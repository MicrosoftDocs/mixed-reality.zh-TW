---
title: Unreal 中的空間錨點
description: 在 Unreal 中使用空間錨點的指南
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 開發, 功能, 文件, 指南, holograms, 空間錨點
ms.openlocfilehash: c35d8efc9998aac5b40de833e5acbf7f80353e6b
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840137"
---
# <a name="spatial-anchors-in-unreal"></a><span data-ttu-id="7e80d-104">Unreal 中的空間錨點</span><span class="sxs-lookup"><span data-stu-id="7e80d-104">Spatial Anchors in Unreal</span></span>

<span data-ttu-id="7e80d-105">空間錨點是用來在應用程式工作階段之間，在真實世界空間中保持全像投影。</span><span class="sxs-lookup"><span data-stu-id="7e80d-105">Spatial anchors are used to persist holograms in real-world space between application sessions.</span></span>  <span data-ttu-id="7e80d-106">這會透過 Unreal 呈現為 ARPins，並儲存在 HoloLens 的錨點存放區中，以在未來的工作階段中載入。</span><span class="sxs-lookup"><span data-stu-id="7e80d-106">This gets surfaced through Unreal as ARPins and gets saved in the HoloLens’ anchor store to be loaded in future sessions.</span></span> 

<span data-ttu-id="7e80d-107">在儲存或載入錨點之前，請先檢查錨點存放區已就緒。</span><span class="sxs-lookup"><span data-stu-id="7e80d-107">Before saving or loading anchors, first check that the anchor store is ready.</span></span>  <span data-ttu-id="7e80d-108">在錨點存放區準備就緒之前，嘗試呼叫任何 HoloLens 錨點功能將會失敗。</span><span class="sxs-lookup"><span data-stu-id="7e80d-108">Attempting to call any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

![空間錨點存放區就緒](images/unreal-spatialanchors-store-ready.PNG)

## <a name="save-anchors"></a><span data-ttu-id="7e80d-110">儲存錨點</span><span class="sxs-lookup"><span data-stu-id="7e80d-110">Save Anchors</span></span>

<span data-ttu-id="7e80d-111">一旦應用程式具有需要釘選到世界的元件，就可以下列序列儲存到錨點存放區：</span><span class="sxs-lookup"><span data-stu-id="7e80d-111">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

![空間錨點儲存](images/unreal-spatialanchors-save.PNG)

<span data-ttu-id="7e80d-113">在這裡，我們會在已知位置繁衍動作項目、使用該位置建立 ARPin 並且根據動作項目的類別命名、將動作項目新增至 ARPin，以及將釘選儲存到 HoloLens 錨點存放區。</span><span class="sxs-lookup"><span data-stu-id="7e80d-113">Here, we are spawning an actor at a known location, creating an ARPin with that location and a name based on the actor’s class, adding the actor to the ARPin, and saving the pin to the HoloLens anchor store.</span></span>  <span data-ttu-id="7e80d-114">我們選擇的錨點名稱必須是唯一的，因此在這個範例中我們會附加目前的時間戳記。</span><span class="sxs-lookup"><span data-stu-id="7e80d-114">The anchor name we choose must be unique, so in this example we append the current timestamp.</span></span>  <span data-ttu-id="7e80d-115">如果錨點成功儲存至錨點存放區，則可以在 [系統] > [對應管理員] > [裝置上儲存的錨點檔案] 底下的 HoloLens 裝置入口網站中，檢查該錨點。</span><span class="sxs-lookup"><span data-stu-id="7e80d-115">If the anchor successfully saves to the anchor store, it can be inspected in the HoloLens device portal under System > Map manager > Anchor Files Saved On Device.</span></span> 

## <a name="load-anchors"></a><span data-ttu-id="7e80d-116">載入錨點</span><span class="sxs-lookup"><span data-stu-id="7e80d-116">Load Anchors</span></span>

<span data-ttu-id="7e80d-117">當應用程式啟動時，可以呼叫下列藍圖來將元件還原至其錨點位置：</span><span class="sxs-lookup"><span data-stu-id="7e80d-117">When an application starts, the following blueprint can be called to restore components to their anchor locations:</span></span>

![空間錨點載入](images/unreal-spatialanchors-load.PNG)

<span data-ttu-id="7e80d-119">在此範例中，我們會逐一查看錨點存放區中的所有錨點、在身分識別繁衍動作項目，並將該動作項目從錨點存放區釘選到 ARPin。</span><span class="sxs-lookup"><span data-stu-id="7e80d-119">In this example, we iterate over all of the anchors in the anchor store, spawn an actor at identity, and pin that actor to the ARPin from the anchor store.</span></span>  <span data-ttu-id="7e80d-120">請務必在身分識別繁衍動作項目，因為錨點會負責根據儲存位置在世界中重新放置全像投影，因此此處新增的任何轉換都會將位移新增至錨點。</span><span class="sxs-lookup"><span data-stu-id="7e80d-120">It is important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved, so any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="7e80d-121">也會查詢錨點識別碼，以便根據錨點的儲存名稱來繁衍不同的動作項目。</span><span class="sxs-lookup"><span data-stu-id="7e80d-121">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="remove-anchors"></a><span data-ttu-id="7e80d-122">移除錨點</span><span class="sxs-lookup"><span data-stu-id="7e80d-122">Remove Anchors</span></span> 

<span data-ttu-id="7e80d-123">當完成使用錨點時，可以清除整個錨點存放區，或從錨點存放區移除個別錨點，使其不包含在未來的工作階段中：</span><span class="sxs-lookup"><span data-stu-id="7e80d-123">When done with an anchor, the entire anchor store can be cleared, or individual anchors can be removed from the anchor store so they are not included in future sessions:</span></span> 

![空間錨點移除](images/unreal-spatialanchors-remove.PNG)

## <a name="see-also"></a><span data-ttu-id="7e80d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e80d-125">See also</span></span>
* [<span data-ttu-id="7e80d-126">空間錨點</span><span class="sxs-lookup"><span data-stu-id="7e80d-126">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="7e80d-127">座標系統</span><span class="sxs-lookup"><span data-stu-id="7e80d-127">Coordinate systems</span></span>](coordinate-systems.md)
