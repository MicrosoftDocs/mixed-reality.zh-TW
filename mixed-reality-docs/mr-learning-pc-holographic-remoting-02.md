---
title: 電腦全像攝影遠端處理教學課程 - 2。 建立全像攝影遠端處理電腦應用程式
description: 完成此課程，以了解如何從電腦到 HoloLens 2 進行遠端混合實境體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 6d11d91a0e08c48c09f676171dcb9bb8a0ff74de
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376370"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a><span data-ttu-id="7719b-105">2.建立全像攝影遠端處理電腦應用程式</span><span class="sxs-lookup"><span data-stu-id="7719b-105">2. Creating a Holographic Remoting PC application</span></span>

<span data-ttu-id="7719b-106">在本教學課程中，您將了解如何建立電腦應用程式來進行全像攝影遠端處理，並在任何時間點連線 HoloLens 2，進而提供一種在混合實境中將 3D 內容視覺化的方式。</span><span class="sxs-lookup"><span data-stu-id="7719b-106">In this tutorial, you will learn how to create a PC app for Holographic Remoting and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="7719b-107">目標</span><span class="sxs-lookup"><span data-stu-id="7719b-107">Objectives</span></span>

* <span data-ttu-id="7719b-108">設定適用於全像攝影遠端處理的 Unity</span><span class="sxs-lookup"><span data-stu-id="7719b-108">Configure Unity for Holographic Remoting</span></span>
* <span data-ttu-id="7719b-109">了解如何使用 Visual Studio 建立及部署應用程式</span><span class="sxs-lookup"><span data-stu-id="7719b-109">Learn how to build and deploy the application with Visual Studio</span></span>
* <span data-ttu-id="7719b-110">開發全像攝影遠端處理應用程式並連線到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="7719b-110">Developing Holographic Remoting application and connecting to HoloLens</span></span>

## <a name="configuring-your-scene-for-holographic-remoting"></a><span data-ttu-id="7719b-111">設定您的場景以進行全像攝影遠端處理</span><span class="sxs-lookup"><span data-stu-id="7719b-111">Configuring your scene for Holographic Remoting</span></span>

<span data-ttu-id="7719b-112">在本節中，您將設定專案，以透過 Wi-Fi 連線即時地將您的混合現實境驗串流至電腦上的 HoloLens 2 裝置。</span><span class="sxs-lookup"><span data-stu-id="7719b-112">In this section, you will configure your project to stream your Mixed Reality experience to your HoloLens 2 device from your PC in real-time over a Wi-Fi connection.</span></span>

<span data-ttu-id="7719b-113">在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.PCHolograhicRemoting] > [Prefabs] 資料夾，然後按一下 **HolographicRemoting** Prefab 並拖曳到您的場景中。</span><span class="sxs-lookup"><span data-stu-id="7719b-113">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** folder, and click and drag **HolographicRemoting** prefab into your scene.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section1-Step1-1.png)

## <a name="build-your-application-to-pc"></a><span data-ttu-id="7719b-115">在電腦中建置應用程式</span><span class="sxs-lookup"><span data-stu-id="7719b-115">Build your application to PC</span></span>

<span data-ttu-id="7719b-116">您的全像攝影遠端處理應用程式現在已準備好在電腦上建置。</span><span class="sxs-lookup"><span data-stu-id="7719b-116">Your Holographic Remoting app is now ready to build on your PC.</span></span> <span data-ttu-id="7719b-117">請遵循下列步驟來進行這些變更，以將此應用程式建立到您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="7719b-117">Follow the below steps and make these changes to build this application on to your PC.</span></span>

### <a name="1-set-the-player-settings"></a><span data-ttu-id="7719b-118">1.設定玩家設定</span><span class="sxs-lookup"><span data-stu-id="7719b-118">1. Set the player settings</span></span>

<span data-ttu-id="7719b-119">在 Unity 功能表中，選取 [編輯] > [專案設定...] 來開啟 [玩家設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="7719b-119">In the Unity menu, select Edit > Project Settings to open the Player Settings window.</span></span>

<span data-ttu-id="7719b-120">在 [XR 設定] 區段中，選取 [支援的 WSA 全像攝影遠端處理] 核取方塊，並啟用全像攝影遠端處理。</span><span class="sxs-lookup"><span data-stu-id="7719b-120">In the **XR Settings** section, select the **WSA Holographic Remoting Supported** checkbox and enable the Holographic Remoting.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a><span data-ttu-id="7719b-122">2.建置 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="7719b-122">2. Build the Unity Project</span></span>

<span data-ttu-id="7719b-123">在 Unity 功能表中，選取 [檔案] > [建置設定] 來開啟 [建置設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="7719b-123">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="7719b-124">在 [建置設定] 視窗中，按一下 [新增開啟的場景] 按鈕，將您目前的場景新增至場景。</span><span class="sxs-lookup"><span data-stu-id="7719b-124">In the Build Settings window, click the ***Add Open Scenes*** button to add your current scene to the Scenes.</span></span> <span data-ttu-id="7719b-125">在 [建置] 清單中，按一下 [建置按鈕] 以開啟 [建置通用 Windows 平台] 視窗：</span><span class="sxs-lookup"><span data-stu-id="7719b-125">In the Build list, then click the ***Build button*** to open the Build Universal Windows Platform window:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

<span data-ttu-id="7719b-127">在 [建置通用 Windows 平台] 視窗中，選擇適當的位置來儲存您的建置，例如 Documents\MixedRealityLearning。</span><span class="sxs-lookup"><span data-stu-id="7719b-127">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="7719b-128">建立新的資料夾，並為其指定適當的名稱，例如 PCHolographicRemoting。</span><span class="sxs-lookup"><span data-stu-id="7719b-128">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="7719b-129">然後按一下 [選取資料夾] 按鈕來啟動建置程序：</span><span class="sxs-lookup"><span data-stu-id="7719b-129">Then click the ***Select Folder*** button to start the build process:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

<span data-ttu-id="7719b-131">等候 Unity 完成建置程序。</span><span class="sxs-lookup"><span data-stu-id="7719b-131">Wait for Unity to finish the build process.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a><span data-ttu-id="7719b-133">3.組建和部署應用程式</span><span class="sxs-lookup"><span data-stu-id="7719b-133">3. Build and deploy the application</span></span>

<span data-ttu-id="7719b-134">當組建程序完成時，Unity 會提示 Windows 檔案總管開啟您儲存組建的位置。</span><span class="sxs-lookup"><span data-stu-id="7719b-134">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="7719b-135">瀏覽該資料夾，按兩下 .sln 檔案即可在 Visual Studio 中開啟該檔案：</span><span class="sxs-lookup"><span data-stu-id="7719b-135">Navigate inside the folder, and double-click the .sln file to open it in Visual Studio:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> <span data-ttu-id="7719b-137">如果 Visual Studio 要求您安裝新元件，請花一些時間確認是否已安裝所有必要元件，如同＜安裝工具＞文件中所指定。</span><span class="sxs-lookup"><span data-stu-id="7719b-137">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the Install the Tools documentation.</span></span>

<span data-ttu-id="7719b-138">藉由選取 x64 架構的發行設定，以及選取本機電腦作為目標，來設定電腦的 Visual Studio：</span><span class="sxs-lookup"><span data-stu-id="7719b-138">Configure Visual Studio for PC by selecting the Release configuration, the x64 architecture, and Local Machine as target:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

<span data-ttu-id="7719b-140">按一下顯示 [本機電腦] 的按鈕。</span><span class="sxs-lookup"><span data-stu-id="7719b-140">Click the button that says ***Local Machine***.</span></span> <span data-ttu-id="7719b-141">其會開始建置應用程式，並將其部署到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="7719b-141">It starts to build and deploy the application on to your PC.</span></span> <span data-ttu-id="7719b-142">應用程式會預設安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="7719b-142">The application will be installed in your PC by default.</span></span>

## <a name="testing-holographic-remoting-remote-application"></a><span data-ttu-id="7719b-143">測試全像攝影遠端處理應用程式</span><span class="sxs-lookup"><span data-stu-id="7719b-143">Testing Holographic Remoting remote application</span></span>

<span data-ttu-id="7719b-144">若要將您的電腦應用程式連線到 HoloLens 2，請遵循下列程序：</span><span class="sxs-lookup"><span data-stu-id="7719b-144">To connect your PC application to your HoloLens 2, follow the below process:</span></span>

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a><span data-ttu-id="7719b-145">1.在 HoloLens 2 裝置上安裝遠端播放程式應用程式</span><span class="sxs-lookup"><span data-stu-id="7719b-145">1. Install the Remoting Player application on HoloLens 2 device</span></span>

* <span data-ttu-id="7719b-146">在您的 HoloLens 2 上，瀏覽市集應用程式並搜尋「遠端播放程式」。</span><span class="sxs-lookup"><span data-stu-id="7719b-146">On your HoloLens 2, visit the Store app and search for "**Remoting Player**."</span></span>
* <span data-ttu-id="7719b-147">選取**遠端處理播放程式**應用程式。</span><span class="sxs-lookup"><span data-stu-id="7719b-147">Select the **Remoting Player** app.</span></span>
* <span data-ttu-id="7719b-148">請點選 [安裝] 來下載並安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="7719b-148">Tap **Install** to download and install the app.</span></span>

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a><span data-ttu-id="7719b-149">2.將全像攝影遠端處理電腦應用程式連線到遠端播放程式</span><span class="sxs-lookup"><span data-stu-id="7719b-149">2. Connect the Holographic remoting PC app to the Remoting Player</span></span>

* <span data-ttu-id="7719b-150">啟動 HoloLens 上的**遠端播放程式**。</span><span class="sxs-lookup"><span data-stu-id="7719b-150">Start the **Remoting Player** on your HoloLens.</span></span>
* <span data-ttu-id="7719b-151">記下 HoloLens 的 **IP 位址**。</span><span class="sxs-lookup"><span data-stu-id="7719b-151">Take note of the HoloLens **IP address**.</span></span> <span data-ttu-id="7719b-152">**遠端播放程式**會在啟動時，將其顯示為全像投影。</span><span class="sxs-lookup"><span data-stu-id="7719b-152">It will be displayed as a hologram by the **Remoting Player** as soon as it launches.</span></span>
* <span data-ttu-id="7719b-153">在您的電腦上開啟全像攝影遠端處理電腦應用程式。</span><span class="sxs-lookup"><span data-stu-id="7719b-153">Open the Holographic Remoting PC application on your PC.</span></span>
* <span data-ttu-id="7719b-154">啟動應用程式之後，輸入 **IP 位址**，然後按一下 [連線] 按鈕以進行連線。</span><span class="sxs-lookup"><span data-stu-id="7719b-154">Once the application is launched, enter the **IP address** and click on the **Connect**  button to connect.</span></span>

## <a name="congratulations"></a><span data-ttu-id="7719b-155">恭喜！</span><span class="sxs-lookup"><span data-stu-id="7719b-155">Congratulations</span></span>

<span data-ttu-id="7719b-156">在本教學課程中，您已了解如何建立全像攝影遠端處理應用程式，並在任何時間點連線 HoloLens 2，進而提供一種在混合實境中將 3D 內容視覺化的方式。</span><span class="sxs-lookup"><span data-stu-id="7719b-156">In this tutorial, you learned how to create a Holographic Remoting remote app and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span> <span data-ttu-id="7719b-157">當 HoloLens 連線到全像攝影遠端處理電腦應用程式之後，您應該會看到混合實境體驗串流至您的 HoloLens 2 裝置。</span><span class="sxs-lookup"><span data-stu-id="7719b-157">Once the HoloLens connected to the Holographic Remoting PC application, you should see the mixed reality experience streaming into your HoloLens 2 device.</span></span>
