---
title: 聊天室掃描視覺效果
description: 需要空間的對應資料的應用程式依賴自動收集一段時間的這項資料的裝置，並以使用者的工作階段之間探索其環境與作用中裝置。
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，應用程式模式、 設計、 HoloLens、 聊天室掃描，空間的對應，介面重構，網格
ms.openlocfilehash: 09df4464ea4dac01dfad637886b07b861f468d4d
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829910"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="c241e-104">聊天室掃描視覺效果</span><span class="sxs-lookup"><span data-stu-id="c241e-104">Room scan visualization</span></span>

<span data-ttu-id="c241e-105">需要空間的對應資料的應用程式依賴自動收集一段時間的這項資料的裝置，並以使用者的工作階段之間探索其環境與作用中裝置。</span><span class="sxs-lookup"><span data-stu-id="c241e-105">Applications that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="c241e-106">完整性和品質的這項資料取決於許多因素，包括使用者已完成探勘數量、 瀏覽過多少時間，以及是否物件，例如 furniture 和機門已因為裝置掃描區域。</span><span class="sxs-lookup"><span data-stu-id="c241e-106">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="c241e-107">若要確保有用空間的對應資料，應用程式開發人員會有數個選項：</span><span class="sxs-lookup"><span data-stu-id="c241e-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="c241e-108">依賴功能可能已收集。</span><span class="sxs-lookup"><span data-stu-id="c241e-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="c241e-109">一開始這項資料可能會不完整。</span><span class="sxs-lookup"><span data-stu-id="c241e-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="c241e-110">要求使用者使用 bloom 筆勢來取得 Windows Mixed Reality 家用，然後瀏覽他們想要使用體驗的區域。</span><span class="sxs-lookup"><span data-stu-id="c241e-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="c241e-111">若要確認所有必要的區域已知的裝置，他們可以使用空中點選。</span><span class="sxs-lookup"><span data-stu-id="c241e-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="c241e-112">建置自訂的探索體驗，在他們自己的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="c241e-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="c241e-113">請注意，在所有這些情況下在探索期間蒐集的實際資料儲存系統應用程式不需要執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="c241e-113">Note that in all these cases the actual data gathered during the exploration is stored by the system and the application does not need to do this.</span></span>

## <a name="device-support"></a><span data-ttu-id="c241e-114">裝置支援</span><span class="sxs-lookup"><span data-stu-id="c241e-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c241e-115"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="c241e-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="c241e-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="c241e-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="c241e-117"><a href="immersive-headset-hardware-details.md"><strong>沈浸式耳機</strong></a></span><span class="sxs-lookup"><span data-stu-id="c241e-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c241e-118">聊天室掃描視覺效果</span><span class="sxs-lookup"><span data-stu-id="c241e-118">Room scan visualization</span></span></td>
        <td><span data-ttu-id="c241e-119">✔️</span><span class="sxs-lookup"><span data-stu-id="c241e-119">✔️</span></span></td>
        <td><span data-ttu-id="c241e-120">❌</span><span class="sxs-lookup"><span data-stu-id="c241e-120">❌</span></span></td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="c241e-121">建置自訂的掃描體驗</span><span class="sxs-lookup"><span data-stu-id="c241e-121">Building a custom scanning experience</span></span>

<span data-ttu-id="c241e-122">應用程式可能會決定要分析空間的對應資料，判斷他們是否想讓使用者執行其他步驟，以改善其完整性和品質經驗的開頭。</span><span class="sxs-lookup"><span data-stu-id="c241e-122">Applications may decide to analyze the spatial mapping data at the start of the experience to judge whether they want the user to perform additional steps to improve its completeness and quality.</span></span> <span data-ttu-id="c241e-123">如果分析指出應該改善品質，開發人員應該提供視覺效果，以指出世界上的覆疊：</span><span class="sxs-lookup"><span data-stu-id="c241e-123">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="c241e-124">在使用者附近的總磁碟區中有多少必須能夠體驗的一部分</span><span class="sxs-lookup"><span data-stu-id="c241e-124">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="c241e-125">使用者應該前往改善資料</span><span class="sxs-lookup"><span data-stu-id="c241e-125">Where the user should go to improve data</span></span>

<span data-ttu-id="c241e-126">使用者不知道如何成為 「 良好 」 的掃描。</span><span class="sxs-lookup"><span data-stu-id="c241e-126">Users do not know what makes a "good" scan.</span></span> <span data-ttu-id="c241e-127">他們需要顯示或告知要尋找的如果它們就必須評估掃描 – 扁平度，實際的牆、 從距離等等。開發人員應該實作的意見反應迴圈，其中包含重新整理掃描或瀏覽階段期間的空間的對應資料。</span><span class="sxs-lookup"><span data-stu-id="c241e-127">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, etc. The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="c241e-128">在許多情況下，可能是最理想的做法，告訴使用者他們需要執行 （例如查看最高限度，查看 furniture 後面），以取得必要的掃描品質。</span><span class="sxs-lookup"><span data-stu-id="c241e-128">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="c241e-129">快取與連續空間對應</span><span class="sxs-lookup"><span data-stu-id="c241e-129">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="c241e-130">空間對應的資料是資料來源的應用程式可以使用最高負載。</span><span class="sxs-lookup"><span data-stu-id="c241e-130">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="c241e-131">若要避免效能問題，例如畫面或間斷的情形，這項資料的耗用量必須小心執行。</span><span class="sxs-lookup"><span data-stu-id="c241e-131">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="c241e-132">作用中的掃描，體驗期間可以幫助或不利，開發人員必須決定要使用哪個方法經驗為基礎。</span><span class="sxs-lookup"><span data-stu-id="c241e-132">Active scanning during an experience can be both beneficial or detrimental and the developer will need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="c241e-133">快取空間的對應</span><span class="sxs-lookup"><span data-stu-id="c241e-133">Cached spatial mapping</span></span>

<span data-ttu-id="c241e-134">如果快取空間的對應，是應用程式，通常空間的對應資料的快照，並體驗的持續期間使用此快照集。</span><span class="sxs-lookup"><span data-stu-id="c241e-134">In the case of cached spatial mapping, the application typically takes a snapshot of the spatial mapping data and uses this snapshot for the duration of the experience.</span></span>

<span data-ttu-id="c241e-135">**權益**</span><span class="sxs-lookup"><span data-stu-id="c241e-135">**Benefits**</span></span>
* <span data-ttu-id="c241e-136">額外負荷降低系統上體驗大幅的乘冪，熱執行前置及 cpu 效能提升時。</span><span class="sxs-lookup"><span data-stu-id="c241e-136">Reduced overhead on the system while the experience is running leading to dramatic power, thermal and cpu performance gains.</span></span>
* <span data-ttu-id="c241e-137">主要的體驗，因為它不會因空間資料變更的簡單實作。</span><span class="sxs-lookup"><span data-stu-id="c241e-137">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="c241e-138">單一成本物理、 圖形和其他用途的空間資料的任何後續處理上一次。</span><span class="sxs-lookup"><span data-stu-id="c241e-138">A single one time cost on any post processing of the spatial data for physics, graphics and other purposes.</span></span>

<span data-ttu-id="c241e-139">**缺點**</span><span class="sxs-lookup"><span data-stu-id="c241e-139">**Drawbacks**</span></span>
* <span data-ttu-id="c241e-140">快取的資料不會反映的真實世界物件或人員的移動。</span><span class="sxs-lookup"><span data-stu-id="c241e-140">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="c241e-141">例如</span><span class="sxs-lookup"><span data-stu-id="c241e-141">E.g.</span></span> <span data-ttu-id="c241e-142">應用程式可能會考慮機門開啟實際上現在關閉時。</span><span class="sxs-lookup"><span data-stu-id="c241e-142">the application might consider a door open when it is actually closed now.</span></span>
* <span data-ttu-id="c241e-143">可能有更多應用程式的記憶體以維持資料的快取的版本。</span><span class="sxs-lookup"><span data-stu-id="c241e-143">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="c241e-144">理想的情況下，這個方法是受控制的環境或資料表頂端遊戲。</span><span class="sxs-lookup"><span data-stu-id="c241e-144">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="c241e-145">連續空間對應</span><span class="sxs-lookup"><span data-stu-id="c241e-145">Continuous spatial mapping</span></span>

<span data-ttu-id="c241e-146">特定的應用程式可能會依賴上會繼續掃描以重新整理空間對應的資料。</span><span class="sxs-lookup"><span data-stu-id="c241e-146">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="c241e-147">**權益**</span><span class="sxs-lookup"><span data-stu-id="c241e-147">**Benefits**</span></span>
* <span data-ttu-id="c241e-148">您不需要建置個別掃描或瀏覽體驗預先在您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c241e-148">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="c241e-149">遊戲時，可以反映的真實世界物件移動但仍會有一些延遲。</span><span class="sxs-lookup"><span data-stu-id="c241e-149">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="c241e-150">**缺點**</span><span class="sxs-lookup"><span data-stu-id="c241e-150">**Drawbacks**</span></span>
* <span data-ttu-id="c241e-151">主要的經驗的實作中較高的複雜性。</span><span class="sxs-lookup"><span data-stu-id="c241e-151">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="c241e-152">如圖形或物理做的變更需要以累加方式擷取這些系統的額外處理的潛在的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="c241e-152">Potential overhead of the additional processing for graphic or physics as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="c241e-153">較高的電源、 散熱和 CPU 衝擊。</span><span class="sxs-lookup"><span data-stu-id="c241e-153">Higher power, thermal and CPU impact.</span></span>

<span data-ttu-id="c241e-154">理想的情況下，這個方法會是其中一個互動移動物件，例如地板上的磁碟機可能會想要正確碰到取決於它是否已開啟或關閉門全像攝影版的汽車中有到全像投影。</span><span class="sxs-lookup"><span data-stu-id="c241e-154">A good case for this method is one where holograms are expected to interact with moving objects, e.g. a holographic car that drives on the floor may want to correctly bump into a door depending on whether it is open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="c241e-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c241e-155">See also</span></span>
* [<span data-ttu-id="c241e-156">空間對應設計</span><span class="sxs-lookup"><span data-stu-id="c241e-156">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="c241e-157">座標系統</span><span class="sxs-lookup"><span data-stu-id="c241e-157">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="c241e-158">空間音效設計</span><span class="sxs-lookup"><span data-stu-id="c241e-158">Spatial sound design</span></span>](spatial-sound-design.md)
