---
title: 可互動物件
description: 一個按鈕很長的比喻, 是用來觸發2D 抽象世界中的事件。 在三維混合現實世界中, 我們不再需要局限于此抽象概念。
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: 混合的現實、控制項、互動、ui、ux
ms.openlocfilehash: 57299cbb758a69603fc68ad5d43af8f2216e5104
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415357"
---
# <a name="interactable-object"></a><span data-ttu-id="eeea3-105">可互動物件</span><span class="sxs-lookup"><span data-stu-id="eeea3-105">Interactable object</span></span>

<span data-ttu-id="eeea3-106">一個按鈕很長的比喻, 是用來觸發2D 抽象世界中的事件。</span><span class="sxs-lookup"><span data-stu-id="eeea3-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="eeea3-107">在三維混合現實世界中, 我們不再需要局限于此抽象概念。</span><span class="sxs-lookup"><span data-stu-id="eeea3-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="eeea3-108">任何專案都可以是觸發事件的**可互動物件**。</span><span class="sxs-lookup"><span data-stu-id="eeea3-108">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="eeea3-109">可互動物件可以從資料表上的咖啡杯, 呈現為以空中浮動的球形文字。</span><span class="sxs-lookup"><span data-stu-id="eeea3-109">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="eeea3-110">在某些情況下, 我們仍會使用傳統按鈕, 例如在對話方塊 UI 中。</span><span class="sxs-lookup"><span data-stu-id="eeea3-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="eeea3-111">按鈕的視覺表示方式取決於內容。</span><span class="sxs-lookup"><span data-stu-id="eeea3-111">The visual representation of the button depends on the context.</span></span>

![Interactible 物件](images/640px-interactibleobject-hero-640px.jpg)


## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="eeea3-113">可互動物件的重要屬性</span><span class="sxs-lookup"><span data-stu-id="eeea3-113">Important properties of the interactable object</span></span>

### <a name="visual-cue"></a><span data-ttu-id="eeea3-114">視覺提示</span><span class="sxs-lookup"><span data-stu-id="eeea3-114">Visual cue</span></span>

<span data-ttu-id="eeea3-115">視覺提示是以光線的形式收到的感應式提示, 並在視覺認知期間由視覺系統處理。</span><span class="sxs-lookup"><span data-stu-id="eeea3-115">Visual cues are sensory cues received by the eye in the form of light and processed by the visual system during visual perception.</span></span> <span data-ttu-id="eeea3-116">由於視覺系統是許多物種的主要功能, 特別是人類的視覺提示, 是世界的認知方式的大量資訊來源。</span><span class="sxs-lookup"><span data-stu-id="eeea3-116">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="eeea3-117">在混合的現實中, 由於全像攝影物件與真實世界的環境混合, 因此可能很難以瞭解哪些物件是可互動的。</span><span class="sxs-lookup"><span data-stu-id="eeea3-117">In mixed reality, since the holographic objects are mixed with the real-world environment, it could be difficult to understand which objects are interactable.</span></span> <span data-ttu-id="eeea3-118">針對您的體驗中的任何可互動物件, 請務必提供每個輸入狀態的區分視覺提示。</span><span class="sxs-lookup"><span data-stu-id="eeea3-118">For any interactable objects in your experience, it is important to provide differentiated visual cue for each input state.</span></span> <span data-ttu-id="eeea3-119">這可協助使用者瞭解您的經驗可互動, 並讓使用者安心使用一致的互動方式。</span><span class="sxs-lookup"><span data-stu-id="eeea3-119">This helps the user understand which part of your experience is interactable and makes the user confident with consistent interaction method.</span></span>

#### <a name="far-interactions"></a><span data-ttu-id="eeea3-120">遠互動</span><span class="sxs-lookup"><span data-stu-id="eeea3-120">Far interactions</span></span>

<span data-ttu-id="eeea3-121">對於使用者可以與注視、手光線和運動控制器光線互動的任何物件, 我們建議您針對這三種輸入狀態有不同的視覺提示:</span><span class="sxs-lookup"><span data-stu-id="eeea3-121">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend to have different visual cue for these three input states:</span></span>
* <span data-ttu-id="eeea3-122">**預設值 (觀察)** :物件的預設閒置狀態。</span><span class="sxs-lookup"><span data-stu-id="eeea3-122">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="eeea3-123">**目標 (滑鼠停留)** :當物件以注視游標、手指鄰近或移動控制器的指標為目標時。</span><span class="sxs-lookup"><span data-stu-id="eeea3-123">**Targeted (Hover)**: When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
* <span data-ttu-id="eeea3-124">已**按下**:當按下滑鼠按鍵時, 請按下或移動控制器的 [選取] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="eeea3-124">**Pressed**: When the object is pressed with air-tap gesture, finger press or motion controller's select button.</span></span>

<span data-ttu-id="eeea3-125">您可以使用反白顯示或調整之類的技術, 為使用者的輸入狀態提供視覺提示。</span><span class="sxs-lookup"><span data-stu-id="eeea3-125">You can use techniques such as highlighting or scaling to provide visual cue to the user’s input states.</span></span> <span data-ttu-id="eeea3-126">在 Windows Mixed Reality 中, 您可以找到在 [開始] 功能表和 [應用程式行] 按鈕上將不同輸入狀態視覺化的範例。</span><span class="sxs-lookup"><span data-stu-id="eeea3-126">In Windows Mixed Reality, you can find the examples of visualizing different input states on Start menu and App Bar buttons.</span></span> 

<span data-ttu-id="eeea3-127">![視覺化觀察狀態、目標狀態和按下狀態的範例](images/640px-interactibleobject-states.png)</span><span class="sxs-lookup"><span data-stu-id="eeea3-127">![Example of visualizing observation state, targeted state, and pressed state](images/640px-interactibleobject-states.png)</span></span><br>
<span data-ttu-id="eeea3-128">*視覺化觀察狀態、目標狀態和按下狀態的範例*</span><span class="sxs-lookup"><span data-stu-id="eeea3-128">*Example of visualizing observation state, targeted state, and pressed state*</span></span>

<span data-ttu-id="eeea3-129">![全像攝影按鈕上的觀察狀態、目標狀態和按下狀態](images/MRTK_InteractableState.png)</span><span class="sxs-lookup"><span data-stu-id="eeea3-129">![Observation state, targeted state, and pressed state on holographic button](images/MRTK_InteractableState.png)</span></span><br>
<span data-ttu-id="eeea3-130">*全像攝影按鈕上的觀察狀態、目標狀態和按下狀態*</span><span class="sxs-lookup"><span data-stu-id="eeea3-130">*Observation state, targeted state, and pressed state on holographic button*</span></span>

#### <a name="neardirect-interactions"></a><span data-ttu-id="eeea3-131">接近 (直接) 互動</span><span class="sxs-lookup"><span data-stu-id="eeea3-131">Near(direct) interactions</span></span>

<span data-ttu-id="eeea3-132">HoloLens 2 支援明確的手寫追蹤輸入, 可讓您與物件互動。</span><span class="sxs-lookup"><span data-stu-id="eeea3-132">HoloLens 2 supports articulated hand tracking input which allows you to interact with objects.</span></span> <span data-ttu-id="eeea3-133">如果沒有 haptic 的意見反應和完美的深度認知, 有時可能很難分辨出手距物件的距離, 或您是否觸及。</span><span class="sxs-lookup"><span data-stu-id="eeea3-133">Without haptic feedback and perfect depth perception sometimes it can be hard to tell how far away your hand is from an object, or whether you are touching.</span></span> <span data-ttu-id="eeea3-134">請務必提供足夠的視覺提示來傳達物件的狀態, 特別是與全息影像相關。</span><span class="sxs-lookup"><span data-stu-id="eeea3-134">It is important to provide enough visual cues to communicate the state of the object and in particular of your hands in relation to holograms.</span></span>

<span data-ttu-id="eeea3-135">使用視覺效果意見反應來傳達下列內容:</span><span class="sxs-lookup"><span data-stu-id="eeea3-135">Use visual feedback to communicate the following:</span></span>
* <span data-ttu-id="eeea3-136">**預設值 (觀察)** :物件的預設閒置狀態。</span><span class="sxs-lookup"><span data-stu-id="eeea3-136">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="eeea3-137">**滑鼠停留**:當手近于全息全像投影時, 請變更視覺效果來溝通該手的目標為全像投影。</span><span class="sxs-lookup"><span data-stu-id="eeea3-137">**Hover**: When hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="eeea3-138">**距離和互動點**: 身為手中的全像投影, 設計意見反應來傳達預定的互動點, 以及從物件到手指的距離</span><span class="sxs-lookup"><span data-stu-id="eeea3-138">**Distance and point of interaction**: As hand approaches hologram, design feedback to communicate the projected point of interaction, as well as how far from the object the finger is</span></span>
* <span data-ttu-id="eeea3-139">**連絡人開始**:變更視覺效果 (淺色、色彩) 以溝通觸控已發生</span><span class="sxs-lookup"><span data-stu-id="eeea3-139">**Contact Begin**: Change visuals (light, color) to communicate that touch has occured</span></span>
* <span data-ttu-id="eeea3-140">**Grasped**:在 grasped 物件時變更視覺效果 (淺色、色彩)。</span><span class="sxs-lookup"><span data-stu-id="eeea3-140">**Grasped**: Change visuals (light, color) when the object is grasped.</span></span>
* <span data-ttu-id="eeea3-141">**連絡人端**:觸控結束時變更視覺效果 (淺色、色彩)。</span><span class="sxs-lookup"><span data-stu-id="eeea3-141">**Contact End**: Change visuals (light, color) when touch has ended.</span></span>

<span data-ttu-id="eeea3-142">![近乎互動狀態的視覺化範例](images/640px-interactibleobject-states-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="eeea3-142">![Example of visualizing near interaction states](images/640px-interactibleobject-states-near.jpg)</span></span><br>
<span data-ttu-id="eeea3-143">*近乎互動狀態的視覺化範例*</span><span class="sxs-lookup"><span data-stu-id="eeea3-143">*Example of visualizing near interaction states*</span></span>

<span data-ttu-id="eeea3-144">[HoloLens 2 中的按鈕](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)顯示將不同輸入互動狀態視覺化的範例。</span><span class="sxs-lookup"><span data-stu-id="eeea3-144">The [Button in HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) shows the example of visualizing different input interaction states.</span></span>

<span data-ttu-id="eeea3-145">![HoloLens 2 中的 [pressable] 按鈕範例](images/640px-interactibleobject-pressablebutton-650px2.jpg)</span><span class="sxs-lookup"><span data-stu-id="eeea3-145">![Example of pressable button in HoloLens 2](images/640px-interactibleobject-pressablebutton-650px2.jpg)</span></span><br>
<span data-ttu-id="eeea3-146">*HoloLens 2 中的 [pressable] 按鈕範例*</span><span class="sxs-lookup"><span data-stu-id="eeea3-146">*Example of pressable button in HoloLens 2*</span></span>

<span data-ttu-id="eeea3-147">在 HoloLens 2 中, 有一個額外的視覺提示, 可改善使用者對深度認知的信心。</span><span class="sxs-lookup"><span data-stu-id="eeea3-147">In HoloLens 2, there is an additional visual cue which improves the user's confidence on the depth perception.</span></span> <span data-ttu-id="eeea3-148">當 fingertip 接近物件時, fingertip 上的環形會顯示並相應減少。</span><span class="sxs-lookup"><span data-stu-id="eeea3-148">The ring on the fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="eeea3-149">環形最後會在按下狀態時聚合到一個點。</span><span class="sxs-lookup"><span data-stu-id="eeea3-149">The ring eventually converges into a dot on press state.</span></span> <span data-ttu-id="eeea3-150">此視覺 affordance 可協助使用者瞭解物件的距離。</span><span class="sxs-lookup"><span data-stu-id="eeea3-150">This visual affordance helps the user understand the distance from the object.</span></span>

<span data-ttu-id="eeea3-151">![Fingertip 環形視覺效果](images/640px-interactibleobject-pressablebutton-650px3.jpg)</span><span class="sxs-lookup"><span data-stu-id="eeea3-151">![Fingertip ring visualization](images/640px-interactibleobject-pressablebutton-650px3.jpg)</span></span><br>
<span data-ttu-id="eeea3-152">*HoloLens 2 中的 Fingertip 環形視覺效果*</span><span class="sxs-lookup"><span data-stu-id="eeea3-152">*Fingertip ring visualization in HoloLens 2*</span></span>

<span data-ttu-id="eeea3-153">![視覺效果意見反應關於手近](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="eeea3-153">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
<span data-ttu-id="eeea3-154">*以鄰近範圍方塊為基礎的視覺效果意見反應範例*</span><span class="sxs-lookup"><span data-stu-id="eeea3-154">*Example of visual feedback based on the proximity - Bounding box*</span></span>


### <a name="audio-cue"></a><span data-ttu-id="eeea3-155">音訊提示</span><span class="sxs-lookup"><span data-stu-id="eeea3-155">Audio cue</span></span>
<span data-ttu-id="eeea3-156">對於直接的互動, 適當的音訊意見反應可以大幅改善使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="eeea3-156">For the direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="eeea3-157">使用音訊意見反應來傳達下列內容:</span><span class="sxs-lookup"><span data-stu-id="eeea3-157">Use audio feedback to communicate the following:</span></span>
* <span data-ttu-id="eeea3-158">**連絡人開始**:開始觸控時播放音效</span><span class="sxs-lookup"><span data-stu-id="eeea3-158">**Contact begin**: Play sound when touch begins</span></span>
* <span data-ttu-id="eeea3-159">**連絡人端**:在 touch 端播放音效</span><span class="sxs-lookup"><span data-stu-id="eeea3-159">**Contact end**: Play sound on touch end</span></span>
* <span data-ttu-id="eeea3-160">**抓取開始**:抓取開始時播放音效</span><span class="sxs-lookup"><span data-stu-id="eeea3-160">**Grab begin**: Play sound when grab starts</span></span>
* <span data-ttu-id="eeea3-161">**抓取結束**:在抓取結束時播放音效</span><span class="sxs-lookup"><span data-stu-id="eeea3-161">**Grab end**: Play sound on grab end</span></span>

### <a name="voice-command"></a><span data-ttu-id="eeea3-162">語音命令</span><span class="sxs-lookup"><span data-stu-id="eeea3-162">Voice command</span></span>
<span data-ttu-id="eeea3-163">針對任何可互動物件, 請務必支援替代互動選項。</span><span class="sxs-lookup"><span data-stu-id="eeea3-163">For any interactable objects, it is important to support alternative interaction options.</span></span> <span data-ttu-id="eeea3-164">在預設情況下, 建議您針對任何可互動的物件支援語音命令。</span><span class="sxs-lookup"><span data-stu-id="eeea3-164">In default, it is recommended to support voice command for any objects that are interactable.</span></span> <span data-ttu-id="eeea3-165">若要改善可搜尋性, 您可以提供滑鼠停留狀態的工具提示。</span><span class="sxs-lookup"><span data-stu-id="eeea3-165">To improve the discoverability, you can provide tooltip on hover state.</span></span>

<img src="images/640px-interactibleobject-voicecommand.jpg" alt="Tooltip for the voice command" title="語音命令的工具提示" width="350"><br/><span data-ttu-id="eeea3-167">*語音命令的工具提示*</span><span class="sxs-lookup"><span data-stu-id="eeea3-167">*Tooltip for the voice command*</span></span>

## <a name="sizing"></a><span data-ttu-id="eeea3-168">調整大小</span><span class="sxs-lookup"><span data-stu-id="eeea3-168">Sizing</span></span>
<span data-ttu-id="eeea3-169">若要確保使用者可以輕鬆地觸及所有可互動物件, 建議您根據其與使用者的距離, 確定可互動符合最小大小 (視覺效果的角度, 通常以度為單位測量)。</span><span class="sxs-lookup"><span data-stu-id="eeea3-169">To ensure that all interactable objects can easily be touched by users, we recommend that you make sure the interactable meets a minimum size (the visual angle often measured in degrees of visual arc) based on the distance it is placed from the user.</span></span> <span data-ttu-id="eeea3-170">視覺角度是以使用者眼和物件之間的距離為依據, 並維持不變, 而目標的實體大小可能會隨著使用者變更的距離而改變。</span><span class="sxs-lookup"><span data-stu-id="eeea3-170">Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="eeea3-171">若要根據與使用者的距離來判斷物件的必要實體大小, 請嘗試使用視覺角度計算機, 例如[這一項](http://elvers.us/perception/visualAngle/)。</span><span class="sxs-lookup"><span data-stu-id="eeea3-171">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](http://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="eeea3-172">以下是最小可互動內容大小的建議。</span><span class="sxs-lookup"><span data-stu-id="eeea3-172">Below are the recommendations for minimum sizes of interactable content.</span></span>

### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="eeea3-173">直接操作的目標大小</span><span class="sxs-lookup"><span data-stu-id="eeea3-173">Target size for direct hand interaction</span></span>
| <span data-ttu-id="eeea3-174">長途電話</span><span class="sxs-lookup"><span data-stu-id="eeea3-174">Distance</span></span> | <span data-ttu-id="eeea3-175">視角</span><span class="sxs-lookup"><span data-stu-id="eeea3-175">Viewing angle</span></span> | <span data-ttu-id="eeea3-176">Size</span><span class="sxs-lookup"><span data-stu-id="eeea3-176">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="eeea3-177">45cm</span><span class="sxs-lookup"><span data-stu-id="eeea3-177">45cm</span></span>  | <span data-ttu-id="eeea3-178">不小於2°</span><span class="sxs-lookup"><span data-stu-id="eeea3-178">no smaller than 2°</span></span> | <span data-ttu-id="eeea3-179">1.6 x 1.6 cm</span><span class="sxs-lookup"><span data-stu-id="eeea3-179">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="eeea3-180">![直接操作的目標大小](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="eeea3-180">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="eeea3-181">*直接操作的目標大小*</span><span class="sxs-lookup"><span data-stu-id="eeea3-181">*Target size for direct hand interaction*</span></span>

<span data-ttu-id="eeea3-182">建立直接互動的按鈕時, 我們建議使用較大大小的最小值 3.2 x 3.2 cm, 以確保有足夠的空間可包含圖示, 而且可能會有一些文字 \* \*</span><span class="sxs-lookup"><span data-stu-id="eeea3-182">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there is enough space to contain an icon and potentially some text\*\*</span></span>

| <span data-ttu-id="eeea3-183">長途電話</span><span class="sxs-lookup"><span data-stu-id="eeea3-183">Distance</span></span> | <span data-ttu-id="eeea3-184">最小大小</span><span class="sxs-lookup"><span data-stu-id="eeea3-184">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="eeea3-185">45cm</span><span class="sxs-lookup"><span data-stu-id="eeea3-185">45cm</span></span>  | <span data-ttu-id="eeea3-186">3.2 x 3.2 cm</span><span class="sxs-lookup"><span data-stu-id="eeea3-186">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="eeea3-187">![按鈕的目標大小](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="eeea3-187">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="eeea3-188">*按鈕的目標大小*</span><span class="sxs-lookup"><span data-stu-id="eeea3-188">*Target size for the buttons*</span></span>


### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="eeea3-189">右手光線或注視互動的目標大小</span><span class="sxs-lookup"><span data-stu-id="eeea3-189">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="eeea3-190">長途電話</span><span class="sxs-lookup"><span data-stu-id="eeea3-190">Distance</span></span> | <span data-ttu-id="eeea3-191">視角</span><span class="sxs-lookup"><span data-stu-id="eeea3-191">Viewing angle</span></span> | <span data-ttu-id="eeea3-192">Size</span><span class="sxs-lookup"><span data-stu-id="eeea3-192">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="eeea3-193">2m</span><span class="sxs-lookup"><span data-stu-id="eeea3-193">2m</span></span>  | <span data-ttu-id="eeea3-194">不小於1°</span><span class="sxs-lookup"><span data-stu-id="eeea3-194">no smaller than 1°</span></span> | <span data-ttu-id="eeea3-195">3.5 x 3.5 cm</span><span class="sxs-lookup"><span data-stu-id="eeea3-195">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="eeea3-196">![右手光線或注視互動的目標大小](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="eeea3-196">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="eeea3-197">*右手光線或注視互動的目標大小*</span><span class="sxs-lookup"><span data-stu-id="eeea3-197">*Target size for hand ray or gaze interaction*</span></span>

## <a name="creating-interactable-object-with-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="eeea3-198">使用混合現實工具組 (MRTK) 建立可互動物件</span><span class="sxs-lookup"><span data-stu-id="eeea3-198">Creating interactable object with Mixed Reality Toolkit (MRTK)</span></span>

<span data-ttu-id="eeea3-199">在 **[混合式現實工具](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 組中, 您可以找到可協助您建立可互動物件的一系列 Unity 腳本和 prefabs。</span><span class="sxs-lookup"><span data-stu-id="eeea3-199">In the **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can find the series of Unity scripts and prefabs that will help you create interactable objects.</span></span> <span data-ttu-id="eeea3-200">您可以使用這些來讓物件回應各種類型的輸入互動狀態。</span><span class="sxs-lookup"><span data-stu-id="eeea3-200">You can use these to make objects respond to various types of input interaction states.</span></span>

* [<span data-ttu-id="eeea3-201">可互動</span><span class="sxs-lookup"><span data-stu-id="eeea3-201">Interactable</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [<span data-ttu-id="eeea3-202">Button</span><span class="sxs-lookup"><span data-stu-id="eeea3-202">Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="eeea3-203">手動互動範例場景</span><span class="sxs-lookup"><span data-stu-id="eeea3-203">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="eeea3-204">MixedRealityToolkit 的標準著色器提供各種選項, 例如**近光源**, 可協助您建立視覺效果和音訊提示。</span><span class="sxs-lookup"><span data-stu-id="eeea3-204">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* [<span data-ttu-id="eeea3-205">MRTK 標準著色器</span><span class="sxs-lookup"><span data-stu-id="eeea3-205">MRTK Standard Shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


## <a name="see-also"></a><span data-ttu-id="eeea3-206">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eeea3-206">See also</span></span>

* [<span data-ttu-id="eeea3-207">周框方塊</span><span class="sxs-lookup"><span data-stu-id="eeea3-207">Bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="eeea3-208">物件集合</span><span class="sxs-lookup"><span data-stu-id="eeea3-208">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="eeea3-209">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="eeea3-209">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)