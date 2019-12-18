---
title: DirectX 中的語音輸入
description: 說明如何在適用于 Windows Mixed Reality 的 DirectX 應用程式中，執行語音命令和小型片語和句子辨識。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: 逐步解說，語音命令，片語，辨識，語音，directx，平臺，cortana，windows mixed reality
ms.openlocfilehash: c0a7ca85c24147e607603e733c9d191c64cbd927
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181818"
---
# <a name="voice-input-in-directx"></a>DirectX 中的語音輸入

本文說明如何在適用于 Windows Mixed Reality 的 DirectX 應用程式中，執行[語音命令](voice-input.md)加上小型片語和句子辨識。

>[!NOTE]
>本文中的程式碼片段使用C++/cx，而不是 C + 17 相容C++的/WinRT，用於[ C++ ](creating-a-holographic-directx-project.md)全像攝影專案範本。  概念對C++/WinRT 專案而言是相當的，但您必須轉譯程式碼。

## <a name="use-speechrecognizer-for-continuous-speech-recognition"></a>使用 SpeechRecognizer 進行連續語音辨識

本節說明如何使用連續的語音辨識，在您的應用程式中啟用語音命令。 本逐步解說會使用[HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964)範例中的程式碼。 當範例正在執行時，請說出其中一個已註冊的色彩命令的名稱，以變更旋轉 cube 的色彩。

首先，建立新的*Windows：： Media：： SpeechRecognition：： SpeechRecognizer*實例。

From *HolographicVoiceInputSampleMain：： CreateSpeechConstraintsForCurrentState*：

```
m_speechRecognizer = ref new SpeechRecognizer();
```

建立語音命令清單，以供辨識器接聽。 在這裡，我們會建立一組命令來變更全息影像的色彩。 為了方便起見，我們也會建立稍後用於命令的資料。

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

您可以使用字典中可能不會有的語音文字來指定命令。

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

若要將命令清單載入至語音辨識器的條件約束清單，請使用[SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx)物件。

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

訂閱語音辨識器[SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)上的[ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx)事件。 當您的其中一個命令已被辨識時，此事件會通知您的應用程式。

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

您的*OnResultGenerated*事件處理常式會接收[SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx)實例中的事件資料。 如果信賴度大於您所定義的臨界值，您的應用程式應該會注意到事件已發生。 儲存事件資料，以便您可以在後續的更新迴圈中使用它。

從*HolographicVoiceInputSampleMain*：

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

在我們的範例程式碼中，我們會根據使用者的命令來變更旋轉全息影像 cube 的色彩。

從*HolographicVoiceInputSampleMain：： Update*：

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

## <a name="use-one-shot-recognition"></a>使用「一次性」辨識

您可以設定語音辨識器來接聽使用者所說的片語或句子。 在此情況下，我們會套用*SpeechRecognitionTopicConstraint* ，告訴語音辨識器預期的輸入類型。 以下是此案例的應用程式工作流程：
1. 您的應用程式會建立 SpeechRecognizer、提供 UI 提示，並開始接聽語音命令。
2. 使用者說出一個片語或句子。
3. 會進行使用者語音的辨識，並將結果傳回給應用程式。 此時，您的應用程式應該提供 UI 提示，表示已發生辨識。
4. 視您想要回應的信賴等級和語音辨識結果的信賴等級而定，您的應用程式可以處理結果並適當地回應。

本節說明如何建立 SpeechRecognizer、編譯條件約束，以及接聽語音輸入。

下列程式碼會編譯主題條件約束，在此案例中會針對 web 搜尋進行優化。

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

如果編譯成功，我們可以繼續進行「語音辨識」。

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

然後，結果會傳回給應用程式。 如果在結果中有足夠的信心，我們可以處理此命令。 此程式碼範例會處理具有至少中等信賴度的結果。

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

當您使用 [語音辨識] 時，請留意可能表示使用者已在系統隱私權設定中關閉麥克風的例外狀況。 這可能會在初始化或辨識期間發生。

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

> [!NOTE]
> 有數個預先定義的[SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx)可供您用來優化語音辨識。

* 若要優化聽寫，請使用聽寫案例。<br/>
   ```
   // Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
   ```

* 針對語音 web 搜尋，請使用下列 web 特定的案例條件約束。

   ```
   // Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
   ```

* 使用表單條件約束來填滿表單。 在這種情況下，最好套用您自己的文法，針對填寫表單進行優化。

   ```
   // Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
   ```
* 您可以用 SRGS 格式提供自己的文法。

## <a name="use-continuous-recognition"></a>使用連續辨識

如需連續聽寫案例，請參閱[Windows 10 UWP 語音程式碼範例](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)。

## <a name="handle-quality-degradation"></a>處理品質降低

環境條件有時會干擾語音辨識。 例如，房間可能太過雜訊，或使用者可能會說話太大的聲音。 語音辨識 API 會盡可能提供導致品質降低的條件相關資訊。 此資訊會透過 WinRT 事件推送至您的應用程式。 下列範例顯示如何訂閱此事件。

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

在我們的程式碼範例中，我們會將條件資訊寫入至偵錯工具主控台。 應用程式可能會想要透過 UI、語音合成和另一個方法，提供意見反應給使用者。 或者，當語音因品質暫時降低而中斷時，可能需要有不同的行為。

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

如果您不是使用 ref 類別來建立 DirectX 應用程式，則必須先取消訂閱事件，再釋放或重新建立語音辨識器。 HolographicSpeechPromptSample 有一個常式，可停止辨識和取消訂閱事件。

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

## <a name="use-speech-synthesis-to-provide-audible-prompts"></a>使用語音合成來提供可聽見的提示

全像攝影語音範例會使用語音合成，向使用者提供可聽見的指示。 本節說明如何建立合成的語音範例，然後透過 HRTF 音訊 Api 重新播放它。

當您要求片語輸入時，您應該提供自己的語音提示。 提示也可以協助指出語音命令何時可以針對連續辨識案例說話。 下列範例示範如何使用語音合成器來執行這項操作。 您也可以使用預先錄製的語音剪輯、視覺 UI 或要說出的另一個指標，例如，在提示不是動態的案例中。

首先，建立 SpeechSynthesizer 物件。

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

您也需要包含要合成之文字的字串。

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

語音會透過 SynthesizeTextToStreamAsync 以非同步方式合成。 在這裡，我們會開始合成語音的非同步工作。

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

語音合成是以位元組資料流程的形式傳送。 我們可以使用該位元組資料流程來初始化 XAudio2 的聲音。 在我們的全像攝影程式碼範例中，我們會以 HRTF 的音訊效果來播放它。

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

如同語音辨識，如果發生錯誤，語音合成會擲回例外狀況。

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

## <a name="see-also"></a>請參閱
* [語音應用程式設計](https://msdn.microsoft.com/library/dn596121.aspx)
* [SpeechRecognitionAndSynthesis 範例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
