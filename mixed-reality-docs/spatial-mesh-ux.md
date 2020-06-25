---
title: 空間網格視覺效果
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: 混合現實、HoloLens、UI 控制項、互動、UI、ux、UX 設計、空間 UI、空間互動、3D UI、3D UX
ms.openlocfilehash: 17a799dcaba5caf4dd7018f8289cad02b40f1277
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85346111"
---
# <a name="spatial-mesh"></a><span data-ttu-id="29963-103">空間網格</span><span class="sxs-lookup"><span data-stu-id="29963-103">Spatial mesh</span></span>

![空間網格](images/UX/MRTK_PulseShader_SpatialMesh.gif)

<span data-ttu-id="29963-105">透過空間網格視覺效果，使用者可以瞭解裝置如何感覺並瞭解實體環境。</span><span class="sxs-lookup"><span data-stu-id="29963-105">Through the spatial mesh visualization, the user can learn how a device perceives and understands the physical environment.</span></span> <span data-ttu-id="29963-106">除了提供空間內容，適當的空間網格視覺效果也可以建立愉悅和神奇體驗。</span><span class="sxs-lookup"><span data-stu-id="29963-106">In addition to providing spatial context, proper spatial mesh visualization can create a delightful and magical experience.</span></span>  

## <a name="design-guideline"></a><span data-ttu-id="29963-107">設計指導方針</span><span class="sxs-lookup"><span data-stu-id="29963-107">Design guideline</span></span>
<span data-ttu-id="29963-108">因為允許使用者專注于內容並與其互動，所以背景中的空間網格的連續和重複視覺效果可能會造成干擾。</span><span class="sxs-lookup"><span data-stu-id="29963-108">Since it's important to allow the user to focus and interact with content, continuous and repeated visualization of the spatial mesh in the background could be distracting.</span></span> <span data-ttu-id="29963-109">建議您謹慎地將環境視覺化，不論是在初始啟動一次，或是當使用者明確地以目標和使用中的空間來查看環境網格時。</span><span class="sxs-lookup"><span data-stu-id="29963-109">It is recommended to visualize the environment sparingly, either only once in the initial launch or when the user shows clear intention to see the environmental mesh by targeting and air-tapping space.</span></span> <span data-ttu-id="29963-110">您可以在 HoloLens shell 中觀察此行為。</span><span class="sxs-lookup"><span data-stu-id="29963-110">You can observe this behavior in the HoloLens shell.</span></span>
<br>


## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="29963-111">適用于 Unity 的 MRTK （混合現實工具組）中的空間網格視覺效果</span><span class="sxs-lookup"><span data-stu-id="29963-111">Spatial mesh visualization in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="29963-112">MRTK 提供多項空間網格視覺效果的材質。</span><span class="sxs-lookup"><span data-stu-id="29963-112">MRTK provides several materials for the spatial mesh visualization.</span></span>

- <span data-ttu-id="29963-113">**MRTK_Wireframe 的 MRTK_Wireframe.** 材質：預設的靜態空間網格材質，顯示不含動畫的網格外框。</span><span class="sxs-lookup"><span data-stu-id="29963-113">**MRTK_Wireframe.mat, MRTK_Wireframe.mat**: Default static spatial mesh material which shows the mesh outlines without animation.</span></span> <span data-ttu-id="29963-114">此材質適用于偵錯工具，因為它會顯示整個空間網格幾何。</span><span class="sxs-lookup"><span data-stu-id="29963-114">This material is useful for debugging purposes since it shows the entire spatial mesh geometries.</span></span> <span data-ttu-id="29963-115">不過，不建議用於生產環境。</span><span class="sxs-lookup"><span data-stu-id="29963-115">However, it is not recommended for production.</span></span>
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- <span data-ttu-id="29963-116">**MRTK_SurfaceReconstruction**的材料：此材質提供您對空間網格的動畫脈衝效果。</span><span class="sxs-lookup"><span data-stu-id="29963-116">**MRTK_SurfaceReconstruction.mat**: This material gives you an animated pulse effect on the spatial mesh.</span></span> <span data-ttu-id="29963-117">您可以使用這項資料，在特定時間或使用者的按下輸入時，將環境視覺化。</span><span class="sxs-lookup"><span data-stu-id="29963-117">You can use this material to visualize the environment at a specific moment of your experience or on the user's air-tap input.</span></span> <span data-ttu-id="29963-118">如需範例，請參閱**PulseShaderExamples。**</span><span class="sxs-lookup"><span data-stu-id="29963-118">See **PulseShaderExamples.unity** scene for the examples.</span></span>
<br>
<img src="images/UX/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* <span data-ttu-id="29963-119">如需詳細資訊，請參閱[MRTK-空間感知](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html)和[MRTK-脈衝著色器](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html)。</span><span class="sxs-lookup"><span data-stu-id="29963-119">Please see [MRTK - Spatial Awareness](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) and [MRTK - Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html) for more details.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="29963-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29963-120">See also</span></span>

* [<span data-ttu-id="29963-121">游標</span><span class="sxs-lookup"><span data-stu-id="29963-121">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="29963-122">手部光線</span><span class="sxs-lookup"><span data-stu-id="29963-122">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="29963-123">Button</span><span class="sxs-lookup"><span data-stu-id="29963-123">Button</span></span>](button.md)
* [<span data-ttu-id="29963-124">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="29963-124">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="29963-125">週框方塊和應用程式列</span><span class="sxs-lookup"><span data-stu-id="29963-125">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="29963-126">操作</span><span class="sxs-lookup"><span data-stu-id="29963-126">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="29963-127">手部功能表</span><span class="sxs-lookup"><span data-stu-id="29963-127">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="29963-128">近端功能表</span><span class="sxs-lookup"><span data-stu-id="29963-128">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="29963-129">物件集合</span><span class="sxs-lookup"><span data-stu-id="29963-129">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="29963-130">語音命令</span><span class="sxs-lookup"><span data-stu-id="29963-130">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="29963-131">鍵盤</span><span class="sxs-lookup"><span data-stu-id="29963-131">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="29963-132">工具提示</span><span class="sxs-lookup"><span data-stu-id="29963-132">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="29963-133">平板</span><span class="sxs-lookup"><span data-stu-id="29963-133">Slate</span></span>](slate.md)
* [<span data-ttu-id="29963-134">滑桿</span><span class="sxs-lookup"><span data-stu-id="29963-134">Slider</span></span>](slider.md)
* [<span data-ttu-id="29963-135">著色器</span><span class="sxs-lookup"><span data-stu-id="29963-135">Shader</span></span>](shader.md)
* [<span data-ttu-id="29963-136">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="29963-136">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="29963-137">顯示進度</span><span class="sxs-lookup"><span data-stu-id="29963-137">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="29963-138">表面磁性</span><span class="sxs-lookup"><span data-stu-id="29963-138">Surface magnetism</span></span>](surface-magnetism.md)
