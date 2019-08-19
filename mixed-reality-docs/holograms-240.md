---
title: MR 分享 240-多個 HoloLens 裝置
description: 請遵循使用 Unity、Visual Studio 和 HoloLens 進行的編碼逐步解說, 以瞭解共用全息影像的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, 共用, 網路, 學院, 教學課程
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522337"
---
>[!NOTE]
><span data-ttu-id="90b4a-104">混合現實學術教學課程的設計是使用 HoloLens (第1代) 和混合現實的沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="90b4a-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="90b4a-105">因此, 對於仍在尋找這些裝置開發指引的開發人員而言, 我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="90b4a-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="90b4a-106">這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="90b4a-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="90b4a-107">系統會保留這些資訊, 以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="90b4a-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="90b4a-108">未來將會有一系列新的教學課程, 將示範如何針對 HoloLens 2 進行開發。</span><span class="sxs-lookup"><span data-stu-id="90b4a-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="90b4a-109">此通知會在張貼時, 使用這些教學課程的連結進行更新。</span><span class="sxs-lookup"><span data-stu-id="90b4a-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a><span data-ttu-id="90b4a-110">MR 分享 240:多個 HoloLens 裝置</span><span class="sxs-lookup"><span data-stu-id="90b4a-110">MR Sharing 240: Multiple HoloLens devices</span></span>

<span data-ttu-id="90b4a-111">在我們的世界中, 當我們在空間上移動時, 會將全像投影。</span><span class="sxs-lookup"><span data-stu-id="90b4a-111">Holograms are given presence in our world by remaining in place as we move about in space.</span></span> <span data-ttu-id="90b4a-112">HoloLens 會藉由使用各種[座標系統](coordinate-systems.md)來追蹤物件的位置和方向, 以保持全息。</span><span class="sxs-lookup"><span data-stu-id="90b4a-112">HoloLens keeps holograms in place by using various [coordinate systems](coordinate-systems.md) to keep track of the location and orientation of objects.</span></span> <span data-ttu-id="90b4a-113">當我們在裝置之間共用這些座標系統時, 我們可以建立共用體驗, 讓我們參與共用的全像世界。</span><span class="sxs-lookup"><span data-stu-id="90b4a-113">When we share these coordinate systems between devices, we can create a shared experience that allows us to take part in a shared holographic world.</span></span>

<span data-ttu-id="90b4a-114">在本教學課程中, 我們將:</span><span class="sxs-lookup"><span data-stu-id="90b4a-114">In this tutorial, we will:</span></span>

* <span data-ttu-id="90b4a-115">設定共用體驗的網路。</span><span class="sxs-lookup"><span data-stu-id="90b4a-115">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="90b4a-116">跨 HoloLens 裝置共用全息影像。</span><span class="sxs-lookup"><span data-stu-id="90b4a-116">Share holograms across HoloLens devices.</span></span>
* <span data-ttu-id="90b4a-117">探索我們分享的全像世界中的其他人。</span><span class="sxs-lookup"><span data-stu-id="90b4a-117">Discover other people in our shared holographic world.</span></span>
* <span data-ttu-id="90b4a-118">建立可讓您以其他玩家為目標並啟動炮彈的共用互動式體驗!</span><span class="sxs-lookup"><span data-stu-id="90b4a-118">Create a shared interactive experience where you can target other players - and launch projectiles at them!</span></span>

## <a name="device-support"></a><span data-ttu-id="90b4a-119">裝置支援</span><span class="sxs-lookup"><span data-stu-id="90b4a-119">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="90b4a-120">粗</span><span class="sxs-lookup"><span data-stu-id="90b4a-120">Course</span></span></th><th style="width:150px"> <span data-ttu-id="90b4a-121"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="90b4a-121"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="90b4a-122"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="90b4a-122"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="90b4a-123">MR 分享 240:多個 HoloLens 裝置</span><span class="sxs-lookup"><span data-stu-id="90b4a-123">MR Sharing 240: Multiple HoloLens devices</span></span></td><td style="text-align: center;"> <span data-ttu-id="90b4a-124">✔️</span><span class="sxs-lookup"><span data-stu-id="90b4a-124">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="90b4a-125">開始之前</span><span class="sxs-lookup"><span data-stu-id="90b4a-125">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="90b4a-126">必要條件</span><span class="sxs-lookup"><span data-stu-id="90b4a-126">Prerequisites</span></span>

* <span data-ttu-id="90b4a-127">以網際網路存取所安裝的正確[工具](install-the-tools.md)設定的 WINDOWS 10 電腦。</span><span class="sxs-lookup"><span data-stu-id="90b4a-127">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md) with Internet access.</span></span>
* <span data-ttu-id="90b4a-128">至少有兩個[設定為開發的](using-visual-studio.md#enabling-developer-mode)HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="90b4a-128">At least two HoloLens devices [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="90b4a-129">專案檔案</span><span class="sxs-lookup"><span data-stu-id="90b4a-129">Project files</span></span>

* <span data-ttu-id="90b4a-130">下載專案所需的[檔案](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip)。</span><span class="sxs-lookup"><span data-stu-id="90b4a-130">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) required by the project.</span></span> <span data-ttu-id="90b4a-131">需要 Unity 2017.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="90b4a-131">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="90b4a-132">如果您仍然需要 Unity 5.6 支援, 請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip)。</span><span class="sxs-lookup"><span data-stu-id="90b4a-132">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span></span>
  * <span data-ttu-id="90b4a-133">如果您仍然需要 Unity 5.5 支援, 請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip)。</span><span class="sxs-lookup"><span data-stu-id="90b4a-133">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span></span>
  * <span data-ttu-id="90b4a-134">如果您仍然需要 Unity 5.4 支援, 請使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip)。</span><span class="sxs-lookup"><span data-stu-id="90b4a-134">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span></span>
* <span data-ttu-id="90b4a-135">將檔案取消封存至您的桌面或其他容易到達的位置。</span><span class="sxs-lookup"><span data-stu-id="90b4a-135">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="90b4a-136">將資料夾名稱保留為**SharedHolograms**。</span><span class="sxs-lookup"><span data-stu-id="90b4a-136">Keep the folder name as **SharedHolograms**.</span></span>

>[!NOTE]
><span data-ttu-id="90b4a-137">如果您想要在下載之前查看原始程式碼, 可以[在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms)取得。</span><span class="sxs-lookup"><span data-stu-id="90b4a-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="90b4a-138">第1章-Hololens 世界</span><span class="sxs-lookup"><span data-stu-id="90b4a-138">Chapter 1 - Holo World</span></span>

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

<span data-ttu-id="90b4a-139">在本章中, 我們將設定第一個 Unity 專案, 並逐步執行組建和部署流程。</span><span class="sxs-lookup"><span data-stu-id="90b4a-139">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="90b4a-140">目標</span><span class="sxs-lookup"><span data-stu-id="90b4a-140">Objectives</span></span>

* <span data-ttu-id="90b4a-141">設定 Unity 以開發全像攝影應用程式。</span><span class="sxs-lookup"><span data-stu-id="90b4a-141">Setup Unity to develop holographic apps.</span></span>
* <span data-ttu-id="90b4a-142">查看您的全息影像!</span><span class="sxs-lookup"><span data-stu-id="90b4a-142">See your hologram!</span></span>

### <a name="instructions"></a><span data-ttu-id="90b4a-143">指示</span><span class="sxs-lookup"><span data-stu-id="90b4a-143">Instructions</span></span>

* <span data-ttu-id="90b4a-144">啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="90b4a-144">Start Unity.</span></span>
* <span data-ttu-id="90b4a-145">選取 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="90b4a-145">Select **Open**.</span></span>
* <span data-ttu-id="90b4a-146">輸入 location 作為您先前 unarchived 的**SharedHolograms**資料夾。</span><span class="sxs-lookup"><span data-stu-id="90b4a-146">Enter location as the **SharedHolograms** folder you previously unarchived.</span></span>
* <span data-ttu-id="90b4a-147">選取 [**專案名稱**], 然後按一下 [**選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="90b4a-147">Select **Project Name** and click **Select Folder**.</span></span>
* <span data-ttu-id="90b4a-148">在階層中, 以滑鼠右鍵按一下**主要相機**, 然後選取 [**刪除**]。</span><span class="sxs-lookup"><span data-stu-id="90b4a-148">In the **Hierarchy**, right-click the **Main Camera** and select **Delete**.</span></span>
* <span data-ttu-id="90b4a-149">在 [ **HoloToolkit-共用-240/Prefabs/攝影機**] 資料夾中, 尋找**主要相機**prefab。</span><span class="sxs-lookup"><span data-stu-id="90b4a-149">In the **HoloToolkit-Sharing-240/Prefabs/Camera** folder, find the **Main Camera** prefab.</span></span>
* <span data-ttu-id="90b4a-150">將**主要相機**拖放到階層中。</span><span class="sxs-lookup"><span data-stu-id="90b4a-150">Drag and drop the **Main Camera** into the **Hierarchy**.</span></span>
* <span data-ttu-id="90b4a-151">在階層中, 按一下 [**建立**] 並**建立空**的。</span><span class="sxs-lookup"><span data-stu-id="90b4a-151">In the **Hierarchy**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="90b4a-152">以滑鼠右鍵按一下新的**GameObject** , 然後選取 [**重新命名**]。</span><span class="sxs-lookup"><span data-stu-id="90b4a-152">Right-click the new **GameObject** and select **Rename**.</span></span>
* <span data-ttu-id="90b4a-153">將 GameObject 重新命名為**HologramCollection**。</span><span class="sxs-lookup"><span data-stu-id="90b4a-153">Rename the GameObject to **HologramCollection**.</span></span>
* <span data-ttu-id="90b4a-154">選取階層中的 [ **HologramCollection** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="90b4a-154">Select the **HologramCollection** object in the **Hierarchy**.</span></span>
* <span data-ttu-id="90b4a-155">在偵測**器**中, 將**轉換位置**設定為:**X0, Y:-0.25, Z:2**。</span><span class="sxs-lookup"><span data-stu-id="90b4a-155">In the **Inspector** set the **transform position** to: **X: 0, Y: -0.25, Z: 2**.</span></span>
* <span data-ttu-id="90b4a-156">在 [**專案] 面板**的 [**全息影像**] 資料夾中, 尋找**EnergyHub**資產。</span><span class="sxs-lookup"><span data-stu-id="90b4a-156">In the **Holograms** folder in the **Project panel**, find the **EnergyHub** asset.</span></span>
* <span data-ttu-id="90b4a-157">將**EnergyHub**物件從 [**專案] 面板**拖放至階層 , 做為**HologramCollection 的子**系。</span><span class="sxs-lookup"><span data-stu-id="90b4a-157">Drag and drop the **EnergyHub** object from the **Project panel** to the **Hierarchy** as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="90b4a-158">選取 [檔案] **> 另存場景**。</span><span class="sxs-lookup"><span data-stu-id="90b4a-158">Select **File > Save Scene As...**</span></span>
* <span data-ttu-id="90b4a-159">將場景命名為**SharedHolograms** , 然後按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="90b4a-159">Name the scene **SharedHolograms** and click **Save**.</span></span>
* <span data-ttu-id="90b4a-160">按下 Unity 中的 [**播放**] 按鈕, 以預覽您的全息影像。</span><span class="sxs-lookup"><span data-stu-id="90b4a-160">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="90b4a-161">按第二次 [**播放**] 以停止預覽模式。</span><span class="sxs-lookup"><span data-stu-id="90b4a-161">Press **Play** a second time to stop preview mode.</span></span>

<span data-ttu-id="90b4a-162">**將專案從 Unity 匯出至 Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="90b4a-162">**Export the project from Unity to Visual Studio**</span></span>
* <span data-ttu-id="90b4a-163">在 Unity 中, 選取 檔案 **> 組建設定**。</span><span class="sxs-lookup"><span data-stu-id="90b4a-163">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="90b4a-164">按一下 [新增] [**開啟場景**] 以加入場景。</span><span class="sxs-lookup"><span data-stu-id="90b4a-164">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="90b4a-165">在 [**平臺**] 清單中選取**通用 Windows 平臺**, 然後按一下 [**切換平臺**]。</span><span class="sxs-lookup"><span data-stu-id="90b4a-165">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="90b4a-166">將**SDK**設定為**通用 10**。</span><span class="sxs-lookup"><span data-stu-id="90b4a-166">Set **SDK** to **Universal 10**.</span></span>
* <span data-ttu-id="90b4a-167">將 [**目標裝置**] 設定為**HoloLens** , 將**UWP 組建類型**設為 [ **D3D**]。</span><span class="sxs-lookup"><span data-stu-id="90b4a-167">Set **Target device** to **HoloLens** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="90b4a-168">檢查**Unity C#專案**。</span><span class="sxs-lookup"><span data-stu-id="90b4a-168">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="90b4a-169">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="90b4a-169">Click **Build**.</span></span>
* <span data-ttu-id="90b4a-170">在出現的 [檔案瀏覽器] 視窗中, 建立名為 "App" 的**新資料夾**。</span><span class="sxs-lookup"><span data-stu-id="90b4a-170">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="90b4a-171">按一下 [**應用程式**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="90b4a-171">Single click the **App** folder.</span></span>
* <span data-ttu-id="90b4a-172">按 [**選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="90b4a-172">Press **Select Folder**.</span></span>
* <span data-ttu-id="90b4a-173">當 Unity 完成時, 將會出現 [檔案瀏覽器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="90b4a-173">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="90b4a-174">開啟**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="90b4a-174">Open the **App** folder.</span></span>
* <span data-ttu-id="90b4a-175">開啟**SharedHolograms**以啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="90b4a-175">Open **SharedHolograms.sln** to launch Visual Studio.</span></span>
* <span data-ttu-id="90b4a-176">使用 Visual Studio 中的頂端工具列, 將目標從 [調試] 變更為 [**發行**], 將 [從 ARM] 變更為**X86**。</span><span class="sxs-lookup"><span data-stu-id="90b4a-176">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="90b4a-177">按一下 [本機電腦] 旁的下拉式箭號, 然後選取 [**遠端裝置**]。</span><span class="sxs-lookup"><span data-stu-id="90b4a-177">Click on the drop-down arrow next to Local Machine, and select **Remote Device**.</span></span>
    * <span data-ttu-id="90b4a-178">將**位址**設定為 HoloLens 的名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="90b4a-178">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="90b4a-179">如果您不知道您的裝置 IP 位址, 請查看 [**設定] > 網路 & [網際網路] > [Advanced Options** **] 或 [你好 cortana, 我的 IP 位址是什麼？]**</span><span class="sxs-lookup"><span data-stu-id="90b4a-179">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
    * <span data-ttu-id="90b4a-180">將 [**驗證模式]** 保持設定為 [**通用**]。</span><span class="sxs-lookup"><span data-stu-id="90b4a-180">Leave the **Authentication Mode** set to **Universal**.</span></span>
    * <span data-ttu-id="90b4a-181">按一下 [**選取**]</span><span class="sxs-lookup"><span data-stu-id="90b4a-181">Click **Select**</span></span>
* <span data-ttu-id="90b4a-182">按一下 [ **Debug > 啟動但不進行調試**] 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="90b4a-182">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="90b4a-183">如果這是您第一次部署至您的裝置, 您必須將[它與 Visual Studio 配對](using-visual-studio.md#pairing-your-device-hololens)。</span><span class="sxs-lookup"><span data-stu-id="90b4a-183">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
* <span data-ttu-id="90b4a-184">放入 HoloLens 並尋找 EnergyHub 的全息影像。</span><span class="sxs-lookup"><span data-stu-id="90b4a-184">Put on your HoloLens and find the EnergyHub hologram.</span></span>

## <a name="chapter-2---interaction"></a><span data-ttu-id="90b4a-185">第2章-互動</span><span class="sxs-lookup"><span data-stu-id="90b4a-185">Chapter 2 - Interaction</span></span>

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

<span data-ttu-id="90b4a-186">在本章中, 我們將與我們的全息影像互動。</span><span class="sxs-lookup"><span data-stu-id="90b4a-186">In this chapter, we'll interact with our holograms.</span></span> <span data-ttu-id="90b4a-187">首先, 我們要新增游標來視覺化我們的[注視](gaze.md)。</span><span class="sxs-lookup"><span data-stu-id="90b4a-187">First, we'll add a cursor to visualize our [Gaze](gaze.md).</span></span> <span data-ttu-id="90b4a-188">然後, 我們將新增[手勢](gestures.md), 並使用我們的手將全息影像放在空間中。</span><span class="sxs-lookup"><span data-stu-id="90b4a-188">Then, we'll add [Gestures](gestures.md) and use our hand to place our holograms in space.</span></span>

### <a name="objectives"></a><span data-ttu-id="90b4a-189">目標</span><span class="sxs-lookup"><span data-stu-id="90b4a-189">Objectives</span></span>

* <span data-ttu-id="90b4a-190">使用注視輸入來控制資料指標。</span><span class="sxs-lookup"><span data-stu-id="90b4a-190">Use gaze input to control a cursor.</span></span>
* <span data-ttu-id="90b4a-191">使用手勢輸入來與全息影像互動。</span><span class="sxs-lookup"><span data-stu-id="90b4a-191">Use gesture input to interact with holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="90b4a-192">指示</span><span class="sxs-lookup"><span data-stu-id="90b4a-192">Instructions</span></span>

<span data-ttu-id="90b4a-193">**目光**</span><span class="sxs-lookup"><span data-stu-id="90b4a-193">**Gaze**</span></span>
* <span data-ttu-id="90b4a-194">在 [階層]**面板**中, 選取 [ **HologramCollection** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="90b4a-194">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="90b4a-195">在 [偵測**器] 面板**中, 按一下 [**加入元件**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="90b4a-195">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="90b4a-196">在功能表中, 在搜尋方塊中輸入 [**注視管理員**]。</span><span class="sxs-lookup"><span data-stu-id="90b4a-196">In the menu, type in the search box **Gaze Manager**.</span></span> <span data-ttu-id="90b4a-197">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="90b4a-197">Select the search result.</span></span>
* <span data-ttu-id="90b4a-198">在**HoloToolkit-Sharing-240\Prefabs\Input**資料夾中, 尋找資料**指標**資產。</span><span class="sxs-lookup"><span data-stu-id="90b4a-198">In the **HoloToolkit-Sharing-240\Prefabs\Input** folder, find the **Cursor** asset.</span></span>
* <span data-ttu-id="90b4a-199">將**游標**資產拖放到階層上。</span><span class="sxs-lookup"><span data-stu-id="90b4a-199">Drag and drop the **Cursor** asset onto the **Hierarchy**.</span></span>

<span data-ttu-id="90b4a-200">**#**</span><span class="sxs-lookup"><span data-stu-id="90b4a-200">**Gesture**</span></span>
* <span data-ttu-id="90b4a-201">在 [階層]**面板**中, 選取 [ **HologramCollection** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="90b4a-201">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="90b4a-202">按一下 [**新增元件**], 然後在 [搜尋] 欄位中輸入**手勢管理員**。</span><span class="sxs-lookup"><span data-stu-id="90b4a-202">Click **Add Component** and type **Gesture Manager** in the search field.</span></span> <span data-ttu-id="90b4a-203">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="90b4a-203">Select the search result.</span></span>
* <span data-ttu-id="90b4a-204">在 [階層]**面板**中, 展開 [ **HologramCollection**]。</span><span class="sxs-lookup"><span data-stu-id="90b4a-204">In the **Hierarchy panel**, expand **HologramCollection**.</span></span>
* <span data-ttu-id="90b4a-205">選取子**EnergyHub**物件。</span><span class="sxs-lookup"><span data-stu-id="90b4a-205">Select the child **EnergyHub** object.</span></span>
* <span data-ttu-id="90b4a-206">在 [偵測**器] 面板**中, 按一下 [**加入元件**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="90b4a-206">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="90b4a-207">在功能表中, 于 [搜尋] 方塊中輸入「**全息影像」位置**。</span><span class="sxs-lookup"><span data-stu-id="90b4a-207">In the menu, type in the search box **Hologram Placement**.</span></span> <span data-ttu-id="90b4a-208">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="90b4a-208">Select the search result.</span></span>
* <span data-ttu-id="90b4a-209">選取 [檔案] **> 儲存場景**, 以儲存場景。</span><span class="sxs-lookup"><span data-stu-id="90b4a-209">Save the scene by selecting **File > Save Scene**.</span></span>

<span data-ttu-id="90b4a-210">**部署和享用**</span><span class="sxs-lookup"><span data-stu-id="90b4a-210">**Deploy and enjoy**</span></span>
* <span data-ttu-id="90b4a-211">使用上一章中的指示, 建立並部署至您的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="90b4a-211">Build and deploy to your HoloLens, using the instructions from the previous chapter.</span></span>
* <span data-ttu-id="90b4a-212">一旦應用程式在您的 HoloLens 上啟動, 請移動您的頭部, 並留意 EnergyHub 如何遵循您的注視。</span><span class="sxs-lookup"><span data-stu-id="90b4a-212">Once the app launches on your HoloLens, move your head around and notice how the EnergyHub follows your gaze.</span></span>
* <span data-ttu-id="90b4a-213">請注意, 當您注視全息的全像投影時, 游標會如何顯示, 而不會在全息的撥雲見日時, 會變更為點光線。</span><span class="sxs-lookup"><span data-stu-id="90b4a-213">Notice how the cursor appears when you gaze upon the hologram, and changes to a point light when not gazing at a hologram.</span></span>
* <span data-ttu-id="90b4a-214">執行 [空中] 以放置全息影像。</span><span class="sxs-lookup"><span data-stu-id="90b4a-214">Perform an air-tap to place the hologram.</span></span> <span data-ttu-id="90b4a-215">在我們的專案中, 您目前只能放置全息影像一次 (重新部署以重試)。</span><span class="sxs-lookup"><span data-stu-id="90b4a-215">At this time in our project, you can only place the hologram once (redeploy to try again).</span></span>

## <a name="chapter-3---shared-coordinates"></a><span data-ttu-id="90b4a-216">第3章-共用座標</span><span class="sxs-lookup"><span data-stu-id="90b4a-216">Chapter 3 - Shared Coordinates</span></span>

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

<span data-ttu-id="90b4a-217">查看和與全息影像互動很有趣, 但讓我們繼續進行。</span><span class="sxs-lookup"><span data-stu-id="90b4a-217">It's fun to see and interact with holograms, but let's go further.</span></span> <span data-ttu-id="90b4a-218">我們會設定我們的第一個共用體驗-每個人都可以一起查看的全息影像。</span><span class="sxs-lookup"><span data-stu-id="90b4a-218">We'll set up our first shared experience - a hologram everyone can see together.</span></span>

### <a name="objectives"></a><span data-ttu-id="90b4a-219">目標</span><span class="sxs-lookup"><span data-stu-id="90b4a-219">Objectives</span></span>

* <span data-ttu-id="90b4a-220">設定共用體驗的網路。</span><span class="sxs-lookup"><span data-stu-id="90b4a-220">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="90b4a-221">建立通用參考點。</span><span class="sxs-lookup"><span data-stu-id="90b4a-221">Establish a common reference point.</span></span>
* <span data-ttu-id="90b4a-222">跨裝置共用座標系統。</span><span class="sxs-lookup"><span data-stu-id="90b4a-222">Share coordinate systems across devices.</span></span>
* <span data-ttu-id="90b4a-223">每個人都看到相同的全息影像!</span><span class="sxs-lookup"><span data-stu-id="90b4a-223">Everyone sees the same hologram!</span></span>

>[!NOTE]
><span data-ttu-id="90b4a-224">必須為應用程式宣告**InternetClientServer**和**PrivateNetworkClientServer**功能, 才能連接到共用伺服器。</span><span class="sxs-lookup"><span data-stu-id="90b4a-224">The **InternetClientServer** and **PrivateNetworkClientServer** capabilities must be declared for an app to connect to the sharing server.</span></span> <span data-ttu-id="90b4a-225">這是針對您已在全息記錄240中完成的作業, 但請記住您自己的專案。</span><span class="sxs-lookup"><span data-stu-id="90b4a-225">This is done for you already in Holograms 240, but keep this in mind for your own projects.</span></span>
>1. <span data-ttu-id="90b4a-226">在 Unity 編輯器中, 流覽至 [編輯 > 專案設定 > Player], 移至播放程式設定</span><span class="sxs-lookup"><span data-stu-id="90b4a-226">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="90b4a-227">按一下 [Windows Store] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="90b4a-227">Click on the "Windows Store" tab</span></span>
>3. <span data-ttu-id="90b4a-228">在 [發佈設定 > 功能] 區段中, 檢查**InternetClientServer**功能和**PrivateNetworkClientServer**功能</span><span class="sxs-lookup"><span data-stu-id="90b4a-228">In the "Publishing Settings > Capabilities" section, check the **InternetClientServer** capability and the **PrivateNetworkClientServer** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="90b4a-229">指示</span><span class="sxs-lookup"><span data-stu-id="90b4a-229">Instructions</span></span>

* <span data-ttu-id="90b4a-230">在 [**專案] 面板**中, 流覽至 [ **HoloToolkit-Sharing-240\Prefabs\Sharing** ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="90b4a-230">In the **Project panel** navigate to the **HoloToolkit-Sharing-240\Prefabs\Sharing** folder.</span></span>
* <span data-ttu-id="90b4a-231">將**共用**prefab 拖放到 [階層]**面板**中。</span><span class="sxs-lookup"><span data-stu-id="90b4a-231">Drag and drop the **Sharing** prefab into the **Hierarchy panel**.</span></span>

<span data-ttu-id="90b4a-232">接下來, 我們需要啟動共用服務。</span><span class="sxs-lookup"><span data-stu-id="90b4a-232">Next we need to launch the sharing service.</span></span> <span data-ttu-id="90b4a-233">只有**一部電腦**在共用體驗中, 才需要執行此步驟。</span><span class="sxs-lookup"><span data-stu-id="90b4a-233">Only **one PC** in the shared experience needs to do this step.</span></span>
* <span data-ttu-id="90b4a-234">在 Unity-在頂端功能表中, 選取 [ **HoloToolkit-共用-240] 功能表**。</span><span class="sxs-lookup"><span data-stu-id="90b4a-234">In Unity - in the top-hand menu - select the **HoloToolkit-Sharing-240 menu**.</span></span>
* <span data-ttu-id="90b4a-235">在下拉式選單中, 選取 [**啟動共用服務**] 專案。</span><span class="sxs-lookup"><span data-stu-id="90b4a-235">Select the **Launch Sharing Service** item in the drop-down.</span></span>
* <span data-ttu-id="90b4a-236">核取 [**私人網路**] 選項, 然後在出現防火牆提示時, 按一下 [**允許存取**]。</span><span class="sxs-lookup"><span data-stu-id="90b4a-236">Check the **Private Network** option and click **Allow Access** when the firewall prompt appears.</span></span>
* <span data-ttu-id="90b4a-237">記下 [共用服務主控台] 視窗中顯示的 IPv4 位址。</span><span class="sxs-lookup"><span data-stu-id="90b4a-237">Note down the IPv4 address displayed in the Sharing Service console window.</span></span> <span data-ttu-id="90b4a-238">這是與執行服務的電腦相同的 IP。</span><span class="sxs-lookup"><span data-stu-id="90b4a-238">This is the same IP as the machine the service is being run on.</span></span>

<span data-ttu-id="90b4a-239">遵循將加入共用體驗的**所有電腦**上的其餘指示。</span><span class="sxs-lookup"><span data-stu-id="90b4a-239">Follow the rest of the instructions on **all PCs** that will join the shared experience.</span></span>
* <span data-ttu-id="90b4a-240">在 [階層] 中, 選取 [**共用**] 物件。</span><span class="sxs-lookup"><span data-stu-id="90b4a-240">In the **Hierarchy**, select the **Sharing** object.</span></span>
* <span data-ttu-id="90b4a-241">在偵測**器**的**共用階段**元件上, 將**伺服器位址**從 ' localhost ' 變更為執行 SharingService 之電腦的 IPv4 位址。</span><span class="sxs-lookup"><span data-stu-id="90b4a-241">In the **Inspector**, on the **Sharing Stage** component, change the **Server Address** from 'localhost' to the IPv4 address of the machine running SharingService.exe.</span></span>
* <span data-ttu-id="90b4a-242">在階層中選取 [ **HologramCollection** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="90b4a-242">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="90b4a-243">在偵測**器**中, 按一下 [**加入元件**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="90b4a-243">In the **Inspector** click the **Add Component** button.</span></span>
* <span data-ttu-id="90b4a-244">在搜尋方塊中, 輸入匯**入匯出錨點管理員**。</span><span class="sxs-lookup"><span data-stu-id="90b4a-244">In the search box, type **Import Export Anchor Manager**.</span></span> <span data-ttu-id="90b4a-245">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="90b4a-245">Select the search result.</span></span>
* <span data-ttu-id="90b4a-246">在 [**專案] 面板**中, 流覽至 [**腳本**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="90b4a-246">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="90b4a-247">按兩下 [ **HologramPlacement** ] 腳本, 在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="90b4a-247">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="90b4a-248">將內容取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="90b4a-248">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;
        
        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* <span data-ttu-id="90b4a-249">回到 Unity, 選取 [階層]**面板**中的 [ **HologramCollection** ]。</span><span class="sxs-lookup"><span data-stu-id="90b4a-249">Back in Unity, select the **HologramCollection** in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="90b4a-250">在 [偵測**器] 面板**中, 按一下 [**加入元件**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="90b4a-250">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="90b4a-251">在功能表中, 于 [搜尋] 方塊中輸入 [**應用程式狀態管理員**]。</span><span class="sxs-lookup"><span data-stu-id="90b4a-251">In the menu, type in the search box **App State Manager**.</span></span> <span data-ttu-id="90b4a-252">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="90b4a-252">Select the search result.</span></span>

<span data-ttu-id="90b4a-253">**部署和享用**</span><span class="sxs-lookup"><span data-stu-id="90b4a-253">**Deploy and enjoy**</span></span>
* <span data-ttu-id="90b4a-254">建立 HoloLens 裝置的專案。</span><span class="sxs-lookup"><span data-stu-id="90b4a-254">Build the project for your HoloLens devices.</span></span>
* <span data-ttu-id="90b4a-255">指定一個要先部署的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="90b4a-255">Designate one HoloLens to deploy to first.</span></span> <span data-ttu-id="90b4a-256">您必須等到將錨點上傳至服務, 才能放置 EnergyHub (這可能需要 ~ 30-60 秒)。</span><span class="sxs-lookup"><span data-stu-id="90b4a-256">You will need to wait for the Anchor to be uploaded to the service before you can place the EnergyHub (this can take ~30-60 seconds).</span></span> <span data-ttu-id="90b4a-257">完成上傳之前, 會忽略您的點按手勢。</span><span class="sxs-lookup"><span data-stu-id="90b4a-257">Until the upload is done, your tap gestures will be ignored.</span></span>
* <span data-ttu-id="90b4a-258">放置 EnergyHub 之後, 其位置將會上傳至服務, 然後您就可以部署到其他所有的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="90b4a-258">After the EnergyHub has been placed, its location will be uploaded to the service and you can then deploy to all other HoloLens devices.</span></span>
* <span data-ttu-id="90b4a-259">當新的 HoloLens 第一次加入會話時, EnergyHub 在該裝置上的位置可能不正確。</span><span class="sxs-lookup"><span data-stu-id="90b4a-259">When a new HoloLens first joins the session, the location of the EnergyHub may not be correct on that device.</span></span> <span data-ttu-id="90b4a-260">不過, 一旦從服務下載錨點和 EnergyHub 位置, EnergyHub 應該會跳至新的共用位置。</span><span class="sxs-lookup"><span data-stu-id="90b4a-260">However, as soon as the anchor and EnergyHub locations have been downloaded from the service, the EnergyHub should jump to the new, shared location.</span></span> <span data-ttu-id="90b4a-261">如果這不是在 ~ 30-60 秒內發生, 請在設定錨點以收集更多的環境線索時, 逐步執行原始 HoloLens 的位置。</span><span class="sxs-lookup"><span data-stu-id="90b4a-261">If this does not happen within ~30-60 seconds, walk to where the original HoloLens was when setting the anchor to gather more environment clues.</span></span> <span data-ttu-id="90b4a-262">如果位置仍未鎖定, 請重新部署至裝置。</span><span class="sxs-lookup"><span data-stu-id="90b4a-262">If the location still does not lock on, redeploy to the device.</span></span>
* <span data-ttu-id="90b4a-263">當裝置已準備就緒且正在執行應用程式時, 請尋找 EnergyHub。</span><span class="sxs-lookup"><span data-stu-id="90b4a-263">When the devices are all ready and running the app, look for the EnergyHub.</span></span> <span data-ttu-id="90b4a-264">您是否同意全像投影的位置, 以及文字所面向的方向為何？</span><span class="sxs-lookup"><span data-stu-id="90b4a-264">Can you all agree on the hologram's location and which direction the text is facing?</span></span>

## <a name="chapter-4---discovery"></a><span data-ttu-id="90b4a-265">第4章-探索</span><span class="sxs-lookup"><span data-stu-id="90b4a-265">Chapter 4 - Discovery</span></span>

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

<span data-ttu-id="90b4a-266">所有人現在都可以看到相同的全息影像!</span><span class="sxs-lookup"><span data-stu-id="90b4a-266">Everyone can now see the same hologram!</span></span> <span data-ttu-id="90b4a-267">現在讓我們看看其他人連線到我們分享的全像世界。</span><span class="sxs-lookup"><span data-stu-id="90b4a-267">Now let's see everyone else connected to our shared holographic world.</span></span> <span data-ttu-id="90b4a-268">在本章中, 我們將在相同的共用會話中抓取所有其他 HoloLens 裝置的頭位置和旋轉。</span><span class="sxs-lookup"><span data-stu-id="90b4a-268">In this chapter, we'll grab the head location and rotation of all other HoloLens devices in the same sharing session.</span></span>

### <a name="objectives"></a><span data-ttu-id="90b4a-269">目標</span><span class="sxs-lookup"><span data-stu-id="90b4a-269">Objectives</span></span>

* <span data-ttu-id="90b4a-270">在我們的共用體驗中探索彼此。</span><span class="sxs-lookup"><span data-stu-id="90b4a-270">Discover each other in our shared experience.</span></span>
* <span data-ttu-id="90b4a-271">選擇並分享玩家頭像。</span><span class="sxs-lookup"><span data-stu-id="90b4a-271">Choose and share a player avatar.</span></span>
* <span data-ttu-id="90b4a-272">在每個人的標題旁附加玩家頭像。</span><span class="sxs-lookup"><span data-stu-id="90b4a-272">Attach the player avatar next to everyone's heads.</span></span>

### <a name="instructions"></a><span data-ttu-id="90b4a-273">指示</span><span class="sxs-lookup"><span data-stu-id="90b4a-273">Instructions</span></span>

* <span data-ttu-id="90b4a-274">在 [**專案] 面板**中, 流覽至 [**全息影像**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="90b4a-274">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="90b4a-275">將**PlayerAvatarStore**拖放到階層中。</span><span class="sxs-lookup"><span data-stu-id="90b4a-275">Drag and drop the **PlayerAvatarStore** into the **Hierarchy**.</span></span>
* <span data-ttu-id="90b4a-276">在 [**專案] 面板**中, 流覽至 [**腳本**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="90b4a-276">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="90b4a-277">按兩下 [ **AvatarSelector** ] 腳本, 在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="90b4a-277">Double-click the **AvatarSelector** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="90b4a-278">將內容取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="90b4a-278">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);        
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* <span data-ttu-id="90b4a-279">在階層中選取 [ **HologramCollection** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="90b4a-279">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="90b4a-280">在偵測**器**中, 按一下 [**加入元件**]。</span><span class="sxs-lookup"><span data-stu-id="90b4a-280">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="90b4a-281">在搜尋方塊中, 輸入**本機播放程式管理員**。</span><span class="sxs-lookup"><span data-stu-id="90b4a-281">In the search box, type **Local Player Manager**.</span></span> <span data-ttu-id="90b4a-282">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="90b4a-282">Select the search result.</span></span>
* <span data-ttu-id="90b4a-283">在階層中選取 [ **HologramCollection** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="90b4a-283">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="90b4a-284">在偵測**器**中, 按一下 [**加入元件**]。</span><span class="sxs-lookup"><span data-stu-id="90b4a-284">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="90b4a-285">在搜尋方塊中, 輸入**Remote Player Manager**。</span><span class="sxs-lookup"><span data-stu-id="90b4a-285">In the search box, type **Remote Player Manager**.</span></span> <span data-ttu-id="90b4a-286">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="90b4a-286">Select the search result.</span></span>
* <span data-ttu-id="90b4a-287">在 Visual Studio 中開啟**HologramPlacement**腳本。</span><span class="sxs-lookup"><span data-stu-id="90b4a-287">Open the **HologramPlacement** script in Visual Studio.</span></span>
* <span data-ttu-id="90b4a-288">將內容取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="90b4a-288">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* <span data-ttu-id="90b4a-289">在 Visual Studio 中開啟**AppStateManager**腳本。</span><span class="sxs-lookup"><span data-stu-id="90b4a-289">Open the **AppStateManager** script in Visual Studio.</span></span>
* <span data-ttu-id="90b4a-290">將內容取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="90b4a-290">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

<span data-ttu-id="90b4a-291">**部署和享用**</span><span class="sxs-lookup"><span data-stu-id="90b4a-291">**Deploy and Enjoy**</span></span>
* <span data-ttu-id="90b4a-292">建立專案並將其部署到您的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="90b4a-292">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="90b4a-293">當您聽到 ping 音效時, 請尋找 [頭像選擇] 功能表, 然後使用 [點一下] 手勢來選取 [頭像]。</span><span class="sxs-lookup"><span data-stu-id="90b4a-293">When you hear a pinging sound, find the avatar selection menu and select an avatar with the air-tap gesture.</span></span>
* <span data-ttu-id="90b4a-294">如果您不想要查看任何全息影像, 當 HoloLens 與服務通訊時, 游標周圍的點會變成不同的色彩: 初始化 (暗紫色)、下載錨點 (綠色)、匯入/匯出位置資料 (黃色)、上傳錨點 (藍色)。</span><span class="sxs-lookup"><span data-stu-id="90b4a-294">If you're not looking at any holograms, the point light around your cursor will turn a different color when your HoloLens is communicating with the service: initializing (dark purple), downloading the anchor (green), importing/exporting location data (yellow), uploading the anchor (blue).</span></span> <span data-ttu-id="90b4a-295">如果您游標周圍的點是預設色彩 (淺紫色), 表示您已準備好與會話中的其他玩家互動!</span><span class="sxs-lookup"><span data-stu-id="90b4a-295">If your point light around your cursor is the default color (light purple), then you are ready to interact with other players in your session!</span></span>
* <span data-ttu-id="90b4a-296">查看連接到您的空間的其他人-將會有一位全像的機器人浮動在其肩上, 並模擬其 head 運動!</span><span class="sxs-lookup"><span data-stu-id="90b4a-296">Look at other people connected to your space - there will be a holographic robot floating above their shoulder and mimicking their head motions!</span></span>

## <a name="chapter-5---placement"></a><span data-ttu-id="90b4a-297">第5章-放置</span><span class="sxs-lookup"><span data-stu-id="90b4a-297">Chapter 5 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

<span data-ttu-id="90b4a-298">在本章中, 我們會將錨點放在真實世界的表面上。</span><span class="sxs-lookup"><span data-stu-id="90b4a-298">In this chapter, we'll make the anchor able to be placed on real-world surfaces.</span></span> <span data-ttu-id="90b4a-299">我們會使用共用座標, 將該錨點置於連線到共用體驗的每個人之間的中間點。</span><span class="sxs-lookup"><span data-stu-id="90b4a-299">We'll use shared coordinates to place that anchor in the middle point between everyone connected to the shared experience.</span></span>

### <a name="objectives"></a><span data-ttu-id="90b4a-300">目標</span><span class="sxs-lookup"><span data-stu-id="90b4a-300">Objectives</span></span>

* <span data-ttu-id="90b4a-301">根據玩家的頭部位置, 將全息影像放在空間地圖上。</span><span class="sxs-lookup"><span data-stu-id="90b4a-301">Place holograms on the spatial map based on players’ head position.</span></span>

### <a name="instructions"></a><span data-ttu-id="90b4a-302">指示</span><span class="sxs-lookup"><span data-stu-id="90b4a-302">Instructions</span></span>

* <span data-ttu-id="90b4a-303">在 [**專案] 面板**中, 流覽至 [**全息影像**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="90b4a-303">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="90b4a-304">將**CustomSpatialMapping** prefab 拖放到階層上。</span><span class="sxs-lookup"><span data-stu-id="90b4a-304">Drag and drop the **CustomSpatialMapping** prefab onto the **Hierarchy**.</span></span>
* <span data-ttu-id="90b4a-305">在 [**專案] 面板**中, 流覽至 [**腳本**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="90b4a-305">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="90b4a-306">按兩下 [ **AppStateManager** ] 腳本, 在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="90b4a-306">Double-click the **AppStateManager** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="90b4a-307">將內容取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="90b4a-307">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to 
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a 
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* <span data-ttu-id="90b4a-308">在 [**專案] 面板**中, 流覽至 [**腳本**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="90b4a-308">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="90b4a-309">按兩下 [ **HologramPlacement** ] 腳本, 在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="90b4a-309">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="90b4a-310">將內容取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="90b4a-310">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the 
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

<span data-ttu-id="90b4a-311">**部署和享用**</span><span class="sxs-lookup"><span data-stu-id="90b4a-311">**Deploy and enjoy**</span></span>
* <span data-ttu-id="90b4a-312">建立專案並將其部署到您的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="90b4a-312">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="90b4a-313">當應用程式準備好時, 請將它放在圓形中, 並注意 EnergyHub 如何出現在每個人的中心。</span><span class="sxs-lookup"><span data-stu-id="90b4a-313">When the app is ready, stand in a circle and notice how the EnergyHub appears in the center of everyone.</span></span>
* <span data-ttu-id="90b4a-314">請點一下以放置 EnergyHub。</span><span class="sxs-lookup"><span data-stu-id="90b4a-314">Tap to place the EnergyHub.</span></span>
* <span data-ttu-id="90b4a-315">請嘗試語音命令「重設目標」來挑選 EnergyHub 備份, 並以群組方式一起運作, 以將全息影像移至新位置。</span><span class="sxs-lookup"><span data-stu-id="90b4a-315">Try the voice command 'Reset Target' to pick the EnergyHub back up and work together as a group to move the hologram to a new location.</span></span>

## <a name="chapter-6---real-world-physics"></a><span data-ttu-id="90b4a-316">第6章-真實世界的物理</span><span class="sxs-lookup"><span data-stu-id="90b4a-316">Chapter 6 - Real-World Physics</span></span>

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

<span data-ttu-id="90b4a-317">在本章中, 我們將新增可從真實世界表面跳動的全息影像。</span><span class="sxs-lookup"><span data-stu-id="90b4a-317">In this chapter we'll add holograms that bounce off real-world surfaces.</span></span> <span data-ttu-id="90b4a-318">觀賞您和朋友所啟動的專案, 填滿您的空間!</span><span class="sxs-lookup"><span data-stu-id="90b4a-318">Watch your space fill up with projects launched by both you and your friends!</span></span>

### <a name="objectives"></a><span data-ttu-id="90b4a-319">目標</span><span class="sxs-lookup"><span data-stu-id="90b4a-319">Objectives</span></span>

* <span data-ttu-id="90b4a-320">啟動會從真實世界表面跳動的炮彈。</span><span class="sxs-lookup"><span data-stu-id="90b4a-320">Launch projectiles that bounce off real-world surfaces.</span></span>
* <span data-ttu-id="90b4a-321">共用炮彈, 讓其他玩家可以看到它們。</span><span class="sxs-lookup"><span data-stu-id="90b4a-321">Share the projectiles so other players can see them.</span></span>

### <a name="instructions"></a><span data-ttu-id="90b4a-322">指示</span><span class="sxs-lookup"><span data-stu-id="90b4a-322">Instructions</span></span>

* <span data-ttu-id="90b4a-323">在階層中選取 [ **HologramCollection** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="90b4a-323">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="90b4a-324">在偵測**器**中, 按一下 [**加入元件**]。</span><span class="sxs-lookup"><span data-stu-id="90b4a-324">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="90b4a-325">在搜尋方塊中, 輸入**Projectile 啟動器**。</span><span class="sxs-lookup"><span data-stu-id="90b4a-325">In the search box, type **Projectile Launcher**.</span></span> <span data-ttu-id="90b4a-326">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="90b4a-326">Select the search result.</span></span>

<span data-ttu-id="90b4a-327">**部署和享用**</span><span class="sxs-lookup"><span data-stu-id="90b4a-327">**Deploy and enjoy**</span></span>
* <span data-ttu-id="90b4a-328">建立並部署至您的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="90b4a-328">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="90b4a-329">當應用程式在所有裝置上執行時, 請按下來在真實世界表面啟動 projectile。</span><span class="sxs-lookup"><span data-stu-id="90b4a-329">When the app is running on all devices, perform an air-tap to launch projectile at real world surfaces.</span></span>
* <span data-ttu-id="90b4a-330">瞭解當您的 projectile 與其他玩家的圖片衝突時, 會發生什麼事!</span><span class="sxs-lookup"><span data-stu-id="90b4a-330">See what happens when your projectile collides with another player's avatar!</span></span>

## <a name="chapter-7---grand-finale"></a><span data-ttu-id="90b4a-331">第7章-總計 Finale</span><span class="sxs-lookup"><span data-stu-id="90b4a-331">Chapter 7 - Grand Finale</span></span>

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

<span data-ttu-id="90b4a-332">在本章中, 我們將發現只能透過共同作業探索的入口網站。</span><span class="sxs-lookup"><span data-stu-id="90b4a-332">In this chapter, we'll uncover a portal that can only be discovered with collaboration.</span></span>

### <a name="objectives"></a><span data-ttu-id="90b4a-333">目標</span><span class="sxs-lookup"><span data-stu-id="90b4a-333">Objectives</span></span>

* <span data-ttu-id="90b4a-334">共同作業以在錨點上啟動足夠的炮彈, 以發現秘密入口網站!</span><span class="sxs-lookup"><span data-stu-id="90b4a-334">Work together to launch enough projectiles at the anchor to uncover a secret portal!</span></span>

### <a name="instructions"></a><span data-ttu-id="90b4a-335">指示</span><span class="sxs-lookup"><span data-stu-id="90b4a-335">Instructions</span></span>

* <span data-ttu-id="90b4a-336">在 [**專案] 面板**中, 流覽至 [**全息影像**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="90b4a-336">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="90b4a-337">將**Underworld**資產拖放為 HologramCollection 的**子**系。</span><span class="sxs-lookup"><span data-stu-id="90b4a-337">Drag and drop the **Underworld** asset as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="90b4a-338">選取**HologramCollection**後, 按一下偵測**器**中的 [**新增元件**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="90b4a-338">With **HologramCollection** selected, click the **Add Component** button in the **Inspector**.</span></span>
* <span data-ttu-id="90b4a-339">在功能表的 [搜尋] 方塊中, 輸入**ExplodeTarget**。</span><span class="sxs-lookup"><span data-stu-id="90b4a-339">In the menu, type in the search box **ExplodeTarget**.</span></span> <span data-ttu-id="90b4a-340">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="90b4a-340">Select the search result.</span></span>
* <span data-ttu-id="90b4a-341">選取**HologramCollection**之後, 從階層中, 將**EnergyHub**物件拖曳至偵測**器**中的**目標**欄位。</span><span class="sxs-lookup"><span data-stu-id="90b4a-341">With **HologramCollection** selected, from the **Hierarchy** drag the **EnergyHub** object to the **Target** field in the **Inspector**.</span></span>
* <span data-ttu-id="90b4a-342">選取**HologramCollection**之後, 從階層中, 將**Underworld**物件拖曳至偵測**器**中的 [ **Underworld** ] 欄位。</span><span class="sxs-lookup"><span data-stu-id="90b4a-342">With **HologramCollection** selected, from the **Hierarchy** drag the **Underworld** object to the **Underworld** field in the **Inspector**.</span></span>

<span data-ttu-id="90b4a-343">**部署和享用**</span><span class="sxs-lookup"><span data-stu-id="90b4a-343">**Deploy and enjoy**</span></span>
* <span data-ttu-id="90b4a-344">建立並部署至您的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="90b4a-344">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="90b4a-345">當應用程式啟動時, 共同合作以在 EnergyHub 啟動炮彈。</span><span class="sxs-lookup"><span data-stu-id="90b4a-345">When the app has launched, collaborate together to launch projectiles at the EnergyHub.</span></span>
* <span data-ttu-id="90b4a-346">當 underworld 出現時, 請在 underworld 機器人上啟動炮彈 (按下機器人三次以增加樂趣)。</span><span class="sxs-lookup"><span data-stu-id="90b4a-346">When the underworld appears, launch projectiles at underworld robots (hit a robot three times for extra fun).</span></span>
