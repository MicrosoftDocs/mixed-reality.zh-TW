---
title: 指針與 DirectX 中的動作控制站
description: 在 原生的 DirectX 應用程式中使用手動追蹤 」 和 「 動作控制站的開發人員指南。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/30/2019
ms.topic: article
keywords: 實際操作、 移動控制站、 directx、 輸入、 全像投影
ms.openlocfilehash: 08666c8c26cd4851c0c003a96a9e96d7a90228ac
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629641"
---
# <a name="hands-and-motion-controllers-in-directx"></a>指針與 DirectX 中的動作控制站

在 Windows Mixed Reality，同時交付和[動作控制器](motion-controllers.md)輸入透過在中找到的空間輸入的 Api，來處理[Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)命名空間。 這可讓您輕鬆地處理常見的動作，如**選取**按下相同的方式，跨雙手及動作控制站。

## <a name="getting-started"></a>使用者入門

若要在 Windows Mixed Reality 中輸入的存取空間，開始 SpatialInteractionManager 介面。  您可以存取這個介面，藉由呼叫[SpatialInteractionManager::GetForCurrentView](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getforcurrentview)，通常是有時在應用程式啟動期間。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

SpatialInteractionManager interactionManager = SpatialInteractionManager::GetForCurrentView();
```

SpatialInteractionManager 的工作就是要提供存取權[SpatialInteractionSources](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource)，代表輸入的來源。  有三種 SpatialInteractionSources 系統所提供。
* **手狀**表示偵測到使用者的手。 手狀來源提供不同的功能，根據裝置，舉凡完全相互連貫的手動追蹤 HoloLens 2 HoloLens 上的基本手勢。 
* **控制器**代表配對的移動控制站。 動作控制站可以提供的各種功能。  例如: 選取觸發程序 」、 「 功能表按鈕 」、 「 掌握按鈕 」、 「 跳動和 「 搖桿。
* **語音**代表使用者的語音讀出系統偵測到的關鍵字。 比方說，此來源會插入選取的按下並發行每當使用者講的是 [選取]。

每個畫面格資料的來源由[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)介面。 有兩種不同的方式來存取此資料，根據您要在您的應用程式中使用事件驅動或以輪詢為基礎的模型。

### <a name="event-driven-input"></a>事件驅動的輸入
SpatialInteractionManager 提供您的應用程式可以接聽的事件數目。  一些範例包括[SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed)， [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased)並[SourceUpdated](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated)。

例如，下列程式碼攔截程序呼叫 MyApp::OnSourcePressed SourcePressed 事件的事件處理常式。  這可讓您的應用程式偵測到任何類型的互動來源上的按。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
interactionManager.SourcePressed({ this, &MyApp::OnSourcePressed });

```

這個已按下的事件會傳送至您的應用程式以非同步的方式，以及對應的 SpatialInteractionSourceState 在按下所發生的時間。 您的應用程式或遊戲引擎可能會想要執行一些處理立即或您可能想要在您處理常式的輸入事件資料排入佇列。 以下是 SourcePressed 事件，示範如何檢查是否已按下 [選取] 按鈕的事件處理常式函式。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

void MyApp::OnSourcePressed(SpatialInteractionManager const& sender, SpatialInteractionSourceEventArgs const& args)
{
    if (args.PressKind() == SpatialInteractionPressKind::Select)
    {
        // Select button was pressed, update app state
    }
}
```

上述程式碼只會檢查 'Select' press，對應到在裝置上的主要動作。 範例包括 HoloLens 上的 AirTap 或是提取動作控制站上的觸發程序。  'Select' 動作表示使用者来啟用它們的目標全像圖。  SourcePressed 事件會引發許多不同的按鈕和筆勢，您可以檢查來測試這些情況下 SpatialInteractionSource 上的其他屬性。

### <a name="polling-based-input"></a>輪詢為基礎的輸入
您也可以使用 SpatialInteractionManager 輪詢有輸入的目前狀態，因此每個畫面。  若要這樣做，只要呼叫[GetDetectedSourcesAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp)每個畫面。  此函數會傳回陣列，其中包含一個[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)每個 active directory 的[SpatialInteractionSource](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource)。 這表示另一個用於每個作用中動作控制站，一個用於每一個追蹤的指針，一個用於語音如果最近已玩具店的 'select' 命令。 您可以檢查每個磁碟機輸入 SpatialInteractionSourceState 上的屬性到您的應用程式。 

以下是如何檢查使用輪詢方法的 'select' 動作的範例。 請注意，*預測*變數代表[HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction)物件，可從此[HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
auto sourceStates = m_spatialInteractionManager.GetDetectedSourcesAtTimestamp(prediction.Timestamp());

for (auto& sourceState : sourceStates)
{
    if (sourceState.IsSelectPressed())
    {
        // Select button is down, update app state
    }
}
```

每個 SpatialInteractionSource 有一個識別碼，可用來識別新的來源，並將相互關聯的現有來源畫面格框架。  指針會指派新的識別碼，每次，但它們將，並輸入 FOV，控制器識別碼的工作階段期間維持靜態。  您可以使用上 SpatialInteractionManager 事件這類[SourceDetected](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcedetected)並[SourceLost](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcelost)、 手進入或離開裝置時做出回應的檢視或當控制器動作會開啟/關閉或配對/配對。

### <a name="predicted-vs-historical-poses"></a>歷程記錄會帶來與預測
請注意，GetDetectedSourcesAtTimestamp 時間戳記參數。 這可讓您要求的狀態，並會造成可以預測的資料或歷程記錄，讓您相互關聯與其他的輸入來源的空間互動。 比方說，呈現時目前的框架中的游標的位置，您可以傳入所提供的預測時間戳記[HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)。 這可讓系統以正向預測密切配合呈現的畫面格的輸出，察覺到的延遲降至最低的游標位置。

不過，這類預測的姿勢不會產生指標的理想光線，針對具有互動資料來源。 例如，按下動作控制器按鈕時，可能需要最多 20 毫秒該事件反昇，以透過藍芽作業系統。 同樣地，使用者執行手動動作之後，一段時間可能會通過，才能在系統偵測到筆勢和應用程式，則它會輪詢。 時您的應用程式會輪詢狀態變更，前端和 hand 帶來用於互動實際發生在過去的結果的目標。 如果您的目標將您目前的 HolographicFrame 時間戳記傳遞至 GetDetectedSourcesAtTimestamp，姿勢會改為可向前預測目標的光跡時將會顯示在畫面格，可能在未來在超過 20 毫秒。 這個未來的姿勢適合*轉譯*互動的來源，但複合的時間問題*目標*互動，因為使用者的目標設為過去發生。

幸運的是， [SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed)， [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased)並[SourceUpdated](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated)事件可提供歷史[狀態](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state)與相關聯每個輸入的事件。  直接包括歷程記錄標頭和 hand 帶來可透過[TryGetPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)，以及歷史[時間戳記](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.timestamp)，您可以傳遞給其他 Api 與此事件相互關聯。

這會產生下列最佳作法時轉譯，而且目標設定為雙手及控制站與每個畫面格：
* 針對**手/控制器轉譯**每個畫面中，您的應用程式應該**輪詢**的**轉寄預測**在目前的框架 photon 階段會造成每個互動來源。  您可以藉由呼叫的所有互動來源輪詢[GetDetectedSourcesAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp)傳入所提供的預測時間戳記的每個框架[HolographicFrame::CurrentPrediction](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.currentprediction)。
* 針對**手/控制站為目標**在按下或版本中，您的應用程式應該處理按下/發行**事件**，raycasting 根據**歷程記錄**的前端或手動姿勢該事件。 您處理來取得這個目標的光跡[SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed)或是[SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased)事件，取得[狀態](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state)屬性與事件引數，然後呼叫其[TryGetPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)方法。

## <a name="cross-device-input-properties"></a>跨裝置的輸入的屬性
SpatialInteractionSource API 支援控制站] 及 [手動追蹤系統有廣泛的功能。 這些功能的數字之間是共通的裝置類型。 例如，手動追蹤和移動控制站這兩個提供的 'select' 動作和 3D 的位置。 可能的話，API 會對應至 SpatialInteractionSource 上的相同屬性的這些常見的功能。  這可讓應用程式更輕鬆地支援各種不同的輸入類型。 下表描述支援的屬性，以及它們如何比較輸入類型。

| 屬性 | 描述 | HoloLens 筆勢 | 動作控制站 | 相互連貫的指針|
|--- |--- |--- |--- |--- |
| [SpatialInteractionSource::**法線慣用手的**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.handedness) | 右側或左側 / 控制站。 | 不支援 | 支援 | 支援 |
| [SpatialInteractionSourceState::**IsSelectPressed**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isselectpressed) | 目前的主要按鈕的狀態。 | 空中點選 | 觸發程序 | 寬鬆空中點選 （垂直縮小） |
| [SpatialInteractionSourceState::**IsGrasped**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isgrasped) | [擷取] 按鈕的目前狀態。 | 不支援 | 擷取按鈕 | 縮小或已關閉的手 |
| [SpatialInteractionSourceState::**IsMenuPressed**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.ismenupressed) | 目前的功能表按鈕的狀態。    | 不支援 | 功能表按鈕 | 不支援 |
| [SpatialInteractionSourceLocation::**Position**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.position) | XYZ 的手動或控點的位置，在控制器上的位置。 | Palm 位置 | 調整底框姿勢位置 | Palm 位置 |
| [SpatialInteractionSourceLocation::**Orientation**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.orientation) | 表示底框之手的方向的四元數會造成在控制器上。 | 不支援 | 調整底框姿勢方向 | Palm 方向 |
| [SpatialPointerInteractionSourcePose::**Position**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.position#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_Position) | 指標與射線的原點。 | 不支援 | 支援 | 支援 |
| [SpatialPointerInteractionSourcePose::**ForwardDirection**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.forwarddirection#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_ForwardDirection) | 光線方向的指標。 | 不支援 | 支援 | 支援 |

部分上述的屬性並不適用於所有裝置、 裝置和 API 提供為了測試這個方法。 例如，您可以檢查[SpatialInteractionSource::IsGraspSupported](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.isgraspsupported)屬性來判斷來源是否提供掌握的動作。

### <a name="grip-pose-vs-pointing-pose"></a>指標的姿勢與的底框姿勢

Windows Mixed Reality 支援各種不同的外型規格的移動控制站。  它也支援相互連貫的手動追蹤系統。  所有這些系統都有不同的游標位置和應用程式應該使用使用者的手中的點或 rendreing 物件進行自然的"forward"方向之間的關聯性。  若要支援所有這些，有兩種類型的 3D 帶來提供兩個手動追蹤和移動控制器。  第一個是調整底框姿勢，代表使用者的游標位置。  第二個指姿勢，表示指標的光線，來自使用者的手或控制站。 因此，如果您想要呈現**使用者的手**或是**物件保留在使用者的手**，例如劍或槍，使用的底框姿勢。 如果您要從控制器或手的形狀，例如，當使用者 raycast**指向 UI** ，使用指標的姿勢。

您可以存取**底框姿勢**透過[SpatialInteractionSourceState::Properties::TryGetLocation(...)](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties.trygetlocation#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).其定義，如下所示：
* **抓住位置**:Palm 距心自然，保留控制器時調整左邊或右邊，置中的底框的位置。
* **抓住方向的右座標軸**:當您完全開啟以形成平坦的 5 手指姿勢手時，光線，一般是您 palm （從左 palm、 從右 palm 回溯順向）
* **抓住方向的順向軸**:當您關閉您的手部分 （如同保存在控制站）、"forward"tube 透過由非 thumb 手指點光線。
* **抓住方向的總軸**:隱含的權限和轉送的定義總軸。

您可以存取**指標姿勢**透過[SpatialInteractionSourceState::Properties::TryGetLocation （...）:: SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose)或[SpatialInteractionSourceState::TryGetPointerPose （...）:: TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_)。

## <a name="controller-specific-input-properties"></a>控制器特有的輸入的屬性
控制站，SpatialInteractionSource 有一個控制器屬性與其他功能。
* **HasThumbstick:** 如果為 true，則控制器會有搖桿。 檢查[ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties)屬性取得搖桿 SpatialInteractionSourceState x 和 y 值 （ThumbstickX 和 ThumbstickY），以及其已按下的狀態 (IsThumbstickPressed)。
* **HasTouchpad:** 如果為 true，則控制器會有觸控板。 檢查取得觸控板 SpatialInteractionSourceState ControllerProperties 屬性 x 和 y 值 （TouchpadX 和 TouchpadY），並知道在使用者觸碰板 (IsTouchpadTouched)，以及它們會按下 （觸控板IsTouchpadPressed)。
* **SimpleHapticsController:** 控制器 SimpleHapticsController API 可讓您檢查控制器，haptics 功能，也可讓您控制 haptic 意見反應。

請注意，觸控板和搖桿的範圍為兩個座標軸的 1-1 （從下至上的情況下，以及從左到右）。 類比的觸發程序存取使用 SpatialInteractionSourceState::SelectPressedValue; 屬性，此範圍會有 0 到 1 的範圍。 值為 1 IsSelectPressed 設為 true，而且所使用的相互關聯任何其他值相互關聯與 IsSelectPressed 等於 false。

## <a name="articulated-hand-tracking"></a>相互連貫的手動追蹤
Windows Mixed Reality API 相互連貫的手動追蹤，例如 HoloLens 2 提供完整的支援。 追蹤的相互連貫的手可用來在應用程式中實作直接操作和點認可輸入的模型。 它也可以用來撰寫完全自訂的互動。

### <a name="hand-skeleton"></a>手狀基本架構
追蹤的相互連貫的手動提供 25 的聯合基本架構，可讓許多不同類型的互動。  基本架構提供 5 接點的索引/中間/信號/小手指、 4 關節 thumb 和 1 手腕聯合。  手腕聯合做為基底的階層。 下圖說明基本架構的版面配置。

![手狀基本架構](images/hand-skeleton.png)

在大部分情況下，每個聯結稱為根據它所代表的骨。  由於在每個聯結有兩個極簡，我們會使用根據該位置的子系拼死每個聯結的命名慣例。  子骨會定義為更手腕骨。  比方說，「 索引 Proximal"聯合包含起始位置的索引 proximal 骨和該骨的方向。  它不包含骨的結束位置。  如果您需要的您會從取得下一步 在階層中，「 索引中繼 」 聯合聯合。

除了 25 的階層式接合，系統會提供 palm 聯結。  Palm 通常不會視為的骨架結構的一部分。  它只被提供便利的方式，以取得整體游標的位置和方向。

為每個共同提供了下列資訊：

| 名稱 | 描述 |
|--- |--- |
|位置 | 3D 定位的結合，可在任何要求座標系統。 |
|Orientation | 3D 方向骨，可在任何要求座標系統。 |
|半徑 | 介面上的共同位置的面板的距離。 適用於微調直接互動或手指寬度所依賴的視覺效果。 |
|準確度 | 如何確定系統覺得這個聯合資訊提供提示。 |

您可以存取透過函式手動基本架構的資料上[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)。  在呼叫此函式[TryGetHandPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygethandpose#Windows_UI_Input_Spatial_SpatialInteractionSourceState_TryGetHandPose)，並傳回呼叫物件[HandPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose)。  如果來源不支援相互連貫的實際操作，此函式會傳回 null。  HandPose 之後，您可以藉由呼叫來取得目前的聯合資料[TryGetJoint](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose.trygetjoint#Windows_Perception_People_HandPose_TryGetJoint_Windows_Perception_Spatial_SpatialCoordinateSystem_Windows_Perception_People_HandJointKind_Windows_Perception_People_JointPose__)，具有名稱的結合您感興趣。  資料以傳回[JointPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.jointpose)結構。  下列程式碼取得食指提示的位置。 變數*currentState*代表的執行個體[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)。

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::Foundation::Numerics;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    JointPose joint;
    if (handPose.TryGetJoint(desiredCoordinateSystem, HandJointKind::IndexTip, joint))
    {
        float3 indexTipPosition = joint.Position;

        // Do something with the index tip position
    }
}
```

### <a name="hand-mesh"></a>手狀網格

相互連貫的手動追蹤 API 可讓您完全 deformable 三角手網格。  此網格即時以及手動基本架構中，可以定義，並可用於視覺效果，以及進階的物理技術。  若要存取手網狀結構，您必須先建立[HandMeshObserver](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver)藉由呼叫物件[TryCreateHandMeshObserverAsync](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)上[SpatialInteractionSource](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource)。  這只需要執行一次針對每個來源，通常您會看到它的第一次。  這表示您將呼叫此函式可建立 HandMeshObserver 物件，只要一隻手進入 FOV。  請注意，這是非同步函式，因此您必須處理的並行存取此處。  一旦可用，您可以藉由呼叫的三角形索引緩衝區要求 HandMeshObserver 物件[GetTriangleIndices](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver.gettriangleindices#Windows_Perception_People_HandMeshObserver_GetTriangleIndices_System_UInt16___)。  索引不會變更框架範圍內，因此您可以一次取得這些，並進行快取來源的存留期。  提供索引的順時針彎曲的順序。

下列程式碼會建立網格觀察者的已卸離 std::thread 啟動，並擷取索引緩衝區，一旦網狀結構觀察者可以使用。  它會從名為開始*currentState*，這是執行個體[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)代表追蹤手的形狀。

```cpp
using namespace Windows::Perception::People;

std::thread createObserverThread([this, currentState]()
{
    HandMeshObserver newHandMeshObserver = currentState.Source().TryCreateHandMeshObserverAsync().get();
    if (newHandMeshObserver)
    {
        unsigned indexCount = newHandMeshObserver.TriangleIndexCount();
        vector<unsigned short> indices(indexCount);
        newHandMeshObserver.GetTriangleIndices(indices);

        // Save the indices and handMeshObserver for later use - and use a mutex to synchronize access if needed!
     }
});
createObserverThread.detach();
```
正在啟動的已卸離的執行緒只是選項之一來處理非同步呼叫。  或者，您可以使用新[co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency)所支援的功能C++/WinRT。

HandMeshObserver 物件之後，您應該保留至其本身及其對應的 SpatialInteractionSource 為作用中的持續時間。  然後每個畫面格，您可以要求它的最新的頂點緩衝區，藉由呼叫表示手形[GetVertexStateForPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver.getvertexstateforpose)並傳入[HandPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose)執行個體，表示您想要的頂點姿勢。  每個頂點緩衝區中的有位置與一般。  以下是如何取得目前的頂點集手動網格的範例。  如往常*currentState*變數所代表的執行個體[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)。

```cpp
using namespace winrt::Windows::Perception::People;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    std::vector<HandMeshVertex> vertices(handMeshObserver.VertexCount());
    auto vertexState = handMeshObserver.GetVertexStateForPose(handPose);
    vertexState.GetVertices(vertices);

    auto meshTransform = vertexState.CoordinateSystem().TryGetTransformTo(desiredCoordinateSystem);
    if (meshTransform != nullptr)
    {
        // Do something with the vertices and mesh transform, along with the indices that you saved earlier
    }
}
```

相較於基本架構的接合，手動網狀結構 API 不允許您指定頂點的座標系統。  相反地， [HandMeshVertexState](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshvertexstate)指定中所提供之頂點的座標系統。  就可以藉由呼叫取得網狀結構轉換[TryGetTransformTo](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem.trygettransformto#Windows_Perception_Spatial_SpatialCoordinateSystem_TryGetTransformTo_Windows_Perception_Spatial_SpatialCoordinateSystem_)並指定您所需的座標系統。  您必須使用此網格轉換，當您使用的頂點。  這種方法會減少 CPU 額外負荷，尤其是如果您只使用網格轉譯進行。

## <a name="gaze-and-commit-composite-gestures"></a>視線並認可複合的筆勢
使用視線認可輸入的模型，特別是在 HoloLens 的應用程式 （第一個一般），空間輸入 API 提供一個選擇性[SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) ，可用於啟用基礎建置的複合筆勢' select' 事件。  藉由路由至全像 SpatialGestureRecognizer 從 SpatialInteractionManager 互動，應用程式可以偵測點選、 保留、 操作及瀏覽事件一致地跨指針、 語音和空間的輸入的裝置，而不需要處理按下並手動釋放。

SpatialGestureRecognizer 執行只有最少去除混淆您要求的筆勢集合之間。 比方說，如果您要求只點選時，使用者可能按住他們的手指，只要他們喜歡和點選，還是會發生。 如果您要求同時點選並按住不放，約一秒鐘的按住他們的手指，軌跡會將升級至保留後點選將不再發生。

若要使用 SpatialGestureRecognizer，處理 SpatialInteractionManager [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected)事件，並抓取 SpatialPointerPose 那里公開。 使用使用者的前端的視線光線，從這個姿勢與全像投影交集和介面網狀結構中使用者的周圍環境，以判斷使用者準備進行互動。 然後，路由 SpatialInteraction 傳送目標全像 SpatialGestureRecognizer 的事件引數中使用其[CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction)方法。 這會啟動解譯根據該互動[SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings)該辨識器上設定，或在建立時- [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings)。

HoloLens 上 （第一次層代）、 互動和筆勢應該通常衍生其目標從使用者的前端的視線，而不是嘗試轉譯，或直接互動的游標位置。 一旦啟動互動，相對的左手邊的動作可用來控制鍵筆勢，如同操作或瀏覽軌跡。

## <a name="see-also"></a>另請參閱
* [DirectX 中的前端和眼睛視線](gaze-in-directx.md)
* [直接操作輸入的模型](direct-manipulation.md)
* [點認可輸入的模型](point-and-commit.md)
* [視線並認可輸入的模型](gaze-and-commit.md)
* [運動控制器](motion-controllers.md)
