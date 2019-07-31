---
title: 多樣式互動概觀
description: 多樣式互動的概觀
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境, 注視, 注視定向, 互動, 設計, hololens, MMR, 多樣式
ms.openlocfilehash: 7b04141c832597be4bb58447629e0ef6e248dc2b
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415249"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="4c735-104">本能互動簡介</span><span class="sxs-lookup"><span data-stu-id="4c735-104">Introducing instinctual interactions</span></span>

<span data-ttu-id="4c735-105">簡單、直覺式互動的原理貫穿整個混合實境平台。</span><span class="sxs-lookup"><span data-stu-id="4c735-105">The philosophy of simple, instinctual interactions is interwoven throughout the Mixed Reality platform.</span></span>  <span data-ttu-id="4c735-106">我們採取了三個步驟，以確保應用程式設計人員和開發人員可為其客戶提供簡單且直覺式的互動。</span><span class="sxs-lookup"><span data-stu-id="4c735-106">We've taken three steps to ensure that application designers and developers can provide their customers with easy and intuitive interactions.</span></span> 

<span data-ttu-id="4c735-107">首先，我們確定我們令人讚嘆的感應器和輸入技術 (包括手部追蹤、眼球追蹤和自然語言) 結合成完美的多樣式互動模型。</span><span class="sxs-lookup"><span data-stu-id="4c735-107">First, we've made sure our sensors and input technologies (which includes hand and eye tracking along with natural language input) combine into seamless, multimodal interaction models.</span></span>  <span data-ttu-id="4c735-108">根據我們的研究，多樣式架構內的設計和開發 (而不是根據單一輸入) 是創造直覺式體驗的關鍵。</span><span class="sxs-lookup"><span data-stu-id="4c735-108">Based on our research, designing and developing within a multimodal framework, and not based on single inputs, is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="4c735-109">其次，我們了解許多開發人員都以多個 HoloLens 裝置為目標，例如 HoloLens 2 和 HoloLens (第 1 代) 或 HoloLens 和 VR。</span><span class="sxs-lookup"><span data-stu-id="4c735-109">Second, we recognize that many developers target multiple HoloLens devices, such as HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  <span data-ttu-id="4c735-110">因此，我們將互動模型設計為可跨裝置運作，即使每個裝置上的輸入技術有所不同。</span><span class="sxs-lookup"><span data-stu-id="4c735-110">So we've designed our interaction models to work across devices, even if the input technology varies on each device.</span></span>  <span data-ttu-id="4c735-111">例如，在採用 6DoF 控制器的 Windows 沉浸式頭戴裝置上的遠距互動以及在 HoloLens 2 上的遠距互動均使用相同的能供性和模式，因此可輕易地進行跨裝置應用程式開發，而提供自然的使用者互動體驗。</span><span class="sxs-lookup"><span data-stu-id="4c735-111">For example, far interaction on a Windows Immersive headset with a 6DoF controller and far interaction on a HoloLens 2 both use  identical affordances and patterns, making it easy for cross-device application development that provides a natural feel to end-user interactions.</span></span> 

<span data-ttu-id="4c735-112">我們雖認同混合實境 (MR) 中有數千種有效、吸引人和神奇的可能互動，但我們發現在應用程式中刻意運用端對端的單一互動模型，是確保使用者順利擁有絕佳體驗的最佳方法。</span><span class="sxs-lookup"><span data-stu-id="4c735-112">While we recognize that there are thousands of effective, engaging, and magical interactions possible in mixed reality (MR), we've found that intentionally employing a single interaction model, end-to-end, in an application is the best way to ensure users are successful and have a great experience.</span></span> <span data-ttu-id="4c735-113">為此，我們在此互動指引中納入了三件事：</span><span class="sxs-lookup"><span data-stu-id="4c735-113">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="4c735-114">本指引的結構以三個主要互動模型以及每個模型所需的元件和模式為主。</span><span class="sxs-lookup"><span data-stu-id="4c735-114">This guidance is structured around the three primary interaction models and the components and patterns required for each.</span></span>
* <span data-ttu-id="4c735-115">我們針對平台所提供的其他優勢納入了補充指引。</span><span class="sxs-lookup"><span data-stu-id="4c735-115">Supplemental guidance has been included about other benefits that our platform provides.</span></span>
* <span data-ttu-id="4c735-116">此外也納入了可針對您的開發案例協助您選取適當互動模型的指引。</span><span class="sxs-lookup"><span data-stu-id="4c735-116">Guidance has also been included to help select the appropriate interaction model for your development scenario.</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="4c735-117">多樣式互動模型</span><span class="sxs-lookup"><span data-stu-id="4c735-117">Multimodal interaction models</span></span>

<span data-ttu-id="4c735-118">根據我們的研究以及客戶的意見反應，我們發現有三個主要互動模型適合大部分的混合實境體驗。</span><span class="sxs-lookup"><span data-stu-id="4c735-118">Based on our research as well as feedback from customers, we've discovered that three primary interaction models suit the majority of mixed reality experiences.</span></span>

<span data-ttu-id="4c735-119">在許多方面，互動模型是使用者用於完成其流程的心智模型。</span><span class="sxs-lookup"><span data-stu-id="4c735-119">In many ways, the interaction model is the user's mental model for completing their flows.</span></span> <span data-ttu-id="4c735-120">上述每種互動模型都已針對一組客戶需求進行最佳化。</span><span class="sxs-lookup"><span data-stu-id="4c735-120">Each of these interaction models is optimized for a set of customer needs.</span></span> <span data-ttu-id="4c735-121">每個模型都很方便且功能強大，並可靠自己的能力使用。</span><span class="sxs-lookup"><span data-stu-id="4c735-121">Each is convenient, powerful, and usable in its own right.</span></span> 

<span data-ttu-id="4c735-122">下圖是簡化的概觀。</span><span class="sxs-lookup"><span data-stu-id="4c735-122">The chart below is a simplified overview.</span></span> <span data-ttu-id="4c735-123">在底下的頁面中，使用每個互動模型的詳細資訊都有連結，其中包含影像和程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="4c735-123">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span> 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4c735-124"><strong>型號</strong></span><span class="sxs-lookup"><span data-stu-id="4c735-124"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="4c735-125"><strong>範例案例</strong></span><span class="sxs-lookup"><span data-stu-id="4c735-125"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="4c735-126"><strong>適合</strong></span><span class="sxs-lookup"><span data-stu-id="4c735-126"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="4c735-127"><strong>硬體</strong></span><span class="sxs-lookup"><span data-stu-id="4c735-127"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="4c735-128"><a href="hands-and-tools.md">手部和運動控制器</a></span><span class="sxs-lookup"><span data-stu-id="4c735-128"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="4c735-129">3D 空間體驗，例如空間版面配置與設計、內容操作或模擬。</span><span class="sxs-lookup"><span data-stu-id="4c735-129">3D spatial experiences, such as spatial layout and design, content manipulation, or simulation.</span></span></td>
        <td><span data-ttu-id="4c735-130">很適用於新使用者，可搭配語音、眼球追蹤或頭部注視使用。</span><span class="sxs-lookup"><span data-stu-id="4c735-130">Great for new users coupled with voice, eye tracking or head gaze.</span></span> <span data-ttu-id="4c735-131">學習曲線很低。</span><span class="sxs-lookup"><span data-stu-id="4c735-131">Low learning curve.</span></span> <span data-ttu-id="4c735-132">手部追蹤和 6DoF 控制器之間的一致 UX。</span><span class="sxs-lookup"><span data-stu-id="4c735-132">Consistent UX across hand tracking and 6DoF controllers.</span></span></td>
        <td><span data-ttu-id="4c735-133">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4c735-133">HoloLens 2</span></span><br><span data-ttu-id="4c735-134">沉浸式頭戴裝置</span><span class="sxs-lookup"><span data-stu-id="4c735-134">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="4c735-135"><a href="hands-free.md">免持式</a></span><span class="sxs-lookup"><span data-stu-id="4c735-135"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="4c735-136">使用者雙手沒空 (例如在職培訓和維護) 時的情境體驗。</span><span class="sxs-lookup"><span data-stu-id="4c735-136">Contextual experiences where a user's hands are occupied, such as on-the-job learning, and maintenance.</span></span></td>
        <td><span data-ttu-id="4c735-137">需要學習一下。</span><span class="sxs-lookup"><span data-stu-id="4c735-137">Some learning required.</span></span> <span data-ttu-id="4c735-138">如果無法使用手部，裝置可搭配語音和自然語言使用。</span><span class="sxs-lookup"><span data-stu-id="4c735-138">If hands are unavailable, the device pairs well with voice and natural language.</span></span></td>
        <td><span data-ttu-id="4c735-139">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4c735-139">HoloLens 2</span></span><br><span data-ttu-id="4c735-140">HoloLens (第 1 代)</span><span class="sxs-lookup"><span data-stu-id="4c735-140">HoloLens (1st gen)</span></span><br><span data-ttu-id="4c735-141">沉浸式頭戴裝置</span><span class="sxs-lookup"><span data-stu-id="4c735-141">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="4c735-142"><a href="gaze-and-commit.md">頭部注視並認可</a></span><span class="sxs-lookup"><span data-stu-id="4c735-142"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="4c735-143">點選體驗，例如 3D 簡報、示範。</span><span class="sxs-lookup"><span data-stu-id="4c735-143">Click-through experiences, e.g. 3D presentations, demos.</span></span></td>
        <td><span data-ttu-id="4c735-144">需要 HMD 訓練，但不是在行動裝置上。</span><span class="sxs-lookup"><span data-stu-id="4c735-144">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="4c735-145">最適合用於可存取的控制器。</span><span class="sxs-lookup"><span data-stu-id="4c735-145">Best for accessible controllers.</span></span> <span data-ttu-id="4c735-146">最適合用於 HoloLens (第 1 代)。</span><span class="sxs-lookup"><span data-stu-id="4c735-146">Best for HoloLens (1st gen).</span></span></td>
        <td><span data-ttu-id="4c735-147">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4c735-147">HoloLens 2</span></span><br><span data-ttu-id="4c735-148">HoloLens (第 1 代)</span><span class="sxs-lookup"><span data-stu-id="4c735-148">HoloLens (1st gen)</span></span><br><span data-ttu-id="4c735-149">沉浸式頭戴裝置</span><span class="sxs-lookup"><span data-stu-id="4c735-149">Immersive headsets</span></span><br><span data-ttu-id="4c735-150">行動 AR</span><span class="sxs-lookup"><span data-stu-id="4c735-150">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="4c735-151">若是確保使用者互動體驗不會有任何落差，從頭到尾遵循單一模型的指引將是最佳方式。</span><span class="sxs-lookup"><span data-stu-id="4c735-151">To ensure that there are no gaps or holes in the user interaction experience, it is best to follow the guidance for a single model from beginning to end.</span></span> 

<span data-ttu-id="4c735-152">為了加快設計和開發速度，我們在每個模型的涵蓋範圍內納入了詳細資訊，以及影像和程式碼範例的連結。</span><span class="sxs-lookup"><span data-stu-id="4c735-152">To speed up design and development, we've included detailed information and links to images and code samples within our coverage of each model.</span></span>

<span data-ttu-id="4c735-153">下列各節會逐步說明選取及實作其中一個互動模型的步驟。</span><span class="sxs-lookup"><span data-stu-id="4c735-153">The sections below walk through the steps for selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="4c735-154">在此頁面結束前，您會了解我們對於下列各項的指引：</span><span class="sxs-lookup"><span data-stu-id="4c735-154">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="4c735-155">為您的客戶選擇互動模型</span><span class="sxs-lookup"><span data-stu-id="4c735-155">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="4c735-156">使用互動模型指引</span><span class="sxs-lookup"><span data-stu-id="4c735-156">Using the interaction model guidance</span></span>
* <span data-ttu-id="4c735-157">互動模型之間的轉換</span><span class="sxs-lookup"><span data-stu-id="4c735-157">Transitioning between interaction models</span></span>
* <span data-ttu-id="4c735-158">設計後續步驟</span><span class="sxs-lookup"><span data-stu-id="4c735-158">Design next steps</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="4c735-159">為您的客戶選擇互動模型</span><span class="sxs-lookup"><span data-stu-id="4c735-159">Choose an interaction model for your customer</span></span>


<span data-ttu-id="4c735-160">開發人員和創作者通常都已考量其客戶可使用的互動類型。</span><span class="sxs-lookup"><span data-stu-id="4c735-160">Typically, developers and creators have thought through the types of interactions that their customers can have.</span></span> <span data-ttu-id="4c735-161">為了鼓勵以客戶為主的設計方式，我們建議您遵循下列指引來選取最適合客戶的互動模型。</span><span class="sxs-lookup"><span data-stu-id="4c735-161">To encourage a customer-focused approach to design, we recommend the following guidance for selecting the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="4c735-162">為什麼要遵循本指引？</span><span class="sxs-lookup"><span data-stu-id="4c735-162">Why follow this guidance?</span></span>

* <span data-ttu-id="4c735-163">我們的互動模型都經過客觀和主觀條件測試，例如實際和認知投入、直覺性和學習力。</span><span class="sxs-lookup"><span data-stu-id="4c735-163">Our interaction models are tested for objective and subjective criteria, such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="4c735-164">由於互動不同，互動模型之間的視覺和音訊能供性及物件行為也可能不同。</span><span class="sxs-lookup"><span data-stu-id="4c735-164">Because interactions differ, visual and audio affordances and object behavior might differ between interaction models.</span></span>  
* <span data-ttu-id="4c735-165">結合多個互動模型的組件，會引起競用能供性 (例如同時手部光線和頭部注視游標) 的風險，進而妨礙和混淆使用者。</span><span class="sxs-lookup"><span data-stu-id="4c735-165">Combining parts of multiple interaction models creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor that can overwhelm and confuse users.</span></span>

<span data-ttu-id="4c735-166">以下是如何針對每個互動模型將能供性和行為最佳化的一些範例。</span><span class="sxs-lookup"><span data-stu-id="4c735-166">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span>  <span data-ttu-id="4c735-167">我們常會看到新使用者有類似的問題，例如「如何得知系統是否能運作、如何得知我可以做什麼，以及如何得知它是否了解我剛做了什麼？」</span><span class="sxs-lookup"><span data-stu-id="4c735-167">We often see new users have similar questions, such as "how do I know the system is working, how do I know what I can do, and how do I know if it understood what I just did?"</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4c735-168"><strong>型號</strong></span><span class="sxs-lookup"><span data-stu-id="4c735-168"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="4c735-169"><strong>如何得知它是否能運作？</strong></span><span class="sxs-lookup"><span data-stu-id="4c735-169"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="4c735-170"><strong>如何得知我可以做什麼？</strong></span><span class="sxs-lookup"><span data-stu-id="4c735-170"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="4c735-171"><strong>如何得知我剛做了什麼？</strong></span><span class="sxs-lookup"><span data-stu-id="4c735-171"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="4c735-172"><a href="hands-and-tools.md">手部和運動控制器</a></span><span class="sxs-lookup"><span data-stu-id="4c735-172"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="4c735-173">我看到手狀網格，我看到指尖能供性或手部/控制器光線。</span><span class="sxs-lookup"><span data-stu-id="4c735-173">I see a hand mesh, I see a fingertip affordance or hand/controller rays.</span></span></td>
        <td><span data-ttu-id="4c735-174">我看到當我的手部靠近時會出現可握住的把手或週框方塊。</span><span class="sxs-lookup"><span data-stu-id="4c735-174">I see grabbable handles or a bounding box appear when my hand is near.</span></span></td>
        <td><span data-ttu-id="4c735-175">我會在握住和放開時聽到聽得見的音調並看到動畫。</span><span class="sxs-lookup"><span data-stu-id="4c735-175">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="4c735-176"><a href="gaze-and-commit.md">頭部注視並認可</a></span><span class="sxs-lookup"><span data-stu-id="4c735-176"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="4c735-177">我在視野中央看到一個游標。</span><span class="sxs-lookup"><span data-stu-id="4c735-177">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="4c735-178">頭部注視游標會在掃過某些物件時變更狀態。</span><span class="sxs-lookup"><span data-stu-id="4c735-178">The head-gaze cursor changes state when over certain objects.</span></span></td>
        <td><span data-ttu-id="4c735-179">當我採取動作時，我會看到/聽到看得見和聽得見的確認。</span><span class="sxs-lookup"><span data-stu-id="4c735-179">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="4c735-180"><a href="hands-free.md">免持式 (頭部注視並佇留)</a></span><span class="sxs-lookup"><span data-stu-id="4c735-180"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="4c735-181">我在視野中央看到一個游標。</span><span class="sxs-lookup"><span data-stu-id="4c735-181">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="4c735-182">當我佇留在可互動的物件上時，我會看到進度列指示器。</span><span class="sxs-lookup"><span data-stu-id="4c735-182">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="4c735-183">當我採取動作時，我會看到/聽到看得見和聽得見的確認。</span><span class="sxs-lookup"><span data-stu-id="4c735-183">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="4c735-184"><a href="hands-free.md">免持式 (語音命令)</a></span><span class="sxs-lookup"><span data-stu-id="4c735-184"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="4c735-185">我看到接聽指示器以及可顯示系統所聽內容的字幕。</span><span class="sxs-lookup"><span data-stu-id="4c735-185">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="4c735-186">我取得語音提示。</span><span class="sxs-lookup"><span data-stu-id="4c735-186">I get voice prompts and hints.</span></span> <span data-ttu-id="4c735-187">當我說：「我可以說什麼？」時，</span><span class="sxs-lookup"><span data-stu-id="4c735-187">When I say: "what can I say?"</span></span> <span data-ttu-id="4c735-188">我看到回饋。</span><span class="sxs-lookup"><span data-stu-id="4c735-188">I see feedback.</span></span></td>
        <td><span data-ttu-id="4c735-189">當我發出命令時，我會看到/聽到看得見和聽得見的確認，或在必要時取得去除混淆 UX。</span><span class="sxs-lookup"><span data-stu-id="4c735-189">I see/ hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="4c735-190">以下是我們發現有助於小組選取互動模型的問題：</span><span class="sxs-lookup"><span data-stu-id="4c735-190">Below are the questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="4c735-191">Q:我的使用者想要觸控全像投影和執行精準全像攝影操作嗎？</span><span class="sxs-lookup"><span data-stu-id="4c735-191">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="4c735-192">答：若是如此，請查看「雙手和運動控制器」互動模型，以雙手或運動控制器進行精準定向和操作。</span><span class="sxs-lookup"><span data-stu-id="4c735-192">A:  If so, check out the Hands and motion controllers interaction model for precision targeting and manipulation with hands or motion controllers.</span></span>
 
2.  <span data-ttu-id="4c735-193">Q:我的使用者需要為了實際操作而騰出雙手嗎？</span><span class="sxs-lookup"><span data-stu-id="4c735-193">Q:  Do my users need to keep their hands free for real-world tasks?</span></span><br><br>
<span data-ttu-id="4c735-194">答：若是如此，請查看免持式互動模型，此模型可透過注視和語音型互動提供絕佳的免持式體驗。</span><span class="sxs-lookup"><span data-stu-id="4c735-194">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="4c735-195">Q:我的使用者是否有時間了解我的 MR 應用程式互動，或者他們需要最低學習曲線的互動？</span><span class="sxs-lookup"><span data-stu-id="4c735-195">Q:  Do my users have time to learn interactions for my MR application or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="4c735-196">答：我們建議使用「雙手和運動控制器」模型進行最低學習曲線和最直覺的互動，只要使用者能夠使用其雙手進行互動即可。</span><span class="sxs-lookup"><span data-stu-id="4c735-196">A:  We recommend the Hands and motion controllers model for the lowest learning curve and most intuitive interactions, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="4c735-197">Q:我的使用者是否要使用運動控制器來指向及操作？</span><span class="sxs-lookup"><span data-stu-id="4c735-197">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="4c735-198">答：「雙手和運動控制器」模型包含優質運動控制器體驗的所有指引。</span><span class="sxs-lookup"><span data-stu-id="4c735-198">A:  The Hands and motion controllers model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="4c735-199">Q:我的使用者是否使用協助工具控制器或通用藍牙控制器，例如 Clicker？</span><span class="sxs-lookup"><span data-stu-id="4c735-199">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="4c735-200">答：我們建議使用所有非追蹤式控制器都適用的「頭部注視並認可」模型。</span><span class="sxs-lookup"><span data-stu-id="4c735-200">A:  We recommend the Head-gaze and commit model for all non-tracked controllers.</span></span> <span data-ttu-id="4c735-201">其設計訴求是可讓使用者使用簡單的「定向和行動」經歷整個體驗。</span><span class="sxs-lookup"><span data-stu-id="4c735-201">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanism.</span></span> 
 
6.  <span data-ttu-id="4c735-202">Q:相對於瀏覽 UI 控制項的密集版面配置，我的使用者只是經由「點選」來進行體驗 (例如在類似 3D 投影片的環境中) 嗎？</span><span class="sxs-lookup"><span data-stu-id="4c735-202">Q: Do my users only progress through an experience by "clicking through" (for example in a 3D slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="4c735-203">答：如果使用者不需要控制大量 UI，則「頭部注視並認可」會提供學得會的選項，使用者就不必擔心如何定向。</span><span class="sxs-lookup"><span data-stu-id="4c735-203">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="4c735-204">Q:我的使用者是否同時使用 HoloLens (第 1 代) 和 HoloLens 2/Windows Mixed Reality 沉浸式頭戴裝置 (VR)？</span><span class="sxs-lookup"><span data-stu-id="4c735-204">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/Windows Mixed Reality immersive headsets (VR)?</span></span><br><br>
<span data-ttu-id="4c735-205">答：由於「頭部注視並認可」是 HoloLens (第 1 代) 適用的互動模型，我們建議支援 HoloLens (第 1 代) 的創作者將「頭部注視並認可」用於使用者在 HoloLens (第 1 代) 頭戴式裝置上所將體驗的任何功能或模式。</span><span class="sxs-lookup"><span data-stu-id="4c735-205">A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users will experience on a HoloLens (1st gen) headset.</span></span> <span data-ttu-id="4c735-206">如需取得多代 HoloLens 絕佳體驗的詳細資訊，請參閱底下有關「轉換互動模型」  的一節。</span><span class="sxs-lookup"><span data-stu-id="4c735-206">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="4c735-207">Q:對於經常移動 (涵蓋大型空間或在空間之間移動) 的使用者，與傾向在單一空間工作的使用者而言，有何差別？</span><span class="sxs-lookup"><span data-stu-id="4c735-207">Q: What about users who are generally mobile, covering a large space or moving between spaces, versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="4c735-208">答：任何互動模型都適用於這些使用者。</span><span class="sxs-lookup"><span data-stu-id="4c735-208">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="4c735-209">[即將推出](index.md#news-and-notes)應用程式設計專屬的詳細指引。</span><span class="sxs-lookup"><span data-stu-id="4c735-209">More guidance specific to app design [coming soon](index.md#news-and-notes).</span></span>


## <a name="transitioning-interaction-models"></a><span data-ttu-id="4c735-210">轉換互動模型</span><span class="sxs-lookup"><span data-stu-id="4c735-210">Transitioning interaction models</span></span>
<span data-ttu-id="4c735-211">在某些使用案例中，可能需要使用多個互動模型。</span><span class="sxs-lookup"><span data-stu-id="4c735-211">There are also use cases that might require utilizing more than one interaction model.</span></span> <span data-ttu-id="4c735-212">例如，您應用程式的「建立流程」使用雙手和運動控制器互動模型，但您想要讓現場技術人員使用免持式模式。</span><span class="sxs-lookup"><span data-stu-id="4c735-212">For example, your application's creation flow utilizes the Hands and motion controllers interaction model, but you want to employ a hands-free mode for field technicians.</span></span>  

<span data-ttu-id="4c735-213">如果您的經驗的確需要多種互動模型，請您留意，有許多終端使用者可能會在轉換模型時遇到困難，尤其是不熟悉混合實境的使用者。</span><span class="sxs-lookup"><span data-stu-id="4c735-213">If your experience does require multiple interaction models, keep in mind that many end users might encounter difficulty when transitioning from one model to another--especially for users who are new to mixed reality.</span></span>

> [!Note]
> <span data-ttu-id="4c735-214">我們會繼續撰寫更多適用於開發人員和設計人員的指引，讓他們了解使用多個 MR 互動模型的方式、時機和原因。</span><span class="sxs-lookup"><span data-stu-id="4c735-214">We're constantly working on more guidance that will be available to developers and designers, informing them about the how, when, and why for using multiple MR interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="4c735-215">請參閱</span><span class="sxs-lookup"><span data-stu-id="4c735-215">See also</span></span>
* [<span data-ttu-id="4c735-216">頭部注視並認可</span><span class="sxs-lookup"><span data-stu-id="4c735-216">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="4c735-217">頭部目光和停駐</span><span class="sxs-lookup"><span data-stu-id="4c735-217">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="4c735-218">手部直接操作</span><span class="sxs-lookup"><span data-stu-id="4c735-218">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="4c735-219">手部指向和行動</span><span class="sxs-lookup"><span data-stu-id="4c735-219">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="4c735-220">筆勢</span><span class="sxs-lookup"><span data-stu-id="4c735-220">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="4c735-221">語音命令</span><span class="sxs-lookup"><span data-stu-id="4c735-221">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="4c735-222">運動控制器</span><span class="sxs-lookup"><span data-stu-id="4c735-222">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="4c735-223">空間音效設計</span><span class="sxs-lookup"><span data-stu-id="4c735-223">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="4c735-224">空間對應設計</span><span class="sxs-lookup"><span data-stu-id="4c735-224">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="4c735-225">舒適度</span><span class="sxs-lookup"><span data-stu-id="4c735-225">Comfort</span></span>](comfort.md)

