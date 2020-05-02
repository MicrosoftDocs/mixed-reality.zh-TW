---
title: Azure 語音服務教學課程 - 3。 新增 Azure 認知服務語音翻譯元件
description: 在此課程中，您將了解如何在混合實境應用程式中實作 Azure 語音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: d8e73e24f0522ff71b95ea1886d59893216b0597
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "79028323"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="29f27-105">3.新增 Azure 認知服務語音翻譯元件</span><span class="sxs-lookup"><span data-stu-id="29f27-105">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="29f27-106">在本教學課程中，您會將語音翻譯新增至您的專案，以讓您將語音翻譯及轉譯成三種不同語言。</span><span class="sxs-lookup"><span data-stu-id="29f27-106">In this tutorial, you will add speech translation to your project which will allow you to translate and transcribed your speech into three different languages.</span></span>

## <a name="objectives"></a><span data-ttu-id="29f27-107">目標</span><span class="sxs-lookup"><span data-stu-id="29f27-107">Objectives</span></span>

* <span data-ttu-id="29f27-108">了解如何整合 Azure 語音翻譯</span><span class="sxs-lookup"><span data-stu-id="29f27-108">Learn how to integrate Azure speech translation</span></span>

## <a name="instructions"></a><span data-ttu-id="29f27-109">指示</span><span class="sxs-lookup"><span data-stu-id="29f27-109">Instructions</span></span>

<span data-ttu-id="29f27-110">在 [階層] 視窗中選取 **Lunarcom** 物件，然後在 [偵測器] 視窗中使用 [新增元件]  按鈕來將 **Lunarcom Translation Recognizer (指令碼)** 元件新增至 Lunarcom 物件，並進行以下設定：</span><span class="sxs-lookup"><span data-stu-id="29f27-110">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Translation Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="29f27-111">將 [目標語言]  變更為您選擇的語言，例如：德文 </span><span class="sxs-lookup"><span data-stu-id="29f27-111">Change the **Target Language** to a language of your choosing, for example, _German_</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="29f27-113">Lunarcom Translation Recognizer (指令碼) 元件不是 MRTK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="29f27-113">The Lunarcom Translation Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="29f27-114">這是本教學課程資產隨附的元件。</span><span class="sxs-lookup"><span data-stu-id="29f27-114">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="29f27-115">如果您現在進入遊戲模式，您可以先按下衛星按鈕來測試語音翻譯。</span><span class="sxs-lookup"><span data-stu-id="29f27-115">If you now enter Game mode, you can test the speech translation by first pressing the satellite button.</span></span> <span data-ttu-id="29f27-116">接下來，假設您的電腦有麥克風，當您說到某個項目時，您的語音會翻譯成您選擇的語言並在終端機面板上進行轉譯：</span><span class="sxs-lookup"><span data-stu-id="29f27-116">Then, assuming your computer has a microphone, when you say something, your speech will be translated into the chosen language and transcribed on the terminal panel:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-2.png)

> [!CAUTION]
> <span data-ttu-id="29f27-118">應用程式必須連線到 Azure，因此請確定您的電腦/裝置已連線到網際網路。</span><span class="sxs-lookup"><span data-stu-id="29f27-118">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="29f27-119">恭喜！</span><span class="sxs-lookup"><span data-stu-id="29f27-119">Congratulations</span></span>

<span data-ttu-id="29f27-120">您的專案現在可以成功地將您所說的字詞轉譯成數種不同的語言。</span><span class="sxs-lookup"><span data-stu-id="29f27-120">Your project can now successfully translate the words you speak into several different languages.</span></span> <span data-ttu-id="29f27-121">在您的裝置上執行應用程式，以確保功能可正常運作。</span><span class="sxs-lookup"><span data-stu-id="29f27-121">Run the application on your device to ensure the feature is working properly.</span></span>

[<span data-ttu-id="29f27-122">下一個教學課程：4.設定意圖和自然語言理解</span><span class="sxs-lookup"><span data-stu-id="29f27-122">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)
