---
title: MR 學習 Speechsdk.quickstart 模組-語音辨識與轉譯
description: 完成此課程, 以瞭解如何在混合現實應用程式中執行 Azure 語音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: e8dc5da5a089079ba38a26969df6070af8bc6200
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460308"
---
# <a name="2----adding-an-offline-mode-for-local-speech-to-text-translation"></a><span data-ttu-id="d676b-104">2.  新增用於本機語音轉換文字翻譯的離線模式</span><span class="sxs-lookup"><span data-stu-id="d676b-104">2.    Adding an offline mode for local speech-to-text translation</span></span>

<span data-ttu-id="d676b-105">在本教學課程中, 我們將新增離線模式, 讓您在無法連線到 Azure 服務時執行本機語音轉換文字翻譯。</span><span class="sxs-lookup"><span data-stu-id="d676b-105">In this tutorial, we'll add an offline mode that lets you perform local speech-to-text translation when we are unable to connect to the Azure service.</span></span> <span data-ttu-id="d676b-106">我們也會*模擬*中斷連線的狀態。</span><span class="sxs-lookup"><span data-stu-id="d676b-106">We will also *simulate* a disconnected state.</span></span>

1. <span data-ttu-id="d676b-107">選取階層中的 [Lunarcom_Base] 物件, 然後按一下 [偵測器] 面板中的 [新增元件]。</span><span class="sxs-lookup"><span data-stu-id="d676b-107">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the Inspector panel.</span></span> <span data-ttu-id="d676b-108">搜尋並選取 [Lunarcom 離線識別]。</span><span class="sxs-lookup"><span data-stu-id="d676b-108">Search for and select the Lunarcom Offline Recognition.</span></span>

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)

2. <span data-ttu-id="d676b-110">按一下 LunarcomOfflineRecognizer 中的下拉式選單, 然後選取 [已啟用]。</span><span class="sxs-lookup"><span data-stu-id="d676b-110">Click the drop-down in the LunarcomOfflineRecognizer, and select Enabled.</span></span> <span data-ttu-id="d676b-111">這會讓專案的行為與使用者不具有連接。</span><span class="sxs-lookup"><span data-stu-id="d676b-111">This programs the project to act like the user doesn't have a connection.</span></span> 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

3. <span data-ttu-id="d676b-113">現在, 按下 [在 Unity 編輯器中播放] 並加以測試。</span><span class="sxs-lookup"><span data-stu-id="d676b-113">Now, press play in Unity Editor, and test it.</span></span> <span data-ttu-id="d676b-114">按下場景左下角的麥克風, 然後開始說話。</span><span class="sxs-lookup"><span data-stu-id="d676b-114">Press the microphone in the bottom left hand corner in the scene, and begin speaking.</span></span> 

> [!NOTE]
> <span data-ttu-id="d676b-115">因為我們已離線, 所以已停用喚醒 word 功能。</span><span class="sxs-lookup"><span data-stu-id="d676b-115">Because we’re offline, wake word functionality has been disabled.</span></span> <span data-ttu-id="d676b-116">當您每次想要在離線時辨識語音時, 都必須實際按一下麥克風。</span><span class="sxs-lookup"><span data-stu-id="d676b-116">You'll have to physically click the microphone every time you wish to have your speech recognized when offline.</span></span> 

<span data-ttu-id="d676b-117">以下是您的場景可能外觀的範例。</span><span class="sxs-lookup"><span data-stu-id="d676b-117">Below is an example of what your scene could look like.</span></span>

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="d676b-119">恭喜！</span><span class="sxs-lookup"><span data-stu-id="d676b-119">Congratulations</span></span>

<span data-ttu-id="d676b-120">已啟用離線模式。</span><span class="sxs-lookup"><span data-stu-id="d676b-120">The offline mode has been enabled.</span></span> <span data-ttu-id="d676b-121">現在, 當您離線時, 您仍然可以使用語音 SDK 來處理您的專案!</span><span class="sxs-lookup"><span data-stu-id="d676b-121">Now, when you're offline, you can still work on your project with the speech-SDK!</span></span> 


[<span data-ttu-id="d676b-122">下一個教學課程:3.新增 Azure 認知服務語音翻譯元件</span><span class="sxs-lookup"><span data-stu-id="d676b-122">Next Tutorial: 3.  Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)

