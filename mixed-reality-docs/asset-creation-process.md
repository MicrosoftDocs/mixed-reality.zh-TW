---
title: 資產建立程序
description: 建立資產，而混合的實境體驗的指引。
author: paseb
ms.author: paseb
ms.date: 03/21/2018
ms.topic: article
keywords: 資產、 建立、 處理程序、 預算、 多邊形、 材質、 著色器、 效能
ms.openlocfilehash: 513a9856ac35e4229cfb7bc8bcb92d9d6a152980
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66692296"
---
# <a name="asset-creation-process"></a><span data-ttu-id="dd847-104">資產建立程序</span><span class="sxs-lookup"><span data-stu-id="dd847-104">Asset creation process</span></span>

<span data-ttu-id="dd847-105">Windows Mixed Reality 是根據數十年來，Microsoft 投入到 DirectX 的投資。</span><span class="sxs-lookup"><span data-stu-id="dd847-105">Windows Mixed Reality builds on the decades of investment Microsoft has made into DirectX.</span></span> <span data-ttu-id="dd847-106">這表示所有經驗和技術的開發人員有建置 3D 圖形會繼續與 HoloLens 具價值。</span><span class="sxs-lookup"><span data-stu-id="dd847-106">This means that all of the experience and skills developers have with building 3D graphics continues to be valuable with HoloLens.</span></span>

<span data-ttu-id="dd847-107">您建立專案的資產有許多的圖形和表單。</span><span class="sxs-lookup"><span data-stu-id="dd847-107">The assets you create for a project come in many shapes and forms.</span></span> <span data-ttu-id="dd847-108">它們可以包含一系列的紋理/影像、 音訊、 視訊、 3D 模型和動畫。</span><span class="sxs-lookup"><span data-stu-id="dd847-108">They can be comprised of a series of textures/images, audio, video, 3D models and animations.</span></span> <span data-ttu-id="dd847-109">我們無法開始涵蓋所有可用的專案中建立不同類型的資產使用的工具。</span><span class="sxs-lookup"><span data-stu-id="dd847-109">We can't begin to cover all the tools that are available to create the different types of assets used in a project.</span></span> <span data-ttu-id="dd847-110">在本文中，我們將著重在 3D 資產建立方法。</span><span class="sxs-lookup"><span data-stu-id="dd847-110">For this article we will focus on 3D asset creation methods.</span></span>

<span data-ttu-id="dd847-111">![流程概念、 建立、 整合和反覆項目](images/concept-creation-integration-iteration-flow-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="dd847-111">![Concept, creation, integration and iteration flow](images/concept-creation-integration-iteration-flow-640px.jpg)</span></span><br>
<span data-ttu-id="dd847-112">*流程概念、 建立、 整合和反覆項目*</span><span class="sxs-lookup"><span data-stu-id="dd847-112">*Concept, creation, integration and iteration flow*</span></span>

## <a name="things-to-consider"></a><span data-ttu-id="dd847-113">要考慮的事項</span><span class="sxs-lookup"><span data-stu-id="dd847-113">Things to consider</span></span>

<span data-ttu-id="dd847-114">當查看您想要建立的體驗將它視為**預算**，您可以花嘗試提供最佳體驗。</span><span class="sxs-lookup"><span data-stu-id="dd847-114">When looking at the experience you're trying to create think of it as a **budget** that you can spend to try to create the best experience.</span></span> <span data-ttu-id="dd847-115">數目沒有一定的固定限制**多邊形**或是**材質類型**用於您的資產，但更預算的組的權衡取捨。</span><span class="sxs-lookup"><span data-stu-id="dd847-115">There is not necessarily hard limits on the number of **polygons** or **types of materials** use in your assets but more a budgeted set of tradeoffs.</span></span>

<span data-ttu-id="dd847-116">以下是範例預算，針對您的體驗。</span><span class="sxs-lookup"><span data-stu-id="dd847-116">Below is an example budget for your experience.</span></span> <span data-ttu-id="dd847-117">效能不通常是單點失敗，但由一千個剪下每個-se 死亡。</span><span class="sxs-lookup"><span data-stu-id="dd847-117">Performance is usually not a single point of failure but death by a thousand cuts per-se.</span></span>
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><span data-ttu-id="dd847-118"><b>資產</b></span><span class="sxs-lookup"><span data-stu-id="dd847-118"><b>Assets</b></span></span></th><th style="text-align:right;"> <span data-ttu-id="dd847-119">CPU</span><span class="sxs-lookup"><span data-stu-id="dd847-119">CPU</span></span></th><th> <span data-ttu-id="dd847-120">GPU</span><span class="sxs-lookup"><span data-stu-id="dd847-120">GPU</span></span></th><th> <span data-ttu-id="dd847-121">記憶體</span><span class="sxs-lookup"><span data-stu-id="dd847-121">Memory</span></span></th>
</tr><tr>
<td> <span data-ttu-id="dd847-122">多邊形</span><span class="sxs-lookup"><span data-stu-id="dd847-122">Polygons</span></span></td><td> <span data-ttu-id="dd847-123">0%</span><span class="sxs-lookup"><span data-stu-id="dd847-123">0%</span></span></td><td> <span data-ttu-id="dd847-124">5%</span><span class="sxs-lookup"><span data-stu-id="dd847-124">5%</span></span></td><td> <span data-ttu-id="dd847-125">10%</span><span class="sxs-lookup"><span data-stu-id="dd847-125">10%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="dd847-126">紋理</span><span class="sxs-lookup"><span data-stu-id="dd847-126">Textures</span></span></td><td> <span data-ttu-id="dd847-127">5%</span><span class="sxs-lookup"><span data-stu-id="dd847-127">5%</span></span></td><td> <span data-ttu-id="dd847-128">15%</span><span class="sxs-lookup"><span data-stu-id="dd847-128">15%</span></span></td><td><span data-ttu-id="dd847-129">25%</span><span class="sxs-lookup"><span data-stu-id="dd847-129">25%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="dd847-130">著色器</span><span class="sxs-lookup"><span data-stu-id="dd847-130">Shaders</span></span></td><td> <span data-ttu-id="dd847-131">15%</span><span class="sxs-lookup"><span data-stu-id="dd847-131">15%</span></span></td><td> <span data-ttu-id="dd847-132">35%</span><span class="sxs-lookup"><span data-stu-id="dd847-132">35%</span></span></td><td> <span data-ttu-id="dd847-133">0%</span><span class="sxs-lookup"><span data-stu-id="dd847-133">0%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="dd847-134"><b>Dynamics</b></span><span class="sxs-lookup"><span data-stu-id="dd847-134"><b>Dynamics</b></span></span></td><td></td><td></td><td></td>
</tr><tr>
<td> <span data-ttu-id="dd847-135">物理</span><span class="sxs-lookup"><span data-stu-id="dd847-135">Physics</span></span></td><td> <span data-ttu-id="dd847-136">5%</span><span class="sxs-lookup"><span data-stu-id="dd847-136">5%</span></span></td><td> <span data-ttu-id="dd847-137">15%</span><span class="sxs-lookup"><span data-stu-id="dd847-137">15%</span></span></td><td> <span data-ttu-id="dd847-138">0%</span><span class="sxs-lookup"><span data-stu-id="dd847-138">0%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="dd847-139">即時光源</span><span class="sxs-lookup"><span data-stu-id="dd847-139">Realtime lighting</span></span></td><td> <span data-ttu-id="dd847-140">10%</span><span class="sxs-lookup"><span data-stu-id="dd847-140">10%</span></span></td><td> <span data-ttu-id="dd847-141">0%</span><span class="sxs-lookup"><span data-stu-id="dd847-141">0%</span></span></td><td> <span data-ttu-id="dd847-142">0%</span><span class="sxs-lookup"><span data-stu-id="dd847-142">0%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="dd847-143">媒體 （音訊/視訊）</span><span class="sxs-lookup"><span data-stu-id="dd847-143">Media (audio/video)</span></span></td><td> -</td><td> <span data-ttu-id="dd847-144">15%</span><span class="sxs-lookup"><span data-stu-id="dd847-144">15%</span></span></td><td> <span data-ttu-id="dd847-145">25%</span><span class="sxs-lookup"><span data-stu-id="dd847-145">25%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="dd847-146">指令碼/邏輯</span><span class="sxs-lookup"><span data-stu-id="dd847-146">Script/logic</span></span></td><td> <span data-ttu-id="dd847-147">25%</span><span class="sxs-lookup"><span data-stu-id="dd847-147">25%</span></span></td><td> <span data-ttu-id="dd847-148">0%</span><span class="sxs-lookup"><span data-stu-id="dd847-148">0%</span></span></td><td> <span data-ttu-id="dd847-149">5%</span><span class="sxs-lookup"><span data-stu-id="dd847-149">5%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="dd847-150">一般的額外負荷</span><span class="sxs-lookup"><span data-stu-id="dd847-150">General overhead</span></span></td><td> <span data-ttu-id="dd847-151">5%</span><span class="sxs-lookup"><span data-stu-id="dd847-151">5%</span></span></td><td> <span data-ttu-id="dd847-152">5%</span><span class="sxs-lookup"><span data-stu-id="dd847-152">5%</span></span></td><td> <span data-ttu-id="dd847-153">5%</span><span class="sxs-lookup"><span data-stu-id="dd847-153">5%</span></span></td>
</tr><tr>
<td> <span data-ttu-id="dd847-154"><b>總計</b></span><span class="sxs-lookup"><span data-stu-id="dd847-154"><b>Total</b></span></span></td><td> <span data-ttu-id="dd847-155"><b>65%</b></span><span class="sxs-lookup"><span data-stu-id="dd847-155"><b>65%</b></span></span></td><td> <span data-ttu-id="dd847-156"><b>90%</b></span><span class="sxs-lookup"><span data-stu-id="dd847-156"><b>90%</b></span></span></td><td> <span data-ttu-id="dd847-157"><b>70%</b></span><span class="sxs-lookup"><span data-stu-id="dd847-157"><b>70%</b></span></span></td>
</tr>
</table>

<span data-ttu-id="dd847-158">**資產總數**</span><span class="sxs-lookup"><span data-stu-id="dd847-158">**Total number of assets**</span></span>
* <span data-ttu-id="dd847-159">多少資產裡所有作用中的場景？</span><span class="sxs-lookup"><span data-stu-id="dd847-159">How many assets are active in the scene?</span></span>

<span data-ttu-id="dd847-160">**資產的複雜度**</span><span class="sxs-lookup"><span data-stu-id="dd847-160">**Complexity of assets**</span></span>
* <span data-ttu-id="dd847-161">多少三角形 / 多邊形嗎？</span><span class="sxs-lookup"><span data-stu-id="dd847-161">How many triangles / polygons?</span></span>
* <span data-ttu-id="dd847-162">複雜程度是著色器？</span><span class="sxs-lookup"><span data-stu-id="dd847-162">How complex is the shader?</span></span>

<span data-ttu-id="dd847-163">開發人員和演出者必須考量的裝置和圖形引擎功能。</span><span class="sxs-lookup"><span data-stu-id="dd847-163">Both the developers and artists have to consider the capabilities of the device and the graphics engine.</span></span> <span data-ttu-id="dd847-164">Microsoft HoloLens 擁有所有的運算和圖形內建的裝置。</span><span class="sxs-lookup"><span data-stu-id="dd847-164">Microsoft HoloLens has all of the computational and graphics built into the device.</span></span> <span data-ttu-id="dd847-165">共用的開發人員認為在行動裝置平台的功能。</span><span class="sxs-lookup"><span data-stu-id="dd847-165">It shares the capabilities developers would find on a mobile platform.</span></span>

<span data-ttu-id="dd847-166">資產的建立程序是不論是否您設為目標的體驗相同[全像攝影版的裝置或沈浸式裝置](mixed-reality.md#the-mixed-reality-spectrum)。</span><span class="sxs-lookup"><span data-stu-id="dd847-166">The creation process for assets is the same regardless of whether you're targeting an experience for a [holographic device or an immersive device](mixed-reality.md#the-mixed-reality-spectrum).</span></span> <span data-ttu-id="dd847-167">要注意的主要項目是如先前所述小數位數以及因為您可以在您將想要維護正確的標尺經驗為基礎的混合實境中看到實際的裝置功能。</span><span class="sxs-lookup"><span data-stu-id="dd847-167">The primary thing to note is the device capability as mentioned above as well as scale since you can see the real world in mixed reality you will want to maintain the correct scale based on the experience.</span></span> 

## <a name="authoring-assets"></a><span data-ttu-id="dd847-168">撰寫資產</span><span class="sxs-lookup"><span data-stu-id="dd847-168">Authoring assets</span></span>

<span data-ttu-id="dd847-169">我們將開始取得您的專案中的資產的方式：</span><span class="sxs-lookup"><span data-stu-id="dd847-169">We'll start with the ways to get assets for your project:</span></span>
1. <span data-ttu-id="dd847-170">建立資產 （撰寫工具和擷取的物件）</span><span class="sxs-lookup"><span data-stu-id="dd847-170">Creating Assets (Authoring tools and object capture)</span></span>
2. <span data-ttu-id="dd847-171">購買資產 （線上的名義購買資產）</span><span class="sxs-lookup"><span data-stu-id="dd847-171">Purchasing Assets (Buying assets online)</span></span>
3. <span data-ttu-id="dd847-172">移植資產 （包含現有的資產）</span><span class="sxs-lookup"><span data-stu-id="dd847-172">Porting Assets (Taking existing assets)</span></span>
4. <span data-ttu-id="dd847-173">外包資產 （從第 3 個合作對象的匯入資產）</span><span class="sxs-lookup"><span data-stu-id="dd847-173">Outsourcing Assets (Importing assets from 3rd parties)</span></span>

### <a name="creating-assets"></a><span data-ttu-id="dd847-174">建立資產</span><span class="sxs-lookup"><span data-stu-id="dd847-174">Creating assets</span></span>

<span data-ttu-id="dd847-175">**撰寫工具**</span><span class="sxs-lookup"><span data-stu-id="dd847-175">**Authoring tools**</span></span><br>
<span data-ttu-id="dd847-176">第一次，您可以在幾個不同的方式建立您自己的資產。</span><span class="sxs-lookup"><span data-stu-id="dd847-176">First you can create your own assets in a number of different ways.</span></span> <span data-ttu-id="dd847-177">3D 的演出者會使用許多應用程式和工具來建立模型組成**網狀結構**，**紋理**，並**材料**。</span><span class="sxs-lookup"><span data-stu-id="dd847-177">3D artists use a number of applications and tools to create models which consist of **meshes**, **textures**, and **materials**.</span></span> <span data-ttu-id="dd847-178">這會接著儲存在可以匯入或使用應用程式，例如圖形引擎所使用的檔案格式 **。FBX**或 **。OBJ**。</span><span class="sxs-lookup"><span data-stu-id="dd847-178">This is then saved in a file format that can be imported or used by the graphics engine used by the app, such as **.FBX** or **.OBJ**.</span></span> <span data-ttu-id="dd847-179">任何工具，產生您所選擇的圖形引擎支援的模型將努力**HoloLens**。</span><span class="sxs-lookup"><span data-stu-id="dd847-179">Any tool that generates a model that your chosen graphics engine supports will work on **HoloLens**.</span></span> <span data-ttu-id="dd847-180">在 3D 的演出者之間有許多選擇使用[的 Autodesk Maya 而其本身是能夠使用 HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA)轉換方法會建立資產。</span><span class="sxs-lookup"><span data-stu-id="dd847-180">Among 3D artists, many choose to use [Autodesk’s Maya which itself is able to use HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) to transform the way assets are created.</span></span> <span data-ttu-id="dd847-181">如果您想要快速得到您也可以使用[3D Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources)所附 Windows 匯出。在您的應用程式中使用的 OBJ。</span><span class="sxs-lookup"><span data-stu-id="dd847-181">If you want to get something in quick you can also use [3D Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) that comes with Windows to export .OBJ for use in your application.</span></span>

<span data-ttu-id="dd847-182">**物件擷取**</span><span class="sxs-lookup"><span data-stu-id="dd847-182">**Object capture**</span></span><br>
<span data-ttu-id="dd847-183">另外還有擷取中 3D 物件的選項。</span><span class="sxs-lookup"><span data-stu-id="dd847-183">There is also the option to capture objects in 3D.</span></span> <span data-ttu-id="dd847-184">擷取以 3D 在意物件及編輯數位內容創作的軟體是越來越受歡迎的 3D 列印興起。</span><span class="sxs-lookup"><span data-stu-id="dd847-184">Capturing inanimate objects in 3D and editing them with digital content creation software is increasingly popular with the rise of 3D printing.</span></span> <span data-ttu-id="dd847-185">使用**Kinect 2**感應器並[3D Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources)您可以使用 「 擷取 」 功能，從真實世界物件建立資產。</span><span class="sxs-lookup"><span data-stu-id="dd847-185">Using the **Kinect 2** sensor and [3D Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) you can use the capture feature to create assets from real world objects.</span></span> <span data-ttu-id="dd847-186">這也是[的工具套件](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software)來執行相同的作業**photogrammetry**藉由處理要編結在一起和網格和紋理的影像數目。</span><span class="sxs-lookup"><span data-stu-id="dd847-186">This is also a [suite of tools](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) to do the same with **photogrammetry** by processing a number of images to stitch together and mesh and textures.</span></span>

### <a name="purchasing-assets"></a><span data-ttu-id="dd847-187">購買的資產</span><span class="sxs-lookup"><span data-stu-id="dd847-187">Purchasing assets</span></span>

<span data-ttu-id="dd847-188">另一個絕佳的選項是購買資產以供您的體驗。</span><span class="sxs-lookup"><span data-stu-id="dd847-188">Another excellent option is to purchase assets for your experience.</span></span> <span data-ttu-id="dd847-189">有許多的資產可透過服務這類[Unity Asset Store](https://www.assetstore.unity3d.com/)或是[TurboSquid](http://www.turbosquid.com/)等等。</span><span class="sxs-lookup"><span data-stu-id="dd847-189">There are a ton of assets available through services such as the [Unity Asset Store](https://www.assetstore.unity3d.com/) or [TurboSquid](http://www.turbosquid.com/) among others.</span></span>

<span data-ttu-id="dd847-190">當您從第 3 方購買資產時一定要檢查下列項目：</span><span class="sxs-lookup"><span data-stu-id="dd847-190">When you purchase assets from a 3rd party you always want to check the following:</span></span>
* <span data-ttu-id="dd847-191">**什麼是多邊計數？**</span><span class="sxs-lookup"><span data-stu-id="dd847-191">**What's the poly count?**</span></span>
  * <span data-ttu-id="dd847-192">它符合您的預算？</span><span class="sxs-lookup"><span data-stu-id="dd847-192">Does it fit within your budget?</span></span>
* <span data-ttu-id="dd847-193">**有模型的詳細資料 (LODs) 層級嗎？**</span><span class="sxs-lookup"><span data-stu-id="dd847-193">**Are there levels of detail (LODs) for the model?**</span></span>
  * <span data-ttu-id="dd847-194">模型的詳細層級可讓您調整模型的效能詳細資料。</span><span class="sxs-lookup"><span data-stu-id="dd847-194">Level of detail of a model allow you to scale the detail of a model for performance.</span></span>
* <span data-ttu-id="dd847-195">**是可用的來源檔案？**</span><span class="sxs-lookup"><span data-stu-id="dd847-195">**Is the source file available?**</span></span>
  * <span data-ttu-id="dd847-196">通常未隨附[Unity Asset Store](https://www.assetstore.unity3d.com/)一律包含與這類服務，但[TurboSquid](http://www.turbosquid.com/)。</span><span class="sxs-lookup"><span data-stu-id="dd847-196">Usually not included with [Unity Asset Store](https://www.assetstore.unity3d.com/) but always included with services like [TurboSquid](http://www.turbosquid.com/).</span></span>
  * <span data-ttu-id="dd847-197">如果沒有來源檔案，您將無法修改資產。</span><span class="sxs-lookup"><span data-stu-id="dd847-197">Without the source file you won't be able to modify the asset.</span></span>
  * <span data-ttu-id="dd847-198">請確定提供的來源檔案可以匯入 3D 的工具。</span><span class="sxs-lookup"><span data-stu-id="dd847-198">Make sure the source file provided can be imported by your 3D tools.</span></span>
* <span data-ttu-id="dd847-199">**了解您的重點**</span><span class="sxs-lookup"><span data-stu-id="dd847-199">**Know what you're getting**</span></span>
  * <span data-ttu-id="dd847-200">所提供的動畫</span><span class="sxs-lookup"><span data-stu-id="dd847-200">Are animations provided?</span></span>
  * <span data-ttu-id="dd847-201">請務必檢查您要購買的資產的 [內容] 清單。</span><span class="sxs-lookup"><span data-stu-id="dd847-201">Make sure to check the contents list of the asset you're purchasing.</span></span>

### <a name="porting-assets"></a><span data-ttu-id="dd847-202">移植的資產</span><span class="sxs-lookup"><span data-stu-id="dd847-202">Porting assets</span></span>

<span data-ttu-id="dd847-203">在某些情況下，您會收到原先在建置以及其他裝置和不同的應用程式的現有資產。</span><span class="sxs-lookup"><span data-stu-id="dd847-203">In some cases you'll be handed existing assets that were originally built for other devices and different apps.</span></span> <span data-ttu-id="dd847-204">在大部分情況下這些資產可以轉換為其應用程式正在使用的圖形引擎與相容的格式。</span><span class="sxs-lookup"><span data-stu-id="dd847-204">In most cases these assets can be converted to formats compatible with the graphics engine their app is using.</span></span>

<span data-ttu-id="dd847-205">移植到 HoloLens 應用程式中使用的資產時您會想要提出下列問題：</span><span class="sxs-lookup"><span data-stu-id="dd847-205">When porting assets to use in your HoloLens application you will want to ask the following:</span></span>
* <span data-ttu-id="dd847-206">**您可以直接匯或需要轉換成另一種格式？**</span><span class="sxs-lookup"><span data-stu-id="dd847-206">**Can you import directly or does need to be converted to another format?**</span></span> <span data-ttu-id="dd847-207">請檢查您所匯入與您使用的圖形引擎的格式。</span><span class="sxs-lookup"><span data-stu-id="dd847-207">Check the format you're importing with the graphics engine you're using.</span></span>
* <span data-ttu-id="dd847-208">**如果將轉換成相容的格式是任何項目遺失嗎？**</span><span class="sxs-lookup"><span data-stu-id="dd847-208">**If converting to a compatible format is anything lost?**</span></span> <span data-ttu-id="dd847-209">有時可能會遺失，詳細資料，或匯入可能會導致需要清除的 3D 撰寫工具中的成品。</span><span class="sxs-lookup"><span data-stu-id="dd847-209">Sometimes details can be lost or importing can cause artifacts that need to be cleaned up in a 3D authoring tool.</span></span>
* <span data-ttu-id="dd847-210">**什麼是三角形/多邊形計算資產？**</span><span class="sxs-lookup"><span data-stu-id="dd847-210">**What is the triangles / polygons count for the asset?**</span></span> <span data-ttu-id="dd847-211">根據您應用程式可以使用預算[Simplygon](https://www.simplygon.com/)或類似的工具，削弱 （可循序或以手動方式減少多邊計數） 以符合您的應用程式的預算內原始的資產。</span><span class="sxs-lookup"><span data-stu-id="dd847-211">Based on the budget for you application you can use [Simplygon](https://www.simplygon.com/) or similar tools to decimate (procedurally or manually reduce poly count) the original asset to fit within your applications budget.</span></span>

### <a name="outsourcing-assets"></a><span data-ttu-id="dd847-212">外包資產</span><span class="sxs-lookup"><span data-stu-id="dd847-212">Outsourcing assets</span></span>

<span data-ttu-id="dd847-213">針對需要比您小組的多個資產的大型專案的另一個選項是建立配備是外包資產建立。</span><span class="sxs-lookup"><span data-stu-id="dd847-213">Another option for larger projects that require more assets than your team is equipped to create is to outsource asset creation.</span></span> <span data-ttu-id="dd847-214">外包的程序牽涉到在外包資產中尋找正確的 studio 或特製化的機構。</span><span class="sxs-lookup"><span data-stu-id="dd847-214">The process of outsourcing involves finding the right studio or agency that specializes in outsourcing assets.</span></span> <span data-ttu-id="dd847-215">這可以是最昂貴的選項，但是也是最具彈性中得到什麼結果。</span><span class="sxs-lookup"><span data-stu-id="dd847-215">This can be the most expensive option but also be the most flexible in what you get.</span></span>
* <span data-ttu-id="dd847-216">**清楚地定義您要要求**</span><span class="sxs-lookup"><span data-stu-id="dd847-216">**Clearly define what you're requesting**</span></span>
  * <span data-ttu-id="dd847-217">盡可能提供盡可能詳細的資料</span><span class="sxs-lookup"><span data-stu-id="dd847-217">Provide as much detail as possible</span></span>
  * <span data-ttu-id="dd847-218">前端、 側邊和回復的概念影像</span><span class="sxs-lookup"><span data-stu-id="dd847-218">Front, side and back concept images</span></span>
  * <span data-ttu-id="dd847-219">在內容中的參考圖案顯示資產</span><span class="sxs-lookup"><span data-stu-id="dd847-219">Reference art showing asset in context</span></span>
  * <span data-ttu-id="dd847-220">小數位數 （通常是以公分為單位指定） 的物件</span><span class="sxs-lookup"><span data-stu-id="dd847-220">Scale of object (Usually specified in centimeters)</span></span>
* <span data-ttu-id="dd847-221">**提供在預算**</span><span class="sxs-lookup"><span data-stu-id="dd847-221">**Provide a Budget**</span></span>
  * <span data-ttu-id="dd847-222">多邊計數範圍</span><span class="sxs-lookup"><span data-stu-id="dd847-222">Poly count range</span></span>
  * <span data-ttu-id="dd847-223">紋理數目</span><span class="sxs-lookup"><span data-stu-id="dd847-223">Number of textures</span></span>
  * <span data-ttu-id="dd847-224">類型的著色器 （如 Unity 和 HoloLens 您一律應該預設第一次為行動裝置的著色器）</span><span class="sxs-lookup"><span data-stu-id="dd847-224">Type of shader (For Unity and HoloLens you should always default to mobile shaders first)</span></span>
* <span data-ttu-id="dd847-225">**了解的成本**</span><span class="sxs-lookup"><span data-stu-id="dd847-225">**Understand the costs**</span></span>
  * <span data-ttu-id="dd847-226">變更要求的外包原則為何？</span><span class="sxs-lookup"><span data-stu-id="dd847-226">What's the outsourcing policy for change requests?</span></span>

<span data-ttu-id="dd847-227">外包可以運作得非常好根據您的專案時間軸，但需要更多的監督以確保您取得正確的資產，則必須在第一次。</span><span class="sxs-lookup"><span data-stu-id="dd847-227">Outsourcing can work extremely well based on your projects timeline but requires more oversight to guarantee that you get the right assets you need the first time.</span></span>
