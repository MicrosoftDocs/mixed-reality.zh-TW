---
title: MR 基本概念 100-開始使用 Unity
description: 了解如何建立第一個基本的混合的實境"hello world"應用程式。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: 混合實境，Windows Mixed Reality、 HoloLens、 沉浸式 vr mr、 開始著手，全像圖、 academy、 教學課程
ms.openlocfilehash: fd3bed955e80ec18b7be500adbdb0fcb7062d129
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993615"
---
>[!NOTE]
><span data-ttu-id="40ee5-104">混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。</span><span class="sxs-lookup"><span data-stu-id="40ee5-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="40ee5-105">因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。</span><span class="sxs-lookup"><span data-stu-id="40ee5-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="40ee5-106">這些教學課程會**_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="40ee5-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="40ee5-107">它們會繼續運作，支援的裝置上維護。</span><span class="sxs-lookup"><span data-stu-id="40ee5-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="40ee5-108">會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="40ee5-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="40ee5-109">當他們回傳時，本聲明將會更新這些教學課程的連結。</span><span class="sxs-lookup"><span data-stu-id="40ee5-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-100-getting-started-with-unity"></a><span data-ttu-id="40ee5-110">MR 基本概念 100:開始使用 Unity</span><span class="sxs-lookup"><span data-stu-id="40ee5-110">MR Basics 100: Getting started with Unity</span></span>

<span data-ttu-id="40ee5-111">本教學課程將逐步引導您建立使用 Unity 建置基本的混合的實境應用程式。</span><span class="sxs-lookup"><span data-stu-id="40ee5-111">This tutorial will walk you through creating a basic mixed reality app built with Unity.</span></span>

## <a name="device-support"></a><span data-ttu-id="40ee5-112">裝置支援</span><span class="sxs-lookup"><span data-stu-id="40ee5-112">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="40ee5-113">課程</span><span class="sxs-lookup"><span data-stu-id="40ee5-113">Course</span></span></th><th style="width:150px"> <span data-ttu-id="40ee5-114"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="40ee5-114"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="40ee5-115"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="40ee5-115"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="40ee5-116">MR 基本概念 100:開始使用 Unity</span><span class="sxs-lookup"><span data-stu-id="40ee5-116">MR Basics 100: Getting started with Unity</span></span></td><td style="text-align: center;"> <span data-ttu-id="40ee5-117">✔️</span><span class="sxs-lookup"><span data-stu-id="40ee5-117">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="40ee5-118">✔️</span><span class="sxs-lookup"><span data-stu-id="40ee5-118">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="40ee5-119">先決條件</span><span class="sxs-lookup"><span data-stu-id="40ee5-119">Prerequisites</span></span>

* <span data-ttu-id="40ee5-120">Windows 10 電腦的正確設定[安裝工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="40ee5-120">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

## <a name="chapter-1---create-a-new-project"></a><span data-ttu-id="40ee5-121">第 1-建立新的專案</span><span class="sxs-lookup"><span data-stu-id="40ee5-121">Chapter 1 - Create a New Project</span></span>

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

<span data-ttu-id="40ee5-122">若要建置使用 Unity 應用程式，必須先建立專案。</span><span class="sxs-lookup"><span data-stu-id="40ee5-122">To build an app with Unity, you first need to create a project.</span></span> <span data-ttu-id="40ee5-123">此專案會組織成幾個資料夾，其中最重要的是您資產的資料夾。</span><span class="sxs-lookup"><span data-stu-id="40ee5-123">This project is organized into a few folders, the most important of which is your Assets folder.</span></span> <span data-ttu-id="40ee5-124">這是保存您從數位內容創作工具，例如 Maya、 最大杜比劇院效果 4d 或您使用 Visual Studio 或您慣用的程式碼編輯器，建立的所有程式碼的 Photoshop 匯入的所有資產的資料夾和任意數目的內容檔案，Unity 會建立為您撰寫場景動畫和其他編輯器中的 Unity 資產類型。</span><span class="sxs-lookup"><span data-stu-id="40ee5-124">This is the folder that holds all assets you import from digital content creation tools such as Maya, Max Cinema 4D or Photoshop, all code you create with Visual Studio or your favorite code editor, and any number of content files that Unity creates as you compose scenes, animations and other Unity asset types in the editor.</span></span>

<span data-ttu-id="40ee5-125">若要建置及部署 UWP 應用程式，Unity 可以匯出為 Visual Studio 方案將會包含所有必要的資產和程式碼檔案的專案。</span><span class="sxs-lookup"><span data-stu-id="40ee5-125">To build and deploy UWP apps, Unity can export the project as a Visual Studio solution that will contain all necessary asset and code files.</span></span>

1. <span data-ttu-id="40ee5-126">啟動 Unity</span><span class="sxs-lookup"><span data-stu-id="40ee5-126">Start Unity</span></span>
2. <span data-ttu-id="40ee5-127">選取**新**</span><span class="sxs-lookup"><span data-stu-id="40ee5-127">Select **New**</span></span>
3. <span data-ttu-id="40ee5-128">輸入專案名稱 （例如：「 MixedRealityIntroduction")</span><span class="sxs-lookup"><span data-stu-id="40ee5-128">Enter a project name (e.g. "MixedRealityIntroduction")</span></span>
4. <span data-ttu-id="40ee5-129">輸入要儲存專案的位置</span><span class="sxs-lookup"><span data-stu-id="40ee5-129">Enter a location to save your project</span></span>
5. <span data-ttu-id="40ee5-130">請確定**3D**切換已選取</span><span class="sxs-lookup"><span data-stu-id="40ee5-130">Ensure the **3D** toggle is selected</span></span>
6. <span data-ttu-id="40ee5-131">選取**建立專案**</span><span class="sxs-lookup"><span data-stu-id="40ee5-131">Select **Create project**</span></span>

<span data-ttu-id="40ee5-132">恭喜，您會以您的混合的實境自訂立即開始的所有安裝程式。</span><span class="sxs-lookup"><span data-stu-id="40ee5-132">Congrats, you are all setup to get started with your mixed reality customizations now.</span></span>

## <a name="chapter-2---setup-the-camera"></a><span data-ttu-id="40ee5-133">第 2 章-安裝相機</span><span class="sxs-lookup"><span data-stu-id="40ee5-133">Chapter 2 - Setup the Camera</span></span>

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

<span data-ttu-id="40ee5-134">Unity Main Camera 處理追蹤的前端和立體視覺呈現。</span><span class="sxs-lookup"><span data-stu-id="40ee5-134">The Unity Main Camera handles head tracking and stereoscopic rendering.</span></span> <span data-ttu-id="40ee5-135">有一些變更，可讓 Main Camera 與混合實境中使用它。</span><span class="sxs-lookup"><span data-stu-id="40ee5-135">There are a few changes to make to the Main Camera to use it with mixed reality.</span></span>
1. <span data-ttu-id="40ee5-136">選取 檔案 > 新的場景</span><span class="sxs-lookup"><span data-stu-id="40ee5-136">Select File > New Scene</span></span>

<span data-ttu-id="40ee5-137">首先，能夠更輕鬆地配置您的應用程式，如果您能想像為使用者的開始位置 (**X**:0， **Y**:0， **Z**:0).</span><span class="sxs-lookup"><span data-stu-id="40ee5-137">First, it will be easier to lay out your app if you imagine the starting position of the user as (**X**: 0, **Y**: 0, **Z**: 0).</span></span> <span data-ttu-id="40ee5-138">由於 Main Camera 正在追蹤使用者的標頭的移動，就可以設定使用者的開始位置設定 Main Camera 的開始位置。</span><span class="sxs-lookup"><span data-stu-id="40ee5-138">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>
1. <span data-ttu-id="40ee5-139">選取  **Main Camera**中**階層**面板</span><span class="sxs-lookup"><span data-stu-id="40ee5-139">Select **Main Camera** in the **Hierarchy** panel</span></span>
2. <span data-ttu-id="40ee5-140">在 [ **Inspector** ] 面板中，尋找**轉換**元件，並變更**位置**從 (**X**:0， **Y**:1、&lt **Z**:-10) 到 (**X**:0， **Y**:0， **Z**:0)</span><span class="sxs-lookup"><span data-stu-id="40ee5-140">In the **Inspector** panel, find the **Transform** component and change the **Position** from (**X**: 0, **Y**: 1, **Z**: -10) to (**X**: 0, **Y**: 0, **Z**: 0)</span></span>

<span data-ttu-id="40ee5-141">第二的預設相機背景需要加以考量。</span><span class="sxs-lookup"><span data-stu-id="40ee5-141">Second, the default Camera background needs some thought.</span></span>

<span data-ttu-id="40ee5-142">**HoloLens 的應用程式**，現實世界裡應該會出現背後的所有項目觀景窗會呈現不天空盒材質。</span><span class="sxs-lookup"><span data-stu-id="40ee5-142">**For HoloLens applications**, the real world should appear behind everything the camera renders, not a Skybox texture.</span></span>
1. <span data-ttu-id="40ee5-143">與**Main Camera**中選取，您仍然**階層** 面板中，尋找**相機**元件**Inspector**面板，並變更**清除旗標**下拉式清單中，從**天空盒**來**單色**。</span><span class="sxs-lookup"><span data-stu-id="40ee5-143">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Clear Flags** dropdown from **Skybox** to **Solid Color**.</span></span>
2. <span data-ttu-id="40ee5-144">選取 **背景**色彩選擇器和變更**RGBA**值 （0，0，0，0）</span><span class="sxs-lookup"><span data-stu-id="40ee5-144">Select the **Background** color picker and change the **RGBA** values to (0, 0, 0, 0)</span></span>

<span data-ttu-id="40ee5-145">**混合的實境應用程式目標為沈浸式耳機**，我們可以使用 Unity 所提供的預設天空盒材質。</span><span class="sxs-lookup"><span data-stu-id="40ee5-145">**For mixed reality applications targeted to immersive headsets**, we can use the default Skybox texture that Unity provides.</span></span>
1. <span data-ttu-id="40ee5-146">與**Main Camera**中選取，您仍然**階層** 面板中，尋找**相機**元件**Inspector**面板，並保留**清除旗標**下拉式清單來**天空盒**。</span><span class="sxs-lookup"><span data-stu-id="40ee5-146">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Clear Flags** dropdown to **Skybox**.</span></span>

<span data-ttu-id="40ee5-147">第三，讓我們考慮接近裁剪平面 Unity 中的，並防止物件呈現太靠近使用者的眼睛使用者接近物件或物件方法的使用者。</span><span class="sxs-lookup"><span data-stu-id="40ee5-147">Third, let us consider the near clip plane in Unity and prevent objects from being rendered too close to the users eyes as a user approaches an object or an object approaches a user.</span></span>

<span data-ttu-id="40ee5-148">**HoloLens 的應用程式**，可以將設定為接近裁剪平面[HoloLens 建議](camera-in-unity.md#clip-planes)0.85 的計量。</span><span class="sxs-lookup"><span data-stu-id="40ee5-148">**For HoloLens applications**, the near clip plane can be set to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 meters.</span></span>
1. <span data-ttu-id="40ee5-149">與**Main Camera**中選取，您仍然**階層**] 面板中，尋找**相機**元件**Inspector**面板，並變更**接近裁剪平面**欄位從 [預設**0.3**來建議 HoloLens **0.85**。</span><span class="sxs-lookup"><span data-stu-id="40ee5-149">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Near Clip Plane** field from the default **0.3** to the HoloLens recommended **0.85**.</span></span>

<span data-ttu-id="40ee5-150">**混合的實境應用程式目標為沈浸式耳機**，我們可以使用 Unity 所提供的預設設定。</span><span class="sxs-lookup"><span data-stu-id="40ee5-150">**For mixed reality applications targeted to immersive headsets**, we can use the default setting that Unity provides.</span></span>
1. <span data-ttu-id="40ee5-151">與**Main Camera**中選取，您仍然**階層** 面板中，尋找**相機**元件**Inspector**面板，並保留**接近裁剪平面**欄位設為預設值**0.3**。</span><span class="sxs-lookup"><span data-stu-id="40ee5-151">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Near Clip Plane** field to the default **0.3**.</span></span>

<span data-ttu-id="40ee5-152">最後，讓我們儲存我們進行到目前為止。</span><span class="sxs-lookup"><span data-stu-id="40ee5-152">Finally, let us save our progress so far.</span></span> <span data-ttu-id="40ee5-153">若要儲存的場景變更，請選取**檔案 > 存場景**，場景命名為**Main**，然後選取**儲存**。</span><span class="sxs-lookup"><span data-stu-id="40ee5-153">To save the scene changes, select **File > Save Scene As**, name the scene **Main**, and select **Save**.</span></span>

## <a name="chapter-3---setup-the-project-settings"></a><span data-ttu-id="40ee5-154">第 3 章-安裝程式的專案設定</span><span class="sxs-lookup"><span data-stu-id="40ee5-154">Chapter 3 - Setup the Project Settings</span></span>

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

<span data-ttu-id="40ee5-155">在本章中，我們會設定一些幫助我們的 Unity 專案設定目標 Windows 全像攝影版 SDK 進行開發。</span><span class="sxs-lookup"><span data-stu-id="40ee5-155">In this chapter, we will set some Unity project settings that help us target the Windows Holographic SDK for development.</span></span> <span data-ttu-id="40ee5-156">我們也將我們的應用程式中設定某些品質設定。</span><span class="sxs-lookup"><span data-stu-id="40ee5-156">We will also set some quality settings for our application.</span></span> <span data-ttu-id="40ee5-157">最後，我們會確保我們建置目標會設定為 Windows 市集。</span><span class="sxs-lookup"><span data-stu-id="40ee5-157">Finally, we will ensure our build targets are set to Windows Store.</span></span>

### <a name="unity-performance-and-quality-settings"></a><span data-ttu-id="40ee5-158">Unity 的效能和品質的設定</span><span class="sxs-lookup"><span data-stu-id="40ee5-158">Unity performance and quality settings</span></span>

<span data-ttu-id="40ee5-159">**HoloLens 的 unity 品質設定**</span><span class="sxs-lookup"><span data-stu-id="40ee5-159">**Unity quality settings for HoloLens**</span></span>

![HoloLens 的 unity 品質設定](images/qualitysettings.png) 

<span data-ttu-id="40ee5-161">維護高的畫面播放速率 HoloLens 上是很重要，因為我們想要微調的最快效能的品質設定。</span><span class="sxs-lookup"><span data-stu-id="40ee5-161">Since maintaining high framerate on HoloLens is so important, we want the quality settings tuned for fastest performance.</span></span> <span data-ttu-id="40ee5-162">如需詳細效能資訊，請[Unity 的效能建議](performance-recommendations-for-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="40ee5-162">For more detailed performance information, [Performance recommendations for Unity](performance-recommendations-for-unity.md).</span></span>
1. <span data-ttu-id="40ee5-163">選取**編輯 > 專案設定 > 品質**</span><span class="sxs-lookup"><span data-stu-id="40ee5-163">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="40ee5-164">選取 **下拉式清單**下方**Windows 市集**標誌，然後選取**非常低**。</span><span class="sxs-lookup"><span data-stu-id="40ee5-164">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="40ee5-165">您知道設定正確時套用的 Windows 市集的資料行中的方塊並**非常低**資料列是綠色。</span><span class="sxs-lookup"><span data-stu-id="40ee5-165">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green.</span></span>

<span data-ttu-id="40ee5-166">**混合的實境應用程式，以阻擋顯示目標**，您可以將品質設定保留為其預設值。</span><span class="sxs-lookup"><span data-stu-id="40ee5-166">**For mixed reality applications targeted to occluded displays**, you can leave the quality settings to its default values.</span></span>

### <a name="target-windows-10-sdk"></a><span data-ttu-id="40ee5-167">目標 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="40ee5-167">Target Windows 10 SDK</span></span>

<span data-ttu-id="40ee5-168">**目標 Windows 全像攝影版 SDK**</span><span class="sxs-lookup"><span data-stu-id="40ee5-168">**Target Windows Holographic SDK**</span></span>

![目標 Windows 全像攝影版 SDK](images/xrsettings.png) 

<span data-ttu-id="40ee5-170">我們需要讓知道我們嘗試匯出的應用程式應該建立 Unity[沈浸式檢視](app-views.md)而不是 2D 檢視。</span><span class="sxs-lookup"><span data-stu-id="40ee5-170">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="40ee5-171">我們可以啟用在 Unity 上的虛擬實境支援 Windows 10 SDK 為目標。</span><span class="sxs-lookup"><span data-stu-id="40ee5-171">We do this by enabling Virtual Reality support on Unity targeting the Windows 10 SDK.</span></span>
1. <span data-ttu-id="40ee5-172">移至**編輯 > 專案設定 > Player**。</span><span class="sxs-lookup"><span data-stu-id="40ee5-172">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="40ee5-173">在 [**偵測器] 面板**播放程式設定中，選取**Windows 市集**圖示。</span><span class="sxs-lookup"><span data-stu-id="40ee5-173">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="40ee5-174">依序展開**XR 設定**群組。</span><span class="sxs-lookup"><span data-stu-id="40ee5-174">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="40ee5-175">在 **轉譯**區段中，按一下**虛擬實境支援**核取方塊以加入新**虛擬實境 Sdk**清單。</span><span class="sxs-lookup"><span data-stu-id="40ee5-175">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="40ee5-176">確認**Windows Mixed Reality**出現在清單中。</span><span class="sxs-lookup"><span data-stu-id="40ee5-176">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="40ee5-177">如果沒有，請選取**+** 按鈕在清單底部，然後選擇**Windows Mixed Reality**。</span><span class="sxs-lookup"><span data-stu-id="40ee5-177">If not, select the **+** button at the bottom of the list and choose **Windows Mixed Reality**.</span></span>

>[!NOTE]
><span data-ttu-id="40ee5-178">如果您看不見**Windows 市集**圖示，並再次檢查以確定您選取 Windows 市集.NET 指令碼後端之前安裝。</span><span class="sxs-lookup"><span data-stu-id="40ee5-178">If you do not see the **Windows Store** icon, double check to make sure you selected the Windows Store .NET Scripting Backend prior to installation.</span></span> <span data-ttu-id="40ee5-179">如果沒有，您可能需要重新安裝正確的 Windows 安裝 Unity。</span><span class="sxs-lookup"><span data-stu-id="40ee5-179">If not, you may need to reinstall Unity with the correct Windows installation.</span></span>

<span data-ttu-id="40ee5-180">**確認.NET 組態**</span><span class="sxs-lookup"><span data-stu-id="40ee5-180">**Verify .NET Configuration**</span></span>

![確認.NET 組態](images/configoptions-375px.png)

1. <span data-ttu-id="40ee5-182">移至**編輯 > 專案設定 > Player** （您可能仍有這在上一個步驟）。</span><span class="sxs-lookup"><span data-stu-id="40ee5-182">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="40ee5-183">在 [**偵測器] 面板**播放程式設定中，選取**Windows 市集**圖示。</span><span class="sxs-lookup"><span data-stu-id="40ee5-183">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="40ee5-184">在 **其他設定**組態區段中，請確定**指令碼的後端**設定為 **.NET**</span><span class="sxs-lookup"><span data-stu-id="40ee5-184">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="40ee5-185">取得套用的所有專案設定得好極了。</span><span class="sxs-lookup"><span data-stu-id="40ee5-185">Awesome job on getting all the project settings applied.</span></span> <span data-ttu-id="40ee5-186">接下來，讓我們新增雷射 ！</span><span class="sxs-lookup"><span data-stu-id="40ee5-186">Next, let us add a hologram!</span></span>

## <a name="chapter-4---create-a-cube"></a><span data-ttu-id="40ee5-187">第 4 層建立 cube</span><span class="sxs-lookup"><span data-stu-id="40ee5-187">Chapter 4 - Create a cube</span></span>

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

<span data-ttu-id="40ee5-188">建立 Unity 專案中的 cube 就如同在 Unity 中建立任何其他物件。</span><span class="sxs-lookup"><span data-stu-id="40ee5-188">Creating a cube in your Unity project is just like creating any other object in Unity.</span></span> <span data-ttu-id="40ee5-189">將放在使用者之前 cube 很容易，因為 Unity 的座標系統對應至真實世界-其中 Unity 中的一個計量是真實的世界中大約一個計量。</span><span class="sxs-lookup"><span data-stu-id="40ee5-189">Placing a cube in front of the user is easy because Unity's coordinate system is mapped to the real world - where one meter in Unity is approximately one meter in the real world.</span></span>
1. <span data-ttu-id="40ee5-190">中的左上角**階層**面板中，選取**建立**下拉式清單中，然後選擇  **3D 物件 > Cube**。</span><span class="sxs-lookup"><span data-stu-id="40ee5-190">In the top left corner of the **Hierarchy** panel, select the **Create** dropdown and choose **3D Object > Cube**.</span></span>
2. <span data-ttu-id="40ee5-191">選取 新建**Cube**中**階層**面板</span><span class="sxs-lookup"><span data-stu-id="40ee5-191">Select the newly created **Cube** in the **Hierarchy** panel</span></span>
3. <span data-ttu-id="40ee5-192">在  **Inspector**尋找**轉換**元件，並變更**位置**來 (**X**:0， **Y**:0， **Z**:2).</span><span class="sxs-lookup"><span data-stu-id="40ee5-192">In the **Inspector** find the **Transform** component and change **Position** to (**X**: 0, **Y**: 0, **Z**: 2).</span></span> <span data-ttu-id="40ee5-193">*這會將 cube 2 公尺之前使用者的起始位置。*</span><span class="sxs-lookup"><span data-stu-id="40ee5-193">*This positions the cube 2 meters in front of the user's starting position.*</span></span>
4. <span data-ttu-id="40ee5-194">在 **轉換**元件，變更**旋轉**到 (**X**:45 **Y**:45 **Z**:45），並變更**擴展**到 (**X**:0.25， **Y**:0.25， **Z**:0.25).</span><span class="sxs-lookup"><span data-stu-id="40ee5-194">In the **Transform** component, change **Rotation** to (**X**: 45, **Y**: 45, **Z**: 45) and change **Scale** to (**X**: 0.25, **Y**: 0.25, **Z**: 0.25).</span></span> <span data-ttu-id="40ee5-195">*這會調整至 0.25 計量 cube。*</span><span class="sxs-lookup"><span data-stu-id="40ee5-195">*This scales the cube to 0.25 meters.*</span></span>
5. <span data-ttu-id="40ee5-196">若要儲存的場景變更，請選取**檔案 > 儲存場景**。</span><span class="sxs-lookup"><span data-stu-id="40ee5-196">To save the scene changes, select **File > Save Scene**.</span></span>

## <a name="chapter-5---verify-on-device-from-unity-editor"></a><span data-ttu-id="40ee5-197">第 5-確認裝置上，從 Unity 編輯器</span><span class="sxs-lookup"><span data-stu-id="40ee5-197">Chapter 5 - Verify on device from Unity editor</span></span>

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

<span data-ttu-id="40ee5-198">既然我們已建立 cube，就可以進行裝置中的快速檢查。</span><span class="sxs-lookup"><span data-stu-id="40ee5-198">Now that we have created our cube, it is time to do a quick check in device.</span></span> <span data-ttu-id="40ee5-199">您可以直接從 Unity 編輯器中。</span><span class="sxs-lookup"><span data-stu-id="40ee5-199">You can do this directly from within the Unity editor.</span></span>

### <a name="initial-setup"></a><span data-ttu-id="40ee5-200">初始設定</span><span class="sxs-lookup"><span data-stu-id="40ee5-200">Initial setup</span></span>
1. <span data-ttu-id="40ee5-201">在開發電腦，在 Unity 中，開啟**檔案 > 組建設定**視窗。</span><span class="sxs-lookup"><span data-stu-id="40ee5-201">On your development PC, in Unity, open **File > Build Settings** window.</span></span>
2. <span data-ttu-id="40ee5-202">變更**平台**要**通用 Windows 平台**按一下**切換平台**</span><span class="sxs-lookup"><span data-stu-id="40ee5-202">Change **Platform** to **Universal Windows Platform** and click **Switch Platfrom**</span></span>

### <a name="for-hololens-use-unity-remoting"></a><span data-ttu-id="40ee5-203">HoloLens 使用 Unity 遠端處理</span><span class="sxs-lookup"><span data-stu-id="40ee5-203">For HoloLens use Unity Remoting</span></span>
1. <span data-ttu-id="40ee5-204">在您的 HoloLens 上安裝，並執行[全像攝影版的遠端播放程式](holographic-remoting-player.md)，可從 Windows 市集。</span><span class="sxs-lookup"><span data-stu-id="40ee5-204">On your HoloLens, install and run the [Holographic Remoting Player](holographic-remoting-player.md), available from the Windows Store.</span></span> <span data-ttu-id="40ee5-205">啟動裝置上的應用程式，它會進入等候狀態，並顯示裝置的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="40ee5-205">Launch the application on the device, and it will enter a waiting state and show the IP address of the device.</span></span> <span data-ttu-id="40ee5-206">請記下 IP。</span><span class="sxs-lookup"><span data-stu-id="40ee5-206">Note down the IP.</span></span>
2. <span data-ttu-id="40ee5-207">開啟**視窗中 > XR > 全像攝影版的模擬**。</span><span class="sxs-lookup"><span data-stu-id="40ee5-207">Open **Window > XR > Holographic Emulation**.</span></span>
3. <span data-ttu-id="40ee5-208">變更**模擬模式**從**無**來**遠端裝置**。</span><span class="sxs-lookup"><span data-stu-id="40ee5-208">Change **Emulation Mode** from **None** to **Remote to Device**.</span></span>
4. <span data-ttu-id="40ee5-209">在 **遠端機器**，輸入您稍早所述的 HoloLens 的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="40ee5-209">In **Remote Machine**, enter the IP address of your HoloLens noted earlier.</span></span>
5. <span data-ttu-id="40ee5-210">按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="40ee5-210">Click **Connect**.</span></span>
6. <span data-ttu-id="40ee5-211">請確定**連線狀態**變更為綠色**Connected**。</span><span class="sxs-lookup"><span data-stu-id="40ee5-211">Ensure the **Connection Status** changes to green **Connected**.</span></span>
7. <span data-ttu-id="40ee5-212">您現在可以按一下現在**播放**在 Unity 編輯器中。</span><span class="sxs-lookup"><span data-stu-id="40ee5-212">Now you can now click **Play** in the Unity editor.</span></span>

<span data-ttu-id="40ee5-213">您現在可以看到 cube 中的裝置，並在編輯器中。</span><span class="sxs-lookup"><span data-stu-id="40ee5-213">You will now be able to see the cube in device and in the editor.</span></span> <span data-ttu-id="40ee5-214">您可以暫停、 檢查物件，及偵錯就像您會在編輯器中，執行應用程式，因為這基本上是發生的事情，但與視訊、 音訊及裝置輸入在主機電腦和裝置之間的網路來回傳輸。</span><span class="sxs-lookup"><span data-stu-id="40ee5-214">You can pause, inspect objects, and debug just like you are running an app in the editor, because that’s essentially what’s happening, but with video, audio, and device input transmitted back and forth across the network between the host machine and the device.</span></span>

### <a name="for-other-mixed-reality-supported-headsets"></a><span data-ttu-id="40ee5-215">其他混合實境支援耳機</span><span class="sxs-lookup"><span data-stu-id="40ee5-215">For other mixed reality supported headsets</span></span>

1. <span data-ttu-id="40ee5-216">連接到開發電腦使用 USB 纜線和 HDMI 的耳機或顯示的連接埠的纜線。</span><span class="sxs-lookup"><span data-stu-id="40ee5-216">Connect the headset to your development PC using the USB cable and the HDMI or display port cable.</span></span>
2. <span data-ttu-id="40ee5-217">啟動**混合實境入口網站**，並確定您已完成初次執行的體驗。</span><span class="sxs-lookup"><span data-stu-id="40ee5-217">Launch the **Mixed Reality Portal** and ensure you have completed the first run experience.</span></span>
3. <span data-ttu-id="40ee5-218">從 Unity，您現在可以按 [播放] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="40ee5-218">From Unity, you can now press the Play button.</span></span>

<span data-ttu-id="40ee5-219">您現在可以看到 cube 呈現在混合的實境耳機，並在編輯器中。</span><span class="sxs-lookup"><span data-stu-id="40ee5-219">You will now be able to see the cube rendering in your mixed reality headset and in the editor.</span></span>

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a><span data-ttu-id="40ee5-220">章節 6-建置，並從 Visual Studio 部署至裝置</span><span class="sxs-lookup"><span data-stu-id="40ee5-220">Chapter 6 - Build and deploy to device from Visual Studio</span></span>

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

<span data-ttu-id="40ee5-221">我們現在已準備好我們的專案，Visual studio 編譯及部署到我們的目標裝置。</span><span class="sxs-lookup"><span data-stu-id="40ee5-221">We are now ready to compile our project to Visual Studio and deploy to our target device.</span></span>

### <a name="export-to-the-visual-studio-solution"></a><span data-ttu-id="40ee5-222">匯出至 Visual Studio 方案</span><span class="sxs-lookup"><span data-stu-id="40ee5-222">Export to the Visual Studio solution</span></span>
1.  <span data-ttu-id="40ee5-223">開啟**檔案 > 組建設定**視窗。</span><span class="sxs-lookup"><span data-stu-id="40ee5-223">Open **File > Build Settings** window.</span></span>
2.  <span data-ttu-id="40ee5-224">按一下 **加入開啟的場景**加入場景。</span><span class="sxs-lookup"><span data-stu-id="40ee5-224">Click **Add Open Scenes** to add the scene.</span></span>
3.  <span data-ttu-id="40ee5-225">變更**平台**要**通用 Windows 平台**然後按一下**切換平台**。</span><span class="sxs-lookup"><span data-stu-id="40ee5-225">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**.</span></span>
4.  <span data-ttu-id="40ee5-226">在  **Windows 市集**設定可確保， **SDK**會**通用 10**。</span><span class="sxs-lookup"><span data-stu-id="40ee5-226">In **Windows Store** settings ensure, **SDK** is **Universal 10**.</span></span>
5.  <span data-ttu-id="40ee5-227">針對目標裝置，留給**任何裝置**occluded 顯示或切換至**HoloLens**。</span><span class="sxs-lookup"><span data-stu-id="40ee5-227">For Target device, leave to **Any Device** for occluded displays or switch to **HoloLens**.</span></span>
6.  <span data-ttu-id="40ee5-228">**UWP 建置型別**應該**D3D**。</span><span class="sxs-lookup"><span data-stu-id="40ee5-228">**UWP Build Type** should be **D3D**.</span></span>
7.  <span data-ttu-id="40ee5-229">**UWP SDK**可能會停留在**最新安裝**。</span><span class="sxs-lookup"><span data-stu-id="40ee5-229">**UWP SDK** could be left at **Latest installed**.</span></span>
8.  <span data-ttu-id="40ee5-230">請檢查**UnityC#專案**偵錯。</span><span class="sxs-lookup"><span data-stu-id="40ee5-230">Check **Unity C# Projects** under Debugging.</span></span>
9.  <span data-ttu-id="40ee5-231">按一下 [建置] 。</span><span class="sxs-lookup"><span data-stu-id="40ee5-231">Click **Build**.</span></span>
10. <span data-ttu-id="40ee5-232">在 [檔案總管] 中，按一下**新的資料夾**並將資料夾命名 **「 應用程式 」**。</span><span class="sxs-lookup"><span data-stu-id="40ee5-232">In the file explorer, click **New Folder** and name the folder **"App"**.</span></span>
11. <span data-ttu-id="40ee5-233">具有**應用程式**按一下 [選取資料夾**選取資料夾**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="40ee5-233">With the **App** folder selected, click the **Select Folder** button.</span></span>
12. <span data-ttu-id="40ee5-234">當完成 Unity 建置，就會顯示 Windows 檔案總管 視窗。</span><span class="sxs-lookup"><span data-stu-id="40ee5-234">When Unity is done building, a Windows File Explorer window will appear.</span></span>
13. <span data-ttu-id="40ee5-235">開啟**應用程式**檔案總管 中的資料夾。</span><span class="sxs-lookup"><span data-stu-id="40ee5-235">Open the **App** folder in file explorer.</span></span>
14. <span data-ttu-id="40ee5-236">開啟產生的 Visual Studio 方案 (在此範例中的 MixedRealityIntroduction.sln)</span><span class="sxs-lookup"><span data-stu-id="40ee5-236">Open the generated Visual Studio solution (MixedRealityIntroduction.sln in this example)</span></span>

### <a name="compile-the-visual-studio-solution"></a><span data-ttu-id="40ee5-237">編譯的 Visual Studio 方案</span><span class="sxs-lookup"><span data-stu-id="40ee5-237">Compile the Visual Studio solution</span></span>

<span data-ttu-id="40ee5-238">最後，我們將會編譯匯出的 Visual Studio 方案，加以部署，並試用看看在裝置上。</span><span class="sxs-lookup"><span data-stu-id="40ee5-238">Finally, we will compile the exported Visual Studio solution, deploy it, and try it out on the device.</span></span>
1. <span data-ttu-id="40ee5-239">在 Visual Studio 中，使用頂端的工具列來變更目標從**偵錯**要**版本**進出**ARM**來**X86**。</span><span class="sxs-lookup"><span data-stu-id="40ee5-239">Using the top toolbar in Visual Studio, change the target from **Debug** to **Release** and from **ARM** to **X86**.</span></span>

<span data-ttu-id="40ee5-240">指示不同部署至模擬器與裝置。</span><span class="sxs-lookup"><span data-stu-id="40ee5-240">The instructions differ for deploying to a device versus the emulator.</span></span> <span data-ttu-id="40ee5-241">請遵循符合您的安裝程式的指示。</span><span class="sxs-lookup"><span data-stu-id="40ee5-241">Follow the instructions that match your setup.</span></span>

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a><span data-ttu-id="40ee5-242">將部署至混合的實境裝置透過 Wi-fi</span><span class="sxs-lookup"><span data-stu-id="40ee5-242">Deploy to mixed reality device over Wi-Fi</span></span>
1. <span data-ttu-id="40ee5-243">按一下箭號旁**本機電腦**按鈕，並變更部署目標，以便**遠端機器**。</span><span class="sxs-lookup"><span data-stu-id="40ee5-243">Click on the arrow next to the **Local Machine** button, and change the deployment target to **Remote Machine**.</span></span>
2. <span data-ttu-id="40ee5-244">輸入您的混合的實境裝置的 IP 位址，然後變更**驗證模式**為通用 （未加密的通訊協定） 的 HoloLens 和**Windows**針對其他裝置。</span><span class="sxs-lookup"><span data-stu-id="40ee5-244">Enter the IP address of your mixed reality device and change **Authentication Mode** to Universal (Unencrypted Protocol) for HoloLens and **Windows** for other devices.</span></span>
3. <span data-ttu-id="40ee5-245">按一下 **偵錯 > 啟動但不偵錯**。</span><span class="sxs-lookup"><span data-stu-id="40ee5-245">Click **Debug > Start without debugging**.</span></span>

<span data-ttu-id="40ee5-246">**針對 HoloLens**，如果這是您第一次部署到您的裝置，您需要配對[使用 Visual Studio](using-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="40ee5-246">**For HoloLens**, If this is the first time deploying to your device, you will need to pair [using Visual Studio](using-visual-studio.md).</span></span>

### <a name="deploy-to-mixed-reality-device-over-usb"></a><span data-ttu-id="40ee5-247">透過 USB 將部署至混合的實境裝置</span><span class="sxs-lookup"><span data-stu-id="40ee5-247">Deploy to mixed reality device over USB</span></span>

<span data-ttu-id="40ee5-248">請確定您的裝置透過 USB 纜線已插入。</span><span class="sxs-lookup"><span data-stu-id="40ee5-248">Ensure you device is plugged in via the USB cable.</span></span>
1. <span data-ttu-id="40ee5-249">**HoloLens**，按一下箭號旁**本機電腦**按鈕，並變更部署目標，以便**裝置**。</span><span class="sxs-lookup"><span data-stu-id="40ee5-249">**For HoloLens**, click on the arrow next to the **Local Machine** button, and change the deployment target to **Device**.</span></span>
2. <span data-ttu-id="40ee5-250">**針對連接到您的電腦的阻擋裝置**，保留到本機電腦的設定。</span><span class="sxs-lookup"><span data-stu-id="40ee5-250">**For targeting occluded devices attached to your PC**, keep the setting to Local Machine.</span></span> <span data-ttu-id="40ee5-251">請確定您已**混合實境入口網站**執行。</span><span class="sxs-lookup"><span data-stu-id="40ee5-251">Ensure you have the **Mixed Reality Portal** running.</span></span>
3. <span data-ttu-id="40ee5-252">按一下 **偵錯 > 啟動但不偵錯**。</span><span class="sxs-lookup"><span data-stu-id="40ee5-252">Click **Debug > Start without debugging**.</span></span>

### <a name="deploy-to-emulator"></a><span data-ttu-id="40ee5-253">部署至模擬器</span><span class="sxs-lookup"><span data-stu-id="40ee5-253">Deploy to Emulator</span></span>
1. <span data-ttu-id="40ee5-254">按一下箭號旁**裝置** 按鈕，並從下拉式清單中，選取**HoloLens 模擬器**。</span><span class="sxs-lookup"><span data-stu-id="40ee5-254">Click on the arrow next to the **Device** button, and from drop down select **HoloLens Emulator**.</span></span>
2. <span data-ttu-id="40ee5-255">按一下 **偵錯 > 啟動但不偵錯**。</span><span class="sxs-lookup"><span data-stu-id="40ee5-255">Click **Debug > Start without debugging**.</span></span>

### <a name="try-out-your-app"></a><span data-ttu-id="40ee5-256">試用您的應用程式</span><span class="sxs-lookup"><span data-stu-id="40ee5-256">Try out your app</span></span>

<span data-ttu-id="40ee5-257">現在，部署您的應用程式時，嘗試移動所有 cube，並觀察它會保持在您面前的世界。</span><span class="sxs-lookup"><span data-stu-id="40ee5-257">Now that your app is deployed, try moving all around the cube and observe that it stays in the world in front of you.</span></span>

## <a name="see-also"></a><span data-ttu-id="40ee5-258">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40ee5-258">See also</span></span>
* [<span data-ttu-id="40ee5-259">Unity 開發概觀</span><span class="sxs-lookup"><span data-stu-id="40ee5-259">Unity development overview</span></span>](unity-development-overview.md)
* [<span data-ttu-id="40ee5-260">使用 Unity 和 Visual Studio 的最佳作法</span><span class="sxs-lookup"><span data-stu-id="40ee5-260">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="40ee5-261">101 MR 基本知識</span><span class="sxs-lookup"><span data-stu-id="40ee5-261">MR Basics 101</span></span>](holograms-101.md)
* [<span data-ttu-id="40ee5-262">MR 基本概念 101E</span><span class="sxs-lookup"><span data-stu-id="40ee5-262">MR Basics 101E</span></span>](holograms-101e.md)
