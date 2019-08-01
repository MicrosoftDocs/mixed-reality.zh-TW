---
title: Azure 語音服務教學課程-2。 新增用於本機語音轉換文字翻譯的離線模式
description: 完成此課程, 以瞭解如何在混合現實應用程式中執行 Azure 語音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 1dd6c01768ddf5dda954f50e0f7507022bd59c3b
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701854"
---
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a><span data-ttu-id="cd44b-105">2.新增用於本機語音轉換文字翻譯的離線模式</span><span class="sxs-lookup"><span data-stu-id="cd44b-105">2. Adding an offline mode for local speech-to-text translation</span></span>

<span data-ttu-id="cd44b-106">在本教學課程中, 我們將新增離線模式, 讓您在無法連線到 Azure 服務時執行本機語音轉換文字翻譯。</span><span class="sxs-lookup"><span data-stu-id="cd44b-106">In this tutorial, we'll add an offline mode that lets you perform local speech-to-text translation when we are unable to connect to the Azure service.</span></span> <span data-ttu-id="cd44b-107">我們也會*模擬*中斷連線的狀態。</span><span class="sxs-lookup"><span data-stu-id="cd44b-107">We will also *simulate* a disconnected state.</span></span>

## <a name="instructions"></a><span data-ttu-id="cd44b-108">指示</span><span class="sxs-lookup"><span data-stu-id="cd44b-108">Instructions</span></span>

1. <span data-ttu-id="cd44b-109">選取階層中的 [Lunarcom_Base] 物件, 然後按一下 [偵測器] 面板中的 [新增元件]。</span><span class="sxs-lookup"><span data-stu-id="cd44b-109">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the Inspector panel.</span></span> <span data-ttu-id="cd44b-110">搜尋並選取 [Lunarcom 離線識別]。</span><span class="sxs-lookup"><span data-stu-id="cd44b-110">Search for and select the Lunarcom Offline Recognition.</span></span>

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)

2. <span data-ttu-id="cd44b-112">按一下 LunarcomOfflineRecognizer 中的下拉式選單, 然後選取 [已啟用]。</span><span class="sxs-lookup"><span data-stu-id="cd44b-112">Click the drop-down in the LunarcomOfflineRecognizer, and select Enabled.</span></span> <span data-ttu-id="cd44b-113">這會讓專案的行為與使用者不具有連接。</span><span class="sxs-lookup"><span data-stu-id="cd44b-113">This programs the project to act like the user doesn't have a connection.</span></span> 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

3. <span data-ttu-id="cd44b-115">現在, 按下 [在 Unity 編輯器中播放] 並加以測試。</span><span class="sxs-lookup"><span data-stu-id="cd44b-115">Now, press play in Unity Editor, and test it.</span></span> <span data-ttu-id="cd44b-116">按下場景左下角的麥克風, 然後開始說話。</span><span class="sxs-lookup"><span data-stu-id="cd44b-116">Press the microphone in the bottom left hand corner in the scene, and begin speaking.</span></span> 

> [!NOTE]
> <span data-ttu-id="cd44b-117">因為我們已離線, 所以已停用喚醒 word 功能。</span><span class="sxs-lookup"><span data-stu-id="cd44b-117">Because we’re offline, wake word functionality has been disabled.</span></span> <span data-ttu-id="cd44b-118">當您每次想要在離線時辨識語音時, 都必須實際按一下麥克風。</span><span class="sxs-lookup"><span data-stu-id="cd44b-118">You'll have to physically click the microphone every time you wish to have your speech recognized when offline.</span></span> 

<span data-ttu-id="cd44b-119">以下是您的場景可能外觀的範例。</span><span class="sxs-lookup"><span data-stu-id="cd44b-119">Below is an example of what your scene could look like.</span></span>

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="cd44b-121">恭喜！</span><span class="sxs-lookup"><span data-stu-id="cd44b-121">Congratulations</span></span>

<span data-ttu-id="cd44b-122">已啟用離線模式。</span><span class="sxs-lookup"><span data-stu-id="cd44b-122">The offline mode has been enabled.</span></span> <span data-ttu-id="cd44b-123">現在, 當您離線時, 您仍然可以使用語音 SDK 來處理您的專案!</span><span class="sxs-lookup"><span data-stu-id="cd44b-123">Now, when you're offline, you can still work on your project with the speech-SDK!</span></span> 


[<span data-ttu-id="cd44b-124">下一個教學課程:3.新增 Azure 認知服務語音翻譯元件</span><span class="sxs-lookup"><span data-stu-id="cd44b-124">Next Tutorial: 3.  Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)

