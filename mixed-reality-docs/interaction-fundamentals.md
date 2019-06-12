---
title: 多樣式互動概觀
description: 多樣式互動的概觀
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境, 注視, 注視定向, 互動, 設計, hololens, MMR, 多樣式
ms.openlocfilehash: bea205edf484a55db701e8e0d1a233234882a272
ms.sourcegitcommit: 9b6949d7cd2e67e6bde9b32aebeaeea325baa6c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66516016"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="688c1-104">本能互動簡介</span><span class="sxs-lookup"><span data-stu-id="688c1-104">Introducing instinctual interactions</span></span>

<span data-ttu-id="688c1-105">簡單、直覺式互動的原理貫穿整個 Microsoft Mixed Reality 平台。</span><span class="sxs-lookup"><span data-stu-id="688c1-105">The philosophy of simple, instinctual interactions is woven throughout the Microsoft Mixed Reality platform.</span></span>  <span data-ttu-id="688c1-106">我們已採取三個步驟，以確保應用程式設計人員和開發人員可為其客戶提供簡單且直覺式的互動。</span><span class="sxs-lookup"><span data-stu-id="688c1-106">We've taken three steps to ensure that application designers and developers can provide easy and intuitive interactions for their customers.</span></span> 

<span data-ttu-id="688c1-107">首先，我們已確定我們令人讚嘆的感應器和輸入的技術 (包括手部追蹤、眼動追蹤和自然語言) 結合成完美的多樣式互動模型。</span><span class="sxs-lookup"><span data-stu-id="688c1-107">First, we've made sure our amazing sensors and input technology, including hand tracking, eye tracking, and natural language, combine into seamless multimodal interaction models.</span></span>  <span data-ttu-id="688c1-108">根據我們的研究，多樣式設計和開發 (而不是根據單一輸入) 是創造直覺式體驗的關鍵。</span><span class="sxs-lookup"><span data-stu-id="688c1-108">Based on our research, designing and developing multimodally -- and not based on single inputs -- is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="688c1-109">其次，我們了解許多開發人員都以多個裝置為目標，不論是 HoloLens 2 和 HoloLens (第 1 代) 或 HoloLens 和 VR。</span><span class="sxs-lookup"><span data-stu-id="688c1-109">Secondly, we recognize that many developers target multiple devices, whether that means HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  <span data-ttu-id="688c1-110">因此，我們將互動模型設計為可跨裝置運作 (即使每個裝置上的輸入技術有所不同)。</span><span class="sxs-lookup"><span data-stu-id="688c1-110">So we've designed our interaction models to work across devices (even if the input technology varies on each device).</span></span>  <span data-ttu-id="688c1-111">例如，在採用 6DOF 控制器的 Windows 沉浸式頭戴裝置上的遠距互動以及在 HoloLens 2 上的遠距互動均使用相同的能供性和模式，可輕易地跨裝置應用。</span><span class="sxs-lookup"><span data-stu-id="688c1-111">For example, far interaction on a Windows Immersive headset with a 6DOF controller and far interaction on a HoloLens 2 both use the identical affordances and patterns, making it easy for cross-device applications.</span></span> <span data-ttu-id="688c1-112">這不只方便開發人員和設計人員使用，對使用者而言也很自然。</span><span class="sxs-lookup"><span data-stu-id="688c1-112">Not only is this convenient for developers and designers, but it feels natural to end users.</span></span> 

<span data-ttu-id="688c1-113">最後，我們雖承認 MR 中有數千種有效、吸引人和神奇的可能互動，但我們發現在應用程式中刻意運用端對端的單一互動模型，是確保使用者順利擁有絕佳體驗的最佳方法。</span><span class="sxs-lookup"><span data-stu-id="688c1-113">Lastly, while we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we have found that intentionally employing a single interaction model end to end in an application is the best way to ensure users are successful and have a great experience.</span></span>  <span data-ttu-id="688c1-114">為此，我們在此互動指引中納入了三件事：</span><span class="sxs-lookup"><span data-stu-id="688c1-114">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="688c1-115">我們讓本指引的結構以三個主要互動模型以及每個模型所需的元件和模式為主</span><span class="sxs-lookup"><span data-stu-id="688c1-115">We've structured this guidance around the three primary interaction models and the components and patterns required for each</span></span>
* <span data-ttu-id="688c1-116">我們納入了我們平台所提供的其他優勢的補充指引</span><span class="sxs-lookup"><span data-stu-id="688c1-116">We've included supplemental guidance on other benefits that our platform provides</span></span>
* <span data-ttu-id="688c1-117">我們納入了可針對您的案例協助選取適當互動模型的指引</span><span class="sxs-lookup"><span data-stu-id="688c1-117">We've included guidance to help select the appropriate interaction model for your scenario</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="688c1-118">多樣式互動模型</span><span class="sxs-lookup"><span data-stu-id="688c1-118">Multimodal interaction models</span></span>

<span data-ttu-id="688c1-119">根據我們的研究以及與客戶到目前為止的合作，我們發現有三個主要互動模型適合大部分的混合實境體驗。</span><span class="sxs-lookup"><span data-stu-id="688c1-119">Based on our research and work with customers to date, we've discovered that three primary interaction models suit the majority of mixed reality experiences.</span></span>

<span data-ttu-id="688c1-120">在許多方面，互動模型是使用者用於完成其流程的心智模型。</span><span class="sxs-lookup"><span data-stu-id="688c1-120">In many ways, the interaction model is the user's mental model for completing their flows.</span></span>  <span data-ttu-id="688c1-121">上述每種互動模型都已針對一組客戶需求進行最佳化，而每個模型都很方便且功能強大，並可靠自己的能力使用。</span><span class="sxs-lookup"><span data-stu-id="688c1-121">Each of these interaction models is optimized for a set of customer needs, and each is convenient, powerful, and usable in its own right.</span></span> 

<span data-ttu-id="688c1-122">下圖是簡化的概觀。</span><span class="sxs-lookup"><span data-stu-id="688c1-122">The chart below is a simplified overview.</span></span>  <span data-ttu-id="688c1-123">在底下的頁面中，使用每個互動模型的詳細資訊都有連結，其中包含影像和程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="688c1-123">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span> 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="688c1-124"><strong>模型</strong></span><span class="sxs-lookup"><span data-stu-id="688c1-124"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="688c1-125"><strong>範例案例</strong></span><span class="sxs-lookup"><span data-stu-id="688c1-125"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="688c1-126"><strong>適合</strong></span><span class="sxs-lookup"><span data-stu-id="688c1-126"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="688c1-127"><strong>硬體</strong></span><span class="sxs-lookup"><span data-stu-id="688c1-127"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="688c1-128"><a href="hands-and-tools.md">手部和運動控制器</a></span><span class="sxs-lookup"><span data-stu-id="688c1-128"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="688c1-129">3D 空間體驗，例如空間版面配置與設計、內容操作或模擬。</span><span class="sxs-lookup"><span data-stu-id="688c1-129">3D spatial experiences, e.g. spatial layout and design, content manipulation, or simulation.</span></span></td>
        <td><span data-ttu-id="688c1-130">很適合於新使用者，可搭配語音、眼動追蹤或頭部注視使用。</span><span class="sxs-lookup"><span data-stu-id="688c1-130">Great for new users, coupled with voice, eye tracking or head gaze.</span></span> <span data-ttu-id="688c1-131">學習曲線很低。</span><span class="sxs-lookup"><span data-stu-id="688c1-131">Low learning curve.</span></span> <span data-ttu-id="688c1-132">手部追蹤和 6 DoF 控制器之間的一致 UX。</span><span class="sxs-lookup"><span data-stu-id="688c1-132">Consistent UX across hand tracking and 6 DoF controllers.</span></span></td>
        <td><span data-ttu-id="688c1-133">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="688c1-133">HoloLens 2</span></span><br><span data-ttu-id="688c1-134">沉浸式頭戴裝置</span><span class="sxs-lookup"><span data-stu-id="688c1-134">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="688c1-135"><a href="hands-free.md">免持式</a></span><span class="sxs-lookup"><span data-stu-id="688c1-135"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="688c1-136">使用者雙手沒空 (例如在職培訓、維護) 時的情境體驗。</span><span class="sxs-lookup"><span data-stu-id="688c1-136">Contextual experiences where a user's hands are occupied, e.g. on-the-job learning, maintenance.</span></span></td>
        <td><span data-ttu-id="688c1-137">需要學習一下。</span><span class="sxs-lookup"><span data-stu-id="688c1-137">Some learning required.</span></span> <span data-ttu-id="688c1-138">如果無法使用手部，請搭配語音和自然語言使用。</span><span class="sxs-lookup"><span data-stu-id="688c1-138">If hands are unavailable pairs well with voice and natural language.</span></span></td>
        <td><span data-ttu-id="688c1-139">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="688c1-139">HoloLens 2</span></span><br><span data-ttu-id="688c1-140">HoloLens (第 1 代)</span><span class="sxs-lookup"><span data-stu-id="688c1-140">HoloLens (1st gen)</span></span><br><span data-ttu-id="688c1-141">沉浸式頭戴裝置</span><span class="sxs-lookup"><span data-stu-id="688c1-141">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="688c1-142"><a href="gaze-and-commit.md">頭部目光和行動</a></span><span class="sxs-lookup"><span data-stu-id="688c1-142"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="688c1-143">點選體驗，例如 3D 簡報、示範。</span><span class="sxs-lookup"><span data-stu-id="688c1-143">Click-through experiences, e.g. 3D presentations, demos.</span></span></td>
        <td><span data-ttu-id="688c1-144">需要 HMD 訓練，但不是在行動裝置上。</span><span class="sxs-lookup"><span data-stu-id="688c1-144">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="688c1-145">最適合用於可存取的控制器。</span><span class="sxs-lookup"><span data-stu-id="688c1-145">Best for accessible controllers.</span></span> <span data-ttu-id="688c1-146">最適合用於 HoloLens (第 1 代)。</span><span class="sxs-lookup"><span data-stu-id="688c1-146">Best for HoloLens (1st gen).</span></span></td>
        <td><span data-ttu-id="688c1-147">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="688c1-147">HoloLens 2</span></span><br><span data-ttu-id="688c1-148">HoloLens (第 1 代)</span><span class="sxs-lookup"><span data-stu-id="688c1-148">HoloLens (1st gen)</span></span><br><span data-ttu-id="688c1-149">沉浸式頭戴裝置</span><span class="sxs-lookup"><span data-stu-id="688c1-149">Immersive headsets</span></span><br><span data-ttu-id="688c1-150">行動 AR</span><span class="sxs-lookup"><span data-stu-id="688c1-150">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="688c1-151">從頭到尾遵循單一模型的指引，是確保您的互動體驗不會有任何落差的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="688c1-151">The best way to ensure there are no gaps or holes in the interaction for your experience is to follow the guidance for a single model from beginning to end.</span></span> 

<span data-ttu-id="688c1-152">為了加快設計和開發速度，我們在每個模型的涵蓋範圍內納入了詳細資訊，以及影像和程式碼範例的連結。</span><span class="sxs-lookup"><span data-stu-id="688c1-152">To speed design and development, we've included detailed information and links to images and code samples within our coverage of each model.</span></span>

<span data-ttu-id="688c1-153">但首先，下列各節會逐步說明選取及實作其中一個互動模型的步驟。</span><span class="sxs-lookup"><span data-stu-id="688c1-153">But first, the sections below walk through the steps of selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="688c1-154">在此頁面結束前，您會了解我們對於下列各項的指引：</span><span class="sxs-lookup"><span data-stu-id="688c1-154">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="688c1-155">為您的客戶選擇互動模型</span><span class="sxs-lookup"><span data-stu-id="688c1-155">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="688c1-156">使用互動模型指引</span><span class="sxs-lookup"><span data-stu-id="688c1-156">Using the interaction model guidance</span></span>
* <span data-ttu-id="688c1-157">互動模型之間的轉換</span><span class="sxs-lookup"><span data-stu-id="688c1-157">Transitioning between interaction models</span></span>
* <span data-ttu-id="688c1-158">設計後續步驟</span><span class="sxs-lookup"><span data-stu-id="688c1-158">Design next steps</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="688c1-159">為您的客戶選擇互動模型</span><span class="sxs-lookup"><span data-stu-id="688c1-159">Choose an interaction model for your customer</span></span>


<span data-ttu-id="688c1-160">最有可能的情況是，開發人員與創作者對於其希望使用者擁有的互動體驗種類也已經有一些想法。</span><span class="sxs-lookup"><span data-stu-id="688c1-160">Most likely, developers and creators also already have some ideas in mind of the kinds of interaction experience they want their users to have.</span></span>
<span data-ttu-id="688c1-161">為了鼓勵以客戶為主的設計方式，我們建議您遵循下面的指引來選取最適合您客戶的互動模型。</span><span class="sxs-lookup"><span data-stu-id="688c1-161">To encourage a customer-focused approach to design, we recommend following the guidance below to select the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="688c1-162">為什麼要遵循本指引？</span><span class="sxs-lookup"><span data-stu-id="688c1-162">Why follow this guidance?</span></span>

* <span data-ttu-id="688c1-163">我們的互動模型都經過客觀和主觀條件測試，例如實際和認知投入、直覺性和學習力。</span><span class="sxs-lookup"><span data-stu-id="688c1-163">Our interaction models are tested for objective and subjective criteria such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="688c1-164">因為互動不同，所以互動模型之間的視覺和音訊能供性及物件行為也可能不同。</span><span class="sxs-lookup"><span data-stu-id="688c1-164">Because interaction differs, visual and audio affordances and object behavior may also differ between the interaction models.</span></span>  
* <span data-ttu-id="688c1-165">將多個互動模型的組件結合在一起，會引起競用能供性 (例如同時手部射線和頭部注視游標) 的風險，進而妨礙和混淆使用者。</span><span class="sxs-lookup"><span data-stu-id="688c1-165">Combining parts of multiple interaction models together creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor, which can overwhelm and confuse users.</span></span>

<span data-ttu-id="688c1-166">以下是如何針對每個互動模型將能供性和行為最佳化的一些範例。</span><span class="sxs-lookup"><span data-stu-id="688c1-166">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span>  <span data-ttu-id="688c1-167">我們常會看到新使用者有類似的問題，例如 「如何得知系統是否能運作、如何得知我可以做什麼，以及如何得知它是否了解我剛做了什麼？」</span><span class="sxs-lookup"><span data-stu-id="688c1-167">We often see new users have similar questions, such as "how do I know the system is working, how do I know what I can do, and how do I know if it understood what I just did?"</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="688c1-168"><strong>型號</strong></span><span class="sxs-lookup"><span data-stu-id="688c1-168"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="688c1-169"><strong>如何得知它是否能運作？</strong></span><span class="sxs-lookup"><span data-stu-id="688c1-169"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="688c1-170"><strong>如何得知我可以做什麼？</strong></span><span class="sxs-lookup"><span data-stu-id="688c1-170"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="688c1-171"><strong>如何得知我剛做了什麼？</strong></span><span class="sxs-lookup"><span data-stu-id="688c1-171"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="688c1-172"><a href="hands-and-tools.md">手部和運動控制器</a></span><span class="sxs-lookup"><span data-stu-id="688c1-172"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="688c1-173">我看到手狀網格，我看到指尖能供性或手部 / 控制器射線。</span><span class="sxs-lookup"><span data-stu-id="688c1-173">I see a hand mesh, I see a fingertip affordance or hand/ controller rays.</span></span></td>
        <td><span data-ttu-id="688c1-174">我看到當我的手部靠近時會出現可握住的把手或週框方塊。</span><span class="sxs-lookup"><span data-stu-id="688c1-174">I see grabbable handles or a bounding box appear when my hand is near.</span></span></td>
        <td><span data-ttu-id="688c1-175">我會在握住和放開時聽到聽得見的音調並看到動畫。</span><span class="sxs-lookup"><span data-stu-id="688c1-175">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="688c1-176"><a href="gaze-and-commit.md">頭部目光和行動</a></span><span class="sxs-lookup"><span data-stu-id="688c1-176"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="688c1-177">我在視野中央看到一個游標。</span><span class="sxs-lookup"><span data-stu-id="688c1-177">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="688c1-178">頭部注視游標會在掃過某些物件時變更狀態。</span><span class="sxs-lookup"><span data-stu-id="688c1-178">The head-gaze cursor changes state when over certain objects.</span></span></td>
        <td><span data-ttu-id="688c1-179">當我採取動作時，我會看到/聽到看得見和聽得見的確認。</span><span class="sxs-lookup"><span data-stu-id="688c1-179">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="688c1-180"><a href="hands-free.md">免持式 (頭部注視並佇留)</a></span><span class="sxs-lookup"><span data-stu-id="688c1-180"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="688c1-181">我在視野中央看到一個游標。</span><span class="sxs-lookup"><span data-stu-id="688c1-181">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="688c1-182">當我佇留在可互動的物件上時，我會看到進度列指示器。</span><span class="sxs-lookup"><span data-stu-id="688c1-182">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="688c1-183">當我採取動作時，我會看到/聽到看得見和聽得見的確認。</span><span class="sxs-lookup"><span data-stu-id="688c1-183">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="688c1-184"><a href="hands-free.md">免持式 (語音命令)</a></span><span class="sxs-lookup"><span data-stu-id="688c1-184"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="688c1-185">我看到接聽指示器以及可顯示系統所聽內容的字幕。</span><span class="sxs-lookup"><span data-stu-id="688c1-185">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="688c1-186">我取得語音提示。</span><span class="sxs-lookup"><span data-stu-id="688c1-186">I get voice prompts and hints.</span></span>  <span data-ttu-id="688c1-187">何時說「我可以說什麼？」</span><span class="sxs-lookup"><span data-stu-id="688c1-187">When I say "what can I say?"</span></span> <span data-ttu-id="688c1-188">我看到回饋。</span><span class="sxs-lookup"><span data-stu-id="688c1-188">I see feedback.</span></span></td>
        <td><span data-ttu-id="688c1-189">當我發出命令時，我會看到/聽到看得見和聽得見的確認，或在必要時取得去除混淆 UX。</span><span class="sxs-lookup"><span data-stu-id="688c1-189">I see/ hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="688c1-190">以下是我們發現有助於小組選取互動模型的問題：</span><span class="sxs-lookup"><span data-stu-id="688c1-190">Below are the questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="688c1-191">Q:我的使用者想要觸控全像投影和執行精準全像攝影操作嗎？</span><span class="sxs-lookup"><span data-stu-id="688c1-191">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="688c1-192">答：若是如此，請查看「雙手和工具」互動模型，以雙手或運動控制器進行精準定向和操作。</span><span class="sxs-lookup"><span data-stu-id="688c1-192">A:  If so, check out the Hands and tools interaction model for precision targeting and manipulation with hands or motion controllers.</span></span>
 
2.  <span data-ttu-id="688c1-193">Q:我的使用者需要為了實際操作而騰出雙手嗎？</span><span class="sxs-lookup"><span data-stu-id="688c1-193">Q:  Do my users need to keep their hands free, for real-world tasks?</span></span><br><br>
<span data-ttu-id="688c1-194">答：若是如此，請查看免持式互動模型，其可透過注視和語音型互動提供絕佳的免持式經驗。</span><span class="sxs-lookup"><span data-stu-id="688c1-194">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze- and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="688c1-195">Q:我的使用者是否有時間了解我的混合實境應用程式互動，或者他們需要可能最低學習曲線的互動？</span><span class="sxs-lookup"><span data-stu-id="688c1-195">Q:  Do my users have time to learn interactions for my mixed reality application, or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="688c1-196">答：我們建議使用「雙手和工具」模型進行最低學習曲線和最直覺的互動，只要使用者能夠使用其雙手進行互動即可。</span><span class="sxs-lookup"><span data-stu-id="688c1-196">A:  We recommend the Hands and Tools model for the lowest learning curve and most intuitive interactions, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="688c1-197">Q:我的使用者是否要使用運動控制器來指向及操作？</span><span class="sxs-lookup"><span data-stu-id="688c1-197">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="688c1-198">答：「雙手和工具」模型包含優質運動控制器體驗的所有指引。</span><span class="sxs-lookup"><span data-stu-id="688c1-198">A:  The Hands and tools model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="688c1-199">Q:我的使用者是否使用協助工具控制器或通用藍牙控制器，例如 Clicker？</span><span class="sxs-lookup"><span data-stu-id="688c1-199">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="688c1-200">答：我們建議使用所有非追蹤式控制器都適用的「頭部注視並認可」模型。</span><span class="sxs-lookup"><span data-stu-id="688c1-200">A:  We recommend the Head-gaze and Commit model for all non-tracked controllers.</span></span>  <span data-ttu-id="688c1-201">其設計訴求是可讓使用者使用簡單的「目標和認可」經歷整個體驗。</span><span class="sxs-lookup"><span data-stu-id="688c1-201">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanic.</span></span> 
 
6.  <span data-ttu-id="688c1-202">Q:相對於瀏覽 UI 控制項的密集版面配置，我的使用者只是經由「點選」來進行體驗 (例如在 3D 類似投影片的環境中) 嗎？</span><span class="sxs-lookup"><span data-stu-id="688c1-202">Q: Do my users only progress through an experience by "clicking through" (for example in a 3d slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="688c1-203">答：如果使用者不需要控制大量 UI，則「頭部注視並認可」會提供學得會的選項，使用者就不必擔心如何定向。</span><span class="sxs-lookup"><span data-stu-id="688c1-203">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="688c1-204">Q:我的使用者是否同時使用 HoloLens (第 1 代) 和 HoloLens 2 / Windows 沉浸式 (VR 頭戴裝置)？</span><span class="sxs-lookup"><span data-stu-id="688c1-204">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/ Windows Immersive (VR headsets)</span></span><br><br>
<span data-ttu-id="688c1-205">答：因為「頭部注視並認可」是 HoloLens (第 1 代) 適用的互動模型，所以我們建議支援 HoloLens (第 1 代) 的創作者將「頭部注視並認可」用於使用者在 HoloLens (第 1 代) 頭戴式裝置上可能體驗的任何功能或模式。</span><span class="sxs-lookup"><span data-stu-id="688c1-205">A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users may experience on a HoloLens (1st gen) headset.</span></span>  <span data-ttu-id="688c1-206">如需取得多代 HoloLens 絕佳體驗的詳細資訊，請參閱底下有關「轉換互動模型」  的一節。</span><span class="sxs-lookup"><span data-stu-id="688c1-206">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="688c1-207">Q:對於經常移動 (涵蓋大型空間或在空間之間移動) 的使用者與傾向在單一空間工作的使用者而言，有何差別？</span><span class="sxs-lookup"><span data-stu-id="688c1-207">Q: What about for users who are generally mobile (covering a large space or moving between spaces), versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="688c1-208">答：任何互動模型都適用於這些使用者。</span><span class="sxs-lookup"><span data-stu-id="688c1-208">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="688c1-209">[即將推出](index.md#news-and-notes)應用程式設計專屬的詳細指引。</span><span class="sxs-lookup"><span data-stu-id="688c1-209">More guidance specific to app design [coming soon](index.md#news-and-notes).</span></span>


## <a name="transition-interaction-models"></a><span data-ttu-id="688c1-210">轉換互動模型</span><span class="sxs-lookup"><span data-stu-id="688c1-210">Transition interaction models</span></span>
<span data-ttu-id="688c1-211">有些時候，您的使用案例可能需要使用一個以上的互動模型。</span><span class="sxs-lookup"><span data-stu-id="688c1-211">There are also cases where your use cases may require that utilizing more than one interaction model.</span></span>  <span data-ttu-id="688c1-212">例如，您應用程式的「建立流程」會利用雙手和運動控制器互動模型，但您想要對現場技術人員運用免持式模型。</span><span class="sxs-lookup"><span data-stu-id="688c1-212">For example, your app's "creation flow" utilizes the Hands and motion controllers interaction model, but you want to employ a Hands-free mode for field technicians.</span></span>  

<span data-ttu-id="688c1-213">如果您的經驗的確需要多種互動模型，我們發現有許多終端使用者可能會在轉換模型時遇到困難 (尤其是不熟悉混合實境的使用者)。</span><span class="sxs-lookup"><span data-stu-id="688c1-213">If your experience does require multiple interaction models, we've found that many end users may encounter difficulty transitioning from one model to another -- especially users who are new to mixed reality.</span></span>

> [!Note]
> <span data-ttu-id="688c1-214">為了協助引導設計人員和開發人員在 MR 中進行困難的選擇，我們正努力準備使用多種互動模型的詳細指引。</span><span class="sxs-lookup"><span data-stu-id="688c1-214">To help guide designers and developers through choices that can be difficult in MR, we're working on more guidance for using multiple interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="688c1-215">請參閱</span><span class="sxs-lookup"><span data-stu-id="688c1-215">See also</span></span>
* [<span data-ttu-id="688c1-216">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="688c1-216">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="688c1-217">頭部目光和停駐</span><span class="sxs-lookup"><span data-stu-id="688c1-217">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="688c1-218">手部直接操作</span><span class="sxs-lookup"><span data-stu-id="688c1-218">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="688c1-219">手部指向和行動</span><span class="sxs-lookup"><span data-stu-id="688c1-219">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="688c1-220">筆勢</span><span class="sxs-lookup"><span data-stu-id="688c1-220">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="688c1-221">語音命令</span><span class="sxs-lookup"><span data-stu-id="688c1-221">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="688c1-222">運動控制器</span><span class="sxs-lookup"><span data-stu-id="688c1-222">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="688c1-223">空間音效設計</span><span class="sxs-lookup"><span data-stu-id="688c1-223">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="688c1-224">空間對應設計</span><span class="sxs-lookup"><span data-stu-id="688c1-224">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="688c1-225">舒適度</span><span class="sxs-lookup"><span data-stu-id="688c1-225">Comfort</span></span>](comfort.md)

