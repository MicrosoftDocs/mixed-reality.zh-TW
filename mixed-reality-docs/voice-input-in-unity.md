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
# <a name="voice-input-in-unity"></a>在 Unity 中的語音輸入

Unity 會公開三種方式可以新增[語音輸入](voice-input.md)您的 Unity 應用程式。

KeywordRecognizer （其中兩種類型的 PhraseRecognizers），與您的應用程式可以指定字串的命令，以接聽的陣列。 GrammarRecognizer （另一種 PhraseRecognizer） 中，使用您的應用程式可以提供定義要接聽的特定文法 SRGS 檔案。 使用 DictationRecognizer，應用程式可以接聽的任何文字，及使用者提供任何提示或其他顯示其語音。

>[!NOTE]
>只有聽寫或片語辨識可以一次處理。 這表示如果 GrammarRecognizer 或 KeywordRecognizer 作用中時，不可為 DictationRecognizer active，反之亦然。

## <a name="enabling-the-capability-for-voice"></a>啟用語音功能

**麥克風**必須宣告功能，讓應用程式利用語音輸入。
1. 瀏覽至 「 編輯 > 專案設定 > 播放程式 」 在 Unity 編輯器中，請移至播放程式設定
2. 按一下 [Windows Store] 索引標籤
3. 在 「 發行的設定 > 功能 」 區段中，檢查**麥克風**功能

## <a name="phrase-recognition"></a>片語辨識

若要啟用您的應用程式接聽特定片語，然後說出使用者採取某些動作，您需要：
1. 指定的片語，以接聽使用 KeywordRecognizer 或 GrammarRecognizer
2. 處理 OnPhraseRecognized 事件並採取動作對應至片語辨識

### <a name="keywordrecognizer"></a>KeywordRecognizer

**命名空間：***UnityEngine.Windows.Speech*<br>
**類型：***KeywordRecognizer*， *PhraseRecognizedEventArgs*， *SpeechError*， *SpeechSystemStatus*

我們需要一些儲存某些按鍵 using 陳述式：

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

然後我們要加上幾個欄位至您的類別，以儲存辨識器和關鍵字]-> [動作字典：

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

現在加入到字典中 （例如 start （） 方法） 內的關鍵字。 我們在此範例中新增的 [啟用] 的關鍵字：

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

建立關鍵字辨識器，並告訴它哪些我們要用來識別：

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

現在註冊 OnPhraseRecognized 事件

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

範例處理常式是：

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

最後，啟動辨識 ！

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a>GrammarRecognizer

**命名空間：***UnityEngine.Windows.Speech*<br>
**型別**:*GrammarRecognizer*， *PhraseRecognizedEventArgs*， *SpeechError*， *SpeechSystemStatus*

如果您指定使用 SRGS 您辨識文法，會使用 GrammarRecognizer。 應用程式有多個只是幾個關鍵字，如果您想要辨識更複雜的片語，或如果您想要輕鬆地開啟和關閉一組命令，這非常有用。 請參閱：[建立使用 SRGS XML 文法](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx)檔案格式資訊。

一旦您 SRGS 文法中，而且它是在您專案中[StreamingAssets 資料夾](http://docs.unity3d.com/Manual/StreamingAssets.html):

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

建立 GrammarRecognizer，並將 SRGS 檔案的路徑傳遞它：

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

現在註冊 OnPhraseRecognized 事件

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

您會收到回呼，其中包含您可以適當地處理您 SRGS 文法中指定的資訊。 將 semanticMeanings 陣列中提供的大部分重要的資訊。

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

最後，啟動辨識 ！

```
grammarRecognizer.Start();
```

## <a name="dictation"></a>聽寫

**命名空間：***UnityEngine.Windows.Speech*<br>
**型別**:*DictationRecognizer*， *SpeechError*， *SpeechSystemStatus*

您可以使用 DictationRecognizer 使用者的語音轉換文字。 會公開 DictationRecognizer[聽寫](voice-input.md#dictation)功能和支援註冊與接聽假設和片語完成事件，讓它們說話時，您可以為這兩個您使用者提供意見反應，之後。 Start （） 和了 stop （） 方法分別啟用和停用段聽寫辨識。 完成後，辨識器，它應該處置使用 dispose （） 方法來釋放它所使用的資源。 它會釋出這些資源自動記憶體回收期間的其他效能成本如果它們不會釋放，在這之前。

有若要開始使用語音輸入所需的只有幾個步驟：
1. 建立新的 DictationRecognizer
2. 處理語音輸入事件
3. 啟動 DictationRecognizer

### <a name="enabling-the-capability-for-dictation"></a>啟用語音輸入的功能

「 網際網路用戶端 」 功能，除了上面所提的 「 麥克風 」 功能必須宣告應用程式利用語音輸入。
1. 瀏覽至"編輯 > 專案設定 > Player"頁面在 Unity 編輯器中，請移至播放程式設定
2. 按一下 [Windows Store] 索引標籤
3. 在 「 發行的設定 > 功能 」 區段中，檢查**InternetClient**功能

### <a name="dictationrecognizer"></a>DictationRecognizer

建立 DictationRecognizer 就像這樣：

```
dictationRecognizer = new DictationRecognizer();
```

有四個可以訂閱和處理來實作語音輸入行為的聽寫事件。
1. DictationResult
2. DictationComplete
3. DictationHypothesis
4. DictationError

**DictationResult**

使用者之後引發此事件，通常會在暫停句子的結尾。 完整辨識這裡傳回的字串。

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

只有在使用者進行通訊時，持續，則會引發此事件。 辨識器接聽，因為它會提供之內容的文字聽過為止。

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

引發此事件是當辨識器停止時，不論是從了 stop （） 呼叫，發生逾時或其他某些錯誤。

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

發生錯誤時，會引發此事件。

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

一旦您有訂閱，並處理您關心的語音輸入事件，請啟動 聽寫辨識器，若要開始接收事件。

```
dictationRecognizer.Start();
```

如果您不再想要保留周圍 DictationRecognizer，您要取消訂閱事件，並處置 DictationRecognizer。

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**祕訣**
* Start （） 和了 stop （） 方法分別啟用和停用段聽寫辨識。
* 完成後，辨識器，它必須處置使用 dispose （） 方法來釋放它所使用的資源。 它會釋出這些資源自動記憶體回收期間的其他效能成本如果它們不會釋放，在這之前。
* 在一段時間之後，就會發生逾時。 您可以檢查這些 DictationComplete 事件中的逾時。 有兩個逾時，要注意的：
   1. 如果辨識器啟動，且聽任何音訊第五秒，它就會逾時。
   2. 如果辨識器已提供結果，但然後聽到 20 秒的無回應，它就會逾時。

## <a name="using-both-phrase-recognition-and-dictation"></a>使用片語辨識和語音輸入

如果您想要使用應用程式中的片語辨識和語音輸入時，您必須完全關閉其中一個其他開始之前。 如果您有多個 KeywordRecognizers 執行時，您可以關閉它們全部一次使用：

```
PhraseRecognitionSystem.Shutdown();
```

若要還原至先前的狀態，所有的辨識器，DictationRecognizer 停止後，您可以呼叫：

```
PhraseRecognitionSystem.Restart();
```

您也可以開始 KeywordRecognizer，將會重新啟動 PhraseRecognitionSystem 以及。

## <a name="using-the-microphone-helper"></a>使用麥克風 helper

混合實境 Toolkit GitHub 上包含麥克風 helper 類別，可在開發人員提示，如果系統上沒有可用的麥克風。 它的其中一種用法是其中一個想要檢查是否有麥克風系統上的應用程式中顯示任何語音互動提示之前。

麥克風協助程式指令碼可在[公用程式的輸入/指令碼資料夾](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs)。 GitHub 存放庫也包含[少量樣本](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs)示範如何使用協助程式。

## <a name="voice-input-in-mixed-reality-toolkit"></a>混合實境工具組中的語音輸入
您可以在此場景中找到的語音輸入的範例。

- [HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
