---
title: 房間掃描視覺效果
description: 需要空間對應資料的應用程式會依賴裝置，在使用者探索其在使用中裝置的環境時，于一段時間內自動收集此資料。
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，應用程式模式，設計，HoloLens，房間掃描，空間對應，網格
ms.openlocfilehash: bdb070407f27d04046bd022894c7a8a01b9658d1
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437521"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="5b85a-104">房間掃描視覺效果</span><span class="sxs-lookup"><span data-stu-id="5b85a-104">Room scan visualization</span></span>

<span data-ttu-id="5b85a-105">需要空間對應資料的應用程式會依賴裝置，在使用者探索其在使用中裝置的環境時，于一段時間內自動收集此資料。</span><span class="sxs-lookup"><span data-stu-id="5b85a-105">Applications that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="5b85a-106">此資料的完整性和品質取決於數個因素，包括使用者已完成的探索量、流覽後經過的時間，以及設備（例如傢俱和門）在掃描區域之後是否已移動。</span><span class="sxs-lookup"><span data-stu-id="5b85a-106">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="5b85a-107">為了確保有用的空間對應資料，應用程式開發人員有數個選項：</span><span class="sxs-lookup"><span data-stu-id="5b85a-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="5b85a-108">依賴可能已收集的內容。</span><span class="sxs-lookup"><span data-stu-id="5b85a-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="5b85a-109">此資料一開始可能不完整。</span><span class="sxs-lookup"><span data-stu-id="5b85a-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="5b85a-110">要求使用者使用 bloom 手勢來進入 Windows Mixed Reality home，然後探索他們想要用於體驗的領域。</span><span class="sxs-lookup"><span data-stu-id="5b85a-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="5b85a-111">他們可以使用 [按一下] 來確認裝置知道所有必要的區域。</span><span class="sxs-lookup"><span data-stu-id="5b85a-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="5b85a-112">在自己的應用程式中建立自訂探索體驗。</span><span class="sxs-lookup"><span data-stu-id="5b85a-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="5b85a-113">請注意，在這些情況下，探索期間所收集的實際資料會由系統儲存，而應用程式不需要這麼做。</span><span class="sxs-lookup"><span data-stu-id="5b85a-113">Note that in all these cases the actual data gathered during the exploration is stored by the system and the application does not need to do this.</span></span>

## <a name="device-support"></a><span data-ttu-id="5b85a-114">裝置支援</span><span class="sxs-lookup"><span data-stu-id="5b85a-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="5b85a-115"><strong>特徵</strong></span><span class="sxs-lookup"><span data-stu-id="5b85a-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="5b85a-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="5b85a-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="5b85a-117"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="5b85a-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="5b85a-118">房間掃描視覺效果</span><span class="sxs-lookup"><span data-stu-id="5b85a-118">Room scan visualization</span></span></td>
        <td><span data-ttu-id="5b85a-119">✔️</span><span class="sxs-lookup"><span data-stu-id="5b85a-119">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="5b85a-120">建立自訂掃描體驗</span><span class="sxs-lookup"><span data-stu-id="5b85a-120">Building a custom scanning experience</span></span>

<span data-ttu-id="5b85a-121">應用程式可能會決定在體驗開始時分析空間對應資料，以判斷他們是否想要讓使用者執行額外的步驟來改善其完整性和品質。</span><span class="sxs-lookup"><span data-stu-id="5b85a-121">Applications may decide to analyze the spatial mapping data at the start of the experience to judge whether they want the user to perform additional steps to improve its completeness and quality.</span></span> <span data-ttu-id="5b85a-122">如果分析指出應該改善品質，開發人員應該提供視覺效果以在世界上重迭，以指出：</span><span class="sxs-lookup"><span data-stu-id="5b85a-122">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="5b85a-123">使用者鄰近範圍中的總數量必須是經驗的一部分</span><span class="sxs-lookup"><span data-stu-id="5b85a-123">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="5b85a-124">使用者應該前往哪裡改善資料</span><span class="sxs-lookup"><span data-stu-id="5b85a-124">Where the user should go to improve data</span></span>

<span data-ttu-id="5b85a-125">使用者不知道什麼會進行「良好」掃描。</span><span class="sxs-lookup"><span data-stu-id="5b85a-125">Users do not know what makes a "good" scan.</span></span> <span data-ttu-id="5b85a-126">如果要求評估掃描– flatness、與實際牆的距離等等，則需要顯示或告訴您要尋找的內容。開發人員應執行意見反應迴圈，其中包括在掃描或流覽階段重新整理空間對應資料。</span><span class="sxs-lookup"><span data-stu-id="5b85a-126">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, etc. The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="5b85a-127">在許多情況下，最好告訴使用者需要執行的動作（例如，查看 [傢俱] 的上限），以便取得所需的掃描品質。</span><span class="sxs-lookup"><span data-stu-id="5b85a-127">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="5b85a-128">快取與連續空間對應</span><span class="sxs-lookup"><span data-stu-id="5b85a-128">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="5b85a-129">空間對應資料是最繁重的資料來源應用程式可使用的權數。</span><span class="sxs-lookup"><span data-stu-id="5b85a-129">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="5b85a-130">若要避免效能問題（例如，已卸載的框架或間斷情形），應該小心地取用此資料。</span><span class="sxs-lookup"><span data-stu-id="5b85a-130">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="5b85a-131">在體驗期間進行主動掃描可能會有好處或不利，而開發人員必須根據經驗決定要使用的方法。</span><span class="sxs-lookup"><span data-stu-id="5b85a-131">Active scanning during an experience can be both beneficial or detrimental and the developer will need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="5b85a-132">快取的空間對應</span><span class="sxs-lookup"><span data-stu-id="5b85a-132">Cached spatial mapping</span></span>

<span data-ttu-id="5b85a-133">在快取空間對應的情況下，應用程式通常會取得空間對應資料的快照，並在體驗期間使用此快照集。</span><span class="sxs-lookup"><span data-stu-id="5b85a-133">In the case of cached spatial mapping, the application typically takes a snapshot of the spatial mapping data and uses this snapshot for the duration of the experience.</span></span>

<span data-ttu-id="5b85a-134">**權益**</span><span class="sxs-lookup"><span data-stu-id="5b85a-134">**Benefits**</span></span>
* <span data-ttu-id="5b85a-135">降低系統的額外負荷，同時體驗會大幅提升電力、冷卻和 cpu 效能。</span><span class="sxs-lookup"><span data-stu-id="5b85a-135">Reduced overhead on the system while the experience is running leading to dramatic power, thermal and cpu performance gains.</span></span>
* <span data-ttu-id="5b85a-136">較簡單的主要體驗執行，因為空間資料的變更不會中斷。</span><span class="sxs-lookup"><span data-stu-id="5b85a-136">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="5b85a-137">針對物理、圖形和其他用途，針對空間資料的任何後置處理進行單一時間成本。</span><span class="sxs-lookup"><span data-stu-id="5b85a-137">A single one time cost on any post processing of the spatial data for physics, graphics and other purposes.</span></span>

<span data-ttu-id="5b85a-138">**缺陷**</span><span class="sxs-lookup"><span data-stu-id="5b85a-138">**Drawbacks**</span></span>
* <span data-ttu-id="5b85a-139">實際的物件或人員的移動不會反映在快取的資料上。</span><span class="sxs-lookup"><span data-stu-id="5b85a-139">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="5b85a-140">例如</span><span class="sxs-lookup"><span data-stu-id="5b85a-140">E.g.</span></span> <span data-ttu-id="5b85a-141">應用程式在實際關閉時，可能會將門視為已開啟。</span><span class="sxs-lookup"><span data-stu-id="5b85a-141">the application might consider a door open when it is actually closed now.</span></span>
* <span data-ttu-id="5b85a-142">可能會有更多應用程式記憶體來維護快取的資料版本。</span><span class="sxs-lookup"><span data-stu-id="5b85a-142">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="5b85a-143">這個方法有一個不錯的例子，就是受控制的環境或資料表最熱門的遊戲。</span><span class="sxs-lookup"><span data-stu-id="5b85a-143">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="5b85a-144">連續空間對應</span><span class="sxs-lookup"><span data-stu-id="5b85a-144">Continuous spatial mapping</span></span>

<span data-ttu-id="5b85a-145">某些應用程式可能會依賴繼續掃描以重新整理空間對應資料。</span><span class="sxs-lookup"><span data-stu-id="5b85a-145">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="5b85a-146">**權益**</span><span class="sxs-lookup"><span data-stu-id="5b85a-146">**Benefits**</span></span>
* <span data-ttu-id="5b85a-147">您不需要在應用程式中預先建立個別的掃描或探索體驗。</span><span class="sxs-lookup"><span data-stu-id="5b85a-147">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="5b85a-148">現實世界物件的移動可以由遊戲反映，但有一些延遲。</span><span class="sxs-lookup"><span data-stu-id="5b85a-148">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="5b85a-149">**缺陷**</span><span class="sxs-lookup"><span data-stu-id="5b85a-149">**Drawbacks**</span></span>
* <span data-ttu-id="5b85a-150">主要體驗的執行複雜度較高。</span><span class="sxs-lookup"><span data-stu-id="5b85a-150">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="5b85a-151">因為需要以累加方式內嵌這些系統的變更，所以圖形或物理的額外處理可能會產生額外負荷。</span><span class="sxs-lookup"><span data-stu-id="5b85a-151">Potential overhead of the additional processing for graphic or physics as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="5b85a-152">較高的電源、熱和 CPU 的影響。</span><span class="sxs-lookup"><span data-stu-id="5b85a-152">Higher power, thermal and CPU impact.</span></span>

<span data-ttu-id="5b85a-153">這種方法的理想情況是，其中的全息影像應該與移動物件互動，例如，地面驅動的全像攝影車，可能會想要根據它是開啟還是關閉來正確地增加到門中。</span><span class="sxs-lookup"><span data-stu-id="5b85a-153">A good case for this method is one where holograms are expected to interact with moving objects, e.g. a holographic car that drives on the floor may want to correctly bump into a door depending on whether it is open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="5b85a-154">請參閱</span><span class="sxs-lookup"><span data-stu-id="5b85a-154">See also</span></span>
* [<span data-ttu-id="5b85a-155">空間對應</span><span class="sxs-lookup"><span data-stu-id="5b85a-155">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="5b85a-156">座標系統</span><span class="sxs-lookup"><span data-stu-id="5b85a-156">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="5b85a-157">空間音效設計</span><span class="sxs-lookup"><span data-stu-id="5b85a-157">Spatial sound design</span></span>](spatial-sound-design.md)
