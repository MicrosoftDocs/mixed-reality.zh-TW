---
title: 注視目標
description: 無論輸入形式為何，當使用者能夠瞄準他們想要進行互動的元素時，所有互動就已建立。
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Mixed Reality, 注視, 注視目標, 互動, 設計
ms.openlocfilehash: eddc832456b2ba0c6bc8955157d2c8e1a268e893
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829846"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="91ff5-104">注視和停留</span><span class="sxs-lookup"><span data-stu-id="91ff5-104">Gaze and dwell</span></span>
<span data-ttu-id="91ff5-105">有很多不同的方式可以確認_認可_, 例如結合注視與_聲音_或_手手勢_。</span><span class="sxs-lookup"><span data-stu-id="91ff5-105">There are lots of different ways to confirm a _commit_ such as combining gaze with _voice_ or _hand gestures_.</span></span>
<span data-ttu-id="91ff5-106">不過, 有數個使用者案例, 使用者的手中可能忙碌或無法追蹤 (例如, 背景工作的工作者人數過大的沉重)。</span><span class="sxs-lookup"><span data-stu-id="91ff5-106">There are several user scenarios though, in which users' hands may either be busy or cannot be tracked (e.g., factory workers with oversized heavy duty gloves).</span></span> <span data-ttu-id="91ff5-107">語音輸入也可能因為使用者喜好設定、社交內容或更高的環境而無法使用。</span><span class="sxs-lookup"><span data-stu-id="91ff5-107">Voice input may also not be available due to user preferences, social context or loud environments.</span></span>
<span data-ttu-id="91ff5-108">做為回溯解決方案, 另一個執行_認可_的選項, 就是將開始保留在我們稱為_停留_的 UI 元素上。</span><span class="sxs-lookup"><span data-stu-id="91ff5-108">As a fallback solution another option to perform a _commit_ is simply to keep staring at a UI element which we refer to as _dwell_.</span></span>
<span data-ttu-id="91ff5-109">您可以使用 head 或眼睛來執行_停留_。</span><span class="sxs-lookup"><span data-stu-id="91ff5-109">A _dwell_ can be performed with either head or eye gaze.</span></span> <span data-ttu-id="91ff5-110">概念很簡單, 而且可以在下列階段中細分:</span><span class="sxs-lookup"><span data-stu-id="91ff5-110">The idea is simple and can be broken down in the following phases:</span></span> 
1. <span data-ttu-id="91ff5-111">使用者在全像攝影按鈕上啟動撥雲見日</span><span class="sxs-lookup"><span data-stu-id="91ff5-111">User starts gazing at a holographic button</span></span>

2. <span data-ttu-id="91ff5-112">在短暫的萌芽延遲 (例如, 150 毫秒) 之後, 會啟動一些視覺效果回饋動畫。</span><span class="sxs-lookup"><span data-stu-id="91ff5-112">After a brief onset delay (e.g., 150 ms) some visual feedback animation is started.</span></span> <span data-ttu-id="91ff5-113">萌芽延遲是用來避免使用者立即隨時掌握意見反應。</span><span class="sxs-lookup"><span data-stu-id="91ff5-113">The onset delay is used to avoid overwhelming the user by immediately popping up feedback all the time.</span></span>
    - <span data-ttu-id="91ff5-114">針對_眼睛眼_, 建議您將下列內容用於視覺監看意見反應的設計:</span><span class="sxs-lookup"><span data-stu-id="91ff5-114">For _eye gaze_, we recommend the following for the design of the visual dwell feedback:</span></span>
      - <span data-ttu-id="91ff5-115">**Blend**:從一開始就看不到完全不透明的意見反應順暢地 blend。</span><span class="sxs-lookup"><span data-stu-id="91ff5-115">**Blend it**: Smoothly blend in the feedback from barely visible at first to fully opaque.</span></span> <span data-ttu-id="91ff5-116">這使得意見反應越不容易分散和 overwhleming, 並妥善配合系統有使用者真正想要與此按鈕互動的信心。</span><span class="sxs-lookup"><span data-stu-id="91ff5-116">This makes the feedback less distracting and overwhleming and nicely aligns with the confidence that the system has that the user really wants to engage with this button.</span></span>
      - <span data-ttu-id="91ff5-117">**將它提取到**:建立視覺效果的意見反應, 而不是縮小大小並移至目標中心, 並在使用者的視覺效果中提取。</span><span class="sxs-lookup"><span data-stu-id="91ff5-117">**Pull it in**: Create a visual feedback than decreases in size and moves towards the center of the target, pulling in the user's visual attention.</span></span> 

3. <span data-ttu-id="91ff5-118">在預先定義的停留時間 (例如, 800 毫秒) 之後, 停留完成並觸發相關聯的事件。</span><span class="sxs-lookup"><span data-stu-id="91ff5-118">After a pre-defined dwell duration (e.g., 800 ms), the dwell completes and an associated event is triggered.</span></span>
    - <span data-ttu-id="91ff5-119">提供一些最終的聽覺或視覺效果意見反應, 讓您現在可以選擇專案的首頁。</span><span class="sxs-lookup"><span data-stu-id="91ff5-119">Provide some finalizing auditory or visual feedback to really bring home that the item got selected now.</span></span>

![停留狀態](images/eyes_dwellstate_recommendation.png)


# <a name="gaze-targeting"></a><span data-ttu-id="91ff5-121">注視目標</span><span class="sxs-lookup"><span data-stu-id="91ff5-121">Gaze targeting</span></span>

<span data-ttu-id="91ff5-122">無論輸入形式為何，當使用者能夠瞄準他們想要進行互動的元素時，所有互動就已建立。</span><span class="sxs-lookup"><span data-stu-id="91ff5-122">All interactions are built upon the ability of a user to target the element they want to interact with, regardless of the input modality.</span></span> <span data-ttu-id="91ff5-123">在 Windows Mixed Reality 中，這通常會使用使用者的注視進行。</span><span class="sxs-lookup"><span data-stu-id="91ff5-123">In Windows Mixed Reality, this is generally done using the user's gaze.</span></span>

<span data-ttu-id="91ff5-124">若要讓使用者能夠順利體驗，系統導出的使用者意圖理解，以及使用者的實際意圖都必須儘可能相吻合。</span><span class="sxs-lookup"><span data-stu-id="91ff5-124">To enable a user to work with an experience successfully, the system's calculated understanding of a user's intent, and the user's actual intent, must align as closely as possible.</span></span> <span data-ttu-id="91ff5-125">系統儘可能正確解譯使用者的預定動作，所以滿意度提升且效能改善。</span><span class="sxs-lookup"><span data-stu-id="91ff5-125">To the degree that the system interprets the user's intended actions correctly, satisfaction increases and performance improves.</span></span>

## <a name="device-support"></a><span data-ttu-id="91ff5-126">裝置支援</span><span class="sxs-lookup"><span data-stu-id="91ff5-126">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="91ff5-127"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="91ff5-127"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="91ff5-128"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="91ff5-128"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="91ff5-129"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="91ff5-129"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="91ff5-130"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="91ff5-130"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="91ff5-131">注視目標</span><span class="sxs-lookup"><span data-stu-id="91ff5-131">Gaze targeting</span></span></td>
        <td><span data-ttu-id="91ff5-132">✔️</span><span class="sxs-lookup"><span data-stu-id="91ff5-132">✔️</span></span></td>
        <td><span data-ttu-id="91ff5-133">✔️</span><span class="sxs-lookup"><span data-stu-id="91ff5-133">✔️</span></span></td>
        <td><span data-ttu-id="91ff5-134">✔️</span><span class="sxs-lookup"><span data-stu-id="91ff5-134">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="91ff5-135">目視目標</span><span class="sxs-lookup"><span data-stu-id="91ff5-135">Eye targeting</span></span></td>
        <td><span data-ttu-id="91ff5-136">❌</span><span class="sxs-lookup"><span data-stu-id="91ff5-136">❌</span></span></td>
        <td><span data-ttu-id="91ff5-137">✔️</span><span class="sxs-lookup"><span data-stu-id="91ff5-137">✔️</span></span></td>
        <td><span data-ttu-id="91ff5-138">❌</span><span class="sxs-lookup"><span data-stu-id="91ff5-138">❌</span></span></td>
    </tr>
</table>

> [!NOTE]
> <span data-ttu-id="91ff5-139">[即將推出](index.md)更多 HoloLens 2 特定指引。</span><span class="sxs-lookup"><span data-stu-id="91ff5-139">More guidance specific to HoloLens 2 [coming soon](index.md).</span></span>

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="91ff5-140">目標大小調整和回饋</span><span class="sxs-lookup"><span data-stu-id="91ff5-140">Target sizing and feedback</span></span>

<span data-ttu-id="91ff5-141">雖已重複表示注視向量可用於細微定向，但通常最適合用於粗略定向 (取得較大的目標)。</span><span class="sxs-lookup"><span data-stu-id="91ff5-141">The gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting (acquiring somewhat larger targets).</span></span> <span data-ttu-id="91ff5-142">在大部分情況下，1 到 1.5 度的最小目標大小應可達成成功的使用者動作，但是 3 度的目標通常可讓速度提升。</span><span class="sxs-lookup"><span data-stu-id="91ff5-142">Minimum target sizes of 1 to 1.5 degrees should allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="91ff5-143">請注意，使用者定向的大小實際上是 2D 區域 (即使是 3D 元素)，無論哪個投影面向他們都應該是可作為目標的區域。</span><span class="sxs-lookup"><span data-stu-id="91ff5-143">Note that the size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="91ff5-144">提供元素為「作用中」(使用者以其為目標) 的一些明顯線索非常有用 - 這可能包括視覺「暫留」效果、音訊醒目提示或點按，或游標與元素的清楚比對等處理。</span><span class="sxs-lookup"><span data-stu-id="91ff5-144">Providing some salient cue that an element is "active" (that the user is targeting it) is extremely helpful - this can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="91ff5-145">![2 個計量表距離的最佳目標大小](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="91ff5-145">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="91ff5-146">*2 個計量表距離的最佳目標大小*</span><span class="sxs-lookup"><span data-stu-id="91ff5-146">*Optimal target size at 2 meter distance*</span></span>

<span data-ttu-id="91ff5-147">![醒目提示注視目標物件的範例](images/gazetargeting-highlighting-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="91ff5-147">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-640px.jpg)</span></span><br>
<span data-ttu-id="91ff5-148">*醒目提示注視目標物件的範例*</span><span class="sxs-lookup"><span data-stu-id="91ff5-148">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="91ff5-149">目標位置</span><span class="sxs-lookup"><span data-stu-id="91ff5-149">Target placement</span></span>

<span data-ttu-id="91ff5-150">使用者通常找不到其視野中位於很高或很低的 UI 元素，而將其大部分的注意力放在其主要焦點的四周 (通常大約在眼部水平高度)。</span><span class="sxs-lookup"><span data-stu-id="91ff5-150">Users will often fail to find UI elements that are positioned very high or very low in their field of view, focusing most of their attention on areas around their main focus (usually roughly eye level).</span></span> <span data-ttu-id="91ff5-151">將大部分的目標放在眼部水平周圍的合理頻帶會有所幫助。</span><span class="sxs-lookup"><span data-stu-id="91ff5-151">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="91ff5-152">假設使用者傾向於隨時將焦點放在相對較小的視覺區域 (視覺的注意視錐大約是 10 度)，將概念上相關的 UI 元素聚集在一起，可以在使用者目光掃過區域時運用逐一項目的注意鏈結行為。</span><span class="sxs-lookup"><span data-stu-id="91ff5-152">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree that they're related conceptually can leverage attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="91ff5-153">在設計 UI 時，請記住 HoloLens 與沉浸式頭戴裝置之間的視野可能有很大的變化。</span><span class="sxs-lookup"><span data-stu-id="91ff5-153">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="91ff5-154">![方便在 Galaxy Explorer 中進行注視定向的分組 UI 元素範例](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="91ff5-154">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="91ff5-155">*方便在 Galaxy Explorer 中進行注視定向的分組 UI 元素範例*</span><span class="sxs-lookup"><span data-stu-id="91ff5-155">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="91ff5-156">改善定向行為</span><span class="sxs-lookup"><span data-stu-id="91ff5-156">Improving targeting behaviors</span></span>

<span data-ttu-id="91ff5-157">如果可以判定使用者瞄準某物的意圖 (或極為近似)，則接受互動時的「近似差錯」嘗試 (彷彿已正確瞄準) 很有幫助。</span><span class="sxs-lookup"><span data-stu-id="91ff5-157">If user intent to target something can be determined (or approximated closely), it can be very helpful to accept "near miss" attempts at interaction as though they were targeted correctly.</span></span> <span data-ttu-id="91ff5-158">有少數幾個成功方法可以納入混合實境體驗：</span><span class="sxs-lookup"><span data-stu-id="91ff5-158">There are a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="gaze-stabilization-gravity-wells"></a><span data-ttu-id="91ff5-159">注視穩定 ("引力 wells")</span><span class="sxs-lookup"><span data-stu-id="91ff5-159">Gaze stabilization ("gravity wells")</span></span>

<span data-ttu-id="91ff5-160">在大部分/所有的時間，應該開啟此功能。</span><span class="sxs-lookup"><span data-stu-id="91ff5-160">This should be turned on most/all of the time.</span></span> <span data-ttu-id="91ff5-161">這項技術會消除使用者可能會有的頭部/頸部緊張情形。</span><span class="sxs-lookup"><span data-stu-id="91ff5-161">This technique removes the natural head/neck jitters that users may have.</span></span> <span data-ttu-id="91ff5-162">以及由於觀看/說話行為而造成的移動。</span><span class="sxs-lookup"><span data-stu-id="91ff5-162">Also movement due to looking/speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="91ff5-163">最接近的連結演算法</span><span class="sxs-lookup"><span data-stu-id="91ff5-163">Closest link algorithms</span></span>

<span data-ttu-id="91ff5-164">這些最適合用於具有疏鬆互動式內容的區域。</span><span class="sxs-lookup"><span data-stu-id="91ff5-164">These work best in areas with sparse interactive content.</span></span> <span data-ttu-id="91ff5-165">如果您非常可能判定使用者嘗試進行互動的項目，則只要假定某些層級的意圖，即可補充其定向能力。</span><span class="sxs-lookup"><span data-stu-id="91ff5-165">If there is a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by simply assuming some level of intent.</span></span>

### <a name="backdatingpostdating-actions"></a><span data-ttu-id="91ff5-166">回溯記日/事後記日動作</span><span class="sxs-lookup"><span data-stu-id="91ff5-166">Backdating/postdating actions</span></span>

<span data-ttu-id="91ff5-167">這項機制對於要求速度的工作很實用。</span><span class="sxs-lookup"><span data-stu-id="91ff5-167">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="91ff5-168">當使用者在一系列以速度為目標/啟用調動的過程中移動時, 可能會有一些意圖, 並允許*遺漏的步驟*來採取動作, 讓使用者在點按 (50 毫秒之前/之後) 稍早或稍微專注于目標在早期測試時生效)。</span><span class="sxs-lookup"><span data-stu-id="91ff5-168">When a user is moving through a series of targeting/activation maneuvers at speed, it can be useful to assume some intent and allow *missed steps* to act upon targets which the user had in focus slightly before or slightly after the tap (50ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="91ff5-169">平滑處理</span><span class="sxs-lookup"><span data-stu-id="91ff5-169">Smoothing</span></span>

<span data-ttu-id="91ff5-170">這項機制可用於路徑移動，減少自然頭部移動特性所造成的些許抖動/搖晃。</span><span class="sxs-lookup"><span data-stu-id="91ff5-170">This mechanism is useful for pathing movements, reducing the slight jitter/wobble due to natural head movement characteristics.</span></span> <span data-ttu-id="91ff5-171">平滑處理路徑移動時，請依照移動的大小/距離 (而非隨著時間) 進行平滑處理</span><span class="sxs-lookup"><span data-stu-id="91ff5-171">When smoothing over pathing motions, smooth by size/distance of movements rather than over time</span></span>

### <a name="magnetism"></a><span data-ttu-id="91ff5-172">磁性</span><span class="sxs-lookup"><span data-stu-id="91ff5-172">Magnetism</span></span>

<span data-ttu-id="91ff5-173">這項機制可以視為更普遍的「最接近連結」演算法版本 - 繪製指向目標的游標，或只要在使用者接近適當目標時增加命中框 (不論是否看得見)，使用互動式版面配置的一些知識更完善處理使用者意圖。</span><span class="sxs-lookup"><span data-stu-id="91ff5-173">This mechanism can be thought of as a more general version of "Closest link" algorithms - drawing a cursor toward a target, or simply increasing hitboxes (whether visibly or not) as users approach likely targets, using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="91ff5-174">這對於小型目標特別有效果。</span><span class="sxs-lookup"><span data-stu-id="91ff5-174">This can be particularly powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="91ff5-175">焦點黏著度</span><span class="sxs-lookup"><span data-stu-id="91ff5-175">Focus stickiness</span></span>

<span data-ttu-id="91ff5-176">在判斷要聚焦在哪些附近互動式元素時，提供目前焦點所在元素的偏差。</span><span class="sxs-lookup"><span data-stu-id="91ff5-176">When determining which nearby interactive elements to give focus to, provide a bias to the element that is currently focused.</span></span> <span data-ttu-id="91ff5-177">這有助於在浮動於兩個具有自然雜訊的元素間中點時，減少不穩定的焦點切換行為。</span><span class="sxs-lookup"><span data-stu-id="91ff5-177">This will help reduce erratic focus switching behaviours when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="91ff5-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91ff5-178">See also</span></span>
* [<span data-ttu-id="91ff5-179">筆勢</span><span class="sxs-lookup"><span data-stu-id="91ff5-179">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="91ff5-180">語音命令</span><span class="sxs-lookup"><span data-stu-id="91ff5-180">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="91ff5-181">游標</span><span class="sxs-lookup"><span data-stu-id="91ff5-181">Cursors</span></span>](cursors.md)
