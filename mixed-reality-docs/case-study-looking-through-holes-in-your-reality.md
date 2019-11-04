---
title: 個案研究-查看您現實中的漏洞
description: 此案例研究會說明如何在 HoloLens 上執行「魔術 window」的效果，讓使用者可以在背景牆後方、樓層下，以及在其實際環境內的虛擬空缺中查看。
author: EricRehmeyer
ms.author: bestruku
ms.date: 10/18/2019
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、魔術 window、視差
ms.openlocfilehash: a1b9f0b2e576379846a867f3d3bffef7d8ec277e
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436663"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a><span data-ttu-id="8e638-104">個案研究-查看您現實中的漏洞</span><span class="sxs-lookup"><span data-stu-id="8e638-104">Case study - Looking through holes in your reality</span></span>

<span data-ttu-id="8e638-105">當人們思考混合現實以及他們可以如何處理 Microsoft HoloLens 時，他們通常會問到「我可以將哪些物件新增到我的房間？」之類的問題。</span><span class="sxs-lookup"><span data-stu-id="8e638-105">When people think about mixed reality and what they can do with Microsoft HoloLens, they usually stick to questions like "What objects can I add to my room?"</span></span> <span data-ttu-id="8e638-106">或是「我可以在我的空間上分層？」</span><span class="sxs-lookup"><span data-stu-id="8e638-106">or “What can I layer on top of my space?"</span></span> <span data-ttu-id="8e638-107">我想要強調另一個您可以考慮的地方—基本上是一種神奇的技巧，也就是使用相同的技術來查詢您的實際實體物件。</span><span class="sxs-lookup"><span data-stu-id="8e638-107">I’d like to highlight another area you can consider—essentially a magic trick—using the same technology to look into or through real physical objects around you.</span></span>

## <a name="the-tech"></a><span data-ttu-id="8e638-108">技術</span><span class="sxs-lookup"><span data-stu-id="8e638-108">The tech</span></span>

<span data-ttu-id="8e638-109">如果您已無法駕馭外星人，因為它們在 **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)** 中分解了您的牆、在 **[片段](case-study-creating-an-immersive-experience-in-fragments.md)** 中解除鎖定牆上的安全，或幸運的是要在 **[2015](https://www.youtube.com/watch?v=QDw5QjDtFy8)** 中的 hangar 上查看 UNSC 無限大，那麼您已經看過我所說的內容。</span><span class="sxs-lookup"><span data-stu-id="8e638-109">If you've fought aliens as they break through your walls in **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)**, unlocked a wall safe in **[Fragments](case-study-creating-an-immersive-experience-in-fragments.md)**, or were lucky enough to see the UNSC Infinity hangar in the **[Halo 5 experience at E3 in 2015](https://www.youtube.com/watch?v=QDw5QjDtFy8)**, then you've seen what I'm talking about.</span></span> <span data-ttu-id="8e638-110">根據您的想像，這個視覺技巧可以用來在您的飾面上放置暫時的洞，或在鬆散的 floorboard 下隱藏世界。</span><span class="sxs-lookup"><span data-stu-id="8e638-110">Depending on your imagination, this visual trick can be used to put temporary holes in your drywall or to hide worlds under a loose floorboard.</span></span>

![RoboRaid 會在您的牆後方新增三維管道和其他結構，只會透過太空入侵者中斷時所建立的漏洞來顯示。](images/roboraid-640px.png)

<span data-ttu-id="8e638-112">RoboRaid 會在您的牆後方新增三維管道和其他結構，只會透過太空入侵者中斷時所建立的漏洞來顯示。</span><span class="sxs-lookup"><span data-stu-id="8e638-112">RoboRaid adds three-dimensional pipes and other structure behind your walls, visible only through holes created as the invaders break through.</span></span>

<span data-ttu-id="8e638-113">使用 HoloLens 上的其中一種獨特的全息影像，應用程式可以在您的牆後方或透過您的樓層提供內容的夢想，其方式與實際的視窗相同。</span><span class="sxs-lookup"><span data-stu-id="8e638-113">Using one of these unique holograms on HoloLens, an app can provide the illusion of content behind your walls or through your floor in the same way that reality presents itself through an actual window.</span></span> <span data-ttu-id="8e638-114">將自己往左移動，您可以看到右側有哪些內容。</span><span class="sxs-lookup"><span data-stu-id="8e638-114">Move yourself left, and you can see whatever is on the right side.</span></span> <span data-ttu-id="8e638-115">深入瞭解，您可以看到更多專案。</span><span class="sxs-lookup"><span data-stu-id="8e638-115">Get closer, and you can see a bit more of everything.</span></span> <span data-ttu-id="8e638-116">主要的差別在於，真正的漏洞讓您能夠通過，而 floor 即時則不會讓您順向神奇全像攝影內容。</span><span class="sxs-lookup"><span data-stu-id="8e638-116">The major difference is that real holes allow you through, while your floor stubbornly won't let you climb through to that magical holographic content.</span></span> <span data-ttu-id="8e638-117">（我會在待處理專案中加入工作）。</span><span class="sxs-lookup"><span data-stu-id="8e638-117">(I'll add a task to the backlog.)</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="8e638-118">幕後</span><span class="sxs-lookup"><span data-stu-id="8e638-118">Behind the scenes</span></span>

<span data-ttu-id="8e638-119">這個技巧是兩種效果的組合。</span><span class="sxs-lookup"><span data-stu-id="8e638-119">This trick is a combination of two effects.</span></span> <span data-ttu-id="8e638-120">首先，使用「空間錨點」將全像攝影內容釘選到世界。</span><span class="sxs-lookup"><span data-stu-id="8e638-120">First, holographic content is pinned to the world using "spatial anchors."</span></span> <span data-ttu-id="8e638-121">使用錨點讓該內容成為「世界鎖定」，表示您所要查看的不會以視覺化方式偏離其附近的實體物件，即使您移動或基礎空間對應系統更新其您房間的3D 模型。</span><span class="sxs-lookup"><span data-stu-id="8e638-121">Using anchors to make that content "world-locked" means that what you're looking at doesn't visually drift away from the physical objects near it, even as you move or the underlying spatial mapping system updates its 3D model of your room.</span></span>

<span data-ttu-id="8e638-122">其次，這種全像攝影內容會以視覺化方式限制在非常特定的空間，因此您只能在現實中看到整個洞。</span><span class="sxs-lookup"><span data-stu-id="8e638-122">Secondly, that holographic content is visually limited to a very specific space, so you can only see through the hole in your reality.</span></span> <span data-ttu-id="8e638-123">這遮蔽是需要查看邏輯洞、視窗或閘口，以銷售訣竅的必要。</span><span class="sxs-lookup"><span data-stu-id="8e638-123">That occlusion is necessary to require looking through a logical hole, window, or doorway, which sells the trick.</span></span> <span data-ttu-id="8e638-124">如果沒有封鎖大部分視圖的專案，密碼 Jurassic 維度的空間破解可能就會像是不良放置的恐龍。</span><span class="sxs-lookup"><span data-stu-id="8e638-124">Without something blocking most of the view, a crack in space to a secret Jurassic dimension might just look like a poorly placed dinosaur.</span></span>

![這不是實際的螢幕擷取畫面，而是從 MR 基本 101 underworld 密碼的說明如何查看 HoloLens。](images/origamiholecomposited-640px.png)

<span data-ttu-id="8e638-128">這不是實際的螢幕擷取畫面，而是從[MR 基本 101](holograms-101.md) underworld 密碼的說明如何查看 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="8e638-128">This is not an actual screenshot, but an illustration of how the secret underworld from the [MR Basics 101](holograms-101.md) looks on HoloLens.</span></span> <span data-ttu-id="8e638-129">黑色主機殼不會顯示，但您可以透過虛擬洞來查看內容。</span><span class="sxs-lookup"><span data-stu-id="8e638-129">The black enclosure doesn’t show up, but you can see content through a virtual hole.</span></span> <span data-ttu-id="8e638-130">（當您查看實際裝置時，地面似乎會消失，因為您的眼睛焦點會與其他距離一樣）。</span><span class="sxs-lookup"><span data-stu-id="8e638-130">(When looking through an actual device, the floor would seem to disappear even more because your eyes focus at a further distance as if it’s not even there.)</span></span>

### <a name="world-locking-holographic-content"></a><span data-ttu-id="8e638-131">世界-鎖定全像攝影內容</span><span class="sxs-lookup"><span data-stu-id="8e638-131">World-locking holographic content</span></span>

<span data-ttu-id="8e638-132">在 Unity 中，使全像攝影內容保持世界鎖定狀態，就像新增 WorldAnchor 元件一樣簡單：</span><span class="sxs-lookup"><span data-stu-id="8e638-132">In Unity, causing holographic content to stay world-locked is as easy as adding a WorldAnchor component:</span></span>

```
myObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="8e638-133">WorldAnchor 元件會持續調整其 GameObject 的位置和旋轉（也就是階層中該物件下的任何其他專案），使其相對於鄰近的實體物件保持穩定。</span><span class="sxs-lookup"><span data-stu-id="8e638-133">The WorldAnchor component will constantly adjust the position and rotation of its GameObject (and thus anything else under that object in the hierarchy) to keep it stable relative to nearby physical objects.</span></span> <span data-ttu-id="8e638-134">撰寫您的內容時，請以您物件的根 pivot 在此虛擬洞置中的方式建立。</span><span class="sxs-lookup"><span data-stu-id="8e638-134">When authoring your content, create it in such a way that the root pivot of your object is centered at this virtual hole.</span></span> <span data-ttu-id="8e638-135">（如果物件的樞紐分析表在牆中是深度的，其位置和旋轉的輕微調整會更明顯，而且洞的外觀可能不穩定）。</span><span class="sxs-lookup"><span data-stu-id="8e638-135">(If your object's pivot is deep in the wall, its slight tweaks in position and rotation will be much more noticeable, and the hole may not look very stable.)</span></span>

### <a name="occluding-everything-but-the-virtual-hole"></a><span data-ttu-id="8e638-136">Occluding 虛擬洞以外的所有專案</span><span class="sxs-lookup"><span data-stu-id="8e638-136">Occluding everything but the virtual hole</span></span>

<span data-ttu-id="8e638-137">有多種方式可以選擇性地封鎖您的牆中隱藏的視圖。</span><span class="sxs-lookup"><span data-stu-id="8e638-137">There are a variety of ways to selectively block the view to what is hidden in your walls.</span></span> <span data-ttu-id="8e638-138">最簡單的方法是讓 HoloLens 使用加法顯示，這表示完全黑色的物件看起來不可見。</span><span class="sxs-lookup"><span data-stu-id="8e638-138">The simplest one takes advantage of the fact that HoloLens uses an additive display, which means that fully black objects appear invisible.</span></span> <span data-ttu-id="8e638-139">您可以在 Unity 中執行這項操作，而不需要進行任何特殊的著色器或材質訣竅，只要建立黑色材質，並將其指派給內容中的物件即可。</span><span class="sxs-lookup"><span data-stu-id="8e638-139">You can do this in Unity without doing any special shader or material tricks— just create a black material and assign it to an object that boxes in your content.</span></span> <span data-ttu-id="8e638-140">如果您不喜歡進行3D 模型化，只要使用幾個預設的四個物件，並稍微重迭它們就可以了。</span><span class="sxs-lookup"><span data-stu-id="8e638-140">If you don't feel like doing 3D modeling, just use a handful of default Quad objects and overlap them slightly.</span></span> <span data-ttu-id="8e638-141">這種方法有幾個缺點，但它是讓工作正常運作的最快方式，而且即使您懷疑稍後可能會想要重構，也是很好的概念證明。</span><span class="sxs-lookup"><span data-stu-id="8e638-141">There are a number of drawbacks to this approach, but it is the fastest way to get something working, and getting a low-fidelity proof of concept working is great, even if you suspect you might want to refactor it later.</span></span>

<span data-ttu-id="8e638-142">上述「黑色箱」方法的一個主要缺點是，它不會有很好的相片。</span><span class="sxs-lookup"><span data-stu-id="8e638-142">One major drawback to the above "black box" approach is that it doesn't photograph well.</span></span> <span data-ttu-id="8e638-143">雖然您的效果可能會透過 HoloLens 的顯示結果，但您所採取的任何螢幕擷取畫面都會顯示大型黑色物件，而不是剩餘的牆或樓層。</span><span class="sxs-lookup"><span data-stu-id="8e638-143">While your effect might look perfect through the display of HoloLens, any screenshots you take will show a large black object instead of what remains of your wall or floor.</span></span> <span data-ttu-id="8e638-144">這是因為實體硬體和螢幕擷取畫面會以不同的方式來複合全息影像和現實。</span><span class="sxs-lookup"><span data-stu-id="8e638-144">The reason for this is that the physical hardware and screenshots composite holograms and reality differently.</span></span> <span data-ttu-id="8e638-145">讓我們繞道一下一些假的數學運算 。</span><span class="sxs-lookup"><span data-stu-id="8e638-145">Let's detour for a moment into some fake math...</span></span>

<span data-ttu-id="8e638-146">*假的數學警示！這些數位和公式的目的是要說明一點，而不是任何精確的度量！*</span><span class="sxs-lookup"><span data-stu-id="8e638-146">*Fake math alert! These numbers and formulas are meant to illustrate a point, not to be any sort of accurate metric!*</span></span>

<span data-ttu-id="8e638-147">您可以透過 HoloLens 看到的內容：</span><span class="sxs-lookup"><span data-stu-id="8e638-147">What you see through HoloLens:</span></span>

```
( Reality * darkening_amount ) + Holograms
```

<span data-ttu-id="8e638-148">您在螢幕擷取畫面和影片中看到的內容：</span><span class="sxs-lookup"><span data-stu-id="8e638-148">What you see in screenshots and video:</span></span>

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

<span data-ttu-id="8e638-149">英文：您透過 HoloLens 看到的內容是簡單的事實（例如透過太陽眼鏡）和應用程式想要顯示的任何全息影像組合。</span><span class="sxs-lookup"><span data-stu-id="8e638-149">In English: What you see through HoloLens is a simple combination of darkened reality (like through sunglasses) and whatever holograms the app wants to show.</span></span> <span data-ttu-id="8e638-150">但是當您拍攝螢幕擷取畫面時，相機的影像會根據每個圖元的透明度值，與應用程式的全息片混合。</span><span class="sxs-lookup"><span data-stu-id="8e638-150">But when you take a screenshot, the camera's image is blended with the app's holograms according to the per-pixel transparency value.</span></span>

<span data-ttu-id="8e638-151">解決這個情況的方法之一，就是將「黑色方塊」材質改成隻寫入深度緩衝區，然後再以所有其他不透明的資料進行排序。</span><span class="sxs-lookup"><span data-stu-id="8e638-151">One way to get around this is to change the "black box" material to only write to the depth buffer, and sort with all the other opaque materials.</span></span> <span data-ttu-id="8e638-152">如需這種情況的範例，請查看[GitHub 上 MixedRealityToolkit 中的 WindowOcclusion。](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader)</span><span class="sxs-lookup"><span data-stu-id="8e638-152">For an example of this, check out the [WindowOcclusion.shader file in the MixedRealityToolkit on GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader).</span></span> <span data-ttu-id="8e638-153">相關行會複製到此處：</span><span class="sxs-lookup"><span data-stu-id="8e638-153">The relevant lines are copied here:</span></span>

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

<span data-ttu-id="8e638-154">（請注意，「Offset 50，100」這一行是用來處理不相關的問題，因此可能有道理）。</span><span class="sxs-lookup"><span data-stu-id="8e638-154">(Note the "Offset 50, 100" line is to deal with unrelated issues, so it'd probably make sense to leave that out.)</span></span>

<span data-ttu-id="8e638-155">執行類似的不可見遮蔽資料，可讓您的應用程式繪製在顯示器和混合現實螢幕擷取畫面中看起來正確的方塊。</span><span class="sxs-lookup"><span data-stu-id="8e638-155">Implementing an invisible occlusion material like that will let your app draw a box that looks correct in the display and in mixed-reality screenshots.</span></span> <span data-ttu-id="8e638-156">對於額外的點數，您可以試著改善該方塊的效能，方法是執行聰明的作業來繪製較少的不可見圖元，但這實際上可以進入直搗黃龍，而且通常不是必要的。</span><span class="sxs-lookup"><span data-stu-id="8e638-156">For bonus points, you can try to improve the performance of that box even further by doing clever things to draw even fewer invisible pixels, but that can really get into the weeds and usually won't be necessary.</span></span>

![以下是來自 MR 基本101的秘密 underworld，因為 Unity 會進行繪製，但 [occluding] 方塊的外部部分除外。](images/underworld-occluded-640px.png)

<span data-ttu-id="8e638-159">以下是來自[MR 基本 101](holograms-101.md)的秘密 underworld，因為 Unity 會進行繪製，但 [occluding] 方塊的外部部分除外。</span><span class="sxs-lookup"><span data-stu-id="8e638-159">Here is the secret underworld from [MR Basics 101](holograms-101.md) as Unity draws it, except for the outer parts of the occluding box.</span></span> <span data-ttu-id="8e638-160">請注意，underworld 的 pivot 位於方塊的中央，這有助於讓孔相對於您實際的樓層保持穩定。</span><span class="sxs-lookup"><span data-stu-id="8e638-160">Note that the pivot for the underworld is at the center of the box, which helps keep the hole as stable as possible relative to your actual floor.</span></span>

## <a name="do-it-yourself"></a><span data-ttu-id="8e638-161">自行執行</span><span class="sxs-lookup"><span data-stu-id="8e638-161">Do it yourself</span></span>

<span data-ttu-id="8e638-162">有 HoloLens，想要自行嘗試效果嗎？</span><span class="sxs-lookup"><span data-stu-id="8e638-162">Have a HoloLens and want to try out the effect for yourself?</span></span> <span data-ttu-id="8e638-163">最簡單的方法就是安裝免費的3D 檢視器應用程式，然後載入[我在 GitHub 上提供的 fbx](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow)檔案，以在您的房間內查看花卉模型。</span><span class="sxs-lookup"><span data-stu-id="8e638-163">The easiest thing you can do (no coding required) is to install the free 3D Viewer app and then load the [download the.fbx file I've provided on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) to view a flower pot model in your room.</span></span> <span data-ttu-id="8e638-164">在 HoloLens 上載入它，您就可以查看工作中的假像。</span><span class="sxs-lookup"><span data-stu-id="8e638-164">Load it on HoloLens, and you can see the illusion at work.</span></span> <span data-ttu-id="8e638-165">當您在模型前方時，您只會看到小洞，其他所有專案則不可見。</span><span class="sxs-lookup"><span data-stu-id="8e638-165">When you're in front of the model, you can only see into the small hole—everything else is invisible.</span></span> <span data-ttu-id="8e638-166">從任何其他端查看模型，它會完全消失。</span><span class="sxs-lookup"><span data-stu-id="8e638-166">Look at the model from any other side and it disappears entirely.</span></span> <span data-ttu-id="8e638-167">使用3D 檢視器的 [移動]、[旋轉] 和 [調整] 控制項，將虛擬洞放在您可以想要產生一些想法的任何垂直表面上！</span><span class="sxs-lookup"><span data-stu-id="8e638-167">Use the movement, rotation, and scale controls of 3D Viewer to position the virtual hole against any vertical surface you can think of to generate some ideas!</span></span>

![在 Unity 編輯器中查看此模型會在 flowerpot 周圍顯示一個大型的黑色方塊。](images/magicwindowflowerpotineditor.png)

<span data-ttu-id="8e638-170">在 Unity 編輯器中查看此模型會在 flowerpot 周圍顯示一個大型的黑色方塊。</span><span class="sxs-lookup"><span data-stu-id="8e638-170">Viewing this model in your Unity editor will show a large black box around the flowerpot.</span></span> <span data-ttu-id="8e638-171">在 HoloLens 上，此方塊會消失，使其成為魔術視窗效果的方式。</span><span class="sxs-lookup"><span data-stu-id="8e638-171">On HoloLens, the box disappears, giving way to a magic window effect.</span></span>

<span data-ttu-id="8e638-172">如果您想要建立使用這項技術的應用程式，請參閱[混合現實教學](tutorials.md)課程中的[MR 基本概念101教學](holograms-101.md)課程。</span><span class="sxs-lookup"><span data-stu-id="8e638-172">If you want to build an app that uses this technique, check out the [MR Basics 101 tutorial](holograms-101.md) in the [Mixed Reality tutorials](tutorials.md).</span></span> <span data-ttu-id="8e638-173">第7章結束于您的樓層中，會顯示隱藏的 underworld （如上圖所示）。</span><span class="sxs-lookup"><span data-stu-id="8e638-173">Chapter 7 ends with an explosion in your floor that reveals a hidden underworld (as pictured above).</span></span> <span data-ttu-id="8e638-174">誰說過教學課程必須是乏味的？</span><span class="sxs-lookup"><span data-stu-id="8e638-174">Who said tutorials had to be boring?</span></span>

<span data-ttu-id="8e638-175">以下是您在下一步可以採取此想法的一些概念：</span><span class="sxs-lookup"><span data-stu-id="8e638-175">Here are some ideas of where you can take this idea next:</span></span>
* <span data-ttu-id="8e638-176">將虛擬洞內的內容視為互動的方式。</span><span class="sxs-lookup"><span data-stu-id="8e638-176">Think of ways to make the content inside the virtual hole interactive.</span></span> <span data-ttu-id="8e638-177">讓您的使用者在其背景上有一些影響，實際上可以改善這項技巧可以提供的意義。</span><span class="sxs-lookup"><span data-stu-id="8e638-177">Letting your users have some impact beyond their walls can really improve the sense of wonder that this trick can provide.</span></span>
* <span data-ttu-id="8e638-178">想辦法將物件查看到已知區域。</span><span class="sxs-lookup"><span data-stu-id="8e638-178">Think of ways to see through objects back to known areas.</span></span> <span data-ttu-id="8e638-179">例如，您要如何在咖啡表中放入全像平面，並查看其底下的樓層？</span><span class="sxs-lookup"><span data-stu-id="8e638-179">For example, how can you put a holographic hole in your coffee table and see your floor beneath it?</span></span>

## <a name="about-the-author"></a><span data-ttu-id="8e638-180">關於作者</span><span class="sxs-lookup"><span data-stu-id="8e638-180">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><span data-ttu-id="8e638-181"><b>Eric Rehmeyer</b></span><span class="sxs-lookup"><span data-stu-id="8e638-181"><b>Eric Rehmeyer</b></span></span><br><span data-ttu-id="8e638-182">資深軟體工程師 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="8e638-182">Senior Software Engineer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="8e638-183">請參閱</span><span class="sxs-lookup"><span data-stu-id="8e638-183">See also</span></span>
* [<span data-ttu-id="8e638-184">MR 基本概念101：使用裝置完成專案</span><span class="sxs-lookup"><span data-stu-id="8e638-184">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="8e638-185">座標系統</span><span class="sxs-lookup"><span data-stu-id="8e638-185">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="8e638-186">空間錨點</span><span class="sxs-lookup"><span data-stu-id="8e638-186">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="8e638-187">空間對應</span><span class="sxs-lookup"><span data-stu-id="8e638-187">Spatial mapping</span></span>](spatial-mapping.md)
