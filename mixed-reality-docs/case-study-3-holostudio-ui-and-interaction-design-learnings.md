---
title: 案例研究-3 HoloStudio UI 和互動設計所獲得的經驗
description: HoloStudio UI 和互動的設計做法
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: 混合實境的 HoloLens，HoloStudio，Windows
ms.openlocfilehash: e01e2ea888398e9982b56fd95f90ef0731ec6bc2
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974822"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a><span data-ttu-id="e3f1d-104">案例研究-3 HoloStudio UI 和互動設計所獲得的經驗</span><span class="sxs-lookup"><span data-stu-id="e3f1d-104">Case study - 3 HoloStudio UI and interaction design learnings</span></span>

<span data-ttu-id="e3f1d-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) HoloLens 是其中一個第一的 Microsoft 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) was one of the first Microsoft apps for HoloLens.</span></span> <span data-ttu-id="e3f1d-106">因為這個緣故，我們必須建立新的 3D UI 的最佳作法和互動的設計。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-106">Because of this, we had to create new best practices for 3D UI and interaction design.</span></span> <span data-ttu-id="e3f1d-107">我們透過大量使用者測試、 建立原型和試驗和錯誤。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-107">We did this through a lot of user testing, prototyping, and trial and error.</span></span>

<span data-ttu-id="e3f1d-108">我們知道，並非所有人擁有的資源任由他們支配，若要執行這種類型的參考資料，因此我們不得不我們資深全像攝影版設計工具中，Marcus Ghaly 共用三件事我們了解有關 HoloLens 的應用程式的 UI 和互動設計 HoloStudio 開發期間。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-108">We know that not everyone has the resources at their disposal to do this type of research, so we had our Sr. Holographic Designer, Marcus Ghaly, share three things we learned during the development of HoloStudio about UI and interaction design for HoloLens apps.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="e3f1d-109">觀看影片</span><span class="sxs-lookup"><span data-stu-id="e3f1d-109">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a><span data-ttu-id="e3f1d-110">問題 #1:使用者不想要其建立四處移動</span><span class="sxs-lookup"><span data-stu-id="e3f1d-110">Problem #1: People didn't want to move around their creations</span></span>

<span data-ttu-id="e3f1d-111">我們原本被設計在 HoloStudio workbench 為矩形，更像您會發現真實世界中。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-111">We originally designed the workbench in HoloStudio as a rectangle, much like you'd find in the real world.</span></span> <span data-ttu-id="e3f1d-112">問題在於，人的體驗，告知他們要坐在桌或讓它們未移動 workbench，在電腦前工作，並探索從所有側邊的 3D 建立時，仍保持存留期。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-112">The problem is that people have a lifetime of experience that tells them to stay still when they're sitting at a desk or working in front of a computer, so they weren't moving around the workbench and exploring their 3D creation from all sides.</span></span>

![矩形 HoloStudio 在 workbench 的設計 dissuaded 四處移動，並看到其從所有側邊建立的使用者。](images/rectangular-workbench-500px.jpg)

<span data-ttu-id="e3f1d-114">我們必須讓 workbench 捨入，因此，沒有任何 「 面對 」，或清除您原本就能進行的深入解析。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-114">We had the insight to make the workbench round, so that there was no "front" or clear place that you were supposed to stand.</span></span> <span data-ttu-id="e3f1d-115">當我們測試時，突然人啟動四處移動，並自行探索其建立。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-115">When we tested this, suddenly people started moving around and exploring their creations on their own.</span></span>

![循環的 workbench 設計建議從頭到尾參與繞其建立的使用者。](images/circular-workbench-500px.jpg)

<span data-ttu-id="e3f1d-117">**我們了解**</span><span class="sxs-lookup"><span data-stu-id="e3f1d-117">**What we learned**</span></span>

<span data-ttu-id="e3f1d-118">請務必考慮什麼是使用者習慣。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-118">Always be thinking about what's comfortable for the user.</span></span> <span data-ttu-id="e3f1d-119">利用他們的實體空間是很棒的功能，HoloLens 和您無法與其他裝置。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-119">Taking advantage of their physical space is a cool feature of HoloLens and something you can't do with other devices.</span></span>

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a><span data-ttu-id="e3f1d-120">問題 #2:強制回應對話方塊有時候是從全像攝影版的框架</span><span class="sxs-lookup"><span data-stu-id="e3f1d-120">Problem #2: Modal dialogs are sometimes out of the holographic frame</span></span>

<span data-ttu-id="e3f1d-121">有時候，您的使用者可能會尋找不同方向從項目需要注意應用程式中。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-121">Sometimes, your user may be looking in a different direction from something that needs their attention in your app.</span></span> <span data-ttu-id="e3f1d-122">在 PC 上，您可以只快顯啟動一個對話方塊，，但如果您這樣做，在某個人的臉部在 3D 的環境中，它可以覺得對話方塊取得它們的方式。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-122">On a PC, you can just pop up a dialog, but if you do this in someone's face in a 3D environment, it can feel like the dialog is getting in their way.</span></span> <span data-ttu-id="e3f1d-123">您需要它們來讀取訊息，但其直覺是將嘗試取得開。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-123">You need them to read the message, but their instinct is to try to get away from it.</span></span> <span data-ttu-id="e3f1d-124">這個反應很棒，如果您在玩遊戲時，但在工具中，針對工作所設計，是不盡理想。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-124">This reaction is great if you're playing a game, but in a tool designed for work, it's less than ideal.</span></span>

<span data-ttu-id="e3f1d-125">在嘗試幾個不同的項目之後, 我們最後決定使用 「 相信有一天泡泡 」 系統對於我們的對話，並加入 tendrils 使用者可遵循在我們的應用程式中需要注意的地方。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-125">After trying a few different things, we finally settled on using a "thought bubble" system for our dialogs and added tendrils that users can follow to where their attention is needed in our application.</span></span> <span data-ttu-id="e3f1d-126">我們也強化了 tendrils 脈衝，其中隱含的方向，讓使用者知道的位置。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-126">We also made the tendrils pulse, which implied a sense of directionality so that users knew where to go.</span></span>

![「 認為泡泡 」 系統包含閃爍 tendrils 提供方向，導致使用者已在應用程式所需注意感。](images/thought-bubble-500px.jpg)

<span data-ttu-id="e3f1d-128">**我們了解**</span><span class="sxs-lookup"><span data-stu-id="e3f1d-128">**What we learned**</span></span>

<span data-ttu-id="e3f1d-129">它是很難在 3D，警告使用者他們需要注意的事項。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-129">It's much harder in 3D to alert users to things they need to pay attention to.</span></span> <span data-ttu-id="e3f1d-130">這類使用注意董事會[空間音效](spatial-sound.md)、 亮色調光線，或思考反昇，可能會導致使用者能所需的位置。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-130">Using attention directors such as [spatial sound](spatial-sound.md), light rays, or thought bubbles, can lead users to where they need to be.</span></span>

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a><span data-ttu-id="e3f1d-131">問題 3:有時候 UI 都可以使用其他全像投影遭到封鎖</span><span class="sxs-lookup"><span data-stu-id="e3f1d-131">Problem #3: Sometimes UI can get blocked by other holograms</span></span>

<span data-ttu-id="e3f1d-132">有些的時候，當使用者想要互動的全像和其相關聯的 UI 控制項，但會從檢視中封鎖，因為另一個全像前面。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-132">There are times when a user wants to interact with a hologram and its associated UI controls, but they are blocked from view because another hologram is in front of them.</span></span> <span data-ttu-id="e3f1d-133">雖然我們開發 HoloStudio，我們會用來參加這個方案的試驗和錯誤。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-133">While we were developing HoloStudio, we used trial and error to come to a solution for this.</span></span>

![如果它與穿著 HoloLens 的使用者之間的另一個全像雷射相關聯的 UI 控制項可能會被封鎖。](images/ui-blocked-500px.jpg)

<span data-ttu-id="e3f1d-135">我們試著將 UI 控制項更接近移至使用者，讓它無法取得受到封鎖，但發現那其實不知道如何讓使用者查看時同時查看很遠的地方是全像已接近您的控制項。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-135">We tried moving the UI control closer to the user so it couldn't get blocked, but found that it wasn't comfortable for the user to look at a control that was near to you while simultaneously looking at a hologram that was far away.</span></span> <span data-ttu-id="e3f1d-136">如果，不過，我們已接近全像前面控制項移至使用者，他們覺得自己已卸離應該會影響全像圖。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-136">If, however, we moved the control in front of the closest hologram to the user, they felt like it was detached from the hologram it should be affecting.</span></span>

<span data-ttu-id="e3f1d-137">最後，我們會最後會建立映像的 UI 控制項，並將其放置在相同的距離使用者為其相關聯，全像圖讓它們都覺得連線。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-137">We finally ended up ghosting the UI control, and put it at the same distance from the user as the hologram it's associated with, so they both feel connected.</span></span> <span data-ttu-id="e3f1d-138">這可讓使用者與控制項互動，即使它已遮蔽。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-138">This allows the user to interact with the control even though it's been obscured.</span></span>

![解決方案： 我們建立 UI 控制項，同時允許與控制項互動，並使它可以連線到它已影響全像映像。](images/ghosting-ui-500px.jpg)

<span data-ttu-id="e3f1d-140">**我們了解**</span><span class="sxs-lookup"><span data-stu-id="e3f1d-140">**What we learned**</span></span>

<span data-ttu-id="e3f1d-141">使用者必須要能夠輕鬆地存取 UI 控制項，即使它們已被封鎖，因此請找出方法，以確保使用者可以完成其身處何處其全像投影真實世界中的工作。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-141">Users need to be able to easily access UI controls even if they've been blocked, so figure out methods to ensure that users can complete their tasks no matter where their holograms are in the real world.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="e3f1d-142">關於作者</span><span class="sxs-lookup"><span data-stu-id="e3f1d-142">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="e3f1d-143"><b>Marcus Ghaly</b></span><span class="sxs-lookup"><span data-stu-id="e3f1d-143"><b>Marcus Ghaly</b></span></span><br><span data-ttu-id="e3f1d-144">Sr.全像攝影版的設計工具 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="e3f1d-144">Sr. Holographic Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="e3f1d-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3f1d-145">See also</span></span>
* [<span data-ttu-id="e3f1d-146">本能互動</span><span class="sxs-lookup"><span data-stu-id="e3f1d-146">Instinctual interactions</span></span>](interaction-fundamentals.md)

 
