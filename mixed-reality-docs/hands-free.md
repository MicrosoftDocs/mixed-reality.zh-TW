---
title: 不需要用手
description: 將您的應用程式優化以進行無人參與
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Mixed Reality, 無人參與, 注視, 注視目標, 互動, 設計
ms.openlocfilehash: 7942192f644a7133335f089cfaaccfaebdd9292e
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414387"
---
# <a name="hands-free"></a><span data-ttu-id="19d70-104">不需要用手</span><span class="sxs-lookup"><span data-stu-id="19d70-104">Hands-free</span></span>



## <a name="scenarios"></a><span data-ttu-id="19d70-105">案例</span><span class="sxs-lookup"><span data-stu-id="19d70-105">Scenarios</span></span>

<span data-ttu-id="19d70-106">如[互動模型總覽](interaction-fundamentals.md)中所述, 一旦您識別出使用者及其目標之後, 請自問他們在完成工作時可能面臨的環境或狀況挑戰。</span><span class="sxs-lookup"><span data-stu-id="19d70-106">As outlined in the [Interaction model overview](interaction-fundamentals.md), once you have identified the users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="19d70-107">例如, 許多使用者需要使用他們的手來完成其真實世界的目標, 而且將難以與以實際操作和控制器為基礎的介面互動。</span><span class="sxs-lookup"><span data-stu-id="19d70-107">For example, many users need to use their hands to accomplish their real-world goals, and will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="19d70-108">某些特定案例可能是:</span><span class="sxs-lookup"><span data-stu-id="19d70-108">Some specific scenarios might be:</span></span> 
* <span data-ttu-id="19d70-109">透過工作進行引導, 而手中的人忙</span><span class="sxs-lookup"><span data-stu-id="19d70-109">Being guided through a task, while hands are busy</span></span>
* <span data-ttu-id="19d70-110">在您的手中參考材質</span><span class="sxs-lookup"><span data-stu-id="19d70-110">Referencing materials while your hands are busy</span></span>
* <span data-ttu-id="19d70-111">手形疲勞</span><span class="sxs-lookup"><span data-stu-id="19d70-111">Hand fatigue</span></span>
* <span data-ttu-id="19d70-112">無法追蹤的手套</span><span class="sxs-lookup"><span data-stu-id="19d70-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="19d70-113">攜帶東西</span><span class="sxs-lookup"><span data-stu-id="19d70-113">Carrying something</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="19d70-114">無人參與形式</span><span class="sxs-lookup"><span data-stu-id="19d70-114">Hands-free modalities</span></span>

### <a name="voice-commandingvoice-designmd"></a>[<span data-ttu-id="19d70-115">語音命令</span><span class="sxs-lookup"><span data-stu-id="19d70-115">Voice commanding</span></span>](voice-design.md)

<span data-ttu-id="19d70-116">使用您的語音來命令並控制介面, 不只允許使用者操作 handsfree, 還會略過多個步驟。</span><span class="sxs-lookup"><span data-stu-id="19d70-116">Using your voice to command and control an interface can not only allow the user to operate handsfree, but also skip multiple steps.</span></span> <span data-ttu-id="19d70-117">此種樣式的使用範圍可讓使用者直接讀取任何按鈕的名稱來啟用它, 就像 it 一樣, 可以與可為您完成工作的代理程式交談。</span><span class="sxs-lookup"><span data-stu-id="19d70-117">The usage of this modality can range from allowing the user to simply read any button's name out loud to activate it, as in See-it-say-it, to conversing with an agent who can accomplish tasks for you.</span></span>



### <a name="head-gaze-and-dwellgaze-and-dwellmd"></a>[<span data-ttu-id="19d70-118">頭部目光和停駐</span><span class="sxs-lookup"><span data-stu-id="19d70-118">Head-gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="19d70-119">在某些實際操作的情況下, 使用您的語音並不是理想或甚至不可能。</span><span class="sxs-lookup"><span data-stu-id="19d70-119">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="19d70-120">較高的處理站環境、隱私權或社交規範都可以是條件約束。</span><span class="sxs-lookup"><span data-stu-id="19d70-120">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="19d70-121">前端的 [注視 + 停留] 模型可讓使用者使用其 head 向量來導覽應用程式, 而 [延遲] 或 [俗套] 按鈕會在一段時間後啟動, 通常大約1秒左右。</span><span class="sxs-lookup"><span data-stu-id="19d70-121">The head gaze + dwell model allows the user to navigate the app by using their head vector to point, while lingering, or dwelling on a button will activate it after a certain amount of time, typically around 1 second or so.</span></span> 


## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="19d70-122">在手上自由轉換</span><span class="sxs-lookup"><span data-stu-id="19d70-122">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="19d70-123">在這些情況下, 您可以將您的手與全像位置互動以進行命令和導覽, 其範圍必須是對應用程式進行端對端作業的絕對需求, 以方便使用者在任何時間進行轉換。階段.</span><span class="sxs-lookup"><span data-stu-id="19d70-123">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the application, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="19d70-124">如果應用程式的需求是一律會使用無人參與, 不論是使用 [停留]、[語音命令] 或 [單一語音] 命令, 請按一下 [選取], 然後務必在您的 UI 中進行適當的 accomodations。</span><span class="sxs-lookup"><span data-stu-id="19d70-124">If the requirement of the application is that it will always be used hands-free, whether by using dwell, voice commands, or the single voice command, "select", then make sure to make the appropriate accomodations in your UI.</span></span> 

<span data-ttu-id="19d70-125">如果您的目標使用者必須自行決定是否要從手中自由切換, 則請務必考慮下列原則。</span><span class="sxs-lookup"><span data-stu-id="19d70-125">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take the following principles into account.</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="19d70-126">假設使用者已處於想要切換的模式</span><span class="sxs-lookup"><span data-stu-id="19d70-126">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="19d70-127">比方說, 如果使用者在工廠中, 觀賞 Hololens 上的影片參照, 並決定要開始使用扳手, 她很可能會開始在 handsfree 中工作, 而不需要減少扳手以按下按鈕。</span><span class="sxs-lookup"><span data-stu-id="19d70-127">For instance, if the user is on the factory floor, watching a video reference on her Hololens, and decides to pick up a wrench to start working, she most likely would start working in handsfree without having to put down the wrench to press a button.</span></span> <span data-ttu-id="19d70-128">她應該能夠使用語音命令叫用語音會話, 停留在已經可見的 UI 上, 以開始停留, 或說出「select」這個字。</span><span class="sxs-lookup"><span data-stu-id="19d70-128">She should be able to invoke a voice session with a voice command, dwell on an already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="19d70-129">使用者應具備下列功能:</span><span class="sxs-lookup"><span data-stu-id="19d70-129">The user should have the ability to:</span></span> 
* <span data-ttu-id="19d70-130">在免實習的情況下切換到無人參與</span><span class="sxs-lookup"><span data-stu-id="19d70-130">Switch to hands-free while hands-free</span></span>
* <span data-ttu-id="19d70-131">改用手</span><span class="sxs-lookup"><span data-stu-id="19d70-131">Switch to hands with your hands</span></span>
* <span data-ttu-id="19d70-132">使用控制器切換到控制器</span><span class="sxs-lookup"><span data-stu-id="19d70-132">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="19d70-133">建立切換模式的重複方式</span><span class="sxs-lookup"><span data-stu-id="19d70-133">Create redundant ways to switch modes</span></span>
<span data-ttu-id="19d70-134">第一個原則是關於 access, 第二個是關於可用性。</span><span class="sxs-lookup"><span data-stu-id="19d70-134">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="19d70-135">不應該只有一種方法可以在模式之間進行轉換。</span><span class="sxs-lookup"><span data-stu-id="19d70-135">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="19d70-136">部分範例如下:</span><span class="sxs-lookup"><span data-stu-id="19d70-136">Some examples would be:</span></span> 
* <span data-ttu-id="19d70-137">開始語音互動的按鈕</span><span class="sxs-lookup"><span data-stu-id="19d70-137">A button to begin voice interactions</span></span>
* <span data-ttu-id="19d70-138">用來轉換至使用注視 + 停留的語音命令</span><span class="sxs-lookup"><span data-stu-id="19d70-138">A voice command to transition to using gaze + dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="19d70-139">新增戲劇的虛線</span><span class="sxs-lookup"><span data-stu-id="19d70-139">Add a dash of drama</span></span>
<span data-ttu-id="19d70-140">模式切換是一項很重要的事, 那就是當這些轉換發生時, 它們是明確而驚人的切換, 讓使用者知道發生了什麼事。</span><span class="sxs-lookup"><span data-stu-id="19d70-140">A mode switch is a big deal--it is important that when these transitions happen that they be an explicit, even dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="19d70-141">可用性檢查清單</span><span class="sxs-lookup"><span data-stu-id="19d70-141">Usability checklist</span></span>

<span data-ttu-id="19d70-142">**使用者是否可以執行所有內容, 以及是否有任何免費的端對端功能？**</span><span class="sxs-lookup"><span data-stu-id="19d70-142">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="19d70-143">每個 interactible 都應該是可存取的無人參與</span><span class="sxs-lookup"><span data-stu-id="19d70-143">Every interactible should be accessible hands-free</span></span>
* <span data-ttu-id="19d70-144">請確定所有自訂手勢都有取代, 例如調整大小、放置、撥動、點擊等。</span><span class="sxs-lookup"><span data-stu-id="19d70-144">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="19d70-145">確保使用者隨時都能自信地控制 UI 目前狀態、放置和詳細資訊</span><span class="sxs-lookup"><span data-stu-id="19d70-145">Ensure that the user has confident control of UI presence, placement, and verbosity at all times</span></span>
    * <span data-ttu-id="19d70-146">以現成的方式取得 UI</span><span class="sxs-lookup"><span data-stu-id="19d70-146">Getting UI out of the way</span></span>
    * <span data-ttu-id="19d70-147">定址不在 view 欄位的 UI (FOV)</span><span class="sxs-lookup"><span data-stu-id="19d70-147">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="19d70-148">我看到的內容有多少, 其中</span><span class="sxs-lookup"><span data-stu-id="19d70-148">How much I see, where, when</span></span>

<span data-ttu-id="19d70-149">**如何使用正確的 affordances 來教授和加強互動的機制？**</span><span class="sxs-lookup"><span data-stu-id="19d70-149">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="19d70-150">使用者瞭解 。</span><span class="sxs-lookup"><span data-stu-id="19d70-150">Does the user understand ...</span></span>
* <span data-ttu-id="19d70-151">...它們的所在模式為何？</span><span class="sxs-lookup"><span data-stu-id="19d70-151">... What mode they are in?</span></span>
* <span data-ttu-id="19d70-152">...在此模式中, 他們可以做什麼？</span><span class="sxs-lookup"><span data-stu-id="19d70-152">... What they can do in this mode?</span></span>
* <span data-ttu-id="19d70-153">...目前的狀態為何？</span><span class="sxs-lookup"><span data-stu-id="19d70-153">... What is the current state?</span></span>
* <span data-ttu-id="19d70-154">...他們可以如何轉移？</span><span class="sxs-lookup"><span data-stu-id="19d70-154">... How they can transition out?</span></span>
    
<span data-ttu-id="19d70-155">**UI 是否已針對無人參與優化？**</span><span class="sxs-lookup"><span data-stu-id="19d70-155">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="19d70-156">範例：停留 affordances 不是內建的一般2D 模式</span><span class="sxs-lookup"><span data-stu-id="19d70-156">Example: Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="19d70-157">範例：語音目標較適合使用物件反白顯示</span><span class="sxs-lookup"><span data-stu-id="19d70-157">Example: Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="19d70-158">範例：語音互動較適合需要開啟的字幕</span><span class="sxs-lookup"><span data-stu-id="19d70-158">Example: Voice interactions are better with captions that have to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="19d70-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19d70-159">See also</span></span>
* [<span data-ttu-id="19d70-160">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="19d70-160">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="19d70-161">手部直接操作</span><span class="sxs-lookup"><span data-stu-id="19d70-161">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="19d70-162">手部指向和行動</span><span class="sxs-lookup"><span data-stu-id="19d70-162">Point and commit with hands</span></span>](point-and-commit.md)
