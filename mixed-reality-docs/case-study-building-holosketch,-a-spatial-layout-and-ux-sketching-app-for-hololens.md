---
title: 個案研究-建立 HoloSketch、適用于 HoloLens 的空間配置和 UX 草繪應用程式
description: HoloSketch 是適用于 HoloLens 的裝置空間配置和 UX 草繪工具，可協助打造全像攝影體驗。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch，HoloLens，Windows Mixed Reality，草繪，應用程式
ms.openlocfilehash: d6d22aae7709bcc1a33b142a100d1a0f9645d3cc
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436950"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a><span data-ttu-id="c2424-104">個案研究-建立 HoloSketch、適用于 HoloLens 的空間配置和 UX 草繪應用程式</span><span class="sxs-lookup"><span data-stu-id="c2424-104">Case study - Building HoloSketch, a spatial layout and UX sketching app for HoloLens</span></span>

<span data-ttu-id="c2424-105">HoloSketch 是適用于 HoloLens 的裝置空間配置和 UX 草繪工具，可協助打造全像攝影體驗。</span><span class="sxs-lookup"><span data-stu-id="c2424-105">HoloSketch is an on-device spatial layout and UX sketching tool for HoloLens to help build holographic experiences.</span></span> <span data-ttu-id="c2424-106">HoloSketch 適用于配對的藍牙鍵盤和滑鼠，以及筆勢和語音命令。</span><span class="sxs-lookup"><span data-stu-id="c2424-106">HoloSketch works with a paired Bluetooth keyboard and mouse as well as gesture and voice commands.</span></span> <span data-ttu-id="c2424-107">HoloSketch 的目的是要提供簡單的 UX 版面組態工具，以進行快速視覺化和反復專案。</span><span class="sxs-lookup"><span data-stu-id="c2424-107">The purpose of HoloSketch is to provide a simple UX layout tool for quick visualization and iteration.</span></span>

<span data-ttu-id="c2424-108">![HoloSketch： HoloLens 的空間配置和 UX 草繪應用程式。](images/holosketch-image-01-640px.png)</span><span class="sxs-lookup"><span data-stu-id="c2424-108">![HoloSketch: A spatial layout and UX sketching app for HoloLens.](images/holosketch-image-01-640px.png)</span></span><br>
<span data-ttu-id="c2424-109">*HoloSketch： HoloLens 的空間配置和 UX 草繪應用程式*</span><span class="sxs-lookup"><span data-stu-id="c2424-109">*HoloSketch: spatial layout and UX sketching app for HoloLens*</span></span>

<span data-ttu-id="c2424-110">![簡單的 UX 版面組態工具來快速視覺化和反復專案。](images/holosketch-image-02.png)</span><span class="sxs-lookup"><span data-stu-id="c2424-110">![A simple UX layout tool for quick visualization and iteration.](images/holosketch-image-02.png)</span></span><br>
<span data-ttu-id="c2424-111">*簡單的 UX 版面組態工具，用於快速視覺化和反復專案*</span><span class="sxs-lookup"><span data-stu-id="c2424-111">*A simple UX layout tool for quick visualization and iteration*</span></span>

## <a name="features"></a><span data-ttu-id="c2424-112">功能</span><span class="sxs-lookup"><span data-stu-id="c2424-112">Features</span></span>

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a><span data-ttu-id="c2424-113">快速研究和擴展原型的基本專案</span><span class="sxs-lookup"><span data-stu-id="c2424-113">Primitives for quick studies and scale-prototyping</span></span>

![使用基本圖案](images/holosketch-primitives-giphy.gif)

<span data-ttu-id="c2424-115">使用基本圖形進行快速的 massing 研究和調整原型。</span><span class="sxs-lookup"><span data-stu-id="c2424-115">Use primitive shapes for quick massing studies and scale-prototyping.</span></span>

### <a name="import-objects-through-onedrive"></a><span data-ttu-id="c2424-116">透過 OneDrive 匯入物件</span><span class="sxs-lookup"><span data-stu-id="c2424-116">Import objects through OneDrive</span></span>

![匯入物件](images/holosketch-importobjects-giphy.gif)

<span data-ttu-id="c2424-118">將 PNG/JPG 影像或 3D FBX 物件（需要在 Unity 中封裝）匯入到混合的現實空間（透過 OneDrive）。</span><span class="sxs-lookup"><span data-stu-id="c2424-118">Import PNG/JPG images or 3D FBX objects(requires packaging in Unity) into the mixed reality space through OneDrive.</span></span>

### <a name="manipulate-objects"></a><span data-ttu-id="c2424-119">操作物件</span><span class="sxs-lookup"><span data-stu-id="c2424-119">Manipulate objects</span></span>

![操作物件](images/manipulate-objects-640px.jpg)

<span data-ttu-id="c2424-121">使用熟悉的3D 物件介面操作物件（移動/旋轉/縮放）。</span><span class="sxs-lookup"><span data-stu-id="c2424-121">Manipulate objects (move/rotate/scale) with a familiar 3D object interface.</span></span>

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a><span data-ttu-id="c2424-122">藍牙、滑鼠/鍵盤、手勢和語音命令</span><span class="sxs-lookup"><span data-stu-id="c2424-122">Bluetooth, mouse/keyboard, gestures and voice commands</span></span>

![支援藍牙](images/supports-bluetooth-640px.jpg)

<span data-ttu-id="c2424-124">HoloSketch 支援藍牙滑鼠/鍵盤、手勢和語音命令。</span><span class="sxs-lookup"><span data-stu-id="c2424-124">HoloSketch supports Bluetooth mouse/keyboard, gestures and voice commands.</span></span>

## <a name="background"></a><span data-ttu-id="c2424-125">背景</span><span class="sxs-lookup"><span data-stu-id="c2424-125">Background</span></span>

### <a name="importance-of-experiencing-your-design-in-the-device"></a><span data-ttu-id="c2424-126">在裝置中體驗設計的重要性</span><span class="sxs-lookup"><span data-stu-id="c2424-126">Importance of experiencing your design in the device</span></span>

<span data-ttu-id="c2424-127">當您設計 HoloLens 的某個專案時，請務必在裝置中體驗您的設計。</span><span class="sxs-lookup"><span data-stu-id="c2424-127">When you design something for HoloLens, it is important to experience your design in the device.</span></span> <span data-ttu-id="c2424-128">混合現實應用程式設計最大的挑戰之一，就是很難瞭解規模、位置和深度，特別是透過傳統2D 草圖。</span><span class="sxs-lookup"><span data-stu-id="c2424-128">One of the biggest challenges in mixed reality app design is that it is hard to get the sense of scale, position and depth, especially through traditional 2D sketches.</span></span>

### <a name="cost-of-2d-based-communication"></a><span data-ttu-id="c2424-129">以2D 為基礎的通訊成本</span><span class="sxs-lookup"><span data-stu-id="c2424-129">Cost of 2D based communication</span></span>

<span data-ttu-id="c2424-130">若要有效地將 UX 流程和案例傳達給其他人，設計人員可能會花很多時間來使用傳統2D 工具（例如 Illustrator、Photoshop 和 PowerPoint）來建立資產。</span><span class="sxs-lookup"><span data-stu-id="c2424-130">To effectively communicate UX flows and scenarios to others, a designer may end up spending a lot of time creating assets using traditional 2D tools such as Illustrator, Photoshop and PowerPoint.</span></span> <span data-ttu-id="c2424-131">這些2D 設計通常需要更多的人力，才能將其轉換成3D。</span><span class="sxs-lookup"><span data-stu-id="c2424-131">These 2D designs often require additional effort to convert them it into 3D.</span></span> <span data-ttu-id="c2424-132">這項從2D 到3D 的轉譯中遺失了一些想法。</span><span class="sxs-lookup"><span data-stu-id="c2424-132">Some ideas are lost in this translation from 2D to 3D.</span></span>

### <a name="complex-deployment-process"></a><span data-ttu-id="c2424-133">複雜的部署流程</span><span class="sxs-lookup"><span data-stu-id="c2424-133">Complex deployment process</span></span>

<span data-ttu-id="c2424-134">因為混合現實是我們的新畫布，所以它牽涉到許多設計反復專案和試用和錯誤的本質。</span><span class="sxs-lookup"><span data-stu-id="c2424-134">Since mixed reality is a new canvas for us, it involves a lot of design iteration and trial and error by its nature.</span></span> <span data-ttu-id="c2424-135">對於不熟悉 Unity 和 Visual Studio 這類工具的設計人員，在 HoloLens 中放在一起並不容易。</span><span class="sxs-lookup"><span data-stu-id="c2424-135">For designer who are not familiar with tools such as Unity and Visual Studio, it is not easy to put something together in HoloLens.</span></span> <span data-ttu-id="c2424-136">通常您必須完成下列程式，才能在裝置中查看 2D/3D 插圖。</span><span class="sxs-lookup"><span data-stu-id="c2424-136">Typically you have to go through the process below to see your 2D/3D artwork in the device.</span></span> <span data-ttu-id="c2424-137">這是設計人員快速地逐一查看想法和案例的一個大障礙。</span><span class="sxs-lookup"><span data-stu-id="c2424-137">This was a big barrier for designers iterating on ideas and scenarios quickly.</span></span>

<span data-ttu-id="c2424-138">![複雜的部署流程](images/holosketch-image-03-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="c2424-138">![Complex deployment process](images/holosketch-image-03-1000px.png)</span></span><br>
<span data-ttu-id="c2424-139">*部署程式*</span><span class="sxs-lookup"><span data-stu-id="c2424-139">*Deployment process*</span></span>

### <a name="simplified-process-with-holosketch"></a><span data-ttu-id="c2424-140">簡化的 HoloSketch 程式</span><span class="sxs-lookup"><span data-stu-id="c2424-140">Simplified process with HoloSketch</span></span>

<span data-ttu-id="c2424-141">有了 HoloSketch，我們想要簡化此程式，而不涉及開發工具和裝置入口網站配對。</span><span class="sxs-lookup"><span data-stu-id="c2424-141">With HoloSketch, we wanted to simplify this process without involving development tools and device portal pairing.</span></span> <span data-ttu-id="c2424-142">使用者可以使用 OneDrive，輕鬆地將 2D/3D 資產放入 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="c2424-142">Using OneDrive, users can easily put 2D/3D assets into HoloLens.</span></span>

<span data-ttu-id="c2424-143">![使用 HoloSketch](images/holosketch-image-04-1000px.png) 簡化的程式</span><span class="sxs-lookup"><span data-stu-id="c2424-143">![Simplified process with HoloSketch](images/holosketch-image-04-1000px.png)</span></span><br>
<span data-ttu-id="c2424-144">*簡化的 HoloSketch 程式*</span><span class="sxs-lookup"><span data-stu-id="c2424-144">*Simplified process with HoloSketch*</span></span>

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a><span data-ttu-id="c2424-145">鼓勵三維設計考慮與解決方案</span><span class="sxs-lookup"><span data-stu-id="c2424-145">Encouraging three-dimensional design thinking and solutions</span></span>

<span data-ttu-id="c2424-146">我們認為這項工具可以讓設計師有機會在真正的3d 空間中探索解決方案，而不會停滯在2D 中。</span><span class="sxs-lookup"><span data-stu-id="c2424-146">We thought this tool would give designers an opportunity to explore solutions in a truly three-dimensional space and not be stuck in 2D.</span></span> <span data-ttu-id="c2424-147">他們不需要考慮為其 UI 建立3D 背景，因為在 HoloLens 案例中，背景是真實世界。</span><span class="sxs-lookup"><span data-stu-id="c2424-147">They don’t have to think about creating a 3D background for their UI since the background is the real world in the case of HoloLens.</span></span> <span data-ttu-id="c2424-148">HoloSketch 開啟了一種方式，讓設計人員能夠輕鬆地探索 HoloLens 上的3D 設計。</span><span class="sxs-lookup"><span data-stu-id="c2424-148">HoloSketch opens up a way for designers to easily explore 3D design on HoloLens.</span></span>

## <a name="get-started"></a><span data-ttu-id="c2424-149">[開始]</span><span class="sxs-lookup"><span data-stu-id="c2424-149">Get Started</span></span>

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a><span data-ttu-id="c2424-150">如何將2D 影像（JPG/PNG）匯入 HoloSketch</span><span class="sxs-lookup"><span data-stu-id="c2424-150">How to import 2D images (JPG/PNG) into HoloSketch</span></span>

* <span data-ttu-id="c2424-151">將 JPG/PNG 影像上傳到您的 OneDrive 資料夾「Documents/HoloSketch」。</span><span class="sxs-lookup"><span data-stu-id="c2424-151">Upload JPG/PNG images to your OneDrive folder ‘Documents/HoloSketch’.</span></span>
* <span data-ttu-id="c2424-152">從 HoloSketch 的 [OneDrive] 功能表中，您可以選取映射並將其放在環境中。</span><span class="sxs-lookup"><span data-stu-id="c2424-152">From the OneDrive menu in HoloSketch, you will be able to select and place the image in the environment.</span></span>

<span data-ttu-id="c2424-153">![匯入2D 影像](images/import-2d-images-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c2424-153">![Importing 2D images](images/import-2d-images-1000px.jpg)</span></span><br>
<span data-ttu-id="c2424-154">*透過 OneDrive 匯入影像和3D 物件*</span><span class="sxs-lookup"><span data-stu-id="c2424-154">*Importing images and 3D objects through OneDrive*</span></span>

### <a name="how-to-import-3d-objects-into-holosketch"></a><span data-ttu-id="c2424-155">如何將3D 物件匯入至 HoloSketch</span><span class="sxs-lookup"><span data-stu-id="c2424-155">How to import 3D objects into HoloSketch</span></span>

<span data-ttu-id="c2424-156">在上傳至 OneDrive 資料夾之前，請先遵循下列步驟，將您的3D 物件封裝到 Unity 資產組合中。</span><span class="sxs-lookup"><span data-stu-id="c2424-156">Before uploading to your OneDrive folder, please follow the steps below to package your 3D objects into a Unity asset bundle.</span></span> <span data-ttu-id="c2424-157">使用此程式，您可以從3D 軟體（例如 Maya、電影院4D 和 Microsoft Paint 3D）匯入 FBX/OBJ 檔案。</span><span class="sxs-lookup"><span data-stu-id="c2424-157">Using this process you can import your FBX/OBJ files from 3D software such as Maya, Cinema 4D and Microsoft Paint 3D.</span></span>

>[!IMPORTANT]
><span data-ttu-id="c2424-158">目前，Unity 版本 5.4.5 f1 支援資產組合建立。</span><span class="sxs-lookup"><span data-stu-id="c2424-158">Currently, asset bundle creation is supported with Unity version 5.4.5f1.</span></span>

1. <span data-ttu-id="c2424-159">下載並開啟 Unity 專案[' AssetBunlder_Unity '](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity)。</span><span class="sxs-lookup"><span data-stu-id="c2424-159">Download and open the Unity project ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span></span> <span data-ttu-id="c2424-160">此 Unity 專案包含產生配套資產的腳本。</span><span class="sxs-lookup"><span data-stu-id="c2424-160">This Unity project includes the script for the bundle asset generation.</span></span>
2. <span data-ttu-id="c2424-161">建立新的 GameObject。</span><span class="sxs-lookup"><span data-stu-id="c2424-161">Create a new GameObject.</span></span>
3. <span data-ttu-id="c2424-162">根據內容來命名 GameObject。</span><span class="sxs-lookup"><span data-stu-id="c2424-162">Name the GameObject based on the contents.</span></span>
4. <span data-ttu-id="c2424-163">在 [偵測器] 面板中，按一下 [新增元件] 並新增 [方塊碰撞器]。</span><span class="sxs-lookup"><span data-stu-id="c2424-163">In the Inspector panel, click ‘Add Component’ and add ‘Box Collider’.</span></span> 

   ![在 [偵測器] 面板中，按一下 [新增元件] 並新增 [Box 碰撞器]](images/holosketch-10a-assetbundles-1000px.png)
   
   ![在 [偵測器] 面板中，按一下 [新增元件] 並新增 [Box 碰撞器] #2](images/holosketch-10b-assetbundles-1000px.png)

5. <span data-ttu-id="c2424-166">將 3D FBX 檔案拖曳至 [專案] 面板，以匯入該檔案。</span><span class="sxs-lookup"><span data-stu-id="c2424-166">Import the 3D FBX file by dragging it into the project panel.</span></span>
6. <span data-ttu-id="c2424-167">將物件拖曳至**新 GameObject**底下的 [階層] 面板。</span><span class="sxs-lookup"><span data-stu-id="c2424-167">Drag the object into the Hierarchy panel **under your new GameObject**.</span></span>

   ![將物件拖曳至新 GameObject 底下的 [階層] 面板](images/holosketch-12-assetbundles-1000px.png)

7. <span data-ttu-id="c2424-169">若不符合物件，請調整 [碰撞項] 維度。</span><span class="sxs-lookup"><span data-stu-id="c2424-169">Adjust the collider dimension if it does not match the object.</span></span> <span data-ttu-id="c2424-170">將物件旋轉成臉部**Z 軸**。</span><span class="sxs-lookup"><span data-stu-id="c2424-170">Rotate the object to face **Z-axis**.</span></span>

   ![如果不符合物件，請調整 [碰撞] 維度。](images/holosketch-13-assetbundles-1000px.png)

8. <span data-ttu-id="c2424-172">將物件從 [階層] 面板拖曳至 [專案] 面板，**使其 prefab**。</span><span class="sxs-lookup"><span data-stu-id="c2424-172">Drag the object from the Hierarchy panel to the Project panel to **make it prefab**.</span></span>
9. <span data-ttu-id="c2424-173">在 [偵測器] 面板的底部，按一下下拉式清單，建立並指派新的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="c2424-173">On the bottom of the inspector panel, click the dropdown, create and assign a new unique name.</span></span> <span data-ttu-id="c2424-174">下列範例顯示如何新增和指派 AssetBundle 名稱的 ' brownchair '。</span><span class="sxs-lookup"><span data-stu-id="c2424-174">Below example shows adding and assigning 'brownchair' for the AssetBundle Name.</span></span> 

   ![在 [檢查器] 面板的底部，按一下下拉式清單並指派新的唯一名稱。](images/holosketch-14-assetbundles-1000px.png)

10. <span data-ttu-id="c2424-176">準備模型物件的縮圖影像。</span><span class="sxs-lookup"><span data-stu-id="c2424-176">Prepare a thumbnail image for the model object.</span></span> 
   <span data-ttu-id="c2424-177">![將影像拖曳到 [專案] 面板中，並指派用於物件的名稱。](images/holosketch-15-assetbundles-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="c2424-177">![Drag an image into the project panel and assign the name used for the object.](images/holosketch-15-assetbundles-1000px.png)</span></span>

11. <span data-ttu-id="c2424-178">在 Unity 專案的 ' 資產 ' 資料夾底下，建立名為 ' Assetbundles ' 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="c2424-178">Create a folder named ‘Assetbundles’ under the Unity project’s ‘Asset’ folder.</span></span>

12. <span data-ttu-id="c2424-179">從 [資產] 功能表中，選取 [Build AssetBundles] 以產生檔案。</span><span class="sxs-lookup"><span data-stu-id="c2424-179">From the Assets menu, select ‘Build AssetBundles’ to generate file.</span></span> 
   <span data-ttu-id="c2424-180">![[資產] 功能表中，選取 [Build AssetBundles] 以產生檔案。](images/holosketch-15a-assetbundles.png)</span><span class="sxs-lookup"><span data-stu-id="c2424-180">![From the Assets menu, select ‘Build AssetBundles’ to generate file.](images/holosketch-15a-assetbundles.png)</span></span>


13. <span data-ttu-id="c2424-181">**將產生的檔案上傳至 OneDrive 上的/Files/Documents/HoloSketch 資料夾。**</span><span class="sxs-lookup"><span data-stu-id="c2424-181">**Upload the generated file to the /Files/Documents/HoloSketch folder on OneDrive.**</span></span> <span data-ttu-id="c2424-182">僅上傳 asset_unique_name 檔案。</span><span class="sxs-lookup"><span data-stu-id="c2424-182">Upload the asset_unique_name file only.</span></span> <span data-ttu-id="c2424-183">您不需要上傳資訊清單檔案或 AssetBundles 檔。</span><span class="sxs-lookup"><span data-stu-id="c2424-183">You don’t need to upload manifest files or AssetBundles file.</span></span> <br>
<span data-ttu-id="c2424-184">![將檔案新增至檔案/檔/HoloSketch/資料夾](images/holosketch-onedriveupload-1000px.png)
![您會在 HoloSketch 的 OneDrive 功能表中看到新增的3D 物件](images/holosketch-14-onedriveexample-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c2424-184">![Add files to Files/Documents/HoloSketch/ folder](images/holosketch-onedriveupload-1000px.png)
![You will see added 3D object in HoloSketch's OneDrive menu](images/holosketch-14-onedriveexample-1000px.jpg)</span></span>

## <a name="how-to-manipulate-the-objects"></a><span data-ttu-id="c2424-185">如何操作物件</span><span class="sxs-lookup"><span data-stu-id="c2424-185">How to manipulate the objects</span></span>

<span data-ttu-id="c2424-186">HoloSketch 支援在3D 軟體中廣泛使用的傳統介面。</span><span class="sxs-lookup"><span data-stu-id="c2424-186">HoloSketch supports the traditional interface that is widely used in 3D software.</span></span> <span data-ttu-id="c2424-187">您可以使用 [移動]、[旋轉]、使用筆勢和滑鼠來縮放物件。</span><span class="sxs-lookup"><span data-stu-id="c2424-187">You can use move, rotate, scale the objects with gestures and a mouse.</span></span> <span data-ttu-id="c2424-188">您可以使用語音或鍵盤，在不同的模式之間快速切換。</span><span class="sxs-lookup"><span data-stu-id="c2424-188">You can quickly switch between different modes with voice or keyboard.</span></span>

### <a name="object-manipulation-modes"></a><span data-ttu-id="c2424-189">物件操作模式</span><span class="sxs-lookup"><span data-stu-id="c2424-189">Object manipulation modes</span></span>

<span data-ttu-id="c2424-190">![如何操作物件](images/holosketch-image-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="c2424-190">![How to manipulate the objects](images/holosketch-image-06-1000px.png)</span></span><br>
<span data-ttu-id="c2424-191">*如何操作物件*</span><span class="sxs-lookup"><span data-stu-id="c2424-191">*How to manipulate the objects*</span></span>

### <a name="contextual-and-tool-belt-menus"></a><span data-ttu-id="c2424-192">內容相關和工具功能表</span><span class="sxs-lookup"><span data-stu-id="c2424-192">Contextual and Tool Belt menus</span></span>

<span data-ttu-id="c2424-193">**使用內容功能表**</span><span class="sxs-lookup"><span data-stu-id="c2424-193">**Using the Contextual Menu**</span></span>

<span data-ttu-id="c2424-194">按兩下以開啟內容功能表。</span><span class="sxs-lookup"><span data-stu-id="c2424-194">Double air tap to open the Contextual Menu.</span></span> 

<span data-ttu-id="c2424-195">功能表項目：</span><span class="sxs-lookup"><span data-stu-id="c2424-195">Menu items:</span></span>
* <span data-ttu-id="c2424-196">**版面配置介面：** 這是一個3D 方格系統，您可以在其中配置多個物件，並將它們當做一個群組來管理。</span><span class="sxs-lookup"><span data-stu-id="c2424-196">**Layout Surface:** This is a 3D grid system where you can layout multiple objects and manage them as a group.</span></span> <span data-ttu-id="c2424-197">在版面配置介面上按兩下以加入物件。</span><span class="sxs-lookup"><span data-stu-id="c2424-197">Double air-tap on the Layout Surface to add objects to it.</span></span>
* <span data-ttu-id="c2424-198">**基本：** 使用 cube、球體、圓柱和圓錐來進行 massing 研究。</span><span class="sxs-lookup"><span data-stu-id="c2424-198">**Primitives:** Use cubes, spheres, cylinders and cones for massing studies.</span></span>
* <span data-ttu-id="c2424-199">**OneDrive：** 開啟 [OneDrive] 功能表以匯入物件。</span><span class="sxs-lookup"><span data-stu-id="c2424-199">**OneDrive:** Open the OneDrive menu to import objects.</span></span>
* <span data-ttu-id="c2424-200">說明 **：** 顯示說明畫面。</span><span class="sxs-lookup"><span data-stu-id="c2424-200">**Help:** Displays help screen.</span></span>

<span data-ttu-id="c2424-201">![內容功能表](images/holosketch-image-07.png)</span><span class="sxs-lookup"><span data-stu-id="c2424-201">![Contextual menu](images/holosketch-image-07.png)</span></span><br>
<span data-ttu-id="c2424-202">*內容功能表*</span><span class="sxs-lookup"><span data-stu-id="c2424-202">*Contextual menu*</span></span>

<span data-ttu-id="c2424-203">**使用 [工具] 功能表**</span><span class="sxs-lookup"><span data-stu-id="c2424-203">**Using the Tool Belt Menu**</span></span>

<span data-ttu-id="c2424-204">[移動]、[旋轉]、[縮放]、[儲存] 和 [載入] 場景可從 [工具] 功能表取得。</span><span class="sxs-lookup"><span data-stu-id="c2424-204">Move, Rotate, Scale, Save, and Load Scene are available from the Tool Belt Menu.</span></span> 

## <a name="using-keyboard-gestures-and-voice-commands"></a><span data-ttu-id="c2424-205">使用鍵盤、手勢和語音命令</span><span class="sxs-lookup"><span data-stu-id="c2424-205">Using keyboard, gestures and voice commands</span></span>

<span data-ttu-id="c2424-206">![鍵盤、手勢和語音命令](images/holosketch-image-08-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="c2424-206">![Keyboard, Gestures and Voice Commands](images/holosketch-image-08-1000px.png)</span></span><br>
<span data-ttu-id="c2424-207">*鍵盤、手勢和語音命令*</span><span class="sxs-lookup"><span data-stu-id="c2424-207">*Keyboard, gestures, and voice commands*</span></span>

## <a name="download-the-app"></a><span data-ttu-id="c2424-208">下載應用程式</span><span class="sxs-lookup"><span data-stu-id="c2424-208">Download the app</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><span data-ttu-id="c2424-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">從 Microsoft Store 免費下載並安裝 HoloSketch 應用程式</a>
</span><span class="sxs-lookup"><span data-stu-id="c2424-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Download and install the HoloSketch app for free from the Microsoft Store</a>
</span></span></td>
</tr>
</table>

## <a name="known-issues"></a><span data-ttu-id="c2424-210">已知問題</span><span class="sxs-lookup"><span data-stu-id="c2424-210">Known issues</span></span>
* <span data-ttu-id="c2424-211">**Unity 版本 5.4.5 f1**支援目前的資產組合建立。</span><span class="sxs-lookup"><span data-stu-id="c2424-211">Currently asset bundle creation is supported with **Unity version 5.4.5f1.**</span></span>
* <span data-ttu-id="c2424-212">視 OneDrive 中的資料量而定，應用程式可能會顯示為已在載入 OneDrive 內容時停止</span><span class="sxs-lookup"><span data-stu-id="c2424-212">Depending on the amount of data in your OneDrive, the app might appear as if it has stopped while loading OneDrive contents</span></span>
* <span data-ttu-id="c2424-213">目前，儲存和載入功能只支援基本物件</span><span class="sxs-lookup"><span data-stu-id="c2424-213">Currently, Save and Load feature only supports primitive objects</span></span>
* <span data-ttu-id="c2424-214">已停用內容功能表上的文字、音效、影片和相片功能表</span><span class="sxs-lookup"><span data-stu-id="c2424-214">Text, Sound, Video and Photo menus are disabled on the contextual menu</span></span>
* <span data-ttu-id="c2424-215">[工具] 功能表上的 [播放] 按鈕會清除操作 gizmos</span><span class="sxs-lookup"><span data-stu-id="c2424-215">The Play button on the Tool Belt menu clears the manipulation gizmos</span></span>

## <a name="sharing-your-sketches"></a><span data-ttu-id="c2424-216">分享您的草圖</span><span class="sxs-lookup"><span data-stu-id="c2424-216">Sharing your sketches</span></span>

<span data-ttu-id="c2424-217">您可以使用 HoloLens 中的影片錄製功能，方法是說「嗨，Cortana，開始/停止錄製」。</span><span class="sxs-lookup"><span data-stu-id="c2424-217">You can use the video recording feature in HoloLens by saying 'Hey Cortana, Start/Stop recording'.</span></span> <span data-ttu-id="c2424-218">將音量向上/向下鍵合在一起，以拍照描繪。</span><span class="sxs-lookup"><span data-stu-id="c2424-218">Press the volume up/down key together to take a picture of your sketch.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="c2424-219">關於作者</span><span class="sxs-lookup"><span data-stu-id="c2424-219">About the authors</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="c2424-220"><b>盾 Yoon 公園</b></span><span class="sxs-lookup"><span data-stu-id="c2424-220"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="c2424-221">UX 設計工具 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="c2424-221">UX Designer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="c2424-222"><b>派翠克 Sebring</b></span><span class="sxs-lookup"><span data-stu-id="c2424-222"><b>Patrick Sebring</b></span></span><br><span data-ttu-id="c2424-223">開發人員 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="c2424-223">Developer @Microsoft</span></span></td>
</tr>
</table> 
