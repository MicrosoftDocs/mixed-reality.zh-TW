# <a name="speech-sdk-learning-module"></a>語音 SDK 學習模組

在本教學課程中，您將建立的混合實境應用程式，探索如何使用 Azure 認知服務語音 SDK 與 HoloLens 2。 完成本教學課程系列，您將能夠使用您的裝置的麥克風 ip-pbx 語音轉換文字即時、 將您的語音翻譯成其他語言中，並利用語音 SDK 的意圖功能，以了解使用語音命令人工智慧。

目標：

- 了解如何將 Azure 語音 SDK 整合到 HoloLens 2 應用程式
- 了解如何使用語音命令
- 了解如何使用語音轉換文字功能

## <a name="instructions"></a>指示

### <a name="getting-started"></a>開始使用

1. 啟動 Unity 並建立新的專案。 輸入專案名稱 「 語音 SDK 學習模組 」。 選擇要儲存專案的位置。 然後按一下 [建立專案]。

![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

> 注意:請確定範本設為 「 3D 」，如上圖所示。

2. 下載[混合實境 Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) Unity 套件，並將它儲存在您的電腦上的資料夾。 匯入 Unity 專案的封裝。 如需如何執行這項操作的詳細指示，請參閱[第 1 課的基本模組](mrlearning-base-ch1.md)。 

3. 下載並匯入 Azure[語音 SDK](https://aka.ms/csspeech/unitypackage) Unity 資產套件。 「 資產 」 選取 [匯入封裝] 然後選取 [自訂封裝]。 按一下以匯入語音 SDK 套件 尋找先前下載的語音 SDK 套件，並開啟它，以開始匯入程序。 

![Module4Chapter1step3im](images/module4chapter1step3im.PNG)

4. 在下一步] 快顯視窗中，按一下 [開始匯入的語音 SDK 套件的 「 匯入 」。 請確定選取所有項目，如下圖所示。

![Module4Chapter1step4im](images/module4chapter1step4im.PNG)


5. 下載[Lunarcom](https://github.com/levilais/Speech-SDK-Module/raw/master/Speech SDK Module/Lunarcom.unitypackage)資產套件。 Lunarcom 資產封裝是資產和這一課一系列開發的指令碼，展示 Azure 的語音 SDK 的實際用途的集合。 它是語音命令終端機中，最後將介面中所開發的組件農曆模組體驗[基底模組的教學課程。](mrlearning-base-ch6.md)
6. 匯入 Unity 專案的 Lunarcom 資產封裝，依照類似的步驟，您用來匯入的混合實境工具組和語音 SDK。
7. 設定混合的實境工具組 (MRTK)。 若要這樣做，《 混合實境 Toolkit 》 中的面板頂端的 程式 視窗中，按一下，然後按 加入至場景，然後設定。

![Module4Chapter1step7im](images/module4chapter1step7im.PNG)

8. 場景會現在有數個新的項目從 MRTK。 儲存在不同的名稱，按一下 [檔案] 下場景，然後 「 另存為"和"SpeechScene"命名您的場景。 

   > 注意:如果 MRTK 加入您的專案，並將不會進入 「 播放 」 模式之後，您可以按在場景的 [播放] 按鈕，您可能需要重新啟動 Unity。 

9. 「 MixedRealityToolkit 「 選取的物件階層中，「 複製和自訂 」 窗格中按一下 偵測器。

![Module4Chapter1step9im](images/module4chapter1step9im.PNG)

10. 也在偵測器窗格中 （包含在您階層中選取 「 MixedRealityToolkit 」 物件），來停用診斷系統取消核取方塊右邊的 「 啟用診斷系統。 」

![Module4Chapter1step10im](images/module4chapter1step10im.PNG)

11. 在 [專案] 面板中，展開 「 Lunarcom"資料夾，「 Lunarcom_Base"prefab 拖曳至您的階層。

![Module4Chapter1step11im](images/module4chapter1step11im.PNG)

12. 選取階層中的"Lunarcom_Base 」 物件，並確定位置設為 x = 0，y = 0，且 z = 0，以及旋轉設為 x = 0，y = 0，且 z = 0。 設定要讀取的縮放比例 x = $0.008，y = $0.008，且 z = 0.01。

![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

13. 按一下 [新增元件]，然後搜尋並選取 「 LunarcomController。 」 此指令碼會包含在您匯入在步驟 6 中 Lunarcom 資產套件。

![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

14. 我們的應用程式連線至 Azure 認知服務，您必須輸入 「 訂用帳戶金鑰 」 也稱為 「 API 金鑰 」 的語音服務。 請遵循指示[此連結](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started)取得免費訂用帳戶金鑰。 一旦您取得訂用帳戶金鑰時，它的欄位中輸入 「 語音服務 API 金鑰 」"LunarcomController 」 中元件的偵測器 面板中，如下圖所示。

15. 請輸入您註冊時選擇您的訂用帳戶金鑰"LunarcomController 」 元件，在 [偵測器] 面板的 [語音服務區域] 欄位中的區域。

![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

16. 在您階層中，展開 「 Lunarcom_Base 」 物件，左邊的箭號，即可然後執行它的子物件，「 終端機 」，在下圖所示相同的動作。

17. 選取 「 Lunarcom_Base"時，請按一下並拖曳 」 Lunarcom 文字"從階層至 「 輸出文字 「 位置 」 LunarcomController 」 元件中在偵測器窗格中，如下圖所示。
18. 現在執行相同的動作，與 「 終端機 」 物件的 「 終端機 」 的位置和 「 連線指示燈控制器 」 位置的 「 連線 Light"物件。

![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

19. 按一下"LunarcomController 」 指令碼，在 [偵測器] 面板中的"Lunarcom 按鈕 」 區段旁的箭號和將大小變更為 3，在鍵盤上按 Enter 或 Return 鍵。 這會導致三個新的 「 項目 」 欄位會出現。

![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

20. 展開"Lunarcom 按鈕 」，即可在您的階層旁的箭號，並使用與上述相同的程序，將拖曳至 0、 1 和 2 的項目參考中的"LunarcomController 」 元件中分別 Mic、 衛星和 Rocket gameobject偵測器 面板中。 

![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

21. 在您階層中選取 「 Lunarcom_Base 」 物件。 在 [偵測器] 面板中按一下 [新增元件] 然後搜尋並選取 「 LunarcomWakeWordRecognizer。 」

![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

22. 在 「 線上醒機的字 」 位置中，輸入 「 啟動終端機。 」 此外，在 「 關閉 Word 」 介面槽中，輸入 「 解除終端機。 」

![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

## <a name="congratulations"></a>恭喜！

您已設定您的應用程式中，然後再由 Azure 中的語音辨識 ！ 執行應用程式，以確保所有函式都能正常運作。 開始說喚醒 smokey 您在步驟 22，「 啟動終端機。 」 然後，選取 麥克風 按鈕，啟動 語音辨識，並開始說話。 您會看到您說話的時候謄寫終端機中的文字。 按第二次的麥克風按鈕，以停止語音辨識。 說 「 關閉終端機 」 來隱藏 Lunarcom 終端機。 在下一個課程中，我們將了解如何使用開啟裝置電源的語音辨識，其中 Azure 的語音 SDK 因為無法使用離線 HoloLens 2 的情況下動態切換。

[下一課：語音 SDK 第 2 課](mrlearning-speechSDK-ch2.md)

