---
title: MR 輸入 210-注視
description: 請遵循使用 Unity、Visual Studio 和 HoloLens 進行的編碼逐步解說, 以深入瞭解看看概念的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, 學院, 教學課程, 注視
ms.openlocfilehash: 076314389ec5ed70347c26d50c6a993f55da0758
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993549"
---
>[!NOTE]
><span data-ttu-id="3f436-104">混合現實學術教學課程的設計是使用 HoloLens (第1代) 和混合現實的沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="3f436-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="3f436-105">因此, 對於仍在尋找這些裝置開發指引的開發人員而言, 我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="3f436-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="3f436-106">這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="3f436-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="3f436-107">系統會保留這些資訊, 以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="3f436-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="3f436-108">未來將會有一系列新的教學課程, 將示範如何針對 HoloLens 2 進行開發。</span><span class="sxs-lookup"><span data-stu-id="3f436-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="3f436-109">此通知會在張貼時, 使用這些教學課程的連結進行更新。</span><span class="sxs-lookup"><span data-stu-id="3f436-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-210-gaze"></a><span data-ttu-id="3f436-110">MR 輸入 210:注視</span><span class="sxs-lookup"><span data-stu-id="3f436-110">MR Input 210: Gaze</span></span>

<span data-ttu-id="3f436-111">[注視](gaze.md)是第一種形式的輸入, 並顯示使用者的意圖和認知。</span><span class="sxs-lookup"><span data-stu-id="3f436-111">[Gaze](gaze.md) is the first form of input and reveals the user's intent and awareness.</span></span> <span data-ttu-id="3f436-112">MR Input 210 (也稱為 Project Explorer) 是深入探討 Windows Mixed Reality 的注視相關概念。</span><span class="sxs-lookup"><span data-stu-id="3f436-112">MR Input 210 (aka Project Explorer) is a deep dive into gaze-related concepts for Windows Mixed Reality.</span></span> <span data-ttu-id="3f436-113">我們將會對游標和全息影像新增內容感知, 並充分利用您的應用程式對使用者注視的認識。</span><span class="sxs-lookup"><span data-stu-id="3f436-113">We will be adding contextual awareness to our cursor and holograms, taking full advantage of what your app knows about the user's gaze.</span></span>

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

<span data-ttu-id="3f436-114">這裡有一個很好用的太空人, 可協助您瞭解一些概念。</span><span class="sxs-lookup"><span data-stu-id="3f436-114">We have a friendly astronaut here to help you learn gaze concepts.</span></span> <span data-ttu-id="3f436-115">在[MR 基本概念 101](holograms-101.md)中, 我們有一個簡單的游標, 只是看著您的注視。</span><span class="sxs-lookup"><span data-stu-id="3f436-115">In [MR Basics 101](holograms-101.md), we had a simple cursor that just followed your gaze.</span></span> <span data-ttu-id="3f436-116">今天, 我們要將一個步驟移到簡單的資料指標之外:</span><span class="sxs-lookup"><span data-stu-id="3f436-116">Today we're moving a step beyond the simple cursor:</span></span>

* <span data-ttu-id="3f436-117">我們會讓游標和我們的全息影像看起來很清楚: 兩者都會根據使用者的外觀, 或使用者*不*在尋找的位置而變更。</span><span class="sxs-lookup"><span data-stu-id="3f436-117">We're making the cursor and our holograms gaze-aware: both will change based on where the user is looking - or where the user is *not* looking.</span></span> <span data-ttu-id="3f436-118">這可讓他們瞭解內容。</span><span class="sxs-lookup"><span data-stu-id="3f436-118">This makes them context-aware.</span></span>
* <span data-ttu-id="3f436-119">我們會將意見反應新增至游標和全息影像, 以提供使用者更多有關目標的內容。</span><span class="sxs-lookup"><span data-stu-id="3f436-119">We will add feedback to our cursor and holograms to give the user more context on what is being targeted.</span></span> <span data-ttu-id="3f436-120">此意見反應可以是音訊和視覺效果。</span><span class="sxs-lookup"><span data-stu-id="3f436-120">This feedback can be audio and visual.</span></span>
* <span data-ttu-id="3f436-121">我們將示範如何以協助使用者達到較小目標的技術為目標。</span><span class="sxs-lookup"><span data-stu-id="3f436-121">We'll show you targeting techniques to help users hit smaller targets.</span></span>
* <span data-ttu-id="3f436-122">我們將示範如何使用方向指標, 將使用者的注意力繪製到您的全息影像。</span><span class="sxs-lookup"><span data-stu-id="3f436-122">We'll show you how to draw the user's attention to your holograms with a directional indicator.</span></span>
* <span data-ttu-id="3f436-123">我們會告訴您, 您可以在世界各地移動您的全息和使用者。</span><span class="sxs-lookup"><span data-stu-id="3f436-123">We'll teach you techniques to take your holograms with the user as she moves around in your world.</span></span>

>[!IMPORTANT]
><span data-ttu-id="3f436-124">下列各章節所內嵌的影片, 都是使用舊版 Unity 和混合現實工具組錄製的。</span><span class="sxs-lookup"><span data-stu-id="3f436-124">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="3f436-125">雖然逐步指示是正確且最新的, 但您可能會在已過期的對應影片中看到腳本和視覺效果。</span><span class="sxs-lookup"><span data-stu-id="3f436-125">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="3f436-126">影片仍包含在 posterity 中, 因為涵蓋的概念仍適用。</span><span class="sxs-lookup"><span data-stu-id="3f436-126">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="3f436-127">裝置支援</span><span class="sxs-lookup"><span data-stu-id="3f436-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="3f436-128">粗</span><span class="sxs-lookup"><span data-stu-id="3f436-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="3f436-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="3f436-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="3f436-130"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="3f436-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="3f436-131">MR 輸入 210:注視</span><span class="sxs-lookup"><span data-stu-id="3f436-131">MR Input 210: Gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="3f436-132">✔️</span><span class="sxs-lookup"><span data-stu-id="3f436-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="3f436-133">✔️</span><span class="sxs-lookup"><span data-stu-id="3f436-133">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="3f436-134">開始之前</span><span class="sxs-lookup"><span data-stu-id="3f436-134">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="3f436-135">必要條件</span><span class="sxs-lookup"><span data-stu-id="3f436-135">Prerequisites</span></span>

* <span data-ttu-id="3f436-136">[已安裝正確工具](install-the-tools.md)的 WINDOWS 10 電腦。</span><span class="sxs-lookup"><span data-stu-id="3f436-136">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="3f436-137">一些基本C#的程式設計能力。</span><span class="sxs-lookup"><span data-stu-id="3f436-137">Some basic C# programming ability.</span></span>
* <span data-ttu-id="3f436-138">您應已完成[MR 基本概念 101](holograms-101.md)。</span><span class="sxs-lookup"><span data-stu-id="3f436-138">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="3f436-139">[為開發設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="3f436-139">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="3f436-140">專案檔案</span><span class="sxs-lookup"><span data-stu-id="3f436-140">Project files</span></span>

* <span data-ttu-id="3f436-141">下載專案所需的[檔案](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip)。</span><span class="sxs-lookup"><span data-stu-id="3f436-141">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) required by the project.</span></span><span data-ttu-id="3f436-142"> 需要 Unity 2017.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="3f436-142"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="3f436-143">將檔案取消封存至您的桌面或其他容易到達的位置。</span><span class="sxs-lookup"><span data-stu-id="3f436-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="3f436-144">如果您想要在下載之前查看原始程式碼, 可以[在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze)取得。</span><span class="sxs-lookup"><span data-stu-id="3f436-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="3f436-145">勘誤和注意事項</span><span class="sxs-lookup"><span data-stu-id="3f436-145">Errata and Notes</span></span>

* <span data-ttu-id="3f436-146">在 Visual Studio 中, 必須停用 (取消核取) [工具-> 選項] 下 > 的 [Just My Code], 才能在程式碼中叫用中斷點。</span><span class="sxs-lookup"><span data-stu-id="3f436-146">In Visual Studio, "Just My Code" needs to be disabled (unchecked) under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="3f436-147">第1章-Unity 設定</span><span class="sxs-lookup"><span data-stu-id="3f436-147">Chapter 1 - Unity Setup</span></span>

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a><span data-ttu-id="3f436-148">目標</span><span class="sxs-lookup"><span data-stu-id="3f436-148">Objectives</span></span>

* <span data-ttu-id="3f436-149">最佳化 Unity 以用於 HoloLens 開發。</span><span class="sxs-lookup"><span data-stu-id="3f436-149">Optimize Unity for HoloLens development.</span></span>
* <span data-ttu-id="3f436-150">匯入資產並設定場景。</span><span class="sxs-lookup"><span data-stu-id="3f436-150">Import assets and setup the scene.</span></span>
* <span data-ttu-id="3f436-151">查看 HoloLens 中的太空人。</span><span class="sxs-lookup"><span data-stu-id="3f436-151">View the astronaut in the HoloLens.</span></span>

### <a name="instructions"></a><span data-ttu-id="3f436-152">指示</span><span class="sxs-lookup"><span data-stu-id="3f436-152">Instructions</span></span>

1. <span data-ttu-id="3f436-153">啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="3f436-153">Start Unity.</span></span>
2. <span data-ttu-id="3f436-154">選取 [**新增專案**]。</span><span class="sxs-lookup"><span data-stu-id="3f436-154">Select **New Project**.</span></span>
3. <span data-ttu-id="3f436-155">將專案命名為**ModelExplorer**。</span><span class="sxs-lookup"><span data-stu-id="3f436-155">Name the project **ModelExplorer**.</span></span>
4. <span data-ttu-id="3f436-156">輸入 [位置] 作為您先前取消封存的 [**注視**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="3f436-156">Enter location as the **Gaze** folder you previously un-archived.</span></span>
5. <span data-ttu-id="3f436-157">確定專案已設定為 **3D**。</span><span class="sxs-lookup"><span data-stu-id="3f436-157">Make sure the project is set to **3D**.</span></span>
6. <span data-ttu-id="3f436-158">按一下 [建立專案]。</span><span class="sxs-lookup"><span data-stu-id="3f436-158">Click **Create Project**.</span></span>

### <a name="unity-settings-for-hololens"></a><span data-ttu-id="3f436-159">HoloLens 的 Unity 設定</span><span class="sxs-lookup"><span data-stu-id="3f436-159">Unity settings for HoloLens</span></span>

<span data-ttu-id="3f436-160">我們需要讓 Unity 知道, 我們嘗試匯出的應用程式應該建立[沉浸式視圖](app-views.md), 而不是2d 視圖。</span><span class="sxs-lookup"><span data-stu-id="3f436-160">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="3f436-161">我們的作法是將 HoloLens 新增為虛擬實境裝置。</span><span class="sxs-lookup"><span data-stu-id="3f436-161">We do that by adding HoloLens as a virtual reality device.</span></span>

1. <span data-ttu-id="3f436-162">移至 **編輯 > 專案設定 > Player**。</span><span class="sxs-lookup"><span data-stu-id="3f436-162">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="3f436-163">在 [玩家設定] 的 [偵測**器] 面板**中, 選取 [ **Windows Store** ] 圖示。</span><span class="sxs-lookup"><span data-stu-id="3f436-163">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="3f436-164">展開 [ **XR 設定**] 群組。</span><span class="sxs-lookup"><span data-stu-id="3f436-164">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="3f436-165">在轉譯區段中, 勾選 [**支援虛擬實境**] 核取方塊, 以新增**虛擬實境 sdk**清單。</span><span class="sxs-lookup"><span data-stu-id="3f436-165">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="3f436-166">確認清單中出現**Windows Mixed Reality** 。</span><span class="sxs-lookup"><span data-stu-id="3f436-166">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="3f436-167">如果沒有，請選取 **+** 按鈕在清單底部，然後選擇**Windows 全像攝影版**。</span><span class="sxs-lookup"><span data-stu-id="3f436-167">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>

<span data-ttu-id="3f436-168">接下來, 我們需要將腳本後端設定為 .NET。</span><span class="sxs-lookup"><span data-stu-id="3f436-168">Next, we need to set our scripting backend to .NET.</span></span>

1. <span data-ttu-id="3f436-169">移至 **編輯 > 專案設定 > 播放** (您在上一個步驟中可能還是會這麼做)。</span><span class="sxs-lookup"><span data-stu-id="3f436-169">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="3f436-170">在 [玩家設定] 的 [偵測**器] 面板**中, 選取 [ **Windows Store** ] 圖示。</span><span class="sxs-lookup"><span data-stu-id="3f436-170">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="3f436-171">在 [**其他設定**] 區段中, 確認 [**腳本後端**] 已設定為 [ **.net** ]</span><span class="sxs-lookup"><span data-stu-id="3f436-171">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="3f436-172">最後, 我們會更新我們的品質設定, 以在 HoloLens 上達到快速的效能。</span><span class="sxs-lookup"><span data-stu-id="3f436-172">Finally, we'll update our quality settings to achieve a fast performance on HoloLens.</span></span>

1. <span data-ttu-id="3f436-173">移至 **編輯 > 專案設定 > 品質**。</span><span class="sxs-lookup"><span data-stu-id="3f436-173">Go to **Edit > Project Settings > Quality**.</span></span>
2. <span data-ttu-id="3f436-174">在 Windows 市集中圖示底下的**預設**資料列中, 按一下向下箭號。</span><span class="sxs-lookup"><span data-stu-id="3f436-174">Click on downward pointing arrow in the **Default** row under the Windows Store icon.</span></span>
3. <span data-ttu-id="3f436-175">對於**Windows Store 應用程式**, 請選取 [**非常低**]。</span><span class="sxs-lookup"><span data-stu-id="3f436-175">Select **Very Low** for **Windows Store Apps**.</span></span>

### <a name="import-project-assets"></a><span data-ttu-id="3f436-176">匯入專案資產</span><span class="sxs-lookup"><span data-stu-id="3f436-176">Import project assets</span></span>

1. <span data-ttu-id="3f436-177">在 [**專案**] 面板中, 以滑鼠右鍵按一下 [**資產**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="3f436-177">Right click the **Assets** folder in the **Project** panel.</span></span>
2. <span data-ttu-id="3f436-178">按一下 [匯**入封裝 > 自訂套件**]。</span><span class="sxs-lookup"><span data-stu-id="3f436-178">Click on **Import Package > Custom Package**.</span></span>
3. <span data-ttu-id="3f436-179">流覽至您所下載的專案檔, 然後按一下 [ **ModelExplorer unitypackage**]。</span><span class="sxs-lookup"><span data-stu-id="3f436-179">Navigate to the project files you downloaded and click on **ModelExplorer.unitypackage**.</span></span>
4. <span data-ttu-id="3f436-180">按一下 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="3f436-180">Click **Open**.</span></span>
5. <span data-ttu-id="3f436-181">封裝載入之後, 按一下 [匯**入**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3f436-181">After the package loads, click on the **Import** button.</span></span>

### <a name="setup-the-scene"></a><span data-ttu-id="3f436-182">設定場景</span><span class="sxs-lookup"><span data-stu-id="3f436-182">Setup the scene</span></span>

1. <span data-ttu-id="3f436-183">在階層中, 刪除**主要相機**。</span><span class="sxs-lookup"><span data-stu-id="3f436-183">In the Hierarchy, delete the **Main Camera**.</span></span>
2. <span data-ttu-id="3f436-184">在**HoloToolkit**資料夾中, 開啟 [**輸入**] 資料夾, 然後開啟 [ **Prefabs** ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="3f436-184">In the **HoloToolkit** folder, open the **Input** folder, then open the **Prefabs** folder.</span></span>
3. <span data-ttu-id="3f436-185">將**MixedRealityCameraParent** Prefab 從**Prefabs**資料夾拖放到階層中。</span><span class="sxs-lookup"><span data-stu-id="3f436-185">Drag and drop the **MixedRealityCameraParent** prefab from the **Prefabs** folder into the **Hierarchy**.</span></span>
4. <span data-ttu-id="3f436-186">以滑鼠右鍵按一下階層中的 [**方向光源**], 然後選取 [**刪除**]。</span><span class="sxs-lookup"><span data-stu-id="3f436-186">Right-click the **Directional Light** in the Hierarchy and select **Delete**.</span></span>
5. <span data-ttu-id="3f436-187">在 [**全息影像**] 資料夾中, 將下列資產拖放到階層的根目錄中:</span><span class="sxs-lookup"><span data-stu-id="3f436-187">In the **Holograms** folder, drag and drop the following assets into the root of the **Hierarchy**:</span></span>
    * <span data-ttu-id="3f436-188">**AstroMan**</span><span class="sxs-lookup"><span data-stu-id="3f436-188">**AstroMan**</span></span>
    * <span data-ttu-id="3f436-189">**無**</span><span class="sxs-lookup"><span data-stu-id="3f436-189">**Lights**</span></span>
    * <span data-ttu-id="3f436-190">**SpaceAudioSource**</span><span class="sxs-lookup"><span data-stu-id="3f436-190">**SpaceAudioSource**</span></span>
    * <span data-ttu-id="3f436-191">**SpaceBackground**</span><span class="sxs-lookup"><span data-stu-id="3f436-191">**SpaceBackground**</span></span>
6. <span data-ttu-id="3f436-192">啟動**播放模式**▶以觀看太空人。</span><span class="sxs-lookup"><span data-stu-id="3f436-192">Start **Play Mode** ▶ to view the astronaut.</span></span>
7. <span data-ttu-id="3f436-193">再次按一下 [**播放模式]** ▶**停止**。</span><span class="sxs-lookup"><span data-stu-id="3f436-193">Click **Play Mode** ▶ again to **Stop**.</span></span>
8. <span data-ttu-id="3f436-194">在 [**全息影像**] 資料夾中, 尋找**Fitbox**資產, 並將它拖曳到階層的根目錄。</span><span class="sxs-lookup"><span data-stu-id="3f436-194">In the **Holograms** folder, find the **Fitbox** asset and drag it to the root of the **Hierarchy**.</span></span>
9. <span data-ttu-id="3f436-195">在 [階層] 面板中選取**Fitbox** 。</span><span class="sxs-lookup"><span data-stu-id="3f436-195">Select the **Fitbox** in the **Hierarchy** panel.</span></span>
10. <span data-ttu-id="3f436-196">從階層中, 將**AstroMan**集合拖曳至 [偵測**器**] 面板中 Fitbox 的 [ **全息影像集合**] 屬性。</span><span class="sxs-lookup"><span data-stu-id="3f436-196">Drag the **AstroMan** collection from the **Hierarchy** to the **Hologram Collection** property of the Fitbox in the **Inspector** panel.</span></span>

### <a name="save-the-project"></a><span data-ttu-id="3f436-197">儲存專案</span><span class="sxs-lookup"><span data-stu-id="3f436-197">Save the project</span></span>

1. <span data-ttu-id="3f436-198">儲存新場景:檔案 **> 另存場景**。</span><span class="sxs-lookup"><span data-stu-id="3f436-198">Save the new scene: **File > Save Scene As**.</span></span>
2. <span data-ttu-id="3f436-199">按一下 [**新增資料夾**], 並將資料夾命名為**場景**。</span><span class="sxs-lookup"><span data-stu-id="3f436-199">Click **New Folder** and name the folder **Scenes**.</span></span>
3. <span data-ttu-id="3f436-200">將檔案命名為 "**ModelExplorer**", 並將它儲存在 [**幕後**] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="3f436-200">Name the file “**ModelExplorer**” and save it in the **Scenes** folder.</span></span>

### <a name="build-the-project"></a><span data-ttu-id="3f436-201">建立專案</span><span class="sxs-lookup"><span data-stu-id="3f436-201">Build the project</span></span>

1. <span data-ttu-id="3f436-202">在 Unity 中, 選取 [檔案] **> [組建設定**]。</span><span class="sxs-lookup"><span data-stu-id="3f436-202">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="3f436-203">按一下 [新增] [**開啟場景**] 以加入場景。</span><span class="sxs-lookup"><span data-stu-id="3f436-203">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="3f436-204">在 [**平臺**] 清單中選取**通用 Windows 平臺**, 然後按一下 [**切換平臺**]。</span><span class="sxs-lookup"><span data-stu-id="3f436-204">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="3f436-205">如果您是特別針對 HoloLens 進行開發, 請將**目標裝置**設定為**hololens**。</span><span class="sxs-lookup"><span data-stu-id="3f436-205">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="3f436-206">否則, 請將它保留在**任何裝置**上。</span><span class="sxs-lookup"><span data-stu-id="3f436-206">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="3f436-207">確定 [**組建類型**] 設定為 [ **D3D** ], 並將 [ **sdk** ] 設定為 [**已安裝最新**版本] (應該是 SDK 16299 或更新版本)。</span><span class="sxs-lookup"><span data-stu-id="3f436-207">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="3f436-208">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="3f436-208">Click **Build**.</span></span>
7. <span data-ttu-id="3f436-209">建立名為 "App" 的**新資料夾**。</span><span class="sxs-lookup"><span data-stu-id="3f436-209">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="3f436-210">按一下 [**應用程式**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="3f436-210">Single click the **App** folder.</span></span>
9. <span data-ttu-id="3f436-211">按 [**選取資料夾**]。</span><span class="sxs-lookup"><span data-stu-id="3f436-211">Press **Select Folder**.</span></span>

<span data-ttu-id="3f436-212">當 Unity 完成時, 將會出現 [檔案瀏覽器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="3f436-212">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="3f436-213">開啟**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="3f436-213">Open the **App** folder.</span></span>
2. <span data-ttu-id="3f436-214">開啟**ModelExplorer Visual Studio 解決方案**。</span><span class="sxs-lookup"><span data-stu-id="3f436-214">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="3f436-215">如果部署至 HoloLens:</span><span class="sxs-lookup"><span data-stu-id="3f436-215">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="3f436-216">使用 Visual Studio 中的頂端工具列, 將目標從 [調試] 變更為 [**發行**], 將 [從 ARM] 變更為**x86**。</span><span class="sxs-lookup"><span data-stu-id="3f436-216">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="3f436-217">按一下 [本機電腦] 按鈕旁的下拉式箭號, 然後選取 [**遠端電腦**]。</span><span class="sxs-lookup"><span data-stu-id="3f436-217">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="3f436-218">輸入**您的 HoloLens 裝置 IP 位址**, 並將驗證模式設定為 **[通用 (未加密的通訊協定)** ]。</span><span class="sxs-lookup"><span data-stu-id="3f436-218">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="3f436-219">按一下 [選取]。</span><span class="sxs-lookup"><span data-stu-id="3f436-219">Click **Select**.</span></span> <span data-ttu-id="3f436-220">如果您不知道您的裝置 IP 位址, 請查看 [設定] [ **> Network & Internet] > [Advanced Options**]。</span><span class="sxs-lookup"><span data-stu-id="3f436-220">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="3f436-221">在頂端功能表列中, 按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="3f436-221">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="3f436-222">如果這是您第一次部署至您的裝置, 您必須將[它與 Visual Studio 配對](using-visual-studio.md#pairing-your-device-hololens)。</span><span class="sxs-lookup"><span data-stu-id="3f436-222">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="3f436-223">應用程式部署完成後, 請使用**select 手勢**來關閉**Fitbox** 。</span><span class="sxs-lookup"><span data-stu-id="3f436-223">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="3f436-224">如果部署到沉浸式耳機:</span><span class="sxs-lookup"><span data-stu-id="3f436-224">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="3f436-225">使用 Visual Studio 中的頂端工具列, 將目標從 [調試] 變更為 [**發行**], 將 [從 ARM] 變更為**x64**。</span><span class="sxs-lookup"><span data-stu-id="3f436-225">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="3f436-226">請確定 [部署目標] 設定為 [**本機電腦**]。</span><span class="sxs-lookup"><span data-stu-id="3f436-226">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="3f436-227">在頂端功能表列中, 按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="3f436-227">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="3f436-228">應用程式部署完成後, 請藉由在動作控制器上提取觸發程式來關閉**Fitbox** 。</span><span class="sxs-lookup"><span data-stu-id="3f436-228">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

## <a name="chapter-2---cursor-and-target-feedback"></a><span data-ttu-id="3f436-229">第2章-資料指標和目標意見反應</span><span class="sxs-lookup"><span data-stu-id="3f436-229">Chapter 2 - Cursor and target feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a><span data-ttu-id="3f436-230">目標</span><span class="sxs-lookup"><span data-stu-id="3f436-230">Objectives</span></span>

* <span data-ttu-id="3f436-231">游標視覺化設計和行為。</span><span class="sxs-lookup"><span data-stu-id="3f436-231">Cursor visual design and behavior.</span></span>
* <span data-ttu-id="3f436-232">注視游標的意見反應。</span><span class="sxs-lookup"><span data-stu-id="3f436-232">Gaze-based cursor feedback.</span></span>
* <span data-ttu-id="3f436-233">以注視式的全息影像意見反應。</span><span class="sxs-lookup"><span data-stu-id="3f436-233">Gaze-based hologram feedback.</span></span>

<span data-ttu-id="3f436-234">我們將根據一些資料指標設計原則來進行工作, 也就是:</span><span class="sxs-lookup"><span data-stu-id="3f436-234">We're going to base our work on some cursor design principles, namely:</span></span>

* <span data-ttu-id="3f436-235">資料指標一律存在。</span><span class="sxs-lookup"><span data-stu-id="3f436-235">The cursor is always present.</span></span>
* <span data-ttu-id="3f436-236">不要讓游標變得太小或太大。</span><span class="sxs-lookup"><span data-stu-id="3f436-236">Don't let the cursor get too small or big.</span></span>
* <span data-ttu-id="3f436-237">避免阻礙內容。</span><span class="sxs-lookup"><span data-stu-id="3f436-237">Avoid obstructing content.</span></span>

### <a name="instructions"></a><span data-ttu-id="3f436-238">指示</span><span class="sxs-lookup"><span data-stu-id="3f436-238">Instructions</span></span>

1. <span data-ttu-id="3f436-239">在**HoloToolkit\Input\Prefabs**資料夾中, 尋找**InputManager**資產。</span><span class="sxs-lookup"><span data-stu-id="3f436-239">In the **HoloToolkit\Input\Prefabs** folder, find the **InputManager** asset.</span></span>
2. <span data-ttu-id="3f436-240">將**InputManager**拖放到階層上。</span><span class="sxs-lookup"><span data-stu-id="3f436-240">Drag and drop the **InputManager** onto the **Hierarchy**.</span></span>
3. <span data-ttu-id="3f436-241">在**HoloToolkit\Input\Prefabs**資料夾中, 尋找資料**指標**資產。</span><span class="sxs-lookup"><span data-stu-id="3f436-241">In the **HoloToolkit\Input\Prefabs** folder, find the **Cursor** asset.</span></span>
4. <span data-ttu-id="3f436-242">將**游標**拖放到階層上。</span><span class="sxs-lookup"><span data-stu-id="3f436-242">Drag and drop the **Cursor** onto the **Hierarchy**.</span></span>
5. <span data-ttu-id="3f436-243">選取階層中的 [ **InputManager** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="3f436-243">Select the **InputManager** object in the **Hierarchy**.</span></span>
6. <span data-ttu-id="3f436-244">將**游標**物件從階層拖曳至 InputManager 的**SimpleSinglePointerSelector**的資料**指標**欄位 (位於偵測**器**底部)。</span><span class="sxs-lookup"><span data-stu-id="3f436-244">Drag the **Cursor** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>

![簡單單一指標選取器設定](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a><span data-ttu-id="3f436-246">組建和部署</span><span class="sxs-lookup"><span data-stu-id="3f436-246">Build and Deploy</span></span>

1. <span data-ttu-id="3f436-247">從 [檔案] **> 組建設定**重建應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f436-247">Rebuild the app from **File > Build Settings**.</span></span>
2. <span data-ttu-id="3f436-248">開啟**應用程式資料夾**。</span><span class="sxs-lookup"><span data-stu-id="3f436-248">Open the **App folder**.</span></span>
3. <span data-ttu-id="3f436-249">開啟**ModelExplorer Visual Studio 解決方案**。</span><span class="sxs-lookup"><span data-stu-id="3f436-249">Open the **ModelExplorer Visual Studio Solution**.</span></span>
4. <span data-ttu-id="3f436-250">按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="3f436-250">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
5. <span data-ttu-id="3f436-251">觀察游標的繪製方式, 以及它在觸及全息圖形時如何變更外觀。</span><span class="sxs-lookup"><span data-stu-id="3f436-251">Observe how the cursor is drawn, and how it changes appearance if it is touching a hologram.</span></span>

### <a name="instructions"></a><span data-ttu-id="3f436-252">指示</span><span class="sxs-lookup"><span data-stu-id="3f436-252">Instructions</span></span>

1. <span data-ttu-id="3f436-253">在 [階層] 面板中, 展開**AstroMan** -> **GEO_G** -> **Back_Center**物件。</span><span class="sxs-lookup"><span data-stu-id="3f436-253">In the **Hierarchy** panel, expand the **AstroMan**->**GEO_G**->**Back_Center** object.</span></span>
2. <span data-ttu-id="3f436-254">按兩下 [ **Interactible.cs** ], 在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="3f436-254">Double click on **Interactible.cs** to open it in Visual Studio.</span></span>
3. <span data-ttu-id="3f436-255">取消批註**Interactible.cs**中**IFocusable. OnFocusEnter ()** 和**IFocusable OnFocusExit ()** 回呼中的行。</span><span class="sxs-lookup"><span data-stu-id="3f436-255">Uncomment the lines in the **IFocusable.OnFocusEnter()** and **IFocusable.OnFocusExit()** callbacks in **Interactible.cs**.</span></span> <span data-ttu-id="3f436-256">當焦點 (由注視或控制器指向) 進入並結束特定 GameObject 的碰撞器時, 混合現實工具組的 InputManager 會呼叫這些方法。</span><span class="sxs-lookup"><span data-stu-id="3f436-256">These are called by the Mixed Reality Toolkit's InputManager when focus (either by gaze or by controller pointing) enters and exits the specific GameObject's collider.</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
><span data-ttu-id="3f436-257">我們使用`EnableKeyword`和`DisableKeyword`更新版本。</span><span class="sxs-lookup"><span data-stu-id="3f436-257">We use `EnableKeyword` and `DisableKeyword` above.</span></span> <span data-ttu-id="3f436-258">為了在您自己的應用程式中搭配使用工具組的標準著色器, 您必須遵循[Unity 指導方針, 透過腳本存取材質](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html)。</span><span class="sxs-lookup"><span data-stu-id="3f436-258">In order to make use of these in your own app with the Toolkit's Standard shader, you'll need to follow the [Unity guidelines for accessing materials via script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span></span> <span data-ttu-id="3f436-259">在此情況下, 我們已包含 [資源] 資料夾中所需反[白顯示材質的三種](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials)變化 (尋找名稱中有醒目提示的三個數據)。</span><span class="sxs-lookup"><span data-stu-id="3f436-259">In this case, we've already included the [three variants of highlighted material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) needed in the Resources folder (look for the three materials with highlight in the name).</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="3f436-260">組建和部署</span><span class="sxs-lookup"><span data-stu-id="3f436-260">Build and Deploy</span></span>

1. <span data-ttu-id="3f436-261">如先前所述, 建立專案並部署至 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="3f436-261">As before, build the project and deploy to the HoloLens.</span></span>
2. <span data-ttu-id="3f436-262">觀察當注視物件導向時所發生的情況, 以及不是什麼時候。</span><span class="sxs-lookup"><span data-stu-id="3f436-262">Observe what happens when the gaze is aimed at an object and when it's not.</span></span>

## <a name="chapter-3---targeting-techniques"></a><span data-ttu-id="3f436-263">第3章-目標技術</span><span class="sxs-lookup"><span data-stu-id="3f436-263">Chapter 3 - Targeting Techniques</span></span>

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a><span data-ttu-id="3f436-264">目標</span><span class="sxs-lookup"><span data-stu-id="3f436-264">Objectives</span></span>

* <span data-ttu-id="3f436-265">讓您更輕鬆地以全息影像為目標。</span><span class="sxs-lookup"><span data-stu-id="3f436-265">Make it easier to target holograms.</span></span>
* <span data-ttu-id="3f436-266">穩定的自然 head 移動。</span><span class="sxs-lookup"><span data-stu-id="3f436-266">Stabilize natural head movements.</span></span>

### <a name="instructions"></a><span data-ttu-id="3f436-267">指示</span><span class="sxs-lookup"><span data-stu-id="3f436-267">Instructions</span></span>

1. <span data-ttu-id="3f436-268">在 [階層] 面板中, 選取 [ **InputManager** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="3f436-268">In the **Hierarchy** panel, select the **InputManager** object.</span></span>
2. <span data-ttu-id="3f436-269">在 [偵測**器**] 面板中, 尋找**注視的穩定**器腳本。</span><span class="sxs-lookup"><span data-stu-id="3f436-269">In the **Inspector** panel, find the **Gaze Stabilizer** script.</span></span> <span data-ttu-id="3f436-270">如果您想要查看, 請按一下該檔案以在 Visual Studio 中開啟。</span><span class="sxs-lookup"><span data-stu-id="3f436-270">Click it to open in Visual Studio, if you want to take a look.</span></span>
    * <span data-ttu-id="3f436-271">此腳本會逐一查看 Raycast 資料的樣本, 並協助將使用者的注視變得穩定, 以達到精確目標。</span><span class="sxs-lookup"><span data-stu-id="3f436-271">This script iterates over samples of Raycast data and helps stabilize the user's gaze for precision targeting.</span></span>
3. <span data-ttu-id="3f436-272">在偵測**器**中, 您可以編輯**儲存的穩定性範例**值。</span><span class="sxs-lookup"><span data-stu-id="3f436-272">In the **Inspector**, you can edit the **Stored Stability Samples** value.</span></span> <span data-ttu-id="3f436-273">此值表示穩定程式會逐一查看以計算穩定值的樣本數。</span><span class="sxs-lookup"><span data-stu-id="3f436-273">This value represents the number of samples that the stabilizer iterates on to calculate the stabilized value.</span></span>

## <a name="chapter-4---directional-indicator"></a><span data-ttu-id="3f436-274">第4章-方向指標</span><span class="sxs-lookup"><span data-stu-id="3f436-274">Chapter 4 - Directional indicator</span></span>

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a><span data-ttu-id="3f436-275">目標</span><span class="sxs-lookup"><span data-stu-id="3f436-275">Objectives</span></span>

* <span data-ttu-id="3f436-276">在游標上新增方向指標, 以協助找出全息影像。</span><span class="sxs-lookup"><span data-stu-id="3f436-276">Add a directional indicator on the cursor to help find holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="3f436-277">指示</span><span class="sxs-lookup"><span data-stu-id="3f436-277">Instructions</span></span>

<span data-ttu-id="3f436-278">我們將使用**DirectionIndicator.cs**檔案, 它會:</span><span class="sxs-lookup"><span data-stu-id="3f436-278">We're going to use the **DirectionIndicator.cs** file which will:</span></span>

1. <span data-ttu-id="3f436-279">如果未在全息影像中撥雲見日使用者, 則顯示方向指標。</span><span class="sxs-lookup"><span data-stu-id="3f436-279">Show the directional indicator if the user is not gazing at the holograms.</span></span>
2. <span data-ttu-id="3f436-280">如果在全息影像中撥雲見日使用者, 則隱藏方向指標。</span><span class="sxs-lookup"><span data-stu-id="3f436-280">Hide the directional indicator if the user is gazing at the holograms.</span></span>
3. <span data-ttu-id="3f436-281">更新方向指標以指向全息影像。</span><span class="sxs-lookup"><span data-stu-id="3f436-281">Update the directional indicator to point to the holograms.</span></span>

<span data-ttu-id="3f436-282">那就開始吧。</span><span class="sxs-lookup"><span data-stu-id="3f436-282">Let's get started.</span></span>

1. <span data-ttu-id="3f436-283">按一下 [階層] 面板中的 [ **AstroMan** ] 物件, 然後**按一下箭**號將它展開。</span><span class="sxs-lookup"><span data-stu-id="3f436-283">Click on the **AstroMan** object in the **Hierarchy** panel and **click the arrow** to expand it.</span></span>
2. <span data-ttu-id="3f436-284">在 [階層] 面板中, 選取 [ **AstroMan**] 下的 [ **DirectionalIndicator** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="3f436-284">In the **Hierarchy** panel, select the **DirectionalIndicator** object under **AstroMan**.</span></span>
3. <span data-ttu-id="3f436-285">在 [偵測**器**] 面板中, 按一下 [**新增元件**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3f436-285">In the **Inspector** panel, click the **Add Component** button.</span></span>
4. <span data-ttu-id="3f436-286">在功能表中, 于搜尋方塊**方向指標**上輸入。</span><span class="sxs-lookup"><span data-stu-id="3f436-286">In the menu, type in the search box **Direction Indicator**.</span></span> <span data-ttu-id="3f436-287">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="3f436-287">Select the search result.</span></span>
5. <span data-ttu-id="3f436-288">在 [階層] 面板中, 將**游標**物件拖放至偵測**器**中的**cursor**屬性。</span><span class="sxs-lookup"><span data-stu-id="3f436-288">In the **Hierarchy** panel, drag and drop the **Cursor** object onto the **Cursor** property in the **Inspector**.</span></span>
6. <span data-ttu-id="3f436-289">在 [**專案**] 面板的 [**全息影像**] 資料夾中, 將**DirectionalIndicator**資產拖放至偵測**器**中的**方向指標**屬性。</span><span class="sxs-lookup"><span data-stu-id="3f436-289">In the **Project** panel, in the **Holograms** folder, drag and drop the **DirectionalIndicator** asset onto the **Directional Indicator** property in the **Inspector**.</span></span>
7. <span data-ttu-id="3f436-290">建立並部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f436-290">Build and deploy the app.</span></span>
8. <span data-ttu-id="3f436-291">觀看方向指標物件如何協助您尋找太空人。</span><span class="sxs-lookup"><span data-stu-id="3f436-291">Watch how the directional indicator object helps you find the astronaut.</span></span>

## <a name="chapter-5---billboarding"></a><span data-ttu-id="3f436-292">第5章-Billboarding</span><span class="sxs-lookup"><span data-stu-id="3f436-292">Chapter 5 - Billboarding</span></span>

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a><span data-ttu-id="3f436-293">目標</span><span class="sxs-lookup"><span data-stu-id="3f436-293">Objectives</span></span>

* <span data-ttu-id="3f436-294">使用 billboarding 讓全像投影永遠都能朝向您的臉。</span><span class="sxs-lookup"><span data-stu-id="3f436-294">Use billboarding to have holograms always face towards you.</span></span>

<span data-ttu-id="3f436-295">我們將使用**Billboard.cs**檔案來保留 GameObject 導向, 使其隨時面向使用者。</span><span class="sxs-lookup"><span data-stu-id="3f436-295">We will be using the **Billboard.cs** file to keep a GameObject oriented such that it is facing the user at all times.</span></span>

1. <span data-ttu-id="3f436-296">在 [階層] 面板中, 選取 [ **AstroMan** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="3f436-296">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
2. <span data-ttu-id="3f436-297">在 [偵測**器**] 面板中, 按一下 [**新增元件**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3f436-297">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="3f436-298">在功能表中, 于搜尋方塊中輸入**佈告欄**。</span><span class="sxs-lookup"><span data-stu-id="3f436-298">In the menu, type in the search box **Billboard**.</span></span> <span data-ttu-id="3f436-299">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="3f436-299">Select the search result.</span></span>
4. <span data-ttu-id="3f436-300">在 [偵測**器**] 中, 將 [ **Pivot 軸**] 設定為**Y**。</span><span class="sxs-lookup"><span data-stu-id="3f436-300">In the **Inspector** set the **Pivot Axis** to **Y**.</span></span>
5. <span data-ttu-id="3f436-301">試試看！</span><span class="sxs-lookup"><span data-stu-id="3f436-301">Try it!</span></span> <span data-ttu-id="3f436-302">如先前一樣, 建立和部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f436-302">Build and deploy the app as before.</span></span>
6. <span data-ttu-id="3f436-303">無論您如何改變觀點, 都能瞭解佈告欄物件的外觀。</span><span class="sxs-lookup"><span data-stu-id="3f436-303">See how the Billboard object faces you no matter how you change the viewpoint.</span></span>
7. <span data-ttu-id="3f436-304">立即從**AstroMan**刪除腳本。</span><span class="sxs-lookup"><span data-stu-id="3f436-304">Delete the script from the **AstroMan** for now.</span></span>

## <a name="chapter-6---tag-along"></a><span data-ttu-id="3f436-305">第6章-標記-沿著</span><span class="sxs-lookup"><span data-stu-id="3f436-305">Chapter 6 - Tag-Along</span></span>

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a><span data-ttu-id="3f436-306">目標</span><span class="sxs-lookup"><span data-stu-id="3f436-306">Objectives</span></span>

* <span data-ttu-id="3f436-307">使用標籤-並讓我們的全息影像沿著我們的房間來追蹤。</span><span class="sxs-lookup"><span data-stu-id="3f436-307">Use Tag-Along to have our holograms follow us around the room.</span></span>

<span data-ttu-id="3f436-308">當我們處理這個問題時, 我們會依照下列設計條件約束來引導我們:</span><span class="sxs-lookup"><span data-stu-id="3f436-308">As we work on this issue, we'll be guided by the following design constraints:</span></span>

* <span data-ttu-id="3f436-309">內容應該一律一目了然。</span><span class="sxs-lookup"><span data-stu-id="3f436-309">Content should always be a glance away.</span></span>
* <span data-ttu-id="3f436-310">內容不應為該方式。</span><span class="sxs-lookup"><span data-stu-id="3f436-310">Content should not be in the way.</span></span>
* <span data-ttu-id="3f436-311">Head 鎖定內容不舒服。</span><span class="sxs-lookup"><span data-stu-id="3f436-311">Head-locking content is uncomfortable.</span></span>

<span data-ttu-id="3f436-312">此處使用的解決方案是使用「標記為一」的方法。</span><span class="sxs-lookup"><span data-stu-id="3f436-312">The solution used here is to use a "tag-along" approach.</span></span>

<span data-ttu-id="3f436-313">標記物件永遠不會完全離開使用者的觀點。</span><span class="sxs-lookup"><span data-stu-id="3f436-313">A tag-along object never fully leaves the user's view.</span></span> <span data-ttu-id="3f436-314">您可以將一個標記視為一個物件, 並將它與使用者的標頭連接在一起。</span><span class="sxs-lookup"><span data-stu-id="3f436-314">You can think of the a tag-along as being an object attached to the user's head by rubber bands.</span></span> <span data-ttu-id="3f436-315">當使用者移動時, 內容會透過滑動到視野的邊緣而不會完全離開, 而保持在簡單概覽。</span><span class="sxs-lookup"><span data-stu-id="3f436-315">As the user moves, the content will stay within an easy glance by sliding towards the edge of the view without completely leaving.</span></span> <span data-ttu-id="3f436-316">當使用者 gazes 到標記物件時, 它會有更完整的視野。</span><span class="sxs-lookup"><span data-stu-id="3f436-316">When the user gazes towards the tag-along object, it comes more fully into view.</span></span>

<span data-ttu-id="3f436-317">我們將使用**SimpleTagalong.cs**檔案, 它會:</span><span class="sxs-lookup"><span data-stu-id="3f436-317">We're going to use the **SimpleTagalong.cs** file which will:</span></span>

1. <span data-ttu-id="3f436-318">判斷標記沿著的物件是否在相機界限內。</span><span class="sxs-lookup"><span data-stu-id="3f436-318">Determine if the Tag-Along object is within the camera bounds.</span></span>
2. <span data-ttu-id="3f436-319">如果不在視圖的 [截位] 中, 請將標記放在視圖的 [截維] 內。</span><span class="sxs-lookup"><span data-stu-id="3f436-319">If not within the view frustum, position the Tag-Along to partially within the view frustum.</span></span>
3. <span data-ttu-id="3f436-320">否則, 請將標記與使用者的預設距離放置在一起。</span><span class="sxs-lookup"><span data-stu-id="3f436-320">Otherwise, position the Tag-Along to a default distance from the user.</span></span>

<span data-ttu-id="3f436-321">若要這麼做, 我們必須先變更**Interactible.cs**腳本以呼叫**TagalongAction**。</span><span class="sxs-lookup"><span data-stu-id="3f436-321">To do this, we first must change the **Interactible.cs** script to call the **TagalongAction**.</span></span>

1. <span data-ttu-id="3f436-322">完成程式碼撰寫練習 6. (取消批註行84到 87) 來編輯**Interactible.cs** 。</span><span class="sxs-lookup"><span data-stu-id="3f436-322">Edit **Interactible.cs** by completing coding exercise 6.a (uncommenting lines 84 to 87).</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

<span data-ttu-id="3f436-323">當您按一下全息影像時, 與**Interactible.cs**配對的**InteractibleAction.cs**腳本會執行自訂動作。</span><span class="sxs-lookup"><span data-stu-id="3f436-323">The **InteractibleAction.cs** script, paired with **Interactible.cs** performs custom actions when you tap on holograms.</span></span> <span data-ttu-id="3f436-324">在此情況下, 我們會使用特別用於標記的一個。</span><span class="sxs-lookup"><span data-stu-id="3f436-324">In this case, we'll use one specifically for tag-along.</span></span>

* <span data-ttu-id="3f436-325">在 [**腳本**] 資料夾中, 按一下 [ **TagalongAction.cs**資產] 以在 Visual Studio 中開啟。</span><span class="sxs-lookup"><span data-stu-id="3f436-325">In the **Scripts** folder click on **TagalongAction.cs** asset to open in Visual Studio.</span></span>
* <span data-ttu-id="3f436-326">完成程式碼撰寫練習, 或將它變更為:</span><span class="sxs-lookup"><span data-stu-id="3f436-326">Complete the coding exercise or change it to this:</span></span>
  * <span data-ttu-id="3f436-327">在階層頂端的 [搜尋] 列中, 輸入**ChestButton_Center** , 然後選取結果。</span><span class="sxs-lookup"><span data-stu-id="3f436-327">At the top of the **Hierarchy**, in the search bar type **ChestButton_Center** and select the result.</span></span>
  * <span data-ttu-id="3f436-328">在 [偵測**器**] 面板中, 按一下 [**新增元件**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3f436-328">In the **Inspector** panel, click the **Add Component** button.</span></span>
  * <span data-ttu-id="3f436-329">在功能表中, 于 [搜尋] 方塊中輸入**Tagalong 動作**。</span><span class="sxs-lookup"><span data-stu-id="3f436-329">In the menu, type in the search box **Tagalong Action**.</span></span> <span data-ttu-id="3f436-330">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="3f436-330">Select the search result.</span></span>
  * <span data-ttu-id="3f436-331">在 [**全息影像**] 資料夾中, 尋找**Tagalong**資產。</span><span class="sxs-lookup"><span data-stu-id="3f436-331">In **Holograms** folder find the **Tagalong** asset.</span></span>
  * <span data-ttu-id="3f436-332">選取階層中的 [ **ChestButton_Center** ] 物件。</span><span class="sxs-lookup"><span data-stu-id="3f436-332">Select the **ChestButton_Center** object in the **Hierarchy**.</span></span> <span data-ttu-id="3f436-333">從 [**專案**] 面板中, 將**TagAlong**物件拖放到 [**要 TagAlong 的物件**] 屬性中。</span><span class="sxs-lookup"><span data-stu-id="3f436-333">Drag and drop the **TagAlong** object from the **Project** panel onto the **Inspector** into the **Object To Tagalong** property.</span></span>
  * <span data-ttu-id="3f436-334">將 [ **Tagalong 動作**] 物件從 [偵測**器**] 拖曳至**Interactible**腳本上的 [ **Interactible 動作**] 欄位中。</span><span class="sxs-lookup"><span data-stu-id="3f436-334">Drag the **Tagalong Action** object from the **Inspector** into the **Interactible Action** field on the **Interactible** script.</span></span>
* <span data-ttu-id="3f436-335">按兩下 [ **TagalongAction** ] 腳本, 在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="3f436-335">Double click the **TagalongAction** script to open it in Visual Studio.</span></span>

![Interactible 設定](images/holograms210-interactible.png)

<span data-ttu-id="3f436-337">我們需要新增下列內容:</span><span class="sxs-lookup"><span data-stu-id="3f436-337">We need to add the following:</span></span>

* <span data-ttu-id="3f436-338">將功能新增至 TagalongAction 腳本中的 PerformAction 函數 (繼承自 InteractibleAction)。</span><span class="sxs-lookup"><span data-stu-id="3f436-338">Add functionality to the PerformAction function in the TagalongAction script (inherited from InteractibleAction).</span></span>
* <span data-ttu-id="3f436-339">將 billboarding 新增至 gazed 物件, 並將 pivot 軸設定為 [XY]。</span><span class="sxs-lookup"><span data-stu-id="3f436-339">Add billboarding to the gazed-upon object, and set the pivot axis to XY.</span></span>
* <span data-ttu-id="3f436-340">然後將簡單的標記新增至物件。</span><span class="sxs-lookup"><span data-stu-id="3f436-340">Then add simple Tag-Along to the object.</span></span>

<span data-ttu-id="3f436-341">以下是來自**TagalongAction.cs**的解決方案:</span><span class="sxs-lookup"><span data-stu-id="3f436-341">Here's our solution, from **TagalongAction.cs**:</span></span>

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* <span data-ttu-id="3f436-342">試試看！</span><span class="sxs-lookup"><span data-stu-id="3f436-342">Try it!</span></span> <span data-ttu-id="3f436-343">建立並部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f436-343">Build and deploy the app.</span></span>
* <span data-ttu-id="3f436-344">監看內容在注視點的中心, 但不會持續且不會封鎖。</span><span class="sxs-lookup"><span data-stu-id="3f436-344">Watch how the content follows the center of the gaze point, but not continuously and without blocking it.</span></span>
