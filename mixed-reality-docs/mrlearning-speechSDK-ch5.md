---
title: MR 學習 Speechsdk.quickstart 模組-語音辨識與轉譯
description: 完成此課程, 以瞭解如何在混合現實應用程式中執行 Azure 語音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: fc65dccfcbc181af0c0b321374c721797e120e5d
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460331"
---
# <a name="speech-sdk-learning-module---rocket-launcher-control-using-speech-commands"></a><span data-ttu-id="43f35-104">語音 SDK 學習模組-使用語音命令 Rocket 啟動器控制項</span><span class="sxs-lookup"><span data-stu-id="43f35-104">Speech SDK Learning Module - Rocket Launcher Control Using Speech Commands</span></span>

<span data-ttu-id="43f35-105">在這一課, 我們將使用 Azure 語音服務的意圖功能來瞭解語音的意圖。</span><span class="sxs-lookup"><span data-stu-id="43f35-105">In this lesson, we will be using Azure Speech Service's Intent feature to understand the intent of the speech.</span></span> <span data-ttu-id="43f35-106">我們會使用 [偵測到的語音] 意圖作為語音命令, 以控制 rocket 啟動器。</span><span class="sxs-lookup"><span data-stu-id="43f35-106">We will be using the detected intent of speech as the voice commands to control the rocket launcher.</span></span> <span data-ttu-id="43f35-107">在此課程中, 我們將匯入 Rocket 啟動器資產, 而我們會將偵測到的意圖語音命令介面為預先定義的控制按鈕, 以控制 Rocket。</span><span class="sxs-lookup"><span data-stu-id="43f35-107">During this lesson, we will be importing the Rocket Launcher asset and We will interface the detected intent voice commands to predefined control buttons to control the rocket.</span></span> 

## <a name="objectives"></a><span data-ttu-id="43f35-108">目標</span><span class="sxs-lookup"><span data-stu-id="43f35-108">Objectives</span></span>

- <span data-ttu-id="43f35-109">瞭解如何將語音意圖連接為語音命令。</span><span class="sxs-lookup"><span data-stu-id="43f35-109">Learn how to connect speech intent as voice commands.</span></span>
- <span data-ttu-id="43f35-110">瞭解如何使用語音意圖語音命令作為 rocket 控制輸入命令。</span><span class="sxs-lookup"><span data-stu-id="43f35-110">Learn how to use speech intent voice commands as rocket control input commands.</span></span>

## <a name="instructions"></a><span data-ttu-id="43f35-111">指示</span><span class="sxs-lookup"><span data-stu-id="43f35-111">Instructions</span></span>
1. <span data-ttu-id="43f35-112">在本教學課程中, 我們將使用「BaseModule」資產, 將 rocket 啟動器與語音命令整合。</span><span class="sxs-lookup"><span data-stu-id="43f35-112">In this tutorial, we will be using a "BaseModule" asset to integrate rocket launcher with the speech commands.</span></span> <span data-ttu-id="43f35-113">為此, 我們需要將資產匯入到專案中。</span><span class="sxs-lookup"><span data-stu-id="43f35-113">For that, we need to import the asset into our project.</span></span> <span data-ttu-id="43f35-114">您可以使用此連結 (附加連結) 來下載 "Rocket 啟動器" 資產。</span><span class="sxs-lookup"><span data-stu-id="43f35-114">You can download the "Rocket Launcher" asset using this link (Attach the link).</span></span> 

2. <span data-ttu-id="43f35-115">若要匯入資產, 請移至資產-> 匯入套件-> 自訂套件-> 流覽至下載的檔案, 然後按一下 [匯入]。</span><span class="sxs-lookup"><span data-stu-id="43f35-115">To import the asset, please go to assets->Import package->Custom package-> navigate to the downloaded file and click import.</span></span>

![module4chapter5step1](images/module4chapter5step1.PNG)

3. <span data-ttu-id="43f35-117">匯入 "Rocket 啟動器" 資產之後, 請在 "Rocket 啟動器" 資料夾內流覽-> Prefabs > 選取 [Rocket Launcher_Complete], 然後將它拖放到現有的場景階層中。</span><span class="sxs-lookup"><span data-stu-id="43f35-117">After importing the "Rocket Launcher" asset, navigate inside the "Rocket Launcher" folder->Prefabs-> Select "Rocket Launcher_Complete", and then drag and drop it into the existing scene Hierarchy.</span></span>

![module4chapter5step2](images/module4chapter5step2.PNG)

4. <span data-ttu-id="43f35-119">現在, 我們需要將我們的「Rocket 啟動器」與我們在上一課中使用的 LUIS 專案整合在一起 (lesson4 的連結)。</span><span class="sxs-lookup"><span data-stu-id="43f35-119">Now we need to integrate our "Rocket Launcher" with our LUIS project that we worked in our previous lesson (link for lesson4).</span></span> <span data-ttu-id="43f35-120">為此, 請展開階層中的 "Rocket Launcher_Complete" prefab, 並尋找 [LaunchRoundButton]、[ResetRoundButton] 和 [放置提示] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="43f35-120">For that, expand the "Rocket Launcher_Complete" prefab in the hierarchy and find the "LaunchRoundButton", "ResetRoundButton" and "Placement Hints" buttons.</span></span>

![module4chapter5step3](images/module4chapter5step3.PNG)

5. <span data-ttu-id="43f35-122">選取 [LaunchRoundButton], 然後在 [偵測器] 面板中, 移至 [可互動], 然後在事件的 [OnClick ()] 底下, 拖放 [LunarModule] prefab。</span><span class="sxs-lookup"><span data-stu-id="43f35-122">Select "LaunchRoundButton" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="43f35-123">然後, 選取 [函式] 下拉式選並選取 [LunarModule], 然後流覽至 "StartThruster ()" 函式並加以選取。</span><span class="sxs-lookup"><span data-stu-id="43f35-123">Then, select the function drop down and select " LunarModule" and then navigate to "StartThruster()" function and select it.</span></span>

![module4chapter5step 3。0](images/module4chapter5step3.0.PNG)

![module4chapter5step3a](images/module4chapter5step3a.PNG)

6. <span data-ttu-id="43f35-126">選取 [ResetRoundButton], 然後在 [偵測器] 面板中, 移至 [可互動], 然後在事件的 [OnClick ()] 底下, 拖放 [LunarModule] prefab。</span><span class="sxs-lookup"><span data-stu-id="43f35-126">Select "ResetRoundButton" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="43f35-127">然後, 選取 [函式] 下拉式選並選取 [LunarModule], 然後流覽至 "resetModule ()" 函式並加以選取。</span><span class="sxs-lookup"><span data-stu-id="43f35-127">Then, select the function drop down and select " LunarModule" and then navigate to "resetModule()" function and select it.</span></span>

![module4chapter5step3b](images/module4chapter5step3b.PNG)

7. <span data-ttu-id="43f35-129">選取 [放置提示], 然後在 [偵測器] 面板中, 移至 [可互動], 然後在事件的 [OnClick ()] 底下, 拖放 "LunarModule" prefab。</span><span class="sxs-lookup"><span data-stu-id="43f35-129">Select "Placement Hints" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="43f35-130">然後, 選取 [函式] 下拉式選並選取 [LunarModule], 然後流覽至 [TogglePlacementHints] 函式, 然後選取 [ToggleGameOBjects ()]。</span><span class="sxs-lookup"><span data-stu-id="43f35-130">Then, select the function drop down and select " LunarModule" and then navigate to "TogglePlacementHints" function and select ToggleGameOBjects().</span></span>

![module4chapter5step3c](images/module4chapter5step3c.PNG)

8.  <span data-ttu-id="43f35-132">接下來, 選取階層中的 [Lunarcom_Completed] prefab, 並流覽至 [Inspector] 中的 [Lunarcom 意圖辨識器] 腳本, 然後將 [LaunchRoundButton]、[ResetRoundButton] 和 [放置提示] 按鈕拖放到其各自的位置。</span><span class="sxs-lookup"><span data-stu-id="43f35-132">Next, Select the Lunarcom_Completed prefab in Hierarchy and navigate to "Lunarcom Intent Recognizer" script in Inspector and then drag and drop  "LaunchRoundButton", "ResetRoundButton" and "Placement Hints" buttons to their respective places.</span></span>

![module4chapter5step4](images/module4chapter5step4.PNG)

9. <span data-ttu-id="43f35-134">按下 Unity 編輯器中的 [播放] 按鈕, 並按一下 [Rocket] 按鈕, 然後有些純粹是像是「推送 Rocket 啟動按鈕」、「顯示位置提示」、「按下 rest 按鈕」或任何其他與啟動、重設或提示 Rocket 啟動器的要求相關的片語。</span><span class="sxs-lookup"><span data-stu-id="43f35-134">Press the play button in Unity Editor and click on the "Rocket" button and utter the phrases like "Push rocket launch button","show me a placement hint", "press the rest button" or any other phrases related to launch, reset or hint's request for the rocket launcher.</span></span>

![module4chapter5step5a](images/module4chapter5step5a.PNG)

![module4chapter5step5b](images/module4chapter5step5b.PNG)

![module4chapter5step5c](images/module4chapter5step5c.PNG)

## <a name="congratulations"></a><span data-ttu-id="43f35-138">恭喜！</span><span class="sxs-lookup"><span data-stu-id="43f35-138">Congratulations</span></span>

<span data-ttu-id="43f35-139">在本課程中, 我們已瞭解如何將 AI 驅動的語音命令連接到語音命令, 以作為輸入法。</span><span class="sxs-lookup"><span data-stu-id="43f35-139">In this lesson, we learned how to connect the AI-powered speech commands to voice commands to use it as an input method.</span></span> <span data-ttu-id="43f35-140">現在, 我們的程式可以使用說話者意圖作為語音命令, 為 rocket 啟動器提供輸入。</span><span class="sxs-lookup"><span data-stu-id="43f35-140">Now our program can use the speakers intent as voice commands to give inputs for the rocket launcher.</span></span>

