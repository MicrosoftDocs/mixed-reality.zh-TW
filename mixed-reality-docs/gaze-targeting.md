---
title: 為目標的視線
description: 使用者能夠針對他們想要進行互動，無論輸入強制回應性的項目所建立的所有互動。
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 混合實境、 視線、 視線目標，就會有互動，設計
ms.openlocfilehash: 1ac4f06208a7574fced0a7e27e93469ec93bf6e0
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873918"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="4bf1d-104">視線和詳述</span><span class="sxs-lookup"><span data-stu-id="4bf1d-104">Gaze and dwell</span></span>
<span data-ttu-id="4bf1d-105">有許多不同的方式，以確認_認可_例如結合使用的視線_語音_或_交給筆勢_。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-105">There are lots of different ways to confirm a _commit_ such as combining gaze with _voice_ or _hand gestures_.</span></span>
<span data-ttu-id="4bf1d-106">有幾個使用者案例，使用者的手可能忙碌中或無法追蹤 （例如過大的韌手套的 factory 工作者）。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-106">There are several user scenarios though, in which users' hands may either be busy or cannot be tracked (e.g., factory workers with oversized heavy duty gloves).</span></span> <span data-ttu-id="4bf1d-107">語音輸入也不可能因為使用者喜好設定、 社交內容或吵雜的環境。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-107">Voice input may also not be available due to user preferences, social context or loud environments.</span></span>
<span data-ttu-id="4bf1d-108">另一個選項來執行做為後援的解決方案_認可_只是保留盯著我們所謂的 UI 項目_探討_。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-108">As a fallback solution another option to perform a _commit_ is simply to keep staring at a UI element which we refer to as _dwell_.</span></span>
<span data-ttu-id="4bf1d-109">A_探討_可進行與標頭或眼睛視線。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-109">A _dwell_ can be performed with either head or eye gaze.</span></span> <span data-ttu-id="4bf1d-110">這個概念很簡單，而且可分成下列階段細分：</span><span class="sxs-lookup"><span data-stu-id="4bf1d-110">The idea is simple and can be broken down in the following phases:</span></span> 
1. <span data-ttu-id="4bf1d-111">使用者啟動 gazing 在全像攝影版的按鈕</span><span class="sxs-lookup"><span data-stu-id="4bf1d-111">User starts gazing at a holographic button</span></span>

2. <span data-ttu-id="4bf1d-112">在簡短的開始延遲 （例如，150 毫秒） 後會啟動一些視覺化回饋動畫。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-112">After a brief onset delay (e.g., 150 ms) some visual feedback animation is started.</span></span> <span data-ttu-id="4bf1d-113">開始延遲用來避免讓使用者以立即彈出的意見反應的時間。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-113">The onset delay is used to avoid overwhelming the user by immediately popping up feedback all the time.</span></span>
    - <span data-ttu-id="4bf1d-114">針對_眼睛視線_，我們建議下列的視覺效果的設計會探討意見反應：</span><span class="sxs-lookup"><span data-stu-id="4bf1d-114">For _eye gaze_, we recommend the following for the design of the visual dwell feedback:</span></span>
      - <span data-ttu-id="4bf1d-115">**Blend 它**:順暢 blend 中從幾乎沒有顯示在第一次到完全不透明的意見反應。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-115">**Blend it**: Smoothly blend in the feedback from barely visible at first to fully opaque.</span></span> <span data-ttu-id="4bf1d-116">這讓意見反應，較少的轉移和 overwhleming，而完全配合系統有使用者真正想要使用此按鈕的信心。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-116">This makes the feedback less distracting and overwhleming and nicely aligns with the confidence that the system has that the user really wants to engage with this button.</span></span>
      - <span data-ttu-id="4bf1d-117">**將它提取**:非可減少的大小，並移往目標，納入使用者視覺化注意 center，請建立視覺化回饋。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-117">**Pull it in**: Create a visual feedback than decreases in size and moves towards the center of the target, pulling in the user's visual attention.</span></span> 

3. <span data-ttu-id="4bf1d-118">預先定義的詳述持續時間 （例如 800 毫秒） 之後, 詳述完成，並觸發相關聯的事件。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-118">After a pre-defined dwell duration (e.g., 800 ms), the dwell completes and an associated event is triggered.</span></span>
    - <span data-ttu-id="4bf1d-119">提供一些完成聽覺或視覺化回饋真的將常用的項目現在已選取。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-119">Provide some finalizing auditory or visual feedback to really bring home that the item got selected now.</span></span>

![探討狀態](images/eyes_dwellstate_recommendation.png)


# <a name="gaze-targeting"></a><span data-ttu-id="4bf1d-121">為目標的視線</span><span class="sxs-lookup"><span data-stu-id="4bf1d-121">Gaze targeting</span></span>

<span data-ttu-id="4bf1d-122">使用者能夠針對他們想要進行互動，無論輸入強制回應性的項目所建立的所有互動。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-122">All interactions are built upon the ability of a user to target the element they want to interact with, regardless of the input modality.</span></span> <span data-ttu-id="4bf1d-123">在 Windows Mixed Reality，這通常是使用使用者的視線。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-123">In Windows Mixed Reality, this is generally done using the user's gaze.</span></span>

<span data-ttu-id="4bf1d-124">若要啟用的使用者，才能順利運作的體驗，系統的導出了解使用者的意圖，以及使用者的實際的意圖，必須為儘可能密集地對齊。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-124">To enable a user to work with an experience successfully, the system's calculated understanding of a user's intent, and the user's actual intent, must align as closely as possible.</span></span> <span data-ttu-id="4bf1d-125">程度系統解譯使用者的預定的動作正確，增加滿意度和效能改善。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-125">To the degree that the system interprets the user's intended actions correctly, satisfaction increases and performance improves.</span></span>

## <a name="device-support"></a><span data-ttu-id="4bf1d-126">裝置支援</span><span class="sxs-lookup"><span data-stu-id="4bf1d-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="4bf1d-127">功能</span><span class="sxs-lookup"><span data-stu-id="4bf1d-127">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="4bf1d-128"><a href="hololens-hardware-details.md">HoloLens （第 1 代）</a></span><span class="sxs-lookup"><span data-stu-id="4bf1d-128"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="4bf1d-129">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4bf1d-129">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="4bf1d-130"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="4bf1d-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="4bf1d-131">為目標的視線</span><span class="sxs-lookup"><span data-stu-id="4bf1d-131">Gaze targeting</span></span></td><td style="text-align: center;"> <span data-ttu-id="4bf1d-132">✔️</span><span class="sxs-lookup"><span data-stu-id="4bf1d-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="4bf1d-133">✔️</span><span class="sxs-lookup"><span data-stu-id="4bf1d-133">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="4bf1d-134">✔️</span><span class="sxs-lookup"><span data-stu-id="4bf1d-134">✔️</span></span> </td>
</tr><tr>
<td> <span data-ttu-id="4bf1d-135">眼睛目標</span><span class="sxs-lookup"><span data-stu-id="4bf1d-135">Eye targeting</span></span></td><td style="text-align: center;"></td><td style="text-align: center;"> <span data-ttu-id="4bf1d-136">✔️</span><span class="sxs-lookup"><span data-stu-id="4bf1d-136">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="4bf1d-137">HoloLens 2 的特定的詳細指引[即將推出](index.md)。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-137">More guidance specific to HoloLens 2 [coming soon](index.md).</span></span>

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="4bf1d-138">目標大小和意見反應</span><span class="sxs-lookup"><span data-stu-id="4bf1d-138">Target sizing and feedback</span></span>

<span data-ttu-id="4bf1d-139">視線向量可能會重複用來順利的目標，但通常最適合 gross 目標 （取得較大目標）。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-139">The gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting (acquiring somewhat larger targets).</span></span> <span data-ttu-id="4bf1d-140">1 到 1.5 度的最小目標大小應該在大部分情況下，允許成功的使用者動作，但目標 3 度通常可讓較快的速度。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-140">Minimum target sizes of 1 to 1.5 degrees should allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="4bf1d-141">請注意，使用者目標實際上是 3D 元素--即使 2D 區域的大小任何投影面向它們應該將目標設為區域。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-141">Note that the size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="4bf1d-142">提供一些主要的項目是 「 作用中 」 （該使用者以其為目標） 的提示會非常有用-這可能包括經過處理，例如顯示 「 暫留 」 效果、 音效反白顯示或需按幾下，或清除元素的資料指標的對齊方式。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-142">Providing some salient cue that an element is "active" (that the user is targeting it) is extremely helpful - this can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="4bf1d-143">![2 個計量表距離的最佳目標大小](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4bf1d-143">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="4bf1d-144">*2 個計量表距離的最佳目標大小*</span><span class="sxs-lookup"><span data-stu-id="4bf1d-144">*Optimal target size at 2 meter distance*</span></span>

<span data-ttu-id="4bf1d-145">![舉例來說，反白顯示的視線目標的物件](images/gazetargeting-highlighting-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4bf1d-145">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-640px.jpg)</span></span><br>
<span data-ttu-id="4bf1d-146">*舉例來說，反白顯示的視線目標的物件*</span><span class="sxs-lookup"><span data-stu-id="4bf1d-146">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="4bf1d-147">目標位置</span><span class="sxs-lookup"><span data-stu-id="4bf1d-147">Target placement</span></span>

<span data-ttu-id="4bf1d-148">使用者將通常無法找到位於很高或極低的 UI 項目中的視角，將焦點放在周圍 （通常大約是眼睛層級） 及其主要焦點區域注意大多。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-148">Users will often fail to find UI elements that are positioned very high or very low in their field of view, focusing most of their attention on areas around their main focus (usually roughly eye level).</span></span> <span data-ttu-id="4bf1d-149">將大部分的目標放在一些合理的頻外，周圍視覺層級可以幫助。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-149">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="4bf1d-150">指定使用者傾向專注於相對較小視覺效果區域 （願景 attentional 圓錐圖是大約 10 度），隨時分組的 UI 項目程度它們在概念上相關可以利用注意鏈結的行為項目到項目以使用者身分將其視線通過區域。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-150">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree that they're related conceptually can leverage attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="4bf1d-151">在設計 UI 時，請記住視野 HoloLens 和沈浸式耳機之間的潛在大變異。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-151">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="4bf1d-152">![舉例而言，更輕鬆的視線 Galaxy 檔案總管中的目標群組的 UI 項目](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4bf1d-152">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="4bf1d-153">*舉例而言，更輕鬆的視線 Galaxy 檔案總管中的目標群組的 UI 項目*</span><span class="sxs-lookup"><span data-stu-id="4bf1d-153">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="4bf1d-154">改善目標的行為</span><span class="sxs-lookup"><span data-stu-id="4bf1d-154">Improving targeting behaviors</span></span>

<span data-ttu-id="4bf1d-155">如果使用者意圖為目標的項目可以決定 （或接近近似），它可以接受"near miss"會嘗試在互動，如同它們已正確目標很有幫助。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-155">If user intent to target something can be determined (or approximated closely), it can be very helpful to accept "near miss" attempts at interaction as though they were targeted correctly.</span></span> <span data-ttu-id="4bf1d-156">有少數幾個成功的方法，可以將其納入混合的實境體驗：</span><span class="sxs-lookup"><span data-stu-id="4bf1d-156">There are a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="gaze-stabilization-gravity-wells"></a><span data-ttu-id="4bf1d-157">視線穩定 (「 重力 wells")</span><span class="sxs-lookup"><span data-stu-id="4bf1d-157">Gaze stabilization ("gravity wells")</span></span>

<span data-ttu-id="4bf1d-158">這應該開啟大部分/所有的時間。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-158">This should be turned on most/all of the time.</span></span> <span data-ttu-id="4bf1d-159">這項技術會移除使用者可能有自然的前端/頸部做法。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-159">This technique removes the natural head/neck jitters that users may have.</span></span> <span data-ttu-id="4bf1d-160">也因為尋找/談到的行為而移動。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-160">Also movement due to looking/speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="4bf1d-161">最接近的連結演算法</span><span class="sxs-lookup"><span data-stu-id="4bf1d-161">Closest link algorithms</span></span>

<span data-ttu-id="4bf1d-162">這些最適合疏鬆的互動式內容區域中。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-162">These work best in areas with sparse interactive content.</span></span> <span data-ttu-id="4bf1d-163">如果有較高的機率，您可以決定使用者已嘗試進行互動，您可以只假設某些層級的意圖來補充其目標的能力。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-163">If there is a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by simply assuming some level of intent.</span></span>

### <a name="backdatingpostdating-actions"></a><span data-ttu-id="4bf1d-164">Backdating/postdating 動作</span><span class="sxs-lookup"><span data-stu-id="4bf1d-164">Backdating/postdating actions</span></span>

<span data-ttu-id="4bf1d-165">這項機制可用於需要速度的工作。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-165">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="4bf1d-166">當使用者是透過一系列的目標/啟用調動的速度移動時，它可用來假設某些意圖，並允許*錯過步驟*目標使用者是否具有焦點稍微之前或之後點選 （稍微採取動作50 毫秒前/後為有效的早期測試）。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-166">When a user is moving through a series of targeting/activation maneuvers at speed, it can be useful to assume some intent and allow *missed steps* to act upon targets which the user had in focus slightly before or slightly after the tap (50ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="4bf1d-167">平滑處理</span><span class="sxs-lookup"><span data-stu-id="4bf1d-167">Smoothing</span></span>

<span data-ttu-id="4bf1d-168">這項機制可用於路徑移動，減少些許抖動/搖晃因為自然磁頭移動特性。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-168">This mechanism is useful for pathing movements, reducing the slight jitter/wobble due to natural head movement characteristics.</span></span> <span data-ttu-id="4bf1d-169">當透過 smooth 大小/距離的移動，而不是經過一段時間的路徑動作平滑處理</span><span class="sxs-lookup"><span data-stu-id="4bf1d-169">When smoothing over pathing motions, smooth by size/distance of movements rather than over time</span></span>

### <a name="magnetism"></a><span data-ttu-id="4bf1d-170">磁場</span><span class="sxs-lookup"><span data-stu-id="4bf1d-170">Magnetism</span></span>

<span data-ttu-id="4bf1d-171">這項機制可以視為 「 最接近連結 」 演算法-繪製為目標，向資料指標，或 （不論明顯與否），只需增加 hitboxes 的較通用版本使用者達到可能的目標，使用互動式的版面配置，以一些知識使用者意圖更好的方法。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-171">This mechanism can be thought of as a more general version of "Closest link" algorithms - drawing a cursor toward a target, or simply increasing hitboxes (whether visibly or not) as users approach likely targets, using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="4bf1d-172">這可以是特別強大，小型的目標。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-172">This can be particularly powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="4bf1d-173">焦點黏著度</span><span class="sxs-lookup"><span data-stu-id="4bf1d-173">Focus stickiness</span></span>

<span data-ttu-id="4bf1d-174">當判斷哪些焦點提供給互動項目附近，會提供目前焦點的項目偏差。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-174">When determining which nearby interactive elements to give focus to, provide a bias to the element that is currently focused.</span></span> <span data-ttu-id="4bf1d-175">這有助於減少不穩定的焦點時具有自然雜訊的兩個項目之間的中間點在浮動切換行為。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-175">This will help reduce erratic focus switching behaviours when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="4bf1d-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bf1d-176">See also</span></span>
* [<span data-ttu-id="4bf1d-177">筆勢</span><span class="sxs-lookup"><span data-stu-id="4bf1d-177">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="4bf1d-178">語音設計</span><span class="sxs-lookup"><span data-stu-id="4bf1d-178">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="4bf1d-179">游標</span><span class="sxs-lookup"><span data-stu-id="4bf1d-179">Cursors</span></span>](cursors.md)
