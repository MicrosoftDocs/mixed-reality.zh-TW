---
title: 本能互動
description: 瞭解貫穿整個混合實境平台的簡單、直覺式互動原理。
author: shengkait
ms.author: shentan
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境, 注視, 注視定向, 互動, 設計, hololens, MMR, 多樣式
ms.openlocfilehash: 6b54d6e844c1b501a0835fc3a48deb4932ba551d
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "74539724"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="5f66c-104">本能互動簡介</span><span class="sxs-lookup"><span data-stu-id="5f66c-104">Introducing instinctual interactions</span></span>

![遠距手部操作](images/04_InteractionFundamentals.png)

<span data-ttu-id="5f66c-106">簡單、直覺式互動的原理貫穿整個混合實境 (MR) 平台。</span><span class="sxs-lookup"><span data-stu-id="5f66c-106">The philosophy of simple, instinctual interactions is interwoven throughout the mixed reality (MR) platform.</span></span> <span data-ttu-id="5f66c-107">我們採取了三個步驟，以確保應用程式設計人員和開發人員可為其客戶提供簡單且直覺式的互動。</span><span class="sxs-lookup"><span data-stu-id="5f66c-107">We've taken three steps to ensure that application designers and developers can provide their customers with easy and intuitive interactions.</span></span> 

<span data-ttu-id="5f66c-108">首先，我們確定我們令人讚嘆的感應器和輸入技術 (包括手部追蹤、眼球追蹤和自然語言) 結合成完美的多樣式互動模型。</span><span class="sxs-lookup"><span data-stu-id="5f66c-108">First, we've made sure our sensors and input technologies (which includes hand and eye tracking along with natural language input) combine into seamless, multimodal interaction models.</span></span>  
<span data-ttu-id="5f66c-109">根據我們的研究，多樣式架構內的設計和開發 (而不是根據個別輸入) 是創造直覺式體驗的關鍵。</span><span class="sxs-lookup"><span data-stu-id="5f66c-109">Based on our research, designing and developing within a multimodal framework (and not based on individual inputs) is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="5f66c-110">其次，我們了解許多開發人員都以多個 HoloLens 裝置為目標，例如 HoloLens 2 和 HoloLens (第 1 代) 或 HoloLens 和 VR。</span><span class="sxs-lookup"><span data-stu-id="5f66c-110">Second, we recognize that many developers target multiple HoloLens devices, such as HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  
<span data-ttu-id="5f66c-111">因此，我們將互動模型設計為可跨裝置運作，即使每個裝置上的輸入技術有所不同。</span><span class="sxs-lookup"><span data-stu-id="5f66c-111">So we've designed our interaction models to work across devices, even if the input technology varies on each device.</span></span>  
<span data-ttu-id="5f66c-112">例如，在採用 6DoF 控制器的 Windows 沉浸式頭戴裝置上的遠距互動以及在 HoloLens 2 上的遠距互動均使用相同的能供性和模式，因此可輕易地進行跨裝置應用程式開發，並提供自然的使用者互動體驗。</span><span class="sxs-lookup"><span data-stu-id="5f66c-112">For example, far interaction on a Windows Immersive headset with a 6DoF controller and far interaction on a HoloLens 2 both use identical affordances and patterns, making it easy for cross-device application development and providing a natural feel to user interactions.</span></span> 

<span data-ttu-id="5f66c-113">我們承認 MR 中有數千種有效、吸引人和神奇的可能互動，但我們也發現在應用程式中刻意運用端對端的單一互動模型，是確保使用者順利擁有絕佳體驗的最佳方法。</span><span class="sxs-lookup"><span data-stu-id="5f66c-113">While we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we've found that intentionally employing a single interaction model end-to-end in an application is the best way to ensure users are successful and have a great experience.</span></span> <span data-ttu-id="5f66c-114">為此，我們在此互動指引中納入了三件事：</span><span class="sxs-lookup"><span data-stu-id="5f66c-114">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="5f66c-115">特定指引，以三個主要互動模型以及每個模型所需的元件和模式為主。</span><span class="sxs-lookup"><span data-stu-id="5f66c-115">Specific guidance around the three primary interaction models and the components and patterns required for each.</span></span>
* <span data-ttu-id="5f66c-116">補充指引，說明我們的平台具備的其他優勢。</span><span class="sxs-lookup"><span data-stu-id="5f66c-116">Supplemental guidance about other benefits that our platform provides.</span></span>
* <span data-ttu-id="5f66c-117">一般指引，可針對您的開發案例協助您選取適當的互動模型。</span><span class="sxs-lookup"><span data-stu-id="5f66c-117">General guidance to help select the appropriate interaction model for your development scenario.</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="5f66c-118">多樣式互動模型</span><span class="sxs-lookup"><span data-stu-id="5f66c-118">Multimodal interaction models</span></span>

<span data-ttu-id="5f66c-119">根據我們的研究以及客戶的意見反應，我們發現有三個主要互動模型適合大部分的混合實境體驗。</span><span class="sxs-lookup"><span data-stu-id="5f66c-119">Based on our research and feedback from customers, we've discovered that three primary interaction models suit the majority of mixed reality experiences.</span></span> <span data-ttu-id="5f66c-120">在許多方面，互動模型是使用者如何完成流程的心智模型。</span><span class="sxs-lookup"><span data-stu-id="5f66c-120">In many ways, the interaction model is the user's mental model for how to complete a workflow.</span></span> <span data-ttu-id="5f66c-121">上述每種互動模型都已針對一套客戶需求進行最佳化，正確使用時每種都很方便、強大、實用。</span><span class="sxs-lookup"><span data-stu-id="5f66c-121">Each of these interaction models is optimized for a set of customer needs and is convenient, powerful, and usable when used correctly.</span></span> 

<span data-ttu-id="5f66c-122">下圖是簡化的概觀。</span><span class="sxs-lookup"><span data-stu-id="5f66c-122">The chart below is a simplified overview.</span></span> <span data-ttu-id="5f66c-123">在底下的頁面中，使用每個互動模型的詳細資訊都有連結，其中包含影像和程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="5f66c-123">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span> 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="5f66c-124"><strong>型號</strong></span><span class="sxs-lookup"><span data-stu-id="5f66c-124"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="5f66c-125"><strong>範例案例</strong></span><span class="sxs-lookup"><span data-stu-id="5f66c-125"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="5f66c-126"><strong>適合</strong></span><span class="sxs-lookup"><span data-stu-id="5f66c-126"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="5f66c-127"><strong>硬體</strong></span><span class="sxs-lookup"><span data-stu-id="5f66c-127"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="5f66c-128"><a href="hands-and-tools.md">手部和運動控制器</a></span><span class="sxs-lookup"><span data-stu-id="5f66c-128"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="5f66c-129">3D 空間體驗，例如空間版面配置與設計、內容操作或模擬。</span><span class="sxs-lookup"><span data-stu-id="5f66c-129">3D spatial experiences, such as spatial layout and design, content manipulation, or simulation.</span></span></td>
        <td><span data-ttu-id="5f66c-130">很適用於新使用者，可搭配語音、眼球追蹤或頭部注視使用。</span><span class="sxs-lookup"><span data-stu-id="5f66c-130">Great for new users coupled with voice, eye tracking or head gaze.</span></span> <span data-ttu-id="5f66c-131">學習曲線很低。</span><span class="sxs-lookup"><span data-stu-id="5f66c-131">Low learning curve.</span></span> <span data-ttu-id="5f66c-132">手部追蹤和 6DoF 控制器之間的一致 UX。</span><span class="sxs-lookup"><span data-stu-id="5f66c-132">Consistent UX across hand tracking and 6DoF controllers.</span></span></td>
        <td><span data-ttu-id="5f66c-133">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="5f66c-133">HoloLens 2</span></span><br><span data-ttu-id="5f66c-134">沉浸式頭戴裝置</span><span class="sxs-lookup"><span data-stu-id="5f66c-134">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="5f66c-135"><a href="hands-free.md">免持式</a></span><span class="sxs-lookup"><span data-stu-id="5f66c-135"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="5f66c-136">使用者雙手沒空 (例如在職培訓和維護) 時的情境體驗。</span><span class="sxs-lookup"><span data-stu-id="5f66c-136">Contextual experiences where a user's hands are occupied, such as on-the-job learning and maintenance.</span></span></td>
        <td><span data-ttu-id="5f66c-137">需要學習一下。</span><span class="sxs-lookup"><span data-stu-id="5f66c-137">Some learning required.</span></span> <span data-ttu-id="5f66c-138">如果無法使用手部，裝置可搭配語音和自然語言使用。</span><span class="sxs-lookup"><span data-stu-id="5f66c-138">If hands are unavailable, the device pairs well with voice and natural language.</span></span></td>
        <td><span data-ttu-id="5f66c-139">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="5f66c-139">HoloLens 2</span></span><br><span data-ttu-id="5f66c-140">HoloLens (第 1 代)</span><span class="sxs-lookup"><span data-stu-id="5f66c-140">HoloLens (1st gen)</span></span><br><span data-ttu-id="5f66c-141">沉浸式頭戴裝置</span><span class="sxs-lookup"><span data-stu-id="5f66c-141">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="5f66c-142"><a href="gaze-and-commit.md">目光和行動</a></span><span class="sxs-lookup"><span data-stu-id="5f66c-142"><a href="gaze-and-commit.md">Gaze and commit</a></span></span></td>
        <td><span data-ttu-id="5f66c-143">點選體驗，例如 3D 簡報、示範。</span><span class="sxs-lookup"><span data-stu-id="5f66c-143">Click-through experiences, e.g. 3D presentations, demos.</span></span></td>
        <td><span data-ttu-id="5f66c-144">需要 HMD 訓練，但不是在行動裝置上。</span><span class="sxs-lookup"><span data-stu-id="5f66c-144">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="5f66c-145">最適合用於可存取的控制器。</span><span class="sxs-lookup"><span data-stu-id="5f66c-145">Best for accessible controllers.</span></span> <span data-ttu-id="5f66c-146">最適合用於 HoloLens (第 1 代)。</span><span class="sxs-lookup"><span data-stu-id="5f66c-146">Best for HoloLens (1st gen).</span></span></td>
        <td><span data-ttu-id="5f66c-147">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="5f66c-147">HoloLens 2</span></span><br><span data-ttu-id="5f66c-148">HoloLens (第 1 代)</span><span class="sxs-lookup"><span data-stu-id="5f66c-148">HoloLens (1st gen)</span></span><br><span data-ttu-id="5f66c-149">沉浸式頭戴裝置</span><span class="sxs-lookup"><span data-stu-id="5f66c-149">Immersive headsets</span></span><br><span data-ttu-id="5f66c-150">行動 AR</span><span class="sxs-lookup"><span data-stu-id="5f66c-150">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="5f66c-151">為了確保使用者互動體驗不會有任何落差，從頭到尾遵循單一模型的指引將是最佳方式。</span><span class="sxs-lookup"><span data-stu-id="5f66c-151">To ensure that there are no gaps in the user interaction experience, it is best to follow the guidance for a single model from beginning to end.</span></span>

<span data-ttu-id="5f66c-152">下列各節會逐步說明選取及實作其中一個互動模型的步驟。</span><span class="sxs-lookup"><span data-stu-id="5f66c-152">The sections below walk through the steps for selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="5f66c-153">在此頁面結束前，您會了解我們對於下列各項的指引：</span><span class="sxs-lookup"><span data-stu-id="5f66c-153">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="5f66c-154">為您的客戶選擇互動模型</span><span class="sxs-lookup"><span data-stu-id="5f66c-154">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="5f66c-155">實作互動模型</span><span class="sxs-lookup"><span data-stu-id="5f66c-155">Implementing the interaction model</span></span>
* <span data-ttu-id="5f66c-156">互動模型之間的轉換</span><span class="sxs-lookup"><span data-stu-id="5f66c-156">Transitioning between interaction models</span></span>
* <span data-ttu-id="5f66c-157">設計後續步驟</span><span class="sxs-lookup"><span data-stu-id="5f66c-157">Design next steps</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="5f66c-158">為您的客戶選擇互動模型</span><span class="sxs-lookup"><span data-stu-id="5f66c-158">Choose an interaction model for your customer</span></span>

<span data-ttu-id="5f66c-159">開發人員和創作者通常都已考量其客戶可使用的互動類型。</span><span class="sxs-lookup"><span data-stu-id="5f66c-159">Typically, developers and creators have thought through the types of interactions that their customers can have.</span></span> <span data-ttu-id="5f66c-160">為了鼓勵以客戶為主的設計方式，我們建議您遵循下列指引來選取最適合客戶的互動模型。</span><span class="sxs-lookup"><span data-stu-id="5f66c-160">To encourage a customer-focused approach to design, we recommend the following guidance for selecting the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="5f66c-161">為什麼要遵循本指引？</span><span class="sxs-lookup"><span data-stu-id="5f66c-161">Why follow this guidance?</span></span>

* <span data-ttu-id="5f66c-162">我們的互動模型都經過客觀和主觀條件測試，例如實際和認知投入、直覺性和學習力。</span><span class="sxs-lookup"><span data-stu-id="5f66c-162">Our interaction models are tested for objective and subjective criteria, such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="5f66c-163">由於互動不同，互動模型之間的視訊/音訊能供性及物件行為也可能不同。</span><span class="sxs-lookup"><span data-stu-id="5f66c-163">Because interactions differ, visual/audio affordances and object behavior might differ between interaction models.</span></span>  
* <span data-ttu-id="5f66c-164">結合多個互動模型的組件，會引起競用能供性 (例如同時手部光線和頭部注視游標) 的風險。</span><span class="sxs-lookup"><span data-stu-id="5f66c-164">Combining parts of multiple interaction models creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor.</span></span> <span data-ttu-id="5f66c-165">這可能會造成使用者的負荷和困惑。</span><span class="sxs-lookup"><span data-stu-id="5f66c-165">This can overwhelm and confuse users.</span></span>

<span data-ttu-id="5f66c-166">以下是如何針對每個互動模型將能供性和行為最佳化的一些範例。</span><span class="sxs-lookup"><span data-stu-id="5f66c-166">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span> <span data-ttu-id="5f66c-167">我們常會看到新使用者有類似的問題，例如「如何得知系統是否能運作」  、「如何得知我可以做什麼」  、「如何得知它是否了解我剛做了什麼？」 </span><span class="sxs-lookup"><span data-stu-id="5f66c-167">We often see new users have similar questions, such as _"how do I know the system is working"_, _"how do I know what I can do"_, and _"how do I know if it understood what I just did?"_</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="5f66c-168"><strong>型號</strong></span><span class="sxs-lookup"><span data-stu-id="5f66c-168"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="5f66c-169"><strong>如何得知它是否能運作？</strong></span><span class="sxs-lookup"><span data-stu-id="5f66c-169"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="5f66c-170"><strong>如何得知我可以做什麼？</strong></span><span class="sxs-lookup"><span data-stu-id="5f66c-170"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="5f66c-171"><strong>如何得知我剛做了什麼？</strong></span><span class="sxs-lookup"><span data-stu-id="5f66c-171"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="5f66c-172"><a href="hands-and-tools.md">手部和運動控制器</a></span><span class="sxs-lookup"><span data-stu-id="5f66c-172"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="5f66c-173">我看到手狀網格、指尖能供性或手部/控制器光線。</span><span class="sxs-lookup"><span data-stu-id="5f66c-173">I see a hand mesh, a fingertip affordance, or hand/controller rays.</span></span></td>
        <td><span data-ttu-id="5f66c-174">我看到當我的手部靠近物件時會出現可握住的把手或週框方塊。</span><span class="sxs-lookup"><span data-stu-id="5f66c-174">I see grabbable handles, or a bounding box appears when my hand is near an object.</span></span></td>
        <td><span data-ttu-id="5f66c-175">我會在握住和放開時聽到聽得見的音調並看到動畫。</span><span class="sxs-lookup"><span data-stu-id="5f66c-175">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="5f66c-176"><a href="gaze-and-commit.md">頭部目光和行動</a></span><span class="sxs-lookup"><span data-stu-id="5f66c-176"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="5f66c-177">我在視野中央看到一個游標。</span><span class="sxs-lookup"><span data-stu-id="5f66c-177">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="5f66c-178">游標會在其掃過某些物件時變更狀態。</span><span class="sxs-lookup"><span data-stu-id="5f66c-178">The cursor changes state when it's over certain objects.</span></span></td>
        <td><span data-ttu-id="5f66c-179">當我採取動作時，我會看到/聽到看得見和聽得見的確認。</span><span class="sxs-lookup"><span data-stu-id="5f66c-179">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="5f66c-180"><a href="hands-free.md">免持式 (頭部注視並佇留)</a></span><span class="sxs-lookup"><span data-stu-id="5f66c-180"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="5f66c-181">我在視野中央看到一個游標。</span><span class="sxs-lookup"><span data-stu-id="5f66c-181">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="5f66c-182">當我佇留在可互動的物件上時，我會看到進度列指示器。</span><span class="sxs-lookup"><span data-stu-id="5f66c-182">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="5f66c-183">當我採取動作時，我會看到/聽到看得見和聽得見的確認。</span><span class="sxs-lookup"><span data-stu-id="5f66c-183">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="5f66c-184"><a href="hands-free.md">免持式 (語音命令)</a></span><span class="sxs-lookup"><span data-stu-id="5f66c-184"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="5f66c-185">我看到接聽指示器以及可顯示系統所聽內容的字幕。</span><span class="sxs-lookup"><span data-stu-id="5f66c-185">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="5f66c-186">我取得語音提示。</span><span class="sxs-lookup"><span data-stu-id="5f66c-186">I get voice prompts and hints.</span></span> <span data-ttu-id="5f66c-187">當我說：「我可以說什麼？」</span><span class="sxs-lookup"><span data-stu-id="5f66c-187">When I say: "What can I say?"</span></span> <span data-ttu-id="5f66c-188">我看到回饋。</span><span class="sxs-lookup"><span data-stu-id="5f66c-188">I see feedback.</span></span></td>
        <td><span data-ttu-id="5f66c-189">當我發出命令時，我會看到/聽到看得見和聽得見的確認，或在必要時取得去除混淆 UX。</span><span class="sxs-lookup"><span data-stu-id="5f66c-189">I see/hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="5f66c-190">以下是我們發現有助於小組選取互動模型的問題：</span><span class="sxs-lookup"><span data-stu-id="5f66c-190">Below are questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="5f66c-191">Q:我的使用者想要觸控全像投影和執行精準全像攝影操作嗎？</span><span class="sxs-lookup"><span data-stu-id="5f66c-191">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="5f66c-192">答：若是如此，請查看「雙手和運動控制器」互動模型，以進行精準定向和操作。</span><span class="sxs-lookup"><span data-stu-id="5f66c-192">A:  If so, check out the Hands and motion controllers interaction model for precision targeting and manipulation.</span></span>
 
2.  <span data-ttu-id="5f66c-193">Q:我的使用者需要為了實際操作而騰出雙手嗎？</span><span class="sxs-lookup"><span data-stu-id="5f66c-193">Q:  Do my users need to keep their hands free for real-world tasks?</span></span><br><br>
<span data-ttu-id="5f66c-194">答：若是如此，請查看免持式互動模型，此模型可透過注視和語音型互動提供絕佳的免持式體驗。</span><span class="sxs-lookup"><span data-stu-id="5f66c-194">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="5f66c-195">Q:我的使用者是否有時間了解我的 MR 應用程式互動，或者他們需要最低學習曲線的互動？</span><span class="sxs-lookup"><span data-stu-id="5f66c-195">Q:  Do my users have time to learn interactions for my MR application or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="5f66c-196">答：針對最低學習曲線和最直覺的互動，我們建議使用「雙手和運動控制器」模型，只要使用者能夠使用其雙手進行互動即可。</span><span class="sxs-lookup"><span data-stu-id="5f66c-196">A:  For the lowest learning curve and most intuitive interactions, we recommend the Hands and motion controllers model, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="5f66c-197">Q:我的使用者是否要使用運動控制器來指向及操作？</span><span class="sxs-lookup"><span data-stu-id="5f66c-197">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="5f66c-198">答：「雙手和運動控制器」模型包含優質運動控制器體驗的所有指引。</span><span class="sxs-lookup"><span data-stu-id="5f66c-198">A:  The Hands and motion controllers model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="5f66c-199">Q:我的使用者是否使用協助工具控制器或通用藍牙控制器，例如 Clicker？</span><span class="sxs-lookup"><span data-stu-id="5f66c-199">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="5f66c-200">答：我們建議使用所有非追蹤式控制器都適用的「頭部注視並認可」模型。</span><span class="sxs-lookup"><span data-stu-id="5f66c-200">A:  We recommend the Head-gaze and commit model for all non-tracked controllers.</span></span> <span data-ttu-id="5f66c-201">其設計訴求是可讓使用者使用簡單的「定向和行動」經歷整個體驗。</span><span class="sxs-lookup"><span data-stu-id="5f66c-201">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanism.</span></span> 
 
6.  <span data-ttu-id="5f66c-202">Q:相對於瀏覽 UI 控制項的密集版面配置，我的使用者只是經由「點選」來進行體驗 (例如在類似 3D 投影片的環境中) 嗎？</span><span class="sxs-lookup"><span data-stu-id="5f66c-202">Q: Do my users only progress through an experience by "clicking through" (for example in a 3D slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="5f66c-203">答：如果使用者不需要控制大量 UI，則「頭部注視並認可」會提供學得會的選項，使用者就不必擔心如何定向。</span><span class="sxs-lookup"><span data-stu-id="5f66c-203">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="5f66c-204">Q:我的使用者是否同時使用 HoloLens (第 1 代) 和 HoloLens 2/Windows Mixed Reality 沉浸式頭戴裝置 (VR)？</span><span class="sxs-lookup"><span data-stu-id="5f66c-204">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/Windows Mixed Reality immersive headsets (VR)?</span></span><br><br>
<span data-ttu-id="5f66c-205">答：由於「頭部注視並認可」是 HoloLens (第 1 代) 適用的互動模型，我們建議支援 HoloLens (第 1 代) 的創作者將「頭部注視並認可」用於使用者在 HoloLens (第 1 代) 頭戴式裝置上所將體驗的任何功能或模式。</span><span class="sxs-lookup"><span data-stu-id="5f66c-205">A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users will experience on a HoloLens (1st gen) headset.</span></span> <span data-ttu-id="5f66c-206">如需取得多代 HoloLens 絕佳體驗的詳細資訊，請參閱底下有關「轉換互動模型」  的一節。</span><span class="sxs-lookup"><span data-stu-id="5f66c-206">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="5f66c-207">Q:對於經常移動 (涵蓋大型空間或在空間之間移動) 的使用者，與傾向在單一空間工作的使用者而言，有何差別？</span><span class="sxs-lookup"><span data-stu-id="5f66c-207">Q: What about users who are generally mobile, covering a large space or moving between spaces, versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="5f66c-208">答：任何互動模型都適用於這些使用者。</span><span class="sxs-lookup"><span data-stu-id="5f66c-208">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="5f66c-209">[即將推出](news.md)應用程式設計專屬的詳細指引。</span><span class="sxs-lookup"><span data-stu-id="5f66c-209">More guidance specific to app design [coming soon](news.md).</span></span>


## <a name="transitioning-interaction-models"></a><span data-ttu-id="5f66c-210">轉換互動模型</span><span class="sxs-lookup"><span data-stu-id="5f66c-210">Transitioning interaction models</span></span>
<span data-ttu-id="5f66c-211">在某些使用案例中，可能需要使用多個互動模型。</span><span class="sxs-lookup"><span data-stu-id="5f66c-211">There are also use cases that might require utilizing more than one interaction model.</span></span> <span data-ttu-id="5f66c-212">例如，您應用程式的「建立流程」使用「雙手和運動控制器」  互動模型，但您想要讓現場技術人員使用免持式模式。</span><span class="sxs-lookup"><span data-stu-id="5f66c-212">For example, your application's creation flow utilizes the _"hands and motion controllers"_ interaction model, but you want to employ a hands-free mode for field technicians.</span></span>
<span data-ttu-id="5f66c-213">如果您的體驗的確需要多種互動模型，請您留意，有許多終端使用者可能會在轉換模型時遇到困難，尤其是不熟悉混合實境的使用者。</span><span class="sxs-lookup"><span data-stu-id="5f66c-213">If your experience does require multiple interaction models, please keep in mind that many users might encounter difficulty when transitioning from one model to another, especially users who are new to mixed reality.</span></span>

> [!Note]
> <span data-ttu-id="5f66c-214">我們會繼續撰寫更多適用於開發人員和設計人員的指引，讓他們了解使用多個 MR 互動模型的方式、時機和原因。</span><span class="sxs-lookup"><span data-stu-id="5f66c-214">We're constantly working on more guidance that will be available to developers and designers, informing them about the how, when, and why for using multiple MR interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="5f66c-215">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f66c-215">See also</span></span>
* [<span data-ttu-id="5f66c-216">舒適度</span><span class="sxs-lookup"><span data-stu-id="5f66c-216">Comfort</span></span>](comfort.md)
* [<span data-ttu-id="5f66c-217">眼動式互動</span><span class="sxs-lookup"><span data-stu-id="5f66c-217">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="5f66c-218">HoloLens 2 的眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="5f66c-218">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="5f66c-219">目光和行動</span><span class="sxs-lookup"><span data-stu-id="5f66c-219">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="5f66c-220">目光和停駐</span><span class="sxs-lookup"><span data-stu-id="5f66c-220">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="5f66c-221">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="5f66c-221">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="5f66c-222">手 - 手勢</span><span class="sxs-lookup"><span data-stu-id="5f66c-222">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="5f66c-223">手 - 指向和行動</span><span class="sxs-lookup"><span data-stu-id="5f66c-223">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="5f66c-224">本能互動</span><span class="sxs-lookup"><span data-stu-id="5f66c-224">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="5f66c-225">運動控制器</span><span class="sxs-lookup"><span data-stu-id="5f66c-225">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="5f66c-226">空間對應</span><span class="sxs-lookup"><span data-stu-id="5f66c-226">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="5f66c-227">空間音效設計</span><span class="sxs-lookup"><span data-stu-id="5f66c-227">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="5f66c-228">語音輸入</span><span class="sxs-lookup"><span data-stu-id="5f66c-228">Voice input</span></span>](voice-input.md)


