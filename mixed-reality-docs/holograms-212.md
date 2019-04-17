---
title: MR 輸入 212-語音
description: 請遵循此程式碼撰寫的逐步解說，使用 Unity、 Visual Studio 和 HoloLens，若要了解語音概念的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、 mixedrealitytoolkit、 mixedrealitytoolkit unity、 academy、 教學課程中，語音
ms.openlocfilehash: 7e792bf40c47d4e1d57898fbe75ad050a030b7e3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591403"
---
>[!NOTE]
><span data-ttu-id="5d053-104">混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。</span><span class="sxs-lookup"><span data-stu-id="5d053-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="5d053-105">因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。</span><span class="sxs-lookup"><span data-stu-id="5d053-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="5d053-106">這些教學課程會**_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="5d053-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="5d053-107">它們會繼續運作，支援的裝置上維護。</span><span class="sxs-lookup"><span data-stu-id="5d053-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="5d053-108">會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="5d053-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="5d053-109">當他們回傳時，本聲明將會更新這些教學課程的連結。</span><span class="sxs-lookup"><span data-stu-id="5d053-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-input-212-voice"></a><span data-ttu-id="5d053-110">MR 輸入 212:語音</span><span class="sxs-lookup"><span data-stu-id="5d053-110">MR Input 212: Voice</span></span>

<span data-ttu-id="5d053-111">[語音輸入](voice-input.md)提供另一種方式與我們全像投影互動。</span><span class="sxs-lookup"><span data-stu-id="5d053-111">[Voice input](voice-input.md) gives us another way to interact with our holograms.</span></span> <span data-ttu-id="5d053-112">語音命令運作非常自然且簡單的方式。</span><span class="sxs-lookup"><span data-stu-id="5d053-112">Voice commands work in a very natural and easy way.</span></span> <span data-ttu-id="5d053-113">設計您的語音命令，使它們：</span><span class="sxs-lookup"><span data-stu-id="5d053-113">Design your voice commands so that they are:</span></span>

* <span data-ttu-id="5d053-114">自然</span><span class="sxs-lookup"><span data-stu-id="5d053-114">Natural</span></span>
* <span data-ttu-id="5d053-115">容易記憶</span><span class="sxs-lookup"><span data-stu-id="5d053-115">Easy to remember</span></span>
* <span data-ttu-id="5d053-116">適當的內容</span><span class="sxs-lookup"><span data-stu-id="5d053-116">Context appropriate</span></span>
* <span data-ttu-id="5d053-117">足以區別相同內容中的其他選項</span><span class="sxs-lookup"><span data-stu-id="5d053-117">Sufficiently distinct from other options within the same context</span></span>

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

<span data-ttu-id="5d053-118">在  [MR 基本概念 101](holograms-101.md)，我們用 KeywordRecognizer 來建置兩個簡單的語音命令。</span><span class="sxs-lookup"><span data-stu-id="5d053-118">In [MR Basics 101](holograms-101.md), we used the KeywordRecognizer to build two simple voice commands.</span></span> <span data-ttu-id="5d053-119">在 MR 輸入 212，我們將更深入了解，並了解如何：</span><span class="sxs-lookup"><span data-stu-id="5d053-119">In MR Input 212, we'll dive deeper and learn how to:</span></span>

* <span data-ttu-id="5d053-120">設計最適合用於 HoloLens 語音引擎的語音命令。</span><span class="sxs-lookup"><span data-stu-id="5d053-120">Design voice commands that are optimized for the HoloLens speech engine.</span></span>
* <span data-ttu-id="5d053-121">讓使用者知道哪些語音命令的可用。</span><span class="sxs-lookup"><span data-stu-id="5d053-121">Make the user aware of what voice commands are available.</span></span>
* <span data-ttu-id="5d053-122">了解，我們得知使用者的語音命令。</span><span class="sxs-lookup"><span data-stu-id="5d053-122">Acknowledge that we've heard the user's voice command.</span></span>
* <span data-ttu-id="5d053-123">了解使用者的是誰說，使用聽寫辨識器。</span><span class="sxs-lookup"><span data-stu-id="5d053-123">Understand what the user is saying, using a Dictation Recognizer.</span></span>
* <span data-ttu-id="5d053-124">使用文法辨識器接聽 SRGS 或語音辨識文法規格，檔案為基礎的命令。</span><span class="sxs-lookup"><span data-stu-id="5d053-124">Use a Grammar Recognizer to listen for commands based on an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

<span data-ttu-id="5d053-125">在此課程中，我們再探討模型總管 中，我們在建置[MR 輸入 210](holograms-210.md)並[MR 輸入 211](holograms-211.md)。</span><span class="sxs-lookup"><span data-stu-id="5d053-125">In this course, we'll revisit Model Explorer, which we built in [MR Input 210](holograms-210.md) and [MR Input 211](holograms-211.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="5d053-126">使用 Unity 及混合實境 toolkit 的推出較舊的版本記錄中的下列章節的每個內嵌的影片。</span><span class="sxs-lookup"><span data-stu-id="5d053-126">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="5d053-127">雖然的逐步指示是準確且即時的您可能會看到指令碼和對應已過期的影片中的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="5d053-127">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="5d053-128">影片仍包含 posterity，和因為概念涵蓋仍然適用。</span><span class="sxs-lookup"><span data-stu-id="5d053-128">The videos remain included for posterity and because the concepts covered still apply.</span></span>


## <a name="device-support"></a><span data-ttu-id="5d053-129">裝置支援</span><span class="sxs-lookup"><span data-stu-id="5d053-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="5d053-130">課程</span><span class="sxs-lookup"><span data-stu-id="5d053-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="5d053-131"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="5d053-131"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="5d053-132"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="5d053-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="5d053-133">MR 輸入 212:語音</span><span class="sxs-lookup"><span data-stu-id="5d053-133">MR Input 212: Voice</span></span></td><td style="text-align: center;"> <span data-ttu-id="5d053-134">✔️</span><span class="sxs-lookup"><span data-stu-id="5d053-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="5d053-135">✔️</span><span class="sxs-lookup"><span data-stu-id="5d053-135">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="5d053-136">開始之前</span><span class="sxs-lookup"><span data-stu-id="5d053-136">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="5d053-137">必要條件</span><span class="sxs-lookup"><span data-stu-id="5d053-137">Prerequisites</span></span>

* <span data-ttu-id="5d053-138">Windows 10 電腦的正確設定[安裝工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="5d053-138">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="5d053-139">基本C#程式設計的能力。</span><span class="sxs-lookup"><span data-stu-id="5d053-139">Some basic C# programming ability.</span></span>
* <span data-ttu-id="5d053-140">您應已完成[MR 基本概念 101](holograms-101.md)。</span><span class="sxs-lookup"><span data-stu-id="5d053-140">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="5d053-141">您應已完成[MR 輸入 210](holograms-210.md)。</span><span class="sxs-lookup"><span data-stu-id="5d053-141">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="5d053-142">您應已完成[MR 輸入 211](holograms-211.md)。</span><span class="sxs-lookup"><span data-stu-id="5d053-142">You should have completed [MR Input 211](holograms-211.md).</span></span>
* <span data-ttu-id="5d053-143">HoloLens 裝置[開發設定的](using-visual-studio.md#enabling-developer-mode)。</span><span class="sxs-lookup"><span data-stu-id="5d053-143">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="5d053-144">專案檔</span><span class="sxs-lookup"><span data-stu-id="5d053-144">Project files</span></span>

* <span data-ttu-id="5d053-145">下載[檔案](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip)專案所需。</span><span class="sxs-lookup"><span data-stu-id="5d053-145">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) required by the project.</span></span> <span data-ttu-id="5d053-146">需要 Unity 2017.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="5d053-146">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="5d053-147">取消封存您的桌面或其他您輕鬆地連線到位置的檔案。</span><span class="sxs-lookup"><span data-stu-id="5d053-147">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="5d053-148">如果您想要查看原始程式碼，在下載之前，它有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice)。</span><span class="sxs-lookup"><span data-stu-id="5d053-148">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="5d053-149">偵錯 errata 和附註</span><span class="sxs-lookup"><span data-stu-id="5d053-149">Errata and Notes</span></span>

* <span data-ttu-id="5d053-150">若要停用 啟用 Just My Code 的需求 (*未核取*) 在 Visual Studio 的 工具-> 選項-> 偵錯以程式碼中設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="5d053-150">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="5d053-151">Unity 安裝</span><span class="sxs-lookup"><span data-stu-id="5d053-151">Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="5d053-152">指示</span><span class="sxs-lookup"><span data-stu-id="5d053-152">Instructions</span></span>

1. <span data-ttu-id="5d053-153">啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="5d053-153">Start Unity.</span></span>
2. <span data-ttu-id="5d053-154">選取 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="5d053-154">Select **Open**.</span></span>
3. <span data-ttu-id="5d053-155">瀏覽至**HolographicAcademy 全像投影-212 語音**資料夾您先前未封存。</span><span class="sxs-lookup"><span data-stu-id="5d053-155">Navigate to the **HolographicAcademy-Holograms-212-Voice** folder you previously un-archived.</span></span>
4. <span data-ttu-id="5d053-156">尋找並選取**起始**/**模型總管**資料夾。</span><span class="sxs-lookup"><span data-stu-id="5d053-156">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="5d053-157">按一下 [**選取資料夾**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5d053-157">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="5d053-158">在 [**專案**] 面板中，展開**場景**資料夾。</span><span class="sxs-lookup"><span data-stu-id="5d053-158">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="5d053-159">按兩下**ModelExplorer**載入在 Unity 中的場景。</span><span class="sxs-lookup"><span data-stu-id="5d053-159">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="5d053-160">建置</span><span class="sxs-lookup"><span data-stu-id="5d053-160">Building</span></span>

1. <span data-ttu-id="5d053-161">在 Unity 中，選取**檔案 > 組建設定**。</span><span class="sxs-lookup"><span data-stu-id="5d053-161">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="5d053-162">如果**場景/ModelExplorer**中未列出**組建中的場景**，按一下 **加入開啟的場景**加入場景。</span><span class="sxs-lookup"><span data-stu-id="5d053-162">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="5d053-163">如果您要特別開發的 HoloLens，設定**目標裝置**要**HoloLens**。</span><span class="sxs-lookup"><span data-stu-id="5d053-163">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="5d053-164">否則，將它保留在**任何裝置**。</span><span class="sxs-lookup"><span data-stu-id="5d053-164">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="5d053-165">確保**建置型別**設為**D3D**並**SDK**設定為**最新安裝**（這應該可以 16299 或更新版本的 SDK）。</span><span class="sxs-lookup"><span data-stu-id="5d053-165">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="5d053-166">按一下 [建置] 。</span><span class="sxs-lookup"><span data-stu-id="5d053-166">Click **Build**.</span></span>
6. <span data-ttu-id="5d053-167">建立**新的資料夾**名為 「 應用程式 」。</span><span class="sxs-lookup"><span data-stu-id="5d053-167">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="5d053-168">只要按一下**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="5d053-168">Single click the **App** folder.</span></span>
8. <span data-ttu-id="5d053-169">按下**選取資料夾**，Unity 將會啟動 Visual studio 中建置專案。</span><span class="sxs-lookup"><span data-stu-id="5d053-169">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="5d053-170">Unity 完成時，會出現檔案總管 視窗。</span><span class="sxs-lookup"><span data-stu-id="5d053-170">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="5d053-171">開啟**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="5d053-171">Open the **App** folder.</span></span>
2. <span data-ttu-id="5d053-172">開啟**ModelExplorer Visual Studio 解決方案**。</span><span class="sxs-lookup"><span data-stu-id="5d053-172">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="5d053-173">如果將部署到 HoloLens:</span><span class="sxs-lookup"><span data-stu-id="5d053-173">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="5d053-174">使用頂端的工具列，在 Visual Studio 中，從 偵錯，若要變更目標**Release**進出至 ARM **x86**。</span><span class="sxs-lookup"><span data-stu-id="5d053-174">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="5d053-175">按一下下拉式清單 [本機電腦] 按鈕旁邊的箭號，然後選取**遠端機器**。</span><span class="sxs-lookup"><span data-stu-id="5d053-175">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="5d053-176">請輸入**HoloLens 裝置的 IP 位址**並將驗證模式設定為**通用 （未加密的通訊協定）**。</span><span class="sxs-lookup"><span data-stu-id="5d053-176">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="5d053-177">按一下 **選取**。</span><span class="sxs-lookup"><span data-stu-id="5d053-177">Click **Select**.</span></span> <span data-ttu-id="5d053-178">如果您不知道您的裝置 IP 位址，查看**設定 > 網路和網際網路 > 進階選項**。</span><span class="sxs-lookup"><span data-stu-id="5d053-178">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="5d053-179">在頂端功能表列中，按一下**偵錯]-> [啟動但不偵錯**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="5d053-179">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="5d053-180">如果這是第一次部署到您的裝置，您必須[與 Visual Studio 中配對](using-visual-studio.md#pairing-your-device-hololens)。</span><span class="sxs-lookup"><span data-stu-id="5d053-180">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="5d053-181">當應用程式部署時，關閉**Fitbox**具有**選取 軌跡**。</span><span class="sxs-lookup"><span data-stu-id="5d053-181">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="5d053-182">如果將部署到擬真耳機：</span><span class="sxs-lookup"><span data-stu-id="5d053-182">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="5d053-183">使用頂端的工具列，在 Visual Studio 中，從 偵錯，若要變更目標**Release**進出至 ARM **x64**。</span><span class="sxs-lookup"><span data-stu-id="5d053-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="5d053-184">請確定部署目標設定為**本機電腦**。</span><span class="sxs-lookup"><span data-stu-id="5d053-184">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="5d053-185">在頂端功能表列中，按一下**偵錯]-> [啟動但不偵錯**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="5d053-185">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="5d053-186">當應用程式部署時，關閉**Fitbox**所提取的動作控制站上的觸發程序。</span><span class="sxs-lookup"><span data-stu-id="5d053-186">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="5d053-187">您可能會注意到一些紅色的錯誤，在 Visual Studio 的 [錯誤] 面板。</span><span class="sxs-lookup"><span data-stu-id="5d053-187">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="5d053-188">它可以安全地忽略它們。</span><span class="sxs-lookup"><span data-stu-id="5d053-188">It is safe to ignore them.</span></span> <span data-ttu-id="5d053-189">切換至 [輸出] 面板，若要檢視實際組建進度。</span><span class="sxs-lookup"><span data-stu-id="5d053-189">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="5d053-190">在 [輸出] 面板中的錯誤會要求您修正 （最常在指令碼中發生錯誤所造成）。</span><span class="sxs-lookup"><span data-stu-id="5d053-190">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---awareness"></a><span data-ttu-id="5d053-191">第 1 章-感知</span><span class="sxs-lookup"><span data-stu-id="5d053-191">Chapter 1 - Awareness</span></span>

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a><span data-ttu-id="5d053-192">目標</span><span class="sxs-lookup"><span data-stu-id="5d053-192">Objectives</span></span>

* <span data-ttu-id="5d053-193">了解**守則**語音命令設計。</span><span class="sxs-lookup"><span data-stu-id="5d053-193">Learn the **Dos and Don'ts** of voice command design.</span></span>
* <span data-ttu-id="5d053-194">使用**KeywordRecognizer**將基礎的視線語音命令。</span><span class="sxs-lookup"><span data-stu-id="5d053-194">Use **KeywordRecognizer** to add gaze based voice commands.</span></span>
* <span data-ttu-id="5d053-195">讓使用者使用資料指標的語音命令察覺**意見反應**。</span><span class="sxs-lookup"><span data-stu-id="5d053-195">Make users aware of voice commands using cursor **feedback**.</span></span>

### <a name="voice-command-design"></a><span data-ttu-id="5d053-196">語音命令設計</span><span class="sxs-lookup"><span data-stu-id="5d053-196">Voice Command Design</span></span>

<span data-ttu-id="5d053-197">在本章中，您將了解設計語音命令。</span><span class="sxs-lookup"><span data-stu-id="5d053-197">In this chapter, you'll learn about designing voice commands.</span></span> <span data-ttu-id="5d053-198">當建立語音命令：</span><span class="sxs-lookup"><span data-stu-id="5d053-198">When creating voice commands:</span></span>

#### <a name="do"></a><span data-ttu-id="5d053-199">DO</span><span class="sxs-lookup"><span data-stu-id="5d053-199">DO</span></span>

* <span data-ttu-id="5d053-200">建立精簡的命令。</span><span class="sxs-lookup"><span data-stu-id="5d053-200">Create concise commands.</span></span> <span data-ttu-id="5d053-201">您不想要 *「 遊戲的目前選取的視訊 」*，因為該命令不是精簡且容易會忘記使用者。</span><span class="sxs-lookup"><span data-stu-id="5d053-201">You don't want to use *"Play the currently selected video"*, because that command is not concise and would easily be forgotten by the user.</span></span> <span data-ttu-id="5d053-202">相反地，您應該使用：*「 播放的視訊"*，因為它是精確且有多個音節。</span><span class="sxs-lookup"><span data-stu-id="5d053-202">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="5d053-203">使用簡單的詞彙。</span><span class="sxs-lookup"><span data-stu-id="5d053-203">Use a simple vocabulary.</span></span> <span data-ttu-id="5d053-204">永遠嘗試使用常見的單字和片語，都能輕鬆地探索並記住使用者。</span><span class="sxs-lookup"><span data-stu-id="5d053-204">Always try to use common words and phrases that are easy for the user to discover and remember.</span></span> <span data-ttu-id="5d053-205">例如，如果您的應用程式有可能顯示或隱藏的附註物件，您可以不使用命令 *」 顯示牌子"*，因為 「 牌子 」 是一個很少使用的詞彙。</span><span class="sxs-lookup"><span data-stu-id="5d053-205">For example, if your application had a note object that could be displayed or hidden from view, you would not use the command *"Show Placard"*, because "placard" is a rarely used term.</span></span> <span data-ttu-id="5d053-206">相反地，您可以使用命令：*「 顯示附註 」*，以顯示您的應用程式中的附註。</span><span class="sxs-lookup"><span data-stu-id="5d053-206">Instead, you would use the command: *"Show Note"*, to reveal the note in your application.</span></span>
* <span data-ttu-id="5d053-207">保持一致。</span><span class="sxs-lookup"><span data-stu-id="5d053-207">Be consistent.</span></span> <span data-ttu-id="5d053-208">語音命令應該保持一致跨應用程式。</span><span class="sxs-lookup"><span data-stu-id="5d053-208">Voice commands should be kept consistent across your application.</span></span> <span data-ttu-id="5d053-209">假設應用程式中有兩個場景，而這兩個場景包含按鈕以關閉應用程式。</span><span class="sxs-lookup"><span data-stu-id="5d053-209">Imagine that you have two scenes in your application and both scenes contain a button for closing the application.</span></span> <span data-ttu-id="5d053-210">如果第一個場景會使用命令 *"Exit"* 觸發按鈕，但第二個場景會使用命令 *「 關閉應用程式 」*，然後使用者要亂成一團了。</span><span class="sxs-lookup"><span data-stu-id="5d053-210">If the first scene used the command *"Exit"* to trigger the button, but the second scene used the command *"Close App"*, then the user is going to get very confused.</span></span> <span data-ttu-id="5d053-211">如果跨多個場景，保存相同的功能，則應該使用相同的語音命令觸發它。</span><span class="sxs-lookup"><span data-stu-id="5d053-211">If the same functionality persists across multiple scenes, then the same voice command should be used to trigger it.</span></span>

#### <a name="dont"></a><span data-ttu-id="5d053-212">不</span><span class="sxs-lookup"><span data-stu-id="5d053-212">DON'T</span></span>

* <span data-ttu-id="5d053-213">使用單一音節命令。</span><span class="sxs-lookup"><span data-stu-id="5d053-213">Use single syllable commands.</span></span> <span data-ttu-id="5d053-214">例如，如果您所建立的語音命令，來播放視訊，您應該避免使用簡單的命令 *「 遊戲 」*，因為它是只有單一音節，輕鬆地可能遺漏的系統。</span><span class="sxs-lookup"><span data-stu-id="5d053-214">As an example, if you were creating a voice command to play a video, you should avoid using the simple command *"Play"*, as it is only a single syllable and could easily be missed by the system.</span></span> <span data-ttu-id="5d053-215">相反地，您應該使用：*「 播放的視訊"*，因為它是精確且有多個音節。</span><span class="sxs-lookup"><span data-stu-id="5d053-215">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="5d053-216">使用系統命令。</span><span class="sxs-lookup"><span data-stu-id="5d053-216">Use system commands.</span></span> <span data-ttu-id="5d053-217">*"Select"* 命令已保留，由系統目前的焦點的物件的點選事件觸發程序。</span><span class="sxs-lookup"><span data-stu-id="5d053-217">The *"Select"* command is reserved by the system to trigger a Tap event for the currently focused object.</span></span> <span data-ttu-id="5d053-218">不要重複使用 *"Select"* 命令中的關鍵字或片語，因為它可能無法運作如預期般。</span><span class="sxs-lookup"><span data-stu-id="5d053-218">Do not re-use the *"Select"* command in a keyword or phrase, as it might not work as you expect.</span></span> <span data-ttu-id="5d053-219">比方說，如果應用程式中選取 cube 的語音命令已 *「 選取的 cube"*，但使用者想要球體時它們玩具店命令，則會改為選取的球體。</span><span class="sxs-lookup"><span data-stu-id="5d053-219">For example, if the voice command for selecting a cube in your application was *"Select cube"*, but the user was looking at a sphere when they uttered the command, then the sphere would be selected instead.</span></span> <span data-ttu-id="5d053-220">同樣的應用程式列命令是啟用的語音。</span><span class="sxs-lookup"><span data-stu-id="5d053-220">Similarly app bar commands are voice enabled.</span></span> <span data-ttu-id="5d053-221">不在 corewindow 成為檢視中使用下列的語音命令：</span><span class="sxs-lookup"><span data-stu-id="5d053-221">Don't use the following speech commands in your CoreWindow View:</span></span>
    1. <span data-ttu-id="5d053-222">返回</span><span class="sxs-lookup"><span data-stu-id="5d053-222">Go Back</span></span>
    2. <span data-ttu-id="5d053-223">捲動工具</span><span class="sxs-lookup"><span data-stu-id="5d053-223">Scroll Tool</span></span>
    3. <span data-ttu-id="5d053-224">縮放工具</span><span class="sxs-lookup"><span data-stu-id="5d053-224">Zoom Tool</span></span>
    4. <span data-ttu-id="5d053-225">拖放工具</span><span class="sxs-lookup"><span data-stu-id="5d053-225">Drag Tool</span></span>
    5. <span data-ttu-id="5d053-226">Adjust</span><span class="sxs-lookup"><span data-stu-id="5d053-226">Adjust</span></span>
    6. <span data-ttu-id="5d053-227">移除</span><span class="sxs-lookup"><span data-stu-id="5d053-227">Remove</span></span>
* <span data-ttu-id="5d053-228">使用類似的音效。</span><span class="sxs-lookup"><span data-stu-id="5d053-228">Use similar sounds.</span></span> <span data-ttu-id="5d053-229">請盡量避免使用光的語音命令。</span><span class="sxs-lookup"><span data-stu-id="5d053-229">Try to avoid using voice commands that rhyme.</span></span> <span data-ttu-id="5d053-230">如果您已將購物應用程式支援 *「 顯示存放區 」* 並 *[顯示更多]* 做為語音命令，則您會想要其他正在使用中時，停用其中一個命令。</span><span class="sxs-lookup"><span data-stu-id="5d053-230">If you had a shopping application which supported *"Show Store"* and *"Show More"* as voice commands, then you would want to disable one of the commands while the other was in use.</span></span> <span data-ttu-id="5d053-231">例如，您可以使用 *[顯示儲存]* 按鈕以開啟市集，並顯示存放區時，則停用該命令以便 *[顯示更多]* 命令可用來瀏覽。</span><span class="sxs-lookup"><span data-stu-id="5d053-231">For example, you could use the *"Show Store"* button to open the store, and then disable that command when the store was displayed so that the *"Show More"* command could be used for browsing.</span></span>

### <a name="instructions"></a><span data-ttu-id="5d053-232">指示</span><span class="sxs-lookup"><span data-stu-id="5d053-232">Instructions</span></span>

* <span data-ttu-id="5d053-233">在 Unity**階層** 面板中，使用 「 搜尋 」 工具來尋找**holoComm_screen_mesh**物件。</span><span class="sxs-lookup"><span data-stu-id="5d053-233">In Unity's **Hierarchy** panel, use the search tool to find the **holoComm_screen_mesh** object.</span></span>
* <span data-ttu-id="5d053-234">按兩下**holoComm_screen_mesh**檢視中的物件**場景**。</span><span class="sxs-lookup"><span data-stu-id="5d053-234">Double-click on the **holoComm_screen_mesh** object to view it in the **Scene**.</span></span> <span data-ttu-id="5d053-235">這是太空人監看式，將會回我們的語音命令。</span><span class="sxs-lookup"><span data-stu-id="5d053-235">This is the astronaut's watch, which will respond to our voice commands.</span></span>
* <span data-ttu-id="5d053-236">在 [ **Inspector** ] 面板中，找出**語音輸入來源 （指令碼）** 元件。</span><span class="sxs-lookup"><span data-stu-id="5d053-236">In the **Inspector** panel, locate the **Speech Input Source (Script)** component.</span></span>
* <span data-ttu-id="5d053-237">依序展開**關鍵字**區段可查看支援的語音命令：**開啟 Communicator**。</span><span class="sxs-lookup"><span data-stu-id="5d053-237">Expand the **Keywords** section to see the supported voice command: **Open Communicator**.</span></span>
* <span data-ttu-id="5d053-238">按一下至右邊的齒輪圖示，然後選取**編輯指令碼**。</span><span class="sxs-lookup"><span data-stu-id="5d053-238">Click the cog to the right side, then select **Edit Script**.</span></span>
* <span data-ttu-id="5d053-239">瀏覽**SpeechInputSource.cs**若要了解如何使用**KeywordRecognizer**新增語音命令。</span><span class="sxs-lookup"><span data-stu-id="5d053-239">Explore **SpeechInputSource.cs** to understand how it uses the **KeywordRecognizer** to add voice commands.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="5d053-240">建置和部署</span><span class="sxs-lookup"><span data-stu-id="5d053-240">Build and Deploy</span></span>

* <span data-ttu-id="5d053-241">在 Unity 中，使用**檔案 > 組建設定**重建應用程式。</span><span class="sxs-lookup"><span data-stu-id="5d053-241">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="5d053-242">開啟**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="5d053-242">Open the **App** folder.</span></span>
* <span data-ttu-id="5d053-243">開啟**ModelExplorer Visual Studio 解決方案**。</span><span class="sxs-lookup"><span data-stu-id="5d053-243">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="5d053-244">（如果您已經建置/部署此專案在 Visual Studio 設定期間，然後您可以開啟 VS 執行個體並按一下 [重新載入全部] 出現提示時）。</span><span class="sxs-lookup"><span data-stu-id="5d053-244">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>

* <span data-ttu-id="5d053-245">在 Visual Studio 中，按一下**偵錯]-> [啟動但不偵錯**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="5d053-245">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="5d053-246">應用程式部署到 HoloLens 之後，關閉 調整的方塊中，使用[空中點選](gestures.md#air-tap)筆勢。</span><span class="sxs-lookup"><span data-stu-id="5d053-246">After the application deploys to the HoloLens, dismiss the fit box using the [air-tap](gestures.md#air-tap) gesture.</span></span>
* <span data-ttu-id="5d053-247">注視太空人監看式。</span><span class="sxs-lookup"><span data-stu-id="5d053-247">Gaze at the astronaut's watch.</span></span>
* <span data-ttu-id="5d053-248">當監看式有焦點時，請確認，游標會變成麥克風。</span><span class="sxs-lookup"><span data-stu-id="5d053-248">When the watch has focus, verify that the cursor changes to a microphone.</span></span> <span data-ttu-id="5d053-249">這會提供應用程式正在接聽的語音命令的意見反應。</span><span class="sxs-lookup"><span data-stu-id="5d053-249">This provides feedback that the application is listening for voice commands.</span></span>
* <span data-ttu-id="5d053-250">請確認，工具提示會出現在 監看式。</span><span class="sxs-lookup"><span data-stu-id="5d053-250">Verify that a tooltip appears on the watch.</span></span> <span data-ttu-id="5d053-251">這可協助使用者探索 *"開啟 Communicator"* 命令。</span><span class="sxs-lookup"><span data-stu-id="5d053-251">This helps users discover the *"Open Communicator"* command.</span></span>
* <span data-ttu-id="5d053-252">同時在監看式 gazing，說 *"開啟 Communicator"* 開啟 communicator 面板。</span><span class="sxs-lookup"><span data-stu-id="5d053-252">While gazing at the watch, say *"Open Communicator"* to open the communicator panel.</span></span>

## <a name="chapter-2---acknowledgement"></a><span data-ttu-id="5d053-253">第 2 章-通知</span><span class="sxs-lookup"><span data-stu-id="5d053-253">Chapter 2 - Acknowledgement</span></span>

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a><span data-ttu-id="5d053-254">目標</span><span class="sxs-lookup"><span data-stu-id="5d053-254">Objectives</span></span>

* <span data-ttu-id="5d053-255">記錄使用麥克風輸入的訊息。</span><span class="sxs-lookup"><span data-stu-id="5d053-255">Record a message using the Microphone input.</span></span>
* <span data-ttu-id="5d053-256">提供意見反應給使用者應用程式正在接聽其語音。</span><span class="sxs-lookup"><span data-stu-id="5d053-256">Give feedback to the user that the application is listening to their voice.</span></span>

>[!NOTE]
><span data-ttu-id="5d053-257">**麥克風**必須宣告功能，讓應用程式從麥克風錄製。</span><span class="sxs-lookup"><span data-stu-id="5d053-257">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="5d053-258">這是針對您已在 MR 輸入 212，但謹記在心，為您自己的專案。</span><span class="sxs-lookup"><span data-stu-id="5d053-258">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="5d053-259">瀏覽至 「 編輯 > 專案設定 > 播放程式 」 在 Unity 編輯器中，請移至播放程式設定</span><span class="sxs-lookup"><span data-stu-id="5d053-259">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="5d053-260">按一下 「 通用 Windows 平台 」 索引標籤</span><span class="sxs-lookup"><span data-stu-id="5d053-260">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="5d053-261">在 「 發行的設定 > 功能 」 區段中，檢查**麥克風**功能</span><span class="sxs-lookup"><span data-stu-id="5d053-261">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="5d053-262">指示</span><span class="sxs-lookup"><span data-stu-id="5d053-262">Instructions</span></span>

* <span data-ttu-id="5d053-263">在 Unity**階層** 面板中，確認**holoComm_screen_mesh**選取物件。</span><span class="sxs-lookup"><span data-stu-id="5d053-263">In Unity's **Hierarchy** panel, verify that the **holoComm_screen_mesh** object is selected.</span></span>
* <span data-ttu-id="5d053-264">在 [ **Inspector** ] 面板中，尋找**太空人監看式 （指令碼）** 元件。</span><span class="sxs-lookup"><span data-stu-id="5d053-264">In the **Inspector** panel, find the **Astronaut Watch (Script)** component.</span></span>
* <span data-ttu-id="5d053-265">按一下已設定的值為小型的藍色 cube **Communicator Prefab**屬性。</span><span class="sxs-lookup"><span data-stu-id="5d053-265">Click on the small, blue cube which is set as the value of the **Communicator Prefab** property.</span></span>
* <span data-ttu-id="5d053-266">在 [**專案**] 面板中， **Communicator** prefab 現在應該有焦點。</span><span class="sxs-lookup"><span data-stu-id="5d053-266">In the **Project** panel, the **Communicator** prefab should now have focus.</span></span>
* <span data-ttu-id="5d053-267">按一下  **Communicator** prefab 中**專案**面板，以檢視及其元件**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="5d053-267">Click on the **Communicator** prefab in the **Project** panel to view its components in the **Inspector**.</span></span>
* <span data-ttu-id="5d053-268">看看**麥克風 Manager （指令碼）** 元件，這可讓我們來記錄使用者的語音。</span><span class="sxs-lookup"><span data-stu-id="5d053-268">Look at the **Microphone Manager (Script)** component, this will allow us to record the user's voice.</span></span>
* <span data-ttu-id="5d053-269">請注意， **Communicator**物件具有**語音輸入處理常式 （指令碼）** 元件回應**傳送訊息**命令。</span><span class="sxs-lookup"><span data-stu-id="5d053-269">Notice that the **Communicator** object has a **Speech Input Handler (Script)** component for responding to the **Send Message** command.</span></span>
* <span data-ttu-id="5d053-270">看看**Communicator （指令碼）** 元件，並按兩下要開啟 Visual Studio 中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="5d053-270">Look at the **Communicator (Script)** component and double-click on the script to open it in Visual Studio.</span></span>

<span data-ttu-id="5d053-271">Communicator.cs 負責 communicator 裝置上設定適當的按鈕狀態。</span><span class="sxs-lookup"><span data-stu-id="5d053-271">Communicator.cs is responsible for setting the proper button states on the communicator device.</span></span> <span data-ttu-id="5d053-272">這可讓我們來記錄訊息、 播放它，並將訊息傳送至太空人的使用者。</span><span class="sxs-lookup"><span data-stu-id="5d053-272">This will allow our users to record a message, play it back, and send the message to the astronaut.</span></span> <span data-ttu-id="5d053-273">它也會啟動並停止動畫的 wave 格式，以確認使用者語音已聽過。</span><span class="sxs-lookup"><span data-stu-id="5d053-273">It will also start and stop an animated wave form, to acknowledge to the user that their voice was heard.</span></span>

* <span data-ttu-id="5d053-274">在  **Communicator.cs**，從刪除下列幾行 （81 和 82）**開始**方法。</span><span class="sxs-lookup"><span data-stu-id="5d053-274">In **Communicator.cs**, delete the following lines (81 and 82) from the **Start** method.</span></span> <span data-ttu-id="5d053-275">這可讓在 communicator 'Record' 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5d053-275">This will enable the 'Record' button on the communicator.</span></span>

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a><span data-ttu-id="5d053-276">建置和部署</span><span class="sxs-lookup"><span data-stu-id="5d053-276">Build and Deploy</span></span>

* <span data-ttu-id="5d053-277">在 Visual Studio 中，重建您的應用程式並部署到裝置。</span><span class="sxs-lookup"><span data-stu-id="5d053-277">In Visual Studio, rebuild your application and deploy to the device.</span></span>
* <span data-ttu-id="5d053-278">注視太空人監看式，並說 *"開啟 Communicator"* 顯示 communicator。</span><span class="sxs-lookup"><span data-stu-id="5d053-278">Gaze at the astronaut's watch and say *"Open Communicator"* to show the communicator.</span></span>
* <span data-ttu-id="5d053-279">按下**記錄**按鈕 （麥克風） 開始的太空人錄製口說的訊息。</span><span class="sxs-lookup"><span data-stu-id="5d053-279">Press the **Record** button (microphone) to start recording a verbal message for the astronaut.</span></span>
* <span data-ttu-id="5d053-280">開始錄製，並確認 wave 動畫播放在 communicator，可提供給使用者的意見反應，要聽語音。</span><span class="sxs-lookup"><span data-stu-id="5d053-280">Start speaking, and verify that the wave animation plays on the communicator, which provides feedback to the user that their voice is heard.</span></span>
* <span data-ttu-id="5d053-281">按下**停止**按鈕 （左上的方），並確認 wave 動畫停止執行。</span><span class="sxs-lookup"><span data-stu-id="5d053-281">Press the **Stop** button (left square), and verify that the wave animation stops running.</span></span>
* <span data-ttu-id="5d053-282">按下**播放**播放錄製的訊息，並聆聽裝置上的按鈕 （右邊的三角形）。</span><span class="sxs-lookup"><span data-stu-id="5d053-282">Press the **Play** button (right triangle) to play back the recorded message and hear it on the device.</span></span>
* <span data-ttu-id="5d053-283">按下**停止**按鈕 （右邊的正方形） 若要停止播放錄製的訊息。</span><span class="sxs-lookup"><span data-stu-id="5d053-283">Press the **Stop** button (right square) to stop playback of the recorded message.</span></span>
* <span data-ttu-id="5d053-284">假設 *[傳送訊息]* 關閉 communicator 並接收來自太空人 '收到的訊息' 的回應。</span><span class="sxs-lookup"><span data-stu-id="5d053-284">Say *"Send Message"* to close the communicator and receive a 'Message Received' response from the astronaut.</span></span>

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a><span data-ttu-id="5d053-285">第 3 章-了解和聽寫辨識器</span><span class="sxs-lookup"><span data-stu-id="5d053-285">Chapter 3 - Understanding and the Dictation Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a><span data-ttu-id="5d053-286">目標</span><span class="sxs-lookup"><span data-stu-id="5d053-286">Objectives</span></span>

* <span data-ttu-id="5d053-287">您可以使用聽寫辨識器，使用者的語音轉換文字。</span><span class="sxs-lookup"><span data-stu-id="5d053-287">Use the Dictation Recognizer to convert the user's speech to text.</span></span>
* <span data-ttu-id="5d053-288">Communicator 中會顯示聽寫辨識器虛無和最終結果。</span><span class="sxs-lookup"><span data-stu-id="5d053-288">Show the Dictation Recognizer's hypothesized and final results in the communicator.</span></span>

<span data-ttu-id="5d053-289">在本章中，我們將使用聽寫辨識器為太空人建立一則訊息。</span><span class="sxs-lookup"><span data-stu-id="5d053-289">In this chapter, we'll use the Dictation Recognizer to create a message for the astronaut.</span></span> <span data-ttu-id="5d053-290">當使用聽寫辨識器，請注意下列事項：</span><span class="sxs-lookup"><span data-stu-id="5d053-290">When using the Dictation Recognizer, keep in mind that:</span></span>

* <span data-ttu-id="5d053-291">您必須連線至 WiFi 聽寫辨識器運作。</span><span class="sxs-lookup"><span data-stu-id="5d053-291">You must be connected to WiFi for the Dictation Recognizer to work.</span></span>
* <span data-ttu-id="5d053-292">在一段時間之後，就會發生逾時。</span><span class="sxs-lookup"><span data-stu-id="5d053-292">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="5d053-293">有兩個逾時，要注意的：</span><span class="sxs-lookup"><span data-stu-id="5d053-293">There are two timeouts to be aware of:</span></span>
  * <span data-ttu-id="5d053-294">如果辨識器啟動，且聽任何音訊第五秒，它就會逾時。</span><span class="sxs-lookup"><span data-stu-id="5d053-294">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
  * <span data-ttu-id="5d053-295">如果辨識器已提供結果，但然後聽到 20 秒的無回應，它就會逾時。</span><span class="sxs-lookup"><span data-stu-id="5d053-295">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>
* <span data-ttu-id="5d053-296">只有一種類型的辨識器 （關鍵字或聽寫） 可以執行一次。</span><span class="sxs-lookup"><span data-stu-id="5d053-296">Only one type of recognizer (Keyword or Dictation) can run at a time.</span></span>

>[!NOTE]
><span data-ttu-id="5d053-297">**麥克風**必須宣告功能，讓應用程式從麥克風錄製。</span><span class="sxs-lookup"><span data-stu-id="5d053-297">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="5d053-298">這是針對您已在 MR 輸入 212，但謹記在心，為您自己的專案。</span><span class="sxs-lookup"><span data-stu-id="5d053-298">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="5d053-299">瀏覽至 「 編輯 > 專案設定 > 播放程式 」 在 Unity 編輯器中，請移至播放程式設定</span><span class="sxs-lookup"><span data-stu-id="5d053-299">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="5d053-300">按一下 「 通用 Windows 平台 」 索引標籤</span><span class="sxs-lookup"><span data-stu-id="5d053-300">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="5d053-301">在 「 發行的設定 > 功能 」 區段中，檢查**麥克風**功能</span><span class="sxs-lookup"><span data-stu-id="5d053-301">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="5d053-302">指示</span><span class="sxs-lookup"><span data-stu-id="5d053-302">Instructions</span></span>

<span data-ttu-id="5d053-303">我們將編輯**MicrophoneManager.cs**使用聽寫辨識器。</span><span class="sxs-lookup"><span data-stu-id="5d053-303">We're going to edit **MicrophoneManager.cs** to use the Dictation Recognizer.</span></span> <span data-ttu-id="5d053-304">這是我們將加入的項目：</span><span class="sxs-lookup"><span data-stu-id="5d053-304">This is what we'll add:</span></span>

1. <span data-ttu-id="5d053-305">當**錄製 按鈕**是我們按下，將**開始 DictationRecognizer**。</span><span class="sxs-lookup"><span data-stu-id="5d053-305">When the **Record button** is pressed, we'll **start the DictationRecognizer**.</span></span>
2. <span data-ttu-id="5d053-306">顯示**假設**的 DictationRecognizer 的瞭解。</span><span class="sxs-lookup"><span data-stu-id="5d053-306">Show the **hypothesis** of what the DictationRecognizer understood.</span></span>
3. <span data-ttu-id="5d053-307">鎖住**結果**的 DictationRecognizer 的瞭解。</span><span class="sxs-lookup"><span data-stu-id="5d053-307">Lock in the **results** of what the DictationRecognizer understood.</span></span>
4. <span data-ttu-id="5d053-308">檢查有從 DictationRecognizer 的逾時。</span><span class="sxs-lookup"><span data-stu-id="5d053-308">Check for timeouts from the DictationRecognizer.</span></span>
5. <span data-ttu-id="5d053-309">當**停止 按鈕**按下時，或 mic 工作階段逾時，**停止 DictationRecognizer**。</span><span class="sxs-lookup"><span data-stu-id="5d053-309">When the **Stop button** is pressed, or the mic session times out, **stop the DictationRecognizer**.</span></span>
6. <span data-ttu-id="5d053-310">重新啟動**KeywordRecognizer**，用接聽**傳送訊息**命令。</span><span class="sxs-lookup"><span data-stu-id="5d053-310">Restart the **KeywordRecognizer**, which will listen for the **Send Message** command.</span></span>

<span data-ttu-id="5d053-311">那就開始吧。</span><span class="sxs-lookup"><span data-stu-id="5d053-311">Let's get started.</span></span> <span data-ttu-id="5d053-312">完成 3.a 中的所有程式碼撰寫練習**MicrophoneManager.cs**，或複製並貼上完成的程式碼下方：</span><span class="sxs-lookup"><span data-stu-id="5d053-312">Complete all coding exercises for 3.a in **MicrophoneManager.cs**, or copy and paste the finished code found below:</span></span>

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using System.Collections;
using System.Text;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Windows.Speech;

namespace Academy
{
    public class MicrophoneManager : MonoBehaviour
    {
        [Tooltip("A text area for the recognizer to display the recognized strings.")]
        [SerializeField]
        private Text dictationDisplay;

        private DictationRecognizer dictationRecognizer;

        // Use this string to cache the text currently displayed in the text box.
        private StringBuilder textSoFar;

        // Using an empty string specifies the default microphone. 
        private static string deviceName = string.Empty;
        private int samplingRate;
        private const int messageLength = 10;

        // Use this to reset the UI once the Microphone is done recording after it was started.
        private bool hasRecordingStarted;

        void Awake()
        {
            /* TODO: DEVELOPER CODING EXERCISE 3.a */

            // 3.a: Create a new DictationRecognizer and assign it to dictationRecognizer variable.
            dictationRecognizer = new DictationRecognizer();

            // 3.a: Register for dictationRecognizer.DictationHypothesis and implement DictationHypothesis below
            // This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
            dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;

            // 3.a: Register for dictationRecognizer.DictationResult and implement DictationResult below
            // This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;

            // 3.a: Register for dictationRecognizer.DictationComplete and implement DictationComplete below
            // This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
            dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;

            // 3.a: Register for dictationRecognizer.DictationError and implement DictationError below
            // This event is fired when an error occurs.
            dictationRecognizer.DictationError += DictationRecognizer_DictationError;

            // Query the maximum frequency of the default microphone. Use 'unused' to ignore the minimum frequency.
            int unused;
            Microphone.GetDeviceCaps(deviceName, out unused, out samplingRate);

            // Use this string to cache the text currently displayed in the text box.
            textSoFar = new StringBuilder();

            // Use this to reset the UI once the Microphone is done recording after it was started.
            hasRecordingStarted = false;
        }

        void Update()
        {
            // 3.a: Add condition to check if dictationRecognizer.Status is Running
            if (hasRecordingStarted && !Microphone.IsRecording(deviceName) && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                // Reset the flag now that we're cleaning up the UI.
                hasRecordingStarted = false;

                // This acts like pressing the Stop button and sends the message to the Communicator.
                // If the microphone stops as a result of timing out, make sure to manually stop the dictation recognizer.
                // Look at the StopRecording function.
                SendMessage("RecordStop");
            }
        }

        /// <summary>
        /// Turns on the dictation recognizer and begins recording audio from the default microphone.
        /// </summary>
        /// <returns>The audio clip recorded from the microphone.</returns>
        public AudioClip StartRecording()
        {
            // 3.a Shutdown the PhraseRecognitionSystem. This controls the KeywordRecognizers
            PhraseRecognitionSystem.Shutdown();

            // 3.a: Start dictationRecognizer
            dictationRecognizer.Start();

            // 3.a Uncomment this line
            dictationDisplay.text = "Dictation is starting. It may take time to display your text the first time, but begin speaking now...";

            // Set the flag that we've started recording.
            hasRecordingStarted = true;

            // Start recording from the microphone for 10 seconds.
            return Microphone.Start(deviceName, false, messageLength, samplingRate);
        }

        /// <summary>
        /// Ends the recording session.
        /// </summary>
        public void StopRecording()
        {
            // 3.a: Check if dictationRecognizer.Status is Running and stop it if so
            if (dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                dictationRecognizer.Stop();
            }

            Microphone.End(deviceName);
        }

        /// <summary>
        /// This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
        /// </summary>
        /// <param name="text">The currently hypothesized recognition.</param>
        private void DictationRecognizer_DictationHypothesis(string text)
        {
            // 3.a: Set DictationDisplay text to be textSoFar and new hypothesized text
            // We don't want to append to textSoFar yet, because the hypothesis may have changed on the next event
            dictationDisplay.text = textSoFar.ToString() + " " + text + "...";
        }

        /// <summary>
        /// This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
        /// </summary>
        /// <param name="text">The text that was heard by the recognizer.</param>
        /// <param name="confidence">A representation of how confident (rejected, low, medium, high) the recognizer is of this recognition.</param>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // 3.a: Append textSoFar with latest text
            textSoFar.Append(text + ". ");

            // 3.a: Set DictationDisplay text to be textSoFar
            dictationDisplay.text = textSoFar.ToString();
        }

        /// <summary>
        /// This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
        /// Typically, this will simply return "Complete". In this case, we check to see if the recognizer timed out.
        /// </summary>
        /// <param name="cause">An enumerated reason for the session completing.</param>
        private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
        {
            // If Timeout occurs, the user has been silent for too long.
            // With dictation, the default timeout after a recognition is 20 seconds.
            // The default timeout with initial silence is 5 seconds.
            if (cause == DictationCompletionCause.TimeoutExceeded)
            {
                Microphone.End(deviceName);

                dictationDisplay.text = "Dictation has timed out. Please press the record button again.";
                SendMessage("ResetAfterTimeout");
            }
        }

        /// <summary>
        /// This event is fired when an error occurs.
        /// </summary>
        /// <param name="error">The string representation of the error reason.</param>
        /// <param name="hresult">The int representation of the hresult.</param>
        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            // 3.a: Set DictationDisplay text to be the error string
            dictationDisplay.text = error + "\nHRESULT: " + hresult;
        }

        /// <summary>
        /// The dictation recognizer may not turn off immediately, so this call blocks on
        /// the recognizer reporting that it has actually stopped.
        /// </summary>
        public IEnumerator WaitForDictationToStop()
        {
            while (dictationRecognizer != null && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                yield return null;
            }
        }
    }
}
```

### <a name="build-and-deploy"></a><span data-ttu-id="5d053-313">建置和部署</span><span class="sxs-lookup"><span data-stu-id="5d053-313">Build and Deploy</span></span>

* <span data-ttu-id="5d053-314">在 Visual Studio 中重建並部署到您的裝置。</span><span class="sxs-lookup"><span data-stu-id="5d053-314">Rebuild in Visual Studio and deploy to your device.</span></span>
* <span data-ttu-id="5d053-315">關閉 [調整] 方塊中的使用空中點選手勢。</span><span class="sxs-lookup"><span data-stu-id="5d053-315">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="5d053-316">注視太空人監看式，並說 *"開啟 Communicator"*。</span><span class="sxs-lookup"><span data-stu-id="5d053-316">Gaze at the astronaut's watch and say *"Open Communicator"*.</span></span>
* <span data-ttu-id="5d053-317">選取 **記錄**按鈕 （麥克風） 來記錄您的訊息。</span><span class="sxs-lookup"><span data-stu-id="5d053-317">Select the **Record** button (microphone) to record your message.</span></span>
* <span data-ttu-id="5d053-318">開始讀出。</span><span class="sxs-lookup"><span data-stu-id="5d053-318">Start speaking.</span></span> <span data-ttu-id="5d053-319">**聽寫辨識器**會解譯您的語音，並在 communicator 顯示虛無的文字。</span><span class="sxs-lookup"><span data-stu-id="5d053-319">The **Dictation Recognizer** will interpret your speech and show the hypothesized text in the communicator.</span></span>
* <span data-ttu-id="5d053-320">嘗試招呼語 *[傳送訊息]* 時記錄訊息。</span><span class="sxs-lookup"><span data-stu-id="5d053-320">Try saying *"Send Message"* while you are recording a message.</span></span> <span data-ttu-id="5d053-321">請注意，**關鍵字的辨識器**不會回應，因為**聽寫辨識器**仍在作用中。</span><span class="sxs-lookup"><span data-stu-id="5d053-321">Notice that the **Keyword Recognizer** does not respond because the **Dictation Recognizer** is still active.</span></span>
* <span data-ttu-id="5d053-322">停止讀出幾秒鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="5d053-322">Stop speaking for a few seconds.</span></span> <span data-ttu-id="5d053-323">觀看聽寫辨識器完成其假設，並顯示最終的結果。</span><span class="sxs-lookup"><span data-stu-id="5d053-323">Watch as the Dictation Recognizer completes its hypothesis and shows the final result.</span></span>
* <span data-ttu-id="5d053-324">開始讀出，然後暫停 20 秒。</span><span class="sxs-lookup"><span data-stu-id="5d053-324">Begin speaking and then pause for 20 seconds.</span></span> <span data-ttu-id="5d053-325">這會導致**聽寫辨識器**逾時。</span><span class="sxs-lookup"><span data-stu-id="5d053-325">This will cause the **Dictation Recognizer** to timeout.</span></span>
* <span data-ttu-id="5d053-326">請注意，**關鍵字的辨識器**上述的逾時之後重新啟用。</span><span class="sxs-lookup"><span data-stu-id="5d053-326">Notice that the **Keyword Recognizer** is re-enabled after the above timeout.</span></span> <span data-ttu-id="5d053-327">Communicator 會立即回應語音命令。</span><span class="sxs-lookup"><span data-stu-id="5d053-327">The communicator will now respond to voice commands.</span></span>
* <span data-ttu-id="5d053-328">假設 *[傳送訊息]* 太空人來傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="5d053-328">Say *"Send Message"* to send the message to the astronaut.</span></span>

## <a name="chapter-4---grammar-recognizer"></a><span data-ttu-id="5d053-329">第 4 章-文法辨識器</span><span class="sxs-lookup"><span data-stu-id="5d053-329">Chapter 4 - Grammar Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a><span data-ttu-id="5d053-330">目標</span><span class="sxs-lookup"><span data-stu-id="5d053-330">Objectives</span></span>

* <span data-ttu-id="5d053-331">使用文法辨識器辨識使用者的語音，依照 SRGS 或語音辨識文法規格的檔案。</span><span class="sxs-lookup"><span data-stu-id="5d053-331">Use the Grammar Recognizer to recognize the user's speech according to an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

>[!NOTE]
><span data-ttu-id="5d053-332">**麥克風**必須宣告功能，讓應用程式從麥克風錄製。</span><span class="sxs-lookup"><span data-stu-id="5d053-332">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="5d053-333">這是針對您已在 MR 輸入 212，但謹記在心，為您自己的專案。</span><span class="sxs-lookup"><span data-stu-id="5d053-333">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="5d053-334">瀏覽至 「 編輯 > 專案設定 > 播放程式 」 在 Unity 編輯器中，請移至播放程式設定</span><span class="sxs-lookup"><span data-stu-id="5d053-334">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="5d053-335">按一下 「 通用 Windows 平台 」 索引標籤</span><span class="sxs-lookup"><span data-stu-id="5d053-335">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="5d053-336">在 「 發行的設定 > 功能 」 區段中，檢查**麥克風**功能</span><span class="sxs-lookup"><span data-stu-id="5d053-336">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="5d053-337">指示</span><span class="sxs-lookup"><span data-stu-id="5d053-337">Instructions</span></span>

1. <span data-ttu-id="5d053-338">在 [**階層**] 面板中，搜尋**Jetpack_Center**並加以選取。</span><span class="sxs-lookup"><span data-stu-id="5d053-338">In the **Hierarchy** panel, search for **Jetpack_Center** and select it.</span></span>
2. <span data-ttu-id="5d053-339">尋求**Tagalong 動作**指令碼**Inspector**面板。</span><span class="sxs-lookup"><span data-stu-id="5d053-339">Look for the **Tagalong Action** script in the **Inspector** panel.</span></span>
3. <span data-ttu-id="5d053-340">按一下右邊的小圓圈**物件來標記沿著**欄位。</span><span class="sxs-lookup"><span data-stu-id="5d053-340">Click the little circle to the right of the **Object To Tag Along** field.</span></span>
4. <span data-ttu-id="5d053-341">在快顯視窗中，搜尋**SRGSToolbox**並從清單中選取。</span><span class="sxs-lookup"><span data-stu-id="5d053-341">In the window that pops up, search for **SRGSToolbox** and select it from the list.</span></span>
5. <span data-ttu-id="5d053-342">看看**SRGSColor.xml**中的檔案**StreamingAssets**資料夾。</span><span class="sxs-lookup"><span data-stu-id="5d053-342">Take a look at the **SRGSColor.xml** file in the **StreamingAssets** folder.</span></span>
* <span data-ttu-id="5d053-343">請參閱 W3C 網站 SRGS 設計規格[此處](https://www.w3.org/TR/speech-grammar/)。</span><span class="sxs-lookup"><span data-stu-id="5d053-343">The SRGS design spec can be found on the W3C website [here](https://www.w3.org/TR/speech-grammar/).</span></span>
* <span data-ttu-id="5d053-344">在我們 SRGS 檔案中，我們有三種類型的規則：</span><span class="sxs-lookup"><span data-stu-id="5d053-344">In our SRGS file, we have three types of rules:</span></span>
  * <span data-ttu-id="5d053-345">可讓您說出十二個色彩的清單中的一個色彩規則。</span><span class="sxs-lookup"><span data-stu-id="5d053-345">A rule which lets you say one color from a list of twelve colors.</span></span>
  * <span data-ttu-id="5d053-346">三個規則的接聽色彩規則和三個圖形的其中一個的組合。</span><span class="sxs-lookup"><span data-stu-id="5d053-346">Three rules which listen for a combination of the color rule and one of the three shapes.</span></span>
  * <span data-ttu-id="5d053-347">根規則 colorChooser，接聽的三個 「 色彩 + 圖形 」 規則的任何組合。</span><span class="sxs-lookup"><span data-stu-id="5d053-347">The root rule, colorChooser, which listens for any combination of the three "color + shape" rules.</span></span> <span data-ttu-id="5d053-348">以任何順序，並在任何數量的只是其中所有三個可說是圖形。</span><span class="sxs-lookup"><span data-stu-id="5d053-348">The shapes can be said in any order and in any amount from just one to all three.</span></span> <span data-ttu-id="5d053-349">這是唯一的規則會接聽該通訊埠，因為它已指定為初始中的檔案頂端的根規則&lt;文法&gt;標記。</span><span class="sxs-lookup"><span data-stu-id="5d053-349">This is the only rule that is listened for, as it's specified as the root rule at the top of the file in the initial &lt;grammar&gt; tag.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="5d053-350">建置和部署</span><span class="sxs-lookup"><span data-stu-id="5d053-350">Build and Deploy</span></span>

* <span data-ttu-id="5d053-351">重建應用程式在 Unity 中，然後建置並從 Visual Studio 體驗 HoloLens 上的應用程式部署。</span><span class="sxs-lookup"><span data-stu-id="5d053-351">Rebuild the application in Unity, then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="5d053-352">關閉 [調整] 方塊中的使用空中點選手勢。</span><span class="sxs-lookup"><span data-stu-id="5d053-352">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="5d053-353">注視太空人 jetpack，並執行空中點選手勢。</span><span class="sxs-lookup"><span data-stu-id="5d053-353">Gaze at the astronaut's jetpack and perform an air-tap gesture.</span></span>
* <span data-ttu-id="5d053-354">開始讀出。</span><span class="sxs-lookup"><span data-stu-id="5d053-354">Start speaking.</span></span> <span data-ttu-id="5d053-355">**文法辨識器**會解譯您的語音，並變更色彩的辨識為基礎的圖形。</span><span class="sxs-lookup"><span data-stu-id="5d053-355">The **Grammar Recognizer** will interpret your speech and change the colors of the shapes based on the recognition.</span></span> <span data-ttu-id="5d053-356">命令的範例是 「 藍色圓形，黃色正方形 」。</span><span class="sxs-lookup"><span data-stu-id="5d053-356">An example command is "blue circle, yellow square".</span></span>
* <span data-ttu-id="5d053-357">執行以關閉工具箱 中的另一個空中點選手勢。</span><span class="sxs-lookup"><span data-stu-id="5d053-357">Perform another air-tap gesture to dismiss the toolbox.</span></span>

## <a name="the-end"></a><span data-ttu-id="5d053-358">結束</span><span class="sxs-lookup"><span data-stu-id="5d053-358">The End</span></span>

<span data-ttu-id="5d053-359">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="5d053-359">Congratulations!</span></span> <span data-ttu-id="5d053-360">您現在已完成**MR 輸入 212:語音**。</span><span class="sxs-lookup"><span data-stu-id="5d053-360">You have now completed **MR Input 212: Voice**.</span></span>

* <span data-ttu-id="5d053-361">您知道守則的語音命令。</span><span class="sxs-lookup"><span data-stu-id="5d053-361">You know the Dos and Don'ts of voice commands.</span></span>
* <span data-ttu-id="5d053-362">您已看到如何工具提示用來讓使用者知道的語音命令。</span><span class="sxs-lookup"><span data-stu-id="5d053-362">You saw how tooltips were employed to make users aware of voice commands.</span></span>
* <span data-ttu-id="5d053-363">您看到了數種用來通知使用者的語音已聽過的意見反應。</span><span class="sxs-lookup"><span data-stu-id="5d053-363">You saw several types of feedback used to acknowledge that the user's voice was heard.</span></span>
* <span data-ttu-id="5d053-364">您知道如何切換關鍵字辨識器與聽寫辨識器，以及這兩項功能如何了解和解譯您的聲音。</span><span class="sxs-lookup"><span data-stu-id="5d053-364">You know how to switch between the Keyword Recognizer and the Dictation Recognizer, and how these two features understand and interpret your voice.</span></span>
* <span data-ttu-id="5d053-365">您已了解如何使用 語音辨識應用程式中的 SRGS 檔及文法辨識器。</span><span class="sxs-lookup"><span data-stu-id="5d053-365">You learned how to use an SRGS file and the Grammar Recognizer for speech recognition in your application.</span></span>
