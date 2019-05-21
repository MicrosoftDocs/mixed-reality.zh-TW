---
title: MR 空間 220-空間的音效
description: 請遵循此程式碼撰寫的逐步解說，若要了解空間音效概念的詳細資料，使用 Unity、 Visual Studio 和 HoloLens。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit mixedrealitytoolkit、 mixedrealitytoolkit unity、 academy、 教學課程中，空間的音效
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591421"
---
>[!NOTE]
><span data-ttu-id="c21d0-104">混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。</span><span class="sxs-lookup"><span data-stu-id="c21d0-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="c21d0-105">因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。</span><span class="sxs-lookup"><span data-stu-id="c21d0-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="c21d0-106">這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="c21d0-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="c21d0-107">它們會繼續運作，支援的裝置上維護。</span><span class="sxs-lookup"><span data-stu-id="c21d0-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="c21d0-108">會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="c21d0-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="c21d0-109">當他們回傳時，本聲明將會更新這些教學課程的連結。</span><span class="sxs-lookup"><span data-stu-id="c21d0-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="c21d0-110">MR 空間 220:空間音效</span><span class="sxs-lookup"><span data-stu-id="c21d0-110">MR Spatial 220: Spatial sound</span></span>

<span data-ttu-id="c21d0-111">[空間音效](spatial-sound.md)活著到全像投影的生命週期，並提供我們的世界中的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="c21d0-111">[Spatial sound](spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="c21d0-112">全像投影組成光線和音效，萬一您無法看見您全像投影，空間音效可協助您找出它們。</span><span class="sxs-lookup"><span data-stu-id="c21d0-112">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="c21d0-113">空間音效不類似的典型的音效，您會聽到電台上，並放置在 3D 空間中的音效。</span><span class="sxs-lookup"><span data-stu-id="c21d0-113">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="c21d0-114">使用空間的音效，您可以進行全像投影音效起來像是背後旁，或甚至在您 ！</span><span class="sxs-lookup"><span data-stu-id="c21d0-114">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="c21d0-115">在本課程中，您將：</span><span class="sxs-lookup"><span data-stu-id="c21d0-115">In this course, you will:</span></span>

* <span data-ttu-id="c21d0-116">設定您的開發環境，以使用 Microsoft 空間音效。</span><span class="sxs-lookup"><span data-stu-id="c21d0-116">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="c21d0-117">使用空間的音效增強互動。</span><span class="sxs-lookup"><span data-stu-id="c21d0-117">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="c21d0-118">搭配空間對應中使用空間的音效。</span><span class="sxs-lookup"><span data-stu-id="c21d0-118">Use Spatial Sound in conjunction with Spatial Mapping.</span></span>
* <span data-ttu-id="c21d0-119">了解完善的設計，以及混用最佳作法。</span><span class="sxs-lookup"><span data-stu-id="c21d0-119">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="c21d0-120">您可以使用音效來增強特殊效果，並將使用者引導至混合實境世界。</span><span class="sxs-lookup"><span data-stu-id="c21d0-120">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="c21d0-121">裝置支援</span><span class="sxs-lookup"><span data-stu-id="c21d0-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c21d0-122">課程</span><span class="sxs-lookup"><span data-stu-id="c21d0-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="c21d0-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c21d0-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c21d0-124"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="c21d0-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="c21d0-125">MR 空間 220:空間音效</span><span class="sxs-lookup"><span data-stu-id="c21d0-125">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="c21d0-126">✔️</span><span class="sxs-lookup"><span data-stu-id="c21d0-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="c21d0-127">✔️</span><span class="sxs-lookup"><span data-stu-id="c21d0-127">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="c21d0-128">開始之前</span><span class="sxs-lookup"><span data-stu-id="c21d0-128">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="c21d0-129">先決條件</span><span class="sxs-lookup"><span data-stu-id="c21d0-129">Prerequisites</span></span>

* <span data-ttu-id="c21d0-130">Windows 10 電腦的正確設定[安裝工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="c21d0-130">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="c21d0-131">基本C#程式設計的能力。</span><span class="sxs-lookup"><span data-stu-id="c21d0-131">Some basic C# programming ability.</span></span>
* <span data-ttu-id="c21d0-132">您應已完成[MR 基本概念 101](holograms-101.md)。</span><span class="sxs-lookup"><span data-stu-id="c21d0-132">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="c21d0-133">HoloLens 裝置[開發設定的](using-visual-studio.md#enabling-developer-mode)。</span><span class="sxs-lookup"><span data-stu-id="c21d0-133">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="c21d0-134">專案檔</span><span class="sxs-lookup"><span data-stu-id="c21d0-134">Project files</span></span>

* <span data-ttu-id="c21d0-135">下載[檔案](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip)專案所需。</span><span class="sxs-lookup"><span data-stu-id="c21d0-135">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span><span data-ttu-id="c21d0-136"> 需要 Unity 2017.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="c21d0-136"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="c21d0-137">如果您仍然需要 Unity 5.6 的支援，請使用[本版](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip)。</span><span class="sxs-lookup"><span data-stu-id="c21d0-137">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="c21d0-138">這一版可能不再是最新狀態。</span><span class="sxs-lookup"><span data-stu-id="c21d0-138">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="c21d0-139">如果您仍然需要 Unity 5.5 的支援，請使用[本版](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip)。</span><span class="sxs-lookup"><span data-stu-id="c21d0-139">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span><span data-ttu-id="c21d0-140"> 這一版可能不再是最新狀態。</span><span class="sxs-lookup"><span data-stu-id="c21d0-140"> This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="c21d0-141">如果您仍然需要 Unity 5.4 的支援，請使用[本版](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip)。</span><span class="sxs-lookup"><span data-stu-id="c21d0-141">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span><span data-ttu-id="c21d0-142"> 這一版可能不再是最新狀態。</span><span class="sxs-lookup"><span data-stu-id="c21d0-142"> This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="c21d0-143">取消封存您的桌面或其他您輕鬆地連線到位置的檔案。</span><span class="sxs-lookup"><span data-stu-id="c21d0-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="c21d0-144">如果您想要查看原始程式碼，在下載之前，它有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound)。</span><span class="sxs-lookup"><span data-stu-id="c21d0-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="c21d0-145">偵錯 errata 和附註</span><span class="sxs-lookup"><span data-stu-id="c21d0-145">Errata and Notes</span></span>

* <span data-ttu-id="c21d0-146">若要停用 啟用 Just My Code 的需求 (*未核取*) 在 Visual Studio 的 工具-> 選項-> 偵錯以程式碼中設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="c21d0-146">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="c21d0-147">第 1 章-Unity 安裝</span><span class="sxs-lookup"><span data-stu-id="c21d0-147">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="c21d0-148">目標</span><span class="sxs-lookup"><span data-stu-id="c21d0-148">Objectives</span></span>

* <span data-ttu-id="c21d0-149">Unity 的音效將組態變更為使用 Microsoft 空間音效。</span><span class="sxs-lookup"><span data-stu-id="c21d0-149">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="c21d0-150">在 Unity 中的物件加入 3D 的聲音。</span><span class="sxs-lookup"><span data-stu-id="c21d0-150">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="c21d0-151">指示</span><span class="sxs-lookup"><span data-stu-id="c21d0-151">Instructions</span></span>

* <span data-ttu-id="c21d0-152">啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="c21d0-152">Start Unity.</span></span>
* <span data-ttu-id="c21d0-153">選取 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-153">Select **Open**.</span></span>
* <span data-ttu-id="c21d0-154">瀏覽至您的桌面及尋找資料夾您先前未封存。</span><span class="sxs-lookup"><span data-stu-id="c21d0-154">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="c21d0-155">按一下 [ **Starting\Decibel**資料夾，然後按下**選取資料夾**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c21d0-155">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="c21d0-156">等待在 Unity 中載入專案。</span><span class="sxs-lookup"><span data-stu-id="c21d0-156">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="c21d0-157">在 [ **專案**] 面板中，開啟**Scenes\Decibel.unity**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-157">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="c21d0-158">在 [**階層**] 面板中，展開**HologramCollection** ，然後選取**P0LY**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-158">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="c21d0-159">在偵測器中，依序展開**AudioSource** ，請注意，沒有任何**Spatialize**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c21d0-159">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="c21d0-160">根據預設，Unity 不會載入空間外掛程式。</span><span class="sxs-lookup"><span data-stu-id="c21d0-160">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="c21d0-161">下列步驟會在專案中啟用空間音效。</span><span class="sxs-lookup"><span data-stu-id="c21d0-161">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="c21d0-162">在 Unity 的上方功能表中，移至**編輯 > 專案設定 > 音訊**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-162">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="c21d0-163">尋找**空間外掛程式**下拉式清單中，然後選取**MS HRTF 空間**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-163">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="c21d0-164">在 **階層**面板中，選取**HologramCollection > P0LY**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-164">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="c21d0-165">在 [ **Inspector** ] 面板中，尋找**音訊來源**元件。</span><span class="sxs-lookup"><span data-stu-id="c21d0-165">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="c21d0-166">請檢查**Spatialize**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c21d0-166">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="c21d0-167">拖曳**空間 Blend**滑桿，一直到**3D**，或輸入**1**編輯方塊中。</span><span class="sxs-lookup"><span data-stu-id="c21d0-167">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="c21d0-168">現在，我們將建置 unity 專案，並設定 Visual Studio 中的解決方案。</span><span class="sxs-lookup"><span data-stu-id="c21d0-168">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="c21d0-169">在 Unity 中，選取**檔案 > 組建設定**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-169">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="c21d0-170">按一下 **加入開啟的場景**加入場景。</span><span class="sxs-lookup"><span data-stu-id="c21d0-170">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="c21d0-171">選取 **通用 Windows 平台**中**平台**清單，然後按一下**切換平台**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-171">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="c21d0-172">如果您要特別開發的 HoloLens，設定**目標裝置**要**HoloLens**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-172">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="c21d0-173">否則，將它保留在**任何裝置**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-173">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="c21d0-174">確保**建置型別**設為**D3D**並**SDK**設定為**最新安裝**（這應該可以 16299 或更新版本的 SDK）。</span><span class="sxs-lookup"><span data-stu-id="c21d0-174">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="c21d0-175">按一下 [建置] 。</span><span class="sxs-lookup"><span data-stu-id="c21d0-175">Click **Build**.</span></span>
7. <span data-ttu-id="c21d0-176">建立**新的資料夾**名為 「 應用程式 」。</span><span class="sxs-lookup"><span data-stu-id="c21d0-176">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="c21d0-177">只要按一下**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="c21d0-177">Single click the **App** folder.</span></span>
9. <span data-ttu-id="c21d0-178">按下**選取資料夾**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-178">Press **Select Folder**.</span></span>

<span data-ttu-id="c21d0-179">Unity 完成時，會出現檔案總管 視窗。</span><span class="sxs-lookup"><span data-stu-id="c21d0-179">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="c21d0-180">開啟**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="c21d0-180">Open the **App** folder.</span></span>
2. <span data-ttu-id="c21d0-181">開啟**Decibel Visual Studio 方案**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-181">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="c21d0-182">如果將部署到 HoloLens:</span><span class="sxs-lookup"><span data-stu-id="c21d0-182">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="c21d0-183">使用頂端的工具列，在 Visual Studio 中，從 偵錯，若要變更目標**Release**進出至 ARM **x86**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="c21d0-184">按一下下拉式清單 [本機電腦] 按鈕旁邊的箭號，然後選取**遠端機器**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-184">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="c21d0-185">請輸入**HoloLens 裝置的 IP 位址**並將驗證模式設定為**通用 （未加密的通訊協定）**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-185">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="c21d0-186">按一下 **選取**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-186">Click **Select**.</span></span> <span data-ttu-id="c21d0-187">如果您不知道您的裝置 IP 位址，查看**設定 > 網路和網際網路 > 進階選項**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-187">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="c21d0-188">在頂端功能表列中，按一下**偵錯]-> [啟動但不偵錯**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-188">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="c21d0-189">如果這是第一次部署到您的裝置，您必須[與 Visual Studio 中配對](using-visual-studio.md#pairing-your-device---hololens-1st-gen)。</span><span class="sxs-lookup"><span data-stu-id="c21d0-189">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).</span></span>

<span data-ttu-id="c21d0-190">如果將部署到擬真耳機：</span><span class="sxs-lookup"><span data-stu-id="c21d0-190">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="c21d0-191">使用頂端的工具列，在 Visual Studio 中，從 偵錯，若要變更目標**Release**進出至 ARM **x64**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-191">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="c21d0-192">請確定部署目標設定為**本機電腦**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-192">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="c21d0-193">在頂端功能表列中，按一下**偵錯]-> [啟動但不偵錯**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-193">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="c21d0-194">第 2 章-空間音效和互動</span><span class="sxs-lookup"><span data-stu-id="c21d0-194">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="c21d0-195">目標</span><span class="sxs-lookup"><span data-stu-id="c21d0-195">Objectives</span></span>

* <span data-ttu-id="c21d0-196">加強使用音效的全像真實性。</span><span class="sxs-lookup"><span data-stu-id="c21d0-196">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="c21d0-197">將使用者的視線使用音效。</span><span class="sxs-lookup"><span data-stu-id="c21d0-197">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="c21d0-198">提供使用音效的筆勢意見反應。</span><span class="sxs-lookup"><span data-stu-id="c21d0-198">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="c21d0-199">第 1 部分-增強的真實性</span><span class="sxs-lookup"><span data-stu-id="c21d0-199">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="c21d0-200">重要概念</span><span class="sxs-lookup"><span data-stu-id="c21d0-200">Key Concepts</span></span>

* <span data-ttu-id="c21d0-201">Spatialize 全像音效。</span><span class="sxs-lookup"><span data-stu-id="c21d0-201">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="c21d0-202">音效來源應該放在全像圖上的適當位置中。</span><span class="sxs-lookup"><span data-stu-id="c21d0-202">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="c21d0-203">音效的適當位置會取決於全像圖。</span><span class="sxs-lookup"><span data-stu-id="c21d0-203">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="c21d0-204">比方說，如果全像人類，音效來源應該靠近嘴巴無法英呎。</span><span class="sxs-lookup"><span data-stu-id="c21d0-204">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="c21d0-205">指示</span><span class="sxs-lookup"><span data-stu-id="c21d0-205">Instructions</span></span>

<span data-ttu-id="c21d0-206">下列指示會附加至全像圖的 spatialized 的音效。</span><span class="sxs-lookup"><span data-stu-id="c21d0-206">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="c21d0-207">在 [**階層**] 面板中，展開**HologramCollection** ，然後選取**P0LY**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-207">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="c21d0-208">在 [ **Inspector** ] 面板的**AudioSource**旁, 按一下圓形**AudioClip** ，然後選取**PolyHover**從快顯視窗中。</span><span class="sxs-lookup"><span data-stu-id="c21d0-208">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="c21d0-209">按一下旁邊的圓形**輸出**，然後選取**SoundEffects**從快顯視窗中。</span><span class="sxs-lookup"><span data-stu-id="c21d0-209">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="c21d0-210">專案 Decibel 使用 Unity **AudioMixer**啟用調整音效的音量的群組層級的元件。</span><span class="sxs-lookup"><span data-stu-id="c21d0-210">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="c21d0-211">受到群組音效如此一來，整體的磁碟區可以進行調整，同時維持每個音效的相對音量。</span><span class="sxs-lookup"><span data-stu-id="c21d0-211">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="c21d0-212">在  **AudioSource**，展開**3D 音效設定**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-212">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="c21d0-213">設定**Doppler 層級**要**0**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-213">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="c21d0-214">Doppler 層級設定為零會停用中的變更 （無論是全像 」 或 「 使用者） 的動作所造成的字幅。</span><span class="sxs-lookup"><span data-stu-id="c21d0-214">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="c21d0-215">Doppler 的典型範例是瞬息萬變的汽車。</span><span class="sxs-lookup"><span data-stu-id="c21d0-215">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="c21d0-216">車輛接近 「 定態的接聽程式時，引擎的字幅上升。</span><span class="sxs-lookup"><span data-stu-id="c21d0-216">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="c21d0-217">當它通過接聽程式時，字幅降低距離。</span><span class="sxs-lookup"><span data-stu-id="c21d0-217">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="c21d0-218">第 2 部分-導向使用者的視線</span><span class="sxs-lookup"><span data-stu-id="c21d0-218">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="c21d0-219">重要概念</span><span class="sxs-lookup"><span data-stu-id="c21d0-219">Key Concepts</span></span>

* <span data-ttu-id="c21d0-220">您可以使用音效來醒目提示重要全像投影。</span><span class="sxs-lookup"><span data-stu-id="c21d0-220">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="c21d0-221">어 有助於引導外觀的眼睛。</span><span class="sxs-lookup"><span data-stu-id="c21d0-221">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="c21d0-222">大腦有某些所學習到的期望。</span><span class="sxs-lookup"><span data-stu-id="c21d0-222">The brain has some learned expectations.</span></span>

<span data-ttu-id="c21d0-223">所學習到預期的其中一個範例是鳥通常會讓人判讀的讀寫頭上方。</span><span class="sxs-lookup"><span data-stu-id="c21d0-223">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="c21d0-224">如果使用者聽到 bird 音效，其反應是查閱。</span><span class="sxs-lookup"><span data-stu-id="c21d0-224">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="c21d0-225">放置 bird 以下使用者可能會導致它們對向的聲音，但其無法找到根據期望的需要來查閱全像正確的方向。</span><span class="sxs-lookup"><span data-stu-id="c21d0-225">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="c21d0-226">指示</span><span class="sxs-lookup"><span data-stu-id="c21d0-226">Instructions</span></span>

<span data-ttu-id="c21d0-227">下列指示啟用 P0LY 背後，隱藏，以便您可以使用音效來找出全像圖。</span><span class="sxs-lookup"><span data-stu-id="c21d0-227">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="c21d0-228">在 **階層**面板中，選取**管理員**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-228">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="c21d0-229">在 [ **Inspector** ] 面板中，尋找**語音輸入處理常式**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-229">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="c21d0-230">在 **語音輸入處理常式**，展開**移隱藏**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-230">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="c21d0-231">變更**沒有任何函式**要**PolyActions.GoHide**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-231">Change **No Function** to **PolyActions.GoHide**.</span></span>

![關鍵字：移隱藏](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="c21d0-233">第 3 部分-筆勢的意見反應</span><span class="sxs-lookup"><span data-stu-id="c21d0-233">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="c21d0-234">重要概念</span><span class="sxs-lookup"><span data-stu-id="c21d0-234">Key Concepts</span></span>

* <span data-ttu-id="c21d0-235">對使用者提供正面的筆勢確認使用音效</span><span class="sxs-lookup"><span data-stu-id="c21d0-235">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="c21d0-236">不會拖垮使用者-太大聲音效 get 的方式</span><span class="sxs-lookup"><span data-stu-id="c21d0-236">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="c21d0-237">細微的音效適合-不會 overshadow 體驗</span><span class="sxs-lookup"><span data-stu-id="c21d0-237">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="c21d0-238">指示</span><span class="sxs-lookup"><span data-stu-id="c21d0-238">Instructions</span></span>

* <span data-ttu-id="c21d0-239">在 [**階層**] 面板中，展開**HologramCollection**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-239">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="c21d0-240">依序展開**EnergyHub** ，然後選取**基底**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-240">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="c21d0-241">在**Inspector**  面板中，按一下**新增元件**，並新增**軌跡音效處理常式**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-241">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="c21d0-242">中**軌跡音效處理常式**旁, 按一下圓形**瀏覽啟動剪輯**並**導覽更新剪輯**，然後選取**RotateClick**從快顯視窗中兩個。</span><span class="sxs-lookup"><span data-stu-id="c21d0-242">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="c21d0-243">按兩下 「 GestureSoundHandler"在 Visual Studio 中載入。</span><span class="sxs-lookup"><span data-stu-id="c21d0-243">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="c21d0-244">筆勢音效處理常式會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="c21d0-244">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="c21d0-245">建立和設定**AudioSource**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-245">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="c21d0-246">地方**AudioSource**的適當位置**GameObject**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-246">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="c21d0-247">在扮演**AudioClip**與筆勢相關聯。</span><span class="sxs-lookup"><span data-stu-id="c21d0-247">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="c21d0-248">建置和部署</span><span class="sxs-lookup"><span data-stu-id="c21d0-248">Build and Deploy</span></span>

1. <span data-ttu-id="c21d0-249">在 Unity 中，選取**檔案 > 組建設定**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-249">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="c21d0-250">按一下 [建置] 。</span><span class="sxs-lookup"><span data-stu-id="c21d0-250">Click **Build**.</span></span>
3. <span data-ttu-id="c21d0-251">只要按一下**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="c21d0-251">Single click the **App** folder.</span></span>
4. <span data-ttu-id="c21d0-252">按下**選取資料夾**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-252">Press **Select Folder**.</span></span>

<span data-ttu-id="c21d0-253">請檢查工具列顯示"Release"、"x86"或"x64"，以及 「 遠端裝置 」。</span><span class="sxs-lookup"><span data-stu-id="c21d0-253">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="c21d0-254">如果沒有，這是 Visual Studio 的程式碼的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c21d0-254">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="c21d0-255">您可能需要重新開啟方案，從應用程式資料夾。</span><span class="sxs-lookup"><span data-stu-id="c21d0-255">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="c21d0-256">如果出現提示，請重新載入專案檔。</span><span class="sxs-lookup"><span data-stu-id="c21d0-256">If prompted, reload the project files.</span></span>
* <span data-ttu-id="c21d0-257">同樣地，從 Visual Studio 部署。</span><span class="sxs-lookup"><span data-stu-id="c21d0-257">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="c21d0-258">應用程式部署後：</span><span class="sxs-lookup"><span data-stu-id="c21d0-258">After the application is deployed:</span></span>

* <span data-ttu-id="c21d0-259">觀察當您移動 P0LY 音效要如何變更。</span><span class="sxs-lookup"><span data-stu-id="c21d0-259">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="c21d0-260">假設 *「 移隱藏 」* 讓 P0LY 移到您背後的位置。</span><span class="sxs-lookup"><span data-stu-id="c21d0-260">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="c21d0-261">發現的音效。</span><span class="sxs-lookup"><span data-stu-id="c21d0-261">Find it by the sound.</span></span>
* <span data-ttu-id="c21d0-262">注視的能源中樞基底。</span><span class="sxs-lookup"><span data-stu-id="c21d0-262">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="c21d0-263">點選並拖曳左或向右旋轉全像圖，並請注意如何滑鼠的聲音確認筆勢。</span><span class="sxs-lookup"><span data-stu-id="c21d0-263">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="c21d0-264">注意：沒有文字面板，可將與您的 tag-along。</span><span class="sxs-lookup"><span data-stu-id="c21d0-264">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="c21d0-265">這會包含在本課程中，您可以使用可用的語音命令。</span><span class="sxs-lookup"><span data-stu-id="c21d0-265">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="c21d0-266">第 3 章-空間音效和空間的對應</span><span class="sxs-lookup"><span data-stu-id="c21d0-266">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="c21d0-267">目標</span><span class="sxs-lookup"><span data-stu-id="c21d0-267">Objectives</span></span>

* <span data-ttu-id="c21d0-268">確認全像投影與真實世界使用音效之間的互動。</span><span class="sxs-lookup"><span data-stu-id="c21d0-268">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="c21d0-269">Occlude 使用真實世界的音效。</span><span class="sxs-lookup"><span data-stu-id="c21d0-269">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="c21d0-270">第 1 部分-真實世界互動</span><span class="sxs-lookup"><span data-stu-id="c21d0-270">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="c21d0-271">重要概念</span><span class="sxs-lookup"><span data-stu-id="c21d0-271">Key Concepts</span></span>

* <span data-ttu-id="c21d0-272">實體物件通常發出聲音時遇到一個介面，或另一個物件。</span><span class="sxs-lookup"><span data-stu-id="c21d0-272">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="c21d0-273">聽起來應該是適當的體驗中的內容。</span><span class="sxs-lookup"><span data-stu-id="c21d0-273">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="c21d0-274">比方說，在資料表上設定一杯要比卸除在一段 metal boulder 安靜音效。</span><span class="sxs-lookup"><span data-stu-id="c21d0-274">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="c21d0-275">指示</span><span class="sxs-lookup"><span data-stu-id="c21d0-275">Instructions</span></span>

* <span data-ttu-id="c21d0-276">在 [**階層**] 面板中，展開**HologramCollection**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-276">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="c21d0-277">依序展開**EnergyHub**，選取**基底**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-277">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="c21d0-278">在**Inspector**  面板中，按一下**新增元件**，並新增**點選來進行與聲音和動作**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-278">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="c21d0-279">在 **點選以使用音效和動作的地方**:</span><span class="sxs-lookup"><span data-stu-id="c21d0-279">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="c21d0-280">請檢查**父置於點選**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-280">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="c21d0-281">設定**放置音效**要**地方**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-281">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="c21d0-282">設定**Pickup 音效**要**Pickup**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-282">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="c21d0-283">按下 + 兩者都在底部**Pickup 動作上**並**上放置動作**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-283">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="c21d0-284">從到場景拖曳 EnergyHub**無 （物件）** 欄位。</span><span class="sxs-lookup"><span data-stu-id="c21d0-284">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="c21d0-285">底下**Pickup 動作上**，按一下**No 函式** -> **EnergyHubBase** -> **ResetAnimation**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-285">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="c21d0-286">底下**上放置動作**，按一下**No 函式** -> **EnergyHubBase** -> **OnSelect**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-286">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![點選以使用音效和動作的位置](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="c21d0-288">第 2 部分-音效的阻擋物</span><span class="sxs-lookup"><span data-stu-id="c21d0-288">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="c21d0-289">重要概念</span><span class="sxs-lookup"><span data-stu-id="c21d0-289">Key Concepts</span></span>

* <span data-ttu-id="c21d0-290">如同光線，可以阻擋。</span><span class="sxs-lookup"><span data-stu-id="c21d0-290">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="c21d0-291">典型的例子是 concert hall。</span><span class="sxs-lookup"><span data-stu-id="c21d0-291">A classic example is a concert hall.</span></span> <span data-ttu-id="c21d0-292">當接聽程式釐 hall 和門以外的單位已關閉，muffled 音樂音效。</span><span class="sxs-lookup"><span data-stu-id="c21d0-292">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="c21d0-293">另外還有通常縮小磁碟區。</span><span class="sxs-lookup"><span data-stu-id="c21d0-293">There is also typically a reduction in volume.</span></span> <span data-ttu-id="c21d0-294">機門開啟時，完整廣泛的聲音會聽到在實際的磁碟區。</span><span class="sxs-lookup"><span data-stu-id="c21d0-294">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="c21d0-295">高頻率音效通常是多個低頻率吸收。</span><span class="sxs-lookup"><span data-stu-id="c21d0-295">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="c21d0-296">指示</span><span class="sxs-lookup"><span data-stu-id="c21d0-296">Instructions</span></span>

* <span data-ttu-id="c21d0-297">在 [**階層**] 面板中，展開**HologramCollection** ，然後選取**P0LY**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-297">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="c21d0-298">在  **Inspector**  面板中，按一下 **新增元件**並新增**音訊 fixit 發出器**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-298">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="c21d0-299">音訊 fixit 發出器類別會提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="c21d0-299">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="c21d0-300">將任何變更還原的磁碟區**AudioSource**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-300">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="c21d0-301">會執行**Physics.RaycastNonAlloc**從使用者的位置中的方向**GameObject**要**AudioEmitter**附加。</span><span class="sxs-lookup"><span data-stu-id="c21d0-301">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="c21d0-302">RaycastNonAlloc 方法當做效能最佳化來配置，以及傳回的結果數目限制。</span><span class="sxs-lookup"><span data-stu-id="c21d0-302">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="c21d0-303">每個**IAudioInfluencer**遇到，呼叫**ApplyEffect**方法。</span><span class="sxs-lookup"><span data-stu-id="c21d0-303">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="c21d0-304">每個先前**IAudioInfluencer**也就是不會再發生，呼叫**RemoveEffect**方法。</span><span class="sxs-lookup"><span data-stu-id="c21d0-304">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="c21d0-305">請注意，AudioEmitter 上更新人性化的時間間隔，而不是以每個畫面格為基礎。</span><span class="sxs-lookup"><span data-stu-id="c21d0-305">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="c21d0-306">這是因為人們通常不會移動速度夠快的要需要更新頻率高於每季或半秒的效果。</span><span class="sxs-lookup"><span data-stu-id="c21d0-306">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="c21d0-307">全像投影快速從一個位置，傳送到另一個可能會中斷的假象。</span><span class="sxs-lookup"><span data-stu-id="c21d0-307">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="c21d0-308">在 [**階層**] 面板中，展開**HologramCollection**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-308">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="c21d0-309">依序展開**EnergyHub** ，然後選取**BlobOutside**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-309">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="c21d0-310">在  **Inspector**  面板中，按一下 **新增元件**並新增**音訊 Occluder**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-310">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="c21d0-311">在 **音訊 Occluder**，將**截止頻率**來**1500年**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-311">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="c21d0-312">此設定會限制 AudioSource 頻率 1500 Hz 和以下版本。</span><span class="sxs-lookup"><span data-stu-id="c21d0-312">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="c21d0-313">設定**磁碟區通過**要**0.9**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-313">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="c21d0-314">此設定可減少的 AudioSource 為它的目前層級 90%。</span><span class="sxs-lookup"><span data-stu-id="c21d0-314">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="c21d0-315">音訊 Occluder 實作 IAudioInfluencer 來：</span><span class="sxs-lookup"><span data-stu-id="c21d0-315">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="c21d0-316">阻擋效果使用套用**AudioLowPassFilter**這會附加到**AudioSource**受管理的購買**AudioEmitter**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-316">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="c21d0-317">適用於 AudioSource 磁碟區衰減。</span><span class="sxs-lookup"><span data-stu-id="c21d0-317">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="c21d0-318">藉由設定中性的截止頻率，並停用篩選器，停用生效。</span><span class="sxs-lookup"><span data-stu-id="c21d0-318">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="c21d0-319">做為中性的頻率是 22 kHz (22000 Hz)。</span><span class="sxs-lookup"><span data-stu-id="c21d0-319">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="c21d0-320">因為它正在上面可以聽到的人耳，這對不會明顯影響聲音的名義上的最大頻率會選擇此頻率。</span><span class="sxs-lookup"><span data-stu-id="c21d0-320">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="c21d0-321">在 **階層**面板中，選取**SpatialMapping**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-321">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="c21d0-322">在  **Inspector**  面板中，按一下 **新增元件**並新增**音訊 Occluder**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-322">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="c21d0-323">在 **音訊 Occluder**，將**截止頻率**來**750**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-323">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="c21d0-324">當多個 occluders 位於使用者之間的路徑，而**AudioEmitter**，最低的頻率會套用至篩選條件。</span><span class="sxs-lookup"><span data-stu-id="c21d0-324">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="c21d0-325">設定**磁碟區通過**要**0.75**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-325">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="c21d0-326">當多個 occluders 位於使用者之間的路徑， **AudioEmitter**，磁碟區通過火套用。</span><span class="sxs-lookup"><span data-stu-id="c21d0-326">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="c21d0-327">在 **階層**面板中，選取**管理員**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-327">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="c21d0-328">在 [ **Inspector** ] 面板中，展開**語音輸入處理常式**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-328">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="c21d0-329">在 **語音輸入處理常式**，展開**移費用**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-329">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="c21d0-330">變更**沒有任何函式**要**PolyActions.GoCharge**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-330">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![關鍵字：移費用](images/gocharge.png)

* <span data-ttu-id="c21d0-332">依序展開**這裡**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-332">Expand **Come Here**.</span></span>
* <span data-ttu-id="c21d0-333">變更**沒有任何函式**要**PolyActions.ComeBack**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-333">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![關鍵字：到這裡](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="c21d0-335">建置和部署</span><span class="sxs-lookup"><span data-stu-id="c21d0-335">Build and Deploy</span></span>

* <span data-ttu-id="c21d0-336">同樣地，建置 Unity 專案，並在 Visual Studio 中部署。</span><span class="sxs-lookup"><span data-stu-id="c21d0-336">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="c21d0-337">應用程式部署後：</span><span class="sxs-lookup"><span data-stu-id="c21d0-337">After the application is deployed:</span></span>

* <span data-ttu-id="c21d0-338">假設 *「 移費用"* 有 P0LY 輸入能源中樞。</span><span class="sxs-lookup"><span data-stu-id="c21d0-338">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="c21d0-339">請注意音效中的變更。</span><span class="sxs-lookup"><span data-stu-id="c21d0-339">Note the change in the sound.</span></span> <span data-ttu-id="c21d0-340">它應該音效 muffled 和有點較小聲。</span><span class="sxs-lookup"><span data-stu-id="c21d0-340">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="c21d0-341">如果您能夠自行位置與塗鴉牆或您與能源中樞之間的其他物件時，您應該注意到因為真實世界會受阻擋音效進一步 muffling。</span><span class="sxs-lookup"><span data-stu-id="c21d0-341">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="c21d0-342">假設 *「 此處出現 」* 有 P0LY 保留能源中樞，並將本身放置您面前。</span><span class="sxs-lookup"><span data-stu-id="c21d0-342">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="c21d0-343">請注意，一旦 P0LY 結束能源中樞也會移除音效的阻擋物。</span><span class="sxs-lookup"><span data-stu-id="c21d0-343">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="c21d0-344">如果您仍然是期待阻擋，就可能會阻擋 P0LY 真實世界。</span><span class="sxs-lookup"><span data-stu-id="c21d0-344">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="c21d0-345">請嘗試以確定您有清楚的視野 P0LY 移動。</span><span class="sxs-lookup"><span data-stu-id="c21d0-345">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="c21d0-346">第 3 部分-聊天室模型</span><span class="sxs-lookup"><span data-stu-id="c21d0-346">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="c21d0-347">重要概念</span><span class="sxs-lookup"><span data-stu-id="c21d0-347">Key Concepts</span></span>

* <span data-ttu-id="c21d0-348">空間的大小提供張神奇參與音效當地語系化的佇列。</span><span class="sxs-lookup"><span data-stu-id="c21d0-348">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="c21d0-349">聊天室模型設定每位**AudioSource**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-349">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="c21d0-350">[Unity 的 MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)提供程式碼，將空間模式設定。</span><span class="sxs-lookup"><span data-stu-id="c21d0-350">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="c21d0-351">混合實境體驗，針對選取的空間模型最適合的真實世界空間。</span><span class="sxs-lookup"><span data-stu-id="c21d0-351">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="c21d0-352">如果您要建立的虛擬實境案例，請選取 聊天室模型最適合虛擬環境。</span><span class="sxs-lookup"><span data-stu-id="c21d0-352">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="c21d0-353">第 4 章-完善的設計</span><span class="sxs-lookup"><span data-stu-id="c21d0-353">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="c21d0-354">目標</span><span class="sxs-lookup"><span data-stu-id="c21d0-354">Objectives</span></span>

* <span data-ttu-id="c21d0-355">了解有效完善的設計考量。</span><span class="sxs-lookup"><span data-stu-id="c21d0-355">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="c21d0-356">了解混用技術和指導方針。</span><span class="sxs-lookup"><span data-stu-id="c21d0-356">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="c21d0-357">第 1 部分-音效和體驗設計</span><span class="sxs-lookup"><span data-stu-id="c21d0-357">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="c21d0-358">本章節將討論主要的聲音和經驗的設計考量和指導方針。</span><span class="sxs-lookup"><span data-stu-id="c21d0-358">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="c21d0-359">標準化所有的音效</span><span class="sxs-lookup"><span data-stu-id="c21d0-359">Normalize all sounds</span></span>

<span data-ttu-id="c21d0-360">這可避免需要特殊案例的程式碼來調整每個可能會很費時的音效的音量，並限制能夠輕鬆地更新音效檔。</span><span class="sxs-lookup"><span data-stu-id="c21d0-360">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="c21d0-361">設計 untethered 體驗</span><span class="sxs-lookup"><span data-stu-id="c21d0-361">Design for an untethered experience</span></span>

<span data-ttu-id="c21d0-362">HoloLens 是完全自主、 untethered 全像攝影版的電腦。</span><span class="sxs-lookup"><span data-stu-id="c21d0-362">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="c21d0-363">您的使用者可以與將會使用您在移動時的體驗。</span><span class="sxs-lookup"><span data-stu-id="c21d0-363">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="c21d0-364">請務必測試您的聲音混合四處跑。</span><span class="sxs-lookup"><span data-stu-id="c21d0-364">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="c21d0-365">發出音效，從您全像投影上的邏輯位置</span><span class="sxs-lookup"><span data-stu-id="c21d0-365">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="c21d0-366">在真實世界中，dog 不會不會從其尾端吠，人類的語音不是來自他/她英呎。</span><span class="sxs-lookup"><span data-stu-id="c21d0-366">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="c21d0-367">避免您的聲音發出從您全像投影中未預期的部份。</span><span class="sxs-lookup"><span data-stu-id="c21d0-367">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="c21d0-368">針對小型全像投影，很合理的幾何中心所發出的聲音。</span><span class="sxs-lookup"><span data-stu-id="c21d0-368">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="c21d0-369">熟悉的聲音都是最可當地語系化</span><span class="sxs-lookup"><span data-stu-id="c21d0-369">Familiar sounds are most localizable</span></span>

<span data-ttu-id="c21d0-370">人類聲音和音樂是很容易就能當地語系化。</span><span class="sxs-lookup"><span data-stu-id="c21d0-370">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="c21d0-371">只要有人撥打您的名稱，就能夠精確地判斷哪些來源之語音的方向和如何很遠的地方。</span><span class="sxs-lookup"><span data-stu-id="c21d0-371">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="c21d0-372">簡短、 不熟悉聽起來較難以當地語系化。</span><span class="sxs-lookup"><span data-stu-id="c21d0-372">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="c21d0-373">網站的使用者的期望</span><span class="sxs-lookup"><span data-stu-id="c21d0-373">Be cognizant of user expectations</span></span>

<span data-ttu-id="c21d0-374">生命週期體驗扮演一個角色在我們能夠識別音效的位置。</span><span class="sxs-lookup"><span data-stu-id="c21d0-374">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="c21d0-375">這是其中一個原因，人類聲音為何特別容易當地語系化。</span><span class="sxs-lookup"><span data-stu-id="c21d0-375">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="c21d0-376">請務必留意您的使用者所學習到的期望放置您的聲音時。</span><span class="sxs-lookup"><span data-stu-id="c21d0-376">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="c21d0-377">比方說，當有人聽到 bird 歌曲他們通常查閱，因為鳥通常超過視野 （飛行或樹狀目錄中）。</span><span class="sxs-lookup"><span data-stu-id="c21d0-377">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="c21d0-378">是不常見的使用者開啟中，正確的方向，但看了錯誤的垂直方向，並成為混淆或挫折時找不到全像的位置。</span><span class="sxs-lookup"><span data-stu-id="c21d0-378">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="c21d0-379">避免隱藏的 fixit 發出器</span><span class="sxs-lookup"><span data-stu-id="c21d0-379">Avoid hidden emitters</span></span>

<span data-ttu-id="c21d0-380">在真實世界中，如果我們聽到聲音，我們可以通常識別發出聲音的物件。</span><span class="sxs-lookup"><span data-stu-id="c21d0-380">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="c21d0-381">這也應該保留在您的經驗，則為 true。</span><span class="sxs-lookup"><span data-stu-id="c21d0-381">This should also hold true in your experiences.</span></span> <span data-ttu-id="c21d0-382">它可以是非常令人不安聽到聲音，就是從來源位置的聲音的使用者，並無法看到物件。</span><span class="sxs-lookup"><span data-stu-id="c21d0-382">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="c21d0-383">有一些例外狀況，這個指導方針。</span><span class="sxs-lookup"><span data-stu-id="c21d0-383">There are some exceptions to this guideline.</span></span> <span data-ttu-id="c21d0-384">例如，環境的音效，例如 crickets 欄位中不需要會顯示。</span><span class="sxs-lookup"><span data-stu-id="c21d0-384">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="c21d0-385">生命週期體驗讓我們熟悉這些聲音，而不需要看到它的來源。</span><span class="sxs-lookup"><span data-stu-id="c21d0-385">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="c21d0-386">第 2 部分-聲音混合</span><span class="sxs-lookup"><span data-stu-id="c21d0-386">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="c21d0-387">以您的混合 HoloLens 上 70%的磁碟區為目標</span><span class="sxs-lookup"><span data-stu-id="c21d0-387">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="c21d0-388">混合的實境體驗可讓全像投影至真實世界中看到。</span><span class="sxs-lookup"><span data-stu-id="c21d0-388">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="c21d0-389">它們也可讓要聽到的真實世界音效。</span><span class="sxs-lookup"><span data-stu-id="c21d0-389">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="c21d0-390">70%的磁碟區目標可讓使用者聽周遭世界，以及您的使用經驗的聲音。</span><span class="sxs-lookup"><span data-stu-id="c21d0-390">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="c21d0-391">在 100%的磁碟區的 HoloLens 應該掉外部清單</span><span class="sxs-lookup"><span data-stu-id="c21d0-391">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="c21d0-392">100%的磁碟區層級就像虛擬實境體驗。</span><span class="sxs-lookup"><span data-stu-id="c21d0-392">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="c21d0-393">以視覺化的方式，使用者會傳輸到不同的世界。</span><span class="sxs-lookup"><span data-stu-id="c21d0-393">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="c21d0-394">相同應該成立用語音。</span><span class="sxs-lookup"><span data-stu-id="c21d0-394">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="c21d0-395">使用 Unity AudioMixer 調整音效的類別</span><span class="sxs-lookup"><span data-stu-id="c21d0-395">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="c21d0-396">在設計您的混合時，通常很有幫助建立音效的類別，並有增加或減少其做為一個單位的磁碟區的能力。</span><span class="sxs-lookup"><span data-stu-id="c21d0-396">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="c21d0-397">這同時啟用快速且輕鬆地對整體混合保留相對的層級的每一種音效。</span><span class="sxs-lookup"><span data-stu-id="c21d0-397">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="c21d0-398">通用類別目錄包括：音效、 環境、 旁白和背景音樂。</span><span class="sxs-lookup"><span data-stu-id="c21d0-398">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="c21d0-399">根據使用者的視線混合音效</span><span class="sxs-lookup"><span data-stu-id="c21d0-399">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="c21d0-400">它通常可用來變更的聲音混合在您的位置為基礎的體驗或使用者的 （不） 尋找。</span><span class="sxs-lookup"><span data-stu-id="c21d0-400">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="c21d0-401">這項技術的常見用法之一是要減少全像投影全像攝影版的畫面格，以簡化使用者將焦點放在前面的資訊以外的磁碟區層級。</span><span class="sxs-lookup"><span data-stu-id="c21d0-401">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="c21d0-402">另一個用法是音效的，增加來強調使用者的一個重要事件的音量。</span><span class="sxs-lookup"><span data-stu-id="c21d0-402">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="c21d0-403">建置您混合</span><span class="sxs-lookup"><span data-stu-id="c21d0-403">Building your mix</span></span>

<span data-ttu-id="c21d0-404">當建置您混合時，建議您開始使用您的體驗背景音訊，並新增根據重要性層級。</span><span class="sxs-lookup"><span data-stu-id="c21d0-404">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="c21d0-405">通常，這會導致正在比先前的每個圖層。</span><span class="sxs-lookup"><span data-stu-id="c21d0-405">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="c21d0-406">想像您混用做為反向的漏斗圖，以最不重要 （及一般 quietest 聲音） 在底部，建議以結構化您的混合類似下圖。</span><span class="sxs-lookup"><span data-stu-id="c21d0-406">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![聲音混合結構](images/soundlevels.png)

<span data-ttu-id="c21d0-408">旁白是有趣的案例。</span><span class="sxs-lookup"><span data-stu-id="c21d0-408">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="c21d0-409">根據您所建立的經驗，您可能想讓立體聲的 （未當地語系化） 音效，或是 spatialize 您旁白。</span><span class="sxs-lookup"><span data-stu-id="c21d0-409">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="c21d0-410">兩個 Microsoft 發行體驗說明每個案例的絕佳範例。</span><span class="sxs-lookup"><span data-stu-id="c21d0-410">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="c21d0-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87)透過使用立體聲的語音。</span><span class="sxs-lookup"><span data-stu-id="c21d0-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="c21d0-412">當 [朗讀程式] 會描述正在檢視的位置時，音效是一致，而不會隨著使用者的位置。</span><span class="sxs-lookup"><span data-stu-id="c21d0-412">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="c21d0-413">這可讓朗讀程式，來描述而不離開環境 spatialized 音效製作場景。</span><span class="sxs-lookup"><span data-stu-id="c21d0-413">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="c21d0-414">[片段](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8)偵探的形式，透過利用 spatialized 的語音。</span><span class="sxs-lookup"><span data-stu-id="c21d0-414">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="c21d0-415">神探語音用來協助您將使用者的重要線索注意，如同實際的人類看得在聊天室中。</span><span class="sxs-lookup"><span data-stu-id="c21d0-415">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="c21d0-416">這可讓至體驗的訓練活動，解決神秘的更有意義。</span><span class="sxs-lookup"><span data-stu-id="c21d0-416">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="c21d0-417">部分 3-效能</span><span class="sxs-lookup"><span data-stu-id="c21d0-417">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="c21d0-418">CPU 使用量</span><span class="sxs-lookup"><span data-stu-id="c21d0-418">CPU usage</span></span>

<span data-ttu-id="c21d0-419">當使用空間音效，10-12 fixit 發出器會耗用大約 12%的 CPU。</span><span class="sxs-lookup"><span data-stu-id="c21d0-419">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="c21d0-420">Stream 長音訊檔案</span><span class="sxs-lookup"><span data-stu-id="c21d0-420">Stream long audio files</span></span>

<span data-ttu-id="c21d0-421">音訊資料可以是很大，尤其是在常見的取樣率 (44.1 和 48 kHz)。</span><span class="sxs-lookup"><span data-stu-id="c21d0-421">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="c21d0-422">一般規則是超過 5-10 秒的音訊檔案應該將它串流至降低應用程式的記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="c21d0-422">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="c21d0-423">在 Unity 中，您可以將標記中的檔案匯入設定資料流的音訊檔案。</span><span class="sxs-lookup"><span data-stu-id="c21d0-423">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![音訊的匯入設定](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="c21d0-425">第 5 章-特殊效果</span><span class="sxs-lookup"><span data-stu-id="c21d0-425">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="c21d0-426">目標</span><span class="sxs-lookup"><span data-stu-id="c21d0-426">Objectives</span></span>

* <span data-ttu-id="c21d0-427">加入 「 魔術 Windows 」 中的深度。</span><span class="sxs-lookup"><span data-stu-id="c21d0-427">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="c21d0-428">帶入虛擬世界中的使用者。</span><span class="sxs-lookup"><span data-stu-id="c21d0-428">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="c21d0-429">Magic Windows</span><span class="sxs-lookup"><span data-stu-id="c21d0-429">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="c21d0-430">重要概念</span><span class="sxs-lookup"><span data-stu-id="c21d0-430">Key Concepts</span></span>

* <span data-ttu-id="c21d0-431">到隱藏的世界中建立檢視，是以視覺方式吸引人。</span><span class="sxs-lookup"><span data-stu-id="c21d0-431">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="c21d0-432">加入音訊效果，接近隱藏世界雷射或使用者時，以加強真實性。</span><span class="sxs-lookup"><span data-stu-id="c21d0-432">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="c21d0-433">指示</span><span class="sxs-lookup"><span data-stu-id="c21d0-433">Instructions</span></span>

* <span data-ttu-id="c21d0-434">在 [**階層**] 面板中，展開**HologramCollection** ，然後選取**底世界**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-434">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="c21d0-435">依序展開**底世界**，然後選取**VoiceSource**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-435">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="c21d0-436">在**Inspector**  面板中，按一下**新增元件**，並新增**使用者語音效果**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-436">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="c21d0-437">**AudioSource**元件會加入至**VoiceSource**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-437">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="c21d0-438">在  **AudioSource**，將**輸出**來**UserVoice (Mixer)**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-438">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="c21d0-439">請檢查**Spatialize**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c21d0-439">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="c21d0-440">拖曳**空間 Blend**滑桿，一直到**3D**，或輸入**1**編輯方塊中。</span><span class="sxs-lookup"><span data-stu-id="c21d0-440">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="c21d0-441">依序展開**3D 音效設定**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-441">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="c21d0-442">設定**Doppler 層級**要**0**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-442">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="c21d0-443">在**使用者語音生效**，將**父物件**來**底世界**從場景。</span><span class="sxs-lookup"><span data-stu-id="c21d0-443">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="c21d0-444">設定**最大距離**要**1**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-444">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="c21d0-445">設定**最大距離**告訴**使用者語音效果**接近的使用者必須是父物件之前已啟用的效果。</span><span class="sxs-lookup"><span data-stu-id="c21d0-445">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="c21d0-446">在 **使用者語音生效**，展開**陣營參數**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-446">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="c21d0-447">設定**深度**要**0.1**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-447">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="c21d0-448">設定**點選 1 個磁碟區**，**點選 2 的磁碟區**並**點選 3 個磁碟區**至**0.8**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-448">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="c21d0-449">設定**原始音效的音量**要**0.5**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-449">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="c21d0-450">先前的設定中設定之參數的 Unity **AudioChorusFilter**用來將功能新增至使用者的語音。</span><span class="sxs-lookup"><span data-stu-id="c21d0-450">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="c21d0-451">在 **使用者語音生效**，展開**Echo 參數**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-451">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="c21d0-452">設定**延遲**到**300**</span><span class="sxs-lookup"><span data-stu-id="c21d0-452">Set **Delay** to **300**</span></span>
* <span data-ttu-id="c21d0-453">設定**Decay 比例**要**0.2**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-453">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="c21d0-454">設定**原始音效的音量**要**0**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-454">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="c21d0-455">先前的設定中設定之參數的 Unity **AudioEchoFilter**用來造成使用者的語音來回應。</span><span class="sxs-lookup"><span data-stu-id="c21d0-455">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="c21d0-456">使用者語音效果指令碼會負責：</span><span class="sxs-lookup"><span data-stu-id="c21d0-456">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="c21d0-457">測量使用者之間的距離而**GameObject**附加指令碼。</span><span class="sxs-lookup"><span data-stu-id="c21d0-457">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="c21d0-458">判斷使用者是否正面向**GameObject**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-458">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="c21d0-459">使用者必須面對 GameObject，不論距離，要啟用的效果。</span><span class="sxs-lookup"><span data-stu-id="c21d0-459">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="c21d0-460">套用並設定**AudioChorusFilter**並**AudioEchoFilter**來**AudioSource**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-460">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="c21d0-461">停用篩選器停用生效。</span><span class="sxs-lookup"><span data-stu-id="c21d0-461">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="c21d0-462">使用者語音效果會使用 Mic Stream 選取器元件，從[Unity 的 MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)，以選取高品質的聲音資料流，並將它路由傳送至 Unity 的音響系統。</span><span class="sxs-lookup"><span data-stu-id="c21d0-462">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="c21d0-463">在 **階層**面板中，選取**管理員**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-463">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="c21d0-464">在 [ **Inspector** ] 面板中，展開**語音輸入處理常式**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-464">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="c21d0-465">在 **語音輸入處理常式**，展開**顯示底世界**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-465">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="c21d0-466">變更**沒有任何函式**要**UnderworldBase.OnEnable**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-466">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![關鍵字：顯示底世界](images/showunderworld.png)

* <span data-ttu-id="c21d0-468">依序展開**隱藏底世界**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-468">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="c21d0-469">變更**沒有任何函式**要**UnderworldBase.OnDisable**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-469">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![關鍵字：隱藏底世界](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="c21d0-471">建置和部署</span><span class="sxs-lookup"><span data-stu-id="c21d0-471">Build and Deploy</span></span>

* <span data-ttu-id="c21d0-472">同樣地，建置 Unity 專案，並在 Visual Studio 中部署。</span><span class="sxs-lookup"><span data-stu-id="c21d0-472">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="c21d0-473">應用程式部署後：</span><span class="sxs-lookup"><span data-stu-id="c21d0-473">After the application is deployed:</span></span>

* <span data-ttu-id="c21d0-474">面臨 （牆上、 floor、 資料表） 的介面和 say *」 顯示底世界 」*。</span><span class="sxs-lookup"><span data-stu-id="c21d0-474">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="c21d0-475">將顯示底世界，並將隱藏所有其他全像投影。</span><span class="sxs-lookup"><span data-stu-id="c21d0-475">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="c21d0-476">如果看不到底世界，請確定您所面對的現實世界的介面。</span><span class="sxs-lookup"><span data-stu-id="c21d0-476">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="c21d0-477">底世界全像之 1 公尺內的方法，並開始交談。</span><span class="sxs-lookup"><span data-stu-id="c21d0-477">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="c21d0-478">現在有音訊效果套用至您的心聲 ！</span><span class="sxs-lookup"><span data-stu-id="c21d0-478">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="c21d0-479">背離底世界，並注意效果不會再套用的方式。</span><span class="sxs-lookup"><span data-stu-id="c21d0-479">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="c21d0-480">假設 *「 隱藏底世界 」* 隱藏底世界。</span><span class="sxs-lookup"><span data-stu-id="c21d0-480">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="c21d0-481">將隱藏底世界，先前隱藏全像投影會重新出現。</span><span class="sxs-lookup"><span data-stu-id="c21d0-481">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="c21d0-482">結束</span><span class="sxs-lookup"><span data-stu-id="c21d0-482">The End</span></span>

<span data-ttu-id="c21d0-483">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="c21d0-483">Congratulations!</span></span> <span data-ttu-id="c21d0-484">您現在已完成**MR 空間 220:空間音效**。</span><span class="sxs-lookup"><span data-stu-id="c21d0-484">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="c21d0-485">聆聽世界和音效實現您的經驗 ！</span><span class="sxs-lookup"><span data-stu-id="c21d0-485">Listen to the world and bring your experiences to life with sound!</span></span>
