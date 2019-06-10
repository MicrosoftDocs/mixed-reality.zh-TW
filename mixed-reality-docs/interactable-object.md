---
title: 可互動的物件
description: 按鈕長久以來所用的觸發事件 2D 抽象全球隱喻。 在三維的混合的現實世界中，我們沒有不再侷限於這個抽象層再的世界。
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 混合的實境、 控制項、 互動、 ui、 ux
ms.openlocfilehash: eea7eff6c591a9319b920936ce2be511cecb7496
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813762"
---
# <a name="interactable-object"></a><span data-ttu-id="01fd2-105">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="01fd2-105">Interactable object</span></span>

<span data-ttu-id="01fd2-106">按鈕長久以來所用的觸發事件 2D 抽象全球隱喻。</span><span class="sxs-lookup"><span data-stu-id="01fd2-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="01fd2-107">在三維的混合的現實世界中，我們沒有不再侷限於這個抽象層再的世界。</span><span class="sxs-lookup"><span data-stu-id="01fd2-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="01fd2-108">任何能**互動的物件**觸發事件。</span><span class="sxs-lookup"><span data-stu-id="01fd2-108">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="01fd2-109">可互動的物件可以表示為任何項目從咖啡杯資料表在空中浮在球形文字說明。</span><span class="sxs-lookup"><span data-stu-id="01fd2-109">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="01fd2-110">我們仍執行能用在某些情況下這類對話方塊 UI 如同傳統的按鈕。</span><span class="sxs-lookup"><span data-stu-id="01fd2-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="01fd2-111">按鈕的視覺表示方式取決於內容。</span><span class="sxs-lookup"><span data-stu-id="01fd2-111">The visual representation of the button depends on the context.</span></span>

![Interactible 物件](images/640px-interactibleobject-hero-640px.jpg)


## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="01fd2-113">可互動的物件的重要屬性</span><span class="sxs-lookup"><span data-stu-id="01fd2-113">Important properties of the interactable object</span></span>

### <a name="visual-cue"></a><span data-ttu-id="01fd2-114">視覺提示</span><span class="sxs-lookup"><span data-stu-id="01fd2-114">Visual cue</span></span>

<span data-ttu-id="01fd2-115">視覺提示是眼睛光線的形式接收，且 visual 系統處理期間視覺的感應式提示。</span><span class="sxs-lookup"><span data-stu-id="01fd2-115">Visual cues are sensory cues received by the eye in the form of light and processed by the visual system during visual perception.</span></span> <span data-ttu-id="01fd2-116">由於 visual 系統是主控在許多物種，尤其是人類的視覺提示是大型中發現世界的如何資訊。</span><span class="sxs-lookup"><span data-stu-id="01fd2-116">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="01fd2-117">在混合實境，全像攝影版的物件會混合使用真實世界的環境，因為它可能會難以了解哪些物件是可互動。</span><span class="sxs-lookup"><span data-stu-id="01fd2-117">In mixed reality, since the holographic objects are mixed with the real-world environment, it could be difficult to understand which objects are interactable.</span></span> <span data-ttu-id="01fd2-118">在您的經驗中任何可互動的物件，請務必提供差異化的視覺提示，針對每個輸入的狀態。</span><span class="sxs-lookup"><span data-stu-id="01fd2-118">For any interactable objects in your experience, it is important to provide differentiated visual cue for each input state.</span></span> <span data-ttu-id="01fd2-119">這可協助使用者了解您的使用經驗的哪個部分是可互動，並使用一致的互動方法，讓使用者有信心。</span><span class="sxs-lookup"><span data-stu-id="01fd2-119">This helps the user understand which part of your experience is interactable and makes the user confident with consistent interaction method.</span></span>

#### <a name="far-interactions"></a><span data-ttu-id="01fd2-120">遠的互動</span><span class="sxs-lookup"><span data-stu-id="01fd2-120">Far interactions</span></span>

<span data-ttu-id="01fd2-121">任何物件該使用者可以互動視線、 手無限遠的光線，與動作控制器的光線，我們建議您有不同的視覺提示。 這三種輸入狀態：</span><span class="sxs-lookup"><span data-stu-id="01fd2-121">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend to have different visual cue for these three input states:</span></span>
* <span data-ttu-id="01fd2-122">**預設值 （觀察）** :預設的閒置狀態的物件。</span><span class="sxs-lookup"><span data-stu-id="01fd2-122">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="01fd2-123">**目標 （暫留）** :當物件的目標與視線指標時，手指鄰近性或動作控制器的指標。</span><span class="sxs-lookup"><span data-stu-id="01fd2-123">**Targeted (Hover)**: When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
* <span data-ttu-id="01fd2-124">**按下**:當物件已按下使用空中點選手勢、 手指按或動作控制器的 [選取] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="01fd2-124">**Pressed**: When the object is pressed with air-tap gesture, finger press or motion controller's select button.</span></span>

<span data-ttu-id="01fd2-125">您可以使用的技術，例如反白顯示或縮放比例來提供視覺提示使用者輸入的狀態。</span><span class="sxs-lookup"><span data-stu-id="01fd2-125">You can use techniques such as highlighting or scaling to provide visual cue to the user’s input states.</span></span> <span data-ttu-id="01fd2-126">在 Windows Mixed Reality，您可以找到視覺化不同輸入的狀態，在 [開始] 功能表和應用程式列按鈕的範例。</span><span class="sxs-lookup"><span data-stu-id="01fd2-126">In Windows Mixed Reality, you can find the examples of visualizing different input states on Start menu and App Bar buttons.</span></span> 

<span data-ttu-id="01fd2-127">![目標狀態，與按下狀態的視覺化觀察狀態範例](images/640px-interactibleobject-states.png)</span><span class="sxs-lookup"><span data-stu-id="01fd2-127">![Example of visualizing observation state, targeted state, and pressed state](images/640px-interactibleobject-states.png)</span></span><br>
<span data-ttu-id="01fd2-128">*目標狀態，與按下狀態的視覺化觀察狀態範例*</span><span class="sxs-lookup"><span data-stu-id="01fd2-128">*Example of visualizing observation state, targeted state, and pressed state*</span></span>

<span data-ttu-id="01fd2-129">![觀察狀態設為目標的狀態，並在全像攝影版的按鈕上按下狀態](images/MRTK_InteractableState.png)</span><span class="sxs-lookup"><span data-stu-id="01fd2-129">![Observation state, targeted state, and pressed state on holographic button](images/MRTK_InteractableState.png)</span></span><br>
<span data-ttu-id="01fd2-130">*觀察狀態設為目標的狀態，並在全像攝影版的按鈕上按下狀態*</span><span class="sxs-lookup"><span data-stu-id="01fd2-130">*Observation state, targeted state, and pressed state on holographic button*</span></span>

#### <a name="neardirect-interactions"></a><span data-ttu-id="01fd2-131">Near(direct) 互動</span><span class="sxs-lookup"><span data-stu-id="01fd2-131">Near(direct) interactions</span></span>

<span data-ttu-id="01fd2-132">HoloLens 2 支援相互連貫的手動追蹤可讓您與物件互動的輸入。</span><span class="sxs-lookup"><span data-stu-id="01fd2-132">HoloLens 2 supports articulated hand tracking input which allows you to interact with objects.</span></span> <span data-ttu-id="01fd2-133">不含 haptic 意見反應和 perception 完美的深度，有時很難判斷您的手距離是從物件，或您是否會觸碰。</span><span class="sxs-lookup"><span data-stu-id="01fd2-133">Without haptic feedback and perfect depth perception sometimes it can be hard to tell how far away your hand is from an object, or whether you are touching.</span></span> <span data-ttu-id="01fd2-134">請務必提供足夠的視覺提示來溝通狀態的物件，特別在全像投影的關聯性中實際操作。</span><span class="sxs-lookup"><span data-stu-id="01fd2-134">It is important to provide enough visual cues to communicate the state of the object and in particular of your hands in relation to holograms.</span></span>

<span data-ttu-id="01fd2-135">您可以使用視覺化回饋，通訊下列：</span><span class="sxs-lookup"><span data-stu-id="01fd2-135">Use visual feedback to communicate the following:</span></span>
* <span data-ttu-id="01fd2-136">**預設值 （觀察）** :預設的閒置狀態的物件。</span><span class="sxs-lookup"><span data-stu-id="01fd2-136">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="01fd2-137">**將滑鼠移至**:手狀即將全像 」，這是進行通訊，手動變更視覺效果的目標全像圖。</span><span class="sxs-lookup"><span data-stu-id="01fd2-137">**Hover**: When hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="01fd2-138">**距離和的互動點**: 手狀接近全像圖時，設計通訊預計的互動點，以及如何遠離物件是指的意見反應</span><span class="sxs-lookup"><span data-stu-id="01fd2-138">**Distance and point of interaction**: As hand approaches hologram, design feedback to communicate the projected point of interaction, as well as how far from the object the finger is</span></span>
* <span data-ttu-id="01fd2-139">**請連絡 Begin**:變更視覺效果 （光線，色彩） 進行通訊的觸控發生</span><span class="sxs-lookup"><span data-stu-id="01fd2-139">**Contact Begin**: Change visuals (light, color) to communicate that touch has occured</span></span>
* <span data-ttu-id="01fd2-140">**Grasped**:變更視覺效果 （光線，色彩） grasped 物件的時機。</span><span class="sxs-lookup"><span data-stu-id="01fd2-140">**Grasped**: Change visuals (light, color) when the object is grasped.</span></span>
* <span data-ttu-id="01fd2-141">**請連絡結束**:變更視覺效果 （光線，色彩） 觸控時結束。</span><span class="sxs-lookup"><span data-stu-id="01fd2-141">**Contact End**: Change visuals (light, color) when touch has ended.</span></span>

<span data-ttu-id="01fd2-142">![視覺化附近互動狀態範例](images/640px-interactibleobject-states-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="01fd2-142">![Example of visualizing near interaction states](images/640px-interactibleobject-states-near.jpg)</span></span><br>
<span data-ttu-id="01fd2-143">*視覺化附近互動狀態範例*</span><span class="sxs-lookup"><span data-stu-id="01fd2-143">*Example of visualizing near interaction states*</span></span>

<span data-ttu-id="01fd2-144">[HoloLens 2 中的按鈕](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)示範視覺化不同輸入的互動狀態。</span><span class="sxs-lookup"><span data-stu-id="01fd2-144">The [Button in HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) shows the example of visualizing different input interaction states.</span></span>

<span data-ttu-id="01fd2-145">![HoloLens 2 pressable 按鈕的範例](images/640px-interactibleobject-pressablebutton-650px2.jpg)</span><span class="sxs-lookup"><span data-stu-id="01fd2-145">![Example of pressable button in HoloLens 2](images/640px-interactibleobject-pressablebutton-650px2.jpg)</span></span><br>
<span data-ttu-id="01fd2-146">*HoloLens 2 pressable 按鈕的範例*</span><span class="sxs-lookup"><span data-stu-id="01fd2-146">*Example of pressable button in HoloLens 2*</span></span>

<span data-ttu-id="01fd2-147">HoloLens 2 中沒有可改善使用者的信心，深度認知上其他視覺提示。</span><span class="sxs-lookup"><span data-stu-id="01fd2-147">In HoloLens 2, there is an additional visual cue which improves the user's confidence on the depth perception.</span></span> <span data-ttu-id="01fd2-148">上寫寫看信號出現，並相應減少，因為寫寫看即將來臨的物件。</span><span class="sxs-lookup"><span data-stu-id="01fd2-148">The ring on the fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="01fd2-149">按下狀態的一個點到最後聚合信號。</span><span class="sxs-lookup"><span data-stu-id="01fd2-149">The ring eventually converges into a dot on press state.</span></span> <span data-ttu-id="01fd2-150">此視覺化功能可見性可協助使用者了解物件之間的距離。</span><span class="sxs-lookup"><span data-stu-id="01fd2-150">This visual affordance helps the user understand the distance from the object.</span></span>

<span data-ttu-id="01fd2-151">![寫寫看環狀視覺效果](images/640px-interactibleobject-pressablebutton-650px3.jpg)</span><span class="sxs-lookup"><span data-stu-id="01fd2-151">![Fingertip ring visualization](images/640px-interactibleobject-pressablebutton-650px3.jpg)</span></span><br>
<span data-ttu-id="01fd2-152">*HoloLens 2 寫寫看環狀視覺效果*</span><span class="sxs-lookup"><span data-stu-id="01fd2-152">*Fingertip ring visualization in HoloLens 2*</span></span>

<span data-ttu-id="01fd2-153">![在手相近的視覺化回饋](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="01fd2-153">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
<span data-ttu-id="01fd2-154">*根據鄰近-週框方塊的視覺化回饋的範例*</span><span class="sxs-lookup"><span data-stu-id="01fd2-154">*Example of visual feedback based on the proximity - Bounding Box*</span></span>


### <a name="audio-cue"></a><span data-ttu-id="01fd2-155">音訊提示</span><span class="sxs-lookup"><span data-stu-id="01fd2-155">Audio cue</span></span>
<span data-ttu-id="01fd2-156">直接手動互動，適當的音訊意見反應可以大幅改善使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="01fd2-156">For the direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="01fd2-157">使用來傳達下列音訊意見反應：</span><span class="sxs-lookup"><span data-stu-id="01fd2-157">Use audio feedback to communicate the following:</span></span>
* <span data-ttu-id="01fd2-158">**請連絡開始**:觸控式開始時播放音效</span><span class="sxs-lookup"><span data-stu-id="01fd2-158">**Contact begin**: Play sound when touch begins</span></span>
* <span data-ttu-id="01fd2-159">**連絡人的結束**:播放音效觸控端</span><span class="sxs-lookup"><span data-stu-id="01fd2-159">**Contact end**: Play sound on touch end</span></span>
* <span data-ttu-id="01fd2-160">**抓取開始**:擷取啟動時播放音效</span><span class="sxs-lookup"><span data-stu-id="01fd2-160">**Grab begin**: Play sound when grab starts</span></span>
* <span data-ttu-id="01fd2-161">**抓取結束**:播放音效抓取端</span><span class="sxs-lookup"><span data-stu-id="01fd2-161">**Grab end**: Play sound on grab end</span></span>

### <a name="voice-command"></a><span data-ttu-id="01fd2-162">語音命令</span><span class="sxs-lookup"><span data-stu-id="01fd2-162">Voice command</span></span>
<span data-ttu-id="01fd2-163">任何可互動的物件，請務必支援替代的互動選項。</span><span class="sxs-lookup"><span data-stu-id="01fd2-163">For any interactable objects, it is important to support alternative interaction options.</span></span> <span data-ttu-id="01fd2-164">在預設情況下，建議您使用支援語音命令是可互動的任何物件。</span><span class="sxs-lookup"><span data-stu-id="01fd2-164">In default, it is recommended to support voice command for any objects that are interactable.</span></span> <span data-ttu-id="01fd2-165">若要改善探索能力，您可以提供工具提示上暫留狀態。</span><span class="sxs-lookup"><span data-stu-id="01fd2-165">To improve the discoverability, you can provide tooltip on hover state.</span></span>

<img src="images/640px-interactibleobject-voicecommand.jpg" alt="Tooltip for the voice command" title="語音命令的工具提示" width="350"><br/><span data-ttu-id="01fd2-167">*語音命令的工具提示*</span><span class="sxs-lookup"><span data-stu-id="01fd2-167">*Tooltip for the voice command*</span></span>

## <a name="creating-interactable-object-with-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="01fd2-168">建立可互動的物件與混合實境工具組 (MRTK)</span><span class="sxs-lookup"><span data-stu-id="01fd2-168">Creating interactable object with Mixed Reality Toolkit (MRTK)</span></span>

<span data-ttu-id="01fd2-169">在  **[混合實境 Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)** ，您可以找到 Unity 指令碼的一系列 prefabs，可協助您建立可互動的物件。</span><span class="sxs-lookup"><span data-stu-id="01fd2-169">In the **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can find the series of Unity scripts and prefabs that will help you create interactable objects.</span></span> <span data-ttu-id="01fd2-170">您可以使用這些物件的各種類型的輸入的互動狀態回應。</span><span class="sxs-lookup"><span data-stu-id="01fd2-170">You can use these to make objects respond to various types of input interaction states.</span></span>

* <span data-ttu-id="01fd2-171">**[Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)**</span><span class="sxs-lookup"><span data-stu-id="01fd2-171">**[Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)**</span></span>
* <span data-ttu-id="01fd2-172">**[按鈕](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)**</span><span class="sxs-lookup"><span data-stu-id="01fd2-172">**[Button](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)**</span></span>
* <span data-ttu-id="01fd2-173">**[手動互動範例場景](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)**</span><span class="sxs-lookup"><span data-stu-id="01fd2-173">**[Hand Interaction Examples Scene](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)**</span></span>

<span data-ttu-id="01fd2-174">提供各種選項，例如 MixedRealityToolkit 的標準著色器**鄰近 light**可協助您建立視覺與音訊提示。</span><span class="sxs-lookup"><span data-stu-id="01fd2-174">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* <span data-ttu-id="01fd2-175">**[MRTK 標準著色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)**</span><span class="sxs-lookup"><span data-stu-id="01fd2-175">**[MRTK Standard Shader](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)**</span></span>


## <a name="see-also"></a><span data-ttu-id="01fd2-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01fd2-176">See also</span></span>

* <span data-ttu-id="01fd2-177">**[週框方塊](app-bar-and-bounding-box.md)**</span><span class="sxs-lookup"><span data-stu-id="01fd2-177">**[Bounding Box](app-bar-and-bounding-box.md)**</span></span>
* <span data-ttu-id="01fd2-178">**[物件集合](object-collection.md)**</span><span class="sxs-lookup"><span data-stu-id="01fd2-178">**[Object collection](object-collection.md)**</span></span>
* <span data-ttu-id="01fd2-179">**[告示板和 tag-along](billboarding-and-tag-along.md)**</span><span class="sxs-lookup"><span data-stu-id="01fd2-179">**[Billboarding and tag-along](billboarding-and-tag-along.md)**</span></span>
