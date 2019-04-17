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
# <a name="volume-rendering"></a><span data-ttu-id="9a8ac-105">磁碟區轉譯</span><span class="sxs-lookup"><span data-stu-id="9a8ac-105">Volume rendering</span></span>

<span data-ttu-id="9a8ac-106">醫療 MRI 或工程的磁碟區，請參閱[維基百科上的磁碟區呈現](https://en.wikipedia.org/wiki/Volume_rendering)。</span><span class="sxs-lookup"><span data-stu-id="9a8ac-106">For medical MRI or engineering volumes, see [Volume Rendering on Wikipedia](https://en.wikipedia.org/wiki/Volume_rendering).</span></span> <span data-ttu-id="9a8ac-107">這些 '體積型映像' 包含豐富的資訊，使用不透明度和整個無法輕鬆地以呈現這類的磁碟區的色彩[多邊形網格](https://en.wikipedia.org/wiki/Polygon_mesh)。</span><span class="sxs-lookup"><span data-stu-id="9a8ac-107">These 'volumetric images' contain rich information with opacity and color throughout the volume that cannot be easily expressed as surfaces such as [polygonal meshes](https://en.wikipedia.org/wiki/Polygon_mesh).</span></span>

<span data-ttu-id="9a8ac-108">重要的解決方案，以改善效能</span><span class="sxs-lookup"><span data-stu-id="9a8ac-108">Key solutions to improve performance</span></span>
1. <span data-ttu-id="9a8ac-109">錯誤：貝氏方法：顯示整個磁碟區，通常會執行速度過慢</span><span class="sxs-lookup"><span data-stu-id="9a8ac-109">BAD: Naïve Approach: Show Whole Volume, generally runs too slowly</span></span>
2. <span data-ttu-id="9a8ac-110">良好：領域平面：顯示單一扇區的磁碟區</span><span class="sxs-lookup"><span data-stu-id="9a8ac-110">GOOD: Cutting Plane: Show only a single slice of the volume</span></span>
3. <span data-ttu-id="9a8ac-111">良好：剪下的子磁碟區：顯示磁碟區只包含幾個圖層</span><span class="sxs-lookup"><span data-stu-id="9a8ac-111">GOOD: Cutting Sub-Volume: Show only a few layers of the volume</span></span>
4. <span data-ttu-id="9a8ac-112">良好：降低磁碟區呈現的解析度 （請參閱 ' 混合解析場景轉譯 '）</span><span class="sxs-lookup"><span data-stu-id="9a8ac-112">GOOD: Lower the resolution of the volume rendering (see 'Mixed Resolution Scene Rendering')</span></span>

<span data-ttu-id="9a8ac-113">只有一段可傳送至任何特定的畫面格的畫面應用程式的資訊，這是總記憶體頻寬。</span><span class="sxs-lookup"><span data-stu-id="9a8ac-113">There is only a certain amount of information that can be transferred from the application to the screen in any particular frame, this is the total memory bandwidth.</span></span> <span data-ttu-id="9a8ac-114">也才能轉換該資料以供呈現任何處理 （或 '陰影'） 也需要時間。</span><span class="sxs-lookup"><span data-stu-id="9a8ac-114">Also any processing (or 'shading') required to transform that data for presentation also requires time.</span></span> <span data-ttu-id="9a8ac-115">執行磁碟區轉譯時的主要考量是這類：</span><span class="sxs-lookup"><span data-stu-id="9a8ac-115">The primary considerations when doing volume rendering are as such:</span></span>
* <span data-ttu-id="9a8ac-116">螢幕寬度 \* 螢幕高度 \* 螢幕計數 \* 磁碟區層級上-，-像素的 = 總計-磁碟區-範例-每一畫面</span><span class="sxs-lookup"><span data-stu-id="9a8ac-116">Screen-Width \* Screen-Height \* Screen-Count \* Volume-Layers-On-That-Pixel = Total-Volume-Samples-Per-Frame</span></span>
* <span data-ttu-id="9a8ac-117">1028 \* 720 \* 2 \* 256 = 378961920 （100%)(完整 res 磁碟區： 太多的範例)</span><span class="sxs-lookup"><span data-stu-id="9a8ac-117">1028 \* 720 \* 2 \* 256 = 378961920 (100%) (full res volume: too many samples)</span></span>
* <span data-ttu-id="9a8ac-118">1028 \* 720 \* 2 \* 1 = 1480320 （0.3%完整) (細的配量：1 個範例，每像素，順利執行）</span><span class="sxs-lookup"><span data-stu-id="9a8ac-118">1028 \* 720 \* 2 \* 1 = 1480320 (0.3% of full) (thin slice: 1 sample per pixel, runs smoothly)</span></span>
* <span data-ttu-id="9a8ac-119">1028 \* 720 \* 2 \* 10 = 14803200 （3.9%完整) (子磁碟區的配量：10 個樣本，每像素，相當順暢執行，看起來 3d）</span><span class="sxs-lookup"><span data-stu-id="9a8ac-119">1028 \* 720 \* 2 \* 10 = 14803200 (3.9% of full) (sub-volume slice: 10 samples per pixel, runs fairly smoothly, looks 3d)</span></span>
* <span data-ttu-id="9a8ac-120">200 \* 200 \* 2 \* 256 = 20480000 （完整的 5%) (降低 res 磁碟區： 較少像素為單位，完整的磁碟區，看起來 3d，但一些 blury)</span><span class="sxs-lookup"><span data-stu-id="9a8ac-120">200 \* 200 \* 2 \* 256 = 20480000 (5% of full) (lower res volume: fewer pixels, full volume, looks 3d but a bit blury)</span></span>

## <a name="representing-3d-textures"></a><span data-ttu-id="9a8ac-121">表示 3D 材質</span><span class="sxs-lookup"><span data-stu-id="9a8ac-121">Representing 3D Textures</span></span>

<span data-ttu-id="9a8ac-122">在 CPU:</span><span class="sxs-lookup"><span data-stu-id="9a8ac-122">On the CPU:</span></span>

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

<span data-ttu-id="9a8ac-123">GPU:</span><span class="sxs-lookup"><span data-stu-id="9a8ac-123">On the GPU:</span></span>

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

## <a name="shading-and-gradients"></a><span data-ttu-id="9a8ac-124">陰影和漸層</span><span class="sxs-lookup"><span data-stu-id="9a8ac-124">Shading and Gradients</span></span>

<span data-ttu-id="9a8ac-125">以灰色顯示的磁碟區，例如 MRI，實用的視覺效果如何。</span><span class="sxs-lookup"><span data-stu-id="9a8ac-125">How to shade an volume, such as MRI, for useful visualization.</span></span> <span data-ttu-id="9a8ac-126">主要方法是將 '濃度視窗 （最小和最大值） 您想要查看強度內，並只需調整規模以納入該空間，以查看黑白的濃度。</span><span class="sxs-lookup"><span data-stu-id="9a8ac-126">The primary method is to have an 'intensity window' (a min and max) that you want to see intensities within, and simply scale into that space to see the black and white intensity.</span></span> <span data-ttu-id="9a8ac-127">可以套用至該範圍中的值 '色彩 ramp'，然後儲存為材質，好讓濃度極端情況下的不同部分可以是不同的陰影的色彩：</span><span class="sxs-lookup"><span data-stu-id="9a8ac-127">A 'color ramp' can then be applied to the values within that range, and stored as a texture, so that different parts of the intensity spectrum can be shaded different colors:</span></span>

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

<span data-ttu-id="9a8ac-128">在許多應用程式都是原始的濃度值與 '區隔 index' 存入我們的磁碟區 （例如區隔不同的組件的面板骨，這些區段通常建立和專家專用的工具）。</span><span class="sxs-lookup"><span data-stu-id="9a8ac-128">In many our applications we store in our volume both a raw intensity value and a 'segmentation index' (to segment different parts such as skin and bone, these segments are generally created by experts in dedicated tools).</span></span> <span data-ttu-id="9a8ac-129">這可以結合上述放在不同的色彩或甚至是不同的色彩遞增每個區段的索引的方法：</span><span class="sxs-lookup"><span data-stu-id="9a8ac-129">This can be combined with the approach above to put a different color, or even different color ramp for each segment index:</span></span>

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a><span data-ttu-id="9a8ac-130">在 著色器配量的磁碟區</span><span class="sxs-lookup"><span data-stu-id="9a8ac-130">Volume Slicing in a Shader</span></span>

<span data-ttu-id="9a8ac-131">絕佳的第一個步驟是建立 「 切割平面 」，可在移動的磁碟區 '切割它'，與掃描的每個點的值。</span><span class="sxs-lookup"><span data-stu-id="9a8ac-131">A great first step is to create a "slicing plane" that can move through the volume, 'slicing it', and how the scan values at each point.</span></span> <span data-ttu-id="9a8ac-132">這是假設是 'VolumeSpace' cube 中，表示其中的磁碟區是在世界空間中，可以做為參考用放置點：</span><span class="sxs-lookup"><span data-stu-id="9a8ac-132">This assumes that there is a 'VolumeSpace' cube, which represents where the volume is in world space, that can be used as a reference for placing the points:</span></span>

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a><span data-ttu-id="9a8ac-133">著色器中的磁碟區追蹤</span><span class="sxs-lookup"><span data-stu-id="9a8ac-133">Volume Tracing in Shaders</span></span>

<span data-ttu-id="9a8ac-134">如何使用 GPU 來執行 （從逐步解說幾個 voxels 然後深度的層級的資料後最上層） 的子磁碟區追蹤：</span><span class="sxs-lookup"><span data-stu-id="9a8ac-134">How to use the GPU to do sub-volume tracing (walks a few voxels deep then layers on the data from back to front):</span></span>

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

## <a name="whole-volume-rendering"></a><span data-ttu-id="9a8ac-135">整個磁碟區轉譯</span><span class="sxs-lookup"><span data-stu-id="9a8ac-135">Whole Volume Rendering</span></span>

<span data-ttu-id="9a8ac-136">我們收到修改上述的子磁碟區程式碼：</span><span class="sxs-lookup"><span data-stu-id="9a8ac-136">Modifying the sub-volume code above we get:</span></span>

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a><span data-ttu-id="9a8ac-137">混合的解析度場景轉譯</span><span class="sxs-lookup"><span data-stu-id="9a8ac-137">Mixed Resolution Scene Rendering</span></span>

<span data-ttu-id="9a8ac-138">如何呈現低解析度場景的一部分，並將它放入位置：</span><span class="sxs-lookup"><span data-stu-id="9a8ac-138">How to render a part of the scene with a low resolution and put it back in place:</span></span>
1. <span data-ttu-id="9a8ac-139">設定兩個幕外的攝影機，其中遵循每個更新每個畫面格的眼睛</span><span class="sxs-lookup"><span data-stu-id="9a8ac-139">Setup two off-screen cameras, one to follow each eye that update each frame</span></span>
2. <span data-ttu-id="9a8ac-140">設定低解析度的兩個呈現目標 (假設 200 x 200 個)，相機會轉譯成</span><span class="sxs-lookup"><span data-stu-id="9a8ac-140">Setup two low-resolution render targets (say 200x200 each), that the cameras render into</span></span>
3. <span data-ttu-id="9a8ac-141">安裝程式在使用者之前移動四組數字</span><span class="sxs-lookup"><span data-stu-id="9a8ac-141">Setup a quad that moves in front of the user</span></span>

<span data-ttu-id="9a8ac-142">每個畫面格：</span><span class="sxs-lookup"><span data-stu-id="9a8ac-142">Each Frame:</span></span>
1. <span data-ttu-id="9a8ac-143">在低解析度繪製眼睛的轉譯目標 （磁碟區資料、 昂貴的著色器）</span><span class="sxs-lookup"><span data-stu-id="9a8ac-143">Draw the render targets for each eye at low-resolution (volume data, expensive shaders, etc.)</span></span>
2. <span data-ttu-id="9a8ac-144">繪製的場景，通常做為完整的解析度 （網狀結構，UI 等等。）</span><span class="sxs-lookup"><span data-stu-id="9a8ac-144">Draw the scene normally as full resolution (meshes, UI, etc.)</span></span>
3. <span data-ttu-id="9a8ac-145">透過場景，請在使用者中，之前的四組數字和投影的低解析度的轉譯。</span><span class="sxs-lookup"><span data-stu-id="9a8ac-145">Draw a quad in front of the user, over the scene, and project the low-res renders onto that.</span></span>
4. <span data-ttu-id="9a8ac-146">結果： visual 組合的高解析度的低解析度，但高密度的磁碟區資料的項目。</span><span class="sxs-lookup"><span data-stu-id="9a8ac-146">Result: visual combination of full-resolution elements with low-resolution but high-density volume data.</span></span>
