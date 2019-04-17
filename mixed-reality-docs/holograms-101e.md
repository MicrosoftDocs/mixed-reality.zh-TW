---
title: MR 基本概念 101E-模擬器使用完整的專案
description: 遵循此程式碼逐步解說如何使用 Unity、 Visual Studio 和 HoloLens 模擬器，以了解全像攝影版的應用程式的基本概念。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: 混合的實境，Windows Mixed Reality、 HoloLens、 全像圖 academy，教學課程中，模擬器
ms.openlocfilehash: 77f7d497396937bf471a69fa514cef84ab0b699d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591575"
---
>[!NOTE]
><span data-ttu-id="5027d-104">混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。</span><span class="sxs-lookup"><span data-stu-id="5027d-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="5027d-105">因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。</span><span class="sxs-lookup"><span data-stu-id="5027d-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="5027d-106">這些教學課程會**_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="5027d-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="5027d-107">它們會繼續運作，支援的裝置上維護。</span><span class="sxs-lookup"><span data-stu-id="5027d-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="5027d-108">會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="5027d-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="5027d-109">當他們回傳時，本聲明將會更新這些教學課程的連結。</span><span class="sxs-lookup"><span data-stu-id="5027d-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a><span data-ttu-id="5027d-110">MR 基本概念 101E:模擬器使用完整的專案</span><span class="sxs-lookup"><span data-stu-id="5027d-110">MR Basics 101E: Complete project with emulator</span></span>

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

<span data-ttu-id="5027d-111">本教學課程將逐步引導您完成的專案，建置在 Unity 中，示範核心 Windows Mixed Reality 功能，包括 HoloLens[視線](gaze.md)，[筆勢](gestures.md)，[語音輸入](voice-input.md)，[空間音效](spatial-sound.md)並[空間對應](spatial-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="5027d-111">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze.md), [gestures](gestures.md), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span> <span data-ttu-id="5027d-112">本教學課程需要大約 1 小時才能完成。</span><span class="sxs-lookup"><span data-stu-id="5027d-112">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="5027d-113">裝置支援</span><span class="sxs-lookup"><span data-stu-id="5027d-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="5027d-114">課程</span><span class="sxs-lookup"><span data-stu-id="5027d-114">Course</span></span></th><th style="width:150px"> <span data-ttu-id="5027d-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="5027d-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="5027d-116"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="5027d-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="5027d-117">MR 基本概念 101E:模擬器使用完整的專案</span><span class="sxs-lookup"><span data-stu-id="5027d-117">MR Basics 101E: Complete project with emulator</span></span></td><td style="text-align: center;"> <span data-ttu-id="5027d-118">✔️</span><span class="sxs-lookup"><span data-stu-id="5027d-118">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="5027d-119">開始之前</span><span class="sxs-lookup"><span data-stu-id="5027d-119">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="5027d-120">必要條件</span><span class="sxs-lookup"><span data-stu-id="5027d-120">Prerequisites</span></span>

* <span data-ttu-id="5027d-121">Windows 10 電腦的正確設定[安裝工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="5027d-121">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

### <a name="project-files"></a><span data-ttu-id="5027d-122">專案檔</span><span class="sxs-lookup"><span data-stu-id="5027d-122">Project files</span></span>

* <span data-ttu-id="5027d-123">下載[檔案](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip)專案所需。</span><span class="sxs-lookup"><span data-stu-id="5027d-123">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="5027d-124"> 需要 Unity 2017.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="5027d-124"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="5027d-125">如果您仍然需要 Unity 5.6 的支援，請使用[本版](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="5027d-125">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="5027d-126">如果您仍然需要 Unity 5.5 的支援，請使用[本版](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="5027d-126">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="5027d-127">如果您仍然需要 Unity 5.4 的支援，請使用[本版](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="5027d-127">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="5027d-128">取消封存您的桌面或其他您輕鬆地連線到位置的檔案。</span><span class="sxs-lookup"><span data-stu-id="5027d-128">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="5027d-129">保留的資料夾名稱，作為**Origami**。</span><span class="sxs-lookup"><span data-stu-id="5027d-129">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="5027d-130">如果您想要查看原始程式碼，在下載之前，它有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)。</span><span class="sxs-lookup"><span data-stu-id="5027d-130">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="5027d-131">第 1 章-「 Holo"world</span><span class="sxs-lookup"><span data-stu-id="5027d-131">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

<span data-ttu-id="5027d-132">在本章中，我們將安裝程式，我們的第一個 Unity 專案並逐步執行組建和部署程序。</span><span class="sxs-lookup"><span data-stu-id="5027d-132">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="5027d-133">目標</span><span class="sxs-lookup"><span data-stu-id="5027d-133">Objectives</span></span>

* <span data-ttu-id="5027d-134">設定全像攝影版的開發環境 Unity。</span><span class="sxs-lookup"><span data-stu-id="5027d-134">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="5027d-135">請全像圖。</span><span class="sxs-lookup"><span data-stu-id="5027d-135">Make a hologram.</span></span>
* <span data-ttu-id="5027d-136">請參閱您所做的雷射。</span><span class="sxs-lookup"><span data-stu-id="5027d-136">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="5027d-137">指示</span><span class="sxs-lookup"><span data-stu-id="5027d-137">Instructions</span></span>

* <span data-ttu-id="5027d-138">啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="5027d-138">Start Unity.</span></span>
* <span data-ttu-id="5027d-139">選取 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="5027d-139">Select **Open**.</span></span>
* <span data-ttu-id="5027d-140">輸入與位置**Origami**資料夾您先前未封存。</span><span class="sxs-lookup"><span data-stu-id="5027d-140">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="5027d-141">選取  **Origami**然後按一下**選取資料夾**。</span><span class="sxs-lookup"><span data-stu-id="5027d-141">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="5027d-142">儲存新的場景：**檔案** / **儲存為場景**。</span><span class="sxs-lookup"><span data-stu-id="5027d-142">Save the new scene: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="5027d-143">命名場景**Origami**然後按**儲存** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5027d-143">Name the scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-camera"></a><span data-ttu-id="5027d-144">設定主攝影機</span><span class="sxs-lookup"><span data-stu-id="5027d-144">Setup the main camera</span></span>

* <span data-ttu-id="5027d-145">在 **階層面板**，選取**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="5027d-145">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="5027d-146">在  **Inspector**將其轉換位置設為**0,0,0**。</span><span class="sxs-lookup"><span data-stu-id="5027d-146">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="5027d-147">尋找**清除旗標**屬性，並將變更從下拉式清單中**天空盒**來**單色**。</span><span class="sxs-lookup"><span data-stu-id="5027d-147">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="5027d-148">按一下 **背景**欄位，以開啟色彩選擇器。</span><span class="sxs-lookup"><span data-stu-id="5027d-148">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="5027d-149">設定**R、 G、 B 和 A**要**0**。</span><span class="sxs-lookup"><span data-stu-id="5027d-149">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="5027d-150">設定場景</span><span class="sxs-lookup"><span data-stu-id="5027d-150">Setup the scene</span></span>

* <span data-ttu-id="5027d-151">在**階層面板**，按一下**建立**並**建立空**。</span><span class="sxs-lookup"><span data-stu-id="5027d-151">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="5027d-152">以滑鼠右鍵按一下 新**GameObject**並選取 重新命名。</span><span class="sxs-lookup"><span data-stu-id="5027d-152">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="5027d-153">重新命名以 GameObject **OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="5027d-153">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="5027d-154">從**全像投影**中的資料夾 **[專案] 面板**:</span><span class="sxs-lookup"><span data-stu-id="5027d-154">From the **Holograms** folder in the **Project Panel**:</span></span>
  * <span data-ttu-id="5027d-155">拖曳**階段**置於階層是子系**OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="5027d-155">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="5027d-156">拖曳**Sphere1**置於階層是子系**OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="5027d-156">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="5027d-157">拖曳**Sphere2**置於階層是子系**OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="5027d-157">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="5027d-158">以滑鼠右鍵按一下**定向光線**物件中**階層面板**，然後選取**刪除**。</span><span class="sxs-lookup"><span data-stu-id="5027d-158">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="5027d-159">從**全像投影**資料夾中，拖曳**燈**的根目錄**階層面板**。</span><span class="sxs-lookup"><span data-stu-id="5027d-159">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="5027d-160">在 **階層**，選取**OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="5027d-160">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="5027d-161">在  **Inspector**，將轉換的位置設為**0，-0.5，2.0**。</span><span class="sxs-lookup"><span data-stu-id="5027d-161">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="5027d-162">按下**播放**預覽您全像投影的 Unity 中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="5027d-162">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="5027d-163">您應該會看到 [預覽] 視窗中的 Origami 物件。</span><span class="sxs-lookup"><span data-stu-id="5027d-163">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="5027d-164">按下**播放**第二次停止 [預覽] 模式。</span><span class="sxs-lookup"><span data-stu-id="5027d-164">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="5027d-165">匯出從 Unity 專案，Visual studio</span><span class="sxs-lookup"><span data-stu-id="5027d-165">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="5027d-166">在 Unity 中，選取**檔案 > 組建設定**。</span><span class="sxs-lookup"><span data-stu-id="5027d-166">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="5027d-167">選取  **Windows 市集**中**平台**清單，然後按一下**切換平台**。</span><span class="sxs-lookup"><span data-stu-id="5027d-167">Select **Windows Store** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="5027d-168">設定**SDK**來**通用 10**並**建置型別**至**D3D**。</span><span class="sxs-lookup"><span data-stu-id="5027d-168">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="5027d-169">請檢查**UnityC#專案**。</span><span class="sxs-lookup"><span data-stu-id="5027d-169">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="5027d-170">按一下 **加入開啟的場景**加入場景。</span><span class="sxs-lookup"><span data-stu-id="5027d-170">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="5027d-171">按一下 **播放程式設定...**.</span><span class="sxs-lookup"><span data-stu-id="5027d-171">Click **Player Settings...**.</span></span>
* <span data-ttu-id="5027d-172">在偵測器窗格中選取**Windows 市集標誌**。</span><span class="sxs-lookup"><span data-stu-id="5027d-172">In the Inspector Panel select the **Windows Store logo**.</span></span> <span data-ttu-id="5027d-173">然後選取**發佈設定**。</span><span class="sxs-lookup"><span data-stu-id="5027d-173">Then select **Publishing Settings**.</span></span>
* <span data-ttu-id="5027d-174">在 **能力**區段中，選取**麥克風**並**SpatialPerception**功能。</span><span class="sxs-lookup"><span data-stu-id="5027d-174">In the **Capabilities** section, select the **Microphone** and **SpatialPerception** capabilities.</span></span>
* <span data-ttu-id="5027d-175">在 [組建設定] 視窗中，按一下**建置**。</span><span class="sxs-lookup"><span data-stu-id="5027d-175">Back in the Build Settings window, click **Build**.</span></span>
* <span data-ttu-id="5027d-176">建立**新的資料夾**名為 「 應用程式 」。</span><span class="sxs-lookup"><span data-stu-id="5027d-176">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="5027d-177">只要按一下**應用程式資料夾**。</span><span class="sxs-lookup"><span data-stu-id="5027d-177">Single click the **App Folder**.</span></span>
* <span data-ttu-id="5027d-178">按下**選取資料夾**。</span><span class="sxs-lookup"><span data-stu-id="5027d-178">Press **Select Folder**.</span></span>
* <span data-ttu-id="5027d-179">Unity 完成時，會出現檔案總管 視窗。</span><span class="sxs-lookup"><span data-stu-id="5027d-179">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="5027d-180">開啟**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="5027d-180">Open the **App** folder.</span></span>
* <span data-ttu-id="5027d-181">開啟**Origami Visual Studio 方案**。</span><span class="sxs-lookup"><span data-stu-id="5027d-181">Open the **Origami Visual Studio Solution**.</span></span>
* <span data-ttu-id="5027d-182">使用頂端的工具列，在 Visual Studio 中，從 偵錯，若要變更目標**Release**進出至 ARM **X86**。</span><span class="sxs-lookup"><span data-stu-id="5027d-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
  * <span data-ttu-id="5027d-183">按一下 [裝置] 按鈕旁邊的箭號，然後選取**HoloLens 模擬器**。</span><span class="sxs-lookup"><span data-stu-id="5027d-183">Click on the arrow next to the Device button, and select **HoloLens Emulator**.</span></span>
  * <span data-ttu-id="5027d-184">按一下 **偵錯-> 啟動但不偵錯**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="5027d-184">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
  * <span data-ttu-id="5027d-185">稍後 Origami 專案會啟動模擬器。</span><span class="sxs-lookup"><span data-stu-id="5027d-185">After some time the emulator will start with the Origami project.</span></span> <span data-ttu-id="5027d-186">當您第一次啟動時[模擬器](using-the-hololens-emulator.md)，可能需要長達 15 分鐘啟動模擬器。</span><span class="sxs-lookup"><span data-stu-id="5027d-186">When first launching the [emulator](using-the-hololens-emulator.md), it can take as long as 15 minutes for the emulator to start up.</span></span> <span data-ttu-id="5027d-187">它會啟動一次，不會將它關閉。</span><span class="sxs-lookup"><span data-stu-id="5027d-187">Once it starts, do not close it.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="5027d-188">第 2 章-視線</span><span class="sxs-lookup"><span data-stu-id="5027d-188">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

<span data-ttu-id="5027d-189">在本章中，我們即將引入互動的三種方法的第一個與您全像投影-[視線](gaze.md)。</span><span class="sxs-lookup"><span data-stu-id="5027d-189">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="5027d-190">目標</span><span class="sxs-lookup"><span data-stu-id="5027d-190">Objectives</span></span>

* <span data-ttu-id="5027d-191">以視覺化方式檢視您的視線使用全球鎖定的資料指標。</span><span class="sxs-lookup"><span data-stu-id="5027d-191">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="5027d-192">指示</span><span class="sxs-lookup"><span data-stu-id="5027d-192">Instructions</span></span>

* <span data-ttu-id="5027d-193">返回您的 Unity 專案，並關閉 [建立設定] 視窗，它是否仍保持開啟。</span><span class="sxs-lookup"><span data-stu-id="5027d-193">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="5027d-194">選取 **全像投影**中的資料夾**專案 面板**。</span><span class="sxs-lookup"><span data-stu-id="5027d-194">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="5027d-195">拖曳**游標**物件插入**階層面板**根層級。</span><span class="sxs-lookup"><span data-stu-id="5027d-195">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="5027d-196">按兩下**游標**才會仔細看看它的物件。</span><span class="sxs-lookup"><span data-stu-id="5027d-196">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="5027d-197">以滑鼠右鍵按一下**指令碼**專案 面板中的資料夾。</span><span class="sxs-lookup"><span data-stu-id="5027d-197">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="5027d-198">按一下 **建立**子功能表。</span><span class="sxs-lookup"><span data-stu-id="5027d-198">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="5027d-199">選取   **C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="5027d-199">Select **C# Script**.</span></span>
* <span data-ttu-id="5027d-200">指令碼命名**WorldCursor**。</span><span class="sxs-lookup"><span data-stu-id="5027d-200">Name the script **WorldCursor**.</span></span> <span data-ttu-id="5027d-201">注意：此名稱區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="5027d-201">Note: The name is case-sensitive.</span></span> <span data-ttu-id="5027d-202">您不需要將.cs 副檔名。</span><span class="sxs-lookup"><span data-stu-id="5027d-202">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="5027d-203">選取 **游標**物件中**階層面板**。</span><span class="sxs-lookup"><span data-stu-id="5027d-203">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="5027d-204">將拖放**WorldCursor**編寫成指令碼**Inspector 面板**。</span><span class="sxs-lookup"><span data-stu-id="5027d-204">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="5027d-205">按兩下**WorldCursor**指令碼，以在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="5027d-205">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="5027d-206">複製並貼上此程式碼**WorldCursor.cs**並**全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="5027d-206">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

* <span data-ttu-id="5027d-207">重建的應用程式**檔案 > 組建設定**。</span><span class="sxs-lookup"><span data-stu-id="5027d-207">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="5027d-208">返回 Visual Studio 方案先前用來部署至模擬器。</span><span class="sxs-lookup"><span data-stu-id="5027d-208">Return to the Visual Studio solution previously used to deploy to the emulator.</span></span>
* <span data-ttu-id="5027d-209">選取 [重新載入全部] 出現提示時。</span><span class="sxs-lookup"><span data-stu-id="5027d-209">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="5027d-210">按一下 **偵錯-> 啟動但不偵錯**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="5027d-210">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="5027d-211">您可以使用 Xbox 控制器場景看一下。</span><span class="sxs-lookup"><span data-stu-id="5027d-211">Use the Xbox controller to look around the scene.</span></span> <span data-ttu-id="5027d-212">請注意，資料指標的形狀之物件的互動方式。</span><span class="sxs-lookup"><span data-stu-id="5027d-212">Notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="5027d-213">第 3 章-筆勢</span><span class="sxs-lookup"><span data-stu-id="5027d-213">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

<span data-ttu-id="5027d-214">在本章中，我們將新增的支援[筆勢](gestures.md)。</span><span class="sxs-lookup"><span data-stu-id="5027d-214">In this chapter, we'll add support for [gestures](gestures.md).</span></span> <span data-ttu-id="5027d-215">當使用者選取的紙張球體時，我們要藉由開啟重力使用 Unity 的物理條件引擎落球體。</span><span class="sxs-lookup"><span data-stu-id="5027d-215">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="5027d-216">目標</span><span class="sxs-lookup"><span data-stu-id="5027d-216">Objectives</span></span>

* <span data-ttu-id="5027d-217">控制您全像投影與選取的筆勢。</span><span class="sxs-lookup"><span data-stu-id="5027d-217">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="5027d-218">指示</span><span class="sxs-lookup"><span data-stu-id="5027d-218">Instructions</span></span>

<span data-ttu-id="5027d-219">我們先建立指令碼，比可以偵測到選取的筆勢。</span><span class="sxs-lookup"><span data-stu-id="5027d-219">We'll start by creating a script than can detect the Select gesture.</span></span>

* <span data-ttu-id="5027d-220">在 **指令碼**資料夾中，建立名為指令碼**GazeGestureManager**。</span><span class="sxs-lookup"><span data-stu-id="5027d-220">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="5027d-221">拖曳**GazeGestureManager**拖曳至指令碼**OrigamiCollection**階層中的物件。</span><span class="sxs-lookup"><span data-stu-id="5027d-221">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="5027d-222">開啟**GazeGestureManager**指令碼在 Visual Studio 中，並新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="5027d-222">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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

* <span data-ttu-id="5027d-223">建立另一個指令碼，在 [指令碼] 資料夾中，這次是名為**SphereCommands**。</span><span class="sxs-lookup"><span data-stu-id="5027d-223">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="5027d-224">依序展開**OrigamiCollection**階層檢視中的物件。</span><span class="sxs-lookup"><span data-stu-id="5027d-224">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="5027d-225">拖曳**SphereCommands**拖曳至指令碼**Sphere1**在階層窗格中的物件。</span><span class="sxs-lookup"><span data-stu-id="5027d-225">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="5027d-226">拖曳**SphereCommands**拖曳至指令碼**Sphere2**在階層窗格中的物件。</span><span class="sxs-lookup"><span data-stu-id="5027d-226">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="5027d-227">在 Visual Studio 中開啟指令碼進行編輯，並以此取代預設的程式碼：</span><span class="sxs-lookup"><span data-stu-id="5027d-227">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="5027d-228">匯出、 建置及部署應用程式到 HoloLens 模擬器。</span><span class="sxs-lookup"><span data-stu-id="5027d-228">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="5027d-229">場景，請看一下，球體看起來的其中一個上置中對齊。</span><span class="sxs-lookup"><span data-stu-id="5027d-229">Look around the scene, and center on one of the spheres.</span></span>
* <span data-ttu-id="5027d-230">按下**A** Xbox 控制器按鈕或按下空格鍵來模擬選取的筆勢。</span><span class="sxs-lookup"><span data-stu-id="5027d-230">Press the **A** button on the Xbox controller or press the Spacebar to simulate the Select gesture.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="5027d-231">第 4 章-語音</span><span class="sxs-lookup"><span data-stu-id="5027d-231">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

<span data-ttu-id="5027d-232">在本章中，我們將新增兩個支援[語音命令](voice-input.md):「 重設的 world 」 來傳回的已卸除到其原始位置，不過這個觀念與 「 卸除 sphere 」 進行切換的球體。</span><span class="sxs-lookup"><span data-stu-id="5027d-232">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to returns the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="5027d-233">目標</span><span class="sxs-lookup"><span data-stu-id="5027d-233">Objectives</span></span>

* <span data-ttu-id="5027d-234">在背景中新增 alwayson 接聽的語音命令。</span><span class="sxs-lookup"><span data-stu-id="5027d-234">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="5027d-235">建立回應語音命令全像圖。</span><span class="sxs-lookup"><span data-stu-id="5027d-235">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="5027d-236">指示</span><span class="sxs-lookup"><span data-stu-id="5027d-236">Instructions</span></span>

* <span data-ttu-id="5027d-237">在 **指令碼**資料夾中，建立名為指令碼**SpeechManager**。</span><span class="sxs-lookup"><span data-stu-id="5027d-237">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="5027d-238">拖曳**SpeechManager**拖曳至指令碼**OrigamiCollection**階層中的物件</span><span class="sxs-lookup"><span data-stu-id="5027d-238">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="5027d-239">開啟**SpeechManager** Visual Studio 中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="5027d-239">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="5027d-240">複製並貼上此程式碼**SpeechManager.cs**並**全部儲存**:</span><span class="sxs-lookup"><span data-stu-id="5027d-240">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="5027d-241">開啟**SphereCommands** Visual Studio 中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="5027d-241">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="5027d-242">更新指令碼來讀取，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5027d-242">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="5027d-243">匯出、 建置及部署應用程式到 HoloLens 模擬器。</span><span class="sxs-lookup"><span data-stu-id="5027d-243">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="5027d-244">模擬器會支援您的電腦的麥克風及語音回應： 調整檢視，使資料指標是其中一個球體看起來，並假設 「 卸除 Sphere 」。</span><span class="sxs-lookup"><span data-stu-id="5027d-244">The emulator will support your PC's microphone and respond to your voice: adjust the view so the cursor is on one of the spheres, and say "Drop Sphere".</span></span>
* <span data-ttu-id="5027d-245">說出 「**重設的世界**「 若要將它們回復到其初始位置。</span><span class="sxs-lookup"><span data-stu-id="5027d-245">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="5027d-246">第 5 章-空間的音效</span><span class="sxs-lookup"><span data-stu-id="5027d-246">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

<span data-ttu-id="5027d-247">在本章中，我們會將音樂新增至應用程式，並接著觸發特定動作的音效。</span><span class="sxs-lookup"><span data-stu-id="5027d-247">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="5027d-248">我們將使用[空間音效](spatial-sound.md)讓音效在 3D 空間中的特定位置。</span><span class="sxs-lookup"><span data-stu-id="5027d-248">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="5027d-249">目標</span><span class="sxs-lookup"><span data-stu-id="5027d-249">Objectives</span></span>

* <span data-ttu-id="5027d-250">聽聽您的世界中全像投影。</span><span class="sxs-lookup"><span data-stu-id="5027d-250">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="5027d-251">指示</span><span class="sxs-lookup"><span data-stu-id="5027d-251">Instructions</span></span>

* <span data-ttu-id="5027d-252">在頂端功能表中 Unity 選取**編輯 > 專案設定 > 音訊**</span><span class="sxs-lookup"><span data-stu-id="5027d-252">In the Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="5027d-253">尋找**空間外掛程式**設定，然後選取**MS HRTF 空間**。</span><span class="sxs-lookup"><span data-stu-id="5027d-253">Find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="5027d-254">從**全像投影**資料夾中，拖曳**環境**物件拖曳至**OrigamiCollection**在階層窗格中的物件。</span><span class="sxs-lookup"><span data-stu-id="5027d-254">From the **Holograms** folder, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="5027d-255">選取  **OrigamiCollection**並尋找**音訊來源**元件。</span><span class="sxs-lookup"><span data-stu-id="5027d-255">Select **OrigamiCollection** and find the **Audio Source** component.</span></span> <span data-ttu-id="5027d-256">變更這些屬性：</span><span class="sxs-lookup"><span data-stu-id="5027d-256">Change these properties:</span></span>
  * <span data-ttu-id="5027d-257">請檢查**Spatialize**屬性。</span><span class="sxs-lookup"><span data-stu-id="5027d-257">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="5027d-258">請檢查**甦醒狀態上播放**。</span><span class="sxs-lookup"><span data-stu-id="5027d-258">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="5027d-259">變更**空間 Blend**要**3D**拖曳到最右邊的滑桿。</span><span class="sxs-lookup"><span data-stu-id="5027d-259">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span>
  * <span data-ttu-id="5027d-260">請檢查**迴圈**屬性。</span><span class="sxs-lookup"><span data-stu-id="5027d-260">Check the **Loop** property.</span></span>
  * <span data-ttu-id="5027d-261">依序展開**3D 音效設定**，並輸入**0.1** for **Doppler 層級**。</span><span class="sxs-lookup"><span data-stu-id="5027d-261">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="5027d-262">設定**磁碟區捲繞**要**對數捲繞**。</span><span class="sxs-lookup"><span data-stu-id="5027d-262">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="5027d-263">設定**最大距離**要**20**。</span><span class="sxs-lookup"><span data-stu-id="5027d-263">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="5027d-264">在 **指令碼**資料夾中，建立名為指令碼**SphereSounds**。</span><span class="sxs-lookup"><span data-stu-id="5027d-264">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="5027d-265">拖曳**SphereSounds**要**Sphere1**並**Sphere2**階層中的物件。</span><span class="sxs-lookup"><span data-stu-id="5027d-265">Drag **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="5027d-266">開啟**SphereSounds**在 Visual Studio 中，更新下列程式碼並**全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="5027d-266">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="5027d-267">儲存指令碼，並返回到 Unity。</span><span class="sxs-lookup"><span data-stu-id="5027d-267">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="5027d-268">匯出、 建置及部署應用程式到 HoloLens 模擬器。</span><span class="sxs-lookup"><span data-stu-id="5027d-268">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="5027d-269">戴上耳機來取得完整的效果，並移動以及接近更聽到任何聲音變更的階段。</span><span class="sxs-lookup"><span data-stu-id="5027d-269">Wear headphones to get the full effect, and move closer and further from the Stage to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="5027d-270">第 6 章-空間對應</span><span class="sxs-lookup"><span data-stu-id="5027d-270">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

<span data-ttu-id="5027d-271">現在我們將使用[空間對應](spatial-mapping.md)放置在真實世界的真實物件上的遊戲面板。</span><span class="sxs-lookup"><span data-stu-id="5027d-271">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="5027d-272">目標</span><span class="sxs-lookup"><span data-stu-id="5027d-272">Objectives</span></span>

* <span data-ttu-id="5027d-273">虛擬世界中帶入您真實的世界。</span><span class="sxs-lookup"><span data-stu-id="5027d-273">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="5027d-274">將您全像投影，在您最感興趣。</span><span class="sxs-lookup"><span data-stu-id="5027d-274">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="5027d-275">指示</span><span class="sxs-lookup"><span data-stu-id="5027d-275">Instructions</span></span>

* <span data-ttu-id="5027d-276">按一下 [**全像投影**專案] 面板中的資料夾。</span><span class="sxs-lookup"><span data-stu-id="5027d-276">Click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="5027d-277">拖曳**空間的對應**資產的根目錄**階層**。</span><span class="sxs-lookup"><span data-stu-id="5027d-277">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="5027d-278">按一下 **空間對應**階層中的物件。</span><span class="sxs-lookup"><span data-stu-id="5027d-278">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="5027d-279">在  **Inspector 面板**，變更下列屬性：</span><span class="sxs-lookup"><span data-stu-id="5027d-279">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="5027d-280">請檢查**繪製視覺網狀結構** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="5027d-280">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="5027d-281">找出**繪製的材質**按一下右側的圓形。</span><span class="sxs-lookup"><span data-stu-id="5027d-281">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="5027d-282">類型"**線框**」 到頂端的 [搜尋] 欄位。</span><span class="sxs-lookup"><span data-stu-id="5027d-282">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="5027d-283">按一下結果，然後關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="5027d-283">Click on the result and then close the window.</span></span>
* <span data-ttu-id="5027d-284">匯出、 建置及部署應用程式到 HoloLens 模擬器。</span><span class="sxs-lookup"><span data-stu-id="5027d-284">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="5027d-285">應用程式執行時，框線會呈現先前掃描的真實世界客廳的網狀結構。</span><span class="sxs-lookup"><span data-stu-id="5027d-285">When the app runs, a mesh of a previously scanned real-world living room will be rendered in wireframe.</span></span>
* <span data-ttu-id="5027d-286">觀看如何輪流球體會切換關閉階段，並送至最低限度值 ！</span><span class="sxs-lookup"><span data-stu-id="5027d-286">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="5027d-287">現在要教您如何將 OrigamiCollection 移至新的位置：</span><span class="sxs-lookup"><span data-stu-id="5027d-287">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="5027d-288">在 **指令碼**資料夾中，建立名為指令碼**TapToPlaceParent**。</span><span class="sxs-lookup"><span data-stu-id="5027d-288">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="5027d-289">在 **階層**，展開**OrigamiCollection** ，然後選取**階段**物件。</span><span class="sxs-lookup"><span data-stu-id="5027d-289">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="5027d-290">拖曳**TapToPlaceParent**階段物件的指令碼。</span><span class="sxs-lookup"><span data-stu-id="5027d-290">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="5027d-291">開啟**TapToPlaceParent**指令碼在 Visual Studio 中，並將它有下列更新：</span><span class="sxs-lookup"><span data-stu-id="5027d-291">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="5027d-292">匯出、 建置和部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="5027d-292">Export, build and deploy the app.</span></span>
* <span data-ttu-id="5027d-293">您現在應該能夠在它 gazing 將遊戲置於特定位置，現在使用選取的動作 (**A**或空格鍵)，移至新的位置，然後再次使用選取的筆勢。</span><span class="sxs-lookup"><span data-stu-id="5027d-293">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture (**A** or Spacebar) and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="the-end"></a><span data-ttu-id="5027d-294">結束</span><span class="sxs-lookup"><span data-stu-id="5027d-294">The end</span></span>

<span data-ttu-id="5027d-295">而且，本教學課程結束 ！</span><span class="sxs-lookup"><span data-stu-id="5027d-295">And that's the end of this tutorial!</span></span>

<span data-ttu-id="5027d-296">您已了解：</span><span class="sxs-lookup"><span data-stu-id="5027d-296">You learned:</span></span>

* <span data-ttu-id="5027d-297">如何建立在 Unity 的全像攝影版的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5027d-297">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="5027d-298">如何使用凝視、 手勢、 語音、 音效及空間對應。</span><span class="sxs-lookup"><span data-stu-id="5027d-298">How to make use of gaze, gesture, voice, sounds, and spatial mapping.</span></span>
* <span data-ttu-id="5027d-299">如何建置和部署使用 Visual Studio 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5027d-299">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="5027d-300">您現在已準備好要開始建立您自己全像攝影版的應用程式 ！</span><span class="sxs-lookup"><span data-stu-id="5027d-300">You are now ready to start creating your own holographic apps!</span></span>

## <a name="see-also"></a><span data-ttu-id="5027d-301">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5027d-301">See also</span></span>

* [<span data-ttu-id="5027d-302">MR 101 基本知識：完整的專案，與裝置</span><span class="sxs-lookup"><span data-stu-id="5027d-302">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="5027d-303">Gaze</span><span class="sxs-lookup"><span data-stu-id="5027d-303">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="5027d-304">筆勢</span><span class="sxs-lookup"><span data-stu-id="5027d-304">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="5027d-305">語音輸入</span><span class="sxs-lookup"><span data-stu-id="5027d-305">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="5027d-306">空間的音效</span><span class="sxs-lookup"><span data-stu-id="5027d-306">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="5027d-307">空間對應</span><span class="sxs-lookup"><span data-stu-id="5027d-307">Spatial mapping</span></span>](spatial-mapping.md)
