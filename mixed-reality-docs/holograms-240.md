---
title: MR 共用 240-多個的 HoloLens 裝置
description: 遵循此程式碼逐步解說如何使用 Unity、 Visual Studio 和 HoloLens，若要了解共用全像投影的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、 mixedrealitytoolkit、 mixedrealitytoolkit unity、 共用、 網路、 academy、 教學課程
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594886"
---
>[!NOTE]
><span data-ttu-id="aecf0-104">混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。</span><span class="sxs-lookup"><span data-stu-id="aecf0-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="aecf0-105">因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。</span><span class="sxs-lookup"><span data-stu-id="aecf0-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="aecf0-106">這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="aecf0-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="aecf0-107">它們會繼續運作，支援的裝置上維護。</span><span class="sxs-lookup"><span data-stu-id="aecf0-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="aecf0-108">會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="aecf0-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="aecf0-109">當他們回傳時，本聲明將會更新這些教學課程的連結。</span><span class="sxs-lookup"><span data-stu-id="aecf0-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a><span data-ttu-id="aecf0-110">MR 共用 240:多個的 HoloLens 裝置</span><span class="sxs-lookup"><span data-stu-id="aecf0-110">MR Sharing 240: Multiple HoloLens devices</span></span>

<span data-ttu-id="aecf0-111">全像投影會就地剩餘的空間中的相關移，以提供我們的世界中的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="aecf0-111">Holograms are given presence in our world by remaining in place as we move about in space.</span></span> <span data-ttu-id="aecf0-112">HoloLens 就地保留全像投影，使用不同[座標系統](coordinate-systems.md)来追蹤的位置和方向的物件。</span><span class="sxs-lookup"><span data-stu-id="aecf0-112">HoloLens keeps holograms in place by using various [coordinate systems](coordinate-systems.md) to keep track of the location and orientation of objects.</span></span> <span data-ttu-id="aecf0-113">當我們共用這些裝置之間的座標系統時，我們可以建立可讓我們參與共用的全像攝影版世界分享的經驗。</span><span class="sxs-lookup"><span data-stu-id="aecf0-113">When we share these coordinate systems between devices, we can create a shared experience that allows us to take part in a shared holographic world.</span></span>

<span data-ttu-id="aecf0-114">在本教學課程中，我們將：</span><span class="sxs-lookup"><span data-stu-id="aecf0-114">In this tutorial, we will:</span></span>

* <span data-ttu-id="aecf0-115">設定網路，以分享經驗。</span><span class="sxs-lookup"><span data-stu-id="aecf0-115">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="aecf0-116">跨 HoloLens 裝置共用全像投影。</span><span class="sxs-lookup"><span data-stu-id="aecf0-116">Share holograms across HoloLens devices.</span></span>
* <span data-ttu-id="aecf0-117">探索我們共用全像攝影版的世界中的其他人員。</span><span class="sxs-lookup"><span data-stu-id="aecf0-117">Discover other people in our shared holographic world.</span></span>
* <span data-ttu-id="aecf0-118">建立共用的互動式體驗，您可以在此目標的其他玩家-並啟動在它們的砲彈 ！</span><span class="sxs-lookup"><span data-stu-id="aecf0-118">Create a shared interactive experience where you can target other players - and launch projectiles at them!</span></span>

## <a name="device-support"></a><span data-ttu-id="aecf0-119">裝置支援</span><span class="sxs-lookup"><span data-stu-id="aecf0-119">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="aecf0-120">課程</span><span class="sxs-lookup"><span data-stu-id="aecf0-120">Course</span></span></th><th style="width:150px"> <span data-ttu-id="aecf0-121"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="aecf0-121"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="aecf0-122"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="aecf0-122"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="aecf0-123">MR 共用 240:多個的 HoloLens 裝置</span><span class="sxs-lookup"><span data-stu-id="aecf0-123">MR Sharing 240: Multiple HoloLens devices</span></span></td><td style="text-align: center;"> <span data-ttu-id="aecf0-124">✔️</span><span class="sxs-lookup"><span data-stu-id="aecf0-124">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="aecf0-125">開始之前</span><span class="sxs-lookup"><span data-stu-id="aecf0-125">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="aecf0-126">先決條件</span><span class="sxs-lookup"><span data-stu-id="aecf0-126">Prerequisites</span></span>

* <span data-ttu-id="aecf0-127">Windows 10 電腦的正確設定[安裝工具](install-the-tools.md)具有網際網路存取。</span><span class="sxs-lookup"><span data-stu-id="aecf0-127">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md) with Internet access.</span></span>
* <span data-ttu-id="aecf0-128">兩個以上的 HoloLens 裝置[開發設定的](using-visual-studio.md#enabling-developer-mode)。</span><span class="sxs-lookup"><span data-stu-id="aecf0-128">At least two HoloLens devices [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="aecf0-129">專案檔</span><span class="sxs-lookup"><span data-stu-id="aecf0-129">Project files</span></span>

* <span data-ttu-id="aecf0-130">下載[檔案](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip)專案所需。</span><span class="sxs-lookup"><span data-stu-id="aecf0-130">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) required by the project.</span></span> <span data-ttu-id="aecf0-131">需要 Unity 2017.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="aecf0-131">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="aecf0-132">如果您仍然需要 Unity 5.6 的支援，請使用[本版](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip)。</span><span class="sxs-lookup"><span data-stu-id="aecf0-132">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span></span>
  * <span data-ttu-id="aecf0-133">如果您仍然需要 Unity 5.5 的支援，請使用[本版](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip)。</span><span class="sxs-lookup"><span data-stu-id="aecf0-133">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span></span>
  * <span data-ttu-id="aecf0-134">如果您仍然需要 Unity 5.4 的支援，請使用[本版](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip)。</span><span class="sxs-lookup"><span data-stu-id="aecf0-134">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span></span>
* <span data-ttu-id="aecf0-135">取消封存您的桌面或其他您輕鬆地連線到位置的檔案。</span><span class="sxs-lookup"><span data-stu-id="aecf0-135">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="aecf0-136">保留的資料夾名稱，作為**SharedHolograms**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-136">Keep the folder name as **SharedHolograms**.</span></span>

>[!NOTE]
><span data-ttu-id="aecf0-137">如果您想要查看原始程式碼，在下載之前，它有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms)。</span><span class="sxs-lookup"><span data-stu-id="aecf0-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="aecf0-138">第 1 章-Holo 世界</span><span class="sxs-lookup"><span data-stu-id="aecf0-138">Chapter 1 - Holo World</span></span>

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

<span data-ttu-id="aecf0-139">在本章中，我們將安裝程式，我們的第一個 Unity 專案並逐步執行組建和部署程序。</span><span class="sxs-lookup"><span data-stu-id="aecf0-139">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="aecf0-140">目標</span><span class="sxs-lookup"><span data-stu-id="aecf0-140">Objectives</span></span>

* <span data-ttu-id="aecf0-141">安裝 Unity 開發全像攝影版的應用程式。</span><span class="sxs-lookup"><span data-stu-id="aecf0-141">Setup Unity to develop holographic apps.</span></span>
* <span data-ttu-id="aecf0-142">請參閱您全像 ！</span><span class="sxs-lookup"><span data-stu-id="aecf0-142">See your hologram!</span></span>

### <a name="instructions"></a><span data-ttu-id="aecf0-143">指示</span><span class="sxs-lookup"><span data-stu-id="aecf0-143">Instructions</span></span>

* <span data-ttu-id="aecf0-144">啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="aecf0-144">Start Unity.</span></span>
* <span data-ttu-id="aecf0-145">選取 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-145">Select **Open**.</span></span>
* <span data-ttu-id="aecf0-146">輸入與位置**SharedHolograms**先前未封存的資料夾。</span><span class="sxs-lookup"><span data-stu-id="aecf0-146">Enter location as the **SharedHolograms** folder you previously unarchived.</span></span>
* <span data-ttu-id="aecf0-147">選取 **專案名稱**然後按一下**選取資料夾**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-147">Select **Project Name** and click **Select Folder**.</span></span>
* <span data-ttu-id="aecf0-148">在 **階層**，以滑鼠右鍵按一下**Main Camera** ，然後選取**刪除**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-148">In the **Hierarchy**, right-click the **Main Camera** and select **Delete**.</span></span>
* <span data-ttu-id="aecf0-149">在  **HoloToolkit 共用-240/Prefabs/攝影**資料夾中，尋找**Main Camera** prefab。</span><span class="sxs-lookup"><span data-stu-id="aecf0-149">In the **HoloToolkit-Sharing-240/Prefabs/Camera** folder, find the **Main Camera** prefab.</span></span>
* <span data-ttu-id="aecf0-150">將拖放**Main Camera**成**階層**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-150">Drag and drop the **Main Camera** into the **Hierarchy**.</span></span>
* <span data-ttu-id="aecf0-151">在**階層**，按一下**建立**並**建立空**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-151">In the **Hierarchy**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="aecf0-152">以滑鼠右鍵按一下 新**GameObject** ，然後選取**重新命名**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-152">Right-click the new **GameObject** and select **Rename**.</span></span>
* <span data-ttu-id="aecf0-153">重新命名以 GameObject **HologramCollection**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-153">Rename the GameObject to **HologramCollection**.</span></span>
* <span data-ttu-id="aecf0-154">選取  **HologramCollection**物件中**階層**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-154">Select the **HologramCollection** object in the **Hierarchy**.</span></span>
* <span data-ttu-id="aecf0-155">在  **Inspector**設定**將位置轉換**來：**X:0，Y:-0.25，Z:2**.</span><span class="sxs-lookup"><span data-stu-id="aecf0-155">In the **Inspector** set the **transform position** to: **X: 0, Y: -0.25, Z: 2**.</span></span>
* <span data-ttu-id="aecf0-156">在 **全像投影**資料夾中的**專案 面板**，尋找**EnergyHub**資產。</span><span class="sxs-lookup"><span data-stu-id="aecf0-156">In the **Holograms** folder in the **Project panel**, find the **EnergyHub** asset.</span></span>
* <span data-ttu-id="aecf0-157">將拖放**EnergyHub**物件 **[專案] 面板**來**階層**為**子系 HologramCollection**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-157">Drag and drop the **EnergyHub** object from the **Project panel** to the **Hierarchy** as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="aecf0-158">選取**檔案 > 儲存場景為...**</span><span class="sxs-lookup"><span data-stu-id="aecf0-158">Select **File > Save Scene As...**</span></span>
* <span data-ttu-id="aecf0-159">命名場景**SharedHolograms**然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-159">Name the scene **SharedHolograms** and click **Save**.</span></span>
* <span data-ttu-id="aecf0-160">按下**播放**預覽您全像投影的 Unity 中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="aecf0-160">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="aecf0-161">按下**播放**第二次停止 [預覽] 模式。</span><span class="sxs-lookup"><span data-stu-id="aecf0-161">Press **Play** a second time to stop preview mode.</span></span>

<span data-ttu-id="aecf0-162">**匯出從 Unity 專案，Visual studio**</span><span class="sxs-lookup"><span data-stu-id="aecf0-162">**Export the project from Unity to Visual Studio**</span></span>
* <span data-ttu-id="aecf0-163">在 Unity 中，選取**檔案 > 組建設定**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-163">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="aecf0-164">按一下 **加入開啟的場景**加入場景。</span><span class="sxs-lookup"><span data-stu-id="aecf0-164">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="aecf0-165">選取 **通用 Windows 平台**中**平台**清單，然後按一下**切換平台**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-165">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="aecf0-166">設定**SDK**要**通用 10**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-166">Set **SDK** to **Universal 10**.</span></span>
* <span data-ttu-id="aecf0-167">設定**目標裝置**要**HoloLens**並**UWP 建置型別**至**D3D**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-167">Set **Target device** to **HoloLens** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="aecf0-168">請檢查**UnityC#專案**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-168">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="aecf0-169">按一下 [建置] 。</span><span class="sxs-lookup"><span data-stu-id="aecf0-169">Click **Build**.</span></span>
* <span data-ttu-id="aecf0-170">在出現的 [檔案總管] 視窗，建立**新的資料夾**名為 「 應用程式 」。</span><span class="sxs-lookup"><span data-stu-id="aecf0-170">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="aecf0-171">只要按一下**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="aecf0-171">Single click the **App** folder.</span></span>
* <span data-ttu-id="aecf0-172">按下**選取資料夾**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-172">Press **Select Folder**.</span></span>
* <span data-ttu-id="aecf0-173">Unity 完成時，會出現檔案總管 視窗。</span><span class="sxs-lookup"><span data-stu-id="aecf0-173">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="aecf0-174">開啟**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="aecf0-174">Open the **App** folder.</span></span>
* <span data-ttu-id="aecf0-175">開啟**SharedHolograms.sln**即可啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="aecf0-175">Open **SharedHolograms.sln** to launch Visual Studio.</span></span>
* <span data-ttu-id="aecf0-176">使用頂端的工具列，在 Visual Studio 中，從 偵錯，若要變更目標**Release**進出至 ARM **X86**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-176">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="aecf0-177">按一下下拉式清單旁的箭號本機電腦，然後選取**遠端裝置**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-177">Click on the drop-down arrow next to Local Machine, and select **Remote Device**.</span></span>
    * <span data-ttu-id="aecf0-178">設定**地址**的名稱或 IP 位址的您 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="aecf0-178">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="aecf0-179">如果您不知道您的裝置 IP 位址，查看**設定 > 網路和網際網路 > 進階選項**詢問 Cortana 或 **「 嘿 Cortana，我的 IP 位址是什麼？ 」**</span><span class="sxs-lookup"><span data-stu-id="aecf0-179">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
    * <span data-ttu-id="aecf0-180">離開**驗證模式**設為**通用**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-180">Leave the **Authentication Mode** set to **Universal**.</span></span>
    * <span data-ttu-id="aecf0-181">按一下 **選取**</span><span class="sxs-lookup"><span data-stu-id="aecf0-181">Click **Select**</span></span>
* <span data-ttu-id="aecf0-182">按一下 **偵錯 > 啟動但不偵錯**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-182">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="aecf0-183">如果這是第一次部署到您的裝置，您必須[與 Visual Studio 中配對](using-visual-studio.md#pairing-your-device-hololens)。</span><span class="sxs-lookup"><span data-stu-id="aecf0-183">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
* <span data-ttu-id="aecf0-184">將放在您的 HoloLens 上，並尋找 EnergyHub 全像圖。</span><span class="sxs-lookup"><span data-stu-id="aecf0-184">Put on your HoloLens and find the EnergyHub hologram.</span></span>

## <a name="chapter-2---interaction"></a><span data-ttu-id="aecf0-185">第 2 章-互動</span><span class="sxs-lookup"><span data-stu-id="aecf0-185">Chapter 2 - Interaction</span></span>

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

<span data-ttu-id="aecf0-186">在本章中，我們將與我們全像投影互動。</span><span class="sxs-lookup"><span data-stu-id="aecf0-186">In this chapter, we'll interact with our holograms.</span></span> <span data-ttu-id="aecf0-187">首先，我們將新增的資料指標，以視覺化方式檢視我們[視線](gaze.md)。</span><span class="sxs-lookup"><span data-stu-id="aecf0-187">First, we'll add a cursor to visualize our [Gaze](gaze.md).</span></span> <span data-ttu-id="aecf0-188">然後，我們將新增[筆勢](gestures.md)和空間中放置我們全像投影中使用我們的游標。</span><span class="sxs-lookup"><span data-stu-id="aecf0-188">Then, we'll add [Gestures](gestures.md) and use our hand to place our holograms in space.</span></span>

### <a name="objectives"></a><span data-ttu-id="aecf0-189">目標</span><span class="sxs-lookup"><span data-stu-id="aecf0-189">Objectives</span></span>

* <span data-ttu-id="aecf0-190">使用視線輸入來控制資料指標。</span><span class="sxs-lookup"><span data-stu-id="aecf0-190">Use gaze input to control a cursor.</span></span>
* <span data-ttu-id="aecf0-191">使用輸入至全像投影與互動的筆勢。</span><span class="sxs-lookup"><span data-stu-id="aecf0-191">Use gesture input to interact with holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="aecf0-192">指示</span><span class="sxs-lookup"><span data-stu-id="aecf0-192">Instructions</span></span>

<span data-ttu-id="aecf0-193">**Gaze**</span><span class="sxs-lookup"><span data-stu-id="aecf0-193">**Gaze**</span></span>
* <span data-ttu-id="aecf0-194">在 **階層面板**選取**HologramCollection**物件。</span><span class="sxs-lookup"><span data-stu-id="aecf0-194">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="aecf0-195">在 [**偵測器] 面板**按一下 [**新增元件**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="aecf0-195">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="aecf0-196">在功能表中，輸入在搜尋方塊**視線 Manager**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-196">In the menu, type in the search box **Gaze Manager**.</span></span> <span data-ttu-id="aecf0-197">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="aecf0-197">Select the search result.</span></span>
* <span data-ttu-id="aecf0-198">在  **HoloToolkit 共用 240\Prefabs\Input**資料夾中，尋找**游標**資產。</span><span class="sxs-lookup"><span data-stu-id="aecf0-198">In the **HoloToolkit-Sharing-240\Prefabs\Input** folder, find the **Cursor** asset.</span></span>
* <span data-ttu-id="aecf0-199">將拖放**游標**拖曳至資產**階層**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-199">Drag and drop the **Cursor** asset onto the **Hierarchy**.</span></span>

<span data-ttu-id="aecf0-200">**筆勢**</span><span class="sxs-lookup"><span data-stu-id="aecf0-200">**Gesture**</span></span>
* <span data-ttu-id="aecf0-201">在 **階層面板**選取**HologramCollection**物件。</span><span class="sxs-lookup"><span data-stu-id="aecf0-201">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="aecf0-202">按一下 [**新增元件**並輸入**筆勢管理員**搜尋] 欄位中。</span><span class="sxs-lookup"><span data-stu-id="aecf0-202">Click **Add Component** and type **Gesture Manager** in the search field.</span></span> <span data-ttu-id="aecf0-203">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="aecf0-203">Select the search result.</span></span>
* <span data-ttu-id="aecf0-204">在 **階層面板**，展開**HologramCollection**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-204">In the **Hierarchy panel**, expand **HologramCollection**.</span></span>
* <span data-ttu-id="aecf0-205">選取子系**EnergyHub**物件。</span><span class="sxs-lookup"><span data-stu-id="aecf0-205">Select the child **EnergyHub** object.</span></span>
* <span data-ttu-id="aecf0-206">在 [**偵測器] 面板**按一下 [**新增元件**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="aecf0-206">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="aecf0-207">在功能表中，輸入在搜尋方塊**全像放置**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-207">In the menu, type in the search box **Hologram Placement**.</span></span> <span data-ttu-id="aecf0-208">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="aecf0-208">Select the search result.</span></span>
* <span data-ttu-id="aecf0-209">選取 來儲存場景**檔案 > 儲存場景**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-209">Save the scene by selecting **File > Save Scene**.</span></span>

<span data-ttu-id="aecf0-210">**部署並享有**</span><span class="sxs-lookup"><span data-stu-id="aecf0-210">**Deploy and enjoy**</span></span>
* <span data-ttu-id="aecf0-211">建置並部署到您的 HoloLens，使用來自上一個章節的指示。</span><span class="sxs-lookup"><span data-stu-id="aecf0-211">Build and deploy to your HoloLens, using the instructions from the previous chapter.</span></span>
* <span data-ttu-id="aecf0-212">一旦您 HoloLens 上啟動應用程式，移動您的標頭，並注意 EnergyHub 如何遵循您的視線。</span><span class="sxs-lookup"><span data-stu-id="aecf0-212">Once the app launches on your HoloLens, move your head around and notice how the EnergyHub follows your gaze.</span></span>
* <span data-ttu-id="aecf0-213">請注意如何資料指標時您視線闀，時，會出現，而且如果不在全像 gazing 會變更為點光線。</span><span class="sxs-lookup"><span data-stu-id="aecf0-213">Notice how the cursor appears when you gaze upon the hologram, and changes to a point light when not gazing at a hologram.</span></span>
* <span data-ttu-id="aecf0-214">執行將全像空中點選。</span><span class="sxs-lookup"><span data-stu-id="aecf0-214">Perform an air-tap to place the hologram.</span></span> <span data-ttu-id="aecf0-215">在我們的專案中，此時您可以只將全像一次 （重新部署到再試一次）。</span><span class="sxs-lookup"><span data-stu-id="aecf0-215">At this time in our project, you can only place the hologram once (redeploy to try again).</span></span>

## <a name="chapter-3---shared-coordinates"></a><span data-ttu-id="aecf0-216">第 3 章-共用座標</span><span class="sxs-lookup"><span data-stu-id="aecf0-216">Chapter 3 - Shared Coordinates</span></span>

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

<span data-ttu-id="aecf0-217">這是查看並與其互動全像投影，更有趣，但讓我們進一步。</span><span class="sxs-lookup"><span data-stu-id="aecf0-217">It's fun to see and interact with holograms, but let's go further.</span></span> <span data-ttu-id="aecf0-218">我們會設定我們第一個共用體驗-雷射，每個人都可以看到在一起。</span><span class="sxs-lookup"><span data-stu-id="aecf0-218">We'll set up our first shared experience - a hologram everyone can see together.</span></span>

### <a name="objectives"></a><span data-ttu-id="aecf0-219">目標</span><span class="sxs-lookup"><span data-stu-id="aecf0-219">Objectives</span></span>

* <span data-ttu-id="aecf0-220">設定網路，以分享經驗。</span><span class="sxs-lookup"><span data-stu-id="aecf0-220">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="aecf0-221">建立一般的參考點。</span><span class="sxs-lookup"><span data-stu-id="aecf0-221">Establish a common reference point.</span></span>
* <span data-ttu-id="aecf0-222">跨裝置共用座標系統。</span><span class="sxs-lookup"><span data-stu-id="aecf0-222">Share coordinate systems across devices.</span></span>
* <span data-ttu-id="aecf0-223">每個人看到相同的全像 ！</span><span class="sxs-lookup"><span data-stu-id="aecf0-223">Everyone sees the same hologram!</span></span>

>[!NOTE]
><span data-ttu-id="aecf0-224">**InternetClientServer**並**PrivateNetworkClientServer**必須連接到共用的伺服器應用程式的宣告功能。</span><span class="sxs-lookup"><span data-stu-id="aecf0-224">The **InternetClientServer** and **PrivateNetworkClientServer** capabilities must be declared for an app to connect to the sharing server.</span></span> <span data-ttu-id="aecf0-225">這是針對您已在全像投影 240 但謹記在心，為您自己的專案。</span><span class="sxs-lookup"><span data-stu-id="aecf0-225">This is done for you already in Holograms 240, but keep this in mind for your own projects.</span></span>
>1. <span data-ttu-id="aecf0-226">瀏覽至 「 編輯 > 專案設定 > 播放程式 」 在 Unity 編輯器中，請移至播放程式設定</span><span class="sxs-lookup"><span data-stu-id="aecf0-226">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="aecf0-227">按一下 [Windows Store] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="aecf0-227">Click on the "Windows Store" tab</span></span>
>3. <span data-ttu-id="aecf0-228">在 「 發行的設定 > 功能 」 區段中，檢查**InternetClientServer**功能並**PrivateNetworkClientServer**功能</span><span class="sxs-lookup"><span data-stu-id="aecf0-228">In the "Publishing Settings > Capabilities" section, check the **InternetClientServer** capability and the **PrivateNetworkClientServer** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="aecf0-229">指示</span><span class="sxs-lookup"><span data-stu-id="aecf0-229">Instructions</span></span>

* <span data-ttu-id="aecf0-230">在  **專案 面板**瀏覽至**HoloToolkit 共用 240\Prefabs\Sharing**資料夾。</span><span class="sxs-lookup"><span data-stu-id="aecf0-230">In the **Project panel** navigate to the **HoloToolkit-Sharing-240\Prefabs\Sharing** folder.</span></span>
* <span data-ttu-id="aecf0-231">將拖放**Sharing**至 prefab**階層面板**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-231">Drag and drop the **Sharing** prefab into the **Hierarchy panel**.</span></span>

<span data-ttu-id="aecf0-232">接下來，我們需要啟動共用服務。</span><span class="sxs-lookup"><span data-stu-id="aecf0-232">Next we need to launch the sharing service.</span></span> <span data-ttu-id="aecf0-233">只有**一部電腦**是共用體驗需要執行此步驟。</span><span class="sxs-lookup"><span data-stu-id="aecf0-233">Only **one PC** in the shared experience needs to do this step.</span></span>
* <span data-ttu-id="aecf0-234">在 Unity-中最上方現有的功能表中，選取**HoloToolkit 共用 240 功能表**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-234">In Unity - in the top-hand menu - select the **HoloToolkit-Sharing-240 menu**.</span></span>
* <span data-ttu-id="aecf0-235">選取 **啟動共用服務**下拉式清單中的項目。</span><span class="sxs-lookup"><span data-stu-id="aecf0-235">Select the **Launch Sharing Service** item in the drop-down.</span></span>
* <span data-ttu-id="aecf0-236">請檢查**私用網路**選項，然後按一下**允許存取**防火牆提示出現時。</span><span class="sxs-lookup"><span data-stu-id="aecf0-236">Check the **Private Network** option and click **Allow Access** when the firewall prompt appears.</span></span>
* <span data-ttu-id="aecf0-237">請記下的共用服務主控台視窗中顯示的 IPv4 位址。</span><span class="sxs-lookup"><span data-stu-id="aecf0-237">Note down the IPv4 address displayed in the Sharing Service console window.</span></span> <span data-ttu-id="aecf0-238">這是與機器服務執行相同的 IP。</span><span class="sxs-lookup"><span data-stu-id="aecf0-238">This is the same IP as the machine the service is being run on.</span></span>

<span data-ttu-id="aecf0-239">依照其餘指示**所有電腦**，將會加入分享的經驗。</span><span class="sxs-lookup"><span data-stu-id="aecf0-239">Follow the rest of the instructions on **all PCs** that will join the shared experience.</span></span>
* <span data-ttu-id="aecf0-240">在 **階層**，選取**共用**物件。</span><span class="sxs-lookup"><span data-stu-id="aecf0-240">In the **Hierarchy**, select the **Sharing** object.</span></span>
* <span data-ttu-id="aecf0-241">在**Inspector**上**共用階段**元件，變更**伺服器位址**從 'localhost' 為執行 SharingService.exe 之電腦的 IPv4 位址。</span><span class="sxs-lookup"><span data-stu-id="aecf0-241">In the **Inspector**, on the **Sharing Stage** component, change the **Server Address** from 'localhost' to the IPv4 address of the machine running SharingService.exe.</span></span>
* <span data-ttu-id="aecf0-242">在 **階層**選取**HologramCollection**物件。</span><span class="sxs-lookup"><span data-stu-id="aecf0-242">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="aecf0-243">在  **Inspector**按一下 **新增元件** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="aecf0-243">In the **Inspector** click the **Add Component** button.</span></span>
* <span data-ttu-id="aecf0-244">在 [搜尋] 方塊中，輸入**匯入匯出的錨點 Manager**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-244">In the search box, type **Import Export Anchor Manager**.</span></span> <span data-ttu-id="aecf0-245">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="aecf0-245">Select the search result.</span></span>
* <span data-ttu-id="aecf0-246">在  **專案 面板**瀏覽至**指令碼**資料夾。</span><span class="sxs-lookup"><span data-stu-id="aecf0-246">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="aecf0-247">按兩下**HologramPlacement**指令碼，以在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="aecf0-247">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="aecf0-248">下列程式碼取代內容。</span><span class="sxs-lookup"><span data-stu-id="aecf0-248">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="aecf0-249">傳回在 Unity 中，選取**HologramCollection**中**階層面板**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-249">Back in Unity, select the **HologramCollection** in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="aecf0-250">在 [**偵測器] 面板**按一下 [**新增元件**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="aecf0-250">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="aecf0-251">在功能表中，輸入在搜尋方塊**應用程式的狀態管理員**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-251">In the menu, type in the search box **App State Manager**.</span></span> <span data-ttu-id="aecf0-252">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="aecf0-252">Select the search result.</span></span>

<span data-ttu-id="aecf0-253">**部署並享有**</span><span class="sxs-lookup"><span data-stu-id="aecf0-253">**Deploy and enjoy**</span></span>
* <span data-ttu-id="aecf0-254">建置您的 HoloLens 裝置專案。</span><span class="sxs-lookup"><span data-stu-id="aecf0-254">Build the project for your HoloLens devices.</span></span>
* <span data-ttu-id="aecf0-255">將指定為第一個部署一個 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="aecf0-255">Designate one HoloLens to deploy to first.</span></span> <span data-ttu-id="aecf0-256">您必須等待才能下 EnergyHub 上傳至服務的錨點 (這可能需要 30-60 秒)。</span><span class="sxs-lookup"><span data-stu-id="aecf0-256">You will need to wait for the Anchor to be uploaded to the service before you can place the EnergyHub (this can take ~30-60 seconds).</span></span> <span data-ttu-id="aecf0-257">上傳完成後，直到您點選手勢都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="aecf0-257">Until the upload is done, your tap gestures will be ignored.</span></span>
* <span data-ttu-id="aecf0-258">已置放 EnergyHub 之後，它的位置將會上傳至服務，並接著便可部署到所有其他的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="aecf0-258">After the EnergyHub has been placed, its location will be uploaded to the service and you can then deploy to all other HoloLens devices.</span></span>
* <span data-ttu-id="aecf0-259">當新的 HoloLens 第一次加入工作階段時，可能不在該裝置上正確 EnergyHub 的位置。</span><span class="sxs-lookup"><span data-stu-id="aecf0-259">When a new HoloLens first joins the session, the location of the EnergyHub may not be correct on that device.</span></span> <span data-ttu-id="aecf0-260">不過，已從服務下載的錨點和 EnergyHub 位置，如 EnergyHub 應該移至新的共用位置。</span><span class="sxs-lookup"><span data-stu-id="aecf0-260">However, as soon as the anchor and EnergyHub locations have been downloaded from the service, the EnergyHub should jump to the new, shared location.</span></span> <span data-ttu-id="aecf0-261">如果這不會在 30 至 60 秒，逐步引導到原始的 HoloLens 的設定來收集多個環境線索的錨點時。</span><span class="sxs-lookup"><span data-stu-id="aecf0-261">If this does not happen within ~30-60 seconds, walk to where the original HoloLens was when setting the anchor to gather more environment clues.</span></span> <span data-ttu-id="aecf0-262">如果位置仍不會鎖定，重新部署至裝置。</span><span class="sxs-lookup"><span data-stu-id="aecf0-262">If the location still does not lock on, redeploy to the device.</span></span>
* <span data-ttu-id="aecf0-263">當裝置時，隨時，並執行應用程式，尋找 EnergyHub。</span><span class="sxs-lookup"><span data-stu-id="aecf0-263">When the devices are all ready and running the app, look for the EnergyHub.</span></span> <span data-ttu-id="aecf0-264">大家都同意在全像的位置可以和文字面向的方向？</span><span class="sxs-lookup"><span data-stu-id="aecf0-264">Can you all agree on the hologram's location and which direction the text is facing?</span></span>

## <a name="chapter-4---discovery"></a><span data-ttu-id="aecf0-265">第 4 章-探索</span><span class="sxs-lookup"><span data-stu-id="aecf0-265">Chapter 4 - Discovery</span></span>

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

<span data-ttu-id="aecf0-266">現在，每個人都可以看到相同的全像 ！</span><span class="sxs-lookup"><span data-stu-id="aecf0-266">Everyone can now see the same hologram!</span></span> <span data-ttu-id="aecf0-267">現在我們來看看其他連線至共用全像攝影版世界的每個人。</span><span class="sxs-lookup"><span data-stu-id="aecf0-267">Now let's see everyone else connected to our shared holographic world.</span></span> <span data-ttu-id="aecf0-268">在本章中，我們就會把相同的共用工作階段中的所有其他的 HoloLens 裝置旋轉與前端的位置。</span><span class="sxs-lookup"><span data-stu-id="aecf0-268">In this chapter, we'll grab the head location and rotation of all other HoloLens devices in the same sharing session.</span></span>

### <a name="objectives"></a><span data-ttu-id="aecf0-269">目標</span><span class="sxs-lookup"><span data-stu-id="aecf0-269">Objectives</span></span>

* <span data-ttu-id="aecf0-270">在我們的共用經驗來發現彼此。</span><span class="sxs-lookup"><span data-stu-id="aecf0-270">Discover each other in our shared experience.</span></span>
* <span data-ttu-id="aecf0-271">選擇，以及共用播放程式顯示圖片。</span><span class="sxs-lookup"><span data-stu-id="aecf0-271">Choose and share a player avatar.</span></span>
* <span data-ttu-id="aecf0-272">將播放程式顯示圖片，每個人的標頭旁邊的連結。</span><span class="sxs-lookup"><span data-stu-id="aecf0-272">Attach the player avatar next to everyone's heads.</span></span>

### <a name="instructions"></a><span data-ttu-id="aecf0-273">指示</span><span class="sxs-lookup"><span data-stu-id="aecf0-273">Instructions</span></span>

* <span data-ttu-id="aecf0-274">在  **專案 面板**瀏覽至**全像投影**資料夾。</span><span class="sxs-lookup"><span data-stu-id="aecf0-274">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="aecf0-275">將拖放**PlayerAvatarStore**成**階層**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-275">Drag and drop the **PlayerAvatarStore** into the **Hierarchy**.</span></span>
* <span data-ttu-id="aecf0-276">在  **專案 面板**瀏覽至**指令碼**資料夾。</span><span class="sxs-lookup"><span data-stu-id="aecf0-276">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="aecf0-277">按兩下**AvatarSelector**指令碼，以在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="aecf0-277">Double-click the **AvatarSelector** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="aecf0-278">下列程式碼取代內容。</span><span class="sxs-lookup"><span data-stu-id="aecf0-278">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="aecf0-279">在 **階層**選取**HologramCollection**物件。</span><span class="sxs-lookup"><span data-stu-id="aecf0-279">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="aecf0-280">在  **Inspector**按一下 **新增元件**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-280">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="aecf0-281">在 [搜尋] 方塊中，輸入**本機播放程式管理員**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-281">In the search box, type **Local Player Manager**.</span></span> <span data-ttu-id="aecf0-282">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="aecf0-282">Select the search result.</span></span>
* <span data-ttu-id="aecf0-283">在 **階層**選取**HologramCollection**物件。</span><span class="sxs-lookup"><span data-stu-id="aecf0-283">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="aecf0-284">在  **Inspector**按一下 **新增元件**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-284">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="aecf0-285">在 [搜尋] 方塊中，輸入**遠端播放程式管理員**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-285">In the search box, type **Remote Player Manager**.</span></span> <span data-ttu-id="aecf0-286">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="aecf0-286">Select the search result.</span></span>
* <span data-ttu-id="aecf0-287">開啟**HologramPlacement** Visual Studio 中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="aecf0-287">Open the **HologramPlacement** script in Visual Studio.</span></span>
* <span data-ttu-id="aecf0-288">下列程式碼取代內容。</span><span class="sxs-lookup"><span data-stu-id="aecf0-288">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="aecf0-289">開啟**AppStateManager** Visual Studio 中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="aecf0-289">Open the **AppStateManager** script in Visual Studio.</span></span>
* <span data-ttu-id="aecf0-290">下列程式碼取代內容。</span><span class="sxs-lookup"><span data-stu-id="aecf0-290">Replace the contents with the code below.</span></span>

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

<span data-ttu-id="aecf0-291">**部署並享有**</span><span class="sxs-lookup"><span data-stu-id="aecf0-291">**Deploy and Enjoy**</span></span>
* <span data-ttu-id="aecf0-292">建置，並將專案部署到您的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="aecf0-292">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="aecf0-293">當您聽到聲音，ping、 虛擬人偶選取功能表中找到並選取 顯示圖片使用空中點選手勢。</span><span class="sxs-lookup"><span data-stu-id="aecf0-293">When you hear a pinging sound, find the avatar selection menu and select an avatar with the air-tap gesture.</span></span>
* <span data-ttu-id="aecf0-294">如果您不想透過任何全像投影，游標周圍輕點將會開啟不同的色彩時您 HoloLens 正在與服務通訊： 初始化 （深紫色）、 下載錨點 （綠色），匯入/匯出位置資料 （黃色），正在上傳 （藍色） 的錨點。</span><span class="sxs-lookup"><span data-stu-id="aecf0-294">If you're not looking at any holograms, the point light around your cursor will turn a different color when your HoloLens is communicating with the service: initializing (dark purple), downloading the anchor (green), importing/exporting location data (yellow), uploading the anchor (blue).</span></span> <span data-ttu-id="aecf0-295">如果游標周圍輕點的預設色彩 （淺紫），接著您就可以與其他玩家互動工作階段中 ！</span><span class="sxs-lookup"><span data-stu-id="aecf0-295">If your point light around your cursor is the default color (light purple), then you are ready to interact with other players in your session!</span></span>
* <span data-ttu-id="aecf0-296">看看其他人連線到您的空間-將會有全像攝影版的機器人浮動高於其 shoulder 和模擬其前端動作 ！</span><span class="sxs-lookup"><span data-stu-id="aecf0-296">Look at other people connected to your space - there will be a holographic robot floating above their shoulder and mimicking their head motions!</span></span>

## <a name="chapter-5---placement"></a><span data-ttu-id="aecf0-297">第 5 章-位置</span><span class="sxs-lookup"><span data-stu-id="aecf0-297">Chapter 5 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

<span data-ttu-id="aecf0-298">在本章中，我們要能夠放在真實世界的表面上的錨點。</span><span class="sxs-lookup"><span data-stu-id="aecf0-298">In this chapter, we'll make the anchor able to be placed on real-world surfaces.</span></span> <span data-ttu-id="aecf0-299">將會錨定在中間點之間每個人都連接到分享經驗中，我們將使用共用的座標。</span><span class="sxs-lookup"><span data-stu-id="aecf0-299">We'll use shared coordinates to place that anchor in the middle point between everyone connected to the shared experience.</span></span>

### <a name="objectives"></a><span data-ttu-id="aecf0-300">目標</span><span class="sxs-lookup"><span data-stu-id="aecf0-300">Objectives</span></span>

* <span data-ttu-id="aecf0-301">全像投影置於空間的對應，根據玩家的前端的位置。</span><span class="sxs-lookup"><span data-stu-id="aecf0-301">Place holograms on the spatial map based on players’ head position.</span></span>

### <a name="instructions"></a><span data-ttu-id="aecf0-302">指示</span><span class="sxs-lookup"><span data-stu-id="aecf0-302">Instructions</span></span>

* <span data-ttu-id="aecf0-303">在  **專案 面板**瀏覽至**全像投影**資料夾。</span><span class="sxs-lookup"><span data-stu-id="aecf0-303">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="aecf0-304">將拖放**CustomSpatialMapping**拖曳至 prefab**階層**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-304">Drag and drop the **CustomSpatialMapping** prefab onto the **Hierarchy**.</span></span>
* <span data-ttu-id="aecf0-305">在  **專案 面板**瀏覽至**指令碼**資料夾。</span><span class="sxs-lookup"><span data-stu-id="aecf0-305">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="aecf0-306">按兩下**AppStateManager**指令碼，以在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="aecf0-306">Double-click the **AppStateManager** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="aecf0-307">下列程式碼取代內容。</span><span class="sxs-lookup"><span data-stu-id="aecf0-307">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="aecf0-308">在  **專案 面板**瀏覽至**指令碼**資料夾。</span><span class="sxs-lookup"><span data-stu-id="aecf0-308">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="aecf0-309">按兩下**HologramPlacement**指令碼，以在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="aecf0-309">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="aecf0-310">下列程式碼取代內容。</span><span class="sxs-lookup"><span data-stu-id="aecf0-310">Replace the contents with the code below.</span></span>

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

<span data-ttu-id="aecf0-311">**部署並享有**</span><span class="sxs-lookup"><span data-stu-id="aecf0-311">**Deploy and enjoy**</span></span>
* <span data-ttu-id="aecf0-312">建置，並將專案部署到您的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="aecf0-312">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="aecf0-313">應用程式準備就緒時，就能在圓形中，並注意 EnergyHub 中央的每個人的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="aecf0-313">When the app is ready, stand in a circle and notice how the EnergyHub appears in the center of everyone.</span></span>
* <span data-ttu-id="aecf0-314">點選要放置 EnergyHub。</span><span class="sxs-lookup"><span data-stu-id="aecf0-314">Tap to place the EnergyHub.</span></span>
* <span data-ttu-id="aecf0-315">嘗試移動到新位置的全像語音命令回挑選 EnergyHub 並合作，為群組的 [重設目標]。</span><span class="sxs-lookup"><span data-stu-id="aecf0-315">Try the voice command 'Reset Target' to pick the EnergyHub back up and work together as a group to move the hologram to a new location.</span></span>

## <a name="chapter-6---real-world-physics"></a><span data-ttu-id="aecf0-316">第 6 章-實境物理</span><span class="sxs-lookup"><span data-stu-id="aecf0-316">Chapter 6 - Real-World Physics</span></span>

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

<span data-ttu-id="aecf0-317">在本章中，我們將新增全像投影，彈開真實世界的介面。</span><span class="sxs-lookup"><span data-stu-id="aecf0-317">In this chapter we'll add holograms that bounce off real-world surfaces.</span></span> <span data-ttu-id="aecf0-318">觀看您啟動由您和您的朋友的專案會填滿的空間 ！</span><span class="sxs-lookup"><span data-stu-id="aecf0-318">Watch your space fill up with projects launched by both you and your friends!</span></span>

### <a name="objectives"></a><span data-ttu-id="aecf0-319">目標</span><span class="sxs-lookup"><span data-stu-id="aecf0-319">Objectives</span></span>

* <span data-ttu-id="aecf0-320">啟動投擲彈開真實世界的介面。</span><span class="sxs-lookup"><span data-stu-id="aecf0-320">Launch projectiles that bounce off real-world surfaces.</span></span>
* <span data-ttu-id="aecf0-321">共用投擲，讓其他玩家可以看到它們。</span><span class="sxs-lookup"><span data-stu-id="aecf0-321">Share the projectiles so other players can see them.</span></span>

### <a name="instructions"></a><span data-ttu-id="aecf0-322">指示</span><span class="sxs-lookup"><span data-stu-id="aecf0-322">Instructions</span></span>

* <span data-ttu-id="aecf0-323">在 **階層**選取**HologramCollection**物件。</span><span class="sxs-lookup"><span data-stu-id="aecf0-323">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="aecf0-324">在  **Inspector**按一下 **新增元件**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-324">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="aecf0-325">在 [搜尋] 方塊中，輸入**彈藥啟動器**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-325">In the search box, type **Projectile Launcher**.</span></span> <span data-ttu-id="aecf0-326">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="aecf0-326">Select the search result.</span></span>

<span data-ttu-id="aecf0-327">**部署並享有**</span><span class="sxs-lookup"><span data-stu-id="aecf0-327">**Deploy and enjoy**</span></span>
* <span data-ttu-id="aecf0-328">建置並部署到您的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="aecf0-328">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="aecf0-329">當所有裝置上執行應用程式時，執行以啟動在真實世界表面的彈藥空中點選。</span><span class="sxs-lookup"><span data-stu-id="aecf0-329">When the app is running on all devices, perform an air-tap to launch projectile at real world surfaces.</span></span>
* <span data-ttu-id="aecf0-330">請參閱您的彈藥衝突與其他播放器的顯示圖片時，會發生什麼事 ！</span><span class="sxs-lookup"><span data-stu-id="aecf0-330">See what happens when your projectile collides with another player's avatar!</span></span>

## <a name="chapter-7---grand-finale"></a><span data-ttu-id="aecf0-331">第 7 章-總計二</span><span class="sxs-lookup"><span data-stu-id="aecf0-331">Chapter 7 - Grand Finale</span></span>

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

<span data-ttu-id="aecf0-332">在本章中，我們會找出只與共同作業探索到的入口網站。</span><span class="sxs-lookup"><span data-stu-id="aecf0-332">In this chapter, we'll uncover a portal that can only be discovered with collaboration.</span></span>

### <a name="objectives"></a><span data-ttu-id="aecf0-333">目標</span><span class="sxs-lookup"><span data-stu-id="aecf0-333">Objectives</span></span>

* <span data-ttu-id="aecf0-334">若要啟動的錨點，以發掘出有用祕密的入口網站在足夠投擲一起運作 ！</span><span class="sxs-lookup"><span data-stu-id="aecf0-334">Work together to launch enough projectiles at the anchor to uncover a secret portal!</span></span>

### <a name="instructions"></a><span data-ttu-id="aecf0-335">指示</span><span class="sxs-lookup"><span data-stu-id="aecf0-335">Instructions</span></span>

* <span data-ttu-id="aecf0-336">在  **專案 面板**瀏覽至**全像投影**資料夾。</span><span class="sxs-lookup"><span data-stu-id="aecf0-336">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="aecf0-337">將拖放**底世界**資產做**HologramCollection 的子系**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-337">Drag and drop the **Underworld** asset as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="aecf0-338">具有**HologramCollection**選取，按一下**新增元件**按鈕**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-338">With **HologramCollection** selected, click the **Add Component** button in the **Inspector**.</span></span>
* <span data-ttu-id="aecf0-339">在功能表中，輸入在搜尋方塊**ExplodeTarget**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-339">In the menu, type in the search box **ExplodeTarget**.</span></span> <span data-ttu-id="aecf0-340">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="aecf0-340">Select the search result.</span></span>
* <span data-ttu-id="aecf0-341">具有**HologramCollection**已選取，從**階層**拖曳**EnergyHub**物件**目標**欄位**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-341">With **HologramCollection** selected, from the **Hierarchy** drag the **EnergyHub** object to the **Target** field in the **Inspector**.</span></span>
* <span data-ttu-id="aecf0-342">與**HologramCollection**已選取，從**階層**拖曳**底世界**物件**底世界**欄位**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="aecf0-342">With **HologramCollection** selected, from the **Hierarchy** drag the **Underworld** object to the **Underworld** field in the **Inspector**.</span></span>

<span data-ttu-id="aecf0-343">**部署並享有**</span><span class="sxs-lookup"><span data-stu-id="aecf0-343">**Deploy and enjoy**</span></span>
* <span data-ttu-id="aecf0-344">建置並部署到您的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="aecf0-344">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="aecf0-345">當應用程式已啟動時，一起共同作業以啟動在 EnergyHub 投擲。</span><span class="sxs-lookup"><span data-stu-id="aecf0-345">When the app has launched, collaborate together to launch projectiles at the EnergyHub.</span></span>
* <span data-ttu-id="aecf0-346">底世界出現時，請啟動砲彈在底世界機器人 （按三次，額外的有趣的機器人）。</span><span class="sxs-lookup"><span data-stu-id="aecf0-346">When the underworld appears, launch projectiles at underworld robots (hit a robot three times for extra fun).</span></span>
