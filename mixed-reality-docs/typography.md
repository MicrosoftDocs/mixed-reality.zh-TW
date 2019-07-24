---
title: 印刷樣式
description: 文字是在您的應用程式體驗中傳遞資訊的重要元素。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality, 設計, 風格, 字型, 印刷樣式, ui, ux
ms.openlocfilehash: cc8e25e9cd7ba41bed179328fe7198e935e65d76
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66830008"
---
# <a name="typography"></a><span data-ttu-id="a2fdc-104">印刷樣式</span><span class="sxs-lookup"><span data-stu-id="a2fdc-104">Typography</span></span>

<span data-ttu-id="a2fdc-105">文字是在您的應用程式體驗中傳遞資訊的重要元素。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-105">Text is an important element for delivering information in your app experience.</span></span> <span data-ttu-id="a2fdc-106">就像2D 螢幕上的印刷樣式一樣, 目標是要清楚易懂。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-106">Just like typography on 2D screens, the goal is to be clear and readable.</span></span> <span data-ttu-id="a2fdc-107">有了混合現實的三維層面, 就有機會以更大的方式來影響文字和整體使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-107">With the three-dimensional aspect of mixed reality, there is an opportunity to affect the text and the overall user experience in an even greater way.</span></span>

<span data-ttu-id="a2fdc-108">![HoloLens 中的印刷樣式範例](images/typography-cover.png)</span><span class="sxs-lookup"><span data-stu-id="a2fdc-108">![Typography example in HoloLens](images/typography-cover.png)</span></span><br>
<span data-ttu-id="a2fdc-109">*HoloLens 中的印刷樣式範例*</span><span class="sxs-lookup"><span data-stu-id="a2fdc-109">*Typography example in HoloLens*</span></span>

<span data-ttu-id="a2fdc-110">當我們談論3D 中的類型時, 通常會考慮體積型3D 文字。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-110">When we talk about type in 3D, we tend to think extruded, volumetric 3D text.</span></span> <span data-ttu-id="a2fdc-111">除了部分商標設計和一些其他有限的應用程式以外, 已延伸的文字通常會降低文字的可讀性。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-111">Except for some logotype designs and a few other limited applications, extruded text tends to degrade the readability of the text.</span></span> <span data-ttu-id="a2fdc-112">雖然我們是設計3D 的經驗, 但我們使用2D 做為型別, 因為它比較容易閱讀, 而且可讀性更高。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-112">Even though we are designing experiences for 3D, we use 2D for the type because it is more legible and easier to read.</span></span>

<span data-ttu-id="a2fdc-113">在 HoloLens 中, 型別是根據加總色彩系統, 使用淡入的影像來建立的。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-113">In HoloLens, type is constructed with holograms using light based on the additive color system.</span></span> <span data-ttu-id="a2fdc-114">就像其他的全息影像一樣, 您可以將 type 放在實際環境中, 而且可以從任何角度來觀察世界。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-114">Just like other holograms, type can be placed in the actual environment where it can be world locked and observed from any angle.</span></span> <span data-ttu-id="a2fdc-115">類型和環境之間的[視差](https://en.wikipedia.org/wiki/Parallax)效果也會增加體驗的深度。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-115">The [parallax](https://en.wikipedia.org/wiki/Parallax) effect between the type and the environment also adds depth to the experience.</span></span>

## <a name="typography-in-mixed-reality"></a><span data-ttu-id="a2fdc-116">混合現實中的印刷樣式</span><span class="sxs-lookup"><span data-stu-id="a2fdc-116">Typography in mixed reality</span></span>

<span data-ttu-id="a2fdc-117">混合式現實中的印刷樣式規則與其他任何地方都沒有不同。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-117">Typographic rules in mixed reality are no different from anywhere else.</span></span> <span data-ttu-id="a2fdc-118">實體世界和虛擬世界中的文字都必須清晰易懂。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-118">Text in both the physical world and the virtual world needs to be legible and readable.</span></span> <span data-ttu-id="a2fdc-119">文字可以在牆上或疊加在實體物件上。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-119">Text could be on a wall or superimposed on a physical object.</span></span> <span data-ttu-id="a2fdc-120">它可以與數位使用者介面一併浮動。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-120">It could be floating along with a digital user interface.</span></span> <span data-ttu-id="a2fdc-121">無論內容為何, 我們會套用相同的印刷樣式規則來進行讀取和辨識。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-121">Regardless of the context, we apply the same typographic rules for reading and recognition.</span></span>

### <a name="create-clear-hierarchy"></a><span data-ttu-id="a2fdc-122">建立明確階層</span><span class="sxs-lookup"><span data-stu-id="a2fdc-122">Create clear hierarchy</span></span>

<span data-ttu-id="a2fdc-123">使用不同的類型大小和加權來建立對比和階層。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-123">Build contrast and hierarchy by using different type sizes and weights.</span></span> <span data-ttu-id="a2fdc-124">在整個應用程式體驗中定義型別斜坡並遵循它, 將會提供具有一致資訊階層的絕佳使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-124">Defining a type ramp and following it throughout the app experience will provide a great user experience with consistent information hierarchy.</span></span>

<span data-ttu-id="a2fdc-125">![輸入斜坡範例](images/typography-ramp-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="a2fdc-125">![Type ramp examples](images/typography-ramp-1000px.jpg)</span></span><br>
<span data-ttu-id="a2fdc-126">*定義您的型別斜坡, 並在整個應用程式體驗中追蹤*</span><span class="sxs-lookup"><span data-stu-id="a2fdc-126">*Define your type ramp and follow it throughout the app experience*</span></span>

### <a name="limit-your-fonts"></a><span data-ttu-id="a2fdc-127">限制字型</span><span class="sxs-lookup"><span data-stu-id="a2fdc-127">Limit your fonts</span></span>

<span data-ttu-id="a2fdc-128">避免在單一內容中使用兩個以上的不同字型系列。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-128">Avoid using more than two different font families in a single context.</span></span> <span data-ttu-id="a2fdc-129">這會破壞您的體驗的顏色和一致性, 並使取用資訊變得更困難。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-129">This will break the harmony and consistency of your experience and make it harder to consume information.</span></span> <span data-ttu-id="a2fdc-130">在 HoloLens 中, 由於資訊會重迭到實體環境的頂端, 因此使用太多字型樣式將會降低體驗。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-130">In HoloLens, since the information is overlaid on top of the physical environment, using too many font styles will degrade the experience.</span></span> <span data-ttu-id="a2fdc-131">Segoe UI 是所有 Microsoft 數位設計的字型。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-131">Segoe UI is the font for all Microsoft digital designs.</span></span> <span data-ttu-id="a2fdc-132">它在 Windows Mixed Reality shell 中是以一致的方式使用。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-132">It is used consistently in the Windows Mixed Reality shell.</span></span> <span data-ttu-id="a2fdc-133">您可以從[Windows 設計工具組頁面](https://docs.microsoft.com/windows/uwp/design-downloads/)下載 Segoe UI 字型檔案。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-133">You can download the Segoe UI font file from the [Windows design toolkit page](https://docs.microsoft.com/windows/uwp/design-downloads/).</span></span>

[<span data-ttu-id="a2fdc-134">Segoe UI 字樣的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="a2fdc-134">More information about the Segoe UI typeface</span></span>](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a><span data-ttu-id="a2fdc-135">避免精簡字型粗細</span><span class="sxs-lookup"><span data-stu-id="a2fdc-135">Avoid thin font weights</span></span>

<span data-ttu-id="a2fdc-136">請避免針對頁首建議42pt 下的類型大小使用 light 或 semilight 做字型粗細, 因為精簡的垂直筆劃將會震動並降低可讀性。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-136">Avoid using light or semilight font weights for type sizes under 42pt since thin vertical strokes will vibrate and degrade legibility.</span></span> <span data-ttu-id="a2fdc-137">具有足夠筆觸粗細的新式字型運作良好。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-137">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="a2fdc-138">例如, 在 HoloLens 中使用標準或粗權數時, Helvetica 和 Arial 會非常清晰。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-138">For example, Helvetica and Arial are very legible in HoloLens using regular or bold weights.</span></span>

### <a name="color"></a><span data-ttu-id="a2fdc-139">色彩</span><span class="sxs-lookup"><span data-stu-id="a2fdc-139">Color</span></span>

<span data-ttu-id="a2fdc-140">在 HoloLens 中, 因為全息影像是以加光源系統來建立, 所以白色文字會非常清晰。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-140">In HoloLens, since the holograms are constructed with an additive light system, white text is highly legible.</span></span> <span data-ttu-id="a2fdc-141">您可以在 [開始] 功能表和應用程式行上找到白色文字的範例。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-141">You can find examples of white text on the Start menu and the App bar.</span></span> <span data-ttu-id="a2fdc-142">即使在 HoloLens 上沒有背面的白色文字運作良好, 但是複雜的實體背景可能會使型別難以閱讀。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-142">Even though white text works well without a back plate on HoloLens, a complex physical background could make the type difficult to read.</span></span> <span data-ttu-id="a2fdc-143">若要改善使用者的焦點, 並將實體背景的干擾降到最低, 建議您在深色或彩色背景板上使用白色文字。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-143">To improve the user's focus and minimize the distraction from a physical background, we recommend using white text on a dark or colored back plate.</span></span>

<br>


<span data-ttu-id="a2fdc-144">![我們建議您在深色或彩色背景板上使用白色文字。*深色或彩色背板上的白色文字範例。* ](images/typography-whiteonblack2-1000px.jpg)
</span><span class="sxs-lookup"><span data-stu-id="a2fdc-144">![We recommend using white text on a dark or colored back plate.](images/typography-whiteonblack2-1000px.jpg)
*Examples of white text on a dark or colored back plate.*</span></span>
<br>

<span data-ttu-id="a2fdc-145">若要使用深色文字, 您應該使用明亮的背板讓它變成可讀取。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-145">To use dark text, you should use a bright back plate to make it readable.</span></span> <span data-ttu-id="a2fdc-146">在 [加法色彩系統] 中, 黑色會顯示為 [透明]。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-146">In additive color systems, black is displayed as transparent.</span></span> <span data-ttu-id="a2fdc-147">這表示您將無法在沒有彩色背景板的情況下看到黑色文字。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-147">This means you will not be able to see the black text without a colored back plate.</span></span>

<span data-ttu-id="a2fdc-148">![黑色文字範例](images/typography-whiteonblack.png)
</span><span class="sxs-lookup"><span data-stu-id="a2fdc-148">![Black text examples](images/typography-whiteonblack.png)
</span></span><br><span data-ttu-id="a2fdc-149">*白色文字的背面和黑色範例*</span><span class="sxs-lookup"><span data-stu-id="a2fdc-149">*Examples of white on back and black on white text*</span></span>


<span data-ttu-id="a2fdc-150">![黑色文字範例](images/640px-typography-blackonwhite.jpg)
</span><span class="sxs-lookup"><span data-stu-id="a2fdc-150">![Black text examples](images/640px-typography-blackonwhite.jpg)
</span></span><br><span data-ttu-id="a2fdc-151">*系統應用程式中的黑色文字範例-儲存和設定*</span><span class="sxs-lookup"><span data-stu-id="a2fdc-151">*Examples of black text in the system apps - Store and Settings*</span></span>

## <a name="recommended-font-size"></a><span data-ttu-id="a2fdc-152">建議的字型大小</span><span class="sxs-lookup"><span data-stu-id="a2fdc-152">Recommended font size</span></span>

<span data-ttu-id="a2fdc-153">如您所見, 我們在 PC 或 tablet 裝置上使用的大小 (通常介於12–32pt 填補之間) 看起來相當小, 距離2計量。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-153">As you can expect, type sizes that we use on a PC or a tablet device (typically between 12–32pt) look quite small at a distance of 2 meters.</span></span> <span data-ttu-id="a2fdc-154">這取決於每個字型的特性, 但一般來說, 建議的最小觀賞角度和可讀性的字型高度是以我們的使用者研究研究為基礎的0.35 °-0.4 °/12.21-13.97mm。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-154">It depends on the characteristics of each font, but in general the recommended minimum viewing angle and the font height for legibility are around 0.35°-0.4°/12.21-13.97mm based on our user research studies.</span></span> <span data-ttu-id="a2fdc-155">大約 35-40pt, 並在 Unity 頁面的[文字中](text-in-unity.md)引進縮放比例。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-155">It is about 35-40pt with the scaling factor introduced in [Text in Unity](text-in-unity.md) page.</span></span> 

<span data-ttu-id="a2fdc-156">若要在 0.45 m (45cm) 附近互動, 最小的可感知字型的視圖角度和高度是0.4 °-0.5 °/3.14 – 3.9 mm。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-156">For the near interaction at 0.45m(45cm), the minimum legible font's viewing angle and the height are 0.4°-0.5° / 3.14–3.9mm.</span></span> <span data-ttu-id="a2fdc-157">其大約是以 Unity 中的[文字](text-in-unity.md)引進的調整因數 9 12pt。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-157">It is about 9-12pt with the scaling factor introduced in [Text in Unity](text-in-unity.md).</span></span>

<span data-ttu-id="a2fdc-158">![近距離和遠處的](images/typography-distance-1000px.jpg)
互動範圍*內容*</span><span class="sxs-lookup"><span data-stu-id="a2fdc-158">![Near and far interaction range](images/typography-distance-1000px.jpg)
*Content at near and far interaction range*</span></span>

### <a name="the-minimum-legible-font-size"></a><span data-ttu-id="a2fdc-159">最小的清晰字型大小</span><span class="sxs-lookup"><span data-stu-id="a2fdc-159">The minimum legible font size</span></span>
| <span data-ttu-id="a2fdc-160">長途電話</span><span class="sxs-lookup"><span data-stu-id="a2fdc-160">Distance</span></span> | <span data-ttu-id="a2fdc-161">視角</span><span class="sxs-lookup"><span data-stu-id="a2fdc-161">Viewing angle</span></span> | <span data-ttu-id="a2fdc-162">文字高度</span><span class="sxs-lookup"><span data-stu-id="a2fdc-162">Text height</span></span> | <span data-ttu-id="a2fdc-163">字型大小 \* \*</span><span class="sxs-lookup"><span data-stu-id="a2fdc-163">Font size\*\*</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="a2fdc-164">45cm (直接操作距離)</span><span class="sxs-lookup"><span data-stu-id="a2fdc-164">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="a2fdc-165">0.4 °-0.5 °</span><span class="sxs-lookup"><span data-stu-id="a2fdc-165">0.4°-0.5°</span></span> | <span data-ttu-id="a2fdc-166">3.14 –3.9 毫米</span><span class="sxs-lookup"><span data-stu-id="a2fdc-166">3.14–3.9mm</span></span> | <span data-ttu-id="a2fdc-167">8.9 – 11.13 pt</span><span class="sxs-lookup"><span data-stu-id="a2fdc-167">8.9–11.13pt</span></span> |
| <span data-ttu-id="a2fdc-168">2m</span><span class="sxs-lookup"><span data-stu-id="a2fdc-168">2m</span></span> | <span data-ttu-id="a2fdc-169">0.35 °-0.4 °</span><span class="sxs-lookup"><span data-stu-id="a2fdc-169">0.35°-0.4°</span></span> | <span data-ttu-id="a2fdc-170">12.21 – 13.97 mm</span><span class="sxs-lookup"><span data-stu-id="a2fdc-170">12.21–13.97mm</span></span> | <span data-ttu-id="a2fdc-171">34.63-39.58 pt</span><span class="sxs-lookup"><span data-stu-id="a2fdc-171">34.63-39.58pt</span></span> |


### <a name="the-comfortably-legible-font-size"></a><span data-ttu-id="a2fdc-172">舒適的字型大小</span><span class="sxs-lookup"><span data-stu-id="a2fdc-172">The comfortably legible font size</span></span>
| <span data-ttu-id="a2fdc-173">長途電話</span><span class="sxs-lookup"><span data-stu-id="a2fdc-173">Distance</span></span> | <span data-ttu-id="a2fdc-174">視角</span><span class="sxs-lookup"><span data-stu-id="a2fdc-174">Viewing angle</span></span> | <span data-ttu-id="a2fdc-175">文字高度</span><span class="sxs-lookup"><span data-stu-id="a2fdc-175">Text height</span></span> | <span data-ttu-id="a2fdc-176">字型大小 \* \*</span><span class="sxs-lookup"><span data-stu-id="a2fdc-176">Font size\*\*</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="a2fdc-177">45cm (直接操作距離)</span><span class="sxs-lookup"><span data-stu-id="a2fdc-177">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="a2fdc-178">0.65 °-0.8 °</span><span class="sxs-lookup"><span data-stu-id="a2fdc-178">0.65°-0.8°</span></span> | <span data-ttu-id="a2fdc-179">5.1-6.3 mm</span><span class="sxs-lookup"><span data-stu-id="a2fdc-179">5.1-6.3mm</span></span> | <span data-ttu-id="a2fdc-180">14.47-17.8 pt</span><span class="sxs-lookup"><span data-stu-id="a2fdc-180">14.47-17.8pt</span></span> |
| <span data-ttu-id="a2fdc-181">2m</span><span class="sxs-lookup"><span data-stu-id="a2fdc-181">2m</span></span> | <span data-ttu-id="a2fdc-182">0.6 °-0.75 °</span><span class="sxs-lookup"><span data-stu-id="a2fdc-182">0.6°-0.75°</span></span> | <span data-ttu-id="a2fdc-183">20.9-26.2 mm</span><span class="sxs-lookup"><span data-stu-id="a2fdc-183">20.9-26.2mm</span></span> | <span data-ttu-id="a2fdc-184">59.4-74.2 pt</span><span class="sxs-lookup"><span data-stu-id="a2fdc-184">59.4-74.2pt</span></span> |


<span data-ttu-id="a2fdc-185">Segoe UI (Windows 的預設字型) 在大多數情況下都很好用。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-185">Segoe UI (the default font for Windows) works well in most cases.</span></span> <span data-ttu-id="a2fdc-186">不過, 請避免使用大小較小的淡或半透明字型系列, 因為精簡的垂直筆劃將會震動, 且會降低可讀性。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-186">However, avoid using light or semi light font families in small size since thin vertical strokes will vibrate and it will degrade the legibility.</span></span> <span data-ttu-id="a2fdc-187">具有足夠筆觸粗細的新式字型運作良好。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-187">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="a2fdc-188">例如, Helvetica 和 Arial 的外觀美觀, 在 HoloLens 中具有一般或粗權數。</span><span class="sxs-lookup"><span data-stu-id="a2fdc-188">For example, Helvetica and Arial look gorgeous and are very legible in HoloLens with regular or bold weights.</span></span>

<span data-ttu-id="a2fdc-189">\* \* 如需 Unity 中文字大小計算的詳細資訊, 請參閱[unity 中](text-in-unity.md)的頁面文字</span><span class="sxs-lookup"><span data-stu-id="a2fdc-189">\*\*For more detailed information about text size calculation in Unity, please refer to the page [Text in Unity](text-in-unity.md)</span></span>

<span data-ttu-id="a2fdc-190">![查看角度](images/Text_In_Unity_ViewingAngle.jpg)
*視圖距離、角度和文字高度*</span><span class="sxs-lookup"><span data-stu-id="a2fdc-190">![Viewing Angle](images/Text_In_Unity_ViewingAngle.jpg)
*Viewing distance, angle, and text height*</span></span>

## <a name="resources"></a><span data-ttu-id="a2fdc-191">資源</span><span class="sxs-lookup"><span data-stu-id="a2fdc-191">Resources</span></span>
* [<span data-ttu-id="a2fdc-192">Segoe 字型</span><span class="sxs-lookup"><span data-stu-id="a2fdc-192">Segoe fonts</span></span>](http://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)
* [<span data-ttu-id="a2fdc-193">HoloLens 字型</span><span class="sxs-lookup"><span data-stu-id="a2fdc-193">HoloLens font</span></span>](http://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)

<span data-ttu-id="a2fdc-194">![HoloLens 字型提供您在 Windows Mixed Reality 中使用的符號字元](images/300px-hololensmdl2symbols.jpg)
</span><span class="sxs-lookup"><span data-stu-id="a2fdc-194">![The HoloLens font gives you the symbol glyphs used in Windows Mixed Reality](images/300px-hololensmdl2symbols.jpg)
</span></span><br><span data-ttu-id="a2fdc-195">*HoloLens 字型提供您在 Windows Mixed Reality 中使用的符號字元。*</span><span class="sxs-lookup"><span data-stu-id="a2fdc-195">*The HoloLens font gives you the symbol glyphs used in Windows Mixed Reality.*</span></span>

## <a name="see-also"></a><span data-ttu-id="a2fdc-196">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2fdc-196">See also</span></span>
* [<span data-ttu-id="a2fdc-197">Unity 中的文字</span><span class="sxs-lookup"><span data-stu-id="a2fdc-197">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="a2fdc-198">色彩、光線和材質</span><span class="sxs-lookup"><span data-stu-id="a2fdc-198">Color, light and materials</span></span>](color,-light-and-materials.md)
