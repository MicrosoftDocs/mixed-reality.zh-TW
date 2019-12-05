---
title: 觀眾檢視
description: 將來自外部裝置的全像投影視覺化，作為在外部顯示器上示範混合實境體驗，或錄製混合實境體驗影片的方法。
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 觀眾檢視, iPhone, iOS, iPad, OpenCV, 相機, ARKit, HoloLens, 混合實境, MixedRealityToolkit, 示範, 錄製
ms.openlocfilehash: 9bc1c2809c7d780d439d9efb58f464b41de3dccd
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491168"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a><span data-ttu-id="44e4a-104">HoloLens 和 HoloLens 2 的觀眾檢視</span><span class="sxs-lookup"><span data-stu-id="44e4a-104">Spectator View for HoloLens and HoloLens 2</span></span>

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a><span data-ttu-id="44e4a-106">概觀</span><span class="sxs-lookup"><span data-stu-id="44e4a-106">Overview</span></span>

<span data-ttu-id="44e4a-107">戴上 HoloLens 時，我們通常會忘記沒有穿戴裝置的人無法體驗我們所體驗的奧妙。</span><span class="sxs-lookup"><span data-stu-id="44e4a-107">When wearing a HoloLens, we often forget that a person who does not have it on is unable to experience the wonders that we can.</span></span> <span data-ttu-id="44e4a-108">觀眾檢視可以讓其他人在 2D 螢幕上看到 HoloLens 使用者在他們的世界中所看到的內容。</span><span class="sxs-lookup"><span data-stu-id="44e4a-108">Spectator View allows others to see on a 2D screen what a HoloLens user sees in their world.</span></span>
<span data-ttu-id="44e4a-109">觀眾檢視提供快速且實惠的方法，讓您使用行動裝置以 HD 錄製全像投影。</span><span class="sxs-lookup"><span data-stu-id="44e4a-109">Spectator View offers a fast and affordable approach to recording holograms in HD with mobile devices.</span></span> <span data-ttu-id="44e4a-110">它也提供透過攝影機的全像投影專業品質錄影。</span><span class="sxs-lookup"><span data-stu-id="44e4a-110">It also offers a professional quality recording of holograms with video cameras.</span></span>

## <a name="key-resources"></a><span data-ttu-id="44e4a-111">主要資源</span><span class="sxs-lookup"><span data-stu-id="44e4a-111">Key Resources</span></span>

* [<span data-ttu-id="44e4a-112">**GitHub 上的觀眾檢視**</span><span class="sxs-lookup"><span data-stu-id="44e4a-112">**Spectator View on GitHub**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView)
* [<span data-ttu-id="44e4a-113">**觀眾檢視文件**</span><span class="sxs-lookup"><span data-stu-id="44e4a-113">**Spectator View Documentation**</span></span>](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [<span data-ttu-id="44e4a-114">**觀眾檢視範例**</span><span class="sxs-lookup"><span data-stu-id="44e4a-114">**Spectator View Samples**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a><span data-ttu-id="44e4a-115">使用案例</span><span class="sxs-lookup"><span data-stu-id="44e4a-115">Use Cases</span></span>
* <span data-ttu-id="44e4a-116">您可以使用 iPhone 或 Android 裝置錄製混合實境體驗。</span><span class="sxs-lookup"><span data-stu-id="44e4a-116">You can record a mixed reality experience using an iPhone or Android device.</span></span> <span data-ttu-id="44e4a-117">以 Full HD 錄製，對全像投影甚至是陰影套用消除鋸齒功能。</span><span class="sxs-lookup"><span data-stu-id="44e4a-117">Record in full HD and apply anti-aliasing to holograms and even shadows.</span></span> <span data-ttu-id="44e4a-118">這是擷取全像投影影片的符合成本效益且快速的方式。</span><span class="sxs-lookup"><span data-stu-id="44e4a-118">It is a cost-effective and quick way to capture video of holograms.</span></span>
* <span data-ttu-id="44e4a-119">直接從您的 iPhone 或 iPad 將即時混合實境體驗串流至 Apple TV，沒有延遲！</span><span class="sxs-lookup"><span data-stu-id="44e4a-119">Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
* <span data-ttu-id="44e4a-120">與來賓分享體驗：讓非 HoloLens 使用者直接從他們的手機或平板電腦體驗全像投影。</span><span class="sxs-lookup"><span data-stu-id="44e4a-120">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

## <a name="current-features"></a><span data-ttu-id="44e4a-121">目前的功能</span><span class="sxs-lookup"><span data-stu-id="44e4a-121">Current Features</span></span>

* <span data-ttu-id="44e4a-122">全像投影的空間同步處理，因此每個人都能在完全相同的位置看到全像投影。</span><span class="sxs-lookup"><span data-stu-id="44e4a-122">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
* <span data-ttu-id="44e4a-123">支援 iOS (已啟用 ARKit 的裝置) 和 Android (已啟用 ARCore 的裝置)。</span><span class="sxs-lookup"><span data-stu-id="44e4a-123">iOS (ARKit-enabled devices) and Android (ARCore-enabled devices) support.</span></span>
<span data-ttu-id="44e4a-124">多個 iOS 來賓。</span><span class="sxs-lookup"><span data-stu-id="44e4a-124">Multiple iOS guests.</span></span>
<span data-ttu-id="44e4a-125">影片錄製 + 全像投影 + 環境音效 + 全像投影音效。</span><span class="sxs-lookup"><span data-stu-id="44e4a-125">Recording of video + holograms + ambient sound + hologram sound.</span></span>
<span data-ttu-id="44e4a-126">共用工作表，讓您可以儲存影片、透過電子郵件傳送，或與其他支援的應用程式共用。</span><span class="sxs-lookup"><span data-stu-id="44e4a-126">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>

<span data-ttu-id="44e4a-127">![標記](images/SpecViewPhoneDemo.jpg)
![標記](images/hololensspectatorview-500px.jpg) ![標記](images/spectatorview-300px.png)</span><span class="sxs-lookup"><span data-stu-id="44e4a-127">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span></span>

<span data-ttu-id="44e4a-128">下表顯示不同的觀眾檢視功能及其功能。</span><span class="sxs-lookup"><span data-stu-id="44e4a-128">The following table shows different Spectator View functionality and their capabilities.</span></span> <span data-ttu-id="44e4a-129">選擇最適合您影片錄製需求的選項：</span><span class="sxs-lookup"><span data-stu-id="44e4a-129">Choose the option that best fits your video recording needs:</span></span>

|                                      | <span data-ttu-id="44e4a-130">行動裝置</span><span class="sxs-lookup"><span data-stu-id="44e4a-130">Mobile</span></span>                  |                    <span data-ttu-id="44e4a-131">攝影機</span><span class="sxs-lookup"><span data-stu-id="44e4a-131">Video Camera</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="44e4a-132">HD 品質</span><span class="sxs-lookup"><span data-stu-id="44e4a-132">HD quality</span></span>                           |         <span data-ttu-id="44e4a-133">Full HD</span><span class="sxs-lookup"><span data-stu-id="44e4a-133">Full HD</span></span>         |        <span data-ttu-id="44e4a-134">專業品質攝影 (由攝影機決定)</span><span class="sxs-lookup"><span data-stu-id="44e4a-134">Professional quality filming (as determined by video camera)</span></span>      |
| <span data-ttu-id="44e4a-135">簡易相機移動</span><span class="sxs-lookup"><span data-stu-id="44e4a-135">Easy camera movement</span></span>                 |            <span data-ttu-id="44e4a-136">✔</span><span class="sxs-lookup"><span data-stu-id="44e4a-136">✔</span></span>            |                      <span data-ttu-id="44e4a-137">✔</span><span class="sxs-lookup"><span data-stu-id="44e4a-137">✔</span></span>                      |
| <span data-ttu-id="44e4a-138">第三人稱視角</span><span class="sxs-lookup"><span data-stu-id="44e4a-138">Third-person view</span></span>                    |            <span data-ttu-id="44e4a-139">✔</span><span class="sxs-lookup"><span data-stu-id="44e4a-139">✔</span></span>            |                      <span data-ttu-id="44e4a-140">✔</span><span class="sxs-lookup"><span data-stu-id="44e4a-140">✔</span></span>                      |
| <span data-ttu-id="44e4a-141">可以串流至螢幕</span><span class="sxs-lookup"><span data-stu-id="44e4a-141">Can be streamed to screens</span></span>           |            <span data-ttu-id="44e4a-142">✔</span><span class="sxs-lookup"><span data-stu-id="44e4a-142">✔</span></span>            |                      <span data-ttu-id="44e4a-143">✔</span><span class="sxs-lookup"><span data-stu-id="44e4a-143">✔</span></span>                      |
| <span data-ttu-id="44e4a-144">可攜式</span><span class="sxs-lookup"><span data-stu-id="44e4a-144">Portable</span></span>                             |            <span data-ttu-id="44e4a-145">✔</span><span class="sxs-lookup"><span data-stu-id="44e4a-145">✔</span></span>            |                                             |
| <span data-ttu-id="44e4a-146">無線</span><span class="sxs-lookup"><span data-stu-id="44e4a-146">Wireless</span></span>                             |            <span data-ttu-id="44e4a-147">✔</span><span class="sxs-lookup"><span data-stu-id="44e4a-147">✔</span></span>            |                                             |
| <span data-ttu-id="44e4a-148">其他必要硬體</span><span class="sxs-lookup"><span data-stu-id="44e4a-148">Additional required hardware</span></span>         |     <span data-ttu-id="44e4a-149">Android 手機、iPhone</span><span class="sxs-lookup"><span data-stu-id="44e4a-149">Android phone, iPhone</span></span>    | <span data-ttu-id="44e4a-150">HoloLens + Rig + 三腳架 + 攝影機 + PC + Unity</span><span class="sxs-lookup"><span data-stu-id="44e4a-150">HoloLens + Rig + Tripod + Video Camera + PC + Unity</span></span> |
| <span data-ttu-id="44e4a-151">硬體投資</span><span class="sxs-lookup"><span data-stu-id="44e4a-151">Hardware investment</span></span>                  |           <span data-ttu-id="44e4a-152">低</span><span class="sxs-lookup"><span data-stu-id="44e4a-152">Low</span></span>            |                     <span data-ttu-id="44e4a-153">高</span><span class="sxs-lookup"><span data-stu-id="44e4a-153">High</span></span>                    |
| <span data-ttu-id="44e4a-154">跨平台</span><span class="sxs-lookup"><span data-stu-id="44e4a-154">Cross-platform</span></span>                       |           <span data-ttu-id="44e4a-155">Android、iOS</span><span class="sxs-lookup"><span data-stu-id="44e4a-155">Android, iOS</span></span>   |                                             |
| <span data-ttu-id="44e4a-156">同步處理的內容</span><span class="sxs-lookup"><span data-stu-id="44e4a-156">Synchronized content</span></span>                 |            <span data-ttu-id="44e4a-157">✔</span><span class="sxs-lookup"><span data-stu-id="44e4a-157">✔</span></span>            |                      <span data-ttu-id="44e4a-158">✔</span><span class="sxs-lookup"><span data-stu-id="44e4a-158">✔</span></span>                      |
| <span data-ttu-id="44e4a-159">執行階段安裝持續時間</span><span class="sxs-lookup"><span data-stu-id="44e4a-159">Runtime setup duration</span></span>               |         <span data-ttu-id="44e4a-160">立即</span><span class="sxs-lookup"><span data-stu-id="44e4a-160">Instant</span></span>          |                     <span data-ttu-id="44e4a-161">慢速</span><span class="sxs-lookup"><span data-stu-id="44e4a-161">Slow</span></span>                    |
## <a name="see-also"></a><span data-ttu-id="44e4a-162">請參閱</span><span class="sxs-lookup"><span data-stu-id="44e4a-162">See also</span></span>

* [<span data-ttu-id="44e4a-163">混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="44e4a-163">Mixed reality capture</span></span>](mixed-reality-capture.md) 
* [<span data-ttu-id="44e4a-164">適用於開發人員的混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="44e4a-164">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="44e4a-165">混合實境中的共用體驗</span><span class="sxs-lookup"><span data-stu-id="44e4a-165">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
