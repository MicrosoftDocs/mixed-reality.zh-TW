---
title: 在 Unity 中的座標系統
description: 了解如何建置讓您輕鬆工作，釐、 聊天室擴展和全球規模的混合實境體驗，在 Unity 中。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 座標系統、 空間座標系統、 方向、 插入擴充槽級別、 常設-小數位數的空間-調整、 全球規模，360 度，插入擴充槽，常設、 聊天室、 世界、 可調整、 位置、 方向、 Unity、 錨點、 空間的錨點、 世界錨點，世界鎖定世界鎖定，以鎖定主體，主體鎖定，追蹤遺失，locatability，範圍中，recenter
ms.openlocfilehash: 36d74488b23587e5c89b40faf97921a10be7473b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2019
ms.locfileid: "59597106"
---
# <a name="coordinate-systems-in-unity"></a><span data-ttu-id="46355-104">在 Unity 中的座標系統</span><span class="sxs-lookup"><span data-stu-id="46355-104">Coordinate systems in Unity</span></span>

<span data-ttu-id="46355-105">Windows Mixed Reality 跨各種不同的支援應用程式[體驗標尺](coordinate-systems.md)，從僅限方向和插入擴充槽擴展應用程式向上透過空間調整應用程式。</span><span class="sxs-lookup"><span data-stu-id="46355-105">Windows Mixed Reality supports apps across a wide range of [experience scales](coordinate-systems.md), from orientation-only and seated-scale apps up through room-scale apps.</span></span> <span data-ttu-id="46355-106">上 HoloLens，您可以更進一步，和建置世界級應用程式，可讓使用者超過 5 公尺，逐步引導瀏覽整個樓層的建置和更新版本。</span><span class="sxs-lookup"><span data-stu-id="46355-106">On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.</span></span>

<span data-ttu-id="46355-107">建置在 Unity 中的混合的實境體驗的第一個步驟是判斷哪些[體驗擴展](coordinate-systems.md)應用程式目標。</span><span class="sxs-lookup"><span data-stu-id="46355-107">Your first step in building a mixed reality experience in Unity is to determine which [experience scale](coordinate-systems.md) your app will target.</span></span>

## <a name="building-an-orientation-only-or-seated-scale-experience"></a><span data-ttu-id="46355-108">建立僅限方向或插入擴充槽-小數位數的體驗</span><span class="sxs-lookup"><span data-stu-id="46355-108">Building an orientation-only or seated-scale experience</span></span>

<span data-ttu-id="46355-109">**命名空間：**  *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="46355-109">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="46355-110">**類型：**  *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="46355-110">**Type:** *XRDevice*</span></span>

<span data-ttu-id="46355-111">建置**僅限方向**或**插入擴充槽擴展經驗**，您必須設定 Unity 固定為追蹤的空間型別。</span><span class="sxs-lookup"><span data-stu-id="46355-111">To build an **orientation-only** or **seated-scale experience**, you must set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="46355-112">這會設定 Unity 的全局座標系統來追蹤[靜態參考座標系](coordinate-systems.md#spatial-coordinate-systems)。</span><span class="sxs-lookup"><span data-stu-id="46355-112">This sets Unity's world coordinate system to track the [stationary frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="46355-113">在 「 定態的追蹤模式中，內容會放在編輯器中只前方相機的預設位置 （正向是-Z） 應用程式啟動時，會出現在使用者之前。</span><span class="sxs-lookup"><span data-stu-id="46355-113">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="46355-114">**命名空間：**  *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="46355-114">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="46355-115">**類型：** *InputTracking*</span><span class="sxs-lookup"><span data-stu-id="46355-115">**Type:** *InputTracking*</span></span>

<span data-ttu-id="46355-116">為純**僅限方向的體驗**例如 360 度視訊檢視器中 （其中位置標頭的更新會讓視覺效果），然後您可以設定[XR。InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html)設為 true:</span><span class="sxs-lookup"><span data-stu-id="46355-116">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="46355-117">針對**安插擴展經驗**，以讓使用者稍後 recenter 安置的原點，您可以呼叫[XR。InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)方法：</span><span class="sxs-lookup"><span data-stu-id="46355-117">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a><span data-ttu-id="46355-118">建置常設-小數位數或聊天室擴展經驗</span><span class="sxs-lookup"><span data-stu-id="46355-118">Building a standing-scale or room-scale experience</span></span>

<span data-ttu-id="46355-119">**命名空間：**  *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="46355-119">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="46355-120">**類型：**  *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="46355-120">**Type:** *XRDevice*</span></span>

<span data-ttu-id="46355-121">針對**常設擴展**或**聊天室擴展經驗**，您必須將內容放置相對於最低限度值。</span><span class="sxs-lookup"><span data-stu-id="46355-121">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="46355-122">您會理解使用者的 floor 使用 **[空間階段](coordinate-systems.md#spatial-coordinate-systems)** 、 樓層來源和選擇性空間界限代表使用者的定義、 設定期間第一次執行。</span><span class="sxs-lookup"><span data-stu-id="46355-122">You reason about the user's floor using the **[spatial stage](coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="46355-123">若要確保 Unity 使用其在 floor 層級的全局座標系統作業，您可以 Unity 設 RoomScale 追蹤空間類型，並確認集合成功：</span><span class="sxs-lookup"><span data-stu-id="46355-123">To ensure that Unity is operating with its world coordinate system at floor-level, you can set Unity to the RoomScale tracking space type, and ensure that the set succeeds:</span></span>

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
* <span data-ttu-id="46355-124">Unity SetTrackingSpaceType 傳回 true，如果已順利切換來追蹤其全局座標系統[階段參照](coordinate-systems.md#spatial-coordinate-systems)。</span><span class="sxs-lookup"><span data-stu-id="46355-124">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="46355-125">如果 SetTrackingSpaceType 傳回 false，Unity 無法切換至階段參考框架，可能會因為使用者未設定即使在其環境中 floor 切換。</span><span class="sxs-lookup"><span data-stu-id="46355-125">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up even a floor in their environment.</span></span> <span data-ttu-id="46355-126">這並不常見，但如果階段已在不同房間內設定和裝置已移至目前的空間，而不需要新的階段中使用者的設定就會發生。</span><span class="sxs-lookup"><span data-stu-id="46355-126">This is not common, but can happen if the stage was set up in a different room and the device was moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="46355-127">一旦您的應用程式已成功設定追蹤的空間型別，內容放在 y 軸上 RoomScale = 的 0 平面會出現在最低限度值。</span><span class="sxs-lookup"><span data-stu-id="46355-127">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="46355-128">（0，0，0） 處的原點，將會在最低限度值的空間在安裝期間，使用者名人-z 表示它們已在安裝期間對向的正向方向其中的特定位置。</span><span class="sxs-lookup"><span data-stu-id="46355-128">The origin at (0, 0, 0) will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>

<span data-ttu-id="46355-129">**命名空間：** *UnityEngine.Experimental.XR*</span><span class="sxs-lookup"><span data-stu-id="46355-129">**Namespace:** *UnityEngine.Experimental.XR*</span></span><br>
<span data-ttu-id="46355-130">**類型：** *界限*</span><span class="sxs-lookup"><span data-stu-id="46355-130">**Type:** *Boundary*</span></span>

<span data-ttu-id="46355-131">在指令碼，您可以呼叫您 TryGetGeometry 方法正在 UnityEngine.Experimental.XR.Boundary 型別，以取得界限的多邊形，然後指定 TrackedArea 界限類型。</span><span class="sxs-lookup"><span data-stu-id="46355-131">In script code, you can then call the TryGetGeometry method on your the UnityEngine.Experimental.XR.Boundary type to get a boundary polygon, specifying a boundary type of TrackedArea.</span></span> <span data-ttu-id="46355-132">如果使用者定義的界限 （得到頂點清單），您就會知道它是安全地傳遞**聊天室擴展經驗**給使用者，可以走的地方周圍場景您建立。</span><span class="sxs-lookup"><span data-stu-id="46355-132">If the user defined a boundary (you get back a list of vertices), you know it is safe to deliver a **room-scale experience** to the user, where they can walk around the scene you create.</span></span>

<span data-ttu-id="46355-133">請注意，系統會自動轉譯界限使用者接近它時。</span><span class="sxs-lookup"><span data-stu-id="46355-133">Note that the system will automatically render the boundary when the user approaches it.</span></span> <span data-ttu-id="46355-134">您的應用程式不需要使用此多邊形呈現本身的界限。</span><span class="sxs-lookup"><span data-stu-id="46355-134">Your app does not need to use this polygon to render the boundary itself.</span></span> <span data-ttu-id="46355-135">不過，您可以選擇使用此界限的多邊形，確保使用者可以實際連線到這些物件，而不需要 teleporting 場景物件的版面配置設定：</span><span class="sxs-lookup"><span data-stu-id="46355-135">However, you may choose to lay out your scene objects using this boundary polygon, to ensure the user can physically reach those objects without teleporting:</span></span>

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="46355-136">建置全球規模的體驗</span><span class="sxs-lookup"><span data-stu-id="46355-136">Building a world-scale experience</span></span>

<span data-ttu-id="46355-137">**命名空間：**  *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="46355-137">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="46355-138">**類型：** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="46355-138">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="46355-139">代表 true**全球級別體驗**在讓使用者超過 5 公尺走廊的 HoloLens，您需要超過所使用的空間調整體驗的新技術。</span><span class="sxs-lookup"><span data-stu-id="46355-139">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="46355-140">您將使用的一個重要技術是建立[空間的錨點](coordinate-systems.md#spatial-anchors)鎖定精確地就地真實世界中，不論幅度有漫遊的使用者，在全像投影的叢集，然後[日後再次在尋找這些全像投影工作階段](coordinate-systems.md#spatial-anchor-persistence)。</span><span class="sxs-lookup"><span data-stu-id="46355-140">One key technique you'll use is to create a [spatial anchor](coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, regardless of how far the user has roamed, and then [find those holograms again in later sessions](coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="46355-141">在 Unity 中，您必須建立空間的錨點加入**WorldAnchor** Unity 元件的 GameObject。</span><span class="sxs-lookup"><span data-stu-id="46355-141">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="46355-142">加入全球錨點</span><span class="sxs-lookup"><span data-stu-id="46355-142">Adding a World Anchor</span></span>

<span data-ttu-id="46355-143">若要加入全球錨點，呼叫 AddComponent<WorldAnchor>遊戲和您想要將真實世界中的錨點的轉換物件上的 （)。</span><span class="sxs-lookup"><span data-stu-id="46355-143">To add a world anchor, call AddComponent<WorldAnchor>() on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="46355-144">就這麼容易！</span><span class="sxs-lookup"><span data-stu-id="46355-144">That's it!</span></span> <span data-ttu-id="46355-145">此遊戲物件會立即錨定至真實世界的目前位置-您可能會看到一段時間，以確保該實體的對齊方式稍微調整其 Unity 全局座標。</span><span class="sxs-lookup"><span data-stu-id="46355-145">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="46355-146">使用[持續性](persistence-in-unity.md)可以找到此錨定位置一次在未來的應用程式工作階段。</span><span class="sxs-lookup"><span data-stu-id="46355-146">Use [persistence](persistence-in-unity.md) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="46355-147">移除世界錨點</span><span class="sxs-lookup"><span data-stu-id="46355-147">Removing a World Anchor</span></span>

<span data-ttu-id="46355-148">如果您不再想 GameObject 鎖定至真實世界的位置，而且不想要將它移至此框架，則您可以只需要呼叫終結世界錨定在元件上。</span><span class="sxs-lookup"><span data-stu-id="46355-148">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="46355-149">如果您想要移動 GameObject 此框架中，您需要改為呼叫 DestroyImmediate。</span><span class="sxs-lookup"><span data-stu-id="46355-149">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="46355-150">移動世界錨定 GameObject</span><span class="sxs-lookup"><span data-stu-id="46355-150">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="46355-151">世界錨定在其上時，不能移動 GameObject 的。</span><span class="sxs-lookup"><span data-stu-id="46355-151">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="46355-152">如果您要移動 GameObject 此框架時，您需要：</span><span class="sxs-lookup"><span data-stu-id="46355-152">If you need to move the GameObject this frame, you need to:</span></span>
1. <span data-ttu-id="46355-153">DestroyImmediate 世界錨點元件</span><span class="sxs-lookup"><span data-stu-id="46355-153">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="46355-154">移動 GameObject</span><span class="sxs-lookup"><span data-stu-id="46355-154">Move the GameObject</span></span>
3. <span data-ttu-id="46355-155">將 World 錨點的新元件新增至 GameObject。</span><span class="sxs-lookup"><span data-stu-id="46355-155">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="46355-156">處理 Locatability 變更</span><span class="sxs-lookup"><span data-stu-id="46355-156">Handling Locatability Changes</span></span>

<span data-ttu-id="46355-157">WorldAnchor 可能無法之外的可尋獲在真實世界的某一點的時間。</span><span class="sxs-lookup"><span data-stu-id="46355-157">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="46355-158">如果發生此情況，Unity 將不會更新錨定的物件的轉換。</span><span class="sxs-lookup"><span data-stu-id="46355-158">If that occurs, Unity will not be updating the transform of the anchored object.</span></span> <span data-ttu-id="46355-159">這也可以變更應用程式執行時。</span><span class="sxs-lookup"><span data-stu-id="46355-159">This also can change while an app is running.</span></span> <span data-ttu-id="46355-160">Locatability 中處理此變更會導致不會出現在正確的實體位置的世界中的物件。</span><span class="sxs-lookup"><span data-stu-id="46355-160">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="46355-161">若要收到 locatability 變更：</span><span class="sxs-lookup"><span data-stu-id="46355-161">To be notified about locatability changes:</span></span>
1. <span data-ttu-id="46355-162">訂閱 OnTrackingChanged 事件</span><span class="sxs-lookup"><span data-stu-id="46355-162">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="46355-163">處理事件</span><span class="sxs-lookup"><span data-stu-id="46355-163">Handle the event</span></span>

<span data-ttu-id="46355-164">**OnTrackingChanged**基礎的空間錨點變更之間的狀態為正在之外的可尋獲與未之外的可尋獲時，就會呼叫事件。</span><span class="sxs-lookup"><span data-stu-id="46355-164">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="46355-165">然後處理事件：</span><span class="sxs-lookup"><span data-stu-id="46355-165">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="46355-166">有時候錨點位於立即。</span><span class="sxs-lookup"><span data-stu-id="46355-166">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="46355-167">在此情況下，此 isLocated 屬性的錨點會設定為 true 時 AddComponent<WorldAnchor>（） 傳回。</span><span class="sxs-lookup"><span data-stu-id="46355-167">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="46355-168">如此一來，就不會觸發 OnTrackingChanged 事件。</span><span class="sxs-lookup"><span data-stu-id="46355-168">As a result, the OnTrackingChanged event will not be triggered.</span></span> <span data-ttu-id="46355-169">全新的模式是呼叫您初始的 IsLocated 狀態的 OnTrackingChanged 處理常式之後附加錨點。</span><span class="sxs-lookup"><span data-stu-id="46355-169">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a><span data-ttu-id="46355-170">在裝置之間共用的錨點</span><span class="sxs-lookup"><span data-stu-id="46355-170">Sharing anchors across devices</span></span>

<span data-ttu-id="46355-171">您可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間的錨點</a>從本機的 WorldAnchor，然後會跨多個 HoloLens、 iOS 和 Android 裝置可以找出您的應用程式建立持久的雲端錨點。</span><span class="sxs-lookup"><span data-stu-id="46355-171">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="46355-172">藉由跨多個裝置共用常見的空間錨點，每位使用者都可以看到相對於該錨點相同的實體位置中呈現內容。</span><span class="sxs-lookup"><span data-stu-id="46355-172">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="46355-173">這可讓您即時分享經驗。</span><span class="sxs-lookup"><span data-stu-id="46355-173">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="46355-174">若要開始建置 Unity 中的共用的體驗，試用 5 分鐘<a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">空間錨點 Unity Azure 快速入門</a>。</span><span class="sxs-lookup"><span data-stu-id="46355-174">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="46355-175">一旦您啟動並執行 Azure 空間的起點，您可以接著<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">建立，並找出在 Unity 中的錨點</a>。</span><span class="sxs-lookup"><span data-stu-id="46355-175">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="46355-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46355-176">See Also</span></span>
* [<span data-ttu-id="46355-177">體驗標尺</span><span class="sxs-lookup"><span data-stu-id="46355-177">Experience scales</span></span>](coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="46355-178">空間的階段</span><span class="sxs-lookup"><span data-stu-id="46355-178">Spatial stage</span></span>](coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="46355-179">追蹤 Unity 中的遺失</span><span class="sxs-lookup"><span data-stu-id="46355-179">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="46355-180">空間的錨點</span><span class="sxs-lookup"><span data-stu-id="46355-180">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="46355-181">在 Unity 中的持續性</span><span class="sxs-lookup"><span data-stu-id="46355-181">Persistence in Unity</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="46355-182">在 Unity 中的共用的體驗</span><span class="sxs-lookup"><span data-stu-id="46355-182">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
* <span data-ttu-id="46355-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間的錨點</a></span><span class="sxs-lookup"><span data-stu-id="46355-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="46355-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure 的空間錨點適用於 Unity SDK</a></span><span class="sxs-lookup"><span data-stu-id="46355-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>