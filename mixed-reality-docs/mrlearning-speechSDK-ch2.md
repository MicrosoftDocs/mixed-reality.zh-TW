---
title: Azure 語音服務教學課程 - 2。 新增本機語音轉換文字翻譯離線模式
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 語音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 75ddce9063bb9d33f5fe2343fe30178222a5f8ac
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "79031606"
---
# <a name="2-using-speech-recognition-to-execute-commands"></a><span data-ttu-id="74267-105">2.使用語音辨識來執行命令</span><span class="sxs-lookup"><span data-stu-id="74267-105">2. Using speech recognition to execute commands</span></span>

<span data-ttu-id="74267-106">在本教學課程中，您將新增使用 Azure 語音辨識執行命令的功能，這可讓您根據所定義的單字或片語進行一些動作。</span><span class="sxs-lookup"><span data-stu-id="74267-106">In this tutorial, you will add the ability to execute commands using Azure speech recognition which will allow you to make something happen based on the word or phrase you define.</span></span>

## <a name="objectives"></a><span data-ttu-id="74267-107">目標</span><span class="sxs-lookup"><span data-stu-id="74267-107">Objectives</span></span>

* <span data-ttu-id="74267-108">了解如何使用 Azure 語音辨識來執行命令</span><span class="sxs-lookup"><span data-stu-id="74267-108">Learn how Azure speech recognition can be used to execute commands</span></span>

## <a name="instructions"></a><span data-ttu-id="74267-109">指示</span><span class="sxs-lookup"><span data-stu-id="74267-109">Instructions</span></span>

<span data-ttu-id="74267-110">在 [階層] 視窗中選取 **Lunarcom** 物件，然後在 [偵測器] 視窗中使用 [新增元件]  按鈕來將 **Lunarcom Wake Word Recognizer (指令碼)** 元件新增至 Lunarcom 物件，並進行以下設定：</span><span class="sxs-lookup"><span data-stu-id="74267-110">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Wake Word Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="74267-111">在 [喚醒字詞]  欄位中，入適當的片語，例如「啟動終端機 (Activate terminal)」  。</span><span class="sxs-lookup"><span data-stu-id="74267-111">In the **Wake Word** field, enter a suitable phrase, for example, _Activate terminal_.</span></span>
* <span data-ttu-id="74267-112">在 [關閉字詞]  欄位中，輸入適當的片語，例如「關閉終端機 (Dismiss terminal)」  。</span><span class="sxs-lookup"><span data-stu-id="74267-112">In the **Dismiss Word** field, enter a suitable phrase, for example, _Dismiss terminal_.</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="74267-114">Lunarcom Wake Word Recognizer (指令碼) 元件不是 MRTK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="74267-114">The Lunarcom Wake Word Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="74267-115">這是本教學課程資產隨附的元件。</span><span class="sxs-lookup"><span data-stu-id="74267-115">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="74267-116">如果您現在進入遊戲模式，如先前的教學課程所示，預設會啟用終端機面板，但您現在可以藉由說出關閉字詞：**關閉終端機**，來將其停用：</span><span class="sxs-lookup"><span data-stu-id="74267-116">If you now enter Game mode, as in the previous tutorial, the terminal panel is enabled by default, but you can now disable it by saying the Dismiss Word, **Dismiss terminal**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-2.png)

<span data-ttu-id="74267-118">然後藉由說出喚醒字詞：**啟動終端機**，來再次將其啟動：</span><span class="sxs-lookup"><span data-stu-id="74267-118">And enable it again by saying the Wake Word, **Activate terminal**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="74267-120">應用程式必須連線到 Azure，因此請確定您的電腦/裝置已連線到網際網路。</span><span class="sxs-lookup"><span data-stu-id="74267-120">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

> [!TIP]
> <span data-ttu-id="74267-121">如果您預期無法經常連線到 Azure，您也可以遵循[啟用語音命令](mrlearning-base-ch5.md#enabling-voice-commands)指示，使用 MRTK 來實作語音命令。</span><span class="sxs-lookup"><span data-stu-id="74267-121">If you anticipate frequently not being able to connect to Azure, you can also implement speech commands using MRTK by following the [Enabling Voice Commands](mrlearning-base-ch5.md#enabling-voice-commands) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="74267-122">恭喜！</span><span class="sxs-lookup"><span data-stu-id="74267-122">Congratulations</span></span>

<span data-ttu-id="74267-123">您已實作由 Azure 提供技術支援的語音命令。</span><span class="sxs-lookup"><span data-stu-id="74267-123">You have implemented speech commands powered by Azure.</span></span> <span data-ttu-id="74267-124">在您的裝置上執行應用程式，以確保功能可正常運作。</span><span class="sxs-lookup"><span data-stu-id="74267-124">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="74267-125">在下一個教學課程中，您將了解如何使用 Azure 語音翻譯來轉譯語音。</span><span class="sxs-lookup"><span data-stu-id="74267-125">In the next tutorial, you will learn how to translate speech using Azure speech translation.</span></span>

[<span data-ttu-id="74267-126">下一個教學課程：3.新增 Azure 認知服務語音翻譯元件</span><span class="sxs-lookup"><span data-stu-id="74267-126">Next Tutorial: 3. Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)
