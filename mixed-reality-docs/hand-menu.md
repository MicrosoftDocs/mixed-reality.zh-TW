---
title: 手形功能表
description: 快顯功能表可讓使用者快速地為常用的函式帶出手動連接的 UI。 這些是我們的最佳做法和功能表的建議。
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: 手形、功能表、按鈕、快速存取、版面配置
ms.openlocfilehash: ee958806ac462535b33164bb4faa4bf1aa29e709
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439249"
---
# <a name="hand-menu"></a><span data-ttu-id="21073-105">手形功能表</span><span class="sxs-lookup"><span data-stu-id="21073-105">Hand menu</span></span>

![Ulnar 端位置](images/MRTK_UX_HandMenu.png)

<span data-ttu-id="21073-107">快顯功能表可讓使用者快速地為常用的函式帶出手動連接的 UI。</span><span class="sxs-lookup"><span data-stu-id="21073-107">Hand menus allow users to quickly bring up hand-attached UI for frequently used functions.</span></span> 

<span data-ttu-id="21073-108">以下是我們在功能表中找到的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="21073-108">Below are the best practices we have found for hand menus.</span></span> <span data-ttu-id="21073-109">您也可以在[MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup)中找到示範 [手形] 功能表的範例場景。</span><span class="sxs-lookup"><span data-stu-id="21073-109">You can also find an example scene demonstrating the hand menu in [MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup).</span></span>

<br>

---

## <a name="behavior-best-practices"></a><span data-ttu-id="21073-110">行為最佳做法</span><span class="sxs-lookup"><span data-stu-id="21073-110">Behavior best practices</span></span>
<span data-ttu-id="21073-111">**答：將按鈕數目保持**在最小的範圍 . 因為手鎖住的功能表和眼睛之間的距離，以及使用者傾向于隨時專注于相對較小的視覺區域（視覺的 attentional 錐形大約是10度），我們建議讓按鈕數目保持小。</span><span class="sxs-lookup"><span data-stu-id="21073-111">**A. Keep the number of buttons small:** Due to the close distance between a hand-locked menu and the eyes and also the user's tendency to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="21073-112">根據我們的探索，即使使用者將其手移至 FOV 的中心，還有三個按鈕的資料行，都能妥善運作。</span><span class="sxs-lookup"><span data-stu-id="21073-112">Based on our exploration, one column with three buttons work well by keeping all the content within the field of view (FOV) even when users move their hands to the center of the FOV.</span></span> 

<span data-ttu-id="21073-113">**B. 利用快顯功能表進行快速動作：** 引發 arm 並維護位置，很容易就會造成 arm 疲勞。</span><span class="sxs-lookup"><span data-stu-id="21073-113">**B. Utilize hand menu for quick action:** Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="21073-114">針對需要短暫互動的功能表，使用手動鎖定的方法。</span><span class="sxs-lookup"><span data-stu-id="21073-114">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="21073-115">如果您的功能表很複雜，而且需要擴充的互動時間，請考慮改為使用世界鎖定或主體鎖定。</span><span class="sxs-lookup"><span data-stu-id="21073-115">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="21073-116">**C. 按鈕/面板角度：** 功能表應朝向相反的肩和中間點：這可讓自然手移動以相反的方式與功能表互動，並避免觸及時的任何笨拙或不舒服的位置。滑鼠鍵.</span><span class="sxs-lookup"><span data-stu-id="21073-116">**C. Button / Panel angle:** Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="21073-117">**D. 考慮支援一次性或無人參與**的作業：不假設這兩個使用者都一律可以使用。</span><span class="sxs-lookup"><span data-stu-id="21073-117">**D. Consider supporting one-handed or hands-free operation:** Do not assume both of the user's hands are always available.</span></span> <span data-ttu-id="21073-118">當一或兩個手無法使用時，請考慮各種內容，並確定您的設計帳戶適用于這些情況。</span><span class="sxs-lookup"><span data-stu-id="21073-118">Consider a wide range of contexts when one or both hands are not available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="21073-119">若要支援單次功能表，您可以嘗試將功能表位置從 [手動鎖定] 轉換為 [世界鎖定] （當手翻轉時）。</span><span class="sxs-lookup"><span data-stu-id="21073-119">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="21073-120">針對無人參與的情況，請考慮使用語音命令來叫用快顯功能表按鈕。</span><span class="sxs-lookup"><span data-stu-id="21073-120">For hands-free scenarios, consider using a voice command to invoke the hand menu buttons.</span></span>

<span data-ttu-id="21073-121">**E. 兩步驟的**叫用：如果您只使用 palm 作為事件來觸發快顯功能表，當您不需要時，可能會不小心出現這種情況，因為人們會刻意移動，以進行通訊和物件操作和不小心。</span><span class="sxs-lookup"><span data-stu-id="21073-121">**E. Two-step invocation:** If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands a lot both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="21073-122">如果您的應用程式中遇到誤報，請考慮新增額外的步驟（除了 palm 事件以外），以叫用右手邊的功能表，例如完全開啟的手指。</span><span class="sxs-lookup"><span data-stu-id="21073-122">If you experience false-positives in your app, consider adding an additional step besides the palm-up event to invoke the hand menu such as fully opened fingers.</span></span>

<span data-ttu-id="21073-123">**F. 避免在手腕（系統首頁按鈕）附近新增按鈕：** 如果功能表按鈕太靠近 [首頁] 按鈕，則在與 [快顯功能表] 互動時，可能會意外觸發。</span><span class="sxs-lookup"><span data-stu-id="21073-123">**F. Avoid adding buttons near the wrist (system home button):** If the hand menu buttons are placed too close to the home button, it may get accidentally triggered while interacting with the hand menu.</span></span>

<span data-ttu-id="21073-124">**G. 測試、測試、測試：** 人員有不同的主體，而且有不同的臨界值來緩和和 discomfort 等等。請務必測試您的設計，並取得來自各種人的意見反應。</span><span class="sxs-lookup"><span data-stu-id="21073-124">**G. Test, test, test:** People have different bodies, with different thresholds for comfort and discomfort, etc. Be sure to test out your design on and get feedback from a variety of people.</span></span>

<br>

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="21073-125">手形功能表位置最佳做法</span><span class="sxs-lookup"><span data-stu-id="21073-125">Hand menu placement best practices</span></span>

<span data-ttu-id="21073-126">在「人為剖析」中，ulnar nerve 是在 ulna 骨骼附近執行的 nerve。</span><span class="sxs-lookup"><span data-stu-id="21073-126">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="21073-127">Ulna 是在 forearm 中找到的長型骨骼，會從肘形延伸到最小的手指。</span><span class="sxs-lookup"><span data-stu-id="21073-127">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="21073-128">以下是根據我們的探勘所建議的2個位置：</span><span class="sxs-lookup"><span data-stu-id="21073-128">Below are 2 recommended placements based on our explorations:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="21073-129">![Ulnar 的側邊位置](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="21073-129">![Ulnar side hand location](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="21073-130">**Ulnar 內部 palm**</span><span class="sxs-lookup"><span data-stu-id="21073-130">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="21073-131">這個位置是可靠的，因為手不會彼此重迭。</span><span class="sxs-lookup"><span data-stu-id="21073-131">This position is reliable because the hands do not overlap each other.</span></span> <span data-ttu-id="21073-132">這對於精確的手勢偵測和追蹤非常重要。</span><span class="sxs-lookup"><span data-stu-id="21073-132">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="21073-133">![Ulnar 的側邊位置](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="21073-133">![Ulnar side hand location](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="21073-134">**B. Ulnar 以上的手勢**</span><span class="sxs-lookup"><span data-stu-id="21073-134">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="21073-135">這個位置非常適合使用者，因為他們不需要使其 arm 太多而無法與功能表進行互動。</span><span class="sxs-lookup"><span data-stu-id="21073-135">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="21073-136">建議您將功能表**13cm**放在 palm 上方，並對齊 ulnar palm 內的按鈕。</span><span class="sxs-lookup"><span data-stu-id="21073-136">We recommend placing menus **13cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="21073-137">閱讀更多最佳按鈕大小</span><span class="sxs-lookup"><span data-stu-id="21073-137">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="21073-138">基於技術原因，我們建議您使用一個必要的實作為此位置：開發人員必須凍結功能表一次，使用者的手勢才會與之互動。</span><span class="sxs-lookup"><span data-stu-id="21073-138">For technical reasons we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="21073-139">這可避免 jitteriness 重迭手，同時也允許以更快的按鈕為目標。</span><span class="sxs-lookup"><span data-stu-id="21073-139">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="21073-140">HoloLens 2 攝影機會在彼此分開時識別正確的手。</span><span class="sxs-lookup"><span data-stu-id="21073-140">HoloLens 2 cameras identify hands accurately when they are separate from each other.</span></span> <span data-ttu-id="21073-141">任何重迭的手可能會導致手中的功能表遠離錨點位置。</span><span class="sxs-lookup"><span data-stu-id="21073-141">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a><span data-ttu-id="21073-142">不建議的功能表位置</span><span class="sxs-lookup"><span data-stu-id="21073-142">Menu positions that are not recommended</span></span>
<span data-ttu-id="21073-143">我們已使用不同的功能表配置和位置完成使用者研究，**不建議**使用下列功能表位置，尋找下列各項研究的缺點：</span><span class="sxs-lookup"><span data-stu-id="21073-143">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="21073-144">![上述 arm](images/AboveArm.gif)</span><span class="sxs-lookup"><span data-stu-id="21073-144">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="21073-145">**Arm 之上**</span><span class="sxs-lookup"><span data-stu-id="21073-145">**Above the arm**</span></span><br>
        <span data-ttu-id="21073-146">1-不容易維護良好的手追蹤</span><span class="sxs-lookup"><span data-stu-id="21073-146">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="21073-147">2-因非自然位置而造成使用者疲勞</span><span class="sxs-lookup"><span data-stu-id="21073-147">2 - Causes user fatigue due to unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="21073-148">![以上的手指](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="21073-148">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="21073-149">**上手指**</span><span class="sxs-lookup"><span data-stu-id="21073-149">**Above fingers**</span></span><br>
        <span data-ttu-id="21073-150">1-疲勞，因為有長時間的手中</span><span class="sxs-lookup"><span data-stu-id="21073-150">1 - Hand fatigue due to holding hand for long time</span></span><br>
        <span data-ttu-id="21073-151">2-追蹤索引和中間接頭的問題</span><span class="sxs-lookup"><span data-stu-id="21073-151">2 - Hand tracking issues on index and middle finger</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="21073-152">![上方的 palm](images/handCenter.gif)</span><span class="sxs-lookup"><span data-stu-id="21073-152">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="21073-153">**上方-中心 palm**</span><span class="sxs-lookup"><span data-stu-id="21073-153">**Above-center palm**</span></span><br>
        <span data-ttu-id="21073-154">1-因手迭而發生的追蹤問題</span><span class="sxs-lookup"><span data-stu-id="21073-154">1 - Hand tracking issues due to overlapping hands</span></span><br>
        <span data-ttu-id="21073-155">2-手疲勞，因為長期保持手，以便與功能表互動</span><span class="sxs-lookup"><span data-stu-id="21073-155">2 - Hand fatigue due to holding hands for long time in order to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="21073-156">![Top Fingertip](images/TopFingerTip.gif)**熱門 Fingertip**</span><span class="sxs-lookup"><span data-stu-id="21073-156">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="21073-157">1-手追蹤問題</span><span class="sxs-lookup"><span data-stu-id="21073-157">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="21073-158">2-手疲勞保持在正常狀態</span><span class="sxs-lookup"><span data-stu-id="21073-158">2 - Hand fatigue holding hand above normal posture</span></span><br>
        <span data-ttu-id="21073-159">3-因手指之間的空間有限而導致按下其他手指的按鈕時發生問題</span><span class="sxs-lookup"><span data-stu-id="21073-159">3 - Issues pressing buttons with other fingers by accident due to limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="21073-160">![Arm](images/BackOfTheArm.gif) 的背面</span><span class="sxs-lookup"><span data-stu-id="21073-160">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="21073-161">**Arm 背面**</span><span class="sxs-lookup"><span data-stu-id="21073-161">**Back of the arm**</span></span><br>
        <span data-ttu-id="21073-162">1-不小心可以觸發 [首頁] 按鈕</span><span class="sxs-lookup"><span data-stu-id="21073-162">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="21073-163">2-不是使用者的自然或舒適位置</span><span class="sxs-lookup"><span data-stu-id="21073-163">2 - Not a natural or comfortable position for users</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---


## <a name="see-also"></a><span data-ttu-id="21073-164">請參閱</span><span class="sxs-lookup"><span data-stu-id="21073-164">See also</span></span>

* [<span data-ttu-id="21073-165">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="21073-165">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="21073-166">手部直接操作</span><span class="sxs-lookup"><span data-stu-id="21073-166">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="21073-167">手部和運動控制器</span><span class="sxs-lookup"><span data-stu-id="21073-167">Hands and motion controllers</span></span>](hands-and-tools.md)
