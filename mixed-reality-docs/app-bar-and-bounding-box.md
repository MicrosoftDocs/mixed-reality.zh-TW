---
title: 應用程式列和週框方塊
description: 應用程式列是物件層級功能表，其中包含一系列的下邊緣的雷射的界限會顯示的按鈕。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，橫條圖、 週框方塊的應用程式
ms.openlocfilehash: bdce92e00193230d1f7a487f11ef0487f1d6657c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595300"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="b4644-104">週框方塊以及應用程式列</span><span class="sxs-lookup"><span data-stu-id="b4644-104">Bounding box and App bar</span></span>
![週框是在混合實境中的物件操作的標準介面。](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="b4644-106">什麼是框方塊？</span><span class="sxs-lookup"><span data-stu-id="b4644-106">What is the Bounding box?</span></span>

<span data-ttu-id="b4644-107">週框是在混合實境中的物件操作的標準介面。</span><span class="sxs-lookup"><span data-stu-id="b4644-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="b4644-108">它會提供使用者功能的物件是目前可調整的可見性。</span><span class="sxs-lookup"><span data-stu-id="b4644-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="b4644-109">邊角，告訴使用者也可以調整的物件。</span><span class="sxs-lookup"><span data-stu-id="b4644-109">The corners tell the user that the object can also scale.</span></span> <span data-ttu-id="b4644-110">此視覺化功能可見性即使看不見的調整模式之外，顯示使用者物件 – 的總面積。</span><span class="sxs-lookup"><span data-stu-id="b4644-110">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="b4644-111">這是特別重要，因為如果不是那麼有，都會移動到另一個物件或介面的物件可能會出現，彷彿其周圍不應該有的空間。</span><span class="sxs-lookup"><span data-stu-id="b4644-111">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span> <span data-ttu-id="b4644-112">HoloLens 2 週框方塊會回應使用者的手指相近。</span><span class="sxs-lookup"><span data-stu-id="b4644-112">On HoloLens 2, the bounding box responds to the user's finger's proximity.</span></span> <span data-ttu-id="b4644-113">它會顯示視覺的意見反應，以協助察覺物件之間的距離。</span><span class="sxs-lookup"><span data-stu-id="b4644-113">It shows visual feedback to help perceive the distance from the object.</span></span> 

<span data-ttu-id="b4644-114">![HoloLens-的-觀點來調整物件透過週框方塊](images/bounding-box-scale.gif)</span><span class="sxs-lookup"><span data-stu-id="b4644-114">![HoloLens point-of-view of scaling an object via bounding box](images/bounding-box-scale.gif)</span></span><br>
<span data-ttu-id="b4644-115">*調整物件透過週框方塊*</span><span class="sxs-lookup"><span data-stu-id="b4644-115">*Scaling an object via bounding box*</span></span>

<span data-ttu-id="b4644-116">週框方塊類似 cube 的邊角遵循廣泛了解適用於調整規模模式。</span><span class="sxs-lookup"><span data-stu-id="b4644-116">The cube-like corners of the bounding box follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="b4644-117">結合使用明確的動作，將物件放入 」 調整模式 」 的是可以同時移動物件，但也在其環境中調整它清除。</span><span class="sxs-lookup"><span data-stu-id="b4644-117">Coupled with the explicit action of putting an object into “adjust mode” it’s clear they can both move the object, but also scale it in their environment.</span></span>

<span data-ttu-id="b4644-118">![HoloLens-的-觀點來旋轉物件透過週框方塊](images/bounding-box-rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="b4644-118">![HoloLens point-of-view of rotating an object via bounding box](images/bounding-box-rotate.gif)</span></span><br>
<span data-ttu-id="b4644-119">*旋轉物件透過週框方塊*</span><span class="sxs-lookup"><span data-stu-id="b4644-119">*Rotating an object via bounding box*</span></span>

<span data-ttu-id="b4644-120">週框方塊的邊緣上更低的球面的提供是旋轉指標。</span><span class="sxs-lookup"><span data-stu-id="b4644-120">The spherical affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="b4644-121">這會讓使用者更多的細緻調整透過其放置全像投影。</span><span class="sxs-lookup"><span data-stu-id="b4644-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="b4644-122">不只可以調整及縮放，但現在也旋轉。</span><span class="sxs-lookup"><span data-stu-id="b4644-122">Not only can they adjust and scale, but now rotate as well.</span></span>

* <span data-ttu-id="b4644-123">開發 Unity 應用程式，請參閱[框方塊上混合實境工具組-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span><span class="sxs-lookup"><span data-stu-id="b4644-123">For Unity app development, see [Bounding box on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span></span>

## <a name="what-is-the-app-bar"></a><span data-ttu-id="b4644-124">什麼是應用程式列？</span><span class="sxs-lookup"><span data-stu-id="b4644-124">What is the App bar?</span></span>

<span data-ttu-id="b4644-125">應用程式列是物件層級功能表，其中包含一系列的下邊緣的雷射的界限會顯示的按鈕。</span><span class="sxs-lookup"><span data-stu-id="b4644-125">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="b4644-126">此模式通常會用來讓使用者能夠移除，並調整全像投影中。</span><span class="sxs-lookup"><span data-stu-id="b4644-126">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span>

<span data-ttu-id="b4644-127">因為此模式會鎖定，世界，當使用者移動應用程式列一律會顯示在最接近使用者的物件端的物件周圍的物件。</span><span class="sxs-lookup"><span data-stu-id="b4644-127">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="b4644-128">雖然這不告示板中，有效地達成相同的結果;防止使用者的位置向 occlude 或會使用從他們的環境中的不同位置的區塊功能。</span><span class="sxs-lookup"><span data-stu-id="b4644-128">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span>

<span data-ttu-id="b4644-129">![雷射四處跑。</span><span class="sxs-lookup"><span data-stu-id="b4644-129">![Walking around a hologram.</span></span> <span data-ttu-id="b4644-130">應用程式列後面。](images/holobar-followuser.gif)</span><span class="sxs-lookup"><span data-stu-id="b4644-130">The App bar follows.](images/holobar-followuser.gif)</span></span><br>
<span data-ttu-id="b4644-131">*雷射四處跑，遵循應用程式列*</span><span class="sxs-lookup"><span data-stu-id="b4644-131">*Walking around a hologram, the App bar follows*</span></span>

<span data-ttu-id="b4644-132">應用程式列中的設計主要是做為管理使用者的環境中放置的物件的方式。</span><span class="sxs-lookup"><span data-stu-id="b4644-132">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="b4644-133">搭配週框方塊，使用者可以完全控制在混合實境中何處以及如何為導向的物件。</span><span class="sxs-lookup"><span data-stu-id="b4644-133">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

* <span data-ttu-id="b4644-134">開發 Unity 應用程式，請參閱[應用程式列上混合實境工具組-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span><span class="sxs-lookup"><span data-stu-id="b4644-134">For Unity app development, see [App bar on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span></span>

## <a name="see-also"></a><span data-ttu-id="b4644-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4644-135">See also</span></span>
* [<span data-ttu-id="b4644-136">週框方塊上混合實境工具組-Unity</span><span class="sxs-lookup"><span data-stu-id="b4644-136">Bounding box on Mixed Reality Toolkit-Unity</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)
* [<span data-ttu-id="b4644-137">應用程式列上混合實境工具組-Unity</span><span class="sxs-lookup"><span data-stu-id="b4644-137">App bar on Mixed Reality Toolkit-Unity</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)
* [<span data-ttu-id="b4644-138">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="b4644-138">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="b4644-139">在 Unity 中的文字</span><span class="sxs-lookup"><span data-stu-id="b4644-139">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="b4644-140">物件集合</span><span class="sxs-lookup"><span data-stu-id="b4644-140">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="b4644-141">顯示進度</span><span class="sxs-lookup"><span data-stu-id="b4644-141">Displaying progress</span></span>](progress.md)
