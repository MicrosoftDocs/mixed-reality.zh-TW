# <a name="speech-sdk-learning-module"></a><span data-ttu-id="cac98-101">語音 SDK 學習模組</span><span class="sxs-lookup"><span data-stu-id="cac98-101">Speech SDK Learning Module</span></span>

<span data-ttu-id="cac98-102">在本教學課程中，您將建立的混合實境應用程式，探索如何使用 Azure 認知服務語音 SDK 與 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="cac98-102">In this tutorial you will create a Mixed Reality application that explores the use of Azure Cognitive Services Speech SDK with the HoloLens 2.</span></span> <span data-ttu-id="cac98-103">完成本教學課程系列，您將能夠使用您的裝置的麥克風 ip-pbx 語音轉換文字即時、 將您的語音翻譯成其他語言中，並利用語音 SDK 的意圖功能，以了解使用語音命令人工智慧。</span><span class="sxs-lookup"><span data-stu-id="cac98-103">When finished with this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Speech SDK’s Intent feature to understand voice commands using artificial intelligence.</span></span>

<span data-ttu-id="cac98-104">目標：</span><span class="sxs-lookup"><span data-stu-id="cac98-104">Objectives:</span></span>

- <span data-ttu-id="cac98-105">了解如何將 Azure 語音 SDK 整合到 HoloLens 2 應用程式</span><span class="sxs-lookup"><span data-stu-id="cac98-105">Learn how to integrate the Azure Speech SDK into a HoloLens 2 application</span></span>
- <span data-ttu-id="cac98-106">了解如何使用語音命令</span><span class="sxs-lookup"><span data-stu-id="cac98-106">Learn how to use voice commands</span></span>
- <span data-ttu-id="cac98-107">了解如何使用語音轉換文字功能</span><span class="sxs-lookup"><span data-stu-id="cac98-107">Learn how to use speech-to-text capabilities</span></span>

## <a name="instructions"></a><span data-ttu-id="cac98-108">指示</span><span class="sxs-lookup"><span data-stu-id="cac98-108">Instructions</span></span>

### <a name="getting-started"></a><span data-ttu-id="cac98-109">開始使用</span><span class="sxs-lookup"><span data-stu-id="cac98-109">Getting Started</span></span>

1. <span data-ttu-id="cac98-110">啟動 Unity 並建立新的專案。</span><span class="sxs-lookup"><span data-stu-id="cac98-110">Start Unity and create a new project.</span></span> <span data-ttu-id="cac98-111">輸入專案名稱 「 語音 SDK 學習模組 」。</span><span class="sxs-lookup"><span data-stu-id="cac98-111">Enter the project name “Speech SDK Learning Module.”</span></span> <span data-ttu-id="cac98-112">選擇要儲存專案的位置。</span><span class="sxs-lookup"><span data-stu-id="cac98-112">Choose a location for where to save your project.</span></span> <span data-ttu-id="cac98-113">然後按一下 [建立專案]。</span><span class="sxs-lookup"><span data-stu-id="cac98-113">Then click "Create Project."</span></span>

![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

> <span data-ttu-id="cac98-115">注意:請確定範本設為 「 3D 」，如上圖所示。</span><span class="sxs-lookup"><span data-stu-id="cac98-115">Note: Ensure that the template is set to "3D," as shown in the image above.</span></span>

2. <span data-ttu-id="cac98-116">下載[混合實境 Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) Unity 套件，並將它儲存在您的電腦上的資料夾。</span><span class="sxs-lookup"><span data-stu-id="cac98-116">Download the [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) Unity package and save it to a folder on your PC.</span></span> <span data-ttu-id="cac98-117">匯入 Unity 專案的封裝。</span><span class="sxs-lookup"><span data-stu-id="cac98-117">Import the package into your Unity project.</span></span> <span data-ttu-id="cac98-118">如需如何執行這項操作的詳細指示，請參閱[第 1 課的基本模組](mrlearning-base-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="cac98-118">For detailed instructions on how to do this, please see [base module lesson 1](mrlearning-base-ch1.md).</span></span> 

3. <span data-ttu-id="cac98-119">下載並匯入 Azure[語音 SDK](https://aka.ms/csspeech/unitypackage) Unity 資產套件。</span><span class="sxs-lookup"><span data-stu-id="cac98-119">Download and import the Azure [Speech SDK](https://aka.ms/csspeech/unitypackage) for Unity asset package.</span></span> <span data-ttu-id="cac98-120">「 資產 」 選取 [匯入封裝] 然後選取 [自訂封裝]。 按一下以匯入語音 SDK 套件</span><span class="sxs-lookup"><span data-stu-id="cac98-120">Import the Speech SDK package by clicking on "assets," selecting "import package," then selecting "custom package."</span></span> <span data-ttu-id="cac98-121">尋找先前下載的語音 SDK 套件，並開啟它，以開始匯入程序。</span><span class="sxs-lookup"><span data-stu-id="cac98-121">Find the Speech SDK package downloaded earlier and open it to begin the importing process.</span></span> 

![Module4Chapter1step3im](images/module4chapter1step3im.PNG)

4. <span data-ttu-id="cac98-123">在下一步] 快顯視窗中，按一下 [開始匯入的語音 SDK 套件的 「 匯入 」。</span><span class="sxs-lookup"><span data-stu-id="cac98-123">In the next pop-up window, click “Import” to begin importing the Speech SDK package.</span></span> <span data-ttu-id="cac98-124">請確定選取所有項目，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="cac98-124">Ensure all items are checked, as shown in the image below.</span></span>

![Module4Chapter1step4im](images/module4chapter1step4im.PNG)


5. <span data-ttu-id="cac98-126">下載[Lunarcom](https://github.com/levilais/Speech-SDK-Module/raw/master/Speech SDK Module/Lunarcom.unitypackage)資產套件。</span><span class="sxs-lookup"><span data-stu-id="cac98-126">Download the [Lunarcom](https://github.com/levilais/Speech-SDK-Module/raw/master/Speech SDK Module/Lunarcom.unitypackage) asset package.</span></span> <span data-ttu-id="cac98-127">Lunarcom 資產封裝是資產和這一課一系列開發的指令碼，展示 Azure 的語音 SDK 的實際用途的集合。</span><span class="sxs-lookup"><span data-stu-id="cac98-127">The Lunarcom asset package is a collection of assets and scripts developed for this lesson series to showcase a practical use of Azure's Speech SDK.</span></span> <span data-ttu-id="cac98-128">它是語音命令終端機中，最後將介面中所開發的組件農曆模組體驗[基底模組的教學課程。](mrlearning-base-ch6.md)</span><span class="sxs-lookup"><span data-stu-id="cac98-128">It is a voice-command terminal that will ultimately interface with the lunar module assembly experience developed in the [Base Module Tutorial.](mrlearning-base-ch6.md)</span></span>
6. <span data-ttu-id="cac98-129">匯入 Unity 專案的 Lunarcom 資產封裝，依照類似的步驟，您用來匯入的混合實境工具組和語音 SDK。</span><span class="sxs-lookup"><span data-stu-id="cac98-129">Import the Lunarcom asset package into your Unity project by following similar steps you took to import the Mixed Reality Toolkit and Speech SDK.</span></span>
7. <span data-ttu-id="cac98-130">設定混合的實境工具組 (MRTK)。</span><span class="sxs-lookup"><span data-stu-id="cac98-130">Configure the Mixed Reality Toolkit (MRTK).</span></span> <span data-ttu-id="cac98-131">若要這樣做，《 混合實境 Toolkit 》 中的面板頂端的 程式 視窗中，按一下，然後按 加入至場景，然後設定。</span><span class="sxs-lookup"><span data-stu-id="cac98-131">To do this, click on the "Mixed Reality Toolkit" panel in the top of your window, and then select "Add to Scene and Configure."</span></span>

![Module4Chapter1step7im](images/module4chapter1step7im.PNG)

8. <span data-ttu-id="cac98-133">場景會現在有數個新的項目從 MRTK。</span><span class="sxs-lookup"><span data-stu-id="cac98-133">Your scene will now have several new items in it from the MRTK.</span></span> <span data-ttu-id="cac98-134">儲存在不同的名稱，按一下 [檔案] 下場景，然後 「 另存為"和"SpeechScene"命名您的場景。</span><span class="sxs-lookup"><span data-stu-id="cac98-134">Save your scene under a different name by clicking on "file," then "save as" and name your scene “SpeechScene”.</span></span> 

   > <span data-ttu-id="cac98-135">注意:如果 MRTK 加入您的專案，並將不會進入 「 播放 」 模式之後，您可以按在場景的 [播放] 按鈕，您可能需要重新啟動 Unity。</span><span class="sxs-lookup"><span data-stu-id="cac98-135">Note: If you press the play button on your scene after you add the MRTK to your project, and it doesn't enter the "play" mode, you may need to restart Unity.</span></span> 

9. <span data-ttu-id="cac98-136">「 MixedRealityToolkit 「 選取的物件階層中，「 複製和自訂 」 窗格中按一下 偵測器。</span><span class="sxs-lookup"><span data-stu-id="cac98-136">With the “MixedRealityToolkit" object selected in your hierarchy, click "copy and customize" in the inspector panel.</span></span>

![Module4Chapter1step9im](images/module4chapter1step9im.PNG)

10. <span data-ttu-id="cac98-138">也在偵測器窗格中 （包含在您階層中選取 「 MixedRealityToolkit 」 物件），來停用診斷系統取消核取方塊右邊的 「 啟用診斷系統。 」</span><span class="sxs-lookup"><span data-stu-id="cac98-138">Also in the inspector panel (with the “MixedRealityToolkit" object selected in your hierarchy), disable the diagnostics system by unchecking the box to the right of "Enable Diagnostics System."</span></span>

![Module4Chapter1step10im](images/module4chapter1step10im.PNG)

11. <span data-ttu-id="cac98-140">在 [專案] 面板中，展開 「 Lunarcom"資料夾，「 Lunarcom_Base"prefab 拖曳至您的階層。</span><span class="sxs-lookup"><span data-stu-id="cac98-140">In the project panel, expand the "Lunarcom" folder and drag the "Lunarcom_Base" prefab into your hierarchy.</span></span>

![Module4Chapter1step11im](images/module4chapter1step11im.PNG)

12. <span data-ttu-id="cac98-142">選取階層中的"Lunarcom_Base 」 物件，並確定位置設為 x = 0，y = 0，且 z = 0，以及旋轉設為 x = 0，y = 0，且 z = 0。</span><span class="sxs-lookup"><span data-stu-id="cac98-142">Select the "Lunarcom_Base" object in your hierarchy and ensure that the position is set to x=0, y=0, and z=0, as well as the rotation set to x=0, y=0, and z=0.</span></span> <span data-ttu-id="cac98-143">設定要讀取的縮放比例 x = $0.008，y = $0.008，且 z = 0.01。</span><span class="sxs-lookup"><span data-stu-id="cac98-143">Set the scale to read x=0.008, y=0.008, and z=0.01.</span></span>

![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

13. <span data-ttu-id="cac98-145">按一下 [新增元件]，然後搜尋並選取 「 LunarcomController。 」</span><span class="sxs-lookup"><span data-stu-id="cac98-145">Click "add component" and search for and select “LunarcomController.”</span></span> <span data-ttu-id="cac98-146">此指令碼會包含在您匯入在步驟 6 中 Lunarcom 資產套件。</span><span class="sxs-lookup"><span data-stu-id="cac98-146">This script is included in the Lunarcom asset pack that you imported in Step 6.</span></span>

![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

14. <span data-ttu-id="cac98-148">我們的應用程式連線至 Azure 認知服務，您必須輸入 「 訂用帳戶金鑰 」 也稱為 「 API 金鑰 」 的語音服務。</span><span class="sxs-lookup"><span data-stu-id="cac98-148">To connect our app to Azure Cognitive Services, you must enter a "subscription key" also known as an "API Key" for the Speech Service.</span></span> <span data-ttu-id="cac98-149">請遵循指示[此連結](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started)取得免費訂用帳戶金鑰。</span><span class="sxs-lookup"><span data-stu-id="cac98-149">Follow the instructions at [this link](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started) to obtain a free subscription key.</span></span> <span data-ttu-id="cac98-150">一旦您取得訂用帳戶金鑰時，它的欄位中輸入 「 語音服務 API 金鑰 」"LunarcomController 」 中元件的偵測器 面板中，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="cac98-150">Once you obtain the subscription key, enter it into the “Speech Service API Key” field of the "LunarcomController" component in the inspector panel, as shown in the image below.</span></span>

15. <span data-ttu-id="cac98-151">請輸入您註冊時選擇您的訂用帳戶金鑰"LunarcomController 」 元件，在 [偵測器] 面板的 [語音服務區域] 欄位中的區域。</span><span class="sxs-lookup"><span data-stu-id="cac98-151">Enter the Region that you chose when you signed up for the subscription key into the “Speech Service Region” field of the "LunarcomController" component in the inspector panel.</span></span>

![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

16. <span data-ttu-id="cac98-153">在您階層中，展開 「 Lunarcom_Base 」 物件，左邊的箭號，即可然後執行它的子物件，「 終端機 」，在下圖所示相同的動作。</span><span class="sxs-lookup"><span data-stu-id="cac98-153">In your hierarchy, expand the "Lunarcom_Base" object by clicking the arrow to the left of it, then do the same for its child object, "Terminal" as shown in the image below.</span></span>

17. <span data-ttu-id="cac98-154">選取 「 Lunarcom_Base"時，請按一下並拖曳 」 Lunarcom 文字"從階層至 「 輸出文字 「 位置 」 LunarcomController 」 元件中在偵測器窗格中，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="cac98-154">While "Lunarcom_Base" is selected, click and drag “Lunarcom Text” from the hierarchy to the "Output Text" slot in the "LunarcomController" component in the inspector panel, as shown in the image below.</span></span>
18. <span data-ttu-id="cac98-155">現在執行相同的動作，與 「 終端機 」 物件的 「 終端機 」 的位置和 「 連線指示燈控制器 」 位置的 「 連線 Light"物件。</span><span class="sxs-lookup"><span data-stu-id="cac98-155">Now do the same thing with the "Terminal" object into the "terminal" slot and the "Connection Light" object to the "Connection Light Controller" slot.</span></span>

![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

19. <span data-ttu-id="cac98-157">按一下"LunarcomController 」 指令碼，在 [偵測器] 面板中的"Lunarcom 按鈕 」 區段旁的箭號和將大小變更為 3，在鍵盤上按 Enter 或 Return 鍵。</span><span class="sxs-lookup"><span data-stu-id="cac98-157">Click the arrow next to the "Lunarcom Buttons" section of the "LunarcomController" script in the inspector panel and change the size to 3 and press the Enter or Return key on your keyboard.</span></span> <span data-ttu-id="cac98-158">這會導致三個新的 「 項目 」 欄位會出現。</span><span class="sxs-lookup"><span data-stu-id="cac98-158">This will cause three new "Element" fields to appear.</span></span>

![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

20. <span data-ttu-id="cac98-160">展開"Lunarcom 按鈕 」，即可在您的階層旁的箭號，並使用與上述相同的程序，將拖曳至 0、 1 和 2 的項目參考中的"LunarcomController 」 元件中分別 Mic、 衛星和 Rocket gameobject偵測器 面板中。</span><span class="sxs-lookup"><span data-stu-id="cac98-160">Expand the "Lunarcom Buttons" by clicking the arrow next to it in your hierarchy and, using the same process as above, drag the Mic, Satellite, and Rocket gameobjects to the Element 0, 1, and 2 references respectively in the "LunarcomController" component in the inspector panel.</span></span> 

![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

21. <span data-ttu-id="cac98-162">在您階層中選取 「 Lunarcom_Base 」 物件。</span><span class="sxs-lookup"><span data-stu-id="cac98-162">Select the "Lunarcom_Base" object in your hierarchy.</span></span> <span data-ttu-id="cac98-163">在 [偵測器] 面板中按一下 [新增元件] 然後搜尋並選取 「 LunarcomWakeWordRecognizer。 」</span><span class="sxs-lookup"><span data-stu-id="cac98-163">Click “Add Component” in the inspector panel and search for and select “LunarcomWakeWordRecognizer.”</span></span>

![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

22. <span data-ttu-id="cac98-165">在 「 線上醒機的字 」 位置中，輸入 「 啟動終端機。 」</span><span class="sxs-lookup"><span data-stu-id="cac98-165">In the "Wake Word" slot, type in "Activate Terminal."</span></span> <span data-ttu-id="cac98-166">此外，在 「 關閉 Word 」 介面槽中，輸入 「 解除終端機。 」</span><span class="sxs-lookup"><span data-stu-id="cac98-166">Also, in the "Dismiss Word" slot, type in "Dismiss Terminal."</span></span>

![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

## <a name="congratulations"></a><span data-ttu-id="cac98-168">恭喜！</span><span class="sxs-lookup"><span data-stu-id="cac98-168">Congratulations</span></span>

<span data-ttu-id="cac98-169">您已設定您的應用程式中，然後再由 Azure 中的語音辨識 ！</span><span class="sxs-lookup"><span data-stu-id="cac98-169">You've set up voice recognition in your application, powered by Azure!</span></span> <span data-ttu-id="cac98-170">執行應用程式，以確保所有函式都能正常運作。</span><span class="sxs-lookup"><span data-stu-id="cac98-170">Run the application to ensure all functions are working properly.</span></span> <span data-ttu-id="cac98-171">開始說喚醒 smokey 您在步驟 22，「 啟動終端機。 」</span><span class="sxs-lookup"><span data-stu-id="cac98-171">Start with saying the wake word you typed in step 22, "Activate Terminal."</span></span> <span data-ttu-id="cac98-172">然後，選取 麥克風 按鈕，啟動 語音辨識，並開始說話。</span><span class="sxs-lookup"><span data-stu-id="cac98-172">Then, select the microphone button to start voice recognition and begin speaking.</span></span> <span data-ttu-id="cac98-173">您會看到您說話的時候謄寫終端機中的文字。</span><span class="sxs-lookup"><span data-stu-id="cac98-173">You will see your words transcribed in the terminal as you speak.</span></span> <span data-ttu-id="cac98-174">按第二次的麥克風按鈕，以停止語音辨識。</span><span class="sxs-lookup"><span data-stu-id="cac98-174">Press the microphone button a second time to stop voice recognition.</span></span> <span data-ttu-id="cac98-175">說 「 關閉終端機 」 來隱藏 Lunarcom 終端機。</span><span class="sxs-lookup"><span data-stu-id="cac98-175">Say "Dismiss Terminal" to hide the Lunarcom terminal.</span></span> <span data-ttu-id="cac98-176">在下一個課程中，我們將了解如何使用開啟裝置電源的語音辨識，其中 Azure 的語音 SDK 因為無法使用離線 HoloLens 2 的情況下動態切換。</span><span class="sxs-lookup"><span data-stu-id="cac98-176">In the next lesson, we'll learn how to dynamically switch to using device-powered voice recognition, for situations where Azure's speech SDK isn't available due to the HoloLens 2 being offline.</span></span>

[<span data-ttu-id="cac98-177">下一課：語音 SDK 第 2 課</span><span class="sxs-lookup"><span data-stu-id="cac98-177">Next Lesson: Speech SDK Lesson 2</span></span>](mrlearning-speechSDK-ch2.md)

