---
title: MR 基本概念 101-使用裝置完成專案
description: 請遵循使用 Unity、Visual Studio 和 HoloLens 進行的編碼逐步解說, 以瞭解 Windows Mixed Reality 的基本概念。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: 混合現實、Windows Mixed Reality、HoloLens、全息裡、學院、教學課程
ms.openlocfilehash: 043ffac8f30a4e29586478b5dca6ecccc2b5afd3
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524023"
---
>[!NOTE]
><span data-ttu-id="f60c2-104">混合現實學術教學課程的設計是使用 HoloLens (第1代) 和混合現實的沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="f60c2-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="f60c2-105">因此, 對於仍在尋找這些裝置開發指引的開發人員而言, 我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="f60c2-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="f60c2-106">這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="f60c2-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="f60c2-107">系統會保留這些資訊, 以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="f60c2-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="f60c2-108">未來將會有一系列新的教學課程, 將示範如何針對 HoloLens 2 進行開發。</span><span class="sxs-lookup"><span data-stu-id="f60c2-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="f60c2-109">此通知會在張貼時, 使用這些教學課程的連結進行更新。</span><span class="sxs-lookup"><span data-stu-id="f60c2-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-101-complete-project-with-device"></a><span data-ttu-id="f60c2-110">MR 基本 101:使用裝置完成專案</span><span class="sxs-lookup"><span data-stu-id="f60c2-110">MR Basics 101: Complete project with device</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

<span data-ttu-id="f60c2-111">本教學課程將逐步引導您完成以 Unity 為基礎的完整專案, 其中示範 HoloLens 上的核心 Windows Mixed Reality 功能, 包括[注視](gaze.md)、[手勢](gestures.md)、[語音輸入](voice-input.md)、[空間音效](spatial-sound.md)和[空間對應](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="f60c2-111">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze.md), [gestures](gestures.md), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span>

<span data-ttu-id="f60c2-112">本教學課程需要大約1小時才能完成。</span><span class="sxs-lookup"><span data-stu-id="f60c2-112">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="f60c2-113">裝置支援</span><span class="sxs-lookup"><span data-stu-id="f60c2-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="f60c2-114">粗</span><span class="sxs-lookup"><span data-stu-id="f60c2-114">Course</span></span></th><th style="width:150px"> <span data-ttu-id="f60c2-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f60c2-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f60c2-116"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="f60c2-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="f60c2-117">MR 基本 101:使用裝置完成專案</span><span class="sxs-lookup"><span data-stu-id="f60c2-117">MR Basics 101: Complete project with device</span></span></td><td style="text-align: center;"> <span data-ttu-id="f60c2-118">✔️</span><span class="sxs-lookup"><span data-stu-id="f60c2-118">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="f60c2-119">開始之前</span><span class="sxs-lookup"><span data-stu-id="f60c2-119">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="f60c2-120">先決條件</span><span class="sxs-lookup"><span data-stu-id="f60c2-120">Prerequisites</span></span>

* <span data-ttu-id="f60c2-121">[已安裝正確工具](install-the-tools.md)的 WINDOWS 10 電腦。</span><span class="sxs-lookup"><span data-stu-id="f60c2-121">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="f60c2-122">[為開發設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="f60c2-122">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="f60c2-123">專案檔案</span><span class="sxs-lookup"><span data-stu-id="f60c2-123">Project files</span></span>

* <span data-ttu-id="f60c2-124">下載專案所需的[檔案](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="f60c2-124">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="f60c2-125"> 需要 Unity 2017.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="f60c2-125"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="f60c2-126">如果您仍然需要 Unity 5.6 支援, 請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="f60c2-126">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="f60c2-127">如果您仍然需要 Unity 5.5 支援, 請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="f60c2-127">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="f60c2-128">如果您仍然需要 Unity 5.4 支援, 請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="f60c2-128">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="f60c2-129">將檔案取消封存至您的桌面或其他容易到達的位置。</span><span class="sxs-lookup"><span data-stu-id="f60c2-129">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="f60c2-130">將資料夾名稱保留為 [**折紙**]。</span><span class="sxs-lookup"><span data-stu-id="f60c2-130">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="f60c2-131">如果您想要在下載之前查看原始程式碼, 可以[在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)取得。</span><span class="sxs-lookup"><span data-stu-id="f60c2-131">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="f60c2-132">第1章-「Hololens」世界</span><span class="sxs-lookup"><span data-stu-id="f60c2-132">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

<span data-ttu-id="f60c2-133">在本章中, 我們將設定第一個 Unity 專案, 並逐步執行組建和部署流程。</span><span class="sxs-lookup"><span data-stu-id="f60c2-133">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="f60c2-134">目標</span><span class="sxs-lookup"><span data-stu-id="f60c2-134">Objectives</span></span>

* <span data-ttu-id="f60c2-135">設定 Unity 以進行全像攝影開發。</span><span class="sxs-lookup"><span data-stu-id="f60c2-135">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="f60c2-136">建立全息影像。</span><span class="sxs-lookup"><span data-stu-id="f60c2-136">Make a hologram.</span></span>
* <span data-ttu-id="f60c2-137">查看您製作的全息影像。</span><span class="sxs-lookup"><span data-stu-id="f60c2-137">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="f60c2-138">指示</span><span class="sxs-lookup"><span data-stu-id="f60c2-138">Instructions</span></span>

* <span data-ttu-id="f60c2-139">啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="f60c2-139">Start Unity.</span></span>
* <span data-ttu-id="f60c2-140">選取 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="f60c2-140">Select **Open**.</span></span>
* <span data-ttu-id="f60c2-141">輸入 [位置] 做為您先前未封存的 [**折紙**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f60c2-141">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="f60c2-142">選取 [**折紙**], 然後按一下 [**選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="f60c2-142">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="f60c2-143">因為**折紙**專案不包含場景, 所以請使用將空的預設場景儲存至新檔案:將場景**另存為。**  / </span><span class="sxs-lookup"><span data-stu-id="f60c2-143">Since the **Origami** project does not contain a scene, save the empty default scene to a new file using: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="f60c2-144">將新場景命名為 [**折紙**], 然後按 [**儲存**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f60c2-144">Name the new scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-virtual-camera"></a><span data-ttu-id="f60c2-145">設定主要虛擬攝影機</span><span class="sxs-lookup"><span data-stu-id="f60c2-145">Setup the main virtual camera</span></span>

* <span data-ttu-id="f60c2-146">在 [階層]**面板**中, 選取 [**主要相機**]。</span><span class="sxs-lookup"><span data-stu-id="f60c2-146">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="f60c2-147">在偵測**器**中, 將其轉換位置設為**0, 0, 0**。</span><span class="sxs-lookup"><span data-stu-id="f60c2-147">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="f60c2-148">尋找 [**清除旗標**] 屬性, 並將下拉式清單從 [ **Skybox** ] 變更為 [**單色**]。</span><span class="sxs-lookup"><span data-stu-id="f60c2-148">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="f60c2-149">按一下 [**背景**] 欄位, 以開啟色彩選擇器。</span><span class="sxs-lookup"><span data-stu-id="f60c2-149">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="f60c2-150">將**R、G、B 和 A**設定為**0**。</span><span class="sxs-lookup"><span data-stu-id="f60c2-150">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="f60c2-151">設定場景</span><span class="sxs-lookup"><span data-stu-id="f60c2-151">Setup the scene</span></span>

* <span data-ttu-id="f60c2-152">在 [階層]**面板**中, 按一下 [**建立**] 並**建立空**的。</span><span class="sxs-lookup"><span data-stu-id="f60c2-152">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="f60c2-153">以滑鼠右鍵按一下新的**GameObject** , 然後選取 [重新命名]。</span><span class="sxs-lookup"><span data-stu-id="f60c2-153">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="f60c2-154">將 GameObject 重新命名為**OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="f60c2-154">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="f60c2-155">從 [專案] 面板中的 [**全息影像**] 資料夾 (展開 [資產], 然後選取 [全息], 或按兩下 [專案] 面板中的 [全息影像] 資料夾</span><span class="sxs-lookup"><span data-stu-id="f60c2-155">From the **Holograms** folder in the Project Panel (expand Assets and select Holograms or double click the Holograms folder in the Project Panel):</span></span>
  * <span data-ttu-id="f60c2-156">將**階段**拖曳到階層中, 成為**OrigamiCollection**的子系。</span><span class="sxs-lookup"><span data-stu-id="f60c2-156">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="f60c2-157">將**Sphere1**拖曳到階層中, 成為**OrigamiCollection**的子系。</span><span class="sxs-lookup"><span data-stu-id="f60c2-157">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="f60c2-158">將**Sphere2**拖曳到階層中, 成為**OrigamiCollection**的子系。</span><span class="sxs-lookup"><span data-stu-id="f60c2-158">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="f60c2-159">以滑鼠右鍵按一下 [階層]**面板**中的 [**方向光源**] 物件, 然後選取 [**刪除**]。</span><span class="sxs-lookup"><span data-stu-id="f60c2-159">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="f60c2-160">從 [**全息影像**] 資料夾, 將 [**燈光**] 拖曳至 [階層]**面板**的根目錄。</span><span class="sxs-lookup"><span data-stu-id="f60c2-160">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="f60c2-161">在階層中, 選取 [ **OrigamiCollection**]。</span><span class="sxs-lookup"><span data-stu-id="f60c2-161">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="f60c2-162">在偵測**器**中, 將轉換位置設定為**0,-0.5, 2.0**。</span><span class="sxs-lookup"><span data-stu-id="f60c2-162">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="f60c2-163">按下 Unity 中的 [**播放**] 按鈕, 以預覽您的全息影像。</span><span class="sxs-lookup"><span data-stu-id="f60c2-163">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="f60c2-164">您應該會在預覽視窗中看到 [折紙] 物件。</span><span class="sxs-lookup"><span data-stu-id="f60c2-164">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="f60c2-165">按第二次 [**播放**] 以停止預覽模式。</span><span class="sxs-lookup"><span data-stu-id="f60c2-165">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="f60c2-166">將專案從 Unity 匯出至 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f60c2-166">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="f60c2-167">在 Unity 中, 選取 檔案 **> 組建設定**。</span><span class="sxs-lookup"><span data-stu-id="f60c2-167">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="f60c2-168">在 [**平臺**] 清單中選取**通用 Windows 平臺**, 然後按一下 [**切換平臺**]。</span><span class="sxs-lookup"><span data-stu-id="f60c2-168">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="f60c2-169">將 [ **SDK** ] 設定為 [**通用 10** ], 將 [**組建類型**] 設為**D3D**</span><span class="sxs-lookup"><span data-stu-id="f60c2-169">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="f60c2-170">檢查**Unity C#專案**。</span><span class="sxs-lookup"><span data-stu-id="f60c2-170">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="f60c2-171">按一下 [新增] [**開啟場景**] 以加入場景。</span><span class="sxs-lookup"><span data-stu-id="f60c2-171">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="f60c2-172">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="f60c2-172">Click **Build**.</span></span>
* <span data-ttu-id="f60c2-173">在出現的 [檔案瀏覽器] 視窗中, 建立名為 "App" 的**新資料夾**。</span><span class="sxs-lookup"><span data-stu-id="f60c2-173">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="f60c2-174">按一下 [**應用程式] 資料夾**。</span><span class="sxs-lookup"><span data-stu-id="f60c2-174">Single click the **App Folder**.</span></span>
* <span data-ttu-id="f60c2-175">按 [**選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="f60c2-175">Press **Select Folder**.</span></span>
* <span data-ttu-id="f60c2-176">當 Unity 完成時, 將會出現 [檔案瀏覽器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="f60c2-176">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="f60c2-177">開啟**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="f60c2-177">Open the **App** folder.</span></span>
* <span data-ttu-id="f60c2-178">開啟 (按兩下) [**折紙**]。</span><span class="sxs-lookup"><span data-stu-id="f60c2-178">Open (double click) **Origami.sln**.</span></span>
* <span data-ttu-id="f60c2-179">使用 Visual Studio 中的頂端工具列, 將目標從 [調試] 變更為 [**發行**], 將 [從 ARM] 變更為**X86**。</span><span class="sxs-lookup"><span data-stu-id="f60c2-179">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="f60c2-180">按一下 [裝置] 按鈕旁邊的箭號, 然後選取 [**遠端電腦**] 以透過 wi-fi 進行部署。</span><span class="sxs-lookup"><span data-stu-id="f60c2-180">Click on the arrow next to the Device button, and select **Remote Machine** to deploy over Wi-Fi.</span></span>
  * <span data-ttu-id="f60c2-181">將**位址**設定為 HoloLens 的名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="f60c2-181">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="f60c2-182">如果您不知道您的裝置 IP 位址, 請查看 [**設定] > 網路 & [網際網路] > [Advanced Options** **] 或 [你好 cortana, 我的 IP 位址是什麼？]**</span><span class="sxs-lookup"><span data-stu-id="f60c2-182">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
  * <span data-ttu-id="f60c2-183">如果 HoloLens 是透過 USB 連接, 您可以改為選取 [**裝置**] 以透過 usb 進行部署。</span><span class="sxs-lookup"><span data-stu-id="f60c2-183">If the HoloLens is attached over USB, you may instead select **Device** to deploy over USB.</span></span>
  * <span data-ttu-id="f60c2-184">將 [**驗證模式]** 保持設定為 [**通用**]。</span><span class="sxs-lookup"><span data-stu-id="f60c2-184">Leave the **Authentication Mode** set to **Universal**.</span></span>
  * <span data-ttu-id="f60c2-185">按一下 [**選取**]</span><span class="sxs-lookup"><span data-stu-id="f60c2-185">Click **Select**</span></span>

* <span data-ttu-id="f60c2-186">按一下 [ **Debug > 啟動但不進行調試**] 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="f60c2-186">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="f60c2-187">如果這是您第一次部署至您的裝置, 您必須將[它與 Visual Studio 配對](using-visual-studio.md#pairing-your-device-hololens-(1st-gen))。</span><span class="sxs-lookup"><span data-stu-id="f60c2-187">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens-(1st-gen)).</span></span>

* <span data-ttu-id="f60c2-188">現在, 折紙專案會建立、部署至您的 HoloLens, 然後執行。</span><span class="sxs-lookup"><span data-stu-id="f60c2-188">The Origami project will now build, deploy to your HoloLens, and then run.</span></span>
* <span data-ttu-id="f60c2-189">放在您的 HoloLens 上, 並查看您的新全息影像。</span><span class="sxs-lookup"><span data-stu-id="f60c2-189">Put on your HoloLens and look around to see your new holograms.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="f60c2-190">第2章-注視</span><span class="sxs-lookup"><span data-stu-id="f60c2-190">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

<span data-ttu-id="f60c2-191">在本章中, 我們將引進三種與您的全息影像互動的第一種方式:[注視](gaze.md)。</span><span class="sxs-lookup"><span data-stu-id="f60c2-191">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="f60c2-192">目標</span><span class="sxs-lookup"><span data-stu-id="f60c2-192">Objectives</span></span>

* <span data-ttu-id="f60c2-193">使用世界鎖定的游標來視覺化您的注視。</span><span class="sxs-lookup"><span data-stu-id="f60c2-193">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="f60c2-194">指示</span><span class="sxs-lookup"><span data-stu-id="f60c2-194">Instructions</span></span>

* <span data-ttu-id="f60c2-195">回到您的 Unity 專案, 並關閉 [組建設定] 視窗 (如果仍處於開啟狀態)。</span><span class="sxs-lookup"><span data-stu-id="f60c2-195">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="f60c2-196">在 [**專案] 面板**中選取 [**全息影像**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f60c2-196">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="f60c2-197">將**游標**物件拖曳至根層級的 [階層]**面板**。</span><span class="sxs-lookup"><span data-stu-id="f60c2-197">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="f60c2-198">按兩下**游標**物件以深入瞭解它。</span><span class="sxs-lookup"><span data-stu-id="f60c2-198">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="f60c2-199">以滑鼠右鍵按一下 [專案] 面板中的 [**腳本**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f60c2-199">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="f60c2-200">按一下 [**建立**] 子功能表。</span><span class="sxs-lookup"><span data-stu-id="f60c2-200">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="f60c2-201">選取 **C# [腳本**]。</span><span class="sxs-lookup"><span data-stu-id="f60c2-201">Select **C# Script**.</span></span>
* <span data-ttu-id="f60c2-202">將腳本命名為**WorldCursor**。</span><span class="sxs-lookup"><span data-stu-id="f60c2-202">Name the script **WorldCursor**.</span></span> <span data-ttu-id="f60c2-203">注意:此名稱區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="f60c2-203">Note: The name is case-sensitive.</span></span> <span data-ttu-id="f60c2-204">您不需要新增 .cs 副檔名。</span><span class="sxs-lookup"><span data-stu-id="f60c2-204">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="f60c2-205">在 [階層]**面板**中選取**游標**物件。</span><span class="sxs-lookup"><span data-stu-id="f60c2-205">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="f60c2-206">將**WorldCursor**腳本拖放到 [偵測**器] 面板**中。</span><span class="sxs-lookup"><span data-stu-id="f60c2-206">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="f60c2-207">按兩下 [ **WorldCursor** ] 腳本, 在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="f60c2-207">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="f60c2-208">將此程式碼複製並貼到**WorldCursor.cs**中, 並**全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="f60c2-208">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

* <span data-ttu-id="f60c2-209">從 [檔案] **> 組建設定**重建應用程式。</span><span class="sxs-lookup"><span data-stu-id="f60c2-209">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="f60c2-210">回到先前用來部署至 HoloLens 的 Visual Studio 解決方案。</span><span class="sxs-lookup"><span data-stu-id="f60c2-210">Return to the Visual Studio solution previously used to deploy to your HoloLens.</span></span>
* <span data-ttu-id="f60c2-211">出現提示時, 選取 [全部重載]。</span><span class="sxs-lookup"><span data-stu-id="f60c2-211">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="f60c2-212">按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="f60c2-212">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="f60c2-213">現在查看場景, 並留意游標如何與物件的形狀互動。</span><span class="sxs-lookup"><span data-stu-id="f60c2-213">Now look around the scene and notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="f60c2-214">第3章-手勢</span><span class="sxs-lookup"><span data-stu-id="f60c2-214">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

<span data-ttu-id="f60c2-215">在本章中, 我們將新增[手勢](gestures.md)的支援。</span><span class="sxs-lookup"><span data-stu-id="f60c2-215">In this chapter, we'll add support for [gestures](gestures.md).</span></span> <span data-ttu-id="f60c2-216">當使用者選取紙球體時, 我們會使用 Unity 的物理引擎來開啟重心, 讓球體變得更容易。</span><span class="sxs-lookup"><span data-stu-id="f60c2-216">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="f60c2-217">目標</span><span class="sxs-lookup"><span data-stu-id="f60c2-217">Objectives</span></span>

* <span data-ttu-id="f60c2-218">使用選取手勢控制您的全息影像。</span><span class="sxs-lookup"><span data-stu-id="f60c2-218">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="f60c2-219">指示</span><span class="sxs-lookup"><span data-stu-id="f60c2-219">Instructions</span></span>

<span data-ttu-id="f60c2-220">首先, 我們會建立腳本, 然後偵測選取手勢。</span><span class="sxs-lookup"><span data-stu-id="f60c2-220">We'll start by creating a script then can detect the Select gesture.</span></span>

* <span data-ttu-id="f60c2-221">在 [**腳本**] 資料夾中, 建立名為**GazeGestureManager**的腳本。</span><span class="sxs-lookup"><span data-stu-id="f60c2-221">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="f60c2-222">將**GazeGestureManager**腳本拖曳至階層中的**OrigamiCollection**物件。</span><span class="sxs-lookup"><span data-stu-id="f60c2-222">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="f60c2-223">在 Visual Studio 中開啟**GazeGestureManager**腳本, 並新增下列程式碼:</span><span class="sxs-lookup"><span data-stu-id="f60c2-223">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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

* <span data-ttu-id="f60c2-224">在 Scripts 資料夾中建立另一個腳本, 這次名為**SphereCommands**。</span><span class="sxs-lookup"><span data-stu-id="f60c2-224">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="f60c2-225">在 [階層] 視圖中展開 [ **OrigamiCollection** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="f60c2-225">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="f60c2-226">將**SphereCommands**腳本拖曳至 [階層] 面板中的**Sphere1**物件。</span><span class="sxs-lookup"><span data-stu-id="f60c2-226">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="f60c2-227">將**SphereCommands**腳本拖曳至 [階層] 面板中的**Sphere2**物件。</span><span class="sxs-lookup"><span data-stu-id="f60c2-227">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="f60c2-228">在 Visual Studio 中開啟腳本進行編輯, 並將預設程式碼取代為:</span><span class="sxs-lookup"><span data-stu-id="f60c2-228">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="f60c2-229">匯出、建立應用程式, 並將其部署至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="f60c2-229">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="f60c2-230">查看其中一個球體。</span><span class="sxs-lookup"><span data-stu-id="f60c2-230">Look at one of the spheres.</span></span>
* <span data-ttu-id="f60c2-231">執行 [選取手勢] 並監看球體拖放到下方的表面。</span><span class="sxs-lookup"><span data-stu-id="f60c2-231">Perform the select gesture and watch the sphere drop onto the surface below.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="f60c2-232">第4章-語音</span><span class="sxs-lookup"><span data-stu-id="f60c2-232">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

<span data-ttu-id="f60c2-233">在本章中, 我們將新增兩個[語音命令](voice-input.md)的支援:「重設世界」以將捨棄的球面傳回其原始位置, 而「卸載球體」則讓球體落在一起。</span><span class="sxs-lookup"><span data-stu-id="f60c2-233">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to return the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="f60c2-234">目標</span><span class="sxs-lookup"><span data-stu-id="f60c2-234">Objectives</span></span>

* <span data-ttu-id="f60c2-235">新增一律在背景中接聽的語音命令。</span><span class="sxs-lookup"><span data-stu-id="f60c2-235">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="f60c2-236">建立可回應語音命令的全息影像。</span><span class="sxs-lookup"><span data-stu-id="f60c2-236">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="f60c2-237">指示</span><span class="sxs-lookup"><span data-stu-id="f60c2-237">Instructions</span></span>

* <span data-ttu-id="f60c2-238">在 [**腳本**] 資料夾中, 建立名為**SpeechManager**的腳本。</span><span class="sxs-lookup"><span data-stu-id="f60c2-238">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="f60c2-239">將**SpeechManager**腳本拖曳至階層中的**OrigamiCollection**物件</span><span class="sxs-lookup"><span data-stu-id="f60c2-239">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="f60c2-240">在 Visual Studio 中開啟**SpeechManager**腳本。</span><span class="sxs-lookup"><span data-stu-id="f60c2-240">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="f60c2-241">將此程式碼複製並貼到**SpeechManager.cs**中, 並**全部儲存**:</span><span class="sxs-lookup"><span data-stu-id="f60c2-241">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="f60c2-242">在 Visual Studio 中開啟**SphereCommands**腳本。</span><span class="sxs-lookup"><span data-stu-id="f60c2-242">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="f60c2-243">更新腳本以進行讀取, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="f60c2-243">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="f60c2-244">匯出、建立應用程式, 並將其部署至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="f60c2-244">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="f60c2-245">查看其中一個球體, 並說「卸載**球體**」。</span><span class="sxs-lookup"><span data-stu-id="f60c2-245">Look at one of the spheres, and say "**Drop Sphere**".</span></span>
* <span data-ttu-id="f60c2-246">請說「**重設世界**」, 使其回到其初始位置。</span><span class="sxs-lookup"><span data-stu-id="f60c2-246">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="f60c2-247">第5章-空間音效</span><span class="sxs-lookup"><span data-stu-id="f60c2-247">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

<span data-ttu-id="f60c2-248">在本章中, 我們會將音樂新增至應用程式, 然後觸發對特定動作的音效效果。</span><span class="sxs-lookup"><span data-stu-id="f60c2-248">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="f60c2-249">我們會使用[空間音效](spatial-sound.md), 在3d 空間中提供特定位置的聲音。</span><span class="sxs-lookup"><span data-stu-id="f60c2-249">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="f60c2-250">目標</span><span class="sxs-lookup"><span data-stu-id="f60c2-250">Objectives</span></span>

* <span data-ttu-id="f60c2-251">聆聽您世界中的全息影像。</span><span class="sxs-lookup"><span data-stu-id="f60c2-251">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="f60c2-252">指示</span><span class="sxs-lookup"><span data-stu-id="f60c2-252">Instructions</span></span>

* <span data-ttu-id="f60c2-253">在 Unity 中從頂端功能表中選取 [**編輯] > 專案設定 > 音訊**</span><span class="sxs-lookup"><span data-stu-id="f60c2-253">In Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="f60c2-254">在右側的 [偵測器] 面板中, 尋找 [**空間定位器外掛程式**] 設定, 然後選取 [ **MS HRTF 空間定位器**]。</span><span class="sxs-lookup"><span data-stu-id="f60c2-254">In the Inspector Panel on the right side, find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="f60c2-255">從 [專案] 面板的 [**全息影像**] 資料夾中, 將 [**環境**] 物件拖曳至 [階層] 面板中的 [ **OrigamiCollection** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="f60c2-255">From the **Holograms** folder in the Project panel, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="f60c2-256">選取 [ **OrigamiCollection** ], 然後在 [偵測器] 面板中尋找 [**音訊來源**] 元件。</span><span class="sxs-lookup"><span data-stu-id="f60c2-256">Select **OrigamiCollection** and find the **Audio Source** component in the Inspector panel.</span></span> <span data-ttu-id="f60c2-257">變更這些屬性:</span><span class="sxs-lookup"><span data-stu-id="f60c2-257">Change these properties:</span></span>
  * <span data-ttu-id="f60c2-258">檢查**Spatialize**屬性。</span><span class="sxs-lookup"><span data-stu-id="f60c2-258">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="f60c2-259">勾選 [**在喚醒時播放**]。</span><span class="sxs-lookup"><span data-stu-id="f60c2-259">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="f60c2-260">將 [**空間 Blend** ] 變更為 [ **3d** ], 方法是將滑杆向右拖曳。</span><span class="sxs-lookup"><span data-stu-id="f60c2-260">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span> <span data-ttu-id="f60c2-261">當您移動滑杆時, 此值應該從0變更為1。</span><span class="sxs-lookup"><span data-stu-id="f60c2-261">The value should change from 0 to 1 when you move the slider.</span></span>
  * <span data-ttu-id="f60c2-262">檢查 [**迴圈**] 屬性。</span><span class="sxs-lookup"><span data-stu-id="f60c2-262">Check the **Loop** property.</span></span>
  * <span data-ttu-id="f60c2-263">展開 [ **3D 音效設定**], 然後針對 [ **Doppler 層級**] 輸入**0.1** 。</span><span class="sxs-lookup"><span data-stu-id="f60c2-263">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="f60c2-264">將 [**磁片區 Rolloff** ] 設定為 [**對數 Rolloff**]。</span><span class="sxs-lookup"><span data-stu-id="f60c2-264">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="f60c2-265">將 [**最大距離**] 設定為**20**。</span><span class="sxs-lookup"><span data-stu-id="f60c2-265">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="f60c2-266">在 [**腳本**] 資料夾中, 建立名為**SphereSounds**的腳本。</span><span class="sxs-lookup"><span data-stu-id="f60c2-266">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="f60c2-267">將**SphereSounds**拖放至階層中的**Sphere1**和**Sphere2**物件。</span><span class="sxs-lookup"><span data-stu-id="f60c2-267">Drag and drop **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="f60c2-268">在 Visual Studio 中開啟**SphereSounds** , 更新下列程式碼並**全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="f60c2-268">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="f60c2-269">儲存腳本, 並返回 Unity。</span><span class="sxs-lookup"><span data-stu-id="f60c2-269">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="f60c2-270">匯出、建立應用程式, 並將其部署至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="f60c2-270">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="f60c2-271">從階段中往上和往上移動, 然後再將其關閉, 以聽到音效的改變。</span><span class="sxs-lookup"><span data-stu-id="f60c2-271">Move closer and further from the Stage and turn side-to-side to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="f60c2-272">第6章-空間對應</span><span class="sxs-lookup"><span data-stu-id="f60c2-272">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

<span data-ttu-id="f60c2-273">現在我們要使用[空間對應](spatial-mapping.md), 將遊戲面板放在真實世界中的實際物件上。</span><span class="sxs-lookup"><span data-stu-id="f60c2-273">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="f60c2-274">目標</span><span class="sxs-lookup"><span data-stu-id="f60c2-274">Objectives</span></span>

* <span data-ttu-id="f60c2-275">將您的真實世界帶入虛擬世界。</span><span class="sxs-lookup"><span data-stu-id="f60c2-275">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="f60c2-276">將您的全息影像放在對您最重要的地方。</span><span class="sxs-lookup"><span data-stu-id="f60c2-276">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="f60c2-277">指示</span><span class="sxs-lookup"><span data-stu-id="f60c2-277">Instructions</span></span>

* <span data-ttu-id="f60c2-278">在 Unity 中, 按一下 [專案] 面板中的 [**全息影像**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f60c2-278">In Unity, click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="f60c2-279">將**空間對應**資產拖曳至階層的根目錄。</span><span class="sxs-lookup"><span data-stu-id="f60c2-279">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="f60c2-280">按一下階層中的 [**空間對應**] 物件。</span><span class="sxs-lookup"><span data-stu-id="f60c2-280">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="f60c2-281">在 [偵測**器] 面板**中, 變更下列屬性:</span><span class="sxs-lookup"><span data-stu-id="f60c2-281">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="f60c2-282">勾選 [**繪製視覺網格**] 方塊。</span><span class="sxs-lookup"><span data-stu-id="f60c2-282">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="f60c2-283">找出 [**繪製材質**], 然後按一下右側的圓形。</span><span class="sxs-lookup"><span data-stu-id="f60c2-283">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="f60c2-284">在頂端的搜尋欄位中輸入「**線框**」。</span><span class="sxs-lookup"><span data-stu-id="f60c2-284">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="f60c2-285">按一下結果, 然後關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="f60c2-285">Click on the result and then close the window.</span></span> <span data-ttu-id="f60c2-286">當您這麼做時, [繪製材質] 的值應該會設定為 [線框]。</span><span class="sxs-lookup"><span data-stu-id="f60c2-286">When you do this, the value for Draw Material should get set to Wireframe.</span></span>
* <span data-ttu-id="f60c2-287">匯出、建立應用程式, 並將其部署至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="f60c2-287">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="f60c2-288">當應用程式執行時, 線框網格會覆迭您的真實世界。</span><span class="sxs-lookup"><span data-stu-id="f60c2-288">When the app runs, a wireframe mesh will overlay your real world.</span></span>
* <span data-ttu-id="f60c2-289">觀賞輪流球體如何落在舞臺上, 以及在地面上!</span><span class="sxs-lookup"><span data-stu-id="f60c2-289">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="f60c2-290">現在, 我們將示範如何將 OrigamiCollection 移到新的位置:</span><span class="sxs-lookup"><span data-stu-id="f60c2-290">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="f60c2-291">在 [**腳本**] 資料夾中, 建立名為**TapToPlaceParent**的腳本。</span><span class="sxs-lookup"><span data-stu-id="f60c2-291">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="f60c2-292">在階層中, 展開 [ **OrigamiCollection** ], 然後選取 [**階段**] 物件。</span><span class="sxs-lookup"><span data-stu-id="f60c2-292">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="f60c2-293">將**TapToPlaceParent**腳本拖曳至階段物件。</span><span class="sxs-lookup"><span data-stu-id="f60c2-293">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="f60c2-294">在 Visual Studio 中開啟**TapToPlaceParent**腳本, 並將它更新為下列內容:</span><span class="sxs-lookup"><span data-stu-id="f60c2-294">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="f60c2-295">匯出、建立及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="f60c2-295">Export, build and deploy the app.</span></span>
* <span data-ttu-id="f60c2-296">現在您應該可以在特定位置撥雲見日遊戲, 方法是使用選取手勢然後移至新位置, 然後再次使用 [選取] 手勢。</span><span class="sxs-lookup"><span data-stu-id="f60c2-296">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="chapter-7---holographic-fun"></a><span data-ttu-id="f60c2-297">第7章-全像攝影</span><span class="sxs-lookup"><span data-stu-id="f60c2-297">Chapter 7 - Holographic fun</span></span>

### <a name="objectives"></a><span data-ttu-id="f60c2-298">目標</span><span class="sxs-lookup"><span data-stu-id="f60c2-298">Objectives</span></span>

* <span data-ttu-id="f60c2-299">顯示全像全像 underworld 的進入。</span><span class="sxs-lookup"><span data-stu-id="f60c2-299">Reveal the entrance to a holographic underworld.</span></span>

### <a name="instructions"></a><span data-ttu-id="f60c2-300">指示</span><span class="sxs-lookup"><span data-stu-id="f60c2-300">Instructions</span></span>

<span data-ttu-id="f60c2-301">現在, 我們將為您示範如何發掘全像攝影 underworld:</span><span class="sxs-lookup"><span data-stu-id="f60c2-301">Now we'll show you how to uncover the holographic underworld:</span></span>

* <span data-ttu-id="f60c2-302">從 [專案] 面板中的 [**全息影像**] 資料夾:</span><span class="sxs-lookup"><span data-stu-id="f60c2-302">From the **Holograms** folder in the Project Panel:</span></span>
  * <span data-ttu-id="f60c2-303">將**Underworld**拖曳到階層中, 成為**OrigamiCollection**的子系。</span><span class="sxs-lookup"><span data-stu-id="f60c2-303">Drag **Underworld** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="f60c2-304">在 [**腳本**] 資料夾中, 建立名為**HitTarget**的腳本。</span><span class="sxs-lookup"><span data-stu-id="f60c2-304">In the **Scripts** folder, create a script named **HitTarget**.</span></span>
* <span data-ttu-id="f60c2-305">在階層中, 展開 [ **OrigamiCollection**]。</span><span class="sxs-lookup"><span data-stu-id="f60c2-305">In the **Hierarchy**, expand the **OrigamiCollection**.</span></span>
* <span data-ttu-id="f60c2-306">展開 [**階段**] 物件, 然後選取 [**目標**物件 (藍色風扇)]。</span><span class="sxs-lookup"><span data-stu-id="f60c2-306">Expand the **Stage** object and select the **Target** object (blue fan).</span></span>
* <span data-ttu-id="f60c2-307">將**HitTarget**腳本拖曳至**目標**物件。</span><span class="sxs-lookup"><span data-stu-id="f60c2-307">Drag the **HitTarget** script onto the **Target** object.</span></span>
* <span data-ttu-id="f60c2-308">在 Visual Studio 中開啟**HitTarget**腳本, 並將它更新為下列內容:</span><span class="sxs-lookup"><span data-stu-id="f60c2-308">Open the **HitTarget** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="f60c2-309">在 [Unity] 中, 選取**目標**物件。</span><span class="sxs-lookup"><span data-stu-id="f60c2-309">In Unity, select the **Target** object.</span></span>
* <span data-ttu-id="f60c2-310">現在會在叫用**目標**元件上顯示兩個公用屬性, 而且需要參考我們場景中的物件:</span><span class="sxs-lookup"><span data-stu-id="f60c2-310">Two public properties are now visible on the **Hit Target** component and need to reference objects in our scene:</span></span>
  * <span data-ttu-id="f60c2-311">將 [ **Underworld** ]從 [階層] 面板拖曳至 [**點擊目標**] 元件上的 [ **Underworld** ] 屬性。</span><span class="sxs-lookup"><span data-stu-id="f60c2-311">Drag **Underworld** from the **Hierarchy** panel to the **Underworld** property on the **Hit Target** component.</span></span>
  * <span data-ttu-id="f60c2-312">將 [**階段**]從 [階層] 面板拖曳至 [物件],**以隱藏** **點擊目標**元件上的屬性。</span><span class="sxs-lookup"><span data-stu-id="f60c2-312">Drag **Stage** from the **Hierarchy** panel to the **Object to Hide** property on the **Hit Target** component.</span></span>
* <span data-ttu-id="f60c2-313">匯出、建立及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="f60c2-313">Export, build and deploy the app.</span></span>
* <span data-ttu-id="f60c2-314">將 [折紙] 集合放在樓層, 然後使用 [選取手勢] 來放置球體。</span><span class="sxs-lookup"><span data-stu-id="f60c2-314">Place the Origami Collection on the floor, and then use the Select gesture to make a sphere drop.</span></span>
* <span data-ttu-id="f60c2-315">當球體到達目標 (藍色風扇) 時, 將會發生激增。</span><span class="sxs-lookup"><span data-stu-id="f60c2-315">When the sphere hits the target (blue fan), an explosion will occur.</span></span> <span data-ttu-id="f60c2-316">將會隱藏集合, 並顯示 underworld 的洞。</span><span class="sxs-lookup"><span data-stu-id="f60c2-316">The collection will be hidden and a hole to the underworld will appear.</span></span>

## <a name="the-end"></a><span data-ttu-id="f60c2-317">結束</span><span class="sxs-lookup"><span data-stu-id="f60c2-317">The end</span></span>

<span data-ttu-id="f60c2-318">這就是本教學課程的結尾!</span><span class="sxs-lookup"><span data-stu-id="f60c2-318">And that's the end of this tutorial!</span></span>

<span data-ttu-id="f60c2-319">您已瞭解:</span><span class="sxs-lookup"><span data-stu-id="f60c2-319">You learned:</span></span>

* <span data-ttu-id="f60c2-320">如何在 Unity 中建立全像攝影應用程式。</span><span class="sxs-lookup"><span data-stu-id="f60c2-320">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="f60c2-321">如何使用 [注視]、[手勢]、[聲音]、[聲音] 和 [空間對應]。</span><span class="sxs-lookup"><span data-stu-id="f60c2-321">How to make use of gaze, gesture, voice, sound, and spatial mapping.</span></span>
* <span data-ttu-id="f60c2-322">如何使用 Visual Studio 建立及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="f60c2-322">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="f60c2-323">您現在已準備好開始建立您自己的全像攝影體驗!</span><span class="sxs-lookup"><span data-stu-id="f60c2-323">You are now ready to start creating your own holographic experience!</span></span>

## <a name="see-also"></a><span data-ttu-id="f60c2-324">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f60c2-324">See also</span></span>

* [<span data-ttu-id="f60c2-325">MR Basics 101E：使用模擬器完成專案</span><span class="sxs-lookup"><span data-stu-id="f60c2-325">MR Basics 101E: Complete project with emulator</span></span>](holograms-101e.md)
* [<span data-ttu-id="f60c2-326">目光</span><span class="sxs-lookup"><span data-stu-id="f60c2-326">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="f60c2-327">筆勢</span><span class="sxs-lookup"><span data-stu-id="f60c2-327">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="f60c2-328">語音輸入</span><span class="sxs-lookup"><span data-stu-id="f60c2-328">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="f60c2-329">空間音效</span><span class="sxs-lookup"><span data-stu-id="f60c2-329">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="f60c2-330">空間對應</span><span class="sxs-lookup"><span data-stu-id="f60c2-330">Spatial mapping</span></span>](spatial-mapping.md)
