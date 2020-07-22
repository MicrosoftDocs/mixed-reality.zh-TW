---
title: Azure 雲端教學課程 - 5. 整合 Azure Bot 服務與 LUIS
description: 完成此課程，以了解如何在 HoloLens 2 應用程式中實作 Azure Bot 服務和自然語言理解。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, hololens 2, azure bot 服務, luis, 自然語言, 對話 bot
ms.localizationpriority: high
ms.openlocfilehash: e3a64488b1d6d22ac52f798fe90356ce8e995e26
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304709"
---
# <a name="5-integrating-azure-bot-service"></a>5.整合 Azure Bot 服務

在本教學課程中，您將了解如何在 **HoloLens 2** 示範應用程式中使用 **Azure Bot 服務**新增 Language Understanding (LUIS)，並在使用者搜尋**追蹤物件**時讓 Bot 協助使用者。 這是兩個部分的教學課程，在第一個部分中，您會使用 [Bot 編輯器](https://docs.microsoft.com/composer/introduction) 作為程式碼免費解決方案來建立 Bot，並快速查看 Azure 函式，以將所需的資料餵給 Bot。 在第二個部分中，您會使用 Unity 專案中的 **BotManager (指令碼)** 來取用託管的 Bot 服務。

## <a name="objectives"></a>目標

## <a name="part-1"></a>第 1 部分

* 了解 Azure Bot 服務的基本概念
* 了解如何使用 Bot 編輯器來建立 Bot
* 了解如何使用 Azure 函式來提供 Azure 儲存體的資料

## <a name="part-2"></a>第 2 部分

* 了解如何設定場景，以在此專案中使用 Azure Bot 服務
* 了解如何透過與 Bot 交談來設定和尋找物件

## <a name="understanding-azure-bot-service"></a>了解 Azure Bot 服務

**Azure Bot 服務**運用 **LUIS**，讓開發人員能夠建立智慧型 Bot 並與使用者保持自然交談。 交談式 Bot 是促進使用者與您的應用程式互動的絕佳方式。 Bot 可以使用 [QnA 標記](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs)作為知識庫， 以 [Language Understanding (LUIS)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp) 的功能來維持複雜的交談。

深入了解 [Azure Bot 服務](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0)。

## <a name="part-1---creating-the-bot"></a>第 1 部分 - 建立 Bot

在 Unity 應用程式中使用 Bot 之前，您必須先開發、提供資料，並將其裝載在 **Azure** 上。
Bot 的目標是要能夠分辨儲存在資料庫中的「追蹤物件」數目、依名稱尋找「追蹤物件」，以及告訴使用者一些相關的基本資訊。

### <a name="a-quick-look-into-tracked-objects-azure-function"></a>快速了解追蹤物件 Azure 函式

您即將開始建立 Bot，但為了方便使用，您必須提供可從中提取資料的資源。 由於 Bot 能夠計算**追蹤物件**數量，並依名稱尋找特定物件及提供詳細資料，您可以使用可存取 **Azure 表格儲存體**的簡單 Azure 函式。

下載 Azure Function 專案：[追蹤物件 Azure 函式](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/AzureFunction_TrackedObjectsService.zip)

此 Azure 函式有兩個動作，分別是 **Count** 和 **Find**，這兩者可透過基本的 HTTP GET 叫用。 您可以在 **Visual Studio** 中檢查程式碼。

深入了解 [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview)。

**Count** 函式會從表格的**表格儲存體** 查詢所有 **TrackedObjects**，非常簡單。 另一方面，**Find** 函式會從 GET 要求取得「名稱」查詢參數，並查詢**表格儲存體**以取得相符的 **TrackedObject** 並傳回 DTO 作為 JSON。

您可以直接從 **Visual Studio** 部署 **Azure 函式**。
在這裡尋找關於 [Azure 函式部署](https://docs.microsoft.com/azure/devops/pipelines/targets/azure-functions?view=azure-devops&tabs=dotnet-core%2Cyaml)的所有資訊。

完成部署之後，在 **Azure 入口網站**中開啟對應的資源，然後按一下「設定」區段下的 [組態]。 在**應用程式設定**中， 您需要提供儲存**追蹤物件**之 **Azure 儲存體**的「連接字串」。 按一下 [新增應用程式設定]，名稱請使用：**AzureStorageConnectionString**，並提供正確的「連接字串」。 之後，請按一下 [儲存]，**Azure 函式**已準備好裝載您接下來會建立的 Bot。

### <a name="creating-a-conversation-bot"></a>建立交談 Bot

有數種方式可開發以 Bot Framework 為基礎的對話式 Bot。 在本課程中，您將使用 [Bot Framework 編輯器](https://docs.microsoft.com/composer/) 桌面應用程式，這是一個適合快速開發的視覺化設計工具。

您可以從 [Github 存放庫](https://github.com/microsoft/BotFramework-Composer/releases)下載最新版本。 適用於 Windows、Mac 和 Linux。

安裝 **Bot Framework 編輯器**後，請啟動應用程式，您應該會看到此介面：

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-1.png)

您已備妥 Bot 編輯器專案，以提供本教學課程所需的對話和觸發程式。
下載專案：[Bot Framework 編輯器專案](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/BotComposerProject_TrackedObjectsBot.zip)

在頂端列上，按一下 [開啟]，然後選取您已下載的 Bot Framework 專案，其名稱為 **TrackedObjectsBot**。 專案完全載入之後，您應該會看到專案已就緒。

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-2.png)

讓我們將焦點放在左側，您可以在這裡看到**對話面板**。 在這裡有一個名為 **TrackedObjectsBot** 的對話，其下有數個**觸發程式**。

深入了解 [Bot Framework 概念](https://docs.microsoft.com/composer/concept-dialog)。

這些觸發程式會執行下列動作：

#### <a name="greeting"></a>問候

這是在「使用者」起始交談時，聊天 Bot 的進入點。

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-3.png)

#### <a name="askingforcount"></a>AskingForCount

當「使用者」要求計算所有**追蹤物件**時，就會觸發此對話。
這些是觸發程式片語：

>* 幫我全部計算 (count me all)
>* 儲存的數目有多少 (how many are stored)

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-4.png)

[LUIS](https://docs.microsoft.com/composer/how-to-use-luis) 讓「使用者」不需要一字不漏地說出某個詞組，而是允許「使用者」自然交談。

在此對話中，Bot 也會與 Azure 函式 **Count** 溝通，稍後會詳細說明。

#### <a name="unknown-intent"></a>不明意圖

如果「使用者」 的輸入不符合任何其他觸發程式條件，就會觸發此對話，請使用者再次陳述問題。

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-5.png)

#### <a name="findentity"></a>FindEntity

由於要分支和存放 Bot 記憶體中的資料，最後一個對話會更複雜。
Bot 會要求使用者提供**追蹤物件**的「名稱」以了解更詳細的資訊，並執行 **Find** Azure 函式查詢，然後使用回應來繼續交談。

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-6.png)

如果找不到**追蹤物件**，就會通知使用者並結束交談。 找到目標的**追蹤物件**時，Bot 會檢查有哪些可用的屬性並加以報告。

### <a name="adapting-the-bot"></a>調整 Bot

**AskingForCount** 和 **FindEntity** 觸發程式必須與後端交談，這表示您必須新增先前部署之 **Azure 函式**的正確 URL。

在對話面板上，按一下 [AskingForCount] 並尋找「傳送 HTTP 要求」動作，您可以在這裡看到欄位 **URL**，您需要變更 **Count** 函式端點的正確 URL。

![mr-learning-azure](images/mr-learning-azure/tutorial5-section5-step1-1.png)

最後，尋找 **FindEntity** 觸發程式，並找到「傳送 HTTP 要求」 動作，在 **URL** 欄位中將 URL 變更為 **Find** 函式端點。

![mr-learning-azure](images/mr-learning-azure/tutorial5-section5-step1-2.png)

一切都設定好之後，您就可以開始部署 Bot 了。 由於您已安裝 Bot Framework 編輯器，因此可以直接從該處發佈。

深入了解 [從 Bot 編輯器發佈 Bot](https://docs.microsoft.com/composer/how-to-publish-bot)。

> [!TIP]
> 您可以自由運用 Bot，例如新增更多觸發程式片語、新的回應或交談分支。

## <a name="part-2---putting-everything-together-in-unity"></a>第 2 部分 - 將所有專案放在 Unity 中

### <a name="preparing-the-scene"></a>準備場景

在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.AzureCloudServices] > [預製物件] > [管理員] 資料夾。

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-1.png)

從該處將預製物件 **ChatBotManager** 移到場景階層中。

將 ChatBotManager 新增至場景之後，請按一下 [聊天 Bot 管理員] 元件。
在偵測器中，您會看到需要填寫的空白 **Direct Line 祕密**欄位。

> [!TIP]
> 您可以在本教學課程的第一個部分中，尋找 **Bot 通道註冊** 類型的資源，以從 Azure 入口網站擷取「祕密金鑰」。

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-2.png)

現在請將 **ChatBotManager** 物件與附加至 **ChatBotPanel** 物件的 **ChatBotController** 元件連線。 在階層中選取 **ChatBotPanel**，您會看到空白的 **聊天 Bot 管理員**欄位，請從階層中將 **ChatBotManager** 物件拖曳到空白的 **聊天 Bot 管理員** 欄位中。

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-3.png)

接下來，您需要一種方法來開啟 **ChatBotPanel**，讓使用者可以與之互動。 從場景視窗中，您可能已注意到 **MainMenu** 物件上出現「聊天 Bot」側邊按鈕可用來解決此問題。

在階層中，尋找 **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot**，並在偵測器中尋找 ButtonConfigHelper 指令碼。 在該處，您會在 **OnClick()** 事件回呼上看到空位。 將 **ChatBotPanel** 拖放到事件位置，從下拉式清單中瀏覽 GameObject，然後在子功能表 *SetActive (bool)* 中選取並啟用核取方塊。

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-4.png)

現在，您可以從主功能表中啟動聊天 Bot，並將場景備妥以供使用。

### <a name="putting-the-bot-to-a-test"></a>測試您的 Bot

#### <a name="asking-about-the-quantity-of-tracked-objects"></a>詢問追蹤物件的數量

首先詢問 Bot 儲存在資料庫中的**追蹤物件**數目。

> [!NOTE]
> 這次您必須從 HoloLens 2 執行應用程式，因為您的系統可能無法使用「文字轉換語音」之類的服務。

在 HoloLens 2 上執行應用程式，然後按一下主功能表旁的「聊天機器人」按鈕。
Bot 會先問候您，現在您可以詢問**有多少物件？**
Bot 應該會告訴您數量並結束交談。

#### <a name="asking-about-a-tracked-object"></a>詢問追蹤物件的相關資訊

現在再次執行應用程式，這次詢問**尋找追蹤物件**，Bot 會詢問您應該以 "car" 回應的名稱，或是您知道存在於資料庫中之其他「追蹤物件」的名稱。 Bot 會告訴您例如說明等詳細資料，以及是否已指派空間錨點。

> [!TIP]
> 試著詢問不存在的**追蹤物件** 不存在，看看 Bot 會如何回應。

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已了解如何使用自然語言的交談，使用 Azure Bot Framework 來與應用程式互動。 您已了解如何開發自己的 Bot，以及要讓其順利執行的所有必要條件。

## <a name="conclusion"></a>結論

在此教學課程系列中，您已體驗到 **Azure 雲端服務**如何為您的應用程式帶來全新且令人興奮的功能。
您現在可以使用 **Azure 儲存體**，將資料和影像儲存在雲端中，使用 **Azure 自訂視覺** 來關聯和定型模型、將物件帶入具有 **Azure Spatial Anchors** 的本機內容，以及實作 **Azure Bot Framework (由 LUIS 提供技術支援)** ，以全新且自然的互動模式新增對話式 Bot。
