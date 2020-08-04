---
title: 多使用者功能教學課程 - 2。 設定 Photon Unity 網路
description: 完成此課程以了解如何在 HoloLens 2 應用程式中實作使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: ed55d1f84db7ee8dc33f0f738de2b6b98a305fd3
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376400"
---
# <a name="2-setting-up-photon-unity-networking"></a><span data-ttu-id="9efc1-105">2.設定 Photon Unity 網路</span><span class="sxs-lookup"><span data-stu-id="9efc1-105">2. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="9efc1-106">概觀</span><span class="sxs-lookup"><span data-stu-id="9efc1-106">Overview</span></span>

<span data-ttu-id="9efc1-107">在本教學課程中，您將使用 Photon Unity 網路 (PUN) 來準備建立共用體驗。</span><span class="sxs-lookup"><span data-stu-id="9efc1-107">In this tutorial, you will prepare for creating a shared experience using Photon Unity Networking (PUN).</span></span> <span data-ttu-id="9efc1-108">您將了解如何建立 Photon PUN 應用程式、將 PUN 資產匯入到您的 Unity 專案，以及將您的 Unity 專案連線到 PUN 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9efc1-108">You will learn how to create a PUN app, import PUN assets into your Unity project, and connect your Unity project to the PUN app.</span></span>

## <a name="objectives"></a><span data-ttu-id="9efc1-109">目標</span><span class="sxs-lookup"><span data-stu-id="9efc1-109">Objectives</span></span>

* <span data-ttu-id="9efc1-110">了解如何建立 PUN 應用程式</span><span class="sxs-lookup"><span data-stu-id="9efc1-110">Learn how to create a PUN app</span></span>
* <span data-ttu-id="9efc1-111">了解如何尋找和匯入PUN 資產</span><span class="sxs-lookup"><span data-stu-id="9efc1-111">Learn how to find and import the PUN assets</span></span>
* <span data-ttu-id="9efc1-112">了解如何將您的 Unity 專案連線至 PUN 應用程式</span><span class="sxs-lookup"><span data-stu-id="9efc1-112">Learn how to connect your Unity project to the PUN app</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="9efc1-113">建立和準備 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="9efc1-113">Creating and preparing the Unity project</span></span>

<span data-ttu-id="9efc1-114">在本節中，您將建立新的 Unity 專案，並使該專案準備好進行 MRTK 開發。</span><span class="sxs-lookup"><span data-stu-id="9efc1-114">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="9efc1-115">為此，請先遵循[初始化您的專案和部署第一個應用程式](mr-learning-base-02.md) (但不包括[對您的裝置建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示)，其中包括下列步驟：</span><span class="sxs-lookup"><span data-stu-id="9efc1-115">For this, first follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="9efc1-116">[建立 Unity 專案](mr-learning-base-02.md#creating-the-unity-project)，並為其提供適當的名稱，例如「MRTK 教學課程」</span><span class="sxs-lookup"><span data-stu-id="9efc1-116">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
1. [<span data-ttu-id="9efc1-117">切換建置平台</span><span class="sxs-lookup"><span data-stu-id="9efc1-117">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. [<span data-ttu-id="9efc1-118">匯入 TextMeshPro 基本資源</span><span class="sxs-lookup"><span data-stu-id="9efc1-118">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
1. [<span data-ttu-id="9efc1-119">匯入混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="9efc1-119">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
1. [<span data-ttu-id="9efc1-120">設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="9efc1-120">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. <span data-ttu-id="9efc1-121">[建立和設定場景](mr-learning-base-02.md#creating-and-configuring-the-scene)並為場景提供適當的名稱，例如 MultiUserCapabilities</span><span class="sxs-lookup"><span data-stu-id="9efc1-121">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *MultiUserCapabilities*</span></span>

<span data-ttu-id="9efc1-122">然後遵循[變更空間感知顯示選項](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)的指示，以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="9efc1-122">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="9efc1-123">將 **MRTK 設定檔**變更為 **DefaultHoloLens2ConfigurationProfile**</span><span class="sxs-lookup"><span data-stu-id="9efc1-123">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="9efc1-124">將**空間感知網格顯示選項**變更為**遮蔽**。</span><span class="sxs-lookup"><span data-stu-id="9efc1-124">Change the **spatial awareness mesh display options** to **Occlusion**.</span></span>

## <a name="enabling-additional-capabilities"></a><span data-ttu-id="9efc1-125">啟用其他功能</span><span class="sxs-lookup"><span data-stu-id="9efc1-125">Enabling additional capabilities</span></span>

<span data-ttu-id="9efc1-126">在 Unity 功能表中，選取 [編輯] > [專案設定...] 來開啟 [玩家設定] 視窗，然後找出 [玩家] >  [發佈設定] 區段：</span><span class="sxs-lookup"><span data-stu-id="9efc1-126">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section2-step1-1.png)

<span data-ttu-id="9efc1-128">在 [發佈設定] 中，向下捲動至 [功能] 區段，然後再次確認您在上述[設定 Unity 專案](mr-learning-base-02.md#configuring-the-unity-project)所啟用的 **InternetClient**、**Microphone**、**SpatialPerception** 和 **GazeInput** 功能是否皆已啟用。</span><span class="sxs-lookup"><span data-stu-id="9efc1-128">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, **SpatialPerception**, and **GazeInput** capabilities, which you enabled during the [Configuring the Unity project](mr-learning-base-02.md#configuring-the-unity-project) step above, are enabled.</span></span>

<span data-ttu-id="9efc1-129">然後啟用下列其他功能：</span><span class="sxs-lookup"><span data-stu-id="9efc1-129">Then enable the following additional capabilities:</span></span>

* <span data-ttu-id="9efc1-130">**InternetClientServer** 功能</span><span class="sxs-lookup"><span data-stu-id="9efc1-130">**InternetClientServer** capability</span></span>
* <span data-ttu-id="9efc1-131">**PrivateNetworkClientServer** 功能</span><span class="sxs-lookup"><span data-stu-id="9efc1-131">**PrivateNetworkClientServer** capability</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section2-step1-2.png)

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="9efc1-133">安裝內建的 Unity 套件</span><span class="sxs-lookup"><span data-stu-id="9efc1-133">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="9efc1-134">在 Unity 功能表中，選取 視窗 >  **套件管理員** 以開啟 套件管理員 視窗，然後選取 AR 基本概念，並按一下 安裝 按鈕以安裝套件：</span><span class="sxs-lookup"><span data-stu-id="9efc1-134">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="9efc1-136">您正在安裝 AR Foundation 套件，因為 Azure Spatial Anchors SDK 需要此套件，您將在下一節中匯入。</span><span class="sxs-lookup"><span data-stu-id="9efc1-136">You are installing the AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="9efc1-137">匯入教學課程資產</span><span class="sxs-lookup"><span data-stu-id="9efc1-137">Importing the tutorial assets</span></span>

<span data-ttu-id="9efc1-138">下載並**依列出順序**來**匯入**下列 Unity 自訂套件：</span><span class="sxs-lookup"><span data-stu-id="9efc1-138">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="9efc1-139">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (2.2.1 版)</span><span class="sxs-lookup"><span data-stu-id="9efc1-139">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (version 2.2.1)</span></span>
* [<span data-ttu-id="9efc1-140">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="9efc1-140">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="9efc1-141">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="9efc1-141">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)
* [<span data-ttu-id="9efc1-142">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="9efc1-142">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage)

<span data-ttu-id="9efc1-143">匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：</span><span class="sxs-lookup"><span data-stu-id="9efc1-143">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="9efc1-145">如需有關如何匯入 Unity 自訂套件的提示，您可以參閱[匯入混合實境工具組 ](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) 的指示。</span><span class="sxs-lookup"><span data-stu-id="9efc1-145">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

> [!NOTE]
> <span data-ttu-id="9efc1-146">匯入 MultiUserCapabilities 教學課程資產套件之後，您會在主控台視窗中看到數個 [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) 錯誤，其指出缺少類型或命名空間。</span><span class="sxs-lookup"><span data-stu-id="9efc1-146">After importing the MultiUserCapabilities tutorial assets package, you will see several [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) errors in the Console window stating that the type or namespace is missing.</span></span> <span data-ttu-id="9efc1-147">這是預期的情況，將在下一節匯入 PUN 資產時解決。</span><span class="sxs-lookup"><span data-stu-id="9efc1-147">This is expected and will be resolved in the next section when you import the PUN assets.</span></span>

## <a name="importing-the-pun-assets"></a><span data-ttu-id="9efc1-148">匯入 PUN 資產</span><span class="sxs-lookup"><span data-stu-id="9efc1-148">Importing the PUN assets</span></span>

<span data-ttu-id="9efc1-149">在 Unity 功能表中，選取 [視窗] > [資產存放區] 來開啟 [資產存放區] 視窗，然後從 Exit Games 搜尋並選取 [PUN 2 - 免費]，按一下 [下載] 按鈕，將資產套件下載到您的 Unity 帳戶：</span><span class="sxs-lookup"><span data-stu-id="9efc1-149">In the Unity menu, select **Window** > **Asset Store** to open the Asset Store window, search for and select **PUN 2 - FREE** from Exit Games, click the **Download** button to download the asset package to your Unity account.</span></span>

<span data-ttu-id="9efc1-150">下載完成時，請按一下 [匯入] 按鈕來開啟 [匯入 Unity 套件] 視窗：</span><span class="sxs-lookup"><span data-stu-id="9efc1-150">When the download is complete, click the **Import** button to open the Import Unity Package window:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-1.png)

<span data-ttu-id="9efc1-152">在 [匯入 Unity 套件] 視窗中，按一下 [全部] 按鈕以確保選取所有資產，然後按一下 [匯入] 按鈕來匯入資產：</span><span class="sxs-lookup"><span data-stu-id="9efc1-152">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-2.png)

<span data-ttu-id="9efc1-154">Unity 完成匯入程序之後，Pun 精靈視窗會隨即出現並載入 PUN 設定功能表，您現在可以忽略或關閉此視窗：</span><span class="sxs-lookup"><span data-stu-id="9efc1-154">Once Unity has completed the import process, the Pun Wizard window will appear with the PUN Setup menu loaded, you can ignore or close this window for now:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-3.png)

## <a name="creating-the-pun-application"></a><span data-ttu-id="9efc1-156">建立 PUN 應用程式</span><span class="sxs-lookup"><span data-stu-id="9efc1-156">Creating the PUN application</span></span>

<span data-ttu-id="9efc1-157">在本節中，您將建立 Photon 帳戶 (如果您還沒有帳戶的話)，並建立新的 PUN 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9efc1-157">In this section, you will create a Photon account, if you don't already have one, and create a new PUN app.</span></span>

<span data-ttu-id="9efc1-158">瀏覽至 Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">儀表板</a> 並登入 (如果您已經有想要使用的帳戶)，否則請按一下 [建立帳戶] 連結，並依照指示註冊新帳戶：</span><span class="sxs-lookup"><span data-stu-id="9efc1-158">Navigate to the Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">dashboard</a> and sign in if you already have an account you want to use, otherwise, click the **Create One** link and follow the instructions to register a new account:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-1.png)

<span data-ttu-id="9efc1-160">登入之後，按一下 [建立新的應用程式] 按鈕：</span><span class="sxs-lookup"><span data-stu-id="9efc1-160">Once signed in, click the **Create a New App** button:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-2.png)

<span data-ttu-id="9efc1-162">在 [建立新的應用程式] 頁面上，輸入下列值：</span><span class="sxs-lookup"><span data-stu-id="9efc1-162">On the Create a New Application page, enter the following values:</span></span>

* <span data-ttu-id="9efc1-163">針對 Photon 類型，請選取 [PUN]</span><span class="sxs-lookup"><span data-stu-id="9efc1-163">For Photon Type, select PUN</span></span>
* <span data-ttu-id="9efc1-164">針對 [名稱]，請輸入適當的名稱，例如 MRTK Tutorials</span><span class="sxs-lookup"><span data-stu-id="9efc1-164">For Name, enter a suitable name, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="9efc1-165">針對 [描述]，您可以選擇性地輸入適當描述</span><span class="sxs-lookup"><span data-stu-id="9efc1-165">For Description, optionally enter a suitable description</span></span>
* <span data-ttu-id="9efc1-166">針對 [URL]，請將欄位保留空白</span><span class="sxs-lookup"><span data-stu-id="9efc1-166">For Url, leave the field empty</span></span>

<span data-ttu-id="9efc1-167">接著按一下 [建立] 按鈕以建立新應用程式：</span><span class="sxs-lookup"><span data-stu-id="9efc1-167">Then click the **Create** button to create the new app:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-3.png)

<span data-ttu-id="9efc1-169">當 Photon 完成建立程序後，新的 PUN 應用程式將會出現在儀表板上：</span><span class="sxs-lookup"><span data-stu-id="9efc1-169">Once Photon has finished the creation process, the new PUN app will appear on your dashboard:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a><span data-ttu-id="9efc1-171">將 Unity 專案連線至 PUN 應用程式</span><span class="sxs-lookup"><span data-stu-id="9efc1-171">Connecting the Unity project to the PUN application</span></span>

<span data-ttu-id="9efc1-172">在本節中，您會將 Unity 專案連線到您在上一節中建立的 PUN 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9efc1-172">In this section, you will connect your Unity project to the PUN app you created in the previous section.</span></span>

<span data-ttu-id="9efc1-173">在 Photon 儀表板上，按一下 [應用程式識別碼] 欄位以顯示應用程式識別碼，然後將其複製到您的剪貼簿：</span><span class="sxs-lookup"><span data-stu-id="9efc1-173">On the Photon dashboard, click the **App ID** field to reveal the app ID, then copy it to your clipboard:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-1.png)

<span data-ttu-id="9efc1-175">在 Unity 功能表中，選取 [視窗] > [Photon Unity 網路] > [PUN 精靈] 以開啟 PUN 精靈視窗，然後按一下 [設定專案] 按鈕以開啟 [PUN 設定] 功能表，並依照下列方式進行設定：</span><span class="sxs-lookup"><span data-stu-id="9efc1-175">In the Unity menu, select **Window** > **Photon Unity Networking** > **PUN Wizard** to open the Pun Wizard window, click the **Setup Project** button to open the PUN Setup menu, and configure it as follows:</span></span>

* <span data-ttu-id="9efc1-176">在 [AppId 或電子郵件] 欄位中，貼上您在上一個步驟中複製的 PUN 應用程式識別碼</span><span class="sxs-lookup"><span data-stu-id="9efc1-176">In the **AppId or Email** field, paste the PUN app ID you copied in the previous step</span></span>

<span data-ttu-id="9efc1-177">然後按一下 [設定專案] 按鈕來套用應用程式識別碼：</span><span class="sxs-lookup"><span data-stu-id="9efc1-177">Then click the **Setup Project** button to apply the app ID:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-2.png)

<span data-ttu-id="9efc1-179">當 Unity 完成 PUN 設定程序後，[PUN 設定] 功能表就會顯示訊息「完成！」訊息</span><span class="sxs-lookup"><span data-stu-id="9efc1-179">Once Unity has finished the PUN setup process, the PUN Setup menu will display the message **Done!**</span></span> <span data-ttu-id="9efc1-180">並自動選取 [專案] 視窗中的 **PhotonServerSettings** 資產，讓其屬性顯示在 [偵測器] 視窗中：</span><span class="sxs-lookup"><span data-stu-id="9efc1-180">and automatically select the **PhotonServerSettings** asset in the Project window, so its properties are displayed in the Inspector window:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="9efc1-182">恭喜！</span><span class="sxs-lookup"><span data-stu-id="9efc1-182">Congratulations</span></span>

<span data-ttu-id="9efc1-183">您已成功建立 PUN 應用程式，並將其連線到您的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="9efc1-183">You have successfully created a PUN app and connected it to your Unity project.</span></span> <span data-ttu-id="9efc1-184">下一個步驟是允許與其他使用者連線，讓多個使用者可以看到彼此。</span><span class="sxs-lookup"><span data-stu-id="9efc1-184">Your next step is to allow connections with other users so that multiple users can see each other.</span></span>

[<span data-ttu-id="9efc1-185">下一個教學課程：3.連線多個使用者</span><span class="sxs-lookup"><span data-stu-id="9efc1-185">Next Tutorial: 3. Connecting multiple users</span></span>](mr-learning-sharing-03.md)
