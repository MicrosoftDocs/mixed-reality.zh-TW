---
title: Azure 語音服務教學課程-3。 新增 Azure 認知服務語音翻譯元件
description: 在此課程中，您將瞭解如何在混合現實應用程式中執行 Azure 語音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: dc5300b51ccb151a2e38f9d15b84a4a9031e2bb4
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143232"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="0730d-105">3. 新增 Azure 認知服務語音翻譯元件</span><span class="sxs-lookup"><span data-stu-id="0730d-105">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="0730d-106">在本教學課程中，您將瞭解專案的 Azure 認知服務語音翻譯元件，以及如何轉譯成三種不同的語言。</span><span class="sxs-lookup"><span data-stu-id="0730d-106">In this tutorial, you'll learn about the Azure Cognitive Services Speech Translation component of your project, as well as how to translate into three different languages.</span></span>

## <a name="instructions"></a><span data-ttu-id="0730d-107">指示</span><span class="sxs-lookup"><span data-stu-id="0730d-107">Instructions</span></span>

1. <span data-ttu-id="0730d-108">選取階層中的 [Lunarcom_Base] 物件，然後按一下 [偵測器] 面板中的 [新增元件]。</span><span class="sxs-lookup"><span data-stu-id="0730d-108">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the inspector panel.</span></span> <span data-ttu-id="0730d-109">搜尋並選取 [Lunarcom 轉譯辨識器]。</span><span class="sxs-lookup"><span data-stu-id="0730d-109">Search for and select Lunarcom Translation Recognizer.</span></span>

    ![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

    <span data-ttu-id="0730d-111">停用離線模式模擬器。</span><span class="sxs-lookup"><span data-stu-id="0730d-111">Disable the offline mode simulator.</span></span>

    ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

    >[!IMPORTANT]
    ><span data-ttu-id="0730d-113">在繼續之前，請先確定已停用離線模式模擬器（如上圖所示），再測試語音 SDK 轉譯程式。</span><span class="sxs-lookup"><span data-stu-id="0730d-113">Before moving on, ensure that the offline mode simulator is disabled (as shown in the image above) before testing the Speech-SDK translator.</span></span> <span data-ttu-id="0730d-114">您必須連線到網際網路，才能轉譯。</span><span class="sxs-lookup"><span data-stu-id="0730d-114">In order to translate, you must be connected to the internet.</span></span>

2. <span data-ttu-id="0730d-115">按一下 Lunarcom 轉譯辨識器中的下拉式選單，然後選取您想要翻譯成的語言。</span><span class="sxs-lookup"><span data-stu-id="0730d-115">Click the drop-down in the Lunarcom Translation Recognizer, and select the language you would like to translate to.</span></span>

    ![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. <span data-ttu-id="0730d-117">執行應用程式並按一下附屬按鈕來測試翻譯工具，然後開始說話。</span><span class="sxs-lookup"><span data-stu-id="0730d-117">Run the application and test the translator by clicking the Satellite button, and begin speaking.</span></span> <span data-ttu-id="0730d-118">再按一次 [衛星] 按鈕，以停止辨識。</span><span class="sxs-lookup"><span data-stu-id="0730d-118">Press the Satellite button again to stop the recognition.</span></span> <span data-ttu-id="0730d-119">以下是場景外觀的範例。</span><span class="sxs-lookup"><span data-stu-id="0730d-119">Below is an example of what your scene should look like.</span></span> <span data-ttu-id="0730d-120">請隨意變更 [目的語言] 下拉式清單下的語言（請參閱上方的影像），以探索其他語言的翻譯。</span><span class="sxs-lookup"><span data-stu-id="0730d-120">Feel free to change the language under the "Target Language" dropdown (see image above) to explore translation into other languages.</span></span>

    <span data-ttu-id="0730d-121">以下是場景看起來應該像這樣的範例：</span><span class="sxs-lookup"><span data-stu-id="0730d-121">Below is an example of what your scene should look like:</span></span>

    ![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="0730d-123">恭喜！</span><span class="sxs-lookup"><span data-stu-id="0730d-123">Congratulations</span></span>

<span data-ttu-id="0730d-124">您的專案現在可以成功地將您所說的單字轉譯成數種不同的語言。</span><span class="sxs-lookup"><span data-stu-id="0730d-124">Your project can now successfully translate the words you speak into several different languages.</span></span> <span data-ttu-id="0730d-125">歡迎您試著使用這些語言，並測試翻譯的正確性。</span><span class="sxs-lookup"><span data-stu-id="0730d-125">Feel free to play around with the languages, and test the accuracy of the translation.</span></span>

[<span data-ttu-id="0730d-126">下一個教學課程： 4. 設定意圖和自然語言理解</span><span class="sxs-lookup"><span data-stu-id="0730d-126">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)
