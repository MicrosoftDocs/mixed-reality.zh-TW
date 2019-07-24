---
title: Unity 中的混合現實原生物件
description: 取得 Unity 中基礎全像原生物件的存取權。
author: vladkol
ms.author: vladkol
ms.date: 05/20/2018
ms.topic: article
keywords: unity、mixed reality、native、xrdevice、spatialcoordinatesystem、holographicframe、holographiccamera、ispatialcoordinatesystem、iholographicframe、iholographiccamera、getnativeptr
ms.openlocfilehash: 76073f5b2adfdf27cfbb153f95bb3a533d02e196
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942094"
---
# <a name="mixed-reality-native-objects-in-unity"></a>Unity 中的混合現實原生物件

[取得 HolographicSpace](getting-a-holographicspace.md)是每個混合現實應用程式開始接收相機資料和呈現畫面格之前的功能。 在 Unity 中, 引擎會為您處理這些步驟, 並在其轉譯迴圈中于內部處理全息的物件和更新。

不過, 在 advanced 案例中, 您可能需要取得基礎原生物件的存取權, 例如<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>和目前的<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>。 <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine. XR. XRDevice</a>提供這些原生物件的存取權。

## <a name="xrdevice"></a>XRDevice 

**命名空間：** *UnityEngine.XR*<br>
**類型：** *XRDevice*

*XRDevice*類型可讓您使用<a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a>方法取得基礎原生物件的存取權。 GetNativePtr 傳回的內容會因不同的平臺而異。 在通用 Windows 平臺上, 當以 Windows Mixed Reality XR SDK 為目標時, XRDevice. GetNativePtr 會將指標 (IntPtr) 傳回至下列結構: 

```cs
using System;
using System.Runtime.InteropServices;

[StructLayout(LayoutKind.Sequential)]
struct HolographicFrameNativeData
{
    public uint VersionNumber;
    public uint MaxNumberOfCameras;
    public IntPtr ISpatialCoordinateSystemPtr; // Windows::Perception::Spatial::ISpatialCoordinateSystem
    public IntPtr IHolographicFramePtr; // Windows::Graphics::Holographic::IHolographicFrame 
    public IntPtr IHolographicCameraPtr; // // Windows::Graphics::Holographic::IHolographicCamera
}
```
您可以使用 PtrToStructure 方法將它轉換成 HolographicFrameNativeData:
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
***IHolographicCameraPtr** 是 IntPtr 封送處理為 UnmanagedType.ByValArray 等於 MaxNumberOfCameras 長度的陣列* 


### <a name="using-holographicframenativedata"></a>使用 HolographicFrameNativeData

> [!NOTE]
> 變更透過 HolographicFrameNativeData 收到的原生物件狀態可能會造成無法預期的行為和轉譯成品, 特別是當 Unity 也是相同狀態的原因時。  例如, 您不應該呼叫 HolographicFrame. UpdateCurrentPrediction, 否則 Unity 以該框架轉譯的姿勢預測, 將不會與 Windows 預期的姿勢同步, 這會減少[全息影像的穩定性](hologram-stability.md)。

當您的原生外掛程式或C#程式碼中需要存取原生介面來進行轉譯或調試時, 您可以使用 HolographicFrameNativeData 中的資料。 

以下範例示範如何使用 HolographicFrameNativeData 來取得目前框架的 photon 時間預測。 
```cs
using System;
using System.Runtime.InteropServices;

public static bool GetCurrentFrameDateTime(out DateTime frameDateTime)
{
#if (!UNITY_EDITOR && UNITY_WSA) || ENABLE_WINMD_SUPPORT
    IntPtr nativeStruct = UnityEngine.XR.XRDevice.GetNativePtr();

    if (nativeStruct != IntPtr.Zero)
    {
        HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativeStruct);

        if (hfd.IHolographicFramePtr != IntPtr.Zero)
        {
            var holographicFrame = (Windows.Graphics.Holographic.HolographicFrame)Marshal.GetObjectForIUnknown(hfd.IHolographicFramePtr);
            frameDateTime = holographicFrame.CurrentPrediction.Timestamp.TargetTime.DateTime;
            return true;
        }
    }

#endif

    frameDateTime = DateTime.MinValue;
    return false;
}

```

## <a name="see-also"></a>另請參閱
* <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>
* [DirectX 中的呈現](rendering-in-directx.md)
