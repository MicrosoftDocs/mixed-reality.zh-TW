---
title: 可互動物件
description: 一個按鈕很長的比喻，是用來觸發2D 抽象世界中的事件。 在三維混合現實世界中，我們不再需要局限于此抽象概念。
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: 混合的現實、控制項、互動、ui、ux
ms.openlocfilehash: 36ca1feeba0e3bf028c64fe7b559d263a8088b96
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438732"
---
# <a name="interactable-object"></a><span data-ttu-id="270fd-105">可互動物件</span><span class="sxs-lookup"><span data-stu-id="270fd-105">Interactable object</span></span>

![Interactible 物件](images/InteractableExamples.png)

<span data-ttu-id="270fd-107">一個按鈕很長的比喻，是用來觸發2D 抽象世界中的事件。</span><span class="sxs-lookup"><span data-stu-id="270fd-107">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="270fd-108">在三維混合現實世界中，我們不再需要局限于此抽象概念。</span><span class="sxs-lookup"><span data-stu-id="270fd-108">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="270fd-109">任何專案都可以是觸發事件的**可互動物件**。</span><span class="sxs-lookup"><span data-stu-id="270fd-109">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="270fd-110">可互動物件可以從資料表上的咖啡杯，呈現為以空中浮動的球形文字。</span><span class="sxs-lookup"><span data-stu-id="270fd-110">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="270fd-111">在某些情況下，我們仍會使用傳統按鈕，例如在對話方塊 UI 中。</span><span class="sxs-lookup"><span data-stu-id="270fd-111">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="270fd-112">按鈕的視覺表示方式取決於內容。</span><span class="sxs-lookup"><span data-stu-id="270fd-112">The visual representation of the button depends on the context.</span></span>

<br>

---


## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="270fd-113">可互動物件的重要屬性</span><span class="sxs-lookup"><span data-stu-id="270fd-113">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="270fd-114">視覺提示</span><span class="sxs-lookup"><span data-stu-id="270fd-114">Visual cues</span></span>

<span data-ttu-id="270fd-115">視覺提示是以光線的形式收到的感應式提示，並在視覺認知期間由視覺系統處理。</span><span class="sxs-lookup"><span data-stu-id="270fd-115">Visual cues are sensory cues received by the eye in the form of light and processed by the visual system during visual perception.</span></span> <span data-ttu-id="270fd-116">由於視覺系統是許多物種的主要功能，特別是人類的視覺提示，是世界的認知方式的大量資訊來源。</span><span class="sxs-lookup"><span data-stu-id="270fd-116">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="270fd-117">由於「全像攝影」物件在混合現實中與真實世界的環境混合，因此可能很難以瞭解哪些物件可以互動。</span><span class="sxs-lookup"><span data-stu-id="270fd-117">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="270fd-118">針對您的體驗中的任何可互動物件，請務必為每個輸入狀態提供區分的視覺提示。</span><span class="sxs-lookup"><span data-stu-id="270fd-118">For any interactable objects in your experience, it is important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="270fd-119">這可協助使用者瞭解您的經驗可互動，並使用一致的互動方法，讓使用者安心。</span><span class="sxs-lookup"><span data-stu-id="270fd-119">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="270fd-120">遠互動</span><span class="sxs-lookup"><span data-stu-id="270fd-120">Far interactions</span></span>

<span data-ttu-id="270fd-121">對於使用者可以與注視、手光線和運動控制器光線互動的任何物件，我們建議您針對這三種輸入狀態有不同的視覺提示：</span><span class="sxs-lookup"><span data-stu-id="270fd-121">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend to have different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="270fd-122">![interactibleobject-狀態-預設](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="270fd-122">![interactibleobject-states-default](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="270fd-123">**預設（觀察）狀態**</span><span class="sxs-lookup"><span data-stu-id="270fd-123">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="270fd-124">物件的預設閒置狀態。</span><span class="sxs-lookup"><span data-stu-id="270fd-124">Default idle state of the object.</span></span>
    <span data-ttu-id="270fd-125">游標不在物件上。</span><span class="sxs-lookup"><span data-stu-id="270fd-125">The cursor is not on the object.</span></span> <span data-ttu-id="270fd-126">未偵測到手。</span><span class="sxs-lookup"><span data-stu-id="270fd-126">Hand is not detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="270fd-127">![interactibleobject 狀態-目標](images/interactibleobject-states-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="270fd-127">![interactibleobject-states-targeted](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="270fd-128">**目標（暫留）狀態**</span><span class="sxs-lookup"><span data-stu-id="270fd-128">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="270fd-129">當物件以注視游標、手指鄰近或移動控制器的指標為目標時。</span><span class="sxs-lookup"><span data-stu-id="270fd-129">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="270fd-130">游標位於物件上。</span><span class="sxs-lookup"><span data-stu-id="270fd-130">The cursor is on the object.</span></span> <span data-ttu-id="270fd-131">已偵測到手中，已備妥。</span><span class="sxs-lookup"><span data-stu-id="270fd-131">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="270fd-132">![interactibleobject 狀態-按下的](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="270fd-132">![interactibleobject-states-pressed](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="270fd-133">**已按下狀態**</span><span class="sxs-lookup"><span data-stu-id="270fd-133">**Pressed state**</span></span><br>
        <span data-ttu-id="270fd-134">當按下滑鼠按鍵時，手指按下或移動控制器的 [選取] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="270fd-134">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="270fd-135">游標位於物件上。</span><span class="sxs-lookup"><span data-stu-id="270fd-135">The cursor is on the object.</span></span> <span data-ttu-id="270fd-136">偵測到手中，按下 [空中]。</span><span class="sxs-lookup"><span data-stu-id="270fd-136">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="270fd-137">您可以使用像是反白顯示或縮放等技術，為使用者的輸入狀態提供視覺提示。</span><span class="sxs-lookup"><span data-stu-id="270fd-137">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="270fd-138">在混合的現實中，您可以在 [開始] 功能表上找到視覺化不同輸入狀態的範例，以及使用應用程式列按鈕。</span><span class="sxs-lookup"><span data-stu-id="270fd-138">In mixed reality, you can find the examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="270fd-139">以下是這些狀態在「全像攝影」**按鈕**上的外觀：</span><span class="sxs-lookup"><span data-stu-id="270fd-139">Here is what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="270fd-140">![interactibleobject-狀態-預設](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="270fd-140">![interactibleobject-states-default](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="270fd-141">**預設（觀察）狀態**</span><span class="sxs-lookup"><span data-stu-id="270fd-141">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="270fd-142">![interactibleobject 狀態-目標](images/MRTK_InteractableState-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="270fd-142">![interactibleobject-states-targeted](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="270fd-143">**目標（暫留）狀態**</span><span class="sxs-lookup"><span data-stu-id="270fd-143">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="270fd-144">![interactibleobject 狀態-按下的](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="270fd-144">![interactibleobject-states-pressed](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="270fd-145">**已按下狀態**</span><span class="sxs-lookup"><span data-stu-id="270fd-145">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="270fd-146">近乎互動（direct）</span><span class="sxs-lookup"><span data-stu-id="270fd-146">Near interactions (direct)</span></span> 

<span data-ttu-id="270fd-147">HoloLens 2 支援明確的手寫追蹤輸入，可讓您與物件互動。</span><span class="sxs-lookup"><span data-stu-id="270fd-147">HoloLens 2 supports articulated hand tracking input which allows you to interact with objects.</span></span> <span data-ttu-id="270fd-148">如果沒有 haptic 的意見反應和完美的深度認知，有時可能很難分辨出手距物件的距離，或您是否觸及它。</span><span class="sxs-lookup"><span data-stu-id="270fd-148">Without haptic feedback and perfect depth perception, it can sometimes be hard to tell how far away your hand is from an object or whether you are touching it.</span></span> <span data-ttu-id="270fd-149">請務必提供足夠的視覺提示來傳達物件的狀態，特別是與該物件相關的實際操作狀態。</span><span class="sxs-lookup"><span data-stu-id="270fd-149">It is important to provide enough visual cues to communicate the state of the object and in particular the state of your hands in relation to that object.</span></span>

<span data-ttu-id="270fd-150">使用視覺效果意見反應來傳達下列內容：</span><span class="sxs-lookup"><span data-stu-id="270fd-150">Use visual feedback to communicate the following:</span></span>
* <span data-ttu-id="270fd-151">**預設值（觀察）** ：物件的預設閒置狀態。</span><span class="sxs-lookup"><span data-stu-id="270fd-151">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="270fd-152">暫**留：當**手近于全息影像時，將視覺效果變更為以全像投影來溝通。</span><span class="sxs-lookup"><span data-stu-id="270fd-152">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="270fd-153">**距離和互動點**：正如手中的「全像投影」，設計意見反應來傳達預定的互動點，以及從物件到手指的距離</span><span class="sxs-lookup"><span data-stu-id="270fd-153">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, as well as how far from the object the finger is</span></span>
* <span data-ttu-id="270fd-154">**連絡人開始**：變更視覺效果（淺色、色彩）以溝通觸控已發生</span><span class="sxs-lookup"><span data-stu-id="270fd-154">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="270fd-155">**Grasped**： Grasped 物件時變更視覺效果（淺色、色彩）</span><span class="sxs-lookup"><span data-stu-id="270fd-155">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="270fd-156">**連絡人結束**：觸控結束時變更視覺效果（淺色、色彩）</span><span class="sxs-lookup"><span data-stu-id="270fd-156">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="270fd-157">![停留（目前）](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="270fd-157">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="270fd-158">**暫留（目前）**</span><span class="sxs-lookup"><span data-stu-id="270fd-158">**Hover (Far)**</span></span><br>
        <span data-ttu-id="270fd-159">根據手的鄰近程度來反白顯示。</span><span class="sxs-lookup"><span data-stu-id="270fd-159">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="270fd-160">![暫留（附近）](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="270fd-160">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="270fd-161">**暫留（接近）**</span><span class="sxs-lookup"><span data-stu-id="270fd-161">**Hover (Near)**</span></span><br>
        <span data-ttu-id="270fd-162">將大小變更反白顯示為根據手的距離。</span><span class="sxs-lookup"><span data-stu-id="270fd-162">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="270fd-163">![觸控/按](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="270fd-163">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="270fd-164">**觸控/按**</span><span class="sxs-lookup"><span data-stu-id="270fd-164">**Touch / press**</span></span><br>
        <span data-ttu-id="270fd-165">視覺效果加上音訊意見反應。</span><span class="sxs-lookup"><span data-stu-id="270fd-165">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="270fd-166">![抓住](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="270fd-166">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="270fd-167">**領會**</span><span class="sxs-lookup"><span data-stu-id="270fd-167">**Grasp**</span></span><br>
        <span data-ttu-id="270fd-168">視覺效果加上音訊意見反應。</span><span class="sxs-lookup"><span data-stu-id="270fd-168">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="270fd-169">[HoloLens 2 上的按鈕](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)是如何視覺化不同輸入互動狀態的範例：</span><span class="sxs-lookup"><span data-stu-id="270fd-169">A [button on HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="270fd-170">![預設](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="270fd-170">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="270fd-171">**預設**</span><span class="sxs-lookup"><span data-stu-id="270fd-171">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="270fd-172">![滑鼠停留](images/640px-interactibleobject-pressablebutton-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="270fd-172">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="270fd-173">**逐個**</span><span class="sxs-lookup"><span data-stu-id="270fd-173">**Hover**</span></span><br>
        <span data-ttu-id="270fd-174">顯示以鄰近性為基礎的光源效果。</span><span class="sxs-lookup"><span data-stu-id="270fd-174">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="270fd-175">![觸控](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="270fd-175">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="270fd-176">**觸控**</span><span class="sxs-lookup"><span data-stu-id="270fd-176">**Touch**</span></span><br>
        <span data-ttu-id="270fd-177">顯示 ripple 效果。</span><span class="sxs-lookup"><span data-stu-id="270fd-177">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="270fd-178">![按](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="270fd-178">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="270fd-179">**出版**</span><span class="sxs-lookup"><span data-stu-id="270fd-179">**Press**</span></span><br>
        <span data-ttu-id="270fd-180">移動 front 盤子。</span><span class="sxs-lookup"><span data-stu-id="270fd-180">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="270fd-181">HoloLens 2 上的「環形」視覺提示</span><span class="sxs-lookup"><span data-stu-id="270fd-181">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="270fd-182">在 HoloLens 2 上有其他視覺提示，可協助使用者深入瞭解。</span><span class="sxs-lookup"><span data-stu-id="270fd-182">On HoloLens 2, there is an additional visual cue which can help the user's perception of depth.</span></span> <span data-ttu-id="270fd-183">當 fingertip 接近物件時，會顯示 fingertip 附近的環形並相應減少。</span><span class="sxs-lookup"><span data-stu-id="270fd-183">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="270fd-184">當到達已按下的狀態時，環形最後會聚合成一個點。</span><span class="sxs-lookup"><span data-stu-id="270fd-184">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="270fd-185">此視覺效果 affordance 可協助使用者瞭解他們與物件之間的距離。</span><span class="sxs-lookup"><span data-stu-id="270fd-185">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="270fd-186">*影片迴圈：根據距離周框方塊的視覺效果意見反應範例*</span><span class="sxs-lookup"><span data-stu-id="270fd-186">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="270fd-187">![空間](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="270fd-187">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="270fd-188">![視覺效果意見反應](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="270fd-188">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="270fd-189">音訊提示</span><span class="sxs-lookup"><span data-stu-id="270fd-189">Audio cues</span></span>

<span data-ttu-id="270fd-190">對於直接的互動，適當的音訊意見反應可以大幅改善使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="270fd-190">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="270fd-191">使用音訊意見反應來傳達下列內容：</span><span class="sxs-lookup"><span data-stu-id="270fd-191">Use audio feedback to communicate the following:</span></span>
* <span data-ttu-id="270fd-192">**連絡人開始**：觸控開始時播放音效</span><span class="sxs-lookup"><span data-stu-id="270fd-192">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="270fd-193">**連絡人結束**：在觸控結束時播放音效</span><span class="sxs-lookup"><span data-stu-id="270fd-193">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="270fd-194">**抓取開始**：抓取開始時播放音效</span><span class="sxs-lookup"><span data-stu-id="270fd-194">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="270fd-195">**抓取結束**：抓取結束時播放音效</span><span class="sxs-lookup"><span data-stu-id="270fd-195">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="270fd-196">語音命令</span><span class="sxs-lookup"><span data-stu-id="270fd-196">Voice commanding</span></span><br>
        <span data-ttu-id="270fd-197">針對任何可互動物件，請務必支援替代互動選項。</span><span class="sxs-lookup"><span data-stu-id="270fd-197">For any interactable objects, it is important to support alternative interaction options.</span></span> <span data-ttu-id="270fd-198">根據預設，我們建議可互動的任何物件都支援[語音命令](voice-design.md)。</span><span class="sxs-lookup"><span data-stu-id="270fd-198">By default, we recommend that [voice commanding](voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="270fd-199">若要改善可搜尋性，您也可以在停留狀態期間提供工具提示。</span><span class="sxs-lookup"><span data-stu-id="270fd-199">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="270fd-200">*影像：語音命令的工具提示*</span><span class="sxs-lookup"><span data-stu-id="270fd-200">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![語音命令](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a><span data-ttu-id="270fd-202">大小調整建議</span><span class="sxs-lookup"><span data-stu-id="270fd-202">Sizing recommendations</span></span> 

<span data-ttu-id="270fd-203">若要確保使用者可以輕鬆地觸及所有可互動物件，建議您根據其與使用者的距離，確定可互動符合最小大小（視覺效果的角度，通常以度為單位測量）。</span><span class="sxs-lookup"><span data-stu-id="270fd-203">To ensure that all interactable objects can easily be touched by users, we recommend that you make sure the interactable meets a minimum size (the visual angle often measured in degrees of visual arc) based on the distance it is placed from the user.</span></span> <span data-ttu-id="270fd-204">視覺角度是以使用者眼和物件之間的距離為依據，並維持不變，而目標的實體大小可能會隨著使用者變更的距離而改變。</span><span class="sxs-lookup"><span data-stu-id="270fd-204">Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="270fd-205">若要根據與使用者的距離來判斷物件的必要實體大小，請嘗試使用視覺角度計算機，例如[這一項](https://elvers.us/perception/visualAngle/)。</span><span class="sxs-lookup"><span data-stu-id="270fd-205">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="270fd-206">以下是最小可互動內容大小的建議。</span><span class="sxs-lookup"><span data-stu-id="270fd-206">Below are the recommendations for minimum sizes of interactable content.</span></span>


### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="270fd-207">直接操作的目標大小</span><span class="sxs-lookup"><span data-stu-id="270fd-207">Target size for direct hand interaction</span></span>

| <span data-ttu-id="270fd-208">長途電話</span><span class="sxs-lookup"><span data-stu-id="270fd-208">Distance</span></span> | <span data-ttu-id="270fd-209">視角</span><span class="sxs-lookup"><span data-stu-id="270fd-209">Viewing angle</span></span> | <span data-ttu-id="270fd-210">Size</span><span class="sxs-lookup"><span data-stu-id="270fd-210">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="270fd-211">45cm</span><span class="sxs-lookup"><span data-stu-id="270fd-211">45cm</span></span>  | <span data-ttu-id="270fd-212">不小於2°</span><span class="sxs-lookup"><span data-stu-id="270fd-212">no smaller than 2°</span></span> | <span data-ttu-id="270fd-213">1.6 x 1.6 cm</span><span class="sxs-lookup"><span data-stu-id="270fd-213">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="270fd-214">直接操作](images/TargetSizingNear.jpg) 的 ![目標大小</span><span class="sxs-lookup"><span data-stu-id="270fd-214">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="270fd-215">*直接操作的目標大小*</span><span class="sxs-lookup"><span data-stu-id="270fd-215">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="270fd-216">按鈕的目標大小</span><span class="sxs-lookup"><span data-stu-id="270fd-216">Target size for buttons</span></span>

<span data-ttu-id="270fd-217">建立直接互動的按鈕時，我們建議使用較大大小的最小值 3.2 x 3.2 cm，以確保有足夠的空間可包含圖示，而且可能會有一些文字。</span><span class="sxs-lookup"><span data-stu-id="270fd-217">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there is enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="270fd-218">長途電話</span><span class="sxs-lookup"><span data-stu-id="270fd-218">Distance</span></span> | <span data-ttu-id="270fd-219">最小大小</span><span class="sxs-lookup"><span data-stu-id="270fd-219">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="270fd-220">45cm</span><span class="sxs-lookup"><span data-stu-id="270fd-220">45cm</span></span>  | <span data-ttu-id="270fd-221">3.2 x 3.2 cm</span><span class="sxs-lookup"><span data-stu-id="270fd-221">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="270fd-222">![按鈕的目標大小](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="270fd-222">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="270fd-223">*按鈕的目標大小*</span><span class="sxs-lookup"><span data-stu-id="270fd-223">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="270fd-224">右手光線或注視互動的目標大小</span><span class="sxs-lookup"><span data-stu-id="270fd-224">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="270fd-225">長途電話</span><span class="sxs-lookup"><span data-stu-id="270fd-225">Distance</span></span> | <span data-ttu-id="270fd-226">視角</span><span class="sxs-lookup"><span data-stu-id="270fd-226">Viewing angle</span></span> | <span data-ttu-id="270fd-227">Size</span><span class="sxs-lookup"><span data-stu-id="270fd-227">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="270fd-228">2m</span><span class="sxs-lookup"><span data-stu-id="270fd-228">2m</span></span>  | <span data-ttu-id="270fd-229">不小於1°</span><span class="sxs-lookup"><span data-stu-id="270fd-229">no smaller than 1°</span></span> | <span data-ttu-id="270fd-230">3.5 x 3.5 cm</span><span class="sxs-lookup"><span data-stu-id="270fd-230">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="270fd-231">![右手光線或注視互動](images/TargetSizingFar.jpg) 的目標大小</span><span class="sxs-lookup"><span data-stu-id="270fd-231">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="270fd-232">*右手光線或注視互動的目標大小*</span><span class="sxs-lookup"><span data-stu-id="270fd-232">*Target size for hand ray or gaze interaction*</span></span>


<br>

---


## <a name="creating-interactable-object-with-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="270fd-233">使用混合現實工具組（MRTK）建立可互動物件</span><span class="sxs-lookup"><span data-stu-id="270fd-233">Creating interactable object with Mixed Reality Toolkit (MRTK)</span></span>

<span data-ttu-id="270fd-234">在 **[混合式現實工具](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 組中，您可以找到可協助您建立可互動物件的一系列 Unity 腳本和 prefabs。</span><span class="sxs-lookup"><span data-stu-id="270fd-234">In the **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can find the series of Unity scripts and prefabs that will help you create interactable objects.</span></span> <span data-ttu-id="270fd-235">您可以使用這些來讓物件回應各種類型的輸入互動狀態。</span><span class="sxs-lookup"><span data-stu-id="270fd-235">You can use these to make objects respond to various types of input interaction states.</span></span>

* [<span data-ttu-id="270fd-236">可互動</span><span class="sxs-lookup"><span data-stu-id="270fd-236">Interactable</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [<span data-ttu-id="270fd-237">Button</span><span class="sxs-lookup"><span data-stu-id="270fd-237">Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="270fd-238">手動互動範例場景</span><span class="sxs-lookup"><span data-stu-id="270fd-238">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="270fd-239">MixedRealityToolkit 的標準著色器提供各種選項，例如**近光源**，可協助您建立視覺效果和音訊提示。</span><span class="sxs-lookup"><span data-stu-id="270fd-239">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* [<span data-ttu-id="270fd-240">MRTK 標準著色器</span><span class="sxs-lookup"><span data-stu-id="270fd-240">MRTK Standard Shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


<br>

---

## <a name="see-also"></a><span data-ttu-id="270fd-241">請參閱</span><span class="sxs-lookup"><span data-stu-id="270fd-241">See also</span></span>

* [<span data-ttu-id="270fd-242">周框方塊</span><span class="sxs-lookup"><span data-stu-id="270fd-242">Bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="270fd-243">物件集合</span><span class="sxs-lookup"><span data-stu-id="270fd-243">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="270fd-244">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="270fd-244">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="270fd-245">語音輸入</span><span class="sxs-lookup"><span data-stu-id="270fd-245">Voice input</span></span>](voice-input.md)
