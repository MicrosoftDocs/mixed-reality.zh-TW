---
title: 手形功能表
description: 快顯功能表可讓使用者快速地為常用的函式帶出手動連接的 UI。 這些是我們的最佳做法和功能表的建議。
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: 手形、功能表、按鈕、快速存取、版面配置
ms.openlocfilehash: c0e1800be69a15706e17f40b1601fc79d05e5d75
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723257"
---
# <a name="hand-menu"></a><span data-ttu-id="92389-105">手形功能表</span><span class="sxs-lookup"><span data-stu-id="92389-105">Hand menu</span></span>

![Ulnar 端位置](images/UX/UX_Hero_HandMenu.jpg)

<span data-ttu-id="92389-107">快顯功能表可讓使用者快速地為常用的函式帶出手動連接的 UI。</span><span class="sxs-lookup"><span data-stu-id="92389-107">Hand menus allow users to quickly bring up hand-attached UI for frequently used functions.</span></span> 

<span data-ttu-id="92389-108">以下是我們在功能表中找到的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="92389-108">Below are the best practices we have found for hand menus.</span></span> <span data-ttu-id="92389-109">您也可以在[MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup)中找到示範 [手形] 功能表的範例場景。</span><span class="sxs-lookup"><span data-stu-id="92389-109">You can also find an example scene demonstrating the hand menu in [MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup).</span></span>

<br>

---

## <a name="behavior-best-practices"></a><span data-ttu-id="92389-110">行為最佳做法</span><span class="sxs-lookup"><span data-stu-id="92389-110">Behavior best practices</span></span>
<span data-ttu-id="92389-111">**答：將按鈕的數目保持**在最小的範圍 . 因為手鎖住的功能表和眼睛之間的距離很近，而且使用者傾向于隨時專注于相對較小的視覺區域（視覺效果的 attentional 錐形大約是10度），我們建議您將按鈕數目保持為小。</span><span class="sxs-lookup"><span data-stu-id="92389-111">**A. Keep the number of buttons small:** Due to the close distance between a hand-locked menu and the eyes and also the user's tendency to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="92389-112">根據我們的探索，即使使用者將其手移至 FOV 的中心，還有三個按鈕的資料行，都能妥善運作。</span><span class="sxs-lookup"><span data-stu-id="92389-112">Based on our exploration, one column with three buttons work well by keeping all the content within the field of view (FOV) even when users move their hands to the center of the FOV.</span></span> 

<span data-ttu-id="92389-113">**B. 利用快顯功能表進行快速動作：** 引發 arm 並維護位置，很容易就會造成 arm 疲勞。</span><span class="sxs-lookup"><span data-stu-id="92389-113">**B. Utilize hand menu for quick action:** Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="92389-114">針對需要短暫互動的功能表，使用手動鎖定的方法。</span><span class="sxs-lookup"><span data-stu-id="92389-114">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="92389-115">如果您的功能表很複雜，而且需要擴充的互動時間，請考慮改為使用世界鎖定或主體鎖定。</span><span class="sxs-lookup"><span data-stu-id="92389-115">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="92389-116">**C. 按鈕/面板的角度：** 功能表應該會以相反的肩和中間來表示：這可讓自然手移動與功能表進行互動，並在觸及按鈕時避免任何難以使用或不舒服的位置。</span><span class="sxs-lookup"><span data-stu-id="92389-116">**C. Button / Panel angle:** Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="92389-117">**D. 考慮支援一次性或無人參與**的作業：不假設這兩個使用者都一律可以使用。</span><span class="sxs-lookup"><span data-stu-id="92389-117">**D. Consider supporting one-handed or hands-free operation:** Do not assume both of the user's hands are always available.</span></span> <span data-ttu-id="92389-118">當一或兩個手無法使用時，請考慮各種內容，並確定您的設計帳戶適用于這些情況。</span><span class="sxs-lookup"><span data-stu-id="92389-118">Consider a wide range of contexts when one or both hands are not available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="92389-119">若要支援單次功能表，您可以嘗試將功能表位置從 [手動鎖定] 轉換為 [世界鎖定] （當手翻轉時）。</span><span class="sxs-lookup"><span data-stu-id="92389-119">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="92389-120">針對無人參與的情況，請考慮使用語音命令來叫用快顯功能表按鈕。</span><span class="sxs-lookup"><span data-stu-id="92389-120">For hands-free scenarios, consider using a voice command to invoke the hand menu buttons.</span></span>

<span data-ttu-id="92389-121">**E. 兩步驟的**叫用：如果您只使用 palm 作為事件來觸發快顯功能表，它可能不會在您不需要時意外出現（誤報），因為人們會刻意（用於通訊和物件操作）和無意地移動其手。</span><span class="sxs-lookup"><span data-stu-id="92389-121">**E. Two-step invocation:** If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands a lot both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="92389-122">如果您的應用程式中遇到誤報，請考慮新增額外的步驟（除了 palm 事件以外），以叫用右手邊的功能表，例如完全開啟的手指。</span><span class="sxs-lookup"><span data-stu-id="92389-122">If you experience false-positives in your app, consider adding an additional step besides the palm-up event to invoke the hand menu such as fully opened fingers.</span></span>

<span data-ttu-id="92389-123">**F. 避免在手腕（系統首頁按鈕）附近新增按鈕：** 如果功能表按鈕太靠近 [首頁] 按鈕，則在與 [快顯功能表] 互動時，可能會意外觸發。</span><span class="sxs-lookup"><span data-stu-id="92389-123">**F. Avoid adding buttons near the wrist (system home button):** If the hand menu buttons are placed too close to the home button, it may get accidentally triggered while interacting with the hand menu.</span></span>

<span data-ttu-id="92389-124">**G. 測試、測試、測試：** 人員有不同的主體，而且有不同的臨界值來緩和和 discomfort 等等。請務必測試您的設計，並取得來自各種人的意見反應。</span><span class="sxs-lookup"><span data-stu-id="92389-124">**G. Test, test, test:** People have different bodies, with different thresholds for comfort and discomfort, etc. Be sure to test out your design on and get feedback from a variety of people.</span></span>

<br>

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="92389-125">手形功能表位置最佳做法</span><span class="sxs-lookup"><span data-stu-id="92389-125">Hand menu placement best practices</span></span>

<span data-ttu-id="92389-126">在「人為剖析」中，ulnar nerve 是在 ulna 骨骼附近執行的 nerve。</span><span class="sxs-lookup"><span data-stu-id="92389-126">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="92389-127">Ulna 是在 forearm 中找到的長型骨骼，會從肘形延伸到最小的手指。</span><span class="sxs-lookup"><span data-stu-id="92389-127">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="92389-128">以下是根據我們的探勘所建議的2個位置：</span><span class="sxs-lookup"><span data-stu-id="92389-128">Below are 2 recommended placements based on our explorations:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="92389-129">![Ulnar 的側邊位置](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="92389-129">![Ulnar side hand location](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="92389-130">**Ulnar 內部 palm**</span><span class="sxs-lookup"><span data-stu-id="92389-130">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="92389-131">這個位置是可靠的，因為手不會彼此重迭。</span><span class="sxs-lookup"><span data-stu-id="92389-131">This position is reliable because the hands do not overlap each other.</span></span> <span data-ttu-id="92389-132">這對於精確的手勢偵測和追蹤非常重要。</span><span class="sxs-lookup"><span data-stu-id="92389-132">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="92389-133">![Ulnar 的側邊位置](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="92389-133">![Ulnar side hand location](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="92389-134">**B. Ulnar 以上的手勢**</span><span class="sxs-lookup"><span data-stu-id="92389-134">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="92389-135">這個位置非常適合使用者，因為他們不需要使其 arm 太多而無法與功能表進行互動。</span><span class="sxs-lookup"><span data-stu-id="92389-135">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="92389-136">建議您將功能表**13cm**放在 palm 上方，並對齊 ulnar palm 內的按鈕。</span><span class="sxs-lookup"><span data-stu-id="92389-136">We recommend placing menus **13cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="92389-137">閱讀更多最佳按鈕大小</span><span class="sxs-lookup"><span data-stu-id="92389-137">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="92389-138">基於技術原因，我們建議您使用一個必要的實作為此位置：開發人員必須凍結功能表一次，使用者的手勢才會與之互動。</span><span class="sxs-lookup"><span data-stu-id="92389-138">For technical reasons we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="92389-139">這可避免 jitteriness 重迭手，同時也允許以更快的按鈕為目標。</span><span class="sxs-lookup"><span data-stu-id="92389-139">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="92389-140">HoloLens 2 攝影機會在彼此分開時識別正確的手。</span><span class="sxs-lookup"><span data-stu-id="92389-140">HoloLens 2 cameras identify hands accurately when they are separate from each other.</span></span> <span data-ttu-id="92389-141">任何重迭的手可能會導致手中的功能表遠離錨點位置。</span><span class="sxs-lookup"><span data-stu-id="92389-141">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a><span data-ttu-id="92389-142">不建議的功能表位置</span><span class="sxs-lookup"><span data-stu-id="92389-142">Menu positions that are not recommended</span></span>
<span data-ttu-id="92389-143">我們已使用不同的功能表配置和位置完成使用者研究，**不建議**使用下列功能表位置，尋找下列各項研究的缺點：</span><span class="sxs-lookup"><span data-stu-id="92389-143">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="92389-144">![上述 arm](images/AboveArm.gif)</span><span class="sxs-lookup"><span data-stu-id="92389-144">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="92389-145">**Arm 之上**</span><span class="sxs-lookup"><span data-stu-id="92389-145">**Above the arm**</span></span><br>
        <span data-ttu-id="92389-146">1-不容易維護良好的手追蹤</span><span class="sxs-lookup"><span data-stu-id="92389-146">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="92389-147">2-因非自然位置而造成使用者疲勞</span><span class="sxs-lookup"><span data-stu-id="92389-147">2 - Causes user fatigue due to unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="92389-148">![以上的手指](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="92389-148">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="92389-149">**上手指**</span><span class="sxs-lookup"><span data-stu-id="92389-149">**Above fingers**</span></span><br>
        <span data-ttu-id="92389-150">1-疲勞，因為有長時間的手中</span><span class="sxs-lookup"><span data-stu-id="92389-150">1 - Hand fatigue due to holding hand for long time</span></span><br>
        <span data-ttu-id="92389-151">2-追蹤索引和中間接頭的問題</span><span class="sxs-lookup"><span data-stu-id="92389-151">2 - Hand tracking issues on index and middle finger</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="92389-152">![上方的 palm](images/handCenter.gif)</span><span class="sxs-lookup"><span data-stu-id="92389-152">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="92389-153">**上方-中心 palm**</span><span class="sxs-lookup"><span data-stu-id="92389-153">**Above-center palm**</span></span><br>
        <span data-ttu-id="92389-154">1-因手迭而發生的追蹤問題</span><span class="sxs-lookup"><span data-stu-id="92389-154">1 - Hand tracking issues due to overlapping hands</span></span><br>
        <span data-ttu-id="92389-155">2-手疲勞，因為長期保持手，以便與功能表互動</span><span class="sxs-lookup"><span data-stu-id="92389-155">2 - Hand fatigue due to holding hands for long time in order to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="92389-156">![Top Fingertip](images/TopFingerTip.gif)**熱門 Fingertip**</span><span class="sxs-lookup"><span data-stu-id="92389-156">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="92389-157">1-手追蹤問題</span><span class="sxs-lookup"><span data-stu-id="92389-157">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="92389-158">2-手疲勞保持在正常狀態</span><span class="sxs-lookup"><span data-stu-id="92389-158">2 - Hand fatigue holding hand above normal posture</span></span><br>
        <span data-ttu-id="92389-159">3-因手指之間的空間有限而導致按下其他手指的按鈕時發生問題</span><span class="sxs-lookup"><span data-stu-id="92389-159">3 - Issues pressing buttons with other fingers by accident due to limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="92389-160">![Arm](images/BackOfTheArm.gif) 的背面</span><span class="sxs-lookup"><span data-stu-id="92389-160">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="92389-161">**Arm 背面**</span><span class="sxs-lookup"><span data-stu-id="92389-161">**Back of the arm**</span></span><br>
        <span data-ttu-id="92389-162">1-不小心可以觸發 [首頁] 按鈕</span><span class="sxs-lookup"><span data-stu-id="92389-162">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="92389-163">2-不是使用者的自然或舒適位置</span><span class="sxs-lookup"><span data-stu-id="92389-163">2 - Not a natural or comfortable position for users</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="92389-164">適用于 Unity 的 MRTK （混合現實工具組）中的手形功能表</span><span class="sxs-lookup"><span data-stu-id="92389-164">Hand menu in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="92389-165">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 提供快顯功能表的腳本和範例場景。</span><span class="sxs-lookup"><span data-stu-id="92389-165">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and example scenes for the hand menu.</span></span> <span data-ttu-id="92389-166">HandConstraintPalmUp 規劃求解腳本可讓您使用各種可設定的選項，輕鬆地將任何物件附加至手中。</span><span class="sxs-lookup"><span data-stu-id="92389-166">HandConstraintPalmUp solver script allows you easily attach any objects to the hands with various configurable options.</span></span>

* [<span data-ttu-id="92389-167">具有 HandConstraint 和 HandConstraintPalmUp 的 MRTK-手形功能表</span><span class="sxs-lookup"><span data-stu-id="92389-167">MRTK - Hand Menu with HandConstraint and HandConstraintPalmUp </span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup)


<br>

---


## <a name="see-also"></a><span data-ttu-id="92389-168">請參閱</span><span class="sxs-lookup"><span data-stu-id="92389-168">See also</span></span>

* [<span data-ttu-id="92389-169">游標</span><span class="sxs-lookup"><span data-stu-id="92389-169">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="92389-170">手部光線</span><span class="sxs-lookup"><span data-stu-id="92389-170">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="92389-171">Button</span><span class="sxs-lookup"><span data-stu-id="92389-171">Button</span></span>](button.md)
* [<span data-ttu-id="92389-172">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="92389-172">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="92389-173">週框方塊和應用程式列</span><span class="sxs-lookup"><span data-stu-id="92389-173">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="92389-174">操作</span><span class="sxs-lookup"><span data-stu-id="92389-174">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="92389-175">手部功能表</span><span class="sxs-lookup"><span data-stu-id="92389-175">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="92389-176">近端功能表</span><span class="sxs-lookup"><span data-stu-id="92389-176">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="92389-177">物件集合</span><span class="sxs-lookup"><span data-stu-id="92389-177">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="92389-178">語音命令</span><span class="sxs-lookup"><span data-stu-id="92389-178">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="92389-179">鍵盤</span><span class="sxs-lookup"><span data-stu-id="92389-179">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="92389-180">工具提示</span><span class="sxs-lookup"><span data-stu-id="92389-180">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="92389-181">平板</span><span class="sxs-lookup"><span data-stu-id="92389-181">Slate</span></span>](slate.md)
* [<span data-ttu-id="92389-182">滑桿</span><span class="sxs-lookup"><span data-stu-id="92389-182">Slider</span></span>](slider.md)
* [<span data-ttu-id="92389-183">著色器</span><span class="sxs-lookup"><span data-stu-id="92389-183">Shader</span></span>](shader.md)
* [<span data-ttu-id="92389-184">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="92389-184">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="92389-185">顯示進度</span><span class="sxs-lookup"><span data-stu-id="92389-185">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="92389-186">表面磁性</span><span class="sxs-lookup"><span data-stu-id="92389-186">Surface magnetism</span></span>](surface-magnetism.md)
