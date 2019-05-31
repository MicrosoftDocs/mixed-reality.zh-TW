---
title: 點與包含實際操作的認可
description: 點和認可輸入模型的概觀
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境，互動、 設計、 hololens、 實際操作，到目前為止，點並認可
ms.openlocfilehash: 30f85d2bb455abab3a533e0a829b4fba8cea0a7a
ms.sourcegitcommit: 5b4292ef786447549c0199003e041ca48bb454cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402377"
---
# <a name="point-and-commit-with-hands"></a><span data-ttu-id="fd902-104">點與包含實際操作的認可</span><span class="sxs-lookup"><span data-stu-id="fd902-104">Point and commit with hands</span></span>
<span data-ttu-id="fd902-105">點與包含實際操作的認可是輸入的模型，可讓使用者為目標、 選取和操作之距離的 2D 內容與 3D 物件。</span><span class="sxs-lookup"><span data-stu-id="fd902-105">Point and commit with hands is an input model that enables users to target, select and manipulate 2D content and 3D objects in the distance.</span></span> <span data-ttu-id="fd902-106">「 目前 」 互動技術是混合實境特有而非方式讓使用者自然地與真實世界的 intereact。</span><span class="sxs-lookup"><span data-stu-id="fd902-106">This "far" interaction technique is unique to mixed reality and is not a way humans naturally intereact with the real world.</span></span> <span data-ttu-id="fd902-107">例如，在進階的 hero 電影*X 男性*，字元[Mo](https://en.wikipedia.org/wiki/Magneto_(comics))能夠連絡和操作與他的實際操作之距離的最物件。</span><span class="sxs-lookup"><span data-stu-id="fd902-107">For example, in the super hero movie *X-Men*, the character [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) is capable of reaching out and manipulating a far object in the distance with his hands.</span></span> <span data-ttu-id="fd902-108">這不是人類可以這麼做實際上。</span><span class="sxs-lookup"><span data-stu-id="fd902-108">This is not something humans can do in reality.</span></span> <span data-ttu-id="fd902-109">在 HoloLens (AR) 和混合實境 (VR) 中，我們會提供使用者這個神奇的電源中斷真實的世界有愉悅的經驗，使用全像攝影版的內容不僅讓互動更有效率且有效的實體條件約束。</span><span class="sxs-lookup"><span data-stu-id="fd902-109">In both HoloLens (AR) and Mixed Reality (VR), we equip users with this magical power, breaking the physical constraint of the real world not only to have a delightful experience with holographic contents but also to make the interaction more effective and efficient.</span></span>

## <a name="device-support"></a><span data-ttu-id="fd902-110">裝置支援</span><span class="sxs-lookup"><span data-stu-id="fd902-110">Device support</span></span>

<span data-ttu-id="fd902-111">輸入的模型</span><span class="sxs-lookup"><span data-stu-id="fd902-111">Input model</span></span> | [<span data-ttu-id="fd902-112">HoloLens （第 1 代）</span><span class="sxs-lookup"><span data-stu-id="fd902-112">HoloLens (1st gen)</span></span>](https://docs.microsoft.com/en-us/windows/mixed-reality/hololens-hardware-details) | <span data-ttu-id="fd902-113">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="fd902-113">HoloLens 2</span></span> | [<span data-ttu-id="fd902-114">沈浸式耳機</span><span class="sxs-lookup"><span data-stu-id="fd902-114">Immersive headsets</span></span>](https://docs.microsoft.com/en-us/windows/mixed-reality/immersive-headset-hardware-details) |
| ---------| -----| ----- | ---------|
<span data-ttu-id="fd902-115">點與包含實際操作的認可</span><span class="sxs-lookup"><span data-stu-id="fd902-115">Point and commit with hands</span></span> | <span data-ttu-id="fd902-116">不支援的 ❌</span><span class="sxs-lookup"><span data-stu-id="fd902-116">❌ Not supported</span></span> | <span data-ttu-id="fd902-117">建議的 ✔️</span><span class="sxs-lookup"><span data-stu-id="fd902-117">✔️ Recommended</span></span> | <span data-ttu-id="fd902-118">建議的 ✔️</span><span class="sxs-lookup"><span data-stu-id="fd902-118">✔️ Recommended</span></span>

<span data-ttu-id="fd902-119">點與認可，也就是指針到目前為止，是利用新的相互連貫的手動追蹤系統的新功能。</span><span class="sxs-lookup"><span data-stu-id="fd902-119">Point and commit, also known as hands far, is one of the new features that utilizes the new articulated hand-tracking system.</span></span> <span data-ttu-id="fd902-120">這個輸入的模型也是透過移動控制站使用的沈浸式耳機的主要輸入的模型。</span><span class="sxs-lookup"><span data-stu-id="fd902-120">This input model is also the primary input model on immersive headsets through the use of motion controllers.</span></span>

## <a name="hand-rays"></a><span data-ttu-id="fd902-121">手動光線</span><span class="sxs-lookup"><span data-stu-id="fd902-121">Hand rays</span></span>

<span data-ttu-id="fd902-122">HoloLens 2 上，我們會建立從 palm 中央弄手光線。</span><span class="sxs-lookup"><span data-stu-id="fd902-122">On HoloLens 2, we created a hand ray that shoots out from the center of a palm.</span></span> <span data-ttu-id="fd902-123">此光線會被視為指針的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="fd902-123">This ray is treated as an extension of the hand.</span></span> <span data-ttu-id="fd902-124">環圈圖形狀的游標會附加至結尾的光線，以指出在與目標物件與光線交集的位置。</span><span class="sxs-lookup"><span data-stu-id="fd902-124">A donut-shaped cursor is attached to the end of the ray to indicate the location where the ray intersects with a target object.</span></span> <span data-ttu-id="fd902-125">將游標放在物件然後可以接收 gestural 命令翻牌。</span><span class="sxs-lookup"><span data-stu-id="fd902-125">The object that the cursor lands on can then receive gestural commands from the hand.</span></span>

<span data-ttu-id="fd902-126">此基本 gestural 命令就會觸發使用姆指與食指執行空中點選動作。</span><span class="sxs-lookup"><span data-stu-id="fd902-126">This basic gestural command is triggered by using the thumb and index finger to perform the air-tap action.</span></span> <span data-ttu-id="fd902-127">藉由使用手動光線單點及空中點選來認可，使用者可以啟動按鈕或 web 內容上的超連結。</span><span class="sxs-lookup"><span data-stu-id="fd902-127">By using the hand ray to point and air tap to commit, users can activate a button or a hyperlink on a web content.</span></span> <span data-ttu-id="fd902-128">更多的複合筆勢，使用者就能夠瀏覽的網頁內容和管理 3D 物件的距離。</span><span class="sxs-lookup"><span data-stu-id="fd902-128">With more composite gestures, users are capable of navigating web content and manipulating 3D objects from a distance.</span></span> <span data-ttu-id="fd902-129">手動光線的視覺化設計還應該因應這些點和認可的狀態，如下所描述和如下所示：</span><span class="sxs-lookup"><span data-stu-id="fd902-129">The visual design of the hand ray should also react to these point and commit states, as described and shown below:</span></span> 

* <span data-ttu-id="fd902-130">在 *指向*狀態時，光線虛線且資料指標的 「 甜甜圈 」 圖形。</span><span class="sxs-lookup"><span data-stu-id="fd902-130">In the *pointing* state, the ray is a dash line and the cursor is a donut shape.</span></span>
* <span data-ttu-id="fd902-131">在 *認可*狀態時，光線變成一條實線，而游標會壓縮成一個點。</span><span class="sxs-lookup"><span data-stu-id="fd902-131">In the *commit* state, the ray turns into a solid line and the cursor shrinks to a dot.</span></span>

![](images/Hand-Rays-720px.jpg)

## <a name="transition-between-near-and-far"></a><span data-ttu-id="fd902-132">和最接近之間轉換</span><span class="sxs-lookup"><span data-stu-id="fd902-132">Transition between near and far</span></span>

<span data-ttu-id="fd902-133">而不是使用特定的動作，例如 「 索引食指指向 」 將光線，我們設計即將出從 palm，釋出和保留更多的倒是手勢的五個指中心這類縮小和抓取光線。</span><span class="sxs-lookup"><span data-stu-id="fd902-133">Instead of using specific gesture, such as "pointing with index finger" to direct the ray, we designed the ray coming out from the center of the palm, releasing and reserving the five fingers for more manipulative gestures, such as pinch and grab.</span></span> <span data-ttu-id="fd902-134">與這個設計中，我們會建立只有一個的心智模型，支援完全相同的一組手勢近乎和遠端互動。</span><span class="sxs-lookup"><span data-stu-id="fd902-134">With this design, we create only one mental model, supporting exactly the same set of hand gestures for both near and far interaction.</span></span> <span data-ttu-id="fd902-135">您可以使用相同的抓取筆勢來操作物件在不同的距離。</span><span class="sxs-lookup"><span data-stu-id="fd902-135">You can use the same grab gesture to manipulate objects at different distances.</span></span> <span data-ttu-id="fd902-136">光線的引動過程是自動和架構的鄰近性：</span><span class="sxs-lookup"><span data-stu-id="fd902-136">The invocation of the rays is automatic and proximity based:</span></span>

*  <span data-ttu-id="fd902-137">在 arm 達到距離 (大約 50 cm) 物件時，光線會關閉自動鼓勵幾近互動。</span><span class="sxs-lookup"><span data-stu-id="fd902-137">When an object is within arm reached distance (roughly 50 cm), the rays are turned off automatically encouraging for near interaction.</span></span>
*  <span data-ttu-id="fd902-138">太遠超過 50 cm 物件時，會開啟光線。</span><span class="sxs-lookup"><span data-stu-id="fd902-138">When the object is farther than 50 cm, the rays are turned on.</span></span> <span data-ttu-id="fd902-139">轉換時應順利且流暢地。</span><span class="sxs-lookup"><span data-stu-id="fd902-139">The transition should be smooth and seamless.</span></span>

![](images/Transition-Between-Near-And-Far-720px.jpg)

## <a name="2d-slate-interaction"></a><span data-ttu-id="fd902-140">2D 平板電腦的互動</span><span class="sxs-lookup"><span data-stu-id="fd902-140">2D slate interaction</span></span>

<span data-ttu-id="fd902-141">2D Slate 是全像攝影版的容器，裝載 2D 應用程式的內容，例如網頁瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="fd902-141">A 2D Slate is a holographic container hosting 2D app contents, such as web browser.</span></span> <span data-ttu-id="fd902-142">到目前為止與 2D 平板式互動的設計概念是要用來選取目標和空中點選來手動光線。</span><span class="sxs-lookup"><span data-stu-id="fd902-142">The design concept for far interacting with a 2D slate is to use hand rays to target and air tap to select.</span></span> <span data-ttu-id="fd902-143">之後手動無限遠的光線與目標，使用者可以空中點選來觸發超連結或按鈕。</span><span class="sxs-lookup"><span data-stu-id="fd902-143">After targeting with a hand ray, users can air tap to trigger a hyperlink or a button.</span></span> <span data-ttu-id="fd902-144">它們可用來 「 空中點選和拖曳 「 一方面向上和向下捲動平板電腦的內容。</span><span class="sxs-lookup"><span data-stu-id="fd902-144">They can use one hand to "air tap and drag" to scroll a slate content up and down.</span></span> <span data-ttu-id="fd902-145">使用兩個實際操作空中點選和拖曳的相對的影片可以縮放 in 和 out 平板電腦的內容。</span><span class="sxs-lookup"><span data-stu-id="fd902-145">The relative motion of using two hands to air tap and drag can zoom in and out the slate content.</span></span>

<span data-ttu-id="fd902-146">目標 gmail.comray.djajadinata 角和邊緣之間的手上會顯示最接近的操作功能可見性。</span><span class="sxs-lookup"><span data-stu-id="fd902-146">Targeting the hand ray at the corners and edges reveals the closest manipulation affordance.</span></span> <span data-ttu-id="fd902-147">藉由"抓取並拖曳 」 操作提供使用者可以執行統一透過角提供縮放比例以及可以自動重排 slate 透過邊緣提供。</span><span class="sxs-lookup"><span data-stu-id="fd902-147">By "grab and drag" the manipulation affordances, users can perform uniform scaling through the corner affordances and can reflow the slate via the edge affordances.</span></span> <span data-ttu-id="fd902-148">抓取並拖曳上方的 2D slate holobar 使用者可以移動整個 slate。</span><span class="sxs-lookup"><span data-stu-id="fd902-148">Grabbing and dragging the holobar at the top of the 2D slate can users move the whole slate.</span></span>

![](images/2D-Slate-Interaction-Far-720px.jpg)

<span data-ttu-id="fd902-149">操作 2D slate 本身：</span><span class="sxs-lookup"><span data-stu-id="fd902-149">For manipulating the 2D slate itself:</span></span><br>

* <span data-ttu-id="fd902-150">使用者點 gmail.comray.djajadinata 角落或以顯示最接近的操作功能可見性的邊緣之間的手。</span><span class="sxs-lookup"><span data-stu-id="fd902-150">Users point the hand ray at the corners or edges to reveal the closest manipulation affordance.</span></span> 
* <span data-ttu-id="fd902-151">藉由套用操作軌跡上的功能可見性，使用者可以執行統一的縮放，透過角功能可見性，而且可以自動重排 slate 透過 edge 功能可見性。</span><span class="sxs-lookup"><span data-stu-id="fd902-151">By applying a manipulation gesture on the affordance, users can perform uniform scaling through the corner affordance and can reflow the slate via the edge affordance.</span></span> 
* <span data-ttu-id="fd902-152">藉由在頂端的 2D slate holobar 套用操作筆勢，使用者可以移動整個 slate。</span><span class="sxs-lookup"><span data-stu-id="fd902-152">By applying a manipulation gesture on the holobar at the top of the 2D slate, users can move the whole slate.</span></span><br>

<br>

## <a name="3d-object-manipulation"></a><span data-ttu-id="fd902-153">3D 物件操作</span><span class="sxs-lookup"><span data-stu-id="fd902-153">3D object manipulation</span></span>

<span data-ttu-id="fd902-154">在直接管理，有兩種方法讓使用者管理 3D 物件、 功能可見性為基礎的管理和非功能可見性根據的操作。</span><span class="sxs-lookup"><span data-stu-id="fd902-154">In direct manipulation, there are two ways for users to manipulate 3D object, affordance-based manipulation and non-affordance based manipulation.</span></span> <span data-ttu-id="fd902-155">在點和認可的模型中，使用者都能達到完全相同的工作透過手動光線。</span><span class="sxs-lookup"><span data-stu-id="fd902-155">In the point and commit model, users are capable of achieving exactly the same tasks through the hand rays.</span></span> <span data-ttu-id="fd902-156">不需要任何其他的學習。</span><span class="sxs-lookup"><span data-stu-id="fd902-156">No additional learning is needed.</span></span><br>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="fd902-157">功能可見性為基礎的操作</span><span class="sxs-lookup"><span data-stu-id="fd902-157">Affordance-based manipulation</span></span>
<span data-ttu-id="fd902-158">使用者會使用點，且顯示週框方塊和操作提供手動光線。</span><span class="sxs-lookup"><span data-stu-id="fd902-158">Users use hand rays to point and reveal the bounding box and manipulation affordances.</span></span> <span data-ttu-id="fd902-159">使用者可以套用操作手勢，來移動整個物件的週框方塊，來旋轉邊緣提供和上 coner 提供一致的方式調整。</span><span class="sxs-lookup"><span data-stu-id="fd902-159">Users can apply the manipulation gesture on the bounding box to move the whole object, on the edge affordances to rotate and on the coner affordances to scale uniformly.</span></span> <br>

![](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="fd902-160">非功能可見性根據的操作</span><span class="sxs-lookup"><span data-stu-id="fd902-160">Non-affordance based manipulation</span></span>
<span data-ttu-id="fd902-161">使用者點顯示週框方塊，然後直接在其上套用操作筆勢的手光線。</span><span class="sxs-lookup"><span data-stu-id="fd902-161">Users point with hand rays to reveal the bounding box then directly apply manipulation gestures on it.</span></span> <span data-ttu-id="fd902-162">與某一方面，轉譯和旋轉的物件相關聯動作和左手邊的方向。</span><span class="sxs-lookup"><span data-stu-id="fd902-162">With one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="fd902-163">與兩個實際操作，使用者可以轉譯、 縮放和旋轉根據相對的兩個實際操作的動作。</span><span class="sxs-lookup"><span data-stu-id="fd902-163">With two hands, users can translate, scale and rotate it according to relative motions of two hands.</span></span><br>

<br>

## <a name="instinctual-gesturers"></a><span data-ttu-id="fd902-164">Instinctual gesturers</span><span class="sxs-lookup"><span data-stu-id="fd902-164">Instinctual gesturers</span></span>
<span data-ttu-id="fd902-165">點及認可 instinctual 筆勢的概念是類似於直接操作。</span><span class="sxs-lookup"><span data-stu-id="fd902-165">The concept of instinctual gestures for point and commit is similar to that for direct manipulation.</span></span> <span data-ttu-id="fd902-166">使用者會假設在 3D 物件上執行的筆勢會程式設計的 UI 提供引導。</span><span class="sxs-lookup"><span data-stu-id="fd902-166">The gestures users are suppose to perform on a 3D object are guided by the design of UI affordances.</span></span> <span data-ttu-id="fd902-167">例如，小型的控制點可能鼓勵使用者使用其姆指與食指，縮小，雖然使用者可能會想要擷取的較大的物件，使用所有的 5 個手指。</span><span class="sxs-lookup"><span data-stu-id="fd902-167">For example, a small control point might motivate users to pinch with their thumb and index finger, while a user might want to grab a larger object using all 5 fingers.</span></span>

![](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a><span data-ttu-id="fd902-168">指針與 6 DoF 控制站之間的對稱式設計</span><span class="sxs-lookup"><span data-stu-id="fd902-168">Symmetric design between hands and 6 DoF controller</span></span> 
<span data-ttu-id="fd902-169">一開始點和進行遠端互動的認可的概念已建立，並定義為混合實境入口網站 (MRP)，其中有很沈浸式耳機使用者，並透過移動控制站的 3D 物件進行互動。</span><span class="sxs-lookup"><span data-stu-id="fd902-169">The concept of point and commit for far interaction was initially created and defined for the Mixed Reality Portal (MRP), where a user wears an immersive headset and interacts with 3D objects via motion controllers.</span></span> <span data-ttu-id="fd902-170">動作控制站疑難排解出指向及管理遠端物件的光線。</span><span class="sxs-lookup"><span data-stu-id="fd902-170">The motion controllers shoot out rays for pointing and manipulating far objects.</span></span> <span data-ttu-id="fd902-171">有進一步認可不同動作的控制站上的按鈕。</span><span class="sxs-lookup"><span data-stu-id="fd902-171">There are buttons on the controllers for further committing different actions.</span></span> <span data-ttu-id="fd902-172">我們運用光線的互動模型，並它們附加至這兩個實際操作。</span><span class="sxs-lookup"><span data-stu-id="fd902-172">We leverage the interaction model of rays and attached them to both hands.</span></span> <span data-ttu-id="fd902-173">透過此對稱的設計，MRP 熟悉的使用者不需要了解另一個用於目前指向及操作的互動模型，在使用 HoloLen 2 時，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="fd902-173">With this symmetric design, users who are familiar with MRP won't need to learn another interaction model for far pointing and manipulation when they use HoloLen 2, and vice versa.</span></span>    

![](images/Symmetric-Design-For-Rays-720px.jpg)<br>

## <a name="instinctual-gestures"></a><span data-ttu-id="fd902-174">Instinctual 筆勢</span><span class="sxs-lookup"><span data-stu-id="fd902-174">Instinctual gestures</span></span>

![](images/Instinctual-Gestures-Far-720px.jpg)

## <a name="see-also"></a><span data-ttu-id="fd902-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd902-175">See also</span></span>
* [<span data-ttu-id="fd902-176">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="fd902-176">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="fd902-177">手部直接操作</span><span class="sxs-lookup"><span data-stu-id="fd902-177">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="fd902-178">本能互動</span><span class="sxs-lookup"><span data-stu-id="fd902-178">Instinctual interactions</span></span>](interaction-fundamentals.md)

