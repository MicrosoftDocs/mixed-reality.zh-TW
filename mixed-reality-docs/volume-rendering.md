---
title: 磁碟區轉譯
description: 體積型的映像包含整個磁碟區無法輕易地表示為表面的色彩不透明度與豐富的資訊。 了解如何有效地呈現 Windows Mixed Reality 體積型映像。
author: KevinKennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: 體積型映像、 磁碟區轉譯、 效能、 混合的實境
ms.openlocfilehash: dc0e75b916ab7cc96be1eccb4ad32ac71f5b75ff
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596680"
---
# <a name="volume-rendering"></a>磁碟區轉譯

醫療 MRI 或工程的磁碟區，請參閱[維基百科上的磁碟區呈現](https://en.wikipedia.org/wiki/Volume_rendering)。 這些 '體積型映像' 包含豐富的資訊，使用不透明度和整個無法輕鬆地以呈現這類的磁碟區的色彩[多邊形網格](https://en.wikipedia.org/wiki/Polygon_mesh)。

重要的解決方案，以改善效能
1. 錯誤：貝氏方法：顯示整個磁碟區，通常會執行速度過慢
2. 良好：領域平面：顯示單一扇區的磁碟區
3. 良好：剪下的子磁碟區：顯示磁碟區只包含幾個圖層
4. 良好：降低磁碟區呈現的解析度 （請參閱 ' 混合解析場景轉譯 '）

只有一段可傳送至任何特定的畫面格的畫面應用程式的資訊，這是總記憶體頻寬。 也才能轉換該資料以供呈現任何處理 （或 '陰影'） 也需要時間。 執行磁碟區轉譯時的主要考量是這類：
* 螢幕寬度 * 螢幕高度 * 螢幕計數 * 磁碟區層級上-，-像素的 = 總計-磁碟區-範例-每一畫面
* 1028 * 720 * 2 * 256 = 378961920 （100%)(完整 res 磁碟區： 太多的範例)
* 1028 * 720 * 2 * 1 = 1480320 （0.3%完整) (細的配量：1 個範例，每像素，順利執行）
* 1028 * 720 * 2 * 10 = 14803200 （3.9%完整) (子磁碟區的配量：10 個樣本，每像素，相當順暢執行，看起來 3d）
* 200 * 200 * 2 * 256 = 20480000 （完整的 5%) (降低 res 磁碟區： 較少像素為單位，完整的磁碟區，看起來 3d，但一些 blury)

## <a name="representing-3d-textures"></a>表示 3D 材質

在 CPU:

```
public struct Int3 { public int X, Y, Z; /* ... */ }
 public class VolumeHeader  {
   public readonly Int3 Size;
   public VolumeHeader(Int3 size) { this.Size = size;  }
   public int CubicToLinearIndex(Int3 index) {
     return index.X + (index.Y * (Size.X)) + (index.Z * (Size.X * Size.Y));
   }
   public Int3 LinearToCubicIndex(int linearIndex)
   {
     return new Int3((linearIndex / 1) % Size.X,
       (linearIndex / Size.X) % Size.Y,
       (linearIndex / (Size.X * Size.Y)) % Size.Z);
   }
   /* ... */
 }
 public class VolumeBuffer<T> {
   public readonly VolumeHeader Header;
   public readonly T[] DataArray;
   public T GetVoxel(Int3 pos)        {
     return this.DataArray[this.Header.CubicToLinearIndex(pos)];
   }
   public void SetVoxel(Int3 pos, T val)        {
     this.DataArray[this.Header.CubicToLinearIndex(pos)] = val;
   }
   public T this[Int3 pos] {
     get { return this.GetVoxel(pos); }
     set { this.SetVoxel(pos, value); }
   }
   /* ... */
 }
```

GPU:

```
float3 _VolBufferSize;
 int3 UnitVolumeToIntVolume(float3 coord) {
   return (int3)( coord * _VolBufferSize.xyz );
 }
 int IntVolumeToLinearIndex(int3 coord, int3 size) {
   return coord.x + ( coord.y * size.x ) + ( coord.z * ( size.x * size.y ) );
 }
 uniform StructuredBuffer<float> _VolBuffer;
 float SampleVol(float3 coord3 ) {
   int3 intIndex3 = UnitVolumeToIntVolume( coord3 );
   int index1D = IntVolumeToLinearIndex( intIndex3, _VolBufferSize.xyz);
   return __VolBuffer[index1D];
 }
```

## <a name="shading-and-gradients"></a>陰影和漸層

以灰色顯示的磁碟區，例如 MRI，實用的視覺效果如何。 主要方法是將 '濃度視窗 （最小和最大值） 您想要查看強度內，並只需調整規模以納入該空間，以查看黑白的濃度。 可以套用至該範圍中的值 '色彩 ramp'，然後儲存為材質，好讓濃度極端情況下的不同部分可以是不同的陰影的色彩：

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

在許多應用程式都是原始的濃度值與 '區隔 index' 存入我們的磁碟區 （例如區隔不同的組件的面板骨，這些區段通常建立和專家專用的工具）。 這可以結合上述放在不同的色彩或甚至是不同的色彩遞增每個區段的索引的方法：

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a>在 著色器配量的磁碟區

絕佳的第一個步驟是建立 「 切割平面 」，可在移動的磁碟區 '切割它'，與掃描的每個點的值。 這是假設是 'VolumeSpace' cube 中，表示其中的磁碟區是在世界空間中，可以做為參考用放置點：

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a>著色器中的磁碟區追蹤

如何使用 GPU 來執行 （從逐步解說幾個 voxels 然後深度的層級的資料後最上層） 的子磁碟區追蹤：

```
float4 AlphaBlend(float4 dst, float4 src) {
   float4 res = (src * src.a) + (dst - dst * src.a);
   res.a = src.a + (dst.a - dst.a*src.a);
   return res;
 }
 float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 0.15; // depth in volume space, customize!!!
   float numLoops = 10; // can be 400 on nice PC
   float4 curColor = float4(0, 0, 0, 0);
   // Figure out front and back volume coords to walk through:
   float3 frontCoord = objPosStart;
   float3 backCoord = frontPos + (normalize(cameraPosVolSpace - objPosStart) * maxDepth);
   float3 stepCoord = (frontCoord - backCoord) / numLoops;
   float3 curCoord = backCoord;
   // Add per-pixel random offset, avoids layer aliasing:
   curCoord += stepCoord * RandomFromPositionFast(objPosStart);
   // Walk from back to front (to make front appear in-front of back):
   for (float i = 0; i < numLoops; i++) {
     float intensity = SampleVol(curCoord);
     float4 shaded = ShadeVol(intensity);
     curColor = AlphaBlend(curColor, shaded);
     curCoord += stepCoord;
   }
   return curColor;
 }
```

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos.xyz, 1));
 float4 cameraInVolSpace = mul(_WorldToVolume, float4(_WorldSpaceCameraPos.xyz, 1));
```

```
// In the pixel shader:
 float4 color = volTraceSubVolume( volSpace, cameraInVolSpace );
```

## <a name="whole-volume-rendering"></a>整個磁碟區轉譯

我們收到修改上述的子磁碟區程式碼：

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a>混合的解析度場景轉譯

如何呈現低解析度場景的一部分，並將它放入位置：
1. 設定兩個幕外的攝影機，其中遵循每個更新每個畫面格的眼睛
2. 設定低解析度的兩個呈現目標 (假設 200 x 200 個)，相機會轉譯成
3. 安裝程式在使用者之前移動四組數字

每個畫面格：
1. 在低解析度繪製眼睛的轉譯目標 （磁碟區資料、 昂貴的著色器）
2. 繪製的場景，通常做為完整的解析度 （網狀結構，UI 等等。）
3. 透過場景，請在使用者中，之前的四組數字和投影的低解析度的轉譯。
4. 結果： visual 組合的高解析度的低解析度，但高密度的磁碟區資料的項目。
