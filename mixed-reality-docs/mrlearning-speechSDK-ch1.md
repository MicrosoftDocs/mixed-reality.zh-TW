---
title: Azure 語音服務教學課程 - 1。 整合並使用語音辨識和文字記錄
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 語音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: f376ab268e9c2869e48b325fa728672a16ee6d32
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303679"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="10979-105">1.整合並使用語音辨識和文字記錄</span><span class="sxs-lookup"><span data-stu-id="10979-105">1. Integrating and using speech recognition and transcription</span></span>

## <a name="overview"></a><span data-ttu-id="10979-106">概觀</span><span class="sxs-lookup"><span data-stu-id="10979-106">Overview</span></span>


<span data-ttu-id="10979-107">在此教學課程系列中，您將建立一個混合實境應用程式，以探索 Azure 語音服務與 HoloLens 2 的使用方式。</span><span class="sxs-lookup"><span data-stu-id="10979-107">In this tutorial series, you will create a Mixed Reality application that explores the use of Azure Speech Services with the HoloLens 2.</span></span> <span data-ttu-id="10979-108">當您完成本教學課程系列時，您將能夠使用裝置的麥克風即時將語音轉譯成文字、將語音翻譯成其他語言，以及利用意圖辨識功能來使用人工智慧了解語音命令。</span><span class="sxs-lookup"><span data-stu-id="10979-108">When you complete this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Intent recognition feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="10979-109">目標</span><span class="sxs-lookup"><span data-stu-id="10979-109">Objectives</span></span>

* <span data-ttu-id="10979-110">了解如何將 Azure 語音服務與 HoloLens 2 應用程式整合</span><span class="sxs-lookup"><span data-stu-id="10979-110">Learn how to integrate Azure Speech Services with a HoloLens 2 application</span></span>
* <span data-ttu-id="10979-111">了解如何使用語音辨識來轉譯文字</span><span class="sxs-lookup"><span data-stu-id="10979-111">Learn how to use speech recognition to transcribe text</span></span>

## <a name="prerequisites"></a><span data-ttu-id="10979-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="10979-112">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="10979-113">如果您尚未完成[入門教學課程](mr-learning-base-01.md)系列，建議您先完成這些教學課程。</span><span class="sxs-lookup"><span data-stu-id="10979-113">If you have not completed the [Getting started tutorials](mr-learning-base-01.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="10979-114">已[安裝正確工具](install-the-tools.md)的 Windows 10 電腦</span><span class="sxs-lookup"><span data-stu-id="10979-114">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="10979-115">Windows 10 SDK 10.0.18362.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="10979-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="10979-116">基本的 C# 程式設計能力</span><span class="sxs-lookup"><span data-stu-id="10979-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="10979-117">已[針對開發而設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置</span><span class="sxs-lookup"><span data-stu-id="10979-117">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="10979-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，已安裝 Unity 2019.2，且已新增通用 Windows 平台組建支援模組</span><span class="sxs-lookup"><span data-stu-id="10979-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="10979-119">本教學課程系列的建議 Unity 版本是 Unity 2019.2. X。</span><span class="sxs-lookup"><span data-stu-id="10979-119">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="10979-120">這個版本能取代上述連結之必要條件中所述的任何 Unity 版本需求或建議。</span><span class="sxs-lookup"><span data-stu-id="10979-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="10979-121">建立和準備 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="10979-121">Creating and preparing the Unity project</span></span>

<span data-ttu-id="10979-122">在本節中，您將建立新的 Unity 專案，並使該專案準備好進行 MRTK 開發。</span><span class="sxs-lookup"><span data-stu-id="10979-122">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="10979-123">為此，請先遵循[初始化您的專案和第一個應用程式](mr-learning-base-02.md) (但不包括[對您的裝置建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示)，其中包括下列步驟：</span><span class="sxs-lookup"><span data-stu-id="10979-123">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="10979-124">[建立 Unity 專案](mr-learning-base-02.md#creating-the-unity-project)，並為其提供適當的名稱，例如「MRTK 教學課程」</span><span class="sxs-lookup"><span data-stu-id="10979-124">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="10979-125">切換建置平台</span><span class="sxs-lookup"><span data-stu-id="10979-125">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
3. [<span data-ttu-id="10979-126">匯入 TextMeshPro 基本資源</span><span class="sxs-lookup"><span data-stu-id="10979-126">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="10979-127">匯入混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="10979-127">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [<span data-ttu-id="10979-128">設定 Unity 專案</span><span class="sxs-lookup"><span data-stu-id="10979-128">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
6. <span data-ttu-id="10979-129">[建立和設定場景](mr-learning-base-02.md#creating-and-configuring-the-scene)並為場景提供適當的名稱，例如 AzureCloudServices</span><span class="sxs-lookup"><span data-stu-id="10979-129">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureSpeechServices*</span></span>

<span data-ttu-id="10979-130">然後遵循[變更空間感知顯示選項](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)的指示，將場景的 MRTK 組態設定檔變更為 **DefaultHoloLens2ConfigurationProfile**，並將空間感知網格的顯示選項變更為 [遮蔽]。</span><span class="sxs-lookup"><span data-stu-id="10979-130">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="configuring-the-speech-commands-start-behavior"></a><span data-ttu-id="10979-131">設定語音命令啟動行為</span><span class="sxs-lookup"><span data-stu-id="10979-131">Configuring the speech commands start behavior</span></span>

<span data-ttu-id="10979-132">由於您將使用語音 SDK 進行語音辨識和轉譯，因此您需要設定 MRTK 語音命令，使其不會干擾語音 SDK 功能。</span><span class="sxs-lookup"><span data-stu-id="10979-132">Because you will use the Speech SDK for speech recognition and transcription you need to configure the MRTK Speech Commands so they do not interfere with the Speech SDK functionality.</span></span> <span data-ttu-id="10979-133">若要達到此目的，您可以將語音命令啟動行為從 [自動啟動] 變更為 [手動啟動]。</span><span class="sxs-lookup"><span data-stu-id="10979-133">To achieve this you can change the speech commands start behavior from Auto Start to Manual Start.</span></span>

<span data-ttu-id="10979-134">在 [階層] 視窗中選取 **MixedRealityToolkit** 物件之後，於 [偵測器] 視窗中選取 [輸入] 索引標籤，並複製 **DefaultHoloLens2InputSystemProfile** 和 **DefaultMixedRealitySpeechCommandsProfile**，然後將**啟動行為**的語音命令變更為 [手動啟動]：</span><span class="sxs-lookup"><span data-stu-id="10979-134">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, select the **Input** tab, clone the **DefaultHoloLens2InputSystemProfile** and the **DefaultMixedRealitySpeechCommandsProfile**, and then change the speech commands **Start Behavior** to **Manual Start**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="10979-136">如需有關如何複製及設定 MRTK 設定檔的提示，您可以參閱[設定混合實境工具組設定檔](mr-learning-base-03.md)的指示。</span><span class="sxs-lookup"><span data-stu-id="10979-136">For a reminder on how to clone and configure MRTK profiles, you can refer to the [Configuring the Mixed Reality Toolkit profiles](mr-learning-base-03.md) instructions.</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="10979-137">設定功能</span><span class="sxs-lookup"><span data-stu-id="10979-137">Configuring the capabilities</span></span>

<span data-ttu-id="10979-138">在 Unity 功能表中，選取 [編輯] > [專案設定...] 來開啟 [玩家設定] 視窗，然後找出 [玩家] >  [發佈設定] 區段：</span><span class="sxs-lookup"><span data-stu-id="10979-138">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-1.png)

<span data-ttu-id="10979-140">在 [發佈設定] 中，向下捲動至 [功能] 區段，然後再次確認您在教學課程開頭建立專案時所啟用的 **InternetClient**、**Microphone** 和 **SpatialPerception** 功能是否皆已啟用。</span><span class="sxs-lookup"><span data-stu-id="10979-140">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="10979-141">然後，啟用 **InternetClientServer** 和 **PrivateNetworkClientServer** 功能：</span><span class="sxs-lookup"><span data-stu-id="10979-141">Then, enable the **InternetClientServer** and **PrivateNetworkClientServer** capabilities:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="10979-143">匯入教學課程資產</span><span class="sxs-lookup"><span data-stu-id="10979-143">Importing the tutorial assets</span></span>

<span data-ttu-id="10979-144">下載並**依列出順序**來**匯入**下列 Unity 自訂套件：</span><span class="sxs-lookup"><span data-stu-id="10979-144">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="10979-145">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (最新版本)</span><span class="sxs-lookup"><span data-stu-id="10979-145">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (latest version)</span></span>
* [<span data-ttu-id="10979-146">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="10979-146">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="10979-147">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="10979-147">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-speech-services-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="10979-148">如需有關如何匯入 Unity 自訂套件的提示，您可以參閱[匯入混合實境工具組](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) 的指示。</span><span class="sxs-lookup"><span data-stu-id="10979-148">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="10979-149">匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：</span><span class="sxs-lookup"><span data-stu-id="10979-149">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section4-step1-1.png)

## <a name="preparing-the-scene"></a><span data-ttu-id="10979-151">準備場景</span><span class="sxs-lookup"><span data-stu-id="10979-151">Preparing the scene</span></span>

<span data-ttu-id="10979-152">在本節中，您將藉由新增教學課程 Prefab 來準備場景，並設定 Lunarcom Controller (指令碼) 元件來控制您的場景。</span><span class="sxs-lookup"><span data-stu-id="10979-152">In this section, you will prepare the scene by adding the tutorial prefab and configure the Lunarcom Controller (Script) component to control your scene.</span></span>

<span data-ttu-id="10979-153">在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.AzureSpeechServices] > [Prefabs] 資料夾，並將 **Lunarcom** Prefab 拖曳至 [階層] 視窗來新增至您的場景：</span><span class="sxs-lookup"><span data-stu-id="10979-153">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** folder and drag the **Lunarcom** prefab into the Hierarchy window to add it to your scene:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-1.png)

<span data-ttu-id="10979-155">在 [階層] 視窗中仍選取 **Lunarcom** 物件的情況下，於 [偵測器] 視窗中使用 [新增元件] 按鈕來將 **Lunarcom Controller (指令碼)** 元件新增至 Lunarcom 物件：</span><span class="sxs-lookup"><span data-stu-id="10979-155">With the **Lunarcom** object still selected in the Hierarchy window, in the Inspector window, use the **Add Component** button to add the **Lunarcom Controller (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> <span data-ttu-id="10979-157">The Lunarcom Controller (指令碼) 元件不是 MRTK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="10979-157">The Lunarcom Controller (Script) component is not part of MRTK.</span></span> <span data-ttu-id="10979-158">這是本教學課程資產隨附的元件。</span><span class="sxs-lookup"><span data-stu-id="10979-158">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="10979-159">在仍選取 **Lunarcom** 物件的情況下，將其展開以顯示其子物件，然後將**Terminal** 物件拖曳到 Lunarcom Controller (指令碼) 元件的 [終端機] 欄位中：</span><span class="sxs-lookup"><span data-stu-id="10979-159">With the **Lunarcom** object still selected, expand it to reveal its child objects, then drag the **Terminal** object into the Lunarcom Controller (Script) component's **Terminal** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-3.png)

<span data-ttu-id="10979-161">在仍選取 **Lunarcom** 物件的情況下，展開 [終端機] 物件以顯示其子物件，然後將 **ConnectionLight** 物件拖曳至 Lunarcom Controller (指令碼) 元件的 [連接光源] 欄位，並將 **OutputText** 物件拖曳至 [輸出文字] 欄位中：</span><span class="sxs-lookup"><span data-stu-id="10979-161">With the **Lunarcom** object still selected, expand the Terminal object to reveal its child objects, then drag the **ConnectionLight** object into the Lunarcom Controller (Script) component's **Connection Light** field and the **OutputText** object into the **Output Text** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-4.png)

<span data-ttu-id="10979-163">在仍選取 **Lunarcom** 物件的情況下，展開 Buttons 物件以顯示其子物件，然後在 [偵測器] 視窗中展開 [按鈕] 清單，將其 [大小] 設定為 3，然後將 **MicButton**、**SatelliteButton** 和 **RocketButton** 物件分別拖曳至**元素** 0、1 及 2 的欄位：</span><span class="sxs-lookup"><span data-stu-id="10979-163">With the **Lunarcom** object still selected, expand the Buttons object to reveal its child objects, and then in the Inspector window, expand the **Buttons** list, set its **Size** to 3, and drag the **MicButton**, **SatelliteButton**, and **RocketButton** objects into the **Element** 0, 1, and 2 fields respectively:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a><span data-ttu-id="10979-165">將 Unity 專案連接至 Azure 資源</span><span class="sxs-lookup"><span data-stu-id="10979-165">Connecting the Unity project to the Azure resource</span></span>

<span data-ttu-id="10979-166">若要使用 Azure 語音服務，您必須建立 Azure 資源，並取得語音服務的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="10979-166">To use Azure Speech Services, you need to create an Azure resource and obtain an API key for the Speech Service.</span></span> <span data-ttu-id="10979-167">請遵循[免費試用語音服務](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started)的指示，並記下您的服務區域 (也就是「位置」) 和 API 金鑰 (也就是 Key1 或 Key2)。</span><span class="sxs-lookup"><span data-stu-id="10979-167">Follow the [Try the Speech service for free](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) instructions and make a note of your service region (also known as Location) and API key (also known as Key1 or Key2).</span></span>

<span data-ttu-id="10979-168">在 [階層] 視窗中選取 **Lunarcom** 物件，然後在 [偵測器] 視窗中尋找 **Lunarcom Controller (指令碼)** 元件的 [語音 SDK 認證] 區段並進行設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="10979-168">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Controller (Script)** component's **Speech SDK Credentials** section and configure it as follows:</span></span>

* <span data-ttu-id="10979-169">在 [語音服務 API 金鑰] 欄位中，輸入您的 API 金鑰 (Key1 或 Key2)</span><span class="sxs-lookup"><span data-stu-id="10979-169">In the **Speech Service API Key** field, enter your API key (Key1 or Key2)</span></span>
* <span data-ttu-id="10979-170">在 [語音服務區域] 欄位中，輸入您的服務區域 (位置)，請使用小寫字母並將空格移除</span><span class="sxs-lookup"><span data-stu-id="10979-170">In the **Speech Service Region** field, enter your service region (Location) using lowercase letters and spaces removed</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a><span data-ttu-id="10979-172">使用語音辨識來轉譯語音</span><span class="sxs-lookup"><span data-stu-id="10979-172">Using speech recognition to transcribe speech</span></span>

<span data-ttu-id="10979-173">在 [階層] 視窗中選取 **Lunarcom** 物件，然後在 [偵測器] 視窗中使用 [新增元件] 按鈕來將 **Lunarcom Speech Recognizer (指令碼)** 元件新增至 Lunarcom 物件：</span><span class="sxs-lookup"><span data-stu-id="10979-173">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Speech Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> <span data-ttu-id="10979-175">Lunarcom Speech Recognizer (指令碼) 元件不是 MRTK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="10979-175">The Lunarcom Speech Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="10979-176">這是本教學課程資產隨附的元件。</span><span class="sxs-lookup"><span data-stu-id="10979-176">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="10979-177">如果您現在進入遊戲模式，您可以先按下麥克風按鈕來測試語音辨識：</span><span class="sxs-lookup"><span data-stu-id="10979-177">If you now enter Game mode, you can test the speech recognition by first pressing the microphone button:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-2.png)

<span data-ttu-id="10979-179">接下來，假設您的電腦有麥克風，當您說到某個項目時，您的語音會在終端機面板上進行轉譯：</span><span class="sxs-lookup"><span data-stu-id="10979-179">Then, assuming your computer has a microphone, when you say something, your speech will be transcribed on the terminal panel:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-3.png)


> [!CAUTION]
> <span data-ttu-id="10979-181">應用程式必須連線到 Azure，因此請確定您的電腦/裝置已連線到網際網路。</span><span class="sxs-lookup"><span data-stu-id="10979-181">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="10979-182">恭喜！</span><span class="sxs-lookup"><span data-stu-id="10979-182">Congratulations</span></span>

<span data-ttu-id="10979-183">您已實行由 Azure 提供技術支援的語音辨識。</span><span class="sxs-lookup"><span data-stu-id="10979-183">You have implemented speech recognition powered by Azure.</span></span> <span data-ttu-id="10979-184">在您的裝置上執行應用程式，以確保功能可正常運作。</span><span class="sxs-lookup"><span data-stu-id="10979-184">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="10979-185">在下一個教學課程中，您將了解如何使用 Azure 語音辨識來執行命令。</span><span class="sxs-lookup"><span data-stu-id="10979-185">In the next tutorial, you will learn how to execute commands using Azure speech recognition.</span></span>

[<span data-ttu-id="10979-186">下一個教學課程：2.使用語音辨識來執行命令</span><span class="sxs-lookup"><span data-stu-id="10979-186">Next tutorial: 2. Using speech recognition to execute commands</span></span>](mrlearning-speechSDK-ch2.md)
