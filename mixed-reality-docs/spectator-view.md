---
title: Spectator 視圖
description: 將來自外部裝置的全息影像視覺化, 做為在外部顯示或錄製混合現實體驗的影片時, 展現混合現實體驗的方法。
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: Spectator View、iPhone、iOS、iPad、OpenCV、攝影機、ARKit、HoloLens、Mixed Reality、MixedRealityToolkit、示範、記錄
ms.openlocfilehash: 02088d7b218a25c72f2eb98ae24c85a90e6e5b86
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293611"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a><span data-ttu-id="0b1b2-104">HoloLens 和 HoloLens 2 的 Spectator 視圖</span><span class="sxs-lookup"><span data-stu-id="0b1b2-104">Spectator View for HoloLens and HoloLens 2</span></span>

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a><span data-ttu-id="0b1b2-106">總覽</span><span class="sxs-lookup"><span data-stu-id="0b1b2-106">Overview</span></span>

<span data-ttu-id="0b1b2-107">當您戴 HoloLens 時, 我們通常會忘記不具有該功能的人員無法體驗我們可以世界真奇妙的情況。</span><span class="sxs-lookup"><span data-stu-id="0b1b2-107">When wearing a HoloLens, we often forget that a person who does not have it on is unable to experience the wonders that we can.</span></span> <span data-ttu-id="0b1b2-108">Spectator View 可讓其他人在2D 螢幕上看到 HoloLens 使用者在世界中看到的內容。</span><span class="sxs-lookup"><span data-stu-id="0b1b2-108">Spectator View allows others to see on a 2D screen what a HoloLens user sees in their world.</span></span>
<span data-ttu-id="0b1b2-109">Spectator View 提供快速且實惠的方法, 讓您以行動裝置錄製 HD 中的全息影像。</span><span class="sxs-lookup"><span data-stu-id="0b1b2-109">Spectator View offers a fast and affordable approach to recording holograms in HD with mobile devices.</span></span> <span data-ttu-id="0b1b2-110">它也提供 DSLR 攝影機的全像攝影的專業品質錄影。</span><span class="sxs-lookup"><span data-stu-id="0b1b2-110">It also offers a professional quality recording of holograms with DSLR cameras.</span></span>

## <a name="key-resources"></a><span data-ttu-id="0b1b2-111">重要資源</span><span class="sxs-lookup"><span data-stu-id="0b1b2-111">Key Resources</span></span>

* [<span data-ttu-id="0b1b2-112">**GitHub 上的 Spectator 視圖**</span><span class="sxs-lookup"><span data-stu-id="0b1b2-112">**Spectator View on GitHub**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView)
* [<span data-ttu-id="0b1b2-113">**結構**</span><span class="sxs-lookup"><span data-stu-id="0b1b2-113">**Architecture**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Architecture.md)
* [<span data-ttu-id="0b1b2-114">**範例**</span><span class="sxs-lookup"><span data-stu-id="0b1b2-114">**Samples**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)
* [<span data-ttu-id="0b1b2-115">**行動設定指示**</span><span class="sxs-lookup"><span data-stu-id="0b1b2-115">**Mobile Setup Instructions**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Setup.md)
* [<span data-ttu-id="0b1b2-116">**DSLR 設定指示**</span><span class="sxs-lookup"><span data-stu-id="0b1b2-116">**DSLR Setup Instructions**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Setup.DSLR.md)

## <a name="use-cases"></a><span data-ttu-id="0b1b2-117">使用案例</span><span class="sxs-lookup"><span data-stu-id="0b1b2-117">Use Cases</span></span>
* <span data-ttu-id="0b1b2-118">您可以使用 iPhone 或 Android 裝置記錄混合現實體驗。</span><span class="sxs-lookup"><span data-stu-id="0b1b2-118">You can record a mixed reality experience using an iPhone or Android device.</span></span> <span data-ttu-id="0b1b2-119">以全 HD 記錄, 並將消除鋸齒功能套用到全息影像, 甚至是陰影。</span><span class="sxs-lookup"><span data-stu-id="0b1b2-119">Record in full HD and apply anti-aliasing to holograms and even shadows.</span></span> <span data-ttu-id="0b1b2-120">這是一種符合成本效益且快速的方式, 可讓您掌握全息影像的影片。</span><span class="sxs-lookup"><span data-stu-id="0b1b2-120">It is a cost-effective and quick way to capture video of holograms.</span></span>
* <span data-ttu-id="0b1b2-121">直接從您的 iPhone 或 iPad 將即時混合現實體驗串流至 Apple 電視, 並延後免費!</span><span class="sxs-lookup"><span data-stu-id="0b1b2-121">Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
* <span data-ttu-id="0b1b2-122">分享來賓的體驗:讓非 HoloLens 使用者直接從他們的手機或平板電腦體驗全息影像。</span><span class="sxs-lookup"><span data-stu-id="0b1b2-122">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

## <a name="current-features"></a><span data-ttu-id="0b1b2-123">目前的功能</span><span class="sxs-lookup"><span data-stu-id="0b1b2-123">Current Features</span></span>

* <span data-ttu-id="0b1b2-124">全息影像的空間同步處理, 因此每個人都能在完全相同的位置看到全像投影。</span><span class="sxs-lookup"><span data-stu-id="0b1b2-124">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
* <span data-ttu-id="0b1b2-125">iOS (啟用 ARKit 的裝置) 和 Android (啟用 ARCore 的裝置) 支援。</span><span class="sxs-lookup"><span data-stu-id="0b1b2-125">iOS (ARKit-enabled devices) and Android (ARCore-enabled devices) support.</span></span>
<span data-ttu-id="0b1b2-126">多個 iOS 來賓。</span><span class="sxs-lookup"><span data-stu-id="0b1b2-126">Multiple iOS guests.</span></span>
<span data-ttu-id="0b1b2-127">影片錄製 + 全像投影 + 環境音效 + 全息影像音效。</span><span class="sxs-lookup"><span data-stu-id="0b1b2-127">Recording of video + holograms + ambient sound + hologram sound.</span></span>
<span data-ttu-id="0b1b2-128">共用工作表, 讓您可以儲存影片、透過電子郵件傳送, 或與其他支援的應用程式共用。</span><span class="sxs-lookup"><span data-stu-id="0b1b2-128">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>

<span data-ttu-id="0b1b2-129">![](images/SpecViewPhoneDemo.jpg)
標記標記![標記](images/hololensspectatorview-500px.jpg) ![](images/spectatorview-300px.png)</span><span class="sxs-lookup"><span data-stu-id="0b1b2-129">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span></span>

<span data-ttu-id="0b1b2-130">下表顯示不同的 Spectator View 功能及其功能。</span><span class="sxs-lookup"><span data-stu-id="0b1b2-130">The following table shows different Spectator View functionality and their capabilities.</span></span> <span data-ttu-id="0b1b2-131">選擇最適合您影片錄製需求的選項:</span><span class="sxs-lookup"><span data-stu-id="0b1b2-131">Choose the option that best fits your video recording needs:</span></span>

|                                      | <span data-ttu-id="0b1b2-132">行動訊息</span><span class="sxs-lookup"><span data-stu-id="0b1b2-132">Mobile</span></span>                  |                    <span data-ttu-id="0b1b2-133">DSLR 攝影機</span><span class="sxs-lookup"><span data-stu-id="0b1b2-133">DSLR Camera</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="0b1b2-134">HD 品質</span><span class="sxs-lookup"><span data-stu-id="0b1b2-134">HD quality</span></span>                           |         <span data-ttu-id="0b1b2-135">全 HD</span><span class="sxs-lookup"><span data-stu-id="0b1b2-135">Full HD</span></span>         |        <span data-ttu-id="0b1b2-136">專業品質 filming (由 DSLR 決定)</span><span class="sxs-lookup"><span data-stu-id="0b1b2-136">Professional quality filming (as determined by DSLR)</span></span>      |
| <span data-ttu-id="0b1b2-137">輕鬆移動相機</span><span class="sxs-lookup"><span data-stu-id="0b1b2-137">Easy camera movement</span></span>                 |            <span data-ttu-id="0b1b2-138">✔</span><span class="sxs-lookup"><span data-stu-id="0b1b2-138">✔</span></span>            |                      <span data-ttu-id="0b1b2-139">✔</span><span class="sxs-lookup"><span data-stu-id="0b1b2-139">✔</span></span>                      |
| <span data-ttu-id="0b1b2-140">第三個人檢視</span><span class="sxs-lookup"><span data-stu-id="0b1b2-140">Third-person view</span></span>                    |            <span data-ttu-id="0b1b2-141">✔</span><span class="sxs-lookup"><span data-stu-id="0b1b2-141">✔</span></span>            |                      <span data-ttu-id="0b1b2-142">✔</span><span class="sxs-lookup"><span data-stu-id="0b1b2-142">✔</span></span>                      |
| <span data-ttu-id="0b1b2-143">可以串流至螢幕</span><span class="sxs-lookup"><span data-stu-id="0b1b2-143">Can be streamed to screens</span></span>           |            <span data-ttu-id="0b1b2-144">✔</span><span class="sxs-lookup"><span data-stu-id="0b1b2-144">✔</span></span>            |                      <span data-ttu-id="0b1b2-145">✔</span><span class="sxs-lookup"><span data-stu-id="0b1b2-145">✔</span></span>                      |
| <span data-ttu-id="0b1b2-146">台</span><span class="sxs-lookup"><span data-stu-id="0b1b2-146">Portable</span></span>                             |            <span data-ttu-id="0b1b2-147">✔</span><span class="sxs-lookup"><span data-stu-id="0b1b2-147">✔</span></span>            |                                             |
| <span data-ttu-id="0b1b2-148">無線</span><span class="sxs-lookup"><span data-stu-id="0b1b2-148">Wireless</span></span>                             |            <span data-ttu-id="0b1b2-149">✔</span><span class="sxs-lookup"><span data-stu-id="0b1b2-149">✔</span></span>            |                                             |
| <span data-ttu-id="0b1b2-150">其他必要的硬體</span><span class="sxs-lookup"><span data-stu-id="0b1b2-150">Additional required hardware</span></span>         |     <span data-ttu-id="0b1b2-151">Android 手機、iPhone</span><span class="sxs-lookup"><span data-stu-id="0b1b2-151">Android phone, iPhone</span></span>    | <span data-ttu-id="0b1b2-152">HoloLens + Rig + 架 + DSLR + PC + Unity</span><span class="sxs-lookup"><span data-stu-id="0b1b2-152">HoloLens + Rig + Tripod + DSLR + PC + Unity</span></span> |
| <span data-ttu-id="0b1b2-153">硬體投資</span><span class="sxs-lookup"><span data-stu-id="0b1b2-153">Hardware investment</span></span>                  |           <span data-ttu-id="0b1b2-154">低</span><span class="sxs-lookup"><span data-stu-id="0b1b2-154">Low</span></span>            |                     <span data-ttu-id="0b1b2-155">高</span><span class="sxs-lookup"><span data-stu-id="0b1b2-155">High</span></span>                    |
| <span data-ttu-id="0b1b2-156">跨平台</span><span class="sxs-lookup"><span data-stu-id="0b1b2-156">Cross-platform</span></span>                       |           <span data-ttu-id="0b1b2-157">Android、iOS</span><span class="sxs-lookup"><span data-stu-id="0b1b2-157">Android, iOS</span></span>   |                                             |
| <span data-ttu-id="0b1b2-158">已同步處理的內容</span><span class="sxs-lookup"><span data-stu-id="0b1b2-158">Synchronized content</span></span>                 |            <span data-ttu-id="0b1b2-159">✔</span><span class="sxs-lookup"><span data-stu-id="0b1b2-159">✔</span></span>            |                      <span data-ttu-id="0b1b2-160">✔</span><span class="sxs-lookup"><span data-stu-id="0b1b2-160">✔</span></span>                      |
| <span data-ttu-id="0b1b2-161">執行時間安裝期間</span><span class="sxs-lookup"><span data-stu-id="0b1b2-161">Runtime setup duration</span></span>               |         <span data-ttu-id="0b1b2-162">暫態</span><span class="sxs-lookup"><span data-stu-id="0b1b2-162">Instant</span></span>          |                     <span data-ttu-id="0b1b2-163">慢速</span><span class="sxs-lookup"><span data-stu-id="0b1b2-163">Slow</span></span>                    |
## <a name="see-also"></a><span data-ttu-id="0b1b2-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b1b2-164">See also</span></span>

* [<span data-ttu-id="0b1b2-165">混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="0b1b2-165">Mixed reality capture</span></span>](mixed-reality-capture.md) 
* [<span data-ttu-id="0b1b2-166">適用於開發人員的混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="0b1b2-166">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="0b1b2-167">混合實境中的共用體驗</span><span class="sxs-lookup"><span data-stu-id="0b1b2-167">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
