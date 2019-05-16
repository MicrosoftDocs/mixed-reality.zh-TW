---
title: DirectX 中的前端和眼睛視線
description: 使用前端的視線和追蹤在原生的 DirectX 應用程式的開發人員指南。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: 視線、 前端的視線、 標頭追蹤、 追蹤、 directx、 輸入、 全像投影
ms.openlocfilehash: f9764132df0ca4ae2f02d8f9a5740530676eb4f5
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629611"
---
# <a name="head-and-eye-gaze-in-directx"></a>DirectX 中的前端和眼睛視線

在 Windows Mixed Reality，視線輸入用來判斷使用者正在查看。 這可以用來驅動主要輸入的模型，例如[視線並認可](gaze-and-commit.md)，同時還可以提供內容的互動類型。 有兩種類型的視線向量可透過 API： 視線和眼睛視線前端。  同時，提供三個維度的光線，與來源和方向。 應用程式可以接著 raycast 到場景或真實世界中，並判斷使用者的目標。

**Head 視線**代表使用者的大腦中指向的方向。 將此視為位置和裝置本身的正向方向，代表在中心位置與點之間兩個顯示。  混合實境的所有裝置上使用 Head 視線。

**眼睛視線**代表使用者的眼睛想要的方向。 原點是位於使用者的眼睛之間。  包括追蹤系統監控的混合實境裝置上使用。

前端和眼睛視線光線都可透過存取[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API。 只要呼叫[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)接收新 SpatialPointerPose 物件在指定的時間戳記並[座標系統](coordinate-systems-in-directx.md)。 此 SpatialPointerPose 包含前端的視線來源和方向。 它也包含眼睛視線原點與方向追蹤是否可用。

## <a name="using-head-gaze"></a>使用前端的視線

若要存取前端的視線，開始藉由呼叫[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)接收新的 SpatialPointerPose 物件。 您必須傳遞下列參數。
 - A [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem)前端的視線表示所需的座標系統。 這由*coordinateSystem*變數中的下列程式碼。 如需詳細資訊，請瀏覽我們[座標系統](coordinate-systems-in-directx.md)開發人員指南。
 - A[時間戳記](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp)表示前端的姿勢要求的確切時間。  您通常會使用對應至目前的框架會顯示時的時間的時間戳記。 您可以取得此預測的顯示時間戳記[HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction)物件，它是透過目前可存取[HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)。  這個 HolographicFramePrediction 物件由*預測*變數中的下列程式碼。

 有效 SpatialPointerPose，前端的位置和正向方向就可以存取為屬性。  下列程式碼示範如何存取它們。

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head gaze
}
```

## <a name="using-eye-gaze"></a>使用眼睛視線

非常類似於前端的視線眼睛視線 API。  它會使用相同[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API，可提供無限遠的光線，來源和方向，您可以針對您的場景 raycast。  唯一的差別是您必須明確啟用追蹤後，再使用所要求存取的眼睛。

### <a name="declaring-the-gaze-input-capability"></a>宣告*視線輸入*功能

按兩下 [appxmanifest 中的檔案*方案總管] 中*。  然後瀏覽至*能力*區段，並檢查*視線輸入*功能。 

![視線輸入的功能](images/gaze-input-capability.png)

這樣會加入下列行以*封裝*appxmanifest 檔案中的區段：
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="requesting-access-to-gaze-input"></a>要求的存取權視線輸入
當您的應用程式啟動時，呼叫[EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync)眼睛追蹤的要求存取。 系統會提示使用者如有需要並傳回[GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus)一旦授與存取權。 這會是管理的非同步呼叫，因此它需要一些額外。 下列範例會啟動等候結果，其儲存至成員變數，呼叫的已卸離 std::thread *m_isEyeTrackingEnabled*。

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::UI::Input;

std::thread requestAccessThread([this]()
{
    auto status = EyesPose::RequestAccessAsync().get();

    if (status == GazeInputAccessStatus::Allowed)
        m_isEyeTrackingEnabled = true;
    else
        m_isEyeTrackingEnabled = false;
});

requestAccessThread.detach();

```

正在啟動的已卸離的執行緒只是選項之一來處理非同步呼叫。  或者，您可以使用新[co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency)所支援的功能C++/WinRT。

### <a name="getting-the-eye-gaze-ray"></a>取得眼睛視線光線

一旦您收到存取權等，您可以自由抓取眼睛視線光線的每個畫面。  如同前端的視線，取得[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose)藉由呼叫[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)所需的時間戳記和座標系統。 包含 SpatialPointerPose [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose)物件傳遞[眼睛](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes)屬性。 此為非 null 才會啟用追蹤。 從這裡您可以檢查裝置中的使用者是否藉由呼叫追蹤校正眼睛[EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)。  接下來，使用[視線](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze)屬性來取得[SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing 眼睛視線位置和方向。 視線屬性可以有時可以是 null，因此請務必檢查為這。 這可能會發生是如果校正的使用者暫時關閉其眼睛。

下列程式碼示範如何存取眼睛視線無限遠的光線。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    if (pointerPose.Eyes() && pointerPose.Eyes().IsCalibrationValid())
    {
        if (pointerPose.Eyes().Gaze())
        {
            auto spatialRay = pointerPose.Eyes().Gaze().Value();
            float3 eyeGazeOrigin = spatialRay.Origin;
            float3 eyeGazeDirection = spatialRay.Direction;
            
            // Do something with the eye gaze
        }
    }
}

```

## <a name="correlating-gaze-with-other-inputs"></a>相互關聯的視線，與其他輸入

有時候您可能會發現您需要[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose)過去與事件對應。 比方說，如果使用者執行空中點選時，您的應用程式可能會想知道他們正在看著。 基於此目的，只使用[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)與預測的畫面格時間將不夠準確因為系統的輸入的處理和顯示時間之間的延遲。

若要解決這種情況的一個方法是讓額外的呼叫[SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)，使用對應至輸入事件的歷程記錄時間戳記。  不過，對於透過 SpatialInteractionManager 路由的輸入，還有更容易的方法。 [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)有其自己[TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)函式。 會提供完全相互關聯的電話[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose)而不需要猜測。 如需有關使用 SpatialInteractionSourceStates 的詳細資訊，看看[雙手及 DirectX 中的動作控制站](hands-and-motion-controllers-in-directx.md)文件。

## <a name="see-also"></a>另請參閱
* [指針與 DirectX 中的動作控制站](hands-and-motion-controllers-in-directx.md)
* [DirectX 中的座標系統](coordinate-systems-in-directx.md)
* [視線並認可輸入的模型](gaze-and-commit.md)

