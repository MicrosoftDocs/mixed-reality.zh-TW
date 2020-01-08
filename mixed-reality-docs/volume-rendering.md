---
title: 磁片區轉譯
description: 體積型影像包含在整個磁片區中具有不透明度和色彩的豐富資訊，無法輕鬆地表示為表面。 瞭解如何在 Windows Mixed Reality 中有效率地轉譯體積型影像。
author: KevinKennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: 體積型影像，磁片區轉譯，效能，混合現實
ms.openlocfilehash: 04931df5e4225225e4c11c3f6d72801e2d58f646
ms.sourcegitcommit: 317653cd8500563c514464f0337c1f230a6f3653
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/28/2019
ms.locfileid: "75503827"
---
# <a name="volume-rendering"></a>磁片區轉譯

針對醫療 MRI 或工程區，請參閱[維琪百科上的磁片](https://en.wikipedia.org/wiki/Volume_rendering)區轉譯。 這些「體積型影像」包含豐富的資訊，在整個磁片區中都不透明度和色彩，而無法輕鬆地表示為[多邊形網格](https://en.wikipedia.org/wiki/Polygon_mesh)之類的表面。

改善效能的主要解決方案
1. 不良：一般方法：顯示整個磁片區，通常執行速度太慢
2. 良好：切割平面：只顯示磁片區的單一配量
3. 良好：剪下的子卷：只顯示磁片區的幾個圖層
4. 良好：降低磁片區轉譯的解析度（請參閱「混合解析度場景呈現」）

只有特定的資訊數量可以從應用程式傳輸到任何特定畫面中的螢幕，這是總記憶體頻寬。 此外，轉換該資料以進行簡報所需的任何處理（或「陰影」）都需要時間。 執行磁片區轉譯時的主要考慮如下：
* 螢幕寬度 * 螢幕-高度 * 螢幕計數 * 磁片區-每個畫面格-圖元數-每格樣本總數
* 1028 * 720 * 2 * 256 = 378961920 （100%）（完整的 res 磁片區：樣本太多）
* 1028 * 720 * 2 * 1 = 1480320 （完整的0.3%）（精簡配量：每圖元1個樣本，執行順暢）
* 1028 * 720 * 2 * 10 = 14803200 （完整的3.9%）（子磁片區配量：每圖元10個樣本，執行相當順暢，外觀為3d）
* 200 * 200 * 2 * 256 = 20480000 （完整的5%）（較低的 res 量：較少的圖元、完整磁片區、看起來像3d，但有點模糊）

## <a name="representing-3d-textures"></a>代表3D 材質

在 CPU 上：

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

在 GPU 上：

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

## <a name="shading-and-gradients"></a>網底和漸層

如何為磁片區加上陰影，例如 MRI，以取得有用的視覺效果。 主要方法是有您想要在其中看到濃度的「濃度視窗」（最小和最大值），而只是調整到該空間以查看黑色和白色濃度。 然後，可以將「顏色斜坡」套用到該範圍內的值，並儲存為材質，讓濃度頻譜的不同部分可以著色不同的色彩：

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

在我們的許多應用程式中，我們都會將原始強度值和「分割索引」（用來分隔不同的部分，例如面板和骨骼）儲存在磁片區中，這些區段通常是由專門工具中的專家所建立。 這可以結合上述方法來為每個區段索引放置不同的色彩，或甚至是不同的色彩斜坡：

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a>著色器中的磁片區切割

最好的第一個步驟是建立「切割平面」，它可以在磁片區中移動、「切割」，以及每個點的掃描值。 這會假設有一個「VolumeSpace」 cube，代表該磁片區在世界空間中的位置，可用來做為放置點的參考：

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a>著色器中的磁片區追蹤

如何使用 GPU 進行子磁片區追蹤（逐步執行幾個體素，然後將資料的層級從後到前）：

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

## <a name="whole-volume-rendering"></a>整個磁片區轉譯

修改上述的子磁片區程式碼，我們得到：

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a>混合解析度場景呈現

如何以低解析度呈現場景的一部分，並將其放回原處：
1. 設定兩個非螢幕相機，一個用於每個更新每個畫面格的眼睛
2. 設定攝影機轉譯成的兩個低解析度轉譯目標（即200x200）
3. 設定在使用者前方移動的四個

每個畫面格：
1. 以低解析度繪製每個眼睛的轉譯目標（磁片區資料、昂貴的著色器等）
2. 將場景正常繪製為完整解析度（網格、UI 等）
3. 在使用者的前方、場景上繪製四個，並將低度的專案轉譯為
4. 結果：具有低解析度但高密度磁片區資料的完整解析度元素的視覺化組合
