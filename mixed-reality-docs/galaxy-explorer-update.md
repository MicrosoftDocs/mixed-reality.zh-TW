---
title: 適用于 HoloLens 2 的 Galaxy Explorer
description: 歡迎使用我們更新 HoloLens 2 的 Galaxy Explorer 的旅程。 就像原始的「Galaxy Explorer」一樣, 我們的小組也會在 GitHub 上開啟專案, 以確保該社區具有完整的存取權。
author: l-garrett
ms.author: grbury
ms.date: 06/30/2019
ms.topic: article
keywords: galaxy explorer, 案例研究, 專案, 範例
ms.openlocfilehash: 1e04b27ff0382d87f8e6a15ae2b7b2284fa020e6
ms.sourcegitcommit: be3631932ea1c88ac3ad8b2390c98c5a6e8b93ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2019
ms.locfileid: "68776542"
---
# <a name="the-making-of-galaxy-explorer-for-hololens-2"></a><span data-ttu-id="447e0-105">適用于 HoloLens 2 的 Galaxy Explorer</span><span class="sxs-lookup"><span data-stu-id="447e0-105">The Making of Galaxy Explorer for HoloLens 2</span></span>

<span data-ttu-id="447e0-106">歡迎使用我們更新 HoloLens 2 的 Galaxy Explorer 的旅程。</span><span class="sxs-lookup"><span data-stu-id="447e0-106">Welcome to the journey of how we are updating Galaxy Explorer for HoloLens 2.</span></span> <span data-ttu-id="447e0-107">[Galaxy Explorer](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer "Galaxy Explorer")最初是以適用于 HoloLens (第1代) 的開放原始碼應用程式開發, 並透過分享您的創意計畫, 而且是許多人的第一個混合現實經驗。</span><span class="sxs-lookup"><span data-stu-id="447e0-107">[Galaxy Explorer](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer "Galaxy Explorer") was originally developed as an open source application for HoloLens (1st gen) through the Share Your Idea program, and is one of the first mixed reality experiences many people had.</span></span> <span data-ttu-id="447e0-108">現在我們要更新它, 以取得[HoloLens 2 的全新且令人興奮的功能](https://www.microsoft.com/hololens/hardware)。</span><span class="sxs-lookup"><span data-stu-id="447e0-108">Now we are updating it for the [new and exciting capabilities of HoloLens 2](https://www.microsoft.com/hololens/hardware).</span></span>

<span data-ttu-id="447e0-109">身為[Microsoft Mixed Reality 工作室](galaxy-explorer-update.md#mixed-reality-studios)的其中一個, 我們通常會開發商業級解決方案, 並在整個創意和開發過程中, 開發 & 在目標平臺上進行測試。</span><span class="sxs-lookup"><span data-stu-id="447e0-109">As one of the [Microsoft Mixed Reality Studios](galaxy-explorer-update.md#mixed-reality-studios), we usually develop commercial grade solutions and are developing & testing on target platforms throughout the creative and development process.</span></span> <span data-ttu-id="447e0-110">我們現在有一種獨特的情況, 也就是還沒有 HoloLens 2 裝置的存取權, 但很高興能夠開始更新至 Galaxy Explorer。</span><span class="sxs-lookup"><span data-stu-id="447e0-110">We now have the unique situation where don’t yet have access to HoloLens 2 devices, but are excited to start the updates to Galaxy Explorer.</span></span> <span data-ttu-id="447e0-111">我們會登機在這個專案上使用架構和工具 (例如[MRTK v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)), 因為它們可以提供給我們和「社區」, 而我們想要帶您一起進行。</span><span class="sxs-lookup"><span data-stu-id="447e0-111">We're embarking on this project utilizing the frameworks and tools (like [MRTK v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)) as they become available to us and the community - and we want to bring you along for the ride.</span></span>

<span data-ttu-id="447e0-112">就像原始的「Galaxy Explorer」一樣,[我們的小組](galaxy-explorer-update.md#meet-the-team)也會在[GitHub 上開啟專案](https://github.com/Microsoft/GalaxyExplorer), 以確保該社區具有完整的存取權。</span><span class="sxs-lookup"><span data-stu-id="447e0-112">Just like the original Galaxy Explorer, [our team](galaxy-explorer-update.md#meet-the-team) will be [open sourcing the project on GitHub](https://github.com/Microsoft/GalaxyExplorer) to ensure that the community has full access.</span></span> <span data-ttu-id="447e0-113">我們也將在這裡記錄我們的旅程, 以完整的透明度說明我們 undertook 從 MRTK v1 移植到 MRTK v2 的方式、如何根據 HoloLens 2 中提供的新功能來增強體驗, 以及如何確保 Galaxy Explorer 保持不變多平臺體驗。</span><span class="sxs-lookup"><span data-stu-id="447e0-113">We will also be documenting our journey here in complete transparency about the ways in which we undertook porting from MRTK v1 to MRTK v2, how we enhanced the experience based on the new features available in HoloLens 2, and how we ensured that Galaxy Explorer remained a multi-platform experience.</span></span> <span data-ttu-id="447e0-114">因此無論您是在 HoloLens (第1代)、HoloLens 2、Windows Mixed Reality 耳機或 Windows 10 desktop 上觀看 Galaxy Explorer, 我們都想要確保您擁有豐富的體驗, 並盡可能享用旅程。</span><span class="sxs-lookup"><span data-stu-id="447e0-114">So whether you're viewing Galaxy Explorer on HoloLens (1st gen), HoloLens 2, a Windows Mixed Reality headset or on your Windows 10 desktop, we want to ensure that you're having an immersive experience and enjoy the journey as much as we are!</span></span>

<span data-ttu-id="447e0-115">此頁面將會隨著我們在專案中的進度擴展, 而我們將會連結至更詳細的文章、程式碼、設計構件、其他 MRTK v2 檔等專案。</span><span class="sxs-lookup"><span data-stu-id="447e0-115">This page will expand as we progress through the project, and we'll link out to more detailed articles, code, design artefacts, additional MRTK v2 documentation, etc. to provide you with an insider's look at the project.</span></span>

## <a name="unveiling-the-new-logo"></a><span data-ttu-id="447e0-116">揭露新標誌</span><span class="sxs-lookup"><span data-stu-id="447e0-116">Unveiling the new logo</span></span>

<span data-ttu-id="447e0-117">我們很興奮地開始使用新的 Galaxy Explorer 標誌的預覽!</span><span class="sxs-lookup"><span data-stu-id="447e0-117">We're excited to kick off with a preview of the new Galaxy Explorer logo!</span></span> <span data-ttu-id="447e0-118">藉由以銀河的方式來以示敬意原始標誌, 我們設計了逼真的視覺效果並更新印刷樣式, 以提供更精緻且現代化的風格。</span><span class="sxs-lookup"><span data-stu-id="447e0-118">While paying homage to the original logo by featuring the Milky Way, we've designed a realistic visualization and updated the typography to provide a more sleek and modern feel.</span></span> <span data-ttu-id="447e0-119">標誌中包含的是搶先查看其中一個新圖示。</span><span class="sxs-lookup"><span data-stu-id="447e0-119">Included in the logo is a sneak peek at one of the new icons.</span></span>

![新的 [Galaxy Explorer] 標誌](images/ge-update-app-icon.png)

<span data-ttu-id="447e0-121">標誌的設計和印刷樣式會在整個體驗中, 設定 UI 元素整體外觀與風格的色調。</span><span class="sxs-lookup"><span data-stu-id="447e0-121">The design and typography of the logo will set the tone for the overall look and feel of UI elements throughout the experience.</span></span> 

## <a name="thinking-about-interactions"></a><span data-ttu-id="447e0-122">考慮互動</span><span class="sxs-lookup"><span data-stu-id="447e0-122">Thinking about interactions</span></span>

<span data-ttu-id="447e0-123">身為創意的 studio, 我們 ecstatic 了將 [Galaxy Explorer] 移植至 HoloLens 2 的許可權。</span><span class="sxs-lookup"><span data-stu-id="447e0-123">As a creative studio, we were ecstatic about the privilege to port Galaxy Explorer to HoloLens 2.</span></span> <span data-ttu-id="447e0-124">我們從一開始就知道, 我們希望體驗成為新裝置的慶祝, 並示範混合現實的能力僅限於想像。</span><span class="sxs-lookup"><span data-stu-id="447e0-124">We knew from the start that we wanted the experience to be a celebration of the new device and to demonstrate that Mixed Reality empowerment is limited only to the imagination.</span></span>

<span data-ttu-id="447e0-125">HoloLens 2 可讓使用者以自然的方式來觸控、抓住和移動全息影像, 它們會回應很多類似實際的物件。</span><span class="sxs-lookup"><span data-stu-id="447e0-125">HoloLens 2 allows users to touch, grasp, and move holograms in ways that feel natural – they respond a lot like real objects.</span></span> <span data-ttu-id="447e0-126">全清楚表達的手模型很驚人, 因為它可讓使用者執行自然的外觀。</span><span class="sxs-lookup"><span data-stu-id="447e0-126">Fully articulated hand models are amazing, because it lets users do what feels natural.</span></span> <span data-ttu-id="447e0-127">例如, 每個人都以不同的方式來挑選杯, 而不是強制執行它, 而是透過 HoloLens 2 來執行。</span><span class="sxs-lookup"><span data-stu-id="447e0-127">For example, everybody picks up a cup slightly differently – and instead of enforcing one particular way to do it, HoloLens 2 lets you do it your way.</span></span>

>[!VIDEO https://www.youtube.com/embed/wogJv5v9x-s]

<span data-ttu-id="447e0-128">這是第一代 HoloLens 裝置上的以空中操作介面為基礎的重大變更。</span><span class="sxs-lookup"><span data-stu-id="447e0-128">This is a big change from the Air Tap-based interfaces on first generation HoloLens devices.</span></span> <span data-ttu-id="447e0-129">使用者現在可以取得「關閉」和「個人」, 而不是與從遠處的全息影像互動。</span><span class="sxs-lookup"><span data-stu-id="447e0-129">Instead of interacting with holograms from a distance, users can now get "up close and personal".</span></span> <span data-ttu-id="447e0-130">將現有的經驗移植到 HoloLens 2 或規劃新的體驗時, 請務必熟悉全像投影的直接操作。</span><span class="sxs-lookup"><span data-stu-id="447e0-130">When porting existing experiences over to HoloLens 2 or planning new ones, it is important to make yourself familiar with the direct manipulation of holograms.</span></span>

### <a name="direct-manipulation-vs-the-vast-distances-in-space"></a><span data-ttu-id="447e0-131">直接操作與空間中的巨大距離</span><span class="sxs-lookup"><span data-stu-id="447e0-131">Direct manipulation vs. the vast distances in space</span></span>

<span data-ttu-id="447e0-132">這是一種神奇的體驗, 可讓您取得地球並將它放在您手中。</span><span class="sxs-lookup"><span data-stu-id="447e0-132">It is a magical experience to be able to reach out, grab a planet and hold it in your hand.</span></span> <span data-ttu-id="447e0-133">這種方法的挑戰是日光系統的大小–非常龐大!</span><span class="sxs-lookup"><span data-stu-id="447e0-133">The challenge with this approach is the size of the solar system – it's huge!</span></span> <span data-ttu-id="447e0-134">使用者必須四處討論他們的房間, 才能與每個地球進行互動。</span><span class="sxs-lookup"><span data-stu-id="447e0-134">The user would need to walk around their room to get close to each planet to be able to interact with it.</span></span>

<span data-ttu-id="447e0-135">為了讓使用者能夠與距離較遠的物件互動, MRTK 提供了從使用者 palm 的中心開始的手片, 做為手的延伸。</span><span class="sxs-lookup"><span data-stu-id="447e0-135">To allow users to interact with objects that are farther away, MRTK offers hand rays that shoot out from the center of the user's palm, acting as an extension of the hand.</span></span> <span data-ttu-id="447e0-136">環圈形游標會附加到光線的尾端, 以指示光線與目標物件相交的位置。</span><span class="sxs-lookup"><span data-stu-id="447e0-136">A donut-shaped cursor is attached to the end of the ray to indicate where the ray intersects with a target object.</span></span> <span data-ttu-id="447e0-137">然後，游標所在的物件就能從手部接收手勢命令。</span><span class="sxs-lookup"><span data-stu-id="447e0-137">The object that the cursor lands on can then receive gestural commands from the hand.</span></span> 

>[!VIDEO https://www.youtube.com/embed/Qol5OFNfN14]

<span data-ttu-id="447e0-138">在原始版本的 [Galaxy Explorer] 中, 使用者會以看看游標的全球為目標, 然後再按 [按較近的電話]。</span><span class="sxs-lookup"><span data-stu-id="447e0-138">In the original version of Galaxy Explorer, the user would target a planet with the gaze cursor and then air tap to call it closer.</span></span> <span data-ttu-id="447e0-139">將體驗移植到 HoloLens 2 最簡單的方式, 就是採取此行為, 並使用手片來選取行星。</span><span class="sxs-lookup"><span data-stu-id="447e0-139">The easiest way to port the experience to HoloLens 2 is to take this behavior and use hand rays to select planets.</span></span> <span data-ttu-id="447e0-140">雖然這是正常運作的功能, 但我們仍想要更多。</span><span class="sxs-lookup"><span data-stu-id="447e0-140">While this was functional, it left us wanting more.</span></span>

### <a name="back-to-the-drawing-board"></a><span data-ttu-id="447e0-141">回到繪圖面板</span><span class="sxs-lookup"><span data-stu-id="447e0-141">Back to the drawing board</span></span>

<span data-ttu-id="447e0-142">我們合在一起, ideate 可以在現有互動之上建立的內容。</span><span class="sxs-lookup"><span data-stu-id="447e0-142">We came together to ideate what could be built on top of the existing interactions.</span></span> <span data-ttu-id="447e0-143">思考是:雖然 HoloLens 2 可讓使用者以自然、實際的方式與全息影像互動, 但全息的全像是不真正的定義。</span><span class="sxs-lookup"><span data-stu-id="447e0-143">The thinking was: Although HoloLens 2 allows users to interact with holograms in natural, realistic ways, holograms are by definition not real.</span></span> <span data-ttu-id="447e0-144">因此, 只要使用者合理情況互動, 就不會影響到實際的物件是否能夠進行互動–我們可以做到這一點。</span><span class="sxs-lookup"><span data-stu-id="447e0-144">So as long as an interaction is plausible for the user, it doesn't matter if that interaction would be possible with a real object or not – we can make it possible.</span></span>

<span data-ttu-id="447e0-145">我們探索的一個概念是以 telekinesis 為基礎–這是一項想法來操控物件的能力。</span><span class="sxs-lookup"><span data-stu-id="447e0-145">One concept that we explored was based on telekinesis – the power to manipulate objects with one's mind.</span></span> <span data-ttu-id="447e0-146">通常會出現在超級主圖電影中, 一位人會想到他們的想法, 並將物件呼叫到他們的手中。</span><span class="sxs-lookup"><span data-stu-id="447e0-146">Often seen in super hero movies, a person would reach out with their mind and call an object into their open hand.</span></span> <span data-ttu-id="447e0-147">我們有更多的想法, 並提出概念的快速草圖。</span><span class="sxs-lookup"><span data-stu-id="447e0-147">We played around with the idea some more and came up with a quick sketch of how the concept could work.</span></span>

![強制抓取互動的概念](images/ge-update-interactions-concept-force-grab.png)

<span data-ttu-id="447e0-149">使用者會將手中的光線指向地球, 這會提供目標意見反應。</span><span class="sxs-lookup"><span data-stu-id="447e0-149">The user would point the hand ray at a planet, which would provide target feedback.</span></span> <span data-ttu-id="447e0-150">當使用者接著擴充其開放式手時, 系統會將地球向使用者提取神奇強制, 直到夠近才能抓取。</span><span class="sxs-lookup"><span data-stu-id="447e0-150">As the user then extends their open hand, the planet would be pulled towards the user by a magical force until it is close enough to grab it.</span></span> <span data-ttu-id="447e0-151">因此, 我們會進行互動的名稱: force 抓取。</span><span class="sxs-lookup"><span data-stu-id="447e0-151">Hence our name for the interaction: force grab.</span></span> <span data-ttu-id="447e0-152">因為使用者會以其手上推播地球, 所以會再次回到其軌道。</span><span class="sxs-lookup"><span data-stu-id="447e0-152">As the user would push away the planet with their open hand, it would return again to its orbit.</span></span>

### <a name="force-grab-prototyping"></a><span data-ttu-id="447e0-153">強制抓取原型</span><span class="sxs-lookup"><span data-stu-id="447e0-153">Force grab prototyping</span></span>

<span data-ttu-id="447e0-154">接著, 我們建立了多個原型來測試概念:互動的整體外觀為何？</span><span class="sxs-lookup"><span data-stu-id="447e0-154">We then created multiple prototypes to test the concept: How does the interaction feel overall?</span></span> <span data-ttu-id="447e0-155">被呼叫的物件是否會在使用者之前停止, 或停留在下的手中？</span><span class="sxs-lookup"><span data-stu-id="447e0-155">Should the called object stop in front of the user or stick to their hands until placed?</span></span> <span data-ttu-id="447e0-156">呼叫的物件是否應該在呼叫時變更大小或小數值？</span><span class="sxs-lookup"><span data-stu-id="447e0-156">Should the called object change size or scale while being called?</span></span>

<!--
Here is Amit Rojtblat (Technical Artist) presenting one of the prototypes to Yasushi Zonno (Creative Lead).

------------------------------------------------------------------

__*--- VIDEO OF AMIT PLAYING AND EXPLAINING THE PROTOTYPE ---*__

__*--- NEEDS TO BE UPLOADED (TO YOUTUBE?) AND LINKED ---*__

------------------------------------------------------------------
-->

### <a name="implementing-force-grab-into-the-application"></a><span data-ttu-id="447e0-157">在應用程式中執行強制抓取</span><span class="sxs-lookup"><span data-stu-id="447e0-157">Implementing force grab into the application</span></span>

<span data-ttu-id="447e0-158">當我們嘗試在行星上進行強制抓取時, 我們發現我們必須變更日光系統的規模。</span><span class="sxs-lookup"><span data-stu-id="447e0-158">When we tried the force grab on planets, we realized that we had to change the scale of the solar system.</span></span> <span data-ttu-id="447e0-159">我們發現日光系統的精確、中型標記法很難以讓使用者瞭解和流覽-它們不知道要查看的位置。</span><span class="sxs-lookup"><span data-stu-id="447e0-159">It turned out that an accurate, medium-sized representation of the solar system is difficult for users to understand and navigate - they did not know where to look.</span></span> <span data-ttu-id="447e0-160">不過, 精確、小型大小的標記法使得某些行星太小, 無法輕易地選取。</span><span class="sxs-lookup"><span data-stu-id="447e0-160">However an accurate, small-sized-representation made some planets too small to be easily selected.</span></span> <span data-ttu-id="447e0-161">因此, 行星的大小和陽曆物件之間的間距, 是設計成在中等大小的房間內感到舒適, 同時維持相對的準確度。</span><span class="sxs-lookup"><span data-stu-id="447e0-161">As a result, the size of the planets and the spacing between solar objects was designed to feel comfortable within a medium-sized room while maintaining relative accuracy.</span></span>

<span data-ttu-id="447e0-162">在開發短期衝刺的後續階段中, 我們已經很幸運地有其他的 MSFT 混合現實專家, 所以我們可以將其輸入做為專家測試人員, 並在強制抓取互動上進行快速反復執行。</span><span class="sxs-lookup"><span data-stu-id="447e0-162">During the later stages of our development sprint, we were lucky enough to have fellow MSFT Mixed Reality experts in-house, so we got to work getting their input as expert testers and doing quick iterations on the force grab interaction.</span></span>

![Jenny Kam 測試 [Galaxy Explorer] 的預覽組建](images/ge-update-user-testing.png)

<span data-ttu-id="447e0-164">在圖片中:Jenny Kam, 資深設計組長, 測試 Galaxy Explorer 的工作進行中。</span><span class="sxs-lookup"><span data-stu-id="447e0-164">In picture: Jenny Kam, Senior Design Lead, testing a work-in-progress of Galaxy Explorer.</span></span>

### <a name="adding-affordances-for-targeting"></a><span data-ttu-id="447e0-165">新增目標的 affordances</span><span class="sxs-lookup"><span data-stu-id="447e0-165">Adding affordances for targeting</span></span>

<span data-ttu-id="447e0-166">當我們在 HoloLens 2 上實驗時, 我們發現即使新的互動是自然且直覺的, 但全息的全像沒有權數或觸覺 sensations。</span><span class="sxs-lookup"><span data-stu-id="447e0-166">As we experimented on HoloLens 2, we found that even though the new interactions are natural and intuitive, holograms remain the same: with no weight or tactile sensations.</span></span> <span data-ttu-id="447e0-167">由於全息影像不會提供自然的意見反應, 讓人類用來接收與物件互動時的情況, 我們需要建立它們。</span><span class="sxs-lookup"><span data-stu-id="447e0-167">Since holograms don't provide natural feedback that humans are used to receiving when they interact with objects, we needed to create them.</span></span>

<span data-ttu-id="447e0-168">我們考慮到使用者會針對其互動的各個階段提供的視覺和音訊意見反應, 而且由於強制抓取機制是與 Galaxy Explorer 互動的核心, 我們進行了許多反復專案。</span><span class="sxs-lookup"><span data-stu-id="447e0-168">We thought about the visual and audio feedback that users would be provided for the various stages of their interactions, and since the force grab mechanism is central to interacting with Galaxy Explorer, we did many iterations.</span></span> <span data-ttu-id="447e0-169">其目標是要為互動的每個階段尋找適當的音訊和視覺效果意見反應: 將焦點放在預期的物件上, 並將其呼叫給使用者, 然後放開它。</span><span class="sxs-lookup"><span data-stu-id="447e0-169">The aim was to find the right balance of audio and visual feedback for each stage of the interaction: focusing on the intended object, calling it to the user, and then releasing it.</span></span> <span data-ttu-id="447e0-170">我們學到的是, 要比我們用於 HoloLens (第一代) 的互動, 需要更多的音訊和視覺效果回饋。</span><span class="sxs-lookup"><span data-stu-id="447e0-170">What we learned is that significantly more audio and visual feedback was required to reinforce the interaction than we were used to for HoloLens (1st gen).</span></span>

![行星上的視覺 affordances](images/ge-update-planet-affordances.png)

### <a name="adding-affordances-for-force-grab"></a><span data-ttu-id="447e0-172">新增 affordances 以強制抓取</span><span class="sxs-lookup"><span data-stu-id="447e0-172">Adding affordances for force grab</span></span>
 
<span data-ttu-id="447e0-173">一旦有了具有音訊和視覺效果 affordances 的基本強制抓取機制, 我們探討了如何讓使用者更容易選擇使用行星。</span><span class="sxs-lookup"><span data-stu-id="447e0-173">Once we had the basic force grab mechanism with audio and visual affordances, we looked at how to make selecting planets more user friendly.</span></span> <span data-ttu-id="447e0-174">有兩個主要的事項要解決:因為日光系統是3D 移動介面, 所以使用者會更複雜地瞭解如何以一致的方式為物件設定目標。</span><span class="sxs-lookup"><span data-stu-id="447e0-174">There were two main things to address: Because the solar system is a 3D moving interface, there is added complexity for users to learn how to target objects consistently.</span></span> <span data-ttu-id="447e0-175">這是因為在選取物件時, 右手光線非常快速, 讓行星更快速地移至使用者。</span><span class="sxs-lookup"><span data-stu-id="447e0-175">This was compounded by the fact that the hand ray is very fast at selecting an object, making planets move towards the user incredibly quickly.</span></span>

<span data-ttu-id="447e0-176">我們使用三個架構的解決方案來達到這個效益。</span><span class="sxs-lookup"><span data-stu-id="447e0-176">We approached this with a three-pronged solution.</span></span> <span data-ttu-id="447e0-177">第一種是相當直覺的: 使選取程式變慢, 讓行星以更自然的步調來處理使用者。</span><span class="sxs-lookup"><span data-stu-id="447e0-177">The first was fairly intuitive: slow down the selection process so that planets approach the user at a more natural pace.</span></span> <span data-ttu-id="447e0-178">調整速度之後, 我們必須重新流覽音訊和視覺效果 affordances, 新增其他音訊意見反應, 做為向使用者追蹤的地球。</span><span class="sxs-lookup"><span data-stu-id="447e0-178">Once the speed was adjusted, we had to revisit the audio and visual affordances, adding additional audio feedback as the planet tracked towards the user.</span></span>

<span data-ttu-id="447e0-179">解決方案的第二個部分是讓整個強制抓取互動的視覺效果非常有形。</span><span class="sxs-lookup"><span data-stu-id="447e0-179">The second part of the solution was to make the visualization of the entire force grab interaction extremely tangible.</span></span> <span data-ttu-id="447e0-180">我們視覺化了一條粗線, 它會在手邊與目標物件連接之後移動, 然後將該物件帶回給使用者的套索。</span><span class="sxs-lookup"><span data-stu-id="447e0-180">We visualized a thick line that moves towards the targeted object once the hand ray connects with it, and then brings the object back to the user - like a lasso.</span></span> 

![適用于 force 抓取的視覺效果「套索」 affordances](images/ge-update-lasso-affordances.png)

<span data-ttu-id="447e0-182">最後, 我們優化了日光系統的規模, 讓行星的大小夠大, 讓使用者的注視和手上的光線達到目標。</span><span class="sxs-lookup"><span data-stu-id="447e0-182">Finally, we optimized the scale of the solar system so that the planets were large enough for the user's gaze and hand ray to target them.</span></span> 

<span data-ttu-id="447e0-183">這三項改良功能可以讓使用者做出精確的選擇, 以直覺的方式對他們呼叫行星。</span><span class="sxs-lookup"><span data-stu-id="447e0-183">These three improvements allowed users to make accurate selections, calling planets to them in an intuitive way.</span></span> <span data-ttu-id="447e0-184">整體來說, 最終強制抓取的效果是在日光系統中提供更多的沉浸式互動體驗。</span><span class="sxs-lookup"><span data-stu-id="447e0-184">Overall, the effect of the final force grab is a more immersive and interactive experience in the solar system.</span></span>

## <a name="spotlight-on-jupiter"></a><span data-ttu-id="447e0-185">木星上的焦點</span><span class="sxs-lookup"><span data-stu-id="447e0-185">Spotlight on Jupiter</span></span>

<span data-ttu-id="447e0-186">建立銀河方式的日光, 是一項 humbling 的經驗。</span><span class="sxs-lookup"><span data-stu-id="447e0-186">Creating the solar bodies of the Milky Way was a humbling experience.</span></span> <span data-ttu-id="447e0-187">特別是, 木星的獨特特性讓它成為耶的可見方式。</span><span class="sxs-lookup"><span data-stu-id="447e0-187">In particular, the unique characteristics of Jupiter make it a sight to behold.</span></span> <span data-ttu-id="447e0-188">這是天然氣巨人的最大和最多色彩, 其包含的品質比所有其他的行星還要大。</span><span class="sxs-lookup"><span data-stu-id="447e0-188">It is the largest and most colorful of the gas giants, and contains more mass than all other planets combined.</span></span> <span data-ttu-id="447e0-189">其晃動和 cloud dynamics 的龐大大小和 mesmerizing 區 prefect, 可讓您特別注意。</span><span class="sxs-lookup"><span data-stu-id="447e0-189">Its sheer size and mesmerizing bands of turbulence and cloud dynamics are prefect for special artistic attention.</span></span>

### <a name="geometry-and-meshes"></a><span data-ttu-id="447e0-190">Geometry 和網格</span><span class="sxs-lookup"><span data-stu-id="447e0-190">Geometry and meshes</span></span>

<span data-ttu-id="447e0-191">隨著天然氣的外部 shell, 這是由 gaseous 層所組成。</span><span class="sxs-lookup"><span data-stu-id="447e0-191">As a gas giant, Jupiter's outer shells consists of gaseous layers.</span></span> <span data-ttu-id="447e0-192">其快速旋轉速度、內部熱度交換和 Coriolis 強制的結合, 可讓您建立色彩豐富的圖層和串流, 以形成 swirling cloud 皮帶和 vortices。</span><span class="sxs-lookup"><span data-stu-id="447e0-192">The combination of its fast rotational speed, inner heat exchange, and Coriolis forces creates colorful layers and streams that form into swirling cloud belts and vortices.</span></span> <span data-ttu-id="447e0-193">在建立我們的日光系統時, 捕捉這個複雜的美式就是關鍵。</span><span class="sxs-lookup"><span data-stu-id="447e0-193">Capturing this intricate beauty was key in creating our solar system.</span></span>

<span data-ttu-id="447e0-194">這會立即清楚地說, 使用視覺化的技術 (例如流暢的模擬) 和具有預先計算串流的動畫紋理不會有任何問題。</span><span class="sxs-lookup"><span data-stu-id="447e0-194">It was immediately clear that using visualizing techniques like fluid simulations and animated textures with precomputed streams were out of question.</span></span> <span data-ttu-id="447e0-195">同時模擬這項功能所需的運算能力, 可能會對效能造成明顯的不利影響。</span><span class="sxs-lookup"><span data-stu-id="447e0-195">The computing power required to simulate this in combination with everything else happening simultaneously would have had significant detrimental impacts on performance.</span></span> 

![木星物件的總覽](images/ge-update-jupiter-shells-complete.jpg)

<span data-ttu-id="447e0-197">下一個方法是「冒煙和鏡像」解決方案, 由覆迭透明材質圖層所組成, 其中每一個都是在旋轉網格的組合上所編譯的面向移動的特定層面。</span><span class="sxs-lookup"><span data-stu-id="447e0-197">The next approach was a 'smoke-and-mirror' solution, consisting of overlaying transparent texture layers, each of which addressed a specific aspect of the atmospheric movement, compiled on a composition of rotating meshes.</span></span>

<span data-ttu-id="447e0-198">在下圖中, 您可以看到左側的內部 shell。</span><span class="sxs-lookup"><span data-stu-id="447e0-198">In the image below, you can see the inner shell on the left.</span></span> <span data-ttu-id="447e0-199">此 matt 圖層提供組合的背景, 以預防組成雲端的多層之間的任何小間隙。</span><span class="sxs-lookup"><span data-stu-id="447e0-199">This matt layer provided a background to the composition to guard against any small gaps between the multiple layers that comprised the clouds.</span></span> <span data-ttu-id="447e0-200">由於圖層的緩慢旋轉, 它也會在較快速的移動群組之間做為視覺化緩衝區, 以協助在整個層中建立視覺 unity。</span><span class="sxs-lookup"><span data-stu-id="447e0-200">Due to the layer's slow rotation, it also served as a visual buffer between the faster moving bands to help build visual unity throughout the layers.</span></span>

<span data-ttu-id="447e0-201">將此錨點設定為模型之後, 移動的雲端層會接著投射在下面所見的中間和右側網格中。</span><span class="sxs-lookup"><span data-stu-id="447e0-201">After setting this anchor to the model, the moving cloud layers were then projected on the middle and right meshes seen below.</span></span>

![使用分隔的 shell 的木星物件總覽](images/ge-update-jupiter-shells-separated.jpg)

### <a name="texturing"></a><span data-ttu-id="447e0-203">繪製</span><span class="sxs-lookup"><span data-stu-id="447e0-203">Texturing</span></span>

<span data-ttu-id="447e0-204">現有材質已分成三個部分的材質, 如下所示:第三部裝載 motionless 的雲端層, 其中有間距可提供視差效果, 中間區段包含快速移動的外部資料流, 而第三個則包含緩慢旋轉的內部基底層。</span><span class="sxs-lookup"><span data-stu-id="447e0-204">The existing texture was separated into a three-part texture atlas: The upper third hosts a motionless layer of clouds with gaps to provide a parallax effect, the middle section contains the fast moving outer streams, and the lower third contains a slowly rotating inner base layer.</span></span>

<span data-ttu-id="447e0-205">特性良好的紅色點也會分成不同的移動部分, 然後插入材質的另一個不可見區域。</span><span class="sxs-lookup"><span data-stu-id="447e0-205">The characteristic Great Red Spot was also separated into its various moving parts and then inserted into an otherwise invisible area of the texture.</span></span> <span data-ttu-id="447e0-206">在下圖的中間區段中, 可以將這些元件視為紅色 toned speckles。</span><span class="sxs-lookup"><span data-stu-id="447e0-206">These components can be seen as the red-toned speckles in the middle section of the image below.</span></span>

<span data-ttu-id="447e0-207">因為每個寬線都有特定的方向和速度, 所以紋理會個別套用至每個網格。</span><span class="sxs-lookup"><span data-stu-id="447e0-207">Because each band has a specific direction and speed, the texture was applied to each mesh individually.</span></span> <span data-ttu-id="447e0-208">然後, 這些網格會有共同的中心和軸點, 以便 concentrically 整個表面的動畫。</span><span class="sxs-lookup"><span data-stu-id="447e0-208">The meshes then had a common center and pivot point, to be able to concentrically animate the whole surface.</span></span>

![木星材質總覽](images/ge-update-jupiter-planet-cloud-texture.png)

### <a name="rotation-and-texture-behavior"></a><span data-ttu-id="447e0-210">旋轉和材質行為</span><span class="sxs-lookup"><span data-stu-id="447e0-210">Rotation and texture behavior</span></span>

<span data-ttu-id="447e0-211">現在已設定了木星的視覺效果組合, 因此我們需要確保已適當地計算並套用旋轉和軌道速度。</span><span class="sxs-lookup"><span data-stu-id="447e0-211">Now that the visual composition of Jupiter was set, we needed to ensure that the rotation and orbit speeds were properly calculated and applied accordingly.</span></span> <span data-ttu-id="447e0-212">針對木星完成完整輪替需要大約9小時的時間。</span><span class="sxs-lookup"><span data-stu-id="447e0-212">It takes roughly 9 hours for Jupiter to complete a full rotation.</span></span> <span data-ttu-id="447e0-213">這是因為差異輪替而定義的。</span><span class="sxs-lookup"><span data-stu-id="447e0-213">This is a matter of definition due to its Differential Rotation.</span></span> <span data-ttu-id="447e0-214">因此, 赤道幾內亞資料流程已設定為「主要資料流程」, 以3600框架進行完整輪替。</span><span class="sxs-lookup"><span data-stu-id="447e0-214">Therefore the equatorial stream has been set as a 'master stream', taking 3600 frames for a full rotation.</span></span> <span data-ttu-id="447e0-215">其他每一層都必須以旋轉速度做為3600的因素, 才能符合其初始位置, 例如600、900、1200、1800等等。</span><span class="sxs-lookup"><span data-stu-id="447e0-215">Every other layer needed to have a rotational speed as a factor of 3600 in order to match its initial position, allowing e.g. 600, 900, 1200, 1800 etc.</span></span>

![木星 shell 紋理](images/ge-update-shell-texture.jpg)


### <a name="the-great-red-spot"></a><span data-ttu-id="447e0-217">絕佳的紅色點</span><span class="sxs-lookup"><span data-stu-id="447e0-217">The Great Red Spot</span></span>

<span data-ttu-id="447e0-218">個別旋轉的資料流程提供了良好的視覺效果, 但在接近範圍觀察到的情況下, 會有更詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="447e0-218">The individually rotating streams provided a good visual impression, but lacked in detail when observed at close range.</span></span>

<span data-ttu-id="447e0-219">最引人注目的部分是木星的絕佳紅色點, 因此我們建立了一組專門用來展示它的網格和紋理。</span><span class="sxs-lookup"><span data-stu-id="447e0-219">The most eye-catching part was Jupiter's Great Red Spot, so we created a set of meshes and textures specifically to showcase it.</span></span>
 
<span data-ttu-id="447e0-220">我們使用的機制類似于木星的波段: 一組旋轉的元件會在彼此之上組成, 同時也會在其「主要圖層」下分組, 以確保不論 rest 移動的速度為何, 它們都會保持在位置。</span><span class="sxs-lookup"><span data-stu-id="447e0-220">We used a similar mechanism as with Jupiter's bands: a set of rotating parts was composed on top of each other, while also being grouped under its 'master layer' to ensure they remain in position no matter how fast the rest moves.</span></span>

<span data-ttu-id="447e0-221">當網格已設定並備妥時, 會套用不同的 stormy vortex 層, 然後每個光碟會個別進行動畫, 而中間的片段則移動速度最快, 而其餘部分則會在移動時逐漸變慢。</span><span class="sxs-lookup"><span data-stu-id="447e0-221">When the meshes were set up and in place, different layers of the stormy vortex were applied and each disc was then animated individually, the center pieces moving fastest, with the rest progressively slowing down as it moving outwards.</span></span>

![木星絕佳的 Red 點網格](images/ge-update-great-red-spot-mesh.jpg)

<span data-ttu-id="447e0-223">組合也具有與每個其他網格相同的樞紐分析表, 同時也會從其原始 y 軸 (!) 中保持其傾斜效果, 以讓您自由地製作旋轉的動畫。</span><span class="sxs-lookup"><span data-stu-id="447e0-223">The composition also had the same pivot as every other mesh, while also keeping its tilt from its original y-axis (!) to allow freedom in animating the rotation.</span></span> <span data-ttu-id="447e0-224">3600框架是基本速率, 每個圖層都有這一段旋轉的因素。</span><span class="sxs-lookup"><span data-stu-id="447e0-224">3600 frames is the base rate, with each layer having a factor of this as a period of rotation.</span></span>

![木星絕佳的紅色點材質](images/ge-update-red-spot-mesh-texture.jpg)

### <a name="getting-it-right-in-unity"></a><span data-ttu-id="447e0-226">直接在 Unity 中取得</span><span class="sxs-lookup"><span data-stu-id="447e0-226">Getting it right in Unity</span></span>

<span data-ttu-id="447e0-227">在 Unity 中執行此動作時, 有幾個重要的事項要謹記在心。</span><span class="sxs-lookup"><span data-stu-id="447e0-227">There are a couple of key things to keep in mind when implementing this in Unity.</span></span>

<span data-ttu-id="447e0-228">在處理大型透明層組時, Unity 很容易混淆。</span><span class="sxs-lookup"><span data-stu-id="447e0-228">Unity is easily confused when dealing with large sets of transparent layers.</span></span> <span data-ttu-id="447e0-229">解決的方法是複製每個網格的材質材質, 並將遞增的轉譯佇列值從內部逐漸套用到外部, 每個資料。</span><span class="sxs-lookup"><span data-stu-id="447e0-229">The solution was to duplicate the texture material for each mesh and apply ascending Render Queue values progressively from the inner to the outer by 5 to each material.</span></span>

<span data-ttu-id="447e0-230">結果是內部命令介面的轉譯佇列值為 3000 (預設值), 而靜態 red toned outer 之後的值為 3005, 則快速的白色外部雲端會有3010。</span><span class="sxs-lookup"><span data-stu-id="447e0-230">The result was the inner shell had a Render Queue value of 3000 (default), the static red-toned outer later had a value of 3005, the fast white outer clouds had 3010.</span></span> <span data-ttu-id="447e0-231">很棒的紅色點 (從內部到外部層的進度) 已在此模型中完成, 值為3025。</span><span class="sxs-lookup"><span data-stu-id="447e0-231">The Great Red Spot (progressing from inner to outer layer), finished with a value of 3025 in this model.</span></span>

![木星最終物件](images/ge-update-jupiter-final.jpg)

### <a name="final-touches"></a><span data-ttu-id="447e0-233">最後的潤色</span><span class="sxs-lookup"><span data-stu-id="447e0-233">Final touches</span></span>

<span data-ttu-id="447e0-234">一開始會先設定多紋理的木星層級, 這證明會不足以進行執行。</span><span class="sxs-lookup"><span data-stu-id="447e0-234">The textured Jupiter layers were set up at first, which proved to be insufficient for implementation.</span></span>

<span data-ttu-id="447e0-235">原始的全球標準著色器 (及其所有變化) 會透過腳本 (SunLightReceiver) (MRTK 標準著色器不支援) 接收其光源資訊。</span><span class="sxs-lookup"><span data-stu-id="447e0-235">The original Planet Standard shader (and all of its variations) receive their lighting information via a script, the SunLightReceiver, which is not supported by the MRTK Standard shader.</span></span>

<span data-ttu-id="447e0-236">單純地交換著色器並不是一種解決方案, 因為地球標準著色器不支援具有透明度的材質對應。</span><span class="sxs-lookup"><span data-stu-id="447e0-236">Simply swapping the shaders wasn't a solution because the Planet Standard shader doesn't support texture maps with transparencies.</span></span> <span data-ttu-id="447e0-237">我們已編輯此著色器, 讓 Jupiter 組建能夠如預期執行。</span><span class="sxs-lookup"><span data-stu-id="447e0-237">We edited this shader in order to make the Jupiter build work as intended.</span></span>

<span data-ttu-id="447e0-238">最後, 您必須將來源 Blend 設定為 10, 並將目的地 Blend 設為 5, 以設定 Alpha 混合。</span><span class="sxs-lookup"><span data-stu-id="447e0-238">Finally the Alpha Blends needed to be set up by setting the Source Blend to 10 as well as the Destination Blend to 5.</span></span>

![木星 Unity 屬性](images/ge-update-jupiter-unity-render-queue.jpg)

<span data-ttu-id="447e0-240">您可以在 [Galaxy Explorer] 中查看木星的最終呈現!</span><span class="sxs-lookup"><span data-stu-id="447e0-240">You can see the final rendering of Jupiter in Galaxy Explorer!</span></span>

## <a name="meet-the-team"></a><span data-ttu-id="447e0-241">認識團隊</span><span class="sxs-lookup"><span data-stu-id="447e0-241">Meet the team</span></span> 

<span data-ttu-id="447e0-242">我們的 Mixed Reality studio 小組由設計人員、3D 演出者、UX 專家、開發人員、程式經理和 studio head 組成。</span><span class="sxs-lookup"><span data-stu-id="447e0-242">Our Mixed Reality studio team is made up of designers, 3D artists, UX specialists, developers, a program manager and a studio head.</span></span> <span data-ttu-id="447e0-243">我們會從世界各地 hail:比利時、加拿大、德國、以色列、日本、英國和美國。</span><span class="sxs-lookup"><span data-stu-id="447e0-243">We hail from all over the world: Belgium, Canada, Germany, Israel, Japan, the United Kingdom and the United States.</span></span> <span data-ttu-id="447e0-244">我們是來自不同背景的豐富團隊: 遊戲-傳統和獨立製作、數位行銷、醫療保健和科學。</span><span class="sxs-lookup"><span data-stu-id="447e0-244">We are a multidisciplinary team that comes from a diverse background: gaming - both traditional and indie, digital marketing, health care and science.</span></span>

<span data-ttu-id="447e0-245">我們很興奮地建立了 HoloLens 2 的 Galaxy Explorer, 並更新 HoloLens (第1代)、VR 和桌上出版本。</span><span class="sxs-lookup"><span data-stu-id="447e0-245">We are excited to create Galaxy Explorer for HoloLens 2, and to update the HoloLens (1st gen), VR and desktop versions.</span></span> 

![Galaxy Explorer 小組](images/ge-update-team-image.png)

<span data-ttu-id="447e0-247">從左上到右:Artemis Tsouflidou (開發人員)、Angie Teickner (視覺化設計工具)、David Janer (UX 設計工具)、劉娜 Garrett (傳遞 & 生產潛在客戶)、Yasushi Zonno (創意潛在客戶)、Eline Ledent (Developer) 和 Ben Turner (Sr-iov)。</span><span class="sxs-lookup"><span data-stu-id="447e0-247">On top from left to right: Artemis Tsouflidou (Developer), Angie Teickner (Visual Designer), David Janer (UX Designer), Laura Garrett (Delivery & Production Lead), Yasushi Zonno (Creative Lead), Eline Ledent (Developer) and Ben Turner (Sr. Developer).</span></span>
<span data-ttu-id="447e0-248">左下到右:Amit Rojtblat (技術演出者)、聖馬丁 Wettig (3D 演出者) 和 Dirk Songuer (Studio Head)。</span><span class="sxs-lookup"><span data-stu-id="447e0-248">Bottom from left to right: Amit Rojtblat (Technical Artist), Martin Wettig (3D Artist) and Dirk Songuer (Studio Head).</span></span>
<span data-ttu-id="447e0-249">未精選:Tim Gerken (技術組長) 和 Oscar Salandin (視覺化設計工具)。</span><span class="sxs-lookup"><span data-stu-id="447e0-249">Not featured: Tim Gerken (Tech Lead) and Oscar Salandin (Visual Designer).</span></span>

## <a name="additional-information"></a><span data-ttu-id="447e0-250">其他資訊</span><span class="sxs-lookup"><span data-stu-id="447e0-250">Additional information</span></span>

### <a name="mixed-reality-studios"></a><span data-ttu-id="447e0-251">混合現實工作室</span><span class="sxs-lookup"><span data-stu-id="447e0-251">Mixed Reality Studios</span></span>

<span data-ttu-id="447e0-252">Microsoft Mixed Reality Studio 團隊 (位於美國、歐洲和亞太地區) 是使用者經驗設計、全像電腦運算、AR/VR 技術和3D 開發的專家;包括3D 資產建立、DirectX、Unity 和 Unreal。</span><span class="sxs-lookup"><span data-stu-id="447e0-252">Microsoft Mixed Reality Studio teams - located in the Americas, Europe and Asia-Pacific - are experts in user experience design, holographic computing, AR/VR technologies, and 3D development; including 3D asset creation, DirectX, Unity and Unreal.</span></span> <span data-ttu-id="447e0-253">我們會協助想像所需的未來、設計、建立及交付解決方案, 同時讓客戶在其組織中建立可測量的影響。</span><span class="sxs-lookup"><span data-stu-id="447e0-253">We help envision desired futures, design, build and deliver solutions, while enabling customers to create measurable impact across their organization.</span></span> <span data-ttu-id="447e0-254">工作室與超過22000的 Microsoft 服務專業人員密切合作, 以進行企業應用程式整合、採用、作業和支援。</span><span class="sxs-lookup"><span data-stu-id="447e0-254">The studios work closely with over 22,000 Microsoft Services professionals for enterprise application integration, adoption, operations and support.</span></span>
