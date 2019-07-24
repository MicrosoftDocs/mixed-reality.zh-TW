---
title: 語音輸入
description: 語音輸入是 HoloLens 和 Windows Mixed Reality 沉浸式耳機的核心輸入。 語音可以用於命令、聽寫、Cortana 等等。
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: ggv、語音、cortana、語音、輸入
ms.openlocfilehash: e21310b940e4a4c3019f61edea695b452e74ab62
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829955"
---
# <a name="voice-input"></a><span data-ttu-id="84552-105">語音輸入</span><span class="sxs-lookup"><span data-stu-id="84552-105">Voice input</span></span>

<span data-ttu-id="84552-106">Voice 是 HoloLens 輸入的三種主要形式之一。</span><span class="sxs-lookup"><span data-stu-id="84552-106">Voice is one of the three key forms of input on HoloLens.</span></span> <span data-ttu-id="84552-107">它可讓您直接命令全息影像, 而不需要使用[手勢](gestures.md)。</span><span class="sxs-lookup"><span data-stu-id="84552-107">It allows you to directly command a hologram without having to use [gestures](gestures.md).</span></span> <span data-ttu-id="84552-108">您只需要[注視](gaze.md)一個全息的程式, 就可以說出您的命令。</span><span class="sxs-lookup"><span data-stu-id="84552-108">You simply [gaze](gaze.md) at a hologram and speak your command.</span></span> <span data-ttu-id="84552-109">語音輸入可以是傳達您意圖的自然方式。</span><span class="sxs-lookup"><span data-stu-id="84552-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="84552-110">語音在遍歷複雜介面時特別有用, 因為它可讓使用者使用一個命令剪下嵌套功能表。</span><span class="sxs-lookup"><span data-stu-id="84552-110">Voice is especially good at traversing complex interfaces because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="84552-111">語音輸入是由在所有其他通用 Windows 應用程式中支援語音的[相同引擎](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx)提供技術支援。</span><span class="sxs-lookup"><span data-stu-id="84552-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all other Universal Windows Apps.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/eHMkOpNUtR8]

## <a name="device-support"></a><span data-ttu-id="84552-112">裝置支援</span><span class="sxs-lookup"><span data-stu-id="84552-112">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="84552-113"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="84552-113"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="84552-114"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="84552-114"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="84552-115"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="84552-115"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="84552-116"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="84552-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="84552-117">語音輸入</span><span class="sxs-lookup"><span data-stu-id="84552-117">Voice input</span></span></td>
        <td><span data-ttu-id="84552-118">✔️</span><span class="sxs-lookup"><span data-stu-id="84552-118">✔️</span></span></td>
        <td><span data-ttu-id="84552-119">✔️</span><span class="sxs-lookup"><span data-stu-id="84552-119">✔️</span></span></td>
        <td><span data-ttu-id="84552-120">✔️ (使用麥克風)</span><span class="sxs-lookup"><span data-stu-id="84552-120">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="84552-121">"Select" 命令</span><span class="sxs-lookup"><span data-stu-id="84552-121">The "select" command</span></span>

<span data-ttu-id="84552-122">即使未特別將語音支援新增至您的應用程式, 您的使用者只要說出「select」, 就可以啟動全息影像。</span><span class="sxs-lookup"><span data-stu-id="84552-122">Even without specifically adding voice support to your app, your users can activate holograms simply by saying "select".</span></span> <span data-ttu-id="84552-123">其行為與 HoloLens 上的[空中](gestures.md#air-tap)按鍵、按下[hololens clicker](hardware-accessories.md#hololens-clicker)上的 [選取] 按鈕, 或在[Windows Mixed Reality 動作控制器](motion-controllers.md)上按下觸發程式一樣。</span><span class="sxs-lookup"><span data-stu-id="84552-123">This behaves the same as an [air tap](gestures.md#air-tap) on HoloLens, pressing the select button on the [HoloLens clicker](hardware-accessories.md#hololens-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="84552-124">您會聽到音效, 並看到包含 [選取] 的工具提示會顯示為 [確認]。</span><span class="sxs-lookup"><span data-stu-id="84552-124">You will hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="84552-125">「選取」是由低乘冪關鍵字偵測演算法所啟用, 因此隨時都可讓您以最少的電池壽命影響來表示, 即使您的手中也一樣。</span><span class="sxs-lookup"><span data-stu-id="84552-125">"Select" is enabled by a low power keyword detection algorithm so it is always available for you to say at any time with minimal battery life impact, even with your hands at your side.</span></span>

> [!NOTE]
> <span data-ttu-id="84552-126">[即將推出](index.md#news-and-notes)更多 HoloLens 2 特定指引。</span><span class="sxs-lookup"><span data-stu-id="84552-126">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

<span data-ttu-id="84552-127">![說「選取」以使用語音命令進行選取](images/kma-voice-select-00170-800px.png)</span><span class="sxs-lookup"><span data-stu-id="84552-127">![Say "select" to use the voice command for selection](images/kma-voice-select-00170-800px.png)</span></span><br>
<span data-ttu-id="84552-128">*說「選取」以使用語音命令進行選取*</span><span class="sxs-lookup"><span data-stu-id="84552-128">*Say "select" to use the voice command for selection*</span></span>

## <a name="hey-cortana"></a><span data-ttu-id="84552-129">嗨 Cortana</span><span class="sxs-lookup"><span data-stu-id="84552-129">Hey Cortana</span></span>

<span data-ttu-id="84552-130">您也可以說「嘿 Cortana」, 隨時帶出 Cortana。</span><span class="sxs-lookup"><span data-stu-id="84552-130">You can also say "Hey Cortana" to bring up Cortana at anytime.</span></span> <span data-ttu-id="84552-131">您不需要等待她繼續詢問您的問題或提供指示, 例如, 試著說「嘿, 我的天氣是什麼？」</span><span class="sxs-lookup"><span data-stu-id="84552-131">You don't have to wait for her to appear to continue asking her your question or giving her an instruction - for example, try saying "Hey Cortana what's the weather?"</span></span> <span data-ttu-id="84552-132">當做單一句子。</span><span class="sxs-lookup"><span data-stu-id="84552-132">as a single sentence.</span></span> <span data-ttu-id="84552-133">如需 Cortana 和您可以執行之動作的詳細資訊, 請直接詢問她!</span><span class="sxs-lookup"><span data-stu-id="84552-133">For more information about Cortana and what you can do, simply ask her!</span></span> <span data-ttu-id="84552-134">說「嘿, 我可以說什麼？」</span><span class="sxs-lookup"><span data-stu-id="84552-134">Say "Hey Cortana what can I say?"</span></span> <span data-ttu-id="84552-135">她會提取一個工作和建議的命令清單。</span><span class="sxs-lookup"><span data-stu-id="84552-135">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="84552-136">如果您已經在 Cortana 應用程式中, 也可以按一下 [ **？** ]</span><span class="sxs-lookup"><span data-stu-id="84552-136">If you're already in the Cortana app you can also click the **?**</span></span> <span data-ttu-id="84552-137">在提要欄位上拉出此相同功能表的圖示。</span><span class="sxs-lookup"><span data-stu-id="84552-137">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="84552-138">**HoloLens 特有的命令**</span><span class="sxs-lookup"><span data-stu-id="84552-138">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="84552-139">「我可以說什麼？」</span><span class="sxs-lookup"><span data-stu-id="84552-139">"What can I say?"</span></span>
* <span data-ttu-id="84552-140">"Go home" 或 "Go to Start"-而不是[bloom](gestures.md#bloom)以進入 [[開始] 功能表](navigating-the-windows-mixed-reality-home.md#start-menu)</span><span class="sxs-lookup"><span data-stu-id="84552-140">"Go home" or "Go to Start" - instead of [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="84552-141">「啟動<app>」</span><span class="sxs-lookup"><span data-stu-id="84552-141">"Launch <app>"</span></span>
* <span data-ttu-id="84552-142">「移<app>至這裡」</span><span class="sxs-lookup"><span data-stu-id="84552-142">"Move <app> here"</span></span>
* <span data-ttu-id="84552-143">「拍照」</span><span class="sxs-lookup"><span data-stu-id="84552-143">"Take a picture"</span></span>
* <span data-ttu-id="84552-144">「開始錄製」</span><span class="sxs-lookup"><span data-stu-id="84552-144">"Start recording"</span></span>
* <span data-ttu-id="84552-145">「停止錄製」</span><span class="sxs-lookup"><span data-stu-id="84552-145">"Stop recording"</span></span>
* <span data-ttu-id="84552-146">「增加亮度」</span><span class="sxs-lookup"><span data-stu-id="84552-146">"Increase the brightness"</span></span>
* <span data-ttu-id="84552-147">「降低亮度」</span><span class="sxs-lookup"><span data-stu-id="84552-147">"Decrease the brightness"</span></span>
* <span data-ttu-id="84552-148">「增加音量」</span><span class="sxs-lookup"><span data-stu-id="84552-148">"Increase the volume"</span></span>
* <span data-ttu-id="84552-149">「減少音量」</span><span class="sxs-lookup"><span data-stu-id="84552-149">"Decrease the volume"</span></span>
* <span data-ttu-id="84552-150">「靜音」或「取消靜音」</span><span class="sxs-lookup"><span data-stu-id="84552-150">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="84552-151">「關閉裝置」</span><span class="sxs-lookup"><span data-stu-id="84552-151">"Shut down the device"</span></span>
* <span data-ttu-id="84552-152">「重新開機裝置」</span><span class="sxs-lookup"><span data-stu-id="84552-152">"Restart the device"</span></span>
* <span data-ttu-id="84552-153">「進入睡眠狀態」</span><span class="sxs-lookup"><span data-stu-id="84552-153">"Go to sleep"</span></span>
* <span data-ttu-id="84552-154">「有什麼時間？」</span><span class="sxs-lookup"><span data-stu-id="84552-154">"What time is it?"</span></span>
* <span data-ttu-id="84552-155">「我剩多少電池？」</span><span class="sxs-lookup"><span data-stu-id="84552-155">"How much battery do I have left?"</span></span>
* <span data-ttu-id="84552-156">"Call <contact>" (需要 Skype for HoloLens)</span><span class="sxs-lookup"><span data-stu-id="84552-156">"Call <contact>" (requires Skype for HoloLens)</span></span>

## <a name="see-it-say-it"></a><span data-ttu-id="84552-157">「見它」</span><span class="sxs-lookup"><span data-stu-id="84552-157">"See It, Say It"</span></span>

<span data-ttu-id="84552-158">HoloLens 有「看它, 假設是語音輸入的模型」, 其中標籤的按鈕會告訴使用者他們也可以說的語音命令。</span><span class="sxs-lookup"><span data-stu-id="84552-158">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="84552-159">例如, 當查看2D 應用程式時, 使用者可以在應用程式行中說出他們看到的「調整」命令, 以調整應用程式在世界中的位置。</span><span class="sxs-lookup"><span data-stu-id="84552-159">For example, when looking at a 2D app, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.</span></span>

![查看2D 應用程式或全息影像時, 使用者可以說出他們在應用程式行中看到的「調整」命令, 以調整應用程式在世界中的位置。](images/microphone-600px.png)

<span data-ttu-id="84552-161">當應用程式遵循此規則時, 使用者可以輕鬆地瞭解如何控制系統。</span><span class="sxs-lookup"><span data-stu-id="84552-161">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="84552-162">為了強調此動作, 當您在按鈕上撥雲見日時, 您會看到一個「聲音停留」工具提示, 如果按鈕已啟用語音, 則會在一秒後出現, 並顯示要說出的命令來「按」。</span><span class="sxs-lookup"><span data-stu-id="84552-162">To reinforce this, while gazing at a button, you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span>

<span data-ttu-id="84552-163">![查看它, 假設命令出現在按鈕下方](images/voice-seeitsayit-600px.png)</span><span class="sxs-lookup"><span data-stu-id="84552-163">![See it, say it commands appear below the buttons](images/voice-seeitsayit-600px.png)</span></span><br>
<span data-ttu-id="84552-164">*「看起來」命令會出現在按鈕下方*</span><span class="sxs-lookup"><span data-stu-id="84552-164">*"See it, say it" commands appear below the buttons*</span></span>

## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="84552-165">快速全息影像操作的語音命令</span><span class="sxs-lookup"><span data-stu-id="84552-165">Voice commands for fast Hologram Manipulation</span></span>

<span data-ttu-id="84552-166">此外, 您也可以在撥雲見日的全息圖中, 使用一些語音命令來快速執行操作工作。</span><span class="sxs-lookup"><span data-stu-id="84552-166">There are also a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks.</span></span> <span data-ttu-id="84552-167">這些語音命令適用于2D 應用程式以及您放在世界中的3D 物件。</span><span class="sxs-lookup"><span data-stu-id="84552-167">These voice commands work on 2D apps as well as 3D objects you have placed in the world.</span></span>

<span data-ttu-id="84552-168">**全息影像操作命令**</span><span class="sxs-lookup"><span data-stu-id="84552-168">**Hologram Manipulation Commands**</span></span>
* <span data-ttu-id="84552-169">臉部我</span><span class="sxs-lookup"><span data-stu-id="84552-169">Face me</span></span>
* <span data-ttu-id="84552-170">較大 |增加</span><span class="sxs-lookup"><span data-stu-id="84552-170">Bigger | Enhance</span></span>
* <span data-ttu-id="84552-171">較小</span><span class="sxs-lookup"><span data-stu-id="84552-171">Smaller</span></span>

## <a name="dictation"></a><span data-ttu-id="84552-172">聽寫</span><span class="sxs-lookup"><span data-stu-id="84552-172">Dictation</span></span>

<span data-ttu-id="84552-173">語音聽寫可以更有效率地在應用程式中輸入文字, 而不是鍵入[空中](gestures.md#air-tap)。</span><span class="sxs-lookup"><span data-stu-id="84552-173">Rather than typing with [air taps](gestures.md#air-tap), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="84552-174">這可以大幅加速輸入, 讓使用者的工作更少。</span><span class="sxs-lookup"><span data-stu-id="84552-174">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="84552-175">![語音聽寫一開始會選取 [麥克風] 按鈕](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="84552-175">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="84552-176">*語音聽寫一開始會選取鍵盤上的 [麥克風] 按鈕*</span><span class="sxs-lookup"><span data-stu-id="84552-176">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="84552-177">當全像攝影鍵盤在使用中時, 您可以切換到聽寫模式, 而不是輸入。</span><span class="sxs-lookup"><span data-stu-id="84552-177">Any time the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="84552-178">選取文字輸入方塊旁邊的麥克風以開始使用。</span><span class="sxs-lookup"><span data-stu-id="84552-178">Select the microphone on the side of the text input box to get started.</span></span>

## <a name="communication"></a><span data-ttu-id="84552-179">通訊</span><span class="sxs-lookup"><span data-stu-id="84552-179">Communication</span></span>

<span data-ttu-id="84552-180">對於想要利用 HoloLens 所提供之自訂音訊輸入處理選項的應用程式, 請務必瞭解您的應用程式可以使用的各種[音訊串流類別](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx)。</span><span class="sxs-lookup"><span data-stu-id="84552-180">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it is important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="84552-181">Windows 10 支援數種不同的串流類別和 HoloLens, 利用其中三種來啟用自訂處理, 以優化專為語音、通訊及其他可用於環境音訊的麥克風音訊品質capture (亦即「攝影機」) 案例。</span><span class="sxs-lookup"><span data-stu-id="84552-181">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication and other which can be used for ambient environment audio capture (i.e. "camcorder") scenarios.</span></span>
* <span data-ttu-id="84552-182">AudioCategory_Communications 串流類別是針對呼叫品質和旁白案例自訂, 並為用戶端提供使用者語音的 Riff-16khz-16bit-mono-pcm 24bit mono 音訊串流</span><span class="sxs-lookup"><span data-stu-id="84552-182">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16kHz 24bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="84552-183">[AudioCategory_Speech stream] 類別是針對 HoloLens (Windows) 語音引擎自訂, 並提供該使用者語音的 Riff-16khz-16bit-mono-pcm 24bit mono 串流。</span><span class="sxs-lookup"><span data-stu-id="84552-183">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16kHz 24bit mono stream of the user's voice.</span></span> <span data-ttu-id="84552-184">如有需要, 可由協力廠商語音引擎使用此類別。</span><span class="sxs-lookup"><span data-stu-id="84552-184">This category can be used by 3rd party speech engines if needed.</span></span>
* <span data-ttu-id="84552-185">[AudioCategory_Other stream] 類別是針對環境環境音訊錄製而自訂, 並提供用戶端 48kHz 24 位身歷聲音訊串流。</span><span class="sxs-lookup"><span data-stu-id="84552-185">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48kHz 24 bit stereo audio stream.</span></span>

<span data-ttu-id="84552-186">所有此音訊處理都是硬體加速的, 這表示在 HoloLens CPU 上進行相同的處理時, 這些功能的耗電量會少很多。</span><span class="sxs-lookup"><span data-stu-id="84552-186">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="84552-187">避免在 CPU 上執行其他音訊輸入處理, 以將系統電池壽命最大化, 並利用內建的卸載音訊輸入處理。</span><span class="sxs-lookup"><span data-stu-id="84552-187">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built in, offloaded audio input processing.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="84552-188">疑難排解</span><span class="sxs-lookup"><span data-stu-id="84552-188">Troubleshooting</span></span>

<span data-ttu-id="84552-189">如果您在使用「選取」和「嘿 Cortana」時遇到任何問題, 請嘗試移到更好的空間、離開雜訊來源, 或說出更大的聲音。</span><span class="sxs-lookup"><span data-stu-id="84552-189">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="84552-190">目前, 所有的 HoloLens 語音辨識都是針對美國英文的原生喇叭進行微調與優化。</span><span class="sxs-lookup"><span data-stu-id="84552-190">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="84552-191">對於 Windows Mixed Reality Developer Edition 版本 2017, 在初始 HMD 連線之後, 音訊端點管理邏輯會正常執行 (永遠) 到電腦桌面。</span><span class="sxs-lookup"><span data-stu-id="84552-191">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="84552-192">在經過 WMR OOBE 之後, 第一次登出/進入事件之前, 使用者可能會遇到各種音訊功能問題, 範圍從沒有音訊到音訊切換, 這取決於第一次連線 HMD 之前設定系統的方式。</span><span class="sxs-lookup"><span data-stu-id="84552-192">Prior to that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up prior to connecting the HMD for the first time.</span></span>

## <a name="see-also"></a><span data-ttu-id="84552-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84552-193">See also</span></span>
* [<span data-ttu-id="84552-194">DirectX 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="84552-194">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="84552-195">Unity 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="84552-195">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="84552-196">MR Input 212：語音</span><span class="sxs-lookup"><span data-stu-id="84552-196">MR Input 212: Voice</span></span>](holograms-212.md)
