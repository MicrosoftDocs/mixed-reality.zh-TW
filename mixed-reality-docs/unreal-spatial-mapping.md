---
title: Unreal 中的空間對應
description: 在 Unreal 中使用空間對應的指南
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 開發, 功能, 文件, 指南, holograms, 空間對應
ms.openlocfilehash: ffa57749cd96e240ac4812f950f4e13a6dbc68bd
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720404"
---
# <a name="spatial-mapping-in-unreal"></a><span data-ttu-id="cf9f3-104">Unreal 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="cf9f3-104">Spatial Mapping in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="cf9f3-105">概觀</span><span class="sxs-lookup"><span data-stu-id="cf9f3-105">Overview</span></span>
<span data-ttu-id="cf9f3-106">空間對應可讓您將物件放在實體世界的表面上，方法是在 HoloLens 周圍顯示世界，這使得全像投影對使用者來說看起來更真實。</span><span class="sxs-lookup"><span data-stu-id="cf9f3-106">Spatial mapping makes it possible to place objects on surfaces in the physical world by showing the world around the HoloLens, which makes holograms seem more real to the user.</span></span> <span data-ttu-id="cf9f3-107">空間對應也會利用真實世界的深度提示，來錨定使用者世界中的物件。這有助於說服使用者這些全像投影實際在其空間內；在空間中浮動或隨著使用者移動的全像投影，將不會覺得真實。</span><span class="sxs-lookup"><span data-stu-id="cf9f3-107">Spatial mapping also anchors objects in the user's world by taking advantage of real world depth cues. This helps convince the user that these holograms are actually in their space; holograms floating in space or moving with the user will not feel as real.</span></span> <span data-ttu-id="cf9f3-108">您想要盡可能地將項目放在舒適的位置。</span><span class="sxs-lookup"><span data-stu-id="cf9f3-108">You want to place items for comfort whenever possible.</span></span>

<span data-ttu-id="cf9f3-109">若要深入了解空間對應品質、放置、遮蔽、轉譯等等，請參閱[空間對應](spatial-mapping.md)文件。</span><span class="sxs-lookup"><span data-stu-id="cf9f3-109">You can find more information on spatial mapping quality, placement, occlusion, rendering, and more, in the [Spatial mapping](spatial-mapping.md) document.</span></span>

## <a name="enabling-spatial-mapping"></a><span data-ttu-id="cf9f3-110">啟用空間對應</span><span class="sxs-lookup"><span data-stu-id="cf9f3-110">Enabling Spatial Mapping</span></span>

<span data-ttu-id="cf9f3-111">若要在 HoloLens 上啟用空間對應：</span><span class="sxs-lookup"><span data-stu-id="cf9f3-111">To enable spatial mapping on HoloLens:</span></span>
- <span data-ttu-id="cf9f3-112">開啟 [編輯] > [專案設定]，然後向下捲動至 [平台] 區段。</span><span class="sxs-lookup"><span data-stu-id="cf9f3-112">Open **Edit > Project Settings** and scroll down to the **Platforms** section.</span></span>    
    + <span data-ttu-id="cf9f3-113">選取 **HoloLens** 並勾選 [空間感知]。</span><span class="sxs-lookup"><span data-stu-id="cf9f3-113">Select **HoloLens** and check **Spatial Perception**.</span></span>

<span data-ttu-id="cf9f3-114">若要在 HoloLens 遊戲中加入空間對應，並偵錯 **MRMesh**：</span><span class="sxs-lookup"><span data-stu-id="cf9f3-114">To opt into spatial mapping and debug the **MRMesh** in a HoloLens game:</span></span>
1. <span data-ttu-id="cf9f3-115">開啟 **ARSessionConfig**，並展開 [ARSettings] > [世界對應] 區段。</span><span class="sxs-lookup"><span data-stu-id="cf9f3-115">Open the **ARSessionConfig** and expand the **ARSettings > World Mapping** section.</span></span> 

2. <span data-ttu-id="cf9f3-116">勾選 [從追蹤的幾何圖形產生網格資料]，這會指示 HoloLens 外掛程式啟動，以非同步方式取得空間對應資料，並透過 **MRMesh**將其呈現給 Unreal。</span><span class="sxs-lookup"><span data-stu-id="cf9f3-116">Check **Generate Mesh Data from Tracked Geometry**, which tells the HoloLens plugin to start asynchronously getting spatial mapping data and surface it to Unreal through the **MRMesh**.</span></span> 
3. <span data-ttu-id="cf9f3-117">勾選 [以線框呈現網格資料]，以在 **MRMesh** 中顯示每個三角形的白色線框。</span><span class="sxs-lookup"><span data-stu-id="cf9f3-117">Check **Render Mesh Data in Wireframe** to show a white wireframe outline of every triangle in the **MRMesh**.</span></span> 

![空間錨點存放區就緒](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a><span data-ttu-id="cf9f3-119">執行階段的空間對應</span><span class="sxs-lookup"><span data-stu-id="cf9f3-119">Spatial Mapping at runtime</span></span>
<span data-ttu-id="cf9f3-120">您可以修改下列參數，以更新空間對應執行階段行為：</span><span class="sxs-lookup"><span data-stu-id="cf9f3-120">You can modify the following parameters to update the spatial mapping runtime behavior:</span></span>

- <span data-ttu-id="cf9f3-121">開啟 [編輯] > [專案設定]、向下捲動至 [平台] 區段，然後選取 [HoloLens] > [空間對應]：</span><span class="sxs-lookup"><span data-stu-id="cf9f3-121">Open **Edit > Project Settings**, scroll down to the **Platforms** section and select **HoloLens > Spatial Mapping**:</span></span> 

![空間錨點專案設定](images/unreal-spatialmapping-projectsettings.PNG)

- <span data-ttu-id="cf9f3-123">**每立方米的三角形數量上限計量**會更新空間對應網格中三角形的密度。</span><span class="sxs-lookup"><span data-stu-id="cf9f3-123">**Max Triangles Per Cubic Meter** updates the density of the triangles in the spatial mapping mesh.</span></span>  
- <span data-ttu-id="cf9f3-124">**空間網格體積大小**是玩家周圍用來呈現和更新空間對應資料的立方體大小。</span><span class="sxs-lookup"><span data-stu-id="cf9f3-124">**Spatial Meshing Volume Size** is the size of the cube around the player to render and update spatial mapping data.</span></span>  
    + <span data-ttu-id="cf9f3-125">如果預期的應用程式執行階段環境預期會很大，此值可能需要很大，才能符合真實世界的空間。</span><span class="sxs-lookup"><span data-stu-id="cf9f3-125">If the expected application runtime environment is expected to be large, this value may need to be large to match the real-world space.</span></span>  <span data-ttu-id="cf9f3-126">另一方面，如果應用程式只需要在使用者附近的表面上放置全像投影，則此值可能會比較小。</span><span class="sxs-lookup"><span data-stu-id="cf9f3-126">On the other hand, this value can be smaller if the application only needs to place holograms on surfaces immediately around the user.</span></span> <span data-ttu-id="cf9f3-127">當使用者在世界中行走時，空間對應體積會隨著他們移動。</span><span class="sxs-lookup"><span data-stu-id="cf9f3-127">As the user walks around the world, the spatial mapping volume will move with them.</span></span> 

## <a name="working-with-mrmesh"></a><span data-ttu-id="cf9f3-128">使用 MongoDB</span><span class="sxs-lookup"><span data-stu-id="cf9f3-128">Working with MRMesh</span></span>
<span data-ttu-id="cf9f3-129">若要可在執行階段存取 **MRMesh**：</span><span class="sxs-lookup"><span data-stu-id="cf9f3-129">To get access to the **MRMesh** at runtime:</span></span>
1. <span data-ttu-id="cf9f3-130">將 **ARTrackableNotify** 元件新增至藍圖動作項目。</span><span class="sxs-lookup"><span data-stu-id="cf9f3-130">Add an **ARTrackableNotify** Component to a Blueprint actor.</span></span> 

![空間錨點的 AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="cf9f3-132">選取 **ARTrackableNotify** 元件，然後展開 [詳細資料] 面板中的 [事件] 區段。</span><span class="sxs-lookup"><span data-stu-id="cf9f3-132">Select the **ARTrackableNotify** component and expand the **Events** section in the **Details** panel.</span></span> 
    - <span data-ttu-id="cf9f3-133">對您要監視的事件按一下 **+** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="cf9f3-133">Click the **+** button on the events you want to monitor.</span></span> 

![空間錨點事件](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="cf9f3-135">在此情況下，會監視 **On Add Tracked Geometry** 事件，這會尋找與空間對應資料相符的有效世界網格。</span><span class="sxs-lookup"><span data-stu-id="cf9f3-135">In this case, the **On Add Tracked Geometry** event is being monitored, which looks for valid world meshes matching to spatial mapping data.</span></span> <span data-ttu-id="cf9f3-136">您可以在 [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) 元件 API 中找到完整的事件清單。</span><span class="sxs-lookup"><span data-stu-id="cf9f3-136">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span> 

<span data-ttu-id="cf9f3-137">您可以在藍圖事件圖形或 C++ 中變更網格的材質。</span><span class="sxs-lookup"><span data-stu-id="cf9f3-137">You can change the mesh’s material in the Blueprint Event Graph or in C++.</span></span> <span data-ttu-id="cf9f3-138">下方螢幕擷取畫面會顯示藍圖路由：</span><span class="sxs-lookup"><span data-stu-id="cf9f3-138">The screenshot below shows the Blueprint route:</span></span> 

![空間錨點範例](images/unreal-spatialmapping-example.PNG)

<span data-ttu-id="cf9f3-140">在 C++ 中，您可以訂閱 `OnTrackableAdded` 委派，以在 `ARTrackedGeometry` 可用時立即取得，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="cf9f3-140">In C++, you can subscribe to the `OnTrackableAdded` delegate to get the `ARTrackedGeometry` as soon as it is available, shown in the code below.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="cf9f3-141">專案的 build.cs 檔案**必須**具有 **PublicDependencyModuleNames** 清單中的 **AugmentedReality**。</span><span class="sxs-lookup"><span data-stu-id="cf9f3-141">The project’s build.cs file **MUST** have **AugmentedReality** in the **PublicDependencyModuleNames** list.</span></span>
> - <span data-ttu-id="cf9f3-142">這包括 **ARBlueprintLibrary** 和 MRMeshComponent，可讓您檢查 **UARTrackedGeometry** 的 **MRMesh** 元件。</span><span class="sxs-lookup"><span data-stu-id="cf9f3-142">This includes **ARBlueprintLibrary.h** and **MRMeshComponent.h**, which lets you inspect the **MRMesh** component of the **UARTrackedGeometry**.</span></span> 

![空間錨點範例程式 C++ 代碼](images/unreal-spatialmapping-examplecode.PNG)

<span data-ttu-id="cf9f3-144">空間對應不是透過 **ARTrackedGeometries** 呈現的唯一資料類型。</span><span class="sxs-lookup"><span data-stu-id="cf9f3-144">Spatial mapping is not the only type of data that gets surfaced through **ARTrackedGeometries**.</span></span> <span data-ttu-id="cf9f3-145">您可以檢查 `EARObjectClassification` 是否為 `World`，其表示這是空間對應幾何。</span><span class="sxs-lookup"><span data-stu-id="cf9f3-145">You can check that the `EARObjectClassification` is `World`, which means this is spatial mapping geometry.</span></span> 

<span data-ttu-id="cf9f3-146">已更新和移除的事件也有類似的委派：</span><span class="sxs-lookup"><span data-stu-id="cf9f3-146">There are similar delegates for updated and removed events:</span></span> 
- `AddOnTrackableUpdatedDelegate_Handle` 
- <span data-ttu-id="cf9f3-147">`AddOnTrackableRemovedDelegate_Handle`。</span><span class="sxs-lookup"><span data-stu-id="cf9f3-147">`AddOnTrackableRemovedDelegate_Handle`.</span></span> 

<span data-ttu-id="cf9f3-148">您可以在 [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API 中找到完整的事件清單。</span><span class="sxs-lookup"><span data-stu-id="cf9f3-148">You can find the full list of events in the [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API.</span></span>

## <a name="see-also"></a><span data-ttu-id="cf9f3-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf9f3-149">See also</span></span>
* [<span data-ttu-id="cf9f3-150">空間對應</span><span class="sxs-lookup"><span data-stu-id="cf9f3-150">Spatial mapping</span></span>](spatial-mapping.md)
