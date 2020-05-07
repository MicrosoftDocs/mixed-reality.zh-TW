---
title: Unreal 中的右手追蹤
description: 說明如何在 Unreal 中使用手動追蹤
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、手勢追蹤
ms.openlocfilehash: 3f7f4dd1eb62cb707eaaf8632a2ba3c280a4ac31
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835389"
---
# <a name="hand-tracking"></a>手動追蹤

「手追蹤」系統使用個人的手掌和手指作為 Unreal 的輸入。 開發人員可以取得每個手指的位置和旋轉、整個 palm，甚至是在自己的程式碼中使用的手勢。 

## <a name="hand-pose"></a>手姿勢

開發人員可以使用這種方式，追蹤作用中使用者的手和手指做為輸入。 這個系統是透過藍圖和 c + + 公開。 技術詳細資料位於對應的 WinRT 類別中。 [HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose)這個 Unreal API 會以 Unreal 的座標系統格式提供資料，而刻度則會使用 Unreal 引擎 synchronised。

### <a name="enum"></a>例舉

EWMRHandKeypoint 描述手的骨骼階層。 

幅

![右手 Keypoint 的 BP](images/unreal/hand-keypoint-bp.png)
 
C++：
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

![手形基本架構](images/hand-skeleton.png)

數值可以在 HandJointKind 的資料表中找到[。](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind)
 
### <a name="functions"></a>函式

若要在藍圖中使用「手追蹤」功能，請開啟「手動追蹤/Windows Mixed Reality」

![右手追蹤 BP](images/unreal/hand-tracking-bp.png)

若為 c + + 函式，請包含 "WindowsMixedRealityHandTrackingFunctionLibrary"

最佳

![支援手動追蹤 BP](images/unreal/supports-hand-tracking-bp.png)
 
C++：
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

如果裝置支援手動追蹤，則傳回 true，如果無法使用手動追蹤，則傳回 false。

最佳

![取得手聯合轉換](images/unreal/get-hand-joint-transform.png)
 
C++：
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

此函式會傳回手的空間資料。 資料會更新框架內的每個畫面格，傳回的值會被快取。 基於效能考慮，不建議在此函式上使用繁重的邏輯。 

* **手形**–使用者的手中，可以是向左或向右
* **Keypoint** –手的骨骼。 
* **轉換**–骨骼基底的座標和方向。 若要取得骨骼結尾的轉換資料，應要求下一個骨骼的基底。 一個特殊的 Tip 骨骼會提供 distal 的結尾。 
* **半徑**：骨骼基底的半徑。
* 傳回**值**-如果已追蹤此框架，則為 true，如果不追蹤骨骼，則為 false。

## <a name="hand-live-link-animation"></a>手上線連結動畫
使用即時連結外掛程式，即可對動畫公開手上的姿勢。 [這裡](https://docs.unrealengine.com/en-US/Engine/Animation/LiveLinkPlugin/index.html)有外掛程式檔

如果已啟用 [Windows Mixed Reality] 和 [即時連結] 外掛程式，請移至 [**視窗] > [即時連結**] 以開啟 [即時連結編輯器] 視窗。 按一下 [ **+ 來源] 按鈕**，並啟用 Windows Mixed Reality 追蹤來源

![即時連結來源](images/unreal/live-link-source.png)
 
當您啟用來源並開啟任何動畫資產之後，動畫的 [預覽場景] 索引標籤會有下列其他選項（詳細資料位於 Unreal 的即時連結檔中，因為外掛程式處於搶鮮版（Beta），程式可能會在稍後變更）

![即時連結動畫](images/unreal/live-link-animation.png)
 
手形動畫階層與 EWMRHandKeypoint 中的相同。 您可以使用 WindowsMixedRealityHandTrackingLiveLinkRemapAsset 來重定動畫的目標。 

![即時連結動畫2](images/unreal/live-link-animation2.png)
 
它可以在編輯器中進行子類別化

![即時連結重新對應](images/unreal/live-link-remap.png)
 
## <a name="hand-mesh"></a>手形網格
代表使用者手的網格。 

![手形網格](images/unreal/hand-mesh.png)
 
### <a name="how-to-enable-and-configure"></a>如何啟用和設定

開發人員可以針對自己的目的，直接存取右手的網格。 必須在 ARSessionConfig： AR 設定-> World 對應中啟用此存取權，> 從追蹤的幾何產生網格資料。 

以下是網格的預設參數：

1.  使用網格資料進行遮蔽
2.  產生網格資料的衝突
3.  產生網格資料的 Nav 網格
4.  線上框中轉譯網格資料-debug 參數，會顯示產生的網格

針對混合的事實專案，這些參數值將用來做為空間對應網格和手寫預設值。 開發人員可以在特定網格的 BP 或程式碼中變更它們。

### <a name="c-api-reference"></a>C + + API 參考 
```cpp
enum class EARObjectClassification : uint8
{
// other types 
    HandMesh,
};
```

此值是所有可追蹤物件之間的右手網格。

```cpp
class FARSupportInterface 
{
public:
// other params 
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

當系統偵測到任何可追蹤物件（包括手形網格）時，就會呼叫這些委派。 
```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```
委派的處理常式應該具有下列簽章：
```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

可以存取網格資料`UARTrackedGeometry::GetUnderlyingMesh`

### <a name="blueprint-api-reference"></a>藍圖 API 參考

開發人員應該將 AR 可追蹤通知元件新增至藍圖執行者

![ARTrackable 通知](images/unreal/ar-trackable-notify.png)
 
然後移至元件的詳細資料 

![ARTrackable 通知2](images/unreal/ar-trackable-notify2.png)
 
在新增/更新/移除追蹤的幾何上，使用如下所示的程式碼覆寫：

![ARTrackable 時通知](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a>手寫光線

開發人員可以使用右手光線做為指標裝置。 系統可在 c + + 和藍圖中取得。 技術上來說，它會公開[SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) 。

值得一提的是，由於所有函式的結果都會變更每個框架，因此全部都可供呼叫。 如需有關單純的 vs 非純虛擬或[可](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)呼叫函式的詳細資訊，請參閱

針對藍圖，請開啟「Windows Mixed Reality HMD」

![手型光線 BP](images/unreal/hand-rays-bp.png)
 
C + + 包含 "WindowsMixedRealityFunctionLibrary"

### <a name="enum"></a>例舉

![輸入控制器按鈕](images/unreal/input-controller-buttons.png)
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```
* **選取**-–使用者觸發的選取事件，可以在 HoloLens 2 中由 airtap 或注視和認可觸發。 另一個觸發此事件的方法是說「Select」。 
* **抓住**-–使用者觸發的「抓住事件」，這是在 HoloLens 2 中藉由關閉全息型的使用者手指來觸發。 
```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```
* **NotTracked** –-不顯示手
* 已**追蹤**–-完全追蹤手

### <a name="struct"></a>結構

![指標姿勢資訊 BP](images/unreal/pointer-pose-info-bp.png)
```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```
* **原點**–手的原點
* **方向**–右手方向
* **向上**–向上向量
* **方向**–方向四元數 
* **追蹤狀態**–目前的追蹤狀態

### <a name="functions"></a>函式

所有的函式都應該可在每個畫面格上呼叫，以進行連續監視。 

![取得指標姿勢資訊](images/unreal/get-pointer-pose-info.png)
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```
函式會傳回此框架中有關光線方向的完整資訊。 

![為 Grasped BP](images/unreal/is-grasped-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
如果手在此框架中 grasped，則傳回 true。 

![為選取按下的 BP](images/unreal/is-select-pressed-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```
如果使用者在此框架中觸發了 Select，則傳回 true。

![已按下按鈕的 BP](images/unreal/is-button-clicked-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```
如果在此框架中觸發事件/按鈕，則傳回 true。

![取得控制器追蹤狀態 BP](images/unreal/get-controller-tracking-status-bp.png)
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
傳回此框架中的追蹤狀態。

## <a name="gestures"></a>軌跡

Hololens 2 可以追蹤空間手勢。 這些手勢的詳細資料[是開發人員可以將其](https://docs.microsoft.com/hololens/hololens2-basic-usage)視為其混合現實應用程式的輸入。 

C + + 函式為 "WindowsMixedRealitySpatialInputFunctionLibrary"

藍圖函數位于 Windows Mixed Reality 空間輸入

![捕獲手勢](images/unreal/capture-gestures.png)

### <a name="enum"></a>例舉

![手勢類型](images/unreal/gesture-type.png)
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```
此列舉描述空間軸手勢。 您可以在[這裡](holograms-211.md)閱讀相關資訊

### <a name="function"></a>函式

![捕獲手勢 BP](images/unreal/capture-gestures-bp.png)
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```
函式會啟用和停用手勢的捕捉。 啟用的手勢會引發輸入事件。 如果啟用手勢 capture 成功，它會傳回 true，如果發生錯誤則傳回 false。
主要事件

![主要事件](images/unreal/key-events.png)

![主要事件2](images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```
如果已啟用手勢，事件就會開始引發。 

