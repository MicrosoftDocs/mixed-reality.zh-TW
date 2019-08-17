---
title: 使用新空間中的 HoloLens
description: HoloLens 學習了一段時間後的空間外觀。 使用者可以透過空間以特定方式移動 HoloLens 來加速此程式。
author: dorreneb
ms.author: dobrown
ms.date: 08/16/2019
ms.topic: article
keywords: Windows Mixed Reality, 設計, 空間對應, HoloLens, 表面重建, 網格, 頭追蹤, 對應
ms.openlocfilehash: a6a83dfc2c883723e4cd79c0dc46a9cd78f1f604
ms.sourcegitcommit: 60f73ca23023c17c1da833c83d2a02f4dcc4d17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566017"
---
# <a name="use-hololens-in-new-spaces"></a><span data-ttu-id="85808-105">使用新空間中的 HoloLens</span><span class="sxs-lookup"><span data-stu-id="85808-105">Use HoloLens in New Spaces</span></span>

<span data-ttu-id="85808-106">HoloLens*對應*或學習的相關資訊, 也就是使用者在空間前後移動的環境。</span><span class="sxs-lookup"><span data-stu-id="85808-106">HoloLens *maps*, or learns information about, its environment as the user moves around a space.</span></span> <span data-ttu-id="85808-107">經過一段時間後, HoloLens 會為環境中所有已觀察到的部分建立*空間對應*。</span><span class="sxs-lookup"><span data-stu-id="85808-107">Over time, the HoloLens builds up a *spatial map* of all parts of the environment that have been observed.</span></span> <span data-ttu-id="85808-108">在觀察到環境中的變更時, HoloLens 會更新對應。</span><span class="sxs-lookup"><span data-stu-id="85808-108">HoloLens updates the map as changes in the environment are observed.</span></span> <span data-ttu-id="85808-109">此掃描會在應用程式啟動時自動儲存。</span><span class="sxs-lookup"><span data-stu-id="85808-109">This scan will automatically persist between app launches.</span></span>

<span data-ttu-id="85808-110">只要裝置已開啟且使用者已登入, HoloLens 就會建立並更新對應。</span><span class="sxs-lookup"><span data-stu-id="85808-110">HoloLens will create and update maps as long as the device is on and a user is logged in.</span></span> <span data-ttu-id="85808-111">如果您按住或磨損裝置, 並將相機指向某個空間, 則裝置會嘗試對應該區域。</span><span class="sxs-lookup"><span data-stu-id="85808-111">If you hold or wear the device with the cameras pointed at a space, the device will try to map the area.</span></span> <span data-ttu-id="85808-112">雖然 HoloLens 會在一段時間內自然地學習空間, 但是有一些秘訣和訣竅可讓您更快且更有效率地對應空間。</span><span class="sxs-lookup"><span data-stu-id="85808-112">While the HoloLens will learn a space naturally over time, there are tips and tricks available to map the space faster and more efficiently.</span></span> 

<span data-ttu-id="85808-113">如果您的 HoloLens 無法對應您的空間或無法校正, 您可以進入有限的模式。</span><span class="sxs-lookup"><span data-stu-id="85808-113">If your HoloLens can’t map your space or is out of calibration, you may enter Limited mode.</span></span> <span data-ttu-id="85808-114">在 [受限] 模式中, 您無法將全息影像放在您的環境中。</span><span class="sxs-lookup"><span data-stu-id="85808-114">In Limited mode, you won’t be able to place holograms in your surroundings.</span></span>

## <a name="tips-and-tricks-for-mapping-spaces"></a><span data-ttu-id="85808-115">對應空間的秘訣和訣竅</span><span class="sxs-lookup"><span data-stu-id="85808-115">Tips and tricks for mapping spaces</span></span>

### <a name="make-sure-the-space-is-set-up-for-mixed-reality"></a><span data-ttu-id="85808-116">請確定已設定混合現實的空間</span><span class="sxs-lookup"><span data-stu-id="85808-116">Make sure the space is set up for mixed reality</span></span>

<span data-ttu-id="85808-117">環境中的功能可能會使 HoloLens 難以解讀空間。</span><span class="sxs-lookup"><span data-stu-id="85808-117">Features in an environment can make it difficult for the HoloLens to interpret a space.</span></span> <span data-ttu-id="85808-118">輕量、空間中的材質、物件的版面配置等等, 全都會影響 HoloLens 如何對應區域。</span><span class="sxs-lookup"><span data-stu-id="85808-118">Light levels, materials in the space, the layout of objects, and more can all affect how HoloLens maps an area.</span></span>

<span data-ttu-id="85808-119">在[hololens 的環境考慮](environment-considerations-for-hololens.md)中, 可以找到設定 hololens 和其他混合現實裝置空間的秘訣。</span><span class="sxs-lookup"><span data-stu-id="85808-119">Tips for setting up your space for HoloLens and other mixed reality devices can be found in [Environment considerations for HoloLens](environment-considerations-for-hololens.md).</span></span>

### <a name="understand-the-scenarios-for-the-area"></a><span data-ttu-id="85808-120">瞭解區域的案例</span><span class="sxs-lookup"><span data-stu-id="85808-120">Understand the scenarios for the area</span></span>

<span data-ttu-id="85808-121">請務必花最多時間來使用 HoloLens, 讓對應更相關且完整。</span><span class="sxs-lookup"><span data-stu-id="85808-121">It is important to spend the most time where you will be using the HoloLens so that the map is relevant and complete.</span></span> 

<span data-ttu-id="85808-122">例如, 如果 HoloLens 的使用者案例牽涉到從點 A 移到第 B 點, 請將該路徑逐一移到三次, 並在您移動時查看所有方向。</span><span class="sxs-lookup"><span data-stu-id="85808-122">For example, if a user scenario for HoloLens involves moving from Point A to Point B, walk that path two to three times, looking in all directions as you move.</span></span> 

### <a name="walk-slowly-around-the-space"></a><span data-ttu-id="85808-123">以緩慢的速度四處流覽空間</span><span class="sxs-lookup"><span data-stu-id="85808-123">Walk slowly around the space</span></span>

<span data-ttu-id="85808-124">如果您在此區域中的速度過快, 可能是 HoloLens 錯過了對應區域。</span><span class="sxs-lookup"><span data-stu-id="85808-124">If you walk too quickly around the area, it's likely that the HoloLens will miss mapping areas.</span></span> <span data-ttu-id="85808-125">沿著空間的速度變慢, 每隔5-8 英尺就能在您的周圍進行討論。</span><span class="sxs-lookup"><span data-stu-id="85808-125">Walk slowly around the space, stopping every 5-8 feet to look around at your surroundings.</span></span>

<span data-ttu-id="85808-126">順暢的移動也可協助 HoloLens 對應更 effeciently。</span><span class="sxs-lookup"><span data-stu-id="85808-126">Smooth movements also help the HoloLens map more effeciently.</span></span>

### <a name="look-in-all-directions"></a><span data-ttu-id="85808-127">查詢所有方向</span><span class="sxs-lookup"><span data-stu-id="85808-127">Look in all directions</span></span>

<span data-ttu-id="85808-128">當您對應空間時, 會提供 HoloLens 更多資料, 其中的點彼此相對。</span><span class="sxs-lookup"><span data-stu-id="85808-128">Looking around as you map the space gives the HoloLens more data on where points are relative to each other.</span></span> 

<span data-ttu-id="85808-129">例如, 如果您找不到, 則 HoloLens 可能無法得知房間內的上限為何。</span><span class="sxs-lookup"><span data-stu-id="85808-129">If you don't look up, for example, the HoloLens may not know where the ceiling in a room is.</span></span> 

<span data-ttu-id="85808-130">當您對應空間時, 別忘了在地面上向下查看。</span><span class="sxs-lookup"><span data-stu-id="85808-130">Don't forget to look down at the floor as you map the space.</span></span>

### <a name="cover-key-areas-multiple-times"></a><span data-ttu-id="85808-131">涵蓋重要區域多次</span><span class="sxs-lookup"><span data-stu-id="85808-131">Cover key areas multiple times</span></span>

<span data-ttu-id="85808-132">在某個區域中多次移動, 將有助於挑選您在第一個逐步解說中可能錯過的功能。</span><span class="sxs-lookup"><span data-stu-id="85808-132">Moving through an area multiple times will help pick up features you may have missed on the first walkthrough.</span></span> <span data-ttu-id="85808-133">嘗試遍歷區域二到三次, 以建立理想的對應。</span><span class="sxs-lookup"><span data-stu-id="85808-133">Try traversing an area two to three times to build an ideal map.</span></span>

<span data-ttu-id="85808-134">可能的話, 在重複這些移動時, 請花點時間在某個方向的區域中進行, 然後再來回進行, 然後回頭流覽您的方式。</span><span class="sxs-lookup"><span data-stu-id="85808-134">If possible, while repeating these movements, spend time walking through an area in one direction, then turn around and walk back the way you came.</span></span>

### <a name="take-your-time-mapping-the-area"></a><span data-ttu-id="85808-135">讓您的時間與區域對應</span><span class="sxs-lookup"><span data-stu-id="85808-135">Take your time mapping the area</span></span>

<span data-ttu-id="85808-136">HoloLens 可能需要15到20分鐘的時間, 才能完全對應並自行調整為其周圍的環境。</span><span class="sxs-lookup"><span data-stu-id="85808-136">It can take between 15 and 20 minutes for the HoloLens to fully map and adjust itself to its surroundings.</span></span> <span data-ttu-id="85808-137">如果您想要經常使用 HoloLens, 讓該時間預先對應空間可能會導致稍後發生問題。</span><span class="sxs-lookup"><span data-stu-id="85808-137">If you have a space in which you plan to use a HoloLens frequently, taking that time up front to map the space can prevent issues later on.</span></span> 

## <a name="possible-errors-in-the-spatial-map"></a><span data-ttu-id="85808-138">空間對應中可能發生的錯誤</span><span class="sxs-lookup"><span data-stu-id="85808-138">Possible errors in the spatial map</span></span>

<span data-ttu-id="85808-139">空間對應資料中的錯誤屬於下列三種類別的其中一種:</span><span class="sxs-lookup"><span data-stu-id="85808-139">Errors in spatial mapping data fall into one of three categories:</span></span>

* <span data-ttu-id="85808-140">*漏洞*:空間對應資料中遺漏了真實世界的表面。</span><span class="sxs-lookup"><span data-stu-id="85808-140">*Holes*: Real-world surfaces are missing from the spatial mapping data.</span></span>
* <span data-ttu-id="85808-141">*Hallucinations*:表面存在於不存在於真實世界中的空間對應資料。</span><span class="sxs-lookup"><span data-stu-id="85808-141">*Hallucinations*: Surfaces exist in the spatial mapping data that do not exist in the real world.</span></span>
* <span data-ttu-id="85808-142">*Wormholes*:HoloLens 「失去」空間對應的一部分, 因為它是在地圖的不同部分, 而不是實際的。</span><span class="sxs-lookup"><span data-stu-id="85808-142">*Wormholes*: HoloLens 'loses' part of the spatial map by thinking it is in a different part of the map than it actually is.</span></span>
* <span data-ttu-id="85808-143">*偏差*:空間對應資料中的表面會 imperfectly 對齊實際的表面, 不論是推送或拉出。</span><span class="sxs-lookup"><span data-stu-id="85808-143">*Bias*: Surfaces in the spatial mapping data are imperfectly aligned with real-world surfaces, either pushed in or pulled out.</span></span>

<span data-ttu-id="85808-144">您可以藉由[刪除您的全息影像](environment-considerations-for-hololens.md)並重新對應空間, 來減輕其中許多錯誤。</span><span class="sxs-lookup"><span data-stu-id="85808-144">Many of these errors can be mitigated by [deleting your holograms](environment-considerations-for-hololens.md) and re-mapping the space.</span></span>