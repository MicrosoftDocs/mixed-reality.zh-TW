---
title: Azure 語音服務教學課程-1。 整合和使用語音辨識與轉譯
description: 完成此課程，以瞭解如何在混合現實應用程式中執行 Azure 語音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 4baef90f8e00e5da1063c708ae24d2057e0dc227
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438380"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a>1. 整合和使用語音辨識與轉譯

本教學課程會建立一個混合現實應用程式，以探索 Azure 認知服務 Speech SDK 與 HoloLens 2 的搭配使用。 完成本教學課程系列之後，您將能夠使用裝置的麥克風即時轉譯語音轉換文字、將語音翻譯成其他語言，以及利用語音 SDK 的意圖功能來瞭解語音命令，方法是使用人工智慧。

## <a name="objectives"></a>目標

- 瞭解如何將 Azure 語音 SDK 整合至 HoloLens 2 應用程式
- 瞭解如何使用語音命令
- 瞭解如何使用語音轉換文字功能

## <a name="instructions"></a>指示

### <a name="getting-started"></a>開始使用

1. 啟動 Unity，並建立新的專案。 輸入專案名稱 [語音 SDK 學習模組]。 選擇要儲存專案的位置。 然後按一下 [建立專案]。

![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

> 注意：請確定範本已設定為3D，如上圖所示。

2. 下載[Mixed Reality 工具](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage)組 Unity 套件，並將它儲存到您電腦上的資料夾。 將套件匯入至您的 Unity 專案。 如需如何執行此動作的詳細指示，請參閱[基底模組第1課](mrlearning-base-ch1.md)。 

3. 下載並匯入 Unity 資產套件的 Azure[語音 SDK](https://aka.ms/csspeech/unitypackage) 。 按一下 [資產]，選取 [匯入套件]，然後選取 [自訂套件]，以匯入語音 SDK 套件。 尋找稍早下載的語音 SDK 套件，然後開啟以開始匯入程式。 

![Module4Chapter1step3ima](images/module4chapter1step3ima.PNG)

![Module4Chapter1step3im](images/module4chapter1step3im.PNG)

4. 在下一個快顯視窗中，按一下 [匯入] 開始匯入語音 SDK 套件。 請確定已核取所有專案，如下圖所示。

![Module4Chapter1step4im](images/module4chapter1step4im.PNG)

5. 按一下[此連結](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2)，以下載語音 SDK 模組資產套件，也就是 Lunarcom 套件。 Lunarcom 資產套件是針對此課程系列所開發的資產和腳本集合，以展示 Azure 語音 SDK 的實際使用。 它是語音命令終端機，最終會與[基本模組教學](mrlearning-base-ch6.md)課程中開發的陰曆模組元件體驗互動。

6. 遵循匯入混合現實工具組和語音 SDK 所需的類似步驟，將 Lunarcom 資產封裝匯入 Unity 專案。
7. 設定混合現實工具組（MRTK）。 若要這麼做，請按一下視窗頂端的 [混合現實工具組] 面板，然後選取 [新增至場景並設定]。

![Module4Chapter1step7im](images/module4chapter1step7im.PNG)

![module4Chapter1step9ima](images/module4chapter1step9ima.PNG)

![module4Chapter1step9imb](images/module4chapter1step9imb.PNG)

8. 您的場景現在在 MRTK 中有數個新專案。 依序按一下 [檔案] 和 [另存新檔]，並命名您的場景 SpeechScene，以不同的名稱儲存場景。 

> 注意：如果您在將 MRTK 新增至專案之後按下 [播放]，而它不進入 [播放] 模式，您可能需要重新開機 Unity。 

9. 在您的階層中選取 MixedRealityToolkit 物件後，按一下 [檢查] 面板中的 [複製並自訂]。

![Module4Chapter1step9im](images/module4chapter1step9im.PNG)

10. 此外，在 [偵測器] 面板中（已選取階層中的 [MixedRealityToolkit] 物件），取消核取 [啟用診斷系統] 右邊的方塊來停用診斷系統。

![Module4Chapter1step9imd](images/module4chapter1step9imd.PNG)

11. 若要啟用語音命令，請選取新建立的 MRTK 設定檔以進行自訂。 在本教學課程中，我們會使用語音辨識和轉譯的輸入語音命令。 讓我們複製輸入設定檔，以變更語音設定。

![Module4Chapter1step11imb](images/module4chapter1step11imb.PNG)

![Module4Chapter1step11imd](images/module4chapter1step11imd.PNG)

12. 複製輸入設定檔之後，請移至 [語音命令] 並複製語音命令。

![Module4Chapter1step12imb](images/module4chapter1step12imb.PNG)

![Module4Chapter1step12imc](images/module4chapter1step12imc.PNG)

13. 現在，在 [語音命令] 底下，移至 [一般設定]，並將 [啟動行為] 設定為 [手動啟動]

![Module4Chapter1step13imb](images/module4chapter1step13imb.PNG)

14. 在 專案 面板中，展開 Lunarcom 資料夾，然後將 Lunarcom_Base prefab 拖曳至您的階層中。

![Module4Chapter1step11im](images/module4chapter1step11im.PNG)

15. 選取階層中的 [Lunarcom_Base] 物件，並確定 [位置] 設定為 x = 0、y = 0、z = 0，而且旋轉設定為 x = 0、y = 0 和 z = 0。 將縮放比例設定為 read x = 0.008、y = 0.008 和 z = 0.01。

![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

16. 按一下 [新增元件]，然後搜尋並選取 [LunarcomController]。 此腳本包含在您于步驟6匯入的 Lunarcom 資產套件中。

![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

17. 若要將我們的應用程式連線到 Azure 認知服務，您必須為語音服務輸入訂用帳戶金鑰（也稱為 API 金鑰）。 請遵循[這裡](https://docs.microsoft.com//azure/cognitive-services/speech-service/get-started)的指示來取得免費的訂用帳戶金鑰。 一旦您取得訂用帳戶金鑰，請在 [偵測器] 面板的 [LunarcomController] 元件的 [語音服務 API 金鑰] 欄位中輸入，如下圖所示。

18. 輸入當您在 [偵測器] 面板中，于 LunarcomController 元件的 [語音服務區域] 欄位中註冊訂用帳戶金鑰時，所選擇的區域。 例如，針對「美國西部」區域，請輸入 "westus"

![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

19. 在您的階層中，按一下其左邊的箭號來展開 [Lunarcom_Base] 物件。 然後對其子物件「Terminal」執行相同的動作，如下圖所示。

20. 選取 [Lunarcom_Base] 時，請按一下階層中的 [Lunarcom 文字]，並將其從階層拖曳至 [偵測器] 面板中 [LunarcomController] 元件的輸出文字位置，如下圖所示。

21. 對終端機物件執行相同的動作，並將連接光源控制到連接光源控制器插槽。

![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

22. 在 [偵測器] 面板中，按一下 LunarcomController 腳本的 [Lunarcom 按鈕] 區段旁邊的箭號，然後將 [大小] 變更為3。 按 Enter 或 Return。 這會導致三個新的元素欄位出現。

![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

23. 按一下階層中其旁邊的箭號以展開 [Lunarcom] 按鈕，並使用上述相同的程式，分別將 Mic、衛星和 Rocket gameobject 拖曳至專案0、1和2的參考，其位於 [LunarcomController] 元件的偵測器面板。 

![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

24. 選取階層中的 [Lunarcom_Base] 物件。 按一下 [偵測器] 面板中的 [新增元件]，然後搜尋並選取 [LunarcomWakeWordRecognizer]。

![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

25. 在 [喚醒文字位置] 中，輸入「啟用終端機」。 在 [解除斷字位置] 中，輸入「關閉終端機」。

![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

### <a name="build-your-application-to-your-device"></a>對您的裝置建置應用程式

1. 前往 [檔案] > [組建設定]，再次開啟 [組建設定] 視窗。

![Tut1-lesson1-step3 Chapter5 步驟1](images/Lesson1Chapter5Step1.JPG)

2. 藉由按一下 [加入開啟場景] 按鈕，來確定您想要嘗試的場景有在 [建置中的場景] 清單中。
3. 按 [Player 設定] 按鈕，然後移至 [發佈設定]。 在 [功能] 底下，啟用：網際網路、網際網路用戶端伺服器、私人網路用戶端伺服器、麥克風和空間感知。
4. 在相同的播放人員設定中，移至 [XR 設定]，然後選取支援的虛擬實境。
5. 按下 [建置] 按鈕，開始建置程序。

![Tut1-lesson1-step3 Chapter5 步驟3](images/Lesson1Chapter5Step3.JPG)

6. 為您的應用程式建立並命名新資料夾。 在下圖中，已建立名為 “App” 的資料夾來包含應用程式。 按一下 [選取資料夾]，即可開始對新建立的資料夾進行建置。 建置完成之後，您可以關閉 Unity 中的 [建置設定] 視窗。 

![Tut1-lesson1-step3 Chapter5 步驟4](images/Lesson1Chapter5Step4.JPG)

> 注意：如果組建失敗，請嘗試重新建立或重新開機 Unity，然後重新建立。 如果您看到錯誤，例如「錯誤： CS0246 = 類型或命名空間名稱 "XX" 找不到（您是否遺漏 using 指示詞或元件參考？）」，則您可能需要安裝[Windows 10 SDK （10.0.18362.0）](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>)

7. 在建置完成之後，開啟新建立的資料夾，其中包含您新建置的應用程式檔案。 按兩下 ".sln" 方案檔，以在 Visual Studio 中開啟方案檔。

> 注意：請務必開啟新建立的資料夾（也就是「應用程式」資料夾，如果遵循先前步驟中的命名慣例），因為該資料夾外部會有類似的 .sln 檔案，不會與組建資料夾內的 .sln 檔案混淆。 

![Lesson1 Chapter5 Step5](images/Lesson1Chapter5Step5.JPG)

> 注意：如果 Visual Studio 要求您安裝新元件，請花點時間確認所有必要元件都已依照[[安裝工具] 頁面中的](install-the-tools.md)指定安裝

8. 使用 USB 纜線，將 HoloLens 2 插入您的電腦。 雖然這些課程指示假設您會以 HoloLens 2 裝置部署測試，但您也可以選擇部署到 [HoloLens 2 模擬器](using-the-hololens-emulator.md)或選擇建立[用於側載的應用程式套件](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)
9. 對您的裝置進行建置之前，請確定裝置處於開發人員模式。 如果這是您第一次部署到 HoloLens 2，Visual Studio 可能會要求您使用 pin 碼來與 HoloLens 2 配對。 若要啟用開發人員模式，或與 Visual Studio 配對，請遵循[這些指示](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio)。

10. 若要設定 Visual Studio 來對 HoloLens 2 進行建置，請選取 [發行] 組態和 [ARM] 架構。

![Tut1-lesson1-step3 Chapter5 Step8](images/Lesson1Chapter5Step8.JPG)

11. 最後一個步驟是選取 [偵錯] > [啟動但不偵錯] 來對您的裝置進行建置。 選取 [啟動但不偵錯] 會讓裝置上的應用程式在建置成功時立即啟動，但 Visual Studio 中不會出現偵錯資訊。 這也表示，當您的應用程式在 HoloLens 2 上執行時，您可以在不需要停止應用程式的情況下拔掉 USB 纜線。 您也可以選取 [建置] > [部署解決方案]，在不自動啟動應用程式的情況下，對您的裝置進行部署。

![Tut1-lesson1-step3 Chapter5 Step9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>恭喜！

您已在應用程式中設定語音辨識（由 Azure 提供技術支援）。 執行應用程式，以確保所有功能和功能都能正常運作。 從說出您在步驟22中輸入的喚醒字，啟用終端機。 選取 [麥克風] 按鈕以開始語音辨識。 開始說話。 您會在說話時看到您在終端機中轉譯的單字。 第二次按下 [麥克風] 按鈕，以停止語音辨識。 假設 [關閉終端機] 以隱藏 Lunarcom 終端機。 在下一課中，我們將瞭解如何在因為 HoloLens 2 離線而無法使用 Azure 語音 SDK 的情況下，以動態方式切換至使用裝置供電的語音辨識。

[下一個教學課程： 2. 新增本機語音轉換文字翻譯的離線模式](mrlearning-speechSDK-ch2.md)

