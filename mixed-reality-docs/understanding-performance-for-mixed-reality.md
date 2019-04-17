---
title: 了解效能 for Mixed Reality
description: 上的 Windows Mixed Reality 應用程式效能最佳化的進階主題和詳細資料
author: Troy-Ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: 混合實境、 混合的實境，虛擬實境、 VR、 MR、 效能、 最佳化、 CPU、 GPU 的 Windows
ms.openlocfilehash: ce59f9023c21dc7c981a2bb97d9fbd0c57622dbf
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596074"
---
# <a name="understanding-performance-for-mixed-reality"></a><span data-ttu-id="7107c-104">混合實境的了解效能</span><span class="sxs-lookup"><span data-stu-id="7107c-104">Understanding performance for mixed reality</span></span>

<span data-ttu-id="7107c-105">這篇文章會介紹了合理化 Mixed Reality 應用程式效能的重要性。</span><span class="sxs-lookup"><span data-stu-id="7107c-105">This article is an introduction into rationalizing the significance of performance for your Mixed Reality app.</span></span>  <span data-ttu-id="7107c-106">如果不會執行您的應用程式，這是在最佳的畫面播放速率，就可以大幅降低使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="7107c-106">User experience can be greatly degraded if your application does not run at optimal frame rate.</span></span> <span data-ttu-id="7107c-107">全像投影會出現不穩定，因此前端追蹤環境的不正確導致體驗不佳的使用者。</span><span class="sxs-lookup"><span data-stu-id="7107c-107">Holograms will appear unstable and head tracking of the environment will be inaccurate leading to an poor experience for the user.</span></span> <span data-ttu-id="7107c-108">事實上，效能必須視為 for Mixed Reality 開發與穩定、 週期工作的最後不使用的第一個類別功能。</span><span class="sxs-lookup"><span data-stu-id="7107c-108">Indeed, performance must be considered as a first class feature for Mixed Reality development and not a stabilization, end of cycle task.</span></span>

<span data-ttu-id="7107c-109">供檢閱，如下所列每個目標平台的高效能的畫面播放速率值。</span><span class="sxs-lookup"><span data-stu-id="7107c-109">For review, the performant framerate values for each target platform are listed below.</span></span>

| <span data-ttu-id="7107c-110">平台</span><span class="sxs-lookup"><span data-stu-id="7107c-110">Platform</span></span> | <span data-ttu-id="7107c-111">目標畫面播放速率</span><span class="sxs-lookup"><span data-stu-id="7107c-111">Target Frame Rate</span></span> |
|----------|-------------------|
| [<span data-ttu-id="7107c-112">HoloLens</span><span class="sxs-lookup"><span data-stu-id="7107c-112">HoloLens</span></span>](hololens-hardware-details.md) | <span data-ttu-id="7107c-113">60 FPS</span><span class="sxs-lookup"><span data-stu-id="7107c-113">60 FPS</span></span> |
| [<span data-ttu-id="7107c-114">電腦的 Windows Mixed Reality Ultra</span><span class="sxs-lookup"><span data-stu-id="7107c-114">Windows Mixed Reality Ultra PCs</span></span>](immersive-headset-hardware-details.md) | <span data-ttu-id="7107c-115">90 的 FPS</span><span class="sxs-lookup"><span data-stu-id="7107c-115">90 FPS</span></span> |
| [<span data-ttu-id="7107c-116">混合實境電腦的 Windows</span><span class="sxs-lookup"><span data-stu-id="7107c-116">Windows Mixed Reality PCs</span></span>](immersive-headset-hardware-details.md) | <span data-ttu-id="7107c-117">60 FPS</span><span class="sxs-lookup"><span data-stu-id="7107c-117">60 FPS</span></span> |

<span data-ttu-id="7107c-118">下列架構提供一般的外框的最佳作法，並了解內容，來達到目標畫面播放速率。</span><span class="sxs-lookup"><span data-stu-id="7107c-118">The framework below gives a general outline for best practices and understandings towards hitting target frame rates.</span></span> <span data-ttu-id="7107c-119">若要深入了解進一步詳細資料，請閱讀[Unity 文件的效能建議](performance-recommendations-for-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="7107c-119">To dive further into details, consider reading the [performance recommendations for Unity article](performance-recommendations-for-unity.md).</span></span> <span data-ttu-id="7107c-120">特別是，此相關的文章將討論如何測量您的 Unity Windows Mixed Reality 應用程式以及在 Unity 環境中採取以改善效能的步驟中的畫面播放速率。</span><span class="sxs-lookup"><span data-stu-id="7107c-120">In particular, this related article will discuss how to measure framerate in your Unity Windows Mixed Reality app as well as steps to take in the Unity environment to improve performance.</span></span>

## <a name="understanding-performance-bottlenecks"></a><span data-ttu-id="7107c-121">了解效能瓶頸</span><span class="sxs-lookup"><span data-stu-id="7107c-121">Understanding performance bottlenecks</span></span>

<span data-ttu-id="7107c-122">如果您的應用程式有績效不佳的畫面播放速率，第一個步驟是分析，並了解您的應用程式的大量運算資源的位置。</span><span class="sxs-lookup"><span data-stu-id="7107c-122">If your app has an underperforming framerate, the first step is to analyze and understand where your application is computationally intensive.</span></span> <span data-ttu-id="7107c-123">有兩個主要的處理器負責轉譯場景的工作： 在 CPU 和 GPU。</span><span class="sxs-lookup"><span data-stu-id="7107c-123">There are two primary processors responsible for the work to render your scene: the CPU and the GPU.</span></span> <span data-ttu-id="7107c-124">這兩個元件的每個處理不同的作業與混合實境應用程式的階段。</span><span class="sxs-lookup"><span data-stu-id="7107c-124">Each of these two components handle different operations and stages of your Mixed Reality app.</span></span> <span data-ttu-id="7107c-125">有三個索引鍵的地方，可能會發生瓶頸。</span><span class="sxs-lookup"><span data-stu-id="7107c-125">There are three key places where bottlenecks may occur.</span></span> 

1. <span data-ttu-id="7107c-126">**應用程式執行緒-CPU** -此執行緒會負責您的應用程式邏輯。</span><span class="sxs-lookup"><span data-stu-id="7107c-126">**App Thread - CPU** - This thread is responsible for your app logic.</span></span> <span data-ttu-id="7107c-127">這包括處理輸入、 動畫、 物理條件，以及其他應用程式的邏輯/狀態</span><span class="sxs-lookup"><span data-stu-id="7107c-127">This includes processing input, animations, physics, and other app logic/state</span></span>
2. <span data-ttu-id="7107c-128">**轉譯執行緒-CPU GPU** -這個執行緒負責提交您的繪製呼叫，以 GPU。</span><span class="sxs-lookup"><span data-stu-id="7107c-128">**Render Thread - CPU to GPU** - This thread is responsible for submitting your draw calls to the GPU.</span></span> <span data-ttu-id="7107c-129">當您的應用程式想要轉譯的物件，例如 cube 或模型時，此執行緒就會傳送要求給 GPU，具有適用於轉譯的架構，以執行這些作業。</span><span class="sxs-lookup"><span data-stu-id="7107c-129">When your app wants to render an object such as a cube or model, this thread sends a request to the GPU, which has an architecture optimized for rendering, to perform these operations.</span></span>
3. <span data-ttu-id="7107c-130">**GPU** - 
   此處理器通常會處理您的應用程式 （模型、 紋理等等） 的 3D 資料轉換為像素為單位，而且最後產生 2D 的映像，以提交至您的裝置 畫面的圖形管線。</span><span class="sxs-lookup"><span data-stu-id="7107c-130">**GPU** - 
 This processor most commonly handles the graphics pipeline of your application to transform 3D data (models, textures, etc) into pixels and ultimately produce a 2D image to submit to your device's screen.</span></span>

![畫面格的存留期](images/lifetime-of-a-frame.png)

<span data-ttu-id="7107c-132">一般而言，HoloLens 的應用程式將會繫結的 GPU。</span><span class="sxs-lookup"><span data-stu-id="7107c-132">Generally, HoloLens applications will be GPU bounded.</span></span> <span data-ttu-id="7107c-133">不過，這不會保留每個應用程式中，則為 true，因此建議使用的工具及技術下, 面以前往特定應用程式的地真。</span><span class="sxs-lookup"><span data-stu-id="7107c-133">However, this does not hold true in every application and thus it is recommended to use the tools & techniques below to get to ground-truth for your particular app.</span></span>

## <a name="how-to-analyze-your-application"></a><span data-ttu-id="7107c-134">如何分析您的應用程式</span><span class="sxs-lookup"><span data-stu-id="7107c-134">How to analyze your application</span></span>

<span data-ttu-id="7107c-135">有許多工具可讓您身為開發人員若要了解您的混合實境應用程式的效能設定檔。</span><span class="sxs-lookup"><span data-stu-id="7107c-135">There are many tools that allow you as a developer to understand the performance profile of your Mixed Reality application.</span></span> <span data-ttu-id="7107c-136">這些可讓您以這兩個您可在此有瓶頸，以及如何它們 manifesting 本身進行偵錯的目標。</span><span class="sxs-lookup"><span data-stu-id="7107c-136">These will enable you to both target where you have bottlenecks and how they are manifesting themselves to debug them.</span></span>

<span data-ttu-id="7107c-137">這是常用且功能強大的工具，來取得深入分析您的應用程式資訊清單。</span><span class="sxs-lookup"><span data-stu-id="7107c-137">This is a list of popular and powerful tools to gain deep profiling information for your application.</span></span>
- [<span data-ttu-id="7107c-138">Intel 圖形效能分析器</span><span class="sxs-lookup"><span data-stu-id="7107c-138">Intel Graphics Performance Analyzers</span></span>](https://software.intel.com/gpa)
- [<span data-ttu-id="7107c-139">Visual Studio 圖形偵錯工具</span><span class="sxs-lookup"><span data-stu-id="7107c-139">Visual Studio Graphics Debuggers</span></span>](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [<span data-ttu-id="7107c-140">Unity Profiler</span><span class="sxs-lookup"><span data-stu-id="7107c-140">Unity Profiler</span></span>](https://docs.unity3d.com/Manual/Profiler.html)
- [<span data-ttu-id="7107c-141">Unity 框架偵錯工具</span><span class="sxs-lookup"><span data-stu-id="7107c-141">Unity Frame Debugger</span></span>](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a><span data-ttu-id="7107c-142">如何在任何環境中的設定檔</span><span class="sxs-lookup"><span data-stu-id="7107c-142">How to profile in any environment</span></span>

<span data-ttu-id="7107c-143">沒有簡單的測試，來快速判斷 是否可能，繫結 GPU 或 CPU 繫結應用程式中。</span><span class="sxs-lookup"><span data-stu-id="7107c-143">There is a simple test to quickly determine if you are likely GPU bounded or CPU bounded in your application.</span></span> <span data-ttu-id="7107c-144">如果您降低解析度轉譯目標輸出時，有較少的像素為單位來計算，因此，較少工作 GPU 必須執行才能呈現的影像。</span><span class="sxs-lookup"><span data-stu-id="7107c-144">If you decrease the resolution of the render target output, there are less pixels to calculate and thus, less work the GPU needs to perform to render an image.</span></span> <span data-ttu-id="7107c-145">檢視區縮放比例 （動態解析調整） 是呈現您的映像，以較小的做法呈現目標輸出裝置可以顯示。</span><span class="sxs-lookup"><span data-stu-id="7107c-145">Viewport scaling (dynamic resolution scaling) is the practice of rendering your image to a smaller render target then your output device can display.</span></span> <span data-ttu-id="7107c-146">裝置會增加取樣從一組較小的像素為單位來顯示最終的映像。</span><span class="sxs-lookup"><span data-stu-id="7107c-146">The device will up-sample from the smaller set of pixels to display your final image.</span></span>

<span data-ttu-id="7107c-147">之後如果，請減少轉譯解析：</span><span class="sxs-lookup"><span data-stu-id="7107c-147">After decreasing rendering resolution, if:</span></span>
1) <span data-ttu-id="7107c-148">應用程式畫面播放速率**增加**，您可能會**GPU 繫結**</span><span class="sxs-lookup"><span data-stu-id="7107c-148">Application framerate **increases**, then you are likely **GPU Bounded**</span></span>
1) <span data-ttu-id="7107c-149">應用程式畫面播放速率**變**，您可能會**CPU 繫結**</span><span class="sxs-lookup"><span data-stu-id="7107c-149">Application framerate **unchanged**, then you are likely **CPU Bounded**</span></span>

>[!NOTE]
><span data-ttu-id="7107c-150">Unity 讓您能夠輕鬆地修改您的應用程式，透過在執行階段的轉譯目標解析度*[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 屬性。</span><span class="sxs-lookup"><span data-stu-id="7107c-150">Unity provides the ability to easily modify the render target resolution of your application at runtime through the *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* property.</span></span> <span data-ttu-id="7107c-151">在裝置上所呈現的最終映像有固定的解析度。</span><span class="sxs-lookup"><span data-stu-id="7107c-151">The final image presented on device has a fixed resolution.</span></span> <span data-ttu-id="7107c-152">平台將範例建置在顯示器上呈現較高解析度影像輸出較低的解析度。</span><span class="sxs-lookup"><span data-stu-id="7107c-152">The platform will sample the lower resolution output to build a higher resolution image for rendering on displays.</span></span> 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a><span data-ttu-id="7107c-153">如何改善您的應用程式</span><span class="sxs-lookup"><span data-stu-id="7107c-153">How to improve your application</span></span>

### <a name="cpu-performance-recommendations"></a><span data-ttu-id="7107c-154">CPU 效能建議</span><span class="sxs-lookup"><span data-stu-id="7107c-154">CPU performance recommendations</span></span>

<span data-ttu-id="7107c-155">一般而言，在 CPU 上的混合的實境應用程式中的大部分工作牽涉到執行 「 模擬 」 的場景及處理大量的唯一應用程式邏輯。</span><span class="sxs-lookup"><span data-stu-id="7107c-155">Generally, most work in a mixed reality application on the CPU involves performing the "simulation" of the scene and processing extensive unique application logic.</span></span> <span data-ttu-id="7107c-156">因此，下列區域通常為目標進行最佳化。</span><span class="sxs-lookup"><span data-stu-id="7107c-156">Thus, the following areas are usually targeted for optimization.</span></span>

- <span data-ttu-id="7107c-157">動畫</span><span class="sxs-lookup"><span data-stu-id="7107c-157">Animations</span></span>
- <span data-ttu-id="7107c-158">簡化物理</span><span class="sxs-lookup"><span data-stu-id="7107c-158">Simplify Physics</span></span>
- <span data-ttu-id="7107c-159">記憶體配置</span><span class="sxs-lookup"><span data-stu-id="7107c-159">Memory allocations</span></span>
- <span data-ttu-id="7107c-160">複雜的演算法 （也就是</span><span class="sxs-lookup"><span data-stu-id="7107c-160">Complex algorithms (i.e</span></span> <span data-ttu-id="7107c-161">反向運動、 路徑尋找）</span><span class="sxs-lookup"><span data-stu-id="7107c-161">inverse kinematics, path-finding)</span></span>

### <a name="gpu-performance-recommendations"></a><span data-ttu-id="7107c-162">GPU 效能建議</span><span class="sxs-lookup"><span data-stu-id="7107c-162">GPU performance recommendations</span></span>

#### <a name="understanding-bandwidth-vs-fill-rate"></a><span data-ttu-id="7107c-163">了解頻寬 vs 填滿率</span><span class="sxs-lookup"><span data-stu-id="7107c-163">Understanding bandwidth vs fill rate</span></span>
<span data-ttu-id="7107c-164">轉譯 GPU 上的框架，應用程式時，通常是受限於記憶體頻寬或填滿率。</span><span class="sxs-lookup"><span data-stu-id="7107c-164">When rendering a frame on the GPU, an application is generally either bounded by memory bandwidth or fill rate.</span></span>

- <span data-ttu-id="7107c-165">**記憶體頻寬**是讀取的速率，並將寫入 GPU 可以從記憶體執行</span><span class="sxs-lookup"><span data-stu-id="7107c-165">**Memory bandwidth** is the rate of reads and writes the GPU can perform from memory</span></span>
    - <span data-ttu-id="7107c-166">若要識別頻寬限制，減少紋理的品質，並檢查畫面播放速率獲得改善。</span><span class="sxs-lookup"><span data-stu-id="7107c-166">To identify bandwidth limitations, reduce texture quality and check if framerate improved.</span></span>
    - <span data-ttu-id="7107c-167">在 Unity 中，做法是藉由變更**材質品質**中**編輯** > **專案設定** >   **[品質設定](https://docs.unity3d.com/Manual/class-QualitySettings.html)**。</span><span class="sxs-lookup"><span data-stu-id="7107c-167">In Unity, this can be done by changing **Texture Quality** in **Edit** > **Project Settings** > **[Quality Settings](https://docs.unity3d.com/Manual/class-QualitySettings.html)**.</span></span>
- <span data-ttu-id="7107c-168">**填滿率**指的是轉譯要在 gpu 每秒繪製的像素的輸送量。</span><span class="sxs-lookup"><span data-stu-id="7107c-168">**Fill rate** refers to the throughput of rendered pixels that can be drawn per second by the GPU.</span></span>
    - <span data-ttu-id="7107c-169">若要識別填滿速率限制，降低顯示器解析度，並檢查畫面播放速率獲得改善。</span><span class="sxs-lookup"><span data-stu-id="7107c-169">To identify fill rate limitations, decrease the display resolution and check if framerate improved.</span></span> 
    - <span data-ttu-id="7107c-170">在 Unity 中，這可以透過*[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 屬性</span><span class="sxs-lookup"><span data-stu-id="7107c-170">In Unity, this can be done via the  *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* property</span></span>

<span data-ttu-id="7107c-171">記憶體頻寬通常會涉及到最佳化</span><span class="sxs-lookup"><span data-stu-id="7107c-171">Memory bandwidth generally involves optimizations to either</span></span>
1) <span data-ttu-id="7107c-172">減少紋理的解決方式</span><span class="sxs-lookup"><span data-stu-id="7107c-172">decrease texture resolutions</span></span>
2) <span data-ttu-id="7107c-173">使用較少的紋理 （亦即</span><span class="sxs-lookup"><span data-stu-id="7107c-173">utilize less textures (i.e</span></span> <span data-ttu-id="7107c-174">法線反射，等等）</span><span class="sxs-lookup"><span data-stu-id="7107c-174">normals, specular, etc)</span></span>

<span data-ttu-id="7107c-175">填滿率主要著重於降低作業需要計算最終呈現的像素數目。</span><span class="sxs-lookup"><span data-stu-id="7107c-175">Fill rate is primarily focused on reducing the number of operations that need to be computed for a final rendered pixel.</span></span> <span data-ttu-id="7107c-176">這個範例通常分為減少</span><span class="sxs-lookup"><span data-stu-id="7107c-176">Examples of this commonly fall into reducing</span></span>
1) <span data-ttu-id="7107c-177">要轉譯/處理序的物件數目</span><span class="sxs-lookup"><span data-stu-id="7107c-177">number of objects to render/process</span></span>
2) <span data-ttu-id="7107c-178">每著色器的作業數目</span><span class="sxs-lookup"><span data-stu-id="7107c-178">number of operations per shader</span></span>
3) <span data-ttu-id="7107c-179">最終的結果 （幾何著色器後, 置處理效果等） 的 GPU 階段數目</span><span class="sxs-lookup"><span data-stu-id="7107c-179">number of GPU stages to final result (geometry shaders, post-processing effects, etc)</span></span>
4) <span data-ttu-id="7107c-180">要呈現 （也就是像素數</span><span class="sxs-lookup"><span data-stu-id="7107c-180">number of pixels to render (i.e</span></span> <span data-ttu-id="7107c-181">顯示器解析度）</span><span class="sxs-lookup"><span data-stu-id="7107c-181">display resolution)</span></span>

#### <a name="reduce-poly-count"></a><span data-ttu-id="7107c-182">多邊計數減少</span><span class="sxs-lookup"><span data-stu-id="7107c-182">Reduce poly count</span></span>
<span data-ttu-id="7107c-183">較高的多邊形計算中的 GPU 的更多作業的結果，並減少場景中的多邊形的數目會減少時間轉譯的幾何內。</span><span class="sxs-lookup"><span data-stu-id="7107c-183">Higher polygon counts result in more operations for the GPU and reducing the number of polygons in your scene will reduce the amount of time to render that geometry.</span></span> <span data-ttu-id="7107c-184">還有其他因素也參與陰影的幾何，仍然十分耗費資源，但多邊形計數是基底的計量來判斷昂貴程度的場景會呈現。</span><span class="sxs-lookup"><span data-stu-id="7107c-184">There are other factors involved as well in shading the geometry that can still be expensive but polygon count is the base metric to determine how expensive a scene will be to render.</span></span>

#### <a name="limit-overdraw"></a><span data-ttu-id="7107c-185">過度限制</span><span class="sxs-lookup"><span data-stu-id="7107c-185">Limit overdraw</span></span>

<span data-ttu-id="7107c-186">最高過度繪製多個物件會轉譯，但因為它們由另一個、 一般接近 occluding 物件隱藏不輸出至畫面時，就會發生。</span><span class="sxs-lookup"><span data-stu-id="7107c-186">High overdraw occurs when multiple objects are rendered but not outputted to the screen as they are hidden by another, generally closer, occluding object.</span></span> <span data-ttu-id="7107c-187">想像一下，看看的牆，有多個聊天室和其背後的幾何。</span><span class="sxs-lookup"><span data-stu-id="7107c-187">Imagine looking at a wall that had multiple rooms and geometry behind it.</span></span> <span data-ttu-id="7107c-188">所有幾何的轉譯就會被處理，但不透明的牆，實際上需要轉譯為它 occludes 所有其他內容的檢視。</span><span class="sxs-lookup"><span data-stu-id="7107c-188">All of the geometry would be processed for rendering but only the opaque wall really needs to be rendered as it occludes the view of all other content.</span></span> <span data-ttu-id="7107c-189">這會導致浪費資源的作業不需要目前的檢視。</span><span class="sxs-lookup"><span data-stu-id="7107c-189">This results in wasteful operations that are not needed for the current view.</span></span>

#### <a name="shaders"></a><span data-ttu-id="7107c-190">著色器</span><span class="sxs-lookup"><span data-stu-id="7107c-190">Shaders</span></span>

<span data-ttu-id="7107c-191">著色器是小型的程式在 GPU 上執行，並通常決定在轉譯的兩個重要步驟：</span><span class="sxs-lookup"><span data-stu-id="7107c-191">Shaders are small programs that run on the GPU and generally determine two important steps in rendering:</span></span>
1) <span data-ttu-id="7107c-192">應螢幕，以及它們的螢幕空間 （也就是中的位置上繪製哪些物件的頂點</span><span class="sxs-lookup"><span data-stu-id="7107c-192">which object's vertices should be drawn on the screen and where they are in screen space (i.e</span></span> <span data-ttu-id="7107c-193">端點著色器）</span><span class="sxs-lookup"><span data-stu-id="7107c-193">the Vertex shader)</span></span>
    - <span data-ttu-id="7107c-194">頂點著色器通常針對每個 GameObject 執行每個頂點</span><span class="sxs-lookup"><span data-stu-id="7107c-194">The Vertex shader is generally executed per vertex for every GameObject</span></span>
2) <span data-ttu-id="7107c-195">功能 （也就是這些像素的色彩</span><span class="sxs-lookup"><span data-stu-id="7107c-195">what to color those pixels (i.e</span></span> <span data-ttu-id="7107c-196">像素著色器）</span><span class="sxs-lookup"><span data-stu-id="7107c-196">the Pixel shader)</span></span>
    - <span data-ttu-id="7107c-197">像素著色器會執行每個像素的裝置存在所呈現的材質</span><span class="sxs-lookup"><span data-stu-id="7107c-197">The Pixel shader is executed per pixel for the texture being rendered for device present</span></span>

<span data-ttu-id="7107c-198">通常著色器所執行的許多轉換和光源計算。</span><span class="sxs-lookup"><span data-stu-id="7107c-198">Typically shaders perform many transformations and lighting calculations.</span></span> <span data-ttu-id="7107c-199">雖然複雜光源模型、 陰影、 和其他作業可以產生絕佳的結果，它們也會隨附價格。</span><span class="sxs-lookup"><span data-stu-id="7107c-199">Although complex lighting models, shadows, and other operations can generate fantastic results, they also come with a price.</span></span> <span data-ttu-id="7107c-200">減少計算著色器的作業數目，可大幅減少每個畫面的 GPU 來完成所需的整體工作。</span><span class="sxs-lookup"><span data-stu-id="7107c-200">Reducing the number of operations computed in shaders can greatly reduce the overall work needed to be done by a GPU per frame.</span></span>

##### <a name="shader-coding-recommendations"></a><span data-ttu-id="7107c-201">著色器程式碼的建議</span><span class="sxs-lookup"><span data-stu-id="7107c-201">Shader coding recommendations</span></span>

- <span data-ttu-id="7107c-202">使用雙線性篩選盡可能</span><span class="sxs-lookup"><span data-stu-id="7107c-202">Use bilinear filtering whenever possible</span></span>
- <span data-ttu-id="7107c-203">重新排列為了同時執行 multiply 和新增使用瘋狂的內建函式的運算式</span><span class="sxs-lookup"><span data-stu-id="7107c-203">Rearrange expressions to use MAD intrinsics in order to do a multiply and an add at the same time</span></span>
- <span data-ttu-id="7107c-204">預先盡量在 CPU 上，並將資料傳遞為常數</span><span class="sxs-lookup"><span data-stu-id="7107c-204">Precalculate as much as possible on the CPU and pass as constants to the material</span></span>
- <span data-ttu-id="7107c-205">**偏好將作業從像素著色器移至頂點著色器**</span><span class="sxs-lookup"><span data-stu-id="7107c-205">**Favor moving operations from the pixel shader to the vertex shader**</span></span>
    - <span data-ttu-id="7107c-206">通常的頂點數目 << # 個像素為單位 （也就是</span><span class="sxs-lookup"><span data-stu-id="7107c-206">Generally the # of vertices << # of pixels (i.e</span></span> <span data-ttu-id="7107c-207">720p = = 921,600 像素為單位，1080p = = 2,073,600 像素為單位，依此類推)</span><span class="sxs-lookup"><span data-stu-id="7107c-207">720p == 921,600 pixels, 1080p == 2,073,600 pixels, etc)</span></span>

#### <a name="remove-gpu-stages"></a><span data-ttu-id="7107c-208">移除 GPU 階段</span><span class="sxs-lookup"><span data-stu-id="7107c-208">Remove GPU stages</span></span>
<span data-ttu-id="7107c-209">後置處理效果，可以是非常耗費資源，並通常禁止的應用程式的填滿率。</span><span class="sxs-lookup"><span data-stu-id="7107c-209">Post-processing effects can be very expensive and generally inhibit the fill rate of your application.</span></span> <span data-ttu-id="7107c-210">這也包括消除鋸齒的技術，例如 MSAA。</span><span class="sxs-lookup"><span data-stu-id="7107c-210">This also includes anti-aliasing techniques such as MSAA.</span></span> <span data-ttu-id="7107c-211">在 HoloLens，建議您使用完全避免這些技術。</span><span class="sxs-lookup"><span data-stu-id="7107c-211">On HoloLens, it is recommended to avoid these techniques entirely.</span></span> <span data-ttu-id="7107c-212">此外，如果可能的話，應避免額外的著色器階段，例如幾何、 輪廓，以及計算著色器。</span><span class="sxs-lookup"><span data-stu-id="7107c-212">Furthermore, additional shader stages such as geometry, hull, and compute shaders should be avoided when possible.</span></span>

## <a name="memory-recommendations"></a><span data-ttu-id="7107c-213">記憶體建議</span><span class="sxs-lookup"><span data-stu-id="7107c-213">Memory recommendations</span></span>
<span data-ttu-id="7107c-214">過多的記憶體配置和解除配置作業可以有負面的影響，在您全像攝影版的應用程式，導致不一致的效能、 凍結的畫面格和其他有害的行為。</span><span class="sxs-lookup"><span data-stu-id="7107c-214">Excessive memory allocation & deallocation operations can have adverse effects on your holographic application resulting in inconsistent performance, frozen frames, and other detrimental behavior.</span></span> <span data-ttu-id="7107c-215">它是特別重要，因為記憶體管理由記憶體回收行程控制在 Unity 中開發時，了解記憶體考量。</span><span class="sxs-lookup"><span data-stu-id="7107c-215">It is especially important to understand memory considerations when developing in Unity since memory management is controlled by the garbage collector.</span></span>

#### <a name="object-pooling"></a><span data-ttu-id="7107c-216">物件集區</span><span class="sxs-lookup"><span data-stu-id="7107c-216">Object pooling</span></span>

<span data-ttu-id="7107c-217">物件共用便是常用的技巧來減少連續配置的成本和取消配置的物件。</span><span class="sxs-lookup"><span data-stu-id="7107c-217">Object pooling is a popular technique to reduce the cost of continuous allocations & deallocations of objects.</span></span> <span data-ttu-id="7107c-218">這是所配置的相同物件的大型集區，並重複使用而不斷產生，並終結一段時間的物件不是此集區中的 非作用中、 可用的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7107c-218">This is done by allocating a large pool of identical objects and re-using inactive, available instances from this pool instead of constantly spawning and destroying objects over time.</span></span> <span data-ttu-id="7107c-219">物件集區很適合重複使用變數的存留期期間應用程式的元件。</span><span class="sxs-lookup"><span data-stu-id="7107c-219">Object pools are great for re-useable components that have variable lifetime during an app.</span></span>

## <a name="see-also"></a><span data-ttu-id="7107c-220">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7107c-220">See also</span></span>
- [<span data-ttu-id="7107c-221">Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="7107c-221">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
- [<span data-ttu-id="7107c-222">Unity 的建議的設定</span><span class="sxs-lookup"><span data-stu-id="7107c-222">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
