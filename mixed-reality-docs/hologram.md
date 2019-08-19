---
title: 什麼是全像投影？
description: HoloLens 可讓您觀賞3d 的全息影像, 並與世界各地出現的光線和音效物件進行互動。
author: beaufolsom
ms.author: befolsom
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, 全息影像, 設計, 互動
ms.openlocfilehash: 714b08db23aa641252291aebe89fa3059c209a6f
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829777"
---
# <a name="what-is-a-hologram"></a><span data-ttu-id="1e9ac-104">什麼是全像投影？</span><span class="sxs-lookup"><span data-stu-id="1e9ac-104">What is a hologram?</span></span>

<span data-ttu-id="1e9ac-105">HoloLens 可讓您建立在世界各地顯示的**全息影像**、光線和音效的物件, 就像是真正的物件一樣。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-105">HoloLens lets you create **holograms**, objects made of light and sound that appear in the world around you, just as if they were real objects.</span></span> <span data-ttu-id="1e9ac-106">全息影像會回應您的[注視](gaze.md)、[手勢](gestures.md)和[語音命令](voice-input.md), 並可與您的[真實世界表面](spatial-mapping.md)互動。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-106">Holograms respond to your [gaze](gaze.md), [gestures](gestures.md) and [voice commands](voice-input.md), and can interact with [real-world surfaces](spatial-mapping.md) around you.</span></span> <span data-ttu-id="1e9ac-107">透過全息影像, 您可以建立屬於您世界的數位物件。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-107">With holograms, you can create digital objects that are part of your world.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/MVXH5V8MVQo]

## <a name="device-support"></a><span data-ttu-id="1e9ac-108">裝置支援</span><span class="sxs-lookup"><span data-stu-id="1e9ac-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1e9ac-109"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="1e9ac-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="1e9ac-110"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="1e9ac-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="1e9ac-111"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="1e9ac-111"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="1e9ac-112"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="1e9ac-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1e9ac-113">全息</span><span class="sxs-lookup"><span data-stu-id="1e9ac-113">Holograms</span></span></td>
        <td><span data-ttu-id="1e9ac-114">✔️</span><span class="sxs-lookup"><span data-stu-id="1e9ac-114">✔️</span></span></td>
        <td><span data-ttu-id="1e9ac-115">✔️</span><span class="sxs-lookup"><span data-stu-id="1e9ac-115">✔️</span></span></td>
        <td><span data-ttu-id="1e9ac-116">❌</span><span class="sxs-lookup"><span data-stu-id="1e9ac-116">❌</span></span></td>
    </tr>
</table>

## <a name="a-hologram-is-made-of-light-and-sound"></a><span data-ttu-id="1e9ac-117">全像投影是由光線和音效所組成</span><span class="sxs-lookup"><span data-stu-id="1e9ac-117">A hologram is made of light and sound</span></span>

<span data-ttu-id="1e9ac-118">HoloLens[呈現](rendering.md)的全息影像會直接出現在使用者眼睛前方的全像攝影畫面中。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-118">The holograms that HoloLens [renders](rendering.md) appear in the holographic frame directly in front of the user's eyes.</span></span> <span data-ttu-id="1e9ac-119">全像投影將光線新增至您的世界, 這表示您可以從顯示器和周圍查看光線。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-119">Holograms add light to your world, which means that you see both the light from the display and the light from your surroundings.</span></span> <span data-ttu-id="1e9ac-120">HoloLens 並不會從眼睛中去除光線, 因此無法以黑色呈現全息影像。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-120">HoloLens doesn't remove light from your eyes, so holograms can't be rendered with the color black.</span></span> <span data-ttu-id="1e9ac-121">而是以透明的方式顯示黑色內容。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-121">Instead, black content appears as transparent.</span></span>

<span data-ttu-id="1e9ac-122">全息影像可以有許多不同的外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-122">Holograms can have many different appearances and behaviors.</span></span> <span data-ttu-id="1e9ac-123">有些是逼真且穩固的, 有些則是編排卡通和 ethereal。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-123">Some are realistic and solid, and others are cartoonish and ethereal.</span></span> <span data-ttu-id="1e9ac-124">全息影像可以反白顯示您的環境中的功能, 而且可以是應用程式使用者介面中的元素。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-124">Holograms can highlight features in your surroundings, and they can be elements in your app's user interface.</span></span>

![全像地面的全像攝影狗](images/fang3-640px.jpg)

<span data-ttu-id="1e9ac-126">全像投影也可以製作[音效](spatial-sound.md), 這看起來就像您的環境中的特定位置。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-126">Holograms can also make [sounds](spatial-sound.md), which will appear to come from a specific place in your surroundings.</span></span> <span data-ttu-id="1e9ac-127">在 HoloLens 上, 音效來自于位於您的耳的兩個喇叭, 而不會加以涵蓋。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-127">On HoloLens, sound comes from two speakers that are located directly above your ears, without covering them.</span></span> <span data-ttu-id="1e9ac-128">與顯示器類似, 喇叭是加總的, 引進新的音效, 而不會封鎖環境中的音效。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-128">Similar to the displays, the speakers are additive, introducing new sounds without blocking the sounds from your environment.</span></span>

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a><span data-ttu-id="1e9ac-129">您可以將全息全像位置放在世界或標籤中</span><span class="sxs-lookup"><span data-stu-id="1e9ac-129">A hologram can be placed in the world or tag along with you</span></span>

<span data-ttu-id="1e9ac-130">當您有想要的全像投影的特定位置時, 可以將它精確[放](coordinate-systems.md)在世界上。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-130">When you have a particular location where you want a hologram, you can [place](coordinate-systems.md) it precisely there in the world.</span></span> <span data-ttu-id="1e9ac-131">當您流覽該全像投影時, 其外觀會相對於您周圍的世界。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-131">As you walk around that hologram, it will appear stable relative to the world around you.</span></span> <span data-ttu-id="1e9ac-132">如果您使用[空間錨點](coordinate-systems.md#spatial-anchors), 將該物件牢固地釘選到世界, 那麼當您稍後返回時, 系統可能會記住您剩下的地方。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-132">If you use a [spatial anchor](coordinate-systems.md#spatial-anchors) to pin that object firmly to the world, the system can even remember where you left it when you come back later.</span></span>

![Maquette 坐在桌上的全像大樓](images/image5-640px.png)

<span data-ttu-id="1e9ac-134">某些全息影像會改為遵循使用者。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-134">Some holograms follow the user instead.</span></span> <span data-ttu-id="1e9ac-135">這些加上標籤的全息影像位置本身相對於使用者, 無論他們在哪裡進行。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-135">These tag-along holograms position themselves relative to the user, no matter where they walk.</span></span> <span data-ttu-id="1e9ac-136">您甚至可以選擇帶您一段時間, 然後將它放在牆上, 一旦到達另一個房間。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-136">You may even choose to bring a hologram with you for a while and then place it on the wall once you get to another room.</span></span>

<span data-ttu-id="1e9ac-137">**最佳作法**</span><span class="sxs-lookup"><span data-stu-id="1e9ac-137">**Best practices**</span></span>
* <span data-ttu-id="1e9ac-138">在某些案例中, 您可能會需要在整個過程中, 讓全息影像保持容易探索或可見。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-138">Some scenarios may demand that holograms remain easily discoverable or visible throughout the experience.</span></span> <span data-ttu-id="1e9ac-139">這種定位的高階方法有兩種。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-139">There are two high-level approaches to this kind of positioning.</span></span> <span data-ttu-id="1e9ac-140">讓我們將它們稱為「**顯示鎖定**」和「**主體鎖定**」。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-140">Let's call them **"display-locked"** and **"body-locked"**.</span></span>
   * <span data-ttu-id="1e9ac-141">顯示鎖定的內容會 positionally 「鎖定」到裝置顯示。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-141">Display-locked content is positionally "locked" to the device display.</span></span> <span data-ttu-id="1e9ac-142">這麼做的原因很多, 包括非自然的「clingyness」, 讓許多使用者感到挫折並想要「搖動」。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-142">This is tricky for a number of reasons, including an unnatural feeling of "clingyness" that makes many users frustrated and wanting to "shake it off."</span></span> <span data-ttu-id="1e9ac-143">一般而言, 許多設計人員都發現它更適合用來避免顯示鎖定的內容。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-143">In general, many designers have found it better to avoid display-locking content.</span></span>
   * <span data-ttu-id="1e9ac-144">主體鎖定的方法遠 forgivable。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-144">The body-locked approach is far more forgivable.</span></span> <span data-ttu-id="1e9ac-145">內文鎖定是指將全息行動網卡至使用者的主體或注視向量, 但位於使用者周圍的3d 空間中。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-145">Body-locking is when a hologram is tethered to the user's body or gaze vector, but is positioned in 3d space around the user.</span></span> <span data-ttu-id="1e9ac-146">許多經驗都採用了內文鎖定行為, 其中的全息顯示「跟隨」使用者注視, 這讓使用者可以旋轉其內文, 並在空間中移動而不會遺失全息影像。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-146">Many experiences have adopted a body-locking behavior where the hologram "follows" the users gaze, which allows the user to rotate their body and move through space without losing the hologram.</span></span> <span data-ttu-id="1e9ac-147">結合延遲可協助全息影像的移動更加自然。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-147">Incorporating a delay helps the hologram movement feel more natural.</span></span> <span data-ttu-id="1e9ac-148">例如, Windows 全像攝影作業系統的某些核心 UI, 會使用不同的內文鎖定, 並在使用者輪流時, 在使用者的注視之後, 使用一種非常類似彈性的延遲。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-148">For example, some core UI of the Windows Holographic OS uses a variation on body-locking that follows the user's gaze with a gentle, elastic-like delay while the user turns their head.</span></span>
* <span data-ttu-id="1e9ac-149">將全息影像放在舒適的觀賞距離, 通常是從 head 開始的大約1-2 計量。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-149">Place the hologram at a comfortable viewing distance typically about 1-2 meters away from the head.</span></span>
* <span data-ttu-id="1e9ac-150">針對必須持續在全像全像攝影框架中的專案提供漂移, 或考慮在使用者變更其觀點時, 將內容以動畫顯示到畫面的一邊。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-150">Provide an amount of drift for elements that must be continually in the holographic frame, or consider animating your content to one side of the display when the user changes their point of view.</span></span>

<span data-ttu-id="1e9ac-151">**將全息影像放在最佳區域, 介於 1.25 m 和5m 之間**</span><span class="sxs-lookup"><span data-stu-id="1e9ac-151">**Place holograms in the optimal zone - between 1.25m and 5m**</span></span>

<span data-ttu-id="1e9ac-152">兩個計量是最理想的, 而且體驗會降低您從一個計量取得的距離。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-152">Two meters is the most optimal, and the experience will degrade the closer you get from one meter.</span></span> <span data-ttu-id="1e9ac-153">距離接近一計量的位置, 定期移動的全息影像較可能會有問題, 而不是固定的全息影像。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-153">At distances nearer than one meter, holograms that regularly move in depth are more likely to be problematic than stationary holograms.</span></span> <span data-ttu-id="1e9ac-154">當內容太近關閉時, 請考慮適當地裁剪或淡出內容, 以免使用者進入非預期的體驗。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-154">Consider gracefully clipping or fading out your content when it gets too close so as not to jar the user into an unexpected experience.</span></span>

![從使用者處放置全息影像的最佳距離。](images/distanceguiderendering-640px.png)

## <a name="a-hologram-interacts-with-you-and-your-world"></a><span data-ttu-id="1e9ac-156">全息與您和您的世界互動</span><span class="sxs-lookup"><span data-stu-id="1e9ac-156">A hologram interacts with you and your world</span></span>

<span data-ttu-id="1e9ac-157">全像投影不只是亮和音效;它們也是您世界中的活躍部分。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-157">Holograms aren't only about light and sound; they're also an active part of your world.</span></span> <span data-ttu-id="1e9ac-158">以您的手眼看一下全像投影和手勢, 而全息的形狀可以開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-158">Gaze at a hologram and gesture with your hand, and a hologram can start to follow you.</span></span> <span data-ttu-id="1e9ac-159">將語音命令提供給全息影像, 它可以回復。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-159">Give a voice command to a hologram, and it can reply.</span></span>

![全像現實生活 motorcycle 的 motorcycle 設計](images/image8-640px.png)

<span data-ttu-id="1e9ac-161">全像投影可以讓個人互動不可能發生在其他地方。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-161">Holograms enable personal interactions that aren't possible elsewhere.</span></span> <span data-ttu-id="1e9ac-162">因為 HoloLens 知道它在世界中的位置, 所以在您離開房間時, 全像攝影的字元可以直接在眼睛中找到。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-162">Because the HoloLens knows where it is in the world, a holographic character can look you directly in the eyes as you walk around the room.</span></span>

<span data-ttu-id="1e9ac-163">全息影像也可以與您的環境互動。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-163">A hologram can also interact with your surroundings.</span></span> <span data-ttu-id="1e9ac-164">例如, 您可以將全像跳動的球放在資料表上方。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-164">For example, you can place a holographic bouncing ball above a table.</span></span> <span data-ttu-id="1e9ac-165">然後, 使用 [點一下], 監看球彈, 並在[觸](gestures.md#air-tap)達資料表時發出音效。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-165">Then, with an [air tap](gestures.md#air-tap), watch the ball bounce and make sound when it hits the table.</span></span>

<span data-ttu-id="1e9ac-166">影像也可以由真實世界的物件 pixels occluded。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-166">Holograms can also be occluded by real-world objects.</span></span> <span data-ttu-id="1e9ac-167">例如, 全像攝影字元可能會逐步解說門, 而不是您所看到的背景。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-167">For example, a holographic character might walk through a door and behind a wall, out of your sight.</span></span>

<span data-ttu-id="1e9ac-168">**整合全息和真實世界的秘訣**</span><span class="sxs-lookup"><span data-stu-id="1e9ac-168">**Tips for integrating holograms and the real world**</span></span>
* <span data-ttu-id="1e9ac-169">對應到 gravitational 規則可讓您更輕鬆地將全息與可信相關聯。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-169">Aligning to gravitational rules makes holograms easier to relate to and more believable.</span></span> <span data-ttu-id="1e9ac-170">示例將全像攝影狗放在基礎上, & 花瓶在資料表上, 而不是將它們浮動在空間中。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-170">eg: Place a holographic dog on the ground & a vase on the table rather than have them floating in space.</span></span>
* <span data-ttu-id="1e9ac-171">許多設計人員發現, 他們甚至可以在全息桌上的表面上建立「負陰影」, 藉此 believably 整合全息影像。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-171">Many designers have found that they can even more believably integrate holograms by creating a "negative shadow" on the surface that the hologram is sitting on.</span></span> <span data-ttu-id="1e9ac-172">其做法是在全像投影的基礎上建立軟性發光, 然後從發光中減去「陰影」。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-172">They do this by creating a soft glow on the ground around the hologram and then subtracting the "shadow" from the glow.</span></span> <span data-ttu-id="1e9ac-173">軟性發光與真實世界的光線整合, 而陰影遮蔽了環境中的全息型。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-173">The soft glow integrates with the light from the real world and the shadow grounds the hologram in the environment.</span></span>

## <a name="a-hologram-is-whatever-you-dream-up"></a><span data-ttu-id="1e9ac-174">全像您的夢想</span><span class="sxs-lookup"><span data-stu-id="1e9ac-174">A hologram is whatever you dream up</span></span>

<span data-ttu-id="1e9ac-175">身為全像攝影的開發人員, 您可以將您的創意細分成2D 畫面, 並在世界各地。</span><span class="sxs-lookup"><span data-stu-id="1e9ac-175">As a holographic developer, you have the power to break your creativity out of 2D screens and into the world around you.</span></span> <span data-ttu-id="1e9ac-176">*您*會建立什麼？</span><span class="sxs-lookup"><span data-stu-id="1e9ac-176">What will *you* build?</span></span>

![生活空間中的全像虛構世界](images/designoverview.jpg)

## <a name="see-also"></a><span data-ttu-id="1e9ac-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e9ac-178">See also</span></span>
* [<span data-ttu-id="1e9ac-179">空間音效</span><span class="sxs-lookup"><span data-stu-id="1e9ac-179">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="1e9ac-180">色彩、光線和材質</span><span class="sxs-lookup"><span data-stu-id="1e9ac-180">Color, light and materials</span></span>](color,-light-and-materials.md)
