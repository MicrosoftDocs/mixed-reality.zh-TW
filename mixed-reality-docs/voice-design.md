---
title: 語音命令
description: 注視、手勢和語音 (GGV) 是 HoloLens 上的主要互動方法。 本文會針對語音設計提供縝密的指導方針。
author: shentan
ms.author: shentan
ms.date: 04/21/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, 設計, 互動, 語音
ms.openlocfilehash: f2362400cba2946c3e97a7128c410ddcd17b4362
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66402373"
---
# <a name="voice-commanding"></a><span data-ttu-id="d92dd-105">語音命令</span><span class="sxs-lookup"><span data-stu-id="d92dd-105">Voice commanding</span></span>

<span data-ttu-id="d92dd-106">使用語音命令時，一般會使用注視來作為鎖定機制，無論是要作為指標 (「選取」) 還是用來對應用程式指示命令 (「看到什麼就說什麼」)。</span><span class="sxs-lookup"><span data-stu-id="d92dd-106">When using voice commands, gaze is typically used as the targeting mechaninism, whether as a pointer ("select") or to direct your command to an application ("see it, say it").</span></span> <span data-ttu-id="d92dd-107">當然，有些語音命令完全不需要目標，例如「移至開始」或「嗨，Cortana」。</span><span class="sxs-lookup"><span data-stu-id="d92dd-107">Of course, some voice commands don't require a target at all, like "go to start" or "Hey, Cortana."</span></span>


## <a name="device-support"></a><span data-ttu-id="d92dd-108">裝置支援</span><span class="sxs-lookup"><span data-stu-id="d92dd-108">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="d92dd-109">功能</span><span class="sxs-lookup"><span data-stu-id="d92dd-109">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="d92dd-110"><a href="hololens-hardware-details.md">HoloLens (第 1 代)</a></span><span class="sxs-lookup"><span data-stu-id="d92dd-110"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="d92dd-111">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d92dd-111">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="d92dd-112"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></span><span class="sxs-lookup"><span data-stu-id="d92dd-112"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="d92dd-113">語音命令</span><span class="sxs-lookup"><span data-stu-id="d92dd-113">Voice commanding</span></span></td><td style="text-align: center;"> <span data-ttu-id="d92dd-114">✔️</span><span class="sxs-lookup"><span data-stu-id="d92dd-114">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="d92dd-115">✔️</span><span class="sxs-lookup"><span data-stu-id="d92dd-115">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="d92dd-116">✔️ (連結頭戴式裝置)</span><span class="sxs-lookup"><span data-stu-id="d92dd-116">✔️ (with headset attached)</span></span></td>
</tr>
</table>



## <a name="how-to-use-voice"></a><span data-ttu-id="d92dd-117">如何使用語音</span><span class="sxs-lookup"><span data-stu-id="d92dd-117">How to use voice</span></span>

<span data-ttu-id="d92dd-118">請考慮對您所建置的任何體驗新增語音命令。</span><span class="sxs-lookup"><span data-stu-id="d92dd-118">Consider adding voice commands to any experience that you build.</span></span> <span data-ttu-id="d92dd-119">語音是功能強大的方式，可方便您控制系統和應用程式。</span><span class="sxs-lookup"><span data-stu-id="d92dd-119">Voice is a powerful and convenient way control the system and apps.</span></span> <span data-ttu-id="d92dd-120">因為使用者說話時的語調和口音各異，適當選擇語音關鍵字才能確保系統會分毫不差地解讀出使用者的命令。</span><span class="sxs-lookup"><span data-stu-id="d92dd-120">Because users speak with a variety of dialects and accents, proper choice of speech keywords will make sure that your users' commands are interpreted unambiguously.</span></span>

### <a name="best-practices"></a><span data-ttu-id="d92dd-121">最佳作法</span><span class="sxs-lookup"><span data-stu-id="d92dd-121">Best practices</span></span>

<span data-ttu-id="d92dd-122">以下是有助於順利辨識語音的一些做法。</span><span class="sxs-lookup"><span data-stu-id="d92dd-122">Below are some practices that will aid in smooth speech recognition.</span></span>
* <span data-ttu-id="d92dd-123">**使用精簡的命令** - 盡可能選擇有兩個以上音節的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d92dd-123">**Use concise commands** - When possible, choose keywords of two or more syllables.</span></span> <span data-ttu-id="d92dd-124">口音不同的人在說單音節的單字時往往會使用不同的元音。</span><span class="sxs-lookup"><span data-stu-id="d92dd-124">One-syllable words tend to use different vowel sounds when spoken by persons of different accents.</span></span> <span data-ttu-id="d92dd-125">範例："Play video" 優於 "Play the currently selected video"</span><span class="sxs-lookup"><span data-stu-id="d92dd-125">Example: "Play video" is better than "Play the currently selected video"</span></span>
* <span data-ttu-id="d92dd-126">**使用簡單的字彙** - 範例："Show note" 優於 "Show placard"</span><span class="sxs-lookup"><span data-stu-id="d92dd-126">**Use simple vocabulary** - Example: "Show note" is better than "Show placard"</span></span>
* <span data-ttu-id="d92dd-127">**確定命令不具破壞性** - 確定可透過語音命令來採取的動作不具破壞性，如果使用者附近有其他人不小心觸發命令，也可以輕鬆地加以復原。</span><span class="sxs-lookup"><span data-stu-id="d92dd-127">**Make sure commands are non destructive** - Make sure any action that can be taken by a speech command is non destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.</span></span>
* <span data-ttu-id="d92dd-128">**避免類似發音的命令** - 避免註冊多個聽起來非常類似的語音命令。</span><span class="sxs-lookup"><span data-stu-id="d92dd-128">**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound very similar.</span></span> <span data-ttu-id="d92dd-129">範例："Show more" 和 "Show store" 的發音會非常類似。</span><span class="sxs-lookup"><span data-stu-id="d92dd-129">Example: "Show more" and "Show store" can be very similar sounding.</span></span>
* <span data-ttu-id="d92dd-130">**將未使用的應用程式取消註冊** - 當應用程式並非處在會讓特定語音命令生效的狀態時，請考慮將其取消註冊，以免該命令與其他命令混淆。</span><span class="sxs-lookup"><span data-stu-id="d92dd-130">**Unregister your app when not it use** - When your app is not in a state in which a particular speech command is valid, consider unregistering it so that other commands are not confused for that one.</span></span>
* <span data-ttu-id="d92dd-131">**使用不同口音進行測試** - 請使用不同口音的使用者測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="d92dd-131">**Test with different accents** - Test your app with users of different accents.</span></span>
* <span data-ttu-id="d92dd-132">**讓語音命令保持一致** - 如果 "Go back" 會回到上一頁，請在應用程式中保持這個行為。</span><span class="sxs-lookup"><span data-stu-id="d92dd-132">**Maintain voice command consistency** - If "Go back" goes to the previous page, maintain this behavior in your applications.</span></span>
* <span data-ttu-id="d92dd-133">**避免使用系統命令** - 下列語音命令已保留給系統使用。</span><span class="sxs-lookup"><span data-stu-id="d92dd-133">**Avoid using system commands** - The following voice commands are reserved for the system.</span></span> <span data-ttu-id="d92dd-134">應用程式請勿使用這些命令。</span><span class="sxs-lookup"><span data-stu-id="d92dd-134">These should not be used by applications.</span></span>
   * <span data-ttu-id="d92dd-135">"Hey Cortana"</span><span class="sxs-lookup"><span data-stu-id="d92dd-135">"Hey Cortana"</span></span>
   * <span data-ttu-id="d92dd-136">"Select"</span><span class="sxs-lookup"><span data-stu-id="d92dd-136">"Select"</span></span>

### <a name="select"></a><span data-ttu-id="d92dd-137">"Select"</span><span class="sxs-lookup"><span data-stu-id="d92dd-137">"Select"</span></span>

<span data-ttu-id="d92dd-138">在任何時候說出 "Select"，都會啟用注視游標所指的目標。</span><span class="sxs-lookup"><span data-stu-id="d92dd-138">Saying "select" at any time will activate whatever the gaze cursor is pointing at.</span></span> 

><span data-ttu-id="d92dd-139">注意：在 HoloLens 2 中，必須先說出 "Select" 一詞來叫用注視游標。</span><span class="sxs-lookup"><span data-stu-id="d92dd-139">Note: In HoloLens 2, the gaze cursor needs to first be invoked by saying the word "select".</span></span> <span data-ttu-id="d92dd-140">再次說出 "Select" 便能啟用。</span><span class="sxs-lookup"><span data-stu-id="d92dd-140">Say, "select" again to activate.</span></span> <span data-ttu-id="d92dd-141">若要隱藏注視游標，使用雙手就可以 - 空中點選或觸碰物件。</span><span class="sxs-lookup"><span data-stu-id="d92dd-141">To hide the gaze cursor, simply use your hands -- airtap or touch an object.</span></span> 

### <a name="see-it-say-it"></a><span data-ttu-id="d92dd-142">看到什麼就說什麼</span><span class="sxs-lookup"><span data-stu-id="d92dd-142">See it, say it</span></span>

<span data-ttu-id="d92dd-143">Windows Mixed Reality 採用「看到什麼就說什麼」語音模型，**按鈕上的標籤會與相關聯的語音命令完全相同**。</span><span class="sxs-lookup"><span data-stu-id="d92dd-143">Windows Mixed Reality has employed a "see it, say it" voice model where **labels on buttons are identical to the associated voice commands**.</span></span> <span data-ttu-id="d92dd-144">因為標籤和語音命令沒有任何不一致，使用者會更加了解要說什麼才能控制系統。</span><span class="sxs-lookup"><span data-stu-id="d92dd-144">Because there isn’t any dissonance between the label and the voice command, users can better understand what to say to control the system.</span></span> <span data-ttu-id="d92dd-145">為了強化這一項功能，當您停駐在某個按鈕上時，便會出現 **「語音停駐提示」** ，來讓您知道哪些按鈕有語音功能。</span><span class="sxs-lookup"><span data-stu-id="d92dd-145">To reinforce this, while dwelling on a button, a **"voice dwell tip"** appears to communicate which buttons are voice enabled.</span></span>


![看到什麼就說什麼的範例 1](images/voice-seeitsayit1-640px.jpg)

<span data-ttu-id="d92dd-147">![看到什麼就說什麼的範例 2](images/voice-seeitsayit2-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="d92dd-147">![See it say it example 2](images/voice-seeitsayit2-640px.jpg)</span></span><br>
<span data-ttu-id="d92dd-148">「看到什麼就說什麼」的範例 </span><span class="sxs-lookup"><span data-stu-id="d92dd-148">*Examples of "see it, say it"*</span></span>

### <a name="voices-strengths"></a><span data-ttu-id="d92dd-149">語音的優點</span><span class="sxs-lookup"><span data-stu-id="d92dd-149">Voice's strengths</span></span>

<span data-ttu-id="d92dd-150">語音輸入是很自然的意圖溝通方式。</span><span class="sxs-lookup"><span data-stu-id="d92dd-150">Voice input is a natural way to communicate our intents.</span></span> <span data-ttu-id="d92dd-151">語音特別適合用於介面的**周遊**，因為這種方式可以幫助使用者跳過介面的多個步驟 (使用者可以在看網頁時說 "go back"，而不必上移再點擊應用程式中的 [上一頁] 按鈕)。</span><span class="sxs-lookup"><span data-stu-id="d92dd-151">Voice is especially good at interface **traversals** because it can help users cut through multiple steps of an interface (a user might say "go back" while looking at Web page, instead of having to go up and hit the back button in the app).</span></span> <span data-ttu-id="d92dd-152">這種方式雖然只節省了一點時間，卻會對使用者感覺到的體驗產生**情感效應**，讓使用者獲得一點超能力。</span><span class="sxs-lookup"><span data-stu-id="d92dd-152">This small time savings has a powerful **emotional effect** on user’s perception of the experience and gives them a small amount superpower.</span></span> <span data-ttu-id="d92dd-153">當我們無法騰出雙手或是在執行**多工**處理時，使用語音也是很方便的輸入方法。</span><span class="sxs-lookup"><span data-stu-id="d92dd-153">Using voice is also a convenient input method when we have our arms full or are **multi-tasking**.</span></span> <span data-ttu-id="d92dd-154">在不方便使用鍵盤來輸入的裝置上，**語音聽寫**會是很有效率的替代輸入方式。</span><span class="sxs-lookup"><span data-stu-id="d92dd-154">On devices where typing on a keyboard is difficult, **voice dictation** can be an efficient alternative way to input.</span></span> <span data-ttu-id="d92dd-155">最後，在某些注視和手勢的**精確範圍**不高的情況下，使用者可能只會信任語音輸入方法。</span><span class="sxs-lookup"><span data-stu-id="d92dd-155">Lastly, in some cases when the **range of accuracy** for gaze and gesture are limited, Voice might be a user’s only trusted method input.</span></span>

<span data-ttu-id="d92dd-156">**使用語音如何讓使用者受益**</span><span class="sxs-lookup"><span data-stu-id="d92dd-156">**How using voice can benefit the user**</span></span>
* <span data-ttu-id="d92dd-157">減少時間 - 語音應該會讓最終目標更有效率。</span><span class="sxs-lookup"><span data-stu-id="d92dd-157">Reduces time - it should make the end goal more efficient.</span></span>
* <span data-ttu-id="d92dd-158">最不費力 - 語音應該會讓工作變得更為流暢且更不費力。</span><span class="sxs-lookup"><span data-stu-id="d92dd-158">Minimizes effort - it should make tasks more fluid and effortless.</span></span>
* <span data-ttu-id="d92dd-159">降低認知負荷 - 語音既直覺、易於了解且容易記住。</span><span class="sxs-lookup"><span data-stu-id="d92dd-159">Reduces cognitive load - it's intuitive, easy to learn, and remember.</span></span>
* <span data-ttu-id="d92dd-160">符合社交規範 - 語音應該會符合社會行為規範。</span><span class="sxs-lookup"><span data-stu-id="d92dd-160">It's socially acceptable - it should fit in with societal norms in terms of behavior.</span></span>
* <span data-ttu-id="d92dd-161">語音很平常 - 語音隨時可以變成慣常行為。</span><span class="sxs-lookup"><span data-stu-id="d92dd-161">It's routine - voice can readily become a habitual behavior.</span></span>

### <a name="voices-weaknesses"></a><span data-ttu-id="d92dd-162">語音的缺點</span><span class="sxs-lookup"><span data-stu-id="d92dd-162">Voice's weaknesses</span></span>

<span data-ttu-id="d92dd-163">語音也有一些缺點。</span><span class="sxs-lookup"><span data-stu-id="d92dd-163">Voice also has some weaknesses.</span></span> <span data-ttu-id="d92dd-164">缺點之一就是細微控制。</span><span class="sxs-lookup"><span data-stu-id="d92dd-164">Fine-grained control is one of them.</span></span> <span data-ttu-id="d92dd-165">(例如，使用者可能會說：「大聲點」，但不會說出大多少。</span><span class="sxs-lookup"><span data-stu-id="d92dd-165">(for example a user might say "louder," but can’t say how much.</span></span> <span data-ttu-id="d92dd-166">「一點」是不容易量化的詞。</span><span class="sxs-lookup"><span data-stu-id="d92dd-166">"A little" is hard to quantify.</span></span> <span data-ttu-id="d92dd-167">使用語音來移動或縮放物體也很困難 (語音不會提供控制項的細微性)。</span><span class="sxs-lookup"><span data-stu-id="d92dd-167">Moving or scaling things with voice is also difficult (voice does not offer the granularity of control).</span></span> <span data-ttu-id="d92dd-168">語音也有缺陷。</span><span class="sxs-lookup"><span data-stu-id="d92dd-168">Voice can also be imperfect.</span></span> <span data-ttu-id="d92dd-169">有時候，語音系統會誤判命令，或無法聽到命令。</span><span class="sxs-lookup"><span data-stu-id="d92dd-169">Sometimes a voice system incorrectly hears a command or fails to hear a command.</span></span> <span data-ttu-id="d92dd-170">不管什麼介面都很難從這類錯誤改正回來。</span><span class="sxs-lookup"><span data-stu-id="d92dd-170">Recovering from such errors is a challenge in any interface.</span></span> <span data-ttu-id="d92dd-171">最後，在公開場合中，使用者可能不方便發出聲音，</span><span class="sxs-lookup"><span data-stu-id="d92dd-171">Lastly, voice may not be socially acceptable in public places.</span></span> <span data-ttu-id="d92dd-172">或者有一些不能或不應該說的話。</span><span class="sxs-lookup"><span data-stu-id="d92dd-172">There are some things that users can’t or shouldn’t say.</span></span> <span data-ttu-id="d92dd-173">遇到這樣的困境時，語音就能發揮所長，無往不利。</span><span class="sxs-lookup"><span data-stu-id="d92dd-173">These cliffs allow speech to be used for what it is best at.</span></span>

### <a name="voice-feedback-states"></a><span data-ttu-id="d92dd-174">語音反饋狀態</span><span class="sxs-lookup"><span data-stu-id="d92dd-174">Voice feedback states</span></span>

<span data-ttu-id="d92dd-175">當語音正確套用時，使用者會了解**他們能說什麼並獲得清楚的反饋**而知道系統**正確聽懂他們的語音**。</span><span class="sxs-lookup"><span data-stu-id="d92dd-175">When Voice is applied properly, the user understands **what they can say and get clear feedback** the system **heard them correctly**.</span></span> <span data-ttu-id="d92dd-176">這兩個訊號會讓使用者有信心，確信他們可以使用語音作為主要輸入方式。</span><span class="sxs-lookup"><span data-stu-id="d92dd-176">These two signals make the user feel confident in using Voice as a primary input.</span></span> <span data-ttu-id="d92dd-177">下圖顯示的是當系統辨識到語音輸入時會有什麼情形，以及系統會如何讓使用者知道這一點。</span><span class="sxs-lookup"><span data-stu-id="d92dd-177">Below is a diagram showing what happens to the cursor when voice input is recognized and how it communicates that to the user.</span></span>

<span data-ttu-id="d92dd-178">![游標的語音反饋狀態](images/voicefeedbackstates.png)</span><span class="sxs-lookup"><span data-stu-id="d92dd-178">![Voice feedback states for cursor](images/voicefeedbackstates.png)</span></span><br>
<span data-ttu-id="d92dd-179">*游標的語音反饋狀態*</span><span class="sxs-lookup"><span data-stu-id="d92dd-179">*Voice feedback states for cursor*</span></span>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a><span data-ttu-id="d92dd-180">針對混合實境中的「語音」，使用者最應該了解的事</span><span class="sxs-lookup"><span data-stu-id="d92dd-180">Top things users should know about "speech" in mixed reality</span></span>
* <span data-ttu-id="d92dd-181">在鎖定按鈕時說出 **"Select"** (您可以在任何地方使用這個命令來按一下按鈕)。</span><span class="sxs-lookup"><span data-stu-id="d92dd-181">Say **"Select"** while targeting a button (you can use this anywhere to click a button).</span></span>
* <span data-ttu-id="d92dd-182">在某些應用程式中，您可以說出**應用程式列按鈕的標籤名稱**來採取動作。</span><span class="sxs-lookup"><span data-stu-id="d92dd-182">You can say the **label name of an app bar button** in some apps to take an action.</span></span> <span data-ttu-id="d92dd-183">例如，在查看應用程式的同時，使用者可以說出「Remove」命令來從該世界中移除應用程式 (這可省下必須用手按一下按鈕的時間)。</span><span class="sxs-lookup"><span data-stu-id="d92dd-183">For example, while looking at an app, a user can say the command "Remove" to remove the app from the world (this saves time from having to click it with your hand).</span></span>
* <span data-ttu-id="d92dd-184">您可以說 **「嗨 Cortana」** 讓 Cortana 開始聽取命令。</span><span class="sxs-lookup"><span data-stu-id="d92dd-184">You can initiate Cortana listening by saying **"Hey Cortana."**</span></span> <span data-ttu-id="d92dd-185">您可以向她問問題 (「嗨 Cortana，艾菲爾鐵塔有多高」)、請她開啟應用程式 (「嗨 Cortana，開啟 Netflix」)，或請她顯示 [開始] 功能表 (「嗨 Cortana，回到首頁」) 等等。</span><span class="sxs-lookup"><span data-stu-id="d92dd-185">You can ask her questions ("Hey Cortana, how tall is the Eiffel tower"), tell her to open an app ("Hey Cortana, open Netflix"), or tell her to bring up the Start Menu ("Hey Cortana, take me home") and more.</span></span>

## <a name="common-questions-and-concerns-users-have-about-voice"></a><span data-ttu-id="d92dd-186">使用者會有的語音相關常見問題和疑慮</span><span class="sxs-lookup"><span data-stu-id="d92dd-186">Common questions and concerns users have about voice</span></span>
* <span data-ttu-id="d92dd-187">我可以說什麼？</span><span class="sxs-lookup"><span data-stu-id="d92dd-187">What can I say?</span></span>
* <span data-ttu-id="d92dd-188">如何知道系統沒有聽錯？</span><span class="sxs-lookup"><span data-stu-id="d92dd-188">How do I know the system heard me correctly?</span></span>
   * <span data-ttu-id="d92dd-189">系統一直聽錯我的語音命令。</span><span class="sxs-lookup"><span data-stu-id="d92dd-189">The system keeps getting my voice commands wrong.</span></span>
   * <span data-ttu-id="d92dd-190">我提供了語音命令，系統卻沒有反應。</span><span class="sxs-lookup"><span data-stu-id="d92dd-190">It doesn’t react when I give it a voice command.</span></span>
* <span data-ttu-id="d92dd-191">我提供了語音命令，系統卻做出錯誤反應。</span><span class="sxs-lookup"><span data-stu-id="d92dd-191">It reacts the wrong way when I give it a voice command.</span></span>
* <span data-ttu-id="d92dd-192">如何讓我的語音以特定應用程式或應用程式命令作為目標？</span><span class="sxs-lookup"><span data-stu-id="d92dd-192">How do I target my voice to a specific app or app command?</span></span>
* <span data-ttu-id="d92dd-193">在 HoloLens 上的全像攝影畫面外，是否可以使用語音來命令物件？</span><span class="sxs-lookup"><span data-stu-id="d92dd-193">Can I use voice to command things out the holographic frame on HoloLens?</span></span>

## <a name="see-also"></a><span data-ttu-id="d92dd-194">請參閱</span><span class="sxs-lookup"><span data-stu-id="d92dd-194">See also</span></span>
* [<span data-ttu-id="d92dd-195">筆勢</span><span class="sxs-lookup"><span data-stu-id="d92dd-195">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="d92dd-196">頭部目光和停駐</span><span class="sxs-lookup"><span data-stu-id="d92dd-196">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
