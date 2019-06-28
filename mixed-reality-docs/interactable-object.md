---
title: 可互動的物件
description: 按鈕長久以來所用的觸發事件 2D 抽象全球隱喻。 在三維的混合的現實世界中，我們沒有不再侷限於這個抽象層再的世界。
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: 混合的實境、 控制項、 互動、 ui、 ux
ms.openlocfilehash: 57299cbb758a69603fc68ad5d43af8f2216e5104
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415357"
---
# <a name="interactable-object"></a><span data-ttu-id="ba331-105">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="ba331-105">Interactable object</span></span>

<span data-ttu-id="ba331-106">按鈕長久以來所用的觸發事件 2D 抽象全球隱喻。</span><span class="sxs-lookup"><span data-stu-id="ba331-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="ba331-107">在三維的混合的現實世界中，我們沒有不再侷限於這個抽象層再的世界。</span><span class="sxs-lookup"><span data-stu-id="ba331-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="ba331-108">任何能**互動的物件**觸發事件。</span><span class="sxs-lookup"><span data-stu-id="ba331-108">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="ba331-109">可互動的物件可以表示為任何項目從咖啡杯資料表在空中浮在球形文字說明。</span><span class="sxs-lookup"><span data-stu-id="ba331-109">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="ba331-110">我們仍執行能用在某些情況下這類對話方塊 UI 如同傳統的按鈕。</span><span class="sxs-lookup"><span data-stu-id="ba331-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="ba331-111">按鈕的視覺表示方式取決於內容。</span><span class="sxs-lookup"><span data-stu-id="ba331-111">The visual representation of the button depends on the context.</span></span>

![Interactible 物件](images/640px-interactibleobject-hero-640px.jpg)


## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="ba331-113">可互動的物件的重要屬性</span><span class="sxs-lookup"><span data-stu-id="ba331-113">Important properties of the interactable object</span></span>

### <a name="visual-cue"></a><span data-ttu-id="ba331-114">視覺提示</span><span class="sxs-lookup"><span data-stu-id="ba331-114">Visual cue</span></span>

<span data-ttu-id="ba331-115">視覺提示是眼睛光線的形式接收，且 visual 系統處理期間視覺的感應式提示。</span><span class="sxs-lookup"><span data-stu-id="ba331-115">Visual cues are sensory cues received by the eye in the form of light and processed by the visual system during visual perception.</span></span> <span data-ttu-id="ba331-116">由於 visual 系統是主控在許多物種，尤其是人類的視覺提示是大型中發現世界的如何資訊。</span><span class="sxs-lookup"><span data-stu-id="ba331-116">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="ba331-117">在混合實境，全像攝影版的物件會混合使用真實世界的環境，因為它可能會難以了解哪些物件是可互動。</span><span class="sxs-lookup"><span data-stu-id="ba331-117">In mixed reality, since the holographic objects are mixed with the real-world environment, it could be difficult to understand which objects are interactable.</span></span> <span data-ttu-id="ba331-118">在您的經驗中任何可互動的物件，請務必提供差異化的視覺提示，針對每個輸入的狀態。</span><span class="sxs-lookup"><span data-stu-id="ba331-118">For any interactable objects in your experience, it is important to provide differentiated visual cue for each input state.</span></span> <span data-ttu-id="ba331-119">這可協助使用者了解您的使用經驗的哪個部分是可互動，並使用一致的互動方法，讓使用者有信心。</span><span class="sxs-lookup"><span data-stu-id="ba331-119">This helps the user understand which part of your experience is interactable and makes the user confident with consistent interaction method.</span></span>

#### <a name="far-interactions"></a><span data-ttu-id="ba331-120">遠的互動</span><span class="sxs-lookup"><span data-stu-id="ba331-120">Far interactions</span></span>

<span data-ttu-id="ba331-121">任何物件該使用者可以互動視線、 手無限遠的光線，與動作控制器的光線，我們建議您有不同的視覺提示。 這三種輸入狀態：</span><span class="sxs-lookup"><span data-stu-id="ba331-121">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend to have different visual cue for these three input states:</span></span>
* <span data-ttu-id="ba331-122">**預設值 （觀察）** :預設的閒置狀態的物件。</span><span class="sxs-lookup"><span data-stu-id="ba331-122">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="ba331-123">**目標 （暫留）** :當物件的目標與視線指標時，手指鄰近性或動作控制器的指標。</span><span class="sxs-lookup"><span data-stu-id="ba331-123">**Targeted (Hover)**: When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
* <span data-ttu-id="ba331-124">**按下**:當物件已按下使用空中點選手勢、 手指按或動作控制器的 [選取] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ba331-124">**Pressed**: When the object is pressed with air-tap gesture, finger press or motion controller's select button.</span></span>

<span data-ttu-id="ba331-125">您可以使用的技術，例如反白顯示或縮放比例來提供視覺提示使用者輸入的狀態。</span><span class="sxs-lookup"><span data-stu-id="ba331-125">You can use techniques such as highlighting or scaling to provide visual cue to the user’s input states.</span></span> <span data-ttu-id="ba331-126">在 Windows Mixed Reality，您可以找到視覺化不同輸入的狀態，在 [開始] 功能表和應用程式列按鈕的範例。</span><span class="sxs-lookup"><span data-stu-id="ba331-126">In Windows Mixed Reality, you can find the examples of visualizing different input states on Start menu and App Bar buttons.</span></span> 

<span data-ttu-id="ba331-127">![目標狀態，與按下狀態的視覺化觀察狀態範例](images/640px-interactibleobject-states.png)</span><span class="sxs-lookup"><span data-stu-id="ba331-127">![Example of visualizing observation state, targeted state, and pressed state](images/640px-interactibleobject-states.png)</span></span><br>
<span data-ttu-id="ba331-128">*目標狀態，與按下狀態的視覺化觀察狀態範例*</span><span class="sxs-lookup"><span data-stu-id="ba331-128">*Example of visualizing observation state, targeted state, and pressed state*</span></span>

<span data-ttu-id="ba331-129">![觀察狀態設為目標的狀態，並在全像攝影版的按鈕上按下狀態](images/MRTK_InteractableState.png)</span><span class="sxs-lookup"><span data-stu-id="ba331-129">![Observation state, targeted state, and pressed state on holographic button](images/MRTK_InteractableState.png)</span></span><br>
<span data-ttu-id="ba331-130">*觀察狀態設為目標的狀態，並在全像攝影版的按鈕上按下狀態*</span><span class="sxs-lookup"><span data-stu-id="ba331-130">*Observation state, targeted state, and pressed state on holographic button*</span></span>

#### <a name="neardirect-interactions"></a><span data-ttu-id="ba331-131">Near(direct) 互動</span><span class="sxs-lookup"><span data-stu-id="ba331-131">Near(direct) interactions</span></span>

<span data-ttu-id="ba331-132">HoloLens 2 支援相互連貫的手動追蹤可讓您與物件互動的輸入。</span><span class="sxs-lookup"><span data-stu-id="ba331-132">HoloLens 2 supports articulated hand tracking input which allows you to interact with objects.</span></span> <span data-ttu-id="ba331-133">不含 haptic 意見反應和 perception 完美的深度，有時很難判斷您的手距離是從物件，或您是否會觸碰。</span><span class="sxs-lookup"><span data-stu-id="ba331-133">Without haptic feedback and perfect depth perception sometimes it can be hard to tell how far away your hand is from an object, or whether you are touching.</span></span> <span data-ttu-id="ba331-134">請務必提供足夠的視覺提示來溝通狀態的物件，特別在全像投影的關聯性中實際操作。</span><span class="sxs-lookup"><span data-stu-id="ba331-134">It is important to provide enough visual cues to communicate the state of the object and in particular of your hands in relation to holograms.</span></span>

<span data-ttu-id="ba331-135">您可以使用視覺化回饋，通訊下列：</span><span class="sxs-lookup"><span data-stu-id="ba331-135">Use visual feedback to communicate the following:</span></span>
* <span data-ttu-id="ba331-136">**預設值 （觀察）** :預設的閒置狀態的物件。</span><span class="sxs-lookup"><span data-stu-id="ba331-136">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="ba331-137">**將滑鼠移至**:手狀即將全像 」，這是進行通訊，手動變更視覺效果的目標全像圖。</span><span class="sxs-lookup"><span data-stu-id="ba331-137">**Hover**: When hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="ba331-138">**距離和的互動點**: 手狀接近全像圖時，設計通訊預計的互動點，以及如何遠離物件是指的意見反應</span><span class="sxs-lookup"><span data-stu-id="ba331-138">**Distance and point of interaction**: As hand approaches hologram, design feedback to communicate the projected point of interaction, as well as how far from the object the finger is</span></span>
* <span data-ttu-id="ba331-139">**請連絡 Begin**:變更視覺效果 （光線，色彩） 進行通訊的觸控發生</span><span class="sxs-lookup"><span data-stu-id="ba331-139">**Contact Begin**: Change visuals (light, color) to communicate that touch has occured</span></span>
* <span data-ttu-id="ba331-140">**Grasped**:變更視覺效果 （光線，色彩） grasped 物件的時機。</span><span class="sxs-lookup"><span data-stu-id="ba331-140">**Grasped**: Change visuals (light, color) when the object is grasped.</span></span>
* <span data-ttu-id="ba331-141">**請連絡結束**:變更視覺效果 （光線，色彩） 觸控時結束。</span><span class="sxs-lookup"><span data-stu-id="ba331-141">**Contact End**: Change visuals (light, color) when touch has ended.</span></span>

<span data-ttu-id="ba331-142">![視覺化附近互動狀態範例](images/640px-interactibleobject-states-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="ba331-142">![Example of visualizing near interaction states](images/640px-interactibleobject-states-near.jpg)</span></span><br>
<span data-ttu-id="ba331-143">*視覺化附近互動狀態範例*</span><span class="sxs-lookup"><span data-stu-id="ba331-143">*Example of visualizing near interaction states*</span></span>

<span data-ttu-id="ba331-144">[HoloLens 2 中的按鈕](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)示範視覺化不同輸入的互動狀態。</span><span class="sxs-lookup"><span data-stu-id="ba331-144">The [Button in HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) shows the example of visualizing different input interaction states.</span></span>

<span data-ttu-id="ba331-145">![HoloLens 2 pressable 按鈕的範例](images/640px-interactibleobject-pressablebutton-650px2.jpg)</span><span class="sxs-lookup"><span data-stu-id="ba331-145">![Example of pressable button in HoloLens 2](images/640px-interactibleobject-pressablebutton-650px2.jpg)</span></span><br>
<span data-ttu-id="ba331-146">*HoloLens 2 pressable 按鈕的範例*</span><span class="sxs-lookup"><span data-stu-id="ba331-146">*Example of pressable button in HoloLens 2*</span></span>

<span data-ttu-id="ba331-147">HoloLens 2 中沒有可改善使用者的信心，深度認知上其他視覺提示。</span><span class="sxs-lookup"><span data-stu-id="ba331-147">In HoloLens 2, there is an additional visual cue which improves the user's confidence on the depth perception.</span></span> <span data-ttu-id="ba331-148">上寫寫看信號出現，並相應減少，因為寫寫看即將來臨的物件。</span><span class="sxs-lookup"><span data-stu-id="ba331-148">The ring on the fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="ba331-149">按下狀態的一個點到最後聚合信號。</span><span class="sxs-lookup"><span data-stu-id="ba331-149">The ring eventually converges into a dot on press state.</span></span> <span data-ttu-id="ba331-150">此視覺化功能可見性可協助使用者了解物件之間的距離。</span><span class="sxs-lookup"><span data-stu-id="ba331-150">This visual affordance helps the user understand the distance from the object.</span></span>

<span data-ttu-id="ba331-151">![寫寫看環狀視覺效果](images/640px-interactibleobject-pressablebutton-650px3.jpg)</span><span class="sxs-lookup"><span data-stu-id="ba331-151">![Fingertip ring visualization](images/640px-interactibleobject-pressablebutton-650px3.jpg)</span></span><br>
<span data-ttu-id="ba331-152">*HoloLens 2 寫寫看環狀視覺效果*</span><span class="sxs-lookup"><span data-stu-id="ba331-152">*Fingertip ring visualization in HoloLens 2*</span></span>

<span data-ttu-id="ba331-153">![在手相近的視覺化回饋](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="ba331-153">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
<span data-ttu-id="ba331-154">*根據鄰近-週框方塊的視覺化回饋的範例*</span><span class="sxs-lookup"><span data-stu-id="ba331-154">*Example of visual feedback based on the proximity - Bounding box*</span></span>


### <a name="audio-cue"></a><span data-ttu-id="ba331-155">音訊提示</span><span class="sxs-lookup"><span data-stu-id="ba331-155">Audio cue</span></span>
<span data-ttu-id="ba331-156">直接手動互動，適當的音訊意見反應可以大幅改善使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="ba331-156">For the direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="ba331-157">使用來傳達下列音訊意見反應：</span><span class="sxs-lookup"><span data-stu-id="ba331-157">Use audio feedback to communicate the following:</span></span>
* <span data-ttu-id="ba331-158">**請連絡開始**:觸控式開始時播放音效</span><span class="sxs-lookup"><span data-stu-id="ba331-158">**Contact begin**: Play sound when touch begins</span></span>
* <span data-ttu-id="ba331-159">**連絡人的結束**:播放音效觸控端</span><span class="sxs-lookup"><span data-stu-id="ba331-159">**Contact end**: Play sound on touch end</span></span>
* <span data-ttu-id="ba331-160">**抓取開始**:擷取啟動時播放音效</span><span class="sxs-lookup"><span data-stu-id="ba331-160">**Grab begin**: Play sound when grab starts</span></span>
* <span data-ttu-id="ba331-161">**抓取結束**:播放音效抓取端</span><span class="sxs-lookup"><span data-stu-id="ba331-161">**Grab end**: Play sound on grab end</span></span>

### <a name="voice-command"></a><span data-ttu-id="ba331-162">語音命令</span><span class="sxs-lookup"><span data-stu-id="ba331-162">Voice command</span></span>
<span data-ttu-id="ba331-163">任何可互動的物件，請務必支援替代的互動選項。</span><span class="sxs-lookup"><span data-stu-id="ba331-163">For any interactable objects, it is important to support alternative interaction options.</span></span> <span data-ttu-id="ba331-164">在預設情況下，建議您使用支援語音命令是可互動的任何物件。</span><span class="sxs-lookup"><span data-stu-id="ba331-164">In default, it is recommended to support voice command for any objects that are interactable.</span></span> <span data-ttu-id="ba331-165">若要改善探索能力，您可以提供工具提示上暫留狀態。</span><span class="sxs-lookup"><span data-stu-id="ba331-165">To improve the discoverability, you can provide tooltip on hover state.</span></span>

<img src="images/640px-interactibleobject-voicecommand.jpg" alt="Tooltip for the voice command" title="語音命令的工具提示" width="350"><br/><span data-ttu-id="ba331-167">*語音命令的工具提示*</span><span class="sxs-lookup"><span data-stu-id="ba331-167">*Tooltip for the voice command*</span></span>

## <a name="sizing"></a><span data-ttu-id="ba331-168">調整大小</span><span class="sxs-lookup"><span data-stu-id="ba331-168">Sizing</span></span>
<span data-ttu-id="ba331-169">為了確保可互動的所有物件都可以輕鬆地接觸都到的使用者，我們建議您確定可互動的符合大小下限 （通常長達 visual 弧線的程度視覺化角度） 根據它會放置在使用者的距離。</span><span class="sxs-lookup"><span data-stu-id="ba331-169">To ensure that all interactable objects can easily be touched by users, we recommend that you make sure the interactable meets a minimum size (the visual angle often measured in degrees of visual arc) based on the distance it is placed from the user.</span></span> <span data-ttu-id="ba331-170">視覺化的角度根據使用者的眼睛與物件之間的距離，並會保持不變，而目標的實體大小從使用者的變更，可能會變更為之間的距離。</span><span class="sxs-lookup"><span data-stu-id="ba331-170">Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="ba331-171">若要判斷使用者之間的距離為基礎的物件所需的實體大小，請嘗試使用 visual 的角度計算機這類[這個](http://elvers.us/perception/visualAngle/)。</span><span class="sxs-lookup"><span data-stu-id="ba331-171">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](http://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="ba331-172">以下是可互動內容的最小大小的建議。</span><span class="sxs-lookup"><span data-stu-id="ba331-172">Below are the recommendations for minimum sizes of interactable content.</span></span>

### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="ba331-173">直接手動互動的目標大小</span><span class="sxs-lookup"><span data-stu-id="ba331-173">Target size for direct hand interaction</span></span>
| <span data-ttu-id="ba331-174">距離</span><span class="sxs-lookup"><span data-stu-id="ba331-174">Distance</span></span> | <span data-ttu-id="ba331-175">檢視角度</span><span class="sxs-lookup"><span data-stu-id="ba331-175">Viewing angle</span></span> | <span data-ttu-id="ba331-176">Size</span><span class="sxs-lookup"><span data-stu-id="ba331-176">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="ba331-177">45 cm</span><span class="sxs-lookup"><span data-stu-id="ba331-177">45cm</span></span>  | <span data-ttu-id="ba331-178">不小於 2 °</span><span class="sxs-lookup"><span data-stu-id="ba331-178">no smaller than 2°</span></span> | <span data-ttu-id="ba331-179">1.6 x 1.6 cm</span><span class="sxs-lookup"><span data-stu-id="ba331-179">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="ba331-180">![直接手動互動的目標大小](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="ba331-180">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="ba331-181">*直接手動互動的目標大小*</span><span class="sxs-lookup"><span data-stu-id="ba331-181">*Target size for direct hand interaction*</span></span>

<span data-ttu-id="ba331-182">在建立時直接互動的按鈕，我們建議您較大大小下限為 3.2 x 3.2 cm，以確保有足夠空間來容納圖示和潛在某些文字 \* \*</span><span class="sxs-lookup"><span data-stu-id="ba331-182">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there is enough space to contain an icon and potentially some text\*\*</span></span>

| <span data-ttu-id="ba331-183">距離</span><span class="sxs-lookup"><span data-stu-id="ba331-183">Distance</span></span> | <span data-ttu-id="ba331-184">最小大小</span><span class="sxs-lookup"><span data-stu-id="ba331-184">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="ba331-185">45 cm</span><span class="sxs-lookup"><span data-stu-id="ba331-185">45cm</span></span>  | <span data-ttu-id="ba331-186">3.2 x 3.2 cm</span><span class="sxs-lookup"><span data-stu-id="ba331-186">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="ba331-187">![按鈕的目標大小](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="ba331-187">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="ba331-188">*按鈕的目標大小*</span><span class="sxs-lookup"><span data-stu-id="ba331-188">*Target size for the buttons*</span></span>


### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="ba331-189">目標手光線的大小或視線互動</span><span class="sxs-lookup"><span data-stu-id="ba331-189">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="ba331-190">距離</span><span class="sxs-lookup"><span data-stu-id="ba331-190">Distance</span></span> | <span data-ttu-id="ba331-191">檢視角度</span><span class="sxs-lookup"><span data-stu-id="ba331-191">Viewing angle</span></span> | <span data-ttu-id="ba331-192">Size</span><span class="sxs-lookup"><span data-stu-id="ba331-192">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="ba331-193">2m</span><span class="sxs-lookup"><span data-stu-id="ba331-193">2m</span></span>  | <span data-ttu-id="ba331-194">不小於 1 °</span><span class="sxs-lookup"><span data-stu-id="ba331-194">no smaller than 1°</span></span> | <span data-ttu-id="ba331-195">3.5 x 3.5 cm</span><span class="sxs-lookup"><span data-stu-id="ba331-195">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="ba331-196">![目標手光線的大小或視線互動](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="ba331-196">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="ba331-197">*目標手光線的大小或視線互動*</span><span class="sxs-lookup"><span data-stu-id="ba331-197">*Target size for hand ray or gaze interaction*</span></span>

## <a name="creating-interactable-object-with-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="ba331-198">建立可互動的物件與混合實境工具組 (MRTK)</span><span class="sxs-lookup"><span data-stu-id="ba331-198">Creating interactable object with Mixed Reality Toolkit (MRTK)</span></span>

<span data-ttu-id="ba331-199">在  **[混合實境 Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)** ，您可以找到 Unity 指令碼的一系列 prefabs，可協助您建立可互動的物件。</span><span class="sxs-lookup"><span data-stu-id="ba331-199">In the **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can find the series of Unity scripts and prefabs that will help you create interactable objects.</span></span> <span data-ttu-id="ba331-200">您可以使用這些物件的各種類型的輸入的互動狀態回應。</span><span class="sxs-lookup"><span data-stu-id="ba331-200">You can use these to make objects respond to various types of input interaction states.</span></span>

* [<span data-ttu-id="ba331-201">Interactable</span><span class="sxs-lookup"><span data-stu-id="ba331-201">Interactable</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [<span data-ttu-id="ba331-202">Button</span><span class="sxs-lookup"><span data-stu-id="ba331-202">Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="ba331-203">手動互動範例場景</span><span class="sxs-lookup"><span data-stu-id="ba331-203">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="ba331-204">提供各種選項，例如 MixedRealityToolkit 的標準著色器**鄰近 light**可協助您建立視覺與音訊提示。</span><span class="sxs-lookup"><span data-stu-id="ba331-204">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* [<span data-ttu-id="ba331-205">MRTK 標準著色器</span><span class="sxs-lookup"><span data-stu-id="ba331-205">MRTK Standard Shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


## <a name="see-also"></a><span data-ttu-id="ba331-206">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba331-206">See also</span></span>

* [<span data-ttu-id="ba331-207">週框方塊</span><span class="sxs-lookup"><span data-stu-id="ba331-207">Bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="ba331-208">物件集合</span><span class="sxs-lookup"><span data-stu-id="ba331-208">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="ba331-209">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="ba331-209">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)