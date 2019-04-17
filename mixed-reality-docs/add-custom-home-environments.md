---
title: 新增自訂的家庭環境
description: 除了我們所提供的 Windows Mixed Reality 家用的環境，您可以實驗建立和使用您自己。
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Windows Mixed Reality、 混合實境，虛擬實境、 VR、 MR、 首頁、 自訂環境、 位置、 cliff 房子、 skyloft、 使用者，建立
ms.openlocfilehash: ef140efd88aa0d3329ae2aa7e5b202c3bfe77c0a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591122"
---
# <a name="add-custom-home-environments"></a><span data-ttu-id="66626-104">新增自訂的家庭環境</span><span class="sxs-lookup"><span data-stu-id="66626-104">Add custom home environments</span></span>

>[!NOTE]
><span data-ttu-id="66626-105">這是實驗性功能。</span><span class="sxs-lookup"><span data-stu-id="66626-105">This is an experimental feature.</span></span> <span data-ttu-id="66626-106">不妨試試樂趣，但請不要感到驚訝，如果所有項目未完全如預期運作。</span><span class="sxs-lookup"><span data-stu-id="66626-106">Give it a try and have fun with it, but don't be surprised if everything doesn't quite work as expected.</span></span> <span data-ttu-id="66626-107">我們計劃要評估的可行性，此功能與感興趣，因此使用它，請告訴我們您的經驗 （和任何您已發現的 bug） 中[開發人員論壇](https://forums.hololens.com/categories/custom-home-environments)。</span><span class="sxs-lookup"><span data-stu-id="66626-107">We're evaluating the viability of this feature and interest in using it, so please tell us about your experience (and any bugs you've found) in the [developer forums](https://forums.hololens.com/categories/custom-home-environments).</span></span>

<span data-ttu-id="66626-108">開頭[Windows 10 April 2018 update](#release-notes-april-2018.md)，啟用了實驗性功能，可讓您將加入 （在 [開始] 功能表中） 的位置選擇器的自訂環境，以做為[Windows Mixed Reality 家用](#navigating-the-windows-mixed-reality-home.md).</span><span class="sxs-lookup"><span data-stu-id="66626-108">Starting with the [Windows 10 April 2018 update](#release-notes-april-2018.md), we've enabled an experimental feature that lets you add custom environments to the Places picker (on the Start menu) to use as the [Windows Mixed Reality home](#navigating-the-windows-mixed-reality-home.md).</span></span> <span data-ttu-id="66626-109">Windows Mixed Reality 有兩個預設環境，Cliff 房屋和 Skyloft，您可以選擇為您的首頁。</span><span class="sxs-lookup"><span data-stu-id="66626-109">Windows Mixed Reality has two default environments, Cliff House and Skyloft, that you can choose as your home.</span></span> <span data-ttu-id="66626-110">建立自訂的環境，可讓您擴充該清單與您自己的創作。</span><span class="sxs-lookup"><span data-stu-id="66626-110">Creating custom environments allows you to expand that list with your own creations.</span></span> <span data-ttu-id="66626-111">我們會提供此處於早期評估從建立者和開發人員感興趣，請參閱何種世界您建立，，和了解如何使用不同的撰寫工具的狀態。</span><span class="sxs-lookup"><span data-stu-id="66626-111">We are making this available in an early state to evaluate interest from creators and developers, see what kinds of worlds you create, and understand how you work with different authoring tools.</span></span>

<span data-ttu-id="66626-112">時使用的自訂環境，您會發現該 teleporting，互動的應用程式，並將放置全像投影的運作方式就像它會以 Skyloft 與 Cliff 房子。</span><span class="sxs-lookup"><span data-stu-id="66626-112">When using a custom environment you'll notice that teleporting, interacting with apps, and placing holograms works just like it does in the Cliff House and Skyloft.</span></span> <span data-ttu-id="66626-113">您可以瀏覽網頁的幻想架構中或未來的縣 （市） 填入全像投影-有無限的可能性 ！</span><span class="sxs-lookup"><span data-stu-id="66626-113">You can browse the web in a fantasy landscape or fill a futuristic city with holograms - the possibilities are endless!</span></span>

## <a name="device-support"></a><span data-ttu-id="66626-114">裝置支援</span><span class="sxs-lookup"><span data-stu-id="66626-114">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="66626-115">功能</span><span class="sxs-lookup"><span data-stu-id="66626-115">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="66626-116"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="66626-116"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="66626-117"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="66626-117"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="66626-118">自訂的家庭環境</span><span class="sxs-lookup"><span data-stu-id="66626-118">Custom home environments</span></span></td><td style="text-align: center;"></td><td style="text-align: center;"> <span data-ttu-id="66626-119">✔️</span><span class="sxs-lookup"><span data-stu-id="66626-119">✔️</span></span></td>
</tr>
</table>

## <a name="trying-a-sample-environment"></a><span data-ttu-id="66626-120">嘗試的範例環境</span><span class="sxs-lookup"><span data-stu-id="66626-120">Trying a sample environment</span></span>

<span data-ttu-id="66626-121">我們已建立範例環境中，將展示一些自訂的家庭環境的創意的可能性。</span><span class="sxs-lookup"><span data-stu-id="66626-121">We've created a sample environment that shows off some of the creative possibilities of custom home environments.</span></span> <span data-ttu-id="66626-122">請遵循下列步驟來試試看：</span><span class="sxs-lookup"><span data-stu-id="66626-122">Follow these steps to try it out:</span></span>
1. <span data-ttu-id="66626-123">[下載我們的範例幻想島環境](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe)（自動解壓縮可執行檔的連結點為單位）。</span><span class="sxs-lookup"><span data-stu-id="66626-123">[Download our sample Fantasy Island environment](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (link points to self-extracting executable).</span></span>

    <span data-ttu-id="66626-124">![幻想島範例環境](images/FantasyLand.jpg)</span><span class="sxs-lookup"><span data-stu-id="66626-124">![Fantasy Island sample environment](images/FantasyLand.jpg)</span></span><br>
    <span data-ttu-id="66626-125">*幻想島範例環境*</span><span class="sxs-lookup"><span data-stu-id="66626-125">*Fantasy Island sample environment*</span></span><br>

2. <span data-ttu-id="66626-126">執行**Fantasy_Island.exe**剛才下載的檔案。</span><span class="sxs-lookup"><span data-stu-id="66626-126">Run the **Fantasy_Island.exe** file you just downloaded.</span></span>

    > [!NOTE]
    > <span data-ttu-id="66626-127">嘗試執行.exe 檔案 （例如這個） 網站下載，您可能會遇到 「 Windows 受保護您的電腦 」 快顯視窗。</span><span class="sxs-lookup"><span data-stu-id="66626-127">When attempting to run a .exe file downloaded from the web (like this one), you may encounter a "Windows protected your PC" pop-up.</span></span> <span data-ttu-id="66626-128">若要從這個快顯視窗中執行 Fantasy_Island.exe，請選取**進一歩**，然後**仍要執行**。</span><span class="sxs-lookup"><span data-stu-id="66626-128">To run Fantasy_Island.exe from this pop-up, select **More info** and then **Run anyway**.</span></span> <span data-ttu-id="66626-129">此安全性設定為了保護您免於下載的檔案，您不一定要信任，因此當您信任的來源檔案時請只選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="66626-129">This security setting is meant to protect you from downloading files you may not want to trust, so please only choose this option when you trust the source of the file.</span></span>

3. <span data-ttu-id="66626-130">開啟**檔案總管**並瀏覽至 [環境] 資料夾，藉由在 [網址] 列中貼上下列： `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`。</span><span class="sxs-lookup"><span data-stu-id="66626-130">Open **File Explorer** and navigate to the environments folder by pasting the following in the address bar: `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`.</span></span>
4. <span data-ttu-id="66626-131">將您下載的範例環境複製到這個資料夾中。</span><span class="sxs-lookup"><span data-stu-id="66626-131">Copy the sample environment that you downloaded into this folder.</span></span>
5. <span data-ttu-id="66626-132">重新啟動**混合實境入口網站**。</span><span class="sxs-lookup"><span data-stu-id="66626-132">Restart **Mixed Reality Portal**.</span></span> <span data-ttu-id="66626-133">這會重新整理在位置選擇器中的環境清單。</span><span class="sxs-lookup"><span data-stu-id="66626-133">This will refresh the list of environments in the Places picker.</span></span>
6. <span data-ttu-id="66626-134">置於耳機。</span><span class="sxs-lookup"><span data-stu-id="66626-134">Put on your headset.</span></span> <span data-ttu-id="66626-135">一旦您在家中，開啟 **[開始] 功能表**使用 Windows 按鈕您的控制器。</span><span class="sxs-lookup"><span data-stu-id="66626-135">Once you're in the home, open the **Start menu** using the Windows button your controller.</span></span>
7. <span data-ttu-id="66626-136">選取 **上的芳鄰**選擇家庭環境的已釘選應用程式清單上方的圖示。</span><span class="sxs-lookup"><span data-stu-id="66626-136">Select the **Places** icon above the list of pinned apps to choose a home environment.</span></span>
8. <span data-ttu-id="66626-137">您會發現您在清單中的位置中下載的幻想島環境。</span><span class="sxs-lookup"><span data-stu-id="66626-137">You will find the Fantasy Island environment that you downloaded in your list of places.</span></span> <span data-ttu-id="66626-138">選取 **幻想島**輸入在新的自訂家庭環境 ！</span><span class="sxs-lookup"><span data-stu-id="66626-138">Select **Fantasy Island** to enter your new custom home environment!</span></span>

## <a name="creating-your-own-custom-environment"></a><span data-ttu-id="66626-139">建立您自己的自訂環境</span><span class="sxs-lookup"><span data-stu-id="66626-139">Creating your own custom environment</span></span>

<span data-ttu-id="66626-140">除了使用我們的範例環境，您可以匯出您自己自訂的環境，使用您最愛的 3D 編輯軟體。</span><span class="sxs-lookup"><span data-stu-id="66626-140">In addition to using our sample environments, you can export your own custom environments using your favorite 3D editing software.</span></span> 

### <a name="modeling-guidelines"></a><span data-ttu-id="66626-141">模型化的指導方針</span><span class="sxs-lookup"><span data-stu-id="66626-141">Modeling guidelines</span></span>

<span data-ttu-id="66626-142">當模型化您的環境，請注意下列建議。</span><span class="sxs-lookup"><span data-stu-id="66626-142">When modeling your environment, keep the following recommendations in mind.</span></span> <span data-ttu-id="66626-143">這有助於確保以正確的方向 believably 大小的世界中的使用者會產生：</span><span class="sxs-lookup"><span data-stu-id="66626-143">This will help ensure the user spawns in the correct orientation in a believably-sized world:</span></span>

1. <span data-ttu-id="66626-144">使用者會繁衍 0,0,0 因此中心所需的繁衍您的位置原點為中心。</span><span class="sxs-lookup"><span data-stu-id="66626-144">Users will spawn at 0,0,0 so center your desired spawn location around the origin.</span></span>
2. <span data-ttu-id="66626-145">工作單位應該設定以公尺為單位，以便可以撰寫全球規模的資產。</span><span class="sxs-lookup"><span data-stu-id="66626-145">Working Units should be set to meters so that assets can be authored at world scale.</span></span>
3. <span data-ttu-id="66626-146">總軸應該設定為"Y"。</span><span class="sxs-lookup"><span data-stu-id="66626-146">The Up axis should be set to “Y”.</span></span>
4. <span data-ttu-id="66626-147">資產應該面臨"forward"朝向正 Z 軸。</span><span class="sxs-lookup"><span data-stu-id="66626-147">The asset should face “forward” towards the positive Z axis.</span></span>
5. <span data-ttu-id="66626-148">所有的網格不需要合併，但建議如果您的目標資源受限的裝置。</span><span class="sxs-lookup"><span data-stu-id="66626-148">All meshes do not need to be combined, but it is recommended if you are targeting resource-constrained devices.</span></span>

### <a name="exporting-your-environment"></a><span data-ttu-id="66626-149">匯出您的環境</span><span class="sxs-lookup"><span data-stu-id="66626-149">Exporting your environment</span></span>

<span data-ttu-id="66626-150">Windows Mixed Reality 依賴二進位 glTF (.glb) 做為資產的傳遞格式的環境。</span><span class="sxs-lookup"><span data-stu-id="66626-150">Windows Mixed Reality relies on binary glTF (.glb) as the asset delivery format for environments.</span></span> <span data-ttu-id="66626-151">glTF 是獲微軟授權使用 3D 資產傳遞 Khronos 群組所維護的免費開放標準。</span><span class="sxs-lookup"><span data-stu-id="66626-151">glTF is a royalty free open standard for 3D asset delivery maintained by the Khronos group.</span></span> <span data-ttu-id="66626-152">隨著 glTF 發展為一種業界標準的可互通的 3D 內容，因此會 Microsoft 的支援格式會在 Windows 應用程式和體驗。</span><span class="sxs-lookup"><span data-stu-id="66626-152">As glTF evolves as an industry standard for interoperable 3D content, so will Microsoft’s support for the format across Windows apps and experiences.</span></span>

<span data-ttu-id="66626-153">匯出資產，以用作自訂家庭環境的第一個步驟產生 glTF 2.0 模型。</span><span class="sxs-lookup"><span data-stu-id="66626-153">The first step in exporting assets to be used as custom home environments is generating a glTF 2.0 model.</span></span> <span data-ttu-id="66626-154">GlTF 工作群組會維護[份支援匯出工具和轉換器](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters)建立 glTF 2.0 模型。</span><span class="sxs-lookup"><span data-stu-id="66626-154">The glTF working group maintains a [list of supported exporters and converters](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) to create a glTF 2.0 model.</span></span> <span data-ttu-id="66626-155">若要開始，使用本頁列出的程式來建立和匯出 glTF 2.0 模型，或轉換現有的模型使用其中一個支援的轉換器。</span><span class="sxs-lookup"><span data-stu-id="66626-155">To get started, use one of the programs listed on this page to create and export a glTF 2.0 model, or convert an existing model using one of the supported converters.</span></span>

<span data-ttu-id="66626-156">此外，請參閱[很有幫助本文](https://www.khronos.org/blog/art-pipeline-for-gltf)這提供封面流程概觀匯出 glTF 模型從 「 blender 」 和 3DS Max 直接。</span><span class="sxs-lookup"><span data-stu-id="66626-156">Additionally, check out [this helpful article](https://www.khronos.org/blog/art-pipeline-for-gltf) which provides an overview of an art workflow for exporting glTF models from Blender and 3DS Max directly.</span></span> 

### <a name="environment-limits"></a><span data-ttu-id="66626-157">環境的限制</span><span class="sxs-lookup"><span data-stu-id="66626-157">Environment limits</span></span>

<span data-ttu-id="66626-158">所有的環境必須是 < 256 mb。</span><span class="sxs-lookup"><span data-stu-id="66626-158">All environments must be < 256 mbs.</span></span> <span data-ttu-id="66626-159">大於 256 mb 為單位的環境將無法載入，並改為使用空的世界就預設天空盒周圍的使用者使用。</span><span class="sxs-lookup"><span data-stu-id="66626-159">Environments larger than 256 mbs will fail to load and fall back to an empty world with just the default skybox surrounding the user.</span></span> <span data-ttu-id="66626-160">建立您的模型時，請記住此檔案的大小限制。</span><span class="sxs-lookup"><span data-stu-id="66626-160">Please keep this file size limit in mind when creating your models.</span></span> <span data-ttu-id="66626-161">此外，如果您打算使用 WindowsMRAssetConverter，如下所述進行環境最佳化，是 cognizant 紋理大小，將會增加，因為最佳化工具會建立紋理，具有較大的檔案大小，但更快載入。</span><span class="sxs-lookup"><span data-stu-id="66626-161">Additionally, if you plan to optimize your environment using the WindowsMRAssetConverter as described below, be cognizant that the texture size will increase as the optimizer creates textures that have a larger file size, but load faster.</span></span> 

### <a name="optimizing-your-environment"></a><span data-ttu-id="66626-162">將您的環境最佳化</span><span class="sxs-lookup"><span data-stu-id="66626-162">Optimizing your environment</span></span>

<span data-ttu-id="66626-163">Windows Mixed Reality 支援許多選用的最佳化功能，可大幅縮短載入時間，您的環境。</span><span class="sxs-lookup"><span data-stu-id="66626-163">Windows Mixed Reality supports a number of optional optimizations that will significantly reduce the load time of your environments.</span></span> <span data-ttu-id="66626-164">這可能會對大部分的紋理，環境來說尤其重要，因為他們有時會在載入時的逾時時間。</span><span class="sxs-lookup"><span data-stu-id="66626-164">This can be especially important for environments with many textures, as they will sometimes time out while loading.</span></span> <span data-ttu-id="66626-165">一般情況下，我們建議此步驟中的所有資產，不過，較小的環境，以幾個或低解析度的紋理不一定需要它。</span><span class="sxs-lookup"><span data-stu-id="66626-165">In general, we recommend this step for all assets, however, smaller environments with few or low-resolution textures won't always require it.</span></span> 

<span data-ttu-id="66626-166">為了簡化此程序，我們建立了[Windows 混合實境資產轉換子 （可在 GitHub 上）](https://github.com/Microsoft/glTF-Toolkit/releases)來執行您的最佳化。</span><span class="sxs-lookup"><span data-stu-id="66626-166">To make this process easier, we have created the [Windows Mixed Reality Asset Converter (available on GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases) to perform your optimizations.</span></span> <span data-ttu-id="66626-167">此工具會執行其他紋理封裝、 壓縮和解決方式向下調整，最佳化任何標準 2.0 glTF 或.glb 使用一組 Microsoft glTF 工具組中可用的公用程式。</span><span class="sxs-lookup"><span data-stu-id="66626-167">This tool uses a set of utilities available in the Microsoft glTF toolkit to optimize any standard 2.0 glTF or .glb by performing an additional texture packing, compression and resolution down-scaling.</span></span> 

<span data-ttu-id="66626-168">這個轉換子目前支援數目來調整最佳化的確切行為的旗標。</span><span class="sxs-lookup"><span data-stu-id="66626-168">The converter currently supports a number of flags to tweak the exact behavior of the optimizations.</span></span> <span data-ttu-id="66626-169">我們建議您執行下列的旗標，為獲得最佳結果：</span><span class="sxs-lookup"><span data-stu-id="66626-169">We recommend running with the following flags for best results:</span></span>

<span data-ttu-id="66626-170">Flag</span><span class="sxs-lookup"><span data-stu-id="66626-170">Flag</span></span>|<span data-ttu-id="66626-171">建議的值</span><span class="sxs-lookup"><span data-stu-id="66626-171">Recommended Value(s)</span></span>|<span data-ttu-id="66626-172">描述</span><span class="sxs-lookup"><span data-stu-id="66626-172">Description</span></span>
---|---|---
<span data-ttu-id="66626-173">-max-texture-size</span><span class="sxs-lookup"><span data-stu-id="66626-173">-max-texture-size</span></span>|<span data-ttu-id="66626-174">1024 或 2048</span><span class="sxs-lookup"><span data-stu-id="66626-174">1024 or 2048</span></span>| <span data-ttu-id="66626-175">調整此選項可改善紋理的品質，預設值是 512 x 512。</span><span class="sxs-lookup"><span data-stu-id="66626-175">Tweak this to improve the quality of the textures, default is 512x512.</span></span> <span data-ttu-id="66626-176">請注意，較大的值會大幅影響環境的檔案大小因此牢記在心 256 mb 的限制</span><span class="sxs-lookup"><span data-stu-id="66626-176">Note that a larger value will significantly impact the file size of the environment so keep the 256 mb limit in mind</span></span>
<span data-ttu-id="66626-177">-min-version</span><span class="sxs-lookup"><span data-stu-id="66626-177">-min-version</span></span>|<span data-ttu-id="66626-178">1803</span><span class="sxs-lookup"><span data-stu-id="66626-178">1803</span></span>|<span data-ttu-id="66626-179">舊版 windows 上才支援自訂的環境 > = 1803年。</span><span class="sxs-lookup"><span data-stu-id="66626-179">Custom environments are only supported on versions of windows >= 1803.</span></span> <span data-ttu-id="66626-180">這個旗標將會移除較舊版本的紋理，並減少檔案大小的最終的資產</span><span class="sxs-lookup"><span data-stu-id="66626-180">This flag will remove textures for older versions and reduce the file size of the final asset</span></span>

<span data-ttu-id="66626-181">例如: </span><span class="sxs-lookup"><span data-stu-id="66626-181">For example:</span></span>

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a><span data-ttu-id="66626-182">測試您的環境</span><span class="sxs-lookup"><span data-stu-id="66626-182">Testing your environment</span></span>

<span data-ttu-id="66626-183">您最終.glb 環境之後您即可耳機中測試它。</span><span class="sxs-lookup"><span data-stu-id="66626-183">Once you have your final .glb environment you're ready to test it out in the headset.</span></span> <span data-ttu-id="66626-184">步驟 2 中開始[「 嘗試的範例環境 」](#trying-a-sample-environment)家用混合實境中作為您的自訂環境的一節。</span><span class="sxs-lookup"><span data-stu-id="66626-184">Start at step 2 in the ["Trying a sample environment"](#trying-a-sample-environment) section to use your custom environment as the mixed reality home.</span></span> 

## <a name="feedback"></a><span data-ttu-id="66626-185">意見反應</span><span class="sxs-lookup"><span data-stu-id="66626-185">Feedback</span></span>

<span data-ttu-id="66626-186">雖然我們會評估此實驗性功能，我們想要了解您如何使用自訂環境、 任何您可能會遇到，有關的錯誤，且您要的功能的方式。</span><span class="sxs-lookup"><span data-stu-id="66626-186">While we're evaluating this experimental feature, we're interested in learning how you're using custom environments, any bugs you may encounter, and how you like the feature.</span></span> <span data-ttu-id="66626-187">請分享建立和使用自訂的家庭環境中的所有意見反應[開發人員論壇](https://forums.hololens.com/categories/custom-home-environments)。</span><span class="sxs-lookup"><span data-stu-id="66626-187">Please share any and all feedback for creating and using custom home environments in the [developer forums](https://forums.hololens.com/categories/custom-home-environments).</span></span>

## <a name="troubleshooting-and-tips"></a><span data-ttu-id="66626-188">疑難排解與秘訣</span><span class="sxs-lookup"><span data-stu-id="66626-188">Troubleshooting and tips</span></span>

### <a name="how-do-i-change-the-name-of-the-environment"></a><span data-ttu-id="66626-189">如何變更環境的名稱？</span><span class="sxs-lookup"><span data-stu-id="66626-189">How do I change the name of the environment?</span></span>

<span data-ttu-id="66626-190">[環境] 資料夾中的檔案名稱將用於在位置選擇器中。</span><span class="sxs-lookup"><span data-stu-id="66626-190">The file name in the environments folder will be used in the Places picker.</span></span> <span data-ttu-id="66626-191">若要變更您的環境名稱只是重新命名環境檔案名稱，並重新混合實境入口網站。</span><span class="sxs-lookup"><span data-stu-id="66626-191">To change the name of your environment simply rename the environment file name, and then restart Mixed Reality Portal.</span></span>

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a><span data-ttu-id="66626-192">如何從我的位置選擇器中移除自訂環境？</span><span class="sxs-lookup"><span data-stu-id="66626-192">How do I remove custom environments from my Places picker?</span></span>

<span data-ttu-id="66626-193">若要移除的自訂環境，請開啟 在您的電腦上的 環境 資料夾 (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) 和刪除環境。</span><span class="sxs-lookup"><span data-stu-id="66626-193">To remove a custom environment, open the environments folder on your PC (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) and delete the environment.</span></span> <span data-ttu-id="66626-194">一旦您重新啟動混合實境入口網站，此環境不會再出現在位置選擇器中。</span><span class="sxs-lookup"><span data-stu-id="66626-194">Once you restart Mixed Reality Portal, this environment will no longer appear in the Places picker.</span></span> 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a><span data-ttu-id="66626-195">如何 default 我最愛的自訂環境？</span><span class="sxs-lookup"><span data-stu-id="66626-195">How do I default to my favorite custom environment?</span></span>

<span data-ttu-id="66626-196">您目前無法變更預設環境。</span><span class="sxs-lookup"><span data-stu-id="66626-196">You can't currently change the default environment.</span></span> <span data-ttu-id="66626-197">每次您重新啟動混合實境入口網站中，您會返回 Cliff 房屋環境。</span><span class="sxs-lookup"><span data-stu-id="66626-197">Each time you restart Mixed Reality Portal, you will be returned to the Cliff House environment.</span></span> 

### <a name="i-spawn-into-a-blank-space"></a><span data-ttu-id="66626-198">我繁衍 （spawn) 至空白空間</span><span class="sxs-lookup"><span data-stu-id="66626-198">I spawn into a blank space</span></span>

<span data-ttu-id="66626-199">Windows Mixed Reality[不支援超過 256 mb 的環境](#environment-limits)。</span><span class="sxs-lookup"><span data-stu-id="66626-199">Windows Mixed Reality [doesn't support environments that exceed 256 mb](#environment-limits).</span></span> <span data-ttu-id="66626-200">當環境超出此限制時，您將登陸在空白的天空方塊中，不具有模型。</span><span class="sxs-lookup"><span data-stu-id="66626-200">When an environment exceeds this limit, you will land in the empty sky box with no model.</span></span>

### <a name="it-takes-a-long-time-to-load-my-environment"></a><span data-ttu-id="66626-201">花費很長的時間，以載入我的環境</span><span class="sxs-lookup"><span data-stu-id="66626-201">It takes a long time to load my environment</span></span>

<span data-ttu-id="66626-202">您可以新增選用的最佳化您的環境，讓它更快載入。</span><span class="sxs-lookup"><span data-stu-id="66626-202">You can add optional optimizations to your environment to make it load faster.</span></span> <span data-ttu-id="66626-203">請參閱[< 最佳化您的環境 >](#optimizing-your-environment)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="66626-203">See ["Optimizing your environment"](#optimizing-your-environment) for details.</span></span>

### <a name="the-scale-of-my-environment-is-incorrect"></a><span data-ttu-id="66626-204">我的環境的縮放比例不正確</span><span class="sxs-lookup"><span data-stu-id="66626-204">The scale of my environment is incorrect</span></span>

<span data-ttu-id="66626-205">載入環境時，Windows Mixed Reality 將轉譯 glTF 單位，以 1 公尺。</span><span class="sxs-lookup"><span data-stu-id="66626-205">Windows Mixed Reality translates glTF units to 1 meter when loading environments.</span></span> <span data-ttu-id="66626-206">如果您的環境載入非預期的小數位數，再次檢查您的匯出工具，以確保您正在建立模型 1 公尺的縮放比例。</span><span class="sxs-lookup"><span data-stu-id="66626-206">If your environment loads up an unexpected scale, double check your exporter to ensure that you're modeling at a 1 meter scale.</span></span> 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a><span data-ttu-id="66626-207">在 我的環境中繁衍位置不正確</span><span class="sxs-lookup"><span data-stu-id="66626-207">The spawn location in my environment is incorrect</span></span>

<span data-ttu-id="66626-208">預設繁衍位置位於 0,0,0 在環境中。</span><span class="sxs-lookup"><span data-stu-id="66626-208">The default spawn location is located at 0,0,0 in the environment.</span></span> <span data-ttu-id="66626-209">其目前無法自訂這個位置，因此您必須修改繁衍點位於所需的繁衍點的來源匯出您的環境。</span><span class="sxs-lookup"><span data-stu-id="66626-209">Its not currently possible to customize this location, so you must modify the spawn point by exporting your environment with the origin positioned at the desired spawn point.</span></span>

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a><span data-ttu-id="66626-210">聲音聽起來不正確的環境中</span><span class="sxs-lookup"><span data-stu-id="66626-210">The audio doesn't sound correct in the environment</span></span>

<span data-ttu-id="66626-211">當您建立您的自訂環境時，它會使用不符合您所建立的實體空間樂器轉譯模擬。</span><span class="sxs-lookup"><span data-stu-id="66626-211">When you create your custom environment, it will be using an acoustics rendering simulation that does not match the physical space you have created.</span></span> <span data-ttu-id="66626-212">音效可能來自錯誤的指示，並聽 muffled。</span><span class="sxs-lookup"><span data-stu-id="66626-212">Sound may come from the wrong directions and may sound muffled.</span></span> 

## <a name="see-also"></a><span data-ttu-id="66626-213">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66626-213">See also</span></span>
* [<span data-ttu-id="66626-214">瀏覽 Windows 混合實境首頁</span><span class="sxs-lookup"><span data-stu-id="66626-214">Navigating the Windows Mixed Reality Home</span></span>](#navigating-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="66626-215">混合實境資產轉換子 （於 GitHub) 的 Windows</span><span class="sxs-lookup"><span data-stu-id="66626-215">Windows Mixed Reality Asset Converter (on GitHub)</span></span>](https://github.com/Microsoft/glTF-Toolkit/releases)

