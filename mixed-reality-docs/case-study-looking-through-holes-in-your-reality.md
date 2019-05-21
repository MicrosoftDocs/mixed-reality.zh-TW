---
title: 案例研究-仔細檢查您實際上的漏洞
description: 此案例研究將說明如何實作 HoloLens，讓使用者看到背後牆、 樓層、 下，並在其實際環境中的虛擬網站上的 「 magic 視窗 」 效果。
author: EricRehmeyer
ms.author: ericrehm
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，HoloLens magic 的視窗中，視差
ms.openlocfilehash: 945a09614fbc77400825b524f4e0b591bf7b1f6b
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873931"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a><span data-ttu-id="67621-104">案例研究-仔細檢查您實際上的漏洞</span><span class="sxs-lookup"><span data-stu-id="67621-104">Case study - Looking through holes in your reality</span></span>

<span data-ttu-id="67621-105">當人們考慮混合的實境，以及他們可以如何使用 Microsoft HoloLens 時，它們通常是堅持問題像是 「 哪些物件新增至我的房間 」？</span><span class="sxs-lookup"><span data-stu-id="67621-105">When people think about mixed reality and what they can do with Microsoft HoloLens, they usually stick to questions like "What objects can I add to my room?"</span></span> <span data-ttu-id="67621-106">或者 「 什麼可以我在我的空間上嗎？ 」</span><span class="sxs-lookup"><span data-stu-id="67621-106">or “What can I layer on top of my space?"</span></span> <span data-ttu-id="67621-107">我想要反白顯示您可以考慮的另一個區域 — 基本上是一個神奇的技巧，來查詢或透過真實的實體物件都使用相同的技術。</span><span class="sxs-lookup"><span data-stu-id="67621-107">I’d like to highlight another area you can consider—essentially a magic trick—using the same technology to look into or through real physical objects around you.</span></span>

## <a name="the-tech"></a><span data-ttu-id="67621-108">技術</span><span class="sxs-lookup"><span data-stu-id="67621-108">The tech</span></span>

<span data-ttu-id="67621-109">如果您已得力外星人，因為它們可能會中斷在您壁 **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)**，解除鎖定在安全的背景牆 **[片段](case-study-creating-an-immersive-experience-in-fragments.md)**，或已幸運若要查看在 UNSC 無限大機庫 **[E3 2015 Halo 5 體驗](https://www.youtube.com/watch?v=QDw5QjDtFy8)**，則您已了解正是我要討論。</span><span class="sxs-lookup"><span data-stu-id="67621-109">If you've fought aliens as they break through your walls in **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)**, unlocked a wall safe in **[Fragments](case-study-creating-an-immersive-experience-in-fragments.md)**, or were lucky enough to see the UNSC Infinity hangar in the **[Halo 5 experience at E3 in 2015](https://www.youtube.com/watch?v=QDw5QjDtFy8)**, then you've seen what I'm talking about.</span></span> <span data-ttu-id="67621-110">根據您的想像力，此 visual 的技巧可以用在您泥中放入暫存的漏洞，或隱藏在鬆散的 floorboard 的世界。</span><span class="sxs-lookup"><span data-stu-id="67621-110">Depending on your imagination, this visual trick can be used to put temporary holes in your drywall or to hide worlds under a loose floorboard.</span></span>

![RoboRaid 加入三維的管道和後置您的背景牆，只能透過建立為 invaders 突破的漏洞來顯示其他結構。](images/roboraid-640px.png)

<span data-ttu-id="67621-112">RoboRaid 加入三維的管道和後置您的背景牆，只能透過建立為 invaders 突破的漏洞來顯示其他結構。</span><span class="sxs-lookup"><span data-stu-id="67621-112">RoboRaid adds three-dimensional pipes and other structure behind your walls, visible only through holes created as the invaders break through.</span></span>

<span data-ttu-id="67621-113">您可以使用其中一個這些唯一全像投影 HoloLens 上，應用程式可以提供深度的內容，您的背景牆後方，或透過您 floor 方式相同，但實際上會透過實際的視窗。</span><span class="sxs-lookup"><span data-stu-id="67621-113">Using one of these unique holograms on HoloLens, an app can provide the illusion of content behind your walls or through your floor in the same way that reality presents itself through an actual window.</span></span> <span data-ttu-id="67621-114">自行保留，移動，您可以看到任何位於右邊。</span><span class="sxs-lookup"><span data-stu-id="67621-114">Move yourself left, and you can see whatever is on the right side.</span></span> <span data-ttu-id="67621-115">越來越接近，以及您可以看到更多的所有項目。</span><span class="sxs-lookup"><span data-stu-id="67621-115">Get closer, and you can see a bit more of everything.</span></span> <span data-ttu-id="67621-116">主要差異是，實際的漏洞可讓您透過，而您 floor stubbornly 不會讓您透過爬該神奇的全像攝影版內容。</span><span class="sxs-lookup"><span data-stu-id="67621-116">The major difference is that real holes allow you through, while your floor stubbornly won't let you climb through to that magical holographic content.</span></span> <span data-ttu-id="67621-117">（我會將工作加入待處理項目）。</span><span class="sxs-lookup"><span data-stu-id="67621-117">(I'll add a task to the backlog.)</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="67621-118">幕後</span><span class="sxs-lookup"><span data-stu-id="67621-118">Behind the scenes</span></span>

<span data-ttu-id="67621-119">這個訣竅是兩個效果的組合。</span><span class="sxs-lookup"><span data-stu-id="67621-119">This trick is a combination of two effects.</span></span> <span data-ttu-id="67621-120">首先，全像攝影版的內容已釘選到全球使用 「 空間錨點 」。</span><span class="sxs-lookup"><span data-stu-id="67621-120">First, holographic content is pinned to the world using "spatial anchors."</span></span> <span data-ttu-id="67621-121">若要讓該內容 「 世界鎖定 」 使用錨點表示，您要尋找在不以視覺化方式漂移離開實體的物件附近，即使在您移動或基礎的空間的對應系統更新您的聊天室其 3D 模型。</span><span class="sxs-lookup"><span data-stu-id="67621-121">Using anchors to make that content "world-locked" means that what you're looking at doesn't visually drift away from the physical objects near it, even as you move or the underlying spatial mapping system updates its 3D model of your room.</span></span>

<span data-ttu-id="67621-122">其次，該全像攝影版的內容會以視覺化方式限制非常特定的空間，讓您可以只看到透過漏洞，您實際上。</span><span class="sxs-lookup"><span data-stu-id="67621-122">Secondly, that holographic content is visually limited to a very specific space, so you can only see through the hole in your reality.</span></span> <span data-ttu-id="67621-123">該阻擋是為了需要仔細檢查邏輯漏洞、 視窗或門口，銷售的技巧。</span><span class="sxs-lookup"><span data-stu-id="67621-123">That occlusion is necessary to require looking through a logical hole, window, or doorway, which sells the trick.</span></span> <span data-ttu-id="67621-124">沒有什麼東西可以封鎖大部分的檢視，裂縫祕密的侏維度空間中，可能只是看起來像不當放置的恐龍。</span><span class="sxs-lookup"><span data-stu-id="67621-124">Without something blocking most of the view, a crack in space to a secret Jurassic dimension might just look like a poorly placed dinosaur.</span></span>

![這不是實際的螢幕擷取畫面，但舉例說明如何在 HoloLens 從 MR 基本概念 101 祕密地底世界的樣子。](images/origamiholecomposited-640px.png)

<span data-ttu-id="67621-128">這不是實際的螢幕擷取畫面，而圖如何從祕密地底世界[MR 基本概念 101](holograms-101.md) HoloLens 上看起來。</span><span class="sxs-lookup"><span data-stu-id="67621-128">This is not an actual screenshot, but an illustration of how the secret underworld from the [MR Basics 101](holograms-101.md) looks on HoloLens.</span></span> <span data-ttu-id="67621-129">黑色的機箱未顯示，但您可以看到透過虛擬的洞裡的內容。</span><span class="sxs-lookup"><span data-stu-id="67621-129">The black enclosure doesn’t show up, but you can see content through a virtual hole.</span></span> <span data-ttu-id="67621-130">（透過實際的裝置時，最低限度值似乎因為眼睛的重點放在進一步的距離，如果找不到甚至更會消失。）</span><span class="sxs-lookup"><span data-stu-id="67621-130">(When looking through an actual device, the floor would seem to disappear even more because your eyes focus at a further distance as if it’s not even there.)</span></span>

### <a name="world-locking-holographic-content"></a><span data-ttu-id="67621-131">世界鎖定全像攝影版的內容</span><span class="sxs-lookup"><span data-stu-id="67621-131">World-locking holographic content</span></span>

<span data-ttu-id="67621-132">在 Unity 中，造成保持世界鎖定全像攝影版的內容是簡單，只要新增 WorldAnchor 元件：</span><span class="sxs-lookup"><span data-stu-id="67621-132">In Unity, causing holographic content to stay world-locked is as easy as adding a WorldAnchor component:</span></span>

```
myObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="67621-133">WorldAnchor 元件將會調整的位置和輪替其 GameObject （和任何其他在該階層中的物件項目） 保持穩定，相對於實體物件附近。</span><span class="sxs-lookup"><span data-stu-id="67621-133">The WorldAnchor component will constantly adjust the position and rotation of its GameObject (and thus anything else under that object in the hierarchy) to keep it stable relative to nearby physical objects.</span></span> <span data-ttu-id="67621-134">當製作您的內容，則會建立物件的 [根] 樞紐，在這個虛擬漏洞置中對齊的方式。</span><span class="sxs-lookup"><span data-stu-id="67621-134">When authoring your content, create it in such a way that the root pivot of your object is centered at this virtual hole.</span></span> <span data-ttu-id="67621-135">（牆上的深度，物件的樞紐分析時，其位置和旋轉的稍微調整會更明顯，而且漏洞不可能看起來非常穩定）。</span><span class="sxs-lookup"><span data-stu-id="67621-135">(If your object's pivot is deep in the wall, its slight tweaks in position and rotation will be much more noticeable, and the hole may not look very stable.)</span></span>

### <a name="occluding-everything-but-the-virtual-hole"></a><span data-ttu-id="67621-136">Occluding 以外的虛擬的漏洞</span><span class="sxs-lookup"><span data-stu-id="67621-136">Occluding everything but the virtual hole</span></span>

<span data-ttu-id="67621-137">有各種不同的方式，選擇性地封鎖項目是隱藏在您的背景牆檢視。</span><span class="sxs-lookup"><span data-stu-id="67621-137">There are a variety of ways to selectively block the view to what is hidden in your walls.</span></span> <span data-ttu-id="67621-138">最簡單的一個利用 HoloLens 使用加法類的顯示，這表示全黑的物件會顯示不可見的事實。</span><span class="sxs-lookup"><span data-stu-id="67621-138">The simplest one takes advantage of the fact that HoloLens uses an additive display, which means that fully black objects appear invisible.</span></span> <span data-ttu-id="67621-139">您可以在 Unity 中而不進行任何特殊的著色器或材質的訣竅，只要建立黑色的資料，並將它指派給您的內容中的物件。</span><span class="sxs-lookup"><span data-stu-id="67621-139">You can do this in Unity without doing any special shader or material tricks— just create a black material and assign it to an object that boxes in your content.</span></span> <span data-ttu-id="67621-140">如果您不想要執行 3D 模型，只要使用少數幾個四組數字的預設物件，並稍微重疊它們。</span><span class="sxs-lookup"><span data-stu-id="67621-140">If you don't feel like doing 3D modeling, just use a handful of default Quad objects and overlap them slightly.</span></span> <span data-ttu-id="67621-141">有一些缺點，這種作法是最快的方法來取得完全運作，但取得低精確度的使用概念證明很棒，，即使您懷疑您可能想要稍後再加以重構。</span><span class="sxs-lookup"><span data-stu-id="67621-141">There are a number of drawbacks to this approach, but it is the fastest way to get something working, and getting a low-fidelity proof of concept working is great, even if you suspect you might want to refactor it later.</span></span>

<span data-ttu-id="67621-142">上述的 「 黑箱 」 方法的一大缺點是不好拍攝。</span><span class="sxs-lookup"><span data-stu-id="67621-142">One major drawback to the above "black box" approach is that it doesn't photograph well.</span></span> <span data-ttu-id="67621-143">效果看起來的 HoloLens 顯示透過完美的您採取任何螢幕擷取畫面會顯示黑色的大型物件，而非剩下的塗鴉牆或樓層。</span><span class="sxs-lookup"><span data-stu-id="67621-143">While your effect might look perfect through the display of HoloLens, any screenshots you take will show a large black object instead of what remains of your wall or floor.</span></span> <span data-ttu-id="67621-144">原因是，但實際上與實體硬體和螢幕擷取畫面複合全像投影以不同的方式。</span><span class="sxs-lookup"><span data-stu-id="67621-144">The reason for this is that the physical hardware and screenshots composite holograms and reality differently.</span></span> <span data-ttu-id="67621-145">讓我們到一些假的數學繞道一下...</span><span class="sxs-lookup"><span data-stu-id="67621-145">Let's detour for a moment into some fake math...</span></span>

<span data-ttu-id="67621-146">*假的數學警示 ！這些數字和公式是為了說明的點，不為任何類型的精確的公制 ！*</span><span class="sxs-lookup"><span data-stu-id="67621-146">*Fake math alert! These numbers and formulas are meant to illustrate a point, not to be any sort of accurate metric!*</span></span>

<span data-ttu-id="67621-147">您看到透過 HoloLens:</span><span class="sxs-lookup"><span data-stu-id="67621-147">What you see through HoloLens:</span></span>

```
( Reality * darkening_amount ) + Holograms
```

<span data-ttu-id="67621-148">您看到螢幕擷取畫面和影片中：</span><span class="sxs-lookup"><span data-stu-id="67621-148">What you see in screenshots and video:</span></span>

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

<span data-ttu-id="67621-149">以英文：您透過 HoloLens 所看到的內容是簡單的組合變暗的事實 （如同透過太陽眼鏡） 和任何應用程式想要顯示全像投影。</span><span class="sxs-lookup"><span data-stu-id="67621-149">In English: What you see through HoloLens is a simple combination of darkened reality (like through sunglasses) and whatever holograms the app wants to show.</span></span> <span data-ttu-id="67621-150">但當您的螢幕擷取畫面，相機的映像會與應用程式的全像投影的每一像素透明度值根據混合。</span><span class="sxs-lookup"><span data-stu-id="67621-150">But when you take a screenshot, the camera's image is blended with the app's holograms according to the per-pixel transparency value.</span></span>

<span data-ttu-id="67621-151">若要解決這個問題的一個方式是變更，只寫入深度緩衝區，並與所有其他不透明資料排序的 「 黑箱作業 」 資料。</span><span class="sxs-lookup"><span data-stu-id="67621-151">One way to get around this is to change the "black box" material to only write to the depth buffer, and sort with all the other opaque materials.</span></span> <span data-ttu-id="67621-152">如這個範例，請參閱[MixedRealityToolkit 在 GitHub 上的 WindowOcclusion.shader 檔案](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader)。</span><span class="sxs-lookup"><span data-stu-id="67621-152">For an example of this, check out the [WindowOcclusion.shader file in the MixedRealityToolkit on GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader).</span></span> <span data-ttu-id="67621-153">這裡複製相關的行：</span><span class="sxs-lookup"><span data-stu-id="67621-153">The relevant lines are copied here:</span></span>

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

<span data-ttu-id="67621-154">(請注意 「 位移 50，100"一行是應付不相關的問題，因此它可能有道理，省略。)</span><span class="sxs-lookup"><span data-stu-id="67621-154">(Note the "Offset 50, 100" line is to deal with unrelated issues, so it'd probably make sense to leave that out.)</span></span>

<span data-ttu-id="67621-155">實作不可見的阻擋物材料，可讓您繪製的方塊，看起來是正確和混合實境螢幕擷取畫面中顯示的應用程式。</span><span class="sxs-lookup"><span data-stu-id="67621-155">Implementing an invisible occlusion material like that will let your app draw a box that looks correct in the display and in mixed-reality screenshots.</span></span> <span data-ttu-id="67621-156">變本加厲，您可以試著改善效能的進一步延伸該方塊 clever 凡事繪製更少看不見的像素，但可以講一下檢討，通常不是必要。</span><span class="sxs-lookup"><span data-stu-id="67621-156">For bonus points, you can try to improve the performance of that box even further by doing clever things to draw even fewer invisible pixels, but that can really get into the weeds and usually won't be necessary.</span></span>

![以下是從 MR 基本概念 101 祕密地底世界，因為 Unity 繪製它，除了 occluding 方塊的外部組件。](images/underworld-occluded-640px.png)

<span data-ttu-id="67621-159">以下是從祕密地底世界[MR 基本概念 101](holograms-101.md)如 Unity 繪製它，除了 occluding 方塊的外部組件。</span><span class="sxs-lookup"><span data-stu-id="67621-159">Here is the secret underworld from [MR Basics 101](holograms-101.md) as Unity draws it, except for the outer parts of the occluding box.</span></span> <span data-ttu-id="67621-160">請注意，底世界的樞紐中央的方塊中，可協助保留漏洞相對於實際的 floor，盡可能穩定。</span><span class="sxs-lookup"><span data-stu-id="67621-160">Note that the pivot for the underworld is at the center of the box, which helps keep the hole as stable as possible relative to your actual floor.</span></span>

## <a name="do-it-yourself"></a><span data-ttu-id="67621-161">自行進行此作業</span><span class="sxs-lookup"><span data-stu-id="67621-161">Do it yourself</span></span>

<span data-ttu-id="67621-162">有 HoloLens 和想要自行試用效果？</span><span class="sxs-lookup"><span data-stu-id="67621-162">Have a HoloLens and want to try out the effect for yourself?</span></span> <span data-ttu-id="67621-163">您可以執行 （不需要撰寫程式碼） 的最簡單件事是要安裝免費的 3D 檢視器應用程式，然後載入[我提供了在 GitHub 的下載 the.fbx 檔案](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow)檢視花卉 pot 模型，在您的房間。</span><span class="sxs-lookup"><span data-stu-id="67621-163">The easiest thing you can do (no coding required) is to install the free 3D Viewer app and then load the [download the.fbx file I've provided on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) to view a flower pot model in your room.</span></span> <span data-ttu-id="67621-164">HoloLens，將其載入，您可以看到工作的假象。</span><span class="sxs-lookup"><span data-stu-id="67621-164">Load it on HoloLens, and you can see the illusion at work.</span></span> <span data-ttu-id="67621-165">當您準備模型之前時，您只能看到到小的漏洞，其他所有項目不會察覺。</span><span class="sxs-lookup"><span data-stu-id="67621-165">When you're in front of the model, you can only see into the small hole—everything else is invisible.</span></span> <span data-ttu-id="67621-166">查看模型，從任何另一端，它完全消失。</span><span class="sxs-lookup"><span data-stu-id="67621-166">Look at the model from any other side and it disappears entirely.</span></span> <span data-ttu-id="67621-167">使用移動、 旋轉和調整控制項的 3D 檢視器來放置虛擬洞，針對任何垂直的介面，您可以將產生一些想法 ！</span><span class="sxs-lookup"><span data-stu-id="67621-167">Use the movement, rotation, and scale controls of 3D Viewer to position the virtual hole against any vertical surface you can think of to generate some ideas!</span></span>

![在 Unity 編輯器中檢視此模型會顯示圍繞 flowerpot 大型黑色方塊。](images/magicwindowflowerpotineditor.png)

<span data-ttu-id="67621-170">在 Unity 編輯器中檢視此模型會顯示圍繞 flowerpot 大型黑色方塊。</span><span class="sxs-lookup"><span data-stu-id="67621-170">Viewing this model in your Unity editor will show a large black box around the flowerpot.</span></span> <span data-ttu-id="67621-171">HoloLens，在方塊就會消失，讓 magic 視窗效果的方法。</span><span class="sxs-lookup"><span data-stu-id="67621-171">On HoloLens, the box disappears, giving way to a magic window effect.</span></span>

<span data-ttu-id="67621-172">如果您想要建置使用這項技術的應用程式，請參閱[MR 基本概念 101 教學課程](holograms-101.md)中[混合實境教學課程](tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="67621-172">If you want to build an app that uses this technique, check out the [MR Basics 101 tutorial](holograms-101.md) in the [Mixed Reality tutorials](tutorials.md).</span></span> <span data-ttu-id="67621-173">第 7 章結尾中會顯示隱藏的底世界 （如上面圖所示） 您 floor 遽增。</span><span class="sxs-lookup"><span data-stu-id="67621-173">Chapter 7 ends with an explosion in your floor that reveals a hidden underworld (as pictured above).</span></span> <span data-ttu-id="67621-174">誰說教學課程必須無聊？</span><span class="sxs-lookup"><span data-stu-id="67621-174">Who said tutorials had to be boring?</span></span>

<span data-ttu-id="67621-175">以下是一些概念的您可以採取這個想法下一步:</span><span class="sxs-lookup"><span data-stu-id="67621-175">Here are some ideas of where you can take this idea next:</span></span>
* <span data-ttu-id="67621-176">將可讓內容內的虛擬的洞裡互動式方法。</span><span class="sxs-lookup"><span data-stu-id="67621-176">Think of ways to make the content inside the virtual hole interactive.</span></span> <span data-ttu-id="67621-177">讓使用者有一些影響超過其牆真的能夠改進難怪這個技巧可提供的意義。</span><span class="sxs-lookup"><span data-stu-id="67621-177">Letting your users have some impact beyond their walls can really improve the sense of wonder that this trick can provide.</span></span>
* <span data-ttu-id="67621-178">將方法可以查看透過回到已知的區域物件。</span><span class="sxs-lookup"><span data-stu-id="67621-178">Think of ways to see through objects back to known areas.</span></span> <span data-ttu-id="67621-179">比方說，可以將全像攝影版的洞裡放在您的咖啡資料表及檢視的方式下的您 floor 嗎？</span><span class="sxs-lookup"><span data-stu-id="67621-179">For example, how can you put a holographic hole in your coffee table and see your floor beneath it?</span></span>

## <a name="about-the-author"></a><span data-ttu-id="67621-180">關於作者</span><span class="sxs-lookup"><span data-stu-id="67621-180">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><span data-ttu-id="67621-181"><b>Eric Rehmeyer</b></span><span class="sxs-lookup"><span data-stu-id="67621-181"><b>Eric Rehmeyer</b></span></span><br><span data-ttu-id="67621-182">資深軟體工程師 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="67621-182">Senior Software Engineer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="67621-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67621-183">See also</span></span>
* [<span data-ttu-id="67621-184">MR Basics 101：使用裝置完成專案</span><span class="sxs-lookup"><span data-stu-id="67621-184">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="67621-185">座標系統</span><span class="sxs-lookup"><span data-stu-id="67621-185">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="67621-186">空間錨點</span><span class="sxs-lookup"><span data-stu-id="67621-186">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="67621-187">空間對應</span><span class="sxs-lookup"><span data-stu-id="67621-187">Spatial mapping</span></span>](spatial-mapping.md)
