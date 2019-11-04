---
title: 混合現實應用程式的類型
description: 開發 Windows Mixed Reality 應用程式的其中一個優點，就是平臺可以從完全沉浸式虛擬環境支援的各種體驗，到使用者目前 environmentl 的淺資訊分層。
author: rwinj
ms.author: willyang
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，設計，應用程式模式
ms.openlocfilehash: 62a0b76ba7853262a46b34466a6d3b0567bc137d
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438245"
---
# <a name="types-of-mixed-reality-apps"></a><span data-ttu-id="98071-104">混合現實應用程式的類型</span><span class="sxs-lookup"><span data-stu-id="98071-104">Types of mixed reality apps</span></span>

<span data-ttu-id="98071-105">開發 Windows Mixed Reality 應用程式的優點之一，是該平台可以支援各種頻譜體驗。</span><span class="sxs-lookup"><span data-stu-id="98071-105">One of the advantages of developing apps for Windows Mixed Reality is that there is a spectrum of experiences that the platform can support.</span></span> <span data-ttu-id="98071-106">從完全沉浸式虛擬環境到使用者目前環境下的輕量資訊分層，Windows Mixed Reality 提供了一組強大的工具，可將任何體驗變為現實。</span><span class="sxs-lookup"><span data-stu-id="98071-106">From fully immersive, virtual environments, to light information layering over a user’s current environment, Windows Mixed Reality provides a robust set of tools to bring any experience to life.</span></span> <span data-ttu-id="98071-107">應用程式製作者必須在開發過程中，儘早瞭解其經驗所在的範圍。</span><span class="sxs-lookup"><span data-stu-id="98071-107">It is important for an app maker to understand early in their development process as to where along this spectrum their experience lies.</span></span> <span data-ttu-id="98071-108">這項決策最終會影響應用程式設計的構成，以及開發的技術路徑。</span><span class="sxs-lookup"><span data-stu-id="98071-108">This decision will ultimately impact both the app design makeup and the technological path for development.</span></span>

## <a name="enhanced-environment-apps-hololens-only"></a><span data-ttu-id="98071-109">增強的環境應用程式（僅限 HoloLens）</span><span class="sxs-lookup"><span data-stu-id="98071-109">Enhanced environment apps (HoloLens only)</span></span>

<span data-ttu-id="98071-110">混合現實能夠為使用者帶來價值的其中一個最強大的方式，就是在使用者目前的環境中，協助放置數位資訊或內容。</span><span class="sxs-lookup"><span data-stu-id="98071-110">One of the most powerful ways that mixed reality can bring value to users is by facilitating the placement of digital information or content in a user’s current environment.</span></span> <span data-ttu-id="98071-111">這是增強的環境應用程式。</span><span class="sxs-lookup"><span data-stu-id="98071-111">This is an enhanced environment app.</span></span> <span data-ttu-id="98071-112">這種方法很常用於應用程式，其中真實世界中的數位內容位置是重要的，而且（或）在他們的體驗期間，讓使用者的真實世界環境「呈現」成為關鍵。</span><span class="sxs-lookup"><span data-stu-id="98071-112">This approach is popular for apps where the contextual placement of digital content in the real world is paramount and/or keeping the user’s real world environment “present” during their experience is key.</span></span> <span data-ttu-id="98071-113">這種方法也可以讓使用者輕鬆地從真實世界的工作移至數位工作，也可以輕鬆地借出更證實，以承諾使用者所看到的混合現實應用程式確實屬於其環境。</span><span class="sxs-lookup"><span data-stu-id="98071-113">This approach also allows users to easily move from real world tasks to digital tasks and back easily, lending even more credence to promise that the mixed reality apps the user sees are truly a part of their environment.</span></span>

<span data-ttu-id="98071-114">![增強的環境應用程式](images/enhancedenvironmentapps-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="98071-114">![Enhanced environment apps](images/enhancedenvironmentapps-640px.jpg)</span></span><br>
<span data-ttu-id="98071-115">*增強的環境應用程式*</span><span class="sxs-lookup"><span data-stu-id="98071-115">*Enhanced environment apps*</span></span>

<span data-ttu-id="98071-116">**範例使用**</span><span class="sxs-lookup"><span data-stu-id="98071-116">**Example uses**</span></span>
* <span data-ttu-id="98071-117">混合現實的「記事本」樣式應用程式，可讓使用者在其環境中建立及放置附注</span><span class="sxs-lookup"><span data-stu-id="98071-117">A mixed reality notepad style app that allows users to create and place notes around their environment</span></span>
* <span data-ttu-id="98071-118">將混合現實電視應用程式放在舒適的觀賞位置</span><span class="sxs-lookup"><span data-stu-id="98071-118">A mixed reality television app placed in a comfortable spot for viewing</span></span>
* <span data-ttu-id="98071-119">位於廚房島上方的混合現實烹飪應用程式，可協助您進行烹飪工作</span><span class="sxs-lookup"><span data-stu-id="98071-119">A mixed reality cooking app placed above the kitchen island to assist in a cooking task</span></span>
* <span data-ttu-id="98071-120">一種混合現實應用程式，可讓使用者感受到「x 光線願景」（也就是放在上並模擬真實世界物件的全息影像，同時允許使用者看到「內部 it」 reality）</span><span class="sxs-lookup"><span data-stu-id="98071-120">A mixed reality app that gives users the feeling of “x-ray vision” (i.e. a hologram placed on top of and mimics a real world object, while allowing the user to see “inside it” holographically)</span></span>
* <span data-ttu-id="98071-121">在整個工廠中放置的混合現實注釋，可提供背景工作的必要資訊</span><span class="sxs-lookup"><span data-stu-id="98071-121">Mixed reality annotations placed throughout a factory to give worker’s necessary information</span></span>
* <span data-ttu-id="98071-122">Office 空間中的混合現實導向</span><span class="sxs-lookup"><span data-stu-id="98071-122">Mixed reality wayfinding in an office space</span></span>
* <span data-ttu-id="98071-123">混合現實桌面體驗（也就是面板遊戲樣式體驗）</span><span class="sxs-lookup"><span data-stu-id="98071-123">Mixed reality tabletop experiences (i.e. board game style experiences)</span></span>
* <span data-ttu-id="98071-124">混合現實通訊應用程式（例如 Skype）</span><span class="sxs-lookup"><span data-stu-id="98071-124">Mixed reality communication apps like Skype</span></span>

## <a name="blended-environment-apps"></a><span data-ttu-id="98071-125">混合式環境應用程式</span><span class="sxs-lookup"><span data-stu-id="98071-125">Blended environment apps</span></span>

<span data-ttu-id="98071-126">由於 Windows Mixed Reality 能夠辨識並對應使用者的環境，因此能夠建立可在使用者空間上完全重迭的數位層。</span><span class="sxs-lookup"><span data-stu-id="98071-126">Given Windows Mixed Reality’s ability to recognize and map the user's environment, it is capable of creating a digital layer that can be completely overlaid on the user’s space.</span></span> <span data-ttu-id="98071-127">精簡層會遵循使用者環境的圖形和界限，但應用程式可以選擇轉換最適合在應用程式中 immerse 使用者的特定元素。</span><span class="sxs-lookup"><span data-stu-id="98071-127">Thin layer respects the shape and boundaries of the user’s environment, but the app may choose to transform certain elements best suited to immerse the user in the app.</span></span> <span data-ttu-id="98071-128">這稱為混合式環境應用程式。</span><span class="sxs-lookup"><span data-stu-id="98071-128">This is called a blended environment app.</span></span> <span data-ttu-id="98071-129">不同于增強的環境應用程式，混合式環境應用程式可能只在意環境的足夠程度來鼓勵特定使用者行為（例如鼓勵移動或流覽），或以變更取代元素（廚房）counter 是以虛擬方式 skinned，以顯示不同的磚模式）。</span><span class="sxs-lookup"><span data-stu-id="98071-129">Unlike an enhanced environment app, blended environment apps may only care enough about the environment to best use its makeup for encouraging specific user behavior (like encouraging movement or exploration) or by replacing elements with changes (a kitchen counter is virtually skinned to show a different tile pattern).</span></span> <span data-ttu-id="98071-130">這種體驗甚至可能會將元素轉換成完全不同的物件，但仍然會保留物件的粗略維度做為其基底（廚房島會轉換成犯罪 thriller 遊戲的 dumpster）。</span><span class="sxs-lookup"><span data-stu-id="98071-130">This type of experience may even transform an element into an entirely different object, but still retain the rough dimensions of the object as its base (a kitchen island is transformed into a dumpster for a crime thriller game).</span></span>

<span data-ttu-id="98071-131">![混合式環境應用程式](images/blendedenvironmentapps-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="98071-131">![Blended environment apps](images/blendedenvironmentapps-640px.jpg)</span></span><br>
<span data-ttu-id="98071-132">*混合式環境應用程式*</span><span class="sxs-lookup"><span data-stu-id="98071-132">*Blended environment apps*</span></span>

<span data-ttu-id="98071-133">**範例使用**</span><span class="sxs-lookup"><span data-stu-id="98071-133">**Example uses**</span></span>
* <span data-ttu-id="98071-134">混合現實內部設計應用程式，可以用不同的色彩和模式繪製牆、countertops 或樓層</span><span class="sxs-lookup"><span data-stu-id="98071-134">A mixed reality interior design app that can paint walls, countertops or floors in different colors and patterns</span></span>
* <span data-ttu-id="98071-135">一種混合現實應用程式，可讓汽車設計人員在現有的汽車上，為近期的汽車重新整理分層新的設計反復專案</span><span class="sxs-lookup"><span data-stu-id="98071-135">A mixed reality app that allows an automotive designer to layer new design iterations for an upcoming car refresh on top of an existing car</span></span>
* <span data-ttu-id="98071-136">平臺已「涵蓋」，並由兒童遊戲中的混合現實水果取代</span><span class="sxs-lookup"><span data-stu-id="98071-136">A bed is “covered” and replaced by a mixed reality fruit stand in children’s game</span></span>
* <span data-ttu-id="98071-137">一台桌面「涵蓋」，並以犯罪 thriller 遊戲中的混合現實 dumpster 取代</span><span class="sxs-lookup"><span data-stu-id="98071-137">A desk is “covered” and replaced with a mixed reality dumpster in a crime thriller game</span></span>
* <span data-ttu-id="98071-138">「涵蓋」懸掛 lantern，並使用大致相同的形狀和維度來取代為 signpost</span><span class="sxs-lookup"><span data-stu-id="98071-138">A hanging lantern is “covered” and replaced with signpost using roughly the same shape and dimension</span></span>
* <span data-ttu-id="98071-139">一種應用程式，可讓使用者在其真實或沉浸式世界牆中的洞孔，以顯示神奇的世界</span><span class="sxs-lookup"><span data-stu-id="98071-139">An app that allows users to blast holes in their real or immersive world walls, which reveal a magical world</span></span>

## <a name="immersive-environment-apps"></a><span data-ttu-id="98071-140">沉浸式環境應用程式</span><span class="sxs-lookup"><span data-stu-id="98071-140">Immersive environment apps</span></span>

<span data-ttu-id="98071-141">沉浸式環境應用程式會以完全改變使用者世界的環境為中心，並可將它們放在不同的時間和空間中。</span><span class="sxs-lookup"><span data-stu-id="98071-141">Immersive environment apps are centered around an environment that completely changes the user’s world and can place them in a different time and space.</span></span> <span data-ttu-id="98071-142">這些環境可以非常真實，建立只受應用程式建立者的想像所限制的沉浸式和「驚心動魄」體驗。</span><span class="sxs-lookup"><span data-stu-id="98071-142">These environments can feel very real, creating immersive and thrilling experiences that are only limited by the app creator’s imagination.</span></span> <span data-ttu-id="98071-143">與混合式環境應用程式不同的是，當 Windows Mixed Reality 識別出使用者的空間之後，沉浸式環境應用程式可能會完全忽略使用者目前的環境，並以本身的其中一個來取代整個股票。</span><span class="sxs-lookup"><span data-stu-id="98071-143">Unlike blended environment apps, once Windows Mixed Reality identifies the user’s space, an immersive environment app may totally disregard the user’s current environment and replace it whole stock with one of its own.</span></span> <span data-ttu-id="98071-144">這些體驗也可能完全分開的時間和空間，這表示使用者可以在沉浸式體驗中，將羅馬的街道引導，而在其實際的空間中則維持不變。</span><span class="sxs-lookup"><span data-stu-id="98071-144">These experiences may also completely separate time and space, meaning a user could walk the streets of Rome in an immersive experience, while remaining relatively still in their real world space.</span></span> <span data-ttu-id="98071-145">對沉浸式環境應用程式而言，真實世界環境的內容可能不重要。</span><span class="sxs-lookup"><span data-stu-id="98071-145">Context of the real world environment may not be important to an immersive environment app.</span></span>

<span data-ttu-id="98071-146">![沉浸式環境應用程式](images/windows-mixed-reality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="98071-146">![Immersive environment apps](images/windows-mixed-reality-640px.jpg)</span></span><br>
<span data-ttu-id="98071-147">*沉浸式環境應用程式*</span><span class="sxs-lookup"><span data-stu-id="98071-147">*Immersive environment apps*</span></span>

<span data-ttu-id="98071-148">**範例使用**</span><span class="sxs-lookup"><span data-stu-id="98071-148">**Example uses**</span></span>
* <span data-ttu-id="98071-149">一種沉浸式應用程式，可讓使用者導覽完全獨立的空間（亦即，逐步解說著名的建築物、博物館、熱門城市）</span><span class="sxs-lookup"><span data-stu-id="98071-149">An immersive app that lets a user tour a space completely separate from their own (i.e. walk through a famous building, museum, popular city)</span></span>
* <span data-ttu-id="98071-150">以使用者為中心協調事件或案例的沉浸式應用程式（也就是工作或效能）</span><span class="sxs-lookup"><span data-stu-id="98071-150">An immersive app that orchestrates an event or scenario around the user (i.e. a battle or a performance)</span></span>

## <a name="see-also"></a><span data-ttu-id="98071-151">請參閱</span><span class="sxs-lookup"><span data-stu-id="98071-151">See also</span></span>
* [<span data-ttu-id="98071-152">開發概觀</span><span class="sxs-lookup"><span data-stu-id="98071-152">Development overview</span></span>](development.md)
* [<span data-ttu-id="98071-153">應用程式模型</span><span class="sxs-lookup"><span data-stu-id="98071-153">App model</span></span>](app-model.md)
* [<span data-ttu-id="98071-154">應用程式檢視</span><span class="sxs-lookup"><span data-stu-id="98071-154">App views</span></span>](app-views.md)
