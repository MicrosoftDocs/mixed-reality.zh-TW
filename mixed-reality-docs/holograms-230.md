---
title: MR 空間 230-空間對應
description: 請遵循使用 Unity、Visual Studio 和 HoloLens 進行的編碼逐步解說, 以瞭解空間對應概念的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, 學院, 教學課程, 空間對應, 表面重建, 網格
ms.openlocfilehash: ed58676a0fda660cc6b4c197239aeb53166baa4d
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993564"
---
>[!NOTE]
><span data-ttu-id="1e659-104">混合現實學術教學課程的設計是使用 HoloLens (第1代) 和混合現實的沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="1e659-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="1e659-105">因此, 對於仍在尋找這些裝置開發指引的開發人員而言, 我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="1e659-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="1e659-106">這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="1e659-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="1e659-107">系統會保留這些資訊, 以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="1e659-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="1e659-108">未來將會有一系列新的教學課程, 將示範如何針對 HoloLens 2 進行開發。</span><span class="sxs-lookup"><span data-stu-id="1e659-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="1e659-109">此通知會在張貼時, 使用這些教學課程的連結進行更新。</span><span class="sxs-lookup"><span data-stu-id="1e659-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-230-spatial-mapping"></a><span data-ttu-id="1e659-110">MR 空間 230:空間對應</span><span class="sxs-lookup"><span data-stu-id="1e659-110">MR Spatial 230: Spatial mapping</span></span>

<span data-ttu-id="1e659-111">「[空間對應](spatial-mapping.md)」結合了真實世界與虛擬世界, 藉由教學有關環境的全息影像。</span><span class="sxs-lookup"><span data-stu-id="1e659-111">[Spatial mapping](spatial-mapping.md) combines the real world and virtual world together by teaching holograms about the environment.</span></span> <span data-ttu-id="1e659-112">在 MR 空間 230 (Project 天文館) 中, 我們將瞭解如何:</span><span class="sxs-lookup"><span data-stu-id="1e659-112">In MR Spatial 230 (Project Planetarium) we'll learn how to:</span></span>

* <span data-ttu-id="1e659-113">掃描環境, 並將資料從 HoloLens 傳輸至您的開發電腦。</span><span class="sxs-lookup"><span data-stu-id="1e659-113">Scan the environment and transfer data from the HoloLens to your development machine.</span></span>
* <span data-ttu-id="1e659-114">探索著色器, 並瞭解如何使用它們來視覺化您的空間。</span><span class="sxs-lookup"><span data-stu-id="1e659-114">Explore shaders and learn how to use them for visualizing your space.</span></span>
* <span data-ttu-id="1e659-115">使用網格處理將房間網格分解成簡單的平面。</span><span class="sxs-lookup"><span data-stu-id="1e659-115">Break down the room mesh into simple planes using mesh processing.</span></span>
* <span data-ttu-id="1e659-116">超越我們在[MR 基本概念 101](holograms-101.md)中所學到的放置技術, 並提供有關如何在環境中放置全息影像的意見反應。</span><span class="sxs-lookup"><span data-stu-id="1e659-116">Go beyond the placement techniques we learned in [MR Basics 101](holograms-101.md), and provide feedback about where a hologram can be placed in the environment.</span></span>
* <span data-ttu-id="1e659-117">探索遮蔽的效果, 因此當您的全息影像位於真實世界的物件後方時, 您仍然可以使用 x 光線願景來查看它!</span><span class="sxs-lookup"><span data-stu-id="1e659-117">Explore occlusion effects, so when your hologram is behind a real-world object, you can still see it with x-ray vision!</span></span>

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a><span data-ttu-id="1e659-118">裝置支援</span><span class="sxs-lookup"><span data-stu-id="1e659-118">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="1e659-119">粗</span><span class="sxs-lookup"><span data-stu-id="1e659-119">Course</span></span></th><th style="width:150px"> <span data-ttu-id="1e659-120"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1e659-120"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1e659-121"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="1e659-121"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="1e659-122">MR 空間 230:空間對應</span><span class="sxs-lookup"><span data-stu-id="1e659-122">MR Spatial 230: Spatial mapping</span></span></td><td style="text-align: center;"> <span data-ttu-id="1e659-123">✔️</span><span class="sxs-lookup"><span data-stu-id="1e659-123">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="1e659-124">開始之前</span><span class="sxs-lookup"><span data-stu-id="1e659-124">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="1e659-125">先決條件</span><span class="sxs-lookup"><span data-stu-id="1e659-125">Prerequisites</span></span>

* <span data-ttu-id="1e659-126">[已安裝正確工具](install-the-tools.md)的 WINDOWS 10 電腦。</span><span class="sxs-lookup"><span data-stu-id="1e659-126">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="1e659-127">一些基本C#的程式設計能力。</span><span class="sxs-lookup"><span data-stu-id="1e659-127">Some basic C# programming ability.</span></span>
* <span data-ttu-id="1e659-128">您應已完成[MR 基本概念 101](holograms-101.md)。</span><span class="sxs-lookup"><span data-stu-id="1e659-128">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="1e659-129">[為開發設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="1e659-129">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="1e659-130">專案檔案</span><span class="sxs-lookup"><span data-stu-id="1e659-130">Project files</span></span>

* <span data-ttu-id="1e659-131">下載專案所需的[檔案](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip)。</span><span class="sxs-lookup"><span data-stu-id="1e659-131">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) required by the project.</span></span><span data-ttu-id="1e659-132"> 需要 Unity 2017.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="1e659-132"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="1e659-133">如果您仍然需要 Unity 5.6 支援, 請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip)。</span><span class="sxs-lookup"><span data-stu-id="1e659-133">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).</span></span>
  * <span data-ttu-id="1e659-134">如果您仍然需要 Unity 5.5 支援, 請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip)。</span><span class="sxs-lookup"><span data-stu-id="1e659-134">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).</span></span>
  * <span data-ttu-id="1e659-135">如果您仍然需要 Unity 5.4 支援, 請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip)。</span><span class="sxs-lookup"><span data-stu-id="1e659-135">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).</span></span>
* <span data-ttu-id="1e659-136">將檔案取消封存至您的桌面或其他容易到達的位置。</span><span class="sxs-lookup"><span data-stu-id="1e659-136">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="1e659-137">如果您想要在下載之前查看原始程式碼, 可以[在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping)取得。</span><span class="sxs-lookup"><span data-stu-id="1e659-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).</span></span>

### <a name="notes"></a><span data-ttu-id="1e659-138">注意</span><span class="sxs-lookup"><span data-stu-id="1e659-138">Notes</span></span>

* <span data-ttu-id="1e659-139">若要在程式碼中叫用中斷點, 請在 [工具] > [> 選項] 底下的 [啟用 Just My Code] Visual Studio 必須停用 (*未*核取)。</span><span class="sxs-lookup"><span data-stu-id="1e659-139">"Enable Just My Code" in Visual Studio needs to be disabled (*unchecked*) under Tools > Options > Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="1e659-140">Unity 設定</span><span class="sxs-lookup"><span data-stu-id="1e659-140">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* <span data-ttu-id="1e659-141">啟動**Unity**。</span><span class="sxs-lookup"><span data-stu-id="1e659-141">Start **Unity**.</span></span>
* <span data-ttu-id="1e659-142">選取 [**新增**] 以建立新的專案。</span><span class="sxs-lookup"><span data-stu-id="1e659-142">Select **New** to create a new project.</span></span>
* <span data-ttu-id="1e659-143">將專案命名為**天文館**。</span><span class="sxs-lookup"><span data-stu-id="1e659-143">Name the project **Planetarium**.</span></span>
* <span data-ttu-id="1e659-144">確認已選取**3d**設定。</span><span class="sxs-lookup"><span data-stu-id="1e659-144">Verify that the **3D** setting is selected.</span></span>
* <span data-ttu-id="1e659-145">按一下 [建立專案]。</span><span class="sxs-lookup"><span data-stu-id="1e659-145">Click **Create Project**.</span></span>
* <span data-ttu-id="1e659-146">一旦 Unity 啟動, 請移至 **編輯 > 專案設定 > Player**。</span><span class="sxs-lookup"><span data-stu-id="1e659-146">Once Unity launches, go to **Edit > Project Settings > Player**.</span></span>
* <span data-ttu-id="1e659-147">在 [偵測**器**] 面板中, 尋找並選取綠色的**Windows Store**圖示。</span><span class="sxs-lookup"><span data-stu-id="1e659-147">In the **Inspector** panel, find and select the green **Windows Store** icon.</span></span>
* <span data-ttu-id="1e659-148">展開 [**其他設定**]。</span><span class="sxs-lookup"><span data-stu-id="1e659-148">Expand **Other Settings**.</span></span>
* <span data-ttu-id="1e659-149">在轉譯區段中, 勾選 [**虛擬實境支援**] 選項。</span><span class="sxs-lookup"><span data-stu-id="1e659-149">In the **Rendering** section, check the **Virtual Reality Supported** option.</span></span>
* <span data-ttu-id="1e659-150">確認**Windows**全像是出現在**虛擬實境 sdk**清單中。</span><span class="sxs-lookup"><span data-stu-id="1e659-150">Verify that **Windows Holographic** appears in the list of **Virtual Reality SDKs**.</span></span> <span data-ttu-id="1e659-151">如果沒有，請選取 **+** 按鈕在清單底部，然後選擇**Windows 全像攝影版**。</span><span class="sxs-lookup"><span data-stu-id="1e659-151">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>
* <span data-ttu-id="1e659-152">展開 [**發行設定**]。</span><span class="sxs-lookup"><span data-stu-id="1e659-152">Expand **Publishing Settings**.</span></span>
* <span data-ttu-id="1e659-153">在 [**功能**] 區段中, 檢查下列設定:</span><span class="sxs-lookup"><span data-stu-id="1e659-153">In the **Capabilities** section, check the following settings:</span></span>
    * <span data-ttu-id="1e659-154">InternetClientServer</span><span class="sxs-lookup"><span data-stu-id="1e659-154">InternetClientServer</span></span>
    * <span data-ttu-id="1e659-155">PrivateNetworkClientServer</span><span class="sxs-lookup"><span data-stu-id="1e659-155">PrivateNetworkClientServer</span></span>
    * <span data-ttu-id="1e659-156">麥克風</span><span class="sxs-lookup"><span data-stu-id="1e659-156">Microphone</span></span>
    * <span data-ttu-id="1e659-157">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="1e659-157">SpatialPerception</span></span>
* <span data-ttu-id="1e659-158">移至 [**編輯] > 專案設定 > 品質**</span><span class="sxs-lookup"><span data-stu-id="1e659-158">Go to **Edit > Project Settings > Quality**</span></span>
* <span data-ttu-id="1e659-159">在 [偵測**器**] 面板的 [Windows Store] 圖示下, 選取 [預設] 列底下的黑色下拉箭號, 並將預設值變更為 [**非常低**]。</span><span class="sxs-lookup"><span data-stu-id="1e659-159">In the **Inspector** panel, under the Windows Store icon, select the black drop-down arrow under the 'Default' row and change the default setting to **Very Low**.</span></span>
* <span data-ttu-id="1e659-160">移至 資產 > 匯**入套件 > 自訂套件**。</span><span class="sxs-lookup"><span data-stu-id="1e659-160">Go to **Assets > Import Package > Custom Package**.</span></span>
* <span data-ttu-id="1e659-161">流覽至 **..\holographicacademy-holograms-230-SpatialMapping\Starting**資料夾。</span><span class="sxs-lookup"><span data-stu-id="1e659-161">Navigate to the **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** folder.</span></span>
* <span data-ttu-id="1e659-162">按一下 [**天文館 unitypackage**]。</span><span class="sxs-lookup"><span data-stu-id="1e659-162">Click on **Planetarium.unitypackage**.</span></span>
* <span data-ttu-id="1e659-163">按一下 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="1e659-163">Click **Open**.</span></span>
* <span data-ttu-id="1e659-164">[匯**入 Unity 封裝**] 視窗應該會出現, 請按一下 [匯**入**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1e659-164">An **Import Unity Package** window should appear, click on the **Import** button.</span></span>
* <span data-ttu-id="1e659-165">等候 Unity 匯入完成此專案所需的所有資產。</span><span class="sxs-lookup"><span data-stu-id="1e659-165">Wait for Unity to import all of the assets that we will need to complete this project.</span></span>
* <span data-ttu-id="1e659-166">在 [階層] 面板中, 刪除**主要相機**。</span><span class="sxs-lookup"><span data-stu-id="1e659-166">In the **Hierarchy** panel, delete the **Main Camera**.</span></span>
* <span data-ttu-id="1e659-167">在 [**專案**] 面板的 [ **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** ] 資料夾中, 尋找**主要相機**物件。</span><span class="sxs-lookup"><span data-stu-id="1e659-167">In the **Project** panel, **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** folder, find the **Main Camera** object.</span></span>
* <span data-ttu-id="1e659-168">將**主要相機**prefab 拖放到 [階層 ] 面板中。</span><span class="sxs-lookup"><span data-stu-id="1e659-168">Drag and drop the **Main Camera** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="1e659-169">在 [階層] 面板中, 刪除**方向光源**物件。</span><span class="sxs-lookup"><span data-stu-id="1e659-169">In the **Hierarchy** panel, delete the **Directional Light** object.</span></span>
* <span data-ttu-id="1e659-170">在 [**專案**] 面板的 [**全息影像**] 資料夾中, 找出**游標**物件。</span><span class="sxs-lookup"><span data-stu-id="1e659-170">In the **Project** panel, **Holograms** folder, locate the **Cursor** object.</span></span>
* <span data-ttu-id="1e659-171">拖曳 & 將**游標**prefab 放在階層中。</span><span class="sxs-lookup"><span data-stu-id="1e659-171">Drag & drop the **Cursor** prefab into the **Hierarchy**.</span></span>
* <span data-ttu-id="1e659-172">在 [階層] 面板中, 選取**游標**物件。</span><span class="sxs-lookup"><span data-stu-id="1e659-172">In the **Hierarchy** panel, select the **Cursor** object.</span></span>
* <span data-ttu-id="1e659-173">在 [偵測**器**] 面板中, 按一下 [**圖層**] 下拉式選, 然後選取 [**編輯圖層**]。</span><span class="sxs-lookup"><span data-stu-id="1e659-173">In the **Inspector** panel, click the **Layer** drop-down and select **Edit Layers...**.</span></span>
* <span data-ttu-id="1e659-174">將**使用者第31層**命名為 "**SpatialMapping**"。</span><span class="sxs-lookup"><span data-stu-id="1e659-174">Name **User Layer 31** as "**SpatialMapping**".</span></span>
* <span data-ttu-id="1e659-175">儲存新場景:**檔案 > 另存場景 .。。**</span><span class="sxs-lookup"><span data-stu-id="1e659-175">Save the new scene: **File > Save Scene As...**</span></span>
* <span data-ttu-id="1e659-176">按一下 [**新增資料夾**], 並將資料夾命名為**場景**。</span><span class="sxs-lookup"><span data-stu-id="1e659-176">Click **New Folder** and name the folder **Scenes**.</span></span>
* <span data-ttu-id="1e659-177">將檔案命名為 "**天文館**", 並將它儲存在 [**幕後**] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="1e659-177">Name the file "**Planetarium**" and save it in the **Scenes** folder.</span></span>

## <a name="chapter-1---scanning"></a><span data-ttu-id="1e659-178">第1章-掃描</span><span class="sxs-lookup"><span data-stu-id="1e659-178">Chapter 1 - Scanning</span></span>

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

<span data-ttu-id="1e659-179">**目標**</span><span class="sxs-lookup"><span data-stu-id="1e659-179">**Objectives**</span></span>
* <span data-ttu-id="1e659-180">瞭解 SurfaceObserver, 以及其設定對體驗和效能有何影響。</span><span class="sxs-lookup"><span data-stu-id="1e659-180">Learn about the SurfaceObserver and how its settings impact experience and performance.</span></span>
* <span data-ttu-id="1e659-181">建立房間掃描體驗, 以收集您房間的網格。</span><span class="sxs-lookup"><span data-stu-id="1e659-181">Create a room scanning experience to collect the meshes of your room.</span></span>

<span data-ttu-id="1e659-182">**螢幕**</span><span class="sxs-lookup"><span data-stu-id="1e659-182">**Instructions**</span></span>
* <span data-ttu-id="1e659-183">在 [**專案**] 面板的 [ **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** ] 資料夾中, 尋找 [ **SpatialMapping** ] prefab。</span><span class="sxs-lookup"><span data-stu-id="1e659-183">In the **Project** panel **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** folder, find the **SpatialMapping** prefab.</span></span>
* <span data-ttu-id="1e659-184">拖曳 & 將**SpatialMapping** prefab 拖放到 [階層] 面板中。</span><span class="sxs-lookup"><span data-stu-id="1e659-184">Drag & drop the **SpatialMapping** prefab into the **Hierarchy** panel.</span></span>

<span data-ttu-id="1e659-185">**組建和部署 (第1部分)**</span><span class="sxs-lookup"><span data-stu-id="1e659-185">**Build and Deploy (part 1)**</span></span>
* <span data-ttu-id="1e659-186">在 Unity 中, 選取 [檔案] **> [組建設定**]。</span><span class="sxs-lookup"><span data-stu-id="1e659-186">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="1e659-187">按一下 [新增] [**開啟場景**], 將**天文館**場景新增至組建。</span><span class="sxs-lookup"><span data-stu-id="1e659-187">Click **Add Open Scenes** to add the **Planetarium** scene to the build.</span></span>
* <span data-ttu-id="1e659-188">在 [**平臺**] 清單中選取**通用 Windows 平臺**, 然後按一下 [**切換平臺**]。</span><span class="sxs-lookup"><span data-stu-id="1e659-188">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="1e659-189">將 [ **SDK**至**通用 10**和**UWP 組建類型**] 設定為 [ **D3D**]。</span><span class="sxs-lookup"><span data-stu-id="1e659-189">Set **SDK** to **Universal 10** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="1e659-190">檢查**Unity C#專案**。</span><span class="sxs-lookup"><span data-stu-id="1e659-190">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="1e659-191">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="1e659-191">Click **Build**.</span></span>
* <span data-ttu-id="1e659-192">建立名為 "App" 的**新資料夾**。</span><span class="sxs-lookup"><span data-stu-id="1e659-192">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="1e659-193">按一下 [**應用程式**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="1e659-193">Single click the **App** folder.</span></span>
* <span data-ttu-id="1e659-194">按 [**選取資料夾**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1e659-194">Press the **Select Folder** button.</span></span>
* <span data-ttu-id="1e659-195">Unity 完成建立時, 將會出現 [檔案瀏覽器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="1e659-195">When Unity is done building, a File Explorer window will appear.</span></span>
* <span data-ttu-id="1e659-196">按兩下 [**應用程式**] 資料夾以開啟它。</span><span class="sxs-lookup"><span data-stu-id="1e659-196">Double-click on the **App** folder to open it.</span></span>
* <span data-ttu-id="1e659-197">按兩下 [**天文館**], 在 Visual Studio 中載入專案。</span><span class="sxs-lookup"><span data-stu-id="1e659-197">Double-click on **Planetarium.sln** to load the project in Visual Studio.</span></span>
* <span data-ttu-id="1e659-198">在 Visual Studio 中, 使用頂端工具列將設定變更為 [**發行**]。</span><span class="sxs-lookup"><span data-stu-id="1e659-198">In Visual Studio, use the top toolbar to change the Configuration to **Release**.</span></span>
* <span data-ttu-id="1e659-199">將平臺變更為**x86**。</span><span class="sxs-lookup"><span data-stu-id="1e659-199">Change the Platform to **x86**.</span></span>
* <span data-ttu-id="1e659-200">按一下 [本機電腦] 右邊的下拉箭號, 然後選取 [**遠端電腦**]。</span><span class="sxs-lookup"><span data-stu-id="1e659-200">Click on the drop-down arrow to the right of 'Local Machine', and select **Remote Machine**.</span></span>
* <span data-ttu-id="1e659-201">在 [位址] 欄位中輸入[您裝置的 IP 位址](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network), 並將驗證模式變更為 **[通用 (未加密的通訊協定)** ]。</span><span class="sxs-lookup"><span data-stu-id="1e659-201">Enter [your device's IP address](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) in the Address field and change Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span>
* <span data-ttu-id="1e659-202">按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="1e659-202">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="1e659-203">監看 [**輸出**] 面板中的 [組建和部署狀態] Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="1e659-203">Watch the **Output** panel in Visual Studio for build and deploy status.</span></span>
* <span data-ttu-id="1e659-204">一旦您的應用程式部署完成, 請在聊天室前後移動。</span><span class="sxs-lookup"><span data-stu-id="1e659-204">Once your app has deployed, walk around the room.</span></span> <span data-ttu-id="1e659-205">您會看到黑色和白色線框網格所涵蓋的周圍表面。</span><span class="sxs-lookup"><span data-stu-id="1e659-205">You will see the surrounding surfaces covered by black and white wireframe meshes.</span></span>
* <span data-ttu-id="1e659-206">掃描您的環境。</span><span class="sxs-lookup"><span data-stu-id="1e659-206">Scan your surroundings.</span></span> <span data-ttu-id="1e659-207">請務必查看 [牆]、[上限] 和 [樓層]。</span><span class="sxs-lookup"><span data-stu-id="1e659-207">Be sure to look at walls, ceilings, and floors.</span></span>

<span data-ttu-id="1e659-208">**組建和部署 (第2部分)**</span><span class="sxs-lookup"><span data-stu-id="1e659-208">**Build and Deploy (part 2)**</span></span>

<span data-ttu-id="1e659-209">現在讓我們來探索空間對應會如何影響效能。</span><span class="sxs-lookup"><span data-stu-id="1e659-209">Now let's explore how Spatial Mapping can affect performance.</span></span>
* <span data-ttu-id="1e659-210">在 Unity 中, 選取 [ **Window > Profiler]** 。</span><span class="sxs-lookup"><span data-stu-id="1e659-210">In Unity, select **Window > Profiler**.</span></span>
* <span data-ttu-id="1e659-211">按一下 [**新增 Profiler] > GPU**。</span><span class="sxs-lookup"><span data-stu-id="1e659-211">Click **Add Profiler > GPU**.</span></span>
* <span data-ttu-id="1e659-212">按一下 [ **Active Profiler <Enter IP>] >** 。</span><span class="sxs-lookup"><span data-stu-id="1e659-212">Click **Active Profiler > <Enter IP>**.</span></span>
* <span data-ttu-id="1e659-213">輸入 HoloLens 的**IP 位址**。</span><span class="sxs-lookup"><span data-stu-id="1e659-213">Enter the **IP address** of your HoloLens.</span></span>
* <span data-ttu-id="1e659-214">按一下 **[連接]** 。</span><span class="sxs-lookup"><span data-stu-id="1e659-214">Click **Connect**.</span></span>
* <span data-ttu-id="1e659-215">觀察 GPU 呈現畫面格所需的毫秒數。</span><span class="sxs-lookup"><span data-stu-id="1e659-215">Observe the number of milliseconds it takes for the GPU to render a frame.</span></span>
* <span data-ttu-id="1e659-216">停止應用程式, 使其無法在裝置上執行。</span><span class="sxs-lookup"><span data-stu-id="1e659-216">Stop the application from running on the device.</span></span>
* <span data-ttu-id="1e659-217">返回 Visual Studio 並開啟**SpatialMappingObserver.cs**。</span><span class="sxs-lookup"><span data-stu-id="1e659-217">Return to Visual Studio and open **SpatialMappingObserver.cs**.</span></span> <span data-ttu-id="1e659-218">您會在 [Assembly-CSharp (通用 Windows)] 專案的 [HoloToolkit\SpatialMapping] 資料夾中找到它。</span><span class="sxs-lookup"><span data-stu-id="1e659-218">You will find it in the HoloToolkit\SpatialMapping folder of the Assembly-CSharp (Universal Windows) project.</span></span>
* <span data-ttu-id="1e659-219">尋找**喚醒 ()** 函式, 並新增下列程式程式碼:**TrianglesPerCubicMeter = 1200;**</span><span class="sxs-lookup"><span data-stu-id="1e659-219">Find the **Awake()** function, and add the following line of code: **TrianglesPerCubicMeter = 1200;**</span></span>
* <span data-ttu-id="1e659-220">將專案重新部署到您的裝置, 然後**重新連接**分析工具。</span><span class="sxs-lookup"><span data-stu-id="1e659-220">Re-deploy the project to your device, and then **reconnect the profiler**.</span></span> <span data-ttu-id="1e659-221">觀察呈現框架的毫秒數變更。</span><span class="sxs-lookup"><span data-stu-id="1e659-221">Observe the change in the number of milliseconds to render a frame.</span></span>
* <span data-ttu-id="1e659-222">停止應用程式, 使其無法在裝置上執行。</span><span class="sxs-lookup"><span data-stu-id="1e659-222">Stop the application from running on the device.</span></span>

<span data-ttu-id="1e659-223">**在 Unity 中儲存和載入**</span><span class="sxs-lookup"><span data-stu-id="1e659-223">**Save and load in Unity**</span></span>

<span data-ttu-id="1e659-224">最後, 讓我們來儲存房間網格, 並將其載入 Unity。</span><span class="sxs-lookup"><span data-stu-id="1e659-224">Finally, let's save our room mesh and load it into Unity.</span></span>
* <span data-ttu-id="1e659-225">返回 Visual Studio, 並移除您在上一節中于**喚醒 ()** 函數中新增的**TrianglesPerCubicMeter**行。</span><span class="sxs-lookup"><span data-stu-id="1e659-225">Return to Visual Studio and remove the **TrianglesPerCubicMeter** line that you added in the **Awake()** function during the previous section.</span></span>
* <span data-ttu-id="1e659-226">將專案重新部署到您的裝置。</span><span class="sxs-lookup"><span data-stu-id="1e659-226">Redeploy the project to your device.</span></span> <span data-ttu-id="1e659-227">我們現在應該以每個立方計量的**500**三角形來執行。</span><span class="sxs-lookup"><span data-stu-id="1e659-227">We should now be running with **500** triangles per cubic meter.</span></span>
* <span data-ttu-id="1e659-228">開啟瀏覽器並輸入 HoloLens IPAddress, 以流覽至**Windows 裝置入口網站**。</span><span class="sxs-lookup"><span data-stu-id="1e659-228">Open a browser and enter in your HoloLens IPAddress to navigate to the **Windows Device Portal**.</span></span>
* <span data-ttu-id="1e659-229">選取左面板中的 [ **3D 視圖**] 選項。</span><span class="sxs-lookup"><span data-stu-id="1e659-229">Select the **3D View** option in the left panel.</span></span>
* <span data-ttu-id="1e659-230">在 [**表面重建**] 底下, 選取 [**更新**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1e659-230">Under **Surface reconstruction** select the **Update** button.</span></span>
* <span data-ttu-id="1e659-231">監看您在 HoloLens 上掃描的區域會顯示在 [顯示] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="1e659-231">Watch as the areas that you have scanned on your HoloLens appear in the display window.</span></span>
* <span data-ttu-id="1e659-232">若要儲存您的房間掃描, 請按 [**儲存**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1e659-232">To save your room scan, press the **Save** button.</span></span>
* <span data-ttu-id="1e659-233">開啟您的 [**下載**] 資料夾, 尋找儲存的房間模型**SRMesh。**</span><span class="sxs-lookup"><span data-stu-id="1e659-233">Open your **Downloads** folder to find the saved room model **SRMesh.obj**.</span></span>
* <span data-ttu-id="1e659-234">將**SRMesh**複製到 Unity 專案的 [**資產**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="1e659-234">Copy **SRMesh.obj** to the **Assets** folder of your Unity project.</span></span>
* <span data-ttu-id="1e659-235">在 Unity 中, 選取 [階層] 面板中的 [ **SpatialMapping** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="1e659-235">In Unity, select the **SpatialMapping** object in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="1e659-236">找出 [**物件介面觀察器 (腳本)** ] 元件。</span><span class="sxs-lookup"><span data-stu-id="1e659-236">Locate the **Object Surface Observer (Script)** component.</span></span>
* <span data-ttu-id="1e659-237">按一下 [**房間模型**] 屬性右邊的圓形。</span><span class="sxs-lookup"><span data-stu-id="1e659-237">Click the circle to the right of the **Room Model** property.</span></span>
* <span data-ttu-id="1e659-238">尋找並選取 [ **SRMesh** ] 物件, 然後關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="1e659-238">Find and select the **SRMesh** object and then close the window.</span></span>
* <span data-ttu-id="1e659-239">確認 [偵測**器**] 面板中的 [**房間模型**] 屬性現在已設定為 [ **SRMesh**]。</span><span class="sxs-lookup"><span data-stu-id="1e659-239">Verify that the **Room Model** property in the **Inspector** panel is now set to **SRMesh**.</span></span>
* <span data-ttu-id="1e659-240">按下 [**播放**] 按鈕以輸入 Unity 的預覽模式。</span><span class="sxs-lookup"><span data-stu-id="1e659-240">Press the **Play** button to enter Unity's preview mode.</span></span>
* <span data-ttu-id="1e659-241">SpatialMapping 元件會從已儲存的房間模型載入網格, 讓您可以在 Unity 中使用它們。</span><span class="sxs-lookup"><span data-stu-id="1e659-241">The SpatialMapping component will load the meshes from the saved room model so you can use them in Unity.</span></span>
* <span data-ttu-id="1e659-242">切換至**場景**視圖, 查看所有使用線框著色器所顯示的房間模型。</span><span class="sxs-lookup"><span data-stu-id="1e659-242">Switch to **Scene** view to see all of your room model displayed with the wireframe shader.</span></span>
* <span data-ttu-id="1e659-243">再按一次 [**播放**] 按鈕, 結束預覽模式。</span><span class="sxs-lookup"><span data-stu-id="1e659-243">Press the **Play** button again to exit preview mode.</span></span>

<span data-ttu-id="1e659-244">**注意：** 下次當您在 Unity 中輸入預覽模式時, 預設會載入儲存的房間網格。</span><span class="sxs-lookup"><span data-stu-id="1e659-244">**NOTE:** The next time that you enter preview mode in Unity, it will load the saved room mesh by default.</span></span>

## <a name="chapter-2---visualization"></a><span data-ttu-id="1e659-245">第2章-視覺效果</span><span class="sxs-lookup"><span data-stu-id="1e659-245">Chapter 2 - Visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

<span data-ttu-id="1e659-246">**目標**</span><span class="sxs-lookup"><span data-stu-id="1e659-246">**Objectives**</span></span>
* <span data-ttu-id="1e659-247">瞭解著色器的基本概念。</span><span class="sxs-lookup"><span data-stu-id="1e659-247">Learn the basics of shaders.</span></span>
* <span data-ttu-id="1e659-248">視覺化您的環境。</span><span class="sxs-lookup"><span data-stu-id="1e659-248">Visualize your surroundings.</span></span>

<span data-ttu-id="1e659-249">**螢幕**</span><span class="sxs-lookup"><span data-stu-id="1e659-249">**Instructions**</span></span>
* <span data-ttu-id="1e659-250">在 Unity 的 [階層] 面板中, 選取 [ **SpatialMapping** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="1e659-250">In Unity's **Hierarchy** panel, select the **SpatialMapping** object.</span></span>
* <span data-ttu-id="1e659-251">在 [偵測**器**] 面板中, 尋找 [**空間對應管理員 (腳本)** ] 元件。</span><span class="sxs-lookup"><span data-stu-id="1e659-251">In the **Inspector** panel, find the **Spatial Mapping Manager (Script)** component.</span></span>
* <span data-ttu-id="1e659-252">按一下 [**表面材質**] 屬性右邊的圓形。</span><span class="sxs-lookup"><span data-stu-id="1e659-252">Click the circle to the right of the **Surface Material** property.</span></span>
* <span data-ttu-id="1e659-253">尋找並選取 [ **BlueLinesOnWalls** ] 材質, 然後關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="1e659-253">Find and select the **BlueLinesOnWalls** material and close the window.</span></span>
* <span data-ttu-id="1e659-254">在 [**專案**面板**著色**器] 資料夾中, 按兩下 [ **BlueLinesOnWalls** ] 以在 Visual Studio 中開啟著色器。</span><span class="sxs-lookup"><span data-stu-id="1e659-254">In the **Project** panel **Shaders** folder, double-click on **BlueLinesOnWalls** to open the shader in Visual Studio.</span></span>
* <span data-ttu-id="1e659-255">這是簡單的圖元 (頂點到片段) 著色器, 可完成下列工作:</span><span class="sxs-lookup"><span data-stu-id="1e659-255">This is a simple pixel (vertex to fragment) shader, which accomplishes the following tasks:</span></span>
    1. <span data-ttu-id="1e659-256">將頂點的位置轉換成世界空間。</span><span class="sxs-lookup"><span data-stu-id="1e659-256">Converts a vertex's location to world space.</span></span>
    2. <span data-ttu-id="1e659-257">檢查頂點的法線, 以判斷圖元是否為垂直。</span><span class="sxs-lookup"><span data-stu-id="1e659-257">Checks the vertex's normal to determine if a pixel is vertical.</span></span>
    3. <span data-ttu-id="1e659-258">設定要呈現的圖元色彩。</span><span class="sxs-lookup"><span data-stu-id="1e659-258">Sets the color of the pixel for rendering.</span></span>

<span data-ttu-id="1e659-259">**組建和部署**</span><span class="sxs-lookup"><span data-stu-id="1e659-259">**Build and Deploy**</span></span>
* <span data-ttu-id="1e659-260">返回 Unity, 然後按下 [**播放**] 進入預覽模式。</span><span class="sxs-lookup"><span data-stu-id="1e659-260">Return to Unity and press **Play** to enter preview mode.</span></span>
* <span data-ttu-id="1e659-261">會在房間網格的所有垂直表面上轉譯藍線 (這會自動從我們儲存的掃描資料載入)。</span><span class="sxs-lookup"><span data-stu-id="1e659-261">Blue lines will be rendered on all vertical surfaces of the room mesh (which automatically loaded from our saved scanning data).</span></span>
* <span data-ttu-id="1e659-262">切換至 [**場景**] 索引標籤, 以調整房間的外觀, 並查看整個房間網格在 Unity 中的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="1e659-262">Switch to the **Scene** tab to adjust your view of the room and see how the entire room mesh appears in Unity.</span></span>
* <span data-ttu-id="1e659-263">在 [**專案**] 面板中, 尋找 [**材質**] 資料夾, 然後選取 [ **BlueLinesOnWalls** ] 資料。</span><span class="sxs-lookup"><span data-stu-id="1e659-263">In the **Project** panel, find the **Materials** folder and select the **BlueLinesOnWalls** material.</span></span>
* <span data-ttu-id="1e659-264">修改某些屬性, 並查看這些變更在 Unity 編輯器中的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="1e659-264">Modify some properties and see how the changes appear in the Unity editor.</span></span>
    * <span data-ttu-id="1e659-265">在 [偵測**器**] 面板中, 調整 [ **LineScale** ] 值, 使線條顯示較粗或更小。</span><span class="sxs-lookup"><span data-stu-id="1e659-265">In the **Inspector** panel, adjust the **LineScale** value to make the lines appear thicker or thinner.</span></span>
    * <span data-ttu-id="1e659-266">在 [偵測**器**] 面板中, 調整 [ **LinesPerMeter** ] 值, 以變更每個牆上出現的行數。</span><span class="sxs-lookup"><span data-stu-id="1e659-266">In the **Inspector** panel, adjust the **LinesPerMeter** value to change how many lines appear on each wall.</span></span>
* <span data-ttu-id="1e659-267">按一下 [**播放**] 以結束預覽模式。</span><span class="sxs-lookup"><span data-stu-id="1e659-267">Click **Play** again to exit preview mode.</span></span>
* <span data-ttu-id="1e659-268">建立並部署至 HoloLens, 並觀察著色器呈現如何顯示在實際表面上。</span><span class="sxs-lookup"><span data-stu-id="1e659-268">Build and deploy to the HoloLens and observe how the shader rendering appears on real surfaces.</span></span>

<span data-ttu-id="1e659-269">Unity 的確是預覽材質的絕佳作業, 但是在裝置中簽出轉譯是個不錯的主意。</span><span class="sxs-lookup"><span data-stu-id="1e659-269">Unity does a great job of previewing materials, but it's always a good idea to check-out rendering in the device.</span></span>

## <a name="chapter-3---processing"></a><span data-ttu-id="1e659-270">第3章-處理</span><span class="sxs-lookup"><span data-stu-id="1e659-270">Chapter 3 - Processing</span></span>

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

<span data-ttu-id="1e659-271">**目標**</span><span class="sxs-lookup"><span data-stu-id="1e659-271">**Objectives**</span></span>
* <span data-ttu-id="1e659-272">瞭解處理空間對應資料以在應用程式中使用的技術。</span><span class="sxs-lookup"><span data-stu-id="1e659-272">Learn techniques to process spatial mapping data for use in your application.</span></span>
* <span data-ttu-id="1e659-273">分析空間對應資料以尋找飛機並移除三角形。</span><span class="sxs-lookup"><span data-stu-id="1e659-273">Analyze spatial mapping data to find planes and remove triangles.</span></span>
* <span data-ttu-id="1e659-274">使用平面來放置全息影像。</span><span class="sxs-lookup"><span data-stu-id="1e659-274">Use planes for hologram placement.</span></span>

<span data-ttu-id="1e659-275">**螢幕**</span><span class="sxs-lookup"><span data-stu-id="1e659-275">**Instructions**</span></span>
* <span data-ttu-id="1e659-276">在 Unity 的 [**專案**] 面板中, [**全息影像**] 資料夾, 尋找**SpatialProcessing**物件。</span><span class="sxs-lookup"><span data-stu-id="1e659-276">In Unity's **Project** panel, **Holograms** folder, find the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="1e659-277">拖曳 & 將**SpatialProcessing**物件拖放到 [階層] 面板中。</span><span class="sxs-lookup"><span data-stu-id="1e659-277">Drag & drop the **SpatialProcessing** object into the **Hierarchy** panel.</span></span>

<span data-ttu-id="1e659-278">SpatialProcessing prefab 包含用來處理空間對應資料的元件。</span><span class="sxs-lookup"><span data-stu-id="1e659-278">The SpatialProcessing prefab includes components for processing the spatial mapping data.</span></span> <span data-ttu-id="1e659-279">**SurfaceMeshesToPlanes.cs**會根據空間對應資料來尋找並產生平面。</span><span class="sxs-lookup"><span data-stu-id="1e659-279">**SurfaceMeshesToPlanes.cs** will find and generate planes based on the spatial mapping data.</span></span> <span data-ttu-id="1e659-280">我們會在應用程式中使用平面來代表牆、樓層和上限。</span><span class="sxs-lookup"><span data-stu-id="1e659-280">We will use planes in our application to represent walls, floors and ceilings.</span></span> <span data-ttu-id="1e659-281">此 prefab 也包含可從空間對應網格中移除頂點的**RemoveSurfaceVertices.cs** 。</span><span class="sxs-lookup"><span data-stu-id="1e659-281">This prefab also includes **RemoveSurfaceVertices.cs** which can remove vertices from the spatial mapping mesh.</span></span> <span data-ttu-id="1e659-282">這可用來在網格中建立孔, 或移除不再需要的多餘三角形 (因為可以改用平面)。</span><span class="sxs-lookup"><span data-stu-id="1e659-282">This can be used to create holes in the mesh, or to remove excess triangles that are no longer needed (because planes can be used instead).</span></span>
* <span data-ttu-id="1e659-283">在 Unity 的 [**專案**] 面板中, [**全息影像**] 資料夾, 尋找**SpaceCollection**物件。</span><span class="sxs-lookup"><span data-stu-id="1e659-283">In Unity's **Project** panel, **Holograms** folder, find the **SpaceCollection** object.</span></span>
* <span data-ttu-id="1e659-284">將**SpaceCollection**物件拖放到 [階層 ] 面板中。</span><span class="sxs-lookup"><span data-stu-id="1e659-284">Drag and drop the **SpaceCollection** object into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="1e659-285">在 [階層] 面板中, 選取 [ **SpatialProcessing** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="1e659-285">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="1e659-286">在 [偵測**器**] 面板中, 尋找 [**播放空間管理員 (腳本)** ] 元件。</span><span class="sxs-lookup"><span data-stu-id="1e659-286">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="1e659-287">按兩下 [ **PlaySpaceManager.cs** ], 在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="1e659-287">Double-click on **PlaySpaceManager.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="1e659-288">PlaySpaceManager.cs 包含應用程式特定的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1e659-288">PlaySpaceManager.cs contains application-specific code.</span></span> <span data-ttu-id="1e659-289">我們會在此腳本中新增功能, 以啟用下列行為:</span><span class="sxs-lookup"><span data-stu-id="1e659-289">We will add functionality to this script to enable the following behavior:</span></span>
1. <span data-ttu-id="1e659-290">超過掃描時間限制之後, 停止收集空間對應資料 (10 秒)。</span><span class="sxs-lookup"><span data-stu-id="1e659-290">Stop collecting spatial mapping data after we exceed the scanning time limit (10 seconds).</span></span>
2. <span data-ttu-id="1e659-291">處理空間對應資料:</span><span class="sxs-lookup"><span data-stu-id="1e659-291">Process the spatial mapping data:</span></span>
    1. <span data-ttu-id="1e659-292">使用 SurfaceMeshesToPlanes 建立更簡單的世界表示, 做為平面 (牆、樓層、上限等)。</span><span class="sxs-lookup"><span data-stu-id="1e659-292">Use SurfaceMeshesToPlanes to create a simpler representation of the world as planes (walls, floors, ceilings, etc).</span></span>
    2. <span data-ttu-id="1e659-293">使用 RemoveSurfaceVertices 來移除落在平面邊界內的曲面三角形。</span><span class="sxs-lookup"><span data-stu-id="1e659-293">Use RemoveSurfaceVertices to remove surface triangles that fall within plane boundaries.</span></span>
3. <span data-ttu-id="1e659-294">在世界各地產生一組全息影像, 並將它們放在靠近使用者的牆和地面平面上。</span><span class="sxs-lookup"><span data-stu-id="1e659-294">Generate a collection of holograms in the world and place them on wall and floor planes near the user.</span></span>

<span data-ttu-id="1e659-295">完成標記在 PlaySpaceManager.cs 中的編碼練習, 或將腳本取代為下列的已完成解決方案:</span><span class="sxs-lookup"><span data-stu-id="1e659-295">Complete the coding exercises marked in PlaySpaceManager.cs, or replace the script with the finished solution from below:</span></span>

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

<span data-ttu-id="1e659-296">**組建和部署**</span><span class="sxs-lookup"><span data-stu-id="1e659-296">**Build and Deploy**</span></span>
* <span data-ttu-id="1e659-297">在部署至 HoloLens 之前, 請按 Unity 中的 [**播放**] 按鈕進入播放模式。</span><span class="sxs-lookup"><span data-stu-id="1e659-297">Before deploying to the HoloLens, press the **Play** button in Unity to enter play mode.</span></span>
* <span data-ttu-id="1e659-298">從檔案載入房間網格之後, 在空間對應網格上開始處理之前, 請等候10秒。</span><span class="sxs-lookup"><span data-stu-id="1e659-298">After the room mesh is loaded from file, wait for 10 seconds before processing starts on the spatial mapping mesh.</span></span>
* <span data-ttu-id="1e659-299">當處理完成時, 會顯示平面來代表樓層、牆、上限等等。</span><span class="sxs-lookup"><span data-stu-id="1e659-299">When processing is complete, planes will appear to represent the floor, walls, ceiling, etc.</span></span>
* <span data-ttu-id="1e659-300">找到所有的平面之後, 您應該會看到日光系統出現在相機附近的地面桌子上。</span><span class="sxs-lookup"><span data-stu-id="1e659-300">After all of the planes have been found, you should see a solar system appear on a table of floor near the camera.</span></span>
* <span data-ttu-id="1e659-301">兩個海報也應該會出現在相機附近的牆上。</span><span class="sxs-lookup"><span data-stu-id="1e659-301">Two posters should appear on walls near the camera too.</span></span> <span data-ttu-id="1e659-302">如果您無法在**遊戲**模式中看到, 請切換到 [**場景**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1e659-302">Switch to the **Scene** tab if you cannot see them in **Game** mode.</span></span>
* <span data-ttu-id="1e659-303">再按一次 [**播放**] 按鈕, 結束播放模式。</span><span class="sxs-lookup"><span data-stu-id="1e659-303">Press the **Play** button again to exit play mode.</span></span>
* <span data-ttu-id="1e659-304">如往常般建立並部署至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="1e659-304">Build and deploy to the HoloLens, as usual.</span></span>
* <span data-ttu-id="1e659-305">等候空間對應資料的掃描和處理完成。</span><span class="sxs-lookup"><span data-stu-id="1e659-305">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="1e659-306">一旦您看到飛機, 請嘗試尋找您世界中的日光系統和海報。</span><span class="sxs-lookup"><span data-stu-id="1e659-306">Once you see planes, try to find the solar system and posters in your world.</span></span>

## <a name="chapter-4---placement"></a><span data-ttu-id="1e659-307">第4章-放置</span><span class="sxs-lookup"><span data-stu-id="1e659-307">Chapter 4 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

<span data-ttu-id="1e659-308">**目標**</span><span class="sxs-lookup"><span data-stu-id="1e659-308">**Objectives**</span></span>
* <span data-ttu-id="1e659-309">判斷是否要在表面上容納全像投影。</span><span class="sxs-lookup"><span data-stu-id="1e659-309">Determine if a hologram will fit on a surface.</span></span>
* <span data-ttu-id="1e659-310">當全息影像可以/無法放在表面上時, 為使用者提供意見反應。</span><span class="sxs-lookup"><span data-stu-id="1e659-310">Provide feedback to the user when a hologram can/cannot fit on a surface.</span></span>

<span data-ttu-id="1e659-311">**螢幕**</span><span class="sxs-lookup"><span data-stu-id="1e659-311">**Instructions**</span></span>
* <span data-ttu-id="1e659-312">在 Unity 的 [階層] 面板中, 選取 [ **SpatialProcessing** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="1e659-312">In Unity's **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="1e659-313">在 [偵測**器**] 面板中, 尋找**Surface 網格到平面 (腳本)** 元件。</span><span class="sxs-lookup"><span data-stu-id="1e659-313">In the **Inspector** panel, find the **Surface Meshes To Planes (Script)** component.</span></span>
* <span data-ttu-id="1e659-314">將 [**繪製平面**] 屬性變更為 [**無**], 以清除選取專案。</span><span class="sxs-lookup"><span data-stu-id="1e659-314">Change the **Draw Planes** property to **Nothing** to clear the selection.</span></span>
* <span data-ttu-id="1e659-315">將 [**繪製平面**] 屬性變更為 [**牆**], 如此就只會呈現牆飛機。</span><span class="sxs-lookup"><span data-stu-id="1e659-315">Change the **Draw Planes** property to **Wall**, so that only wall planes will be rendered.</span></span>
* <span data-ttu-id="1e659-316">在 [**專案**] 面板的 [**腳本**] 資料夾中, 按兩下 [ **Placeable.cs** ] 以在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="1e659-316">In the **Project** panel, **Scripts** folder, double-click on **Placeable.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="1e659-317">可**放置**的腳本已附加至在完成平面尋找之後所建立的海報和投影方塊。</span><span class="sxs-lookup"><span data-stu-id="1e659-317">The **Placeable** script is already attached to the posters and projection box that are created after plane finding completes.</span></span> <span data-ttu-id="1e659-318">我們只需要取消批註一些程式碼, 這個腳本就會達到下列目的:</span><span class="sxs-lookup"><span data-stu-id="1e659-318">All we need to do is uncomment some code, and this script will achieve the following:</span></span>
1. <span data-ttu-id="1e659-319">藉由從周框 cube 的中央和四個角落 raycasting, 判斷全像投影是否適合表面。</span><span class="sxs-lookup"><span data-stu-id="1e659-319">Determine if a hologram will fit on a surface by raycasting from the center and four corners of the bounding cube.</span></span>
2. <span data-ttu-id="1e659-320">請檢查表面法線, 判斷它是否夠平滑, 以讓全息圖形坐在上齊。</span><span class="sxs-lookup"><span data-stu-id="1e659-320">Check the surface normal to determine if it is smooth enough for the hologram to sit flush on.</span></span>
3. <span data-ttu-id="1e659-321">在全像投影上轉譯周框 cube, 以在放置時顯示其實際大小。</span><span class="sxs-lookup"><span data-stu-id="1e659-321">Render a bounding cube around the hologram to show its actual size while being placed.</span></span>
4. <span data-ttu-id="1e659-322">將陰影的下方/後方轉換成遮蔽, 以顯示放置在地面/牆上的位置。</span><span class="sxs-lookup"><span data-stu-id="1e659-322">Cast a shadow under/behind the hologram to show where it will be placed on the floor/wall.</span></span>
5. <span data-ttu-id="1e659-323">如果不能在表面上放置全息影像, 請將陰影轉譯為紅色, 如果可以, 則呈現綠色。</span><span class="sxs-lookup"><span data-stu-id="1e659-323">Render the shadow as red, if the hologram cannot be placed on the surface, or green, if it can.</span></span>
6. <span data-ttu-id="1e659-324">重新調整全息影像的方向, 使其與具有相似性的表面類型 (垂直或水準) 對齊。</span><span class="sxs-lookup"><span data-stu-id="1e659-324">Re-orient the hologram to align with the surface type (vertical or horizontal) that it has affinity to.</span></span>
7. <span data-ttu-id="1e659-325">順暢地將全息影像放在選取的表面上, 以避免跳躍或貼齊行為。</span><span class="sxs-lookup"><span data-stu-id="1e659-325">Smoothly place the hologram on the selected surface to avoid jumping or snapping behavior.</span></span>

<span data-ttu-id="1e659-326">取消批註下列編碼練習中的所有程式碼, 或在**Placeable.cs**中使用這個已完成的解決方案:</span><span class="sxs-lookup"><span data-stu-id="1e659-326">Uncomment all code in the coding exercise below, or use this completed solution in **Placeable.cs**:</span></span>

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

<span data-ttu-id="1e659-327">**組建和部署**</span><span class="sxs-lookup"><span data-stu-id="1e659-327">**Build and Deploy**</span></span>
* <span data-ttu-id="1e659-328">如先前所述, 建立專案並部署至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="1e659-328">As before, build the project and deploy to the HoloLens.</span></span>
* <span data-ttu-id="1e659-329">等候空間對應資料的掃描和處理完成。</span><span class="sxs-lookup"><span data-stu-id="1e659-329">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="1e659-330">當您看到日光系統時, 請看下面的投影方塊, 然後執行 select 手勢來四處移動。</span><span class="sxs-lookup"><span data-stu-id="1e659-330">When you see the solar system, gaze at the projection box below and perform a select gesture to move it around.</span></span> <span data-ttu-id="1e659-331">選取投影方塊時, 會在 [投射] 方塊周圍看到周框 cube。</span><span class="sxs-lookup"><span data-stu-id="1e659-331">While the projection box is selected, a bounding cube will be visible around the projection box.</span></span>
* <span data-ttu-id="1e659-332">將您的前端移到室內的不同位置。</span><span class="sxs-lookup"><span data-stu-id="1e659-332">Move you head to gaze at a different location in the room.</span></span> <span data-ttu-id="1e659-333">投影方塊應遵循您的注視。</span><span class="sxs-lookup"><span data-stu-id="1e659-333">The projection box should follow your gaze.</span></span> <span data-ttu-id="1e659-334">當投影方塊下方的陰影變成紅色時, 您就無法將全息影像放在該介面上。</span><span class="sxs-lookup"><span data-stu-id="1e659-334">When the shadow below the projection box turns red, you cannot place the hologram on that surface.</span></span> <span data-ttu-id="1e659-335">當投影方塊下方的陰影變成綠色時, 您可以藉由執行另一個 select 手勢來放置全息影像。</span><span class="sxs-lookup"><span data-stu-id="1e659-335">When the shadow below the projection box turns green, you can place the hologram by performing another select gesture.</span></span>
* <span data-ttu-id="1e659-336">尋找並選取牆上的其中一個全像攝影海報, 將其移至新位置。</span><span class="sxs-lookup"><span data-stu-id="1e659-336">Find and select one of the holographic posters on a wall to move it to a new location.</span></span> <span data-ttu-id="1e659-337">請注意, 您無法將海報放在樓層或上限, 而且當您四處移動時, 它會保持正確導向每個牆。</span><span class="sxs-lookup"><span data-stu-id="1e659-337">Notice that you cannot place the poster on the floor or ceiling, and that it stays correctly oriented to each wall as you move around.</span></span>

## <a name="chapter-5---occlusion"></a><span data-ttu-id="1e659-338">第5章-遮蔽</span><span class="sxs-lookup"><span data-stu-id="1e659-338">Chapter 5 - Occlusion</span></span>

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

<span data-ttu-id="1e659-339">**目標**</span><span class="sxs-lookup"><span data-stu-id="1e659-339">**Objectives**</span></span>
* <span data-ttu-id="1e659-340">判斷空間對應網格是否 pixels occluded 全息影像。</span><span class="sxs-lookup"><span data-stu-id="1e659-340">Determine if a hologram is occluded by the spatial mapping mesh.</span></span>
* <span data-ttu-id="1e659-341">套用不同的遮蔽技術, 以達到有趣的效果。</span><span class="sxs-lookup"><span data-stu-id="1e659-341">Apply different occlusion techniques to achieve a fun effect.</span></span>

<span data-ttu-id="1e659-342">**螢幕**</span><span class="sxs-lookup"><span data-stu-id="1e659-342">**Instructions**</span></span>

<span data-ttu-id="1e659-343">首先, 我們要讓空間對應網格遮蔽其他的全息影像, 而不 occluding 真實世界:</span><span class="sxs-lookup"><span data-stu-id="1e659-343">First, we are going to allow the spatial mapping mesh to occlude other holograms without occluding the real world:</span></span>
* <span data-ttu-id="1e659-344">在 [階層] 面板中, 選取 [ **SpatialProcessing** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="1e659-344">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="1e659-345">在 [偵測**器**] 面板中, 尋找 [**播放空間管理員 (腳本)** ] 元件。</span><span class="sxs-lookup"><span data-stu-id="1e659-345">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="1e659-346">按一下 [**次要材質**] 屬性右邊的圓形。</span><span class="sxs-lookup"><span data-stu-id="1e659-346">Click the circle to the right of the **Secondary Material** property.</span></span>
* <span data-ttu-id="1e659-347">尋找並選取 [**遮蔽**] 材質, 然後關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="1e659-347">Find and select the **Occlusion** material and close the window.</span></span>

<span data-ttu-id="1e659-348">接下來, 我們要在地球中加入一個特殊的行為, 讓它在另一個全息的 pixels occluded (像是太陽) 或空間對應網格時, 有一個藍色醒目提示:</span><span class="sxs-lookup"><span data-stu-id="1e659-348">Next, we are going to add a special behavior to Earth, so that it has a blue highlight whenever it becomes occluded by another hologram (like the sun), or by the spatial mapping mesh:</span></span>
* <span data-ttu-id="1e659-349">在 [**專案**] 面板的 [**全息影像**] 資料夾中, 展開 [ **SolarSystem** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="1e659-349">In the **Project** panel, in the **Holograms** folder, expand the **SolarSystem** object.</span></span>
* <span data-ttu-id="1e659-350">按一下 [**地球**]。</span><span class="sxs-lookup"><span data-stu-id="1e659-350">Click on **Earth**.</span></span>
* <span data-ttu-id="1e659-351">在 [偵測**器**] 面板中, 尋找地球材質 (底部元件)。</span><span class="sxs-lookup"><span data-stu-id="1e659-351">In the **Inspector** panel, find the Earth's material (bottom component).</span></span>
* <span data-ttu-id="1e659-352">在 [**著色器] 下拉式**按鈕中, 將著色器變更為 [**自訂 > OcclusionRim**]。</span><span class="sxs-lookup"><span data-stu-id="1e659-352">In the **Shader drop-down**, change the shader to **Custom > OcclusionRim**.</span></span> <span data-ttu-id="1e659-353">這會在每次由另一個物件 pixels occluded 時, 針對地球呈現藍色醒目提示。</span><span class="sxs-lookup"><span data-stu-id="1e659-353">This will render a blue highlight around Earth whenever it is occluded by another object.</span></span>

<span data-ttu-id="1e659-354">最後, 我們要為太陽系中的行星啟用 x 光線視覺效果。</span><span class="sxs-lookup"><span data-stu-id="1e659-354">Finally, we are going to enable an x-ray vision effect for planets in our solar system.</span></span> <span data-ttu-id="1e659-355">我們需要編輯**PlanetOcclusion.cs** (可在 Scripts\SolarSystem 資料夾中找到), 才能達到下列目的:</span><span class="sxs-lookup"><span data-stu-id="1e659-355">We will need to edit **PlanetOcclusion.cs** (found in the Scripts\SolarSystem folder) in order to achieve the following:</span></span>
1. <span data-ttu-id="1e659-356">判斷 SpatialMapping 層 (房間網格和平面) 是否 pixels occluded 地球。</span><span class="sxs-lookup"><span data-stu-id="1e659-356">Determine if a planet is occluded by the SpatialMapping layer (room meshes and planes).</span></span>
2. <span data-ttu-id="1e659-357">每次由 SpatialMapping 圖層 pixels occluded 時, 顯示地球的線框表示。</span><span class="sxs-lookup"><span data-stu-id="1e659-357">Show the wireframe representation of a planet whenever it is occluded by the SpatialMapping layer.</span></span>
3. <span data-ttu-id="1e659-358">當 SpatialMapping 圖層未封鎖時, 隱藏地球的線框標記法。</span><span class="sxs-lookup"><span data-stu-id="1e659-358">Hide the wireframe representation of a planet when it is not blocked by the SpatialMapping layer.</span></span>

<span data-ttu-id="1e659-359">遵循 PlanetOcclusion.cs 中的程式碼撰寫練習, 或使用下列解決方案:</span><span class="sxs-lookup"><span data-stu-id="1e659-359">Follow the coding exercise in PlanetOcclusion.cs, or use the following solution:</span></span>

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

<span data-ttu-id="1e659-360">**組建和部署**</span><span class="sxs-lookup"><span data-stu-id="1e659-360">**Build and Deploy**</span></span>
* <span data-ttu-id="1e659-361">如往常般建立應用程式並將其部署至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="1e659-361">Build and deploy the application to HoloLens, as usual.</span></span>
* <span data-ttu-id="1e659-362">等候空間對應資料的掃描和處理完成 (您應該會看到藍色的線條出現在牆上)。</span><span class="sxs-lookup"><span data-stu-id="1e659-362">Wait for scanning and processing of the spatial mapping data to be complete (you should see blue lines appear on walls).</span></span>
* <span data-ttu-id="1e659-363">尋找並選取 [日光系統] 的 [投射] 方塊, 然後設定牆或計數器後方的方塊。</span><span class="sxs-lookup"><span data-stu-id="1e659-363">Find and select the solar system's projection box and then set the box next to a wall or behind a counter.</span></span>
* <span data-ttu-id="1e659-364">您可以在 [海報] 或 [投影] 方塊中隱藏 [對等的表面], 以查看基本遮蔽。</span><span class="sxs-lookup"><span data-stu-id="1e659-364">You can view basic occlusion by hiding behind surfaces to peer at the poster or projection box.</span></span>
* <span data-ttu-id="1e659-365">找出地球, 當它放在另一個全息或表面後面時, 應該會有藍色醒目提示效果。</span><span class="sxs-lookup"><span data-stu-id="1e659-365">Look for the Earth, there should be a blue highlight effect whenever it goes behind another hologram or surface.</span></span>
* <span data-ttu-id="1e659-366">當行星在室內或房間內的其他表面上移動時, 觀看。</span><span class="sxs-lookup"><span data-stu-id="1e659-366">Watch as the planets move behind the wall or other surfaces in the room.</span></span> <span data-ttu-id="1e659-367">您現在有 x 光線願景, 可以看到其框線骨架!</span><span class="sxs-lookup"><span data-stu-id="1e659-367">You now have x-ray vision and can see their wireframe skeletons!</span></span>

## <a name="the-end"></a><span data-ttu-id="1e659-368">結束</span><span class="sxs-lookup"><span data-stu-id="1e659-368">The End</span></span>

<span data-ttu-id="1e659-369">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="1e659-369">Congratulations!</span></span> <span data-ttu-id="1e659-370">您現在已完成**MR 空間 230:空間對應**。</span><span class="sxs-lookup"><span data-stu-id="1e659-370">You have now completed **MR Spatial 230: Spatial mapping**.</span></span>
* <span data-ttu-id="1e659-371">您知道如何掃描您的環境, 並將空間對應資料載入 Unity。</span><span class="sxs-lookup"><span data-stu-id="1e659-371">You know how to scan your environment and load spatial mapping data to Unity.</span></span>
* <span data-ttu-id="1e659-372">您會瞭解著色器的基本概念, 以及如何使用材質來重新視覺化世界。</span><span class="sxs-lookup"><span data-stu-id="1e659-372">You understand the basics of shaders and how materials can be used to re-visualize the world.</span></span>
* <span data-ttu-id="1e659-373">您已瞭解用來尋找平面和從網格中移除三角形的新處理技術。</span><span class="sxs-lookup"><span data-stu-id="1e659-373">You learned of new processing techniques for finding planes and removing triangles from a mesh.</span></span>
* <span data-ttu-id="1e659-374">您可以在有意義的表面上移動和放置全息影像。</span><span class="sxs-lookup"><span data-stu-id="1e659-374">You were able to move and place holograms on surfaces that made sense.</span></span>
* <span data-ttu-id="1e659-375">您遇到了不同的遮蔽技巧, 駕馭了 x 光線願景的威力!</span><span class="sxs-lookup"><span data-stu-id="1e659-375">You experienced different occlusion techniques and harnessed the power of x-ray vision!</span></span>
