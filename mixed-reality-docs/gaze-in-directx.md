---
title: DirectX 中的列印頭和眼睛
description: 在原生 DirectX 應用程式中使用 head 注視和眼追蹤的開發人員指南。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: 眼睛眼, 列印頭, 頭追蹤, 眼睛追蹤, directx, 輸入, 全息影像
ms.openlocfilehash: 2197f0ba3ecb77188d532d77ba29595c380a039d
ms.sourcegitcommit: ff330a7e36e5ff7ae0e9a08c0e99eb7f3f81361f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122052"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a>DirectX 中的列印頭和眼睛輸入

在 Windows Mixed Reality 中, 眼睛和列印頭的輸入是用來判斷使用者正在查看的內容。 這可用來驅動主要輸入模型 (例如[head 和 commit](gaze-and-commit.md)), 也可以提供互動類型的內容。 有兩種類型的注視向量可透過 API 取得: 頭眼和眼睛。  這兩者都是以具有原點和方向的三維光線形式提供。 然後, 應用程式可以 raycast 至其幕後或真實世界, 並判斷使用者的目標。

**Head** , 代表使用者的標頭指向的方向。 請將此視為裝置本身的位置和正向方向, 其位置代表兩個顯示器之間的中心點。 所有混合現實裝置上都可使用 Head 注視。

**眼睛**指的是使用者眼所期待的方向。 原點位於使用者的眼睛之間。  其適用于包含眼睛追蹤系統的混合現實裝置。

Head 和眼睛光線都可透過[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API 來存取。 只要呼叫[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) , 即可在指定的時間戳記和[座標系統](coordinate-systems-in-directx.md)上接收新的 SpatialPointerPose 物件。 此 SpatialPointerPose 包含一個頭部的原點和方向。 它也包含眼睛的原點和方向 (如果有眼睛追蹤可用的話)。

## <a name="using-head-gaze"></a>使用頭部注視

若要存取頭部, 請先呼叫[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)來接收新的 SpatialPointerPose 物件。 您必須傳遞下列參數。
 - [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) , 代表 head 的所需座標系統。 這會由下列程式碼中的*coordinateSystem*變數表示。 如需詳細資訊, 請造訪我們的[座標系統](coordinate-systems-in-directx.md)開發人員指南。
 - [時間戳記](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp), 表示要求之 head 姿勢的確切時間。  通常您會使用時間戳, 其對應到目前畫面格的顯示時間。 您可以從[HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction)物件取得這個預測的顯示時間戳記, 這可透過目前的[HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)來存取。  這個 HolographicFramePrediction 物件是由下列程式碼中的*預測*變數表示。

 一旦您擁有有效的 SpatialPointerPose, 就可以存取標頭位置和正向方向作為屬性。  下列程式碼說明如何存取它們。

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head-gaze
}
```

## <a name="using-eye-gaze"></a>使用眼注視

眼睛的 API 非常類似于列印頭。  它會使用相同的[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, 它會提供您可以針對場景 raycast 的光線來源和方向。  唯一的差別在於, 您必須先明確啟用眼睛追蹤, 才能使用它。 為此, 您需要執行兩個步驟:
1. 要求使用者在您的應用程式中使用目視追蹤的許可權。
2. 在您的套件資訊清單中啟用「注視輸入」功能。

### <a name="requesting-access-to-eye-gaze-input"></a>要求存取眼睛輸入
當您的應用程式啟動時, 呼叫[EyesPose:: RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync)以要求存取眼追蹤。 系統會視需要提示使用者, 並在授與存取權之後傳回[GazeInputAccessStatus:: 允許](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus)。 這是非同步呼叫, 因此需要一些額外的管理。 下列範例會啟動中斷連結的 std:: thread 以等候結果, 並將其儲存至名為*m_isEyeTrackingEnabled*的成員變數。

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
啟動卸離的執行緒只是處理非同步呼叫的一個選項。  或者, 您可以使用C++/winrt 所支援的新[co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency)功能
以下是詢問使用者權限的另一個範例:
-   EyesPose:: IsSupported () 可讓應用程式只在有眼睛追蹤器時觸發許可權對話方塊。
-   GazeInputAccessStatus m_gazeInputAccessStatus;這是為了防止再次彈出許可權提示。

```cpp
GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.

// This will trigger to show the permission prompt to the user.
// Ask for access if there is a corresponding device and registry flag did not disable it.
if (Windows::Perception::People::EyesPose::IsSupported() &&
   (m_gazeInputAccessStatus == GazeInputAccessStatus::Unspecified))
{ 
    Concurrency::create_task(Windows::Perception::People::EyesPose::RequestAccessAsync()).then(
    [this](GazeInputAccessStatus status)
    {
        // GazeInputAccessStatus::{Allowed, DeniedBySystem, DeniedByUser, Unspecified}
            m_gazeInputAccessStatus = status;
        
        // Let's be sure to not ask again.
        if(status == GazeInputAccessStatus::Unspecified)
        {
                m_gazeInputAccessStatus = GazeInputAccessStatus::DeniedBySystem;    
        }
    });
}

```


### <a name="declaring-the-gaze-input-capability"></a>宣告*注視輸入*功能

按兩下*方案總管*中的 package.appxmanifest.xml 檔案。  然後流覽至 [*功能*] 區段, 並查看 [*注視] 輸入*功能。 

![注視輸入功能](images/gaze-input-capability.png)

這會將下列幾行新增至 package.appxmanifest.xml 檔案中的*Package*區段:
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a>取得眼睛光線
一旦您收到 ET 的存取權, 就可以自由地抓取每個畫面格的眼睛光線。
就像使用 head, 使用所需的時間戳記和座標系統呼叫[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)來取得[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) 。 SpatialPointerPose 會透過[眼睛](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes)屬性包含[EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose)物件。 只有在已啟用眼睛追蹤時, 此值才會是 null。 從該處, 您可以藉由呼叫[EyesPose:: IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)來檢查裝置中的使用者是否具有眼睛追蹤校準。  接下來, 使用 [[注視](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze)] 屬性來取得[SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray)寫入眼的位置和方向。 注視屬性有時可以是 null, 因此請務必檢查是否有此情況。 如果已校正的使用者暫時關閉其眼睛, 就可能發生這種情況。

下列程式碼顯示如何存取眼睛光線。

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
            
            // Do something with the eye-gaze
        }
    }
}

```

## <a name="correlating-gaze-with-other-inputs"></a>將注視與其他輸入相互關聯

有時候, 您可能會發現需要與過去事件對應的[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) 。 例如, 如果使用者執行空中碰, 您的應用程式可能會想要知道他們所看到的內容。 基於此目的, 只要將[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)與預測的框架時間搭配使用, 就會因為系統輸入處理和顯示時間之間的延遲而不正確。 此外, 如果針對目標使用眼睛眼, 我們的眼睛通常會在完成認可動作之前繼續進行。 這不是簡單的點按問題, 但在結合長語音命令與快速的移動時, 會變得更重要。 處理這種情況的其中一種方式, 是使用對應于輸入事件的歷程記錄時間戳記, 對[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)進行額外的呼叫。  

不過, 針對透過 SpatialInteractionManager 進行路由的輸入, 有一個比較簡單的方法。 [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)有它自己的[TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)函數。 呼叫可提供完美的相互關聯[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) , 而不需要猜測。 如需有關使用 SpatialInteractionSourceStates 的詳細資訊, 請參閱 DirectX 檔[中的實習和運動控制器](hands-and-motion-controllers-in-directx.md)。

## <a name="see-also"></a>另請參閱
* [頭部注視和認可輸入模型](gaze-and-commit.md)
* [HoloLens 2 上的眼睛](eye-tracking.md)
* [校正](calibration.md)
* [DirectX 中的座標系統](coordinate-systems-in-directx.md)
* [DirectX 中的語音輸入](voice-input-in-directx.md)
* [DirectX 中的手部和運動控制器](hands-and-motion-controllers-in-directx.md)
