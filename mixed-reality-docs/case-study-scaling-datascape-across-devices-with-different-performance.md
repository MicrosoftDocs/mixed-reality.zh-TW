---
title: 案例研究-跨裝置採用不同效能調整的 Datascape
description: 此案例研究提供您深入了解 Microsoft 開發人員如何最佳化 Datascape 應用程式利用某個範圍的效能功能的裝置上提供絕佳的體驗。
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 沈浸式耳機，效能最佳化，VR 案例研究
ms.openlocfilehash: 990a5ee6de07b6416e3150a7885220409a9c8d93
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597034"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a><span data-ttu-id="29d93-104">案例研究-跨裝置採用不同效能調整的 Datascape</span><span class="sxs-lookup"><span data-stu-id="29d93-104">Case study - Scaling Datascape across devices with different performance</span></span>

<span data-ttu-id="29d93-105">Datascape 是內部開發 microsoft 我們著重於顯示地形模型的資料之上的天氣資料的其中一個 Windows Mixed Reality 應用程式。</span><span class="sxs-lookup"><span data-stu-id="29d93-105">Datascape is a Windows Mixed Reality application developed internally at Microsoft where we focused on displaying weather data on top of terrain data.</span></span> <span data-ttu-id="29d93-106">應用程式從探索資料，在混合實境中住全像攝影版的資料視覺效果的使用者，探索的使用者取得獨特的見解。</span><span class="sxs-lookup"><span data-stu-id="29d93-106">The application explores the unique insights users gain from discovering data in mixed reality by surrounding the user with holographic data visualization.</span></span>

<span data-ttu-id="29d93-107">針對 Datascape 我們想要以不同的硬體功能，範圍從以 Windows Mixed Reality 沈浸式耳機，Microsoft HoloLens 和低功率電腦，到高階的 GPU 與最新的電腦為目標的各種不同的平台。</span><span class="sxs-lookup"><span data-stu-id="29d93-107">For Datascape we wanted to target a variety of platforms with different hardware capabilities ranging from Microsoft HoloLens to Windows Mixed Reality immersive headsets, and from lower-powered PCs to the very latest PCs with high-end GPU.</span></span> <span data-ttu-id="29d93-108">主要的挑戰轉譯場景在視覺上吸引人的幾與許多不同的圖形功能的裝置上同時執行高的畫面播放速率。</span><span class="sxs-lookup"><span data-stu-id="29d93-108">The main challenge was rendering our scene in a visually appealing matter on devices with wildly different graphics capabilities while executing at a high framerate.</span></span>

<span data-ttu-id="29d93-109">此案例研究將逐步引導的程序和技術用來建立一些我們更多的 GPU 密集系統，說明我們所遇到的問題，以及我們如何克服。</span><span class="sxs-lookup"><span data-stu-id="29d93-109">This case study will walk through the process and techniques used to create some of our more GPU-intensive systems, describing the problems we encountered and how we overcame them.</span></span>

## <a name="transparency-and-overdraw"></a><span data-ttu-id="29d93-110">透明度和過度繪製</span><span class="sxs-lookup"><span data-stu-id="29d93-110">Transparency and overdraw</span></span>

<span data-ttu-id="29d93-111">我們主要的轉譯工具處理透明度，因為透明效果可能會在 GPU 上耗費資源。</span><span class="sxs-lookup"><span data-stu-id="29d93-111">Our main rendering struggles dealt with transparency, since transparency can be expensive on a GPU.</span></span>

<span data-ttu-id="29d93-112">實線幾何可以轉譯前面到後面在寫入至停止任何未來的像素後方從正在捨棄該像素的深度緩衝區。</span><span class="sxs-lookup"><span data-stu-id="29d93-112">Solid geometry can be rendered front to back while writing to the depth buffer, stopping any future pixels located behind that pixel from being discarded.</span></span> <span data-ttu-id="29d93-113">這可防止執行像素著色器，可大幅加速此程序隱藏像素為單位。</span><span class="sxs-lookup"><span data-stu-id="29d93-113">This prevents hidden pixels from executing the pixel shader, speeding up the process significantly.</span></span> <span data-ttu-id="29d93-114">如果幾何以最佳方式排序，將會一次繪製在螢幕上的每個像素。</span><span class="sxs-lookup"><span data-stu-id="29d93-114">If geometry is sorted optimally, each pixel on the screen will be drawn only once.</span></span>

<span data-ttu-id="29d93-115">要排序的透明幾何需求回到前端，並依賴混用來在螢幕上的目前像素的像素著色器輸出。</span><span class="sxs-lookup"><span data-stu-id="29d93-115">Transparent geometry needs to be sorted back to front and relies on blending the output of the pixel shader to the current pixel on the screen.</span></span> <span data-ttu-id="29d93-116">這會導致每個像素繪製到多次每個畫面，稱為 「 過度繪製在螢幕上。</span><span class="sxs-lookup"><span data-stu-id="29d93-116">This can result in each pixel on the screen being drawn to multiple times per frame, referred to as overdraw.</span></span>

<span data-ttu-id="29d93-117">HoloLens 和主要電腦，螢幕只可填入少數幾個時間，讓透明轉譯有問題。</span><span class="sxs-lookup"><span data-stu-id="29d93-117">For HoloLens and mainstream PCs, the screen can only be filled a handful of times, making transparent rendering problematic.</span></span>

## <a name="introduction-to-datascape-scene-components"></a><span data-ttu-id="29d93-118">Datascape 場景元件簡介</span><span class="sxs-lookup"><span data-stu-id="29d93-118">Introduction to Datascape scene components</span></span>

<span data-ttu-id="29d93-119">我們有三個主要元件至我們的場景;**UI 中，地圖**，並**天氣**。</span><span class="sxs-lookup"><span data-stu-id="29d93-119">We had three major components to our scene; **the UI, the map**, and **the weather**.</span></span> <span data-ttu-id="29d93-120">我們早知道我們的天氣影響會需要它無法取得的所有 GPU 時間，因此我們刻意設計的 UI 和地形會減少任何過度繪製的方式。</span><span class="sxs-lookup"><span data-stu-id="29d93-120">We knew early on that our weather effects would require all the GPU time it could get, so we purposely designed the UI and terrain in a way that would reduce any overdraw.</span></span>

<span data-ttu-id="29d93-121">我們重新設計了 UI 多次降到最低數量過度繪製它會產生。</span><span class="sxs-lookup"><span data-stu-id="29d93-121">We reworked the UI several times to minimize the amount of overdraw it would produce.</span></span> <span data-ttu-id="29d93-122">我們 erred 側邊更複雜的幾何，而不是覆疊透明圖案在彼此之上的元件，例如發光按鈕和對應的概觀。</span><span class="sxs-lookup"><span data-stu-id="29d93-122">We erred on the side of more complex geometry rather than overlaying transparent art on top of each other for components like glowing buttons and map overviews.</span></span>

<span data-ttu-id="29d93-123">對應中，我們使用的自訂著色器會去除標準的 Unity 功能，例如陰影或複雜的光線，取代為簡單的單一 sun 光源模型計算和自訂的霧計算。</span><span class="sxs-lookup"><span data-stu-id="29d93-123">For the map, we used a custom shader that would strip out standard Unity features such as shadows and complex lighting, replacing them with a simple single sun lighting model and a custom fog calculation.</span></span> <span data-ttu-id="29d93-124">這會產生簡單的像素著色器，並釋出 GPU 循環。</span><span class="sxs-lookup"><span data-stu-id="29d93-124">This produced a simple pixel shader and free up GPU cycles.</span></span>

<span data-ttu-id="29d93-125">我們設法取得 UI 和地圖來轉譯在預算其中並不需要任何變更，根據硬體;不過，天氣視覺效果，尤其是雲端轉譯，證實是更有挑戰性 ！</span><span class="sxs-lookup"><span data-stu-id="29d93-125">We managed to get both the UI and the map to rendering at budget where we did not need any changes to them depending on the hardware; however, the weather visualization, in particular the cloud rendering, proved to be more of a challenge!</span></span>

## <a name="background-on-cloud-data"></a><span data-ttu-id="29d93-126">雲端資料的背景</span><span class="sxs-lookup"><span data-stu-id="29d93-126">Background on cloud data</span></span>

<span data-ttu-id="29d93-127">我們的雲端資料從 NOAA 伺服器下載 (http://nomads.ncep.noaa.gov/)和來到我們在三個不同的 2D 層級，而每個雲端的上方和下方的高度，以及雲端中為每個資料格方格的密度。</span><span class="sxs-lookup"><span data-stu-id="29d93-127">Our cloud data was downloaded from NOAA servers (http://nomads.ncep.noaa.gov/) and came to us in three distinct 2D layers, each with the top and bottom height of the cloud, as well as the density of the cloud for each cell of the grid.</span></span> <span data-ttu-id="29d93-128">資料已處理到雲端資訊材質其中每個元件儲存在 GPU 上方便存取的材質的紅色、 綠色和藍色元件。</span><span class="sxs-lookup"><span data-stu-id="29d93-128">The data got processed into a cloud info texture where each component was stored in the red, green, and blue component of the texture for easy access on the GPU.</span></span>

## <a name="geometry-clouds"></a><span data-ttu-id="29d93-129">幾何雲端</span><span class="sxs-lookup"><span data-stu-id="29d93-129">Geometry clouds</span></span>

<span data-ttu-id="29d93-130">若要確定我們低電源的電腦可能會造成我們首先決定我們雲端過度繪製一種方法，會使用實線幾何降到最低。</span><span class="sxs-lookup"><span data-stu-id="29d93-130">To make sure our lower-powered machines could render our clouds we decided to start with an approach that would use solid geometry to minimize overdraw.</span></span>

<span data-ttu-id="29d93-131">我們第一次嘗試產生每個圖層使用的每個頂點的雲端資訊材質半徑來產生圖形實心和網格來產生雲端。</span><span class="sxs-lookup"><span data-stu-id="29d93-131">We first tried producing clouds by generating a solid heightmap mesh for each layer using the radius of the cloud info texture per vertex to generate the shape.</span></span> <span data-ttu-id="29d93-132">我們可以使用幾何著色器以產生在頂端和底部的 雲端產生紮實的雲端圖形的頂點。</span><span class="sxs-lookup"><span data-stu-id="29d93-132">We used a geometry shader to produce the vertices both at the top and the bottom of the cloud generating solid cloud shapes.</span></span> <span data-ttu-id="29d93-133">我們會使用從材質的密度值色彩的更多的密集雲端深色的雲端。</span><span class="sxs-lookup"><span data-stu-id="29d93-133">We used the density value from the texture to color the cloud with darker colors for more dense clouds.</span></span>

<span data-ttu-id="29d93-134">**建立頂點著色器：**</span><span class="sxs-lookup"><span data-stu-id="29d93-134">**Shader for creating the vertices:**</span></span>

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

<span data-ttu-id="29d93-135">我們引進了以取得詳細資料，以實際的資料為基礎的小型的非搜尋模式。</span><span class="sxs-lookup"><span data-stu-id="29d93-135">We introduced a small noise pattern to get more detail on top of the real data.</span></span> <span data-ttu-id="29d93-136">若要產生 round 雲端邊緣，我們裁剪像素像素著色器中的內插補點的半徑值叫用捨棄近乎零值的臨界值時。</span><span class="sxs-lookup"><span data-stu-id="29d93-136">To produce round cloud edges, we clipped the pixels in the pixel shader when the interpolated radius value hit a threshold to discard near-zero values.</span></span>

![幾何雲端](images/datascape-geometry-clouds-700px.jpg)

<span data-ttu-id="29d93-138">由於雲端是單色幾何，可以呈現之前隱藏底下的任何耗費資源的對應像素為單位，以進一步提升畫面播放速率地形。</span><span class="sxs-lookup"><span data-stu-id="29d93-138">Since the clouds are solid geometry, they can be rendered before the terrain to hide any expensive map pixels underneath to further improve framerate.</span></span> <span data-ttu-id="29d93-139">此解決方案會執行也在最小空間從所有的視訊卡，高階顯示卡，以及 HoloLens，因為實線幾何呈現方法。</span><span class="sxs-lookup"><span data-stu-id="29d93-139">This solution ran well on all graphics cards from min-spec to high-end graphics cards, as well as on HoloLens, because of the solid geometry rendering approach.</span></span>

## <a name="solid-particle-clouds"></a><span data-ttu-id="29d93-140">Solid 粒子雲端</span><span class="sxs-lookup"><span data-stu-id="29d93-140">Solid particle clouds</span></span>

<span data-ttu-id="29d93-141">我們現在必須產生適當的表示法，我們的雲端資料，但已 「 哇 」 因數有點低落並未傳達我們想要讓我們高階的電腦的體積型風格的備份解決方案。</span><span class="sxs-lookup"><span data-stu-id="29d93-141">We now had a backup solution that produced a decent representation of our cloud data, but was a bit lackluster in the “wow” factor and did not convey the volumetric feel that we wanted for our high-end machines.</span></span>

<span data-ttu-id="29d93-142">下一步建立雲端代表約 100,000 個物件，以產生更有機和體積型的外觀。</span><span class="sxs-lookup"><span data-stu-id="29d93-142">Our next step was creating the clouds by representing them with approximately 100,000 particles to produce a more organic and volumetric look.</span></span>

<span data-ttu-id="29d93-143">如果物件保持穩固，而且排序前-後，我們仍然有許多優點背後先前呈現的物件，像素的深度緩衝區剔除減少過度繪製。</span><span class="sxs-lookup"><span data-stu-id="29d93-143">If particles stay solid and sort front-to-back, we can still benefit from depth buffer culling of the pixels behind previously rendered particles, reducing the overdraw.</span></span> <span data-ttu-id="29d93-144">此外，使用以物件為基礎的解決方案，我們可以改變為目標的不同硬體使用的物件數量。</span><span class="sxs-lookup"><span data-stu-id="29d93-144">Also, with a particle-based solution, we can alter the amount of particles used to target different hardware.</span></span> <span data-ttu-id="29d93-145">不過，所有像素仍然需要進行深度測試，而導致某些額外的負荷。</span><span class="sxs-lookup"><span data-stu-id="29d93-145">However, all pixels still need to be depth tested, which results in some additional overhead.</span></span>

<span data-ttu-id="29d93-146">首先，我們會在啟動建立物件周圍的經驗的中心點的位置。</span><span class="sxs-lookup"><span data-stu-id="29d93-146">First, we created particle positions around the center point of the experience at startup.</span></span> <span data-ttu-id="29d93-147">我們發佈更緊密圍繞中心物件和較少的距離。</span><span class="sxs-lookup"><span data-stu-id="29d93-147">We distributed the particles more densely around the center and less so in the distance.</span></span> <span data-ttu-id="29d93-148">我們預先排序從中央到後端的所有物件，因此會先呈現最接近的物件。</span><span class="sxs-lookup"><span data-stu-id="29d93-148">We pre-sorted all particles from the center to the back so that the closest particles would render first.</span></span>

<span data-ttu-id="29d93-149">計算著色器會放置在正確的高度和色彩，其根據密度的每個物件的雲端資訊材質的範例。</span><span class="sxs-lookup"><span data-stu-id="29d93-149">A compute shader would sample the cloud info texture to position each particle at a correct height and color it based on the density.</span></span>

<span data-ttu-id="29d93-150">我們使用了*DrawProcedural*來呈現每個物件允許完全保持在 GPU 上的物件資料的四倍。</span><span class="sxs-lookup"><span data-stu-id="29d93-150">We used *DrawProcedural* to render a quad per particle allowing the particle data to stay on the GPU at all times.</span></span>

<span data-ttu-id="29d93-151">每個物件包含高度和半徑。</span><span class="sxs-lookup"><span data-stu-id="29d93-151">Each particle contained both a height and a radius.</span></span> <span data-ttu-id="29d93-152">以從雲端資訊材質取樣的雲端資料為基礎的高度和半徑根據初始分配，它會計算儲存到其最接近像素的水平距離。</span><span class="sxs-lookup"><span data-stu-id="29d93-152">The height was based on the cloud data sampled from the cloud info texture, and the radius was based on the initial distribution where it would be calculated to store the horizontal distance to its closest neighbor.</span></span> <span data-ttu-id="29d93-153">四邊形會調整成本身，因此當使用者查看它的水平靠高度來使用這項資料會顯示高度，且當使用者查看由上而下，會涵蓋與其相鄰項目之間的區域。</span><span class="sxs-lookup"><span data-stu-id="29d93-153">The quads would use this data to orient itself angled by the height so that when users look at it horizontally, the height would be shown, and when users looked at it top-down, the area between its neighbors would be covered.</span></span>

![物件圖形](images/particle-shape-700px.png)

<span data-ttu-id="29d93-155">**顯示發佈的著色器程式碼：**</span><span class="sxs-lookup"><span data-stu-id="29d93-155">**Shader code showing the distribution:**</span></span>

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

<span data-ttu-id="29d93-156">因為我們排序物件前至後，我們仍使用剪輯 (不是 blend) 透明的像素的實心樣式著色器，這項技術會處理物件，避免成本高昂的過度繪製，即使在低電源的電腦上令人驚訝的數量。</span><span class="sxs-lookup"><span data-stu-id="29d93-156">Since we sort the particles front-to-back and we still used a solid style shader to clip (not blend) transparent pixels, this technique handles a surprising amount of particles, avoiding costly over-draw even on the lower-powered machines.</span></span>

## <a name="transparent-particle-clouds"></a><span data-ttu-id="29d93-157">透明粒子雲端</span><span class="sxs-lookup"><span data-stu-id="29d93-157">Transparent particle clouds</span></span>

<span data-ttu-id="29d93-158">Solid 物件提供良好的有機感覺到雲端的圖形，但仍需要銷售定域機組的 fluffiness 的項目。</span><span class="sxs-lookup"><span data-stu-id="29d93-158">The solid particles provided a good organic feel to the shape of the clouds but still needed something to sell the fluffiness of clouds.</span></span> <span data-ttu-id="29d93-159">我們因而決定試用我們可以在其中引進 transparency 高階顯示卡的自訂解決方案。</span><span class="sxs-lookup"><span data-stu-id="29d93-159">We decided to try a custom solution for the high-end graphics cards where we can introduce transparency.</span></span>

<span data-ttu-id="29d93-160">若要這樣做我們只要切換物件的初始排序順序，並變更使用 alpha 的材質著色器。</span><span class="sxs-lookup"><span data-stu-id="29d93-160">To do this we simply switched the initial sorting order of the particles and changed the shader to use the textures alpha.</span></span>

![Fluffy 雲端](images/fluffy-clouds-700px.jpg)

<span data-ttu-id="29d93-162">它看起來很但證實是更困難的機器而言過於沉重的因為它會造成轉譯時間的數百個螢幕上的每個像素 ！</span><span class="sxs-lookup"><span data-stu-id="29d93-162">It looked great but proved to be too heavy for even the toughest machines since it would result in rendering each pixel on the screen hundreds of times!</span></span>

## <a name="render-off-screen-with-lower-resolution"></a><span data-ttu-id="29d93-163">呈現較低解析度的幕外</span><span class="sxs-lookup"><span data-stu-id="29d93-163">Render off-screen with lower resolution</span></span>

<span data-ttu-id="29d93-164">為了減少由雲端轉譯的像素數，我們開始 （相較於螢幕） 的一季解析緩衝區中將它們呈現並自動縮放的最終結果備份在螢幕上的所有物件具有已都繪製後。</span><span class="sxs-lookup"><span data-stu-id="29d93-164">To reduce the number of pixels rendered by the clouds, we started rendering them in a quarter resolution buffer (compared to the screen) and stretching the end result back up onto the screen after all the particles had been drawn.</span></span> <span data-ttu-id="29d93-165">這給了我們大約 4 倍的速度增益，但隨附幾個需要注意的事項。</span><span class="sxs-lookup"><span data-stu-id="29d93-165">This gave us roughly a 4x speedup, but came with a couple of caveats.</span></span>

<span data-ttu-id="29d93-166">**轉譯幕外的程式碼：**</span><span class="sxs-lookup"><span data-stu-id="29d93-166">**Code for rendering off-screen:**</span></span>

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

<span data-ttu-id="29d93-167">首先，當呈現到幕外緩衝區，我們遺失所有深入資訊我們主要的場景，請從導致物件後面山地呈現 mountain 之上。</span><span class="sxs-lookup"><span data-stu-id="29d93-167">First, when rendering into an off-screen buffer, we lost all depth information from our main scene, resulting in particles behind mountains rendering on top of the mountain.</span></span>

<span data-ttu-id="29d93-168">第二，延伸緩衝區也引進了種解析度變更的我們定域機組的邊緣上的成品。</span><span class="sxs-lookup"><span data-stu-id="29d93-168">Second, stretching the buffer also introduced artifacts on the edges of our clouds where the resolution change was noticeable.</span></span> <span data-ttu-id="29d93-169">下面兩節會討論我們解決這些問題的方式。</span><span class="sxs-lookup"><span data-stu-id="29d93-169">The next two sections talk about how we resolved these issues.</span></span>

## <a name="particle-depth-buffer"></a><span data-ttu-id="29d93-170">物件的深度緩衝區</span><span class="sxs-lookup"><span data-stu-id="29d93-170">Particle depth buffer</span></span>

<span data-ttu-id="29d93-171">若要讓 mountain 或物件可能涵蓋其背後的物件與世界幾何同時存在的物件，我們會填入與深度緩衝區，其中包含的主要場景幾何的幕外緩衝區。</span><span class="sxs-lookup"><span data-stu-id="29d93-171">To make the particles co-exist with the world geometry where a mountain or object could cover particles behind it, we populated the off-screen buffer with a depth buffer containing the geometry of the main scene.</span></span> <span data-ttu-id="29d93-172">若要產生這類的深度緩衝區，我們建立第二個的相機，呈現僅實線幾何和場景的深度。</span><span class="sxs-lookup"><span data-stu-id="29d93-172">To produce such depth buffer, we created a second camera, rendering only the solid geometry and depth of the scene.</span></span>

<span data-ttu-id="29d93-173">我們接著使用新的材質中定域機組的像素著色器 occlude 像素為單位。</span><span class="sxs-lookup"><span data-stu-id="29d93-173">We then used the new texture in the pixel shader of the clouds to occlude pixels.</span></span> <span data-ttu-id="29d93-174">我們可以用相同的材質來計算至雲端的像素背後的幾何距離。</span><span class="sxs-lookup"><span data-stu-id="29d93-174">We used the same texture to calculate the distance to the geometry behind a cloud pixel.</span></span> <span data-ttu-id="29d93-175">藉由使用這麼遠的距離，並將它套用到像素的 alpha，我們現在會影響的雲端淡出，因為它們更接近地形、 移除任何硬碟的剪下符合物件和地形。</span><span class="sxs-lookup"><span data-stu-id="29d93-175">By using that distance and applying it to the alpha of the pixel, we now had the effect of clouds fading out as they get close to terrain, removing any hard cuts where particles and terrain meet.</span></span>

![混合成地形模型的雲端](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a><span data-ttu-id="29d93-177">銳利化邊緣</span><span class="sxs-lookup"><span data-stu-id="29d93-177">Sharpening the edges</span></span>

<span data-ttu-id="29d93-178">向上延展雲端看起來幾乎完全相同物件的中心的標準大小雲端，或在它們重疊，但會有些成品示範雲端邊緣。</span><span class="sxs-lookup"><span data-stu-id="29d93-178">The stretched-up clouds looked almost identical to the normal size clouds at the center of the particles or where they overlapped, but showed some artifacts at the cloud edges.</span></span> <span data-ttu-id="29d93-179">否則清晰的邊緣會看起來是模糊，而且觀景窗移動時，所導入別名的效果。</span><span class="sxs-lookup"><span data-stu-id="29d93-179">Otherwise sharp edges would appear blurry and alias effects were introduced when the camera moved.</span></span>

<span data-ttu-id="29d93-180">我們解決幕外緩衝區，以判斷項重大變更相較之下發生 (1) 上執行簡單的著色器。</span><span class="sxs-lookup"><span data-stu-id="29d93-180">We solved this by running a simple shader on the off-screen buffer to determine where big changes in contrast occurred (1).</span></span> <span data-ttu-id="29d93-181">我們的像素，與重大變更到新的樣板緩衝區 (2)。</span><span class="sxs-lookup"><span data-stu-id="29d93-181">We put the pixels with big changes into a new stencil buffer (2).</span></span> <span data-ttu-id="29d93-182">然後我們會使用遮罩的樣板緩衝區這些高對比區域時套用的幕外緩衝區到螢幕，導致漏洞之中及四周的雲端 (3)。</span><span class="sxs-lookup"><span data-stu-id="29d93-182">We then used the stencil buffer to mask out these high contrast areas when applying the off-screen buffer back to the screen, resulting in holes in and around the clouds (3).</span></span>

<span data-ttu-id="29d93-183">我們再轉譯所有物件一次在全螢幕模式中，但這次使用樣板緩衝區表示遮住的所有項目，但邊緣，導致 像素為單位的最少觸及 (4)。</span><span class="sxs-lookup"><span data-stu-id="29d93-183">We then rendered all the particles again in full-screen mode, but this time used the stencil buffer to mask out everything but the edges, resulting in a minimal set of pixels touched (4).</span></span> <span data-ttu-id="29d93-184">命令緩衝區已建立的物件，所以我們只需要讓呈現一次新的相機。</span><span class="sxs-lookup"><span data-stu-id="29d93-184">Since the command buffer was already created for the particles, we simply had to render it again to the new camera.</span></span>

![轉譯雲端邊緣的進展](images/cloud-steps-1-4-700px.jpg)

<span data-ttu-id="29d93-186">最終結果是清晰的邊緣，定域機組的廉價 center 區段。</span><span class="sxs-lookup"><span data-stu-id="29d93-186">The end result was sharp edges with cheap center sections of the clouds.</span></span>

<span data-ttu-id="29d93-187">雖然這遠快於轉譯中的所有物件都全螢幕，沒有測試針對樣板緩衝區的像素，因此產生大量過度繪製仍產生相關成本仍然隨附的成本。</span><span class="sxs-lookup"><span data-stu-id="29d93-187">While this was much faster than rendering all particles in full screen, there is still a cost associated with testing a pixel against the stencil buffer, so a massive amount of overdraw still came with a cost.</span></span>

## <a name="culling-particles"></a><span data-ttu-id="29d93-188">挑選出的物件</span><span class="sxs-lookup"><span data-stu-id="29d93-188">Culling particles</span></span>

<span data-ttu-id="29d93-189">如需我們風力效果，我們可以產生長的三角形帶狀線計算著色器，建立許多 wisps 風向的世界中。</span><span class="sxs-lookup"><span data-stu-id="29d93-189">For our wind effect, we generated long triangle strips in a compute shader, creating many wisps of wind in the world.</span></span> <span data-ttu-id="29d93-190">不大填滿率，因為產生的 skinny 階梯狀 wind 生效時，它會產生許多數十萬的頂點，頂點著色器造成沈重的負載。</span><span class="sxs-lookup"><span data-stu-id="29d93-190">While the wind effect was not heavy on fill rate due to skinny strips generated, it produced many hundreds of thousands of vertices resulting in a heavy load for the vertex shader.</span></span>

<span data-ttu-id="29d93-191">我們引進了附加的計算著色器，以摘要風力帶狀線要繪製的子集上的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="29d93-191">We introduced append buffers on the compute shader to feed a subset of the wind strips to be drawn.</span></span> <span data-ttu-id="29d93-192">透過一些簡單的檢視範圍揀選 logic 計算著色器中，我們無法判斷寬帶是否視界之外，並防止它新增至推播的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="29d93-192">With some simple view frustum culling logic in the compute shader, we could determine if a strip was outside of camera view and prevent it from being added to the push buffer.</span></span> <span data-ttu-id="29d93-193">這帶狀線的數量大幅降低，釋出一些在 GPU 上所需的循環。</span><span class="sxs-lookup"><span data-stu-id="29d93-193">This reduced the amount of strips significantly, freeing up some needed cycles on the GPU.</span></span>

<span data-ttu-id="29d93-194">**展示附加緩衝區的程式碼：**</span><span class="sxs-lookup"><span data-stu-id="29d93-194">**Code demonstrating an append buffer:**</span></span>

<span data-ttu-id="29d93-195">*計算著色器：*</span><span class="sxs-lookup"><span data-stu-id="29d93-195">*Compute shader:*</span></span>

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

<span data-ttu-id="29d93-196">*C#程式碼：*</span><span class="sxs-lookup"><span data-stu-id="29d93-196">*C# code:*</span></span>

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

<span data-ttu-id="29d93-197">我們嘗試的雲端物件，我們會在此挑選其上計算著色器，並只推入要呈現的可見物件上使用相同的技巧。</span><span class="sxs-lookup"><span data-stu-id="29d93-197">We tried using the same technique on the cloud particles, where we would cull them on the compute shader and only push the visible particles to be rendered.</span></span> <span data-ttu-id="29d93-198">這項技術實際上沒有儲存我們大部分在 GPU 上因為最大的瓶頸是呈現在畫面中，而不計算頂點的成本上的量像素。</span><span class="sxs-lookup"><span data-stu-id="29d93-198">This technique actually did not save us much on the GPU since the biggest bottleneck was the amount pixels rendered on the screen, and not the cost of calculating the vertices.</span></span>

<span data-ttu-id="29d93-199">這項技術的其他問題已附加緩衝區填入以隨機順序本質平行運算粒子，導致為未排序，導致產生閃爍的雲端物件的已排序的物件。</span><span class="sxs-lookup"><span data-stu-id="29d93-199">The other problem with this technique was that the append buffer populated in random order due to its parallelized nature of computing the particles, causing the sorted particles to be un-sorted, resulting in flickering cloud particles.</span></span>

<span data-ttu-id="29d93-200">要排序的推播緩衝區的技術，但數量有限的效能提升，我們從剔除物件會有可能與其他的排序，位移，因此我們決定不追求此最佳化。</span><span class="sxs-lookup"><span data-stu-id="29d93-200">There are techniques to sort the push buffer, but the limited amount of performance gain we got out of culling particles would likely be offset with an additional sort, so we decided to not pursue this optimization.</span></span>

## <a name="adaptive-rendering"></a><span data-ttu-id="29d93-201">自適性轉譯</span><span class="sxs-lookup"><span data-stu-id="29d93-201">Adaptive rendering</span></span>

<span data-ttu-id="29d93-202">為了確保穩定的應用程式上的畫面播放速率，搭配不同的轉譯條件，例如多雲 vs 的清楚檢視，我們導入了適應性呈現應用程式。</span><span class="sxs-lookup"><span data-stu-id="29d93-202">To ensure a steady framerate on an app with varying rendering conditions like a cloudy vs a clear view, we introduced adaptive rendering to our app.</span></span>

<span data-ttu-id="29d93-203">自適性轉譯的第一個步驟是測量 GPU。</span><span class="sxs-lookup"><span data-stu-id="29d93-203">The first step of adaptive rendering is to measure GPU.</span></span> <span data-ttu-id="29d93-204">我們採用的方法來插入 GPU 命令緩衝區的開頭和結尾呈現的畫面格的自訂程式碼，擷取同時左邊和右邊的眼睛螢幕的時間。</span><span class="sxs-lookup"><span data-stu-id="29d93-204">We did this by inserting custom code into the GPU command buffer at the beginning and the end of a rendered frame, capturing both the left and right eye screen time.</span></span>

<span data-ttu-id="29d93-205">藉由測量轉譯，並和比較，我們了解我們已捨棄畫面如何關閉我們想要重新整理速率，所花費的時間。</span><span class="sxs-lookup"><span data-stu-id="29d93-205">By measuring the time spent rendering and comparing it to our desired refresh-rate we got a sense of how close we were to dropping frames.</span></span>

<span data-ttu-id="29d93-206">當接近捨棄畫面，我們採用我們的轉譯，若要加快。</span><span class="sxs-lookup"><span data-stu-id="29d93-206">When close to dropping frames, we adapt our rendering to make it faster.</span></span> <span data-ttu-id="29d93-207">一個簡單的方式進行調整變更檢視區大小的畫面中，需要取得呈現較少像素為單位。</span><span class="sxs-lookup"><span data-stu-id="29d93-207">One simple way of adapting is changing the viewport size of the screen, requiring less pixels to get rendered.</span></span>

<span data-ttu-id="29d93-208">藉由使用*UnityEngine.XR.XRSettings.renderViewportScale*系統壓縮目標的檢視區，並會自動伸展備份至適當比例 畫面的結果。</span><span class="sxs-lookup"><span data-stu-id="29d93-208">By using *UnityEngine.XR.XRSettings.renderViewportScale* the system shrinks the targeted viewport and automatically stretches the result back up to fit the screen.</span></span> <span data-ttu-id="29d93-209">小幅變更擴展全球幾何上難以通知而 0.7 縮放比例需要呈現的像素為單位的一半數量。</span><span class="sxs-lookup"><span data-stu-id="29d93-209">A small change in scale is barely noticeable on world geometry, and a scale factor of 0.7 requires half the amount of pixels to be rendered.</span></span>

![70%小數位數一半的像素](images/datascape-scaling-700px.jpg)

<span data-ttu-id="29d93-211">當我們偵測到我們在降低影格數我們降低固定數字的小數位數，並增加回我們速度不夠快一次執行時。</span><span class="sxs-lookup"><span data-stu-id="29d93-211">When we detect that we are about to drop frames we lower the scale by a fixed number, and increase it back when we are running fast enough again.</span></span>

<span data-ttu-id="29d93-212">雖然我們決定要使用哪些雲端技術為基礎的圖形在啟動時的硬體功能，它可以為基礎的資料是來自 GPU 度量，以防止系統保持在低解析度長的時間，但這一點我們沒有時間 若要瀏覽 Datascape 中。</span><span class="sxs-lookup"><span data-stu-id="29d93-212">While we decided what cloud technique to use based on graphics capabilities of the hardware at startup, it is possible to base it on data from the GPU measurement to prevent the system from staying at low resolution for a long time, but this is something we did not have time to explore in Datascape.</span></span>

## <a name="final-thoughts"></a><span data-ttu-id="29d93-213">結論</span><span class="sxs-lookup"><span data-stu-id="29d93-213">Final thoughts</span></span>

<span data-ttu-id="29d93-214">目標為各種不同的硬體具挑戰性，而且需要一些規劃。</span><span class="sxs-lookup"><span data-stu-id="29d93-214">Targeting a variety of hardware is challenging and requires some planning.</span></span>

<span data-ttu-id="29d93-215">我們建議您先以熟悉問題空間，及開發將在您的機器執行的備份解決方案的低功率電腦為目標。</span><span class="sxs-lookup"><span data-stu-id="29d93-215">We recommend that you start targeting lower-powered machines to get familiar with the problem space and develop a backup solution that will run on all your machines.</span></span> <span data-ttu-id="29d93-216">設計您的解決方案使用的填滿率納入考量，因為像素為單位將會是您最寶貴的資源。</span><span class="sxs-lookup"><span data-stu-id="29d93-216">Design your solution with fill rate in mind, since pixels will be your most precious resource.</span></span> <span data-ttu-id="29d93-217">透過透明效果的目標實線幾何。</span><span class="sxs-lookup"><span data-stu-id="29d93-217">Target solid geometry over transparency.</span></span>

<span data-ttu-id="29d93-218">備份解決方案中,，您可以再啟動高端機器的更多複雜的分層或也許增強您的備份解決方案的解析度。</span><span class="sxs-lookup"><span data-stu-id="29d93-218">With a backup solution, you can then start layering in more complexity for high end machines or maybe just enhance resolution of your backup solution.</span></span>

<span data-ttu-id="29d93-219">設計最糟的情況，並可能考慮使用適應性呈現沈重的情況下。</span><span class="sxs-lookup"><span data-stu-id="29d93-219">Design for worst case scenarios, and maybe consider using adaptive rendering for heavy situations.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="29d93-220">關於作者</span><span class="sxs-lookup"><span data-stu-id="29d93-220">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="29d93-221"><b>Robert Ferrese</b></span><span class="sxs-lookup"><span data-stu-id="29d93-221"><b>Robert Ferrese</b></span></span><br><span data-ttu-id="29d93-222">軟體工程師 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="29d93-222">Software engineer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="29d93-223"><b>Dan Andersson</b></span><span class="sxs-lookup"><span data-stu-id="29d93-223"><b>Dan Andersson</b></span></span><br><span data-ttu-id="29d93-224">軟體工程師 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="29d93-224">Software engineer @Microsoft</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="29d93-225">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29d93-225">See also</span></span>
* [<span data-ttu-id="29d93-226">了解效能 for Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="29d93-226">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="29d93-227">Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="29d93-227">Performance Recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

 
