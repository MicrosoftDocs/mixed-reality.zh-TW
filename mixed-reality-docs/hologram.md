---
title: 什麼是全像投影？
description: HoloLens 可讓您檢視並與其互動三維全像投影，物件所做的光線和音效，會出現在您的世界。
author: beaufolsom
ms.author: befolsom
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、 HoloLens、 全像投影、 設計、 互動
ms.openlocfilehash: 5a6cc4df764b1f92f6bea2d7d6e6effe2164e4d6
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591185"
---
# <a name="what-is-a-hologram"></a><span data-ttu-id="3b72d-104">什麼是全像投影？</span><span class="sxs-lookup"><span data-stu-id="3b72d-104">What is a hologram?</span></span>

<span data-ttu-id="3b72d-105">HoloLens 可讓您建立**全像投影**、 物件所做的光線和音效，會出現在世界各地，就如同它們是真正的物件。</span><span class="sxs-lookup"><span data-stu-id="3b72d-105">HoloLens lets you create **holograms**, objects made of light and sound that appear in the world around you, just as if they were real objects.</span></span> <span data-ttu-id="3b72d-106">全像投影回應您[視線](gaze.md)，[筆勢](gestures.md)並[語音命令](voice-input.md)，並可進行互動[真實世界介面](spatial-mapping.md)看待您。</span><span class="sxs-lookup"><span data-stu-id="3b72d-106">Holograms respond to your [gaze](gaze.md), [gestures](gestures.md) and [voice commands](voice-input.md), and can interact with [real-world surfaces](spatial-mapping.md) around you.</span></span> <span data-ttu-id="3b72d-107">使用全像投影，您可以建立屬於您的世界的數位物件。</span><span class="sxs-lookup"><span data-stu-id="3b72d-107">With holograms, you can create digital objects that are part of your world.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/MVXH5V8MVQo]

## <a name="device-support"></a><span data-ttu-id="3b72d-108">裝置支援</span><span class="sxs-lookup"><span data-stu-id="3b72d-108">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="3b72d-109">功能</span><span class="sxs-lookup"><span data-stu-id="3b72d-109">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="3b72d-110"><a href="hololens-hardware-details.md">HoloLens （第 1 代）</a></span><span class="sxs-lookup"><span data-stu-id="3b72d-110"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="3b72d-111">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3b72d-111">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="3b72d-112"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="3b72d-112"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="3b72d-113">全像投影</span><span class="sxs-lookup"><span data-stu-id="3b72d-113">Holograms</span></span></td><td style="text-align: center;"> <span data-ttu-id="3b72d-114">✔️</span><span class="sxs-lookup"><span data-stu-id="3b72d-114">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="3b72d-115">✔️</span><span class="sxs-lookup"><span data-stu-id="3b72d-115">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

## <a name="a-hologram-is-made-of-light-and-sound"></a><span data-ttu-id="3b72d-116">雷射組成光線和音效</span><span class="sxs-lookup"><span data-stu-id="3b72d-116">A hologram is made of light and sound</span></span>

<span data-ttu-id="3b72d-117">全像投影的 HoloLens[呈現](rendering.md)會出現在全像攝影版的畫面格，直接呈現使用者的眼睛。</span><span class="sxs-lookup"><span data-stu-id="3b72d-117">The holograms that HoloLens [renders](rendering.md) appear in the holographic frame directly in front of the user's eyes.</span></span> <span data-ttu-id="3b72d-118">全像投影會加入您的世界裡，這表示您看到從顯示的光線和從周圍環境光中的光線。</span><span class="sxs-lookup"><span data-stu-id="3b72d-118">Holograms add light to your world, which means that you see both the light from the display and the light from your surroundings.</span></span> <span data-ttu-id="3b72d-119">HoloLens 不移除 light 眼睛，讓全像投影無法轉譯色彩黑色。</span><span class="sxs-lookup"><span data-stu-id="3b72d-119">HoloLens doesn't remove light from your eyes, so holograms can't be rendered with the color black.</span></span> <span data-ttu-id="3b72d-120">相反地，黑色的內容會顯示為透明。</span><span class="sxs-lookup"><span data-stu-id="3b72d-120">Instead, black content appears as transparent.</span></span>

<span data-ttu-id="3b72d-121">全像投影可以有許多不同的外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="3b72d-121">Holograms can have many different appearances and behaviors.</span></span> <span data-ttu-id="3b72d-122">一些實際並選取 實線，而其他人 cartoonish 和把。</span><span class="sxs-lookup"><span data-stu-id="3b72d-122">Some are realistic and solid, and others are cartoonish and ethereal.</span></span> <span data-ttu-id="3b72d-123">全像投影可以反白顯示功能的光線，並且可以在您的應用程式使用者介面中的項目。</span><span class="sxs-lookup"><span data-stu-id="3b72d-123">Holograms can highlight features in your surroundings, and they can be elements in your app's user interface.</span></span>

![地板上逐一查看的 dog 全像攝影版](images/fang3-640px.jpg)

<span data-ttu-id="3b72d-125">也可以將全像投影[音效](spatial-sound.md)，這會顯示為來自在周圍環境中的特定位置。</span><span class="sxs-lookup"><span data-stu-id="3b72d-125">Holograms can also make [sounds](spatial-sound.md), which will appear to come from a specific place in your surroundings.</span></span> <span data-ttu-id="3b72d-126">在 HoloLens，聽起來是來自兩個位於正上方 되 어，而不涵蓋它們的主講人。</span><span class="sxs-lookup"><span data-stu-id="3b72d-126">On HoloLens, sound comes from two speakers that are located directly above your ears, without covering them.</span></span> <span data-ttu-id="3b72d-127">類似於顯示器，主講人是加總，而不會封鎖您的環境的聲音引進新的音效。</span><span class="sxs-lookup"><span data-stu-id="3b72d-127">Similar to the displays, the speakers are additive, introducing new sounds without blocking the sounds from your environment.</span></span>

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a><span data-ttu-id="3b72d-128">全像可以放置在全球或配合您的標記</span><span class="sxs-lookup"><span data-stu-id="3b72d-128">A hologram can be placed in the world or tag along with you</span></span>

<span data-ttu-id="3b72d-129">當您有想讓雷射的特定位置時，您可以[放置](coordinate-systems.md)其中精確地世界中。</span><span class="sxs-lookup"><span data-stu-id="3b72d-129">When you have a particular location where you want a hologram, you can [place](coordinate-systems.md) it precisely there in the world.</span></span> <span data-ttu-id="3b72d-130">逐步解決該全像圖時，它會顯示相對於您的世界穩定。</span><span class="sxs-lookup"><span data-stu-id="3b72d-130">As you walk around that hologram, it will appear stable relative to the world around you.</span></span> <span data-ttu-id="3b72d-131">如果您使用[空間的錨點](coordinate-systems.md#spatial-anchors)釘選穩固地以全球該物件，系統可以甚至記住離開的地方它時您後續返回頁面。</span><span class="sxs-lookup"><span data-stu-id="3b72d-131">If you use a [spatial anchor](coordinate-systems.md#spatial-anchors) to pin that object firmly to the world, the system can even remember where you left it when you come back later.</span></span>

![坐在資料表上的全像攝影版建置 maquette](images/image5-640px.png)

<span data-ttu-id="3b72d-133">某些全像投影請改為遵循使用者。</span><span class="sxs-lookup"><span data-stu-id="3b72d-133">Some holograms follow the user instead.</span></span> <span data-ttu-id="3b72d-134">這些 tag-along 全像投影會將本身相對於使用者，無論他們逐步解說的位置。</span><span class="sxs-lookup"><span data-stu-id="3b72d-134">These tag-along holograms position themselves relative to the user, no matter where they walk.</span></span> <span data-ttu-id="3b72d-135">您甚至可以選擇來與您全像一段時間，並再將它放在塗鴉牆上一旦您取得另一個房間內。</span><span class="sxs-lookup"><span data-stu-id="3b72d-135">You may even choose to bring a hologram with you for a while and then place it on the wall once you get to another room.</span></span>

<span data-ttu-id="3b72d-136">**最佳作法**</span><span class="sxs-lookup"><span data-stu-id="3b72d-136">**Best practices**</span></span>
* <span data-ttu-id="3b72d-137">某些情況下可能會要求全像投影，維持輕鬆探索或可見的體驗。</span><span class="sxs-lookup"><span data-stu-id="3b72d-137">Some scenarios may demand that holograms remain easily discoverable or visible throughout the experience.</span></span> <span data-ttu-id="3b72d-138">有兩種高層級的方法，以這種定位。</span><span class="sxs-lookup"><span data-stu-id="3b72d-138">There are two high-level approaches to this kind of positioning.</span></span> <span data-ttu-id="3b72d-139">暫且把他們 **「 顯示鎖定 」** 並 **「 主體鎖定 」**。</span><span class="sxs-lookup"><span data-stu-id="3b72d-139">Let's call them **"display-locked"** and **"body-locked"**.</span></span>
   * <span data-ttu-id="3b72d-140">顯示鎖定的內容是依位置來建立 「 鎖定 」 裝置螢幕。</span><span class="sxs-lookup"><span data-stu-id="3b72d-140">Display-locked content is positionally "locked" to the device display.</span></span> <span data-ttu-id="3b72d-141">弔詭的多種原因所造成，包括 「 clingyness 」，讓許多使用者受挫非自然掌控，且想要"shake 它。 」</span><span class="sxs-lookup"><span data-stu-id="3b72d-141">This is tricky for a number of reasons, including an unnatural feeling of "clingyness" that makes many users frustrated and wanting to "shake it off."</span></span> <span data-ttu-id="3b72d-142">一般情況下，許多設計工具中發現最好避免顯示鎖定的內容。</span><span class="sxs-lookup"><span data-stu-id="3b72d-142">In general, many designers have found it better to avoid display-locking content.</span></span>
   * <span data-ttu-id="3b72d-143">主體鎖定方法是更 forgivable。</span><span class="sxs-lookup"><span data-stu-id="3b72d-143">The body-locked approach is far more forgivable.</span></span> <span data-ttu-id="3b72d-144">主體鎖定時，雷射行動網卡的使用者主體或視線向量，但位於使用者周圍的 3d 空間中。</span><span class="sxs-lookup"><span data-stu-id="3b72d-144">Body-locking is when a hologram is tethered to the user's body or gaze vector, but is positioned in 3d space around the user.</span></span> <span data-ttu-id="3b72d-145">許多體驗已採用其中全像 「 遵循 」 使用者視線，可讓使用者旋轉其主體，並移動空間，而不會遺失全像本文鎖定的行為。</span><span class="sxs-lookup"><span data-stu-id="3b72d-145">Many experiences have adopted a body-locking behavior where the hologram "follows" the users gaze, which allows the user to rotate their body and move through space without losing the hologram.</span></span> <span data-ttu-id="3b72d-146">併入延遲有助於感覺更自然的全像移動。</span><span class="sxs-lookup"><span data-stu-id="3b72d-146">Incorporating a delay helps the hologram movement feel more natural.</span></span> <span data-ttu-id="3b72d-147">比方說，一些核心 Windows 全像攝影版作業系統的 UI 會在接下來溫和，類似彈性的延遲時間的使用者的視線，當使用者開啟腦袋內文-鎖定使用變化。</span><span class="sxs-lookup"><span data-stu-id="3b72d-147">For example, some core UI of the Windows Holographic OS uses a variation on body-locking that follows the user's gaze with a gentle, elastic-like delay while the user turns their head.</span></span>
* <span data-ttu-id="3b72d-148">在置入全像舒適的檢視距離通常約 1-2 俖籇標頭。</span><span class="sxs-lookup"><span data-stu-id="3b72d-148">Place the hologram at a comfortable viewing distance typically about 1-2 meters away from the head.</span></span>
* <span data-ttu-id="3b72d-149">提供必須持續在全像攝影版的框架內，或請考慮當使用者變更他們的觀點來看，以動畫顯示您的內容，顯示的某一端的項目數量漂移。</span><span class="sxs-lookup"><span data-stu-id="3b72d-149">Provide an amount of drift for elements that must be continually in the holographic frame, or consider animating your content to one side of the display when the user changes their point of view.</span></span>

<span data-ttu-id="3b72d-150">**全像投影置於 「 最佳 」 區域-1.25 m 和 5 分鐘之間**</span><span class="sxs-lookup"><span data-stu-id="3b72d-150">**Place holograms in the optimal zone - between 1.25m and 5m**</span></span>

<span data-ttu-id="3b72d-151">兩個計量是最適合的並體驗將會降低您從一個計量的取得越快。</span><span class="sxs-lookup"><span data-stu-id="3b72d-151">Two meters is the most optimal, and the experience will degrade the closer you get from one meter.</span></span> <span data-ttu-id="3b72d-152">越重要比一個計量表距離，定期移動防禦全像投影是更有可能是比 「 定態全像投影有問題。</span><span class="sxs-lookup"><span data-stu-id="3b72d-152">At distances nearer than one meter, holograms that regularly move in depth are more likely to be problematic than stationary holograms.</span></span> <span data-ttu-id="3b72d-153">建議您依正常程序裁剪或淡出您的內容，當它取得太接近來為未 jar 使用者到未預期的體驗。</span><span class="sxs-lookup"><span data-stu-id="3b72d-153">Consider gracefully clipping or fading out your content when it gets too close so as not to jar the user into an unexpected experience.</span></span>

![對於將使用者從全像投影的最佳距離。](images/distanceguiderendering-640px.png)

## <a name="a-hologram-interacts-with-you-and-your-world"></a><span data-ttu-id="3b72d-155">您和您的世界互動全像</span><span class="sxs-lookup"><span data-stu-id="3b72d-155">A hologram interacts with you and your world</span></span>

<span data-ttu-id="3b72d-156">全像投影不只需光線和音效;它們也是世界的您中作用中的部份。</span><span class="sxs-lookup"><span data-stu-id="3b72d-156">Holograms aren't only about light and sound; they're also an active part of your world.</span></span> <span data-ttu-id="3b72d-157">在全像和您用手，筆勢的視線雷射可以開始依照您。</span><span class="sxs-lookup"><span data-stu-id="3b72d-157">Gaze at a hologram and gesture with your hand, and a hologram can start to follow you.</span></span> <span data-ttu-id="3b72d-158">以全像圖中，所發出的語音命令，它可以回覆。</span><span class="sxs-lookup"><span data-stu-id="3b72d-158">Give a voice command to a hologram, and it can reply.</span></span>

![納入實際 motorcycle 主體上的全像攝影版 motorcycle 設計](images/image8-640px.png)

<span data-ttu-id="3b72d-160">全像投影可讓個人在其他地方不可行的互動。</span><span class="sxs-lookup"><span data-stu-id="3b72d-160">Holograms enable personal interactions that aren't possible elsewhere.</span></span> <span data-ttu-id="3b72d-161">由於 HoloLens 知道其所在的世界中，全像攝影版的字元可以查看您直接眼睛逐步房間周圍。</span><span class="sxs-lookup"><span data-stu-id="3b72d-161">Because the HoloLens knows where it is in the world, a holographic character can look you directly in the eyes as you walk around the room.</span></span>

<span data-ttu-id="3b72d-162">雷射也可以與周圍環境互動。</span><span class="sxs-lookup"><span data-stu-id="3b72d-162">A hologram can also interact with your surroundings.</span></span> <span data-ttu-id="3b72d-163">例如，您可以放置全像攝影版的彈跳球，上述資料表。</span><span class="sxs-lookup"><span data-stu-id="3b72d-163">For example, you can place a holographic bouncing ball above a table.</span></span> <span data-ttu-id="3b72d-164">然後，再[空中點選](gestures.md#air-tap)，觀看球彈，並讓音效，當它叫用的資料表。</span><span class="sxs-lookup"><span data-stu-id="3b72d-164">Then, with an [air tap](gestures.md#air-tap), watch the ball bounce and make sound when it hits the table.</span></span>

<span data-ttu-id="3b72d-165">真實世界物件也可以阻擋全像投影。</span><span class="sxs-lookup"><span data-stu-id="3b72d-165">Holograms can also be occluded by real-world objects.</span></span> <span data-ttu-id="3b72d-166">例如，透過門後，請在牆上、 您使其看不可能會逐步引導全像攝影版的字元。</span><span class="sxs-lookup"><span data-stu-id="3b72d-166">For example, a holographic character might walk through a door and behind a wall, out of your sight.</span></span>

<span data-ttu-id="3b72d-167">**整合全像投影和真實世界的秘訣**</span><span class="sxs-lookup"><span data-stu-id="3b72d-167">**Tips for integrating holograms and the real world**</span></span>
* <span data-ttu-id="3b72d-168">對齊重力規則可讓全像投影，與相關的工作變得更容易且更可信。</span><span class="sxs-lookup"><span data-stu-id="3b72d-168">Aligning to gravitational rules makes holograms easier to relate to and more believable.</span></span> <span data-ttu-id="3b72d-169">例如：將全像攝影版的 dog 放在地上 & 花瓶資料表上的，而不是讓它們在空間中浮動。</span><span class="sxs-lookup"><span data-stu-id="3b72d-169">eg: Place a holographic dog on the ground & a vase on the table rather than have them floating in space.</span></span>
* <span data-ttu-id="3b72d-170">許多設計工具中發現，甚至更 believably 可以藉由建立全像正坐在介面上的 「 負值陰影 」 整合全像投影。</span><span class="sxs-lookup"><span data-stu-id="3b72d-170">Many designers have found that they can even more believably integrate holograms by creating a "negative shadow" on the surface that the hologram is sitting on.</span></span> <span data-ttu-id="3b72d-171">他們這麼做，藉由建立周圍全像地面上的虛光暈，並再減去 「 影子 」 從光暈。</span><span class="sxs-lookup"><span data-stu-id="3b72d-171">They do this by creating a soft glow on the ground around the hologram and then subtracting the "shadow" from the glow.</span></span> <span data-ttu-id="3b72d-172">軟光暈整合在現實世界中光線和陰影 grounds 全像在環境中。</span><span class="sxs-lookup"><span data-stu-id="3b72d-172">The soft glow integrates with the light from the real world and the shadow grounds the hologram in the environment.</span></span>

## <a name="a-hologram-is-whatever-you-dream-up"></a><span data-ttu-id="3b72d-173">雷射是您一起完成的任何內容</span><span class="sxs-lookup"><span data-stu-id="3b72d-173">A hologram is whatever you dream up</span></span>

<span data-ttu-id="3b72d-174">身為全像攝影版的開發人員，您必須能夠中斷您的創意出 2D 螢幕並進入您的世界。</span><span class="sxs-lookup"><span data-stu-id="3b72d-174">As a holographic developer, you have the power to break your creativity out of 2D screens and into the world around you.</span></span> <span data-ttu-id="3b72d-175">項目有哪些*您*建置？</span><span class="sxs-lookup"><span data-stu-id="3b72d-175">What will *you* build?</span></span>

![在客廳中全像攝影版的虛數世界](images/designoverview.jpg)

## <a name="see-also"></a><span data-ttu-id="3b72d-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b72d-177">See also</span></span>
* [<span data-ttu-id="3b72d-178">空間的音效</span><span class="sxs-lookup"><span data-stu-id="3b72d-178">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="3b72d-179">色彩、 光線和材質</span><span class="sxs-lookup"><span data-stu-id="3b72d-179">Color, light and materials</span></span>](color,-light-and-materials.md)
