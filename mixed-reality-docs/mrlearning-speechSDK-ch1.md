---
title: Azure 語音服務教學課程 - 1。 整合並使用語音辨識和文字記錄
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 語音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 71a6c2124258f05e80e624b940386db72a36070b
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604979"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="03ef1-105">1.整合並使用語音辨識和文字記錄</span><span class="sxs-lookup"><span data-stu-id="03ef1-105">1. Integrating and using speech recognition and transcription</span></span>

## <a name="overview"></a><span data-ttu-id="03ef1-106">概觀</span><span class="sxs-lookup"><span data-stu-id="03ef1-106">Overview</span></span>


<span data-ttu-id="03ef1-107">在此教學課程系列中，您將建立一個混合實境應用程式，以探索 Azure 語音服務與 HoloLens 2 的使用方式。</span><span class="sxs-lookup"><span data-stu-id="03ef1-107">In this tutorial series, you will create a Mixed Reality application that explores the use of Azure Speech Services with the HoloLens 2.</span></span> <span data-ttu-id="03ef1-108">當您完成本教學課程系列時，您將能夠使用裝置的麥克風即時將語音轉譯成文字、將語音翻譯成其他語言，以及利用意圖辨識功能來使用人工智慧了解語音命令。</span><span class="sxs-lookup"><span data-stu-id="03ef1-108">When you complete this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Intent recognition feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="03ef1-109">目標</span><span class="sxs-lookup"><span data-stu-id="03ef1-109">Objectives</span></span>

* <span data-ttu-id="03ef1-110">了解如何將 Azure 語音服務與 HoloLens 2 應用程式整合</span><span class="sxs-lookup"><span data-stu-id="03ef1-110">Learn how to integrate Azure Speech Services with a HoloLens 2 application</span></span>
* <span data-ttu-id="03ef1-111">了解如何使用語音辨識來轉譯文字</span><span class="sxs-lookup"><span data-stu-id="03ef1-111">Learn how to use speech recognition to transcribe text</span></span>

## <a name="prerequisites"></a><span data-ttu-id="03ef1-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="03ef1-112">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="03ef1-113">如果您尚未完成[入門教學課程](mrlearning-base.md)系列，建議您先完成這些教學課程。</span><span class="sxs-lookup"><span data-stu-id="03ef1-113">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="03ef1-114">已[安裝正確工具](install-the-tools.md)的 Windows 10 電腦</span><span class="sxs-lookup"><span data-stu-id="03ef1-114">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="03ef1-115">Windows 10 SDK 10.0.18362.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="03ef1-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="03ef1-116">基本的 C# 程式設計能力</span><span class="sxs-lookup"><span data-stu-id="03ef1-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="03ef1-117">已[針對開發而設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置</span><span class="sxs-lookup"><span data-stu-id="03ef1-117">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="03ef1-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，已安裝 Unity 2019.2，且已新增通用 Windows 平台組建支援模組</span><span class="sxs-lookup"><span data-stu-id="03ef1-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="03ef1-119">本教學課程系列的建議 Unity 版本是 Unity 2019.2. X。</span><span class="sxs-lookup"><span data-stu-id="03ef1-119">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="03ef1-120">這個版本能取代上述連結之必要條件中所述的任何 Unity 版本需求或建議。</span><span class="sxs-lookup"><span data-stu-id="03ef1-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="03ef1-121">建立和準備 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="03ef1-121">Creating and preparing the Unity project</span></span>

<span data-ttu-id="03ef1-122">在本節中，您將建立新的 Unity 專案，並使該專案準備好進行 MRTK 開發。</span><span class="sxs-lookup"><span data-stu-id="03ef1-122">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="03ef1-123">為此，請先遵循[初始化您的專案和第一個應用程式](mrlearning-base-ch1.md) (但不包括[對您的裝置建置應用程式](mrlearning-base-ch1.md#build-your-application-to-your-device)的指示)，其中包括下列步驟：</span><span class="sxs-lookup"><span data-stu-id="03ef1-123">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="03ef1-124">[建立新的 Unity 專案](mrlearning-base-ch1.md#create-new-unity-project)，並為其提供適當的名稱，例如「MRTK 教學課程」 </span><span class="sxs-lookup"><span data-stu-id="03ef1-124">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

2. [<span data-ttu-id="03ef1-125">設定適用於 Windows Mixed Reality 的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="03ef1-125">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="03ef1-126">匯入 TextMesh Pro 基本資源</span><span class="sxs-lookup"><span data-stu-id="03ef1-126">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="03ef1-127">匯入混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="03ef1-127">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="03ef1-128">設定用於混合實境工具組的 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="03ef1-128">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="03ef1-129">[將 Mixed Reality 工具組新增至 Unity 場景](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)並為場景提供適當的名稱，例如 AzureSpeechServices </span><span class="sxs-lookup"><span data-stu-id="03ef1-129">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *AzureSpeechServices*</span></span>

<span data-ttu-id="03ef1-130">然後遵循[如何設定混合實境工具組設定檔 (變更空間感知顯示選項)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) 的指示，將場景的 MRTK 組態設定檔變更為 **DefaultHoloLens2ConfigurationProfile**，並將空間感知網格的顯示選項變更為 [遮蔽]  。</span><span class="sxs-lookup"><span data-stu-id="03ef1-130">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="03ef1-131">如上方連結：[設定用於混合實境工具組的 Unity 專案](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)中所述的指示，強烈建議您不要為 Unity 啟用 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="03ef1-131">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="configuring-the-speech-commands-start-behavior"></a><span data-ttu-id="03ef1-132">設定語音命令啟動行為</span><span class="sxs-lookup"><span data-stu-id="03ef1-132">Configuring the speech commands start behavior</span></span>

<span data-ttu-id="03ef1-133">由於您將使用語音 SDK 進行語音辨識和轉譯，因此您需要設定 MRTK 語音命令，使其不會干擾語音 SDK 功能。</span><span class="sxs-lookup"><span data-stu-id="03ef1-133">Because you will use the Speech SDK for speech recognition and transcription you need to configure the MRTK Speech Commands so they do not interfere with the Speech SDK functionality.</span></span> <span data-ttu-id="03ef1-134">若要達到此目的，您可以將語音命令啟動行為從 [自動啟動] 變更為 [手動啟動]。</span><span class="sxs-lookup"><span data-stu-id="03ef1-134">To achieve this you can change the speech commands start behavior from Auto Start to Manual Start.</span></span>

<span data-ttu-id="03ef1-135">在 [階層] 視窗中選取 **MixedRealityToolkit** 物件之後，於 [偵測器] 視窗中選取 [輸入]  索引標籤，並複製 **DefaultHoloLens2InputSystemProfile** 和 **DefaultMixedRealitySpeechCommandsProfile**，然後將**啟動行為**的語音命令變更為 [手動啟動]  ：</span><span class="sxs-lookup"><span data-stu-id="03ef1-135">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, select the **Input** tab, clone the **DefaultHoloLens2InputSystemProfile** and the **DefaultMixedRealitySpeechCommandsProfile**, and then change the speech commands **Start Behavior** to **Manual Start**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="03ef1-137">如需有關如何複製和設定 MRTK 設定檔的提示，您可以參閱[如何設定混合實境工具組設定檔 (變更空間感知顯示選項)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) 的指示。</span><span class="sxs-lookup"><span data-stu-id="03ef1-137">For a reminder on how to clone and configure MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="03ef1-138">設定功能</span><span class="sxs-lookup"><span data-stu-id="03ef1-138">Configuring the capabilities</span></span>

<span data-ttu-id="03ef1-139">在 Unity 功能表中，選取 [編輯]   > [專案設定...]  來開啟 [玩家設定] 視窗，然後找出 [玩家]   >  [發佈設定]  區段：</span><span class="sxs-lookup"><span data-stu-id="03ef1-139">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-1.png)

<span data-ttu-id="03ef1-141">在 [發佈設定]  中，向下捲動至 [功能]  區段，然後再次確認您在教學課程開頭建立專案時所啟用的 **InternetClient**、**Microphone** 和 **SpatialPerception** 功能是否皆已啟用。</span><span class="sxs-lookup"><span data-stu-id="03ef1-141">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="03ef1-142">然後，啟用 **InternetClientServer** 和 **PrivateNetworkClientServer** 功能：</span><span class="sxs-lookup"><span data-stu-id="03ef1-142">Then, enable the **InternetClientServer** and **PrivateNetworkClientServer** capabilities:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="03ef1-144">匯入教學課程資產</span><span class="sxs-lookup"><span data-stu-id="03ef1-144">Importing the tutorial assets</span></span>

<span data-ttu-id="03ef1-145">下載並**依列出順序**來**匯入**下列 Unity 自訂套件：</span><span class="sxs-lookup"><span data-stu-id="03ef1-145">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="03ef1-146">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (最新版本)</span><span class="sxs-lookup"><span data-stu-id="03ef1-146">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (latest version)</span></span>
* [<span data-ttu-id="03ef1-147">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="03ef1-147">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="03ef1-148">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="03ef1-148">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-speech-services-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="03ef1-149">如需有關如何匯入 Unity 自訂套件的提示，您可以參閱[匯入混合實境工具組](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) 的指示。</span><span class="sxs-lookup"><span data-stu-id="03ef1-149">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="03ef1-150">匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：</span><span class="sxs-lookup"><span data-stu-id="03ef1-150">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section4-step1-1.png)

## <a name="preparing-the-scene"></a><span data-ttu-id="03ef1-152">準備場景</span><span class="sxs-lookup"><span data-stu-id="03ef1-152">Preparing the scene</span></span>

<span data-ttu-id="03ef1-153">在本節中，您將藉由新增教學課程 Prefab 來準備場景，並設定 Lunarcom Controller (指令碼) 元件來控制您的場景。</span><span class="sxs-lookup"><span data-stu-id="03ef1-153">In this section, you will prepare the scene by adding the tutorial prefab and configure the Lunarcom Controller (Script) component to control your scene.</span></span>

<span data-ttu-id="03ef1-154">在 [專案] 視窗中，瀏覽至 [資產]   > [MRTK.Tutorials.AzureSpeechServices]   > [Prefabs]  資料夾，並將 **Lunarcom** Prefab 拖曳至 [階層] 視窗來新增至您的場景：</span><span class="sxs-lookup"><span data-stu-id="03ef1-154">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** folder and drag the **Lunarcom** prefab into the Hierarchy window to add it to your scene:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-1.png)

<span data-ttu-id="03ef1-156">在 [階層] 視窗中仍選取 **Lunarcom** 物件的情況下，於 [偵測器] 視窗中使用 [新增元件]  按鈕來將 **Lunarcom Controller (指令碼)** 元件新增至 Lunarcom 物件：</span><span class="sxs-lookup"><span data-stu-id="03ef1-156">With the **Lunarcom** object still selected in the Hierarchy window, in the Inspector window, use the **Add Component** button to add the **Lunarcom Controller (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> <span data-ttu-id="03ef1-158">The Lunarcom Controller (指令碼) 元件不是 MRTK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="03ef1-158">The Lunarcom Controller (Script) component is not part of MRTK.</span></span> <span data-ttu-id="03ef1-159">這是本教學課程資產隨附的元件。</span><span class="sxs-lookup"><span data-stu-id="03ef1-159">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="03ef1-160">在仍選取 **Lunarcom** 物件的情況下，將其展開以顯示其子物件，然後將**Terminal** 物件拖曳到 Lunarcom Controller (指令碼) 元件的 [終端機]  欄位中：</span><span class="sxs-lookup"><span data-stu-id="03ef1-160">With the **Lunarcom** object still selected, expand it to reveal its child objects, then drag the **Terminal** object into the Lunarcom Controller (Script) component's **Terminal** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-3.png)

<span data-ttu-id="03ef1-162">在仍選取 **Lunarcom** 物件的情況下，展開 [終端機] 物件以顯示其子物件，然後將 **ConnectionLight** 物件拖曳至 Lunarcom Controller (指令碼) 元件的 [連接光源]  欄位，並將 **OutputText** 物件拖曳至 [輸出文字]  欄位中：</span><span class="sxs-lookup"><span data-stu-id="03ef1-162">With the **Lunarcom** object still selected, expand the Terminal object to reveal its child objects, then drag the **ConnectionLight** object into the Lunarcom Controller (Script) component's **Connection Light** field and the **OutputText** object into the **Output Text** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-4.png)

<span data-ttu-id="03ef1-164">在仍選取 **Lunarcom** 物件的情況下，展開 Buttons 物件以顯示其子物件，然後在 [偵測器] 視窗中展開 [按鈕]  清單，將其 [大小]  設定為 3，然後將 **MicButton**、**SatelliteButton** 和 **RocketButton** 物件分別拖曳至**元素** 0、1 及 2 的欄位：</span><span class="sxs-lookup"><span data-stu-id="03ef1-164">With the **Lunarcom** object still selected, expand the Buttons object to reveal its child objects, and then in the Inspector window, expand the **Buttons** list, set its **Size** to 3, and drag the **MicButton**, **SatelliteButton**, and **RocketButton** objects into the **Element** 0, 1, and 2 fields respectively:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a><span data-ttu-id="03ef1-166">將 Unity 專案連接至 Azure 資源</span><span class="sxs-lookup"><span data-stu-id="03ef1-166">Connecting the Unity project to the Azure resource</span></span>

<span data-ttu-id="03ef1-167">若要使用 Azure 語音服務，您必須建立 Azure 資源，並取得語音服務的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="03ef1-167">To use Azure Speech Services, you need to create an Azure resource and obtain an API key for the Speech Service.</span></span> <span data-ttu-id="03ef1-168">請遵循[免費試用語音服務](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started)的指示，並記下您的服務區域 (也就是「位置」) 和 API 金鑰 (也就是 Key1 或 Key2)。</span><span class="sxs-lookup"><span data-stu-id="03ef1-168">Follow the [Try the Speech service for free](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) instructions and make a note of your service region (also known as Location) and API key (also known as Key1 or Key2).</span></span>

<span data-ttu-id="03ef1-169">在 [階層] 視窗中選取 **Lunarcom** 物件，然後在 [偵測器] 視窗中尋找 **Lunarcom Controller (指令碼)** 元件的 [語音 SDK 認證]  區段並進行設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="03ef1-169">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Controller (Script)** component's **Speech SDK Credentials** section and configure it as follows:</span></span>

* <span data-ttu-id="03ef1-170">在 [語音服務 API 金鑰]  欄位中，輸入您的 API 金鑰 (Key1 或 Key2)</span><span class="sxs-lookup"><span data-stu-id="03ef1-170">In the **Speech Service API Key** field, enter your API key (Key1 or Key2)</span></span>
* <span data-ttu-id="03ef1-171">在 [語音服務區域]  欄位中，輸入您的服務區域 (位置)，請使用小寫字母並將空格移除</span><span class="sxs-lookup"><span data-stu-id="03ef1-171">In the **Speech Service Region** field, enter your service region (Location) using lowercase letters and spaces removed</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a><span data-ttu-id="03ef1-173">使用語音辨識來轉譯語音</span><span class="sxs-lookup"><span data-stu-id="03ef1-173">Using speech recognition to transcribe speech</span></span>

<span data-ttu-id="03ef1-174">在 [階層] 視窗中選取 **Lunarcom** 物件，然後在 [偵測器] 視窗中使用 [新增元件]  按鈕來將 **Lunarcom Speech Recognizer (指令碼)** 元件新增至 Lunarcom 物件：</span><span class="sxs-lookup"><span data-stu-id="03ef1-174">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Speech Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> <span data-ttu-id="03ef1-176">Lunarcom Speech Recognizer (指令碼) 元件不是 MRTK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="03ef1-176">The Lunarcom Speech Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="03ef1-177">這是本教學課程資產隨附的元件。</span><span class="sxs-lookup"><span data-stu-id="03ef1-177">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="03ef1-178">如果您現在進入遊戲模式，您可以先按下麥克風按鈕來測試語音辨識：</span><span class="sxs-lookup"><span data-stu-id="03ef1-178">If you now enter Game mode, you can test the speech recognition by first pressing the microphone button:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-2.png)

<span data-ttu-id="03ef1-180">接下來，假設您的電腦有麥克風，當您說到某個項目時，您的語音會在終端機面板上進行轉譯：</span><span class="sxs-lookup"><span data-stu-id="03ef1-180">Then, assuming your computer has a microphone, when you say something, your speech will be transcribed on the terminal panel:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-3.png)


> [!CAUTION]
> <span data-ttu-id="03ef1-182">應用程式必須連線到 Azure，因此請確定您的電腦/裝置已連線到網際網路。</span><span class="sxs-lookup"><span data-stu-id="03ef1-182">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="03ef1-183">恭喜！</span><span class="sxs-lookup"><span data-stu-id="03ef1-183">Congratulations</span></span>

<span data-ttu-id="03ef1-184">您已實行由 Azure 提供技術支援的語音辨識。</span><span class="sxs-lookup"><span data-stu-id="03ef1-184">You have implemented speech recognition powered by Azure.</span></span> <span data-ttu-id="03ef1-185">在您的裝置上執行應用程式，以確保功能可正常運作。</span><span class="sxs-lookup"><span data-stu-id="03ef1-185">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="03ef1-186">在下一個教學課程中，您將了解如何使用 Azure 語音辨識來執行命令。</span><span class="sxs-lookup"><span data-stu-id="03ef1-186">In the next tutorial, you will learn how to execute commands using Azure speech recognition.</span></span>

[<span data-ttu-id="03ef1-187">下一個教學課程：2.使用語音辨識來執行命令</span><span class="sxs-lookup"><span data-stu-id="03ef1-187">Next tutorial: 2. Using speech recognition to execute commands</span></span>](mrlearning-speechSDK-ch2.md)
