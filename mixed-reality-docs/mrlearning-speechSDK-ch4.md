---
title: MR 學習 Speechsdk.quickstart 模組-語音辨識與轉譯
description: 完成此課程, 以瞭解如何在混合現實應用程式中執行 Azure 語音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: b434b9c79a702067a9c3db6fb25b0f75cdc6030d
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485781"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="83d9a-104">4.設定意圖和自然語言理解</span><span class="sxs-lookup"><span data-stu-id="83d9a-104">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="83d9a-105">在這一課, 我們將探索 Azure 語音服務的意圖功能。</span><span class="sxs-lookup"><span data-stu-id="83d9a-105">In this lesson, we will explore the Azure Speech Service's Intent feature.</span></span> <span data-ttu-id="83d9a-106">「意圖」功能可讓我們使用 AI 提供的語音命令來提供應用程式, 使用者可以在其中說出非特定的語音命令, 並仍然讓系統瞭解其意圖。</span><span class="sxs-lookup"><span data-stu-id="83d9a-106">The Intent feature allows us to equip our application with AI-powered voice commands, where users can say non-specific voice commands, and still have their intent understood by the system.</span></span> <span data-ttu-id="83d9a-107">在此課程中, 我們將設定 Azure LUIS 入口網站、設定我們的意圖/實體/語句、發佈意圖資源、將 Unity 應用程式連接至意圖資源, 以及進行我們的第一個意圖 API 呼叫。</span><span class="sxs-lookup"><span data-stu-id="83d9a-107">During this lesson, we will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

## <a name="objectives"></a><span data-ttu-id="83d9a-108">目標</span><span class="sxs-lookup"><span data-stu-id="83d9a-108">Objectives</span></span>

- <span data-ttu-id="83d9a-109">瞭解如何在我們的應用程式中設定意圖和自然語言理解</span><span class="sxs-lookup"><span data-stu-id="83d9a-109">Learn how to set up intent and natural language understanding in our application</span></span>
- <span data-ttu-id="83d9a-110">瞭解如何設定 Azure 的 LUIS 入口網站</span><span class="sxs-lookup"><span data-stu-id="83d9a-110">Learn how to set up Azure's LUIS Portal</span></span>
- <span data-ttu-id="83d9a-111">瞭解如何在 Azure 上設定意圖、實體和語句</span><span class="sxs-lookup"><span data-stu-id="83d9a-111">Learn how to set up intent, entities, and utterances on Azure</span></span>

## <a name="instructions"></a><span data-ttu-id="83d9a-112">指示</span><span class="sxs-lookup"><span data-stu-id="83d9a-112">Instructions</span></span>
1. <span data-ttu-id="83d9a-113">允許您的電腦啟用聽寫, 若要這麼做, 請移至 [Windows 設定], 選取 [隱私權], 然後選取 [語音], 最後是 [筆跡 & 輸入], 然後開啟 [語音服務] 並輸入建議。</span><span class="sxs-lookup"><span data-stu-id="83d9a-113">Allow your machine to enable Dictation, to do this, go to Windows Settings, select "privacy," then "speech," and finally "inking & typing" and turn on speech services and typing suggestions.</span></span>

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)


2. <span data-ttu-id="83d9a-117">登入[Azure 入口網站](https://portal.azure.com/)。</span><span class="sxs-lookup"><span data-stu-id="83d9a-117">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="83d9a-118">登入之後, 請按一下 [建立資源], 並搜尋 "Language Understanding", 然後按一下 enter。</span><span class="sxs-lookup"><span data-stu-id="83d9a-118">Once you are logged in, click on Create a resource, and search for "Language Understanding," and click enter.</span></span>

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. <span data-ttu-id="83d9a-120">選取 [建立] 按鈕, 以建立此服務的實例。</span><span class="sxs-lookup"><span data-stu-id="83d9a-120">Select the Create button, to create an instance of this service.</span></span> <span data-ttu-id="83d9a-121">將專案命名為 "Speech_SDK_Learning_Module", 然後選取 [隨用隨付]。</span><span class="sxs-lookup"><span data-stu-id="83d9a-121">Name your project “Speech_SDK_Learning_Module” and select “Pay As You Go.”</span></span>

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. <span data-ttu-id="83d9a-124">選取您的區域。</span><span class="sxs-lookup"><span data-stu-id="83d9a-124">Select your Region.</span></span>  <span data-ttu-id="83d9a-125">基於本教學課程的目的, 請選取 [(US) 美國西部]。</span><span class="sxs-lookup"><span data-stu-id="83d9a-125">For the purpose of this tutorial, select "(US) West US."</span></span> <span data-ttu-id="83d9a-126">然後選擇 [F0] 作為 [定價層]。</span><span class="sxs-lookup"><span data-stu-id="83d9a-126">Then choose "F0" for the pricing tier.</span></span> <span data-ttu-id="83d9a-127">現在, 按一下 [建立] (位於左下角) 以建立資源。</span><span class="sxs-lookup"><span data-stu-id="83d9a-127">Now click "create" (located in the bottom left corner) to create the resource.</span></span>

>  <span data-ttu-id="83d9a-128">注意: 按一下 [建立] 之後, 您必須等候服務建立, 這可能需要一分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="83d9a-128">Note: once you have clicked on "create," you will have to wait for the service to be created, this might take a minute.</span></span>

5. <span data-ttu-id="83d9a-129">建立資源之後, 入口網站中會出現通知。</span><span class="sxs-lookup"><span data-stu-id="83d9a-129">A notification will appear in the portal once the Resource is created.</span></span> <span data-ttu-id="83d9a-130">按一下此通知, 然後選取 [移至資源]。</span><span class="sxs-lookup"><span data-stu-id="83d9a-130">Click on this notification and select "Go to resource."</span></span>

6. <span data-ttu-id="83d9a-131">從 "LUIS API" 服務的 [快速入門] 頁面, 流覽至第一個步驟, 抓取您的 [金鑰], 然後按一下 [金鑰] (您也可以按一下下圖中的藍色超連結 [金鑰] 來達成此目的)。</span><span class="sxs-lookup"><span data-stu-id="83d9a-131">From the "Quick Start" page of your "LUIS API" service, navigate to the first step, grab your "keys," and click "keys" (you can also achieve this by clicking the blue hyperlink "keys," shown in the image below).</span></span> <span data-ttu-id="83d9a-132">這會顯示您的服務「金鑰」。</span><span class="sxs-lookup"><span data-stu-id="83d9a-132">This will reveal your service, "Keys."</span></span> <span data-ttu-id="83d9a-133">儲存其中一個金鑰的複本, 讓您稍後可以在應用程式中使用它。</span><span class="sxs-lookup"><span data-stu-id="83d9a-133">Save a copy of one of the keys so you can use it later in the app.</span></span>

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. <span data-ttu-id="83d9a-135">回到第2b 節下的 [快速入門] 頁面, 按一下 [Language Understanding 入口網站] (如上圖所示), 將其重新導向至您將用來在 LUIS 應用程式中建立新服務的網頁。</span><span class="sxs-lookup"><span data-stu-id="83d9a-135">Back in the "Quick Start" page under Section 2b, click on "Language Understanding Portal" (shown in the image above) to be redirected to the webpage which you will use to create your new service, within the LUIS application.</span></span>

> <span data-ttu-id="83d9a-136">注意:到達「Language Understanding 入口網站」時, 您可能需要登入 (如果您尚未這麼做), 其認證與您的 Azure 入口網站相同。</span><span class="sxs-lookup"><span data-stu-id="83d9a-136">Note: Upon reaching the "Language Understanding Portal," you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="83d9a-137">如果這是您第一次使用 LUIS, 您將需要向下滾動到歡迎頁面底部, 以尋找並按一下 [建立 LUIS] 應用程式按鈕。</span><span class="sxs-lookup"><span data-stu-id="83d9a-137">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the "Create LUIS" app button.</span></span>

8. <span data-ttu-id="83d9a-138">登入之後, 按一下 [我的應用程式] (如果您目前不在該區段中)。</span><span class="sxs-lookup"><span data-stu-id="83d9a-138">Once logged in, click My Apps (if you are not in that section currently).</span></span> <span data-ttu-id="83d9a-139">然後, 您可以按一下 [建立新的應用程式]。</span><span class="sxs-lookup"><span data-stu-id="83d9a-139">You can then click on Create new app.</span></span> <span data-ttu-id="83d9a-140">將新的應用程式命名為「語音 SDK 學習模組」。</span><span class="sxs-lookup"><span data-stu-id="83d9a-140">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="83d9a-141">也將「語音 SDK 學習模組」新增至 [描述] 欄位。</span><span class="sxs-lookup"><span data-stu-id="83d9a-141">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="83d9a-142">然後按一下 [完成]。</span><span class="sxs-lookup"><span data-stu-id="83d9a-142">Then click "done."</span></span>

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> <span data-ttu-id="83d9a-145">下如果您的應用程式應該瞭解與英文不同的語言, 您應該將「文化特性」變更為適當的語言。</span><span class="sxs-lookup"><span data-stu-id="83d9a-145">note: If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

9. <span data-ttu-id="83d9a-146">按一下位於右上方的 [組建]。</span><span class="sxs-lookup"><span data-stu-id="83d9a-146">Click “Build” located in the top right.</span></span>

10. <span data-ttu-id="83d9a-147">在左側的 [應用程式資產] 底下, 選取 [意圖], 然後按一下 [建立新意圖], 並將它命名為 "PressButton"。</span><span class="sxs-lookup"><span data-stu-id="83d9a-147">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span> 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> <span data-ttu-id="83d9a-149">注意:請務必使用本教學課程中使用的意圖和機構名稱, 因為 Lunarcom 應用程式會依名稱參考它們。</span><span class="sxs-lookup"><span data-stu-id="83d9a-149">Note: It is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span> 
>
> <span data-ttu-id="83d9a-150">注意: 您現在應該有2個意圖-"PressButton" 和 "None"。</span><span class="sxs-lookup"><span data-stu-id="83d9a-150">Note: you should now have 2 Intents - “PressButton” and “None."</span></span>

11. <span data-ttu-id="83d9a-151">在左側的 [應用程式資產] 底下, 選取 [實體], 然後按一下 [建立新實體], 並將其命名為「動作」, 並將實體類型保留為「簡單」。</span><span class="sxs-lookup"><span data-stu-id="83d9a-151">Under App Assets on the left, select “Entities” and click “Create New Entity” and name it “Action” and keep the Entity Type as “Simple.”</span></span>

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. <span data-ttu-id="83d9a-153">再次按一下 [建立新實體], 並將它命名為 "Target", 並將實體類型保留為「簡單」。</span><span class="sxs-lookup"><span data-stu-id="83d9a-153">Click “Create New Entity” again and name it “Target” and keep the Entity Type as “Simple” as well.</span></span>

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. <span data-ttu-id="83d9a-155">在左側的 [應用程式資產] 底下, 選取 [意圖], 然後按一下您在步驟10中建立的「PressButton」意圖。</span><span class="sxs-lookup"><span data-stu-id="83d9a-155">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. <span data-ttu-id="83d9a-157">按一下右側的 [視圖選項] 下拉式清單, 然後選取 [顯示實體值]。</span><span class="sxs-lookup"><span data-stu-id="83d9a-157">Click on the "View options" dropdown on the right and select "show entity values."</span></span> 

![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)<span data-ttu-id="83d9a-159">按一下 [輸入範例 ...]</span><span class="sxs-lookup"><span data-stu-id="83d9a-159">Click on the “Enter an example…”</span></span> <span data-ttu-id="83d9a-160">工具箱.</span><span class="sxs-lookup"><span data-stu-id="83d9a-160">textbox.</span></span> <span data-ttu-id="83d9a-161">然後, 輸入下列語句:</span><span class="sxs-lookup"><span data-stu-id="83d9a-161">Then, enter the following utterances:</span></span> 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. <span data-ttu-id="83d9a-163">按一下右側的 [視圖選項] 下拉式清單, 然後選取 [顯示機構名稱]。</span><span class="sxs-lookup"><span data-stu-id="83d9a-163">Click on the "View options" dropdown on the right and select "Show entity names."</span></span>

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. <span data-ttu-id="83d9a-165">確定10個語句中的每個都在下列位置具有下列實體標籤1。)按一下標記錯誤的單字, 然後在快顯視窗中選取 [移除標籤] 和 [2])。按一下應該加上標籤的單字, 然後在快顯視窗中選取適當的標籤。</span><span class="sxs-lookup"><span data-stu-id="83d9a-165">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. <span data-ttu-id="83d9a-167">現在, 若要發行模型, 請按一下右上方的 [定型]。</span><span class="sxs-lookup"><span data-stu-id="83d9a-167">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="83d9a-168">然後, 在完成處理之後, 按一下右上方的 [測試]。</span><span class="sxs-lookup"><span data-stu-id="83d9a-168">Then, once it has finished processing, click "Test" in the top right.</span></span>

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. <span data-ttu-id="83d9a-170">在文字方塊中輸入「選取啟動按鈕」。</span><span class="sxs-lookup"><span data-stu-id="83d9a-170">Enter in “select the launch button” in  the textbox.</span></span>

> <span data-ttu-id="83d9a-171">注意: 我們並未在語句中新增「選取」做為動作, 但如果您按一下 [檢查], 則模型會被辨識為「選取」做為動作實體。</span><span class="sxs-lookup"><span data-stu-id="83d9a-171">note: we did not add “select” as an action in any of our Utterances - but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. <span data-ttu-id="83d9a-173">現在, 按一下右上方的 [發佈]。</span><span class="sxs-lookup"><span data-stu-id="83d9a-173">Now, click "publish" in the top right.</span></span> <span data-ttu-id="83d9a-174">確定下拉式清單顯示「生產環境」, 然後按一下快顯上的 [發佈]。</span><span class="sxs-lookup"><span data-stu-id="83d9a-174">Ensure the dropdown says “Production” and click "publish" on the popup as well.</span></span> 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. <span data-ttu-id="83d9a-176">發佈之後, 頁面頂端應該會出現綠色橫條。</span><span class="sxs-lookup"><span data-stu-id="83d9a-176">Once published, a green bar should appear at the top of the page.</span></span>  <span data-ttu-id="83d9a-177">按一下要移至 [管理] 頁面的綠色橫條。</span><span class="sxs-lookup"><span data-stu-id="83d9a-177">Click on the green bar to be taken to the "Manage" page.</span></span> 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. <span data-ttu-id="83d9a-179">按一下左側 [應用程式設定] 底下的 [金鑰和端點]。</span><span class="sxs-lookup"><span data-stu-id="83d9a-179">Click on "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="83d9a-180">然後, 將下拉式的 [發行至] 設定為 [生產]。</span><span class="sxs-lookup"><span data-stu-id="83d9a-180">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="83d9a-181">設定 [時區] 以符合您的時間, 然後選取方塊以包含所有預測的意圖分數。</span><span class="sxs-lookup"><span data-stu-id="83d9a-181">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="83d9a-182">最後, 按一下 [指派資源]。</span><span class="sxs-lookup"><span data-stu-id="83d9a-182">Lastly, Click on "Assign resource."</span></span>

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. <span data-ttu-id="83d9a-184">從第一個下拉式清單中選取 [租使用者], 然後在 [訂用帳戶名稱] 下拉式清單中選取 [隨用隨付]。</span><span class="sxs-lookup"><span data-stu-id="83d9a-184">Select tenant from the first dropdown, and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="83d9a-185">在 [LUIS 資源名稱] 下, 選擇我們在步驟1-5 中所建立的資源。</span><span class="sxs-lookup"><span data-stu-id="83d9a-185">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="83d9a-186">然後, 按一下 [指派資源]。</span><span class="sxs-lookup"><span data-stu-id="83d9a-186">Then, click on "Assign resource."</span></span> 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> <span data-ttu-id="83d9a-188">注意:請務必複製並儲存與剛才指派的資源相關聯的端點 URL, 以便在下一節中輕鬆存取。</span><span class="sxs-lookup"><span data-stu-id="83d9a-188">Note: Ensure to copy and save the Endpoint URL associated with the resource we just assigned so that it is easily accessible for the next section.</span></span>
>
> <span data-ttu-id="83d9a-189">注意:在 [租使用者名稱] 中, 放入您為此應用程式建立的公司或設定檔。</span><span class="sxs-lookup"><span data-stu-id="83d9a-189">Note: For the Tenant name, put your corporation or profile that you created for this application.</span></span>

23. <span data-ttu-id="83d9a-190">現在, 在 Unity 中開啟新的應用程式, 然後選取階層中的 [Lunarcom_Base] 物件。</span><span class="sxs-lookup"><span data-stu-id="83d9a-190">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="83d9a-191">按一下 [偵測器] 面板中的 [新增元件], 然後搜尋並選取 [LunarcomIntentRecognizer]。</span><span class="sxs-lookup"><span data-stu-id="83d9a-191">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. <span data-ttu-id="83d9a-193">在 [偵測器] 面板中 "LunarcomIntentRecognizer" 的 [Luis 端點] 欄位中, 輸入您在步驟22中儲存的端點 URL。</span><span class="sxs-lookup"><span data-stu-id="83d9a-193">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span> 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  <span data-ttu-id="83d9a-195">注意:在 [偵測器] 面板的 [LunarcomOfflineRecognizer] 元件中, 確定已針對 [SimulateOfflineMode] 選取 [停用], 否則測試程式將無法正常執行。</span><span class="sxs-lookup"><span data-stu-id="83d9a-195">Note: In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span> 

25. <span data-ttu-id="83d9a-196">按下 Unity 編輯器中的 [播放] 按鈕, 然後按一下 [rocket] 按鈕以啟動意圖辨識。</span><span class="sxs-lookup"><span data-stu-id="83d9a-196">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="83d9a-197">有些純粹是「選取啟動 rocket 按鈕」一詞。</span><span class="sxs-lookup"><span data-stu-id="83d9a-197">Utter the phrase “select the launch rocket button.”</span></span>

>  <span data-ttu-id="83d9a-198">注意:應用程式已辨識所需的函式, 並已啟用 [rocket] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="83d9a-198">Note: The app recognized the desired function and activated the rocket button.</span></span>
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="83d9a-200">恭喜！</span><span class="sxs-lookup"><span data-stu-id="83d9a-200">Congratulations</span></span>

<span data-ttu-id="83d9a-201">在本課程中, 我們已瞭解如何新增 AI 驅動的語音命令!</span><span class="sxs-lookup"><span data-stu-id="83d9a-201">In this lesson, we learned how to add AI-powered speech commands!</span></span> <span data-ttu-id="83d9a-202">您的程式現在可以辨識使用者的意圖, 即使他們沒有有些純粹是精確的語音命令也一樣。</span><span class="sxs-lookup"><span data-stu-id="83d9a-202">Now your program can recognize users' intent even if they do not utter precise voice commands.</span></span>

