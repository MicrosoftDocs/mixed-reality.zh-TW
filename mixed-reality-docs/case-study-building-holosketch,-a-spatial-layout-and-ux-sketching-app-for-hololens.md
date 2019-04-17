---
title: 案例研究-建置 HoloSketch、 空間配置和草擬的 HoloLens 的應用程式的 UX
description: 裝置上的空間配置和 UX 草擬工具可協助您建立全像攝影版的體驗的 HoloLens HoloSketch。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch、 HoloLens、 Windows Mixed Reality，草擬，應用程式
ms.openlocfilehash: d7f94a09bf4a8a16000c2345adf1a046dab4bd15
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591867"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a><span data-ttu-id="102ba-104">案例研究-建置 HoloSketch、 空間配置和草擬的 HoloLens 的應用程式的 UX</span><span class="sxs-lookup"><span data-stu-id="102ba-104">Case study - Building HoloSketch, a spatial layout and UX sketching app for HoloLens</span></span>

<span data-ttu-id="102ba-105">裝置上的空間配置和 UX 草擬工具可協助您建立全像攝影版的體驗的 HoloLens HoloSketch。</span><span class="sxs-lookup"><span data-stu-id="102ba-105">HoloSketch is an on-device spatial layout and UX sketching tool for HoloLens to help build holographic experiences.</span></span> <span data-ttu-id="102ba-106">HoloSketch 搭配配對的藍芽鍵盤和滑鼠以及手勢及語音命令。</span><span class="sxs-lookup"><span data-stu-id="102ba-106">HoloSketch works with a paired Bluetooth keyboard and mouse as well as gesture and voice commands.</span></span> <span data-ttu-id="102ba-107">HoloSketch 的目的是提供一個簡單的 UX 版面配置工具快速的視覺效果和反覆項目。</span><span class="sxs-lookup"><span data-stu-id="102ba-107">The purpose of HoloSketch is to provide a simple UX layout tool for quick visualization and iteration.</span></span>

<span data-ttu-id="102ba-108">![HoloSketch:空間配置和草擬的 HoloLens 的應用程式的 UX 中。](images/holosketch-image-01-640px.png)</span><span class="sxs-lookup"><span data-stu-id="102ba-108">![HoloSketch: A spatial layout and UX sketching app for HoloLens.](images/holosketch-image-01-640px.png)</span></span><br>
<span data-ttu-id="102ba-109">*HoloSketch： 空間配置和草擬的 HoloLens 的應用程式的 UX*</span><span class="sxs-lookup"><span data-stu-id="102ba-109">*HoloSketch: spatial layout and UX sketching app for HoloLens*</span></span>

<span data-ttu-id="102ba-110">![簡單 UX 版面配置工具，快速的視覺效果和反覆項目。](images/holosketch-image-02.png)</span><span class="sxs-lookup"><span data-stu-id="102ba-110">![A simple UX layout tool for quick visualization and iteration.](images/holosketch-image-02.png)</span></span><br>
<span data-ttu-id="102ba-111">*簡單的 UX 版面配置工具的快速視覺效果和反覆項目*</span><span class="sxs-lookup"><span data-stu-id="102ba-111">*A simple UX layout tool for quick visualization and iteration*</span></span>

## <a name="features"></a><span data-ttu-id="102ba-112">功能</span><span class="sxs-lookup"><span data-stu-id="102ba-112">Features</span></span>

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a><span data-ttu-id="102ba-113">快速研究和小數位數原型設計的基本項目</span><span class="sxs-lookup"><span data-stu-id="102ba-113">Primitives for quick studies and scale-prototyping</span></span>

![使用基本的圖形](images/holosketch-primitives-giphy.gif)

<span data-ttu-id="102ba-115">您可以使用 基本的圖形快速聚集研究和原型設計的小數位數。</span><span class="sxs-lookup"><span data-stu-id="102ba-115">Use primitive shapes for quick massing studies and scale-prototyping.</span></span>

### <a name="import-objects-through-onedrive"></a><span data-ttu-id="102ba-116">透過 OneDrive 匯入物件</span><span class="sxs-lookup"><span data-stu-id="102ba-116">Import objects through OneDrive</span></span>

![匯入物件](images/holosketch-importobjects-giphy.gif)

<span data-ttu-id="102ba-118">匯入 PNG/JPG 影像或 3D FBX 物件 （需要封裝，Unity 中的） 至混合的實境空間透過 OneDrive。</span><span class="sxs-lookup"><span data-stu-id="102ba-118">Import PNG/JPG images or 3D FBX objects(requires packaging in Unity) into the mixed reality space through OneDrive.</span></span>

### <a name="manipulate-objects"></a><span data-ttu-id="102ba-119">管理物件</span><span class="sxs-lookup"><span data-stu-id="102ba-119">Manipulate objects</span></span>

![處理物件](images/manipulate-objects-640px.jpg)

<span data-ttu-id="102ba-121">操作與熟悉的 3D 物件介面的物件 （移動/旋轉/縮放比例）。</span><span class="sxs-lookup"><span data-stu-id="102ba-121">Manipulate objects (move/rotate/scale) with a familiar 3D object interface.</span></span>

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a><span data-ttu-id="102ba-122">藍芽、 滑鼠] / [鍵盤、 手勢和語音命令</span><span class="sxs-lookup"><span data-stu-id="102ba-122">Bluetooth, mouse/keyboard, gestures and voice commands</span></span>

![支援藍芽](images/supports-bluetooth-640px.jpg)

<span data-ttu-id="102ba-124">HoloSketch 支援藍芽滑鼠] / [鍵盤、 手勢和語音命令。</span><span class="sxs-lookup"><span data-stu-id="102ba-124">HoloSketch supports Bluetooth mouse/keyboard, gestures and voice commands.</span></span>

## <a name="background"></a><span data-ttu-id="102ba-125">背景</span><span class="sxs-lookup"><span data-stu-id="102ba-125">Background</span></span>

### <a name="importance-of-experiencing-your-design-in-the-device"></a><span data-ttu-id="102ba-126">發生在裝置中的設計的重要性</span><span class="sxs-lookup"><span data-stu-id="102ba-126">Importance of experiencing your design in the device</span></span>

<span data-ttu-id="102ba-127">當您設計的項目為 HoloLens 時，務必體驗您的裝置中的設計。</span><span class="sxs-lookup"><span data-stu-id="102ba-127">When you design something for HoloLens, it is important to experience your design in the device.</span></span> <span data-ttu-id="102ba-128">在混合的實境應用程式設計中最大的挑戰之一是很難概略了解的延展性、 位置與深度，尤其是透過傳統的 2D 草圖。</span><span class="sxs-lookup"><span data-stu-id="102ba-128">One of the biggest challenges in mixed reality app design is that it is hard to get the sense of scale, position and depth, especially through traditional 2D sketches.</span></span>

### <a name="cost-of-2d-based-communication"></a><span data-ttu-id="102ba-129">2D 的費用依通訊</span><span class="sxs-lookup"><span data-stu-id="102ba-129">Cost of 2D based communication</span></span>

<span data-ttu-id="102ba-130">若要有效地傳達 UX 流程和其他人的案例，設計工具可能會得到花很多時間來建立使用傳統的 2D 工具，例如 Illustrator、 Photoshop 和 PowerPoint 的資產。</span><span class="sxs-lookup"><span data-stu-id="102ba-130">To effectively communicate UX flows and scenarios to others, a designer may end up spending a lot of time creating assets using traditional 2D tools such as Illustrator, Photoshop and PowerPoint.</span></span> <span data-ttu-id="102ba-131">這些 2D 設計通常需要額外的工作，將它們轉換到 3D。</span><span class="sxs-lookup"><span data-stu-id="102ba-131">These 2D designs often require additional effort to convert them it into 3D.</span></span> <span data-ttu-id="102ba-132">一些構想是中遺失這項轉譯 2D 到 3D。</span><span class="sxs-lookup"><span data-stu-id="102ba-132">Some ideas are lost in this translation from 2D to 3D.</span></span>

### <a name="complex-deployment-process"></a><span data-ttu-id="102ba-133">複雜的部署程序</span><span class="sxs-lookup"><span data-stu-id="102ba-133">Complex deployment process</span></span>

<span data-ttu-id="102ba-134">混合的實境是我們新的畫布，因為它牽涉到大量的設計反覆項目和試驗和錯誤本質上。</span><span class="sxs-lookup"><span data-stu-id="102ba-134">Since mixed reality is a new canvas for us, it involves a lot of design iteration and trial and error by its nature.</span></span> <span data-ttu-id="102ba-135">不熟悉使用 Unity 和 Visual Studio 等工具的設計工具，它並不容易在 HoloLens 一起放置一些項目。</span><span class="sxs-lookup"><span data-stu-id="102ba-135">For designer who are not familiar with tools such as Unity and Visual Studio, it is not easy to put something together in HoloLens.</span></span> <span data-ttu-id="102ba-136">通常您必須完成以下程序以查看您的 2D/3D 圖檔，在裝置中。</span><span class="sxs-lookup"><span data-stu-id="102ba-136">Typically you have to go through the process below to see your 2D/3D artwork in the device.</span></span> <span data-ttu-id="102ba-137">這是快速反覆運算的想法和案例的設計工具的大障礙。</span><span class="sxs-lookup"><span data-stu-id="102ba-137">This was a big barrier for designers iterating on ideas and scenarios quickly.</span></span>

<span data-ttu-id="102ba-138">![複雜的部署程序](images/holosketch-image-03-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="102ba-138">![Complex deployment process](images/holosketch-image-03-1000px.png)</span></span><br>
<span data-ttu-id="102ba-139">*部署程序*</span><span class="sxs-lookup"><span data-stu-id="102ba-139">*Deployment process*</span></span>

### <a name="simplified-process-with-holosketch"></a><span data-ttu-id="102ba-140">使用 HoloSketch 的簡化程序</span><span class="sxs-lookup"><span data-stu-id="102ba-140">Simplified process with HoloSketch</span></span>

<span data-ttu-id="102ba-141">使用 HoloSketch，我們想要簡化這個程序不需要涉及開發工具，並將其裝置入口網站配對。</span><span class="sxs-lookup"><span data-stu-id="102ba-141">With HoloSketch, we wanted to simplify this process without involving development tools and device portal pairing.</span></span> <span data-ttu-id="102ba-142">使用 OneDrive，使用者可以輕鬆地將 2D/3D 資產置於 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="102ba-142">Using OneDrive, users can easily put 2D/3D assets into HoloLens.</span></span>

<span data-ttu-id="102ba-143">![使用 HoloSketch 的簡化程序](images/holosketch-image-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="102ba-143">![Simplified process with HoloSketch](images/holosketch-image-04-1000px.png)</span></span><br>
<span data-ttu-id="102ba-144">*使用 HoloSketch 的簡化程序*</span><span class="sxs-lookup"><span data-stu-id="102ba-144">*Simplified process with HoloSketch*</span></span>

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a><span data-ttu-id="102ba-145">令人滿意的三維的設計考慮與解決方案</span><span class="sxs-lookup"><span data-stu-id="102ba-145">Encouraging three-dimensional design thinking and solutions</span></span>

<span data-ttu-id="102ba-146">我們認為這項工具可讓設計工具有機會探索真正三維空間中的解決方案，並不會卡在 2D。</span><span class="sxs-lookup"><span data-stu-id="102ba-146">We thought this tool would give designers an opportunity to explore solutions in a truly three-dimensional space and not be stuck in 2D.</span></span> <span data-ttu-id="102ba-147">他們不必考慮由於背景是實際在 Hololens 的情況下，為其 UI 建立 3D 的背景。</span><span class="sxs-lookup"><span data-stu-id="102ba-147">They don’t have to think about creating a 3D background for their UI since the background is the real world in the case of Hololens.</span></span> <span data-ttu-id="102ba-148">HoloSketch 會開啟設計工具，可輕鬆地將 3D 設計探討 Hololens 的方式。</span><span class="sxs-lookup"><span data-stu-id="102ba-148">HoloSketch opens up a way for designers to easily explore 3D design on Hololens.</span></span>

## <a name="get-started"></a><span data-ttu-id="102ba-149">開始使用</span><span class="sxs-lookup"><span data-stu-id="102ba-149">Get Started</span></span>

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a><span data-ttu-id="102ba-150">如何將 HoloSketch 匯入的 2D 影像 (JPG/PNG)</span><span class="sxs-lookup"><span data-stu-id="102ba-150">How to import 2D images (JPG/PNG) into HoloSketch</span></span>

* <span data-ttu-id="102ba-151">JPG/PNG 影像上傳至您的 OneDrive 資料夾 ' 文件/HoloSketch '。</span><span class="sxs-lookup"><span data-stu-id="102ba-151">Upload JPG/PNG images to your OneDrive folder ‘Documents/HoloSketch’.</span></span>
* <span data-ttu-id="102ba-152">從 OneDrive 中的功能表 HoloSketch，您可以選取，然後放置在環境中的映像。</span><span class="sxs-lookup"><span data-stu-id="102ba-152">From the OneDrive menu in HoloSketch, you will be able to select and place the image in the environment.</span></span>

<span data-ttu-id="102ba-153">![匯入的 2D 影像](images/import-2d-images-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="102ba-153">![Importing 2D images](images/import-2d-images-1000px.jpg)</span></span><br>
<span data-ttu-id="102ba-154">*匯入映像和透過 OneDrive 的 3D 物件*</span><span class="sxs-lookup"><span data-stu-id="102ba-154">*Importing images and 3D objects through OneDrive*</span></span>

### <a name="how-to-import-3d-objects-into-holosketch"></a><span data-ttu-id="102ba-155">如何將 HoloSketch 匯入 3D 物件</span><span class="sxs-lookup"><span data-stu-id="102ba-155">How to import 3D objects into HoloSketch</span></span>

<span data-ttu-id="102ba-156">再上傳至您的 OneDrive 資料夾時，請遵循下列步驟來封裝您的 3D 物件至 Unity 資產套件組合。</span><span class="sxs-lookup"><span data-stu-id="102ba-156">Before uploading to your OneDrive folder, please follow the steps below to package your 3D objects into a Unity asset bundle.</span></span> <span data-ttu-id="102ba-157">使用此程序您可以從 3D 的軟體，例如 Maya、 電影院 4d 和 Microsoft 小畫家 3D 匯 FBX/OBJ 檔案。</span><span class="sxs-lookup"><span data-stu-id="102ba-157">Using this process you can import your FBX/OBJ files from 3D software such as Maya, Cinema 4D and Microsoft Paint 3D.</span></span>

>[!IMPORTANT]
><span data-ttu-id="102ba-158">目前，資產套件組合建立支援 Unity 版本 5.4.5f1。</span><span class="sxs-lookup"><span data-stu-id="102ba-158">Currently, asset bundle creation is supported with Unity version 5.4.5f1.</span></span>

1. <span data-ttu-id="102ba-159">下載並開啟 Unity 專案['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity)。</span><span class="sxs-lookup"><span data-stu-id="102ba-159">Download and open the Unity project ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span></span> <span data-ttu-id="102ba-160">這個 Unity 專案包含的套件組合的資產產生指令碼。</span><span class="sxs-lookup"><span data-stu-id="102ba-160">This Unity project includes the script for the bundle asset generation.</span></span>
2. <span data-ttu-id="102ba-161">建立新的 GameObject。</span><span class="sxs-lookup"><span data-stu-id="102ba-161">Create a new GameObject.</span></span>
3. <span data-ttu-id="102ba-162">命名內容為基礎的 GameObject。</span><span class="sxs-lookup"><span data-stu-id="102ba-162">Name the GameObject based on the contents.</span></span>
4. <span data-ttu-id="102ba-163">在 偵測器 面板中，按一下 新增元件並加入 ' 方塊 Collider'。</span><span class="sxs-lookup"><span data-stu-id="102ba-163">In the Inspector panel, click ‘Add Component’ and add ‘Box Collider’.</span></span> 

   ![在 [偵測器] 面板中，按一下 [加入元件]，然後新增 ' 方塊 Collider'](images/holosketch-10a-assetbundles-1000px.png)
   
   ![在 偵測器 面板中，按一下 新增元件，並加入 ' 方塊 Collider' #2](images/holosketch-10b-assetbundles-1000px.png)

5. <span data-ttu-id="102ba-166">匯入 3D FBX 檔拖曳到 [專案] 面板。</span><span class="sxs-lookup"><span data-stu-id="102ba-166">Import the 3D FBX file by dragging it into the project panel.</span></span>
6. <span data-ttu-id="102ba-167">將物件拖曳到 [階層] 面板**在新的 GameObject**。</span><span class="sxs-lookup"><span data-stu-id="102ba-167">Drag the object into the Hierarchy panel **under your new GameObject**.</span></span>

   ![將物件拖曳到 新的 GameObject 下的 階層 面板](images/holosketch-12-assetbundles-1000px.png)

7. <span data-ttu-id="102ba-169">如果不符合物件，請調整 collider 維度。</span><span class="sxs-lookup"><span data-stu-id="102ba-169">Adjust the collider dimension if it does not match the object.</span></span> <span data-ttu-id="102ba-170">旋轉物件面臨**z 軸**。</span><span class="sxs-lookup"><span data-stu-id="102ba-170">Rotate the object to face **Z-axis**.</span></span>

   ![如果不符合物件，請調整 collider 維度。](images/holosketch-13-assetbundles-1000px.png)

8. <span data-ttu-id="102ba-172">將物件從 [階層] 面板拖曳至 [專案] 面板來**使得 prefab**。</span><span class="sxs-lookup"><span data-stu-id="102ba-172">Drag the object from the Hierarchy panel to the Project panel to **make it prefab**.</span></span>
9. <span data-ttu-id="102ba-173">[偵測器] 面板底部，按一下下拉式清單中，建立並指派新的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="102ba-173">On the bottom of the inspector panel, click the dropdown, create and assign a new unique name.</span></span> <span data-ttu-id="102ba-174">下列範例示範如何新增及指派 'brownchair' AssetBundle 名稱。</span><span class="sxs-lookup"><span data-stu-id="102ba-174">Below example shows adding and assigning 'brownchair' for the AssetBundle Name.</span></span> 

   ![在 [偵測器] 面板底部，按一下下拉式清單中，指派新的唯一名稱。](images/holosketch-14-assetbundles-1000px.png)

10. <span data-ttu-id="102ba-176">準備模型物件的縮圖影像。</span><span class="sxs-lookup"><span data-stu-id="102ba-176">Prepare a thumbnail image for the model object.</span></span> 
   <span data-ttu-id="102ba-177">![將影像拖曳到 [專案] 面板，並指派物件的名稱。](images/holosketch-15-assetbundles-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="102ba-177">![Drag an image into the project panel and assign the name used for the object.](images/holosketch-15-assetbundles-1000px.png)</span></span>

11. <span data-ttu-id="102ba-178">Unity 專案的 '資產' 資料夾下建立名為 'Assetbundles' 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="102ba-178">Create a folder named ‘Assetbundles’ under the Unity project’s ‘Asset’ folder.</span></span>

12. <span data-ttu-id="102ba-179">從 [資產] 功能表中，選取 [產生檔案的 ' 建置 AssetBundles']。</span><span class="sxs-lookup"><span data-stu-id="102ba-179">From the Assets menu, select ‘Build AssetBundles’ to generate file.</span></span> 
   <span data-ttu-id="102ba-180">![從 [資產] 功能表中，選取 [產生檔案的 ' 建置 AssetBundles']。](images/holosketch-15a-assetbundles.png)</span><span class="sxs-lookup"><span data-stu-id="102ba-180">![From the Assets menu, select ‘Build AssetBundles’ to generate file.](images/holosketch-15a-assetbundles.png)</span></span>


13. <span data-ttu-id="102ba-181">**將產生的檔案上傳到 OneDrive /Files/Documents/HoloSketch 資料夾。**</span><span class="sxs-lookup"><span data-stu-id="102ba-181">**Upload the generated file to the /Files/Documents/HoloSketch folder on OneDrive.**</span></span> <span data-ttu-id="102ba-182">上傳僅 asset_unique_name 檔案。</span><span class="sxs-lookup"><span data-stu-id="102ba-182">Upload the asset_unique_name file only.</span></span> <span data-ttu-id="102ba-183">您不需要上傳資訊清單檔案或 AssetBundles 檔案。</span><span class="sxs-lookup"><span data-stu-id="102ba-183">You don’t need to upload manifest files or AssetBundles file.</span></span> <br>
<span data-ttu-id="102ba-184">![將檔案新增至檔案/文件/HoloSketch/資料夾](images/holosketch-onedriveupload-1000px.png)
![您會看到已新增的 HoloSketch 的 OneDrive 功能表中的 3D 物件](images/holosketch-14-onedriveexample-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="102ba-184">![Add files to Files/Documents/HoloSketch/ folder](images/holosketch-onedriveupload-1000px.png)
![You will see added 3D object in HoloSketch's OneDrive menu](images/holosketch-14-onedriveexample-1000px.jpg)</span></span>

## <a name="how-to-manipulate-the-objects"></a><span data-ttu-id="102ba-185">如何管理物件</span><span class="sxs-lookup"><span data-stu-id="102ba-185">How to manipulate the objects</span></span>

<span data-ttu-id="102ba-186">HoloSketch 支援廣泛使用的傳統介面中 3D 的軟體。</span><span class="sxs-lookup"><span data-stu-id="102ba-186">HoloSketch supports the traditional interface that is widely used in 3D software.</span></span> <span data-ttu-id="102ba-187">您可以使用移動、 旋轉、 縮放筆勢和滑鼠的物件。</span><span class="sxs-lookup"><span data-stu-id="102ba-187">You can use move, rotate, scale the objects with gestures and a mouse.</span></span> <span data-ttu-id="102ba-188">您可以快速切換不同的模式，透過語音或鍵盤。</span><span class="sxs-lookup"><span data-stu-id="102ba-188">You can quickly switch between different modes with voice or keyboard.</span></span>

### <a name="object-manipulation-modes"></a><span data-ttu-id="102ba-189">物件的操作模式</span><span class="sxs-lookup"><span data-stu-id="102ba-189">Object manipulation modes</span></span>

<span data-ttu-id="102ba-190">![如何管理物件](images/holosketch-image-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="102ba-190">![How to manipulate the objects](images/holosketch-image-06-1000px.png)</span></span><br>
<span data-ttu-id="102ba-191">*如何管理物件*</span><span class="sxs-lookup"><span data-stu-id="102ba-191">*How to manipulate the objects*</span></span>

### <a name="contextual-and-tool-belt-menus"></a><span data-ttu-id="102ba-192">內容 與 工具 功能表</span><span class="sxs-lookup"><span data-stu-id="102ba-192">Contextual and Tool Belt menus</span></span>

<span data-ttu-id="102ba-193">**使用操作功能表**</span><span class="sxs-lookup"><span data-stu-id="102ba-193">**Using the Contextual Menu**</span></span>

<span data-ttu-id="102ba-194">若要開啟操作功能表的雙精度浮點空中點選。</span><span class="sxs-lookup"><span data-stu-id="102ba-194">Double air tap to open the Contextual Menu.</span></span> 

<span data-ttu-id="102ba-195">功能表項目：</span><span class="sxs-lookup"><span data-stu-id="102ba-195">Menu items:</span></span>
* <span data-ttu-id="102ba-196">**配置的介面：** 這是 3D 方格系統，您可以配置多個物件，並以群組方式管理它們。</span><span class="sxs-lookup"><span data-stu-id="102ba-196">**Layout Surface:** This is a 3D grid system where you can layout multiple objects and manage them as a group.</span></span> <span data-ttu-id="102ba-197">將物件新增至該版面配置介面上 double 空中點選。</span><span class="sxs-lookup"><span data-stu-id="102ba-197">Double air-tap on the Layout Surface to add objects to it.</span></span>
* <span data-ttu-id="102ba-198">**基本項目：** 使用 cube、 陳列、 圓柱和圓錐體聚集研究。</span><span class="sxs-lookup"><span data-stu-id="102ba-198">**Primitives:** Use cubes, spheres, cylinders and cones for massing studies.</span></span>
* <span data-ttu-id="102ba-199">**OneDrive:** 開啟 [OneDrive] 功能表，以匯入物件。</span><span class="sxs-lookup"><span data-stu-id="102ba-199">**OneDrive:** Open the OneDrive menu to import objects.</span></span>
* <span data-ttu-id="102ba-200">**說明：** 顯示說明畫面。</span><span class="sxs-lookup"><span data-stu-id="102ba-200">**Help:** Displays help screen.</span></span>

<span data-ttu-id="102ba-201">![操作功能表](images/holosketch-image-07.png)</span><span class="sxs-lookup"><span data-stu-id="102ba-201">![Contextual menu](images/holosketch-image-07.png)</span></span><br>
<span data-ttu-id="102ba-202">*操作功能表*</span><span class="sxs-lookup"><span data-stu-id="102ba-202">*Contextual menu*</span></span>

<span data-ttu-id="102ba-203">**使用工具帶狀功能表**</span><span class="sxs-lookup"><span data-stu-id="102ba-203">**Using the Tool Belt Menu**</span></span>

<span data-ttu-id="102ba-204">移動、 旋轉，小數位數、 儲存和載入場景都是從工具帶狀功能表。</span><span class="sxs-lookup"><span data-stu-id="102ba-204">Move, Rotate, Scale, Save, and Load Scene are available from the Tool Belt Menu.</span></span> 

## <a name="using-keyboard-gestures-and-voice-commands"></a><span data-ttu-id="102ba-205">使用鍵盤、 手勢及語音命令</span><span class="sxs-lookup"><span data-stu-id="102ba-205">Using keyboard, gestures and voice commands</span></span>

<span data-ttu-id="102ba-206">![鍵盤、 手勢及語音命令](images/holosketch-image-08-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="102ba-206">![Keyboard, Gestures and Voice Commands](images/holosketch-image-08-1000px.png)</span></span><br>
<span data-ttu-id="102ba-207">*鍵盤、 筆勢和語音命令*</span><span class="sxs-lookup"><span data-stu-id="102ba-207">*Keyboard, gestures, and voice commands*</span></span>

## <a name="download-the-app"></a><span data-ttu-id="102ba-208">下載應用程式</span><span class="sxs-lookup"><span data-stu-id="102ba-208">Download the app</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><span data-ttu-id="102ba-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">下載並安裝免費 Microsoft Store HoloSketch 應用程式</a>
</span><span class="sxs-lookup"><span data-stu-id="102ba-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Download and install the HoloSketch app for free from the Microsoft Store</a>
</span></span></td>
</tr>
</table>

## <a name="known-issues"></a><span data-ttu-id="102ba-210">已知問題</span><span class="sxs-lookup"><span data-stu-id="102ba-210">Known issues</span></span>
* <span data-ttu-id="102ba-211">目前資產套件組合建立支援**Unity 版本 5.4.5f1。**</span><span class="sxs-lookup"><span data-stu-id="102ba-211">Currently asset bundle creation is supported with **Unity version 5.4.5f1.**</span></span>
* <span data-ttu-id="102ba-212">根據您的 OneDrive 中的資料數量的應用程式可能會出現如同它已停止載入 OneDrive 內容時</span><span class="sxs-lookup"><span data-stu-id="102ba-212">Depending on the amount of data in your OneDrive, the app might appear as if it has stopped while loading OneDrive contents</span></span>
* <span data-ttu-id="102ba-213">目前，儲存並載入功能僅支援基本的物件</span><span class="sxs-lookup"><span data-stu-id="102ba-213">Currently, Save and Load feature only supports primitive objects</span></span>
* <span data-ttu-id="102ba-214">操作功能表上的文字、 聲音、 視訊和相片的功能表會停用</span><span class="sxs-lookup"><span data-stu-id="102ba-214">Text, Sound, Video and Photo menus are disabled on the contextual menu</span></span>
* <span data-ttu-id="102ba-215">在 [工具] 功能表上的 [播放] 按鈕會清除操作 gizmo</span><span class="sxs-lookup"><span data-stu-id="102ba-215">The Play button on the Tool Belt menu clears the manipulation gizmos</span></span>

## <a name="sharing-your-sketches"></a><span data-ttu-id="102ba-216">共用您的草圖</span><span class="sxs-lookup"><span data-stu-id="102ba-216">Sharing your sketches</span></span>

<span data-ttu-id="102ba-217">您可以使用視訊錄製中的功能 HoloLens 說明 ' 嘿 Cortana 開始/停止錄製 '。</span><span class="sxs-lookup"><span data-stu-id="102ba-217">You can use the video recording feature in HoloLens by saying 'Hey Cortana, Start/Stop recording'.</span></span> <span data-ttu-id="102ba-218">按向上/向下一起為您的草圖的索引鍵的磁碟區。</span><span class="sxs-lookup"><span data-stu-id="102ba-218">Press the volume up/down key together to take a picture of your sketch.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="102ba-219">關於作者</span><span class="sxs-lookup"><span data-stu-id="102ba-219">About the authors</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="102ba-220"><b>盾 Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="102ba-220"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="102ba-221">UX 設計工具 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="102ba-221">UX Designer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="102ba-222"><b>Patrick Sebring</b></span><span class="sxs-lookup"><span data-stu-id="102ba-222"><b>Patrick Sebring</b></span></span><br><span data-ttu-id="102ba-223">開發人員 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="102ba-223">Developer @Microsoft</span></span></td>
</tr>
</table> 
