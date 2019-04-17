---
title: DirectX 中的語音輸入
description: 說明如何在 DirectX 應用程式中實作語音命令和小型的片語和句子辨識，如 Windows Mixed Reality。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: 逐步解說中，語音命令、 片語、 辨識、 語音、 directx、 平台、 cortana、 windows 混合的實境
ms.openlocfilehash: 728457a495616e5f65ec3986dfb6ac60231f9e46
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2019
ms.locfileid: "59597126"
---
# <a name="voice-input-in-directx"></a>DirectX 中的語音輸入

本主題說明如何實作[語音命令](voice-input.md)，小型字詞和句子中與辨識 Windows Mixed Reality 的 DirectX 應用程式。

>[!NOTE]
>目前在這篇文章中的程式碼片段示範如何使用C++/CX 而不是 C + + 17 相容C++中所使用的 /WinRT [ C++全像攝影版的專案範本](creating-a-holographic-directx-project.md)。  概念是相等的C++/WinRT 專案，但您必須將轉譯程式碼。

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a>SpeechRecognizer 用於連續的語音命令辨識

在本節中，我們會說明如何使用連續的語音辨識來啟用您的應用程式中的語音命令。 本逐步解說使用的程式碼[HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964)範例。 當執行範例時，將其中一個已註冊的色彩命令，以變更旋轉立方體的色彩名稱。

首先，建立新**Windows::Media::SpeechRecognition::SpeechRecognizer**執行個體。

從*HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:

```
m_speechRecognizer = ref new SpeechRecognizer();
```

您必須建立一份要接聽的辨識器的語音命令。 我們在這裡，建構一組命令，變更全像圖的色彩。 為了方便起見，我們也會建立的資料，我們將在稍後使用的命令。

```
m_speechCommandList = ref new Platform::Collections::Vector<String^>();
   m_speechCommandData.clear();
   m_speechCommandList->Append(StringReference(L"white"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"grey"));
   m_speechCommandData.push_back(float4(0.5f, 0.5f, 0.5f, 1.f));
   m_speechCommandList->Append(StringReference(L"green"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"black"));
   m_speechCommandData.push_back(float4(0.1f, 0.1f, 0.1f, 1.f));
   m_speechCommandList->Append(StringReference(L"red"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"yellow"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"aquamarine"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"blue"));
   m_speechCommandData.push_back(float4(0.f, 0.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"purple"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 1.f, 1.f));
```

命令可以使用語音的文字可能不在字典中指定：

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

命令的清單會載入語音辨識器的條件約束清單。 這是藉由使用[SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx)物件。

```
SpeechRecognitionListConstraint^ spConstraint = ref new SpeechRecognitionListConstraint(m_speechCommandList);
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(spConstraint);
   create_task(m_speechRecognizer->CompileConstraintsAsync()).then([this](SpeechRecognitionCompilationResult^ compilationResult)
   {
       if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
       {
           m_speechRecognizer->ContinuousRecognitionSession->StartAsync();
       }
       else
       {
           // Handle errors here.
       }
   });
```

訂閱[ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx)語音辨識器上的事件[SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)。 當其中一個命令的已辨識時，此事件會通知您的應用程式。

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

您**OnResultGenerated**事件處理常式會接收事件資料中的[SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx)執行個體。 信賴度是比您已定義的臨界值，如果您的應用程式應該注意的事件發生。 儲存事件資料，讓您可以在後續更新迴圈中使用它。

從*HolographicVoiceInputSampleMain.cpp*:

```
// Change the cube color, if we get a valid result.
   void HolographicVoiceInputSampleMain::OnResultGenerated(SpeechContinuousRecognitionSession ^sender, SpeechContinuousRecognitionResultGeneratedEventArgs ^args)
   {
       if (args->Result->RawConfidence > 0.5f)
       {
           m_lastCommand = args->Result->Text;
       }
   }
```

請使用不過適用於您應用程式案例的資料。 在我們的範例程式碼，我們會變更根據使用者的命令，將旋轉全像 cube 的色彩。

從*HolographicVoiceInputSampleMain::Update*:

```
// Check for new speech input since the last frame.
   if (m_lastCommand != nullptr)
   {
       auto command = m_lastCommand;
       m_lastCommand = nullptr;

       int i = 0;
       for each (auto& iter in m_speechCommandList)
       {
           if (iter == command)
           {
               m_spinningCubeRenderer->SetColor(m_speechCommandData[i]);
               break;
           }

           ++i;
       }
   }
```

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a>用於單次辨識語音片語和句子中的聽寫

您可以設定要接聽的片語或句子說出使用者的語音辨識器。 在此情況下，我們會套用 SpeechRecognitionTopicConstraint，告訴語音辨識器的預期輸入類型。 應用程式工作流程如下所示，這種類型的使用案例：
1. 您的應用程式建立 SpeechRecognizer、 提供 UI 提示，並開始接聽立即讀出命令。
2. 使用者所說片語或句子。
3. 使用者的語音辨識會執行，而且結果會傳回到應用程式。 此時，您的應用程式應該提供 UI 提示，指出發生辨識。
4. 根據您想要回應的信心層級和語音辨識結果的信賴等級，您的應用程式可以處理結果，並適時回應。

本節說明如何建立 SpeechRecognizer、 編譯條件約束，以及接聽語音輸入。

下列程式碼會編譯主題條件約束，在此情況下最適合用於 Web 搜尋。

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

如果編譯成功，我們可以繼續使用語音辨識。

```
try
       {
           SpeechRecognitionCompilationResult^ compilationResult = previousTask.get();

           // Check to make sure that the constraints were in a proper format and the recognizer was able to compile it.
           if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
           {
               // If the compilation succeeded, we can start listening for the user's spoken phrase or sentence.
               create_task(m_speechRecognizer->RecognizeAsync()).then([this](task<SpeechRecognitionResult^>& previousTask)
               {
```

然後會將結果傳回至應用程式。 如果我們有足夠的信心，結果中，我們可以處理命令。 此程式碼範例會使用至少要有中度信心處理結果。

```
try
                   {
                       auto result = previousTask.get();

                       if (result->Status != SpeechRecognitionResultStatus::Success)
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech recognition was not successful: ") +
                               result->Status.ToString()->Data() +
                               L"\n"
                               );
                       }

                       // In this example, we look for at least medium confidence in the speech result.
                       if ((result->Confidence == SpeechRecognitionConfidence::High) ||
                           (result->Confidence == SpeechRecognitionConfidence::Medium))
                       {
                           // If the user said a color name anywhere in their phrase, it will be recognized in the
                           // Update loop; then, the cube will change color.
                           m_lastCommand = result->Text;

                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech phrase was: ") +
                               m_lastCommand->Data() +
                               L"\n"
                               );
                       }
                       else
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Recognition confidence not high enough: ") +
                               result->Confidence.ToString()->Data() +
                               L"\n"
                               );
                       }
                   }
```

每當您使用語音辨識時，您應該注意的例外狀況可能表示使用者已關閉系統的隱私權設定 中的麥克風。 在初始化期間，或在辨識時，也可能會發生。

```
catch (Exception^ exception)
                   {
                       // Note that if you get an "Access is denied" exception, you might need to enable the microphone
                       // privacy setting on the device and/or add the microphone capability to your app manifest.

                       PrintWstringToDebugConsole(
                           std::wstring(L"Speech recognizer error: ") +
                           exception->ToString()->Data() +
                           L"\n"
                           );
                   }
               });

               return true;
           }
           else
           {
               OutputDebugStringW(L"Could not initialize predefined grammar speech engine!\n");

               // Handle errors here.
               return false;
           }
       }
       catch (Exception^ exception)
       {
           // Note that if you get an "Access is denied" exception, you might need to enable the microphone
           // privacy setting on the device and/or add the microphone capability to your app manifest.

           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to initialize predefined grammar speech engine:") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
           return false;
       }
   });
```

**注意：** 有數個預先定義的[SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx)適用於最佳化語音辨識。
* 如果您想要聽寫的最佳化，請使用聽寫案例：

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* 當使用語音來執行 Web 搜尋，您可以使用 Web 特定案例條件約束，如下所示：

```
// Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
```
* 您可以使用表單條件約束來填寫表單。 在此情況下，最好是將您自己最適合用於填寫表單的文法。

```
// Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
```
* 您可以提供您自己使用 SRGS 格式的文法。

## <a name="use-continuous-freeform-speech-dictation"></a>使用連續的任意形狀的語音聽寫

請參閱 Windows 10 UWP 語音程式碼範例，針對連續聽寫案例[這裡。](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)

## <a name="handle-degradation-in-quality"></a>降低品質，控制代碼

在環境中的條件有時候可以防止語音辨識工作。 比方說，空間可能會太吵雜，或使用者可能會說話音量太高。 語音辨識 API 會提供資訊，可能的話，品質造成效能降低的情況。

這項資訊會推送至您的應用程式使用 WinRT 事件。 以下是如何訂閱此事件的範例。

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

在程式碼範例中，我們選擇的條件資訊寫入偵錯主控台。 應用程式可能會想要提供意見反應，使用者可透過 UI、 語音合成，並依此類推，或者它可能需要有不同的行為語音時中斷的暫時降低品質。

```
void HolographicSpeechPromptSampleMain::OnSpeechQualityDegraded(SpeechRecognizer^ recognizer, SpeechRecognitionQualityDegradingEventArgs^ args)
   {
       switch (args->Problem)
       {
       case SpeechRecognitionAudioProblem::TooFast:
           OutputDebugStringW(L"The user spoke too quickly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooSlow:
           OutputDebugStringW(L"The user spoke too slowly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooQuiet:
           OutputDebugStringW(L"The user spoke too softly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooLoud:
           OutputDebugStringW(L"The user spoke too loudly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooNoisy:
           OutputDebugStringW(L"There is too much noise in the signal.\n");
           break;

       case SpeechRecognitionAudioProblem::NoSignal:
           OutputDebugStringW(L"There is no signal.\n");
           break;

       case SpeechRecognitionAudioProblem::None:
       default:
           OutputDebugStringW(L"An error was reported with no information.\n");
           break;
       }
   }
```

如果您不使用 ref 類別建立您的 DirectX 應用程式，您必須取消訂閱事件之前釋放或重新建立您的語音辨識器。 HolographicSpeechPromptSample 已停止辨識，並取消訂閱事件的常式就像這樣：

```
Concurrency::task<void> HolographicSpeechPromptSampleMain::StopCurrentRecognizerIfExists()
   {
       return create_task([this]()
       {
           if (m_speechRecognizer != nullptr)
           {
               return create_task(m_speechRecognizer->StopRecognitionAsync()).then([this]()
               {
                   m_speechRecognizer->RecognitionQualityDegrading -= m_speechRecognitionQualityDegradedToken;

                   if (m_speechRecognizer->ContinuousRecognitionSession != nullptr)
                   {
                       m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated -= m_speechRecognizerResultEventToken;
                   }
               });
           }
           else
           {
               return create_task([this]() { m_speechRecognizer = nullptr; });
           }
       });
   }
```

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a>使用語音合成，提供可發出聲音的語音提示

全像攝影版的語音範例可用於語音合成可發出聲音的指示提供給使用者。 本主題會逐步建立合成的語音的範例中，以及玩它使用 HRTF 音訊 Api 的程序。

您應該提供要求的輸入片語時，會提示您自己的語音。 這也可以很有幫助，指出當語音命令可以讀出，針對連續辨識情節。 以下是如何利用語音合成器; 的範例請注意，您也可以使用預先錄製的聲音美工圖案、 visual 的 UI 中或其他指標的功能，比方說，在提示字元不是動態的案例中。

首先，建立 SpeechSynthesizer 物件：

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

您也必須具有要合成文字的字串：

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

使用 SynthesizeTextToStreamAsync 以非同步方式，被合成語音。 在這裡，我們開始一項非同步工作合成語音。

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

語音合成是傳送以位元組資料流。 我們可以初始化使用該位元組資料流; XAudio2 語音如需我們全像攝影版的程式碼範例中，我們播放它為 HRTF 音訊效果。

```
Windows::Media::SpeechSynthesis::SpeechSynthesisStream^ stream = synthesisStreamTask.get();

           auto hr = m_speechSynthesisSound.Initialize(stream, 0);
           if (SUCCEEDED(hr))
           {
               m_speechSynthesisSound.SetEnvironment(HrtfEnvironment::Small);
               m_speechSynthesisSound.Start();

               // Amount of time to pause after the audio prompt is complete, before listening
               // for speech input.
               static const float bufferTime = 0.15f;

               // Wait until the prompt is done before listening.
               m_secondsUntilSoundIsComplete = m_speechSynthesisSound.GetDuration() + bufferTime;
               m_waitingForSpeechPrompt = true;
           }
       }
```

為透過語音辨識，語音合成會擲回例外狀況發生錯誤時。

```
catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to synthesize speech: ") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
       }
   });
```

## <a name="see-also"></a>另請參閱
* [語音應用程式的設計](https://msdn.microsoft.com/library/dn596121.aspx)
* [DirectX 中的空間音效](spatial-sound-in-directx.md)
* [SpeechRecognitionAndSynthesis 範例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
