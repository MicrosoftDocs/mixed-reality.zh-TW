---
title: 資產建立流程
description: 建立混合現實體驗資產的指導方針。
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: 資產, 建立, 進程, 預算, 多邊形, 紋理, 著色器, 效能
ms.openlocfilehash: f7bee55249764af37453ea0fab01730b43907569
ms.sourcegitcommit: c4d0132ea755c861c504dad46957e791b9c705d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69896499"
---
# <a name="asset-creation-process"></a><span data-ttu-id="3fe47-104">資產建立流程</span><span class="sxs-lookup"><span data-stu-id="3fe47-104">Asset creation process</span></span>

<span data-ttu-id="3fe47-105">Windows Mixed Reality 建基於 Microsoft 在 DirectX 中所做的數十年投資。</span><span class="sxs-lookup"><span data-stu-id="3fe47-105">Windows Mixed Reality builds on the decades of investment Microsoft has made into DirectX.</span></span> <span data-ttu-id="3fe47-106">這表示開發人員建立3D 圖形所擁有的所有經驗和技能, 在 HoloLens 方面仍然相當重要。</span><span class="sxs-lookup"><span data-stu-id="3fe47-106">This means that all of the experience and skills developers have with building 3D graphics continues to be valuable with HoloLens.</span></span>

<span data-ttu-id="3fe47-107">您為專案建立的資產會有許多圖形和表單。</span><span class="sxs-lookup"><span data-stu-id="3fe47-107">The assets you create for a project come in many shapes and forms.</span></span> <span data-ttu-id="3fe47-108">它們可以由一系列材質/影像、音訊、影片、3D 模型和動畫所組成。</span><span class="sxs-lookup"><span data-stu-id="3fe47-108">They can be comprised of a series of textures/images, audio, video, 3D models and animations.</span></span> <span data-ttu-id="3fe47-109">我們無法開始涵蓋可用來建立專案中所使用之不同類型資產的所有工具。</span><span class="sxs-lookup"><span data-stu-id="3fe47-109">We can't begin to cover all the tools that are available to create the different types of assets used in a project.</span></span> <span data-ttu-id="3fe47-110">在本文中, 我們將著重于3D 資產建立方法。</span><span class="sxs-lookup"><span data-stu-id="3fe47-110">For this article we will focus on 3D asset creation methods.</span></span>

<span data-ttu-id="3fe47-111">![概念、建立、整合和反復專案流程](images/concept-creation-integration-iteration-flow-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="3fe47-111">![Concept, creation, integration and iteration flow](images/concept-creation-integration-iteration-flow-640px.jpg)</span></span><br>
<span data-ttu-id="3fe47-112">*概念、建立、整合和反復專案流程*</span><span class="sxs-lookup"><span data-stu-id="3fe47-112">*Concept, creation, integration and iteration flow*</span></span>

## <a name="things-to-consider"></a><span data-ttu-id="3fe47-113">要考慮的事項</span><span class="sxs-lookup"><span data-stu-id="3fe47-113">Things to consider</span></span>

<span data-ttu-id="3fe47-114">在查看您的經驗時, 您嘗試將它視為**預算**, 您可以用它來嘗試建立最佳體驗。</span><span class="sxs-lookup"><span data-stu-id="3fe47-114">When looking at the experience you're trying to create think of it as a **budget** that you can spend to try to create the best experience.</span></span> <span data-ttu-id="3fe47-115">您的資產中所使用的**多邊形**或**材質類型**數目不一定會有固定限制, 但會有一組預算的取捨。</span><span class="sxs-lookup"><span data-stu-id="3fe47-115">There is not necessarily hard limits on the number of **polygons** or **types of materials** use in your assets but more a budgeted set of tradeoffs.</span></span>

<span data-ttu-id="3fe47-116">以下是您體驗的範例預算。</span><span class="sxs-lookup"><span data-stu-id="3fe47-116">Below is an example budget for your experience.</span></span> <span data-ttu-id="3fe47-117">效能通常不是單一失敗點, 但每個 se 會有一千個剪下的死亡。</span><span class="sxs-lookup"><span data-stu-id="3fe47-117">Performance is usually not a single point of failure but death by a thousand cuts per-se.</span></span>
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><span data-ttu-id="3fe47-118"><b>固定資產</b></span><span class="sxs-lookup"><span data-stu-id="3fe47-118"><b>Assets</b></span></span></th><th style="text-align:right;"> <span data-ttu-id="3fe47-119">CPU</span><span class="sxs-lookup"><span data-stu-id="3fe47-119">CPU</span></span></th><th> <span data-ttu-id="3fe47-120">GPU</span><span class="sxs-lookup"><span data-stu-id="3fe47-120">GPU</span></span></th><th> <span data-ttu-id="3fe47-121">記憶體</span><span class="sxs-lookup"><span data-stu-id="3fe47-121">Memory</span></span></th>
</tr><tr>
<td> <span data-ttu-id="3fe47-122">多邊形</span><span class="sxs-lookup"><span data-stu-id="3fe47-122">Polygons</span></span></td><td> <span data-ttu-id="3fe47-123">0</span><span class="sxs-lookup"><span data-stu-id="3fe47-123">0%</span></span></td><td> <span data-ttu-id="3fe47-124">5%</span><span class="sxs-lookup"><span data-stu-id="3fe47-124">5%</span></span></td><td> <span data-ttu-id="3fe47-125">10%</span><span class="sxs-lookup"><span data-stu-id="3fe47-125">10%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="3fe47-126">紋理</span><span class="sxs-lookup"><span data-stu-id="3fe47-126">Textures</span></span></td><td> <span data-ttu-id="3fe47-127">5%</span><span class="sxs-lookup"><span data-stu-id="3fe47-127">5%</span></span></td><td> <span data-ttu-id="3fe47-128">次</span><span class="sxs-lookup"><span data-stu-id="3fe47-128">15%</span></span></td><td><span data-ttu-id="3fe47-129">25%</span><span class="sxs-lookup"><span data-stu-id="3fe47-129">25%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="3fe47-130">著色器</span><span class="sxs-lookup"><span data-stu-id="3fe47-130">Shaders</span></span></td><td> <span data-ttu-id="3fe47-131">次</span><span class="sxs-lookup"><span data-stu-id="3fe47-131">15%</span></span></td><td> <span data-ttu-id="3fe47-132">35%</span><span class="sxs-lookup"><span data-stu-id="3fe47-132">35%</span></span></td><td> <span data-ttu-id="3fe47-133">0</span><span class="sxs-lookup"><span data-stu-id="3fe47-133">0%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="3fe47-134"><b>特性</b></span><span class="sxs-lookup"><span data-stu-id="3fe47-134"><b>Dynamics</b></span></span></td><td></td><td></td><td></td>
</tr><tr>
<td> <span data-ttu-id="3fe47-135">物理</span><span class="sxs-lookup"><span data-stu-id="3fe47-135">Physics</span></span></td><td> <span data-ttu-id="3fe47-136">5%</span><span class="sxs-lookup"><span data-stu-id="3fe47-136">5%</span></span></td><td> <span data-ttu-id="3fe47-137">次</span><span class="sxs-lookup"><span data-stu-id="3fe47-137">15%</span></span></td><td> <span data-ttu-id="3fe47-138">0</span><span class="sxs-lookup"><span data-stu-id="3fe47-138">0%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="3fe47-139">即時光源</span><span class="sxs-lookup"><span data-stu-id="3fe47-139">Realtime lighting</span></span></td><td> <span data-ttu-id="3fe47-140">10%</span><span class="sxs-lookup"><span data-stu-id="3fe47-140">10%</span></span></td><td> <span data-ttu-id="3fe47-141">0</span><span class="sxs-lookup"><span data-stu-id="3fe47-141">0%</span></span></td><td> <span data-ttu-id="3fe47-142">0</span><span class="sxs-lookup"><span data-stu-id="3fe47-142">0%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="3fe47-143">媒體 (音訊/影片)</span><span class="sxs-lookup"><span data-stu-id="3fe47-143">Media (audio/video)</span></span></td><td> -</td><td> <span data-ttu-id="3fe47-144">次</span><span class="sxs-lookup"><span data-stu-id="3fe47-144">15%</span></span></td><td> <span data-ttu-id="3fe47-145">25%</span><span class="sxs-lookup"><span data-stu-id="3fe47-145">25%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="3fe47-146">腳本/邏輯</span><span class="sxs-lookup"><span data-stu-id="3fe47-146">Script/logic</span></span></td><td> <span data-ttu-id="3fe47-147">25%</span><span class="sxs-lookup"><span data-stu-id="3fe47-147">25%</span></span></td><td> <span data-ttu-id="3fe47-148">0</span><span class="sxs-lookup"><span data-stu-id="3fe47-148">0%</span></span></td><td> <span data-ttu-id="3fe47-149">5%</span><span class="sxs-lookup"><span data-stu-id="3fe47-149">5%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="3fe47-150">一般負擔</span><span class="sxs-lookup"><span data-stu-id="3fe47-150">General overhead</span></span></td><td> <span data-ttu-id="3fe47-151">5%</span><span class="sxs-lookup"><span data-stu-id="3fe47-151">5%</span></span></td><td> <span data-ttu-id="3fe47-152">5%</span><span class="sxs-lookup"><span data-stu-id="3fe47-152">5%</span></span></td><td> <span data-ttu-id="3fe47-153">5%</span><span class="sxs-lookup"><span data-stu-id="3fe47-153">5%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="3fe47-154"><b>總數</b></span><span class="sxs-lookup"><span data-stu-id="3fe47-154"><b>Total</b></span></span></td><td> <span data-ttu-id="3fe47-155"><b>65%</b></span><span class="sxs-lookup"><span data-stu-id="3fe47-155"><b>65%</b></span></span></td><td> <span data-ttu-id="3fe47-156"><b>90%</b></span><span class="sxs-lookup"><span data-stu-id="3fe47-156"><b>90%</b></span></span></td><td> <span data-ttu-id="3fe47-157"><b>70%</b></span><span class="sxs-lookup"><span data-stu-id="3fe47-157"><b>70%</b></span></span></td>
</tr>
</table>

<span data-ttu-id="3fe47-158">**資產總數**</span><span class="sxs-lookup"><span data-stu-id="3fe47-158">**Total number of assets**</span></span>
* <span data-ttu-id="3fe47-159">場景中有多少個作用中的資產？</span><span class="sxs-lookup"><span data-stu-id="3fe47-159">How many assets are active in the scene?</span></span>

<span data-ttu-id="3fe47-160">**資產的複雜性**</span><span class="sxs-lookup"><span data-stu-id="3fe47-160">**Complexity of assets**</span></span>
* <span data-ttu-id="3fe47-161">有多少三角形/多邊形？</span><span class="sxs-lookup"><span data-stu-id="3fe47-161">How many triangles / polygons?</span></span>
* <span data-ttu-id="3fe47-162">著色器有多複雜？</span><span class="sxs-lookup"><span data-stu-id="3fe47-162">How complex is the shader?</span></span> <span data-ttu-id="3fe47-163">使用混合現實工具組時, 建議使用[混合現實工具組標準著色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md)來減少著色器的複雜度。</span><span class="sxs-lookup"><span data-stu-id="3fe47-163">When using the Mixed Reality Toolkit, it is recommended to use the [Mixed Reality Toolkit Standard shader](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md) to reduce shader complexity.</span></span>

<span data-ttu-id="3fe47-164">開發人員和演出者都必須考慮裝置和圖形引擎的功能。</span><span class="sxs-lookup"><span data-stu-id="3fe47-164">Both the developers and artists have to consider the capabilities of the device and the graphics engine.</span></span> <span data-ttu-id="3fe47-165">Microsoft HoloLens 具有內建于裝置的所有計算和圖形。</span><span class="sxs-lookup"><span data-stu-id="3fe47-165">Microsoft HoloLens has all of the computational and graphics built into the device.</span></span> <span data-ttu-id="3fe47-166">它會分享開發人員可在行動平臺上找到的功能。</span><span class="sxs-lookup"><span data-stu-id="3fe47-166">It shares the capabilities developers would find on a mobile platform.</span></span>

<span data-ttu-id="3fe47-167">無論您是以全像攝影[裝置或沉浸式裝置](mixed-reality.md#the-mixed-reality-spectrum)的體驗為目標, 資產的建立程式都是一樣的。</span><span class="sxs-lookup"><span data-stu-id="3fe47-167">The creation process for assets is the same regardless of whether you're targeting an experience for a [holographic device or an immersive device](mixed-reality.md#the-mixed-reality-spectrum).</span></span> <span data-ttu-id="3fe47-168">要注意的主要事項是如上所述的裝置功能以及規模, 因為您可以在混合現實中看到真實世界, 您會想要根據經驗來維持正確的規模。</span><span class="sxs-lookup"><span data-stu-id="3fe47-168">The primary thing to note is the device capability as mentioned above as well as scale since you can see the real world in mixed reality you will want to maintain the correct scale based on the experience.</span></span> 

## <a name="authoring-assets"></a><span data-ttu-id="3fe47-169">撰寫資產</span><span class="sxs-lookup"><span data-stu-id="3fe47-169">Authoring assets</span></span>

<span data-ttu-id="3fe47-170">我們將從為您的專案取得資產的方法開始:</span><span class="sxs-lookup"><span data-stu-id="3fe47-170">We'll start with the ways to get assets for your project:</span></span>
1. <span data-ttu-id="3fe47-171">建立資產 (撰寫工具和物件捕捉)</span><span class="sxs-lookup"><span data-stu-id="3fe47-171">Creating Assets (Authoring tools and object capture)</span></span>
2. <span data-ttu-id="3fe47-172">購買資產 (線上購買資產)</span><span class="sxs-lookup"><span data-stu-id="3fe47-172">Purchasing Assets (Buying assets online)</span></span>
3. <span data-ttu-id="3fe47-173">移植資產 (取得現有資產)</span><span class="sxs-lookup"><span data-stu-id="3fe47-173">Porting Assets (Taking existing assets)</span></span>
4. <span data-ttu-id="3fe47-174">外包資產 (匯入協力廠商的資產)</span><span class="sxs-lookup"><span data-stu-id="3fe47-174">Outsourcing Assets (Importing assets from 3rd parties)</span></span>

### <a name="creating-assets"></a><span data-ttu-id="3fe47-175">建立資產</span><span class="sxs-lookup"><span data-stu-id="3fe47-175">Creating assets</span></span>

<span data-ttu-id="3fe47-176">**撰寫工具**</span><span class="sxs-lookup"><span data-stu-id="3fe47-176">**Authoring tools**</span></span><br>
<span data-ttu-id="3fe47-177">首先, 您可以使用數種不同的方式來建立自己的資產。</span><span class="sxs-lookup"><span data-stu-id="3fe47-177">First you can create your own assets in a number of different ways.</span></span> <span data-ttu-id="3fe47-178">3D 演出者會使用一些應用程式和工具來建立包含**網格**、**材質**和**材質**的模型。</span><span class="sxs-lookup"><span data-stu-id="3fe47-178">3D artists use a number of applications and tools to create models which consist of **meshes**, **textures**, and **materials**.</span></span> <span data-ttu-id="3fe47-179">然後, 這會以檔案格式儲存, 以供應用程式使用的圖形引擎 (例如) 匯入或使用 **。FBX**或 **。OBJ**。</span><span class="sxs-lookup"><span data-stu-id="3fe47-179">This is then saved in a file format that can be imported or used by the graphics engine used by the app, such as **.FBX** or **.OBJ**.</span></span> <span data-ttu-id="3fe47-180">任何會產生所選圖形引擎支援之模型的工具, 都可以在**HoloLens**上使用。</span><span class="sxs-lookup"><span data-stu-id="3fe47-180">Any tool that generates a model that your chosen graphics engine supports will work on **HoloLens**.</span></span> <span data-ttu-id="3fe47-181">在3D 演出者之間, 許多選擇使用[Autodesk 的 Maya, 其本身能夠使用 HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA)來轉換資產的建立方式。</span><span class="sxs-lookup"><span data-stu-id="3fe47-181">Among 3D artists, many choose to use [Autodesk’s Maya which itself is able to use HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) to transform the way assets are created.</span></span> <span data-ttu-id="3fe47-182">如果您想要取得快速的內容, 也可以使用隨附于 Windows 的[3d](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources)產生器來進行匯出。要在您的應用程式中使用的 OBJ。</span><span class="sxs-lookup"><span data-stu-id="3fe47-182">If you want to get something in quick you can also use [3D Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) that comes with Windows to export .OBJ for use in your application.</span></span>

<span data-ttu-id="3fe47-183">**物件捕獲**</span><span class="sxs-lookup"><span data-stu-id="3fe47-183">**Object capture**</span></span><br>
<span data-ttu-id="3fe47-184">另外還有在3D 中捕捉物件的選項。</span><span class="sxs-lookup"><span data-stu-id="3fe47-184">There is also the option to capture objects in 3D.</span></span> <span data-ttu-id="3fe47-185">透過3D 列印的增加, 在3D 中捕捉無生命物件, 並使用數位內容建立軟體進行編輯。</span><span class="sxs-lookup"><span data-stu-id="3fe47-185">Capturing inanimate objects in 3D and editing them with digital content creation software is increasingly popular with the rise of 3D printing.</span></span> <span data-ttu-id="3fe47-186">使用**Kinect 2**感應器和[3d Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) , 您可以使用 [捕捉] 功能, 從真實世界的物件建立資產。</span><span class="sxs-lookup"><span data-stu-id="3fe47-186">Using the **Kinect 2** sensor and [3D Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) you can use the capture feature to create assets from real world objects.</span></span> <span data-ttu-id="3fe47-187">這也是一[套工具](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software), 可透過處理多個要裝訂在一起的影像, 以及網格和紋理來執行相同的**攝影測量**。</span><span class="sxs-lookup"><span data-stu-id="3fe47-187">This is also a [suite of tools](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) to do the same with **photogrammetry** by processing a number of images to stitch together and mesh and textures.</span></span>

### <a name="purchasing-assets"></a><span data-ttu-id="3fe47-188">購買資產</span><span class="sxs-lookup"><span data-stu-id="3fe47-188">Purchasing assets</span></span>

<span data-ttu-id="3fe47-189">另一個絕佳的選項是購買資產以獲得您的體驗。</span><span class="sxs-lookup"><span data-stu-id="3fe47-189">Another excellent option is to purchase assets for your experience.</span></span> <span data-ttu-id="3fe47-190">服務中有大量的資產可供使用, 例如[Unity 資產存放區](https://www.assetstore.unity3d.com/)或[TurboSquid](http://www.turbosquid.com/)其他。</span><span class="sxs-lookup"><span data-stu-id="3fe47-190">There are a ton of assets available through services such as the [Unity Asset Store](https://www.assetstore.unity3d.com/) or [TurboSquid](http://www.turbosquid.com/) among others.</span></span>

<span data-ttu-id="3fe47-191">當您從協力廠商購買資產時, 您一定會想要檢查下列事項:</span><span class="sxs-lookup"><span data-stu-id="3fe47-191">When you purchase assets from a 3rd party you always want to check the following:</span></span>
* <span data-ttu-id="3fe47-192">**Poly 計數為何？**</span><span class="sxs-lookup"><span data-stu-id="3fe47-192">**What's the poly count?**</span></span>
  * <span data-ttu-id="3fe47-193">它是否符合您的預算？</span><span class="sxs-lookup"><span data-stu-id="3fe47-193">Does it fit within your budget?</span></span>
* <span data-ttu-id="3fe47-194">**模型有何層級的詳細資料 (LODs)？**</span><span class="sxs-lookup"><span data-stu-id="3fe47-194">**Are there levels of detail (LODs) for the model?**</span></span>
  * <span data-ttu-id="3fe47-195">模型的詳細資料層級可讓您針對效能調整模型的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="3fe47-195">Level of detail of a model allow you to scale the detail of a model for performance.</span></span>
* <span data-ttu-id="3fe47-196">**來源檔案是否可用？**</span><span class="sxs-lookup"><span data-stu-id="3fe47-196">**Is the source file available?**</span></span>
  * <span data-ttu-id="3fe47-197">通常不會包含在[Unity 資產存放區](https://www.assetstore.unity3d.com/)中, 但一律會包含在服務 (例如[TurboSquid](http://www.turbosquid.com/)) 中。</span><span class="sxs-lookup"><span data-stu-id="3fe47-197">Usually not included with [Unity Asset Store](https://www.assetstore.unity3d.com/) but always included with services like [TurboSquid](http://www.turbosquid.com/).</span></span>
  * <span data-ttu-id="3fe47-198">若沒有原始檔, 您將無法修改資產。</span><span class="sxs-lookup"><span data-stu-id="3fe47-198">Without the source file you won't be able to modify the asset.</span></span>
  * <span data-ttu-id="3fe47-199">請確定您的3D 工具可以匯入所提供的來源檔案。</span><span class="sxs-lookup"><span data-stu-id="3fe47-199">Make sure the source file provided can be imported by your 3D tools.</span></span>
* <span data-ttu-id="3fe47-200">**瞭解您所取得的內容**</span><span class="sxs-lookup"><span data-stu-id="3fe47-200">**Know what you're getting**</span></span>
  * <span data-ttu-id="3fe47-201">是否提供動畫？</span><span class="sxs-lookup"><span data-stu-id="3fe47-201">Are animations provided?</span></span>
  * <span data-ttu-id="3fe47-202">請務必檢查您所購買資產的 [內容] 清單。</span><span class="sxs-lookup"><span data-stu-id="3fe47-202">Make sure to check the contents list of the asset you're purchasing.</span></span>

### <a name="porting-assets"></a><span data-ttu-id="3fe47-203">移植資產</span><span class="sxs-lookup"><span data-stu-id="3fe47-203">Porting assets</span></span>

<span data-ttu-id="3fe47-204">在某些情況下, 您會將原本針對其他裝置和不同應用程式建立的現有資產遞交給您。</span><span class="sxs-lookup"><span data-stu-id="3fe47-204">In some cases you'll be handed existing assets that were originally built for other devices and different apps.</span></span> <span data-ttu-id="3fe47-205">在大部分情況下, 這些資產可以轉換成與應用程式所使用之圖形引擎相容的格式。</span><span class="sxs-lookup"><span data-stu-id="3fe47-205">In most cases these assets can be converted to formats compatible with the graphics engine their app is using.</span></span>

<span data-ttu-id="3fe47-206">當您在 HoloLens 應用程式中移植資產以使用時, 您會想要詢問下列事項:</span><span class="sxs-lookup"><span data-stu-id="3fe47-206">When porting assets to use in your HoloLens application you will want to ask the following:</span></span>
* <span data-ttu-id="3fe47-207">**您可以直接匯入, 還是需要轉換成另一種格式？**</span><span class="sxs-lookup"><span data-stu-id="3fe47-207">**Can you import directly or does need to be converted to another format?**</span></span> <span data-ttu-id="3fe47-208">請使用您所使用的圖形引擎來檢查您要匯入的格式。</span><span class="sxs-lookup"><span data-stu-id="3fe47-208">Check the format you're importing with the graphics engine you're using.</span></span>
* <span data-ttu-id="3fe47-209">**如果轉換成相容的格式會遺失任何專案嗎？**</span><span class="sxs-lookup"><span data-stu-id="3fe47-209">**If converting to a compatible format is anything lost?**</span></span> <span data-ttu-id="3fe47-210">有時候詳細資料可能會遺失或匯入可能會導致需要在 3D authoring tool 中清除的成品。</span><span class="sxs-lookup"><span data-stu-id="3fe47-210">Sometimes details can be lost or importing can cause artifacts that need to be cleaned up in a 3D authoring tool.</span></span>
* <span data-ttu-id="3fe47-211">**資產的三角形/多邊形計數為何？**</span><span class="sxs-lookup"><span data-stu-id="3fe47-211">**What is the triangles / polygons count for the asset?**</span></span> <span data-ttu-id="3fe47-212">根據您應用程式的預算, 您可以使用[Simplygon](https://www.simplygon.com/)或類似工具來刪減 (cti 或手動減少 poly 計數) 原始資產, 以符合您的應用程式預算。</span><span class="sxs-lookup"><span data-stu-id="3fe47-212">Based on the budget for you application you can use [Simplygon](https://www.simplygon.com/) or similar tools to decimate (procedurally or manually reduce poly count) the original asset to fit within your applications budget.</span></span>

### <a name="outsourcing-assets"></a><span data-ttu-id="3fe47-213">外包資產</span><span class="sxs-lookup"><span data-stu-id="3fe47-213">Outsourcing assets</span></span>

<span data-ttu-id="3fe47-214">對於需要比您的小組建立的更多資產的大型專案, 另一個選項是將資產建立外包。</span><span class="sxs-lookup"><span data-stu-id="3fe47-214">Another option for larger projects that require more assets than your team is equipped to create is to outsource asset creation.</span></span> <span data-ttu-id="3fe47-215">外包的程式牽涉到尋找專門從事外包資產的適當 studio 或機構。</span><span class="sxs-lookup"><span data-stu-id="3fe47-215">The process of outsourcing involves finding the right studio or agency that specializes in outsourcing assets.</span></span> <span data-ttu-id="3fe47-216">這可能是成本最高的選項, 但也是您取得的最具彈性。</span><span class="sxs-lookup"><span data-stu-id="3fe47-216">This can be the most expensive option but also be the most flexible in what you get.</span></span>
* <span data-ttu-id="3fe47-217">**清楚地定義您所要求的內容**</span><span class="sxs-lookup"><span data-stu-id="3fe47-217">**Clearly define what you're requesting**</span></span>
  * <span data-ttu-id="3fe47-218">盡可能提供最多詳細資料</span><span class="sxs-lookup"><span data-stu-id="3fe47-218">Provide as much detail as possible</span></span>
  * <span data-ttu-id="3fe47-219">Front、側視圖和 back 概念影像</span><span class="sxs-lookup"><span data-stu-id="3fe47-219">Front, side and back concept images</span></span>
  * <span data-ttu-id="3fe47-220">顯示內容中資產的參考圖片</span><span class="sxs-lookup"><span data-stu-id="3fe47-220">Reference art showing asset in context</span></span>
  * <span data-ttu-id="3fe47-221">物件的小數值 (通常以釐米指定)</span><span class="sxs-lookup"><span data-stu-id="3fe47-221">Scale of object (Usually specified in centimeters)</span></span>
* <span data-ttu-id="3fe47-222">**提供預算**</span><span class="sxs-lookup"><span data-stu-id="3fe47-222">**Provide a Budget**</span></span>
  * <span data-ttu-id="3fe47-223">Poly 計數範圍</span><span class="sxs-lookup"><span data-stu-id="3fe47-223">Poly count range</span></span>
  * <span data-ttu-id="3fe47-224">紋理數目</span><span class="sxs-lookup"><span data-stu-id="3fe47-224">Number of textures</span></span>
  * <span data-ttu-id="3fe47-225">著色器的類型 (適用于 Unity 和 HoloLens, 請一律先預設為行動著色器)</span><span class="sxs-lookup"><span data-stu-id="3fe47-225">Type of shader (For Unity and HoloLens you should always default to mobile shaders first)</span></span>
* <span data-ttu-id="3fe47-226">**瞭解成本**</span><span class="sxs-lookup"><span data-stu-id="3fe47-226">**Understand the costs**</span></span>
  * <span data-ttu-id="3fe47-227">變更要求的外包原則是什麼？</span><span class="sxs-lookup"><span data-stu-id="3fe47-227">What's the outsourcing policy for change requests?</span></span>

<span data-ttu-id="3fe47-228">外包可以根據您的專案時間軸來執行得非常順利, 但需要更多監督, 以確保您第一次取得所需的適當資產。</span><span class="sxs-lookup"><span data-stu-id="3fe47-228">Outsourcing can work extremely well based on your projects timeline but requires more oversight to guarantee that you get the right assets you need the first time.</span></span>
