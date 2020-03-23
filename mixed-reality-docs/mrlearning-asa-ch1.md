---
title: Azure Spatial Anchor 教學課程 - 1。 開始使用 Azure Spatial Anchors
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: fa0ebc409fa38f664bdd0966906c6fd77f7a6081
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376145"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="8ab29-105">1.開始使用 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="8ab29-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="8ab29-106">概觀</span><span class="sxs-lookup"><span data-stu-id="8ab29-106">Overview</span></span>

<span data-ttu-id="8ab29-107">歡迎使用第二個系列的 HoloLens 2 教學課程。</span><span class="sxs-lookup"><span data-stu-id="8ab29-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="8ab29-108">在此三個部分的教學課程系列中，您將了解 Azure Spatial Anchors 的基本概念。</span><span class="sxs-lookup"><span data-stu-id="8ab29-108">In this three-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="8ab29-109">在第一個教學課程：[開始使用 Azure Spatial Anchors](mrlearning-asa-ch1.md) 中，您將探索啟動和停止 Azure 工作階段，以及在單一裝置上建立、上傳和下載 Azure 錨點所需的各種步驟。</span><span class="sxs-lookup"><span data-stu-id="8ab29-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="8ab29-110">在第二個教學課程：[儲存、擷取和共用 Azure Spatial Anchors](mrlearning-asa-ch2.md) 中，您將了解如何藉由將錨點資訊儲存至 HoloLens 2 的儲存體，來將 Azure Spatial Anchors 儲存到多個應用程式工作階段，以及如何將此錨點資訊與其他裝置共用，使多個裝置的錨點一致。</span><span class="sxs-lookup"><span data-stu-id="8ab29-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="8ab29-111">在第三個教學課程：[顯示 Azure Spatial Anchor 回饋](mrlearning-asa-ch3.md)中，您將了解如何在使用 Azure Spatial Anchors 時，向使用者提供錨點事件和狀態的意見反應。</span><span class="sxs-lookup"><span data-stu-id="8ab29-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="8ab29-112">目標</span><span class="sxs-lookup"><span data-stu-id="8ab29-112">Objectives</span></span>

* <span data-ttu-id="8ab29-113">了解 HoloLens 2 的 Azure Spatial Anchors 開發基本概念</span><span class="sxs-lookup"><span data-stu-id="8ab29-113">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="8ab29-114">建立、上傳及下載空間錨點</span><span class="sxs-lookup"><span data-stu-id="8ab29-114">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8ab29-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="8ab29-115">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="8ab29-116">如果您尚未完成[入門教學課程](mrlearning-base.md)系列，建議您先完成這些教學課程。</span><span class="sxs-lookup"><span data-stu-id="8ab29-116">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="8ab29-117">已[安裝正確工具](install-the-tools.md)的 Windows 10 電腦</span><span class="sxs-lookup"><span data-stu-id="8ab29-117">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="8ab29-118">Windows 10 SDK 10.0.18362.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="8ab29-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="8ab29-119">基本的 C# 程式設計能力</span><span class="sxs-lookup"><span data-stu-id="8ab29-119">Some basic C# programming ability</span></span>
* <span data-ttu-id="8ab29-120">已[針對開發而設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置</span><span class="sxs-lookup"><span data-stu-id="8ab29-120">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="8ab29-121"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，已安裝 Unity 2019.2，且已新增通用 Windows 平台組建支援模組</span><span class="sxs-lookup"><span data-stu-id="8ab29-121"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="8ab29-122">完成[建立空間錨點資源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)區段，其位於[教學課程：建立使用 Azure Spatial Anchors 的 Unity HoloLens 應用程式](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)。</span><span class="sxs-lookup"><span data-stu-id="8ab29-122">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8ab29-123">本教學課程系列的建議 Unity 版本是 Unity 2019.2. X。</span><span class="sxs-lookup"><span data-stu-id="8ab29-123">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="8ab29-124">這個版本能取代上述連結之必要條件中所述的任何 Unity 版本需求或建議。</span><span class="sxs-lookup"><span data-stu-id="8ab29-124">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="8ab29-125">建立 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="8ab29-125">Creating the Unity project</span></span>
<!-- TODO: Consider renaming to 'Creating and preparing the Unity scene and project'-->

<span data-ttu-id="8ab29-126">在本節中，您將建立新的 Unity 專案，並使該專案準備好進行 MRTK 開發。</span><span class="sxs-lookup"><span data-stu-id="8ab29-126">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="8ab29-127">為此，請先遵循[初始化您的專案和第一個應用程式](mrlearning-base-ch1.md) (但不包括[對您的裝置建置應用程式](mrlearning-base-ch1.md#build-your-application-to-your-device)的指示)，其中包括下列步驟：</span><span class="sxs-lookup"><span data-stu-id="8ab29-127">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="8ab29-128">[建立新的 Unity 專案](mrlearning-base-ch1.md#create-new-unity-project)，並為其提供適當的名稱，例如「MRTK 教學課程」  。</span><span class="sxs-lookup"><span data-stu-id="8ab29-128">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*.</span></span>

2. [<span data-ttu-id="8ab29-129">設定適用於 Windows Mixed Reality 的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="8ab29-129">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="8ab29-130">匯入 TextMesh Pro 基本資源</span><span class="sxs-lookup"><span data-stu-id="8ab29-130">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="8ab29-131">匯入混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="8ab29-131">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="8ab29-132">設定用於混合實境工具組的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="8ab29-132">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="8ab29-133">[將 Mixed Reality 工具組新增至 Unity 場景](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)並為場景提供適當的名稱，例如 AzureSpatialAnchors </span><span class="sxs-lookup"><span data-stu-id="8ab29-133">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="8ab29-134">然後遵循[如何設定混合實境工具組設定檔 (變更空間感知顯示選項)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) 的指示，將場景的 MRTK 組態設定檔變更為 **DefaultHoloLens2ConfigurationProfile**，並將空間感知網格的顯示選項變更為 [遮蔽]  。</span><span class="sxs-lookup"><span data-stu-id="8ab29-134">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="8ab29-135">如上方連結：[設定用於混合實境工具組的 Unity 專案](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)中所述的指示，強烈建議您不要為 Unity 啟用 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="8ab29-135">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="8ab29-136">新增內建的 Unity 套件</span><span class="sxs-lookup"><span data-stu-id="8ab29-136">Adding inbuilt Unity packages</span></span>
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

<span data-ttu-id="8ab29-137">在本節中，您將安裝 Unity 的內建 AR Foundation 套件，因為您在下一節匯入 Azure Spatial Anchors SDK 時會需要此套件。</span><span class="sxs-lookup"><span data-stu-id="8ab29-137">In this section, you will install Unity's inbuilt AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

<span data-ttu-id="8ab29-138">在 Unity 功能表中，選取 [視窗]   >  **[套件管理員]** ：</span><span class="sxs-lookup"><span data-stu-id="8ab29-138">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="8ab29-140">可能需要幾秒鐘的時間，AR Foundation 套件才會出現在清單中。</span><span class="sxs-lookup"><span data-stu-id="8ab29-140">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

<span data-ttu-id="8ab29-141">在 [套件管理員] 視窗中選取 [AR Foundation]  ，然後按一下 [安裝]  按鈕來安裝套件：</span><span class="sxs-lookup"><span data-stu-id="8ab29-141">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="8ab29-143">匯入教學課程資產</span><span class="sxs-lookup"><span data-stu-id="8ab29-143">Importing the tutorial assets</span></span>

<span data-ttu-id="8ab29-144">下載並**依列出順序**來**匯入**下列 Unity 自訂套件：</span><span class="sxs-lookup"><span data-stu-id="8ab29-144">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="8ab29-145">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (2.1.1 版)</span><span class="sxs-lookup"><span data-stu-id="8ab29-145">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
* [<span data-ttu-id="8ab29-146">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span><span class="sxs-lookup"><span data-stu-id="8ab29-146">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
* [<span data-ttu-id="8ab29-147">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="8ab29-147">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="8ab29-148">如需有關如何匯入 Unity 自訂套件的提示，您可以參閱[匯入混合實境工具組](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) 的指示。</span><span class="sxs-lookup"><span data-stu-id="8ab29-148">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="8ab29-149">匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：</span><span class="sxs-lookup"><span data-stu-id="8ab29-149">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="8ab29-151">建立和準備場景</span><span class="sxs-lookup"><span data-stu-id="8ab29-151">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="8ab29-152">在本節中，您將藉由新增一些教學課程 Prefab 來準備場景。</span><span class="sxs-lookup"><span data-stu-id="8ab29-152">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="8ab29-153">在 [專案] 視窗中，瀏覽至 [資產]   > [MRTK.Tutorials.AzureSpatialAnchors]   > [Prefab]  資料夾。</span><span class="sxs-lookup"><span data-stu-id="8ab29-153">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="8ab29-154">按住 CTRL 鍵並按一下 [ButtonParent]  、[DebugWindow]  、[Instructions]  和 [ParentAnchor]  以選取四個 Prefab：</span><span class="sxs-lookup"><span data-stu-id="8ab29-154">While holding down the CTRL button, click on **ButtonParent**, **DebugWindow**, **Instructions**, and **ParentAnchor** to select the four prefabs:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

<span data-ttu-id="8ab29-156">選取四個 Prefab 之後，將其拖曳到 [階層] 視窗中，即可新增至場景：</span><span class="sxs-lookup"><span data-stu-id="8ab29-156">With the four prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

<span data-ttu-id="8ab29-158">若要將焦點放在場景中的物件上，您可以按兩下 ParentAnchor 物件，然後再次將場景稍微縮小：</span><span class="sxs-lookup"><span data-stu-id="8ab29-158">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> <span data-ttu-id="8ab29-160">如果您發現場景中的大圖示 (例如大型邊框的 'T' 圖示) 會造成干擾，您可以藉由將 <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">Gizmo 切換</a>到關閉位置來將其隱藏。</span><span class="sxs-lookup"><span data-stu-id="8ab29-160">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="8ab29-161">設定按鈕以操作場景</span><span class="sxs-lookup"><span data-stu-id="8ab29-161">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="8ab29-162">在本節中，您將在場景中新增指令碼來建立一系列的按鈕事件，以示範本機錨點和 Azure Spatial Anchors 在應用程式中的行為基礎。</span><span class="sxs-lookup"><span data-stu-id="8ab29-162">In this section, you will add scripts into the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a><span data-ttu-id="8ab29-163">1.設定 Pressable Button Holo Lens 2 (指令碼) 元件</span><span class="sxs-lookup"><span data-stu-id="8ab29-163">1. Configure the Pressable Button Holo Lens 2 (Script) component</span></span>

<span data-ttu-id="8ab29-164">在 [階層] 視窗中，展開 **ButtonParent** 物件，然後選取名為 **StartAzureSession**的第一個子物件：</span><span class="sxs-lookup"><span data-stu-id="8ab29-164">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

<span data-ttu-id="8ab29-166">在 [偵測器] 視窗中，找出 **Pressable Button Holo Lens 2 (指令碼)** 元件，然後按一下 [+]  圖示，將新的事件接聽程式新增至 **Button Pressed ()** 事件：</span><span class="sxs-lookup"><span data-stu-id="8ab29-166">In the Inspector window, locate the **Pressable Button Holo Lens 2 (Script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

<span data-ttu-id="8ab29-168">在 [階層] 視窗中仍選取 StartAzureSession 物件的情況下，按一下 **ParentAnchor** 物件並將其從 [階層] 視窗拖曳至您剛才所新增事件接聽程式的空白 [無 (物件)]  欄位，讓 ParentAnchor 物件可以從此按鈕接聽按下按鈕的事件：</span><span class="sxs-lookup"><span data-stu-id="8ab29-168">With the StartAzureSession object still selected in the Hierarchy window, click-and-drag the **ParentAnchor** object from the Hierarchy window into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

<span data-ttu-id="8ab29-170">按一下相同事件接聽程式的 [無函式]  下拉式清單，然後選取 [AnchorModuleScript]   > [StartAzureSession ()]  ，將 StartAzureSession () 函式設定為從此按鈕引發「按下按鈕」事件時所觸發的動作：</span><span class="sxs-lookup"><span data-stu-id="8ab29-170">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a><span data-ttu-id="8ab29-172">2.設定 Interactable (指令碼) 元件</span><span class="sxs-lookup"><span data-stu-id="8ab29-172">2. Configure the Interactable (Script) component</span></span>

<span data-ttu-id="8ab29-173">在 [階層] 視窗中仍然選取 StartAzureSession 物件的情況下，在 [偵測器] 視窗中找出 **Interactable (指令碼)** 元件，並針對 **OnClick ()** 事件重複上述步驟 1 中的相同程序：</span><span class="sxs-lookup"><span data-stu-id="8ab29-173">With the StartAzureSession object still selected in the Hierarchy window, in the Inspector window, locate the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a><span data-ttu-id="8ab29-175">3.設定其餘按鈕</span><span class="sxs-lookup"><span data-stu-id="8ab29-175">3. Configure the remaining buttons</span></span>

<span data-ttu-id="8ab29-176">針對其餘的每個按鈕，完成上述步驟 1 和 2 中所述的程序，將函式指派給 **Button Pressed ()** 和 **OnClick ()** 事件：</span><span class="sxs-lookup"><span data-stu-id="8ab29-176">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the **Button Pressed ()** and **OnClick ()** events:</span></span>

* <span data-ttu-id="8ab29-177">針對 **StopAzureSession** 物件，請指派 AnchorModuleScript > **StopAzureSession ()** 函式。</span><span class="sxs-lookup"><span data-stu-id="8ab29-177">For the **StopAzureSession** object, assign the AnchorModuleScript > **StopAzureSession ()** function.</span></span>
* <span data-ttu-id="8ab29-178">針對 **CreateAzureAnchor** 物件，請指派 AnchorModuleScript > **CreateAzureAnchor ()** 函式，</span><span class="sxs-lookup"><span data-stu-id="8ab29-178">For the **CreateAzureAnchor** object, assign the AnchorModuleScript > **CreateAzureAnchor ()** function,</span></span>
  * <span data-ttu-id="8ab29-179">然後將 **ParentAnchor** 再次拖曳到空白的 [無 (遊戲)]  欄位中。</span><span class="sxs-lookup"><span data-stu-id="8ab29-179">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="8ab29-180">針對 **RemoveLocalAnchor** 物件，請指派 AnchorModuleScript > **RemoveLocalAnchor ()** 函式，</span><span class="sxs-lookup"><span data-stu-id="8ab29-180">For the **RemoveLocalAnchor** object, assign the AnchorModuleScript > **RemoveLocalAnchor ()** function,</span></span>
  * <span data-ttu-id="8ab29-181">然後將 **ParentAnchor** 再次拖曳到空白的 [無 (遊戲)]  欄位中。</span><span class="sxs-lookup"><span data-stu-id="8ab29-181">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="8ab29-182">針對 **FindAzureAnchor** 物件，請指派 AnchorModuleScript > **FindAzureAnchor ()** 函式。</span><span class="sxs-lookup"><span data-stu-id="8ab29-182">For the **FindAzureAnchor** object, assign the AnchorModuleScript > **FindAzureAnchor ()** function.</span></span>
* <span data-ttu-id="8ab29-183">針對 **DeleteAzureAnchor** 物件，請指派 AnchorModuleScript > **DeleteAzureAnchor ()** 函式。</span><span class="sxs-lookup"><span data-stu-id="8ab29-183">For the **DeleteAzureAnchor** object, assign the AnchorModuleScript > **DeleteAzureAnchor ()** function.</span></span>

### <a name="4-connect-the-scene-to-the-azure-resource"></a><span data-ttu-id="8ab29-184">4.將場景連線至 Azure 資源</span><span class="sxs-lookup"><span data-stu-id="8ab29-184">4. Connect the scene to the Azure resource</span></span>

<span data-ttu-id="8ab29-185">在 [階層] 視窗中，選取 **ParentAnchor** 物件，然後在 [偵測器] 視窗中，向下瀏覽至 **Spatial Anchor Manager (指令碼)** 元件。</span><span class="sxs-lookup"><span data-stu-id="8ab29-185">In the Hierarchy window, select the **ParentAnchor** object and in the Inspector window, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

<span data-ttu-id="8ab29-186">然後，在 [認證]  區段中，將您在本教學課程[必要條件](mrlearning-asa-ch1.md#prerequisites)中所建立的 Spatial Anchors 帳戶識別碼和金鑰，貼入對應的 [Spatial Anchors 帳戶識別碼]  和 [Spatial Anchors 帳戶金鑰]  欄位：</span><span class="sxs-lookup"><span data-stu-id="8ab29-186">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key, which you created as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites), into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="8ab29-188">嘗試 Azure Spatial Anchors 的基本行為</span><span class="sxs-lookup"><span data-stu-id="8ab29-188">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="8ab29-189">現在，您的場景已設定為示範 Azure Spatial Anchors 的基本概念，您可以開始部署應用程式來搶先體驗 firsthand。</span><span class="sxs-lookup"><span data-stu-id="8ab29-189">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="8ab29-190">1.新增額外的必要功能</span><span class="sxs-lookup"><span data-stu-id="8ab29-190">1. Add additional required capabilities</span></span>

<span data-ttu-id="8ab29-191">在 Unity 功能表中，選取 [編輯]   > [專案設定...]  來開啟 [玩家設定] 視窗：</span><span class="sxs-lookup"><span data-stu-id="8ab29-191">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

<span data-ttu-id="8ab29-193">在 [玩家設定] 視窗中選取 [玩家]  ，然後選取 [發佈設定]  ：</span><span class="sxs-lookup"><span data-stu-id="8ab29-193">In the Player Settings window, select **Player** and then **Publishing Settings**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

<span data-ttu-id="8ab29-195">在 [發佈設定]  中，向下捲動至 [功能]  區段，然後再次確認您在教學課程開頭建立專案時所啟用的 **InternetClient**、**Microphone** 和 **SpatialPerception** 功能是否皆已啟用。</span><span class="sxs-lookup"><span data-stu-id="8ab29-195">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="8ab29-196">然後，啟用 **InternetClientServer**、**PrivateNetworkClientServer**、**RemovableStorage**和 **Webcam** 功能：</span><span class="sxs-lookup"><span data-stu-id="8ab29-196">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, and **Webcam** capabilities:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="8ab29-198">2.將應用程式部署至 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="8ab29-198">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="8ab29-199">Azure Spatial Anchors 無法在 Unity 中執行，因此若要測試 Azure Spatial Anchors 功能，您必須將專案部署至您的裝置。</span><span class="sxs-lookup"><span data-stu-id="8ab29-199">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="8ab29-200">如需有關如何建立 Unity 專案並將其部署至 HoloLens 2 的提示，您可以參閱[對您的裝置建置應用程式](mrlearning-base-ch1.md#build-your-application-to-your-device)的指示。</span><span class="sxs-lookup"><span data-stu-id="8ab29-200">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="8ab29-201">3.在 HoloLens 2 上執行應用程式，並遵循應用程式內的指示</span><span class="sxs-lookup"><span data-stu-id="8ab29-201">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="8ab29-202">Azure Spatial Anchors 會使用網際網路來儲存和載入錨點資料，因此請確定您的裝置已連線到網際網路。</span><span class="sxs-lookup"><span data-stu-id="8ab29-202">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="8ab29-203">當應用程式在您的裝置上執行時，請遵循 Azure Spatial Anchor 教學課程指示面板上顯示的螢幕指示：</span><span class="sxs-lookup"><span data-stu-id="8ab29-203">When the application is running on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="8ab29-205">錨點體驗</span><span class="sxs-lookup"><span data-stu-id="8ab29-205">Anchoring an experience</span></span>

<span data-ttu-id="8ab29-206">在前面幾節中，您已了解 Azure Spatial Anchors 的基本概念。</span><span class="sxs-lookup"><span data-stu-id="8ab29-206">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="8ab29-207">我們使用了立方體和連結的錨點來呈現及視覺化父遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="8ab29-207">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="8ab29-208">在本節中，您將了解如何藉由將整個體驗放在 ParentAnchor 物件的子系，來為其建立錨點。</span><span class="sxs-lookup"><span data-stu-id="8ab29-208">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

### <a name="1-add-the-rocket-launcher-experience"></a><span data-ttu-id="8ab29-209">1.新增火箭發射器的體驗</span><span class="sxs-lookup"><span data-stu-id="8ab29-209">1. Add the Rocket Launcher experience</span></span>

<span data-ttu-id="8ab29-210">在 [專案] 視窗中，流覽至 [資產]   > [MRTK.Tutorials.GettingStarted]   > [Prefabs]   > [RocketLauncher]  資料夾，並選取 **RocketLauncher_Complete** Prefab：</span><span class="sxs-lookup"><span data-stu-id="8ab29-210">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder and select the **RocketLauncher_Complete** prefab:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

<span data-ttu-id="8ab29-212">在仍選取 RocketLauncher_Complete Prefab 的情況下，將其拖曳至 [階層] 視窗中 **ParentAnchor** 物件的上方，使其成為 ParentAnchor 物件的子系：</span><span class="sxs-lookup"><span data-stu-id="8ab29-212">With the RocketLauncher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy window to make it a child of the ParentAnchor object:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a><span data-ttu-id="8ab29-214">2.重新放置火箭發射器的體驗</span><span class="sxs-lookup"><span data-stu-id="8ab29-214">2. Reposition the Rocket Launcher experience</span></span>

<span data-ttu-id="8ab29-215">將 **RocketLauncher_Complete** 物件的位置、旋轉和規模調整為適當的規模和方向，同時確保 **ParentAnchor** 物件仍為公開狀態，例如：</span><span class="sxs-lookup"><span data-stu-id="8ab29-215">Position, rotate, and scale the **RocketLauncher_Complete** object to a suitable scale and orientation, while also ensuring the **ParentAnchor** object is still exposed, for example:</span></span>

* <span data-ttu-id="8ab29-216">變形**位置** X = 0、Y = 0、Z = 3.75</span><span class="sxs-lookup"><span data-stu-id="8ab29-216">Transform **Position** X = 0, Y = 0, Z = 3.75</span></span>
* <span data-ttu-id="8ab29-217">變形**旋轉** X = 0、Y = 90、Z = 0</span><span class="sxs-lookup"><span data-stu-id="8ab29-217">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="8ab29-218">變形**縮放** X = 10、Y = 10、Z = 10</span><span class="sxs-lookup"><span data-stu-id="8ab29-218">Transform **Scale** X = 10, Y = 10, Z = 10</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

<span data-ttu-id="8ab29-220">在應用程式中，使用者現在可以藉由移動立方體來重新放置整個火箭發射器的體驗。</span><span class="sxs-lookup"><span data-stu-id="8ab29-220">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

> [!TIP]
> <span data-ttu-id="8ab29-221">有各種不同的使用者體驗流程可用於重新置放體驗，包括使用重新置放物件 (例如本教學課程中使用的立方體)、使用按鈕來切換環繞體驗的周框方塊、使用位置和旋轉 gizmo 等等。</span><span class="sxs-lookup"><span data-stu-id="8ab29-221">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="8ab29-222">恭喜！</span><span class="sxs-lookup"><span data-stu-id="8ab29-222">Congratulations</span></span>

<span data-ttu-id="8ab29-223">在本教學課程中，您已了解 Azure Spatial Anchors 的基本概念。</span><span class="sxs-lookup"><span data-stu-id="8ab29-223">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="8ab29-224">本教學課程提供了您幾個按鈕，讓您探索啟動和停止 Azure Spatial Anchors 工作階段，以及在單一裝置上建立、上傳和下載 Azure Spatial Anchors 所需的各種步驟。</span><span class="sxs-lookup"><span data-stu-id="8ab29-224">The tutorial provided you with several buttons that let you explore the various steps required to start and stop an Azure Spatial Anchors session and create, upload and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="8ab29-225">在下一個課程中，您將了解如何將 Azure 錨點識別碼儲存至 HoloLens 2 以便擷取 (即使在重新啟動應用程式之後)，以及如何在多個裝置之間傳輸錨點識別碼以達到空間對齊。</span><span class="sxs-lookup"><span data-stu-id="8ab29-225">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="8ab29-226">下一課：2.儲存、擷取和共用 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="8ab29-226">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)
