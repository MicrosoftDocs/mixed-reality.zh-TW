---
title: 頭部注視並佇留
description: 頭部注視並佇留輸入模型的概觀
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
keywords: Mixed Reality, 注視, 佇留, 互動, 設計
ms.openlocfilehash: 6d209d3cc91ceecb4b9feef2925f093288c9f8ac
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439309"
---
# <a name="head-gaze-and-dwell"></a><span data-ttu-id="1d70f-104">頭部注視並佇留</span><span class="sxs-lookup"><span data-stu-id="1d70f-104">Head-gaze and dwell</span></span>

<span data-ttu-id="1d70f-105">當手上拿著工具和組件時，手勢可以很繁瑣或不可能進行。</span><span class="sxs-lookup"><span data-stu-id="1d70f-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="1d70f-106">語音命令 (例如手勢) 在特定情境 (例如極度喧噪的情況) 中可能不大可靠。</span><span class="sxs-lookup"><span data-stu-id="1d70f-106">Voice commands, like gestures, can be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="1d70f-107">此外，使用語音來控制電腦並不十分普遍，但的確可取得資料流！</span><span class="sxs-lookup"><span data-stu-id="1d70f-107">Additionally, using voice to control computers isn't universally common, but it certainly is gaining steam!</span></span> <span data-ttu-id="1d70f-108">「頭部注視並佇留」提供最熟悉且容易掌握的機制，可在 HoloLens 上以抬頭和免持式運作。</span><span class="sxs-lookup"><span data-stu-id="1d70f-108">Head-gaze and dwell offers the most familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="1d70f-109">此外，「頭部注視並佇留」 100% 可靠，完全不受雜訊干擾，而且在作業環境中也沒有靜音限制。</span><span class="sxs-lookup"><span data-stu-id="1d70f-109">Additionally, head-gaze and dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="scenarios"></a><span data-ttu-id="1d70f-110">案例</span><span class="sxs-lookup"><span data-stu-id="1d70f-110">Scenarios</span></span>

<span data-ttu-id="1d70f-111">列印頭和停留擅長在某人的手中與其他工作忙碌的案例中，而且因為環境或社交條件約束，所以語音不是100% 可靠或無法使用。</span><span class="sxs-lookup"><span data-stu-id="1d70f-111">Head-gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or available due to environmental or social constraints.</span></span> <span data-ttu-id="1d70f-112">穿戴 HoloLens 的人員在修理汽車引擎時覆疊參考資訊就是個不錯的範例。</span><span class="sxs-lookup"><span data-stu-id="1d70f-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="1d70f-113">他們的雙手忙著拿起工具，或在靠向引擎室時支撐其身體。</span><span class="sxs-lookup"><span data-stu-id="1d70f-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="1d70f-114">車庫空間很吵雜，充斥著工具的碰撞和唧唧聲，讓語音命令變得難以使用。</span><span class="sxs-lookup"><span data-stu-id="1d70f-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="1d70f-115">列印頭和停留可讓使用 HoloLens 的人安心地流覽其參考資料，而不會中斷工作流程。</span><span class="sxs-lookup"><span data-stu-id="1d70f-115">Head-gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="1d70f-116">裝置支援</span><span class="sxs-lookup"><span data-stu-id="1d70f-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1d70f-117"><strong>輸入模型</strong></span><span class="sxs-lookup"><span data-stu-id="1d70f-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="1d70f-118"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="1d70f-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="1d70f-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="1d70f-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="1d70f-120"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="1d70f-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1d70f-121">頭部注視並佇留</span><span class="sxs-lookup"><span data-stu-id="1d70f-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="1d70f-122">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="1d70f-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="1d70f-123">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="1d70f-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="1d70f-124">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="1d70f-124">✔️ Recommended</span></span></td>
    </tr>
</table>


## <a name="design-principles"></a><span data-ttu-id="1d70f-125">設計原則</span><span class="sxs-lookup"><span data-stu-id="1d70f-125">Design principles</span></span>

<span data-ttu-id="1d70f-126">**避免「注視武器」**</span><span class="sxs-lookup"><span data-stu-id="1d70f-126">**Avoid "Gaze as a weapon"**</span></span>

<span data-ttu-id="1d70f-127">「頭部注視並佇留」需要直覺式視覺化回饋，但是太多回饋可能會引起焦慮。</span><span class="sxs-lookup"><span data-stu-id="1d70f-127">Head-gaze and dwell requires visual feedback to be intuitive, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="1d70f-128">回饋應協助使用者知道他們所定向的目標，但不會針對其意圖予以自動選取。</span><span class="sxs-lookup"><span data-stu-id="1d70f-128">The feedback should help a user know what they're targeting, but not auto-select it against their intent.</span></span> <span data-ttu-id="1d70f-129">讀取文字、圖示和標籤需要額外的考量，在選取之前為人員提供吸收資訊的空間。</span><span class="sxs-lookup"><span data-stu-id="1d70f-129">Reading text, icons, and labels requires extra consideration to provide a person room to absorb the information before selecting.</span></span>
    
<span data-ttu-id="1d70f-130">**搜尋 Goldilocks 速度**</span><span class="sxs-lookup"><span data-stu-id="1d70f-130">**Seek Goldilocks speed**</span></span>
    
<span data-ttu-id="1d70f-131">佇留互動可根據瀏覽的影響而有不同的計時器 - 較多常用功能通常受益於更快速的填滿時間，而較多衍生性功能則可受益於較長的填滿時間。</span><span class="sxs-lookup"><span data-stu-id="1d70f-131">Dwell interactions can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="1d70f-132">使用填滿效果來顯示這些計時器時，填滿色彩的動畫曲線對於較快速填滿時間的感覺有正面影響。</span><span class="sxs-lookup"><span data-stu-id="1d70f-132">When using a fill-effect to show these timers, animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="1d70f-133">應可慮讓使用者決定快速/中等/緩慢填滿速度覆寫。</span><span class="sxs-lookup"><span data-stu-id="1d70f-133">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
<span data-ttu-id="1d70f-134">**假設不是-yo 的效果**</span><span class="sxs-lookup"><span data-stu-id="1d70f-134">**Say no-no to yo-yo effect**</span></span>

<span data-ttu-id="1d70f-135">溜溜球效應是當內容和「頭部注視並佇留」控制項的放置方式強迫人們要不斷地重複仰視和俯視時，可能出現的不舒適頭部移動模式。</span><span class="sxs-lookup"><span data-stu-id="1d70f-135">The yo-yo effect is an uncomfortable pattern of head movement that can emerge when the placement of content and head-gaze and dwell controls forces people to constantly look up and down repeatedly.</span></span> <span data-ttu-id="1d70f-136">例如，底部有 [中] 和 [停留] 按鈕的清單導覽，會引發一個迴圈，並顯示 [停留]、[查看結果]、[停留于]、[停止顯示] 等等。這個產生的模式不舒服，應避免將導覽控制項放在需要較少來回的集中式位置。</span><span class="sxs-lookup"><span data-stu-id="1d70f-136">For example, a list nav with the head-gaze and dwell button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, etc. This resulting pattern is uncomfortable and should be avoided by placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="1d70f-137">與效應相關的佇留按鈕放置方式，對於舒適度而言很重要。</span><span class="sxs-lookup"><span data-stu-id="1d70f-137">Placement of dwell buttons relative to their effects becomes important for comfort.</span></span>

<br>

---


## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="1d70f-138">UX 指導方針和最佳作法</span><span class="sxs-lookup"><span data-stu-id="1d70f-138">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="1d70f-139">目標大小</span><span class="sxs-lookup"><span data-stu-id="1d70f-139">Target sizes</span></span>
  <span data-ttu-id="1d70f-140">為了方便存取，頭眼和停留目標必須夠大，才能輕鬆查看，並在指定的時間在目標上保留一部穩定的標頭。</span><span class="sxs-lookup"><span data-stu-id="1d70f-140">To be easily accessible, head-gaze and dwell targets need to be large enough to comfortably look at, and hold one's head stable on the target for the prescribed time.</span></span> <span data-ttu-id="1d70f-141">我們建議的最小目標大小為2度，以達到最舒適的體驗。</span><span class="sxs-lookup"><span data-stu-id="1d70f-141">We recommend a minimum target size of 2 degrees to achieve the most comfortable experience.</span></span> 

### <a name="visual-feedback"></a><span data-ttu-id="1d70f-142">視覺回饋</span><span class="sxs-lookup"><span data-stu-id="1d70f-142">Visual feedback</span></span>

<span data-ttu-id="1d70f-143">使用放射狀填滿來表示佇留計時器時，從按鈕中心開始。</span><span class="sxs-lookup"><span data-stu-id="1d70f-143">When using a radial fill to represent the dwell timer, start from the center of button.</span></span> <span data-ttu-id="1d70f-144">相較於不同按鈕上的所有不同方向，一致的回應比較不容易混淆。</span><span class="sxs-lookup"><span data-stu-id="1d70f-144">A consistent response is less confusing than all different directions on different buttons.</span></span> 

  * <span data-ttu-id="1d70f-145">有方向的互動 (例如，向上/向下/左/右瀏覽等) 可以打破此規則。</span><span class="sxs-lookup"><span data-stu-id="1d70f-145">This rule can be broken though for directional interactions (e.g., nav up/down/left/right, etc.).</span></span> <span data-ttu-id="1d70f-146">例如，Microsoft Dynamics 365 Guides 讓「下一頁/上一頁」成為左右填滿則屬例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1d70f-146">For example, Microsoft Dynamics 365 Guides makes an exception on NEXT/BACK being left right fills.</span></span>
  * <span data-ttu-id="1d70f-147">在關閉按鈕等情境下，請考慮從外部反轉放射狀填滿。</span><span class="sxs-lookup"><span data-stu-id="1d70f-147">Consider inverting radial fill from outside, for scenarios like toggling a button off.</span></span> <span data-ttu-id="1d70f-148">按壓按鈕的反向感覺是可維護的良好視覺模式。</span><span class="sxs-lookup"><span data-stu-id="1d70f-148">The inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="1d70f-149">漸進式揭露</span><span class="sxs-lookup"><span data-stu-id="1d70f-149">Progressive disclosure</span></span>

<span data-ttu-id="1d70f-150">漸進式揭露表示只有盡可能詳細顯示與互動的每個階段相關。</span><span class="sxs-lookup"><span data-stu-id="1d70f-150">Progressive disclosure means only showing as much detail as is relevant at each stage of an interaction.</span></span> <span data-ttu-id="1d70f-151">對於佇留，這表示佇留目標會顯現於醒目提示 (例如，在清單控制項中)。</span><span class="sxs-lookup"><span data-stu-id="1d70f-151">For dwell, that means the dwell target is revealed on highlight (e.g., in a list control).</span></span>

 ### <a name="oversized-targets"></a><span data-ttu-id="1d70f-152">過大的目標</span><span class="sxs-lookup"><span data-stu-id="1d70f-152">Oversized targets</span></span>
<span data-ttu-id="1d70f-153">佇留區域可大於非使用中的圖示，使其更容易使用，例如 Microsoft Dynamics 365 Guides 中的 [上一頁] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1d70f-153">Dwell region can be larger than inactive icon to make it easier to use, like the Back button in Microsoft Dynamics 365 Guides.</span></span>

### <a name="prevent-flickering-with-delayed-feedback"></a><span data-ttu-id="1d70f-154">使用延遲回饋防止閃爍</span><span class="sxs-lookup"><span data-stu-id="1d70f-154">Prevent flickering with delayed feedback</span></span>
<span data-ttu-id="1d70f-155">在開始視覺化回饋前使用短暫延遲，可避免有人經過佇留目標時發生閃爍。</span><span class="sxs-lookup"><span data-stu-id="1d70f-155">Use a short delay before starting visual feedback to avoid flickering when someone passes over a dwell target.</span></span>
* <span data-ttu-id="1d70f-156">對於經常互動的按鈕，請讓延遲變得非常短，讓應用程式感覺為被動。</span><span class="sxs-lookup"><span data-stu-id="1d70f-156">For buttons interacted with frequently, keep the delay very short so the application feels reactive.</span></span>
* <span data-ttu-id="1d70f-157">對於不常進行互動的按鈕，較長的延遲可能會適當地避免介面感覺 twitchy。</span><span class="sxs-lookup"><span data-stu-id="1d70f-157">For buttons that are interacted with infrequently, a longer delay can be appropriate to avoid the interface feeling twitchy.</span></span>


<br>

---

## <a name="ui-patterns"></a><span data-ttu-id="1d70f-158">UI 模式</span><span class="sxs-lookup"><span data-stu-id="1d70f-158">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="1d70f-159">高頻率按鈕</span><span class="sxs-lookup"><span data-stu-id="1d70f-159">High frequency buttons</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="1d70f-160">高頻率按鈕是常用於整個應用程式的按鈕。</span><span class="sxs-lookup"><span data-stu-id="1d70f-160">High frequency buttons are buttons that are used commonly throughout an application.</span></span> <span data-ttu-id="1d70f-161">Microsoft Dynamics 365 Guides 中的下一頁和上一頁按鈕都是不錯的範例。</span><span class="sxs-lookup"><span data-stu-id="1d70f-161">A good example of these are the next and back buttons in Microsoft Dynamics 365 Guides.</span></span><br>
        <br>
        <span data-ttu-id="1d70f-162">**相關**</span><span class="sxs-lookup"><span data-stu-id="1d70f-162">**Recommendations**</span></span><br>
  * <span data-ttu-id="1d70f-163">高頻率的按鈕應該很大，使用 head</span><span class="sxs-lookup"><span data-stu-id="1d70f-163">High frequency buttons should be large, easier to hit with head-gaze</span></span>
  * <span data-ttu-id="1d70f-164">保持近乎眼的高度，以避免人體工學。</span><span class="sxs-lookup"><span data-stu-id="1d70f-164">Stay near eye height to avoid ergonomic straining.</span></span><br>
        <br>
<span data-ttu-id="1d70f-165">*影像： Microsoft Dynamics 365 guide [下一步] 按鈕*</span><span class="sxs-lookup"><span data-stu-id="1d70f-165">*Image: Microsoft Dynamics 365 Guides next button*</span></span>
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 指南 [下一步] 按鈕](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a><span data-ttu-id="1d70f-167">低頻率按鈕</span><span class="sxs-lookup"><span data-stu-id="1d70f-167">Low frequency buttons</span></span>
<span data-ttu-id="1d70f-168">低頻率按鈕是整個應用程式中不會定期互動的按鈕。</span><span class="sxs-lookup"><span data-stu-id="1d70f-168">Low frequency buttons are buttons that are not interacted with as regularly throughout the application.</span></span> <span data-ttu-id="1d70f-169">可存取 [設定] 功能表的按鈕，或可清除所有工作的按鈕都是不錯的範例。</span><span class="sxs-lookup"><span data-stu-id="1d70f-169">A good example might be a button to access the settings menu, or a button to clear all work.</span></span>

* <span data-ttu-id="1d70f-170">嘗試讓這些按鈕不在常用的頭部注視路徑中，以免意外啟動。</span><span class="sxs-lookup"><span data-stu-id="1d70f-170">Try to keep these buttons out of the way of frequent head-gaze paths to avoid accidental activation.</span></span> 

<br>

---

### <a name="confirmations"></a><span data-ttu-id="1d70f-171">確認</span><span class="sxs-lookup"><span data-stu-id="1d70f-171">Confirmations</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="1d70f-172">當某個動作有重大影響時 (例如收費、刪除工作或開始長時間處理)，最好確認個人要選取按鈕。</span><span class="sxs-lookup"><span data-stu-id="1d70f-172">When an action has significant impact, like charging money, deleting work, or starting a long process, it is useful to confirm that a person meant to select a button.</span></span><br>
        <br>
        <span data-ttu-id="1d70f-173">**相關**</span><span class="sxs-lookup"><span data-stu-id="1d70f-173">**Recommendations**</span></span><br>
  * <span data-ttu-id="1d70f-174">在主要按鈕上顯示選取醒目提示。</span><span class="sxs-lookup"><span data-stu-id="1d70f-174">Show selection highlight on main button.</span></span>
  * <span data-ttu-id="1d70f-175">與選取醒目提示同時顯示佇留目標。</span><span class="sxs-lookup"><span data-stu-id="1d70f-175">Reveal dwell target at same time as selection highlight.</span></span>
  * <span data-ttu-id="1d70f-176">對於次要按鈕，顯示頭部注視的佇留目標。</span><span class="sxs-lookup"><span data-stu-id="1d70f-176">For the secondary button, reveal the dwell target on head-gaze.</span></span><br>
        <br>
<span data-ttu-id="1d70f-177">*影像： Microsoft Dynamics 365 指南確認對話方塊*</span><span class="sxs-lookup"><span data-stu-id="1d70f-177">*Image: Microsoft Dynamics 365 Guides confirmation dialog*</span></span>
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 指南確認對話方塊](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a><span data-ttu-id="1d70f-179">切換按鈕</span><span class="sxs-lookup"><span data-stu-id="1d70f-179">Toggle buttons</span></span>
<span data-ttu-id="1d70f-180">切換按鈕需要一些微妙的邏輯，才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="1d70f-180">Toggle buttons require some nuanced logic to work properly.</span></span> <span data-ttu-id="1d70f-181">當人員佇留在切換按鈕並啟動它時，他們需要結束按鈕，然後回頭重新啟動佇留邏輯。</span><span class="sxs-lookup"><span data-stu-id="1d70f-181">When a person dwells on a toggle button and actives it, they need to exit the button and then return to restart the dwell logic.</span></span> <span data-ttu-id="1d70f-182">切換按鈕會有清楚的作用與非作用中狀態很重要。</span><span class="sxs-lookup"><span data-stu-id="1d70f-182">It is important that togglable buttons have a clear active versus inactive state.</span></span> 

<br>

---

### <a name="list-views"></a><span data-ttu-id="1d70f-183">清單檢視</span><span class="sxs-lookup"><span data-stu-id="1d70f-183">List views</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="1d70f-184">清單視圖會針對 head 注視和停留輸入呈現特定挑戰。</span><span class="sxs-lookup"><span data-stu-id="1d70f-184">List views present a particular challenge for head-gaze and dwell input.</span></span> <span data-ttu-id="1d70f-185">人們需要能夠掃描內容，而不覺得必須偷偷摸摸地環顧佇留目標。</span><span class="sxs-lookup"><span data-stu-id="1d70f-185">People need to be able to scan the content without feeling like that have to tiptoe around the dwell targets.</span></span><br>
        <br>
<span data-ttu-id="1d70f-186">**相關**</span><span class="sxs-lookup"><span data-stu-id="1d70f-186">**Recommendations**</span></span><br>
  * <span data-ttu-id="1d70f-187">當 head gazed 時，會將整個資料列醒目提示，但不會開始停留，除非您在特定的停留目標上出現 head 注視。</span><span class="sxs-lookup"><span data-stu-id="1d70f-187">Have the entire row highlight when head-gazed but doesn’t begin dwell unless head-gaze is on the specific dwell target.</span></span>
  * <span data-ttu-id="1d70f-188">只有在資料列反白顯示時，才會顯示停留目標，以在視覺效果雜訊上減少。</span><span class="sxs-lookup"><span data-stu-id="1d70f-188">Only show the dwell target when the row is highlighted to cut down on visual noise.</span></span>
  * <span data-ttu-id="1d70f-189">請清楚，並與停留目標的位置保持一致。</span><span class="sxs-lookup"><span data-stu-id="1d70f-189">Be clear and consistent with the position of dwell targets.</span></span>
  * <span data-ttu-id="1d70f-190">不要同時顯示所有的停留目標，以避免重複的 UI。</span><span class="sxs-lookup"><span data-stu-id="1d70f-190">Don't show all dwell targets at once to avoid repetitive UI.</span></span>
  * <span data-ttu-id="1d70f-191">盡可能重複使用相同的模式，以建立 UX 的熟悉度。</span><span class="sxs-lookup"><span data-stu-id="1d70f-191">Re-use the same pattern as often as possible to establish UX familiarity.</span></span><br>
        <br>
<span data-ttu-id="1d70f-192">*映射： Microsoft Dynamics 365 指南清單*</span><span class="sxs-lookup"><span data-stu-id="1d70f-192">*Image: Microsoft Dynamics 365 Guides list*</span></span>
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 指南清單](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a><span data-ttu-id="1d70f-194">請參閱</span><span class="sxs-lookup"><span data-stu-id="1d70f-194">See also</span></span>
* [<span data-ttu-id="1d70f-195">注視和認可</span><span class="sxs-lookup"><span data-stu-id="1d70f-195">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="1d70f-196">直接操作</span><span class="sxs-lookup"><span data-stu-id="1d70f-196">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="1d70f-197">實習手勢</span><span class="sxs-lookup"><span data-stu-id="1d70f-197">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="1d70f-198">實際操作和認可</span><span class="sxs-lookup"><span data-stu-id="1d70f-198">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="1d70f-199">本能互動</span><span class="sxs-lookup"><span data-stu-id="1d70f-199">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="1d70f-200">語音輸入</span><span class="sxs-lookup"><span data-stu-id="1d70f-200">Voice input</span></span>](voice-input.md)
