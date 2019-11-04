---
title: 設計您自己的沉浸式環境
description: 除了我們提供的 Windows Mixed Reality 家庭環境之外，您還可以試驗自己的建立和使用。
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Windows Mixed Reality，混合現實，虛擬實境，VR，MR，Home，自訂環境，地點，cliff 房屋，skyloft，使用者，建立
ms.openlocfilehash: e133e1438410540592a51f54ed136aecd04c6244
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437075"
---
# <a name="design-your-own-immersive-environments"></a><span data-ttu-id="4b025-104">設計您自己的沉浸式環境</span><span class="sxs-lookup"><span data-stu-id="4b025-104">Design your own immersive environments</span></span>

>[!NOTE]
><span data-ttu-id="4b025-105">這是實驗性的功能。</span><span class="sxs-lookup"><span data-stu-id="4b025-105">This is an experimental feature.</span></span> <span data-ttu-id="4b025-106">試試看吧！，如果所有東西都不會如預期般運作，則不會驚訝。</span><span class="sxs-lookup"><span data-stu-id="4b025-106">Give it a try and have fun with it, but don't be surprised if everything doesn't quite work as expected.</span></span> <span data-ttu-id="4b025-107">我們正在評估這項功能的可用性，並對其使用感興趣，因此請在[開發人員論壇](https://forums.hololens.com/categories/custom-home-environments)中告訴我們您的經驗（以及您發現的任何錯誤）。</span><span class="sxs-lookup"><span data-stu-id="4b025-107">We're evaluating the viability of this feature and interest in using it, so please tell us about your experience (and any bugs you've found) in the [developer forums](https://forums.hololens.com/categories/custom-home-environments).</span></span>

<span data-ttu-id="4b025-108">從[windows 10 2018 年4月更新](release-notes-april-2018.md)開始，我們已啟用實驗性功能，可讓您將自訂環境新增至 [位置] 選擇器（在 [開始] 功能表上），以做為[Windows Mixed Reality 首頁](navigating-the-windows-mixed-reality-home.md)。</span><span class="sxs-lookup"><span data-stu-id="4b025-108">Starting with the [Windows 10 April 2018 update](release-notes-april-2018.md), we've enabled an experimental feature that lets you add custom environments to the Places picker (on the Start menu) to use as the [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md).</span></span> <span data-ttu-id="4b025-109">Windows Mixed Reality 有兩個預設環境： Cliff 房子和 Skyloft，您可以選擇做為首頁。</span><span class="sxs-lookup"><span data-stu-id="4b025-109">Windows Mixed Reality has two default environments, Cliff House and Skyloft, that you can choose as your home.</span></span> <span data-ttu-id="4b025-110">建立自訂環境可讓您使用自己的建立來擴充該清單。</span><span class="sxs-lookup"><span data-stu-id="4b025-110">Creating custom environments allows you to expand that list with your own creations.</span></span> <span data-ttu-id="4b025-111">我們會使這項功能在早期的狀態下提供，以評估建立者和開發人員的興趣、查看您所建立的各種類型，以及瞭解如何使用不同的撰寫工具。</span><span class="sxs-lookup"><span data-stu-id="4b025-111">We are making this available in an early state to evaluate interest from creators and developers, see what kinds of worlds you create, and understand how you work with different authoring tools.</span></span>

<span data-ttu-id="4b025-112">使用自訂環境時，您會注意到 teleporting、與應用程式互動，以及放置全息影像的運作方式，就像在 Cliff 房子和 Skyloft 中一樣。</span><span class="sxs-lookup"><span data-stu-id="4b025-112">When using a custom environment you'll notice that teleporting, interacting with apps, and placing holograms works just like it does in the Cliff House and Skyloft.</span></span> <span data-ttu-id="4b025-113">您可以在幻想的橫向流覽 web，或使用全像幻想式道具的城市填補，這可能是無限的！</span><span class="sxs-lookup"><span data-stu-id="4b025-113">You can browse the web in a fantasy landscape or fill a futuristic city with holograms - the possibilities are endless!</span></span>

## <a name="device-support"></a><span data-ttu-id="4b025-114">裝置支援</span><span class="sxs-lookup"><span data-stu-id="4b025-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4b025-115"><strong>特徵</strong></span><span class="sxs-lookup"><span data-stu-id="4b025-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="4b025-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b025-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="4b025-117"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="4b025-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4b025-118">自訂家庭環境</span><span class="sxs-lookup"><span data-stu-id="4b025-118">Custom home environments</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="4b025-119">✔️</span><span class="sxs-lookup"><span data-stu-id="4b025-119">✔️</span></span></td>
    </tr>
</table>

## <a name="trying-a-sample-environment"></a><span data-ttu-id="4b025-120">嘗試範例環境</span><span class="sxs-lookup"><span data-stu-id="4b025-120">Trying a sample environment</span></span>

<span data-ttu-id="4b025-121">我們建立了一個範例環境，其中顯示一些自訂家庭環境的創意可能性。</span><span class="sxs-lookup"><span data-stu-id="4b025-121">We've created a sample environment that shows off some of the creative possibilities of custom home environments.</span></span> <span data-ttu-id="4b025-122">請遵循下列步驟來試用：</span><span class="sxs-lookup"><span data-stu-id="4b025-122">Follow these steps to try it out:</span></span>
1. <span data-ttu-id="4b025-123">[下載我們的範例幻想島環境](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe)（連結點到自我解壓縮的可執行檔）。</span><span class="sxs-lookup"><span data-stu-id="4b025-123">[Download our sample Fantasy Island environment](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (link points to self-extracting executable).</span></span>

    <span data-ttu-id="4b025-124">![的幻想島範例環境](images/FantasyLand.jpg)</span><span class="sxs-lookup"><span data-stu-id="4b025-124">![Fantasy Island sample environment](images/FantasyLand.jpg)</span></span><br>
    <span data-ttu-id="4b025-125">*幻想島範例環境*</span><span class="sxs-lookup"><span data-stu-id="4b025-125">*Fantasy Island sample environment*</span></span><br>

2. <span data-ttu-id="4b025-126">執行您剛才下載的**Fantasy_Island .exe**檔案。</span><span class="sxs-lookup"><span data-stu-id="4b025-126">Run the **Fantasy_Island.exe** file you just downloaded.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4b025-127">當您嘗試執行從 web 下載的 .exe 檔案時（例如此檔案），您可能會遇到「Windows 受保護的電腦」快顯視窗。</span><span class="sxs-lookup"><span data-stu-id="4b025-127">When attempting to run a .exe file downloaded from the web (like this one), you may encounter a "Windows protected your PC" pop-up.</span></span> <span data-ttu-id="4b025-128">若要從此快顯視窗執行 Fantasy_Island .exe，請選取 [**更多資訊**]，然後 [**仍要執行**]。</span><span class="sxs-lookup"><span data-stu-id="4b025-128">To run Fantasy_Island.exe from this pop-up, select **More info** and then **Run anyway**.</span></span> <span data-ttu-id="4b025-129">此安全性設定的目的是為了保護您無法下載您不想要信任的檔案，因此請只在信任檔案來源時選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="4b025-129">This security setting is meant to protect you from downloading files you may not want to trust, so please only choose this option when you trust the source of the file.</span></span>

3. <span data-ttu-id="4b025-130">開啟 [檔案**瀏覽器**]，然後在網址列中貼上下列內容，以流覽至 [環境] 資料夾： `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`。</span><span class="sxs-lookup"><span data-stu-id="4b025-130">Open **File Explorer** and navigate to the environments folder by pasting the following in the address bar: `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`.</span></span>
4. <span data-ttu-id="4b025-131">將您下載的範例環境複製到此資料夾中。</span><span class="sxs-lookup"><span data-stu-id="4b025-131">Copy the sample environment that you downloaded into this folder.</span></span>
5. <span data-ttu-id="4b025-132">重新開機**混合現實入口網站**。</span><span class="sxs-lookup"><span data-stu-id="4b025-132">Restart **Mixed Reality Portal**.</span></span> <span data-ttu-id="4b025-133">這會重新整理位置選擇器中的環境清單。</span><span class="sxs-lookup"><span data-stu-id="4b025-133">This will refresh the list of environments in the Places picker.</span></span>
6. <span data-ttu-id="4b025-134">放在您的耳機上。</span><span class="sxs-lookup"><span data-stu-id="4b025-134">Put on your headset.</span></span> <span data-ttu-id="4b025-135">在首頁之後，使用 [Windows] 按鈕控制器開啟 [**開始] 功能表**。</span><span class="sxs-lookup"><span data-stu-id="4b025-135">Once you're in the home, open the **Start menu** using the Windows button your controller.</span></span>
7. <span data-ttu-id="4b025-136">選取釘選的應用程式清單上方的 [**位置**] 圖示，以選擇家庭環境。</span><span class="sxs-lookup"><span data-stu-id="4b025-136">Select the **Places** icon above the list of pinned apps to choose a home environment.</span></span>
8. <span data-ttu-id="4b025-137">您會在您的地點清單中找到您所下載的「幻想島」環境。</span><span class="sxs-lookup"><span data-stu-id="4b025-137">You will find the Fantasy Island environment that you downloaded in your list of places.</span></span> <span data-ttu-id="4b025-138">選取 [**幻想島**] 以輸入新的自訂家庭環境！</span><span class="sxs-lookup"><span data-stu-id="4b025-138">Select **Fantasy Island** to enter your new custom home environment!</span></span>

## <a name="creating-your-own-custom-environment"></a><span data-ttu-id="4b025-139">建立您自己的自訂環境</span><span class="sxs-lookup"><span data-stu-id="4b025-139">Creating your own custom environment</span></span>

<span data-ttu-id="4b025-140">除了使用我們的範例環境之外，您還可以使用您最愛的3D 編輯軟體，匯出自己的自訂環境。</span><span class="sxs-lookup"><span data-stu-id="4b025-140">In addition to using our sample environments, you can export your own custom environments using your favorite 3D editing software.</span></span> 

### <a name="modeling-guidelines"></a><span data-ttu-id="4b025-141">模型化方針</span><span class="sxs-lookup"><span data-stu-id="4b025-141">Modeling guidelines</span></span>

<span data-ttu-id="4b025-142">在模型化您的環境時，請記住下列建議。</span><span class="sxs-lookup"><span data-stu-id="4b025-142">When modeling your environment, keep the following recommendations in mind.</span></span> <span data-ttu-id="4b025-143">這可協助確保使用者在 believably 大小的世界中，以正確的方向產生：</span><span class="sxs-lookup"><span data-stu-id="4b025-143">This will help ensure the user spawns in the correct orientation in a believably-sized world:</span></span>

1. <span data-ttu-id="4b025-144">使用者將會產生0，0，0，將您所需的衍生位置置在原點周圍。</span><span class="sxs-lookup"><span data-stu-id="4b025-144">Users will spawn at 0,0,0 so center your desired spawn location around the origin.</span></span>
2. <span data-ttu-id="4b025-145">工作單位應設定為計量，以便可在世界各地撰寫資產。</span><span class="sxs-lookup"><span data-stu-id="4b025-145">Working Units should be set to meters so that assets can be authored at world scale.</span></span>
3. <span data-ttu-id="4b025-146">向上軸應該設定為 "Y"。</span><span class="sxs-lookup"><span data-stu-id="4b025-146">The Up axis should be set to “Y”.</span></span>
4. <span data-ttu-id="4b025-147">資產應該朝正 Z 軸「順向」。</span><span class="sxs-lookup"><span data-stu-id="4b025-147">The asset should face “forward” towards the positive Z axis.</span></span>
5. <span data-ttu-id="4b025-148">所有的網格都不需要合併，但如果您的目標是受資源限制的裝置，則建議使用此選項。</span><span class="sxs-lookup"><span data-stu-id="4b025-148">All meshes do not need to be combined, but it is recommended if you are targeting resource-constrained devices.</span></span>

### <a name="exporting-your-environment"></a><span data-ttu-id="4b025-149">匯出您的環境</span><span class="sxs-lookup"><span data-stu-id="4b025-149">Exporting your environment</span></span>

<span data-ttu-id="4b025-150">Windows Mixed Reality 依賴二進位 glTF （. glb）作為環境的資產傳遞格式。</span><span class="sxs-lookup"><span data-stu-id="4b025-150">Windows Mixed Reality relies on binary glTF (.glb) as the asset delivery format for environments.</span></span> <span data-ttu-id="4b025-151">glTF 是由 Khronos 群組維護之3D 資產傳遞的免費開放標準。</span><span class="sxs-lookup"><span data-stu-id="4b025-151">glTF is a royalty free open standard for 3D asset delivery maintained by the Khronos group.</span></span> <span data-ttu-id="4b025-152">隨著 glTF 發展成可互通3D 內容的業界標準，Microsoft 也會支援跨 Windows 應用程式和體驗的格式。</span><span class="sxs-lookup"><span data-stu-id="4b025-152">As glTF evolves as an industry standard for interoperable 3D content, so will Microsoft’s support for the format across Windows apps and experiences.</span></span>

<span data-ttu-id="4b025-153">匯出資產以作為自訂家庭環境的第一個步驟是產生 glTF 2.0 模型。</span><span class="sxs-lookup"><span data-stu-id="4b025-153">The first step in exporting assets to be used as custom home environments is generating a glTF 2.0 model.</span></span> <span data-ttu-id="4b025-154">GlTF 工作群組會維護一份[支援的匯出工具和轉換器清單](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters)，以建立 glTF 2.0 模型。</span><span class="sxs-lookup"><span data-stu-id="4b025-154">The glTF working group maintains a [list of supported exporters and converters](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) to create a glTF 2.0 model.</span></span> <span data-ttu-id="4b025-155">若要開始，請使用此頁面上所列的其中一個程式來建立和匯出 glTF 2.0 模型，或使用其中一個支援的轉換器來轉換現有的模型。</span><span class="sxs-lookup"><span data-stu-id="4b025-155">To get started, use one of the programs listed on this page to create and export a glTF 2.0 model, or convert an existing model using one of the supported converters.</span></span>

<span data-ttu-id="4b025-156">此外，請參閱[這篇實用的文章](https://www.khronos.org/blog/art-pipeline-for-gltf)，其中提供了直接從 BLENDER 和 3DS Max 匯出 glTF 模型的藝術工作流程總覽。</span><span class="sxs-lookup"><span data-stu-id="4b025-156">Additionally, check out [this helpful article](https://www.khronos.org/blog/art-pipeline-for-gltf) which provides an overview of an art workflow for exporting glTF models from Blender and 3DS Max directly.</span></span> 

### <a name="environment-limits"></a><span data-ttu-id="4b025-157">環境限制</span><span class="sxs-lookup"><span data-stu-id="4b025-157">Environment limits</span></span>

<span data-ttu-id="4b025-158">所有環境都必須 < 256 mb。</span><span class="sxs-lookup"><span data-stu-id="4b025-158">All environments must be < 256 mbs.</span></span> <span data-ttu-id="4b025-159">大於 256 mb 的環境將無法載入並切換回空白的世界，只有使用者周圍的預設 skybox。</span><span class="sxs-lookup"><span data-stu-id="4b025-159">Environments larger than 256 mbs will fail to load and fall back to an empty world with just the default skybox surrounding the user.</span></span> <span data-ttu-id="4b025-160">建立模型時，請記住此檔案大小限制。</span><span class="sxs-lookup"><span data-stu-id="4b025-160">Please keep this file size limit in mind when creating your models.</span></span> <span data-ttu-id="4b025-161">此外，如果您打算使用 WindowsMRAssetConverter 來優化您的環境，如下所述，請 cognizant 紋理大小會隨著優化工具建立具有較大檔案大小的材質而增加，但載入速度更快。</span><span class="sxs-lookup"><span data-stu-id="4b025-161">Additionally, if you plan to optimize your environment using the WindowsMRAssetConverter as described below, be cognizant that the texture size will increase as the optimizer creates textures that have a larger file size, but load faster.</span></span> 

### <a name="optimizing-your-environment"></a><span data-ttu-id="4b025-162">將您的環境優化</span><span class="sxs-lookup"><span data-stu-id="4b025-162">Optimizing your environment</span></span>

<span data-ttu-id="4b025-163">Windows Mixed Reality 支援數個選擇性的優化，可大幅減少您環境的載入時間。</span><span class="sxs-lookup"><span data-stu-id="4b025-163">Windows Mixed Reality supports a number of optional optimizations that will significantly reduce the load time of your environments.</span></span> <span data-ttu-id="4b025-164">對於具有許多材質的環境而言，這可能特別重要，因為它們有時會在載入時超時。</span><span class="sxs-lookup"><span data-stu-id="4b025-164">This can be especially important for environments with many textures, as they will sometimes time out while loading.</span></span> <span data-ttu-id="4b025-165">一般來說，我們建議所有資產使用此步驟，不過，只有少數或低解析度紋理的小型環境不一定會要求它。</span><span class="sxs-lookup"><span data-stu-id="4b025-165">In general, we recommend this step for all assets, however, smaller environments with few or low-resolution textures won't always require it.</span></span> 

<span data-ttu-id="4b025-166">為了簡化此程式，我們已建立[Windows Mixed Reality 資產轉換器（可在 GitHub 上取得）](https://github.com/Microsoft/glTF-Toolkit/releases)來執行您的優化。</span><span class="sxs-lookup"><span data-stu-id="4b025-166">To make this process easier, we have created the [Windows Mixed Reality Asset Converter (available on GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases) to perform your optimizations.</span></span> <span data-ttu-id="4b025-167">這項工具會使用 Microsoft glTF 工具組中提供的一組公用程式，藉由執行額外的材質封裝、壓縮和解析度向下延展來優化任何標準 2.0 glTF 或 glb。</span><span class="sxs-lookup"><span data-stu-id="4b025-167">This tool uses a set of utilities available in the Microsoft glTF toolkit to optimize any standard 2.0 glTF or .glb by performing an additional texture packing, compression and resolution down-scaling.</span></span> 

<span data-ttu-id="4b025-168">轉換器目前支援多個旗標，以調整優化的確切行為。</span><span class="sxs-lookup"><span data-stu-id="4b025-168">The converter currently supports a number of flags to tweak the exact behavior of the optimizations.</span></span> <span data-ttu-id="4b025-169">我們建議使用下列旗標來執行，以取得最佳結果：</span><span class="sxs-lookup"><span data-stu-id="4b025-169">We recommend running with the following flags for best results:</span></span>

<span data-ttu-id="4b025-170">Flag</span><span class="sxs-lookup"><span data-stu-id="4b025-170">Flag</span></span>|<span data-ttu-id="4b025-171">建議的值</span><span class="sxs-lookup"><span data-stu-id="4b025-171">Recommended Value(s)</span></span>|<span data-ttu-id="4b025-172">說明</span><span class="sxs-lookup"><span data-stu-id="4b025-172">Description</span></span>
---|---|---
<span data-ttu-id="4b025-173">-最大-材質-大小</span><span class="sxs-lookup"><span data-stu-id="4b025-173">-max-texture-size</span></span>|<span data-ttu-id="4b025-174">1024或2048</span><span class="sxs-lookup"><span data-stu-id="4b025-174">1024 or 2048</span></span>| <span data-ttu-id="4b025-175">調整此項以改善材質的品質，預設值為512x512。</span><span class="sxs-lookup"><span data-stu-id="4b025-175">Tweak this to improve the quality of the textures, default is 512x512.</span></span> <span data-ttu-id="4b025-176">請注意，較大的值會大幅影響環境的檔案大小，因此請記住 256 mb 的限制</span><span class="sxs-lookup"><span data-stu-id="4b025-176">Note that a larger value will significantly impact the file size of the environment so keep the 256 mb limit in mind</span></span>
<span data-ttu-id="4b025-177">-最小-版本</span><span class="sxs-lookup"><span data-stu-id="4b025-177">-min-version</span></span>|<span data-ttu-id="4b025-178">1803</span><span class="sxs-lookup"><span data-stu-id="4b025-178">1803</span></span>|<span data-ttu-id="4b025-179">只有 windows > = 1803 版本才支援自訂環境。</span><span class="sxs-lookup"><span data-stu-id="4b025-179">Custom environments are only supported on versions of windows >= 1803.</span></span> <span data-ttu-id="4b025-180">此旗標會移除較舊版本的材質，並減少最終資產的檔案大小</span><span class="sxs-lookup"><span data-stu-id="4b025-180">This flag will remove textures for older versions and reduce the file size of the final asset</span></span>

<span data-ttu-id="4b025-181">例如：</span><span class="sxs-lookup"><span data-stu-id="4b025-181">For example:</span></span>

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a><span data-ttu-id="4b025-182">測試您的環境</span><span class="sxs-lookup"><span data-stu-id="4b025-182">Testing your environment</span></span>

<span data-ttu-id="4b025-183">當您擁有最後的 glb 環境之後，就可以開始在耳機中進行測試。</span><span class="sxs-lookup"><span data-stu-id="4b025-183">Once you have your final .glb environment you're ready to test it out in the headset.</span></span> <span data-ttu-id="4b025-184">從「[試用範例環境](#trying-a-sample-environment)」一節的步驟2開始，使用您的自訂環境作為混合現實首頁。</span><span class="sxs-lookup"><span data-stu-id="4b025-184">Start at step 2 in the ["Trying a sample environment"](#trying-a-sample-environment) section to use your custom environment as the mixed reality home.</span></span> 

## <a name="feedback"></a><span data-ttu-id="4b025-185">意見反應</span><span class="sxs-lookup"><span data-stu-id="4b025-185">Feedback</span></span>

<span data-ttu-id="4b025-186">雖然我們正在評估這項實驗性功能，但我們想要瞭解您使用自訂環境的方式、您可能遇到的任何 bug，以及您喜歡這項功能的方式。</span><span class="sxs-lookup"><span data-stu-id="4b025-186">While we're evaluating this experimental feature, we're interested in learning how you're using custom environments, any bugs you may encounter, and how you like the feature.</span></span> <span data-ttu-id="4b025-187">請在[開發人員論壇](https://forums.hololens.com/categories/custom-home-environments)中分享建立和使用自訂家庭環境的任何意見反應。</span><span class="sxs-lookup"><span data-stu-id="4b025-187">Please share any and all feedback for creating and using custom home environments in the [developer forums](https://forums.hololens.com/categories/custom-home-environments).</span></span>

## <a name="troubleshooting-and-tips"></a><span data-ttu-id="4b025-188">疑難排解與秘訣</span><span class="sxs-lookup"><span data-stu-id="4b025-188">Troubleshooting and tips</span></span>

### <a name="how-do-i-change-the-name-of-the-environment"></a><span data-ttu-id="4b025-189">如何? 變更環境的名稱嗎？</span><span class="sxs-lookup"><span data-stu-id="4b025-189">How do I change the name of the environment?</span></span>

<span data-ttu-id="4b025-190">[環境] 資料夾中的檔案名將用於 [位置] 選擇器。</span><span class="sxs-lookup"><span data-stu-id="4b025-190">The file name in the environments folder will be used in the Places picker.</span></span> <span data-ttu-id="4b025-191">若要變更您的環境名稱，只需重新命名環境檔案名，然後重新開機混合現實入口網站。</span><span class="sxs-lookup"><span data-stu-id="4b025-191">To change the name of your environment simply rename the environment file name, and then restart Mixed Reality Portal.</span></span>

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a><span data-ttu-id="4b025-192">如何? 從我的地點選擇器中移除自訂環境嗎？</span><span class="sxs-lookup"><span data-stu-id="4b025-192">How do I remove custom environments from my Places picker?</span></span>

<span data-ttu-id="4b025-193">若要移除自訂環境，請在您的電腦上開啟 [環境] 資料夾（`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`），然後刪除環境。</span><span class="sxs-lookup"><span data-stu-id="4b025-193">To remove a custom environment, open the environments folder on your PC (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) and delete the environment.</span></span> <span data-ttu-id="4b025-194">一旦您重新開機混合現實入口網站，這個環境就不會再出現在 [位置] 選擇器中。</span><span class="sxs-lookup"><span data-stu-id="4b025-194">Once you restart Mixed Reality Portal, this environment will no longer appear in the Places picker.</span></span> 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a><span data-ttu-id="4b025-195">如何? 預設為我最愛的自訂環境嗎？</span><span class="sxs-lookup"><span data-stu-id="4b025-195">How do I default to my favorite custom environment?</span></span>

<span data-ttu-id="4b025-196">您目前無法變更預設環境。</span><span class="sxs-lookup"><span data-stu-id="4b025-196">You can't currently change the default environment.</span></span> <span data-ttu-id="4b025-197">每次您重新開機混合現實入口網站時，將會回到 Cliff 房屋環境。</span><span class="sxs-lookup"><span data-stu-id="4b025-197">Each time you restart Mixed Reality Portal, you will be returned to the Cliff House environment.</span></span> 

### <a name="i-spawn-into-a-blank-space"></a><span data-ttu-id="4b025-198">我會產生一個空格</span><span class="sxs-lookup"><span data-stu-id="4b025-198">I spawn into a blank space</span></span>

<span data-ttu-id="4b025-199">Windows Mixed Reality[不支援超過 256 mb 的環境](#environment-limits)。</span><span class="sxs-lookup"><span data-stu-id="4b025-199">Windows Mixed Reality [doesn't support environments that exceed 256 mb](#environment-limits).</span></span> <span data-ttu-id="4b025-200">當環境超出此限制時，您會進入空的天空方塊，而不會有任何型號。</span><span class="sxs-lookup"><span data-stu-id="4b025-200">When an environment exceeds this limit, you will land in the empty sky box with no model.</span></span>

### <a name="it-takes-a-long-time-to-load-my-environment"></a><span data-ttu-id="4b025-201">載入我的環境需要很長的時間</span><span class="sxs-lookup"><span data-stu-id="4b025-201">It takes a long time to load my environment</span></span>

<span data-ttu-id="4b025-202">您可以在您的環境中新增選擇性的優化，使其更快載入。</span><span class="sxs-lookup"><span data-stu-id="4b025-202">You can add optional optimizations to your environment to make it load faster.</span></span> <span data-ttu-id="4b025-203">如需詳細資訊，請參閱「[優化您的環境](#optimizing-your-environment)」。</span><span class="sxs-lookup"><span data-stu-id="4b025-203">See ["Optimizing your environment"](#optimizing-your-environment) for details.</span></span>

### <a name="the-scale-of-my-environment-is-incorrect"></a><span data-ttu-id="4b025-204">我的環境規模不正確</span><span class="sxs-lookup"><span data-stu-id="4b025-204">The scale of my environment is incorrect</span></span>

<span data-ttu-id="4b025-205">Windows Mixed Reality 會在載入環境時將 glTF 單位轉譯為1計量。</span><span class="sxs-lookup"><span data-stu-id="4b025-205">Windows Mixed Reality translates glTF units to 1 meter when loading environments.</span></span> <span data-ttu-id="4b025-206">如果您的環境載入非預期的規模，請再次檢查您的匯出工具，以確定您是以1個計量規模進行模型化。</span><span class="sxs-lookup"><span data-stu-id="4b025-206">If your environment loads up an unexpected scale, double check your exporter to ensure that you're modeling at a 1 meter scale.</span></span> 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a><span data-ttu-id="4b025-207">我的環境中的衍生位置不正確</span><span class="sxs-lookup"><span data-stu-id="4b025-207">The spawn location in my environment is incorrect</span></span>

<span data-ttu-id="4b025-208">預設的產生位置位於環境中的0，0，0。</span><span class="sxs-lookup"><span data-stu-id="4b025-208">The default spawn location is located at 0,0,0 in the environment.</span></span> <span data-ttu-id="4b025-209">目前無法自訂此位置，因此您必須藉由將您的環境匯出至所需的衍生點，以修改產生點。</span><span class="sxs-lookup"><span data-stu-id="4b025-209">Its not currently possible to customize this location, so you must modify the spawn point by exporting your environment with the origin positioned at the desired spawn point.</span></span>

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a><span data-ttu-id="4b025-210">在環境中音訊的音效不正確</span><span class="sxs-lookup"><span data-stu-id="4b025-210">The audio doesn't sound correct in the environment</span></span>

<span data-ttu-id="4b025-211">當您建立自訂環境時，它會使用不符合您所建立之實體空間的聲場呈現模擬。</span><span class="sxs-lookup"><span data-stu-id="4b025-211">When you create your custom environment, it will be using an acoustics rendering simulation that does not match the physical space you have created.</span></span> <span data-ttu-id="4b025-212">音效可能來自錯誤的方向，而且可能聽起來 muffled。</span><span class="sxs-lookup"><span data-stu-id="4b025-212">Sound may come from the wrong directions and may sound muffled.</span></span> 

## <a name="see-also"></a><span data-ttu-id="4b025-213">請參閱</span><span class="sxs-lookup"><span data-stu-id="4b025-213">See also</span></span>
* [<span data-ttu-id="4b025-214">Windows Mixed Reality 資產轉換器（位於 GitHub）</span><span class="sxs-lookup"><span data-stu-id="4b025-214">Windows Mixed Reality Asset Converter (on GitHub)</span></span>](https://github.com/Microsoft/glTF-Toolkit/releases)

