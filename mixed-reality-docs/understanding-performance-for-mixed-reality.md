---
title: 瞭解混合現實的效能
description: 優化 Windows Mixed Reality 應用程式效能的 Advanced 主題和詳細資料
author: Troy-Ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: Windows Mixed Reality, 混合現實, 虛擬實境, VR, MR, 效能, 優化, CPU, GPU
ms.openlocfilehash: ce59f9023c21dc7c981a2bb97d9fbd0c57622dbf
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548833"
---
# <a name="understanding-performance-for-mixed-reality"></a><span data-ttu-id="9d428-104">瞭解混合現實的效能</span><span class="sxs-lookup"><span data-stu-id="9d428-104">Understanding performance for mixed reality</span></span>

<span data-ttu-id="9d428-105">本文介紹合理化混合現實應用程式效能的重要性。</span><span class="sxs-lookup"><span data-stu-id="9d428-105">This article is an introduction into rationalizing the significance of performance for your Mixed Reality app.</span></span>  <span data-ttu-id="9d428-106">如果您的應用程式未以最佳畫面播放速率執行, 則使用者體驗可能會大幅降低。</span><span class="sxs-lookup"><span data-stu-id="9d428-106">User experience can be greatly degraded if your application does not run at optimal frame rate.</span></span> <span data-ttu-id="9d428-107">全像投影會出現不穩定的情況, 而且環境的頭追蹤會不正確, 導致使用者的體驗不佳。</span><span class="sxs-lookup"><span data-stu-id="9d428-107">Holograms will appear unstable and head tracking of the environment will be inaccurate leading to an poor experience for the user.</span></span> <span data-ttu-id="9d428-108">事實上, 必須將效能視為混合現實開發的第一類功能, 而不是穩定的迴圈結束工作。</span><span class="sxs-lookup"><span data-stu-id="9d428-108">Indeed, performance must be considered as a first class feature for Mixed Reality development and not a stabilization, end of cycle task.</span></span>

<span data-ttu-id="9d428-109">如需審查, 以下列出每個目標平臺的高效能的畫面播放速率值。</span><span class="sxs-lookup"><span data-stu-id="9d428-109">For review, the performant framerate values for each target platform are listed below.</span></span>

| <span data-ttu-id="9d428-110">平台</span><span class="sxs-lookup"><span data-stu-id="9d428-110">Platform</span></span> | <span data-ttu-id="9d428-111">目標畫面播放速率</span><span class="sxs-lookup"><span data-stu-id="9d428-111">Target Frame Rate</span></span> |
|----------|-------------------|
| [<span data-ttu-id="9d428-112">HoloLens</span><span class="sxs-lookup"><span data-stu-id="9d428-112">HoloLens</span></span>](hololens-hardware-details.md) | <span data-ttu-id="9d428-113">60 FPS</span><span class="sxs-lookup"><span data-stu-id="9d428-113">60 FPS</span></span> |
| [<span data-ttu-id="9d428-114">Windows Mixed Reality Ultra 電腦</span><span class="sxs-lookup"><span data-stu-id="9d428-114">Windows Mixed Reality Ultra PCs</span></span>](immersive-headset-hardware-details.md) | <span data-ttu-id="9d428-115">90 FPS</span><span class="sxs-lookup"><span data-stu-id="9d428-115">90 FPS</span></span> |
| [<span data-ttu-id="9d428-116">Windows Mixed Reality 電腦</span><span class="sxs-lookup"><span data-stu-id="9d428-116">Windows Mixed Reality PCs</span></span>](immersive-headset-hardware-details.md) | <span data-ttu-id="9d428-117">60 FPS</span><span class="sxs-lookup"><span data-stu-id="9d428-117">60 FPS</span></span> |

<span data-ttu-id="9d428-118">以下架構提供最佳做法的一般大綱, 以及達到目標畫面播放速率的稍微瞭解。</span><span class="sxs-lookup"><span data-stu-id="9d428-118">The framework below gives a general outline for best practices and understandings towards hitting target frame rates.</span></span> <span data-ttu-id="9d428-119">若要深入瞭解詳細資料, 請考慮閱讀[Unity 的效能建議一文](performance-recommendations-for-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="9d428-119">To dive further into details, consider reading the [performance recommendations for Unity article](performance-recommendations-for-unity.md).</span></span> <span data-ttu-id="9d428-120">特別是, 這篇相關文章將討論如何測量 Unity Windows Mixed Reality 應用程式中的幀速度, 以及在 Unity 環境中採取的步驟來改善效能。</span><span class="sxs-lookup"><span data-stu-id="9d428-120">In particular, this related article will discuss how to measure framerate in your Unity Windows Mixed Reality app as well as steps to take in the Unity environment to improve performance.</span></span>

## <a name="understanding-performance-bottlenecks"></a><span data-ttu-id="9d428-121">瞭解效能瓶頸</span><span class="sxs-lookup"><span data-stu-id="9d428-121">Understanding performance bottlenecks</span></span>

<span data-ttu-id="9d428-122">如果您的應用程式具有表現不佳的畫面播放速率, 第一個步驟是分析並瞭解您的應用程式需要大量計算的位置。</span><span class="sxs-lookup"><span data-stu-id="9d428-122">If your app has an underperforming framerate, the first step is to analyze and understand where your application is computationally intensive.</span></span> <span data-ttu-id="9d428-123">有兩個主要處理器負責呈現場景的工作: CPU 和 GPU。</span><span class="sxs-lookup"><span data-stu-id="9d428-123">There are two primary processors responsible for the work to render your scene: the CPU and the GPU.</span></span> <span data-ttu-id="9d428-124">這兩個元件都會處理混合現實應用程式的不同作業和階段。</span><span class="sxs-lookup"><span data-stu-id="9d428-124">Each of these two components handle different operations and stages of your Mixed Reality app.</span></span> <span data-ttu-id="9d428-125">有三個可能發生瓶頸的關鍵位置。</span><span class="sxs-lookup"><span data-stu-id="9d428-125">There are three key places where bottlenecks may occur.</span></span> 

1. <span data-ttu-id="9d428-126">**應用程式執行緒-CPU** -此執行緒負責您的應用程式邏輯。</span><span class="sxs-lookup"><span data-stu-id="9d428-126">**App Thread - CPU** - This thread is responsible for your app logic.</span></span> <span data-ttu-id="9d428-127">這包括處理輸入、動畫、物理和其他應用程式邏輯/狀態</span><span class="sxs-lookup"><span data-stu-id="9d428-127">This includes processing input, animations, physics, and other app logic/state</span></span>
2. <span data-ttu-id="9d428-128">**將執行緒 CPU 轉譯為 gpu** -此執行緒負責將您的繪製呼叫提交至 gpu。</span><span class="sxs-lookup"><span data-stu-id="9d428-128">**Render Thread - CPU to GPU** - This thread is responsible for submitting your draw calls to the GPU.</span></span> <span data-ttu-id="9d428-129">當您的應用程式想要轉譯物件 (例如 cube 或模型) 時, 此執行緒會將要求傳送至 GPU, 其具有針對轉譯而優化的架構, 以執行這些作業。</span><span class="sxs-lookup"><span data-stu-id="9d428-129">When your app wants to render an object such as a cube or model, this thread sends a request to the GPU, which has an architecture optimized for rendering, to perform these operations.</span></span>
3. <span data-ttu-id="9d428-130">**GPU**- 
   此處理器最常處理應用程式的圖形管線, 以將3d 資料 (模型、材質等等) 轉換成圖元, 最後產生2d 影像以提交至裝置的螢幕。</span><span class="sxs-lookup"><span data-stu-id="9d428-130">**GPU** - 
 This processor most commonly handles the graphics pipeline of your application to transform 3D data (models, textures, etc) into pixels and ultimately produce a 2D image to submit to your device's screen.</span></span>

![框架的存留期](images/lifetime-of-a-frame.png)

<span data-ttu-id="9d428-132">一般來說, HoloLens 應用程式會受到 GPU 限制。</span><span class="sxs-lookup"><span data-stu-id="9d428-132">Generally, HoloLens applications will be GPU bounded.</span></span> <span data-ttu-id="9d428-133">不過, 這並不會在每個應用程式中都成立, 因此建議使用以下的工具 & 技術, 為您的特定應用程式提供最真實的做法。</span><span class="sxs-lookup"><span data-stu-id="9d428-133">However, this does not hold true in every application and thus it is recommended to use the tools & techniques below to get to ground-truth for your particular app.</span></span>

## <a name="how-to-analyze-your-application"></a><span data-ttu-id="9d428-134">如何分析您的應用程式</span><span class="sxs-lookup"><span data-stu-id="9d428-134">How to analyze your application</span></span>

<span data-ttu-id="9d428-135">有許多工具可讓您身為開發人員, 以瞭解混合現實應用程式的效能設定檔。</span><span class="sxs-lookup"><span data-stu-id="9d428-135">There are many tools that allow you as a developer to understand the performance profile of your Mixed Reality application.</span></span> <span data-ttu-id="9d428-136">這些可讓您以具有瓶頸的目標, 以及它們本身股潮流以進行偵錯工具的方式來進行。</span><span class="sxs-lookup"><span data-stu-id="9d428-136">These will enable you to both target where you have bottlenecks and how they are manifesting themselves to debug them.</span></span>

<span data-ttu-id="9d428-137">這是熱門且功能強大的工具清單, 可取得應用程式的深入剖析資訊。</span><span class="sxs-lookup"><span data-stu-id="9d428-137">This is a list of popular and powerful tools to gain deep profiling information for your application.</span></span>
- [<span data-ttu-id="9d428-138">Intel 圖形效能分析器</span><span class="sxs-lookup"><span data-stu-id="9d428-138">Intel Graphics Performance Analyzers</span></span>](https://software.intel.com/gpa)
- [<span data-ttu-id="9d428-139">Visual Studio 圖形偵錯工具</span><span class="sxs-lookup"><span data-stu-id="9d428-139">Visual Studio Graphics Debuggers</span></span>](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [<span data-ttu-id="9d428-140">Unity Profiler</span><span class="sxs-lookup"><span data-stu-id="9d428-140">Unity Profiler</span></span>](https://docs.unity3d.com/Manual/Profiler.html)
- [<span data-ttu-id="9d428-141">Unity 框架偵錯工具</span><span class="sxs-lookup"><span data-stu-id="9d428-141">Unity Frame Debugger</span></span>](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a><span data-ttu-id="9d428-142">如何在任何環境中進行分析</span><span class="sxs-lookup"><span data-stu-id="9d428-142">How to profile in any environment</span></span>

<span data-ttu-id="9d428-143">有一個簡單的測試可以快速判斷您的應用程式中是否有可能的 GPU 界限或 CPU 限制。</span><span class="sxs-lookup"><span data-stu-id="9d428-143">There is a simple test to quickly determine if you are likely GPU bounded or CPU bounded in your application.</span></span> <span data-ttu-id="9d428-144">如果您降低轉譯目標輸出的解析度, 則會有較少的圖元來計算, 因此 GPU 需要執行以轉譯影像的工作量較少。</span><span class="sxs-lookup"><span data-stu-id="9d428-144">If you decrease the resolution of the render target output, there are less pixels to calculate and thus, less work the GPU needs to perform to render an image.</span></span> <span data-ttu-id="9d428-145">視口調整 (動態解析度調整) 是將影像轉譯成較小的轉譯目標, 然後您的輸出裝置可以顯示的做法。</span><span class="sxs-lookup"><span data-stu-id="9d428-145">Viewport scaling (dynamic resolution scaling) is the practice of rendering your image to a smaller render target then your output device can display.</span></span> <span data-ttu-id="9d428-146">裝置會從較小的圖元集合中取樣, 以顯示您的最終影像。</span><span class="sxs-lookup"><span data-stu-id="9d428-146">The device will up-sample from the smaller set of pixels to display your final image.</span></span>

<span data-ttu-id="9d428-147">在減少轉譯解析度之後, 如果:</span><span class="sxs-lookup"><span data-stu-id="9d428-147">After decreasing rendering resolution, if:</span></span>
1) <span data-ttu-id="9d428-148">應用程式的畫面播放速率**會增加**, 因此您可能會**限制 GPU**</span><span class="sxs-lookup"><span data-stu-id="9d428-148">Application framerate **increases**, then you are likely **GPU Bounded**</span></span>
1) <span data-ttu-id="9d428-149">應用程式的畫面播放速率**未**變更, 您可能會受到**CPU 限制**</span><span class="sxs-lookup"><span data-stu-id="9d428-149">Application framerate **unchanged**, then you are likely **CPU Bounded**</span></span>

>[!NOTE]
><span data-ttu-id="9d428-150">Unity 讓您能夠輕鬆地修改您的應用程式，透過在執行階段的轉譯目標解析度 *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 屬性。</span><span class="sxs-lookup"><span data-stu-id="9d428-150">Unity provides the ability to easily modify the render target resolution of your application at runtime through the *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* property.</span></span> <span data-ttu-id="9d428-151">裝置上顯示的最終映射具有固定的解析度。</span><span class="sxs-lookup"><span data-stu-id="9d428-151">The final image presented on device has a fixed resolution.</span></span> <span data-ttu-id="9d428-152">平臺會取樣較低的解析度輸出, 以建立更高解析度的影像, 以便在顯示器上呈現。</span><span class="sxs-lookup"><span data-stu-id="9d428-152">The platform will sample the lower resolution output to build a higher resolution image for rendering on displays.</span></span> 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a><span data-ttu-id="9d428-153">如何改善您的應用程式</span><span class="sxs-lookup"><span data-stu-id="9d428-153">How to improve your application</span></span>

### <a name="cpu-performance-recommendations"></a><span data-ttu-id="9d428-154">CPU 效能建議</span><span class="sxs-lookup"><span data-stu-id="9d428-154">CPU performance recommendations</span></span>

<span data-ttu-id="9d428-155">一般來說, CPU 上混合現實應用程式中的大部分工作都牽涉到執行場景的「模擬」, 並處理大量的獨特應用程式邏輯。</span><span class="sxs-lookup"><span data-stu-id="9d428-155">Generally, most work in a mixed reality application on the CPU involves performing the "simulation" of the scene and processing extensive unique application logic.</span></span> <span data-ttu-id="9d428-156">因此, 下欄區域通常會以優化為目標。</span><span class="sxs-lookup"><span data-stu-id="9d428-156">Thus, the following areas are usually targeted for optimization.</span></span>

- <span data-ttu-id="9d428-157">動畫</span><span class="sxs-lookup"><span data-stu-id="9d428-157">Animations</span></span>
- <span data-ttu-id="9d428-158">簡化物理</span><span class="sxs-lookup"><span data-stu-id="9d428-158">Simplify Physics</span></span>
- <span data-ttu-id="9d428-159">記憶體配置</span><span class="sxs-lookup"><span data-stu-id="9d428-159">Memory allocations</span></span>
- <span data-ttu-id="9d428-160">複雜演算法 (亦即</span><span class="sxs-lookup"><span data-stu-id="9d428-160">Complex algorithms (i.e</span></span> <span data-ttu-id="9d428-161">反向運動, 路徑尋找)</span><span class="sxs-lookup"><span data-stu-id="9d428-161">inverse kinematics, path-finding)</span></span>

### <a name="gpu-performance-recommendations"></a><span data-ttu-id="9d428-162">GPU 效能建議</span><span class="sxs-lookup"><span data-stu-id="9d428-162">GPU performance recommendations</span></span>

#### <a name="understanding-bandwidth-vs-fill-rate"></a><span data-ttu-id="9d428-163">瞭解頻寬與填滿率</span><span class="sxs-lookup"><span data-stu-id="9d428-163">Understanding bandwidth vs fill rate</span></span>
<span data-ttu-id="9d428-164">在 GPU 上轉譯框架時, 應用程式通常會受到記憶體頻寬或填滿率的限制。</span><span class="sxs-lookup"><span data-stu-id="9d428-164">When rendering a frame on the GPU, an application is generally either bounded by memory bandwidth or fill rate.</span></span>

- <span data-ttu-id="9d428-165">**記憶體頻寬**是 GPU 可以從記憶體執行的讀取和寫入速率</span><span class="sxs-lookup"><span data-stu-id="9d428-165">**Memory bandwidth** is the rate of reads and writes the GPU can perform from memory</span></span>
    - <span data-ttu-id="9d428-166">若要找出頻寬限制, 請降低材質品質, 並檢查是否已改善畫面播放速率。</span><span class="sxs-lookup"><span data-stu-id="9d428-166">To identify bandwidth limitations, reduce texture quality and check if framerate improved.</span></span>
    - <span data-ttu-id="9d428-167">在 Unity 中, 您可以在 [ **編輯** > **專案設定** >  \*\*[品質] 設定](https://docs.unity3d.com/Manual/class-QualitySettings.html)\*\* 中變更**材質品質**來完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="9d428-167">In Unity, this can be done by changing **Texture Quality** in **Edit** > **Project Settings** > **[Quality Settings](https://docs.unity3d.com/Manual/class-QualitySettings.html)**.</span></span>
- <span data-ttu-id="9d428-168">[**填滿速率**] 是指 GPU 每秒可繪製的轉譯圖元輸送量。</span><span class="sxs-lookup"><span data-stu-id="9d428-168">**Fill rate** refers to the throughput of rendered pixels that can be drawn per second by the GPU.</span></span>
    - <span data-ttu-id="9d428-169">若要識別填滿率限制, 請減少顯示器解析度, 並檢查是否已改善畫面播放速率。</span><span class="sxs-lookup"><span data-stu-id="9d428-169">To identify fill rate limitations, decrease the display resolution and check if framerate improved.</span></span> 
    - <span data-ttu-id="9d428-170">在 Unity 中，這可以透過 *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 屬性</span><span class="sxs-lookup"><span data-stu-id="9d428-170">In Unity, this can be done via the  *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* property</span></span>

<span data-ttu-id="9d428-171">記憶體頻寬通常牽涉到下列其中一項的優化</span><span class="sxs-lookup"><span data-stu-id="9d428-171">Memory bandwidth generally involves optimizations to either</span></span>
1) <span data-ttu-id="9d428-172">減少材質解析度</span><span class="sxs-lookup"><span data-stu-id="9d428-172">decrease texture resolutions</span></span>
2) <span data-ttu-id="9d428-173">利用較少的紋理 (也就是</span><span class="sxs-lookup"><span data-stu-id="9d428-173">utilize less textures (i.e</span></span> <span data-ttu-id="9d428-174">法線、反射等等)</span><span class="sxs-lookup"><span data-stu-id="9d428-174">normals, specular, etc)</span></span>

<span data-ttu-id="9d428-175">[填滿速率] 主要著重于減少需要針對最終呈現圖元計算的作業數目。</span><span class="sxs-lookup"><span data-stu-id="9d428-175">Fill rate is primarily focused on reducing the number of operations that need to be computed for a final rendered pixel.</span></span> <span data-ttu-id="9d428-176">這種情況的範例通常會減少</span><span class="sxs-lookup"><span data-stu-id="9d428-176">Examples of this commonly fall into reducing</span></span>
1) <span data-ttu-id="9d428-177">要呈現/處理的物件數目</span><span class="sxs-lookup"><span data-stu-id="9d428-177">number of objects to render/process</span></span>
2) <span data-ttu-id="9d428-178">每個著色器的作業數目</span><span class="sxs-lookup"><span data-stu-id="9d428-178">number of operations per shader</span></span>
3) <span data-ttu-id="9d428-179">最後結果的 GPU 階段數 (幾何著色器、後置處理效果等)</span><span class="sxs-lookup"><span data-stu-id="9d428-179">number of GPU stages to final result (geometry shaders, post-processing effects, etc)</span></span>
4) <span data-ttu-id="9d428-180">要呈現的圖元數 (亦即</span><span class="sxs-lookup"><span data-stu-id="9d428-180">number of pixels to render (i.e</span></span> <span data-ttu-id="9d428-181">顯示器解析度)</span><span class="sxs-lookup"><span data-stu-id="9d428-181">display resolution)</span></span>

#### <a name="reduce-poly-count"></a><span data-ttu-id="9d428-182">減少 poly 計數</span><span class="sxs-lookup"><span data-stu-id="9d428-182">Reduce poly count</span></span>
<span data-ttu-id="9d428-183">較高的多邊形計數會導致 GPU 的更多作業, 並減少場景中的多邊形數目, 以減少呈現該幾何的時間量。</span><span class="sxs-lookup"><span data-stu-id="9d428-183">Higher polygon counts result in more operations for the GPU and reducing the number of polygons in your scene will reduce the amount of time to render that geometry.</span></span> <span data-ttu-id="9d428-184">還有其他因素會加上陰影, 但可能仍然很昂貴, 但多邊形計數是基底計量, 用來判斷要呈現場景的代價。</span><span class="sxs-lookup"><span data-stu-id="9d428-184">There are other factors involved as well in shading the geometry that can still be expensive but polygon count is the base metric to determine how expensive a scene will be to render.</span></span>

#### <a name="limit-overdraw"></a><span data-ttu-id="9d428-185">限制過度繪製</span><span class="sxs-lookup"><span data-stu-id="9d428-185">Limit overdraw</span></span>

<span data-ttu-id="9d428-186">當轉譯多個物件但未輸出到螢幕上, 但另一個通常較近的 occluding 物件隱藏時, 就會發生高過度繪製。</span><span class="sxs-lookup"><span data-stu-id="9d428-186">High overdraw occurs when multiple objects are rendered but not outputted to the screen as they are hidden by another, generally closer, occluding object.</span></span> <span data-ttu-id="9d428-187">想像一下有多個房間和幾何背後的牆。</span><span class="sxs-lookup"><span data-stu-id="9d428-187">Imagine looking at a wall that had multiple rooms and geometry behind it.</span></span> <span data-ttu-id="9d428-188">所有的幾何都會處理以進行轉譯, 但只有不透明的牆在 occludes 所有其他內容的觀點時, 才需要轉譯。</span><span class="sxs-lookup"><span data-stu-id="9d428-188">All of the geometry would be processed for rendering but only the opaque wall really needs to be rendered as it occludes the view of all other content.</span></span> <span data-ttu-id="9d428-189">這會導致目前的觀點不需要浪費作業。</span><span class="sxs-lookup"><span data-stu-id="9d428-189">This results in wasteful operations that are not needed for the current view.</span></span>

#### <a name="shaders"></a><span data-ttu-id="9d428-190">著色器</span><span class="sxs-lookup"><span data-stu-id="9d428-190">Shaders</span></span>

<span data-ttu-id="9d428-191">著色器是在 GPU 上執行的小型程式, 通常會判斷轉譯中的兩個重要步驟:</span><span class="sxs-lookup"><span data-stu-id="9d428-191">Shaders are small programs that run on the GPU and generally determine two important steps in rendering:</span></span>
1) <span data-ttu-id="9d428-192">哪一個物件的頂點應該繪製在畫面上, 以及它們在螢幕空間中的位置 (亦即</span><span class="sxs-lookup"><span data-stu-id="9d428-192">which object's vertices should be drawn on the screen and where they are in screen space (i.e</span></span> <span data-ttu-id="9d428-193">頂點著色器)</span><span class="sxs-lookup"><span data-stu-id="9d428-193">the Vertex shader)</span></span>
    - <span data-ttu-id="9d428-194">端點著色器通常會針對每個 GameObject 的每個頂點執行</span><span class="sxs-lookup"><span data-stu-id="9d428-194">The Vertex shader is generally executed per vertex for every GameObject</span></span>
2) <span data-ttu-id="9d428-195">這些圖元的色彩 (亦即</span><span class="sxs-lookup"><span data-stu-id="9d428-195">what to color those pixels (i.e</span></span> <span data-ttu-id="9d428-196">圖元著色器)</span><span class="sxs-lookup"><span data-stu-id="9d428-196">the Pixel shader)</span></span>
    - <span data-ttu-id="9d428-197">圖元著色器會針對呈現的裝置材質, 每圖元執行一次</span><span class="sxs-lookup"><span data-stu-id="9d428-197">The Pixel shader is executed per pixel for the texture being rendered for device present</span></span>

<span data-ttu-id="9d428-198">著色器通常會執行許多轉換和光源計算。</span><span class="sxs-lookup"><span data-stu-id="9d428-198">Typically shaders perform many transformations and lighting calculations.</span></span> <span data-ttu-id="9d428-199">雖然複雜的光源模型、陰影和其他作業可以產生絕佳的結果, 但也會提供價格。</span><span class="sxs-lookup"><span data-stu-id="9d428-199">Although complex lighting models, shadows, and other operations can generate fantastic results, they also come with a price.</span></span> <span data-ttu-id="9d428-200">減少在著色器中計算的作業數目, 可以大幅減少每個畫面的 GPU 所需的整體工作。</span><span class="sxs-lookup"><span data-stu-id="9d428-200">Reducing the number of operations computed in shaders can greatly reduce the overall work needed to be done by a GPU per frame.</span></span>

##### <a name="shader-coding-recommendations"></a><span data-ttu-id="9d428-201">著色器編碼建議</span><span class="sxs-lookup"><span data-stu-id="9d428-201">Shader coding recommendations</span></span>

- <span data-ttu-id="9d428-202">盡可能使用雙線性篩選</span><span class="sxs-lookup"><span data-stu-id="9d428-202">Use bilinear filtering whenever possible</span></span>
- <span data-ttu-id="9d428-203">重新排列運算式以使用 MAD 內建函式, 以便同時執行乘法和 add</span><span class="sxs-lookup"><span data-stu-id="9d428-203">Rearrange expressions to use MAD intrinsics in order to do a multiply and an add at the same time</span></span>
- <span data-ttu-id="9d428-204">在 CPU 上盡可能 Precalculate, 並以常數的形式傳遞至材質</span><span class="sxs-lookup"><span data-stu-id="9d428-204">Precalculate as much as possible on the CPU and pass as constants to the material</span></span>
- <span data-ttu-id="9d428-205">**偏好將作業從圖元著色器移至頂點著色器**</span><span class="sxs-lookup"><span data-stu-id="9d428-205">**Favor moving operations from the pixel shader to the vertex shader**</span></span>
    - <span data-ttu-id="9d428-206">一般來說, 頂點的 # < < 的圖元數 (亦即</span><span class="sxs-lookup"><span data-stu-id="9d428-206">Generally the # of vertices << # of pixels (i.e</span></span> <span data-ttu-id="9d428-207">720p = = 921600 圖元、1080p = = 2073600 圖元等等)</span><span class="sxs-lookup"><span data-stu-id="9d428-207">720p == 921,600 pixels, 1080p == 2,073,600 pixels, etc)</span></span>

#### <a name="remove-gpu-stages"></a><span data-ttu-id="9d428-208">移除 GPU 階段</span><span class="sxs-lookup"><span data-stu-id="9d428-208">Remove GPU stages</span></span>
<span data-ttu-id="9d428-209">後續處理效果可能非常昂貴, 而且通常會抑制應用程式的填滿率。</span><span class="sxs-lookup"><span data-stu-id="9d428-209">Post-processing effects can be very expensive and generally inhibit the fill rate of your application.</span></span> <span data-ttu-id="9d428-210">這也包含消除鋸齒的技術, 例如 MSAA。</span><span class="sxs-lookup"><span data-stu-id="9d428-210">This also includes anti-aliasing techniques such as MSAA.</span></span> <span data-ttu-id="9d428-211">在 HoloLens 上, 建議您完全避免這些技術。</span><span class="sxs-lookup"><span data-stu-id="9d428-211">On HoloLens, it is recommended to avoid these techniques entirely.</span></span> <span data-ttu-id="9d428-212">此外, 您應該盡可能避免其他的著色器階段, 例如幾何、輪廓和計算著色器。</span><span class="sxs-lookup"><span data-stu-id="9d428-212">Furthermore, additional shader stages such as geometry, hull, and compute shaders should be avoided when possible.</span></span>

## <a name="memory-recommendations"></a><span data-ttu-id="9d428-213">記憶體建議</span><span class="sxs-lookup"><span data-stu-id="9d428-213">Memory recommendations</span></span>
<span data-ttu-id="9d428-214">記憶體配置過多 & 解除配置作業可能會對您的全像攝影應用程式造成不良的影響, 因而導致效能不一致、凍結的框架和其他有害行為。</span><span class="sxs-lookup"><span data-stu-id="9d428-214">Excessive memory allocation & deallocation operations can have adverse effects on your holographic application resulting in inconsistent performance, frozen frames, and other detrimental behavior.</span></span> <span data-ttu-id="9d428-215">在 Unity 中開發時, 請務必瞭解記憶體考慮, 因為記憶體管理是由垃圾收集行程所控制。</span><span class="sxs-lookup"><span data-stu-id="9d428-215">It is especially important to understand memory considerations when developing in Unity since memory management is controlled by the garbage collector.</span></span>

#### <a name="object-pooling"></a><span data-ttu-id="9d428-216">物件共用</span><span class="sxs-lookup"><span data-stu-id="9d428-216">Object pooling</span></span>

<span data-ttu-id="9d428-217">物件共用是一種常用的技術, 可降低連續配置 & 取消設定物件的成本。</span><span class="sxs-lookup"><span data-stu-id="9d428-217">Object pooling is a popular technique to reduce the cost of continuous allocations & deallocations of objects.</span></span> <span data-ttu-id="9d428-218">這是藉由配置相同物件的大型集區, 並重複使用此集區中的非作用中、可用的實例來完成, 而不是在一段時間內不斷產生和終結物件。</span><span class="sxs-lookup"><span data-stu-id="9d428-218">This is done by allocating a large pool of identical objects and re-using inactive, available instances from this pool instead of constantly spawning and destroying objects over time.</span></span> <span data-ttu-id="9d428-219">物件集區非常適合在應用程式期間有變數存留期的重複使用元件。</span><span class="sxs-lookup"><span data-stu-id="9d428-219">Object pools are great for re-useable components that have variable lifetime during an app.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d428-220">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d428-220">See also</span></span>
- [<span data-ttu-id="9d428-221">對 Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="9d428-221">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
- [<span data-ttu-id="9d428-222">Unity 的建議設定</span><span class="sxs-lookup"><span data-stu-id="9d428-222">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
