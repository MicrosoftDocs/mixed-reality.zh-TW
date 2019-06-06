---
title: 在 Unity 中的文字
description: 若要在 Unity 中顯示文字，有兩種類型的文字元件，您可以使用-UI 文字和 3D 文字網狀結構。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，設計、 控制項、 字型、 印刷樣式、 ui、 ux
ms.openlocfilehash: a601ab5ab5168f286a0935ca06eeec13022e1eee
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66692313"
---
# <a name="text-in-unity"></a><span data-ttu-id="ecd8b-104">在 Unity 中的文字</span><span class="sxs-lookup"><span data-stu-id="ecd8b-104">Text in Unity</span></span>

<span data-ttu-id="ecd8b-105">文字可以是其中一個最重要的元件，在全像攝影版的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-105">Text is one of the most important components in holographic apps.</span></span> <span data-ttu-id="ecd8b-106">若要在 Unity 中顯示文字，有三種您可以使用文字元件 — UI 文字、 3D 文字網狀結構，和文字 Mesh Pro。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-106">To display text in Unity, there are three types of text components you can use — UI Text, 3D Text Mesh, and Text Mesh Pro.</span></span> <span data-ttu-id="ecd8b-107">依預設 UI 文字和 3D 文字網格看起來是模糊且太大。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-107">By default UI Text and 3D Text Mesh appear blurry and are too big.</span></span> <span data-ttu-id="ecd8b-108">您需要調整幾個變數，以取得明確的高品質文字 HoloLens 中具有可管理的大小。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-108">You need to tweak a few variables to get sharp, high-quality text that has a manageable size in HoloLens.</span></span> <span data-ttu-id="ecd8b-109">藉由套用縮放比例，以取得適當的維度，使用 UI 文字和 3D 文字 Mesh 的元件時，您可以達到更好的呈現品質。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-109">By applying scaling factor to get proper dimensions when using the UI Text and 3D Text Mesh components, you can achieve better rendering quality.</span></span>

<span data-ttu-id="ecd8b-110">![如何取得聰明又美觀的文字](images/hug-text-02-640px.png)</span><span class="sxs-lookup"><span data-stu-id="ecd8b-110">![How to get sharp and beautiful text](images/hug-text-02-640px.png)</span></span><br>
<span data-ttu-id="ecd8b-111">*在 Unity 中的模糊的預設文字*</span><span class="sxs-lookup"><span data-stu-id="ecd8b-111">*Blurry default text in Unity*</span></span>

## <a name="working-with-unitys-3d-texttext-mesh-and-ui-text"></a><span data-ttu-id="ecd8b-112">使用 Unity 的 3D 文字 （Text 網狀結構） 和 UI 文字</span><span class="sxs-lookup"><span data-stu-id="ecd8b-112">Working with Unity's 3D Text(Text Mesh) and UI Text</span></span>

<span data-ttu-id="ecd8b-113">Unity 假設所有新增至場景的新項目 1 中的大小或 100%轉換小數位數，會轉譯為大約 1 公尺 HoloLens 上的 Unity 單位。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-113">Unity assumes all new elements added to a scene are 1 Unity Unit in size, or 100% transform scale, which translates to about 1 meter on HoloLens.</span></span> <span data-ttu-id="ecd8b-114">如果字型是週框方塊 3D TextMesh 隨附的預設位置的高度大約 1 公尺。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-114">In the case of fonts, the bounding box for a 3D TextMesh comes in by default at about 1 meter in height.</span></span>

<span data-ttu-id="ecd8b-115">![使用 Unity 中的字型](images/640px-hug-text-03.png)</span><span class="sxs-lookup"><span data-stu-id="ecd8b-115">![Working with Fonts in Unity](images/640px-hug-text-03.png)</span></span><br>
<span data-ttu-id="ecd8b-116">*預設 Unity 3D 文字 (Text Mesh) 佔用 1 Unity 單位為 1 公尺*</span><span class="sxs-lookup"><span data-stu-id="ecd8b-116">*Default Unity 3D Text (Text Mesh) occupies 1 Unity Unit which is 1 meter*</span></span>

<br>
<span data-ttu-id="ecd8b-117">大部分的視覺化設計工具會使用點來定義真實世界中的字型大小。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-117">Most visual designers use points to define font sizes in the real world.</span></span> <span data-ttu-id="ecd8b-118">有大約 2835 (2,834.645666399962) 在 1 公尺的點。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-118">There are about 2835 (2,834.645666399962) points in 1 meter.</span></span> <span data-ttu-id="ecd8b-119">根據點系統轉換為 1 公尺和 Unity 的預設文字 Mesh 字型大小為 13，13 除以 2835年等於 0.0046 (0.004586111116 很精確) 的簡單數學運算提供良好的標準擴展開始 （部分可能會想要為 0.005 捨入）。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-119">Based on the point system conversion to 1 meter and Unity's default Text Mesh font size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) provides a good standard scale to start with (some may wish to round to 0.005).</span></span> <span data-ttu-id="ecd8b-120">調整文字物件或為這些值的容器不會只允許 1 對 1 轉換字型的大小在設計程式中，但也提供一種標準，因此您可以在您的經驗來維護一致性。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-120">Scaling the text object or container to these values will not only allow for the 1:1 conversion of font sizes in a design program, but also provides a standard so you can maintain consistency throughout your experience.</span></span>

<span data-ttu-id="ecd8b-121">![Unity 3D 文字網格不同的字型大小](images/Text_In_Unity_Measurements1.png)</span><span class="sxs-lookup"><span data-stu-id="ecd8b-121">![Unity 3D Text Mesh with different font sizes](images/Text_In_Unity_Measurements1.png)</span></span><br>
<span data-ttu-id="ecd8b-122">*調整 Unity 3D 文字和 UI 文字值*</span><span class="sxs-lookup"><span data-stu-id="ecd8b-122">*Scaling values for the Unity 3D Text and UI Text*</span></span>

<span data-ttu-id="ecd8b-123">![Unity 3D 文字網格不同的字型大小](images/hug-text-05-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="ecd8b-123">![Unity 3D Text Mesh with different font sizes](images/hug-text-05-1000px.png)</span></span><br>
<span data-ttu-id="ecd8b-124">*Unity 3D 文字網格最佳化的值*</span><span class="sxs-lookup"><span data-stu-id="ecd8b-124">*Unity 3D Text Mesh with optimized values*</span></span>

<br>
<span data-ttu-id="ecd8b-125">當將 UI 或畫布的基礎的文字項目新增至場景，大小差異大於仍是。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-125">When adding a UI or canvas based text element to a scene, the size disparity is greater still.</span></span> <span data-ttu-id="ecd8b-126">在這兩個大小的差異是大約 1000年%，這會將縮放比例 0.00046 (0.0004586111116 很精確) 基礎的 UI 文字元件或超過 0.0005 的捨入的值。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-126">The differences in the two sizes is about 1000%, which would bring the scale factor for UI based text components to 0.00046 (0.0004586111116 to be exact) or 0.0005 for the rounded value.</span></span>

<span data-ttu-id="ecd8b-127">![使用不同的動態像素，每個單位值的 unity UI 文字](images/hug-text-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="ecd8b-127">![Unity UI Text with different dynamic pixels per unit values](images/hug-text-04-1000px.png)</span></span><br>
<span data-ttu-id="ecd8b-128">*Unity UI 文字，以最佳化的值*</span><span class="sxs-lookup"><span data-stu-id="ecd8b-128">*Unity UI Text with optimized values*</span></span>

<br>

>[!NOTE]
><span data-ttu-id="ecd8b-129">任何字型的預設值可能會受到該字型或字型如何匯入至 Unity 的紋理大小。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-129">The default value of any font may be affected by the texture size of that font or how the font was imported into Unity.</span></span> <span data-ttu-id="ecd8b-130">這些測試所據以執行在 Unity 中的預設新細明體字型，以及其他匯入的一種字型。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-130">These tests were performed based on the default Arial font in Unity, as well as one other imported font.</span></span>

## <a name="working-with-text-mesh-pro"></a><span data-ttu-id="ecd8b-131">處理文字 Mesh Pro</span><span class="sxs-lookup"><span data-stu-id="ecd8b-131">Working with Text Mesh Pro</span></span>

<span data-ttu-id="ecd8b-132">使用 Unity 的文字 Mesh Pro，您可以保護的文字呈現品質。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-132">With Unity's Text Mesh Pro, you can secure the text rendering quality.</span></span> <span data-ttu-id="ecd8b-133">它支援不論距離使用清晰的文字外框[SDF （簽署距離欄位）](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf)技巧。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-133">It supports crisp text outline regardless of the distance using the [SDF(Signed Distance Field)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) technique.</span></span> <span data-ttu-id="ecd8b-134">使用 3D 文字網格和 UI 文字上面使用的相同計算方法，我們可以找出適當的調整值，要使用傳統的印刷樣式端點。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-134">Using the same calculation method that we used above for the 3D Text Mesh and UI Text, we can find proper scaling values to use conventional typographic Point.</span></span> <span data-ttu-id="ecd8b-135">由於預設 3D 大小 36 Mesh Pro 文字字型顯示 2.5 Unity Unit(2.5m) 的周框，我們可以使用縮放比例值 0.005 若要使用的點數大小。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-135">Since the default 3D Text Mesh Pro font with the size 36 shows the bounding of 2.5 Unity Unit(2.5m), we can use scaling value 0.005 to use the Point size.</span></span> <span data-ttu-id="ecd8b-136">文字 Mesh Pro UI 功能表底下有週框大小的 25 Unity Unit(25m) 預設值。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-136">The Text Mesh Pro under UI menu has the default bounding size of 25 Unity Unit(25m).</span></span> <span data-ttu-id="ecd8b-137">這會提供超過 0.0005 的縮放比例的值。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-137">This gives us 0.0005 for the scaling value.</span></span>

<span data-ttu-id="ecd8b-138">![Unity 3D 文字網格不同的字型大小](images/Text_In_Unity_Measurements2.png)</span><span class="sxs-lookup"><span data-stu-id="ecd8b-138">![Unity 3D Text Mesh with different font sizes](images/Text_In_Unity_Measurements2.png)</span></span><br>
<span data-ttu-id="ecd8b-139">*調整 Unity 3D 文字和 UI 文字值*</span><span class="sxs-lookup"><span data-stu-id="ecd8b-139">*Scaling values for the Unity 3D Text and UI Text*</span></span>

## <a name="recommended-text-size"></a><span data-ttu-id="ecd8b-140">建議的文字大小</span><span class="sxs-lookup"><span data-stu-id="ecd8b-140">Recommended text size</span></span>
<span data-ttu-id="ecd8b-141">您可能已經想到，我們使用電腦或平板電腦裝置 （通常在 12 – 產生 32pt) 之間的類型大小的 2 公尺的距離看變得很小。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-141">As you can expect, type sizes that we use on a PC or a tablet device (typically between 12–32pt) look quite small at a distance of 2 meters.</span></span> <span data-ttu-id="ecd8b-142">它取決於特性的每種字型，但一般情況下檢視角度和字型高度，以利閱讀建議的最小周圍 0.35°-0.4°/12.21-13.97mm 根據我們的使用者研究工作。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-142">It depends on the characteristics of each font, but in general the recommended minimum viewing angle and the font height for legibility are around 0.35°-0.4°/12.21-13.97mm based on our user research studies.</span></span> <span data-ttu-id="ecd8b-143">它是關於 35 40pt 上面介紹的縮放因數。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-143">It is about 35-40pt with the scaling factor introduced above.</span></span> 

<span data-ttu-id="ecd8b-144">在 0.45m(45cm) 幾近互動，最小易於閱讀字型檢視角度和高度是 0.4 °-0.5 ° / 3.14 – 3.9 mm。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-144">For the near interaction at 0.45m(45cm), the minimum legible font's viewing angle and the height are 0.4°-0.5° / 3.14–3.9mm.</span></span> <span data-ttu-id="ecd8b-145">它是關於 9 12pt 上面介紹的縮放因數。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-145">It is about 9-12pt with the scaling factor introduced above.</span></span>

<span data-ttu-id="ecd8b-146">![不久，到目前為止的互動範圍](images/typography-distance-1000px.jpg)
*內容在附近，遠的互動範圍*</span><span class="sxs-lookup"><span data-stu-id="ecd8b-146">![Near and far interaction range](images/typography-distance-1000px.jpg)
*Content at near and far interaction range*</span></span>

### <a name="the-minimum-legible-font-size"></a><span data-ttu-id="ecd8b-147">易於閱讀的字型大小下限</span><span class="sxs-lookup"><span data-stu-id="ecd8b-147">The minimum legible font size</span></span>
| <span data-ttu-id="ecd8b-148">距離</span><span class="sxs-lookup"><span data-stu-id="ecd8b-148">Distance</span></span> | <span data-ttu-id="ecd8b-149">檢視角度</span><span class="sxs-lookup"><span data-stu-id="ecd8b-149">Viewing angle</span></span> | <span data-ttu-id="ecd8b-150">文字高度</span><span class="sxs-lookup"><span data-stu-id="ecd8b-150">Text height</span></span> | <span data-ttu-id="ecd8b-151">字型大小</span><span class="sxs-lookup"><span data-stu-id="ecd8b-151">Font size</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="ecd8b-152">45 cm （直接操作距離）</span><span class="sxs-lookup"><span data-stu-id="ecd8b-152">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="ecd8b-153">0.4°-0.5°</span><span class="sxs-lookup"><span data-stu-id="ecd8b-153">0.4°-0.5°</span></span> | <span data-ttu-id="ecd8b-154">3.14–3.9mm</span><span class="sxs-lookup"><span data-stu-id="ecd8b-154">3.14–3.9mm</span></span> | <span data-ttu-id="ecd8b-155">8.9–11.13pt</span><span class="sxs-lookup"><span data-stu-id="ecd8b-155">8.9–11.13pt</span></span> |
| <span data-ttu-id="ecd8b-156">2m</span><span class="sxs-lookup"><span data-stu-id="ecd8b-156">2m</span></span> | <span data-ttu-id="ecd8b-157">0.35°-0.4°</span><span class="sxs-lookup"><span data-stu-id="ecd8b-157">0.35°-0.4°</span></span> | <span data-ttu-id="ecd8b-158">12.21–13.97mm</span><span class="sxs-lookup"><span data-stu-id="ecd8b-158">12.21–13.97mm</span></span> | <span data-ttu-id="ecd8b-159">34.63-39.58pt</span><span class="sxs-lookup"><span data-stu-id="ecd8b-159">34.63-39.58pt</span></span> |


### <a name="the-comfortably-legible-font-size"></a><span data-ttu-id="ecd8b-160">舒服地易於閱讀的字型大小</span><span class="sxs-lookup"><span data-stu-id="ecd8b-160">The comfortably legible font size</span></span>
| <span data-ttu-id="ecd8b-161">距離</span><span class="sxs-lookup"><span data-stu-id="ecd8b-161">Distance</span></span> | <span data-ttu-id="ecd8b-162">檢視角度</span><span class="sxs-lookup"><span data-stu-id="ecd8b-162">Viewing angle</span></span> | <span data-ttu-id="ecd8b-163">文字高度</span><span class="sxs-lookup"><span data-stu-id="ecd8b-163">Text height</span></span> | <span data-ttu-id="ecd8b-164">字型大小</span><span class="sxs-lookup"><span data-stu-id="ecd8b-164">Font size</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="ecd8b-165">45 cm （直接操作距離）</span><span class="sxs-lookup"><span data-stu-id="ecd8b-165">45cm (direct manipulation distance)</span></span> | <span data-ttu-id="ecd8b-166">0.65°-0.8°</span><span class="sxs-lookup"><span data-stu-id="ecd8b-166">0.65°-0.8°</span></span> | <span data-ttu-id="ecd8b-167">5.1-6.3mm</span><span class="sxs-lookup"><span data-stu-id="ecd8b-167">5.1-6.3mm</span></span> | <span data-ttu-id="ecd8b-168">14.47-17.8pt</span><span class="sxs-lookup"><span data-stu-id="ecd8b-168">14.47-17.8pt</span></span> |
| <span data-ttu-id="ecd8b-169">2m</span><span class="sxs-lookup"><span data-stu-id="ecd8b-169">2m</span></span> | <span data-ttu-id="ecd8b-170">0.6°-0.75°</span><span class="sxs-lookup"><span data-stu-id="ecd8b-170">0.6°-0.75°</span></span> | <span data-ttu-id="ecd8b-171">20.9-26.2mm</span><span class="sxs-lookup"><span data-stu-id="ecd8b-171">20.9-26.2mm</span></span> | <span data-ttu-id="ecd8b-172">59.4-74.2pt</span><span class="sxs-lookup"><span data-stu-id="ecd8b-172">59.4-74.2pt</span></span> |

<span data-ttu-id="ecd8b-173">Segoe UI （Windows 的預設字型） 也適用於大部分的情況。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-173">Segoe UI (the default font for Windows) works well in most cases.</span></span> <span data-ttu-id="ecd8b-174">不過，在避免使用 light 或半淺色字型系列較小，因為將震動精簡型的垂直筆劃，而且它會降低易讀性。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-174">However, avoid using light or semi light font families in small size since thin vertical strokes will vibrate and it will degrade the legibility.</span></span> <span data-ttu-id="ecd8b-175">新式的字型，具有足夠的筆劃粗細正常運作。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-175">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="ecd8b-176">比方說，新細明體新細明體看起來美觀和 HoloLens 中使用規則或粗體加權非常清晰。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-176">For example, Helvetica and Arial look gorgeous and are very legible in HoloLens with regular or bold weights.</span></span>


<span data-ttu-id="ecd8b-177">![檢視角度](images/Text_In_Unity_ViewingAngle.jpg)
*檢視距離、 角度和文字的高度*</span><span class="sxs-lookup"><span data-stu-id="ecd8b-177">![Viewing Angle](images/Text_In_Unity_ViewingAngle.jpg)
*Viewing distance, angle, and text height*</span></span>

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a><span data-ttu-id="ecd8b-178">明確的文字呈現品質與正確的維度</span><span class="sxs-lookup"><span data-stu-id="ecd8b-178">Sharp text rendering quality with proper dimension</span></span>

<span data-ttu-id="ecd8b-179">根據這些縮放係數，我們建立了[UI 文字與 3D 文字 Mesh 的文字 prefabs](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-179">Based on these scaling factors, we have created [text prefabs with UI Text and 3D Text Mesh](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text).</span></span> <span data-ttu-id="ecd8b-180">開發人員可以使用這些 prefabs，以取得明確的文字和一致的字型大小。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-180">Developers can use these prefabs to get sharp text and consistent font size.</span></span>

<span data-ttu-id="ecd8b-181">![明確的文字呈現品質與正確的維度](images/hug-text-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="ecd8b-181">![Sharp text rendering quality with proper dimension](images/hug-text-06-1000px.png)</span></span><br>
<span data-ttu-id="ecd8b-182">*明確的文字呈現品質與正確的維度*</span><span class="sxs-lookup"><span data-stu-id="ecd8b-182">*Sharp text rendering quality with proper dimension*</span></span>

## <a name="shader-with-occlusion-support"></a><span data-ttu-id="ecd8b-183">阻擋支援的著色器</span><span class="sxs-lookup"><span data-stu-id="ecd8b-183">Shader with occlusion support</span></span>

<span data-ttu-id="ecd8b-184">Unity 的預設字型材質不支援會受阻擋。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-184">Unity's default font material does not support occlusion.</span></span> <span data-ttu-id="ecd8b-185">因為這個緣故，您會看到的文字物件後面預設。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-185">Because of this, you will see the text behind the objects by default.</span></span> <span data-ttu-id="ecd8b-186">我們已包含簡單[著色器，支援會受阻擋](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/Text3DShader.shader)。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-186">We have included a simple [shader that supports the occlusion](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/Text3DShader.shader).</span></span> <span data-ttu-id="ecd8b-187">下圖顯示 （左邊） 的預設字型資料的文字和具有適當的阻擋物 （右） 的文字。</span><span class="sxs-lookup"><span data-stu-id="ecd8b-187">The image below shows the text with default font material (left) and the text with proper occlusion (right).</span></span>

<span data-ttu-id="ecd8b-188">![阻擋支援的著色器](images/hug-text-07-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="ecd8b-188">![Shader with occlusion support](images/hug-text-07-1000px.png)</span></span><br>
<span data-ttu-id="ecd8b-189">*阻擋支援的著色器*</span><span class="sxs-lookup"><span data-stu-id="ecd8b-189">*Shader with occlusion support*</span></span>


## <a name="see-also"></a><span data-ttu-id="ecd8b-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ecd8b-190">See also</span></span>
* [<span data-ttu-id="ecd8b-191">在 MRTK 文字 Prefab</span><span class="sxs-lookup"><span data-stu-id="ecd8b-191">Text Prefab in the MRTK</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)
* [<span data-ttu-id="ecd8b-192">印刷樣式</span><span class="sxs-lookup"><span data-stu-id="ecd8b-192">Typography</span></span>](typography.md)

 
