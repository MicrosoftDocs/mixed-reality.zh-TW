---
title: 案例研究-擴展 HoloLens 空間對應功能
description: 當建立我們的第一個應用程式的 Microsoft HoloLens，我們想要看到我們可以就遠推送空間對應的界限在裝置上。
author: jevertt
ms.author: jevertt
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，HoloLens，空間對應
ms.openlocfilehash: 602b629afa5900ff34c28b3a3a32725af06590b7
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595755"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a><span data-ttu-id="fa7cf-104">案例研究-擴展 HoloLens 空間對應功能</span><span class="sxs-lookup"><span data-stu-id="fa7cf-104">Case study - Expanding the spatial mapping capabilities of HoloLens</span></span>

<span data-ttu-id="fa7cf-105">當建立我們的第一個應用程式的 Microsoft HoloLens，我們想要看到我們可以就遠推送空間對應的界限在裝置上。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-105">When creating our first apps for Microsoft HoloLens, we were eager to see just how far we could push the boundaries of spatial mapping on the device.</span></span> <span data-ttu-id="fa7cf-106">Jeff Evertt，Microsoft Studios 的軟體工程師會說明如何從需要更充分掌控全像投影會放在使用者的實際操作環境的方式開發新的技術。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-106">Jeff Evertt, a software engineer at Microsoft Studios, explains how a new technology was developed out of the need for more control over how holograms are placed in a user's real-world environment.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="fa7cf-107">觀看影片</span><span class="sxs-lookup"><span data-stu-id="fa7cf-107">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a><span data-ttu-id="fa7cf-108">超出空間對應</span><span class="sxs-lookup"><span data-stu-id="fa7cf-108">Beyond spatial mapping</span></span>

<span data-ttu-id="fa7cf-109">雖然我們已努力[片段](https://www.microsoft.com/p/fragments/9nblggh5ggm8)並[Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1)、 兩個 HoloLens 的第一個遊戲，我們發現當我們的全像投影在真實世界的程序位置，我們需要更高的層級了解使用者的環境。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-109">While we were working on [Fragments](https://www.microsoft.com/p/fragments/9nblggh5ggm8) and [Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), two of the first games for HoloLens, we found that when we were doing procedural placement of holograms in the physical world, we needed a higher level of understanding about the user's environment.</span></span> <span data-ttu-id="fa7cf-110">每個遊戲都有它自己的特定位置需求：片段，比方說，我們想要能夠區分不同的介面 — 例如最低限度值或資料表，將相關的位置中的線索。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-110">Each game had its own specific placement needs: In Fragments, for example, we wanted to be able to distinguish between different surfaces—such as the floor or a table—to place clues in relevant locations.</span></span> <span data-ttu-id="fa7cf-111">我們也想要能夠識別介面，例如沙發或椅子，坐 life-size 全像攝影版的字元。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-111">We also wanted to be able to identify surfaces that life-size holographic characters could sit on, such as a couch or a chair.</span></span> <span data-ttu-id="fa7cf-112">在 Young Conker 我們想 Conker 和他的對手，若要能夠在玩家的房間內引發的介面作為平台。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-112">In Young Conker, we wanted Conker and his opponents to be able to use raised surfaces in a player's room as platforms.</span></span>

<span data-ttu-id="fa7cf-113">[Asobo Studios](http://www.asobostudio.com/index.html)，適用於這些遊戲中，我們開發的合作夥伴來解決標題面臨這個問題，並建立擴充的 HoloLens 空間的對應功能的技術。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-113">[Asobo Studios](http://www.asobostudio.com/index.html), our development partner for these games, faced this problem head-on and created a technology that extends the spatial mapping capabilities of HoloLens.</span></span> <span data-ttu-id="fa7cf-114">使用這種情況，我們就可以分析玩家的空間，並識別介面，例如牆壁、 資料表、 椅子和樓層。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-114">Using this, we could analyze a player's room and identify surfaces such as walls, tables, chairs, and floors.</span></span> <span data-ttu-id="fa7cf-115">它也讓我們能夠最佳化對一組條件約束，來判斷最佳放置全像攝影版的物件。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-115">It also gave us the ability to optimize against a set of constraints to determine the best placement for holographic objects.</span></span>

## <a name="the-spatial-understanding-code"></a><span data-ttu-id="fa7cf-116">空間的了解程式碼</span><span class="sxs-lookup"><span data-stu-id="fa7cf-116">The spatial understanding code</span></span>

<span data-ttu-id="fa7cf-117">我們花了 Asobo 的原始程式碼，並建立封裝這項技術的文件庫。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-117">We took Asobo's original code and created a library that encapsulates this technology.</span></span> <span data-ttu-id="fa7cf-118">Microsoft Asobo 現在開放原始碼這段程式碼，以及擁有上開放[MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping)供您使用您自己的專案中。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-118">Microsoft and Asobo have now open-sourced this code and made it available on [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) for you to use in your own projects.</span></span> <span data-ttu-id="fa7cf-119">所有的原始程式碼，會包含可讓您根據您的需求進行自訂，並與社群分享您的增強功能。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-119">All the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="fa7cf-120">程式碼C++已經包裝成 UWP DLL 並公開至 Unity 中使用求解[掉落 prefab 內含 MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding)。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-120">The code for the C++ solver has been wrapped into a UWP DLL and exposed to Unity with a [drop-in prefab contained within MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).</span></span>

<span data-ttu-id="fa7cf-121">有許多有用的查詢包含在 Unity 範例可讓您尋找在牆上的空白空間，將物件放上或在地板上的大型空間上，找出的字元坐著和各種其他空間的了解查詢的位置。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-121">There are many useful queries included in the Unity sample that will allow you to find empty spaces on walls, place objects on the ceiling or on large spaces on the floor, identify places for characters to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="fa7cf-122">雖然 HoloLens 所提供的空間對應解決方案設計為泛型程度足以符合完整的問題空間一系列的需求，以支援的兩個特定的遊戲需要建置空間的了解模組。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-122">While the spatial mapping solution provided by HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="fa7cf-123">因此，其解決方案被圍繞的特定處理程序和假設組：</span><span class="sxs-lookup"><span data-stu-id="fa7cf-123">As such, its solution is structured around a specific process and set of assumptions:</span></span>
* <span data-ttu-id="fa7cf-124">**固定大小 playspace**:使用者初始呼叫中指定的最大 playspace 大小。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-124">**Fixed size playspace**: The user specifies the maximum playspace size in the init call.</span></span>
* <span data-ttu-id="fa7cf-125">**單次掃描處理序**:此程序需要離散掃描的階段的使用者將周圍的引導，定義 playspace。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-125">**One-time scan process**: The process requires a discrete scanning phase where the user walks around, defining the playspace.</span></span> <span data-ttu-id="fa7cf-126">掃描已完成之後，查詢函數將不會運作之前。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-126">Query functions will not function until after the scan has been finalized.</span></span>
* <span data-ttu-id="fa7cf-127">**使用者導向 playspace"繪圖"**:在掃描階段中，使用者會移動，並尋找周圍 playspace，有效地繪製應該包含的區域。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-127">**User driven playspace “painting”**: During the scanning phase, the user moves and looks around the playspace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="fa7cf-128">產生的網狀結構，務必在這個階段期間提供使用者意見反應。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-128">The generated mesh is important to provide user feedback during this phase.</span></span>
* <span data-ttu-id="fa7cf-129">**室內住家或辦公室安裝**:查詢函式被專為一般的介面及背景牆直角。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-129">**Indoors home or office setup**: The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="fa7cf-130">這是軟性限制。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-130">This is a soft limitation.</span></span> <span data-ttu-id="fa7cf-131">不過，在掃描階段中，主座標軸分析會完成最佳化網狀結構鑲嵌式主要和次要軸。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-131">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="fa7cf-132">聊天室掃描程序</span><span class="sxs-lookup"><span data-stu-id="fa7cf-132">Room Scanning Process</span></span>

<span data-ttu-id="fa7cf-133">當您載入的空間的了解模組時，您將會的先掃描您的空間，因此，所有可用的介面 — 例如 floor、 ceiling 和牆，識別出並標示為。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-133">When you load the spatial understanding module, the first thing you'll do is scan your space, so all the usable surfaces—such as the floor, ceiling, and walls—are identified and labeled.</span></span> <span data-ttu-id="fa7cf-134">在掃描過程中，您看一下您的會議室和 「 小畫家 ' 應該在掃描中包含的區域。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-134">During the scanning process, you look around your room and "paint' the areas that should be included in the scan.</span></span>

<span data-ttu-id="fa7cf-135">在這個階段期間看到網格就是聊天室的一項重要的視覺回饋，可讓使用者知道正被掃描的哪些部分。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-135">The mesh seen during this phase is an important piece of visual feedback that lets users know what parts of the room are being scanned.</span></span> <span data-ttu-id="fa7cf-136">空間的了解模組 DLL 在內部儲存 playspace，以調整大小的 8 cm voxel cube 的方格。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-136">The DLL for the spatial understanding module internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="fa7cf-137">在掃描的初始部分，主要元件分析完成來決定座標軸的聊天室。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-137">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="fa7cf-138">就內部而言，它會儲存這些軸對齊其 voxel 空間。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-138">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="fa7cf-139">網格會產生大約每秒擷取 isosurface voxel 磁碟區。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-139">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span>

![空間對應以白色的網狀結構和了解 playspace mesh 中綠色](images/spatial-mapping-500px.png)

<span data-ttu-id="fa7cf-141">空間對應以白色的網狀結構和了解 playspace mesh 中綠色</span><span class="sxs-lookup"><span data-stu-id="fa7cf-141">Spatial mapping mesh in white and understanding playspace mesh in green</span></span>



<span data-ttu-id="fa7cf-142">包含的 SpatialUnderstanding.cs 檔案管理掃描階段的程序。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-142">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="fa7cf-143">它會呼叫下列函數：</span><span class="sxs-lookup"><span data-stu-id="fa7cf-143">It calls the following functions:</span></span>
* <span data-ttu-id="fa7cf-144">**SpatialUnderstanding_Init**:在開始時，請呼叫一次。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-144">**SpatialUnderstanding_Init**: Called once at the start.</span></span>
* <span data-ttu-id="fa7cf-145">**GeneratePlayspace_InitScan**:指出應該開始掃描階段。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-145">**GeneratePlayspace_InitScan**: Indicates that the scan phase should begin.</span></span>
* <span data-ttu-id="fa7cf-146">**GeneratePlayspace_UpdateScan_DynamicScan**:每個畫面呼叫來更新掃描程序。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-146">**GeneratePlayspace_UpdateScan_DynamicScan**: Called each frame to update the scanning process.</span></span> <span data-ttu-id="fa7cf-147">鏡頭位置和方向傳遞，且用於 playspace 繪製程序，上面所述。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-147">The camera position and orientation is passed in and is used for the playspace painting process, described above.</span></span>
* <span data-ttu-id="fa7cf-148">**GeneratePlayspace_RequestFinish**:呼叫以完成 playspace。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-148">**GeneratePlayspace_RequestFinish**: Called to finalize the playspace.</span></span> <span data-ttu-id="fa7cf-149">這將使用 「 繪製 「 掃描階段期間的區域，以定義並鎖定 playspace。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-149">This will use the areas “painted” during the scan phase to define and lock the playspace.</span></span> <span data-ttu-id="fa7cf-150">應用程式可以查詢統計資料期間掃描階段，以及查詢自訂的網狀結構，提供使用者意見反應。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-150">The application can query statistics during the scanning phase as well as query the custom mesh for providing user feedback.</span></span>
* <span data-ttu-id="fa7cf-151">**Import_UnderstandingMesh**:在掃描期間， **SpatialUnderstandingCustomMesh**模組所提供，並放在了解 prefab 的行為會定期查詢自訂處理序所產生的網格。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-151">**Import_UnderstandingMesh**: During scanning, the **SpatialUnderstandingCustomMesh** behavior provided by the module and placed on the understanding prefab will periodically query the custom mesh generated by the process.</span></span> <span data-ttu-id="fa7cf-152">此外，這是一次之後掃描已完成。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-152">In addition, this is done once more after scanning has been finalized.</span></span>

<span data-ttu-id="fa7cf-153">掃描流程，由驅動**SpatialUnderstanding**行為會呼叫**InitScan**，然後**UpdateScan**每個畫面格。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-153">The scanning flow, driven by the **SpatialUnderstanding** behavior calls **InitScan**, then **UpdateScan** each frame.</span></span> <span data-ttu-id="fa7cf-154">當統計資料的查詢報告合理的涵蓋範圍時，使用者可以呼叫 airtap **RequestFinish**表示 「 掃描 」 階段的結束。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-154">When the statistics query reports reasonable coverage, the user can airtap to call **RequestFinish** to indicate the end of the scanning phase.</span></span> <span data-ttu-id="fa7cf-155">**UpdateScan**呼叫傳回之前會繼續值會指出 DLL 已完成處理。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-155">**UpdateScan** continues to be called until it’s return value indicates that the DLL has completed processing.</span></span>

## <a name="the-queries"></a><span data-ttu-id="fa7cf-156">查詢</span><span class="sxs-lookup"><span data-stu-id="fa7cf-156">The queries</span></span>

<span data-ttu-id="fa7cf-157">掃描完成之後，您將能夠存取的介面中查詢的三種不同類型：</span><span class="sxs-lookup"><span data-stu-id="fa7cf-157">Once the scan is complete, you'll be able to access three different types of queries in the interface:</span></span>
* <span data-ttu-id="fa7cf-158">**拓撲查詢**:這些是房間的快速掃描的拓撲為基礎的查詢。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-158">**Topology queries**: These are fast queries that are based on the topology of the scanned room.</span></span>
* <span data-ttu-id="fa7cf-159">**圖形查詢**:這些會利用拓撲查詢來尋找水平的介面，會以您定義的自訂圖形完全相符的結果。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-159">**Shape queries**: These utilize the results of your topology queries to find horizontal surfaces that are a good match to custom shapes that you define.</span></span>
* <span data-ttu-id="fa7cf-160">**物件放置查詢**:這些是更複雜的查詢尋找一組規則和條件約束的物件為基礎的自動調整的位置。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-160">**Object placement queries**: These are more complex queries that find the best-fit location based on a set of rules and constraints for the object.</span></span>

<span data-ttu-id="fa7cf-161">除了三個主要的查詢，raycasting 介面可用來擷取已加上標記的介面型別和自訂 watertight 聊天室網格可以複製出來。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-161">In addition to the three primary queries, there is a raycasting interface which can be used to retrieve tagged surface types and a custom watertight room mesh can be copied out.</span></span>

### <a name="topology-queries"></a><span data-ttu-id="fa7cf-162">查詢拓撲</span><span class="sxs-lookup"><span data-stu-id="fa7cf-162">Topology queries</span></span>

<span data-ttu-id="fa7cf-163">Dll 拓樸管理員會處理環境的標記。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-163">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="fa7cf-164">如先前所述，大部分的資料會儲存在 surfels，內含 voxel 磁碟區。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-164">As mentioned above, much of the data is stored within surfels, which are contained within a voxel volume.</span></span> <span data-ttu-id="fa7cf-165">颾魤 ㄛ **PlaySpaceInfos**結構用來儲存 playspace，包括 world 對齊 （下文詳細資料）、 floor、 ceiling 高度與相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-165">In addition, the **PlaySpaceInfos** structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span>

<span data-ttu-id="fa7cf-166">啟發學習法用於決定 floor、 ceiling 和牆。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-166">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="fa7cf-167">比方說，有超過 1 m2 介面區的最大值與最低的水平的介面會被視為最低限度值。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-167">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="fa7cf-168">請注意，在掃描程序期間的相機路徑也會在此程序。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-168">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="fa7cf-169">子集拓樸管理員所公開的查詢會透過 DLL 公開出。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-169">A subset of the queries exposed by the Topology manager are exposed out through the DLL.</span></span> <span data-ttu-id="fa7cf-170">公開的拓樸查詢如下所示：</span><span class="sxs-lookup"><span data-stu-id="fa7cf-170">The exposed topology queries are as follows:</span></span>
* <span data-ttu-id="fa7cf-171">QueryTopology_FindPositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="fa7cf-171">QueryTopology_FindPositionsOnWalls</span></span>
* <span data-ttu-id="fa7cf-172">QueryTopology_FindLargePositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="fa7cf-172">QueryTopology_FindLargePositionsOnWalls</span></span>
* <span data-ttu-id="fa7cf-173">QueryTopology_FindLargestWall</span><span class="sxs-lookup"><span data-stu-id="fa7cf-173">QueryTopology_FindLargestWall</span></span>
* <span data-ttu-id="fa7cf-174">QueryTopology_FindPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="fa7cf-174">QueryTopology_FindPositionsOnFloor</span></span>
* <span data-ttu-id="fa7cf-175">QueryTopology_FindLargestPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="fa7cf-175">QueryTopology_FindLargestPositionsOnFloor</span></span>
* <span data-ttu-id="fa7cf-176">QueryTopology_FindPositionsSittable</span><span class="sxs-lookup"><span data-stu-id="fa7cf-176">QueryTopology_FindPositionsSittable</span></span>

<span data-ttu-id="fa7cf-177">每個查詢都有特定查詢型別參數組。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-177">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="fa7cf-178">在下列範例中，使用者會指定最小高度和寬度所需的磁碟區、 樓層、 窗格和前面的磁碟區的許可的最小數量的最小的放置高度。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-178">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="fa7cf-179">所有度量均是以公尺為單位。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-179">All measurements are in meters.</span></span>




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="fa7cf-180">這些查詢會取得預先配置的陣列**TopologyResult**結構。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-180">Each of these queries takes a pre-allocated array of **TopologyResult** structures.</span></span> <span data-ttu-id="fa7cf-181">**LocationCount**參數會指定傳入之陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-181">The **locationCount** parameter specifies the length of the passed-in array.</span></span> <span data-ttu-id="fa7cf-182">傳回值會報告傳回的位置數目。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-182">The return value reports the number of returned locations.</span></span> <span data-ttu-id="fa7cf-183">這個數字絕不會大於傳入**locationCount**參數。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-183">This number is never greater than the passed-in **locationCount** parameter.</span></span>

<span data-ttu-id="fa7cf-184">**TopologyResult**包含傳回的磁碟區、 面向的方向 （也就是一般） 和維度的找到空間的中心位置。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-184">The **TopologyResult** contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

<span data-ttu-id="fa7cf-185">請注意，在 Unity 範例中，這些查詢連結至虛擬 UI 面板中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-185">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="fa7cf-186">硬碟的範例程式碼參數，這些查詢能夠合理值的每個。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-186">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="fa7cf-187">請參閱*SpaceVisualizer.cs*範例程式碼，如需其他範例。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-187">See *SpaceVisualizer.cs* in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="fa7cf-188">圖形查詢</span><span class="sxs-lookup"><span data-stu-id="fa7cf-188">Shape queries</span></span>

<span data-ttu-id="fa7cf-189">DLL 時，圖形分析器內 (**ShapeAnalyzer_W**) 要比對由使用者定義的自訂圖形會使用拓撲分析器。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-189">Inside of the DLL, the shape analyzer (**ShapeAnalyzer_W**) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="fa7cf-190">Unity 範例有一組預先定義的圖形查詢 功能表的 圖形 索引標籤上所示。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-190">The Unity sample has a pre-defined set of shapes which are shown in the query menu, on the shape tab.</span></span>

<span data-ttu-id="fa7cf-191">請注意，水平介面僅適用於圖形分析。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-191">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="fa7cf-192">沙發上，比方說，是由一般基座介面和一般頂端的沙發上一步的定義。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-192">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="fa7cf-193">Shape 查詢會尋找的特定大小、 頁高及長寬範圍，以對齊，且已連線的兩個介面的兩個介面。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-193">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="fa7cf-194">使用 Api 術語，沙發車座和沙發背面的頂端是圖案元件與需求的對齊圖形元件的限制。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-194">Using the APIs terminology, the couch seat and the top of the back of the couch are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="fa7cf-195">Unity 範例中定義的範例查詢 (**ShapeDefinition.cs**)、 「 sittable"物件如下所示：</span><span class="sxs-lookup"><span data-stu-id="fa7cf-195">An example query defined in the Unity sample (**ShapeDefinition.cs**), for “sittable” objects is as follows:</span></span>




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

<span data-ttu-id="fa7cf-196">每個圖形查詢是由一組圖形元件，各有一組元件條件約束和一組列出元件之間的相依性圖形的條件約束的定義。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-196">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which lists dependencies between the components.</span></span> <span data-ttu-id="fa7cf-197">此範例包含三個條件約束的單一元件定義及元件之間沒有任何圖形條件約束 （因為只有一個元件）。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-197">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="fa7cf-198">相反地，沙發圖形有兩個圖形的元件和四個圖形的條件約束。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-198">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="fa7cf-199">請注意，（0 到 1，在此範例中），使用者的元件清單中的其索引所識別的元件。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-199">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

<span data-ttu-id="fa7cf-200">在 Unity 模組提供包裝函式函數，讓您輕鬆建立自訂圖形定義。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-200">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="fa7cf-201">元件和圖形的條件約束的完整清單可在**SpatialUnderstandingDll.cs**內**ShapeComponentConstraint**並**ShapeConstraint**結構。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-201">The full list of component and shape constraints can be found in **SpatialUnderstandingDll.cs** within the **ShapeComponentConstraint** and the **ShapeConstraint** structures.</span></span>

![藍色矩形反白顯示椅子 shape 查詢的結果。](images/chair-shape-query-500px.png)

<span data-ttu-id="fa7cf-203">藍色矩形反白顯示椅子 shape 查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-203">The blue rectangle highlights the results of the chair shape query.</span></span>



### <a name="object-placement-solver"></a><span data-ttu-id="fa7cf-204">物件放置規劃求解</span><span class="sxs-lookup"><span data-stu-id="fa7cf-204">Object placement solver</span></span>

<span data-ttu-id="fa7cf-205">物件放置查詢可用來識別要放置您的物件的實體空間中的理想位置。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-205">Object placement queries can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="fa7cf-206">求解器將會尋找指定物件的規則和條件約束的自動調整的位置。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-206">The solver will find the best-fit location given the object rules and constraints.</span></span> <span data-ttu-id="fa7cf-207">此外，物件查詢會一直保存到該物件中已移除**Solver_RemoveObject**或是**Solver_RemoveAllObjects**呼叫，允許限制多的物件位置。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-207">In addition, object queries persist until the object is removed with **Solver_RemoveObject** or **Solver_RemoveAllObjects** calls, allowing constrained multi-object placement.</span></span>

<span data-ttu-id="fa7cf-208">物件放置查詢是由三個部分所組成： 參數、 一份規則與條件約束清單的位置類型。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-208">Object placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="fa7cf-209">若要執行查詢時，使用下列 API:</span><span class="sxs-lookup"><span data-stu-id="fa7cf-209">To run a query, use the following API:</span></span>




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
<span data-ttu-id="fa7cf-210">此函數會接受物件名稱、 位置定義和規則和條件約束的清單。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-210">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="fa7cf-211">C#包裝函式提供的建構可讓您輕鬆的規則和條件約束建構的 helper 函式。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-211">The C# wrappers provide construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="fa7cf-212">放置定義包含查詢型別 — 也就是下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="fa7cf-212">The placement definition contains the query type — that is, one of the following:</span></span>




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

<span data-ttu-id="fa7cf-213">每個位置型別具有一組唯一類型的參數。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-213">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="fa7cf-214">**ObjectPlacementDefinition**結構包含一組靜態的 helper 函式來建立這些定義。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-214">The **ObjectPlacementDefinition** structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="fa7cf-215">例如，若要尋找之處，將物件放在地板上，您可以使用下列函式：</span><span class="sxs-lookup"><span data-stu-id="fa7cf-215">For example, to find a place to put an object on the floor, you can use the following function:</span></span> 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

<span data-ttu-id="fa7cf-216">除了放置型別中，您可以提供一組規則和條件約束。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-216">In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="fa7cf-217">不能違反規則。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-217">Rules cannot be violated.</span></span> <span data-ttu-id="fa7cf-218">選取最佳的放置位置的條件約束的集合針對最適合然後滿足的類型與規則的可能的放置位置。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-218">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints to select the optimal placement location.</span></span> <span data-ttu-id="fa7cf-219">每個規則和條件約束可以提供靜態建立函式所建立。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-219">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="fa7cf-220">如下所示的範例規則和條件約束建構函式。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-220">An example rule and constraint construction function is provided below.</span></span>




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="fa7cf-221">下列物件放置查詢會尋找放介面的邊緣，一半的計量 cube、 遠離其他先前放置物件及附近的聊天室中央的地方。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-221">The object placement query below is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>




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

<span data-ttu-id="fa7cf-222">如果成功， **ObjectPlacementResult**傳回結構，包含放置位置、 維度和方向。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-222">If successful, an **ObjectPlacementResult** structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="fa7cf-223">此外，位置會加入 DLL 的內部放置的物件清單。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-223">In addition, the placement is added to the DLL’s internal list of placed objects.</span></span> <span data-ttu-id="fa7cf-224">後續的放置查詢會將此物件納入考量。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-224">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="fa7cf-225">**LevelSolver.cs** Unity 範例中的檔案包含更多的範例查詢。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-225">The **LevelSolver.cs** file in the Unity sample contains more example queries.</span></span>

![藍色方塊會顯示 立即從觀景窗位置 」 規則的三個位置上 Floor 查詢的結果。](images/away-from-camera-position-500px.png)

<span data-ttu-id="fa7cf-227">藍色方塊會顯示 立即從觀景窗位置 」 規則的三個位置上 Floor 查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-227">The blue boxes show the result from three Place On Floor queries with "away from camera position" rules.</span></span>


<span data-ttu-id="fa7cf-228">**秘訣：**</span><span class="sxs-lookup"><span data-stu-id="fa7cf-228">**Tips:**</span></span>
* <span data-ttu-id="fa7cf-229">解決層級或應用程式的案例所需的多個物件的放置位置，先解決不可或缺和大型物件，來最大化的空間，您可以找到的機率。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-229">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects to maximize the probability that a space can be found.</span></span>
* <span data-ttu-id="fa7cf-230">放置順序非常重要。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-230">Placement order is important.</span></span> <span data-ttu-id="fa7cf-231">如果找不到物件的位置，請嘗試較不受條件約束的組態。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-231">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="fa7cf-232">後援設定一組非常重要跨許多空間組態支援的功能。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-232">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="fa7cf-233">光跡轉型</span><span class="sxs-lookup"><span data-stu-id="fa7cf-233">Ray casting</span></span>

<span data-ttu-id="fa7cf-234">除了三個主要的查詢，光跡轉型介面可以用來擷取已加上標記的介面型別，而且可以複製自訂 watertight playspace 網狀結構出聊天室已進行掃描而且已完成之後, 標籤內部產生介面之類的floor、 ceiling，以及背景牆。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-234">In addition to the three primary queries, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="fa7cf-235">**PlayspaceRaycast**函式會採用無限遠的光線，並傳回如果光線衝突與已知的介面，而且如果是的話，該介面的表單中的相關資訊**RaycastResult**。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-235">The **PlayspaceRaycast** function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a **RaycastResult**.</span></span> 


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

<span data-ttu-id="fa7cf-236">就內部而言，raycast 會計算針對 playspace 計算立方的 8 cm voxel 表示法。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-236">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="fa7cf-237">每個 voxel 包含一組已處理的拓撲資料 (也稱為 surfels) 的介面項目。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-237">Each voxel contains a set of surface elements with processed topology data (also known as surfels).</span></span> <span data-ttu-id="fa7cf-238">比較交集的 voxel 資料格內所含 surfels 和最符合項目用來查閱拓撲資訊。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-238">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="fa7cf-239">此拓撲的資料包含標記的形式傳回**SurfaceTypes**列舉，以及在交集的介面的介面區。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-239">This topology data contains the labeling returned in the form of the **SurfaceTypes** enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="fa7cf-240">在 Unity 範例中，資料指標會轉換每個畫面格無限遠的光線。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-240">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="fa7cf-241">首先，針對 Unity colliders;第二，針對了解模組的世界表示法;而最後，針對 UI 項目。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-241">First, against Unity’s colliders; second, against the understanding module’s world representation; and finally, against the UI elements.</span></span> <span data-ttu-id="fa7cf-242">在此應用程式中，UI 會取得優先權，了解結果，然後最後，Unity colliders。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-242">In this application, UI gets priority, then the understanding result, and finally, Unity’s colliders.</span></span> <span data-ttu-id="fa7cf-243">**SurfaceType**回報為游標後面的文字。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-243">The **SurfaceType** is reported as text next to the cursor.</span></span>

![Raycast 結果報告使用最低限度值的交集。](images/raycast-result-500px.jpg)

<span data-ttu-id="fa7cf-245">Raycast 結果報告使用最低限度值的交集。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-245">Raycast result reporting intersection with the floor.</span></span>


## <a name="get-the-code"></a><span data-ttu-id="fa7cf-246">取得程式碼</span><span class="sxs-lookup"><span data-stu-id="fa7cf-246">Get the code</span></span>

<span data-ttu-id="fa7cf-247">開放原始碼程式碼位於[MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-247">The open-source code is available in [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span></span> <span data-ttu-id="fa7cf-248">讓我們知道[HoloLens 的開發人員論壇](https://forums.hololens.com/)如果您的專案中使用的程式碼。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-248">Let us know on the [HoloLens Developer Forums](https://forums.hololens.com/) if you use the code in a project.</span></span> <span data-ttu-id="fa7cf-249">期待看看您如何使用它 ！</span><span class="sxs-lookup"><span data-stu-id="fa7cf-249">We can't wait to see what you do with it!</span></span>

## <a name="about-the-author"></a><span data-ttu-id="fa7cf-250">關於作者</span><span class="sxs-lookup"><span data-stu-id="fa7cf-250">About the author</span></span>

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <span data-ttu-id="fa7cf-251"><b>Jeff Evertt</b>是軟體工程潛在客戶曾 HoloLens 上早期以來，從 incubation 體驗開發。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-251"><b>Jeff Evertt</b> is a software engineering lead who has worked on HoloLens since the early days, from incubation to experience development.</span></span> <span data-ttu-id="fa7cf-252">HoloLens 之前, 他曾在 Xbox Kinect 上和在遊戲產業中，在各種不同的平台和遊戲。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-252">Before HoloLens, he worked on the Xbox Kinect and in the games industry on a wide variety of platforms and games.</span></span> <span data-ttu-id="fa7cf-253">Jeff 是熱衷於機器人、 圖形及亮色移嗶聲的號誌的事。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-253">Jeff is passionate about robotics, graphics, and things with flashy lights that go beep.</span></span> <span data-ttu-id="fa7cf-254">他喜歡學習新事物，並使用軟體，硬體，而且特別是在兩個相交所在的空間。</span><span class="sxs-lookup"><span data-stu-id="fa7cf-254">He enjoys learning new things and working on software, hardware, and particularly in the space where the two intersect.</span></span></td>
</tr>
</table>



## <a name="see-also"></a><span data-ttu-id="fa7cf-255">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa7cf-255">See also</span></span>
* [<span data-ttu-id="fa7cf-256">空間對應</span><span class="sxs-lookup"><span data-stu-id="fa7cf-256">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="fa7cf-257">空間對應設計</span><span class="sxs-lookup"><span data-stu-id="fa7cf-257">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="fa7cf-258">聊天室掃描視覺效果</span><span class="sxs-lookup"><span data-stu-id="fa7cf-258">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="fa7cf-259">MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="fa7cf-259">MixedRealityToolkit-Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="fa7cf-260">Asobo Studio:從 HoloLens 開發的 frontline 課程</span><span class="sxs-lookup"><span data-stu-id="fa7cf-260">Asobo Studio: Lessons from the frontline of HoloLens development</span></span>](http://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
