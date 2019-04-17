---
title: 定期的資料表的項目
description: 定期資料表項目是開放原始碼的範例應用程式從 Microsoft 的混合實境設計實驗室中，您可以了解如何使用各種使用的物件集合的介面型別來配置在 3D 空間中物件的陣列。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，設計，範例應用程式，控制項
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596692"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="1de4a-104">定期的資料表的項目</span><span class="sxs-lookup"><span data-stu-id="1de4a-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="1de4a-105">這篇文章討論探勘的範例，我們已在中建立[混合實境設計實驗室](https://github.com/Microsoft/MRDesignLabs_Unity)，我們分享我們所獲得的經驗相關的位置和建議混合實境應用程式開發。</span><span class="sxs-lookup"><span data-stu-id="1de4a-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="1de4a-106">當我們新的探索，就會持續改進我們的設計相關的文章和程式碼。</span><span class="sxs-lookup"><span data-stu-id="1de4a-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="1de4a-107">[項目的周期資料表](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)是 Microsoft 的混合實境設計實驗室一個開放原始碼的範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="1de4a-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is a open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="1de4a-108">與此專案中，您可以了解如何使用各種使用的介面型別來配置在 3D 空間中物件的陣列**[物件集合](object-collection.md)**。</span><span class="sxs-lookup"><span data-stu-id="1de4a-108">With this project, you can learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](object-collection.md)**.</span></span> <span data-ttu-id="1de4a-109">也了解如何建立可互動回應 HoloLens 的標準輸入的物件。</span><span class="sxs-lookup"><span data-stu-id="1de4a-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="1de4a-110">您可以使用此專案的元件建立您自己也就是混合實境應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="1de4a-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![時段的資料表的項目應用程式](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a><span data-ttu-id="1de4a-112">關於應用程式</span><span class="sxs-lookup"><span data-stu-id="1de4a-112">About the app</span></span>

<span data-ttu-id="1de4a-113">化學的項目和其屬性，在 3D 空間中的每個項目的周期資料表以視覺化方式呈現。</span><span class="sxs-lookup"><span data-stu-id="1de4a-113">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="1de4a-114">它會合併 HoloLens 基本互動，例如視線和空中點選。</span><span class="sxs-lookup"><span data-stu-id="1de4a-114">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="1de4a-115">使用者可以了解動畫效果的 3D 模型的項目。</span><span class="sxs-lookup"><span data-stu-id="1de4a-115">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="1de4a-116">它們以視覺化方式可以了解的項目 electron 殼層和其核心-質子與 neutrons 所組成。</span><span class="sxs-lookup"><span data-stu-id="1de4a-116">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="1de4a-117">背景</span><span class="sxs-lookup"><span data-stu-id="1de4a-117">Background</span></span>

<span data-ttu-id="1de4a-118">我第一次發生 HoloLens 之後，定期資料表 」 應用程式是我知道我想要在混合實境中進行實驗與了解。</span><span class="sxs-lookup"><span data-stu-id="1de4a-118">After I first experienced HoloLens, a periodic table app was an idea I knew that I wanted to experiment with in mixed reality.</span></span> <span data-ttu-id="1de4a-119">因為每個項目會以文字顯示的許多資料點，我認為它是絕佳的主題來探索在 3D 空間中的印刷樣式組合。</span><span class="sxs-lookup"><span data-stu-id="1de4a-119">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="1de4a-120">正在將視覺化項目的 electron 模型是此專案的另一個有趣的部分。</span><span class="sxs-lookup"><span data-stu-id="1de4a-120">Being able to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="1de4a-121">設計</span><span class="sxs-lookup"><span data-stu-id="1de4a-121">Design</span></span>

<span data-ttu-id="1de4a-122">針對定期資料表的預設檢視，我想像的情況會包含每個元素的 electron 模型的立體方塊。</span><span class="sxs-lookup"><span data-stu-id="1de4a-122">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="1de4a-123">每個方塊的介面是半透明，讓使用者無法取得項目的磁碟區的約略的構念。</span><span class="sxs-lookup"><span data-stu-id="1de4a-123">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="1de4a-124">視線和空中點選一下，使用者可以開啟每個項目的詳細檢視。</span><span class="sxs-lookup"><span data-stu-id="1de4a-124">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="1de4a-125">若要讓資料表檢視和詳細資料檢視之間的轉換，平滑且自然，我進行類似的方塊，在現實生活中開啟實體互動。</span><span class="sxs-lookup"><span data-stu-id="1de4a-125">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="1de4a-126">![設計草圖](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="1de4a-126">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="1de4a-127">*設計草圖*</span><span class="sxs-lookup"><span data-stu-id="1de4a-127">*Design sketches*</span></span>

<span data-ttu-id="1de4a-128">在詳細資料檢視中，我想要視覺化具有完美地呈現的文字在 3D 空間中的每個項目資訊。</span><span class="sxs-lookup"><span data-stu-id="1de4a-128">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="1de4a-129">動畫的 3D electron 模型會顯示在中心區域，並可從不同角度檢視。</span><span class="sxs-lookup"><span data-stu-id="1de4a-129">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![互動](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="1de4a-131">![Prototypes](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="1de4a-131">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="1de4a-132">*互動原型*</span><span class="sxs-lookup"><span data-stu-id="1de4a-132">*Interaction prototypes*</span></span>

<span data-ttu-id="1de4a-133">使用者可以空中點選底部的資料表上的按鈕變更介面的類型-它們可以平面、 cylinder、 球體和散佈圖之間切換。</span><span class="sxs-lookup"><span data-stu-id="1de4a-133">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="1de4a-134">常見控制項和使用此應用程式中的模式</span><span class="sxs-lookup"><span data-stu-id="1de4a-134">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="1de4a-135">可互動的物件 （按鈕）</span><span class="sxs-lookup"><span data-stu-id="1de4a-135">Interactable object (button)</span></span>

<span data-ttu-id="1de4a-136">[可互動的物件](interactable-object.md)是基本的 HoloLens 輸入可以回應的物件。</span><span class="sxs-lookup"><span data-stu-id="1de4a-136">[Interactable object](interactable-object.md) is an object which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="1de4a-137">它可做為 prefab/指令碼可以輕鬆地套用至任何物件。</span><span class="sxs-lookup"><span data-stu-id="1de4a-137">It is provided as a prefab/script which you can easily apply to any object.</span></span> <span data-ttu-id="1de4a-138">比方說，您可以讓場景的咖啡 cup 互動，並回應的輸入，例如視線、 空中點選瀏覽和操作的筆勢。</span><span class="sxs-lookup"><span data-stu-id="1de4a-138">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation and manipulation gestures.</span></span> [<span data-ttu-id="1de4a-139">深入了解</span><span class="sxs-lookup"><span data-stu-id="1de4a-139">Learn more</span></span>](interactable-object.md)

![nteractable 物件](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="1de4a-141">物件集合</span><span class="sxs-lookup"><span data-stu-id="1de4a-141">Object collection</span></span>

<span data-ttu-id="1de4a-142">[物件集合](object-collection.md)是一種物件，可協助您配置不同圖形中的多個物件。</span><span class="sxs-lookup"><span data-stu-id="1de4a-142">[Object collection](object-collection.md) is an object which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="1de4a-143">它支援平面、 cylinder、 球體和散佈圖。</span><span class="sxs-lookup"><span data-stu-id="1de4a-143">It supports plane, cylinder, sphere and scatter.</span></span> <span data-ttu-id="1de4a-144">您可以設定其他屬性，例如半徑、 資料列數和間距。</span><span class="sxs-lookup"><span data-stu-id="1de4a-144">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="1de4a-145">深入了解</span><span class="sxs-lookup"><span data-stu-id="1de4a-145">Learn more</span></span>](object-collection.md)

![物件集合](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a><span data-ttu-id="1de4a-147">Fitbox</span><span class="sxs-lookup"><span data-stu-id="1de4a-147">Fitbox</span></span>

<span data-ttu-id="1de4a-148">根據預設，全像投影會置於 gazing 使用者的所在位置目前啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="1de4a-148">By default, holograms will be placed in the location where the user is gazing at the moment the application is launched.</span></span> <span data-ttu-id="1de4a-149">這有時會導致不想要的結果，例如背後牆或中間的資料表置入全像投影。</span><span class="sxs-lookup"><span data-stu-id="1de4a-149">This sometimes leads to unwanted result such as holograms being placed behind a wall or in the middle of a table.</span></span> <span data-ttu-id="1de4a-150">Fitbox 可讓使用者使用視線判斷全像放置的位置。</span><span class="sxs-lookup"><span data-stu-id="1de4a-150">A fitbox allows a user to use gaze to determine the location where the hologram will be placed.</span></span> <span data-ttu-id="1de4a-151">它會使用簡單的 PNG 影像材質可輕鬆地自訂您自己的映像或 3D 物件。</span><span class="sxs-lookup"><span data-stu-id="1de4a-151">It is made with a simple PNG image texture which can be easily customized with your own images or 3D objects.</span></span>

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a><span data-ttu-id="1de4a-153">技術詳細資料</span><span class="sxs-lookup"><span data-stu-id="1de4a-153">Technical details</span></span>

<span data-ttu-id="1de4a-154">您可以找到指令碼和 prefabs 定期資料表項目應用程式[混合實境設計 Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)。</span><span class="sxs-lookup"><span data-stu-id="1de4a-154">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="application-examples"></a><span data-ttu-id="1de4a-155">應用程式範例</span><span class="sxs-lookup"><span data-stu-id="1de4a-155">Application examples</span></span>

<span data-ttu-id="1de4a-156">以下是一些您可以利用此專案中的元件建立的想法。</span><span class="sxs-lookup"><span data-stu-id="1de4a-156">Here are some ideas for what you could create by leveraging the components in this project.</span></span>

### <a name="stock-data-visualization-app"></a><span data-ttu-id="1de4a-157">內建的資料視覺效果應用程式</span><span class="sxs-lookup"><span data-stu-id="1de4a-157">Stock data visualization app</span></span>

<span data-ttu-id="1de4a-158">您可以使用相同的控制項和互動模型做為定期資料表的項目範例，來建置應用程式以視覺化方式顯示股票市場資料。</span><span class="sxs-lookup"><span data-stu-id="1de4a-158">Using the same controls and interaction model as the Periodic Table of the Elements sample, you could build an app which visualizes stock market data.</span></span> <span data-ttu-id="1de4a-159">此範例會使用物件集合的控制項來配置更低的球面的圖形中的內建資料。</span><span class="sxs-lookup"><span data-stu-id="1de4a-159">This example uses the Object collection control to lay out stock data in a spherical shape.</span></span> <span data-ttu-id="1de4a-160">您可以想像，無法顯示的每個股票的其他資訊以有趣的方式的詳細資料檢視。</span><span class="sxs-lookup"><span data-stu-id="1de4a-160">You can imagine a detail view where additional information about each stock could be displayed in an interesting way.</span></span>

![應用程式範例：財務 (3 之 1)](images/640px-periodictable-applicationexamples-finance1.jpg)

![應用程式範例：財務 (3 之 2)](images/640px-periodictable-applicationexamples-finance2.jpg)

<span data-ttu-id="1de4a-163">![應用程式範例：財務 (3 之 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span><span class="sxs-lookup"><span data-stu-id="1de4a-163">![Application example: Finance (3 of 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span></span><br>
<span data-ttu-id="1de4a-164">*如何定期資料表的項目範例應用程式中使用的物件集合無法使用的財務應用程式中的範例*</span><span class="sxs-lookup"><span data-stu-id="1de4a-164">*An example of how the Object collection used in the Periodic Table of the Elements sample app could be used in a finance app*</span></span>

### <a name="sports-app"></a><span data-ttu-id="1de4a-165">運動應用程式</span><span class="sxs-lookup"><span data-stu-id="1de4a-165">Sports app</span></span>

<span data-ttu-id="1de4a-166">這是視覺化使用物件集合和項目範例應用程式定期從其他元件的運動資料的範例。</span><span class="sxs-lookup"><span data-stu-id="1de4a-166">This is an example of visualizing sports data using Object collection and other components from the Periodic Table of the Elements sample app.</span></span>

![應用程式範例：運動 (3 之 1)](images/640px-periodictable-applicationexamples-sports0.jpg)

![應用程式範例：運動 (3 之 2)](images/640px-periodictable-applicationexamples-sports1.jpg)

<span data-ttu-id="1de4a-169">![應用程式範例：運動 (3 之 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span><span class="sxs-lookup"><span data-stu-id="1de4a-169">![Application example: Sports (3 of 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span></span><br>
<span data-ttu-id="1de4a-170">*運動應用程式中使用的物件集合中的項目範例 appcould 定期資料表的使用方式範例*</span><span class="sxs-lookup"><span data-stu-id="1de4a-170">*An example of how the Object collection used in the Periodic Table of the Elements sample appcould be used in a sports app*</span></span>

## <a name="about-the-author"></a><span data-ttu-id="1de4a-171">關於作者</span><span class="sxs-lookup"><span data-stu-id="1de4a-171">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="1de4a-172"><b>盾 Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="1de4a-172"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="1de4a-173">UX 設計工具 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="1de4a-173">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="1de4a-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1de4a-174">See also</span></span>

* [<span data-ttu-id="1de4a-175">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="1de4a-175">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="1de4a-176">物件集合</span><span class="sxs-lookup"><span data-stu-id="1de4a-176">Object collection</span></span>](object-collection.md)
