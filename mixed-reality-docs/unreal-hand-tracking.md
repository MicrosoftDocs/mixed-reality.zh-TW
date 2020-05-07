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
# <a name="hand-tracking"></a><span data-ttu-id="91095-104">手動追蹤</span><span class="sxs-lookup"><span data-stu-id="91095-104">Hand Tracking</span></span>

<span data-ttu-id="91095-105">「手追蹤」系統使用個人的手掌和手指作為 Unreal 的輸入。</span><span class="sxs-lookup"><span data-stu-id="91095-105">The hand tracking system uses a person’s palms and fingers as input to Unreal.</span></span> <span data-ttu-id="91095-106">開發人員可以取得每個手指的位置和旋轉、整個 palm，甚至是在自己的程式碼中使用的手勢。</span><span class="sxs-lookup"><span data-stu-id="91095-106">A developer can get every finger’s position and rotation, the entire palm, and even hand gestures to use in their own code.</span></span> 

## <a name="hand-pose"></a><span data-ttu-id="91095-107">手姿勢</span><span class="sxs-lookup"><span data-stu-id="91095-107">Hand Pose</span></span>

<span data-ttu-id="91095-108">開發人員可以使用這種方式，追蹤作用中使用者的手和手指做為輸入。</span><span class="sxs-lookup"><span data-stu-id="91095-108">Using the hand pose, developers can track the hands and fingers of the active user as input.</span></span> <span data-ttu-id="91095-109">這個系統是透過藍圖和 c + + 公開。</span><span class="sxs-lookup"><span data-stu-id="91095-109">This system is exposed through both Blueprints and C++.</span></span> <span data-ttu-id="91095-110">技術詳細資料位於對應的 WinRT 類別中。 [HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose)這個 Unreal API 會以 Unreal 的座標系統格式提供資料，而刻度則會使用 Unreal 引擎 synchronised。</span><span class="sxs-lookup"><span data-stu-id="91095-110">Technical details are in the corresponding WinRT class [Windows.Perception.People.HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) This Unreal API provides the data in the format of Unreal’s coordinate system and ticks are synchronised with the Unreal Engine.</span></span>

### <a name="enum"></a><span data-ttu-id="91095-111">例舉</span><span class="sxs-lookup"><span data-stu-id="91095-111">Enum</span></span>

<span data-ttu-id="91095-112">EWMRHandKeypoint 描述手的骨骼階層。</span><span class="sxs-lookup"><span data-stu-id="91095-112">EWMRHandKeypoint describes the Hand’s bone hierarchy.</span></span> 

<span data-ttu-id="91095-113">幅</span><span class="sxs-lookup"><span data-stu-id="91095-113">Blueprint:</span></span>

![右手 Keypoint 的 BP](images/unreal/hand-keypoint-bp.png)
 
<span data-ttu-id="91095-115">C++：</span><span class="sxs-lookup"><span data-stu-id="91095-115">C++:</span></span>
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

<span data-ttu-id="91095-117">數值可以在 HandJointKind 的資料表中找到[。](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind)</span><span class="sxs-lookup"><span data-stu-id="91095-117">The numerical values can be found in the table [Windows.Perception.People.HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind)</span></span>
 
### <a name="functions"></a><span data-ttu-id="91095-118">函式</span><span class="sxs-lookup"><span data-stu-id="91095-118">Functions</span></span>

<span data-ttu-id="91095-119">若要在藍圖中使用「手追蹤」功能，請開啟「手動追蹤/Windows Mixed Reality」</span><span class="sxs-lookup"><span data-stu-id="91095-119">To use hand tracking functions in Blueprints, open "Hand Tracking/Windows Mixed Reality"</span></span>

![右手追蹤 BP](images/unreal/hand-tracking-bp.png)

<span data-ttu-id="91095-121">若為 c + + 函式，請包含 "WindowsMixedRealityHandTrackingFunctionLibrary"</span><span class="sxs-lookup"><span data-stu-id="91095-121">For C++ functions, include "WindowsMixedRealityHandTrackingFunctionLibrary.h"</span></span>

<span data-ttu-id="91095-122">最佳</span><span class="sxs-lookup"><span data-stu-id="91095-122">BP:</span></span>

![支援手動追蹤 BP](images/unreal/supports-hand-tracking-bp.png)
 
<span data-ttu-id="91095-124">C++：</span><span class="sxs-lookup"><span data-stu-id="91095-124">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

<span data-ttu-id="91095-125">如果裝置支援手動追蹤，則傳回 true，如果無法使用手動追蹤，則傳回 false。</span><span class="sxs-lookup"><span data-stu-id="91095-125">Returns true if hand tracking is supported on the device, false if hand tracking is not available.</span></span>

<span data-ttu-id="91095-126">最佳</span><span class="sxs-lookup"><span data-stu-id="91095-126">BP:</span></span>

![取得手聯合轉換](images/unreal/get-hand-joint-transform.png)
 
<span data-ttu-id="91095-128">C++：</span><span class="sxs-lookup"><span data-stu-id="91095-128">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="91095-129">此函式會傳回手的空間資料。</span><span class="sxs-lookup"><span data-stu-id="91095-129">This function returns spatial data of the hand.</span></span> <span data-ttu-id="91095-130">資料會更新框架內的每個畫面格，傳回的值會被快取。</span><span class="sxs-lookup"><span data-stu-id="91095-130">The data updates every frame, inside a frame the returned values are cached.</span></span> <span data-ttu-id="91095-131">基於效能考慮，不建議在此函式上使用繁重的邏輯。</span><span class="sxs-lookup"><span data-stu-id="91095-131">It is not recommended to have heavy logic on this function for performance reasons.</span></span> 

* <span data-ttu-id="91095-132">**手形**–使用者的手中，可以是向左或向右</span><span class="sxs-lookup"><span data-stu-id="91095-132">**Hand** – hand of the user, may be left or right</span></span>
* <span data-ttu-id="91095-133">**Keypoint** –手的骨骼。</span><span class="sxs-lookup"><span data-stu-id="91095-133">**Keypoint** – the bone of the hand.</span></span> 
* <span data-ttu-id="91095-134">**轉換**–骨骼基底的座標和方向。</span><span class="sxs-lookup"><span data-stu-id="91095-134">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="91095-135">若要取得骨骼結尾的轉換資料，應要求下一個骨骼的基底。</span><span class="sxs-lookup"><span data-stu-id="91095-135">To get the transform data for the end of a bone, the base of the next bone should be requested.</span></span> <span data-ttu-id="91095-136">一個特殊的 Tip 骨骼會提供 distal 的結尾。</span><span class="sxs-lookup"><span data-stu-id="91095-136">A special Tip bone gives end of distal.</span></span> 
* <span data-ttu-id="91095-137">**半徑**：骨骼基底的半徑。</span><span class="sxs-lookup"><span data-stu-id="91095-137">**Radius** — radius of the base of the bone.</span></span>
* <span data-ttu-id="91095-138">傳回**值**-如果已追蹤此框架，則為 true，如果不追蹤骨骼，則為 false。</span><span class="sxs-lookup"><span data-stu-id="91095-138">**Return Value** — true if the bone is tracked this frame, false if the bone is not tracked.</span></span>

## <a name="hand-live-link-animation"></a><span data-ttu-id="91095-139">手上線連結動畫</span><span class="sxs-lookup"><span data-stu-id="91095-139">Hand Live Link Animation</span></span>
<span data-ttu-id="91095-140">使用即時連結外掛程式，即可對動畫公開手上的姿勢。</span><span class="sxs-lookup"><span data-stu-id="91095-140">Hand poses are exposed to Animation using the Live Link plugin.</span></span> <span data-ttu-id="91095-141">[這裡](https://docs.unrealengine.com/en-US/Engine/Animation/LiveLinkPlugin/index.html)有外掛程式檔</span><span class="sxs-lookup"><span data-stu-id="91095-141">The plugin documentation is [here](https://docs.unrealengine.com/en-US/Engine/Animation/LiveLinkPlugin/index.html)</span></span>

<span data-ttu-id="91095-142">如果已啟用 [Windows Mixed Reality] 和 [即時連結] 外掛程式，請移至 [**視窗] > [即時連結**] 以開啟 [即時連結編輯器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="91095-142">If the Windows Mixed Reality and Live Link plugins are enabled, go to **Window > Live Link** to open the Live Link editor window.</span></span> <span data-ttu-id="91095-143">按一下 [ **+ 來源] 按鈕**，並啟用 Windows Mixed Reality 追蹤來源</span><span class="sxs-lookup"><span data-stu-id="91095-143">Click the **+ Source button** and enable Windows Mixed Reality Hand Tracking Source</span></span>

![即時連結來源](images/unreal/live-link-source.png)
 
<span data-ttu-id="91095-145">當您啟用來源並開啟任何動畫資產之後，動畫的 [預覽場景] 索引標籤會有下列其他選項（詳細資料位於 Unreal 的即時連結檔中，因為外掛程式處於搶鮮版（Beta），程式可能會在稍後變更）</span><span class="sxs-lookup"><span data-stu-id="91095-145">After you enable the source and open any animation asset, the Preview Scene tab of Animation will have the following additional options (the details are in Unreal’s Live Link documentation- as the plugin is in beta, the process may change later)</span></span>

![即時連結動畫](images/unreal/live-link-animation.png)
 
<span data-ttu-id="91095-147">手形動畫階層與 EWMRHandKeypoint 中的相同。</span><span class="sxs-lookup"><span data-stu-id="91095-147">The hand animation hierarchy is the same as in EWMRHandKeypoint.</span></span> <span data-ttu-id="91095-148">您可以使用 WindowsMixedRealityHandTrackingLiveLinkRemapAsset 來重定動畫的目標。</span><span class="sxs-lookup"><span data-stu-id="91095-148">Animation can be retargeted using WindowsMixedRealityHandTrackingLiveLinkRemapAsset.</span></span> 

![即時連結動畫2](images/unreal/live-link-animation2.png)
 
<span data-ttu-id="91095-150">它可以在編輯器中進行子類別化</span><span class="sxs-lookup"><span data-stu-id="91095-150">It can be subclassed in the editor</span></span>

![即時連結重新對應](images/unreal/live-link-remap.png)
 
## <a name="hand-mesh"></a><span data-ttu-id="91095-152">手形網格</span><span class="sxs-lookup"><span data-stu-id="91095-152">Hand Mesh</span></span>
<span data-ttu-id="91095-153">代表使用者手的網格。</span><span class="sxs-lookup"><span data-stu-id="91095-153">Mesh representing the user hands.</span></span> 

![手形網格](images/unreal/hand-mesh.png)
 
### <a name="how-to-enable-and-configure"></a><span data-ttu-id="91095-155">如何啟用和設定</span><span class="sxs-lookup"><span data-stu-id="91095-155">How to enable and configure</span></span>

<span data-ttu-id="91095-156">開發人員可以針對自己的目的，直接存取右手的網格。</span><span class="sxs-lookup"><span data-stu-id="91095-156">Developers can get direct access to hand meshes for their own purposes.</span></span> <span data-ttu-id="91095-157">必須在 ARSessionConfig： AR 設定-> World 對應中啟用此存取權，> 從追蹤的幾何產生網格資料。</span><span class="sxs-lookup"><span data-stu-id="91095-157">This access must be enabled in ARSessionConfig: AR Settings -> World Mapping -> Generate Mesh Data from Tracked Geometry.</span></span> 

<span data-ttu-id="91095-158">以下是網格的預設參數：</span><span class="sxs-lookup"><span data-stu-id="91095-158">Here are the default parameters for meshes:</span></span>

1.  <span data-ttu-id="91095-159">使用網格資料進行遮蔽</span><span class="sxs-lookup"><span data-stu-id="91095-159">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="91095-160">產生網格資料的衝突</span><span class="sxs-lookup"><span data-stu-id="91095-160">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="91095-161">產生網格資料的 Nav 網格</span><span class="sxs-lookup"><span data-stu-id="91095-161">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="91095-162">線上框中轉譯網格資料-debug 參數，會顯示產生的網格</span><span class="sxs-lookup"><span data-stu-id="91095-162">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="91095-163">針對混合的事實專案，這些參數值將用來做為空間對應網格和手寫預設值。</span><span class="sxs-lookup"><span data-stu-id="91095-163">For mixed reality projects, these parameter values will be used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="91095-164">開發人員可以在特定網格的 BP 或程式碼中變更它們。</span><span class="sxs-lookup"><span data-stu-id="91095-164">Developers can change them in BP or code for any particular mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="91095-165">C + + API 參考</span><span class="sxs-lookup"><span data-stu-id="91095-165">C++ API Reference</span></span> 
```cpp
enum class EARObjectClassification : uint8
{
// other types 
    HandMesh,
};
```

<span data-ttu-id="91095-166">此值是所有可追蹤物件之間的右手網格。</span><span class="sxs-lookup"><span data-stu-id="91095-166">This value is the hand mesh among all trackable objects.</span></span>

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

<span data-ttu-id="91095-167">當系統偵測到任何可追蹤物件（包括手形網格）時，就會呼叫這些委派。</span><span class="sxs-lookup"><span data-stu-id="91095-167">These delegates are called when the system detects any trackable object, including a hand mesh.</span></span> 
```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```
<span data-ttu-id="91095-168">委派的處理常式應該具有下列簽章：</span><span class="sxs-lookup"><span data-stu-id="91095-168">Handlers to the delegates should have the following signature:</span></span>
```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

<span data-ttu-id="91095-169">可以存取網格資料`UARTrackedGeometry::GetUnderlyingMesh`</span><span class="sxs-lookup"><span data-stu-id="91095-169">Mesh data can be accessed by `UARTrackedGeometry::GetUnderlyingMesh`</span></span>

### <a name="blueprint-api-reference"></a><span data-ttu-id="91095-170">藍圖 API 參考</span><span class="sxs-lookup"><span data-stu-id="91095-170">Blueprint API Reference</span></span>

<span data-ttu-id="91095-171">開發人員應該將 AR 可追蹤通知元件新增至藍圖執行者</span><span class="sxs-lookup"><span data-stu-id="91095-171">Developers should add an AR Trackable Notify Component to a Blueprint actor</span></span>

![ARTrackable 通知](images/unreal/ar-trackable-notify.png)
 
<span data-ttu-id="91095-173">然後移至元件的詳細資料</span><span class="sxs-lookup"><span data-stu-id="91095-173">Then go to the component’s details</span></span> 

![ARTrackable 通知2](images/unreal/ar-trackable-notify2.png)
 
<span data-ttu-id="91095-175">在新增/更新/移除追蹤的幾何上，使用如下所示的程式碼覆寫：</span><span class="sxs-lookup"><span data-stu-id="91095-175">And overwrite On Add/Update/Remove Tracked Geometry with code like the below:</span></span>

![ARTrackable 時通知](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a><span data-ttu-id="91095-177">手寫光線</span><span class="sxs-lookup"><span data-stu-id="91095-177">Hand Rays</span></span>

<span data-ttu-id="91095-178">開發人員可以使用右手光線做為指標裝置。</span><span class="sxs-lookup"><span data-stu-id="91095-178">Developers can use a hand ray as a pointing device.</span></span> <span data-ttu-id="91095-179">系統可在 c + + 和藍圖中取得。</span><span class="sxs-lookup"><span data-stu-id="91095-179">The system is available in C++ and Blueprint.</span></span> <span data-ttu-id="91095-180">技術上來說，它會公開[SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) 。</span><span class="sxs-lookup"><span data-stu-id="91095-180">Technically it exposes [Windows.UI.Input.Spatial.SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose)</span></span>

<span data-ttu-id="91095-181">值得一提的是，由於所有函式的結果都會變更每個框架，因此全部都可供呼叫。</span><span class="sxs-lookup"><span data-stu-id="91095-181">It’s important to mention that since the results of all the functions changes every frame, they are all made callable.</span></span> <span data-ttu-id="91095-182">如需有關單純的 vs 非純虛擬或[可](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)呼叫函式的詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="91095-182">For more information about pure vs impure or callable functions, see [that](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)</span></span>

<span data-ttu-id="91095-183">針對藍圖，請開啟「Windows Mixed Reality HMD」</span><span class="sxs-lookup"><span data-stu-id="91095-183">For Blueprint open “Windows Mixed Reality HMD”</span></span>

![手型光線 BP](images/unreal/hand-rays-bp.png)
 
<span data-ttu-id="91095-185">C + + 包含 "WindowsMixedRealityFunctionLibrary"</span><span class="sxs-lookup"><span data-stu-id="91095-185">For C++ include "WindowsMixedRealityFunctionLibrary.h"</span></span>

### <a name="enum"></a><span data-ttu-id="91095-186">例舉</span><span class="sxs-lookup"><span data-stu-id="91095-186">Enum</span></span>

![輸入控制器按鈕](images/unreal/input-controller-buttons.png)
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```
* <span data-ttu-id="91095-188">**選取**-–使用者觸發的選取事件，可以在 HoloLens 2 中由 airtap 或注視和認可觸發。</span><span class="sxs-lookup"><span data-stu-id="91095-188">**Select** -– User triggered Select event, which can be triggered in HoloLens 2 by airtap or gaze and commit.</span></span> <span data-ttu-id="91095-189">另一個觸發此事件的方法是說「Select」。</span><span class="sxs-lookup"><span data-stu-id="91095-189">Another way to trigger this event is to say “Select”.</span></span> 
* <span data-ttu-id="91095-190">**抓住**-–使用者觸發的「抓住事件」，這是在 HoloLens 2 中藉由關閉全息型的使用者手指來觸發。</span><span class="sxs-lookup"><span data-stu-id="91095-190">**Grasp** -– User triggered Grasp event, which is triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span> 
```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```
* <span data-ttu-id="91095-191">**NotTracked** –-不顯示手</span><span class="sxs-lookup"><span data-stu-id="91095-191">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="91095-192">已**追蹤**–-完全追蹤手</span><span class="sxs-lookup"><span data-stu-id="91095-192">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="91095-193">結構</span><span class="sxs-lookup"><span data-stu-id="91095-193">Struct</span></span>

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
* <span data-ttu-id="91095-195">**原點**–手的原點</span><span class="sxs-lookup"><span data-stu-id="91095-195">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="91095-196">**方向**–右手方向</span><span class="sxs-lookup"><span data-stu-id="91095-196">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="91095-197">**向上**–向上向量</span><span class="sxs-lookup"><span data-stu-id="91095-197">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="91095-198">**方向**–方向四元數</span><span class="sxs-lookup"><span data-stu-id="91095-198">**Orientation** – orientation quaternion</span></span> 
* <span data-ttu-id="91095-199">**追蹤狀態**–目前的追蹤狀態</span><span class="sxs-lookup"><span data-stu-id="91095-199">**Tracking Status** – current tracking status</span></span>

### <a name="functions"></a><span data-ttu-id="91095-200">函式</span><span class="sxs-lookup"><span data-stu-id="91095-200">Functions</span></span>

<span data-ttu-id="91095-201">所有的函式都應該可在每個畫面格上呼叫，以進行連續監視。</span><span class="sxs-lookup"><span data-stu-id="91095-201">All the functions should be callable on every frame for continuous monitoring.</span></span> 

![取得指標姿勢資訊](images/unreal/get-pointer-pose-info.png)
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```
<span data-ttu-id="91095-203">函式會傳回此框架中有關光線方向的完整資訊。</span><span class="sxs-lookup"><span data-stu-id="91095-203">The function returns the full information about the hand ray direction in this frame.</span></span> 

![為 Grasped BP](images/unreal/is-grasped-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
<span data-ttu-id="91095-205">如果手在此框架中 grasped，則傳回 true。</span><span class="sxs-lookup"><span data-stu-id="91095-205">Returns true if the hand is grasped in this frame.</span></span> 

![為選取按下的 BP](images/unreal/is-select-pressed-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```
<span data-ttu-id="91095-207">如果使用者在此框架中觸發了 Select，則傳回 true。</span><span class="sxs-lookup"><span data-stu-id="91095-207">Returns true if the user triggered Select in this frame.</span></span>

![已按下按鈕的 BP](images/unreal/is-button-clicked-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```
<span data-ttu-id="91095-209">如果在此框架中觸發事件/按鈕，則傳回 true。</span><span class="sxs-lookup"><span data-stu-id="91095-209">Returns true if the event/button is triggered in this frame.</span></span>

![取得控制器追蹤狀態 BP](images/unreal/get-controller-tracking-status-bp.png)
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
<span data-ttu-id="91095-211">傳回此框架中的追蹤狀態。</span><span class="sxs-lookup"><span data-stu-id="91095-211">Returns the tracking status in this frame.</span></span>

## <a name="gestures"></a><span data-ttu-id="91095-212">軌跡</span><span class="sxs-lookup"><span data-stu-id="91095-212">Gestures</span></span>

<span data-ttu-id="91095-213">Hololens 2 可以追蹤空間手勢。</span><span class="sxs-lookup"><span data-stu-id="91095-213">The Hololens 2 can track spatial gestures.</span></span> <span data-ttu-id="91095-214">這些手勢的詳細資料[是開發人員可以將其](https://docs.microsoft.com/hololens/hololens2-basic-usage)視為其混合現實應用程式的輸入。</span><span class="sxs-lookup"><span data-stu-id="91095-214">Details about these gestures are [here](https://docs.microsoft.com/hololens/hololens2-basic-usage) A developer can capture them as input to their mixed reality application.</span></span> 

<span data-ttu-id="91095-215">C + + 函式為 "WindowsMixedRealitySpatialInputFunctionLibrary"</span><span class="sxs-lookup"><span data-stu-id="91095-215">The C++ function is in "WindowsMixedRealitySpatialInputFunctionLibrary.h"</span></span>

<span data-ttu-id="91095-216">藍圖函數位于 Windows Mixed Reality 空間輸入</span><span class="sxs-lookup"><span data-stu-id="91095-216">The Blueprint function is in Windows Mixed Reality Spatial Input</span></span>

![捕獲手勢](images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="91095-218">例舉</span><span class="sxs-lookup"><span data-stu-id="91095-218">Enum</span></span>

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
<span data-ttu-id="91095-220">此列舉描述空間軸手勢。</span><span class="sxs-lookup"><span data-stu-id="91095-220">This enum describes spatial axis gestures.</span></span> <span data-ttu-id="91095-221">您可以在[這裡](holograms-211.md)閱讀相關資訊</span><span class="sxs-lookup"><span data-stu-id="91095-221">You can read about them [here](holograms-211.md)</span></span>

### <a name="function"></a><span data-ttu-id="91095-222">函式</span><span class="sxs-lookup"><span data-stu-id="91095-222">Function</span></span>

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
<span data-ttu-id="91095-224">函式會啟用和停用手勢的捕捉。</span><span class="sxs-lookup"><span data-stu-id="91095-224">The function enables and disables capturing of gestures.</span></span> <span data-ttu-id="91095-225">啟用的手勢會引發輸入事件。</span><span class="sxs-lookup"><span data-stu-id="91095-225">The enabled gestures fire input events.</span></span> <span data-ttu-id="91095-226">如果啟用手勢 capture 成功，它會傳回 true，如果發生錯誤則傳回 false。</span><span class="sxs-lookup"><span data-stu-id="91095-226">It returns true if enabling gesture capture succeeded and false if there's an error.</span></span>
<span data-ttu-id="91095-227">主要事件</span><span class="sxs-lookup"><span data-stu-id="91095-227">Key Events</span></span>

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
<span data-ttu-id="91095-230">如果已啟用手勢，事件就會開始引發。</span><span class="sxs-lookup"><span data-stu-id="91095-230">If the gesture is enabled, the events begin firing.</span></span> 

