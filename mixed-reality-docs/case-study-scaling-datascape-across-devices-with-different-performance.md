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
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a>案例研究-跨裝置採用不同效能調整的 Datascape

Datascape 是內部開發 microsoft 我們著重於顯示地形模型的資料之上的天氣資料的其中一個 Windows Mixed Reality 應用程式。 應用程式從探索資料，在混合實境中住全像攝影版的資料視覺效果的使用者，探索的使用者取得獨特的見解。

針對 Datascape 我們想要以不同的硬體功能，範圍從以 Windows Mixed Reality 沈浸式耳機，Microsoft HoloLens 和低功率電腦，到高階的 GPU 與最新的電腦為目標的各種不同的平台。 主要的挑戰轉譯場景在視覺上吸引人的幾與許多不同的圖形功能的裝置上同時執行高的畫面播放速率。

此案例研究將逐步引導的程序和技術用來建立一些我們更多的 GPU 密集系統，說明我們所遇到的問題，以及我們如何克服。

## <a name="transparency-and-overdraw"></a>透明度和過度繪製

我們主要的轉譯工具處理透明度，因為透明效果可能會在 GPU 上耗費資源。

實線幾何可以轉譯前面到後面在寫入至停止任何未來的像素後方從正在捨棄該像素的深度緩衝區。 這可防止執行像素著色器，可大幅加速此程序隱藏像素為單位。 如果幾何以最佳方式排序，將會一次繪製在螢幕上的每個像素。

要排序的透明幾何需求回到前端，並依賴混用來在螢幕上的目前像素的像素著色器輸出。 這會導致每個像素繪製到多次每個畫面，稱為 「 過度繪製在螢幕上。

HoloLens 和主要電腦，螢幕只可填入少數幾個時間，讓透明轉譯有問題。

## <a name="introduction-to-datascape-scene-components"></a>Datascape 場景元件簡介

我們有三個主要元件至我們的場景;**UI 中，地圖**，並**天氣**。 我們早知道我們的天氣影響會需要它無法取得的所有 GPU 時間，因此我們刻意設計的 UI 和地形會減少任何過度繪製的方式。

我們重新設計了 UI 多次降到最低數量過度繪製它會產生。 我們 erred 側邊更複雜的幾何，而不是覆疊透明圖案在彼此之上的元件，例如發光按鈕和對應的概觀。

對應中，我們使用的自訂著色器會去除標準的 Unity 功能，例如陰影或複雜的光線，取代為簡單的單一 sun 光源模型計算和自訂的霧計算。 這會產生簡單的像素著色器，並釋出 GPU 循環。

我們設法取得 UI 和地圖來轉譯在預算其中並不需要任何變更，根據硬體;不過，天氣視覺效果，尤其是雲端轉譯，證實是更有挑戰性 ！

## <a name="background-on-cloud-data"></a>雲端資料的背景

我們的雲端資料從 NOAA 伺服器下載 (http://nomads.ncep.noaa.gov/)和來到我們在三個不同的 2D 層級，而每個雲端的上方和下方的高度，以及雲端中為每個資料格方格的密度。 資料已處理到雲端資訊材質其中每個元件儲存在 GPU 上方便存取的材質的紅色、 綠色和藍色元件。

## <a name="geometry-clouds"></a>幾何雲端

若要確定我們低電源的電腦可能會造成我們首先決定我們雲端過度繪製一種方法，會使用實線幾何降到最低。

我們第一次嘗試產生每個圖層使用的每個頂點的雲端資訊材質半徑來產生圖形實心和網格來產生雲端。 我們可以使用幾何著色器以產生在頂端和底部的 雲端產生紮實的雲端圖形的頂點。 我們會使用從材質的密度值色彩的更多的密集雲端深色的雲端。

**建立頂點著色器：**

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

我們引進了以取得詳細資料，以實際的資料為基礎的小型的非搜尋模式。 若要產生 round 雲端邊緣，我們裁剪像素像素著色器中的內插補點的半徑值叫用捨棄近乎零值的臨界值時。

![幾何雲端](images/datascape-geometry-clouds-700px.jpg)

由於雲端是單色幾何，可以呈現之前隱藏底下的任何耗費資源的對應像素為單位，以進一步提升畫面播放速率地形。 此解決方案會執行也在最小空間從所有的視訊卡，高階顯示卡，以及 HoloLens，因為實線幾何呈現方法。

## <a name="solid-particle-clouds"></a>Solid 粒子雲端

我們現在必須產生適當的表示法，我們的雲端資料，但已 「 哇 」 因數有點低落並未傳達我們想要讓我們高階的電腦的體積型風格的備份解決方案。

下一步建立雲端代表約 100,000 個物件，以產生更有機和體積型的外觀。

如果物件保持穩固，而且排序前-後，我們仍然有許多優點背後先前呈現的物件，像素的深度緩衝區剔除減少過度繪製。 此外，使用以物件為基礎的解決方案，我們可以改變為目標的不同硬體使用的物件數量。 不過，所有像素仍然需要進行深度測試，而導致某些額外的負荷。

首先，我們會在啟動建立物件周圍的經驗的中心點的位置。 我們發佈更緊密圍繞中心物件和較少的距離。 我們預先排序從中央到後端的所有物件，因此會先呈現最接近的物件。

計算著色器會放置在正確的高度和色彩，其根據密度的每個物件的雲端資訊材質的範例。

我們使用了*DrawProcedural*來呈現每個物件允許完全保持在 GPU 上的物件資料的四倍。

每個物件包含高度和半徑。 以從雲端資訊材質取樣的雲端資料為基礎的高度和半徑根據初始分配，它會計算儲存到其最接近像素的水平距離。 四邊形會調整成本身，因此當使用者查看它的水平靠高度來使用這項資料會顯示高度，且當使用者查看由上而下，會涵蓋與其相鄰項目之間的區域。

![物件圖形](images/particle-shape-700px.png)

**顯示發佈的著色器程式碼：**

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

因為我們排序物件前至後，我們仍使用剪輯 (不是 blend) 透明的像素的實心樣式著色器，這項技術會處理物件，避免成本高昂的過度繪製，即使在低電源的電腦上令人驚訝的數量。

## <a name="transparent-particle-clouds"></a>透明粒子雲端

Solid 物件提供良好的有機感覺到雲端的圖形，但仍需要銷售定域機組的 fluffiness 的項目。 我們因而決定試用我們可以在其中引進 transparency 高階顯示卡的自訂解決方案。

若要這樣做我們只要切換物件的初始排序順序，並變更使用 alpha 的材質著色器。

![Fluffy 雲端](images/fluffy-clouds-700px.jpg)

它看起來很但證實是更困難的機器而言過於沉重的因為它會造成轉譯時間的數百個螢幕上的每個像素 ！

## <a name="render-off-screen-with-lower-resolution"></a>呈現較低解析度的幕外

為了減少由雲端轉譯的像素數，我們開始 （相較於螢幕） 的一季解析緩衝區中將它們呈現並自動縮放的最終結果備份在螢幕上的所有物件具有已都繪製後。 這給了我們大約 4 倍的速度增益，但隨附幾個需要注意的事項。

**轉譯幕外的程式碼：**

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

首先，當呈現到幕外緩衝區，我們遺失所有深入資訊我們主要的場景，請從導致物件後面山地呈現 mountain 之上。

第二，延伸緩衝區也引進了種解析度變更的我們定域機組的邊緣上的成品。 下面兩節會討論我們解決這些問題的方式。

## <a name="particle-depth-buffer"></a>物件的深度緩衝區

若要讓 mountain 或物件可能涵蓋其背後的物件與世界幾何同時存在的物件，我們會填入與深度緩衝區，其中包含的主要場景幾何的幕外緩衝區。 若要產生這類的深度緩衝區，我們建立第二個的相機，呈現僅實線幾何和場景的深度。

我們接著使用新的材質中定域機組的像素著色器 occlude 像素為單位。 我們可以用相同的材質來計算至雲端的像素背後的幾何距離。 藉由使用這麼遠的距離，並將它套用到像素的 alpha，我們現在會影響的雲端淡出，因為它們更接近地形、 移除任何硬碟的剪下符合物件和地形。

![混合成地形模型的雲端](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a>銳利化邊緣

向上延展雲端看起來幾乎完全相同物件的中心的標準大小雲端，或在它們重疊，但會有些成品示範雲端邊緣。 否則清晰的邊緣會看起來是模糊，而且觀景窗移動時，所導入別名的效果。

我們解決幕外緩衝區，以判斷項重大變更相較之下發生 (1) 上執行簡單的著色器。 我們的像素，與重大變更到新的樣板緩衝區 (2)。 然後我們會使用遮罩的樣板緩衝區這些高對比區域時套用的幕外緩衝區到螢幕，導致漏洞之中及四周的雲端 (3)。

我們再轉譯所有物件一次在全螢幕模式中，但這次使用樣板緩衝區表示遮住的所有項目，但邊緣，導致 像素為單位的最少觸及 (4)。 命令緩衝區已建立的物件，所以我們只需要讓呈現一次新的相機。

![轉譯雲端邊緣的進展](images/cloud-steps-1-4-700px.jpg)

最終結果是清晰的邊緣，定域機組的廉價 center 區段。

雖然這遠快於轉譯中的所有物件都全螢幕，沒有測試針對樣板緩衝區的像素，因此產生大量過度繪製仍產生相關成本仍然隨附的成本。

## <a name="culling-particles"></a>挑選出的物件

如需我們風力效果，我們可以產生長的三角形帶狀線計算著色器，建立許多 wisps 風向的世界中。 不大填滿率，因為產生的 skinny 階梯狀 wind 生效時，它會產生許多數十萬的頂點，頂點著色器造成沈重的負載。

我們引進了附加的計算著色器，以摘要風力帶狀線要繪製的子集上的緩衝區。 透過一些簡單的檢視範圍揀選 logic 計算著色器中，我們無法判斷寬帶是否視界之外，並防止它新增至推播的緩衝區。 這帶狀線的數量大幅降低，釋出一些在 GPU 上所需的循環。

**展示附加緩衝區的程式碼：**

*計算著色器：*

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

*C#程式碼：*

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

我們嘗試的雲端物件，我們會在此挑選其上計算著色器，並只推入要呈現的可見物件上使用相同的技巧。 這項技術實際上沒有儲存我們大部分在 GPU 上因為最大的瓶頸是呈現在畫面中，而不計算頂點的成本上的量像素。

這項技術的其他問題已附加緩衝區填入以隨機順序本質平行運算粒子，導致為未排序，導致產生閃爍的雲端物件的已排序的物件。

要排序的推播緩衝區的技術，但數量有限的效能提升，我們從剔除物件會有可能與其他的排序，位移，因此我們決定不追求此最佳化。

## <a name="adaptive-rendering"></a>自適性轉譯

為了確保穩定的應用程式上的畫面播放速率，搭配不同的轉譯條件，例如多雲 vs 的清楚檢視，我們導入了適應性呈現應用程式。

自適性轉譯的第一個步驟是測量 GPU。 我們採用的方法來插入 GPU 命令緩衝區的開頭和結尾呈現的畫面格的自訂程式碼，擷取同時左邊和右邊的眼睛螢幕的時間。

藉由測量轉譯，並和比較，我們了解我們已捨棄畫面如何關閉我們想要重新整理速率，所花費的時間。

當接近捨棄畫面，我們採用我們的轉譯，若要加快。 一個簡單的方式進行調整變更檢視區大小的畫面中，需要取得呈現較少像素為單位。

藉由使用*UnityEngine.XR.XRSettings.renderViewportScale*系統壓縮目標的檢視區，並會自動伸展備份至適當比例 畫面的結果。 小幅變更擴展全球幾何上難以通知而 0.7 縮放比例需要呈現的像素為單位的一半數量。

![70%小數位數一半的像素](images/datascape-scaling-700px.jpg)

當我們偵測到我們在降低影格數我們降低固定數字的小數位數，並增加回我們速度不夠快一次執行時。

雖然我們決定要使用哪些雲端技術為基礎的圖形在啟動時的硬體功能，它可以為基礎的資料是來自 GPU 度量，以防止系統保持在低解析度長的時間，但這一點我們沒有時間 若要瀏覽 Datascape 中。

## <a name="final-thoughts"></a>結論

目標為各種不同的硬體具挑戰性，而且需要一些規劃。

我們建議您先以熟悉問題空間，及開發將在您的機器執行的備份解決方案的低功率電腦為目標。 設計您的解決方案使用的填滿率納入考量，因為像素為單位將會是您最寶貴的資源。 透過透明效果的目標實線幾何。

備份解決方案中,，您可以再啟動高端機器的更多複雜的分層或也許增強您的備份解決方案的解析度。

設計最糟的情況，並可能考慮使用適應性呈現沈重的情況下。

## <a name="about-the-authors"></a>關於作者

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><b>Robert Ferrese</b><br>軟體工程師 @Microsoft</td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><b>Dan Andersson</b><br>軟體工程師 @Microsoft</td>
</tr>
</table>


## <a name="see-also"></a>另請參閱
* [了解效能 for Mixed Reality](understanding-performance-for-mixed-reality.md)
* [Unity 的效能建議](performance-recommendations-for-unity.md)

 
