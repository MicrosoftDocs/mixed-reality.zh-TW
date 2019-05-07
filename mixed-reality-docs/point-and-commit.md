---
title: 點和認可
description: 點和認可輸入模型的概觀
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
keywords: 混合實境，互動，設計
ms.openlocfilehash: e0e9c97053734ac0125fce40be7ffe9afbd2dd68
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2019
ms.locfileid: "64581308"
---
# <a name="point-and-commit"></a><span data-ttu-id="395ee-104">點和認可</span><span class="sxs-lookup"><span data-stu-id="395ee-104">Point and commit</span></span>
<span data-ttu-id="395ee-105">點和認可是輸入的模型可讓使用者為目標、 選取和操作內容 2D 和 3D 物件的距離。</span><span class="sxs-lookup"><span data-stu-id="395ee-105">Point and commit is an input model enables users to target, select and manipulate 2D contents and 3D objects in a distance.</span></span> <span data-ttu-id="395ee-106">這個 「 Far"互動技術是 navel 的互動式體驗，人為的是不需要在每日與真實世界互動期間。</span><span class="sxs-lookup"><span data-stu-id="395ee-106">This "Far" interaction technique is a navel interactive experience that human being didn't really have during their daily interaction with the real world.</span></span> <span data-ttu-id="395ee-107">比方說，在進階的 hero 電影，Mo 能夠的觸角和操作遠的物件，透過實際操作的距離，但人們在實際上無法做到。</span><span class="sxs-lookup"><span data-stu-id="395ee-107">For example, in a super hero movie, Magneto is capable of reaching out and manipulating a far object via hands in a distance, but human can't do it in reality.</span></span> <span data-ttu-id="395ee-108">在 Microsoft HoloLens (AR) 和 Microsoft 混合實境 (VR) 中，我們讓使用者這個神奇的電源中斷不只是為了讓愉悅的經驗，使用全像攝影版的內容，但讓互動更有效率的真實世界的實體條件約束和有效的。</span><span class="sxs-lookup"><span data-stu-id="395ee-108">In both Microsoft HoloLens (AR) and Microsoft Mixed Reality (VR), we equip users this magical power, breaking the physical constraint of real world not only to have delightful experience with holographic contents but to make the interaction more effective and efficient.</span></span>

## <a name="device-support"></a><span data-ttu-id="395ee-109">裝置支援</span><span class="sxs-lookup"><span data-stu-id="395ee-109">Device support</span></span>
<table>
    <colgroup>
    <col width="40%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="395ee-110"><strong>輸入的模型</strong></span><span class="sxs-lookup"><span data-stu-id="395ee-110"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="395ee-111"><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="395ee-111"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="395ee-112"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="395ee-112"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="395ee-113"><a href="immersive-headset-hardware-details.md"><strong>沈浸式耳機</strong></a></span><span class="sxs-lookup"><span data-stu-id="395ee-113"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="395ee-114">點和認可 （最手動互動）</span><span class="sxs-lookup"><span data-stu-id="395ee-114">Point and commit (far hand interaction)</span></span></td>
        <td><span data-ttu-id="395ee-115">不支援的 ❌</span><span class="sxs-lookup"><span data-stu-id="395ee-115">❌ Not supported</span></span></td>
        <td><span data-ttu-id="395ee-116">建議的 ✔️</span><span class="sxs-lookup"><span data-stu-id="395ee-116">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="395ee-117">建議的 ✔️</span><span class="sxs-lookup"><span data-stu-id="395ee-117">✔️ Recommended</span></span></td>
    </tr>
</table>
<br>
<span data-ttu-id="395ee-118">點和認可已 HoloLens 2，利用新的相互連貫的手動追蹤系統上的主要輸入模型的其中一個。</span><span class="sxs-lookup"><span data-stu-id="395ee-118">Point and commit has been one of the primary input models on HoloLens 2, utilizing the new articulated hand tracking system.</span></span> <span data-ttu-id="395ee-119">這個輸入的模型也是透過移動控制站使用的沈浸式耳機的主要輸入的模型。</span><span class="sxs-lookup"><span data-stu-id="395ee-119">This input model is also the primary input model on immersive headsets through the use of motion controllers.</span></span> <span data-ttu-id="395ee-120">點和認可是我們建議您將前端視線輸入的模型和 HoloLens 上認可 （第 1 代）。</span><span class="sxs-lookup"><span data-stu-id="395ee-120">Point and Commit is the input model that we suggest to replace the Head Gaze and Commit on HoloLens (1st gen).</span></span> 

## <a name="hand-rays"></a><span data-ttu-id="395ee-121">手動光線</span><span class="sxs-lookup"><span data-stu-id="395ee-121">Hand rays</span></span>
<span data-ttu-id="395ee-122">HoloLens 2 上，我們會建立疑難排解從 palm 中央手光線。</span><span class="sxs-lookup"><span data-stu-id="395ee-122">On HoloLens 2, we create a hand ray shooting out from the center of a palm.</span></span> <span data-ttu-id="395ee-123">與射線會被視為指針的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="395ee-123">The ray is treated as an extension of the hand.</span></span> <span data-ttu-id="395ee-124">環圈圖的圖形資料指標會附加結尾的光線，暗示與命中物件中的光線交集的位置。</span><span class="sxs-lookup"><span data-stu-id="395ee-124">A donut shape cursor is attached at the end of the ray to imply the location where the ray intersects with a hitted object.</span></span> <span data-ttu-id="395ee-125">資料指標進入物件會接收來自手形的 gestural 的命令。</span><span class="sxs-lookup"><span data-stu-id="395ee-125">The object that the cursor lands will receive gestural commands from the hand.</span></span> 

<span data-ttu-id="395ee-126">非常基本的 gestural 命令就會觸發使用姆指與食指執行空中點選手勢。</span><span class="sxs-lookup"><span data-stu-id="395ee-126">The very basic gestural command is triggered by using thumb and index finger to perform air tap gesture.</span></span> <span data-ttu-id="395ee-127">藉由使用手動光線單點及空中點選來認可，使用者可以啟動按鈕或 web 內容上的超連結。</span><span class="sxs-lookup"><span data-stu-id="395ee-127">By using hand ray to point and air tap to commit, users can activate a button or a hyperlink on a web content.</span></span> <span data-ttu-id="395ee-128">更多的複合筆勢，使用者就能夠瀏覽的網頁內容和管理 3D 物件的距離。</span><span class="sxs-lookup"><span data-stu-id="395ee-128">With more composite gestures, users are capable of navigating the web content and manipulating 3D objects in a distance.</span></span> <span data-ttu-id="395ee-129">手動光線的視覺化設計也應該回應點，並認可狀態：</span><span class="sxs-lookup"><span data-stu-id="395ee-129">The visual design of the hand ray should also react to point and commit states:</span></span> <br>
* <span data-ttu-id="395ee-130">在指標的狀態，光線 dash 分行、 且資料指標是環圈圖的圖形。</span><span class="sxs-lookup"><span data-stu-id="395ee-130">In the pointing state, the ray is dash lined, and the cursor is a donut shape.</span></span>
* <span data-ttu-id="395ee-131">在認可的狀態，光線變成一條實線，而游標會壓縮成一個點。</span><span class="sxs-lookup"><span data-stu-id="395ee-131">in the committing state, the ray turns into a solid line, and the cursor shrinks to a dot.</span></span><br><br>
![](images/Hand-Rays-720px.jpg)<br>

## <a name="transition-between-near-and-far"></a><span data-ttu-id="395ee-132">和最接近之間轉換</span><span class="sxs-lookup"><span data-stu-id="395ee-132">Transition between near and far</span></span>
<span data-ttu-id="395ee-133">而不是使用特定的筆勢，例如指向食指導向無限遠的光線，與我們設計來自中心的 palm、 光線，釋出和保留的多個 gestural 操作的五個指。</span><span class="sxs-lookup"><span data-stu-id="395ee-133">Instead of using specific gestures, such as pointing with index finger to direct the ray, we design the ray coming out from the center of the palm, releasing and reserving the five fingers for more gestural manipulations.</span></span> <span data-ttu-id="395ee-134">因此，HoloLens 2 支援幾近和遠端互動完全相同的一組手勢。</span><span class="sxs-lookup"><span data-stu-id="395ee-134">Therefore, HoloLens 2 supports exactly the same set of hand gestures for both near and far interaction.</span></span> <span data-ttu-id="395ee-135">從靠近最互動，以及反向傳輸的使用者時，就不需要任何其他的學習。</span><span class="sxs-lookup"><span data-stu-id="395ee-135">No additional learning is needed when users transit from near to far interactions, and vice versa.</span></span> <span data-ttu-id="395ee-136">使用者可以使用相同的抓取筆勢來操作物件在不同的距離。</span><span class="sxs-lookup"><span data-stu-id="395ee-136">Users can use the same grab gesture to manipulate objects at different distances.</span></span> <span data-ttu-id="395ee-137">光線的引動過程是自動和架構的鄰近性：</span><span class="sxs-lookup"><span data-stu-id="395ee-137">The invocation of the rays is automatic and proximity based:</span></span> <br>
* <span data-ttu-id="395ee-138">在 arm 達到距離 (大約 50 cm) 物件時，光線會關閉自動鼓勵幾近互動。</span><span class="sxs-lookup"><span data-stu-id="395ee-138">when an object is within arm reached distance (roughly 50 cm), the rays are turned off automatically encouraging for near interaction.</span></span> 
* <span data-ttu-id="395ee-139">太遠超過 50 cm 物件時，會開啟光線。</span><span class="sxs-lookup"><span data-stu-id="395ee-139">When the object is farther than 50 cm, the rays are turned on.</span></span>

<span data-ttu-id="395ee-140">這項機制會使轉換順利且流暢地。</span><span class="sxs-lookup"><span data-stu-id="395ee-140">This mechanism makes the transition smooth and seamless.</span></span><br>
![](images/Transition-Between-Near-And-Far-720px.jpg)<br>

## <a name="2d-slate-interaction"></a><span data-ttu-id="395ee-141">2D 平板電腦的互動</span><span class="sxs-lookup"><span data-stu-id="395ee-141">2D slate interaction</span></span>
<span data-ttu-id="395ee-142">2D slate 是全像攝影版的容器，裝載 2D 應用程式的內容，例如網頁瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="395ee-142">A 2D slate is a holographic container hosting 2D app contents, such as web browser.</span></span> <span data-ttu-id="395ee-143">到目前為止與 2D 平板式互動的設計概念是單點及空中點選來認可使用手動光線。</span><span class="sxs-lookup"><span data-stu-id="395ee-143">The design concept for far interacting with a 2D slate is to use hand rays to point and air tap to commit.</span></span><br>

<span data-ttu-id="395ee-144">如果需要互動的平板電腦的常數：</span><span class="sxs-lookup"><span data-stu-id="395ee-144">For interacting with the slate contant:</span></span><br>

* <span data-ttu-id="395ee-145">使用者可以在超連結或按鈕，然後才能加以啟動空中點選點。</span><span class="sxs-lookup"><span data-stu-id="395ee-145">Users can point at a hyperlink or a button, then air tap to activate it.</span></span> 
* <span data-ttu-id="395ee-146">若要執行以向上和向下捲動平板電腦的內容瀏覽動作時，使用者可以使用一隻手。</span><span class="sxs-lookup"><span data-stu-id="395ee-146">Users can use one hand to perform a navigation gesture to scroll a slate content up and down.</span></span> 
* <span data-ttu-id="395ee-147">使用者可以使用兩個實際操作，來執行瀏覽手勢來縮放 in 和 out 平板電腦的內容。</span><span class="sxs-lookup"><span data-stu-id="395ee-147">Users can use two hands to perform navigation gestures to zoom in and out the slate content.</span></span><br><br>

![](images/2D-Slate-Interaction-Far-720px.jpg)<br>

<span data-ttu-id="395ee-148">操作 2D slate 本身：</span><span class="sxs-lookup"><span data-stu-id="395ee-148">For manipulating the 2D slate itself:</span></span><br>

* <span data-ttu-id="395ee-149">使用者點 gmail.comray.djajadinata 角落或以顯示最接近的操作功能可見性的邊緣之間的手。</span><span class="sxs-lookup"><span data-stu-id="395ee-149">Users point the hand ray at the corners or edges to reveal the closest manipulation affordance.</span></span> 
* <span data-ttu-id="395ee-150">藉由套用操作軌跡上的功能可見性，使用者可以執行統一的縮放，透過角功能可見性，而且可以自動重排 slate 透過 edge 功能可見性。</span><span class="sxs-lookup"><span data-stu-id="395ee-150">By applying a manipulation gesture on the affordance, users can perform uniform scaling through the corner affordance and can reflow the slate via the edge affordance.</span></span> 
* <span data-ttu-id="395ee-151">藉由在頂端的 2D slate holobar 套用操作筆勢，使用者可以移動整個 slate。</span><span class="sxs-lookup"><span data-stu-id="395ee-151">By applying a manipulation gesture on the holobar at the top of the 2D slate, users can move the whole slate.</span></span><br>

<br>

## <a name="3d-object-manipulation"></a><span data-ttu-id="395ee-152">3D 物件操作</span><span class="sxs-lookup"><span data-stu-id="395ee-152">3D object manipulation</span></span>
<span data-ttu-id="395ee-153">在直接管理，有兩種方式來操作 3D 物件的使用者功能可見性基礎操作和非 affordnace 基礎操作。</span><span class="sxs-lookup"><span data-stu-id="395ee-153">In direct manipulation, there are two ways for users to manipulate 3D object, Affordance Based Manipulation and Non-affordnace Based Manipulation.</span></span> <span data-ttu-id="395ee-154">在點和認可的模型中，使用者都能達到完全相同的工作透過手動光線。</span><span class="sxs-lookup"><span data-stu-id="395ee-154">In point and commit model, users are capable of achieving exactly the same tasks through the hand rays.</span></span> <span data-ttu-id="395ee-155">不需要任何其他的學習。</span><span class="sxs-lookup"><span data-stu-id="395ee-155">No additional learning is needed.</span></span><br>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="395ee-156">基礎功能的可見性操作</span><span class="sxs-lookup"><span data-stu-id="395ee-156">Affordance based manipulation</span></span>
<span data-ttu-id="395ee-157">使用者會使用點，且顯示週框方塊和操作提供手動光線。</span><span class="sxs-lookup"><span data-stu-id="395ee-157">Users use hand rays to point and reveal the bounding box and manipulation affordances.</span></span> <span data-ttu-id="395ee-158">使用者可以套用操作手勢，來移動整個物件的週框方塊，來旋轉邊緣提供和上 coner 提供一致的方式調整。</span><span class="sxs-lookup"><span data-stu-id="395ee-158">Users can apply the manipulation gesture on the bounding box to move the whole object, on the edge affordances to rotate and on the coner affordances to scale uniformly.</span></span> <br>

![](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="395ee-159">非功能可見性根據的操作</span><span class="sxs-lookup"><span data-stu-id="395ee-159">Non-affordance based manipulation</span></span>
<span data-ttu-id="395ee-160">使用者點顯示週框方塊，然後直接在其上套用操作筆勢的手光線。</span><span class="sxs-lookup"><span data-stu-id="395ee-160">Users point with hand rays to reveal the bounding box then directly apply manipulation gestures on it.</span></span> <span data-ttu-id="395ee-161">與某一方面，轉譯和旋轉的物件相關聯動作和左手邊的方向。</span><span class="sxs-lookup"><span data-stu-id="395ee-161">With one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="395ee-162">與兩個實際操作，使用者可以轉譯、 縮放和旋轉根據相對的兩個實際操作的動作。</span><span class="sxs-lookup"><span data-stu-id="395ee-162">With two hands, users can translate, scale and rotate it according to relative motions of two hands.</span></span><br>

<br>

## <a name="instinctual-gesturers"></a><span data-ttu-id="395ee-163">Instinctual gesturers</span><span class="sxs-lookup"><span data-stu-id="395ee-163">Instinctual gesturers</span></span>
<span data-ttu-id="395ee-164">點及認可 instinctual 筆勢的概念是同步槲臗懟。</span><span class="sxs-lookup"><span data-stu-id="395ee-164">The concept of instinctual gestures for point and commit is in sync with that for direct manipulation.</span></span> <span data-ttu-id="395ee-165">假設的 3D 物件上執行的筆勢使用者會引導您的 UI 提供的設計。</span><span class="sxs-lookup"><span data-stu-id="395ee-165">What gestures users suppose to perform on a 3D object are guided by the design of UI affordances.</span></span> <span data-ttu-id="395ee-166">小型的控制點會鼓勵使用者時的大型物件，讓使用者能夠抓取 5 食指姆指與食指，以縮小。</span><span class="sxs-lookup"><span data-stu-id="395ee-166">A small control point would motivate users to pinch with thumb and index finger, while a large object makes users to grab with 5 finger.</span></span>

![](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a><span data-ttu-id="395ee-167">指針與 6 DoF 控制站之間的對稱式設計</span><span class="sxs-lookup"><span data-stu-id="395ee-167">Symmetric design between hands and 6 DoF controller</span></span> 
<span data-ttu-id="395ee-168">首先建立並定義為混合實境入口網站 (MRP)，其中使用者 wear 沈浸式耳機並與其互動的 3d 物件透過移動控制站進行遠端互動點和認可模型的概念。</span><span class="sxs-lookup"><span data-stu-id="395ee-168">The concept of point and commit model for far interaction is firstly created and defined for the Mixed Reality Portal (MRP), where users wear an immersive headset and interact with the 3d object via motion controllers.</span></span> <span data-ttu-id="395ee-169">動作控制站疑難排解出指向及管理遠端物件的光線。</span><span class="sxs-lookup"><span data-stu-id="395ee-169">The motion controllers shoot out rays for pointing and manipulating far objects.</span></span> <span data-ttu-id="395ee-170">有進一步認可不同功能的控制站上的按鈕。</span><span class="sxs-lookup"><span data-stu-id="395ee-170">There are buttons on the controllers for further committing different functionalities.</span></span> <span data-ttu-id="395ee-171">我們運用光線的互動模型，並將它們連接在這兩個手上。</span><span class="sxs-lookup"><span data-stu-id="395ee-171">We leverage the interaction model of rays and attach them on both hands.</span></span> <span data-ttu-id="395ee-172">透過此對稱的設計，MRP 熟悉的使用者不需要了解另一個用於目前指向及操作時使用 HoloLen 2 的第一次的互動模型，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="395ee-172">With this symmetric design, users who are familiar with MRP won't need to learn another interaction model for far pointing and manipulation while first time using HoloLen 2, and vice versa.</span></span>    

![](images/Symmetric-Design-For-Rays-720px.jpg)<br>


## <a name="see-also"></a><span data-ttu-id="395ee-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="395ee-173">See also</span></span>
* [<span data-ttu-id="395ee-174">視線與認可</span><span class="sxs-lookup"><span data-stu-id="395ee-174">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="395ee-175">直接操作</span><span class="sxs-lookup"><span data-stu-id="395ee-175">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="395ee-176">互動基本概念</span><span class="sxs-lookup"><span data-stu-id="395ee-176">Interaction fundamentals</span></span>](interaction-fundamentals.md)
