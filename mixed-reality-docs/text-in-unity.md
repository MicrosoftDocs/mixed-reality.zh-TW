---
title: 在 Unity 中的文字
description: 若要在 Unity 中顯示文字，有兩種類型的文字元件，您可以使用-UI 文字和 3D 文字網狀結構。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，設計、 控制項、 字型、 印刷樣式、 ui、 ux
ms.openlocfilehash: 02f282ab80a44190d21d2dadefeb7a624c862d04
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596362"
---
# <a name="text-in-unity"></a><span data-ttu-id="4a201-104">在 Unity 中的文字</span><span class="sxs-lookup"><span data-stu-id="4a201-104">Text in Unity</span></span>

<span data-ttu-id="4a201-105">文字可以是其中一個最重要的元件，在全像攝影版的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="4a201-105">Text is one of the most important components in holographic apps.</span></span> <span data-ttu-id="4a201-106">若要在 Unity 中顯示文字，有兩種類型的文字元件，您可以使用-UI 文字和 3D 文字網狀結構。</span><span class="sxs-lookup"><span data-stu-id="4a201-106">To display text in Unity, there are two types of text components you can use — UI Text and 3D Text Mesh.</span></span> <span data-ttu-id="4a201-107">依預設它們看起來是模糊且太大。</span><span class="sxs-lookup"><span data-stu-id="4a201-107">By default they appear blurry and are too big.</span></span> <span data-ttu-id="4a201-108">您需要調整幾個變數，以取得明確的高品質文字 HoloLens 中具有可管理的大小。</span><span class="sxs-lookup"><span data-stu-id="4a201-108">You need to tweak a few variables to get sharp, high-quality text that has a manageable size in HoloLens.</span></span> <span data-ttu-id="4a201-109">藉由套用縮放比例，以取得適當的維度，使用 UI 文字和 3D 文字 Mesh 的元件時，您可以達到更好的呈現品質。</span><span class="sxs-lookup"><span data-stu-id="4a201-109">By applying scaling factor to get proper dimensions when using the UI Text and 3D Text Mesh components, you can achieve better rendering quality.</span></span>

<span data-ttu-id="4a201-110">![如何取得聰明又美觀的文字](images/hug-text-02-640px.png)</span><span class="sxs-lookup"><span data-stu-id="4a201-110">![How to get sharp and beautiful text](images/hug-text-02-640px.png)</span></span><br>
<span data-ttu-id="4a201-111">*在 Unity 中的模糊的預設文字*</span><span class="sxs-lookup"><span data-stu-id="4a201-111">*Blurry default text in Unity*</span></span>

## <a name="working-with-fonts-in-unity"></a><span data-ttu-id="4a201-112">使用 Unity 中的字型</span><span class="sxs-lookup"><span data-stu-id="4a201-112">Working with fonts in Unity</span></span>

<span data-ttu-id="4a201-113">Unity 假設所有新增至場景的新項目 1 中的大小或 100%轉換小數位數，會轉譯為大約 1 公尺 HoloLens 上的 Unity 單位。</span><span class="sxs-lookup"><span data-stu-id="4a201-113">Unity assumes all new elements added to a scene are 1 Unity Unit in size, or 100% transform scale, which translates to about 1 meter on HoloLens.</span></span> <span data-ttu-id="4a201-114">如果字型是週框方塊 3D TextMesh 隨附的預設位置的高度大約 1 公尺。</span><span class="sxs-lookup"><span data-stu-id="4a201-114">In the case of fonts, the bounding box for a 3D TextMesh comes in by default at about 1 meter in height.</span></span>

<span data-ttu-id="4a201-115">![使用 Unity 中的字型](images/640px-hug-text-03.png)</span><span class="sxs-lookup"><span data-stu-id="4a201-115">![Working with Fonts in Unity](images/640px-hug-text-03.png)</span></span><br>
<span data-ttu-id="4a201-116">*預設 Unity 文字佔用 1 Unity 單位為 1 公尺*</span><span class="sxs-lookup"><span data-stu-id="4a201-116">*Default Unity text occupies 1 Unity Unit which is 1 meter*</span></span>

<br>
<span data-ttu-id="4a201-117">大部分的視覺化設計工具會使用點來定義真實世界中的字型大小。</span><span class="sxs-lookup"><span data-stu-id="4a201-117">Most visual designers use points to define font sizes in the real world.</span></span> <span data-ttu-id="4a201-118">有大約 2835 (2,834.645666399962) 在 1 公尺的點。</span><span class="sxs-lookup"><span data-stu-id="4a201-118">There are about 2835 (2,834.645666399962) points in 1 meter.</span></span> <span data-ttu-id="4a201-119">根據點系統轉換為 1 公尺和 Unity 的預設文字 Mesh 字型大小為 13，13 除以 2835年等於 0.0046 (0.004586111116 很精確) 的簡單數學運算提供良好的標準擴展開始 （部分可能會想要為 0.005 捨入）。</span><span class="sxs-lookup"><span data-stu-id="4a201-119">Based on the point system conversion to 1 meter and Unity's default Text Mesh font size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) provides a good standard scale to start with (some may wish to round to 0.005).</span></span> <span data-ttu-id="4a201-120">調整文字物件或為這些值的容器不會只允許 1 對 1 轉換字型的大小在設計程式中，但也提供一種標準，讓您可以維護整個應用程式或遊戲的一致性。</span><span class="sxs-lookup"><span data-stu-id="4a201-120">Scaling the text object or container to these values will not only allow for the 1:1 conversion of font sizes in a design program, but also provides a standard so you can maintain consistency throughout your application or game.</span></span>

<span data-ttu-id="4a201-121">![Unity 3D 文字網格不同的字型大小](images/hug-text-05-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="4a201-121">![Unity 3D Text Mesh with different font sizes](images/hug-text-05-1000px.png)</span></span><br>
<span data-ttu-id="4a201-122">*Unity 3D 文字網格最佳化的值*</span><span class="sxs-lookup"><span data-stu-id="4a201-122">*Unity 3D Text Mesh with optimized values*</span></span>

<br>
<span data-ttu-id="4a201-123">當將 UI 或畫布的基礎的文字項目新增至場景，大小差異大於仍是。</span><span class="sxs-lookup"><span data-stu-id="4a201-123">When adding a UI or canvas based text element to a scene, the size disparity is greater still.</span></span> <span data-ttu-id="4a201-124">在這兩個大小的差異是大約 1000年%，這會將縮放比例 0.00046 (0.0004586111116 很精確) 基礎的 UI 文字元件或超過 0.0005 的捨入的值。</span><span class="sxs-lookup"><span data-stu-id="4a201-124">The differences in the two sizes is about 1000%, which would bring the scale factor for UI based text components to 0.00046 (0.0004586111116 to be exact) or 0.0005 for the rounded value.</span></span>

<span data-ttu-id="4a201-125">![使用不同的動態像素，每個單位值的 unity UI 文字](images/hug-text-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="4a201-125">![Unity UI Text with different dynamic pixels per unit values](images/hug-text-04-1000px.png)</span></span><br>
<span data-ttu-id="4a201-126">*Unity UI 文字，以最佳化的值*</span><span class="sxs-lookup"><span data-stu-id="4a201-126">*Unity UI Text with optimized values*</span></span>

<br>

>[!NOTE]
><span data-ttu-id="4a201-127">任何字型的預設值可能會受到該字型或字型如何匯入至 Unity 的紋理大小。</span><span class="sxs-lookup"><span data-stu-id="4a201-127">The default value of any font may be affected by the texture size of that font or how the font was imported into Unity.</span></span> <span data-ttu-id="4a201-128">這些測試所據以執行在 Unity 中的預設新細明體字型，以及其他匯入的一種字型。</span><span class="sxs-lookup"><span data-stu-id="4a201-128">These tests were performed based on the default Arial font in Unity, as well as one other imported font.</span></span>

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a><span data-ttu-id="4a201-129">明確的文字呈現品質與正確的維度</span><span class="sxs-lookup"><span data-stu-id="4a201-129">Sharp text rendering quality with proper dimension</span></span>

<span data-ttu-id="4a201-130">根據這些縮放係數，我們建立了[兩個 prefabs-UI 文字和 3D 文字 Mesh](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Prefabs)。</span><span class="sxs-lookup"><span data-stu-id="4a201-130">Based on these scaling factors, we have created [two prefabs - UI Text and 3D Text Mesh](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Prefabs).</span></span> <span data-ttu-id="4a201-131">開發人員可以使用這些 prefabs，以取得明確的文字和一致的字型大小。</span><span class="sxs-lookup"><span data-stu-id="4a201-131">Developers can use these prefabs to get sharp text and consistent font size.</span></span>

<span data-ttu-id="4a201-132">![明確的文字呈現品質與正確的維度](images/hug-text-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="4a201-132">![Sharp text rendering quality with proper dimension](images/hug-text-06-1000px.png)</span></span><br>
<span data-ttu-id="4a201-133">*明確的文字呈現品質與正確的維度*</span><span class="sxs-lookup"><span data-stu-id="4a201-133">*Sharp text rendering quality with proper dimension*</span></span>

## <a name="shader-with-occlusion-support"></a><span data-ttu-id="4a201-134">阻擋支援的著色器</span><span class="sxs-lookup"><span data-stu-id="4a201-134">Shader with occlusion support</span></span>

<span data-ttu-id="4a201-135">Unity 的預設字型材質不支援會受阻擋。</span><span class="sxs-lookup"><span data-stu-id="4a201-135">Unity's default font material does not support occlusion.</span></span> <span data-ttu-id="4a201-136">因為這個緣故，您會看到的文字物件後面預設。</span><span class="sxs-lookup"><span data-stu-id="4a201-136">Because of this, you will see the text behind the objects by default.</span></span> <span data-ttu-id="4a201-137">我們已包含簡單[著色器，支援會受阻擋](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Shaders)。</span><span class="sxs-lookup"><span data-stu-id="4a201-137">We have included a simple [shader that supports the occlusion](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Shaders).</span></span> <span data-ttu-id="4a201-138">下圖顯示 （左邊） 的預設字型資料的文字和具有適當的阻擋物 （右） 的文字。</span><span class="sxs-lookup"><span data-stu-id="4a201-138">The image below shows the text with default font material (left) and the text with proper occlusion (right).</span></span>

<span data-ttu-id="4a201-139">![阻擋支援的著色器](images/hug-text-07-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="4a201-139">![Shader with occlusion support](images/hug-text-07-1000px.png)</span></span><br>
<span data-ttu-id="4a201-140">*阻擋支援的著色器*</span><span class="sxs-lookup"><span data-stu-id="4a201-140">*Shader with occlusion support*</span></span>

## <a name="recommended-type-size"></a><span data-ttu-id="4a201-141">建議的類型大小</span><span class="sxs-lookup"><span data-stu-id="4a201-141">Recommended type size</span></span>

<span data-ttu-id="4a201-142">您可能已經想到，我們使用電腦或平板電腦裝置 （通常在 12 – 產生 32pt) 之間的類型大小的 2 公尺的距離看變得很小。</span><span class="sxs-lookup"><span data-stu-id="4a201-142">As you can expect, type sizes that we use on a PC or a tablet device (typically between 12–32pt) look quite small at a distance of 2 meters.</span></span> <span data-ttu-id="4a201-143">這取決於每個字型的特性，但在一般情況下建議最小的類型大小，以利閱讀筆劃振動不在於 30pt，根據上面介紹的縮放比例。</span><span class="sxs-lookup"><span data-stu-id="4a201-143">It depends on the characteristics of each font, but in general the recommended minimum type size for legibility without stroke vibration is around 30pt, based on the scaling factor introduced above.</span></span> <span data-ttu-id="4a201-144">如果您的應用程式應該使用更接近的距離，就可以使用較小的類型大小。</span><span class="sxs-lookup"><span data-stu-id="4a201-144">If your app is supposed to be used at a closer distance, smaller type sizes could be used.</span></span> <span data-ttu-id="4a201-145">字型選擇功能，Segoe UI （Windows 的預設字型） 非常適合大部分情況。</span><span class="sxs-lookup"><span data-stu-id="4a201-145">For the font selection, Segoe UI (the default font for Windows) works well in most cases.</span></span> <span data-ttu-id="4a201-146">不過，請避免使用 light 或半淺色字型 42pt 之下的類型大小，因為將震動精簡型的垂直筆劃，而且它會降低易讀性。</span><span class="sxs-lookup"><span data-stu-id="4a201-146">However, avoid using light or semi light fonts for type sizes under 42pt since thin vertical strokes will vibrate and it will degrade the legibility.</span></span> <span data-ttu-id="4a201-147">新式的字型，具有足夠的筆劃粗細正常運作。</span><span class="sxs-lookup"><span data-stu-id="4a201-147">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="4a201-148">比方說，新細明體新細明體看起來美觀和 HoloLens 中使用規則或粗體加權非常清晰。</span><span class="sxs-lookup"><span data-stu-id="4a201-148">For example, Helvetica and Arial look gorgeous and are very legible in HoloLens with regular or bold weights.</span></span>

<span data-ttu-id="4a201-149">![建議的類型大小](images/hug-text-08-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="4a201-149">![Recommended type size](images/hug-text-08-1000px.png)</span></span><br>
<span data-ttu-id="4a201-150">*型別 ramp 範例*</span><span class="sxs-lookup"><span data-stu-id="4a201-150">*Type ramp example*</span></span>

## <a name="see-also"></a><span data-ttu-id="4a201-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a201-151">See also</span></span>
* [<span data-ttu-id="4a201-152">在 MixedRealityToolkit 文字 Prefab</span><span class="sxs-lookup"><span data-stu-id="4a201-152">Text Prefab in the MixedRealityToolkit</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Prefabs)
* [<span data-ttu-id="4a201-153">Prefab 的範例文字版面配置和場景</span><span class="sxs-lookup"><span data-stu-id="4a201-153">Sample text layout prefab and scene</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX/Scenes)
* [<span data-ttu-id="4a201-154">Typography</span><span class="sxs-lookup"><span data-stu-id="4a201-154">Typography</span></span>](typography.md)

 
