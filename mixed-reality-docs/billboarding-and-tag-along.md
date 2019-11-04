---
title: Billboarding 和標記-沿著
description: 具有 billboarding 的物件一律會向自己引導，以面對使用者。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，billboarding，加上標記
ms.openlocfilehash: 032e665d94a73b94b59f693e452874af0b45f021
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436995"
---
# <a name="billboarding-and-tag-along"></a><span data-ttu-id="53a8d-104">Billboarding 和標記-沿著</span><span class="sxs-lookup"><span data-stu-id="53a8d-104">Billboarding and tag-along</span></span>

<br>

<img src="images/billboarding-fragments.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">

<span data-ttu-id="53a8d-105">Billboarding 是一種行為概念，可套用至混合現實中的物件。</span><span class="sxs-lookup"><span data-stu-id="53a8d-105">Billboarding is a behavioral concept that can be applied to objects in mixed reality.</span></span> <span data-ttu-id="53a8d-106">具有 billboarding 的物件一律會向自己引導，以面對使用者。</span><span class="sxs-lookup"><span data-stu-id="53a8d-106">Objects with billboarding always orient themselves to face the user.</span></span> <span data-ttu-id="53a8d-107">這對於文字和功能表系統特別有説明，其中放置在使用者環境中的靜態物件（世界鎖定的）會在使用者四處移動時隱藏或無法讀取。</span><span class="sxs-lookup"><span data-stu-id="53a8d-107">This is especially helpful with text and menuing systems where static objects placed in the user's environment (world-locked) would be otherwise obscured or unreadable if a user were to move around.</span></span>

<span data-ttu-id="53a8d-108">啟用 billboarding 的物件可以在使用者的環境中自由地旋轉。</span><span class="sxs-lookup"><span data-stu-id="53a8d-108">Objects with billboarding enabled can rotate freely in the user's environment.</span></span> <span data-ttu-id="53a8d-109">視設計考慮而定，它們也可以限制為單一軸。</span><span class="sxs-lookup"><span data-stu-id="53a8d-109">They can also be constrained to a single axis depending on design considerations.</span></span> <span data-ttu-id="53a8d-110">請記住，如果 billboarded 物件的位置太接近其他物件，或在 HoloLens 中太接近掃描的表面，則可能會裁剪或遮蔽本身。</span><span class="sxs-lookup"><span data-stu-id="53a8d-110">Keep in mind, billboarded objects may clip or occlude themselves if they are placed too close to other objects, or in HoloLens, too close scanned surfaces.</span></span> <span data-ttu-id="53a8d-111">若要避免這種情況，請考慮物件在已啟用 billboarding 的軸上旋轉時，可能會產生的總使用量。</span><span class="sxs-lookup"><span data-stu-id="53a8d-111">To avoid this, think about the total footprint an object may produce when rotated on the axis enabled for billboarding.</span></span>

## <a name="what-is-a-tag-along"></a><span data-ttu-id="53a8d-112">什麼是標記？</span><span class="sxs-lookup"><span data-stu-id="53a8d-112">What is a tag-along?</span></span>

<span data-ttu-id="53a8d-113">標記-沿著可新增至全息影像的行為概念，包括 billboarded 物件。</span><span class="sxs-lookup"><span data-stu-id="53a8d-113">Tag-along is a behavioral concept that can be added to holograms, including billboarded objects.</span></span> <span data-ttu-id="53a8d-114">此互動是達到 head 鎖定內容效果的更自然易懂方式。</span><span class="sxs-lookup"><span data-stu-id="53a8d-114">This interaction is a more natural and friendly way of achieving the effect of head-locked content.</span></span> <span data-ttu-id="53a8d-115">標記物件會嘗試永不離開使用者的視圖。</span><span class="sxs-lookup"><span data-stu-id="53a8d-115">A tag-along object attempts to never leave the user's view.</span></span> <span data-ttu-id="53a8d-116">如此一來，使用者就能自由地與之前的內容進行互動，同時還會看到其直接觀賞外的全息影像。</span><span class="sxs-lookup"><span data-stu-id="53a8d-116">This allows the user to freely interact with what is front of them while also still seeing the holograms outside their direct view.</span></span>

<span data-ttu-id="53a8d-117">![HoloLens pin 面板是如何進行標記的絕佳範例](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="53a8d-117">![The HoloLens pins panel is a great example of how tag-along behaves](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="53a8d-118">*HoloLens 的 [開始] 功能表是標記和行為的絕佳範例*</span><span class="sxs-lookup"><span data-stu-id="53a8d-118">*The HoloLens Start menu is a great example of tag-along behavior*</span></span>

<span data-ttu-id="53a8d-119">加上標籤的物件具有可以微調其行為方式的參數。</span><span class="sxs-lookup"><span data-stu-id="53a8d-119">Tag-along objects have parameters which can fine-tune the way they behave.</span></span> <span data-ttu-id="53a8d-120">當使用者在其環境中移動時，可以視需要在使用者的視線中進入或登出內容。</span><span class="sxs-lookup"><span data-stu-id="53a8d-120">Content can be in or out of the user’s line of sight as desired while the user moves around their environment.</span></span> <span data-ttu-id="53a8d-121">當使用者移動時，內容會透過滑動到視野的邊緣來嘗試停留在使用者的其邊界中，視使用者移動的速度而定，可能會讓內容暫時消失。</span><span class="sxs-lookup"><span data-stu-id="53a8d-121">As the user moves, the content will attempt to stay within the user’s periphery by sliding towards the edge of the view, depending on how quickly a user moves may leave the content temporarily out of view.</span></span> <span data-ttu-id="53a8d-122">當使用者 gazes 到標記物件時，它會有更完整的視野。</span><span class="sxs-lookup"><span data-stu-id="53a8d-122">When the user gazes towards the tag-along object, it comes more fully into view.</span></span> <span data-ttu-id="53a8d-123">將內容視為「一目了然」，讓使用者不會忘記內容的方向。</span><span class="sxs-lookup"><span data-stu-id="53a8d-123">Think of content always being "a glance away" so users never forget what direction their content is in.</span></span>

<span data-ttu-id="53a8d-124">其他參數可以讓以標籤為依據的物件，由橡皮區連接到使用者的前端。</span><span class="sxs-lookup"><span data-stu-id="53a8d-124">Additional parameters can make the tag-along object feel attached to the user's head by a rubber band.</span></span> <span data-ttu-id="53a8d-125">抑制加速或減速會為物件提供權數，使其更實際呈現。</span><span class="sxs-lookup"><span data-stu-id="53a8d-125">Dampening acceleration or deceleration gives weight to the object making it feel more physically present.</span></span> <span data-ttu-id="53a8d-126">這個春季行為是一個 affordance，可協助使用者建立標記運作方式的精確心理模型。</span><span class="sxs-lookup"><span data-stu-id="53a8d-126">This spring behavior is an affordance that helps the user build an accurate mental model of how tag-along works.</span></span> <span data-ttu-id="53a8d-127">當使用者在標記模式下具有物件時，音訊有助於提供額外的 affordances。</span><span class="sxs-lookup"><span data-stu-id="53a8d-127">Audio helps provide additional affordances for when users have objects in tag-along mode.</span></span> <span data-ttu-id="53a8d-128">音訊應該會強化移動的速度;快速的前端應該提供更明顯的音效效果，而如果有任何影響，自然速度應該會有最小的音訊。</span><span class="sxs-lookup"><span data-stu-id="53a8d-128">Audio should reinforce the speed of movement; a fast head turn should provide a more noticeable sound effect while walking at a natural speed should have minimal audio if any effects at all.</span></span>

<span data-ttu-id="53a8d-129">就像真正的前端鎖定內容一樣，如果在使用者的觀點裡經常移動或說得太多，標籤物件就可以證明很大或 nauseating。</span><span class="sxs-lookup"><span data-stu-id="53a8d-129">Just like truly head-locked content, tag-along objects can prove overwhelming or nauseating if they move wildly or spring too much in the user’s view.</span></span> <span data-ttu-id="53a8d-130">當使用者查看並快速停止時，他們的分辨會告訴他們已停止。</span><span class="sxs-lookup"><span data-stu-id="53a8d-130">As a user looks around and then quickly stop, their senses tell them they have stopped.</span></span> <span data-ttu-id="53a8d-131">其餘額會通知他們其前端已停止轉動，而其願景也會導致世界停止轉動。</span><span class="sxs-lookup"><span data-stu-id="53a8d-131">Their balance informs them that their head has stopped turning as well as their vision sees the world stop turning.</span></span> <span data-ttu-id="53a8d-132">不過，如果在使用者停止時，標記會繼續移動，可能會混淆其感知。</span><span class="sxs-lookup"><span data-stu-id="53a8d-132">However, if tag-along keeps on moving when the user has stopped, it may confuse their senses.</span></span>

## <a name="see-also"></a><span data-ttu-id="53a8d-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="53a8d-133">See also</span></span>
* [<span data-ttu-id="53a8d-134">游標</span><span class="sxs-lookup"><span data-stu-id="53a8d-134">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="53a8d-135">本能互動</span><span class="sxs-lookup"><span data-stu-id="53a8d-135">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="53a8d-136">舒適度</span><span class="sxs-lookup"><span data-stu-id="53a8d-136">Comfort</span></span>](comfort.md)
