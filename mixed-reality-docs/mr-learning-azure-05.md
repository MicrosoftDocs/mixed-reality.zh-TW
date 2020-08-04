---
title: Azure 雲端教學課程 - 5. 整合 Azure Bot 服務與 LUIS
description: 完成此課程，以了解如何在 HoloLens 2 應用程式中實作 Azure Bot 服務和自然語言理解。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, hololens 2, azure bot 服務, luis, 自然語言, 對話 bot
ms.localizationpriority: high
ms.openlocfilehash: daf97cde1477a84c1776a069ec5b8d1a185b63cc
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376450"
---
# <a name="5-integrating-azure-bot-service"></a><span data-ttu-id="d2799-105">5.整合 Azure Bot 服務</span><span class="sxs-lookup"><span data-stu-id="d2799-105">5. Integrating Azure Bot Service</span></span>

<span data-ttu-id="d2799-106">在本教學課程中，您將了解如何在 **HoloLens 2** 示範應用程式中使用 **Azure Bot 服務**新增 Language Understanding (LUIS)，並在使用者搜尋**追蹤物件**時讓 Bot 協助使用者。</span><span class="sxs-lookup"><span data-stu-id="d2799-106">In this tutorial, you will learn how to use **Azure Bot Service** in the **HoloLens 2** demo application to add Language Understanding (LUIS) and letting the Bot assist the user when searching for **Tracked Objects**.</span></span> <span data-ttu-id="d2799-107">這是兩個部分的教學課程，在第一個部分中，您會使用 [Bot 編輯器](https://docs.microsoft.com/composer/introduction) 作為程式碼免費解決方案來建立 Bot，並快速查看 Azure 函式，以將所需的資料餵給 Bot。</span><span class="sxs-lookup"><span data-stu-id="d2799-107">This is a two part tutorial where in the first part you create the Bot with the [Bot Composer](https://docs.microsoft.com/composer/introduction) as a code free solution and take a quick look in the Azure Function that feeds the Bot with the needed data.</span></span> <span data-ttu-id="d2799-108">在第二個部分中，您會使用 Unity 專案中的 **BotManager (指令碼)** 來取用託管的 Bot 服務。</span><span class="sxs-lookup"><span data-stu-id="d2799-108">In the second part you use the **BotManager (script)** in the Unity project to consume the hosted Bot Service.</span></span>

## <a name="objectives"></a><span data-ttu-id="d2799-109">目標</span><span class="sxs-lookup"><span data-stu-id="d2799-109">Objectives</span></span>

## <a name="part-1"></a><span data-ttu-id="d2799-110">第 1 部分</span><span class="sxs-lookup"><span data-stu-id="d2799-110">Part 1</span></span>

* <span data-ttu-id="d2799-111">了解 Azure Bot 服務的基本概念</span><span class="sxs-lookup"><span data-stu-id="d2799-111">Learn the basics about Azure Bot Service</span></span>
* <span data-ttu-id="d2799-112">了解如何使用 Bot 編輯器來建立 Bot</span><span class="sxs-lookup"><span data-stu-id="d2799-112">Learn how to use the Bot Composer to create a Bot</span></span>
* <span data-ttu-id="d2799-113">了解如何使用 Azure 函式來提供 Azure 儲存體的資料</span><span class="sxs-lookup"><span data-stu-id="d2799-113">Learn how to use an Azure Function to provide data from the Azure Storage</span></span>

## <a name="part-2"></a><span data-ttu-id="d2799-114">第 2 部分</span><span class="sxs-lookup"><span data-stu-id="d2799-114">Part 2</span></span>

* <span data-ttu-id="d2799-115">了解如何設定場景，以在此專案中使用 Azure Bot 服務</span><span class="sxs-lookup"><span data-stu-id="d2799-115">Learn how to setup the scene to use Azure Bot Service in this project</span></span>
* <span data-ttu-id="d2799-116">了解如何透過與 Bot 交談來設定和尋找物件</span><span class="sxs-lookup"><span data-stu-id="d2799-116">Learn how to set and find objects via conversing with the Bot</span></span>

## <a name="understanding-azure-bot-service"></a><span data-ttu-id="d2799-117">了解 Azure Bot 服務</span><span class="sxs-lookup"><span data-stu-id="d2799-117">Understanding Azure Bot Service</span></span>

<span data-ttu-id="d2799-118">**Azure Bot 服務**運用 **LUIS**，讓開發人員能夠建立智慧型 Bot 並與使用者保持自然交談。</span><span class="sxs-lookup"><span data-stu-id="d2799-118">The **Azure Bot Service** empowers developers to create intelligent bots that can maintain natural conversation with users thanks to **LUIS**.</span></span> <span data-ttu-id="d2799-119">交談式 Bot 是促進使用者與您的應用程式互動的絕佳方式。</span><span class="sxs-lookup"><span data-stu-id="d2799-119">A conversational Bot is a great way to expand the ways a user can interact with your application.</span></span> <span data-ttu-id="d2799-120">Bot 可以使用 [QnA 標記](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs)作為知識庫， 以 [Language Understanding (LUIS)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp) 的功能來維持複雜的交談。</span><span class="sxs-lookup"><span data-stu-id="d2799-120">A Bot can act as a knowledge base with a [QnA Marker](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs) to maintaining sophisticated conversation with the power of [Language Understanding (LUIS)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp).</span></span>

<span data-ttu-id="d2799-121">深入了解 [Azure Bot 服務](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0)。</span><span class="sxs-lookup"><span data-stu-id="d2799-121">Learn more about [Azure Bot Service](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0).</span></span>

## <a name="part-1---creating-the-bot"></a><span data-ttu-id="d2799-122">第 1 部分 - 建立 Bot</span><span class="sxs-lookup"><span data-stu-id="d2799-122">Part 1 - Creating the Bot</span></span>

<span data-ttu-id="d2799-123">在 Unity 應用程式中使用 Bot 之前，您必須先開發、提供資料，並將其裝載在 **Azure** 上。</span><span class="sxs-lookup"><span data-stu-id="d2799-123">Before you can use the bot in the Unity application, you need to develope it, provide it with data and host it on **Azure**.</span></span>
<span data-ttu-id="d2799-124">Bot 的目標是要能夠分辨儲存在資料庫中的「追蹤物件」數目、依名稱尋找「追蹤物件」，以及告訴使用者一些相關的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="d2799-124">The goal of the bot is to have the abilities to tell how many *Tracked Objects* are stored in the database, find a *Tracked Object* by its name, and tell the user some basic information about it.</span></span>

### <a name="a-quick-look-into-tracked-objects-azure-function"></a><span data-ttu-id="d2799-125">快速了解追蹤物件 Azure 函式</span><span class="sxs-lookup"><span data-stu-id="d2799-125">A quick look into Tracked Objects Azure Function</span></span>

<span data-ttu-id="d2799-126">您即將開始建立 Bot，但為了方便使用，您必須提供可從中提取資料的資源。</span><span class="sxs-lookup"><span data-stu-id="d2799-126">You are about to start creating the Bot, but to make it useful you need to give it a resource from which it can pull data.</span></span> <span data-ttu-id="d2799-127">由於 Bot 能夠計算**追蹤物件**數量，並依名稱尋找特定物件及提供詳細資料，您可以使用可存取 **Azure 表格儲存體**的簡單 Azure 函式。</span><span class="sxs-lookup"><span data-stu-id="d2799-127">Since the *Bot* will be able to count the amount of **Tracked Objects**, find specific ones by name and tell details, you will use a simple Azure Function that has access to the **Azure Table storage**.</span></span>

<span data-ttu-id="d2799-128">下載 Azure Function 專案：[追蹤物件 Azure 函式](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/AzureFunction_TrackedObjectsService.zip)</span><span class="sxs-lookup"><span data-stu-id="d2799-128">Download the Azure Function Project: [Tracked Objects Azure Function](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/AzureFunction_TrackedObjectsService.zip)</span></span>

<span data-ttu-id="d2799-129">此 Azure 函式有兩個動作，分別是 **Count** 和 **Find**，這兩者可透過基本的 HTTP GET 叫用。</span><span class="sxs-lookup"><span data-stu-id="d2799-129">This Azure Function has two actions, **Count** and **Find** which can be invoked via basic *HTTP* *GET* calls.</span></span> <span data-ttu-id="d2799-130">您可以在 **Visual Studio** 中檢查程式碼。</span><span class="sxs-lookup"><span data-stu-id="d2799-130">You can inspect the code in **Visual Studio**.</span></span>

<span data-ttu-id="d2799-131">深入了解 [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview)。</span><span class="sxs-lookup"><span data-stu-id="d2799-131">Learn more about [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="d2799-132">**Count** 函式會從表格的**表格儲存體** 查詢所有 **TrackedObjects**，非常簡單。</span><span class="sxs-lookup"><span data-stu-id="d2799-132">The **Count** function queries from the **Table storage** all **TrackedObjects** from the table, very simple.</span></span> <span data-ttu-id="d2799-133">另一方面，**Find** 函式會從 GET 要求取得「名稱」查詢參數，並查詢**表格儲存體**以取得相符的 **TrackedObject** 並傳回 DTO 作為 JSON。</span><span class="sxs-lookup"><span data-stu-id="d2799-133">On the other hand the **Find** function takes a *name* query parameter from the *GET* request and queries the **Table storage** for a matching **TrackedObject** and returns a DTO as JSON.</span></span>

<span data-ttu-id="d2799-134">您可以直接從 **Visual Studio** 部署 **Azure 函式**。</span><span class="sxs-lookup"><span data-stu-id="d2799-134">You can deploy this **Azure Function** directly from **Visual Studio**.</span></span>
<span data-ttu-id="d2799-135">在這裡尋找關於 [Azure 函式部署](https://docs.microsoft.com/azure/devops/pipelines/targets/azure-functions?view=azure-devops&tabs=dotnet-core%2Cyaml)的所有資訊。</span><span class="sxs-lookup"><span data-stu-id="d2799-135">Find here all information regarding [Azure Function deployment](https://docs.microsoft.com/azure/devops/pipelines/targets/azure-functions?view=azure-devops&tabs=dotnet-core%2Cyaml).</span></span>

<span data-ttu-id="d2799-136">完成部署之後，在 **Azure 入口網站**中開啟對應的資源，然後按一下「設定」區段下的 [組態]。</span><span class="sxs-lookup"><span data-stu-id="d2799-136">Once you have completed the deployment, in the **Azure Portal**, open the corresponding resource and click on **Configuration** which is under the *Settings* section.</span></span> <span data-ttu-id="d2799-137">在**應用程式設定**中， 您需要提供儲存**追蹤物件**之 **Azure 儲存體**的「連接字串」。</span><span class="sxs-lookup"><span data-stu-id="d2799-137">There on **Application Settings** you need to provide the *Connection string* to the **Azure Storage** where the **Tracked Objects** are stored.</span></span> <span data-ttu-id="d2799-138">按一下 [新增應用程式設定]，名稱請使用：**AzureStorageConnectionString**，並提供正確的「連接字串」。</span><span class="sxs-lookup"><span data-stu-id="d2799-138">Click on **New Application setting** and use for name: **AzureStorageConnectionString** and for value provide the correct *Connection string*.</span></span> <span data-ttu-id="d2799-139">之後，請按一下 [儲存]，**Azure 函式**已準備好裝載您接下來會建立的 Bot。</span><span class="sxs-lookup"><span data-stu-id="d2799-139">After that click on **Save** and the **Azure Function** is ready to server the *Bot* which you will create next.</span></span>

### <a name="creating-a-conversation-bot"></a><span data-ttu-id="d2799-140">建立交談 Bot</span><span class="sxs-lookup"><span data-stu-id="d2799-140">Creating a conversation Bot</span></span>

<span data-ttu-id="d2799-141">有數種方式可開發以 Bot Framework 為基礎的對話式 Bot。</span><span class="sxs-lookup"><span data-stu-id="d2799-141">There are several ways to develope a Bot Framework based conversational bot.</span></span> <span data-ttu-id="d2799-142">在本課程中，您將使用 [Bot Framework 編輯器](https://docs.microsoft.com/composer/) 桌面應用程式，這是一個適合快速開發的視覺化設計工具。</span><span class="sxs-lookup"><span data-stu-id="d2799-142">In this lesson you will use the [Bot Framework Composer](https://docs.microsoft.com/composer/) desktop application which is a visual designer that is perfect for rapid development.</span></span>

<span data-ttu-id="d2799-143">您可以從 [Github 存放庫](https://github.com/microsoft/BotFramework-Composer/releases)下載最新版本。</span><span class="sxs-lookup"><span data-stu-id="d2799-143">You can download the latest releases from the [Github repository](https://github.com/microsoft/BotFramework-Composer/releases).</span></span> <span data-ttu-id="d2799-144">適用於 Windows、Mac 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="d2799-144">It is available for Windows, Mac, and Linux.</span></span>

<span data-ttu-id="d2799-145">安裝 **Bot Framework 編輯器**後，請啟動應用程式，您應該會看到此介面：</span><span class="sxs-lookup"><span data-stu-id="d2799-145">Once the **Bot Framework Composer** is installed, start the application and you should see this interface:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-1.png)

<span data-ttu-id="d2799-147">您已備妥 Bot 編輯器專案，以提供本教學課程所需的對話和觸發程式。</span><span class="sxs-lookup"><span data-stu-id="d2799-147">You have prepared a bot composer project which provides the needed dialogues and triggers for this tutorial.</span></span>
<span data-ttu-id="d2799-148">下載專案：[Bot Framework 編輯器專案](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/BotComposerProject_TrackedObjectsBot.zip)</span><span class="sxs-lookup"><span data-stu-id="d2799-148">Download the project: [Bot Framework Composer project](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/BotComposerProject_TrackedObjectsBot.zip)</span></span>

<span data-ttu-id="d2799-149">在頂端列上，按一下 [開啟]，然後選取您已下載的 Bot Framework 專案，其名稱為 **TrackedObjectsBot**。</span><span class="sxs-lookup"><span data-stu-id="d2799-149">On the top bar click on **Open** and select the Bot Framework project you have downloaded which is named **TrackedObjectsBot**.</span></span> <span data-ttu-id="d2799-150">專案完全載入之後，您應該會看到專案已就緒。</span><span class="sxs-lookup"><span data-stu-id="d2799-150">After the project is fully loaded, you should see the project ready.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-2.png)

<span data-ttu-id="d2799-152">讓我們將焦點放在左側，您可以在這裡看到**對話面板**。</span><span class="sxs-lookup"><span data-stu-id="d2799-152">Let's focus on the left side where you can see the **Dialogs Panel**.</span></span> <span data-ttu-id="d2799-153">在這裡有一個名為 **TrackedObjectsBot** 的對話，其下有數個**觸發程式**。</span><span class="sxs-lookup"><span data-stu-id="d2799-153">There you have one dialog named **TrackedObjectsBot** under which you can see several **Triggers**.</span></span>

<span data-ttu-id="d2799-154">深入了解 [Bot Framework 概念](https://docs.microsoft.com/composer/concept-dialog)。</span><span class="sxs-lookup"><span data-stu-id="d2799-154">Learn more about [Bot Framework concepts](https://docs.microsoft.com/composer/concept-dialog).</span></span>

<span data-ttu-id="d2799-155">這些觸發程式會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="d2799-155">These triggers do the following:</span></span>

#### <a name="greeting"></a><span data-ttu-id="d2799-156">問候</span><span class="sxs-lookup"><span data-stu-id="d2799-156">Greeting</span></span>

<span data-ttu-id="d2799-157">這是在「使用者」起始交談時，聊天 Bot 的進入點。</span><span class="sxs-lookup"><span data-stu-id="d2799-157">This is the entry point of the chat *bot* when ever a *user* initiates a conversation.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-3.png)

#### <a name="askingforcount"></a><span data-ttu-id="d2799-159">AskingForCount</span><span class="sxs-lookup"><span data-stu-id="d2799-159">AskingForCount</span></span>

<span data-ttu-id="d2799-160">當「使用者」要求計算所有**追蹤物件**時，就會觸發此對話。</span><span class="sxs-lookup"><span data-stu-id="d2799-160">This dialog is triggered when the *user* asks for counting all **Tracked Objects**.</span></span>
<span data-ttu-id="d2799-161">這些是觸發程式片語：</span><span class="sxs-lookup"><span data-stu-id="d2799-161">These are the trigger phrases:</span></span>

>* <span data-ttu-id="d2799-162">幫我全部計算 (count me all)</span><span class="sxs-lookup"><span data-stu-id="d2799-162">count me all</span></span>
>* <span data-ttu-id="d2799-163">儲存的數目有多少 (how many are stored)</span><span class="sxs-lookup"><span data-stu-id="d2799-163">how many are stored</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-4.png)

<span data-ttu-id="d2799-165">[LUIS](https://docs.microsoft.com/composer/how-to-use-luis) 讓「使用者」不需要一字不漏地說出某個詞組，而是允許「使用者」自然交談。</span><span class="sxs-lookup"><span data-stu-id="d2799-165">Thanks to [LUIS](https://docs.microsoft.com/composer/how-to-use-luis) the *user* does not have to ask the phrases in that exact way which allows a natural conversation for the *user*.</span></span>

<span data-ttu-id="d2799-166">在此對話中，Bot 也會與 Azure 函式 **Count** 溝通，稍後會詳細說明。</span><span class="sxs-lookup"><span data-stu-id="d2799-166">In this dialog the *bot* will also talk to the **Count** Azure Function, more about that later.</span></span>

#### <a name="unknown-intent"></a><span data-ttu-id="d2799-167">不明意圖</span><span class="sxs-lookup"><span data-stu-id="d2799-167">Unknown Intent</span></span>

<span data-ttu-id="d2799-168">如果「使用者」 的輸入不符合任何其他觸發程式條件，就會觸發此對話，請使用者再次陳述問題。</span><span class="sxs-lookup"><span data-stu-id="d2799-168">This dialogue is triggered if the input from the *user* does not fit any other trigger condition and responses the user with trying his question again.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-5.png)

#### <a name="findentity"></a><span data-ttu-id="d2799-170">FindEntity</span><span class="sxs-lookup"><span data-stu-id="d2799-170">FindEntity</span></span>

<span data-ttu-id="d2799-171">由於要分支和存放 Bot 記憶體中的資料，最後一個對話會更複雜。</span><span class="sxs-lookup"><span data-stu-id="d2799-171">The last dialogue is more complex with branching and storing data in the *bots* memory.</span></span>
<span data-ttu-id="d2799-172">Bot 會要求使用者提供**追蹤物件**的「名稱」以了解更詳細的資訊，並執行 **Find** Azure 函式查詢，然後使用回應來繼續交談。</span><span class="sxs-lookup"><span data-stu-id="d2799-172">It asks the user for the *name* of the **Tracked Object** it want's to know more information about, performs a query to the **Find** Azure Function, and uses the response to proceed with the conversation.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-6.png)

<span data-ttu-id="d2799-174">如果找不到**追蹤物件**，就會通知使用者並結束交談。</span><span class="sxs-lookup"><span data-stu-id="d2799-174">If the **Tracked Object** is not found, the user is informed and the conversation ends.</span></span> <span data-ttu-id="d2799-175">找到目標的**追蹤物件**時，Bot 會檢查有哪些可用的屬性並加以報告。</span><span class="sxs-lookup"><span data-stu-id="d2799-175">When the **Tracked Object** in question is found, the boot will check what properties are available and report on them.</span></span>

### <a name="adapting-the-bot"></a><span data-ttu-id="d2799-176">調整 Bot</span><span class="sxs-lookup"><span data-stu-id="d2799-176">Adapting the Bot</span></span>

<span data-ttu-id="d2799-177">**AskingForCount** 和 **FindEntity** 觸發程式必須與後端交談，這表示您必須新增先前部署之 **Azure 函式**的正確 URL。</span><span class="sxs-lookup"><span data-stu-id="d2799-177">The **AskingForCount** and **FindEntity** trigger need to talk to the backend, this means you have to add the correct URL of the **Azure Function** you deployed previously.</span></span>

<span data-ttu-id="d2799-178">在對話面板上，按一下 [AskingForCount] 並尋找「傳送 HTTP 要求」動作，您可以在這裡看到欄位 **URL**，您需要變更 **Count** 函式端點的正確 URL。</span><span class="sxs-lookup"><span data-stu-id="d2799-178">On the dialog panel click on **AskingForCount** and locate the *Send an HTTP request* action, here you can see the field **URL** which you need to change the correct URL for the **Count** function endpoint.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section5-step1-1.png)

<span data-ttu-id="d2799-180">最後，尋找 **FindEntity** 觸發程式，並找到「傳送 HTTP 要求」 動作，在 **URL** 欄位中將 URL 變更為 **Find** 函式端點。</span><span class="sxs-lookup"><span data-stu-id="d2799-180">Finally, look for the **FindEntity** trigger and locate the *Send an HTTP request* action, in the **URL** field change the URL to the **Find** function endpoint.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section5-step1-2.png)

<span data-ttu-id="d2799-182">一切都設定好之後，您就可以開始部署 Bot 了。</span><span class="sxs-lookup"><span data-stu-id="d2799-182">With everything set you are now ready to deploy the Bot.</span></span> <span data-ttu-id="d2799-183">由於您已安裝 Bot Framework 編輯器，因此可以直接從該處發佈。</span><span class="sxs-lookup"><span data-stu-id="d2799-183">Since you have Bot Framework composer installed, you can publish it directly from there.</span></span>

<span data-ttu-id="d2799-184">深入了解 [從 Bot 編輯器發佈 Bot](https://docs.microsoft.com/composer/how-to-publish-bot)。</span><span class="sxs-lookup"><span data-stu-id="d2799-184">Learn more about [Publish a bot from Bot Composer](https://docs.microsoft.com/composer/how-to-publish-bot).</span></span>

> [!TIP]
> <span data-ttu-id="d2799-185">您可以自由運用 Bot，例如新增更多觸發程式片語、新的回應或交談分支。</span><span class="sxs-lookup"><span data-stu-id="d2799-185">Feel free playing around with Bot by adding more trigger phrases, new responses or conversation branching.</span></span>

## <a name="part-2---putting-everything-together-in-unity"></a><span data-ttu-id="d2799-186">第 2 部分 - 將所有專案放在 Unity 中</span><span class="sxs-lookup"><span data-stu-id="d2799-186">Part 2 - Putting everything together in Unity</span></span>

### <a name="preparing-the-scene"></a><span data-ttu-id="d2799-187">準備場景</span><span class="sxs-lookup"><span data-stu-id="d2799-187">Preparing the scene</span></span>

<span data-ttu-id="d2799-188">在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.AzureCloudServices] > [預製物件] > [管理員] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="d2799-188">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-1.png)

<span data-ttu-id="d2799-190">從該處將預製物件 **ChatBotManager** 移到場景階層中。</span><span class="sxs-lookup"><span data-stu-id="d2799-190">From there move the prefab **ChatBotManager** into the scene Hierarchy.</span></span>

<span data-ttu-id="d2799-191">將 ChatBotManager 新增至場景之後，請按一下 [聊天 Bot 管理員] 元件。</span><span class="sxs-lookup"><span data-stu-id="d2799-191">Once you add the ChatBotManager to the scene, click on the **Chat Bot Manager** component.</span></span>
<span data-ttu-id="d2799-192">在偵測器中，您會看到需要填寫的空白 **Direct Line 祕密**欄位。</span><span class="sxs-lookup"><span data-stu-id="d2799-192">In the Inspector you will see that there is an empty **Direct Line Secret Key** field which you need to fill out.</span></span>

> [!TIP]
> <span data-ttu-id="d2799-193">您可以在本教學課程的第一個部分中，尋找 **Bot 通道註冊** 類型的資源，以從 Azure 入口網站擷取「祕密金鑰」。</span><span class="sxs-lookup"><span data-stu-id="d2799-193">You can retrieve the *secret key* from the Azure portal by looking for the resource of type **Bot Channels Registration** you have created in the first part of this tutorial.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-2.png)

<span data-ttu-id="d2799-195">現在請將 **ChatBotManager** 物件與附加至 **ChatBotPanel** 物件的 **ChatBotController** 元件連線。</span><span class="sxs-lookup"><span data-stu-id="d2799-195">Now you will connect the **ChatBotManager** object with the **ChatBotController** component that is attached to the **ChatBotPanel** object.</span></span> <span data-ttu-id="d2799-196">在階層中選取 **ChatBotPanel**，您會看到空白的 **聊天 Bot 管理員**欄位，請從階層中將 **ChatBotManager** 物件拖曳到空白的 **聊天 Bot 管理員** 欄位中。</span><span class="sxs-lookup"><span data-stu-id="d2799-196">In the Hierarchy select the **ChatBotPanel** and you will see an empty **Chat Bot Manager** field, drag from the Hierarchy the **ChatBotManager** object into the empty **Chat Bot Manager** field.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-3.png)

<span data-ttu-id="d2799-198">接下來，您需要一種方法來開啟 **ChatBotPanel**，讓使用者可以與之互動。</span><span class="sxs-lookup"><span data-stu-id="d2799-198">Next you need a way to open the **ChatBotPanel** so that the user can interact with it.</span></span> <span data-ttu-id="d2799-199">從場景視窗中，您可能已注意到 **MainMenu** 物件上出現「聊天 Bot」側邊按鈕可用來解決此問題。</span><span class="sxs-lookup"><span data-stu-id="d2799-199">From the Scene window you may have noticed that there is a *Chat Bot* side button on the **MainMenu** object, you will use it to solve this problem.</span></span>

<span data-ttu-id="d2799-200">在階層中，尋找 **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot**，並在偵測器中尋找 ButtonConfigHelper 指令碼。</span><span class="sxs-lookup"><span data-stu-id="d2799-200">In the Hierarchy locate **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot** and locate in the Inspector the *ButtonConfigHelper* script.</span></span> <span data-ttu-id="d2799-201">在該處，您會在 **OnClick()** 事件回呼上看到空位。</span><span class="sxs-lookup"><span data-stu-id="d2799-201">There you will see an empty slot on the **OnClick()** event callback.</span></span> <span data-ttu-id="d2799-202">將 **ChatBotPanel** 拖放到事件位置，從下拉式清單中瀏覽 GameObject，然後在子功能表 *SetActive (bool)* 中選取並啟用核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d2799-202">Drag and drop the **ChatBotPanel** to the event slot, from the dropdown list navigate *GameObject*, then select in the sub menu *SetActive (bool)* and enable the checkbox.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-4.png)

<span data-ttu-id="d2799-204">現在，您可以從主功能表中啟動聊天 Bot，並將場景備妥以供使用。</span><span class="sxs-lookup"><span data-stu-id="d2799-204">Now the chat bot can be stared from the main menu and with that the scene is ready for use.</span></span>

### <a name="putting-the-bot-to-a-test"></a><span data-ttu-id="d2799-205">測試您的 Bot</span><span class="sxs-lookup"><span data-stu-id="d2799-205">Putting the bot to a test</span></span>

#### <a name="asking-about-the-quantity-of-tracked-objects"></a><span data-ttu-id="d2799-206">詢問追蹤物件的數量</span><span class="sxs-lookup"><span data-stu-id="d2799-206">Asking about the quantity of tracked objects</span></span>

<span data-ttu-id="d2799-207">首先詢問 Bot 儲存在資料庫中的**追蹤物件**數目。</span><span class="sxs-lookup"><span data-stu-id="d2799-207">First you test asking the bot how many **Tracked Objects** are stored in the database.</span></span>

> [!NOTE]
> <span data-ttu-id="d2799-208">這次您必須從 HoloLens 2 執行應用程式，因為您的系統可能無法使用「文字轉換語音」之類的服務。</span><span class="sxs-lookup"><span data-stu-id="d2799-208">This time you must run the application from the HoloLens 2 because services like *text-to-speech* may not be available on your system.</span></span>

<span data-ttu-id="d2799-209">在 HoloLens 2 上執行應用程式，然後按一下主功能表旁的「聊天機器人」按鈕。</span><span class="sxs-lookup"><span data-stu-id="d2799-209">Run the application on your HoloLens 2 and click on the *Chat Bot* button next to the main menu.</span></span>
<span data-ttu-id="d2799-210">Bot 會先問候您，現在您可以詢問**有多少物件？**</span><span class="sxs-lookup"><span data-stu-id="d2799-210">The bot will be greeting you, now ask **how many objects do we have?**</span></span>
<span data-ttu-id="d2799-211">Bot 應該會告訴您數量並結束交談。</span><span class="sxs-lookup"><span data-stu-id="d2799-211">It should tell you the quantity and end the conversation.</span></span>

#### <a name="asking-about-a-tracked-object"></a><span data-ttu-id="d2799-212">詢問追蹤物件的相關資訊</span><span class="sxs-lookup"><span data-stu-id="d2799-212">Asking about a tracked object</span></span>

<span data-ttu-id="d2799-213">現在再次執行應用程式，這次詢問**尋找追蹤物件**，Bot 會詢問您應該以 "car" 回應的名稱，或是您知道存在於資料庫中之其他「追蹤物件」的名稱。</span><span class="sxs-lookup"><span data-stu-id="d2799-213">Now run the application again and this time ask **find me a tracked object**, the bot will be asking you the name to which you should respond with the "car" or the name of an other *Tracked Object* you know exists in the database.</span></span> <span data-ttu-id="d2799-214">Bot 會告訴您例如說明等詳細資料，以及是否已指派空間錨點。</span><span class="sxs-lookup"><span data-stu-id="d2799-214">The bot will tell you details like description and if it has a spatial anchor assigned.</span></span>

> [!TIP]
> <span data-ttu-id="d2799-215">試著詢問不存在的**追蹤物件** 不存在，看看 Bot 會如何回應。</span><span class="sxs-lookup"><span data-stu-id="d2799-215">Try out asking for an **Tracked Objects** that does not exist and hear how the bot responds.</span></span>

## <a name="congratulations"></a><span data-ttu-id="d2799-216">恭喜！</span><span class="sxs-lookup"><span data-stu-id="d2799-216">Congratulations</span></span>

<span data-ttu-id="d2799-217">在本教學課程中，您已了解如何使用自然語言的交談，使用 Azure Bot Framework 來與應用程式互動。</span><span class="sxs-lookup"><span data-stu-id="d2799-217">In this tutorial you learned how Azure Bot Framework can be used to interact with the application via conversation with natural language.</span></span> <span data-ttu-id="d2799-218">您已了解如何開發自己的 Bot，以及要讓其順利執行的所有必要條件。</span><span class="sxs-lookup"><span data-stu-id="d2799-218">You learned how to develope your own bot and what all the moving pieces are to get it running,</span></span>

## <a name="conclusion"></a><span data-ttu-id="d2799-219">結論</span><span class="sxs-lookup"><span data-stu-id="d2799-219">Conclusion</span></span>

<span data-ttu-id="d2799-220">在此教學課程系列中，您已體驗到 **Azure 雲端服務**如何為您的應用程式帶來全新且令人興奮的功能。</span><span class="sxs-lookup"><span data-stu-id="d2799-220">Through the course of this tutorial series you experienced how **Azure Cloud services** brought new and exciting features to your application.</span></span>
<span data-ttu-id="d2799-221">您現在可以使用 **Azure 儲存體**，將資料和影像儲存在雲端中，使用 **Azure 自訂視覺** 來關聯和定型模型、將物件帶入具有 **Azure Spatial Anchors** 的本機內容，以及實作 **Azure Bot Framework (由 LUIS 提供技術支援)** ，以全新且自然的互動模式新增對話式 Bot。</span><span class="sxs-lookup"><span data-stu-id="d2799-221">You can now store data and images in the cloud with **Azure Storage**, use **Azure Custom Vision** to associate images and train a model, bring objects to a local context with **Azure Spatial Anchors**, and implement **Azure Bot Framework powered by LUIS** to add a conversational bot for a new and natural interaction pattern.</span></span>
