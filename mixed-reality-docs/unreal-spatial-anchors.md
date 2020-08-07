---
title: Unreal 中的本機空間錨點
description: 在 Unreal 中使用空間錨點的指南
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 開發, 功能, 文件, 指南, holograms, 空間錨點
ms.openlocfilehash: b102d506b1d670291c3b97ca34d277e2597af043
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376042"
---
# <a name="local-spatial-anchors-in-unreal"></a><span data-ttu-id="599e0-104">Unreal 中的本機空間錨點</span><span class="sxs-lookup"><span data-stu-id="599e0-104">Local Spatial Anchors in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="599e0-105">概觀</span><span class="sxs-lookup"><span data-stu-id="599e0-105">Overview</span></span>

<span data-ttu-id="599e0-106">空間錨點是用來在應用程式工作階段之間，在真實世界空間中儲存全像投影。</span><span class="sxs-lookup"><span data-stu-id="599e0-106">Spatial anchors are used to save holograms in real-world space between application sessions.</span></span> <span data-ttu-id="599e0-107">這些會透過 Unreal 呈現為 **ARPins**，並儲存在 HoloLens 的錨點存放區中，可在未來的工作階段中載入。</span><span class="sxs-lookup"><span data-stu-id="599e0-107">These get surfaced through Unreal as **ARPin**s and saved in the HoloLens’ anchor store, which is loaded in future sessions.</span></span> <span data-ttu-id="599e0-108">本機錨點是沒有網際網路連線時的理想後援。</span><span class="sxs-lookup"><span data-stu-id="599e0-108">Local anchors are ideal as a fallback when there is no internet connectivity.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="599e0-109">本機錨點會儲存在裝置上，而 Azure Spatial Anchors 會儲存在雲端。</span><span class="sxs-lookup"><span data-stu-id="599e0-109">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="599e0-110">如果您想要使用 Azure 雲端服務來儲存您的錨點，我們有一份文件可引導您整合 [Azure Spatial Anchors](unreal-azure-spatial-anchors.md)。</span><span class="sxs-lookup"><span data-stu-id="599e0-110">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](unreal-azure-spatial-anchors.md).</span></span> <span data-ttu-id="599e0-111">請注意，您在同一個專案中可以有本機和 Azure 錨點，而不會發生衝突。</span><span class="sxs-lookup"><span data-stu-id="599e0-111">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="checking-the-anchor-store"></a><span data-ttu-id="599e0-112">檢查錨定存放區</span><span class="sxs-lookup"><span data-stu-id="599e0-112">Checking the anchor store</span></span>

<span data-ttu-id="599e0-113">在儲存或載入錨點之前，必須先檢查錨點存放區是否準備就緒。</span><span class="sxs-lookup"><span data-stu-id="599e0-113">Before saving or loading anchors, you need to check if the anchor store is ready.</span></span>  <span data-ttu-id="599e0-114">在錨點存放區準備就緒之前，呼叫任何 HoloLens 錨點功能將會失敗。</span><span class="sxs-lookup"><span data-stu-id="599e0-114">Calling any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

![空間錨點存放區就緒](images/unreal-spatialanchors-store-ready.PNG)

## <a name="saving-anchors"></a><span data-ttu-id="599e0-116">儲存錨點</span><span class="sxs-lookup"><span data-stu-id="599e0-116">Saving anchors</span></span>

<span data-ttu-id="599e0-117">一旦應用程式具有需要釘選到世界的元件，就可以下列序列儲存到錨點存放區：</span><span class="sxs-lookup"><span data-stu-id="599e0-117">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

![空間錨點儲存](images/unreal-spatialanchors-save.PNG)

<span data-ttu-id="599e0-119">將此細分：</span><span class="sxs-lookup"><span data-stu-id="599e0-119">Breaking this down:</span></span>
1. <span data-ttu-id="599e0-120">在已知位置繁衍動作項目。</span><span class="sxs-lookup"><span data-stu-id="599e0-120">Spawn an actor at a known location.</span></span>
2. <span data-ttu-id="599e0-121">根據動作項目的類別，建立具有該位置和名稱的 **ARPin**。</span><span class="sxs-lookup"><span data-stu-id="599e0-121">Create an **ARPin** with that location and a name based on the actor’s class.</span></span> 
3. <span data-ttu-id="599e0-122">將動作項目新增至 **ARPin**，並將圖釘儲存至 HoloLens 錨點存放區。</span><span class="sxs-lookup"><span data-stu-id="599e0-122">Add the actor to the **ARPin** and save the pin to the HoloLens anchor store.</span></span>  
    * <span data-ttu-id="599e0-123">您選擇的錨點名稱必須是唯一的，在這個範例中，其為目前的時間戳記。</span><span class="sxs-lookup"><span data-stu-id="599e0-123">The anchor name you choose must be unique, which in this example is the current timestamp.</span></span> 

4. <span data-ttu-id="599e0-124">如果錨點成功儲存至錨點存放區，則您可以在 [系統] > [對應管理員] > [裝置上儲存的錨點檔案] 底下的 HoloLens 裝置入口網站中，檢查該錨點。</span><span class="sxs-lookup"><span data-stu-id="599e0-124">If the anchor is successfully saved to the anchor store, you can be inspect it in the HoloLens device portal under **System > Map manager > Anchor Files Saved On Device**.</span></span> 

## <a name="loading-anchors"></a><span data-ttu-id="599e0-125">載入錨點</span><span class="sxs-lookup"><span data-stu-id="599e0-125">Loading anchors</span></span>

<span data-ttu-id="599e0-126">當應用程式啟動時，您可以使用下列藍圖來將元件還原至其錨點位置：</span><span class="sxs-lookup"><span data-stu-id="599e0-126">When an application starts, you can use the following blueprint to restore components to their anchor locations:</span></span>

![空間錨點載入](images/unreal-spatialanchors-load.PNG)

<span data-ttu-id="599e0-128">將此細分：</span><span class="sxs-lookup"><span data-stu-id="599e0-128">Breaking this down:</span></span>
1. <span data-ttu-id="599e0-129">逐一查看錨點存放區中的所有錨點。</span><span class="sxs-lookup"><span data-stu-id="599e0-129">Iterate over all of the anchors in the anchor store.</span></span> 
2. <span data-ttu-id="599e0-130">在身分識別中繁衍動作項目。</span><span class="sxs-lookup"><span data-stu-id="599e0-130">Spawn an actor at identity.</span></span>
3. <span data-ttu-id="599e0-131">從錨點存放區將該動作項目釘選到 **ARPin**。</span><span class="sxs-lookup"><span data-stu-id="599e0-131">Pin that actor to the **ARPin** from the anchor store.</span></span>  

    * <span data-ttu-id="599e0-132">請務必在身分識別繁衍動作項目，因為錨點會負責根據儲存位置在世界中重新放置全像投影。</span><span class="sxs-lookup"><span data-stu-id="599e0-132">It's important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved.</span></span> <span data-ttu-id="599e0-133">此處新增的任何轉換都會將位移新增至錨點。</span><span class="sxs-lookup"><span data-stu-id="599e0-133">Any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="599e0-134">也會查詢錨點識別碼，以便根據錨點的儲存名稱來繁衍不同的動作項目。</span><span class="sxs-lookup"><span data-stu-id="599e0-134">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="removing-anchors"></a><span data-ttu-id="599e0-135">移除錨點</span><span class="sxs-lookup"><span data-stu-id="599e0-135">Removing anchors</span></span> 

<span data-ttu-id="599e0-136">當您完成錨點時，可以使用 **Remove ARPin from WMRAnchor Store** 和 **Remove All ARPins from WMRAnchor Store** 元件，清除個別錨點或整個錨點存放區。</span><span class="sxs-lookup"><span data-stu-id="599e0-136">When you're done with an anchor you can clear individual anchors or the entire anchor store with the **Remove ARPin from WMRAnchor Store** and **Remove All ARPins from WMRAnchor Store** components.</span></span>

![空間錨點移除](images/unreal-spatialanchors-remove.PNG)

> [!NOTE]
> <span data-ttu-id="599e0-138">請記住，空間錨點仍是 Beta 版，因此請務必回頭查看是否有更新的資訊和功能。</span><span class="sxs-lookup"><span data-stu-id="599e0-138">Bear in mind that Spatial Anchors are still in Beta, so be sure to check back for updated information and features.</span></span>

## <a name="see-also"></a><span data-ttu-id="599e0-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="599e0-139">See also</span></span>
* [<span data-ttu-id="599e0-140">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="599e0-140">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)
* [<span data-ttu-id="599e0-141">空間錨點</span><span class="sxs-lookup"><span data-stu-id="599e0-141">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="599e0-142">座標系統</span><span class="sxs-lookup"><span data-stu-id="599e0-142">Coordinate systems</span></span>](coordinate-systems.md)
