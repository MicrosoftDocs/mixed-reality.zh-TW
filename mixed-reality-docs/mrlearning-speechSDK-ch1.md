---
title: Azure 語音服務教學課程-1。 整合和使用語音辨識與轉譯
description: 完成此課程，以瞭解如何在混合現實應用程式中執行 Azure 語音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 25e5aa05839845620a23c3dba6698ac7b5854d6d
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553968"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="dc87d-105">1. 整合和使用語音辨識與轉譯</span><span class="sxs-lookup"><span data-stu-id="dc87d-105">1. Integrating and using speech recognition and transcription</span></span>

## <a name="overview"></a><span data-ttu-id="dc87d-106">概觀</span><span class="sxs-lookup"><span data-stu-id="dc87d-106">Overview</span></span>

<span data-ttu-id="dc87d-107">本教學課程會建立一個混合現實應用程式，以探索 Azure 認知服務 Speech SDK 與 HoloLens 2 的搭配使用。</span><span class="sxs-lookup"><span data-stu-id="dc87d-107">This tutorial creates a Mixed Reality application that explores the use of Azure Cognitive Services Speech SDK with the HoloLens 2.</span></span> <span data-ttu-id="dc87d-108">當您完成本教學課程系列時，您將能夠使用裝置的麥克風即時轉譯語音轉換成文字、將語音翻譯成其他語言，以及利用語音 SDK 的意圖功能來瞭解使用人工智慧的語音命令情報.</span><span class="sxs-lookup"><span data-stu-id="dc87d-108">When you complete this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Speech SDK’s Intent feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="dc87d-109">目標</span><span class="sxs-lookup"><span data-stu-id="dc87d-109">Objectives</span></span>

* <span data-ttu-id="dc87d-110">瞭解如何將 Azure 語音 SDK 整合至 HoloLens 2 應用程式</span><span class="sxs-lookup"><span data-stu-id="dc87d-110">Learn how to integrate the Azure Speech SDK into a HoloLens 2 application</span></span>
* <span data-ttu-id="dc87d-111">瞭解如何使用語音命令</span><span class="sxs-lookup"><span data-stu-id="dc87d-111">Learn how to use voice commands</span></span>
* <span data-ttu-id="dc87d-112">瞭解如何使用語音轉換文字功能</span><span class="sxs-lookup"><span data-stu-id="dc87d-112">Learn how to use speech-to-text capabilities</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dc87d-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="dc87d-113">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="dc87d-114">如果您尚未完成[快速入門教學](mrlearning-base.md)課程系列，建議您先完成這些教學課程。</span><span class="sxs-lookup"><span data-stu-id="dc87d-114">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="dc87d-115">已[安裝正確工具](install-the-tools.md)的 Windows 10 電腦</span><span class="sxs-lookup"><span data-stu-id="dc87d-115">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="dc87d-116">Windows 10 SDK 10.0.18362.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="dc87d-116">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="dc87d-117">基本的 C# 程式設計能力</span><span class="sxs-lookup"><span data-stu-id="dc87d-117">Some basic C# programming ability</span></span>
* <span data-ttu-id="dc87d-118">已[針對開發而設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置</span><span class="sxs-lookup"><span data-stu-id="dc87d-118">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>

>[!IMPORTANT]
> <span data-ttu-id="dc87d-119">本教學課程系列的建議 Unity 版本是 Unity 2019.2. X。</span><span class="sxs-lookup"><span data-stu-id="dc87d-119">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="dc87d-120">這個版本能取代上述連結之必要條件中所述的任何 Unity 版本需求或建議。</span><span class="sxs-lookup"><span data-stu-id="dc87d-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="getting-started"></a><span data-ttu-id="dc87d-121">使用者入門</span><span class="sxs-lookup"><span data-stu-id="dc87d-121">Getting Started</span></span>

1. <span data-ttu-id="dc87d-122">啟動 Unity，並建立新的專案。</span><span class="sxs-lookup"><span data-stu-id="dc87d-122">Start Unity, and create a new project.</span></span> <span data-ttu-id="dc87d-123">輸入專案名稱 [語音 SDK 學習模組]。</span><span class="sxs-lookup"><span data-stu-id="dc87d-123">Enter the project name Speech SDK Learning Module.</span></span> <span data-ttu-id="dc87d-124">選擇要儲存專案的位置。</span><span class="sxs-lookup"><span data-stu-id="dc87d-124">Choose a location for where to save your project.</span></span> <span data-ttu-id="dc87d-125">按一下 [建立專案]。</span><span class="sxs-lookup"><span data-stu-id="dc87d-125">Click Create Project.</span></span>

    ![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

    >[!NOTE]
    ><span data-ttu-id="dc87d-127">請確定範本已設定為3D，如上圖所示。</span><span class="sxs-lookup"><span data-stu-id="dc87d-127">Ensure that the template is set to 3D, as shown in the image above.</span></span>

2. <span data-ttu-id="dc87d-128">下載[Mixed Reality 工具](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)組 Unity [foundation 封裝版本 2.3.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage) ，並將它儲存到您電腦上的資料夾。</span><span class="sxs-lookup"><span data-stu-id="dc87d-128">Download the [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity [foundation package version 2.3.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage) and save it to a folder on your PC.</span></span> <span data-ttu-id="dc87d-129">將套件匯入至您的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="dc87d-129">Import the package into your Unity project.</span></span> <span data-ttu-id="dc87d-130">如需如何執行此動作的詳細指示，請參閱[快速入門教學課程-第2課。初始化您的專案和第一個應用程式](mrlearning-base-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="dc87d-130">For detailed instructions on how to do this, see the [Getting started tutorials - Lesson 2. Initializing your project and first application](mrlearning-base-ch1.md).</span></span>

3. <span data-ttu-id="dc87d-131">下載並匯入 Unity 資產套件的 Azure[語音 SDK](https://aka.ms/csspeech/unitypackage) 。</span><span class="sxs-lookup"><span data-stu-id="dc87d-131">Download and import the Azure [Speech SDK](https://aka.ms/csspeech/unitypackage) for the Unity asset package.</span></span> <span data-ttu-id="dc87d-132">按一下 [資產]，選取 [匯入套件]，然後選取 [自訂套件]，以匯入語音 SDK 套件。</span><span class="sxs-lookup"><span data-stu-id="dc87d-132">Import the Speech SDK package by clicking on Assets, selecting Import package, then selecting Custom Package.</span></span> <span data-ttu-id="dc87d-133">尋找稍早下載的語音 SDK 套件，然後開啟以開始匯入程式。</span><span class="sxs-lookup"><span data-stu-id="dc87d-133">Find the Speech SDK package downloaded earlier, and open it to begin the importing process.</span></span>

    ![mrlearning-speech-ch1-1-step3a .png](images/mrlearning-speech-ch1-1-step3a.png)

    ![mrlearning-speech-ch1-1-step3b .png](images/mrlearning-speech-ch1-1-step3b.png)

4. <span data-ttu-id="dc87d-136">在下一個快顯視窗中，按一下 [匯入] 開始匯入語音 SDK 套件。</span><span class="sxs-lookup"><span data-stu-id="dc87d-136">In the next pop-up window, click Import to begin importing the Speech SDK package.</span></span> <span data-ttu-id="dc87d-137">請確定已核取所有專案，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="dc87d-137">Ensure all items are checked, as shown in the image below.</span></span>

    ![mrlearning-speech-ch1-1-step4 .png](images/mrlearning-speech-ch1-1-step4.png)

5. <span data-ttu-id="dc87d-139">下載教學課程資產：</span><span class="sxs-lookup"><span data-stu-id="dc87d-139">Download the tutorial assets:</span></span>
    * [<span data-ttu-id="dc87d-140">MRTK.HoloLens2 GettingStarted. 2.3.0.2. unitypackage</span><span class="sxs-lookup"><span data-stu-id="dc87d-140">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
    * <span data-ttu-id="dc87d-141">[SpeechSDKAssets. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/Speech_2/SpeechSDKAssets.unitypackage) （版本1.2）</span><span class="sxs-lookup"><span data-stu-id="dc87d-141">[SpeechSDKAssets.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/Speech_2/SpeechSDKAssets.unitypackage) (version 1.2)</span></span>

    <span data-ttu-id="dc87d-142">SpeechSDKAssets 資產套件是針對此教學課程系列所開發的資產和腳本集合，以展示 Azure 語音 SDK 的實際使用。</span><span class="sxs-lookup"><span data-stu-id="dc87d-142">The SpeechSDKAssets asset package is a collection of assets and scripts developed for this tutorial series to showcase practical use of Azure's Speech SDK.</span></span> <span data-ttu-id="dc87d-143">這是語音命令終端機，最終會與[快速入門教學課程-第7課所開發的 Rocket 啟動器元件體驗互動。建立農曆模組範例應用程式](mrlearning-base-ch6.md)。</span><span class="sxs-lookup"><span data-stu-id="dc87d-143">It is a voice-command terminal that will ultimately interface with the Rocket Launcher assembly experience developed in the [Getting started tutorials - Lesson 7. Creating a Lunar Module sample application](mrlearning-base-ch6.md).</span></span>

6. <span data-ttu-id="dc87d-144">遵循匯入混合現實工具組和語音 SDK 所需的類似步驟，將兩個教學課程資產封裝匯入 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="dc87d-144">Import the two tutorial asset packages into your Unity project by following similar steps you took to import the Mixed Reality Toolkit and Speech SDK.</span></span>

7. <span data-ttu-id="dc87d-145">設定混合現實工具組（MRTK）。</span><span class="sxs-lookup"><span data-stu-id="dc87d-145">Configure the Mixed Reality Toolkit (MRTK).</span></span>

    <span data-ttu-id="dc87d-146">若要這麼做，請按一下視窗頂端的 [混合現實工具組] 面板，然後選取 [新增至場景並設定]。</span><span class="sxs-lookup"><span data-stu-id="dc87d-146">To do this, click on the Mixed Reality Toolkit panel in the top of your window, and then select Add to Scene and Configure.</span></span>

    ![mrlearning-speech-ch1-1-step7a .png](images/mrlearning-speech-ch1-1-step7a.png)

    <span data-ttu-id="dc87d-148">在場景階層中選取 MixedRealityToolkit 物件之後，在 [偵測器] 視窗中選取 [DefaultHoloLens2ConfigurationProfile]，使其成為混合現實工具組的作用中設定檔。</span><span class="sxs-lookup"><span data-stu-id="dc87d-148">With the MixedRealityToolkit object selected in your scene hierarchy, in the Inspector window, select DefaultHoloLens2ConfigurationProfile to make it the Active Profile for the Mixed Reality Toolkit.</span></span>

    ![mrlearning-speech-ch1-1-step7b .png](images/mrlearning-speech-ch1-1-step7b.png)

8. <span data-ttu-id="dc87d-150">您的場景現在在 MRTK 中有數個新專案。</span><span class="sxs-lookup"><span data-stu-id="dc87d-150">Your scene now has several new items in it from the MRTK.</span></span> <span data-ttu-id="dc87d-151">依序按一下 [檔案] 和 [另存新檔]，並命名您的場景 SpeechScene，以不同的名稱儲存場景。</span><span class="sxs-lookup"><span data-stu-id="dc87d-151">Save your scene under a different name by clicking on "file," then "save as" and name your scene SpeechScene.</span></span>

    >[!NOTE]
    ><span data-ttu-id="dc87d-152">如果您在將 MRTK 新增至專案後按下場景上的 [播放]，而它不進入 [播放] 模式，您可能需要重新開機 Unity。</span><span class="sxs-lookup"><span data-stu-id="dc87d-152">If you press Play on your scene after you add the MRTK to your project, and it doesn't enter play mode, you might need to restart Unity.</span></span>

9. <span data-ttu-id="dc87d-153">在場景階層中選取 MixedRealityToolkit 物件後，按一下 [複製] & [檢查] 面板中的 [自訂]，開啟複製設定檔快顯視窗。</span><span class="sxs-lookup"><span data-stu-id="dc87d-153">With the MixedRealityToolkit object selected in your scene hierarchy, click Copy & Customize in the Inspector panel to open the Clone Profile popup.</span></span> <span data-ttu-id="dc87d-154">在 [複製設定檔] 快顯視窗中，為您的自訂設定檔輸入適當的名稱，例如 [自訂 HoloLens2ConfigurationProfile]。</span><span class="sxs-lookup"><span data-stu-id="dc87d-154">In the Clone Profile popup, enter a suitable name for your custom profile, for example, Custom HoloLens2ConfigurationProfile.</span></span> <span data-ttu-id="dc87d-155">按一下 [複製] 來建立您的自訂設定檔，並將它設定為使用中的設定檔。</span><span class="sxs-lookup"><span data-stu-id="dc87d-155">Click Clone to create your custom configuration profile and set it as the active profile.</span></span>

    ![mrlearning-speech-ch1-1-step9 .png](images/mrlearning-speech-ch1-1-step9.png)

10. <span data-ttu-id="dc87d-157">此外，在 [偵測器] 面板中（已選取階層中的 [MixedRealityToolkit] 物件），取消核取 [啟用診斷系統] 右邊的方塊來停用診斷系統。</span><span class="sxs-lookup"><span data-stu-id="dc87d-157">Also in the Inspector panel (with the MixedRealityToolkit object selected in your hierarchy), disable the diagnostics system by unchecking the box to the right of Enable Diagnostics System.</span></span>

    ![mrlearning-speech-ch1-1-step10 .png](images/mrlearning-speech-ch1-1-step10.png)

11. <span data-ttu-id="dc87d-159">在本教學課程中，我們會使用語音辨識和轉譯的輸入語音命令。</span><span class="sxs-lookup"><span data-stu-id="dc87d-159">In this tutorial, we are using the input speech commands for speech recognition and transcription.</span></span> <span data-ttu-id="dc87d-160">讓我們複製輸入設定檔，以變更語音設定。</span><span class="sxs-lookup"><span data-stu-id="dc87d-160">Let's clone the input profile to make changes to speech settings.</span></span>

    <span data-ttu-id="dc87d-161">當您的場景階層中仍然選取 MixedRealityToolkit 物件時，請按一下 [檢查] 面板中的 [小型複製] 按鈕，以開啟 [複製設定檔] 快顯視窗。</span><span class="sxs-lookup"><span data-stu-id="dc87d-161">With the MixedRealityToolkit object still selected in your scene hierarchy, click the small Clone button in the Inspector panel to open the Clone Profile popup.</span></span> <span data-ttu-id="dc87d-162">在 [複製設定檔] 快顯視窗中，為您的自訂設定檔輸入適當的名稱，例如 [自訂 HoloLens2InputSystemProfile]，然後按一下 [複製] 來建立自訂輸入系統設定檔，並將它設定為使用中設定檔。</span><span class="sxs-lookup"><span data-stu-id="dc87d-162">In the Clone Profile popup, enter a suitable name for your custom profile, for example, Custom HoloLens2InputSystemProfile, and then click Clone to create your custom input system profile and set it as the active profile.</span></span>

    ![mrlearning-speech-ch1-1-step11 .png](images/mrlearning-speech-ch1-1-step11.png)

12. <span data-ttu-id="dc87d-164">複製輸入設定檔之後，展開 [語音] 區段，然後遵循上一個步驟中的相同程式來複製語音命令設定檔。</span><span class="sxs-lookup"><span data-stu-id="dc87d-164">Once the input profile is cloned, expand the Speech section and follow the same process as in the previous step to clone the speech commands profile.</span></span>

    ![mrlearning-speech-ch1-1-step12 .png](images/mrlearning-speech-ch1-1-step12.png)

13. <span data-ttu-id="dc87d-166">在 [語音] 區段下，移至 [一般設定]，並將 [啟動行為] 變更為手動啟動。</span><span class="sxs-lookup"><span data-stu-id="dc87d-166">Under the Speech section, go to General Settings and change Start Behavior to Manual Start.</span></span>

    ![mrlearning-speech-ch1-1-step13 .png](images/mrlearning-speech-ch1-1-step13.png)

14. <span data-ttu-id="dc87d-168">在 專案 面板中，展開 Lunarcom 資料夾，然後將 Lunarcom_Base prefab 拖曳到您的場景階層中。</span><span class="sxs-lookup"><span data-stu-id="dc87d-168">In the Project panel, expand the Lunarcom folder and drag the Lunarcom_Base prefab into your scene hierarchy.</span></span>

    ![mrlearning-speech-ch1-1-step14 .png](images/mrlearning-speech-ch1-1-step14.png)

15. <span data-ttu-id="dc87d-170">選取階層中的 [Lunarcom_Base] 物件，並確定 [位置] 設定為 x = 0、y = 0、z = 0，而且旋轉設定為 x = 0、y = 0 和 z = 0。</span><span class="sxs-lookup"><span data-stu-id="dc87d-170">Select the Lunarcom_Base object in your hierarchy, and ensure that the position is set to x=0, y=0, and z=0, as well as the rotation set to x=0, y=0, and z=0.</span></span> <span data-ttu-id="dc87d-171">將縮放比例設定為 read x = 0.008、y = 0.008 和 z = 0.01。</span><span class="sxs-lookup"><span data-stu-id="dc87d-171">Set the scale to read x=0.008, y=0.008, and z=0.01.</span></span>

    ![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

16. <span data-ttu-id="dc87d-173">按一下 [新增元件]，然後搜尋並選取 [Lunarcom 控制器]。</span><span class="sxs-lookup"><span data-stu-id="dc87d-173">Click Add Component, and search for and select Lunarcom Controller.</span></span> <span data-ttu-id="dc87d-174">此腳本包含在您于步驟6匯入的 Lunarcom 資產套件中。</span><span class="sxs-lookup"><span data-stu-id="dc87d-174">This script is included in the Lunarcom asset pack that you imported in Step 6.</span></span>

    ![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

17. <span data-ttu-id="dc87d-176">若要將我們的應用程式連線到 Azure 認知服務，您必須為語音服務輸入訂用帳戶金鑰（也稱為 API 金鑰）。</span><span class="sxs-lookup"><span data-stu-id="dc87d-176">To connect our application to Azure Cognitive Services, you must enter a subscription key (also known as an API Key), for the Speech Service.</span></span> <span data-ttu-id="dc87d-177">請遵循[這裡](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started)的指示來取得免費的訂用帳戶金鑰。</span><span class="sxs-lookup"><span data-stu-id="dc87d-177">Follow the instructions at [here](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) to obtain a free subscription key.</span></span> <span data-ttu-id="dc87d-178">一旦您取得訂用帳戶金鑰，請在 [偵測器] 面板的 [LunarcomController] 元件的 [語音服務 API 金鑰] 欄位中輸入它，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="dc87d-178">Once you obtain the subscription key, enter it into the Speech Service API Key field of the LunarcomController component in the Inspector panel, as shown in the image below.</span></span>

18. <span data-ttu-id="dc87d-179">輸入當您在 [偵測器] 面板中，于 LunarcomController 元件的 [語音服務區域] 欄位中註冊訂用帳戶金鑰時，所選擇的區域。</span><span class="sxs-lookup"><span data-stu-id="dc87d-179">Enter the Region that you chose when you signed up for the subscription key into the Speech Service Region field of the LunarcomController component in the Inspector panel.</span></span> <span data-ttu-id="dc87d-180">例如，針對區域美國西部，請輸入 "westus"。</span><span class="sxs-lookup"><span data-stu-id="dc87d-180">For example, for the region West US type in "westus".</span></span>

    ![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

19. <span data-ttu-id="dc87d-182">在您的階層中，按一下其左邊的箭號來展開 [Lunarcom_Base] 物件。</span><span class="sxs-lookup"><span data-stu-id="dc87d-182">In your hierarchy, expand the Lunarcom_Base object by clicking the arrow to the left of it.</span></span> <span data-ttu-id="dc87d-183">然後對其子物件「Terminal」執行相同的動作，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="dc87d-183">Then do the same for its child object, "Terminal, as shown in the image below.</span></span>

20. <span data-ttu-id="dc87d-184">選取 [Lunarcom_Base] 時，請在 [偵測器] 面板中按一下 [Lunarcom 文字]，並將其從階層拖曳至 [LunarcomController] 元件中的輸出文字位置，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="dc87d-184">While Lunarcom_Base is selected, click and drag Lunarcom Text from the hierarchy to the Output Text slot in the LunarcomController component in the Inspector panel, as shown in the image below.</span></span>

21. <span data-ttu-id="dc87d-185">對終端機物件執行相同的動作，並將連接光源控制到連接光源控制器插槽。</span><span class="sxs-lookup"><span data-stu-id="dc87d-185">Do the same thing with the Terminal object into the Terminal slot and the Connection Light object to the Connection Light Controller slot.</span></span>

    ![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

22. <span data-ttu-id="dc87d-187">在 [偵測器] 面板中，按一下 LunarcomController 腳本的 [Lunarcom 按鈕] 區段旁邊的箭號，然後將 [大小] 變更為3。</span><span class="sxs-lookup"><span data-stu-id="dc87d-187">Click the arrow next to the Lunarcom Buttons section of the LunarcomController script in the Inspector panel, and change the size to 3.</span></span> <span data-ttu-id="dc87d-188">按 Enter 或 Return。</span><span class="sxs-lookup"><span data-stu-id="dc87d-188">Press Enter or Return.</span></span> <span data-ttu-id="dc87d-189">這會導致三個新的元素欄位出現。</span><span class="sxs-lookup"><span data-stu-id="dc87d-189">This causes three new Element fields to appear.</span></span>

    ![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

23. <span data-ttu-id="dc87d-191">按一下階層中其旁邊的箭號以展開 [Lunarcom] 按鈕，並使用上述相同的程式，分別將 Mic、衛星和 Rocket gameobject 拖曳至專案0、1和2的參考，其位於 [LunarcomController] 元件的偵測器面板。</span><span class="sxs-lookup"><span data-stu-id="dc87d-191">Expand the Lunarcom Buttons by clicking the arrow next to it in your hierarchy, and using the same process as above, drag the Mic, Satellite, and Rocket gameobjects to the Element 0, 1, and 2 references, respectively, in the LunarcomController component in the Inspector panel.</span></span>

    ![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

24. <span data-ttu-id="dc87d-193">選取階層中的 [Lunarcom_Base] 物件。</span><span class="sxs-lookup"><span data-stu-id="dc87d-193">Select the Lunarcom_Base" object in your hierarchy.</span></span> <span data-ttu-id="dc87d-194">按一下 [偵測器] 面板中的 [新增元件]，然後搜尋並選取 [Lunarcom 語音辨識器]。</span><span class="sxs-lookup"><span data-stu-id="dc87d-194">Click Add Component in the inspector panel and search for and select Lunarcom Speech Recognizer.</span></span> <span data-ttu-id="dc87d-195">重複相同的步驟，以新增 Lunarcom 喚醒字辨識器。</span><span class="sxs-lookup"><span data-stu-id="dc87d-195">Repeat the same steps to add Lunarcom Wake Word Recognizer.</span></span>

    ![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

25. <span data-ttu-id="dc87d-197">在 [喚醒文字位置] 中，輸入「啟用終端機」。</span><span class="sxs-lookup"><span data-stu-id="dc87d-197">In the Wake Word slot, type in Activate Terminal.</span></span> <span data-ttu-id="dc87d-198">在 [解除斷字位置] 中，輸入「關閉終端機」。</span><span class="sxs-lookup"><span data-stu-id="dc87d-198">In the Dismiss Word slot, type Dismiss Terminal.</span></span>

    ![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

## <a name="build-your-application-to-your-device"></a><span data-ttu-id="dc87d-200">對您的裝置建置應用程式</span><span class="sxs-lookup"><span data-stu-id="dc87d-200">Build your application to your device</span></span>

1. <span data-ttu-id="dc87d-201">前往 [檔案] > [組建設定]，再次開啟 [組建設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="dc87d-201">Open the build settings window again by going to File>Build Settings.</span></span>

    ![images/mrlearning-語音-ch1-2-步驟1](images/mrlearning-speach-ch1-2-step1.jpg)

2. <span data-ttu-id="dc87d-203">藉由按一下 [加入開啟場景] 按鈕，來確定您想要嘗試的場景有在 [建置中的場景] 清單中。</span><span class="sxs-lookup"><span data-stu-id="dc87d-203">Ensure the scene you want to try is in the “Scenes in Build” list by clicking on the “Add Open Scenes” button.</span></span>

3. <span data-ttu-id="dc87d-204">按 [Player 設定] 按鈕，然後移至 [發佈設定]。</span><span class="sxs-lookup"><span data-stu-id="dc87d-204">Press the Player Settings button and go to Publishing Settings.</span></span> <span data-ttu-id="dc87d-205">在 [功能] 底下，啟用：網際網路、網際網路用戶端伺服器、私人網路用戶端伺服器、麥克風和空間感知。</span><span class="sxs-lookup"><span data-stu-id="dc87d-205">Under Capabilities, enable: Internet, Internet Client Server, Private Network Client Server, Microphone and Spatial Perception.</span></span>

4. <span data-ttu-id="dc87d-206">在相同的播放人員設定中，移至 [XR 設定]，然後選取支援的虛擬實境。</span><span class="sxs-lookup"><span data-stu-id="dc87d-206">In the same Player Settings, go to XR settings  and select the Virtual Reality Supported to ON.</span></span>

5. <span data-ttu-id="dc87d-207">按下 [建置] 按鈕，開始建置程序。</span><span class="sxs-lookup"><span data-stu-id="dc87d-207">Press the Build button to begin the build process.</span></span>

    ![mrlearning-speech-ch1-2-步驟5](images/mrlearning-speach-ch1-2-step5.jpg)

6. <span data-ttu-id="dc87d-209">為您的應用程式建立並命名新資料夾。</span><span class="sxs-lookup"><span data-stu-id="dc87d-209">Create and name a new folder for your application.</span></span> <span data-ttu-id="dc87d-210">在下圖中，已建立名為 “App” 的資料夾來包含應用程式。</span><span class="sxs-lookup"><span data-stu-id="dc87d-210">In the image below, a folder with the name “App” was created to contain the application.</span></span> <span data-ttu-id="dc87d-211">按一下 [選取資料夾]，即可開始對新建立的資料夾進行建置。</span><span class="sxs-lookup"><span data-stu-id="dc87d-211">Click “Select Folder” to begin building to the newly created folder.</span></span> <span data-ttu-id="dc87d-212">建置完成之後，您可以關閉 Unity 中的 [建置設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="dc87d-212">After the build has completed, you may close the "Build Settings" window in Unity.</span></span>

    ![mrlearning-speech-ch1-2-步驟6](images/mrlearning-speach-ch1-2-step6.jpg)

    >[!NOTE]
    ><span data-ttu-id="dc87d-214">如果建置失敗，請再試一次，或重新啟動 Unity，然後重新建置。</span><span class="sxs-lookup"><span data-stu-id="dc87d-214">If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="dc87d-215">如果您看到錯誤，例如「錯誤： CS0246 = 類型或命名空間名稱 "XX" 找不到（您是否遺漏 using 指示詞或元件參考？）」，您可能需要安裝[Windows 10 SDK （10.0.18362.0）](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>)</span><span class="sxs-lookup"><span data-stu-id="dc87d-215">If you see an error such as "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?)", you may need to install [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>)</span></span>

7. <span data-ttu-id="dc87d-216">在建置完成之後，開啟新建立的資料夾，其中包含您新建置的應用程式檔案。</span><span class="sxs-lookup"><span data-stu-id="dc87d-216">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="dc87d-217">按兩下 ".sln" 方案檔，以在 Visual Studio 中開啟方案檔。</span><span class="sxs-lookup"><span data-stu-id="dc87d-217">Double-click on the “.sln” solution file to open the solution file in Visual Studio.</span></span>

    >[!NOTE]
    ><span data-ttu-id="dc87d-218">請務必開啟新建立的資料夾（也就是「應用程式」資料夾，如果遵循先前步驟中的命名慣例），因為該資料夾外部會有類似的名稱 .sln 檔案，與組建資料夾內的 .sln 檔案不同。</span><span class="sxs-lookup"><span data-stu-id="dc87d-218">Be sure to open the newly created folder (i.e., the "App" folder, if following the naming conventions from the previous steps), as there will be a similarly named .sln file outside of that folder that is different from the .sln file inside the build folder.</span></span> 

    ![mrlearning-speech-ch1-2-step7](images/mrlearning-speach-ch1-2-step7.jpg)

    >[!NOTE]
    ><span data-ttu-id="dc87d-220">如果 Visual Studio 要求您安裝新元件，請確定已依照[[安裝工具] 頁面中的](install-the-tools.md)指定安裝所有必要元件</span><span class="sxs-lookup"><span data-stu-id="dc87d-220">If Visual Studio asks you to install new components, ensure that all prerequisite components are installed as specified in [the "Install the Tools" page](install-the-tools.md)</span></span>

8. <span data-ttu-id="dc87d-221">使用 USB 纜線，將 HoloLens 2 插入您的電腦。</span><span class="sxs-lookup"><span data-stu-id="dc87d-221">Plug your HoloLens 2 into your PC with the USB cable.</span></span> <span data-ttu-id="dc87d-222">雖然這些課程指示假設您會以 HoloLens 2 裝置部署測試，但您也可以選擇部署到 [HoloLens 2 模擬器](using-the-hololens-emulator.md)或選擇建立[用於側載的應用程式套件](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span><span class="sxs-lookup"><span data-stu-id="dc87d-222">While these lesson instructions assume you will be deploying a testing with a HoloLens 2 device, you may also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span></span>

9. <span data-ttu-id="dc87d-223">對您的裝置進行建置之前，請確定裝置處於開發人員模式。</span><span class="sxs-lookup"><span data-stu-id="dc87d-223">Before building to your device, ensure that the device is in Developer Mode.</span></span> <span data-ttu-id="dc87d-224">如果這是您第一次部署到 HoloLens 2，Visual Studio 可能會要求您使用 pin 碼來與 HoloLens 2 配對。</span><span class="sxs-lookup"><span data-stu-id="dc87d-224">If this is your first time deploying to the HoloLens 2, Visual Studio may ask you to pair your HoloLens 2 with a pin.</span></span> <span data-ttu-id="dc87d-225">若要啟用開發人員模式，或與 Visual Studio 配對，請遵循[這些指示](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="dc87d-225">Please follow [these instructions](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio) if you need to enable developer mode or pair with Visual Studio.</span></span>

10. <span data-ttu-id="dc87d-226">若要設定 Visual Studio 來對 HoloLens 2 進行建置，請選取 [發行] 組態和 [ARM] 架構。</span><span class="sxs-lookup"><span data-stu-id="dc87d-226">Configure Visual Studio for building to your HoloLens 2 by selecting the “Release” configuration and the “ARM” architecture.</span></span>

    ![mrlearning-speech-ch1-2-step10](images/mrlearning-speach-ch1-2-step10.jpg)

11. <span data-ttu-id="dc87d-228">最後一個步驟是選取 [偵錯] > [啟動但不偵錯] 來對您的裝置進行建置。</span><span class="sxs-lookup"><span data-stu-id="dc87d-228">The final step is to build to your device by selecting Debug>Start without Debugging.</span></span> <span data-ttu-id="dc87d-229">選取 [啟動但不偵錯] 會讓裝置上的應用程式在建置成功時立即啟動，但 Visual Studio 中不會出現偵錯資訊。</span><span class="sxs-lookup"><span data-stu-id="dc87d-229">Selecting “Start without Debugging” will cause the application to immediately start on your device upon a successful build, but without Debugging information appearing in Visual Studio.</span></span> <span data-ttu-id="dc87d-230">這也表示，當您的應用程式在 HoloLens 2 上執行時，您可以在不需要停止應用程式的情況下拔掉 USB 纜線。</span><span class="sxs-lookup"><span data-stu-id="dc87d-230">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span> <span data-ttu-id="dc87d-231">您也可以選取 [建置] > [部署解決方案]，在不自動啟動應用程式的情況下，對您的裝置進行部署。</span><span class="sxs-lookup"><span data-stu-id="dc87d-231">You may also select Build>Deploy Solution to deploy to your device without having the application automatically start.</span></span>

    ![mrlearning-speech-ch1-2-step11.JPG](images/mrlearning-speach-ch1-2-step11.jpg)

## <a name="congratulations"></a><span data-ttu-id="dc87d-233">恭喜</span><span class="sxs-lookup"><span data-stu-id="dc87d-233">Congratulations</span></span>

<span data-ttu-id="dc87d-234">您已在應用程式中設定語音辨識（由 Azure 提供技術支援）。</span><span class="sxs-lookup"><span data-stu-id="dc87d-234">You've set up voice recognition in your application, powered by Azure.</span></span> <span data-ttu-id="dc87d-235">執行應用程式，以確保所有功能和功能都能正常運作。</span><span class="sxs-lookup"><span data-stu-id="dc87d-235">Run the application to ensure all functions and features are working properly.</span></span> <span data-ttu-id="dc87d-236">從說出您在步驟25輸入的喚醒字，啟用終端機。</span><span class="sxs-lookup"><span data-stu-id="dc87d-236">Start with saying the wake word you typed in Step 25, Activate Terminal.</span></span> <span data-ttu-id="dc87d-237">選取 [麥克風] 按鈕以開始語音辨識。</span><span class="sxs-lookup"><span data-stu-id="dc87d-237">Select the Microphone button to start voice recognition.</span></span> <span data-ttu-id="dc87d-238">開始說話。</span><span class="sxs-lookup"><span data-stu-id="dc87d-238">Begin speaking.</span></span> <span data-ttu-id="dc87d-239">您會在說話時看到您在終端機中轉譯的單字。</span><span class="sxs-lookup"><span data-stu-id="dc87d-239">You will see your words transcribed in the terminal as you speak.</span></span> <span data-ttu-id="dc87d-240">第二次按下 [麥克風] 按鈕，以停止語音辨識。</span><span class="sxs-lookup"><span data-stu-id="dc87d-240">Press the Microphone button a second time to stop voice recognition.</span></span> <span data-ttu-id="dc87d-241">假設 [關閉終端機] 以隱藏 Lunarcom 終端機。</span><span class="sxs-lookup"><span data-stu-id="dc87d-241">Say Dismiss Terminal to hide the Lunarcom terminal.</span></span> <span data-ttu-id="dc87d-242">在下一課中，您將瞭解如何在因為 HoloLens 2 離線而無法使用 Azure 語音 SDK 的情況下，以動態方式切換至使用裝置供電的語音辨識。</span><span class="sxs-lookup"><span data-stu-id="dc87d-242">In the next lesson, you'll learn how to dynamically switch to using device-powered voice recognition for situations where Azure's speech SDK isn't available due to the HoloLens 2 being offline.</span></span>

[<span data-ttu-id="dc87d-243">下一個教學課程： 2. 新增本機語音轉換文字翻譯的離線模式</span><span class="sxs-lookup"><span data-stu-id="dc87d-243">Next tutorial: 2. Adding an offline mode for local speech-to-text translation</span></span>](mrlearning-speechSDK-ch2.md)
