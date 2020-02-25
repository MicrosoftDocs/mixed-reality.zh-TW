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
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a>1. 整合和使用語音辨識與轉譯

## <a name="overview"></a>概觀

本教學課程會建立一個混合現實應用程式，以探索 Azure 認知服務 Speech SDK 與 HoloLens 2 的搭配使用。 當您完成本教學課程系列時，您將能夠使用裝置的麥克風即時轉譯語音轉換成文字、將語音翻譯成其他語言，以及利用語音 SDK 的意圖功能來瞭解使用人工智慧的語音命令情報.

## <a name="objectives"></a>目標

* 瞭解如何將 Azure 語音 SDK 整合至 HoloLens 2 應用程式
* 瞭解如何使用語音命令
* 瞭解如何使用語音轉換文字功能

## <a name="prerequisites"></a>必要條件

>[!TIP]
>如果您尚未完成[快速入門教學](mrlearning-base.md)課程系列，建議您先完成這些教學課程。

* 已[安裝正確工具](install-the-tools.md)的 Windows 10 電腦
* Windows 10 SDK 10.0.18362.0 或更新版本
* 基本的 C# 程式設計能力
* 已[針對開發而設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置

>[!IMPORTANT]
> 本教學課程系列的建議 Unity 版本是 Unity 2019.2. X。 這個版本能取代上述連結之必要條件中所述的任何 Unity 版本需求或建議。

## <a name="getting-started"></a>使用者入門

1. 啟動 Unity，並建立新的專案。 輸入專案名稱 [語音 SDK 學習模組]。 選擇要儲存專案的位置。 按一下 [建立專案]。

    ![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

    >[!NOTE]
    >請確定範本已設定為3D，如上圖所示。

2. 下載[Mixed Reality 工具](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)組 Unity [foundation 封裝版本 2.3.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage) ，並將它儲存到您電腦上的資料夾。 將套件匯入至您的 Unity 專案。 如需如何執行此動作的詳細指示，請參閱[快速入門教學課程-第2課。初始化您的專案和第一個應用程式](mrlearning-base-ch1.md)。

3. 下載並匯入 Unity 資產套件的 Azure[語音 SDK](https://aka.ms/csspeech/unitypackage) 。 按一下 [資產]，選取 [匯入套件]，然後選取 [自訂套件]，以匯入語音 SDK 套件。 尋找稍早下載的語音 SDK 套件，然後開啟以開始匯入程式。

    ![mrlearning-speech-ch1-1-step3a .png](images/mrlearning-speech-ch1-1-step3a.png)

    ![mrlearning-speech-ch1-1-step3b .png](images/mrlearning-speech-ch1-1-step3b.png)

4. 在下一個快顯視窗中，按一下 [匯入] 開始匯入語音 SDK 套件。 請確定已核取所有專案，如下圖所示。

    ![mrlearning-speech-ch1-1-step4 .png](images/mrlearning-speech-ch1-1-step4.png)

5. 下載教學課程資產：
    * [MRTK.HoloLens2 GettingStarted. 2.3.0.2. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
    * [SpeechSDKAssets. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/Speech_2/SpeechSDKAssets.unitypackage) （版本1.2）

    SpeechSDKAssets 資產套件是針對此教學課程系列所開發的資產和腳本集合，以展示 Azure 語音 SDK 的實際使用。 這是語音命令終端機，最終會與[快速入門教學課程-第7課所開發的 Rocket 啟動器元件體驗互動。建立農曆模組範例應用程式](mrlearning-base-ch6.md)。

6. 遵循匯入混合現實工具組和語音 SDK 所需的類似步驟，將兩個教學課程資產封裝匯入 Unity 專案。

7. 設定混合現實工具組（MRTK）。

    若要這麼做，請按一下視窗頂端的 [混合現實工具組] 面板，然後選取 [新增至場景並設定]。

    ![mrlearning-speech-ch1-1-step7a .png](images/mrlearning-speech-ch1-1-step7a.png)

    在場景階層中選取 MixedRealityToolkit 物件之後，在 [偵測器] 視窗中選取 [DefaultHoloLens2ConfigurationProfile]，使其成為混合現實工具組的作用中設定檔。

    ![mrlearning-speech-ch1-1-step7b .png](images/mrlearning-speech-ch1-1-step7b.png)

8. 您的場景現在在 MRTK 中有數個新專案。 依序按一下 [檔案] 和 [另存新檔]，並命名您的場景 SpeechScene，以不同的名稱儲存場景。

    >[!NOTE]
    >如果您在將 MRTK 新增至專案後按下場景上的 [播放]，而它不進入 [播放] 模式，您可能需要重新開機 Unity。

9. 在場景階層中選取 MixedRealityToolkit 物件後，按一下 [複製] & [檢查] 面板中的 [自訂]，開啟複製設定檔快顯視窗。 在 [複製設定檔] 快顯視窗中，為您的自訂設定檔輸入適當的名稱，例如 [自訂 HoloLens2ConfigurationProfile]。 按一下 [複製] 來建立您的自訂設定檔，並將它設定為使用中的設定檔。

    ![mrlearning-speech-ch1-1-step9 .png](images/mrlearning-speech-ch1-1-step9.png)

10. 此外，在 [偵測器] 面板中（已選取階層中的 [MixedRealityToolkit] 物件），取消核取 [啟用診斷系統] 右邊的方塊來停用診斷系統。

    ![mrlearning-speech-ch1-1-step10 .png](images/mrlearning-speech-ch1-1-step10.png)

11. 在本教學課程中，我們會使用語音辨識和轉譯的輸入語音命令。 讓我們複製輸入設定檔，以變更語音設定。

    當您的場景階層中仍然選取 MixedRealityToolkit 物件時，請按一下 [檢查] 面板中的 [小型複製] 按鈕，以開啟 [複製設定檔] 快顯視窗。 在 [複製設定檔] 快顯視窗中，為您的自訂設定檔輸入適當的名稱，例如 [自訂 HoloLens2InputSystemProfile]，然後按一下 [複製] 來建立自訂輸入系統設定檔，並將它設定為使用中設定檔。

    ![mrlearning-speech-ch1-1-step11 .png](images/mrlearning-speech-ch1-1-step11.png)

12. 複製輸入設定檔之後，展開 [語音] 區段，然後遵循上一個步驟中的相同程式來複製語音命令設定檔。

    ![mrlearning-speech-ch1-1-step12 .png](images/mrlearning-speech-ch1-1-step12.png)

13. 在 [語音] 區段下，移至 [一般設定]，並將 [啟動行為] 變更為手動啟動。

    ![mrlearning-speech-ch1-1-step13 .png](images/mrlearning-speech-ch1-1-step13.png)

14. 在 專案 面板中，展開 Lunarcom 資料夾，然後將 Lunarcom_Base prefab 拖曳到您的場景階層中。

    ![mrlearning-speech-ch1-1-step14 .png](images/mrlearning-speech-ch1-1-step14.png)

15. 選取階層中的 [Lunarcom_Base] 物件，並確定 [位置] 設定為 x = 0、y = 0、z = 0，而且旋轉設定為 x = 0、y = 0 和 z = 0。 將縮放比例設定為 read x = 0.008、y = 0.008 和 z = 0.01。

    ![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

16. 按一下 [新增元件]，然後搜尋並選取 [Lunarcom 控制器]。 此腳本包含在您于步驟6匯入的 Lunarcom 資產套件中。

    ![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

17. 若要將我們的應用程式連線到 Azure 認知服務，您必須為語音服務輸入訂用帳戶金鑰（也稱為 API 金鑰）。 請遵循[這裡](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started)的指示來取得免費的訂用帳戶金鑰。 一旦您取得訂用帳戶金鑰，請在 [偵測器] 面板的 [LunarcomController] 元件的 [語音服務 API 金鑰] 欄位中輸入它，如下圖所示。

18. 輸入當您在 [偵測器] 面板中，于 LunarcomController 元件的 [語音服務區域] 欄位中註冊訂用帳戶金鑰時，所選擇的區域。 例如，針對區域美國西部，請輸入 "westus"。

    ![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

19. 在您的階層中，按一下其左邊的箭號來展開 [Lunarcom_Base] 物件。 然後對其子物件「Terminal」執行相同的動作，如下圖所示。

20. 選取 [Lunarcom_Base] 時，請在 [偵測器] 面板中按一下 [Lunarcom 文字]，並將其從階層拖曳至 [LunarcomController] 元件中的輸出文字位置，如下圖所示。

21. 對終端機物件執行相同的動作，並將連接光源控制到連接光源控制器插槽。

    ![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

22. 在 [偵測器] 面板中，按一下 LunarcomController 腳本的 [Lunarcom 按鈕] 區段旁邊的箭號，然後將 [大小] 變更為3。 按 Enter 或 Return。 這會導致三個新的元素欄位出現。

    ![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

23. 按一下階層中其旁邊的箭號以展開 [Lunarcom] 按鈕，並使用上述相同的程式，分別將 Mic、衛星和 Rocket gameobject 拖曳至專案0、1和2的參考，其位於 [LunarcomController] 元件的偵測器面板。

    ![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

24. 選取階層中的 [Lunarcom_Base] 物件。 按一下 [偵測器] 面板中的 [新增元件]，然後搜尋並選取 [Lunarcom 語音辨識器]。 重複相同的步驟，以新增 Lunarcom 喚醒字辨識器。

    ![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

25. 在 [喚醒文字位置] 中，輸入「啟用終端機」。 在 [解除斷字位置] 中，輸入「關閉終端機」。

    ![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

## <a name="build-your-application-to-your-device"></a>對您的裝置建置應用程式

1. 前往 [檔案] > [組建設定]，再次開啟 [組建設定] 視窗。

    ![images/mrlearning-語音-ch1-2-步驟1](images/mrlearning-speach-ch1-2-step1.jpg)

2. 藉由按一下 [加入開啟場景] 按鈕，來確定您想要嘗試的場景有在 [建置中的場景] 清單中。

3. 按 [Player 設定] 按鈕，然後移至 [發佈設定]。 在 [功能] 底下，啟用：網際網路、網際網路用戶端伺服器、私人網路用戶端伺服器、麥克風和空間感知。

4. 在相同的播放人員設定中，移至 [XR 設定]，然後選取支援的虛擬實境。

5. 按下 [建置] 按鈕，開始建置程序。

    ![mrlearning-speech-ch1-2-步驟5](images/mrlearning-speach-ch1-2-step5.jpg)

6. 為您的應用程式建立並命名新資料夾。 在下圖中，已建立名為 “App” 的資料夾來包含應用程式。 按一下 [選取資料夾]，即可開始對新建立的資料夾進行建置。 建置完成之後，您可以關閉 Unity 中的 [建置設定] 視窗。

    ![mrlearning-speech-ch1-2-步驟6](images/mrlearning-speach-ch1-2-step6.jpg)

    >[!NOTE]
    >如果建置失敗，請再試一次，或重新啟動 Unity，然後重新建置。 如果您看到錯誤，例如「錯誤： CS0246 = 類型或命名空間名稱 "XX" 找不到（您是否遺漏 using 指示詞或元件參考？）」，您可能需要安裝[Windows 10 SDK （10.0.18362.0）](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>)

7. 在建置完成之後，開啟新建立的資料夾，其中包含您新建置的應用程式檔案。 按兩下 ".sln" 方案檔，以在 Visual Studio 中開啟方案檔。

    >[!NOTE]
    >請務必開啟新建立的資料夾（也就是「應用程式」資料夾，如果遵循先前步驟中的命名慣例），因為該資料夾外部會有類似的名稱 .sln 檔案，與組建資料夾內的 .sln 檔案不同。 

    ![mrlearning-speech-ch1-2-step7](images/mrlearning-speach-ch1-2-step7.jpg)

    >[!NOTE]
    >如果 Visual Studio 要求您安裝新元件，請確定已依照[[安裝工具] 頁面中的](install-the-tools.md)指定安裝所有必要元件

8. 使用 USB 纜線，將 HoloLens 2 插入您的電腦。 雖然這些課程指示假設您會以 HoloLens 2 裝置部署測試，但您也可以選擇部署到 [HoloLens 2 模擬器](using-the-hololens-emulator.md)或選擇建立[用於側載的應用程式套件](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)

9. 對您的裝置進行建置之前，請確定裝置處於開發人員模式。 如果這是您第一次部署到 HoloLens 2，Visual Studio 可能會要求您使用 pin 碼來與 HoloLens 2 配對。 若要啟用開發人員模式，或與 Visual Studio 配對，請遵循[這些指示](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio)。

10. 若要設定 Visual Studio 來對 HoloLens 2 進行建置，請選取 [發行] 組態和 [ARM] 架構。

    ![mrlearning-speech-ch1-2-step10](images/mrlearning-speach-ch1-2-step10.jpg)

11. 最後一個步驟是選取 [偵錯] > [啟動但不偵錯] 來對您的裝置進行建置。 選取 [啟動但不偵錯] 會讓裝置上的應用程式在建置成功時立即啟動，但 Visual Studio 中不會出現偵錯資訊。 這也表示，當您的應用程式在 HoloLens 2 上執行時，您可以在不需要停止應用程式的情況下拔掉 USB 纜線。 您也可以選取 [建置] > [部署解決方案]，在不自動啟動應用程式的情況下，對您的裝置進行部署。

    ![mrlearning-speech-ch1-2-step11.JPG](images/mrlearning-speach-ch1-2-step11.jpg)

## <a name="congratulations"></a>恭喜

您已在應用程式中設定語音辨識（由 Azure 提供技術支援）。 執行應用程式，以確保所有功能和功能都能正常運作。 從說出您在步驟25輸入的喚醒字，啟用終端機。 選取 [麥克風] 按鈕以開始語音辨識。 開始說話。 您會在說話時看到您在終端機中轉譯的單字。 第二次按下 [麥克風] 按鈕，以停止語音辨識。 假設 [關閉終端機] 以隱藏 Lunarcom 終端機。 在下一課中，您將瞭解如何在因為 HoloLens 2 離線而無法使用 Azure 語音 SDK 的情況下，以動態方式切換至使用裝置供電的語音辨識。

[下一個教學課程： 2. 新增本機語音轉換文字翻譯的離線模式](mrlearning-speechSDK-ch2.md)
