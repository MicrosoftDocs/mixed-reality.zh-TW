---
title: 可互動的物件
description: 按鈕長久以來所用的觸發事件 2D 抽象全球隱喻。 在三維的混合的現實世界中，我們沒有不再侷限於這個抽象層再的世界。
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 混合的實境、 控制項、 互動、 ui、 ux
ms.openlocfilehash: f349d21707375690e00b0f7e465634c62be1537e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594760"
---
# <a name="interactable-object"></a><span data-ttu-id="9c96f-105">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="9c96f-105">Interactable object</span></span>

<span data-ttu-id="9c96f-106">按鈕長久以來所用的觸發事件 2D 抽象全球隱喻。</span><span class="sxs-lookup"><span data-stu-id="9c96f-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="9c96f-107">在三維的混合的現實世界中，我們沒有不再侷限於這個抽象層再的世界。</span><span class="sxs-lookup"><span data-stu-id="9c96f-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="9c96f-108">任何能**互動的物件**觸發事件。</span><span class="sxs-lookup"><span data-stu-id="9c96f-108">Anything can be an **Interactable object** that triggers an event.</span></span> <span data-ttu-id="9c96f-109">可互動的物件可以表示為任何項目從咖啡杯資料表在空中浮在球形文字說明。</span><span class="sxs-lookup"><span data-stu-id="9c96f-109">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="9c96f-110">我們仍執行能用在某些情況下這類對話方塊 UI 如同傳統的按鈕。</span><span class="sxs-lookup"><span data-stu-id="9c96f-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="9c96f-111">按鈕的視覺表示方式取決於內容。</span><span class="sxs-lookup"><span data-stu-id="9c96f-111">The visual representation of the button depends on the context.</span></span>

![Interactible 物件英雄影像](images/640px-interactibleobject-hero-640px.jpg)


<span data-ttu-id="9c96f-113">在  **[混合實境 Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)**，我們建立了一系列的 Unity 指令碼和 prefabs，可協助您建立可互動的物件。</span><span class="sxs-lookup"><span data-stu-id="9c96f-113">In the **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, we have created a series of Unity scripts and prefabs that will help you create Interactable objects.</span></span> <span data-ttu-id="9c96f-114">您可以使用這些來建立任何類型的使用者可以與之互動，使用這些標準的互動狀態的物件： 觀察，設為目標，並按下。</span><span class="sxs-lookup"><span data-stu-id="9c96f-114">You can use these to create any type of object that the user can interact with, using these standard interaction states: observation, targeted and pressed.</span></span> <span data-ttu-id="9c96f-115">您可以輕鬆自訂視覺效果的設計，與您自己的資產。</span><span class="sxs-lookup"><span data-stu-id="9c96f-115">You can easily customize the visual design with your own assets.</span></span> <span data-ttu-id="9c96f-116">詳細的動畫可以自訂所建立，並指派對應的動畫剪輯，在 Unity 的 [動畫] 控制器中的互動狀態，或使用 offset 和小數位數。</span><span class="sxs-lookup"><span data-stu-id="9c96f-116">Detailed animations can be customized by either creating and assigning corresponding animation clips for the interaction states in the Unity's animation controller or using offset and scale.</span></span> 


## <a name="visual-feedback-for-the-different-input-interaction-states"></a><span data-ttu-id="9c96f-117">針對不同的輸入的互動狀態的視覺回饋</span><span class="sxs-lookup"><span data-stu-id="9c96f-117">Visual feedback for the different input interaction states</span></span>

<span data-ttu-id="9c96f-118">在混合實境，全像攝影版的物件會混合使用真實世界的環境，因為它可能會難以了解哪些物件是可互動。</span><span class="sxs-lookup"><span data-stu-id="9c96f-118">In mixed reality, since the holographic objects are mixed with the real-world environment, it could be difficult to understand which objects are interactable.</span></span> <span data-ttu-id="9c96f-119">在您的經驗中任何可互動的物件，請務必提供差異化的視覺化回饋，針對每個輸入的狀態。</span><span class="sxs-lookup"><span data-stu-id="9c96f-119">For any interactable objects in your experience, it is important to provide differentiated visual feedback for each input state.</span></span> <span data-ttu-id="9c96f-120">這可協助使用者了解您的使用經驗的哪個部分是可互動，並使用一致的互動方法，讓使用者有信心。</span><span class="sxs-lookup"><span data-stu-id="9c96f-120">This helps the user understand which part of your experience is interactable and makes the user confident with consistent interaction method.</span></span>

<span data-ttu-id="9c96f-121">任何物件該使用者可以與互動，我們建議使用有不同的視覺回饋，針對這三個輸入狀態：</span><span class="sxs-lookup"><span data-stu-id="9c96f-121">For any objects that user can interact with, we recommended to have different visual feedback for these three input states:</span></span>
* <span data-ttu-id="9c96f-122">**觀察**:預設的閒置狀態的物件。</span><span class="sxs-lookup"><span data-stu-id="9c96f-122">**Observation**: Default idle state of the object.</span></span>
* <span data-ttu-id="9c96f-123">**目標**:當物件的目標與視線指標時，手指鄰近性或動作控制器的指標。</span><span class="sxs-lookup"><span data-stu-id="9c96f-123">**Targeted**: When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
* <span data-ttu-id="9c96f-124">**按下**:當物件已按下使用空中點選手勢、 手指按或動作控制器的 [選取] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="9c96f-124">**Pressed**: When the object is pressed with air-tap gesture, finger press or motion controller's select button.</span></span>

<span data-ttu-id="9c96f-125">![全像攝影版的按鈕](images/640px-interactibleobject-holographicbutton-650px.jpg)</span><span class="sxs-lookup"><span data-stu-id="9c96f-125">![Holographic button](images/640px-interactibleobject-holographicbutton-650px.jpg)</span></span><br>
<span data-ttu-id="9c96f-126">*觀察狀態設為目標的狀態，並按下狀態*</span><span class="sxs-lookup"><span data-stu-id="9c96f-126">*Observation state, targeted state, and pressed state*</span></span>

<span data-ttu-id="9c96f-127">在 Windows Mixed Reality，您可以找到視覺化不同輸入的狀態，在 [開始] 功能表和應用程式列按鈕的範例。</span><span class="sxs-lookup"><span data-stu-id="9c96f-127">In Windows Mixed Reality, you can find the examples of visualizing different input states on Start menu and App Bar buttons.</span></span> <span data-ttu-id="9c96f-128">您可以使用的技術，例如反白顯示或縮放比例提供視覺化回應使用者輸入的狀態。</span><span class="sxs-lookup"><span data-stu-id="9c96f-128">You can use techniques such as highlighting or scaling to provide visual feedback to the user’s input states.</span></span>

<span data-ttu-id="9c96f-129">在 HoloLens 2 中，因為它支援完全相互連貫的手動追蹤輸入，我們可以提供根據傳遞給鄰近的額外提供。</span><span class="sxs-lookup"><span data-stu-id="9c96f-129">In HoloLens 2, since it supports fully articulated hand tracking input, we can provide additional affordances based on the proximity to the hands.</span></span> <span data-ttu-id="9c96f-130">[HoloLens 2 中的按鈕](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)顯示此範例。</span><span class="sxs-lookup"><span data-stu-id="9c96f-130">The [Button in HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) shows this example.</span></span>

![Pressable 按鈕](images/640px-interactibleobject-pressablebutton-650px.jpg)<br>




## <a name="interactable-object-samples"></a><span data-ttu-id="9c96f-132">可互動的物件範例</span><span class="sxs-lookup"><span data-stu-id="9c96f-132">Interactable object samples</span></span>

### <a name="mesh-button"></a><span data-ttu-id="9c96f-133">網狀結構按鈕</span><span class="sxs-lookup"><span data-stu-id="9c96f-133">Mesh button</span></span>

![網狀結構按鈕](images/640px-interactibleobject-meshbutton.jpg)

<span data-ttu-id="9c96f-135">這些是可互動的物件為使用基本類型和匯入的 3D 網格的範例。</span><span class="sxs-lookup"><span data-stu-id="9c96f-135">These are examples using primitives and imported 3D meshes as Interactable objects.</span></span> <span data-ttu-id="9c96f-136">您可以輕鬆地指派不同的規模、 位移和色彩值來回應每個輸入的互動狀態。</span><span class="sxs-lookup"><span data-stu-id="9c96f-136">You can easily assign different scale, offset and color values to respond to each input interaction state.</span></span>

### <a name="toolbar"></a><span data-ttu-id="9c96f-137">工具列</span><span class="sxs-lookup"><span data-stu-id="9c96f-137">Toolbar</span></span>

![工具列](images/640px-interactibleobject-toolbar.jpg)

<span data-ttu-id="9c96f-139">工具列是廣泛使用的模式，在混合的實境體驗中。</span><span class="sxs-lookup"><span data-stu-id="9c96f-139">A toolbar is a widely used pattern in mixed reality experiences.</span></span> <span data-ttu-id="9c96f-140">它是簡單的按鈕與其他的行為集合，例如[Billboarding 和 tag-along](billboarding-and-tag-along.md)。</span><span class="sxs-lookup"><span data-stu-id="9c96f-140">It is a simple collection of buttons with additional behaviors such as [Billboarding and tag-along](billboarding-and-tag-along.md).</span></span> <span data-ttu-id="9c96f-141">此範例會使用從 MixedRealityToolkit Billboarding 和 tag-along 指令碼。</span><span class="sxs-lookup"><span data-stu-id="9c96f-141">This example uses a Billboarding and tag-along script from the MixedRealityToolkit.</span></span> <span data-ttu-id="9c96f-142">您可以控制詳細的行為，包括距離，移動速度和臨界值。</span><span class="sxs-lookup"><span data-stu-id="9c96f-142">You can control detailed behaviors including distance, moving speed and threshold values.</span></span>

### <a name="traditional-button"></a><span data-ttu-id="9c96f-143">傳統的按鈕</span><span class="sxs-lookup"><span data-stu-id="9c96f-143">Traditional button</span></span>

![傳統的按鈕](images/640px-interactibleobject-traditionalbutton.jpg)

<span data-ttu-id="9c96f-145">此範例顯示傳統的 2D 樣式 按鈕。</span><span class="sxs-lookup"><span data-stu-id="9c96f-145">This example shows a traditional 2D style button.</span></span> <span data-ttu-id="9c96f-146">每個輸入的狀態具有稍有不同的深度和動畫屬性。</span><span class="sxs-lookup"><span data-stu-id="9c96f-146">Each input state has a slightly different depth and animation property.</span></span>

### <a name="other-examples"></a><span data-ttu-id="9c96f-147">其他範例</span><span class="sxs-lookup"><span data-stu-id="9c96f-147">Other examples</span></span>

<span data-ttu-id="9c96f-148">![推播 按鈕](images/640px-interactibleobject-pushbutton.jpg)</span><span class="sxs-lookup"><span data-stu-id="9c96f-148">![Push button](images/640px-interactibleobject-pushbutton.jpg)</span></span><br>
<span data-ttu-id="9c96f-149">*推播 按鈕*</span><span class="sxs-lookup"><span data-stu-id="9c96f-149">*Push button*</span></span>
<br>
<span data-ttu-id="9c96f-150">![真實生活物件](images/640px-interactibleobject-reallifeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="9c96f-150">![Real Life object](images/640px-interactibleobject-reallifeobject.jpg)</span></span><br>
<span data-ttu-id="9c96f-151">*真實物件*</span><span class="sxs-lookup"><span data-stu-id="9c96f-151">*Real life object*</span></span>

<span data-ttu-id="9c96f-152">使用 HoloLens，您可以利用的實體空間。</span><span class="sxs-lookup"><span data-stu-id="9c96f-152">With HoloLens, you can leverage physical space.</span></span> <span data-ttu-id="9c96f-153">想像一下全像攝影版的按鈕，在實體的塗鴉牆上。</span><span class="sxs-lookup"><span data-stu-id="9c96f-153">Imagine a holographic push button on a physical wall.</span></span> <span data-ttu-id="9c96f-154">或如何在實際的資料表上的咖啡 cup？</span><span class="sxs-lookup"><span data-stu-id="9c96f-154">Or how about a coffee cup on a real table?</span></span> <span data-ttu-id="9c96f-155">使用從模型化軟體匯入的 3D 模型，我們可以建立可互動的物件，類似於現實生活中的物件。</span><span class="sxs-lookup"><span data-stu-id="9c96f-155">Using 3D models imported from modeling software, we can create an Interactable object that resembles real life object.</span></span> <span data-ttu-id="9c96f-156">因為它是數位物件時，我們可以新增神奇的互動。</span><span class="sxs-lookup"><span data-stu-id="9c96f-156">Since it's a digital object, we can add magical interactions to it.</span></span>

## <a name="interactable-object-in-mixed-reality-toolkit"></a><span data-ttu-id="9c96f-157">混合實境工具組中的互動物件</span><span class="sxs-lookup"><span data-stu-id="9c96f-157">Interactable object in Mixed Reality Toolkit</span></span>
<span data-ttu-id="9c96f-158">您可以找到[Interactable 範例物件混合實境工具組中](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)</span><span class="sxs-lookup"><span data-stu-id="9c96f-158">You can find the [examples of Interactable object in Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)</span></span>


## <a name="see-also"></a><span data-ttu-id="9c96f-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c96f-159">See also</span></span>
* [<span data-ttu-id="9c96f-160">在混合的實境 Toolkit Unity pressable 按鈕</span><span class="sxs-lookup"><span data-stu-id="9c96f-160">Pressable Button on Mixed Reality Toolkit-Unity</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="9c96f-161">物件集合</span><span class="sxs-lookup"><span data-stu-id="9c96f-161">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="9c96f-162">告示板和 tag-along</span><span class="sxs-lookup"><span data-stu-id="9c96f-162">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
