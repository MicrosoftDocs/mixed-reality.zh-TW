---
title: MR 空間 230-空間對應
description: 遵循此程式碼逐步解說如何使用 Unity、 Visual Studio 和 HoloLens，若要了解空間對應概念的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、 mixedrealitytoolkit、 mixedrealitytoolkit unity、 academy、 教學課程中，空間的對應、 介面重構，網格
ms.openlocfilehash: ed58676a0fda660cc6b4c197239aeb53166baa4d
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993564"
---
>[!NOTE]
><span data-ttu-id="ab675-104">混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。</span><span class="sxs-lookup"><span data-stu-id="ab675-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="ab675-105">因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。</span><span class="sxs-lookup"><span data-stu-id="ab675-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="ab675-106">這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="ab675-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="ab675-107">它們會繼續運作，支援的裝置上維護。</span><span class="sxs-lookup"><span data-stu-id="ab675-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="ab675-108">會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="ab675-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="ab675-109">當他們回傳時，本聲明將會更新這些教學課程的連結。</span><span class="sxs-lookup"><span data-stu-id="ab675-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-230-spatial-mapping"></a><span data-ttu-id="ab675-110">MR 空間 230:空間對應</span><span class="sxs-lookup"><span data-stu-id="ab675-110">MR Spatial 230: Spatial mapping</span></span>

<span data-ttu-id="ab675-111">[空間對應](spatial-mapping.md)實際及虛擬世界結合所教授的環境相關全像投影。</span><span class="sxs-lookup"><span data-stu-id="ab675-111">[Spatial mapping](spatial-mapping.md) combines the real world and virtual world together by teaching holograms about the environment.</span></span> <span data-ttu-id="ab675-112">MR 空間 230 (專案 Planetarium) 中我們將了解如何：</span><span class="sxs-lookup"><span data-stu-id="ab675-112">In MR Spatial 230 (Project Planetarium) we'll learn how to:</span></span>

* <span data-ttu-id="ab675-113">掃描您的開發電腦以 HoloLens 的環境和傳輸資料。</span><span class="sxs-lookup"><span data-stu-id="ab675-113">Scan the environment and transfer data from the HoloLens to your development machine.</span></span>
* <span data-ttu-id="ab675-114">探索著色器，並了解如何使用它們以視覺化方式呈現您的空間。</span><span class="sxs-lookup"><span data-stu-id="ab675-114">Explore shaders and learn how to use them for visualizing your space.</span></span>
* <span data-ttu-id="ab675-115">細分成使用網格處理簡單的平面空間網狀結構。</span><span class="sxs-lookup"><span data-stu-id="ab675-115">Break down the room mesh into simple planes using mesh processing.</span></span>
* <span data-ttu-id="ab675-116">除了在中學到的放置技術移[MR 基本概念 101](holograms-101.md)，並提供意見反應全像可以放置在環境中。</span><span class="sxs-lookup"><span data-stu-id="ab675-116">Go beyond the placement techniques we learned in [MR Basics 101](holograms-101.md), and provide feedback about where a hologram can be placed in the environment.</span></span>
* <span data-ttu-id="ab675-117">瀏覽的阻擋物的影響，因此在真實世界物件後面您全像圖時，您仍然可以看到它與超人 ！</span><span class="sxs-lookup"><span data-stu-id="ab675-117">Explore occlusion effects, so when your hologram is behind a real-world object, you can still see it with x-ray vision!</span></span>

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a><span data-ttu-id="ab675-118">裝置支援</span><span class="sxs-lookup"><span data-stu-id="ab675-118">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="ab675-119">課程</span><span class="sxs-lookup"><span data-stu-id="ab675-119">Course</span></span></th><th style="width:150px"> <span data-ttu-id="ab675-120"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ab675-120"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ab675-121"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="ab675-121"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="ab675-122">MR 空間 230:空間對應</span><span class="sxs-lookup"><span data-stu-id="ab675-122">MR Spatial 230: Spatial mapping</span></span></td><td style="text-align: center;"> <span data-ttu-id="ab675-123">✔️</span><span class="sxs-lookup"><span data-stu-id="ab675-123">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="ab675-124">開始之前</span><span class="sxs-lookup"><span data-stu-id="ab675-124">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="ab675-125">先決條件</span><span class="sxs-lookup"><span data-stu-id="ab675-125">Prerequisites</span></span>

* <span data-ttu-id="ab675-126">Windows 10 電腦的正確設定[安裝工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="ab675-126">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="ab675-127">基本C#程式設計的能力。</span><span class="sxs-lookup"><span data-stu-id="ab675-127">Some basic C# programming ability.</span></span>
* <span data-ttu-id="ab675-128">您應已完成[MR 基本概念 101](holograms-101.md)。</span><span class="sxs-lookup"><span data-stu-id="ab675-128">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="ab675-129">HoloLens 裝置[開發設定的](using-visual-studio.md#enabling-developer-mode)。</span><span class="sxs-lookup"><span data-stu-id="ab675-129">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="ab675-130">專案檔</span><span class="sxs-lookup"><span data-stu-id="ab675-130">Project files</span></span>

* <span data-ttu-id="ab675-131">下載[檔案](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip)專案所需。</span><span class="sxs-lookup"><span data-stu-id="ab675-131">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) required by the project.</span></span><span data-ttu-id="ab675-132"> 需要 Unity 2017.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="ab675-132"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="ab675-133">如果您仍然需要 Unity 5.6 的支援，請使用[本版](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip)。</span><span class="sxs-lookup"><span data-stu-id="ab675-133">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).</span></span>
  * <span data-ttu-id="ab675-134">如果您仍然需要 Unity 5.5 的支援，請使用[本版](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip)。</span><span class="sxs-lookup"><span data-stu-id="ab675-134">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).</span></span>
  * <span data-ttu-id="ab675-135">如果您仍然需要 Unity 5.4 的支援，請使用[本版](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip)。</span><span class="sxs-lookup"><span data-stu-id="ab675-135">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).</span></span>
* <span data-ttu-id="ab675-136">取消封存您的桌面或其他您輕鬆地連線到位置的檔案。</span><span class="sxs-lookup"><span data-stu-id="ab675-136">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="ab675-137">如果您想要查看原始程式碼，在下載之前，它有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping)。</span><span class="sxs-lookup"><span data-stu-id="ab675-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).</span></span>

### <a name="notes"></a><span data-ttu-id="ab675-138">附註</span><span class="sxs-lookup"><span data-stu-id="ab675-138">Notes</span></span>

* <span data-ttu-id="ab675-139">在 Visual Studio 需要停用中的 [啟用 Just My Code] (*未核取*) 下工具 > 選項 > 若要在程式碼中設定中斷點的偵錯。</span><span class="sxs-lookup"><span data-stu-id="ab675-139">"Enable Just My Code" in Visual Studio needs to be disabled (*unchecked*) under Tools > Options > Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="ab675-140">Unity 安裝</span><span class="sxs-lookup"><span data-stu-id="ab675-140">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* <span data-ttu-id="ab675-141">開始**Unity**。</span><span class="sxs-lookup"><span data-stu-id="ab675-141">Start **Unity**.</span></span>
* <span data-ttu-id="ab675-142">選取 **新增**建立新的專案。</span><span class="sxs-lookup"><span data-stu-id="ab675-142">Select **New** to create a new project.</span></span>
* <span data-ttu-id="ab675-143">將專案命名為**Planetarium**。</span><span class="sxs-lookup"><span data-stu-id="ab675-143">Name the project **Planetarium**.</span></span>
* <span data-ttu-id="ab675-144">確認**3D**選取設定。</span><span class="sxs-lookup"><span data-stu-id="ab675-144">Verify that the **3D** setting is selected.</span></span>
* <span data-ttu-id="ab675-145">按一下 **建立專案**。</span><span class="sxs-lookup"><span data-stu-id="ab675-145">Click **Create Project**.</span></span>
* <span data-ttu-id="ab675-146">一旦 Unity 啟動時，請移至**編輯 > 專案設定 > Player**。</span><span class="sxs-lookup"><span data-stu-id="ab675-146">Once Unity launches, go to **Edit > Project Settings > Player**.</span></span>
* <span data-ttu-id="ab675-147">在 [ **Inspector** ] 面板中，尋找並選取綠色**Windows Store**圖示。</span><span class="sxs-lookup"><span data-stu-id="ab675-147">In the **Inspector** panel, find and select the green **Windows Store** icon.</span></span>
* <span data-ttu-id="ab675-148">依序展開**其他設定**。</span><span class="sxs-lookup"><span data-stu-id="ab675-148">Expand **Other Settings**.</span></span>
* <span data-ttu-id="ab675-149">在 **轉譯**區段中，按一下**受支援的虛擬實境**選項。</span><span class="sxs-lookup"><span data-stu-id="ab675-149">In the **Rendering** section, check the **Virtual Reality Supported** option.</span></span>
* <span data-ttu-id="ab675-150">確認**Windows 全像攝影版**清單中會出現**虛擬實境 Sdk**。</span><span class="sxs-lookup"><span data-stu-id="ab675-150">Verify that **Windows Holographic** appears in the list of **Virtual Reality SDKs**.</span></span> <span data-ttu-id="ab675-151">如果沒有，請選取 **+** 按鈕在清單底部，然後選擇**Windows 全像攝影版**。</span><span class="sxs-lookup"><span data-stu-id="ab675-151">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>
* <span data-ttu-id="ab675-152">依序展開**發佈設定**。</span><span class="sxs-lookup"><span data-stu-id="ab675-152">Expand **Publishing Settings**.</span></span>
* <span data-ttu-id="ab675-153">在 **功能**區段中，請檢查下列設定：</span><span class="sxs-lookup"><span data-stu-id="ab675-153">In the **Capabilities** section, check the following settings:</span></span>
    * <span data-ttu-id="ab675-154">InternetClientServer</span><span class="sxs-lookup"><span data-stu-id="ab675-154">InternetClientServer</span></span>
    * <span data-ttu-id="ab675-155">PrivateNetworkClientServer</span><span class="sxs-lookup"><span data-stu-id="ab675-155">PrivateNetworkClientServer</span></span>
    * <span data-ttu-id="ab675-156">麥克風</span><span class="sxs-lookup"><span data-stu-id="ab675-156">Microphone</span></span>
    * <span data-ttu-id="ab675-157">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="ab675-157">SpatialPerception</span></span>
* <span data-ttu-id="ab675-158">移至**編輯 > 專案設定 > 品質**</span><span class="sxs-lookup"><span data-stu-id="ab675-158">Go to **Edit > Project Settings > Quality**</span></span>
* <span data-ttu-id="ab675-159">在 [ **Inspector** ] 面板中，在 Windows 市集圖示，選取黑色的向下箭頭，在 'Default' 資料列，並將變更預設設定，以**非常低**。</span><span class="sxs-lookup"><span data-stu-id="ab675-159">In the **Inspector** panel, under the Windows Store icon, select the black drop-down arrow under the 'Default' row and change the default setting to **Very Low**.</span></span>
* <span data-ttu-id="ab675-160">移至**資產 > 匯入封裝 > 自訂套件**。</span><span class="sxs-lookup"><span data-stu-id="ab675-160">Go to **Assets > Import Package > Custom Package**.</span></span>
* <span data-ttu-id="ab675-161">瀏覽至 **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting**資料夾。</span><span class="sxs-lookup"><span data-stu-id="ab675-161">Navigate to the **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** folder.</span></span>
* <span data-ttu-id="ab675-162">按一下  **Planetarium.unitypackage**。</span><span class="sxs-lookup"><span data-stu-id="ab675-162">Click on **Planetarium.unitypackage**.</span></span>
* <span data-ttu-id="ab675-163">按一下 [開啟] 。</span><span class="sxs-lookup"><span data-stu-id="ab675-163">Click **Open**.</span></span>
* <span data-ttu-id="ab675-164">**匯入 Unity 封裝**應該會出現視窗，按一下**匯入** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ab675-164">An **Import Unity Package** window should appear, click on the **Import** button.</span></span>
* <span data-ttu-id="ab675-165">等待匯入的所有資產，我們將完成此專案需要 Unity。</span><span class="sxs-lookup"><span data-stu-id="ab675-165">Wait for Unity to import all of the assets that we will need to complete this project.</span></span>
* <span data-ttu-id="ab675-166">在 [**階層**] 面板中，刪除**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="ab675-166">In the **Hierarchy** panel, delete the **Main Camera**.</span></span>
* <span data-ttu-id="ab675-167">在 [**專案**] 面板中， **HoloToolkit-SpatialMapping-230\Utilities\Prefabs**資料夾中，尋找**Main Camera**物件。</span><span class="sxs-lookup"><span data-stu-id="ab675-167">In the **Project** panel, **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** folder, find the **Main Camera** object.</span></span>
* <span data-ttu-id="ab675-168">將拖放**Main Camera**至 prefab**階層**面板。</span><span class="sxs-lookup"><span data-stu-id="ab675-168">Drag and drop the **Main Camera** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="ab675-169">在 [**階層**] 面板中，刪除**定向光線**物件。</span><span class="sxs-lookup"><span data-stu-id="ab675-169">In the **Hierarchy** panel, delete the **Directional Light** object.</span></span>
* <span data-ttu-id="ab675-170">在 [**專案**] 面板中，**全像投影**資料夾中，找出**游標**物件。</span><span class="sxs-lookup"><span data-stu-id="ab675-170">In the **Project** panel, **Holograms** folder, locate the **Cursor** object.</span></span>
* <span data-ttu-id="ab675-171">拖放**游標**至 prefab**階層**。</span><span class="sxs-lookup"><span data-stu-id="ab675-171">Drag & drop the **Cursor** prefab into the **Hierarchy**.</span></span>
* <span data-ttu-id="ab675-172">在 **階層**面板中，選取**游標**物件。</span><span class="sxs-lookup"><span data-stu-id="ab675-172">In the **Hierarchy** panel, select the **Cursor** object.</span></span>
* <span data-ttu-id="ab675-173">在 [ **Inspector** ] 面板中，按一下**層**下拉式清單，然後選取**編輯圖層...**.</span><span class="sxs-lookup"><span data-stu-id="ab675-173">In the **Inspector** panel, click the **Layer** drop-down and select **Edit Layers...**.</span></span>
* <span data-ttu-id="ab675-174">名稱**使用者層級 31**做為 「**SpatialMapping**"。</span><span class="sxs-lookup"><span data-stu-id="ab675-174">Name **User Layer 31** as "**SpatialMapping**".</span></span>
* <span data-ttu-id="ab675-175">儲存新的場景：**檔案 > 儲存場景為...**</span><span class="sxs-lookup"><span data-stu-id="ab675-175">Save the new scene: **File > Save Scene As...**</span></span>
* <span data-ttu-id="ab675-176">按一下 **新的資料夾**並將資料夾命名**場景**。</span><span class="sxs-lookup"><span data-stu-id="ab675-176">Click **New Folder** and name the folder **Scenes**.</span></span>
* <span data-ttu-id="ab675-177">將檔案命名為"**Planetarium**"並將它儲存在**場景**資料夾。</span><span class="sxs-lookup"><span data-stu-id="ab675-177">Name the file "**Planetarium**" and save it in the **Scenes** folder.</span></span>

## <a name="chapter-1---scanning"></a><span data-ttu-id="ab675-178">第 1 章-掃描</span><span class="sxs-lookup"><span data-stu-id="ab675-178">Chapter 1 - Scanning</span></span>

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

<span data-ttu-id="ab675-179">**目標**</span><span class="sxs-lookup"><span data-stu-id="ab675-179">**Objectives**</span></span>
* <span data-ttu-id="ab675-180">深入了解 SurfaceObserver 和其設定影響如何體驗和效能。</span><span class="sxs-lookup"><span data-stu-id="ab675-180">Learn about the SurfaceObserver and how its settings impact experience and performance.</span></span>
* <span data-ttu-id="ab675-181">建立聊天室掃描以收集您的聊天室的網格的體驗。</span><span class="sxs-lookup"><span data-stu-id="ab675-181">Create a room scanning experience to collect the meshes of your room.</span></span>

<span data-ttu-id="ab675-182">**指示**</span><span class="sxs-lookup"><span data-stu-id="ab675-182">**Instructions**</span></span>
* <span data-ttu-id="ab675-183">在 **專案**面板**HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs**資料夾中，尋找**SpatialMapping** prefab。</span><span class="sxs-lookup"><span data-stu-id="ab675-183">In the **Project** panel **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** folder, find the **SpatialMapping** prefab.</span></span>
* <span data-ttu-id="ab675-184">拖放**SpatialMapping**至 prefab**階層**面板。</span><span class="sxs-lookup"><span data-stu-id="ab675-184">Drag & drop the **SpatialMapping** prefab into the **Hierarchy** panel.</span></span>

<span data-ttu-id="ab675-185">**建置和部署 （第 1 部分）**</span><span class="sxs-lookup"><span data-stu-id="ab675-185">**Build and Deploy (part 1)**</span></span>
* <span data-ttu-id="ab675-186">在 Unity 中，選取**檔案 > 組建設定**。</span><span class="sxs-lookup"><span data-stu-id="ab675-186">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="ab675-187">按一下 **加入開啟的場景**若要加入**Planetarium**場景方向，以建置。</span><span class="sxs-lookup"><span data-stu-id="ab675-187">Click **Add Open Scenes** to add the **Planetarium** scene to the build.</span></span>
* <span data-ttu-id="ab675-188">選取 **通用 Windows 平台**中**平台**清單，然後按一下**切換平台**。</span><span class="sxs-lookup"><span data-stu-id="ab675-188">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="ab675-189">設定**SDK**要**通用 10**並**UWP 建置型別**來**D3D**。</span><span class="sxs-lookup"><span data-stu-id="ab675-189">Set **SDK** to **Universal 10** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="ab675-190">請檢查**UnityC#專案**。</span><span class="sxs-lookup"><span data-stu-id="ab675-190">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="ab675-191">按一下 [建置] 。</span><span class="sxs-lookup"><span data-stu-id="ab675-191">Click **Build**.</span></span>
* <span data-ttu-id="ab675-192">建立**新的資料夾**名為 「 應用程式 」。</span><span class="sxs-lookup"><span data-stu-id="ab675-192">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="ab675-193">只要按一下**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="ab675-193">Single click the **App** folder.</span></span>
* <span data-ttu-id="ab675-194">按下**選取資料夾** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ab675-194">Press the **Select Folder** button.</span></span>
* <span data-ttu-id="ab675-195">當完成 Unity 建置時，會出現檔案總管 視窗。</span><span class="sxs-lookup"><span data-stu-id="ab675-195">When Unity is done building, a File Explorer window will appear.</span></span>
* <span data-ttu-id="ab675-196">按兩下**應用程式**資料夾將它開啟。</span><span class="sxs-lookup"><span data-stu-id="ab675-196">Double-click on the **App** folder to open it.</span></span>
* <span data-ttu-id="ab675-197">按兩下**Planetarium.sln**載入 Visual Studio 中的專案。</span><span class="sxs-lookup"><span data-stu-id="ab675-197">Double-click on **Planetarium.sln** to load the project in Visual Studio.</span></span>
* <span data-ttu-id="ab675-198">在 Visual Studio 中，請變更設定以使用頂端的工具列**發行**。</span><span class="sxs-lookup"><span data-stu-id="ab675-198">In Visual Studio, use the top toolbar to change the Configuration to **Release**.</span></span>
* <span data-ttu-id="ab675-199">變更平台**x86**。</span><span class="sxs-lookup"><span data-stu-id="ab675-199">Change the Platform to **x86**.</span></span>
* <span data-ttu-id="ab675-200">按一下右邊的 本機電腦上，' 的下拉式箭號，然後選取**遠端機器**。</span><span class="sxs-lookup"><span data-stu-id="ab675-200">Click on the drop-down arrow to the right of 'Local Machine', and select **Remote Machine**.</span></span>
* <span data-ttu-id="ab675-201">請輸入[裝置的 IP 位址](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) 欄位中的位址和驗證模式變更為**通用 （未加密的通訊協定）**。</span><span class="sxs-lookup"><span data-stu-id="ab675-201">Enter [your device's IP address](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) in the Address field and change Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span>
* <span data-ttu-id="ab675-202">按一下 **偵錯-> 啟動但不偵錯**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="ab675-202">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="ab675-203">監看式**輸出**面板在 Visual Studio 中建置和部署狀態。</span><span class="sxs-lookup"><span data-stu-id="ab675-203">Watch the **Output** panel in Visual Studio for build and deploy status.</span></span>
* <span data-ttu-id="ab675-204">一旦您的應用程式已部署，逐步房間周圍。</span><span class="sxs-lookup"><span data-stu-id="ab675-204">Once your app has deployed, walk around the room.</span></span> <span data-ttu-id="ab675-205">您會看到黑白的線框網格所涵蓋的周圍介面。</span><span class="sxs-lookup"><span data-stu-id="ab675-205">You will see the surrounding surfaces covered by black and white wireframe meshes.</span></span>
* <span data-ttu-id="ab675-206">掃描您恍神。</span><span class="sxs-lookup"><span data-stu-id="ab675-206">Scan your surroundings.</span></span> <span data-ttu-id="ab675-207">請務必查看牆壁、 上限和樓層。</span><span class="sxs-lookup"><span data-stu-id="ab675-207">Be sure to look at walls, ceilings, and floors.</span></span>

<span data-ttu-id="ab675-208">**建置和部署 （第 2 部分）**</span><span class="sxs-lookup"><span data-stu-id="ab675-208">**Build and Deploy (part 2)**</span></span>

<span data-ttu-id="ab675-209">現在讓我們來探索如何設定對應的空間可能會影響效能。</span><span class="sxs-lookup"><span data-stu-id="ab675-209">Now let's explore how Spatial Mapping can affect performance.</span></span>
* <span data-ttu-id="ab675-210">在 Unity 中，選取**視窗中 > Profiler**。</span><span class="sxs-lookup"><span data-stu-id="ab675-210">In Unity, select **Window > Profiler**.</span></span>
* <span data-ttu-id="ab675-211">按一下 **新增 Profiler > GPU**。</span><span class="sxs-lookup"><span data-stu-id="ab675-211">Click **Add Profiler > GPU**.</span></span>
* <span data-ttu-id="ab675-212">按一下 **作用中的 Profiler > <Enter IP>** 。</span><span class="sxs-lookup"><span data-stu-id="ab675-212">Click **Active Profiler > <Enter IP>**.</span></span>
* <span data-ttu-id="ab675-213">請輸入**IP 位址**的您 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="ab675-213">Enter the **IP address** of your HoloLens.</span></span>
* <span data-ttu-id="ab675-214">按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="ab675-214">Click **Connect**.</span></span>
* <span data-ttu-id="ab675-215">觀察 GPU 來轉譯畫面格所花費的毫秒的數。</span><span class="sxs-lookup"><span data-stu-id="ab675-215">Observe the number of milliseconds it takes for the GPU to render a frame.</span></span>
* <span data-ttu-id="ab675-216">停止從裝置上執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="ab675-216">Stop the application from running on the device.</span></span>
* <span data-ttu-id="ab675-217">返回 Visual Studio，然後開啟**SpatialMappingObserver.cs**。</span><span class="sxs-lookup"><span data-stu-id="ab675-217">Return to Visual Studio and open **SpatialMappingObserver.cs**.</span></span> <span data-ttu-id="ab675-218">您會發現它 HoloToolkit\SpatialMapping 專案資料夾中的組件 CSharp (通用 Windows)。</span><span class="sxs-lookup"><span data-stu-id="ab675-218">You will find it in the HoloToolkit\SpatialMapping folder of the Assembly-CSharp (Universal Windows) project.</span></span>
* <span data-ttu-id="ab675-219">尋找**Awake()** 函式，並新增下列程式碼行：**TrianglesPerCubicMeter = 1200;**</span><span class="sxs-lookup"><span data-stu-id="ab675-219">Find the **Awake()** function, and add the following line of code: **TrianglesPerCubicMeter = 1200;**</span></span>
* <span data-ttu-id="ab675-220">重新部署專案，以您的裝置，然後**重新連線的程式碼剖析工具**。</span><span class="sxs-lookup"><span data-stu-id="ab675-220">Re-deploy the project to your device, and then **reconnect the profiler**.</span></span> <span data-ttu-id="ab675-221">觀察到的變更要呈現的畫面格的毫秒數。</span><span class="sxs-lookup"><span data-stu-id="ab675-221">Observe the change in the number of milliseconds to render a frame.</span></span>
* <span data-ttu-id="ab675-222">停止從裝置上執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="ab675-222">Stop the application from running on the device.</span></span>

<span data-ttu-id="ab675-223">**儲存並在 Unity 中載入**</span><span class="sxs-lookup"><span data-stu-id="ab675-223">**Save and load in Unity**</span></span>

<span data-ttu-id="ab675-224">最後，讓我們儲存我們的房間網狀結構，並將其載入至 Unity。</span><span class="sxs-lookup"><span data-stu-id="ab675-224">Finally, let's save our room mesh and load it into Unity.</span></span>
* <span data-ttu-id="ab675-225">返回 Visual Studio，並移除**TrianglesPerCubicMeter**您在中新增的一行**Awake()** 函式在上一節。</span><span class="sxs-lookup"><span data-stu-id="ab675-225">Return to Visual Studio and remove the **TrianglesPerCubicMeter** line that you added in the **Awake()** function during the previous section.</span></span>
* <span data-ttu-id="ab675-226">專案重新部署至您的裝置。</span><span class="sxs-lookup"><span data-stu-id="ab675-226">Redeploy the project to your device.</span></span> <span data-ttu-id="ab675-227">我們現在應該執行含**500**三角形每三次方的計量。</span><span class="sxs-lookup"><span data-stu-id="ab675-227">We should now be running with **500** triangles per cubic meter.</span></span>
* <span data-ttu-id="ab675-228">開啟瀏覽器並瀏覽至您 HoloLens IPAddress 報名參加**Windows Device Portal**。</span><span class="sxs-lookup"><span data-stu-id="ab675-228">Open a browser and enter in your HoloLens IPAddress to navigate to the **Windows Device Portal**.</span></span>
* <span data-ttu-id="ab675-229">選取  **3D 檢視**左方面板中的選項。</span><span class="sxs-lookup"><span data-stu-id="ab675-229">Select the **3D View** option in the left panel.</span></span>
* <span data-ttu-id="ab675-230">底下**介面重構**選取**更新** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ab675-230">Under **Surface reconstruction** select the **Update** button.</span></span>
* <span data-ttu-id="ab675-231">觀看您已掃描您 HoloLens 的區域會出現在顯示視窗。</span><span class="sxs-lookup"><span data-stu-id="ab675-231">Watch as the areas that you have scanned on your HoloLens appear in the display window.</span></span>
* <span data-ttu-id="ab675-232">若要儲存您的房間掃描，請按**儲存** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ab675-232">To save your room scan, press the **Save** button.</span></span>
* <span data-ttu-id="ab675-233">開啟您**下載**資料夾，找出儲存的空間模型**SRMesh.obj**。</span><span class="sxs-lookup"><span data-stu-id="ab675-233">Open your **Downloads** folder to find the saved room model **SRMesh.obj**.</span></span>
* <span data-ttu-id="ab675-234">複製**SRMesh.obj**要**資產**Unity 專案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="ab675-234">Copy **SRMesh.obj** to the **Assets** folder of your Unity project.</span></span>
* <span data-ttu-id="ab675-235">在 Unity 中，選取**SpatialMapping**物件中**階層**面板。</span><span class="sxs-lookup"><span data-stu-id="ab675-235">In Unity, select the **SpatialMapping** object in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="ab675-236">找出**物件介面觀察者 （指令碼）** 元件。</span><span class="sxs-lookup"><span data-stu-id="ab675-236">Locate the **Object Surface Observer (Script)** component.</span></span>
* <span data-ttu-id="ab675-237">按一下右側的圓形**聊天室模型**屬性。</span><span class="sxs-lookup"><span data-stu-id="ab675-237">Click the circle to the right of the **Room Model** property.</span></span>
* <span data-ttu-id="ab675-238">尋找並選取**SRMesh**物件，並接著關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="ab675-238">Find and select the **SRMesh** object and then close the window.</span></span>
* <span data-ttu-id="ab675-239">確認**聊天室模型**中的屬性**Inspector**面板現在已設定為**SRMesh**。</span><span class="sxs-lookup"><span data-stu-id="ab675-239">Verify that the **Room Model** property in the **Inspector** panel is now set to **SRMesh**.</span></span>
* <span data-ttu-id="ab675-240">按下**播放**輸入 Unity 的 [預覽] 模式的按鈕。</span><span class="sxs-lookup"><span data-stu-id="ab675-240">Press the **Play** button to enter Unity's preview mode.</span></span>
* <span data-ttu-id="ab675-241">SpatialMapping 元件將從儲存的空間模型載入網格，讓您可以在 Unity 中使用它們。</span><span class="sxs-lookup"><span data-stu-id="ab675-241">The SpatialMapping component will load the meshes from the saved room model so you can use them in Unity.</span></span>
* <span data-ttu-id="ab675-242">若要切換**場景**檢視來查看所有聊天室模型顯示框線著色器。</span><span class="sxs-lookup"><span data-stu-id="ab675-242">Switch to **Scene** view to see all of your room model displayed with the wireframe shader.</span></span>
* <span data-ttu-id="ab675-243">按下**播放** 按鈕以結束 預覽 模式。</span><span class="sxs-lookup"><span data-stu-id="ab675-243">Press the **Play** button again to exit preview mode.</span></span>

<span data-ttu-id="ab675-244">**注意：** 您在 Unity 中，輸入 [預覽] 模式下一次它預設會載入已儲存的房間網狀結構的。</span><span class="sxs-lookup"><span data-stu-id="ab675-244">**NOTE:** The next time that you enter preview mode in Unity, it will load the saved room mesh by default.</span></span>

## <a name="chapter-2---visualization"></a><span data-ttu-id="ab675-245">第 2 章-視覺效果</span><span class="sxs-lookup"><span data-stu-id="ab675-245">Chapter 2 - Visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

<span data-ttu-id="ab675-246">**目標**</span><span class="sxs-lookup"><span data-stu-id="ab675-246">**Objectives**</span></span>
* <span data-ttu-id="ab675-247">了解著色器的基本概念。</span><span class="sxs-lookup"><span data-stu-id="ab675-247">Learn the basics of shaders.</span></span>
* <span data-ttu-id="ab675-248">以視覺化方式檢視您恍神。</span><span class="sxs-lookup"><span data-stu-id="ab675-248">Visualize your surroundings.</span></span>

<span data-ttu-id="ab675-249">**指示**</span><span class="sxs-lookup"><span data-stu-id="ab675-249">**Instructions**</span></span>
* <span data-ttu-id="ab675-250">在 Unity**階層**面板中，選取**SpatialMapping**物件。</span><span class="sxs-lookup"><span data-stu-id="ab675-250">In Unity's **Hierarchy** panel, select the **SpatialMapping** object.</span></span>
* <span data-ttu-id="ab675-251">在 [ **Inspector** ] 面板中，尋找**空間對應 Manager （指令碼）** 元件。</span><span class="sxs-lookup"><span data-stu-id="ab675-251">In the **Inspector** panel, find the **Spatial Mapping Manager (Script)** component.</span></span>
* <span data-ttu-id="ab675-252">按一下右側的圓形**表面材質**屬性。</span><span class="sxs-lookup"><span data-stu-id="ab675-252">Click the circle to the right of the **Surface Material** property.</span></span>
* <span data-ttu-id="ab675-253">尋找並選取**BlueLinesOnWalls** material 和關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="ab675-253">Find and select the **BlueLinesOnWalls** material and close the window.</span></span>
* <span data-ttu-id="ab675-254">在 **專案**面板**著色器**資料夾中，按兩下**BlueLinesOnWalls**以開啟 Visual Studio 中的 著色器。</span><span class="sxs-lookup"><span data-stu-id="ab675-254">In the **Project** panel **Shaders** folder, double-click on **BlueLinesOnWalls** to open the shader in Visual Studio.</span></span>
* <span data-ttu-id="ab675-255">這是簡單的像素 （頂點來分割） 著色器，將完成下列工作：</span><span class="sxs-lookup"><span data-stu-id="ab675-255">This is a simple pixel (vertex to fragment) shader, which accomplishes the following tasks:</span></span>
    1. <span data-ttu-id="ab675-256">將頂點位置轉換為全局空間中。</span><span class="sxs-lookup"><span data-stu-id="ab675-256">Converts a vertex's location to world space.</span></span>
    2. <span data-ttu-id="ab675-257">檢查 頂點的標準來判斷是否垂直的像素。</span><span class="sxs-lookup"><span data-stu-id="ab675-257">Checks the vertex's normal to determine if a pixel is vertical.</span></span>
    3. <span data-ttu-id="ab675-258">設定轉譯的像素的色彩。</span><span class="sxs-lookup"><span data-stu-id="ab675-258">Sets the color of the pixel for rendering.</span></span>

<span data-ttu-id="ab675-259">**建置和部署**</span><span class="sxs-lookup"><span data-stu-id="ab675-259">**Build and Deploy**</span></span>
* <span data-ttu-id="ab675-260">傳回至 Unity 並按下**播放**進入預覽模式。</span><span class="sxs-lookup"><span data-stu-id="ab675-260">Return to Unity and press **Play** to enter preview mode.</span></span>
* <span data-ttu-id="ab675-261">藍線將會呈現所有垂直的表面的房間網狀結構 （這會自動載入已儲存掃描資料）。</span><span class="sxs-lookup"><span data-stu-id="ab675-261">Blue lines will be rendered on all vertical surfaces of the room mesh (which automatically loaded from our saved scanning data).</span></span>
* <span data-ttu-id="ab675-262">若要切換**場景**調整檢視的空間，並查看整個房間網狀結構 Unity 中顯示的方式 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ab675-262">Switch to the **Scene** tab to adjust your view of the room and see how the entire room mesh appears in Unity.</span></span>
* <span data-ttu-id="ab675-263">在 [**專案**] 面板中，尋找**材料**資料夾，然後選取**BlueLinesOnWalls**材料。</span><span class="sxs-lookup"><span data-stu-id="ab675-263">In the **Project** panel, find the **Materials** folder and select the **BlueLinesOnWalls** material.</span></span>
* <span data-ttu-id="ab675-264">修改某些屬性，請參閱如何在 Unity 編輯器中顯示變更。</span><span class="sxs-lookup"><span data-stu-id="ab675-264">Modify some properties and see how the changes appear in the Unity editor.</span></span>
    * <span data-ttu-id="ab675-265">在 [ **Inspector** ] 面板中，調整**LineScale**讓出現較粗或越窄資料行的值。</span><span class="sxs-lookup"><span data-stu-id="ab675-265">In the **Inspector** panel, adjust the **LineScale** value to make the lines appear thicker or thinner.</span></span>
    * <span data-ttu-id="ab675-266">在 [ **Inspector** ] 面板中，調整**LinesPerMeter**變更多少行出現在每個背景牆上的值。</span><span class="sxs-lookup"><span data-stu-id="ab675-266">In the **Inspector** panel, adjust the **LinesPerMeter** value to change how many lines appear on each wall.</span></span>
* <span data-ttu-id="ab675-267">按一下 **播放**，結束 預覽 模式。</span><span class="sxs-lookup"><span data-stu-id="ab675-267">Click **Play** again to exit preview mode.</span></span>
* <span data-ttu-id="ab675-268">建置和部署到 HoloLens 並觀察著色器呈現實際的介面上的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="ab675-268">Build and deploy to the HoloLens and observe how the shader rendering appears on real surfaces.</span></span>

<span data-ttu-id="ab675-269">Unity 直接挑明解的預覽資料，但它一律是個不錯的主意，在裝置中的簽出轉譯。</span><span class="sxs-lookup"><span data-stu-id="ab675-269">Unity does a great job of previewing materials, but it's always a good idea to check-out rendering in the device.</span></span>

## <a name="chapter-3---processing"></a><span data-ttu-id="ab675-270">第 3 章-處理</span><span class="sxs-lookup"><span data-stu-id="ab675-270">Chapter 3 - Processing</span></span>

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

<span data-ttu-id="ab675-271">**目標**</span><span class="sxs-lookup"><span data-stu-id="ab675-271">**Objectives**</span></span>
* <span data-ttu-id="ab675-272">了解技術來處理您的應用程式中使用的空間的對應資料。</span><span class="sxs-lookup"><span data-stu-id="ab675-272">Learn techniques to process spatial mapping data for use in your application.</span></span>
* <span data-ttu-id="ab675-273">分析空間對應的資料，來尋找飛機，並移除三角形。</span><span class="sxs-lookup"><span data-stu-id="ab675-273">Analyze spatial mapping data to find planes and remove triangles.</span></span>
* <span data-ttu-id="ab675-274">使用全像放置平面。</span><span class="sxs-lookup"><span data-stu-id="ab675-274">Use planes for hologram placement.</span></span>

<span data-ttu-id="ab675-275">**指示**</span><span class="sxs-lookup"><span data-stu-id="ab675-275">**Instructions**</span></span>
* <span data-ttu-id="ab675-276">在 Unity**專案** 面板中，**全像投影**資料夾中，尋找**SpatialProcessing**物件。</span><span class="sxs-lookup"><span data-stu-id="ab675-276">In Unity's **Project** panel, **Holograms** folder, find the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="ab675-277">拖放**SpatialProcessing**物件插入**階層**面板。</span><span class="sxs-lookup"><span data-stu-id="ab675-277">Drag & drop the **SpatialProcessing** object into the **Hierarchy** panel.</span></span>

<span data-ttu-id="ab675-278">SpatialProcessing prefab 包含元件處理空間的對應資料。</span><span class="sxs-lookup"><span data-stu-id="ab675-278">The SpatialProcessing prefab includes components for processing the spatial mapping data.</span></span> <span data-ttu-id="ab675-279">**SurfaceMeshesToPlanes.cs**會尋找並產生空間的對應資料為基礎的平面。</span><span class="sxs-lookup"><span data-stu-id="ab675-279">**SurfaceMeshesToPlanes.cs** will find and generate planes based on the spatial mapping data.</span></span> <span data-ttu-id="ab675-280">我們將使用我們的應用程式中的平面，來代表牆壁、 樓層及上限。</span><span class="sxs-lookup"><span data-stu-id="ab675-280">We will use planes in our application to represent walls, floors and ceilings.</span></span> <span data-ttu-id="ab675-281">也包含此 prefab **RemoveSurfaceVertices.cs**這可以移除空間對應網狀結構中的頂點。</span><span class="sxs-lookup"><span data-stu-id="ab675-281">This prefab also includes **RemoveSurfaceVertices.cs** which can remove vertices from the spatial mapping mesh.</span></span> <span data-ttu-id="ab675-282">這可以用來建立的網狀結構中的漏洞，或移除多餘的三角形，不再需要 （因為可以改用平面）。</span><span class="sxs-lookup"><span data-stu-id="ab675-282">This can be used to create holes in the mesh, or to remove excess triangles that are no longer needed (because planes can be used instead).</span></span>
* <span data-ttu-id="ab675-283">在 Unity**專案** 面板中，**全像投影**資料夾中，尋找**SpaceCollection**物件。</span><span class="sxs-lookup"><span data-stu-id="ab675-283">In Unity's **Project** panel, **Holograms** folder, find the **SpaceCollection** object.</span></span>
* <span data-ttu-id="ab675-284">將拖放**SpaceCollection**物件插入**階層**面板。</span><span class="sxs-lookup"><span data-stu-id="ab675-284">Drag and drop the **SpaceCollection** object into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="ab675-285">在 **階層**面板中，選取**SpatialProcessing**物件。</span><span class="sxs-lookup"><span data-stu-id="ab675-285">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="ab675-286">在 [ **Inspector** ] 面板中，尋找**播放 （指令碼） 的空間 Manager**元件。</span><span class="sxs-lookup"><span data-stu-id="ab675-286">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="ab675-287">按兩下**PlaySpaceManager.cs**在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="ab675-287">Double-click on **PlaySpaceManager.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="ab675-288">PlaySpaceManager.cs 包含特定應用程式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ab675-288">PlaySpaceManager.cs contains application-specific code.</span></span> <span data-ttu-id="ab675-289">我們會將功能加入此指令碼，以啟用下列行為：</span><span class="sxs-lookup"><span data-stu-id="ab675-289">We will add functionality to this script to enable the following behavior:</span></span>
1. <span data-ttu-id="ab675-290">停止收集資料空間的對應之後我們超過掃描的時間限制 （10 秒）。</span><span class="sxs-lookup"><span data-stu-id="ab675-290">Stop collecting spatial mapping data after we exceed the scanning time limit (10 seconds).</span></span>
2. <span data-ttu-id="ab675-291">處理序空間的對應資料：</span><span class="sxs-lookup"><span data-stu-id="ab675-291">Process the spatial mapping data:</span></span>
    1. <span data-ttu-id="ab675-292">您可以使用 SurfaceMeshesToPlanes 建立平面 （牆壁、 樓層、 上限等） 的簡單世界的表示法。</span><span class="sxs-lookup"><span data-stu-id="ab675-292">Use SurfaceMeshesToPlanes to create a simpler representation of the world as planes (walls, floors, ceilings, etc).</span></span>
    2. <span data-ttu-id="ab675-293">您可以使用 RemoveSurfaceVertices 移除介面平面界限內的三角形。</span><span class="sxs-lookup"><span data-stu-id="ab675-293">Use RemoveSurfaceVertices to remove surface triangles that fall within plane boundaries.</span></span>
3. <span data-ttu-id="ab675-294">在世界裡產生的全像投影集合，並將它們放在接近使用者的背景牆和樓層平面上。</span><span class="sxs-lookup"><span data-stu-id="ab675-294">Generate a collection of holograms in the world and place them on wall and floor planes near the user.</span></span>

<span data-ttu-id="ab675-295">完成中 PlaySpaceManager.cs，標示的程式碼撰寫練習，或從下方取代已完成解決方案的指令碼：</span><span class="sxs-lookup"><span data-stu-id="ab675-295">Complete the coding exercises marked in PlaySpaceManager.cs, or replace the script with the finished solution from below:</span></span>

```cs
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;

/// <summary>
/// The SurfaceManager class allows applications to scan the environment for a specified amount of time 
/// and then process the Spatial Mapping Mesh (find planes, remove vertices) after that time has expired.
/// </summary>
public class PlaySpaceManager : Singleton<PlaySpaceManager>
{
    [Tooltip("When checked, the SurfaceObserver will stop running after a specified amount of time.")]
    public bool limitScanningByTime = true;

    [Tooltip("How much time (in seconds) that the SurfaceObserver will run after being started; used when 'Limit Scanning By Time' is checked.")]
    public float scanTime = 30.0f;

    [Tooltip("Material to use when rendering Spatial Mapping meshes while the observer is running.")]
    public Material defaultMaterial;

    [Tooltip("Optional Material to use when rendering Spatial Mapping meshes after the observer has been stopped.")]
    public Material secondaryMaterial;

    [Tooltip("Minimum number of floor planes required in order to exit scanning/processing mode.")]
    public uint minimumFloors = 1;

    [Tooltip("Minimum number of wall planes required in order to exit scanning/processing mode.")]
    public uint minimumWalls = 1;

    /// <summary>
    /// Indicates if processing of the surface meshes is complete.
    /// </summary>
    private bool meshesProcessed = false;

    /// <summary>
    /// GameObject initialization.
    /// </summary>
    private void Start()
    {
        // Update surfaceObserver and storedMeshes to use the same material during scanning.
        SpatialMappingManager.Instance.SetSurfaceMaterial(defaultMaterial);

        // Register for the MakePlanesComplete event.
        SurfaceMeshesToPlanes.Instance.MakePlanesComplete += SurfaceMeshesToPlanes_MakePlanesComplete;
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        // Check to see if the spatial mapping data has been processed
        // and if we are limiting how much time the user can spend scanning.
        if (!meshesProcessed && limitScanningByTime)
        {
            // If we have not processed the spatial mapping data
            // and scanning time is limited...

            // Check to see if enough scanning time has passed
            // since starting the observer.
            if (limitScanningByTime && ((Time.time - SpatialMappingManager.Instance.StartTime) < scanTime))
            {
                // If we have a limited scanning time, then we should wait until
                // enough time has passed before processing the mesh.
            }
            else
            {
                // The user should be done scanning their environment,
                // so start processing the spatial mapping data...

                /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

                // 3.a: Check if IsObserverRunning() is true on the
                // SpatialMappingManager.Instance.
                if(SpatialMappingManager.Instance.IsObserverRunning())
                {
                    // 3.a: If running, Stop the observer by calling
                    // StopObserver() on the SpatialMappingManager.Instance.
                    SpatialMappingManager.Instance.StopObserver();
                }

                // 3.a: Call CreatePlanes() to generate planes.
                CreatePlanes();

                // 3.a: Set meshesProcessed to true.
                meshesProcessed = true;
            }
        }
    }

    /// <summary>
    /// Handler for the SurfaceMeshesToPlanes MakePlanesComplete event.
    /// </summary>
    /// <param name="source">Source of the event.</param>
    /// <param name="args">Args for the event.</param>
    private void SurfaceMeshesToPlanes_MakePlanesComplete(object source, System.EventArgs args)
    {
        /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

        // Collection of floor and table planes that we can use to set horizontal items on.
        List<GameObject> horizontal = new List<GameObject>();

        // Collection of wall planes that we can use to set vertical items on.
        List<GameObject> vertical = new List<GameObject>();

        // 3.a: Get all floor and table planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'horizontal' list.
        horizontal = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Table | PlaneTypes.Floor);

        // 3.a: Get all wall planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'vertical' list.
        vertical = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Wall);

        // Check to see if we have enough horizontal planes (minimumFloors)
        // and vertical planes (minimumWalls), to set holograms on in the world.
        if (horizontal.Count >= minimumFloors && vertical.Count >= minimumWalls)
        {
            // We have enough floors and walls to place our holograms on...

            // 3.a: Let's reduce our triangle count by removing triangles
            // from SpatialMapping meshes that intersect with our active planes.
            // Call RemoveVertices().
            // Pass in all activePlanes found by SurfaceMeshesToPlanes.Instance.
            RemoveVertices(SurfaceMeshesToPlanes.Instance.ActivePlanes);

            // 3.a: We can indicate to the user that scanning is over by
            // changing the material applied to the Spatial Mapping meshes.
            // Call SpatialMappingManager.Instance.SetSurfaceMaterial().
            // Pass in the secondaryMaterial.
            SpatialMappingManager.Instance.SetSurfaceMaterial(secondaryMaterial);

            // 3.a: We are all done processing the mesh, so we can now
            // initialize a collection of Placeable holograms in the world
            // and use horizontal/vertical planes to set their starting positions.
            // Call SpaceCollectionManager.Instance.GenerateItemsInWorld().
            // Pass in the lists of horizontal and vertical planes that we found earlier.
            SpaceCollectionManager.Instance.GenerateItemsInWorld(horizontal, vertical);
        }
        else
        {
            // We do not have enough floors/walls to place our holograms on...

            // 3.a: Re-enter scanning mode so the user can find more surfaces by 
            // calling StartObserver() on the SpatialMappingManager.Instance.
            SpatialMappingManager.Instance.StartObserver();

            // 3.a: Re-process spatial data after scanning completes by
            // re-setting meshesProcessed to false.
            meshesProcessed = false;
        }
    }

    /// <summary>
    /// Creates planes from the spatial mapping surfaces.
    /// </summary>
    private void CreatePlanes()
    {
        // Generate planes based on the spatial map.
        SurfaceMeshesToPlanes surfaceToPlanes = SurfaceMeshesToPlanes.Instance;
        if (surfaceToPlanes != null && surfaceToPlanes.enabled)
        {
            surfaceToPlanes.MakePlanes();
        }
    }

    /// <summary>
    /// Removes triangles from the spatial mapping surfaces.
    /// </summary>
    /// <param name="boundingObjects"></param>
    private void RemoveVertices(IEnumerable<GameObject> boundingObjects)
    {
        RemoveSurfaceVertices removeVerts = RemoveSurfaceVertices.Instance;
        if (removeVerts != null && removeVerts.enabled)
        {
            removeVerts.RemoveSurfaceVerticesWithinBounds(boundingObjects);
        }
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        if (SurfaceMeshesToPlanes.Instance != null)
        {
            SurfaceMeshesToPlanes.Instance.MakePlanesComplete -= SurfaceMeshesToPlanes_MakePlanesComplete;
        }
    }
}
```

<span data-ttu-id="ab675-296">**建置和部署**</span><span class="sxs-lookup"><span data-stu-id="ab675-296">**Build and Deploy**</span></span>
* <span data-ttu-id="ab675-297">在之前部署到 HoloLens 上，按下**播放**Unity 輸入播放模式中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="ab675-297">Before deploying to the HoloLens, press the **Play** button in Unity to enter play mode.</span></span>
* <span data-ttu-id="ab675-298">聊天室網格會從檔案載入之後，請等候 10 秒前開始空間對應 mesh 上的處理。</span><span class="sxs-lookup"><span data-stu-id="ab675-298">After the room mesh is loaded from file, wait for 10 seconds before processing starts on the spatial mapping mesh.</span></span>
* <span data-ttu-id="ab675-299">處理序完成時，飛機會出現代表樓層、 牆壁、 ceiling、 等等。</span><span class="sxs-lookup"><span data-stu-id="ab675-299">When processing is complete, planes will appear to represent the floor, walls, ceiling, etc.</span></span>
* <span data-ttu-id="ab675-300">在所有的平面會被發現，您應該會看到太陽系，會出現在接近觀景窗的樓層的資料表。</span><span class="sxs-lookup"><span data-stu-id="ab675-300">After all of the planes have been found, you should see a solar system appear on a table of floor near the camera.</span></span>
* <span data-ttu-id="ab675-301">兩個海報應該會出現在接近觀景窗的背景牆上太。</span><span class="sxs-lookup"><span data-stu-id="ab675-301">Two posters should appear on walls near the camera too.</span></span> <span data-ttu-id="ab675-302">切換至**場景**索引標籤上，如果看不到它們**遊戲**模式。</span><span class="sxs-lookup"><span data-stu-id="ab675-302">Switch to the **Scene** tab if you cannot see them in **Game** mode.</span></span>
* <span data-ttu-id="ab675-303">按下**播放** 按鈕以結束遊戲模式。</span><span class="sxs-lookup"><span data-stu-id="ab675-303">Press the **Play** button again to exit play mode.</span></span>
* <span data-ttu-id="ab675-304">建置並部署至 HoloLens，像往常一樣。</span><span class="sxs-lookup"><span data-stu-id="ab675-304">Build and deploy to the HoloLens, as usual.</span></span>
* <span data-ttu-id="ab675-305">等候掃描，以及處理空間的對應資料，才能完成。</span><span class="sxs-lookup"><span data-stu-id="ab675-305">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="ab675-306">一旦您看到平面，試著找出您的世界中的太陽系和海報。</span><span class="sxs-lookup"><span data-stu-id="ab675-306">Once you see planes, try to find the solar system and posters in your world.</span></span>

## <a name="chapter-4---placement"></a><span data-ttu-id="ab675-307">第 4 章-位置</span><span class="sxs-lookup"><span data-stu-id="ab675-307">Chapter 4 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

<span data-ttu-id="ab675-308">**目標**</span><span class="sxs-lookup"><span data-stu-id="ab675-308">**Objectives**</span></span>
* <span data-ttu-id="ab675-309">決定是否全像圖都會百分之百符合介面上。</span><span class="sxs-lookup"><span data-stu-id="ab675-309">Determine if a hologram will fit on a surface.</span></span>
* <span data-ttu-id="ab675-310">雷射可以或不符合在介面上時，請提供意見給使用者。</span><span class="sxs-lookup"><span data-stu-id="ab675-310">Provide feedback to the user when a hologram can/cannot fit on a surface.</span></span>

<span data-ttu-id="ab675-311">**指示**</span><span class="sxs-lookup"><span data-stu-id="ab675-311">**Instructions**</span></span>
* <span data-ttu-id="ab675-312">在 Unity**階層**面板中，選取**SpatialProcessing**物件。</span><span class="sxs-lookup"><span data-stu-id="ab675-312">In Unity's **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="ab675-313">在 [ **Inspector** ] 面板中，尋找**介面網狀結構至平面 （指令碼）** 元件。</span><span class="sxs-lookup"><span data-stu-id="ab675-313">In the **Inspector** panel, find the **Surface Meshes To Planes (Script)** component.</span></span>
* <span data-ttu-id="ab675-314">變更**繪製平面**屬性設**Nothing**清除選取項目。</span><span class="sxs-lookup"><span data-stu-id="ab675-314">Change the **Draw Planes** property to **Nothing** to clear the selection.</span></span>
* <span data-ttu-id="ab675-315">變更**繪製平面**屬性設**牆**，如此一來，只有牆平面將會呈現。</span><span class="sxs-lookup"><span data-stu-id="ab675-315">Change the **Draw Planes** property to **Wall**, so that only wall planes will be rendered.</span></span>
* <span data-ttu-id="ab675-316">在 [**專案**] 面板中，**指令碼**資料夾中，按兩下**Placeable.cs**在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="ab675-316">In the **Project** panel, **Scripts** folder, double-click on **Placeable.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="ab675-317">**Placeable**指令碼已附加至平面尋找完成之後所建立的海報和投影。</span><span class="sxs-lookup"><span data-stu-id="ab675-317">The **Placeable** script is already attached to the posters and projection box that are created after plane finding completes.</span></span> <span data-ttu-id="ab675-318">我們只需要為一些程式碼，取消註解，此指令碼將會達到下列目的：</span><span class="sxs-lookup"><span data-stu-id="ab675-318">All we need to do is uncomment some code, and this script will achieve the following:</span></span>
1. <span data-ttu-id="ab675-319">決定是否全像圖都會百分之百符合由中央和四個角落的週框的 cube raycasting 介面上。</span><span class="sxs-lookup"><span data-stu-id="ab675-319">Determine if a hologram will fit on a surface by raycasting from the center and four corners of the bounding cube.</span></span>
2. <span data-ttu-id="ab675-320">請檢查以判斷是否順利清除坐全像圖的一般介面。</span><span class="sxs-lookup"><span data-stu-id="ab675-320">Check the surface normal to determine if it is smooth enough for the hologram to sit flush on.</span></span>
3. <span data-ttu-id="ab675-321">轉譯時放顯示實際大小闀週框 olap cube。</span><span class="sxs-lookup"><span data-stu-id="ab675-321">Render a bounding cube around the hologram to show its actual size while being placed.</span></span>
4. <span data-ttu-id="ab675-322">投射陰影下/背後全像圖來顯示它放置在 floor/塗鴉牆上。</span><span class="sxs-lookup"><span data-stu-id="ab675-322">Cast a shadow under/behind the hologram to show where it will be placed on the floor/wall.</span></span>
5. <span data-ttu-id="ab675-323">如果全像不能放在介面中或綠色，如果可以請為紅色，轉譯的陰影。</span><span class="sxs-lookup"><span data-stu-id="ab675-323">Render the shadow as red, if the hologram cannot be placed on the surface, or green, if it can.</span></span>
6. <span data-ttu-id="ab675-324">重新導向以配合其同質性介面的型別 （垂直或水平） 全像圖。</span><span class="sxs-lookup"><span data-stu-id="ab675-324">Re-orient the hologram to align with the surface type (vertical or horizontal) that it has affinity to.</span></span>
7. <span data-ttu-id="ab675-325">順暢全像置於選取的介面，以避免跳躍或貼齊行為。</span><span class="sxs-lookup"><span data-stu-id="ab675-325">Smoothly place the hologram on the selected surface to avoid jumping or snapping behavior.</span></span>

<span data-ttu-id="ab675-326">在下面的程式碼撰寫練習中的所有程式碼取消註解，或使用內已完成的解決方案**Placeable.cs**:</span><span class="sxs-lookup"><span data-stu-id="ab675-326">Uncomment all code in the coding exercise below, or use this completed solution in **Placeable.cs**:</span></span>

```cs
using System.Collections.Generic;
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Enumeration containing the surfaces on which a GameObject
/// can be placed.  For simplicity of this sample, only one
/// surface type is allowed to be selected.
/// </summary>
public enum PlacementSurfaces
{
    // Horizontal surface with an upward pointing normal.    
    Horizontal = 1,

    // Vertical surface with a normal facing the user.
    Vertical = 2,
}

/// <summary>
/// The Placeable class implements the logic used to determine if a GameObject
/// can be placed on a target surface. Constraints for placement include:
/// * No part of the GameObject's box collider impacts with another object in the scene
/// * The object lays flat (within specified tolerances) against the surface
/// * The object would not fall off of the surface if gravity were enabled.
/// This class also provides the following visualizations.
/// * A transparent cube representing the object's box collider.
/// * Shadow on the target surface indicating whether or not placement is valid.
/// </summary>
public class Placeable : MonoBehaviour
{
    [Tooltip("The base material used to render the bounds asset when placement is allowed.")]
    public Material PlaceableBoundsMaterial = null;

    [Tooltip("The base material used to render the bounds asset when placement is not allowed.")]
    public Material NotPlaceableBoundsMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it allowed.")]
    public Material PlaceableShadowMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it not allowed.")]
    public Material NotPlaceableShadowMaterial = null;

    [Tooltip("The type of surface on which the object can be placed.")]
    public PlacementSurfaces PlacementSurface = PlacementSurfaces.Horizontal;

    [Tooltip("The child object(s) to hide during placement.")]
    public List<GameObject> ChildrenToHide = new List<GameObject>();

    /// <summary>
    /// Indicates if the object is in the process of being placed.
    /// </summary>
    public bool IsPlacing { get; private set; }

    // The most recent distance to the surface.  This is used to 
    // locate the object when the user's gaze does not intersect
    // with the Spatial Mapping mesh.
    private float lastDistance = 2.0f;

    // The distance away from the target surface that the object should hover prior while being placed.
    private float hoverDistance = 0.15f;

    // Threshold (the closer to 0, the stricter the standard) used to determine if a surface is flat.
    private float distanceThreshold = 0.02f;

    // Threshold (the closer to 1, the stricter the standard) used to determine if a surface is vertical.
    private float upNormalThreshold = 0.9f;

    // Maximum distance, from the object, that placement is allowed.
    // This is used when raycasting to see if the object is near a placeable surface.
    private float maximumPlacementDistance = 5.0f;

    // Speed (1.0 being fastest) at which the object settles to the surface upon placement.
    private float placementVelocity = 0.06f;

    // Indicates whether or not this script manages the object's box collider.
    private bool managingBoxCollider = false;

    // The box collider used to determine of the object will fit in the desired location.
    // It is also used to size the bounding cube.
    private BoxCollider boxCollider = null;

    // Visible asset used to show the dimensions of the object. This asset is sized
    // using the box collider's bounds.
    private GameObject boundsAsset = null;

    // Visible asset used to show the where the object is attempting to be placed.
    // This asset is sized using the box collider's bounds.
    private GameObject shadowAsset = null;

    // The location at which the object will be placed.
    private Vector3 targetPosition;

    /// <summary>
    /// Called when the GameObject is created.
    /// </summary>
    private void Awake()
    {
        targetPosition = gameObject.transform.position;

        // Get the object's collider.
        boxCollider = gameObject.GetComponent<BoxCollider>();
        if (boxCollider == null)
        {
            // The object does not have a collider, create one and remember that
            // we are managing it.
            managingBoxCollider = true;
            boxCollider = gameObject.AddComponent<BoxCollider>();
            boxCollider.enabled = false;
        }

        // Create the object that will be used to indicate the bounds of the GameObject.
        boundsAsset = GameObject.CreatePrimitive(PrimitiveType.Cube);
        boundsAsset.transform.parent = gameObject.transform;
        boundsAsset.SetActive(false);

        // Create a object that will be used as a shadow.
        shadowAsset = GameObject.CreatePrimitive(PrimitiveType.Quad);
        shadowAsset.transform.parent = gameObject.transform;
        shadowAsset.SetActive(false);
    }

    /// <summary>
    /// Called when our object is selected.  Generally called by
    /// a gesture management component.
    /// </summary>
    public void OnSelect()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (!IsPlacing)
        {
            OnPlacementStart();
        }
        else
        {
            OnPlacementStop();
        }
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (IsPlacing)
        {
            // Move the object.
            Move();

            // Set the visual elements.
            Vector3 targetPosition;
            Vector3 surfaceNormal;
            bool canBePlaced = ValidatePlacement(out targetPosition, out surfaceNormal);
            DisplayBounds(canBePlaced);
            DisplayShadow(targetPosition, surfaceNormal, canBePlaced);
        }
        else
        {
            // Disable the visual elements.
            boundsAsset.SetActive(false);
            shadowAsset.SetActive(false);

            // Gracefully place the object on the target surface.
            float dist = (gameObject.transform.position - targetPosition).magnitude;
            if (dist > 0)
            {
                gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, targetPosition, placementVelocity / dist);
            }
            else
            {
                // Unhide the child object(s) to make placement easier.
                for (int i = 0; i < ChildrenToHide.Count; i++)
                {
                    ChildrenToHide[i].SetActive(true);
                }
            }
        }
    }

    /// <summary>
    /// Verify whether or not the object can be placed.
    /// </summary>
    /// <param name="position">
    /// The target position on the surface.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the object is to be placed.
    /// </param>
    /// <returns>
    /// True if the target position is valid for placing the object, otherwise false.
    /// </returns>
    private bool ValidatePlacement(out Vector3 position, out Vector3 surfaceNormal)
    {
        Vector3 raycastDirection = gameObject.transform.forward;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            // Raycast from the bottom face of the box collider.
            raycastDirection = -(Vector3.up);
        }

        // Initialize out parameters.
        position = Vector3.zero;
        surfaceNormal = Vector3.zero;

        Vector3[] facePoints = GetColliderFacePoints();

        // The origin points we receive are in local space and we 
        // need to raycast in world space.
        for (int i = 0; i < facePoints.Length; i++)
        {
            facePoints[i] = gameObject.transform.TransformVector(facePoints[i]) + gameObject.transform.position;
        }

        // Cast a ray from the center of the box collider face to the surface.
        RaycastHit centerHit;
        if (!Physics.Raycast(facePoints[0],
                        raycastDirection,
                        out centerHit,
                        maximumPlacementDistance,
                        SpatialMappingManager.Instance.LayerMask))
        {
            // If the ray failed to hit the surface, we are done.
            return false;
        }

        // We have found a surface.  Set position and surfaceNormal.
        position = centerHit.point;
        surfaceNormal = centerHit.normal;

        // Cast a ray from the corners of the box collider face to the surface.
        for (int i = 1; i < facePoints.Length; i++)
        {
            RaycastHit hitInfo;
            if (Physics.Raycast(facePoints[i],
                                raycastDirection,
                                out hitInfo,
                                maximumPlacementDistance,
                                SpatialMappingManager.Instance.LayerMask))
            {
                // To be a valid placement location, each of the corners must have a similar
                // enough distance to the surface as the center point
                if (!IsEquivalentDistance(centerHit.distance, hitInfo.distance))
                {
                    return false;
                }
            }
            else
            {
                // The raycast failed to intersect with the target layer.
                return false;
            }
        }

        return true;
    }

    /// <summary>
    /// Determine the coordinates, in local space, of the box collider face that 
    /// will be placed against the target surface.
    /// </summary>
    /// <returns>
    /// Vector3 array with the center point of the face at index 0.
    /// </returns>
    private Vector3[] GetColliderFacePoints()
    {
        // Get the collider extents.  
        // The size values are twice the extents.
        Vector3 extents = boxCollider.size / 2;

        // Calculate the min and max values for each coordinate.
        float minX = boxCollider.center.x - extents.x;
        float maxX = boxCollider.center.x + extents.x;
        float minY = boxCollider.center.y - extents.y;
        float maxY = boxCollider.center.y + extents.y;
        float minZ = boxCollider.center.z - extents.z;
        float maxZ = boxCollider.center.z + extents.z;

        Vector3 center;
        Vector3 corner0;
        Vector3 corner1;
        Vector3 corner2;
        Vector3 corner3;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            center = new Vector3(boxCollider.center.x, minY, boxCollider.center.z);
            corner0 = new Vector3(minX, minY, minZ);
            corner1 = new Vector3(minX, minY, maxZ);
            corner2 = new Vector3(maxX, minY, minZ);
            corner3 = new Vector3(maxX, minY, maxZ);
        }
        else
        {
            // Placing on vertical surfaces.
            center = new Vector3(boxCollider.center.x, boxCollider.center.y, maxZ);
            corner0 = new Vector3(minX, minY, maxZ);
            corner1 = new Vector3(minX, maxY, maxZ);
            corner2 = new Vector3(maxX, minY, maxZ);
            corner3 = new Vector3(maxX, maxY, maxZ);
        }

        return new Vector3[] { center, corner0, corner1, corner2, corner3 };
    }

    /// <summary>
    /// Put the object into placement mode.
    /// </summary>
    public void OnPlacementStart()
    {
        // If we are managing the collider, enable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = true;
        }

        // Hide the child object(s) to make placement easier.
        for (int i = 0; i < ChildrenToHide.Count; i++)
        {
            ChildrenToHide[i].SetActive(false);
        }

        // Tell the gesture manager that it is to assume
        // all input is to be given to this object.
        GestureManager.Instance.OverrideFocusedObject = gameObject;

        // Enter placement mode.
        IsPlacing = true;
    }

    /// <summary>
    /// Take the object out of placement mode.
    /// </summary>
    /// <remarks>
    /// This method will leave the object in placement mode if called while
    /// the object is in an invalid location.  To determine whether or not
    /// the object has been placed, check the value of the IsPlacing property.
    /// </remarks>
    public void OnPlacementStop()
    {
        // ValidatePlacement requires a normal as an out parameter.
        Vector3 position;
        Vector3 surfaceNormal;

        // Check to see if we can exit placement mode.
        if (!ValidatePlacement(out position, out surfaceNormal))
        {
            return;
        }

        // The object is allowed to be placed.
        // We are placing at a small buffer away from the surface.
        targetPosition = position + (0.01f * surfaceNormal);

        OrientObject(true, surfaceNormal);

        // If we are managing the collider, disable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = false;
        }

        // Tell the gesture manager that it is to resume
        // its normal behavior.
        GestureManager.Instance.OverrideFocusedObject = null;

        // Exit placement mode.
        IsPlacing = false;
    }

    /// <summary>
    /// Positions the object along the surface toward which the user is gazing.
    /// </summary>
    /// <remarks>
    /// If the user's gaze does not intersect with a surface, the object
    /// will remain at the most recently calculated distance.
    /// </remarks>
    private void Move()
    {
        Vector3 moveTo = gameObject.transform.position;
        Vector3 surfaceNormal = Vector3.zero;
        RaycastHit hitInfo;

        bool hit = Physics.Raycast(Camera.main.transform.position,
                                Camera.main.transform.forward,
                                out hitInfo,
                                20f,
                                SpatialMappingManager.Instance.LayerMask);

        if (hit)
        {
            float offsetDistance = hoverDistance;

            // Place the object a small distance away from the surface while keeping 
            // the object from going behind the user.
            if (hitInfo.distance <= hoverDistance)
            {
                offsetDistance = 0f;
            }

            moveTo = hitInfo.point + (offsetDistance * hitInfo.normal);

            lastDistance = hitInfo.distance;
            surfaceNormal = hitInfo.normal;
        }
        else
        {
            // The raycast failed to hit a surface.  In this case, keep the object at the distance of the last
            // intersected surface.
            moveTo = Camera.main.transform.position + (Camera.main.transform.forward * lastDistance);
        }

        // Follow the user's gaze.
        float dist = Mathf.Abs((gameObject.transform.position - moveTo).magnitude);
        gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, moveTo, placementVelocity / dist);

        // Orient the object.
        // We are using the return value from Physics.Raycast to instruct
        // the OrientObject function to align to the vertical surface if appropriate.
        OrientObject(hit, surfaceNormal);
    }

    /// <summary>
    /// Orients the object so that it faces the user.
    /// </summary>
    /// <param name="alignToVerticalSurface">
    /// If true and the object is to be placed on a vertical surface, 
    /// orient parallel to the target surface.  If false, orient the object 
    /// to face the user.
    /// </param>
    /// <param name="surfaceNormal">
    /// The target surface's normal vector.
    /// </param>
    /// <remarks>
    /// The aligntoVerticalSurface parameter is ignored if the object
    /// is to be placed on a horizontalSurface
    /// </remarks>
    private void OrientObject(bool alignToVerticalSurface, Vector3 surfaceNormal)
    {
        Quaternion rotation = Camera.main.transform.localRotation;

        // If the user's gaze does not intersect with the Spatial Mapping mesh,
        // orient the object towards the user.
        if (alignToVerticalSurface && (PlacementSurface == PlacementSurfaces.Vertical))
        {
            // We are placing on a vertical surface.
            // If the normal of the Spatial Mapping mesh indicates that the
            // surface is vertical, orient parallel to the surface.
            if (Mathf.Abs(surfaceNormal.y) <= (1 - upNormalThreshold))
            {
                rotation = Quaternion.LookRotation(-surfaceNormal, Vector3.up);
            }
        }
        else
        {
            rotation.x = 0f;
            rotation.z = 0f;
        }

        gameObject.transform.rotation = rotation;
    }

    /// <summary>
    /// Displays the bounds asset.
    /// </summary>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayBounds(bool canBePlaced)
    {
        // Ensure the bounds asset is sized and positioned correctly.
        boundsAsset.transform.localPosition = boxCollider.center;
        boundsAsset.transform.localScale = boxCollider.size;
        boundsAsset.transform.rotation = gameObject.transform.rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = PlaceableBoundsMaterial;
        }
        else
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableBoundsMaterial;
        }

        // Show the bounds asset.
        boundsAsset.SetActive(true);
    }

    /// <summary>
    /// Displays the placement shadow asset.
    /// </summary>
    /// <param name="position">
    /// The position at which to place the shadow asset.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the asset will be placed
    /// </param>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayShadow(Vector3 position,
                            Vector3 surfaceNormal,
                            bool canBePlaced)
    {
        // Rotate and scale the shadow so that it is displayed on the correct surface and matches the object.
        float rotationX = 0.0f;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            rotationX = 90.0f;
            shadowAsset.transform.localScale = new Vector3(boxCollider.size.x, boxCollider.size.z, 1);
        }
        else
        {
            shadowAsset.transform.localScale = boxCollider.size;
        }

        Quaternion rotation = Quaternion.Euler(rotationX, gameObject.transform.rotation.eulerAngles.y, 0);
        shadowAsset.transform.rotation = rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = PlaceableShadowMaterial;
        }
        else
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableShadowMaterial;
        }

        // Show the shadow asset as appropriate.        
        if (position != Vector3.zero)
        {
            // Position the shadow a small distance from the target surface, along the normal.
            shadowAsset.transform.position = position + (0.01f * surfaceNormal);
            shadowAsset.SetActive(true);
        }
        else
        {
            shadowAsset.SetActive(false);
        }
    }

    /// <summary>
    /// Determines if two distance values should be considered equivalent. 
    /// </summary>
    /// <param name="d1">
    /// Distance to compare.
    /// </param>
    /// <param name="d2">
    /// Distance to compare.
    /// </param>
    /// <returns>
    /// True if the distances are within the desired tolerance, otherwise false.
    /// </returns>
    private bool IsEquivalentDistance(float d1, float d2)
    {
        float dist = Mathf.Abs(d1 - d2);
        return (dist <= distanceThreshold);
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        // Unload objects we have created.
        Destroy(boundsAsset);
        boundsAsset = null;
        Destroy(shadowAsset);
        shadowAsset = null;
    }
}
```

<span data-ttu-id="ab675-327">**建置和部署**</span><span class="sxs-lookup"><span data-stu-id="ab675-327">**Build and Deploy**</span></span>
* <span data-ttu-id="ab675-328">同樣地，建置專案，並將部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="ab675-328">As before, build the project and deploy to the HoloLens.</span></span>
* <span data-ttu-id="ab675-329">等候掃描，以及處理空間的對應資料，才能完成。</span><span class="sxs-lookup"><span data-stu-id="ab675-329">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="ab675-330">當您看到太陽系時，注視下的 [投影] 方塊，並執行選取的動作並四處移動。</span><span class="sxs-lookup"><span data-stu-id="ab675-330">When you see the solar system, gaze at the projection box below and perform a select gesture to move it around.</span></span> <span data-ttu-id="ab675-331">選取 [投影] 方塊時，請週框的 cube 會顯示該投影的周圍。</span><span class="sxs-lookup"><span data-stu-id="ab675-331">While the projection box is selected, a bounding cube will be visible around the projection box.</span></span>
* <span data-ttu-id="ab675-332">將您注視聊天室中的不同位置的標頭。</span><span class="sxs-lookup"><span data-stu-id="ab675-332">Move you head to gaze at a different location in the room.</span></span> <span data-ttu-id="ab675-333">[投影] 方塊應遵循您的視線。</span><span class="sxs-lookup"><span data-stu-id="ab675-333">The projection box should follow your gaze.</span></span> <span data-ttu-id="ab675-334">當陰影投射方塊下方會變成紅色時，您無法將全像圖放在該介面上。</span><span class="sxs-lookup"><span data-stu-id="ab675-334">When the shadow below the projection box turns red, you cannot place the hologram on that surface.</span></span> <span data-ttu-id="ab675-335">當陰影投射方塊下方會變成綠色時，您可以將全像藉由執行另一個選取的筆勢。</span><span class="sxs-lookup"><span data-stu-id="ab675-335">When the shadow below the projection box turns green, you can place the hologram by performing another select gesture.</span></span>
* <span data-ttu-id="ab675-336">尋找並選取其中一個全像攝影版的海報上將它移至新位置。</span><span class="sxs-lookup"><span data-stu-id="ab675-336">Find and select one of the holographic posters on a wall to move it to a new location.</span></span> <span data-ttu-id="ab675-337">請注意，您無法將海報放上下限或上限，而且它會保持正確導向每個背景牆當您移動。</span><span class="sxs-lookup"><span data-stu-id="ab675-337">Notice that you cannot place the poster on the floor or ceiling, and that it stays correctly oriented to each wall as you move around.</span></span>

## <a name="chapter-5---occlusion"></a><span data-ttu-id="ab675-338">第 5 章-阻擋</span><span class="sxs-lookup"><span data-stu-id="ab675-338">Chapter 5 - Occlusion</span></span>

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

<span data-ttu-id="ab675-339">**目標**</span><span class="sxs-lookup"><span data-stu-id="ab675-339">**Objectives**</span></span>
* <span data-ttu-id="ab675-340">決定是否全像圖會阻擋空間對應網狀結構。</span><span class="sxs-lookup"><span data-stu-id="ab675-340">Determine if a hologram is occluded by the spatial mapping mesh.</span></span>
* <span data-ttu-id="ab675-341">套用不同的阻擋物技術以達成一個有趣效果。</span><span class="sxs-lookup"><span data-stu-id="ab675-341">Apply different occlusion techniques to achieve a fun effect.</span></span>

<span data-ttu-id="ab675-342">**指示**</span><span class="sxs-lookup"><span data-stu-id="ab675-342">**Instructions**</span></span>

<span data-ttu-id="ab675-343">首先，我們將允許 occlude 其他全像投影，而不需要 occluding 真實世界空間的對應網格：</span><span class="sxs-lookup"><span data-stu-id="ab675-343">First, we are going to allow the spatial mapping mesh to occlude other holograms without occluding the real world:</span></span>
* <span data-ttu-id="ab675-344">在 **階層**面板中，選取**SpatialProcessing**物件。</span><span class="sxs-lookup"><span data-stu-id="ab675-344">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="ab675-345">在 [ **Inspector** ] 面板中，尋找**播放 （指令碼） 的空間 Manager**元件。</span><span class="sxs-lookup"><span data-stu-id="ab675-345">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="ab675-346">按一下右側的圓形**次要材料**屬性。</span><span class="sxs-lookup"><span data-stu-id="ab675-346">Click the circle to the right of the **Secondary Material** property.</span></span>
* <span data-ttu-id="ab675-347">尋找並選取**阻擋**material 和關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="ab675-347">Find and select the **Occlusion** material and close the window.</span></span>

<span data-ttu-id="ab675-348">接下來，我們會將地球，特殊的行為，使其具有藍色醒目提示，它會變成阻擋其他全像 （例如，sun)，或空間的對應網狀結構時：</span><span class="sxs-lookup"><span data-stu-id="ab675-348">Next, we are going to add a special behavior to Earth, so that it has a blue highlight whenever it becomes occluded by another hologram (like the sun), or by the spatial mapping mesh:</span></span>
* <span data-ttu-id="ab675-349">在 [**專案**] 面板的**全像投影**資料夾中，展開**SolarSystem**物件。</span><span class="sxs-lookup"><span data-stu-id="ab675-349">In the **Project** panel, in the **Holograms** folder, expand the **SolarSystem** object.</span></span>
* <span data-ttu-id="ab675-350">按一下 **地球**。</span><span class="sxs-lookup"><span data-stu-id="ab675-350">Click on **Earth**.</span></span>
* <span data-ttu-id="ab675-351">在 [ **Inspector** ] 面板中，尋找地球的資料 （底部元件）。</span><span class="sxs-lookup"><span data-stu-id="ab675-351">In the **Inspector** panel, find the Earth's material (bottom component).</span></span>
* <span data-ttu-id="ab675-352">在 **著色器下拉式清單**，變更著色器**自訂 > OcclusionRim**。</span><span class="sxs-lookup"><span data-stu-id="ab675-352">In the **Shader drop-down**, change the shader to **Custom > OcclusionRim**.</span></span> <span data-ttu-id="ab675-353">每當另一個物件阻擋，這會造成地球周圍的藍色醒目提示。</span><span class="sxs-lookup"><span data-stu-id="ab675-353">This will render a blue highlight around Earth whenever it is occluded by another object.</span></span>

<span data-ttu-id="ab675-354">最後，我們會讓我們太陽系中行星 x 光視覺效果。</span><span class="sxs-lookup"><span data-stu-id="ab675-354">Finally, we are going to enable an x-ray vision effect for planets in our solar system.</span></span> <span data-ttu-id="ab675-355">我們將需要編輯**PlanetOcclusion.cs** （Scripts\SolarSystem 資料夾中找到） 才能達成以下目標：</span><span class="sxs-lookup"><span data-stu-id="ab675-355">We will need to edit **PlanetOcclusion.cs** (found in the Scripts\SolarSystem folder) in order to achieve the following:</span></span>
1. <span data-ttu-id="ab675-356">決定是否要將全球 occluded SpatialMapping 層 （聊天室網格和平面）。</span><span class="sxs-lookup"><span data-stu-id="ab675-356">Determine if a planet is occluded by the SpatialMapping layer (room meshes and planes).</span></span>
2. <span data-ttu-id="ab675-357">顯示全球的線框表示法，每當 SpatialMapping 層阻擋。</span><span class="sxs-lookup"><span data-stu-id="ab675-357">Show the wireframe representation of a planet whenever it is occluded by the SpatialMapping layer.</span></span>
3. <span data-ttu-id="ab675-358">全球的線框表示法時隱藏 SpatialMapping 層不會封鎖它。</span><span class="sxs-lookup"><span data-stu-id="ab675-358">Hide the wireframe representation of a planet when it is not blocked by the SpatialMapping layer.</span></span>

<span data-ttu-id="ab675-359">請依照下列程式碼撰寫練習在 PlanetOcclusion.cs，或使用下列解決方法：</span><span class="sxs-lookup"><span data-stu-id="ab675-359">Follow the coding exercise in PlanetOcclusion.cs, or use the following solution:</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Determines when the occluded version of the planet should be visible.
/// This script allows us to do selective occlusion, so the occlusionObject
/// will only be rendered when a Spatial Mapping surface is occluding the planet,
/// not when another hologram is responsible for the occlusion.
/// </summary>
public class PlanetOcclusion : MonoBehaviour
{
    [Tooltip("Object to display when the planet is occluded.")]
    public GameObject occlusionObject;

    /// <summary>
    /// Points to raycast to when checking for occlusion.
    /// </summary>
    private Vector3[] checkPoints;

    // Use this for initialization
    void Start()
    {
        occlusionObject.SetActive(false);

        // Set the check points to use when testing for occlusion.
        MeshFilter filter = gameObject.GetComponent<MeshFilter>();
        Vector3 extents = filter.mesh.bounds.extents;
        Vector3 center = filter.mesh.bounds.center;
        Vector3 top = new Vector3(center.x, center.y + extents.y, center.z);
        Vector3 left = new Vector3(center.x - extents.x, center.y, center.z);
        Vector3 right = new Vector3(center.x + extents.x, center.y, center.z);
        Vector3 bottom = new Vector3(center.x, center.y - extents.y, center.z);

        checkPoints = new Vector3[] { center, top, left, right, bottom };
    }

    // Update is called once per frame
    void Update()
    {
        /* TODO: 5.a DEVELOPER CODING EXERCISE 5.a */

        // Check to see if any of the planet's boundary points are occluded.
        for (int i = 0; i < checkPoints.Length; i++)
        {
            // 5.a: Convert the current checkPoint to world coordinates.
            // Call gameObject.transform.TransformPoint(checkPoints[i]).
            // Assign the result to a new Vector3 variable called 'checkPt'.
            Vector3 checkPt = gameObject.transform.TransformPoint(checkPoints[i]);

            // 5.a: Call Vector3.Distance() to calculate the distance
            // between the Main Camera's position and 'checkPt'.
            // Assign the result to a new float variable called 'distance'.
            float distance = Vector3.Distance(Camera.main.transform.position, checkPt);

            // 5.a: Take 'checkPt' and subtract the Main Camera's position from it.
            // Assign the result to a new Vector3 variable called 'direction'.
            Vector3 direction = checkPt - Camera.main.transform.position;

            // Used to indicate if the call to Physics.Raycast() was successful.
            bool raycastHit = false;

            // 5.a: Check if the planet is occluded by a spatial mapping surface.
            // Call Physics.Raycast() with the following arguments:
            // - Pass in the Main Camera's position as the origin.
            // - Pass in 'direction' for the direction.
            // - Pass in 'distance' for the maxDistance.
            // - Pass in SpatialMappingManager.Instance.LayerMask as layerMask.
            // Assign the result to 'raycastHit'.
            raycastHit = Physics.Raycast(Camera.main.transform.position, direction, distance, SpatialMappingManager.Instance.LayerMask);

            if (raycastHit)
            {
                // 5.a: Our raycast hit a surface, so the planet is occluded.
                // Set the occlusionObject to active.
                occlusionObject.SetActive(true);

                // At least one point is occluded, so break from the loop.
                break;
            }
            else
            {
                // 5.a: The Raycast did not hit, so the planet is not occluded.
                // Deactivate the occlusionObject.
                occlusionObject.SetActive(false);
            }
        }
    }
}
```

<span data-ttu-id="ab675-360">**建置和部署**</span><span class="sxs-lookup"><span data-stu-id="ab675-360">**Build and Deploy**</span></span>
* <span data-ttu-id="ab675-361">建置並如往常般部署 HoloLens，應用程式。</span><span class="sxs-lookup"><span data-stu-id="ab675-361">Build and deploy the application to HoloLens, as usual.</span></span>
* <span data-ttu-id="ab675-362">等候掃描和空間的對應資料，以完成處理 （您應該會看到出現在牆上的藍線）。</span><span class="sxs-lookup"><span data-stu-id="ab675-362">Wait for scanning and processing of the spatial mapping data to be complete (you should see blue lines appear on walls).</span></span>
* <span data-ttu-id="ab675-363">尋找和選取太陽系的 [投影] 方塊，然後將方塊旁邊的塗鴉牆或背後的計數器。</span><span class="sxs-lookup"><span data-stu-id="ab675-363">Find and select the solar system's projection box and then set the box next to a wall or behind a counter.</span></span>
* <span data-ttu-id="ab675-364">您可以檢視對等互連的海報，或是投影方塊介面背後的隱藏基本的阻擋物。</span><span class="sxs-lookup"><span data-stu-id="ab675-364">You can view basic occlusion by hiding behind surfaces to peer at the poster or projection box.</span></span>
* <span data-ttu-id="ab675-365">尋找地球，應該會有藍色醒目提示效果時它會在另一個全像圖或介面。</span><span class="sxs-lookup"><span data-stu-id="ab675-365">Look for the Earth, there should be a blue highlight effect whenever it goes behind another hologram or surface.</span></span>
* <span data-ttu-id="ab675-366">觀看行星移動在牆上或在聊天室中的其他介面。</span><span class="sxs-lookup"><span data-stu-id="ab675-366">Watch as the planets move behind the wall or other surfaces in the room.</span></span> <span data-ttu-id="ab675-367">現在，您會有 x 光，可以看到其框線基本架構 ！</span><span class="sxs-lookup"><span data-stu-id="ab675-367">You now have x-ray vision and can see their wireframe skeletons!</span></span>

## <a name="the-end"></a><span data-ttu-id="ab675-368">結束</span><span class="sxs-lookup"><span data-stu-id="ab675-368">The End</span></span>

<span data-ttu-id="ab675-369">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="ab675-369">Congratulations!</span></span> <span data-ttu-id="ab675-370">您現在已完成**MR 空間 230:空間對應**。</span><span class="sxs-lookup"><span data-stu-id="ab675-370">You have now completed **MR Spatial 230: Spatial mapping**.</span></span>
* <span data-ttu-id="ab675-371">您知道如何將掃描您的環境和負載空間的對應資料到 Unity。</span><span class="sxs-lookup"><span data-stu-id="ab675-371">You know how to scan your environment and load spatial mapping data to Unity.</span></span>
* <span data-ttu-id="ab675-372">您了解著色器，以及如何使用資料，以重新在世界各地以視覺化方式檢視基本的概念。</span><span class="sxs-lookup"><span data-stu-id="ab675-372">You understand the basics of shaders and how materials can be used to re-visualize the world.</span></span>
* <span data-ttu-id="ab675-373">您已了解新的處理技巧，來尋找平面移除網狀結構中的三角形。</span><span class="sxs-lookup"><span data-stu-id="ab675-373">You learned of new processing techniques for finding planes and removing triangles from a mesh.</span></span>
* <span data-ttu-id="ab675-374">您無法移動，並將全像投影放不二人選的表面。</span><span class="sxs-lookup"><span data-stu-id="ab675-374">You were able to move and place holograms on surfaces that made sense.</span></span>
* <span data-ttu-id="ab675-375">您發生不同的阻擋物技術，已經超人威力 ！</span><span class="sxs-lookup"><span data-stu-id="ab675-375">You experienced different occlusion techniques and harnessed the power of x-ray vision!</span></span>
