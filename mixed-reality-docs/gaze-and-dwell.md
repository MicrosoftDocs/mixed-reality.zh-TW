---
title: 頭部注視並佇留
description: 頭部注視並佇留輸入模型的概觀
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 注視, 佇留, 互動, 設計
ms.openlocfilehash: 70b25949380679d2edc81b07ab54f24fa20e3f3d
ms.sourcegitcommit: 9b6949d7cd2e67e6bde9b32aebeaeea325baa6c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66516009"
---
# <a name="head-gaze-and-dwell"></a><span data-ttu-id="35c98-104">頭部注視並佇留</span><span class="sxs-lookup"><span data-stu-id="35c98-104">Head-gaze and dwell</span></span>

<span data-ttu-id="35c98-105">當手上拿著工具和組件時，手勢可以很繁瑣或不可能進行。</span><span class="sxs-lookup"><span data-stu-id="35c98-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="35c98-106">語音命令 (例如手勢) 在特定情境 (例如極度喧噪的情況) 中可能不大可靠。</span><span class="sxs-lookup"><span data-stu-id="35c98-106">Voice commands, like gestures, can be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="35c98-107">此外，使用語音來控制電腦並不十分普遍，但的確可取得資料流！</span><span class="sxs-lookup"><span data-stu-id="35c98-107">Additionally, using voice to control computers isn't universally common, but it certainly is gaining steam!</span></span> <span data-ttu-id="35c98-108">「頭部注視並佇留」提供最熟悉且容易掌握的機制，可在 HoloLens 上以抬頭和免持式運作。</span><span class="sxs-lookup"><span data-stu-id="35c98-108">Head-gaze and dwell offers the most familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="35c98-109">此外，「頭部注視並佇留」 100% 可靠，完全不受雜訊干擾，而且在作業環境中也沒有靜音限制。</span><span class="sxs-lookup"><span data-stu-id="35c98-109">Additionally, head-gaze and dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="scenarios"></a><span data-ttu-id="35c98-110">案例</span><span class="sxs-lookup"><span data-stu-id="35c98-110">Scenarios</span></span>

<span data-ttu-id="35c98-111">當人員的雙手正忙於處理其他工作時，「頭部注視並佇留」十分出色，且由於環境或社交限制，語音並未達到 100% 可靠或可用。</span><span class="sxs-lookup"><span data-stu-id="35c98-111">Head-gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or availible due to environmental or social constraints.</span></span> <span data-ttu-id="35c98-112">穿戴 HoloLens 的人員在修理汽車引擎時覆疊參考資訊就是個不錯的範例。</span><span class="sxs-lookup"><span data-stu-id="35c98-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="35c98-113">他們的雙手忙著拿起工具，或在靠向引擎室時支撐其身體。</span><span class="sxs-lookup"><span data-stu-id="35c98-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="35c98-114">車庫空間很吵雜，充斥著工具的碰撞和唧唧聲，讓語音命令變得難以使用。</span><span class="sxs-lookup"><span data-stu-id="35c98-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="35c98-115">「頭部注視並佇留」可讓穿戴 HoloLens 的人員自信地瀏覽其參考資料，而不需中斷其工作流程。</span><span class="sxs-lookup"><span data-stu-id="35c98-115">Head-gaze and dwell allows the person in the HoloLens to confidently navigate their reference material without interupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="35c98-116">裝置支援</span><span class="sxs-lookup"><span data-stu-id="35c98-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="35c98-117"><strong>輸入模型</strong></span><span class="sxs-lookup"><span data-stu-id="35c98-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="35c98-118"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="35c98-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="35c98-119"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="35c98-119"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="35c98-120"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="35c98-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="35c98-121">頭部注視並佇留</span><span class="sxs-lookup"><span data-stu-id="35c98-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="35c98-122">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="35c98-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="35c98-123">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="35c98-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="35c98-124">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="35c98-124">✔️ Recommended</span></span></td>
    </tr>
</table>

## <a name="goals"></a><span data-ttu-id="35c98-125">目標</span><span class="sxs-lookup"><span data-stu-id="35c98-125">Goals</span></span>

<span data-ttu-id="35c98-126">不需使用語音，提供完全免持式互動的機制。</span><span class="sxs-lookup"><span data-stu-id="35c98-126">Provide a mechanism for fully hands-free interactions, without using voice.</span></span>

## <a name="design-principles"></a><span data-ttu-id="35c98-127">設計原則</span><span class="sxs-lookup"><span data-stu-id="35c98-127">Design principles</span></span>

1. <span data-ttu-id="35c98-128">避免「使用注視作為手段」</span><span class="sxs-lookup"><span data-stu-id="35c98-128">Avoid "Gaze as a weapon"</span></span>

    <span data-ttu-id="35c98-129">「頭部注視並佇留」需要直覺式視覺化回饋，但是太多回饋可能會引起焦慮。</span><span class="sxs-lookup"><span data-stu-id="35c98-129">Head-gaze and dwell requires visual feedback to be intuitive, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="35c98-130">回饋應協助使用者知道他們所定向的目標，但不會針對其意圖予以自動選取。</span><span class="sxs-lookup"><span data-stu-id="35c98-130">The feedback should help a user know what they're targeting, but not auto-select it against their intent.</span></span> <span data-ttu-id="35c98-131">讀取文字、圖示和標籤需要額外的考量，在選取之前為人員提供吸收資訊的空間。</span><span class="sxs-lookup"><span data-stu-id="35c98-131">Reading text, icons, and labels requires extra consideration to provide a person room to absorb the information before selecting.</span></span>
    
2. <span data-ttu-id="35c98-132">追求 Goldilocks 速度</span><span class="sxs-lookup"><span data-stu-id="35c98-132">Seek Goldilocks speed</span></span>
    
    <span data-ttu-id="35c98-133">佇留互動可根據瀏覽的影響而有不同的計時器 - 較多常用功能通常受益於更快速的填滿時間，而較多衍生性功能則可受益於較長的填滿時間。</span><span class="sxs-lookup"><span data-stu-id="35c98-133">Dwell interactions can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="35c98-134">使用填滿效果來顯示這些計時器時，填滿色彩的動畫曲線對於較快速填滿時間的感覺有正面影響。</span><span class="sxs-lookup"><span data-stu-id="35c98-134">When using a fill-effect to show these timers, animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="35c98-135">應可慮讓使用者決定快速/中等/緩慢填滿速度覆寫。</span><span class="sxs-lookup"><span data-stu-id="35c98-135">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
3. <span data-ttu-id="35c98-136">Say no-no to yo-yo 效應</span><span class="sxs-lookup"><span data-stu-id="35c98-136">Say no-no to yo-yo effect</span></span>

    <span data-ttu-id="35c98-137">溜溜球效應是當內容和「頭部注視並佇留」控制項的放置方式強迫人們要不斷地重複仰視和俯視時，可能出現的不舒適頭部移動模式。</span><span class="sxs-lookup"><span data-stu-id="35c98-137">The yo-yo effect is an uncomfortable pattern of head movement that can emerge when the placement of content and head-gaze and dwell controls forces people to constantly look up and down repeatedly.</span></span> <span data-ttu-id="35c98-138">比方說，使用底部的「頭部注視並佇留」按鈕進行清單瀏覽會引發以下迴圈：俯視佇留、仰視結果、俯視佇留等。所產生的這個模式並不舒適，應藉由將瀏覽控制項放在需要較少往返的集中位置加以避免。</span><span class="sxs-lookup"><span data-stu-id="35c98-138">For example, a list nav with the head-gaze and dwell button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, etc. This resulting pattern is uncomfortable and should be avoided by placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="35c98-139">與效應相關的佇留按鈕放置方式，對於舒適度而言很重要。</span><span class="sxs-lookup"><span data-stu-id="35c98-139">Placement of dwell buttons relative to their effects becomes important for comfort.</span></span>

## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="35c98-140">UX 指導方針和最佳作法</span><span class="sxs-lookup"><span data-stu-id="35c98-140">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="35c98-141">目標大小</span><span class="sxs-lookup"><span data-stu-id="35c98-141">Target sizes</span></span>
  <span data-ttu-id="35c98-142">為了要更容易存取，「頭部注視並佇留」目標必須大到足以舒適地定向，而且將頭部穩定地朝向目標並持續一段規定的時間。</span><span class="sxs-lookup"><span data-stu-id="35c98-142">To be easily accessible, head-gaze and dwell targets need to be large enough to comforatably target, and hold one's head stabily on the target for the prescribed time.</span></span> <span data-ttu-id="35c98-143">建議的最小目標大小為 2 度，可達到最熟悉的舒適體驗。</span><span class="sxs-lookup"><span data-stu-id="35c98-143">We reccomend a minimum target size of 2 degrees to achieve the most comfortable experience.</span></span> 

### <a name="visual-feedback"></a><span data-ttu-id="35c98-144">視覺化回饋</span><span class="sxs-lookup"><span data-stu-id="35c98-144">Visual feedback</span></span>

<span data-ttu-id="35c98-145">使用放射狀填滿來表示佇留計時器時，從按鈕中心開始。</span><span class="sxs-lookup"><span data-stu-id="35c98-145">When using a radial fill to represent the dwell timer, start from the center of button.</span></span> <span data-ttu-id="35c98-146">相較於不同按鈕上的所有不同方向，一致的回應比較不容易混淆。</span><span class="sxs-lookup"><span data-stu-id="35c98-146">A consistent response is less confusing than all different directions on different buttons.</span></span> 

  * <span data-ttu-id="35c98-147">有方向的互動 (例如，向上/向下/左/右瀏覽等) 可以打破此規則。</span><span class="sxs-lookup"><span data-stu-id="35c98-147">This rule can be broken though for directional interactions (e.g., nav up/down/left/right, etc.).</span></span> <span data-ttu-id="35c98-148">例如，Microsoft Dynamics 365 Guides 讓「下一頁/上一頁」成為左右填滿則屬例外狀況。</span><span class="sxs-lookup"><span data-stu-id="35c98-148">For example, Microsoft Dynamics 365 Guides makes an exception on NEXT/BACK being left right fills.</span></span>
  * <span data-ttu-id="35c98-149">在關閉按鈕等情境下，請考慮從外部反轉放射狀填滿。</span><span class="sxs-lookup"><span data-stu-id="35c98-149">Consider inverting radial fill from outside, for scenarios like toggling a button off.</span></span> <span data-ttu-id="35c98-150">按壓按鈕的反向感覺是可維護的良好視覺模式。</span><span class="sxs-lookup"><span data-stu-id="35c98-150">The inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="35c98-151">漸進式揭露</span><span class="sxs-lookup"><span data-stu-id="35c98-151">Progressive disclosure</span></span>

<span data-ttu-id="35c98-152">漸進式揭露表示只有盡可能詳細顯示與互動的每個階段相關。</span><span class="sxs-lookup"><span data-stu-id="35c98-152">Progressive disclosure means only showing as much detail as is relevant at each stage of an interaction.</span></span> <span data-ttu-id="35c98-153">對於佇留，這表示佇留目標會顯現於醒目提示 (例如，在清單控制項中)。</span><span class="sxs-lookup"><span data-stu-id="35c98-153">For dwell, that means the dwell target is revealed on highlight (e.g., in a list control).</span></span>

 ### <a name="oversized-targets"></a><span data-ttu-id="35c98-154">過大的目標</span><span class="sxs-lookup"><span data-stu-id="35c98-154">Oversized targets</span></span>
<span data-ttu-id="35c98-155">佇留區域可大於非使用中的圖示，使其更容易使用，例如 Microsoft Dynamics 365 Guides 中的 [上一頁] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="35c98-155">Dwell region can be larger than inactive icon to make it easier to use, like the Back button in Microsoft Dynamics 365 Guides.</span></span>

### <a name="prevent-flickering-with-delayed-feedback"></a><span data-ttu-id="35c98-156">使用延遲回饋防止閃爍</span><span class="sxs-lookup"><span data-stu-id="35c98-156">Prevent flickering with delayed feedback</span></span>
<span data-ttu-id="35c98-157">在開始視覺化回饋前使用短暫延遲，可避免有人經過佇留目標時發生閃爍。</span><span class="sxs-lookup"><span data-stu-id="35c98-157">Use a short delay before starting visual feedback to avoid flickering when someone passes over a dwell target.</span></span>
* <span data-ttu-id="35c98-158">對於經常使用的按鈕，讓延遲保持非常短暫，應用程式就會覺得有反應。</span><span class="sxs-lookup"><span data-stu-id="35c98-158">For buttons inteacted with frequently, keep the delay very short so the application feels reactive.</span></span>
* <span data-ttu-id="35c98-159">對於不常使用的按鈕，較長的延遲可能不適合，以免介面感覺焦躁不安。</span><span class="sxs-lookup"><span data-stu-id="35c98-159">For buttons that are interacted with infrequenctly a longer delay can be approprate to avoid the interface feeling twitchy.</span></span>

## <a name="ui-patterns"></a><span data-ttu-id="35c98-160">UI 模式</span><span class="sxs-lookup"><span data-stu-id="35c98-160">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="35c98-161">高頻率按鈕</span><span class="sxs-lookup"><span data-stu-id="35c98-161">High frequency buttons</span></span>
<span data-ttu-id="35c98-162">![Microsoft Dynamics 365 Guides 下一頁按鈕](images/GuideNextButton.png "Microsoft Dynamics 365 Guides 下一步按鈕") 高頻率按鈕就是常用於整個應用程式的按鈕。</span><span class="sxs-lookup"><span data-stu-id="35c98-162">![Microsoft Dynamics 365 Guides Next Button](images/GuideNextButton.png "Microsoft Dynamics 365 Guides Next Button") High frequency buttons are buttons that are used commonly throughout an application.</span></span> <span data-ttu-id="35c98-163">Microsoft Dynamics 365 Guides 中的下一頁和上一頁按鈕都是不錯的範例。</span><span class="sxs-lookup"><span data-stu-id="35c98-163">A good example of these are the next and back buttons in Microsoft Dynamics 365 Guides.</span></span>

<span data-ttu-id="35c98-164">高頻率按鈕應該...</span><span class="sxs-lookup"><span data-stu-id="35c98-164">High frequency buttons should...</span></span>
* <span data-ttu-id="35c98-165">是較大的按鈕，可輕易以頭部注視方式點擊</span><span class="sxs-lookup"><span data-stu-id="35c98-165">be larger buttons, easier to hit with head-gaze</span></span>
* <span data-ttu-id="35c98-166">位置接近眼部高度，以免造成人體工學負擔。</span><span class="sxs-lookup"><span data-stu-id="35c98-166">stay near eye height to avoid ergonomic straining.</span></span>

### <a name="low-frequency-buttons"></a><span data-ttu-id="35c98-167">低頻率按鈕</span><span class="sxs-lookup"><span data-stu-id="35c98-167">Low frequency buttons</span></span>
<span data-ttu-id="35c98-168">低頻率按鈕是整個應用程式中不會定期互動的按鈕。</span><span class="sxs-lookup"><span data-stu-id="35c98-168">Low frequency buttons are buttons that are not interacted with as regularly throughout the application.</span></span> <span data-ttu-id="35c98-169">可存取 [設定] 功能表的按鈕，或可清除所有工作的按鈕都是不錯的範例。</span><span class="sxs-lookup"><span data-stu-id="35c98-169">A good example might be a button to access the settings menu, or a button to clear all work.</span></span>

* <span data-ttu-id="35c98-170">嘗試讓這些按鈕不在常用的頭部注視路徑中，以免意外啟動。</span><span class="sxs-lookup"><span data-stu-id="35c98-170">Try to keep these buttons out of the way of frequent head-gaze paths to avoid accidental activation.</span></span> 

### <a name="confirmations"></a><span data-ttu-id="35c98-171">確認</span><span class="sxs-lookup"><span data-stu-id="35c98-171">Confirmations</span></span>
<span data-ttu-id="35c98-172">![Microsoft Dynamics 365 Guides 確認對話方塊](images/GuidesConfirmation.png "Microsoft Dynamics 365 Guides 確認對話方塊")</span><span class="sxs-lookup"><span data-stu-id="35c98-172">![Microsoft Dynamics 365 Guides Confirmation Dialog](images/GuidesConfirmation.png "Microsoft Dynamics 365 Guides Confirmation Dialog")</span></span>

<span data-ttu-id="35c98-173">當某個動作有重大影響時 (例如收費、刪除工作或開始長時間處理)，最好確認個人要選取按鈕。</span><span class="sxs-lookup"><span data-stu-id="35c98-173">When an action has significant impact, like charging money, deleting work, or starting a long process, it is useful to confirm that a person meant to select a button.</span></span> <span data-ttu-id="35c98-174">對於「頭部注視並佇留」UI，確認對話方塊有一些模式和考量：</span><span class="sxs-lookup"><span data-stu-id="35c98-174">For head-gaze and dwell UIs there are some patterns and considerations for confirmation dialogs:</span></span>

  * <span data-ttu-id="35c98-175">在主要按鈕上顯示選取醒目提示。</span><span class="sxs-lookup"><span data-stu-id="35c98-175">Show selection highlight on main button.</span></span>
  * <span data-ttu-id="35c98-176">與選取醒目提示同時顯示佇留目標。</span><span class="sxs-lookup"><span data-stu-id="35c98-176">Reveal dwell target at same time as selection highlight.</span></span>
  * <span data-ttu-id="35c98-177">對於次要按鈕，顯示頭部注視的佇留目標。</span><span class="sxs-lookup"><span data-stu-id="35c98-177">For the secondary button, reveal the dwell target on head-gaze.</span></span>
        
### <a name="toggle-buttons"></a><span data-ttu-id="35c98-178">切換按鈕</span><span class="sxs-lookup"><span data-stu-id="35c98-178">Toggle buttons</span></span>
<span data-ttu-id="35c98-179">切換按鈕需要一些微妙的邏輯，才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="35c98-179">Toggle buttons require some nuanced logic to work properly.</span></span> <span data-ttu-id="35c98-180">當人員佇留在切換按鈕並啟動它時，他們需要結束按鈕，然後回頭重新啟動佇留邏輯。</span><span class="sxs-lookup"><span data-stu-id="35c98-180">When a person dwells on a toggle button and actives it, they need to exit the button and then return to restart the dwell logic.</span></span> <span data-ttu-id="35c98-181">切換按鈕會有清楚的作用與非作用中狀態很重要。</span><span class="sxs-lookup"><span data-stu-id="35c98-181">It is important that togglable buttons have a clear active versus inactive state.</span></span> 

### <a name="list-views"></a><span data-ttu-id="35c98-182">清單檢視</span><span class="sxs-lookup"><span data-stu-id="35c98-182">List views</span></span>
<span data-ttu-id="35c98-183">![Microsoft Dynamics 365 Guides 確認對話方塊](images/GuidesListView.png "Microsoft Dynamics 365 Guides 確認對話方塊")清單檢視呈現「頭部注視並佇留」輸入的特定挑戰。</span><span class="sxs-lookup"><span data-stu-id="35c98-183">![Microsoft Dynamics 365 Guides Confirmation Dialog](images/GuidesListView.png "Microsoft Dynamics 365 Guides Confirmation Dialog") List views present a particular challenge for head-gaze and dwell input.</span></span> <span data-ttu-id="35c98-184">人們需要能夠掃描內容，而不覺得必須偷偷摸摸地環顧佇留目標。</span><span class="sxs-lookup"><span data-stu-id="35c98-184">People need to be able to scan the content without feeling like that have to tiptoe around the dwell targets.</span></span> 

<span data-ttu-id="35c98-185">設計清單檢視的一些秘訣：</span><span class="sxs-lookup"><span data-stu-id="35c98-185">Some tips for designing list views:</span></span>
* <span data-ttu-id="35c98-186">使用頭部注視時整列醒目提示，但不會開始佇留，除非頭部注視位於特定佇留目標上。</span><span class="sxs-lookup"><span data-stu-id="35c98-186">have the entire row highlight when head-gazed but doesn’t begin dwell unless head-gaze is on the specific dwell target.</span></span>
* <span data-ttu-id="35c98-187">醒目提示該列時，只顯示佇留目標，以降低視覺雜訊。</span><span class="sxs-lookup"><span data-stu-id="35c98-187">only show the dwell target when the row is highlighted to cut down on visual noise.</span></span>
* <span data-ttu-id="35c98-188">佇留目標的位置清楚而一致。</span><span class="sxs-lookup"><span data-stu-id="35c98-188">be clear and consistent with the position of dwell targets.</span></span>
* <span data-ttu-id="35c98-189">不要一次顯示所有佇留目標，以避免重複的 UI</span><span class="sxs-lookup"><span data-stu-id="35c98-189">don't show all dwell targets at once to avoid repetitive UI</span></span>
* <span data-ttu-id="35c98-190">盡可能重新使用相同的模式以便熟悉 UX</span><span class="sxs-lookup"><span data-stu-id="35c98-190">re-use the same pattern as often as possible to establish UX familiarity</span></span>
 
 ## <a name="see-also"></a><span data-ttu-id="35c98-191">請參閱</span><span class="sxs-lookup"><span data-stu-id="35c98-191">See also</span></span>
* [<span data-ttu-id="35c98-192">手部直接操作</span><span class="sxs-lookup"><span data-stu-id="35c98-192">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="35c98-193">手部指向和行動</span><span class="sxs-lookup"><span data-stu-id="35c98-193">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="35c98-194">本能互動</span><span class="sxs-lookup"><span data-stu-id="35c98-194">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="35c98-195">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="35c98-195">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="35c98-196">語音命令</span><span class="sxs-lookup"><span data-stu-id="35c98-196">Voice commanding</span></span>](voice-design.md)
