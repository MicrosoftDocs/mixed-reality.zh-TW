---
title: Azure 語音服務教學課程 - 4。 設定意圖和自然語言理解
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 語音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 8cebe1fb203aeed9a262a2e9f482993b4775e0a6
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303659"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a>4.設定意圖和自然語言理解

在本教學課程中，您將探索 Azure 語音服務的意圖辨識。 意圖辨識可讓您使用 AI 驅動的語音命令來裝備我們的應用程式，使用者可以說出非特定的語音命令，但系統仍可了解其意圖。

## <a name="objectives"></a>目標

* 了解如何在 LUIS 入口網站中設定意圖、實體和語句
* 了解如何在我們的應用程式中實作意圖和自然語言理解

## <a name="preparing-the-scene"></a>準備場景

在 [階層] 視窗中選取 **Lunarcom** 物件，然後在 [偵測器] 視窗中使用 [新增元件]  按鈕來將 **Lunarcom Intent Recognizer (指令碼)** 元件新增至 Lunarcom 物件：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-1.png)

在 [專案] 視窗中，瀏覽至 [資產]   > [MRTK.Tutorials.GettingStarted]   > [Prefabs]   > [RocketLauncher]  資料夾，將 **RocketLauncher_Complete** Prefab 拖曳到您的 [階層] 視窗中，並將其放在相機前方的適當位置，例如：

* 變形**位置** X = 0、Y = -0.4、Z = 1
* 變形**旋轉** X = 0、Y = 90、Z = 0

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-2.png)

在 [階層] 視窗中，再次選取 [Lunarcom]  物件，然後展開 [RocketLauncher_Complete]   > [按鈕]  物件，並將每個**按鈕**物件的子物件指派至對應的 [月球發射器按鈕]  欄位：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-3.png)

## <a name="creating-the-azure-language-understanding-resource"></a>建立 Azure Language Understanding 資源

在本節中，您將為下一節要建立的 Language Understanding Intelligent Service (LUIS) 應用程式建立 Azure 預測資源。

登入 <a href="https://portal.azure.com" target="_blank">Azure</a>，然後按一下 [建立資源]  。 然後搜尋並選取 **Language Understanding**：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-1.png)

按一下 [建立]  按鈕，以建立此服務的執行個體：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-2.png)

在 [建立] 頁面上，按一下 [預測]  選項，並輸入下列值：

* 針對**訂用帳戶**，如果您有試用版訂用帳戶，請選取 [免費試用]  ，否則請選取其他訂用帳戶的其中一個
* 在 [資源群組]  中，按一下 [新建]  連結並輸入適當名稱 (例如 MRKT-Tutorials)  ，然後按一下 [確定] 

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-3.png)

> [!NOTE]
> 從撰寫本文的時間起，您不需要建立撰寫資源，因為當您在下一節中建立 Language Understanding Intelligent Service (LUIS) 時，系統會在 LUIS 內自動產生撰寫試用版金鑰。

> [!TIP]
> 如果您的 Azure 帳戶中已有另一個適當的資源群組 (例如，您已完成 [Azure Spatial Anchors](mr-learning-asa-01.md) 教學課程)，您就可以使用此資源群組，而不用建立新的資源群組。

繼續在 [建立] 頁面上輸入下列值：

* 針對 [名稱]  ，請為服務輸入適當的名稱，例如 MRTK-Tutorials-AzureSpeechServices 
* 針對 [預測位置]  ，請選擇接近應用程式使用者實體位置的位置，例如 [(美國) 美國西部] 
* 針對 [預測定價層]  ，基於本教學課程的目的，請選取 [F0 (每秒 5 個呼叫，每月 10K 個呼叫)] 

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-4.png)

接下來，移至 [檢閱 + 建立]  索引標籤，檢閱詳細資料後按一下頁面底部的 [建立]  按鈕，即可建立資源及新的資源群組 (如果您已設定要建立新的資源群組)：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-5.png)

> [!NOTE]
> 按一下 [建立] 按鈕之後，您必須等候服務建立，這可能需要幾分鐘的時間。

資源建立程序完成後，您會看到**部署已完成**的訊息：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-6.png)

## <a name="creating-the-language-understanding-intelligent-service-luis"></a>建立 Language Understanding Intelligent Service (LUIS)

在本節中，您將建立 LUIS 應用程式、設定和訓練其預測模型，並將其連線至您在上一個步驟中建立的 Azure 預測資源。

具體而言，您將建立一個意圖，如果使用者說出應該採取的動作，則應用程式將會根據使用者所參考的按鈕，從場景中的三個紅色按鈕之一觸發 Interactable.OnClick() 事件。

例如，如果使用者說 "go ahead and launch the rocket" (繼續並發射火箭)  ，應用程式會預測 **go ahead** 代表應採取一些**動作**，以及預測**目標**的 Interactable.OnClick() 事件位於**啟動**按鈕上。

達成此動作所需採取的主要步驟如下：

1. 建立 LUIS 應用程式
2. 建立意圖
3. 建立範例語句
4. 建立實體
5. 將實體指派給範例語句
6. 訓練、測試及發佈應用程式
7. 將 Azure 預測資源指派給應用程式

### <a name="1-create-a-luis-app"></a>1.建立 LUIS 應用程式

使用您在上一節中建立 Azure 資源時所使用的相同使用者帳戶登入 <a href="https://www.luis.ai" target="_blank">LUIS</a>，選取您的國家/地區並同意使用條款。 在下一個步驟中，當系統要求您**連結您的 Azure 帳戶**時，請選擇 **繼續使用您的試用金鑰**，改為使用 Azure 撰寫資源。

> [!NOTE]
> 如果您已註冊 LUIS，而您的撰寫試用金鑰已過期，您可以參閱 [遷移至 Azure 資源撰寫金鑰](https://docs.microsoft.com/azure/cognitive-services/luis/luis-migration-authoring)文件，將您的 LUIS 撰寫資源切換為 Azure。

登入後，瀏覽至 [我的應用程式]  頁面，然後按一下 [建立新的應用程式]  ，然後在 [建立新的應用程式]  快顯視窗中輸入下列值：

* 針對 [名稱]  ，請輸入適當的名稱，例如 MRTK Tutorials - AzureSpeechServices 
* 針對 [文化特性]  ，請選取 [英文] 
* 針對 [描述]  ，您可以選擇性地輸入適當描述

然後按一下 [完成]  按鈕來建立新的應用程式：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-1.png)

建立新的應用程式之後，您會進入該應用程式的**儀表板**頁面：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-2.png)

### <a name="2-create-intents"></a>2.建立意圖

從儀表板頁面瀏覽至 [組建] > [應用程式資產] > [意圖]  頁面，按一下 [建立新意圖]  ，然後在 [建立新意圖]  快顯視窗中輸入下列值：

* 針對 [意圖名稱]  ，請輸入 **PressButton**

然後按一下 [完成]  按鈕來建立新的意圖：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-1.png)

> [!CAUTION]
> 基於本教學課程的目的，您的 Unity 專案會依據名稱來參考此意圖，亦即：'PressButton'。 因此，請務必將您的意圖命名為完全相同的名稱。

建立新的意圖之後，您會進入該意圖的頁面：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-2.png)

### <a name="3-create-example-utterances"></a>3.建立範例語句

前往 **PressButton** 意圖的**範例語句**清單，並新增下列範例語句：

* activate launch sequence (啟動發射順序)
* show me a placement hint (顯示位置提示)
* initiate the launch sequence (起始發射順序)
* press placement hints button (按下位置提示按鈕)
* give me a hint (給我一個提示)
* push the launch button (按下啟動按鈕)
* i need a hint (我需要提示)
* press the reset button (按下重設按鈕)
* time to reset the experience (重設體驗的時機)
* go ahead and launch the rocket (繼續並發射火箭)

新增所有範例語句之後，您的 PressButton 意圖頁面看起來應該像這樣：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step3-1.png)

> [!CAUTION]
> 基於本教學課程的目的，您的 Unity 專案會參考以下單字：'hint' (提示)、'hints' (提示)、'reset' (重設) 和 'launch' (發射)。 因此，請務必以完全相同的方式來拼寫這些單字。

### <a name="4-create-entities"></a>4.建立實體

從 PressButton 意圖頁面瀏覽至 [組建] > [應用程式資產] > [實體]  頁面，按一下 [建立新實體]  ，然後在 [建立新實體]  快顯視窗中輸入下列值：

* 在 [實體名稱]  中，輸入**動作**
* 針對 [實體類型]  ，請選取 [簡單] 

然後按一下 [完成]  按鈕來建立新的實體：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-1.png)

**重複**上一個步驟來建立名為**目標**的另一個實體，因此您有名為「動作」和「目標」的兩個實體：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-2.png)

> [!CAUTION]
> 基於本教學課程的目的，您的 Unity 專案會依據名稱來參考這些實體，亦即：「動作」與「目標」。 因此，請務必將您的實體命名為完全相同的名稱。

### <a name="5-assign-entities-to-the-example-utterances"></a>5.將實體指派給範例語句

在 [實體] 頁面上，瀏覽回到 **PressButton** 意圖頁面。

回到 PressButton 意圖頁面之後，按一下單字 **go**，然後再按一下單字 **ahead**，接著從內容快顯功能表中選取 [動作 (簡單)]  ，將 **go ahead** 標示為**動作**實體值：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-1.png)

**go ahead** 片語現在已定義為**動作**實體值。 如果您將滑鼠游標暫留在動作實體名稱上方，您可以看到相關的動作實體值：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-2.png)

> [!NOTE]
> 上圖中顯示在標籤底下的紅線表示尚未對實體值進行預測，當您在下一節中訓練模型時，此問題就會解決。

接下來，按一下單字 **launch**，然後從內容快顯功能表中選取 [目標 (簡單)]  ，將  標記為**目標**實體值：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-3.png)

單字 **launch**現在已定義為**目標**實體值。 如果您將滑鼠游標暫留在目標實體名稱上方，您可以看到相關的目標實體值：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-4.png)

PressButton 意圖範例語句 'go ahead and launch the rocket' 現在已設定為可進行預測，如下所示：

* 意圖：PressButton
* 動作實體：go ahead
* 目標實體：launch

**重複**前兩個步驟的程序，將動作和目標實體標籤指派給每一個範例語句，請記住，下列單字應該標示為**目標**實體：

* **hint** (以 Unity 專案中的 HintsButton 為目標)
* **hints** (以 Unity 專案中的 HintsButton 目標)
* **reset** (以 Unity 專案中的 ResetButton 為目標)
* **launch** (以 Unity 專案中的 LaunchButton 為目標)

標記所有範例語句之後，您的 PressButton 意圖頁面看起來應該像這樣：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-5.png)

如需其他方法來再次檢查您是否已指派正確實體，請按一下 [檢視選項]  功能表，並將此檢視切換為 [顯示實體值]  ：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-6.png)

現在，當檢視設定為顯示實體值時，您可以將滑鼠游標停留在加上標籤的單字和片語上，以快速驗證指派的實體名稱：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-7.png)

### <a name="6-train-test-and-publish-the-app"></a>6.訓練、測試及發佈應用程式

若要訓練應用程式，請按一下 [訓練]  按鈕，並等候訓練程序完成：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-1.png)

> [!NOTE]
> 如您在上圖中所見，所有標籤底下的紅線都已移除，這表示我們已對所有實體值進行預測。 另請注意，[訓練] 按鈕左邊的狀態圖示已從紅色變更為綠色。

當訓練程序完成時，請按一下 [測試]  按鈕，然後輸入 **go ahead and launch the rocket** 並按下 Enter 鍵：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-2.png)

測試語句處理完成後，請按一下 [檢查]  來查看測試結果：

* 意圖：PressButton (98.5% 的確定性)
* 動作實體：go ahead
* 目標實體：launch

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-3.png)

若要發佈應用程式，請按一下右上方的 [發佈]  按鈕，然後在 [選擇發佈位置和設定]  快顯視窗中選取 [生產]  ，然後按一下 [發佈]  按鈕：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-4.png)

等待發佈程序完成：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-5.png)

### <a name="7-assign-an-azure-prediction-resource-to-the-app"></a>7.將 Azure 預測資源指派給應用程式

瀏覽至 [管理] > [應用程式設定] > [Azure 資源]  頁面：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-1.png)

在 Azure 資源頁面上，按一下 [新增預測資源]  按鈕，然後在 [將資源指派給您的應用程式]  快顯視窗中選取下列值：

* 針對 [租用戶名稱]  ，請選取您的租用戶名稱
* 針對 [訂用帳戶名稱]  ，請選取您稍早[建立 Azure Language Understanding 資源](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)時使用的相同訂用帳戶
* 針對 [LUIS 資源名稱]  ，請選取您稍早[建立 Azure Language Understanding 資源時](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)建立的預測資源

然後按一下 [指派資源]  按鈕，將 Azure 預測資源指派給您的應用程式：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-2.png)

指派資源之後，您的 Azure 資源頁面看起來應該會像這樣：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-3.png)

## <a name="connecting-the-unity-project-to-the-luis-app"></a>將 Unity 專案連線至 LUIS 應用程式

在 [管理] > [應用程式設定] > [Azure 資源]  頁面上，按一下**複製**圖示來複製**查詢範例**：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-1.png)

回到 Unity 專案，在 [階層] 視窗中選取 **Lunarcom** 物件，然後在 [偵測器] 視窗中尋找 **Lunarcom Intent Recognizer (指令碼)** 元件並進行設定，如下所示：

* 在 [LUIS 端點]  欄位中，貼上您在上一個步驟中複製的**查詢範例**：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-2.png)

## <a name="testing-and-improving-the-intent-recognition"></a>測試和改善意圖辨識

若要直接在 Unity 編輯器中使用意圖辨識，您必須允許您的開發電腦使用聽寫。 若要確認此設定是否開啟，請開啟 Windows 的 [設定]  ，然後選擇 [隱私權]   > [語音]  ，並確定 [線上語音辨識]  已開啟：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-1.png)

如果您現在進入遊戲模式，您可以先按下火箭按鈕來測試意圖辨識。 然後，假設您的電腦有麥克風，當您說出第一個範例語句：**go ahead and launch the rocket**時，您就會看到 LunarModule 發射至太空中：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-2.png)

請嘗試所有**範例語句**，然後嘗試一些**有變化的範例語句**變體，以及幾個**隨機語句**。

接下來，返回 <a href="https://www.luis.ai" target="_blank">LUIS</a> 並瀏覽至 [組建] > [改善應用程式效能] >[檢閱端點語句]  頁面，使用**切換**按鈕從 [預設實體] 檢視切換至 [語彙基元檢視]  ，然檢閱語句：

* 在 [語句]  資料行中，視需要變更即移除指派的標籤，使其符合您的意圖
* 在 [符合的意圖]  資料行中，確認意圖是否正確
* 在 [新增/刪除]  資料行中，按一下綠色核取記號按鈕來新增語句，或按一下紅色 x 按鈕來將其刪除

當您依據需求檢閱多個語句之後，請按一下 [訓練]  按鈕來重新訓練模型，然後按一下 [發佈]  按鈕來重新發佈更新的應用程式：

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-3.png)

> [!NOTE]
> 如果端點語句未與 PressButton 意圖一致，但您希望模型知道語句沒有意圖，您可以將符合的意圖變更為 [無]。

您可以依據需求來多次**重覆**此程序，以達到改善應用程式模型的目的。

## <a name="congratulations"></a>恭喜！

您的專案現在已具備 AI 驅動的語音命令，可讓您的應用程式辨識使用者的意圖 (即使使用者沒有十分精確地傳達命令)。 在您的裝置上執行應用程式，以確保功能可正常運作。
