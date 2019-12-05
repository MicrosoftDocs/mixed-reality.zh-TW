---
title: 色彩、光線和材質
description: 設計混合實境的內容時，必須仔細考慮您體驗中所使用的每個視覺資產的色彩、光源和材質。
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，設計，色彩，光線，材質
ms.openlocfilehash: b29fe8da92e67d15592f9d4503bc278d4fe9fd95
ms.sourcegitcommit: 05fa75193059a2dac4b580a9eef7b6c4bb64d8d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74835084"
---
# <a name="color-light-and-materials"></a><span data-ttu-id="59cf9-104">色彩、光線和材質</span><span class="sxs-lookup"><span data-stu-id="59cf9-104">Color, light and materials</span></span>

<span data-ttu-id="59cf9-105">設計混合實境的內容時，必須仔細考慮您體驗中所使用的每個視覺資產的色彩、光源和材質。</span><span class="sxs-lookup"><span data-stu-id="59cf9-105">Designing content for mixed reality requires careful consideration of color, lighting, and materials for each of the visual assets used in your experience.</span></span> <span data-ttu-id="59cf9-106">這些決策可用於美觀用途，例如使用光線和材質來設定沉浸式環境的色調，以及功能的用途，例如使用驚人的色彩來警示使用者即將採取的動作。</span><span class="sxs-lookup"><span data-stu-id="59cf9-106">These decisions can be for both aesthetic purposes, like using light and material to set the tone of an immersive environment, and functional purposes, like using striking colors to alert users of an impending action.</span></span> <span data-ttu-id="59cf9-107">每個決策都必須針對經驗目標裝置的機會和限制進行權衡。</span><span class="sxs-lookup"><span data-stu-id="59cf9-107">Each of these decisions must be weighed against the opportunities and constraints of your experience’s target device.</span></span>

<span data-ttu-id="59cf9-108">以下是在沉浸式和全像耳機上轉譯資產的特定指導方針。</span><span class="sxs-lookup"><span data-stu-id="59cf9-108">Below are guidelines specific to rendering assets on both immersive and holographic headsets.</span></span> <span data-ttu-id="59cf9-109">其中有許多是與其他技術領域緊密相關，而且有一份相關主題清單可以在本文結尾的 [[另請參閱](color,-light-and-materials.md#see-also)] 一節中找到。</span><span class="sxs-lookup"><span data-stu-id="59cf9-109">Many of these are closely tied to other technical areas and a list of related subjects can be found in the [See also](color,-light-and-materials.md#see-also) section at the end of this article.</span></span>

## <a name="rendering-on-immersive-vs-holographic-devices"></a><span data-ttu-id="59cf9-110">在沉浸式與全像攝影裝置上呈現</span><span class="sxs-lookup"><span data-stu-id="59cf9-110">Rendering on immersive vs. holographic devices</span></span>

<span data-ttu-id="59cf9-111">與全像攝影耳機中轉譯的內容相比，以沉浸式耳機轉譯的內容會以視覺化方式呈現。</span><span class="sxs-lookup"><span data-stu-id="59cf9-111">Content rendered in immersive headsets will appear visually different when compared to content rendered in holographic headsets.</span></span> <span data-ttu-id="59cf9-112">雖然沉浸式耳機通常會以2D 螢幕上的預期來轉譯內容，但 HoloLens 這類的全像攝影耳機會使用色彩順序，請參閱以 RGB 顯示呈現全息影像。</span><span class="sxs-lookup"><span data-stu-id="59cf9-112">While immersive headsets generally render content much as you would expect on a 2D screen, holographic headsets like HoloLens use color-sequential, see-through RGB displays to renders holograms.</span></span>

<span data-ttu-id="59cf9-113">總是花時間在全像耳機中測試您的全像攝影體驗。</span><span class="sxs-lookup"><span data-stu-id="59cf9-113">Always take time to test your holographic experiences in a holographic headset.</span></span> <span data-ttu-id="59cf9-114">內容的外觀（即使是專為全像攝影裝置所建立），在次要監視器、快照和 spectator view 中的顯示方式會有所不同。</span><span class="sxs-lookup"><span data-stu-id="59cf9-114">The appearance of content, even if it is built specifically for holographic devices, will differ as seen on secondary monitors, snapshots, and in spectator view.</span></span> <span data-ttu-id="59cf9-115">別忘了使用裝置的經驗、測試全息影像的光線，以及從所有邊（以及從上方和下方）觀察內容的呈現方式。</span><span class="sxs-lookup"><span data-stu-id="59cf9-115">Remember to walk around experiences with a device, testing the lighting of holograms and observing from all sides (as well as from above and below) how your content is rendered.</span></span> <span data-ttu-id="59cf9-116">請務必在裝置上的亮度設定範圍進行測試，因為不太可能所有的使用者都會共用假設的預設值，以及一組不同的光源條件。</span><span class="sxs-lookup"><span data-stu-id="59cf9-116">Be sure to test at a range of brightness settings on the device, as it is unlikely all users will share an assumed default, as well as a diverse set of lighting conditions.</span></span>

## <a name="fundamentals-of-rendering-on-holographic-devices"></a><span data-ttu-id="59cf9-117">在全像攝影裝置上呈現的基本概念</span><span class="sxs-lookup"><span data-stu-id="59cf9-117">Fundamentals of rendering on holographic devices</span></span>
* <span data-ttu-id="59cf9-118">全像攝影**裝置具有 [加法] 顯示器**–從真實世界將光線新增到光線來建立全像投影，白色會顯示為明亮，而黑色則會透明。</span><span class="sxs-lookup"><span data-stu-id="59cf9-118">**Holographic devices have additive displays** – Holograms are created by adding light to the light from the real world – white will appear brightly, while black will appear transparent.</span></span>
* <span data-ttu-id="59cf9-119">**色彩影響會因使用者的環境而異**–使用者的房間內有許多不同的光源狀況。</span><span class="sxs-lookup"><span data-stu-id="59cf9-119">**Colors impact varies with the user’s environment** – There are many diverse lighting conditions in a user’s room.</span></span> <span data-ttu-id="59cf9-120">建立具有適當對比層級的內容，以利清楚地協助。</span><span class="sxs-lookup"><span data-stu-id="59cf9-120">Create content with appropriate levels of contrast to help with clarity.</span></span>
* <span data-ttu-id="59cf9-121">**避免動態光源**–全像全像攝影的全像攝影，最有效率。</span><span class="sxs-lookup"><span data-stu-id="59cf9-121">**Avoid dynamic lighting** – Holograms that are uniformly lit in holographic experiences are the most efficient.</span></span> <span data-ttu-id="59cf9-122">使用 advanced、dynamic 光源可能會超過行動裝置的功能。</span><span class="sxs-lookup"><span data-stu-id="59cf9-122">Using advanced, dynamic lighting will likely exceed the capabilities of mobile devices.</span></span> <span data-ttu-id="59cf9-123">需要動態光源時，建議使用[混合現實工具組標準著色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md)。</span><span class="sxs-lookup"><span data-stu-id="59cf9-123">When dynamic lighting is required, it is recommended to use the [Mixed Reality Toolkit Standard shader](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md).</span></span> 

## <a name="designing-with-color"></a><span data-ttu-id="59cf9-124">使用色彩進行設計</span><span class="sxs-lookup"><span data-stu-id="59cf9-124">Designing with color</span></span>

<span data-ttu-id="59cf9-125">由於加總顯示的本質，某些色彩在全像攝影顯示器上可能會有所不同。</span><span class="sxs-lookup"><span data-stu-id="59cf9-125">Due to the nature of additive displays, certain colors can appear different on holographic displays.</span></span> <span data-ttu-id="59cf9-126">有些色彩會在光源環境中彈出，有些則會顯示為較不影響力。</span><span class="sxs-lookup"><span data-stu-id="59cf9-126">Some colors will pop in lighting environments while others will appear as less impactful.</span></span> <span data-ttu-id="59cf9-127">酷炫色彩通常會 recede 到背景，而暖色彩會跳至前景。</span><span class="sxs-lookup"><span data-stu-id="59cf9-127">Cool colors tend to recede into the background while warm colors jump to the foreground.</span></span> <span data-ttu-id="59cf9-128">當您探索體驗的色彩時，請考慮下列因素：</span><span class="sxs-lookup"><span data-stu-id="59cf9-128">Consider these factors as you explore color in your experiences:</span></span>
* <span data-ttu-id="59cf9-129">**色域**-HoloLens 從「寬範圍」的色彩中獲益，概念上類似于 Adobe RGB。</span><span class="sxs-lookup"><span data-stu-id="59cf9-129">**Gamut** - HoloLens benefits from a "wide gamut" of color, conceptually similar to Adobe RGB.</span></span> <span data-ttu-id="59cf9-130">因此，某些色彩可能會在裝置中呈現不同的品質和標記法。</span><span class="sxs-lookup"><span data-stu-id="59cf9-130">As a result, some colors can exhibit different qualities and representation in the device.</span></span>
* <span data-ttu-id="59cf9-131">**Gamma** -呈現影像的亮度和對比會因沉浸式和全像攝影裝置而異。</span><span class="sxs-lookup"><span data-stu-id="59cf9-131">**Gamma** - The brightness and contrast of the rendered image will vary between immersive and holographic devices.</span></span> <span data-ttu-id="59cf9-132">這些裝置的差異通常會顯示色彩和陰影的深色區域、更多或較不明亮。</span><span class="sxs-lookup"><span data-stu-id="59cf9-132">These device differences often appear to make dark areas of color and shadows, more or less bright.</span></span>
* <span data-ttu-id="59cf9-133">**色彩分隔**-也稱為 "color 並劃分" 或 "color fringing"，當使用者以眼睛追蹤物件時，移動全息影像（包括游標）最常發生的色彩區分。</span><span class="sxs-lookup"><span data-stu-id="59cf9-133">**Color separation** - Also called "color breakup" or "color fringing", color separation most commonly occurs with moving holograms (including cursor) when a user tracks objects with their eyes.</span></span>
* <span data-ttu-id="59cf9-134">**色彩一致性**-通常會將全像投影轉譯成明亮，使其維持色彩一致性（不論背景為何）。</span><span class="sxs-lookup"><span data-stu-id="59cf9-134">**Color uniformity** - Typically holograms are rendered brightly enough so that they maintain color uniformity, regardless of the background.</span></span> <span data-ttu-id="59cf9-135">大型區域可能會變得 blotchy。</span><span class="sxs-lookup"><span data-stu-id="59cf9-135">Large areas may become blotchy.</span></span> <span data-ttu-id="59cf9-136">避免出現明亮、純色的大型區域。</span><span class="sxs-lookup"><span data-stu-id="59cf9-136">Avoid large regions of bright, solid color.</span></span>
* <span data-ttu-id="59cf9-137">**呈現淺色**-白色外觀非常明亮，應謹慎使用。</span><span class="sxs-lookup"><span data-stu-id="59cf9-137">**Rendering light colors** - White appears very bright and should be used sparingly.</span></span> <span data-ttu-id="59cf9-138">在大部分情況下，請考慮使用與 R 235 G 235 B 235 有關的白色值。</span><span class="sxs-lookup"><span data-stu-id="59cf9-138">For most cases, consider a white value around R 235 G 235 B 235.</span></span> <span data-ttu-id="59cf9-139">較大的區域可能會造成使用者 discomfort。</span><span class="sxs-lookup"><span data-stu-id="59cf9-139">Large bright areas may cause user discomfort.</span></span>

<span data-ttu-id="59cf9-140">**呈現深色色彩**</span><span class="sxs-lookup"><span data-stu-id="59cf9-140">**Rendering dark colors**</span></span>

<span data-ttu-id="59cf9-141">由於加總顯示的本質，暗色調會顯示為透明。</span><span class="sxs-lookup"><span data-stu-id="59cf9-141">Due to the nature of additive displays, dark colors appear transparent.</span></span> <span data-ttu-id="59cf9-142">實心的黑色物件與真實世界的外觀並無不同。</span><span class="sxs-lookup"><span data-stu-id="59cf9-142">A solid black object will appear no different from the real world.</span></span> <span data-ttu-id="59cf9-143">請參閱下方的 Alpha 色板。</span><span class="sxs-lookup"><span data-stu-id="59cf9-143">See Alpha channel below.</span></span> <span data-ttu-id="59cf9-144">若要讓「黑色」的外觀嘗試使用非常深的灰階 RGB 值，例如16、16、16。</span><span class="sxs-lookup"><span data-stu-id="59cf9-144">To give the appearance of “black” try a very dark grey RGB value such as 16,16,16.</span></span>

<span data-ttu-id="59cf9-145">![一般與寬色色域](images/640px-widegamut.png)</span><span class="sxs-lookup"><span data-stu-id="59cf9-145">![Normal vs. wide color gamut](images/640px-widegamut.png)</span></span><br>
<span data-ttu-id="59cf9-146">*一般與寬色色域*</span><span class="sxs-lookup"><span data-stu-id="59cf9-146">*Normal vs. wide color gamut*</span></span>

## <a name="technical-considerations"></a><span data-ttu-id="59cf9-147">技術考慮</span><span class="sxs-lookup"><span data-stu-id="59cf9-147">Technical considerations</span></span>
* <span data-ttu-id="59cf9-148">**別名**-明智失真、不規則或「樓梯步驟」，其中全息圖形幾何的邊緣會符合真實世界。</span><span class="sxs-lookup"><span data-stu-id="59cf9-148">**Aliasing** - Be considerate of aliasing, jagged or “stair steps” where the edge of a hologram’s geometry meets the real world.</span></span> <span data-ttu-id="59cf9-149">使用具有高細節的材質可以 aggravate 此效果。</span><span class="sxs-lookup"><span data-stu-id="59cf9-149">Using textures with high detail can aggravate this effect.</span></span> <span data-ttu-id="59cf9-150">材質應該對應並啟用篩選。</span><span class="sxs-lookup"><span data-stu-id="59cf9-150">Textures should be mapped and filtering enabled.</span></span> <span data-ttu-id="59cf9-151">請考慮將全息影像的邊緣漸淡，或加入在物件周圍建立黑色邊緣框線的材質。</span><span class="sxs-lookup"><span data-stu-id="59cf9-151">Consider fading the edges of holograms or adding a texture that creates a black edge border around objects.</span></span> <span data-ttu-id="59cf9-152">盡可能避免精簡型幾何。</span><span class="sxs-lookup"><span data-stu-id="59cf9-152">Avoid thin geometry where possible.</span></span>
* <span data-ttu-id="59cf9-153">**Alpha**色板-您必須針對未轉譯全息影像的任何零件，清除您的 Alpha 色板以完全透明。</span><span class="sxs-lookup"><span data-stu-id="59cf9-153">**Alpha channel** - You must clear your alpha channel to fully transparent for any parts where you are not rendering a hologram.</span></span> <span data-ttu-id="59cf9-154">當您從裝置或使用 Spectator View 取得影像/影片時，將 Alpha 未定義的會導致視覺效果構件。</span><span class="sxs-lookup"><span data-stu-id="59cf9-154">Leaving the alpha undefined leads to visual artifacts when taking images/videos from the device or with Spectator View.</span></span>
* <span data-ttu-id="59cf9-155">**材質軟化**-由於光線是全像投影顯示器的加法，因此最好避免較大的明亮色彩，因為它們通常不會產生想要的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="59cf9-155">**Texture softening** - Since light is additive in holographic displays, it is best to avoid large regions of bright, solid color as they often do not produce the intended visual effect.</span></span>

## <a name="storytelling-with-light-and-color"></a><span data-ttu-id="59cf9-156">以光線和色彩故事行銷</span><span class="sxs-lookup"><span data-stu-id="59cf9-156">Storytelling with light and color</span></span>

<span data-ttu-id="59cf9-157">光線和色彩可協助讓您的全息影像在使用者的環境中以更自然的方式呈現，以及提供使用者的指引和協助。</span><span class="sxs-lookup"><span data-stu-id="59cf9-157">Light and color can help make your holograms appear more naturally in a user's environment as well as offer guidance and help for the user.</span></span> <span data-ttu-id="59cf9-158">對於全像攝影的體驗，請在探索光源和色彩時考慮下列因素：</span><span class="sxs-lookup"><span data-stu-id="59cf9-158">For holographic experiences, consider these factors as you explore lighting and color:</span></span>

:::row:::
    :::column:::
* <span data-ttu-id="59cf9-159">**Vignetting** -加深材質的「vignette」效果有助於將使用者的注意力放在視圖欄位的中央。</span><span class="sxs-lookup"><span data-stu-id="59cf9-159">**Vignetting** - A 'vignette' effect to darken materials can help focus the user's attention on the center of the field of view.</span></span> <span data-ttu-id="59cf9-160">此效果會從使用者的注視向量中，以一些半徑來去除全息的全像投影資料。</span><span class="sxs-lookup"><span data-stu-id="59cf9-160">This effect darkens the hologram's material at some radius from the user's gaze vector.</span></span> <span data-ttu-id="59cf9-161">請注意，當使用者的視圖從傾斜或 glancing 角度進行全息時，這也是有效的。</span><span class="sxs-lookup"><span data-stu-id="59cf9-161">Note that this is also effective when the user's views holograms from an oblique or glancing angle.</span></span><br>
* <span data-ttu-id="59cf9-162">**強調**-透過對比色彩、亮度和光源，將注意力吸引物件或互動點。</span><span class="sxs-lookup"><span data-stu-id="59cf9-162">**Emphasis** - Draw attention to objects or points of interaction by contrasting colors, brightness, and lighting.</span></span> <span data-ttu-id="59cf9-163">如需故事行銷中光源方法的詳細資訊，請參閱[圖元 Cinematography-電腦圖形的光源方法](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf)。</span><span class="sxs-lookup"><span data-stu-id="59cf9-163">For a more detailed look at lighting methods in storytelling, see [Pixel Cinematography - A Lighting Approach for Computer Graphics](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf).</span></span><br>
        <br>
        <span data-ttu-id="59cf9-164">*影像：使用色彩來顯示故事行銷元素的強調，此處顯示于[片段](https://www.microsoft.com/p/fragments/9nblggh5ggm8)的場景中。*</span><span class="sxs-lookup"><span data-stu-id="59cf9-164">*Image: Use of color to show emphasis for storytelling elements, shown here in a scene from [Fragments](https://www.microsoft.com/p/fragments/9nblggh5ggm8).*</span></span>
    :::column-end:::
        :::column:::
        ![使用色彩來顯示故事行銷元素的強調，此處顯示于片段的場景中。](images/640px-fragments.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="see-also"></a><span data-ttu-id="59cf9-166">請參閱</span><span class="sxs-lookup"><span data-stu-id="59cf9-166">See also</span></span>
* [<span data-ttu-id="59cf9-167">色彩分隔</span><span class="sxs-lookup"><span data-stu-id="59cf9-167">Color Separation</span></span>](hologram-stability.md#color-separation)
* [<span data-ttu-id="59cf9-168">全息</span><span class="sxs-lookup"><span data-stu-id="59cf9-168">Holograms</span></span>](hologram.md)
* [<span data-ttu-id="59cf9-169">Microsoft 設計語言-色彩</span><span class="sxs-lookup"><span data-stu-id="59cf9-169">Microsoft Design Language - color</span></span>](https://www.microsoft.com/design/color)
* [<span data-ttu-id="59cf9-170">通用 Windows 平臺色彩</span><span class="sxs-lookup"><span data-stu-id="59cf9-170">Universal Windows Platform - color</span></span>](https://docs.microsoft.com/windows/uwp/style/color)