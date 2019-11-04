---
title: 不需要用手
description: 將您的應用程式優化以進行無人參與
author: liamartinez
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Mixed Reality，無人參與，注視，注視目標，互動，設計
ms.openlocfilehash: b2405f5dca19838271363f53ca377c4f90ca1b36
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435080"
---
# <a name="hands-free"></a><span data-ttu-id="e1320-104">不需要用手</span><span class="sxs-lookup"><span data-stu-id="e1320-104">Hands-free</span></span>

## <a name="scenarios"></a><span data-ttu-id="e1320-105">案例</span><span class="sxs-lookup"><span data-stu-id="e1320-105">Scenarios</span></span>

<span data-ttu-id="e1320-106">如[互動模型總覽](interaction-fundamentals.md)中所述，一旦識別出您的使用者及其目標之後，請自問他們在完成工作時可能面臨的環境或狀況挑戰。</span><span class="sxs-lookup"><span data-stu-id="e1320-106">As outlined in the [interaction model overview](interaction-fundamentals.md), once you have identified your users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="e1320-107">例如，許多使用者需要使用他們的手來完成其真實世界的目標，而且他們將難以與以實際操作和控制器為基礎的介面互動。</span><span class="sxs-lookup"><span data-stu-id="e1320-107">For example, many users need to use their hands to accomplish their real-world goals, and they will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="e1320-108">某些特定案例包括：</span><span class="sxs-lookup"><span data-stu-id="e1320-108">Some specific scenarios include:</span></span> 
* <span data-ttu-id="e1320-109">透過工作進行引導，而使用者的手忙碌中</span><span class="sxs-lookup"><span data-stu-id="e1320-109">Being guided through a task, while the user's hands are busy</span></span>
* <span data-ttu-id="e1320-110">當使用者的手忙碌時參考素材</span><span class="sxs-lookup"><span data-stu-id="e1320-110">Referencing materials while the user's hands are busy</span></span>
* <span data-ttu-id="e1320-111">手形疲勞</span><span class="sxs-lookup"><span data-stu-id="e1320-111">Hand fatigue</span></span>
* <span data-ttu-id="e1320-112">無法追蹤的手套</span><span class="sxs-lookup"><span data-stu-id="e1320-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="e1320-113">親自攜帶東西</span><span class="sxs-lookup"><span data-stu-id="e1320-113">Carrying something in their hands</span></span>
* <span data-ttu-id="e1320-114">執行大型手勢的社交 awkwardness</span><span class="sxs-lookup"><span data-stu-id="e1320-114">Social awkwardness to perform large hand gestures</span></span>
* <span data-ttu-id="e1320-115">緊密空格</span><span class="sxs-lookup"><span data-stu-id="e1320-115">Tight spaces</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="e1320-116">無人參與形式</span><span class="sxs-lookup"><span data-stu-id="e1320-116">Hands-free modalities</span></span>

### <a name="voice-inputvoice-inputmd"></a>[<span data-ttu-id="e1320-117">語音輸入</span><span class="sxs-lookup"><span data-stu-id="e1320-117">Voice input</span></span>](voice-input.md)

<span data-ttu-id="e1320-118">使用您的語音來命令和控制介面提供便利的方式來操作無人參與，並視需要使用快捷方式來彈性略過多個步驟。</span><span class="sxs-lookup"><span data-stu-id="e1320-118">Using your voice to command and control an interface offers a convenient way to operate hands-free and to use shortcuts to flexibly skip multiple steps if desired.</span></span> <span data-ttu-id="e1320-119">使用語音輸入時，使用者可以直接讀取任何按鈕的名稱來啟用它（「_見它，說它」）_ ，然後與可為您完成工作的數位代理程式對話。</span><span class="sxs-lookup"><span data-stu-id="e1320-119">With voice input, the user can simply read any button's name out loud to activate it _("see it, say it")_ and converse with a digital agent who can accomplish tasks for you.</span></span>


### <a name="gaze-and-dwellgaze-and-dwellmd"></a>[<span data-ttu-id="e1320-120">目光和停駐</span><span class="sxs-lookup"><span data-stu-id="e1320-120">Gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="e1320-121">在某些實際操作的情況下，使用您的語音並不是理想或甚至不可能。</span><span class="sxs-lookup"><span data-stu-id="e1320-121">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="e1320-122">較高的處理站環境、隱私權或社交規範都可以是條件約束。</span><span class="sxs-lookup"><span data-stu-id="e1320-122">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="e1320-123">[監看式] 和 [停留] 模型可讓使用者導覽應用程式，而不需要任何額外的輸入，並將其放在其眼或前端中：使用者只要在目標上保留撥雲見日（及其頭部或眼睛）並 lingers，即可啟動它。</span><span class="sxs-lookup"><span data-stu-id="e1320-123">The gaze + dwell model allows the user to navigate an app without any additional input aside from their eye or head gaze: The user simply keeps gazing (with their head or eyes) at the target and lingers there for a moment to activate it.</span></span> <span data-ttu-id="e1320-124">若要深入瞭解您的眼睛 + 停留的個別設計考慮，請查看[眼中的](gaze-and-dwell-eyes.md)[監看式] 和 [列印頭] [+](gaze-and-dwell-head.md)[停留]。</span><span class="sxs-lookup"><span data-stu-id="e1320-124">To learn more about the individual design considerations for gaze + dwell, check out [eye-gaze + dwell](gaze-and-dwell-eyes.md) and [head-gaze + dwell](gaze-and-dwell-head.md).</span></span>


## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="e1320-125">在手上自由轉換</span><span class="sxs-lookup"><span data-stu-id="e1320-125">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="e1320-126">在這些情況下，您可以將您的手與全像位置互動以進行命令和導覽，其範圍必須是對應用程式進行端對端作業的絕對需求，以方便使用者在任何時間進行轉換。階段.</span><span class="sxs-lookup"><span data-stu-id="e1320-126">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the application, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="e1320-127">如果應用程式的需求是一律會使用無人參與，不論是使用 [停留]、[自訂語音命令] 或 [單一語音] 命令，請按一下 [選取]，然後務必在您的 UI 中做出適當的便利。</span><span class="sxs-lookup"><span data-stu-id="e1320-127">If the requirement of the application is that it will always be used hands-free, whether by using dwell, custom voice commands, or the single voice command, "select", then make sure to make the appropriate accommodations in your UI.</span></span> 

<span data-ttu-id="e1320-128">如果您的目標使用者必須自行決定是否要從手中自由切換，則請務必考慮下列原則。</span><span class="sxs-lookup"><span data-stu-id="e1320-128">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take the following principles into account.</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="e1320-129">假設使用者已處於想要切換的模式</span><span class="sxs-lookup"><span data-stu-id="e1320-129">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="e1320-130">比方說，如果使用者在工廠中，觀賞 HoloLens 上的影片參照，並決定要開始使用扳手，她很可能會開始自由操作，而不需要放下扳手來按下按鈕。</span><span class="sxs-lookup"><span data-stu-id="e1320-130">For instance, if the user is on the factory floor, watching a video reference on her HoloLens, and decides to pick up a wrench to start working, she most likely would start working in hands-free without having to put down the wrench to press a button.</span></span> <span data-ttu-id="e1320-131">她應該能夠使用語音命令叫用語音會話，停留在已經可見的 UI 上，以開始停留，或說出「select」這個字。</span><span class="sxs-lookup"><span data-stu-id="e1320-131">She should be able to invoke a voice session with a voice command, dwell on an already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="e1320-132">使用者應具備下列功能：</span><span class="sxs-lookup"><span data-stu-id="e1320-132">The user should have the ability to:</span></span> 
* <span data-ttu-id="e1320-133">在免實習的情況下切換到無人參與</span><span class="sxs-lookup"><span data-stu-id="e1320-133">Switch to hands-free while hands-free</span></span>
* <span data-ttu-id="e1320-134">改用手</span><span class="sxs-lookup"><span data-stu-id="e1320-134">Switch to hands with your hands</span></span>
* <span data-ttu-id="e1320-135">使用控制器切換到控制器</span><span class="sxs-lookup"><span data-stu-id="e1320-135">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="e1320-136">建立切換模式的重複方式</span><span class="sxs-lookup"><span data-stu-id="e1320-136">Create redundant ways to switch modes</span></span>
<span data-ttu-id="e1320-137">第一個原則是關於 access，第二個是關於可用性。</span><span class="sxs-lookup"><span data-stu-id="e1320-137">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="e1320-138">不應該只有一種方法可以在模式之間進行轉換。</span><span class="sxs-lookup"><span data-stu-id="e1320-138">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="e1320-139">部分範例如下：</span><span class="sxs-lookup"><span data-stu-id="e1320-139">Some examples would be:</span></span> 
* <span data-ttu-id="e1320-140">開始語音互動的按鈕</span><span class="sxs-lookup"><span data-stu-id="e1320-140">A button to begin voice interactions</span></span>
* <span data-ttu-id="e1320-141">用來轉換至的語音命令，使用頭部注視和停留</span><span class="sxs-lookup"><span data-stu-id="e1320-141">A voice command to transition to, using head-gaze and dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="e1320-142">新增戲劇的虛線</span><span class="sxs-lookup"><span data-stu-id="e1320-142">Add a dash of drama</span></span>
<span data-ttu-id="e1320-143">模式切換是一項很重要的事，那就是當這些轉換發生時，它們是明確的，甚至是很大的切換，讓使用者知道發生了什麼事。</span><span class="sxs-lookup"><span data-stu-id="e1320-143">A mode switch is a big deal--it is important that when these transitions happen that they be an explicit, even a dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="e1320-144">可用性檢查清單</span><span class="sxs-lookup"><span data-stu-id="e1320-144">Usability checklist</span></span>

<span data-ttu-id="e1320-145">**使用者是否可以執行所有內容，以及是否有任何免費的端對端功能？**</span><span class="sxs-lookup"><span data-stu-id="e1320-145">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="e1320-146">每個可互動都應該是可存取的無人參與</span><span class="sxs-lookup"><span data-stu-id="e1320-146">Every interactable should be accessible hands-free</span></span>
* <span data-ttu-id="e1320-147">請確定所有自訂手勢都有取代，例如調整大小、放置、撥動、點擊等。</span><span class="sxs-lookup"><span data-stu-id="e1320-147">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="e1320-148">確保使用者隨時都能自信地控制 UI 目前狀態、放置和詳細資訊</span><span class="sxs-lookup"><span data-stu-id="e1320-148">Ensure that the user has confident control of UI presence, placement, and verbosity at all times</span></span>
    * <span data-ttu-id="e1320-149">以現成的方式取得 UI</span><span class="sxs-lookup"><span data-stu-id="e1320-149">Getting UI out of the way</span></span>
    * <span data-ttu-id="e1320-150">定址不在 view 欄位的 UI （FOV）</span><span class="sxs-lookup"><span data-stu-id="e1320-150">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="e1320-151">我看到的內容有多少，其中</span><span class="sxs-lookup"><span data-stu-id="e1320-151">How much I see, where, when</span></span>

<span data-ttu-id="e1320-152">**如何使用正確的 affordances 來教授和加強互動的機制？**</span><span class="sxs-lookup"><span data-stu-id="e1320-152">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="e1320-153">使用者瞭解 。</span><span class="sxs-lookup"><span data-stu-id="e1320-153">Does the user understand ...</span></span>
* <span data-ttu-id="e1320-154">...它們的所在模式為何？</span><span class="sxs-lookup"><span data-stu-id="e1320-154">... What mode they are in?</span></span>
* <span data-ttu-id="e1320-155">...在此模式中，他們可以做什麼？</span><span class="sxs-lookup"><span data-stu-id="e1320-155">... What they can do in this mode?</span></span>
* <span data-ttu-id="e1320-156">...目前的狀態為何？</span><span class="sxs-lookup"><span data-stu-id="e1320-156">... What is the current state?</span></span>
* <span data-ttu-id="e1320-157">...他們可以如何轉移？</span><span class="sxs-lookup"><span data-stu-id="e1320-157">... How they can transition out?</span></span>
    
<span data-ttu-id="e1320-158">**UI 是否已針對無人參與優化？**</span><span class="sxs-lookup"><span data-stu-id="e1320-158">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="e1320-159">範例：停留 affordances 不是內建的一般2D 模式</span><span class="sxs-lookup"><span data-stu-id="e1320-159">Example: Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="e1320-160">範例：語音目標較適合使用物件反白顯示</span><span class="sxs-lookup"><span data-stu-id="e1320-160">Example: Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="e1320-161">範例：語音互動較適合需要開啟的字幕</span><span class="sxs-lookup"><span data-stu-id="e1320-161">Example: Voice interactions are better with captions that need to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="e1320-162">請參閱</span><span class="sxs-lookup"><span data-stu-id="e1320-162">See also</span></span>
* [<span data-ttu-id="e1320-163">HoloLens 2 上的眼睛追蹤</span><span class="sxs-lookup"><span data-stu-id="e1320-163">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="e1320-164">注視和認可</span><span class="sxs-lookup"><span data-stu-id="e1320-164">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="e1320-165">目光和停駐</span><span class="sxs-lookup"><span data-stu-id="e1320-165">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="e1320-166">直接操作</span><span class="sxs-lookup"><span data-stu-id="e1320-166">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="e1320-167">實習手勢</span><span class="sxs-lookup"><span data-stu-id="e1320-167">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="e1320-168">實際操作和認可</span><span class="sxs-lookup"><span data-stu-id="e1320-168">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="e1320-169">本能互動</span><span class="sxs-lookup"><span data-stu-id="e1320-169">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="e1320-170">語音輸入</span><span class="sxs-lookup"><span data-stu-id="e1320-170">Voice input</span></span>](voice-input.md)
