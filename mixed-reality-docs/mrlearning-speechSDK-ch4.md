## <a name="lesson-4"></a>第 4 課

在第 4 章，我們將探討語音服務的意圖功能。 我們將設定我們的 Azure LUIS 入口網站、 設定我們意圖/實體/談話、 發佈我們的意圖資源、 我們的 Unity 應用程式連線至我們的意圖的資源，並讓我們第一次的意圖 API 呼叫。

1. 可讓您的機器以啟用語音輸入，若要這樣做，移至 Windows 設定，選取 隱私權，然後"speech，"而最後 「 筆跡 & 輸入"並開啟語音服務與輸入的建議。

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

> 注意： 如需如何在 Mac/Macbook 上執行這項操作的資訊，請按一下[此處](linkgoeshere)。

2. 登入[Azure 入口網站](https://portal.azure.com/)。 一旦您登入，按一下建立的資源，並搜尋 「 語言理解 」，然後按一下 [輸入]。

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. 選取 [建立] 按鈕來建立此服務的執行個體。 命名您的專案 「 Speech_SDK_Learning_Module"，然後選取 「 預付。 」

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. 選取您的區域。  針對此教學課程中，選取 "（美國） West US"。 定價層，然後選擇 「 F0"。 現在按一下 [建立] （位於左下角） 來建立資源。

   >  注意： 一旦您按一下 [建立] 時，您必須建立服務，這可能需要一分鐘。

5. 通知會出現在入口網站中，一旦建立資源。 按一下此通知，然後選取 [前往資源]。

6. 從 「 LUIS API 」 服務的 [快速啟動] 頁面，瀏覽至第一個步驟，取得您的 「 金鑰 」，並按一下 [金鑰] （您也可以達到這按一下藍色的超連結"索引鍵，"如下圖所示）。 這將顯示您的服務，[金鑰]。 因此您可以稍後在應用程式中使用它，請儲存其中一個金鑰的副本。

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. 在 [快速啟動] 頁面的下一節 2b，按一下"Language Understanding 入口網站 」 （如圖所示），重新導向至用來建立新的服務，LUIS 應用程式中的網頁。

> 注意：達到 「 Language Understanding 入口網站 」 時，您可能需要登入，如果您還沒有，與您的 Azure 入口網站相同的認證。 如果這是您第一次使用 LUIS，您必須捲動到底部的 歡迎 頁面來尋找並按一下 「 建立 LUIS 」 應用程式 按鈕。

8. 登入之後，按一下 [我的應用程式] （如果您目前不是在該區段中）。 您可以按一下在 建立新的應用程式。 將新的應用程式命名為 「 語音 SDK 學習模組 」。 加入 [描述] 欄位，以及 「 語音 SDK 學習模組 」。 然後按一下 [完成]。

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> 注意：如果您的應用程式應該了解不同於英語的語言，您應該將"Culture"變更為適當的語言。

9. 按一下位於右上方 「 建置 」。

10. 在左側的應用程式資產下, 選取 「 意圖 」，然後按一下 「 建立新的意圖 」 並將它命名"PressButton。 」 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> 注意： 務必要使用的意圖和實體用於本教學課程中，因為 Lunarcom 應用程式將會參考它們的名稱，即可依名稱。  其他的專案，命名慣例可以您選擇的任何內容。 
>
> 注意： 您現在應該有 2 個意圖-「 PressButton"和"None"。

11. 在左側的應用程式資產下, 選取 「 實體 」 並按一下 「 建立新的實體 」 和 「 動作 」 將它命名，讓實體類型為 「 簡單 」。

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. 再按一次 「 建立新的實體 」 和其命名為 「 目標 」，以及保留為 「 簡單 」 的實體類型。

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. 在左側的應用程式資產下, 選取 「 意圖 」 然後按一下您在步驟 10 中建立您 「 PressButton"意圖。

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. 按一下右邊的 [檢視選項] 下拉式清單，然後選取 [顯示] 實體的值。 

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)按一下 輸入範例...」 文字方塊中。 然後，輸入下列的表達方式： 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. 按一下右邊的 [檢視選項] 下拉式清單，然後選取 [顯示] 實體名稱。

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. 請確認每 10 個談話 1 在下列位置中有下列的實體標籤。)按一下上的文字會誤標，然後在快顯視窗，選取 [移除標籤] 和 2。）按一下上應該有標示的文字，然後在快顯視窗，選取適當的標籤。

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. 現在，如果要發佈模型，請按一下右上方的 「 定型 」。 然後完成處理後，按一下右上方的 ["Test"]。

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. 在中輸入 「 選取 [啟動] 按鈕 」 的文字方塊中。

> 注意： 我們並未新增 「 選取 」 做為動作在任何我們談話-，但如果您按一下 「 檢查 」，此模型視為 「 選取 」 動作實體。
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. 現在，按一下右上方的 [發佈]。 確定 下拉式清單中顯示 「 生產 」，然後按一下 發佈，在快顯視窗以及。 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. 發行之後，綠色列應該會出現在頁面頂端。  按一下即可前往 [管理] 頁面上的綠色列。 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. 按一下左側 [金鑰和端點] 下 [應用程式設定]。 然後，將下拉式清單 [發行至] 設為 「 生產 」。 設定時區-以符合您，並核取方塊以包含所有預測的意圖分數。 最後，按一下 「 指派資源 」。

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. 從第一個下拉式清單中，選取租用戶，然後選取 「 隨用隨付 」 訂用帳戶名稱的下拉式清單中。 LUIS 資源名稱，請在 選擇上述步驟 1-5 中建立的資源。 然後，按一下 「 指派資源 」。 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> 注意： 請務必複製並儲存，我們只會指派，以便輕鬆存取以供下一節中的資源相關聯的端點 URL。
>
> 注意： 針對租用戶名稱，將您的公司或您建立此應用程式設定檔。

23. 現在，在 Unity 中開啟新的應用程式，並選取 Lunarcom_Base 物件階層架構中。 在 [偵測器] 面板中按一下 [新增元件] 然後搜尋並選取 「 LunarcomIntentRecognizer。 」

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. Luis 端點在欄位中 「 LunarcomIntentRecognizer 「 偵測器 面板中，輸入您在步驟 22 儲存端點 URL。 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  注意："LunarcomOfflineRecognizer 」 元件中在偵測器窗格中，請確定已為"SimulateOfflineMode 「 否則選取 [停用] 時，測試計劃將無法運作。 

25. 在 Unity 編輯器中按下 [播放] 按鈕，然後按一下 [rocket] 按鈕，啟動意圖辨識。 岳母片語 「 選取啟動 rocket 按鈕。 」

>  注意：應用程式識別所需的函式，並啟動 rocket 按鈕。
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a>恭喜！

正式，您了解如何從語音 SDK 程式新增語音命令 ！ 現在您的程式可以辨識語音命令的各種變體。 測試它，並擁有一些有趣 ！

[下一課：語音 SDK 第 5 課](placeholderlink)

