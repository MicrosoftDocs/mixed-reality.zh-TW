---
title: 手部指向和行動
description: 指向和行動輸入模型的概觀
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境, 互動, 設計, hololens, 手部, 遠方, 指向和行動
ms.openlocfilehash: 4e19a7fd95bac42283ce3e3176a1363afda8f220
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414543"
---
# <a name="point-and-commit-with-hands"></a><span data-ttu-id="3807f-104">手部指向和行動</span><span class="sxs-lookup"><span data-stu-id="3807f-104">Point and commit with hands</span></span>
<span data-ttu-id="3807f-105">手部指向和行動是輸入模型，可讓使用者鎖定目標、選取和操作遠方的 2D 內容與 3D 物件。</span><span class="sxs-lookup"><span data-stu-id="3807f-105">Point and commit with hands is an input model that enables users to target, select and manipulate 2D content and 3D objects in the distance.</span></span> <span data-ttu-id="3807f-106">「遠方 (far)」互動技術是混合實境特有的技術，不是使用者與真實世界自然互動的方式。</span><span class="sxs-lookup"><span data-stu-id="3807f-106">This "far" interaction technique is unique to mixed reality, and is not a way humans naturally intereact with the real world.</span></span> <span data-ttu-id="3807f-107">例如，在超級英雄電影「X 戰警」  中，[萬磁王](https://en.wikipedia.org/wiki/Magneto_(comics))能夠使用他的手觸碰和操作遠方物件。</span><span class="sxs-lookup"><span data-stu-id="3807f-107">For example, in the super hero movie, *X-Men*, the character [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) is capable of reaching out and manipulating a far object in the distance with his hands.</span></span> <span data-ttu-id="3807f-108">這不是人類在現實中可做到的事。</span><span class="sxs-lookup"><span data-stu-id="3807f-108">This is not something humans can do in reality.</span></span> <span data-ttu-id="3807f-109">在 HoloLens (AR) 和混合實境 (MR) 中，我們會賦予使用者這個神奇的力量，來打破真實世界的實質限制，而且我們不只透過全像攝影來提供有趣的體驗，還會讓使用者互動變得更有效率。</span><span class="sxs-lookup"><span data-stu-id="3807f-109">In both HoloLens (AR) and Mixed Reality (MR), we equip users with this magical power, breaking the physical constraint of the real world, not only to have a fun experience with holographic contents but also to make user interactions more effective and efficient.</span></span>

## <a name="device-support"></a><span data-ttu-id="3807f-110">裝置支援</span><span class="sxs-lookup"><span data-stu-id="3807f-110">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="3807f-111"><strong>輸入模型</strong></span><span class="sxs-lookup"><span data-stu-id="3807f-111"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="3807f-112"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="3807f-112"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="3807f-113"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="3807f-113"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="3807f-114"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="3807f-114"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="3807f-115">手部指向和行動</span><span class="sxs-lookup"><span data-stu-id="3807f-115">Point and commit with hands</span></span></td>
     <td><span data-ttu-id="3807f-116">❌ 不支援</span><span class="sxs-lookup"><span data-stu-id="3807f-116">❌ Not supported</span></span></td>
     <td><span data-ttu-id="3807f-117">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="3807f-117">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="3807f-118">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="3807f-118">✔️ Recommended</span></span></td>
</tr>
</table>


<span data-ttu-id="3807f-119">指向和行動 (也稱為 hands far) 是利用新式關節手部追蹤系統的新功能之一。</span><span class="sxs-lookup"><span data-stu-id="3807f-119">Point and commit, also known as hands far, is one of the new features that utilizes the new articulated hand-tracking system.</span></span> <span data-ttu-id="3807f-120">透過運動控制器使用的沈浸式耳機也是以此輸入模型作為主要輸入模型。</span><span class="sxs-lookup"><span data-stu-id="3807f-120">This input model is also the primary input model on immersive headsets through the use of motion controllers.</span></span>

## <a name="hand-rays"></a><span data-ttu-id="3807f-121">手部光線 (Hand Ray)</span><span class="sxs-lookup"><span data-stu-id="3807f-121">Hand rays</span></span>

<span data-ttu-id="3807f-122">在 HoloLens 2 上，我們已建立可從使用者手掌中央發射的手部光線。</span><span class="sxs-lookup"><span data-stu-id="3807f-122">On HoloLens 2, we created a hand ray that shoots out from the center of the user's palm.</span></span> <span data-ttu-id="3807f-123">此光線將視為手的延伸。</span><span class="sxs-lookup"><span data-stu-id="3807f-123">This ray is treated as an extension of the hand.</span></span> <span data-ttu-id="3807f-124">光線末端會附加環狀游標，以指出光線與目標物件交集的位置。</span><span class="sxs-lookup"><span data-stu-id="3807f-124">A donut-shaped cursor is attached to the end of the ray to indicate the location where the ray intersects with a target object.</span></span> <span data-ttu-id="3807f-125">然後，游標所在的物件就能從手部接收手勢命令。</span><span class="sxs-lookup"><span data-stu-id="3807f-125">The object that the cursor lands on can then receive gestural commands from the hand.</span></span>

<span data-ttu-id="3807f-126">此基本手勢命令會藉由使用拇指與食指執行空中點選動作來觸發。</span><span class="sxs-lookup"><span data-stu-id="3807f-126">This basic gestural command is triggered by using the thumb and index finger to perform the air-tap action.</span></span> <span data-ttu-id="3807f-127">藉由使用手部光線進行指向及空中點選來行動，使用者就可以啟用按鈕或超連結。</span><span class="sxs-lookup"><span data-stu-id="3807f-127">By using the hand ray to point and air tap to commit, users can activate a button or a hyperlink.</span></span> <span data-ttu-id="3807f-128">藉由更多的複合手勢，使用者還能夠從遠處瀏覽網頁內容和操作 3D 物件。</span><span class="sxs-lookup"><span data-stu-id="3807f-128">With more composite gestures, users are capable of navigating web content and manipulating 3D objects from a distance.</span></span> <span data-ttu-id="3807f-129">手動光線的視覺化設計也會反應這些指向和行動狀態，請見下列圖示和說明：</span><span class="sxs-lookup"><span data-stu-id="3807f-129">The visual design of the hand ray should also react to these point and commit states, as described and shown below:</span></span> 

* <span data-ttu-id="3807f-130">在「指向」  狀態時，光線呈虛線，而指標呈環狀。</span><span class="sxs-lookup"><span data-stu-id="3807f-130">In the *pointing* state, the ray is a dash line and the cursor is a donut shape.</span></span>
* <span data-ttu-id="3807f-131">在「行動」  狀態時，光線變成一條實線，而游標會壓縮成一個點。</span><span class="sxs-lookup"><span data-stu-id="3807f-131">In the *commit* state, the ray turns into a solid line and the cursor shrinks to a dot.</span></span>

<span data-ttu-id="3807f-132">![手部光線的指向和行動狀態](images/Hand-Rays-720px.jpg)</span><span class="sxs-lookup"><span data-stu-id="3807f-132">![Pointing and commit states for hand rays](images/Hand-Rays-720px.jpg)</span></span><br>
<span data-ttu-id="3807f-133">*手部光線的指向 (左) 和行動 (右) 狀態*</span><span class="sxs-lookup"><span data-stu-id="3807f-133">*Pointing (left) and commit (right) states for hand rays*</span></span>

## <a name="transition-between-near-and-far"></a><span data-ttu-id="3807f-134">遠近轉換</span><span class="sxs-lookup"><span data-stu-id="3807f-134">Transition between near and far</span></span>

<span data-ttu-id="3807f-135">我們不是使用「以食指指向」之類的特定手勢來指引光線方向，而是設計讓光線從手掌發出，並釋出和保留五個手指頭來操作更多手勢，例如捏取和抓取。</span><span class="sxs-lookup"><span data-stu-id="3807f-135">Instead of using specific gestures, such as "pointing with index finger", to direct the ray, we designed the ray coming out from the center of the palm, releasing and reserving the five fingers for more manipulative gestures, such as pinch and grab.</span></span> <span data-ttu-id="3807f-136">透過這項設計，我們只需建立一個心智模型，即可針對遠近互動支援完全相同的一組手勢。</span><span class="sxs-lookup"><span data-stu-id="3807f-136">With this design, we create only one mental model, supporting exactly the same set of hand gestures for both near and far interaction.</span></span> <span data-ttu-id="3807f-137">您可以使用相同的抓取手勢來操作不同距離的物件。</span><span class="sxs-lookup"><span data-stu-id="3807f-137">You can use the same grab gesture to manipulate objects at different distances.</span></span> <span data-ttu-id="3807f-138">光線的引動過程會根據鄰近程度自動執行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3807f-138">The invocation of the rays is automatic and proximity based as follows:</span></span>

*  <span data-ttu-id="3807f-139">當物件位在手臂可及的範圍內 (大約 50 公分) 時，光線就會自動關閉，並建議您進行近距離互動。</span><span class="sxs-lookup"><span data-stu-id="3807f-139">When an object is within arm's length (roughly 50 cm), the rays are turned off automatically, encouraging near interaction.</span></span>
*  <span data-ttu-id="3807f-140">物件距離超過 50 公分時，光線就會開啟。</span><span class="sxs-lookup"><span data-stu-id="3807f-140">When the object is farther than 50 cm, the rays are turned on.</span></span> <span data-ttu-id="3807f-141">此轉換會很順利且流暢。</span><span class="sxs-lookup"><span data-stu-id="3807f-141">The transition should be smooth and seamless.</span></span>

<span data-ttu-id="3807f-142">![遠近互動都使用同一組手勢](images/Transition-Between-Near-And-Far-720px.jpg)</span><span class="sxs-lookup"><span data-stu-id="3807f-142">![The same set of hand gestures are used for both near and far interaction](images/Transition-Between-Near-And-Far-720px.jpg)</span></span><br>
<span data-ttu-id="3807f-143">*遠近互動都使用同一組手勢。*</span><span class="sxs-lookup"><span data-stu-id="3807f-143">*The same set of hand gestures are used for both near and far interaction.*</span></span>

## <a name="2d-slate-interaction"></a><span data-ttu-id="3807f-144">2D 平板互動</span><span class="sxs-lookup"><span data-stu-id="3807f-144">2D slate interaction</span></span>

<span data-ttu-id="3807f-145">2D 平板是裝載 2D 應用程式內容 (例如網頁瀏覽器) 的全像攝影容器。</span><span class="sxs-lookup"><span data-stu-id="3807f-145">A 2D slate is a holographic container hosting 2D app contents, such as a web browser.</span></span> <span data-ttu-id="3807f-146">以 2D 平板進行遠端互動的設計概念是，使用手部光線來鎖定目標和使用空中點選來選取項目。</span><span class="sxs-lookup"><span data-stu-id="3807f-146">The design concept for far interacting with a 2D slate is to use hand rays to target and air tap to select.</span></span> <span data-ttu-id="3807f-147">以手部光線鎖定目標後，使用者可以透過空中點選來觸發超連結或按鈕。</span><span class="sxs-lookup"><span data-stu-id="3807f-147">After targeting with a hand ray, users can air tap to trigger a hyperlink or a button.</span></span> <span data-ttu-id="3807f-148">他們可使用一隻手來進行「空中點選和拖曳」，進而上下捲動平板內容。</span><span class="sxs-lookup"><span data-stu-id="3807f-148">They can use one hand to "air tap and drag" to scroll slate content up and down.</span></span> <span data-ttu-id="3807f-149">使用兩隻手進行空中點選和拖曳的相對動作則可縮放平板內容。</span><span class="sxs-lookup"><span data-stu-id="3807f-149">The relative motion of using two hands to air tap and drag can zoom in and out the slate content.</span></span>

<span data-ttu-id="3807f-150">將手部光線的目標鎖定在角落和邊緣會顯示最接近的操作能供性 (affordance)。</span><span class="sxs-lookup"><span data-stu-id="3807f-150">Targeting the hand ray at the corners and edges reveals the closest manipulation affordance.</span></span> <span data-ttu-id="3807f-151">藉由「抓取並拖曳」操作能供性，使用者可以透過角落能供性執行統一的尺寸調整，以及可透過邊緣能供性來重排平板。</span><span class="sxs-lookup"><span data-stu-id="3807f-151">By "grab and drag" manipulation affordances, users can perform uniform scaling through the corner affordances, and can reflow the slate via the edge affordances.</span></span> <span data-ttu-id="3807f-152">藉由抓取並拖曳 2D 平板上方的 holobar，使用者可以移動整個平板。</span><span class="sxs-lookup"><span data-stu-id="3807f-152">Grabbing and dragging the holobar at the top of the 2D slate lets users move the entire slate.</span></span>

![2D 平板互動](images/2D-Slate-Interaction-Far-720px.jpg)

<span data-ttu-id="3807f-154">操作 2D 平板：</span><span class="sxs-lookup"><span data-stu-id="3807f-154">For manipulating the 2D slate:</span></span><br>

* <span data-ttu-id="3807f-155">使用者將手部光線指向角落或邊緣時，可顯示最接近的操作能供性。</span><span class="sxs-lookup"><span data-stu-id="3807f-155">Users point the hand ray at the corners or edges to reveal the closest manipulation affordance.</span></span> 
* <span data-ttu-id="3807f-156">藉由在能供性上套用操作手勢，使用者可以透過角落能供性執行統一的尺寸調整，以及可透過邊緣能供性來重排平板。</span><span class="sxs-lookup"><span data-stu-id="3807f-156">By applying a manipulation gesture on the affordance, users can perform uniform scaling through the corner affordance, and can reflow the slate via the edge affordance.</span></span> 
* <span data-ttu-id="3807f-157">藉由在 2D 平板頂端的 holobar 上套用操作手勢，使用者可以移動整個平板。</span><span class="sxs-lookup"><span data-stu-id="3807f-157">By applying a manipulation gesture on the holobar at the top of the 2D slate, users can move the entire slate.</span></span><br>

<br>

## <a name="3d-object-manipulation"></a><span data-ttu-id="3807f-158">3D 物件操作</span><span class="sxs-lookup"><span data-stu-id="3807f-158">3D object manipulation</span></span>

<span data-ttu-id="3807f-159">在直接操作中，有兩種方法可讓使用者操作 3D 物件：能供性操作與非能供性操作。</span><span class="sxs-lookup"><span data-stu-id="3807f-159">In direct manipulation, there are two ways for users to manipulate 3D objects: affordance-based manipulation and non-affordance based manipulation.</span></span> <span data-ttu-id="3807f-160">在指向和行動模型中，使用者都能透過手部光線來完成完全相同的工作。</span><span class="sxs-lookup"><span data-stu-id="3807f-160">In the point and commit model, users are capable of achieving exactly the same tasks through the hand rays.</span></span> <span data-ttu-id="3807f-161">不需要進行任何其他學習。</span><span class="sxs-lookup"><span data-stu-id="3807f-161">No additional learning is needed.</span></span><br>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="3807f-162">能供性操作</span><span class="sxs-lookup"><span data-stu-id="3807f-162">Affordance-based manipulation</span></span>
<span data-ttu-id="3807f-163">使用者使用手部光線來指向並顯示週框方塊和操作能供性。</span><span class="sxs-lookup"><span data-stu-id="3807f-163">Users use hand rays to point and reveal the bounding box and manipulation affordances.</span></span> <span data-ttu-id="3807f-164">使用者可以將操作手勢套用到週框方塊來移動整個物件，套用到邊緣能供性可旋轉物件，套用到角落能供性可統一調整物件大小。</span><span class="sxs-lookup"><span data-stu-id="3807f-164">Users can apply the manipulation gesture on the bounding box to move the whole object, on the edge affordances to rotate, and on the corner affordances to scale uniformly.</span></span> <br>

![能供性操作](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="3807f-166">非能供性操作</span><span class="sxs-lookup"><span data-stu-id="3807f-166">Non-affordance based manipulation</span></span>
<span data-ttu-id="3807f-167">使用者透過手部光線指向來顯示週框方塊，然後直接在其上方套用操作手勢。</span><span class="sxs-lookup"><span data-stu-id="3807f-167">Users point with hand rays to reveal the bounding box then directly apply manipulation gestures on it.</span></span> <span data-ttu-id="3807f-168">若使用一隻手，物件的轉譯和旋轉會與手的動作和方向相關聯。</span><span class="sxs-lookup"><span data-stu-id="3807f-168">With one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="3807f-169">若使用兩隻手，使用者可以根據兩隻手的相對動作來轉譯、縮放及旋轉週框方塊。</span><span class="sxs-lookup"><span data-stu-id="3807f-169">With two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span><br>

<br>

## <a name="instinctual-gestures"></a><span data-ttu-id="3807f-170">本能手勢</span><span class="sxs-lookup"><span data-stu-id="3807f-170">Instinctual gestures</span></span>
<span data-ttu-id="3807f-171">指向和行動的本能手勢基本上類似於[手部直接操作](direct-manipulation.md)。</span><span class="sxs-lookup"><span data-stu-id="3807f-171">The concept of instinctual gestures for point and commit is similar to that for [direct manipulation with hands](direct-manipulation.md).</span></span> <span data-ttu-id="3807f-172">使用者在 3D 物件上執行的手勢，皆由 UI 能供性的設計來引導。</span><span class="sxs-lookup"><span data-stu-id="3807f-172">The gestures users perform on a 3D object are guided by the design of UI affordances.</span></span> <span data-ttu-id="3807f-173">例如，在使用者想使用五隻手指頭來抓取較大的物件時，小型控點可能會促使使用者運用其拇指與食指來捏取物件。</span><span class="sxs-lookup"><span data-stu-id="3807f-173">For example, a small control point might motivate users to pinch with their thumb and index finger, while a user might want to grab a larger object using all five fingers.</span></span>

![本能手勢](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a><span data-ttu-id="3807f-175">手部與 6 DoF 控制器之間的對稱設計</span><span class="sxs-lookup"><span data-stu-id="3807f-175">Symmetric design between hands and 6 DoF controller</span></span> 
<span data-ttu-id="3807f-176">一開始，用於遠距互動的指向和行動概念是針對混合實境入口 (MRP) 所建立及定義，在該入口中，使用者會戴著沉浸式頭戴裝置，並透過運動控制器來與 3D 物件互動。</span><span class="sxs-lookup"><span data-stu-id="3807f-176">The concept of point and commit for far interaction was initially created and defined for the Mixed Reality Portal (MRP) where a user wears an immersive headset and interacts with 3D objects via motion controllers.</span></span> <span data-ttu-id="3807f-177">運動控制器會發射光線來指向及操作遠方物件。</span><span class="sxs-lookup"><span data-stu-id="3807f-177">The motion controllers shoot out rays for pointing and manipulating far objects.</span></span> <span data-ttu-id="3807f-178">控制器上有按鈕，可用來進一步執行不同動作。</span><span class="sxs-lookup"><span data-stu-id="3807f-178">There are buttons on the controllers for further committing different actions.</span></span> <span data-ttu-id="3807f-179">我們運用光線的互動模型，並將其連結至雙手。</span><span class="sxs-lookup"><span data-stu-id="3807f-179">We leverage the interaction model of rays and attached them to both hands.</span></span> <span data-ttu-id="3807f-180">透過此對稱設計，熟悉 MRP 的使用者在使用 HoloLen 2 時，不需要學習另一個用於遠端指向及操作的互動模型，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="3807f-180">With this symmetric design, users who are familiar with MRP won't need to learn another interaction model for far pointing and manipulation when they use HoloLen 2, and vice versa.</span></span>    

![手部與 6 DoF 控制器之間的對稱設計](images/Symmetric-Design-For-Rays-720px.jpg)<br>


## <a name="see-also"></a><span data-ttu-id="3807f-182">請參閱</span><span class="sxs-lookup"><span data-stu-id="3807f-182">See also</span></span>
* [<span data-ttu-id="3807f-183">頭部注視並認可</span><span class="sxs-lookup"><span data-stu-id="3807f-183">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="3807f-184">手部直接操作</span><span class="sxs-lookup"><span data-stu-id="3807f-184">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="3807f-185">本能互動</span><span class="sxs-lookup"><span data-stu-id="3807f-185">Instinctual interactions</span></span>](interaction-fundamentals.md)

