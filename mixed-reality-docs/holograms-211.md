---
title: MR 輸入 211-手勢
description: 遵循此編碼逐步解說，使用 Unity、Visual Studio 和 HoloLens 來瞭解手勢概念的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit-unity、學院、教學課程、手勢
ms.openlocfilehash: d7a92e4b2f196d6d8b0ba0fe3ccb2aed87479ac1
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434693"
---
>[!NOTE]
><span data-ttu-id="29501-104">混合現實學術教學課程的設計是使用 HoloLens （第1代）和混合現實的沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="29501-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="29501-105">因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="29501-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="29501-106">這些教學課程 **_不_** 會以最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="29501-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="29501-107">系統會保留這些資訊，以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="29501-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="29501-108">HoloLens 2 已張貼[一系列新的教學](mrlearning-base.md)課程。</span><span class="sxs-lookup"><span data-stu-id="29501-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

# <a name="mr-input-211-gesture"></a><span data-ttu-id="29501-109">MR 輸入211：手勢</span><span class="sxs-lookup"><span data-stu-id="29501-109">MR Input 211: Gesture</span></span>

<span data-ttu-id="29501-110">[手勢](gaze-and-commit.md#composite-gestures)會將使用者意圖變成動作。</span><span class="sxs-lookup"><span data-stu-id="29501-110">[Gestures](gaze-and-commit.md#composite-gestures) turn user intention into action.</span></span> <span data-ttu-id="29501-111">透過手勢，使用者可以與全息影像互動。</span><span class="sxs-lookup"><span data-stu-id="29501-111">With gestures, users can interact with holograms.</span></span> <span data-ttu-id="29501-112">在本課程中，我們將學習如何追蹤使用者的手、回應使用者輸入，並根據手中的狀態和位置提供意見反應給使用者。</span><span class="sxs-lookup"><span data-stu-id="29501-112">In this course, we'll learn how to track the user's hands, respond to user input, and give feedback to the user based on hand state and location.</span></span>

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

<span data-ttu-id="29501-113">在[MR 基本 101](holograms-101.md)中，我們使用了簡單的點按手勢來與我們的全息影像互動。</span><span class="sxs-lookup"><span data-stu-id="29501-113">In [MR Basics 101](holograms-101.md), we used a simple air-tap gesture to interact with our holograms.</span></span> <span data-ttu-id="29501-114">現在，我們將超越空中操作手勢，並探索新的概念來：</span><span class="sxs-lookup"><span data-stu-id="29501-114">Now, we'll move beyond the air-tap gesture and explore new concepts to:</span></span>

* <span data-ttu-id="29501-115">偵測使用者的手追蹤，並提供意見反應給使用者。</span><span class="sxs-lookup"><span data-stu-id="29501-115">Detect when the user's hand is being tracked and provide feedback to the user.</span></span>
* <span data-ttu-id="29501-116">使用導覽手勢來旋轉我們的全息影像。</span><span class="sxs-lookup"><span data-stu-id="29501-116">Use a navigation gesture to rotate our holograms.</span></span>
* <span data-ttu-id="29501-117">當使用者想要離開時，請提供意見反應。</span><span class="sxs-lookup"><span data-stu-id="29501-117">Provide feedback when the user's hand is about to go out of view.</span></span>
* <span data-ttu-id="29501-118">使用操作事件可讓使用者以自己的手移動全息影像。</span><span class="sxs-lookup"><span data-stu-id="29501-118">Use manipulation events to allow users to move holograms with their hands.</span></span>

<span data-ttu-id="29501-119">在此課程中，我們將會回顧 Unity 專案**模型瀏覽器**，我們在[MR 輸入 210](holograms-210.md)中建立了這項功能。</span><span class="sxs-lookup"><span data-stu-id="29501-119">In this course, we'll revisit the Unity project **Model Explorer**, which we built in [MR Input 210](holograms-210.md).</span></span> <span data-ttu-id="29501-120">我們的太空人 friend 會回頭協助我們探索這些新的手勢概念。</span><span class="sxs-lookup"><span data-stu-id="29501-120">Our astronaut friend is back to assist us in our exploration of these new gesture concepts.</span></span>

>[!IMPORTANT]
><span data-ttu-id="29501-121">下列各章節所內嵌的影片，都是使用舊版 Unity 和混合現實工具組錄製的。</span><span class="sxs-lookup"><span data-stu-id="29501-121">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="29501-122">雖然逐步指示是正確且最新的，但您可能會在已過期的對應影片中看到腳本和視覺效果。</span><span class="sxs-lookup"><span data-stu-id="29501-122">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="29501-123">影片仍包含在 posterity 中，因為涵蓋的概念仍適用。</span><span class="sxs-lookup"><span data-stu-id="29501-123">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="29501-124">裝置支援</span><span class="sxs-lookup"><span data-stu-id="29501-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="29501-125">粗</span><span class="sxs-lookup"><span data-stu-id="29501-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="29501-126"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="29501-126"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="29501-127"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="29501-127"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="29501-128">MR 輸入211：手勢</span><span class="sxs-lookup"><span data-stu-id="29501-128">MR Input 211: Gesture</span></span></td><td style="text-align: center;"> <span data-ttu-id="29501-129">✔️</span><span class="sxs-lookup"><span data-stu-id="29501-129">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="29501-130">✔️</span><span class="sxs-lookup"><span data-stu-id="29501-130">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="29501-131">開始之前</span><span class="sxs-lookup"><span data-stu-id="29501-131">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="29501-132">必要條件</span><span class="sxs-lookup"><span data-stu-id="29501-132">Prerequisites</span></span>

* <span data-ttu-id="29501-133">[已安裝正確工具](install-the-tools.md)的 WINDOWS 10 電腦。</span><span class="sxs-lookup"><span data-stu-id="29501-133">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="29501-134">一些基本C#的程式設計能力。</span><span class="sxs-lookup"><span data-stu-id="29501-134">Some basic C# programming ability.</span></span>
* <span data-ttu-id="29501-135">您應已完成[MR 基本概念 101](holograms-101.md)。</span><span class="sxs-lookup"><span data-stu-id="29501-135">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="29501-136">您應已完成[MR 輸入 210](holograms-210.md)。</span><span class="sxs-lookup"><span data-stu-id="29501-136">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="29501-137">[為開發設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="29501-137">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="29501-138">專案檔案</span><span class="sxs-lookup"><span data-stu-id="29501-138">Project files</span></span>

* <span data-ttu-id="29501-139">下載專案[所需的](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip)檔案。</span><span class="sxs-lookup"><span data-stu-id="29501-139">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) required by the project.</span></span><span data-ttu-id="29501-140"> 需要 Unity 2017.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="29501-140"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="29501-141">將檔案取消封存至您的桌面或其他容易到達的位置。</span><span class="sxs-lookup"><span data-stu-id="29501-141">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="29501-142">如果您想要在下載之前查看原始程式碼，可以[在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture)取得。</span><span class="sxs-lookup"><span data-stu-id="29501-142">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="29501-143">勘誤和注意事項</span><span class="sxs-lookup"><span data-stu-id="29501-143">Errata and Notes</span></span>

* <span data-ttu-id="29501-144">必須在 Visual Studio 下的 [工具]-[> 選項]-[> 的偵錯工具] 中停用（*取消*核取） [啟用 Just My Code]，才能在程式碼中叫用中斷點。</span><span class="sxs-lookup"><span data-stu-id="29501-144">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-0---unity-setup"></a><span data-ttu-id="29501-145">第0章-Unity 設定</span><span class="sxs-lookup"><span data-stu-id="29501-145">Chapter 0 - Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="29501-146">指示</span><span class="sxs-lookup"><span data-stu-id="29501-146">Instructions</span></span>

1. <span data-ttu-id="29501-147">啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="29501-147">Start Unity.</span></span>
2. <span data-ttu-id="29501-148">選取 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="29501-148">Select **Open**.</span></span>
3. <span data-ttu-id="29501-149">流覽至您先前取消封存的**手勢**資料夾。</span><span class="sxs-lookup"><span data-stu-id="29501-149">Navigate to the **Gesture** folder you previously un-archived.</span></span>
4. <span data-ttu-id="29501-150">尋找並選取 [**開始**/**模型瀏覽器**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="29501-150">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="29501-151">按一下 [**選取資料夾**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="29501-151">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="29501-152">在 [**專案**] 面板中，展開 [**幕後**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="29501-152">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="29501-153">按兩下 [ **ModelExplorer**場景]，將其載入 Unity。</span><span class="sxs-lookup"><span data-stu-id="29501-153">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="29501-154">建置</span><span class="sxs-lookup"><span data-stu-id="29501-154">Building</span></span>

1. <span data-ttu-id="29501-155">在 Unity 中，選取 [檔案] **> [組建設定**]。</span><span class="sxs-lookup"><span data-stu-id="29501-155">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="29501-156">如果 [**場景/ModelExplorer** ] 未在 [組建] 的**場景**中列出，請按一下 [**新增開啟場景**] 以加入場景。</span><span class="sxs-lookup"><span data-stu-id="29501-156">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="29501-157">如果您是特別針對 HoloLens 進行開發，請將**目標裝置**設定為**hololens**。</span><span class="sxs-lookup"><span data-stu-id="29501-157">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="29501-158">否則，請將它保留在**任何裝置**上。</span><span class="sxs-lookup"><span data-stu-id="29501-158">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="29501-159">確定 [**組建類型**] 設定為 [ **D3D** ]，並將 [ **sdk** ] 設定為 [**已安裝最新**版本] （應該是 SDK 16299 或更新版本）。</span><span class="sxs-lookup"><span data-stu-id="29501-159">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="29501-160">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="29501-160">Click **Build**.</span></span>
6. <span data-ttu-id="29501-161">建立名為 "App" 的**新資料夾**。</span><span class="sxs-lookup"><span data-stu-id="29501-161">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="29501-162">按一下 [**應用程式**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="29501-162">Single click the **App** folder.</span></span>
8. <span data-ttu-id="29501-163">按下 [**選取資料夾**]，Unity 就會開始建立 Visual Studio 的專案。</span><span class="sxs-lookup"><span data-stu-id="29501-163">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="29501-164">當 Unity 完成時，將會出現 [檔案瀏覽器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="29501-164">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="29501-165">開啟**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="29501-165">Open the **App** folder.</span></span>
2. <span data-ttu-id="29501-166">開啟**ModelExplorer Visual Studio 解決方案**。</span><span class="sxs-lookup"><span data-stu-id="29501-166">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="29501-167">如果部署至 HoloLens：</span><span class="sxs-lookup"><span data-stu-id="29501-167">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="29501-168">使用 Visual Studio 中的頂端工具列，將目標從 [調試] 變更為 [**發行**]，將 [從 ARM] 變更為**x86**。</span><span class="sxs-lookup"><span data-stu-id="29501-168">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="29501-169">按一下 [本機電腦] 按鈕旁的下拉式箭號，然後選取 [**遠端電腦**]。</span><span class="sxs-lookup"><span data-stu-id="29501-169">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="29501-170">輸入**您的 HoloLens 裝置 IP 位址**，並將驗證模式設定為 **[通用（未加密的通訊協定）** ]。</span><span class="sxs-lookup"><span data-stu-id="29501-170">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="29501-171">按一下 [**選取**]。</span><span class="sxs-lookup"><span data-stu-id="29501-171">Click **Select**.</span></span> <span data-ttu-id="29501-172">如果您不知道您的裝置 IP 位址，請查看 [設定] [ **> Network & Internet] > [Advanced Options**]。</span><span class="sxs-lookup"><span data-stu-id="29501-172">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="29501-173">在頂端功能表列中，按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="29501-173">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="29501-174">如果這是您第一次部署至您的裝置，您必須將[它與 Visual Studio 配對](using-visual-studio.md#pairing-your-device)。</span><span class="sxs-lookup"><span data-stu-id="29501-174">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>
5. <span data-ttu-id="29501-175">應用程式部署完成後，請使用**select 手勢**來關閉**Fitbox** 。</span><span class="sxs-lookup"><span data-stu-id="29501-175">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="29501-176">如果部署到沉浸式耳機：</span><span class="sxs-lookup"><span data-stu-id="29501-176">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="29501-177">使用 Visual Studio 中的頂端工具列，將目標從 [調試] 變更為 [**發行**]，將 [從 ARM] 變更為**x64**。</span><span class="sxs-lookup"><span data-stu-id="29501-177">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="29501-178">請確定 [部署目標] 設定為 [**本機電腦**]。</span><span class="sxs-lookup"><span data-stu-id="29501-178">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="29501-179">在頂端功能表列中，按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="29501-179">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="29501-180">應用程式部署完成後，請藉由在動作控制器上提取觸發程式來關閉**Fitbox** 。</span><span class="sxs-lookup"><span data-stu-id="29501-180">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="29501-181">在 [Visual Studio 錯誤] 面板中，您可能會注意到一些紅色錯誤。</span><span class="sxs-lookup"><span data-stu-id="29501-181">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="29501-182">可以放心地忽略它們。</span><span class="sxs-lookup"><span data-stu-id="29501-182">It is safe to ignore them.</span></span> <span data-ttu-id="29501-183">切換至 [輸出] 面板以查看實際的組建進度。</span><span class="sxs-lookup"><span data-stu-id="29501-183">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="29501-184">[輸出] 面板中的錯誤會要求您進行修正（最常見的原因是腳本錯誤）。</span><span class="sxs-lookup"><span data-stu-id="29501-184">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---hand-detected-feedback"></a><span data-ttu-id="29501-185">第1章-一手偵測到的意見反應</span><span class="sxs-lookup"><span data-stu-id="29501-185">Chapter 1 - Hand detected feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a><span data-ttu-id="29501-186">目標</span><span class="sxs-lookup"><span data-stu-id="29501-186">Objectives</span></span>

* <span data-ttu-id="29501-187">訂閱手寫追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="29501-187">Subscribe to hand tracking events.</span></span>
* <span data-ttu-id="29501-188">使用游標意見反應，在追蹤手時顯示使用者。</span><span class="sxs-lookup"><span data-stu-id="29501-188">Use cursor feedback to show users when a hand is being tracked.</span></span>

>[!NOTE]
><span data-ttu-id="29501-189">在 HoloLens 2 上，只要看到手（而不只是指手指的狀態）時，就會引發實習偵測。</span><span class="sxs-lookup"><span data-stu-id="29501-189">On HoloLens 2 , hands detected fires whenever hands are visible (not just when a finger is pointing up).</span></span>

### <a name="instructions"></a><span data-ttu-id="29501-190">指示</span><span class="sxs-lookup"><span data-stu-id="29501-190">Instructions</span></span>

* <span data-ttu-id="29501-191">**在 [階層**] 面板中，展開 [ **InputManager** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="29501-191">In the **Hierarchy** panel, expand the **InputManager** object.</span></span>
* <span data-ttu-id="29501-192">尋找並選取**GesturesInput**物件。</span><span class="sxs-lookup"><span data-stu-id="29501-192">Look for and select the **GesturesInput** object.</span></span>

<span data-ttu-id="29501-193">**InteractionInputSource.cs**腳本會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="29501-193">The **InteractionInputSource.cs** script performs these steps:</span></span>

1. <span data-ttu-id="29501-194">訂閱 InteractionSourceDetected 和 InteractionSourceLost 事件。</span><span class="sxs-lookup"><span data-stu-id="29501-194">Subscribes to the InteractionSourceDetected and InteractionSourceLost events.</span></span>
2. <span data-ttu-id="29501-195">設定 HandDetected 狀態。</span><span class="sxs-lookup"><span data-stu-id="29501-195">Sets the HandDetected state.</span></span>
3. <span data-ttu-id="29501-196">從 InteractionSourceDetected 和 InteractionSourceLost 事件取消訂閱。</span><span class="sxs-lookup"><span data-stu-id="29501-196">Unsubscribes from the InteractionSourceDetected and InteractionSourceLost events.</span></span>

<span data-ttu-id="29501-197">接下來，我們會將我們的資料指標從[MR 輸入 210](holograms-210.md)升級為根據使用者的動作顯示意見反應的資料指標。</span><span class="sxs-lookup"><span data-stu-id="29501-197">Next, we'll upgrade our cursor from [MR Input 210](holograms-210.md) into one that shows feedback depending on the user's actions.</span></span>

1. <span data-ttu-id="29501-198">**在 [階層] 面板中**，選取**游標**物件，並將它刪除。</span><span class="sxs-lookup"><span data-stu-id="29501-198">In the **Hierarchy** panel, select the **Cursor** object and delete it.</span></span>
2. <span data-ttu-id="29501-199">在 [**專案**] 面板中，搜尋**CursorWithFeedback** ，**並將它拖曳至 [階層**] 面板。</span><span class="sxs-lookup"><span data-stu-id="29501-199">In the **Project** panel, search for **CursorWithFeedback** and drag it into the **Hierarchy** panel.</span></span>
3. <span data-ttu-id="29501-200">按一下 [階層 **] 面板中的 [** **InputManager** ]，然後將**CursorWithFeedback**物件從階層**拖曳至 InputManager**的**SimpleSinglePointerSelector**的 [**游標**] 欄位（位於底部）偵測**器**。</span><span class="sxs-lookup"><span data-stu-id="29501-200">Click on **InputManager** in the **Hierarchy** panel, then drag the **CursorWithFeedback** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>
4. <span data-ttu-id="29501-201">按一下階層**中的 [** **CursorWithFeedback** ]。</span><span class="sxs-lookup"><span data-stu-id="29501-201">Click on the **CursorWithFeedback** in the **Hierarchy**.</span></span>
5. <span data-ttu-id="29501-202">在 [偵測**器**] 面板中，展開**物件游標**腳本上的 [**游標狀態資料**]。</span><span class="sxs-lookup"><span data-stu-id="29501-202">In the **Inspector** panel, expand **Cursor State Data** on the **Object Cursor** script.</span></span>

<span data-ttu-id="29501-203">**游標狀態資料**的運作方式如下所示：</span><span class="sxs-lookup"><span data-stu-id="29501-203">The **Cursor State Data** works like this:</span></span>

* <span data-ttu-id="29501-204">任何**觀察**狀態表示不會偵測到任何手，而且使用者只需要尋找。</span><span class="sxs-lookup"><span data-stu-id="29501-204">Any **Observe** state means that no hand is detected and the user is simply looking around.</span></span>
* <span data-ttu-id="29501-205">任何**互動**狀態表示偵測到手或控制器。</span><span class="sxs-lookup"><span data-stu-id="29501-205">Any **Interact** state means that a hand or controller is detected.</span></span>
* <span data-ttu-id="29501-206">任何**停留**狀態表示使用者正在查看全像投影。</span><span class="sxs-lookup"><span data-stu-id="29501-206">Any **Hover** state means the user is looking at a hologram.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="29501-207">組建和部署</span><span class="sxs-lookup"><span data-stu-id="29501-207">Build and Deploy</span></span>

* <span data-ttu-id="29501-208">在 Unity 中，使用檔案 **> 組建設定**來重建應用程式。</span><span class="sxs-lookup"><span data-stu-id="29501-208">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="29501-209">開啟**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="29501-209">Open the **App** folder.</span></span>
* <span data-ttu-id="29501-210">如果尚未開啟，請開啟**ModelExplorer Visual Studio 解決方案**。</span><span class="sxs-lookup"><span data-stu-id="29501-210">If it's not already open, open the **ModelExplorer Visual Studio Solution**.</span></span>
  * <span data-ttu-id="29501-211">（如果您已經在安裝期間于 Visual Studio 內建立/部署此專案，則可以開啟 VS 的實例，然後在出現提示時按一下 [全部重載]）。</span><span class="sxs-lookup"><span data-stu-id="29501-211">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>
* <span data-ttu-id="29501-212">在 Visual Studio 中，按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="29501-212">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="29501-213">將應用程式部署至 HoloLens 之後，請使用 [點一下] 手勢來關閉 fitbox。</span><span class="sxs-lookup"><span data-stu-id="29501-213">After the application deploys to the HoloLens, dismiss the fitbox using the air-tap gesture.</span></span>
* <span data-ttu-id="29501-214">將您的手移到視野中，並將您的索引指向天空以開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="29501-214">Move your hand into view and point your index finger to the sky to start hand tracking.</span></span>
* <span data-ttu-id="29501-215">向左、向右、向上和向下移動。</span><span class="sxs-lookup"><span data-stu-id="29501-215">Move your hand left, right, up and down.</span></span>
* <span data-ttu-id="29501-216">在偵測到您的手時，觀看游標變更的方式，然後從 view 中消失。</span><span class="sxs-lookup"><span data-stu-id="29501-216">Watch how the cursor changes when your hand is detected and then lost from view.</span></span>
* <span data-ttu-id="29501-217">如果您使用的是沉浸式耳機，就必須連接並中斷控制器的連線。</span><span class="sxs-lookup"><span data-stu-id="29501-217">If you're on an immersive headset, you'll have to connect and disconnect your controller.</span></span> <span data-ttu-id="29501-218">此意見反應在沉浸式裝置上會變得較不有趣，因為連線的控制器一律會「可用」。</span><span class="sxs-lookup"><span data-stu-id="29501-218">This feedback becomes less interesting on an immersive device, as a connected controller will always be "available".</span></span>

## <a name="chapter-2---navigation"></a><span data-ttu-id="29501-219">第2章-流覽</span><span class="sxs-lookup"><span data-stu-id="29501-219">Chapter 2 - Navigation</span></span>

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a><span data-ttu-id="29501-220">目標</span><span class="sxs-lookup"><span data-stu-id="29501-220">Objectives</span></span>

* <span data-ttu-id="29501-221">使用導覽手勢事件來旋轉太空人。</span><span class="sxs-lookup"><span data-stu-id="29501-221">Use Navigation gesture events to rotate the astronaut.</span></span>

### <a name="instructions"></a><span data-ttu-id="29501-222">指示</span><span class="sxs-lookup"><span data-stu-id="29501-222">Instructions</span></span>

<span data-ttu-id="29501-223">若要在我們的應用程式中使用導覽手勢，我們將在導覽手勢發生時，編輯**GestureAction.cs**以旋轉物件。</span><span class="sxs-lookup"><span data-stu-id="29501-223">To use Navigation gestures in our app, we are going to edit **GestureAction.cs** to rotate objects when the Navigation gesture occurs.</span></span> <span data-ttu-id="29501-224">此外，我們還會將意見反應新增至游標，以便在導覽可供使用時顯示。</span><span class="sxs-lookup"><span data-stu-id="29501-224">Additionally, we'll add feedback to the cursor to display when Navigation is available.</span></span>

1. <span data-ttu-id="29501-225">**在 [階層**] 面板中，展開 [ **CursorWithFeedback**]。</span><span class="sxs-lookup"><span data-stu-id="29501-225">In the **Hierarchy** panel, expand **CursorWithFeedback**.</span></span>
2. <span data-ttu-id="29501-226">在 [**全息影像**] 資料夾中，尋找**ScrollFeedback**資產。</span><span class="sxs-lookup"><span data-stu-id="29501-226">In the **Holograms** folder, find the **ScrollFeedback** asset.</span></span>
3. <span data-ttu-id="29501-227">將**ScrollFeedback** prefab 拖放到階層中的**CursorWithFeedback** **GameObject。**</span><span class="sxs-lookup"><span data-stu-id="29501-227">Drag and drop the **ScrollFeedback** prefab onto the **CursorWithFeedback** GameObject in the **Hierarchy**.</span></span>
4. <span data-ttu-id="29501-228">按一下 [ **CursorWithFeedback**]。</span><span class="sxs-lookup"><span data-stu-id="29501-228">Click on **CursorWithFeedback**.</span></span>
5. <span data-ttu-id="29501-229">在 [偵測**器**] 面板中，按一下 [**新增元件**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="29501-229">In the **Inspector** panel, click the **Add Component** button.</span></span>
6. <span data-ttu-id="29501-230">在功能表的 [搜尋] 方塊中，輸入**CursorFeedback**。</span><span class="sxs-lookup"><span data-stu-id="29501-230">In the menu, type in the search box **CursorFeedback**.</span></span> <span data-ttu-id="29501-231">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="29501-231">Select the search result.</span></span>
7. <span data-ttu-id="29501-232">從階層中，將**ScrollFeedback** **物件拖放至偵測** **器**中**游標意見**反應元件的 [ **Scroll 偵測到的遊戲物件**] 屬性。</span><span class="sxs-lookup"><span data-stu-id="29501-232">Drag and drop the **ScrollFeedback** object from the **Hierarchy** onto the **Scroll Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>
8. <span data-ttu-id="29501-233">**在 [階層**] 面板中，選取 [ **AstroMan** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="29501-233">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
9. <span data-ttu-id="29501-234">在 [偵測**器**] 面板中，按一下 [**新增元件**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="29501-234">In the **Inspector** panel, click the **Add Component** button.</span></span>
10. <span data-ttu-id="29501-235">在功能表中，于 [搜尋] 方塊中輸入**手勢動作**。</span><span class="sxs-lookup"><span data-stu-id="29501-235">In the menu, type in the search box **Gesture Action**.</span></span> <span data-ttu-id="29501-236">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="29501-236">Select the search result.</span></span>

<span data-ttu-id="29501-237">接下來，在 Visual Studio 中開啟**GestureAction.cs** 。</span><span class="sxs-lookup"><span data-stu-id="29501-237">Next, open **GestureAction.cs** in Visual Studio.</span></span> <span data-ttu-id="29501-238">在編碼練習 2. c 中，編輯腳本以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="29501-238">In coding exercise 2.c, edit the script to do the following:</span></span>

1. <span data-ttu-id="29501-239">每當執行導覽手勢時 **，旋轉 AstroMan**物件。</span><span class="sxs-lookup"><span data-stu-id="29501-239">**Rotate the AstroMan** object whenever a Navigation gesture is performed.</span></span>
2. <span data-ttu-id="29501-240">計算**rotationFactor**以控制套用至物件的旋轉量。</span><span class="sxs-lookup"><span data-stu-id="29501-240">Calculate the **rotationFactor** to control the amount of rotation applied to the object.</span></span>
3. <span data-ttu-id="29501-241">當使用者向左或向右移動時，旋轉 y 軸的**物件**。</span><span class="sxs-lookup"><span data-stu-id="29501-241">**Rotate the object** around the y-axis when the user moves their hand left or right.</span></span>

<span data-ttu-id="29501-242">在腳本中完成程式碼編寫練習 2. c，或以下列已完成的解決方案取代程式碼：</span><span class="sxs-lookup"><span data-stu-id="29501-242">Complete coding exercises 2.c in the script, or replace the code with the completed solution below:</span></span>

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

<span data-ttu-id="29501-243">您會發現其他導覽事件已填入一些資訊。</span><span class="sxs-lookup"><span data-stu-id="29501-243">You'll notice that the other navigation events are already filled in with some info.</span></span> <span data-ttu-id="29501-244">我們會將 GameObject 推送至工具組的 InputSystem's 強制堆疊，讓使用者不需要在開始旋轉之後，將焦點保持在太空人上。</span><span class="sxs-lookup"><span data-stu-id="29501-244">We push the GameObject onto the Toolkit's InputSystem's modal stack, so the user doesn't have to maintain focus on the Astronaut once rotation has begun.</span></span> <span data-ttu-id="29501-245">同樣地，在手勢完成後，我們會將 GameObject 從堆疊中彈出。</span><span class="sxs-lookup"><span data-stu-id="29501-245">Correspondingly, we pop the GameObject off the stack once the gesture is completed.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="29501-246">組建和部署</span><span class="sxs-lookup"><span data-stu-id="29501-246">Build and Deploy</span></span>

1. <span data-ttu-id="29501-247">在 Unity 中重建應用程式，然後從 Visual Studio 建立及部署，以在 HoloLens 中執行。</span><span class="sxs-lookup"><span data-stu-id="29501-247">Rebuild the application in Unity and then build and deploy from Visual Studio to run it in the HoloLens.</span></span>
2. <span data-ttu-id="29501-248">看一下太空人，游標的任一邊應該會出現兩個箭號。</span><span class="sxs-lookup"><span data-stu-id="29501-248">Gaze at the astronaut, two arrows should appear on either side of the cursor.</span></span> <span data-ttu-id="29501-249">這個新的視覺效果表示太空人可以旋轉。</span><span class="sxs-lookup"><span data-stu-id="29501-249">This new visual indicates that the astronaut can be rotated.</span></span>
3. <span data-ttu-id="29501-250">將您的手放在就緒的位置（食指指向天空），讓 HoloLens 能夠開始追蹤您的手。</span><span class="sxs-lookup"><span data-stu-id="29501-250">Place your hand in the ready position (index finger pointed towards the sky) so the HoloLens will start tracking your hand.</span></span>
4. <span data-ttu-id="29501-251">若要旋轉太空人，請將您的索引指向縮小位置，然後向左或向右移動以觸發 NavigationX 手勢。</span><span class="sxs-lookup"><span data-stu-id="29501-251">To rotate the astronaut, lower your index finger to a pinch position, and then move your hand left or right to trigger the NavigationX gesture.</span></span>

## <a name="chapter-3---hand-guidance"></a><span data-ttu-id="29501-252">第3章-右手指引</span><span class="sxs-lookup"><span data-stu-id="29501-252">Chapter 3 - Hand Guidance</span></span>

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a><span data-ttu-id="29501-253">目標</span><span class="sxs-lookup"><span data-stu-id="29501-253">Objectives</span></span>

* <span data-ttu-id="29501-254">使用**手動指引分數**來協助預測何時會遺失手動追蹤。</span><span class="sxs-lookup"><span data-stu-id="29501-254">Use **hand guidance score** to help predict when hand tracking will be lost.</span></span>
* <span data-ttu-id="29501-255">提供**游標的意見**反應，以顯示使用者何時接近相機的觀看邊緣。</span><span class="sxs-lookup"><span data-stu-id="29501-255">Provide **feedback on the cursor** to show when the user's hand nears the camera's edge of view.</span></span>

### <a name="instructions"></a><span data-ttu-id="29501-256">指示</span><span class="sxs-lookup"><span data-stu-id="29501-256">Instructions</span></span>

1. <span data-ttu-id="29501-257">**在 [階層**] 面板中，選取 [ **CursorWithFeedback** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="29501-257">In the **Hierarchy** panel, select the **CursorWithFeedback** object.</span></span>
2. <span data-ttu-id="29501-258">在 [偵測**器**] 面板中，按一下 [**新增元件**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="29501-258">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="29501-259">在功能表中，于搜尋方塊中輸入**指引**。</span><span class="sxs-lookup"><span data-stu-id="29501-259">In the menu, type in the search box **Hand Guidance**.</span></span> <span data-ttu-id="29501-260">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="29501-260">Select the search result.</span></span>
4. <span data-ttu-id="29501-261">在 [**專案**面板] [**全息影像**] 資料夾中，尋找**HandGuidanceFeedback**資產。</span><span class="sxs-lookup"><span data-stu-id="29501-261">In the **Project** panel **Holograms** folder, find the **HandGuidanceFeedback** asset.</span></span>
5. <span data-ttu-id="29501-262">將**HandGuidanceFeedback**資產拖放至 [偵測**器**] 面板中的 [**右手指引指標**] 屬性。</span><span class="sxs-lookup"><span data-stu-id="29501-262">Drag and drop the **HandGuidanceFeedback** asset onto the **Hand Guidance Indicator** property in the **Inspector** panel.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="29501-263">組建和部署</span><span class="sxs-lookup"><span data-stu-id="29501-263">Build and Deploy</span></span>

* <span data-ttu-id="29501-264">在 Unity 中重建應用程式，然後從 Visual Studio 建立及部署，以在 HoloLens 上體驗應用程式。</span><span class="sxs-lookup"><span data-stu-id="29501-264">Rebuild the application in Unity and then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="29501-265">帶入您的手中，並提起您的索引手指以進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="29501-265">Bring your hand into view and raise your index finger to get tracked.</span></span>
* <span data-ttu-id="29501-266">使用導覽手勢開始旋轉太空人（將您的索引手指和 thumb 一起縮小）。</span><span class="sxs-lookup"><span data-stu-id="29501-266">Start rotating the astronaut with the Navigation gesture (pinch your index finger and thumb together).</span></span>
* <span data-ttu-id="29501-267">將您的手往左、靠右、向上和向下移動。</span><span class="sxs-lookup"><span data-stu-id="29501-267">Move your hand far left, right, up, and down.</span></span>
* <span data-ttu-id="29501-268">當您的手接近手勢框架的邊緣時，游標旁邊應該會出現箭號，以警告您將會遺失追蹤。</span><span class="sxs-lookup"><span data-stu-id="29501-268">As your hand nears the edge of the gesture frame, an arrow should appear next to the cursor to warn you that hand tracking will be lost.</span></span> <span data-ttu-id="29501-269">箭號表示要移動手的方向，以避免追蹤遺失。</span><span class="sxs-lookup"><span data-stu-id="29501-269">The arrow indicates which direction to move your hand in order to prevent tracking from being lost.</span></span>

## <a name="chapter-4---manipulation"></a><span data-ttu-id="29501-270">第4章-操作</span><span class="sxs-lookup"><span data-stu-id="29501-270">Chapter 4 - Manipulation</span></span>

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a><span data-ttu-id="29501-271">目標</span><span class="sxs-lookup"><span data-stu-id="29501-271">Objectives</span></span>

* <span data-ttu-id="29501-272">使用操作事件以您的手移動太空人。</span><span class="sxs-lookup"><span data-stu-id="29501-272">Use Manipulation events to move the astronaut with your hands.</span></span>
* <span data-ttu-id="29501-273">提供游標的意見反應，讓使用者知道何時可以使用操作。</span><span class="sxs-lookup"><span data-stu-id="29501-273">Provide feedback on the cursor to let the user know when Manipulation can be used.</span></span>

### <a name="instructions"></a><span data-ttu-id="29501-274">指示</span><span class="sxs-lookup"><span data-stu-id="29501-274">Instructions</span></span>

<span data-ttu-id="29501-275">GestureManager.cs 和 AstronautManager.cs 可讓我們執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="29501-275">GestureManager.cs and AstronautManager.cs will allow us to do the following:</span></span>

1. <span data-ttu-id="29501-276">使用語音關鍵字 "**Move 太空人**" 啟用**操作**手勢，並將 [**旋轉太空人**] 停用。</span><span class="sxs-lookup"><span data-stu-id="29501-276">Use the speech keyword "**Move Astronaut**" to enable **Manipulation** gestures and "**Rotate Astronaut**" to disable them.</span></span>
2. <span data-ttu-id="29501-277">切換為回應**操作手勢辨識器**。</span><span class="sxs-lookup"><span data-stu-id="29501-277">Switch to responding to the **Manipulation Gesture Recognizer**.</span></span>

<span data-ttu-id="29501-278">那就開始吧。</span><span class="sxs-lookup"><span data-stu-id="29501-278">Let's get started.</span></span>

1. <span data-ttu-id="29501-279">**在 [階層**] 面板中，建立新的空白 GameObject。</span><span class="sxs-lookup"><span data-stu-id="29501-279">In the **Hierarchy** panel, create a new empty GameObject.</span></span> <span data-ttu-id="29501-280">將它命名為 "**AstronautManager**"。</span><span class="sxs-lookup"><span data-stu-id="29501-280">Name it "**AstronautManager**".</span></span>
2. <span data-ttu-id="29501-281">在 [偵測**器**] 面板中，按一下 [**新增元件**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="29501-281">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="29501-282">在功能表的 [**太空人管理員**] 搜尋方塊中輸入。</span><span class="sxs-lookup"><span data-stu-id="29501-282">In the menu, type in the search box **Astronaut Manager**.</span></span> <span data-ttu-id="29501-283">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="29501-283">Select the search result.</span></span>
4. <span data-ttu-id="29501-284">在 [偵測**器**] 面板中，按一下 [**新增元件**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="29501-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
5. <span data-ttu-id="29501-285">在功能表中，于 [**語音輸入來源**] 搜尋方塊中輸入。</span><span class="sxs-lookup"><span data-stu-id="29501-285">In the menu, type in the search box **Speech Input Source**.</span></span> <span data-ttu-id="29501-286">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="29501-286">Select the search result.</span></span>

<span data-ttu-id="29501-287">我們現在會新增控制太空人互動狀態所需的語音命令。</span><span class="sxs-lookup"><span data-stu-id="29501-287">We'll now add the speech commands required to control the interaction state of the astronaut.</span></span>

1. <span data-ttu-id="29501-288">展開偵測**器**中的 [**關鍵字**] 區段。</span><span class="sxs-lookup"><span data-stu-id="29501-288">Expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="29501-289">按一下右手邊的  **+** ，以加入新的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="29501-289">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="29501-290">輸入關鍵字做為**移動太空人**。</span><span class="sxs-lookup"><span data-stu-id="29501-290">Type the Keyword as **Move Astronaut**.</span></span> <span data-ttu-id="29501-291">如有需要，您可以隨意新增金鑰快捷方式。</span><span class="sxs-lookup"><span data-stu-id="29501-291">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="29501-292">按一下右手邊的  **+** ，以加入新的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="29501-292">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="29501-293">輸入關鍵字作為 [**旋轉太空人**]。</span><span class="sxs-lookup"><span data-stu-id="29501-293">Type the Keyword as **Rotate Astronaut**.</span></span> <span data-ttu-id="29501-294">如有需要，您可以隨意新增金鑰快捷方式。</span><span class="sxs-lookup"><span data-stu-id="29501-294">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="29501-295">對應的處理常式程式碼可以在**GestureAction.cs**中的**ISpeechHandler. OnSpeechKeywordRecognized**處理常式中找到。</span><span class="sxs-lookup"><span data-stu-id="29501-295">The corresponding handler code can be found in **GestureAction.cs**, in the **ISpeechHandler.OnSpeechKeywordRecognized** handler.</span></span>

![如何設定第4章的語音輸入來源](images/holograms211-speech.png)

<span data-ttu-id="29501-297">接下來，我們會在資料指標上設定操作意見反應。</span><span class="sxs-lookup"><span data-stu-id="29501-297">Next, we'll setup the manipulation feedback on the cursor.</span></span>

1. <span data-ttu-id="29501-298">在 [**專案**面板] [**全息影像**] 資料夾中，尋找**PathingFeedback**資產。</span><span class="sxs-lookup"><span data-stu-id="29501-298">In the **Project** panel **Holograms** folder, find the **PathingFeedback** asset.</span></span>
2. <span data-ttu-id="29501-299">將**PathingFeedback** prefab 拖放到階層中的**CursorWithFeedback**物件上 **。**</span><span class="sxs-lookup"><span data-stu-id="29501-299">Drag and drop the **PathingFeedback** prefab onto the **CursorWithFeedback** object in the **Hierarchy**.</span></span>
3. <span data-ttu-id="29501-300">**在 [階層**] 面板中，按一下 [ **CursorWithFeedback**]。</span><span class="sxs-lookup"><span data-stu-id="29501-300">In the **Hierarchy** panel, click on **CursorWithFeedback**.</span></span>
4. <span data-ttu-id="29501-301">從階層中，將**PathingFeedback** **物件拖放至偵測** **器**的資料**指標意見**反應元件中的 [偵測到的內容]**遊戲物件**屬性。</span><span class="sxs-lookup"><span data-stu-id="29501-301">Drag and drop the **PathingFeedback** object from the **Hierarchy** onto the **Pathing Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>

<span data-ttu-id="29501-302">現在，我們需要將程式碼新增至**GestureAction.cs** ，以啟用下列各項：</span><span class="sxs-lookup"><span data-stu-id="29501-302">Now we need to add code to **GestureAction.cs** to enable the following:</span></span>

1. <span data-ttu-id="29501-303">將程式碼新增至**IManipulationHandler. OnManipulationUpdated**函式，此函式會在偵測到**操作**手勢時移動太空人。</span><span class="sxs-lookup"><span data-stu-id="29501-303">Add code to the **IManipulationHandler.OnManipulationUpdated** function, which will move the astronaut when a **Manipulation** gesture is detected.</span></span>
2. <span data-ttu-id="29501-304">計算**移動向量**，以根據手上的位置判斷太空人的移動位置。</span><span class="sxs-lookup"><span data-stu-id="29501-304">Calculate the **movement vector** to determine where the astronaut should be moved to based on hand position.</span></span>
3. <span data-ttu-id="29501-305">**將太空人移**至新位置。</span><span class="sxs-lookup"><span data-stu-id="29501-305">**Move** the astronaut to the new position.</span></span>

<span data-ttu-id="29501-306">完成程式碼撰寫練習 4. 中的**GestureAction.cs**，或使用下列已完成的解決方案：</span><span class="sxs-lookup"><span data-stu-id="29501-306">Complete coding exercise 4.a in **GestureAction.cs**, or use our completed solution below:</span></span>

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

### <a name="build-and-deploy"></a><span data-ttu-id="29501-307">組建和部署</span><span class="sxs-lookup"><span data-stu-id="29501-307">Build and Deploy</span></span>

* <span data-ttu-id="29501-308">在 Unity 中重建，然後從 Visual Studio 建立及部署，以在 HoloLens 中執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="29501-308">Rebuild in Unity and then build and deploy from Visual Studio to run the app in HoloLens.</span></span>
* <span data-ttu-id="29501-309">將您的手移到 HoloLens 前方，並引發您的索引手指，讓它可以進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="29501-309">Move your hand in front of the HoloLens and raise your index finger so that it can be tracked.</span></span>
* <span data-ttu-id="29501-310">將游標放在太空人上。</span><span class="sxs-lookup"><span data-stu-id="29501-310">Focus the cursor over the astronaut.</span></span>
* <span data-ttu-id="29501-311">說「移動太空人」，以操作手勢移動太空人。</span><span class="sxs-lookup"><span data-stu-id="29501-311">Say 'Move Astronaut' to move the astronaut with a Manipulation gesture.</span></span>
* <span data-ttu-id="29501-312">游標周圍應會出現四個箭號，表示程式會立即回應操作事件。</span><span class="sxs-lookup"><span data-stu-id="29501-312">Four arrows should appear around the cursor to indicate that the program will now respond to Manipulation events.</span></span>
* <span data-ttu-id="29501-313">將您的索引向下移到您的經驗，並將其 pinched 在一起。</span><span class="sxs-lookup"><span data-stu-id="29501-313">Lower your index finger down to your thumb, and keep them pinched together.</span></span>
* <span data-ttu-id="29501-314">當您四處移動時，太空人也會移動（這是操作）。</span><span class="sxs-lookup"><span data-stu-id="29501-314">As you move your hand around, the astronaut will move too (this is Manipulation).</span></span>
* <span data-ttu-id="29501-315">請提高您的索引手指，以停止操作太空人。</span><span class="sxs-lookup"><span data-stu-id="29501-315">Raise your index finger to stop manipulating the astronaut.</span></span>
* <span data-ttu-id="29501-316">注意：如果您在移動手前不要說「移動太空人」，則會改為使用導覽手勢。</span><span class="sxs-lookup"><span data-stu-id="29501-316">Note: If you do not say 'Move Astronaut' before moving your hand, then the Navigation gesture will be used instead.</span></span>
* <span data-ttu-id="29501-317">說「旋轉太空人」回到 rotatable 狀態。</span><span class="sxs-lookup"><span data-stu-id="29501-317">Say 'Rotate Astronaut' to return to the rotatable state.</span></span>

## <a name="chapter-5---model-expansion"></a><span data-ttu-id="29501-318">第5章-模型展開</span><span class="sxs-lookup"><span data-stu-id="29501-318">Chapter 5 - Model expansion</span></span>

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a><span data-ttu-id="29501-319">目標</span><span class="sxs-lookup"><span data-stu-id="29501-319">Objectives</span></span>

* <span data-ttu-id="29501-320">將太空人模型展開成多個較小的片段，讓使用者可以與之互動。</span><span class="sxs-lookup"><span data-stu-id="29501-320">Expand the Astronaut model into multiple, smaller pieces that the user can interact with.</span></span>
* <span data-ttu-id="29501-321">使用導覽和操作手勢來個別移動每個部分。</span><span class="sxs-lookup"><span data-stu-id="29501-321">Move each piece individually using Navigation and Manipulation gestures.</span></span>

### <a name="instructions"></a><span data-ttu-id="29501-322">指示</span><span class="sxs-lookup"><span data-stu-id="29501-322">Instructions</span></span>

<span data-ttu-id="29501-323">在本節中，我們將完成下列工作：</span><span class="sxs-lookup"><span data-stu-id="29501-323">In this section, we will accomplish the following tasks:</span></span>

1. <span data-ttu-id="29501-324">加入新的關鍵字「**展開模型**」以展開太空人模型。</span><span class="sxs-lookup"><span data-stu-id="29501-324">Add a new keyword "**Expand Model**" to expand the astronaut model.</span></span>
2. <span data-ttu-id="29501-325">加入新的關鍵字「**重設模型**」，將模型傳回原始格式。</span><span class="sxs-lookup"><span data-stu-id="29501-325">Add a new Keyword "**Reset Model**" to return the model to its original form.</span></span>

<span data-ttu-id="29501-326">我們會藉由在上一章中新增兩個關鍵字到語音輸入來源來完成此動作。</span><span class="sxs-lookup"><span data-stu-id="29501-326">We'll do this by adding two more keywords to the Speech Input Source from the previous chapter.</span></span> <span data-ttu-id="29501-327">我們也將示範另一種處理辨識事件的方式。</span><span class="sxs-lookup"><span data-stu-id="29501-327">We'll also demonstrate another way to handle recognition events.</span></span>

1. <span data-ttu-id="29501-328">在偵測器**中按一下**[上一頁]，然後展開 [**檢查**] 中的 [**關鍵字**] 區段。</span><span class="sxs-lookup"><span data-stu-id="29501-328">Click back on **AstronautManager** in the **Inspector** and expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="29501-329">按一下右手邊的  **+** ，以加入新的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="29501-329">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="29501-330">輸入關鍵字作為 [**展開模型**]。</span><span class="sxs-lookup"><span data-stu-id="29501-330">Type the Keyword as **Expand Model**.</span></span> <span data-ttu-id="29501-331">如有需要，您可以隨意新增金鑰快捷方式。</span><span class="sxs-lookup"><span data-stu-id="29501-331">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="29501-332">按一下右手邊的  **+** ，以加入新的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="29501-332">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="29501-333">輸入關鍵字作為 [**重設模型**]。</span><span class="sxs-lookup"><span data-stu-id="29501-333">Type the Keyword as **Reset Model**.</span></span> <span data-ttu-id="29501-334">如有需要，您可以隨意新增金鑰快捷方式。</span><span class="sxs-lookup"><span data-stu-id="29501-334">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="29501-335">在 [偵測**器**] 面板中，按一下 [**新增元件**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="29501-335">In the **Inspector** panel, click the **Add Component** button.</span></span>
7. <span data-ttu-id="29501-336">在功能表中，于 [**語音輸入處理常式**] 搜尋方塊中輸入。</span><span class="sxs-lookup"><span data-stu-id="29501-336">In the menu, type in the search box **Speech Input Handler**.</span></span> <span data-ttu-id="29501-337">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="29501-337">Select the search result.</span></span>
8. <span data-ttu-id="29501-338">檢查**是全域接聽程式**，因為我們想要讓這些命令都能正常執行，而不受我們所關注的 GameObject。</span><span class="sxs-lookup"><span data-stu-id="29501-338">Check **Is Global Listener**, since we want these commands to work regardless of the GameObject we're focusing.</span></span>
9. <span data-ttu-id="29501-339">按一下 [ **+** ] 按鈕，然後從 [關鍵字] 下拉式清單中選取 [**展開模型**]。</span><span class="sxs-lookup"><span data-stu-id="29501-339">Click the **+** button and select **Expand Model** from the Keyword dropdown.</span></span>
10. <span data-ttu-id="29501-340">按一下 [回應] 底下的 [ **+** ]，然後將**AstronautManager**從階層**拖曳至 [** 無] **（物件）** 欄位。</span><span class="sxs-lookup"><span data-stu-id="29501-340">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
11. <span data-ttu-id="29501-341">現在，按一下 [**沒有**函式] 下拉式清單，選取 [ **AstronautManager**]，然後選取 [ **ExpandModelCommand**]。</span><span class="sxs-lookup"><span data-stu-id="29501-341">Now, click the **No Function** dropdown, select **AstronautManager**, then **ExpandModelCommand**.</span></span>
12. <span data-ttu-id="29501-342">按一下語音輸入處理常式的 **+**  按鈕，然後從 關鍵字 下拉式清單中選取 **重設模型**。</span><span class="sxs-lookup"><span data-stu-id="29501-342">Click the Speech Input Handler's **+** button and select **Reset Model** from the Keyword dropdown.</span></span>
13. <span data-ttu-id="29501-343">按一下 [回應] 底下的 [ **+** ]，然後將**AstronautManager**從階層**拖曳至 [** 無] **（物件）** 欄位。</span><span class="sxs-lookup"><span data-stu-id="29501-343">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
14. <span data-ttu-id="29501-344">現在，按一下 [**沒有**函式] 下拉式清單，選取 [ **AstronautManager**]，然後選取 [ **ResetModelCommand**]。</span><span class="sxs-lookup"><span data-stu-id="29501-344">Now, click the **No Function** dropdown, select **AstronautManager**, then **ResetModelCommand**.</span></span>

![如何設定第5章的語音輸入來源和處理常式](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a><span data-ttu-id="29501-346">組建和部署</span><span class="sxs-lookup"><span data-stu-id="29501-346">Build and Deploy</span></span>

* <span data-ttu-id="29501-347">試試看！</span><span class="sxs-lookup"><span data-stu-id="29501-347">Try it!</span></span> <span data-ttu-id="29501-348">建立應用程式並將其部署至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="29501-348">Build and deploy the app to the HoloLens.</span></span>
* <span data-ttu-id="29501-349">假設**展開模型**以查看展開的太空人模型。</span><span class="sxs-lookup"><span data-stu-id="29501-349">Say **Expand Model** to see the expanded astronaut model.</span></span>
* <span data-ttu-id="29501-350">使用 [**導覽**] 來旋轉太空人花色的個別部分。</span><span class="sxs-lookup"><span data-stu-id="29501-350">Use **Navigation** to rotate individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="29501-351">假設**Move 太空人**，然後使用**操作**來移動太空人花色的個別部分。</span><span class="sxs-lookup"><span data-stu-id="29501-351">Say **Move Astronaut** and then use **Manipulation** to move individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="29501-352">假設 [**旋轉太空人**] 再次旋轉各部分。</span><span class="sxs-lookup"><span data-stu-id="29501-352">Say **Rotate Astronaut** to rotate the pieces again.</span></span>
* <span data-ttu-id="29501-353">假設 [**重設模型**] 會將太空人回到其原始表單。</span><span class="sxs-lookup"><span data-stu-id="29501-353">Say **Reset Model** to return the astronaut to its original form.</span></span>

## <a name="the-end"></a><span data-ttu-id="29501-354">結束</span><span class="sxs-lookup"><span data-stu-id="29501-354">The End</span></span>

<span data-ttu-id="29501-355">恭喜！</span><span class="sxs-lookup"><span data-stu-id="29501-355">Congratulations!</span></span> <span data-ttu-id="29501-356">您現在已完成**MR 輸入211：手勢**。</span><span class="sxs-lookup"><span data-stu-id="29501-356">You have now completed **MR Input 211: Gesture**.</span></span>

* <span data-ttu-id="29501-357">您知道如何偵測和回應手動追蹤、導覽和操作事件。</span><span class="sxs-lookup"><span data-stu-id="29501-357">You know how to detect and respond to hand tracking, navigation and manipulation events.</span></span>
* <span data-ttu-id="29501-358">您瞭解導覽和動作筆勢之間的差異。</span><span class="sxs-lookup"><span data-stu-id="29501-358">You understand the difference between Navigation and Manipulation gestures.</span></span>
* <span data-ttu-id="29501-359">您知道如何變更游標，以便在偵測到手時、即將遺失時，以及物件支援不同互動（導覽與操作）時，提供視覺效果的意見反應。</span><span class="sxs-lookup"><span data-stu-id="29501-359">You know how to change the cursor to provide visual feedback for when a hand is detected, when a hand is about to be lost, and for when an object supports different interactions (Navigation vs Manipulation).</span></span>
