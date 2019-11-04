---
title: Unity 中的語音輸入
description: Unity 公開三種方式，可將語音輸入新增至您的 Windows Mixed Reality 應用程式。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 語音輸入、KeywordRecognizer、GrammarRecognizer、麥克風、聽寫、語音
ms.openlocfilehash: d1cd2a2b954a195bc3f2688d915965f89aa30f98
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438194"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="cc41f-104">Unity 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="cc41f-104">Voice input in Unity</span></span>

>[!NOTE]
><span data-ttu-id="cc41f-105">除了下列資訊之外，請考慮使用認知語音服務 SDK 的 Unity 外掛程式，其具有更佳的語音精確度結果，並可讓您輕鬆存取語音轉文字解碼和先進的語音功能，例如對話方塊、意圖型互動、轉譯、文字轉換語音和自然語言語音辨識。</span><span class="sxs-lookup"><span data-stu-id="cc41f-105">Instead of the below information, consider using the Unity plug-in for the Cognitive Speech Services SDK which has much better Speech Accuracy results and provides easy access to speech-to-text decode and advanced speech features like dialog, intent based interaction, translation, text-to-speech synthesis and natural language speech recognition.</span></span> <span data-ttu-id="cc41f-106">在這裡尋找範例和檔： https://docs.microsoft.com//azure/cognitive-services/speech-service/quickstart-csharp-unity</span><span class="sxs-lookup"><span data-stu-id="cc41f-106">Find the sample and documentaion here: https://docs.microsoft.com//azure/cognitive-services/speech-service/quickstart-csharp-unity</span></span>   

<span data-ttu-id="cc41f-107">Unity 會公開三種將[語音輸入](voice-input.md)新增至 Unity 應用程式的方式。</span><span class="sxs-lookup"><span data-stu-id="cc41f-107">Unity exposes three ways to add [Voice input](voice-input.md) to your Unity application.</span></span>

<span data-ttu-id="cc41f-108">使用 KeywordRecognizer （PhraseRecognizers 的兩種類型之一）時，您的應用程式可以指定要接聽的字串命令陣列。</span><span class="sxs-lookup"><span data-stu-id="cc41f-108">With the KeywordRecognizer (one of two types of PhraseRecognizers), your app can be given an array of string commands to listen for.</span></span> <span data-ttu-id="cc41f-109">使用 GrammarRecognizer （PhraseRecognizer 的其他類型）時，您的應用程式可以指定一個 SRGS 檔案，以定義要接聽的特定文法。</span><span class="sxs-lookup"><span data-stu-id="cc41f-109">With the GrammarRecognizer (the other type of PhraseRecognizer), your app can be given an SRGS file defining a specific grammar to listen for.</span></span> <span data-ttu-id="cc41f-110">透過 DictationRecognizer，您的應用程式可以接聽任何單字，並為使用者提供其語音的附注或其他顯示。</span><span class="sxs-lookup"><span data-stu-id="cc41f-110">With the DictationRecognizer, your app can listen for any word and provide the user with a note or other display of their speech.</span></span>

>[!NOTE]
><span data-ttu-id="cc41f-111">只能一次處理聽寫或片語辨識。</span><span class="sxs-lookup"><span data-stu-id="cc41f-111">Only dictation or phrase recognition can be handled at once.</span></span> <span data-ttu-id="cc41f-112">這表示，如果 GrammarRecognizer 或 KeywordRecognizer 作用中，DictationRecognizer 就無法作用，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="cc41f-112">That means if a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can not be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="cc41f-113">啟用語音功能</span><span class="sxs-lookup"><span data-stu-id="cc41f-113">Enabling the capability for Voice</span></span>

<span data-ttu-id="cc41f-114">必須為應用程式宣告**麥克風**功能，才能利用語音輸入。</span><span class="sxs-lookup"><span data-stu-id="cc41f-114">The **Microphone** capability must be declared for an app to leverage Voice input.</span></span>
1. <span data-ttu-id="cc41f-115">在 Unity 編輯器中，流覽至 [編輯 > 專案設定 > Player]，移至播放程式設定</span><span class="sxs-lookup"><span data-stu-id="cc41f-115">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
2. <span data-ttu-id="cc41f-116">按一下 [Windows Store] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="cc41f-116">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="cc41f-117">在 [發佈設定 > 功能] 區段中，檢查**麥克風**功能</span><span class="sxs-lookup"><span data-stu-id="cc41f-117">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="cc41f-118">片語辨識</span><span class="sxs-lookup"><span data-stu-id="cc41f-118">Phrase Recognition</span></span>

<span data-ttu-id="cc41f-119">若要讓您的應用程式接聽使用者所說的特定片語，請採取一些動作，您必須：</span><span class="sxs-lookup"><span data-stu-id="cc41f-119">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="cc41f-120">使用 KeywordRecognizer 或 GrammarRecognizer 指定要接聽的片語</span><span class="sxs-lookup"><span data-stu-id="cc41f-120">Specify which phrases to listen for using a KeywordRecognizer or GrammarRecognizer</span></span>
2. <span data-ttu-id="cc41f-121">處理 OnPhraseRecognized 事件，並採取對應至已辨識片語的動作</span><span class="sxs-lookup"><span data-stu-id="cc41f-121">Handle the OnPhraseRecognized event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="cc41f-122">KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="cc41f-122">KeywordRecognizer</span></span>

<span data-ttu-id="cc41f-123">**命名空間：** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="cc41f-123">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="cc41f-124">**類型：** *KeywordRecognizer*、 *PhraseRecognizedEventArgs*、 *SpeechError*、 *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="cc41f-124">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="cc41f-125">我們需要幾個 using 語句來儲存一些按鍵：</span><span class="sxs-lookup"><span data-stu-id="cc41f-125">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="cc41f-126">接著，讓我們將幾個欄位新增至您的類別，以儲存辨識器和關鍵字 > 動作字典：</span><span class="sxs-lookup"><span data-stu-id="cc41f-126">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="cc41f-127">現在將關鍵字新增至字典（例如，在 Start （）方法內）。</span><span class="sxs-lookup"><span data-stu-id="cc41f-127">Now add a keyword to the dictionary (e.g. inside of a Start() method).</span></span> <span data-ttu-id="cc41f-128">我們要在此範例中新增 "activate" 關鍵字：</span><span class="sxs-lookup"><span data-stu-id="cc41f-128">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="cc41f-129">建立關鍵字辨識器並告訴它我們要辨識的內容：</span><span class="sxs-lookup"><span data-stu-id="cc41f-129">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="cc41f-130">立即註冊 OnPhraseRecognized 事件</span><span class="sxs-lookup"><span data-stu-id="cc41f-130">Now register for the OnPhraseRecognized event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="cc41f-131">範例處理常式如下：</span><span class="sxs-lookup"><span data-stu-id="cc41f-131">An example handler is:</span></span>

```
private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    System.Action keywordAction;
    // if the keyword recognized is in our dictionary, call that Action.
    if (keywords.TryGetValue(args.text, out keywordAction))
    {
        keywordAction.Invoke();
    }
}
```

<span data-ttu-id="cc41f-132">最後，開始辨識！</span><span class="sxs-lookup"><span data-stu-id="cc41f-132">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="cc41f-133">GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="cc41f-133">GrammarRecognizer</span></span>

<span data-ttu-id="cc41f-134">**命名空間：** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="cc41f-134">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="cc41f-135">**類型**： *GrammarRecognizer*、 *PhraseRecognizedEventArgs*、 *SpeechError*、 *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="cc41f-135">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="cc41f-136">如果您要使用 SRGS 來指定辨識文法，則會使用 GrammarRecognizer。</span><span class="sxs-lookup"><span data-stu-id="cc41f-136">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="cc41f-137">如果您的應用程式有多個關鍵字，如果您想要辨識較複雜的片語，或如果您想要輕鬆地開啟和關閉命令集，這項功能就很有用。</span><span class="sxs-lookup"><span data-stu-id="cc41f-137">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="cc41f-138">請參閱：[使用 SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx)為檔案格式資訊建立文法。</span><span class="sxs-lookup"><span data-stu-id="cc41f-138">See: [Create Grammars Using SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) for file format information.</span></span>

<span data-ttu-id="cc41f-139">一旦您有了 SRGS 文法，它就會在您的專案中[StreamingAssets 資料夾](https://docs.unity3d.com/Manual/StreamingAssets.html)內：</span><span class="sxs-lookup"><span data-stu-id="cc41f-139">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](https://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="cc41f-140">建立 GrammarRecognizer，並將路徑傳遞至您的 SRGS 檔案：</span><span class="sxs-lookup"><span data-stu-id="cc41f-140">Create a GrammarRecognizer and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="cc41f-141">立即註冊 OnPhraseRecognized 事件</span><span class="sxs-lookup"><span data-stu-id="cc41f-141">Now register for the OnPhraseRecognized event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="cc41f-142">您會取得一個回呼，其中包含您可以適當處理的 [SRGS 文法] 中所指定的資訊。</span><span class="sxs-lookup"><span data-stu-id="cc41f-142">You will get a callback containing information specified in your SRGS grammar which you can handle appropriately.</span></span> <span data-ttu-id="cc41f-143">大部分的重要資訊將會在 semanticMeanings 陣列中提供。</span><span class="sxs-lookup"><span data-stu-id="cc41f-143">Most of the important information will be provided in the semanticMeanings array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="cc41f-144">最後，開始辨識！</span><span class="sxs-lookup"><span data-stu-id="cc41f-144">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="cc41f-145">聽寫</span><span class="sxs-lookup"><span data-stu-id="cc41f-145">Dictation</span></span>

<span data-ttu-id="cc41f-146">**命名空間：** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="cc41f-146">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="cc41f-147">**類型**： *DictationRecognizer*、 *SpeechError*、 *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="cc41f-147">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="cc41f-148">使用 DictationRecognizer 將使用者的語音轉換成文字。</span><span class="sxs-lookup"><span data-stu-id="cc41f-148">Use the DictationRecognizer to convert the user's speech to text.</span></span> <span data-ttu-id="cc41f-149">DictationRecognizer 會公開[聽寫](voice-input.md#dictation)功能，並支援註冊和接聽假設和片語完成的事件，讓您可以在使用者說話和之後，提供意見反應給您的使用者。</span><span class="sxs-lookup"><span data-stu-id="cc41f-149">The DictationRecognizer exposes [dictation](voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="cc41f-150">Start （）和 Stop （）方法分別啟用和停用聽寫辨識。</span><span class="sxs-lookup"><span data-stu-id="cc41f-150">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="cc41f-151">完成辨識器之後，應該使用 Dispose （）方法來釋放它所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="cc41f-151">Once done with the recognizer, it should be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="cc41f-152">它會在垃圾收集期間以額外的效能成本自動釋放這些資源（如果之前未釋放）。</span><span class="sxs-lookup"><span data-stu-id="cc41f-152">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>

<span data-ttu-id="cc41f-153">開始使用聽寫只需要幾個步驟：</span><span class="sxs-lookup"><span data-stu-id="cc41f-153">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="cc41f-154">建立新的 DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="cc41f-154">Create a new DictationRecognizer</span></span>
2. <span data-ttu-id="cc41f-155">處理聽寫事件</span><span class="sxs-lookup"><span data-stu-id="cc41f-155">Handle Dictation events</span></span>
3. <span data-ttu-id="cc41f-156">啟動 DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="cc41f-156">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="cc41f-157">啟用聽寫功能</span><span class="sxs-lookup"><span data-stu-id="cc41f-157">Enabling the capability for dictation</span></span>

<span data-ttu-id="cc41f-158">除了上面提到的「麥克風」功能以外，您必須為應用程式宣告「網際網路用戶端」功能，才能利用聽寫。</span><span class="sxs-lookup"><span data-stu-id="cc41f-158">The "Internet Client" capability, in addition to the "Microphone" capability mentioned above, must be declared for an app to leverage dictation.</span></span>
1. <span data-ttu-id="cc41f-159">在 Unity 編輯器中，流覽至 [編輯 > 專案設定 > Player] 頁面，移至播放程式設定</span><span class="sxs-lookup"><span data-stu-id="cc41f-159">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="cc41f-160">按一下 [Windows Store] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="cc41f-160">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="cc41f-161">在 [發佈設定 > 功能] 區段中，檢查**InternetClient**功能</span><span class="sxs-lookup"><span data-stu-id="cc41f-161">In the "Publishing Settings > Capabilities" section, check the **InternetClient** capability</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="cc41f-162">DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="cc41f-162">DictationRecognizer</span></span>

<span data-ttu-id="cc41f-163">建立 DictationRecognizer，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cc41f-163">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="cc41f-164">有四個聽寫事件可供訂閱並處理來執行聽寫行為。</span><span class="sxs-lookup"><span data-stu-id="cc41f-164">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. <span data-ttu-id="cc41f-165">DictationResult</span><span class="sxs-lookup"><span data-stu-id="cc41f-165">DictationResult</span></span>
2. <span data-ttu-id="cc41f-166">DictationComplete</span><span class="sxs-lookup"><span data-stu-id="cc41f-166">DictationComplete</span></span>
3. <span data-ttu-id="cc41f-167">DictationHypothesis</span><span class="sxs-lookup"><span data-stu-id="cc41f-167">DictationHypothesis</span></span>
4. <span data-ttu-id="cc41f-168">DictationError</span><span class="sxs-lookup"><span data-stu-id="cc41f-168">DictationError</span></span>

<span data-ttu-id="cc41f-169">**DictationResult**</span><span class="sxs-lookup"><span data-stu-id="cc41f-169">**DictationResult**</span></span>

<span data-ttu-id="cc41f-170">這個事件會在使用者暫停之後引發，通常是在句子的結尾。</span><span class="sxs-lookup"><span data-stu-id="cc41f-170">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="cc41f-171">這裡會傳回完整辨識的字串。</span><span class="sxs-lookup"><span data-stu-id="cc41f-171">The full recognized string is returned here.</span></span>

<span data-ttu-id="cc41f-172">首先，訂閱 DictationResult 事件：</span><span class="sxs-lookup"><span data-stu-id="cc41f-172">First, subscribe to the DictationResult event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="cc41f-173">然後處理 DictationResult 回呼：</span><span class="sxs-lookup"><span data-stu-id="cc41f-173">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="cc41f-174">**DictationHypothesis**</span><span class="sxs-lookup"><span data-stu-id="cc41f-174">**DictationHypothesis**</span></span>

<span data-ttu-id="cc41f-175">當使用者在交談時，會持續引發此事件。</span><span class="sxs-lookup"><span data-stu-id="cc41f-175">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="cc41f-176">當辨識器接聽時，它會提供目前為止聽到的文字。</span><span class="sxs-lookup"><span data-stu-id="cc41f-176">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="cc41f-177">首先，訂閱 DictationHypothesis 事件：</span><span class="sxs-lookup"><span data-stu-id="cc41f-177">First, subscribe to the DictationHypothesis event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="cc41f-178">然後處理 DictationHypothesis 回呼：</span><span class="sxs-lookup"><span data-stu-id="cc41f-178">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="cc41f-179">**DictationComplete**</span><span class="sxs-lookup"><span data-stu-id="cc41f-179">**DictationComplete**</span></span>

<span data-ttu-id="cc41f-180">當辨識器停止時，不論是從呼叫停止（），還是發生超時，或某個其他錯誤，都會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="cc41f-180">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="cc41f-181">首先，訂閱 DictationComplete 事件：</span><span class="sxs-lookup"><span data-stu-id="cc41f-181">First, subscribe to the DictationComplete event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="cc41f-182">然後處理 DictationComplete 回呼：</span><span class="sxs-lookup"><span data-stu-id="cc41f-182">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="cc41f-183">**DictationError**</span><span class="sxs-lookup"><span data-stu-id="cc41f-183">**DictationError**</span></span>

<span data-ttu-id="cc41f-184">發生錯誤時，就會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="cc41f-184">This event is fired when an error occurs.</span></span>

<span data-ttu-id="cc41f-185">首先，訂閱 DictationError 事件：</span><span class="sxs-lookup"><span data-stu-id="cc41f-185">First, subscribe to the DictationError event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="cc41f-186">然後處理 DictationError 回呼：</span><span class="sxs-lookup"><span data-stu-id="cc41f-186">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="cc41f-187">當您訂閱並處理您關心的聽寫事件之後，請啟動聽寫辨識器以開始接收事件。</span><span class="sxs-lookup"><span data-stu-id="cc41f-187">Once you have subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="cc41f-188">如果您不想再讓 DictationRecognizer 保持不變，您必須取消訂閱事件並處置 DictationRecognizer。</span><span class="sxs-lookup"><span data-stu-id="cc41f-188">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="cc41f-189">**各種**</span><span class="sxs-lookup"><span data-stu-id="cc41f-189">**Tips**</span></span>
* <span data-ttu-id="cc41f-190">Start （）和 Stop （）方法分別啟用和停用聽寫辨識。</span><span class="sxs-lookup"><span data-stu-id="cc41f-190">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="cc41f-191">完成辨識器之後，必須使用 Dispose （）方法來處置它，以釋放它所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="cc41f-191">Once done with the recognizer, it must be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="cc41f-192">它會在垃圾收集期間以額外的效能成本自動釋放這些資源（如果之前未釋放）。</span><span class="sxs-lookup"><span data-stu-id="cc41f-192">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>
* <span data-ttu-id="cc41f-193">在設定的一段時間後發生超時。</span><span class="sxs-lookup"><span data-stu-id="cc41f-193">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="cc41f-194">您可以在 DictationComplete 事件中檢查這些超時。</span><span class="sxs-lookup"><span data-stu-id="cc41f-194">You can check for these timeouts in the DictationComplete event.</span></span> <span data-ttu-id="cc41f-195">有兩個要注意的超時：</span><span class="sxs-lookup"><span data-stu-id="cc41f-195">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="cc41f-196">如果辨識器啟動且未在前五秒聽到任何音訊，則會超時。</span><span class="sxs-lookup"><span data-stu-id="cc41f-196">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
   2. <span data-ttu-id="cc41f-197">如果辨識器已指定結果，但接著會聽到24秒的無聲，則會超時。</span><span class="sxs-lookup"><span data-stu-id="cc41f-197">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="cc41f-198">同時使用片語辨識和聽寫</span><span class="sxs-lookup"><span data-stu-id="cc41f-198">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="cc41f-199">如果您想要在您的應用程式中同時使用片語辨識和聽寫，您必須完全關閉其中一項，然後才能啟動另一個。</span><span class="sxs-lookup"><span data-stu-id="cc41f-199">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="cc41f-200">如果您有多個 KeywordRecognizers 正在執行，您可以一次將它們全部關閉，方法是：</span><span class="sxs-lookup"><span data-stu-id="cc41f-200">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="cc41f-201">為了將所有辨識器還原成先前的狀態，在 DictationRecognizer 停止之後，您可以呼叫：</span><span class="sxs-lookup"><span data-stu-id="cc41f-201">In order to restore all recognizers to their previous state, after the DictationRecognizer has stopped, you can call:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="cc41f-202">您也可以直接啟動 KeywordRecognizer，這也會重新開機 PhraseRecognitionSystem。</span><span class="sxs-lookup"><span data-stu-id="cc41f-202">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="using-the-microphone-helper"></a><span data-ttu-id="cc41f-203">使用麥克風協助程式</span><span class="sxs-lookup"><span data-stu-id="cc41f-203">Using the microphone helper</span></span>

<span data-ttu-id="cc41f-204">GitHub 上的混合現實工具組包含麥克風協助程式類別，可在系統上有可用的麥克風時，在開發人員提示。</span><span class="sxs-lookup"><span data-stu-id="cc41f-204">The Mixed Reality Toolkit on GitHub contains a microphone helper class to hint at developers if there is a usable microphone on the system.</span></span> <span data-ttu-id="cc41f-205">其中一個用途是在應用程式中顯示任何語音互動提示之前，要檢查系統上是否有麥克風。</span><span class="sxs-lookup"><span data-stu-id="cc41f-205">One use for it is where one would want to check if there is microphone on system before showing any speech interaction hints in the application.</span></span>

<span data-ttu-id="cc41f-206">您可以在 [[輸入/腳本/公用程式] 資料夾](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs)中找到麥克風協助程式腳本。</span><span class="sxs-lookup"><span data-stu-id="cc41f-206">The microphone helper script can be found in the [Input/Scripts/Utilities folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span></span> <span data-ttu-id="cc41f-207">GitHub 存放庫也包含示範如何使用 helper 的[小型範例](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs)。</span><span class="sxs-lookup"><span data-stu-id="cc41f-207">The GitHub repo also contains a [small sample](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) demonstrating how to use the helper.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="cc41f-208">混合現實工具組中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="cc41f-208">Voice input in Mixed Reality Toolkit</span></span>
<span data-ttu-id="cc41f-209">您可以在此場景中找到語音輸入的範例。</span><span class="sxs-lookup"><span data-stu-id="cc41f-209">You can find the examples of the voice input in this scene.</span></span>

- [<span data-ttu-id="cc41f-210">HoloToolkit-Examples/Input/場景/SpeechInputSource unity</span><span class="sxs-lookup"><span data-stu-id="cc41f-210">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
