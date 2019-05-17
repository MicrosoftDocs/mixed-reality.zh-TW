---
title: 不需要用手
description: 最佳化您的應用程式，針對免持聽筒
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: 混合實境，免持聽筒，視線，視線目標，就會有互動，設計
ms.openlocfilehash: 59a460a0c46ace7e633381019d29af54b1061695
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629014"
---
# <a name="hands-free"></a><span data-ttu-id="cc461-104">不需要用手</span><span class="sxs-lookup"><span data-stu-id="cc461-104">Hands-free</span></span>



## <a name="scenarios"></a><span data-ttu-id="cc461-105">案例</span><span class="sxs-lookup"><span data-stu-id="cc461-105">Scenarios</span></span>

<span data-ttu-id="cc461-106">中所述[互動模型概觀](interaction-fundamentals.md)、 一次您已識別的使用者和其目標、 自問一樣來完成其工作，他們可能會面臨哪些環境或環境的挑戰。</span><span class="sxs-lookup"><span data-stu-id="cc461-106">As outlined in the [interaction model overview](interaction-fundamentals.md), once you have identified the users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="cc461-107">比方說，許多使用者需要使用其實際操作完成其真實世界的目標，並將很難與實際操作和控制站的基礎介面互動。</span><span class="sxs-lookup"><span data-stu-id="cc461-107">For example, many users need to use their hands to accomplish their real-world goals and will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="cc461-108">某些特定情況下可能是：</span><span class="sxs-lookup"><span data-stu-id="cc461-108">Some specific scenarios might be:</span></span> 
* <span data-ttu-id="cc461-109">正在引導您完成一項工作，指針是忙碌中</span><span class="sxs-lookup"><span data-stu-id="cc461-109">Being guided through a task, while hands are busy</span></span>
* <span data-ttu-id="cc461-110">您手裡忙碌時，參考資料</span><span class="sxs-lookup"><span data-stu-id="cc461-110">Referencing materials while your hands are busy</span></span>
* <span data-ttu-id="cc461-111">手狀疲勞</span><span class="sxs-lookup"><span data-stu-id="cc461-111">Hand fatigue</span></span>
* <span data-ttu-id="cc461-112">無法追蹤的手套</span><span class="sxs-lookup"><span data-stu-id="cc461-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="cc461-113">執行項目</span><span class="sxs-lookup"><span data-stu-id="cc461-113">Carrying something</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="cc461-114">免持聽筒型態</span><span class="sxs-lookup"><span data-stu-id="cc461-114">Hands-free modalities</span></span>

### <a name="voice-commandingvoice-designmd"></a>[<span data-ttu-id="cc461-115">語音命令</span><span class="sxs-lookup"><span data-stu-id="cc461-115">Voice commanding</span></span>](voice-design.md)

<span data-ttu-id="cc461-116">使用您的語音命令和控制介面可以不只允許使用者操作 handsfree，但也略過多個步驟。</span><span class="sxs-lookup"><span data-stu-id="cc461-116">Using your voice to command and control an interface can not only allow the user to operate handsfree, but also skip multiple steps.</span></span> <span data-ttu-id="cc461-117">此樣式的使用方式的範圍可以從允許使用者只讀取任何按鈕名稱大聲來啟動它，如所示，請參閱-it-say-it，來與代理程式可以為您完成的工作人員交談。</span><span class="sxs-lookup"><span data-stu-id="cc461-117">The usage of this modality can range from allowing the user to simply reading any button's name out loud to activate it, as in See-it-say-it, to conversing with an agent who can accomplish tasks for you.</span></span>



### <a name="head-gaze-and-dwellgaze-and-dwellmd"></a>[<span data-ttu-id="cc461-118">Head 視線和詳述</span><span class="sxs-lookup"><span data-stu-id="cc461-118">Head-gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="cc461-119">在某些免持聽筒的情況下，使用您的聲音不是理想或甚至可以。</span><span class="sxs-lookup"><span data-stu-id="cc461-119">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="cc461-120">大聲工廠環境、 隱私權或社交規範都可以條件約束。</span><span class="sxs-lookup"><span data-stu-id="cc461-120">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="cc461-121">標頭視線 + 探討模型可讓使用者使用其前端的向量來點，而延遲，以瀏覽應用程式或談論按鈕會啟動它之後一段時間 （通常大約 1 秒左右）。</span><span class="sxs-lookup"><span data-stu-id="cc461-121">The head gaze + dwell model allows the user to navigate the app by using their head vector to point, while lingering, or dwelling on a button will activate it after a certain amount of time (typically around 1 second or so).</span></span> 


## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="cc461-122">轉換流入和流出免持聽筒</span><span class="sxs-lookup"><span data-stu-id="cc461-122">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="cc461-123">針對這些案例中，釋放與命令和導覽全像投影互動雙手範圍可以從正在操作的應用程式端對端到便利性，使用者在任何時候，可以轉換和出的是絕對需求。</span><span class="sxs-lookup"><span data-stu-id="cc461-123">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the app, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="cc461-124">如果應用程式的需求是，它將一律會使用免持聽筒，無論是使用詳述、 語音命令或單一語音命令，"select"，則請務必在您的 UI 中進行適當的 accomodations。</span><span class="sxs-lookup"><span data-stu-id="cc461-124">If the requirement of the app is that it will always be used hands-free, whether by using dwell, voice commands, or the single voice command, "select", then make sure to make the appropriate accomodations in your UI.</span></span> 

<span data-ttu-id="cc461-125">如果您的目標使用者必須能夠從手切換至免持聽筒自行斟酌，則務必考量這些原則：</span><span class="sxs-lookup"><span data-stu-id="cc461-125">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take these principles into account:</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="cc461-126">假設使用者已在他們想要切換到的模式</span><span class="sxs-lookup"><span data-stu-id="cc461-126">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="cc461-127">比方說，如果您的使用者是在工廠，觀賞視訊她 Hololens 上的參考，並決定挑選扳手，若要開始使用，她很可能想要開始在 handsfree 不必寫下按下按鈕扳手。</span><span class="sxs-lookup"><span data-stu-id="cc461-127">For instance, if your user is on the factory floor, watching a video reference on her Hololens, and decides to pick up a wrench to start working, she most likely would like to begin working in handsfree without having to put down the wrench to press a button.</span></span> <span data-ttu-id="cc461-128">她應該要能夠叫用語音命令的語音工作階段，會探討已顯示的 UI，以開始詳述，或說出單字"select"。</span><span class="sxs-lookup"><span data-stu-id="cc461-128">She should be able to invoke a voice session with a voice command, dwell on already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="cc461-129">使用者應該能夠：</span><span class="sxs-lookup"><span data-stu-id="cc461-129">The user should have the ability to:</span></span> 
* <span data-ttu-id="cc461-130">切換至 handsfree handsfree 時</span><span class="sxs-lookup"><span data-stu-id="cc461-130">Switch to handsfree while handsfree</span></span>
* <span data-ttu-id="cc461-131">切換到您手裡使用的實際操作</span><span class="sxs-lookup"><span data-stu-id="cc461-131">Switch to hands with your hands</span></span>
* <span data-ttu-id="cc461-132">切換至使用控制器的控制站</span><span class="sxs-lookup"><span data-stu-id="cc461-132">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="cc461-133">建立備援的方式，若要切換模式</span><span class="sxs-lookup"><span data-stu-id="cc461-133">Create redundant ways to switch modes</span></span>
<span data-ttu-id="cc461-134">關於存取的第一個準則時，第二個是有關可用性。</span><span class="sxs-lookup"><span data-stu-id="cc461-134">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="cc461-135">不只應該有單一的方式來轉換流入和流出一種模式。</span><span class="sxs-lookup"><span data-stu-id="cc461-135">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="cc461-136">某些範例可能是：</span><span class="sxs-lookup"><span data-stu-id="cc461-136">Some examples would be:</span></span> 
* <span data-ttu-id="cc461-137">若要開始的語音互動的按鈕</span><span class="sxs-lookup"><span data-stu-id="cc461-137">A button to begin voice interactions</span></span>
* <span data-ttu-id="cc461-138">要轉換的語音命令，使用視線 + 詳述</span><span class="sxs-lookup"><span data-stu-id="cc461-138">A voice command to transition to using gaze + dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="cc461-139">加入劇本一層樓</span><span class="sxs-lookup"><span data-stu-id="cc461-139">Add a dash of drama</span></span>
<span data-ttu-id="cc461-140">模式參數是什麼大不了的事--很重要，這些轉換發生時，它們是個明確、 更大的參數，讓使用者知道發生了什麼事。</span><span class="sxs-lookup"><span data-stu-id="cc461-140">A mode switch is a big deal -- it is important that when these transitions happen, that they be an explicit, even dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="cc461-141">可用性檢查清單</span><span class="sxs-lookup"><span data-stu-id="cc461-141">Usability checklist</span></span>

<span data-ttu-id="cc461-142">**使用者可以做的所有項目和免持聽筒，端對端的任何作業？**</span><span class="sxs-lookup"><span data-stu-id="cc461-142">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="cc461-143">每個 interactible 必須能夠存取免持聽筒</span><span class="sxs-lookup"><span data-stu-id="cc461-143">Every interactible should be accessible hands-free</span></span>
* <span data-ttu-id="cc461-144">確定所有自訂筆勢的詳細資訊，例如調整大小、 放置、 swipes、 點選等的取代項目。</span><span class="sxs-lookup"><span data-stu-id="cc461-144">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="cc461-145">請確定使用者隨時都有信心控制 UI 的目前狀態、 位置、 詳細資訊</span><span class="sxs-lookup"><span data-stu-id="cc461-145">Ensure that the user has confident control of UI presence, placement, verbosity at all times</span></span>
    * <span data-ttu-id="cc461-146">取得 UI 的方式</span><span class="sxs-lookup"><span data-stu-id="cc461-146">Getting UI out of the way</span></span>
    * <span data-ttu-id="cc461-147">定址超出欄位的視角 (FOV) 的 UI</span><span class="sxs-lookup"><span data-stu-id="cc461-147">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="cc461-148">我看到多少，其中時</span><span class="sxs-lookup"><span data-stu-id="cc461-148">How much I see, where, when</span></span>

<span data-ttu-id="cc461-149">**互動的機制所教授和進行與右提供？**</span><span class="sxs-lookup"><span data-stu-id="cc461-149">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="cc461-150">使用者可以了解...</span><span class="sxs-lookup"><span data-stu-id="cc461-150">Does the user understand ...</span></span>
* <span data-ttu-id="cc461-151">...它們會在何種模式？</span><span class="sxs-lookup"><span data-stu-id="cc461-151">... What mode they are in?</span></span>
* <span data-ttu-id="cc461-152">...它們可以做什麼在這個模式？</span><span class="sxs-lookup"><span data-stu-id="cc461-152">... What they can do in this mode?</span></span>
* <span data-ttu-id="cc461-153">...目前的狀態為何？</span><span class="sxs-lookup"><span data-stu-id="cc461-153">... What is the current state?</span></span>
* <span data-ttu-id="cc461-154">...如何可以轉換出嗎？</span><span class="sxs-lookup"><span data-stu-id="cc461-154">... How they can transition out?</span></span>
    
<span data-ttu-id="cc461-155">**UI 最適合用於免持聽筒嗎？**</span><span class="sxs-lookup"><span data-stu-id="cc461-155">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="cc461-156">Ex.</span><span class="sxs-lookup"><span data-stu-id="cc461-156">Ex.</span></span> <span data-ttu-id="cc461-157">詳述提供不是內建於一般的 2D 模式</span><span class="sxs-lookup"><span data-stu-id="cc461-157">Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="cc461-158">Ex.</span><span class="sxs-lookup"><span data-stu-id="cc461-158">Ex.</span></span> <span data-ttu-id="cc461-159">語音目標是透過反白顯示的物件更趨完美</span><span class="sxs-lookup"><span data-stu-id="cc461-159">Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="cc461-160">Ex.</span><span class="sxs-lookup"><span data-stu-id="cc461-160">Ex.</span></span> <span data-ttu-id="cc461-161">語音互動會透過已開啟的原文字幕更趨完美</span><span class="sxs-lookup"><span data-stu-id="cc461-161">Voice interactions are better with captions that have to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="cc461-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc461-162">See also</span></span>
* [<span data-ttu-id="cc461-163">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="cc461-163">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="cc461-164">直接操作</span><span class="sxs-lookup"><span data-stu-id="cc461-164">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="cc461-165">指向和行動</span><span class="sxs-lookup"><span data-stu-id="cc461-165">Point and commit</span></span>](point-and-commit.md)