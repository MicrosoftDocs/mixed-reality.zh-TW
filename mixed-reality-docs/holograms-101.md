---
title: MR 基本概念 101-使用裝置完成專案
description: 請遵循使用 Unity、Visual Studio 和 HoloLens 進行的編碼逐步解說，以瞭解 Windows Mixed Reality 的基本概念。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: 混合現實、Windows Mixed Reality、HoloLens、全息裡、學院、教學課程
ms.openlocfilehash: 456aeea88b0d7f51acb52156d8139ec2df06883a
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434715"
---
>[!NOTE]
><span data-ttu-id="0cfcc-104">混合現實學術教學課程的設計是使用 HoloLens （第1代）和混合現實的沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="0cfcc-105">因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="0cfcc-106">這些教學課程 **_不_** 會以最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="0cfcc-107">系統會保留這些資訊，以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="0cfcc-108">HoloLens 2 已張貼[一系列新的教學](mrlearning-base.md)課程。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-basics-101-complete-project-with-device"></a><span data-ttu-id="0cfcc-109">MR 基本概念101：使用裝置完成專案</span><span class="sxs-lookup"><span data-stu-id="0cfcc-109">MR Basics 101: Complete project with device</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

<span data-ttu-id="0cfcc-110">本教學課程將逐步引導您完成以 Unity 為基礎的完整專案，其中示範 HoloLens 上的核心 Windows Mixed Reality 功能，包括[注視](gaze-and-commit.md)、[手勢](gaze-and-commit.md#composite-gestures)、[語音輸入](voice-input.md)、[空間音效](spatial-sound.md)和[空間對應](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="0cfcc-110">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze-and-commit.md), [gestures](gaze-and-commit.md#composite-gestures), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span>

<span data-ttu-id="0cfcc-111">本教學課程需要大約1小時才能完成。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-111">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="0cfcc-112">裝置支援</span><span class="sxs-lookup"><span data-stu-id="0cfcc-112">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="0cfcc-113">粗</span><span class="sxs-lookup"><span data-stu-id="0cfcc-113">Course</span></span></th><th style="width:150px"> <span data-ttu-id="0cfcc-114"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="0cfcc-114"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="0cfcc-115"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="0cfcc-115"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="0cfcc-116">MR 基本概念101：使用裝置完成專案</span><span class="sxs-lookup"><span data-stu-id="0cfcc-116">MR Basics 101: Complete project with device</span></span></td><td style="text-align: center;"> <span data-ttu-id="0cfcc-117">✔️</span><span class="sxs-lookup"><span data-stu-id="0cfcc-117">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="0cfcc-118">開始之前</span><span class="sxs-lookup"><span data-stu-id="0cfcc-118">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="0cfcc-119">必要條件</span><span class="sxs-lookup"><span data-stu-id="0cfcc-119">Prerequisites</span></span>

* <span data-ttu-id="0cfcc-120">[已安裝正確工具](install-the-tools.md)的 WINDOWS 10 電腦。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-120">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="0cfcc-121">[為開發設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-121">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="0cfcc-122">專案檔案</span><span class="sxs-lookup"><span data-stu-id="0cfcc-122">Project files</span></span>

* <span data-ttu-id="0cfcc-123">下載專案[所需的](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip)檔案。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-123">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="0cfcc-124"> 需要 Unity 2017.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-124"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="0cfcc-125">如果您仍然需要 Unity 5.6 支援，請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-125">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="0cfcc-126">如果您仍然需要 Unity 5.5 支援，請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-126">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="0cfcc-127">如果您仍然需要 Unity 5.4 支援，請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-127">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="0cfcc-128">將檔案取消封存至您的桌面或其他容易到達的位置。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-128">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="0cfcc-129">將資料夾名稱保留為 [**折紙**]。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-129">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="0cfcc-130">如果您想要在下載之前查看原始程式碼，可以[在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)取得。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-130">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="0cfcc-131">第1章-「Hololens」世界</span><span class="sxs-lookup"><span data-stu-id="0cfcc-131">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

<span data-ttu-id="0cfcc-132">在本章中，我們將設定第一個 Unity 專案，並逐步執行組建和部署流程。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-132">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="0cfcc-133">目標</span><span class="sxs-lookup"><span data-stu-id="0cfcc-133">Objectives</span></span>

* <span data-ttu-id="0cfcc-134">設定 Unity 以進行全像攝影開發。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-134">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="0cfcc-135">建立全息影像。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-135">Make a hologram.</span></span>
* <span data-ttu-id="0cfcc-136">查看您製作的全息影像。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-136">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="0cfcc-137">指示</span><span class="sxs-lookup"><span data-stu-id="0cfcc-137">Instructions</span></span>

* <span data-ttu-id="0cfcc-138">啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-138">Start Unity.</span></span>
* <span data-ttu-id="0cfcc-139">選取 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-139">Select **Open**.</span></span>
* <span data-ttu-id="0cfcc-140">輸入 [位置] 做為您先前未封存的 [**折紙**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-140">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="0cfcc-141">選取 [**折紙**]，然後按一下 [**選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-141">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="0cfcc-142">因為**折紙**專案不包含場景，所以請使用： **File** / **將場景儲存為**，將空的預設場景儲存至新檔案。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-142">Since the **Origami** project does not contain a scene, save the empty default scene to a new file using: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="0cfcc-143">將新場景命名為 [**折紙**]，然後按 [**儲存**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-143">Name the new scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-virtual-camera"></a><span data-ttu-id="0cfcc-144">設定主要虛擬攝影機</span><span class="sxs-lookup"><span data-stu-id="0cfcc-144">Setup the main virtual camera</span></span>

* <span data-ttu-id="0cfcc-145">在 [階層]**面板**中，選取 [**主要相機**]。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-145">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="0cfcc-146">在偵測**器**中，將其轉換位置設為**0，0，0**。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-146">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="0cfcc-147">尋找 [**清除旗標**] 屬性，並將下拉式清單從 [ **Skybox** ] 變更為 [**單色**]。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-147">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="0cfcc-148">按一下 [**背景**] 欄位，以開啟色彩選擇器。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-148">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="0cfcc-149">將**R、G、B 和 A**設定為**0**。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-149">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="0cfcc-150">設定場景</span><span class="sxs-lookup"><span data-stu-id="0cfcc-150">Setup the scene</span></span>

* <span data-ttu-id="0cfcc-151">在 [階層]**面板**中，按一下 [**建立**] 並**建立空**的。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-151">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="0cfcc-152">以滑鼠右鍵按一下新的**GameObject** ，然後選取 [重新命名]。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-152">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="0cfcc-153">將 GameObject 重新命名為**OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-153">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="0cfcc-154">從 [專案] 面板中的 [**全息影像**] 資料夾（展開 [資產]，然後選取 [全息]，或按兩下 [專案] 面板中的 [全息影像] 資料夾</span><span class="sxs-lookup"><span data-stu-id="0cfcc-154">From the **Holograms** folder in the Project Panel (expand Assets and select Holograms or double click the Holograms folder in the Project Panel):</span></span>
  * <span data-ttu-id="0cfcc-155">將**階段**拖曳到階層中，成為**OrigamiCollection**的子系。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-155">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="0cfcc-156">將**Sphere1**拖曳到階層中，成為**OrigamiCollection**的子系。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-156">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="0cfcc-157">將**Sphere2**拖曳到階層中，成為**OrigamiCollection**的子系。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-157">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="0cfcc-158">以滑鼠右鍵按一下 [階層]**面板**中的 [**方向光源**] 物件，然後選取 [**刪除**]。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-158">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="0cfcc-159">從 [**全息影像**] 資料夾，將 [**燈光**] 拖曳至 [階層]**面板**的根目錄。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-159">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="0cfcc-160">在階層**中，選取**[ **OrigamiCollection**]。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-160">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="0cfcc-161">在偵測**器**中，將轉換位置設定為**0，-0.5，2.0**。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-161">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="0cfcc-162">按下 Unity 中的 [**播放**] 按鈕，以預覽您的全息影像。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-162">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="0cfcc-163">您應該會在預覽視窗中看到 [折紙] 物件。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-163">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="0cfcc-164">按第二次 [**播放**] 以停止預覽模式。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-164">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="0cfcc-165">將專案從 Unity 匯出至 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0cfcc-165">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="0cfcc-166">在 Unity 中，選取 檔案 **> 組建設定**。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-166">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="0cfcc-167">在 [**平臺**] 清單中選取**通用 Windows 平臺**，然後按一下 [**切換平臺**]。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-167">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="0cfcc-168">將 [ **SDK** ] 設定為 [**通用 10** ]，將 [**組建類型**] 設為**D3D**</span><span class="sxs-lookup"><span data-stu-id="0cfcc-168">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="0cfcc-169">檢查**Unity C#專案**。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-169">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="0cfcc-170">按一下 [新增] [**開啟場景**] 以加入場景。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-170">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="0cfcc-171">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-171">Click **Build**.</span></span>
* <span data-ttu-id="0cfcc-172">在出現的 [檔案瀏覽器] 視窗中，建立名為 "App" 的**新資料夾**。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-172">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="0cfcc-173">按一下 [**應用程式] 資料夾**。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-173">Single click the **App Folder**.</span></span>
* <span data-ttu-id="0cfcc-174">按 [**選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-174">Press **Select Folder**.</span></span>
* <span data-ttu-id="0cfcc-175">當 Unity 完成時，將會出現 [檔案瀏覽器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-175">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="0cfcc-176">開啟**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-176">Open the **App** folder.</span></span>
* <span data-ttu-id="0cfcc-177">開啟（按兩下） [**折紙**]。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-177">Open (double click) **Origami.sln**.</span></span>
* <span data-ttu-id="0cfcc-178">使用 Visual Studio 中的頂端工具列，將目標從 [調試] 變更為 [**發行**]，將 [從 ARM] 變更為**X86**。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-178">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="0cfcc-179">按一下 [裝置] 按鈕旁邊的箭號，然後選取 [**遠端電腦**] 以透過 wi-fi 進行部署。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-179">Click on the arrow next to the Device button, and select **Remote Machine** to deploy over Wi-Fi.</span></span>
  * <span data-ttu-id="0cfcc-180">將**位址**設定為 HoloLens 的名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-180">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="0cfcc-181">如果您不知道您的裝置 IP 位址，請查看 [**設定] > 網路 & [網際網路] > [Advanced Options** **] 或 [你好 cortana，我的 IP 位址是什麼？]**</span><span class="sxs-lookup"><span data-stu-id="0cfcc-181">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
  * <span data-ttu-id="0cfcc-182">如果 HoloLens 是透過 USB 連接，您可以改為選取 [**裝置**] 以透過 usb 進行部署。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-182">If the HoloLens is attached over USB, you may instead select **Device** to deploy over USB.</span></span>
  * <span data-ttu-id="0cfcc-183">將 [**驗證模式]** 保持設定為 [**通用**]。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-183">Leave the **Authentication Mode** set to **Universal**.</span></span>
  * <span data-ttu-id="0cfcc-184">按一下 [**選取**]</span><span class="sxs-lookup"><span data-stu-id="0cfcc-184">Click **Select**</span></span>

* <span data-ttu-id="0cfcc-185">按一下 [ **Debug > 啟動但不進行調試**] 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-185">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="0cfcc-186">如果這是您第一次部署至您的裝置，您必須將[它與 Visual Studio 配對](using-visual-studio.md#pairing-your-device)。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-186">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>

* <span data-ttu-id="0cfcc-187">現在，折紙專案會建立、部署至您的 HoloLens，然後執行。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-187">The Origami project will now build, deploy to your HoloLens, and then run.</span></span>
* <span data-ttu-id="0cfcc-188">放在您的 HoloLens 上，並查看您的新全息影像。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-188">Put on your HoloLens and look around to see your new holograms.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="0cfcc-189">第2章-注視</span><span class="sxs-lookup"><span data-stu-id="0cfcc-189">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

<span data-ttu-id="0cfcc-190">在本章中，我們將引進三種與您的全息影像互動的第一種方式：[注視](gaze-and-commit.md)。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-190">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze-and-commit.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="0cfcc-191">目標</span><span class="sxs-lookup"><span data-stu-id="0cfcc-191">Objectives</span></span>

* <span data-ttu-id="0cfcc-192">使用世界鎖定的游標來視覺化您的注視。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-192">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="0cfcc-193">指示</span><span class="sxs-lookup"><span data-stu-id="0cfcc-193">Instructions</span></span>

* <span data-ttu-id="0cfcc-194">回到您的 Unity 專案，並關閉 [組建設定] 視窗（如果仍處於開啟狀態）。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-194">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="0cfcc-195">在 [**專案] 面板**中選取 [**全息影像**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-195">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="0cfcc-196">將**游標**物件拖曳至根層級的 [階層]**面板**。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-196">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="0cfcc-197">按兩下**游標**物件以深入瞭解它。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-197">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="0cfcc-198">以滑鼠右鍵按一下 [專案] 面板中的 [**腳本**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-198">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="0cfcc-199">按一下 [**建立**] 子功能表。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-199">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="0cfcc-200">選取 **C# [腳本**]。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-200">Select **C# Script**.</span></span>
* <span data-ttu-id="0cfcc-201">將腳本命名為**WorldCursor**。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-201">Name the script **WorldCursor**.</span></span> <span data-ttu-id="0cfcc-202">注意：名稱會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-202">Note: The name is case-sensitive.</span></span> <span data-ttu-id="0cfcc-203">您不需要新增 .cs 副檔名。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-203">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="0cfcc-204">在 [階層]**面板**中選取**游標**物件。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-204">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="0cfcc-205">將**WorldCursor**腳本拖放到 [偵測**器] 面板**中。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-205">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="0cfcc-206">按兩下 [ **WorldCursor** ] 腳本，在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-206">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="0cfcc-207">將此程式碼複製並貼到**WorldCursor.cs**中，並**全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-207">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

* <span data-ttu-id="0cfcc-208">從 [檔案] **> 組建設定**重建應用程式。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-208">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="0cfcc-209">回到先前用來部署至 HoloLens 的 Visual Studio 解決方案。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-209">Return to the Visual Studio solution previously used to deploy to your HoloLens.</span></span>
* <span data-ttu-id="0cfcc-210">出現提示時，選取 [全部重載]。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-210">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="0cfcc-211">按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-211">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="0cfcc-212">現在查看場景，並留意游標如何與物件的形狀互動。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-212">Now look around the scene and notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="0cfcc-213">第3章-手勢</span><span class="sxs-lookup"><span data-stu-id="0cfcc-213">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

<span data-ttu-id="0cfcc-214">在本章中，我們將新增[手勢](gaze-and-commit.md#composite-gestures)的支援。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-214">In this chapter, we'll add support for [gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="0cfcc-215">當使用者選取紙球體時，我們會使用 Unity 的物理引擎來開啟重心，讓球體變得更容易。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-215">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="0cfcc-216">目標</span><span class="sxs-lookup"><span data-stu-id="0cfcc-216">Objectives</span></span>

* <span data-ttu-id="0cfcc-217">使用選取手勢控制您的全息影像。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-217">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="0cfcc-218">指示</span><span class="sxs-lookup"><span data-stu-id="0cfcc-218">Instructions</span></span>

<span data-ttu-id="0cfcc-219">首先，我們會建立腳本，然後偵測選取手勢。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-219">We'll start by creating a script then can detect the Select gesture.</span></span>

* <span data-ttu-id="0cfcc-220">在 [**腳本**] 資料夾中，建立名為**GazeGestureManager**的腳本。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-220">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="0cfcc-221">將**GazeGestureManager**腳本拖曳至階層中的**OrigamiCollection**物件。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-221">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="0cfcc-222">在 Visual Studio 中開啟**GazeGestureManager**腳本，並新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="0cfcc-222">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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

* <span data-ttu-id="0cfcc-223">在 Scripts 資料夾中建立另一個腳本，這次名為**SphereCommands**。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-223">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="0cfcc-224">在 [階層] 視圖中展開 [ **OrigamiCollection** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-224">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="0cfcc-225">將**SphereCommands**腳本拖曳至 [階層] 面板中的**Sphere1**物件。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-225">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="0cfcc-226">將**SphereCommands**腳本拖曳至 [階層] 面板中的**Sphere2**物件。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-226">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="0cfcc-227">在 Visual Studio 中開啟腳本進行編輯，並將預設程式碼取代為：</span><span class="sxs-lookup"><span data-stu-id="0cfcc-227">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="0cfcc-228">匯出、建立應用程式，並將其部署至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-228">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="0cfcc-229">查看其中一個球體。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-229">Look at one of the spheres.</span></span>
* <span data-ttu-id="0cfcc-230">執行 [選取手勢] 並監看球體拖放到下方的表面。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-230">Perform the select gesture and watch the sphere drop onto the surface below.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="0cfcc-231">第4章-語音</span><span class="sxs-lookup"><span data-stu-id="0cfcc-231">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

<span data-ttu-id="0cfcc-232">在本章中，我們將新增兩個[語音命令](voice-input.md)的支援：「重設世界」以將捨棄的球面傳回原始位置，而「捨棄球體」則讓球體落在外。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-232">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to return the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="0cfcc-233">目標</span><span class="sxs-lookup"><span data-stu-id="0cfcc-233">Objectives</span></span>

* <span data-ttu-id="0cfcc-234">新增一律在背景中接聽的語音命令。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-234">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="0cfcc-235">建立可回應語音命令的全息影像。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-235">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="0cfcc-236">指示</span><span class="sxs-lookup"><span data-stu-id="0cfcc-236">Instructions</span></span>

* <span data-ttu-id="0cfcc-237">在 [**腳本**] 資料夾中，建立名為**SpeechManager**的腳本。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-237">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="0cfcc-238">將**SpeechManager**腳本拖曳至階層中的**OrigamiCollection**物件</span><span class="sxs-lookup"><span data-stu-id="0cfcc-238">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="0cfcc-239">在 Visual Studio 中開啟**SpeechManager**腳本。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-239">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="0cfcc-240">將此程式碼複製並貼到**SpeechManager.cs**中，並**全部儲存**：</span><span class="sxs-lookup"><span data-stu-id="0cfcc-240">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="0cfcc-241">在 Visual Studio 中開啟**SphereCommands**腳本。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-241">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="0cfcc-242">更新腳本以進行讀取，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0cfcc-242">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="0cfcc-243">匯出、建立應用程式，並將其部署至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-243">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="0cfcc-244">查看其中一個球體，並說「卸載**球體**」。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-244">Look at one of the spheres, and say "**Drop Sphere**".</span></span>
* <span data-ttu-id="0cfcc-245">請說「**重設世界**」，使其回到其初始位置。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-245">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="0cfcc-246">第5章-空間音效</span><span class="sxs-lookup"><span data-stu-id="0cfcc-246">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

<span data-ttu-id="0cfcc-247">在本章中，我們會將音樂新增至應用程式，然後觸發對特定動作的音效效果。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-247">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="0cfcc-248">我們會使用[空間音效](spatial-sound.md)，在3d 空間中提供特定位置的聲音。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-248">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="0cfcc-249">目標</span><span class="sxs-lookup"><span data-stu-id="0cfcc-249">Objectives</span></span>

* <span data-ttu-id="0cfcc-250">聆聽您世界中的全息影像。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-250">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="0cfcc-251">指示</span><span class="sxs-lookup"><span data-stu-id="0cfcc-251">Instructions</span></span>

* <span data-ttu-id="0cfcc-252">在 Unity 中從頂端功能表中選取 [**編輯] > 專案設定 > 音訊**</span><span class="sxs-lookup"><span data-stu-id="0cfcc-252">In Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="0cfcc-253">在右側的 [偵測器] 面板中，尋找 [**空間定位器外掛程式**] 設定，然後選取 [ **MS HRTF 空間定位器**]。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-253">In the Inspector Panel on the right side, find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="0cfcc-254">從 [專案] 面板的 [**全息影像**] 資料夾中，將 [**環境**] 物件拖曳至 [階層] 面板中的 [ **OrigamiCollection** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-254">From the **Holograms** folder in the Project panel, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="0cfcc-255">選取 [ **OrigamiCollection** ]，然後在 [偵測器] 面板中尋找 [**音訊來源**] 元件。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-255">Select **OrigamiCollection** and find the **Audio Source** component in the Inspector panel.</span></span> <span data-ttu-id="0cfcc-256">變更這些屬性：</span><span class="sxs-lookup"><span data-stu-id="0cfcc-256">Change these properties:</span></span>
  * <span data-ttu-id="0cfcc-257">檢查**Spatialize**屬性。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-257">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="0cfcc-258">勾選 [**在喚醒時播放**]。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-258">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="0cfcc-259">將 [**空間 Blend** ] 變更為 [ **3d** ]，方法是將滑杆向右拖曳。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-259">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span> <span data-ttu-id="0cfcc-260">當您移動滑杆時，此值應該從0變更為1。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-260">The value should change from 0 to 1 when you move the slider.</span></span>
  * <span data-ttu-id="0cfcc-261">檢查 [**迴圈**] 屬性。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-261">Check the **Loop** property.</span></span>
  * <span data-ttu-id="0cfcc-262">展開 [ **3D 音效設定**]，然後針對 [ **Doppler 層級**] 輸入**0.1** 。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-262">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="0cfcc-263">將 [**磁片區 Rolloff** ] 設定為 [**對數 Rolloff**]。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-263">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="0cfcc-264">將 [**最大距離**] 設定為**20**。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-264">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="0cfcc-265">在 [**腳本**] 資料夾中，建立名為**SphereSounds**的腳本。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-265">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="0cfcc-266">將**SphereSounds**拖放至階層中的**Sphere1**和**Sphere2**物件。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-266">Drag and drop **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="0cfcc-267">在 Visual Studio 中開啟**SphereSounds** ，更新下列程式碼並**全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-267">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="0cfcc-268">儲存腳本，並返回 Unity。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-268">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="0cfcc-269">匯出、建立應用程式，並將其部署至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-269">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="0cfcc-270">從階段中往上和往上移動，然後再將其關閉，以聽到音效的改變。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-270">Move closer and further from the Stage and turn side-to-side to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="0cfcc-271">第6章-空間對應</span><span class="sxs-lookup"><span data-stu-id="0cfcc-271">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

<span data-ttu-id="0cfcc-272">現在我們要使用[空間對應](spatial-mapping.md)，將遊戲面板放在真實世界中的實際物件上。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-272">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="0cfcc-273">目標</span><span class="sxs-lookup"><span data-stu-id="0cfcc-273">Objectives</span></span>

* <span data-ttu-id="0cfcc-274">將您的真實世界帶入虛擬世界。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-274">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="0cfcc-275">將您的全息影像放在對您最重要的地方。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-275">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="0cfcc-276">指示</span><span class="sxs-lookup"><span data-stu-id="0cfcc-276">Instructions</span></span>

* <span data-ttu-id="0cfcc-277">在 Unity 中，按一下 [專案] 面板中的 [**全息影像**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-277">In Unity, click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="0cfcc-278">將**空間對應**資產拖曳至**階層的根目錄。**</span><span class="sxs-lookup"><span data-stu-id="0cfcc-278">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="0cfcc-279">按一下階層中的 [**空間對應**] 物件。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-279">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="0cfcc-280">在 [偵測**器] 面板**中，變更下列屬性：</span><span class="sxs-lookup"><span data-stu-id="0cfcc-280">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="0cfcc-281">勾選 [**繪製視覺網格**] 方塊。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-281">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="0cfcc-282">找出 [**繪製材質**]，然後按一下右側的圓形。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-282">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="0cfcc-283">在頂端的搜尋欄位中輸入「**線框**」。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-283">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="0cfcc-284">按一下結果，然後關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-284">Click on the result and then close the window.</span></span> <span data-ttu-id="0cfcc-285">當您這麼做時，[繪製材質] 的值應該會設定為 [線框]。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-285">When you do this, the value for Draw Material should get set to Wireframe.</span></span>
* <span data-ttu-id="0cfcc-286">匯出、建立應用程式，並將其部署至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-286">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="0cfcc-287">當應用程式執行時，線框網格會覆迭您的真實世界。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-287">When the app runs, a wireframe mesh will overlay your real world.</span></span>
* <span data-ttu-id="0cfcc-288">觀賞輪流球體如何落在舞臺上，以及在地面上！</span><span class="sxs-lookup"><span data-stu-id="0cfcc-288">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="0cfcc-289">現在，我們將示範如何將 OrigamiCollection 移到新的位置：</span><span class="sxs-lookup"><span data-stu-id="0cfcc-289">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="0cfcc-290">在 [**腳本**] 資料夾中，建立名為**TapToPlaceParent**的腳本。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-290">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="0cfcc-291">在階層**中，展開**[ **OrigamiCollection** ]，然後選取 [**階段**] 物件。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-291">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="0cfcc-292">將**TapToPlaceParent**腳本拖曳至階段物件。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-292">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="0cfcc-293">在 Visual Studio 中開啟**TapToPlaceParent**腳本，並將它更新為下列內容：</span><span class="sxs-lookup"><span data-stu-id="0cfcc-293">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="0cfcc-294">匯出、建立及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-294">Export, build and deploy the app.</span></span>
* <span data-ttu-id="0cfcc-295">現在您應該可以在特定位置撥雲見日遊戲，方法是使用選取手勢然後移至新位置，然後再次使用 [選取] 手勢。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-295">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="chapter-7---holographic-fun"></a><span data-ttu-id="0cfcc-296">第7章-全像攝影</span><span class="sxs-lookup"><span data-stu-id="0cfcc-296">Chapter 7 - Holographic fun</span></span>

### <a name="objectives"></a><span data-ttu-id="0cfcc-297">目標</span><span class="sxs-lookup"><span data-stu-id="0cfcc-297">Objectives</span></span>

* <span data-ttu-id="0cfcc-298">顯示全像全像 underworld 的進入。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-298">Reveal the entrance to a holographic underworld.</span></span>

### <a name="instructions"></a><span data-ttu-id="0cfcc-299">指示</span><span class="sxs-lookup"><span data-stu-id="0cfcc-299">Instructions</span></span>

<span data-ttu-id="0cfcc-300">現在，我們將為您示範如何發掘全像攝影 underworld：</span><span class="sxs-lookup"><span data-stu-id="0cfcc-300">Now we'll show you how to uncover the holographic underworld:</span></span>

* <span data-ttu-id="0cfcc-301">從 [專案] 面板中的 [**全息影像**] 資料夾：</span><span class="sxs-lookup"><span data-stu-id="0cfcc-301">From the **Holograms** folder in the Project Panel:</span></span>
  * <span data-ttu-id="0cfcc-302">將**Underworld**拖曳到階層中，成為**OrigamiCollection**的子系。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-302">Drag **Underworld** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="0cfcc-303">在 [**腳本**] 資料夾中，建立名為**HitTarget**的腳本。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-303">In the **Scripts** folder, create a script named **HitTarget**.</span></span>
* <span data-ttu-id="0cfcc-304">**在階層中，展開**[ **OrigamiCollection**]。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-304">In the **Hierarchy**, expand the **OrigamiCollection**.</span></span>
* <span data-ttu-id="0cfcc-305">展開 [**階段**] 物件，然後選取 [**目標**物件（藍色風扇）]。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-305">Expand the **Stage** object and select the **Target** object (blue fan).</span></span>
* <span data-ttu-id="0cfcc-306">將**HitTarget**腳本拖曳至**目標**物件。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-306">Drag the **HitTarget** script onto the **Target** object.</span></span>
* <span data-ttu-id="0cfcc-307">在 Visual Studio 中開啟**HitTarget**腳本，並將它更新為下列內容：</span><span class="sxs-lookup"><span data-stu-id="0cfcc-307">Open the **HitTarget** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="0cfcc-308">在 [Unity] 中，選取**目標**物件。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-308">In Unity, select the **Target** object.</span></span>
* <span data-ttu-id="0cfcc-309">現在會在叫用**目標**元件上顯示兩個公用屬性，而且需要參考我們場景中的物件：</span><span class="sxs-lookup"><span data-stu-id="0cfcc-309">Two public properties are now visible on the **Hit Target** component and need to reference objects in our scene:</span></span>
  * <span data-ttu-id="0cfcc-310">將 [ **Underworld** ] 從 [階層 **] 面板拖曳**至 [**點擊目標**] 元件上的 [ **Underworld** ] 屬性。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-310">Drag **Underworld** from the **Hierarchy** panel to the **Underworld** property on the **Hit Target** component.</span></span>
  * <span data-ttu-id="0cfcc-311">將 [**階段**] 從 [階層 **] 面板拖曳**至 [物件]，**以隱藏** **點擊目標**元件上的屬性。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-311">Drag **Stage** from the **Hierarchy** panel to the **Object to Hide** property on the **Hit Target** component.</span></span>
* <span data-ttu-id="0cfcc-312">匯出、建立及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-312">Export, build and deploy the app.</span></span>
* <span data-ttu-id="0cfcc-313">將 [折紙] 集合放在樓層，然後使用 [選取手勢] 來放置球體。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-313">Place the Origami Collection on the floor, and then use the Select gesture to make a sphere drop.</span></span>
* <span data-ttu-id="0cfcc-314">當球體到達目標（藍色風扇）時，將會發生激增。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-314">When the sphere hits the target (blue fan), an explosion will occur.</span></span> <span data-ttu-id="0cfcc-315">將會隱藏集合，並顯示 underworld 的洞。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-315">The collection will be hidden and a hole to the underworld will appear.</span></span>

## <a name="the-end"></a><span data-ttu-id="0cfcc-316">結束</span><span class="sxs-lookup"><span data-stu-id="0cfcc-316">The end</span></span>

<span data-ttu-id="0cfcc-317">這就是本教學課程的結尾！</span><span class="sxs-lookup"><span data-stu-id="0cfcc-317">And that's the end of this tutorial!</span></span>

<span data-ttu-id="0cfcc-318">您已瞭解：</span><span class="sxs-lookup"><span data-stu-id="0cfcc-318">You learned:</span></span>

* <span data-ttu-id="0cfcc-319">如何在 Unity 中建立全像攝影應用程式。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-319">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="0cfcc-320">如何使用 [注視]、[手勢]、[聲音]、[聲音] 和 [空間對應]。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-320">How to make use of gaze, gesture, voice, sound, and spatial mapping.</span></span>
* <span data-ttu-id="0cfcc-321">如何使用 Visual Studio 建立及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="0cfcc-321">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="0cfcc-322">您現在已準備好開始建立您自己的全像攝影體驗！</span><span class="sxs-lookup"><span data-stu-id="0cfcc-322">You are now ready to start creating your own holographic experience!</span></span>

## <a name="see-also"></a><span data-ttu-id="0cfcc-323">請參閱</span><span class="sxs-lookup"><span data-stu-id="0cfcc-323">See also</span></span>

* [<span data-ttu-id="0cfcc-324">MR 基本概念101E：使用模擬器完成專案</span><span class="sxs-lookup"><span data-stu-id="0cfcc-324">MR Basics 101E: Complete project with emulator</span></span>](holograms-101e.md)
* [<span data-ttu-id="0cfcc-325">目光</span><span class="sxs-lookup"><span data-stu-id="0cfcc-325">Gaze</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="0cfcc-326">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="0cfcc-326">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="0cfcc-327">語音輸入</span><span class="sxs-lookup"><span data-stu-id="0cfcc-327">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="0cfcc-328">空間音效</span><span class="sxs-lookup"><span data-stu-id="0cfcc-328">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="0cfcc-329">空間對應</span><span class="sxs-lookup"><span data-stu-id="0cfcc-329">Spatial mapping</span></span>](spatial-mapping.md)
