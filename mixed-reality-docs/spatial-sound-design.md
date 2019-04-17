---
title: 空間完善的設計
description: 空間的聲音是訓練活動，協助工具，在混合的實境應用程式的 UX 設計的強大工具。
author: joekellyms
ms.author: joekelly
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，空間的音效、 設計、 樣式
ms.openlocfilehash: c8f5268faf5eef779401c046947c3137d177cb89
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591140"
---
# <a name="spatial-sound-design"></a><span data-ttu-id="c56c0-104">空間完善的設計</span><span class="sxs-lookup"><span data-stu-id="c56c0-104">Spatial sound design</span></span>

<span data-ttu-id="c56c0-105">空間的聲音是訓練活動，協助工具，在混合的實境應用程式的 UX 設計的強大工具。</span><span class="sxs-lookup"><span data-stu-id="c56c0-105">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

<span data-ttu-id="c56c0-106">如果您曾經玩過[Marco Polo](https://en.wikipedia.org/wiki/Marco_Polo_(game))，或者有其他人呼叫您的手機，以協助您找到它，您已熟悉空間音效的重要性。</span><span class="sxs-lookup"><span data-stu-id="c56c0-106">If you've ever played [Marco Polo](https://en.wikipedia.org/wiki/Marco_Polo_(game)), or had someone call your phone to help you locate it, you are already familiar with the importance of spatial sound.</span></span> <span data-ttu-id="c56c0-107">我們在日常生活中使用音效提示，來找出物件，取得某人的注意，或進一步了解我們的環境。</span><span class="sxs-lookup"><span data-stu-id="c56c0-107">We use sound cues in our daily lives to locate objects, get someone's attention, or get a better understanding of our environment.</span></span> <span data-ttu-id="c56c0-108">更接近您的應用程式的聲音行為真實世界、 更多的說服和吸引人的會您的虛擬世界中所顯示的一樣。</span><span class="sxs-lookup"><span data-stu-id="c56c0-108">The more closely your app's sound behaves like it does in the real world, the more convincing and engaging your virtual world will be.</span></span>

<br>

> [!VIDEO https://www.youtube.com/embed/aB3TDjYklmo]

## <a name="device-support"></a><span data-ttu-id="c56c0-109">裝置支援</span><span class="sxs-lookup"><span data-stu-id="c56c0-109">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c56c0-110">功能</span><span class="sxs-lookup"><span data-stu-id="c56c0-110">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="c56c0-111"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c56c0-111"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c56c0-112"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="c56c0-112"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="c56c0-113">空間音效</span><span class="sxs-lookup"><span data-stu-id="c56c0-113">Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="c56c0-114">✔️</span><span class="sxs-lookup"><span data-stu-id="c56c0-114">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="c56c0-115">✔️</span><span class="sxs-lookup"><span data-stu-id="c56c0-115">✔️</span></span></td>
</tr>
</table>

## <a name="four-key-things-spatial-sound-does-for-mixed-reality-development"></a><span data-ttu-id="c56c0-116">四個空間的聲音會替混合的實境開發的重要事項</span><span class="sxs-lookup"><span data-stu-id="c56c0-116">Four key things spatial sound does for mixed reality development</span></span>

<span data-ttu-id="c56c0-117">根據預設，音效播放立體聲。</span><span class="sxs-lookup"><span data-stu-id="c56c0-117">By default, sounds are played back in stereo.</span></span> <span data-ttu-id="c56c0-118">這表示聲音會玩沒有空間的位置，讓使用者不知道聲音來自何處。</span><span class="sxs-lookup"><span data-stu-id="c56c0-118">This means the sound will play with no spatial position, so the user does not know where the sound came from.</span></span> <span data-ttu-id="c56c0-119">空間的聲音會執行混合的實境開發的四個重要的事項：</span><span class="sxs-lookup"><span data-stu-id="c56c0-119">Spatial sound does four key things for mixed reality development:</span></span>

<span data-ttu-id="c56c0-120">**接地**</span><span class="sxs-lookup"><span data-stu-id="c56c0-120">**Grounding**</span></span>

<span data-ttu-id="c56c0-121">沒有聲音，虛擬物件實際上就不再存在於當我們開啟它們遠離我們標頭。</span><span class="sxs-lookup"><span data-stu-id="c56c0-121">Without sound, virtual objects effectively cease to exist when we turn our head away from them.</span></span> <span data-ttu-id="c56c0-122">就像真正的物件，您會想要聽聽這些物件，即使看不到它們，而且您想要找不到這些任何位置都可以。</span><span class="sxs-lookup"><span data-stu-id="c56c0-122">Just like real objects, you want to be able to hear these objects even when you can't see them, and you want to be able to locate them anywhere around you.</span></span> <span data-ttu-id="c56c0-123">就像虛擬物件必須奠基於對以視覺化方式來與您的實際混合，他們也必須用語音接地。</span><span class="sxs-lookup"><span data-stu-id="c56c0-123">Just as virtual objects need to be grounded visually to blend with your real world, they also need to be grounded audibly.</span></span> <span data-ttu-id="c56c0-124">空間音效順暢地混合現實世界裡音訊環境與數位音訊的環境。</span><span class="sxs-lookup"><span data-stu-id="c56c0-124">Spatial sound seamlessly blends your real world audio environment with the digital audio environment.</span></span>

<span data-ttu-id="c56c0-125">**使用者注意**</span><span class="sxs-lookup"><span data-stu-id="c56c0-125">**User attention**</span></span>

<span data-ttu-id="c56c0-126">在混合的實境體驗，您無法假設正在您的使用者，並預期會看到您以視覺方式放置在世界的內容。</span><span class="sxs-lookup"><span data-stu-id="c56c0-126">In mixed reality experiences, you can't assume where your user is looking and expect them to see something you place in the world visually.</span></span> <span data-ttu-id="c56c0-127">但使用者一律可以聽到聲音，播放甚至物件播放音效時其背後。</span><span class="sxs-lookup"><span data-stu-id="c56c0-127">But users can always hear a sound play even when the object playing the sound is behind them.</span></span> <span data-ttu-id="c56c0-128">使用者習慣擁有繪製以音效-注意我們 instinctually 目光轉向我們聽聽我們週遭的物件。</span><span class="sxs-lookup"><span data-stu-id="c56c0-128">People are used to having their attention drawn by sound - we instinctually look toward an object that we hear around us.</span></span> <span data-ttu-id="c56c0-129">當您想要直接將音效，位置是很自然且快速的方式，引導他們的使用者的視線的特定位置，而不是指向它們在視覺上，使用箭號。</span><span class="sxs-lookup"><span data-stu-id="c56c0-129">When you want to direct your user's gaze to a particular place, rather than using an arrow to point them visually, placing a sound in that location is a very natural and fast way to guide them.</span></span>

<span data-ttu-id="c56c0-130">**訓練活動**</span><span class="sxs-lookup"><span data-stu-id="c56c0-130">**Immersion**</span></span>

<span data-ttu-id="c56c0-131">當物件移動，或相衝突時，通常會聽到這些資料之間的互動。</span><span class="sxs-lookup"><span data-stu-id="c56c0-131">When objects move or collide, we usually hear those interactions between materials.</span></span> <span data-ttu-id="c56c0-132">因此當您的物件不相同的聲音就像在真實世界中，訓練活動的層級是遺失-例如一路向下觀賞嚇人的影片與磁碟區。</span><span class="sxs-lookup"><span data-stu-id="c56c0-132">So when your objects don't make the same sound they would in the real world, a level of immersion is lost - like watching a scary movie with the volume all the way down.</span></span> <span data-ttu-id="c56c0-133">聽起來真實世界中的來自空間-中的特定點，當我們開啟我們，我們聽聽這些聽起來來自何處耳朵，相對的變更，並追蹤的任何音效位置這種方式。</span><span class="sxs-lookup"><span data-stu-id="c56c0-133">All sounds in the real world come from a particular point in space - when we turn our heads, we hear the change in where those sounds are coming from relative to our ears, and we can track the location of any sound this way.</span></span> <span data-ttu-id="c56c0-134">Spatialized 聽起來構成的位置超出我們可以看到 「 風格 」。</span><span class="sxs-lookup"><span data-stu-id="c56c0-134">Spatialized sounds make up the "feel" of a place beyond what we can see.</span></span>

<span data-ttu-id="c56c0-135">**互動設計**</span><span class="sxs-lookup"><span data-stu-id="c56c0-135">**Interaction design**</span></span>

<span data-ttu-id="c56c0-136">在大部分傳統的互動式體驗，以標準 mono 或音響播放互動音效，例如 UI 音效。</span><span class="sxs-lookup"><span data-stu-id="c56c0-136">In most traditional interactive experiences, interaction sounds like UI sound effects are played in standard mono or stereo.</span></span> <span data-ttu-id="c56c0-137">但是，因為在混合實境中的所有項目 （包括 UI） 的 3D 空間中有這些物件受益於 spatialized 音效。</span><span class="sxs-lookup"><span data-stu-id="c56c0-137">But because everything in mixed reality exists in 3D space - including the UI - these objects benefit from spatialized sounds.</span></span> <span data-ttu-id="c56c0-138">當我們按下按鈕，以在真實世界中的時，我們聽到的聲音來自於該按鈕。</span><span class="sxs-lookup"><span data-stu-id="c56c0-138">When we press a button in the real world, the sound we hear comes from that button.</span></span> <span data-ttu-id="c56c0-139">藉由 spatializing 互動的聲音，我們會一次提供更自然且真實的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="c56c0-139">By spatializing interaction sounds, we again provide a more natural and realistic user experience.</span></span>

## <a name="best-practices-when-using-spatial-sound"></a><span data-ttu-id="c56c0-140">使用空間的聲音時的最佳作法</span><span class="sxs-lookup"><span data-stu-id="c56c0-140">Best practices when using spatial sound</span></span>

<span data-ttu-id="c56c0-141">**實際的聲音優於合成或非自然音效運作**</span><span class="sxs-lookup"><span data-stu-id="c56c0-141">**Real sounds work better than synthesized or unnatural sounds**</span></span>

<span data-ttu-id="c56c0-142">更熟悉您的使用者是使用音效，它會認為，更多真實的類型，並更輕鬆地他們將能夠在其環境中找到它。</span><span class="sxs-lookup"><span data-stu-id="c56c0-142">The more familiar your user is with a type of sound, the more real it will feel, and the more easily they will be able to locate it in their environment.</span></span> <span data-ttu-id="c56c0-143">人類聲音，比方說，是一種非常常見的音效，並您的使用者將會找到它只要盡真人和他們交談，聊天室中。</span><span class="sxs-lookup"><span data-stu-id="c56c0-143">A human voice, for example, is a very common type of sound, and your users will locate it just as quickly as a real person in the room talking to them.</span></span>

<span data-ttu-id="c56c0-144">**預期優先於模擬**</span><span class="sxs-lookup"><span data-stu-id="c56c0-144">**Expectation trumps simulation**</span></span>

<span data-ttu-id="c56c0-145">如果您習慣於來自特定方向的音效，將會引導您注意，不論空間提示該方向中。例如，大多時候我們聽聽鳥，它們是我們上面。</span><span class="sxs-lookup"><span data-stu-id="c56c0-145">If you are used to a sound coming from a particular direction, your attention will be guided in that direction regardless of spatial cues. For example, most of the time that we hear birds, they are above us.</span></span> <span data-ttu-id="c56c0-146">即使您將其下方的聲音，播放音效的 bird 會很有可能會導致您的使用者，來查閱。</span><span class="sxs-lookup"><span data-stu-id="c56c0-146">Playing the sound of a bird will most likely cause your user to look up, even if you place the sound below them.</span></span> <span data-ttu-id="c56c0-147">這是通常令人混淆，建議使用像是這些點，而不需以更自然的體驗會針對它們的期望。</span><span class="sxs-lookup"><span data-stu-id="c56c0-147">This is usually confusing, and it is recommended that you work with expectations like these rather than going against them for a more natural experience.</span></span>

<span data-ttu-id="c56c0-148">**應該 spatialized 大部分的音效**</span><span class="sxs-lookup"><span data-stu-id="c56c0-148">**Most sounds should be spatialized**</span></span>

<span data-ttu-id="c56c0-149">如先前所述，在混合實境中的所有項目在 3D 空間中存在-您聽起來也應該。</span><span class="sxs-lookup"><span data-stu-id="c56c0-149">As mentioned above, everything in Mixed Reality exists in 3D space - your sounds should as well.</span></span> <span data-ttu-id="c56c0-150">特別是當它繫結至功能表或一些其他的 UI，甚至音樂有時可以受益於往。</span><span class="sxs-lookup"><span data-stu-id="c56c0-150">Even music can sometimes benefit from spatialization, particularly when it's tied to a menu or some other UI.</span></span>

<span data-ttu-id="c56c0-151">**避免不可見的 fixit 發出器**</span><span class="sxs-lookup"><span data-stu-id="c56c0-151">**Avoid invisible emitters**</span></span>

<span data-ttu-id="c56c0-152">因為我們已經看我們聽聽我們週遭的音效已條件，它可以是一種非自然和甚至 unnerving 的體驗，以找出有沒有視覺化的目前狀態的音效。</span><span class="sxs-lookup"><span data-stu-id="c56c0-152">Because we've been conditioned to look at sounds that we hear around us, it can be an unnatural and even unnerving experience to locate a sound that has no visual presence.</span></span> <span data-ttu-id="c56c0-153">在真實世界中的音效不來自空白空間，因此務必如果音訊的 fixit 發出器置於使用者的即時環境，它也會顯示。</span><span class="sxs-lookup"><span data-stu-id="c56c0-153">Sounds in the real world don't come from empty space, so be sure that if an audio emitter is placed within the user's immediate environment that it can also be seen.</span></span>

<span data-ttu-id="c56c0-154">**避免空間遮罩**</span><span class="sxs-lookup"><span data-stu-id="c56c0-154">**Avoid spatial masking**</span></span>

<span data-ttu-id="c56c0-155">空間音效依賴十分難以察覺的原音提示，可以由其他音效不堪負荷。</span><span class="sxs-lookup"><span data-stu-id="c56c0-155">Spatial sound relies on very subtle acoustic cues that can be overpowered by other sounds.</span></span> <span data-ttu-id="c56c0-156">如果您有立體聲的音樂或環境的聲音，請確定它們是夠低，在混合，以提供詳細資料的程式會讓使用者輕鬆地找到它們，並方便響起真實與自然的 spatialized 聲音的空間。</span><span class="sxs-lookup"><span data-stu-id="c56c0-156">If you do have stereo music or ambient sounds, make sure they are low enough in the mix to give room for the details of your spatialized sounds that will allow your users to locate them easily, and keep them sounding realistic and natural.</span></span>

## <a name="general-concepts-to-keep-in-mind-when-using-spatial-sound"></a><span data-ttu-id="c56c0-157">要牢記在心，使用空間的聲音時的一般概念</span><span class="sxs-lookup"><span data-stu-id="c56c0-157">General concepts to keep in mind when using spatial sound</span></span>

<span data-ttu-id="c56c0-158">**空間的聲音是模擬**</span><span class="sxs-lookup"><span data-stu-id="c56c0-158">**Spatial sound is a simulation**</span></span>

<span data-ttu-id="c56c0-159">最常使用的空間聲音正在看起來好像它動畫從實際或虛擬世界中物件的音效。</span><span class="sxs-lookup"><span data-stu-id="c56c0-159">The most frequent use of spatial sound is making a sound seem as though it is emanating from a real or virtual object in the world.</span></span> <span data-ttu-id="c56c0-160">因此，spatialized 聽起來可能最有意義來自這類物件。</span><span class="sxs-lookup"><span data-stu-id="c56c0-160">Thus, spatialized sounds may make the most sense coming from such objects.</span></span>

<span data-ttu-id="c56c0-161">請注意，會根據大小的物件和使用者的距離明顯認知空間聲音表示音效一定不應發出物件 （差異） 的中心的精確度。</span><span class="sxs-lookup"><span data-stu-id="c56c0-161">Note that the perceived accuracy of spatial sound means that a sound shouldn't necessarily emit from the center of an object, as the difference will be noticeable depending on the size of the object and distance from the user.</span></span> <span data-ttu-id="c56c0-162">使用小型物件，該物件的中心點是通常就已足夠。</span><span class="sxs-lookup"><span data-stu-id="c56c0-162">With small objects, the center point of the object is usually sufficient.</span></span> <span data-ttu-id="c56c0-163">對於較大的物件，您可能想音效的 fixit 發出器或多個的 fixit 發出器應該會產生聲音物件內的特定位置。</span><span class="sxs-lookup"><span data-stu-id="c56c0-163">For larger objects, you may want a sound emitter or multiple emitters at the specific location within the object that is supposed to be producing the sound.</span></span>

<span data-ttu-id="c56c0-164">**標準化所有的音效**</span><span class="sxs-lookup"><span data-stu-id="c56c0-164">**Normalize all sounds**</span></span>

<span data-ttu-id="c56c0-165">距離衰減發生快速在來自使用者的第一個計量表中，其方式就如同真實世界中。</span><span class="sxs-lookup"><span data-stu-id="c56c0-165">Distance attenuation happens quickly within the first meter from the user, as it does in the real world.</span></span> <span data-ttu-id="c56c0-166">所有音訊檔案應該標準化為確保實際精確距離衰減，而且，可以聽到聲音時數個度量消失 （如果適用）。</span><span class="sxs-lookup"><span data-stu-id="c56c0-166">All audio files should be normalized to ensure physically accurate distance attenuation, and ensure that a sound can be heard when several meters away (when applicable).</span></span> <span data-ttu-id="c56c0-167">空間的音訊引擎會處理所需的 「 覺得 「 就在一定距離之間 （含衰減和 「 距離提示 」 的組合），並套用任何衰減除此之外，可以減少的影響音效衰減。</span><span class="sxs-lookup"><span data-stu-id="c56c0-167">The spatial audio engine will handle the attenuation necessary for a sound to "feel" like it's at a certain distance (with a combination of attenuation and "distance cues"), and applying any attenuation on top of that could reduce the effect.</span></span> <span data-ttu-id="c56c0-168">外部模擬實際的物件，初始距離的衰變*空間音效*聽起來可能會讓適當的音訊的混合。</span><span class="sxs-lookup"><span data-stu-id="c56c0-168">Outside of simulating a real object, the initial distance decay of *spatial sound* sounds will likely be more than enough for a proper mix of your audio.</span></span>

<span data-ttu-id="c56c0-169">**物件探索和使用者介面**</span><span class="sxs-lookup"><span data-stu-id="c56c0-169">**Object discovery and user interfaces**</span></span>

<span data-ttu-id="c56c0-170">使用時音訊提示，將超過其目前的檢視使用者的注意力導向，音效應可發出聲音且顯著混合，也高於任何立體聲的音效，與任何其他 spatialized 的音效這可能會偏離方向的音訊提示中。</span><span class="sxs-lookup"><span data-stu-id="c56c0-170">When using audio cues to direct the user's attention beyond their current view, the sound should be audible and prominent in the mix, well above any stereo sounds, and any other spatialized sounds which might distract from the directional audio cue.</span></span> <span data-ttu-id="c56c0-171">音效與音樂與使用者介面 （例如功能表） 的項目相關聯，音效的 fixit 發出器應該附加至該物件。</span><span class="sxs-lookup"><span data-stu-id="c56c0-171">For sounds and music that are associated with an element of the user interface (e.g. a menu), the sound emitter should be attached to that object.</span></span> <span data-ttu-id="c56c0-172">立體聲和其他非位置音訊播放可能會使 spatialized 的項目使用者找出困難 (請參閱上述：避免空間遮罩）。</span><span class="sxs-lookup"><span data-stu-id="c56c0-172">Stereo and other non-positional audio playing can make spatialized elements difficult for users to locate (See above: Avoid spatial masking).</span></span>

<span data-ttu-id="c56c0-173">**透過標準的 3D 音效盡量使用空間的音效**</span><span class="sxs-lookup"><span data-stu-id="c56c0-173">**Use spatial sound over standard 3D sound as much as possible**</span></span>

<span data-ttu-id="c56c0-174">在混合實境，以獲得最佳使用者體驗，以 3D 的音訊，都應該使用空間的音效，而不是傳統的 3D 音訊技術來達成。</span><span class="sxs-lookup"><span data-stu-id="c56c0-174">In mixed reality, for the best user experience, 3D audio should be achieved using spatial sound rather than legacy 3D audio technologies.</span></span> <span data-ttu-id="c56c0-175">一般情況下，改善的空間值得小型的 CPU 成本是透過標準 3D 音效。</span><span class="sxs-lookup"><span data-stu-id="c56c0-175">In general, the improved spatialization is worth the small CPU cost over standard 3D sound.</span></span> <span data-ttu-id="c56c0-176">標準 3D 音訊可以用於低優先順序的音效、 音效 spatialized 但不一定是繫結至實體或虛擬的物件和使用者永遠不會需要找出與應用程式互動的物件。</span><span class="sxs-lookup"><span data-stu-id="c56c0-176">Standard 3D audio can be used for low-priority sounds, sounds that are spatialized but not necessarily tied to a physical or virtual object, and objects that the user never need locate to interact with the app.</span></span>

## <a name="see-also"></a><span data-ttu-id="c56c0-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c56c0-177">See also</span></span>
* [<span data-ttu-id="c56c0-178">空間的音效</span><span class="sxs-lookup"><span data-stu-id="c56c0-178">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="c56c0-179">空間對應</span><span class="sxs-lookup"><span data-stu-id="c56c0-179">Spatial mapping</span></span>](spatial-mapping.md)
