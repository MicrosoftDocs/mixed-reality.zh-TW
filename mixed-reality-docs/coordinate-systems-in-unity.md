---
title: Unity 中的座標系統
description: 瞭解如何在 Unity 中建立站上、中度、會議室和全球規模的混合現實體驗。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 座標系統，空間座標系統，僅限方向，固定規模，大規模，室內規模，世界級，360度，站，室內，房間，世界，縮放，位置，方向，Unity，錨點，空間錨點，世界錨點，世界鎖定，世界-鎖定，內文鎖定，內文鎖定，追蹤遺失，locatability，界限，recenter
ms.openlocfilehash: 36d74488b23587e5c89b40faf97921a10be7473b
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375765"
---
# <a name="coordinate-systems-in-unity"></a><span data-ttu-id="3a857-104">Unity 中的座標系統</span><span class="sxs-lookup"><span data-stu-id="3a857-104">Coordinate systems in Unity</span></span>

<span data-ttu-id="3a857-105">Windows Mixed Reality 支援各種[經驗調整](coordinate-systems.md)的應用程式，從僅限方向的應用程式，以及透過會議室規模應用程式來擴充的上移。</span><span class="sxs-lookup"><span data-stu-id="3a857-105">Windows Mixed Reality supports apps across a wide range of [experience scales](coordinate-systems.md), from orientation-only and seated-scale apps up through room-scale apps.</span></span> <span data-ttu-id="3a857-106">在 HoloLens 上，您可以進一步建立全球規模的應用程式，讓使用者不超過5計量，探索大樓的整個樓層。</span><span class="sxs-lookup"><span data-stu-id="3a857-106">On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.</span></span>

<span data-ttu-id="3a857-107">在 Unity 中建立混合現實體驗的第一個步驟，是要判斷您的應用程式將會以何種方式[調整](coordinate-systems.md)您的 app 目標。</span><span class="sxs-lookup"><span data-stu-id="3a857-107">Your first step in building a mixed reality experience in Unity is to determine which [experience scale](coordinate-systems.md) your app will target.</span></span>

## <a name="building-an-orientation-only-or-seated-scale-experience"></a><span data-ttu-id="3a857-108">建立僅限方向或固定規模的體驗</span><span class="sxs-lookup"><span data-stu-id="3a857-108">Building an orientation-only or seated-scale experience</span></span>

<span data-ttu-id="3a857-109">**命名空間：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="3a857-109">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="3a857-110">**類型：** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="3a857-110">**Type:** *XRDevice*</span></span>

<span data-ttu-id="3a857-111">若要建立**僅限方向**或**固定大小的體驗**，您必須將 Unity 設定為固定的追蹤空間類型。</span><span class="sxs-lookup"><span data-stu-id="3a857-111">To build an **orientation-only** or **seated-scale experience**, you must set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="3a857-112">這會設定 Unity 的全局座標系統，以追蹤[固定的參考框架](coordinate-systems.md#spatial-coordinate-systems)。</span><span class="sxs-lookup"><span data-stu-id="3a857-112">This sets Unity's world coordinate system to track the [stationary frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="3a857-113">在「固定」追蹤模式中，放在編輯器中的內容，就像是在相機的預設位置前方（[轉寄] 為-Z），會在應用程式啟動時顯示在使用者的前方。</span><span class="sxs-lookup"><span data-stu-id="3a857-113">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="3a857-114">**命名空間：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="3a857-114">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="3a857-115">**類型：** *InputTracking*</span><span class="sxs-lookup"><span data-stu-id="3a857-115">**Type:** *InputTracking*</span></span>

<span data-ttu-id="3a857-116">如需純**方向的體驗**，例如360度的影片檢視器（位置標頭更新會破壞此假像），您可以接著設定[XR。InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html)為 true：</span><span class="sxs-lookup"><span data-stu-id="3a857-116">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="3a857-117">針對**固定規模的體驗**，若要讓使用者稍後 recenter 已放置的來源，您可以呼叫[XR。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)方法：</span><span class="sxs-lookup"><span data-stu-id="3a857-117">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a><span data-ttu-id="3a857-118">建立大規模或會議室的體驗</span><span class="sxs-lookup"><span data-stu-id="3a857-118">Building a standing-scale or room-scale experience</span></span>

<span data-ttu-id="3a857-119">**命名空間：** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="3a857-119">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="3a857-120">**類型：** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="3a857-120">**Type:** *XRDevice*</span></span>

<span data-ttu-id="3a857-121">針對**大規模**或**會議室的體驗**，您將需要放置相對於樓層的內容。</span><span class="sxs-lookup"><span data-stu-id="3a857-121">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="3a857-122">您的使用者使用 **[空間階段](coordinate-systems.md#spatial-coordinate-systems)** （代表使用者定義的樓層層級原點和選擇性的房間界限），這是您在第一次執行期間設定的原因。</span><span class="sxs-lookup"><span data-stu-id="3a857-122">You reason about the user's floor using the **[spatial stage](coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="3a857-123">為確保 Unity 與其在樓層層級的全局座標系統運作，您可以將 Unity 設定為 RoomScale 追蹤空間類型，並確定設定成功：</span><span class="sxs-lookup"><span data-stu-id="3a857-123">To ensure that Unity is operating with its world coordinate system at floor-level, you can set Unity to the RoomScale tracking space type, and ensure that the set succeeds:</span></span>

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```
* <span data-ttu-id="3a857-124">如果 SetTrackingSpaceType 傳回 true，Unity 已成功切換其全局座標系統，以追蹤[參考的階段框架](coordinate-systems.md#spatial-coordinate-systems)。</span><span class="sxs-lookup"><span data-stu-id="3a857-124">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="3a857-125">如果 SetTrackingSpaceType 傳回 false，則 Unity 無法切換至參考的階段框架，可能是因為使用者尚未在其環境中設定。</span><span class="sxs-lookup"><span data-stu-id="3a857-125">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up even a floor in their environment.</span></span> <span data-ttu-id="3a857-126">這並不常見，但如果階段是在不同的房間內設定，而裝置已移至目前的房間，而沒有使用者設定新的階段，則可能會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="3a857-126">This is not common, but can happen if the stage was set up in a different room and the device was moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="3a857-127">一旦您的應用程式成功設定 RoomScale 追蹤空間類型，放置在 y = 0 平面上的內容就會出現在樓層上。</span><span class="sxs-lookup"><span data-stu-id="3a857-127">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="3a857-128">位於（0，0，0）的原點會是在室內設定期間使用者勇敢面對考驗的特定位置，其中-Z 代表在安裝期間所面臨的正向方向。</span><span class="sxs-lookup"><span data-stu-id="3a857-128">The origin at (0, 0, 0) will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>

<span data-ttu-id="3a857-129">**命名空間：** *UnityEngine。 XR*</span><span class="sxs-lookup"><span data-stu-id="3a857-129">**Namespace:** *UnityEngine.Experimental.XR*</span></span><br>
<span data-ttu-id="3a857-130">**類型：** *界限*</span><span class="sxs-lookup"><span data-stu-id="3a857-130">**Type:** *Boundary*</span></span>

<span data-ttu-id="3a857-131">在腳本程式碼中，您可以在上呼叫 TryGetGeometry 方法，以取得界限多邊形，並指定 TrackedArea 的界限類型。</span><span class="sxs-lookup"><span data-stu-id="3a857-131">In script code, you can then call the TryGetGeometry method on your the UnityEngine.Experimental.XR.Boundary type to get a boundary polygon, specifying a boundary type of TrackedArea.</span></span> <span data-ttu-id="3a857-132">如果使用者定義界限（您會取得頂點清單），您就知道可以安全地提供**會議室規模的體驗**給使用者，讓他們能在其中四處流覽您建立的場景。</span><span class="sxs-lookup"><span data-stu-id="3a857-132">If the user defined a boundary (you get back a list of vertices), you know it is safe to deliver a **room-scale experience** to the user, where they can walk around the scene you create.</span></span>

<span data-ttu-id="3a857-133">請注意，當使用者對邊界進行方法時，系統將會自動呈現界限。</span><span class="sxs-lookup"><span data-stu-id="3a857-133">Note that the system will automatically render the boundary when the user approaches it.</span></span> <span data-ttu-id="3a857-134">您的應用程式不需要使用此多邊形來呈現界限本身。</span><span class="sxs-lookup"><span data-stu-id="3a857-134">Your app does not need to use this polygon to render the boundary itself.</span></span> <span data-ttu-id="3a857-135">不過，您可以選擇使用此界限多邊形來配置場景物件，以確保使用者可以在不 teleporting 的情況下，實際觸及那些物件：</span><span class="sxs-lookup"><span data-stu-id="3a857-135">However, you may choose to lay out your scene objects using this boundary polygon, to ensure the user can physically reach those objects without teleporting:</span></span>

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="3a857-136">建立全球規模的體驗</span><span class="sxs-lookup"><span data-stu-id="3a857-136">Building a world-scale experience</span></span>

<span data-ttu-id="3a857-137">**命名空間：** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="3a857-137">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="3a857-138">**類型：** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="3a857-138">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="3a857-139">如需 HoloLens 的真實**全球化體驗**，讓使用者穿梭超過5計量，您將需要新的技術，超越用於會議室規模的經驗。</span><span class="sxs-lookup"><span data-stu-id="3a857-139">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="3a857-140">您將使用的一項重要技巧，就是建立[空間錨點](coordinate-systems.md#spatial-anchors)，以在實體世界中精確地鎖定全像位置的全息影像叢集，而不論使用者已漫遊的距離為何，然後[在後續的會話中再次尋找那些全息影像](coordinate-systems.md#spatial-anchor-persistence)。</span><span class="sxs-lookup"><span data-stu-id="3a857-140">One key technique you'll use is to create a [spatial anchor](coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, regardless of how far the user has roamed, and then [find those holograms again in later sessions](coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="3a857-141">在 Unity 中，您可以藉由將**WorldAnchor** Unity 元件新增至 GameObject 來建立空間錨點。</span><span class="sxs-lookup"><span data-stu-id="3a857-141">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="3a857-142">新增世界錨點</span><span class="sxs-lookup"><span data-stu-id="3a857-142">Adding a World Anchor</span></span>

<span data-ttu-id="3a857-143">若要新增世界錨點，請使用您想要錨定在現實世界中的轉換，在遊戲物件上呼叫 AddComponent<WorldAnchor>（）。</span><span class="sxs-lookup"><span data-stu-id="3a857-143">To add a world anchor, call AddComponent<WorldAnchor>() on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="3a857-144">這樣就完成了！</span><span class="sxs-lookup"><span data-stu-id="3a857-144">That's it!</span></span> <span data-ttu-id="3a857-145">這個遊戲物件現在會錨定在實體世界中的目前位置，您可能會看到其 Unity world 座標會稍微調整一段時間，以確保實體對齊。</span><span class="sxs-lookup"><span data-stu-id="3a857-145">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="3a857-146">使用[持續](persistence-in-unity.md)性，以在未來的應用程式會話中再次尋找此錨定位置。</span><span class="sxs-lookup"><span data-stu-id="3a857-146">Use [persistence](persistence-in-unity.md) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="3a857-147">移除世界錨點</span><span class="sxs-lookup"><span data-stu-id="3a857-147">Removing a World Anchor</span></span>

<span data-ttu-id="3a857-148">如果您不想再讓 GameObject 鎖定到實體世界位置，而不打算將它移到此框架，則您可以直接在「世界錨點」元件上呼叫摧毀。</span><span class="sxs-lookup"><span data-stu-id="3a857-148">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="3a857-149">如果您想要移動 GameObject 此框架，您必須改為呼叫 DestroyImmediate。</span><span class="sxs-lookup"><span data-stu-id="3a857-149">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="3a857-150">移動世界錨定的 GameObject</span><span class="sxs-lookup"><span data-stu-id="3a857-150">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="3a857-151">當世界錨點在 GameObject 時，無法移動。</span><span class="sxs-lookup"><span data-stu-id="3a857-151">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="3a857-152">如果您需要將 GameObject 移到此框架，您必須：</span><span class="sxs-lookup"><span data-stu-id="3a857-152">If you need to move the GameObject this frame, you need to:</span></span>
1. <span data-ttu-id="3a857-153">DestroyImmediate 世界錨點元件</span><span class="sxs-lookup"><span data-stu-id="3a857-153">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="3a857-154">移動 GameObject</span><span class="sxs-lookup"><span data-stu-id="3a857-154">Move the GameObject</span></span>
3. <span data-ttu-id="3a857-155">將新的「世界錨點」元件新增至 GameObject。</span><span class="sxs-lookup"><span data-stu-id="3a857-155">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="3a857-156">處理 Locatability 變更</span><span class="sxs-lookup"><span data-stu-id="3a857-156">Handling Locatability Changes</span></span>

<span data-ttu-id="3a857-157">實體世界中的某個時間點可能不會有 WorldAnchor。</span><span class="sxs-lookup"><span data-stu-id="3a857-157">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="3a857-158">如果發生這種情況，Unity 將不會更新已錨定物件的轉換。</span><span class="sxs-lookup"><span data-stu-id="3a857-158">If that occurs, Unity will not be updating the transform of the anchored object.</span></span> <span data-ttu-id="3a857-159">當應用程式正在執行時，這也會變更。</span><span class="sxs-lookup"><span data-stu-id="3a857-159">This also can change while an app is running.</span></span> <span data-ttu-id="3a857-160">無法處理 locatability 中的變更，會導致物件不會出現在世界中正確的實體位置。</span><span class="sxs-lookup"><span data-stu-id="3a857-160">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="3a857-161">若要收到有關 locatability 變更的通知：</span><span class="sxs-lookup"><span data-stu-id="3a857-161">To be notified about locatability changes:</span></span>
1. <span data-ttu-id="3a857-162">訂閱 OnTrackingChanged 事件</span><span class="sxs-lookup"><span data-stu-id="3a857-162">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="3a857-163">處理事件</span><span class="sxs-lookup"><span data-stu-id="3a857-163">Handle the event</span></span>

<span data-ttu-id="3a857-164">每當基礎空間錨點在要找出的狀態與未被定位之間變更時，就會呼叫**OnTrackingChanged**事件。</span><span class="sxs-lookup"><span data-stu-id="3a857-164">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="3a857-165">然後處理事件：</span><span class="sxs-lookup"><span data-stu-id="3a857-165">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="3a857-166">有時錨點會立即找到。</span><span class="sxs-lookup"><span data-stu-id="3a857-166">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="3a857-167">在此情況下，當 AddComponent<WorldAnchor>（）傳回時，錨點的這個 isLocated 屬性會設定為 true。</span><span class="sxs-lookup"><span data-stu-id="3a857-167">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="3a857-168">因此，將不會觸發 OnTrackingChanged 事件。</span><span class="sxs-lookup"><span data-stu-id="3a857-168">As a result, the OnTrackingChanged event will not be triggered.</span></span> <span data-ttu-id="3a857-169">全新的模式是在附加錨點之後，以初始 IsLocated 狀態呼叫 OnTrackingChanged 處理常式。</span><span class="sxs-lookup"><span data-stu-id="3a857-169">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a><span data-ttu-id="3a857-170">跨裝置共用錨點</span><span class="sxs-lookup"><span data-stu-id="3a857-170">Sharing anchors across devices</span></span>

<span data-ttu-id="3a857-171">您可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a>，從本機 WorldAnchor 建立長期雲端錨點，然後您的應用程式可以在多個 HoloLens、IOS 和 Android 裝置上尋找。</span><span class="sxs-lookup"><span data-stu-id="3a857-171">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="3a857-172">藉由共用多個裝置上的通用空間錨點，每個使用者都可以看到相對於相同實體位置中的錨點所呈現的內容。</span><span class="sxs-lookup"><span data-stu-id="3a857-172">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="3a857-173">這可提供即時共用體驗。</span><span class="sxs-lookup"><span data-stu-id="3a857-173">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="3a857-174">若要開始在 Unity 中建立共用體驗，請嘗試5分鐘的<a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 空間錨點 Unity 快速入門</a>。</span><span class="sxs-lookup"><span data-stu-id="3a857-174">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="3a857-175">當您使用 Azure 空間錨點啟動並執行之後，就可以<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中建立和尋找錨點</a>。</span><span class="sxs-lookup"><span data-stu-id="3a857-175">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="3a857-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a857-176">See Also</span></span>
* [<span data-ttu-id="3a857-177">經驗調整</span><span class="sxs-lookup"><span data-stu-id="3a857-177">Experience scales</span></span>](coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="3a857-178">空間階段</span><span class="sxs-lookup"><span data-stu-id="3a857-178">Spatial stage</span></span>](coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="3a857-179">Unity 中的追蹤遺失</span><span class="sxs-lookup"><span data-stu-id="3a857-179">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="3a857-180">空間錨點</span><span class="sxs-lookup"><span data-stu-id="3a857-180">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="3a857-181">Unity 中的持續性</span><span class="sxs-lookup"><span data-stu-id="3a857-181">Persistence in Unity</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="3a857-182">Unity 中的共用體驗</span><span class="sxs-lookup"><span data-stu-id="3a857-182">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
* <span data-ttu-id="3a857-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="3a857-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="3a857-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">適用于 Unity 的 Azure 空間錨點 SDK</a></span><span class="sxs-lookup"><span data-stu-id="3a857-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>