---
title: 磁片區轉譯
description: 體積型影像包含在整個磁片區中具有不透明度和色彩的豐富資訊，無法輕鬆地表示為表面。 瞭解如何在 Windows Mixed Reality 中有效率地轉譯體積型影像。
author: kevinkennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: 體積型影像，磁片區轉譯，效能，混合現實
ms.openlocfilehash: 6dbb49c31761d4b7b9da5060d15763c3925be754
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277946"
---
# <a name="volume-rendering"></a><span data-ttu-id="25898-105">磁片區轉譯</span><span class="sxs-lookup"><span data-stu-id="25898-105">Volume rendering</span></span>

<span data-ttu-id="25898-106">針對醫療 MRI 或工程區，請參閱[維琪百科上的磁片](https://en.wikipedia.org/wiki/Volume_rendering)區轉譯。</span><span class="sxs-lookup"><span data-stu-id="25898-106">For medical MRI or engineering volumes, see [Volume Rendering on Wikipedia](https://en.wikipedia.org/wiki/Volume_rendering).</span></span> <span data-ttu-id="25898-107">這些「體積型影像」包含豐富的資訊，在整個磁片區中都不透明度和色彩，而無法輕鬆地表示為[多邊形網格](https://en.wikipedia.org/wiki/Polygon_mesh)之類的表面。</span><span class="sxs-lookup"><span data-stu-id="25898-107">These 'volumetric images' contain rich information with opacity and color throughout the volume that cannot be easily expressed as surfaces such as [polygonal meshes](https://en.wikipedia.org/wiki/Polygon_mesh).</span></span>

<span data-ttu-id="25898-108">改善效能的主要解決方案</span><span class="sxs-lookup"><span data-stu-id="25898-108">Key solutions to improve performance</span></span>
1. <span data-ttu-id="25898-109">不良：一般方法：顯示整個磁片區，通常執行速度太慢</span><span class="sxs-lookup"><span data-stu-id="25898-109">BAD: Naïve Approach: Show Whole Volume, generally runs too slowly</span></span>
2. <span data-ttu-id="25898-110">良好：切割平面：只顯示磁片區的單一配量</span><span class="sxs-lookup"><span data-stu-id="25898-110">GOOD: Cutting Plane: Show only a single slice of the volume</span></span>
3. <span data-ttu-id="25898-111">良好：剪下的子卷：只顯示磁片區的幾個圖層</span><span class="sxs-lookup"><span data-stu-id="25898-111">GOOD: Cutting Sub-Volume: Show only a few layers of the volume</span></span>
4. <span data-ttu-id="25898-112">良好：降低磁片區轉譯的解析度（請參閱「混合解析度場景呈現」）</span><span class="sxs-lookup"><span data-stu-id="25898-112">GOOD: Lower the resolution of the volume rendering (see 'Mixed Resolution Scene Rendering')</span></span>

<span data-ttu-id="25898-113">只有特定的資訊數量可以從應用程式傳輸到任何特定畫面中的螢幕，這是總記憶體頻寬。</span><span class="sxs-lookup"><span data-stu-id="25898-113">There is only a certain amount of information that can be transferred from the application to the screen in any particular frame, which is the total memory bandwidth.</span></span> <span data-ttu-id="25898-114">此外，轉換該資料以進行簡報所需的任何處理（或「陰影」）都需要時間。</span><span class="sxs-lookup"><span data-stu-id="25898-114">Also, any processing (or 'shading') required to transform that data for presentation requires time.</span></span> <span data-ttu-id="25898-115">執行磁片區轉譯時的主要考慮如下：</span><span class="sxs-lookup"><span data-stu-id="25898-115">The primary considerations when doing volume rendering are as such:</span></span>
* <span data-ttu-id="25898-116">螢幕寬度 \* 螢幕-高度 \* 螢幕計數 \* 磁片區-每個畫面格-圖元數-每格樣本總數</span><span class="sxs-lookup"><span data-stu-id="25898-116">Screen-Width \* Screen-Height \* Screen-Count \* Volume-Layers-On-That-Pixel = Total-Volume-Samples-Per-Frame</span></span>
* <span data-ttu-id="25898-117">1028 \* 720 \* 2 \* 256 = 378961920 （100%）（完整的 res 磁片區：樣本太多）</span><span class="sxs-lookup"><span data-stu-id="25898-117">1028 \* 720 \* 2 \* 256 = 378961920 (100%) (full res volume: too many samples)</span></span>
* <span data-ttu-id="25898-118">1028 \* 720 \* 2 \* 1 = 1480320 （完整的0.3%）（精簡配量：每圖元1個樣本，執行順暢）</span><span class="sxs-lookup"><span data-stu-id="25898-118">1028 \* 720 \* 2 \* 1 = 1480320 (0.3% of full) (thin slice: 1 sample per pixel, runs smoothly)</span></span>
* <span data-ttu-id="25898-119">1028 \* 720 \* 2 \* 10 = 14803200 （完整的3.9%）（子磁片區配量：每圖元10個樣本，執行相當順暢，外觀為3d）</span><span class="sxs-lookup"><span data-stu-id="25898-119">1028 \* 720 \* 2 \* 10 = 14803200 (3.9% of full) (sub-volume slice: 10 samples per pixel, runs fairly smoothly, looks 3d)</span></span>
* <span data-ttu-id="25898-120">200 \* 200 \* 2 \* 256 = 20480000 （完整的5%）（較低的 res 量：較少的圖元、完整磁片區、看起來像3d，但有點模糊）</span><span class="sxs-lookup"><span data-stu-id="25898-120">200 \* 200 \* 2 \* 256 = 20480000 (5% of full) (lower res volume: fewer pixels, full volume, looks 3d but a bit blurry)</span></span>

## <a name="representing-3d-textures"></a><span data-ttu-id="25898-121">代表3D 材質</span><span class="sxs-lookup"><span data-stu-id="25898-121">Representing 3D Textures</span></span>

<span data-ttu-id="25898-122">在 CPU 上：</span><span class="sxs-lookup"><span data-stu-id="25898-122">On the CPU:</span></span>

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

<span data-ttu-id="25898-123">在 GPU 上：</span><span class="sxs-lookup"><span data-stu-id="25898-123">On the GPU:</span></span>

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

## <a name="shading-and-gradients"></a><span data-ttu-id="25898-124">網底和漸層</span><span class="sxs-lookup"><span data-stu-id="25898-124">Shading and Gradients</span></span>

<span data-ttu-id="25898-125">如何為磁片區加上陰影，例如 MRI，以取得有用的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="25898-125">How to shade a volume, such as MRI, for useful visualization.</span></span> <span data-ttu-id="25898-126">主要方法是有您想要在其中看到濃度的「濃度視窗」（最小和最大值），而只是調整到該空間以查看黑色和白色濃度。</span><span class="sxs-lookup"><span data-stu-id="25898-126">The primary method is to have an 'intensity window' (a min and max) that you want to see intensities within, and simply scale into that space to see the black and white intensity.</span></span> <span data-ttu-id="25898-127">然後，可以將「顏色斜坡」套用到該範圍內的值，並儲存為材質，讓濃度頻譜的不同部分可以著色不同的色彩：</span><span class="sxs-lookup"><span data-stu-id="25898-127">A 'color ramp' can then be applied to the values within that range, and stored as a texture, so that different parts of the intensity spectrum can be shaded different colors:</span></span>

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

<span data-ttu-id="25898-128">在我們的許多應用程式中，我們都會將原始強度值和「分割索引」（用來分隔不同的部分，例如面板和骨骼）儲存在磁片區中，這些區段通常是由專門工具中的專家所建立。</span><span class="sxs-lookup"><span data-stu-id="25898-128">In many of our applications, we store in our volume both a raw intensity value and a 'segmentation index' (to segment different parts such as skin and bone; these segments are generally created by experts in dedicated tools).</span></span> <span data-ttu-id="25898-129">這可以結合上述方法來為每個區段索引放置不同的色彩，或甚至是不同的色彩斜坡：</span><span class="sxs-lookup"><span data-stu-id="25898-129">This can be combined with the approach above to put a different color, or even different color ramp for each segment index:</span></span>

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a><span data-ttu-id="25898-130">著色器中的磁片區切割</span><span class="sxs-lookup"><span data-stu-id="25898-130">Volume Slicing in a Shader</span></span>

<span data-ttu-id="25898-131">最好的第一個步驟是建立「切割平面」，它可以在磁片區中移動、「切割」，以及每個點的掃描值。</span><span class="sxs-lookup"><span data-stu-id="25898-131">A great first step is to create a "slicing plane" that can move through the volume, 'slicing it', and how the scan values at each point.</span></span> <span data-ttu-id="25898-132">這會假設有一個「VolumeSpace」 cube，代表該磁片區在世界空間中的位置，可用來做為放置點的參考：</span><span class="sxs-lookup"><span data-stu-id="25898-132">This assumes that there is a 'VolumeSpace' cube, which represents where the volume is in world space, that can be used as a reference for placing the points:</span></span>

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a><span data-ttu-id="25898-133">著色器中的磁片區追蹤</span><span class="sxs-lookup"><span data-stu-id="25898-133">Volume Tracing in Shaders</span></span>

<span data-ttu-id="25898-134">如何使用 GPU 進行子磁片區追蹤（逐步執行幾個體素，然後將資料的層級從後到前）：</span><span class="sxs-lookup"><span data-stu-id="25898-134">How to use the GPU to do sub-volume tracing (walks a few voxels deep, then layers on the data from back to front):</span></span>

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

## <a name="whole-volume-rendering"></a><span data-ttu-id="25898-135">整個磁片區轉譯</span><span class="sxs-lookup"><span data-stu-id="25898-135">Whole Volume Rendering</span></span>

<span data-ttu-id="25898-136">修改上述的子磁片區程式碼，我們得到：</span><span class="sxs-lookup"><span data-stu-id="25898-136">Modifying the sub-volume code above, we get:</span></span>

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a><span data-ttu-id="25898-137">混合解析度場景呈現</span><span class="sxs-lookup"><span data-stu-id="25898-137">Mixed Resolution Scene Rendering</span></span>

<span data-ttu-id="25898-138">如何以低解析度呈現場景的一部分，並將其放回原處：</span><span class="sxs-lookup"><span data-stu-id="25898-138">How to render a part of the scene with a low resolution and put it back in place:</span></span>
1. <span data-ttu-id="25898-139">設定兩個非螢幕相機，一個用於每個更新每個畫面格的眼睛</span><span class="sxs-lookup"><span data-stu-id="25898-139">Setup two off-screen cameras, one to follow each eye that update each frame</span></span>
2. <span data-ttu-id="25898-140">設定攝影機轉譯成的兩個低解析度轉譯目標（即200x200）</span><span class="sxs-lookup"><span data-stu-id="25898-140">Setup two low-resolution render targets (i.e. 200x200 each) that the cameras render into</span></span>
3. <span data-ttu-id="25898-141">設定在使用者前方移動的四個</span><span class="sxs-lookup"><span data-stu-id="25898-141">Setup a quad that moves in front of the user</span></span>

<span data-ttu-id="25898-142">每個畫面格：</span><span class="sxs-lookup"><span data-stu-id="25898-142">Each Frame:</span></span>
1. <span data-ttu-id="25898-143">以低解析度繪製每個眼睛的轉譯目標（磁片區資料、昂貴的著色器等）</span><span class="sxs-lookup"><span data-stu-id="25898-143">Draw the render targets for each eye at low-resolution (volume data, expensive shaders, etc.)</span></span>
2. <span data-ttu-id="25898-144">將場景正常繪製為完整解析度（網格、UI 等）</span><span class="sxs-lookup"><span data-stu-id="25898-144">Draw the scene normally as full resolution (meshes, UI, etc.)</span></span>
3. <span data-ttu-id="25898-145">在使用者的前方、場景上繪製四個，並將低度的專案轉譯為</span><span class="sxs-lookup"><span data-stu-id="25898-145">Draw a quad in front of the user, over the scene, and project the low-res renders onto that</span></span>
4. <span data-ttu-id="25898-146">結果：具有低解析度但高密度磁片區資料的完整解析度元素的視覺化組合</span><span class="sxs-lookup"><span data-stu-id="25898-146">Result: visual combination of full-resolution elements with low-resolution but high-density volume data</span></span>
