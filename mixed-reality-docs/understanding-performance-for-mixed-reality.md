---
title: 瞭解混合現實的效能
description: 優化 Windows Mixed Reality 應用程式效能的 Advanced 主題和詳細資料
author: Troy-Ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: Windows Mixed Reality，混合現實，虛擬實境，VR，MR，效能，優化，CPU，GPU
ms.openlocfilehash: 7d8a0c95d59ec7e42e11bc1e1b6b40c702e01529
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438240"
---
# <a name="understanding-performance-for-mixed-reality"></a><span data-ttu-id="b962e-104">瞭解混合現實的效能</span><span class="sxs-lookup"><span data-stu-id="b962e-104">Understanding performance for mixed reality</span></span>

<span data-ttu-id="b962e-105">本文介紹如何瞭解混合現實應用程式的效能重要性。</span><span class="sxs-lookup"><span data-stu-id="b962e-105">This article is an introduction to understanding the significance of performance for your Mixed Reality app.</span></span>  <span data-ttu-id="b962e-106">如果您的應用程式未以最佳畫面播放速率執行，則使用者體驗可能會大幅降低。</span><span class="sxs-lookup"><span data-stu-id="b962e-106">User experience can be greatly degraded if your application does not run at optimal frame rate.</span></span> <span data-ttu-id="b962e-107">全像投影會出現不穩定的情況，而環境的頭追蹤則不正確，導致使用者的體驗不佳。</span><span class="sxs-lookup"><span data-stu-id="b962e-107">Holograms will appear unstable and head tracking of the environment will be inaccurate, leading to an poor experience for the user.</span></span> <span data-ttu-id="b962e-108">效能必須視為混合現實開發的第一類功能，而不是波蘭文工作。</span><span class="sxs-lookup"><span data-stu-id="b962e-108">Performance must be considered a first class feature for mixed reality development and not a polish task.</span></span>

<span data-ttu-id="b962e-109">以下列出每個目標平臺的高效能速率值。</span><span class="sxs-lookup"><span data-stu-id="b962e-109">The performant framerate values for each target platform are listed below.</span></span>

| <span data-ttu-id="b962e-110">平台</span><span class="sxs-lookup"><span data-stu-id="b962e-110">Platform</span></span> | <span data-ttu-id="b962e-111">目標畫面播放速率</span><span class="sxs-lookup"><span data-stu-id="b962e-111">Target Frame Rate</span></span> |
|----------|-------------------|
| [<span data-ttu-id="b962e-112">HoloLens</span><span class="sxs-lookup"><span data-stu-id="b962e-112">HoloLens</span></span>](hololens-hardware-details.md) | <span data-ttu-id="b962e-113">60 FPS</span><span class="sxs-lookup"><span data-stu-id="b962e-113">60 FPS</span></span> |
| [<span data-ttu-id="b962e-114">Windows Mixed Reality Ultra 電腦</span><span class="sxs-lookup"><span data-stu-id="b962e-114">Windows Mixed Reality Ultra PCs</span></span>](immersive-headset-hardware-details.md) | <span data-ttu-id="b962e-115">90 FPS</span><span class="sxs-lookup"><span data-stu-id="b962e-115">90 FPS</span></span> |
| [<span data-ttu-id="b962e-116">Windows Mixed Reality 電腦</span><span class="sxs-lookup"><span data-stu-id="b962e-116">Windows Mixed Reality PCs</span></span>](immersive-headset-hardware-details.md) | <span data-ttu-id="b962e-117">60 FPS</span><span class="sxs-lookup"><span data-stu-id="b962e-117">60 FPS</span></span> |

<span data-ttu-id="b962e-118">以下架構概述達到目標畫面播放速率的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="b962e-118">The framework below outlines best practices for hitting target frame rates.</span></span> <span data-ttu-id="b962e-119">如果在 Unity 中進行開發，請考慮閱讀[unity 的效能建議一文](performance-recommendations-for-unity.md)，以取得在 Unity 環境中測量和改善畫面播放速率的秘訣。</span><span class="sxs-lookup"><span data-stu-id="b962e-119">If developing in Unity, consider reading the [performance recommendations for Unity article](performance-recommendations-for-unity.md) for tips on measuring and improving framerate in the Unity environment.</span></span>

## <a name="understanding-performance-bottlenecks"></a><span data-ttu-id="b962e-120">瞭解效能瓶頸</span><span class="sxs-lookup"><span data-stu-id="b962e-120">Understanding performance bottlenecks</span></span>

<span data-ttu-id="b962e-121">如果您的應用程式具有表現不佳的畫面播放速率，第一個步驟是分析並瞭解您的應用程式需要大量計算的位置。</span><span class="sxs-lookup"><span data-stu-id="b962e-121">If your app has an underperforming framerate, the first step is to analyze and understand where your application is computationally intensive.</span></span> <span data-ttu-id="b962e-122">有兩個主要處理器負責呈現場景的工作： CPU 和 GPU。</span><span class="sxs-lookup"><span data-stu-id="b962e-122">There are two primary processors responsible for the work to render your scene: the CPU and the GPU.</span></span> <span data-ttu-id="b962e-123">每個都處理您混合現實應用程式的不同層面。</span><span class="sxs-lookup"><span data-stu-id="b962e-123">Each of these handle different aspects of your Mixed Reality app.</span></span> <span data-ttu-id="b962e-124">有三個主要位置可能發生瓶頸：</span><span class="sxs-lookup"><span data-stu-id="b962e-124">There are three key places where bottlenecks may occur:</span></span> 

1. <span data-ttu-id="b962e-125">**應用程式執行緒-CPU** -此執行緒負責您的應用程式邏輯。</span><span class="sxs-lookup"><span data-stu-id="b962e-125">**App Thread - CPU** - This thread is responsible for your app logic.</span></span> <span data-ttu-id="b962e-126">這包括處理輸入、動畫、物理和其他應用程式邏輯。</span><span class="sxs-lookup"><span data-stu-id="b962e-126">This includes processing input, animations, physics, and other app logic.</span></span>
2. <span data-ttu-id="b962e-127">**將執行緒 CPU 轉譯為 gpu** -此執行緒負責將您的繪製呼叫提交至 gpu。</span><span class="sxs-lookup"><span data-stu-id="b962e-127">**Render Thread - CPU to GPU** - This thread is responsible for submitting your draw calls to the GPU.</span></span> <span data-ttu-id="b962e-128">當您的應用程式想要呈現物件（例如 cube 或模型）時，此執行緒會將要求傳送至 GPU 以執行這些作業。</span><span class="sxs-lookup"><span data-stu-id="b962e-128">When your app wants to render an object such as a cube or model, this thread sends a request to the GPU to perform these operations.</span></span>
3. <span data-ttu-id="b962e-129">**GPU** -此處理器最常處理應用程式的圖形管線，以將3d 資料（模型、紋理等）轉換成圖元。</span><span class="sxs-lookup"><span data-stu-id="b962e-129">**GPU** - This processor most commonly handles the graphics pipeline of your application to transform 3D data (models, textures, etc.) into pixels.</span></span> <span data-ttu-id="b962e-130">最後，它會產生2D 影像以提交至裝置的螢幕。</span><span class="sxs-lookup"><span data-stu-id="b962e-130">It ultimately produces a 2D image to submit to your device's screen.</span></span>

![框架的存留期](images/lifetime-of-a-frame.png)

<span data-ttu-id="b962e-132">通常，HoloLens 應用程式會受到 GPU 的限制，但不一定是固定的。</span><span class="sxs-lookup"><span data-stu-id="b962e-132">Generally, HoloLens applications will be GPU bound, but not always.</span></span> <span data-ttu-id="b962e-133">使用下列工具和技術來瞭解您的特定應用程式瓶頸的位置。</span><span class="sxs-lookup"><span data-stu-id="b962e-133">Use the tools and techniques below to understand where your particular app is bottlenecked.</span></span>

## <a name="how-to-analyze-your-application"></a><span data-ttu-id="b962e-134">如何分析您的應用程式</span><span class="sxs-lookup"><span data-stu-id="b962e-134">How to analyze your application</span></span>

<span data-ttu-id="b962e-135">有許多工具可讓您瞭解混合現實應用程式的效能設定檔。</span><span class="sxs-lookup"><span data-stu-id="b962e-135">There are many tools that allow you to understand the performance profile of your mixed reality application.</span></span> <span data-ttu-id="b962e-136">這些可讓您找出發生瓶頸的位置和原因，讓您可以解決問題。</span><span class="sxs-lookup"><span data-stu-id="b962e-136">These will enable you to find where and why you have bottlenecks, so you can address them.</span></span>

<span data-ttu-id="b962e-137">以下是取得應用程式深入分析資訊的一些常見工具：</span><span class="sxs-lookup"><span data-stu-id="b962e-137">Below are some common tools to gain deep profiling information for your application:</span></span>
- [<span data-ttu-id="b962e-138">Intel 圖形效能分析器</span><span class="sxs-lookup"><span data-stu-id="b962e-138">Intel Graphics Performance Analyzers</span></span>](https://software.intel.com/gpa)
- [<span data-ttu-id="b962e-139">Visual Studio 圖形偵錯工具</span><span class="sxs-lookup"><span data-stu-id="b962e-139">Visual Studio Graphics Debuggers</span></span>](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [<span data-ttu-id="b962e-140">Unity Profiler</span><span class="sxs-lookup"><span data-stu-id="b962e-140">Unity Profiler</span></span>](https://docs.unity3d.com/Manual/Profiler.html)
- [<span data-ttu-id="b962e-141">Unity 框架偵錯工具</span><span class="sxs-lookup"><span data-stu-id="b962e-141">Unity Frame Debugger</span></span>](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a><span data-ttu-id="b962e-142">如何在任何環境中進行分析</span><span class="sxs-lookup"><span data-stu-id="b962e-142">How to profile in any environment</span></span>

<span data-ttu-id="b962e-143">判斷您的應用程式中是否已系結 GPU 或 CPU 系結的一種方式，是降低轉譯目標輸出的解析度。</span><span class="sxs-lookup"><span data-stu-id="b962e-143">One way to determine if you are GPU bound or CPU bound in your application is to decrease the resolution of the render target output.</span></span> <span data-ttu-id="b962e-144">藉由減少要計算的圖元數，這將可減少您的 GPU 負載。</span><span class="sxs-lookup"><span data-stu-id="b962e-144">By reducing the number of pixels to calculate, this will reduce your GPU load.</span></span> <span data-ttu-id="b962e-145">裝置會轉譯成較小的材質，然後向上取樣以顯示您的最終影像。</span><span class="sxs-lookup"><span data-stu-id="b962e-145">The device will render to a smaller texture, then up-sample to display your final image.</span></span>

<span data-ttu-id="b962e-146">在減少轉譯解析度之後，如果：</span><span class="sxs-lookup"><span data-stu-id="b962e-146">After decreasing rendering resolution, if:</span></span>
1) <span data-ttu-id="b962e-147">應用程式的畫面播放速率**會增加**，因此您可能會受到**GPU 的限制**</span><span class="sxs-lookup"><span data-stu-id="b962e-147">Application framerate **increases**, then you are likely **GPU Bound**</span></span>
1) <span data-ttu-id="b962e-148">應用程式的畫面播放速率**未**變更，您可能會受到**CPU 限制**</span><span class="sxs-lookup"><span data-stu-id="b962e-148">Application framerate **unchanged**, then you are likely **CPU Bound**</span></span>

>[!NOTE]
><span data-ttu-id="b962e-149">Unity 可讓您透過 *[XRSettings renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 屬性，在執行時間輕鬆修改應用程式的呈現目標解析度。</span><span class="sxs-lookup"><span data-stu-id="b962e-149">Unity provides the ability to easily modify the render target resolution of your application at runtime through the *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* property.</span></span> <span data-ttu-id="b962e-150">裝置上顯示的最終映射具有固定的解析度。</span><span class="sxs-lookup"><span data-stu-id="b962e-150">The final image presented on device has a fixed resolution.</span></span> <span data-ttu-id="b962e-151">平臺會取樣較低的解析度輸出，以建立更高解析度的影像，以便在顯示器上呈現。</span><span class="sxs-lookup"><span data-stu-id="b962e-151">The platform will sample the lower resolution output to build a higher resolution image for rendering on displays.</span></span> 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a><span data-ttu-id="b962e-152">如何改善您的應用程式</span><span class="sxs-lookup"><span data-stu-id="b962e-152">How to improve your application</span></span>

### <a name="cpu-performance-recommendations"></a><span data-ttu-id="b962e-153">CPU 效能建議</span><span class="sxs-lookup"><span data-stu-id="b962e-153">CPU performance recommendations</span></span>

<span data-ttu-id="b962e-154">一般來說，CPU 上混合現實應用程式中的大部分工作都牽涉到執行場景的「模擬」，以及處理您的應用程式邏輯。</span><span class="sxs-lookup"><span data-stu-id="b962e-154">Generally, most work in a mixed reality application on the CPU involves performing the "simulation" of the scene and processing your application logic.</span></span> <span data-ttu-id="b962e-155">下欄區域通常會以優化為目標：</span><span class="sxs-lookup"><span data-stu-id="b962e-155">The following areas are usually targeted for optimization:</span></span>

- <span data-ttu-id="b962e-156">動畫</span><span class="sxs-lookup"><span data-stu-id="b962e-156">Animations</span></span>
- <span data-ttu-id="b962e-157">物理</span><span class="sxs-lookup"><span data-stu-id="b962e-157">Physics</span></span>
- <span data-ttu-id="b962e-158">記憶體配置</span><span class="sxs-lookup"><span data-stu-id="b962e-158">Memory allocations</span></span>
- <span data-ttu-id="b962e-159">複雜演算法（亦即</span><span class="sxs-lookup"><span data-stu-id="b962e-159">Complex algorithms (i.e</span></span> <span data-ttu-id="b962e-160">反向運動，路徑尋找）</span><span class="sxs-lookup"><span data-stu-id="b962e-160">inverse kinematics, path-finding)</span></span>

### <a name="gpu-performance-recommendations"></a><span data-ttu-id="b962e-161">GPU 效能建議</span><span class="sxs-lookup"><span data-stu-id="b962e-161">GPU performance recommendations</span></span>

#### <a name="understanding-bandwidth-vs-fill-rate"></a><span data-ttu-id="b962e-162">瞭解頻寬與填滿率</span><span class="sxs-lookup"><span data-stu-id="b962e-162">Understanding bandwidth vs. fill rate</span></span>
<span data-ttu-id="b962e-163">在 GPU 上轉譯框架時，應用程式通常會受到記憶體頻寬或填滿率的限制。</span><span class="sxs-lookup"><span data-stu-id="b962e-163">When rendering a frame on the GPU, an application is generally either bound by memory bandwidth or fill rate.</span></span>

- <span data-ttu-id="b962e-164">**記憶體頻寬**是 GPU 可以從記憶體執行的讀取和寫入速率</span><span class="sxs-lookup"><span data-stu-id="b962e-164">**Memory bandwidth** is the rate of reads and writes the GPU can perform from memory</span></span>
    - <span data-ttu-id="b962e-165">若要找出頻寬限制，請降低材質品質，並檢查幀的是否已改善。</span><span class="sxs-lookup"><span data-stu-id="b962e-165">To identify bandwidth limitations, reduce texture quality and check if the framerate has improved.</span></span>
    - <span data-ttu-id="b962e-166">在 Unity 中, 您可以在 [ **編輯**專案設定 >  > 品質] 設定 **[中變更](https://docs.unity3d.com/Manual/class-QualitySettings.html)材質品質**來完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="b962e-166">In Unity, this can be done by changing **Texture Quality** in **Edit** > **Project Settings** > **[Quality Settings](https://docs.unity3d.com/Manual/class-QualitySettings.html)**.</span></span>
- <span data-ttu-id="b962e-167">[**填滿速率**] 是指 GPU 每秒可繪製的圖元。</span><span class="sxs-lookup"><span data-stu-id="b962e-167">**Fill rate** refers to the pixels that can be drawn per second by the GPU.</span></span>
    - <span data-ttu-id="b962e-168">若要識別填滿率限制，請減少顯示器解析度，並檢查是否已改善畫面播放速率。</span><span class="sxs-lookup"><span data-stu-id="b962e-168">To identify fill rate limitations, decrease the display resolution and check if framerate improved.</span></span> 
    - <span data-ttu-id="b962e-169">在 Unity 中，這可以透過 *[XRSettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 屬性來完成。</span><span class="sxs-lookup"><span data-stu-id="b962e-169">In Unity, this can be done via the  *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* property</span></span>

<span data-ttu-id="b962e-170">記憶體頻寬通常牽涉到下列其中一項的優化：</span><span class="sxs-lookup"><span data-stu-id="b962e-170">Memory bandwidth generally involves optimizations to either:</span></span>
1) <span data-ttu-id="b962e-171">減少材質解析度</span><span class="sxs-lookup"><span data-stu-id="b962e-171">Decrease texture resolutions</span></span>
2) <span data-ttu-id="b962e-172">使用較少的材質（法線、反射等等）</span><span class="sxs-lookup"><span data-stu-id="b962e-172">Utilize fewer textures (normals, specular, etc.)</span></span>

<span data-ttu-id="b962e-173">[填滿速率] 著重于減少需要針對最終呈現圖元計算的作業數目。</span><span class="sxs-lookup"><span data-stu-id="b962e-173">Fill rate is focused on reducing the number of operations that need to be computed for a final rendered pixel.</span></span> <span data-ttu-id="b962e-174">這包括減少：</span><span class="sxs-lookup"><span data-stu-id="b962e-174">This includes reducing:</span></span>
1) <span data-ttu-id="b962e-175">要呈現/處理的物件數目</span><span class="sxs-lookup"><span data-stu-id="b962e-175">Number of objects to render/process</span></span>
2) <span data-ttu-id="b962e-176">每個著色器的作業數目</span><span class="sxs-lookup"><span data-stu-id="b962e-176">Number of operations per shader</span></span>
3) <span data-ttu-id="b962e-177">最後結果的 GPU 階段數（幾何著色器、後置處理效果等）</span><span class="sxs-lookup"><span data-stu-id="b962e-177">Number of GPU stages to final result (geometry shaders, post-processing effects, etc.)</span></span>
4) <span data-ttu-id="b962e-178">要呈現的圖元數（顯示解析度）</span><span class="sxs-lookup"><span data-stu-id="b962e-178">Number of pixels to render (display resolution)</span></span>

#### <a name="reduce-polygon-count"></a><span data-ttu-id="b962e-179">減少多邊形計數</span><span class="sxs-lookup"><span data-stu-id="b962e-179">Reduce polygon count</span></span>
<span data-ttu-id="b962e-180">較高的多邊形計數會產生更多 GPU 的作業;減少場景中的多邊形數目會減少轉譯時間。</span><span class="sxs-lookup"><span data-stu-id="b962e-180">Higher polygon counts result in more operations for the GPU; reducing the number of polygons in your scene will reduce the render time.</span></span> <span data-ttu-id="b962e-181">有一些其他因素會使幾何變得昂貴，但多邊形計數是最簡單的計量，用以判斷要呈現場景的成本。</span><span class="sxs-lookup"><span data-stu-id="b962e-181">There are other factors involved in shading the geometry that can be expensive, but polygon count is the simplest metric to determine how expensive a scene will be to render.</span></span>

#### <a name="limit-overdraw"></a><span data-ttu-id="b962e-182">限制過度繪製</span><span class="sxs-lookup"><span data-stu-id="b962e-182">Limit overdraw</span></span>

<span data-ttu-id="b962e-183">當有多個物件呈現，但因為 occluding 物件隱藏而未顯示在螢幕上時，就會發生高過度繪製。</span><span class="sxs-lookup"><span data-stu-id="b962e-183">High overdraw occurs when multiple objects are rendered but not shown on screen as they are hidden by an occluding object.</span></span> <span data-ttu-id="b962e-184">想像一下，看一下有物件背後的牆。</span><span class="sxs-lookup"><span data-stu-id="b962e-184">Imagine looking at a wall that has objects behind it.</span></span> <span data-ttu-id="b962e-185">所有的幾何都會處理以進行轉譯，但只需要轉譯不透明的牆。</span><span class="sxs-lookup"><span data-stu-id="b962e-185">All of the geometry would be processed for rendering, but only the opaque wall needs to be rendered.</span></span> <span data-ttu-id="b962e-186">這會導致不必要的作業。</span><span class="sxs-lookup"><span data-stu-id="b962e-186">This results in unnecessary operations.</span></span>

#### <a name="shaders"></a><span data-ttu-id="b962e-187">著色器</span><span class="sxs-lookup"><span data-stu-id="b962e-187">Shaders</span></span>

<span data-ttu-id="b962e-188">著色器是在 GPU 上執行的小型程式，會在轉譯時執行兩個重要步驟：</span><span class="sxs-lookup"><span data-stu-id="b962e-188">Shaders are small programs that run on the GPU and perform two important steps in rendering:</span></span>
1) <span data-ttu-id="b962e-189">判斷應該繪製哪些頂點，以及它們在螢幕空間中的位置（頂點著色器）</span><span class="sxs-lookup"><span data-stu-id="b962e-189">Determining which vertices should be drawn and where they are in screen space (the Vertex shader)</span></span>
    - <span data-ttu-id="b962e-190">頂點著色器通常會針對每個網格執行每個頂點。</span><span class="sxs-lookup"><span data-stu-id="b962e-190">The Vertex shader is generally executed per vertex for every mesh.</span></span>
2) <span data-ttu-id="b962e-191">判斷每個圖元的色彩（圖元著色器）</span><span class="sxs-lookup"><span data-stu-id="b962e-191">Determining the color of each pixel (the Pixel shader)</span></span>
    - <span data-ttu-id="b962e-192">圖元著色器會針對幾何轉譯成材質的每個圖元執行。</span><span class="sxs-lookup"><span data-stu-id="b962e-192">The Pixel shader is executed per pixel rendered by the geometry to the texture being rendered to.</span></span>

<span data-ttu-id="b962e-193">著色器通常會執行許多轉換和光源計算。</span><span class="sxs-lookup"><span data-stu-id="b962e-193">Typically, shaders perform many transformations and lighting calculations.</span></span> <span data-ttu-id="b962e-194">雖然複雜的光源模型、陰影和其他作業可以產生絕佳的結果，但也會提供價格。</span><span class="sxs-lookup"><span data-stu-id="b962e-194">Although complex lighting models, shadows, and other operations can generate fantastic results, they also come with a price.</span></span> <span data-ttu-id="b962e-195">減少著色器中計算的作業數目，可以大幅減少每個畫面格所需的 GPU 工作量。</span><span class="sxs-lookup"><span data-stu-id="b962e-195">Reducing the number of operations computed in shaders can greatly reduce the work needed for the GPU per frame.</span></span>

##### <a name="shader-coding-recommendations"></a><span data-ttu-id="b962e-196">著色器編碼建議</span><span class="sxs-lookup"><span data-stu-id="b962e-196">Shader coding recommendations</span></span>

- <span data-ttu-id="b962e-197">盡可能使用雙線性篩選</span><span class="sxs-lookup"><span data-stu-id="b962e-197">Use bilinear filtering, whenever possible</span></span>
- <span data-ttu-id="b962e-198">重新排列運算式以使用 MAD 內建函式，以便同時執行乘法和 add</span><span class="sxs-lookup"><span data-stu-id="b962e-198">Rearrange expressions to use MAD intrinsics in order to do a multiply and an add at the same time</span></span>
- <span data-ttu-id="b962e-199">在 CPU 上盡可能 Precalculate，並以常數的形式傳遞至材質</span><span class="sxs-lookup"><span data-stu-id="b962e-199">Precalculate as much as possible on the CPU and pass as constants to the material</span></span>
- <span data-ttu-id="b962e-200">**偏好將作業從圖元著色器移至頂點著色器**</span><span class="sxs-lookup"><span data-stu-id="b962e-200">**Favor moving operations from the pixel shader to the vertex shader**</span></span>
    - <span data-ttu-id="b962e-201">通常，頂點數目遠小於圖元數（720p 為921600圖元、1080p 為2073600圖元等等）。</span><span class="sxs-lookup"><span data-stu-id="b962e-201">Generally, the number of vertices is much smaller than the number of pixels (720p is 921,600 pixels, 1080p is 2,073,600 pixels, etc.)</span></span>

#### <a name="remove-gpu-stages"></a><span data-ttu-id="b962e-202">移除 GPU 階段</span><span class="sxs-lookup"><span data-stu-id="b962e-202">Remove GPU stages</span></span>
<span data-ttu-id="b962e-203">後續處理效果可能非常昂貴，而且會增加應用程式的填滿率。</span><span class="sxs-lookup"><span data-stu-id="b962e-203">Post-processing effects can be very expensive and increase the fill rate of your application.</span></span> <span data-ttu-id="b962e-204">這包括消除鋸齒的技術，例如 MSAA。</span><span class="sxs-lookup"><span data-stu-id="b962e-204">This includes anti-aliasing techniques such as MSAA.</span></span> <span data-ttu-id="b962e-205">在 HoloLens 上，建議您完全避免這些技術，以及額外的著色器階段，例如幾何、輪廓和計算著色器。</span><span class="sxs-lookup"><span data-stu-id="b962e-205">On HoloLens, it is recommended to avoid these techniques entirely, as well as additional shader stages such as geometry, hull, and compute shaders.</span></span>

## <a name="memory-recommendations"></a><span data-ttu-id="b962e-206">記憶體建議</span><span class="sxs-lookup"><span data-stu-id="b962e-206">Memory recommendations</span></span>
<span data-ttu-id="b962e-207">過多的記憶體配置和解除配置作業，可能會導致效能不一致、凍結的框架和其他不利的行為。</span><span class="sxs-lookup"><span data-stu-id="b962e-207">Excessive memory allocation and deallocation operations can result in inconsistent performance, frozen frames, and other detrimental behavior.</span></span> <span data-ttu-id="b962e-208">在 Unity 中開發時，請務必瞭解記憶體考慮，因為記憶體管理是由垃圾收集行程所控制。</span><span class="sxs-lookup"><span data-stu-id="b962e-208">It is especially important to understand memory considerations when developing in Unity, since memory management is controlled by the garbage collector.</span></span>

#### <a name="object-pooling"></a><span data-ttu-id="b962e-209">物件共用</span><span class="sxs-lookup"><span data-stu-id="b962e-209">Object pooling</span></span>

<span data-ttu-id="b962e-210">物件共用是降低連續配置和物件取消配置成本的常用技術。</span><span class="sxs-lookup"><span data-stu-id="b962e-210">Object pooling is a popular technique to reduce the cost of continuous allocations and deallocations of objects.</span></span> <span data-ttu-id="b962e-211">這是藉由配置相同物件的大型集區，並重複使用此集區中的非作用中、可用的實例來完成，而不是在一段時間內不斷產生和終結物件。</span><span class="sxs-lookup"><span data-stu-id="b962e-211">This is done by allocating a large pool of identical objects and re-using inactive, available instances from this pool instead of constantly spawning and destroying objects over time.</span></span> <span data-ttu-id="b962e-212">物件集區非常適合在應用程式期間有變數存留期的重複使用元件。</span><span class="sxs-lookup"><span data-stu-id="b962e-212">Object pools are great for re-useable components that have variable lifetime during an app.</span></span>

## <a name="see-also"></a><span data-ttu-id="b962e-213">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b962e-213">See also</span></span>
- [<span data-ttu-id="b962e-214">對 Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="b962e-214">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
- [<span data-ttu-id="b962e-215">Unity 的建議設定</span><span class="sxs-lookup"><span data-stu-id="b962e-215">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
