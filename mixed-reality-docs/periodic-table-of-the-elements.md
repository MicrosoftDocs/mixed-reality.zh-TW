---
title: 元素週期表
description: 專案的定期資料表是來自 Microsoft Mixed Reality 設計實驗室的開放原始碼範例應用程式, 您可以在其中瞭解如何使用物件集合, 在3D 空間中配置具有各種介面類別型的物件陣列。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、設計、範例應用程式、控制項
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525293"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="e81be-104">元素週期表</span><span class="sxs-lookup"><span data-stu-id="e81be-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="e81be-105">本文討論我們在[混合現實設計實驗室](https://github.com/Microsoft/MRDesignLabs_Unity)中建立的探索範例, 這是我們分享我們學習的相關資訊, 並提供混合現實應用程式開發的建議。</span><span class="sxs-lookup"><span data-stu-id="e81be-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="e81be-106">我們的設計相關文章和程式碼將會隨著我們進行新的探索而演進。</span><span class="sxs-lookup"><span data-stu-id="e81be-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="e81be-107">[元素的定期資料表](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)是來自 Microsoft 混合現實設計實驗室的開放原始碼範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="e81be-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is a open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="e81be-108">與此專案中，您可以了解如何使用各種使用的介面型別來配置在 3D 空間中物件的陣列 **[物件集合](object-collection.md)** 。</span><span class="sxs-lookup"><span data-stu-id="e81be-108">With this project, you can learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](object-collection.md)**.</span></span> <span data-ttu-id="e81be-109">另請瞭解如何建立可回應 HoloLens 標準輸入的可互動物件。</span><span class="sxs-lookup"><span data-stu-id="e81be-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="e81be-110">您可以使用這個專案的元件來建立自己的混合現實應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="e81be-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![Elements 應用程式的期間資料表](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a><span data-ttu-id="e81be-112">關於應用程式</span><span class="sxs-lookup"><span data-stu-id="e81be-112">About the app</span></span>

<span data-ttu-id="e81be-113">專案的定期資料表會在3D 空間中將化學元素和其每個屬性視覺化。</span><span class="sxs-lookup"><span data-stu-id="e81be-113">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="e81be-114">它結合了 HoloLens 的基本互動, 例如注視和空中。</span><span class="sxs-lookup"><span data-stu-id="e81be-114">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="e81be-115">使用者可以瞭解具有動畫3D 模型的元素。</span><span class="sxs-lookup"><span data-stu-id="e81be-115">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="e81be-116">他們可以視覺化方式瞭解元素的 electron shell 和其系統核心, 這是由 protons 和 neutrons 所組成。</span><span class="sxs-lookup"><span data-stu-id="e81be-116">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="e81be-117">背景</span><span class="sxs-lookup"><span data-stu-id="e81be-117">Background</span></span>

<span data-ttu-id="e81be-118">在我第一次體驗 HoloLens 之後, 週期性資料表應用程式就是我知道, 我想要在混合現實中進行實驗。</span><span class="sxs-lookup"><span data-stu-id="e81be-118">After I first experienced HoloLens, a periodic table app was an idea I knew that I wanted to experiment with in mixed reality.</span></span> <span data-ttu-id="e81be-119">由於每個元素都有許多以文字顯示的資料點, 因此我認為在3D 空間中探索印刷樣式是很重要的主題。</span><span class="sxs-lookup"><span data-stu-id="e81be-119">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="e81be-120">能夠將元素的 electron 模型視覺化, 是這個專案的另一個有趣的部分。</span><span class="sxs-lookup"><span data-stu-id="e81be-120">Being able to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="e81be-121">設計</span><span class="sxs-lookup"><span data-stu-id="e81be-121">Design</span></span>

<span data-ttu-id="e81be-122">就定期資料表的預設觀點而言, 我想到了三維方塊, 其中包含每個元素的 electron 模型。</span><span class="sxs-lookup"><span data-stu-id="e81be-122">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="e81be-123">每個方塊的表面都是半透明的, 讓使用者能夠大致瞭解元素的磁片區。</span><span class="sxs-lookup"><span data-stu-id="e81be-123">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="e81be-124">有了注視和空中碰, 使用者就可以開啟每個元素的詳細觀點。</span><span class="sxs-lookup"><span data-stu-id="e81be-124">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="e81be-125">為了讓資料表視圖和詳細資料檢視之間的轉換順暢且自然, 我使其類似于在真實生活中開啟的實際互動。</span><span class="sxs-lookup"><span data-stu-id="e81be-125">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="e81be-126">![設計草圖](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="e81be-126">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="e81be-127">*設計草圖*</span><span class="sxs-lookup"><span data-stu-id="e81be-127">*Design sketches*</span></span>

<span data-ttu-id="e81be-128">在詳細資料檢視中, 我想要使用3D 空間中的精美轉譯文字, 將每個元素的資訊視覺化。</span><span class="sxs-lookup"><span data-stu-id="e81be-128">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="e81be-129">動畫 3D electron 模型會顯示在中央區域, 而且可以從不同角度來查看。</span><span class="sxs-lookup"><span data-stu-id="e81be-129">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![互動](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="e81be-131">![@](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="e81be-131">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="e81be-132">*互動原型*</span><span class="sxs-lookup"><span data-stu-id="e81be-132">*Interaction prototypes*</span></span>

<span data-ttu-id="e81be-133">使用者可以藉由使用下表底部的按鈕來變更表面類型-它們可以在平面、圓柱、球面和散佈圖之間切換。</span><span class="sxs-lookup"><span data-stu-id="e81be-133">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="e81be-134">此應用程式中使用的通用控制項和模式</span><span class="sxs-lookup"><span data-stu-id="e81be-134">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="e81be-135">可互動物件 (按鈕)</span><span class="sxs-lookup"><span data-stu-id="e81be-135">Interactable object (button)</span></span>

<span data-ttu-id="e81be-136">[可互動物件](interactable-object.md)是可回應基本 HoloLens 輸入的物件。</span><span class="sxs-lookup"><span data-stu-id="e81be-136">[Interactable object](interactable-object.md) is an object which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="e81be-137">它是以 prefab/腳本的形式提供, 您可以輕鬆地將它套用至任何物件。</span><span class="sxs-lookup"><span data-stu-id="e81be-137">It is provided as a prefab/script which you can easily apply to any object.</span></span> <span data-ttu-id="e81be-138">例如, 您可以在場景中可互動, 並回應像是注視、空中碰、導覽和操作手勢等輸入。</span><span class="sxs-lookup"><span data-stu-id="e81be-138">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation and manipulation gestures.</span></span> [<span data-ttu-id="e81be-139">深入了解</span><span class="sxs-lookup"><span data-stu-id="e81be-139">Learn more</span></span>](interactable-object.md)

![nteractable 物件](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="e81be-141">物件集合</span><span class="sxs-lookup"><span data-stu-id="e81be-141">Object collection</span></span>

<span data-ttu-id="e81be-142">[物件集合](object-collection.md)是一種物件, 可協助您在各種不同的圖形中配置多個物件。</span><span class="sxs-lookup"><span data-stu-id="e81be-142">[Object collection](object-collection.md) is an object which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="e81be-143">它支援平面、圓柱、球面和散佈圖。</span><span class="sxs-lookup"><span data-stu-id="e81be-143">It supports plane, cylinder, sphere and scatter.</span></span> <span data-ttu-id="e81be-144">您可以設定其他屬性, 例如 radius、資料列數目和間距。</span><span class="sxs-lookup"><span data-stu-id="e81be-144">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="e81be-145">深入了解</span><span class="sxs-lookup"><span data-stu-id="e81be-145">Learn more</span></span>](object-collection.md)

![物件集合](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a><span data-ttu-id="e81be-147">Fitbox</span><span class="sxs-lookup"><span data-stu-id="e81be-147">Fitbox</span></span>

<span data-ttu-id="e81be-148">根據預設, 在應用程式啟動時, 會將全息影像放在撥雲見日使用者的位置。</span><span class="sxs-lookup"><span data-stu-id="e81be-148">By default, holograms will be placed in the location where the user is gazing at the moment the application is launched.</span></span> <span data-ttu-id="e81be-149">這有時會導致不想要的結果, 例如將全息影像放在牆後方或在資料表的中間。</span><span class="sxs-lookup"><span data-stu-id="e81be-149">This sometimes leads to unwanted result such as holograms being placed behind a wall or in the middle of a table.</span></span> <span data-ttu-id="e81be-150">Fitbox 可讓使用者使用注視來決定要放置全息的位置。</span><span class="sxs-lookup"><span data-stu-id="e81be-150">A fitbox allows a user to use gaze to determine the location where the hologram will be placed.</span></span> <span data-ttu-id="e81be-151">這是使用簡單的 PNG 影像材質所建立, 您可以使用自己的影像或3D 物件輕鬆地自訂它。</span><span class="sxs-lookup"><span data-stu-id="e81be-151">It is made with a simple PNG image texture which can be easily customized with your own images or 3D objects.</span></span>

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a><span data-ttu-id="e81be-153">技術詳細資料</span><span class="sxs-lookup"><span data-stu-id="e81be-153">Technical details</span></span>

<span data-ttu-id="e81be-154">您可以在[混合現實設計實驗室 GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)上找到適用于 Elements 應用程式的定期資料表的腳本和 prefabs。</span><span class="sxs-lookup"><span data-stu-id="e81be-154">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="application-examples"></a><span data-ttu-id="e81be-155">應用程式範例</span><span class="sxs-lookup"><span data-stu-id="e81be-155">Application examples</span></span>

<span data-ttu-id="e81be-156">以下是您可以利用此專案中的元件來建立的一些概念。</span><span class="sxs-lookup"><span data-stu-id="e81be-156">Here are some ideas for what you could create by leveraging the components in this project.</span></span>

### <a name="stock-data-visualization-app"></a><span data-ttu-id="e81be-157">股票資料視覺效果應用程式</span><span class="sxs-lookup"><span data-stu-id="e81be-157">Stock data visualization app</span></span>

<span data-ttu-id="e81be-158">使用與專案範例的定期資料表相同的控制項和互動模型, 您可以建立可將股票市場資料視覺化的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e81be-158">Using the same controls and interaction model as the Periodic Table of the Elements sample, you could build an app which visualizes stock market data.</span></span> <span data-ttu-id="e81be-159">這個範例會使用物件集合控制項來配置球面圖形中的股票資料。</span><span class="sxs-lookup"><span data-stu-id="e81be-159">This example uses the Object collection control to lay out stock data in a spherical shape.</span></span> <span data-ttu-id="e81be-160">您可以想像一下詳細資料檢視, 其中每個股票的其他資訊可能會以有趣的方式顯示。</span><span class="sxs-lookup"><span data-stu-id="e81be-160">You can imagine a detail view where additional information about each stock could be displayed in an interesting way.</span></span>

![應用程式範例:財務 (1/3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![應用程式範例:財務 (2/3)](images/640px-periodictable-applicationexamples-finance2.jpg)

<span data-ttu-id="e81be-163">![應用程式範例:財務 (3/3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span><span class="sxs-lookup"><span data-stu-id="e81be-163">![Application example: Finance (3 of 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span></span><br>
<span data-ttu-id="e81be-164">*如何在財務應用程式中使用在專案範例應用程式的定期資料表中使用的物件集合範例*</span><span class="sxs-lookup"><span data-stu-id="e81be-164">*An example of how the Object collection used in the Periodic Table of the Elements sample app could be used in a finance app*</span></span>

### <a name="sports-app"></a><span data-ttu-id="e81be-165">運動應用程式</span><span class="sxs-lookup"><span data-stu-id="e81be-165">Sports app</span></span>

<span data-ttu-id="e81be-166">這是使用專案範例應用程式的定期資料表中的物件集合和其他元件來視覺化運動資料的範例。</span><span class="sxs-lookup"><span data-stu-id="e81be-166">This is an example of visualizing sports data using Object collection and other components from the Periodic Table of the Elements sample app.</span></span>

![應用程式範例:運動 (1/3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![應用程式範例:運動 (2/3)](images/640px-periodictable-applicationexamples-sports1.jpg)

<span data-ttu-id="e81be-169">![應用程式範例:運動 (3/3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span><span class="sxs-lookup"><span data-stu-id="e81be-169">![Application example: Sports (3 of 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span></span><br>
<span data-ttu-id="e81be-170">*如何在運動應用程式中使用 appcould 元素範例的定期資料表中所使用的物件集合範例*</span><span class="sxs-lookup"><span data-stu-id="e81be-170">*An example of how the Object collection used in the Periodic Table of the Elements sample appcould be used in a sports app*</span></span>

## <a name="about-the-author"></a><span data-ttu-id="e81be-171">關於作者</span><span class="sxs-lookup"><span data-stu-id="e81be-171">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="e81be-172"><b>盾 Yoon 公園</b></span><span class="sxs-lookup"><span data-stu-id="e81be-172"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="e81be-173">UX 設計工具@Microsoft</span><span class="sxs-lookup"><span data-stu-id="e81be-173">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="e81be-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e81be-174">See also</span></span>

* [<span data-ttu-id="e81be-175">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="e81be-175">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="e81be-176">物件集合</span><span class="sxs-lookup"><span data-stu-id="e81be-176">Object collection</span></span>](object-collection.md)
