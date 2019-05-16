---
title: 多樣式互動概觀
description: 多樣式互動的概觀
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境、 視線、 視線目標，就會有互動，設計、 hololens MMR，multimodal
ms.openlocfilehash: 771ebe44dc984c9d4550638bef405810d86b8d69
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730826"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="99f10-104">簡介 instinctual 互動</span><span class="sxs-lookup"><span data-stu-id="99f10-104">Introducing instinctual interactions</span></span>

<span data-ttu-id="99f10-105">簡單、 instinctual 互動的原理是這整個 Microsoft 混合實境 (MMR) 平台上，從軟體的硬體。</span><span class="sxs-lookup"><span data-stu-id="99f10-105">The philosophy of simple, instinctual interactions is woven throughout the Microsoft Mixed Reality (MMR) platform, from hardware to software.</span></span>

<span data-ttu-id="99f10-106">這些 instinctual 互動會利用所有可用輸入的技術，包括無縫式的多樣式互動模型中的追蹤內到外、 手動追蹤、 追蹤、 眼睛和自然語言。</span><span class="sxs-lookup"><span data-stu-id="99f10-106">These instinctual interactions utilize all available input technologies, including inside-out tracking, hand tracking, eye tracking, and natural language, in seamless multimodal interaction models.</span></span> <span data-ttu-id="99f10-107">根據我們的研究，設計和開發 multimodals，而不是依據單一的輸入時而言至關重要 instinctive 的體驗。</span><span class="sxs-lookup"><span data-stu-id="99f10-107">Based on our research, designing and developing multimodals, and not based on single inputs, is critical when creating instinctive experiences.</span></span>

<span data-ttu-id="99f10-108">所有裝置類型也自然對齊 Instinctual 互動模型。</span><span class="sxs-lookup"><span data-stu-id="99f10-108">The Instinctual Interaction models also naturally align across device types.</span></span>  <span data-ttu-id="99f10-109">比方說，遠互動的沈浸式耳機上自由 (DoF) 控制器 6 度和 HoloLens 2 上的遠端互動使用相同的提供、 模式和行為。</span><span class="sxs-lookup"><span data-stu-id="99f10-109">For example, far interaction on an immersive headset with a 6 degrees of freedom (DoF) controller and far interaction on a HoloLens 2 use the same affordances, patterns, and behaviors.</span></span>  <span data-ttu-id="99f10-110">不只是此方便開發人員和設計工具，但它自然給使用者。</span><span class="sxs-lookup"><span data-stu-id="99f10-110">Not only is this convenient for developers and designers, but it feels natural to end users.</span></span>


<span data-ttu-id="99f10-111">最後，雖然我們辨識有數千個更有效、 更吸引人，並在 MR 神奇互動，但我們發現該刻意採用的互動模型中端對端應用程式是確保使用者是否順利的最佳辦法，有絕佳的體驗。</span><span class="sxs-lookup"><span data-stu-id="99f10-111">Lastly, while we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we have found that intentionally employing a single interaction model end to end in an application is the best way to ensure users are successful and have a great experience.</span></span>  <span data-ttu-id="99f10-112">為此，我們包含了這個互動的指導方針中的三個項目：</span><span class="sxs-lookup"><span data-stu-id="99f10-112">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="99f10-113">我們已建立結構周圍的三個主要的互動模型的元件和模式所需的每本指導方針</span><span class="sxs-lookup"><span data-stu-id="99f10-113">We've structured this guidance around the three primary interaction models and the components and patterns required for each</span></span>
* <span data-ttu-id="99f10-114">我們包含了其他優點，我們的平台提供的補充指引</span><span class="sxs-lookup"><span data-stu-id="99f10-114">We've included supplemental guidance on other benefits that our platform provides</span></span>
* <span data-ttu-id="99f10-115">我們包含了指引，幫助您選取適當的互動模型，您的案例</span><span class="sxs-lookup"><span data-stu-id="99f10-115">We've included guidance to help select the appropriate interaction model for your scenario</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="99f10-116">多樣式的互動模型</span><span class="sxs-lookup"><span data-stu-id="99f10-116">Multimodal interaction models</span></span>

<span data-ttu-id="99f10-117">根據我們的研究和與客戶合作，日期的工作，我們發現符合大部分的混合實境體驗的三種主要的互動模型。</span><span class="sxs-lookup"><span data-stu-id="99f10-117">Based on our research and work with customers to date, we've discovered three primary interaction models that suit the majority of Mixed Reality experiences.</span></span>  

<span data-ttu-id="99f10-118">您可以將這些互動模型想像成心智模型中的使用者完成其流程。</span><span class="sxs-lookup"><span data-stu-id="99f10-118">Think of these interaction models as the user's mental model for completing their flows.</span></span>

<span data-ttu-id="99f10-119">每個這些互動模型是便利又強大，而且可用於其自己的權限，和所有適用於一組客戶的需求。</span><span class="sxs-lookup"><span data-stu-id="99f10-119">Each of these interaction models is convenient, powerful, and usable in its own right, and all are optimized for a set of customer needs.</span></span> <span data-ttu-id="99f10-120">檢視圖表下方，而是針對案例、 範例和每個互動模型的優點。</span><span class="sxs-lookup"><span data-stu-id="99f10-120">View the chart below, for scenarios, examples, and benefits of each interaction model.</span></span>  

<span data-ttu-id="99f10-121">**型號**</span><span class="sxs-lookup"><span data-stu-id="99f10-121">**Model**</span></span> | <span data-ttu-id="99f10-122">**[指針和工具](https://docs.microsoft.com/en-us/windows/mixed-reality/hands-and-tools)**</span><span class="sxs-lookup"><span data-stu-id="99f10-122">**[Hands and Tools](https://docs.microsoft.com/en-us/windows/mixed-reality/hands-and-tools)**</span></span> | <span data-ttu-id="99f10-123">**[免持聽筒](https://docs.microsoft.com/en-us/windows/mixed-reality/hands-free)**</span><span class="sxs-lookup"><span data-stu-id="99f10-123">**[Hands free](https://docs.microsoft.com/en-us/windows/mixed-reality/hands-free)**</span></span> | <span data-ttu-id="99f10-124">**[視線並認可](https://docs.microsoft.com/en-us/windows/mixed-reality/gaze-and-commit?)**</span><span class="sxs-lookup"><span data-stu-id="99f10-124">**[Gaze and Commit](https://docs.microsoft.com/en-us/windows/mixed-reality/gaze-and-commit?)**</span></span>
|--------- | --------------| ------------| ---------|
<span data-ttu-id="99f10-125">**範例案例**</span><span class="sxs-lookup"><span data-stu-id="99f10-125">**Example Scenarios**</span></span> | <span data-ttu-id="99f10-126">3D 空間的體驗，例如空間版面配置與設計，內容操作或模擬</span><span class="sxs-lookup"><span data-stu-id="99f10-126">3D spatial experiences, e.g. spatial layout and design, content manipulation, or simulation</span></span> | <span data-ttu-id="99f10-127">其中使用者的手都被佔用，例如工作學習，維護的情境體驗</span><span class="sxs-lookup"><span data-stu-id="99f10-127">Contextual experiences where a user's hands are occupied, e.g. on the-job learning, maintenance</span></span>| <span data-ttu-id="99f10-128">點選體驗，例如 3D 簡報、 示範</span><span class="sxs-lookup"><span data-stu-id="99f10-128">Click-through experiences, e.g. 3D presentations, demos</span></span>
<span data-ttu-id="99f10-129">**調整**</span><span class="sxs-lookup"><span data-stu-id="99f10-129">**Fit**</span></span> | <span data-ttu-id="99f10-130">適用於新的使用者，結合的 wit 語音眼睛追蹤或前端的視線。</span><span class="sxs-lookup"><span data-stu-id="99f10-130">Great for new users, coupled wit voice, eye tracking or head gaze.</span></span> <span data-ttu-id="99f10-131">學習曲線很低。</span><span class="sxs-lookup"><span data-stu-id="99f10-131">Low learning curve.</span></span> <span data-ttu-id="99f10-132">手動追蹤和 6 DoF 控制器之間的一致 UX。</span><span class="sxs-lookup"><span data-stu-id="99f10-132">Consistent UX across hand tracking and 6 DoF controllers.</span></span> | <span data-ttu-id="99f10-133">學習所需的部分。</span><span class="sxs-lookup"><span data-stu-id="99f10-133">Some learning required.</span></span> <span data-ttu-id="99f10-134">如果實際操作是無法使用的組，與語音和自然語言</span><span class="sxs-lookup"><span data-stu-id="99f10-134">If hands are unavailable pairs well with voice and natural language</span></span> | <span data-ttu-id="99f10-135">需要訓練 HMDs 上但不是能在行動裝置。</span><span class="sxs-lookup"><span data-stu-id="99f10-135">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="99f10-136">最適合可存取的控制器最適合 HoloLens （第 1 代）</span><span class="sxs-lookup"><span data-stu-id="99f10-136">Best for accessible controllers Best for HoloLens (1st gen)</span></span> |
<span data-ttu-id="99f10-137">**硬體**</span><span class="sxs-lookup"><span data-stu-id="99f10-137">**Hardware**</span></span> | <span data-ttu-id="99f10-138">HoloLens 2 沈浸式耳機</span><span class="sxs-lookup"><span data-stu-id="99f10-138">HoloLens 2 Immersive headsets</span></span> | <span data-ttu-id="99f10-139">HoloLens 2 HoloLens （第 1 代） 沈浸式耳機</span><span class="sxs-lookup"><span data-stu-id="99f10-139">HoloLens 2 HoloLens (1st gen) Immersive headsets</span></span> | <span data-ttu-id="99f10-140">HoloLens 2 沈浸式耳機</span><span class="sxs-lookup"><span data-stu-id="99f10-140">HoloLens 2 Immersive headsets</span></span> | <span data-ttu-id="99f10-141">HoloLens 2 HoloLens （第 1 代） 沈浸式耳機 Mobile AR</span><span class="sxs-lookup"><span data-stu-id="99f10-141">HoloLens 2 HoloLens (1st gen) Immersive headsets Mobile AR</span></span> |

<span data-ttu-id="99f10-142">以下圖例和從我們的 Unity MRTK 範例內容的連結以及頁面上，是順暢地一起使用所有可用的輸入，在每個互動模型的詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="99f10-142">Detailed information for using all available inputs seamlessly together in each interaction model is on the pages that follow, as well as illustrations and links to sample content from our Unity MRTK.</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="99f10-143">選擇您的客戶互動模型</span><span class="sxs-lookup"><span data-stu-id="99f10-143">Choose an interaction model for your customer</span></span>


<span data-ttu-id="99f10-144">最有可能，開發人員與創作者也已經有一些概念記住它們想要將使用者的互動體驗的種類。</span><span class="sxs-lookup"><span data-stu-id="99f10-144">Most likely, developers and creators also already have some ideas in mind of the kinds of interaction experience they want their users to have.</span></span>
<span data-ttu-id="99f10-145">若要鼓勵客戶為主的方法，來設計，我們建議您遵循下列指導方針來選取適合您的客戶互動模型。</span><span class="sxs-lookup"><span data-stu-id="99f10-145">To encourage a customer-focused approach to design, we recommend following the guidance below to select the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="99f10-146">為什麼要遵循本指導方針？</span><span class="sxs-lookup"><span data-stu-id="99f10-146">Why follow this guidance?</span></span>

* <span data-ttu-id="99f10-147">我們的互動模型測試的目標和實體和認知投入時間、 intuitiveness，等 learnability 主觀的準則。</span><span class="sxs-lookup"><span data-stu-id="99f10-147">Our interaction models are tested for objective and subjective criteria such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="99f10-148">因為互動不同，提供視覺與音訊及物件行為可能也不同之間的互動模型。</span><span class="sxs-lookup"><span data-stu-id="99f10-148">Because interaction differs, visual and audio affordances and object behavior may also differ between the interaction models.</span></span>  
* <span data-ttu-id="99f10-149">結合多個互動模型的組件建立競爭提供，例如同時手動光線和 head 視線資料指標，會拖垮而造成使用者混淆的風險。</span><span class="sxs-lookup"><span data-stu-id="99f10-149">Combining parts of multiple interaction models together creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor, which overwhelm and confuse users.</span></span>

<span data-ttu-id="99f10-150">以下是如何提供和行為最適合用於每個互動模型的一些範例。</span><span class="sxs-lookup"><span data-stu-id="99f10-150">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span>  <span data-ttu-id="99f10-151">我們通常會看到新的使用者為類似的問題，例如 「 如何知道系統運作，如何知道我可以做什麼，和如何知道是否瞭解我剛才那樣？ 」</span><span class="sxs-lookup"><span data-stu-id="99f10-151">We often see new users as similar questions, such as "how do I know the system is working, how do I know what I can do, and how do I know if it understood what I just did?"</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="99f10-152"><strong>型號</strong></span><span class="sxs-lookup"><span data-stu-id="99f10-152"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="99f10-153"><strong>如何知道它是否運作？</strong></span><span class="sxs-lookup"><span data-stu-id="99f10-153"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="99f10-154"><strong>如何知道我可以做什麼？</strong></span><span class="sxs-lookup"><span data-stu-id="99f10-154"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="99f10-155"><strong>如何得知我只是做什麼？</strong></span><span class="sxs-lookup"><span data-stu-id="99f10-155"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="99f10-156"><a href="hands-and-tools.md">指針和工具</a></span><span class="sxs-lookup"><span data-stu-id="99f10-156"><a href="hands-and-tools.md">Hands and tools</a></span></span></td>
        <td><span data-ttu-id="99f10-157">我看到 mesh 手的形狀，我看到寫寫看功能可見性或手動 / 控制器光線。</span><span class="sxs-lookup"><span data-stu-id="99f10-157">I see a hand mesh, I see a fingertip affordance or hand/ controller rays.</span></span></td>
        <td><span data-ttu-id="99f10-158">我看到 grabbable 的控制代碼或我的手附近時，會顯示週框方塊。</span><span class="sxs-lookup"><span data-stu-id="99f10-158">I see grabbable handles or a bounding box appear when my hand is near.</span></span></td>
        <td><span data-ttu-id="99f10-159">我聽到可發出聲音的音調看動畫上擷取和釋放。</span><span class="sxs-lookup"><span data-stu-id="99f10-159">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="99f10-160"><a href="gaze-and-commit.md">頭部目光和行動</a></span><span class="sxs-lookup"><span data-stu-id="99f10-160"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="99f10-161">我看到我的檢視的中央資料指標。</span><span class="sxs-lookup"><span data-stu-id="99f10-161">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="99f10-162">Head 視線游標會變更透過某些物件時的狀態。</span><span class="sxs-lookup"><span data-stu-id="99f10-162">The head-gaze cursor changes state when over certain objects.</span></span></td>
        <td><span data-ttu-id="99f10-163">我看到/聽到視覺和聽覺確認，當我採取的動作。</span><span class="sxs-lookup"><span data-stu-id="99f10-163">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="99f10-164"><a href="hands-free.md">免持聽筒 （Head 視線和詳述）</a></span><span class="sxs-lookup"><span data-stu-id="99f10-164"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="99f10-165">我看到我的檢視的中央資料指標。</span><span class="sxs-lookup"><span data-stu-id="99f10-165">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="99f10-166">我會探討可互動的物件時，我就會看到進度列指示器。</span><span class="sxs-lookup"><span data-stu-id="99f10-166">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="99f10-167">我看到/聽到視覺和聽覺確認，當我採取的動作。</span><span class="sxs-lookup"><span data-stu-id="99f10-167">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="99f10-168"><a href="hands-free.md">免持聽筒 （語音命令）</a></span><span class="sxs-lookup"><span data-stu-id="99f10-168"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="99f10-169">我看到接聽的指標，並顯示系統聽過的標題。</span><span class="sxs-lookup"><span data-stu-id="99f10-169">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="99f10-170">取得語音提示與提示。</span><span class="sxs-lookup"><span data-stu-id="99f10-170">I get voice prompts and hints.</span></span>  <span data-ttu-id="99f10-171">我說 「 我可以說什麼？ 」</span><span class="sxs-lookup"><span data-stu-id="99f10-171">When I say "what can I say?"</span></span> <span data-ttu-id="99f10-172">我看到的意見反應。</span><span class="sxs-lookup"><span data-stu-id="99f10-172">I see feedback.</span></span></td>
        <td><span data-ttu-id="99f10-173">我看到/聽到視覺和聽覺確認我所發出的命令，或取得去除混淆時所需的 UX。</span><span class="sxs-lookup"><span data-stu-id="99f10-173">I see/ hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="99f10-174">以下是問題，我們發現說明小組選取互動模型：</span><span class="sxs-lookup"><span data-stu-id="99f10-174">Below are the questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="99f10-175">Q:我的使用者要觸控全像投影和執行精確度全像攝影版操作嗎？</span><span class="sxs-lookup"><span data-stu-id="99f10-175">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="99f10-176">答：如果是的話，請查看雙手及工具互動模型的精確度為目標和操作與實際操作或動作控制站。</span><span class="sxs-lookup"><span data-stu-id="99f10-176">A:  If so, check out the Hands and tools interaction model for precision targeting and manipulation with hands or motion controllers.</span></span>
 
2.  <span data-ttu-id="99f10-177">Q:我的使用者需要保留其免費的實際工作的實際操作嗎？</span><span class="sxs-lookup"><span data-stu-id="99f10-177">Q:  Do my users need to keep their hands free, for real-world tasks?</span></span><br><br>
<span data-ttu-id="99f10-178">答：如果是的話，看看免持聽筒互動模型，以提供絕佳免持聽筒經驗，透過視線和語音為基礎的互動。</span><span class="sxs-lookup"><span data-stu-id="99f10-178">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze- and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="99f10-179">Q:我的使用者擁有以了解我的混合的實境應用程式互動的時間或者它們需要與最低的學習曲線的互動可能？</span><span class="sxs-lookup"><span data-stu-id="99f10-179">Q:  Do my users have time to learn interactions for my mixed reality application, or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="99f10-180">答：只要使用者就能夠使用其實際操作的互動，我們會建議最低的學習曲線和最直覺的互動，雙手及工具的模型。</span><span class="sxs-lookup"><span data-stu-id="99f10-180">A:  We recommend the Hands and Tools model for the lowest learning curve and most intuitive interactions, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="99f10-181">Q:我的使用者是否指向和操作使用動作控制站？</span><span class="sxs-lookup"><span data-stu-id="99f10-181">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="99f10-182">答：雙手及工具的模型包含移動控制站更優質的體驗的所有指引。</span><span class="sxs-lookup"><span data-stu-id="99f10-182">A:  The Hands and tools model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="99f10-183">Q:我的使用者使用的協助工具控制站或通用的藍牙控制器，例如 clicker 嗎？</span><span class="sxs-lookup"><span data-stu-id="99f10-183">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="99f10-184">答：我們建議所有的非追蹤控制站的 Head 視線和認可模型。</span><span class="sxs-lookup"><span data-stu-id="99f10-184">A:  We recommend the Head-gaze and Commit model for all non-tracked controllers.</span></span>  <span data-ttu-id="99f10-185">它設計成可讓使用者周遊使用簡單的 「 目標和認可 」 技師的整個體驗。</span><span class="sxs-lookup"><span data-stu-id="99f10-185">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanic.</span></span> 
 
6.  <span data-ttu-id="99f10-186">Q:我的使用者只介紹體驗 「 按一下 」 （例如在 3d 類似投影片的環境中），相對於瀏覽密集的 UI 控制項的版面配置嗎？</span><span class="sxs-lookup"><span data-stu-id="99f10-186">Q: Do my users only progress through an experience by "clicking through" (for example in a 3d slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="99f10-187">答：如果使用者不需要控制 UI 的很多，Head 視線和認可會提供準備的選項，使用者就不必擔心如何為目標。</span><span class="sxs-lookup"><span data-stu-id="99f10-187">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="99f10-188">Q:我的使用者使用這兩個 HoloLens （第 1 代） 和 HoloLens 2 / Windows 沉浸式 （VR 耳機）</span><span class="sxs-lookup"><span data-stu-id="99f10-188">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/ Windows Immersive (VR headsets)</span></span><br><br>
<span data-ttu-id="99f10-189">答：因為 Head 視線和認可 HoloLens 互動模型 （第 1 代），我們建議最好讓支援 HoloLens 的建立者 （第 1 代） 使用 Head 視線和認可的任何功能或使用者可能會遇到 HoloLens 的模式 （第 1 代） 耳機。</span><span class="sxs-lookup"><span data-stu-id="99f10-189">A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users may experience on a HoloLens (1st gen) headset.</span></span>  <span data-ttu-id="99f10-190">請參閱下一節上*轉換互動模型*如需詳細資訊，讓多個 HoloLens 層代的絕佳體驗。</span><span class="sxs-lookup"><span data-stu-id="99f10-190">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="99f10-191">Q:功能的相關使用者是一般行動裝置 （涵蓋大型空間或空間之間移動），與使用者要在單一的空間中運作？</span><span class="sxs-lookup"><span data-stu-id="99f10-191">Q: What about for users who are generally mobile (covering a large space or moving between spaces), versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="99f10-192">答：任何互動模型將適用於這些使用者。</span><span class="sxs-lookup"><span data-stu-id="99f10-192">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="99f10-193">特定應用程式的設計的詳細指引[即將推出](index.md#news-and-notes)。</span><span class="sxs-lookup"><span data-stu-id="99f10-193">More guidance specific to app design [coming soon](index.md#news-and-notes).</span></span>


## <a name="transition-interaction-models"></a><span data-ttu-id="99f10-194">轉換互動模型</span><span class="sxs-lookup"><span data-stu-id="99f10-194">Transition interaction models</span></span>
<span data-ttu-id="99f10-195">也有一些情況下，您的使用案例可能需要使用一個以上的互動模型。</span><span class="sxs-lookup"><span data-stu-id="99f10-195">There are also cases where your use cases may require that utilizing more than one interaction model.</span></span>  <span data-ttu-id="99f10-196">比方說，您的應用程式 「 建立流程 」 會利用雙手及工具互動模型，但您想要的現場技術人員運用免持聽筒的模式。</span><span class="sxs-lookup"><span data-stu-id="99f10-196">For example, your app's "creation flow" utilizes the Hands and tools interaction model, but you want to employ a Hands-free mode for field technicians.</span></span>  

<span data-ttu-id="99f10-197">如果您的經驗並需要多種互動模型，我們發現許多終端使用者可能會遇到困難，從一種模型之間，尤其是不熟悉 MR 終端使用者的轉換。</span><span class="sxs-lookup"><span data-stu-id="99f10-197">If your experience does require multiple interaction models, we've found that many end users may encounter difficulty transitioning from one model to another -- especially end users who are new to MR.</span></span>

> [!Note]
> <span data-ttu-id="99f10-198">為了協助指南的設計人員和開發人員很難在 MR 的選擇，我們正努力使用多種互動模型的詳細指引。</span><span class="sxs-lookup"><span data-stu-id="99f10-198">To help guide designers and developers through choices that can be difficult in MR, we're working on more guidance for using multiple interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="99f10-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99f10-199">See also</span></span>
* [<span data-ttu-id="99f10-200">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="99f10-200">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="99f10-201">直接操作</span><span class="sxs-lookup"><span data-stu-id="99f10-201">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="99f10-202">指向和行動</span><span class="sxs-lookup"><span data-stu-id="99f10-202">Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="99f10-203">目光目標</span><span class="sxs-lookup"><span data-stu-id="99f10-203">Gaze targeting</span></span>](gaze-targeting.md)
* [<span data-ttu-id="99f10-204">筆勢</span><span class="sxs-lookup"><span data-stu-id="99f10-204">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="99f10-205">語音設計</span><span class="sxs-lookup"><span data-stu-id="99f10-205">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="99f10-206">運動控制器</span><span class="sxs-lookup"><span data-stu-id="99f10-206">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="99f10-207">空間音效設計</span><span class="sxs-lookup"><span data-stu-id="99f10-207">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="99f10-208">空間對應設計</span><span class="sxs-lookup"><span data-stu-id="99f10-208">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="99f10-209">舒適度</span><span class="sxs-lookup"><span data-stu-id="99f10-209">Comfort</span></span>](comfort.md)
