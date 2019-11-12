---
title: Azure 語音服務教學課程-3。 新增 Azure 認知服務語音翻譯元件
description: 完成此課程，以瞭解如何在混合現實應用程式中執行 Azure 語音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 490b9f6142208a190748b6d76c57be493172c1e5
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913206"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="2fd3a-105">3. 新增 Azure 認知服務語音翻譯元件</span><span class="sxs-lookup"><span data-stu-id="2fd3a-105">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="2fd3a-106">在本教學課程中，我們將瞭解專案中的 Azure 認知服務語音翻譯元件，並轉譯成三種不同的語言。</span><span class="sxs-lookup"><span data-stu-id="2fd3a-106">In this tutorial, we learn about the Azure Cognitive Services Speech Translation component in our project as well as translate into three different languages.</span></span>

## <a name="instructions"></a><span data-ttu-id="2fd3a-107">指示</span><span class="sxs-lookup"><span data-stu-id="2fd3a-107">Instructions</span></span>

1. <span data-ttu-id="2fd3a-108">選取階層中的 [Lunarcom_Base] 物件，然後按一下 [偵測器] 面板中的 [新增元件]。</span><span class="sxs-lookup"><span data-stu-id="2fd3a-108">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the inspector panel.</span></span> <span data-ttu-id="2fd3a-109">搜尋並選取 [Lunarcom 轉譯辨識器]。</span><span class="sxs-lookup"><span data-stu-id="2fd3a-109">Search for and select Lunarcom Translation Recognizer.</span></span>

    ![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

    <span data-ttu-id="2fd3a-111">停用離線模式模擬器。</span><span class="sxs-lookup"><span data-stu-id="2fd3a-111">Disable the offline mode simulator.</span></span>

    ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

    >[!IMPORTANT]
    ><span data-ttu-id="2fd3a-113">在繼續之前，請先確定已停用離線模式模擬器（如上圖所示），然後再測試語音 SDK 轉譯程式。</span><span class="sxs-lookup"><span data-stu-id="2fd3a-113">Before moving on, ensure the offline mode simulator is disabled, as shown in the image above, before testing the Speech-SDK translator.</span></span> <span data-ttu-id="2fd3a-114">您必須連線到網際網路，才能轉譯。</span><span class="sxs-lookup"><span data-stu-id="2fd3a-114">In order to translate, you must be connected to the internet.</span></span>

2. <span data-ttu-id="2fd3a-115">按一下 Lunarcom 轉譯辨識器中的下拉式選單，然後選取您想要翻譯成的語言。</span><span class="sxs-lookup"><span data-stu-id="2fd3a-115">Click the drop-down in the Lunarcom Translation Recognizer, and select the language you would like to translate to.</span></span>

    ![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. <span data-ttu-id="2fd3a-117">現在，請執行應用程式並按一下附屬按鈕來測試翻譯工具，然後開始說話。</span><span class="sxs-lookup"><span data-stu-id="2fd3a-117">Now, run the application and test the translator by clicking the Satellite button, and begin speaking.</span></span> <span data-ttu-id="2fd3a-118">再按一次 [衛星] 按鈕，以停止辨識。</span><span class="sxs-lookup"><span data-stu-id="2fd3a-118">Press the Satellite button again to stop the recognition.</span></span> <span data-ttu-id="2fd3a-119">以下是場景外觀的範例。</span><span class="sxs-lookup"><span data-stu-id="2fd3a-119">Below is an example of what your scene should look like.</span></span> <span data-ttu-id="2fd3a-120">請隨意變更 [目的語言] 下拉式清單下的語言（請參閱上方的影像），以探索其他語言的翻譯。</span><span class="sxs-lookup"><span data-stu-id="2fd3a-120">Feel free to change the language under the "Target Language" dropdown (see image above) to explore translation into other languages.</span></span>

    <span data-ttu-id="2fd3a-121">以下是場景看起來應該像這樣的範例：</span><span class="sxs-lookup"><span data-stu-id="2fd3a-121">Below is an example of what your scene should look like:</span></span>

    ![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="2fd3a-123">恭喜！</span><span class="sxs-lookup"><span data-stu-id="2fd3a-123">Congratulations</span></span>

<span data-ttu-id="2fd3a-124">您的專案現在可以將您所說的單字轉譯成數種不同的語言。</span><span class="sxs-lookup"><span data-stu-id="2fd3a-124">Now your project can translate the words you speak into several different languages.</span></span> <span data-ttu-id="2fd3a-125">歡迎您試著使用這些語言，並測試翻譯的正確性。</span><span class="sxs-lookup"><span data-stu-id="2fd3a-125">Feel free to play around with the languages, and test the accuracy of the translation.</span></span>

[<span data-ttu-id="2fd3a-126">下一個教學課程： 4. 設定意圖和自然語言理解</span><span class="sxs-lookup"><span data-stu-id="2fd3a-126">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)
