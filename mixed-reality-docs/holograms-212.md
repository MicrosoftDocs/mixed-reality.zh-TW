---
title: MR 輸入 212-語音
description: 請遵循使用 Unity、Visual Studio 和 HoloLens 進行的編碼逐步解說，以瞭解語音概念的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit-unity、學院、教學課程、語音
ms.openlocfilehash: 9db503ea4c7db9a3eb272ad9663024ca3a407dda
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434595"
---
>[!NOTE]
><span data-ttu-id="756f3-104">混合現實學術教學課程的設計是使用 HoloLens （第1代）和混合現實的沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="756f3-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="756f3-105">因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="756f3-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="756f3-106">這些教學課程 **_不_** 會以最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="756f3-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="756f3-107">系統會保留這些資訊，以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="756f3-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="756f3-108">HoloLens 2 已張貼[一系列新的教學](mrlearning-base.md)課程。</span><span class="sxs-lookup"><span data-stu-id="756f3-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-input-212-voice"></a><span data-ttu-id="756f3-109">MR 輸入212：語音</span><span class="sxs-lookup"><span data-stu-id="756f3-109">MR Input 212: Voice</span></span>

<span data-ttu-id="756f3-110">[語音輸入](voice-input.md)可讓我們以另一種方式與我們的全息影像互動。</span><span class="sxs-lookup"><span data-stu-id="756f3-110">[Voice input](voice-input.md) gives us another way to interact with our holograms.</span></span> <span data-ttu-id="756f3-111">語音命令以非常自然且簡單的方式工作。</span><span class="sxs-lookup"><span data-stu-id="756f3-111">Voice commands work in a very natural and easy way.</span></span> <span data-ttu-id="756f3-112">設計您的語音命令，使其成為：</span><span class="sxs-lookup"><span data-stu-id="756f3-112">Design your voice commands so that they are:</span></span>

* <span data-ttu-id="756f3-113">自然災害</span><span class="sxs-lookup"><span data-stu-id="756f3-113">Natural</span></span>
* <span data-ttu-id="756f3-114">容易記住</span><span class="sxs-lookup"><span data-stu-id="756f3-114">Easy to remember</span></span>
* <span data-ttu-id="756f3-115">適當的內容</span><span class="sxs-lookup"><span data-stu-id="756f3-115">Context appropriate</span></span>
* <span data-ttu-id="756f3-116">與相同內容中的其他選項有充分的區別</span><span class="sxs-lookup"><span data-stu-id="756f3-116">Sufficiently distinct from other options within the same context</span></span>

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

<span data-ttu-id="756f3-117">在[MR 基本概念 101](holograms-101.md)中，我們使用 KeywordRecognizer 來建立兩個簡單的語音命令。</span><span class="sxs-lookup"><span data-stu-id="756f3-117">In [MR Basics 101](holograms-101.md), we used the KeywordRecognizer to build two simple voice commands.</span></span> <span data-ttu-id="756f3-118">在 MR 輸入212中，我們將深入探討並瞭解如何：</span><span class="sxs-lookup"><span data-stu-id="756f3-118">In MR Input 212, we'll dive deeper and learn how to:</span></span>

* <span data-ttu-id="756f3-119">設計針對 HoloLens 語音引擎優化的語音命令。</span><span class="sxs-lookup"><span data-stu-id="756f3-119">Design voice commands that are optimized for the HoloLens speech engine.</span></span>
* <span data-ttu-id="756f3-120">讓使用者知道有哪些語音命令可供使用。</span><span class="sxs-lookup"><span data-stu-id="756f3-120">Make the user aware of what voice commands are available.</span></span>
* <span data-ttu-id="756f3-121">承認我們聽到了使用者的語音命令。</span><span class="sxs-lookup"><span data-stu-id="756f3-121">Acknowledge that we've heard the user's voice command.</span></span>
* <span data-ttu-id="756f3-122">使用聽寫辨識器來瞭解使用者所說的意義。</span><span class="sxs-lookup"><span data-stu-id="756f3-122">Understand what the user is saying, using a Dictation Recognizer.</span></span>
* <span data-ttu-id="756f3-123">使用文法辨識器，根據 SRGS 或語音辨識文法規格（file）接聽命令。</span><span class="sxs-lookup"><span data-stu-id="756f3-123">Use a Grammar Recognizer to listen for commands based on an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

<span data-ttu-id="756f3-124">在本課程中，我們將重新探討 Model Explorer，我們在[Mr 輸入 210](holograms-210.md)和[mr 輸入 211](holograms-211.md)中建立。</span><span class="sxs-lookup"><span data-stu-id="756f3-124">In this course, we'll revisit Model Explorer, which we built in [MR Input 210](holograms-210.md) and [MR Input 211](holograms-211.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="756f3-125">下列各章節所內嵌的影片，都是使用舊版 Unity 和混合現實工具組錄製的。</span><span class="sxs-lookup"><span data-stu-id="756f3-125">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="756f3-126">雖然逐步指示是正確且最新的，但您可能會在已過期的對應影片中看到腳本和視覺效果。</span><span class="sxs-lookup"><span data-stu-id="756f3-126">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="756f3-127">影片仍包含在 posterity 中，因為涵蓋的概念仍適用。</span><span class="sxs-lookup"><span data-stu-id="756f3-127">The videos remain included for posterity and because the concepts covered still apply.</span></span>


## <a name="device-support"></a><span data-ttu-id="756f3-128">裝置支援</span><span class="sxs-lookup"><span data-stu-id="756f3-128">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="756f3-129">粗</span><span class="sxs-lookup"><span data-stu-id="756f3-129">Course</span></span></th><th style="width:150px"> <span data-ttu-id="756f3-130"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="756f3-130"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="756f3-131"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="756f3-131"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="756f3-132">MR 輸入212：語音</span><span class="sxs-lookup"><span data-stu-id="756f3-132">MR Input 212: Voice</span></span></td><td style="text-align: center;"> <span data-ttu-id="756f3-133">✔️</span><span class="sxs-lookup"><span data-stu-id="756f3-133">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="756f3-134">✔️</span><span class="sxs-lookup"><span data-stu-id="756f3-134">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="756f3-135">開始之前</span><span class="sxs-lookup"><span data-stu-id="756f3-135">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="756f3-136">必要條件</span><span class="sxs-lookup"><span data-stu-id="756f3-136">Prerequisites</span></span>

* <span data-ttu-id="756f3-137">[已安裝正確工具](install-the-tools.md)的 WINDOWS 10 電腦。</span><span class="sxs-lookup"><span data-stu-id="756f3-137">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="756f3-138">一些基本C#的程式設計能力。</span><span class="sxs-lookup"><span data-stu-id="756f3-138">Some basic C# programming ability.</span></span>
* <span data-ttu-id="756f3-139">您應已完成[MR 基本概念 101](holograms-101.md)。</span><span class="sxs-lookup"><span data-stu-id="756f3-139">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="756f3-140">您應已完成[MR 輸入 210](holograms-210.md)。</span><span class="sxs-lookup"><span data-stu-id="756f3-140">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="756f3-141">您應已完成[MR 輸入 211](holograms-211.md)。</span><span class="sxs-lookup"><span data-stu-id="756f3-141">You should have completed [MR Input 211](holograms-211.md).</span></span>
* <span data-ttu-id="756f3-142">[為開發設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="756f3-142">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="756f3-143">專案檔案</span><span class="sxs-lookup"><span data-stu-id="756f3-143">Project files</span></span>

* <span data-ttu-id="756f3-144">下載專案[所需的](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip)檔案。</span><span class="sxs-lookup"><span data-stu-id="756f3-144">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) required by the project.</span></span> <span data-ttu-id="756f3-145">需要 Unity 2017.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="756f3-145">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="756f3-146">將檔案取消封存至您的桌面或其他容易到達的位置。</span><span class="sxs-lookup"><span data-stu-id="756f3-146">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="756f3-147">如果您想要在下載之前查看原始程式碼，可以[在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice)取得。</span><span class="sxs-lookup"><span data-stu-id="756f3-147">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="756f3-148">勘誤和注意事項</span><span class="sxs-lookup"><span data-stu-id="756f3-148">Errata and Notes</span></span>

* <span data-ttu-id="756f3-149">必須在 Visual Studio 下的 [工具]-[> 選項]-[> 的偵錯工具] 中停用（*取消*核取） [啟用 Just My Code]，才能在程式碼中叫用中斷點。</span><span class="sxs-lookup"><span data-stu-id="756f3-149">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="756f3-150">Unity 設定</span><span class="sxs-lookup"><span data-stu-id="756f3-150">Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="756f3-151">指示</span><span class="sxs-lookup"><span data-stu-id="756f3-151">Instructions</span></span>

1. <span data-ttu-id="756f3-152">啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="756f3-152">Start Unity.</span></span>
2. <span data-ttu-id="756f3-153">選取 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="756f3-153">Select **Open**.</span></span>
3. <span data-ttu-id="756f3-154">流覽至您先前取消封存的**HolographicAcademy-全息-212-Voice**資料夾。</span><span class="sxs-lookup"><span data-stu-id="756f3-154">Navigate to the **HolographicAcademy-Holograms-212-Voice** folder you previously un-archived.</span></span>
4. <span data-ttu-id="756f3-155">尋找並選取 [**開始**/**模型瀏覽器**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="756f3-155">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="756f3-156">按一下 [**選取資料夾**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="756f3-156">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="756f3-157">在 [**專案**] 面板中，展開 [**幕後**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="756f3-157">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="756f3-158">按兩下 [ **ModelExplorer**場景]，將其載入 Unity。</span><span class="sxs-lookup"><span data-stu-id="756f3-158">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="756f3-159">建置</span><span class="sxs-lookup"><span data-stu-id="756f3-159">Building</span></span>

1. <span data-ttu-id="756f3-160">在 Unity 中，選取 [檔案] **> [組建設定**]。</span><span class="sxs-lookup"><span data-stu-id="756f3-160">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="756f3-161">如果 [**場景/ModelExplorer** ] 未在 [組建] 的**場景**中列出，請按一下 [**新增開啟場景**] 以加入場景。</span><span class="sxs-lookup"><span data-stu-id="756f3-161">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="756f3-162">如果您是特別針對 HoloLens 進行開發，請將**目標裝置**設定為**hololens**。</span><span class="sxs-lookup"><span data-stu-id="756f3-162">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="756f3-163">否則，請將它保留在**任何裝置**上。</span><span class="sxs-lookup"><span data-stu-id="756f3-163">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="756f3-164">確定 [**組建類型**] 設定為 [ **D3D** ]，並將 [ **sdk** ] 設定為 [**已安裝最新**版本] （應該是 SDK 16299 或更新版本）。</span><span class="sxs-lookup"><span data-stu-id="756f3-164">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="756f3-165">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="756f3-165">Click **Build**.</span></span>
6. <span data-ttu-id="756f3-166">建立名為 "App" 的**新資料夾**。</span><span class="sxs-lookup"><span data-stu-id="756f3-166">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="756f3-167">按一下 [**應用程式**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="756f3-167">Single click the **App** folder.</span></span>
8. <span data-ttu-id="756f3-168">按下 [**選取資料夾**]，Unity 就會開始建立 Visual Studio 的專案。</span><span class="sxs-lookup"><span data-stu-id="756f3-168">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="756f3-169">當 Unity 完成時，將會出現 [檔案瀏覽器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="756f3-169">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="756f3-170">開啟**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="756f3-170">Open the **App** folder.</span></span>
2. <span data-ttu-id="756f3-171">開啟**ModelExplorer Visual Studio 解決方案**。</span><span class="sxs-lookup"><span data-stu-id="756f3-171">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="756f3-172">如果部署至 HoloLens：</span><span class="sxs-lookup"><span data-stu-id="756f3-172">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="756f3-173">使用 Visual Studio 中的頂端工具列，將目標從 [調試] 變更為 [**發行**]，將 [從 ARM] 變更為**x86**。</span><span class="sxs-lookup"><span data-stu-id="756f3-173">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="756f3-174">按一下 [本機電腦] 按鈕旁的下拉式箭號，然後選取 [**遠端電腦**]。</span><span class="sxs-lookup"><span data-stu-id="756f3-174">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="756f3-175">輸入**您的 HoloLens 裝置 IP 位址**，並將驗證模式設定為 **[通用（未加密的通訊協定）** ]。</span><span class="sxs-lookup"><span data-stu-id="756f3-175">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="756f3-176">按一下 [**選取**]。</span><span class="sxs-lookup"><span data-stu-id="756f3-176">Click **Select**.</span></span> <span data-ttu-id="756f3-177">如果您不知道您的裝置 IP 位址，請查看 [設定] [ **> Network & Internet] > [Advanced Options**]。</span><span class="sxs-lookup"><span data-stu-id="756f3-177">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="756f3-178">在頂端功能表列中，按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="756f3-178">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="756f3-179">如果這是您第一次部署至您的裝置，您必須將[它與 Visual Studio 配對](using-visual-studio.md#pairing-your-device)。</span><span class="sxs-lookup"><span data-stu-id="756f3-179">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>
5. <span data-ttu-id="756f3-180">應用程式部署完成後，請使用**select 手勢**來關閉**Fitbox** 。</span><span class="sxs-lookup"><span data-stu-id="756f3-180">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="756f3-181">如果部署到沉浸式耳機：</span><span class="sxs-lookup"><span data-stu-id="756f3-181">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="756f3-182">使用 Visual Studio 中的頂端工具列，將目標從 [調試] 變更為 [**發行**]，將 [從 ARM] 變更為**x64**。</span><span class="sxs-lookup"><span data-stu-id="756f3-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="756f3-183">請確定 [部署目標] 設定為 [**本機電腦**]。</span><span class="sxs-lookup"><span data-stu-id="756f3-183">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="756f3-184">在頂端功能表列中，按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="756f3-184">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="756f3-185">應用程式部署完成後，請藉由在動作控制器上提取觸發程式來關閉**Fitbox** 。</span><span class="sxs-lookup"><span data-stu-id="756f3-185">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="756f3-186">在 [Visual Studio 錯誤] 面板中，您可能會注意到一些紅色錯誤。</span><span class="sxs-lookup"><span data-stu-id="756f3-186">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="756f3-187">可以放心地忽略它們。</span><span class="sxs-lookup"><span data-stu-id="756f3-187">It is safe to ignore them.</span></span> <span data-ttu-id="756f3-188">切換至 [輸出] 面板以查看實際的組建進度。</span><span class="sxs-lookup"><span data-stu-id="756f3-188">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="756f3-189">[輸出] 面板中的錯誤會要求您進行修正（最常見的原因是腳本錯誤）。</span><span class="sxs-lookup"><span data-stu-id="756f3-189">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---awareness"></a><span data-ttu-id="756f3-190">第1章-認知</span><span class="sxs-lookup"><span data-stu-id="756f3-190">Chapter 1 - Awareness</span></span>

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a><span data-ttu-id="756f3-191">目標</span><span class="sxs-lookup"><span data-stu-id="756f3-191">Objectives</span></span>

* <span data-ttu-id="756f3-192">瞭解語音命令設計的**Dos 和非注意事項**。</span><span class="sxs-lookup"><span data-stu-id="756f3-192">Learn the **Dos and Don'ts** of voice command design.</span></span>
* <span data-ttu-id="756f3-193">使用**KeywordRecognizer**來新增注視型語音命令。</span><span class="sxs-lookup"><span data-stu-id="756f3-193">Use **KeywordRecognizer** to add gaze based voice commands.</span></span>
* <span data-ttu-id="756f3-194">使用游標**意見**反應讓使用者知道語音命令。</span><span class="sxs-lookup"><span data-stu-id="756f3-194">Make users aware of voice commands using cursor **feedback**.</span></span>

### <a name="voice-command-design"></a><span data-ttu-id="756f3-195">語音命令設計</span><span class="sxs-lookup"><span data-stu-id="756f3-195">Voice Command Design</span></span>

<span data-ttu-id="756f3-196">在本章中，您將瞭解如何設計語音命令。</span><span class="sxs-lookup"><span data-stu-id="756f3-196">In this chapter, you'll learn about designing voice commands.</span></span> <span data-ttu-id="756f3-197">建立語音命令的時機：</span><span class="sxs-lookup"><span data-stu-id="756f3-197">When creating voice commands:</span></span>

#### <a name="do"></a><span data-ttu-id="756f3-198">DO</span><span class="sxs-lookup"><span data-stu-id="756f3-198">DO</span></span>

* <span data-ttu-id="756f3-199">建立簡潔的命令。</span><span class="sxs-lookup"><span data-stu-id="756f3-199">Create concise commands.</span></span> <span data-ttu-id="756f3-200">您不想使用 *[播放目前選取的影片]* ，因為該命令並不簡潔，而且使用者很容易就會忘記。</span><span class="sxs-lookup"><span data-stu-id="756f3-200">You don't want to use *"Play the currently selected video"*, because that command is not concise and would easily be forgotten by the user.</span></span> <span data-ttu-id="756f3-201">相反地，您應該使用：「*播放影片*」，因為它很簡潔，而且有多個音節。</span><span class="sxs-lookup"><span data-stu-id="756f3-201">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="756f3-202">使用簡單的詞彙。</span><span class="sxs-lookup"><span data-stu-id="756f3-202">Use a simple vocabulary.</span></span> <span data-ttu-id="756f3-203">請一律嘗試使用簡單的字詞和片語，讓使用者輕鬆探索並記住。</span><span class="sxs-lookup"><span data-stu-id="756f3-203">Always try to use common words and phrases that are easy for the user to discover and remember.</span></span> <span data-ttu-id="756f3-204">例如，如果您的應用程式具有可從 view 顯示或隱藏的記事物件，您就不會使用 " *Show 牌子"* 命令，因為 "牌子" 是很少使用的詞彙。</span><span class="sxs-lookup"><span data-stu-id="756f3-204">For example, if your application had a note object that could be displayed or hidden from view, you would not use the command *"Show Placard"*, because "placard" is a rarely used term.</span></span> <span data-ttu-id="756f3-205">相反地，您會使用命令：「 *Show Note*」，在您的應用程式中顯示便箋。</span><span class="sxs-lookup"><span data-stu-id="756f3-205">Instead, you would use the command: *"Show Note"*, to reveal the note in your application.</span></span>
* <span data-ttu-id="756f3-206">保持一致。</span><span class="sxs-lookup"><span data-stu-id="756f3-206">Be consistent.</span></span> <span data-ttu-id="756f3-207">語音命令在您的應用程式中應該保持一致。</span><span class="sxs-lookup"><span data-stu-id="756f3-207">Voice commands should be kept consistent across your application.</span></span> <span data-ttu-id="756f3-208">假設您的應用程式中有兩個場景，而這兩個場景都包含一個用來關閉應用程式的按鈕。</span><span class="sxs-lookup"><span data-stu-id="756f3-208">Imagine that you have two scenes in your application and both scenes contain a button for closing the application.</span></span> <span data-ttu-id="756f3-209">如果第一個場景使用「結束」*命令來觸發*按鈕，但第二個場景使用「*關閉應用程式*」命令，那麼使用者就會變得非常困惑。</span><span class="sxs-lookup"><span data-stu-id="756f3-209">If the first scene used the command *"Exit"* to trigger the button, but the second scene used the command *"Close App"*, then the user is going to get very confused.</span></span> <span data-ttu-id="756f3-210">如果相同的功能跨多個場景持續存在，則應該使用相同的語音命令來觸發它。</span><span class="sxs-lookup"><span data-stu-id="756f3-210">If the same functionality persists across multiple scenes, then the same voice command should be used to trigger it.</span></span>

#### <a name="dont"></a><span data-ttu-id="756f3-211">不要</span><span class="sxs-lookup"><span data-stu-id="756f3-211">DON'T</span></span>

* <span data-ttu-id="756f3-212">使用單一的音節命令。</span><span class="sxs-lookup"><span data-stu-id="756f3-212">Use single syllable commands.</span></span> <span data-ttu-id="756f3-213">例如，如果您要建立語音命令來播放影片，應該避免使用簡單的命令「*播放*」，因為它只是單一的音節，而且系統可能會輕易地錯過。</span><span class="sxs-lookup"><span data-stu-id="756f3-213">As an example, if you were creating a voice command to play a video, you should avoid using the simple command *"Play"*, as it is only a single syllable and could easily be missed by the system.</span></span> <span data-ttu-id="756f3-214">相反地，您應該使用：「*播放影片*」，因為它很簡潔，而且有多個音節。</span><span class="sxs-lookup"><span data-stu-id="756f3-214">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="756f3-215">使用系統命令。</span><span class="sxs-lookup"><span data-stu-id="756f3-215">Use system commands.</span></span> <span data-ttu-id="756f3-216">系統會保留 *"Select"* 命令，以觸發目前焦點物件的攻絲事件。</span><span class="sxs-lookup"><span data-stu-id="756f3-216">The *"Select"* command is reserved by the system to trigger a Tap event for the currently focused object.</span></span> <span data-ttu-id="756f3-217">請勿在關鍵字或片語中重複使用 *"Select"* 命令，因為它可能無法如您預期般運作。</span><span class="sxs-lookup"><span data-stu-id="756f3-217">Do not re-use the *"Select"* command in a keyword or phrase, as it might not work as you expect.</span></span> <span data-ttu-id="756f3-218">例如，如果在應用程式中選取 cube 的語音命令是「*選取 cube*」，但使用者在從未提到命令時查看球體，則會改為選取球體。</span><span class="sxs-lookup"><span data-stu-id="756f3-218">For example, if the voice command for selecting a cube in your application was *"Select cube"*, but the user was looking at a sphere when they uttered the command, then the sphere would be selected instead.</span></span> <span data-ttu-id="756f3-219">同樣地，應用程式行命令也會啟用語音。</span><span class="sxs-lookup"><span data-stu-id="756f3-219">Similarly app bar commands are voice enabled.</span></span> <span data-ttu-id="756f3-220">請勿在您的 CoreWindow 視圖中使用下列語音命令：</span><span class="sxs-lookup"><span data-stu-id="756f3-220">Don't use the following speech commands in your CoreWindow View:</span></span>
    1. <span data-ttu-id="756f3-221">回去</span><span class="sxs-lookup"><span data-stu-id="756f3-221">Go Back</span></span>
    2. <span data-ttu-id="756f3-222">捲軸工具</span><span class="sxs-lookup"><span data-stu-id="756f3-222">Scroll Tool</span></span>
    3. <span data-ttu-id="756f3-223">縮放工具</span><span class="sxs-lookup"><span data-stu-id="756f3-223">Zoom Tool</span></span>
    4. <span data-ttu-id="756f3-224">拖曳工具</span><span class="sxs-lookup"><span data-stu-id="756f3-224">Drag Tool</span></span>
    5. <span data-ttu-id="756f3-225">Adjust</span><span class="sxs-lookup"><span data-stu-id="756f3-225">Adjust</span></span>
    6. <span data-ttu-id="756f3-226">移除</span><span class="sxs-lookup"><span data-stu-id="756f3-226">Remove</span></span>
* <span data-ttu-id="756f3-227">使用類似的聲音。</span><span class="sxs-lookup"><span data-stu-id="756f3-227">Use similar sounds.</span></span> <span data-ttu-id="756f3-228">請嘗試避免使用 rhyme 的語音命令。</span><span class="sxs-lookup"><span data-stu-id="756f3-228">Try to avoid using voice commands that rhyme.</span></span> <span data-ttu-id="756f3-229">如果您的購物應用程式支援「*顯示存放區*」和「*顯示更多*」做為語音命令，則您會想要在另一個使用中時停用其中一個命令。</span><span class="sxs-lookup"><span data-stu-id="756f3-229">If you had a shopping application which supported *"Show Store"* and *"Show More"* as voice commands, then you would want to disable one of the commands while the other was in use.</span></span> <span data-ttu-id="756f3-230">例如，您可以使用 [*顯示存放區]* 按鈕來開啟存放區，然後在顯示商店時停用該命令，讓 [*顯示更多]* 命令可以用於流覽。</span><span class="sxs-lookup"><span data-stu-id="756f3-230">For example, you could use the *"Show Store"* button to open the store, and then disable that command when the store was displayed so that the *"Show More"* command could be used for browsing.</span></span>

### <a name="instructions"></a><span data-ttu-id="756f3-231">指示</span><span class="sxs-lookup"><span data-stu-id="756f3-231">Instructions</span></span>

* <span data-ttu-id="756f3-232">在**Unity 的 [** 階層] 面板中，使用 [搜尋] 工具來尋找**holoComm_screen_mesh**物件。</span><span class="sxs-lookup"><span data-stu-id="756f3-232">In Unity's **Hierarchy** panel, use the search tool to find the **holoComm_screen_mesh** object.</span></span>
* <span data-ttu-id="756f3-233">按兩下 [ **holoComm_screen_mesh** ] 物件，在**場景**中進行查看。</span><span class="sxs-lookup"><span data-stu-id="756f3-233">Double-click on the **holoComm_screen_mesh** object to view it in the **Scene**.</span></span> <span data-ttu-id="756f3-234">這是太空人的監看式，它會回應我們的語音命令。</span><span class="sxs-lookup"><span data-stu-id="756f3-234">This is the astronaut's watch, which will respond to our voice commands.</span></span>
* <span data-ttu-id="756f3-235">在 [偵測**器**] 面板中，找出 [**語音輸入來源（腳本）** ] 元件。</span><span class="sxs-lookup"><span data-stu-id="756f3-235">In the **Inspector** panel, locate the **Speech Input Source (Script)** component.</span></span>
* <span data-ttu-id="756f3-236">展開 [**關鍵字**] 區段以查看支援的語音命令： [**開啟 Communicator**]。</span><span class="sxs-lookup"><span data-stu-id="756f3-236">Expand the **Keywords** section to see the supported voice command: **Open Communicator**.</span></span>
* <span data-ttu-id="756f3-237">按一下右側的 [齒輪]，然後選取 [**編輯腳本**]。</span><span class="sxs-lookup"><span data-stu-id="756f3-237">Click the cog to the right side, then select **Edit Script**.</span></span>
* <span data-ttu-id="756f3-238">探索**SpeechInputSource.cs**以瞭解它如何使用**KeywordRecognizer**來新增語音命令。</span><span class="sxs-lookup"><span data-stu-id="756f3-238">Explore **SpeechInputSource.cs** to understand how it uses the **KeywordRecognizer** to add voice commands.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="756f3-239">組建和部署</span><span class="sxs-lookup"><span data-stu-id="756f3-239">Build and Deploy</span></span>

* <span data-ttu-id="756f3-240">在 Unity 中，使用檔案 **> 組建設定**來重建應用程式。</span><span class="sxs-lookup"><span data-stu-id="756f3-240">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="756f3-241">開啟**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="756f3-241">Open the **App** folder.</span></span>
* <span data-ttu-id="756f3-242">開啟**ModelExplorer Visual Studio 解決方案**。</span><span class="sxs-lookup"><span data-stu-id="756f3-242">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="756f3-243">（如果您已經在安裝期間于 Visual Studio 內建立/部署此專案，則可以開啟 VS 的實例，然後在出現提示時按一下 [全部重載]）。</span><span class="sxs-lookup"><span data-stu-id="756f3-243">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>

* <span data-ttu-id="756f3-244">在 Visual Studio 中，按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="756f3-244">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="756f3-245">將應用程式部署至 HoloLens 之後，請[使用 [點按] 手勢關閉](gaze-and-commit.md#composite-gestures)[調整] 方塊。</span><span class="sxs-lookup"><span data-stu-id="756f3-245">After the application deploys to the HoloLens, dismiss the fit box using the [air-tap](gaze-and-commit.md#composite-gestures) gesture.</span></span>
* <span data-ttu-id="756f3-246">觀賞太空人的監看。</span><span class="sxs-lookup"><span data-stu-id="756f3-246">Gaze at the astronaut's watch.</span></span>
* <span data-ttu-id="756f3-247">當監看式具有焦點時，請確認游標變更為麥克風。</span><span class="sxs-lookup"><span data-stu-id="756f3-247">When the watch has focus, verify that the cursor changes to a microphone.</span></span> <span data-ttu-id="756f3-248">這會提供應用程式接聽語音命令的意見反應。</span><span class="sxs-lookup"><span data-stu-id="756f3-248">This provides feedback that the application is listening for voice commands.</span></span>
* <span data-ttu-id="756f3-249">確認 [監看式] 上出現工具提示。</span><span class="sxs-lookup"><span data-stu-id="756f3-249">Verify that a tooltip appears on the watch.</span></span> <span data-ttu-id="756f3-250">這可協助使用者探索 *"Open Communicator"* 命令。</span><span class="sxs-lookup"><span data-stu-id="756f3-250">This helps users discover the *"Open Communicator"* command.</span></span>
* <span data-ttu-id="756f3-251">在監看撥雲見日時，請說「*開啟 communicator* 」以開啟 communicator 面板。</span><span class="sxs-lookup"><span data-stu-id="756f3-251">While gazing at the watch, say *"Open Communicator"* to open the communicator panel.</span></span>

## <a name="chapter-2---acknowledgement"></a><span data-ttu-id="756f3-252">第2章-通知</span><span class="sxs-lookup"><span data-stu-id="756f3-252">Chapter 2 - Acknowledgement</span></span>

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a><span data-ttu-id="756f3-253">目標</span><span class="sxs-lookup"><span data-stu-id="756f3-253">Objectives</span></span>

* <span data-ttu-id="756f3-254">使用麥克風輸入記錄訊息。</span><span class="sxs-lookup"><span data-stu-id="756f3-254">Record a message using the Microphone input.</span></span>
* <span data-ttu-id="756f3-255">提供意見反應給應用程式正在接聽其語音的使用者。</span><span class="sxs-lookup"><span data-stu-id="756f3-255">Give feedback to the user that the application is listening to their voice.</span></span>

>[!NOTE]
><span data-ttu-id="756f3-256">必須針對要從麥克風錄製的應用程式宣告**麥克風**功能。</span><span class="sxs-lookup"><span data-stu-id="756f3-256">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="756f3-257">您已在 MR 輸入212中完成這項作業，但請記住您自己的專案。</span><span class="sxs-lookup"><span data-stu-id="756f3-257">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="756f3-258">在 Unity 編輯器中，流覽至 [編輯 > 專案設定 > Player]，移至播放程式設定</span><span class="sxs-lookup"><span data-stu-id="756f3-258">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="756f3-259">按一下 [通用 Windows 平臺] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="756f3-259">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="756f3-260">在 [發佈設定 > 功能] 區段中，檢查**麥克風**功能</span><span class="sxs-lookup"><span data-stu-id="756f3-260">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="756f3-261">指示</span><span class="sxs-lookup"><span data-stu-id="756f3-261">Instructions</span></span>

* <span data-ttu-id="756f3-262">在**Unity 的 [** 階層] 面板中，確認已選取 [ **holoComm_screen_mesh** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="756f3-262">In Unity's **Hierarchy** panel, verify that the **holoComm_screen_mesh** object is selected.</span></span>
* <span data-ttu-id="756f3-263">在 [偵測**器**] 面板中，尋找 [**太空人 Watch （腳本）]** 元件。</span><span class="sxs-lookup"><span data-stu-id="756f3-263">In the **Inspector** panel, find the **Astronaut Watch (Script)** component.</span></span>
* <span data-ttu-id="756f3-264">按一下已設定為**Communicator Prefab**屬性值的小型藍色 cube。</span><span class="sxs-lookup"><span data-stu-id="756f3-264">Click on the small, blue cube which is set as the value of the **Communicator Prefab** property.</span></span>
* <span data-ttu-id="756f3-265">在 [**專案**] 面板中， **Communicator** prefab 現在應該會有焦點。</span><span class="sxs-lookup"><span data-stu-id="756f3-265">In the **Project** panel, the **Communicator** prefab should now have focus.</span></span>
* <span data-ttu-id="756f3-266">按一下 [**專案**] 面板中的 [ **Communicator** ] prefab，以在偵測**器**中查看其元件。</span><span class="sxs-lookup"><span data-stu-id="756f3-266">Click on the **Communicator** prefab in the **Project** panel to view its components in the **Inspector**.</span></span>
* <span data-ttu-id="756f3-267">查看**麥克風管理員（腳本）** 元件，這可讓我們記錄使用者的聲音。</span><span class="sxs-lookup"><span data-stu-id="756f3-267">Look at the **Microphone Manager (Script)** component, this will allow us to record the user's voice.</span></span>
* <span data-ttu-id="756f3-268">請注意， **Communicator**物件具有用來回應 [**傳送訊息**] 命令的**語音輸入處理常式（腳本）** 元件。</span><span class="sxs-lookup"><span data-stu-id="756f3-268">Notice that the **Communicator** object has a **Speech Input Handler (Script)** component for responding to the **Send Message** command.</span></span>
* <span data-ttu-id="756f3-269">查看**Communicator （Script）** 元件，然後按兩下腳本以在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="756f3-269">Look at the **Communicator (Script)** component and double-click on the script to open it in Visual Studio.</span></span>

<span data-ttu-id="756f3-270">Communicator.cs 會負責在 communicator 裝置上設定適當的按鈕狀態。</span><span class="sxs-lookup"><span data-stu-id="756f3-270">Communicator.cs is responsible for setting the proper button states on the communicator device.</span></span> <span data-ttu-id="756f3-271">這可讓我們的使用者記錄郵件、播放訊息，並將訊息傳送至太空人。</span><span class="sxs-lookup"><span data-stu-id="756f3-271">This will allow our users to record a message, play it back, and send the message to the astronaut.</span></span> <span data-ttu-id="756f3-272">它也會啟動和停止動畫 wave 表單，以向使用者表示其聲音已聽到。</span><span class="sxs-lookup"><span data-stu-id="756f3-272">It will also start and stop an animated wave form, to acknowledge to the user that their voice was heard.</span></span>

* <span data-ttu-id="756f3-273">在**Communicator.cs**中，從**Start**方法刪除下列幾行（81和82）。</span><span class="sxs-lookup"><span data-stu-id="756f3-273">In **Communicator.cs**, delete the following lines (81 and 82) from the **Start** method.</span></span> <span data-ttu-id="756f3-274">這會啟用 communicator 上的 [記錄] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="756f3-274">This will enable the 'Record' button on the communicator.</span></span>

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a><span data-ttu-id="756f3-275">組建和部署</span><span class="sxs-lookup"><span data-stu-id="756f3-275">Build and Deploy</span></span>

* <span data-ttu-id="756f3-276">在 Visual Studio 中，重建您的應用程式並部署至裝置。</span><span class="sxs-lookup"><span data-stu-id="756f3-276">In Visual Studio, rebuild your application and deploy to the device.</span></span>
* <span data-ttu-id="756f3-277">看一下太空人的監看，並說「*開啟 communicator* 」來顯示 Communicator。</span><span class="sxs-lookup"><span data-stu-id="756f3-277">Gaze at the astronaut's watch and say *"Open Communicator"* to show the communicator.</span></span>
* <span data-ttu-id="756f3-278">按 [**錄製**] 按鈕（麥克風）開始錄製太空人的口頭訊息。</span><span class="sxs-lookup"><span data-stu-id="756f3-278">Press the **Record** button (microphone) to start recording a verbal message for the astronaut.</span></span>
* <span data-ttu-id="756f3-279">開始說話，並確認 wave 動畫在 communicator 上播放，這會提供意見反應給使用者聽到語音的聲音。</span><span class="sxs-lookup"><span data-stu-id="756f3-279">Start speaking, and verify that the wave animation plays on the communicator, which provides feedback to the user that their voice is heard.</span></span>
* <span data-ttu-id="756f3-280">按下 [**停止**] 按鈕（左正方形），然後確認 wave 動畫停止執行。</span><span class="sxs-lookup"><span data-stu-id="756f3-280">Press the **Stop** button (left square), and verify that the wave animation stops running.</span></span>
* <span data-ttu-id="756f3-281">按下 [**播放**] 按鈕（直角三角形）來播放錄製的訊息，並在裝置上聆聽。</span><span class="sxs-lookup"><span data-stu-id="756f3-281">Press the **Play** button (right triangle) to play back the recorded message and hear it on the device.</span></span>
* <span data-ttu-id="756f3-282">按下 [**停止**] 按鈕（右方形）以停止播放已錄製的訊息。</span><span class="sxs-lookup"><span data-stu-id="756f3-282">Press the **Stop** button (right square) to stop playback of the recorded message.</span></span>
* <span data-ttu-id="756f3-283">說出「*傳送訊息*」，關閉 communicator 並接收來自太空人的「收到的訊息」回應。</span><span class="sxs-lookup"><span data-stu-id="756f3-283">Say *"Send Message"* to close the communicator and receive a 'Message Received' response from the astronaut.</span></span>

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a><span data-ttu-id="756f3-284">第3章-瞭解和聽寫辨識器</span><span class="sxs-lookup"><span data-stu-id="756f3-284">Chapter 3 - Understanding and the Dictation Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a><span data-ttu-id="756f3-285">目標</span><span class="sxs-lookup"><span data-stu-id="756f3-285">Objectives</span></span>

* <span data-ttu-id="756f3-286">使用聽寫辨識器將使用者的語音轉換成文字。</span><span class="sxs-lookup"><span data-stu-id="756f3-286">Use the Dictation Recognizer to convert the user's speech to text.</span></span>
* <span data-ttu-id="756f3-287">在 communicator 中顯示聽寫辨識器的假設和最終結果。</span><span class="sxs-lookup"><span data-stu-id="756f3-287">Show the Dictation Recognizer's hypothesized and final results in the communicator.</span></span>

<span data-ttu-id="756f3-288">在本章中，我們將使用聽寫辨識器來建立太空人的訊息。</span><span class="sxs-lookup"><span data-stu-id="756f3-288">In this chapter, we'll use the Dictation Recognizer to create a message for the astronaut.</span></span> <span data-ttu-id="756f3-289">使用聽寫辨識器時，請記住：</span><span class="sxs-lookup"><span data-stu-id="756f3-289">When using the Dictation Recognizer, keep in mind that:</span></span>

* <span data-ttu-id="756f3-290">您必須連接到 WiFi，聽寫辨識器才能正常執行。</span><span class="sxs-lookup"><span data-stu-id="756f3-290">You must be connected to WiFi for the Dictation Recognizer to work.</span></span>
* <span data-ttu-id="756f3-291">在設定的一段時間後發生超時。</span><span class="sxs-lookup"><span data-stu-id="756f3-291">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="756f3-292">有兩個要注意的超時：</span><span class="sxs-lookup"><span data-stu-id="756f3-292">There are two timeouts to be aware of:</span></span>
  * <span data-ttu-id="756f3-293">如果辨識器啟動且未在前五秒聽到任何音訊，則會超時。</span><span class="sxs-lookup"><span data-stu-id="756f3-293">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
  * <span data-ttu-id="756f3-294">如果辨識器已指定結果，但接著會聽到24秒的無聲，則會超時。</span><span class="sxs-lookup"><span data-stu-id="756f3-294">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>
* <span data-ttu-id="756f3-295">一次只能執行一種類型的辨識器（關鍵字或聽寫）。</span><span class="sxs-lookup"><span data-stu-id="756f3-295">Only one type of recognizer (Keyword or Dictation) can run at a time.</span></span>

>[!NOTE]
><span data-ttu-id="756f3-296">必須針對要從麥克風錄製的應用程式宣告**麥克風**功能。</span><span class="sxs-lookup"><span data-stu-id="756f3-296">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="756f3-297">您已在 MR 輸入212中完成這項作業，但請記住您自己的專案。</span><span class="sxs-lookup"><span data-stu-id="756f3-297">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="756f3-298">在 Unity 編輯器中，流覽至 [編輯 > 專案設定 > Player]，移至播放程式設定</span><span class="sxs-lookup"><span data-stu-id="756f3-298">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="756f3-299">按一下 [通用 Windows 平臺] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="756f3-299">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="756f3-300">在 [發佈設定 > 功能] 區段中，檢查**麥克風**功能</span><span class="sxs-lookup"><span data-stu-id="756f3-300">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="756f3-301">指示</span><span class="sxs-lookup"><span data-stu-id="756f3-301">Instructions</span></span>

<span data-ttu-id="756f3-302">我們即將編輯**MicrophoneManager.cs**以使用聽寫辨識器。</span><span class="sxs-lookup"><span data-stu-id="756f3-302">We're going to edit **MicrophoneManager.cs** to use the Dictation Recognizer.</span></span> <span data-ttu-id="756f3-303">這就是我們要加入的內容：</span><span class="sxs-lookup"><span data-stu-id="756f3-303">This is what we'll add:</span></span>

1. <span data-ttu-id="756f3-304">按下 [**錄製] 按鈕**時，我們會**開始 DictationRecognizer**。</span><span class="sxs-lookup"><span data-stu-id="756f3-304">When the **Record button** is pressed, we'll **start the DictationRecognizer**.</span></span>
2. <span data-ttu-id="756f3-305">顯示 DictationRecognizer 瞭解的**假設**。</span><span class="sxs-lookup"><span data-stu-id="756f3-305">Show the **hypothesis** of what the DictationRecognizer understood.</span></span>
3. <span data-ttu-id="756f3-306">鎖定 DictationRecognizer 瞭解的**結果**。</span><span class="sxs-lookup"><span data-stu-id="756f3-306">Lock in the **results** of what the DictationRecognizer understood.</span></span>
4. <span data-ttu-id="756f3-307">檢查 DictationRecognizer 的是否有超時。</span><span class="sxs-lookup"><span data-stu-id="756f3-307">Check for timeouts from the DictationRecognizer.</span></span>
5. <span data-ttu-id="756f3-308">當按下 [**停止] 按鈕**或 mic 會話超時時，請**停止 DictationRecognizer**。</span><span class="sxs-lookup"><span data-stu-id="756f3-308">When the **Stop button** is pressed, or the mic session times out, **stop the DictationRecognizer**.</span></span>
6. <span data-ttu-id="756f3-309">重新開機**KeywordRecognizer**，這會接聽 [**傳送訊息**] 命令。</span><span class="sxs-lookup"><span data-stu-id="756f3-309">Restart the **KeywordRecognizer**, which will listen for the **Send Message** command.</span></span>

<span data-ttu-id="756f3-310">那就開始吧。</span><span class="sxs-lookup"><span data-stu-id="756f3-310">Let's get started.</span></span> <span data-ttu-id="756f3-311">在**MicrophoneManager.cs**中完成所有的程式碼撰寫練習，或複製並貼上完成的程式碼，如下所示：</span><span class="sxs-lookup"><span data-stu-id="756f3-311">Complete all coding exercises for 3.a in **MicrophoneManager.cs**, or copy and paste the finished code found below:</span></span>

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

### <a name="build-and-deploy"></a><span data-ttu-id="756f3-312">組建和部署</span><span class="sxs-lookup"><span data-stu-id="756f3-312">Build and Deploy</span></span>

* <span data-ttu-id="756f3-313">在 Visual Studio 中重建，並部署至您的裝置。</span><span class="sxs-lookup"><span data-stu-id="756f3-313">Rebuild in Visual Studio and deploy to your device.</span></span>
* <span data-ttu-id="756f3-314">使用 [空中] 手勢關閉 [調整] 方塊。</span><span class="sxs-lookup"><span data-stu-id="756f3-314">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="756f3-315">觀賞太空人的監看，並說出「 *Open Communicator*」。</span><span class="sxs-lookup"><span data-stu-id="756f3-315">Gaze at the astronaut's watch and say *"Open Communicator"*.</span></span>
* <span data-ttu-id="756f3-316">選取 [**錄製**] 按鈕（麥克風）以記錄您的訊息。</span><span class="sxs-lookup"><span data-stu-id="756f3-316">Select the **Record** button (microphone) to record your message.</span></span>
* <span data-ttu-id="756f3-317">開始說話。</span><span class="sxs-lookup"><span data-stu-id="756f3-317">Start speaking.</span></span> <span data-ttu-id="756f3-318">**聽寫辨識器**會解讀您的語音，並在 communicator 中顯示假設的文字。</span><span class="sxs-lookup"><span data-stu-id="756f3-318">The **Dictation Recognizer** will interpret your speech and show the hypothesized text in the communicator.</span></span>
* <span data-ttu-id="756f3-319">當您錄製訊息時，請嘗試說出「*傳送訊息*」。</span><span class="sxs-lookup"><span data-stu-id="756f3-319">Try saying *"Send Message"* while you are recording a message.</span></span> <span data-ttu-id="756f3-320">請注意，**關鍵字辨識器**不會回應，因為**聽寫辨識器**仍在作用中。</span><span class="sxs-lookup"><span data-stu-id="756f3-320">Notice that the **Keyword Recognizer** does not respond because the **Dictation Recognizer** is still active.</span></span>
* <span data-ttu-id="756f3-321">停止說話幾秒鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="756f3-321">Stop speaking for a few seconds.</span></span> <span data-ttu-id="756f3-322">監看聽寫辨識器如何完成其假設，並顯示最終結果。</span><span class="sxs-lookup"><span data-stu-id="756f3-322">Watch as the Dictation Recognizer completes its hypothesis and shows the final result.</span></span>
* <span data-ttu-id="756f3-323">開始說話，然後暫停20秒。</span><span class="sxs-lookup"><span data-stu-id="756f3-323">Begin speaking and then pause for 20 seconds.</span></span> <span data-ttu-id="756f3-324">這會導致**聽寫辨識器**超時。</span><span class="sxs-lookup"><span data-stu-id="756f3-324">This will cause the **Dictation Recognizer** to timeout.</span></span>
* <span data-ttu-id="756f3-325">請注意，在上述的超時之後，會重新啟用**關鍵字辨識器**。</span><span class="sxs-lookup"><span data-stu-id="756f3-325">Notice that the **Keyword Recognizer** is re-enabled after the above timeout.</span></span> <span data-ttu-id="756f3-326">Communicator 現在會回應語音命令。</span><span class="sxs-lookup"><span data-stu-id="756f3-326">The communicator will now respond to voice commands.</span></span>
* <span data-ttu-id="756f3-327">說「*傳送訊息*」將訊息傳送至太空人。</span><span class="sxs-lookup"><span data-stu-id="756f3-327">Say *"Send Message"* to send the message to the astronaut.</span></span>

## <a name="chapter-4---grammar-recognizer"></a><span data-ttu-id="756f3-328">第4章-文法辨識器</span><span class="sxs-lookup"><span data-stu-id="756f3-328">Chapter 4 - Grammar Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a><span data-ttu-id="756f3-329">目標</span><span class="sxs-lookup"><span data-stu-id="756f3-329">Objectives</span></span>

* <span data-ttu-id="756f3-330">使用文法辨識器，根據 SRGS 或語音辨識文法規格（file）識別使用者的語音。</span><span class="sxs-lookup"><span data-stu-id="756f3-330">Use the Grammar Recognizer to recognize the user's speech according to an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

>[!NOTE]
><span data-ttu-id="756f3-331">必須針對要從麥克風錄製的應用程式宣告**麥克風**功能。</span><span class="sxs-lookup"><span data-stu-id="756f3-331">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="756f3-332">您已在 MR 輸入212中完成這項作業，但請記住您自己的專案。</span><span class="sxs-lookup"><span data-stu-id="756f3-332">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="756f3-333">在 Unity 編輯器中，流覽至 [編輯 > 專案設定 > Player]，移至播放程式設定</span><span class="sxs-lookup"><span data-stu-id="756f3-333">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="756f3-334">按一下 [通用 Windows 平臺] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="756f3-334">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="756f3-335">在 [發佈設定 > 功能] 區段中，檢查**麥克風**功能</span><span class="sxs-lookup"><span data-stu-id="756f3-335">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="756f3-336">指示</span><span class="sxs-lookup"><span data-stu-id="756f3-336">Instructions</span></span>

1. <span data-ttu-id="756f3-337">**在 [階層**] 面板中，搜尋**Jetpack_Center**並加以選取。</span><span class="sxs-lookup"><span data-stu-id="756f3-337">In the **Hierarchy** panel, search for **Jetpack_Center** and select it.</span></span>
2. <span data-ttu-id="756f3-338">在 [偵測**器**] 面板中尋找**Tagalong 動作**腳本。</span><span class="sxs-lookup"><span data-stu-id="756f3-338">Look for the **Tagalong Action** script in the **Inspector** panel.</span></span>
3. <span data-ttu-id="756f3-339">按一下要**沿著欄位標記的物件**右邊的小圓圈。</span><span class="sxs-lookup"><span data-stu-id="756f3-339">Click the little circle to the right of the **Object To Tag Along** field.</span></span>
4. <span data-ttu-id="756f3-340">在快顯的視窗中，搜尋**SRGSToolbox** ，並從清單中選取它。</span><span class="sxs-lookup"><span data-stu-id="756f3-340">In the window that pops up, search for **SRGSToolbox** and select it from the list.</span></span>
5. <span data-ttu-id="756f3-341">請查看**StreamingAssets**資料夾中的**SRGSColor。**</span><span class="sxs-lookup"><span data-stu-id="756f3-341">Take a look at the **SRGSColor.xml** file in the **StreamingAssets** folder.</span></span>
    1. <span data-ttu-id="756f3-342">您可以在[這裡](https://www.w3.org/TR/speech-grammar/)的 W3C 網站上找到 SRGS 設計規格。</span><span class="sxs-lookup"><span data-stu-id="756f3-342">The SRGS design spec can be found on the W3C website [here](https://www.w3.org/TR/speech-grammar/).</span></span>

<span data-ttu-id="756f3-343">在我們的 SRGS 檔案中，我們有三種類型的規則：</span><span class="sxs-lookup"><span data-stu-id="756f3-343">In our SRGS file, we have three types of rules:</span></span>

* <span data-ttu-id="756f3-344">一種規則，可讓您從十二種色彩的清單中說出一種色彩。</span><span class="sxs-lookup"><span data-stu-id="756f3-344">A rule which lets you say one color from a list of twelve colors.</span></span>
* <span data-ttu-id="756f3-345">這三個規則會接聽色彩規則和三個圖形其中之一的組合。</span><span class="sxs-lookup"><span data-stu-id="756f3-345">Three rules which listen for a combination of the color rule and one of the three shapes.</span></span>
* <span data-ttu-id="756f3-346">根規則 colorChooser，它會接聽三種「色彩和形狀」規則的任何組合。</span><span class="sxs-lookup"><span data-stu-id="756f3-346">The root rule, colorChooser, which listens for any combination of the three "color + shape" rules.</span></span> <span data-ttu-id="756f3-347">這些圖形可以用任何順序來表示，而且從1到三的任何數量都是。</span><span class="sxs-lookup"><span data-stu-id="756f3-347">The shapes can be said in any order and in any amount from just one to all three.</span></span> <span data-ttu-id="756f3-348">這是唯一接聽的規則，因為它是在初始 &lt;文法&gt; 標記中的檔案頂端指定為根規則。</span><span class="sxs-lookup"><span data-stu-id="756f3-348">This is the only rule that is listened for, as it's specified as the root rule at the top of the file in the initial &lt;grammar&gt; tag.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="756f3-349">組建和部署</span><span class="sxs-lookup"><span data-stu-id="756f3-349">Build and Deploy</span></span>

* <span data-ttu-id="756f3-350">在 Unity 中重建應用程式，然後從 Visual Studio 建立及部署，以在 HoloLens 上體驗應用程式。</span><span class="sxs-lookup"><span data-stu-id="756f3-350">Rebuild the application in Unity, then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="756f3-351">使用 [空中] 手勢關閉 [調整] 方塊。</span><span class="sxs-lookup"><span data-stu-id="756f3-351">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="756f3-352">看一下太空人的 jetpack，並執行空中碰手勢。</span><span class="sxs-lookup"><span data-stu-id="756f3-352">Gaze at the astronaut's jetpack and perform an air-tap gesture.</span></span>
* <span data-ttu-id="756f3-353">開始說話。</span><span class="sxs-lookup"><span data-stu-id="756f3-353">Start speaking.</span></span> <span data-ttu-id="756f3-354">**文法辨識器**會解讀您的語音，並根據辨識變更圖形的色彩。</span><span class="sxs-lookup"><span data-stu-id="756f3-354">The **Grammar Recognizer** will interpret your speech and change the colors of the shapes based on the recognition.</span></span> <span data-ttu-id="756f3-355">範例命令為「藍色圓形、黃色正方形」。</span><span class="sxs-lookup"><span data-stu-id="756f3-355">An example command is "blue circle, yellow square".</span></span>
* <span data-ttu-id="756f3-356">執行另一個空中碰手勢來關閉 [工具箱]。</span><span class="sxs-lookup"><span data-stu-id="756f3-356">Perform another air-tap gesture to dismiss the toolbox.</span></span>

## <a name="the-end"></a><span data-ttu-id="756f3-357">結束</span><span class="sxs-lookup"><span data-stu-id="756f3-357">The End</span></span>

<span data-ttu-id="756f3-358">恭喜！</span><span class="sxs-lookup"><span data-stu-id="756f3-358">Congratulations!</span></span> <span data-ttu-id="756f3-359">您現在已完成**MR 輸入212： Voice**。</span><span class="sxs-lookup"><span data-stu-id="756f3-359">You have now completed **MR Input 212: Voice**.</span></span>

* <span data-ttu-id="756f3-360">您知道語音命令的 Dos 和注意事項。</span><span class="sxs-lookup"><span data-stu-id="756f3-360">You know the Dos and Don'ts of voice commands.</span></span>
* <span data-ttu-id="756f3-361">您已瞭解如何運用工具提示，讓使用者知道語音命令。</span><span class="sxs-lookup"><span data-stu-id="756f3-361">You saw how tooltips were employed to make users aware of voice commands.</span></span>
* <span data-ttu-id="756f3-362">您看到了數種類型的意見反應，用來確認使用者的語音已被聽到。</span><span class="sxs-lookup"><span data-stu-id="756f3-362">You saw several types of feedback used to acknowledge that the user's voice was heard.</span></span>
* <span data-ttu-id="756f3-363">您知道如何在關鍵字辨識器和聽寫辨識器之間切換，以及這兩項功能如何瞭解和解讀您的聲音。</span><span class="sxs-lookup"><span data-stu-id="756f3-363">You know how to switch between the Keyword Recognizer and the Dictation Recognizer, and how these two features understand and interpret your voice.</span></span>
* <span data-ttu-id="756f3-364">您已瞭解如何在應用程式中使用 SRGS 檔案和文法辨識器來進行語音辨識。</span><span class="sxs-lookup"><span data-stu-id="756f3-364">You learned how to use an SRGS file and the Grammar Recognizer for speech recognition in your application.</span></span>
