---
title: MR 學習 Speechsdk.quickstart 模組-語音辨識與轉譯
description: 完成此課程, 以瞭解如何在混合現實應用程式中執行 Azure 語音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: e5d0919a69c9e6b0c4233d23bf6d370f3def6576
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460316"
---
# <a name="3----adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="f0a6c-104">3.  新增 Azure 認知服務語音翻譯元件</span><span class="sxs-lookup"><span data-stu-id="f0a6c-104">3.    Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="f0a6c-105">在本教學課程中, 我們將瞭解如何 aabout 專案中的 Azure 認知服務語音翻譯元件, 並轉譯成三種不同的語言。</span><span class="sxs-lookup"><span data-stu-id="f0a6c-105">In this tutorial, we learn aabout the Azure Cognitive Services Speech Translation component in our project as well as translate into three different languages.</span></span> 

1. <span data-ttu-id="f0a6c-106">選取階層中的 [Lunarcom_Base] 物件, 然後按一下 [偵測器] 面板中的 [新增元件]。</span><span class="sxs-lookup"><span data-stu-id="f0a6c-106">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the inspector panel.</span></span> <span data-ttu-id="f0a6c-107">搜尋並選取 [LunarcomTranslationRecognizer]。</span><span class="sxs-lookup"><span data-stu-id="f0a6c-107">Search for and select LunarcomTranslationRecognizer.</span></span>

![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

> <span data-ttu-id="f0a6c-109">注意:請確定已停用離線模式模擬器, 然後再測試語音 SDK 轉譯程式。</span><span class="sxs-lookup"><span data-stu-id="f0a6c-109">Note: Ensure the offline mode simulator is disabled before testing the Speech-SDK translator.</span></span> <span data-ttu-id="f0a6c-110">您必須連線到網際網路, 才能轉譯。</span><span class="sxs-lookup"><span data-stu-id="f0a6c-110">In order to translate, you must be connected to the internet.</span></span> <span data-ttu-id="f0a6c-111">請參閱下方的影像, 尋找此設定的位置。</span><span class="sxs-lookup"><span data-stu-id="f0a6c-111">See image below on where to find this setting.</span></span> 
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

2. <span data-ttu-id="f0a6c-113">按一下 LunarcomTranslationRecognizer 中的下拉式選單, 然後選取您想要翻譯成的語言。</span><span class="sxs-lookup"><span data-stu-id="f0a6c-113">Click the drop-down in the LunarcomTranslationRecognizer, and select the language you would like to translate to.</span></span>

![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. <span data-ttu-id="f0a6c-115">現在, 請執行應用程式並按一下附屬按鈕來測試翻譯工具, 然後開始說話。</span><span class="sxs-lookup"><span data-stu-id="f0a6c-115">Now, run the application and test the translator by clicking the Satellite button, and begin speaking.</span></span> <span data-ttu-id="f0a6c-116">再按一次 [衛星] 按鈕, 以停止辨識。</span><span class="sxs-lookup"><span data-stu-id="f0a6c-116">Press the Satellite button again to stop the recognition.</span></span> <span data-ttu-id="f0a6c-117">以下是場景外觀的範例。</span><span class="sxs-lookup"><span data-stu-id="f0a6c-117">Below is an example of what your scene should look like.</span></span> <span data-ttu-id="f0a6c-118">請隨意變更 [目的語言] 下拉式清單下的語言 (請參閱上方的影像), 以探索其他語言的翻譯。</span><span class="sxs-lookup"><span data-stu-id="f0a6c-118">Feel free to change the language under the "Target Language" dropdown (see image above) to explore translation into other languages.</span></span>

> <span data-ttu-id="f0a6c-119">注意:在測試之前, 請確定已停用離線模擬器, 如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="f0a6c-119">Note: Before testing, ensure that the offline simulator is disabled, as shown in the image below.</span></span>
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

<span data-ttu-id="f0a6c-121">以下是場景看起來應該像這樣的範例:</span><span class="sxs-lookup"><span data-stu-id="f0a6c-121">Below is an example of what your scene should look like:</span></span>

![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="f0a6c-123">恭喜！</span><span class="sxs-lookup"><span data-stu-id="f0a6c-123">Congratulations</span></span>

<span data-ttu-id="f0a6c-124">您的專案現在可以將您所說的單字轉譯成數種不同的語言。</span><span class="sxs-lookup"><span data-stu-id="f0a6c-124">Now  your project can translate the words you speak into several different languages.</span></span> <span data-ttu-id="f0a6c-125">歡迎您試著使用這些語言, 並測試翻譯的正確性。</span><span class="sxs-lookup"><span data-stu-id="f0a6c-125">Feel free to play around with the languages, and test the accuracy of the translation.</span></span> 

[<span data-ttu-id="f0a6c-126">下一個教學課程:4.設定意圖和自然語言理解</span><span class="sxs-lookup"><span data-stu-id="f0a6c-126">Next tutorial: 4.  Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)

