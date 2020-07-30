---
title: Unity 中的文字
description: 若要在 Unity 中顯示文字，您可以使用兩種類型的文字元件： UI 文字和3D 文字網格。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality，設計，控制項，字型，印刷樣式，ui，ux
ms.openlocfilehash: 6aa03eedf717fb73877db8660526e13444c43fe9
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376570"
---
# <a name="text-in-unity"></a><span data-ttu-id="7dd65-104">Unity 中的文字</span><span class="sxs-lookup"><span data-stu-id="7dd65-104">Text in Unity</span></span>

<span data-ttu-id="7dd65-105">文字是全像攝影應用程式中最重要的元件之一。</span><span class="sxs-lookup"><span data-stu-id="7dd65-105">Text is one of the most important components in holographic apps.</span></span> <span data-ttu-id="7dd65-106">若要在 Unity 中顯示文字，有三種類型的文字元件可供您使用： UI 文字、3D 文本網格和文本網格專業人員。</span><span class="sxs-lookup"><span data-stu-id="7dd65-106">To display text in Unity, there are three types of text components you can use — UI Text, 3D Text Mesh, and Text Mesh Pro.</span></span> <span data-ttu-id="7dd65-107">根據預設，UI 文字和3D 文本網格會呈現模糊且太大。</span><span class="sxs-lookup"><span data-stu-id="7dd65-107">By default, UI Text and 3D Text Mesh appear blurry and are too big.</span></span> <span data-ttu-id="7dd65-108">您需要調整一些變數，以取得在 HoloLens 中具有可管理大小的清晰、高品質文字。</span><span class="sxs-lookup"><span data-stu-id="7dd65-108">You need to tweak a few variables to get sharp, high-quality text that has a manageable size in HoloLens.</span></span> <span data-ttu-id="7dd65-109">藉由在使用 UI 文字和3D 文本網格元件時，套用縮放比例來取得適當的維度，您可以達到更佳的轉譯品質。</span><span class="sxs-lookup"><span data-stu-id="7dd65-109">By applying a scaling factor to get proper dimensions when using the UI Text and 3D Text Mesh components, you can achieve better rendering quality.</span></span>

<span data-ttu-id="7dd65-110">![如何取得清晰且美觀的文字](images/hug-text-02-640px.png)</span><span class="sxs-lookup"><span data-stu-id="7dd65-110">![How to get sharp and beautiful text](images/hug-text-02-640px.png)</span></span><br>
<span data-ttu-id="7dd65-111">*Unity 中的模糊預設文字*</span><span class="sxs-lookup"><span data-stu-id="7dd65-111">*Blurry default text in Unity*</span></span>

## <a name="working-with-unitys-3d-text-text-mesh-and-ui-text"></a><span data-ttu-id="7dd65-112">使用 Unity 的3D 文字（文本網格）和 UI 文字</span><span class="sxs-lookup"><span data-stu-id="7dd65-112">Working with Unity's 3D Text (Text Mesh) and UI Text</span></span>

<span data-ttu-id="7dd65-113">Unity 假設所有新增至場景的新專案都是大小的1個 Unity 單位，或100% 的轉換小數值，這在 HoloLens 上轉譯為約1個計量。</span><span class="sxs-lookup"><span data-stu-id="7dd65-113">Unity assumes that all new elements added to a scene are 1 Unity Unit in size, or 100% transform scale, which translates to about 1 meter on HoloLens.</span></span> <span data-ttu-id="7dd65-114">在字型的案例中，3D TextMesh 的周框方塊預設會出現在最高1計量的高度。</span><span class="sxs-lookup"><span data-stu-id="7dd65-114">In the case of fonts, the bounding box for a 3D TextMesh comes in by default at about 1 meter in height.</span></span>

<span data-ttu-id="7dd65-115">![在 Unity 中使用字型](images/640px-hug-text-03.png)</span><span class="sxs-lookup"><span data-stu-id="7dd65-115">![Working with Fonts in Unity](images/640px-hug-text-03.png)</span></span><br>
<span data-ttu-id="7dd65-116">*Default Unity 3D Text （文本網格）佔用1個 Unity 單位，也就是1個計量*</span><span class="sxs-lookup"><span data-stu-id="7dd65-116">*Default Unity 3D Text (Text Mesh) occupies 1 Unity Unit which is 1 meter*</span></span>

<br>
<span data-ttu-id="7dd65-117">大部分的視覺效果設計工具會使用點來定義真實世界中的字型大小。</span><span class="sxs-lookup"><span data-stu-id="7dd65-117">Most visual designers use points to define font sizes in the real world.</span></span> <span data-ttu-id="7dd65-118">1計量中大約有2835（2，834.645666399962）點。</span><span class="sxs-lookup"><span data-stu-id="7dd65-118">There are about 2835 (2,834.645666399962) points in 1 meter.</span></span> <span data-ttu-id="7dd65-119">根據 [將系統轉換成1個計量] 和 [Unity 的預設文本網格字型大小] 為13，[13] 的簡單數學運算除以2835等於0.0046 （0.004586111116 是精確的），這可提供良好的標準調整來開始使用（有些可能會想要舍入0.005）。</span><span class="sxs-lookup"><span data-stu-id="7dd65-119">Based on the point system conversion to 1 meter and Unity's default Text Mesh font size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) which provides a good standard scale to start with (some may wish to round to 0.005).</span></span> <span data-ttu-id="7dd65-120">將文字物件或容器調整為這些值，不只允許在設計程式中轉換1:1 的字型大小，同時也提供標準，讓您可以在整個體驗中維持一致性。</span><span class="sxs-lookup"><span data-stu-id="7dd65-120">Scaling the text object or container to these values will not only allow for the 1:1 conversion of font sizes in a design program, but also provides a standard so you can maintain consistency throughout your experience.</span></span>

<span data-ttu-id="7dd65-121">![具有不同字型大小的 Unity 3D 文本網格](images/Text_In_Unity_Measurements1.png)</span><span class="sxs-lookup"><span data-stu-id="7dd65-121">![Unity 3D Text Mesh with different font sizes](images/Text_In_Unity_Measurements1.png)</span></span><br>
<span data-ttu-id="7dd65-122">*調整 Unity 3D 文字和 UI 文字的值*</span><span class="sxs-lookup"><span data-stu-id="7dd65-122">*Scaling values for the Unity 3D Text and UI Text*</span></span>

<br>

<span data-ttu-id="7dd65-123">![具有不同字型大小的 Unity 3D 文本網格](images/hug-text-05-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="7dd65-123">![Unity 3D Text Mesh with different font sizes](images/hug-text-05-1000px.png)</span></span><br>
<span data-ttu-id="7dd65-124">*具有優化值的 Unity 3D 文本網格*</span><span class="sxs-lookup"><span data-stu-id="7dd65-124">*Unity 3D Text Mesh with optimized values*</span></span>

<br>
<span data-ttu-id="7dd65-125">將 UI 或畫布型文字專案新增至場景時，[大小] 差異仍然會大於。</span><span class="sxs-lookup"><span data-stu-id="7dd65-125">When adding a UI or canvas based text element to a scene, the size disparity is greater still.</span></span> <span data-ttu-id="7dd65-126">這兩種大小的差異大約是1000%，這會將以 UI 為基礎之文字元件的縮放比例，帶入0.00046 （0.0004586111116 是精確的）或四捨五入值的0.0005。</span><span class="sxs-lookup"><span data-stu-id="7dd65-126">The differences in the two sizes is about 1000%, which would bring the scale factor for UI based text components to 0.00046 (0.0004586111116 to be exact) or 0.0005 for the rounded value.</span></span>

<span data-ttu-id="7dd65-127">![具有每個單位值不同動態圖元的 Unity UI 文字](images/hug-text-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="7dd65-127">![Unity UI Text with different dynamic pixels per unit values](images/hug-text-04-1000px.png)</span></span><br>
<span data-ttu-id="7dd65-128">*具有優化值的 Unity UI 文字*</span><span class="sxs-lookup"><span data-stu-id="7dd65-128">*Unity UI Text with optimized values*</span></span>

<br>

>[!NOTE]
><span data-ttu-id="7dd65-129">任何字型的預設值可能會受到該字型的材質大小，或字型匯入 Unity 的方式所影響。</span><span class="sxs-lookup"><span data-stu-id="7dd65-129">The default value of any font may be affected by the texture size of that font or how the font was imported into Unity.</span></span> <span data-ttu-id="7dd65-130">這些測試是根據 Unity 中的預設 Arial 字型，以及另一個已匯入的字型來執行。</span><span class="sxs-lookup"><span data-stu-id="7dd65-130">These tests were performed based on the default Arial font in Unity, as well as one other imported font.</span></span>

## <a name="working-with-text-mesh-pro"></a><span data-ttu-id="7dd65-131">使用文本網格 Pro</span><span class="sxs-lookup"><span data-stu-id="7dd65-131">Working with Text Mesh Pro</span></span>

<span data-ttu-id="7dd65-132">使用 Unity 的文本網格 Pro，您可以保護文字轉譯品質。</span><span class="sxs-lookup"><span data-stu-id="7dd65-132">With Unity's Text Mesh Pro, you can secure the text rendering quality.</span></span> <span data-ttu-id="7dd65-133">不論使用 [[帶正負號距離] 欄位（.sdf）](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf)技術的距離為何，它都支援簡潔的文字外框。</span><span class="sxs-lookup"><span data-stu-id="7dd65-133">It supports crisp text outlines regardless of the distance using the [Signed Distance Field (SDF)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) technique.</span></span> <span data-ttu-id="7dd65-134">針對3D 文字網格和 UI 文字，使用我們先前使用的相同計算方法，我們可以尋找適當的縮放值以搭配傳統的印刷點使用。</span><span class="sxs-lookup"><span data-stu-id="7dd65-134">Using the same calculation method that we used above for the 3D Text Mesh and UI Text, we can find the proper scaling values to use with conventional typographic points.</span></span> <span data-ttu-id="7dd65-135">由於預設的3D 文字網格 Pro 字型（大小為36）的周框大小為 2.5 Unity 單位（2.5 m），因此我們可以使用調整值0.005 來取得點大小。</span><span class="sxs-lookup"><span data-stu-id="7dd65-135">Since the default 3D Text Mesh Pro font with the size of 36 has a bounding size of 2.5 Unity units (2.5m), we can use a scaling value of 0.005 to get the point size.</span></span> <span data-ttu-id="7dd65-136">UI 功能表底下的文本網格 Pro 具有25個 Unity 單位（25m）的預設周框大小。</span><span class="sxs-lookup"><span data-stu-id="7dd65-136">The Text Mesh Pro under the UI menu has a default bounding size of 25 Unity units (25m).</span></span> <span data-ttu-id="7dd65-137">這可為我們提供0.0005 的調整值。</span><span class="sxs-lookup"><span data-stu-id="7dd65-137">This gives us 0.0005 for the scaling value.</span></span>

<span data-ttu-id="7dd65-138">![具有不同字型大小的 Unity 3D 文本網格](images/Text_In_Unity_Measurements2.png)</span><span class="sxs-lookup"><span data-stu-id="7dd65-138">![Unity 3D Text Mesh with different font sizes](images/Text_In_Unity_Measurements2.png)</span></span><br>
<span data-ttu-id="7dd65-139">*調整 Unity 3D 文字和 UI 文字的值*</span><span class="sxs-lookup"><span data-stu-id="7dd65-139">*Scaling values for the Unity 3D Text and UI Text*</span></span>

## <a name="recommended-text-size"></a><span data-ttu-id="7dd65-140">建議的文字大小</span><span class="sxs-lookup"><span data-stu-id="7dd65-140">Recommended text size</span></span>
<span data-ttu-id="7dd65-141">如您所見，我們在 PC 或 tablet 裝置上使用的大小（通常介於12–32pt 填補之間）看起來相當小，距離2計量。</span><span class="sxs-lookup"><span data-stu-id="7dd65-141">As you can expect, type sizes that we use on a PC or a tablet device (typically between 12–32pt) look quite small at a distance of 2 meters.</span></span> <span data-ttu-id="7dd65-142">這取決於每個字型的特性，但一般來說，建議的最小觀賞角度和可讀性的字型高度是以我們的使用者研究研究為基礎的0.35 °-0.4 °/12.21-13.97mm。</span><span class="sxs-lookup"><span data-stu-id="7dd65-142">It depends on the characteristics of each font, but in general the recommended minimum viewing angle and the font height for legibility are around 0.35°-0.4°/12.21-13.97mm based on our user research studies.</span></span> <span data-ttu-id="7dd65-143">大約 35-40pt，並有上述的縮放因數。</span><span class="sxs-lookup"><span data-stu-id="7dd65-143">It is about 35-40pt with the scaling factor introduced above.</span></span> 

<span data-ttu-id="7dd65-144">若要在 0.45 m （45cm）附近互動，最小的可感知字型的視圖角度和高度是0.4 °-0.5 °/3.14 – 3.9 mm。</span><span class="sxs-lookup"><span data-stu-id="7dd65-144">For the near interaction at 0.45m (45cm), the minimum legible font's viewing angle and the height are 0.4°-0.5° / 3.14–3.9mm.</span></span> <span data-ttu-id="7dd65-145">其大約為 9-12pt，並具有上述的縮放比例。</span><span class="sxs-lookup"><span data-stu-id="7dd65-145">It is about 9-12pt with the scaling factor introduced above.</span></span>

<span data-ttu-id="7dd65-146">![近距離和遠處的互動範圍 ](images/typography-distance-1000px.jpg)
 *內容*</span><span class="sxs-lookup"><span data-stu-id="7dd65-146">![Near and far interaction range](images/typography-distance-1000px.jpg)
*Content at near and far interaction range*</span></span>

### <a name="the-minimum-legible-font-size"></a><span data-ttu-id="7dd65-147">最小的清晰字型大小</span><span class="sxs-lookup"><span data-stu-id="7dd65-147">The minimum legible font size</span></span>
| <span data-ttu-id="7dd65-148">距離</span><span class="sxs-lookup"><span data-stu-id="7dd65-148">Distance</span></span> | <span data-ttu-id="7dd65-149">視角</span><span class="sxs-lookup"><span data-stu-id="7dd65-149">Viewing angle</span></span> | <span data-ttu-id="7dd65-150">文字高度</span><span class="sxs-lookup"><span data-stu-id="7dd65-150">Text height</span></span> | <span data-ttu-id="7dd65-151">字型大小</span><span class="sxs-lookup"><span data-stu-id="7dd65-151">Font size</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="7dd65-152">45cm （直接操作距離）</span><span class="sxs-lookup"><span data-stu-id="7dd65-152">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="7dd65-153">0.4 °-0.5 °</span><span class="sxs-lookup"><span data-stu-id="7dd65-153">0.4°-0.5°</span></span> | <span data-ttu-id="7dd65-154">3.14 –3.9 毫米</span><span class="sxs-lookup"><span data-stu-id="7dd65-154">3.14–3.9mm</span></span> | <span data-ttu-id="7dd65-155">8.9 – 11.13 pt</span><span class="sxs-lookup"><span data-stu-id="7dd65-155">8.9–11.13pt</span></span> |
| <span data-ttu-id="7dd65-156">2m</span><span class="sxs-lookup"><span data-stu-id="7dd65-156">2m</span></span> | <span data-ttu-id="7dd65-157">0.35 °-0.4 °</span><span class="sxs-lookup"><span data-stu-id="7dd65-157">0.35°-0.4°</span></span> | <span data-ttu-id="7dd65-158">12.21 – 13.97 mm</span><span class="sxs-lookup"><span data-stu-id="7dd65-158">12.21–13.97mm</span></span> | <span data-ttu-id="7dd65-159">34.63-39.58 pt</span><span class="sxs-lookup"><span data-stu-id="7dd65-159">34.63-39.58pt</span></span> |


### <a name="the-comfortably-legible-font-size"></a><span data-ttu-id="7dd65-160">舒適的字型大小</span><span class="sxs-lookup"><span data-stu-id="7dd65-160">The comfortably legible font size</span></span>
| <span data-ttu-id="7dd65-161">距離</span><span class="sxs-lookup"><span data-stu-id="7dd65-161">Distance</span></span> | <span data-ttu-id="7dd65-162">視角</span><span class="sxs-lookup"><span data-stu-id="7dd65-162">Viewing angle</span></span> | <span data-ttu-id="7dd65-163">文字高度</span><span class="sxs-lookup"><span data-stu-id="7dd65-163">Text height</span></span> | <span data-ttu-id="7dd65-164">字型大小</span><span class="sxs-lookup"><span data-stu-id="7dd65-164">Font size</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="7dd65-165">45cm （直接操作距離）</span><span class="sxs-lookup"><span data-stu-id="7dd65-165">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="7dd65-166">0.65 °-0.8 °</span><span class="sxs-lookup"><span data-stu-id="7dd65-166">0.65°-0.8°</span></span> | <span data-ttu-id="7dd65-167">5.1-6.3 mm</span><span class="sxs-lookup"><span data-stu-id="7dd65-167">5.1-6.3mm</span></span> | <span data-ttu-id="7dd65-168">14.47-17.8 pt</span><span class="sxs-lookup"><span data-stu-id="7dd65-168">14.47-17.8pt</span></span> |
| <span data-ttu-id="7dd65-169">2m</span><span class="sxs-lookup"><span data-stu-id="7dd65-169">2m</span></span> | <span data-ttu-id="7dd65-170">0.6 °-0.75 °</span><span class="sxs-lookup"><span data-stu-id="7dd65-170">0.6°-0.75°</span></span> | <span data-ttu-id="7dd65-171">20.9-26.2 mm</span><span class="sxs-lookup"><span data-stu-id="7dd65-171">20.9-26.2mm</span></span> | <span data-ttu-id="7dd65-172">59.4-74.2 pt</span><span class="sxs-lookup"><span data-stu-id="7dd65-172">59.4-74.2pt</span></span> |

<span data-ttu-id="7dd65-173">Segoe UI （Windows 的預設字型）在大多數情況下都很好用。</span><span class="sxs-lookup"><span data-stu-id="7dd65-173">Segoe UI (the default font for Windows) works well in most cases.</span></span> <span data-ttu-id="7dd65-174">不過，請避免使用大小較小的淡或半透明字型系列，因為精簡的垂直筆劃將會震動，且會降低可讀性。</span><span class="sxs-lookup"><span data-stu-id="7dd65-174">However, avoid using light or semi light font families in small size since thin vertical strokes will vibrate and it will degrade the legibility.</span></span> <span data-ttu-id="7dd65-175">具有足夠筆觸粗細的新式字型運作良好。</span><span class="sxs-lookup"><span data-stu-id="7dd65-175">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="7dd65-176">例如，Helvetica 和 Arial 的外觀美觀，在 HoloLens 中具有一般或粗權數。</span><span class="sxs-lookup"><span data-stu-id="7dd65-176">For example, Helvetica and Arial look gorgeous and are very legible in HoloLens with regular or bold weights.</span></span>


<span data-ttu-id="7dd65-177">![查看角度 ](images/Text_In_Unity_ViewingAngle.jpg)
 *視圖距離、角度和文字高度*</span><span class="sxs-lookup"><span data-stu-id="7dd65-177">![Viewing Angle](images/Text_In_Unity_ViewingAngle.jpg)
*Viewing distance, angle, and text height*</span></span>

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a><span data-ttu-id="7dd65-178">具有適當維度的銳利文字轉譯品質</span><span class="sxs-lookup"><span data-stu-id="7dd65-178">Sharp text rendering quality with proper dimension</span></span>

<span data-ttu-id="7dd65-179">根據這些縮放因素，我們建立[了具有 UI 文字和3D 文字網格的文字 prefabs](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)。</span><span class="sxs-lookup"><span data-stu-id="7dd65-179">Based on these scaling factors, we have created [text prefabs with UI Text and 3D Text Mesh](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Prefabs/Text).</span></span> <span data-ttu-id="7dd65-180">開發人員可以使用這些 prefabs 來取得清晰的文字和一致的字型大小。</span><span class="sxs-lookup"><span data-stu-id="7dd65-180">Developers can use these prefabs to get sharp text and consistent font size.</span></span>

<span data-ttu-id="7dd65-181">![具有適當維度的銳利文字轉譯品質](images/hug-text-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="7dd65-181">![Sharp text rendering quality with proper dimension](images/hug-text-06-1000px.png)</span></span><br>
<span data-ttu-id="7dd65-182">*具有適當維度的銳利文字轉譯品質*</span><span class="sxs-lookup"><span data-stu-id="7dd65-182">*Sharp text rendering quality with proper dimension*</span></span>

## <a name="shader-with-occlusion-support"></a><span data-ttu-id="7dd65-183">具有遮蔽支援的著色器</span><span class="sxs-lookup"><span data-stu-id="7dd65-183">Shader with occlusion support</span></span>

<span data-ttu-id="7dd65-184">Unity 的預設字型材質不支援遮蔽。</span><span class="sxs-lookup"><span data-stu-id="7dd65-184">Unity's default font material does not support occlusion.</span></span> <span data-ttu-id="7dd65-185">因此，根據預設，您會看到物件後面的文字。</span><span class="sxs-lookup"><span data-stu-id="7dd65-185">Because of this, you will see the text behind the objects by default.</span></span> <span data-ttu-id="7dd65-186">我們已包含[支援遮蔽的簡單著色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/Text3DShader.shader)。</span><span class="sxs-lookup"><span data-stu-id="7dd65-186">We have included a simple [shader that supports the occlusion](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/Text3DShader.shader).</span></span> <span data-ttu-id="7dd65-187">下圖顯示具有預設字型材質（左）的文字，以及具有適當遮蔽的文字（right）。</span><span class="sxs-lookup"><span data-stu-id="7dd65-187">The image below shows the text with default font material (left) and the text with proper occlusion (right).</span></span>

<span data-ttu-id="7dd65-188">![具有遮蔽支援的著色器](images/hug-text-07-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="7dd65-188">![Shader with occlusion support](images/hug-text-07-1000px.png)</span></span><br>
<span data-ttu-id="7dd65-189">*具有遮蔽支援的著色器*</span><span class="sxs-lookup"><span data-stu-id="7dd65-189">*Shader with occlusion support*</span></span>


## <a name="see-also"></a><span data-ttu-id="7dd65-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7dd65-190">See also</span></span>
* [<span data-ttu-id="7dd65-191">MRTK 中的文字 Prefab</span><span class="sxs-lookup"><span data-stu-id="7dd65-191">Text Prefab in the MRTK</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)
* [<span data-ttu-id="7dd65-192">印刷樣式</span><span class="sxs-lookup"><span data-stu-id="7dd65-192">Typography</span></span>](typography.md)

 
