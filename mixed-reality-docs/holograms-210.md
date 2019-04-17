---
title: MR 輸入 210-視線
description: 遵循此程式碼逐步解說如何使用 Unity、 Visual Studio 和 HoloLens，若要了解視線概念的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit mixedrealitytoolkit、 mixedrealitytoolkit-academy，教學課程，視線 unity
ms.openlocfilehash: 63c55e8a7a348f2a3e0cc29a9795d7fabcef5df0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591563"
---
>[!NOTE]
><span data-ttu-id="0d268-104">混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。</span><span class="sxs-lookup"><span data-stu-id="0d268-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="0d268-105">因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。</span><span class="sxs-lookup"><span data-stu-id="0d268-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="0d268-106">這些教學課程會**_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="0d268-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="0d268-107">它們會繼續運作，支援的裝置上維護。</span><span class="sxs-lookup"><span data-stu-id="0d268-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="0d268-108">會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="0d268-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="0d268-109">當他們回傳時，本聲明將會更新這些教學課程的連結。</span><span class="sxs-lookup"><span data-stu-id="0d268-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-210-gaze"></a><span data-ttu-id="0d268-110">MR 輸入 210:注視</span><span class="sxs-lookup"><span data-stu-id="0d268-110">MR Input 210: Gaze</span></span>

<span data-ttu-id="0d268-111">[視線](gaze.md)是第一種形式的輸入，並會顯示使用者的意圖和感知。</span><span class="sxs-lookup"><span data-stu-id="0d268-111">[Gaze](gaze.md) is the first form of input and reveals the user's intent and awareness.</span></span> <span data-ttu-id="0d268-112">MR 輸入 210 (也稱為專案總管) 是深入探討 Windows Mixed Reality 視線相關概念。</span><span class="sxs-lookup"><span data-stu-id="0d268-112">MR Input 210 (aka Project Explorer) is a deep dive into gaze-related concepts for Windows Mixed Reality.</span></span> <span data-ttu-id="0d268-113">我們將新增內容感知到我們的資料指標和全像投影，充分利用您的應用程式知道使用者的視線有關。</span><span class="sxs-lookup"><span data-stu-id="0d268-113">We will be adding contextual awareness to our cursor and holograms, taking full advantage of what your app knows about the user's gaze.</span></span>

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

<span data-ttu-id="0d268-114">我們必須易記太空人這裡幫助您了解視線概念。</span><span class="sxs-lookup"><span data-stu-id="0d268-114">We have a friendly astronaut here to help you learn gaze concepts.</span></span> <span data-ttu-id="0d268-115">在  [MR 基本概念 101](holograms-101.md)，我們只是後接您的視線簡單資料指標。</span><span class="sxs-lookup"><span data-stu-id="0d268-115">In [MR Basics 101](holograms-101.md), we had a simple cursor that just followed your gaze.</span></span> <span data-ttu-id="0d268-116">今天我們要移動的簡單資料指標的後續步驟：</span><span class="sxs-lookup"><span data-stu-id="0d268-116">Today we're moving a step beyond the simple cursor:</span></span>

* <span data-ttu-id="0d268-117">我們將會讓資料指標而且我們全像投影視線注意： 同時會隨著使用者注視的位置-，或使用者所在*不*尋找。</span><span class="sxs-lookup"><span data-stu-id="0d268-117">We're making the cursor and our holograms gaze-aware: both will change based on where the user is looking - or where the user is *not* looking.</span></span> <span data-ttu-id="0d268-118">這讓它們更能感知環境。</span><span class="sxs-lookup"><span data-stu-id="0d268-118">This makes them context-aware.</span></span>
* <span data-ttu-id="0d268-119">我們會將我們的資料指標和全像投影至多個內容上所設定的目標是授與使用者意見反應。</span><span class="sxs-lookup"><span data-stu-id="0d268-119">We will add feedback to our cursor and holograms to give the user more context on what is being targeted.</span></span> <span data-ttu-id="0d268-120">此意見反應可以音訊和視覺化。</span><span class="sxs-lookup"><span data-stu-id="0d268-120">This feedback can be audio and visual.</span></span>
* <span data-ttu-id="0d268-121">我們將示範您目標的技術，可協助使用者點擊較小的目標。</span><span class="sxs-lookup"><span data-stu-id="0d268-121">We'll show you targeting techniques to help users hit smaller targets.</span></span>
* <span data-ttu-id="0d268-122">我們將示範如何強調使用者的您具有方向性指標全像投影。</span><span class="sxs-lookup"><span data-stu-id="0d268-122">We'll show you how to draw the user's attention to your holograms with a directional indicator.</span></span>
* <span data-ttu-id="0d268-123">我們會教導您全像投影需要與使用者，因為她在您的世界中移動的技術。</span><span class="sxs-lookup"><span data-stu-id="0d268-123">We'll teach you techniques to take your holograms with the user as she moves around in your world.</span></span>

>[!IMPORTANT]
><span data-ttu-id="0d268-124">使用 Unity 及混合實境 toolkit 的推出較舊的版本記錄中的下列章節的每個內嵌的影片。</span><span class="sxs-lookup"><span data-stu-id="0d268-124">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="0d268-125">雖然的逐步指示是準確且即時的您可能會看到指令碼和對應已過期的影片中的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="0d268-125">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="0d268-126">影片仍包含 posterity，和因為概念涵蓋仍然適用。</span><span class="sxs-lookup"><span data-stu-id="0d268-126">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="0d268-127">裝置支援</span><span class="sxs-lookup"><span data-stu-id="0d268-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="0d268-128">課程</span><span class="sxs-lookup"><span data-stu-id="0d268-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="0d268-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="0d268-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="0d268-130"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="0d268-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="0d268-131">MR 輸入 210:注視</span><span class="sxs-lookup"><span data-stu-id="0d268-131">MR Input 210: Gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="0d268-132">✔️</span><span class="sxs-lookup"><span data-stu-id="0d268-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="0d268-133">✔️</span><span class="sxs-lookup"><span data-stu-id="0d268-133">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="0d268-134">開始之前</span><span class="sxs-lookup"><span data-stu-id="0d268-134">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="0d268-135">必要條件</span><span class="sxs-lookup"><span data-stu-id="0d268-135">Prerequisites</span></span>

* <span data-ttu-id="0d268-136">Windows 10 電腦的正確設定[安裝工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="0d268-136">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="0d268-137">基本C#程式設計的能力。</span><span class="sxs-lookup"><span data-stu-id="0d268-137">Some basic C# programming ability.</span></span>
* <span data-ttu-id="0d268-138">您應已完成[MR 基本概念 101](holograms-101.md)。</span><span class="sxs-lookup"><span data-stu-id="0d268-138">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="0d268-139">HoloLens 裝置[開發設定的](using-visual-studio.md#enabling-developer-mode)。</span><span class="sxs-lookup"><span data-stu-id="0d268-139">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="0d268-140">專案檔</span><span class="sxs-lookup"><span data-stu-id="0d268-140">Project files</span></span>

* <span data-ttu-id="0d268-141">下載[檔案](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip)專案所需。</span><span class="sxs-lookup"><span data-stu-id="0d268-141">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) required by the project.</span></span><span data-ttu-id="0d268-142"> 需要 Unity 2017.2 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="0d268-142"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="0d268-143">取消封存您的桌面或其他您輕鬆地連線到位置的檔案。</span><span class="sxs-lookup"><span data-stu-id="0d268-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="0d268-144">如果您想要查看原始程式碼，在下載之前，它有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze)。</span><span class="sxs-lookup"><span data-stu-id="0d268-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="0d268-145">偵錯 errata 和附註</span><span class="sxs-lookup"><span data-stu-id="0d268-145">Errata and Notes</span></span>

* <span data-ttu-id="0d268-146">在 Visual Studio 中，Just My Code 必須是停用 （未核取） 在 工具-> 選項-> 若要在程式碼中設定中斷點的偵錯。</span><span class="sxs-lookup"><span data-stu-id="0d268-146">In Visual Studio, "Just My Code" needs to be disabled (unchecked) under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="0d268-147">第 1 章-Unity 安裝</span><span class="sxs-lookup"><span data-stu-id="0d268-147">Chapter 1 - Unity Setup</span></span>

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a><span data-ttu-id="0d268-148">目標</span><span class="sxs-lookup"><span data-stu-id="0d268-148">Objectives</span></span>

* <span data-ttu-id="0d268-149">最佳化 HoloLens 開發 Unity。</span><span class="sxs-lookup"><span data-stu-id="0d268-149">Optimize Unity for HoloLens development.</span></span>
* <span data-ttu-id="0d268-150">匯入資產，並設定場景。</span><span class="sxs-lookup"><span data-stu-id="0d268-150">Import assets and setup the scene.</span></span>
* <span data-ttu-id="0d268-151">檢視太空人 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="0d268-151">View the astronaut in the HoloLens.</span></span>

### <a name="instructions"></a><span data-ttu-id="0d268-152">指示</span><span class="sxs-lookup"><span data-stu-id="0d268-152">Instructions</span></span>

1. <span data-ttu-id="0d268-153">啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="0d268-153">Start Unity.</span></span>
2. <span data-ttu-id="0d268-154">選取 **新的專案**。</span><span class="sxs-lookup"><span data-stu-id="0d268-154">Select **New Project**.</span></span>
3. <span data-ttu-id="0d268-155">將專案命名為**ModelExplorer**。</span><span class="sxs-lookup"><span data-stu-id="0d268-155">Name the project **ModelExplorer**.</span></span>
4. <span data-ttu-id="0d268-156">輸入與位置**視線**資料夾您先前未封存。</span><span class="sxs-lookup"><span data-stu-id="0d268-156">Enter location as the **Gaze** folder you previously un-archived.</span></span>
5. <span data-ttu-id="0d268-157">請確定專案已設定為**3D**。</span><span class="sxs-lookup"><span data-stu-id="0d268-157">Make sure the project is set to **3D**.</span></span>
6. <span data-ttu-id="0d268-158">按一下 **建立專案**。</span><span class="sxs-lookup"><span data-stu-id="0d268-158">Click **Create Project**.</span></span>

### <a name="unity-settings-for-hololens"></a><span data-ttu-id="0d268-159">HoloLens 的 unity 設定</span><span class="sxs-lookup"><span data-stu-id="0d268-159">Unity settings for HoloLens</span></span>

<span data-ttu-id="0d268-160">我們需要讓知道我們嘗試匯出的應用程式應該建立 Unity[沈浸式檢視](app-views.md)而不是 2D 檢視。</span><span class="sxs-lookup"><span data-stu-id="0d268-160">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="0d268-161">我們的做法是將做為虛擬實境裝置的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="0d268-161">We do that by adding HoloLens as a virtual reality device.</span></span>

1. <span data-ttu-id="0d268-162">移至**編輯 > 專案設定 > Player**。</span><span class="sxs-lookup"><span data-stu-id="0d268-162">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="0d268-163">在 [**偵測器] 面板**播放程式設定中，選取**Windows 市集**圖示。</span><span class="sxs-lookup"><span data-stu-id="0d268-163">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="0d268-164">依序展開**XR 設定**群組。</span><span class="sxs-lookup"><span data-stu-id="0d268-164">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="0d268-165">在 **轉譯**區段中，按一下**虛擬實境支援**核取方塊以加入新**虛擬實境 Sdk**清單。</span><span class="sxs-lookup"><span data-stu-id="0d268-165">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="0d268-166">確認**Windows Mixed Reality**出現在清單中。</span><span class="sxs-lookup"><span data-stu-id="0d268-166">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="0d268-167">如果沒有，請選取**+** 按鈕在清單底部，然後選擇**Windows 全像攝影版**。</span><span class="sxs-lookup"><span data-stu-id="0d268-167">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>

<span data-ttu-id="0d268-168">接下來，我們需要將我們指令碼的後端設定為.NET。</span><span class="sxs-lookup"><span data-stu-id="0d268-168">Next, we need to set our scripting backend to .NET.</span></span>

1. <span data-ttu-id="0d268-169">移至**編輯 > 專案設定 > Player** （您可能仍有這在上一個步驟）。</span><span class="sxs-lookup"><span data-stu-id="0d268-169">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="0d268-170">在 [**偵測器] 面板**播放程式設定中，選取**Windows 市集**圖示。</span><span class="sxs-lookup"><span data-stu-id="0d268-170">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="0d268-171">在 **其他設定**組態區段中，請確定**指令碼的後端**設定為 **.NET**</span><span class="sxs-lookup"><span data-stu-id="0d268-171">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="0d268-172">最後，我們會更新我們的品質設定，以達到 HoloLens 上快速的效能。</span><span class="sxs-lookup"><span data-stu-id="0d268-172">Finally, we'll update our quality settings to achieve a fast performance on HoloLens.</span></span>

1. <span data-ttu-id="0d268-173">移至**編輯 > 專案設定 > 品質**。</span><span class="sxs-lookup"><span data-stu-id="0d268-173">Go to **Edit > Project Settings > Quality**.</span></span>
2. <span data-ttu-id="0d268-174">按一下向下鍵在**預設**在 Windows 市集圖示的資料列。</span><span class="sxs-lookup"><span data-stu-id="0d268-174">Click on downward pointing arrow in the **Default** row under the Windows Store icon.</span></span>
3. <span data-ttu-id="0d268-175">選取 **最快**for **Windows 市集應用程式**。</span><span class="sxs-lookup"><span data-stu-id="0d268-175">Select **Fastest** for **Windows Store Apps**.</span></span>

### <a name="import-project-assets"></a><span data-ttu-id="0d268-176">匯入專案資產</span><span class="sxs-lookup"><span data-stu-id="0d268-176">Import project assets</span></span>

1. <span data-ttu-id="0d268-177">以滑鼠右鍵按一下**資產**中的資料夾**專案**面板。</span><span class="sxs-lookup"><span data-stu-id="0d268-177">Right click the **Assets** folder in the **Project** panel.</span></span>
2. <span data-ttu-id="0d268-178">按一下 **匯入封裝 > 自訂套件**。</span><span class="sxs-lookup"><span data-stu-id="0d268-178">Click on **Import Package > Custom Package**.</span></span>
3. <span data-ttu-id="0d268-179">瀏覽至您下載的專案檔案，然後按一下**ModelExplorer.unitypackage**。</span><span class="sxs-lookup"><span data-stu-id="0d268-179">Navigate to the project files you downloaded and click on **ModelExplorer.unitypackage**.</span></span>
4. <span data-ttu-id="0d268-180">按一下 [開啟] 。</span><span class="sxs-lookup"><span data-stu-id="0d268-180">Click **Open**.</span></span>
5. <span data-ttu-id="0d268-181">封裝載入之後，請按一下**匯入** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0d268-181">After the package loads, click on the **Import** button.</span></span>

### <a name="setup-the-scene"></a><span data-ttu-id="0d268-182">設定場景</span><span class="sxs-lookup"><span data-stu-id="0d268-182">Setup the scene</span></span>

1. <span data-ttu-id="0d268-183">在階層中，刪除**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="0d268-183">In the Hierarchy, delete the **Main Camera**.</span></span>
2. <span data-ttu-id="0d268-184">在  **HoloToolkit**資料夾中，開啟**輸入**資料夾，然後開啟**Prefabs**資料夾。</span><span class="sxs-lookup"><span data-stu-id="0d268-184">In the **HoloToolkit** folder, open the **Input** folder, then open the **Prefabs** folder.</span></span>
3. <span data-ttu-id="0d268-185">將拖放**MixedRealityCameraParent** prefab 來自**Prefabs**資料夾**階層**。</span><span class="sxs-lookup"><span data-stu-id="0d268-185">Drag and drop the **MixedRealityCameraParent** prefab from the **Prefabs** folder into the **Hierarchy**.</span></span>
4. <span data-ttu-id="0d268-186">以滑鼠右鍵按一下**定向光線**階層，然後選取**刪除**。</span><span class="sxs-lookup"><span data-stu-id="0d268-186">Right-click the **Directional Light** in the Hierarchy and select **Delete**.</span></span>
5. <span data-ttu-id="0d268-187">在 **全像投影**資料夾中，拖放的根目錄中的下列資產**階層**:</span><span class="sxs-lookup"><span data-stu-id="0d268-187">In the **Holograms** folder, drag and drop the following assets into the root of the **Hierarchy**:</span></span>
    * <span data-ttu-id="0d268-188">**AstroMan**</span><span class="sxs-lookup"><span data-stu-id="0d268-188">**AstroMan**</span></span>
    * <span data-ttu-id="0d268-189">**號誌**</span><span class="sxs-lookup"><span data-stu-id="0d268-189">**Lights**</span></span>
    * <span data-ttu-id="0d268-190">**SpaceAudioSource**</span><span class="sxs-lookup"><span data-stu-id="0d268-190">**SpaceAudioSource**</span></span>
    * <span data-ttu-id="0d268-191">**SpaceBackground**</span><span class="sxs-lookup"><span data-stu-id="0d268-191">**SpaceBackground**</span></span>
6. <span data-ttu-id="0d268-192">開始**播放模式**檢視太空人 ▶。</span><span class="sxs-lookup"><span data-stu-id="0d268-192">Start **Play Mode** ▶ to view the astronaut.</span></span>
7. <span data-ttu-id="0d268-193">按一下 **播放模式**▶ 一次，若要**停止**。</span><span class="sxs-lookup"><span data-stu-id="0d268-193">Click **Play Mode** ▶ again to **Stop**.</span></span>
8. <span data-ttu-id="0d268-194">在 **全像投影**資料夾中，尋找**Fitbox**資產並將它拖曳到的根目錄**階層**。</span><span class="sxs-lookup"><span data-stu-id="0d268-194">In the **Holograms** folder, find the **Fitbox** asset and drag it to the root of the **Hierarchy**.</span></span>
9. <span data-ttu-id="0d268-195">選取  **Fitbox**中**階層**面板。</span><span class="sxs-lookup"><span data-stu-id="0d268-195">Select the **Fitbox** in the **Hierarchy** panel.</span></span>
10. <span data-ttu-id="0d268-196">拖曳**AstroMan**從集合**階層**來**闀集合**屬性中 Fitbox **Inspector**面板。</span><span class="sxs-lookup"><span data-stu-id="0d268-196">Drag the **AstroMan** collection from the **Hierarchy** to the **Hologram Collection** property of the Fitbox in the **Inspector** panel.</span></span>

### <a name="save-the-project"></a><span data-ttu-id="0d268-197">儲存專案</span><span class="sxs-lookup"><span data-stu-id="0d268-197">Save the project</span></span>

1. <span data-ttu-id="0d268-198">儲存新的場景：**檔案 > 儲存為場景**。</span><span class="sxs-lookup"><span data-stu-id="0d268-198">Save the new scene: **File > Save Scene As**.</span></span>
2. <span data-ttu-id="0d268-199">按一下 **新的資料夾**並將資料夾命名**場景**。</span><span class="sxs-lookup"><span data-stu-id="0d268-199">Click **New Folder** and name the folder **Scenes**.</span></span>
3. <span data-ttu-id="0d268-200">將檔案命名為"**ModelExplorer**"並將它儲存在**場景**資料夾。</span><span class="sxs-lookup"><span data-stu-id="0d268-200">Name the file “**ModelExplorer**” and save it in the **Scenes** folder.</span></span>

### <a name="build-the-project"></a><span data-ttu-id="0d268-201">建置專案</span><span class="sxs-lookup"><span data-stu-id="0d268-201">Build the project</span></span>

1. <span data-ttu-id="0d268-202">在 Unity 中，選取**檔案 > 組建設定**。</span><span class="sxs-lookup"><span data-stu-id="0d268-202">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="0d268-203">按一下 **加入開啟的場景**加入場景。</span><span class="sxs-lookup"><span data-stu-id="0d268-203">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="0d268-204">選取 **通用 Windows 平台**中**平台**清單，然後按一下**切換平台**。</span><span class="sxs-lookup"><span data-stu-id="0d268-204">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="0d268-205">如果您要特別開發的 HoloLens，設定**目標裝置**要**HoloLens**。</span><span class="sxs-lookup"><span data-stu-id="0d268-205">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="0d268-206">否則，將它保留在**任何裝置**。</span><span class="sxs-lookup"><span data-stu-id="0d268-206">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="0d268-207">確保**建置型別**設為**D3D**並**SDK**設定為**最新安裝**（這應該可以 16299 或更新版本的 SDK）。</span><span class="sxs-lookup"><span data-stu-id="0d268-207">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="0d268-208">按一下 [建置] 。</span><span class="sxs-lookup"><span data-stu-id="0d268-208">Click **Build**.</span></span>
7. <span data-ttu-id="0d268-209">建立**新的資料夾**名為 「 應用程式 」。</span><span class="sxs-lookup"><span data-stu-id="0d268-209">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="0d268-210">只要按一下**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="0d268-210">Single click the **App** folder.</span></span>
9. <span data-ttu-id="0d268-211">按下**選取資料夾**。</span><span class="sxs-lookup"><span data-stu-id="0d268-211">Press **Select Folder**.</span></span>

<span data-ttu-id="0d268-212">Unity 完成時，會出現檔案總管 視窗。</span><span class="sxs-lookup"><span data-stu-id="0d268-212">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="0d268-213">開啟**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="0d268-213">Open the **App** folder.</span></span>
2. <span data-ttu-id="0d268-214">開啟**ModelExplorer Visual Studio 解決方案**。</span><span class="sxs-lookup"><span data-stu-id="0d268-214">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="0d268-215">如果將部署到 HoloLens:</span><span class="sxs-lookup"><span data-stu-id="0d268-215">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="0d268-216">使用頂端的工具列，在 Visual Studio 中，從 偵錯，若要變更目標**Release**進出至 ARM **x86**。</span><span class="sxs-lookup"><span data-stu-id="0d268-216">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="0d268-217">按一下下拉式清單 [本機電腦] 按鈕旁邊的箭號，然後選取**遠端機器**。</span><span class="sxs-lookup"><span data-stu-id="0d268-217">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="0d268-218">請輸入**HoloLens 裝置的 IP 位址**並將驗證模式設定為**通用 （未加密的通訊協定）**。</span><span class="sxs-lookup"><span data-stu-id="0d268-218">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="0d268-219">按一下 **選取**。</span><span class="sxs-lookup"><span data-stu-id="0d268-219">Click **Select**.</span></span> <span data-ttu-id="0d268-220">如果您不知道您的裝置 IP 位址，查看**設定 > 網路和網際網路 > 進階選項**。</span><span class="sxs-lookup"><span data-stu-id="0d268-220">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="0d268-221">在頂端功能表列中，按一下**偵錯]-> [啟動但不偵錯**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="0d268-221">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="0d268-222">如果這是第一次部署到您的裝置，您必須[與 Visual Studio 中配對](using-visual-studio.md#pairing-your-device-hololens)。</span><span class="sxs-lookup"><span data-stu-id="0d268-222">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="0d268-223">當應用程式部署時，關閉**Fitbox**具有**選取 軌跡**。</span><span class="sxs-lookup"><span data-stu-id="0d268-223">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="0d268-224">如果將部署到擬真耳機：</span><span class="sxs-lookup"><span data-stu-id="0d268-224">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="0d268-225">使用頂端的工具列，在 Visual Studio 中，從 偵錯，若要變更目標**Release**進出至 ARM **x64**。</span><span class="sxs-lookup"><span data-stu-id="0d268-225">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="0d268-226">請確定部署目標設定為**本機電腦**。</span><span class="sxs-lookup"><span data-stu-id="0d268-226">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="0d268-227">在頂端功能表列中，按一下**偵錯]-> [啟動但不偵錯**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="0d268-227">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="0d268-228">當應用程式部署時，關閉**Fitbox**所提取的動作控制站上的觸發程序。</span><span class="sxs-lookup"><span data-stu-id="0d268-228">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

## <a name="chapter-2---cursor-and-target-feedback"></a><span data-ttu-id="0d268-229">第 2 章-資料指標和目標的意見反應</span><span class="sxs-lookup"><span data-stu-id="0d268-229">Chapter 2 - Cursor and target feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a><span data-ttu-id="0d268-230">目標</span><span class="sxs-lookup"><span data-stu-id="0d268-230">Objectives</span></span>

* <span data-ttu-id="0d268-231">資料指標的視覺化設計和行為。</span><span class="sxs-lookup"><span data-stu-id="0d268-231">Cursor visual design and behavior.</span></span>
* <span data-ttu-id="0d268-232">視線為基礎的資料指標的意見反應。</span><span class="sxs-lookup"><span data-stu-id="0d268-232">Gaze-based cursor feedback.</span></span>
* <span data-ttu-id="0d268-233">視線型全像意見反應。</span><span class="sxs-lookup"><span data-stu-id="0d268-233">Gaze-based hologram feedback.</span></span>

<span data-ttu-id="0d268-234">我們將努力根據部分的資料指標設計原則，也就是：</span><span class="sxs-lookup"><span data-stu-id="0d268-234">We're going to base our work on some cursor design principles, namely:</span></span>

* <span data-ttu-id="0d268-235">資料指標一律會出現。</span><span class="sxs-lookup"><span data-stu-id="0d268-235">The cursor is always present.</span></span>
* <span data-ttu-id="0d268-236">不要讓取得太小或最大的資料指標。</span><span class="sxs-lookup"><span data-stu-id="0d268-236">Don't let the cursor get too small or big.</span></span>
* <span data-ttu-id="0d268-237">避免阻礙內容。</span><span class="sxs-lookup"><span data-stu-id="0d268-237">Avoid obstructing content.</span></span>

### <a name="instructions"></a><span data-ttu-id="0d268-238">指示</span><span class="sxs-lookup"><span data-stu-id="0d268-238">Instructions</span></span>

1. <span data-ttu-id="0d268-239">在  **HoloToolkit\Input\Prefabs**資料夾中，尋找**InputManager**資產。</span><span class="sxs-lookup"><span data-stu-id="0d268-239">In the **HoloToolkit\Input\Prefabs** folder, find the **InputManager** asset.</span></span>
2. <span data-ttu-id="0d268-240">將拖放**InputManager**拖曳至**階層**。</span><span class="sxs-lookup"><span data-stu-id="0d268-240">Drag and drop the **InputManager** onto the **Hierarchy**.</span></span>
3. <span data-ttu-id="0d268-241">在  **HoloToolkit\Input\Prefabs**資料夾中，尋找**游標**資產。</span><span class="sxs-lookup"><span data-stu-id="0d268-241">In the **HoloToolkit\Input\Prefabs** folder, find the **Cursor** asset.</span></span>
4. <span data-ttu-id="0d268-242">將拖放**游標**拖曳至**階層**。</span><span class="sxs-lookup"><span data-stu-id="0d268-242">Drag and drop the **Cursor** onto the **Hierarchy**.</span></span>
5. <span data-ttu-id="0d268-243">選取  **InputManager**物件中**階層**。</span><span class="sxs-lookup"><span data-stu-id="0d268-243">Select the **InputManager** object in the **Hierarchy**.</span></span>
6. <span data-ttu-id="0d268-244">拖曳**游標**物件**階層**到 InputManager **SimpleSinglePointerSelector**的**游標**欄位中，在底部**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="0d268-244">Drag the **Cursor** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>

![簡單的單一指標選取器設定](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a><span data-ttu-id="0d268-246">建置和部署</span><span class="sxs-lookup"><span data-stu-id="0d268-246">Build and Deploy</span></span>

1. <span data-ttu-id="0d268-247">重建的應用程式**檔案 > 組建設定**。</span><span class="sxs-lookup"><span data-stu-id="0d268-247">Rebuild the app from **File > Build Settings**.</span></span>
2. <span data-ttu-id="0d268-248">開啟**應用程式資料夾**。</span><span class="sxs-lookup"><span data-stu-id="0d268-248">Open the **App folder**.</span></span>
3. <span data-ttu-id="0d268-249">開啟**ModelExplorer Visual Studio 解決方案**。</span><span class="sxs-lookup"><span data-stu-id="0d268-249">Open the **ModelExplorer Visual Studio Solution**.</span></span>
4. <span data-ttu-id="0d268-250">按一下 **偵錯-> 啟動但不偵錯**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="0d268-250">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
5. <span data-ttu-id="0d268-251">觀察資料指標的繪製方式及其如何變更外觀如果雷射筆碰觸。</span><span class="sxs-lookup"><span data-stu-id="0d268-251">Observe how the cursor is drawn, and how it changes appearance if it is touching a hologram.</span></span>

### <a name="instructions"></a><span data-ttu-id="0d268-252">指示</span><span class="sxs-lookup"><span data-stu-id="0d268-252">Instructions</span></span>

1. <span data-ttu-id="0d268-253">在 [**階層**] 面板中，展開**AstroMan**->**GEO_G**->**Back_Center**物件。</span><span class="sxs-lookup"><span data-stu-id="0d268-253">In the **Hierarchy** panel, expand the **AstroMan**->**GEO_G**->**Back_Center** object.</span></span>
2. <span data-ttu-id="0d268-254">按兩下**Interactible.cs**在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="0d268-254">Double click on **Interactible.cs** to open it in Visual Studio.</span></span>
3. <span data-ttu-id="0d268-255">中的行取消註解**IFocusable.OnFocusEnter()** 並**IFocusable.OnFocusExit()** 中的回呼**Interactible.cs**。</span><span class="sxs-lookup"><span data-stu-id="0d268-255">Uncomment the lines in the **IFocusable.OnFocusEnter()** and **IFocusable.OnFocusExit()** callbacks in **Interactible.cs**.</span></span> <span data-ttu-id="0d268-256">（或視線控制器指） 焦點進入和離開特定的 GameObject collider 時，這些是由混合實境工具組的 InputManager 進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="0d268-256">These are called by the Mixed Reality Toolkit's InputManager when focus (either by gaze or by controller pointing) enters and exits the specific GameObject's collider.</span></span>

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
><span data-ttu-id="0d268-257">我們會使用`EnableKeyword`和`DisableKeyword`上方。</span><span class="sxs-lookup"><span data-stu-id="0d268-257">We use `EnableKeyword` and `DisableKeyword` above.</span></span> <span data-ttu-id="0d268-258">為了讓使用您自己的應用程式與工具組的標準著色器中，您必須遵循[Unity 指導方針，以存取透過指令碼的教材](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html)。</span><span class="sxs-lookup"><span data-stu-id="0d268-258">In order to make use of these in your own app with the Toolkit's Standard shader, you'll need to follow the [Unity guidelines for accessing materials via script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span></span> <span data-ttu-id="0d268-259">在此情況下，我們已加入[反白顯示資料的三種變化](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials)需要 （尋找反白顯示的名稱中使用的三個資料） 中的 [資源] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="0d268-259">In this case, we've already included the [three variants of highlighted material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) needed in the Resources folder (look for the three materials with highlight in the name).</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="0d268-260">建置和部署</span><span class="sxs-lookup"><span data-stu-id="0d268-260">Build and Deploy</span></span>

1. <span data-ttu-id="0d268-261">同樣地，建置專案，並將部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="0d268-261">As before, build the project and deploy to the HoloLens.</span></span>
2. <span data-ttu-id="0d268-262">觀察視線旨在物件時，會發生什麼事並不是。</span><span class="sxs-lookup"><span data-stu-id="0d268-262">Observe what happens when the gaze is aimed at an object and when it's not.</span></span>

## <a name="chapter-3---targeting-techniques"></a><span data-ttu-id="0d268-263">第 3 章-為目標的技術</span><span class="sxs-lookup"><span data-stu-id="0d268-263">Chapter 3 - Targeting Techniques</span></span>

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a><span data-ttu-id="0d268-264">目標</span><span class="sxs-lookup"><span data-stu-id="0d268-264">Objectives</span></span>

* <span data-ttu-id="0d268-265">讓您更輕鬆地目標全像投影。</span><span class="sxs-lookup"><span data-stu-id="0d268-265">Make it easier to target holograms.</span></span>
* <span data-ttu-id="0d268-266">穩固自然前端的移動。</span><span class="sxs-lookup"><span data-stu-id="0d268-266">Stabilize natural head movements.</span></span>

### <a name="instructions"></a><span data-ttu-id="0d268-267">指示</span><span class="sxs-lookup"><span data-stu-id="0d268-267">Instructions</span></span>

1. <span data-ttu-id="0d268-268">在 **階層**面板中，選取**InputManager**物件。</span><span class="sxs-lookup"><span data-stu-id="0d268-268">In the **Hierarchy** panel, select the **InputManager** object.</span></span>
2. <span data-ttu-id="0d268-269">在 [ **Inspector** ] 面板中，尋找**視線對**指令碼。</span><span class="sxs-lookup"><span data-stu-id="0d268-269">In the **Inspector** panel, find the **Gaze Stabilizer** script.</span></span> <span data-ttu-id="0d268-270">如果您想要看，請按一下以在 Visual Studio 中開啟。</span><span class="sxs-lookup"><span data-stu-id="0d268-270">Click it to open in Visual Studio, if you want to take a look.</span></span>
    * <span data-ttu-id="0d268-271">此指令碼會逐一查看 Raycast 資料的範例，並協助穩定的有效位數為目標的使用者的視線。</span><span class="sxs-lookup"><span data-stu-id="0d268-271">This script iterates over samples of Raycast data and helps stabilize the user's gaze for precision targeting.</span></span>
3. <span data-ttu-id="0d268-272">在  **Inspector**，您可以編輯**儲存穩定性範例**值。</span><span class="sxs-lookup"><span data-stu-id="0d268-272">In the **Inspector**, you can edit the **Stored Stability Samples** value.</span></span> <span data-ttu-id="0d268-273">這個值表示對會逐一查看直到計算穩定的值的樣本數目。</span><span class="sxs-lookup"><span data-stu-id="0d268-273">This value represents the number of samples that the stabilizer iterates on to calculate the stabilized value.</span></span>

## <a name="chapter-4---directional-indicator"></a><span data-ttu-id="0d268-274">第 4 章-方向性指標</span><span class="sxs-lookup"><span data-stu-id="0d268-274">Chapter 4 - Directional indicator</span></span>

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a><span data-ttu-id="0d268-275">目標</span><span class="sxs-lookup"><span data-stu-id="0d268-275">Objectives</span></span>

* <span data-ttu-id="0d268-276">新增資料指標以協助找出全像投影的方向性指標。</span><span class="sxs-lookup"><span data-stu-id="0d268-276">Add a directional indicator on the cursor to help find holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="0d268-277">指示</span><span class="sxs-lookup"><span data-stu-id="0d268-277">Instructions</span></span>

<span data-ttu-id="0d268-278">我們將使用**DirectionIndicator.cs**檔案將會：</span><span class="sxs-lookup"><span data-stu-id="0d268-278">We're going to use the **DirectionIndicator.cs** file which will:</span></span>

1. <span data-ttu-id="0d268-279">如果使用者不會 gazing 在全像投影的情況下顯示方向性指標。</span><span class="sxs-lookup"><span data-stu-id="0d268-279">Show the directional indicator if the user is not gazing at the holograms.</span></span>
2. <span data-ttu-id="0d268-280">如果使用者 gazing 在全像投影，請隱藏方向性指標。</span><span class="sxs-lookup"><span data-stu-id="0d268-280">Hide the directional indicator if the user is gazing at the holograms.</span></span>
3. <span data-ttu-id="0d268-281">更新為指向全像投影的方向性指標。</span><span class="sxs-lookup"><span data-stu-id="0d268-281">Update the directional indicator to point to the holograms.</span></span>

<span data-ttu-id="0d268-282">那就開始吧。</span><span class="sxs-lookup"><span data-stu-id="0d268-282">Let's get started.</span></span>

1. <span data-ttu-id="0d268-283">按一下**AstroMan**物件中**階層**面板並**按一下箭號**加以展開。</span><span class="sxs-lookup"><span data-stu-id="0d268-283">Click on the **AstroMan** object in the **Hierarchy** panel and **click the arrow** to expand it.</span></span>
2. <span data-ttu-id="0d268-284">在 **階層**面板中，選取**DirectionalIndicator**物件下**AstroMan**。</span><span class="sxs-lookup"><span data-stu-id="0d268-284">In the **Hierarchy** panel, select the **DirectionalIndicator** object under **AstroMan**.</span></span>
3. <span data-ttu-id="0d268-285">在  **Inspector**  面板中，按一下**新增元件** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0d268-285">In the **Inspector** panel, click the **Add Component** button.</span></span>
4. <span data-ttu-id="0d268-286">在功能表中，輸入在搜尋方塊**方向指標**。</span><span class="sxs-lookup"><span data-stu-id="0d268-286">In the menu, type in the search box **Direction Indicator**.</span></span> <span data-ttu-id="0d268-287">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="0d268-287">Select the search result.</span></span>
5. <span data-ttu-id="0d268-288">中**階層** 面板、 拖曳和卸除**游標**物件拖曳至**游標**中的屬性**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="0d268-288">In the **Hierarchy** panel, drag and drop the **Cursor** object onto the **Cursor** property in the **Inspector**.</span></span>
6. <span data-ttu-id="0d268-289">在 [**專案**] 面板的**全像投影**資料夾、 拖放**DirectionalIndicator**拖曳至資產**方向性指標**中的屬性**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="0d268-289">In the **Project** panel, in the **Holograms** folder, drag and drop the **DirectionalIndicator** asset onto the **Directional Indicator** property in the **Inspector**.</span></span>
7. <span data-ttu-id="0d268-290">建置及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="0d268-290">Build and deploy the app.</span></span>
8. <span data-ttu-id="0d268-291">觀看方向性指標物件如何協助您找出太空人。</span><span class="sxs-lookup"><span data-stu-id="0d268-291">Watch how the directional indicator object helps you find the astronaut.</span></span>

## <a name="chapter-5---billboarding"></a><span data-ttu-id="0d268-292">第 5 章-告示板</span><span class="sxs-lookup"><span data-stu-id="0d268-292">Chapter 5 - Billboarding</span></span>

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a><span data-ttu-id="0d268-293">目標</span><span class="sxs-lookup"><span data-stu-id="0d268-293">Objectives</span></span>

* <span data-ttu-id="0d268-294">使用告示板，讓全像投影一律面臨朝向您。</span><span class="sxs-lookup"><span data-stu-id="0d268-294">Use billboarding to have holograms always face towards you.</span></span>

<span data-ttu-id="0d268-295">我們將使用**Billboard.cs**檔案以保留導向，使其面向使用者隨時 GameObject。</span><span class="sxs-lookup"><span data-stu-id="0d268-295">We will be using the **Billboard.cs** file to keep a GameObject oriented such that it is facing the user at all times.</span></span>

1. <span data-ttu-id="0d268-296">在 **階層**面板中，選取**AstroMan**物件。</span><span class="sxs-lookup"><span data-stu-id="0d268-296">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
2. <span data-ttu-id="0d268-297">在  **Inspector**  面板中，按一下**新增元件** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0d268-297">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="0d268-298">在功能表中，輸入在搜尋方塊**告示板**。</span><span class="sxs-lookup"><span data-stu-id="0d268-298">In the menu, type in the search box **Billboard**.</span></span> <span data-ttu-id="0d268-299">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="0d268-299">Select the search result.</span></span>
4. <span data-ttu-id="0d268-300">在  **Inspector**設定**Pivot Axis**來**Y**。</span><span class="sxs-lookup"><span data-stu-id="0d268-300">In the **Inspector** set the **Pivot Axis** to **Y**.</span></span>
5. <span data-ttu-id="0d268-301">試試看！</span><span class="sxs-lookup"><span data-stu-id="0d268-301">Try it!</span></span> <span data-ttu-id="0d268-302">建置並部署為應用程式之前。</span><span class="sxs-lookup"><span data-stu-id="0d268-302">Build and deploy the app as before.</span></span>
6. <span data-ttu-id="0d268-303">請參閱如何告示板物件也會等您不論您如何變更觀點來看。</span><span class="sxs-lookup"><span data-stu-id="0d268-303">See how the Billboard object faces you no matter how you change the viewpoint.</span></span>
7. <span data-ttu-id="0d268-304">刪除從指令碼**AstroMan**現在。</span><span class="sxs-lookup"><span data-stu-id="0d268-304">Delete the script from the **AstroMan** for now.</span></span>

## <a name="chapter-6---tag-along"></a><span data-ttu-id="0d268-305">第 6 章-Tag-Along</span><span class="sxs-lookup"><span data-stu-id="0d268-305">Chapter 6 - Tag-Along</span></span>

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a><span data-ttu-id="0d268-306">目標</span><span class="sxs-lookup"><span data-stu-id="0d268-306">Objectives</span></span>

* <span data-ttu-id="0d268-307">您可以使用 Tag-Along，讓我們全像投影房間周圍關注我們。</span><span class="sxs-lookup"><span data-stu-id="0d268-307">Use Tag-Along to have our holograms follow us around the room.</span></span>

<span data-ttu-id="0d268-308">當我們處理此問題，我們將會引導您藉由下列的設計限制：</span><span class="sxs-lookup"><span data-stu-id="0d268-308">As we work on this issue, we'll be guided by the following design constraints:</span></span>

* <span data-ttu-id="0d268-309">內容應該總是一目瞭然消失。</span><span class="sxs-lookup"><span data-stu-id="0d268-309">Content should always be a glance away.</span></span>
* <span data-ttu-id="0d268-310">內容不應方式。</span><span class="sxs-lookup"><span data-stu-id="0d268-310">Content should not be in the way.</span></span>
* <span data-ttu-id="0d268-311">Head 鎖定的內容時感到不舒服。</span><span class="sxs-lookup"><span data-stu-id="0d268-311">Head-locking content is uncomfortable.</span></span>

<span data-ttu-id="0d268-312">這裡使用的解決方案是使用 「 tag-along"的方法。</span><span class="sxs-lookup"><span data-stu-id="0d268-312">The solution used here is to use a "tag-along" approach.</span></span>

<span data-ttu-id="0d268-313">Tag-along 物件永遠不會完整保留使用者的檢視。</span><span class="sxs-lookup"><span data-stu-id="0d268-313">A tag-along object never fully leaves the user's view.</span></span> <span data-ttu-id="0d268-314">您可以將 tag-along 視為物件附加至使用者的大腦拖放群組列。</span><span class="sxs-lookup"><span data-stu-id="0d268-314">You can think of the a tag-along as being an object attached to the user's head by rubber bands.</span></span> <span data-ttu-id="0d268-315">當使用者移動，內容會維持內輕鬆瀏覽，而不需要完全離開滑動朝向檢視的邊緣。</span><span class="sxs-lookup"><span data-stu-id="0d268-315">As the user moves, the content will stay within an easy glance by sliding towards the edge of the view without completely leaving.</span></span> <span data-ttu-id="0d268-316">當使用者 gazes 朝向 tag-along 物件時，它進入更完整檢視。</span><span class="sxs-lookup"><span data-stu-id="0d268-316">When the user gazes towards the tag-along object, it comes more fully into view.</span></span>

<span data-ttu-id="0d268-317">我們將使用**SimpleTagalong.cs**檔案將會：</span><span class="sxs-lookup"><span data-stu-id="0d268-317">We're going to use the **SimpleTagalong.cs** file which will:</span></span>

1. <span data-ttu-id="0d268-318">判斷 Tag-Along 物件是否相機的範圍內。</span><span class="sxs-lookup"><span data-stu-id="0d268-318">Determine if the Tag-Along object is within the camera bounds.</span></span>
2. <span data-ttu-id="0d268-319">如果沒有檢視範圍內的位置來 Tag-Along，部分在檢視範圍內。</span><span class="sxs-lookup"><span data-stu-id="0d268-319">If not within the view frustum, position the Tag-Along to partially within the view frustum.</span></span>
3. <span data-ttu-id="0d268-320">從使用者的預設距離，否則為位置 Tag-Along。</span><span class="sxs-lookup"><span data-stu-id="0d268-320">Otherwise, position the Tag-Along to a default distance from the user.</span></span>

<span data-ttu-id="0d268-321">若要這樣做，我們首先必須變更**Interactible.cs**指令碼來呼叫**TagalongAction**。</span><span class="sxs-lookup"><span data-stu-id="0d268-321">To do this, we first must change the **Interactible.cs** script to call the **TagalongAction**.</span></span>

1. <span data-ttu-id="0d268-322">編輯**Interactible.cs**完成程式碼撰寫練習 6.a （取消註解線條 84 到 87）。</span><span class="sxs-lookup"><span data-stu-id="0d268-322">Edit **Interactible.cs** by completing coding exercise 6.a (uncommenting lines 84 to 87).</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

<span data-ttu-id="0d268-323">**InteractibleAction.cs**指令碼，搭配**Interactible.cs**執行自訂動作，當您點選 全像投影。</span><span class="sxs-lookup"><span data-stu-id="0d268-323">The **InteractibleAction.cs** script, paired with **Interactible.cs** performs custom actions when you tap on holograms.</span></span> <span data-ttu-id="0d268-324">在此情況下，我們將使用其中一個專為 tag-along。</span><span class="sxs-lookup"><span data-stu-id="0d268-324">In this case, we'll use one specifically for tag-along.</span></span>

* <span data-ttu-id="0d268-325">在 **指令碼**資料夾中的，按一下  **TagalongAction.cs**資產在 Visual Studio 中開啟。</span><span class="sxs-lookup"><span data-stu-id="0d268-325">In the **Scripts** folder click on **TagalongAction.cs** asset to open in Visual Studio.</span></span>
* <span data-ttu-id="0d268-326">完成程式碼撰寫練習，或將其變更如下：</span><span class="sxs-lookup"><span data-stu-id="0d268-326">Complete the coding exercise or change it to this:</span></span>
  * <span data-ttu-id="0d268-327">在頂端**階層**，在搜尋列中輸入**ChestButton_Center**和選取的結果。</span><span class="sxs-lookup"><span data-stu-id="0d268-327">At the top of the **Hierarchy**, in the search bar type **ChestButton_Center** and select the result.</span></span>
  * <span data-ttu-id="0d268-328">在  **Inspector**  面板中，按一下**新增元件** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0d268-328">In the **Inspector** panel, click the **Add Component** button.</span></span>
  * <span data-ttu-id="0d268-329">在功能表中，輸入在搜尋方塊**Tagalong 動作**。</span><span class="sxs-lookup"><span data-stu-id="0d268-329">In the menu, type in the search box **Tagalong Action**.</span></span> <span data-ttu-id="0d268-330">選取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="0d268-330">Select the search result.</span></span>
  * <span data-ttu-id="0d268-331">在 [**全像投影**] 資料夾尋找**Tagalong**資產。</span><span class="sxs-lookup"><span data-stu-id="0d268-331">In **Holograms** folder find the **Tagalong** asset.</span></span>
  * <span data-ttu-id="0d268-332">選取  **ChestButton_Center**物件中**階層**。</span><span class="sxs-lookup"><span data-stu-id="0d268-332">Select the **ChestButton_Center** object in the **Hierarchy**.</span></span> <span data-ttu-id="0d268-333">將拖放**TagAlong**物件**專案**面板拖曳至**Inspector**成**物件至 Tagalong**屬性。</span><span class="sxs-lookup"><span data-stu-id="0d268-333">Drag and drop the **TagAlong** object from the **Project** panel onto the **Inspector** into the **Object To Tagalong** property.</span></span>
  * <span data-ttu-id="0d268-334">拖曳**Tagalong 動作**物件**Inspector**成**Interactible 動作**欄位**Interactible**指令碼。</span><span class="sxs-lookup"><span data-stu-id="0d268-334">Drag the **Tagalong Action** object from the **Inspector** into the **Interactible Action** field on the **Interactible** script.</span></span>
* <span data-ttu-id="0d268-335">按兩下**TagalongAction**指令碼，以在 Visual Studio 中開啟它。</span><span class="sxs-lookup"><span data-stu-id="0d268-335">Double click the **TagalongAction** script to open it in Visual Studio.</span></span>

![Interactible 設定](images/holograms210-interactible.png)

<span data-ttu-id="0d268-337">我們需要加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="0d268-337">We need to add the following:</span></span>

* <span data-ttu-id="0d268-338">將功能加入 PerformAction 函式 （繼承自 InteractibleAction） TagalongAction 指令碼中。</span><span class="sxs-lookup"><span data-stu-id="0d268-338">Add functionality to the PerformAction function in the TagalongAction script (inherited from InteractibleAction).</span></span>
* <span data-ttu-id="0d268-339">告示板 gazed 基礎物件，加上 pivot axis 設 XY 散佈圖。</span><span class="sxs-lookup"><span data-stu-id="0d268-339">Add billboarding to the gazed-upon object, and set the pivot axis to XY.</span></span>
* <span data-ttu-id="0d268-340">然後新增至物件的簡單 Tag-Along。</span><span class="sxs-lookup"><span data-stu-id="0d268-340">Then add simple Tag-Along to the object.</span></span>

<span data-ttu-id="0d268-341">以下是我們的解決方案，從**TagalongAction.cs**:</span><span class="sxs-lookup"><span data-stu-id="0d268-341">Here's our solution, from **TagalongAction.cs**:</span></span>

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

* <span data-ttu-id="0d268-342">試試看！</span><span class="sxs-lookup"><span data-stu-id="0d268-342">Try it!</span></span> <span data-ttu-id="0d268-343">建置及部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="0d268-343">Build and deploy the app.</span></span>
* <span data-ttu-id="0d268-344">觀看如何的內容會遵循中心的視線點，但不是持續，而不會封鎖它。</span><span class="sxs-lookup"><span data-stu-id="0d268-344">Watch how the content follows the center of the gaze point, but not continuously and without blocking it.</span></span>
