---
title: 3D 應用程式啟動程式的設計指引
description: 3D 應用程式啟動程式是一個 「 實體 」 的物件，他們可以選取的啟動應用程式的使用者的混合的實境房子。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，設計、 3D 應用程式啟動程式、 沈浸式耳機、 即時的 cube
ms.openlocfilehash: 47db5bffa121c0cc11d246dc749c464e5f187270
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591328"
---
# <a name="3d-app-launcher-design-guidance"></a><span data-ttu-id="0c33b-104">3D 應用程式啟動程式的設計指引</span><span class="sxs-lookup"><span data-stu-id="0c33b-104">3D app launcher design guidance</span></span>

<span data-ttu-id="0c33b-105">當您將在 Windows Mixed Reality 沈浸式 (VR) 耳機時，您可以輸入家中的 Windows Mixed Reality 視覺化為房屋下懸崖住山脈與水 (雖然您可以[選擇其他環境，甚至建立您自己](add-custom-home-environments.md)).</span><span class="sxs-lookup"><span data-stu-id="0c33b-105">When you put on a Windows Mixed Reality immersive (VR) headset, you enter the Windows Mixed Reality home, visualized as a house on a cliff surrounded by mountains and water (though you can [choose other environments and even create your own](add-custom-home-environments.md)).</span></span> <span data-ttu-id="0c33b-106">這個空間內首頁，使用者可以自由排列及組織的 3D 物件和他們很關心它們想要的任何方式的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0c33b-106">Within the space of this home, a user is free to arrange and organize the 3D objects and apps that they care about any way they want.</span></span> <span data-ttu-id="0c33b-107">A **3D 應用程式啟動器**是在使用者的 「 實體 」 物件的混合實境房子，他們可以選取的啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="0c33b-107">A **3D app launcher** is a “physical” object in the user’s mixed reality house that they can select to launch an app.</span></span>

<span data-ttu-id="0c33b-108">![範例：浮動 Bird 3D 應用程式啟動器](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="0c33b-108">![Example: Floaty Bird 3D app launcher](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="0c33b-109">*浮動 Bird 3D 應用程式啟動器範例 （虛構應用程式）*</span><span class="sxs-lookup"><span data-stu-id="0c33b-109">*Floaty Bird 3D app launcher example (fictional app)*</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="0c33b-110">3D 應用程式啟動器建立程序</span><span class="sxs-lookup"><span data-stu-id="0c33b-110">3D app launcher creation process</span></span>

<span data-ttu-id="0c33b-111">有 3 個步驟以建立 3D 應用程式啟動程式：</span><span class="sxs-lookup"><span data-stu-id="0c33b-111">There are 3 steps to creating a 3D app launcher:</span></span>
1. <span data-ttu-id="0c33b-112">設計和 concepting （本文）</span><span class="sxs-lookup"><span data-stu-id="0c33b-112">Designing and concepting (this article)</span></span>
2. [<span data-ttu-id="0c33b-113">模型化和匯出</span><span class="sxs-lookup"><span data-stu-id="0c33b-113">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="0c33b-114">請將它整合到您的應用程式：</span><span class="sxs-lookup"><span data-stu-id="0c33b-114">Integrating it into your application:</span></span>
    * [<span data-ttu-id="0c33b-115">UWP 應用程式</span><span class="sxs-lookup"><span data-stu-id="0c33b-115">UWP apps</span></span>](implementing-3d-app-launchers.md)
    * [<span data-ttu-id="0c33b-116">Win32 應用程式</span><span class="sxs-lookup"><span data-stu-id="0c33b-116">Win32 apps</span></span>](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a><span data-ttu-id="0c33b-117">設計概念</span><span class="sxs-lookup"><span data-stu-id="0c33b-117">Design concepts</span></span>

### <a name="fantastic-yet-familiar"></a><span data-ttu-id="0c33b-118">超棒的但熟悉</span><span class="sxs-lookup"><span data-stu-id="0c33b-118">Fantastic yet familiar</span></span>

<span data-ttu-id="0c33b-119">您的應用程式啟動程式存在於 Windows Mixed Reality 環境是部分陌生，部分成冊/sci-fi。</span><span class="sxs-lookup"><span data-stu-id="0c33b-119">The Windows Mixed Reality environment your app launcher lives in is part familiar, part fantastical/sci-fi.</span></span> <span data-ttu-id="0c33b-120">最佳的啟動器會遵循這個世界的規則。</span><span class="sxs-lookup"><span data-stu-id="0c33b-120">The best launchers follow the rules of this world.</span></span> <span data-ttu-id="0c33b-121">將如何從您的應用程式，採用熟悉的代表性物件，但東改西改的一些實際的現實的規則。</span><span class="sxs-lookup"><span data-stu-id="0c33b-121">Think of how you can take a familiar, representative object from your app, but bend some of the rules of actual reality.</span></span> <span data-ttu-id="0c33b-122">將會產生魔術。</span><span class="sxs-lookup"><span data-stu-id="0c33b-122">Magic will result.</span></span>

### <a name="intuitive"></a><span data-ttu-id="0c33b-123">直覺式</span><span class="sxs-lookup"><span data-stu-id="0c33b-123">Intuitive</span></span>

<span data-ttu-id="0c33b-124">當您查看您的應用程式啟動程式時，其用途-啟動您的應用程式-應該很明顯，而且不應該造成任何混淆。</span><span class="sxs-lookup"><span data-stu-id="0c33b-124">When you look at your app launcher, its purpose - to launch your app - should be obvious and shouldn’t cause any confusion.</span></span> <span data-ttu-id="0c33b-125">比方說，是確定您的啟動程式是您的應用程式，它將不會混淆 decor Cliff 屋裡的一項明顯夠代表。</span><span class="sxs-lookup"><span data-stu-id="0c33b-125">For example, be sure your launcher is an obvious-enough representative of your app that it won’t be confused for a piece of decor in the Cliff House.</span></span> <span data-ttu-id="0c33b-126">您的應用程式啟動程式應該邀請人觸控/選取它。</span><span class="sxs-lookup"><span data-stu-id="0c33b-126">Your app launcher should invite people to touch/select it.</span></span>

<span data-ttu-id="0c33b-127">![範例：全新的附註 3D 應用程式啟動器](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="0c33b-127">![Example: Fresh Note 3D app launcher](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="0c33b-128">*全新的附註 3D 應用程式啟動器範例 （虛構應用程式）*</span><span class="sxs-lookup"><span data-stu-id="0c33b-128">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="home-scale"></a><span data-ttu-id="0c33b-129">主要刻度</span><span class="sxs-lookup"><span data-stu-id="0c33b-129">Home scale</span></span>

<span data-ttu-id="0c33b-130">3D 應用程式啟動器 live Cliff 屋裡，其預設大小應該意義與其他 「 實體 」 物件空間中。</span><span class="sxs-lookup"><span data-stu-id="0c33b-130">3D app launchers live in the Cliff House and their default size should make sense with the other “physical” objects in the space.</span></span> <span data-ttu-id="0c33b-131">如果您將您的啟動器，說，一家工廠或某些 furniture，應該會覺得在家裡、 size-wise。</span><span class="sxs-lookup"><span data-stu-id="0c33b-131">If you place your launcher beside, say, a house plant or some furniture, it should feel at home, size-wise.</span></span> <span data-ttu-id="0c33b-132">若要查看其外觀在 30 三次方公分為單位，但請記住，使用者可以相應增加或相應減少是否他們想，是不錯的起點。</span><span class="sxs-lookup"><span data-stu-id="0c33b-132">A good starting point is to see how it looks at 30 cubic centimeters, but remember that users can scale it up or down if they like.</span></span>

### <a name="own-able"></a><span data-ttu-id="0c33b-133">可擁有的</span><span class="sxs-lookup"><span data-stu-id="0c33b-133">Own-able</span></span>

<span data-ttu-id="0c33b-134">應用程式啟動程式應該感覺個人會也很高興在其空間中的物件。</span><span class="sxs-lookup"><span data-stu-id="0c33b-134">The app launcher should feel like an object a person would be excited to have in their space.</span></span> <span data-ttu-id="0c33b-135">他們將能幾乎周圍本身與這些項目，讓啟動器應該覺得喜歡使用者思考是想要找出並保留附近。</span><span class="sxs-lookup"><span data-stu-id="0c33b-135">They’ll be virtually surrounding themselves with these things, so the launcher should feel like something the user thought was desirable enough to seek out and keep nearby.</span></span>

<span data-ttu-id="0c33b-136">![範例：Astro Warp 3D 應用程式啟動器](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="0c33b-136">![Example: Astro Warp 3D app launcher](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="0c33b-137">*Astro Warp 3D 應用程式啟動器範例 （虛構應用程式）*</span><span class="sxs-lookup"><span data-stu-id="0c33b-137">*Astro Warp 3D app launcher example (fictional app)*</span></span>

### <a name="recognizable"></a><span data-ttu-id="0c33b-138">可辨識</span><span class="sxs-lookup"><span data-stu-id="0c33b-138">Recognizable</span></span>

<span data-ttu-id="0c33b-139">您的 3D 應用程式啟動程式應該立即 express 人看到 」 您的應用程式的品牌 」。</span><span class="sxs-lookup"><span data-stu-id="0c33b-139">Your 3D app launcher should instantly express “your app’s brand” to people who see it.</span></span> <span data-ttu-id="0c33b-140">如果您有星號字元或特別識別的物件在您的應用程式中，我們建議使用其做為您的設計的很大一部份。</span><span class="sxs-lookup"><span data-stu-id="0c33b-140">If you have a star character or an especially identifiable object in your app, we recommend using that as a big part of your design.</span></span> <span data-ttu-id="0c33b-141">在混合的實境世界中，物件會比只單獨商標的使用者從連往更有意思。</span><span class="sxs-lookup"><span data-stu-id="0c33b-141">In a mixed reality world, an object will draw more interest from users than just a logo alone.</span></span> <span data-ttu-id="0c33b-142">可辨識物件通訊的品牌，快速且清楚地。</span><span class="sxs-lookup"><span data-stu-id="0c33b-142">Recognizable objects communicate brand quickly and clearly.</span></span>

### <a name="volumetric"></a><span data-ttu-id="0c33b-143">體積型</span><span class="sxs-lookup"><span data-stu-id="0c33b-143">Volumetric</span></span>

<span data-ttu-id="0c33b-144">您的應用程式值得使用更不只是一般的平面上放置您的標誌和呼叫一天。</span><span class="sxs-lookup"><span data-stu-id="0c33b-144">Your app deserves more than just putting your logo on a flat plane and calling it a day.</span></span> <span data-ttu-id="0c33b-145">您的啟動程式應該感覺上是令人興奮、 3D、 實體的物件，在使用者的空間中。</span><span class="sxs-lookup"><span data-stu-id="0c33b-145">Your launcher should feel like an exciting, 3D, physical object in the user’s space.</span></span> <span data-ttu-id="0c33b-146">是不錯的方法是假設您的應用程式即將要 Macy 感恩節天行列中有一個球形文字說明。</span><span class="sxs-lookup"><span data-stu-id="0c33b-146">A good approach is to imagine your app was going to have a balloon in the Macy’s Thanksgiving Day Parade.</span></span> <span data-ttu-id="0c33b-147">問問自己，什麼會真的讚嘆的人員為其來源巷口？</span><span class="sxs-lookup"><span data-stu-id="0c33b-147">Ask yourself, what would really wow people as it came down the street?</span></span> <span data-ttu-id="0c33b-148">項目看起來很棒從頭到尾檢視？</span><span class="sxs-lookup"><span data-stu-id="0c33b-148">What would look great from all viewing angles?</span></span>


:::row:::
    :::column:::
        ![Logo only](images/20171016-140436-mixedreality-640px.jpg)
        *Logo only*
    :::column-end:::
    :::column:::
        ![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg)
        *More recognizable with a character*
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
        ![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg)
        *Flat approach, not surprisingly, feels flat*
    :::column-end:::
    :::column:::
        ![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg)
        *Volumetric approach better showcases your app*
    :::column-end:::
:::row-end:::


## <a name="tips-for-good-3d-models"></a><span data-ttu-id="0c33b-149">良好的 3D 模型的秘訣</span><span class="sxs-lookup"><span data-stu-id="0c33b-149">Tips for good 3D models</span></span>

### <a name="best-practices"></a><span data-ttu-id="0c33b-150">最佳作法</span><span class="sxs-lookup"><span data-stu-id="0c33b-150">Best practices</span></span>
* <span data-ttu-id="0c33b-151">在規劃您的應用程式啟動器的維度，限定大約 30 cm cube。</span><span class="sxs-lookup"><span data-stu-id="0c33b-151">When planning dimensions for your app launcher, shoot for roughly a 30cm cube.</span></span> <span data-ttu-id="0c33b-152">因此，1:1:1 大小比率。</span><span class="sxs-lookup"><span data-stu-id="0c33b-152">So, a 1:1:1 size ratio.</span></span>
* <span data-ttu-id="0c33b-153">模型必須是 10000 的多邊形。</span><span class="sxs-lookup"><span data-stu-id="0c33b-153">Models must be under 10,000 polygons.</span></span> [<span data-ttu-id="0c33b-154">深入了解三角形計數和層級的詳細資料 (LODs)</span><span class="sxs-lookup"><span data-stu-id="0c33b-154">Learn more about triangle counts and levels of details (LODs)</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* <span data-ttu-id="0c33b-155">在盡可能沈浸式耳機上進行測試。</span><span class="sxs-lookup"><span data-stu-id="0c33b-155">Test on an immersive headset when possible.</span></span>
* <span data-ttu-id="0c33b-156">建置到您的模型幾何詳細資料，盡可能 – 不要依賴紋理的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="0c33b-156">Build details into your model’s geometry where possible – don’t rely on textures for detail.</span></span>
* <span data-ttu-id="0c33b-157">建置"water 緊密 」 關閉幾何。</span><span class="sxs-lookup"><span data-stu-id="0c33b-157">Build “water tight” closed geometry.</span></span> <span data-ttu-id="0c33b-158">未設定模型中沒有安全漏洞。</span><span class="sxs-lookup"><span data-stu-id="0c33b-158">No holes that are not modeled in.</span></span>
* <span data-ttu-id="0c33b-159">使用自然的資料物件中。</span><span class="sxs-lookup"><span data-stu-id="0c33b-159">Use natural materials in your object.</span></span> <span data-ttu-id="0c33b-160">想像一下製作真實世界中。</span><span class="sxs-lookup"><span data-stu-id="0c33b-160">Imagine crafting it in the real world.</span></span>
* <span data-ttu-id="0c33b-161">請確定您的模型讀取也在不同距離和大小。</span><span class="sxs-lookup"><span data-stu-id="0c33b-161">Make sure your model reads well at different distances and sizes.</span></span>
* <span data-ttu-id="0c33b-162">準備好您的模型時，讀取[匯出資產指導方針](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview)。</span><span class="sxs-lookup"><span data-stu-id="0c33b-162">When your model is ready to go, read the [exporting assets guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span></span>

<span data-ttu-id="0c33b-163">![微妙的細節，材質中的模型](images/20171013-143334-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="0c33b-163">![Model with subtle details in the texture](images/20171013-143334-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="0c33b-164">*微妙的細節，材質中的模型*</span><span class="sxs-lookup"><span data-stu-id="0c33b-164">*Model with subtle details in the texture*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="0c33b-165">要避免的事項</span><span class="sxs-lookup"><span data-stu-id="0c33b-165">What to avoid</span></span>
* <span data-ttu-id="0c33b-166">請勿使用高對比詳細資料或小型的忙線中的模式和紋理。</span><span class="sxs-lookup"><span data-stu-id="0c33b-166">Don't use high-contrast details or small, busy patterns and textures.</span></span>
* <span data-ttu-id="0c33b-167">請勿使用精簡型的幾何 – 不運作也在距離，並將別名格式錯誤。</span><span class="sxs-lookup"><span data-stu-id="0c33b-167">Don't use thin geometry – it doesn’t work well at a distance and will alias badly.</span></span>
* <span data-ttu-id="0c33b-168">不要讓擴充您的模型部分太多超過 1:1:1 大小比率。</span><span class="sxs-lookup"><span data-stu-id="0c33b-168">Don't let parts of your model extend too much beyond the 1:1:1 size ratio.</span></span> <span data-ttu-id="0c33b-169">它會建立縮放問題。</span><span class="sxs-lookup"><span data-stu-id="0c33b-169">It will create scaling problems.</span></span>

<span data-ttu-id="0c33b-170">![避免高對比 」、 「 小忙線中的模式](images/20171013-143603-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="0c33b-170">![Avoid high-contrast, small busy patterns](images/20171013-143603-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="0c33b-171">*避免高對比、 小型、 忙碌中的模式*</span><span class="sxs-lookup"><span data-stu-id="0c33b-171">*Avoid high-contrast, small, busy patterns*</span></span>

## <a name="how-to-handle-type"></a><span data-ttu-id="0c33b-172">如何控制代碼類型</span><span class="sxs-lookup"><span data-stu-id="0c33b-172">How to handle type</span></span>

### <a name="best-practices"></a><span data-ttu-id="0c33b-173">最佳作法</span><span class="sxs-lookup"><span data-stu-id="0c33b-173">Best practices</span></span>
* <span data-ttu-id="0c33b-174">我們建議您的型別包含大約 1/3 的應用程式啟動器 （或以上）。</span><span class="sxs-lookup"><span data-stu-id="0c33b-174">We recommend your type comprises about 1/3 of your app launcher (or more).</span></span> <span data-ttu-id="0c33b-175">類型為重點，讓人們可以您啟動器的是，事實上，啟動器，因此如果是很重大很不錯的主意。</span><span class="sxs-lookup"><span data-stu-id="0c33b-175">Type is the main thing that gives people an idea that your launcher is, in fact, a launcher so it’s nice if it’s pretty substantial.</span></span>
* <span data-ttu-id="0c33b-176">避免進行非常廣泛的型別，請盡量保持它的應用程式啟動器的範圍內 core 維度 （增加或減少）。</span><span class="sxs-lookup"><span data-stu-id="0c33b-176">Avoid making type super wide – try to keep it within the confines of the app launchers core dimensions (more or less).</span></span>
* <span data-ttu-id="0c33b-177">一般型別可以運作，但請注意，它很難檢視從某些角度和在某些環境中。</span><span class="sxs-lookup"><span data-stu-id="0c33b-177">Flat type can work, but be aware that it can be hard to view from certain angles and in certain environments.</span></span> <span data-ttu-id="0c33b-178">您可以考慮將它置於實體物件或其可協助完成這背後的背景。</span><span class="sxs-lookup"><span data-stu-id="0c33b-178">You might consider putting it a solid object or backdrop behind it to help with this.</span></span>
* <span data-ttu-id="0c33b-179">新增維度，以便您的型別覺得不錯 3D 中。</span><span class="sxs-lookup"><span data-stu-id="0c33b-179">Adding dimension to your type feels nice in 3D.</span></span> <span data-ttu-id="0c33b-180">陰影的類型不同，較深的色彩可以降低了可讀性。</span><span class="sxs-lookup"><span data-stu-id="0c33b-180">Shading the sides of the type a different, darker color can help with readability.</span></span>


:::row:::
    :::column:::
        ![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png)
        *Flat type without a backdrop can be hard to view from certain angles and in certain environments*
    :::column-end:::
    :::column:::
        ![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png)
        *Type with a built-in backdrop can work well*
    :::column-end:::
    :::column:::
        ![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg)
        *Extruded type can work well if you shade the sides*
    :::column-end:::
:::row-end:::


<span data-ttu-id="0c33b-181">**工作的類型色彩**</span><span class="sxs-lookup"><span data-stu-id="0c33b-181">**Type colors that work**</span></span>
* <span data-ttu-id="0c33b-182">白皮書</span><span class="sxs-lookup"><span data-stu-id="0c33b-182">White</span></span>
* <span data-ttu-id="0c33b-183">黑色</span><span class="sxs-lookup"><span data-stu-id="0c33b-183">Black</span></span>
* <span data-ttu-id="0c33b-184">亮半飽和的色彩</span><span class="sxs-lookup"><span data-stu-id="0c33b-184">Bright semi-saturated color</span></span>

<span data-ttu-id="0c33b-185">![工作的類型色彩。](images/20171016-112111-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="0c33b-185">![Type colors that work.](images/20171016-112111-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="0c33b-186">*工作的類型色彩*</span><span class="sxs-lookup"><span data-stu-id="0c33b-186">*Type colors that work*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="0c33b-187">要避免的事項</span><span class="sxs-lookup"><span data-stu-id="0c33b-187">What to avoid</span></span>

<span data-ttu-id="0c33b-188">**造成麻煩的類型色彩**</span><span class="sxs-lookup"><span data-stu-id="0c33b-188">**Type colors that cause trouble**</span></span>
* <span data-ttu-id="0c33b-189">Mid 撥號音</span><span class="sxs-lookup"><span data-stu-id="0c33b-189">Mid-tones</span></span>
* <span data-ttu-id="0c33b-190">灰色</span><span class="sxs-lookup"><span data-stu-id="0c33b-190">Gray</span></span>
* <span data-ttu-id="0c33b-191">過度飽和的色彩或已去色的色彩</span><span class="sxs-lookup"><span data-stu-id="0c33b-191">Over-saturated colors or desaturated colors</span></span>

<span data-ttu-id="0c33b-192">![輸入造成麻煩的色彩。](images/20171016-112246-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="0c33b-192">![Type colors that cause trouble.](images/20171016-112246-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="0c33b-193">*造成麻煩的類型色彩*</span><span class="sxs-lookup"><span data-stu-id="0c33b-193">*Type colors that cause trouble*</span></span>

## <a name="lighting"></a><span data-ttu-id="0c33b-194">光源</span><span class="sxs-lookup"><span data-stu-id="0c33b-194">Lighting</span></span>

<span data-ttu-id="0c33b-195">您的應用程式啟動器的光源來自 Cliff 房屋環境。</span><span class="sxs-lookup"><span data-stu-id="0c33b-195">The lighting for your app launcher comes from the Cliff House environment.</span></span> <span data-ttu-id="0c33b-196">請務必測試您的啟動程式在整個房子的幾個地方，讓它看起來沒問題中光線和陰影。</span><span class="sxs-lookup"><span data-stu-id="0c33b-196">Be sure to test your launcher in several places throughout the house so it looks good in both light and shadows.</span></span> <span data-ttu-id="0c33b-197">好消息是，如果您照著本文件中的其他設計指導方針，您的啟動程式應該相當良好 Cliff 屋裡大多數的光源。</span><span class="sxs-lookup"><span data-stu-id="0c33b-197">The good news is, if you’ve followed the other design guidance in this document, your launcher should be in pretty good shape for most lighting in the Cliff House.</span></span>

<span data-ttu-id="0c33b-198">若要測試您程式啟動器中環境中的各種燈的外觀良好是 Studio 媒體的空間，和上一步 」 高台 （使用草坪具體的區域） 上任何位置外。</span><span class="sxs-lookup"><span data-stu-id="0c33b-198">Good places to test how your launcher looks in the various lights in the environment are the Studio, the Media Room, anywhere outside and on the Back Patio (the concrete area with the lawn).</span></span> <span data-ttu-id="0c33b-199">另一個很好的測試，就是將它放在一半的光線和一半的陰影，並看看它的外觀。</span><span class="sxs-lookup"><span data-stu-id="0c33b-199">Another good test is to put it in half light and half shadow and see what it looks like.</span></span>

<span data-ttu-id="0c33b-200">![請確定您的啟動程式看起來不錯中光線和陰影。](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="0c33b-200">![Make sure your launcher looks good in both light and shadows.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="0c33b-201">*請確定您的啟動程式看起來不錯中光線和陰影*</span><span class="sxs-lookup"><span data-stu-id="0c33b-201">*Make sure your launcher looks good in both light and shadows*</span></span>

## <a name="texturing"></a><span data-ttu-id="0c33b-202">材質</span><span class="sxs-lookup"><span data-stu-id="0c33b-202">Texturing</span></span>

### <a name="authoring-your-textures"></a><span data-ttu-id="0c33b-203">撰寫您的紋理</span><span class="sxs-lookup"><span data-stu-id="0c33b-203">Authoring your textures</span></span>

<span data-ttu-id="0c33b-204">您的 3D 應用程式啟動器的結束格式會.glb 檔案，會使用 PBR （實際基礎轉譯） 管線。</span><span class="sxs-lookup"><span data-stu-id="0c33b-204">The end format of your 3D app launcher will be a .glb file, which is made using the PBR (Physically Based Rendering) pipeline.</span></span> <span data-ttu-id="0c33b-205">這可以是複雜的程序-現在是採用技術的演出者，如果您還沒有這麼做的好時機。</span><span class="sxs-lookup"><span data-stu-id="0c33b-205">This can be a tricky process - now is a good time to employ a technical artist if you haven't already.</span></span> <span data-ttu-id="0c33b-206">如果您是勇敢 DIY-呃，花時間[研究，了解 PBR 術語](http://wiki.polycount.com/wiki/PBR)事情實際上在您開始前，將可協助您避免常見的錯誤。</span><span class="sxs-lookup"><span data-stu-id="0c33b-206">If you’re a brave DIY-er, taking the time to [research and learn PBR terminology](http://wiki.polycount.com/wiki/PBR) and what’s happening under the hood before you begin will help you avoid common mistakes.</span></span> 

<span data-ttu-id="0c33b-207">![範例：全新的注意應用程式](images/pbr-freshnote1-640px-500px.png)</span><span class="sxs-lookup"><span data-stu-id="0c33b-207">![Example: Fresh Note app](images/pbr-freshnote1-640px-500px.png)</span></span><br>
<span data-ttu-id="0c33b-208">*全新的附註 3D 應用程式啟動器範例 （虛構應用程式）*</span><span class="sxs-lookup"><span data-stu-id="0c33b-208">*Fresh Note 3D app launcher example (fictional app)*</span></span>

<span data-ttu-id="0c33b-209">**建議撰寫工具**</span><span class="sxs-lookup"><span data-stu-id="0c33b-209">**Recommended authoring tool**</span></span>

<span data-ttu-id="0c33b-210">我們建議您使用[物質複製](https://www.allegorithmic.com/products/substance-painter)由 Allegorithmic 來撰寫您的最後一個檔案。</span><span class="sxs-lookup"><span data-stu-id="0c33b-210">We recommend using [Substance Painter](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic to author your final file.</span></span> <span data-ttu-id="0c33b-211">如果您不熟悉撰寫在物質複製，這裡的 PBR 著色器[教學課程](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials)。</span><span class="sxs-lookup"><span data-stu-id="0c33b-211">If you’re not familiar with authoring PBR shaders in Substance Painter, here’s a [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span></span>

<span data-ttu-id="0c33b-212">(或者[3D Coat](https://3dcoat.com/home/)， [Quixel Suite 2](https://quixel.se/suite2/)，或[Marmoset Toolbag](https://www.marmoset.co/toolbag/)只有當您更熟悉其中一種，也可以運作。)</span><span class="sxs-lookup"><span data-stu-id="0c33b-212">(Alternately [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), or [Marmoset Toolbag](https://www.marmoset.co/toolbag/) would also work if you’re more familiar with one of these.)</span></span>

### <a name="best-practices"></a><span data-ttu-id="0c33b-213">最佳作法</span><span class="sxs-lookup"><span data-stu-id="0c33b-213">Best practices</span></span>

* <span data-ttu-id="0c33b-214">如果您的應用程式啟動程式物件所撰寫的 PBR，它應該是將它轉換為 Cliff 房屋環境很簡單。</span><span class="sxs-lookup"><span data-stu-id="0c33b-214">If your app launcher object was authored for PBR, it should be pretty straightforward to convert it for the Cliff House environment.</span></span>
* <span data-ttu-id="0c33b-215">我們的著色器所預期的 Metal/粗糙度工作流程 – Unreal PBR 著色器是關閉的傳真。</span><span class="sxs-lookup"><span data-stu-id="0c33b-215">Our shader is expecting a Metal/Roughness work flow – The Unreal PBR shader is a close facsimile.</span></span>
* <span data-ttu-id="0c33b-216">當匯出您的紋理保持[建議的紋理大小](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines)記住。</span><span class="sxs-lookup"><span data-stu-id="0c33b-216">When exporting your textures keep the [recommended texture sizes](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) in mind.</span></span>
* <span data-ttu-id="0c33b-217">務必先建置您即時的光線的物件，這表示：</span><span class="sxs-lookup"><span data-stu-id="0c33b-217">Make sure to build your objects for real-time lighting — this means:</span></span>
    * <span data-ttu-id="0c33b-218">避免烤的 shadows – 或繪製的陰影</span><span class="sxs-lookup"><span data-stu-id="0c33b-218">Avoid baked shadows – or painted shadows</span></span>
    * <span data-ttu-id="0c33b-219">避免烤的光源的紋理中</span><span class="sxs-lookup"><span data-stu-id="0c33b-219">Avoid baked lighting in the textures</span></span>
    * <span data-ttu-id="0c33b-220">使用其中一種撰寫套件 PBR 資料以取得正確的對應產生我們的著色器</span><span class="sxs-lookup"><span data-stu-id="0c33b-220">Use one of the PBR material authoring packages to get the right maps generated for our shader</span></span>

## <a name="see-also"></a><span data-ttu-id="0c33b-221">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c33b-221">See also</span></span>

* [<span data-ttu-id="0c33b-222">在首頁的混合實境中建立使用 3D 模型</span><span class="sxs-lookup"><span data-stu-id="0c33b-222">Create 3D models for use in the mixed reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="0c33b-223">實作 3D 應用程式啟動器 (UWP app)</span><span class="sxs-lookup"><span data-stu-id="0c33b-223">Implement 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="0c33b-224">實作 3D 應用程式啟動器 （Win32 應用程式）</span><span class="sxs-lookup"><span data-stu-id="0c33b-224">Implement 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
