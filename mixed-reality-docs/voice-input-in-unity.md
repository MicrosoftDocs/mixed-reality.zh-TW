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
# <a name="voice-input-in-unity"></a>Unity 中的語音輸入

>[!NOTE]
>除了下列資訊之外，請考慮使用認知語音服務 SDK 的 Unity 外掛程式，其具有更佳的語音精確度結果，並可讓您輕鬆存取語音轉文字解碼和先進的語音功能，例如對話方塊、意圖型互動、轉譯、文字轉換語音和自然語言語音辨識。 在這裡尋找範例和檔： https://docs.microsoft.com//azure/cognitive-services/speech-service/quickstart-csharp-unity   

Unity 會公開三種將[語音輸入](voice-input.md)新增至 Unity 應用程式的方式。

使用 KeywordRecognizer （PhraseRecognizers 的兩種類型之一）時，您的應用程式可以指定要接聽的字串命令陣列。 使用 GrammarRecognizer （PhraseRecognizer 的其他類型）時，您的應用程式可以指定一個 SRGS 檔案，以定義要接聽的特定文法。 透過 DictationRecognizer，您的應用程式可以接聽任何單字，並為使用者提供其語音的附注或其他顯示。

>[!NOTE]
>只能一次處理聽寫或片語辨識。 這表示，如果 GrammarRecognizer 或 KeywordRecognizer 作用中，DictationRecognizer 就無法作用，反之亦然。

## <a name="enabling-the-capability-for-voice"></a>啟用語音功能

必須為應用程式宣告**麥克風**功能，才能利用語音輸入。
1. 在 Unity 編輯器中，流覽至 [編輯 > 專案設定 > Player]，移至播放程式設定
2. 按一下 [Windows Store] 索引標籤
3. 在 [發佈設定 > 功能] 區段中，檢查**麥克風**功能

## <a name="phrase-recognition"></a>片語辨識

若要讓您的應用程式接聽使用者所說的特定片語，請採取一些動作，您必須：
1. 使用 KeywordRecognizer 或 GrammarRecognizer 指定要接聽的片語
2. 處理 OnPhraseRecognized 事件，並採取對應至已辨識片語的動作

### <a name="keywordrecognizer"></a>KeywordRecognizer

**命名空間：** *UnityEngine*<br>
**類型：** *KeywordRecognizer*、 *PhraseRecognizedEventArgs*、 *SpeechError*、 *SpeechSystemStatus*

我們需要幾個 using 語句來儲存一些按鍵：

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

接著，讓我們將幾個欄位新增至您的類別，以儲存辨識器和關鍵字 > 動作字典：

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

現在將關鍵字新增至字典（例如，在 Start （）方法內）。 我們要在此範例中新增 "activate" 關鍵字：

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

建立關鍵字辨識器並告訴它我們要辨識的內容：

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

立即註冊 OnPhraseRecognized 事件

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

範例處理常式如下：

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

最後，開始辨識！

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a>GrammarRecognizer

**命名空間：** *UnityEngine*<br>
**類型**： *GrammarRecognizer*、 *PhraseRecognizedEventArgs*、 *SpeechError*、 *SpeechSystemStatus*

如果您要使用 SRGS 來指定辨識文法，則會使用 GrammarRecognizer。 如果您的應用程式有多個關鍵字，如果您想要辨識較複雜的片語，或如果您想要輕鬆地開啟和關閉命令集，這項功能就很有用。 請參閱：[使用 SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx)為檔案格式資訊建立文法。

一旦您有了 SRGS 文法，它就會在您的專案中[StreamingAssets 資料夾](https://docs.unity3d.com/Manual/StreamingAssets.html)內：

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

建立 GrammarRecognizer，並將路徑傳遞至您的 SRGS 檔案：

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

立即註冊 OnPhraseRecognized 事件

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

您會取得一個回呼，其中包含您可以適當處理的 [SRGS 文法] 中所指定的資訊。 大部分的重要資訊將會在 semanticMeanings 陣列中提供。

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

最後，開始辨識！

```
grammarRecognizer.Start();
```

## <a name="dictation"></a>聽寫

**命名空間：** *UnityEngine*<br>
**類型**： *DictationRecognizer*、 *SpeechError*、 *SpeechSystemStatus*

使用 DictationRecognizer 將使用者的語音轉換成文字。 DictationRecognizer 會公開[聽寫](voice-input.md#dictation)功能，並支援註冊和接聽假設和片語完成的事件，讓您可以在使用者說話和之後，提供意見反應給您的使用者。 Start （）和 Stop （）方法分別啟用和停用聽寫辨識。 完成辨識器之後，應該使用 Dispose （）方法來釋放它所使用的資源。 它會在垃圾收集期間以額外的效能成本自動釋放這些資源（如果之前未釋放）。

開始使用聽寫只需要幾個步驟：
1. 建立新的 DictationRecognizer
2. 處理聽寫事件
3. 啟動 DictationRecognizer

### <a name="enabling-the-capability-for-dictation"></a>啟用聽寫功能

除了上面提到的「麥克風」功能以外，您必須為應用程式宣告「網際網路用戶端」功能，才能利用聽寫。
1. 在 Unity 編輯器中，流覽至 [編輯 > 專案設定 > Player] 頁面，移至播放程式設定
2. 按一下 [Windows Store] 索引標籤
3. 在 [發佈設定 > 功能] 區段中，檢查**InternetClient**功能

### <a name="dictationrecognizer"></a>DictationRecognizer

建立 DictationRecognizer，如下所示：

```
dictationRecognizer = new DictationRecognizer();
```

有四個聽寫事件可供訂閱並處理來執行聽寫行為。
1. DictationResult
2. DictationComplete
3. DictationHypothesis
4. DictationError

**DictationResult**

這個事件會在使用者暫停之後引發，通常是在句子的結尾。 這裡會傳回完整辨識的字串。

首先，訂閱 DictationResult 事件：

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

然後處理 DictationResult 回呼：

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

**DictationHypothesis**

當使用者在交談時，會持續引發此事件。 當辨識器接聽時，它會提供目前為止聽到的文字。

首先，訂閱 DictationHypothesis 事件：

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

然後處理 DictationHypothesis 回呼：

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

**DictationComplete**

當辨識器停止時，不論是從呼叫停止（），還是發生超時，或某個其他錯誤，都會引發此事件。

首先，訂閱 DictationComplete 事件：

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

然後處理 DictationComplete 回呼：

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

**DictationError**

發生錯誤時，就會引發此事件。

首先，訂閱 DictationError 事件：

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

然後處理 DictationError 回呼：

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

當您訂閱並處理您關心的聽寫事件之後，請啟動聽寫辨識器以開始接收事件。

```
dictationRecognizer.Start();
```

如果您不想再讓 DictationRecognizer 保持不變，您必須取消訂閱事件並處置 DictationRecognizer。

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**各種**
* Start （）和 Stop （）方法分別啟用和停用聽寫辨識。
* 完成辨識器之後，必須使用 Dispose （）方法來處置它，以釋放它所使用的資源。 它會在垃圾收集期間以額外的效能成本自動釋放這些資源（如果之前未釋放）。
* 在設定的一段時間後發生超時。 您可以在 DictationComplete 事件中檢查這些超時。 有兩個要注意的超時：
   1. 如果辨識器啟動且未在前五秒聽到任何音訊，則會超時。
   2. 如果辨識器已指定結果，但接著會聽到24秒的無聲，則會超時。

## <a name="using-both-phrase-recognition-and-dictation"></a>同時使用片語辨識和聽寫

如果您想要在您的應用程式中同時使用片語辨識和聽寫，您必須完全關閉其中一項，然後才能啟動另一個。 如果您有多個 KeywordRecognizers 正在執行，您可以一次將它們全部關閉，方法是：

```
PhraseRecognitionSystem.Shutdown();
```

為了將所有辨識器還原成先前的狀態，在 DictationRecognizer 停止之後，您可以呼叫：

```
PhraseRecognitionSystem.Restart();
```

您也可以直接啟動 KeywordRecognizer，這也會重新開機 PhraseRecognitionSystem。

## <a name="using-the-microphone-helper"></a>使用麥克風協助程式

GitHub 上的混合現實工具組包含麥克風協助程式類別，可在系統上有可用的麥克風時，在開發人員提示。 其中一個用途是在應用程式中顯示任何語音互動提示之前，要檢查系統上是否有麥克風。

您可以在 [[輸入/腳本/公用程式] 資料夾](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs)中找到麥克風協助程式腳本。 GitHub 存放庫也包含示範如何使用 helper 的[小型範例](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs)。

## <a name="voice-input-in-mixed-reality-toolkit"></a>混合現實工具組中的語音輸入
您可以在此場景中找到語音輸入的範例。

- [HoloToolkit-Examples/Input/場景/SpeechInputSource unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
