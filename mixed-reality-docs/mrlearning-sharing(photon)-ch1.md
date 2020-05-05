---
title: 多使用者功能教學課程 - 1。 設定 Photon Unity 網路
description: 完成此課程以了解如何在 HoloLens 2 應用程式中實作使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 2f5b55fe9c54e9e2c08177266c04a97d2302230e
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610752"
---
# <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="89060-105">1.設定 Photon Unity 網路</span><span class="sxs-lookup"><span data-stu-id="89060-105">1. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="89060-106">概觀</span><span class="sxs-lookup"><span data-stu-id="89060-106">Overview</span></span>

<span data-ttu-id="89060-107">在本教學課程中，您將了解如何使用 Photon Unity 網路 (PUN) 來準備建立共用體驗。</span><span class="sxs-lookup"><span data-stu-id="89060-107">In this tutorial, you will learn how to prepare for creating a shared experience using Photon Unity Networking (PUN).</span></span> <span data-ttu-id="89060-108">Photon 是可讓混合實境開發人員用來建立共用體驗的眾多網路功能選項之一。</span><span class="sxs-lookup"><span data-stu-id="89060-108">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="89060-109">您將了解如何建立 Photon PUN 應用程式、將 Photon PUN 資產匯入到您的 Unity 專案，以及將您的 Unity 專案連線到 Photon PUN 應用程式。</span><span class="sxs-lookup"><span data-stu-id="89060-109">You will learn how to create a Photon PUN application, import Photon PUN assets into your Unity project, and connect your Unity project to the Photon PUN application.</span></span>

## <a name="objectives"></a><span data-ttu-id="89060-110">目標</span><span class="sxs-lookup"><span data-stu-id="89060-110">Objectives</span></span>

* <span data-ttu-id="89060-111">了解如何建立 Photon PUN 應用程式</span><span class="sxs-lookup"><span data-stu-id="89060-111">Learn how to create a Photon PUN application</span></span>
* <span data-ttu-id="89060-112">了解如何尋找和匯入 Photon PUN 資產</span><span class="sxs-lookup"><span data-stu-id="89060-112">Learn how to find and import the Photon PUN assets</span></span>
* <span data-ttu-id="89060-113">了解如何將您的 Unity 專案連線至 Photon PUN 應用程式</span><span class="sxs-lookup"><span data-stu-id="89060-113">Learn how to connect your Unity project to the Photon PUN application</span></span>

## <a name="prerequisites"></a><span data-ttu-id="89060-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="89060-114">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="89060-115">如果您尚未完成[入門教學課程](mrlearning-base.md)及 [Azure Spatial Anchors 教學課程](mrlearning-asa-ch1.md)的教學課程系列，建議您先完成這些教學課程。</span><span class="sxs-lookup"><span data-stu-id="89060-115">If you have not completed the [Getting started tutorials](mrlearning-base.md) and [Azure Spatial Anchors tutorials](mrlearning-asa-ch1.md) tutorial series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="89060-116">已[安裝正確工具](install-the-tools.md)的 Windows 10 電腦</span><span class="sxs-lookup"><span data-stu-id="89060-116">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="89060-117">Windows 10 SDK 10.0.18362.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="89060-117">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="89060-118">基本的 C# 程式設計能力</span><span class="sxs-lookup"><span data-stu-id="89060-118">Some basic C# programming ability</span></span>
* <span data-ttu-id="89060-119">已[針對開發而設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置</span><span class="sxs-lookup"><span data-stu-id="89060-119">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="89060-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，已安裝 Unity 2019.2，且已新增通用 Windows 平台組建支援模組</span><span class="sxs-lookup"><span data-stu-id="89060-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="89060-121">完成[建立空間錨點資源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)區段，其位於[教學課程：建立使用 Azure Spatial Anchors 的 Unity HoloLens 應用程式](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)</span><span class="sxs-lookup"><span data-stu-id="89060-121">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>

> [!IMPORTANT]
> <span data-ttu-id="89060-122">本教學課程系列的建議 Unity 版本是 Unity 2019.2. X。</span><span class="sxs-lookup"><span data-stu-id="89060-122">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="89060-123">這個版本能取代上述連結之必要條件中所述的任何 Unity 版本需求或建議。</span><span class="sxs-lookup"><span data-stu-id="89060-123">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="89060-124">建立和準備 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="89060-124">Creating and preparing the Unity project</span></span>

<span data-ttu-id="89060-125">在本節中，您將建立新的 Unity 專案，並使該專案準備好進行 MRTK 開發。</span><span class="sxs-lookup"><span data-stu-id="89060-125">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="89060-126">為此，請先遵循[初始化您的專案和第一個應用程式](mrlearning-base-ch1.md) (但不包括[對您的裝置建置應用程式](mrlearning-base-ch1.md#build-your-application-to-your-device)的指示)，其中包括下列步驟：</span><span class="sxs-lookup"><span data-stu-id="89060-126">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="89060-127">[建立新的 Unity 專案](mrlearning-base-ch1.md#create-new-unity-project)，並為其提供適當的名稱，例如「MRTK 教學課程」 </span><span class="sxs-lookup"><span data-stu-id="89060-127">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

2. [<span data-ttu-id="89060-128">設定適用於 Windows Mixed Reality 的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="89060-128">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="89060-129">匯入 TextMesh Pro 基本資源</span><span class="sxs-lookup"><span data-stu-id="89060-129">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="89060-130">匯入混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="89060-130">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="89060-131">設定用於混合實境工具組的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="89060-131">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="89060-132">[將 Mixed Reality 工具組新增至 Unity 場景](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)並為場景提供適當的名稱，例如 *MultiUserCapabilities*</span><span class="sxs-lookup"><span data-stu-id="89060-132">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *MultiUserCapabilities*</span></span>

<span data-ttu-id="89060-133">然後遵循[如何設定混合實境工具組設定檔 (變更空間感知顯示選項)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) 的指示，將場景的 MRTK 組態設定檔變更為 **DefaultHoloLens2ConfigurationProfile**，並將空間感知網格的顯示選項變更為 [遮蔽]  。</span><span class="sxs-lookup"><span data-stu-id="89060-133">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="89060-134">如上方連結：[設定用於混合實境工具組的 Unity 專案](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)中所述的指示，強烈建議您不要為 Unity 啟用 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="89060-134">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="89060-135">設定功能</span><span class="sxs-lookup"><span data-stu-id="89060-135">Configuring the capabilities</span></span>

<span data-ttu-id="89060-136">在 Unity 功能表中，選取 [編輯]   > [專案設定...]  來開啟 [玩家設定] 視窗，然後找出 [玩家]   >  [發佈設定]  區段：</span><span class="sxs-lookup"><span data-stu-id="89060-136">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-1.png)

<span data-ttu-id="89060-138">在 [發佈設定]  中，向下捲動至 [功能]  區段，然後再次確認您在教學課程開頭建立專案時所啟用的 **InternetClient**、**Microphone** 和 **SpatialPerception** 功能是否皆已啟用。</span><span class="sxs-lookup"><span data-stu-id="89060-138">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="89060-139">然後，啟用 **InternetClientServer**、**PrivateNetworkClientServer**和 **RemovableStorage** 功能：</span><span class="sxs-lookup"><span data-stu-id="89060-139">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, and **RemovableStorage** capabilities:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-2.png)

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="89060-141">新增內建的 Unity 套件</span><span class="sxs-lookup"><span data-stu-id="89060-141">Adding inbuilt Unity packages</span></span>
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

<span data-ttu-id="89060-142">在本節中，您將安裝 Unity 的內建 AR Foundation 套件，因為您在下一節匯入 Azure Spatial Anchors SDK 時會需要此套件。</span><span class="sxs-lookup"><span data-stu-id="89060-142">In this section, you will install Unity's inbuilt AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

<span data-ttu-id="89060-143">在 Unity 功能表中，選取 [視窗]   >  **[套件管理員]** ：</span><span class="sxs-lookup"><span data-stu-id="89060-143">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="89060-145">可能需要幾秒鐘的時間，AR Foundation 套件才會出現在清單中。</span><span class="sxs-lookup"><span data-stu-id="89060-145">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

<span data-ttu-id="89060-146">在 [套件管理員] 視窗中選取 [AR Foundation]  ，然後按一下 [安裝]  按鈕來安裝套件：</span><span class="sxs-lookup"><span data-stu-id="89060-146">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="89060-148">匯入教學課程資產</span><span class="sxs-lookup"><span data-stu-id="89060-148">Importing the tutorial assets</span></span>

<span data-ttu-id="89060-149">下載並**依列出順序**來**匯入**下列 Unity 自訂套件：</span><span class="sxs-lookup"><span data-stu-id="89060-149">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="89060-150">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (2.1.1 版)</span><span class="sxs-lookup"><span data-stu-id="89060-150">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
* [<span data-ttu-id="89060-151">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="89060-151">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="89060-152">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="89060-152">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)
* [<span data-ttu-id="89060-153">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="89060-153">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="89060-154">如需有關如何匯入 Unity 自訂套件的提示，您可以參閱[匯入混合實境工具組](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) 的指示。</span><span class="sxs-lookup"><span data-stu-id="89060-154">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="89060-155">匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：</span><span class="sxs-lookup"><span data-stu-id="89060-155">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="89060-157">匯入 MultiUserCapabilities 教學課程資產套件之後，您會在主控台視窗中看到數個 [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) 錯誤，其指出缺少類型或命名空間。</span><span class="sxs-lookup"><span data-stu-id="89060-157">After importing the MultiUserCapabilities tutorial assets package, you will see several [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) errors in the Console window stating that the type or namespace is missing.</span></span> <span data-ttu-id="89060-158">這是預期的情況，將在下一節匯入 Photon 資產時解決。</span><span class="sxs-lookup"><span data-stu-id="89060-158">This is to be expected and will be resolved in the next section when you import the Photon assets.</span></span>

## <a name="importing-the-photon-assets"></a><span data-ttu-id="89060-159">匯入 Photon 資產</span><span class="sxs-lookup"><span data-stu-id="89060-159">Importing the Photon assets</span></span>

<span data-ttu-id="89060-160">在本節中，您將從 Unity 的資產存放區匯入 Photon Unity 網路 (PUN) 資產。</span><span class="sxs-lookup"><span data-stu-id="89060-160">In this section, you will import the Photon Unity Network (PUN) assets from Unity's Asset Store.</span></span>

<span data-ttu-id="89060-161">在 Unity 功能表中，選取 [視窗]   > [資產存放區]  來開啟 [資產存放區] 視窗，然後從 Exit Games 搜尋並選取 [PUN 2 - 免費]  ，並按一下 [下載]  按鈕，將資產套件下載到您的 Unity 帳戶：</span><span class="sxs-lookup"><span data-stu-id="89060-161">In the Unity menu, select **Window** > **Asset Store** to open the Asset Store window, search for and select **PUN 2 - FREE** from Exit Games, and then click the **Download** button to download the asset package to your Unity account:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-1.png)

<span data-ttu-id="89060-163">下載完成時，請按一下 [匯入]  按鈕來開啟 [匯入 Unity 套件] 視窗：</span><span class="sxs-lookup"><span data-stu-id="89060-163">When the download is complete, click the **Import** button to open the Import Unity Package window:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-2.png)

<span data-ttu-id="89060-165">在 [匯入 Unity 套件] 視窗中，按一下 [全部]  按鈕以確保選取所有資產，然後按一下 [匯入]  按鈕來匯入資產：</span><span class="sxs-lookup"><span data-stu-id="89060-165">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-3.png)

<span data-ttu-id="89060-167">Unity 完成匯入程序之後，Pun 精靈視窗會隨即出現並載入 PUN 設定功能表，您現在可以忽略或關閉此視窗：</span><span class="sxs-lookup"><span data-stu-id="89060-167">Once Unity has completed the import process, the Pun Wizard window will appear with the PUN Setup menu loaded, you can ignore or close this window for now:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-4.png)

## <a name="setting-up-photon"></a><span data-ttu-id="89060-169">設定 Photon</span><span class="sxs-lookup"><span data-stu-id="89060-169">Setting up Photon</span></span>

<span data-ttu-id="89060-170">在本節中，您將建立 Photon 帳戶 (如果您還沒有帳戶的話)，並建立新的 PUN 應用程式。</span><span class="sxs-lookup"><span data-stu-id="89060-170">In this section, you will create a Photon account, if you don't already have one, and create a new PUN application.</span></span>

<span data-ttu-id="89060-171">瀏覽至 Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">儀表板</a> 並登入 (如果您已經有想要使用的帳戶)，否則請按一下 [建立帳戶]  連結，並依照指示註冊新帳戶：</span><span class="sxs-lookup"><span data-stu-id="89060-171">Navigate to the Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">dashboard</a> and sign in if you already have an account you want to use, otherwise, click the **Create One** link and follow the instructions to register a new account:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-1.png)

<span data-ttu-id="89060-173">登入之後，按一下 [建立新的應用程式]  按鈕：</span><span class="sxs-lookup"><span data-stu-id="89060-173">Once signed in, click the **Create a New App** button:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-2.png)

<span data-ttu-id="89060-175">在 [建立新的應用程式] 頁面上，輸入下列值：</span><span class="sxs-lookup"><span data-stu-id="89060-175">On the Create a New Application page, enter the following values:</span></span>

* <span data-ttu-id="89060-176">針對 [Photon 類型]，請選取 [Photon PUN]</span><span class="sxs-lookup"><span data-stu-id="89060-176">For Photon Type, select Photon PUN</span></span>
* <span data-ttu-id="89060-177">針對 [名稱]，請輸入適當的名稱，例如 MRTK Tutorials </span><span class="sxs-lookup"><span data-stu-id="89060-177">For Name, enter a suitable name, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="89060-178">針對 [描述]，您可以選擇性地輸入適當描述</span><span class="sxs-lookup"><span data-stu-id="89060-178">For Description, optionally enter a suitable description</span></span>
* <span data-ttu-id="89060-179">針對 [URL]，請將欄位保留空白</span><span class="sxs-lookup"><span data-stu-id="89060-179">For Url, leave the field empty</span></span>

<span data-ttu-id="89060-180">按一下 [建立]  按鈕以建立新端點：</span><span class="sxs-lookup"><span data-stu-id="89060-180">Then click the **Create** button to create the new application:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-3.png)

<span data-ttu-id="89060-182">當 Photon 完成建立程序後，新的 PUN 應用程式將會出現在儀表板上：</span><span class="sxs-lookup"><span data-stu-id="89060-182">Once Photon has finished the creation process, the new PUN application will appear on your dashboard:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a><span data-ttu-id="89060-184">將 Unity 專案連線至 PUN 應用程式</span><span class="sxs-lookup"><span data-stu-id="89060-184">Connecting the Unity project to the PUN application</span></span>

<span data-ttu-id="89060-185">在本節中，您會將 Unity 專案連線到您在上一節中建立的 PUN 應用程式。</span><span class="sxs-lookup"><span data-stu-id="89060-185">In this section, you will connect your Unity project to the PUN application you created in the previous section.</span></span>

<span data-ttu-id="89060-186">在 Photon 儀表板上，按一下 [應用程式識別碼]  欄位以顯示應用程式識別碼，然後將其複製到您的剪貼簿：</span><span class="sxs-lookup"><span data-stu-id="89060-186">On the Photon dashboard, click the **App ID** field to reveal the app ID, then copy it to your clipboard:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-1.png)

<span data-ttu-id="89060-188">在 Unity 功能表中，選取 [視窗]   > [Photon Unity 網路]   > [PUN 精靈]  以開啟 PUN 精靈視窗，然後按一下 [設定專案]  按鈕以開啟 [PUN 設定] 功能表，並依照下列方式進行設定：</span><span class="sxs-lookup"><span data-stu-id="89060-188">In the Unity menu, select **Window** > **Photon Unity Networking** > **PUN Wizard** to open the Pun Wizard window, click the **Setup Project** button to open the PUN Setup menu, and configure it as follows:</span></span>

* <span data-ttu-id="89060-189">在 [AppId 或電子郵件]  欄位中，貼上您在上一個步驟中複製的 PUN 應用程式識別碼</span><span class="sxs-lookup"><span data-stu-id="89060-189">In the **AppId or Email** field, paste the PUN app ID you copied in the previous step</span></span>

<span data-ttu-id="89060-190">然後按一下 [設定專案]  按鈕來套用應用程式識別碼：</span><span class="sxs-lookup"><span data-stu-id="89060-190">Then click the **Setup Project** button to apply the app ID:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-2.png)

<span data-ttu-id="89060-192">當 Unity 完成 PUN 設定程序後，[PUN 設定] 功能表就會顯示訊息「完成！」  訊息</span><span class="sxs-lookup"><span data-stu-id="89060-192">Once Unity has finished the PUN setup process, the PUN Setup menu will display the message **Done!**</span></span> <span data-ttu-id="89060-193">並自動選取 [專案] 視窗中的 **PhotonServerSettings** 資產，讓其屬性顯示在 [偵測器] 視窗中：</span><span class="sxs-lookup"><span data-stu-id="89060-193">and automatically select the **PhotonServerSettings** asset in the Project window so its properties are displayed in the Inspector window:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="89060-195">恭喜！</span><span class="sxs-lookup"><span data-stu-id="89060-195">Congratulations</span></span>

<span data-ttu-id="89060-196">您已成功建立 Photon PUN 應用程式，並將其連線到您的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="89060-196">You have successfully created a Photon PUN application and connected it to your Unity project.</span></span> <span data-ttu-id="89060-197">下一個步驟是允許與其他使用者連線，讓多個使用者可以看到彼此。</span><span class="sxs-lookup"><span data-stu-id="89060-197">Your next step is to allow connections with other users so that multiple users can see each other.</span></span>

<span data-ttu-id="89060-198">[下一個教學課程：2.連線多個使用者](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="89060-198">[Next tutorial: 2. Connecting multiple users](mrlearning-sharing(photon)-ch2.md)</span></span>
