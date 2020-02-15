---
title: Azure 空間錨點教學課程-1。 開始使用 Azure 空間錨點
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 21883e95e92f8808bcf270e6d8091f31933ab6fa
ms.sourcegitcommit: a580166a19294f835b8e09c780f663f228dd5de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77250811"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="41d7b-105">1. 開始使用 Azure 空間錨點</span><span class="sxs-lookup"><span data-stu-id="41d7b-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="41d7b-106">概觀</span><span class="sxs-lookup"><span data-stu-id="41d7b-106">Overview</span></span>

<span data-ttu-id="41d7b-107">歡迎使用第二系列的 HoloLens 2 教學課程。</span><span class="sxs-lookup"><span data-stu-id="41d7b-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="41d7b-108">在這三部分的教學課程系列中，您將瞭解 Azure 空間錨點的基本概念。</span><span class="sxs-lookup"><span data-stu-id="41d7b-108">In this three-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="41d7b-109">在第一個教學課程中，[開始使用 Azure 空間錨點](mrlearning-asa-ch1.md)，您將探索啟動和停止 azure 會話，以及在單一裝置上建立、上傳和下載 azure 錨點所需的各種步驟。</span><span class="sxs-lookup"><span data-stu-id="41d7b-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="41d7b-110">在第二個教學課程中，[儲存、抓取和共用 Azure 空間錨點](mrlearning-asa-ch2.md)，您將瞭解如何藉由將錨點資訊儲存至 HoloLens 2 的儲存體，來將 Azure 空間錨點儲存到多個應用程式會話，以及如何將此錨點資訊與其他裝置共用，以進行多重裝置錨定的對齊。</span><span class="sxs-lookup"><span data-stu-id="41d7b-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="41d7b-111">在第三個教學課程中，[顯示 Azure 空間錨點意見](mrlearning-asa-ch3.md)反應，您將瞭解如何在使用 Azure 空間錨點時，為使用者提供錨點事件和狀態的相關意見反應。</span><span class="sxs-lookup"><span data-stu-id="41d7b-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="41d7b-112">目標</span><span class="sxs-lookup"><span data-stu-id="41d7b-112">Objectives</span></span>

* <span data-ttu-id="41d7b-113">瞭解使用 HoloLens 2 的 Azure 空間錨點進行開發的基本概念</span><span class="sxs-lookup"><span data-stu-id="41d7b-113">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="41d7b-114">建立、上傳及下載空間錨點</span><span class="sxs-lookup"><span data-stu-id="41d7b-114">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="41d7b-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="41d7b-115">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="41d7b-116">如果您尚未完成[快速入門教學](mrlearning-base.md)課程系列，建議您先完成這些教學課程。</span><span class="sxs-lookup"><span data-stu-id="41d7b-116">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="41d7b-117">[已安裝正確工具](install-the-tools.md)的 WINDOWS 10 電腦</span><span class="sxs-lookup"><span data-stu-id="41d7b-117">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="41d7b-118">Windows 10 SDK 10.0.18362.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="41d7b-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="41d7b-119">一些基本C#的程式設計能力</span><span class="sxs-lookup"><span data-stu-id="41d7b-119">Some basic C# programming ability</span></span>
* <span data-ttu-id="41d7b-120">[為開發設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置</span><span class="sxs-lookup"><span data-stu-id="41d7b-120">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="41d7b-121">已安裝 Unity 2019.2. X 的<a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity 中樞</a>，並已新增通用 Windows 平臺組建支援模組</span><span class="sxs-lookup"><span data-stu-id="41d7b-121"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="41d7b-122">完成[快速入門：建立使用 Azure 空間錨點的 Unity HoloLens 應用程式](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)教學課程中的[建立空間錨點資源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)一節。</span><span class="sxs-lookup"><span data-stu-id="41d7b-122">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="41d7b-123">本教學課程系列的建議 Unity 版本是 Unity 2019.2. X。</span><span class="sxs-lookup"><span data-stu-id="41d7b-123">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="41d7b-124">這會取代上述所連結之必要條件中所述的任何 Unity 版本需求或建議。</span><span class="sxs-lookup"><span data-stu-id="41d7b-124">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="41d7b-125">建立 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="41d7b-125">Creating the Unity project</span></span>
<!-- TODO: Consider renaming to 'Creating and preparing the Unity scene and project'-->

<span data-ttu-id="41d7b-126">在本節中，您將建立新的 Unity 專案，並準備好進行 MRTK 開發。</span><span class="sxs-lookup"><span data-stu-id="41d7b-126">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span> <span data-ttu-id="41d7b-127">為此，請遵循[初始化您的專案和第一個應用程式](mrlearning-base-ch1.md)，但不包括[組建您的應用程式到您的裝置](mrlearning-base-ch1.md#build-your-application-to-your-device)指示，其中包括下列步驟：</span><span class="sxs-lookup"><span data-stu-id="41d7b-127">For this, please follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="41d7b-128">[建立新的 Unity 專案](mrlearning-base-ch1.md#create-new-unity-project)，並為其提供適當的名稱，例如*MRTK 教學*課程。</span><span class="sxs-lookup"><span data-stu-id="41d7b-128">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*.</span></span>

2. [<span data-ttu-id="41d7b-129">設定適用于 Windows Mixed Reality 的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="41d7b-129">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="41d7b-130">匯入 TextMesh Pro 基本資源</span><span class="sxs-lookup"><span data-stu-id="41d7b-130">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="41d7b-131">匯入 Mixed Reality 工具組</span><span class="sxs-lookup"><span data-stu-id="41d7b-131">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="41d7b-132">設定混合現實工具組的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="41d7b-132">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="41d7b-133">[將 Mixed Reality 工具組新增至 Unity 場景](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)，並為場景提供適當的名稱，例如*AzureSpatialAnchors*</span><span class="sxs-lookup"><span data-stu-id="41d7b-133">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

> [!CAUTION]
> <span data-ttu-id="41d7b-134">如上述連結的[混合現實工具組指示設定 Unity 專案](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)中所述，MSBuild for Unity 可能不支援您將使用的所有 sdk，而且在啟用後可能會很難停用。</span><span class="sxs-lookup"><span data-stu-id="41d7b-134">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, MSBuild for Unity may not support all SDKs you will be using and can be challenging to disable after it has been enabled.</span></span> <span data-ttu-id="41d7b-135">因此，強烈建議您不要啟用適用于 Unity 的 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="41d7b-135">Consequently, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="41d7b-136">新增內建 Unity 套件</span><span class="sxs-lookup"><span data-stu-id="41d7b-136">Adding inbuilt Unity packages</span></span>
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

<span data-ttu-id="41d7b-137">在本節中，您將安裝 Unity 的內建 AR Foundation 套件，因為您將在下一節中匯入 Azure 空間錨點 SDK 所需。</span><span class="sxs-lookup"><span data-stu-id="41d7b-137">In this section, you will install Unity's inbuilt AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

<span data-ttu-id="41d7b-138">在 Unity 功能表中，選取 [Window > **封裝管理員** **]** ：</span><span class="sxs-lookup"><span data-stu-id="41d7b-138">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="41d7b-140">這可能需要幾秒鐘的時間，AR Foundation 封裝才會出現在清單中。</span><span class="sxs-lookup"><span data-stu-id="41d7b-140">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

<span data-ttu-id="41d7b-141">在 [套件管理員] 視窗中，選取 [ **AR Foundation** ]，然後按一下 [**安裝**] 按鈕來安裝套件：</span><span class="sxs-lookup"><span data-stu-id="41d7b-141">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="41d7b-143">匯入教學課程資產</span><span class="sxs-lookup"><span data-stu-id="41d7b-143">Importing the tutorial assets</span></span>

<span data-ttu-id="41d7b-144">依照**列出的順序**下載並匯**入**下列 Unity 自訂套件：</span><span class="sxs-lookup"><span data-stu-id="41d7b-144">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="41d7b-145">[AzureSpatialAnchors. unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) （2.1.1 版）</span><span class="sxs-lookup"><span data-stu-id="41d7b-145">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
* [<span data-ttu-id="41d7b-146">MRTK.HoloLens2 GettingStarted. 2.2.0.1. unitypackage</span><span class="sxs-lookup"><span data-stu-id="41d7b-146">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.2.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.2.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.2.0.1.unitypackage)
* [<span data-ttu-id="41d7b-147">MRTK.HoloLens2 AzureSpatialAnchors. 2.2.0.0. unitypackage</span><span class="sxs-lookup"><span data-stu-id="41d7b-147">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.2.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.2.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.2.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="41d7b-148">如需有關如何匯入 Unity 自訂套件的提醒，您可以參閱匯[入混合現實工具](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)組指示。</span><span class="sxs-lookup"><span data-stu-id="41d7b-148">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="41d7b-149">匯入教學課程資產之後，您的 [專案] 視窗看起來應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="41d7b-149">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="41d7b-151">建立和準備場景</span><span class="sxs-lookup"><span data-stu-id="41d7b-151">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="41d7b-152">在本節中，您將藉由新增一些教學課程 prefabs 來準備場景。</span><span class="sxs-lookup"><span data-stu-id="41d7b-152">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="41d7b-153">在 [專案] 視窗中，流覽至 [**資產**] [ > **MRTK]。教學課程. AzureSpatialAnchors** > **Prefabs**資料夾。</span><span class="sxs-lookup"><span data-stu-id="41d7b-153">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="41d7b-154">按住 CTRL 鍵時，按一下 [ **ButtonParent**]、[ **DebugWindow**]、[**指示**] 和 [ **ParentAnchor** ] 以選取四個 prefabs：</span><span class="sxs-lookup"><span data-stu-id="41d7b-154">While holding down the CTRL button, click on **ButtonParent**, **DebugWindow**, **Instructions**, and **ParentAnchor** to select the four prefabs:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

<span data-ttu-id="41d7b-156">在選取四個 prefabs 的情況下，將它們拖曳到 [階層] 視窗中，以將它們新增至場景：</span><span class="sxs-lookup"><span data-stu-id="41d7b-156">With the four prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

<span data-ttu-id="41d7b-158">若要將焦點放在場景中的物件上，您可以按兩下 [ParentAnchor] 物件，然後再稍微縮小一次：</span><span class="sxs-lookup"><span data-stu-id="41d7b-158">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> <span data-ttu-id="41d7b-160">比方說，如果您在場景中找到大圖示，例如，大框的 ' t ' 圖示會有干擾，您可以將<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">Gizmos 切換</a>到 off 位置來隱藏它們。</span><span class="sxs-lookup"><span data-stu-id="41d7b-160">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="41d7b-161">設定按鈕以操作場景</span><span class="sxs-lookup"><span data-stu-id="41d7b-161">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="41d7b-162">在本節中，您將在場景中新增腳本，以建立一系列的按鈕事件，以示範本機錨點和 Azure 空間錨點在應用程式中的行為。</span><span class="sxs-lookup"><span data-stu-id="41d7b-162">In this section, you will add scripts into the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a><span data-ttu-id="41d7b-163">1. 設定 Pressable 按鈕 Hololens 透鏡2（腳本）元件</span><span class="sxs-lookup"><span data-stu-id="41d7b-163">1. Configure the Pressable Button Holo Lens 2 (Script) component</span></span>

<span data-ttu-id="41d7b-164">在 [階層] 視窗中，展開 [ **ButtonParent** ] 物件，並選取名為**StartAzureSession**的第一個子物件：</span><span class="sxs-lookup"><span data-stu-id="41d7b-164">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

<span data-ttu-id="41d7b-166">在 [偵測器] 視窗中，找出 [ **Pressable] 按鈕 Hololens 透鏡2（腳本）** 元件，然後按一下 [ **+** ] 圖示，將新的事件接聽程式新增至**按下的按鈕（）** 事件：</span><span class="sxs-lookup"><span data-stu-id="41d7b-166">In the Inspector window, locate the **Pressable Button Holo Lens 2 (Script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

<span data-ttu-id="41d7b-168">在 [階層] 視窗中仍然選取 StartAzureSession 物件時，按一下並將**ParentAnchor**物件從 [階層] 視窗拖曳至您剛才加入之事件接聽程式的 [空的**無（物件）** ] 欄位中，讓 ParentAnchor 物件可以從這個按鈕接聽按鈕已按下的事件：</span><span class="sxs-lookup"><span data-stu-id="41d7b-168">With the StartAzureSession object still selected in the Hierarchy window, click-and-drag the **ParentAnchor** object from the Hierarchy window into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

<span data-ttu-id="41d7b-170">按一下同一個事件接聽程式的 [**無**函式] 下拉式清單，然後選取 [ **AnchorModuleScript** > **StartAzureSession （）** ]，將 StartAzureSession （）函數設定為從這個按鈕引發按鈕按下的事件時所觸發的動作：</span><span class="sxs-lookup"><span data-stu-id="41d7b-170">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a><span data-ttu-id="41d7b-172">2. 設定可互動（腳本）元件</span><span class="sxs-lookup"><span data-stu-id="41d7b-172">2. Configure the Interactable (Script) component</span></span>

<span data-ttu-id="41d7b-173">在 [階層] 視窗中，仍然選取 StartAzureSession 物件，在 [偵測器] 視窗中，找出 [**可互動（腳本）** ] 元件，並針對**OnClick （）** 事件重複上述步驟1中的相同進程：</span><span class="sxs-lookup"><span data-stu-id="41d7b-173">With the StartAzureSession object still selected in the Hierarchy window, in the Inspector window, locate the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a><span data-ttu-id="41d7b-175">3. 設定其餘按鈕</span><span class="sxs-lookup"><span data-stu-id="41d7b-175">3. Configure the remaining buttons</span></span>

<span data-ttu-id="41d7b-176">針對其餘的每個按鈕，完成上述步驟1和2中所述的程式，將函式指派給**按下按鈕的（）** 和**OnClick （）** 事件：</span><span class="sxs-lookup"><span data-stu-id="41d7b-176">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the **Button Pressed ()** and **OnClick ()** events:</span></span>

* <span data-ttu-id="41d7b-177">針對**StopAzureSession**物件，指派 AnchorModuleScript > **StopAzureSession （）** 函數。</span><span class="sxs-lookup"><span data-stu-id="41d7b-177">For the **StopAzureSession** object, assign the AnchorModuleScript > **StopAzureSession ()** function.</span></span>
* <span data-ttu-id="41d7b-178">針對**CreateAzureAnchor**物件，指派 AnchorModuleScript > **CreateAzureAnchor （）** 函數，</span><span class="sxs-lookup"><span data-stu-id="41d7b-178">For the **CreateAzureAnchor** object, assign the AnchorModuleScript > **CreateAzureAnchor ()** function,</span></span>
  * <span data-ttu-id="41d7b-179">然後再次將**ParentAnchor**拖曳至 [空的**無（遊戲物件）** ] 欄位。</span><span class="sxs-lookup"><span data-stu-id="41d7b-179">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="41d7b-180">針對**RemoveLocalAnchor**物件，指派 AnchorModuleScript > **RemoveLocalAnchor （）** 函數，</span><span class="sxs-lookup"><span data-stu-id="41d7b-180">For the **RemoveLocalAnchor** object, assign the AnchorModuleScript > **RemoveLocalAnchor ()** function,</span></span>
  * <span data-ttu-id="41d7b-181">然後再次將**ParentAnchor**拖曳至 [空的**無（遊戲物件）** ] 欄位。</span><span class="sxs-lookup"><span data-stu-id="41d7b-181">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="41d7b-182">針對**FindAzureAnchor**物件，指派 AnchorModuleScript > **FindAzureAnchor （）** 函數。</span><span class="sxs-lookup"><span data-stu-id="41d7b-182">For the **FindAzureAnchor** object, assign the AnchorModuleScript > **FindAzureAnchor ()** function.</span></span>
* <span data-ttu-id="41d7b-183">針對**DeleteAzureAnchor**物件，指派 AnchorModuleScript > **DeleteAzureAnchor （）** 函數。</span><span class="sxs-lookup"><span data-stu-id="41d7b-183">For the **DeleteAzureAnchor** object, assign the AnchorModuleScript > **DeleteAzureAnchor ()** function.</span></span>

### <a name="4-connect-the-scene-to-the-azure-resource"></a><span data-ttu-id="41d7b-184">4. 將場景連線至 Azure 資源</span><span class="sxs-lookup"><span data-stu-id="41d7b-184">4. Connect the scene to the Azure resource</span></span>

<span data-ttu-id="41d7b-185">在 [階層] 視窗中，選取 [ **ParentAnchor** ] 物件，然後在 [偵測器] 視窗中，向下流覽至 [**空間錨點管理員（腳本）** ] 元件。</span><span class="sxs-lookup"><span data-stu-id="41d7b-185">In the Hierarchy window, select the **ParentAnchor** object and in the Inspector window, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

<span data-ttu-id="41d7b-186">然後，在 [**認證**] 區段中，將您在本教學[課程必要條件](mrlearning-asa-ch1.md#prerequisites)中建立的空間錨點帳戶識別碼和金鑰貼到對應的 [**空間錨點帳戶識別碼**] 和 [**空間錨點帳戶金鑰**] 欄位中：</span><span class="sxs-lookup"><span data-stu-id="41d7b-186">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key, which you created as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites), into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="41d7b-188">嘗試 Azure 空間錨點的基本行為</span><span class="sxs-lookup"><span data-stu-id="41d7b-188">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="41d7b-189">您的場景已設定為示範 Azure 空間錨點的基本概念，現在可以部署應用程式，以便體驗 Azure 空間錨點搶先它。</span><span class="sxs-lookup"><span data-stu-id="41d7b-189">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="41d7b-190">1. 新增額外的必要功能</span><span class="sxs-lookup"><span data-stu-id="41d7b-190">1. Add additional required capabilities</span></span>

<span data-ttu-id="41d7b-191">在 Unity 功能表中，選取 **編輯** > **專案設定 ...**  以開啟 Player 設定 視窗：</span><span class="sxs-lookup"><span data-stu-id="41d7b-191">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

<span data-ttu-id="41d7b-193">在 [Player 設定] 視窗中，依序選取 [ **player** ] 和 [**發佈設定**]：</span><span class="sxs-lookup"><span data-stu-id="41d7b-193">In the Player Settings window, select **Player** and then **Publishing Settings**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

<span data-ttu-id="41d7b-195">在 [**發行設定**] 中，向下流覽至 [**功能**] 區段，然後再次檢查您在教學課程開頭建立專案時所啟用的**InternetClient**、**麥克風**和**SpatialPerception**功能是否已啟用。</span><span class="sxs-lookup"><span data-stu-id="41d7b-195">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="41d7b-196">然後，啟用**InternetClientServer**、 **PrivateNetworkClientServer**、 **RemovableStorage**和**網路**攝影機功能：</span><span class="sxs-lookup"><span data-stu-id="41d7b-196">Then, enabled the **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, and **Webcam** capabilities:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="41d7b-198">2. 將應用程式部署至 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="41d7b-198">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="41d7b-199">Azure 空間錨點無法在 Unity 中執行，因此若要測試 Azure 空間錨點功能，您必須將專案部署至您的裝置。</span><span class="sxs-lookup"><span data-stu-id="41d7b-199">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="41d7b-200">如需有關如何建立 Unity 專案並將其部署至 HoloLens 2 的提醒，您可以參閱將[您的應用程式建立至您的裝置](mrlearning-base-ch1.md#build-your-application-to-your-device)指示。</span><span class="sxs-lookup"><span data-stu-id="41d7b-200">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="41d7b-201">3. 在 HoloLens 2 上執行應用程式，並遵循應用程式內的指示</span><span class="sxs-lookup"><span data-stu-id="41d7b-201">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="41d7b-202">Azure 空間錨點會使用網際網路來儲存和載入錨定資料，因此請確定您的裝置已連線到網際網路。</span><span class="sxs-lookup"><span data-stu-id="41d7b-202">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="41d7b-203">當應用程式在您的裝置上執行時，請遵循 Azure 空間錨點教學課程指示面板上顯示的螢幕指示：</span><span class="sxs-lookup"><span data-stu-id="41d7b-203">When the application is running on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="41d7b-205">錨定體驗</span><span class="sxs-lookup"><span data-stu-id="41d7b-205">Anchoring an experience</span></span>

<span data-ttu-id="41d7b-206">在前面幾節中，您已瞭解 Azure 空間錨點的基本概念。</span><span class="sxs-lookup"><span data-stu-id="41d7b-206">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="41d7b-207">我們使用 cube 來呈現父遊戲物件，並使用連結的錨點將其視覺化。</span><span class="sxs-lookup"><span data-stu-id="41d7b-207">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="41d7b-208">在本節中，您將瞭解如何藉由將它放在 ParentAnchor 物件的子系，來錨定整個體驗。</span><span class="sxs-lookup"><span data-stu-id="41d7b-208">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

### <a name="1-add-the-rocket-launcher-experience"></a><span data-ttu-id="41d7b-209">1. 新增 Rocket 啟動器體驗</span><span class="sxs-lookup"><span data-stu-id="41d7b-209">1. Add the Rocket Launcher experience</span></span>

<span data-ttu-id="41d7b-210">在 [專案] 視窗中，流覽至 [**資產**] > **MRTK。教學課程. GettingStarted** > **Prefabs** > **RocketLauncher**資料夾，然後選取**RocketLauncher_Complete** prefab：</span><span class="sxs-lookup"><span data-stu-id="41d7b-210">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder and select the **RocketLauncher_Complete** prefab:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

<span data-ttu-id="41d7b-212">在仍選取 [RocketLauncher_Complete prefab] 的情況下，將其拖曳至 [階層] 視窗中的 [ **ParentAnchor** ] 物件上方，使其成為 ParentAnchor 物件的子系：</span><span class="sxs-lookup"><span data-stu-id="41d7b-212">With the RocketLauncher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy window to make it a child of the ParentAnchor object:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a><span data-ttu-id="41d7b-214">2. 重新置放 Rocket 啟動器體驗</span><span class="sxs-lookup"><span data-stu-id="41d7b-214">2. Reposition the Rocket Launcher experience</span></span>

<span data-ttu-id="41d7b-215">將**RocketLauncher_Complete**物件定位、旋轉和縮放至適當的縮放和方向，同時確保**ParentAnchor**物件仍會公開，例如：</span><span class="sxs-lookup"><span data-stu-id="41d7b-215">Position, rotate, and scale the **RocketLauncher_Complete** object to a suitable scale and orientation, while also ensuring the **ParentAnchor** object is still exposed, for example:</span></span>

* <span data-ttu-id="41d7b-216">轉換**位置**X = 1，Y = 0，Z = 3.75</span><span class="sxs-lookup"><span data-stu-id="41d7b-216">Transform **Position** X = 1, Y = 0, Z = 3.75</span></span>
* <span data-ttu-id="41d7b-217">轉換**旋轉**X = 0、Y = 90、Z = 0</span><span class="sxs-lookup"><span data-stu-id="41d7b-217">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="41d7b-218">轉換**小數值**X = 10，Y = 10，Z = 10</span><span class="sxs-lookup"><span data-stu-id="41d7b-218">Transform **Scale** X = 10, Y = 10, Z = 10</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

<span data-ttu-id="41d7b-220">在應用程式中，使用者現在可以藉由移動 cube 來重新放置整個 Rocket 啟動器的使用體驗。</span><span class="sxs-lookup"><span data-stu-id="41d7b-220">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

> [!TIP]
> <span data-ttu-id="41d7b-221">有各種不同的使用者體驗流程可進行重新置放的體驗，包括使用重新置放的物件（例如本教學課程中使用的 cube）、使用按鈕來切換環繞體驗的周框方塊、使用位置和旋轉gizmos，還有更多。</span><span class="sxs-lookup"><span data-stu-id="41d7b-221">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="41d7b-222">恭喜！</span><span class="sxs-lookup"><span data-stu-id="41d7b-222">Congratulations</span></span>

<span data-ttu-id="41d7b-223">在本教學課程中，您已瞭解 Azure 空間錨點的基本概念。</span><span class="sxs-lookup"><span data-stu-id="41d7b-223">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="41d7b-224">本教學課程提供您幾個按鈕，可讓您探索啟動和停止 Azure 空間錨點會話，以及在單一裝置上建立、上傳和下載 Azure 空間錨點所需的各種步驟。</span><span class="sxs-lookup"><span data-stu-id="41d7b-224">The tutorial provided you with several buttons that let you explore the various steps required to start and stop an Azure Spatial Anchors session and create, upload and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="41d7b-225">在下一課中，您將瞭解如何將 Azure 錨點識別碼儲存至 HoloLens 2 進行抓取，即使在重新開機應用程式之後，以及如何在多個裝置之間傳輸錨點識別碼以達成空間對齊。</span><span class="sxs-lookup"><span data-stu-id="41d7b-225">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="41d7b-226">下一課： 2. 儲存、正在抓取和共用 Azure 空間錨點</span><span class="sxs-lookup"><span data-stu-id="41d7b-226">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)
