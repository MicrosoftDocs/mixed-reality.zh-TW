---
title: 週框方塊以及應用程式列
description: 應用程式列是物件層級功能表，其中包含一系列的下邊緣的雷射的界限會顯示的按鈕。
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality，橫條圖、 週框方塊的應用程式
ms.openlocfilehash: d289be31129324c6ff419b69dbce52bd8f62eb64
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829681"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="fb078-104">週框方塊以及應用程式列</span><span class="sxs-lookup"><span data-stu-id="fb078-104">Bounding box and App bar</span></span>
![週框是在混合實境中的物件操作的標準介面。](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="fb078-106">什麼是框方塊？</span><span class="sxs-lookup"><span data-stu-id="fb078-106">What is the Bounding box?</span></span>

<span data-ttu-id="fb078-107">週框是在混合實境中的物件操作的標準介面。</span><span class="sxs-lookup"><span data-stu-id="fb078-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="fb078-108">它會提供使用者功能的物件是目前可調整的可見性。</span><span class="sxs-lookup"><span data-stu-id="fb078-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="fb078-109">邊角，告訴使用者也可以調整的物件。</span><span class="sxs-lookup"><span data-stu-id="fb078-109">The corners tell the user that the object can also scale.</span></span> <span data-ttu-id="fb078-110">此視覺化功能可見性即使看不見的調整模式之外，顯示使用者物件 – 的總面積。</span><span class="sxs-lookup"><span data-stu-id="fb078-110">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="fb078-111">這是特別重要，因為如果不是那麼有，都會移動到另一個物件或介面的物件可能會出現，彷彿其周圍不應該有的空間。</span><span class="sxs-lookup"><span data-stu-id="fb078-111">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span> <span data-ttu-id="fb078-112">HoloLens 2 週框方塊搭配直接手動操作，並回應使用者的手指相近。</span><span class="sxs-lookup"><span data-stu-id="fb078-112">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="fb078-113">它會顯示視覺的意見反應，以協助使用者察覺物件之間的距離。</span><span class="sxs-lookup"><span data-stu-id="fb078-113">It shows visual feedback to help the user perceive the distance from the object.</span></span> 

<span data-ttu-id="fb078-114">![HoloLens-的-觀點來調整物件透過週框方塊](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="fb078-114">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
<span data-ttu-id="fb078-115">*調整物件透過週框方塊*</span><span class="sxs-lookup"><span data-stu-id="fb078-115">*Scaling an object via bounding box*</span></span>

<span data-ttu-id="fb078-116">週框方塊邊角中的控制代碼會遵循廣泛了解調整規模模式。</span><span class="sxs-lookup"><span data-stu-id="fb078-116">The handles in the corners of the bounding box follow a widely understood pattern for adjusting scale.</span></span> 

<span data-ttu-id="fb078-117">![HoloLens-的-觀點來旋轉物件透過週框方塊](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="fb078-117">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
<span data-ttu-id="fb078-118">*旋轉物件透過週框方塊*</span><span class="sxs-lookup"><span data-stu-id="fb078-118">*Rotating an object via bounding box*</span></span>


<span data-ttu-id="fb078-119">![在手相近的視覺化回饋](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="fb078-119">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
<span data-ttu-id="fb078-120">*根據鄰近的視覺化回饋*</span><span class="sxs-lookup"><span data-stu-id="fb078-120">*Visual feedback based on the proximity*</span></span>

<span data-ttu-id="fb078-121">週框方塊邊緣的垂直矩形提供會旋轉指示器。</span><span class="sxs-lookup"><span data-stu-id="fb078-121">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="fb078-122">這會讓使用者更多的細緻調整透過其放置全像投影。</span><span class="sxs-lookup"><span data-stu-id="fb078-122">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="fb078-123">不只可以調整及縮放，但現在也旋轉。</span><span class="sxs-lookup"><span data-stu-id="fb078-123">Not only can they adjust and scale, but now rotate as well.</span></span>

* <span data-ttu-id="fb078-124">開發 Unity 應用程式，請參閱[框方塊上混合實境工具組-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span><span class="sxs-lookup"><span data-stu-id="fb078-124">For Unity app development, see [Bounding box on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span></span>



## <a name="what-is-the-app-bar"></a><span data-ttu-id="fb078-125">什麼是應用程式列？</span><span class="sxs-lookup"><span data-stu-id="fb078-125">What is the App bar?</span></span>

<span data-ttu-id="fb078-126">應用程式列是物件層級功能表，其中包含一系列的下邊緣的雷射的界限會顯示的按鈕。</span><span class="sxs-lookup"><span data-stu-id="fb078-126">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="fb078-127">此模式通常會用來讓使用者能夠移除，並調整全像投影中。</span><span class="sxs-lookup"><span data-stu-id="fb078-127">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span>

<span data-ttu-id="fb078-128">因為此模式會鎖定，世界，當使用者移動應用程式列一律會顯示在最接近使用者的物件端的物件周圍的物件。</span><span class="sxs-lookup"><span data-stu-id="fb078-128">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="fb078-129">雖然這不告示板中，有效地達成相同的結果;防止使用者的位置向 occlude 或會使用從他們的環境中的不同位置的區塊功能。</span><span class="sxs-lookup"><span data-stu-id="fb078-129">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span>

<span data-ttu-id="fb078-130">![雷射四處跑。</span><span class="sxs-lookup"><span data-stu-id="fb078-130">![Walking around a hologram.</span></span> <span data-ttu-id="fb078-131">應用程式列後面。](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="fb078-131">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
<span data-ttu-id="fb078-132">*雷射四處跑，遵循應用程式列*</span><span class="sxs-lookup"><span data-stu-id="fb078-132">*Walking around a hologram, the App bar follows*</span></span>

<span data-ttu-id="fb078-133">應用程式列中的設計主要是做為管理使用者的環境中放置的物件的方式。</span><span class="sxs-lookup"><span data-stu-id="fb078-133">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="fb078-134">搭配週框方塊，使用者可以完全控制在混合實境中何處以及如何為導向的物件。</span><span class="sxs-lookup"><span data-stu-id="fb078-134">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

* <span data-ttu-id="fb078-135">開發 Unity 應用程式，請參閱[應用程式列上混合實境工具組-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span><span class="sxs-lookup"><span data-stu-id="fb078-135">For Unity app development, see [App bar on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span></span>

## <a name="see-also"></a><span data-ttu-id="fb078-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb078-136">See also</span></span>
* [<span data-ttu-id="fb078-137">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="fb078-137">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="fb078-138">Unity 中的文字</span><span class="sxs-lookup"><span data-stu-id="fb078-138">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="fb078-139">物件集合</span><span class="sxs-lookup"><span data-stu-id="fb078-139">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="fb078-140">顯示進度</span><span class="sxs-lookup"><span data-stu-id="fb078-140">Displaying progress</span></span>](progress.md)
