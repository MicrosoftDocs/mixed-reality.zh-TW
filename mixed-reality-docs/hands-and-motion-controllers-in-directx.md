---
title: DirectX 中的實習和運動控制器
description: 在原生 DirectX 應用程式中使用手動追蹤和動作控制器的開發人員指南。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/30/2019
ms.topic: article
keywords: 手、運動控制器、directx、輸入、全息影像
ms.openlocfilehash: 08666c8c26cd4851c0c003a96a9e96d7a90228ac
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629641"
---
# <a name="hands-and-motion-controllers-in-directx"></a>DirectX 中的實習和運動控制器

在 Windows Mixed Reality 中, 會透過[windows. UI. input](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)命名空間中找到的空間輸入 api 來處理「手」和「[移動控制器](motion-controllers.md)」輸入。 如此一來, 您就可以輕鬆處理一般動作, 像是在手和運動控制器上同時按相同方式。

## <a name="getting-started"></a>使用者入門

若要存取 Windows Mixed Reality 中的空間輸入, 請從 SpatialInteractionManager 介面開始。  您可以藉由呼叫[SpatialInteractionManager:: GetForCurrentView](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getforcurrentview)來存取此介面, 通常是在應用程式啟動期間的一段時間。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

SpatialInteractionManager interactionManager = SpatialInteractionManager::GetForCurrentView();
```

SpatialInteractionManager 的工作是提供[SpatialInteractionSources](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource)的存取權, 這代表輸入的來源。  系統中有三種可用的 SpatialInteractionSources。
* **手**代表使用者所偵測到的手。 手來源提供以裝置為基礎的不同功能, 範圍從 HoloLens 上的基本手勢到 HoloLens 2 上的完整清楚表達追蹤。 
* **控制器**代表配對的動作控制器。 動作控制器可以提供各種功能。  例如: 選取 [觸發程式]、[功能表按鈕]、[touchpads] 和 [thumbsticks]。
* **Voice**代表使用者的語音說話系統偵測到的關鍵字。 例如, 每當使用者說「Select」時, 此來源就會插入 Select 按和放開。

來源的每個畫面格資料會以[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)介面表示。 有兩種不同的方式可以存取這項資料, 取決於您是否想要在應用程式中使用事件驅動或輪詢型模型。

### <a name="event-driven-input"></a>事件驅動的輸入
SpatialInteractionManager 會提供一些您的應用程式可以接聽的事件。  其中一些範例包括[SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed)、 [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased)和[SourceUpdated](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated)。

例如, 下列程式碼會將名為 MyApp:: OnSourcePressed 的事件處理常式連結至 SourcePressed 事件。  這可讓您的應用程式偵測到任何類型互動來源上的按下動作。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
interactionManager.SourcePressed({ this, &MyApp::OnSourcePressed });

```

這個按下的事件會以非同步方式傳送至您的應用程式, 以及按下發生時的對應 SpatialInteractionSourceState。 您的應用程式或遊戲引擎可能會想要立即執行一些處理, 或者您可能想要在輸入處理常式中將事件資料排入佇列。 以下是 SourcePressed 事件的事件處理常式函式, 它會顯示如何檢查是否已按下 [選取] 按鈕。

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

上述程式碼只會檢查 [Select] 按下, 其對應至裝置上的主要動作。 範例包括在 HoloLens 上執行 AirTap, 或在動作控制器上提取觸發程式。  [選取] 按下代表使用者想要啟用其目標的全息影像。  SourcePressed 事件將會針對許多不同的按鈕和手勢引發, 您可以檢查 SpatialInteractionSource 上的其他屬性來測試這些案例。

### <a name="polling-based-input"></a>以輪詢為基礎的輸入
您也可以使用 SpatialInteractionManager 來輪詢每個框架之輸入的目前狀態。  若要這樣做, 只要在每個框架中呼叫[GetDetectedSourcesAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp)即可。  此函式會傳回陣列, 其中包含每個現用[SpatialInteractionSource](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource)的一個[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) 。 這表示每個作用中的動作控制器各一個, 每個追蹤的手一個, 另一個用於語音 (如果最近從未提到 ' select ' 命令)。 接著, 您可以檢查每個 SpatialInteractionSourceState 上的屬性, 以將輸入帶入您的應用程式中。 

以下是如何使用輪詢方法來檢查「選取」動作的範例。 請注意,*預測*變數代表可從[HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)取得的[HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction)物件。

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

每個 SpatialInteractionSource 都有一個識別碼, 可讓您用來識別新的來源, 並使現有的來源與框架相互關聯。  每次離開時都會指派一個新的識別碼, 然後輸入 FOV, 但在會話的持續時間內, 控制器識別碼會保持靜態。  您可以使用 SpatialInteractionManager 上的事件 (例如[SourceDetected](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcedetected)和[SourceLost](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcelost)), 以在進入或離開裝置時做出反應, 或在動作控制器開啟/關閉或配對/未配對時回應。

### <a name="predicted-vs-historical-poses"></a>預測與歷程記錄的比較
請注意, GetDetectedSourcesAtTimestamp 具有 timestamp 參數。 這可讓您要求狀態並產生預測或歷程記錄的資料, 讓您將空間互動與其他輸入來源相互關聯。 例如, 在目前的框架中轉譯手的位置時, 您可以傳入[HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)所提供的預測時間戳記。 這可讓系統向前預測手的位置, 以緊密地配合轉譯的畫面格輸出, 並將認知的延遲降到最低。

不過, 這類預測的姿勢並不會產生以互動來源為目標的理想指標光線。 例如, 按下 [移動控制器] 按鈕時, 可能需要20毫秒該事件, 才能透過藍牙向上到作業系統。 同樣地, 在使用者執行右手手勢之後, 可能會在系統偵測到手勢之前經過一些時間, 然後您的應用程式會輪詢它。 當您的應用程式輪詢狀態變更時, 就會用來以過去實際發生的互動為目標。 如果您將目前 HolographicFrame 的時間戳記傳遞至 GetDetectedSourcesAtTimestamp, 則會在顯示畫面格時, 將姿勢預測為目標光線, 而這可能會超過未來的20毫秒。 這個未來的姿勢適用于轉譯互動來源, 但會將我們的時間問題放在使用者的目標發生在過去的互動上。

幸好, [SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed)、 [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased)和[SourceUpdated](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated)事件會提供與每個輸入事件相關聯的歷程記錄[狀態](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state)。  這會直接包含透過[TryGetPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)提供的歷程記錄, 以及您可以傳遞給其他 api 以與此事件相互關聯的歷程記錄[時間戳記](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.timestamp)。

這會導致下列最佳作法: 在每個框架中呈現和鎖定目標時,
* 對於呈現每個畫面格的**手動/控制**站, 您的應用程式應該**輪詢**每個互動來源在目前框架 photon 時間的順**向預測**姿勢。  您可以藉由呼叫[GetDetectedSourcesAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp)每個畫面格來輪詢所有互動來源, 傳入[HolographicFrame:: CurrentPrediction](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.currentprediction)所提供的預測時間戳記。
* 對於以按下或發行為**目標的手動/控制**站, 您的應用程式應根據該事件的歷程**記錄**head 或手, 處理已按下/已釋放的**事件**raycasting。 您可以藉由處理[SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed)或[SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased)事件、從事件引數取得[State](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state)屬性, 然後呼叫其[TryGetPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)方法, 來取得此目標光線。

## <a name="cross-device-input-properties"></a>跨裝置輸入屬性
SpatialInteractionSource API 支援具有各種功能的控制器和手追蹤系統。 其中一些功能在裝置類型之間是共通的。 例如, 「手追蹤」和「動作控制器」都提供「選取」動作和3D 位置。 API 盡可能將這些通用功能對應至 SpatialInteractionSource 上的相同屬性。  這可讓應用程式更輕鬆地支援廣泛的輸入類型。 下表描述支援的屬性, 以及它們如何在輸入類型之間進行比較。

| 屬性 | 描述 | HoloLens 手勢 | 運動控制器 | 清楚表達的手|
|--- |--- |--- |--- |--- |
| [SpatialInteractionSource::**慣用手**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.handedness) | 向右或向左或控制器。 | 不支援 | 支援 | 支援 |
| [SpatialInteractionSourceState::**IsSelectPressed**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isselectpressed) | 主要按鈕的目前狀態。 | 空中碰 | 觸發程序 | 寬鬆的點擊 (直立縮小) |
| [SpatialInteractionSourceState::**IsGrasped**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isgrasped) | [抓取] 按鈕的目前狀態。 | 不支援 | 抓取按鈕 | 縮小或右 |
| [SpatialInteractionSourceState::**IsMenuPressed**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.ismenupressed) | 功能表按鈕的目前狀態。    | 不支援 | 功能表按鈕 | 不支援 |
| [SpatialInteractionSourceLocation::**Position**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.position) | 控制器上的手邊或手柄位置的 XYZ 位置。 | Palm 位置 | 手柄姿勢位置 | Palm 位置 |
| [SpatialInteractionSourceLocation::**取向**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.orientation) | 四元數, 表示控制器上手形或底底姿勢的方向。 | 不支援 | 手柄姿勢方向 | Palm 方向 |
| [SpatialPointerInteractionSourcePose::**Position**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.position#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_Position) | 指標光線的原點。 | 不支援 | 支援 | 支援 |
| [SpatialPointerInteractionSourcePose::**ForwardDirection**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.forwarddirection#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_ForwardDirection) | 指標光線的方向。 | 不支援 | 支援 | 支援 |

在所有裝置上都無法使用上述屬性, 而 API 會提供測試此項的方法。 例如, 您可以檢查[SpatialInteractionSource:: IsGraspSupported](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.isgraspsupported)屬性來判斷來源是否提供了「抓住」動作。

### <a name="grip-pose-vs-pointing-pose"></a>抓握姿勢與指標姿勢

Windows Mixed Reality 支援各種外型規格中的動作控制器。  它也支援明確表述的追蹤系統。  所有這些系統在手上的位置與自然「向前」方向之間有不同的關聯性, 應用程式應該在使用者手中用來指向或 rendreing 物件。  為了支援所有這種情況, 有兩種類型的3D 姿勢可提供給手追蹤和動作控制器。  第一個是「底框姿勢」, 代表使用者的手位置。  第二個是指向姿勢, 表示來自使用者的手或控制器的指標光線。 因此, 如果您想要轉譯使用者的**手**或**保留在使用者手中的物件**(例如寶劍或機槍), 請使用「底握姿勢」。 如果您想要從控制器或手中 raycast (例如, 當使用者**指向 UI**時), 請使用指標姿勢。

您可以透過[SpatialInteractionSourceState::P 屬性 r):: TryGetLocation (...)](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties.trygetlocation#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_)來存取底框**姿勢**。其定義如下:
* **抓握位置**:自然地保留控制器時的 palm 距心, 會向左或右調整以置中的位置。
* **抓握方向的右軸**:當您完全開啟手來形成一般的5方姿勢時, 您的 palm 的光線 (從左 palm 向前, 向右的 palm 往後)
* **抓握方向的正向軸**:當您關閉手中的部分 (如同按住控制器) 時, 就會以非拇指手指所形成的電子管「轉送」光線。
* **抓握方向的向上軸**:右邊和後向定義所隱含的向上軸。

您可以透過[SpatialInteractionSourceState::P 屬性 r):: TryGetLocation (...):: SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose)或[SpatialInteractionSourceState:: TryGetPointerPose (...):: TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_)來存取**指標姿勢**.

## <a name="controller-specific-input-properties"></a>控制器特定的輸入屬性
對於控制器而言, SpatialInteractionSource 具有具有額外功能的控制器屬性。
* **HasThumbstick:** 若為 true, 則控制器具有操縱杆。 檢查 SpatialInteractionSourceState 的[ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties)屬性, 以取得操縱杆 x 和 y 值 (ThumbstickX 和 ThumbstickY), 以及其按下的狀態 (IsThumbstickPressed)。
* **HasTouchpad:** 若為 true, 則控制器具有觸控板。 檢查 SpatialInteractionSourceState 的 ControllerProperties 屬性, 以取得觸控板 x 和 y 值 (TouchpadX 和 TouchpadY), 並知道使用者是否觸及 pad (IsTouchpadTouched), 以及是否按下觸控板 (IsTouchpadPressed).
* **SimpleHapticsController:** 控制器的 SimpleHapticsController API 可讓您檢查控制器的 haptics 功能, 也可讓您控制 haptic 的意見反應。

請注意, 針對兩個軸 (從下到上, 以及從左至右), 觸控板和操縱杆的範圍都是-1 到1。 類比觸發程式的範圍 (使用 SpatialInteractionSourceState:: SelectPressedValue 屬性存取) 的範圍為0到1。 值為1時, 與 IsSelectPressed 等於 true,任何其他值會與 IsSelectPressed (等於 false) 相互關聯。

## <a name="articulated-hand-tracking"></a>明確表述的手勢追蹤
Windows Mixed Reality API 可完整支援已示範的追蹤, 例如在 HoloLens 2 上。 有清楚的手勢追蹤可以用來在您的應用程式中執行直接操作和點對認可輸入模型。 它也可以用來撰寫完全自訂互動。

### <a name="hand-skeleton"></a>手形基本架構
明確表述的「追蹤」提供25個聯合基本架構, 可啟用許多不同類型的互動。  此基本架構提供5個接點給索引/中間/環形/小手指, 4 個接點用於 thumb, 而1個手腕接點。  手腕接點會作為階層的基礎。 下圖說明基本架構的版面配置。

![手形基本架構](images/hand-skeleton.png)

在大部分的情況下, 每個聯合都會根據它所代表的骨骼來命名。  因為每個聯合都有兩個骨骼, 所以我們會根據該位置的子系骨骼, 使用每個聯合的命名慣例。  子系骨骼會從手腕進一步定義為骨骼。  例如, "Index Proximal" 聯合包含 Index Proximal 骨骼的開始位置, 以及該骨骼的方向。  它不包含骨骼的結束位置。  如果您需要的話, 您可以從階層中的下一個聯合 (「索引中繼」聯合) 取得它。

除了25個階層式接點外, 系統還提供了一種 palm 聯合。  Palm 通常不會被視為骨架結構的一部分。  它只是用來取得手的整體位置和方向的便利方式。

每個聯合都會提供下列資訊:

| 名稱 | 描述 |
|--- |--- |
|位置 | 聯合的3D 位置, 適用于任何要求的座標系統。 |
|Orientation | 骨骼的3D 方向, 適用于任何要求的座標系統。 |
|半徑 | 在聯合位置與面板表面的距離。 適用于微調依賴手指寬度的直接互動或視覺效果。 |
|準確度 | 提供有關系統如何自信此聯合資訊的提示。 |

您可以透過[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)上的函式來存取手邊的基本架構資料。  函式稱為[TryGetHandPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygethandpose#Windows_UI_Input_Spatial_SpatialInteractionSourceState_TryGetHandPose), 它會傳回名為[HandPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose)的物件。  如果來源不支援明確表達的手, 則此函式會傳回 null。  一旦有了 HandPose, 您就可以使用您感興趣的聯合名稱來呼叫[TryGetJoint](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose.trygetjoint#Windows_Perception_People_HandPose_TryGetJoint_Windows_Perception_Spatial_SpatialCoordinateSystem_Windows_Perception_People_HandJointKind_Windows_Perception_People_JointPose__), 以取得目前的聯合資料。  資料會以[JointPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.jointpose)結構的形式傳回。  下列程式碼會取得索引手指秘訣的位置。 變數*currentState*代表[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)的實例。

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

### <a name="hand-mesh"></a>手形網格

明確 deformable 的手勢追蹤 API 允許完整的三角形網格。  此網格可以與手形基本架構即時 deform, 而且適用于視覺效果及先進的物理技術。  若要存取右手網格, 您必須先在[SpatialInteractionSource](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource)上呼叫[TryCreateHandMeshObserverAsync](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)來建立[HandMeshObserver](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver)物件。  這只需要針對每個來源執行一次, 通常是您第一次看到它時。  這表示每當手進入 FOV 時, 您都會呼叫此函式來建立 HandMeshObserver 物件。  請注意, 這是非同步函式, 因此您必須在這裡處理一些平行存取。  一旦可用, 您就可以呼叫[GetTriangleIndices](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver.gettriangleindices#Windows_Perception_People_HandMeshObserver_GetTriangleIndices_System_UInt16___)來要求三角形索引緩衝區的 HandMeshObserver 物件。  索引不會變更框架的框架, 因此您可以取得這一次, 並在來源的存留期內加以快取。  索引是以順時針的纏繞順序提供。

下列程式碼會啟動已卸離的 std:: thread 來建立網格觀察者, 並在網格觀察器可供使用之後, 將索引緩衝區解壓縮。  它會從名為*currentState*的變數開始, 這是代表追蹤的[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)實例。

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
啟動卸離的執行緒只是處理非同步呼叫的一個選項。  或者, 您可以使用C++/winrt 所支援的新[co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency)功能

一旦有了 HandMeshObserver 物件, 您就應該在其對應的 SpatialInteractionSource 為作用中的持續時間內保存它。  接著, 您可以藉由呼叫[GetVertexStateForPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver.getvertexstateforpose)並傳入[HandPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose)實例 (代表您想要使用頂點的姿勢), 將每個框架要求它提供代表手的最新頂點緩衝區。  緩衝區中的每個頂點都有位置和標準。  以下範例示範如何取得右手網格的目前頂點集。  就像之前一樣, *currentState*變數代表[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)的實例。

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

相對於基本架構接點, 右手邊網格 API 不允許您指定頂點的座標系統。  相反地, [HandMeshVertexState](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshvertexstate)會指定要在其中提供頂點的座標系統。  接著, 您可以藉由呼叫[TryGetTransformTo](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem.trygettransformto#Windows_Perception_Spatial_SpatialCoordinateSystem_TryGetTransformTo_Windows_Perception_Spatial_SpatialCoordinateSystem_)並指定所需的座標系統, 來取得網格轉換。  每當您使用頂點時, 都必須使用此網格轉換。  這種方法可減少 CPU 的額外負荷, 特別是當您只是為了轉譯目的而使用網格時。

## <a name="gaze-and-commit-composite-gestures"></a>注視和認可複合手勢
對於使用注視和認可輸入模型的應用程式, 特別是在 HoloLens (第一代) 上, 空間輸入 API 會提供選擇性的[SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) , 可用來啟用以 ' select ' 事件為基礎的複合手勢。  藉由將來自 SpatialInteractionManager 的互動路由至全息影像的 SpatialGestureRecognizer, 應用程式可以在手、語音和空間輸入裝置之間一致地偵測點分、保存、操作和流覽事件, 而不必處理按下的動作和會手動發行。

SpatialGestureRecognizer 只會在您要求的一組手勢之間執行最少的去除混淆。 例如, 如果您只需要點一下, 使用者只要按下滑鼠, 就可以按住其手指, 而且仍然會發生點碰。 如果您同時要求點一下並按住, 請在大約一秒後按住手指, 手勢將會升階為按住, 而且不會再出現點分。

若要使用 SpatialGestureRecognizer, 請處理 SpatialInteractionManager 的[InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected)事件, 並抓取該處公開的 SpatialPointerPose。 使用來自此姿勢的使用者前端光線, 與使用者環境中的全息和表面網格交集, 以判斷使用者要與誰互動。 然後, 使用[CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction)方法, 將事件引數中的 SpatialInteraction 路由至目標全息影像的 SpatialGestureRecognizer。 這會根據在建立時或由[TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings)在該辨識器上設定的[SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) , 開始解讀該互動。

在 HoloLens (第一代) 上, 互動和手勢通常會從使用者的眼中衍生其目標, 而不是嘗試直接在手中呈現或互動。 互動開始之後, 手的相對運動可能會用來控制手勢, 如同操作或導覽手勢。

## <a name="see-also"></a>另請參閱
* [DirectX 中的頭部和眼睛目光](gaze-in-directx.md)
* [直接操作輸入模型](direct-manipulation.md)
* [點對認可輸入模型](point-and-commit.md)
* [注視和認可輸入模型](gaze-and-commit.md)
* [運動控制器](motion-controllers.md)
