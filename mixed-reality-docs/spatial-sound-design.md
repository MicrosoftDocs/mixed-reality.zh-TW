---
title: 空間音效設計
description: 空間音效是強大的工具，可在混合現實應用程式中進行深度、協助工具及 UX 設計。
author: joekellyms
ms.author: joekelly
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，空間音效，設計，樣式
ms.openlocfilehash: acc568eeb08d2a27574dcfbc9f132519e1e31843
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438285"
---
# <a name="spatial-sound-design"></a><span data-ttu-id="bde3e-104">空間音效設計</span><span class="sxs-lookup"><span data-stu-id="bde3e-104">Spatial sound design</span></span>

<span data-ttu-id="bde3e-105">空間音效是強大的工具，可在混合現實應用程式中進行深度、協助工具及 UX 設計。</span><span class="sxs-lookup"><span data-stu-id="bde3e-105">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

<span data-ttu-id="bde3e-106">如果您曾玩過[Marco 水球資料](https://en.wikipedia.org/wiki/Marco_Polo_(game))，或有人撥打電話協助您找到它，您已經很熟悉空間音效的重要性。</span><span class="sxs-lookup"><span data-stu-id="bde3e-106">If you've ever played [Marco Polo](https://en.wikipedia.org/wiki/Marco_Polo_(game)), or had someone call your phone to help you locate it, you are already familiar with the importance of spatial sound.</span></span> <span data-ttu-id="bde3e-107">我們會在日常生活中使用音效提示來找出物件、取得某人的注意，或進一步瞭解我們的環境。</span><span class="sxs-lookup"><span data-stu-id="bde3e-107">We use sound cues in our daily lives to locate objects, get someone's attention, or get a better understanding of our environment.</span></span> <span data-ttu-id="bde3e-108">您的應用程式音效行為就像在現實世界中一樣，更值得的是，您的虛擬世界也會更具說服力。</span><span class="sxs-lookup"><span data-stu-id="bde3e-108">The more closely your app's sound behaves like it does in the real world, the more convincing and engaging your virtual world will be.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a><span data-ttu-id="bde3e-109">裝置支援</span><span class="sxs-lookup"><span data-stu-id="bde3e-109">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="bde3e-110"><strong>特徵</strong></span><span class="sxs-lookup"><span data-stu-id="bde3e-110"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="bde3e-111"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="bde3e-111"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="bde3e-112"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="bde3e-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="bde3e-113">空間音效設計</span><span class="sxs-lookup"><span data-stu-id="bde3e-113">Spatial sound design</span></span></td>
        <td><span data-ttu-id="bde3e-114">✔️</span><span class="sxs-lookup"><span data-stu-id="bde3e-114">✔️</span></span></td>
        <td><span data-ttu-id="bde3e-115">✔️</span><span class="sxs-lookup"><span data-stu-id="bde3e-115">✔️</span></span></td>
    </tr>
</table>


## <a name="four-key-things-spatial-sound-does-for-mixed-reality-development"></a><span data-ttu-id="bde3e-116">有四個重要事項空間音效適用于混合現實開發</span><span class="sxs-lookup"><span data-stu-id="bde3e-116">Four key things spatial sound does for mixed reality development</span></span>

<span data-ttu-id="bde3e-117">預設會以身歷聲播放聲音。</span><span class="sxs-lookup"><span data-stu-id="bde3e-117">By default, sounds are played back in stereo.</span></span> <span data-ttu-id="bde3e-118">這表示音效會在沒有空間位置的情況下播放，因此使用者不知道音效的來源。</span><span class="sxs-lookup"><span data-stu-id="bde3e-118">This means the sound will play with no spatial position, so the user does not know where the sound came from.</span></span> <span data-ttu-id="bde3e-119">空間音效針對混合現實開發進行四個重要事項：</span><span class="sxs-lookup"><span data-stu-id="bde3e-119">Spatial sound does four key things for mixed reality development:</span></span>

<span data-ttu-id="bde3e-120">**舌**</span><span class="sxs-lookup"><span data-stu-id="bde3e-120">**Grounding**</span></span>

<span data-ttu-id="bde3e-121">如果沒有音效，虛擬物件會在離開時，有效地停止存在。</span><span class="sxs-lookup"><span data-stu-id="bde3e-121">Without sound, virtual objects effectively cease to exist when we turn our head away from them.</span></span> <span data-ttu-id="bde3e-122">就像真正的物件一樣，即使您看不到這些物件，也想要能夠聽到它們，而且想要能夠在任何地方找到它們。</span><span class="sxs-lookup"><span data-stu-id="bde3e-122">Just like real objects, you want to be able to hear these objects even when you can't see them, and you want to be able to locate them anywhere around you.</span></span> <span data-ttu-id="bde3e-123">就像虛擬物件需要以視覺化方式與真實世界混合，它們也必須以語音的形式進行接地。</span><span class="sxs-lookup"><span data-stu-id="bde3e-123">Just as virtual objects need to be grounded visually to blend with your real world, they also need to be grounded audibly.</span></span> <span data-ttu-id="bde3e-124">空間音效可順暢地將您的真實世界音訊環境與數位音訊環境結合。</span><span class="sxs-lookup"><span data-stu-id="bde3e-124">Spatial sound seamlessly blends your real world audio environment with the digital audio environment.</span></span>

<span data-ttu-id="bde3e-125">**使用者注意**</span><span class="sxs-lookup"><span data-stu-id="bde3e-125">**User attention**</span></span>

<span data-ttu-id="bde3e-126">在混合現實的體驗中，您無法假設使用者正在尋找的位置，並預期他們會看到您在世界中所處的東西。</span><span class="sxs-lookup"><span data-stu-id="bde3e-126">In mixed reality experiences, you can't assume where your user is looking and expect them to see something you place in the world visually.</span></span> <span data-ttu-id="bde3e-127">但是即使在播放音效的物件落後時，使用者也可以聽到播放音效。</span><span class="sxs-lookup"><span data-stu-id="bde3e-127">But users can always hear a sound play even when the object playing the sound is behind them.</span></span> <span data-ttu-id="bde3e-128">人們用來以音效繪製注意力-我們 instinctually 探討我們聽到我們的物件。</span><span class="sxs-lookup"><span data-stu-id="bde3e-128">People are used to having their attention drawn by sound - we instinctually look toward an object that we hear around us.</span></span> <span data-ttu-id="bde3e-129">當您想要將使用者的注視導向至特定位置，而不是使用箭號來以視覺方式指向時，將音效放在該位置，是非常自然且快速的方式。</span><span class="sxs-lookup"><span data-stu-id="bde3e-129">When you want to direct your user's gaze to a particular place, rather than using an arrow to point them visually, placing a sound in that location is a very natural and fast way to guide them.</span></span>

<span data-ttu-id="bde3e-130">**深度**</span><span class="sxs-lookup"><span data-stu-id="bde3e-130">**Immersion**</span></span>

<span data-ttu-id="bde3e-131">當物件移動或衝突時，通常會聽到這些材質之間的互動。</span><span class="sxs-lookup"><span data-stu-id="bde3e-131">When objects move or collide, we usually hear those interactions between materials.</span></span> <span data-ttu-id="bde3e-132">因此，當您的物件不會在真實世界中建立相同的音效時，就會失去一層深度，像是監看具有音量的恐怖電影。</span><span class="sxs-lookup"><span data-stu-id="bde3e-132">So when your objects don't make the same sound they would in the real world, a level of immersion is lost - like watching a scary movie with the volume all the way down.</span></span> <span data-ttu-id="bde3e-133">真實世界中的所有音效都來自于空間中的特定時間點-當我們轉型時，我們會聽到這些音效從相對於我們的耳的變更，而我們可以這種方式追蹤任何聲音的位置。</span><span class="sxs-lookup"><span data-stu-id="bde3e-133">All sounds in the real world come from a particular point in space - when we turn our heads, we hear the change in where those sounds are coming from relative to our ears, and we can track the location of any sound this way.</span></span> <span data-ttu-id="bde3e-134">Hrtf 聽起來可以讓您的「感覺」超越我們所見的範圍。</span><span class="sxs-lookup"><span data-stu-id="bde3e-134">Spatialized sounds make up the "feel" of a place beyond what we can see.</span></span>

<span data-ttu-id="bde3e-135">**互動設計**</span><span class="sxs-lookup"><span data-stu-id="bde3e-135">**Interaction design**</span></span>

<span data-ttu-id="bde3e-136">在最傳統的互動式體驗中，互動音效（如 UI 音效）會以標準 mono 或身歷聲播放。</span><span class="sxs-lookup"><span data-stu-id="bde3e-136">In most traditional interactive experiences, interaction sounds like UI sound effects are played in standard mono or stereo.</span></span> <span data-ttu-id="bde3e-137">但因為混合現實中的所有專案都存在於3D 空間中（包括 UI），所以這些物件從 hrtf 音效中受益。</span><span class="sxs-lookup"><span data-stu-id="bde3e-137">But because everything in mixed reality exists in 3D space - including the UI - these objects benefit from spatialized sounds.</span></span> <span data-ttu-id="bde3e-138">當我們在現實世界中按下按鈕時，我們聽到的聲音來自該按鈕。</span><span class="sxs-lookup"><span data-stu-id="bde3e-138">When we press a button in the real world, the sound we hear comes from that button.</span></span> <span data-ttu-id="bde3e-139">藉由 spatializing 互動音效，我們再次提供更自然且逼真的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="bde3e-139">By spatializing interaction sounds, we again provide a more natural and realistic user experience.</span></span>

## <a name="best-practices-when-using-spatial-sound"></a><span data-ttu-id="bde3e-140">使用空間音效的最佳做法</span><span class="sxs-lookup"><span data-stu-id="bde3e-140">Best practices when using spatial sound</span></span>

<span data-ttu-id="bde3e-141">**真實音效的效果優於合成或非自然音效**</span><span class="sxs-lookup"><span data-stu-id="bde3e-141">**Real sounds work better than synthesized or unnatural sounds**</span></span>

<span data-ttu-id="bde3e-142">您的使用者會使用某種類型的音效，這就是更真實的感覺，而且可以更輕鬆地在其環境中找到它。</span><span class="sxs-lookup"><span data-stu-id="bde3e-142">The more familiar your user is with a type of sound, the more real it will feel, and the more easily they will be able to locate it in their environment.</span></span> <span data-ttu-id="bde3e-143">例如，人類語音是一種非常常見的音效類型，而您的使用者會像是房間裡的真正人一樣快速地找到它。</span><span class="sxs-lookup"><span data-stu-id="bde3e-143">A human voice, for example, is a very common type of sound, and your users will locate it just as quickly as a real person in the room talking to them.</span></span>

<span data-ttu-id="bde3e-144">**預期的優先于模擬**</span><span class="sxs-lookup"><span data-stu-id="bde3e-144">**Expectation trumps simulation**</span></span>

<span data-ttu-id="bde3e-145">如果您使用的是來自特定方向的音效，不論空間提示為何，您的注意力都會以該方向引導。例如，大部分的人都聽過鳥瞰，這些都是在美國。</span><span class="sxs-lookup"><span data-stu-id="bde3e-145">If you are used to a sound coming from a particular direction, your attention will be guided in that direction regardless of spatial cues. For example, most of the time that we hear birds, they are above us.</span></span> <span data-ttu-id="bde3e-146">播放鳥的音效很可能會導致您的使用者進行查閱，即使您將音效放在其下方也一樣。</span><span class="sxs-lookup"><span data-stu-id="bde3e-146">Playing the sound of a bird will most likely cause your user to look up, even if you place the sound below them.</span></span> <span data-ttu-id="bde3e-147">這通常會造成混淆，因此建議您處理這類預期，而不要使用它們，以獲得更自然的體驗。</span><span class="sxs-lookup"><span data-stu-id="bde3e-147">This is usually confusing, and it is recommended that you work with expectations like these rather than going against them for a more natural experience.</span></span>

<span data-ttu-id="bde3e-148">**大部分的音效都應該是 hrtf**</span><span class="sxs-lookup"><span data-stu-id="bde3e-148">**Most sounds should be spatialized**</span></span>

<span data-ttu-id="bde3e-149">如上所述，混合現實中的所有專案都存在於3D 空間中，您的音效也應該如此。</span><span class="sxs-lookup"><span data-stu-id="bde3e-149">As mentioned above, everything in Mixed Reality exists in 3D space - your sounds should as well.</span></span> <span data-ttu-id="bde3e-150">即使是音樂也可以受益于 spatialization，特別是當它系結至功能表或其他 UI 時。</span><span class="sxs-lookup"><span data-stu-id="bde3e-150">Even music can sometimes benefit from spatialization, particularly when it's tied to a menu or some other UI.</span></span>

<span data-ttu-id="bde3e-151">**避免隱藏的發射器**</span><span class="sxs-lookup"><span data-stu-id="bde3e-151">**Avoid invisible emitters**</span></span>

<span data-ttu-id="bde3e-152">因為我們已有條件地查看我們聽到的聲音，所以可能是非自然，甚至是 unnerving 的經驗，以找出沒有視覺狀態的音效。</span><span class="sxs-lookup"><span data-stu-id="bde3e-152">Because we've been conditioned to look at sounds that we hear around us, it can be an unnatural and even unnerving experience to locate a sound that has no visual presence.</span></span> <span data-ttu-id="bde3e-153">真實世界中的音效不是來自空白的空間，因此請確定如果音訊發射器放在使用者的立即環境中，也可以看到它。</span><span class="sxs-lookup"><span data-stu-id="bde3e-153">Sounds in the real world don't come from empty space, so be sure that if an audio emitter is placed within the user's immediate environment that it can also be seen.</span></span>

<span data-ttu-id="bde3e-154">**避免空間遮罩**</span><span class="sxs-lookup"><span data-stu-id="bde3e-154">**Avoid spatial masking**</span></span>

<span data-ttu-id="bde3e-155">空間音效依賴非常微妙的聲場提示，可由其他音效不堪負荷。</span><span class="sxs-lookup"><span data-stu-id="bde3e-155">Spatial sound relies on very subtle acoustic cues that can be overpowered by other sounds.</span></span> <span data-ttu-id="bde3e-156">如果您有身歷聲音樂或環境音效，請確定它們的混合不足以提供 hrtf 音效的詳細資料，讓您的使用者可以輕鬆地找到它們，並將它們聽起來是真實且自然的。</span><span class="sxs-lookup"><span data-stu-id="bde3e-156">If you do have stereo music or ambient sounds, make sure they are low enough in the mix to give room for the details of your spatialized sounds that will allow your users to locate them easily, and keep them sounding realistic and natural.</span></span>

## <a name="general-concepts-to-keep-in-mind-when-using-spatial-sound"></a><span data-ttu-id="bde3e-157">使用空間音效時，要牢記在心的一般概念</span><span class="sxs-lookup"><span data-stu-id="bde3e-157">General concepts to keep in mind when using spatial sound</span></span>

<span data-ttu-id="bde3e-158">**空間音效是模擬**</span><span class="sxs-lookup"><span data-stu-id="bde3e-158">**Spatial sound is a simulation**</span></span>

<span data-ttu-id="bde3e-159">空間音效最常用的方式，就好像是從世界上的真實或虛擬物件 mouseleave。</span><span class="sxs-lookup"><span data-stu-id="bde3e-159">The most frequent use of spatial sound is making a sound seem as though it is emanating from a real or virtual object in the world.</span></span> <span data-ttu-id="bde3e-160">因此，hrtf 聽起來可能是來自這類物件最有意義的。</span><span class="sxs-lookup"><span data-stu-id="bde3e-160">Thus, spatialized sounds may make the most sense coming from such objects.</span></span>

<span data-ttu-id="bde3e-161">請注意，看到的空間音效精確度表示音效不一定要從物件的中心發出，因為差異會因為物件的大小和與使用者的距離而明顯不同。</span><span class="sxs-lookup"><span data-stu-id="bde3e-161">Note that the perceived accuracy of spatial sound means that a sound shouldn't necessarily emit from the center of an object, as the difference will be noticeable depending on the size of the object and distance from the user.</span></span> <span data-ttu-id="bde3e-162">使用小型物件時，物件的中心點通常就已足夠。</span><span class="sxs-lookup"><span data-stu-id="bde3e-162">With small objects, the center point of the object is usually sufficient.</span></span> <span data-ttu-id="bde3e-163">對於較大的物件，您可能會想要在物件內的特定位置（應該會產生音效）上有音效發射器或多個發射器。</span><span class="sxs-lookup"><span data-stu-id="bde3e-163">For larger objects, you may want a sound emitter or multiple emitters at the specific location within the object that is supposed to be producing the sound.</span></span>

<span data-ttu-id="bde3e-164">**標準化所有聲音**</span><span class="sxs-lookup"><span data-stu-id="bde3e-164">**Normalize all sounds**</span></span>

<span data-ttu-id="bde3e-165">距離衰減會在使用者的第一個計量中快速進行，如同在現實世界中一樣。</span><span class="sxs-lookup"><span data-stu-id="bde3e-165">Distance attenuation happens quickly within the first meter from the user, as it does in the real world.</span></span> <span data-ttu-id="bde3e-166">所有的音訊檔案都應該正規化，以確保實際精確的距離衰減，並確保在有數個計量時可以聽到音效（如果適用）。</span><span class="sxs-lookup"><span data-stu-id="bde3e-166">All audio files should be normalized to ensure physically accurate distance attenuation, and ensure that a sound can be heard when several meters away (when applicable).</span></span> <span data-ttu-id="bde3e-167">空間音效引擎會處理音效「感覺」所需的衰減，如同在特定距離（結合了衰減和「距離提示」），並在上套用任何衰減，這可能會降低效果。</span><span class="sxs-lookup"><span data-stu-id="bde3e-167">The spatial audio engine will handle the attenuation necessary for a sound to "feel" like it's at a certain distance (with a combination of attenuation and "distance cues"), and applying any attenuation on top of that could reduce the effect.</span></span> <span data-ttu-id="bde3e-168">除了模擬實際物件外，*空間音效*的初始距離可能會比適當地混合您的音訊還多。</span><span class="sxs-lookup"><span data-stu-id="bde3e-168">Outside of simulating a real object, the initial distance decay of *spatial sound* sounds will likely be more than enough for a proper mix of your audio.</span></span>

<span data-ttu-id="bde3e-169">**物件探索和使用者介面**</span><span class="sxs-lookup"><span data-stu-id="bde3e-169">**Object discovery and user interfaces**</span></span>

<span data-ttu-id="bde3e-170">當使用 [音訊提示] 將使用者的注意力引導到超出其目前的視圖時，音效應該會在混合中、在任何身歷聲音效，以及任何其他 hrtf 聽起來可能會干擾方向音訊提示的情況下，聽起來很明顯。</span><span class="sxs-lookup"><span data-stu-id="bde3e-170">When using audio cues to direct the user's attention beyond their current view, the sound should be audible and prominent in the mix, well above any stereo sounds, and any other spatialized sounds which might distract from the directional audio cue.</span></span> <span data-ttu-id="bde3e-171">對於與使用者介面專案（例如功能表）相關聯的聲音和音樂，音效發射器應該附加至該物件。</span><span class="sxs-lookup"><span data-stu-id="bde3e-171">For sounds and music that are associated with an element of the user interface (e.g. a menu), the sound emitter should be attached to that object.</span></span> <span data-ttu-id="bde3e-172">身歷聲和其他非位置音訊播放可讓使用者很容易找到 hrtf 元素（請參閱上方：避免空間遮罩）。</span><span class="sxs-lookup"><span data-stu-id="bde3e-172">Stereo and other non-positional audio playing can make spatialized elements difficult for users to locate (See above: Avoid spatial masking).</span></span>

<span data-ttu-id="bde3e-173">**盡可能使用標準3D 音效的空間音效**</span><span class="sxs-lookup"><span data-stu-id="bde3e-173">**Use spatial sound over standard 3D sound as much as possible**</span></span>

<span data-ttu-id="bde3e-174">在混合的現實中，為了獲得最佳的使用者體驗，您應該使用空間音效而不是舊版3D 音訊技術來達成3D 音訊。</span><span class="sxs-lookup"><span data-stu-id="bde3e-174">In mixed reality, for the best user experience, 3D audio should be achieved using spatial sound rather than legacy 3D audio technologies.</span></span> <span data-ttu-id="bde3e-175">一般來說，改善的 spatialization 是值得一提的是標準3D 音效的小型 CPU 成本。</span><span class="sxs-lookup"><span data-stu-id="bde3e-175">In general, the improved spatialization is worth the small CPU cost over standard 3D sound.</span></span> <span data-ttu-id="bde3e-176">標準3D 音訊可用於低優先順序音效、hrtf 但不一定會系結至實體或虛擬物件的聲音，以及使用者不需要尋找來與應用程式互動的物件。</span><span class="sxs-lookup"><span data-stu-id="bde3e-176">Standard 3D audio can be used for low-priority sounds, sounds that are spatialized but not necessarily tied to a physical or virtual object, and objects that the user never need locate to interact with the app.</span></span>

## <a name="see-also"></a><span data-ttu-id="bde3e-177">請參閱</span><span class="sxs-lookup"><span data-stu-id="bde3e-177">See also</span></span>
* [<span data-ttu-id="bde3e-178">空間音效</span><span class="sxs-lookup"><span data-stu-id="bde3e-178">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="bde3e-179">空間對應</span><span class="sxs-lookup"><span data-stu-id="bde3e-179">Spatial mapping</span></span>](spatial-mapping.md)
