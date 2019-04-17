---
title: 在 Unity 中的語音輸入
description: Unity 會公開三種方式可以新增至您的 Windows Mixed Reality 應用程式的語音輸入。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 輸入的語音、 KeywordRecognizer、 GrammarRecognizer、 麥克風、 聽寫、 語音
ms.openlocfilehash: ef8114a1c877fe9b858122e0c64628d4b71a69cd
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597011"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="44f76-104">在 Unity 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="44f76-104">Voice input in Unity</span></span>

<span data-ttu-id="44f76-105">Unity 會公開三種方式可以新增[語音輸入](voice-input.md)您的 Unity 應用程式。</span><span class="sxs-lookup"><span data-stu-id="44f76-105">Unity exposes three ways to add [Voice input](voice-input.md) to your Unity application.</span></span>

<span data-ttu-id="44f76-106">KeywordRecognizer （其中兩種類型的 PhraseRecognizers），與您的應用程式可以指定字串的命令，以接聽的陣列。</span><span class="sxs-lookup"><span data-stu-id="44f76-106">With the KeywordRecognizer (one of two types of PhraseRecognizers), your app can be given an array of string commands to listen for.</span></span> <span data-ttu-id="44f76-107">GrammarRecognizer （另一種 PhraseRecognizer） 中，使用您的應用程式可以提供定義要接聽的特定文法 SRGS 檔案。</span><span class="sxs-lookup"><span data-stu-id="44f76-107">With the GrammarRecognizer (the other type of PhraseRecognizer), your app can be given an SRGS file defining a specific grammar to listen for.</span></span> <span data-ttu-id="44f76-108">使用 DictationRecognizer，應用程式可以接聽的任何文字，及使用者提供任何提示或其他顯示其語音。</span><span class="sxs-lookup"><span data-stu-id="44f76-108">With the DictationRecognizer, your app can listen for any word and provide the user with a note or other display of their speech.</span></span>

>[!NOTE]
><span data-ttu-id="44f76-109">只有聽寫或片語辨識可以一次處理。</span><span class="sxs-lookup"><span data-stu-id="44f76-109">Only dictation or phrase recognition can be handled at once.</span></span> <span data-ttu-id="44f76-110">這表示如果 GrammarRecognizer 或 KeywordRecognizer 作用中時，不可為 DictationRecognizer active，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="44f76-110">That means if a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can not be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="44f76-111">啟用語音功能</span><span class="sxs-lookup"><span data-stu-id="44f76-111">Enabling the capability for Voice</span></span>

<span data-ttu-id="44f76-112">**麥克風**必須宣告功能，讓應用程式利用語音輸入。</span><span class="sxs-lookup"><span data-stu-id="44f76-112">The **Microphone** capability must be declared for an app to leverage Voice input.</span></span>
1. <span data-ttu-id="44f76-113">瀏覽至 「 編輯 > 專案設定 > 播放程式 」 在 Unity 編輯器中，請移至播放程式設定</span><span class="sxs-lookup"><span data-stu-id="44f76-113">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
2. <span data-ttu-id="44f76-114">按一下 [Windows Store] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="44f76-114">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="44f76-115">在 「 發行的設定 > 功能 」 區段中，檢查**麥克風**功能</span><span class="sxs-lookup"><span data-stu-id="44f76-115">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="44f76-116">片語辨識</span><span class="sxs-lookup"><span data-stu-id="44f76-116">Phrase Recognition</span></span>

<span data-ttu-id="44f76-117">若要啟用您的應用程式接聽特定片語，然後說出使用者採取某些動作，您需要：</span><span class="sxs-lookup"><span data-stu-id="44f76-117">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="44f76-118">指定的片語，以接聽使用 KeywordRecognizer 或 GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="44f76-118">Specify which phrases to listen for using a KeywordRecognizer or GrammarRecognizer</span></span>
2. <span data-ttu-id="44f76-119">處理 OnPhraseRecognized 事件並採取動作對應至片語辨識</span><span class="sxs-lookup"><span data-stu-id="44f76-119">Handle the OnPhraseRecognized event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="44f76-120">KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="44f76-120">KeywordRecognizer</span></span>

<span data-ttu-id="44f76-121">\**命名空間：\*\*\*UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="44f76-121">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="44f76-122">\**類型：\*\*\*KeywordRecognizer*， *PhraseRecognizedEventArgs*， *SpeechError*， *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="44f76-122">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="44f76-123">我們需要一些儲存某些按鍵 using 陳述式：</span><span class="sxs-lookup"><span data-stu-id="44f76-123">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="44f76-124">然後我們要加上幾個欄位至您的類別，以儲存辨識器和關鍵字]-> [動作字典：</span><span class="sxs-lookup"><span data-stu-id="44f76-124">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="44f76-125">現在加入到字典中 （例如 start （） 方法） 內的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="44f76-125">Now add a keyword to the dictionary (e.g. inside of a Start() method).</span></span> <span data-ttu-id="44f76-126">我們在此範例中新增的 [啟用] 的關鍵字：</span><span class="sxs-lookup"><span data-stu-id="44f76-126">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="44f76-127">建立關鍵字辨識器，並告訴它哪些我們要用來識別：</span><span class="sxs-lookup"><span data-stu-id="44f76-127">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="44f76-128">現在註冊 OnPhraseRecognized 事件</span><span class="sxs-lookup"><span data-stu-id="44f76-128">Now register for the OnPhraseRecognized event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="44f76-129">範例處理常式是：</span><span class="sxs-lookup"><span data-stu-id="44f76-129">An example handler is:</span></span>

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

<span data-ttu-id="44f76-130">最後，啟動辨識 ！</span><span class="sxs-lookup"><span data-stu-id="44f76-130">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="44f76-131">GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="44f76-131">GrammarRecognizer</span></span>

<span data-ttu-id="44f76-132">\**命名空間：\*\*\*UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="44f76-132">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="44f76-133">**型別**:*GrammarRecognizer*， *PhraseRecognizedEventArgs*， *SpeechError*， *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="44f76-133">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="44f76-134">如果您指定使用 SRGS 您辨識文法，會使用 GrammarRecognizer。</span><span class="sxs-lookup"><span data-stu-id="44f76-134">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="44f76-135">應用程式有多個只是幾個關鍵字，如果您想要辨識更複雜的片語，或如果您想要輕鬆地開啟和關閉一組命令，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="44f76-135">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="44f76-136">請參閱：[建立使用 SRGS XML 文法](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx)檔案格式資訊。</span><span class="sxs-lookup"><span data-stu-id="44f76-136">See: [Create Grammars Using SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) for file format information.</span></span>

<span data-ttu-id="44f76-137">一旦您 SRGS 文法中，而且它是在您專案中[StreamingAssets 資料夾](http://docs.unity3d.com/Manual/StreamingAssets.html):</span><span class="sxs-lookup"><span data-stu-id="44f76-137">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](http://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="44f76-138">建立 GrammarRecognizer，並將 SRGS 檔案的路徑傳遞它：</span><span class="sxs-lookup"><span data-stu-id="44f76-138">Create a GrammarRecognizer and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="44f76-139">現在註冊 OnPhraseRecognized 事件</span><span class="sxs-lookup"><span data-stu-id="44f76-139">Now register for the OnPhraseRecognized event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="44f76-140">您會收到回呼，其中包含您可以適當地處理您 SRGS 文法中指定的資訊。</span><span class="sxs-lookup"><span data-stu-id="44f76-140">You will get a callback containing information specified in your SRGS grammar which you can handle appropriately.</span></span> <span data-ttu-id="44f76-141">將 semanticMeanings 陣列中提供的大部分重要的資訊。</span><span class="sxs-lookup"><span data-stu-id="44f76-141">Most of the important information will be provided in the semanticMeanings array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="44f76-142">最後，啟動辨識 ！</span><span class="sxs-lookup"><span data-stu-id="44f76-142">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="44f76-143">聽寫</span><span class="sxs-lookup"><span data-stu-id="44f76-143">Dictation</span></span>

<span data-ttu-id="44f76-144">\**命名空間：\*\*\*UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="44f76-144">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="44f76-145">**型別**:*DictationRecognizer*， *SpeechError*， *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="44f76-145">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="44f76-146">您可以使用 DictationRecognizer 使用者的語音轉換文字。</span><span class="sxs-lookup"><span data-stu-id="44f76-146">Use the DictationRecognizer to convert the user's speech to text.</span></span> <span data-ttu-id="44f76-147">會公開 DictationRecognizer[聽寫](voice-input.md#dictation)功能和支援註冊與接聽假設和片語完成事件，讓它們說話時，您可以為這兩個您使用者提供意見反應，之後。</span><span class="sxs-lookup"><span data-stu-id="44f76-147">The DictationRecognizer exposes [dictation](voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="44f76-148">Start （） 和了 stop （） 方法分別啟用和停用段聽寫辨識。</span><span class="sxs-lookup"><span data-stu-id="44f76-148">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="44f76-149">完成後，辨識器，它應該處置使用 dispose （） 方法來釋放它所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="44f76-149">Once done with the recognizer, it should be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="44f76-150">它會釋出這些資源自動記憶體回收期間的其他效能成本如果它們不會釋放，在這之前。</span><span class="sxs-lookup"><span data-stu-id="44f76-150">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>

<span data-ttu-id="44f76-151">有若要開始使用語音輸入所需的只有幾個步驟：</span><span class="sxs-lookup"><span data-stu-id="44f76-151">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="44f76-152">建立新的 DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="44f76-152">Create a new DictationRecognizer</span></span>
2. <span data-ttu-id="44f76-153">處理語音輸入事件</span><span class="sxs-lookup"><span data-stu-id="44f76-153">Handle Dictation events</span></span>
3. <span data-ttu-id="44f76-154">啟動 DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="44f76-154">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="44f76-155">啟用語音輸入的功能</span><span class="sxs-lookup"><span data-stu-id="44f76-155">Enabling the capability for dictation</span></span>

<span data-ttu-id="44f76-156">「 網際網路用戶端 」 功能，除了上面所提的 「 麥克風 」 功能必須宣告應用程式利用語音輸入。</span><span class="sxs-lookup"><span data-stu-id="44f76-156">The "Internet Client" capability, in addition to the "Microphone" capability mentioned above, must be declared for an app to leverage dictation.</span></span>
1. <span data-ttu-id="44f76-157">瀏覽至"編輯 > 專案設定 > Player"頁面在 Unity 編輯器中，請移至播放程式設定</span><span class="sxs-lookup"><span data-stu-id="44f76-157">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="44f76-158">按一下 [Windows Store] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="44f76-158">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="44f76-159">在 「 發行的設定 > 功能 」 區段中，檢查**InternetClient**功能</span><span class="sxs-lookup"><span data-stu-id="44f76-159">In the "Publishing Settings > Capabilities" section, check the **InternetClient** capability</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="44f76-160">DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="44f76-160">DictationRecognizer</span></span>

<span data-ttu-id="44f76-161">建立 DictationRecognizer 就像這樣：</span><span class="sxs-lookup"><span data-stu-id="44f76-161">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="44f76-162">有四個可以訂閱和處理來實作語音輸入行為的聽寫事件。</span><span class="sxs-lookup"><span data-stu-id="44f76-162">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. <span data-ttu-id="44f76-163">DictationResult</span><span class="sxs-lookup"><span data-stu-id="44f76-163">DictationResult</span></span>
2. <span data-ttu-id="44f76-164">DictationComplete</span><span class="sxs-lookup"><span data-stu-id="44f76-164">DictationComplete</span></span>
3. <span data-ttu-id="44f76-165">DictationHypothesis</span><span class="sxs-lookup"><span data-stu-id="44f76-165">DictationHypothesis</span></span>
4. <span data-ttu-id="44f76-166">DictationError</span><span class="sxs-lookup"><span data-stu-id="44f76-166">DictationError</span></span>

<span data-ttu-id="44f76-167">**DictationResult**</span><span class="sxs-lookup"><span data-stu-id="44f76-167">**DictationResult**</span></span>

<span data-ttu-id="44f76-168">使用者之後引發此事件，通常會在暫停句子的結尾。</span><span class="sxs-lookup"><span data-stu-id="44f76-168">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="44f76-169">完整辨識這裡傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="44f76-169">The full recognized string is returned here.</span></span>

<span data-ttu-id="44f76-170">首先，訂閱 DictationResult 事件：</span><span class="sxs-lookup"><span data-stu-id="44f76-170">First, subscribe to the DictationResult event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="44f76-171">然後處理 DictationResult 回呼：</span><span class="sxs-lookup"><span data-stu-id="44f76-171">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="44f76-172">**DictationHypothesis**</span><span class="sxs-lookup"><span data-stu-id="44f76-172">**DictationHypothesis**</span></span>

<span data-ttu-id="44f76-173">只有在使用者進行通訊時，持續，則會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="44f76-173">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="44f76-174">辨識器接聽，因為它會提供之內容的文字聽過為止。</span><span class="sxs-lookup"><span data-stu-id="44f76-174">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="44f76-175">首先，訂閱 DictationHypothesis 事件：</span><span class="sxs-lookup"><span data-stu-id="44f76-175">First, subscribe to the DictationHypothesis event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="44f76-176">然後處理 DictationHypothesis 回呼：</span><span class="sxs-lookup"><span data-stu-id="44f76-176">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="44f76-177">**DictationComplete**</span><span class="sxs-lookup"><span data-stu-id="44f76-177">**DictationComplete**</span></span>

<span data-ttu-id="44f76-178">引發此事件是當辨識器停止時，不論是從了 stop （） 呼叫，發生逾時或其他某些錯誤。</span><span class="sxs-lookup"><span data-stu-id="44f76-178">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="44f76-179">首先，訂閱 DictationComplete 事件：</span><span class="sxs-lookup"><span data-stu-id="44f76-179">First, subscribe to the DictationComplete event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="44f76-180">然後處理 DictationComplete 回呼：</span><span class="sxs-lookup"><span data-stu-id="44f76-180">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="44f76-181">**DictationError**</span><span class="sxs-lookup"><span data-stu-id="44f76-181">**DictationError**</span></span>

<span data-ttu-id="44f76-182">發生錯誤時，會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="44f76-182">This event is fired when an error occurs.</span></span>

<span data-ttu-id="44f76-183">首先，訂閱 DictationError 事件：</span><span class="sxs-lookup"><span data-stu-id="44f76-183">First, subscribe to the DictationError event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="44f76-184">然後處理 DictationError 回呼：</span><span class="sxs-lookup"><span data-stu-id="44f76-184">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="44f76-185">一旦您有訂閱，並處理您關心的語音輸入事件，請啟動 聽寫辨識器，若要開始接收事件。</span><span class="sxs-lookup"><span data-stu-id="44f76-185">Once you have subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="44f76-186">如果您不再想要保留周圍 DictationRecognizer，您要取消訂閱事件，並處置 DictationRecognizer。</span><span class="sxs-lookup"><span data-stu-id="44f76-186">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="44f76-187">**祕訣**</span><span class="sxs-lookup"><span data-stu-id="44f76-187">**Tips**</span></span>
* <span data-ttu-id="44f76-188">Start （） 和了 stop （） 方法分別啟用和停用段聽寫辨識。</span><span class="sxs-lookup"><span data-stu-id="44f76-188">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="44f76-189">完成後，辨識器，它必須處置使用 dispose （） 方法來釋放它所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="44f76-189">Once done with the recognizer, it must be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="44f76-190">它會釋出這些資源自動記憶體回收期間的其他效能成本如果它們不會釋放，在這之前。</span><span class="sxs-lookup"><span data-stu-id="44f76-190">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>
* <span data-ttu-id="44f76-191">在一段時間之後，就會發生逾時。</span><span class="sxs-lookup"><span data-stu-id="44f76-191">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="44f76-192">您可以檢查這些 DictationComplete 事件中的逾時。</span><span class="sxs-lookup"><span data-stu-id="44f76-192">You can check for these timeouts in the DictationComplete event.</span></span> <span data-ttu-id="44f76-193">有兩個逾時，要注意的：</span><span class="sxs-lookup"><span data-stu-id="44f76-193">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="44f76-194">如果辨識器啟動，且聽任何音訊第五秒，它就會逾時。</span><span class="sxs-lookup"><span data-stu-id="44f76-194">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
   2. <span data-ttu-id="44f76-195">如果辨識器已提供結果，但然後聽到 20 秒的無回應，它就會逾時。</span><span class="sxs-lookup"><span data-stu-id="44f76-195">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="44f76-196">使用片語辨識和語音輸入</span><span class="sxs-lookup"><span data-stu-id="44f76-196">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="44f76-197">如果您想要使用應用程式中的片語辨識和語音輸入時，您必須完全關閉其中一個其他開始之前。</span><span class="sxs-lookup"><span data-stu-id="44f76-197">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="44f76-198">如果您有多個 KeywordRecognizers 執行時，您可以關閉它們全部一次使用：</span><span class="sxs-lookup"><span data-stu-id="44f76-198">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="44f76-199">若要還原至先前的狀態，所有的辨識器，DictationRecognizer 停止後，您可以呼叫：</span><span class="sxs-lookup"><span data-stu-id="44f76-199">In order to restore all recognizers to their previous state, after the DictationRecognizer has stopped, you can call:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="44f76-200">您也可以開始 KeywordRecognizer，將會重新啟動 PhraseRecognitionSystem 以及。</span><span class="sxs-lookup"><span data-stu-id="44f76-200">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="using-the-microphone-helper"></a><span data-ttu-id="44f76-201">使用麥克風 helper</span><span class="sxs-lookup"><span data-stu-id="44f76-201">Using the microphone helper</span></span>

<span data-ttu-id="44f76-202">混合實境 Toolkit GitHub 上包含麥克風 helper 類別，可在開發人員提示，如果系統上沒有可用的麥克風。</span><span class="sxs-lookup"><span data-stu-id="44f76-202">The Mixed Reality Toolkit on GitHub contains a microphone helper class to hint at developers if there is a usable microphone on the system.</span></span> <span data-ttu-id="44f76-203">它的其中一種用法是其中一個想要檢查是否有麥克風系統上的應用程式中顯示任何語音互動提示之前。</span><span class="sxs-lookup"><span data-stu-id="44f76-203">One use for it is where one would want to check if there is microphone on system before showing any speech interaction hints in the application.</span></span>

<span data-ttu-id="44f76-204">麥克風協助程式指令碼可在[公用程式的輸入/指令碼資料夾](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs)。</span><span class="sxs-lookup"><span data-stu-id="44f76-204">The microphone helper script can be found in the [Input/Scripts/Utilities folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span></span> <span data-ttu-id="44f76-205">GitHub 存放庫也包含[少量樣本](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs)示範如何使用協助程式。</span><span class="sxs-lookup"><span data-stu-id="44f76-205">The GitHub repo also contains a [small sample](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) demonstrating how to use the helper.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="44f76-206">混合實境工具組中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="44f76-206">Voice input in Mixed Reality Toolkit</span></span>
<span data-ttu-id="44f76-207">您可以在此場景中找到的語音輸入的範例。</span><span class="sxs-lookup"><span data-stu-id="44f76-207">You can find the examples of the voice input in this scene.</span></span>

- [<span data-ttu-id="44f76-208">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span><span class="sxs-lookup"><span data-stu-id="44f76-208">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
