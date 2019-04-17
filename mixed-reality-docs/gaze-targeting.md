---
title: 為目標的視線
description: 使用者能夠針對他們想要進行互動，無論輸入強制回應性的項目所建立的所有互動。
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 混合實境、 視線、 視線目標，就會有互動，設計
ms.openlocfilehash: c3225e27331f8afcda65469eb84fe5470bf6ee8c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592084"
---
# <a name="gaze-targeting"></a><span data-ttu-id="aa8b3-104">為目標的視線</span><span class="sxs-lookup"><span data-stu-id="aa8b3-104">Gaze targeting</span></span>

<span data-ttu-id="aa8b3-105">使用者能夠針對他們想要進行互動，無論輸入強制回應性的項目所建立的所有互動。</span><span class="sxs-lookup"><span data-stu-id="aa8b3-105">All interactions are built upon the ability of a user to target the element they want to interact with, regardless of the input modality.</span></span> <span data-ttu-id="aa8b3-106">在 Windows Mixed Reality，這通常是使用使用者的視線。</span><span class="sxs-lookup"><span data-stu-id="aa8b3-106">In Windows Mixed Reality, this is generally done using the user's gaze.</span></span>

<span data-ttu-id="aa8b3-107">若要啟用的使用者，才能順利運作的體驗，系統的導出了解使用者的意圖，以及使用者的實際的意圖，必須為儘可能密集地對齊。</span><span class="sxs-lookup"><span data-stu-id="aa8b3-107">To enable a user to work with an experience successfully, the system's calculated understanding of a user's intent, and the user's actual intent, must align as closely as possible.</span></span> <span data-ttu-id="aa8b3-108">程度系統解譯使用者的預定的動作正確，增加滿意度和效能改善。</span><span class="sxs-lookup"><span data-stu-id="aa8b3-108">To the degree that the system interprets the user's intended actions correctly, satisfaction increases and performance improves.</span></span>

## <a name="device-support"></a><span data-ttu-id="aa8b3-109">裝置支援</span><span class="sxs-lookup"><span data-stu-id="aa8b3-109">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="aa8b3-110">功能</span><span class="sxs-lookup"><span data-stu-id="aa8b3-110">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="aa8b3-111"><a href="hololens-hardware-details.md">HoloLens （第 1 代）</a></span><span class="sxs-lookup"><span data-stu-id="aa8b3-111"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="aa8b3-112">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="aa8b3-112">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="aa8b3-113"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="aa8b3-113"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="aa8b3-114">為目標的視線</span><span class="sxs-lookup"><span data-stu-id="aa8b3-114">Gaze targeting</span></span></td><td style="text-align: center;"> <span data-ttu-id="aa8b3-115">✔️</span><span class="sxs-lookup"><span data-stu-id="aa8b3-115">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="aa8b3-116">✔️</span><span class="sxs-lookup"><span data-stu-id="aa8b3-116">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="aa8b3-117">✔️</span><span class="sxs-lookup"><span data-stu-id="aa8b3-117">✔️</span></span> </td>
</tr><tr>
<td> <span data-ttu-id="aa8b3-118">眼睛目標</span><span class="sxs-lookup"><span data-stu-id="aa8b3-118">Eye targeting</span></span></td><td style="text-align: center;"></td><td style="text-align: center;"> <span data-ttu-id="aa8b3-119">✔️</span><span class="sxs-lookup"><span data-stu-id="aa8b3-119">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="aa8b3-120">HoloLens 2 的特定的詳細指引[即將推出](index.md#news-and-notes)。</span><span class="sxs-lookup"><span data-stu-id="aa8b3-120">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="aa8b3-121">目標大小和意見反應</span><span class="sxs-lookup"><span data-stu-id="aa8b3-121">Target sizing and feedback</span></span>

<span data-ttu-id="aa8b3-122">視線向量可能會重複用來順利的目標，但通常最適合 gross 目標 （取得較大目標）。</span><span class="sxs-lookup"><span data-stu-id="aa8b3-122">The gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting (acquiring somewhat larger targets).</span></span> <span data-ttu-id="aa8b3-123">1 到 1.5 度的最小目標大小應該在大部分情況下，允許成功的使用者動作，但目標 3 度通常可讓較快的速度。</span><span class="sxs-lookup"><span data-stu-id="aa8b3-123">Minimum target sizes of 1 to 1.5 degrees should allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="aa8b3-124">請注意，使用者目標實際上是 3D 元素--即使 2D 區域的大小任何投影面向它們應該將目標設為區域。</span><span class="sxs-lookup"><span data-stu-id="aa8b3-124">Note that the size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="aa8b3-125">提供一些主要的項目是 「 作用中 」 （該使用者以其為目標） 的提示會非常有用-這可能包括經過處理，例如顯示 「 暫留 」 效果、 音效反白顯示或需按幾下，或清除元素的資料指標的對齊方式。</span><span class="sxs-lookup"><span data-stu-id="aa8b3-125">Providing some salient cue that an element is "active" (that the user is targeting it) is extremely helpful - this can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="aa8b3-126">![2 個計量表距離的最佳目標大小](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="aa8b3-126">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="aa8b3-127">*2 個計量表距離的最佳目標大小*</span><span class="sxs-lookup"><span data-stu-id="aa8b3-127">*Optimal target size at 2 meter distance*</span></span>

<span data-ttu-id="aa8b3-128">![舉例來說，反白顯示的視線目標的物件](images/gazetargeting-highlighting-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="aa8b3-128">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-640px.jpg)</span></span><br>
<span data-ttu-id="aa8b3-129">*舉例來說，反白顯示的視線目標的物件*</span><span class="sxs-lookup"><span data-stu-id="aa8b3-129">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="aa8b3-130">目標位置</span><span class="sxs-lookup"><span data-stu-id="aa8b3-130">Target placement</span></span>

<span data-ttu-id="aa8b3-131">使用者將通常無法找到位於很高或極低的 UI 項目中的視角，將焦點放在周圍 （通常大約是眼睛層級） 及其主要焦點區域注意大多。</span><span class="sxs-lookup"><span data-stu-id="aa8b3-131">Users will often fail to find UI elements that are positioned very high or very low in their field of view, focusing most of their attention on areas around their main focus (usually roughly eye level).</span></span> <span data-ttu-id="aa8b3-132">將大部分的目標放在一些合理的頻外，周圍視覺層級可以幫助。</span><span class="sxs-lookup"><span data-stu-id="aa8b3-132">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="aa8b3-133">指定使用者傾向專注於相對較小視覺效果區域 （願景 attentional 圓錐圖是大約 10 度），隨時分組的 UI 項目程度它們在概念上相關可以利用注意鏈結的行為項目到項目以使用者身分將其視線通過區域。</span><span class="sxs-lookup"><span data-stu-id="aa8b3-133">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree that they're related conceptually can leverage attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="aa8b3-134">在設計 UI 時，請記住視野 HoloLens 和沈浸式耳機之間的潛在大變異。</span><span class="sxs-lookup"><span data-stu-id="aa8b3-134">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="aa8b3-135">![舉例而言，更輕鬆的視線 Galaxy 檔案總管中的目標群組的 UI 項目](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="aa8b3-135">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="aa8b3-136">*舉例而言，更輕鬆的視線 Galaxy 檔案總管中的目標群組的 UI 項目*</span><span class="sxs-lookup"><span data-stu-id="aa8b3-136">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="aa8b3-137">改善目標的行為</span><span class="sxs-lookup"><span data-stu-id="aa8b3-137">Improving targeting behaviors</span></span>

<span data-ttu-id="aa8b3-138">如果使用者意圖為目標的項目可以決定 （或接近近似），它可以接受"near miss"會嘗試在互動，如同它們已正確目標很有幫助。</span><span class="sxs-lookup"><span data-stu-id="aa8b3-138">If user intent to target something can be determined (or approximated closely), it can be very helpful to accept "near miss" attempts at interaction as though they were targeted correctly.</span></span> <span data-ttu-id="aa8b3-139">有少數幾個成功的方法，可以將其納入混合的實境體驗：</span><span class="sxs-lookup"><span data-stu-id="aa8b3-139">There are a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="gaze-stabilization-gravity-wells"></a><span data-ttu-id="aa8b3-140">視線穩定 (「 重力 wells")</span><span class="sxs-lookup"><span data-stu-id="aa8b3-140">Gaze stabilization ("gravity wells")</span></span>

<span data-ttu-id="aa8b3-141">這應該開啟大部分/所有的時間。</span><span class="sxs-lookup"><span data-stu-id="aa8b3-141">This should be turned on most/all of the time.</span></span> <span data-ttu-id="aa8b3-142">這項技術會移除使用者可能有自然的前端/頸部做法。</span><span class="sxs-lookup"><span data-stu-id="aa8b3-142">This technique removes the natural head/neck jitters that users may have.</span></span> <span data-ttu-id="aa8b3-143">也因為尋找/談到的行為而移動。</span><span class="sxs-lookup"><span data-stu-id="aa8b3-143">Also movement due to looking/speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="aa8b3-144">最接近的連結演算法</span><span class="sxs-lookup"><span data-stu-id="aa8b3-144">Closest link algorithms</span></span>

<span data-ttu-id="aa8b3-145">這些最適合疏鬆的互動式內容區域中。</span><span class="sxs-lookup"><span data-stu-id="aa8b3-145">These work best in areas with sparse interactive content.</span></span> <span data-ttu-id="aa8b3-146">如果有較高的機率，您可以決定使用者已嘗試進行互動，您可以只假設某些層級的意圖來補充其目標的能力。</span><span class="sxs-lookup"><span data-stu-id="aa8b3-146">If there is a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by simply assuming some level of intent.</span></span>

### <a name="backdatingpostdating-actions"></a><span data-ttu-id="aa8b3-147">Backdating/postdating 動作</span><span class="sxs-lookup"><span data-stu-id="aa8b3-147">Backdating/postdating actions</span></span>

<span data-ttu-id="aa8b3-148">這項機制可用於需要速度的工作。</span><span class="sxs-lookup"><span data-stu-id="aa8b3-148">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="aa8b3-149">當使用者是透過一系列的目標/啟用調動的速度移動時，它可用來假設某些意圖，並允許*錯過步驟*目標使用者是否具有焦點稍微之前或之後點選 （稍微採取動作50 毫秒前/後為有效的早期測試）。</span><span class="sxs-lookup"><span data-stu-id="aa8b3-149">When a user is moving through a series of targeting/activation maneuvers at speed, it can be useful to assume some intent and allow *missed steps* to act upon targets which the user had in focus slightly before or slightly after the tap (50ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="aa8b3-150">平滑處理</span><span class="sxs-lookup"><span data-stu-id="aa8b3-150">Smoothing</span></span>

<span data-ttu-id="aa8b3-151">這項機制可用於路徑移動，減少些許抖動/搖晃因為自然磁頭移動特性。</span><span class="sxs-lookup"><span data-stu-id="aa8b3-151">This mechanism is useful for pathing movements, reducing the slight jitter/wobble due to natural head movement characteristics.</span></span> <span data-ttu-id="aa8b3-152">當透過 smooth 大小/距離的移動，而不是經過一段時間的路徑動作平滑處理</span><span class="sxs-lookup"><span data-stu-id="aa8b3-152">When smoothing over pathing motions, smooth by size/distance of movements rather than over time</span></span>

### <a name="magnetism"></a><span data-ttu-id="aa8b3-153">磁場</span><span class="sxs-lookup"><span data-stu-id="aa8b3-153">Magnetism</span></span>

<span data-ttu-id="aa8b3-154">這項機制可以視為 「 最接近連結 」 演算法-繪製為目標，向資料指標，或 （不論明顯與否），只需增加 hitboxes 的較通用版本使用者達到可能的目標，使用互動式的版面配置，以一些知識使用者意圖更好的方法。</span><span class="sxs-lookup"><span data-stu-id="aa8b3-154">This mechanism can be thought of as a more general version of "Closest link" algorithms - drawing a cursor toward a target, or simply increasing hitboxes (whether visibly or not) as users approach likely targets, using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="aa8b3-155">這可以是特別強大，小型的目標。</span><span class="sxs-lookup"><span data-stu-id="aa8b3-155">This can be particularly powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="aa8b3-156">焦點黏著度</span><span class="sxs-lookup"><span data-stu-id="aa8b3-156">Focus stickiness</span></span>

<span data-ttu-id="aa8b3-157">當判斷哪些焦點提供給互動項目附近，會提供目前焦點的項目偏差。</span><span class="sxs-lookup"><span data-stu-id="aa8b3-157">When determining which nearby interactive elements to give focus to, provide a bias to the element that is currently focused.</span></span> <span data-ttu-id="aa8b3-158">這有助於減少不穩定的焦點時具有自然雜訊的兩個項目之間的中間點在浮動切換行為。</span><span class="sxs-lookup"><span data-stu-id="aa8b3-158">This will help reduce erratic focus switching behaviours when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="aa8b3-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa8b3-159">See also</span></span>
* [<span data-ttu-id="aa8b3-160">筆勢</span><span class="sxs-lookup"><span data-stu-id="aa8b3-160">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="aa8b3-161">語音設計</span><span class="sxs-lookup"><span data-stu-id="aa8b3-161">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="aa8b3-162">資料指標</span><span class="sxs-lookup"><span data-stu-id="aa8b3-162">Cursors</span></span>](cursors.md)
