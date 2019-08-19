---
title: MR 基本概念 101E-使用模擬器完成專案
description: 遵循使用 Unity、Visual Studio 和 HoloLens 模擬器的編碼逐步解說, 學習全像攝影應用程式的基本概念。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: 混合現實、Windows Mixed Reality、HoloLens、全息裡、學院、教學課程、模擬器
ms.openlocfilehash: 77f7d497396937bf471a69fa514cef84ab0b699d
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522329"
---
>[!NOTE]
><span data-ttu-id="4420d-104">混合現實學術教學課程的設計是使用 HoloLens (第1代) 和混合現實的沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="4420d-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="4420d-105">因此, 對於仍在尋找這些裝置開發指引的開發人員而言, 我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="4420d-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="4420d-106">這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="4420d-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="4420d-107">系統會保留這些資訊, 以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="4420d-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="4420d-108">未來將會有一系列新的教學課程, 將示範如何針對 HoloLens 2 進行開發。</span><span class="sxs-lookup"><span data-stu-id="4420d-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="4420d-109">此通知會在張貼時, 使用這些教學課程的連結進行更新。</span><span class="sxs-lookup"><span data-stu-id="4420d-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a><span data-ttu-id="4420d-110">MR 基本概念 101E:使用模擬器完成專案</span><span class="sxs-lookup"><span data-stu-id="4420d-110">MR Basics 101E: Complete project with emulator</span></span>

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

<span data-ttu-id="4420d-111">本教學課程將逐步引導您完成以 Unity 為基礎的完整專案, 其中示範 HoloLens 上的核心 Windows Mixed Reality 功能, 包括[注視](gaze.md)、[手勢](gestures.md)、[語音輸入](voice-input.md)、[空間音效](spatial-sound.md)和[空間對應](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="4420d-111">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze.md), [gestures](gestures.md), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span> <span data-ttu-id="4420d-112">本教學課程需要大約1小時才能完成。</span><span class="sxs-lookup"><span data-stu-id="4420d-112">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="4420d-113">裝置支援</span><span class="sxs-lookup"><span data-stu-id="4420d-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="4420d-114">粗</span><span class="sxs-lookup"><span data-stu-id="4420d-114">Course</span></span></th><th style="width:150px"> <span data-ttu-id="4420d-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="4420d-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="4420d-116"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="4420d-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="4420d-117">MR 基本概念 101E:使用模擬器完成專案</span><span class="sxs-lookup"><span data-stu-id="4420d-117">MR Basics 101E: Complete project with emulator</span></span></td><td style="text-align: center;"> <span data-ttu-id="4420d-118">✔️</span><span class="sxs-lookup"><span data-stu-id="4420d-118">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="4420d-119">開始之前</span><span class="sxs-lookup"><span data-stu-id="4420d-119">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="4420d-120">先決條件</span><span class="sxs-lookup"><span data-stu-id="4420d-120">Prerequisites</span></span>

* <span data-ttu-id="4420d-121">[已安裝正確工具](install-the-tools.md)的 WINDOWS 10 電腦。</span><span class="sxs-lookup"><span data-stu-id="4420d-121">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

### <a name="project-files"></a><span data-ttu-id="4420d-122">專案檔案</span><span class="sxs-lookup"><span data-stu-id="4420d-122">Project files</span></span>

* <span data-ttu-id="4420d-123">下載專案所需的[檔案](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="4420d-123">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="4420d-124"> 需要 Unity 2017.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="4420d-124"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="4420d-125">如果您仍然需要 Unity 5.6 支援, 請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="4420d-125">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="4420d-126">如果您仍然需要 Unity 5.5 支援, 請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="4420d-126">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="4420d-127">如果您仍然需要 Unity 5.4 支援, 請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="4420d-127">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="4420d-128">將檔案取消封存至您的桌面或其他容易到達的位置。</span><span class="sxs-lookup"><span data-stu-id="4420d-128">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="4420d-129">將資料夾名稱保留為 [**折紙**]。</span><span class="sxs-lookup"><span data-stu-id="4420d-129">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="4420d-130">如果您想要在下載之前查看原始程式碼, 可以[在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)取得。</span><span class="sxs-lookup"><span data-stu-id="4420d-130">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="4420d-131">第1章-「Hololens」世界</span><span class="sxs-lookup"><span data-stu-id="4420d-131">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

<span data-ttu-id="4420d-132">在本章中, 我們將設定第一個 Unity 專案, 並逐步執行組建和部署流程。</span><span class="sxs-lookup"><span data-stu-id="4420d-132">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="4420d-133">目標</span><span class="sxs-lookup"><span data-stu-id="4420d-133">Objectives</span></span>

* <span data-ttu-id="4420d-134">設定 Unity 以進行全像攝影開發。</span><span class="sxs-lookup"><span data-stu-id="4420d-134">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="4420d-135">建立全息影像。</span><span class="sxs-lookup"><span data-stu-id="4420d-135">Make a hologram.</span></span>
* <span data-ttu-id="4420d-136">查看您製作的全息影像。</span><span class="sxs-lookup"><span data-stu-id="4420d-136">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="4420d-137">指示</span><span class="sxs-lookup"><span data-stu-id="4420d-137">Instructions</span></span>

* <span data-ttu-id="4420d-138">啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="4420d-138">Start Unity.</span></span>
* <span data-ttu-id="4420d-139">選取 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="4420d-139">Select **Open**.</span></span>
* <span data-ttu-id="4420d-140">輸入 [位置] 做為您先前未封存的 [**折紙**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4420d-140">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="4420d-141">選取 [**折紙**], 然後按一下 [**選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="4420d-141">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="4420d-142">儲存新場景:將場景**另存為。**  / </span><span class="sxs-lookup"><span data-stu-id="4420d-142">Save the new scene: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="4420d-143">將場景命名為「**折紙**」, 然後按 [**儲存**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4420d-143">Name the scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-camera"></a><span data-ttu-id="4420d-144">設定主要攝影機</span><span class="sxs-lookup"><span data-stu-id="4420d-144">Setup the main camera</span></span>

* <span data-ttu-id="4420d-145">在 [階層]**面板**中, 選取 [**主要相機**]。</span><span class="sxs-lookup"><span data-stu-id="4420d-145">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="4420d-146">在偵測**器**中, 將其轉換位置設為**0, 0, 0**。</span><span class="sxs-lookup"><span data-stu-id="4420d-146">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="4420d-147">尋找 [**清除旗標**] 屬性, 並將下拉式清單從 [ **Skybox** ] 變更為 [**單色**]。</span><span class="sxs-lookup"><span data-stu-id="4420d-147">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="4420d-148">按一下 [**背景**] 欄位, 以開啟色彩選擇器。</span><span class="sxs-lookup"><span data-stu-id="4420d-148">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="4420d-149">將**R、G、B 和 A**設定為**0**。</span><span class="sxs-lookup"><span data-stu-id="4420d-149">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="4420d-150">設定場景</span><span class="sxs-lookup"><span data-stu-id="4420d-150">Setup the scene</span></span>

* <span data-ttu-id="4420d-151">在 [階層]**面板**中, 按一下 [**建立**] 並**建立空**的。</span><span class="sxs-lookup"><span data-stu-id="4420d-151">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="4420d-152">以滑鼠右鍵按一下新的**GameObject** , 然後選取 [重新命名]。</span><span class="sxs-lookup"><span data-stu-id="4420d-152">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="4420d-153">將 GameObject 重新命名為**OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="4420d-153">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="4420d-154">從 [**專案] 面板**中的 [**全息影像**] 資料夾:</span><span class="sxs-lookup"><span data-stu-id="4420d-154">From the **Holograms** folder in the **Project Panel**:</span></span>
  * <span data-ttu-id="4420d-155">將**階段**拖曳到階層中, 成為**OrigamiCollection**的子系。</span><span class="sxs-lookup"><span data-stu-id="4420d-155">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="4420d-156">將**Sphere1**拖曳到階層中, 成為**OrigamiCollection**的子系。</span><span class="sxs-lookup"><span data-stu-id="4420d-156">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="4420d-157">將**Sphere2**拖曳到階層中, 成為**OrigamiCollection**的子系。</span><span class="sxs-lookup"><span data-stu-id="4420d-157">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="4420d-158">以滑鼠右鍵按一下 [階層]**面板**中的 [**方向光源**] 物件, 然後選取 [**刪除**]。</span><span class="sxs-lookup"><span data-stu-id="4420d-158">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="4420d-159">從 [**全息影像**] 資料夾, 將 [**燈光**] 拖曳至 [階層]**面板**的根目錄。</span><span class="sxs-lookup"><span data-stu-id="4420d-159">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="4420d-160">在階層中, 選取 [ **OrigamiCollection**]。</span><span class="sxs-lookup"><span data-stu-id="4420d-160">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="4420d-161">在偵測**器**中, 將轉換位置設定為**0,-0.5, 2.0**。</span><span class="sxs-lookup"><span data-stu-id="4420d-161">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="4420d-162">按下 Unity 中的 [**播放**] 按鈕, 以預覽您的全息影像。</span><span class="sxs-lookup"><span data-stu-id="4420d-162">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="4420d-163">您應該會在預覽視窗中看到 [折紙] 物件。</span><span class="sxs-lookup"><span data-stu-id="4420d-163">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="4420d-164">按第二次 [**播放**] 以停止預覽模式。</span><span class="sxs-lookup"><span data-stu-id="4420d-164">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="4420d-165">將專案從 Unity 匯出至 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4420d-165">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="4420d-166">在 Unity 中, 選取 檔案 **> 組建設定**。</span><span class="sxs-lookup"><span data-stu-id="4420d-166">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="4420d-167">在 [**平臺**] 清單中選取 [ **Windows 儲存區**], 然後按一下 [**切換平臺**]。</span><span class="sxs-lookup"><span data-stu-id="4420d-167">Select **Windows Store** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="4420d-168">將 [ **SDK** ] 設定為 [**通用 10** ], 將 [**組建類型**] 設為**D3D**</span><span class="sxs-lookup"><span data-stu-id="4420d-168">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="4420d-169">檢查**Unity C#專案**。</span><span class="sxs-lookup"><span data-stu-id="4420d-169">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="4420d-170">按一下 [新增] [**開啟場景**] 以加入場景。</span><span class="sxs-lookup"><span data-stu-id="4420d-170">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="4420d-171">按一下 [**玩家設定**]。</span><span class="sxs-lookup"><span data-stu-id="4420d-171">Click **Player Settings...**.</span></span>
* <span data-ttu-id="4420d-172">在 [偵測器] 面板中, 選取 [ **Windows Store] 標誌**。</span><span class="sxs-lookup"><span data-stu-id="4420d-172">In the Inspector Panel select the **Windows Store logo**.</span></span> <span data-ttu-id="4420d-173">然後選取 [**發行設定**]。</span><span class="sxs-lookup"><span data-stu-id="4420d-173">Then select **Publishing Settings**.</span></span>
* <span data-ttu-id="4420d-174">在 [**功能**] 區段中, 選取 [**麥克風**] 和 [ **SpatialPerception** ] 功能。</span><span class="sxs-lookup"><span data-stu-id="4420d-174">In the **Capabilities** section, select the **Microphone** and **SpatialPerception** capabilities.</span></span>
* <span data-ttu-id="4420d-175">回到 [組建設定] 視窗, 按一下 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="4420d-175">Back in the Build Settings window, click **Build**.</span></span>
* <span data-ttu-id="4420d-176">建立名為 "App" 的**新資料夾**。</span><span class="sxs-lookup"><span data-stu-id="4420d-176">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="4420d-177">按一下 [**應用程式] 資料夾**。</span><span class="sxs-lookup"><span data-stu-id="4420d-177">Single click the **App Folder**.</span></span>
* <span data-ttu-id="4420d-178">按 [**選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="4420d-178">Press **Select Folder**.</span></span>
* <span data-ttu-id="4420d-179">當 Unity 完成時, 將會出現 [檔案瀏覽器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="4420d-179">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="4420d-180">開啟**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="4420d-180">Open the **App** folder.</span></span>
* <span data-ttu-id="4420d-181">開啟 [**日式 Visual Studio] 解決方案**。</span><span class="sxs-lookup"><span data-stu-id="4420d-181">Open the **Origami Visual Studio Solution**.</span></span>
* <span data-ttu-id="4420d-182">使用 Visual Studio 中的頂端工具列, 將目標從 [調試] 變更為 [**發行**], 將 [從 ARM] 變更為**X86**。</span><span class="sxs-lookup"><span data-stu-id="4420d-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
  * <span data-ttu-id="4420d-183">按一下 [裝置] 按鈕旁邊的箭號, 然後選取 [ **HoloLens 模擬器**]。</span><span class="sxs-lookup"><span data-stu-id="4420d-183">Click on the arrow next to the Device button, and select **HoloLens Emulator**.</span></span>
  * <span data-ttu-id="4420d-184">按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="4420d-184">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
  * <span data-ttu-id="4420d-185">經過一段時間之後, 模擬器就會以折紙專案開始。</span><span class="sxs-lookup"><span data-stu-id="4420d-185">After some time the emulator will start with the Origami project.</span></span> <span data-ttu-id="4420d-186">第一次啟動[模擬器](using-the-hololens-emulator.md)時, 啟動模擬器可能需要15分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="4420d-186">When first launching the [emulator](using-the-hololens-emulator.md), it can take as long as 15 minutes for the emulator to start up.</span></span> <span data-ttu-id="4420d-187">啟動之後, 請勿將它關閉。</span><span class="sxs-lookup"><span data-stu-id="4420d-187">Once it starts, do not close it.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="4420d-188">第2章-注視</span><span class="sxs-lookup"><span data-stu-id="4420d-188">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

<span data-ttu-id="4420d-189">在本章中, 我們將引進三種與您的全息影像互動的第一種方式:[注視](gaze.md)。</span><span class="sxs-lookup"><span data-stu-id="4420d-189">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="4420d-190">目標</span><span class="sxs-lookup"><span data-stu-id="4420d-190">Objectives</span></span>

* <span data-ttu-id="4420d-191">使用世界鎖定的游標來視覺化您的注視。</span><span class="sxs-lookup"><span data-stu-id="4420d-191">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="4420d-192">指示</span><span class="sxs-lookup"><span data-stu-id="4420d-192">Instructions</span></span>

* <span data-ttu-id="4420d-193">回到您的 Unity 專案, 並關閉 [組建設定] 視窗 (如果仍處於開啟狀態)。</span><span class="sxs-lookup"><span data-stu-id="4420d-193">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="4420d-194">在 [**專案] 面板**中選取 [**全息影像**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4420d-194">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="4420d-195">將**游標**物件拖曳至根層級的 [階層]**面板**。</span><span class="sxs-lookup"><span data-stu-id="4420d-195">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="4420d-196">按兩下**游標**物件以深入瞭解它。</span><span class="sxs-lookup"><span data-stu-id="4420d-196">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="4420d-197">以滑鼠右鍵按一下 [專案] 面板中的 [**腳本**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4420d-197">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="4420d-198">按一下 [**建立**] 子功能表。</span><span class="sxs-lookup"><span data-stu-id="4420d-198">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="4420d-199">選取 **C# [腳本**]。</span><span class="sxs-lookup"><span data-stu-id="4420d-199">Select **C# Script**.</span></span>
* <span data-ttu-id="4420d-200">將腳本命名為**WorldCursor**。</span><span class="sxs-lookup"><span data-stu-id="4420d-200">Name the script **WorldCursor**.</span></span> <span data-ttu-id="4420d-201">注意:此名稱區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="4420d-201">Note: The name is case-sensitive.</span></span> <span data-ttu-id="4420d-202">您不需要新增 .cs 副檔名。</span><span class="sxs-lookup"><span data-stu-id="4420d-202">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="4420d-203">在 [階層]**面板**中選取**游標**物件。</span><span class="sxs-lookup"><span data-stu-id="4420d-203">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="4420d-204">將**WorldCursor**腳本拖放到 [偵測**器] 面板**中。</span><span class="sxs-lookup"><span data-stu-id="4420d-204">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="4420d-205">按兩下 [ **WorldCursor** ] 腳本, 在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="4420d-205">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="4420d-206">將此程式碼複製並貼到**WorldCursor.cs**中, 並**全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="4420d-206">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move thecursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* <span data-ttu-id="4420d-207">從 [檔案] **> 組建設定**重建應用程式。</span><span class="sxs-lookup"><span data-stu-id="4420d-207">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="4420d-208">回到先前用來部署至模擬器的 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="4420d-208">Return to the Visual Studio solution previously used to deploy to the emulator.</span></span>
* <span data-ttu-id="4420d-209">出現提示時, 選取 [全部重載]。</span><span class="sxs-lookup"><span data-stu-id="4420d-209">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="4420d-210">按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="4420d-210">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="4420d-211">使用 Xbox 控制器來尋找場景。</span><span class="sxs-lookup"><span data-stu-id="4420d-211">Use the Xbox controller to look around the scene.</span></span> <span data-ttu-id="4420d-212">請注意游標如何與物件的形狀互動。</span><span class="sxs-lookup"><span data-stu-id="4420d-212">Notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="4420d-213">第3章-手勢</span><span class="sxs-lookup"><span data-stu-id="4420d-213">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

<span data-ttu-id="4420d-214">在本章中, 我們將新增[手勢](gestures.md)的支援。</span><span class="sxs-lookup"><span data-stu-id="4420d-214">In this chapter, we'll add support for [gestures](gestures.md).</span></span> <span data-ttu-id="4420d-215">當使用者選取紙球體時, 我們會使用 Unity 的物理引擎來開啟重心, 讓球體變得更容易。</span><span class="sxs-lookup"><span data-stu-id="4420d-215">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="4420d-216">目標</span><span class="sxs-lookup"><span data-stu-id="4420d-216">Objectives</span></span>

* <span data-ttu-id="4420d-217">使用選取手勢控制您的全息影像。</span><span class="sxs-lookup"><span data-stu-id="4420d-217">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="4420d-218">指示</span><span class="sxs-lookup"><span data-stu-id="4420d-218">Instructions</span></span>

<span data-ttu-id="4420d-219">我們將從建立腳本開始, 而不會偵測到選取手勢。</span><span class="sxs-lookup"><span data-stu-id="4420d-219">We'll start by creating a script than can detect the Select gesture.</span></span>

* <span data-ttu-id="4420d-220">在 [**腳本**] 資料夾中, 建立名為**GazeGestureManager**的腳本。</span><span class="sxs-lookup"><span data-stu-id="4420d-220">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="4420d-221">將**GazeGestureManager**腳本拖曳至階層中的**OrigamiCollection**物件。</span><span class="sxs-lookup"><span data-stu-id="4420d-221">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="4420d-222">在 Visual Studio 中開啟**GazeGestureManager**腳本, 並新增下列程式碼:</span><span class="sxs-lookup"><span data-stu-id="4420d-222">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Start()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* <span data-ttu-id="4420d-223">在 Scripts 資料夾中建立另一個腳本, 這次名為**SphereCommands**。</span><span class="sxs-lookup"><span data-stu-id="4420d-223">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="4420d-224">在 [階層] 視圖中展開 [ **OrigamiCollection** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="4420d-224">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="4420d-225">將**SphereCommands**腳本拖曳至 [階層] 面板中的**Sphere1**物件。</span><span class="sxs-lookup"><span data-stu-id="4420d-225">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="4420d-226">將**SphereCommands**腳本拖曳至 [階層] 面板中的**Sphere2**物件。</span><span class="sxs-lookup"><span data-stu-id="4420d-226">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="4420d-227">在 Visual Studio 中開啟腳本進行編輯, 並將預設程式碼取代為:</span><span class="sxs-lookup"><span data-stu-id="4420d-227">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* <span data-ttu-id="4420d-228">匯出、建立應用程式, 並將其部署至 HoloLens 模擬器。</span><span class="sxs-lookup"><span data-stu-id="4420d-228">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="4420d-229">查看場景, 並將中心放在其中一個球體。</span><span class="sxs-lookup"><span data-stu-id="4420d-229">Look around the scene, and center on one of the spheres.</span></span>
* <span data-ttu-id="4420d-230">按下 Xbox 控制器上的**一個**按鈕, 或按空格鍵以模擬選取手勢。</span><span class="sxs-lookup"><span data-stu-id="4420d-230">Press the **A** button on the Xbox controller or press the Spacebar to simulate the Select gesture.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="4420d-231">第4章-語音</span><span class="sxs-lookup"><span data-stu-id="4420d-231">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

<span data-ttu-id="4420d-232">在本章中, 我們將新增兩個[語音命令](voice-input.md)的支援:「重設世界」以將捨棄的球面傳回其原始位置, 而「卸載球體」則讓球體落在一起。</span><span class="sxs-lookup"><span data-stu-id="4420d-232">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to returns the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="4420d-233">目標</span><span class="sxs-lookup"><span data-stu-id="4420d-233">Objectives</span></span>

* <span data-ttu-id="4420d-234">新增一律在背景中接聽的語音命令。</span><span class="sxs-lookup"><span data-stu-id="4420d-234">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="4420d-235">建立可回應語音命令的全息影像。</span><span class="sxs-lookup"><span data-stu-id="4420d-235">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="4420d-236">指示</span><span class="sxs-lookup"><span data-stu-id="4420d-236">Instructions</span></span>

* <span data-ttu-id="4420d-237">在 [**腳本**] 資料夾中, 建立名為**SpeechManager**的腳本。</span><span class="sxs-lookup"><span data-stu-id="4420d-237">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="4420d-238">將**SpeechManager**腳本拖曳至階層中的**OrigamiCollection**物件</span><span class="sxs-lookup"><span data-stu-id="4420d-238">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="4420d-239">在 Visual Studio 中開啟**SpeechManager**腳本。</span><span class="sxs-lookup"><span data-stu-id="4420d-239">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="4420d-240">將此程式碼複製並貼到**SpeechManager.cs**中, 並**全部儲存**:</span><span class="sxs-lookup"><span data-stu-id="4420d-240">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* <span data-ttu-id="4420d-241">在 Visual Studio 中開啟**SphereCommands**腳本。</span><span class="sxs-lookup"><span data-stu-id="4420d-241">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="4420d-242">更新腳本以進行讀取, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="4420d-242">Update the script to read as follows:</span></span>

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* <span data-ttu-id="4420d-243">匯出、建立應用程式, 並將其部署至 HoloLens 模擬器。</span><span class="sxs-lookup"><span data-stu-id="4420d-243">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="4420d-244">模擬器會支援您電腦的麥克風並回應您的聲音: 調整視圖, 使游標位於球體的其中一個, 並說出「卸載球體」。</span><span class="sxs-lookup"><span data-stu-id="4420d-244">The emulator will support your PC's microphone and respond to your voice: adjust the view so the cursor is on one of the spheres, and say "Drop Sphere".</span></span>
* <span data-ttu-id="4420d-245">請說「**重設世界**」, 使其回到其初始位置。</span><span class="sxs-lookup"><span data-stu-id="4420d-245">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="4420d-246">第5章-空間音效</span><span class="sxs-lookup"><span data-stu-id="4420d-246">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

<span data-ttu-id="4420d-247">在本章中, 我們會將音樂新增至應用程式, 然後觸發對特定動作的音效效果。</span><span class="sxs-lookup"><span data-stu-id="4420d-247">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="4420d-248">我們會使用[空間音效](spatial-sound.md), 在3d 空間中提供特定位置的聲音。</span><span class="sxs-lookup"><span data-stu-id="4420d-248">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="4420d-249">目標</span><span class="sxs-lookup"><span data-stu-id="4420d-249">Objectives</span></span>

* <span data-ttu-id="4420d-250">聆聽您世界中的全息影像。</span><span class="sxs-lookup"><span data-stu-id="4420d-250">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="4420d-251">指示</span><span class="sxs-lookup"><span data-stu-id="4420d-251">Instructions</span></span>

* <span data-ttu-id="4420d-252">在 Unity 中, 從頂端功能表中選取 [**編輯] > 專案設定 > 音訊**</span><span class="sxs-lookup"><span data-stu-id="4420d-252">In the Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="4420d-253">尋找**空間定位器外掛程式**設定, 然後選取 [ **MS HRTF 空間定位器**]。</span><span class="sxs-lookup"><span data-stu-id="4420d-253">Find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="4420d-254">從 [**全息影像**] 資料夾, 將 [**環境**] 物件拖曳至 [階層] 面板中的 [ **OrigamiCollection** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="4420d-254">From the **Holograms** folder, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="4420d-255">選取 [ **OrigamiCollection** ], 然後尋找 [**音訊來源**] 元件。</span><span class="sxs-lookup"><span data-stu-id="4420d-255">Select **OrigamiCollection** and find the **Audio Source** component.</span></span> <span data-ttu-id="4420d-256">變更這些屬性:</span><span class="sxs-lookup"><span data-stu-id="4420d-256">Change these properties:</span></span>
  * <span data-ttu-id="4420d-257">檢查**Spatialize**屬性。</span><span class="sxs-lookup"><span data-stu-id="4420d-257">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="4420d-258">勾選 [**在喚醒時播放**]。</span><span class="sxs-lookup"><span data-stu-id="4420d-258">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="4420d-259">將 [**空間 Blend** ] 變更為 [ **3d** ], 方法是將滑杆向右拖曳。</span><span class="sxs-lookup"><span data-stu-id="4420d-259">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span>
  * <span data-ttu-id="4420d-260">檢查 [**迴圈**] 屬性。</span><span class="sxs-lookup"><span data-stu-id="4420d-260">Check the **Loop** property.</span></span>
  * <span data-ttu-id="4420d-261">展開 [ **3D 音效設定**], 然後針對 [ **Doppler 層級**] 輸入**0.1** 。</span><span class="sxs-lookup"><span data-stu-id="4420d-261">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="4420d-262">將 [**磁片區 Rolloff** ] 設定為 [**對數 Rolloff**]。</span><span class="sxs-lookup"><span data-stu-id="4420d-262">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="4420d-263">將 [**最大距離**] 設定為**20**。</span><span class="sxs-lookup"><span data-stu-id="4420d-263">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="4420d-264">在 [**腳本**] 資料夾中, 建立名為**SphereSounds**的腳本。</span><span class="sxs-lookup"><span data-stu-id="4420d-264">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="4420d-265">將 [ **SphereSounds** ] 拖曳至階層中的**Sphere1**和**Sphere2**物件。</span><span class="sxs-lookup"><span data-stu-id="4420d-265">Drag **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="4420d-266">在 Visual Studio 中開啟**SphereSounds** , 更新下列程式碼並**全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="4420d-266">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* <span data-ttu-id="4420d-267">儲存腳本, 並返回 Unity。</span><span class="sxs-lookup"><span data-stu-id="4420d-267">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="4420d-268">匯出、建立應用程式, 並將其部署至 HoloLens 模擬器。</span><span class="sxs-lookup"><span data-stu-id="4420d-268">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="4420d-269">戴耳機以獲得完整的效果, 並從階段中更靠近或更深入地收聽音效變更。</span><span class="sxs-lookup"><span data-stu-id="4420d-269">Wear headphones to get the full effect, and move closer and further from the Stage to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="4420d-270">第6章-空間對應</span><span class="sxs-lookup"><span data-stu-id="4420d-270">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

<span data-ttu-id="4420d-271">現在我們要使用[空間對應](spatial-mapping.md), 將遊戲面板放在真實世界中的實際物件上。</span><span class="sxs-lookup"><span data-stu-id="4420d-271">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="4420d-272">目標</span><span class="sxs-lookup"><span data-stu-id="4420d-272">Objectives</span></span>

* <span data-ttu-id="4420d-273">將您的真實世界帶入虛擬世界。</span><span class="sxs-lookup"><span data-stu-id="4420d-273">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="4420d-274">將您的全息影像放在對您最重要的地方。</span><span class="sxs-lookup"><span data-stu-id="4420d-274">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="4420d-275">指示</span><span class="sxs-lookup"><span data-stu-id="4420d-275">Instructions</span></span>

* <span data-ttu-id="4420d-276">按一下 [專案] 面板中的 [**全息影像**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4420d-276">Click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="4420d-277">將**空間對應**資產拖曳至階層的根目錄。</span><span class="sxs-lookup"><span data-stu-id="4420d-277">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="4420d-278">按一下階層中的 [**空間對應**] 物件。</span><span class="sxs-lookup"><span data-stu-id="4420d-278">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="4420d-279">在 [偵測**器] 面板**中, 變更下列屬性:</span><span class="sxs-lookup"><span data-stu-id="4420d-279">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="4420d-280">勾選 [**繪製視覺網格**] 方塊。</span><span class="sxs-lookup"><span data-stu-id="4420d-280">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="4420d-281">找出 [**繪製材質**], 然後按一下右側的圓形。</span><span class="sxs-lookup"><span data-stu-id="4420d-281">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="4420d-282">在頂端的搜尋欄位中輸入「**線框**」。</span><span class="sxs-lookup"><span data-stu-id="4420d-282">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="4420d-283">按一下結果, 然後關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="4420d-283">Click on the result and then close the window.</span></span>
* <span data-ttu-id="4420d-284">匯出、建立應用程式, 並將其部署至 HoloLens 模擬器。</span><span class="sxs-lookup"><span data-stu-id="4420d-284">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="4420d-285">當應用程式執行時, 系統會以線框呈現先前掃描的實際生活空間網格。</span><span class="sxs-lookup"><span data-stu-id="4420d-285">When the app runs, a mesh of a previously scanned real-world living room will be rendered in wireframe.</span></span>
* <span data-ttu-id="4420d-286">觀賞輪流球體如何落在舞臺上, 以及在地面上!</span><span class="sxs-lookup"><span data-stu-id="4420d-286">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="4420d-287">現在, 我們將示範如何將 OrigamiCollection 移到新的位置:</span><span class="sxs-lookup"><span data-stu-id="4420d-287">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="4420d-288">在 [**腳本**] 資料夾中, 建立名為**TapToPlaceParent**的腳本。</span><span class="sxs-lookup"><span data-stu-id="4420d-288">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="4420d-289">在階層中, 展開 [ **OrigamiCollection** ], 然後選取 [**階段**] 物件。</span><span class="sxs-lookup"><span data-stu-id="4420d-289">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="4420d-290">將**TapToPlaceParent**腳本拖曳至階段物件。</span><span class="sxs-lookup"><span data-stu-id="4420d-290">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="4420d-291">在 Visual Studio 中開啟**TapToPlaceParent**腳本, 並將它更新為下列內容:</span><span class="sxs-lookup"><span data-stu-id="4420d-291">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* <span data-ttu-id="4420d-292">匯出、建立及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="4420d-292">Export, build and deploy the app.</span></span>
* <span data-ttu-id="4420d-293">現在您應該可以使用選取手勢 (**a**或空格鍵) 然後移至新位置, 然後再次使用 [選取] 手勢, 將遊戲放在特定位置。</span><span class="sxs-lookup"><span data-stu-id="4420d-293">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture (**A** or Spacebar) and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="the-end"></a><span data-ttu-id="4420d-294">結束</span><span class="sxs-lookup"><span data-stu-id="4420d-294">The end</span></span>

<span data-ttu-id="4420d-295">這就是本教學課程的結尾!</span><span class="sxs-lookup"><span data-stu-id="4420d-295">And that's the end of this tutorial!</span></span>

<span data-ttu-id="4420d-296">您已瞭解:</span><span class="sxs-lookup"><span data-stu-id="4420d-296">You learned:</span></span>

* <span data-ttu-id="4420d-297">如何在 Unity 中建立全像攝影應用程式。</span><span class="sxs-lookup"><span data-stu-id="4420d-297">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="4420d-298">如何使用 [注視]、[手勢]、[聲音]、[音效] 和 [空間對應]。</span><span class="sxs-lookup"><span data-stu-id="4420d-298">How to make use of gaze, gesture, voice, sounds, and spatial mapping.</span></span>
* <span data-ttu-id="4420d-299">如何使用 Visual Studio 建立及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="4420d-299">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="4420d-300">您現在已準備好開始建立自己的全像攝影應用程式!</span><span class="sxs-lookup"><span data-stu-id="4420d-300">You are now ready to start creating your own holographic apps!</span></span>

## <a name="see-also"></a><span data-ttu-id="4420d-301">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4420d-301">See also</span></span>

* [<span data-ttu-id="4420d-302">MR Basics 101：使用裝置完成專案</span><span class="sxs-lookup"><span data-stu-id="4420d-302">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="4420d-303">目光</span><span class="sxs-lookup"><span data-stu-id="4420d-303">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="4420d-304">筆勢</span><span class="sxs-lookup"><span data-stu-id="4420d-304">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="4420d-305">語音輸入</span><span class="sxs-lookup"><span data-stu-id="4420d-305">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="4420d-306">空間音效</span><span class="sxs-lookup"><span data-stu-id="4420d-306">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="4420d-307">空間對應</span><span class="sxs-lookup"><span data-stu-id="4420d-307">Spatial mapping</span></span>](spatial-mapping.md)
