---
title: 多樣式互動概觀
description: 多樣式互動的概觀
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
keywords: 混合實境，視線、 視線目標，就會有互動，設計
ms.openlocfilehash: 8c578d9a67f6809df69fb132f4c46a381726596e
ms.sourcegitcommit: d6d96d552ec10cd7e6502fbbc1905432e2878325
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524343"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="82264-104">簡介 instinctual 互動</span><span class="sxs-lookup"><span data-stu-id="82264-104">Introducing instinctual interactions</span></span>
<span data-ttu-id="82264-105">簡單、 instinctual 互動的原理是這整個 Microsoft 混合實境平台。</span><span class="sxs-lookup"><span data-stu-id="82264-105">The philosophy of simple, instinctual interactions is woven throughout the Microsoft Mixed Reality platform.</span></span>  <span data-ttu-id="82264-106">我們已採取三個步驟，以確保應用程式設計師和開發人員可以提供簡單且直覺式的互動，供其客戶。</span><span class="sxs-lookup"><span data-stu-id="82264-106">We've taken three steps to ensure that application designers and developers can provide easy and intuitive interactions for their customers.</span></span> 

<span data-ttu-id="82264-107">首先，我們已確認我們令人讚嘆的感應器和輸入的技術，包括手動追蹤、 追蹤、 眼睛和自然語言，結合無縫式的多樣式互動模型。</span><span class="sxs-lookup"><span data-stu-id="82264-107">First, we've made sure our amazing sensors and input technology, including hand tracking, eye tracking, and natural language, combine into seamless multimodal interaction models.</span></span>  <span data-ttu-id="82264-108">根據我們的研究，設計和開發 multimodally-而不根據單一輸入--建立 instinctual 體驗的關鍵。</span><span class="sxs-lookup"><span data-stu-id="82264-108">Based on our research, designing and developing multimodally -- and not based on single inputs -- is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="82264-109">其次，我們了解許多開發人員目標多個裝置，不論其是指 HoloLens 2 和 HoloLens （第 1 代） 或 HoloLens 和 VR。</span><span class="sxs-lookup"><span data-stu-id="82264-109">Secondly, we recognize that many developers target multiple devices, whether that means HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  <span data-ttu-id="82264-110">因此，我們已設計我們的互動模型，才能在裝置上 （即使輸入的技術而異，每個裝置上）。</span><span class="sxs-lookup"><span data-stu-id="82264-110">So we've designed our interaction models to work across devices (even if the input technology varies on each device).</span></span>  <span data-ttu-id="82264-111">比方說，Windows 沈浸式耳機 6DoF 控制站上的遠端互動和 HoloLens 2 這兩個最互動使用的相同的提供和模式，輕鬆跨裝置應用程式。</span><span class="sxs-lookup"><span data-stu-id="82264-111">For example, far interaction on a Windows Immersive headset with a 6DoF controller and far interaction on a HoloLens 2 both use the identical affordances and patterns, making it easy for cross-device applications.</span></span> <span data-ttu-id="82264-112">不只是此方便開發人員和設計工具，但它自然給使用者。</span><span class="sxs-lookup"><span data-stu-id="82264-112">Not only is this convenient for developers and designers, but it feels natural to end users.</span></span> 

<span data-ttu-id="82264-113">最後，雖然我們辨識有數千個更有效、 更吸引人，並在 MR 神奇互動，但我們發現該刻意採用的互動模型中端對端應用程式是確保使用者是否順利的最佳辦法，有絕佳的體驗。</span><span class="sxs-lookup"><span data-stu-id="82264-113">Lastly, while we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we have found that intentionally employing a single interaction model end to end in an application is the best way to ensure users are successful and have a great experience.</span></span>  <span data-ttu-id="82264-114">為此，我們包含了這個互動的指導方針中的三個項目：</span><span class="sxs-lookup"><span data-stu-id="82264-114">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="82264-115">我們已建立結構周圍的三個主要的互動模型的元件和模式所需的每本指導方針</span><span class="sxs-lookup"><span data-stu-id="82264-115">We've structured this guidance around the three primary interaction models and the components and patterns required for each</span></span>
* <span data-ttu-id="82264-116">我們包含了其他優點，我們的平台提供的補充指引</span><span class="sxs-lookup"><span data-stu-id="82264-116">We've included supplemental guidance on other benefits that our platform provides</span></span>
* <span data-ttu-id="82264-117">我們包含了指引，幫助您選取適當的互動模型，您的案例</span><span class="sxs-lookup"><span data-stu-id="82264-117">We've included guidance to help select the appropriate interaction model for your scenario</span></span>


## <a name="three-multimodal-interaction-models"></a><span data-ttu-id="82264-118">三個多模式的互動模型</span><span class="sxs-lookup"><span data-stu-id="82264-118">Three multimodal interaction models</span></span>
<span data-ttu-id="82264-119">根據我們的研究和與客戶合作，日期的工作，我們發現三個主要的互動模型符合大部分的混合實境體驗。</span><span class="sxs-lookup"><span data-stu-id="82264-119">Based on our research and work with customers to date, we've discovered that three primary interaction models suit the majority of Mixed Reality experiences.</span></span>

<span data-ttu-id="82264-120">在許多方面的互動模型是使用者的心智模型完成其流程。</span><span class="sxs-lookup"><span data-stu-id="82264-120">In many ways, the interaction model  is the user's mental model for completing their flows.</span></span>  <span data-ttu-id="82264-121">每個這些互動模型最適合客戶需求的一組，每一個是便利又強大，而且可用於自己的權限。</span><span class="sxs-lookup"><span data-stu-id="82264-121">Each of these interaction models is optimized for a set of customer needs, and each is convenient, powerful, and usable in its own right.</span></span> 

<span data-ttu-id="82264-122">下列圖表是簡化的概觀。</span><span class="sxs-lookup"><span data-stu-id="82264-122">The chart below is a simplified overview.</span></span>  <span data-ttu-id="82264-123">使用每個互動模型的詳細的資訊會在下方的頁面，即可使用影像和程式碼範例連結。</span><span class="sxs-lookup"><span data-stu-id="82264-123">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span>  

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="82264-124"><strong>型號</strong></span><span class="sxs-lookup"><span data-stu-id="82264-124"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="82264-125"><strong>範例案例</strong></span><span class="sxs-lookup"><span data-stu-id="82264-125"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="82264-126"><strong>調整</strong></span><span class="sxs-lookup"><span data-stu-id="82264-126"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="82264-127"><strong>硬體</strong></span><span class="sxs-lookup"><span data-stu-id="82264-127"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="82264-128"><a href="hands-and-tools.md">指針和工具</a></span><span class="sxs-lookup"><span data-stu-id="82264-128"><a href="hands-and-tools.md">Hands and tools</a></span></span></td>
        <td><span data-ttu-id="82264-129">3D 空間的體驗</span><span class="sxs-lookup"><span data-stu-id="82264-129">3D spatial experiences</span></span><br><span data-ttu-id="82264-130">例如空間配置和設計、 操作的內容或模擬</span><span class="sxs-lookup"><span data-stu-id="82264-130">e.g. spatial layout and design, content manipulation, or simulation</span></span></td>
        <td><span data-ttu-id="82264-131">適用於新的使用者</span><span class="sxs-lookup"><span data-stu-id="82264-131">Great for new users</span></span><br><span data-ttu-id="82264-132">學習曲線很低</span><span class="sxs-lookup"><span data-stu-id="82264-132">Low learning curve</span></span><br><span data-ttu-id="82264-133">奠基於對的簡單 visual 提供</span><span class="sxs-lookup"><span data-stu-id="82264-133">Grounded in easy visual affordances</span></span><br><span data-ttu-id="82264-134">手動追蹤和 6DoF 控制站之間的一致 UX</span><span class="sxs-lookup"><span data-stu-id="82264-134">Consistent UX across hand tracking and 6DoF controllers</span></span><br><span data-ttu-id="82264-135">如果結合語音、 眼睛追蹤或前端的視線很棒</span><span class="sxs-lookup"><span data-stu-id="82264-135">Great when coupled with voice, eye tracking, or head gaze</span></span></td>
        <td><span data-ttu-id="82264-136">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="82264-136">HoloLens 2</span></span><br><span data-ttu-id="82264-137">Windows 包含 6DoF 控制站的沈浸式</span><span class="sxs-lookup"><span data-stu-id="82264-137">Windows Immersive w/ 6DoF Controllers</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="82264-138"><a href="hands-free.md">免持式</a></span><span class="sxs-lookup"><span data-stu-id="82264-138"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="82264-139">其中使用者的手佔用例如作業學習，維護的情境體驗</span><span class="sxs-lookup"><span data-stu-id="82264-139">Contextual experiences where a user's hands are occupied e.g. on the-job learning, maintenance</span></span></td>
        <td><span data-ttu-id="82264-140">有些學習所需</span><span class="sxs-lookup"><span data-stu-id="82264-140">Some learning required</span></span><br><span data-ttu-id="82264-141">如果無法使用指針</span><span class="sxs-lookup"><span data-stu-id="82264-141">If hands are unavailable</span></span><br><span data-ttu-id="82264-142">與語音和自然語言的配對</span><span class="sxs-lookup"><span data-stu-id="82264-142">pairs well with voice and natural language</span></span></td>
        <td><span data-ttu-id="82264-143">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="82264-143">HoloLens 2</span></span><br><span data-ttu-id="82264-144">HoloLens （第 1 代）</span><span class="sxs-lookup"><span data-stu-id="82264-144">HoloLens (1st gen)</span></span><br> <span data-ttu-id="82264-145">沈浸式 Windows</span><span class="sxs-lookup"><span data-stu-id="82264-145">Windows Immersive</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="82264-146"><a href="gaze-and-commit.md">頭部目光和行動</a></span><span class="sxs-lookup"><span data-stu-id="82264-146"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="82264-147">點選體驗例如 3D 簡報、 示範</span><span class="sxs-lookup"><span data-stu-id="82264-147">Click-through experiences e.g. 3D presentations, demos</span></span></td>
        <td><span data-ttu-id="82264-148">需要訓練 HMDs 上但不是能在行動裝置</span><span class="sxs-lookup"><span data-stu-id="82264-148">Requires training on HMDs but not on mobile</span></span><br><span data-ttu-id="82264-149">最適合可存取的控制站</span><span class="sxs-lookup"><span data-stu-id="82264-149">Best for accessible controllers</span></span><br><span data-ttu-id="82264-150">最適合 HoloLens （第 1 代）</span><span class="sxs-lookup"><span data-stu-id="82264-150">Best for HoloLens (1st gen)</span></span></td>
        <td><span data-ttu-id="82264-151">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="82264-151">HoloLens 2</span></span><br><span data-ttu-id="82264-152">HoloLens （第 1 代）</span><span class="sxs-lookup"><span data-stu-id="82264-152">HoloLens (1st gen)</span></span><br> <span data-ttu-id="82264-153">沈浸式 Windows</span><span class="sxs-lookup"><span data-stu-id="82264-153">Windows Immersive</span></span><br> <span data-ttu-id="82264-154">Mobile AR</span><span class="sxs-lookup"><span data-stu-id="82264-154">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="82264-155">請確定沒有任何間距或您的體驗的互動中出現漏洞的最佳方式是遵循從開始到結束的單一模型的指引。</span><span class="sxs-lookup"><span data-stu-id="82264-155">The best way to ensure there are no gaps or holes in the interaction for your experience is to follow the guidance for a single model from beginning to end.</span></span> 

<span data-ttu-id="82264-156">為了加快速度設計和開發，我們包含了詳細的資訊和連結的影像和程式碼範例在我們的每個模型的涵蓋範圍內。</span><span class="sxs-lookup"><span data-stu-id="82264-156">To speed design and development, we've included detailed information and links to images and code samples within our coverage of each model.</span></span>

<span data-ttu-id="82264-157">但首先，下列各節會逐步選取及實作其中一個互動模型。</span><span class="sxs-lookup"><span data-stu-id="82264-157">But first, the sections below walk through the steps of selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="82264-158">結束此頁面時，您會先了解我們的指引：</span><span class="sxs-lookup"><span data-stu-id="82264-158">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="82264-159">選擇您的客戶互動模型</span><span class="sxs-lookup"><span data-stu-id="82264-159">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="82264-160">使用互動模型的指導方針</span><span class="sxs-lookup"><span data-stu-id="82264-160">Using the interaction model guidance</span></span>
* <span data-ttu-id="82264-161">互動模型之間轉換</span><span class="sxs-lookup"><span data-stu-id="82264-161">Transitioning between interaction models</span></span>
* <span data-ttu-id="82264-162">設計後續步驟</span><span class="sxs-lookup"><span data-stu-id="82264-162">Design next steps</span></span>

## <a name="choosing-an-interaction-model-for-your-customer"></a><span data-ttu-id="82264-163">選擇您的客戶互動模型</span><span class="sxs-lookup"><span data-stu-id="82264-163">Choosing an interaction model for your customer</span></span>

<span data-ttu-id="82264-164">最有可能，開發人員與創作者已經有一些概念記住它們想要為其使用者的互動體驗的種類。</span><span class="sxs-lookup"><span data-stu-id="82264-164">Most likely, developers and creators already have some ideas in mind of the kinds of interaction experience they want for their users.</span></span>
<span data-ttu-id="82264-165">若要鼓勵客戶為主的方法，來設計，我們建議您遵循下列指導方針來選取適合您的客戶互動模型。</span><span class="sxs-lookup"><span data-stu-id="82264-165">To encourage a customer-focused approach to design, we recommend following the guidance below to select the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="82264-166">為什麼要遵循本指導方針？</span><span class="sxs-lookup"><span data-stu-id="82264-166">Why follow this guidance?</span></span>

* <span data-ttu-id="82264-167">我們的互動模型測試的目標和實體和認知投入時間、 intuitiveness，等 learnability 主觀的準則。</span><span class="sxs-lookup"><span data-stu-id="82264-167">Our interaction models are tested for objective and subjective criteria such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="82264-168">因為互動不同，提供視覺與音訊及物件行為可能也不同之間的互動模型。</span><span class="sxs-lookup"><span data-stu-id="82264-168">Because interaction differs, visual and audio affordances and object behavior may also differ between the interaction models.</span></span>  
* <span data-ttu-id="82264-169">結合多個互動模型的組件建立競爭提供，例如同時手動光線和視線資料指標，會拖垮而造成使用者混淆的風險。</span><span class="sxs-lookup"><span data-stu-id="82264-169">Combining parts of multiple interaction models together creates the risk of competing affordances, such as simultaneous hand rays and a gaze cursor, which overwhelm and confuse users.</span></span>

<span data-ttu-id="82264-170">以下是如何提供和行為最適合用於每個互動模型的一些範例。</span><span class="sxs-lookup"><span data-stu-id="82264-170">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span>  <span data-ttu-id="82264-171">我們通常會看到新的使用者為類似的問題，例如 「 如何知道系統運作，如何知道我可以做什麼，和如何知道是否瞭解我剛才那樣？ 」</span><span class="sxs-lookup"><span data-stu-id="82264-171">We often see new users as similar questions, such as "how do I know the system is working, how do I know what I can do, and how do I know if it understood what I just did?"</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="82264-172"><strong>型號</strong></span><span class="sxs-lookup"><span data-stu-id="82264-172"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="82264-173"><strong>如何知道它是否運作？</strong></span><span class="sxs-lookup"><span data-stu-id="82264-173"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="82264-174"><strong>如何知道我可以做什麼？</strong></span><span class="sxs-lookup"><span data-stu-id="82264-174"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="82264-175"><strong>如何得知我只是做什麼？</strong></span><span class="sxs-lookup"><span data-stu-id="82264-175"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="82264-176"><a href="hands-and-tools.md">指針和工具</a></span><span class="sxs-lookup"><span data-stu-id="82264-176"><a href="hands-and-tools.md">Hands and tools</a></span></span></td>
        <td><span data-ttu-id="82264-177">我看到 mesh 手的形狀，我看到寫寫看功能可見性或手動 / 控制器光線。</span><span class="sxs-lookup"><span data-stu-id="82264-177">I see a hand mesh, I see a fingertip affordance or hand/ controller rays.</span></span></td>
        <td><span data-ttu-id="82264-178">我看到 grabbable 的控制代碼或我的手附近時，會顯示週框方塊。</span><span class="sxs-lookup"><span data-stu-id="82264-178">I see grabbable handles or a bounding box appear when my hand is near.</span></span></td>
        <td><span data-ttu-id="82264-179">我聽到可發出聲音的音調看動畫上擷取和釋放。</span><span class="sxs-lookup"><span data-stu-id="82264-179">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="82264-180"><a href="gaze-and-commit.md">頭部目光和行動</a></span><span class="sxs-lookup"><span data-stu-id="82264-180"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="82264-181">我看到我的檢視的中央資料指標。</span><span class="sxs-lookup"><span data-stu-id="82264-181">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="82264-182">視線游標會變更透過某些物件時的狀態。</span><span class="sxs-lookup"><span data-stu-id="82264-182">The gaze cursor changes state when over certain objects.</span></span></td>
        <td><span data-ttu-id="82264-183">我看到/聽到視覺和聽覺確認，當我採取的動作。</span><span class="sxs-lookup"><span data-stu-id="82264-183">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="82264-184"><a href="hands-free.md">免持聽筒 （視線和詳述）</a></span><span class="sxs-lookup"><span data-stu-id="82264-184"><a href="hands-free.md">Hands-free (Gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="82264-185">我看到我的檢視的中央資料指標。</span><span class="sxs-lookup"><span data-stu-id="82264-185">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="82264-186">我會探討可互動的物件時，我就會看到進度列指示器。</span><span class="sxs-lookup"><span data-stu-id="82264-186">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="82264-187">我看到/聽到視覺和聽覺確認，當我採取的動作。</span><span class="sxs-lookup"><span data-stu-id="82264-187">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="82264-188"><a href="hands-free.md">免持聽筒 （語音命令）</a></span><span class="sxs-lookup"><span data-stu-id="82264-188"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="82264-189">我看到接聽的指標，並顯示系統聽過的標題。</span><span class="sxs-lookup"><span data-stu-id="82264-189">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="82264-190">取得語音提示與提示。</span><span class="sxs-lookup"><span data-stu-id="82264-190">I get voice prompts and hints.</span></span>  <span data-ttu-id="82264-191">我說 「 我可以說什麼？ 」</span><span class="sxs-lookup"><span data-stu-id="82264-191">When I say "what can I say?"</span></span> <span data-ttu-id="82264-192">我看到的意見反應。</span><span class="sxs-lookup"><span data-stu-id="82264-192">I see feedback.</span></span></td>
        <td><span data-ttu-id="82264-193">我看到/聽到視覺和聽覺確認我所發出的命令，或取得去除混淆時所需的 UX。</span><span class="sxs-lookup"><span data-stu-id="82264-193">I see/ hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="82264-194">以下是問題，我們發現說明小組選取互動模型：</span><span class="sxs-lookup"><span data-stu-id="82264-194">Below are the questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="82264-195">Q:我的使用者要觸控全像投影和執行精確度全像攝影版操作嗎？</span><span class="sxs-lookup"><span data-stu-id="82264-195">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span>
<span data-ttu-id="82264-196">答：如果是的話，請查看雙手及工具互動模型的精確度為目標和操作與實際操作或動作控制站。</span><span class="sxs-lookup"><span data-stu-id="82264-196">A:  If so, check out the Hands and Tools interaction model for precision targeting and manipulation with hands or motion controllers.</span></span>
 
2.  <span data-ttu-id="82264-197">Q:我的使用者需要保留其免費的實際工作的實際操作嗎？</span><span class="sxs-lookup"><span data-stu-id="82264-197">Q:  Do my users need to keep their hands free, for real-world tasks?</span></span>
<span data-ttu-id="82264-198">答：如果是的話，看看免持聽筒互動模型，以提供絕佳免持聽筒經驗，透過視線和語音為基礎的互動。</span><span class="sxs-lookup"><span data-stu-id="82264-198">A:  If so, take a look at the Hands-Free interaction model, which provides a great hands-free experience through gaze- and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="82264-199">Q:我的使用者擁有以了解我的混合的實境應用程式互動的時間或者它們需要與最低的學習曲線的互動可能？</span><span class="sxs-lookup"><span data-stu-id="82264-199">Q:  Do my users have time to learn interactions for my mixed reality application, or do they need the interactions with the lowest learning curve possible?</span></span>
<span data-ttu-id="82264-200">答：只要使用者就能夠使用其實際操作的互動，我們會建議最低的學習曲線和最直覺的互動，雙手及工具的模型。</span><span class="sxs-lookup"><span data-stu-id="82264-200">A:  We recommend the Hands and Tools model for the lowest learning curve and most intuitive interactions, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="82264-201">Q:我的使用者是否指向和操作使用動作控制站？</span><span class="sxs-lookup"><span data-stu-id="82264-201">Q:  Do my users use motion controllers for pointing and manipulation?</span></span>
<span data-ttu-id="82264-202">答：雙手及工具的模型包含移動控制站更優質的體驗的所有指引。</span><span class="sxs-lookup"><span data-stu-id="82264-202">A:  The Hands and Tools model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="82264-203">Q:我的使用者使用的協助工具控制站或通用的藍牙控制器，例如 clicker 嗎？</span><span class="sxs-lookup"><span data-stu-id="82264-203">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span>
<span data-ttu-id="82264-204">答：我們建議所有的非追蹤控制站的 Head 視線和認可模型。</span><span class="sxs-lookup"><span data-stu-id="82264-204">A:  We recommend the Head-gaze and commit model for all non-tracked controllers.</span></span>  <span data-ttu-id="82264-205">它設計成可讓使用者周遊使用簡單的 「 目標和認可 」 技師的整個體驗。</span><span class="sxs-lookup"><span data-stu-id="82264-205">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanic.</span></span> 
 
6.  <span data-ttu-id="82264-206">Q:我的使用者只介紹體驗 「 按一下 」 （例如在 3d 類似投影片的環境中），相對於瀏覽密集的 UI 控制項的版面配置嗎？</span><span class="sxs-lookup"><span data-stu-id="82264-206">Q: Do my users only progress through an experience by "clicking through" (for example in a 3d slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span>
<span data-ttu-id="82264-207">答：如果使用者不需要控制 UI 的很多，Head 視線和認可會提供準備的選項，使用者就不必擔心如何為目標。</span><span class="sxs-lookup"><span data-stu-id="82264-207">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="82264-208">Q:我的使用者使用這兩個 HoloLens （第 1 代） 和 HoloLens 2 / Windows 沉浸式 （VR 耳機） 的 a:因為 Head 視線和認可 HoloLens 互動模型 （第 1 代），我們建議最好讓支援 HoloLens 的建立者 （第 1 代） 使用 Head 視線和認可的任何功能或使用者可能會遇到 HoloLens 的模式 （第 1 代） 耳機。</span><span class="sxs-lookup"><span data-stu-id="82264-208">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/ Windows Immersive (VR headsets) A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users may experience on a HoloLens (1st gen) headset.</span></span>  <span data-ttu-id="82264-209">請參閱下一節上*轉換互動模型*如需詳細資訊，讓多個 HoloLens 層代的絕佳體驗。</span><span class="sxs-lookup"><span data-stu-id="82264-209">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="82264-210">Q:功能的相關使用者是一般行動裝置 （涵蓋大型空間或空間之間移動），與使用者要在單一的空間中運作？</span><span class="sxs-lookup"><span data-stu-id="82264-210">Q: What about for users who are generally mobile (covering a large space or moving between spaces), versus users who tend to work in a single space?</span></span>  
<span data-ttu-id="82264-211">答：任何互動模型將適用於這些使用者。</span><span class="sxs-lookup"><span data-stu-id="82264-211">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="82264-212">特定應用程式的設計的詳細指引[即將推出](index.md#news-and-notes)。</span><span class="sxs-lookup"><span data-stu-id="82264-212">More guidance specific to app design [coming soon](index.md#news-and-notes).</span></span>


## <a name="transition-interaction-models"></a><span data-ttu-id="82264-213">轉換互動模型</span><span class="sxs-lookup"><span data-stu-id="82264-213">Transition interaction models</span></span>
<span data-ttu-id="82264-214">也有一些情況下，您的使用案例可能需要使用一個以上的互動模型。</span><span class="sxs-lookup"><span data-stu-id="82264-214">There are also cases where your use cases may require that utilizing more than one interaction model.</span></span>  <span data-ttu-id="82264-215">比方說，您的應用程式 「 建立流程 」 會利用雙手及工具互動模型，但您想要的現場技術人員運用免持聽筒的模式。</span><span class="sxs-lookup"><span data-stu-id="82264-215">For example, your app's "creation flow" utilizes the Hands and tools interaction model, but you want to employ a Hands-free mode for field technicians.</span></span>  

<span data-ttu-id="82264-216">如果您的經驗並需要多種互動模型，我們發現許多終端使用者可能會遇到困難，從一種模型之間，尤其是不熟悉 MR 終端使用者的轉換。</span><span class="sxs-lookup"><span data-stu-id="82264-216">If your experience does require multiple interaction models, we've found that many end users may encounter difficulty transitioning from one model to another -- especially end users who are new to MR.</span></span>

> [!Note]
> <span data-ttu-id="82264-217">為了協助指南的設計人員和開發人員很難在 MR 的選擇，我們正努力使用多種互動模型的詳細指引。</span><span class="sxs-lookup"><span data-stu-id="82264-217">To help guide designers and developers through choices that can be difficult in MR, we're working on more guidance for using multiple interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="82264-218">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82264-218">See also</span></span>
* [<span data-ttu-id="82264-219">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="82264-219">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="82264-220">直接操作</span><span class="sxs-lookup"><span data-stu-id="82264-220">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="82264-221">指向和行動</span><span class="sxs-lookup"><span data-stu-id="82264-221">Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="82264-222">目光目標</span><span class="sxs-lookup"><span data-stu-id="82264-222">Gaze targeting</span></span>](gaze-targeting.md)
* [<span data-ttu-id="82264-223">筆勢</span><span class="sxs-lookup"><span data-stu-id="82264-223">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="82264-224">語音設計</span><span class="sxs-lookup"><span data-stu-id="82264-224">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="82264-225">運動控制器</span><span class="sxs-lookup"><span data-stu-id="82264-225">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="82264-226">空間音效設計</span><span class="sxs-lookup"><span data-stu-id="82264-226">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="82264-227">空間對應設計</span><span class="sxs-lookup"><span data-stu-id="82264-227">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="82264-228">舒適度</span><span class="sxs-lookup"><span data-stu-id="82264-228">Comfort</span></span>](comfort.md)
