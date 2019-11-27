---
title: 什麼是混合實境？
description: 本文會定義混合的事實，並示範簡單的 AR 和 VR 裝置，以及 Windows Mixed Reality 裝置（例如 Microsoft HoloLens 和 Windows Mixed Reality 沉浸式耳機），並配合混合現實頻譜。
author: BrandonBray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: mixed reality，全像，ar，vr，mr，xr，增強的現實，虛擬實境，說明
ms.openlocfilehash: 65588902565ee0c5a1710f823311ccdecc23230e
ms.sourcegitcommit: 83698638b93c5ba77b3ffc399f1706482539f27b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74539564"
---
# <a name="what-is-mixed-reality"></a><span data-ttu-id="0f987-104">什麼是混合實境？</span><span class="sxs-lookup"><span data-stu-id="0f987-104">What is mixed reality?</span></span>

![在 HoloLens 2 上實際操作點和認可](images/02_MixedRealitySlashMixedReality.png)

<span data-ttu-id="0f987-106">混合實境是實體環境與數位世界混合的結果。</span><span class="sxs-lookup"><span data-stu-id="0f987-106">Mixed reality is the result of blending the physical world with the digital world.</span></span> <span data-ttu-id="0f987-107">混合的實境是人類、電腦和環境互動的全新演進，並且解放了以前僅限於我們想像的可能性。</span><span class="sxs-lookup"><span data-stu-id="0f987-107">Mixed reality is the next evolution in human, computer, and environment interaction and unlocks possibilities that before now were restricted to our imaginations.</span></span> <span data-ttu-id="0f987-108">這是藉由電腦視覺、圖形處理能力、顯示器技術和輸入系統的進展而達成的。</span><span class="sxs-lookup"><span data-stu-id="0f987-108">It is made possible by advancements in computer vision, graphical processing power, display technology, and input systems.</span></span> <span data-ttu-id="0f987-109">「*混合現實*」一詞原本是由 Paul Milgram 和 Fumio Kishino 「[混合現實視覺效果的分類法](https://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)」所引進的1994論文。</span><span class="sxs-lookup"><span data-stu-id="0f987-109">The term *mixed reality* was originally introduced in a 1994 paper by Paul Milgram and Fumio Kishino, "[A Taxonomy of Mixed Reality Visual Displays](https://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)."</span></span> <span data-ttu-id="0f987-110">其論文引進了*virtuality continuum*的概念，並著重于如何套用分類法的分類。</span><span class="sxs-lookup"><span data-stu-id="0f987-110">Their paper introduced the concept of the *virtuality continuum*, and focused on how the categorization of taxonomy applied to displays.</span></span> <span data-ttu-id="0f987-111">從那時起，混合現實的應用程式會超出顯示範圍。</span><span class="sxs-lookup"><span data-stu-id="0f987-111">Since then, the application of mixed reality goes beyond displays.</span></span> <span data-ttu-id="0f987-112">它也包含環境輸入、空間音效和位置。</span><span class="sxs-lookup"><span data-stu-id="0f987-112">It also includes environmental input, spatial sound, and location.</span></span>

<span data-ttu-id="0f987-113">![混合的現實頻譜](images/MixedRealitySpectrum-worlds.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f987-113">![The mixed reality spectrum](images/MixedRealitySpectrum-worlds.jpg)</span></span><br>
<span data-ttu-id="0f987-114">*混合現實是將實體世界與數位世界相結合的結果。*</span><span class="sxs-lookup"><span data-stu-id="0f987-114">*Mixed reality is the result of blending the physical world with the digital world.*</span></span>

<br>

---

## <a name="environmental-input-and-perception"></a><span data-ttu-id="0f987-115">環境輸入和認知</span><span class="sxs-lookup"><span data-stu-id="0f987-115">Environmental input and perception</span></span>

<span data-ttu-id="0f987-116">過去幾年來，人類與電腦輸入之間的關聯性已經過充分的探索。</span><span class="sxs-lookup"><span data-stu-id="0f987-116">Over the past several decades, the relationship between human and computer input has been well explored.</span></span> <span data-ttu-id="0f987-117">它甚至已經過廣泛研究的專業領域，稱為*人類電腦互動*或 HCI。</span><span class="sxs-lookup"><span data-stu-id="0f987-117">It even has a widely studied discipline known as *human computer interaction* or HCI.</span></span> <span data-ttu-id="0f987-118">人類輸入會透過各種不同的方式進行，包括鍵盤、滑鼠、觸控、筆墨、語音，甚至是 Kinect 的框架追蹤。</span><span class="sxs-lookup"><span data-stu-id="0f987-118">Human input happens through a variety of means, including keyboards, mice, touch, ink, voice, and even Kinect skeletal tracking.</span></span>

<span data-ttu-id="0f987-119">在感應器和處理方面的改進，是從環境逐漸增加到電腦輸入的新區域。</span><span class="sxs-lookup"><span data-stu-id="0f987-119">Advancements in sensors and processing are giving rise to a new area of computer input from environments.</span></span> <span data-ttu-id="0f987-120">電腦與環境之間的互動是有效的環境理解或*認知*。</span><span class="sxs-lookup"><span data-stu-id="0f987-120">The interaction between computers and environments is effectively environmental understanding or *perception*.</span></span> <span data-ttu-id="0f987-121">因此，Windows 中顯示環境資訊的 API 名稱稱為「[認知 api](https://docs.microsoft.com/uwp/api/Windows.Perception)」。</span><span class="sxs-lookup"><span data-stu-id="0f987-121">Hence the API names in Windows that reveal environmental information are called the [perception APIs](https://docs.microsoft.com/uwp/api/Windows.Perception).</span></span> <span data-ttu-id="0f987-122">環境輸入會在世界中（例如， [head 追蹤](coordinate-systems.md)）、表面和邊界（例如[空間對應](spatial-mapping.md)和[場景理解](scene-understanding.md)）、環境光源、環境音效、物件辨識等專案中，捕捉到人員的位置。和位置。</span><span class="sxs-lookup"><span data-stu-id="0f987-122">Environmental input captures things like a person's position in the world (e.g. [head tracking](coordinate-systems.md)), surfaces and boundaries (e.g. [spatial mapping](spatial-mapping.md) and [scene understanding](scene-understanding.md)), ambient lighting, environmental sound, object recognition, and location.</span></span>

<br>



:::row:::
    :::column:::
        <span data-ttu-id="0f987-123">現在，所有三種**電腦處理、人類輸入和環境輸入**的組合，都能為您創造出真正的混合現實體驗。</span><span class="sxs-lookup"><span data-stu-id="0f987-123">Now, the combination of all three--**computer processing, human input, and environmental input**--sets the opportunity to create true mixed reality experiences.</span></span> <span data-ttu-id="0f987-124">透過實體世界的移動可以轉譯成數位世界中的移動。</span><span class="sxs-lookup"><span data-stu-id="0f987-124">Movement through the physical world can translate to movement in the digital world.</span></span> <span data-ttu-id="0f987-125">實體世界的界限可能會影響數位世界中的應用程式體驗，例如遊戲播放。</span><span class="sxs-lookup"><span data-stu-id="0f987-125">Boundaries in the physical world can influence application experiences, such as game play, in the digital world.</span></span> <span data-ttu-id="0f987-126">如果沒有環境輸入，體驗就無法在實體和數位現實之間混合。</span><span class="sxs-lookup"><span data-stu-id="0f987-126">Without environmental input, experiences cannot blend between physical and digital realities.</span></span><br>
        <br>
        <span data-ttu-id="0f987-127">*影像：電腦、人類和環境之間的互動。*</span><span class="sxs-lookup"><span data-stu-id="0f987-127">*Image: The interactions between between computers, humans and environments.*</span></span>
    :::column-end:::
        :::column:::
       ![顯示電腦、人類和環境之間互動的卞氏圖表](images/mixed-reality-venn-diagram-300px.png)<br> 
    :::column-end:::
:::row-end:::

<br>

---


## <a name="the-mixed-reality-spectrum"></a><span data-ttu-id="0f987-129">混合現實頻譜</span><span class="sxs-lookup"><span data-stu-id="0f987-129">The mixed reality spectrum</span></span>

<span data-ttu-id="0f987-130">因為混合現實會混合實體和數位世界，所以這兩個現實會定義一系列稱為 virtuality continuum 的極座標。</span><span class="sxs-lookup"><span data-stu-id="0f987-130">Since mixed reality blends both physical and digital worlds, these two realities define the polar ends of a spectrum known as the virtuality continuum.</span></span> <span data-ttu-id="0f987-131">為了簡單起見，我們將此稱為「*混合現實」頻譜*。</span><span class="sxs-lookup"><span data-stu-id="0f987-131">For simplicity, we refer to this as the *mixed reality spectrum*.</span></span> <span data-ttu-id="0f987-132">在左側，我們有實際的現實，也就是我們的存在;在右手邊，我們有對應的數位現實。</span><span class="sxs-lookup"><span data-stu-id="0f987-132">On the left-hand side we have physical reality in which we, humans, exist; on the right-hand side we have the corresponding digital reality.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a><span data-ttu-id="0f987-133">增強與虛擬實境的比較</span><span class="sxs-lookup"><span data-stu-id="0f987-133">Augmented vs. virtual reality</span></span>

<span data-ttu-id="0f987-134">現今市場上大部分的行動電話幾乎都沒有環境理解功能。</span><span class="sxs-lookup"><span data-stu-id="0f987-134">Most mobile phones on the market today have little to no environmental understanding capabilities.</span></span> <span data-ttu-id="0f987-135">因此，他們所提供的體驗無法在實體和數位現實之間混合。</span><span class="sxs-lookup"><span data-stu-id="0f987-135">Thus the experiences they offer cannot mix between physical and digital realities.</span></span> <span data-ttu-id="0f987-136">在實體世界的影片串流上重迭圖形的體驗，會有更豐富的*現實*。</span><span class="sxs-lookup"><span data-stu-id="0f987-136">The experiences that overlay graphics on video streams of the physical world are *augmented reality*.</span></span> <span data-ttu-id="0f987-137">遮蔽您的觀點來呈現數位體驗的經驗，就是*虛擬實境*。</span><span class="sxs-lookup"><span data-stu-id="0f987-137">The experiences that occlude your view to present a digital experience are *virtual reality*.</span></span> <span data-ttu-id="0f987-138">如您所見，在這兩個極端之間啟用的經驗，是*混合現實*的：</span><span class="sxs-lookup"><span data-stu-id="0f987-138">As you can see, the experiences enabled between these two extremes is *mixed reality*:</span></span>
* <span data-ttu-id="0f987-139">從實體世界開始，將數位物件（例如全息的影像）放在真正的處。</span><span class="sxs-lookup"><span data-stu-id="0f987-139">Starting with the physical world, placing a digital object, such as a hologram, as if it was really there.</span></span>
* <span data-ttu-id="0f987-140">從實體世界開始，另一個人的數位標記法--[頭像]--顯示離開便箋時的位置。</span><span class="sxs-lookup"><span data-stu-id="0f987-140">Starting with the physical world, a digital representation of another person--an avatar--shows the location where they were standing when leaving notes.</span></span> <span data-ttu-id="0f987-141">換句話說，在不同時間點表示非同步共同作業的經驗。</span><span class="sxs-lookup"><span data-stu-id="0f987-141">In other words, experiences that represent asynchronous collaboration at different points in time.</span></span>
* <span data-ttu-id="0f987-142">從數位世界開始，實體世界（例如牆和傢俱）的實體界限會以數位方式出現在體驗中，以協助使用者避免實體物件。</span><span class="sxs-lookup"><span data-stu-id="0f987-142">Starting with a digital world, physical boundaries from the physical world, such as walls and furniture, appear digitally within the experience to help users avoid physical objects.</span></span>


<br>

<span data-ttu-id="0f987-143">![混合的現實頻譜](images/MixedRealitySpectrum.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f987-143">![The mixed reality spectrum](images/MixedRealitySpectrum.jpg)</span></span><br>
<span data-ttu-id="0f987-144">*混合現實頻譜*</span><span class="sxs-lookup"><span data-stu-id="0f987-144">*The mixed reality spectrum*</span></span>

<br>

<span data-ttu-id="0f987-145">現今提供的大部分增強的現實和虛擬實境產品，都代表此頻譜的一小部分。</span><span class="sxs-lookup"><span data-stu-id="0f987-145">Most augmented reality and virtual reality offerings available today represent a very small part of this spectrum.</span></span> <span data-ttu-id="0f987-146">不過，它們也是較大混合現實頻譜的子集。</span><span class="sxs-lookup"><span data-stu-id="0f987-146">They are, however, subsets of the larger mixed reality spectrum.</span></span> <span data-ttu-id="0f987-147">Windows 10 以整個頻譜為基礎，並可讓人、地點和事物的數位代表與真實世界混合。</span><span class="sxs-lookup"><span data-stu-id="0f987-147">Windows 10 is built with the entire spectrum in mind, and allows blending digital representations of people, places, and things with the real world.</span></span>




## <a name="devices-and-experiences"></a><span data-ttu-id="0f987-148">裝置和體驗</span><span class="sxs-lookup"><span data-stu-id="0f987-148">Devices and experiences</span></span>


<span data-ttu-id="0f987-149">有兩種主要的裝置類型可提供 Windows Mixed Reality 體驗：</span><span class="sxs-lookup"><span data-stu-id="0f987-149">There are two main types of devices that deliver Windows Mixed Reality experiences:</span></span>
1. <span data-ttu-id="0f987-150">**全像攝影裝置。**</span><span class="sxs-lookup"><span data-stu-id="0f987-150">**Holographic devices.**</span></span> <span data-ttu-id="0f987-151">這些特性是由裝置將數位內容放在真實世界中的功能來表示，就像真正的一樣。</span><span class="sxs-lookup"><span data-stu-id="0f987-151">These are characterized by the device's ability to place digital content in the real world as if it were really there.</span></span>
2. <span data-ttu-id="0f987-152">**沉浸式裝置。**</span><span class="sxs-lookup"><span data-stu-id="0f987-152">**Immersive devices.**</span></span> <span data-ttu-id="0f987-153">這些特性是由裝置建立「目前狀態」的能力所組成--隱藏實體世界，並以數位體驗取代。</span><span class="sxs-lookup"><span data-stu-id="0f987-153">These are characterized by the device's ability to create a sense of "presence"--hiding the physical world, and replacing it with a digital experience.</span></span>

<table>
<tr>
<th width="20%"> <span data-ttu-id="0f987-154">特性</span><span class="sxs-lookup"><span data-stu-id="0f987-154">Characteristic</span></span></th><th width="40%"> <span data-ttu-id="0f987-155">全像攝影裝置</span><span class="sxs-lookup"><span data-stu-id="0f987-155">Holographic Devices</span></span></th><th width="40%"> <span data-ttu-id="0f987-156">沉浸式裝置</span><span class="sxs-lookup"><span data-stu-id="0f987-156">Immersive Devices</span></span></th>
</tr><tr>
<td> <span data-ttu-id="0f987-157">範例裝置</span><span class="sxs-lookup"><span data-stu-id="0f987-157">Example Device</span></span></td><td> <span data-ttu-id="0f987-158">Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="0f987-158">Microsoft HoloLens</span></span><br /> <img alt="Microsoft HoloLens image" width="300" height="169" src="images/mshololens-hero1-whitbg-rgb-300px.png" /></td><td> <span data-ttu-id="0f987-159">Acer Windows Mixed Reality 開發版</span><span class="sxs-lookup"><span data-stu-id="0f987-159">Acer Windows Mixed Reality Development Edition</span></span><br /> <img alt="Acer Windows Mixed Reality Development Edition image" width="300" height="169" src="images/acer-windows-mixed-reality-development-edition-headset-300px.jpg" /></td>
</tr><tr>
<td> <span data-ttu-id="0f987-160">顯示器</span><span class="sxs-lookup"><span data-stu-id="0f987-160">Display</span></span></td><td> <span data-ttu-id="0f987-161"><i>查看顯示。</i></span><span class="sxs-lookup"><span data-stu-id="0f987-161"><i>See-through display.</i></span></span> <span data-ttu-id="0f987-162">可讓使用者在戴頭戴式裝置時查看實體環境。</span><span class="sxs-lookup"><span data-stu-id="0f987-162">Allows user to see the physical environment while wearing the headset.</span></span></td><td> <span data-ttu-id="0f987-163"><i>不透明的顯示。</i></span><span class="sxs-lookup"><span data-stu-id="0f987-163"><i>Opaque display.</i></span></span> <span data-ttu-id="0f987-164">在戴頭戴式裝置時封鎖實體環境。</span><span class="sxs-lookup"><span data-stu-id="0f987-164">Blocks out the physical environment while wearing the headset.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="0f987-165">引起</span><span class="sxs-lookup"><span data-stu-id="0f987-165">Movement</span></span></td><td> <span data-ttu-id="0f987-166">完整的六度自由移動，包括旋轉和轉譯。</span><span class="sxs-lookup"><span data-stu-id="0f987-166">Full six-degrees-of-freedom movement, both rotation and translation.</span></span></td><td> <span data-ttu-id="0f987-167">完整的六度自由移動，包括旋轉和轉譯。</span><span class="sxs-lookup"><span data-stu-id="0f987-167">Full six-degrees-of-freedom movement, both rotation and translation.</span></span></td>
</tr>
</table>

<span data-ttu-id="0f987-168">請注意，無論裝置是連線到其他電腦或行動網卡到另一部電腦（透過 USB 纜線或 Wi-fi）或是獨立的（非網路共用），都不會反映裝置是否為全像攝影或沉浸式。</span><span class="sxs-lookup"><span data-stu-id="0f987-168">Note, whether a device is connected to or tethered to a separate PC (via USB cable or Wi-Fi) or self-contained (untethered) does not reflect whether a device is holographic or immersive.</span></span> <span data-ttu-id="0f987-169">當然，改善行動性的功能會導致更好的體驗，而且全像攝影和沉浸式裝置都可能是行動網卡或非網路共用。</span><span class="sxs-lookup"><span data-stu-id="0f987-169">Certainly, features that improve mobility lead to better experiences, and both holographic and immersive devices could be tethered or untethered.</span></span>


<span data-ttu-id="0f987-170">技術進步是已啟用混合現實體驗的功能。</span><span class="sxs-lookup"><span data-stu-id="0f987-170">Technological advancement is what has enabled mixed reality experiences.</span></span> <span data-ttu-id="0f987-171">目前沒有任何可在整個頻譜中執行體驗的裝置。</span><span class="sxs-lookup"><span data-stu-id="0f987-171">There are no devices today that can run experiences across the entire spectrum.</span></span> <span data-ttu-id="0f987-172">不過，Windows 10 為裝置製造商和開發人員提供通用的混合現實平臺。</span><span class="sxs-lookup"><span data-stu-id="0f987-172">However, Windows 10 provides a common mixed reality platform for both device manufacturers and developers.</span></span> <span data-ttu-id="0f987-173">現今的裝置可以支援混合現實頻譜內的特定範圍。</span><span class="sxs-lookup"><span data-stu-id="0f987-173">Devices today can support a specific range within the mixed reality spectrum.</span></span> <span data-ttu-id="0f987-174">經過一段時間後，新的裝置將會擴充該範圍。</span><span class="sxs-lookup"><span data-stu-id="0f987-174">Over time, new devices will expand that range.</span></span> <span data-ttu-id="0f987-175">未來，全像攝影的裝置會變得更沉浸，而沉浸式裝置會變得更好。</span><span class="sxs-lookup"><span data-stu-id="0f987-175">In the future, holographic devices will become more immersive, and immersive devices will become more holographic.</span></span>

<br>

<span data-ttu-id="0f987-176">混合現實頻譜中的 ![裝置類型](images/MixedRealitySpectrum-devices.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f987-176">![Device types in the mixed reality spectrum](images/MixedRealitySpectrum-devices.jpg)</span></span><br>
<span data-ttu-id="0f987-177">*其中的裝置存在於混合現實頻譜上*</span><span class="sxs-lookup"><span data-stu-id="0f987-177">*Where devices exist on the mixed reality spectrum*</span></span>

<span data-ttu-id="0f987-178">通常，最好考慮應用程式或遊戲開發人員想要建立哪種類型的經驗。</span><span class="sxs-lookup"><span data-stu-id="0f987-178">Often, it is best to think what type of experience an application or game developer wants to create.</span></span> <span data-ttu-id="0f987-179">這些體驗通常會以特定點或元件為目標。</span><span class="sxs-lookup"><span data-stu-id="0f987-179">The experiences will typically target a specific point or part on the spectrum.</span></span> <span data-ttu-id="0f987-180">然後，開發人員應該考慮他們想要作為目標的裝置功能。</span><span class="sxs-lookup"><span data-stu-id="0f987-180">Then, developers should consider the capabilities of devices they want to target.</span></span> <span data-ttu-id="0f987-181">比方說，依賴實體世界的經驗在 HoloLens 上的效果最佳。</span><span class="sxs-lookup"><span data-stu-id="0f987-181">For example, experiences that rely on the physical world will run best on HoloLens.</span></span>
* <span data-ttu-id="0f987-182">**朝左邊（接近實體現實）。**</span><span class="sxs-lookup"><span data-stu-id="0f987-182">**Towards the left (near physical reality).**</span></span> <span data-ttu-id="0f987-183">使用者仍然存在於其實體環境中，而且永遠不會相信他們已離開該環境。</span><span class="sxs-lookup"><span data-stu-id="0f987-183">Users remain present in their physical environment and are never made to believe they have left that environment.</span></span>
* <span data-ttu-id="0f987-184">**中間（完全混合的事實）。**</span><span class="sxs-lookup"><span data-stu-id="0f987-184">**In the middle (fully mixed reality).**</span></span> <span data-ttu-id="0f987-185">這些體驗 blend 了真實世界與數位世界。</span><span class="sxs-lookup"><span data-stu-id="0f987-185">These experiences blend the real world and the digital world.</span></span> <span data-ttu-id="0f987-186">看過電影[Jumanji](https://en.wikipedia.org/wiki/Jumanji)的觀看者，可以協調出故事所在的房屋實體結構與蛙鳴環境的混合方式。</span><span class="sxs-lookup"><span data-stu-id="0f987-186">Viewers who have seen the movie [Jumanji](https://en.wikipedia.org/wiki/Jumanji) can reconcile how the physical structure of the house where the story took place was blended with a jungle environment.</span></span>
* <span data-ttu-id="0f987-187">**向右（接近數位現實）。**</span><span class="sxs-lookup"><span data-stu-id="0f987-187">**Towards the right (near digital reality).**</span></span> <span data-ttu-id="0f987-188">使用者會遇到完全數位的環境，而且不會察覺實體環境中發生的情況。</span><span class="sxs-lookup"><span data-stu-id="0f987-188">Users experience a completely digital environment, and are unaware of what occurs in the physical environment around them.</span></span>


## <a name="see-also"></a><span data-ttu-id="0f987-189">請參閱</span><span class="sxs-lookup"><span data-stu-id="0f987-189">See also</span></span>

* [<span data-ttu-id="0f987-190">什麼是全像投影？</span><span class="sxs-lookup"><span data-stu-id="0f987-190">What is a hologram?</span></span>](hologram.md)
* [<span data-ttu-id="0f987-191">瞭解混合現實的基本概念</span><span class="sxs-lookup"><span data-stu-id="0f987-191">Understand the basics of mixed reality</span></span>](index.md#understand-the-basics)
* [<span data-ttu-id="0f987-192">開始建立和原型設計</span><span class="sxs-lookup"><span data-stu-id="0f987-192">Start creating and prototyping</span></span>](design.md)
* [<span data-ttu-id="0f987-193">了解工具和架構</span><span class="sxs-lookup"><span data-stu-id="0f987-193">Learn the tools and architecture</span></span>](development.md)

