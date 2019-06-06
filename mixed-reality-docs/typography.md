---
title: 印刷樣式
description: 在您的應用程式體驗中提供資訊的重要項目文字。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，設計、 樣式、 字型、 印刷樣式、 ui、 ux
ms.openlocfilehash: debf125a7f82ac79fe3ad776ba9c8c0b69396848
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66692386"
---
# <a name="typography"></a><span data-ttu-id="43722-104">印刷樣式</span><span class="sxs-lookup"><span data-stu-id="43722-104">Typography</span></span>

<span data-ttu-id="43722-105">在您的應用程式體驗中提供資訊的重要項目文字。</span><span class="sxs-lookup"><span data-stu-id="43722-105">Text is an important element for delivering information in your app experience.</span></span> <span data-ttu-id="43722-106">就像在 2D 螢幕上的印刷樣式，目標是清楚且容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="43722-106">Just like typography on 2D screens, the goal is to be clear and readable.</span></span> <span data-ttu-id="43722-107">有了混合實境的 3d 外觀，就有機會影響文字和整體使用者體驗更佳的方式。</span><span class="sxs-lookup"><span data-stu-id="43722-107">With the three-dimensional aspect of mixed reality, there is an opportunity to affect the text and the overall user experience in an even greater way.</span></span>

<span data-ttu-id="43722-108">![HoloLens 中的印刷樣式範例](images/typography-cover.png)</span><span class="sxs-lookup"><span data-stu-id="43722-108">![Typography example in HoloLens](images/typography-cover.png)</span></span><br>
<span data-ttu-id="43722-109">*HoloLens 中的印刷樣式範例*</span><span class="sxs-lookup"><span data-stu-id="43722-109">*Typography example in HoloLens*</span></span>

<span data-ttu-id="43722-110">當我們談論 3D 中的型別時，我們傾向於認為立體、 體積型的 3D 文字。</span><span class="sxs-lookup"><span data-stu-id="43722-110">When we talk about type in 3D, we tend to think extruded, volumetric 3D text.</span></span> <span data-ttu-id="43722-111">有些商標設計和一些其他受限應用程式，除了立體的文字通常會降低文字的可讀性。</span><span class="sxs-lookup"><span data-stu-id="43722-111">Except for some logotype designs and a few other limited applications, extruded text tends to degrade the readability of the text.</span></span> <span data-ttu-id="43722-112">即使我們 3d 設計體驗，我們使用 2D 類型因為會更清晰且容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="43722-112">Even though we are designing experiences for 3D, we use 2D for the type because it is more legible and easier to read.</span></span>

<span data-ttu-id="43722-113">HoloLens，在全像投影使用加法類色彩系統為基礎的光線建構型別。</span><span class="sxs-lookup"><span data-stu-id="43722-113">In HoloLens, type is constructed with holograms using light based on the additive color system.</span></span> <span data-ttu-id="43722-114">就像其他全像投影，型別可以放在實際環境中可 world 鎖定，而且從任何角度觀察到。</span><span class="sxs-lookup"><span data-stu-id="43722-114">Just like other holograms, type can be placed in the actual environment where it can be world locked and observed from any angle.</span></span> <span data-ttu-id="43722-115">[視差](https://en.wikipedia.org/wiki/Parallax)類型和環境之間的效果也會增加深度經驗。</span><span class="sxs-lookup"><span data-stu-id="43722-115">The [parallax](https://en.wikipedia.org/wiki/Parallax) effect between the type and the environment also adds depth to the experience.</span></span>

## <a name="typography-in-mixed-reality"></a><span data-ttu-id="43722-116">在混合實境中的印刷樣式</span><span class="sxs-lookup"><span data-stu-id="43722-116">Typography in mixed reality</span></span>

<span data-ttu-id="43722-117">在混合實境中的印刷樣式規則是一樣的任何其他地方。</span><span class="sxs-lookup"><span data-stu-id="43722-117">Typographic rules in mixed reality are no different from anywhere else.</span></span> <span data-ttu-id="43722-118">虛擬世界和現實生活中的文字必須是易於閱讀、 可讀性更高。</span><span class="sxs-lookup"><span data-stu-id="43722-118">Text in both the physical world and the virtual world needs to be legible and readable.</span></span> <span data-ttu-id="43722-119">文字可能會在牆上或重疊，實體物件。</span><span class="sxs-lookup"><span data-stu-id="43722-119">Text could be on a wall or superimposed on a physical object.</span></span> <span data-ttu-id="43722-120">它可以浮動以及數位使用者介面。</span><span class="sxs-lookup"><span data-stu-id="43722-120">It could be floating along with a digital user interface.</span></span> <span data-ttu-id="43722-121">不論內容中，我們會套用相同的讀取和辨識的印刷樣式規則。</span><span class="sxs-lookup"><span data-stu-id="43722-121">Regardless of the context, we apply the same typographic rules for reading and recognition.</span></span>

### <a name="create-clear-hierarchy"></a><span data-ttu-id="43722-122">建立明確階層</span><span class="sxs-lookup"><span data-stu-id="43722-122">Create clear hierarchy</span></span>

<span data-ttu-id="43722-123">使用不同類型的大小和重量，建置對比和階層。</span><span class="sxs-lookup"><span data-stu-id="43722-123">Build contrast and hierarchy by using different type sizes and weights.</span></span> <span data-ttu-id="43722-124">定義型別遞增，並遵循整個應用程式體驗會提供絕佳的使用者體驗與一致的資訊階層。</span><span class="sxs-lookup"><span data-stu-id="43722-124">Defining a type ramp and following it throughout the app experience will provide a great user experience with consistent information hierarchy.</span></span>

<span data-ttu-id="43722-125">![類型 ramp 範例](images/typography-ramp-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="43722-125">![Type ramp examples](images/typography-ramp-1000px.jpg)</span></span><br>
<span data-ttu-id="43722-126">*定義型別遞增，並遵循整個應用程式體驗*</span><span class="sxs-lookup"><span data-stu-id="43722-126">*Define your type ramp and follow it throughout the app experience*</span></span>

### <a name="limit-your-fonts"></a><span data-ttu-id="43722-127">限制您的字型</span><span class="sxs-lookup"><span data-stu-id="43722-127">Limit your fonts</span></span>

<span data-ttu-id="43722-128">請避免使用單一的內容中的兩個以上不同的字型系列。</span><span class="sxs-lookup"><span data-stu-id="43722-128">Avoid using more than two different font families in a single context.</span></span> <span data-ttu-id="43722-129">這會中斷 harmony 和一致性的經驗，並讓它更難使用資訊。</span><span class="sxs-lookup"><span data-stu-id="43722-129">This will break the harmony and consistency of your experience and make it harder to consume information.</span></span> <span data-ttu-id="43722-130">在 HoloLens，因為資訊顯示在實際環境中，頂端使用太多的字型樣式會降低體驗。</span><span class="sxs-lookup"><span data-stu-id="43722-130">In HoloLens, since the information is overlaid on top of the physical environment, using too many font styles will degrade the experience.</span></span> <span data-ttu-id="43722-131">Segoe UI 是所有 Microsoft 的數位設計的字型。</span><span class="sxs-lookup"><span data-stu-id="43722-131">Segoe UI is the font for all Microsoft digital designs.</span></span> <span data-ttu-id="43722-132">它會以一致的方式在 Windows Mixed Reality 殼層。</span><span class="sxs-lookup"><span data-stu-id="43722-132">It is used consistently in the Windows Mixed Reality shell.</span></span> <span data-ttu-id="43722-133">您可以下載 Segoe UI 字型檔案，從[Windows 設計的工具組頁面](https://docs.microsoft.com/windows/uwp/design-downloads/)。</span><span class="sxs-lookup"><span data-stu-id="43722-133">You can download the Segoe UI font file from the [Windows design toolkit page](https://docs.microsoft.com/windows/uwp/design-downloads/).</span></span>

[<span data-ttu-id="43722-134">Segoe UI 字樣的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="43722-134">More information about the Segoe UI typeface</span></span>](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a><span data-ttu-id="43722-135">避免細的字型粗細</span><span class="sxs-lookup"><span data-stu-id="43722-135">Avoid thin font weights</span></span>

<span data-ttu-id="43722-136">避免使用淡或 semilight 字型加權 42pt 之下的類型大小，因為精簡型的垂直筆劃會震動並降低以利閱讀。</span><span class="sxs-lookup"><span data-stu-id="43722-136">Avoid using light or semilight font weights for type sizes under 42pt since thin vertical strokes will vibrate and degrade legibility.</span></span> <span data-ttu-id="43722-137">新式的字型，具有足夠的筆劃粗細正常運作。</span><span class="sxs-lookup"><span data-stu-id="43722-137">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="43722-138">比方說，新細明體和 Arial。 非常清晰 HoloLens 中使用規則或粗體加權值</span><span class="sxs-lookup"><span data-stu-id="43722-138">For example, Helvetica and Arial are very legible in HoloLens using regular or bold weights.</span></span>

### <a name="color"></a><span data-ttu-id="43722-139">色彩</span><span class="sxs-lookup"><span data-stu-id="43722-139">Color</span></span>

<span data-ttu-id="43722-140">在 HoloLens，因為全像投影建構與加總淺系統，白色文字是極高。</span><span class="sxs-lookup"><span data-stu-id="43722-140">In HoloLens, since the holograms are constructed with an additive light system, white text is highly legible.</span></span> <span data-ttu-id="43722-141">您可以找到 [開始] 功能表和應用程式列上的白色文字的範例。</span><span class="sxs-lookup"><span data-stu-id="43722-141">You can find examples of white text on the Start menu and the App bar.</span></span> <span data-ttu-id="43722-142">即使也無須後的調色盤的白色文字是 HoloLens 上運作，複雜的實體背景使得類型難以閱讀。</span><span class="sxs-lookup"><span data-stu-id="43722-142">Even though white text works well without a back plate on HoloLens, a complex physical background could make the type difficult to read.</span></span> <span data-ttu-id="43722-143">若要為了改善使用者的焦點，並將實體的背景的干擾降到最低，建議使用深色或回彩色的調色盤上的白色文字。</span><span class="sxs-lookup"><span data-stu-id="43722-143">To improve the user's focus and minimize the distraction from a physical background, we recommend using white text on a dark or colored back plate.</span></span>

<br>


<span data-ttu-id="43722-144">![我們建議使用深色或彩色後調色盤上的白色文字。](images/typography-whiteonblack2-1000px.jpg)
*暗色或彩色後調色盤上的白色文字的範例。*</span><span class="sxs-lookup"><span data-stu-id="43722-144">![We recommend using white text on a dark or colored back plate.](images/typography-whiteonblack2-1000px.jpg)
*Examples of white text on a dark or colored back plate.*</span></span>
<br>

<span data-ttu-id="43722-145">若要使用深色的文字，您應該使用亮後盤子讓它更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="43722-145">To use dark text, you should use a bright back plate to make it readable.</span></span> <span data-ttu-id="43722-146">在累加式的色彩系統中，黑色會以透明方式顯示。</span><span class="sxs-lookup"><span data-stu-id="43722-146">In additive color systems, black is displayed as transparent.</span></span> <span data-ttu-id="43722-147">這表示您將無法看到回盤子的黑色文字而不需要以顏色標示。</span><span class="sxs-lookup"><span data-stu-id="43722-147">This means you will not be able to see the black text without a colored back plate.</span></span>

<span data-ttu-id="43722-148">![黑色文字範例](images/typography-whiteonblack.png)
</span><span class="sxs-lookup"><span data-stu-id="43722-148">![Black text examples](images/typography-whiteonblack.png)
</span></span><br><span data-ttu-id="43722-149">*上一步的白色與黑色白色文字的範例*</span><span class="sxs-lookup"><span data-stu-id="43722-149">*Examples of white on back and black on white text*</span></span>


<span data-ttu-id="43722-150">![黑色文字範例](images/640px-typography-blackonwhite.jpg)
</span><span class="sxs-lookup"><span data-stu-id="43722-150">![Black text examples](images/640px-typography-blackonwhite.jpg)
</span></span><br><span data-ttu-id="43722-151">*在 系統應用程式-存放區和設定的黑色文字的範例*</span><span class="sxs-lookup"><span data-stu-id="43722-151">*Examples of black text in the system apps - Store and Settings*</span></span>

## <a name="recommended-font-size"></a><span data-ttu-id="43722-152">建議使用的字型大小</span><span class="sxs-lookup"><span data-stu-id="43722-152">Recommended font size</span></span>

<span data-ttu-id="43722-153">您可能已經想到，我們使用電腦或平板電腦裝置 （通常在 12 – 產生 32pt) 之間的類型大小的 2 公尺的距離看變得很小。</span><span class="sxs-lookup"><span data-stu-id="43722-153">As you can expect, type sizes that we use on a PC or a tablet device (typically between 12–32pt) look quite small at a distance of 2 meters.</span></span> <span data-ttu-id="43722-154">它取決於特性的每種字型，但一般情況下檢視角度和字型高度，以利閱讀建議的最小周圍 0.35°-0.4°/12.21-13.97mm 根據我們的使用者研究工作。</span><span class="sxs-lookup"><span data-stu-id="43722-154">It depends on the characteristics of each font, but in general the recommended minimum viewing angle and the font height for legibility are around 0.35°-0.4°/12.21-13.97mm based on our user research studies.</span></span> <span data-ttu-id="43722-155">它是關於 35 40pt 上面介紹的縮放因數。</span><span class="sxs-lookup"><span data-stu-id="43722-155">It is about 35-40pt with the scaling factor introduced above.</span></span> 

<span data-ttu-id="43722-156">在 0.45m(45cm) 幾近互動，最小易於閱讀字型檢視角度和高度是 0.4 °-0.5 ° / 3.14 – 3.9 mm。</span><span class="sxs-lookup"><span data-stu-id="43722-156">For the near interaction at 0.45m(45cm), the minimum legible font's viewing angle and the height are 0.4°-0.5° / 3.14–3.9mm.</span></span> <span data-ttu-id="43722-157">它是關於 9 12pt 上面介紹的縮放因數。</span><span class="sxs-lookup"><span data-stu-id="43722-157">It is about 9-12pt with the scaling factor introduced above.</span></span>

<span data-ttu-id="43722-158">![不久，到目前為止的互動範圍](images/typography-distance-1000px.jpg)
*內容在附近，遠的互動範圍*</span><span class="sxs-lookup"><span data-stu-id="43722-158">![Near and far interaction range](images/typography-distance-1000px.jpg)
*Content at near and far interaction range*</span></span>

### <a name="the-minimum-legible-font-size"></a><span data-ttu-id="43722-159">易於閱讀的字型大小下限</span><span class="sxs-lookup"><span data-stu-id="43722-159">The minimum legible font size</span></span>
| <span data-ttu-id="43722-160">距離</span><span class="sxs-lookup"><span data-stu-id="43722-160">Distance</span></span> | <span data-ttu-id="43722-161">檢視角度</span><span class="sxs-lookup"><span data-stu-id="43722-161">Viewing angle</span></span> | <span data-ttu-id="43722-162">文字高度</span><span class="sxs-lookup"><span data-stu-id="43722-162">Text height</span></span> | <span data-ttu-id="43722-163">字型的大小 \* \*</span><span class="sxs-lookup"><span data-stu-id="43722-163">Font size\*\*</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="43722-164">45 cm （直接操作距離）</span><span class="sxs-lookup"><span data-stu-id="43722-164">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="43722-165">0.4°-0.5°</span><span class="sxs-lookup"><span data-stu-id="43722-165">0.4°-0.5°</span></span> | <span data-ttu-id="43722-166">3.14–3.9mm</span><span class="sxs-lookup"><span data-stu-id="43722-166">3.14–3.9mm</span></span> | <span data-ttu-id="43722-167">8.9–11.13pt</span><span class="sxs-lookup"><span data-stu-id="43722-167">8.9–11.13pt</span></span> |
| <span data-ttu-id="43722-168">2m</span><span class="sxs-lookup"><span data-stu-id="43722-168">2m</span></span> | <span data-ttu-id="43722-169">0.35°-0.4°</span><span class="sxs-lookup"><span data-stu-id="43722-169">0.35°-0.4°</span></span> | <span data-ttu-id="43722-170">12.21–13.97mm</span><span class="sxs-lookup"><span data-stu-id="43722-170">12.21–13.97mm</span></span> | <span data-ttu-id="43722-171">34.63-39.58pt</span><span class="sxs-lookup"><span data-stu-id="43722-171">34.63-39.58pt</span></span> |


### <a name="the-comfortably-legible-font-size"></a><span data-ttu-id="43722-172">舒服地易於閱讀的字型大小</span><span class="sxs-lookup"><span data-stu-id="43722-172">The comfortably legible font size</span></span>
| <span data-ttu-id="43722-173">距離</span><span class="sxs-lookup"><span data-stu-id="43722-173">Distance</span></span> | <span data-ttu-id="43722-174">檢視角度</span><span class="sxs-lookup"><span data-stu-id="43722-174">Viewing angle</span></span> | <span data-ttu-id="43722-175">文字高度</span><span class="sxs-lookup"><span data-stu-id="43722-175">Text height</span></span> | <span data-ttu-id="43722-176">字型的大小 \* \*</span><span class="sxs-lookup"><span data-stu-id="43722-176">Font size\*\*</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="43722-177">45 cm （直接操作距離）</span><span class="sxs-lookup"><span data-stu-id="43722-177">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="43722-178">0.65°-0.8°</span><span class="sxs-lookup"><span data-stu-id="43722-178">0.65°-0.8°</span></span> | <span data-ttu-id="43722-179">5.1-6.3mm</span><span class="sxs-lookup"><span data-stu-id="43722-179">5.1-6.3mm</span></span> | <span data-ttu-id="43722-180">14.47-17.8pt</span><span class="sxs-lookup"><span data-stu-id="43722-180">14.47-17.8pt</span></span> |
| <span data-ttu-id="43722-181">2m</span><span class="sxs-lookup"><span data-stu-id="43722-181">2m</span></span> | <span data-ttu-id="43722-182">0.6°-0.75°</span><span class="sxs-lookup"><span data-stu-id="43722-182">0.6°-0.75°</span></span> | <span data-ttu-id="43722-183">20.9-26.2mm</span><span class="sxs-lookup"><span data-stu-id="43722-183">20.9-26.2mm</span></span> | <span data-ttu-id="43722-184">59.4-74.2pt</span><span class="sxs-lookup"><span data-stu-id="43722-184">59.4-74.2pt</span></span> |


<span data-ttu-id="43722-185">Segoe UI （Windows 的預設字型） 也適用於大部分的情況。</span><span class="sxs-lookup"><span data-stu-id="43722-185">Segoe UI (the default font for Windows) works well in most cases.</span></span> <span data-ttu-id="43722-186">不過，在避免使用 light 或半淺色字型系列較小，因為將震動精簡型的垂直筆劃，而且它會降低易讀性。</span><span class="sxs-lookup"><span data-stu-id="43722-186">However, avoid using light or semi light font families in small size since thin vertical strokes will vibrate and it will degrade the legibility.</span></span> <span data-ttu-id="43722-187">新式的字型，具有足夠的筆劃粗細正常運作。</span><span class="sxs-lookup"><span data-stu-id="43722-187">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="43722-188">比方說，新細明體新細明體看起來美觀和 HoloLens 中使用規則或粗體加權非常清晰。</span><span class="sxs-lookup"><span data-stu-id="43722-188">For example, Helvetica and Arial look gorgeous and are very legible in HoloLens with regular or bold weights.</span></span>

<span data-ttu-id="43722-189">\* \* 如需詳細資訊在 Unity 中的文字大小計算時，請參閱頁面[Unity 中的文字](text-in-unity.md)</span><span class="sxs-lookup"><span data-stu-id="43722-189">\*\*For more detailed information about text size calculation in Unity, please refer to the page [Text in Unity](text-in-unity.md)</span></span>

<span data-ttu-id="43722-190">![檢視角度](images/Text_In_Unity_ViewingAngle.jpg)
*檢視距離、 角度和文字的高度*</span><span class="sxs-lookup"><span data-stu-id="43722-190">![Viewing Angle](images/Text_In_Unity_ViewingAngle.jpg)
*Viewing distance, angle, and text height*</span></span>

## <a name="resources"></a><span data-ttu-id="43722-191">資源</span><span class="sxs-lookup"><span data-stu-id="43722-191">Resources</span></span>
* [<span data-ttu-id="43722-192">Segoe 字型</span><span class="sxs-lookup"><span data-stu-id="43722-192">Segoe fonts</span></span>](http://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)
* [<span data-ttu-id="43722-193">HoloLens 字型</span><span class="sxs-lookup"><span data-stu-id="43722-193">HoloLens font</span></span>](http://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)

<span data-ttu-id="43722-194">![HoloLens 字型可讓您使用 Windows Mixed Reality 符號字符](images/300px-hololensmdl2symbols.jpg)
</span><span class="sxs-lookup"><span data-stu-id="43722-194">![The HoloLens font gives you the symbol glyphs used in Windows Mixed Reality](images/300px-hololensmdl2symbols.jpg)
</span></span><br><span data-ttu-id="43722-195">*HoloLens 字型可讓您使用 Windows Mixed Reality 符號字符。*</span><span class="sxs-lookup"><span data-stu-id="43722-195">*The HoloLens font gives you the symbol glyphs used in Windows Mixed Reality.*</span></span>

## <a name="see-also"></a><span data-ttu-id="43722-196">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43722-196">See also</span></span>
* [<span data-ttu-id="43722-197">Unity 中的文字</span><span class="sxs-lookup"><span data-stu-id="43722-197">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="43722-198">色彩、光線和材質</span><span class="sxs-lookup"><span data-stu-id="43722-198">Color, light and materials</span></span>](color,-light-and-materials.md)
