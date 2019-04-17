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
# <a name="voice-input-in-directx"></a><span data-ttu-id="21e10-104">DirectX 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="21e10-104">Voice input in DirectX</span></span>

<span data-ttu-id="21e10-105">本主題說明如何實作[語音命令](voice-input.md)，小型字詞和句子中與辨識 Windows Mixed Reality 的 DirectX 應用程式。</span><span class="sxs-lookup"><span data-stu-id="21e10-105">This topic explains how to implement [voice commands](voice-input.md), and small phrase and sentence recognition in a DirectX app for Windows Mixed Reality.</span></span>

>[!NOTE]
><span data-ttu-id="21e10-106">目前在這篇文章中的程式碼片段示範如何使用C++/CX 而不是 C + + 17 相容C++中所使用的 /WinRT [ C++全像攝影版的專案範本](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="21e10-106">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="21e10-107">概念是相等的C++/WinRT 專案，但您必須將轉譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="21e10-107">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a><span data-ttu-id="21e10-108">SpeechRecognizer 用於連續的語音命令辨識</span><span class="sxs-lookup"><span data-stu-id="21e10-108">Use a SpeechRecognizer for continuous recognition of voice commands</span></span>

<span data-ttu-id="21e10-109">在本節中，我們會說明如何使用連續的語音辨識來啟用您的應用程式中的語音命令。</span><span class="sxs-lookup"><span data-stu-id="21e10-109">In this section, we describe how to use continuous speech recognition to enable voice commands in your app.</span></span> <span data-ttu-id="21e10-110">本逐步解說使用的程式碼[HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964)範例。</span><span class="sxs-lookup"><span data-stu-id="21e10-110">This walkthrough uses code from the [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964) Sample.</span></span> <span data-ttu-id="21e10-111">當執行範例時，將其中一個已註冊的色彩命令，以變更旋轉立方體的色彩名稱。</span><span class="sxs-lookup"><span data-stu-id="21e10-111">When the sample is running, speak the name of one of the registered color commands to change the color of the spinning cube.</span></span>

<span data-ttu-id="21e10-112">首先，建立新**Windows::Media::SpeechRecognition::SpeechRecognizer**執行個體。</span><span class="sxs-lookup"><span data-stu-id="21e10-112">First, create a new **Windows::Media::SpeechRecognition::SpeechRecognizer** instance.</span></span>

<span data-ttu-id="21e10-113">從*HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span><span class="sxs-lookup"><span data-stu-id="21e10-113">From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span></span>

```
m_speechRecognizer = ref new SpeechRecognizer();
```

<span data-ttu-id="21e10-114">您必須建立一份要接聽的辨識器的語音命令。</span><span class="sxs-lookup"><span data-stu-id="21e10-114">You'll need to create a list of speech commands for the recognizer to listen for.</span></span> <span data-ttu-id="21e10-115">我們在這裡，建構一組命令，變更全像圖的色彩。</span><span class="sxs-lookup"><span data-stu-id="21e10-115">Here, we construct a set of commands to change the color of a hologram.</span></span> <span data-ttu-id="21e10-116">為了方便起見，我們也會建立的資料，我們將在稍後使用的命令。</span><span class="sxs-lookup"><span data-stu-id="21e10-116">For the sake of convenience, we also create the data that we'll use for the commands later on.</span></span>

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

<span data-ttu-id="21e10-117">命令可以使用語音的文字可能不在字典中指定：</span><span class="sxs-lookup"><span data-stu-id="21e10-117">Commands can be specified using phonetic words that might not be in a dictionary:</span></span>

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

<span data-ttu-id="21e10-118">命令的清單會載入語音辨識器的條件約束清單。</span><span class="sxs-lookup"><span data-stu-id="21e10-118">The list of commands is loaded into the list of constraints for the speech recognizer.</span></span> <span data-ttu-id="21e10-119">這是藉由使用[SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx)物件。</span><span class="sxs-lookup"><span data-stu-id="21e10-119">This is done by using a [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) object.</span></span>

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

<span data-ttu-id="21e10-120">訂閱[ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx)語音辨識器上的事件[SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)。</span><span class="sxs-lookup"><span data-stu-id="21e10-120">Subscribe to the [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) event on the speech recognizer's [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span></span> <span data-ttu-id="21e10-121">當其中一個命令的已辨識時，此事件會通知您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="21e10-121">This event notifies your app when one of your commands has been recognized.</span></span>

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

<span data-ttu-id="21e10-122">您**OnResultGenerated**事件處理常式會接收事件資料中的[SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx)執行個體。</span><span class="sxs-lookup"><span data-stu-id="21e10-122">Your **OnResultGenerated** event handler receives event data in a [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) instance.</span></span> <span data-ttu-id="21e10-123">信賴度是比您已定義的臨界值，如果您的應用程式應該注意的事件發生。</span><span class="sxs-lookup"><span data-stu-id="21e10-123">If the confidence is greater than the threshold you have defined, your app should note that the event happened.</span></span> <span data-ttu-id="21e10-124">儲存事件資料，讓您可以在後續更新迴圈中使用它。</span><span class="sxs-lookup"><span data-stu-id="21e10-124">Save the event data so that you can make use of it in a subsequent update loop.</span></span>

<span data-ttu-id="21e10-125">從*HolographicVoiceInputSampleMain.cpp*:</span><span class="sxs-lookup"><span data-stu-id="21e10-125">From *HolographicVoiceInputSampleMain.cpp*:</span></span>

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

<span data-ttu-id="21e10-126">請使用不過適用於您應用程式案例的資料。</span><span class="sxs-lookup"><span data-stu-id="21e10-126">Make use of the data however applicable to your app scenario.</span></span> <span data-ttu-id="21e10-127">在我們的範例程式碼，我們會變更根據使用者的命令，將旋轉全像 cube 的色彩。</span><span class="sxs-lookup"><span data-stu-id="21e10-127">In our example code, we change the color of the spinning hologram cube according to the user's command.</span></span>

<span data-ttu-id="21e10-128">從*HolographicVoiceInputSampleMain::Update*:</span><span class="sxs-lookup"><span data-stu-id="21e10-128">From *HolographicVoiceInputSampleMain::Update*:</span></span>

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

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a><span data-ttu-id="21e10-129">用於單次辨識語音片語和句子中的聽寫</span><span class="sxs-lookup"><span data-stu-id="21e10-129">Use dictation for one-shot recognition of speech phrases and sentences</span></span>

<span data-ttu-id="21e10-130">您可以設定要接聽的片語或句子說出使用者的語音辨識器。</span><span class="sxs-lookup"><span data-stu-id="21e10-130">You can configure a speech recognizer to listen for phrases or sentences spoken by the user.</span></span> <span data-ttu-id="21e10-131">在此情況下，我們會套用 SpeechRecognitionTopicConstraint，告訴語音辨識器的預期輸入類型。</span><span class="sxs-lookup"><span data-stu-id="21e10-131">In this case, we apply a SpeechRecognitionTopicConstraint that tells the speech recognizer what type of input to expect.</span></span> <span data-ttu-id="21e10-132">應用程式工作流程如下所示，這種類型的使用案例：</span><span class="sxs-lookup"><span data-stu-id="21e10-132">The app workflow is as follows, for this type of use case:</span></span>
1. <span data-ttu-id="21e10-133">您的應用程式建立 SpeechRecognizer、 提供 UI 提示，並開始接聽立即讀出命令。</span><span class="sxs-lookup"><span data-stu-id="21e10-133">Your app creates the SpeechRecognizer, provides UI prompts, and starts listening for a command to be spoken immediately.</span></span>
2. <span data-ttu-id="21e10-134">使用者所說片語或句子。</span><span class="sxs-lookup"><span data-stu-id="21e10-134">The user speaks a phrase, or sentence.</span></span>
3. <span data-ttu-id="21e10-135">使用者的語音辨識會執行，而且結果會傳回到應用程式。</span><span class="sxs-lookup"><span data-stu-id="21e10-135">Recognition of the user's speech is performed, and a result is returned to the app.</span></span> <span data-ttu-id="21e10-136">此時，您的應用程式應該提供 UI 提示，指出發生辨識。</span><span class="sxs-lookup"><span data-stu-id="21e10-136">At this point, your app should provide a UI prompt indicating that recognition has occurred.</span></span>
4. <span data-ttu-id="21e10-137">根據您想要回應的信心層級和語音辨識結果的信賴等級，您的應用程式可以處理結果，並適時回應。</span><span class="sxs-lookup"><span data-stu-id="21e10-137">Depending on the confidence level you want to respond to and the confidence level of the speech recognition result, your app can process the result and respond as appropriate.</span></span>

<span data-ttu-id="21e10-138">本節說明如何建立 SpeechRecognizer、 編譯條件約束，以及接聽語音輸入。</span><span class="sxs-lookup"><span data-stu-id="21e10-138">This section describes how to create a SpeechRecognizer, compile the constraint, and listen for speech input.</span></span>

<span data-ttu-id="21e10-139">下列程式碼會編譯主題條件約束，在此情況下最適合用於 Web 搜尋。</span><span class="sxs-lookup"><span data-stu-id="21e10-139">The following code compiles the topic constraint, which in this case is optimized for Web search.</span></span>

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

<span data-ttu-id="21e10-140">如果編譯成功，我們可以繼續使用語音辨識。</span><span class="sxs-lookup"><span data-stu-id="21e10-140">If compilation succeeds, we can proceed with speech recognition.</span></span>

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

<span data-ttu-id="21e10-141">然後會將結果傳回至應用程式。</span><span class="sxs-lookup"><span data-stu-id="21e10-141">The result is then returned to the app.</span></span> <span data-ttu-id="21e10-142">如果我們有足夠的信心，結果中，我們可以處理命令。</span><span class="sxs-lookup"><span data-stu-id="21e10-142">If we are confident enough in the result, we can process the command.</span></span> <span data-ttu-id="21e10-143">此程式碼範例會使用至少要有中度信心處理結果。</span><span class="sxs-lookup"><span data-stu-id="21e10-143">This code example processes results with at least Medium confidence.</span></span>

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

<span data-ttu-id="21e10-144">每當您使用語音辨識時，您應該注意的例外狀況可能表示使用者已關閉系統的隱私權設定 中的麥克風。</span><span class="sxs-lookup"><span data-stu-id="21e10-144">Whenever you use speech recognition, you should watch for exceptions that could indicate the user has turned off the microphone in the system privacy settings.</span></span> <span data-ttu-id="21e10-145">在初始化期間，或在辨識時，也可能會發生。</span><span class="sxs-lookup"><span data-stu-id="21e10-145">This can happen during initialization, or during recognition.</span></span>

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

<span data-ttu-id="21e10-146">**注意：** 有數個預先定義的[SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx)適用於最佳化語音辨識。</span><span class="sxs-lookup"><span data-stu-id="21e10-146">**NOTE:** There are several predefined [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) available for optimizing speech recognition.</span></span>
* <span data-ttu-id="21e10-147">如果您想要聽寫的最佳化，請使用聽寫案例：</span><span class="sxs-lookup"><span data-stu-id="21e10-147">If you want to optimize for dictation, use the Dictation scenario:</span></span>

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* <span data-ttu-id="21e10-148">當使用語音來執行 Web 搜尋，您可以使用 Web 特定案例條件約束，如下所示：</span><span class="sxs-lookup"><span data-stu-id="21e10-148">When using speech to perform a Web search, you can use a Web-specific scenario constraint as follows:</span></span>

```
// Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
```
* <span data-ttu-id="21e10-149">您可以使用表單條件約束來填寫表單。</span><span class="sxs-lookup"><span data-stu-id="21e10-149">Use the form constraint to fill out forms.</span></span> <span data-ttu-id="21e10-150">在此情況下，最好是將您自己最適合用於填寫表單的文法。</span><span class="sxs-lookup"><span data-stu-id="21e10-150">In this case, it is best to apply your own grammar that is optimized for filling out your form.</span></span>

```
// Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
```
* <span data-ttu-id="21e10-151">您可以提供您自己使用 SRGS 格式的文法。</span><span class="sxs-lookup"><span data-stu-id="21e10-151">You can provide your own grammar using the SRGS format.</span></span>

## <a name="use-continuous-freeform-speech-dictation"></a><span data-ttu-id="21e10-152">使用連續的任意形狀的語音聽寫</span><span class="sxs-lookup"><span data-stu-id="21e10-152">Use continuous, freeform speech dictation</span></span>

<span data-ttu-id="21e10-153">請參閱 Windows 10 UWP 語音程式碼範例，針對連續聽寫案例[這裡。](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span><span class="sxs-lookup"><span data-stu-id="21e10-153">See the Windows 10 UWP speech code sample for the continuous dictation scenario [here.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span></span>

## <a name="handle-degradation-in-quality"></a><span data-ttu-id="21e10-154">降低品質，控制代碼</span><span class="sxs-lookup"><span data-stu-id="21e10-154">Handle degradation in quality</span></span>

<span data-ttu-id="21e10-155">在環境中的條件有時候可以防止語音辨識工作。</span><span class="sxs-lookup"><span data-stu-id="21e10-155">Conditions in the environment can sometimes prevent speech recognition from working.</span></span> <span data-ttu-id="21e10-156">比方說，空間可能會太吵雜，或使用者可能會說話音量太高。</span><span class="sxs-lookup"><span data-stu-id="21e10-156">For example, the room might be too noisy or the user might speak at too high a volume.</span></span> <span data-ttu-id="21e10-157">語音辨識 API 會提供資訊，可能的話，品質造成效能降低的情況。</span><span class="sxs-lookup"><span data-stu-id="21e10-157">The speech recognition API provides info, where possible, about conditions that have caused a degradation in quality.</span></span>

<span data-ttu-id="21e10-158">這項資訊會推送至您的應用程式使用 WinRT 事件。</span><span class="sxs-lookup"><span data-stu-id="21e10-158">This information is pushed to your app using a WinRT event.</span></span> <span data-ttu-id="21e10-159">以下是如何訂閱此事件的範例。</span><span class="sxs-lookup"><span data-stu-id="21e10-159">Here is an example of how to subscribe to this event.</span></span>

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

<span data-ttu-id="21e10-160">在程式碼範例中，我們選擇的條件資訊寫入偵錯主控台。</span><span class="sxs-lookup"><span data-stu-id="21e10-160">In our code sample, we choose to write the conditions info to the debug console.</span></span> <span data-ttu-id="21e10-161">應用程式可能會想要提供意見反應，使用者可透過 UI、 語音合成，並依此類推，或者它可能需要有不同的行為語音時中斷的暫時降低品質。</span><span class="sxs-lookup"><span data-stu-id="21e10-161">An app might want to provide feedback to the user via UI, speech synthesis, and so on, or it might need to behave differently when speech is interrupted by a temporary reduction in quality.</span></span>

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

<span data-ttu-id="21e10-162">如果您不使用 ref 類別建立您的 DirectX 應用程式，您必須取消訂閱事件之前釋放或重新建立您的語音辨識器。</span><span class="sxs-lookup"><span data-stu-id="21e10-162">If you are not using ref classes to create your DirectX app, you must unsubscribe from the event before releasing or recreating your speech recognizer.</span></span> <span data-ttu-id="21e10-163">HolographicSpeechPromptSample 已停止辨識，並取消訂閱事件的常式就像這樣：</span><span class="sxs-lookup"><span data-stu-id="21e10-163">The HolographicSpeechPromptSample has a routine to stop recognition, and unsubscribe from events like so:</span></span>

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

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a><span data-ttu-id="21e10-164">使用語音合成，提供可發出聲音的語音提示</span><span class="sxs-lookup"><span data-stu-id="21e10-164">Use speech synthesis to provide audible voice prompts</span></span>

<span data-ttu-id="21e10-165">全像攝影版的語音範例可用於語音合成可發出聲音的指示提供給使用者。</span><span class="sxs-lookup"><span data-stu-id="21e10-165">The holographic speech samples use speech synthesis to provide audible instructions to the user.</span></span> <span data-ttu-id="21e10-166">本主題會逐步建立合成的語音的範例中，以及玩它使用 HRTF 音訊 Api 的程序。</span><span class="sxs-lookup"><span data-stu-id="21e10-166">This topic walks through the process of creating a synthesized voice sample, and playing it back using the HRTF audio APIs.</span></span>

<span data-ttu-id="21e10-167">您應該提供要求的輸入片語時，會提示您自己的語音。</span><span class="sxs-lookup"><span data-stu-id="21e10-167">You should provide your own speech prompts when requesting phrase input.</span></span> <span data-ttu-id="21e10-168">這也可以很有幫助，指出當語音命令可以讀出，針對連續辨識情節。</span><span class="sxs-lookup"><span data-stu-id="21e10-168">This can also be helpful for indicating when speech commands can be spoken, for a continuous recognition scenario.</span></span> <span data-ttu-id="21e10-169">以下是如何利用語音合成器; 的範例請注意，您也可以使用預先錄製的聲音美工圖案、 visual 的 UI 中或其他指標的功能，比方說，在提示字元不是動態的案例中。</span><span class="sxs-lookup"><span data-stu-id="21e10-169">Here is an example of how to do that with a speech synthesizer; note that you could also use a pre-recorded voice clip, a visual UI, or other indicator of what to say, for example in scenarios where the prompt is not dynamic.</span></span>

<span data-ttu-id="21e10-170">首先，建立 SpeechSynthesizer 物件：</span><span class="sxs-lookup"><span data-stu-id="21e10-170">First, create the SpeechSynthesizer object:</span></span>

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

<span data-ttu-id="21e10-171">您也必須具有要合成文字的字串：</span><span class="sxs-lookup"><span data-stu-id="21e10-171">You also need a string with the text to be synthesized:</span></span>

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

<span data-ttu-id="21e10-172">使用 SynthesizeTextToStreamAsync 以非同步方式，被合成語音。</span><span class="sxs-lookup"><span data-stu-id="21e10-172">Speech is synthesized asynchronously using SynthesizeTextToStreamAsync.</span></span> <span data-ttu-id="21e10-173">在這裡，我們開始一項非同步工作合成語音。</span><span class="sxs-lookup"><span data-stu-id="21e10-173">Here, we kick off an async task to synthesize the speech.</span></span>

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

<span data-ttu-id="21e10-174">語音合成是傳送以位元組資料流。</span><span class="sxs-lookup"><span data-stu-id="21e10-174">The speech synthesis is sent as a byte stream.</span></span> <span data-ttu-id="21e10-175">我們可以初始化使用該位元組資料流; XAudio2 語音如需我們全像攝影版的程式碼範例中，我們播放它為 HRTF 音訊效果。</span><span class="sxs-lookup"><span data-stu-id="21e10-175">We can initialize an XAudio2 voice using that byte stream; for our holographic code samples, we play it back as an HRTF audio effect.</span></span>

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

<span data-ttu-id="21e10-176">為透過語音辨識，語音合成會擲回例外狀況發生錯誤時。</span><span class="sxs-lookup"><span data-stu-id="21e10-176">As with speech recognition, speech synthesis will throw an exception if something goes wrong.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="21e10-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21e10-177">See also</span></span>
* [<span data-ttu-id="21e10-178">語音應用程式的設計</span><span class="sxs-lookup"><span data-stu-id="21e10-178">Speech app design</span></span>](https://msdn.microsoft.com/library/dn596121.aspx)
* [<span data-ttu-id="21e10-179">DirectX 中的空間音效</span><span class="sxs-lookup"><span data-stu-id="21e10-179">Spatial sound in DirectX</span></span>](spatial-sound-in-directx.md)
* [<span data-ttu-id="21e10-180">SpeechRecognitionAndSynthesis 範例</span><span class="sxs-lookup"><span data-stu-id="21e10-180">SpeechRecognitionAndSynthesis sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
