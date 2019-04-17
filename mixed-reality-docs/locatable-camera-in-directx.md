---
title: DirectX 之外的可尋獲觀景窗
description: 說明如何在 HoloLens 的應用程式中使用的觀點 (POV) 相機。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens 之外的可尋獲相機、 觀點來看，POV unporoject、 媒體基礎，MF，自訂接收、 逐步解說、 範例程式碼
ms.openlocfilehash: 374b61e3d9bb0e97d5f0c5c8e17a5c882a4ebcd3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595305"
---
# <a name="locatable-camera-in-directx"></a>DirectX 之外的可尋獲觀景窗

本主題描述如何設定[媒體基礎](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx)若要存取管線[相機](locatable-camera.md)在 DirectX 應用程式，包括框架的中繼資料，可讓您找出的映像產生真實世界中。

## <a name="windows-media-capture-and-media-foundation-development-imfattributes"></a>Windows 媒體擷取和 Media Foundation 開發：IMFAttributes

每個影像框架[包含座標系統](locatable-camera.md#images-with-coordinate-systems)，以及兩個重要的轉換。 「 檢視 」 轉換從數位相機，以提供的座標系統的對應和相機中的 「 投射 」 對應至映像中的像素。 座標系統以及 2 的轉換以內嵌中繼資料中每一個透過媒體基礎的影像框架[IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx)。

### <a name="sample-usage-of-reading-attributes-with-mf-custom-sink-and-doing-projection"></a>讀取具有 MF 自訂接收器的屬性，以及執行投影的範例用法

在您自訂的 MF 的接收資料流 ([IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx))，您會收到[IMFSample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx)範例屬性：

下列 MediaExtensions 必須定義為基礎的 WinRT 程式碼：

```
EXTERN_GUID(MFSampleExtension_Spatial_CameraViewTransform, 0x4e251fa4, 0x830f, 0x4770, 0x85, 0x9a, 0x4b, 0x8d, 0x99, 0xaa, 0x80, 0x9b);
EXTERN_GUID(MFSampleExtension_Spatial_CameraCoordinateSystem, 0x9d13c82f, 0x2199, 0x4e67, 0x91, 0xcd, 0xd1, 0xa4, 0x18, 0x1f, 0x25, 0x34);
EXTERN_GUID(MFSampleExtension_Spatial_CameraProjectionTransform, 0x47f9fcb5, 0x2a02, 0x4f26, 0xa4, 0x77, 0x79, 0x2f, 0xdf, 0x95, 0x88, 0x6a);
```

您無法從 WinRT Api，存取這些屬性，但需要媒體延伸模組實作[IMFTransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) （適用於影響） 或[IMFMediaSink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx)並[IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) (自訂接收）。 當您處理此延伸模組中的範例可能是在[IMFTransform::ProcessInput()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[IMFTransform::ProcessOutput()](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx)或[IMFStreamSink::ProcessSample()](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx)，您可以查詢的屬性，例如此範例。

```
ComPtr<IUnknown> spUnknown;
ComPtr<Windows::Perception::Spatial::ISpatialCoordinateSystem> spSpatialCoordinateSystem;
ComPtr<Windows::Foundation::IReference<Windows::Foundation::Numerics::Matrix4x4>> spTransformRef;
Windows::Foundation::Numerics::Matrix4x4 worldToCameraMatrix;
Windows::Foundation::Numerics::Matrix4x4 viewMatrix;
Windows::Foundation::Numerics::Matrix4x4 projectionMatrix;
UINT32 cbBlobSize = 0;
hr = pSample->GetUnknown(MFSampleExtension_Spatial_CameraCoordinateSystem, IID_PPV_ARGS(&spUnknown));
if (SUCCEEDED(hr))
{
    hr = spUnknown.As(&spSpatialCoordinateSystem);
    if (FAILED(hr))
    {
        return hr;
    }
    hr = pSample->GetBlob(MFSampleExtension_Spatial_CameraViewTransform,
                          (UINT8*)(&viewMatrix),
                          sizeof(viewMatrix),
                          &cbBlobSize);
    if (SUCCEEDED(hr) && cbBlobSize == sizeof(Windows::Foundation::Numerics::Matrix4x4))
    {
        hr = pSample->GetBlob(MFSampleExtension_Spatial_CameraProjectionTransform,
                              (UINT8*)(&projectionMatrix),
                              sizeof(projectionMatrix),
                              &cbBlobSize);
        if (SUCCEEDED(hr) && cbBlobSize == sizeof(Windows::Foundation::Numerics::Matrix4x4))
        {
            // Assume m_spCurrentCoordinateSystem is representing
            // world coordinate system application is using
            hr = m_spCurrentCoordinateSystem->TryGetTransformTo(spSpatialCoordinateSystem.Get(),
                                                                &spTransformRef);
            if (FAILED(hr))
            {
                return hr;
            }
            hr = spTransformRef->get_Value(&worldToCameraMatrix);
            if (FAILED(hr))
            {
                return hr;
            }
        }
    }
}
```

若要存取相機中的紋理，您需要建立相機框架紋理相同 D3D 裝置。 此 D3D 裝置處於[IMFDXGIDeviceManager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx)擷取管線中。 若要從媒體擷取您可以使用取得 DXGI 裝置管理員[IAdvancedMediaCapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx)並[IAdvancedMediaCaptureSettings](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx)介面。

```
Microsoft::WRL::ComPtr<IAdvancedMediaCapture> spAdvancedMediaCapture;
Microsoft::WRL::ComPtr<IAdvancedMediaCaptureSettings> spAdvancedMediaCaptureSettings;
Microsoft::WRL::ComPtr<IMFDXGIDeviceManager> spDXGIDeviceManager;
// Assume mediaCapture is Windows::Media::Capture::MediaCapture and initialized
if (SUCCEEDED(((IUnknown *)(mediaCapture))->QueryInterface(IID_PPV_ARGS(&spAdvancedMediaCapture))))
{
    if (SUCCEEDED(spAdvancedMediaCapture->GetAdvancedMediaCaptureSettings(&spAdvancedMediaCaptureSettings)))
    {
        spAdvancedMediaCaptureSettings->GetDirectxDeviceManager(&spDXGIDeviceManager);
    }
}
```

您也可以啟用滑鼠和鍵盤輸入為選擇性的輸入方法，為您的 Windows Mixed Reality 應用程式。 這也可以是很棒的偵錯功能，例如 HoloLens，裝置，並可能需要使用者輸入的沈浸式耳機附加至個人電腦中執行的混合的實境應用程式。
