## <a name="lesson-4"></a><span data-ttu-id="253e8-101">第 4 課</span><span class="sxs-lookup"><span data-stu-id="253e8-101">Lesson 4</span></span>

<span data-ttu-id="253e8-102">在第 4 章，我們將探討語音服務的意圖功能。</span><span class="sxs-lookup"><span data-stu-id="253e8-102">In chapter 4, we will explore the Speech services Intent feature.</span></span> <span data-ttu-id="253e8-103">我們將設定我們的 Azure LUIS 入口網站、 設定我們意圖/實體/談話、 發佈我們的意圖資源、 我們的 Unity 應用程式連線至我們的意圖的資源，並讓我們第一次的意圖 API 呼叫。</span><span class="sxs-lookup"><span data-stu-id="253e8-103">We will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

1. <span data-ttu-id="253e8-104">可讓您的機器以啟用語音輸入，若要這樣做，移至 Windows 設定，選取 隱私權，然後"speech，"而最後 「 筆跡 & 輸入"並開啟語音服務與輸入的建議。</span><span class="sxs-lookup"><span data-stu-id="253e8-104">Allow your machine to enable Dictation, to do this, go to Windows Settings, select "privacy," then "speech," and finally "inking & typing" and turn on speech services and typing suggestions.</span></span>

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

> <span data-ttu-id="253e8-108">注意： 如需如何在 Mac/Macbook 上執行這項操作的資訊，請按一下[此處](linkgoeshere)。</span><span class="sxs-lookup"><span data-stu-id="253e8-108">note: for information on how to do this on a Mac/Macbook, click [here](linkgoeshere).</span></span>

2. <span data-ttu-id="253e8-109">登入[Azure 入口網站](https://portal.azure.com/)。</span><span class="sxs-lookup"><span data-stu-id="253e8-109">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="253e8-110">一旦您登入，按一下建立的資源，並搜尋 「 語言理解 」，然後按一下 [輸入]。</span><span class="sxs-lookup"><span data-stu-id="253e8-110">Once you are logged in, click on Create a resource, and search for "Language Understanding," and click enter.</span></span>

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. <span data-ttu-id="253e8-112">選取 [建立] 按鈕來建立此服務的執行個體。</span><span class="sxs-lookup"><span data-stu-id="253e8-112">Select the Create button, to create an instance of this service.</span></span> <span data-ttu-id="253e8-113">命名您的專案 「 Speech_SDK_Learning_Module"，然後選取 「 預付。 」</span><span class="sxs-lookup"><span data-stu-id="253e8-113">Name your project “Speech_SDK_Learning_Module” and select “Pay As You Go.”</span></span>

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. <span data-ttu-id="253e8-116">選取您的區域。</span><span class="sxs-lookup"><span data-stu-id="253e8-116">Select your Region.</span></span>  <span data-ttu-id="253e8-117">針對此教學課程中，選取 "（美國） West US"。</span><span class="sxs-lookup"><span data-stu-id="253e8-117">For the purpose of this tutorial, select "(US) West US."</span></span> <span data-ttu-id="253e8-118">定價層，然後選擇 「 F0"。</span><span class="sxs-lookup"><span data-stu-id="253e8-118">Then choose "F0" for the pricing tier.</span></span> <span data-ttu-id="253e8-119">現在按一下 [建立] （位於左下角） 來建立資源。</span><span class="sxs-lookup"><span data-stu-id="253e8-119">Now click "create" (located in the bottom left corner) to create the resource.</span></span>

   >  <span data-ttu-id="253e8-120">注意： 一旦您按一下 [建立] 時，您必須建立服務，這可能需要一分鐘。</span><span class="sxs-lookup"><span data-stu-id="253e8-120">note: once you have clicked on "create," you will have to wait for the service to be created, this might take a minute.</span></span>

5. <span data-ttu-id="253e8-121">通知會出現在入口網站中，一旦建立資源。</span><span class="sxs-lookup"><span data-stu-id="253e8-121">A notification will appear in the portal once the Resource is created.</span></span> <span data-ttu-id="253e8-122">按一下此通知，然後選取 [前往資源]。</span><span class="sxs-lookup"><span data-stu-id="253e8-122">Click on this notification and select "Go to resource."</span></span>

6. <span data-ttu-id="253e8-123">從 「 LUIS API 」 服務的 [快速啟動] 頁面，瀏覽至第一個步驟，取得您的 「 金鑰 」，並按一下 [金鑰] （您也可以達到這按一下藍色的超連結"索引鍵，"如下圖所示）。</span><span class="sxs-lookup"><span data-stu-id="253e8-123">From the "Quick Start" page of your "LUIS API" service, navigate to the first step, grab your "keys," and click "keys" (you can also achieve this by clicking the blue hyperlink "keys," shown in the image below).</span></span> <span data-ttu-id="253e8-124">這將顯示您的服務，[金鑰]。</span><span class="sxs-lookup"><span data-stu-id="253e8-124">This will reveal your service, "Keys."</span></span> <span data-ttu-id="253e8-125">因此您可以稍後在應用程式中使用它，請儲存其中一個金鑰的副本。</span><span class="sxs-lookup"><span data-stu-id="253e8-125">Save a copy of one of the keys so you can use it later in the app.</span></span>

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. <span data-ttu-id="253e8-127">在 [快速啟動] 頁面的下一節 2b，按一下"Language Understanding 入口網站 」 （如圖所示），重新導向至用來建立新的服務，LUIS 應用程式中的網頁。</span><span class="sxs-lookup"><span data-stu-id="253e8-127">Back in the "Quick Start" page under Section 2b, click on "Language Understanding Portal" (shown in the image above) to be redirected to the webpage which you will use to create your new service, within the LUIS application.</span></span>

> <span data-ttu-id="253e8-128">注意：達到 「 Language Understanding 入口網站 」 時，您可能需要登入，如果您還沒有，與您的 Azure 入口網站相同的認證。</span><span class="sxs-lookup"><span data-stu-id="253e8-128">note: Upon reaching the "Language Understanding Portal," you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="253e8-129">如果這是您第一次使用 LUIS，您必須捲動到底部的 歡迎 頁面來尋找並按一下 「 建立 LUIS 」 應用程式 按鈕。</span><span class="sxs-lookup"><span data-stu-id="253e8-129">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the "Create LUIS" app button.</span></span>

8. <span data-ttu-id="253e8-130">登入之後，按一下 [我的應用程式] （如果您目前不是在該區段中）。</span><span class="sxs-lookup"><span data-stu-id="253e8-130">Once logged in, click My Apps (if you are not in that section currently).</span></span> <span data-ttu-id="253e8-131">您可以按一下在 建立新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="253e8-131">You can then click on Create new app.</span></span> <span data-ttu-id="253e8-132">將新的應用程式命名為 「 語音 SDK 學習模組 」。</span><span class="sxs-lookup"><span data-stu-id="253e8-132">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="253e8-133">加入 [描述] 欄位，以及 「 語音 SDK 學習模組 」。</span><span class="sxs-lookup"><span data-stu-id="253e8-133">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="253e8-134">然後按一下 [完成]。</span><span class="sxs-lookup"><span data-stu-id="253e8-134">Then click "done."</span></span>

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> <span data-ttu-id="253e8-137">注意：如果您的應用程式應該了解不同於英語的語言，您應該將"Culture"變更為適當的語言。</span><span class="sxs-lookup"><span data-stu-id="253e8-137">note: If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

9. <span data-ttu-id="253e8-138">按一下位於右上方 「 建置 」。</span><span class="sxs-lookup"><span data-stu-id="253e8-138">Click “Build” located in the top right.</span></span>

10. <span data-ttu-id="253e8-139">在左側的應用程式資產下, 選取 「 意圖 」，然後按一下 「 建立新的意圖 」 並將它命名"PressButton。 」</span><span class="sxs-lookup"><span data-stu-id="253e8-139">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span> 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> <span data-ttu-id="253e8-141">注意： 務必要使用的意圖和實體用於本教學課程中，因為 Lunarcom 應用程式將會參考它們的名稱，即可依名稱。</span><span class="sxs-lookup"><span data-stu-id="253e8-141">note: it is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span>  <span data-ttu-id="253e8-142">其他的專案，命名慣例可以您選擇的任何內容。</span><span class="sxs-lookup"><span data-stu-id="253e8-142">For other projects, naming conventions can be whatever you choose.</span></span> 
>
> <span data-ttu-id="253e8-143">注意： 您現在應該有 2 個意圖-「 PressButton"和"None"。</span><span class="sxs-lookup"><span data-stu-id="253e8-143">note: you should now have 2 Intents - “PressButton” and “None."</span></span>

11. <span data-ttu-id="253e8-144">在左側的應用程式資產下, 選取 「 實體 」 並按一下 「 建立新的實體 」 和 「 動作 」 將它命名，讓實體類型為 「 簡單 」。</span><span class="sxs-lookup"><span data-stu-id="253e8-144">Under App Assets on the left, select “Entities” and click “Create New Entity” and name it “Action” and keep the Entity Type as “Simple.”</span></span>

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. <span data-ttu-id="253e8-146">再按一次 「 建立新的實體 」 和其命名為 「 目標 」，以及保留為 「 簡單 」 的實體類型。</span><span class="sxs-lookup"><span data-stu-id="253e8-146">Click “Create New Entity” again and name it “Target” and keep the Entity Type as “Simple” as well.</span></span>

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. <span data-ttu-id="253e8-148">在左側的應用程式資產下, 選取 「 意圖 」 然後按一下您在步驟 10 中建立您 「 PressButton"意圖。</span><span class="sxs-lookup"><span data-stu-id="253e8-148">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. <span data-ttu-id="253e8-150">按一下右邊的 [檢視選項] 下拉式清單，然後選取 [顯示] 實體的值。</span><span class="sxs-lookup"><span data-stu-id="253e8-150">Click on the "View options" dropdown on the right and select "show entity values."</span></span> 

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)<span data-ttu-id="253e8-152">按一下 輸入範例...」</span><span class="sxs-lookup"><span data-stu-id="253e8-152">Click on the “Enter an example…”</span></span> <span data-ttu-id="253e8-153">文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="253e8-153">textbox.</span></span> <span data-ttu-id="253e8-154">然後，輸入下列的表達方式：</span><span class="sxs-lookup"><span data-stu-id="253e8-154">Then, enter the following utterances:</span></span> 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. <span data-ttu-id="253e8-156">按一下右邊的 [檢視選項] 下拉式清單，然後選取 [顯示] 實體名稱。</span><span class="sxs-lookup"><span data-stu-id="253e8-156">Click on the "View options" dropdown on the right and select "Show entity names."</span></span>

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. <span data-ttu-id="253e8-158">請確認每 10 個談話 1 在下列位置中有下列的實體標籤。)按一下上的文字會誤標，然後在快顯視窗，選取 [移除標籤] 和 2。）按一下上應該有標示的文字，然後在快顯視窗，選取適當的標籤。</span><span class="sxs-lookup"><span data-stu-id="253e8-158">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. <span data-ttu-id="253e8-160">現在，如果要發佈模型，請按一下右上方的 「 定型 」。</span><span class="sxs-lookup"><span data-stu-id="253e8-160">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="253e8-161">然後完成處理後，按一下右上方的 ["Test"]。</span><span class="sxs-lookup"><span data-stu-id="253e8-161">Then, once it has finished processing, click "Test" in the top right.</span></span>

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. <span data-ttu-id="253e8-163">在中輸入 「 選取 [啟動] 按鈕 」 的文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="253e8-163">Enter in “select the launch button” in  the textbox.</span></span>

> <span data-ttu-id="253e8-164">注意： 我們並未新增 「 選取 」 做為動作在任何我們談話-，但如果您按一下 「 檢查 」，此模型視為 「 選取 」 動作實體。</span><span class="sxs-lookup"><span data-stu-id="253e8-164">note: we did not add “select” as an action in any of our Utterances - but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. <span data-ttu-id="253e8-166">現在，按一下右上方的 [發佈]。</span><span class="sxs-lookup"><span data-stu-id="253e8-166">Now, click "publish" in the top right.</span></span> <span data-ttu-id="253e8-167">確定 下拉式清單中顯示 「 生產 」，然後按一下 發佈，在快顯視窗以及。</span><span class="sxs-lookup"><span data-stu-id="253e8-167">Ensure the dropdown says “Production” and click "publish" on the popup as well.</span></span> 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. <span data-ttu-id="253e8-169">發行之後，綠色列應該會出現在頁面頂端。</span><span class="sxs-lookup"><span data-stu-id="253e8-169">Once published, a green bar should appear at the top of the page.</span></span>  <span data-ttu-id="253e8-170">按一下即可前往 [管理] 頁面上的綠色列。</span><span class="sxs-lookup"><span data-stu-id="253e8-170">Click on the green bar to be taken to the "Manage" page.</span></span> 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. <span data-ttu-id="253e8-172">按一下左側 [金鑰和端點] 下 [應用程式設定]。</span><span class="sxs-lookup"><span data-stu-id="253e8-172">Click on "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="253e8-173">然後，將下拉式清單 [發行至] 設為 「 生產 」。</span><span class="sxs-lookup"><span data-stu-id="253e8-173">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="253e8-174">設定時區-以符合您，並核取方塊以包含所有預測的意圖分數。</span><span class="sxs-lookup"><span data-stu-id="253e8-174">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="253e8-175">最後，按一下 「 指派資源 」。</span><span class="sxs-lookup"><span data-stu-id="253e8-175">Lastly, Click on "Assign resource."</span></span>

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. <span data-ttu-id="253e8-177">從第一個下拉式清單中，選取租用戶，然後選取 「 隨用隨付 」 訂用帳戶名稱的下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="253e8-177">Select tenant from the first dropdown, and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="253e8-178">LUIS 資源名稱，請在 選擇上述步驟 1-5 中建立的資源。</span><span class="sxs-lookup"><span data-stu-id="253e8-178">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="253e8-179">然後，按一下 「 指派資源 」。</span><span class="sxs-lookup"><span data-stu-id="253e8-179">Then, click on "Assign resource."</span></span> 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> <span data-ttu-id="253e8-181">注意： 請務必複製並儲存，我們只會指派，以便輕鬆存取以供下一節中的資源相關聯的端點 URL。</span><span class="sxs-lookup"><span data-stu-id="253e8-181">note: ensure to copy and save the Endpoint URL associated with the resource we just assigned so that it is easily accessible for the next section.</span></span>
>
> <span data-ttu-id="253e8-182">注意： 針對租用戶名稱，將您的公司或您建立此應用程式設定檔。</span><span class="sxs-lookup"><span data-stu-id="253e8-182">note: for the Tenant name, put your corporation or profile that you created for this application.</span></span>

23. <span data-ttu-id="253e8-183">現在，在 Unity 中開啟新的應用程式，並選取 Lunarcom_Base 物件階層架構中。</span><span class="sxs-lookup"><span data-stu-id="253e8-183">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="253e8-184">在 [偵測器] 面板中按一下 [新增元件] 然後搜尋並選取 「 LunarcomIntentRecognizer。 」</span><span class="sxs-lookup"><span data-stu-id="253e8-184">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. <span data-ttu-id="253e8-186">Luis 端點在欄位中 「 LunarcomIntentRecognizer 「 偵測器 面板中，輸入您在步驟 22 儲存端點 URL。</span><span class="sxs-lookup"><span data-stu-id="253e8-186">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span> 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  <span data-ttu-id="253e8-188">注意："LunarcomOfflineRecognizer 」 元件中在偵測器窗格中，請確定已為"SimulateOfflineMode 「 否則選取 [停用] 時，測試計劃將無法運作。</span><span class="sxs-lookup"><span data-stu-id="253e8-188">note: In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span> 

25. <span data-ttu-id="253e8-189">在 Unity 編輯器中按下 [播放] 按鈕，然後按一下 [rocket] 按鈕，啟動意圖辨識。</span><span class="sxs-lookup"><span data-stu-id="253e8-189">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="253e8-190">岳母片語 「 選取啟動 rocket 按鈕。 」</span><span class="sxs-lookup"><span data-stu-id="253e8-190">Utter the phrase “select the launch rocket button.”</span></span>

>  <span data-ttu-id="253e8-191">注意：應用程式識別所需的函式，並啟動 rocket 按鈕。</span><span class="sxs-lookup"><span data-stu-id="253e8-191">note: The app recognized the desired function and activated the rocket button.</span></span>
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="253e8-193">恭喜！</span><span class="sxs-lookup"><span data-stu-id="253e8-193">Congratulations</span></span>

<span data-ttu-id="253e8-194">正式，您了解如何從語音 SDK 程式新增語音命令 ！</span><span class="sxs-lookup"><span data-stu-id="253e8-194">You officially learned how to add speech commands from the speech SDK program!</span></span> <span data-ttu-id="253e8-195">現在您的程式可以辨識語音命令的各種變體。</span><span class="sxs-lookup"><span data-stu-id="253e8-195">Now your program can recognize speech commands of all kinds of variants.</span></span> <span data-ttu-id="253e8-196">測試它，並擁有一些有趣 ！</span><span class="sxs-lookup"><span data-stu-id="253e8-196">Test it out and have a little fun with it!</span></span>

[<span data-ttu-id="253e8-197">下一課：語音 SDK 第 5 課</span><span class="sxs-lookup"><span data-stu-id="253e8-197">Next Lesson: Speech SDK Lesson 5</span></span>](placeholderlink)

