---
title: Head 視線和詳述
description: Head 視線和詳述輸入模型的概觀
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境，視線、 詳述、 互動，設計
ms.openlocfilehash: 05457b35c13422c8aa6663bdf52a489a4f5afdaa
ms.sourcegitcommit: b5bad4eeb5cdd0c2a7b639442656c306e8b5853b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2019
ms.locfileid: "65813986"
---
# <a name="head-gaze-and-dwell"></a><span data-ttu-id="e25f8-104">Head 視線和詳述</span><span class="sxs-lookup"><span data-stu-id="e25f8-104">Head-gaze and Dwell</span></span>

<span data-ttu-id="e25f8-105">指針會佔用工具和組件，當筆勢可以很繁瑣或是不可能。</span><span class="sxs-lookup"><span data-stu-id="e25f8-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="e25f8-106">語音命令，例如筆勢，可以在特定內容中，例如在極大的情況下不可靠。</span><span class="sxs-lookup"><span data-stu-id="e25f8-106">Voice commands, like gestures, can be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="e25f8-107">此外，使用語音來控制電腦不普遍常見，但它的確取得資料流 ！</span><span class="sxs-lookup"><span data-stu-id="e25f8-107">Additionally, using voice to control computers isn't universally common, but it certainly is gaining steam!</span></span> <span data-ttu-id="e25f8-108">Head 視線和詳述提供 heads-up 和免持聽筒 HoloLens 上工作的最熟悉且容易主要機制。</span><span class="sxs-lookup"><span data-stu-id="e25f8-108">Head-gaze and dwell offers the most familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="e25f8-109">此外，head 視線，並詳述為 100%可靠與雜訊干擾或無回應中的條件約束的作業環境無關。</span><span class="sxs-lookup"><span data-stu-id="e25f8-109">Additionally, head-gaze and dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="scenarios"></a><span data-ttu-id="e25f8-110">案例</span><span class="sxs-lookup"><span data-stu-id="e25f8-110">Scenarios</span></span>

<span data-ttu-id="e25f8-111">Head 視線和詳述的過人之處的人手正忙於處理其他工作，並語音未達到 100%可靠或可用由於環境或社交條件約束。</span><span class="sxs-lookup"><span data-stu-id="e25f8-111">Head-gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or availible due to environmental or social constraints.</span></span> <span data-ttu-id="e25f8-112">例如，穿著 HoloLens 重疊時修復汽車引擎的參考資訊的人員。</span><span class="sxs-lookup"><span data-stu-id="e25f8-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="e25f8-113">其指針是忙著處理工具或支援其主體，因為他們了解到引擎區間。</span><span class="sxs-lookup"><span data-stu-id="e25f8-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="e25f8-114">車庫空間是大了，常數 banging 和熱烈的工具，讓語音命令的變得困難。</span><span class="sxs-lookup"><span data-stu-id="e25f8-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="e25f8-115">Head 視線和詳述允許其工作流程的人員有自信地瀏覽其參考資料，而不需要 interupting HoloLens。</span><span class="sxs-lookup"><span data-stu-id="e25f8-115">Head-gaze and dwell allows the person in the HoloLens to confidently navigate their reference material without interupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="e25f8-116">裝置支援</span><span class="sxs-lookup"><span data-stu-id="e25f8-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="e25f8-117"><strong>輸入的模型</strong></span><span class="sxs-lookup"><span data-stu-id="e25f8-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="e25f8-118"><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="e25f8-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="e25f8-119"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="e25f8-119"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="e25f8-120"><a href="immersive-headset-hardware-details.md"><strong>沈浸式耳機</strong></a></span><span class="sxs-lookup"><span data-stu-id="e25f8-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="e25f8-121">Head 視線和詳述</span><span class="sxs-lookup"><span data-stu-id="e25f8-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="e25f8-122">建議的 ✔️</span><span class="sxs-lookup"><span data-stu-id="e25f8-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="e25f8-123">建議的 ✔️</span><span class="sxs-lookup"><span data-stu-id="e25f8-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="e25f8-124">建議的 ✔️</span><span class="sxs-lookup"><span data-stu-id="e25f8-124">✔️ Recommended</span></span></td>
    </tr>
</table>

## <a name="goals"></a><span data-ttu-id="e25f8-125">目標</span><span class="sxs-lookup"><span data-stu-id="e25f8-125">Goals</span></span>

<span data-ttu-id="e25f8-126">提供一種機制，完全免持聽筒互動，而不需使用語音。</span><span class="sxs-lookup"><span data-stu-id="e25f8-126">Provide a mechanism for fully hands-free interactions, without using Voice.</span></span>

## <a name="design-principles"></a><span data-ttu-id="e25f8-127">設計原則</span><span class="sxs-lookup"><span data-stu-id="e25f8-127">Design principles</span></span>

1. <span data-ttu-id="e25f8-128">避免 「 視線作為武器 」</span><span class="sxs-lookup"><span data-stu-id="e25f8-128">Avoid "Gaze as a weapon"</span></span>

    <span data-ttu-id="e25f8-129">Head 視線和詳述需要是直覺式的視覺回饋，但是太多的意見反應可以引發前。</span><span class="sxs-lookup"><span data-stu-id="e25f8-129">Head-gaze and dwell requires visual feedback to be intuitive, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="e25f8-130">意見反應應該協助使用者，知道什麼它們的目標，但不是自動選取它對其意圖。</span><span class="sxs-lookup"><span data-stu-id="e25f8-130">The feedback should help a user know what they're targeting, but not auto-select it against their intent.</span></span> <span data-ttu-id="e25f8-131">讀取文字、 圖示和標籤需要額外的考量，以提供人員聊天室吸收之前選取的資訊。</span><span class="sxs-lookup"><span data-stu-id="e25f8-131">Reading text, icons, and labels requires extra consideration to provide a person room to absorb the information before selecting.</span></span>
    
2. <span data-ttu-id="e25f8-132">搜尋 Goldilocks 速度</span><span class="sxs-lookup"><span data-stu-id="e25f8-132">Seek Goldilocks speed</span></span>
    
    <span data-ttu-id="e25f8-133">詳述的互動可以有不同的計時器為基礎的導覽的影響-較常使用的函式將通常受益於更快速的填滿時間，而更衍生性損害函式可能會受益於較長的填滿時間。</span><span class="sxs-lookup"><span data-stu-id="e25f8-133">Dwell interactions can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="e25f8-134">使用時填滿效果以顯示這些計時器，填滿色彩的動畫曲線可以正面影響更快速的填滿時間能的一目了然。</span><span class="sxs-lookup"><span data-stu-id="e25f8-134">When using a fill-effect to show these timers, animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="e25f8-135">應該採取的考量，以讓使用者決定從快速/medium/緩慢填滿速度覆寫。</span><span class="sxs-lookup"><span data-stu-id="e25f8-135">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
3. <span data-ttu-id="e25f8-136">假設 no-no 爬昇效果</span><span class="sxs-lookup"><span data-stu-id="e25f8-136">Say no-no to yo-yo effect</span></span>

    <span data-ttu-id="e25f8-137">爬昇效果是磁頭移動時的內容和標頭視線詳述的控制項位置會強制要不斷地尋找重複向上和向下的人，可能會出現，只要不模式。</span><span class="sxs-lookup"><span data-stu-id="e25f8-137">The yo-yo effect is an uncomfortable pattern of head movement that can emerge when the placement of content and head-gaze and dwell controls forces people to constantly look up and down repeatedly.</span></span> <span data-ttu-id="e25f8-138">比方說，使用底部的 [標頭視線及詳述] 按鈕清單導覽會引發迴圈的-外觀下會探討，請在查詢結果，請查看要探討等。這個產生的模式時感到不舒服，及應避免將導覽控制項放在上一步往來需要較少的集中位置。</span><span class="sxs-lookup"><span data-stu-id="e25f8-138">For example, a list nav with the head-gaze and dwell button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, etc. This resulting pattern is uncomfortable and should be avoided by placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="e25f8-139">放置相對於其效果詳述按鈕變得很重要的緩和。</span><span class="sxs-lookup"><span data-stu-id="e25f8-139">Placement of dwell buttons relative to their effects becomes important for comfort.</span></span>

## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="e25f8-140">UX 指導方針和最佳作法</span><span class="sxs-lookup"><span data-stu-id="e25f8-140">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="e25f8-141">目標大小</span><span class="sxs-lookup"><span data-stu-id="e25f8-141">Target sizes</span></span>
  <span data-ttu-id="e25f8-142">若要更容易存取，head 視線和目標必須大到足以 comforatably 目標會探討並按住其中的標頭 stabily 目標規定的時間。</span><span class="sxs-lookup"><span data-stu-id="e25f8-142">To be easily accessible, head-gaze and dwell targets need to be large enough to comforatably target, and hold one's head stabily on the target for the prescribed time.</span></span> <span data-ttu-id="e25f8-143">建議的最小目標大小的 2 個角度，以達到最熟悉的體驗。</span><span class="sxs-lookup"><span data-stu-id="e25f8-143">We reccomend a minimum target size of 2 degrees to achieve the most comfortable experience.</span></span> 

### <a name="visual-feedback"></a><span data-ttu-id="e25f8-144">視覺化回饋</span><span class="sxs-lookup"><span data-stu-id="e25f8-144">Visual feedback</span></span>

<span data-ttu-id="e25f8-145">當使用放射狀填滿代表詳述計時器，開始從按鈕的中心。</span><span class="sxs-lookup"><span data-stu-id="e25f8-145">When using a radial fill to represent the dwell timer, start from the center of button.</span></span> <span data-ttu-id="e25f8-146">一致的回應是不同的按鈕上的所有不同方向比不容易產生混淆。</span><span class="sxs-lookup"><span data-stu-id="e25f8-146">A consistent response is less confusing than all different directions on different buttons.</span></span> 

  * <span data-ttu-id="e25f8-147">此規則可以中斷雖然方向互動 （例如，瀏覽向上/向下/左/右，等等）。</span><span class="sxs-lookup"><span data-stu-id="e25f8-147">This rule can be broken though for directional interactions (e.g., nav up/down/left/right, etc.).</span></span> <span data-ttu-id="e25f8-148">比方說，在下一步/背面的例外狀況的 Microsoft Dynamics 365 指南會停留右邊會填滿。</span><span class="sxs-lookup"><span data-stu-id="e25f8-148">For example, Microsoft Dynamics 365 Guides makes an exception on NEXT/BACK being left right fills.</span></span>
  * <span data-ttu-id="e25f8-149">請考慮反轉放射狀填滿從外部，適合進行關閉切換按鈕。</span><span class="sxs-lookup"><span data-stu-id="e25f8-149">Consider inverting radial fill from outside, for scenarios like toggling a button off.</span></span> <span data-ttu-id="e25f8-150">按下按鈕反掌控是維護良好的視覺化模式。</span><span class="sxs-lookup"><span data-stu-id="e25f8-150">The inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="e25f8-151">漸進式揭露</span><span class="sxs-lookup"><span data-stu-id="e25f8-151">Progressive Disclosure</span></span>

<span data-ttu-id="e25f8-152">漸進式揭露表示只顯示盡可能詳細互動的每個階段無關。</span><span class="sxs-lookup"><span data-stu-id="e25f8-152">Progressive disclosure means only showing as much detail as is relevant at each stage of an interaction.</span></span> <span data-ttu-id="e25f8-153">詳述，這表示詳述目標介紹反白顯示 （例如，在清單控制項）。</span><span class="sxs-lookup"><span data-stu-id="e25f8-153">For dwell, that means the dwell target is revealed on highlight (e.g., in a list control).</span></span>

 ### <a name="oversized-targets"></a><span data-ttu-id="e25f8-154">過大的目標</span><span class="sxs-lookup"><span data-stu-id="e25f8-154">Oversized Targets</span></span>
<span data-ttu-id="e25f8-155">詳述區域可能大於非使用中的圖示，以讓它更容易使用，例如 Microsoft Dynamics 365 指南中的 [上一頁] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e25f8-155">Dwell region can be larger than inactive icon to make it easier to use, like the Back button in Microsoft Dynamics 365 Guides.</span></span>

### <a name="prevent-flickering-with-delayed-feedback"></a><span data-ttu-id="e25f8-156">避免延遲的意見反應的閃爍</span><span class="sxs-lookup"><span data-stu-id="e25f8-156">Prevent flickering with delayed feedback</span></span>
<span data-ttu-id="e25f8-157">使用開始視覺化回應之前的短暫的延遲，可避免閃爍有人經過詳述目標時。</span><span class="sxs-lookup"><span data-stu-id="e25f8-157">Use a short delay before starting visual feedback to avoid flickering when someone passes over a dwell target.</span></span>
* <span data-ttu-id="e25f8-158">讓應用程式感覺反應式經常使用的按鈕 inteacted，保留很短的延遲。</span><span class="sxs-lookup"><span data-stu-id="e25f8-158">For buttons inteacted with frequently, keep the delay very short so the application feels reactive.</span></span>
* <span data-ttu-id="e25f8-159">Infrequenctly 互動的按鈕更長的延遲可能 approprate 以避免覺得 twitchy 的介面。</span><span class="sxs-lookup"><span data-stu-id="e25f8-159">For buttons that are interacted with infrequenctly a longer delay can be approprate to avoid the interface feeling twitchy.</span></span>

## <a name="ui-patterns"></a><span data-ttu-id="e25f8-160">UI 模式</span><span class="sxs-lookup"><span data-stu-id="e25f8-160">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="e25f8-161">高頻率按鈕</span><span class="sxs-lookup"><span data-stu-id="e25f8-161">High frequency buttons</span></span>
<span data-ttu-id="e25f8-162">![Microsoft Dynamics 365 指南下一步 按鈕](images/GuideNextButton.png "Microsoft Dynamics 365 指南下一步 按鈕")高頻率餂鈕蒻通常用整個應用程式。</span><span class="sxs-lookup"><span data-stu-id="e25f8-162">![Microsoft Dynamics 365 Guides Next Button](images/GuideNextButton.png "Microsoft Dynamics 365 Guides Next Button") High frequency buttons are buttons that are used commonly throughout an application.</span></span> <span data-ttu-id="e25f8-163">良好的範例，這些是 Microsoft Dynamics 365 指南中的 下一步 和上一步 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e25f8-163">A good example of these are the next and back buttons in Microsoft Dynamics 365 Guides.</span></span>

<span data-ttu-id="e25f8-164">高頻率按鈕應該...</span><span class="sxs-lookup"><span data-stu-id="e25f8-164">High frequency buttons should...</span></span>
* <span data-ttu-id="e25f8-165">會比較容易遇到 head 視線較大的按鈕，</span><span class="sxs-lookup"><span data-stu-id="e25f8-165">be larger buttons, easier to hit with head-gaze</span></span>
* <span data-ttu-id="e25f8-166">保持眼睛高度，以避免工學就附近。</span><span class="sxs-lookup"><span data-stu-id="e25f8-166">stay near eye height to avoid ergonomic straining.</span></span>

### <a name="low-frequency-buttons"></a><span data-ttu-id="e25f8-167">低頻率按鈕</span><span class="sxs-lookup"><span data-stu-id="e25f8-167">Low frequency buttons</span></span>
<span data-ttu-id="e25f8-168">低頻率餂鈕蒻，不或與之互動，定期整個應用程式。</span><span class="sxs-lookup"><span data-stu-id="e25f8-168">Low frequency buttons are buttons that are not interacted with as regularly throughout the application.</span></span> <span data-ttu-id="e25f8-169">按鈕可存取 [設定] 功能表中或按鈕即可清除所有的工作，可能是不錯的範例。</span><span class="sxs-lookup"><span data-stu-id="e25f8-169">A good example might be a button to access the settings menu, or a button to clear all work.</span></span>

* <span data-ttu-id="e25f8-170">嘗試將保留不頻繁的 head 視線路徑，以避免意外啟動妨礙這些按鈕。</span><span class="sxs-lookup"><span data-stu-id="e25f8-170">Try to keep these buttons out of the way of frequent head-gaze paths to avoid accidental activation.</span></span> 

### <a name="confirmations"></a><span data-ttu-id="e25f8-171">確認</span><span class="sxs-lookup"><span data-stu-id="e25f8-171">Confirmations</span></span>
<span data-ttu-id="e25f8-172">![Microsoft Dynamics 365 指南確認對話方塊](images/GuidesConfirmation.png "Microsoft Dynamics 365 指南確認對話方塊")</span><span class="sxs-lookup"><span data-stu-id="e25f8-172">![Microsoft Dynamics 365 Guides Confirmation Dialog](images/GuidesConfirmation.png "Microsoft Dynamics 365 Guides Confirmation Dialog")</span></span>

<span data-ttu-id="e25f8-173">當動作有重大影響，例如收費 money、 刪除工作，或從較長的處理序中，最好確認個人要選取按鈕。</span><span class="sxs-lookup"><span data-stu-id="e25f8-173">When an action has significant impact, like charging money, deleting work, or starting a long process, it is useful to confirm that a person meant to select a button.</span></span> <span data-ttu-id="e25f8-174">Head 視線和詳述有 Ui 會有一些模式和確認對話方塊的考量：</span><span class="sxs-lookup"><span data-stu-id="e25f8-174">For head-gaze and dwell UIs there are some patterns and considerations for confirmation dialogs:</span></span>

  * <span data-ttu-id="e25f8-175">顯示主要按鈕的選取項目反白顯示。</span><span class="sxs-lookup"><span data-stu-id="e25f8-175">Show selection highlight on main button.</span></span>
  * <span data-ttu-id="e25f8-176">顯示與選取項目醒目提示同時探討目標。</span><span class="sxs-lookup"><span data-stu-id="e25f8-176">Reveal dwell target at same time as selection highlight.</span></span>
  * <span data-ttu-id="e25f8-177">次要的按鈕，會顯示在標頭視線詳述目標。</span><span class="sxs-lookup"><span data-stu-id="e25f8-177">For the secondary button, reveal the dwell target on head-gaze.</span></span>
        
### <a name="toggle-buttons"></a><span data-ttu-id="e25f8-178">切換按鈕</span><span class="sxs-lookup"><span data-stu-id="e25f8-178">Toggle buttons</span></span>
<span data-ttu-id="e25f8-179">切換按鈕都需要一些微妙的邏輯，才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="e25f8-179">Toggle buttons require some nuanced logic to work properly.</span></span> <span data-ttu-id="e25f8-180">當個人埋在切換按鈕和在職員工它時，他們就需要結束按鈕，然後再回頭重新啟動詳述邏輯。</span><span class="sxs-lookup"><span data-stu-id="e25f8-180">When a person dwells on a toggle button and actives it, they need to exit the button and then return to restart the dwell logic.</span></span> <span data-ttu-id="e25f8-181">很重要，可切換按鈕就會有清楚的作用與非作用中狀態。</span><span class="sxs-lookup"><span data-stu-id="e25f8-181">It is important that togglable buttons have a clear active versus inactive state.</span></span> 

### <a name="list-views"></a><span data-ttu-id="e25f8-182">清單檢視</span><span class="sxs-lookup"><span data-stu-id="e25f8-182">List views</span></span>
<span data-ttu-id="e25f8-183">![Microsoft Dynamics 365 指南確認對話方塊](images/GuidesListView.png "Microsoft Dynamics 365 指南確認對話方塊")清單檢視呈現 head 視線的特定挑戰，並探討輸入。</span><span class="sxs-lookup"><span data-stu-id="e25f8-183">![Microsoft Dynamics 365 Guides Confirmation Dialog](images/GuidesListView.png "Microsoft Dynamics 365 Guides Confirmation Dialog") List views present a particular challenge for head-gaze and dwell input.</span></span> <span data-ttu-id="e25f8-184">人員需要能夠掃描內容而有 tiptoe 周圍詳述目標。</span><span class="sxs-lookup"><span data-stu-id="e25f8-184">People need to be able to scan the content without feeling like that have to tiptoe around the dwell targets.</span></span> 

<span data-ttu-id="e25f8-185">設計清單檢視的一些秘訣：</span><span class="sxs-lookup"><span data-stu-id="e25f8-185">Some tips for designing list views:</span></span>
* <span data-ttu-id="e25f8-186">具有標頭 gazed，但不開始詳述，head 視線除非特定詳述目標上時反白顯示的整個資料列。</span><span class="sxs-lookup"><span data-stu-id="e25f8-186">have the entire row highlight when head-gazed but doesn’t begin dwell unless head-gaze is on the specific dwell target.</span></span>
* <span data-ttu-id="e25f8-187">若要減少視覺干擾也會反白顯示資料列時，只顯示詳述目標。</span><span class="sxs-lookup"><span data-stu-id="e25f8-187">only show the dwell target when the row is highlighted to cut down on visual noise.</span></span>
* <span data-ttu-id="e25f8-188">是清楚且一致的詳述目標位置。</span><span class="sxs-lookup"><span data-stu-id="e25f8-188">be clear and consistent with the position of dwell targets.</span></span>
* <span data-ttu-id="e25f8-189">不會顯示所有會探討目標一次，以避免重複的 UI</span><span class="sxs-lookup"><span data-stu-id="e25f8-189">don't show all dwell targets at once to avoid repetitive UI</span></span>
* <span data-ttu-id="e25f8-190">重新建立 UX 熟悉盡可能經常使用相同的模式</span><span class="sxs-lookup"><span data-stu-id="e25f8-190">re-use the same pattern as often as possible to establish UX familiarity</span></span>
 
 ## <a name="see-also"></a><span data-ttu-id="e25f8-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e25f8-191">See also</span></span>
* [<span data-ttu-id="e25f8-192">直接操作</span><span class="sxs-lookup"><span data-stu-id="e25f8-192">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="e25f8-193">指向和行動</span><span class="sxs-lookup"><span data-stu-id="e25f8-193">Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="e25f8-194">互動基本概念</span><span class="sxs-lookup"><span data-stu-id="e25f8-194">Interaction fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="e25f8-195">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="e25f8-195">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="e25f8-196">目光和語音</span><span class="sxs-lookup"><span data-stu-id="e25f8-196">Gaze and voice</span></span>](voice-design.md)
