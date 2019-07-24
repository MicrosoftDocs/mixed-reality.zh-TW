---
title: 案例研究-在不同效能的裝置上調整 Datascape
description: 此案例研究可讓您深入瞭解 Microsoft 開發人員如何將 Datascape 應用程式優化, 以透過各種效能功能, 在裝置之間提供引人注目的體驗。
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 沉浸式耳機、效能優化、VR、案例研究
ms.openlocfilehash: 990a5ee6de07b6416e3150a7885220409a9c8d93
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63523364"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a><span data-ttu-id="ce1fb-104">案例研究-在不同效能的裝置上調整 Datascape</span><span class="sxs-lookup"><span data-stu-id="ce1fb-104">Case study - Scaling Datascape across devices with different performance</span></span>

<span data-ttu-id="ce1fb-105">Datascape 是 Microsoft 內部開發的 Windows Mixed Reality 應用程式, 我們將焦點放在在地形資料上顯示天氣資料。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-105">Datascape is a Windows Mixed Reality application developed internally at Microsoft where we focused on displaying weather data on top of terrain data.</span></span> <span data-ttu-id="ce1fb-106">應用程式會藉由將使用者與全像攝影資料視覺效果括住, 探索使用者在混合現實中探索資料所獲得的獨特見解。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-106">The application explores the unique insights users gain from discovering data in mixed reality by surrounding the user with holographic data visualization.</span></span>

<span data-ttu-id="ce1fb-107">針對 Datascape, 我們想要以各種不同的平臺為目標, 包括從 Microsoft HoloLens 到 Windows Mixed Reality 的沉浸式耳機, 以及從低電源的電腦到具有高階 GPU 的最新電腦。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-107">For Datascape we wanted to target a variety of platforms with different hardware capabilities ranging from Microsoft HoloLens to Windows Mixed Reality immersive headsets, and from lower-powered PCs to the very latest PCs with high-end GPU.</span></span> <span data-ttu-id="ce1fb-108">主要的挑戰是以視覺上吸引人的方式來呈現場景, 而這些裝置的圖形功能截然不同, 同時以高幀的速度執行。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-108">The main challenge was rendering our scene in a visually appealing matter on devices with wildly different graphics capabilities while executing at a high framerate.</span></span>

<span data-ttu-id="ce1fb-109">此案例研究將逐步解說用來建立一些較多 GPU 密集型系統的程式和技術, 並說明我們遇到的問題以及如何克服了它們。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-109">This case study will walk through the process and techniques used to create some of our more GPU-intensive systems, describing the problems we encountered and how we overcame them.</span></span>

## <a name="transparency-and-overdraw"></a><span data-ttu-id="ce1fb-110">透明度和過度繪製</span><span class="sxs-lookup"><span data-stu-id="ce1fb-110">Transparency and overdraw</span></span>

<span data-ttu-id="ce1fb-111">我們的主要轉譯掙扎會處理透明度, 因為透明度在 GPU 上可能會耗用大量資源。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-111">Our main rendering struggles dealt with transparency, since transparency can be expensive on a GPU.</span></span>

<span data-ttu-id="ce1fb-112">在寫入深度緩衝區時, 可以將固定幾何向前轉譯, 以停止捨棄該圖元背後的任何未來圖元。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-112">Solid geometry can be rendered front to back while writing to the depth buffer, stopping any future pixels located behind that pixel from being discarded.</span></span> <span data-ttu-id="ce1fb-113">這可避免隱藏圖元執行圖元著色器, 並大幅加快進程的速度。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-113">This prevents hidden pixels from executing the pixel shader, speeding up the process significantly.</span></span> <span data-ttu-id="ce1fb-114">如果幾何是以最佳方式排序, 螢幕上的每個圖元只會繪製一次。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-114">If geometry is sorted optimally, each pixel on the screen will be drawn only once.</span></span>

<span data-ttu-id="ce1fb-115">透明幾何必須重新排序回到 front, 而且需要將圖元著色器的輸出與螢幕上的目前圖元進行混合。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-115">Transparent geometry needs to be sorted back to front and relies on blending the output of the pixel shader to the current pixel on the screen.</span></span> <span data-ttu-id="ce1fb-116">這可能會導致畫面上每個圖元繪製到每個畫面格多次, 稱為過度繪製。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-116">This can result in each pixel on the screen being drawn to multiple times per frame, referred to as overdraw.</span></span>

<span data-ttu-id="ce1fb-117">若是 HoloLens 和主流電腦, 畫面只會填滿幾次, 使透明呈現有問題。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-117">For HoloLens and mainstream PCs, the screen can only be filled a handful of times, making transparent rendering problematic.</span></span>

## <a name="introduction-to-datascape-scene-components"></a><span data-ttu-id="ce1fb-118">Datascape 場景元件簡介</span><span class="sxs-lookup"><span data-stu-id="ce1fb-118">Introduction to Datascape scene components</span></span>

<span data-ttu-id="ce1fb-119">我們的場景有三個主要元件;**UI、地圖**和**天氣**。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-119">We had three major components to our scene; **the UI, the map**, and **the weather**.</span></span> <span data-ttu-id="ce1fb-120">我們及早知道我們的氣象效應需要所有的 GPU 時間, 因此我們刻意以減少任何過度繪製的方式設計 UI 和地形。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-120">We knew early on that our weather effects would require all the GPU time it could get, so we purposely designed the UI and terrain in a way that would reduce any overdraw.</span></span>

<span data-ttu-id="ce1fb-121">我們已將 UI 改編數次, 以將所產生的過度繪製量降到最低。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-121">We reworked the UI several times to minimize the amount of overdraw it would produce.</span></span> <span data-ttu-id="ce1fb-122">我們會在更複雜的幾何端大錯特錯人, 而不是針對發光按鈕和地圖總覽等元件, 將透明的圖案疊加在彼此之上。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-122">We erred on the side of more complex geometry rather than overlaying transparent art on top of each other for components like glowing buttons and map overviews.</span></span>

<span data-ttu-id="ce1fb-123">針對地圖, 我們使用自訂著色器來去除標準 Unity 功能 (例如陰影和複雜光源), 以簡單的單一 sun 光源模型和自訂的霧化計算來取代它們。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-123">For the map, we used a custom shader that would strip out standard Unity features such as shadows and complex lighting, replacing them with a simple single sun lighting model and a custom fog calculation.</span></span> <span data-ttu-id="ce1fb-124">這會產生簡單的圖元著色器, 並釋放 GPU 週期。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-124">This produced a simple pixel shader and free up GPU cycles.</span></span>

<span data-ttu-id="ce1fb-125">我們設法讓 UI 和地圖在預算中呈現, 而不需要對它們進行任何變更 (視硬體而定)。不過, 氣象視覺效果 (尤其是雲端轉譯) 證明是一項挑戰!</span><span class="sxs-lookup"><span data-stu-id="ce1fb-125">We managed to get both the UI and the map to rendering at budget where we did not need any changes to them depending on the hardware; however, the weather visualization, in particular the cloud rendering, proved to be more of a challenge!</span></span>

## <a name="background-on-cloud-data"></a><span data-ttu-id="ce1fb-126">雲端資料的背景</span><span class="sxs-lookup"><span data-stu-id="ce1fb-126">Background on cloud data</span></span>

<span data-ttu-id="ce1fb-127">我們的雲端資料是從 NOAA 伺服器下載 http://nomads.ncep.noaa.gov/) (並以三個不同的2d 層來提供, 每個都有雲端的上而下高度), 以及格線的每個資料格的雲端密度。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-127">Our cloud data was downloaded from NOAA servers (http://nomads.ncep.noaa.gov/) and came to us in three distinct 2D layers, each with the top and bottom height of the cloud, as well as the density of the cloud for each cell of the grid.</span></span> <span data-ttu-id="ce1fb-128">資料已處理到雲端資訊材質, 其中每個元件都儲存在材質的紅色、綠色和藍色元件中, 以便在 GPU 上輕鬆存取。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-128">The data got processed into a cloud info texture where each component was stored in the red, green, and blue component of the texture for easy access on the GPU.</span></span>

## <a name="geometry-clouds"></a><span data-ttu-id="ce1fb-129">Geometry 雲端</span><span class="sxs-lookup"><span data-stu-id="ce1fb-129">Geometry clouds</span></span>

<span data-ttu-id="ce1fb-130">為了確保我們的低電源機器可以轉譯我們的雲端, 我們決定從使用固態幾何來將過度繪製降至最低的方法開始。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-130">To make sure our lower-powered machines could render our clouds we decided to start with an approach that would use solid geometry to minimize overdraw.</span></span>

<span data-ttu-id="ce1fb-131">我們先嘗試產生雲端, 方法是使用每個頂點的雲端資訊材質半徑來產生圖形, 為每個圖層產生一個穩固的 heightmap 網格。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-131">We first tried producing clouds by generating a solid heightmap mesh for each layer using the radius of the cloud info texture per vertex to generate the shape.</span></span> <span data-ttu-id="ce1fb-132">我們使用了幾何著色器, 在雲端產生穩固的雲端圖形時, 同時在其上方和底部產生頂點。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-132">We used a geometry shader to produce the vertices both at the top and the bottom of the cloud generating solid cloud shapes.</span></span> <span data-ttu-id="ce1fb-133">我們使用材質的密度值, 以較高的雲端色彩來為雲端著色。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-133">We used the density value from the texture to color the cloud with darker colors for more dense clouds.</span></span>

<span data-ttu-id="ce1fb-134">**用於建立頂點的著色器:**</span><span class="sxs-lookup"><span data-stu-id="ce1fb-134">**Shader for creating the vertices:**</span></span>

```
v2g vert (appdata v)
{
    v2g o;
    o.height = tex2Dlod(_MainTex, float4(v.uv, 0, 0)).x;
    o.vertex = v.vertex;
    return o;
}
 
g2f GetOutput(v2g input, float heightDirection)
{
    g2f ret;
    float4 newBaseVert = input.vertex;
    newBaseVert.y += input.height * heightDirection * _HeigthScale;
    ret.vertex = UnityObjectToClipPos(newBaseVert);
    ret.height = input.height;
    return ret;
}
 
[maxvertexcount(6)]
void geo(triangle v2g p[3], inout TriangleStream<g2f> triStream)
{
    float heightTotal = p[0].height + p[1].height + p[2].height;
    if (heightTotal > 0)
    {
        triStream.Append(GetOutput(p[0], 1));
        triStream.Append(GetOutput(p[1], 1));
        triStream.Append(GetOutput(p[2], 1));
 
        triStream.RestartStrip();
 
        triStream.Append(GetOutput(p[2], -1));
        triStream.Append(GetOutput(p[1], -1));
        triStream.Append(GetOutput(p[0], -1));
    }
}
fixed4 frag (g2f i) : SV_Target
{
    clip(i.height - 0.1f);
 
    float3 finalColor = lerp(_LowColor, _HighColor, i.height);
    return float4(finalColor, 1);
}
```

<span data-ttu-id="ce1fb-135">我們引進了一個小型的雜訊模式, 以取得實際資料的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-135">We introduced a small noise pattern to get more detail on top of the real data.</span></span> <span data-ttu-id="ce1fb-136">若要產生圓角的雲端邊緣, 我們會在插入半徑值達到閾值以捨棄接近零的值時, 裁剪圖元著色器中的圖元。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-136">To produce round cloud edges, we clipped the pixels in the pixel shader when the interpolated radius value hit a threshold to discard near-zero values.</span></span>

![Geometry 雲端](images/datascape-geometry-clouds-700px.jpg)

<span data-ttu-id="ce1fb-138">由於雲端是穩固的幾何, 因此可以在地形之前轉譯, 以隱藏下任何昂貴的地圖圖元, 以進一步改善畫面播放速率。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-138">Since the clouds are solid geometry, they can be rendered before the terrain to hide any expensive map pixels underneath to further improve framerate.</span></span> <span data-ttu-id="ce1fb-139">此解決方案適用于從最小規格到高階圖形配接器的所有圖形配接器, 以及 HoloLens, 因為其為固態幾何轉譯方法。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-139">This solution ran well on all graphics cards from min-spec to high-end graphics cards, as well as on HoloLens, because of the solid geometry rendering approach.</span></span>

## <a name="solid-particle-clouds"></a><span data-ttu-id="ce1fb-140">實心物件雲端</span><span class="sxs-lookup"><span data-stu-id="ce1fb-140">Solid particle clouds</span></span>

<span data-ttu-id="ce1fb-141">我們現在有一個備份解決方案, 它會產生適當的雲端資料標記法, 但在「wow」因素中有點 lackluster, 而且不會針對我們的高階機器傳達所需的體積型風格。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-141">We now had a backup solution that produced a decent representation of our cloud data, but was a bit lackluster in the “wow” factor and did not convey the volumetric feel that we wanted for our high-end machines.</span></span>

<span data-ttu-id="ce1fb-142">我們的下一步是以大約100000的粒子來建立雲端, 以產生更具有機和體積型的外觀。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-142">Our next step was creating the clouds by representing them with approximately 100,000 particles to produce a more organic and volumetric look.</span></span>

<span data-ttu-id="ce1fb-143">如果粒子保持不變, 並在前端進行排序, 我們仍然可以受益于先前轉譯之粒子背後圖元的深度緩衝區剔除, 以減少過度繪製。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-143">If particles stay solid and sort front-to-back, we can still benefit from depth buffer culling of the pixels behind previously rendered particles, reducing the overdraw.</span></span> <span data-ttu-id="ce1fb-144">此外, 使用以物件為基礎的解決方案時, 我們可以改變用來以不同硬體為目標的粒子量。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-144">Also, with a particle-based solution, we can alter the amount of particles used to target different hardware.</span></span> <span data-ttu-id="ce1fb-145">不過, 所有圖元仍然需要深度測試, 這會導致一些額外的負荷。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-145">However, all pixels still need to be depth tested, which results in some additional overhead.</span></span>

<span data-ttu-id="ce1fb-146">首先, 我們在啟動時, 建立了在經驗中心點周圍的物件位置。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-146">First, we created particle positions around the center point of the experience at startup.</span></span> <span data-ttu-id="ce1fb-147">我們在中心前後散佈了密集, 而不是距離。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-147">We distributed the particles more densely around the center and less so in the distance.</span></span> <span data-ttu-id="ce1fb-148">我們已預先排序從中心到後的所有粒子, 讓最接近的粒子先呈現。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-148">We pre-sorted all particles from the center to the back so that the closest particles would render first.</span></span>

<span data-ttu-id="ce1fb-149">計算著色器會取樣雲端資訊材質, 以正確的高度定位每個物件, 並根據密度來加以色彩。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-149">A compute shader would sample the cloud info texture to position each particle at a correct height and color it based on the density.</span></span>

<span data-ttu-id="ce1fb-150">我們使用*DrawProcedural*來轉譯每個物件四個, 讓物件資料隨時保持在 GPU 上。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-150">We used *DrawProcedural* to render a quad per particle allowing the particle data to stay on the GPU at all times.</span></span>

<span data-ttu-id="ce1fb-151">每個物件都包含高度和半徑。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-151">Each particle contained both a height and a radius.</span></span> <span data-ttu-id="ce1fb-152">高度是以雲端資訊材質取樣的雲端資料為基礎, 而半徑是根據初始分佈, 其計算方式是將水準距離儲存至其最近的鄰近位置。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-152">The height was based on the cloud data sampled from the cloud info texture, and the radius was based on the initial distribution where it would be calculated to store the horizontal distance to its closest neighbor.</span></span> <span data-ttu-id="ce1fb-153">四邊形會使用這項資料, 將其本身設為高度的角度, 讓使用者能以水準方式查看, 高度會顯示出來, 而當使用者從上而下查看時, 會涵蓋其鄰近專案之間的區域。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-153">The quads would use this data to orient itself angled by the height so that when users look at it horizontally, the height would be shown, and when users looked at it top-down, the area between its neighbors would be covered.</span></span>

![物件圖形](images/particle-shape-700px.png)

<span data-ttu-id="ce1fb-155">**顯示分佈的著色器程式碼:**</span><span class="sxs-lookup"><span data-stu-id="ce1fb-155">**Shader code showing the distribution:**</span></span>

```
ComputeBuffer cloudPointBuffer = new ComputeBuffer(6, quadPointsStride);
cloudPointBuffer.SetData(new[]
{
    new Vector2(-.5f, .5f),
    new Vector2(.5f, .5f),
    new Vector2(.5f, -.5f),
    new Vector2(.5f, -.5f),
    new Vector2(-.5f, -.5f),
    new Vector2(-.5f, .5f)
});
 
StructuredBuffer<float2> quadPoints;
StructuredBuffer<float3> particlePositions;
v2f vert(uint id : SV_VertexID, uint inst : SV_InstanceID)
{
    // Find the center of the quad, from local to world space
    float4 centerPoint = mul(unity_ObjectToWorld, float4(particlePositions[inst], 1));
 
    // Calculate y offset for each quad point
    float3 cameraForward = normalize(centerPoint - _WorldSpaceCameraPos);
    float y = dot(quadPoints[id].xy, cameraForward.xz);
 
    // Read out the particle data
    float radius = ...;
    float height = ...;
 
    // Set the position of the vert
    float4 finalPos = centerPoint + float4(quadPoints[id].x, y * height, quadPoints[id].y, 0) * radius;
    o.pos = mul(UNITY_MATRIX_VP, float4(finalPos.xyz, 1));
    o.uv = quadPoints[id].xy + 0.5;
 
    return o;
}
```

<span data-ttu-id="ce1fb-156">由於我們會將粒子向前排序, 而且我們仍使用純色著色器來裁剪 (而不是 blend) 透明圖元, 因此這項技術會處理驚人的粒子量, 即使在較低的電腦上, 也能避免昂貴的過度繪製。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-156">Since we sort the particles front-to-back and we still used a solid style shader to clip (not blend) transparent pixels, this technique handles a surprising amount of particles, avoiding costly over-draw even on the lower-powered machines.</span></span>

## <a name="transparent-particle-clouds"></a><span data-ttu-id="ce1fb-157">透明的物件雲端</span><span class="sxs-lookup"><span data-stu-id="ce1fb-157">Transparent particle clouds</span></span>

<span data-ttu-id="ce1fb-158">穩固的微粒為雲端的形狀提供了良好的有機風格, 但仍需要銷售雲端 fluffiness 的東西。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-158">The solid particles provided a good organic feel to the shape of the clouds but still needed something to sell the fluffiness of clouds.</span></span> <span data-ttu-id="ce1fb-159">我們決定針對可引進透明度的高階圖形配接器嘗試自訂解決方案。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-159">We decided to try a custom solution for the high-end graphics cards where we can introduce transparency.</span></span>

<span data-ttu-id="ce1fb-160">為了這麼做, 我們只是切換了粒子的初始排序次序, 並將著色器變更為使用材質 Alpha。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-160">To do this we simply switched the initial sorting order of the particles and changed the shader to use the textures alpha.</span></span>

![Fluffy 雲端](images/fluffy-clouds-700px.jpg)

<span data-ttu-id="ce1fb-162">它看起來很棒, 但證明即使是最棘手的機器, 也是太大, 因為這會導致螢幕上的每個圖元呈現數百次!</span><span class="sxs-lookup"><span data-stu-id="ce1fb-162">It looked great but proved to be too heavy for even the toughest machines since it would result in rendering each pixel on the screen hundreds of times!</span></span>

## <a name="render-off-screen-with-lower-resolution"></a><span data-ttu-id="ce1fb-163">以較低解析度呈現螢幕上的</span><span class="sxs-lookup"><span data-stu-id="ce1fb-163">Render off-screen with lower resolution</span></span>

<span data-ttu-id="ce1fb-164">為了減少雲端所轉譯的圖元數, 我們開始將它們呈現在四分之一解析度緩衝區中 (與螢幕相較之下), 並在繪製所有的微粒之後, 將最後的結果延展到螢幕上。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-164">To reduce the number of pixels rendered by the clouds, we started rendering them in a quarter resolution buffer (compared to the screen) and stretching the end result back up onto the screen after all the particles had been drawn.</span></span> <span data-ttu-id="ce1fb-165">這讓我們達到4倍的速度, 但有幾個注意事項。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-165">This gave us roughly a 4x speedup, but came with a couple of caveats.</span></span>

<span data-ttu-id="ce1fb-166">**以畫面呈現的程式碼:**</span><span class="sxs-lookup"><span data-stu-id="ce1fb-166">**Code for rendering off-screen:**</span></span>

```
cloudBlendingCommand = new CommandBuffer();
Camera.main.AddCommandBuffer(whenToComposite, cloudBlendingCommand);
 
cloudCamera.CopyFrom(Camera.main);
cloudCamera.rect = new Rect(0, 0, 1, 1);    //Adaptive rendering can set the main camera to a smaller rect
cloudCamera.clearFlags = CameraClearFlags.Color;
cloudCamera.backgroundColor = new Color(0, 0, 0, 1);
 
currentCloudTexture = RenderTexture.GetTemporary(Camera.main.pixelWidth / 2, Camera.main.pixelHeight / 2, 0);
cloudCamera.targetTexture = currentCloudTexture;
 
// Render clouds to the offscreen buffer
cloudCamera.Render();
cloudCamera.targetTexture = null;
 
// Blend low-res clouds to the main target
cloudBlendingCommand.Blit(currentCloudTexture, new RenderTargetIdentifier(BuiltinRenderTextureType.CurrentActive), blitMaterial);
```

<span data-ttu-id="ce1fb-167">第一, 當轉譯成非螢幕緩衝區時, 我們會遺失主要場景的所有深度資訊, 導致山脈呈現在山地之上。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-167">First, when rendering into an off-screen buffer, we lost all depth information from our main scene, resulting in particles behind mountains rendering on top of the mountain.</span></span>

<span data-ttu-id="ce1fb-168">第二, 延伸緩衝區也會在我們的雲端邊緣導入的構件, 其中的解決方式變更很明顯。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-168">Second, stretching the buffer also introduced artifacts on the edges of our clouds where the resolution change was noticeable.</span></span> <span data-ttu-id="ce1fb-169">接下來的兩節將討論如何解決這些問題。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-169">The next two sections talk about how we resolved these issues.</span></span>

## <a name="particle-depth-buffer"></a><span data-ttu-id="ce1fb-170">物件深度緩衝區</span><span class="sxs-lookup"><span data-stu-id="ce1fb-170">Particle depth buffer</span></span>

<span data-ttu-id="ce1fb-171">為了讓您的微粒與世界幾何並存, 其中的山地或物件可以涵蓋其背後的微粒, 我們以深度緩衝區擴展出螢幕緩衝區, 其中包含主要場景的幾何。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-171">To make the particles co-exist with the world geometry where a mountain or object could cover particles behind it, we populated the off-screen buffer with a depth buffer containing the geometry of the main scene.</span></span> <span data-ttu-id="ce1fb-172">為了產生這類深度緩衝區, 我們建立了第二張攝影機, 只呈現場景的穩固幾何和深度。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-172">To produce such depth buffer, we created a second camera, rendering only the solid geometry and depth of the scene.</span></span>

<span data-ttu-id="ce1fb-173">然後, 我們在雲端的圖元著色器中使用新材質來遮蔽圖元。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-173">We then used the new texture in the pixel shader of the clouds to occlude pixels.</span></span> <span data-ttu-id="ce1fb-174">我們使用相同的材質來計算雲端圖元背後幾何的距離。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-174">We used the same texture to calculate the distance to the geometry behind a cloud pixel.</span></span> <span data-ttu-id="ce1fb-175">藉由使用該距離並將其套用到圖元的 Alpha, 我們現在讓雲端的效果淡出, 因為它們接近地形, 因此會移除任何與微粒和地形符合的硬式切割。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-175">By using that distance and applying it to the alpha of the pixel, we now had the effect of clouds fading out as they get close to terrain, removing any hard cuts where particles and terrain meet.</span></span>

![混合成地形的雲端](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a><span data-ttu-id="ce1fb-177">銳化邊緣</span><span class="sxs-lookup"><span data-stu-id="ce1fb-177">Sharpening the edges</span></span>

<span data-ttu-id="ce1fb-178">向上延展的雲端看起來幾乎與位於或彼此重迭的一般大小雲端相同, 但在雲端邊緣有一些成品。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-178">The stretched-up clouds looked almost identical to the normal size clouds at the center of the particles or where they overlapped, but showed some artifacts at the cloud edges.</span></span> <span data-ttu-id="ce1fb-179">否則, 銳利邊緣會顯得模糊不清, 而且當相機移動時, 會引進別名效果。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-179">Otherwise sharp edges would appear blurry and alias effects were introduced when the camera moved.</span></span>

<span data-ttu-id="ce1fb-180">我們解決了這種情況, 方法是在非螢幕緩衝區上執行簡單的著色器, 判斷發生重大變更的情況 (1)。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-180">We solved this by running a simple shader on the off-screen buffer to determine where big changes in contrast occurred (1).</span></span> <span data-ttu-id="ce1fb-181">我們會將具有重大變更的圖元放入新的樣板緩衝區 (2)。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-181">We put the pixels with big changes into a new stencil buffer (2).</span></span> <span data-ttu-id="ce1fb-182">接著, 我們使用樣板緩衝區, 在將外螢幕緩衝區套用回螢幕時, 遮罩掉這些高對比區域, 因而導致雲端中的漏洞 (3)。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-182">We then used the stencil buffer to mask out these high contrast areas when applying the off-screen buffer back to the screen, resulting in holes in and around the clouds (3).</span></span>

<span data-ttu-id="ce1fb-183">然後, 我們會以全螢幕模式再次呈現所有的微粒, 但這次使用樣板緩衝區來遮罩邊緣以外的所有專案, 而導致最小的圖元組觸及 (4)。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-183">We then rendered all the particles again in full-screen mode, but this time used the stencil buffer to mask out everything but the edges, resulting in a minimal set of pixels touched (4).</span></span> <span data-ttu-id="ce1fb-184">由於已為粒子建立命令緩衝區, 因此我們只需要再次將它轉譯到新的相機。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-184">Since the command buffer was already created for the particles, we simply had to render it again to the new camera.</span></span>

![呈現雲端邊緣的進展](images/cloud-steps-1-4-700px.jpg)

<span data-ttu-id="ce1fb-186">最終結果是以雲端的便宜中心區段來利邊緣。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-186">The end result was sharp edges with cheap center sections of the clouds.</span></span>

<span data-ttu-id="ce1fb-187">雖然這比在全螢幕中轉譯所有的微粒快, 但仍有與針對樣板緩衝區測試圖元相關聯的成本, 因此大量的過度繪製仍會產生成本。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-187">While this was much faster than rendering all particles in full screen, there is still a cost associated with testing a pixel against the stencil buffer, so a massive amount of overdraw still came with a cost.</span></span>

## <a name="culling-particles"></a><span data-ttu-id="ce1fb-188">剔除粒子</span><span class="sxs-lookup"><span data-stu-id="ce1fb-188">Culling particles</span></span>

<span data-ttu-id="ce1fb-189">針對我們的風效果, 我們在計算著色器中產生長三角形的去除, 並在世界各地建立許多 wisps。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-189">For our wind effect, we generated long triangle strips in a compute shader, creating many wisps of wind in the world.</span></span> <span data-ttu-id="ce1fb-190">雖然由於產生訣竅的結果, 而不會對填滿率造成沉重的影響, 但它產生了數十萬個頂點, 因而導致頂點著色器的負載過重。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-190">While the wind effect was not heavy on fill rate due to skinny strips generated, it produced many hundreds of thousands of vertices resulting in a heavy load for the vertex shader.</span></span>

<span data-ttu-id="ce1fb-191">我們在計算著色器上引進了附加緩衝區, 以饋送要繪製之風的部分。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-191">We introduced append buffers on the compute shader to feed a subset of the wind strips to be drawn.</span></span> <span data-ttu-id="ce1fb-192">使用一些簡單的視圖, 在計算著色器中剔除邏輯時, 我們可以判斷帶狀是否在相機外, 並防止它加入推播緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-192">With some simple view frustum culling logic in the compute shader, we could determine if a strip was outside of camera view and prevent it from being added to the push buffer.</span></span> <span data-ttu-id="ce1fb-193">這會大幅減少分割量, 並在 GPU 上釋放一些所需的迴圈。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-193">This reduced the amount of strips significantly, freeing up some needed cycles on the GPU.</span></span>

<span data-ttu-id="ce1fb-194">**示範附加緩衝區的程式碼:**</span><span class="sxs-lookup"><span data-stu-id="ce1fb-194">**Code demonstrating an append buffer:**</span></span>

<span data-ttu-id="ce1fb-195">*計算著色器:*</span><span class="sxs-lookup"><span data-stu-id="ce1fb-195">*Compute shader:*</span></span>

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

<span data-ttu-id="ce1fb-196">*C#錯誤碼*</span><span class="sxs-lookup"><span data-stu-id="ce1fb-196">*C# code:*</span></span>

```
protected void Awake() 
{
    // Create an append buffer, setting the maximum size and the contents stride length
    culledParticlesIdxBuffer = new ComputeBuffer(ParticleCount, sizeof(int), ComputeBufferType.Append);
 
    // Set up Args Buffer for Draw Procedural Indirect
    argsBuffer = new ComputeBuffer(4, sizeof(int), ComputeBufferType.IndirectArguments);
    argsBuffer.SetData(new int[] { DataVertCount, 0, 0, 0 });
}
 
protected void Update()
{
    // Reset the append buffer, and dispatch the compute shader normally
    culledParticlesIdxBuffer.SetCounterValue(0);
 
    computer.Dispatch(...)
 
    // Copy the append buffer count into the args buffer used by the Draw Procedural Indirect call
    ComputeBuffer.CopyCount(culledParticlesIdxBuffer, argsBuffer, dstOffset: 1);
    ribbonRenderCommand.DrawProceduralIndirect(Matrix4x4.identity, renderMaterial, 0, MeshTopology.Triangles, dataBuffer);
}
```

<span data-ttu-id="ce1fb-197">我們嘗試在雲端的粒子上使用相同的技巧, 我們會在計算著色器上挑選它們, 並只推送要呈現的可見粒子。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-197">We tried using the same technique on the cloud particles, where we would cull them on the compute shader and only push the visible particles to be rendered.</span></span> <span data-ttu-id="ce1fb-198">這項技術實際上並不會在 GPU 上節省大量的空間, 因為最大的瓶頸是螢幕上呈現的圖元量, 而不是計算頂點的成本。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-198">This technique actually did not save us much on the GPU since the biggest bottleneck was the amount pixels rendered on the screen, and not the cost of calculating the vertices.</span></span>

<span data-ttu-id="ce1fb-199">這項技術的另一個問題是, 附加緩衝區會以隨機順序擴展, 因為它會平行處理其運算, 而使排序的微粒不會排序, 而導致雲端的微粒。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-199">The other problem with this technique was that the append buffer populated in random order due to its parallelized nature of computing the particles, causing the sorted particles to be un-sorted, resulting in flickering cloud particles.</span></span>

<span data-ttu-id="ce1fb-200">有一些方法可以排序推播緩衝區, 但我們從剔除的部分取得的效能提升數量可能會與其他排序有時差, 所以我們決定不採用這項優化。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-200">There are techniques to sort the push buffer, but the limited amount of performance gain we got out of culling particles would likely be offset with an additional sort, so we decided to not pursue this optimization.</span></span>

## <a name="adaptive-rendering"></a><span data-ttu-id="ce1fb-201">適應性呈現</span><span class="sxs-lookup"><span data-stu-id="ce1fb-201">Adaptive rendering</span></span>

<span data-ttu-id="ce1fb-202">為了確保在應用程式上使用不同的轉譯條件 (例如, 像是一種雲與清楚的觀點), 其呈穩定的畫面播放速率, 我們為應用程式引進了適應性轉譯</span><span class="sxs-lookup"><span data-stu-id="ce1fb-202">To ensure a steady framerate on an app with varying rendering conditions like a cloudy vs a clear view, we introduced adaptive rendering to our app.</span></span>

<span data-ttu-id="ce1fb-203">適應性轉譯的第一個步驟是測量 GPU。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-203">The first step of adaptive rendering is to measure GPU.</span></span> <span data-ttu-id="ce1fb-204">我們的做法是將自訂程式碼插入 GPU 命令緩衝區, 並在轉譯的框架開頭和結尾處, 同時捕捉左右畫面時間。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-204">We did this by inserting custom code into the GPU command buffer at the beginning and the end of a rendered frame, capturing both the left and right eye screen time.</span></span>

<span data-ttu-id="ce1fb-205">藉由測量花費在轉譯的時間, 並將其與我們所需的重新整理率進行比較, 我們就可以瞭解如何關閉畫面。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-205">By measuring the time spent rendering and comparing it to our desired refresh-rate we got a sense of how close we were to dropping frames.</span></span>

<span data-ttu-id="ce1fb-206">當關閉畫面時, 我們會調整轉譯, 讓它更快速。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-206">When close to dropping frames, we adapt our rendering to make it faster.</span></span> <span data-ttu-id="ce1fb-207">一個簡單的調整方式是變更螢幕的視口大小, 而需要較少的圖元來呈現。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-207">One simple way of adapting is changing the viewport size of the screen, requiring less pixels to get rendered.</span></span>

<span data-ttu-id="ce1fb-208">藉由使用*UnityEngine. XR. renderViewportScale* , 系統會縮小目標的視口, 並自動將結果向上調整為符合畫面。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-208">By using *UnityEngine.XR.XRSettings.renderViewportScale* the system shrinks the targeted viewport and automatically stretches the result back up to fit the screen.</span></span> <span data-ttu-id="ce1fb-209">小規模的小規模變更在世界幾何上幾乎不明顯, 而縮放比例為0.7 需要呈現一半的圖元量。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-209">A small change in scale is barely noticeable on world geometry, and a scale factor of 0.7 requires half the amount of pixels to be rendered.</span></span>

![70% 的比例, 一半的圖元](images/datascape-scaling-700px.jpg)

<span data-ttu-id="ce1fb-211">當我們偵測到我們即將捨棄畫面格時, 我們會以固定的數位來降低尺規, 並在執行得夠快時將它增加回來。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-211">When we detect that we are about to drop frames we lower the scale by a fixed number, and increase it back when we are running fast enough again.</span></span>

<span data-ttu-id="ce1fb-212">雖然我們在啟動時決定要根據硬體的圖形功能來使用哪個雲端技術, 但還是可以根據 GPU 測量的資料來避免系統長時間保持低解析度, 但這是我們沒有時間的問題 在 Datascape 中探索。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-212">While we decided what cloud technique to use based on graphics capabilities of the hardware at startup, it is possible to base it on data from the GPU measurement to prevent the system from staying at low resolution for a long time, but this is something we did not have time to explore in Datascape.</span></span>

## <a name="final-thoughts"></a><span data-ttu-id="ce1fb-213">最後的想法</span><span class="sxs-lookup"><span data-stu-id="ce1fb-213">Final thoughts</span></span>

<span data-ttu-id="ce1fb-214">以各種不同的硬體為目標是一項挑戰, 需要進行一些規劃。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-214">Targeting a variety of hardware is challenging and requires some planning.</span></span>

<span data-ttu-id="ce1fb-215">我們建議您開始以較低電源的電腦為目標, 以熟悉問題空間, 並開發將在所有電腦上執行的備份解決方案。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-215">We recommend that you start targeting lower-powered machines to get familiar with the problem space and develop a backup solution that will run on all your machines.</span></span> <span data-ttu-id="ce1fb-216">設計您的解決方案, 並記住其填滿率, 因為圖元是您最寶貴的資源。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-216">Design your solution with fill rate in mind, since pixels will be your most precious resource.</span></span> <span data-ttu-id="ce1fb-217">透過透明度的目標穩固幾何。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-217">Target solid geometry over transparency.</span></span>

<span data-ttu-id="ce1fb-218">有了備份解決方案, 您就可以在高階機器上以更複雜的方式開始分層, 或只是加強備份解決方案的解析。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-218">With a backup solution, you can then start layering in more complexity for high end machines or maybe just enhance resolution of your backup solution.</span></span>

<span data-ttu-id="ce1fb-219">針對最糟的案例進行設計, 而且可能會考慮針對繁重的情況使用適應性呈現。</span><span class="sxs-lookup"><span data-stu-id="ce1fb-219">Design for worst case scenarios, and maybe consider using adaptive rendering for heavy situations.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="ce1fb-220">關於作者</span><span class="sxs-lookup"><span data-stu-id="ce1fb-220">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="ce1fb-221"><b>Robert Ferrese</b></span><span class="sxs-lookup"><span data-stu-id="ce1fb-221"><b>Robert Ferrese</b></span></span><br><span data-ttu-id="ce1fb-222">軟體工程師@Microsoft</span><span class="sxs-lookup"><span data-stu-id="ce1fb-222">Software engineer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="ce1fb-223"><b>Dan Andersson</b></span><span class="sxs-lookup"><span data-stu-id="ce1fb-223"><b>Dan Andersson</b></span></span><br><span data-ttu-id="ce1fb-224">軟體工程師@Microsoft</span><span class="sxs-lookup"><span data-stu-id="ce1fb-224">Software engineer @Microsoft</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="ce1fb-225">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce1fb-225">See also</span></span>
* [<span data-ttu-id="ce1fb-226">瞭解混合現實的效能</span><span class="sxs-lookup"><span data-stu-id="ce1fb-226">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="ce1fb-227">Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="ce1fb-227">Performance Recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

 
