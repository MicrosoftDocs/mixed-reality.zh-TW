---
title: 案例研究-在不同效能的裝置上調整 Datascape
description: 此案例研究可讓您深入瞭解 Microsoft 開發人員如何將 Datascape 應用程式優化，以透過各種效能功能，在裝置之間提供引人注目的體驗。
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 沉浸式耳機、效能優化、VR、案例研究
ms.openlocfilehash: 05f97188c81d85685540be998111ecfc47d9ef9c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436511"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a>案例研究-在不同效能的裝置上調整 Datascape

Datascape 是 Microsoft 內部開發的 Windows Mixed Reality 應用程式，我們將焦點放在在地形資料上顯示天氣資料。 應用程式會藉由將使用者與全像攝影資料視覺效果括住，探索使用者在混合現實中探索資料所獲得的獨特見解。

針對 Datascape，我們想要以各種不同的平臺為目標，包括從 Microsoft HoloLens 到 Windows Mixed Reality 的沉浸式耳機，以及從低電源的電腦到具有高階 GPU 的最新電腦。 主要的挑戰是以視覺上吸引人的方式來呈現場景，而這些裝置的圖形功能截然不同，同時以高幀的速度執行。

此案例研究將逐步解說用來建立一些較多 GPU 密集型系統的程式和技術，並說明我們遇到的問題以及如何克服了它們。

## <a name="transparency-and-overdraw"></a>透明度和過度繪製

我們的主要轉譯掙扎會處理透明度，因為透明度在 GPU 上可能會耗用大量資源。

在寫入深度緩衝區時，可以將固定幾何向前轉譯，以停止捨棄該圖元背後的任何未來圖元。 這可避免隱藏圖元執行圖元著色器，並大幅加快進程的速度。 如果幾何是以最佳方式排序，螢幕上的每個圖元只會繪製一次。

透明幾何必須重新排序回到 front，而且需要將圖元著色器的輸出與螢幕上的目前圖元進行混合。 這可能會導致畫面上每個圖元繪製到每個畫面格多次，稱為過度繪製。

若是 HoloLens 和主流電腦，畫面只會填滿幾次，使透明呈現有問題。

## <a name="introduction-to-datascape-scene-components"></a>Datascape 場景元件簡介

我們的場景有三個主要元件;**UI、地圖**和**天氣**。 我們及早知道我們的氣象效應需要所有的 GPU 時間，因此我們刻意以減少任何過度繪製的方式設計 UI 和地形。

我們已將 UI 改編數次，以將所產生的過度繪製量降到最低。 我們會在更複雜的幾何端大錯特錯人，而不是針對發光按鈕和地圖總覽等元件，將透明的圖案疊加在彼此之上。

針對地圖，我們使用自訂著色器來去除標準 Unity 功能（例如陰影和複雜光源），以簡單的單一 sun 光源模型和自訂的霧化計算來取代它們。 這會產生簡單的圖元著色器，並釋放 GPU 週期。

我們設法讓 UI 和地圖在預算中呈現，而不需要對它們進行任何變更（視硬體而定）。不過，氣象視覺效果（尤其是雲端轉譯）證明是一項挑戰！

## <a name="background-on-cloud-data"></a>雲端資料的背景

我們的雲端資料是從 NOAA 伺服器下載（ https://nomads.ncep.noaa.gov/) ，並在三個不同的2D 圖層中提供給我們，每個都有雲端的上而下高度，以及格線的每個資料格的雲端密度。 資料已處理到雲端資訊材質，其中每個元件都儲存在材質的紅色、綠色和藍色元件中，以便在 GPU 上輕鬆存取。

## <a name="geometry-clouds"></a>Geometry 雲端

為了確保我們的低電源機器可以轉譯我們的雲端，我們決定從使用固態幾何來將過度繪製降至最低的方法開始。

我們先嘗試產生雲端，方法是使用每個頂點的雲端資訊材質半徑來產生圖形，為每個圖層產生一個穩固的 heightmap 網格。 我們使用了幾何著色器，在雲端產生穩固的雲端圖形時，同時在其上方和底部產生頂點。 我們使用材質的密度值，以較高的雲端色彩來為雲端著色。

**用於建立頂點的著色器：**

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

我們引進了一個小型的雜訊模式，以取得實際資料的詳細資訊。 若要產生圓角的雲端邊緣，我們會在插入半徑值達到閾值以捨棄接近零的值時，裁剪圖元著色器中的圖元。

![Geometry 雲端](images/datascape-geometry-clouds-700px.jpg)

由於雲端是穩固的幾何，因此可以在地形之前轉譯，以隱藏下任何昂貴的地圖圖元，以進一步改善畫面播放速率。 此解決方案適用于從最小規格到高階圖形配接器的所有圖形配接器，以及 HoloLens，因為其為固態幾何轉譯方法。

## <a name="solid-particle-clouds"></a>實心物件雲端

我們現在有一個備份解決方案，它會產生適當的雲端資料標記法，但在「wow」因素中有點 lackluster，而且不會針對我們的高階機器傳達所需的體積型風格。

我們的下一步是以大約100000的粒子來建立雲端，以產生更具有機和體積型的外觀。

如果粒子保持不變，並在前端進行排序，我們仍然可以受益于先前轉譯之粒子背後圖元的深度緩衝區剔除，以減少過度繪製。 此外，使用以物件為基礎的解決方案時，我們可以改變用來以不同硬體為目標的粒子量。 不過，所有圖元仍然需要深度測試，這會導致一些額外的負荷。

首先，我們在啟動時，建立了在經驗中心點周圍的物件位置。 我們在中心前後散佈了密集，而不是距離。 我們已預先排序從中心到後的所有粒子，讓最接近的粒子先呈現。

計算著色器會取樣雲端資訊材質，以正確的高度定位每個物件，並根據密度來加以色彩。

我們使用*DrawProcedural*來轉譯每個物件四個，讓物件資料隨時保持在 GPU 上。

每個物件都包含高度和半徑。 高度是以雲端資訊材質取樣的雲端資料為基礎，而半徑是根據初始分佈，其計算方式是將水準距離儲存至其最近的鄰近位置。 四邊形會使用這項資料，將其本身設為高度的角度，讓使用者能以水準方式查看，高度會顯示出來，而當使用者從上而下查看時，會涵蓋其鄰近專案之間的區域。

![物件圖形](images/particle-shape-700px.png)

**顯示分佈的著色器程式碼：**

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

由於我們會將粒子向前排序，而且我們仍使用純色著色器來裁剪（而不是 blend）透明圖元，因此這項技術會處理驚人的粒子量，即使在較低的電腦上，也能避免昂貴的過度繪製。

## <a name="transparent-particle-clouds"></a>透明的物件雲端

穩固的微粒為雲端的形狀提供了良好的有機風格，但仍需要銷售雲端 fluffiness 的東西。 我們決定針對可引進透明度的高階圖形配接器嘗試自訂解決方案。

為了這麼做，我們只是切換了粒子的初始排序次序，並將著色器變更為使用材質 Alpha。

![Fluffy 雲端](images/fluffy-clouds-700px.jpg)

它看起來很棒，但證明即使是最棘手的機器，也是太大，因為這會導致螢幕上的每個圖元呈現數百次！

## <a name="render-off-screen-with-lower-resolution"></a>以較低解析度呈現螢幕上的

為了減少雲端所轉譯的圖元數，我們開始將它們呈現在四分之一解析度緩衝區中（與螢幕相較之下），並在繪製所有的微粒之後，將最後的結果延展到螢幕上。 這讓我們達到4倍的速度，但有幾個注意事項。

**以畫面呈現的程式碼：**

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

第一，當轉譯成非螢幕緩衝區時，我們會遺失主要場景的所有深度資訊，導致山脈呈現在山地之上。

第二，延伸緩衝區也會在我們的雲端邊緣導入的構件，其中的解決方式變更很明顯。 接下來的兩節將討論如何解決這些問題。

## <a name="particle-depth-buffer"></a>物件深度緩衝區

為了讓您的微粒與世界幾何並存，其中的山地或物件可以涵蓋其背後的微粒，我們以深度緩衝區擴展出螢幕緩衝區，其中包含主要場景的幾何。 為了產生這類深度緩衝區，我們建立了第二張攝影機，只呈現場景的穩固幾何和深度。

然後，我們在雲端的圖元著色器中使用新材質來遮蔽圖元。 我們使用相同的材質來計算雲端圖元背後幾何的距離。 藉由使用該距離並將其套用到圖元的 Alpha，我們現在讓雲端的效果淡出，因為它們接近地形，因此會移除任何與微粒和地形符合的硬式切割。

![混合成地形的雲端](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a>銳化邊緣

向上延展的雲端看起來幾乎與位於或彼此重迭的一般大小雲端相同，但在雲端邊緣有一些成品。 否則，銳利邊緣會顯得模糊不清，而且當相機移動時，會引進別名效果。

我們解決了這種情況，方法是在非螢幕緩衝區上執行簡單的著色器，判斷發生重大變更的情況（1）。 我們會將具有重大變更的圖元放入新的樣板緩衝區（2）。 接著，我們使用樣板緩衝區，在將外螢幕緩衝區套用回螢幕時，遮罩掉這些高對比區域，因而導致雲端中的漏洞（3）。

然後，我們會以全螢幕模式再次呈現所有的微粒，但這次使用樣板緩衝區來遮罩邊緣以外的所有專案，而導致最小的圖元組觸及（4）。 由於已為粒子建立命令緩衝區，因此我們只需要再次將它轉譯到新的相機。

![呈現雲端邊緣的進展](images/cloud-steps-1-4-700px.jpg)

最終結果是以雲端的便宜中心區段來利邊緣。

雖然這比在全螢幕中轉譯所有的微粒快，但仍有與針對樣板緩衝區測試圖元相關聯的成本，因此大量的過度繪製仍會產生成本。

## <a name="culling-particles"></a>剔除粒子

針對我們的風效果，我們在計算著色器中產生長三角形的去除，並在世界各地建立許多 wisps。 雖然由於產生訣竅的結果，而不會對填滿率造成沉重的影響，但它產生了數十萬個頂點，因而導致頂點著色器的負載過重。

我們在計算著色器上引進了附加緩衝區，以饋送要繪製之風的部分。 使用一些簡單的視圖，在計算著色器中剔除邏輯時，我們可以判斷帶狀是否在相機外，並防止它加入推播緩衝區。 這會大幅減少分割量，並在 GPU 上釋放一些所需的迴圈。

**示範附加緩衝區的程式碼：**

*計算著色器：*

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

*C#錯誤碼*

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

我們嘗試在雲端的粒子上使用相同的技巧，我們會在計算著色器上挑選它們，並只推送要呈現的可見粒子。 這項技術實際上並不會在 GPU 上節省大量的空間，因為最大的瓶頸是螢幕上呈現的圖元量，而不是計算頂點的成本。

這項技術的另一個問題是，附加緩衝區會以隨機順序擴展，因為它會平行處理其運算，而使排序的微粒不會排序，而導致雲端的微粒。

有一些方法可以排序推播緩衝區，但我們從剔除的部分取得的效能提升數量可能會與其他排序有時差，所以我們決定不採用這項優化。

## <a name="adaptive-rendering"></a>適應性呈現

為了確保在應用程式上使用不同的轉譯條件（例如，像是一種雲與清楚的觀點），其呈穩定的畫面播放速率，我們為應用程式引進了適應性轉譯

適應性轉譯的第一個步驟是測量 GPU。 我們的做法是將自訂程式碼插入 GPU 命令緩衝區，並在轉譯的框架開頭和結尾處，同時捕捉左右畫面時間。

藉由測量花費在轉譯的時間，並將其與我們所需的重新整理率進行比較，我們就可以瞭解如何關閉畫面。

當關閉畫面時，我們會調整轉譯，讓它更快速。 一個簡單的調整方式是變更螢幕的視口大小，而需要較少的圖元來呈現。

藉由使用*UnityEngine. XR. renderViewportScale* ，系統會縮小目標的視口，並自動將結果向上調整為符合畫面。 小規模的小規模變更在世界幾何上幾乎不明顯，而縮放比例為0.7 需要呈現一半的圖元量。

![70% 的比例，一半的圖元](images/datascape-scaling-700px.jpg)

當我們偵測到我們即將捨棄畫面格時，我們會以固定的數位來降低尺規，並在執行得夠快時將它增加回來。

雖然我們在啟動時決定要根據硬體的圖形功能來使用哪個雲端技術，但還是可以根據 GPU 測量的資料來避免系統長時間保持低解析度，但這是我們沒有時間的問題 在 Datascape 中探索。

## <a name="final-thoughts"></a>最後的想法

以各種不同的硬體為目標是一項挑戰，需要進行一些規劃。

我們建議您開始以較低電源的電腦為目標，以熟悉問題空間，並開發將在所有電腦上執行的備份解決方案。 設計您的解決方案，並記住其填滿率，因為圖元是您最寶貴的資源。 透過透明度的目標穩固幾何。

有了備份解決方案，您就可以在高階機器上以更複雜的方式開始分層，或只是加強備份解決方案的解析。

針對最糟的案例進行設計，而且可能會考慮針對繁重的情況使用適應性呈現。

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


## <a name="see-also"></a>請參閱
* [瞭解混合現實的效能](understanding-performance-for-mixed-reality.md)
* [Unity 的效能建議](performance-recommendations-for-unity.md)

 
