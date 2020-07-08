---
title: 手部功能表
description: 快顯功能表可讓使用者快速地為常用的函式帶出手動連接的 UI。 這些是我們的最佳做法和功能表的建議。
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: 手形、功能表、按鈕、快速存取、版面配置
ms.openlocfilehash: d1d15b36bab2ca2082ca4ba91b9c64862893f80c
ms.sourcegitcommit: fef42e2908e49822f2d13b05d2f9260bf0d72158
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "86061163"
---
# <a name="hand-menu"></a><span data-ttu-id="57a48-105">手部功能表</span><span class="sxs-lookup"><span data-stu-id="57a48-105">Hand menu</span></span>

![Ulnar 端位置](images/UX/UX_Hero_HandMenu.jpg)

<span data-ttu-id="57a48-107">[手形] 功能表是 HoloLens 2 中最獨特的 UX 模式之一。</span><span class="sxs-lookup"><span data-stu-id="57a48-107">The hand menu is one of the most unique UX patterns in HoloLens 2.</span></span> <span data-ttu-id="57a48-108">它可讓您快速啟動右手附的 UI。</span><span class="sxs-lookup"><span data-stu-id="57a48-108">It allows you to quickly bring up hand-attached UI.</span></span> <span data-ttu-id="57a48-109">因為它可隨時存取，而且可以輕鬆地顯示及隱藏，所以很適合用於快速動作。</span><span class="sxs-lookup"><span data-stu-id="57a48-109">Since it's accessible anytime and can be shown and hidden easily, it's great for quick actions.</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

<span data-ttu-id="57a48-110">您會在下面的清單中找到使用 [手形] 功能表的建議最佳作法。</span><span class="sxs-lookup"><span data-stu-id="57a48-110">You'll find our recommended best practices for working with hand menus in the list below.</span></span> <span data-ttu-id="57a48-111">您也可以在[MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)中找到示範 [手形] 功能表的範例場景。</span><span class="sxs-lookup"><span data-stu-id="57a48-111">You can also find an example scene demonstrating the hand menu in [MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html).</span></span>

<br>


---

## <a name="best-practices"></a><span data-ttu-id="57a48-112">最佳作法</span><span class="sxs-lookup"><span data-stu-id="57a48-112">Best practices</span></span>
<span data-ttu-id="57a48-113">**讓按鈕數目保持小**</span><span class="sxs-lookup"><span data-stu-id="57a48-113">**Keep the number of buttons small**</span></span> 

<span data-ttu-id="57a48-114">由於已鎖定的功能表和眼睛之間的距離，以及使用者傾向于隨時專注于相對較小的視覺區域（視覺效果的 attentional 錐形大約是10度），因此建議您將按鈕數目保持為小。</span><span class="sxs-lookup"><span data-stu-id="57a48-114">Due to the close distance between a hand-locked menu and the eyes and also the user's tendency to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="57a48-115">根據我們的探索，有三個按鈕的資料行，即使在使用者將其手移至 FOV 的中心時，也會將所有內容都保存在視野中（FOV）。</span><span class="sxs-lookup"><span data-stu-id="57a48-115">Based on our exploration, one column with three buttons works well by keeping all the content within the field of view (FOV) even when a user moves their hands to the center of the FOV.</span></span> 

<span data-ttu-id="57a48-116">**利用快顯功能表進行快速動作**</span><span class="sxs-lookup"><span data-stu-id="57a48-116">**Utilize hand menu for quick action**</span></span> 

<span data-ttu-id="57a48-117">引發 arm 並維護位置，很容易就會造成 arm 疲勞。</span><span class="sxs-lookup"><span data-stu-id="57a48-117">Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="57a48-118">針對需要短暫互動的功能表，使用手動鎖定的方法。</span><span class="sxs-lookup"><span data-stu-id="57a48-118">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="57a48-119">如果您的功能表很複雜，而且需要擴充的互動時間，請考慮改為使用世界鎖定或主體鎖定。</span><span class="sxs-lookup"><span data-stu-id="57a48-119">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="57a48-120">**按鈕/面板角度**</span><span class="sxs-lookup"><span data-stu-id="57a48-120">**Button / Panel angle**</span></span>

<span data-ttu-id="57a48-121">功能表應該以相反的肩和中間的方式來表示：這可讓自然手移動以相反的方式與功能表互動，並在觸及按鈕時避免任何不難或不舒服的位置。</span><span class="sxs-lookup"><span data-stu-id="57a48-121">Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="57a48-122">**考慮支援一次性或免手操作**</span><span class="sxs-lookup"><span data-stu-id="57a48-122">**Consider supporting one-handed or hands-free operation**</span></span>

<span data-ttu-id="57a48-123">請勿假設這兩個使用者都一律可以使用。</span><span class="sxs-lookup"><span data-stu-id="57a48-123">Do not assume both of the user's hands are always available.</span></span> <span data-ttu-id="57a48-124">當一或兩個手無法使用時，請考慮各種內容，並確定您的設計帳戶適用于這些情況。</span><span class="sxs-lookup"><span data-stu-id="57a48-124">Consider a wide range of contexts when one or both hands are not available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="57a48-125">若要支援單次功能表，您可以嘗試將功能表位置從 [手動鎖定] 轉換為 [世界鎖定] （當手翻轉時）。</span><span class="sxs-lookup"><span data-stu-id="57a48-125">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="57a48-126">針對無人參與的案例，請考慮使用語音命令來叫用快顯功能表。</span><span class="sxs-lookup"><span data-stu-id="57a48-126">For hands-free scenarios, consider using a voice command to invoke the hand menu.</span></span>

<span data-ttu-id="57a48-127">**避免在手腕（系統首頁按鈕）附近新增按鈕**</span><span class="sxs-lookup"><span data-stu-id="57a48-127">**Avoid adding buttons near the wrist (system home button)**</span></span>

<span data-ttu-id="57a48-128">如果功能表按鈕太靠近 [首頁] 按鈕，則在與 [滑鼠] 功能表互動時，可能會不小心觸發。</span><span class="sxs-lookup"><span data-stu-id="57a48-128">If the hand menu buttons are placed too close to the home button, it may accidentally trigger while interacting with the hand menu.</span></span>

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a><span data-ttu-id="57a48-129">具有大型和複雜 UI 控制項的快顯功能表</span><span class="sxs-lookup"><span data-stu-id="57a48-129">Hand menu with large and complex UI controls</span></span>
<img src="images/UX/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<span data-ttu-id="57a48-130">建議您限制在連接功能表上的按鈕或 UI 控制項數目。</span><span class="sxs-lookup"><span data-stu-id="57a48-130">It's recommended to limit the number of buttons or UI controls on hand-attached menus.</span></span> <span data-ttu-id="57a48-131">這是因為與大量 UI 元素的擴充互動可能會導致 arm 疲勞。</span><span class="sxs-lookup"><span data-stu-id="57a48-131">This is because extended interaction with a large number of UI elements can cause arm fatigue.</span></span> <span data-ttu-id="57a48-132">如果您的經驗需要大型功能表，請提供一種簡單的方式，讓使用者可以輕鬆地鎖定功能表。</span><span class="sxs-lookup"><span data-stu-id="57a48-132">If your experience requires a large menu, provide an easy way for the user to world lock the menu.</span></span> <span data-ttu-id="57a48-133">我們建議的一項技巧，就是在手離開或翻轉使用者時，將功能表向外鎖定。</span><span class="sxs-lookup"><span data-stu-id="57a48-133">One technique we recommend is to world-lock then menu when the hand drops or flips away from the user.</span></span> <span data-ttu-id="57a48-134">第二種方法是讓使用者直接抓取功能表。</span><span class="sxs-lookup"><span data-stu-id="57a48-134">A second technique is to allow the user to directly grab the menu with the other hand.</span></span> <span data-ttu-id="57a48-135">當使用者放開功能表時，功能表應該是「世界鎖定」。</span><span class="sxs-lookup"><span data-stu-id="57a48-135">When the user releases the menu, the menu should world lock.</span></span> <span data-ttu-id="57a48-136">如此一來，使用者可以在一段頗長的時間內輕鬆且放心地與各種 UI 專案互動。</span><span class="sxs-lookup"><span data-stu-id="57a48-136">This way, a user can interact with various UI elements comfortably and confidently over an extended period of time.</span></span> 

<span data-ttu-id="57a48-137">當功能表為 [世界鎖定] 時，請務必提供一種方式來移動功能表，並在不再需要時關閉功能表。</span><span class="sxs-lookup"><span data-stu-id="57a48-137">When the menu is world-locked, make sure to provide a way to move the menu, and close the menu when it's no longer needed.</span></span> <span data-ttu-id="57a48-138">藉由在功能表的側邊或頂端提供控點，讓功能表變成可移動。</span><span class="sxs-lookup"><span data-stu-id="57a48-138">Make the menu movable by providing handles on the sides or top of menu.</span></span> <span data-ttu-id="57a48-139">新增 [關閉] 按鈕以允許關閉功能表。</span><span class="sxs-lookup"><span data-stu-id="57a48-139">Add a close button to allow the menu to close.</span></span> <span data-ttu-id="57a48-140">[允許] 功能表在使用者手上臉部時，重新附加至手邊。</span><span class="sxs-lookup"><span data-stu-id="57a48-140">Allow for the menu to re-attach to the hand when the user hand faces the user.</span></span> <span data-ttu-id="57a48-141">我們也建議要求使用者 gazes，以防止啟用錯誤（請參閱下文）。</span><span class="sxs-lookup"><span data-stu-id="57a48-141">We also recommend requiring that the users gazes at their hand to prevent false activations (see below).</span></span>

<span data-ttu-id="57a48-142">**顯示可用性問題的大型功能表**</span><span class="sxs-lookup"><span data-stu-id="57a48-142">**Large menu that shows a usability issue**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

<span data-ttu-id="57a48-143">**在手上的世界鎖定功能表**</span><span class="sxs-lookup"><span data-stu-id="57a48-143">**World-locked menu on hand drop**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

<span data-ttu-id="57a48-144">**手動抓取 & 提取至世界-鎖定功能表**</span><span class="sxs-lookup"><span data-stu-id="57a48-144">**Manual grab & pull to world-lock the menu**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]


## <a name="how-to-prevent-false-activation"></a><span data-ttu-id="57a48-145">如何防止啟用錯誤</span><span class="sxs-lookup"><span data-stu-id="57a48-145">How to prevent false activation</span></span>

<span data-ttu-id="57a48-146">如果您只使用 palm 作為事件來觸發快顯功能表，它可能會在您不需要時意外出現（誤報），因為人們會刻意（用於通訊和物件操作）和無意地移動其手。</span><span class="sxs-lookup"><span data-stu-id="57a48-146">If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="57a48-147">若要減少錯誤的啟用，請新增一個額外的步驟，除了 palm 事件以外，叫用快顯功能表（例如完全開啟的手指，或使用者刻意撥雲見日的手勢）。</span><span class="sxs-lookup"><span data-stu-id="57a48-147">To reduce false activations, add an additional step besides the palm-up event to invoke the hand menu (such as fully opened fingers, or the user intentionally gazing at their hand).</span></span>

<span data-ttu-id="57a48-148">**需要一般 Palm**</span><span class="sxs-lookup"><span data-stu-id="57a48-148">**Require Flat Palm**</span></span>

<span data-ttu-id="57a48-149">藉由要求一般的開放式手勢，您可以防止在環境中進行通訊時，使用者操作物件或手勢時可能發生的錯誤啟用。</span><span class="sxs-lookup"><span data-stu-id="57a48-149">By requiring a flat open hand, you can prevent false activation that might occur as the user manipulates objects or gestures while communicating within an environment.</span></span> 

<span data-ttu-id="57a48-150">**需要注視**</span><span class="sxs-lookup"><span data-stu-id="57a48-150">**Require Gaze**</span></span>

<span data-ttu-id="57a48-151">藉由要求使用者注視（使用眼睛眼或列印頭），它會防止錯誤的啟用，因為使用者必須故意將他們的注意力直接導向至第二個啟動步驟（使用可微調的距離閾值來允許使用者輕鬆）。</span><span class="sxs-lookup"><span data-stu-id="57a48-151">By requiring the user to gaze at their hand (either with eye gaze or head gaze), it prevents false activations due to the user having to intentionally direct their attention to the hand as a secondary activation step (with a tunable distance threshold used to allow for user comfort).</span></span>  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="57a48-152">手形功能表位置最佳做法</span><span class="sxs-lookup"><span data-stu-id="57a48-152">Hand menu placement best practices</span></span>

<span data-ttu-id="57a48-153">在「人為剖析」中，ulnar nerve 是在 ulna 骨骼附近執行的 nerve。</span><span class="sxs-lookup"><span data-stu-id="57a48-153">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="57a48-154">Ulna 是在 forearm 中找到的長型骨骼，會從肘形延伸到最小的手指。</span><span class="sxs-lookup"><span data-stu-id="57a48-154">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="57a48-155">以下是根據我們的探勘所建議的2個位置：</span><span class="sxs-lookup"><span data-stu-id="57a48-155">Below are 2 recommended placements based on our explorations:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="57a48-156">![Ulnar 端位置](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="57a48-156">![Ulnar side hand location](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="57a48-157">**Ulnar 內部 palm**</span><span class="sxs-lookup"><span data-stu-id="57a48-157">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="57a48-158">這個位置是可靠的，因為手不會彼此重迭。</span><span class="sxs-lookup"><span data-stu-id="57a48-158">This position is reliable because the hands do not overlap each other.</span></span> <span data-ttu-id="57a48-159">這對於精確的手勢偵測和追蹤非常重要。</span><span class="sxs-lookup"><span data-stu-id="57a48-159">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="57a48-160">![Ulnar 端位置](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="57a48-160">![Ulnar side hand location](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="57a48-161">**B. Ulnar 以上的手勢**</span><span class="sxs-lookup"><span data-stu-id="57a48-161">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="57a48-162">這個位置非常適合使用者，因為他們不需要使其 arm 太多而無法與功能表進行互動。</span><span class="sxs-lookup"><span data-stu-id="57a48-162">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="57a48-163">建議您將功能表**13cm**放在 palm 上方，並對齊 ulnar palm 內的按鈕。</span><span class="sxs-lookup"><span data-stu-id="57a48-163">We recommend placing menus **13cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="57a48-164">閱讀更多最佳按鈕大小</span><span class="sxs-lookup"><span data-stu-id="57a48-164">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="57a48-165">基於技術原因，我們建議您使用一個必要的實作為此位置：開發人員必須凍結功能表一次，使用者的手勢才會與之互動。</span><span class="sxs-lookup"><span data-stu-id="57a48-165">For technical reasons we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="57a48-166">這可避免 jitteriness 重迭手，同時也允許以更快的按鈕為目標。</span><span class="sxs-lookup"><span data-stu-id="57a48-166">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="57a48-167">HoloLens 2 攝影機會在彼此分開時識別正確的手。</span><span class="sxs-lookup"><span data-stu-id="57a48-167">HoloLens 2 cameras identify hands accurately when they are separate from each other.</span></span> <span data-ttu-id="57a48-168">任何重迭的手可能會導致手中的功能表遠離錨點位置。</span><span class="sxs-lookup"><span data-stu-id="57a48-168">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a><span data-ttu-id="57a48-169">不建議的功能表位置</span><span class="sxs-lookup"><span data-stu-id="57a48-169">Menu positions that are not recommended</span></span>
<span data-ttu-id="57a48-170">我們已使用不同的功能表配置和位置完成使用者研究，**不建議**使用下列功能表位置，尋找下列各項研究的缺點：</span><span class="sxs-lookup"><span data-stu-id="57a48-170">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="57a48-171">![上方 arm](images/AboveArm.gif)</span><span class="sxs-lookup"><span data-stu-id="57a48-171">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="57a48-172">**Arm 之上**</span><span class="sxs-lookup"><span data-stu-id="57a48-172">**Above the arm**</span></span><br>
        <span data-ttu-id="57a48-173">1-不容易維護良好的手追蹤</span><span class="sxs-lookup"><span data-stu-id="57a48-173">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="57a48-174">2-因非自然位置而造成使用者疲勞</span><span class="sxs-lookup"><span data-stu-id="57a48-174">2 - Causes user fatigue due to unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="57a48-175">![上手指](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="57a48-175">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="57a48-176">**上手指**</span><span class="sxs-lookup"><span data-stu-id="57a48-176">**Above fingers**</span></span><br>
        <span data-ttu-id="57a48-177">1-手疲勞，因為有長時間保留手</span><span class="sxs-lookup"><span data-stu-id="57a48-177">1 - Hand fatigue due to holding out hand for a long time</span></span><br>
        <span data-ttu-id="57a48-178">2-追蹤索引和中間手指的問題</span><span class="sxs-lookup"><span data-stu-id="57a48-178">2 - Hand tracking issues on index and middle fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="57a48-179">![上方的 palm](images/handCenter.gif)</span><span class="sxs-lookup"><span data-stu-id="57a48-179">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="57a48-180">**上方-中心 palm**</span><span class="sxs-lookup"><span data-stu-id="57a48-180">**Above-center palm**</span></span><br>
        <span data-ttu-id="57a48-181">1-因手迭而發生的追蹤問題</span><span class="sxs-lookup"><span data-stu-id="57a48-181">1 - Hand tracking issues due to overlapping hands</span></span><br>
        <span data-ttu-id="57a48-182">2-手疲勞，因為長期保持手，以便與功能表互動</span><span class="sxs-lookup"><span data-stu-id="57a48-182">2 - Hand fatigue due to holding hands for long time in order to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="57a48-183">![熱門 Fingertip ](images/TopFingerTip.gif) **熱門 Fingertip**</span><span class="sxs-lookup"><span data-stu-id="57a48-183">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="57a48-184">1-手追蹤問題</span><span class="sxs-lookup"><span data-stu-id="57a48-184">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="57a48-185">2-從保持在正常狀態的手中疲勞</span><span class="sxs-lookup"><span data-stu-id="57a48-185">2 - Hand fatigue from holding hand above normal posture</span></span><br>
        <span data-ttu-id="57a48-186">3-因手指之間的空間有限而導致按下其他手指的按鈕時發生問題</span><span class="sxs-lookup"><span data-stu-id="57a48-186">3 - Issues pressing buttons with other fingers by accident due to limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="57a48-187">![Arm 背面](images/BackOfTheArm.gif)</span><span class="sxs-lookup"><span data-stu-id="57a48-187">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="57a48-188">**Arm 背面**</span><span class="sxs-lookup"><span data-stu-id="57a48-188">**Back of the arm**</span></span><br>
        <span data-ttu-id="57a48-189">1-不小心可以觸發 [首頁] 按鈕</span><span class="sxs-lookup"><span data-stu-id="57a48-189">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="57a48-190">2-不是自然或舒適的位置</span><span class="sxs-lookup"><span data-stu-id="57a48-190">2 - Not a natural or comfortable position</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="57a48-191">適用于 Unity 的 MRTK （混合現實工具組）中的手形功能表</span><span class="sxs-lookup"><span data-stu-id="57a48-191">Hand menu in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="57a48-192">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 提供快顯功能表的腳本和範例場景。</span><span class="sxs-lookup"><span data-stu-id="57a48-192">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and example scenes for the hand menu.</span></span> <span data-ttu-id="57a48-193">HandConstraintPalmUp 規劃求解腳本可讓您使用各種可設定的選項，將任何物件附加至手中。</span><span class="sxs-lookup"><span data-stu-id="57a48-193">The HandConstraintPalmUp solver script allows you to attach any objects to the hands with various configurable options.</span></span> <span data-ttu-id="57a48-194">MRTK 的功能表範例包含有用的選項，例如可防止啟用 false 的一般 palm 和注視需求。</span><span class="sxs-lookup"><span data-stu-id="57a48-194">MRTK's hand menu examples include useful options such as flat palm and gaze requirement for preventing false activation.</span></span>

* [<span data-ttu-id="57a48-195">手形功能表檔</span><span class="sxs-lookup"><span data-stu-id="57a48-195">Hand Menu Documentations</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)
* [<span data-ttu-id="57a48-196">手形功能表範例場景</span><span class="sxs-lookup"><span data-stu-id="57a48-196">Hand Menu Example Scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

<span data-ttu-id="57a48-197">您可以使用 MRTK 範例中樞應用程式來試用 HoloLens 2 中的功能表範例。</span><span class="sxs-lookup"><span data-stu-id="57a48-197">You can try hand menu examples in HoloLens 2 with MRTK Examples Hub app.</span></span> 
* [<span data-ttu-id="57a48-198">MRTK 範例中樞中的手形功能表場景</span><span class="sxs-lookup"><span data-stu-id="57a48-198">Hand Menu Scene in MRTK Examples Hub</span></span>](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---


## <a name="see-also"></a><span data-ttu-id="57a48-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57a48-199">See also</span></span>

* [<span data-ttu-id="57a48-200">游標</span><span class="sxs-lookup"><span data-stu-id="57a48-200">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="57a48-201">手部光線</span><span class="sxs-lookup"><span data-stu-id="57a48-201">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="57a48-202">Button</span><span class="sxs-lookup"><span data-stu-id="57a48-202">Button</span></span>](button.md)
* [<span data-ttu-id="57a48-203">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="57a48-203">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="57a48-204">週框方塊和應用程式列</span><span class="sxs-lookup"><span data-stu-id="57a48-204">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="57a48-205">操作</span><span class="sxs-lookup"><span data-stu-id="57a48-205">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="57a48-206">手部功能表</span><span class="sxs-lookup"><span data-stu-id="57a48-206">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="57a48-207">近端功能表</span><span class="sxs-lookup"><span data-stu-id="57a48-207">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="57a48-208">物件集合</span><span class="sxs-lookup"><span data-stu-id="57a48-208">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="57a48-209">語音命令</span><span class="sxs-lookup"><span data-stu-id="57a48-209">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="57a48-210">鍵盤</span><span class="sxs-lookup"><span data-stu-id="57a48-210">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="57a48-211">工具提示</span><span class="sxs-lookup"><span data-stu-id="57a48-211">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="57a48-212">平板</span><span class="sxs-lookup"><span data-stu-id="57a48-212">Slate</span></span>](slate.md)
* [<span data-ttu-id="57a48-213">滑桿</span><span class="sxs-lookup"><span data-stu-id="57a48-213">Slider</span></span>](slider.md)
* [<span data-ttu-id="57a48-214">著色器</span><span class="sxs-lookup"><span data-stu-id="57a48-214">Shader</span></span>](shader.md)
* [<span data-ttu-id="57a48-215">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="57a48-215">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="57a48-216">顯示進度</span><span class="sxs-lookup"><span data-stu-id="57a48-216">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="57a48-217">表面磁性</span><span class="sxs-lookup"><span data-stu-id="57a48-217">Surface magnetism</span></span>](surface-magnetism.md)
