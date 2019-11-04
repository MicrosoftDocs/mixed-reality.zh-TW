---
title: 周框方塊和應用程式行
description: 應用程式行是一個物件層級的功能表，其中包含一系列的按鈕，可顯示在全息圖界限的下邊緣。
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality，應用程式行，周框方塊
ms.openlocfilehash: f09187bc2a3969a8f844711052e15433f5449d6d
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437060"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="778fc-104">周框方塊和應用程式行</span><span class="sxs-lookup"><span data-stu-id="778fc-104">Bounding box and App bar</span></span>
![周框是混合現實中物件操作的標準介面。](images/640px-boundingbox-hero.jpg)<br>

<br>

---

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="778fc-106">什麼是周框方塊？</span><span class="sxs-lookup"><span data-stu-id="778fc-106">What is the Bounding box?</span></span>

<span data-ttu-id="778fc-107">周框是混合現實中物件操作的標準介面。</span><span class="sxs-lookup"><span data-stu-id="778fc-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="778fc-108">它會為使用者提供物件目前可調整的 affordance。</span><span class="sxs-lookup"><span data-stu-id="778fc-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="778fc-109">在 HoloLens 2 上，周框方塊適用于直接操作，並會回應使用者的 finger's 鄰近性。</span><span class="sxs-lookup"><span data-stu-id="778fc-109">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="778fc-110">它會顯示視覺化的意見反應，以協助使用者感知物件的距離。</span><span class="sxs-lookup"><span data-stu-id="778fc-110">It shows visual feedback to help the user perceive the distance from the object.</span></span>

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a><span data-ttu-id="778fc-111">縮放物件</span><span class="sxs-lookup"><span data-stu-id="778fc-111">Scaling an object</span></span><br>
        <span data-ttu-id="778fc-112">周框方塊的角落告訴使用者該物件可以調整。</span><span class="sxs-lookup"><span data-stu-id="778fc-112">The corners of the bounding box tell the user that the object can scale.</span></span> <span data-ttu-id="778fc-113">控點會遵循廣泛瞭解的調整尺規模式。</span><span class="sxs-lookup"><span data-stu-id="778fc-113">The handles follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="778fc-114">此視覺效果 affordance 會顯示使用者物件的總區域，即使它在調整模式之外看不到也一樣。</span><span class="sxs-lookup"><span data-stu-id="778fc-114">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="778fc-115">這點特別重要，因為如果不存在，則將物件貼齊至另一個物件或表面時，其行為可能會與不應存在的空間相同。</span><span class="sxs-lookup"><span data-stu-id="778fc-115">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span><br>
        <br>
        <span data-ttu-id="778fc-116">*影片迴圈：透過周框方塊縮放物件*</span><span class="sxs-lookup"><span data-stu-id="778fc-116">*Video loop: Scaling an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="778fc-117">![空間](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="778fc-117">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="778fc-118">![HoloLens 透過周框方塊縮放物件的觀點](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="778fc-118">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a><span data-ttu-id="778fc-119">旋轉物件</span><span class="sxs-lookup"><span data-stu-id="778fc-119">Rotating an object</span></span><br>
        <span data-ttu-id="778fc-120">周框方塊邊緣的垂直矩形 affordances 是旋轉指示器。</span><span class="sxs-lookup"><span data-stu-id="778fc-120">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="778fc-121">這可讓使用者更精細地調整其放入的全息影像。</span><span class="sxs-lookup"><span data-stu-id="778fc-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="778fc-122">不僅可以調整和縮放，而且現在也會旋轉。</span><span class="sxs-lookup"><span data-stu-id="778fc-122">Not only can they adjust and scale, but now rotate as well.</span></span><br>
        <br>
        <span data-ttu-id="778fc-123">*影片迴圈：透過周框方塊旋轉物件*</span><span class="sxs-lookup"><span data-stu-id="778fc-123">*Video loop: Rotating an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="778fc-124">![空間](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="778fc-124">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="778fc-125">![HoloLens 透過周框方塊旋轉物件](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="778fc-125">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a><span data-ttu-id="778fc-126">HoloLens 2 上有關手近距離的視覺回饋</span><span class="sxs-lookup"><span data-stu-id="778fc-126">Visual feedback on hand proximity on HoloLens 2</span></span><br>
        <span data-ttu-id="778fc-127">在 HoloLens 2 上有其他視覺提示，可協助使用者深入瞭解。</span><span class="sxs-lookup"><span data-stu-id="778fc-127">On HoloLens 2, there is an additional visual cue which can help the user's perception of depth.</span></span> <span data-ttu-id="778fc-128">當 fingertip 接近物件時，會顯示 fingertip 附近的環形並相應減少。</span><span class="sxs-lookup"><span data-stu-id="778fc-128">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="778fc-129">當到達已按下的狀態時，環形最後會聚合成一個點。</span><span class="sxs-lookup"><span data-stu-id="778fc-129">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="778fc-130">此視覺效果 affordance 可協助使用者瞭解他們與物件之間的距離。</span><span class="sxs-lookup"><span data-stu-id="778fc-130">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="778fc-131">*影片迴圈：根據距離周框方塊的視覺效果意見反應範例*</span><span class="sxs-lookup"><span data-stu-id="778fc-131">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="778fc-132">![空間](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="778fc-132">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="778fc-133">![視覺效果意見反應](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="778fc-133">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="778fc-134">**針對 Unity 應用程式開發，請參閱[混合現實工具組-Unity 中的周框方塊。](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span><span class="sxs-lookup"><span data-stu-id="778fc-134">**For Unity app development, see [Bounding box in the Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span></span>

<br>

---

## <a name="what-is-the-app-bar"></a><span data-ttu-id="778fc-135">什麼是應用程式行？</span><span class="sxs-lookup"><span data-stu-id="778fc-135">What is the App bar?</span></span>

<span data-ttu-id="778fc-136">應用程式行是一個物件層級的功能表，其中包含一系列的按鈕，可顯示在全息圖界限的下邊緣。</span><span class="sxs-lookup"><span data-stu-id="778fc-136">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="778fc-137">此模式通常用來提供使用者移除和調整全息影像的能力。</span><span class="sxs-lookup"><span data-stu-id="778fc-137">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span> <span data-ttu-id="778fc-138">應用程式行主要是用來在使用者環境中管理放置物件的一種方式。</span><span class="sxs-lookup"><span data-stu-id="778fc-138">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="778fc-139">與周框方塊結合，使用者可以完全掌控物件在混合現實中的方向和方式。</span><span class="sxs-lookup"><span data-stu-id="778fc-139">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a><span data-ttu-id="778fc-140">應用程式行會遵循使用者</span><span class="sxs-lookup"><span data-stu-id="778fc-140">The App bar follows the user</span></span><br>
        <span data-ttu-id="778fc-141">由於此模式會與世界鎖定的物件搭配使用，因此當使用者四處移動物件時，應用程式行一律會顯示在最靠近使用者的物件端。</span><span class="sxs-lookup"><span data-stu-id="778fc-141">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="778fc-142">雖然這不是 billboarding 的，但實際上會達到相同的結果;防止使用者的位置遮蔽或封鎖在其環境中不同位置可能會提供的功能。</span><span class="sxs-lookup"><span data-stu-id="778fc-142">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span> <br>
        <br>
        <span data-ttu-id="778fc-143">*影片迴圈：四處流覽全像投影，應用程式行如下*</span><span class="sxs-lookup"><span data-stu-id="778fc-143">*Video loop: Walking around a hologram, the App bar follows*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="778fc-144">![空間](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="778fc-144">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="778fc-145">![四處流覽全像投影。</span><span class="sxs-lookup"><span data-stu-id="778fc-145">![Walking around a hologram.</span></span> <span data-ttu-id="778fc-146">應用程式行如下。](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="778fc-146">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>



<span data-ttu-id="778fc-147">**針對 Unity 應用程式開發，請參閱[混合現實工具組-Unity 中的應用程式行。](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)**</span><span class="sxs-lookup"><span data-stu-id="778fc-147">**For Unity app development, see [App bar in the Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)**</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="778fc-148">請參閱</span><span class="sxs-lookup"><span data-stu-id="778fc-148">See also</span></span>
* [<span data-ttu-id="778fc-149">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="778fc-149">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="778fc-150">Unity 中的文字</span><span class="sxs-lookup"><span data-stu-id="778fc-150">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="778fc-151">物件集合</span><span class="sxs-lookup"><span data-stu-id="778fc-151">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="778fc-152">顯示進度</span><span class="sxs-lookup"><span data-stu-id="778fc-152">Displaying progress</span></span>](progress.md)
