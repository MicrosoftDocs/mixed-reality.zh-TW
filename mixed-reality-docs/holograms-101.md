---
title: MR 基本概念 101-與裝置的完整專案
description: 請遵循此程式碼撰寫的逐步解說，使用 Unity、 Visual Studio 和 HoloLens，若要了解 Windows Mixed Reality 的基本概念。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: 混合實境，Windows Mixed Reality、 HoloLens、 全像圖、 academy、 教學課程
ms.openlocfilehash: 043ffac8f30a4e29586478b5dca6ecccc2b5afd3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591556"
---
>[!NOTE]
><span data-ttu-id="e36ed-104">混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。</span><span class="sxs-lookup"><span data-stu-id="e36ed-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="e36ed-105">因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。</span><span class="sxs-lookup"><span data-stu-id="e36ed-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="e36ed-106">這些教學課程會**_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="e36ed-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="e36ed-107">它們會繼續運作，支援的裝置上維護。</span><span class="sxs-lookup"><span data-stu-id="e36ed-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="e36ed-108">會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="e36ed-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="e36ed-109">當他們回傳時，本聲明將會更新這些教學課程的連結。</span><span class="sxs-lookup"><span data-stu-id="e36ed-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-101-complete-project-with-device"></a><span data-ttu-id="e36ed-110">MR 101 基本知識：完整的專案，與裝置</span><span class="sxs-lookup"><span data-stu-id="e36ed-110">MR Basics 101: Complete project with device</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

<span data-ttu-id="e36ed-111">本教學課程將逐步引導您完成的專案，建置在 Unity 中，示範核心 Windows Mixed Reality 功能，包括 HoloLens[視線](gaze.md)，[筆勢](gestures.md)，[語音輸入](voice-input.md)，[空間音效](spatial-sound.md)並[空間對應](spatial-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="e36ed-111">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze.md), [gestures](gestures.md), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span>

<span data-ttu-id="e36ed-112">本教學課程需要大約 1 小時才能完成。</span><span class="sxs-lookup"><span data-stu-id="e36ed-112">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="e36ed-113">裝置支援</span><span class="sxs-lookup"><span data-stu-id="e36ed-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="e36ed-114">課程</span><span class="sxs-lookup"><span data-stu-id="e36ed-114">Course</span></span></th><th style="width:150px"> <span data-ttu-id="e36ed-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="e36ed-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="e36ed-116"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="e36ed-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="e36ed-117">MR 101 基本知識：完整的專案，與裝置</span><span class="sxs-lookup"><span data-stu-id="e36ed-117">MR Basics 101: Complete project with device</span></span></td><td style="text-align: center;"> <span data-ttu-id="e36ed-118">✔️</span><span class="sxs-lookup"><span data-stu-id="e36ed-118">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="e36ed-119">開始之前</span><span class="sxs-lookup"><span data-stu-id="e36ed-119">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="e36ed-120">先決條件</span><span class="sxs-lookup"><span data-stu-id="e36ed-120">Prerequisites</span></span>

* <span data-ttu-id="e36ed-121">Windows 10 電腦的正確設定[安裝工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="e36ed-121">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="e36ed-122">HoloLens 裝置[開發設定的](using-visual-studio.md#enabling-developer-mode)。</span><span class="sxs-lookup"><span data-stu-id="e36ed-122">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="e36ed-123">專案檔</span><span class="sxs-lookup"><span data-stu-id="e36ed-123">Project files</span></span>

* <span data-ttu-id="e36ed-124">下載[檔案](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip)專案所需。</span><span class="sxs-lookup"><span data-stu-id="e36ed-124">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="e36ed-125"> 需要 Unity 2017.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="e36ed-125"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="e36ed-126">如果您仍然需要 Unity 5.6 的支援，請使用[本版](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="e36ed-126">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="e36ed-127">如果您仍然需要 Unity 5.5 的支援，請使用[本版](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="e36ed-127">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="e36ed-128">如果您仍然需要 Unity 5.4 的支援，請使用[本版](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="e36ed-128">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="e36ed-129">取消封存您的桌面或其他您輕鬆地連線到位置的檔案。</span><span class="sxs-lookup"><span data-stu-id="e36ed-129">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="e36ed-130">保留的資料夾名稱，作為**Origami**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-130">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="e36ed-131">如果您想要查看原始程式碼，在下載之前，它有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)。</span><span class="sxs-lookup"><span data-stu-id="e36ed-131">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="e36ed-132">第 1 章-「 Holo"world</span><span class="sxs-lookup"><span data-stu-id="e36ed-132">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

<span data-ttu-id="e36ed-133">在本章中，我們將安裝程式，我們的第一個 Unity 專案並逐步執行組建和部署程序。</span><span class="sxs-lookup"><span data-stu-id="e36ed-133">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="e36ed-134">目標</span><span class="sxs-lookup"><span data-stu-id="e36ed-134">Objectives</span></span>

* <span data-ttu-id="e36ed-135">設定全像攝影版的開發環境 Unity。</span><span class="sxs-lookup"><span data-stu-id="e36ed-135">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="e36ed-136">請全像圖。</span><span class="sxs-lookup"><span data-stu-id="e36ed-136">Make a hologram.</span></span>
* <span data-ttu-id="e36ed-137">請參閱您所做的雷射。</span><span class="sxs-lookup"><span data-stu-id="e36ed-137">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="e36ed-138">指示</span><span class="sxs-lookup"><span data-stu-id="e36ed-138">Instructions</span></span>

* <span data-ttu-id="e36ed-139">啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="e36ed-139">Start Unity.</span></span>
* <span data-ttu-id="e36ed-140">選取 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-140">Select **Open**.</span></span>
* <span data-ttu-id="e36ed-141">輸入與位置**Origami**資料夾您先前未封存。</span><span class="sxs-lookup"><span data-stu-id="e36ed-141">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="e36ed-142">選取  **Origami**然後按一下**選取資料夾**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-142">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="e36ed-143">由於**Origami**專案未包含場景，儲存新的檔案使用空的預設場景：**檔案** / **儲存為場景**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-143">Since the **Origami** project does not contain a scene, save the empty default scene to a new file using: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="e36ed-144">命名新的場景**Origami**然後按**儲存** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e36ed-144">Name the new scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-virtual-camera"></a><span data-ttu-id="e36ed-145">安裝程式主要的虛擬觀景窗</span><span class="sxs-lookup"><span data-stu-id="e36ed-145">Setup the main virtual camera</span></span>

* <span data-ttu-id="e36ed-146">在 **階層面板**，選取**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-146">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="e36ed-147">在  **Inspector**將其轉換位置設為**0,0,0**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-147">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="e36ed-148">尋找**清除旗標**屬性，並將變更從下拉式清單中**天空盒**來**單色**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-148">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="e36ed-149">按一下 **背景**欄位，以開啟色彩選擇器。</span><span class="sxs-lookup"><span data-stu-id="e36ed-149">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="e36ed-150">設定**R、 G、 B 和 A**要**0**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-150">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="e36ed-151">設定場景</span><span class="sxs-lookup"><span data-stu-id="e36ed-151">Setup the scene</span></span>

* <span data-ttu-id="e36ed-152">在**階層面板**，按一下**建立**並**建立空**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-152">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="e36ed-153">以滑鼠右鍵按一下 新**GameObject**並選取 重新命名。</span><span class="sxs-lookup"><span data-stu-id="e36ed-153">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="e36ed-154">重新命名以 GameObject **OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-154">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="e36ed-155">從**全像投影**專案] 面板中的資料夾 （展開資產，並選取 [全像投影或按兩下 [專案] 面板中的 [全像投影] 資料夾）：</span><span class="sxs-lookup"><span data-stu-id="e36ed-155">From the **Holograms** folder in the Project Panel (expand Assets and select Holograms or double click the Holograms folder in the Project Panel):</span></span>
  * <span data-ttu-id="e36ed-156">拖曳**階段**置於階層是子系**OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-156">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="e36ed-157">拖曳**Sphere1**置於階層是子系**OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-157">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="e36ed-158">拖曳**Sphere2**置於階層是子系**OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-158">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="e36ed-159">以滑鼠右鍵按一下**定向光線**物件中**階層面板**，然後選取**刪除**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-159">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="e36ed-160">從**全像投影**資料夾中，拖曳**燈**的根目錄**階層面板**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-160">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="e36ed-161">在 **階層**，選取**OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-161">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="e36ed-162">在  **Inspector**，將轉換的位置設為**0，-0.5，2.0**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-162">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="e36ed-163">按下**播放**預覽您全像投影的 Unity 中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="e36ed-163">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="e36ed-164">您應該會看到 [預覽] 視窗中的 Origami 物件。</span><span class="sxs-lookup"><span data-stu-id="e36ed-164">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="e36ed-165">按下**播放**第二次停止 [預覽] 模式。</span><span class="sxs-lookup"><span data-stu-id="e36ed-165">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="e36ed-166">匯出從 Unity 專案，Visual studio</span><span class="sxs-lookup"><span data-stu-id="e36ed-166">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="e36ed-167">在 Unity 中，選取**檔案 > 組建設定**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-167">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="e36ed-168">選取 **通用 Windows 平台**中**平台**清單，然後按一下**切換平台**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-168">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="e36ed-169">設定**SDK**來**通用 10**並**建置型別**至**D3D**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-169">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="e36ed-170">請檢查**UnityC#專案**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-170">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="e36ed-171">按一下 **加入開啟的場景**加入場景。</span><span class="sxs-lookup"><span data-stu-id="e36ed-171">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="e36ed-172">按一下 [建置] 。</span><span class="sxs-lookup"><span data-stu-id="e36ed-172">Click **Build**.</span></span>
* <span data-ttu-id="e36ed-173">在出現的 [檔案總管] 視窗，建立**新的資料夾**名為 「 應用程式 」。</span><span class="sxs-lookup"><span data-stu-id="e36ed-173">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="e36ed-174">只要按一下**應用程式資料夾**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-174">Single click the **App Folder**.</span></span>
* <span data-ttu-id="e36ed-175">按下**選取資料夾**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-175">Press **Select Folder**.</span></span>
* <span data-ttu-id="e36ed-176">Unity 完成時，會出現檔案總管 視窗。</span><span class="sxs-lookup"><span data-stu-id="e36ed-176">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="e36ed-177">開啟**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="e36ed-177">Open the **App** folder.</span></span>
* <span data-ttu-id="e36ed-178">（按兩下） 開放**Origami.sln**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-178">Open (double click) **Origami.sln**.</span></span>
* <span data-ttu-id="e36ed-179">使用頂端的工具列，在 Visual Studio 中，從 偵錯，若要變更目標**Release**進出至 ARM **X86**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-179">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="e36ed-180">按一下 [裝置] 按鈕旁邊的箭號，然後選取**遠端機器**透過 Wi-fi 部署。</span><span class="sxs-lookup"><span data-stu-id="e36ed-180">Click on the arrow next to the Device button, and select **Remote Machine** to deploy over Wi-Fi.</span></span>
  * <span data-ttu-id="e36ed-181">設定**地址**的名稱或 IP 位址的您 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e36ed-181">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="e36ed-182">如果您不知道您的裝置 IP 位址，查看**設定 > 網路和網際網路 > 進階選項**詢問 Cortana 或 **「 嘿 Cortana，我的 IP 位址是什麼？ 」**</span><span class="sxs-lookup"><span data-stu-id="e36ed-182">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
  * <span data-ttu-id="e36ed-183">如果透過 USB 連接的 HoloLens，可能會改為選取**裝置**透過 USB 進行部署。</span><span class="sxs-lookup"><span data-stu-id="e36ed-183">If the HoloLens is attached over USB, you may instead select **Device** to deploy over USB.</span></span>
  * <span data-ttu-id="e36ed-184">離開**驗證模式**設為**通用**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-184">Leave the **Authentication Mode** set to **Universal**.</span></span>
  * <span data-ttu-id="e36ed-185">按一下 **選取**</span><span class="sxs-lookup"><span data-stu-id="e36ed-185">Click **Select**</span></span>

* <span data-ttu-id="e36ed-186">按一下 **偵錯 > 啟動但不偵錯**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-186">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="e36ed-187">如果這是第一次部署到您的裝置，您必須[與 Visual Studio 中配對](using-visual-studio.md#pairing-your-device-hololens-(1st-gen))。</span><span class="sxs-lookup"><span data-stu-id="e36ed-187">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens-(1st-gen)).</span></span>

* <span data-ttu-id="e36ed-188">Origami 專案將立即建置、 部署到您的 HoloLens，然後再執行。</span><span class="sxs-lookup"><span data-stu-id="e36ed-188">The Origami project will now build, deploy to your HoloLens, and then run.</span></span>
* <span data-ttu-id="e36ed-189">將放在您的 HoloLens 上，若要查看您新全像投影看一下。</span><span class="sxs-lookup"><span data-stu-id="e36ed-189">Put on your HoloLens and look around to see your new holograms.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="e36ed-190">第 2 章-視線</span><span class="sxs-lookup"><span data-stu-id="e36ed-190">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

<span data-ttu-id="e36ed-191">在本章中，我們即將引入互動的三種方法的第一個與您全像投影-[視線](gaze.md)。</span><span class="sxs-lookup"><span data-stu-id="e36ed-191">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="e36ed-192">目標</span><span class="sxs-lookup"><span data-stu-id="e36ed-192">Objectives</span></span>

* <span data-ttu-id="e36ed-193">以視覺化方式檢視您的視線使用全球鎖定的資料指標。</span><span class="sxs-lookup"><span data-stu-id="e36ed-193">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="e36ed-194">指示</span><span class="sxs-lookup"><span data-stu-id="e36ed-194">Instructions</span></span>

* <span data-ttu-id="e36ed-195">返回您的 Unity 專案，並關閉 [建立設定] 視窗，它是否仍保持開啟。</span><span class="sxs-lookup"><span data-stu-id="e36ed-195">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="e36ed-196">選取 **全像投影**中的資料夾**專案 面板**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-196">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="e36ed-197">拖曳**游標**物件插入**階層面板**根層級。</span><span class="sxs-lookup"><span data-stu-id="e36ed-197">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="e36ed-198">按兩下**游標**才會仔細看看它的物件。</span><span class="sxs-lookup"><span data-stu-id="e36ed-198">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="e36ed-199">以滑鼠右鍵按一下**指令碼**專案 面板中的資料夾。</span><span class="sxs-lookup"><span data-stu-id="e36ed-199">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="e36ed-200">按一下 **建立**子功能表。</span><span class="sxs-lookup"><span data-stu-id="e36ed-200">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="e36ed-201">選取   **C#指令碼**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-201">Select **C# Script**.</span></span>
* <span data-ttu-id="e36ed-202">指令碼命名**WorldCursor**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-202">Name the script **WorldCursor**.</span></span> <span data-ttu-id="e36ed-203">注意：此名稱區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="e36ed-203">Note: The name is case-sensitive.</span></span> <span data-ttu-id="e36ed-204">您不需要將.cs 副檔名。</span><span class="sxs-lookup"><span data-stu-id="e36ed-204">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="e36ed-205">選取 **游標**物件中**階層面板**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-205">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="e36ed-206">將拖放**WorldCursor**編寫成指令碼**Inspector 面板**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-206">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="e36ed-207">按兩下**WorldCursor**指令碼，以在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="e36ed-207">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="e36ed-208">複製並貼上此程式碼**WorldCursor.cs**並**全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-208">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

            // Move the cursor to the point where the raycast hit.
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

* <span data-ttu-id="e36ed-209">重建的應用程式**檔案 > 組建設定**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-209">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="e36ed-210">返回先前用來部署到您的 HoloLens 的 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="e36ed-210">Return to the Visual Studio solution previously used to deploy to your HoloLens.</span></span>
* <span data-ttu-id="e36ed-211">選取 [重新載入全部] 出現提示時。</span><span class="sxs-lookup"><span data-stu-id="e36ed-211">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="e36ed-212">按一下 **偵錯-> 啟動但不偵錯**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-212">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="e36ed-213">現在看一下場景，並注意資料指標的形狀之物件的互動方式。</span><span class="sxs-lookup"><span data-stu-id="e36ed-213">Now look around the scene and notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="e36ed-214">第 3 章-筆勢</span><span class="sxs-lookup"><span data-stu-id="e36ed-214">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

<span data-ttu-id="e36ed-215">在本章中，我們將新增的支援[筆勢](gestures.md)。</span><span class="sxs-lookup"><span data-stu-id="e36ed-215">In this chapter, we'll add support for [gestures](gestures.md).</span></span> <span data-ttu-id="e36ed-216">當使用者選取的紙張球體時，我們要藉由開啟重力使用 Unity 的物理條件引擎落球體。</span><span class="sxs-lookup"><span data-stu-id="e36ed-216">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="e36ed-217">目標</span><span class="sxs-lookup"><span data-stu-id="e36ed-217">Objectives</span></span>

* <span data-ttu-id="e36ed-218">控制您全像投影與選取的筆勢。</span><span class="sxs-lookup"><span data-stu-id="e36ed-218">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="e36ed-219">指示</span><span class="sxs-lookup"><span data-stu-id="e36ed-219">Instructions</span></span>

<span data-ttu-id="e36ed-220">我們一開始是建立指令碼，然後可以偵測到選取的筆勢。</span><span class="sxs-lookup"><span data-stu-id="e36ed-220">We'll start by creating a script then can detect the Select gesture.</span></span>

* <span data-ttu-id="e36ed-221">在 **指令碼**資料夾中，建立名為指令碼**GazeGestureManager**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-221">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="e36ed-222">拖曳**GazeGestureManager**拖曳至指令碼**OrigamiCollection**階層中的物件。</span><span class="sxs-lookup"><span data-stu-id="e36ed-222">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="e36ed-223">開啟**GazeGestureManager**指令碼在 Visual Studio 中，並新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="e36ed-223">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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
    void Awake()
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

* <span data-ttu-id="e36ed-224">建立另一個指令碼，在 [指令碼] 資料夾中，這次是名為**SphereCommands**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-224">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="e36ed-225">依序展開**OrigamiCollection**階層檢視中的物件。</span><span class="sxs-lookup"><span data-stu-id="e36ed-225">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="e36ed-226">拖曳**SphereCommands**拖曳至指令碼**Sphere1**在階層窗格中的物件。</span><span class="sxs-lookup"><span data-stu-id="e36ed-226">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="e36ed-227">拖曳**SphereCommands**拖曳至指令碼**Sphere2**在階層窗格中的物件。</span><span class="sxs-lookup"><span data-stu-id="e36ed-227">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="e36ed-228">在 Visual Studio 中開啟指令碼進行編輯，並以此取代預設的程式碼：</span><span class="sxs-lookup"><span data-stu-id="e36ed-228">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="e36ed-229">匯出、 建置和部署到您的 HoloLens 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e36ed-229">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="e36ed-230">看看其中一個所置放的球體。</span><span class="sxs-lookup"><span data-stu-id="e36ed-230">Look at one of the spheres.</span></span>
* <span data-ttu-id="e36ed-231">執行選取的動作，並觀看球體放入以下的介面。</span><span class="sxs-lookup"><span data-stu-id="e36ed-231">Perform the select gesture and watch the sphere drop onto the surface below.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="e36ed-232">第 4 章-語音</span><span class="sxs-lookup"><span data-stu-id="e36ed-232">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

<span data-ttu-id="e36ed-233">在本章中，我們將新增兩個支援[語音命令](voice-input.md):「 重設的 world 」 到其原始位置，傳回已卸除的球體看起來，並捨棄球體 進行切換的球體。</span><span class="sxs-lookup"><span data-stu-id="e36ed-233">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to return the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="e36ed-234">目標</span><span class="sxs-lookup"><span data-stu-id="e36ed-234">Objectives</span></span>

* <span data-ttu-id="e36ed-235">在背景中新增 alwayson 接聽的語音命令。</span><span class="sxs-lookup"><span data-stu-id="e36ed-235">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="e36ed-236">建立回應語音命令全像圖。</span><span class="sxs-lookup"><span data-stu-id="e36ed-236">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="e36ed-237">指示</span><span class="sxs-lookup"><span data-stu-id="e36ed-237">Instructions</span></span>

* <span data-ttu-id="e36ed-238">在 **指令碼**資料夾中，建立名為指令碼**SpeechManager**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-238">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="e36ed-239">拖曳**SpeechManager**拖曳至指令碼**OrigamiCollection**階層中的物件</span><span class="sxs-lookup"><span data-stu-id="e36ed-239">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="e36ed-240">開啟**SpeechManager** Visual Studio 中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="e36ed-240">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="e36ed-241">複製並貼上此程式碼**SpeechManager.cs**並**全部儲存**:</span><span class="sxs-lookup"><span data-stu-id="e36ed-241">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="e36ed-242">開啟**SphereCommands** Visual Studio 中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="e36ed-242">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="e36ed-243">更新指令碼來讀取，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e36ed-243">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="e36ed-244">匯出、 建置和部署到您的 HoloLens 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e36ed-244">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="e36ed-245">看看其中一個球體看起來，並說"**卸除的球體**"。</span><span class="sxs-lookup"><span data-stu-id="e36ed-245">Look at one of the spheres, and say "**Drop Sphere**".</span></span>
* <span data-ttu-id="e36ed-246">說出 「**重設的世界**「 若要將它們回復到其初始位置。</span><span class="sxs-lookup"><span data-stu-id="e36ed-246">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="e36ed-247">第 5 章-空間的音效</span><span class="sxs-lookup"><span data-stu-id="e36ed-247">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

<span data-ttu-id="e36ed-248">在本章中，我們會將音樂新增至應用程式，並接著觸發特定動作的音效。</span><span class="sxs-lookup"><span data-stu-id="e36ed-248">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="e36ed-249">我們將使用[空間音效](spatial-sound.md)讓音效在 3D 空間中的特定位置。</span><span class="sxs-lookup"><span data-stu-id="e36ed-249">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="e36ed-250">目標</span><span class="sxs-lookup"><span data-stu-id="e36ed-250">Objectives</span></span>

* <span data-ttu-id="e36ed-251">聽聽您的世界中全像投影。</span><span class="sxs-lookup"><span data-stu-id="e36ed-251">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="e36ed-252">指示</span><span class="sxs-lookup"><span data-stu-id="e36ed-252">Instructions</span></span>

* <span data-ttu-id="e36ed-253">在頂端功能表中的 Unity 選取**編輯 > 專案設定 > 音訊**</span><span class="sxs-lookup"><span data-stu-id="e36ed-253">In Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="e36ed-254">在右側 [偵測器] 面板中，尋找**空間外掛程式**設定，然後選取**MS HRTF 空間**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-254">In the Inspector Panel on the right side, find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="e36ed-255">從**全像投影**資料夾，在 [專案] 面板中，拖曳**環境**物件拖曳至**OrigamiCollection**在階層窗格中的物件。</span><span class="sxs-lookup"><span data-stu-id="e36ed-255">From the **Holograms** folder in the Project panel, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="e36ed-256">選取  **OrigamiCollection**並尋找**音訊來源**元件在偵測器窗格中。</span><span class="sxs-lookup"><span data-stu-id="e36ed-256">Select **OrigamiCollection** and find the **Audio Source** component in the Inspector panel.</span></span> <span data-ttu-id="e36ed-257">變更這些屬性：</span><span class="sxs-lookup"><span data-stu-id="e36ed-257">Change these properties:</span></span>
  * <span data-ttu-id="e36ed-258">請檢查**Spatialize**屬性。</span><span class="sxs-lookup"><span data-stu-id="e36ed-258">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="e36ed-259">請檢查**甦醒狀態上播放**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-259">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="e36ed-260">變更**空間 Blend**要**3D**拖曳到最右邊的滑桿。</span><span class="sxs-lookup"><span data-stu-id="e36ed-260">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span> <span data-ttu-id="e36ed-261">值應該將從 0 變更為 1 時移動滑桿。</span><span class="sxs-lookup"><span data-stu-id="e36ed-261">The value should change from 0 to 1 when you move the slider.</span></span>
  * <span data-ttu-id="e36ed-262">請檢查**迴圈**屬性。</span><span class="sxs-lookup"><span data-stu-id="e36ed-262">Check the **Loop** property.</span></span>
  * <span data-ttu-id="e36ed-263">依序展開**3D 音效設定**，並輸入**0.1** for **Doppler 層級**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-263">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="e36ed-264">設定**磁碟區捲繞**要**對數捲繞**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-264">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="e36ed-265">設定**最大距離**要**20**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-265">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="e36ed-266">在 **指令碼**資料夾中，建立名為指令碼**SphereSounds**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-266">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="e36ed-267">將拖放**SphereSounds**要**Sphere1**並**Sphere2**階層中的物件。</span><span class="sxs-lookup"><span data-stu-id="e36ed-267">Drag and drop **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="e36ed-268">開啟**SphereSounds**在 Visual Studio 中，更新下列程式碼並**全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-268">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="e36ed-269">儲存指令碼，並返回到 Unity。</span><span class="sxs-lookup"><span data-stu-id="e36ed-269">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="e36ed-270">匯出、 建置和部署到您的 HoloLens 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e36ed-270">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="e36ed-271">放大及更階段，然後開啟要並存至聽到任何聲音變更。</span><span class="sxs-lookup"><span data-stu-id="e36ed-271">Move closer and further from the Stage and turn side-to-side to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="e36ed-272">第 6 章-空間對應</span><span class="sxs-lookup"><span data-stu-id="e36ed-272">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

<span data-ttu-id="e36ed-273">現在我們將使用[空間對應](spatial-mapping.md)放置在真實世界的真實物件上的遊戲面板。</span><span class="sxs-lookup"><span data-stu-id="e36ed-273">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="e36ed-274">目標</span><span class="sxs-lookup"><span data-stu-id="e36ed-274">Objectives</span></span>

* <span data-ttu-id="e36ed-275">虛擬世界中帶入您真實的世界。</span><span class="sxs-lookup"><span data-stu-id="e36ed-275">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="e36ed-276">將您全像投影，在您最感興趣。</span><span class="sxs-lookup"><span data-stu-id="e36ed-276">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="e36ed-277">指示</span><span class="sxs-lookup"><span data-stu-id="e36ed-277">Instructions</span></span>

* <span data-ttu-id="e36ed-278">在 Unity 中，按一下**全像投影**專案 面板中的資料夾。</span><span class="sxs-lookup"><span data-stu-id="e36ed-278">In Unity, click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="e36ed-279">拖曳**空間的對應**資產的根目錄**階層**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-279">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="e36ed-280">按一下 **空間對應**階層中的物件。</span><span class="sxs-lookup"><span data-stu-id="e36ed-280">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="e36ed-281">在  **Inspector 面板**，變更下列屬性：</span><span class="sxs-lookup"><span data-stu-id="e36ed-281">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="e36ed-282">請檢查**繪製視覺網狀結構** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="e36ed-282">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="e36ed-283">找出**繪製的材質**按一下右側的圓形。</span><span class="sxs-lookup"><span data-stu-id="e36ed-283">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="e36ed-284">類型"**線框**」 到頂端的 [搜尋] 欄位。</span><span class="sxs-lookup"><span data-stu-id="e36ed-284">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="e36ed-285">按一下結果，然後關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="e36ed-285">Click on the result and then close the window.</span></span> <span data-ttu-id="e36ed-286">當您這樣做時，繪製資料的值應該設定製作。</span><span class="sxs-lookup"><span data-stu-id="e36ed-286">When you do this, the value for Draw Material should get set to Wireframe.</span></span>
* <span data-ttu-id="e36ed-287">匯出、 建置和部署到您的 HoloLens 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e36ed-287">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="e36ed-288">當應用程式執行時，框線網狀結構將覆疊您真實的世界。</span><span class="sxs-lookup"><span data-stu-id="e36ed-288">When the app runs, a wireframe mesh will overlay your real world.</span></span>
* <span data-ttu-id="e36ed-289">觀看如何輪流球體會切換關閉階段，並送至最低限度值 ！</span><span class="sxs-lookup"><span data-stu-id="e36ed-289">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="e36ed-290">現在要教您如何將 OrigamiCollection 移至新的位置：</span><span class="sxs-lookup"><span data-stu-id="e36ed-290">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="e36ed-291">在 **指令碼**資料夾中，建立名為指令碼**TapToPlaceParent**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-291">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="e36ed-292">在 **階層**，展開**OrigamiCollection** ，然後選取**階段**物件。</span><span class="sxs-lookup"><span data-stu-id="e36ed-292">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="e36ed-293">拖曳**TapToPlaceParent**階段物件的指令碼。</span><span class="sxs-lookup"><span data-stu-id="e36ed-293">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="e36ed-294">開啟**TapToPlaceParent**指令碼在 Visual Studio 中，並將它有下列更新：</span><span class="sxs-lookup"><span data-stu-id="e36ed-294">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="e36ed-295">匯出、 建置和部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="e36ed-295">Export, build and deploy the app.</span></span>
* <span data-ttu-id="e36ed-296">現在您現在應該可以加在遊戲中的特定位置 gazing 一下，使用選取的筆勢然後移至新的位置，並再次使用選取的筆勢。</span><span class="sxs-lookup"><span data-stu-id="e36ed-296">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="chapter-7---holographic-fun"></a><span data-ttu-id="e36ed-297">第 7 章-全像攝影版的樂趣</span><span class="sxs-lookup"><span data-stu-id="e36ed-297">Chapter 7 - Holographic fun</span></span>

### <a name="objectives"></a><span data-ttu-id="e36ed-298">目標</span><span class="sxs-lookup"><span data-stu-id="e36ed-298">Objectives</span></span>

* <span data-ttu-id="e36ed-299">顯示 全像攝影版的地底世界的入口。</span><span class="sxs-lookup"><span data-stu-id="e36ed-299">Reveal the entrance to a holographic underworld.</span></span>

### <a name="instructions"></a><span data-ttu-id="e36ed-300">指示</span><span class="sxs-lookup"><span data-stu-id="e36ed-300">Instructions</span></span>

<span data-ttu-id="e36ed-301">現在要教您如何找出全像攝影版的地底世界：</span><span class="sxs-lookup"><span data-stu-id="e36ed-301">Now we'll show you how to uncover the holographic underworld:</span></span>

* <span data-ttu-id="e36ed-302">從**全像投影**專案 面板中的資料夾：</span><span class="sxs-lookup"><span data-stu-id="e36ed-302">From the **Holograms** folder in the Project Panel:</span></span>
  * <span data-ttu-id="e36ed-303">拖曳**底世界**置於階層是子系**OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-303">Drag **Underworld** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="e36ed-304">在 **指令碼**資料夾中，建立名為指令碼**HitTarget**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-304">In the **Scripts** folder, create a script named **HitTarget**.</span></span>
* <span data-ttu-id="e36ed-305">在 **階層**，展開**OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="e36ed-305">In the **Hierarchy**, expand the **OrigamiCollection**.</span></span>
* <span data-ttu-id="e36ed-306">依序展開**階段**物件，並選取**目標**物件 （藍色風扇）。</span><span class="sxs-lookup"><span data-stu-id="e36ed-306">Expand the **Stage** object and select the **Target** object (blue fan).</span></span>
* <span data-ttu-id="e36ed-307">拖曳**HitTarget**拖曳至指令碼**目標**物件。</span><span class="sxs-lookup"><span data-stu-id="e36ed-307">Drag the **HitTarget** script onto the **Target** object.</span></span>
* <span data-ttu-id="e36ed-308">開啟**HitTarget**指令碼在 Visual Studio 中，並將它有下列更新：</span><span class="sxs-lookup"><span data-stu-id="e36ed-308">Open the **HitTarget** script in Visual Studio, and update it to be the following:</span></span>

```cs
using UnityEngine;

public class HitTarget : MonoBehaviour
{
    // These public fields become settable properties in the Unity editor.
    public GameObject underworld;
    public GameObject objectToHide;

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Hide the stage and show the underworld.
        objectToHide.SetActive(false);
        underworld.SetActive(true);

        // Disable Spatial Mapping to let the spheres enter the underworld.
        SpatialMapping.Instance.MappingEnabled = false;
    }
}
```

* <span data-ttu-id="e36ed-309">在 Unity 中，選取**目標**物件。</span><span class="sxs-lookup"><span data-stu-id="e36ed-309">In Unity, select the **Target** object.</span></span>
* <span data-ttu-id="e36ed-310">兩個公用屬性現在會顯示在**叫用目標**元件以及我們的場景中的參考物件的需求：</span><span class="sxs-lookup"><span data-stu-id="e36ed-310">Two public properties are now visible on the **Hit Target** component and need to reference objects in our scene:</span></span>
  * <span data-ttu-id="e36ed-311">拖曳**底世界**從**階層**面板**底世界**屬性**叫用目標**元件。</span><span class="sxs-lookup"><span data-stu-id="e36ed-311">Drag **Underworld** from the **Hierarchy** panel to the **Underworld** property on the **Hit Target** component.</span></span>
  * <span data-ttu-id="e36ed-312">拖曳**階段**從**階層**面板**隱藏物件**屬性**叫用目標**元件。</span><span class="sxs-lookup"><span data-stu-id="e36ed-312">Drag **Stage** from the **Hierarchy** panel to the **Object to Hide** property on the **Hit Target** component.</span></span>
* <span data-ttu-id="e36ed-313">匯出、 建置和部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="e36ed-313">Export, build and deploy the app.</span></span>
* <span data-ttu-id="e36ed-314">將 Origami 集合放在最低限度值，並接著使用選取的動作進行卸除的球體。</span><span class="sxs-lookup"><span data-stu-id="e36ed-314">Place the Origami Collection on the floor, and then use the Select gesture to make a sphere drop.</span></span>
* <span data-ttu-id="e36ed-315">當球體叫用目標 （藍色風扇） 時，則會發生遽增。</span><span class="sxs-lookup"><span data-stu-id="e36ed-315">When the sphere hits the target (blue fan), an explosion will occur.</span></span> <span data-ttu-id="e36ed-316">集合將會隱藏，並會出現一個洞地底世界。</span><span class="sxs-lookup"><span data-stu-id="e36ed-316">The collection will be hidden and a hole to the underworld will appear.</span></span>

## <a name="the-end"></a><span data-ttu-id="e36ed-317">結束</span><span class="sxs-lookup"><span data-stu-id="e36ed-317">The end</span></span>

<span data-ttu-id="e36ed-318">而且，本教學課程結束 ！</span><span class="sxs-lookup"><span data-stu-id="e36ed-318">And that's the end of this tutorial!</span></span>

<span data-ttu-id="e36ed-319">您已了解：</span><span class="sxs-lookup"><span data-stu-id="e36ed-319">You learned:</span></span>

* <span data-ttu-id="e36ed-320">如何建立在 Unity 的全像攝影版的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e36ed-320">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="e36ed-321">如何使用視線、 手勢、 語音、 聲音、 和空間的對應。</span><span class="sxs-lookup"><span data-stu-id="e36ed-321">How to make use of gaze, gesture, voice, sound, and spatial mapping.</span></span>
* <span data-ttu-id="e36ed-322">如何建置和部署使用 Visual Studio 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e36ed-322">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="e36ed-323">您現在已準備好要開始建立您自己全像攝影版的體驗 ！</span><span class="sxs-lookup"><span data-stu-id="e36ed-323">You are now ready to start creating your own holographic experience!</span></span>

## <a name="see-also"></a><span data-ttu-id="e36ed-324">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e36ed-324">See also</span></span>

* [<span data-ttu-id="e36ed-325">MR 基本概念 101E:模擬器使用完整的專案</span><span class="sxs-lookup"><span data-stu-id="e36ed-325">MR Basics 101E: Complete project with emulator</span></span>](holograms-101e.md)
* [<span data-ttu-id="e36ed-326">Gaze</span><span class="sxs-lookup"><span data-stu-id="e36ed-326">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="e36ed-327">筆勢</span><span class="sxs-lookup"><span data-stu-id="e36ed-327">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="e36ed-328">語音輸入</span><span class="sxs-lookup"><span data-stu-id="e36ed-328">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="e36ed-329">空間的音效</span><span class="sxs-lookup"><span data-stu-id="e36ed-329">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="e36ed-330">空間對應</span><span class="sxs-lookup"><span data-stu-id="e36ed-330">Spatial mapping</span></span>](spatial-mapping.md)
