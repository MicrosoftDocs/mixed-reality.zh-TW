---
title: 3D 應用程式啟動器設計指引
description: 3D 應用程式啟動器是使用者 mixed reality 房屋中的「實體」物件，他們可以選擇用來啟動應用程式。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，設計，3D 應用程式啟動器，沉浸式耳機，即時 cube
ms.openlocfilehash: ce9d242e26d67c8fe5af7ac32f4e910a15715d25
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437228"
---
# <a name="3d-app-launcher-design-guidance"></a><span data-ttu-id="87e34-104">3D 應用程式啟動器設計指引</span><span class="sxs-lookup"><span data-stu-id="87e34-104">3D app launcher design guidance</span></span>

<span data-ttu-id="87e34-105">當您放在 Windows Mixed Reality 沉浸式（VR）頭戴式裝置上時，您會進入 Windows Mixed Reality 首頁，並以山脈和水括住的 cliff 做為房屋（雖然您可以[選擇其他環境，甚至是建立自己的環境](add-custom-home-environments.md)）。</span><span class="sxs-lookup"><span data-stu-id="87e34-105">When you put on a Windows Mixed Reality immersive (VR) headset, you enter the Windows Mixed Reality home, visualized as a house on a cliff surrounded by mountains and water (though you can [choose other environments and even create your own](add-custom-home-environments.md)).</span></span> <span data-ttu-id="87e34-106">在此家中的空間內，使用者可以自由地排列及組織其所需的3D 物件和應用程式。</span><span class="sxs-lookup"><span data-stu-id="87e34-106">Within the space of this home, a user is free to arrange and organize the 3D objects and apps that they care about any way they want.</span></span> <span data-ttu-id="87e34-107">**3d 應用程式啟動器**是使用者 mixed reality 房屋中的「實體」物件，他們可以選擇用來啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="87e34-107">A **3D app launcher** is a “physical” object in the user’s mixed reality house that they can select to launch an app.</span></span>

<span data-ttu-id="87e34-108">![範例： Floaty 鳥3D 應用程式啟動器](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="87e34-108">![Example: Floaty Bird 3D app launcher](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="87e34-109">*Floaty 鳥3D 應用程式啟動器範例（虛構應用程式）*</span><span class="sxs-lookup"><span data-stu-id="87e34-109">*Floaty Bird 3D app launcher example (fictional app)*</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="87e34-110">3D 應用程式啟動器建立進程</span><span class="sxs-lookup"><span data-stu-id="87e34-110">3D app launcher creation process</span></span>

<span data-ttu-id="87e34-111">建立3D 應用程式啟動器有3個步驟：</span><span class="sxs-lookup"><span data-stu-id="87e34-111">There are 3 steps to creating a 3D app launcher:</span></span>
1. <span data-ttu-id="87e34-112">設計和 concepting （本文）</span><span class="sxs-lookup"><span data-stu-id="87e34-112">Designing and concepting (this article)</span></span>
2. [<span data-ttu-id="87e34-113">模型化和匯出</span><span class="sxs-lookup"><span data-stu-id="87e34-113">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="87e34-114">將它整合到您的應用程式中：</span><span class="sxs-lookup"><span data-stu-id="87e34-114">Integrating it into your application:</span></span>
    * [<span data-ttu-id="87e34-115">UWP app</span><span class="sxs-lookup"><span data-stu-id="87e34-115">UWP apps</span></span>](implementing-3d-app-launchers.md)
    * [<span data-ttu-id="87e34-116">Win32 應用程式</span><span class="sxs-lookup"><span data-stu-id="87e34-116">Win32 apps</span></span>](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a><span data-ttu-id="87e34-117">設計概念</span><span class="sxs-lookup"><span data-stu-id="87e34-117">Design concepts</span></span>

### <a name="fantastic-yet-familiar"></a><span data-ttu-id="87e34-118">非常熟悉的絕佳</span><span class="sxs-lookup"><span data-stu-id="87e34-118">Fantastic yet familiar</span></span>

<span data-ttu-id="87e34-119">您的應用程式啟動器所在的 Windows Mixed Reality 環境是常見的部分 fantastical/sci。</span><span class="sxs-lookup"><span data-stu-id="87e34-119">The Windows Mixed Reality environment your app launcher lives in is part familiar, part fantastical/sci-fi.</span></span> <span data-ttu-id="87e34-120">最佳的啟動器會遵循此世界的規則。</span><span class="sxs-lookup"><span data-stu-id="87e34-120">The best launchers follow the rules of this world.</span></span> <span data-ttu-id="87e34-121">請考慮如何從您的應用程式中採取熟悉、具代表性的物件，但會將一些實際的現實規則折。</span><span class="sxs-lookup"><span data-stu-id="87e34-121">Think of how you can take a familiar, representative object from your app, but bend some of the rules of actual reality.</span></span> <span data-ttu-id="87e34-122">會產生魔術。</span><span class="sxs-lookup"><span data-stu-id="87e34-122">Magic will result.</span></span>

### <a name="intuitive"></a><span data-ttu-id="87e34-123">基本</span><span class="sxs-lookup"><span data-stu-id="87e34-123">Intuitive</span></span>

<span data-ttu-id="87e34-124">當您查看應用程式啟動器時，其目的是要啟動您的應用程式，應該很明顯，而且不會造成任何混淆。</span><span class="sxs-lookup"><span data-stu-id="87e34-124">When you look at your app launcher, its purpose - to launch your app - should be obvious and shouldn’t cause any confusion.</span></span> <span data-ttu-id="87e34-125">例如，請確定您的啟動器是您應用程式的相當明顯的代表，而不會與 Cliff 房屋中的一段 décor 混淆。</span><span class="sxs-lookup"><span data-stu-id="87e34-125">For example, be sure your launcher is an obvious-enough representative of your app that it won’t be confused for a piece of decor in the Cliff House.</span></span> <span data-ttu-id="87e34-126">您的應用程式啟動器應邀請人員進行觸控/選取。</span><span class="sxs-lookup"><span data-stu-id="87e34-126">Your app launcher should invite people to touch/select it.</span></span>

<span data-ttu-id="87e34-127">![範例：全新附注3D 應用程式啟動器](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="87e34-127">![Example: Fresh Note 3D app launcher](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="87e34-128">*最新附注3D 應用程式啟動器範例（虛構應用程式）*</span><span class="sxs-lookup"><span data-stu-id="87e34-128">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="home-scale"></a><span data-ttu-id="87e34-129">首頁規模</span><span class="sxs-lookup"><span data-stu-id="87e34-129">Home scale</span></span>

<span data-ttu-id="87e34-130">3D 應用程式啟動器會存留在 Cliff 房屋中，而其預設大小應該與空間中的其他「實體」物件有意義。</span><span class="sxs-lookup"><span data-stu-id="87e34-130">3D app launchers live in the Cliff House and their default size should make sense with the other “physical” objects in the space.</span></span> <span data-ttu-id="87e34-131">如果您將啟動器放在旁邊（例如，房屋工廠或某些傢俱），它應該會在家裡，以大小為依據。</span><span class="sxs-lookup"><span data-stu-id="87e34-131">If you place your launcher beside, say, a house plant or some furniture, it should feel at home, size-wise.</span></span> <span data-ttu-id="87e34-132">最好的起點是查看它看起來是30個立方的角度，但請記住，使用者可以視需要相應增加或減少。</span><span class="sxs-lookup"><span data-stu-id="87e34-132">A good starting point is to see how it looks at 30 cubic centimeters, but remember that users can scale it up or down if they like.</span></span>

### <a name="own-able"></a><span data-ttu-id="87e34-133">擁有能力</span><span class="sxs-lookup"><span data-stu-id="87e34-133">Own-able</span></span>

<span data-ttu-id="87e34-134">應用程式啟動器應該會像是使用者在其空間中可能很高興的物件。</span><span class="sxs-lookup"><span data-stu-id="87e34-134">The app launcher should feel like an object a person would be excited to have in their space.</span></span> <span data-ttu-id="87e34-135">它們幾乎都是在這些專案的周圍，因此啟動器應該會像是使用者認為有足夠的東西來尋求和保持鄰近。</span><span class="sxs-lookup"><span data-stu-id="87e34-135">They’ll be virtually surrounding themselves with these things, so the launcher should feel like something the user thought was desirable enough to seek out and keep nearby.</span></span>

<span data-ttu-id="87e34-136">![範例： Astro 扭曲3D 應用程式啟動器](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="87e34-136">![Example: Astro Warp 3D app launcher](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="87e34-137">*Astro 扭曲3D 應用程式啟動器範例（虛構應用程式）*</span><span class="sxs-lookup"><span data-stu-id="87e34-137">*Astro Warp 3D app launcher example (fictional app)*</span></span>

### <a name="recognizable"></a><span data-ttu-id="87e34-138">辨識</span><span class="sxs-lookup"><span data-stu-id="87e34-138">Recognizable</span></span>

<span data-ttu-id="87e34-139">您的3D 應用程式啟動器應該會立即將「您的應用程式品牌」表示為看到它的人員。</span><span class="sxs-lookup"><span data-stu-id="87e34-139">Your 3D app launcher should instantly express “your app’s brand” to people who see it.</span></span> <span data-ttu-id="87e34-140">如果您的應用程式中有星號字元或特別可識別的物件，我們建議您將其當做設計的一個重要部分使用。</span><span class="sxs-lookup"><span data-stu-id="87e34-140">If you have a star character or an especially identifiable object in your app, we recommend using that as a big part of your design.</span></span> <span data-ttu-id="87e34-141">在混合現實世界中，物件對使用者的興趣會比僅限標誌更有趣。</span><span class="sxs-lookup"><span data-stu-id="87e34-141">In a mixed reality world, an object will draw more interest from users than just a logo alone.</span></span> <span data-ttu-id="87e34-142">可辨識的物件可快速且清楚地傳達品牌。</span><span class="sxs-lookup"><span data-stu-id="87e34-142">Recognizable objects communicate brand quickly and clearly.</span></span>

### <a name="volumetric"></a><span data-ttu-id="87e34-143">體積型</span><span class="sxs-lookup"><span data-stu-id="87e34-143">Volumetric</span></span>

<span data-ttu-id="87e34-144">您的應用程式所需的不僅僅是將您的標誌放在平面上，並一天呼叫它。</span><span class="sxs-lookup"><span data-stu-id="87e34-144">Your app deserves more than just putting your logo on a flat plane and calling it a day.</span></span> <span data-ttu-id="87e34-145">您的啟動器應該會像是使用者空間中令人興奮的3D 實體物件。</span><span class="sxs-lookup"><span data-stu-id="87e34-145">Your launcher should feel like an exciting, 3D, physical object in the user’s space.</span></span> <span data-ttu-id="87e34-146">理想的方法是假設您的應用程式在 Macy 的感恩節日行列中會有一個氣球。</span><span class="sxs-lookup"><span data-stu-id="87e34-146">A good approach is to imagine your app was going to have a balloon in the Macy’s Thanksgiving Day Parade.</span></span> <span data-ttu-id="87e34-147">問自己，究竟是什麼人會碰到街道的問題呢？</span><span class="sxs-lookup"><span data-stu-id="87e34-147">Ask yourself, what would really wow people as it came down the street?</span></span> <span data-ttu-id="87e34-148">所有的觀賞角度看起來很棒嗎？</span><span class="sxs-lookup"><span data-stu-id="87e34-148">What would look great from all viewing angles?</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="87e34-149">僅](images/20171016-140436-mixedreality-640px.jpg)*標誌*![標誌</span><span class="sxs-lookup"><span data-stu-id="87e34-149">![Logo only](images/20171016-140436-mixedreality-640px.jpg) *Logo only*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="87e34-150">使用字元](images/20171016-140557-mixedreality-640px.jpg)*更容易辨識*![更容易辨識</span><span class="sxs-lookup"><span data-stu-id="87e34-150">![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg) *More recognizable with a character*</span></span>
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
        <span data-ttu-id="87e34-151">![一般方法，而不是驚訝的，自然](images/20171016-155101-mixedreality-640px.jpg) 的平面*方法，而不是驚訝的*平面</span><span class="sxs-lookup"><span data-stu-id="87e34-151">![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg) *Flat approach, not surprisingly, feels flat*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="87e34-152">![體積型方法更妥善展示應用程式](images/20171016-161407-mixedreality-640px.jpg)*體積型方法更妥善展示您的應用程式*</span><span class="sxs-lookup"><span data-stu-id="87e34-152">![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg) *Volumetric approach better showcases your app*</span></span>
    :::column-end:::
:::row-end:::


## <a name="tips-for-good-3d-models"></a><span data-ttu-id="87e34-153">良好3D 模型的秘訣</span><span class="sxs-lookup"><span data-stu-id="87e34-153">Tips for good 3D models</span></span>

### <a name="best-practices"></a><span data-ttu-id="87e34-154">最佳做法</span><span class="sxs-lookup"><span data-stu-id="87e34-154">Best practices</span></span>
* <span data-ttu-id="87e34-155">在規劃應用程式啟動器的維度時，大約會針對 30cm cube 進行排除。</span><span class="sxs-lookup"><span data-stu-id="87e34-155">When planning dimensions for your app launcher, shoot for roughly a 30cm cube.</span></span> <span data-ttu-id="87e34-156">因此，1:1:1 的大小比例。</span><span class="sxs-lookup"><span data-stu-id="87e34-156">So, a 1:1:1 size ratio.</span></span>
* <span data-ttu-id="87e34-157">模型必須低於10000個多邊形。</span><span class="sxs-lookup"><span data-stu-id="87e34-157">Models must be under 10,000 polygons.</span></span> [<span data-ttu-id="87e34-158">深入瞭解三角形計數和詳細資料層級（LODs）</span><span class="sxs-lookup"><span data-stu-id="87e34-158">Learn more about triangle counts and levels of details (LODs)</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* <span data-ttu-id="87e34-159">盡可能在沉浸式耳機上測試。</span><span class="sxs-lookup"><span data-stu-id="87e34-159">Test on an immersive headset when possible.</span></span>
* <span data-ttu-id="87e34-160">盡可能將詳細資料組建到模型的幾何中–不依賴材質以取得詳細資料。</span><span class="sxs-lookup"><span data-stu-id="87e34-160">Build details into your model’s geometry where possible – don’t rely on textures for detail.</span></span>
* <span data-ttu-id="87e34-161">建立「水緊密」封閉的幾何。</span><span class="sxs-lookup"><span data-stu-id="87e34-161">Build “water tight” closed geometry.</span></span> <span data-ttu-id="87e34-162">沒有任何在中模型化的漏洞。</span><span class="sxs-lookup"><span data-stu-id="87e34-162">No holes that are not modeled in.</span></span>
* <span data-ttu-id="87e34-163">在您的物件中使用自然材質。</span><span class="sxs-lookup"><span data-stu-id="87e34-163">Use natural materials in your object.</span></span> <span data-ttu-id="87e34-164">想像一下在現實世界裡製作它。</span><span class="sxs-lookup"><span data-stu-id="87e34-164">Imagine crafting it in the real world.</span></span>
* <span data-ttu-id="87e34-165">請確定您的模型會以不同的距離和大小來妥善閱讀。</span><span class="sxs-lookup"><span data-stu-id="87e34-165">Make sure your model reads well at different distances and sizes.</span></span>
* <span data-ttu-id="87e34-166">當您的模型準備就緒時，請閱讀[匯出資產指導方針](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview)。</span><span class="sxs-lookup"><span data-stu-id="87e34-166">When your model is ready to go, read the [exporting assets guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span></span>

<span data-ttu-id="87e34-167">材質中包含細微詳細資料的 ![模型](images/20171013-143334-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="87e34-167">![Model with subtle details in the texture](images/20171013-143334-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="87e34-168">*材質中包含細微詳細資料的模型*</span><span class="sxs-lookup"><span data-stu-id="87e34-168">*Model with subtle details in the texture*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="87e34-169">應避免的事項</span><span class="sxs-lookup"><span data-stu-id="87e34-169">What to avoid</span></span>
* <span data-ttu-id="87e34-170">請勿使用高對比的詳細資料或小型、忙碌的模式和紋理。</span><span class="sxs-lookup"><span data-stu-id="87e34-170">Don't use high-contrast details or small, busy patterns and textures.</span></span>
* <span data-ttu-id="87e34-171">不要使用精簡型幾何–它不會在某個距離運作良好，而且別名會不正確。</span><span class="sxs-lookup"><span data-stu-id="87e34-171">Don't use thin geometry – it doesn’t work well at a distance and will alias badly.</span></span>
* <span data-ttu-id="87e34-172">不要讓模型的部分延伸太多超過1:1:1 的大小比例。</span><span class="sxs-lookup"><span data-stu-id="87e34-172">Don't let parts of your model extend too much beyond the 1:1:1 size ratio.</span></span> <span data-ttu-id="87e34-173">它會建立調整問題。</span><span class="sxs-lookup"><span data-stu-id="87e34-173">It will create scaling problems.</span></span>

<span data-ttu-id="87e34-174">![避免高對比、小型忙碌模式](images/20171013-143603-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="87e34-174">![Avoid high-contrast, small busy patterns](images/20171013-143603-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="87e34-175">*避免高對比、小型、忙碌模式*</span><span class="sxs-lookup"><span data-stu-id="87e34-175">*Avoid high-contrast, small, busy patterns*</span></span>

## <a name="how-to-handle-type"></a><span data-ttu-id="87e34-176">如何處理類型</span><span class="sxs-lookup"><span data-stu-id="87e34-176">How to handle type</span></span>

### <a name="best-practices"></a><span data-ttu-id="87e34-177">最佳做法</span><span class="sxs-lookup"><span data-stu-id="87e34-177">Best practices</span></span>
* <span data-ttu-id="87e34-178">我們建議您的類型包含應用程式啟動器（或更多）的1/3。</span><span class="sxs-lookup"><span data-stu-id="87e34-178">We recommend your type comprises about 1/3 of your app launcher (or more).</span></span> <span data-ttu-id="87e34-179">「類型」（Type）主要是讓人們知道您的啟動器實際上是啟動器，因此如果非常重要，就很好用。</span><span class="sxs-lookup"><span data-stu-id="87e34-179">Type is the main thing that gives people an idea that your launcher is, in fact, a launcher so it’s nice if it’s pretty substantial.</span></span>
* <span data-ttu-id="87e34-180">避免讓類型變寬–請嘗試將它保留在應用程式啟動器核心維度的範圍內（更多或更少）。</span><span class="sxs-lookup"><span data-stu-id="87e34-180">Avoid making type super wide – try to keep it within the confines of the app launchers core dimensions (more or less).</span></span>
* <span data-ttu-id="87e34-181">一般類型可以工作，但請注意，在某些環境中可能難以從特定角度進行觀看。</span><span class="sxs-lookup"><span data-stu-id="87e34-181">Flat type can work, but be aware that it can be hard to view from certain angles and in certain environments.</span></span> <span data-ttu-id="87e34-182">您可以考慮將它放在其背後的實心物件或背景，以協助解決此情況。</span><span class="sxs-lookup"><span data-stu-id="87e34-182">You might consider putting it a solid object or backdrop behind it to help with this.</span></span>
* <span data-ttu-id="87e34-183">將維度加入至您的類型會在3D 中感覺良好。</span><span class="sxs-lookup"><span data-stu-id="87e34-183">Adding dimension to your type feels nice in 3D.</span></span> <span data-ttu-id="87e34-184">網底：類型的兩側不同，較暗的色彩有助於閱讀。</span><span class="sxs-lookup"><span data-stu-id="87e34-184">Shading the sides of the type a different, darker color can help with readability.</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="87e34-185">不使用背景的 ![平面類型可能難以從特定角度觀看，而且在特定環境中](images/flattype-640px.png)*沒有背景的平面類型，* 在某些環境中可能難以觀看</span><span class="sxs-lookup"><span data-stu-id="87e34-185">![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png) *Flat type without a backdrop can be hard to view from certain angles and in certain environments*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="87e34-186">具有內建背景的 ![類型可以正常運作](images/flattypeandbkg-640px.png)*類型具有內建的背景功能，因此可以運作良好*</span><span class="sxs-lookup"><span data-stu-id="87e34-186">![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png) *Type with a built-in backdrop can work well*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="87e34-187">如果您為邊加上陰影，![的拉伸類型就能正常運作](images/20171016-160221-mixedreality-640px.jpg)*拉伸類型*</span><span class="sxs-lookup"><span data-stu-id="87e34-187">![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg) *Extruded type can work well if you shade the sides*</span></span>
    :::column-end:::
:::row-end:::


<span data-ttu-id="87e34-188">**輸入可使用的色彩**</span><span class="sxs-lookup"><span data-stu-id="87e34-188">**Type colors that work**</span></span>
* <span data-ttu-id="87e34-189">份</span><span class="sxs-lookup"><span data-stu-id="87e34-189">White</span></span>
* <span data-ttu-id="87e34-190">號</span><span class="sxs-lookup"><span data-stu-id="87e34-190">Black</span></span>
* <span data-ttu-id="87e34-191">明亮的半形色彩</span><span class="sxs-lookup"><span data-stu-id="87e34-191">Bright semi-saturated color</span></span>

<span data-ttu-id="87e34-192">![類型可使用的色彩。](images/20171016-112111-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="87e34-192">![Type colors that work.](images/20171016-112111-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="87e34-193">*輸入可使用的色彩*</span><span class="sxs-lookup"><span data-stu-id="87e34-193">*Type colors that work*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="87e34-194">應避免的事項</span><span class="sxs-lookup"><span data-stu-id="87e34-194">What to avoid</span></span>

<span data-ttu-id="87e34-195">**輸入造成問題的色彩**</span><span class="sxs-lookup"><span data-stu-id="87e34-195">**Type colors that cause trouble**</span></span>
* <span data-ttu-id="87e34-196">中間色調</span><span class="sxs-lookup"><span data-stu-id="87e34-196">Mid-tones</span></span>
* <span data-ttu-id="87e34-197">灰色</span><span class="sxs-lookup"><span data-stu-id="87e34-197">Gray</span></span>
* <span data-ttu-id="87e34-198">過度飽和色彩或 desaturated 色彩</span><span class="sxs-lookup"><span data-stu-id="87e34-198">Over-saturated colors or desaturated colors</span></span>

<span data-ttu-id="87e34-199">![類型會造成問題的色彩。](images/20171016-112246-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="87e34-199">![Type colors that cause trouble.](images/20171016-112246-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="87e34-200">*輸入造成問題的色彩*</span><span class="sxs-lookup"><span data-stu-id="87e34-200">*Type colors that cause trouble*</span></span>

## <a name="lighting"></a><span data-ttu-id="87e34-201">光源</span><span class="sxs-lookup"><span data-stu-id="87e34-201">Lighting</span></span>

<span data-ttu-id="87e34-202">應用程式啟動器的光源來自 Cliff 房屋環境。</span><span class="sxs-lookup"><span data-stu-id="87e34-202">The lighting for your app launcher comes from the Cliff House environment.</span></span> <span data-ttu-id="87e34-203">請務必在房屋的幾個地方測試您的啟動程式，使其在光線和陰影中都看起來很好。</span><span class="sxs-lookup"><span data-stu-id="87e34-203">Be sure to test your launcher in several places throughout the house so it looks good in both light and shadows.</span></span> <span data-ttu-id="87e34-204">好消息是，如果您已依照本檔中的其他設計指引進行，則您的啟動器應該會針對 Cliff 房屋中的大部分光源提供良好的圖形。</span><span class="sxs-lookup"><span data-stu-id="87e34-204">The good news is, if you’ve followed the other design guidance in this document, your launcher should be in pretty good shape for most lighting in the Cliff House.</span></span>

<span data-ttu-id="87e34-205">測試啟動程式如何在環境中查看各種光線的好地方，就是 Studio、媒體聊天室、Patio 內外的任何位置（具有草地的具體區域）。</span><span class="sxs-lookup"><span data-stu-id="87e34-205">Good places to test how your launcher looks in the various lights in the environment are the Studio, the Media Room, anywhere outside and on the Back Patio (the concrete area with the lawn).</span></span> <span data-ttu-id="87e34-206">另一個良好的測試是將它放在半淺色和半陰影，看看它的外觀。</span><span class="sxs-lookup"><span data-stu-id="87e34-206">Another good test is to put it in half light and half shadow and see what it looks like.</span></span>

<span data-ttu-id="87e34-207">![確保您的啟動器在光線和陰影中都看起來良好。](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="87e34-207">![Make sure your launcher looks good in both light and shadows.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="87e34-208">*請確定您的啟動器在光線和陰影中都看起來良好*</span><span class="sxs-lookup"><span data-stu-id="87e34-208">*Make sure your launcher looks good in both light and shadows*</span></span>

## <a name="texturing"></a><span data-ttu-id="87e34-209">繪製</span><span class="sxs-lookup"><span data-stu-id="87e34-209">Texturing</span></span>

### <a name="authoring-your-textures"></a><span data-ttu-id="87e34-210">撰寫您的紋理</span><span class="sxs-lookup"><span data-stu-id="87e34-210">Authoring your textures</span></span>

<span data-ttu-id="87e34-211">3D 應用程式啟動器的結束格式會是 glb 檔案，這是使用 .PBR （實際轉譯）管線所建立的。</span><span class="sxs-lookup"><span data-stu-id="87e34-211">The end format of your 3D app launcher will be a .glb file, which is made using the PBR (Physically Based Rendering) pipeline.</span></span> <span data-ttu-id="87e34-212">這可能是一種棘手的程式，如果您還沒這麼做，現在是採用技術演出者的好時機。</span><span class="sxs-lookup"><span data-stu-id="87e34-212">This can be a tricky process - now is a good time to employ a technical artist if you haven't already.</span></span> <span data-ttu-id="87e34-213">如果您是美麗 DIY-er，請花時間[研究並學習 .pbr 術語](https://wiki.polycount.com/wiki/PBR)，而在您開始之前，將會協助您避免常見的錯誤。</span><span class="sxs-lookup"><span data-stu-id="87e34-213">If you’re a brave DIY-er, taking the time to [research and learn PBR terminology](https://wiki.polycount.com/wiki/PBR) and what’s happening under the hood before you begin will help you avoid common mistakes.</span></span> 

<span data-ttu-id="87e34-214">![範例：全新便箋應用程式](images/pbr-freshnote1-640px-500px.png)</span><span class="sxs-lookup"><span data-stu-id="87e34-214">![Example: Fresh Note app](images/pbr-freshnote1-640px-500px.png)</span></span><br>
<span data-ttu-id="87e34-215">*最新附注3D 應用程式啟動器範例（虛構應用程式）*</span><span class="sxs-lookup"><span data-stu-id="87e34-215">*Fresh Note 3D app launcher example (fictional app)*</span></span>

<span data-ttu-id="87e34-216">**建議的 authoring tool**</span><span class="sxs-lookup"><span data-stu-id="87e34-216">**Recommended authoring tool**</span></span>

<span data-ttu-id="87e34-217">我們建議使用 Allegorithmic 的[物質刷](https://www.allegorithmic.com/products/substance-painter)來撰寫您的最終檔案。</span><span class="sxs-lookup"><span data-stu-id="87e34-217">We recommend using [Substance Painter](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic to author your final file.</span></span> <span data-ttu-id="87e34-218">如果您不熟悉在「物質刷」中撰寫「.PBR 著色器」，以下是一個[教學](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials)課程。</span><span class="sxs-lookup"><span data-stu-id="87e34-218">If you’re not familiar with authoring PBR shaders in Substance Painter, here’s a [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span></span>

<span data-ttu-id="87e34-219">（或者，如果您比較熟悉其中一個，則[Coat](https://3dcoat.com/home/)、 [Quixel Suite 2](https://quixel.se/suite2/)或[Marmoset Toolbag](https://www.marmoset.co/toolbag/)也適用）。</span><span class="sxs-lookup"><span data-stu-id="87e34-219">(Alternately [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), or [Marmoset Toolbag](https://www.marmoset.co/toolbag/) would also work if you’re more familiar with one of these.)</span></span>

### <a name="best-practices"></a><span data-ttu-id="87e34-220">最佳做法</span><span class="sxs-lookup"><span data-stu-id="87e34-220">Best practices</span></span>

* <span data-ttu-id="87e34-221">如果您的應用程式啟動器物件是針對 .PBR 所撰寫，則將它轉換為 Cliff 房屋環境應該相當簡單。</span><span class="sxs-lookup"><span data-stu-id="87e34-221">If your app launcher object was authored for PBR, it should be pretty straightforward to convert it for the Cliff House environment.</span></span>
* <span data-ttu-id="87e34-222">我們的著色器預期是金屬/粗糙度工作流程– Unreal 的 .PBR 著色器是一個靠近的傳真。</span><span class="sxs-lookup"><span data-stu-id="87e34-222">Our shader is expecting a Metal/Roughness work flow – The Unreal PBR shader is a close facsimile.</span></span>
* <span data-ttu-id="87e34-223">匯出材質時，請記住[建議的材質大小](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines)。</span><span class="sxs-lookup"><span data-stu-id="87e34-223">When exporting your textures keep the [recommended texture sizes](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) in mind.</span></span>
* <span data-ttu-id="87e34-224">請務必建立即時光源的物件，這表示：</span><span class="sxs-lookup"><span data-stu-id="87e34-224">Make sure to build your objects for real-time lighting — this means:</span></span>
    * <span data-ttu-id="87e34-225">避免內建陰影-或繪製陰影</span><span class="sxs-lookup"><span data-stu-id="87e34-225">Avoid baked shadows – or painted shadows</span></span>
    * <span data-ttu-id="87e34-226">避免在材質中內建光源</span><span class="sxs-lookup"><span data-stu-id="87e34-226">Avoid baked lighting in the textures</span></span>
    * <span data-ttu-id="87e34-227">使用其中一個 .PBR 材質撰寫套件來取得為著色器產生的正確對應</span><span class="sxs-lookup"><span data-stu-id="87e34-227">Use one of the PBR material authoring packages to get the right maps generated for our shader</span></span>

## <a name="see-also"></a><span data-ttu-id="87e34-228">請參閱</span><span class="sxs-lookup"><span data-stu-id="87e34-228">See also</span></span>

* [<span data-ttu-id="87e34-229">建立要在混合現實首頁中使用的3D 模型</span><span class="sxs-lookup"><span data-stu-id="87e34-229">Create 3D models for use in the mixed reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="87e34-230">實作 3D 應用程式啟動器 (UWP 應用程式)</span><span class="sxs-lookup"><span data-stu-id="87e34-230">Implement 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="87e34-231">實作 3D 應用程式啟動器 (Win32 應用程式)</span><span class="sxs-lookup"><span data-stu-id="87e34-231">Implement 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
