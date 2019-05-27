---
title: 語音命令
description: 凝視、 手勢及語音 (GGV) 是在 HoloLens 互動的主要方法。 這篇文章提供語音設計縝密的指導方針。
author: shentan
ms.author: shentan
ms.date: 04/21/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality，設計、 互動、 語音
ms.openlocfilehash: 084c1228d17c3e23b38d9b8918c13080598aea98
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039184"
---
# <a name="voice-commanding"></a><span data-ttu-id="c314a-105">語音命令</span><span class="sxs-lookup"><span data-stu-id="c314a-105">Voice commanding</span></span>

<span data-ttu-id="c314a-106">使用語音命令時，視線通常做為目標的 mechaninism，是否為指標 (「 select 」) 或指示您的應用程式的命令 （"看到它，它說出"）。</span><span class="sxs-lookup"><span data-stu-id="c314a-106">When using voice commands, gaze is typically used as the targeting mechaninism, whether as a pointer ("select") or to direct your command to an application ("see it, say it").</span></span> <span data-ttu-id="c314a-107">當然，有些語音命令不需要為目標，例如 「 移至啟動 」 或 「 嗨，Cortana。 」</span><span class="sxs-lookup"><span data-stu-id="c314a-107">Of course, some voice commands don't require a target at all, like "go to start" or "Hey, Cortana."</span></span>


## <a name="device-support"></a><span data-ttu-id="c314a-108">裝置支援</span><span class="sxs-lookup"><span data-stu-id="c314a-108">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c314a-109">功能</span><span class="sxs-lookup"><span data-stu-id="c314a-109">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="c314a-110"><a href="hololens-hardware-details.md">HoloLens （第 1 代）</a></span><span class="sxs-lookup"><span data-stu-id="c314a-110"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="c314a-111">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c314a-111">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="c314a-112"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="c314a-112"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td></td><td style="text-align: center;"> <span data-ttu-id="c314a-113">✔️</span><span class="sxs-lookup"><span data-stu-id="c314a-113">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="c314a-114">✔️</span><span class="sxs-lookup"><span data-stu-id="c314a-114">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="c314a-115">✔️ （具有附加的耳機）</span><span class="sxs-lookup"><span data-stu-id="c314a-115">✔️ (with headset attached)</span></span></td>
</tr>
</table>



## <a name="how-to-use-voice"></a><span data-ttu-id="c314a-116">如何使用語音</span><span class="sxs-lookup"><span data-stu-id="c314a-116">How to use voice</span></span>

<span data-ttu-id="c314a-117">請考慮將語音命令加入至任何您所建置的經驗。</span><span class="sxs-lookup"><span data-stu-id="c314a-117">Consider adding voice commands to any experience that you build.</span></span> <span data-ttu-id="c314a-118">語音是功能強大又方便的方式控制系統和應用程式。</span><span class="sxs-lookup"><span data-stu-id="c314a-118">Voice is a powerful and convenient way control the system and apps.</span></span> <span data-ttu-id="c314a-119">因為使用者使用各種方言和重音符號，語音關鍵字的適當的選項將可確保您的使用者命令會明確地解譯。</span><span class="sxs-lookup"><span data-stu-id="c314a-119">Because users speak with a variety of dialects and accents, proper choice of speech keywords will make sure that your users' commands are interpreted unambiguously.</span></span>

### <a name="best-practices"></a><span data-ttu-id="c314a-120">最佳作法</span><span class="sxs-lookup"><span data-stu-id="c314a-120">Best practices</span></span>

<span data-ttu-id="c314a-121">以下是將有助於順利的語音辨識中的一些做法。</span><span class="sxs-lookup"><span data-stu-id="c314a-121">Below are some practices that will aid in smooth speech recognition.</span></span>
* <span data-ttu-id="c314a-122">**使用精簡命令**-可能的話，請選擇兩個或多個音節的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c314a-122">**Use concise commands** - When possible, choose keywords of two or more syllables.</span></span> <span data-ttu-id="c314a-123">一個音節字通常會使用不同的元音時說出不同的腔調字的人員。</span><span class="sxs-lookup"><span data-stu-id="c314a-123">One-syllable words tend to use different vowel sounds when spoken by persons of different accents.</span></span> <span data-ttu-id="c314a-124">範例：「 播放視訊 」 是優於 「 遊戲的目前選取的視訊 」</span><span class="sxs-lookup"><span data-stu-id="c314a-124">Example: "Play video" is better than "Play the currently selected video"</span></span>
* <span data-ttu-id="c314a-125">**使用簡單的字彙記憶**-範例：「 顯示附註 」 是優於"Show 牌子"</span><span class="sxs-lookup"><span data-stu-id="c314a-125">**Use simple vocabulary** - Example: "Show note" is better than "Show placard"</span></span>
* <span data-ttu-id="c314a-126">**請確定命令是非破壞性**-請確定非破壞性的語音命令可以採取任何動作，並可以輕鬆地復原以免不小心談到接近使用者的另一個人會觸發命令。</span><span class="sxs-lookup"><span data-stu-id="c314a-126">**Make sure commands are non destructive** - Make sure any action that can be taken by a speech command is non destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.</span></span>
* <span data-ttu-id="c314a-127">**避免類似發音命令**-避免註冊多個語音命令，聽起來非常類似。</span><span class="sxs-lookup"><span data-stu-id="c314a-127">**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound very similar.</span></span> <span data-ttu-id="c314a-128">範例：顯示更多 」 和 「 顯示存放區 」 可以是非常類似的發音。</span><span class="sxs-lookup"><span data-stu-id="c314a-128">Example: "Show more" and "Show store" can be very similar sounding.</span></span>
* <span data-ttu-id="c314a-129">**取消註冊您的應用程式，當未使用**-當您的應用程式不是處於特定的語音命令是否有效，請考慮它取消登錄，讓其他命令不會混淆那。</span><span class="sxs-lookup"><span data-stu-id="c314a-129">**Unregister your app when not it use** - When your app is not in a state in which a particular speech command is valid, consider unregistering it so that other commands are not confused for that one.</span></span>
* <span data-ttu-id="c314a-130">**測試具有不同的重音符號**-使用不同的重音符號的使用者測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="c314a-130">**Test with different accents** - Test your app with users of different accents.</span></span>
* <span data-ttu-id="c314a-131">**維護語音命令一致性**-如果 「 返回 」 移至前一個頁面中，維護您的應用程式中的這個行為。</span><span class="sxs-lookup"><span data-stu-id="c314a-131">**Maintain voice command consistency** - If "Go back" goes to the previous page, maintain this behavior in your applications.</span></span>
* <span data-ttu-id="c314a-132">**請避免使用系統命令**-系統保留下列的語音命令。</span><span class="sxs-lookup"><span data-stu-id="c314a-132">**Avoid using system commands** - The following voice commands are reserved for the system.</span></span> <span data-ttu-id="c314a-133">這些不應由應用程式。</span><span class="sxs-lookup"><span data-stu-id="c314a-133">These should not be used by applications.</span></span>
   * <span data-ttu-id="c314a-134">「 嘿 Cortana 」</span><span class="sxs-lookup"><span data-stu-id="c314a-134">"Hey Cortana"</span></span>
   * <span data-ttu-id="c314a-135">[選取]</span><span class="sxs-lookup"><span data-stu-id="c314a-135">"Select"</span></span>

### <a name="select"></a><span data-ttu-id="c314a-136">[選取]</span><span class="sxs-lookup"><span data-stu-id="c314a-136">"Select"</span></span>

<span data-ttu-id="c314a-137">指出在任何時間的 [選取]，將會啟用任何視線資料指標指向。</span><span class="sxs-lookup"><span data-stu-id="c314a-137">Saying "select" at any time will activate whatever the gaze cursor is pointing at.</span></span> 

><span data-ttu-id="c314a-138">注意:HoloLens 2 視線資料指標需求，要先叫用說出單字"select"。</span><span class="sxs-lookup"><span data-stu-id="c314a-138">Note: In HoloLens 2, the gaze cursor needs to first be invoked by saying the word "select".</span></span> <span data-ttu-id="c314a-139">說: 「 選取 」 再次啟用。</span><span class="sxs-lookup"><span data-stu-id="c314a-139">Say, "select" again to activate.</span></span> <span data-ttu-id="c314a-140">若要隱藏視線資料指標，只要使用雙手-airtap 或觸控物件。</span><span class="sxs-lookup"><span data-stu-id="c314a-140">To hide the gaze cursor, simply use your hands -- airtap or touch an object.</span></span> 

### <a name="see-it-say-it"></a><span data-ttu-id="c314a-141">看到它，例如它</span><span class="sxs-lookup"><span data-stu-id="c314a-141">See it, say it</span></span>

<span data-ttu-id="c314a-142">Windows Mixed Reality 採用"看到它，它說出"語音模型所在**按鈕上的標籤都相同的相關聯的語音命令**。</span><span class="sxs-lookup"><span data-stu-id="c314a-142">Windows Mixed Reality has employed a "see it, say it" voice model where **labels on buttons are identical to the associated voice commands**.</span></span> <span data-ttu-id="c314a-143">因為沒有任何 dissonance 標籤和語音命令之間，使用者可以進一步了解到控制系統。</span><span class="sxs-lookup"><span data-stu-id="c314a-143">Because there isn’t any dissonance between the label and the voice command, users can better understand what to say to control the system.</span></span> <span data-ttu-id="c314a-144">為了強化，談論 按鈕，同時 **「 語音會探討提示 」** 似乎通訊的按鈕可使用語音。</span><span class="sxs-lookup"><span data-stu-id="c314a-144">To reinforce this, while dwelling on a button, a **"voice dwell tip"** appears to communicate which buttons are voice enabled.</span></span>


![請參閱它說它範例 1](images/voice-seeitsayit1-640px.jpg)

<span data-ttu-id="c314a-146">![請參閱它說它範例 2](images/voice-seeitsayit2-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c314a-146">![See it say it example 2](images/voice-seeitsayit2-640px.jpg)</span></span><br>
<span data-ttu-id="c314a-147">*範例"看到它，它說出"*</span><span class="sxs-lookup"><span data-stu-id="c314a-147">*Examples of "see it, say it"*</span></span>

### <a name="voices-strengths"></a><span data-ttu-id="c314a-148">語音的優點</span><span class="sxs-lookup"><span data-stu-id="c314a-148">Voice's strengths</span></span>

<span data-ttu-id="c314a-149">語音輸入是自然的方式來溝通我們的意圖。</span><span class="sxs-lookup"><span data-stu-id="c314a-149">Voice input is a natural way to communicate our intents.</span></span> <span data-ttu-id="c314a-150">語音很特別適合介面**周遊**因為它可以幫助使用者剪下 （使用者可能會說 「 返回 」 同時尋找在網頁上，而不必移及叫用應用程式中的 [上一頁] 按鈕） 介面的多個步驟。</span><span class="sxs-lookup"><span data-stu-id="c314a-150">Voice is especially good at interface **traversals** because it can help users cut through multiple steps of an interface (a user might say "go back" while looking at Web page, instead of having to go up and hit the back button in the app).</span></span> <span data-ttu-id="c314a-151">此小型省時有一個功能強大**情感的影響**使用者的體驗的觀感，並提供少量即可增強。</span><span class="sxs-lookup"><span data-stu-id="c314a-151">This small time savings has a powerful **emotional effect** on user’s perception of the experience and gives them a small amount superpower.</span></span> <span data-ttu-id="c314a-152">使用語音也是方便的輸入的方法，當我們有我們完整的召集令或是**多工**。</span><span class="sxs-lookup"><span data-stu-id="c314a-152">Using voice is also a convenient input method when we have our arms full or are **multi-tasking**.</span></span> <span data-ttu-id="c314a-153">裝置相當困難，在鍵盤上鍵入**語音聽寫**可以輸入有效的替代方式。</span><span class="sxs-lookup"><span data-stu-id="c314a-153">On devices where typing on a keyboard is difficult, **voice dictation** can be an efficient alternative way to input.</span></span> <span data-ttu-id="c314a-154">最後，在某些情況下的時機**各種精確度**語音視線和筆勢的限制，可能是使用者的只有受信任輸入的方法。</span><span class="sxs-lookup"><span data-stu-id="c314a-154">Lastly, in some cases when the **range of accuracy** for gaze and gesture are limited, Voice might be a user’s only trusted method input.</span></span>

<span data-ttu-id="c314a-155">**使用語音如何受益的使用者**</span><span class="sxs-lookup"><span data-stu-id="c314a-155">**How using voice can benefit the user**</span></span>
* <span data-ttu-id="c314a-156">減少時間-它應該建立的最終目的更有效率。</span><span class="sxs-lookup"><span data-stu-id="c314a-156">Reduces time - it should make the end goal more efficient.</span></span>
* <span data-ttu-id="c314a-157">投入時間-最小化可以讓工作更流暢且不費吹灰之力。</span><span class="sxs-lookup"><span data-stu-id="c314a-157">Minimizes effort - it should make tasks more fluid and effortless.</span></span>
* <span data-ttu-id="c314a-158">降低認知負載-很直覺且易於了解，並記住。</span><span class="sxs-lookup"><span data-stu-id="c314a-158">Reduces cognitive load - it's intuitive, easy to learn, and remember.</span></span>
* <span data-ttu-id="c314a-159">它是可接受社交-它應該放入社會規範方面的行為。</span><span class="sxs-lookup"><span data-stu-id="c314a-159">It's socially acceptable - it should fit in with societal norms in terms of behavior.</span></span>
* <span data-ttu-id="c314a-160">它的常式-語音可以輕易地成為 habitual 的行為。</span><span class="sxs-lookup"><span data-stu-id="c314a-160">It's routine - voice can readily become a habitual behavior.</span></span>

### <a name="voices-weaknesses"></a><span data-ttu-id="c314a-161">語音的缺點</span><span class="sxs-lookup"><span data-stu-id="c314a-161">Voice's weaknesses</span></span>

<span data-ttu-id="c314a-162">語音也有一些缺點。</span><span class="sxs-lookup"><span data-stu-id="c314a-162">Voice also has some weaknesses.</span></span> <span data-ttu-id="c314a-163">更細緻的控制是其中一個。</span><span class="sxs-lookup"><span data-stu-id="c314a-163">Fine-grained control is one of them.</span></span> <span data-ttu-id="c314a-164">（例如使用者可能是說: 「 大聲點，「 但不能說多少。</span><span class="sxs-lookup"><span data-stu-id="c314a-164">(for example a user might say "louder," but can’t say how much.</span></span> <span data-ttu-id="c314a-165">"A little"很難加以量化。</span><span class="sxs-lookup"><span data-stu-id="c314a-165">"A little" is hard to quantify.</span></span> <span data-ttu-id="c314a-166">移動或調整加聲音的項目也是很困難 （語音不提供控制項的資料粒度）。</span><span class="sxs-lookup"><span data-stu-id="c314a-166">Moving or scaling things with voice is also difficult (voice does not offer the granularity of control).</span></span> <span data-ttu-id="c314a-167">語音也可以完美。</span><span class="sxs-lookup"><span data-stu-id="c314a-167">Voice can also be imperfect.</span></span> <span data-ttu-id="c314a-168">有時候語音系統未正確聽到命令，或無法聽到命令。</span><span class="sxs-lookup"><span data-stu-id="c314a-168">Sometimes a voice system incorrectly hears a command or fails to hear a command.</span></span> <span data-ttu-id="c314a-169">從這類錯誤復原是任何介面中的一項挑戰。</span><span class="sxs-lookup"><span data-stu-id="c314a-169">Recovering from such errors is a challenge in any interface.</span></span> <span data-ttu-id="c314a-170">最後，語音可能無法接受社交公共場合中。</span><span class="sxs-lookup"><span data-stu-id="c314a-170">Lastly, voice may not be socially acceptable in public places.</span></span> <span data-ttu-id="c314a-171">有幾個步驟，使用者無法或不應該假設。</span><span class="sxs-lookup"><span data-stu-id="c314a-171">There are some things that users can’t or shouldn’t say.</span></span> <span data-ttu-id="c314a-172">這些懸崖允許用於它是最適合的語音。</span><span class="sxs-lookup"><span data-stu-id="c314a-172">These cliffs allow speech to be used for what it is best at.</span></span>

### <a name="voice-feedback-states"></a><span data-ttu-id="c314a-173">語音意見反應狀態</span><span class="sxs-lookup"><span data-stu-id="c314a-173">Voice feedback states</span></span>

<span data-ttu-id="c314a-174">使用者語音正確套用時，了解**什麼它們可以說出並取得明確的意見反應**系統**聽過它們正確**。</span><span class="sxs-lookup"><span data-stu-id="c314a-174">When Voice is applied properly, the user understands **what they can say and get clear feedback** the system **heard them correctly**.</span></span> <span data-ttu-id="c314a-175">這些兩個訊號會讓使用者相信他們在使用語音作為主要的輸入。</span><span class="sxs-lookup"><span data-stu-id="c314a-175">These two signals make the user feel confident in using Voice as a primary input.</span></span> <span data-ttu-id="c314a-176">以下是圖表，顯示哪些會發生資料指標時辨識語音輸入和如何它傳達給使用者。</span><span class="sxs-lookup"><span data-stu-id="c314a-176">Below is a diagram showing what happens to the cursor when voice input is recognized and how it communicates that to the user.</span></span>

<span data-ttu-id="c314a-177">![資料指標的語音意見反應狀態](images/voicefeedbackstates.png)</span><span class="sxs-lookup"><span data-stu-id="c314a-177">![Voice feedback states for cursor](images/voicefeedbackstates.png)</span></span><br>
<span data-ttu-id="c314a-178">*資料指標的語音意見反應狀態*</span><span class="sxs-lookup"><span data-stu-id="c314a-178">*Voice feedback states for cursor*</span></span>

## <a name="top-things-users-should-know-about-speech-on-windows-mixed-reality"></a><span data-ttu-id="c314a-179">最上層的項目使用者應該了解 Windows Mixed reality，"speech"</span><span class="sxs-lookup"><span data-stu-id="c314a-179">Top things users should know about "speech" on Windows Mixed Reality</span></span>
* <span data-ttu-id="c314a-180">假設 **"Select"** 時目標 （您可以使用這任何地方按一下按鈕） 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c314a-180">Say **"Select"** while targeting a button (you can use this anywhere to click a button).</span></span>
* <span data-ttu-id="c314a-181">您可以說**應用程式列按鈕的標籤名稱**在採取行動的某些應用程式。</span><span class="sxs-lookup"><span data-stu-id="c314a-181">You can say the **label name of an app bar button** in some apps to take an action.</span></span> <span data-ttu-id="c314a-182">比方說，同時查看應用程式，使用者可以說的命令 「 移除 」 世界中移除的應用程式 （這將節省毋需按一下您用手時間）。</span><span class="sxs-lookup"><span data-stu-id="c314a-182">For example, while looking at an app, a user can say the command "Remove" to remove the app from the world (this saves time from having to click it with your hand).</span></span>
* <span data-ttu-id="c314a-183">您可以起始接聽招呼語的 Cortana **「 嘿 Cortana 」。**</span><span class="sxs-lookup"><span data-stu-id="c314a-183">You can initiate Cortana listening by saying **"Hey Cortana."**</span></span> <span data-ttu-id="c314a-184">您可以詢問她問題 (「 嘿 Cortana，如何調整成高是艾菲爾鐵塔 」)，告訴她開啟應用程式 (「 嘿 Cortana，開啟 Netflix 」)，或只能告訴她啟動 (「 嘿 Cortana，採用我首頁 」) 的 [開始] 功能表和更多功能。</span><span class="sxs-lookup"><span data-stu-id="c314a-184">You can ask her questions ("Hey Cortana, how tall is the Eiffel tower"), tell her to open an app ("Hey Cortana, open Netflix"), or tell her to bring up the Start Menu ("Hey Cortana, take me home") and more.</span></span>

## <a name="common-questions-and-concerns-users-have-about-voice"></a><span data-ttu-id="c314a-185">常見的問題和疑難使用者有語音相關</span><span class="sxs-lookup"><span data-stu-id="c314a-185">Common questions and concerns users have about voice</span></span>
* <span data-ttu-id="c314a-186">我可以說什麼？</span><span class="sxs-lookup"><span data-stu-id="c314a-186">What can I say?</span></span>
* <span data-ttu-id="c314a-187">如何知道系統沒聽錯正確？</span><span class="sxs-lookup"><span data-stu-id="c314a-187">How do I know the system heard me correctly?</span></span>
   * <span data-ttu-id="c314a-188">系統會取得我的語音命令錯誤。</span><span class="sxs-lookup"><span data-stu-id="c314a-188">The system keeps getting my voice commands wrong.</span></span>
   * <span data-ttu-id="c314a-189">我為它提供了語音命令時，它沒有反應。</span><span class="sxs-lookup"><span data-stu-id="c314a-189">It doesn’t react when I give it a voice command.</span></span>
* <span data-ttu-id="c314a-190">當我為它提供了語音命令時，它會回應錯誤的方式。</span><span class="sxs-lookup"><span data-stu-id="c314a-190">It reacts the wrong way when I give it a voice command.</span></span>
* <span data-ttu-id="c314a-191">如何以我的聲音到特定的應用程式或應用程式指令的目標？</span><span class="sxs-lookup"><span data-stu-id="c314a-191">How do I target my voice to a specific app or app command?</span></span>
* <span data-ttu-id="c314a-192">可以使用語音命令方面的全像攝影版的框架和 HoloLens 上嗎？</span><span class="sxs-lookup"><span data-stu-id="c314a-192">Can I use voice to command things out the holographic frame on HoloLens?</span></span>

## <a name="see-also"></a><span data-ttu-id="c314a-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c314a-193">See also</span></span>
* [<span data-ttu-id="c314a-194">筆勢</span><span class="sxs-lookup"><span data-stu-id="c314a-194">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="c314a-195">頭部目光和停駐</span><span class="sxs-lookup"><span data-stu-id="c314a-195">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
