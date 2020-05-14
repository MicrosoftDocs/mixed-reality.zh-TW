---
title: Unreal 中的空間對應
description: 在 Unreal 中使用空間對應的指南
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 開發, 功能, 文件, 指南, holograms, 空間對應
ms.openlocfilehash: 32f8247010745b23bf73c5161c378bc1284169ef
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840077"
---
# <a name="spatial-mapping-in-unreal"></a><span data-ttu-id="87e6e-104">Unreal 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="87e6e-104">Spatial Mapping in Unreal</span></span>

<span data-ttu-id="87e6e-105">若要在 HoloLens 上啟用空間對應，請確定已在 [專案設定] > [平台] > [HoloLens] > [功能] 下的 Unreal 編輯器中勾選「空間感知」功能。</span><span class="sxs-lookup"><span data-stu-id="87e6e-105">To enable spatial mapping on HoloLens, ensure that the “Spatial Perception” capability is checked in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span>  

<span data-ttu-id="87e6e-106">若要在 HoloLens 遊戲中選擇使用空間對應，請在 ARSessionConfig 中啟用 [從追蹤的幾何圖形產生網格資料]。</span><span class="sxs-lookup"><span data-stu-id="87e6e-106">To opt into using spatial mapping in a HoloLens game, enable the “Generate Mesh Data from Tracked Geometry” in the ARSessionConfig.</span></span>  <span data-ttu-id="87e6e-107">然後 HoloLens 外掛程式會以非同步方式取得空間對應資料，並透過 MRMesh 將其呈現給 Unreal。</span><span class="sxs-lookup"><span data-stu-id="87e6e-107">The HoloLens plugin will then asynchronously get spatial mapping data and surface it to Unreal through the MRMesh.</span></span> 

![空間錨點存放區就緒](images/unreal-spatialmapping-arsettings.PNG)

<span data-ttu-id="87e6e-109">若要查看空間對應網格的偵錯視覺化效果，請啟用 ARSessionConfig 中的 [以線框呈現網格資料] 核取方塊，以查看 MRMesh 中每個三角形的白色線框。</span><span class="sxs-lookup"><span data-stu-id="87e6e-109">To see a debug visualization of the spatial mapping mesh, enable the “Render Mesh Data in Wireframe” checkbox in the ARSessionConfig to see a white wireframe outline of every triangle in the MRMesh.</span></span> 

<span data-ttu-id="87e6e-110">在 [專案設定] > [平台] > [HoloLens] > [空間對應] 中，您可以修改下列參數來更新空間對應的執行階段行為：</span><span class="sxs-lookup"><span data-stu-id="87e6e-110">In Project Settings > Platform > HoloLens > Spatial Mapping, the following parameters can be modified to update spatial mapping’s runtime behavior:</span></span> 

![空間錨點專案設定](images/unreal-spatialmapping-projectsettings.PNG)

<span data-ttu-id="87e6e-112">「每立方米的三角形數量上限計量」會更新空間對應網格中三角形的密度。</span><span class="sxs-lookup"><span data-stu-id="87e6e-112">Max Triangles Per Cubic Meter will update the density of the triangles in the spatial mapping mesh.</span></span>  <span data-ttu-id="87e6e-113">「空間網格體積大小」表示玩家周圍用來呈現和更新空間對應資料的立方體大小。</span><span class="sxs-lookup"><span data-stu-id="87e6e-113">Spatial Meshing Volume Size indicates the size of the cube around the player to render and update spatial mapping data.</span></span>  <span data-ttu-id="87e6e-114">如果預期的應用程式執行階段環境預期會很大，此欄位可能需要很大，才能符合真實世界的空間。</span><span class="sxs-lookup"><span data-stu-id="87e6e-114">If the expected application runtime environment is expected to be large, this field may need to be large to match the real-world space.</span></span>  <span data-ttu-id="87e6e-115">相反地，如果應用程式只需要在使用者附近的表面上放置全像投影，則此欄位可能會比較小。</span><span class="sxs-lookup"><span data-stu-id="87e6e-115">Conversely, if the application only needs to place holograms on surfaces immediately around the user, this field can be smaller.</span></span>  <span data-ttu-id="87e6e-116">當使用者在世界中行走時，空間對應體積會隨著他們移動。</span><span class="sxs-lookup"><span data-stu-id="87e6e-116">As the user walks around the world, the spatial mapping volume will move with them.</span></span> 

<span data-ttu-id="87e6e-117">若要在執行階段取得 MRMesh 的存取權，請先將 AR Trackable Notify 元件新增至藍圖動作項目：</span><span class="sxs-lookup"><span data-stu-id="87e6e-117">To get access to the MRMesh at runtime, first add an AR Trackable Notify Component to a Blueprint actor:</span></span> 

![空間錨點的 AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

<span data-ttu-id="87e6e-119">然後移至元件的詳細資料，並且按一下要監視事件的綠色 "+" 按鈕。</span><span class="sxs-lookup"><span data-stu-id="87e6e-119">Then go to the component’s details and click on the green “+” button on the events to monitor.</span></span> 

![空間錨點事件](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="87e6e-121">在此案例中，我們會監視 On Add Tracked Geometry 事件，尋找與空間對應資料相對應的有效世界網格，並變更網格的材質：</span><span class="sxs-lookup"><span data-stu-id="87e6e-121">In this case we monitor the On Add Tracked Geometry event looking for valid world meshes which correspond to spatial mapping data, and change the mesh’s material:</span></span> 

![空間錨點範例](images/unreal-spatialmapping-example.PNG)

<span data-ttu-id="87e6e-123">在 C++ 中，我們可以訂閱 OnTrackableAdded 委派，以便在 ARTrackedGeometry 可供使用時立即取得。</span><span class="sxs-lookup"><span data-stu-id="87e6e-123">In C++, we can subscribe to the OnTrackableAdded delegate to get the ARTrackedGeometry as soon as it is available.</span></span>  <span data-ttu-id="87e6e-124">已更新和移除的事件也有類似的委派：AddOnTrackableUpdatedDelegate_Handle 和 AddOnTrackableRemovedDelegate_Handle。</span><span class="sxs-lookup"><span data-stu-id="87e6e-124">There are similar delegates for updated and removed events: AddOnTrackableUpdatedDelegate_Handle and AddOnTrackableRemovedDelegate_Handle.</span></span> 

![空間錨點範例程式 C++ 代碼](images/unreal-spatialmapping-examplecode.PNG)

<span data-ttu-id="87e6e-126">專案的 build.cs 必須在 PublicDependencyModuleNames 清單中有 "AugmentedReality"，才能包含 “ARBlueprintLibrary.h” 和 “MRMesh” 來檢查 UARTrackedGeometry 的 MRMesh 元件。</span><span class="sxs-lookup"><span data-stu-id="87e6e-126">The project’s build.cs must have “AugmentedReality” in the PublicDependencyModuleNames list to include “ARBlueprintLibrary.h” and “MRMesh” to inspect the MRMesh component of the UARTrackedGeometry.</span></span> 

<span data-ttu-id="87e6e-127">空間對應不是透過 ARTrackedGeometry 呈現的唯一資料類型，因此我們會先檢查 EARObjectClassification 是不是「世界」，以表示這是空間對應幾何圖形。</span><span class="sxs-lookup"><span data-stu-id="87e6e-127">Spatial mapping is not the only type of data that gets surfaced through ARTrackedGeometries, so we first check that the EARObjectClassification is World, which indicates that this is spatial mapping geometry.</span></span> 

## <a name="see-also"></a><span data-ttu-id="87e6e-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87e6e-128">See also</span></span>
* [<span data-ttu-id="87e6e-129">空間對應</span><span class="sxs-lookup"><span data-stu-id="87e6e-129">Spatial mapping</span></span>](spatial-mapping.md)
