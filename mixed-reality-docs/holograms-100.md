---
title: MR 基本概念 100-開始使用 Unity
description: 瞭解如何建立您的第一個基本混合現實 "hello world" 應用程式。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: 混合現實，Windows Mixed Reality，HoloLens，沉浸，vr，mr，開始使用，全息影像，學院，教學課程
ms.openlocfilehash: 58a1785ef74872c633cf65d6a32e24d517367359
ms.sourcegitcommit: f523b74a549721b6bec69cb5d2eca5b7673a793c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85570311"
---
# <a name="mr-basics-100-getting-started-with-unity"></a><span data-ttu-id="f7320-104">MR Basics 100：開始使用 Unity</span><span class="sxs-lookup"><span data-stu-id="f7320-104">MR Basics 100: Getting started with Unity</span></span>

>[!IMPORTANT]
><span data-ttu-id="f7320-105">混合實境學院教學課程的設計是以 HoloLens (第 1 代) 和混合實境沉浸式頭戴裝置為準。</span><span class="sxs-lookup"><span data-stu-id="f7320-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="f7320-106">因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。</span><span class="sxs-lookup"><span data-stu-id="f7320-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="f7320-107">這些教學課程**_不會_** 使用用於 HoloLens 2 的最新工具組或互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="f7320-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="f7320-108">系統會保留這些資訊，以繼續在支援的裝置上運作。</span><span class="sxs-lookup"><span data-stu-id="f7320-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="f7320-109">已針對 HoloLens 2 公佈[一系列新的教學課程](mrlearning-base.md)。</span><span class="sxs-lookup"><span data-stu-id="f7320-109">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<span data-ttu-id="f7320-110">本教學課程將逐步引導您建立以 Unity 建立的基本混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="f7320-110">This tutorial will walk you through creating a basic mixed reality app built with Unity.</span></span>

## <a name="device-support"></a><span data-ttu-id="f7320-111">裝置支援</span><span class="sxs-lookup"><span data-stu-id="f7320-111">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="f7320-112">課程</span><span class="sxs-lookup"><span data-stu-id="f7320-112">Course</span></span></th><th style="width:150px"> <span data-ttu-id="f7320-113"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f7320-113"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f7320-114"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="f7320-114"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="f7320-115">MR Basics 100：開始使用 Unity</span><span class="sxs-lookup"><span data-stu-id="f7320-115">MR Basics 100: Getting started with Unity</span></span></td><td style="text-align: center;"> <span data-ttu-id="f7320-116">✔️</span><span class="sxs-lookup"><span data-stu-id="f7320-116">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="f7320-117">✔️</span><span class="sxs-lookup"><span data-stu-id="f7320-117">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="f7320-118">必要條件</span><span class="sxs-lookup"><span data-stu-id="f7320-118">Prerequisites</span></span>

* <span data-ttu-id="f7320-119">[已安裝正確工具](install-the-tools.md)的 WINDOWS 10 電腦。</span><span class="sxs-lookup"><span data-stu-id="f7320-119">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

## <a name="chapter-1---create-a-new-project"></a><span data-ttu-id="f7320-120">第1章-建立新專案</span><span class="sxs-lookup"><span data-stu-id="f7320-120">Chapter 1 - Create a New Project</span></span>

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

<span data-ttu-id="f7320-121">若要使用 Unity 來建立應用程式，您必須先建立專案。</span><span class="sxs-lookup"><span data-stu-id="f7320-121">To build an app with Unity, you first need to create a project.</span></span> <span data-ttu-id="f7320-122">此專案會組織成幾個資料夾，其中最重要的是您的資產資料夾。</span><span class="sxs-lookup"><span data-stu-id="f7320-122">This project is organized into a few folders, the most important of which is your Assets folder.</span></span> <span data-ttu-id="f7320-123">此資料夾會保存您從數位內容建立工具（例如 Maya、最大電影院4D 或 Photoshop）匯入的所有資產、您使用 Visual Studio 或慣用的程式碼編輯器建立的所有程式碼，以及 Unity 在您撰寫場景、動畫及編輯器中的其他 Unity 資產類型時所建立的任何內容檔案數目。</span><span class="sxs-lookup"><span data-stu-id="f7320-123">This is the folder that holds all assets you import from digital content creation tools such as Maya, Max Cinema 4D or Photoshop, all code you create with Visual Studio or your favorite code editor, and any number of content files that Unity creates as you compose scenes, animations and other Unity asset types in the editor.</span></span>

<span data-ttu-id="f7320-124">若要建立和部署 UWP 應用程式，Unity 可以將專案匯出為 Visual Studio 方案，其中包含所有必要的資產和程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="f7320-124">To build and deploy UWP apps, Unity can export the project as a Visual Studio solution that will contain all necessary asset and code files.</span></span>

1. <span data-ttu-id="f7320-125">啟動 Unity</span><span class="sxs-lookup"><span data-stu-id="f7320-125">Start Unity</span></span>
2. <span data-ttu-id="f7320-126">選取 [**新增**]</span><span class="sxs-lookup"><span data-stu-id="f7320-126">Select **New**</span></span>
3. <span data-ttu-id="f7320-127">輸入專案名稱（例如 "MixedRealityIntroduction"）</span><span class="sxs-lookup"><span data-stu-id="f7320-127">Enter a project name (e.g. "MixedRealityIntroduction")</span></span>
4. <span data-ttu-id="f7320-128">輸入儲存專案的位置</span><span class="sxs-lookup"><span data-stu-id="f7320-128">Enter a location to save your project</span></span>
5. <span data-ttu-id="f7320-129">確定已選取**3d**切換</span><span class="sxs-lookup"><span data-stu-id="f7320-129">Ensure the **3D** toggle is selected</span></span>
6. <span data-ttu-id="f7320-130">選取 [**建立專案**]</span><span class="sxs-lookup"><span data-stu-id="f7320-130">Select **Create project**</span></span>

<span data-ttu-id="f7320-131">恭喜，您可以立即開始進行混合現實的自訂。</span><span class="sxs-lookup"><span data-stu-id="f7320-131">Congrats, you are all setup to get started with your mixed reality customizations now.</span></span>

## <a name="chapter-2---setup-the-camera"></a><span data-ttu-id="f7320-132">第2章-設定相機</span><span class="sxs-lookup"><span data-stu-id="f7320-132">Chapter 2 - Setup the Camera</span></span>

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

<span data-ttu-id="f7320-133">Unity 主要攝影機會處理 head 追蹤和 stereoscopic 轉譯。</span><span class="sxs-lookup"><span data-stu-id="f7320-133">The Unity Main Camera handles head tracking and stereoscopic rendering.</span></span> <span data-ttu-id="f7320-134">主要相機有幾個變更可用於混合現實。</span><span class="sxs-lookup"><span data-stu-id="f7320-134">There are a few changes to make to the Main Camera to use it with mixed reality.</span></span>

1. <span data-ttu-id="f7320-135">選取檔案 > 新場景</span><span class="sxs-lookup"><span data-stu-id="f7320-135">Select File > New Scene</span></span>

<span data-ttu-id="f7320-136">首先，如果您認為使用者的開始位置是（**X**：0， **Y**：0， **Z**：0），則可以更輕鬆地配置應用程式。</span><span class="sxs-lookup"><span data-stu-id="f7320-136">First, it will be easier to lay out your app if you imagine the starting position of the user as (**X**: 0, **Y**: 0, **Z**: 0).</span></span> <span data-ttu-id="f7320-137">由於主要攝影機是追蹤使用者頭部的移動，因此可以藉由設定主要攝影機的開始位置來設定使用者的開始位置。</span><span class="sxs-lookup"><span data-stu-id="f7320-137">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>

1. <span data-ttu-id="f7320-138">**在 [階層**] 面板中選取**主要相機**</span><span class="sxs-lookup"><span data-stu-id="f7320-138">Select **Main Camera** in the **Hierarchy** panel</span></span>
2. <span data-ttu-id="f7320-139">在 [偵測**器**] 面板中，尋找 [**轉換**] 元件，並將**位置**從（**x**：0， **y**：1， **z**：-10）變更為（**x**：0， **y**：0， **Z**：0）</span><span class="sxs-lookup"><span data-stu-id="f7320-139">In the **Inspector** panel, find the **Transform** component and change the **Position** from (**X**: 0, **Y**: 1, **Z**: -10) to (**X**: 0, **Y**: 0, **Z**: 0)</span></span>

<span data-ttu-id="f7320-140">第二，預設的相機背景需要一些思考。</span><span class="sxs-lookup"><span data-stu-id="f7320-140">Second, the default Camera background needs some thought.</span></span>

<span data-ttu-id="f7320-141">若是**HoloLens 應用程式**，真實世界應該會出現在相機呈現的所有內容後方，而不是 Skybox 材質。</span><span class="sxs-lookup"><span data-stu-id="f7320-141">**For HoloLens applications**, the real world should appear behind everything the camera renders, not a Skybox texture.</span></span>

1. <span data-ttu-id="f7320-142">在 [階層] 面板中仍然選取**主要相機**後，**在 [偵測\*\*\*\*器**] 面板中尋找**相機**元件，並將 [**清除旗標**] 下拉式清單從**Skybox**變更為**純色**。</span><span class="sxs-lookup"><span data-stu-id="f7320-142">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Clear Flags** dropdown from **Skybox** to **Solid Color**.</span></span>
2. <span data-ttu-id="f7320-143">選取**背景**色彩選擇器，並將**RGBA**值變更為（0，0，0，0）</span><span class="sxs-lookup"><span data-stu-id="f7320-143">Select the **Background** color picker and change the **RGBA** values to (0, 0, 0, 0)</span></span>

<span data-ttu-id="f7320-144">**對於以沉浸式耳機為目標的混合現實應用程式**，我們可以使用 Unity 提供的預設 Skybox 材質。</span><span class="sxs-lookup"><span data-stu-id="f7320-144">**For mixed reality applications targeted to immersive headsets**, we can use the default Skybox texture that Unity provides.</span></span>

1. <span data-ttu-id="f7320-145">**在 [階層] 面板中**，仍然選取**主要相機**，請在 [偵測**器**] 面板中尋找**相機**元件，並將 [**清除旗標**] 下拉式清單保留為**Skybox**。</span><span class="sxs-lookup"><span data-stu-id="f7320-145">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Clear Flags** dropdown to **Skybox**.</span></span>

<span data-ttu-id="f7320-146">第三，讓我們考慮 Unity 中附近的裁剪平面，防止物件在使用者接近物件或物件接近使用者的情況下，呈現太接近使用者的眼睛。</span><span class="sxs-lookup"><span data-stu-id="f7320-146">Third, let us consider the near clip plane in Unity and prevent objects from being rendered too close to the users eyes as a user approaches an object or an object approaches a user.</span></span>

<span data-ttu-id="f7320-147">若是**hololens 應用程式**，接近的裁剪平面可以設定為[hololens 建議](camera-in-unity.md#clip-planes)的0.85 計量。</span><span class="sxs-lookup"><span data-stu-id="f7320-147">**For HoloLens applications**, the near clip plane can be set to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 meters.</span></span>

1. <span data-ttu-id="f7320-148">**在 [階層] 面板中**仍然選取**主要相機**時，請在 [偵測**器**] 面板中尋找**相機**元件，並將 [**接近剪切平面**] 欄位從預設**0.3**變更為 [HoloLens 建議**0.85**]。</span><span class="sxs-lookup"><span data-stu-id="f7320-148">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Near Clip Plane** field from the default **0.3** to the HoloLens recommended **0.85**.</span></span>

<span data-ttu-id="f7320-149">**對於以沉浸式耳機為目標的混合現實應用程式**，我們可以使用 Unity 提供的預設設定。</span><span class="sxs-lookup"><span data-stu-id="f7320-149">**For mixed reality applications targeted to immersive headsets**, we can use the default setting that Unity provides.</span></span>

1. <span data-ttu-id="f7320-150">**在 [階層] 面板中**仍然選取**主要相機**時，請在 [偵測**器**] 面板中尋找**相機**元件，並將 [**近端剪切平面**] 欄位保留為預設值**0.3**。</span><span class="sxs-lookup"><span data-stu-id="f7320-150">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Near Clip Plane** field to the default **0.3**.</span></span>

<span data-ttu-id="f7320-151">最後，讓我們來儲存我們目前的進度。</span><span class="sxs-lookup"><span data-stu-id="f7320-151">Finally, let us save our progress so far.</span></span> <span data-ttu-id="f7320-152">若要儲存場景變更，請選取 [檔案] **> 另存場景**]，將場景命名為**Main**，然後選取 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="f7320-152">To save the scene changes, select **File > Save Scene As**, name the scene **Main**, and select **Save**.</span></span>

## <a name="chapter-3---setup-the-project-settings"></a><span data-ttu-id="f7320-153">第3章-設定專案設定</span><span class="sxs-lookup"><span data-stu-id="f7320-153">Chapter 3 - Setup the Project Settings</span></span>

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

<span data-ttu-id="f7320-154">在本章中，我們將設定一些 Unity 專案設定，以協助我們以 Windows 全像開發 SDK 為目標。</span><span class="sxs-lookup"><span data-stu-id="f7320-154">In this chapter, we will set some Unity project settings that help us target the Windows Holographic SDK for development.</span></span> <span data-ttu-id="f7320-155">我們也會為應用程式設定一些品質設定。</span><span class="sxs-lookup"><span data-stu-id="f7320-155">We will also set some quality settings for our application.</span></span> <span data-ttu-id="f7320-156">最後，我們會確保組建目標設定為通用 Windows 平臺。</span><span class="sxs-lookup"><span data-stu-id="f7320-156">Finally, we will ensure our build targets are set to Universal Windows Platform.</span></span>

### <a name="unity-performance-and-quality-settings"></a><span data-ttu-id="f7320-157">Unity 效能和品質設定</span><span class="sxs-lookup"><span data-stu-id="f7320-157">Unity performance and quality settings</span></span>

<span data-ttu-id="f7320-158">**HoloLens 的 Unity 品質設定**</span><span class="sxs-lookup"><span data-stu-id="f7320-158">**Unity quality settings for HoloLens**</span></span>

![HoloLens 的 Unity 品質設定](images/qualitysettings.png)

<span data-ttu-id="f7320-160">因為在 HoloLens 上維持高畫面播放速率相當重要，所以我們想要調整品質設定以取得最快的效能。</span><span class="sxs-lookup"><span data-stu-id="f7320-160">Since maintaining high framerate on HoloLens is so important, we want the quality settings tuned for fastest performance.</span></span> <span data-ttu-id="f7320-161">如需更詳細的效能資訊，請[查看 Unity 的效能建議](performance-recommendations-for-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="f7320-161">For more detailed performance information, [Performance recommendations for Unity](performance-recommendations-for-unity.md).</span></span>

1. <span data-ttu-id="f7320-162">選取 [**編輯] > 專案設定 > 品質**</span><span class="sxs-lookup"><span data-stu-id="f7320-162">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="f7320-163">選取 [**通用 Windows 平臺**標誌底下的**下拉式清單**，然後選取 [**非常低**]。</span><span class="sxs-lookup"><span data-stu-id="f7320-163">Select the **dropdown** under the **Universal Windows Platform** logo and select **Very Low**.</span></span> <span data-ttu-id="f7320-164">當 [通用 Windows 平臺] 資料行中的方塊和**非常低**的資料列都是綠色時，您會知道設定已正確套用。</span><span class="sxs-lookup"><span data-stu-id="f7320-164">You'll know the setting is applied correctly when the box in the Universal Windows Platform column and **Very Low** row is green.</span></span>

<span data-ttu-id="f7320-165">**針對以 pixels occluded 為目標的混合現實應用程式**，您可以將品質設定保留為預設值。</span><span class="sxs-lookup"><span data-stu-id="f7320-165">**For mixed reality applications targeted to occluded displays**, you can leave the quality settings to its default values.</span></span>

### <a name="target-windows-10-sdk"></a><span data-ttu-id="f7320-166">以 Windows 10 SDK 為目標</span><span class="sxs-lookup"><span data-stu-id="f7320-166">Target Windows 10 SDK</span></span>

<span data-ttu-id="f7320-167">**以 Windows 全像的 SDK 為目標**</span><span class="sxs-lookup"><span data-stu-id="f7320-167">**Target Windows Holographic SDK**</span></span>

![以 Windows 全像的 SDK 為目標](images/xrsettings.png)

<span data-ttu-id="f7320-169">我們需要讓 Unity 知道，我們嘗試匯出的應用程式應該建立[沉浸式視圖](app-views.md)，而不是2d 視圖。</span><span class="sxs-lookup"><span data-stu-id="f7320-169">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="f7320-170">我們的作法是在以 Windows 10 SDK 為目標的 Unity 上啟用虛擬實境支援。</span><span class="sxs-lookup"><span data-stu-id="f7320-170">We do this by enabling Virtual Reality support on Unity targeting the Windows 10 SDK.</span></span>

1. <span data-ttu-id="f7320-171">移至 [**編輯] > 專案設定 > Player**]。</span><span class="sxs-lookup"><span data-stu-id="f7320-171">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="f7320-172">在 [玩家設定] 的 [偵測**器] 面板**中，選取 [**通用 Windows 平臺**] 圖示。</span><span class="sxs-lookup"><span data-stu-id="f7320-172">In the **Inspector Panel** for Player Settings, select the **Universal Windows Platform** icon.</span></span>
3. <span data-ttu-id="f7320-173">展開 [XR 設定] 群組。</span><span class="sxs-lookup"><span data-stu-id="f7320-173">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="f7320-174">**在轉譯區段中**，勾選 [**支援虛擬實境**] 核取方塊，以新增**虛擬實境 sdk**清單。</span><span class="sxs-lookup"><span data-stu-id="f7320-174">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="f7320-175">確認 **Windows Mixed Reality** 出現在清單中。</span><span class="sxs-lookup"><span data-stu-id="f7320-175">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="f7320-176">如果沒有，請選取清單底部的 **+** 按鈕，然後選擇 [Windows Mixed Reality]。</span><span class="sxs-lookup"><span data-stu-id="f7320-176">If not, select the **+** button at the bottom of the list and choose **Windows Mixed Reality**.</span></span>

>[!NOTE]
><span data-ttu-id="f7320-177">如果您看不到 [**通用 Windows 平臺**] 圖示，請再次檢查以確定您在安裝期間已選取 [通用 Windows 平臺組建支援]。</span><span class="sxs-lookup"><span data-stu-id="f7320-177">If you do not see the **Universal Windows Platform** icon, double check to make sure you selected Universal Windows Platform Build Support during installation.</span></span> <span data-ttu-id="f7320-178">如果沒有，您可能需要以正確的 Windows 安裝重新安裝 Unity。</span><span class="sxs-lookup"><span data-stu-id="f7320-178">If not, you may need to reinstall Unity with the correct Windows installation.</span></span>

<span data-ttu-id="f7320-179">取得套用所有專案設定的絕佳作業。</span><span class="sxs-lookup"><span data-stu-id="f7320-179">Awesome job on getting all the project settings applied.</span></span> <span data-ttu-id="f7320-180">接下來，讓我們新增全息影像！</span><span class="sxs-lookup"><span data-stu-id="f7320-180">Next, let us add a hologram!</span></span>

## <a name="chapter-4---create-a-cube"></a><span data-ttu-id="f7320-181">第4章-建立 cube</span><span class="sxs-lookup"><span data-stu-id="f7320-181">Chapter 4 - Create a cube</span></span>

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

<span data-ttu-id="f7320-182">在 Unity 專案中建立 cube，就像在 Unity 中建立任何其他物件一樣。</span><span class="sxs-lookup"><span data-stu-id="f7320-182">Creating a cube in your Unity project is just like creating any other object in Unity.</span></span> <span data-ttu-id="f7320-183">將 cube 放在使用者的前方很容易，因為 Unity 的座標系統會對應到真實世界-其中 Unity 中的一個計量是真實世界中的一個計量。</span><span class="sxs-lookup"><span data-stu-id="f7320-183">Placing a cube in front of the user is easy because Unity's coordinate system is mapped to the real world - where one meter in Unity is approximately one meter in the real world.</span></span>

1. <span data-ttu-id="f7320-184">**在 [階層] 面板的**左上角，選取 [**建立**] 下拉式清單，然後選擇 [ **3d 物件 > Cube**]。</span><span class="sxs-lookup"><span data-stu-id="f7320-184">In the top left corner of the **Hierarchy** panel, select the **Create** dropdown and choose **3D Object > Cube**.</span></span>
2. <span data-ttu-id="f7320-185">在 [階層 **] 面板中**選取新建立的**Cube**</span><span class="sxs-lookup"><span data-stu-id="f7320-185">Select the newly created **Cube** in the **Hierarchy** panel</span></span>
3. <span data-ttu-id="f7320-186">在偵測**器**中，尋找 [**轉換**] 元件，並將 [**位置**] 變更為（**X**：0， **Y**：0， **Z**：2）。</span><span class="sxs-lookup"><span data-stu-id="f7320-186">In the **Inspector** find the **Transform** component and change **Position** to (**X**: 0, **Y**: 0, **Z**: 2).</span></span> <span data-ttu-id="f7320-187">*這會將 cube 2 計量置於使用者開始位置的前方。*</span><span class="sxs-lookup"><span data-stu-id="f7320-187">*This positions the cube 2 meters in front of the user's starting position.*</span></span>
4. <span data-ttu-id="f7320-188">在 [**轉換**] 元件中，將 [**旋轉**] 變更為（**x**：45， **Y**：45， **Z**：45），並將 [**調整**為] （**x**：0.25， **Y**：0.25， **z**：0.25）。</span><span class="sxs-lookup"><span data-stu-id="f7320-188">In the **Transform** component, change **Rotation** to (**X**: 45, **Y**: 45, **Z**: 45) and change **Scale** to (**X**: 0.25, **Y**: 0.25, **Z**: 0.25).</span></span> <span data-ttu-id="f7320-189">*這會將 cube 調整為0.25 計量。*</span><span class="sxs-lookup"><span data-stu-id="f7320-189">*This scales the cube to 0.25 meters.*</span></span>
5. <span data-ttu-id="f7320-190">若要儲存場景變更，請選取 [檔案] **> 儲存場景**]。</span><span class="sxs-lookup"><span data-stu-id="f7320-190">To save the scene changes, select **File > Save Scene**.</span></span>

## <a name="chapter-5---verify-on-device-from-unity-editor"></a><span data-ttu-id="f7320-191">第5章-從 Unity 編輯器進行裝置驗證</span><span class="sxs-lookup"><span data-stu-id="f7320-191">Chapter 5 - Verify on device from Unity editor</span></span>

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

<span data-ttu-id="f7320-192">既然我們已經建立 cube，就可以開始快速檢查裝置。</span><span class="sxs-lookup"><span data-stu-id="f7320-192">Now that we have created our cube, it is time to do a quick check in device.</span></span> <span data-ttu-id="f7320-193">您可以直接從 Unity 編輯器中執行此動作。</span><span class="sxs-lookup"><span data-stu-id="f7320-193">You can do this directly from within the Unity editor.</span></span>

### <a name="initial-setup"></a><span data-ttu-id="f7320-194">初始設定</span><span class="sxs-lookup"><span data-stu-id="f7320-194">Initial setup</span></span>

1. <span data-ttu-id="f7320-195">在開發電腦的 Unity 中，開啟 [檔案] **> [組建設定**] 視窗。</span><span class="sxs-lookup"><span data-stu-id="f7320-195">On your development PC, in Unity, open **File > Build Settings** window.</span></span>
2. <span data-ttu-id="f7320-196">將**平臺**變更為**通用 Windows 平臺**，然後按一下 [**切換平臺**]</span><span class="sxs-lookup"><span data-stu-id="f7320-196">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**</span></span>

### <a name="for-hololens-use-unity-remoting"></a><span data-ttu-id="f7320-197">若是 HoloLens，請使用 Unity Remoting</span><span class="sxs-lookup"><span data-stu-id="f7320-197">For HoloLens use Unity Remoting</span></span>

1. <span data-ttu-id="f7320-198">在您的 HoloLens 上，安裝並執行可從 Windows 市集中取得的全像攝影[遠端播放](holographic-remoting-player.md)程式。</span><span class="sxs-lookup"><span data-stu-id="f7320-198">On your HoloLens, install and run the [Holographic Remoting Player](holographic-remoting-player.md), available from the Windows Store.</span></span> <span data-ttu-id="f7320-199">在裝置上啟動應用程式，它會進入等候狀態，並顯示裝置的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="f7320-199">Launch the application on the device, and it will enter a waiting state and show the IP address of the device.</span></span> <span data-ttu-id="f7320-200">記下 IP。</span><span class="sxs-lookup"><span data-stu-id="f7320-200">Note down the IP.</span></span>
2. <span data-ttu-id="f7320-201">開啟**Window > XR >** 全像的模擬。</span><span class="sxs-lookup"><span data-stu-id="f7320-201">Open **Window > XR > Holographic Emulation**.</span></span>
3. <span data-ttu-id="f7320-202">將**模擬模式**從 [**無**] 變更為 [**遠端] 至 [裝置**]。</span><span class="sxs-lookup"><span data-stu-id="f7320-202">Change **Emulation Mode** from **None** to **Remote to Device**.</span></span>
4. <span data-ttu-id="f7320-203">在 [**遠端電腦**] 中，輸入您先前記下的 HOLOLENS 的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="f7320-203">In **Remote Machine**, enter the IP address of your HoloLens noted earlier.</span></span>
5. <span data-ttu-id="f7320-204">按一下 [ **連接**]。</span><span class="sxs-lookup"><span data-stu-id="f7320-204">Click **Connect**.</span></span>
6. <span data-ttu-id="f7320-205">確定 [**連接狀態**] 變更為 [綠色**已連接**]。</span><span class="sxs-lookup"><span data-stu-id="f7320-205">Ensure the **Connection Status** changes to green **Connected**.</span></span>
7. <span data-ttu-id="f7320-206">現在您可以按一下 Unity 編輯器中的 [**播放**]。</span><span class="sxs-lookup"><span data-stu-id="f7320-206">Now you can now click **Play** in the Unity editor.</span></span>

<span data-ttu-id="f7320-207">您現在將能夠在 [裝置] 和編輯器中看到 cube。</span><span class="sxs-lookup"><span data-stu-id="f7320-207">You will now be able to see the cube in device and in the editor.</span></span> <span data-ttu-id="f7320-208">就像在編輯器中執行應用程式一樣，您可以暫停、檢查物件和進行 debug，因為這基本上是發生的情況，但是會在主機電腦與裝置之間的網路上來回傳輸影片、音訊和裝置輸入。</span><span class="sxs-lookup"><span data-stu-id="f7320-208">You can pause, inspect objects, and debug just like you are running an app in the editor, because that's essentially what's happening, but with video, audio, and device input transmitted back and forth across the network between the host machine and the device.</span></span>

### <a name="for-other-mixed-reality-supported-headsets"></a><span data-ttu-id="f7320-209">適用于其他混合現實支援的耳機</span><span class="sxs-lookup"><span data-stu-id="f7320-209">For other mixed reality supported headsets</span></span>

1. <span data-ttu-id="f7320-210">使用 USB 纜線和 HDMI 或顯示器埠纜線，將耳機連接到您的開發電腦。</span><span class="sxs-lookup"><span data-stu-id="f7320-210">Connect the headset to your development PC using the USB cable and the HDMI or display port cable.</span></span>
2. <span data-ttu-id="f7320-211">啟動**混合現實入口網站**，並確定您已完成第一次執行體驗。</span><span class="sxs-lookup"><span data-stu-id="f7320-211">Launch the **Mixed Reality Portal** and ensure you have completed the first run experience.</span></span>
3. <span data-ttu-id="f7320-212">從 Unity，您現在可以按下 [播放] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f7320-212">From Unity, you can now press the Play button.</span></span>

<span data-ttu-id="f7320-213">您現在可以在混合現實頭戴式耳機和編輯器中看到 cube 呈現。</span><span class="sxs-lookup"><span data-stu-id="f7320-213">You will now be able to see the cube rendering in your mixed reality headset and in the editor.</span></span>

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a><span data-ttu-id="f7320-214">第6章-從 Visual Studio 建立及部署至裝置</span><span class="sxs-lookup"><span data-stu-id="f7320-214">Chapter 6 - Build and deploy to device from Visual Studio</span></span>

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

<span data-ttu-id="f7320-215">我們現在已準備好編譯專案，以 Visual Studio 並部署至目標裝置。</span><span class="sxs-lookup"><span data-stu-id="f7320-215">We are now ready to compile our project to Visual Studio and deploy to our target device.</span></span>

### <a name="export-to-the-visual-studio-solution"></a><span data-ttu-id="f7320-216">匯出至 Visual Studio 解決方案</span><span class="sxs-lookup"><span data-stu-id="f7320-216">Export to the Visual Studio solution</span></span>

1. <span data-ttu-id="f7320-217">開啟 [檔案] **> 組建設定**] 視窗。</span><span class="sxs-lookup"><span data-stu-id="f7320-217">Open **File > Build Settings** window.</span></span>
1. <span data-ttu-id="f7320-218">按一下 [新增] [**開啟場景**] 以加入場景。</span><span class="sxs-lookup"><span data-stu-id="f7320-218">Click **Add Open Scenes** to add the scene.</span></span>
1. <span data-ttu-id="f7320-219">將**平臺**變更為**通用 Windows 平臺**，然後按一下 [**切換平臺**]。</span><span class="sxs-lookup"><span data-stu-id="f7320-219">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**.</span></span>
1. <span data-ttu-id="f7320-220">在**通用 Windows 平臺**設定中，請確定**SDK**是**通用 10**。</span><span class="sxs-lookup"><span data-stu-id="f7320-220">In **Universal Windows Platform** settings, ensure **SDK** is **Universal 10**.</span></span>
1. <span data-ttu-id="f7320-221">針對 [目標裝置]，保留 [**任何裝置**以進行 pixels occluded] 或 [切換至**HoloLens**]。</span><span class="sxs-lookup"><span data-stu-id="f7320-221">For Target device, leave to **Any Device** for occluded displays or switch to **HoloLens**.</span></span>
1. <span data-ttu-id="f7320-222">**UWP 組建類型**應該是**D3D**。</span><span class="sxs-lookup"><span data-stu-id="f7320-222">**UWP Build Type** should be **D3D**.</span></span>
1. <span data-ttu-id="f7320-223">**UWP SDK**可以保持在**最新的安裝**位置。</span><span class="sxs-lookup"><span data-stu-id="f7320-223">**UWP SDK** could be left at **Latest installed**.</span></span>
1. <span data-ttu-id="f7320-224">按一下 [建置]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f7320-224">Click **Build**.</span></span>
1. <span data-ttu-id="f7320-225">在 [檔案瀏覽器] 中，按一下 [**新增資料夾**]，並將資料夾命名為「**應用程式**」。</span><span class="sxs-lookup"><span data-stu-id="f7320-225">In the file explorer, click **New Folder** and name the folder **"App"**.</span></span>
1. <span data-ttu-id="f7320-226">選取**應用程式**資料夾後，按一下 [**選取資料夾**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f7320-226">With the **App** folder selected, click the **Select Folder** button.</span></span>
1. <span data-ttu-id="f7320-227">Unity 完成建立時，將會出現 Windows 檔案瀏覽器視窗。</span><span class="sxs-lookup"><span data-stu-id="f7320-227">When Unity is done building, a Windows File Explorer window will appear.</span></span>
1. <span data-ttu-id="f7320-228">在檔案瀏覽器中開啟**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="f7320-228">Open the **App** folder in file explorer.</span></span>
1. <span data-ttu-id="f7320-229">開啟產生的 Visual Studio 方案（在此範例中為 MixedRealityIntroduction）</span><span class="sxs-lookup"><span data-stu-id="f7320-229">Open the generated Visual Studio solution (MixedRealityIntroduction.sln in this example)</span></span>

### <a name="compile-the-visual-studio-solution"></a><span data-ttu-id="f7320-230">編譯 Visual Studio 解決方案</span><span class="sxs-lookup"><span data-stu-id="f7320-230">Compile the Visual Studio solution</span></span>

<span data-ttu-id="f7320-231">最後，我們將編譯匯出的 Visual Studio 解決方案、部署它，然後在裝置上試試看。</span><span class="sxs-lookup"><span data-stu-id="f7320-231">Finally, we will compile the exported Visual Studio solution, deploy it, and try it out on the device.</span></span>

1. <span data-ttu-id="f7320-232">使用 Visual Studio 中的頂端工具列，將目標從 [**調試**] 變更為 [**發行**]，將 [從**ARM** ] 變更為**X86**。</span><span class="sxs-lookup"><span data-stu-id="f7320-232">Using the top toolbar in Visual Studio, change the target from **Debug** to **Release** and from **ARM** to **X86**.</span></span>

<span data-ttu-id="f7320-233">部署至裝置與模擬器的指示不同。</span><span class="sxs-lookup"><span data-stu-id="f7320-233">The instructions differ for deploying to a device versus the emulator.</span></span> <span data-ttu-id="f7320-234">遵循符合您設定的指示。</span><span class="sxs-lookup"><span data-stu-id="f7320-234">Follow the instructions that match your setup.</span></span>

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a><span data-ttu-id="f7320-235">透過 Wi-fi 部署到混合現實裝置</span><span class="sxs-lookup"><span data-stu-id="f7320-235">Deploy to mixed reality device over Wi-Fi</span></span>

1. <span data-ttu-id="f7320-236">按一下 [**本機電腦**] 按鈕旁的箭號，然後將部署目標變更為 [**遠端電腦**]。</span><span class="sxs-lookup"><span data-stu-id="f7320-236">Click on the arrow next to the **Local Machine** button, and change the deployment target to **Remote Machine**.</span></span>
2. <span data-ttu-id="f7320-237">輸入您 mixed reality 裝置的 IP 位址，並將其他裝置的 HoloLens 和**Windows**的**驗證模式**變更為通用（未加密的通訊協定）。</span><span class="sxs-lookup"><span data-stu-id="f7320-237">Enter the IP address of your mixed reality device and change **Authentication Mode** to Universal (Unencrypted Protocol) for HoloLens and **Windows** for other devices.</span></span>
3. <span data-ttu-id="f7320-238">按一下 [ **Debug > 啟動但不進行調試**]。</span><span class="sxs-lookup"><span data-stu-id="f7320-238">Click **Debug > Start without debugging**.</span></span>

<span data-ttu-id="f7320-239">若是**HoloLens**，如果這是您第一次部署至您的裝置，您將需要[使用 Visual Studio](using-visual-studio.md)配對。</span><span class="sxs-lookup"><span data-stu-id="f7320-239">**For HoloLens**, If this is the first time deploying to your device, you will need to pair [using Visual Studio](using-visual-studio.md).</span></span>

### <a name="deploy-to-mixed-reality-device-over-usb"></a><span data-ttu-id="f7320-240">透過 USB 部署到混合現實裝置</span><span class="sxs-lookup"><span data-stu-id="f7320-240">Deploy to mixed reality device over USB</span></span>

<span data-ttu-id="f7320-241">請確定您的裝置已透過 USB 纜線插入。</span><span class="sxs-lookup"><span data-stu-id="f7320-241">Ensure you device is plugged in via the USB cable.</span></span>

1. <span data-ttu-id="f7320-242">若是**HoloLens**，請按一下 [**本機電腦**] 按鈕旁的箭號，然後將部署目標變更為 [**裝置**]。</span><span class="sxs-lookup"><span data-stu-id="f7320-242">**For HoloLens**, click on the arrow next to the **Local Machine** button, and change the deployment target to **Device**.</span></span>
2. <span data-ttu-id="f7320-243">**針對連接到您電腦的 pixels occluded 裝置**，請將設定保留在 [本機電腦]。</span><span class="sxs-lookup"><span data-stu-id="f7320-243">**For targeting occluded devices attached to your PC**, keep the setting to Local Machine.</span></span> <span data-ttu-id="f7320-244">請確定您有執行中的**混合現實入口網站**。</span><span class="sxs-lookup"><span data-stu-id="f7320-244">Ensure you have the **Mixed Reality Portal** running.</span></span>
3. <span data-ttu-id="f7320-245">按一下 [ **Debug > 啟動但不進行調試**]。</span><span class="sxs-lookup"><span data-stu-id="f7320-245">Click **Debug > Start without debugging**.</span></span>

### <a name="deploy-to-emulator"></a><span data-ttu-id="f7320-246">部署至模擬器</span><span class="sxs-lookup"><span data-stu-id="f7320-246">Deploy to Emulator</span></span>

1. <span data-ttu-id="f7320-247">按一下 [**裝置**] 按鈕旁邊的箭號，然後從下拉式選選取 [ **HoloLens 模擬器**]。</span><span class="sxs-lookup"><span data-stu-id="f7320-247">Click on the arrow next to the **Device** button, and from drop down select **HoloLens Emulator**.</span></span>
2. <span data-ttu-id="f7320-248">按一下 [ **Debug > 啟動但不進行調試**]。</span><span class="sxs-lookup"><span data-stu-id="f7320-248">Click **Debug > Start without debugging**.</span></span>

### <a name="try-out-your-app"></a><span data-ttu-id="f7320-249">試用您的應用程式</span><span class="sxs-lookup"><span data-stu-id="f7320-249">Try out your app</span></span>

<span data-ttu-id="f7320-250">現在您已部署您的應用程式，請嘗試在 cube 前後移動，並觀察它是否留在您的前方。</span><span class="sxs-lookup"><span data-stu-id="f7320-250">Now that your app is deployed, try moving all around the cube and observe that it stays in the world in front of you.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7320-251">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7320-251">See also</span></span>

* [<span data-ttu-id="f7320-252">Unity 開發概觀</span><span class="sxs-lookup"><span data-stu-id="f7320-252">Unity development overview</span></span>](unity-development-overview.md)
* [<span data-ttu-id="f7320-253">使用 Unity 和 Visual Studio 的最佳作法</span><span class="sxs-lookup"><span data-stu-id="f7320-253">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="f7320-254">MR Basics 101</span><span class="sxs-lookup"><span data-stu-id="f7320-254">MR Basics 101</span></span>](holograms-101.md)
* [<span data-ttu-id="f7320-255">MR Basics 101E</span><span class="sxs-lookup"><span data-stu-id="f7320-255">MR Basics 101E</span></span>](holograms-101e.md)
