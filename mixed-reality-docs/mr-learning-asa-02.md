---
title: Azure Spatial Anchor 教學課程 - 2。 開始使用 Azure Spatial Anchors
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure Spatial Anchors。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: d117839e51e586f4b905a20510fffc670d34cd4e
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376490"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="24b4c-105">2.開始使用 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="24b4c-105">2. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="24b4c-106">概觀</span><span class="sxs-lookup"><span data-stu-id="24b4c-106">Overview</span></span>

<span data-ttu-id="24b4c-107">在此教學課程中，您將探索啟動和停止 Azure Spatial Anchors 工作階段，以及在單一裝置上建立、上傳和下載 Azure Spatial Anchors 所需的各種步驟。</span><span class="sxs-lookup"><span data-stu-id="24b4c-107">In this tutorial, you will explore the various steps required to start and stop an Azure Spatial Anchors session and to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

## <a name="objectives"></a><span data-ttu-id="24b4c-108">目標</span><span class="sxs-lookup"><span data-stu-id="24b4c-108">Objectives</span></span>

* <span data-ttu-id="24b4c-109">了解 HoloLens 2 的 Azure Spatial Anchors 開發基本概念</span><span class="sxs-lookup"><span data-stu-id="24b4c-109">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="24b4c-110">了解如何建立空間錨點，並從 Azure 提取這些錨點</span><span class="sxs-lookup"><span data-stu-id="24b4c-110">Learn how to create spatial anchors and fetch them from Azure</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="24b4c-111">建立和準備 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="24b4c-111">Creating and preparing the Unity project</span></span>

<span data-ttu-id="24b4c-112">在本節中，您將建立新的 Unity 專案，並使該專案準備好進行 MRTK 開發。</span><span class="sxs-lookup"><span data-stu-id="24b4c-112">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="24b4c-113">為此，請先遵循[初始化您的專案和部署第一個應用程式](mr-learning-base-02.md) (但不包括[對您的裝置建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示)，其中包括下列步驟：</span><span class="sxs-lookup"><span data-stu-id="24b4c-113">For this, first follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="24b4c-114">[建立 Unity 專案](mr-learning-base-02.md#creating-the-unity-project)，並為其提供適當的名稱，例如「MRTK 教學課程」</span><span class="sxs-lookup"><span data-stu-id="24b4c-114">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
1. [<span data-ttu-id="24b4c-115">切換建置平台</span><span class="sxs-lookup"><span data-stu-id="24b4c-115">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. [<span data-ttu-id="24b4c-116">匯入 TextMeshPro 基本資源</span><span class="sxs-lookup"><span data-stu-id="24b4c-116">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
1. [<span data-ttu-id="24b4c-117">匯入混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="24b4c-117">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
1. [<span data-ttu-id="24b4c-118">設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="24b4c-118">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. <span data-ttu-id="24b4c-119">[建立和設定場景](mr-learning-base-02.md#creating-and-configuring-the-scene)並為場景提供適當的名稱，例如 AzureSpatialAnchors</span><span class="sxs-lookup"><span data-stu-id="24b4c-119">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="24b4c-120">然後遵循[變更空間感知顯示選項](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)的指示，以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="24b4c-120">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="24b4c-121">將 **MRTK 設定檔**變更為 **DefaultHoloLens2ConfigurationProfile**</span><span class="sxs-lookup"><span data-stu-id="24b4c-121">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="24b4c-122">將**空間感知網格顯示選項**變更為**遮蔽**。</span><span class="sxs-lookup"><span data-stu-id="24b4c-122">Change the **spatial awareness mesh display options** to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="24b4c-123">安裝內建的 Unity 套件</span><span class="sxs-lookup"><span data-stu-id="24b4c-123">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="24b4c-124">在 Unity 功能表中，選取 [視窗] >  **[套件管理員]** 以開啟 [套件管理員] 視窗，然後選取 [AR 基本概念]，並按一下 [安裝] 按鈕以安裝套件：</span><span class="sxs-lookup"><span data-stu-id="24b4c-124">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="24b4c-126">您正在安裝 AR Foundation 套件，因為 Azure Spatial Anchors SDK 需要此套件，您將在下一節中匯入。</span><span class="sxs-lookup"><span data-stu-id="24b4c-126">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="24b4c-127">匯入教學課程資產</span><span class="sxs-lookup"><span data-stu-id="24b4c-127">Importing the tutorial assets</span></span>

<span data-ttu-id="24b4c-128">下載並**依列出順序**來**匯入**下列 Unity 自訂套件：</span><span class="sxs-lookup"><span data-stu-id="24b4c-128">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="24b4c-129">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (2.2.1 版)</span><span class="sxs-lookup"><span data-stu-id="24b4c-129">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (version 2.2.1)</span></span>
* [<span data-ttu-id="24b4c-130">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="24b4c-130">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="24b4c-131">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="24b4c-131">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)

<span data-ttu-id="24b4c-132">匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：</span><span class="sxs-lookup"><span data-stu-id="24b4c-132">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="24b4c-134">如需有關如何匯入 Unity 自訂套件的提示，您可以參閱[匯入混合實境工具組](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) 的指示。</span><span class="sxs-lookup"><span data-stu-id="24b4c-134">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="24b4c-135">準備場景</span><span class="sxs-lookup"><span data-stu-id="24b4c-135">Preparing the scene</span></span>

<span data-ttu-id="24b4c-136">在本節中，您將藉由新增一些教學課程 Prefab 來準備場景。</span><span class="sxs-lookup"><span data-stu-id="24b4c-136">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="24b4c-137">在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.AzureSpatialAnchors] > [Prefabs] 資料夾，然後按一下下列 Prefab 並將其拖曳至 [階層] 視窗中，將其新增到您的場景中：</span><span class="sxs-lookup"><span data-stu-id="24b4c-137">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="24b4c-138">**ButtonParent** Prefab</span><span class="sxs-lookup"><span data-stu-id="24b4c-138">**ButtonParent** prefabs</span></span>
* <span data-ttu-id="24b4c-139">**DebugWindow** Prefab</span><span class="sxs-lookup"><span data-stu-id="24b4c-139">**DebugWindow** prefabs</span></span>
* <span data-ttu-id="24b4c-140">**Instructions** Prefab</span><span class="sxs-lookup"><span data-stu-id="24b4c-140">**Instructions** prefabs</span></span>
* <span data-ttu-id="24b4c-141">**ParentAnchor** Prefab</span><span class="sxs-lookup"><span data-stu-id="24b4c-141">**ParentAnchor** prefabs</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="24b4c-143">如果您發現場景中的大圖示 (例如大型邊框的 'T' 圖示) 會造成干擾，您可以藉由將 <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">Gizmo 切換</a>到關閉位置來將其隱藏，如上圖所示。</span><span class="sxs-lookup"><span data-stu-id="24b4c-143">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="24b4c-144">設定按鈕以操作場景</span><span class="sxs-lookup"><span data-stu-id="24b4c-144">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="24b4c-145">在本節中，您將在場景中新增指令碼來建立一系列的按鈕事件，以示範本機錨點和 Azure Spatial Anchors 在應用程式中的行為基礎。</span><span class="sxs-lookup"><span data-stu-id="24b4c-145">In this section, you will add scripts to the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an app.</span></span>

<span data-ttu-id="24b4c-146">在 [階層] 視窗中，展開 **ButtonParent** 物件，並選取名為 **StartAzureSession** 的第一個子物件，然後在 [偵測器] 視窗中，設定 **Button Config Helper (指令碼)** 元件的 **On Click ()** 事件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="24b4c-146">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**, in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="24b4c-147">將 **ParentAnchor** 物件指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="24b4c-147">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="24b4c-148">從 [沒有函式] 下拉式清單中，選取 [AnchorModuleScript] > [StartAzureSession ()]，以將此函式設定為觸發事件時所要執行的動作</span><span class="sxs-lookup"><span data-stu-id="24b4c-148">From the **No Function** dropdown, select **AnchorModuleScript** > **StartAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-1.png)

<span data-ttu-id="24b4c-150">在 [階層] 視窗中，選取名為 **StopAzureSession** 的下一個按鈕，然後在 [偵測器] 視窗中，設定 **Button Config Helper (指令碼)** 元件的 **On Click ()** 事件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="24b4c-150">In the Hierarchy window, select the next button named **StopAzureSession**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="24b4c-151">將 **ParentAnchor** 物件指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="24b4c-151">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="24b4c-152">從 [沒有函式] 下拉式清單中，選取 [AnchorModuleScript] > [StopAzureSession ()]，以將此函式設定為觸發事件時所要執行的動作</span><span class="sxs-lookup"><span data-stu-id="24b4c-152">From the **No Function** dropdown, select **AnchorModuleScript** > **StopAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-2.png)

<span data-ttu-id="24b4c-154">在 [階層] 視窗中，選取名為 **CreateAzureAnchor** 的下一個按鈕，然後在 [偵測器] 視窗中，設定 **Button Config Helper (指令碼)** 元件的 **On Click ()** 事件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="24b4c-154">In the Hierarchy window, select the next button named **CreateAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="24b4c-155">將 **ParentAnchor** 物件指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="24b4c-155">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="24b4c-156">從 [沒有函式] 下拉式清單中，選取 [AnchorModuleScript] > [CreateAzureAnchor ()]，以將此函式設定為觸發事件時所要執行的動作</span><span class="sxs-lookup"><span data-stu-id="24b4c-156">From the **No Function** dropdown, select **AnchorModuleScript** > **CreateAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="24b4c-157">將 **ParentAnchor** 物件指派給空的 [無 (遊戲物件)] 欄位，使其成為 CreateAzureAnchor () 函式的引數</span><span class="sxs-lookup"><span data-stu-id="24b4c-157">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the CreateAzureAnchor () function</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-3.png)

<span data-ttu-id="24b4c-159">在 [階層] 視窗中，選取名為 **RemoveLocalAnchor** 的下一個按鈕，然後在 [偵測器] 視窗中，設定 **Button Config Helper (指令碼)** 元件的 **On Click ()** 事件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="24b4c-159">In the Hierarchy window, select the next button named **RemoveLocalAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="24b4c-160">將 **ParentAnchor** 物件指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="24b4c-160">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="24b4c-161">從 [沒有函式] 下拉式清單中，選取 [AnchorModuleScript] > [RemoveLocalAnchor ()]，以將此函式設定為觸發事件時所要執行的動作</span><span class="sxs-lookup"><span data-stu-id="24b4c-161">From the **No Function** dropdown, select **AnchorModuleScript** > **RemoveLocalAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="24b4c-162">將 **ParentAnchor** 物件指派給空的 [無 (遊戲物件)] 欄位，使其成為 RemoveLocalAnchor () 函式的引數</span><span class="sxs-lookup"><span data-stu-id="24b4c-162">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the RemoveLocalAnchor () function</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-4.png)

<span data-ttu-id="24b4c-164">在 [階層] 視窗中，選取名為 **FindAzureAnchor** 的下一個按鈕，然後在 [偵測器] 視窗中，設定 **Button Config Helper (指令碼)** 元件的 **On Click ()** 事件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="24b4c-164">In the Hierarchy window, select the next button named **FindAzureAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="24b4c-165">將 **ParentAnchor** 物件指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="24b4c-165">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="24b4c-166">從 [沒有函式] 下拉式清單中，選取 [AnchorModuleScript] > [FindAzureAnchor ()]，以將此函式設定為觸發事件時所要執行的動作</span><span class="sxs-lookup"><span data-stu-id="24b4c-166">From the **No Function** dropdown, select **AnchorModuleScript** > **FindAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-5.png)

<span data-ttu-id="24b4c-168">在 [階層] 視窗中，選取名為 **DeleteAzureAnchor** 的下一個按鈕，然後在 [偵測器] 視窗中，設定 **Button Config Helper (指令碼)** 元件的 **On Click ()** 事件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="24b4c-168">In the Hierarchy window, select the next button named **DeleteAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="24b4c-169">將 **ParentAnchor** 物件指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="24b4c-169">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="24b4c-170">從 [沒有函式] 下拉式清單中，選取 [AnchorModuleScript] > [DeleteAzureAnchor ()]，以將此函式設定為觸發事件時所要執行的動作</span><span class="sxs-lookup"><span data-stu-id="24b4c-170">From the **No Function** dropdown, select **AnchorModuleScript** > **DeleteAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="24b4c-172">將場景連線至 Azure 資源</span><span class="sxs-lookup"><span data-stu-id="24b4c-172">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="24b4c-173">在 [階層] 視窗中，選取 **ParentAnchor** 物件，然後在 [偵測器] 視窗中尋找 **Spatial Anchor Manager (指令碼)** 元件。</span><span class="sxs-lookup"><span data-stu-id="24b4c-173">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component.</span></span> <span data-ttu-id="24b4c-174">使用 Azure Spatial Anchors 帳戶中的認證來設定 [認證] 區段，該帳戶會在本教學課程系列的[必要條件](mr-learning-asa-01.md#prerequisites)中建立：</span><span class="sxs-lookup"><span data-stu-id="24b4c-174">Configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-asa-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="24b4c-175">在 [Spatial Anchors Account 識別碼] 欄位中，貼上 Azure Spatial Anchors 帳戶中的**帳戶識別碼**</span><span class="sxs-lookup"><span data-stu-id="24b4c-175">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="24b4c-176">在 [Spatial Anchors 帳戶金鑰] 欄位中，貼上 Azure Spatial Anchors 帳戶中的主要或次要**存取金鑰**</span><span class="sxs-lookup"><span data-stu-id="24b4c-176">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="24b4c-178">嘗試 Azure Spatial Anchors 的基本行為</span><span class="sxs-lookup"><span data-stu-id="24b4c-178">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="24b4c-179">Azure Spatial Anchors 無法在 Unity 中執行，因此若要測試 Azure Spatial Anchors 功能，您必須在裝置中建置專案並部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="24b4c-179">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to build the project and deploy the app to your device.</span></span>

> [!TIP]
> <span data-ttu-id="24b4c-180">如需有關如何建立 Unity 專案並將其部署至 HoloLens 2 的提醒，您可以參閱[對您的 HoloLens 2 建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示。</span><span class="sxs-lookup"><span data-stu-id="24b4c-180">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

<span data-ttu-id="24b4c-181">當應用程式在您的裝置上執行時，請遵循 Azure Spatial Anchor 教學課程指示面板上顯示的螢幕指示：</span><span class="sxs-lookup"><span data-stu-id="24b4c-181">When the app runs on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

1. <span data-ttu-id="24b4c-182">將立方體移至不同的位置</span><span class="sxs-lookup"><span data-stu-id="24b4c-182">Move the cube to a different location</span></span>
1. <span data-ttu-id="24b4c-183">啟動 Azure 工作階段</span><span class="sxs-lookup"><span data-stu-id="24b4c-183">Start Azure Session</span></span>
1. <span data-ttu-id="24b4c-184">建立 Azure 錨點 (在立方體的位置上建立錨點)。</span><span class="sxs-lookup"><span data-stu-id="24b4c-184">Create Azure Anchor (creates an anchor at the location of the cube).</span></span>
1. <span data-ttu-id="24b4c-185">停止 Azure 工作階段</span><span class="sxs-lookup"><span data-stu-id="24b4c-185">Stop Azure Session</span></span>
1. <span data-ttu-id="24b4c-186">移除區域錨點 (允許使用者移動立方體)</span><span class="sxs-lookup"><span data-stu-id="24b4c-186">Remove Local Anchor (allows the user to move the cube)</span></span>
1. <span data-ttu-id="24b4c-187">將立方體移至其他地方</span><span class="sxs-lookup"><span data-stu-id="24b4c-187">Move the cube somewhere else</span></span>
1. <span data-ttu-id="24b4c-188">啟動 Azure 工作階段</span><span class="sxs-lookup"><span data-stu-id="24b4c-188">Start Azure Session</span></span>
1. <span data-ttu-id="24b4c-189">尋找 Azure 錨點 (將立方體置於步驟 3 的位置)</span><span class="sxs-lookup"><span data-stu-id="24b4c-189">Find Azure Anchor (positions the cube at the location from step 3)</span></span>
1. <span data-ttu-id="24b4c-190">刪除 Azure 錨點</span><span class="sxs-lookup"><span data-stu-id="24b4c-190">Delete Azure Anchor</span></span>
1. <span data-ttu-id="24b4c-191">停止 Azure 工作階段</span><span class="sxs-lookup"><span data-stu-id="24b4c-191">Stop Azure session</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> <span data-ttu-id="24b4c-193">Azure Spatial Anchors 會使用網際網路來儲存和載入錨點資料，因此請確定您的裝置已連線到網際網路。</span><span class="sxs-lookup"><span data-stu-id="24b4c-193">Azure Spatial Anchors uses the internet to save and load the anchor data, so make sure your device is connected to the internet.</span></span>

## <a name="anchoring-an-experience"></a><span data-ttu-id="24b4c-194">錨點體驗</span><span class="sxs-lookup"><span data-stu-id="24b4c-194">Anchoring an experience</span></span>

<span data-ttu-id="24b4c-195">在前面幾節中，您已了解 Azure Spatial Anchors 的基本概念。</span><span class="sxs-lookup"><span data-stu-id="24b4c-195">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="24b4c-196">我們使用了立方體和連結的錨點來呈現及視覺化父遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="24b4c-196">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="24b4c-197">在本節中，您將了解如何藉由將整個體驗放在 ParentAnchor 物件的子系，來為其建立錨點。</span><span class="sxs-lookup"><span data-stu-id="24b4c-197">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

<span data-ttu-id="24b4c-198">在 [階層] 視窗中，選取 **ParentAnchor** 物件，然後在 [偵測器] 視窗中設定**變形**元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="24b4c-198">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, configure the **Transform** components as follows:</span></span>

* <span data-ttu-id="24b4c-199">將 [X 軸縮放] 變更為 1.1</span><span class="sxs-lookup"><span data-stu-id="24b4c-199">Change **Scale X** to 1.1</span></span>
* <span data-ttu-id="24b4c-200">將 [Z 軸縮放] 變更為 1.1</span><span class="sxs-lookup"><span data-stu-id="24b4c-200">Change **Scale Z** to 1.1</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-1.png)

<span data-ttu-id="24b4c-202">在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.GettingStarted] > [Prefabs] > [Rover] 資料夾，然後按一下 **RoverExplorer_Complete** Prefab，並將其拖曳至 [階層] 視窗中來新增到您的場景中：</span><span class="sxs-lookup"><span data-stu-id="24b4c-202">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** folder, then click-and-drag the **RoverExplorer_Complete** prefab into the Hierarchy window to add it to the scene:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-2.png)

<span data-ttu-id="24b4c-204">在 [階層] 視窗中，繼續選取新增的 RoverModule_Complete 物件，並將其拖曳至 **ParentAnchor** 物件，使其成為 ParentAnchor 物件的子系：</span><span class="sxs-lookup"><span data-stu-id="24b4c-204">With the newly added RoverModule_Complete object still selected in the Hierarchy window, drag it onto the **ParentAnchor** object to make it a child of the ParentAnchor object:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-3.png)

<span data-ttu-id="24b4c-206">如果您現在重建專案，並將應用程式部署到您的裝置，您現在就可以藉由移動已調整大小的立方體來重新放置整個 Rover Explorer 體驗。</span><span class="sxs-lookup"><span data-stu-id="24b4c-206">If you now rebuild the project and deploy the app to your device, you can now reposition the entire Rover Explorer experience by moving the resized cube.</span></span>

> [!TIP]
> <span data-ttu-id="24b4c-207">有各種不同的使用者體驗流程可用於重新置放體驗，包括使用重新置放物件 (例如本教學課程中使用的立方體)、使用按鈕來切換環繞體驗的周框方塊、使用位置和旋轉 gizmo 等等。</span><span class="sxs-lookup"><span data-stu-id="24b4c-207">A variety of user experience flows for repositioning experiences, including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="24b4c-208">恭喜！</span><span class="sxs-lookup"><span data-stu-id="24b4c-208">Congratulations</span></span>

<span data-ttu-id="24b4c-209">在本教學課程中，您已了解 Azure Spatial Anchors 的基本概念。</span><span class="sxs-lookup"><span data-stu-id="24b4c-209">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="24b4c-210">本教學課程提供了您幾個按鈕，讓您探索啟動和停止 Azure Spatial Anchors 工作階段所需的各種步驟。</span><span class="sxs-lookup"><span data-stu-id="24b4c-210">This tutorial provided you with several buttons to let you explore the various steps required to start and stop an Azure Spatial Anchors session.</span></span> <span data-ttu-id="24b4c-211">此外，也可以在單一裝置上建立、上傳和下載 Azure Spatial Anchors。</span><span class="sxs-lookup"><span data-stu-id="24b4c-211">Also, to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="24b4c-212">在下一個教學課程中，您將了解如何將 Azure 錨點識別碼儲存至 HoloLens 2 以便擷取 (即使在重新啟動應用程式之後)，以及如何在多個裝置之間傳輸錨點識別碼以達到空間對齊。</span><span class="sxs-lookup"><span data-stu-id="24b4c-212">In the next tutorial, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the app is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="24b4c-213">下一個教學課程：3.儲存、擷取和共用 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="24b4c-213">Next Tutorial: 3. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
