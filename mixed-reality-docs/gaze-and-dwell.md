---
title: 視線和詳述
description: 視線和詳述輸入模型的概觀
author: liamartinez
ms.author: liamar
ms.date: 03/31/2019
ms.topic: article
keywords: 混合實境，視線、 詳述、 互動，設計
ms.openlocfilehash: a50ae948a351f5152ebb98778da9be8c08090d72
ms.sourcegitcommit: 222cba2d622b47f75949bf8af80d5c62de4dceab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "64914615"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="058d0-104">視線和詳述</span><span class="sxs-lookup"><span data-stu-id="058d0-104">Gaze and dwell</span></span>

<span data-ttu-id="058d0-105">指針會佔用工具和組件，當筆勢可以很繁瑣或是不可能。</span><span class="sxs-lookup"><span data-stu-id="058d0-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span>  <span data-ttu-id="058d0-106">語音命令，例如鍵筆勢，可以視情況下不可靠，例如在極大的情況下。</span><span class="sxs-lookup"><span data-stu-id="058d0-106">Voice commands, like gesture, can be situationally unreliable, for example under excessively loud conditions.</span></span>  <span data-ttu-id="058d0-107">此外，使用語音來控制電腦不是主要的互動，但當然取得資料流 ！</span><span class="sxs-lookup"><span data-stu-id="058d0-107">Additionally, using voice to control computers isn't a mainstream interaction yet, but it certainly is gaining steam!</span></span>  <span data-ttu-id="058d0-108">視線詳述提供工作抬頭免持聽筒 HoloLens 上的最熟悉且容易主要機制。</span><span class="sxs-lookup"><span data-stu-id="058d0-108">Gaze dwell offers the most familiar and easy-to-master mechanism for working heads-up hands-free on HoloLens.</span></span>  <span data-ttu-id="058d0-109">此外，視線詳述是 100%可靠與雜訊干擾或無回應中的條件約束的作業環境無關。</span><span class="sxs-lookup"><span data-stu-id="058d0-109">Additionally, gaze dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="goals"></a><span data-ttu-id="058d0-110">目標</span><span class="sxs-lookup"><span data-stu-id="058d0-110">Goals</span></span>

<span data-ttu-id="058d0-111">提供機制，以完整免持聽筒互動，而不需使用語音。</span><span class="sxs-lookup"><span data-stu-id="058d0-111">Provide a mechanism for full hands-free interactions, without using Voice.</span></span>

## <a name="design-principles"></a><span data-ttu-id="058d0-112">設計原則</span><span class="sxs-lookup"><span data-stu-id="058d0-112">Design principles</span></span>

1. <span data-ttu-id="058d0-113">視線不是武器</span><span class="sxs-lookup"><span data-stu-id="058d0-113">Gaze is not a weapon</span></span>
    
    <span data-ttu-id="058d0-114">視線需要視覺化回饋直覺互動，但是太多的意見反應可以引發前。</span><span class="sxs-lookup"><span data-stu-id="058d0-114">Gaze requires visual feedback for intuitive interaction, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="058d0-115">意見反應應該協助使用者，知道什麼他們設為目標，但不是自動選取針對其意圖。</span><span class="sxs-lookup"><span data-stu-id="058d0-115">The feedback should help a user know what they're targeting, but not auto-select against their intent.</span></span> <span data-ttu-id="058d0-116">讀取文字需要額外的考量，以提供使用者空間，以吸收之前選取的資訊。</span><span class="sxs-lookup"><span data-stu-id="058d0-116">Reading text requires extra consideration to provide a user room to absorb the info before selecting.</span></span>
    
2. <span data-ttu-id="058d0-117">搜尋 Goldilocks 速度</span><span class="sxs-lookup"><span data-stu-id="058d0-117">Seek Goldilocks speed</span></span>
    
    <span data-ttu-id="058d0-118">詳述填滿可以有不同的計時器為基礎的導覽的影響-較常使用的函式將通常受益於更快速的填滿時間，而更衍生性損害函式可能會受益於較長的填滿時間。</span><span class="sxs-lookup"><span data-stu-id="058d0-118">The dwell fill can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="058d0-119">填滿色彩的動畫曲線可以正面影響更快速的填滿時間能的一目了然。</span><span class="sxs-lookup"><span data-stu-id="058d0-119">Animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="058d0-120">應該採取的考量，以讓使用者決定從快速/medium/緩慢填滿速度覆寫。</span><span class="sxs-lookup"><span data-stu-id="058d0-120">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
3. <span data-ttu-id="058d0-121">假設 no-no 爬昇效果</span><span class="sxs-lookup"><span data-stu-id="058d0-121">Say no-no to yo-yo effect</span></span>

    <span data-ttu-id="058d0-122">爬昇效果 (也稱為 「 夜間在 Roxbury 」) 是不安的模式，從特定位置的內容和視線型控制項，可能會出現。</span><span class="sxs-lookup"><span data-stu-id="058d0-122">The yo-yo effect (also known as "Night at the Roxbury") is an uncomfortable pattern that can emerge from certain  placement of content and gaze-based controls.</span></span> <span data-ttu-id="058d0-123">比方說，使用底部的 [填滿] 按鈕清單導覽會引發迴圈的-外觀下會探討、 查詢結果、 向下瀏覽至詳述，依此類推。這個產生的模式時感到不舒服，及應避免將導覽控制項放在上一步往來需要較少的集中位置。</span><span class="sxs-lookup"><span data-stu-id="058d0-123">For example, a list nav with the fill button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, etc. This resulting pattern is uncomfortable and should be avoided by placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="058d0-124">放置相對於其效果詳述按鈕變得很重要的緩和。</span><span class="sxs-lookup"><span data-stu-id="058d0-124">Placement of dwell buttons relative to their effects becomes important for comfort.</span></span>

## <a name="ui-patterns"></a><span data-ttu-id="058d0-125">UI 模式</span><span class="sxs-lookup"><span data-stu-id="058d0-125">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="058d0-126">高頻率按鈕</span><span class="sxs-lookup"><span data-stu-id="058d0-126">High frequency buttons</span></span>
    
* <span data-ttu-id="058d0-127">下一步 / 上一頁 按鈕</span><span class="sxs-lookup"><span data-stu-id="058d0-127">Next/Back buttons</span></span>
  * <span data-ttu-id="058d0-128">非常短的延遲預先填滿 （快顯重繪閃動緩衝處理）</span><span class="sxs-lookup"><span data-stu-id="058d0-128">Very short delay pre-fill (flyover flicker buffer)</span></span>
  * <span data-ttu-id="058d0-129">較大的按鈕都使用視線叫用的工作變得更容易</span><span class="sxs-lookup"><span data-stu-id="058d0-129">Larger buttons are easier to hit with gaze</span></span>
  * <span data-ttu-id="058d0-130">好讓這些欄位的眼睛高度互動所以沒有壓力</span><span class="sxs-lookup"><span data-stu-id="058d0-130">Nice to keep these at eye height so no strain to interact</span></span>
  * <span data-ttu-id="058d0-131">詳述區域可能大於非使用中的圖示，以讓它更容易使用 （後）</span><span class="sxs-lookup"><span data-stu-id="058d0-131">Dwell region can be larger than inactive icon to make it easier to use (BACK)</span></span>

### <a name="low-frequency-buttons"></a><span data-ttu-id="058d0-132">低頻率按鈕</span><span class="sxs-lookup"><span data-stu-id="058d0-132">Low frequency buttons</span></span>
    
* <span data-ttu-id="058d0-133">啟動 [設定] 功能表</span><span class="sxs-lookup"><span data-stu-id="058d0-133">Activate settings menu</span></span>
  * <span data-ttu-id="058d0-134">再延遲預先填滿好 （快顯重繪閃動緩衝處理）</span><span class="sxs-lookup"><span data-stu-id="058d0-134">Longer delay pre-fill okay (flyover flicker buffer)</span></span>
  * <span data-ttu-id="058d0-135">請盡量保持頻繁的資料指標路徑利用這些按鈕</span><span class="sxs-lookup"><span data-stu-id="058d0-135">Try to keep these buttons out of the way of frequent cursor pathways</span></span>

* <span data-ttu-id="058d0-136">確認 （也就是掃描流程，對話方塊）</span><span class="sxs-lookup"><span data-stu-id="058d0-136">Confirmations (i.e. scan flow, dialogs)</span></span>
  * <span data-ttu-id="058d0-137">主要按鈕上顯示選取項目反白顯示</span><span class="sxs-lookup"><span data-stu-id="058d0-137">Show selection highlight on main button</span></span>
  * <span data-ttu-id="058d0-138">顯示與選取項目醒目提示同時探討目標</span><span class="sxs-lookup"><span data-stu-id="058d0-138">Reveal dwell target at same time as selection highlight</span></span>
  * <span data-ttu-id="058d0-139">使用會探討周圍的圖示，以保持介面更簡單的目標</span><span class="sxs-lookup"><span data-stu-id="058d0-139">Use dwell target surrounding icon to keep interface simple</span></span>
  * <span data-ttu-id="058d0-140">重要的決策，不會啟用反白顯示，因此會詳述目標顯示靈活的時間</span><span class="sxs-lookup"><span data-stu-id="058d0-140">Important decision, so highlight doesn't activate, reveals dwell target for reconsideration time</span></span>
        
### <a name="toggle-buttons"></a><span data-ttu-id="058d0-141">切換按鈕</span><span class="sxs-lookup"><span data-stu-id="058d0-141">Toggle buttons</span></span>

* <span data-ttu-id="058d0-142">Pin</span><span class="sxs-lookup"><span data-stu-id="058d0-142">Pin</span></span>
  * <span data-ttu-id="058d0-143">清除作用中/非作用中的視覺狀態</span><span class="sxs-lookup"><span data-stu-id="058d0-143">Clear active/inactive visual state</span></span>
  * <span data-ttu-id="058d0-144">放射狀填滿協助焦點使用者，並提供自然的進度</span><span class="sxs-lookup"><span data-stu-id="058d0-144">Radial fill helps focus user and provides natural progress</span></span> 

* <span data-ttu-id="058d0-145">個別的設定</span><span class="sxs-lookup"><span data-stu-id="058d0-145">Individual settings</span></span>
  * <span data-ttu-id="058d0-146">清除作用中/非作用中狀態</span><span class="sxs-lookup"><span data-stu-id="058d0-146">Clear active/inactive states</span></span>
  * <span data-ttu-id="058d0-147">探討左周圍的圖示上的所有目標</span><span class="sxs-lookup"><span data-stu-id="058d0-147">Dwell targets all on left surrounding icon</span></span>
  * <span data-ttu-id="058d0-148">詳述目標只顯示選取項目時反白顯示作用中</span><span class="sxs-lookup"><span data-stu-id="058d0-148">Dwell targets only show up when selection highlight active</span></span>
  * <span data-ttu-id="058d0-149">"會探討在滑桿上 「 右端的開啟/關閉設定</span><span class="sxs-lookup"><span data-stu-id="058d0-149">"Dwell on slider" on right side for on/off settings</span></span>

### <a name="list-views"></a><span data-ttu-id="058d0-150">清單檢視</span><span class="sxs-lookup"><span data-stu-id="058d0-150">List views</span></span>

* <span data-ttu-id="058d0-151">瀏覽清單檢視-引導要開啟的檔案</span><span class="sxs-lookup"><span data-stu-id="058d0-151">Browsing list view - guide files to open</span></span>
  * <span data-ttu-id="058d0-152">資料指標反白顯示資料列從任何位置上的資料列，但不開始詳述</span><span class="sxs-lookup"><span data-stu-id="058d0-152">Cursor highlights row from anywhere on row but doesn’t begin dwell</span></span>
  * <span data-ttu-id="058d0-153">當資料列資料指標所反白顯示時，詳述目標出現在左邊</span><span class="sxs-lookup"><span data-stu-id="058d0-153">When row is highlighted by cursor, dwell target appears on left</span></span>
  * <span data-ttu-id="058d0-154">探討目標一律在所有的清單檢視中的文字左邊圓形</span><span class="sxs-lookup"><span data-stu-id="058d0-154">Dwell target always a circle on left side of text in all list views</span></span>
  * <span data-ttu-id="058d0-155">不會顯示所有會探討目標一次，以避免重複的 UI</span><span class="sxs-lookup"><span data-stu-id="058d0-155">Don't show all dwell targets at once to avoid repetitive UI</span></span>
  * <span data-ttu-id="058d0-156">重複使用相同的模式，以建立 UX 的熟悉度</span><span class="sxs-lookup"><span data-stu-id="058d0-156">Re-use the same pattern to establish UX familiarity</span></span>
        
* <span data-ttu-id="058d0-157">瀏覽清單檢視-指南中的工作/步驟的階層架構</span><span class="sxs-lookup"><span data-stu-id="058d0-157">Browsing list view - hierarchy of tasks/steps in a guide</span></span>
  * <span data-ttu-id="058d0-158">探討目標永遠左邊算起的圓形</span><span class="sxs-lookup"><span data-stu-id="058d0-158">Dwell target always a circle on left side of text</span></span>
  * <span data-ttu-id="058d0-159">展開/摺疊會探討功能可見性</span><span class="sxs-lookup"><span data-stu-id="058d0-159">Collapse/expand dwell affordance</span></span>
        
* <span data-ttu-id="058d0-160">瀏覽清單檢視模式，請選取</span><span class="sxs-lookup"><span data-stu-id="058d0-160">Browsing list view - mode select</span></span>
  * <span data-ttu-id="058d0-161">請遵循上面所建立的模式</span><span class="sxs-lookup"><span data-stu-id="058d0-161">Follow patterns established above</span></span>

### <a name="contextual-buttons"></a><span data-ttu-id="058d0-162">內容按鈕</span><span class="sxs-lookup"><span data-stu-id="058d0-162">Contextual buttons</span></span>

* <span data-ttu-id="058d0-163">顯示/隱藏 3D-顯示總 3D 中沿著 tether 接近全像投影</span><span class="sxs-lookup"><span data-stu-id="058d0-163">Show/Hide 3D - shows up in 3D along tether near holograms</span></span> 
  * <span data-ttu-id="058d0-164">清除作用中/非作用中的視覺狀態</span><span class="sxs-lookup"><span data-stu-id="058d0-164">Clear active/inactive visual state</span></span>

### <a name="pivots"></a><span data-ttu-id="058d0-165">樞紐</span><span class="sxs-lookup"><span data-stu-id="058d0-165">Pivots</span></span>

* <span data-ttu-id="058d0-166">最近/All 指南清單</span><span class="sxs-lookup"><span data-stu-id="058d0-166">Recent/All guides list</span></span>
  * <span data-ttu-id="058d0-167">填滿剩餘表示哪一個索引標籤為作用中的 UI 功能可見性</span><span class="sxs-lookup"><span data-stu-id="058d0-167">Fill the UI affordance that remains to indicate which tab is active</span></span>
  * <span data-ttu-id="058d0-168">為簡短的單字樞紐分析表中，我們選擇放棄詳述目標模式</span><span class="sxs-lookup"><span data-stu-id="058d0-168">For short single word pivots, we elected to forego the dwell target pattern</span></span>
  * <span data-ttu-id="058d0-169">我們透過另一個 2 的圓形目標和更多的 UI 偏好簡化的介面</span><span class="sxs-lookup"><span data-stu-id="058d0-169">We favored the simplified interface over another 2 circle targets and a wider UI</span></span>
  * <span data-ttu-id="058d0-170">在我們的案例中，字詞很短的延遲提供足夠的緩和填滿之前</span><span class="sxs-lookup"><span data-stu-id="058d0-170">In our case, the words are short enough that a delay provides enough comfort before filling</span></span>


## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="058d0-171">UX 指導方針和最佳作法</span><span class="sxs-lookup"><span data-stu-id="058d0-171">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="058d0-172">目標大小</span><span class="sxs-lookup"><span data-stu-id="058d0-172">Target sizes</span></span>

  * <span data-ttu-id="058d0-173">釘選圖示的大小下限：在 Unity 中，30 Mru （@ 2 分 30 公分） 的世界空間中的 6 cm</span><span class="sxs-lookup"><span data-stu-id="058d0-173">Pin icon minimum size: 6cm in world space in Unity, 30 MRUs ( 30cm @ 2m)</span></span>
  * <span data-ttu-id="058d0-174">完全是目標"magnetized 」 或 「 便利貼 」？</span><span class="sxs-lookup"><span data-stu-id="058d0-174">Are the targets "magnetized" or "sticky" at all?</span></span> <span data-ttu-id="058d0-175">（也就是視線平滑化資料指標）</span><span class="sxs-lookup"><span data-stu-id="058d0-175">(i.e. gaze cursor smoothing)</span></span>

### <a name="animation"></a><span data-ttu-id="058d0-176">動畫</span><span class="sxs-lookup"><span data-stu-id="058d0-176">Animation</span></span>

  * <span data-ttu-id="058d0-177">詳述 visual 的觸發程序.5sec 前所延遲</span><span class="sxs-lookup"><span data-stu-id="058d0-177">Delay before dwell visual triggers .5sec</span></span>
  * <span data-ttu-id="058d0-178">詳述 visual 1.2 秒的持續時間</span><span class="sxs-lookup"><span data-stu-id="058d0-178">Duration of dwell visual 1.2sec</span></span>
  * <span data-ttu-id="058d0-179">在動畫上的曲線嗎？</span><span class="sxs-lookup"><span data-stu-id="058d0-179">Curve on animation?</span></span>

### <a name="visual-feedback"></a><span data-ttu-id="058d0-180">視覺化回饋</span><span class="sxs-lookup"><span data-stu-id="058d0-180">Visual feedback</span></span>

  * <span data-ttu-id="058d0-181">放射狀填滿從視線資料指標的開始位置</span><span class="sxs-lookup"><span data-stu-id="058d0-181">Radial fill from gaze cursor start location</span></span>
  * <span data-ttu-id="058d0-182">從中央按鈕一律星形的填滿。</span><span class="sxs-lookup"><span data-stu-id="058d0-182">Always radial fill from center of button.</span></span> <span data-ttu-id="058d0-183">一致的回應是不同的按鈕上的所有不同方向比不容易產生混淆。</span><span class="sxs-lookup"><span data-stu-id="058d0-183">A consistent response is less confusing than all different directions on different buttons.</span></span> 
    * <span data-ttu-id="058d0-184">此規則可以中斷雖然方向互動 （例如，瀏覽向上/向下/左/右，等等）。</span><span class="sxs-lookup"><span data-stu-id="058d0-184">This rule can be broken though for directional interactions (e.g., nav up/down/left/right, etc.).</span></span> <span data-ttu-id="058d0-185">例如，在下一步/後要保留的例外狀況的指南會以滑鼠右鍵會填滿。</span><span class="sxs-lookup"><span data-stu-id="058d0-185">For example, Guides makes an exception on NEXT/BACK being left right fills.</span></span>
    * <span data-ttu-id="058d0-186">請考慮反轉從放射狀填滿外的 （如果切換關閉）。</span><span class="sxs-lookup"><span data-stu-id="058d0-186">Consider inverting radial fill from outside (if toggling off).</span></span> <span data-ttu-id="058d0-187">按下按鈕反掌控是維護良好的視覺化模式。</span><span class="sxs-lookup"><span data-stu-id="058d0-187">THe inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="058d0-188">漸進式揭露</span><span class="sxs-lookup"><span data-stu-id="058d0-188">Progressive Disclosure</span></span>

 * <span data-ttu-id="058d0-189">漸進式揭露表示詳述目標揭露上反白顯示 （例如，在清單控制項）</span><span class="sxs-lookup"><span data-stu-id="058d0-189">Progressive disclosure means that the dwell target is revealed on highlight (e.g., in a list control)</span></span>
 * <span data-ttu-id="058d0-190">視線上文字的任何位置上顯示的文字列反白顯示與焦點</span><span class="sxs-lookup"><span data-stu-id="058d0-190">Text bar highlights with spotlight reveal on gaze anywhere on text</span></span>
 * <span data-ttu-id="058d0-191">視線填滿目標永遠會出現在左邊，但只適用於反白顯示的清單項目</span><span class="sxs-lookup"><span data-stu-id="058d0-191">Gaze fill target appears always on left, but only for the list item which is highlighted</span></span>
 * <span data-ttu-id="058d0-192">請避免上的所有詳述目標都隨時因重複外觀的堆疊的圓形</span><span class="sxs-lookup"><span data-stu-id="058d0-192">Try to avoid having all dwell targets on at all times due to repetitive look of stacked circles</span></span>
 
 ## <a name="see-also"></a><span data-ttu-id="058d0-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="058d0-193">See also</span></span>
* [<span data-ttu-id="058d0-194">直接操作</span><span class="sxs-lookup"><span data-stu-id="058d0-194">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="058d0-195">點和認可</span><span class="sxs-lookup"><span data-stu-id="058d0-195">Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="058d0-196">互動基本概念</span><span class="sxs-lookup"><span data-stu-id="058d0-196">Interaction fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="058d0-197">Head 視線與認可</span><span class="sxs-lookup"><span data-stu-id="058d0-197">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="058d0-198">視線和語音</span><span class="sxs-lookup"><span data-stu-id="058d0-198">Gaze and voice</span></span>](voice-design.md)
