---
title: 語音輸入
description: 語音輸入是 HoloLens 與 Windows Mixed Reality 沈浸式耳機的核心輸入。 語音可以用於命令、 聽寫、 Cortana 和更多功能。
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: ggv、 語音、 cortana、 語音、 輸入
ms.openlocfilehash: e21310b940e4a4c3019f61edea695b452e74ab62
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829955"
---
# <a name="voice-input"></a><span data-ttu-id="72ef9-105">語音輸入</span><span class="sxs-lookup"><span data-stu-id="72ef9-105">Voice input</span></span>

<span data-ttu-id="72ef9-106">語音是三個索引鍵形式的輸入上的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="72ef9-106">Voice is one of the three key forms of input on HoloLens.</span></span> <span data-ttu-id="72ef9-107">它可讓您直接命令而不需要使用的 雷射[筆勢](gestures.md)。</span><span class="sxs-lookup"><span data-stu-id="72ef9-107">It allows you to directly command a hologram without having to use [gestures](gestures.md).</span></span> <span data-ttu-id="72ef9-108">您只要[視線](gaze.md)在全像並將您的命令。</span><span class="sxs-lookup"><span data-stu-id="72ef9-108">You simply [gaze](gaze.md) at a hologram and speak your command.</span></span> <span data-ttu-id="72ef9-109">語音輸入可以是以自然的方式，向您的意圖。</span><span class="sxs-lookup"><span data-stu-id="72ef9-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="72ef9-110">語音很特別適合周遊複雜的介面，因為它可讓使用者透過巢狀以一個命令的功能表剪下。</span><span class="sxs-lookup"><span data-stu-id="72ef9-110">Voice is especially good at traversing complex interfaces because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="72ef9-111">語音輸入由[相同的引擎](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx)語音支援在所有其他通用 Windows 應用程式。</span><span class="sxs-lookup"><span data-stu-id="72ef9-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all other Universal Windows Apps.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/eHMkOpNUtR8]

## <a name="device-support"></a><span data-ttu-id="72ef9-112">裝置支援</span><span class="sxs-lookup"><span data-stu-id="72ef9-112">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="72ef9-113"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="72ef9-113"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="72ef9-114"><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="72ef9-114"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="72ef9-115"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="72ef9-115"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="72ef9-116"><a href="immersive-headset-hardware-details.md"><strong>沈浸式耳機</strong></a></span><span class="sxs-lookup"><span data-stu-id="72ef9-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="72ef9-117">語音輸入</span><span class="sxs-lookup"><span data-stu-id="72ef9-117">Voice input</span></span></td>
        <td><span data-ttu-id="72ef9-118">✔️</span><span class="sxs-lookup"><span data-stu-id="72ef9-118">✔️</span></span></td>
        <td><span data-ttu-id="72ef9-119">✔️</span><span class="sxs-lookup"><span data-stu-id="72ef9-119">✔️</span></span></td>
        <td><span data-ttu-id="72ef9-120">✔️ （與麥克風）</span><span class="sxs-lookup"><span data-stu-id="72ef9-120">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="72ef9-121">「 Select 」 命令</span><span class="sxs-lookup"><span data-stu-id="72ef9-121">The "select" command</span></span>

<span data-ttu-id="72ef9-122">即使沒有特別將語音支援新增至您的應用程式中，您的使用者可以啟用全像投影，只要說 「 選取 」。</span><span class="sxs-lookup"><span data-stu-id="72ef9-122">Even without specifically adding voice support to your app, your users can activate holograms simply by saying "select".</span></span> <span data-ttu-id="72ef9-123">此行為與相同[空中點選](gestures.md#air-tap)HoloLens，在按下 [選取] 按鈕上[HoloLens clicker](hardware-accessories.md#hololens-clicker)，或按下上的觸發程序[Windows Mixed Reality 動作控制器](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="72ef9-123">This behaves the same as an [air tap](gestures.md#air-tap) on HoloLens, pressing the select button on the [HoloLens clicker](hardware-accessories.md#hololens-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="72ef9-124">您會聽到聲音，請參閱 「 select 」 與工具提示會顯示為確認。</span><span class="sxs-lookup"><span data-stu-id="72ef9-124">You will hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="72ef9-125">因此永遠都是可供您肯定地說隨時具有最小電池壽命的影響，即使在您這端雙手 「 選取 」 會啟用低電源關鍵字偵測演算法。</span><span class="sxs-lookup"><span data-stu-id="72ef9-125">"Select" is enabled by a low power keyword detection algorithm so it is always available for you to say at any time with minimal battery life impact, even with your hands at your side.</span></span>

> [!NOTE]
> <span data-ttu-id="72ef9-126">HoloLens 2 的特定的詳細指引[即將推出](index.md#news-and-notes)。</span><span class="sxs-lookup"><span data-stu-id="72ef9-126">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

<span data-ttu-id="72ef9-127">![輸入 「 select 」 用於選取的語音命令](images/kma-voice-select-00170-800px.png)</span><span class="sxs-lookup"><span data-stu-id="72ef9-127">![Say "select" to use the voice command for selection](images/kma-voice-select-00170-800px.png)</span></span><br>
<span data-ttu-id="72ef9-128">*輸入 「 select 」 用於選取的語音命令*</span><span class="sxs-lookup"><span data-stu-id="72ef9-128">*Say "select" to use the voice command for selection*</span></span>

## <a name="hey-cortana"></a><span data-ttu-id="72ef9-129">嗨 Cortana</span><span class="sxs-lookup"><span data-stu-id="72ef9-129">Hey Cortana</span></span>

<span data-ttu-id="72ef9-130">您也可以說 「 嘿 Cortana 」，以隨時顯示 Cortana。</span><span class="sxs-lookup"><span data-stu-id="72ef9-130">You can also say "Hey Cortana" to bring up Cortana at anytime.</span></span> <span data-ttu-id="72ef9-131">您不必等待她出現繼續要求您的問題，或讓她指令-例如，嘗試說: 「 嘿 Cortana 什麼是天氣？ 」</span><span class="sxs-lookup"><span data-stu-id="72ef9-131">You don't have to wait for her to appear to continue asking her your question or giving her an instruction - for example, try saying "Hey Cortana what's the weather?"</span></span> <span data-ttu-id="72ef9-132">為單一的句子。</span><span class="sxs-lookup"><span data-stu-id="72ef9-132">as a single sentence.</span></span> <span data-ttu-id="72ef9-133">如需 Cortana 和用途的詳細資訊，只要問她 ！</span><span class="sxs-lookup"><span data-stu-id="72ef9-133">For more information about Cortana and what you can do, simply ask her!</span></span> <span data-ttu-id="72ef9-134">說出 「 嘿 Cortana 如何我嗎？ 」</span><span class="sxs-lookup"><span data-stu-id="72ef9-134">Say "Hey Cortana what can I say?"</span></span> <span data-ttu-id="72ef9-135">她會提取的工作及建議的命令清單。</span><span class="sxs-lookup"><span data-stu-id="72ef9-135">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="72ef9-136">如果您已經在 Cortana 應用程式中您也可以按一下**嗎？**</span><span class="sxs-lookup"><span data-stu-id="72ef9-136">If you're already in the Cortana app you can also click the **?**</span></span> <span data-ttu-id="72ef9-137">在資訊看板，調出這個相同的功能表上的圖示。</span><span class="sxs-lookup"><span data-stu-id="72ef9-137">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="72ef9-138">**HoloLens 特有的命令**</span><span class="sxs-lookup"><span data-stu-id="72ef9-138">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="72ef9-139">「我可以說什麼？」</span><span class="sxs-lookup"><span data-stu-id="72ef9-139">"What can I say?"</span></span>
* <span data-ttu-id="72ef9-140">「 移首頁 」 或 「 移至 開始 「-而不是[bloom](gestures.md#bloom)以前往[[開始] 功能表](navigating-the-windows-mixed-reality-home.md#start-menu)</span><span class="sxs-lookup"><span data-stu-id="72ef9-140">"Go home" or "Go to Start" - instead of [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="72ef9-141">「 啟動<app>"</span><span class="sxs-lookup"><span data-stu-id="72ef9-141">"Launch <app>"</span></span>
* <span data-ttu-id="72ef9-142">「 移動<app>這裡 」</span><span class="sxs-lookup"><span data-stu-id="72ef9-142">"Move <app> here"</span></span>
* <span data-ttu-id="72ef9-143">「 拍照"</span><span class="sxs-lookup"><span data-stu-id="72ef9-143">"Take a picture"</span></span>
* <span data-ttu-id="72ef9-144">[開始錄製]</span><span class="sxs-lookup"><span data-stu-id="72ef9-144">"Start recording"</span></span>
* <span data-ttu-id="72ef9-145">[停止錄製]</span><span class="sxs-lookup"><span data-stu-id="72ef9-145">"Stop recording"</span></span>
* <span data-ttu-id="72ef9-146">"Increase 亮度"</span><span class="sxs-lookup"><span data-stu-id="72ef9-146">"Increase the brightness"</span></span>
* <span data-ttu-id="72ef9-147">"Decrease 亮度"</span><span class="sxs-lookup"><span data-stu-id="72ef9-147">"Decrease the brightness"</span></span>
* <span data-ttu-id="72ef9-148">"Increase 磁碟區 」</span><span class="sxs-lookup"><span data-stu-id="72ef9-148">"Increase the volume"</span></span>
* <span data-ttu-id="72ef9-149">"Decrease 磁碟區 」</span><span class="sxs-lookup"><span data-stu-id="72ef9-149">"Decrease the volume"</span></span>
* <span data-ttu-id="72ef9-150">「 靜音 」 或者 「 取消靜音 」</span><span class="sxs-lookup"><span data-stu-id="72ef9-150">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="72ef9-151">「 關閉裝置 」</span><span class="sxs-lookup"><span data-stu-id="72ef9-151">"Shut down the device"</span></span>
* <span data-ttu-id="72ef9-152">[重新啟動裝置]</span><span class="sxs-lookup"><span data-stu-id="72ef9-152">"Restart the device"</span></span>
* <span data-ttu-id="72ef9-153">[執行進入睡眠狀態]</span><span class="sxs-lookup"><span data-stu-id="72ef9-153">"Go to sleep"</span></span>
* <span data-ttu-id="72ef9-154">「 什麼時候是什麼？ 」</span><span class="sxs-lookup"><span data-stu-id="72ef9-154">"What time is it?"</span></span>
* <span data-ttu-id="72ef9-155">「 還剩多少電池？ 」</span><span class="sxs-lookup"><span data-stu-id="72ef9-155">"How much battery do I have left?"</span></span>
* <span data-ttu-id="72ef9-156">「 呼叫<contact>」 （需要 Skype 的 HoloLens）</span><span class="sxs-lookup"><span data-stu-id="72ef9-156">"Call <contact>" (requires Skype for HoloLens)</span></span>

## <a name="see-it-say-it"></a><span data-ttu-id="72ef9-157">"看到它，它說出"</span><span class="sxs-lookup"><span data-stu-id="72ef9-157">"See It, Say It"</span></span>

<span data-ttu-id="72ef9-158">HoloLens 具有"看到它，它說出"的模型，如語音輸入，其中上按鈕的標籤會告知使用者他們也可以說出哪些語音命令。</span><span class="sxs-lookup"><span data-stu-id="72ef9-158">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="72ef9-159">比方說，2D 應用程式時，使用者就可以說 「 調整 」 命令，這個命令會在他們會看到應用程式列中調整應用程式的世界中的位置。</span><span class="sxs-lookup"><span data-stu-id="72ef9-159">For example, when looking at a 2D app, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.</span></span>

![使用者在 2D 應用程式或全像檢視，可以說他們看到的應用程式列中調整應用程式的位置，世界中的 「 調整 」 命令](images/microphone-600px.png)

<span data-ttu-id="72ef9-161">當應用程式遵循這項規則時，使用者可以輕鬆地了解要說來控制系統的內容。</span><span class="sxs-lookup"><span data-stu-id="72ef9-161">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="72ef9-162">為了強化，同時 gazing 按鈕時，您會看到 「 語音詳述 「 工具提示，如果按鈕是語音功能，而且會顯示 「 按 」 它與交談的命令，會出現在一秒後。</span><span class="sxs-lookup"><span data-stu-id="72ef9-162">To reinforce this, while gazing at a button, you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span>

<span data-ttu-id="72ef9-163">![看到它，例如其命令會出現下方的按鈕](images/voice-seeitsayit-600px.png)</span><span class="sxs-lookup"><span data-stu-id="72ef9-163">![See it, say it commands appear below the buttons](images/voice-seeitsayit-600px.png)</span></span><br>
<span data-ttu-id="72ef9-164">*「 請查看它說它的項目 」 命令會出現下方的按鈕*</span><span class="sxs-lookup"><span data-stu-id="72ef9-164">*"See it, say it" commands appear below the buttons*</span></span>

## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="72ef9-165">快速的全像操作的語音命令</span><span class="sxs-lookup"><span data-stu-id="72ef9-165">Voice commands for fast Hologram Manipulation</span></span>

<span data-ttu-id="72ef9-166">另外還有幾個的語音命令可以說出時 gazing 在全像圖，快速地進行操作工作。</span><span class="sxs-lookup"><span data-stu-id="72ef9-166">There are also a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks.</span></span> <span data-ttu-id="72ef9-167">這些語音命令處理 2D 應用程式，以及您已置於世界的 3D 物件。</span><span class="sxs-lookup"><span data-stu-id="72ef9-167">These voice commands work on 2D apps as well as 3D objects you have placed in the world.</span></span>

<span data-ttu-id="72ef9-168">**全像操作命令**</span><span class="sxs-lookup"><span data-stu-id="72ef9-168">**Hologram Manipulation Commands**</span></span>
* <span data-ttu-id="72ef9-169">面臨我</span><span class="sxs-lookup"><span data-stu-id="72ef9-169">Face me</span></span>
* <span data-ttu-id="72ef9-170">較大 |增強</span><span class="sxs-lookup"><span data-stu-id="72ef9-170">Bigger | Enhance</span></span>
* <span data-ttu-id="72ef9-171">較小</span><span class="sxs-lookup"><span data-stu-id="72ef9-171">Smaller</span></span>

## <a name="dictation"></a><span data-ttu-id="72ef9-172">聽寫</span><span class="sxs-lookup"><span data-stu-id="72ef9-172">Dictation</span></span>

<span data-ttu-id="72ef9-173">而不是型別與[空中點選](gestures.md#air-tap)，語音表示可能會將文字輸入至應用程式更有效率。</span><span class="sxs-lookup"><span data-stu-id="72ef9-173">Rather than typing with [air taps](gestures.md#air-tap), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="72ef9-174">這可以大幅加速使用者更不費力的輸入。</span><span class="sxs-lookup"><span data-stu-id="72ef9-174">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="72ef9-175">![語音表示一開始會選取 [麥克風] 按鈕](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="72ef9-175">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="72ef9-176">*語音表示一開始會選取鍵盤上的 [麥克風] 按鈕*</span><span class="sxs-lookup"><span data-stu-id="72ef9-176">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="72ef9-177">每當全像攝影版的鍵盤時作用中，您可以切換到聽寫模式，而不是輸入。</span><span class="sxs-lookup"><span data-stu-id="72ef9-177">Any time the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="72ef9-178">選取旁邊的文字輸入方塊，若要開始麥克風。</span><span class="sxs-lookup"><span data-stu-id="72ef9-178">Select the microphone on the side of the text input box to get started.</span></span>

## <a name="communication"></a><span data-ttu-id="72ef9-179">通訊</span><span class="sxs-lookup"><span data-stu-id="72ef9-179">Communication</span></span>

<span data-ttu-id="72ef9-180">應用程式想要利用自訂的音訊輸入處理 HoloLens 所提供的選項，請務必了解各種[音訊資料流類別](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx)可取用您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="72ef9-180">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it is important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="72ef9-181">若要啟用自訂的處理最佳化量身打造的語音、 通訊以及其他可用環境的環境音訊的麥克風音訊品質，所使用的三個 Windows 10 支援數個不同的資料流的類別和 HoloLens 讓擷取 （也就是 「 攝錄影機"） 的案例。</span><span class="sxs-lookup"><span data-stu-id="72ef9-181">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication and other which can be used for ambient environment audio capture (i.e. "camcorder") scenarios.</span></span>
* <span data-ttu-id="72ef9-182">AudioCategory_Communications 資料流類別自訂的通話品質和旁白的案例，並為用戶端提供使用者的語音 16 kHz 24 位元單聲道音訊資料流</span><span class="sxs-lookup"><span data-stu-id="72ef9-182">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16kHz 24bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="72ef9-183">AudioCategory_Speech 資料流類別自訂的 HoloLens (Windows) 的語音引擎，並提供使用者的語音 16 kHz 24 位元 mono 資料流。</span><span class="sxs-lookup"><span data-stu-id="72ef9-183">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16kHz 24bit mono stream of the user's voice.</span></span> <span data-ttu-id="72ef9-184">可以由第 3 個合作對象語音引擎使用這個類別，如有需要。</span><span class="sxs-lookup"><span data-stu-id="72ef9-184">This category can be used by 3rd party speech engines if needed.</span></span>
* <span data-ttu-id="72ef9-185">AudioCategory_Other 資料流類別自訂的環境的環境音訊錄製，並提供 48 kHz 24 位元是立體聲音訊資料流中的用戶端。</span><span class="sxs-lookup"><span data-stu-id="72ef9-185">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48kHz 24 bit stereo audio stream.</span></span>

<span data-ttu-id="72ef9-186">所有此音訊處理將會啟用硬體加速表示功能清空少很多比如果相同的處理已完成 HoloLens CPU 上的電源。</span><span class="sxs-lookup"><span data-stu-id="72ef9-186">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="72ef9-187">避免執行其他處理延長系統電池壽命，並利用內建在 CPU 上的音訊輸入中，卸載音訊的輸入的處理。</span><span class="sxs-lookup"><span data-stu-id="72ef9-187">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built in, offloaded audio input processing.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="72ef9-188">疑難排解</span><span class="sxs-lookup"><span data-stu-id="72ef9-188">Troubleshooting</span></span>

<span data-ttu-id="72ef9-189">如果您遇到任何問題，使用 「 選取 」 和 「 嘿 Cortana 」，請嘗試將移至更安靜的空間，並開啟遠離干擾，或透過說話大聲點的來源。</span><span class="sxs-lookup"><span data-stu-id="72ef9-189">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="72ef9-190">在此階段中，是調整 HoloLens 上所有的語音辨識，並將其最佳化是專為母語的英文 （美國） 中。</span><span class="sxs-lookup"><span data-stu-id="72ef9-190">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="72ef9-191">Windows Mixed Reality Developer Edition 版本 2017年中，音訊的端點管理邏輯將會正常運作 （永遠） 之後登入並回復在電腦桌面上初始 HMD 連接之後。</span><span class="sxs-lookup"><span data-stu-id="72ef9-191">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="72ef9-192">之前 out/上課 WMR OOBE 後的事件中的第一次登，使用者可能會遇到各種舉凡根據系統的設定方式的第一次連接 HMD 之前切換不含音訊不含音訊的音訊功能問題。</span><span class="sxs-lookup"><span data-stu-id="72ef9-192">Prior to that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up prior to connecting the HMD for the first time.</span></span>

## <a name="see-also"></a><span data-ttu-id="72ef9-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72ef9-193">See also</span></span>
* [<span data-ttu-id="72ef9-194">DirectX 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="72ef9-194">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="72ef9-195">Unity 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="72ef9-195">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="72ef9-196">MR Input 212：語音</span><span class="sxs-lookup"><span data-stu-id="72ef9-196">MR Input 212: Voice</span></span>](holograms-212.md)
