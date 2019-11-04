---
title: 案例研究-擴充 HoloLens 的空間對應功能
description: 建立 Microsoft HoloLens 的第一個應用程式時，我們正積極看到我們可以在裝置上推送空間對應界限的程度。
author: jevertt
ms.author: jemccull
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、空間對應
ms.openlocfilehash: 5142cb383d4408b29eb17eb5ede84d19b2533dc4
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436729"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a><span data-ttu-id="66ca0-104">案例研究-擴充 HoloLens 的空間對應功能</span><span class="sxs-lookup"><span data-stu-id="66ca0-104">Case study - Expanding the spatial mapping capabilities of HoloLens</span></span>

<span data-ttu-id="66ca0-105">建立 Microsoft HoloLens 的第一個應用程式時，我們正積極看到我們可以在裝置上推送空間對應界限的程度。</span><span class="sxs-lookup"><span data-stu-id="66ca0-105">When creating our first apps for Microsoft HoloLens, we were eager to see just how far we could push the boundaries of spatial mapping on the device.</span></span> <span data-ttu-id="66ca0-106">Jeff Evertt 是 Microsoft 工作室的軟體工程師，說明如何開發新的技術，以更充分掌控在使用者的真實世界環境中如何放置全息影像。</span><span class="sxs-lookup"><span data-stu-id="66ca0-106">Jeff Evertt, a software engineer at Microsoft Studios, explains how a new technology was developed out of the need for more control over how holograms are placed in a user's real-world environment.</span></span>

> [!NOTE]
> <span data-ttu-id="66ca0-107">HoloLens 2 實行新的[場景理解運行](scene-understanding.md)時間，為混合現實開發人員提供結構化的高階環境標記法，其設計目的是為了讓環保感知應用程式的開發更加直覺。</span><span class="sxs-lookup"><span data-stu-id="66ca0-107">HoloLens 2 implements a new [Scene Understanding Runtime](scene-understanding.md), that provides Mixed Reality developers with a structured, high-level environment representation designed to make developing for environmentally aware applications intuitive.</span></span> 

## <a name="watch-the-video"></a><span data-ttu-id="66ca0-108">觀看影片</span><span class="sxs-lookup"><span data-stu-id="66ca0-108">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a><span data-ttu-id="66ca0-109">超出空間對應</span><span class="sxs-lookup"><span data-stu-id="66ca0-109">Beyond spatial mapping</span></span>

<span data-ttu-id="66ca0-110">雖然我們正在處理[片段](https://www.microsoft.com/p/fragments/9nblggh5ggm8)和[年輕 Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1)，但我們發現 HoloLens 的第一場遊戲，在實際執行的是在實體世界中進行全息的程式化時，我們需要更深入瞭解使用者的環境.</span><span class="sxs-lookup"><span data-stu-id="66ca0-110">While we were working on [Fragments](https://www.microsoft.com/p/fragments/9nblggh5ggm8) and [Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), two of the first games for HoloLens, we found that when we were doing procedural placement of holograms in the physical world, we needed a higher level of understanding about the user's environment.</span></span> <span data-ttu-id="66ca0-111">每個遊戲都有自己特定的位置需求：在片段中，我們想要能夠區別不同的表面（例如樓層或資料表），以將線索放在相關的位置。</span><span class="sxs-lookup"><span data-stu-id="66ca0-111">Each game had its own specific placement needs: In Fragments, for example, we wanted to be able to distinguish between different surfaces—such as the floor or a table—to place clues in relevant locations.</span></span> <span data-ttu-id="66ca0-112">我們也想要能夠找出生活大小的全像是沙發或椅子的表面。</span><span class="sxs-lookup"><span data-stu-id="66ca0-112">We also wanted to be able to identify surfaces that life-size holographic characters could sit on, such as a couch or a chair.</span></span> <span data-ttu-id="66ca0-113">在年輕的 Conker 中，我們希望 Conker 和他的對手能夠在玩家的房間中，以平臺的形式使用凸起的表面。</span><span class="sxs-lookup"><span data-stu-id="66ca0-113">In Young Conker, we wanted Conker and his opponents to be able to use raised surfaces in a player's room as platforms.</span></span>

<span data-ttu-id="66ca0-114">[Asobo 工作室](https://www.asobostudio.com/index.html)是適用于這些遊戲的開發合作夥伴，面對這個問題所在，並建立了一項技術來擴充 HoloLens 的空間對應功能。</span><span class="sxs-lookup"><span data-stu-id="66ca0-114">[Asobo Studios](https://www.asobostudio.com/index.html), our development partner for these games, faced this problem head-on and created a technology that extends the spatial mapping capabilities of HoloLens.</span></span> <span data-ttu-id="66ca0-115">使用這種方式，我們可以分析玩家的房間，並找出牆、表格、椅子和樓層等表面。</span><span class="sxs-lookup"><span data-stu-id="66ca0-115">Using this, we could analyze a player's room and identify surfaces such as walls, tables, chairs, and floors.</span></span> <span data-ttu-id="66ca0-116">它也讓我們能夠優化一組條件約束，以判斷全像攝影物件的最佳位置。</span><span class="sxs-lookup"><span data-stu-id="66ca0-116">It also gave us the ability to optimize against a set of constraints to determine the best placement for holographic objects.</span></span>

## <a name="the-spatial-understanding-code"></a><span data-ttu-id="66ca0-117">空間理解程式碼</span><span class="sxs-lookup"><span data-stu-id="66ca0-117">The spatial understanding code</span></span>

<span data-ttu-id="66ca0-118">我們採用 Asobo 的原始程式碼，並建立封裝這項技術的程式庫。</span><span class="sxs-lookup"><span data-stu-id="66ca0-118">We took Asobo's original code and created a library that encapsulates this technology.</span></span> <span data-ttu-id="66ca0-119">Microsoft 和 Asobo 現已開放原始碼，並將其提供給[MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) ，供您在自己的專案中使用。</span><span class="sxs-lookup"><span data-stu-id="66ca0-119">Microsoft and Asobo have now open-sourced this code and made it available on [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) for you to use in your own projects.</span></span> <span data-ttu-id="66ca0-120">包含所有原始程式碼，讓您可以依據自己的需求進行自訂，並與您的社區分享您的改進。</span><span class="sxs-lookup"><span data-stu-id="66ca0-120">All the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="66ca0-121">此C++規劃求解的程式碼已包裝成 UWP DLL，並使用[包含在 MixedRealityToolkit 內的下拉式 Prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding)公開至 Unity。</span><span class="sxs-lookup"><span data-stu-id="66ca0-121">The code for the C++ solver has been wrapped into a UWP DLL and exposed to Unity with a [drop-in prefab contained within MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).</span></span>

<span data-ttu-id="66ca0-122">Unity 範例中包含許多有用的查詢，可讓您在牆上尋找空的空間、將物件放在最上方或較大的空間上、找出要放置的字元位置，以及其他許多空間理解查詢。</span><span class="sxs-lookup"><span data-stu-id="66ca0-122">There are many useful queries included in the Unity sample that will allow you to find empty spaces on walls, place objects on the ceiling or on large spaces on the floor, identify places for characters to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="66ca0-123">雖然 HoloLens 提供的空間對應解決方案的設計是為了符合整個範圍問題空間的需求，但空間理解模組是為了支援兩個特定遊戲的需求而打造。</span><span class="sxs-lookup"><span data-stu-id="66ca0-123">While the spatial mapping solution provided by HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="66ca0-124">因此，其解決方案的結構是以特定的程式和假設的集合為根據：</span><span class="sxs-lookup"><span data-stu-id="66ca0-124">As such, its solution is structured around a specific process and set of assumptions:</span></span>
* <span data-ttu-id="66ca0-125">**固定大小 playspace**：使用者指定 init 呼叫中的最大 playspace 大小。</span><span class="sxs-lookup"><span data-stu-id="66ca0-125">**Fixed size playspace**: The user specifies the maximum playspace size in the init call.</span></span>
* <span data-ttu-id="66ca0-126">單次掃描程式：此程式需要一**段**獨立的掃描階段，使用者會在此逐步解說，定義 playspace。</span><span class="sxs-lookup"><span data-stu-id="66ca0-126">**One-time scan process**: The process requires a discrete scanning phase where the user walks around, defining the playspace.</span></span> <span data-ttu-id="66ca0-127">在完成掃描之後，查詢函數才會運作。</span><span class="sxs-lookup"><span data-stu-id="66ca0-127">Query functions will not function until after the scan has been finalized.</span></span>
* <span data-ttu-id="66ca0-128">**使用者導向的 playspace 「繪製**」：在掃描階段，使用者會移動並尋找 playspace，有效地繪製應該包含的區域。</span><span class="sxs-lookup"><span data-stu-id="66ca0-128">**User driven playspace “painting”**: During the scanning phase, the user moves and looks around the playspace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="66ca0-129">產生的網格非常重要，可在此階段提供使用者意見反應。</span><span class="sxs-lookup"><span data-stu-id="66ca0-129">The generated mesh is important to provide user feedback during this phase.</span></span>
* <span data-ttu-id="66ca0-130">**室內家用或 office 安裝程式**：查詢函式是以適當角度針對平面和牆而設計的。</span><span class="sxs-lookup"><span data-stu-id="66ca0-130">**Indoors home or office setup**: The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="66ca0-131">這是一項軟性限制。</span><span class="sxs-lookup"><span data-stu-id="66ca0-131">This is a soft limitation.</span></span> <span data-ttu-id="66ca0-132">不過，在掃描階段，主要軸分析會完成，以優化主要和次要軸的網格鑲嵌。</span><span class="sxs-lookup"><span data-stu-id="66ca0-132">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="66ca0-133">房間掃描程式</span><span class="sxs-lookup"><span data-stu-id="66ca0-133">Room Scanning Process</span></span>

<span data-ttu-id="66ca0-134">當您載入空間理解模組時，您要做的第一件事就是掃描您的空間，如此一來，所有可用的表面（例如樓層、上限和牆）都會被識別和標示。</span><span class="sxs-lookup"><span data-stu-id="66ca0-134">When you load the spatial understanding module, the first thing you'll do is scan your space, so all the usable surfaces—such as the floor, ceiling, and walls—are identified and labeled.</span></span> <span data-ttu-id="66ca0-135">在掃描過程中，您會尋找您的聊天室，並「繪製」應該包含在掃描中的區域。</span><span class="sxs-lookup"><span data-stu-id="66ca0-135">During the scanning process, you look around your room and "paint' the areas that should be included in the scan.</span></span>

<span data-ttu-id="66ca0-136">在這個階段中看到的網格是一項很重要的視覺化意見反應，可讓使用者知道房間的哪些部分正在進行掃描。</span><span class="sxs-lookup"><span data-stu-id="66ca0-136">The mesh seen during this phase is an important piece of visual feedback that lets users know what parts of the room are being scanned.</span></span> <span data-ttu-id="66ca0-137">空間理解模組的 DLL 會在內部將 playspace 儲存為8cm 大小體素 cube 的方格。</span><span class="sxs-lookup"><span data-stu-id="66ca0-137">The DLL for the spatial understanding module internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="66ca0-138">在掃描的初始部分期間，主要元件分析會完成以判斷房間的軸。</span><span class="sxs-lookup"><span data-stu-id="66ca0-138">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="66ca0-139">就內部而言，它會儲存其對應至這些座標軸的體素空間。</span><span class="sxs-lookup"><span data-stu-id="66ca0-139">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="66ca0-140">從體素磁片區解壓縮 isosurface，大約每秒會產生一次網格。</span><span class="sxs-lookup"><span data-stu-id="66ca0-140">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span>

![空間對應網格（白色）和瞭解 playspace 網格（綠色）](images/spatial-mapping-500px.png)

<span data-ttu-id="66ca0-142">空間對應網格（白色）和瞭解 playspace 網格（綠色）</span><span class="sxs-lookup"><span data-stu-id="66ca0-142">Spatial mapping mesh in white and understanding playspace mesh in green</span></span>



<span data-ttu-id="66ca0-143">內含的 SpatialUnderstanding.cs 檔案會管理掃描階段程式。</span><span class="sxs-lookup"><span data-stu-id="66ca0-143">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="66ca0-144">它會呼叫下列函數：</span><span class="sxs-lookup"><span data-stu-id="66ca0-144">It calls the following functions:</span></span>
* <span data-ttu-id="66ca0-145">**SpatialUnderstanding_Init**：在開始時呼叫一次。</span><span class="sxs-lookup"><span data-stu-id="66ca0-145">**SpatialUnderstanding_Init**: Called once at the start.</span></span>
* <span data-ttu-id="66ca0-146">**GeneratePlayspace_InitScan**：表示掃描階段應開始。</span><span class="sxs-lookup"><span data-stu-id="66ca0-146">**GeneratePlayspace_InitScan**: Indicates that the scan phase should begin.</span></span>
* <span data-ttu-id="66ca0-147">**GeneratePlayspace_UpdateScan_DynamicScan**：呼叫每個畫面格，以更新掃描程式。</span><span class="sxs-lookup"><span data-stu-id="66ca0-147">**GeneratePlayspace_UpdateScan_DynamicScan**: Called each frame to update the scanning process.</span></span> <span data-ttu-id="66ca0-148">相機位置和方向會傳入，並用於 playspace 繪製進程，如上所述。</span><span class="sxs-lookup"><span data-stu-id="66ca0-148">The camera position and orientation is passed in and is used for the playspace painting process, described above.</span></span>
* <span data-ttu-id="66ca0-149">**GeneratePlayspace_RequestFinish**：呼叫以完成 playspace。</span><span class="sxs-lookup"><span data-stu-id="66ca0-149">**GeneratePlayspace_RequestFinish**: Called to finalize the playspace.</span></span> <span data-ttu-id="66ca0-150">這會使用掃描階段期間「已繪製」的區域來定義和鎖定 playspace。</span><span class="sxs-lookup"><span data-stu-id="66ca0-150">This will use the areas “painted” during the scan phase to define and lock the playspace.</span></span> <span data-ttu-id="66ca0-151">應用程式可以在掃描階段查詢統計資料，以及查詢自訂網格以提供使用者意見反應。</span><span class="sxs-lookup"><span data-stu-id="66ca0-151">The application can query statistics during the scanning phase as well as query the custom mesh for providing user feedback.</span></span>
* <span data-ttu-id="66ca0-152">**Import_UnderstandingMesh**：在掃描期間，模組所提供並放在「瞭解」 Prefab 的**SpatialUnderstandingCustomMesh**行為，會定期查詢進程所產生的自訂網格。</span><span class="sxs-lookup"><span data-stu-id="66ca0-152">**Import_UnderstandingMesh**: During scanning, the **SpatialUnderstandingCustomMesh** behavior provided by the module and placed on the understanding prefab will periodically query the custom mesh generated by the process.</span></span> <span data-ttu-id="66ca0-153">此外，這項作業會在完成掃描之後再進行一次。</span><span class="sxs-lookup"><span data-stu-id="66ca0-153">In addition, this is done once more after scanning has been finalized.</span></span>

<span data-ttu-id="66ca0-154">**SpatialUnderstanding**行為所驅動的掃描流程會呼叫**InitScan**，然後**UpdateScan**每個畫面格。</span><span class="sxs-lookup"><span data-stu-id="66ca0-154">The scanning flow, driven by the **SpatialUnderstanding** behavior calls **InitScan**, then **UpdateScan** each frame.</span></span> <span data-ttu-id="66ca0-155">當統計資料查詢報告合理的涵蓋範圍時，使用者可以 airtap 呼叫**RequestFinish**來表示掃描階段結束。</span><span class="sxs-lookup"><span data-stu-id="66ca0-155">When the statistics query reports reasonable coverage, the user can airtap to call **RequestFinish** to indicate the end of the scanning phase.</span></span> <span data-ttu-id="66ca0-156">**UpdateScan**會繼續呼叫，直到它的傳回值指出 DLL 已完成處理。</span><span class="sxs-lookup"><span data-stu-id="66ca0-156">**UpdateScan** continues to be called until it’s return value indicates that the DLL has completed processing.</span></span>

## <a name="the-queries"></a><span data-ttu-id="66ca0-157">查詢</span><span class="sxs-lookup"><span data-stu-id="66ca0-157">The queries</span></span>

<span data-ttu-id="66ca0-158">掃描完成之後，您將能夠在介面中存取三種不同類型的查詢：</span><span class="sxs-lookup"><span data-stu-id="66ca0-158">Once the scan is complete, you'll be able to access three different types of queries in the interface:</span></span>
* <span data-ttu-id="66ca0-159">**拓撲查詢**：這些是根據掃描聊天室拓撲的快速查詢。</span><span class="sxs-lookup"><span data-stu-id="66ca0-159">**Topology queries**: These are fast queries that are based on the topology of the scanned room.</span></span>
* <span data-ttu-id="66ca0-160">**成形查詢**：這些會利用拓撲查詢的結果來尋找與您定義的自訂圖形非常相符的水準表面。</span><span class="sxs-lookup"><span data-stu-id="66ca0-160">**Shape queries**: These utilize the results of your topology queries to find horizontal surfaces that are a good match to custom shapes that you define.</span></span>
* <span data-ttu-id="66ca0-161">**物件放置查詢**：這些是更複雜的查詢，可根據物件的一組規則和條件約束，尋找最適合的位置。</span><span class="sxs-lookup"><span data-stu-id="66ca0-161">**Object placement queries**: These are more complex queries that find the best-fit location based on a set of rules and constraints for the object.</span></span>

<span data-ttu-id="66ca0-162">除了三個主要查詢以外，還有一個 raycasting 介面可用來取出標記的表面類型，而自訂的防水室網格則可以複製出來。</span><span class="sxs-lookup"><span data-stu-id="66ca0-162">In addition to the three primary queries, there is a raycasting interface which can be used to retrieve tagged surface types and a custom watertight room mesh can be copied out.</span></span>

### <a name="topology-queries"></a><span data-ttu-id="66ca0-163">拓撲查詢</span><span class="sxs-lookup"><span data-stu-id="66ca0-163">Topology queries</span></span>

<span data-ttu-id="66ca0-164">在 DLL 中，拓撲管理員會處理環境的標籤。</span><span class="sxs-lookup"><span data-stu-id="66ca0-164">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="66ca0-165">如先前所述，大部分的資料會儲存在 surfels 中，並包含在體素磁片區中。</span><span class="sxs-lookup"><span data-stu-id="66ca0-165">As mentioned above, much of the data is stored within surfels, which are contained within a voxel volume.</span></span> <span data-ttu-id="66ca0-166">此外， **PlaySpaceInfos**結構是用來儲存 playspace 的相關資訊，包括世界對齊（更多詳細資料，如下所示）、樓層和上限高度。</span><span class="sxs-lookup"><span data-stu-id="66ca0-166">In addition, the **PlaySpaceInfos** structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span>

<span data-ttu-id="66ca0-167">啟發學習法是用來決定樓層、上限和牆。</span><span class="sxs-lookup"><span data-stu-id="66ca0-167">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="66ca0-168">例如，具有大於1個 m2 介面區的最大和最低水準表面會視為樓層。</span><span class="sxs-lookup"><span data-stu-id="66ca0-168">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="66ca0-169">請注意，在掃描過程中的相機路徑也會在此程式中使用。</span><span class="sxs-lookup"><span data-stu-id="66ca0-169">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="66ca0-170">拓撲管理員所公開的查詢子集會透過 DLL 公開。</span><span class="sxs-lookup"><span data-stu-id="66ca0-170">A subset of the queries exposed by the Topology manager are exposed out through the DLL.</span></span> <span data-ttu-id="66ca0-171">公開的拓撲查詢如下所示：</span><span class="sxs-lookup"><span data-stu-id="66ca0-171">The exposed topology queries are as follows:</span></span>
* <span data-ttu-id="66ca0-172">QueryTopology_FindPositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="66ca0-172">QueryTopology_FindPositionsOnWalls</span></span>
* <span data-ttu-id="66ca0-173">QueryTopology_FindLargePositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="66ca0-173">QueryTopology_FindLargePositionsOnWalls</span></span>
* <span data-ttu-id="66ca0-174">QueryTopology_FindLargestWall</span><span class="sxs-lookup"><span data-stu-id="66ca0-174">QueryTopology_FindLargestWall</span></span>
* <span data-ttu-id="66ca0-175">QueryTopology_FindPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="66ca0-175">QueryTopology_FindPositionsOnFloor</span></span>
* <span data-ttu-id="66ca0-176">QueryTopology_FindLargestPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="66ca0-176">QueryTopology_FindLargestPositionsOnFloor</span></span>
* <span data-ttu-id="66ca0-177">QueryTopology_FindPositionsSittable</span><span class="sxs-lookup"><span data-stu-id="66ca0-177">QueryTopology_FindPositionsSittable</span></span>

<span data-ttu-id="66ca0-178">每個查詢都有一組參數，特定于查詢類型。</span><span class="sxs-lookup"><span data-stu-id="66ca0-178">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="66ca0-179">在下列範例中，使用者會指定所需磁片區的最小高度 & 寬度、樓層上方的最小放置高度，以及該磁片區前方的最小間隙量。</span><span class="sxs-lookup"><span data-stu-id="66ca0-179">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="66ca0-180">所有的測量單位都是計量。</span><span class="sxs-lookup"><span data-stu-id="66ca0-180">All measurements are in meters.</span></span>




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="66ca0-181">這些查詢都會接受預先配置的**TopologyResult**結構陣列。</span><span class="sxs-lookup"><span data-stu-id="66ca0-181">Each of these queries takes a pre-allocated array of **TopologyResult** structures.</span></span> <span data-ttu-id="66ca0-182">**LocationCount**參數會指定傳入陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="66ca0-182">The **locationCount** parameter specifies the length of the passed-in array.</span></span> <span data-ttu-id="66ca0-183">傳回值會報告傳回位置的數目。</span><span class="sxs-lookup"><span data-stu-id="66ca0-183">The return value reports the number of returned locations.</span></span> <span data-ttu-id="66ca0-184">這個數位絕不會大於傳入的**locationCount**參數。</span><span class="sxs-lookup"><span data-stu-id="66ca0-184">This number is never greater than the passed-in **locationCount** parameter.</span></span>

<span data-ttu-id="66ca0-185">**TopologyResult**包含所傳回之磁片區的中心位置、面向的方向（也就是一般），以及所找到空間的尺寸。</span><span class="sxs-lookup"><span data-stu-id="66ca0-185">The **TopologyResult** contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

<span data-ttu-id="66ca0-186">請注意，在 Unity 範例中，每個查詢都會連結到虛擬 UI 面板中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="66ca0-186">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="66ca0-187">範例會將這些查詢的參數硬編碼成合理的值。</span><span class="sxs-lookup"><span data-stu-id="66ca0-187">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="66ca0-188">如需更多範例，請參閱範例程式碼中的*SpaceVisualizer.cs* 。</span><span class="sxs-lookup"><span data-stu-id="66ca0-188">See *SpaceVisualizer.cs* in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="66ca0-189">圖形查詢</span><span class="sxs-lookup"><span data-stu-id="66ca0-189">Shape queries</span></span>

<span data-ttu-id="66ca0-190">在 DLL 內，「圖形分析器」（**ShapeAnalyzer_W**）會使用「拓撲分析器」比對使用者所定義的自訂圖形。</span><span class="sxs-lookup"><span data-stu-id="66ca0-190">Inside of the DLL, the shape analyzer (**ShapeAnalyzer_W**) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="66ca0-191">Unity 範例具有一組預先定義的圖形，會顯示在 [圖形] 索引標籤上的 [查詢] 功能表中。</span><span class="sxs-lookup"><span data-stu-id="66ca0-191">The Unity sample has a pre-defined set of shapes which are shown in the query menu, on the shape tab.</span></span>

<span data-ttu-id="66ca0-192">請注意，圖形分析僅適用于水準表面。</span><span class="sxs-lookup"><span data-stu-id="66ca0-192">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="66ca0-193">例如，沙發是由平面上表面和沙發的平面上方所定義。</span><span class="sxs-lookup"><span data-stu-id="66ca0-193">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="66ca0-194">圖形查詢會尋找指定大小、高度和外觀範圍的兩個表面，並對齊並連接兩個表面。</span><span class="sxs-lookup"><span data-stu-id="66ca0-194">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="66ca0-195">使用 Api 詞彙，沙發基座和沙發背面是圖形元件，而對齊需求是圖形元件條件約束。</span><span class="sxs-lookup"><span data-stu-id="66ca0-195">Using the APIs terminology, the couch seat and the top of the back of the couch are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="66ca0-196">在 Unity 範例（**ShapeDefinition.cs**）中定義的範例查詢，適用于 "sittable" 物件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="66ca0-196">An example query defined in the Unity sample (**ShapeDefinition.cs**), for “sittable” objects is as follows:</span></span>




```
shapeComponents = new List<ShapeComponent>()
     {
          new ShapeComponent(
               new List<ShapeComponentConstraint>()
               {
                    ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
                    ShapeComponentConstraint.Create_SurfaceCount_Min(1),
                    ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
               }),
     };
     AddShape("Sittable", shapeComponents);
```

<span data-ttu-id="66ca0-197">每個形狀查詢都是由一組圖形元件所定義，每個都有一組元件條件約束和一組圖形條件約束，以列出元件之間的相依性。</span><span class="sxs-lookup"><span data-stu-id="66ca0-197">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which lists dependencies between the components.</span></span> <span data-ttu-id="66ca0-198">這個範例包含單一元件定義中的三個條件約束，而且元件之間沒有任何圖形條件約束（因為只有一個元件）。</span><span class="sxs-lookup"><span data-stu-id="66ca0-198">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="66ca0-199">相反地，「沙發」圖形有兩個「圖形」元件和四個「形狀」條件約束。</span><span class="sxs-lookup"><span data-stu-id="66ca0-199">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="66ca0-200">請注意，元件是由使用者的元件清單中的索引所識別（在此範例中為0和1）。</span><span class="sxs-lookup"><span data-stu-id="66ca0-200">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

<span data-ttu-id="66ca0-201">Unity 模組中提供了包裝函式，可讓您輕鬆地建立自訂圖形定義。</span><span class="sxs-lookup"><span data-stu-id="66ca0-201">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="66ca0-202">元件和圖形條件約束的完整清單可在**ShapeComponentConstraint**和**ShapeConstraint**結構內的**SpatialUnderstandingDll.cs**中找到。</span><span class="sxs-lookup"><span data-stu-id="66ca0-202">The full list of component and shape constraints can be found in **SpatialUnderstandingDll.cs** within the **ShapeComponentConstraint** and the **ShapeConstraint** structures.</span></span>

![藍色矩形會反白顯示「椅子圖形」查詢的結果。](images/chair-shape-query-500px.png)

<span data-ttu-id="66ca0-204">藍色矩形會反白顯示「椅子圖形」查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="66ca0-204">The blue rectangle highlights the results of the chair shape query.</span></span>



### <a name="object-placement-solver"></a><span data-ttu-id="66ca0-205">物件放置規劃求解</span><span class="sxs-lookup"><span data-stu-id="66ca0-205">Object placement solver</span></span>

<span data-ttu-id="66ca0-206">物件放置查詢可以用來識別實體空間中的理想位置，以放置您的物件。</span><span class="sxs-lookup"><span data-stu-id="66ca0-206">Object placement queries can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="66ca0-207">在指定物件規則和條件約束的情況下，此規劃求解會尋找最適合的位置。</span><span class="sxs-lookup"><span data-stu-id="66ca0-207">The solver will find the best-fit location given the object rules and constraints.</span></span> <span data-ttu-id="66ca0-208">此外，物件查詢會持續存在，直到使用**Solver_RemoveObject**或**Solver_RemoveAllObjects**呼叫移除物件為止，允許受限制的多物件放置。</span><span class="sxs-lookup"><span data-stu-id="66ca0-208">In addition, object queries persist until the object is removed with **Solver_RemoveObject** or **Solver_RemoveAllObjects** calls, allowing constrained multi-object placement.</span></span>

<span data-ttu-id="66ca0-209">物件放置查詢包含三個部分：具有參數的放置類型、規則清單和條件約束清單。</span><span class="sxs-lookup"><span data-stu-id="66ca0-209">Object placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="66ca0-210">若要執行查詢，請使用下列 API：</span><span class="sxs-lookup"><span data-stu-id="66ca0-210">To run a query, use the following API:</span></span>




```
public static int Solver_PlaceObject(
                [In] string objectName,
                [In] IntPtr placementDefinition,    // ObjectPlacementDefinition
                [In] int placementRuleCount,
                [In] IntPtr placementRules,         // ObjectPlacementRule
                [In] int constraintCount,
                [In] IntPtr placementConstraints,   // ObjectPlacementConstraint
                [Out] IntPtr placementResult)
```
<span data-ttu-id="66ca0-211">此函式會接受物件名稱、位置定義，以及規則和條件約束的清單。</span><span class="sxs-lookup"><span data-stu-id="66ca0-211">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="66ca0-212">包裝C#函式提供了結構協助程式函式，讓規則和條件約束結構更輕鬆。</span><span class="sxs-lookup"><span data-stu-id="66ca0-212">The C# wrappers provide construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="66ca0-213">放置定義包含查詢類型，也就是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="66ca0-213">The placement definition contains the query type — that is, one of the following:</span></span>




```
public enum PlacementType
                {
                    Place_OnFloor,
                    Place_OnWall,
                    Place_OnCeiling,
                    Place_OnShape,
                    Place_OnEdge,
                    Place_OnFloorAndCeiling,
                    Place_RandomInAir,
                    Place_InMidAir,
                    Place_UnderFurnitureEdge,
                };
```

<span data-ttu-id="66ca0-214">每個放置類型都具有類型特有的一組參數。</span><span class="sxs-lookup"><span data-stu-id="66ca0-214">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="66ca0-215">**ObjectPlacementDefinition**結構包含一組用來建立這些定義的靜態 helper 函式。</span><span class="sxs-lookup"><span data-stu-id="66ca0-215">The **ObjectPlacementDefinition** structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="66ca0-216">例如，若要尋找將物件放在樓層的位置，您可以使用下列函數：</span><span class="sxs-lookup"><span data-stu-id="66ca0-216">For example, to find a place to put an object on the floor, you can use the following function:</span></span> 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

<span data-ttu-id="66ca0-217">除了放置類型之外，您還可以提供一組規則和條件約束。</span><span class="sxs-lookup"><span data-stu-id="66ca0-217">In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="66ca0-218">無法違反規則。</span><span class="sxs-lookup"><span data-stu-id="66ca0-218">Rules cannot be violated.</span></span> <span data-ttu-id="66ca0-219">接著，符合類型和規則的可能位置位置會根據條件約束的集合進行優化，以選取最佳的放置位置。</span><span class="sxs-lookup"><span data-stu-id="66ca0-219">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints to select the optimal placement location.</span></span> <span data-ttu-id="66ca0-220">每個規則和條件約束都可以由提供的靜態建立函式來建立。</span><span class="sxs-lookup"><span data-stu-id="66ca0-220">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="66ca0-221">以下提供範例規則和條件約束結構函數。</span><span class="sxs-lookup"><span data-stu-id="66ca0-221">An example rule and constraint construction function is provided below.</span></span>




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="66ca0-222">下面的物件放置查詢會尋找一個位置，將半計量 cube 放在表面的邊緣，而不是從其他先前放置的物件，靠近房間的中心。</span><span class="sxs-lookup"><span data-stu-id="66ca0-222">The object placement query below is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>




```
List<ObjectPlacementRule> rules = 
          new List<ObjectPlacementRule>() {
               ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
          };

     List<ObjectPlacementConstraint> constraints = 
          new List<ObjectPlacementConstraint> {
               ObjectPlacementConstraint.Create_NearCenter(),
          };

     Solver_PlaceObject(
          “MyCustomObject”,
          new ObjectPlacementDefinition.Create_OnEdge(
          new Vector3(0.25f, 0.25f, 0.25f), 
          new Vector3(0.25f, 0.25f, 0.25f)),
          rules.Count,
          UnderstandingDLL.PinObject(rules.ToArray()),
          constraints.Count,
          UnderstandingDLL.PinObject(constraints.ToArray()),
          UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

<span data-ttu-id="66ca0-223">如果成功，則會傳回包含放置位置、維度和方向的**ObjectPlacementResult**結構。</span><span class="sxs-lookup"><span data-stu-id="66ca0-223">If successful, an **ObjectPlacementResult** structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="66ca0-224">此外，放置會加入至 DLL 的已放置物件的內部清單。</span><span class="sxs-lookup"><span data-stu-id="66ca0-224">In addition, the placement is added to the DLL’s internal list of placed objects.</span></span> <span data-ttu-id="66ca0-225">後續的放置查詢將會將此物件列入考慮。</span><span class="sxs-lookup"><span data-stu-id="66ca0-225">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="66ca0-226">Unity 範例中的**LevelSolver.cs**檔案包含更多範例查詢。</span><span class="sxs-lookup"><span data-stu-id="66ca0-226">The **LevelSolver.cs** file in the Unity sample contains more example queries.</span></span>

![藍色方塊會顯示三個位置查詢的結果，其中包含「遠離相機位置」規則。](images/away-from-camera-position-500px.png)

<span data-ttu-id="66ca0-228">藍色方塊會顯示三個位置查詢的結果，其中包含「遠離相機位置」規則。</span><span class="sxs-lookup"><span data-stu-id="66ca0-228">The blue boxes show the result from three Place On Floor queries with "away from camera position" rules.</span></span>


<span data-ttu-id="66ca0-229">**各種**</span><span class="sxs-lookup"><span data-stu-id="66ca0-229">**Tips:**</span></span>
* <span data-ttu-id="66ca0-230">解決層級或應用程式案例所需之多個物件的放置位置時，首先要解決不可或缺和大型的物件，以最大化找出空間的機率。</span><span class="sxs-lookup"><span data-stu-id="66ca0-230">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects to maximize the probability that a space can be found.</span></span>
* <span data-ttu-id="66ca0-231">放置順序很重要。</span><span class="sxs-lookup"><span data-stu-id="66ca0-231">Placement order is important.</span></span> <span data-ttu-id="66ca0-232">如果找不到物件位置，請嘗試較不受限制的設定。</span><span class="sxs-lookup"><span data-stu-id="66ca0-232">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="66ca0-233">具有一組回溯設定對於跨多個房間設定支援功能非常重要。</span><span class="sxs-lookup"><span data-stu-id="66ca0-233">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="66ca0-234">光線轉換</span><span class="sxs-lookup"><span data-stu-id="66ca0-234">Ray casting</span></span>

<span data-ttu-id="66ca0-235">除了三個主要查詢以外，光線轉型介面可以用來抓取已標記的表面型別，而自訂的防水 playspace 網格可以在掃描完房間之後複製出來，而標籤則會在內部為表面產生，如下圖所示：樓層、上限和牆。</span><span class="sxs-lookup"><span data-stu-id="66ca0-235">In addition to the three primary queries, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="66ca0-236">**PlayspaceRaycast**函式會採用光線，並在光線與已知表面衝突時傳回，如果是，則會傳回該介面的相關資訊（以**RaycastResult**的形式呈現）。</span><span class="sxs-lookup"><span data-stu-id="66ca0-236">The **PlayspaceRaycast** function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a **RaycastResult**.</span></span> 


```
struct RaycastResult
     {
          enum SurfaceTypes
          {
               Invalid, // No intersection
               Other,
               Floor,
               FloorLike,         // Not part of the floor topology, 
                                  //     but close to the floor and looks like the floor
               Platform,          // Horizontal platform between the ground and 
                                  //     the ceiling
               Ceiling,
               WallExternal,
               WallLike,          // Not part of the external wall surface, 
                                  //     but vertical surface that looks like a 
                                  //    wall structure
               };
               SurfaceTypes SurfaceType;
               float SurfaceArea;   // Zero if unknown 
                                        //  (i.e. if not part of the topology analysis)
               DirectX::XMFLOAT3 IntersectPoint;
               DirectX::XMFLOAT3 IntersectNormal;
     };
```

<span data-ttu-id="66ca0-237">就內部而言，會針對 playspace 的計算8cm 立方體素標記法來計算 raycast。</span><span class="sxs-lookup"><span data-stu-id="66ca0-237">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="66ca0-238">每個體素都包含一組具有已處理拓撲資料的 surface 元素（也稱為 surfels）。</span><span class="sxs-lookup"><span data-stu-id="66ca0-238">Each voxel contains a set of surface elements with processed topology data (also known as surfels).</span></span> <span data-ttu-id="66ca0-239">交集的體素資料格內所包含的 surfels 會進行比較，並使用最符合的方式來查閱拓撲資訊。</span><span class="sxs-lookup"><span data-stu-id="66ca0-239">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="66ca0-240">此拓撲資料包含以**SurfaceTypes**列舉的形式傳回的標籤，以及交集資料表面的介面區。</span><span class="sxs-lookup"><span data-stu-id="66ca0-240">This topology data contains the labeling returned in the form of the **SurfaceTypes** enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="66ca0-241">在 Unity 範例中，游標會將光線轉換成每個畫面格。</span><span class="sxs-lookup"><span data-stu-id="66ca0-241">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="66ca0-242">首先，針對 Unity 的 colliders;第二，針對瞭解模組的世界標記法;最後，針對 UI 元素。</span><span class="sxs-lookup"><span data-stu-id="66ca0-242">First, against Unity’s colliders; second, against the understanding module’s world representation; and finally, against the UI elements.</span></span> <span data-ttu-id="66ca0-243">在此應用程式中，UI 會取得優先順序，然後是瞭解結果，最後是 Unity 的 colliders。</span><span class="sxs-lookup"><span data-stu-id="66ca0-243">In this application, UI gets priority, then the understanding result, and finally, Unity’s colliders.</span></span> <span data-ttu-id="66ca0-244">**SurfaceType**會回報為游標旁的文字。</span><span class="sxs-lookup"><span data-stu-id="66ca0-244">The **SurfaceType** is reported as text next to the cursor.</span></span>

![Raycast 與樓層的結果報告交集。](images/raycast-result-500px.jpg)

<span data-ttu-id="66ca0-246">Raycast 與樓層的結果報告交集。</span><span class="sxs-lookup"><span data-stu-id="66ca0-246">Raycast result reporting intersection with the floor.</span></span>


## <a name="get-the-code"></a><span data-ttu-id="66ca0-247">取得程式碼</span><span class="sxs-lookup"><span data-stu-id="66ca0-247">Get the code</span></span>

<span data-ttu-id="66ca0-248">[MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)中提供開放原始碼程式碼。</span><span class="sxs-lookup"><span data-stu-id="66ca0-248">The open-source code is available in [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span></span> <span data-ttu-id="66ca0-249">如果您使用專案中的程式碼，請在[HoloLens 開發人員論壇](https://forums.hololens.com/)上讓我們知道。</span><span class="sxs-lookup"><span data-stu-id="66ca0-249">Let us know on the [HoloLens Developer Forums](https://forums.hololens.com/) if you use the code in a project.</span></span> <span data-ttu-id="66ca0-250">我們無法等您瞭解如何處理！</span><span class="sxs-lookup"><span data-stu-id="66ca0-250">We can't wait to see what you do with it!</span></span>

## <a name="about-the-author"></a><span data-ttu-id="66ca0-251">關於作者</span><span class="sxs-lookup"><span data-stu-id="66ca0-251">About the author</span></span>

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <span data-ttu-id="66ca0-252"><b>Jeff Evertt</b>是一家從 incubation 到經驗開發以來，曾經開始使用 HoloLens 的軟體工程組長。</span><span class="sxs-lookup"><span data-stu-id="66ca0-252"><b>Jeff Evertt</b> is a software engineering lead who has worked on HoloLens since the early days, from incubation to experience development.</span></span> <span data-ttu-id="66ca0-253">在 HoloLens 之前，他曾在各種平臺和遊戲的 Xbox Kinect 和遊戲產業中工作。</span><span class="sxs-lookup"><span data-stu-id="66ca0-253">Before HoloLens, he worked on the Xbox Kinect and in the games industry on a wide variety of platforms and games.</span></span> <span data-ttu-id="66ca0-254">Jeff 的熱衷於是關於機器人、圖形和亮色燈的問題。</span><span class="sxs-lookup"><span data-stu-id="66ca0-254">Jeff is passionate about robotics, graphics, and things with flashy lights that go beep.</span></span> <span data-ttu-id="66ca0-255">他喜歡學習新事物，以及處理軟體、硬體，尤其是在這兩個交集的空間中。</span><span class="sxs-lookup"><span data-stu-id="66ca0-255">He enjoys learning new things and working on software, hardware, and particularly in the space where the two intersect.</span></span></td>
</tr>
</table>



## <a name="see-also"></a><span data-ttu-id="66ca0-256">請參閱</span><span class="sxs-lookup"><span data-stu-id="66ca0-256">See also</span></span>
* [<span data-ttu-id="66ca0-257">空間對應</span><span class="sxs-lookup"><span data-stu-id="66ca0-257">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="66ca0-258">場景理解</span><span class="sxs-lookup"><span data-stu-id="66ca0-258">Scene understanding</span></span>](scene-understanding.md)
* [<span data-ttu-id="66ca0-259">空間位置掃描視覺效果</span><span class="sxs-lookup"><span data-stu-id="66ca0-259">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="66ca0-260">MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="66ca0-260">MixedRealityToolkit-Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="66ca0-261">Asobo Studio： HoloLens 開發第一線的課程</span><span class="sxs-lookup"><span data-stu-id="66ca0-261">Asobo Studio: Lessons from the frontline of HoloLens development</span></span>](https://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
