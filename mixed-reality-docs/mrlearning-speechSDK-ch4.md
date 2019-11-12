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
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="e7f54-105">4. 設定意圖和自然語言理解</span><span class="sxs-lookup"><span data-stu-id="e7f54-105">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="e7f54-106">在這一課，我們將探索 Azure 語音服務的意圖功能。</span><span class="sxs-lookup"><span data-stu-id="e7f54-106">In this lesson, we will explore the Azure Speech Service's Intent feature.</span></span> <span data-ttu-id="e7f54-107">「意圖」功能可讓我們使用 AI 提供的語音命令來提供應用程式，使用者可以在其中說出非特定的語音命令，並仍然讓系統瞭解其意圖。</span><span class="sxs-lookup"><span data-stu-id="e7f54-107">The Intent feature allows us to equip our application with AI-powered voice commands, where users can say non-specific voice commands, and still have their intent understood by the system.</span></span> <span data-ttu-id="e7f54-108">在此課程中，我們將設定 Azure LUIS 入口網站、設定我們的意圖/實體/語句、發佈意圖資源、將 Unity 應用程式連接至意圖資源，以及進行我們的第一個意圖 API 呼叫。</span><span class="sxs-lookup"><span data-stu-id="e7f54-108">During this lesson, we will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

## <a name="objectives"></a><span data-ttu-id="e7f54-109">目標</span><span class="sxs-lookup"><span data-stu-id="e7f54-109">Objectives</span></span>

- <span data-ttu-id="e7f54-110">瞭解如何在我們的應用程式中設定意圖和自然語言理解</span><span class="sxs-lookup"><span data-stu-id="e7f54-110">Learn how to set up intent and natural language understanding in our application</span></span>
- <span data-ttu-id="e7f54-111">瞭解如何設定 Azure 的 LUIS 入口網站</span><span class="sxs-lookup"><span data-stu-id="e7f54-111">Learn how to set up Azure's LUIS Portal</span></span>
- <span data-ttu-id="e7f54-112">瞭解如何在 Azure 上設定意圖、實體和語句</span><span class="sxs-lookup"><span data-stu-id="e7f54-112">Learn how to set up intent, entities, and utterances on Azure</span></span>

## <a name="instructions"></a><span data-ttu-id="e7f54-113">指示</span><span class="sxs-lookup"><span data-stu-id="e7f54-113">Instructions</span></span>

1. <span data-ttu-id="e7f54-114">允許您的電腦啟用聽寫，若要這麼做，請移至 [Windows 設定]，選取 [隱私權]，然後選取 [語音]，最後是 [筆跡 & 輸入]，然後開啟 [語音服務] 並輸入建議。</span><span class="sxs-lookup"><span data-stu-id="e7f54-114">Allow your machine to enable Dictation, to do this, go to Windows Settings, select "privacy," then "speech," and finally "inking & typing" and turn on speech services and typing suggestions.</span></span>

    ![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

    ![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

    ![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

2. <span data-ttu-id="e7f54-118">登入[Azure 入口網站](https://portal.azure.com/)。</span><span class="sxs-lookup"><span data-stu-id="e7f54-118">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="e7f54-119">登入之後，請按一下 [建立資源]，並搜尋 "Language Understanding"，然後按一下 enter。</span><span class="sxs-lookup"><span data-stu-id="e7f54-119">Once you are logged in, click on Create a resource, and search for "Language Understanding," and click enter.</span></span>

    ![mrlearning-speech-ch4-1-step2 .png](images/mrlearning-speech-ch4-1-step2.png)

3. <span data-ttu-id="e7f54-121">按一下 [**建立**] 按鈕，以建立此服務的實例。</span><span class="sxs-lookup"><span data-stu-id="e7f54-121">Click the **Create** button to create an instance of this service.</span></span>

    ![mrlearning-speech-ch4-1-step3a .png](images/mrlearning-speech-ch4-1-step3a.png)

    <span data-ttu-id="e7f54-123">提供資源的**名稱**，例如*語音-SDK 學習模組*。</span><span class="sxs-lookup"><span data-stu-id="e7f54-123">Give your resource a **Name**, for example, *Speech-SDK-Learning-Module*.</span></span> <span data-ttu-id="e7f54-124">針對 [**訂**用帳戶]，選取 [*隨用隨付*] 或 [*免費記錄*] （如果您有試用帳戶）。</span><span class="sxs-lookup"><span data-stu-id="e7f54-124">For **Subscription**, select *Pay As You Go* or *Free Trail* if you have a trial account.</span></span> <span data-ttu-id="e7f54-125">接下來，按一下 [**建立新**的] 連結，輸入名稱（例如， *HoloLens-2-教學課程-資源群組*），然後按一下 [**確定]** 按鈕，以建立新的**資源群組**。</span><span class="sxs-lookup"><span data-stu-id="e7f54-125">Next, create a new **Resource Group** by clicking the **Create new** link, enter a name, for example, *HoloLens-2-Tutorials-Resource-Group*, and clicking the **OK** button.</span></span>

    ![mrlearning-speech-ch4-1-step3b .png](images/mrlearning-speech-ch4-1-step3b.png)

4. <span data-ttu-id="e7f54-127">選取您的**撰寫位置**和**執行時間位置**，基於本教學課程的目的，請使用 *（us）「美國西部*」。</span><span class="sxs-lookup"><span data-stu-id="e7f54-127">Select your **Authoring location** and **Runtime location**, for the purpose of this tutorial, use *(US) West US*.</span></span> <span data-ttu-id="e7f54-128">然後選擇 [**撰寫] 定價層**和 [執行時間]**定價層**的 [ *F0 （每秒5個呼叫]、[每月*10，000個呼叫]）。</span><span class="sxs-lookup"><span data-stu-id="e7f54-128">Then choose *F0 (5 Calls per second, 10K Calls per month)* for the **Authoring pricing tier** and **Runtime pricing tier**.</span></span> <span data-ttu-id="e7f54-129">最後，按一下 [**建立**] 按鈕，以建立資源和新的資源群組。</span><span class="sxs-lookup"><span data-stu-id="e7f54-129">Finally, click the **Create** button to create the resource as well as the new resource group.</span></span>

    ![mrlearning-speech-ch4-1-step4 .png](images/mrlearning-speech-ch4-1-step4.png)

    >[!NOTE]
    ><span data-ttu-id="e7f54-131">按一下 [建立] 按鈕之後，您必須等候服務建立，這可能需要幾分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="e7f54-131">After you click the Create button you will have to wait for the service to be created, this might take a few minute.</span></span>

5. <span data-ttu-id="e7f54-132">資源建立程式完成後，您會看到**部署已完成**的訊息。</span><span class="sxs-lookup"><span data-stu-id="e7f54-132">Once the resource creation process is complete, you will see the message **Your deployment is complete**.</span></span>

    ![mrlearning-speech-ch4-1-step5 .png](images/mrlearning-speech-ch4-1-step5.png)

6. <span data-ttu-id="e7f54-134">使用相同的使用者帳戶，登入[Language Understanding 智慧型服務（LUIS）](https://www.luis.ai/)入口網站，選取您的國家/地區，並同意使用條款。</span><span class="sxs-lookup"><span data-stu-id="e7f54-134">Using the same user account, sign in to the [Language Understanding Intelligent Service (LUIS)](https://www.luis.ai/) portal, select your country, and agree to the terms of use.</span></span>

    >[!NOTE]
    ><span data-ttu-id="e7f54-135">到達 Language Understanding 入口網站時，您可能需要登入（如果您尚未這麼做），其認證與您的 Azure 入口網站相同。</span><span class="sxs-lookup"><span data-stu-id="e7f54-135">Upon reaching the Language Understanding portal, you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="e7f54-136">如果這是您第一次使用 LUIS，您將需要向下滾動到歡迎頁面底部，以尋找並按一下 [建立 LUIS] 應用程式按鈕。</span><span class="sxs-lookup"><span data-stu-id="e7f54-136">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the "Create LUIS" app button.</span></span>

7. <span data-ttu-id="e7f54-137">登入之後，按一下 [我的應用程式] （如果您目前不在該區段中）。</span><span class="sxs-lookup"><span data-stu-id="e7f54-137">Once logged in, click My Apps (if you are not in that section currently).</span></span> <span data-ttu-id="e7f54-138">然後，您可以按一下 [建立新的應用程式]。</span><span class="sxs-lookup"><span data-stu-id="e7f54-138">You can then click on Create new app.</span></span> <span data-ttu-id="e7f54-139">將新的應用程式命名為「語音 SDK 學習模組」。</span><span class="sxs-lookup"><span data-stu-id="e7f54-139">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="e7f54-140">也將「語音 SDK 學習模組」新增至 [描述] 欄位。</span><span class="sxs-lookup"><span data-stu-id="e7f54-140">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="e7f54-141">然後按一下 [完成]。</span><span class="sxs-lookup"><span data-stu-id="e7f54-141">Then click "done."</span></span>

    ![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

    ![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

    >[!NOTE]
    ><span data-ttu-id="e7f54-144">如果您的應用程式應該瞭解與英文不同的語言，您應該將「文化特性」變更為適當的語言。</span><span class="sxs-lookup"><span data-stu-id="e7f54-144">If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

8. <span data-ttu-id="e7f54-145">按一下位於右上方的 [組建]。</span><span class="sxs-lookup"><span data-stu-id="e7f54-145">Click “Build” located in the top right.</span></span>

9. <span data-ttu-id="e7f54-146">在左側的 [應用程式資產] 底下，選取 [意圖]，然後按一下 [建立新意圖]，並將它命名為 "PressButton"。</span><span class="sxs-lookup"><span data-stu-id="e7f54-146">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span>

    ![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

    >[!NOTE]
    ><span data-ttu-id="e7f54-148">請務必使用本教學課程中使用的意圖和機構名稱，因為 Lunarcom 應用程式會依名稱參考它們。</span><span class="sxs-lookup"><span data-stu-id="e7f54-148">It is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span>

    >[!NOTE]
    ><span data-ttu-id="e7f54-149">您現在應該有兩個意圖-"PressButton" 和 "None"。</span><span class="sxs-lookup"><span data-stu-id="e7f54-149">You should now have 2 Intents - “PressButton” and “None."</span></span>

10. <span data-ttu-id="e7f54-150">在左側的 [應用程式資產] 底下，選取 [實體]，然後按一下 [建立新實體]，並將其命名為「動作」，並將實體類型保留為「簡單」。</span><span class="sxs-lookup"><span data-stu-id="e7f54-150">Under App Assets on the left, select “Entities” and click “Create New Entity” and name it “Action” and keep the Entity Type as “Simple.”</span></span>

    ![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

11. <span data-ttu-id="e7f54-152">再次按一下 [建立新實體]，並將它命名為 "Target"，並將實體類型保留為「簡單」。</span><span class="sxs-lookup"><span data-stu-id="e7f54-152">Click “Create New Entity” again and name it “Target” and keep the Entity Type as “Simple” as well.</span></span>

    ![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

12. <span data-ttu-id="e7f54-154">在左側的 [應用程式資產] 底下，選取 [意圖]，然後按一下您在步驟10中建立的「PressButton」意圖。</span><span class="sxs-lookup"><span data-stu-id="e7f54-154">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

    ![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

13. <span data-ttu-id="e7f54-156">按一下右側的 [視圖選項] 下拉式清單，然後選取 [顯示實體值]。</span><span class="sxs-lookup"><span data-stu-id="e7f54-156">Click on the "View options" dropdown on the right and select "show entity values."</span></span>

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)

    <span data-ttu-id="e7f54-158">按一下 [輸入範例 ...]</span><span class="sxs-lookup"><span data-stu-id="e7f54-158">Click on the “Enter an example…”</span></span> <span data-ttu-id="e7f54-159">工具箱.</span><span class="sxs-lookup"><span data-stu-id="e7f54-159">textbox.</span></span> <span data-ttu-id="e7f54-160">然後，輸入下列語句：</span><span class="sxs-lookup"><span data-stu-id="e7f54-160">Then, enter the following utterances:</span></span>

    ![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

14. <span data-ttu-id="e7f54-162">按一下右側的 [視圖選項] 下拉式清單，然後選取 [顯示機構名稱]。</span><span class="sxs-lookup"><span data-stu-id="e7f54-162">Click on the "View options" dropdown on the right and select "Show entity names."</span></span>

    ![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

15. <span data-ttu-id="e7f54-164">確定10個語句中的每個都在下列位置具有下列實體標籤1。）按一下標記錯誤的單字，然後在快顯視窗中選取 [移除標籤] 和 [2]）。按一下應該加上標籤的單字，然後在快顯視窗中選取適當的標籤。</span><span class="sxs-lookup"><span data-stu-id="e7f54-164">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

    ![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

16. <span data-ttu-id="e7f54-166">現在，若要發行模型，請按一下右上方的 [定型]。</span><span class="sxs-lookup"><span data-stu-id="e7f54-166">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="e7f54-167">然後，在完成處理之後，按一下右上方的 [測試]。</span><span class="sxs-lookup"><span data-stu-id="e7f54-167">Then, once it has finished processing, click "Test" in the top right.</span></span>

    ![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

17. <span data-ttu-id="e7f54-169">在文字方塊中輸入「選取啟動按鈕」。</span><span class="sxs-lookup"><span data-stu-id="e7f54-169">Enter in “select the launch button” in  the textbox.</span></span>

    >[!NOTE]
    ><span data-ttu-id="e7f54-170">我們並未在語句中新增「選取」做為動作，但如果您按一下 [檢查]，則模型會被辨識為「選取」做為動作實體。</span><span class="sxs-lookup"><span data-stu-id="e7f54-170">We did not add “select” as an action in any of our Utterances - but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
    >
    > ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

18. <span data-ttu-id="e7f54-172">現在，按一下右上方的 [發佈]。</span><span class="sxs-lookup"><span data-stu-id="e7f54-172">Now, click "publish" in the top right.</span></span> <span data-ttu-id="e7f54-173">確定下拉式清單顯示「生產環境」，然後按一下快顯上的 [發佈]。</span><span class="sxs-lookup"><span data-stu-id="e7f54-173">Ensure the dropdown says “Production” and click "publish" on the popup as well.</span></span>

    ![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

19. <span data-ttu-id="e7f54-175">發佈之後，頁面頂端應該會出現綠色橫條。</span><span class="sxs-lookup"><span data-stu-id="e7f54-175">Once published, a green bar should appear at the top of the page.</span></span>  <span data-ttu-id="e7f54-176">按一下要移至 [管理] 頁面的綠色橫條。</span><span class="sxs-lookup"><span data-stu-id="e7f54-176">Click on the green bar to be taken to the "Manage" page.</span></span>

    ![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

20. <span data-ttu-id="e7f54-178">按一下左側 [應用程式設定] 底下的 [金鑰和端點]。</span><span class="sxs-lookup"><span data-stu-id="e7f54-178">Click on "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="e7f54-179">然後，將下拉式的 [發行至] 設定為 [生產]。</span><span class="sxs-lookup"><span data-stu-id="e7f54-179">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="e7f54-180">設定 [時區] 以符合您的時間，然後選取方塊以包含所有預測的意圖分數。</span><span class="sxs-lookup"><span data-stu-id="e7f54-180">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="e7f54-181">最後，按一下 [指派資源]。</span><span class="sxs-lookup"><span data-stu-id="e7f54-181">Lastly, Click on "Assign resource."</span></span>

    ![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

21. <span data-ttu-id="e7f54-183">從第一個下拉式清單中選取 [租使用者]，然後在 [訂用帳戶名稱] 下拉式清單中選取 [隨用隨付]。</span><span class="sxs-lookup"><span data-stu-id="e7f54-183">Select tenant from the first dropdown, and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="e7f54-184">在 [LUIS 資源名稱] 下，選擇我們在步驟1-5 中所建立的資源。</span><span class="sxs-lookup"><span data-stu-id="e7f54-184">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="e7f54-185">然後，按一下 [指派資源]。</span><span class="sxs-lookup"><span data-stu-id="e7f54-185">Then, click on "Assign resource."</span></span>

    ![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

    >[!NOTE]
    ><span data-ttu-id="e7f54-187">請務必複製並儲存與剛才指派的資源相關聯的端點 URL，以便在下一節中輕鬆存取。</span><span class="sxs-lookup"><span data-stu-id="e7f54-187">Ensure to copy and save the Endpoint URL associated with the resource we just assigned so that it is easily accessible for the next section.</span></span>

    >[!NOTE]
    ><span data-ttu-id="e7f54-188">在 [租使用者名稱] 中，放入您為此應用程式建立的公司或設定檔。</span><span class="sxs-lookup"><span data-stu-id="e7f54-188">For the Tenant name, put your corporation or profile that you created for this application.</span></span>

22. <span data-ttu-id="e7f54-189">現在，在 Unity 中開啟新的應用程式，然後選取階層中的 [Lunarcom_Base] 物件。</span><span class="sxs-lookup"><span data-stu-id="e7f54-189">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="e7f54-190">按一下 [偵測器] 面板中的 [新增元件]，然後搜尋並選取 [LunarcomIntentRecognizer]。</span><span class="sxs-lookup"><span data-stu-id="e7f54-190">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

    ![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

23. <span data-ttu-id="e7f54-192">在 [偵測器] 面板中 "LunarcomIntentRecognizer" 的 [Luis 端點] 欄位中，輸入您在步驟22中儲存的端點 URL。</span><span class="sxs-lookup"><span data-stu-id="e7f54-192">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span>

    ![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

    >[!NOTE]
    ><span data-ttu-id="e7f54-194">在 [偵測器] 面板的 [LunarcomOfflineRecognizer] 元件中，確定已針對 [SimulateOfflineMode] 選取 [停用]，否則測試程式將無法正常執行。</span><span class="sxs-lookup"><span data-stu-id="e7f54-194">In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span>

24. <span data-ttu-id="e7f54-195">按下 Unity 編輯器中的 [播放] 按鈕，然後按一下 [rocket] 按鈕以啟動意圖辨識。</span><span class="sxs-lookup"><span data-stu-id="e7f54-195">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="e7f54-196">有些純粹是「選取啟動 rocket 按鈕」一詞。</span><span class="sxs-lookup"><span data-stu-id="e7f54-196">Utter the phrase “select the launch rocket button.”</span></span>

    >[!NOTE]
    ><span data-ttu-id="e7f54-197">應用程式已辨識所需的函式，並已啟用 [rocket] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e7f54-197">The app recognized the desired function and activated the rocket button.</span></span>
    >
    >![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="e7f54-199">恭喜！</span><span class="sxs-lookup"><span data-stu-id="e7f54-199">Congratulations</span></span>

<span data-ttu-id="e7f54-200">在本課程中，我們已瞭解如何新增 AI 驅動的語音命令！</span><span class="sxs-lookup"><span data-stu-id="e7f54-200">In this lesson, we learned how to add AI-powered speech commands!</span></span> <span data-ttu-id="e7f54-201">您的程式現在可以辨識使用者的意圖，即使他們沒有有些純粹是精確的語音命令也一樣。</span><span class="sxs-lookup"><span data-stu-id="e7f54-201">Now your program can recognize users' intent even if they do not utter precise voice commands.</span></span>
