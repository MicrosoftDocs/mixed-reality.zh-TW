---
title: Azure Spatial Anchors 教學課程 - 4. 適用於 Android 和 iOS 的 Azure Spatial Anchors
description: 完成此教學課程以了解如何在混合實境應用程式中實作 Azure Spatial Anchors。
author: jessemcculloch
ms.author: jemccull
ms.date: 05/18/2020
ms.topic: article
keywords: 混合實境、unity、教學課程、課程、hololens、azure、空間錨點
ms.localizationpriority: high
ms.openlocfilehash: 78fa6a2cdd29bd424ec3016a5467760063b87a14
ms.sourcegitcommit: 7011ac6fde80e5c45f04192fa1db6e1eb559e3b0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2020
ms.locfileid: "84327924"
---
# <a name="4-azure-spatial-anchors-for-android-and-ios"></a><span data-ttu-id="5da9a-105">4.適用於 Android 和 iOS 的 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="5da9a-105">4. Azure Spatial Anchors for Android and iOS</span></span>

<span data-ttu-id="5da9a-106">在本教學課程中，您將了解如何使用 AR Foundation、ARCore XR 外掛程式和 ARKit XR 外掛程式，在 Android 和 iOS 裝置上建置專案。</span><span class="sxs-lookup"><span data-stu-id="5da9a-106">In this tutorial, you will learn how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

## <a name="objectives"></a><span data-ttu-id="5da9a-107">目標</span><span class="sxs-lookup"><span data-stu-id="5da9a-107">Objectives</span></span>

* <span data-ttu-id="5da9a-108">了解如何使用 Unity AR Foundation 和 ARCore XR 外掛程式，在 Android 裝置上建置專案。</span><span class="sxs-lookup"><span data-stu-id="5da9a-108">Learn how to build your project to Android device using Unity AR Foundation and ARCore XR Plugin.</span></span>
* <span data-ttu-id="5da9a-109">了解如何使用 Unity AR Foundation 和 ARKit XR 外掛程式，在 iOS 裝置上建置專案。</span><span class="sxs-lookup"><span data-stu-id="5da9a-109">Learn how to build your project to an iOS device using Unity AR Foundation and ARKit XR Plugin.</span></span>

> [!NOTE]
> <span data-ttu-id="5da9a-110">若要完成本教學課程，請確定您已完成 Azure Spatial Anchors 教學課程 -> [開始使用 Azure Spatial Anchors](mrlearning-asa-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="5da9a-110">To complete this tutorial, make sure you have completed Azure Spatial Anchors Tutorials -> [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md).</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="5da9a-111">新增內建的 Unity 套件</span><span class="sxs-lookup"><span data-stu-id="5da9a-111">Adding inbuilt Unity packages</span></span>

<span data-ttu-id="5da9a-112">在本節中，您將安裝支援 Android 和 iOS 裝置所需的 Unity 內建 AR Foundation、ARCore XR 外掛程式和 ARKit XR 外掛程式套件。</span><span class="sxs-lookup"><span data-stu-id="5da9a-112">In this section, you will install Unity inbuilt AR Foundation, ARCore XR Plugin, and ARKit XR Plugin packages required to support Android and iOS devices.</span></span>

<span data-ttu-id="5da9a-113">請確定您已安裝這些 Unity 套件的正確版本，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5da9a-113">Make sure you install the correct version of these Unity packages as listed below:</span></span>

* <span data-ttu-id="5da9a-114">**AR Foundation 2.1.4**</span><span class="sxs-lookup"><span data-stu-id="5da9a-114">**AR Foundation 2.1.4**</span></span>
* <span data-ttu-id="5da9a-115">**ARCore XR 外掛程式 2.2.0 預覽版 2**</span><span class="sxs-lookup"><span data-stu-id="5da9a-115">**ARCore XR plugin 2.2.0 preview 2**</span></span>
* <span data-ttu-id="5da9a-116">**ARKit XR 外掛程式 2.1.1**</span><span class="sxs-lookup"><span data-stu-id="5da9a-116">**ARKit XR plugin 2.1.1**</span></span>

> [!NOTE]
> <span data-ttu-id="5da9a-117">如果您正針對 Android 開發本專案，則不需要安裝 ARKit XR 外掛程式套件。</span><span class="sxs-lookup"><span data-stu-id="5da9a-117">If you are developing this project for Android, there is no need to install the ARKit XR Plugin package.</span></span> <span data-ttu-id="5da9a-118">同樣地，如果您要針對 iOS 開發本專案，就不需要安裝 ARCore XR 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="5da9a-118">Similarly, if you are developing this project for iOS, you do not need to install the ARCore XR Plugin.</span></span>

<span data-ttu-id="5da9a-119">在 Unity 功能表中，選取 [視窗] >  **[套件管理員]** ：</span><span class="sxs-lookup"><span data-stu-id="5da9a-119">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-1.png)

<span data-ttu-id="5da9a-121">可能需要幾秒鐘的時間，清單中才會出現所有套件。</span><span class="sxs-lookup"><span data-stu-id="5da9a-121">It might take a few seconds before all packages appear in the list.</span></span> <span data-ttu-id="5da9a-122">按一下 [進階] 選項，然後選取 [顯示預覽套件]，以顯示預覽套件。</span><span class="sxs-lookup"><span data-stu-id="5da9a-122">Display preview packages by clicking on Advanced option and select **Show preview packages.**</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-2.png)

<span data-ttu-id="5da9a-124">在 [套件管理員] 視窗中，選取 [AR Foundation]，您會在此看到許多版本，且需要選取 [版本 2.1.4]，然後按一下 [更新至 2.1.4] 按鈕以更新套件：</span><span class="sxs-lookup"><span data-stu-id="5da9a-124">In the Package Manager window, select **AR Foundation**, here you see many version and need to select **version 2.1.4** and update the package by clicking the **Update to 2.1.4** button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-3.png)

<span data-ttu-id="5da9a-126">若要支援 Android 裝置，請遵循相同的程序來匯入 **ARCore XR 外掛程式 2.2.0 預覽版 2**。</span><span class="sxs-lookup"><span data-stu-id="5da9a-126">To support Android devices, follow the same process to import **ARCore XR Plugin 2.2.0 preview 2**.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-4.png)

<span data-ttu-id="5da9a-128">若要支援 iOS 裝置，您應該從套件管理員匯入 **ARKit XR 外掛程式 2.1.1** Unity 套件。</span><span class="sxs-lookup"><span data-stu-id="5da9a-128">To support iOS devices, you should import the **ARKit XR plugin 2.1.1** Unity package from the Package Manager.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-5.png)

## <a name="customize-mrtk-to-support-ar-foundation-camera"></a><span data-ttu-id="5da9a-130">自訂 MRTK 以支援 AR Foundation 相機</span><span class="sxs-lookup"><span data-stu-id="5da9a-130">Customize MRTK to support AR Foundation camera</span></span>

<span data-ttu-id="5da9a-131">在 [階層] 視窗中選取 [MixedRealityToolKit]，然後在 [偵測器] 視窗中，按一下 [混合實境工具組] 中的 [複製] 按鈕，以自訂 MRTK 設定以支援 AR Foundation。</span><span class="sxs-lookup"><span data-stu-id="5da9a-131">Customize MRTK settings to support AR Foundation by selecting MixedRealityToolKit in the Hierarchy window and click the **Clone** button in Mixed Reality ToolKit in the Inspector window.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-1.png)

<span data-ttu-id="5da9a-133">當您按一下 [複製] 按鈕時，會出現新的 [複製設定檔] 視窗，然後再按一下 [複製] 按鈕來複製 **DefaultMixedRealityToolkitProfile**。</span><span class="sxs-lookup"><span data-stu-id="5da9a-133">When you click the **Clone** button, a new clone Profile window will appear, click on the **Clone** button again to clone the **DefaultMixedRealityToolkitProfile**.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-2.png)

<span data-ttu-id="5da9a-135">同樣地，在 [偵測器] 視窗中複製 [相機設定檔]。</span><span class="sxs-lookup"><span data-stu-id="5da9a-135">Similarly, clone the **Camera Profile** in the Inspector window.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-3.png)

<span data-ttu-id="5da9a-137">在 [偵測器] 視窗中，找出 MixedReality，並選取 [相機] 索引標籤。展開 [偵測器] 視窗中的相機設定提供者，然後按一下 [+ 新增相機設定提供者] > 展開 [新的資料提供者 1] > 選取類型 [無] > 選取 [Microsoft.MixedReality.Toolkit.Experimental.UnityAR] > 選取 [UnityARCameraSettings]。</span><span class="sxs-lookup"><span data-stu-id="5da9a-137">In the Inspector window, locate the MixedReality, select the **Camera** tab. Expand the camera setting providers in the inspector window and click on **+ Add Camera Setting Provider** > expand **New data provider 1** > select type **None** > select **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > select **UnityARCameraSettings**.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-4.png)

<span data-ttu-id="5da9a-139">在 [階層] 視窗中選取 MixedRealityToolKit 物件之後，在 [偵測器] 視窗中按一下 [新增元件] 按鈕，然後輸入 AR 參考點管理員並選取指令碼，即可附加支援的指令碼。</span><span class="sxs-lookup"><span data-stu-id="5da9a-139">With the MixedRealityToolKit object selected in the Hierarchy window, In the Inspector window, attach supporting scripts by clicking on the **Add component** button and type in AR reference Point manager and select the script.</span></span>

<span data-ttu-id="5da9a-140">新增 [AR 參考點管理員] 指令碼會自動將 [AR 工作階段來源] 新增至 [偵測器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="5da9a-140">Adding the  **AR Reference Point Manager** script will automatically add **AR session origin** to the Inspector window.</span></span> <span data-ttu-id="5da9a-141">新增支援的指令碼之後，[偵測器] 視窗外觀如下所示。</span><span class="sxs-lookup"><span data-stu-id="5da9a-141">After adding the supporting scripts, the Inspector window should look like this.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-5.png)

## <a name="build-an-application-to-an-android-device"></a><span data-ttu-id="5da9a-143">將應用程式建置到 Android 裝置</span><span class="sxs-lookup"><span data-stu-id="5da9a-143">Build an application to an Android device</span></span>

<span data-ttu-id="5da9a-144">若要將此應用程式建置到 Android 裝置，請按一下視窗頂端的 [檔案]，然後選取 [建置設定]。</span><span class="sxs-lookup"><span data-stu-id="5da9a-144">To build this application to your Android device, click on **File** at the top of the window and select **Build Settings.**</span></span> <span data-ttu-id="5da9a-145">畫面上會出現新的視窗，選取 [Android]，然後按一下 [切換平台]。</span><span class="sxs-lookup"><span data-stu-id="5da9a-145">A new window will appear on the screen, select **Android**, and click on the **Switch Platform**.</span></span> <span data-ttu-id="5da9a-146">切換平台需要幾分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="5da9a-146">It will take a few minutes to switch platform.</span></span> <span data-ttu-id="5da9a-147">切換至 Android 平台之後，按一下 [新增開啟場景]，並確定您目前的場景是 [組建中的場景] 清單中唯一選取的場景。</span><span class="sxs-lookup"><span data-stu-id="5da9a-147">After switching to the Android platform, click on **Add Open Scenes** and make sure your current scene is the only selected scene in the **Scenes In Build** list.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-1.png)

<span data-ttu-id="5da9a-149">關閉 [建置設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="5da9a-149">Close the **Build Settings** window.</span></span> <span data-ttu-id="5da9a-150">在 Unity 功能表中，選取 [混合實境工具組] > [公用程式] > [設定 Unity 專案] ，然後按一下 [套用] 來設定 Android 平台的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="5da9a-150">In the Unity menu, select Mixed Reality Toolkit > Utilities > Configure Unity Project and click on **Apply** to configure the Unity project for the Android platform.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-2.png)

<span data-ttu-id="5da9a-152">在 Unity 功能表中，選取 [編輯]  >  [專案設定] 來開啟 [專案設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="5da9a-152">In the Unity menu, select **Edit** > **Project Settings** to open the Project Settings window.</span></span> <span data-ttu-id="5da9a-153">在 [專案設定] 視窗中，選取 [玩家] 索引標籤，展開 [其他設定] 區段，選取 [Vulkan]，並按一下 " **-** " 符號將其移除。</span><span class="sxs-lookup"><span data-stu-id="5da9a-153">In the Project Settings, window selects the **Player** tab, expand the **Other Settings** section, select **Vulkan**, and remove it by clicking the "**-**" symbol.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-3.png)

<span data-ttu-id="5da9a-155">關閉 [玩家設定] 視窗，然後再次開啟 [建置設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="5da9a-155">Close the **Player Settings** window and open the **Build Settings** window again.</span></span> <span data-ttu-id="5da9a-156">接著，使用 USB 纜線將 Android 裝置連接到您的電腦，並在 [建置並執行] 下拉式清單中選取您的裝置，再按一下 [建置並執行]。</span><span class="sxs-lookup"><span data-stu-id="5da9a-156">Then, using a USB cable, connect your Android device to your computer and select your device in the **Build and Run** on the dropdown, then click **Build And Run**.</span></span> <span data-ttu-id="5da9a-157">系統會要求您儲存 .apk 檔案，您可以選擇任何名稱。</span><span class="sxs-lookup"><span data-stu-id="5da9a-157">You will be asked to save a .apk file, which you can pick any name.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-4.png)

> [!NOTE]
> <span data-ttu-id="5da9a-159">如果您在 Unity 主控台視窗中遇到與 Android SDK、NDK 和/或 JDK 模組相關的任何錯誤，則需要開啟 Unity Hub，並安裝適用於 Android 建置支援模組相關聯的 SDK、NDK 和 JDK 模組。</span><span class="sxs-lookup"><span data-stu-id="5da9a-159">If you get any error in the Unity Console window related to Android SDK, NDK, and or JDK modules, you need to open Unity Hub and install the associated SDK, NDK, and JDK modules for the Android Build Support module.</span></span>

<span data-ttu-id="5da9a-160">當建置程序完成時，應用程式應該會自動載入您的 Android 裝置。</span><span class="sxs-lookup"><span data-stu-id="5da9a-160">When the build process is complete, your applications should automatically load on your Android device.</span></span>

## <a name="build-an-application-to-ios-device"></a><span data-ttu-id="5da9a-161">將應用程式建置到 iOS 裝置</span><span class="sxs-lookup"><span data-stu-id="5da9a-161">Build an application to iOS Device</span></span>

<span data-ttu-id="5da9a-162">若要將此應用程式建置到 iOS 裝置，請按一下視窗頂端的 [檔案]，然後選取 [組建設定]。</span><span class="sxs-lookup"><span data-stu-id="5da9a-162">To build this application to your iOS device, click on **File** at the top of the window and select **Build Settings.**</span></span> <span data-ttu-id="5da9a-163">畫面上會出現新的視窗，選取 [iOS]，然後按一下 [切換平台]。</span><span class="sxs-lookup"><span data-stu-id="5da9a-163">A new window will appear on the screen, then select **iOS** and click on the **Switch Platform**.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-1.png)

<span data-ttu-id="5da9a-165">關閉 [建置設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="5da9a-165">Close the **Build Settings** window.</span></span> <span data-ttu-id="5da9a-166">在 Unity 功能表中，選取 [混合實境工具組] > [公用程式] > [設定 Unity 專案] ，然後按一下 [套用] 來設定 iOS 平台的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="5da9a-166">In the Unity menu, select Mixed Reality Toolkit > Utilities > Configure Unity Project, and click on **Apply** to configure the Unity project for the iOS platform.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-2.png)

<span data-ttu-id="5da9a-168">若要建置 iOS XCode 專案，請移至 [建置設定]，然後按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="5da9a-168">To build the iOS XCode project, go to Build Settings, and click on **Build**.</span></span>

<span data-ttu-id="5da9a-169">請遵循[本指南](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project)，以了解如何將此專案部署至您的 iOS 裝置。</span><span class="sxs-lookup"><span data-stu-id="5da9a-169">Follow [this guide](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) to learn how to deploy this project to your iOS device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="5da9a-170">恭喜！</span><span class="sxs-lookup"><span data-stu-id="5da9a-170">Congratulations</span></span>

<span data-ttu-id="5da9a-171">在本教學課程中，您已了解如何針對 Android 和 iOS 裝置建置專案。</span><span class="sxs-lookup"><span data-stu-id="5da9a-171">In this tutorial, you learned how to build your project for Android and iOS devices.</span></span> <span data-ttu-id="5da9a-172">您也了解如何使用 AR Foundation、ARCore XR 外掛程式和 ARKit XR 外掛程式，讓您的專案適用於 Android 和 iOS 裝置。</span><span class="sxs-lookup"><span data-stu-id="5da9a-172">You also learned how to use AR Foundation, ARCore XR Plugin, and ARKit XR Plugin to make your project work for Android and iOS devices.</span></span>
