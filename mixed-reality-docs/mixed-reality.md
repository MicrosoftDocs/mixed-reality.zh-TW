---
title: 什麼是混合實境？
description: 本文定義混合實境，並示範混合實境頻譜搭配簡單的 AR 和 VR 裝置以及 Windows Mixed Reality 裝置 (例如 Microsoft HoloLens 和 Windows Mixed Reality 沉浸式頭戴裝置)。
author: brandonbray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: 混合實境, 全像攝影, ar, vr, mr, xr, 擴增實境, 虛擬實境, 說明
ms.localizationpriority: high
ms.openlocfilehash: 541752ef32149f64f9b85616883c284b33bb8fed
ms.sourcegitcommit: 8daefb763d1f23fe02b95b766b00b373f04c5c2d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2020
ms.locfileid: "86447904"
---
# <a name="what-is-mixed-reality"></a><span data-ttu-id="08313-104">什麼是混合實境？</span><span class="sxs-lookup"><span data-stu-id="08313-104">What is mixed reality?</span></span>

![在 HoloLens 2 上手部指向和行動](images/02_MixedRealitySlashMixedReality.png)

<span data-ttu-id="08313-106">混合實境是實體環境與數位世界混合的結果。</span><span class="sxs-lookup"><span data-stu-id="08313-106">Mixed reality is the result of blending the physical world with the digital world.</span></span> <span data-ttu-id="08313-107">混合的實境是人類、電腦和環境互動的全新演進，並且解放了以前僅限於我們想像的可能性。</span><span class="sxs-lookup"><span data-stu-id="08313-107">Mixed reality is the next evolution in human, computer, and environment interaction and unlocks possibilities that before now were restricted to our imaginations.</span></span> <span data-ttu-id="08313-108">這是藉由提升電腦視覺、圖形處理能力、顯示器技術和輸入系統所達成。</span><span class="sxs-lookup"><span data-stu-id="08313-108">It is made possible by advancements in computer vision, graphical processing power, display technology, and input systems.</span></span> <span data-ttu-id="08313-109">「混合實境」  一詞最初是由 Paul Milgram 和 Fumio Kishino 在 1994 年的論文《[混合實境視覺顯示器分類法 (A Taxonomy of Mixed Reality Visual Displays)](https://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)》中提出。</span><span class="sxs-lookup"><span data-stu-id="08313-109">The term *mixed reality* was originally introduced in a 1994 paper by Paul Milgram and Fumio Kishino, "[A Taxonomy of Mixed Reality Visual Displays](https://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)."</span></span> <span data-ttu-id="08313-110">他們的論文提出 *Virtuality Continuum* 的概念，並著重於分類法分類套用至顯示器的方式。</span><span class="sxs-lookup"><span data-stu-id="08313-110">Their paper introduced the concept of the *virtuality continuum*, and focused on how the categorization of taxonomy applied to displays.</span></span> <span data-ttu-id="08313-111">從那時起，混合實境便不只應用於顯示器。</span><span class="sxs-lookup"><span data-stu-id="08313-111">Since then, the application of mixed reality goes beyond displays.</span></span> <span data-ttu-id="08313-112">還包含環境輸入、空間音效和位置。</span><span class="sxs-lookup"><span data-stu-id="08313-112">It also includes environmental input, spatial sound, and location.</span></span>

<span data-ttu-id="08313-113">![混合實境頻譜](images/mixedrealityspectrum-worlds.png)</span><span class="sxs-lookup"><span data-stu-id="08313-113">![The mixed reality spectrum](images/mixedrealityspectrum-worlds.png)</span></span><br>
<span data-ttu-id="08313-114">*影像：混合實境是實體環境與數位世界混合的結果。*</span><span class="sxs-lookup"><span data-stu-id="08313-114">*Image: Mixed reality is the result of blending the physical world with the digital world.*</span></span>

<br>

---

## <a name="environmental-input-and-perception"></a><span data-ttu-id="08313-115">環境輸入和認知</span><span class="sxs-lookup"><span data-stu-id="08313-115">Environmental input and perception</span></span>

<span data-ttu-id="08313-116">過去數十年來，已充分探索人類與電腦輸入之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="08313-116">Over the past several decades, the relationship between human and computer input has been well explored.</span></span> <span data-ttu-id="08313-117">甚至還有一個廣為研究的專業領域，稱為「人機互動」  或 HCI。</span><span class="sxs-lookup"><span data-stu-id="08313-117">It even has a widely studied discipline known as *human computer interaction* or HCI.</span></span> <span data-ttu-id="08313-118">人類輸入會透過各種不同的方式進行，包括鍵盤、滑鼠、觸控、筆跡、語音，甚至是 Kinect 的框架追蹤。</span><span class="sxs-lookup"><span data-stu-id="08313-118">Human input happens through a variety of means, including keyboards, mice, touch, ink, voice, and even Kinect skeletal tracking.</span></span>

<span data-ttu-id="08313-119">在感應器和處理方面的提升，逐漸使環境中的電腦輸入形成新的區域。</span><span class="sxs-lookup"><span data-stu-id="08313-119">Advancements in sensors and processing are giving rise to a new area of computer input from environments.</span></span> <span data-ttu-id="08313-120">電腦與環境之間的互動是有效的環境理解或「感知」  。</span><span class="sxs-lookup"><span data-stu-id="08313-120">The interaction between computers and environments is effectively environmental understanding or *perception*.</span></span> <span data-ttu-id="08313-121">因此，Windows 中顯示環境資訊的 API 名稱即稱為「[認知 API」](https://docs.microsoft.com/uwp/api/Windows.Perception)。</span><span class="sxs-lookup"><span data-stu-id="08313-121">Hence the API names in Windows that reveal environmental information are called the [perception APIs](https://docs.microsoft.com/uwp/api/Windows.Perception).</span></span> <span data-ttu-id="08313-122">環境輸入會擷取諸多事物，像是使用者所處的位置 (例如[人頭追蹤](coordinate-systems.md))、表面和邊界 (例如[空間對應](spatial-mapping.md)和[場景理解](scene-understanding.md))、環境光源、環境音效、物件辨識和位置。</span><span class="sxs-lookup"><span data-stu-id="08313-122">Environmental input captures things like a person's position in the world (e.g. [head tracking](coordinate-systems.md)), surfaces and boundaries (e.g. [spatial mapping](spatial-mapping.md) and [scene understanding](scene-understanding.md)), ambient lighting, environmental sound, object recognition, and location.</span></span>

<br>

<span data-ttu-id="08313-123">![顯示電腦、人類與環境之間互動的卞氏圖表](images/mixed-reality-venn-diagram-300px.png)</span><span class="sxs-lookup"><span data-stu-id="08313-123">![Venn diagram showing interactions between computers, humans and environments](images/mixed-reality-venn-diagram-300px.png)</span></span><br><span data-ttu-id="08313-124"> \
*影像：電腦、人類與環境之間的互動。*</span><span class="sxs-lookup"><span data-stu-id="08313-124"> \
*Image: The interactions between between computers, humans and environments.*</span></span>

<br>

<span data-ttu-id="08313-125">現在，**電腦處理、人類輸入和環境輸入**這三個的組合，樹立了建立真正混合實境體驗的機會。</span><span class="sxs-lookup"><span data-stu-id="08313-125">Now, the combination of all three--**computer processing, human input, and environmental input**--sets the opportunity to create true mixed reality experiences.</span></span> <span data-ttu-id="08313-126">實體世界中的移動可以轉譯成數位世界中的移動。</span><span class="sxs-lookup"><span data-stu-id="08313-126">Movement through the physical world can translate to movement in the digital world.</span></span> <span data-ttu-id="08313-127">實體世界的界限可能會影響數位世界中的應用程式體驗，例如遊戲進行。</span><span class="sxs-lookup"><span data-stu-id="08313-127">Boundaries in the physical world can influence application experiences, such as game play, in the digital world.</span></span> <span data-ttu-id="08313-128">如果沒有環境輸入，體驗就無法混合實體與數位實境。</span><span class="sxs-lookup"><span data-stu-id="08313-128">Without environmental input, experiences cannot blend between physical and digital realities.</span></span><br>

<br>

---


## <a name="the-mixed-reality-spectrum"></a><span data-ttu-id="08313-129">混合實境頻譜</span><span class="sxs-lookup"><span data-stu-id="08313-129">The mixed reality spectrum</span></span>

<span data-ttu-id="08313-130">因為混合實境會混合實體和數位世界，這兩個實境就定義了頻譜的兩極，稱為 Virtuality Continuum。</span><span class="sxs-lookup"><span data-stu-id="08313-130">Since mixed reality blends both physical and digital worlds, these two realities define the polar ends of a spectrum known as the virtuality continuum.</span></span> <span data-ttu-id="08313-131">為了簡單起見，我們將此稱為「混合實境頻譜」  。</span><span class="sxs-lookup"><span data-stu-id="08313-131">For simplicity, we refer to this as the *mixed reality spectrum*.</span></span> <span data-ttu-id="08313-132">在左側，是實體實境，也就是我們人類所在之處；在右側，則是對應的數位實境。</span><span class="sxs-lookup"><span data-stu-id="08313-132">On the left-hand side we have physical reality in which we, humans, exist; on the right-hand side we have the corresponding digital reality.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a><span data-ttu-id="08313-133">擴增與虛擬實境</span><span class="sxs-lookup"><span data-stu-id="08313-133">Augmented vs. virtual reality</span></span>

<span data-ttu-id="08313-134">現今市場上大部分的行動電話幾乎都沒有環境理解功能。</span><span class="sxs-lookup"><span data-stu-id="08313-134">Most mobile phones on the market today have little to no environmental understanding capabilities.</span></span> <span data-ttu-id="08313-135">因此，他們所提供的體驗無法混合實體和數位實境。</span><span class="sxs-lookup"><span data-stu-id="08313-135">Thus the experiences they offer cannot mix between physical and digital realities.</span></span> <span data-ttu-id="08313-136">在實體世界的影片串流上重疊圖形的體驗即為「擴增實境」  。</span><span class="sxs-lookup"><span data-stu-id="08313-136">The experiences that overlay graphics on video streams of the physical world are *augmented reality*.</span></span> <span data-ttu-id="08313-137">遮蔽您的檢視來呈現數位體驗的體驗即為「虛擬實境」  。</span><span class="sxs-lookup"><span data-stu-id="08313-137">The experiences that occlude your view to present a digital experience are *virtual reality*.</span></span> <span data-ttu-id="08313-138">如您所見，在這兩個極端之間的體驗，即為「混合實境」  ：</span><span class="sxs-lookup"><span data-stu-id="08313-138">As you can see, the experiences enabled between these two extremes is *mixed reality*:</span></span>
* <span data-ttu-id="08313-139">從實體世界開始，放置數位物件 (例如全像投影)，如同真實存在一般。</span><span class="sxs-lookup"><span data-stu-id="08313-139">Starting with the physical world, placing a digital object, such as a hologram, as if it was really there.</span></span>
* <span data-ttu-id="08313-140">從實體世界開始，另一個人的數位表示法 -- [頭像] -- 顯示他們在留言時所處的位置。</span><span class="sxs-lookup"><span data-stu-id="08313-140">Starting with the physical world, a digital representation of another person--an avatar--shows the location where they were standing when leaving notes.</span></span> <span data-ttu-id="08313-141">換句話說，即為不同時間點表示非同步共同作業的體驗。</span><span class="sxs-lookup"><span data-stu-id="08313-141">In other words, experiences that represent asynchronous collaboration at different points in time.</span></span>
* <span data-ttu-id="08313-142">從數位世界開始，實體世界 (例如牆和傢俱) 的實體界限會以數位方式出現在體驗中，以協助使用者避免實體物件。</span><span class="sxs-lookup"><span data-stu-id="08313-142">Starting with a digital world, physical boundaries from the physical world, such as walls and furniture, appear digitally within the experience to help users avoid physical objects.</span></span>


<br>

<span data-ttu-id="08313-143">![混合實境頻譜](images/mixedrealityspectrum.png)</span><span class="sxs-lookup"><span data-stu-id="08313-143">![The mixed reality spectrum](images/mixedrealityspectrum.png)</span></span><br>
<span data-ttu-id="08313-144">*影像：混合實境頻譜*</span><span class="sxs-lookup"><span data-stu-id="08313-144">*Image: The mixed reality spectrum*</span></span>

<br>

<span data-ttu-id="08313-145">現今提供的大部分擴增實境和虛擬實境產品，都代表此頻譜的一小部分。</span><span class="sxs-lookup"><span data-stu-id="08313-145">Most augmented reality and virtual reality offerings available today represent a very small part of this spectrum.</span></span> <span data-ttu-id="08313-146">不過，它們也是較大混合實境頻譜的子集。</span><span class="sxs-lookup"><span data-stu-id="08313-146">They are, however, subsets of the larger mixed reality spectrum.</span></span> <span data-ttu-id="08313-147">Windows 10 以整個頻譜為基礎，並可將數位方式呈現的人員、環境和事物與真實世界混合。</span><span class="sxs-lookup"><span data-stu-id="08313-147">Windows 10 is built with the entire spectrum in mind, and allows blending digital representations of people, places, and things with the real world.</span></span>




## <a name="devices-and-experiences"></a><span data-ttu-id="08313-148">裝置和體驗</span><span class="sxs-lookup"><span data-stu-id="08313-148">Devices and experiences</span></span>


<span data-ttu-id="08313-149">有兩種主要的裝置類型可提供 Windows Mixed Reality 體驗：</span><span class="sxs-lookup"><span data-stu-id="08313-149">There are two main types of devices that deliver Windows Mixed Reality experiences:</span></span>
1. <span data-ttu-id="08313-150">**全像攝影裝置。**</span><span class="sxs-lookup"><span data-stu-id="08313-150">**Holographic devices.**</span></span> <span data-ttu-id="08313-151">這些特性是由裝置將數位內容放在真實世界中的功能來表示，如同真實存在一般。</span><span class="sxs-lookup"><span data-stu-id="08313-151">These are characterized by the device's ability to place digital content in the real world as if it were really there.</span></span>
2. <span data-ttu-id="08313-152">**沉浸式裝置。**</span><span class="sxs-lookup"><span data-stu-id="08313-152">**Immersive devices.**</span></span> <span data-ttu-id="08313-153">這些特性是由裝置建立「目前狀態」的功能來表示 -- 隱藏實體世界，並以數位體驗取代。</span><span class="sxs-lookup"><span data-stu-id="08313-153">These are characterized by the device's ability to create a sense of "presence"--hiding the physical world, and replacing it with a digital experience.</span></span>

<table>
<tr>
<th width="30%"> <span data-ttu-id="08313-154">特性</span><span class="sxs-lookup"><span data-stu-id="08313-154">Characteristic</span></span></th><th width="35%"> <span data-ttu-id="08313-155">全像攝影裝置</span><span class="sxs-lookup"><span data-stu-id="08313-155">Holographic devices</span></span></th><th width="35%"> <span data-ttu-id="08313-156">沉浸式裝置</span><span class="sxs-lookup"><span data-stu-id="08313-156">Immersive devices</span></span></th>
</tr><tr>
<td><span data-ttu-id="08313-157"><strong>範例裝置</strong></span><span class="sxs-lookup"><span data-stu-id="08313-157"><strong>Example device</strong></span></span></td><td> <span data-ttu-id="08313-158">Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="08313-158">Microsoft HoloLens</span></span><br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> <span data-ttu-id="08313-159">Samsung HMD Odyssey+</span><span class="sxs-lookup"><span data-stu-id="08313-159">Samsung HMD Odyssey+</span></span><br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><span data-ttu-id="08313-160"><strong>顯示器</strong></span><span class="sxs-lookup"><span data-stu-id="08313-160"><strong>Display</strong></span></span></td><td> <span data-ttu-id="08313-161">透明顯示器。</span><span class="sxs-lookup"><span data-stu-id="08313-161">See-through display.</span></span> <span data-ttu-id="08313-162">讓使用者在穿戴頭戴式裝置時可看到實體環境。</span><span class="sxs-lookup"><span data-stu-id="08313-162">Allows user to see the physical environment while wearing the headset.</span></span></td><td> <span data-ttu-id="08313-163">不透明顯示器。</span><span class="sxs-lookup"><span data-stu-id="08313-163">Opaque display.</span></span> <span data-ttu-id="08313-164">在穿戴頭戴式裝置時封鎖實體環境。</span><span class="sxs-lookup"><span data-stu-id="08313-164">Blocks out the physical environment while wearing the headset.</span></span></td>
</tr><tr>
<td><span data-ttu-id="08313-165"><strong>移動</strong></span><span class="sxs-lookup"><span data-stu-id="08313-165"><strong>Movement</strong></span></span></td><td> <span data-ttu-id="08313-166">完整的六度自由移動，包括旋轉和轉譯。</span><span class="sxs-lookup"><span data-stu-id="08313-166">Full six-degrees-of-freedom movement, both rotation and translation.</span></span></td><td> <span data-ttu-id="08313-167">完整的六度自由移動，包括旋轉和轉譯。</span><span class="sxs-lookup"><span data-stu-id="08313-167">Full six-degrees-of-freedom movement, both rotation and translation.</span></span></td>
</tr>
</table>



<span data-ttu-id="08313-168">請注意，無論裝置是連線到其他電腦或以行動網卡連線到其他電腦 (透過 USB 纜線或 Wi-Fi) 或是獨立的 (未連線)，都不會反映裝置是否為全像攝影還是沉浸式。</span><span class="sxs-lookup"><span data-stu-id="08313-168">Note, whether a device is connected to or tethered to a separate PC (via USB cable or Wi-Fi) or self-contained (untethered) does not reflect whether a device is holographic or immersive.</span></span> <span data-ttu-id="08313-169">當然，增加行動性的功能會帶來更好的體驗，且全像攝影和沉浸式裝置都可能是以行動網卡連線或是未連線的。</span><span class="sxs-lookup"><span data-stu-id="08313-169">Certainly, features that improve mobility lead to better experiences, and both holographic and immersive devices could be tethered or untethered.</span></span>


<span data-ttu-id="08313-170">技術提升是已啟用混合實境體驗的功能。</span><span class="sxs-lookup"><span data-stu-id="08313-170">Technological advancement is what has enabled mixed reality experiences.</span></span> <span data-ttu-id="08313-171">目前沒有任何裝置可在整個頻譜中執行體驗。</span><span class="sxs-lookup"><span data-stu-id="08313-171">There are no devices today that can run experiences across the entire spectrum.</span></span> <span data-ttu-id="08313-172">不過，Windows 10 同時為裝置製造商和開發人員提供通用的混合實境平台。</span><span class="sxs-lookup"><span data-stu-id="08313-172">However, Windows 10 provides a common mixed reality platform for both device manufacturers and developers.</span></span> <span data-ttu-id="08313-173">現今的裝置可以支援混合實境頻譜內的特定範圍。</span><span class="sxs-lookup"><span data-stu-id="08313-173">Devices today can support a specific range within the mixed reality spectrum.</span></span> <span data-ttu-id="08313-174">經過一段時間後，新的裝置將會擴充該範圍。</span><span class="sxs-lookup"><span data-stu-id="08313-174">Over time, new devices will expand that range.</span></span> <span data-ttu-id="08313-175">在未來，全像攝影裝置會變得更沉浸式，而沉浸式裝置會變得更全像攝影。</span><span class="sxs-lookup"><span data-stu-id="08313-175">In the future, holographic devices will become more immersive, and immersive devices will become more holographic.</span></span>

<br>

<span data-ttu-id="08313-176">![混合實境頻譜中的裝置類型](images/Final_WhatIsMixedReality07.png)</span><span class="sxs-lookup"><span data-stu-id="08313-176">![Device types in the mixed reality spectrum](images/Final_WhatIsMixedReality07.png)</span></span><br>
<span data-ttu-id="08313-177">*影像：裝置在混合實境頻譜上的位置*</span><span class="sxs-lookup"><span data-stu-id="08313-177">*Image: Where devices exist on the mixed reality spectrum*</span></span>

<span data-ttu-id="08313-178">通常，最好能考量應用程式或遊戲開發人員想要建立的經驗類型。</span><span class="sxs-lookup"><span data-stu-id="08313-178">Often, it is best to think what type of experience an application or game developer wants to create.</span></span> <span data-ttu-id="08313-179">這些體驗通常會以頻譜上的特定點或部分作為目標。</span><span class="sxs-lookup"><span data-stu-id="08313-179">The experiences will typically target a specific point or part on the spectrum.</span></span> <span data-ttu-id="08313-180">然後，開發人員應該考慮他們想要作為目標的裝置功能。</span><span class="sxs-lookup"><span data-stu-id="08313-180">Then, developers should consider the capabilities of devices they want to target.</span></span> <span data-ttu-id="08313-181">例如，仰賴實體世界的體驗在 HoloLens 上的效果最佳。</span><span class="sxs-lookup"><span data-stu-id="08313-181">For example, experiences that rely on the physical world will run best on HoloLens.</span></span>
* <span data-ttu-id="08313-182">**向左 (接近實體實境)。**</span><span class="sxs-lookup"><span data-stu-id="08313-182">**Towards the left (near physical reality).**</span></span> <span data-ttu-id="08313-183">使用者仍然存在於其實體環境中，且永遠不會相信他們已離開該環境。</span><span class="sxs-lookup"><span data-stu-id="08313-183">Users remain present in their physical environment and are never made to believe they have left that environment.</span></span>
* <span data-ttu-id="08313-184">**中間 (完全混合實境)。**</span><span class="sxs-lookup"><span data-stu-id="08313-184">**In the middle (fully mixed reality).**</span></span> <span data-ttu-id="08313-185">這些體驗混合了真實世界與數位世界。</span><span class="sxs-lookup"><span data-stu-id="08313-185">These experiences blend the real world and the digital world.</span></span> <span data-ttu-id="08313-186">看過[野蠻遊戲](https://en.wikipedia.org/wiki/Jumanji)這部電影的觀看者，可以調整故事中所出現房屋的實體結構與叢林環境的混合方式。</span><span class="sxs-lookup"><span data-stu-id="08313-186">Viewers who have seen the movie [Jumanji](https://en.wikipedia.org/wiki/Jumanji) can reconcile how the physical structure of the house where the story took place was blended with a jungle environment.</span></span>
* <span data-ttu-id="08313-187">**向右 (接近數位實境)。**</span><span class="sxs-lookup"><span data-stu-id="08313-187">**Towards the right (near digital reality).**</span></span> <span data-ttu-id="08313-188">使用者會遇到完全數位的環境，且不會察覺周遭實體環境中發生的情況。</span><span class="sxs-lookup"><span data-stu-id="08313-188">Users experience a completely digital environment, and are unaware of what occurs in the physical environment around them.</span></span>


## <a name="see-also"></a><span data-ttu-id="08313-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08313-189">See also</span></span>

* [<span data-ttu-id="08313-190">什麼是全像投影？</span><span class="sxs-lookup"><span data-stu-id="08313-190">What is a hologram?</span></span>](hologram.md)
* [<span data-ttu-id="08313-191">了解混合實境的基本概念</span><span class="sxs-lookup"><span data-stu-id="08313-191">Understand the basics of mixed reality</span></span>](get-started-with-mr.md#understand-the-basics)
* [<span data-ttu-id="08313-192">開始建立並建立原型</span><span class="sxs-lookup"><span data-stu-id="08313-192">Start creating and prototyping</span></span>](design.md)
* [<span data-ttu-id="08313-193">了解工具和架構</span><span class="sxs-lookup"><span data-stu-id="08313-193">Learn the tools and architecture</span></span>](development.md)

