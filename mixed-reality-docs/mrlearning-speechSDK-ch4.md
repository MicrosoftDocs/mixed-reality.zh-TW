---
title: Azure 語音服務教學課程 - 4。 設定意圖和自然語言理解
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 語音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: b2342e7d0d502af2787ca311d18a44f8726acf2d
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/10/2020
ms.locfileid: "79028551"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="3938d-105">4.設定意圖和自然語言理解</span><span class="sxs-lookup"><span data-stu-id="3938d-105">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="3938d-106">在本教學課程中，您將探索 Azure 語音服務的意圖辨識。</span><span class="sxs-lookup"><span data-stu-id="3938d-106">In this tutorial, you will explore the Azure Speech Service's intent recognition.</span></span> <span data-ttu-id="3938d-107">意圖辨識可讓您使用 AI 驅動的語音命令來裝備我們的應用程式，使用者可以說出非特定的語音命令，但系統仍可了解其意圖。</span><span class="sxs-lookup"><span data-stu-id="3938d-107">The intent recognition allows you to equip our application with AI-powered speech commands, where users can say non-specific speech commands and still have their intent understood by the system.</span></span>

## <a name="objectives"></a><span data-ttu-id="3938d-108">目標</span><span class="sxs-lookup"><span data-stu-id="3938d-108">Objectives</span></span>

* <span data-ttu-id="3938d-109">了解如何在 LUIS 入口網站中設定意圖、實體和語句</span><span class="sxs-lookup"><span data-stu-id="3938d-109">Learn how to set up intent, entities, and utterances in the LUIS portal</span></span>
* <span data-ttu-id="3938d-110">了解如何在我們的應用程式中實作意圖和自然語言理解</span><span class="sxs-lookup"><span data-stu-id="3938d-110">Learn how to implement intent and natural language understanding in our application</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="3938d-111">準備場景</span><span class="sxs-lookup"><span data-stu-id="3938d-111">Preparing the scene</span></span>

<span data-ttu-id="3938d-112">在 [階層] 視窗中選取 **Lunarcom** 物件，然後在 [偵測器] 視窗中使用 [新增元件]  按鈕來將 **Lunarcom Intent Recognizer (指令碼)** 元件新增至 Lunarcom 物件：</span><span class="sxs-lookup"><span data-stu-id="3938d-112">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Intent Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-1.png)

<span data-ttu-id="3938d-114">在 [專案] 視窗中，瀏覽至 [資產]   > [MRTK.Tutorials.GettingStarted]   > [Prefabs]   > [RocketLauncher]  資料夾，將 **RocketLauncher_Complete** Prefab 拖曳到您的 [階層] 視窗中，並將其放在相機前方的適當位置，例如：</span><span class="sxs-lookup"><span data-stu-id="3938d-114">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher_Complete** prefab into your Hierarchy window, and place it at a suitable location in front of the camera, for example:</span></span>

* <span data-ttu-id="3938d-115">變形**位置** X = 0、Y = -0.4、Z = 1</span><span class="sxs-lookup"><span data-stu-id="3938d-115">Transform **Position** X = 0, Y = -0.4, Z = 1</span></span>
* <span data-ttu-id="3938d-116">變形**旋轉** X = 0、Y = 90、Z = 0</span><span class="sxs-lookup"><span data-stu-id="3938d-116">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-2.png)

<span data-ttu-id="3938d-118">在 [階層] 視窗中，再次選取 [Lunarcom]  物件，然後展開 [RocketLauncher_Complete]   > [按鈕]  物件，並將每個**按鈕**物件的子物件指派至對應的 [月球發射器按鈕]  欄位：</span><span class="sxs-lookup"><span data-stu-id="3938d-118">In the Hierarchy window, select the **Lunarcom** object again, then expand the **RocketLauncher_Complete** > **Button** object and assign each of the **Buttons** object's child objects to the corresponding **Lunar Launcher Buttons** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-3.png)

## <a name="creating-the-azure-language-understanding-resource"></a><span data-ttu-id="3938d-120">建立 Azure Language Understanding 資源</span><span class="sxs-lookup"><span data-stu-id="3938d-120">Creating the Azure Language Understanding resource</span></span>

<span data-ttu-id="3938d-121">在本節中，您將為下一節要建立的 Language Understanding Intelligent Service (LUIS) 應用程式建立 Azure 預測資源。</span><span class="sxs-lookup"><span data-stu-id="3938d-121">In this section, you will create an Azure prediction resource for the Language Understanding Intelligent Service (LUIS) app you will create in the next section.</span></span>

<span data-ttu-id="3938d-122">登入 <a href="https://portal.azure.com" target="_blank">Azure</a>，然後按一下 [建立資源]  。</span><span class="sxs-lookup"><span data-stu-id="3938d-122">Sign in to <a href="https://portal.azure.com" target="_blank">Azure</a> and click **Create a resource**.</span></span> <span data-ttu-id="3938d-123">然後搜尋並選取 **Language Understanding**：</span><span class="sxs-lookup"><span data-stu-id="3938d-123">Then search for and select **Language Understanding**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-1.png)

<span data-ttu-id="3938d-125">按一下 [建立]  按鈕，以建立此服務的執行個體：</span><span class="sxs-lookup"><span data-stu-id="3938d-125">Click the **Create** button to create an instance of this service:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-2.png)

<span data-ttu-id="3938d-127">在 [建立] 頁面上，按一下 [預測]  選項，並輸入下列值：</span><span class="sxs-lookup"><span data-stu-id="3938d-127">On the Create page, click the **Prediction** option and enter the following values:</span></span>

* <span data-ttu-id="3938d-128">針對**訂用帳戶**，如果您有試用版訂用帳戶，請選取 [免費試用]  ，否則請選取其他訂用帳戶的其中一個</span><span class="sxs-lookup"><span data-stu-id="3938d-128">For **Subscription**, select **Free Trail** if you have a trial subscription, otherwise, select one of your other subscriptions</span></span>
* <span data-ttu-id="3938d-129">在 [資源群組]  中，按一下 [新建]  連結並輸入適當名稱 (例如 MRKT-Tutorials)  ，然後按一下 [確定] </span><span class="sxs-lookup"><span data-stu-id="3938d-129">For the **Resource group**, click the **Create new** link, enter a suitable name, for example, *MRKT-Tutorials*, and then click the **OK**</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="3938d-131">從撰寫本文的時間起，您不需要建立撰寫資源，因為當您在下一節中建立 Language Understanding Intelligent Service (LUIS) 時，系統會在 LUIS 內自動產生撰寫試用版金鑰。</span><span class="sxs-lookup"><span data-stu-id="3938d-131">As of the time of this writing, you do not need to create an authoring resource because an authoring trial key will automatically be generated within LUIS when you create the Language Understanding Intelligent Service (LUIS) in the next section.</span></span>

> [!TIP]
> <span data-ttu-id="3938d-132">如果您的 Azure 帳戶中已有另一個適當的資源群組 (例如，您已完成 [Azure Spatial Anchors](mrlearning-asa-ch1.md) 教學課程)，您就可以使用此資源群組，而不用建立新的資源群組。</span><span class="sxs-lookup"><span data-stu-id="3938d-132">If you already have another suitable resource group in your Azure account, for example, if you completed the [Azure Spatial Anchors](mrlearning-asa-ch1.md) tutorial, you may use this resource group instead of creating a new one.</span></span>

<span data-ttu-id="3938d-133">繼續在 [建立] 頁面上輸入下列值：</span><span class="sxs-lookup"><span data-stu-id="3938d-133">While still on the Create page, enter the following values:</span></span>

* <span data-ttu-id="3938d-134">針對 [名稱]  ，請為服務輸入適當的名稱，例如 MRTK-Tutorials-AzureSpeechServices </span><span class="sxs-lookup"><span data-stu-id="3938d-134">For **Name**, enter a suitable name for the service, for example, *MRTK-Tutorials-AzureSpeechServices*</span></span>
* <span data-ttu-id="3938d-135">針對 [預測位置]  ，請選擇接近應用程式使用者實體位置的位置，例如 [(美國) 美國西部] </span><span class="sxs-lookup"><span data-stu-id="3938d-135">For **Prediction location**, choose a location close to your app users' physical location, for example, *(US) West US*</span></span>
* <span data-ttu-id="3938d-136">針對 [預測定價層]  ，基於本教學課程的目的，請選取 [F0 (每秒 5 個呼叫，每月 10K 個呼叫)] </span><span class="sxs-lookup"><span data-stu-id="3938d-136">For **Prediction pricing tier**, for the purpose of this tutorial, select **F0 (5 Calls per second, 10K Calls per month)**</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-4.png)

<span data-ttu-id="3938d-138">接下來，移至 [檢閱 + 建立]  索引標籤，檢閱詳細資料後按一下頁面底部的 [建立]  按鈕，即可建立資源及新的資源群組 (如果您已設定要建立新的資源群組)：</span><span class="sxs-lookup"><span data-stu-id="3938d-138">Next, go to the **Review + create** tab, review the details, and then click the **Create** button, located at the bottom of the page, to create the resource, as well as, the new resource group if you configured one to be created:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-5.png)

> [!NOTE]
> <span data-ttu-id="3938d-140">按一下 [建立] 按鈕之後，您必須等候服務建立，這可能需要幾分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="3938d-140">After you click the Create button, you will have to wait for the service to be created, which might take a few minutes.</span></span>

<span data-ttu-id="3938d-141">資源建立程序完成後，您會看到**部署已完成**的訊息：</span><span class="sxs-lookup"><span data-stu-id="3938d-141">Once the resource creation process is completed, you will see the message **Your deployment is complete**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-6.png)

## <a name="creating-the-language-understanding-intelligent-service-luis"></a><span data-ttu-id="3938d-143">建立 Language Understanding Intelligent Service (LUIS)</span><span class="sxs-lookup"><span data-stu-id="3938d-143">Creating the Language Understanding Intelligent Service (LUIS)</span></span>

<span data-ttu-id="3938d-144">在本節中，您將建立 LUIS 應用程式、設定和訓練其預測模型，並將其連線至您在上一個步驟中建立的 Azure 預測資源。</span><span class="sxs-lookup"><span data-stu-id="3938d-144">In this section, you will create a LUIS app, configure and train its prediction model, and connect it to the Azure prediction resource you created in the previous step.</span></span>

<span data-ttu-id="3938d-145">具體而言，您將建立一個意圖，如果使用者說出應該採取的動作，則應用程式將會根據使用者所參考的按鈕，從場景中的三個紅色按鈕之一觸發 Interactable.OnClick() 事件。</span><span class="sxs-lookup"><span data-stu-id="3938d-145">Specifically, you will create an intent that if the user says an action should be taken, the app will trigger the Interactable.OnClick() event on one of the three red buttons in the scene, depending on which button the user references.</span></span>

<span data-ttu-id="3938d-146">例如，如果使用者說 "go ahead and launch the rocket" (繼續並發射火箭)  ，應用程式會預測 **go ahead** 代表應採取一些**動作**，以及預測**目標**的 Interactable.OnClick() 事件位於**啟動**按鈕上。</span><span class="sxs-lookup"><span data-stu-id="3938d-146">For example, if the user says **go ahead and launch the rocket**, the app will predict that **go ahead** means some **action** should be taken, and that the Interactable.OnClick() event to **target** is on the **launch** button.</span></span>

<span data-ttu-id="3938d-147">達成此動作所需採取的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="3938d-147">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="3938d-148">建立 LUIS 應用程式</span><span class="sxs-lookup"><span data-stu-id="3938d-148">Create a LUIS app</span></span>
2. <span data-ttu-id="3938d-149">建立意圖</span><span class="sxs-lookup"><span data-stu-id="3938d-149">Create intents</span></span>
3. <span data-ttu-id="3938d-150">建立範例語句</span><span class="sxs-lookup"><span data-stu-id="3938d-150">Create example utterances</span></span>
4. <span data-ttu-id="3938d-151">建立實體</span><span class="sxs-lookup"><span data-stu-id="3938d-151">Create entities</span></span>
5. <span data-ttu-id="3938d-152">將實體指派給範例語句</span><span class="sxs-lookup"><span data-stu-id="3938d-152">Assign entities to the example utterances</span></span>
6. <span data-ttu-id="3938d-153">訓練、測試及發佈應用程式</span><span class="sxs-lookup"><span data-stu-id="3938d-153">Train, test, and publish the app</span></span>
7. <span data-ttu-id="3938d-154">將 Azure 預測資源指派給應用程式</span><span class="sxs-lookup"><span data-stu-id="3938d-154">Assign an Azure prediction resource to the app</span></span>

### <a name="1-create-a-luis-app"></a><span data-ttu-id="3938d-155">1.建立 LUIS 應用程式</span><span class="sxs-lookup"><span data-stu-id="3938d-155">1. Create a LUIS app</span></span>

<span data-ttu-id="3938d-156">使用您在上一節中建立 Azure 資源時所使用的相同使用者帳戶登入 <a href="https://www.luis.ai" target="_blank">LUIS</a>，選取您的國家/地區並同意使用條款。</span><span class="sxs-lookup"><span data-stu-id="3938d-156">Using the same user account you used when creating the Azure resource in the previous section, sign in to <a href="https://www.luis.ai" target="_blank">LUIS</a>, select your country, and agree to the terms of use.</span></span> <span data-ttu-id="3938d-157">在下一個步驟中，當系統要求您**連結您的 Azure 帳戶**時，請選擇 **繼續使用您的試用金鑰**，改為使用 Azure 撰寫資源。</span><span class="sxs-lookup"><span data-stu-id="3938d-157">In the next step, when asked to **Link your Azure account**, choose **Continue using your trial key**, to use an Azure authoring resource instead.</span></span>

> [!NOTE]
> <span data-ttu-id="3938d-158">如果您已註冊 LUIS，而您的撰寫試用金鑰已過期，您可以參閱 [遷移至 Azure 資源撰寫金鑰](https://docs.microsoft.com/azure/cognitive-services/luis/luis-migration-authoring)文件，將您的 LUIS 撰寫資源切換為 Azure。</span><span class="sxs-lookup"><span data-stu-id="3938d-158">If you have already signed up for LUIS and your authoring trial key has expired, you can refer to the [Migrate to an Azure resource authoring key](https://docs.microsoft.com/azure/cognitive-services/luis/luis-migration-authoring) documentation to switch your LUIS authoring resource to Azure.</span></span>

<span data-ttu-id="3938d-159">登入後，瀏覽至 [我的應用程式]  頁面，然後按一下 [建立新的應用程式]  ，然後在 [建立新的應用程式]  快顯視窗中輸入下列值：</span><span class="sxs-lookup"><span data-stu-id="3938d-159">Once signed in, navigate to the **My apps** page, then click **Create new app** and enter the following values in the **Create new app** popup window:</span></span>

* <span data-ttu-id="3938d-160">針對 [名稱]  ，請輸入適當的名稱，例如 MRTK Tutorials - AzureSpeechServices </span><span class="sxs-lookup"><span data-stu-id="3938d-160">For **Name**, enter a suitable name, for example, *MRTK Tutorials - AzureSpeechServices*</span></span>
* <span data-ttu-id="3938d-161">針對 [文化特性]  ，請選取 [英文] </span><span class="sxs-lookup"><span data-stu-id="3938d-161">For **Culture**, select **English**</span></span>
* <span data-ttu-id="3938d-162">針對 [描述]  ，您可以選擇性地輸入適當描述</span><span class="sxs-lookup"><span data-stu-id="3938d-162">For **Description**, optionally enter a suitable description</span></span>

<span data-ttu-id="3938d-163">然後按一下 [完成]  按鈕來建立新的應用程式：</span><span class="sxs-lookup"><span data-stu-id="3938d-163">Then click the **Done** button to create the new app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-1.png)

<span data-ttu-id="3938d-165">建立新的應用程式之後，您會進入該應用程式的**儀表板**頁面：</span><span class="sxs-lookup"><span data-stu-id="3938d-165">When the new app has been created, you will be taken to that app's **Dashboard** page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-2.png)

### <a name="2-create-intents"></a><span data-ttu-id="3938d-167">2.建立意圖</span><span class="sxs-lookup"><span data-stu-id="3938d-167">2. Create intents</span></span>

<span data-ttu-id="3938d-168">從儀表板頁面瀏覽至 [組建] > [應用程式資產] > [意圖]  頁面，按一下 [建立新意圖]  ，然後在 [建立新意圖]  快顯視窗中輸入下列值：</span><span class="sxs-lookup"><span data-stu-id="3938d-168">From the Dashboard page, navigate to the Build > App Assets > **Intents** page, then click **Create new intent** and enter the following value in the **Create new intent** popup window:</span></span>

* <span data-ttu-id="3938d-169">針對 [意圖名稱]  ，請輸入 **PressButton**</span><span class="sxs-lookup"><span data-stu-id="3938d-169">For **Intent name**, enter **PressButton**</span></span>

<span data-ttu-id="3938d-170">然後按一下 [完成]  按鈕來建立新的意圖：</span><span class="sxs-lookup"><span data-stu-id="3938d-170">Then click the **Done** button to create the new intent:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-1.png)

> [!CAUTION]
> <span data-ttu-id="3938d-172">基於本教學課程的目的，您的 Unity 專案會依據名稱來參考此意圖，亦即：'PressButton'。</span><span class="sxs-lookup"><span data-stu-id="3938d-172">For the purpose of this tutorial, your Unity project will reference this intent by its name, i.e. 'PressButton'.</span></span> <span data-ttu-id="3938d-173">因此，請務必將您的意圖命名為完全相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="3938d-173">Consequently, it is extremely important that you name your intent exactly the same.</span></span>

<span data-ttu-id="3938d-174">建立新的意圖之後，您會進入該意圖的頁面：</span><span class="sxs-lookup"><span data-stu-id="3938d-174">When the new intent has been created, you will be taken to that intent's page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-2.png)

### <a name="3-create-example-utterances"></a><span data-ttu-id="3938d-176">3.建立範例語句</span><span class="sxs-lookup"><span data-stu-id="3938d-176">3. Create example utterances</span></span>

<span data-ttu-id="3938d-177">前往 **PressButton** 意圖的**範例語句**清單，並新增下列範例語句：</span><span class="sxs-lookup"><span data-stu-id="3938d-177">To the **PressButton** intent's **Example utterance** list, add the following example utterances:</span></span>

* <span data-ttu-id="3938d-178">activate launch sequence (啟動發射順序)</span><span class="sxs-lookup"><span data-stu-id="3938d-178">activate launch sequence</span></span>
* <span data-ttu-id="3938d-179">show me a placement hint (顯示位置提示)</span><span class="sxs-lookup"><span data-stu-id="3938d-179">show me a placement hint</span></span>
* <span data-ttu-id="3938d-180">initiate the launch sequence (起始發射順序)</span><span class="sxs-lookup"><span data-stu-id="3938d-180">initiate the launch sequence</span></span>
* <span data-ttu-id="3938d-181">press placement hints button (按下位置提示按鈕)</span><span class="sxs-lookup"><span data-stu-id="3938d-181">press placement hints button</span></span>
* <span data-ttu-id="3938d-182">give me a hint (給我一個提示)</span><span class="sxs-lookup"><span data-stu-id="3938d-182">give me a hint</span></span>
* <span data-ttu-id="3938d-183">push the launch button (按下啟動按鈕)</span><span class="sxs-lookup"><span data-stu-id="3938d-183">push the launch button</span></span>
* <span data-ttu-id="3938d-184">i need a hint (我需要提示)</span><span class="sxs-lookup"><span data-stu-id="3938d-184">i need a hint</span></span>
* <span data-ttu-id="3938d-185">press the reset button (按下重設按鈕)</span><span class="sxs-lookup"><span data-stu-id="3938d-185">press the reset button</span></span>
* <span data-ttu-id="3938d-186">time to reset the experience (重設體驗的時機)</span><span class="sxs-lookup"><span data-stu-id="3938d-186">time to reset the experience</span></span>
* <span data-ttu-id="3938d-187">go ahead and launch the rocket (繼續並發射火箭)</span><span class="sxs-lookup"><span data-stu-id="3938d-187">go ahead and launch the rocket</span></span>

<span data-ttu-id="3938d-188">新增所有範例語句之後，您的 PressButton 意圖頁面看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="3938d-188">When all the example utterances have been added, your PressButton intent page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step3-1.png)

> [!CAUTION]
> <span data-ttu-id="3938d-190">基於本教學課程的目的，您的 Unity 專案會參考以下單字：'hint' (提示)、'hints' (提示)、'reset' (重設) 和 'launch' (發射)。</span><span class="sxs-lookup"><span data-stu-id="3938d-190">For the purpose of this tutorial, your Unity project will reference the words 'hint', 'hints', 'reset', and 'launch'.</span></span> <span data-ttu-id="3938d-191">因此，請務必以完全相同的方式來拼寫這些單字。</span><span class="sxs-lookup"><span data-stu-id="3938d-191">Consequently, it is extremely important that you spell these words in the exact same way.</span></span>

### <a name="4-create-entities"></a><span data-ttu-id="3938d-192">4.建立實體</span><span class="sxs-lookup"><span data-stu-id="3938d-192">4. Create entities</span></span>

<span data-ttu-id="3938d-193">從 PressButton 意圖頁面瀏覽至 [組建] > [應用程式資產] > [實體]  頁面，按一下 [建立新實體]  ，然後在 [建立新實體]  快顯視窗中輸入下列值：</span><span class="sxs-lookup"><span data-stu-id="3938d-193">From the PressButton intent page, navigate to the Build > App Assets > **Entities** page, then click **Create new entity** and enter the following values in the **Create new entity** popup window:</span></span>

* <span data-ttu-id="3938d-194">在 [實體名稱]  中，輸入**動作**</span><span class="sxs-lookup"><span data-stu-id="3938d-194">For **Entity name**, enter **Action**</span></span>
* <span data-ttu-id="3938d-195">針對 [實體類型]  ，請選取 [簡單] </span><span class="sxs-lookup"><span data-stu-id="3938d-195">For **Entity type**, select **Simple**</span></span>

<span data-ttu-id="3938d-196">然後按一下 [完成]  按鈕來建立新的實體：</span><span class="sxs-lookup"><span data-stu-id="3938d-196">Then click the **Done** button to create the new entity:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-1.png)

<span data-ttu-id="3938d-198">**重複**上一個步驟來建立名為**目標**的另一個實體，因此您有名為「動作」和「目標」的兩個實體：</span><span class="sxs-lookup"><span data-stu-id="3938d-198">**Repeat** the previous step to create another entity named **Target**, so you have two entities named Action and Target:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-2.png)

> [!CAUTION]
> <span data-ttu-id="3938d-200">基於本教學課程的目的，您的 Unity 專案會依據名稱來參考這些實體，亦即：「動作」與「目標」。</span><span class="sxs-lookup"><span data-stu-id="3938d-200">For the purpose of this tutorial, your Unity project will reference these entities by their names, i.e. 'Action' and 'Target'.</span></span> <span data-ttu-id="3938d-201">因此，請務必將您的實體命名為完全相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="3938d-201">Consequently, it is extremely important that you name your entities exactly the same.</span></span>

### <a name="5-assign-entities-to-the-example-utterances"></a><span data-ttu-id="3938d-202">5.將實體指派給範例語句</span><span class="sxs-lookup"><span data-stu-id="3938d-202">5. Assign entities to the example utterances</span></span>

<span data-ttu-id="3938d-203">在 [實體] 頁面上，瀏覽回到 **PressButton** 意圖頁面。</span><span class="sxs-lookup"><span data-stu-id="3938d-203">From the Entities page, navigate back to the **PressButton** intent page.</span></span>

<span data-ttu-id="3938d-204">回到 PressButton 意圖頁面之後，按一下單字 **go**，然後再按一下單字 **ahead**，接著從內容快顯功能表中選取 [動作 (簡單)]  ，將 **go ahead** 標示為**動作**實體值：</span><span class="sxs-lookup"><span data-stu-id="3938d-204">Once back on the the PressButton intent page, click on the word **go** and then on the word **ahead**, and then select **Action (Simple)** from the contextual popup menu to label **go ahead** as an **Action** entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-1.png)

<span data-ttu-id="3938d-206">**go ahead** 片語現在已定義為**動作**實體值。</span><span class="sxs-lookup"><span data-stu-id="3938d-206">The **go ahead** phrase is now defined as an **Action** entity value.</span></span> <span data-ttu-id="3938d-207">如果您將滑鼠游標暫留在動作實體名稱上方，您可以看到相關的動作實體值：</span><span class="sxs-lookup"><span data-stu-id="3938d-207">If you hover your mouse cursor above the Action entity name, you can see the associated Action entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-2.png)

> [!NOTE]
> <span data-ttu-id="3938d-209">上圖中顯示在標籤底下的紅線表示尚未對實體值進行預測，當您在下一節中訓練模型時，此問題就會解決。</span><span class="sxs-lookup"><span data-stu-id="3938d-209">The red line you see under the label in the image above indicates that the entity value has not been predicted, this will be resolved when you train the model in the next section.</span></span>

<span data-ttu-id="3938d-210">接下來，按一下單字 **launch**，然後從內容快顯功能表中選取 [目標 (簡單)]  ，將  標記為**目標**實體值：</span><span class="sxs-lookup"><span data-stu-id="3938d-210">Next, click on the word **launch**, and then select **Target (Simple)** from the contextual popup menu to label **launch** as a **Target** entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-3.png)

<span data-ttu-id="3938d-212">單字 **launch**現在已定義為**目標**實體值。</span><span class="sxs-lookup"><span data-stu-id="3938d-212">The **launch** word is now defined as a **Target** entity value.</span></span> <span data-ttu-id="3938d-213">如果您將滑鼠游標暫留在目標實體名稱上方，您可以看到相關的目標實體值：</span><span class="sxs-lookup"><span data-stu-id="3938d-213">If you hover your mouse cursor above the Target entity name, you can see the associated Target entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-4.png)

<span data-ttu-id="3938d-215">PressButton 意圖範例語句 'go ahead and launch the rocket' 現在已設定為可進行預測，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3938d-215">The PressButton intent example utterance 'go ahead and launch the rocket' is now configured to be predicted as follows:</span></span>

* <span data-ttu-id="3938d-216">意圖：PressButton</span><span class="sxs-lookup"><span data-stu-id="3938d-216">Intent: PressButton</span></span>
* <span data-ttu-id="3938d-217">動作實體：go ahead</span><span class="sxs-lookup"><span data-stu-id="3938d-217">Action entity: go ahead</span></span>
* <span data-ttu-id="3938d-218">目標實體：launch</span><span class="sxs-lookup"><span data-stu-id="3938d-218">Target entity: launch</span></span>

<span data-ttu-id="3938d-219">**重複**前兩個步驟的程序，將動作和目標實體標籤指派給每一個範例語句，請記住，下列單字應該標示為**目標**實體：</span><span class="sxs-lookup"><span data-stu-id="3938d-219">**Repeat** the previous two-step process to assign an Action and a Target entity label to each of the example utterances, keeping in mind that the following words should be labeled as **Target** entities:</span></span>

* <span data-ttu-id="3938d-220">**hint** (以 Unity 專案中的 HintsButton 為目標)</span><span class="sxs-lookup"><span data-stu-id="3938d-220">**hint** (targets the HintsButton in the Unity project)</span></span>
* <span data-ttu-id="3938d-221">**hints** (以 Unity 專案中的 HintsButton 目標)</span><span class="sxs-lookup"><span data-stu-id="3938d-221">**hints** (targets HintsButton in the Unity project)</span></span>
* <span data-ttu-id="3938d-222">**reset** (以 Unity 專案中的 ResetButton 為目標)</span><span class="sxs-lookup"><span data-stu-id="3938d-222">**reset** (targets the ResetButton in the Unity project)</span></span>
* <span data-ttu-id="3938d-223">**launch** (以 Unity 專案中的 LaunchButton 為目標)</span><span class="sxs-lookup"><span data-stu-id="3938d-223">**launch** (targets the LaunchButton in the Unity project)</span></span>

<span data-ttu-id="3938d-224">標記所有範例語句之後，您的 PressButton 意圖頁面看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="3938d-224">When all the example utterances have been labeled, your PressButton intent page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-5.png)

<span data-ttu-id="3938d-226">如需其他方法來再次檢查您是否已指派正確實體，請按一下 [檢視選項]  功能表，並將此檢視切換為 [顯示實體值]  ：</span><span class="sxs-lookup"><span data-stu-id="3938d-226">For an alternative way to double-check that you have assigned the correct entities, click the **View options** menu and switch the view to **Show entity values**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-6.png)

<span data-ttu-id="3938d-228">現在，當檢視設定為顯示實體值時，您可以將滑鼠游標停留在加上標籤的單字和片語上，以快速驗證指派的實體名稱：</span><span class="sxs-lookup"><span data-stu-id="3938d-228">Now, with the view set to show entity values, you can hover the mouse courser over the labeled words and phrases to quickly verify the assigned entity name:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-7.png)

### <a name="6-train-test-and-publish-the-app"></a><span data-ttu-id="3938d-230">6.訓練、測試及發佈應用程式</span><span class="sxs-lookup"><span data-stu-id="3938d-230">6. Train, test, and publish the app</span></span>

<span data-ttu-id="3938d-231">若要訓練應用程式，請按一下 [訓練]  按鈕，並等候訓練程序完成：</span><span class="sxs-lookup"><span data-stu-id="3938d-231">To train the app, click the **Train** button and wait for the training process to complete:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-1.png)

> [!NOTE]
> <span data-ttu-id="3938d-233">如您在上圖中所見，所有標籤底下的紅線都已移除，這表示我們已對所有實體值進行預測。</span><span class="sxs-lookup"><span data-stu-id="3938d-233">As you can see in the image above, the red lines under all the labels have been removed, indicating that all the entity values have been predicted.</span></span> <span data-ttu-id="3938d-234">另請注意，[訓練] 按鈕左邊的狀態圖示已從紅色變更為綠色。</span><span class="sxs-lookup"><span data-stu-id="3938d-234">Also notice that the status icon to the left of the Train button has changed color from red to green.</span></span>

<span data-ttu-id="3938d-235">當訓練程序完成時，請按一下 [測試]  按鈕，然後輸入 **go ahead and launch the rocket** 並按下 Enter 鍵：</span><span class="sxs-lookup"><span data-stu-id="3938d-235">When the training is finished processing, click the **Test** button, then type in **go ahead and launch the rocket** and press the Enter key:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-2.png)

<span data-ttu-id="3938d-237">測試語句處理完成後，請按一下 [檢查]  來查看測試結果：</span><span class="sxs-lookup"><span data-stu-id="3938d-237">When the test utterance has been processed, click **Inspect** to see the test result:</span></span>

* <span data-ttu-id="3938d-238">意圖：PressButton (98.5% 的確定性)</span><span class="sxs-lookup"><span data-stu-id="3938d-238">Intent: PressButton (with a 98.5% certainty)</span></span>
* <span data-ttu-id="3938d-239">動作實體：go ahead</span><span class="sxs-lookup"><span data-stu-id="3938d-239">Action entity: go ahead</span></span>
* <span data-ttu-id="3938d-240">目標實體：launch</span><span class="sxs-lookup"><span data-stu-id="3938d-240">Target entity: launch</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-3.png)

<span data-ttu-id="3938d-242">若要發佈應用程式，請按一下右上方的 [發佈]  按鈕，然後在 [選擇發佈位置和設定]  快顯視窗中選取 [生產]  ，然後按一下 [發佈]  按鈕：</span><span class="sxs-lookup"><span data-stu-id="3938d-242">To publish the app, click the **Publish** button in the top right, then in the **Choose your publishing slot and settings** popup window, select **Production** and click the **Publish** button:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-4.png)

<span data-ttu-id="3938d-244">等待發佈程序完成：</span><span class="sxs-lookup"><span data-stu-id="3938d-244">Wait for the publishing process to complete:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-5.png)

### <a name="7-assign-an-azure-prediction-resource-to-the-app"></a><span data-ttu-id="3938d-246">7.將 Azure 預測資源指派給應用程式</span><span class="sxs-lookup"><span data-stu-id="3938d-246">7. Assign an Azure prediction resource to the app</span></span>

<span data-ttu-id="3938d-247">瀏覽至 [管理] > [應用程式設定] > [Azure 資源]  頁面：</span><span class="sxs-lookup"><span data-stu-id="3938d-247">Navigate to the Manage > Application Settings > **Azure Resources** page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-1.png)

<span data-ttu-id="3938d-249">在 Azure 資源頁面上，按一下 [新增預測資源]  按鈕，然後在 [將資源指派給您的應用程式]  快顯視窗中選取下列值：</span><span class="sxs-lookup"><span data-stu-id="3938d-249">On the Azure Resources page, click the **Add prediction resource** button and select the following values in the **Assign a resource to your app** popup window:</span></span>

* <span data-ttu-id="3938d-250">針對 [租用戶名稱]  ，請選取您的租用戶名稱</span><span class="sxs-lookup"><span data-stu-id="3938d-250">For **Tenant name**, select your tenant name</span></span>
* <span data-ttu-id="3938d-251">針對 [訂用帳戶名稱]  ，請選取您稍早[建立 Azure Language Understanding 資源](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)時使用的相同訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="3938d-251">For **Subscription Name**, select the same subscription you used earlier when [Creating the Azure Language Understanding resource](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)</span></span>
* <span data-ttu-id="3938d-252">針對 [LUIS 資源名稱]  ，請選取您稍早[建立 Azure Language Understanding 資源時](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)建立的預測資源</span><span class="sxs-lookup"><span data-stu-id="3938d-252">For **LUIS resource name**, select the prediction resource you created earlier when [Creating the Azure Language Understanding resource](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)</span></span>

<span data-ttu-id="3938d-253">然後按一下 [指派資源]  按鈕，將 Azure 預測資源指派給您的應用程式：</span><span class="sxs-lookup"><span data-stu-id="3938d-253">Then click the **Assign resource** button to assign the Azure prediction resource to your app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-2.png)

<span data-ttu-id="3938d-255">指派資源之後，您的 Azure 資源頁面看起來應該會像這樣：</span><span class="sxs-lookup"><span data-stu-id="3938d-255">When the resource has been assigned, your Azure Resources page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-3.png)

## <a name="connecting-the-unity-project-to-the-luis-app"></a><span data-ttu-id="3938d-257">將 Unity 專案連線至 LUIS 應用程式</span><span class="sxs-lookup"><span data-stu-id="3938d-257">Connecting the Unity project to the LUIS app</span></span>

<span data-ttu-id="3938d-258">在 [管理] > [應用程式設定] > [Azure 資源]  頁面上，按一下**複製**圖示來複製**查詢範例**：</span><span class="sxs-lookup"><span data-stu-id="3938d-258">On the Manage > Application Settings > **Azure Resources** page, click the **copy** icon to copy the **Example Query**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-1.png)

<span data-ttu-id="3938d-260">回到 Unity 專案，在 [階層] 視窗中選取 **Lunarcom** 物件，然後在 [偵測器] 視窗中尋找 **Lunarcom Intent Recognizer (指令碼)** 元件並進行設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3938d-260">Back in your Unity project, in the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Intent Recognizer (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="3938d-261">在 [LUIS 端點]  欄位中，貼上您在上一個步驟中複製的**查詢範例**：</span><span class="sxs-lookup"><span data-stu-id="3938d-261">In the **LUIS Endpoint** field, past the **Example Query** you copied in the previous step:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-2.png)

## <a name="testing-and-improving-the-intent-recognition"></a><span data-ttu-id="3938d-263">測試和改善意圖辨識</span><span class="sxs-lookup"><span data-stu-id="3938d-263">Testing and improving the intent recognition</span></span>

<span data-ttu-id="3938d-264">若要直接在 Unity 編輯器中使用意圖辨識，您必須允許您的開發電腦使用聽寫。</span><span class="sxs-lookup"><span data-stu-id="3938d-264">To use intent recognition directly in the Unity editor, you must allow your development computer to use dictation.</span></span> <span data-ttu-id="3938d-265">若要確認此設定是否開啟，請開啟 Windows 的 [設定]  ，然後選擇 [隱私權]   > [語音]  ，並確定 [線上語音辨識]  已開啟：</span><span class="sxs-lookup"><span data-stu-id="3938d-265">To verify this setting, open Windows **Settings** then choose **Privacy** > **Speech** and ensure **Online speech recognition** is turned on:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-1.png)

<span data-ttu-id="3938d-267">如果您現在進入遊戲模式，您可以先按下火箭按鈕來測試意圖辨識。</span><span class="sxs-lookup"><span data-stu-id="3938d-267">If you now enter Game mode, you can test the intent recognition by first pressing the rocket button.</span></span> <span data-ttu-id="3938d-268">然後，假設您的電腦有麥克風，當您說出第一個範例語句：**go ahead and launch the rocket**時，您就會看到 LunarModule 發射至太空中：</span><span class="sxs-lookup"><span data-stu-id="3938d-268">Then, assuming your computer has a microphone, when you say the first example utterance, **go ahead and launch the rocket**, you will see the LunarModule launch into space:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-2.png)

<span data-ttu-id="3938d-270">請嘗試所有**範例語句**，然後嘗試一些**有變化的範例語句**變體，以及幾個**隨機語句**。</span><span class="sxs-lookup"><span data-stu-id="3938d-270">Try all the **example utterances**, then some **variation of the example utterances**, as well as, a few **random utterances**.</span></span>

<span data-ttu-id="3938d-271">接下來，返回 <a href="https://www.luis.ai" target="_blank">LUIS</a> 並瀏覽至 [組建] > [改善應用程式效能] >[檢閱端點語句]  頁面，使用**切換**按鈕從 [預設實體] 檢視切換至 [語彙基元檢視]  ，然檢閱語句：</span><span class="sxs-lookup"><span data-stu-id="3938d-271">Next, return to <a href="https://www.luis.ai" target="_blank">LUIS</a> and navigate to Build > Improve app performance > **Review endpoint utterances** page, use the **toggle** button to switch from the default Entities View to **Tokens View**, and then review the utterances:</span></span>

* <span data-ttu-id="3938d-272">在 [語句]  資料行中，視需要變更即移除指派的標籤，使其符合您的意圖</span><span class="sxs-lookup"><span data-stu-id="3938d-272">In the **Utterance** column, change and remove the assigned labels as needed so they align with your intent</span></span>
* <span data-ttu-id="3938d-273">在 [符合的意圖]  資料行中，確認意圖是否正確</span><span class="sxs-lookup"><span data-stu-id="3938d-273">In the **Aligned intent** column, verify that the intent is correct</span></span>
* <span data-ttu-id="3938d-274">在 [新增/刪除]  資料行中，按一下綠色核取記號按鈕來新增語句，或按一下紅色 x 按鈕來將其刪除</span><span class="sxs-lookup"><span data-stu-id="3938d-274">In the **Add/Delete** column, click the green check mark button to add the utterance or the red x button to delete it</span></span>

<span data-ttu-id="3938d-275">當您依據需求檢閱多個語句之後，請按一下 [訓練]  按鈕來重新訓練模型，然後按一下 [發佈]  按鈕來重新發佈更新的應用程式：</span><span class="sxs-lookup"><span data-stu-id="3938d-275">When you have reviewed as many utterances as you like, click the **Train** button to retrain the model, then the **Publish** button to republish the updated app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-3.png)

> [!NOTE]
> <span data-ttu-id="3938d-277">如果端點語句未與 PressButton 意圖一致，但您希望模型知道語句沒有意圖，您可以將符合的意圖變更為 [無]。</span><span class="sxs-lookup"><span data-stu-id="3938d-277">If an endpoint utterance does not align with the PressButton intent, but you would like your model to know that the utterance has no intent, you can change the Aligned intent to None.</span></span>

<span data-ttu-id="3938d-278">您可以依據需求來多次**重覆**此程序，以達到改善應用程式模型的目的。</span><span class="sxs-lookup"><span data-stu-id="3938d-278">**Repeat** this process as many times as you like to improve your app model.</span></span>

## <a name="congratulations"></a><span data-ttu-id="3938d-279">恭喜！</span><span class="sxs-lookup"><span data-stu-id="3938d-279">Congratulations</span></span>

<span data-ttu-id="3938d-280">您的專案現在已具備 AI 驅動的語音命令，可讓您的應用程式辨識使用者的意圖 (即使使用者沒有十分精確地傳達命令)。</span><span class="sxs-lookup"><span data-stu-id="3938d-280">Your project now have AI-powered speech commands, allowing your application to recognize the users' intent even if they do not utter precise commands.</span></span> <span data-ttu-id="3938d-281">在您的裝置上執行應用程式，以確保功能可正常運作。</span><span class="sxs-lookup"><span data-stu-id="3938d-281">Run the application on your device to ensure the feature is working properly.</span></span>
