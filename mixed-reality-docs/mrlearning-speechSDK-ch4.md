---
title: Azure 語音服務教學課程-4。 設定意圖和自然語言理解
description: 完成此課程，以瞭解如何在混合現實應用程式中執行 Azure 語音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 9235452d9dce38e9d849821a694a5d4c710d8e87
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913281"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a>4. 設定意圖和自然語言理解

在這一課，我們將探索 Azure 語音服務的意圖功能。 「意圖」功能可讓我們使用 AI 提供的語音命令來提供應用程式，使用者可以在其中說出非特定的語音命令，並仍然讓系統瞭解其意圖。 在此課程中，我們將設定 Azure LUIS 入口網站、設定我們的意圖/實體/語句、發佈意圖資源、將 Unity 應用程式連接至意圖資源，以及進行我們的第一個意圖 API 呼叫。

## <a name="objectives"></a>目標

- 瞭解如何在我們的應用程式中設定意圖和自然語言理解
- 瞭解如何設定 Azure 的 LUIS 入口網站
- 瞭解如何在 Azure 上設定意圖、實體和語句

## <a name="instructions"></a>指示

1. 允許您的電腦啟用聽寫，若要這麼做，請移至 [Windows 設定]，選取 [隱私權]，然後選取 [語音]，最後是 [筆跡 & 輸入]，然後開啟 [語音服務] 並輸入建議。

    ![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

    ![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

    ![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

2. 登入[Azure 入口網站](https://portal.azure.com/)。 登入之後，請按一下 [建立資源]，並搜尋 "Language Understanding"，然後按一下 enter。

    ![mrlearning-speech-ch4-1-step2 .png](images/mrlearning-speech-ch4-1-step2.png)

3. 按一下 [**建立**] 按鈕，以建立此服務的實例。

    ![mrlearning-speech-ch4-1-step3a .png](images/mrlearning-speech-ch4-1-step3a.png)

    提供資源的**名稱**，例如*語音-SDK 學習模組*。 針對 [**訂**用帳戶]，選取 [*隨用隨付*] 或 [*免費記錄*] （如果您有試用帳戶）。 接下來，按一下 [**建立新**的] 連結，輸入名稱（例如， *HoloLens-2-教學課程-資源群組*），然後按一下 [**確定]** 按鈕，以建立新的**資源群組**。

    ![mrlearning-speech-ch4-1-step3b .png](images/mrlearning-speech-ch4-1-step3b.png)

4. 選取您的**撰寫位置**和**執行時間位置**，基於本教學課程的目的，請使用 *（us）「美國西部*」。 然後選擇 [**撰寫] 定價層**和 [執行時間]**定價層**的 [ *F0 （每秒5個呼叫]、[每月*10，000個呼叫]）。 最後，按一下 [**建立**] 按鈕，以建立資源和新的資源群組。

    ![mrlearning-speech-ch4-1-step4 .png](images/mrlearning-speech-ch4-1-step4.png)

    >[!NOTE]
    >按一下 [建立] 按鈕之後，您必須等候服務建立，這可能需要幾分鐘的時間。

5. 資源建立程式完成後，您會看到**部署已完成**的訊息。

    ![mrlearning-speech-ch4-1-step5 .png](images/mrlearning-speech-ch4-1-step5.png)

6. 使用相同的使用者帳戶，登入[Language Understanding 智慧型服務（LUIS）](https://www.luis.ai/)入口網站，選取您的國家/地區，並同意使用條款。

    >[!NOTE]
    >到達 Language Understanding 入口網站時，您可能需要登入（如果您尚未這麼做），其認證與您的 Azure 入口網站相同。 如果這是您第一次使用 LUIS，您將需要向下滾動到歡迎頁面底部，以尋找並按一下 [建立 LUIS] 應用程式按鈕。

7. 登入之後，按一下 [我的應用程式] （如果您目前不在該區段中）。 然後，您可以按一下 [建立新的應用程式]。 將新的應用程式命名為「語音 SDK 學習模組」。 也將「語音 SDK 學習模組」新增至 [描述] 欄位。 然後按一下 [完成]。

    ![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

    ![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

    >[!NOTE]
    >如果您的應用程式應該瞭解與英文不同的語言，您應該將「文化特性」變更為適當的語言。

8. 按一下位於右上方的 [組建]。

9. 在左側的 [應用程式資產] 底下，選取 [意圖]，然後按一下 [建立新意圖]，並將它命名為 "PressButton"。

    ![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

    >[!NOTE]
    >請務必使用本教學課程中使用的意圖和機構名稱，因為 Lunarcom 應用程式會依名稱參考它們。

    >[!NOTE]
    >您現在應該有兩個意圖-"PressButton" 和 "None"。

10. 在左側的 [應用程式資產] 底下，選取 [實體]，然後按一下 [建立新實體]，並將其命名為「動作」，並將實體類型保留為「簡單」。

    ![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

11. 再次按一下 [建立新實體]，並將它命名為 "Target"，並將實體類型保留為「簡單」。

    ![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

12. 在左側的 [應用程式資產] 底下，選取 [意圖]，然後按一下您在步驟10中建立的「PressButton」意圖。

    ![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

13. 按一下右側的 [視圖選項] 下拉式清單，然後選取 [顯示實體值]。

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)

    按一下 [輸入範例 ...] 工具箱. 然後，輸入下列語句：

    ![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

14. 按一下右側的 [視圖選項] 下拉式清單，然後選取 [顯示機構名稱]。

    ![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

15. 確定10個語句中的每個都在下列位置具有下列實體標籤1。）按一下標記錯誤的單字，然後在快顯視窗中選取 [移除標籤] 和 [2]）。按一下應該加上標籤的單字，然後在快顯視窗中選取適當的標籤。

    ![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

16. 現在，若要發行模型，請按一下右上方的 [定型]。 然後，在完成處理之後，按一下右上方的 [測試]。

    ![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

17. 在文字方塊中輸入「選取啟動按鈕」。

    >[!NOTE]
    >我們並未在語句中新增「選取」做為動作，但如果您按一下 [檢查]，則模型會被辨識為「選取」做為動作實體。
    >
    > ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

18. 現在，按一下右上方的 [發佈]。 確定下拉式清單顯示「生產環境」，然後按一下快顯上的 [發佈]。

    ![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

19. 發佈之後，頁面頂端應該會出現綠色橫條。  按一下要移至 [管理] 頁面的綠色橫條。

    ![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

20. 按一下左側 [應用程式設定] 底下的 [金鑰和端點]。 然後，將下拉式的 [發行至] 設定為 [生產]。 設定 [時區] 以符合您的時間，然後選取方塊以包含所有預測的意圖分數。 最後，按一下 [指派資源]。

    ![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

21. 從第一個下拉式清單中選取 [租使用者]，然後在 [訂用帳戶名稱] 下拉式清單中選取 [隨用隨付]。 在 [LUIS 資源名稱] 下，選擇我們在步驟1-5 中所建立的資源。 然後，按一下 [指派資源]。

    ![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

    >[!NOTE]
    >請務必複製並儲存與剛才指派的資源相關聯的端點 URL，以便在下一節中輕鬆存取。

    >[!NOTE]
    >在 [租使用者名稱] 中，放入您為此應用程式建立的公司或設定檔。

22. 現在，在 Unity 中開啟新的應用程式，然後選取階層中的 [Lunarcom_Base] 物件。 按一下 [偵測器] 面板中的 [新增元件]，然後搜尋並選取 [LunarcomIntentRecognizer]。

    ![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

23. 在 [偵測器] 面板中 "LunarcomIntentRecognizer" 的 [Luis 端點] 欄位中，輸入您在步驟22中儲存的端點 URL。

    ![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

    >[!NOTE]
    >在 [偵測器] 面板的 [LunarcomOfflineRecognizer] 元件中，確定已針對 [SimulateOfflineMode] 選取 [停用]，否則測試程式將無法正常執行。

24. 按下 Unity 編輯器中的 [播放] 按鈕，然後按一下 [rocket] 按鈕以啟動意圖辨識。 有些純粹是「選取啟動 rocket 按鈕」一詞。

    >[!NOTE]
    >應用程式已辨識所需的函式，並已啟用 [rocket] 按鈕。
    >
    >![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a>恭喜！

在本課程中，我們已瞭解如何新增 AI 驅動的語音命令！ 您的程式現在可以辨識使用者的意圖，即使他們沒有有些純粹是精確的語音命令也一樣。
