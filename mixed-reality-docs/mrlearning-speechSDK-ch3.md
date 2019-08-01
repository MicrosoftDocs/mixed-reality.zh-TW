---
title: Azure 語音服務教學課程-3。 新增 Azure 認知服務語音翻譯元件
description: 完成此課程, 以瞭解如何在混合現實應用程式中執行 Azure 語音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 27742702f7a274b3212cdf12c77d8acfa0a29834
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701831"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="057e8-105">3.新增 Azure 認知服務語音翻譯元件</span><span class="sxs-lookup"><span data-stu-id="057e8-105">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="057e8-106">在本教學課程中, 我們將瞭解如何 aabout 專案中的 Azure 認知服務語音翻譯元件, 並轉譯成三種不同的語言。</span><span class="sxs-lookup"><span data-stu-id="057e8-106">In this tutorial, we learn aabout the Azure Cognitive Services Speech Translation component in our project as well as translate into three different languages.</span></span> 

## <a name="instructions"></a><span data-ttu-id="057e8-107">指示</span><span class="sxs-lookup"><span data-stu-id="057e8-107">Instructions</span></span>

1. <span data-ttu-id="057e8-108">選取階層中的 [Lunarcom_Base] 物件, 然後按一下 [偵測器] 面板中的 [新增元件]。</span><span class="sxs-lookup"><span data-stu-id="057e8-108">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the inspector panel.</span></span> <span data-ttu-id="057e8-109">搜尋並選取 [LunarcomTranslationRecognizer]。</span><span class="sxs-lookup"><span data-stu-id="057e8-109">Search for and select LunarcomTranslationRecognizer.</span></span>

![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

> <span data-ttu-id="057e8-111">注意:請確定已停用離線模式模擬器, 然後再測試語音 SDK 轉譯程式。</span><span class="sxs-lookup"><span data-stu-id="057e8-111">Note: Ensure the offline mode simulator is disabled before testing the Speech-SDK translator.</span></span> <span data-ttu-id="057e8-112">您必須連線到網際網路, 才能轉譯。</span><span class="sxs-lookup"><span data-stu-id="057e8-112">In order to translate, you must be connected to the internet.</span></span> <span data-ttu-id="057e8-113">請參閱下方的影像, 尋找此設定的位置。</span><span class="sxs-lookup"><span data-stu-id="057e8-113">See image below on where to find this setting.</span></span> 
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

2. <span data-ttu-id="057e8-115">按一下 LunarcomTranslationRecognizer 中的下拉式選單, 然後選取您想要翻譯成的語言。</span><span class="sxs-lookup"><span data-stu-id="057e8-115">Click the drop-down in the LunarcomTranslationRecognizer, and select the language you would like to translate to.</span></span>

![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. <span data-ttu-id="057e8-117">現在, 請執行應用程式並按一下附屬按鈕來測試翻譯工具, 然後開始說話。</span><span class="sxs-lookup"><span data-stu-id="057e8-117">Now, run the application and test the translator by clicking the Satellite button, and begin speaking.</span></span> <span data-ttu-id="057e8-118">再按一次 [衛星] 按鈕, 以停止辨識。</span><span class="sxs-lookup"><span data-stu-id="057e8-118">Press the Satellite button again to stop the recognition.</span></span> <span data-ttu-id="057e8-119">以下是場景外觀的範例。</span><span class="sxs-lookup"><span data-stu-id="057e8-119">Below is an example of what your scene should look like.</span></span> <span data-ttu-id="057e8-120">請隨意變更 [目的語言] 下拉式清單下的語言 (請參閱上方的影像), 以探索其他語言的翻譯。</span><span class="sxs-lookup"><span data-stu-id="057e8-120">Feel free to change the language under the "Target Language" dropdown (see image above) to explore translation into other languages.</span></span>

> <span data-ttu-id="057e8-121">注意:在測試之前, 請確定已停用離線模擬器, 如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="057e8-121">Note: Before testing, ensure that the offline simulator is disabled, as shown in the image below.</span></span>
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

<span data-ttu-id="057e8-123">以下是場景看起來應該像這樣的範例:</span><span class="sxs-lookup"><span data-stu-id="057e8-123">Below is an example of what your scene should look like:</span></span>

![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="057e8-125">恭喜！</span><span class="sxs-lookup"><span data-stu-id="057e8-125">Congratulations</span></span>

<span data-ttu-id="057e8-126">您的專案現在可以將您所說的單字轉譯成數種不同的語言。</span><span class="sxs-lookup"><span data-stu-id="057e8-126">Now  your project can translate the words you speak into several different languages.</span></span> <span data-ttu-id="057e8-127">歡迎您試著使用這些語言, 並測試翻譯的正確性。</span><span class="sxs-lookup"><span data-stu-id="057e8-127">Feel free to play around with the languages, and test the accuracy of the translation.</span></span> 

[<span data-ttu-id="057e8-128">下一個教學課程:4.設定意圖和自然語言理解</span><span class="sxs-lookup"><span data-stu-id="057e8-128">Next tutorial: 4.  Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)

