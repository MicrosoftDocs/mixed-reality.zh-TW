---
title: Azure 空間錨點教學課程-1。 開始使用 Azure 空間錨點
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 861c42f9449fcb3cf038258af91088fc927941e5
ms.sourcegitcommit: f4812e1312c4751a22a2de56771c475b22a4ba24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2019
ms.locfileid: "74940956"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="8417f-105">1. 開始使用 Azure 空間錨點</span><span class="sxs-lookup"><span data-stu-id="8417f-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="8417f-106">概觀</span><span class="sxs-lookup"><span data-stu-id="8417f-106">Overview</span></span>

<span data-ttu-id="8417f-107">歡迎使用第二系列的 HoloLens 2 教學課程。</span><span class="sxs-lookup"><span data-stu-id="8417f-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="8417f-108">在這三部分的教學課程系列中，您將瞭解 Azure 空間錨點的基本概念。</span><span class="sxs-lookup"><span data-stu-id="8417f-108">In this three-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="8417f-109">在第一個教學課程中，[開始使用 Azure 空間錨點](mrlearning-asa-ch1.md)，您將探索啟動和停止 azure 會話，以及在單一裝置上建立、上傳和下載 azure 錨點所需的各種步驟。</span><span class="sxs-lookup"><span data-stu-id="8417f-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="8417f-110">在第二個教學課程中，[儲存、抓取和共用 Azure 空間錨點](mrlearning-asa-ch2.md)，您將瞭解如何藉由將錨點資訊儲存至 HoloLens 2 的儲存體，來將 Azure 空間錨點儲存到多個應用程式會話，以及如何將此錨點資訊與其他裝置共用，以進行多重裝置錨定的對齊。</span><span class="sxs-lookup"><span data-stu-id="8417f-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="8417f-111">在第三個教學課程中，[顯示 Azure 空間錨點意見](mrlearning-asa-ch3.md)反應，您將瞭解如何在使用 Azure 空間錨點時，為使用者提供錨點事件和狀態的相關意見反應。</span><span class="sxs-lookup"><span data-stu-id="8417f-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="8417f-112">目標</span><span class="sxs-lookup"><span data-stu-id="8417f-112">Objectives</span></span>

* <span data-ttu-id="8417f-113">瞭解使用 HoloLens 2 的 Azure 空間錨點進行開發的基本概念</span><span class="sxs-lookup"><span data-stu-id="8417f-113">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="8417f-114">建立、上傳及下載空間錨點</span><span class="sxs-lookup"><span data-stu-id="8417f-114">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8417f-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="8417f-115">Prerequisites</span></span>

* <span data-ttu-id="8417f-116">符合[快速入門：建立使用 Azure 空間錨點的 Unity HoloLens 應用程式](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)教學[課程的必要條件](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#prerequisites)一節中所列的需求。</span><span class="sxs-lookup"><span data-stu-id="8417f-116">Meet the requirements listed in the [Prerequisites](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#prerequisites) section of the  [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>
* <span data-ttu-id="8417f-117">完成[快速入門：建立使用 Azure 空間錨點的 Unity HoloLens 應用程式](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)教學課程中的[建立空間錨點資源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)一節。</span><span class="sxs-lookup"><span data-stu-id="8417f-117">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>
* <span data-ttu-id="8417f-118">如果您尚未完成[快速入門教學](mrlearning-base.md)課程系列，建議您先完成這些教學課程。</span><span class="sxs-lookup"><span data-stu-id="8417f-118">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="8417f-119">建立 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="8417f-119">Creating the Unity project</span></span>

<span data-ttu-id="8417f-120">在本節中，您將建立新的 Unity 專案，並針對 Windows Mixed Reality 進行設定。</span><span class="sxs-lookup"><span data-stu-id="8417f-120">In this section, you will create a new Unity project and configure it for Windows Mixed Reality.</span></span>

1. <span data-ttu-id="8417f-121">建立 Unity 專案，並為其提供適當的名稱，例如_Azure 空間錨點教學_課程。</span><span class="sxs-lookup"><span data-stu-id="8417f-121">Create a Unity project and give it a suitable name, for example, _Azure Spatial Anchors tutorial_.</span></span>

2. <span data-ttu-id="8417f-122">設定適用于 Windows Mixed Reality 的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="8417f-122">Configure the Unity project for Windows Mixed Reality.</span></span>

    >[!TIP]
    ><span data-ttu-id="8417f-123">如需有關如何建立 Unity 專案並針對 Windows Mixed Reality 進行設定的提醒，您可以參閱[初始化專案和第一個應用程式](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1)教學課程中的[建立新的 Unity 專案](mrlearning-base-ch1.md#create-new-unity-project)和設定適用于[windows mixed reality 的 unity 專案](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)一節，這是使用者入門[教學](mrlearning-base.md)課程系列的一部分。</span><span class="sxs-lookup"><span data-stu-id="8417f-123">For a reminder on how to create a Unity project and configure it for Windows Mixed Reality, you can refer to the [Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and the [Configure the Unity project for Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality) sections of the [Initializing your project and first application](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) tutorial which is part of the the [Getting started tutorials](mrlearning-base.md) series.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="8417f-124">新增內建 Unity 套件</span><span class="sxs-lookup"><span data-stu-id="8417f-124">Adding inbuilt Unity packages</span></span>

<span data-ttu-id="8417f-125">在本節中，您將會新增要在專案中使用的工具組和 Sdk 所需的內建 Unity 資產和套件。</span><span class="sxs-lookup"><span data-stu-id="8417f-125">In this section, you will add inbuilt Unity assets and packages required by the toolkits and SDKs you will be using in the project.</span></span>

1. <span data-ttu-id="8417f-126">匯入 TMP 基本資源。</span><span class="sxs-lookup"><span data-stu-id="8417f-126">Import TMP Essential Resources.</span></span>

    >[!NOTE]
    ><span data-ttu-id="8417f-127">我們正在新增此封裝，因為它是混合現實工具組的必要項。</span><span class="sxs-lookup"><span data-stu-id="8417f-127">We are adding this package because it is required by the Mixed Reality Toolkit.</span></span>

    <span data-ttu-id="8417f-128">在 Unity 功能表中，選取 [Window > **TextMeshPro** > 匯**入 TMP 基本資源** **]** 。</span><span class="sxs-lookup"><span data-stu-id="8417f-128">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-1.1.png)

    <span data-ttu-id="8417f-130">在 [匯入 Unity 封裝] 快顯視窗中，先確定已選取所有資產，方法是按一下 [**全部**] 按鈕，然後按一下 [匯**入**] 按鈕來匯入資產。</span><span class="sxs-lookup"><span data-stu-id="8417f-130">In the Import Unity Package pop-up window, first make sure all the assets are selected by clicking the **All** button, then import the assets by clicking the **Import** button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-1.2.png)

2. <span data-ttu-id="8417f-132">安裝 AR Foundation。</span><span class="sxs-lookup"><span data-stu-id="8417f-132">Install AR Foundation.</span></span>

    >[!NOTE]
    ><span data-ttu-id="8417f-133">我們會新增此封裝，因為 Azure 空間錨點 SDK 需要此套件。</span><span class="sxs-lookup"><span data-stu-id="8417f-133">We are adding this package because it is required by the Azure Spatial Anchors SDK.</span></span>

    <span data-ttu-id="8417f-134">在 Unity 功能表中，選取 [Window > **封裝管理員** **]** 。</span><span class="sxs-lookup"><span data-stu-id="8417f-134">In the Unity menu, select **Window** > **Package Manager**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-2.1.png)

    <span data-ttu-id="8417f-136">在 [套件管理員] 視窗中，選取 [ **AR Foundation** ]，然後按一下 [**安裝**] 按鈕來安裝封裝。</span><span class="sxs-lookup"><span data-stu-id="8417f-136">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button.</span></span>

    >[!IMPORTANT]
    ><span data-ttu-id="8417f-137">這可能需要幾秒鐘的時間，AR Foundation 封裝才會出現在清單中。</span><span class="sxs-lookup"><span data-stu-id="8417f-137">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-2.2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="8417f-139">匯入教學課程資產</span><span class="sxs-lookup"><span data-stu-id="8417f-139">Importing the tutorial assets</span></span>

<span data-ttu-id="8417f-140">在本節中，您將下載並匯入所有教學課程資產。</span><span class="sxs-lookup"><span data-stu-id="8417f-140">In this section, you will download and import all the tutorial assets.</span></span>

1. <span data-ttu-id="8417f-141">下載資產。</span><span class="sxs-lookup"><span data-stu-id="8417f-141">Download the assets.</span></span>

    * <span data-ttu-id="8417f-142">[AzureSpatialAnchors. unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) （版本2.0.0）</span><span class="sxs-lookup"><span data-stu-id="8417f-142">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (version 2.0.0)</span></span>
    * [<span data-ttu-id="8417f-143">MixedReality. 2.1.0. unitypackage。</span><span class="sxs-lookup"><span data-stu-id="8417f-143">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)
    * [<span data-ttu-id="8417f-144">MRTK.HoloLens2 GettingStarted. 2.1.0.1. unitypackage</span><span class="sxs-lookup"><span data-stu-id="8417f-144">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage)
    * [<span data-ttu-id="8417f-145">MRTK.HoloLens2 AzureSpatialAnchors. 2.1.0.1. unitypackage</span><span class="sxs-lookup"><span data-stu-id="8417f-145">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage)

2. <span data-ttu-id="8417f-146">匯入資產。</span><span class="sxs-lookup"><span data-stu-id="8417f-146">Import the assets.</span></span>

    <span data-ttu-id="8417f-147">在 Unity 功能表中，選取 **資產** > 匯**入套件** > **自訂封裝**...。</span><span class="sxs-lookup"><span data-stu-id="8417f-147">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.1.png)

    <span data-ttu-id="8417f-149">在 [匯入套件 ...]快顯視窗中，選取 [ **AzureSpatialAnchors] unitypackage** ，然後按一下 [**開啟**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="8417f-149">In the Import package... pop-up window, select the **AzureSpatialAnchors.unitypackage** and click the **Open** button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.2.png)

    <span data-ttu-id="8417f-151">在 [匯入 Unity 封裝] 快顯視窗中，先確定已選取所有資產，方法是按一下 [**全部**] 按鈕，然後按一下 [匯**入**] 按鈕來匯入資產。</span><span class="sxs-lookup"><span data-stu-id="8417f-151">In the Import Unity Package pop-up window, first make sure all the assets are selected by clicking the **All** button, then import the assets by clicking the **Import** button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.3.png)

    <span data-ttu-id="8417f-153">重複這些步驟來匯入其餘的資產套件。</span><span class="sxs-lookup"><span data-stu-id="8417f-153">Repeat these steps to import the remaining asset packages.</span></span> <span data-ttu-id="8417f-154">完成後，您的 Unity 專案的 [**資產**] 資料夾應該會包含這些子資料夾。</span><span class="sxs-lookup"><span data-stu-id="8417f-154">Once complete, your Unity project's **Assets** folder should contain these sub-folders.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.4.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="8417f-156">建立和準備場景</span><span class="sxs-lookup"><span data-stu-id="8417f-156">Creating and preparing the scene</span></span>

<span data-ttu-id="8417f-157">在本節中，您將藉由新增混合現實工具組和一些教學課程 prefabs 來建立和準備場景。</span><span class="sxs-lookup"><span data-stu-id="8417f-157">In this section, you will create and prepare the scene by adding the Mixed Reality Toolkit and some of the tutorial prefabs.</span></span>

1. <span data-ttu-id="8417f-158">建立新場景。</span><span class="sxs-lookup"><span data-stu-id="8417f-158">Create a new scene.</span></span>

    <span data-ttu-id="8417f-159">在 Unity 功能表中 **，選取 [** 檔案] > [**新場景**]。</span><span class="sxs-lookup"><span data-stu-id="8417f-159">In the Unity menu, select **File** > **New Scene**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.1.png)

    <span data-ttu-id="8417f-161">在 Unity 功能表中 **，選取** 檔案 > **另存**新檔 ...。</span><span class="sxs-lookup"><span data-stu-id="8417f-161">In the Unity menu, select **File** > **Save As...**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.2.png)

    <span data-ttu-id="8417f-163">在 [儲存場景] 快顯視窗中，流覽至專案的 [**幕後**] 資料夾，為您的場景提供適當的名稱（例如_ASATutorialScene_），然後按一下 [**儲存**] 按鈕來儲存場景。</span><span class="sxs-lookup"><span data-stu-id="8417f-163">In the Save Scene pop-up window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _ASATutorialScene_, and save the scene by clicking the **Save** button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.3.png)

    >[!TIP]
    ><span data-ttu-id="8417f-165">只要此場景位於專案的 [資產] 資料夾內，您就可以將它儲存在您喜歡的任何地方。</span><span class="sxs-lookup"><span data-stu-id="8417f-165">You can save the scene anywhere you like as long as it is inside the project's Assets folder.</span></span> <span data-ttu-id="8417f-166">不過，若要讓您的專案組織，通常建議將它儲存在專案的 [場景] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="8417f-166">However, to keep your project organized, it's generally recommended to save it in the project's Scenes folder.</span></span>

2. <span data-ttu-id="8417f-167">新增混合現實工具組。</span><span class="sxs-lookup"><span data-stu-id="8417f-167">Add the Mixed Reality Toolkit.</span></span>

    <span data-ttu-id="8417f-168">在 Unity 功能表中，選取 **混合現實工具**組， > **新增至場景並設定 ...** 。</span><span class="sxs-lookup"><span data-stu-id="8417f-168">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.1.png)

    <span data-ttu-id="8417f-170">在 [選取 MixedRealityToolkitConfigurationProfile] 快顯視窗中，按一下**DefaultHoloLens2ConfigurationProfile** ，將其設定為場景的 MRTK 設定檔。</span><span class="sxs-lookup"><span data-stu-id="8417f-170">In the Select MixedRealityToolkitConfigurationProfile pop-up window, click the **DefaultHoloLens2ConfigurationProfile** to set it as the scene's MRTK configuration profile.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.2.png)

    <span data-ttu-id="8417f-172">在 Unity 功能表中 **，選取** 檔案 > **儲存** 以儲存場景。</span><span class="sxs-lookup"><span data-stu-id="8417f-172">In the Unity menu, select **File** > **Save** to save the scene.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.3.png)

    >[!TIP]
    ><span data-ttu-id="8417f-174">當您進行本教學課程時，您可以使用鍵盤快速鍵 CTRL + S （macOS 上的 command + S）來快速儲存場景。</span><span class="sxs-lookup"><span data-stu-id="8417f-174">You can use the keyboard shortcut CTRL+S (command + S on macOS) to quickly save your scene as you are working through this tutorial.</span></span>

3. <span data-ttu-id="8417f-175">新增教學課程 prefabs。</span><span class="sxs-lookup"><span data-stu-id="8417f-175">Add the tutorial prefabs.</span></span>

    <span data-ttu-id="8417f-176">在 [專案] 面板中，流覽至 [**資產**] [ > **MRTK]。教學課程. AzureSpatialAnchors** > **Prefabs**資料夾。</span><span class="sxs-lookup"><span data-stu-id="8417f-176">In the Project panel, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="8417f-177">按住 CTRL 鍵（macOS 上的命令）時，按一下 [ **ButtonParent**]、[ **DebugWindow**] 和 [ **ParentAnchor** ] 以選取三個 prefabs。</span><span class="sxs-lookup"><span data-stu-id="8417f-177">While holding down the CTRL button (command on macOS), click on **ButtonParent**, **DebugWindow**, and **ParentAnchor** to select the three prefabs.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.1.png)

    <span data-ttu-id="8417f-179">在選取了三個 prefabs 的情況下，將它們拖曳到 [階層] 面板中，以將它們新增至場景。</span><span class="sxs-lookup"><span data-stu-id="8417f-179">With the three prefabs still selected, drag them into the Hierarchy panel to add them to the scene.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.2.png)

    <span data-ttu-id="8417f-181">若要將焦點放在場景中的物件上，您可以按兩下 [ParentAnchor] 物件，然後再稍微縮小一次。</span><span class="sxs-lookup"><span data-stu-id="8417f-181">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.3.png)

    >[!TIP]
    ><span data-ttu-id="8417f-183">比方說，如果您在場景中找到大圖示，例如，大框的 ' t ' 圖示會有干擾，您可以將<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">Gizmos 切換</a>到 off 位置來隱藏它們。</span><span class="sxs-lookup"><span data-stu-id="8417f-183">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="8417f-184">設定按鈕以操作場景</span><span class="sxs-lookup"><span data-stu-id="8417f-184">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="8417f-185">在本節中，您將在場景中新增 prefabs 和腳本，以建立一系列的按鈕，以示範本機錨點和 Azure 空間錨點在應用程式中的行為。</span><span class="sxs-lookup"><span data-stu-id="8417f-185">In this section, you will add prefabs and scripts into the scene to create a series of buttons that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

1. <span data-ttu-id="8417f-186">設定 Pressable 按鈕 Hololens 透鏡2（腳本）元件。</span><span class="sxs-lookup"><span data-stu-id="8417f-186">Configure the Pressable Button Holo Lens 2 (script) component.</span></span>

    <span data-ttu-id="8417f-187">在 [階層] 面板中，展開 [ **ButtonParent** ] 物件，並選取名為**StartAzureSession**的第一個子物件。</span><span class="sxs-lookup"><span data-stu-id="8417f-187">In the Hierarchy panel, expand the **ButtonParent** object and select the first child object named **StartAzureSession**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.1.png)

    <span data-ttu-id="8417f-189">在 [偵測器] 面板中，向下**Pressable 按鈕 Hololens 透鏡2（腳本）** 元件，然後按一下 [ **+** ] 圖示，將新的事件接聽程式新增至**按下的按鈕（）** 事件。</span><span class="sxs-lookup"><span data-stu-id="8417f-189">In the Inspector panel, scroll down to the **Pressable Button Holo Lens 2 (script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.2.png)

    <span data-ttu-id="8417f-191">在 [階層] 面板中仍選取 StartAzureSession 物件時，按一下-並將**ParentAnchor**物件從 [階層] 面板拖曳至您剛才加入之事件接聽程式的 [空的**無（物件）** ] 欄位中，讓 ParentAnchor 物件在此按鈕中聆聽已按下按鈕的事件。</span><span class="sxs-lookup"><span data-stu-id="8417f-191">With the StartAzureSession object still selected in the Hierarchy panel, click-and-drag the **ParentAnchor** object from the Hierarchy panel into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.3.png)

    <span data-ttu-id="8417f-193">按一下相同事件接聽程式的 [**無**函式] 下拉式清單，然後選取 [ **AnchorModuleScript** > **StartAzureSession （）** ]，將 StartAzureSession （）函數設定為從這個按鈕引發按鈕按下的事件時所觸發的動作。</span><span class="sxs-lookup"><span data-stu-id="8417f-193">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.4.png)

2. <span data-ttu-id="8417f-195">設定可互動（腳本）元件。</span><span class="sxs-lookup"><span data-stu-id="8417f-195">Configure the Interactable (script) component.</span></span>

    <span data-ttu-id="8417f-196">在 [階層] 面板中仍然選取 StartAzureSession 物件時，請在 [偵測器] 面板中，向下流覽至 [**可互動（腳本）** ] 元件，然後針對**OnClick （）** 事件重複上述步驟1中的相同進程。</span><span class="sxs-lookup"><span data-stu-id="8417f-196">With the StartAzureSession object still selected in the Hierarchy panel, in the Inspector panel, scroll down to the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-2.1.png)

3. <span data-ttu-id="8417f-198">設定其餘按鈕</span><span class="sxs-lookup"><span data-stu-id="8417f-198">Configure the remaining buttons</span></span>

    <span data-ttu-id="8417f-199">針對其餘的每個按鈕，完成上述步驟1和2中所述的程式，將函式指派給按下的按鈕（）和 OnClick （）事件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8417f-199">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the Button Pressed () and OnClick () events following:</span></span>

    * <span data-ttu-id="8417f-200">針對**StopAzureSession**物件，指派**StopAzureSession （）** 函數。</span><span class="sxs-lookup"><span data-stu-id="8417f-200">For the **StopAzureSession** object, assign the **StopAzureSession()** function.</span></span>
    * <span data-ttu-id="8417f-201">針對**CreateAnchor**物件，指派**CreateAzureAnchor （）** 函式，然後將**ParentAnchor**再次拖曳到空白的**None （遊戲物件）** 欄位中。</span><span class="sxs-lookup"><span data-stu-id="8417f-201">For the **CreateAnchor** object, assign the **CreateAzureAnchor()** function, then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
    * <span data-ttu-id="8417f-202">針對 [**開始尋找錨點**物件]，指派**FindAzureAnchor （）** 函數。</span><span class="sxs-lookup"><span data-stu-id="8417f-202">For the **Start Looking for Anchor** object, assign the **FindAzureAnchor()** function.</span></span>
    * <span data-ttu-id="8417f-203">針對 [**刪除 Azure 錨點**] 物件，指派**DeleteAzureAnchor （）** 函數。</span><span class="sxs-lookup"><span data-stu-id="8417f-203">For the **Delete Azure Anchor** object, assign the **DeleteAzureAnchor()** function.</span></span>
    * <span data-ttu-id="8417f-204">針對 [**刪除本機錨點**] 物件，指派**RemoveLocalAnchor （）** 函式，然後再次將**ParentAnchor**拖曳至 [空的**無（遊戲物件）** ] 欄位。</span><span class="sxs-lookup"><span data-stu-id="8417f-204">For the **Delete Local Anchor** object, assign the **RemoveLocalAnchor()** function, then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>

4. <span data-ttu-id="8417f-205">將場景連線至 Azure 資源</span><span class="sxs-lookup"><span data-stu-id="8417f-205">Connect the scene to the Azure resource</span></span>

    <span data-ttu-id="8417f-206">在 [階層] 面板中，選取 [ **ParentAnchor** ] 物件，然後在 [偵測器] 面板中，向下流覽至 [**空間錨點管理員（腳本）** ] 元件。</span><span class="sxs-lookup"><span data-stu-id="8417f-206">In the Hierarchy panel, select the **ParentAnchor** object and in the Inspector panel, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

    <span data-ttu-id="8417f-207">然後，在 [**認證**] 區段中，將您的空間錨點帳戶識別碼和金鑰貼入對應的 [**空間錨點帳戶識別碼**] 和 [**空間錨點帳戶金鑰**] 欄位。</span><span class="sxs-lookup"><span data-stu-id="8417f-207">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields.</span></span>

    >[!NOTE]
    ><span data-ttu-id="8417f-208">您已在本教學[課程的必要條件](mrlearning-asa-ch1.md#prerequisites)中建立空間錨點帳戶識別碼和金鑰。</span><span class="sxs-lookup"><span data-stu-id="8417f-208">You created your Spatial Anchors Account Id and Key as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites).</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-4.1.png)

    >[!CAUTION]
    ><span data-ttu-id="8417f-210">請確定您已儲存場景。</span><span class="sxs-lookup"><span data-stu-id="8417f-210">Make sure you save your scene.</span></span>

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="8417f-211">嘗試 Azure 空間錨點的基本行為</span><span class="sxs-lookup"><span data-stu-id="8417f-211">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="8417f-212">您的場景已設定為示範 Azure 空間錨點的基本概念，現在可以部署應用程式，以便體驗 Azure 空間錨點搶先它。</span><span class="sxs-lookup"><span data-stu-id="8417f-212">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

1. <span data-ttu-id="8417f-213">新增額外的必要功能。</span><span class="sxs-lookup"><span data-stu-id="8417f-213">Add additional required capabilities.</span></span>

    <span data-ttu-id="8417f-214">在 Unity 功能表中，選取 **編輯** > **專案設定 ...**  以開啟 播放 設定面板。</span><span class="sxs-lookup"><span data-stu-id="8417f-214">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings panel.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.1.png)

    <span data-ttu-id="8417f-216">在 [Player 設定] 面板中，依序選取 [ **player** ] 和 [**發佈設定**]。</span><span class="sxs-lookup"><span data-stu-id="8417f-216">In the Player Settings panel, select **Player** and then **Publishing Settings**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.2.png)

    <span data-ttu-id="8417f-218">在 [**發行設定**] 中，向下流覽至 [**功能**] 區段，然後再次檢查您在教學課程開頭建立專案時所啟用的**SpatialPerception**（已啟用）。</span><span class="sxs-lookup"><span data-stu-id="8417f-218">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that **SpatialPerception**, which you enabled when you created the project at the beginning of the tutorial, is enabled.</span></span> <span data-ttu-id="8417f-219">然後，啟用**InternetClient**、 **InternetClientServer**、 **PrivateNetworkClientServer**、 **RemovableStorage**、**網路**攝影機和**麥克風**等功能。</span><span class="sxs-lookup"><span data-stu-id="8417f-219">Then, enabled the **InternetClient**, **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, **Webcam**, and **Microphone** capabilities.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.3.png)

2. <span data-ttu-id="8417f-221">將應用程式部署至 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="8417f-221">Deploy the app to your HoloLens 2.</span></span>

    >[!TIP]
    ><span data-ttu-id="8417f-222">如需有關如何建立 Unity 專案並將其部署至 HoloLens 2 的提醒，您可以參閱[初始化專案和第一個應用程式](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1)教學課程的「將[應用程式建立到您的裝置](mrlearning-base-ch1.md#build-your-application-to-your-device)」區段，這是使用者入門[教學](mrlearning-base.md)課程系列的一部分。</span><span class="sxs-lookup"><span data-stu-id="8417f-222">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) sections of the [Initializing your project and first application](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) tutorial which is part of the the [Getting started tutorials](mrlearning-base.md) series.</span></span>

3. <span data-ttu-id="8417f-223">執行應用程式，並遵循應用程式內的指示。</span><span class="sxs-lookup"><span data-stu-id="8417f-223">Run the app and follow the in-app instructions.</span></span>

    >[!CAUTION]
    ><span data-ttu-id="8417f-224">Azure 空間錨點會使用網際網路來儲存和載入錨定資料，因此請確定您的裝置已連線到網際網路。</span><span class="sxs-lookup"><span data-stu-id="8417f-224">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

    <span data-ttu-id="8417f-225">當應用程式在您的裝置上執行時，請遵循**Azure 空間錨點模組指示**面板上顯示的螢幕指示。</span><span class="sxs-lookup"><span data-stu-id="8417f-225">When the application is running on your device, follow the on-screen instructions displayed on the **Azure Spatial Anchor Module Instructions** panel.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-3.1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="8417f-227">錨定體驗</span><span class="sxs-lookup"><span data-stu-id="8417f-227">Anchoring an experience</span></span>

<span data-ttu-id="8417f-228">在前面幾節中，您已瞭解 Azure 空間錨點的基本概念。</span><span class="sxs-lookup"><span data-stu-id="8417f-228">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="8417f-229">我們使用 cube 來呈現父遊戲物件，並使用連結的錨點將其視覺化。</span><span class="sxs-lookup"><span data-stu-id="8417f-229">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="8417f-230">在本節中，您將瞭解如何藉由將它放在 ParentAnchor 物件的子系，來錨定整個體驗。</span><span class="sxs-lookup"><span data-stu-id="8417f-230">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

1. <span data-ttu-id="8417f-231">新增 Rocket 啟動器體驗。</span><span class="sxs-lookup"><span data-stu-id="8417f-231">Add the Rocket Launcher experience.</span></span>

    <span data-ttu-id="8417f-232">在 專案 面板中，流覽至 **資產**  > **MRTK。GettingStarted** > **Prefabs**  資料夾，然後選取**Rocket Launcher_Complete** prefab。</span><span class="sxs-lookup"><span data-stu-id="8417f-232">In the Project panel, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder and select the **Rocket Launcher_Complete** prefab.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-1.1.png)

    <span data-ttu-id="8417f-234">在仍選取 [Rocket Launcher_Complete prefab] 的情況下，將其拖曳至 [階層] 面板中的 [ **ParentAnchor** ] 物件上方，使其成為 ParentAnchor 物件的子系。</span><span class="sxs-lookup"><span data-stu-id="8417f-234">With the Rocket Launcher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy panel to make it a child of the ParentAnchor object.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-1.2.png)

2. <span data-ttu-id="8417f-236">重新置放 Rocket 啟動器體驗。</span><span class="sxs-lookup"><span data-stu-id="8417f-236">Reposition the Rocket Launcher experience.</span></span>

    <span data-ttu-id="8417f-237">移動模組**Rocket Launcher_Complete**物件，讓**ParentAnchor** （cube）仍然公開。</span><span class="sxs-lookup"><span data-stu-id="8417f-237">Move module **Rocket Launcher_Complete** object so that the **ParentAnchor** (the cube) is still exposed.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-2.1.png)

    <span data-ttu-id="8417f-239">在應用程式中，使用者現在可以藉由移動 cube 來重新放置整個 Rocket 啟動器的使用體驗。</span><span class="sxs-lookup"><span data-stu-id="8417f-239">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

    >[!TIP]
    ><span data-ttu-id="8417f-240">有各種不同的使用者體驗流程可進行重新置放的體驗，包括使用重新置放的物件（例如本教學課程中使用的 cube）、使用按鈕來切換環繞體驗的周框方塊、使用位置和旋轉gizmos，還有更多。</span><span class="sxs-lookup"><span data-stu-id="8417f-240">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="8417f-241">恭喜！</span><span class="sxs-lookup"><span data-stu-id="8417f-241">Congratulations</span></span>

<span data-ttu-id="8417f-242">在本教學課程中，您已瞭解 Azure 空間錨點的基本概念。</span><span class="sxs-lookup"><span data-stu-id="8417f-242">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="8417f-243">這一課提供了數個按鈕，可讓您探索啟動和停止 Azure 會話，以及在單一裝置上建立、上傳和下載 azure 錨點所需的各種步驟。</span><span class="sxs-lookup"><span data-stu-id="8417f-243">This Lesson provided you with several buttons that let you  explore the various steps required to start and stop an Azure session and create, upload and download azure anchors on a single device.</span></span>

<span data-ttu-id="8417f-244">在下一課中，您將瞭解如何將 Azure 錨點識別碼儲存至 HoloLens 2 進行抓取，即使在重新開機應用程式之後，以及如何在多個裝置之間傳輸錨點識別碼以達成空間對齊。</span><span class="sxs-lookup"><span data-stu-id="8417f-244">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="8417f-245">下一課： 2. 儲存、正在抓取和共用 Azure 空間錨點</span><span class="sxs-lookup"><span data-stu-id="8417f-245">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)
