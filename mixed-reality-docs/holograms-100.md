---
title: MR 基本概念 100-開始使用 Unity
description: 瞭解如何建立您的第一個基本混合現實 "hello world" 應用程式。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: 混合現實，Windows Mixed Reality，HoloLens，沉浸，vr，mr，開始使用，全息影像，學院，教學課程
ms.openlocfilehash: 5e9a90af6b80333addbde2a2e11086372483b7c3
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434780"
---
>[!NOTE]
><span data-ttu-id="10c03-104">混合現實學術教學課程的設計是使用 HoloLens （第1代）和混合現實的沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="10c03-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="10c03-105">因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="10c03-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="10c03-106">這些教學課程 **_不_** 會以最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="10c03-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="10c03-107">系統會保留這些資訊，以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="10c03-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="10c03-108">HoloLens 2 已張貼[一系列新的教學](mrlearning-base.md)課程。</span><span class="sxs-lookup"><span data-stu-id="10c03-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-basics-100-getting-started-with-unity"></a><span data-ttu-id="10c03-109">MR 基本概念100：開始使用 Unity</span><span class="sxs-lookup"><span data-stu-id="10c03-109">MR Basics 100: Getting started with Unity</span></span>

<span data-ttu-id="10c03-110">本教學課程將逐步引導您建立以 Unity 建立的基本混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="10c03-110">This tutorial will walk you through creating a basic mixed reality app built with Unity.</span></span>

## <a name="device-support"></a><span data-ttu-id="10c03-111">裝置支援</span><span class="sxs-lookup"><span data-stu-id="10c03-111">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="10c03-112">粗</span><span class="sxs-lookup"><span data-stu-id="10c03-112">Course</span></span></th><th style="width:150px"> <span data-ttu-id="10c03-113"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="10c03-113"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="10c03-114"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="10c03-114"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="10c03-115">MR 基本概念100：開始使用 Unity</span><span class="sxs-lookup"><span data-stu-id="10c03-115">MR Basics 100: Getting started with Unity</span></span></td><td style="text-align: center;"> <span data-ttu-id="10c03-116">✔️</span><span class="sxs-lookup"><span data-stu-id="10c03-116">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="10c03-117">✔️</span><span class="sxs-lookup"><span data-stu-id="10c03-117">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="10c03-118">必要條件</span><span class="sxs-lookup"><span data-stu-id="10c03-118">Prerequisites</span></span>

* <span data-ttu-id="10c03-119">[已安裝正確工具](install-the-tools.md)的 WINDOWS 10 電腦。</span><span class="sxs-lookup"><span data-stu-id="10c03-119">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

## <a name="chapter-1---create-a-new-project"></a><span data-ttu-id="10c03-120">第1章-建立新專案</span><span class="sxs-lookup"><span data-stu-id="10c03-120">Chapter 1 - Create a New Project</span></span>

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

<span data-ttu-id="10c03-121">若要使用 Unity 來建立應用程式，您必須先建立專案。</span><span class="sxs-lookup"><span data-stu-id="10c03-121">To build an app with Unity, you first need to create a project.</span></span> <span data-ttu-id="10c03-122">此專案會組織成幾個資料夾，其中最重要的是您的資產資料夾。</span><span class="sxs-lookup"><span data-stu-id="10c03-122">This project is organized into a few folders, the most important of which is your Assets folder.</span></span> <span data-ttu-id="10c03-123">這是保存您從數位內容建立工具（例如 Maya、最大影院4D 或 Photoshop）匯入之所有資產的資料夾，您使用 Visual Studio 或慣用的程式碼編輯器建立的所有程式碼，以及 Unity 在撰寫場景時所建立的任何內容檔案數目、動畫，以及編輯器中的其他 Unity 資產類型。</span><span class="sxs-lookup"><span data-stu-id="10c03-123">This is the folder that holds all assets you import from digital content creation tools such as Maya, Max Cinema 4D or Photoshop, all code you create with Visual Studio or your favorite code editor, and any number of content files that Unity creates as you compose scenes, animations and other Unity asset types in the editor.</span></span>

<span data-ttu-id="10c03-124">若要建立和部署 UWP 應用程式，Unity 可以將專案匯出為 Visual Studio 方案，其中包含所有必要的資產和程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="10c03-124">To build and deploy UWP apps, Unity can export the project as a Visual Studio solution that will contain all necessary asset and code files.</span></span>

1. <span data-ttu-id="10c03-125">啟動 Unity</span><span class="sxs-lookup"><span data-stu-id="10c03-125">Start Unity</span></span>
2. <span data-ttu-id="10c03-126">選取 [**新增**]</span><span class="sxs-lookup"><span data-stu-id="10c03-126">Select **New**</span></span>
3. <span data-ttu-id="10c03-127">輸入專案名稱（例如 "MixedRealityIntroduction"）</span><span class="sxs-lookup"><span data-stu-id="10c03-127">Enter a project name (e.g. "MixedRealityIntroduction")</span></span>
4. <span data-ttu-id="10c03-128">輸入儲存專案的位置</span><span class="sxs-lookup"><span data-stu-id="10c03-128">Enter a location to save your project</span></span>
5. <span data-ttu-id="10c03-129">確定已選取**3d**切換</span><span class="sxs-lookup"><span data-stu-id="10c03-129">Ensure the **3D** toggle is selected</span></span>
6. <span data-ttu-id="10c03-130">選取 [**建立專案**]</span><span class="sxs-lookup"><span data-stu-id="10c03-130">Select **Create project**</span></span>

<span data-ttu-id="10c03-131">恭喜，您可以立即開始進行混合現實的自訂。</span><span class="sxs-lookup"><span data-stu-id="10c03-131">Congrats, you are all setup to get started with your mixed reality customizations now.</span></span>

## <a name="chapter-2---setup-the-camera"></a><span data-ttu-id="10c03-132">第2章-設定相機</span><span class="sxs-lookup"><span data-stu-id="10c03-132">Chapter 2 - Setup the Camera</span></span>

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

<span data-ttu-id="10c03-133">Unity 主要攝影機會處理 head 追蹤和 stereoscopic 轉譯。</span><span class="sxs-lookup"><span data-stu-id="10c03-133">The Unity Main Camera handles head tracking and stereoscopic rendering.</span></span> <span data-ttu-id="10c03-134">主要相機有幾個變更可用於混合現實。</span><span class="sxs-lookup"><span data-stu-id="10c03-134">There are a few changes to make to the Main Camera to use it with mixed reality.</span></span>

1. <span data-ttu-id="10c03-135">選取檔案 > 新場景</span><span class="sxs-lookup"><span data-stu-id="10c03-135">Select File > New Scene</span></span>

<span data-ttu-id="10c03-136">首先，如果您認為使用者的開始位置是（**X**：0， **Y**：0， **Z**：0），則可以更輕鬆地配置應用程式。</span><span class="sxs-lookup"><span data-stu-id="10c03-136">First, it will be easier to lay out your app if you imagine the starting position of the user as (**X**: 0, **Y**: 0, **Z**: 0).</span></span> <span data-ttu-id="10c03-137">由於主要攝影機是追蹤使用者頭部的移動，因此可以藉由設定主要攝影機的開始位置來設定使用者的開始位置。</span><span class="sxs-lookup"><span data-stu-id="10c03-137">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>

1. <span data-ttu-id="10c03-138">**在 [階層**] 面板中選取**主要相機**</span><span class="sxs-lookup"><span data-stu-id="10c03-138">Select **Main Camera** in the **Hierarchy** panel</span></span>
2. <span data-ttu-id="10c03-139">在 [偵測**器**] 面板中，尋找 [**轉換**] 元件，並將**位置**從（**x**：0， **y**：1， **z**：-10）變更為（**x**：0， **y**：0， **Z**：0）</span><span class="sxs-lookup"><span data-stu-id="10c03-139">In the **Inspector** panel, find the **Transform** component and change the **Position** from (**X**: 0, **Y**: 1, **Z**: -10) to (**X**: 0, **Y**: 0, **Z**: 0)</span></span>

<span data-ttu-id="10c03-140">第二，預設的相機背景需要一些思考。</span><span class="sxs-lookup"><span data-stu-id="10c03-140">Second, the default Camera background needs some thought.</span></span>

<span data-ttu-id="10c03-141">若是**HoloLens 應用程式**，真實世界應該會出現在相機呈現的所有內容後方，而不是 Skybox 材質。</span><span class="sxs-lookup"><span data-stu-id="10c03-141">**For HoloLens applications**, the real world should appear behind everything the camera renders, not a Skybox texture.</span></span>

1. <span data-ttu-id="10c03-142">在 [階層] 面板中仍然選取**主要相機**後，**在 [偵測** **器**] 面板中尋找**相機**元件，並將 [**清除旗標**] 下拉式清單從**Skybox**變更為**純色**。</span><span class="sxs-lookup"><span data-stu-id="10c03-142">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Clear Flags** dropdown from **Skybox** to **Solid Color**.</span></span>
2. <span data-ttu-id="10c03-143">選取**背景**色彩選擇器，並將**RGBA**值變更為（0，0，0，0）</span><span class="sxs-lookup"><span data-stu-id="10c03-143">Select the **Background** color picker and change the **RGBA** values to (0, 0, 0, 0)</span></span>

<span data-ttu-id="10c03-144">**對於以沉浸式耳機為目標的混合現實應用程式**，我們可以使用 Unity 提供的預設 Skybox 材質。</span><span class="sxs-lookup"><span data-stu-id="10c03-144">**For mixed reality applications targeted to immersive headsets**, we can use the default Skybox texture that Unity provides.</span></span>

1. <span data-ttu-id="10c03-145">**在 [階層] 面板中**，仍然選取**主要相機**，請在 [偵測**器**] 面板中尋找**相機**元件，並將 [**清除旗標**] 下拉式清單保留為**Skybox**。</span><span class="sxs-lookup"><span data-stu-id="10c03-145">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Clear Flags** dropdown to **Skybox**.</span></span>

<span data-ttu-id="10c03-146">第三，讓我們考慮 Unity 中附近的裁剪平面，防止物件在使用者接近物件或物件接近使用者的情況下，呈現太接近使用者的眼睛。</span><span class="sxs-lookup"><span data-stu-id="10c03-146">Third, let us consider the near clip plane in Unity and prevent objects from being rendered too close to the users eyes as a user approaches an object or an object approaches a user.</span></span>

<span data-ttu-id="10c03-147">若是**hololens 應用程式**，接近的裁剪平面可以設定為[hololens 建議](camera-in-unity.md#clip-planes)的0.85 計量。</span><span class="sxs-lookup"><span data-stu-id="10c03-147">**For HoloLens applications**, the near clip plane can be set to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 meters.</span></span>

1. <span data-ttu-id="10c03-148">**在 [階層] 面板中**仍然選取**主要相機**時，請在 [偵測**器**] 面板中尋找**相機**元件，並將 [**近端剪切平面**] 欄位從預設**0.3**變更為 [HoloLens 建議**0.85]** .</span><span class="sxs-lookup"><span data-stu-id="10c03-148">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Near Clip Plane** field from the default **0.3** to the HoloLens recommended **0.85**.</span></span>

<span data-ttu-id="10c03-149">**對於以沉浸式耳機為目標的混合現實應用程式**，我們可以使用 Unity 提供的預設設定。</span><span class="sxs-lookup"><span data-stu-id="10c03-149">**For mixed reality applications targeted to immersive headsets**, we can use the default setting that Unity provides.</span></span>

1. <span data-ttu-id="10c03-150">**在 [階層] 面板中**仍然選取**主要相機**時，請在 [偵測**器**] 面板中尋找**相機**元件，並將 [**近端剪切平面**] 欄位保留為預設值**0.3**。</span><span class="sxs-lookup"><span data-stu-id="10c03-150">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Near Clip Plane** field to the default **0.3**.</span></span>

<span data-ttu-id="10c03-151">最後，讓我們來儲存我們目前的進度。</span><span class="sxs-lookup"><span data-stu-id="10c03-151">Finally, let us save our progress so far.</span></span> <span data-ttu-id="10c03-152">若要儲存場景變更，請選取 檔案 **> 另存場景**，將場景命名為**Main**，然後選取 **儲存**。</span><span class="sxs-lookup"><span data-stu-id="10c03-152">To save the scene changes, select **File > Save Scene As**, name the scene **Main**, and select **Save**.</span></span>

## <a name="chapter-3---setup-the-project-settings"></a><span data-ttu-id="10c03-153">第3章-設定專案設定</span><span class="sxs-lookup"><span data-stu-id="10c03-153">Chapter 3 - Setup the Project Settings</span></span>

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

<span data-ttu-id="10c03-154">在本章中，我們將設定一些 Unity 專案設定，以協助我們以 Windows 全像開發 SDK 為目標。</span><span class="sxs-lookup"><span data-stu-id="10c03-154">In this chapter, we will set some Unity project settings that help us target the Windows Holographic SDK for development.</span></span> <span data-ttu-id="10c03-155">我們也會為應用程式設定一些品質設定。</span><span class="sxs-lookup"><span data-stu-id="10c03-155">We will also set some quality settings for our application.</span></span> <span data-ttu-id="10c03-156">最後，我們會確保組建目標設定為 Windows Store。</span><span class="sxs-lookup"><span data-stu-id="10c03-156">Finally, we will ensure our build targets are set to Windows Store.</span></span>

### <a name="unity-performance-and-quality-settings"></a><span data-ttu-id="10c03-157">Unity 效能和品質設定</span><span class="sxs-lookup"><span data-stu-id="10c03-157">Unity performance and quality settings</span></span>

<span data-ttu-id="10c03-158">**HoloLens 的 Unity 品質設定**</span><span class="sxs-lookup"><span data-stu-id="10c03-158">**Unity quality settings for HoloLens**</span></span>

![HoloLens 的 Unity 品質設定](images/qualitysettings.png)

<span data-ttu-id="10c03-160">因為在 HoloLens 上維持高畫面播放速率相當重要，所以我們想要調整品質設定以取得最快的效能。</span><span class="sxs-lookup"><span data-stu-id="10c03-160">Since maintaining high framerate on HoloLens is so important, we want the quality settings tuned for fastest performance.</span></span> <span data-ttu-id="10c03-161">如需更詳細的效能資訊，請[查看 Unity 的效能建議](performance-recommendations-for-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="10c03-161">For more detailed performance information, [Performance recommendations for Unity](performance-recommendations-for-unity.md).</span></span>

1. <span data-ttu-id="10c03-162">選取 [**編輯] > 專案設定 > 品質**</span><span class="sxs-lookup"><span data-stu-id="10c03-162">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="10c03-163">選取 [ **Windows Store** ] 標誌底下的**下拉式清單**，然後選取 [**非常低**]。</span><span class="sxs-lookup"><span data-stu-id="10c03-163">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="10c03-164">當 [Windows Store] 資料行中的方塊和**非常低**的資料列都是綠色時，您會知道設定已正確套用。</span><span class="sxs-lookup"><span data-stu-id="10c03-164">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green.</span></span>

<span data-ttu-id="10c03-165">**針對以 pixels occluded 為目標的混合現實應用程式**，您可以將品質設定保留為預設值。</span><span class="sxs-lookup"><span data-stu-id="10c03-165">**For mixed reality applications targeted to occluded displays**, you can leave the quality settings to its default values.</span></span>

### <a name="target-windows-10-sdk"></a><span data-ttu-id="10c03-166">以 Windows 10 SDK 為目標</span><span class="sxs-lookup"><span data-stu-id="10c03-166">Target Windows 10 SDK</span></span>

<span data-ttu-id="10c03-167">**以 Windows 全像的 SDK 為目標**</span><span class="sxs-lookup"><span data-stu-id="10c03-167">**Target Windows Holographic SDK**</span></span>

![以 Windows 全像的 SDK 為目標](images/xrsettings.png)

<span data-ttu-id="10c03-169">我們需要讓 Unity 知道，我們嘗試匯出的應用程式應該建立[沉浸式視圖](app-views.md)，而不是2d 視圖。</span><span class="sxs-lookup"><span data-stu-id="10c03-169">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="10c03-170">我們的作法是在以 Windows 10 SDK 為目標的 Unity 上啟用虛擬實境支援。</span><span class="sxs-lookup"><span data-stu-id="10c03-170">We do this by enabling Virtual Reality support on Unity targeting the Windows 10 SDK.</span></span>

1. <span data-ttu-id="10c03-171">移至 **編輯 > 專案設定 > Player**。</span><span class="sxs-lookup"><span data-stu-id="10c03-171">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="10c03-172">在 [玩家設定] 的 [偵測**器] 面板**中，選取 [ **Windows Store** ] 圖示。</span><span class="sxs-lookup"><span data-stu-id="10c03-172">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="10c03-173">展開 [ **XR 設定**] 群組。</span><span class="sxs-lookup"><span data-stu-id="10c03-173">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="10c03-174">**在轉譯區段中**，勾選 [**支援虛擬實境**] 核取方塊，以新增**虛擬實境 sdk**清單。</span><span class="sxs-lookup"><span data-stu-id="10c03-174">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="10c03-175">確認清單中出現**Windows Mixed Reality** 。</span><span class="sxs-lookup"><span data-stu-id="10c03-175">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="10c03-176">如果沒有，請選取清單底部的 [ **+** ] 按鈕，然後選擇 [ **Windows Mixed Reality**]。</span><span class="sxs-lookup"><span data-stu-id="10c03-176">If not, select the **+** button at the bottom of the list and choose **Windows Mixed Reality**.</span></span>

>[!NOTE]
><span data-ttu-id="10c03-177">如果您看不到 [ **Windows store** ] 圖示，請再次檢查以確定您在安裝之前已選取 [windows Store .Net 腳本後端]。</span><span class="sxs-lookup"><span data-stu-id="10c03-177">If you do not see the **Windows Store** icon, double check to make sure you selected the Windows Store .NET Scripting Backend prior to installation.</span></span> <span data-ttu-id="10c03-178">如果不是，您可能需要使用正確的 Windows 安裝來重新安裝 Unity。</span><span class="sxs-lookup"><span data-stu-id="10c03-178">If not, you may need to reinstall Unity with the correct Windows installation.</span></span>

<span data-ttu-id="10c03-179">**確認 .NET 設定**</span><span class="sxs-lookup"><span data-stu-id="10c03-179">**Verify .NET Configuration**</span></span>

![確認 .NET 設定](images/configoptions-375px.png)

1. <span data-ttu-id="10c03-181">移至 **編輯 > 專案設定 > 播放** （您在上一個步驟中可能還是會這麼做）。</span><span class="sxs-lookup"><span data-stu-id="10c03-181">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="10c03-182">在 [玩家設定] 的 [偵測**器] 面板**中，選取 [ **Windows Store** ] 圖示。</span><span class="sxs-lookup"><span data-stu-id="10c03-182">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="10c03-183">在 [**其他設定**] 區段中，確認 [**腳本後端**] 已設定為 [ **.net** ]</span><span class="sxs-lookup"><span data-stu-id="10c03-183">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="10c03-184">取得套用所有專案設定的絕佳作業。</span><span class="sxs-lookup"><span data-stu-id="10c03-184">Awesome job on getting all the project settings applied.</span></span> <span data-ttu-id="10c03-185">接下來，讓我們新增全息影像！</span><span class="sxs-lookup"><span data-stu-id="10c03-185">Next, let us add a hologram!</span></span>

## <a name="chapter-4---create-a-cube"></a><span data-ttu-id="10c03-186">第4章-建立 cube</span><span class="sxs-lookup"><span data-stu-id="10c03-186">Chapter 4 - Create a cube</span></span>

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

<span data-ttu-id="10c03-187">在 Unity 專案中建立 cube，就像在 Unity 中建立任何其他物件一樣。</span><span class="sxs-lookup"><span data-stu-id="10c03-187">Creating a cube in your Unity project is just like creating any other object in Unity.</span></span> <span data-ttu-id="10c03-188">將 cube 放在使用者的前方很容易，因為 Unity 的座標系統會對應到真實世界-其中 Unity 中的一個計量是真實世界中的一個計量。</span><span class="sxs-lookup"><span data-stu-id="10c03-188">Placing a cube in front of the user is easy because Unity's coordinate system is mapped to the real world - where one meter in Unity is approximately one meter in the real world.</span></span>

1. <span data-ttu-id="10c03-189">**在 [階層] 面板的**左上角，選取 [**建立**] 下拉式清單，然後選擇 [ **3d 物件 > Cube**]。</span><span class="sxs-lookup"><span data-stu-id="10c03-189">In the top left corner of the **Hierarchy** panel, select the **Create** dropdown and choose **3D Object > Cube**.</span></span>
2. <span data-ttu-id="10c03-190">在 [階層 **] 面板中**選取新建立的**Cube**</span><span class="sxs-lookup"><span data-stu-id="10c03-190">Select the newly created **Cube** in the **Hierarchy** panel</span></span>
3. <span data-ttu-id="10c03-191">在偵測**器**中，尋找 [**轉換**] 元件，並將 [**位置**] 變更為（**X**：0， **Y**：0， **Z**：2）。</span><span class="sxs-lookup"><span data-stu-id="10c03-191">In the **Inspector** find the **Transform** component and change **Position** to (**X**: 0, **Y**: 0, **Z**: 2).</span></span> <span data-ttu-id="10c03-192">*這會將 cube 2 計量置於使用者開始位置的前方。*</span><span class="sxs-lookup"><span data-stu-id="10c03-192">*This positions the cube 2 meters in front of the user's starting position.*</span></span>
4. <span data-ttu-id="10c03-193">在 [**轉換**] 元件中，將 [**旋轉**] 變更為（**x**：45， **Y**：45， **Z**：45），並將 [**調整**為] （**x**：0.25， **Y**：0.25， **z**：0.25）。</span><span class="sxs-lookup"><span data-stu-id="10c03-193">In the **Transform** component, change **Rotation** to (**X**: 45, **Y**: 45, **Z**: 45) and change **Scale** to (**X**: 0.25, **Y**: 0.25, **Z**: 0.25).</span></span> <span data-ttu-id="10c03-194">*這會將 cube 調整為0.25 計量。*</span><span class="sxs-lookup"><span data-stu-id="10c03-194">*This scales the cube to 0.25 meters.*</span></span>
5. <span data-ttu-id="10c03-195">若要儲存場景變更，請選取 檔案 **> 儲存場景**。</span><span class="sxs-lookup"><span data-stu-id="10c03-195">To save the scene changes, select **File > Save Scene**.</span></span>

## <a name="chapter-5---verify-on-device-from-unity-editor"></a><span data-ttu-id="10c03-196">第5章-從 Unity 編輯器進行裝置驗證</span><span class="sxs-lookup"><span data-stu-id="10c03-196">Chapter 5 - Verify on device from Unity editor</span></span>

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

<span data-ttu-id="10c03-197">既然我們已經建立 cube，就可以開始快速檢查裝置。</span><span class="sxs-lookup"><span data-stu-id="10c03-197">Now that we have created our cube, it is time to do a quick check in device.</span></span> <span data-ttu-id="10c03-198">您可以直接從 Unity 編輯器中執行此動作。</span><span class="sxs-lookup"><span data-stu-id="10c03-198">You can do this directly from within the Unity editor.</span></span>

### <a name="initial-setup"></a><span data-ttu-id="10c03-199">初始設定</span><span class="sxs-lookup"><span data-stu-id="10c03-199">Initial setup</span></span>

1. <span data-ttu-id="10c03-200">在開發電腦的 Unity 中，開啟 [檔案] **> [組建設定**] 視窗。</span><span class="sxs-lookup"><span data-stu-id="10c03-200">On your development PC, in Unity, open **File > Build Settings** window.</span></span>
2. <span data-ttu-id="10c03-201">將**平臺**變更為**通用 Windows 平臺**，然後按一下 **切換平臺**</span><span class="sxs-lookup"><span data-stu-id="10c03-201">Change **Platform** to **Universal Windows Platform** and click **Switch Platfrom**</span></span>

### <a name="for-hololens-use-unity-remoting"></a><span data-ttu-id="10c03-202">若是 HoloLens，請使用 Unity Remoting</span><span class="sxs-lookup"><span data-stu-id="10c03-202">For HoloLens use Unity Remoting</span></span>

1. <span data-ttu-id="10c03-203">在您的 HoloLens 上，安裝並執行可從 Windows 市集中取得的全像攝影[遠端播放](holographic-remoting-player.md)程式。</span><span class="sxs-lookup"><span data-stu-id="10c03-203">On your HoloLens, install and run the [Holographic Remoting Player](holographic-remoting-player.md), available from the Windows Store.</span></span> <span data-ttu-id="10c03-204">在裝置上啟動應用程式，它會進入等候狀態，並顯示裝置的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="10c03-204">Launch the application on the device, and it will enter a waiting state and show the IP address of the device.</span></span> <span data-ttu-id="10c03-205">記下 IP。</span><span class="sxs-lookup"><span data-stu-id="10c03-205">Note down the IP.</span></span>
2. <span data-ttu-id="10c03-206">開啟**Window > XR >** 全像的模擬。</span><span class="sxs-lookup"><span data-stu-id="10c03-206">Open **Window > XR > Holographic Emulation**.</span></span>
3. <span data-ttu-id="10c03-207">將**模擬模式**從 [**無**] 變更為 [**遠端] 至 [裝置**]。</span><span class="sxs-lookup"><span data-stu-id="10c03-207">Change **Emulation Mode** from **None** to **Remote to Device**.</span></span>
4. <span data-ttu-id="10c03-208">在 [**遠端電腦**] 中，輸入您先前記下的 HOLOLENS 的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="10c03-208">In **Remote Machine**, enter the IP address of your HoloLens noted earlier.</span></span>
5. <span data-ttu-id="10c03-209">按一下 **\[連線\]** 。</span><span class="sxs-lookup"><span data-stu-id="10c03-209">Click **Connect**.</span></span>
6. <span data-ttu-id="10c03-210">確定 [**連接狀態**] 變更為 [綠色**已連接**]。</span><span class="sxs-lookup"><span data-stu-id="10c03-210">Ensure the **Connection Status** changes to green **Connected**.</span></span>
7. <span data-ttu-id="10c03-211">現在您可以按一下 Unity 編輯器中的 [**播放**]。</span><span class="sxs-lookup"><span data-stu-id="10c03-211">Now you can now click **Play** in the Unity editor.</span></span>

<span data-ttu-id="10c03-212">您現在將能夠在 [裝置] 和編輯器中看到 cube。</span><span class="sxs-lookup"><span data-stu-id="10c03-212">You will now be able to see the cube in device and in the editor.</span></span> <span data-ttu-id="10c03-213">就像在編輯器中執行應用程式一樣，您可以暫停、檢查物件和進行 debug，因為這基本上是發生的情況，但是會在主機電腦與裝置之間的網路上來回傳輸影片、音訊和裝置輸入。</span><span class="sxs-lookup"><span data-stu-id="10c03-213">You can pause, inspect objects, and debug just like you are running an app in the editor, because that’s essentially what’s happening, but with video, audio, and device input transmitted back and forth across the network between the host machine and the device.</span></span>

### <a name="for-other-mixed-reality-supported-headsets"></a><span data-ttu-id="10c03-214">適用于其他混合現實支援的耳機</span><span class="sxs-lookup"><span data-stu-id="10c03-214">For other mixed reality supported headsets</span></span>

1. <span data-ttu-id="10c03-215">使用 USB 纜線和 HDMI 或顯示器埠纜線，將耳機連接到您的開發電腦。</span><span class="sxs-lookup"><span data-stu-id="10c03-215">Connect the headset to your development PC using the USB cable and the HDMI or display port cable.</span></span>
2. <span data-ttu-id="10c03-216">啟動**混合現實入口網站**，並確定您已完成第一次執行體驗。</span><span class="sxs-lookup"><span data-stu-id="10c03-216">Launch the **Mixed Reality Portal** and ensure you have completed the first run experience.</span></span>
3. <span data-ttu-id="10c03-217">從 Unity，您現在可以按下 [播放] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="10c03-217">From Unity, you can now press the Play button.</span></span>

<span data-ttu-id="10c03-218">您現在可以在混合現實頭戴式耳機和編輯器中看到 cube 呈現。</span><span class="sxs-lookup"><span data-stu-id="10c03-218">You will now be able to see the cube rendering in your mixed reality headset and in the editor.</span></span>

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a><span data-ttu-id="10c03-219">第6章-從 Visual Studio 建立及部署至裝置</span><span class="sxs-lookup"><span data-stu-id="10c03-219">Chapter 6 - Build and deploy to device from Visual Studio</span></span>

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

<span data-ttu-id="10c03-220">我們現在已準備好編譯專案，以 Visual Studio 並部署至目標裝置。</span><span class="sxs-lookup"><span data-stu-id="10c03-220">We are now ready to compile our project to Visual Studio and deploy to our target device.</span></span>

### <a name="export-to-the-visual-studio-solution"></a><span data-ttu-id="10c03-221">匯出至 Visual Studio 解決方案</span><span class="sxs-lookup"><span data-stu-id="10c03-221">Export to the Visual Studio solution</span></span>

1.  <span data-ttu-id="10c03-222">開啟 檔案 **> 組建設定** 視窗。</span><span class="sxs-lookup"><span data-stu-id="10c03-222">Open **File > Build Settings** window.</span></span>
2.  <span data-ttu-id="10c03-223">按一下 [新增] [**開啟場景**] 以加入場景。</span><span class="sxs-lookup"><span data-stu-id="10c03-223">Click **Add Open Scenes** to add the scene.</span></span>
3.  <span data-ttu-id="10c03-224">將**平臺**變更為**通用 Windows 平臺**，然後按一下 [**切換平臺**]。</span><span class="sxs-lookup"><span data-stu-id="10c03-224">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**.</span></span>
4.  <span data-ttu-id="10c03-225">在**Windows Store**設定中， **SDK**為**通用 10**。</span><span class="sxs-lookup"><span data-stu-id="10c03-225">In **Windows Store** settings ensure, **SDK** is **Universal 10**.</span></span>
5.  <span data-ttu-id="10c03-226">針對 [目標裝置]，保留 [**任何裝置**以進行 pixels occluded] 或 [切換至**HoloLens**]。</span><span class="sxs-lookup"><span data-stu-id="10c03-226">For Target device, leave to **Any Device** for occluded displays or switch to **HoloLens**.</span></span>
6.  <span data-ttu-id="10c03-227">**UWP 組建類型**應該是**D3D**。</span><span class="sxs-lookup"><span data-stu-id="10c03-227">**UWP Build Type** should be **D3D**.</span></span>
7.  <span data-ttu-id="10c03-228">**UWP SDK**可以保持在**最新的安裝**位置。</span><span class="sxs-lookup"><span data-stu-id="10c03-228">**UWP SDK** could be left at **Latest installed**.</span></span>
8.  <span data-ttu-id="10c03-229">檢查 [調試] 底下的**Unity C#專案**。</span><span class="sxs-lookup"><span data-stu-id="10c03-229">Check **Unity C# Projects** under Debugging.</span></span>
9.  <span data-ttu-id="10c03-230">按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="10c03-230">Click **Build**.</span></span>
10. <span data-ttu-id="10c03-231">在 [檔案瀏覽器] 中，按一下 [**新增資料夾**]，並將資料夾命名為「**應用程式**」。</span><span class="sxs-lookup"><span data-stu-id="10c03-231">In the file explorer, click **New Folder** and name the folder **"App"**.</span></span>
11. <span data-ttu-id="10c03-232">選取**應用程式**資料夾後，按一下 [**選取資料夾**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="10c03-232">With the **App** folder selected, click the **Select Folder** button.</span></span>
12. <span data-ttu-id="10c03-233">Unity 完成建立時，將會出現 Windows 檔案瀏覽器視窗。</span><span class="sxs-lookup"><span data-stu-id="10c03-233">When Unity is done building, a Windows File Explorer window will appear.</span></span>
13. <span data-ttu-id="10c03-234">在檔案瀏覽器中開啟**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="10c03-234">Open the **App** folder in file explorer.</span></span>
14. <span data-ttu-id="10c03-235">開啟產生的 Visual Studio 方案（在此範例中為 MixedRealityIntroduction）</span><span class="sxs-lookup"><span data-stu-id="10c03-235">Open the generated Visual Studio solution (MixedRealityIntroduction.sln in this example)</span></span>

### <a name="compile-the-visual-studio-solution"></a><span data-ttu-id="10c03-236">編譯 Visual Studio 解決方案</span><span class="sxs-lookup"><span data-stu-id="10c03-236">Compile the Visual Studio solution</span></span>

<span data-ttu-id="10c03-237">最後，我們將編譯匯出的 Visual Studio 解決方案、部署它，然後在裝置上試試看。</span><span class="sxs-lookup"><span data-stu-id="10c03-237">Finally, we will compile the exported Visual Studio solution, deploy it, and try it out on the device.</span></span>

1. <span data-ttu-id="10c03-238">使用 Visual Studio 中的頂端工具列，將目標從 [**調試**] 變更為 [**發行**]，將 [從**ARM** ] 變更為**X86**。</span><span class="sxs-lookup"><span data-stu-id="10c03-238">Using the top toolbar in Visual Studio, change the target from **Debug** to **Release** and from **ARM** to **X86**.</span></span>

<span data-ttu-id="10c03-239">部署至裝置與模擬器的指示不同。</span><span class="sxs-lookup"><span data-stu-id="10c03-239">The instructions differ for deploying to a device versus the emulator.</span></span> <span data-ttu-id="10c03-240">遵循符合您設定的指示。</span><span class="sxs-lookup"><span data-stu-id="10c03-240">Follow the instructions that match your setup.</span></span>

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a><span data-ttu-id="10c03-241">透過 Wi-fi 部署到混合現實裝置</span><span class="sxs-lookup"><span data-stu-id="10c03-241">Deploy to mixed reality device over Wi-Fi</span></span>

1. <span data-ttu-id="10c03-242">按一下 [**本機電腦**] 按鈕旁的箭號，然後將部署目標變更為 [**遠端電腦**]。</span><span class="sxs-lookup"><span data-stu-id="10c03-242">Click on the arrow next to the **Local Machine** button, and change the deployment target to **Remote Machine**.</span></span>
2. <span data-ttu-id="10c03-243">輸入您 mixed reality 裝置的 IP 位址，並將其他裝置的 HoloLens 和**Windows**的**驗證模式**變更為通用（未加密的通訊協定）。</span><span class="sxs-lookup"><span data-stu-id="10c03-243">Enter the IP address of your mixed reality device and change **Authentication Mode** to Universal (Unencrypted Protocol) for HoloLens and **Windows** for other devices.</span></span>
3. <span data-ttu-id="10c03-244">按一下 [ **Debug > 啟動但不進行調試**]。</span><span class="sxs-lookup"><span data-stu-id="10c03-244">Click **Debug > Start without debugging**.</span></span>

<span data-ttu-id="10c03-245">若是**HoloLens**，如果這是您第一次部署至您的裝置，您將需要[使用 Visual Studio](using-visual-studio.md)配對。</span><span class="sxs-lookup"><span data-stu-id="10c03-245">**For HoloLens**, If this is the first time deploying to your device, you will need to pair [using Visual Studio](using-visual-studio.md).</span></span>

### <a name="deploy-to-mixed-reality-device-over-usb"></a><span data-ttu-id="10c03-246">透過 USB 部署到混合現實裝置</span><span class="sxs-lookup"><span data-stu-id="10c03-246">Deploy to mixed reality device over USB</span></span>

<span data-ttu-id="10c03-247">請確定您的裝置已透過 USB 纜線插入。</span><span class="sxs-lookup"><span data-stu-id="10c03-247">Ensure you device is plugged in via the USB cable.</span></span>

1. <span data-ttu-id="10c03-248">若是**HoloLens**，請按一下 [**本機電腦**] 按鈕旁的箭號，然後將部署目標變更為 [**裝置**]。</span><span class="sxs-lookup"><span data-stu-id="10c03-248">**For HoloLens**, click on the arrow next to the **Local Machine** button, and change the deployment target to **Device**.</span></span>
2. <span data-ttu-id="10c03-249">**針對連接到您電腦的 pixels occluded 裝置**，請將設定保留在 [本機電腦]。</span><span class="sxs-lookup"><span data-stu-id="10c03-249">**For targeting occluded devices attached to your PC**, keep the setting to Local Machine.</span></span> <span data-ttu-id="10c03-250">請確定您有執行中的**混合現實入口網站**。</span><span class="sxs-lookup"><span data-stu-id="10c03-250">Ensure you have the **Mixed Reality Portal** running.</span></span>
3. <span data-ttu-id="10c03-251">按一下 [ **Debug > 啟動但不進行調試**]。</span><span class="sxs-lookup"><span data-stu-id="10c03-251">Click **Debug > Start without debugging**.</span></span>

### <a name="deploy-to-emulator"></a><span data-ttu-id="10c03-252">部署至模擬器</span><span class="sxs-lookup"><span data-stu-id="10c03-252">Deploy to Emulator</span></span>

1. <span data-ttu-id="10c03-253">按一下 [**裝置**] 按鈕旁邊的箭號，然後從下拉式選選取 [ **HoloLens 模擬器**]。</span><span class="sxs-lookup"><span data-stu-id="10c03-253">Click on the arrow next to the **Device** button, and from drop down select **HoloLens Emulator**.</span></span>
2. <span data-ttu-id="10c03-254">按一下 [ **Debug > 啟動但不進行調試**]。</span><span class="sxs-lookup"><span data-stu-id="10c03-254">Click **Debug > Start without debugging**.</span></span>

### <a name="try-out-your-app"></a><span data-ttu-id="10c03-255">試用您的應用程式</span><span class="sxs-lookup"><span data-stu-id="10c03-255">Try out your app</span></span>

<span data-ttu-id="10c03-256">現在您已部署您的應用程式，請嘗試在 cube 前後移動，並觀察它是否留在您的前方。</span><span class="sxs-lookup"><span data-stu-id="10c03-256">Now that your app is deployed, try moving all around the cube and observe that it stays in the world in front of you.</span></span>

## <a name="see-also"></a><span data-ttu-id="10c03-257">請參閱</span><span class="sxs-lookup"><span data-stu-id="10c03-257">See also</span></span>

* [<span data-ttu-id="10c03-258">Unity 開發概觀</span><span class="sxs-lookup"><span data-stu-id="10c03-258">Unity development overview</span></span>](unity-development-overview.md)
* [<span data-ttu-id="10c03-259">使用 Unity 和 Visual Studio 的最佳作法</span><span class="sxs-lookup"><span data-stu-id="10c03-259">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="10c03-260">MR 基本101</span><span class="sxs-lookup"><span data-stu-id="10c03-260">MR Basics 101</span></span>](holograms-101.md)
* [<span data-ttu-id="10c03-261">MR 基本概念101E</span><span class="sxs-lookup"><span data-stu-id="10c03-261">MR Basics 101E</span></span>](holograms-101e.md)
