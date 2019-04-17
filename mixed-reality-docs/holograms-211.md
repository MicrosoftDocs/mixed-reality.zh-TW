---
title: MR 輸入 211-筆勢
description: 請遵循此程式碼撰寫的逐步解說，使用 Unity、 Visual Studio 和 HoloLens，若要了解筆勢概念的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、 mixedrealitytoolkit、 mixedrealitytoolkit unity、 academy、 教學課程中，軌跡
ms.openlocfilehash: 76d2b4c0ac3d0a3783b091f7dc8c39548a18b548
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596146"
---
>[!NOTE]
><span data-ttu-id="e6fe4-104">混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="e6fe4-105">因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="e6fe4-106">這些教學課程會**_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="e6fe4-107">它們會繼續運作，支援的裝置上維護。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="e6fe4-108">會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="e6fe4-109">當他們回傳時，本聲明將會更新這些教學課程的連結。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-211-gesture"></a><span data-ttu-id="e6fe4-110">MR 輸入 211:手勢</span><span class="sxs-lookup"><span data-stu-id="e6fe4-110">MR Input 211: Gesture</span></span>

<span data-ttu-id="e6fe4-111">[筆勢](gestures.md)變成動作的使用者意圖。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-111">[Gestures](gestures.md) turn user intention into action.</span></span> <span data-ttu-id="e6fe4-112">處理筆勢，使用者可以互動全像投影。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-112">With gestures, users can interact with holograms.</span></span> <span data-ttu-id="e6fe4-113">在此課程中，我們將了解如何追蹤使用者的手中，回應使用者輸入，和以提供給使用者的意見反應手邊基礎狀態下和位置。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-113">In this course, we'll learn how to track the user's hands, respond to user input, and give feedback to the user based on hand state and location.</span></span>

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

<span data-ttu-id="e6fe4-114">在  [MR 基本概念 101](holograms-101.md)，我們使用簡單的空中點選手勢互動我們全像投影。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-114">In [MR Basics 101](holograms-101.md), we used a simple air-tap gesture to interact with our holograms.</span></span> <span data-ttu-id="e6fe4-115">現在，我們會超越空中點選手勢，並瀏覽至新的概念：</span><span class="sxs-lookup"><span data-stu-id="e6fe4-115">Now, we'll move beyond the air-tap gesture and explore new concepts to:</span></span>

* <span data-ttu-id="e6fe4-116">偵測何時正在追蹤使用者的手狀，並提供意見反應給使用者。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-116">Detect when the user's hand is being tracked and provide feedback to the user.</span></span>
* <span data-ttu-id="e6fe4-117">您可以使用 瀏覽筆勢來旋轉我們全像投影。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-117">Use a navigation gesture to rotate our holograms.</span></span>
* <span data-ttu-id="e6fe4-118">當使用者的手超出檢視時，請提供意見反應。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-118">Provide feedback when the user's hand is about to go out of view.</span></span>
* <span data-ttu-id="e6fe4-119">您可以使用操作事件，讓使用者移動其指針與全像投影。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-119">Use manipulation events to allow users to move holograms with their hands.</span></span>

<span data-ttu-id="e6fe4-120">在此課程中，我們再探討 Unity 專案**模型總管**，我們建置[MR 輸入 210](holograms-210.md)。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-120">In this course, we'll revisit the Unity project **Model Explorer**, which we built in [MR Input 210](holograms-210.md).</span></span> <span data-ttu-id="e6fe4-121">我們太空人朋友是回到協助我們探索這些新的筆勢概念。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-121">Our astronaut friend is back to assist us in our exploration of these new gesture concepts.</span></span>

>[!IMPORTANT]
><span data-ttu-id="e6fe4-122">使用 Unity 及混合實境 toolkit 的推出較舊的版本記錄中的下列章節的每個內嵌的影片。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-122">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="e6fe4-123">雖然的逐步指示是準確且即時的您可能會看到指令碼和對應已過期的影片中的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-123">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="e6fe4-124">影片仍包含 posterity，和因為概念涵蓋仍然適用。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-124">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="e6fe4-125">裝置支援</span><span class="sxs-lookup"><span data-stu-id="e6fe4-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="e6fe4-126">課程</span><span class="sxs-lookup"><span data-stu-id="e6fe4-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="e6fe4-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="e6fe4-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="e6fe4-128"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="e6fe4-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="e6fe4-129">MR 輸入 211:手勢</span><span class="sxs-lookup"><span data-stu-id="e6fe4-129">MR Input 211: Gesture</span></span></td><td style="text-align: center;"> <span data-ttu-id="e6fe4-130">✔️</span><span class="sxs-lookup"><span data-stu-id="e6fe4-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="e6fe4-131">✔️</span><span class="sxs-lookup"><span data-stu-id="e6fe4-131">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="e6fe4-132">開始之前</span><span class="sxs-lookup"><span data-stu-id="e6fe4-132">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="e6fe4-133">先決條件</span><span class="sxs-lookup"><span data-stu-id="e6fe4-133">Prerequisites</span></span>

* <span data-ttu-id="e6fe4-134">Windows 10 電腦的正確設定[安裝工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-134">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="e6fe4-135">基本C#程式設計的能力。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-135">Some basic C# programming ability.</span></span>
* <span data-ttu-id="e6fe4-136">您應已完成[MR 基本概念 101](holograms-101.md)。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-136">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="e6fe4-137">您應已完成[MR 輸入 210](holograms-210.md)。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-137">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="e6fe4-138">HoloLens 裝置[開發設定的](using-visual-studio.md#enabling-developer-mode)。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-138">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="e6fe4-139">專案檔</span><span class="sxs-lookup"><span data-stu-id="e6fe4-139">Project files</span></span>

* <span data-ttu-id="e6fe4-140">下載[檔案](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip)專案所需。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-140">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) required by the project.</span></span><span data-ttu-id="e6fe4-141"> 需要 Unity 2017.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-141"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="e6fe4-142">取消封存您的桌面或其他您輕鬆地連線到位置的檔案。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="e6fe4-143">如果您想要查看原始程式碼，在下載之前，它有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture)。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="e6fe4-144">偵錯 errata 和附註</span><span class="sxs-lookup"><span data-stu-id="e6fe4-144">Errata and Notes</span></span>

* <span data-ttu-id="e6fe4-145">若要停用 啟用 Just My Code 的需求 (*未核取*) 在 Visual Studio 的 工具-> 選項-> 偵錯以程式碼中設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-145">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-0---unity-setup"></a><span data-ttu-id="e6fe4-146">第 0-Unity 安裝</span><span class="sxs-lookup"><span data-stu-id="e6fe4-146">Chapter 0 - Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="e6fe4-147">指示</span><span class="sxs-lookup"><span data-stu-id="e6fe4-147">Instructions</span></span>

1. <span data-ttu-id="e6fe4-148">啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-148">Start Unity.</span></span>
2. <span data-ttu-id="e6fe4-149">選取 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-149">Select **Open**.</span></span>
3. <span data-ttu-id="e6fe4-150">瀏覽至**筆勢**資料夾您先前未封存。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-150">Navigate to the **Gesture** folder you previously un-archived.</span></span>
4. <span data-ttu-id="e6fe4-151">尋找並選取**起始**/**模型總管**資料夾。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-151">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="e6fe4-152">按一下 [**選取資料夾**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-152">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="e6fe4-153">在 [**專案**] 面板中，展開**場景**資料夾。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-153">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="e6fe4-154">按兩下**ModelExplorer**載入在 Unity 中的場景。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-154">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="e6fe4-155">建置</span><span class="sxs-lookup"><span data-stu-id="e6fe4-155">Building</span></span>

1. <span data-ttu-id="e6fe4-156">在 Unity 中，選取**檔案 > 組建設定**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-156">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="e6fe4-157">如果**場景/ModelExplorer**中未列出**組建中的場景**，按一下 **加入開啟的場景**加入場景。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-157">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="e6fe4-158">如果您要特別開發的 HoloLens，設定**目標裝置**要**HoloLens**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-158">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="e6fe4-159">否則，將它保留在**任何裝置**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-159">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="e6fe4-160">確保**建置型別**設為**D3D**並**SDK**設定為**最新安裝**（這應該可以 16299 或更新版本的 SDK）。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-160">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="e6fe4-161">按一下 [建置] 。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-161">Click **Build**.</span></span>
6. <span data-ttu-id="e6fe4-162">建立**新的資料夾**名為 「 應用程式 」。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-162">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="e6fe4-163">只要按一下**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-163">Single click the **App** folder.</span></span>
8. <span data-ttu-id="e6fe4-164">按下**選取資料夾**，Unity 將會啟動 Visual studio 中建置專案。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-164">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="e6fe4-165">Unity 完成時，會出現檔案總管 視窗。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-165">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="e6fe4-166">開啟**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-166">Open the **App** folder.</span></span>
2. <span data-ttu-id="e6fe4-167">開啟**ModelExplorer Visual Studio 解決方案**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-167">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="e6fe4-168">如果將部署到 HoloLens:</span><span class="sxs-lookup"><span data-stu-id="e6fe4-168">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="e6fe4-169">使用頂端的工具列，在 Visual Studio 中，從 偵錯，若要變更目標**Release**進出至 ARM **x86**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-169">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="e6fe4-170">按一下下拉式清單 [本機電腦] 按鈕旁邊的箭號，然後選取**遠端機器**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-170">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="e6fe4-171">請輸入**HoloLens 裝置的 IP 位址**並將驗證模式設定為**通用 （未加密的通訊協定）**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-171">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="e6fe4-172">按一下 **選取**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-172">Click **Select**.</span></span> <span data-ttu-id="e6fe4-173">如果您不知道您的裝置 IP 位址，查看**設定 > 網路和網際網路 > 進階選項**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-173">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="e6fe4-174">在頂端功能表列中，按一下**偵錯]-> [啟動但不偵錯**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-174">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="e6fe4-175">如果這是第一次部署到您的裝置，您必須[與 Visual Studio 中配對](using-visual-studio.md#pairing-your-device-hololens)。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-175">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="e6fe4-176">當應用程式部署時，關閉**Fitbox**具有**選取 軌跡**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-176">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="e6fe4-177">如果將部署到擬真耳機：</span><span class="sxs-lookup"><span data-stu-id="e6fe4-177">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="e6fe4-178">使用頂端的工具列，在 Visual Studio 中，從 偵錯，若要變更目標**Release**進出至 ARM **x64**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-178">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="e6fe4-179">請確定部署目標設定為**本機電腦**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-179">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="e6fe4-180">在頂端功能表列中，按一下**偵錯]-> [啟動但不偵錯**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-180">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="e6fe4-181">當應用程式部署時，關閉**Fitbox**所提取的動作控制站上的觸發程序。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-181">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="e6fe4-182">您可能會注意到一些紅色的錯誤，在 Visual Studio 的 [錯誤] 面板。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-182">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="e6fe4-183">它可以安全地忽略它們。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-183">It is safe to ignore them.</span></span> <span data-ttu-id="e6fe4-184">切換至 [輸出] 面板，若要檢視實際組建進度。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-184">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="e6fe4-185">在 [輸出] 面板中的錯誤會要求您修正 （最常在指令碼中發生錯誤所造成）。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-185">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---hand-detected-feedback"></a><span data-ttu-id="e6fe4-186">第 1 章-手動偵測到的意見反應</span><span class="sxs-lookup"><span data-stu-id="e6fe4-186">Chapter 1 - Hand detected feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a><span data-ttu-id="e6fe4-187">目標</span><span class="sxs-lookup"><span data-stu-id="e6fe4-187">Objectives</span></span>

* <span data-ttu-id="e6fe4-188">訂閱交給追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-188">Subscribe to hand tracking events.</span></span>
* <span data-ttu-id="e6fe4-189">您可以使用資料指標的意見反應，正在追蹤手的形狀時，顯示使用者。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-189">Use cursor feedback to show users when a hand is being tracked.</span></span>

### <a name="instructions"></a><span data-ttu-id="e6fe4-190">指示</span><span class="sxs-lookup"><span data-stu-id="e6fe4-190">Instructions</span></span>

* <span data-ttu-id="e6fe4-191">在 [**階層**] 面板中，展開**InputManager**物件。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-191">In the **Hierarchy** panel, expand the **InputManager** object.</span></span>
* <span data-ttu-id="e6fe4-192">尋找並選取**GesturesInput**物件。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-192">Look for and select the **GesturesInput** object.</span></span>

<span data-ttu-id="e6fe4-193">**InteractionInputSource.cs**指令碼會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="e6fe4-193">The **InteractionInputSource.cs** script performs these steps:</span></span>

1. <span data-ttu-id="e6fe4-194">訂閱 InteractionSourceDetected 和 InteractionSourceLost 事件。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-194">Subscribes to the InteractionSourceDetected and InteractionSourceLost events.</span></span>
2. <span data-ttu-id="e6fe4-195">設定 HandDetected 狀態。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-195">Sets the HandDetected state.</span></span>
3. <span data-ttu-id="e6fe4-196">從 InteractionSourceDetected 和 InteractionSourceLost 事件取消訂閱。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-196">Unsubscribes from the InteractionSourceDetected and InteractionSourceLost events.</span></span>

<span data-ttu-id="e6fe4-197">接下來，我們將升級從資料指標[MR 輸入 210](holograms-210.md)成一個顯示意見反應，視使用者的動作而定。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-197">Next, we'll upgrade our cursor from [MR Input 210](holograms-210.md) into one that shows feedback depending on the user's actions.</span></span>

1. <span data-ttu-id="e6fe4-198">在 **階層**面板中，選取**游標**物件，並將它刪除。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-198">In the **Hierarchy** panel, select the **Cursor** object and delete it.</span></span>
2. <span data-ttu-id="e6fe4-199">在 [**專案**] 面板中，搜尋**CursorWithFeedback**並將它拖曳到**階層**面板。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-199">In the **Project** panel, search for **CursorWithFeedback** and drag it into the **Hierarchy** panel.</span></span>
3. <span data-ttu-id="e6fe4-200">按一下 [ **InputManager**中**階層**] 面板，然後以拖曳方式**CursorWithFeedback**物件**階層**到InputManager 的**SimpleSinglePointerSelector**的**游標**欄位中，在底部**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-200">Click on **InputManager** in the **Hierarchy** panel, then drag the **CursorWithFeedback** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>
4. <span data-ttu-id="e6fe4-201">按一下  **CursorWithFeedback**中**階層**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-201">Click on the **CursorWithFeedback** in the **Hierarchy**.</span></span>
5. <span data-ttu-id="e6fe4-202">在**Inspector**  面板中，展開**游標狀態資料**上**物件的資料指標**指令碼。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-202">In the **Inspector** panel, expand **Cursor State Data** on the **Object Cursor** script.</span></span>

<span data-ttu-id="e6fe4-203">**資料指標狀態資料**運作方式如下所示：</span><span class="sxs-lookup"><span data-stu-id="e6fe4-203">The **Cursor State Data** works like this:</span></span>

* <span data-ttu-id="e6fe4-204">任何**觀察**狀態表示沒有手動偵測到並四處只尋找使用者。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-204">Any **Observe** state means that no hand is detected and the user is simply looking around.</span></span>
* <span data-ttu-id="e6fe4-205">任何**Interact**手形或控制站會偵測到的狀態表示。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-205">Any **Interact** state means that a hand or controller is detected.</span></span>
* <span data-ttu-id="e6fe4-206">任何**暫留**狀態表示使用者查看雷射。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-206">Any **Hover** state means the user is looking at a hologram.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="e6fe4-207">建置和部署</span><span class="sxs-lookup"><span data-stu-id="e6fe4-207">Build and Deploy</span></span>

* <span data-ttu-id="e6fe4-208">在 Unity 中，使用**檔案 > 組建設定**重建應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-208">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="e6fe4-209">開啟**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-209">Open the **App** folder.</span></span>
* <span data-ttu-id="e6fe4-210">如果它尚未開啟，開啟**ModelExplorer Visual Studio 方案**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-210">If it's not already open, open the **ModelExplorer Visual Studio Solution**.</span></span>
  * <span data-ttu-id="e6fe4-211">（如果您已經建置/部署此專案在 Visual Studio 設定期間，然後您可以開啟 VS 執行個體並按一下 [重新載入全部] 出現提示時）。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-211">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>
* <span data-ttu-id="e6fe4-212">在 Visual Studio 中，按一下**偵錯]-> [啟動但不偵錯**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-212">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="e6fe4-213">應用程式部署到 HoloLens 之後，關閉使用空中點選手勢 fitbox。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-213">After the application deploys to the HoloLens, dismiss the fitbox using the air-tap gesture.</span></span>
* <span data-ttu-id="e6fe4-214">將您的手才移至 檢視和食指指向天空啟動手動追蹤。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-214">Move your hand into view and point your index finger to the sky to start hand tracking.</span></span>
* <span data-ttu-id="e6fe4-215">移動您的手左、 右、 向上和向下。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-215">Move your hand left, right, up and down.</span></span>
* <span data-ttu-id="e6fe4-216">觀看如何，游標會變成手上已偵測到，再從檢視遺失時。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-216">Watch how the cursor changes when your hand is detected and then lost from view.</span></span>
* <span data-ttu-id="e6fe4-217">如果您所在的沈浸式耳機時，您必須連接或中斷連接您的控制器。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-217">If you're on an immersive headset, you'll have to connect and disconnect your controller.</span></span> <span data-ttu-id="e6fe4-218">連接的控制器一律是 「 可用 」 時，此意見反應會變得較不有趣沈浸式裝置。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-218">This feedback becomes less interesting on an immersive device, as a connected controller will always be "available".</span></span>

## <a name="chapter-2---navigation"></a><span data-ttu-id="e6fe4-219">第 2 章-瀏覽</span><span class="sxs-lookup"><span data-stu-id="e6fe4-219">Chapter 2 - Navigation</span></span>

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a><span data-ttu-id="e6fe4-220">目標</span><span class="sxs-lookup"><span data-stu-id="e6fe4-220">Objectives</span></span>

* <span data-ttu-id="e6fe4-221">您可以使用 瀏覽軌跡事件來旋轉太空人。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-221">Use Navigation gesture events to rotate the astronaut.</span></span>

### <a name="instructions"></a><span data-ttu-id="e6fe4-222">指示</span><span class="sxs-lookup"><span data-stu-id="e6fe4-222">Instructions</span></span>

<span data-ttu-id="e6fe4-223">若要使用軌跡瀏覽我們的應用程式中，我們將編輯**GestureAction.cs**時瀏覽鍵筆勢，就會發生旋轉物件。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-223">To use Navigation gestures in our app, we are going to edit **GestureAction.cs** to rotate objects when the Navigation gesture occurs.</span></span> <span data-ttu-id="e6fe4-224">此外，我們將新增意見反應，來瀏覽可用時，所顯示的游標。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-224">Additionally, we'll add feedback to the cursor to display when Navigation is available.</span></span>

1. <span data-ttu-id="e6fe4-225">在 [**階層**] 面板中，展開**CursorWithFeedback**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-225">In the **Hierarchy** panel, expand **CursorWithFeedback**.</span></span>
2. <span data-ttu-id="e6fe4-226">在 **全像投影**資料夾中，尋找**ScrollFeedback**資產。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-226">In the **Holograms** folder, find the **ScrollFeedback** asset.</span></span>
3. <span data-ttu-id="e6fe4-227">將拖放**ScrollFeedback**拖曳至 prefab **CursorWithFeedback**中的 GameObject**階層**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-227">Drag and drop the **ScrollFeedback** prefab onto the **CursorWithFeedback** GameObject in the **Hierarchy**.</span></span>
4. <span data-ttu-id="e6fe4-228">按一下  **CursorWithFeedback**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-228">Click on **CursorWithFeedback**.</span></span>
5. <span data-ttu-id="e6fe4-229">在  **Inspector**  面板中，按一下**新增元件** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-229">In the **Inspector** panel, click the **Add Component** button.</span></span>
6. <span data-ttu-id="e6fe4-230">在功能表中，輸入在搜尋方塊**CursorFeedback**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-230">In the menu, type in the search box **CursorFeedback**.</span></span> <span data-ttu-id="e6fe4-231">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-231">Select the search result.</span></span>
7. <span data-ttu-id="e6fe4-232">將拖放**ScrollFeedback**物件**階層**拖曳至**捲動偵測到的遊戲物件**中的屬性**資料指標的意見反應**元件**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-232">Drag and drop the **ScrollFeedback** object from the **Hierarchy** onto the **Scroll Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>
8. <span data-ttu-id="e6fe4-233">在 **階層**面板中，選取**AstroMan**物件。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-233">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
9. <span data-ttu-id="e6fe4-234">在  **Inspector**  面板中，按一下**新增元件** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-234">In the **Inspector** panel, click the **Add Component** button.</span></span>
10. <span data-ttu-id="e6fe4-235">在功能表中，輸入在搜尋方塊**手勢動作**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-235">In the menu, type in the search box **Gesture Action**.</span></span> <span data-ttu-id="e6fe4-236">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-236">Select the search result.</span></span>

<span data-ttu-id="e6fe4-237">接下來，開啟**GestureAction.cs** Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-237">Next, open **GestureAction.cs** in Visual Studio.</span></span> <span data-ttu-id="e6fe4-238">在撰寫程式碼練習 2.c，編輯指令碼，執行下列操作：</span><span class="sxs-lookup"><span data-stu-id="e6fe4-238">In coding exercise 2.c, edit the script to do the following:</span></span>

1. <span data-ttu-id="e6fe4-239">**旋轉 AstroMan**物件每當執行瀏覽動作時。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-239">**Rotate the AstroMan** object whenever a Navigation gesture is performed.</span></span>
2. <span data-ttu-id="e6fe4-240">計算**rotationFactor**來控制旋轉套用至物件的大小。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-240">Calculate the **rotationFactor** to control the amount of rotation applied to the object.</span></span>
3. <span data-ttu-id="e6fe4-241">**旋轉物件**繞 y 軸，當使用者將其手動左邊或右邊。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-241">**Rotate the object** around the y-axis when the user moves their hand left or right.</span></span>

<span data-ttu-id="e6fe4-242">完整的程式碼撰寫練習 2.c 指令碼或取代已完成的解決方案使用的程式碼中：</span><span class="sxs-lookup"><span data-stu-id="e6fe4-242">Complete coding exercises 2.c in the script, or replace the code with the completed solution below:</span></span>

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

<span data-ttu-id="e6fe4-243">您會發現其他瀏覽事件已經會填入部分資訊。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-243">You'll notice that the other navigation events are already filled in with some info.</span></span> <span data-ttu-id="e6fe4-244">我們將推送到此工具組的 GameObject InputSystem 的強制回應堆疊，因此使用者不需要專注在太空人一旦開始旋轉。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-244">We push the GameObject onto the Toolkit's InputSystem's modal stack, so the user doesn't have to maintain focus on the Astronaut once rotation has begun.</span></span> <span data-ttu-id="e6fe4-245">同樣地，我們顯示堆疊中取出 GameObject 完成筆勢。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-245">Correspondingly, we pop the GameObject off the stack once the gesture is completed.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="e6fe4-246">建置和部署</span><span class="sxs-lookup"><span data-stu-id="e6fe4-246">Build and Deploy</span></span>

1. <span data-ttu-id="e6fe4-247">重建 Unity 中的應用程式，然後建置並部署從執行中的 HoloLens 的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-247">Rebuild the application in Unity and then build and deploy from Visual Studio to run it in the HoloLens.</span></span>
2. <span data-ttu-id="e6fe4-248">注視太空人，兩個箭號應該會出現在左邊或右邊的資料指標。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-248">Gaze at the astronaut, two arrows should appear on either side of the cursor.</span></span> <span data-ttu-id="e6fe4-249">這個新的視覺效果指示太空人可以被輪替。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-249">This new visual indicates that the astronaut can be rotated.</span></span>
3. <span data-ttu-id="e6fe4-250">將手放在準備好的位置 （食指指向天空） 讓 HoloLens 會開始追蹤您的手。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-250">Place your hand in the ready position (index finger pointed towards the sky) so the HoloLens will start tracking your hand.</span></span>
4. <span data-ttu-id="e6fe4-251">若要輪替太空人，降低食指到縮小的位置，然後再移手左邊或右邊觸發 NavigationX 筆勢。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-251">To rotate the astronaut, lower your index finger to a pinch position, and then move your hand left or right to trigger the NavigationX gesture.</span></span>

## <a name="chapter-3---hand-guidance"></a><span data-ttu-id="e6fe4-252">第 3 章-手動指引</span><span class="sxs-lookup"><span data-stu-id="e6fe4-252">Chapter 3 - Hand Guidance</span></span>

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a><span data-ttu-id="e6fe4-253">目標</span><span class="sxs-lookup"><span data-stu-id="e6fe4-253">Objectives</span></span>

* <span data-ttu-id="e6fe4-254">使用**交給指引分數**協助預測時，手動追蹤將會遺失。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-254">Use **hand guidance score** to help predict when hand tracking will be lost.</span></span>
* <span data-ttu-id="e6fe4-255">提供**意見反應游標**顯示當使用者的手接近檢視的相機的邊緣。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-255">Provide **feedback on the cursor** to show when the user's hand nears the camera's edge of view.</span></span>

### <a name="instructions"></a><span data-ttu-id="e6fe4-256">指示</span><span class="sxs-lookup"><span data-stu-id="e6fe4-256">Instructions</span></span>

1. <span data-ttu-id="e6fe4-257">在 **階層**面板中，選取**CursorWithFeedback**物件。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-257">In the **Hierarchy** panel, select the **CursorWithFeedback** object.</span></span>
2. <span data-ttu-id="e6fe4-258">在  **Inspector**  面板中，按一下**新增元件** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-258">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="e6fe4-259">在功能表中，輸入在搜尋方塊**手指引**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-259">In the menu, type in the search box **Hand Guidance**.</span></span> <span data-ttu-id="e6fe4-260">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-260">Select the search result.</span></span>
4. <span data-ttu-id="e6fe4-261">在 **專案**面板**全像投影**資料夾中，尋找**HandGuidanceFeedback**資產。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-261">In the **Project** panel **Holograms** folder, find the **HandGuidanceFeedback** asset.</span></span>
5. <span data-ttu-id="e6fe4-262">將拖放**HandGuidanceFeedback**拖曳至資產**手指引指標**中的屬性**Inspector**面板。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-262">Drag and drop the **HandGuidanceFeedback** asset onto the **Hand Guidance Indicator** property in the **Inspector** panel.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="e6fe4-263">建置和部署</span><span class="sxs-lookup"><span data-stu-id="e6fe4-263">Build and Deploy</span></span>

* <span data-ttu-id="e6fe4-264">重建 Unity 中的應用程式然後建置並從 Visual Studio 體驗 HoloLens 上的應用程式部署。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-264">Rebuild the application in Unity and then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="e6fe4-265">您的手帶入檢視，並引發食指取得追蹤。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-265">Bring your hand into view and raise your index finger to get tracked.</span></span>
* <span data-ttu-id="e6fe4-266">開始輪替與瀏覽筆勢太空人 （縮小食指和 thumb 一起）。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-266">Start rotating the astronaut with the Navigation gesture (pinch your index finger and thumb together).</span></span>
* <span data-ttu-id="e6fe4-267">最左邊，以滑鼠右鍵，，向上和向下，請移動您的手。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-267">Move your hand far left, right, up, and down.</span></span>
* <span data-ttu-id="e6fe4-268">因為您的手接近筆勢框架邊緣，應該旁出現的箭號來警告您該追蹤的手狀游標將會遺失。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-268">As your hand nears the edge of the gesture frame, an arrow should appear next to the cursor to warn you that hand tracking will be lost.</span></span> <span data-ttu-id="e6fe4-269">箭號表示的方向，以避免遺失追蹤移動您的手。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-269">The arrow indicates which direction to move your hand in order to prevent tracking from being lost.</span></span>

## <a name="chapter-4---manipulation"></a><span data-ttu-id="e6fe4-270">第 4 章-操作</span><span class="sxs-lookup"><span data-stu-id="e6fe4-270">Chapter 4 - Manipulation</span></span>

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a><span data-ttu-id="e6fe4-271">目標</span><span class="sxs-lookup"><span data-stu-id="e6fe4-271">Objectives</span></span>

* <span data-ttu-id="e6fe4-272">若要移動雙手太空人使用操作事件。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-272">Use Manipulation events to move the astronaut with your hands.</span></span>
* <span data-ttu-id="e6fe4-273">若要讓使用者知道可以使用操作時資料指標上提供意見反應。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-273">Provide feedback on the cursor to let the user know when Manipulation can be used.</span></span>

### <a name="instructions"></a><span data-ttu-id="e6fe4-274">指示</span><span class="sxs-lookup"><span data-stu-id="e6fe4-274">Instructions</span></span>

<span data-ttu-id="e6fe4-275">GestureManager.cs 和 AstronautManager.cs 可讓我們執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="e6fe4-275">GestureManager.cs and AstronautManager.cs will allow us to do the following:</span></span>

1. <span data-ttu-id="e6fe4-276">使用語音關鍵字"**移動太空人**「 若要啟用**操作**筆勢和 「**旋轉太空人**"停用它們。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-276">Use the speech keyword "**Move Astronaut**" to enable **Manipulation** gestures and "**Rotate Astronaut**" to disable them.</span></span>
2. <span data-ttu-id="e6fe4-277">切換至回應**操作筆勢辨識器**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-277">Switch to responding to the **Manipulation Gesture Recognizer**.</span></span>

<span data-ttu-id="e6fe4-278">那就開始吧。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-278">Let's get started.</span></span>

1. <span data-ttu-id="e6fe4-279">在 [**階層**] 面板中，建立新的空 GameObject。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-279">In the **Hierarchy** panel, create a new empty GameObject.</span></span> <span data-ttu-id="e6fe4-280">它命名為"**AstronautManager**"。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-280">Name it "**AstronautManager**".</span></span>
2. <span data-ttu-id="e6fe4-281">在  **Inspector**  面板中，按一下**新增元件** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-281">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="e6fe4-282">在功能表中，輸入在搜尋方塊**太空人 Manager**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-282">In the menu, type in the search box **Astronaut Manager**.</span></span> <span data-ttu-id="e6fe4-283">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-283">Select the search result.</span></span>
4. <span data-ttu-id="e6fe4-284">在  **Inspector**  面板中，按一下**新增元件** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
5. <span data-ttu-id="e6fe4-285">在功能表中，輸入在搜尋方塊**語音輸入來源**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-285">In the menu, type in the search box **Speech Input Source**.</span></span> <span data-ttu-id="e6fe4-286">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-286">Select the search result.</span></span>

<span data-ttu-id="e6fe4-287">現在，我們要加入控制太空人互動狀態所需的語音命令。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-287">We'll now add the speech commands required to control the interaction state of the astronaut.</span></span>

1. <span data-ttu-id="e6fe4-288">依序展開**關鍵字**一節**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-288">Expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="e6fe4-289">按一下  **+** 右邊加入新的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-289">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="e6fe4-290">類型為關鍵字**移動太空人**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-290">Type the Keyword as **Move Astronaut**.</span></span> <span data-ttu-id="e6fe4-291">歡迎加入索引鍵的快顯，如有需要。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-291">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="e6fe4-292">按一下  **+** 右邊加入新的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-292">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="e6fe4-293">類型為關鍵字**旋轉太空人**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-293">Type the Keyword as **Rotate Astronaut**.</span></span> <span data-ttu-id="e6fe4-294">歡迎加入索引鍵的快顯，如有需要。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-294">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="e6fe4-295">對應的處理常式程式碼可在**GestureAction.cs**，請在**ISpeechHandler.OnSpeechKeywordRecognized**處理常式。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-295">The corresponding handler code can be found in **GestureAction.cs**, in the **ISpeechHandler.OnSpeechKeywordRecognized** handler.</span></span>

![如何設定第 4 章語音輸入來源](images/holograms211-speech.png)

<span data-ttu-id="e6fe4-297">接下來，我們將設定資料指標上的操作意見反應。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-297">Next, we'll setup the manipulation feedback on the cursor.</span></span>

1. <span data-ttu-id="e6fe4-298">在 **專案**面板**全像投影**資料夾中，尋找**PathingFeedback**資產。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-298">In the **Project** panel **Holograms** folder, find the **PathingFeedback** asset.</span></span>
2. <span data-ttu-id="e6fe4-299">將拖放**PathingFeedback**拖曳至 prefab **CursorWithFeedback**物件**階層**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-299">Drag and drop the **PathingFeedback** prefab onto the **CursorWithFeedback** object in the **Hierarchy**.</span></span>
3. <span data-ttu-id="e6fe4-300">在 [**階層**] 面板中，按一下**CursorWithFeedback**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-300">In the **Hierarchy** panel, click on **CursorWithFeedback**.</span></span>
4. <span data-ttu-id="e6fe4-301">將拖放**PathingFeedback**物件**階層**拖曳至**路徑偵測到的遊戲物件**中的屬性**資料指標的意見反應**元件**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-301">Drag and drop the **PathingFeedback** object from the **Hierarchy** onto the **Pathing Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>

<span data-ttu-id="e6fe4-302">現在我們要將程式碼加入**GestureAction.cs**以啟用下列：</span><span class="sxs-lookup"><span data-stu-id="e6fe4-302">Now we need to add code to **GestureAction.cs** to enable the following:</span></span>

1. <span data-ttu-id="e6fe4-303">將程式碼加入**IManipulationHandler.OnManipulationUpdated**函式，會移動太空人時**操作**偵測到筆勢時。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-303">Add code to the **IManipulationHandler.OnManipulationUpdated** function, which will move the astronaut when a **Manipulation** gesture is detected.</span></span>
2. <span data-ttu-id="e6fe4-304">計算**移動向量**來判斷應該太空人移到基底的庫存位置。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-304">Calculate the **movement vector** to determine where the astronaut should be moved to based on hand position.</span></span>
3. <span data-ttu-id="e6fe4-305">**移動**太空人移動至新位置。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-305">**Move** the astronaut to the new position.</span></span>

<span data-ttu-id="e6fe4-306">完整的程式碼撰寫練習在 4.a **GestureAction.cs**，或使用我們已完成的解決方案下方：</span><span class="sxs-lookup"><span data-stu-id="e6fe4-306">Complete coding exercise 4.a in **GestureAction.cs**, or use our completed solution below:</span></span>

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a><span data-ttu-id="e6fe4-307">建置和部署</span><span class="sxs-lookup"><span data-stu-id="e6fe4-307">Build and Deploy</span></span>

* <span data-ttu-id="e6fe4-308">在 Unity 中重建然後建置並部署從執行中 HoloLens 的應用程式的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-308">Rebuild in Unity and then build and deploy from Visual Studio to run the app in HoloLens.</span></span>
* <span data-ttu-id="e6fe4-309">移動手 HoloLens 前方，並引發食指，以便可以追蹤。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-309">Move your hand in front of the HoloLens and raise your index finger so that it can be tracked.</span></span>
* <span data-ttu-id="e6fe4-310">透過太空人著重資料指標。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-310">Focus the cursor over the astronaut.</span></span>
* <span data-ttu-id="e6fe4-311">假設要移動與操作筆勢太空人的 ' 移動太空人 '。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-311">Say 'Move Astronaut' to move the astronaut with a Manipulation gesture.</span></span>
* <span data-ttu-id="e6fe4-312">四個箭號應否顯示資料指標來表示程式會立即回應操作事件。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-312">Four arrows should appear around the cursor to indicate that the program will now respond to Manipulation events.</span></span>
* <span data-ttu-id="e6fe4-313">降低食指向您捲動方塊中，並讓他們一起 pinched。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-313">Lower your index finger down to your thumb, and keep them pinched together.</span></span>
* <span data-ttu-id="e6fe4-314">當您移動您的手周圍，也會跟著移動太空人 （這是操作）。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-314">As you move your hand around, the astronaut will move too (this is Manipulation).</span></span>
* <span data-ttu-id="e6fe4-315">引發食指停止操作太空人。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-315">Raise your index finger to stop manipulating the astronaut.</span></span>
* <span data-ttu-id="e6fe4-316">注意：如果移動您的手之前不假設移動太空人然後瀏覽軌跡將會改用。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-316">Note: If you do not say 'Move Astronaut' before moving your hand, then the Navigation gesture will be used instead.</span></span>
* <span data-ttu-id="e6fe4-317">假設 '旋轉太空人' 回到座艙的狀態。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-317">Say 'Rotate Astronaut' to return to the rotatable state.</span></span>

## <a name="chapter-5---model-expansion"></a><span data-ttu-id="e6fe4-318">第 5 章-模型擴充</span><span class="sxs-lookup"><span data-stu-id="e6fe4-318">Chapter 5 - Model expansion</span></span>

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a><span data-ttu-id="e6fe4-319">目標</span><span class="sxs-lookup"><span data-stu-id="e6fe4-319">Objectives</span></span>

* <span data-ttu-id="e6fe4-320">展開太空人模型分成多個、 較小組件的使用者可以與互動。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-320">Expand the Astronaut model into multiple, smaller pieces that the user can interact with.</span></span>
* <span data-ttu-id="e6fe4-321">移動使用個別的軌跡瀏覽和操作每個片段。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-321">Move each piece individually using Navigation and Manipulation gestures.</span></span>

### <a name="instructions"></a><span data-ttu-id="e6fe4-322">指示</span><span class="sxs-lookup"><span data-stu-id="e6fe4-322">Instructions</span></span>

<span data-ttu-id="e6fe4-323">在本節中，我們將完成下列工作：</span><span class="sxs-lookup"><span data-stu-id="e6fe4-323">In this section, we will accomplish the following tasks:</span></span>

1. <span data-ttu-id="e6fe4-324">加入新的關鍵字 「**展開模型**"展開太空人模型。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-324">Add a new keyword "**Expand Model**" to expand the astronaut model.</span></span>
2. <span data-ttu-id="e6fe4-325">加入新的關鍵字 「**重設的模型**"以返回其原始形式的模型。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-325">Add a new Keyword "**Reset Model**" to return the model to its original form.</span></span>

<span data-ttu-id="e6fe4-326">我們會加入語音輸入來源中的兩個的多個關鍵字，從上一章。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-326">We'll do this by adding two more keywords to the Speech Input Source from the previous chapter.</span></span> <span data-ttu-id="e6fe4-327">我們也將示範另一種方式來處理辨識的事件。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-327">We'll also demonstrate another way to handle recognition events.</span></span>

1. <span data-ttu-id="e6fe4-328">按一下 上一步**AstronautManager**中**Inspector**展開**關鍵字**一節中**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-328">Click back on **AstronautManager** in the **Inspector** and expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="e6fe4-329">按一下  **+** 右邊加入新的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-329">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="e6fe4-330">類型為關鍵字**展開模型**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-330">Type the Keyword as **Expand Model**.</span></span> <span data-ttu-id="e6fe4-331">歡迎加入索引鍵的快顯，如有需要。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-331">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="e6fe4-332">按一下  **+** 右邊加入新的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-332">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="e6fe4-333">類型為關鍵字**重設模型**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-333">Type the Keyword as **Reset Model**.</span></span> <span data-ttu-id="e6fe4-334">歡迎加入索引鍵的快顯，如有需要。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-334">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="e6fe4-335">在  **Inspector**  面板中，按一下**新增元件** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-335">In the **Inspector** panel, click the **Add Component** button.</span></span>
7. <span data-ttu-id="e6fe4-336">在功能表中，輸入在搜尋方塊**語音輸入處理常式**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-336">In the menu, type in the search box **Speech Input Handler**.</span></span> <span data-ttu-id="e6fe4-337">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-337">Select the search result.</span></span>
8. <span data-ttu-id="e6fe4-338">請檢查**是全域的接聽程式**，因為我們希望我們著重這些命令不受限於 GameObject。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-338">Check **Is Global Listener**, since we want these commands to work regardless of the GameObject we're focusing.</span></span>
9. <span data-ttu-id="e6fe4-339">按一下  **+** 按鈕，然後選取**展開模型**關鍵字下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-339">Click the **+** button and select **Expand Model** from the Keyword dropdown.</span></span>
10. <span data-ttu-id="e6fe4-340">按一下  **+** 下的回應，並將拖曳**AstronautManager**從**階層**到**None （物件）** 欄位。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-340">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
11. <span data-ttu-id="e6fe4-341">現在，按一下  **No 函式**下拉式清單中，選取**AstronautManager**，然後**ExpandModelCommand**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-341">Now, click the **No Function** dropdown, select **AstronautManager**, then **ExpandModelCommand**.</span></span>
12. <span data-ttu-id="e6fe4-342">按一下 語音輸入處理常式**+** 按鈕，然後選取**重設的模型**關鍵字下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-342">Click the Speech Input Handler's **+** button and select **Reset Model** from the Keyword dropdown.</span></span>
13. <span data-ttu-id="e6fe4-343">按一下  **+** 下的回應，並將拖曳**AstronautManager**從**階層**到**None （物件）** 欄位。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-343">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
14. <span data-ttu-id="e6fe4-344">現在，按一下  **No 函式**下拉式清單中，選取**AstronautManager**，然後**ResetModelCommand**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-344">Now, click the **No Function** dropdown, select **AstronautManager**, then **ResetModelCommand**.</span></span>

![如何設定語音輸入來源和處理常式的第 5 章](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a><span data-ttu-id="e6fe4-346">建置和部署</span><span class="sxs-lookup"><span data-stu-id="e6fe4-346">Build and Deploy</span></span>

* <span data-ttu-id="e6fe4-347">試試看！</span><span class="sxs-lookup"><span data-stu-id="e6fe4-347">Try it!</span></span> <span data-ttu-id="e6fe4-348">建置並部署到 HoloLens 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-348">Build and deploy the app to the HoloLens.</span></span>
* <span data-ttu-id="e6fe4-349">假設**展開模型**來查看展開的太空人模型。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-349">Say **Expand Model** to see the expanded astronaut model.</span></span>
* <span data-ttu-id="e6fe4-350">使用**瀏覽**旋轉太空人花色的各個部分。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-350">Use **Navigation** to rotate individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="e6fe4-351">假設**移動太空人**，然後使用**操作**移動太空人花色的各個部分。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-351">Say **Move Astronaut** and then use **Manipulation** to move individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="e6fe4-352">假設**旋轉太空人**再次旋轉項目。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-352">Say **Rotate Astronaut** to rotate the pieces again.</span></span>
* <span data-ttu-id="e6fe4-353">假設**重設的模型**太空人返回其原始形式。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-353">Say **Reset Model** to return the astronaut to its original form.</span></span>

## <a name="the-end"></a><span data-ttu-id="e6fe4-354">結束</span><span class="sxs-lookup"><span data-stu-id="e6fe4-354">The End</span></span>

<span data-ttu-id="e6fe4-355">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="e6fe4-355">Congratulations!</span></span> <span data-ttu-id="e6fe4-356">您現在已完成**MR 輸入 211:筆勢**。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-356">You have now completed **MR Input 211: Gesture**.</span></span>

* <span data-ttu-id="e6fe4-357">您知道如何偵測和回應交給追蹤、 瀏覽和操作事件。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-357">You know how to detect and respond to hand tracking, navigation and manipulation events.</span></span>
* <span data-ttu-id="e6fe4-358">您了解瀏覽和操作筆勢之間的差異。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-358">You understand the difference between Navigation and Manipulation gestures.</span></span>
* <span data-ttu-id="e6fe4-359">您知道如何變更資料指標來手動偵測到時，會遺失，手的形狀時以及當物件支援不同的互動 （瀏覽與操作） 提供視覺化回饋。</span><span class="sxs-lookup"><span data-stu-id="e6fe4-359">You know how to change the cursor to provide visual feedback for when a hand is detected, when a hand is about to be lost, and for when an object supports different interactions (Navigation vs Manipulation).</span></span>
