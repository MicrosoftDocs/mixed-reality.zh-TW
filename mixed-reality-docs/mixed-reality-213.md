---
title: MR 輸入 213
description: 遵循此程式碼撰寫的教學課程使用 Unity、 Visual Studio 和沈浸式耳機，若要了解動作控制器的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit，mixedrealitytoolkit，mixedrealitytoolkit-unity 沉浸式動作控制站、 academy、 教學課程
ms.openlocfilehash: 85449795a4fb3d182101cb5b4c4ce3fe85b009c0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596966"
---
>[!NOTE]
><span data-ttu-id="25759-104">混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。</span><span class="sxs-lookup"><span data-stu-id="25759-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="25759-105">因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。</span><span class="sxs-lookup"><span data-stu-id="25759-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="25759-106">這些教學課程會 **_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。</span><span class="sxs-lookup"><span data-stu-id="25759-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="25759-107">它們會繼續運作，支援的裝置上維護。</span><span class="sxs-lookup"><span data-stu-id="25759-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="25759-108">會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="25759-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="25759-109">當他們回傳時，本聲明將會更新這些教學課程的連結。</span><span class="sxs-lookup"><span data-stu-id="25759-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-input-213-motion-controllers"></a><span data-ttu-id="25759-110">MR 輸入 213:動作控制站</span><span class="sxs-lookup"><span data-stu-id="25759-110">MR Input 213: Motion controllers</span></span>

<span data-ttu-id="25759-111">混合的現實世界中的動作控制站加入互動性的另一個層級。</span><span class="sxs-lookup"><span data-stu-id="25759-111">Motion controllers in the mixed reality world add another level of interactivity.</span></span> <span data-ttu-id="25759-112">具有[動作控制器](motion-controllers.md)，我們可以直接將其與物件互動以更自然的方式類似於我們在現實生活中的實體互動中增加訓練活動，並在您的應用程式體驗會非常喜歡這樣。</span><span class="sxs-lookup"><span data-stu-id="25759-112">With [motion controllers](motion-controllers.md), we can directly interact with objects in a more natural way, similar to our physical interactions in real life, increasing immersion and delight in your app experience.</span></span>

<span data-ttu-id="25759-113">在 MR 輸入 213，我們將探討動作控制器的輸入的事件，藉由建立簡單的空間繪製體驗。</span><span class="sxs-lookup"><span data-stu-id="25759-113">In MR Input 213, we will explore the motion controller's input events by creating a simple spatial painting experience.</span></span> <span data-ttu-id="25759-114">與此應用程式，使用者可以在 3d 空間中，使用各種類型的筆刷和色彩繪製。</span><span class="sxs-lookup"><span data-stu-id="25759-114">With this app, users can paint in three-dimensional space with various types of brushes and colors.</span></span>

## <a name="topics-covered-in-this-tutorial"></a><span data-ttu-id="25759-115">在本教學課程所涵蓋的主題</span><span class="sxs-lookup"><span data-stu-id="25759-115">Topics covered in this tutorial</span></span>

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|<span data-ttu-id="25759-119">**控制器的視覺效果**</span><span class="sxs-lookup"><span data-stu-id="25759-119">**Controller visualization**</span></span>|<span data-ttu-id="25759-120">**控制站的輸入的事件**</span><span class="sxs-lookup"><span data-stu-id="25759-120">**Controller input events**</span></span>|<span data-ttu-id="25759-121">**自訂的控制器和 UI**</span><span class="sxs-lookup"><span data-stu-id="25759-121">**Custom controller and UI**</span></span>|
|<span data-ttu-id="25759-122">了解如何呈現在 Unity 的遊戲模式和執行階段的動作控制器模型。</span><span class="sxs-lookup"><span data-stu-id="25759-122">Learn how to render motion controller models in Unity's game mode and runtime.</span></span>|<span data-ttu-id="25759-123">了解不同類型的餂鈕瓿咘和他們的應用程式。</span><span class="sxs-lookup"><span data-stu-id="25759-123">Understand different types of button events and their applications.</span></span>|<span data-ttu-id="25759-124">了解如何覆疊在控制器上的 UI 項目，或完全加以自訂。</span><span class="sxs-lookup"><span data-stu-id="25759-124">Learn how to overlay UI elements on top of the controller or fully customize it.</span></span>|

## <a name="device-support"></a><span data-ttu-id="25759-125">裝置支援</span><span class="sxs-lookup"><span data-stu-id="25759-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="25759-126">課程</span><span class="sxs-lookup"><span data-stu-id="25759-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="25759-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="25759-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="25759-128"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="25759-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="25759-129">MR 輸入 213:動作控制站</span><span class="sxs-lookup"><span data-stu-id="25759-129">MR Input 213: Motion controllers</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="25759-130">✔️</span><span class="sxs-lookup"><span data-stu-id="25759-130">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="25759-131">開始之前</span><span class="sxs-lookup"><span data-stu-id="25759-131">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="25759-132">先決條件</span><span class="sxs-lookup"><span data-stu-id="25759-132">Prerequisites</span></span>

<span data-ttu-id="25759-133">請參閱安裝檢查清單的沈浸式耳機[本頁](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="25759-133">See the installation checklist for immersive headsets on [this page](install-the-tools.md).</span></span>

* <span data-ttu-id="25759-134">本教學課程需要[Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span><span class="sxs-lookup"><span data-stu-id="25759-134">This tutorial requires [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span></span>

### <a name="project-files"></a><span data-ttu-id="25759-135">專案檔</span><span class="sxs-lookup"><span data-stu-id="25759-135">Project files</span></span>

* <span data-ttu-id="25759-136">[將檔案下載](https://github.com/Microsoft/MixedReality213/archive/master.zip)需要專案，然後將檔案解壓縮至桌面。</span><span class="sxs-lookup"><span data-stu-id="25759-136">[Download the files](https://github.com/Microsoft/MixedReality213/archive/master.zip) required by the project and extract the files to the Desktop.</span></span>

>[!NOTE]
><span data-ttu-id="25759-137">如果您想要查看原始程式碼，在下載之前，它有[可在 GitHub 上](https://github.com/Microsoft/MixedReality213)。</span><span class="sxs-lookup"><span data-stu-id="25759-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/MixedReality213).</span></span>

## <a name="unity-setup"></a><span data-ttu-id="25759-138">Unity 安裝</span><span class="sxs-lookup"><span data-stu-id="25759-138">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a><span data-ttu-id="25759-139">目標</span><span class="sxs-lookup"><span data-stu-id="25759-139">Objectives</span></span>

* <span data-ttu-id="25759-140">最佳化 Unity for Windows Mixed Reality 開發</span><span class="sxs-lookup"><span data-stu-id="25759-140">Optimize Unity for Windows Mixed Reality development</span></span>
* <span data-ttu-id="25759-141">設定混合的實境相機</span><span class="sxs-lookup"><span data-stu-id="25759-141">Setup Mixed Reality Camera</span></span>
* <span data-ttu-id="25759-142">設定環境</span><span class="sxs-lookup"><span data-stu-id="25759-142">Setup environment</span></span>

### <a name="instructions"></a><span data-ttu-id="25759-143">指示</span><span class="sxs-lookup"><span data-stu-id="25759-143">Instructions</span></span>

* <span data-ttu-id="25759-144">啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="25759-144">Start Unity.</span></span>
* <span data-ttu-id="25759-145">選取 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="25759-145">Select **Open**.</span></span>
* <span data-ttu-id="25759-146">瀏覽至您的桌面及尋找**MixedReality213 master**先前未封存的資料夾。</span><span class="sxs-lookup"><span data-stu-id="25759-146">Navigate to your Desktop and find the **MixedReality213-master** folder you previously unarchived.</span></span>
* <span data-ttu-id="25759-147">按一下 [選擇資料夾]。</span><span class="sxs-lookup"><span data-stu-id="25759-147">Click **Select Folder**.</span></span>
* <span data-ttu-id="25759-148">Unity 完成載入專案檔案之後, 您將能夠看到 Unity 編輯器。</span><span class="sxs-lookup"><span data-stu-id="25759-148">Once Unity finishes loading project files, you will be able to see Unity editor.</span></span>
* <span data-ttu-id="25759-149">在 Unity 中，選取**檔案 > 組建設定**。</span><span class="sxs-lookup"><span data-stu-id="25759-149">In Unity, select **File > Build Settings**.</span></span>

![MR213_BuildSettings](images/mr213-buildsettings-450px.png)
* <span data-ttu-id="25759-151">選取 [**通用 Windows 平台**中**平台**清單，然後按一下**切換平台**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="25759-151">Select **Universal Windows Platform** in the **Platform** list and click the **Switch Platform** button.</span></span>
* <span data-ttu-id="25759-152">若要設定目標裝置**任何裝置**</span><span class="sxs-lookup"><span data-stu-id="25759-152">Set Target Device to **Any device**</span></span>
* <span data-ttu-id="25759-153">設定組建類型為**D3D**</span><span class="sxs-lookup"><span data-stu-id="25759-153">Set Build Type to **D3D**</span></span>
* <span data-ttu-id="25759-154">若要設定 SDK**最新安裝**</span><span class="sxs-lookup"><span data-stu-id="25759-154">Set SDK to **Latest Installed**</span></span>
* <span data-ttu-id="25759-155">請檢查**UnityC#專案**</span><span class="sxs-lookup"><span data-stu-id="25759-155">Check **Unity C# Projects**</span></span>
    * <span data-ttu-id="25759-156">這可讓您修改 Visual Studio 專案中的指令碼檔案，而不需重建 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="25759-156">This allows you modify script files in the Visual Studio project without rebuilding Unity project.</span></span>
* <span data-ttu-id="25759-157">按一下  **Player 設定**。</span><span class="sxs-lookup"><span data-stu-id="25759-157">Click **Player Settings**.</span></span>
* <span data-ttu-id="25759-158">在 [ **Inspector** ] 面板中，捲動到底部</span><span class="sxs-lookup"><span data-stu-id="25759-158">In the **Inspector** panel, scroll down to the bottom</span></span>
* <span data-ttu-id="25759-159">在 XR 設定中，檢查**虛擬實境支援**</span><span class="sxs-lookup"><span data-stu-id="25759-159">In XR Settings, check **Virtual Reality Supported**</span></span>
* <span data-ttu-id="25759-160">在 虛擬實境 Sdk 中，選取**Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="25759-160">Under Virtual Reality SDKs, select **Windows Mixed Reality**</span></span>

![MR213_XRSettings](images/mr213-xrsettings-500px.png)
* <span data-ttu-id="25759-162">關閉**組建設定**視窗。</span><span class="sxs-lookup"><span data-stu-id="25759-162">Close **Build Settings** window.</span></span>

### <a name="project-structure"></a><span data-ttu-id="25759-163">專案結構</span><span class="sxs-lookup"><span data-stu-id="25759-163">Project structure</span></span>

<span data-ttu-id="25759-164">本教學課程會使用 **[混合實境工具組-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 。</span><span class="sxs-lookup"><span data-stu-id="25759-164">This tutorial uses **[Mixed Reality Toolkit - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**.</span></span> <span data-ttu-id="25759-165">您可以找到這些發行版本[本頁](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)。</span><span class="sxs-lookup"><span data-stu-id="25759-165">You can find the releases on [this page](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span></span>

![ProjectStructure](images/mr213-projectstructure-650px.png)

<span data-ttu-id="25759-167">**已完成的場景，供您參考**</span><span class="sxs-lookup"><span data-stu-id="25759-167">**Completed scenes for your reference**</span></span>
* <span data-ttu-id="25759-168">您會發現兩個已完成下的 Unity 場景**場景**資料夾。</span><span class="sxs-lookup"><span data-stu-id="25759-168">You will find two completed Unity scenes under **Scenes** folder.</span></span>
    * <span data-ttu-id="25759-169">**MixedReality213**:已完成的場景，使用單一的筆刷</span><span class="sxs-lookup"><span data-stu-id="25759-169">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="25759-170">**MixedReality213Advanced**:完成進階的設計，含有多個筆刷的場景</span><span class="sxs-lookup"><span data-stu-id="25759-170">**MixedReality213Advanced**: Completed scene for advanced design with multiple brushes</span></span>

<span data-ttu-id="25759-171">**新的場景設定本教學課程**</span><span class="sxs-lookup"><span data-stu-id="25759-171">**New Scene setup for the tutorial**</span></span>
* <span data-ttu-id="25759-172">在 Unity 中，按一下 **檔案 > 新的場景**</span><span class="sxs-lookup"><span data-stu-id="25759-172">In Unity, click **File > New Scene**</span></span>
* <span data-ttu-id="25759-173">刪除**主攝影機**和**定向光線**</span><span class="sxs-lookup"><span data-stu-id="25759-173">Delete **Main Camera** and **Directional Light**</span></span>
* <span data-ttu-id="25759-174">從 **[專案] 面板**，搜尋並拖曳到下列 prefabs**階層**面板：</span><span class="sxs-lookup"><span data-stu-id="25759-174">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="25759-175">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="25759-175">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span></span>
    * <span data-ttu-id="25759-176">Assets/AppPrefabs/**Environment**</span><span class="sxs-lookup"><span data-stu-id="25759-176">Assets/AppPrefabs/**Environment**</span></span>

![相機和環境](images/mr213-cameraenvironment-300px.jpg)
* <span data-ttu-id="25759-178">有兩個混合實境工具組中的相機 prefabs:</span><span class="sxs-lookup"><span data-stu-id="25759-178">There are two camera prefabs in Mixed Reality Toolkit:</span></span>
    * <span data-ttu-id="25759-179">**MixedRealityCamera.prefab**:只有相機</span><span class="sxs-lookup"><span data-stu-id="25759-179">**MixedRealityCamera.prefab**: Camera only</span></span>
    * <span data-ttu-id="25759-180">**MixedRealityCameraParent.prefab**:相機屏障 + 界限</span><span class="sxs-lookup"><span data-stu-id="25759-180">**MixedRealityCameraParent.prefab**: Camera + Teleportation + Boundary</span></span>
    * <span data-ttu-id="25759-181">在本教學課程中，我們將使用**MixedRealityCamera**沒有空間傳送功能。</span><span class="sxs-lookup"><span data-stu-id="25759-181">In this tutorial, we will use **MixedRealityCamera** without teleportation feature.</span></span> <span data-ttu-id="25759-182">因為這個緣故，我們加入簡單**環境**prefab 其中包含讓使用者覺得腳踏實地的基本樓層。</span><span class="sxs-lookup"><span data-stu-id="25759-182">Because of this, we added simple **Environment** prefab which contains a basic floor to make the user feel grounded.</span></span>
    * <span data-ttu-id="25759-183">若要深入了解與屏障**MixedRealityCameraParent**，請參閱[進階設計-屏障和 locomotion](#advanced-design---teleportation-and-locomotion)</span><span class="sxs-lookup"><span data-stu-id="25759-183">To learn more about the teleportation with **MixedRealityCameraParent**, see [Advanced design - Teleportation and locomotion](#advanced-design---teleportation-and-locomotion)</span></span>

<span data-ttu-id="25759-184">**天空盒安裝程式**</span><span class="sxs-lookup"><span data-stu-id="25759-184">**Skybox setup**</span></span>
* <span data-ttu-id="25759-185">按一下 **視窗 > 光源 > 設定**</span><span class="sxs-lookup"><span data-stu-id="25759-185">Click **Window > Lighting > Settings**</span></span>
* <span data-ttu-id="25759-186">按一下右側的圓形**天空盒資料欄位**</span><span class="sxs-lookup"><span data-stu-id="25759-186">Click the circle on the right side of the **Skybox Material field**</span></span>
* <span data-ttu-id="25759-187">輸入 'gray'，然後選取  **SkyboxGray**</span><span class="sxs-lookup"><span data-stu-id="25759-187">Type in ‘gray’ and select **SkyboxGray**</span></span>

<span data-ttu-id="25759-188">(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span><span class="sxs-lookup"><span data-stu-id="25759-188">(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span></span>

![設定天空盒](images/mr123-skyboxsetting-400px.jpg)
* <span data-ttu-id="25759-190">請檢查**天空盒**選項，以查看指派灰色的漸層停駐天空盒</span><span class="sxs-lookup"><span data-stu-id="25759-190">Check **Skybox** option to be able to see assigned gray gradient skybox</span></span>

![切換天空盒選項](images/mr213-skyboxcheck-400px.jpg)
* <span data-ttu-id="25759-192">使用 MixedRealityCamera、 環境和灰色的天空盒場景會如下所示。</span><span class="sxs-lookup"><span data-stu-id="25759-192">The scene with MixedRealityCamera, Environment and gray skybox will look like this.</span></span>

![MixedReality213 環境](images/mr213-environment-600px.jpg)
* <span data-ttu-id="25759-194">按一下 **檔案 > 儲存為場景**</span><span class="sxs-lookup"><span data-stu-id="25759-194">Click **File > Save Scene as**</span></span>
* <span data-ttu-id="25759-195">**儲存**場景的任何名稱的資料夾下場景</span><span class="sxs-lookup"><span data-stu-id="25759-195">**Save** your scene under Scenes folder with any name</span></span>

## <a name="chapter-1---controller-visualization"></a><span data-ttu-id="25759-196">第 1 章-控制站的視覺效果</span><span class="sxs-lookup"><span data-stu-id="25759-196">Chapter 1 - Controller visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a><span data-ttu-id="25759-197">目標</span><span class="sxs-lookup"><span data-stu-id="25759-197">Objectives</span></span>

* <span data-ttu-id="25759-198">了解如何在 Unity 的遊戲模式，並在執行階段，控制器模型呈現動作。</span><span class="sxs-lookup"><span data-stu-id="25759-198">Learn how to render motion controller models in Unity's game mode and at runtime.</span></span>

<span data-ttu-id="25759-199">Windows Mixed Reality 提供動畫的控制器模型，以控制站的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="25759-199">Windows Mixed Reality provides an animated controller model for controller visualization.</span></span> <span data-ttu-id="25759-200">有數種方法，您可以在您的應用程式採取控制器視覺效果：</span><span class="sxs-lookup"><span data-stu-id="25759-200">There are several approaches you can take for controller visualization in your app:</span></span>
* <span data-ttu-id="25759-201">預設值-使用預設的控制站，而不需修改</span><span class="sxs-lookup"><span data-stu-id="25759-201">Default - Using default controller without modification</span></span>
* <span data-ttu-id="25759-202">混合式-使用預設的控制站，但自訂一些其項目或重疊 UI 元件</span><span class="sxs-lookup"><span data-stu-id="25759-202">Hybrid - Using default controller, but customizing some of its elements or overlaying UI components</span></span>
* <span data-ttu-id="25759-203">取代為使用您自己自訂的控制站的 3D 模型</span><span class="sxs-lookup"><span data-stu-id="25759-203">Replacement - Using your own customized 3D model for the controller</span></span>

<span data-ttu-id="25759-204">在本章中，我們將了解這些控制器自訂的範例。</span><span class="sxs-lookup"><span data-stu-id="25759-204">In this chapter, we will learn about the examples of these controller customizations.</span></span>

### <a name="instructions"></a><span data-ttu-id="25759-205">指示</span><span class="sxs-lookup"><span data-stu-id="25759-205">Instructions</span></span>

* <span data-ttu-id="25759-206">在 [**專案**] 面板中，鍵入**MotionControllers**在搜尋方塊中。</span><span class="sxs-lookup"><span data-stu-id="25759-206">In the **Project** panel, type **MotionControllers** in the search box .</span></span> <span data-ttu-id="25759-207">您也可以尋找其下的資產/HoloToolkit/輸入/Prefabs /。</span><span class="sxs-lookup"><span data-stu-id="25759-207">You can also find it under Assets/HoloToolkit/Input/Prefabs/.</span></span>
* <span data-ttu-id="25759-208">拖曳**MotionControllers**至 prefab**階層**面板。</span><span class="sxs-lookup"><span data-stu-id="25759-208">Drag the **MotionControllers** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="25759-209">按一下  **MotionControllers** prefab 中**階層**面板。</span><span class="sxs-lookup"><span data-stu-id="25759-209">Click on the **MotionControllers** prefab in the **Hierarchy** panel.</span></span>

<span data-ttu-id="25759-210">**MotionControllers prefab**</span><span class="sxs-lookup"><span data-stu-id="25759-210">**MotionControllers prefab**</span></span>

<span data-ttu-id="25759-211">**MotionControllers** prefab 已經**MotionControllerVisualizer**指令碼，其會提供替代的控制器模型中的位置。</span><span class="sxs-lookup"><span data-stu-id="25759-211">**MotionControllers** prefab has a **MotionControllerVisualizer** script which provides the slots for alternate controller models.</span></span> <span data-ttu-id="25759-212">如果您指派您自己自訂的 3D 模型，例如手形或拉鋸，並檢查 「 一律使用替代左/右模型 」，您會看到它們，而不是預設模型。</span><span class="sxs-lookup"><span data-stu-id="25759-212">If you assign your own custom 3D models such as a hand or a sword and check 'Always Use Alternate Left/Right Model', you will see them instead of the default model.</span></span> <span data-ttu-id="25759-213">我們將使用第 4 章中的這個位置來取代控制器模型使用筆刷。</span><span class="sxs-lookup"><span data-stu-id="25759-213">We will use this slot in Chapter 4 to replace the controller model with a brush.</span></span>

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

<span data-ttu-id="25759-215">**指示**</span><span class="sxs-lookup"><span data-stu-id="25759-215">**Instructions**</span></span>
* <span data-ttu-id="25759-216">在 [ **Inspector** ] 面板中，按兩下**MotionControllerVisualizer**若要查看 Visual Studio 中的程式碼的指令碼</span><span class="sxs-lookup"><span data-stu-id="25759-216">In the **Inspector** panel, double click **MotionControllerVisualizer** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="25759-217">**MotionControllerVisualizer script**</span><span class="sxs-lookup"><span data-stu-id="25759-217">**MotionControllerVisualizer script**</span></span>

<span data-ttu-id="25759-218">**MotionControllerVisualizer**並**MotionControllerInfo**類別提供方法來存取及修改的預設控制器模型。</span><span class="sxs-lookup"><span data-stu-id="25759-218">The **MotionControllerVisualizer** and **MotionControllerInfo** classes provide the means to access & modify the default controller models.</span></span> <span data-ttu-id="25759-219">**MotionControllerVisualizer**訂閱 Unity **InteractionSourceDetected**事件和自動會具現化控制器模型時找到它們。</span><span class="sxs-lookup"><span data-stu-id="25759-219">**MotionControllerVisualizer** subscribes to Unity's **InteractionSourceDetected** event and automatically instantiates controller models when they are found.</span></span>

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

<span data-ttu-id="25759-220">根據傳遞的控制器模型[glTF 規格](https://github.com/KhronosGroup/glTF)。</span><span class="sxs-lookup"><span data-stu-id="25759-220">The controller models are delivered according to [the glTF specification](https://github.com/KhronosGroup/glTF).</span></span> <span data-ttu-id="25759-221">已建立這種格式提供常見的格式，同時改善傳輸和解壓縮 3D 資產背後的程序。</span><span class="sxs-lookup"><span data-stu-id="25759-221">This format has been created to provide a common format, while improving the process behind transmitting and unpacking 3D assets.</span></span> <span data-ttu-id="25759-222">在此情況下，我們要擷取及載入控制器模型，在執行階段，我們想要讓使用者的體驗盡可能順暢地，而且它具有不保證動作控制器的哪一個版本的使用者可能會使用。</span><span class="sxs-lookup"><span data-stu-id="25759-222">In this case, we need to retrieve and load the controller models at runtime, as we want to make the user's experience as seamless as possible, and it's not guaranteed which version of the motion controllers the user might be using.</span></span> <span data-ttu-id="25759-223">本課程中的，混合實境工具組，透過使用 Khronos 群組的版本[UnityGLTF 專案](https://github.com/KhronosGroup/UnityGLTF)。</span><span class="sxs-lookup"><span data-stu-id="25759-223">This course, via the Mixed Reality Toolkit, uses a version of the Khronos Group's [UnityGLTF project](https://github.com/KhronosGroup/UnityGLTF).</span></span>

<span data-ttu-id="25759-224">一旦已傳遞控制站，可以使用指令碼**MotionControllerInfo**來尋找特定控制器的項目轉換，讓它們可以正確地定位本身。</span><span class="sxs-lookup"><span data-stu-id="25759-224">Once the controller has been delivered, scripts can use **MotionControllerInfo** to find the transforms for specific controller elements so they can correctly position themselves.</span></span>

<span data-ttu-id="25759-225">在稍後的章節中，我們將了解如何使用這些指令碼來將 UI 項目連結的控制站。</span><span class="sxs-lookup"><span data-stu-id="25759-225">In a later chapter, we will learn how to use these scripts to attach UI elements to the controllers.</span></span>

<span data-ttu-id="25759-226">*某些指令碼，在中，您會發現使用的程式碼區塊 **#if ！UNITY_EDITOR**或是**UNITY_WSA**。只在 UWP 執行階段上的事件，是當您將部署到 Windows 執行的這些程式碼區塊。這是因為不同的一組 Unity editor 和 UWP 應用程式執行階段所使用的 Api。*</span><span class="sxs-lookup"><span data-stu-id="25759-226">*In some scripts, you will find code blocks with **#if !UNITY_EDITOR** or **UNITY_WSA**. These code blocks run only on the UWP runtime when you deploy to Windows. This is because the set of APIs used by the Unity editor and the UWP app runtime are different.*</span></span>
* <span data-ttu-id="25759-227">**儲存**場景，然後按一下**播放** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="25759-227">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="25759-228">您會看到在場景中耳機的移動控制站。</span><span class="sxs-lookup"><span data-stu-id="25759-228">You will be able to see the scene with motion controllers in your headset.</span></span> <span data-ttu-id="25759-229">您可以看到詳細的動畫按鈕按下滑鼠、 搖桿移動和觸控板觸控反白顯示。</span><span class="sxs-lookup"><span data-stu-id="25759-229">You can see detailed animations for button clicks, thumbstick movement, and touchpad touch highlighting.</span></span>

![MR213_Controller 視覺效果預設](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a><span data-ttu-id="25759-231">第 2 章-附加到控制器的 UI 項目</span><span class="sxs-lookup"><span data-stu-id="25759-231">Chapter 2 - Attaching UI elements to the controller</span></span>

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a><span data-ttu-id="25759-232">目標</span><span class="sxs-lookup"><span data-stu-id="25759-232">Objectives</span></span>

* <span data-ttu-id="25759-233">深入了解動作控制器的項目</span><span class="sxs-lookup"><span data-stu-id="25759-233">Learn about the elements of the motion controllers</span></span>
* <span data-ttu-id="25759-234">了解如何將物件附加到特定的組件的控制站</span><span class="sxs-lookup"><span data-stu-id="25759-234">Learn how to attach objects to specific parts of the controllers</span></span>

<span data-ttu-id="25759-235">在本章中，您將學習如何將使用者介面項目新增至控制器的使用者可以輕鬆地存取和操作，是在任何時間。</span><span class="sxs-lookup"><span data-stu-id="25759-235">In this chapter, you will learn how to add user interface elements to the controller which the user can easily access and manipulate at anytime.</span></span> <span data-ttu-id="25759-236">您也將學習如何將新增簡單的色彩選擇器 UI 使用觸控輸入。</span><span class="sxs-lookup"><span data-stu-id="25759-236">You will also learn how to add a simple color picker UI using the touchpad input.</span></span>

### <a name="instructions"></a><span data-ttu-id="25759-237">指示</span><span class="sxs-lookup"><span data-stu-id="25759-237">Instructions</span></span>

* <span data-ttu-id="25759-238">在 [**專案**] 面板中，搜尋**MotionControllerInfo**指令碼。</span><span class="sxs-lookup"><span data-stu-id="25759-238">In the **Project** panel, search **MotionControllerInfo** script.</span></span>
* <span data-ttu-id="25759-239">在搜尋結果中，按兩下**MotionControllerInfo**若要查看 Visual Studio 中的程式碼的指令碼。</span><span class="sxs-lookup"><span data-stu-id="25759-239">From the search result, double click **MotionControllerInfo** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="25759-240">**MotionControllerInfo script**</span><span class="sxs-lookup"><span data-stu-id="25759-240">**MotionControllerInfo script**</span></span>

<span data-ttu-id="25759-241">第一個步驟是選擇您想要附加至 UI 的控制站的哪個項目。</span><span class="sxs-lookup"><span data-stu-id="25759-241">The first step is to choose which element of the controller you want the UI to attach to.</span></span> <span data-ttu-id="25759-242">這些項目會定義於**ControllerElementEnum**中**MotionControllerInfo.cs**。</span><span class="sxs-lookup"><span data-stu-id="25759-242">These elements are defined in **ControllerElementEnum** in **MotionControllerInfo.cs**.</span></span>

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)
* <span data-ttu-id="25759-244">**首頁**</span><span class="sxs-lookup"><span data-stu-id="25759-244">**Home**</span></span>
* <span data-ttu-id="25759-245">**功能表**</span><span class="sxs-lookup"><span data-stu-id="25759-245">**Menu**</span></span>
* <span data-ttu-id="25759-246">**Grasp**</span><span class="sxs-lookup"><span data-stu-id="25759-246">**Grasp**</span></span>
* <span data-ttu-id="25759-247">**搖桿**</span><span class="sxs-lookup"><span data-stu-id="25759-247">**Thumbstick**</span></span>
* <span data-ttu-id="25759-248">**Select**</span><span class="sxs-lookup"><span data-stu-id="25759-248">**Select**</span></span>
* <span data-ttu-id="25759-249">**觸控板**</span><span class="sxs-lookup"><span data-stu-id="25759-249">**Touchpad**</span></span>
* <span data-ttu-id="25759-250">**指標的姿勢**– 此項目代表指正向方向的控制站的提示。</span><span class="sxs-lookup"><span data-stu-id="25759-250">**Pointing pose** – this element represents the tip of the controller pointing forward direction.</span></span>

<span data-ttu-id="25759-251">**指示**</span><span class="sxs-lookup"><span data-stu-id="25759-251">**Instructions**</span></span>
* <span data-ttu-id="25759-252">在 [**專案**] 面板中，搜尋**AttachToController**指令碼。</span><span class="sxs-lookup"><span data-stu-id="25759-252">In the **Project** panel, search **AttachToController** script.</span></span>
* <span data-ttu-id="25759-253">在搜尋結果中，按兩下**AttachToController**若要查看 Visual Studio 中的程式碼的指令碼。</span><span class="sxs-lookup"><span data-stu-id="25759-253">From the search result, double click **AttachToController** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="25759-254">**AttachToController 指令碼**</span><span class="sxs-lookup"><span data-stu-id="25759-254">**AttachToController script**</span></span>

<span data-ttu-id="25759-255">**AttachToController**指令碼提供簡單的方式，將任何物件附加至指定的控制器法線慣用手和項目。</span><span class="sxs-lookup"><span data-stu-id="25759-255">The **AttachToController** script provides a simple way to attach any objects to a specified controller handedness and element.</span></span>

<span data-ttu-id="25759-256">In **AttachElementToController()**,</span><span class="sxs-lookup"><span data-stu-id="25759-256">In **AttachElementToController()**,</span></span>
* <span data-ttu-id="25759-257">檢查使用的法線慣用手的**MotionControllerInfo.Handedness**</span><span class="sxs-lookup"><span data-stu-id="25759-257">Check handedness using **MotionControllerInfo.Handedness**</span></span>
* <span data-ttu-id="25759-258">取得控制器使用的特定項目**MotionControllerInfo.TryGetElement()**</span><span class="sxs-lookup"><span data-stu-id="25759-258">Get specific element of the controller using **MotionControllerInfo.TryGetElement()**</span></span>
* <span data-ttu-id="25759-259">擷取的項目之後從控制器模型，而父系下它的物件轉換，並將物件的本機位置和旋轉設為零。</span><span class="sxs-lookup"><span data-stu-id="25759-259">After retrieving the element's transform from the controller model, parent the object under it and set object's local position & rotation to zero.</span></span>

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type " + element + " under controller " + newController.ControllerParent.name + "; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

<span data-ttu-id="25759-260">若要使用最簡單的方式**AttachToController**指令碼是從它繼承，如我們所做的情況**ColorPickerWheel。**</span><span class="sxs-lookup"><span data-stu-id="25759-260">The simplest way to use **AttachToController** script is to inherit from it, as we've done in the case of **ColorPickerWheel.**</span></span> <span data-ttu-id="25759-261">只是覆寫**OnAttachToController**並**OnDetatchFromController**函式來執行您的設定 / 細目時偵測到 / 中斷連接的控制器。</span><span class="sxs-lookup"><span data-stu-id="25759-261">Simply override the **OnAttachToController** and **OnDetatchFromController** functions to perform your setup / breakdown when the controller is detected / disconnected.</span></span>

<span data-ttu-id="25759-262">**指示**</span><span class="sxs-lookup"><span data-stu-id="25759-262">**Instructions**</span></span>
* <span data-ttu-id="25759-263">在 [**專案**] 面板中，在 [搜尋] 方塊中輸入**ColorPickerWheel**。</span><span class="sxs-lookup"><span data-stu-id="25759-263">In the **Project** panel, type in the search box **ColorPickerWheel**.</span></span> <span data-ttu-id="25759-264">您也可以尋找其下的資產/AppPrefabs /。</span><span class="sxs-lookup"><span data-stu-id="25759-264">You can also find it under Assets/AppPrefabs/.</span></span>
* <span data-ttu-id="25759-265">拖曳**ColorPickerWheel**至 prefab**階層**面板。</span><span class="sxs-lookup"><span data-stu-id="25759-265">Drag **ColorPickerWheel** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="25759-266">按一下  **ColorPickerWheel** prefab 中**階層**面板。</span><span class="sxs-lookup"><span data-stu-id="25759-266">Click the **ColorPickerWheel** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="25759-267">在 [ **Inspector** ] 面板中，按兩下**ColorPickerWheel**若要查看 Visual Studio 中的程式碼的指令碼。</span><span class="sxs-lookup"><span data-stu-id="25759-267">In the **Inspector** panel, double click **ColorPickerWheel** Script to see the code in Visual Studio.</span></span>

![ColorPickerWheel prefab](images/mr213-colorpickerwheel-1000px.jpg)

<span data-ttu-id="25759-269">**ColorPickerWheel 指令碼**</span><span class="sxs-lookup"><span data-stu-id="25759-269">**ColorPickerWheel script**</span></span>

<span data-ttu-id="25759-270">由於**ColorPickerWheel**繼承**AttachToController**，它會顯示**法線慣用手**並**項目**中**Inspector**面板。</span><span class="sxs-lookup"><span data-stu-id="25759-270">Since **ColorPickerWheel** inherits **AttachToController**, it shows **Handedness** and **Element** in the **Inspector** panel.</span></span> <span data-ttu-id="25759-271">我們將會將附加 UI 至左的控制站上的觸控板項目。</span><span class="sxs-lookup"><span data-stu-id="25759-271">We'll be attaching the UI to the Touchpad element on the left controller.</span></span>

![ColorPickerWheel 指令碼](images/mr213-attachtocontroller-300px.jpg)

<span data-ttu-id="25759-273">**ColorPickerWheel**會覆寫**OnAttachToController**並**OnDetatchFromController**訂閱將會用於下一步 一章中使用的色彩選取範圍之輸入事件觸控輸入。</span><span class="sxs-lookup"><span data-stu-id="25759-273">**ColorPickerWheel** overrides the **OnAttachToController** and **OnDetatchFromController** to subscribe to the input event which will be used in next chapter for color selection with touchpad input.</span></span>

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```
* <span data-ttu-id="25759-274">**儲存**場景，然後按一下**播放** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="25759-274">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="25759-275">**另一個方法來將物件附加至控制器**</span><span class="sxs-lookup"><span data-stu-id="25759-275">**Alternative method for attaching objects to the controllers**</span></span>

<span data-ttu-id="25759-276">我們建議您的指令碼繼承自**AttachToController** ，並覆寫**OnAttachToController**。</span><span class="sxs-lookup"><span data-stu-id="25759-276">We recommend that your scripts inherit from **AttachToController** and override **OnAttachToController**.</span></span> <span data-ttu-id="25759-277">不過，這不一定可行。</span><span class="sxs-lookup"><span data-stu-id="25759-277">However, this may not always be possible.</span></span> <span data-ttu-id="25759-278">替代方法使用它作為獨立元件。</span><span class="sxs-lookup"><span data-stu-id="25759-278">An alternative is using it as a standalone component.</span></span> <span data-ttu-id="25759-279">當您想要將現有的 prefab 連結到控制器，而不需要重構您的指令碼時，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="25759-279">This can be useful when you want to attach an existing prefab to a controller without refactoring your scripts.</span></span> <span data-ttu-id="25759-280">只需要等候 IsAttached 設為您的類別之前執行任何設定，則為 true。</span><span class="sxs-lookup"><span data-stu-id="25759-280">Simply have your class wait for IsAttached to be set to true before performing any setup.</span></span> <span data-ttu-id="25759-281">若要這樣做最簡單的方式是使用協同程式的 'Start'。</span><span class="sxs-lookup"><span data-stu-id="25759-281">The simplest way to do this is by using a coroutine for 'Start.'</span></span>

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a><span data-ttu-id="25759-282">第 3 章-使用觸控輸入</span><span class="sxs-lookup"><span data-stu-id="25759-282">Chapter 3 - Working with touchpad input</span></span>

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a><span data-ttu-id="25759-283">目標</span><span class="sxs-lookup"><span data-stu-id="25759-283">Objectives</span></span>

* <span data-ttu-id="25759-284">了解如何取得觸控輸入的資料事件</span><span class="sxs-lookup"><span data-stu-id="25759-284">Learn how to get touchpad input data events</span></span>
* <span data-ttu-id="25759-285">了解如何使用觸控板座標軸位置資訊，針對您的應用程式體驗</span><span class="sxs-lookup"><span data-stu-id="25759-285">Learn how to use touchpad axis position information for your app experience</span></span>

### <a name="instructions"></a><span data-ttu-id="25759-286">指示</span><span class="sxs-lookup"><span data-stu-id="25759-286">Instructions</span></span>

* <span data-ttu-id="25759-287">在 **階層** 面板中，按一下  **ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="25759-287">In the **Hierarchy** panel, click **ColorPickerWheel**</span></span>
* <span data-ttu-id="25759-288">在  **Inspector**  面板的  **Animatior**，按兩下  **ColorPickerWheelController**</span><span class="sxs-lookup"><span data-stu-id="25759-288">In the **Inspector** panel, under **Animatior**, double click **ColorPickerWheelController**</span></span>
* <span data-ttu-id="25759-289">您將能夠看到**動畫**開啟索引標籤</span><span class="sxs-lookup"><span data-stu-id="25759-289">You will be able to see **Animator** tab opened</span></span>

<span data-ttu-id="25759-290">**顯示/隱藏 UI 與 Unity 的動畫控制器**</span><span class="sxs-lookup"><span data-stu-id="25759-290">**Showing/hiding UI with Unity's Animation controller**</span></span>

<span data-ttu-id="25759-291">若要顯示和隱藏**ColorPickerWheel** UI 中的動畫，我們會使用[Unity 的動畫系統](https://docs.unity3d.com/Manual/AnimationOverview.html)。</span><span class="sxs-lookup"><span data-stu-id="25759-291">To show and hide the **ColorPickerWheel** UI with animation, we are using [Unity's animation system](https://docs.unity3d.com/Manual/AnimationOverview.html).</span></span> <span data-ttu-id="25759-292">設定**ColorPickerWheel**的**Visible**屬性設為 true 或 false 的觸發程序**顯示**並**隱藏**動畫觸發程序。</span><span class="sxs-lookup"><span data-stu-id="25759-292">Setting the **ColorPickerWheel**'s **Visible** property to true or false triggers **Show** and **Hide** animation triggers.</span></span> <span data-ttu-id="25759-293">**顯示**並**隱藏**中所定義的參數**ColorPickerWheelController**動畫控制器。</span><span class="sxs-lookup"><span data-stu-id="25759-293">**Show** and **Hide** parameters are defined in the **ColorPickerWheelController** animation controller.</span></span>

![Unity 動畫控制器](images/mr123-animationcontroller-550px.jpg)

<span data-ttu-id="25759-295">**指示**</span><span class="sxs-lookup"><span data-stu-id="25759-295">**Instructions**</span></span>
* <span data-ttu-id="25759-296">在 **階層**面板中，選取**ColorPickerWheel** prefab</span><span class="sxs-lookup"><span data-stu-id="25759-296">In the **Hierarchy** panel, select **ColorPickerWheel** prefab</span></span>
* <span data-ttu-id="25759-297">在 [ **Inspector** ] 面板中，按兩下**ColorPickerWheel**若要查看 Visual Studio 中的程式碼的指令碼</span><span class="sxs-lookup"><span data-stu-id="25759-297">In the **Inspector** panel, double click **ColorPickerWheel** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="25759-298">**ColorPickerWheel 指令碼**</span><span class="sxs-lookup"><span data-stu-id="25759-298">**ColorPickerWheel script**</span></span>

<span data-ttu-id="25759-299">**ColorPickerWheel**訂閱 Unity **InteractionSourceUpdated**接聽觸控事件的事件。</span><span class="sxs-lookup"><span data-stu-id="25759-299">**ColorPickerWheel** subscribes to Unity's **InteractionSourceUpdated** event to listen for touchpad events.</span></span>

<span data-ttu-id="25759-300">在  **InteractionSourceUpdated()**，指令碼會先檢查以確保它：</span><span class="sxs-lookup"><span data-stu-id="25759-300">In **InteractionSourceUpdated()**, the script first checks to ensure that it:</span></span>
* <span data-ttu-id="25759-301">是實際的觸控事件 (obj.state。**touchpadTouched**)</span><span class="sxs-lookup"><span data-stu-id="25759-301">is actually a touchpad event (obj.state.**touchpadTouched**)</span></span>
* <span data-ttu-id="25759-302">來自左方的控制站 (obj.state.source。**法線慣用手的**)</span><span class="sxs-lookup"><span data-stu-id="25759-302">originates from the left controller (obj.state.source.**handedness**)</span></span>

<span data-ttu-id="25759-303">如果兩者都是 true，觸控板的位置 (obj.state。**touchpadPosition**) 指派給**selectorPosition**。</span><span class="sxs-lookup"><span data-stu-id="25759-303">If both are true, the touchpad position (obj.state.**touchpadPosition**) is assigned to **selectorPosition**.</span></span>

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

<span data-ttu-id="25759-304">在  **update （)**，這取決於**可見**屬性，就會觸發色彩選擇器的動畫元件中顯示和隱藏動畫觸發程序</span><span class="sxs-lookup"><span data-stu-id="25759-304">In **Update()**, based on **visible** property, it triggers Show and Hide animation triggers in the color picker's animator component</span></span>

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

<span data-ttu-id="25759-305">在  **update （)**， **selectorPosition**用來轉換無限遠的光線色彩轉輪網狀結構 collider 傳回 UV 位置。</span><span class="sxs-lookup"><span data-stu-id="25759-305">In **Update()**, **selectorPosition** is used to cast a ray at the color wheel's mesh collider, which returns a UV position.</span></span> <span data-ttu-id="25759-306">這個位置可用來尋找像素座標和色彩的色彩轉輪材質的值。</span><span class="sxs-lookup"><span data-stu-id="25759-306">This position can then be used to find the pixel coordinate and color value of the color wheel's texture.</span></span> <span data-ttu-id="25759-307">這個值是透過其他指令碼必須能夠**SelectedColor**屬性。</span><span class="sxs-lookup"><span data-stu-id="25759-307">This value is accessible to other scripts via the **SelectedColor** property.</span></span>

![色彩選擇器滾輪 Raycasting](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a><span data-ttu-id="25759-309">第 4 章-覆寫控制器模型</span><span class="sxs-lookup"><span data-stu-id="25759-309">Chapter 4 - Overriding controller model</span></span>

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a><span data-ttu-id="25759-310">目標</span><span class="sxs-lookup"><span data-stu-id="25759-310">Objectives</span></span>

* <span data-ttu-id="25759-311">了解如何覆寫控制器模型，以自訂的 3D 模型。</span><span class="sxs-lookup"><span data-stu-id="25759-311">Learn how to override the controller model with a custom 3D model.</span></span>

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a><span data-ttu-id="25759-313">指示</span><span class="sxs-lookup"><span data-stu-id="25759-313">Instructions</span></span>

* <span data-ttu-id="25759-314">按一下  **MotionControllers**中**階層**面板。</span><span class="sxs-lookup"><span data-stu-id="25759-314">Click **MotionControllers** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="25759-315">按一下右側的圓形**替代的右方控制器**欄位。</span><span class="sxs-lookup"><span data-stu-id="25759-315">Click the circle on the right side of the **Alternate Right Controller** field.</span></span>
* <span data-ttu-id="25759-316">在中輸入 **' BrushController**'，然後從結果選取 prefab。</span><span class="sxs-lookup"><span data-stu-id="25759-316">Type in **'BrushController**' and select the prefab from the result.</span></span> <span data-ttu-id="25759-317">您可以找到它資產/AppPrefabs/**BrushController**。</span><span class="sxs-lookup"><span data-stu-id="25759-317">You can find it under Assets/AppPrefabs/**BrushController**.</span></span>
* <span data-ttu-id="25759-318">檢查**一律使用替代的正確模型**</span><span class="sxs-lookup"><span data-stu-id="25759-318">Check **Always Use Alternate Right Model**</span></span>

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

<span data-ttu-id="25759-320">**BrushController** prefab 沒有要納入**階層**面板。</span><span class="sxs-lookup"><span data-stu-id="25759-320">The **BrushController** prefab does not have to be included in the **Hierarchy** panel.</span></span> <span data-ttu-id="25759-321">不過，若要查看它的子元件：</span><span class="sxs-lookup"><span data-stu-id="25759-321">However, to check out its child components:</span></span>
* <span data-ttu-id="25759-322">在 [**專案**] 面板中，輸入**BrushController**拖**BrushController**至 prefab**階層**面板。</span><span class="sxs-lookup"><span data-stu-id="25759-322">In the **Project** panel, type in **BrushController** and drag **BrushController** prefab into the **Hierarchy** panel.</span></span>

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

<span data-ttu-id="25759-324">您會發現**祕訣**元件**BrushController**。</span><span class="sxs-lookup"><span data-stu-id="25759-324">You will find the **Tip** component in **BrushController**.</span></span> <span data-ttu-id="25759-325">我們將使用其轉型，以啟動/停止繪製線條。</span><span class="sxs-lookup"><span data-stu-id="25759-325">We will use its transform to start/stop drawing lines.</span></span>
* <span data-ttu-id="25759-326">刪除**BrushController**從**階層**面板。</span><span class="sxs-lookup"><span data-stu-id="25759-326">Delete the **BrushController** from the **Hierarchy** panel.</span></span>
* <span data-ttu-id="25759-327">**儲存**場景，然後按一下**播放** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="25759-327">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="25759-328">您將能夠看到筆刷模型取代右移動控制器。</span><span class="sxs-lookup"><span data-stu-id="25759-328">You will be able to see the brush model replaced the right-hand motion controller.</span></span>

## <a name="chapter-5---painting-with-select-input"></a><span data-ttu-id="25759-329">第 5 章-使用選取的輸入繪製</span><span class="sxs-lookup"><span data-stu-id="25759-329">Chapter 5 - Painting with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a><span data-ttu-id="25759-330">目標</span><span class="sxs-lookup"><span data-stu-id="25759-330">Objectives</span></span>

* <span data-ttu-id="25759-331">了解如何使用 [選取] 按鈕的事件來啟動和停止為線條繪圖</span><span class="sxs-lookup"><span data-stu-id="25759-331">Learn how to use the Select button event to start and stop a line drawing</span></span>

### <a name="instructions"></a><span data-ttu-id="25759-332">指示</span><span class="sxs-lookup"><span data-stu-id="25759-332">Instructions</span></span>

* <span data-ttu-id="25759-333">搜尋**BrushController** prefab 中**專案**面板。</span><span class="sxs-lookup"><span data-stu-id="25759-333">Search **BrushController** prefab in the **Project** panel.</span></span>
* <span data-ttu-id="25759-334">在 [ **Inspector** ] 面板中，按兩下**BrushController**若要查看 Visual Studio 中的程式碼的指令碼</span><span class="sxs-lookup"><span data-stu-id="25759-334">In the **Inspector** panel, double click **BrushController** Script to see the code in Visual Studio</span></span>

<span data-ttu-id="25759-335">**BrushController 指令碼**</span><span class="sxs-lookup"><span data-stu-id="25759-335">**BrushController script**</span></span>

<span data-ttu-id="25759-336">**BrushController**訂閱 InteractionManager **InteractionSourcePressed**並**InteractionSourceReleased**事件。</span><span class="sxs-lookup"><span data-stu-id="25759-336">**BrushController** subscribes to the InteractionManager's **InteractionSourcePressed** and **InteractionSourceReleased** events.</span></span> <span data-ttu-id="25759-337">當**InteractionSourcePressed**觸發事件時，筆刷**繪製**屬性設定為 true，當**InteractionSourceReleased**觸發事件時，筆刷的**繪製**屬性設定為 false。</span><span class="sxs-lookup"><span data-stu-id="25759-337">When **InteractionSourcePressed** event is triggered, the brush's **Draw** property is set to true; when **InteractionSourceReleased** event is triggered, the brush's **Draw** property is set to false.</span></span>

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

<span data-ttu-id="25759-338">雖然**繪製**設為 true，筆刷會產生點中具現化的 Unity **LineRenderer**。</span><span class="sxs-lookup"><span data-stu-id="25759-338">While **Draw** is set to true, the brush will generate points in an instantiated Unity **LineRenderer**.</span></span> <span data-ttu-id="25759-339">此 prefab 的參考會保留在的筆刷**筆劃 Prefab**欄位。</span><span class="sxs-lookup"><span data-stu-id="25759-339">A reference to this prefab is kept in the brush's **Stroke Prefab** field.</span></span>

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

<span data-ttu-id="25759-340">若要使用目前選取的色彩，色彩選擇器滾輪 UI 中，從**BrushController**必須有參考**ColorPickerWheel**物件。</span><span class="sxs-lookup"><span data-stu-id="25759-340">To use the currently selected color from the color picker wheel UI, **BrushController** needs to have a reference to the **ColorPickerWheel** object.</span></span> <span data-ttu-id="25759-341">因為**BrushController** prefab 在做為取代控制站的執行階段具現化，場景中物件的任何參考必須在執行階段進行設定。</span><span class="sxs-lookup"><span data-stu-id="25759-341">Because the **BrushController** prefab is instantiated at runtime as a replacement controller, any references to objects in the scene will have to be set at runtime.</span></span> <span data-ttu-id="25759-342">在此案例中，我們使用**GameObject.FindObjectOfType**找出**ColorPickerWheel**:</span><span class="sxs-lookup"><span data-stu-id="25759-342">In this case we use **GameObject.FindObjectOfType** to locate the **ColorPickerWheel**:</span></span>

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```
* <span data-ttu-id="25759-343">**儲存**場景，然後按一下**播放** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="25759-343">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="25759-344">您可以繪製線條和繪製右手邊的控制站上使用 [選取] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="25759-344">You will be able to draw the lines and paint using the select button on the right-hand controller.</span></span>

## <a name="chapter-6---object-spawning-with-select-input"></a><span data-ttu-id="25759-345">輸入一章 6-繁衍與選取的物件</span><span class="sxs-lookup"><span data-stu-id="25759-345">Chapter 6 - Object spawning with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a><span data-ttu-id="25759-346">目標</span><span class="sxs-lookup"><span data-stu-id="25759-346">Objectives</span></span>

* <span data-ttu-id="25759-347">了解如何使用 Select 和理解餂鈕瓿咘輸入</span><span class="sxs-lookup"><span data-stu-id="25759-347">Learn how to use Select and Grasp button input events</span></span>
* <span data-ttu-id="25759-348">了解如何具現化物件</span><span class="sxs-lookup"><span data-stu-id="25759-348">Learn how to instantiate objects</span></span>

### <a name="instructions"></a><span data-ttu-id="25759-349">指示</span><span class="sxs-lookup"><span data-stu-id="25759-349">Instructions</span></span>

* <span data-ttu-id="25759-350">在 [**專案**] 面板中，鍵入**ObjectSpawner**在搜尋方塊中。</span><span class="sxs-lookup"><span data-stu-id="25759-350">In the **Project** panel, type **ObjectSpawner** in the search box.</span></span> <span data-ttu-id="25759-351">您也可以尋找其下的資產/AppPrefabs /</span><span class="sxs-lookup"><span data-stu-id="25759-351">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="25759-352">拖曳**ObjectSpawner**至 prefab**階層**面板。</span><span class="sxs-lookup"><span data-stu-id="25759-352">Drag the **ObjectSpawner** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="25759-353">按一下  **ObjectSpawner**中**階層**面板。</span><span class="sxs-lookup"><span data-stu-id="25759-353">Click **ObjectSpawner** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="25759-354">**ObjectSpawner**具有名為欄位**色彩來源**。</span><span class="sxs-lookup"><span data-stu-id="25759-354">**ObjectSpawner** has a field named **Color Source**.</span></span>
* <span data-ttu-id="25759-355">從**階層** 面板中，拖曳**ColorPickerWheel**到這個欄位的參考。</span><span class="sxs-lookup"><span data-stu-id="25759-355">From the **Hierarchy** panel, drag the **ColorPickerWheel** reference into this field.</span></span>

![物件 Spawner 偵測器](images/mr213-objectspawnercolorpickerwheel-650px.jpg)
* <span data-ttu-id="25759-357">按一下  **ObjectSpawner** prefab 中**階層**面板。</span><span class="sxs-lookup"><span data-stu-id="25759-357">Click the **ObjectSpawner** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="25759-358">在 [ **Inspector** ] 面板中，按兩下**ObjectSpawner**若要查看 Visual Studio 中的程式碼的指令碼。</span><span class="sxs-lookup"><span data-stu-id="25759-358">In the **Inspector** panel, double click **ObjectSpawner** Script to see the code in Visual Studio.</span></span>

<span data-ttu-id="25759-359">**ObjectSpawner 指令碼**</span><span class="sxs-lookup"><span data-stu-id="25759-359">**ObjectSpawner script**</span></span>

<span data-ttu-id="25759-360">**ObjectSpawner**會具現化的空間的基本網格 （cube、 球體、 圓柱） 的複本。</span><span class="sxs-lookup"><span data-stu-id="25759-360">The **ObjectSpawner** instantiates copies of a primitive mesh (cube, sphere, cylinder) into the space.</span></span> <span data-ttu-id="25759-361">當**InteractionSourcePressed**它會檢查法線慣用手的而且如果偵測到**InteractionSourcePressType.Grasp**或是**InteractionSourcePressType.Select**事件。</span><span class="sxs-lookup"><span data-stu-id="25759-361">When a **InteractionSourcePressed** is detected it checks the handedness and if it's an **InteractionSourcePressType.Grasp** or **InteractionSourcePressType.Select** event.</span></span>

<span data-ttu-id="25759-362">針對**抓住**事件，就會自動遞增的索引型別的目前網格 （sphere、 cube、 圓柱）</span><span class="sxs-lookup"><span data-stu-id="25759-362">For a **Grasp** event, it increments the index of current mesh type (sphere, cube, cylinder)</span></span>

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

<span data-ttu-id="25759-363">針對**選取 **事件，請在**SpawnObject()**，新的物件會具現化、 非父代和發行到全球。</span><span class="sxs-lookup"><span data-stu-id="25759-363">For a **Select** event, in **SpawnObject()**, a new object is instantiated, un-parented and released into the world.</span></span>

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detatch the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

<span data-ttu-id="25759-364">**ObjectSpawner**會使用**ColorPickerWheel**設定顯示物件的材質的色彩。</span><span class="sxs-lookup"><span data-stu-id="25759-364">The **ObjectSpawner** uses the **ColorPickerWheel** to set the color of the display object's material.</span></span> <span data-ttu-id="25759-365">繁衍 （spawn） 的物件會獲得這份資料的執行個體，因此它們會保留其色彩。</span><span class="sxs-lookup"><span data-stu-id="25759-365">Spawned objects are given an instance of this material so they will retain their color.</span></span>
* <span data-ttu-id="25759-366">**儲存**場景，然後按一下**播放** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="25759-366">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="25759-367">您將能夠變更掌握按鈕的物件，然後繁衍 （spawn） 使用 [選取] 按鈕的物件。</span><span class="sxs-lookup"><span data-stu-id="25759-367">You will be able to change the objects with the Grasp button and spawn objects with the Select button.</span></span>

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a><span data-ttu-id="25759-368">建置並部署至混合實境入口網站的 應用程式</span><span class="sxs-lookup"><span data-stu-id="25759-368">Build and deploy app to Mixed Reality Portal</span></span>
* <span data-ttu-id="25759-369">在 Unity 中，選取**檔案 > 組建設定**。</span><span class="sxs-lookup"><span data-stu-id="25759-369">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="25759-370">按一下 **加入開啟的場景**以新增至目前場景**組建中的場景**。</span><span class="sxs-lookup"><span data-stu-id="25759-370">Click **Add Open Scenes** to add current scene to the **Scenes In Build**.</span></span>
* <span data-ttu-id="25759-371">按一下 [建置] 。</span><span class="sxs-lookup"><span data-stu-id="25759-371">Click **Build**.</span></span>
* <span data-ttu-id="25759-372">建立**新的資料夾**名為 「 應用程式 」。</span><span class="sxs-lookup"><span data-stu-id="25759-372">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="25759-373">只要按一下**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="25759-373">Single click the **App** folder.</span></span>
* <span data-ttu-id="25759-374">按一下 [選擇資料夾]。</span><span class="sxs-lookup"><span data-stu-id="25759-374">Click **Select Folder**.</span></span>
* <span data-ttu-id="25759-375">Unity 完成時，會出現檔案總管 視窗。</span><span class="sxs-lookup"><span data-stu-id="25759-375">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="25759-376">開啟**應用程式**資料夾。</span><span class="sxs-lookup"><span data-stu-id="25759-376">Open the **App** folder.</span></span>
* <span data-ttu-id="25759-377">按兩下**YourSceneName.sln** Visual Studio 方案檔。</span><span class="sxs-lookup"><span data-stu-id="25759-377">Double click **YourSceneName.sln** Visual Studio Solution file.</span></span>
* <span data-ttu-id="25759-378">使用頂端的工具列，在 Visual Studio 中，從 偵錯，若要變更目標**Release**進出至 ARM **X64**。</span><span class="sxs-lookup"><span data-stu-id="25759-378">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X64**.</span></span>
* <span data-ttu-id="25759-379">按一下 [裝置] 按鈕旁邊的下拉式箭號，然後選取**本機電腦**。</span><span class="sxs-lookup"><span data-stu-id="25759-379">Click on the drop-down arrow next to the Device button, and select **Local Machine**.</span></span>
* <span data-ttu-id="25759-380">按一下 **偵錯-> 啟動但不偵錯**中的功能表或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="25759-380">Click **Debug -> Start Without debugging** in the menu or press **Ctrl + F5**.</span></span>

<span data-ttu-id="25759-381">現在應用程式是內建，並安裝在混合實境入口網站。</span><span class="sxs-lookup"><span data-stu-id="25759-381">Now the app is built and installed in Mixed Reality Portal.</span></span> <span data-ttu-id="25759-382">您可以重新啟動透過在混合實境入口網站中的 [開始] 功能表。</span><span class="sxs-lookup"><span data-stu-id="25759-382">You can launch it again through Start menu in Mixed Reality Portal.</span></span>

## <a name="advanced-design---brush-tools-with-radial-layout"></a><span data-ttu-id="25759-383">進階的程式設計-使用放射狀版面配置的筆刷工具</span><span class="sxs-lookup"><span data-stu-id="25759-383">Advanced design - Brush tools with radial layout</span></span>

![MixedReality213 Main](images/mr213-main-600px.jpg)

<span data-ttu-id="25759-385">在本章中，您將學習如何使用自訂的筆刷工具集合取代預設動作的控制器模型。</span><span class="sxs-lookup"><span data-stu-id="25759-385">In this chapter, you will learn how to replace the default motion controller model with a custom brush tool collection.</span></span> <span data-ttu-id="25759-386">供您參考，您可以找到完整的場景**MixedReality213Advanced**下方**場景**資料夾。</span><span class="sxs-lookup"><span data-stu-id="25759-386">For your reference, you can find the completed scene **MixedReality213Advanced** under **Scenes** folder.</span></span>

### <a name="instructions"></a><span data-ttu-id="25759-387">指示</span><span class="sxs-lookup"><span data-stu-id="25759-387">Instructions</span></span>

* <span data-ttu-id="25759-388">在 [**專案**] 面板中，鍵入**BrushSelector**在搜尋方塊中。</span><span class="sxs-lookup"><span data-stu-id="25759-388">In the **Project** panel, type **BrushSelector** in the search box .</span></span> <span data-ttu-id="25759-389">您也可以尋找其下的資產/AppPrefabs /</span><span class="sxs-lookup"><span data-stu-id="25759-389">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="25759-390">拖曳**BrushSelector**至 prefab**階層**面板。</span><span class="sxs-lookup"><span data-stu-id="25759-390">Drag the **BrushSelector** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="25759-391">為組織建立空白 GameObject 呼叫**筆刷**</span><span class="sxs-lookup"><span data-stu-id="25759-391">For organization, create an empty GameObject called **Brushes**</span></span>
* <span data-ttu-id="25759-392">下列從 prefabs 拖曳**專案** 面板到**筆刷**</span><span class="sxs-lookup"><span data-stu-id="25759-392">Drag following prefabs from the **Project** panel into **Brushes**</span></span>
    * <span data-ttu-id="25759-393">Assets/AppPrefabs/**BrushFat**</span><span class="sxs-lookup"><span data-stu-id="25759-393">Assets/AppPrefabs/**BrushFat**</span></span>
    * <span data-ttu-id="25759-394">Assets/AppPrefabs/**BrushThin**</span><span class="sxs-lookup"><span data-stu-id="25759-394">Assets/AppPrefabs/**BrushThin**</span></span>
    * <span data-ttu-id="25759-395">Assets/AppPrefabs/**Eraser**</span><span class="sxs-lookup"><span data-stu-id="25759-395">Assets/AppPrefabs/**Eraser**</span></span>
    * <span data-ttu-id="25759-396">Assets/AppPrefabs/**MarkerFat**</span><span class="sxs-lookup"><span data-stu-id="25759-396">Assets/AppPrefabs/**MarkerFat**</span></span>
    * <span data-ttu-id="25759-397">Assets/AppPrefabs/**MarkerThin**</span><span class="sxs-lookup"><span data-stu-id="25759-397">Assets/AppPrefabs/**MarkerThin**</span></span>
    * <span data-ttu-id="25759-398">Assets/AppPrefabs/**Pencil**</span><span class="sxs-lookup"><span data-stu-id="25759-398">Assets/AppPrefabs/**Pencil**</span></span>

![筆刷](images/mixedreality213-brushes-250px.png)
* <span data-ttu-id="25759-400">按一下  **MotionControllers** prefab 中**階層**面板。</span><span class="sxs-lookup"><span data-stu-id="25759-400">Click **MotionControllers** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="25759-401">在 [ **Inspector** ] 面板中，取消核取**一律使用替代權限模型**上**動作控制器的視覺化檢視**</span><span class="sxs-lookup"><span data-stu-id="25759-401">In the **Inspector** panel, uncheck **Always Use Alternate Right Model** on the **Motion Controller Visualizer**</span></span>
* <span data-ttu-id="25759-402">在 **階層** 面板中，按一下  **BrushSelector**</span><span class="sxs-lookup"><span data-stu-id="25759-402">In the **Hierarchy** panel, click **BrushSelector**</span></span>
* <span data-ttu-id="25759-403">**BrushSelector**具有名為欄位**ColorPicker**</span><span class="sxs-lookup"><span data-stu-id="25759-403">**BrushSelector** has a field named **ColorPicker**</span></span>
* <span data-ttu-id="25759-404">從**階層** 面板中，拖曳**ColorPickerWheel**成**ColorPicker**欄位中**Inspector**面板。</span><span class="sxs-lookup"><span data-stu-id="25759-404">From the **Hierarchy** panel, drag the **ColorPickerWheel** into **ColorPicker** field in the **Inspector** panel.</span></span>

![指派至筆刷選取器 ColorPickerWheel](images/mr213-brushselector-500px.jpg)
* <span data-ttu-id="25759-406">在 **階層** 面板的  **BrushSelector** prefab，選取**功能表**物件。</span><span class="sxs-lookup"><span data-stu-id="25759-406">In the **Hierarchy** panel, under **BrushSelector** prefab, select the **Menu** object.</span></span>
* <span data-ttu-id="25759-407">在  **Inspector**  面板的  **LineObjectCollection**元件，開啟**物件**陣列下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="25759-407">In the **Inspector** panel, under the **LineObjectCollection** component, open the **Objects** array dropdown.</span></span> <span data-ttu-id="25759-408">您會看到空的插槽 6。</span><span class="sxs-lookup"><span data-stu-id="25759-408">You will see 6 empty slots.</span></span>
* <span data-ttu-id="25759-409">從**階層** 面板中，拖曳每個父代下 prefabs**筆刷**GameObject 到這些位置依任何順序。</span><span class="sxs-lookup"><span data-stu-id="25759-409">From the **Hierarchy** panel, drag each of the prefabs parented under the **Brushes** GameObject into these slots in any order.</span></span> <span data-ttu-id="25759-410">（請確定您從場景，而不在專案資料夾 prefabs 拖曳 prefabs。）</span><span class="sxs-lookup"><span data-stu-id="25759-410">(Make sure you're dragging the prefabs from the scene, not the prefabs in the project folder.)</span></span>

![筆刷選取器](images/mr213-brushselectorbrushes-700px.jpg)

<span data-ttu-id="25759-412">**BrushSelector prefab**</span><span class="sxs-lookup"><span data-stu-id="25759-412">**BrushSelector prefab**</span></span>

<span data-ttu-id="25759-413">由於**BrushSelector**繼承**AttachToController**，它會顯示**法線慣用手**並**項目**中的選項**Inspector**面板。</span><span class="sxs-lookup"><span data-stu-id="25759-413">Since the **BrushSelector** inherits **AttachToController**, it shows **Handedness** and **Element** options in the **Inspector** panel.</span></span> <span data-ttu-id="25759-414">我們選取 **權限**並**指向會造成**來將筆刷工具附加至有正向方向的右手邊控制器。</span><span class="sxs-lookup"><span data-stu-id="25759-414">We selected **Right** and **Pointing Pose** to attach brush tools to the right hand controller with forward direction.</span></span>

<span data-ttu-id="25759-415">**BrushSelector**會利用兩個公用程式：</span><span class="sxs-lookup"><span data-stu-id="25759-415">The **BrushSelector** makes use of two utilities:</span></span>
* <span data-ttu-id="25759-416">**橢圓形**： 用來產生點沿著橢圓形圖案的空間中。</span><span class="sxs-lookup"><span data-stu-id="25759-416">**Ellipse**: used to generate points in space along an ellipse shape.</span></span>
* <span data-ttu-id="25759-417">**LineObjectCollection**： 會使用任何列類別 （例如橢圓形） 所產生的點物件。</span><span class="sxs-lookup"><span data-stu-id="25759-417">**LineObjectCollection**: distributes objects using the points generated by any Line class (eg, Ellipse).</span></span> <span data-ttu-id="25759-418">這是什麼我們將使用放置我們沿著 [橢圓形] 圖形的筆刷。</span><span class="sxs-lookup"><span data-stu-id="25759-418">This is what we'll be using to place our brushes along the Ellipse shape.</span></span>

<span data-ttu-id="25759-419">結合時，這些公用程式可用來建立星形功能表。</span><span class="sxs-lookup"><span data-stu-id="25759-419">When combined, these utilities can be used to create a radial menu.</span></span>

<span data-ttu-id="25759-420">**LineObjectCollection 指令碼**</span><span class="sxs-lookup"><span data-stu-id="25759-420">**LineObjectCollection script**</span></span>

<span data-ttu-id="25759-421">**LineObjectCollection**具有適用於大小、 位置和旋轉物件沿著其列分散的控制。</span><span class="sxs-lookup"><span data-stu-id="25759-421">**LineObjectCollection** has controls for the size, position and rotation of objects distributed along its line.</span></span> <span data-ttu-id="25759-422">這是適合用來建立類似的筆刷選取器的放射狀功能表。</span><span class="sxs-lookup"><span data-stu-id="25759-422">This is useful for creating radial menus like the brush selector.</span></span> <span data-ttu-id="25759-423">若要建立外觀的筆刷可從 nothing 在接近選取置中位置，如**ObjectScale**邊緣的曲線要求尖峰期的置中與 tapers 已關閉。</span><span class="sxs-lookup"><span data-stu-id="25759-423">To create the appearance of brushes that scale up from nothing as they approach the center selected position, the **ObjectScale** curve peaks in the center and tapers off at the edges.</span></span>

<span data-ttu-id="25759-424">**BrushSelector 指令碼**</span><span class="sxs-lookup"><span data-stu-id="25759-424">**BrushSelector script**</span></span>

<span data-ttu-id="25759-425">若是**BrushSelector**，我們選擇使用程序的動畫。</span><span class="sxs-lookup"><span data-stu-id="25759-425">In the case of the **BrushSelector**, we've chosen to use procedural animation.</span></span> <span data-ttu-id="25759-426">首先，筆刷模型發佈的方式，藉由將橢圓形**LineObjectCollection**指令碼。</span><span class="sxs-lookup"><span data-stu-id="25759-426">First, brush models are distributed in an ellipse by the **LineObjectCollection** script.</span></span> <span data-ttu-id="25759-427">然後，每個筆刷是負責維護其根據使用者的手中的位置及其**DisplayMode**變更取決於選擇的值。</span><span class="sxs-lookup"><span data-stu-id="25759-427">Then, each brush is responsible for maintaining its position in the user's hand based on its **DisplayMode** value, which changes based on the selection.</span></span> <span data-ttu-id="25759-428">我們選擇程序性的方法，因為高中斷在使用者選取筆刷的筆刷位置轉換的機率。</span><span class="sxs-lookup"><span data-stu-id="25759-428">We chose a procedural approach because of the high probability of brush position transitions being interrupted as the user selects brushes.</span></span> <span data-ttu-id="25759-429">Mecanim 動畫可以依正常程序，處理中斷，但它通常會比簡單的 Lerp 作業更複雜。</span><span class="sxs-lookup"><span data-stu-id="25759-429">Mecanim animations can handle interruptions gracefully, but it tends to be more complicated than a simple Lerp operation.</span></span>

<span data-ttu-id="25759-430">**BrushSelector**使用兩者的組合。</span><span class="sxs-lookup"><span data-stu-id="25759-430">**BrushSelector** uses a combination of both.</span></span> <span data-ttu-id="25759-431">偵測到觸控輸入時，筆刷選項就會顯示出來，並沿著放射狀功能表相應增加。</span><span class="sxs-lookup"><span data-stu-id="25759-431">When touchpad input is detected, brush options become visible and scale up along the radial menu.</span></span> <span data-ttu-id="25759-432">逾時期限 （表示使用者已選取項目） 之後的筆刷選項擴展向下同樣地，離開只有選取的筆刷。</span><span class="sxs-lookup"><span data-stu-id="25759-432">After a timeout period (which indicates that the user has made a selection) the brush options scale down again, leaving only the selected brush.</span></span>

<span data-ttu-id="25759-433">**視覺化觸控輸入**</span><span class="sxs-lookup"><span data-stu-id="25759-433">**Visualizing touchpad input**</span></span>

<span data-ttu-id="25759-434">即使是在其中已完全取代控制器模型的情況下，很有幫助顯示原始的模型輸入中的 輸入。</span><span class="sxs-lookup"><span data-stu-id="25759-434">Even in cases where the controller model has been completely replaced, it can be helpful to show input on the original model inputs.</span></span> <span data-ttu-id="25759-435">這有助於在現實中以讓使用者的動作。</span><span class="sxs-lookup"><span data-stu-id="25759-435">This helps to ground the user's actions in reality.</span></span> <span data-ttu-id="25759-436">針對**BrushSelector**我們選擇要觸控板短暫顯示在收到輸入。</span><span class="sxs-lookup"><span data-stu-id="25759-436">For the **BrushSelector** we've chosen to make the touchpad briefly visible when the input is received.</span></span> <span data-ttu-id="25759-437">這樣做，請從控制器，其內容取代為自訂的資料，擷取觸控板項目，然後將漸層套用至該材質的色彩，根據過去的時間觸控板收到輸入時。</span><span class="sxs-lookup"><span data-stu-id="25759-437">This was done by retrieving the Touchpad element from the controller, replacing its material with a custom material, then applying a gradient to that material's color based on the last time touchpad input was received.</span></span>

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }
            
    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

<span data-ttu-id="25759-438">**觸控輸入的筆刷工具選取範圍**</span><span class="sxs-lookup"><span data-stu-id="25759-438">**Brush tool selection with touchpad input**</span></span>

<span data-ttu-id="25759-439">當筆刷選取器偵測到觸控的已按下的輸入時，它會檢查以判斷它是向左或向右輸入的位置。</span><span class="sxs-lookup"><span data-stu-id="25759-439">When the brush selector detects touchpad's pressed input, it checks the position of the input to determine if it was to the left or right.</span></span>

<span data-ttu-id="25759-440">**使用 selectPressedAmount 筆劃粗細**</span><span class="sxs-lookup"><span data-stu-id="25759-440">**Stroke thickness with selectPressedAmount**</span></span>

<span data-ttu-id="25759-441">而不是**InteractionSourcePressType.Select**中的事件**InteractionSourcePressed()**，您可以取得已按下量透過類比值**selectPressedAmount**.</span><span class="sxs-lookup"><span data-stu-id="25759-441">Instead of the **InteractionSourcePressType.Select** event in the **InteractionSourcePressed()**, you can get the analog value of the pressed amount through **selectPressedAmount**.</span></span> <span data-ttu-id="25759-442">此值可以在擷取**InteractionSourceUpdated()**。</span><span class="sxs-lookup"><span data-stu-id="25759-442">This value can be retrieved in **InteractionSourceUpdated()**.</span></span>

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

<span data-ttu-id="25759-443">**橡皮擦指令碼**</span><span class="sxs-lookup"><span data-stu-id="25759-443">**Eraser script**</span></span>

<span data-ttu-id="25759-444">**橡皮擦**是一種特殊的覆寫基底的筆刷**筆刷**的**DrawOverTime()** 函式。</span><span class="sxs-lookup"><span data-stu-id="25759-444">**Eraser** is a special type of brush that overrides the base **Brush**'s **DrawOverTime()** function.</span></span> <span data-ttu-id="25759-445">繪製，則為 true 時，橡皮擦會檢查其提示是否與任何現有的筆刷筆劃。</span><span class="sxs-lookup"><span data-stu-id="25759-445">While Draw is true, the eraser checks to see if its tip intersects with any existing brush strokes.</span></span> <span data-ttu-id="25759-446">若是如此，它們是新增至佇列，以關閉壓縮，而且刪除。</span><span class="sxs-lookup"><span data-stu-id="25759-446">If it does, they are added to a queue to be shrunk down and deleted.</span></span>

## <a name="advanced-design---teleportation-and-locomotion"></a><span data-ttu-id="25759-447">進階的設計-屏障和 locomotion</span><span class="sxs-lookup"><span data-stu-id="25759-447">Advanced design - Teleportation and locomotion</span></span>

<span data-ttu-id="25759-448">如果您想要允許使用者與使用搖桿的屏障中移動場景，請使用**MixedRealityCameraParent**而不是**MixedRealityCamera**。</span><span class="sxs-lookup"><span data-stu-id="25759-448">If you want to allow the user to move around the scene with teleportation using thumbstick, use **MixedRealityCameraParent** instead of **MixedRealityCamera**.</span></span> <span data-ttu-id="25759-449">您也需要新增**InputManager**並**DefaultCusor**。</span><span class="sxs-lookup"><span data-stu-id="25759-449">You also need to add **InputManager** and **DefaultCusor**.</span></span> <span data-ttu-id="25759-450">由於**MixedRealityCameraParent**已經包含**MotionControllers**並**界限**做為子元件，您應該移除現有**MotionControllers**並**環境**prefab。</span><span class="sxs-lookup"><span data-stu-id="25759-450">Since **MixedRealityCameraParent** already includes **MotionControllers** and **Boundary** as child components, you should remove existing **MotionControllers** and **Environment** prefab.</span></span>

### <a name="instructions"></a><span data-ttu-id="25759-451">指示</span><span class="sxs-lookup"><span data-stu-id="25759-451">Instructions</span></span>

* <span data-ttu-id="25759-452">在 [**階層**] 面板中，刪除**MixedRealityCamera**，**環境**並**MotionControllers**</span><span class="sxs-lookup"><span data-stu-id="25759-452">In the **Hierarchy** panel, delete **MixedRealityCamera**, **Environment** and **MotionControllers**</span></span>
* <span data-ttu-id="25759-453">從 **[專案] 面板**，搜尋並拖曳到下列 prefabs**階層**面板：</span><span class="sxs-lookup"><span data-stu-id="25759-453">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="25759-454">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span><span class="sxs-lookup"><span data-stu-id="25759-454">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span></span>
    * <span data-ttu-id="25759-455">Assets/AppPrefabs/Input/Prefabs/**InputManager**</span><span class="sxs-lookup"><span data-stu-id="25759-455">Assets/AppPrefabs/Input/Prefabs/**InputManager**</span></span>
    * <span data-ttu-id="25759-456">Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span><span class="sxs-lookup"><span data-stu-id="25759-456">Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span></span>

![混合的實境相機父代](images/mr213-cameraparent-300px.png)
* <span data-ttu-id="25759-458">在 **階層** 面板中，按一下 **輸入管理員**</span><span class="sxs-lookup"><span data-stu-id="25759-458">In the **Hierarchy** panel, click **Input Manager**</span></span>
* <span data-ttu-id="25759-459">在 [ **Inspector** ] 面板中，向下捲動至**簡單的單一指標選取器**區段</span><span class="sxs-lookup"><span data-stu-id="25759-459">In the **Inspector** panel, scroll down to the **Simple Single Pointer Selector** section</span></span>
* <span data-ttu-id="25759-460">從**階層** 面板中，拖曳**DefaultCursor**成**游標**欄位</span><span class="sxs-lookup"><span data-stu-id="25759-460">From the **Hierarchy** panel, drag **DefaultCursor** into **Cursor** field</span></span>

![指派 DefaultCursor](images/mr213-defaultcursor-500px.png)
* <span data-ttu-id="25759-462">**儲存**場景，然後按一下**播放** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="25759-462">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="25759-463">您可以使用搖桿來旋轉左/右或傳送。</span><span class="sxs-lookup"><span data-stu-id="25759-463">You will be able to use the thumbstick to rotate left/right or teleport.</span></span>

## <a name="the-end"></a><span data-ttu-id="25759-464">結束</span><span class="sxs-lookup"><span data-stu-id="25759-464">The end</span></span>

<span data-ttu-id="25759-465">而且，本教學課程結束 ！</span><span class="sxs-lookup"><span data-stu-id="25759-465">And that's the end of this tutorial!</span></span> <span data-ttu-id="25759-466">您已了解：</span><span class="sxs-lookup"><span data-stu-id="25759-466">You learned:</span></span>
* <span data-ttu-id="25759-467">如何使用 Unity 的遊戲模式和執行階段中的動作控制器模型。</span><span class="sxs-lookup"><span data-stu-id="25759-467">How to work with motion controller models in Unity's game mode and runtime.</span></span>
* <span data-ttu-id="25759-468">如何使用不同類型的餂鈕瓿咘和他們的應用程式。</span><span class="sxs-lookup"><span data-stu-id="25759-468">How to use different types of button events and their applications.</span></span>
* <span data-ttu-id="25759-469">如何覆疊在控制器上的 UI 項目，或完全加以自訂。</span><span class="sxs-lookup"><span data-stu-id="25759-469">How to overlay UI elements on top of the controller or fully customize it.</span></span>

<span data-ttu-id="25759-470">您現在已準備好開始使用影片控制站中建立您自己的沉浸式體驗 ！</span><span class="sxs-lookup"><span data-stu-id="25759-470">You are now ready to start creating your own immersive experience with motion controllers!</span></span>

## <a name="completed-scenes"></a><span data-ttu-id="25759-471">已完成的場景</span><span class="sxs-lookup"><span data-stu-id="25759-471">Completed scenes</span></span>

* <span data-ttu-id="25759-472">在 Unity**專案**] 面板中的，按一下 [**場景**資料夾。</span><span class="sxs-lookup"><span data-stu-id="25759-472">In Unity's **Project** panel click on the **Scenes** folder.</span></span>
* <span data-ttu-id="25759-473">您會發現兩個 Unity sceens **MixedReality213**並**MixedReality213Advanced**。</span><span class="sxs-lookup"><span data-stu-id="25759-473">You will find two Unity sceens **MixedReality213** and **MixedReality213Advanced**.</span></span>
    * <span data-ttu-id="25759-474">**MixedReality213**:已完成的場景，使用單一的筆刷</span><span class="sxs-lookup"><span data-stu-id="25759-474">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="25759-475">**MixedReality213Advanced**:已完成的場景中填入多個筆刷選取按鈕的按下量範例</span><span class="sxs-lookup"><span data-stu-id="25759-475">**MixedReality213Advanced**: Completed scene with multiple brush with select button's press amount example</span></span>

## <a name="see-also"></a><span data-ttu-id="25759-476">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25759-476">See also</span></span>

* [<span data-ttu-id="25759-477">MR 輸入 213 專案檔</span><span class="sxs-lookup"><span data-stu-id="25759-477">MR Input 213 project files</span></span>](https://github.com/Microsoft/MixedReality213)
* [<span data-ttu-id="25759-478">混合的實境工具組-動作控制器測試場景</span><span class="sxs-lookup"><span data-stu-id="25759-478">Mixed Reality Toolkit - Motion Controller Test scene</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [<span data-ttu-id="25759-479">混合的實境工具組-抓取機制</span><span class="sxs-lookup"><span data-stu-id="25759-479">Mixed Reality Toolkit - Grab Mechanics</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [<span data-ttu-id="25759-480">動作控制器的開發指導方針</span><span class="sxs-lookup"><span data-stu-id="25759-480">Motion controller development guidelines</span></span>](motion-controllers.md)
