---
title: 應用程式的品質準則
description: 本文件說明最上層的因素影響混合的實境應用程式的品質。
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: 應用程式品質準則，混合實境，混合實境應用程式
ms.openlocfilehash: 756bc148f290aa3406c9ac8bb7003d463c62772c
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974743"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="1bb90-104">應用程式的品質準則</span><span class="sxs-lookup"><span data-stu-id="1bb90-104">App quality criteria</span></span>

<span data-ttu-id="1bb90-105">本文件說明最上層的因素影響混合的實境應用程式的品質。</span><span class="sxs-lookup"><span data-stu-id="1bb90-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="1bb90-106">針對每個因素提供下列資訊</span><span class="sxs-lookup"><span data-stu-id="1bb90-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="1bb90-107">概觀 ─ 品質係數和重要性的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="1bb90-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="1bb90-108">裝置影響-哪一種視窗混合實境裝置會受到影響。</span><span class="sxs-lookup"><span data-stu-id="1bb90-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="1bb90-109">品質準則 – 如何評估品質係數。</span><span class="sxs-lookup"><span data-stu-id="1bb90-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="1bb90-110">如何測量 – 量值 （或體驗） 問題的方法。</span><span class="sxs-lookup"><span data-stu-id="1bb90-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="1bb90-111">建議 – 摘要的方法來提供較佳的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="1bb90-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="1bb90-112">資源-相關的開發人員和設計資源，適合用來建立更優質的應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="1bb90-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="1bb90-113">畫面播放速率</span><span class="sxs-lookup"><span data-stu-id="1bb90-113">Frame rate</span></span>

<span data-ttu-id="1bb90-114">畫面播放速率是全像穩定性和使用者緩和的第一要件。</span><span class="sxs-lookup"><span data-stu-id="1bb90-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="1bb90-115">畫面播放速率低於建議的目標可能會導致出現抖動，造成負面影響的經驗 believability，而可能造成眼睛疲勞全像投影。</span><span class="sxs-lookup"><span data-stu-id="1bb90-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="1bb90-116">60 赫茲或您想要支援根據哪一個 Windows Mixed Reality 相容電腦的 90 Hz，將會針對您的體驗，在 Windows Mixed Reality 沈浸式耳機目標畫面播放速率。</span><span class="sxs-lookup"><span data-stu-id="1bb90-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="1bb90-117">HoloLens 目標畫面播放速率是 60 赫茲。</span><span class="sxs-lookup"><span data-stu-id="1bb90-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="1bb90-118">裝置的影響</span><span class="sxs-lookup"><span data-stu-id="1bb90-118">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="1bb90-119"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1bb90-119"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1bb90-120"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="1bb90-120"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="1bb90-121">✔️</span><span class="sxs-lookup"><span data-stu-id="1bb90-121">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="1bb90-122">✔️</span><span class="sxs-lookup"><span data-stu-id="1bb90-122">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="1bb90-123">品質準則</span><span class="sxs-lookup"><span data-stu-id="1bb90-123">Quality criteria</span></span>

|  <span data-ttu-id="1bb90-124">最佳</span><span class="sxs-lookup"><span data-stu-id="1bb90-124">Best</span></span>  |  <span data-ttu-id="1bb90-125">符合</span><span class="sxs-lookup"><span data-stu-id="1bb90-125">Meets</span></span> |  <span data-ttu-id="1bb90-126">失敗</span><span class="sxs-lookup"><span data-stu-id="1bb90-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="1bb90-127">應用程式一致的方式符合每個目標裝置的第二個 (FPS) 目標畫面格：HoloLens; 上的 60 fps在 超級電腦; 90 fps並在主要電腦上的 60 fps。</span><span class="sxs-lookup"><span data-stu-id="1bb90-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="1bb90-128">應用程式有間歇性的框架會卸除不妨礙的核心體驗;或 FPS 一致低於所需目標，但不會妨礙應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="1bb90-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="1bb90-129">應用程式發生平均每隔 10 秒或更少的畫面播放速率會下降。</span><span class="sxs-lookup"><span data-stu-id="1bb90-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="1bb90-130">如何測量</span><span class="sxs-lookup"><span data-stu-id="1bb90-130">How to measure</span></span>

* <span data-ttu-id="1bb90-131">透過提供即時的畫面格速率圖形所[Windows Device Portal](using-the-windows-device-portal.md#system-performance) [系統效能] 底下。</span><span class="sxs-lookup"><span data-stu-id="1bb90-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="1bb90-132">進行偵錯開發，將應用程式中的畫面播放速率診斷計時器。</span><span class="sxs-lookup"><span data-stu-id="1bb90-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="1bb90-133">請參閱範例計數器的資源。</span><span class="sxs-lookup"><span data-stu-id="1bb90-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="1bb90-134">藉由左右移動您執行應用程式時，可以在裝置發生畫面格速率會卸除。</span><span class="sxs-lookup"><span data-stu-id="1bb90-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="1bb90-135">如果全像圖顯示非預期的抖動移動，然後低畫面播放速率或穩定性平面是可能的原因。</span><span class="sxs-lookup"><span data-stu-id="1bb90-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="1bb90-136">建議</span><span class="sxs-lookup"><span data-stu-id="1bb90-136">Recommendations</span></span>

* <span data-ttu-id="1bb90-137">開發工作的開頭加入畫面格速率計數器。</span><span class="sxs-lookup"><span data-stu-id="1bb90-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="1bb90-138">應該評估並適當地解析為效能錯誤會造成畫面播放速率下降的變更。</span><span class="sxs-lookup"><span data-stu-id="1bb90-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="1bb90-139">資源</span><span class="sxs-lookup"><span data-stu-id="1bb90-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="1bb90-140">文件</span><span class="sxs-lookup"><span data-stu-id="1bb90-140">Documentation</span></span>

* [<span data-ttu-id="1bb90-141">了解效能 for Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="1bb90-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="1bb90-142">全像穩定性和畫面播放速率</span><span class="sxs-lookup"><span data-stu-id="1bb90-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="1bb90-143">資產的效能預算</span><span class="sxs-lookup"><span data-stu-id="1bb90-143">Asset performance budget</span></span>](asset-creation-process.md)
* [<span data-ttu-id="1bb90-144">對 Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="1bb90-144">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="1bb90-145">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="1bb90-145">Tools and tutorials</span></span>

* [<span data-ttu-id="1bb90-146">MRToolkit，FPS 計數器顯示</span><span class="sxs-lookup"><span data-stu-id="1bb90-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="1bb90-147">MRToolkit，著色器</span><span class="sxs-lookup"><span data-stu-id="1bb90-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="1bb90-148">外部參考</span><span class="sxs-lookup"><span data-stu-id="1bb90-148">External references</span></span>

* [<span data-ttu-id="1bb90-149">Unity，最佳化行動應用程式</span><span class="sxs-lookup"><span data-stu-id="1bb90-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="1bb90-150">全像穩定性</span><span class="sxs-lookup"><span data-stu-id="1bb90-150">Hologram stability</span></span>

<span data-ttu-id="1bb90-151">穩定全像投影會增加的可用性和 believability 應用程式，並建立更舒適的檢視經驗的使用者。</span><span class="sxs-lookup"><span data-stu-id="1bb90-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="1bb90-152">全像穩定性的品質是良好的應用程式開發，以及裝置的能力，以了解 （追蹤） 的結果，其環境。</span><span class="sxs-lookup"><span data-stu-id="1bb90-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="1bb90-153">穩定性的第一要件畫面播放速率時，其他因素可能會影響穩定性包括：</span><span class="sxs-lookup"><span data-stu-id="1bb90-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="1bb90-154">穩定平面的使用</span><span class="sxs-lookup"><span data-stu-id="1bb90-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="1bb90-155">空間的錨點的距離</span><span class="sxs-lookup"><span data-stu-id="1bb90-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="1bb90-156">追蹤</span><span class="sxs-lookup"><span data-stu-id="1bb90-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="1bb90-157">裝置的影響</span><span class="sxs-lookup"><span data-stu-id="1bb90-157">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="1bb90-158"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1bb90-158"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1bb90-159"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="1bb90-159"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="1bb90-160">✔️</span><span class="sxs-lookup"><span data-stu-id="1bb90-160">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="1bb90-161">品質準則</span><span class="sxs-lookup"><span data-stu-id="1bb90-161">Quality criteria</span></span>

|  <span data-ttu-id="1bb90-162">最佳</span><span class="sxs-lookup"><span data-stu-id="1bb90-162">Best</span></span>  |  <span data-ttu-id="1bb90-163">符合</span><span class="sxs-lookup"><span data-stu-id="1bb90-163">Meets</span></span> |  <span data-ttu-id="1bb90-164">失敗</span><span class="sxs-lookup"><span data-stu-id="1bb90-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="1bb90-165">以一致的方式，全像投影會出現穩定狀態。</span><span class="sxs-lookup"><span data-stu-id="1bb90-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="1bb90-166">次要內容表現出非預期的移動方式;或非預期的移動不會影響整體應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="1bb90-166">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="1bb90-167">在框架中的主要內容表現出非預期的移動。</span><span class="sxs-lookup"><span data-stu-id="1bb90-167">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="1bb90-168">如何測量</span><span class="sxs-lookup"><span data-stu-id="1bb90-168">How to measure</span></span>

<span data-ttu-id="1bb90-169">頭戴裝置和檢視體驗時：</span><span class="sxs-lookup"><span data-stu-id="1bb90-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="1bb90-170">移動您並排，如果全像投影顯示非預期的移動然後低畫面播放速率，或不正確的對齊方式主要平面穩定性平面的是可能的原因。</span><span class="sxs-lookup"><span data-stu-id="1bb90-170">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="1bb90-171">移動全像投影和環境中，找出 jumpiness 泳道等的行為。</span><span class="sxs-lookup"><span data-stu-id="1bb90-171">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="1bb90-172">這種類型的動作可能被造成裝置不追蹤環境或距離的空間的錨點。</span><span class="sxs-lookup"><span data-stu-id="1bb90-172">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="1bb90-173">如果是大型或多個全像投影會在框架中，觀察在各種深度的全像行為，而您前端的位置從左右移動，如果 shakiness 出現這可能是因穩定平面。</span><span class="sxs-lookup"><span data-stu-id="1bb90-173">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recomendations"></a><span data-ttu-id="1bb90-174">建議</span><span class="sxs-lookup"><span data-stu-id="1bb90-174">Recomendations</span></span>

* <span data-ttu-id="1bb90-175">開發工作的開頭加入的畫面播放速率計時器。</span><span class="sxs-lookup"><span data-stu-id="1bb90-175">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="1bb90-176">使用穩定平面。</span><span class="sxs-lookup"><span data-stu-id="1bb90-176">Use the stabilization plane.</span></span>
* <span data-ttu-id="1bb90-177">一定會轉譯錨定全像投影中的其錨點 3 公尺。</span><span class="sxs-lookup"><span data-stu-id="1bb90-177">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="1bb90-178">請確定您的環境設定適當的追蹤。</span><span class="sxs-lookup"><span data-stu-id="1bb90-178">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="1bb90-179">設計您的體驗，以避免全像投影的範圍內的各個主要的深度層級。</span><span class="sxs-lookup"><span data-stu-id="1bb90-179">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="1bb90-180">資源</span><span class="sxs-lookup"><span data-stu-id="1bb90-180">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="1bb90-181">文件</span><span class="sxs-lookup"><span data-stu-id="1bb90-181">Documentation</span></span>

* [<span data-ttu-id="1bb90-182">全像穩定性和畫面播放速率</span><span class="sxs-lookup"><span data-stu-id="1bb90-182">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="1bb90-183">案例研究，使用穩定平面</span><span class="sxs-lookup"><span data-stu-id="1bb90-183">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="1bb90-184">了解效能 for Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="1bb90-184">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="1bb90-185">對 Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="1bb90-185">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="1bb90-186">空間錨點</span><span class="sxs-lookup"><span data-stu-id="1bb90-186">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="1bb90-187">處理追蹤錯誤</span><span class="sxs-lookup"><span data-stu-id="1bb90-187">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="1bb90-188">靜態參考座標系</span><span class="sxs-lookup"><span data-stu-id="1bb90-188">Stationary frame of reference</span></span>](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="1bb90-189">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="1bb90-189">Tools and tutorials</span></span>

* [<span data-ttu-id="1bb90-190">MR 附屬套件，Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="1bb90-190">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="1bb90-191">在實際的介面上的全像投影位置</span><span class="sxs-lookup"><span data-stu-id="1bb90-191">Holograms position on real surfaces</span></span>

<span data-ttu-id="1bb90-192">Misalignments 的全像投影的實體物件 （如果要置於彼此） 是清楚的非等位的全像投影和真實世界。</span><span class="sxs-lookup"><span data-stu-id="1bb90-192">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="1bb90-193">位置的精確度應該是相對的案例需求比方說，一般的表面放置可用空間的對應，但更精確的位置將會需要某些使用標記和校正。</span><span class="sxs-lookup"><span data-stu-id="1bb90-193">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="1bb90-194">裝置的影響</span><span class="sxs-lookup"><span data-stu-id="1bb90-194">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="1bb90-195"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1bb90-195"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1bb90-196"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="1bb90-196"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="1bb90-197">✔️</span><span class="sxs-lookup"><span data-stu-id="1bb90-197">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="1bb90-198">品質準則</span><span class="sxs-lookup"><span data-stu-id="1bb90-198">Quality criteria</span></span>

|  <span data-ttu-id="1bb90-199">最佳</span><span class="sxs-lookup"><span data-stu-id="1bb90-199">Best</span></span>  |  <span data-ttu-id="1bb90-200">符合</span><span class="sxs-lookup"><span data-stu-id="1bb90-200">Meets</span></span> |  <span data-ttu-id="1bb90-201">失敗</span><span class="sxs-lookup"><span data-stu-id="1bb90-201">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="1bb90-202">全像投影對齊英吋為單位的範圍通常以公分為單位的介面。</span><span class="sxs-lookup"><span data-stu-id="1bb90-202">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="1bb90-203">如果需要更精確，應用程式應該提供有效率的方法中所需的應用程式規格的共同作業。</span><span class="sxs-lookup"><span data-stu-id="1bb90-203">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="1bb90-204">NA</span><span class="sxs-lookup"><span data-stu-id="1bb90-204">NA</span></span> | <span data-ttu-id="1bb90-205">全像投影重大介面平面或似乎 float 遠離介面會出現與實體的目標物件未對齊。</span><span class="sxs-lookup"><span data-stu-id="1bb90-205">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="1bb90-206">如果需要精確度，全像投影應該符合案例的鄰近性規格。</span><span class="sxs-lookup"><span data-stu-id="1bb90-206">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="1bb90-207">如何測量</span><span class="sxs-lookup"><span data-stu-id="1bb90-207">How to measure</span></span>

* <span data-ttu-id="1bb90-208">空間對應的全像投影不應該出現大幅浮動的上方或下方的介面。</span><span class="sxs-lookup"><span data-stu-id="1bb90-208">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="1bb90-209">全像投影需要精確的位置應該有某種形式的標記，並在校正的精確度的案例需求的系統。</span><span class="sxs-lookup"><span data-stu-id="1bb90-209">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="1bb90-210">建議</span><span class="sxs-lookup"><span data-stu-id="1bb90-210">Recommendations</span></span>

* <span data-ttu-id="1bb90-211">空間對應可用於將物件放在介面上，有效位數不需要時。</span><span class="sxs-lookup"><span data-stu-id="1bb90-211">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="1bb90-212">最佳的有效位數，如使用標記或海報來設定全像投影和 Xbox 控制器 （或一些手動的對齊方式機制） 的最終的校正。</span><span class="sxs-lookup"><span data-stu-id="1bb90-212">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="1bb90-213">請考慮分成邏輯的組件中的超大型全像投影大小以及對齊這些介面的每個組件。</span><span class="sxs-lookup"><span data-stu-id="1bb90-213">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="1bb90-214">未正確設定 interpupilary 的距離 (IPD) 也可以影響全像對齊。</span><span class="sxs-lookup"><span data-stu-id="1bb90-214">Improperly set interpupilary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="1bb90-215">一律先設定使用者的 IPD 的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="1bb90-215">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="1bb90-216">資源</span><span class="sxs-lookup"><span data-stu-id="1bb90-216">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="1bb90-217">文件</span><span class="sxs-lookup"><span data-stu-id="1bb90-217">Documentation</span></span>

* [<span data-ttu-id="1bb90-218">空間的對應位置</span><span class="sxs-lookup"><span data-stu-id="1bb90-218">Spatial mapping placement</span></span>](spatial-mapping.md#placement)
* [<span data-ttu-id="1bb90-219">掃描處理程序的房間</span><span class="sxs-lookup"><span data-stu-id="1bb90-219">Room scanning process</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="1bb90-220">空間的錨點的最佳作法</span><span class="sxs-lookup"><span data-stu-id="1bb90-220">Spatial anchors best practices</span></span>](spatial-anchors.md#best-practices)
* [<span data-ttu-id="1bb90-221">處理追蹤錯誤</span><span class="sxs-lookup"><span data-stu-id="1bb90-221">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="1bb90-222">Unity 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="1bb90-222">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="1bb90-223">Vuforia 開發概觀</span><span class="sxs-lookup"><span data-stu-id="1bb90-223">Vuforia development overview</span></span>](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="1bb90-224">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="1bb90-224">Tools and tutorials</span></span>

* [<span data-ttu-id="1bb90-225">MR Spatial 230：空間對應</span><span class="sxs-lookup"><span data-stu-id="1bb90-225">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="1bb90-226">MR 工具組，空間的對應程式庫</span><span class="sxs-lookup"><span data-stu-id="1bb90-226">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="1bb90-227">MR 附屬套件，海報校正範例</span><span class="sxs-lookup"><span data-stu-id="1bb90-227">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="1bb90-228">MR 附屬套件，Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="1bb90-228">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="1bb90-229">外部參考</span><span class="sxs-lookup"><span data-stu-id="1bb90-229">External references</span></span>

* [<span data-ttu-id="1bb90-230">Lowes 案例研究，有效位數的對齊方式</span><span class="sxs-lookup"><span data-stu-id="1bb90-230">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="1bb90-231">緩和的檢視區域</span><span class="sxs-lookup"><span data-stu-id="1bb90-231">Viewing zone of comfort</span></span>

<span data-ttu-id="1bb90-232">應用程式開發人員控制使用者的眼睛將內容和全像投影放在不同的深度交集的位置。</span><span class="sxs-lookup"><span data-stu-id="1bb90-232">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="1bb90-233">穿著 HoloLens 的使用者會永遠足以容納要保持清晰的影像 HoloLens 顯示因為固定的光學距離約 2.0 m 遠離使用者的 2.0 萬個。</span><span class="sxs-lookup"><span data-stu-id="1bb90-233">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="1bb90-234">不適當內容的深度可能會導致 visual discomfort 或疲勞。</span><span class="sxs-lookup"><span data-stu-id="1bb90-234">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="1bb90-235">裝置的影響</span><span class="sxs-lookup"><span data-stu-id="1bb90-235">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="1bb90-236"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1bb90-236"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1bb90-237"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="1bb90-237"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="1bb90-238">✔️</span><span class="sxs-lookup"><span data-stu-id="1bb90-238">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="1bb90-239">品質準則</span><span class="sxs-lookup"><span data-stu-id="1bb90-239">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="1bb90-240">最佳</span><span class="sxs-lookup"><span data-stu-id="1bb90-240">Best</span></span> </td><td><ul>
<li><span data-ttu-id="1bb90-241">將內容放在 2 分鐘。</span><span class="sxs-lookup"><span data-stu-id="1bb90-241">Place content at 2m.</span></span></li><li><span data-ttu-id="1bb90-242">全像投影不能放在 2 分鐘，而且無法避免的聚合和住宿之間的衝突，全像放置的最佳區域時 1.25 m 和 5 分鐘之間。</span><span class="sxs-lookup"><span data-stu-id="1bb90-242">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="1bb90-243">在每個案例中，設計工具應該在建構內容，以鼓勵使用者互動 1 + m 消失 （例如調整內容大小和位置參數的預設值）。</span><span class="sxs-lookup"><span data-stu-id="1bb90-243">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="1bb90-244">除非特別不需要的案例，裁剪平面應該與 fadeout 開始 1m 的實作。</span><span class="sxs-lookup"><span data-stu-id="1bb90-244">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="1bb90-245">在需要仔細觀察蒼穹全像所在的情況下，內容不應該超過 50 cm 接近。</span><span class="sxs-lookup"><span data-stu-id="1bb90-245">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="1bb90-246">符合</span><span class="sxs-lookup"><span data-stu-id="1bb90-246">Meets</span></span></td><td> <span data-ttu-id="1bb90-247">內容是中的檢視和動作的指導方針，但不當使用或不使用裁剪平面。</span><span class="sxs-lookup"><span data-stu-id="1bb90-247">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="1bb90-248">失敗</span><span class="sxs-lookup"><span data-stu-id="1bb90-248">Fail</span></span> </td><td> <span data-ttu-id="1bb90-249">太靠近呈現內容 (通常&lt;1.25 m 或&lt;50 cm 的 「 定態全像投影需要仔細觀察。)</span><span class="sxs-lookup"><span data-stu-id="1bb90-249">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="1bb90-250">如何測量</span><span class="sxs-lookup"><span data-stu-id="1bb90-250">How to measure</span></span>

* <span data-ttu-id="1bb90-251">內容通常都是 2m 淘汰過，但無法進一步比 1.25 或進一步超過 5 分鐘。</span><span class="sxs-lookup"><span data-stu-id="1bb90-251">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="1bb90-252">少數的例外狀況，HoloLens 裁剪轉譯距離應該設定為.85CM fadeout 的起價 1m 的內容使用。</span><span class="sxs-lookup"><span data-stu-id="1bb90-252">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="1bb90-253">方法內容，並注意裁剪平面的效果。</span><span class="sxs-lookup"><span data-stu-id="1bb90-253">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="1bb90-254">不應該接近放下 50 cm 比靜態內容。</span><span class="sxs-lookup"><span data-stu-id="1bb90-254">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="1bb90-255">建議</span><span class="sxs-lookup"><span data-stu-id="1bb90-255">Recommendations</span></span>

* <span data-ttu-id="1bb90-256">設計最佳的檢視之間距離的 2m 的內容。</span><span class="sxs-lookup"><span data-stu-id="1bb90-256">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="1bb90-257">設 85 cm 使用的內容開頭 1m fadeout 裁剪轉譯距離。</span><span class="sxs-lookup"><span data-stu-id="1bb90-257">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="1bb90-258">「 定態全像投影需要更接近檢視，應該不超過 30 cm 接近裁剪平面以及 fadeout 應該開始至少 10 個 cm 遠離裁剪平面。</span><span class="sxs-lookup"><span data-stu-id="1bb90-258">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="1bb90-259">資源</span><span class="sxs-lookup"><span data-stu-id="1bb90-259">Resources</span></span>

* [<span data-ttu-id="1bb90-260">轉譯距離</span><span class="sxs-lookup"><span data-stu-id="1bb90-260">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="1bb90-261">Unity 中的焦點</span><span class="sxs-lookup"><span data-stu-id="1bb90-261">Focus point in Unity</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="1bb90-262">小數位數的實驗</span><span class="sxs-lookup"><span data-stu-id="1bb90-262">Experimenting with scale</span></span>](scale.md#experimenting-with-scale)
* [<span data-ttu-id="1bb90-263">文字，建議使用的字型大小</span><span class="sxs-lookup"><span data-stu-id="1bb90-263">Text, Recommended font size</span></span>](typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="1bb90-264">深度切換</span><span class="sxs-lookup"><span data-stu-id="1bb90-264">Depth switching</span></span>

<span data-ttu-id="1bb90-265">檢視區域的緩和問題，不論要求之間切換時，經常或快速使用者接近，而且最主要的物件 （包括全像投影和實際內容） 可能會導致 oculomotor 疲勞症和一般 discomfort。</span><span class="sxs-lookup"><span data-stu-id="1bb90-265">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="1bb90-266">裝置的影響</span><span class="sxs-lookup"><span data-stu-id="1bb90-266">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="1bb90-267"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1bb90-267"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1bb90-268"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="1bb90-268"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="1bb90-269">✔️</span><span class="sxs-lookup"><span data-stu-id="1bb90-269">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="1bb90-270">✔️</span><span class="sxs-lookup"><span data-stu-id="1bb90-270">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="1bb90-271">品質準則</span><span class="sxs-lookup"><span data-stu-id="1bb90-271">Quality criteria</span></span>

|  <span data-ttu-id="1bb90-272">最佳</span><span class="sxs-lookup"><span data-stu-id="1bb90-272">Best</span></span>  |  <span data-ttu-id="1bb90-273">符合</span><span class="sxs-lookup"><span data-stu-id="1bb90-273">Meets</span></span> |  <span data-ttu-id="1bb90-274">失敗</span><span class="sxs-lookup"><span data-stu-id="1bb90-274">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="1bb90-275">有限或自然深度切換，並不會造成使用者出奇聚焦。</span><span class="sxs-lookup"><span data-stu-id="1bb90-275">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="1bb90-276">突然深度參數這是核心，而且設計到應用程式體驗或突然深度參數所造成未預期的實際內容。</span><span class="sxs-lookup"><span data-stu-id="1bb90-276">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="1bb90-277">一致的深度交換器或突然深度切換，就不需要或應用程式體驗的核心。</span><span class="sxs-lookup"><span data-stu-id="1bb90-277">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="1bb90-278">如何測量</span><span class="sxs-lookup"><span data-stu-id="1bb90-278">How to measure</span></span>

* <span data-ttu-id="1bb90-279">如果應用程式需要使用者以一致的方式和/或突然變更深度焦點，則切換問題的深度。</span><span class="sxs-lookup"><span data-stu-id="1bb90-279">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="1bb90-280">建議</span><span class="sxs-lookup"><span data-stu-id="1bb90-280">Recommendations</span></span>

* <span data-ttu-id="1bb90-281">保持一致的主要平面中的主要內容，以確保穩定平面符合主要的平面。</span><span class="sxs-lookup"><span data-stu-id="1bb90-281">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="1bb90-282">這將有助於解決 oculomotor 疲勞症和非預期的全像移動。</span><span class="sxs-lookup"><span data-stu-id="1bb90-282">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="1bb90-283">資源</span><span class="sxs-lookup"><span data-stu-id="1bb90-283">Resources</span></span>

* [<span data-ttu-id="1bb90-284">轉譯距離</span><span class="sxs-lookup"><span data-stu-id="1bb90-284">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="1bb90-285">Unity 中的焦點</span><span class="sxs-lookup"><span data-stu-id="1bb90-285">Focus point in Unity</span></span>](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="1bb90-286">使用的空間的音效</span><span class="sxs-lookup"><span data-stu-id="1bb90-286">Use of spatial sound</span></span>

<span data-ttu-id="1bb90-287">在 Windows Mixed Reality，音訊引擎會提供混合的實境體驗聽覺元件，藉由模擬 3D 音效使用方向、 距離和環境的模擬。</span><span class="sxs-lookup"><span data-stu-id="1bb90-287">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="1bb90-288">在 應用程式中使用空間的聲音各地使用者允許開發人員 convincingly 置於 3 維空間 （球形） 中的音效。</span><span class="sxs-lookup"><span data-stu-id="1bb90-288">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="1bb90-289">這些聽起來再看起來將如同就像是來自真正的實體物件或使用者的周圍環境中混合的實境全像投影。</span><span class="sxs-lookup"><span data-stu-id="1bb90-289">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="1bb90-290">空間的聲音是訓練活動，協助工具，在混合的實境應用程式的 UX 設計的強大工具。</span><span class="sxs-lookup"><span data-stu-id="1bb90-290">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="1bb90-291">裝置的影響</span><span class="sxs-lookup"><span data-stu-id="1bb90-291">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="1bb90-292"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1bb90-292"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1bb90-293"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="1bb90-293"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="1bb90-294">✔️</span><span class="sxs-lookup"><span data-stu-id="1bb90-294">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="1bb90-295">✔️</span><span class="sxs-lookup"><span data-stu-id="1bb90-295">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="1bb90-296">品質準則</span><span class="sxs-lookup"><span data-stu-id="1bb90-296">Quality criteria</span></span>

|  <span data-ttu-id="1bb90-297">最佳</span><span class="sxs-lookup"><span data-stu-id="1bb90-297">Best</span></span>  |  <span data-ttu-id="1bb90-298">符合</span><span class="sxs-lookup"><span data-stu-id="1bb90-298">Meets</span></span> |  <span data-ttu-id="1bb90-299">失敗</span><span class="sxs-lookup"><span data-stu-id="1bb90-299">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="1bb90-300">以邏輯方式 spatialized 音效，和 UX 適當地使用音效來協助物件探索和使用者意見反應。</span><span class="sxs-lookup"><span data-stu-id="1bb90-300">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="1bb90-301">音效的案例是自然並與物件相關的正規化。</span><span class="sxs-lookup"><span data-stu-id="1bb90-301">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="1bb90-302">空間的音訊會適當地用於 believability 缺少做為以協助使用者意見反應與探索性的方法。</span><span class="sxs-lookup"><span data-stu-id="1bb90-302">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="1bb90-303">如預期般運作，不 spatialized 音效和/或缺乏可協助使用者在 UX 中的音效</span><span class="sxs-lookup"><span data-stu-id="1bb90-303">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="1bb90-304">或不被視為或案例的設計使用空間的音訊。</span><span class="sxs-lookup"><span data-stu-id="1bb90-304">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="1bb90-305">如何測量</span><span class="sxs-lookup"><span data-stu-id="1bb90-305">How to measure</span></span>

* <span data-ttu-id="1bb90-306">一般情況下，相關的音效應該發出從目標全像投影 (例如。，全像攝影版的 dog 樹皮聲音。)</span><span class="sxs-lookup"><span data-stu-id="1bb90-306">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="1bb90-307">音效提示應該用於整個 UX 協助使用者意見反應或感知的全像攝影版的框架外的動作。</span><span class="sxs-lookup"><span data-stu-id="1bb90-307">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="1bb90-308">建議</span><span class="sxs-lookup"><span data-stu-id="1bb90-308">Recommendations</span></span>

* <span data-ttu-id="1bb90-309">物件探索和使用者介面協助使用空間的音訊。</span><span class="sxs-lookup"><span data-stu-id="1bb90-309">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="1bb90-310">實際的聲音優於合成或非自然音效運作。</span><span class="sxs-lookup"><span data-stu-id="1bb90-310">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="1bb90-311">應該 spatialized 大部分的音效。</span><span class="sxs-lookup"><span data-stu-id="1bb90-311">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="1bb90-312">避免不可見的 fixit 發出器。</span><span class="sxs-lookup"><span data-stu-id="1bb90-312">Avoid invisible emitters.</span></span>
* <span data-ttu-id="1bb90-313">避免空間的遮罩。</span><span class="sxs-lookup"><span data-stu-id="1bb90-313">Avoid spatial masking.</span></span>
* <span data-ttu-id="1bb90-314">正規化聽起來。</span><span class="sxs-lookup"><span data-stu-id="1bb90-314">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="1bb90-315">資源</span><span class="sxs-lookup"><span data-stu-id="1bb90-315">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="1bb90-316">文件</span><span class="sxs-lookup"><span data-stu-id="1bb90-316">Documentation</span></span>

* [<span data-ttu-id="1bb90-317">空間音效</span><span class="sxs-lookup"><span data-stu-id="1bb90-317">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="1bb90-318">空間音效設計</span><span class="sxs-lookup"><span data-stu-id="1bb90-318">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="1bb90-319">Unity 中的空間音效</span><span class="sxs-lookup"><span data-stu-id="1bb90-319">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="1bb90-320">案例研究，如 HoloTour 聲音的空間</span><span class="sxs-lookup"><span data-stu-id="1bb90-320">Case study, Spatial sound for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="1bb90-321">案例研究，RoboRaid 中使用空間的音效</span><span class="sxs-lookup"><span data-stu-id="1bb90-321">Case study, Using spatial sound in RoboRaid</span></span>](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="1bb90-322">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="1bb90-322">Tools and tutorials</span></span>

* [<span data-ttu-id="1bb90-323">MR Spatial 220：空間音效</span><span class="sxs-lookup"><span data-stu-id="1bb90-323">MR Spatial 220: Spatial sound</span></span>](holograms-220.md)
* [<span data-ttu-id="1bb90-324">MRToolkit，空間音訊</span><span class="sxs-lookup"><span data-stu-id="1bb90-324">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="1bb90-325">焦點放在全像攝影版的框架 (FOV) 界限</span><span class="sxs-lookup"><span data-stu-id="1bb90-325">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="1bb90-326">設計良好的使用者體驗，可以建立和維護擴充大約是使用者在虛擬環境的有用的內容。</span><span class="sxs-lookup"><span data-stu-id="1bb90-326">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="1bb90-327">緩和 FOV 界限的效果牽涉到仔細考量的設計內容的小數位數和內容，請使用空間的音訊、 指引系統和使用者的位置。</span><span class="sxs-lookup"><span data-stu-id="1bb90-327">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="1bb90-328">如果，使用者會覺得小於受損根據 FOV 界限時有舒適的應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="1bb90-328">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="1bb90-329">裝置的影響</span><span class="sxs-lookup"><span data-stu-id="1bb90-329">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="1bb90-330"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1bb90-330"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1bb90-331"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="1bb90-331"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="1bb90-332">✔️</span><span class="sxs-lookup"><span data-stu-id="1bb90-332">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="1bb90-333">品質準則</span><span class="sxs-lookup"><span data-stu-id="1bb90-333">Quality criteria</span></span>

|  <span data-ttu-id="1bb90-334">最佳</span><span class="sxs-lookup"><span data-stu-id="1bb90-334">Best</span></span>  |  <span data-ttu-id="1bb90-335">符合</span><span class="sxs-lookup"><span data-stu-id="1bb90-335">Meets</span></span> |  <span data-ttu-id="1bb90-336">失敗</span><span class="sxs-lookup"><span data-stu-id="1bb90-336">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="1bb90-337">使用者永遠不會遺失內容，而且知道如何檢視。</span><span class="sxs-lookup"><span data-stu-id="1bb90-337">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="1bb90-338">大型物件提供內容協助。</span><span class="sxs-lookup"><span data-stu-id="1bb90-338">Context assistance is provided for large objects.</span></span> <span data-ttu-id="1bb90-339">外框以外的物件提供可測知性和檢視的指引。</span><span class="sxs-lookup"><span data-stu-id="1bb90-339">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="1bb90-340">一般情況下，動態設計和小數位數全像投影適合舒適的檢視體驗。</span><span class="sxs-lookup"><span data-stu-id="1bb90-340">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="1bb90-341">使用者永遠不會遺失內容，但在少數的情況下，可能需要額外的頸部影片。</span><span class="sxs-lookup"><span data-stu-id="1bb90-341">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="1bb90-342">在少數的情況下擴展可能會中斷可能導致某些頸部動作，若要檢視全像投影的垂直或水平框架是全像投影。</span><span class="sxs-lookup"><span data-stu-id="1bb90-342">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="1bb90-343">使用者可能會遺失內容及/或一致的頸部動作，才能檢視全像投影。</span><span class="sxs-lookup"><span data-stu-id="1bb90-343">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="1bb90-344">沒有內容的指引將物件移容易會遺失任何可搜尋性指引，或高全像投影框架外部，全像攝影版的大型物件，需要一般的頸部運動，讓檢視。</span><span class="sxs-lookup"><span data-stu-id="1bb90-344">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="1bb90-345">如何測量</span><span class="sxs-lookup"><span data-stu-id="1bb90-345">How to measure</span></span>

* <span data-ttu-id="1bb90-346">內容 （大） 的全像遺失或不了解由於未經裁剪界限上。</span><span class="sxs-lookup"><span data-stu-id="1bb90-346">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="1bb90-347">全像投影的位置很難找到因為缺乏注意主管或快速斷斷續續全像攝影版的畫面格的內容。</span><span class="sxs-lookup"><span data-stu-id="1bb90-347">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="1bb90-348">案例需要一般和重複向上和向下完整查看導致頸部疲勞雷射前端的動作。</span><span class="sxs-lookup"><span data-stu-id="1bb90-348">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="1bb90-349">建議</span><span class="sxs-lookup"><span data-stu-id="1bb90-349">Recommendations</span></span>

* <span data-ttu-id="1bb90-350">開始體驗與小型物件符合 FOV，然後轉換至較大版本的視覺提示。</span><span class="sxs-lookup"><span data-stu-id="1bb90-350">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="1bb90-351">若要協助使用者尋找內容超出 FOV 使用空間的音訊，並注意董事會。</span><span class="sxs-lookup"><span data-stu-id="1bb90-351">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="1bb90-352">儘可能，避免，垂直裁剪 FOV 全像投影。</span><span class="sxs-lookup"><span data-stu-id="1bb90-352">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="1bb90-353">為使用者提供最佳的檢視位置的應用程式指引。</span><span class="sxs-lookup"><span data-stu-id="1bb90-353">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="1bb90-354">資源</span><span class="sxs-lookup"><span data-stu-id="1bb90-354">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="1bb90-355">文件</span><span class="sxs-lookup"><span data-stu-id="1bb90-355">Documentation</span></span>

* [<span data-ttu-id="1bb90-356">全像攝影框架</span><span class="sxs-lookup"><span data-stu-id="1bb90-356">Holographic frame</span></span>](holographic-frame.md)
* [<span data-ttu-id="1bb90-357">案例研究、 HoloStudio UI 和互動的設計做法</span><span class="sxs-lookup"><span data-stu-id="1bb90-357">Case Study, HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="1bb90-358">小數位數的物件和環境</span><span class="sxs-lookup"><span data-stu-id="1bb90-358">Scale of objects and environments</span></span>](scale.md)
* [<span data-ttu-id="1bb90-359">資料指標的視覺提示</span><span class="sxs-lookup"><span data-stu-id="1bb90-359">Cursors, Visual cues</span></span>](cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="1bb90-360">外部參考</span><span class="sxs-lookup"><span data-stu-id="1bb90-360">External references</span></span>

* [<span data-ttu-id="1bb90-361">關於 FOV 多 ado</span><span class="sxs-lookup"><span data-stu-id="1bb90-361">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="1bb90-362">內容回應至使用者的位置</span><span class="sxs-lookup"><span data-stu-id="1bb90-362">Content reacts to user position</span></span>

<span data-ttu-id="1bb90-363">全像投影應該回應大致上的 「 真實 」 物件的相同方式的使用者位置。</span><span class="sxs-lookup"><span data-stu-id="1bb90-363">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="1bb90-364">是值得注意的設計考量的重點是一定不能假設使用者的位置的 UI 項目為靜態，並且配合使用者的動作。</span><span class="sxs-lookup"><span data-stu-id="1bb90-364">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="1bb90-365">設計正確配合使用者位置的應用程式建立更可信的體驗，並讓它更容易使用。</span><span class="sxs-lookup"><span data-stu-id="1bb90-365">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="1bb90-366">裝置的影響</span><span class="sxs-lookup"><span data-stu-id="1bb90-366">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="1bb90-367"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1bb90-367"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1bb90-368"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="1bb90-368"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="1bb90-369">✔️</span><span class="sxs-lookup"><span data-stu-id="1bb90-369">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="1bb90-370">✔️</span><span class="sxs-lookup"><span data-stu-id="1bb90-370">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="1bb90-371">品質準則</span><span class="sxs-lookup"><span data-stu-id="1bb90-371">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="1bb90-372">最佳</span><span class="sxs-lookup"><span data-stu-id="1bb90-372">Best</span></span> </td><td> <span data-ttu-id="1bb90-373">內容和 UI 調整至使用者的位置，讓使用者自然互動與預期的使用者移動的範圍內的內容。</span><span class="sxs-lookup"><span data-stu-id="1bb90-373">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="1bb90-374">符合</span><span class="sxs-lookup"><span data-stu-id="1bb90-374">Meets</span></span> </td><td> <span data-ttu-id="1bb90-375">UI 調整到使用者的位置，但可能會妨礙要求使用者調整其位置的索引鍵內容的檢視。</span><span class="sxs-lookup"><span data-stu-id="1bb90-375">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="1bb90-376">失敗</span><span class="sxs-lookup"><span data-stu-id="1bb90-376">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="1bb90-377">UI 項目遺失或鎖定期間移動而造成使用者出奇返回 （或尋找） 控制項。</span><span class="sxs-lookup"><span data-stu-id="1bb90-377">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="1bb90-378">主要內容的檢視限制的 UI 項目。</span><span class="sxs-lookup"><span data-stu-id="1bb90-378">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="1bb90-379">UI 移動不適合檢視趨勢電子報，尤其是與距離<a href="billboarding-and-tag-along.md">tag-along</a> UI 項目。</span><span class="sxs-lookup"><span data-stu-id="1bb90-379">UI movement is not optimized for viewing distance and momentum particularly with <a href="billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="1bb90-380">如何測量</span><span class="sxs-lookup"><span data-stu-id="1bb90-380">How to measure</span></span>

* <span data-ttu-id="1bb90-381">所有度量均應完成的案例在合理範圍內。</span><span class="sxs-lookup"><span data-stu-id="1bb90-381">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="1bb90-382">當使用者移動而異時，請勿嘗試誘騙具有極高的使用者移動的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1bb90-382">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="1bb90-383">UI 項目，相關的控制項應該是可以使用無論使用者移動。</span><span class="sxs-lookup"><span data-stu-id="1bb90-383">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="1bb90-384">比方說，如果使用者是檢視，並與 zoom 的 3D 對應四處跑，縮放控制項應該不論位置為何，使用者可以輕易地使用。</span><span class="sxs-lookup"><span data-stu-id="1bb90-384">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="1bb90-385">建議</span><span class="sxs-lookup"><span data-stu-id="1bb90-385">Recommendations</span></span>

* <span data-ttu-id="1bb90-386">使用者是數位相機，它們控制移動。</span><span class="sxs-lookup"><span data-stu-id="1bb90-386">The user is the camera and they control the movement.</span></span> <span data-ttu-id="1bb90-387">讓這些磁碟機。</span><span class="sxs-lookup"><span data-stu-id="1bb90-387">Let them drive.</span></span>
* <span data-ttu-id="1bb90-388">考慮告示板文字，否則會世界鎖定或遮蔽如果使用者的施展空間系統四處移動。</span><span class="sxs-lookup"><span data-stu-id="1bb90-388">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="1bb90-389">您可以使用 tag-along 必須遵循使用者，同時仍然允許使用者查看最前面的內容。</span><span class="sxs-lookup"><span data-stu-id="1bb90-389">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="1bb90-390">資源</span><span class="sxs-lookup"><span data-stu-id="1bb90-390">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="1bb90-391">文件</span><span class="sxs-lookup"><span data-stu-id="1bb90-391">Documentation</span></span>

* [<span data-ttu-id="1bb90-392">互動設計</span><span class="sxs-lookup"><span data-stu-id="1bb90-392">Interaction design</span></span>](hologram.md)
* [<span data-ttu-id="1bb90-393">色彩、 光線及材料</span><span class="sxs-lookup"><span data-stu-id="1bb90-393">Color, light, and material</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="1bb90-394">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="1bb90-394">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="1bb90-395">本能互動</span><span class="sxs-lookup"><span data-stu-id="1bb90-395">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="1bb90-396">自我動作和使用者 locomotion</span><span class="sxs-lookup"><span data-stu-id="1bb90-396">Self-motion and user locomotion</span></span>](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="1bb90-397">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="1bb90-397">Tools and tutorials</span></span>

* [<span data-ttu-id="1bb90-398">MR Input 210：目光</span><span class="sxs-lookup"><span data-stu-id="1bb90-398">MR Input 210: Gaze</span></span>](holograms-210.md)

## <a name="input-interaction-clarity"></a><span data-ttu-id="1bb90-399">輸入的互動清晰度</span><span class="sxs-lookup"><span data-stu-id="1bb90-399">Input interaction clarity</span></span>

<span data-ttu-id="1bb90-400">輸入的互動清楚很重要的應用程式的可用性，以及包含輸入的一致性、 易學、 可搜尋性互動的方法。</span><span class="sxs-lookup"><span data-stu-id="1bb90-400">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="1bb90-401">使用者應該能夠使用不含 relearning 的全平台的常見的互動方式。</span><span class="sxs-lookup"><span data-stu-id="1bb90-401">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="1bb90-402">如果應用程式有自訂的輸入，它應該能夠清楚地溝通和證明。</span><span class="sxs-lookup"><span data-stu-id="1bb90-402">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="1bb90-403">裝置的影響</span><span class="sxs-lookup"><span data-stu-id="1bb90-403">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="1bb90-404"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1bb90-404"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1bb90-405"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="1bb90-405"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="1bb90-406">✔️</span><span class="sxs-lookup"><span data-stu-id="1bb90-406">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="1bb90-407">✔️</span><span class="sxs-lookup"><span data-stu-id="1bb90-407">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="1bb90-408">品質準則</span><span class="sxs-lookup"><span data-stu-id="1bb90-408">Quality criteria</span></span>

|  <span data-ttu-id="1bb90-409">最佳</span><span class="sxs-lookup"><span data-stu-id="1bb90-409">Best</span></span>  |  <span data-ttu-id="1bb90-410">符合</span><span class="sxs-lookup"><span data-stu-id="1bb90-410">Meets</span></span> |  <span data-ttu-id="1bb90-411">失敗</span><span class="sxs-lookup"><span data-stu-id="1bb90-411">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="1bb90-412">輸入的互動方法都必須配合提供的 Windows Mixed Reality[指引](interaction-fundamentals.md)。</span><span class="sxs-lookup"><span data-stu-id="1bb90-412">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](interaction-fundamentals.md).</span></span> <span data-ttu-id="1bb90-413">任何自訂的輸入不應該重複使用標準輸入 （而不是使用標準互動），必須能夠清楚地溝通和證明給使用者。</span><span class="sxs-lookup"><span data-stu-id="1bb90-413">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="1bb90-414">類似於最好的方式，但自訂的輸入是多餘的標準輸入的方法。</span><span class="sxs-lookup"><span data-stu-id="1bb90-414">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="1bb90-415">使用者仍可達到的目標和透過應用程式體驗的進度。</span><span class="sxs-lookup"><span data-stu-id="1bb90-415">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="1bb90-416">了解輸入的方法或按鈕對應很難。</span><span class="sxs-lookup"><span data-stu-id="1bb90-416">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="1bb90-417">輸入大量自訂，不支援標準的輸入，而不需指示，或可能會造成疲勞症和緩和問題。</span><span class="sxs-lookup"><span data-stu-id="1bb90-417">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="1bb90-418">如何測量</span><span class="sxs-lookup"><span data-stu-id="1bb90-418">How to measure</span></span>

* <span data-ttu-id="1bb90-419">應用程式中使用一致[標準輸入方法。](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="1bb90-419">The app uses consistent [standard input methods.](interaction-fundamentals.md)</span></span>
* <span data-ttu-id="1bb90-420">如果應用程式而代理商輸入，是將它透過清楚地溝通：</span><span class="sxs-lookup"><span data-stu-id="1bb90-420">If the app has custome input, it is clearly communicated through:</span></span>
* <span data-ttu-id="1bb90-421">首次執行經驗</span><span class="sxs-lookup"><span data-stu-id="1bb90-421">First-run experience</span></span>
* <span data-ttu-id="1bb90-422">簡介畫面</span><span class="sxs-lookup"><span data-stu-id="1bb90-422">Introductory screens</span></span>
* <span data-ttu-id="1bb90-423">工具提示</span><span class="sxs-lookup"><span data-stu-id="1bb90-423">Tooltips</span></span>
* <span data-ttu-id="1bb90-424">手狀 coach</span><span class="sxs-lookup"><span data-stu-id="1bb90-424">Hand coach</span></span>
* <span data-ttu-id="1bb90-425">說明區段</span><span class="sxs-lookup"><span data-stu-id="1bb90-425">Help section</span></span>
* <span data-ttu-id="1bb90-426">旁白</span><span class="sxs-lookup"><span data-stu-id="1bb90-426">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="1bb90-427">建議</span><span class="sxs-lookup"><span data-stu-id="1bb90-427">Recommendations</span></span>

* <span data-ttu-id="1bb90-428">使用盡可能的標準輸入的方法。</span><span class="sxs-lookup"><span data-stu-id="1bb90-428">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="1bb90-429">非標準的輸入方法提供示範、 教學課程和工具提示。</span><span class="sxs-lookup"><span data-stu-id="1bb90-429">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="1bb90-430">使用整個應用程式一致的互動模型。</span><span class="sxs-lookup"><span data-stu-id="1bb90-430">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="1bb90-431">資源</span><span class="sxs-lookup"><span data-stu-id="1bb90-431">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="1bb90-432">文件</span><span class="sxs-lookup"><span data-stu-id="1bb90-432">Documentation</span></span>

* [<span data-ttu-id="1bb90-433">本能互動</span><span class="sxs-lookup"><span data-stu-id="1bb90-433">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="1bb90-434">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="1bb90-434">Interactable objects</span></span>](interactable-object.md)
* [<span data-ttu-id="1bb90-435">頭部目光和停駐</span><span class="sxs-lookup"><span data-stu-id="1bb90-435">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="1bb90-436">游標</span><span class="sxs-lookup"><span data-stu-id="1bb90-436">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="1bb90-437">舒適度與視線</span><span class="sxs-lookup"><span data-stu-id="1bb90-437">Comfort and gaze</span></span>](comfort.md#gaze-direction)
* [<span data-ttu-id="1bb90-438">筆勢</span><span class="sxs-lookup"><span data-stu-id="1bb90-438">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="1bb90-439">語音輸入</span><span class="sxs-lookup"><span data-stu-id="1bb90-439">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="1bb90-440">語音命令</span><span class="sxs-lookup"><span data-stu-id="1bb90-440">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="1bb90-441">運動控制器</span><span class="sxs-lookup"><span data-stu-id="1bb90-441">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="1bb90-442">Unity 的輸入移植指南</span><span class="sxs-lookup"><span data-stu-id="1bb90-442">Input porting guide for Unity</span></span>](input-porting-guide-for-unity.md)
* [<span data-ttu-id="1bb90-443">Unity 中的鍵盤輸入</span><span class="sxs-lookup"><span data-stu-id="1bb90-443">Keyboard input in Unity</span></span>](keyboard-input-in-unity.md)
* [<span data-ttu-id="1bb90-444">Unity 中的目光</span><span class="sxs-lookup"><span data-stu-id="1bb90-444">Gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="1bb90-445">Unity 中的筆勢和運動控制器</span><span class="sxs-lookup"><span data-stu-id="1bb90-445">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="1bb90-446">Unity 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="1bb90-446">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="1bb90-447">DirectX 中的鍵盤、滑鼠及控制器輸入</span><span class="sxs-lookup"><span data-stu-id="1bb90-447">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="1bb90-448">DirectX 中的頭部和眼睛目光</span><span class="sxs-lookup"><span data-stu-id="1bb90-448">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="1bb90-449">DirectX 中的手部和運動控制器</span><span class="sxs-lookup"><span data-stu-id="1bb90-449">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="1bb90-450">DirectX 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="1bb90-450">Voice input in DirectX</span></span>](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="1bb90-451">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="1bb90-451">Tools and tutorials</span></span>

* [<span data-ttu-id="1bb90-452">案例研究：為達成更多個人運算</span><span class="sxs-lookup"><span data-stu-id="1bb90-452">Case study: The pursuit of more personal computing</span></span>](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="1bb90-453">Cast 研究：HoloStudio UI 和互動的設計做法</span><span class="sxs-lookup"><span data-stu-id="1bb90-453">Cast study: HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="1bb90-454">範例應用程式：定期的資料表的項目</span><span class="sxs-lookup"><span data-stu-id="1bb90-454">Sample app: Periodic table of the elements</span></span>](periodic-table-of-the-elements.md)
* [<span data-ttu-id="1bb90-455">範例應用程式：農曆模組</span><span class="sxs-lookup"><span data-stu-id="1bb90-455">Sample app: Lunar module</span></span>](lunar-module.md)
* [<span data-ttu-id="1bb90-456">MR Input 210：目光</span><span class="sxs-lookup"><span data-stu-id="1bb90-456">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="1bb90-457">MR Input 211：筆勢</span><span class="sxs-lookup"><span data-stu-id="1bb90-457">MR Input 211: Gestures</span></span>](holograms-211.md)
* [<span data-ttu-id="1bb90-458">MR Input 212：語音</span><span class="sxs-lookup"><span data-stu-id="1bb90-458">MR Input 212: Voice</span></span>](holograms-212.md)

## <a name="interactable-objects"></a><span data-ttu-id="1bb90-459">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="1bb90-459">Interactable objects</span></span>

<span data-ttu-id="1bb90-460">按鈕長久以來所用的觸發事件 2D 抽象全球隱喻。</span><span class="sxs-lookup"><span data-stu-id="1bb90-460">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="1bb90-461">在三維的混合的現實世界中，我們沒有不再侷限於這個抽象層再的世界。</span><span class="sxs-lookup"><span data-stu-id="1bb90-461">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="1bb90-462">任何項目可以是可互動的物件，都會觸發事件。</span><span class="sxs-lookup"><span data-stu-id="1bb90-462">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="1bb90-463">可互動的物件可以表示為任何項目從咖啡杯資料表在空中浮在球形文字說明。</span><span class="sxs-lookup"><span data-stu-id="1bb90-463">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="1bb90-464">表單中，不論可互動的物件應該清楚地識別使用者已透過視覺與音訊提示。</span><span class="sxs-lookup"><span data-stu-id="1bb90-464">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="1bb90-465">裝置的影響</span><span class="sxs-lookup"><span data-stu-id="1bb90-465">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="1bb90-466"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1bb90-466"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1bb90-467"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="1bb90-467"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="1bb90-468">✔️</span><span class="sxs-lookup"><span data-stu-id="1bb90-468">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="1bb90-469">✔️</span><span class="sxs-lookup"><span data-stu-id="1bb90-469">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="1bb90-470">品質準則</span><span class="sxs-lookup"><span data-stu-id="1bb90-470">Quality criteria</span></span>

|  <span data-ttu-id="1bb90-471">最佳</span><span class="sxs-lookup"><span data-stu-id="1bb90-471">Best</span></span>  |  <span data-ttu-id="1bb90-472">符合</span><span class="sxs-lookup"><span data-stu-id="1bb90-472">Meets</span></span> |  <span data-ttu-id="1bb90-473">失敗</span><span class="sxs-lookup"><span data-stu-id="1bb90-473">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="1bb90-474">表單中，不論可互動的物件都可透過視覺與音訊提示辨識三種狀態： 閒置，設為目標，並選取。</span><span class="sxs-lookup"><span data-stu-id="1bb90-474">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="1bb90-475">「 請查看它說它的項目 」 會清楚且一致地使用整個體驗。</span><span class="sxs-lookup"><span data-stu-id="1bb90-475">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="1bb90-476">物件會調整，並散發到允許免費為目標的錯誤。</span><span class="sxs-lookup"><span data-stu-id="1bb90-476">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="1bb90-477">使用者可以辨識為可透過音訊或視覺效果的意見反應，互動的物件和目標即可啟動物件。</span><span class="sxs-lookup"><span data-stu-id="1bb90-477">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="1bb90-478">沒有 visual 或音訊提示，使用者無法辨識的可互動的物件。</span><span class="sxs-lookup"><span data-stu-id="1bb90-478">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="1bb90-479">互動是因為物件小數位數或物件之間的距離而容易發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="1bb90-479">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="1bb90-480">如何測量</span><span class="sxs-lookup"><span data-stu-id="1bb90-480">How to measure</span></span>

* <span data-ttu-id="1bb90-481">可互動的物件會被視為 '互動';包括按鈕、 功能表和應用程式特定的內容。</span><span class="sxs-lookup"><span data-stu-id="1bb90-481">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="1bb90-482">根據經驗法則應該有視覺與音訊提示以互動的物件為目標時。</span><span class="sxs-lookup"><span data-stu-id="1bb90-482">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="1bb90-483">建議</span><span class="sxs-lookup"><span data-stu-id="1bb90-483">Recommendations</span></span>

* <span data-ttu-id="1bb90-484">使用互動視覺與音訊的意見反應。</span><span class="sxs-lookup"><span data-stu-id="1bb90-484">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="1bb90-485">視覺化回饋應該加以區別，針對每個輸入狀態 （閒置、 目標、 選取）</span><span class="sxs-lookup"><span data-stu-id="1bb90-485">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="1bb90-486">可互動的物件應該調整，而且置於錯誤的可用目標。</span><span class="sxs-lookup"><span data-stu-id="1bb90-486">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="1bb90-487">群組可互動的物件 （例如功能表列或清單中） 應該針對適當的間距。</span><span class="sxs-lookup"><span data-stu-id="1bb90-487">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="1bb90-488">按鈕和功能表支援語音命令，應該為命令關鍵字提供文字的標籤 （"看到它，它說出"）</span><span class="sxs-lookup"><span data-stu-id="1bb90-488">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="1bb90-489">資源</span><span class="sxs-lookup"><span data-stu-id="1bb90-489">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="1bb90-490">文件</span><span class="sxs-lookup"><span data-stu-id="1bb90-490">Documentation</span></span>

* [<span data-ttu-id="1bb90-491">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="1bb90-491">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="1bb90-492">Unity 中的文字</span><span class="sxs-lookup"><span data-stu-id="1bb90-492">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="1bb90-493">應用程式列和週框方塊</span><span class="sxs-lookup"><span data-stu-id="1bb90-493">App bar and bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="1bb90-494">語音命令</span><span class="sxs-lookup"><span data-stu-id="1bb90-494">Voice commanding</span></span>](voice-design.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="1bb90-495">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="1bb90-495">Tools and tutorials</span></span>

* [<span data-ttu-id="1bb90-496">混合的實境工具組-UX</span><span class="sxs-lookup"><span data-stu-id="1bb90-496">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="1bb90-497">掃描的房間</span><span class="sxs-lookup"><span data-stu-id="1bb90-497">Room scanning</span></span>

<span data-ttu-id="1bb90-498">需要空間的對應資料的應用程式依賴自動收集一段時間的這項資料的裝置，並以使用者的工作階段之間探索其環境與作用中裝置。</span><span class="sxs-lookup"><span data-stu-id="1bb90-498">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="1bb90-499">完整性和品質的這項資料取決於許多因素，包括使用者已完成探勘數量、 瀏覽過多少時間，以及是否物件，例如 furniture 和機門已因為裝置掃描區域。</span><span class="sxs-lookup"><span data-stu-id="1bb90-499">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="1bb90-500">許多應用程式會分析空間的對應資料的使用經驗判斷使用者是否應該執行其他步驟，以改善的完整性和品質空間對應的開頭。</span><span class="sxs-lookup"><span data-stu-id="1bb90-500">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="1bb90-501">如果使用者所掃描的環境，清除掃描體驗期間，應該提供指引。</span><span class="sxs-lookup"><span data-stu-id="1bb90-501">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="1bb90-502">裝置的影響</span><span class="sxs-lookup"><span data-stu-id="1bb90-502">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="1bb90-503"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1bb90-503"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1bb90-504"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="1bb90-504"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="1bb90-505">✔️</span><span class="sxs-lookup"><span data-stu-id="1bb90-505">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="1bb90-506">品質準則</span><span class="sxs-lookup"><span data-stu-id="1bb90-506">Quality criteria</span></span>

|  <span data-ttu-id="1bb90-507">最佳</span><span class="sxs-lookup"><span data-stu-id="1bb90-507">Best</span></span>  |  <span data-ttu-id="1bb90-508">符合</span><span class="sxs-lookup"><span data-stu-id="1bb90-508">Meets</span></span> |  <span data-ttu-id="1bb90-509">失敗</span><span class="sxs-lookup"><span data-stu-id="1bb90-509">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="1bb90-510">空間網狀結構的視覺效果會告訴使用者掃描正在進行中。</span><span class="sxs-lookup"><span data-stu-id="1bb90-510">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="1bb90-511">使用者清楚知道該如何和何時掃描啟動和停止。</span><span class="sxs-lookup"><span data-stu-id="1bb90-511">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="1bb90-512">提供空間網狀結構的視覺效果，但使用者可能不清楚知道要如何，會提供任何進度資訊。</span><span class="sxs-lookup"><span data-stu-id="1bb90-512">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="1bb90-513">網狀結構的任何視覺效果。</span><span class="sxs-lookup"><span data-stu-id="1bb90-513">No visualization of mesh.</span></span> <span data-ttu-id="1bb90-514">提供給使用者有關何處尋找或當掃描啟動/停止任何指引資訊。</span><span class="sxs-lookup"><span data-stu-id="1bb90-514">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="1bb90-515">如何測量</span><span class="sxs-lookup"><span data-stu-id="1bb90-515">How to measure</span></span>

* <span data-ttu-id="1bb90-516">在所需的空間掃描時，會指出哪裡可找到此項目，以及何時開始和停止掃描提供視覺與音訊的指引。</span><span class="sxs-lookup"><span data-stu-id="1bb90-516">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="1bb90-517">建議</span><span class="sxs-lookup"><span data-stu-id="1bb90-517">Recommendations</span></span>

* <span data-ttu-id="1bb90-518">表示在使用者附近的總磁碟區中有多少必須能夠體驗的一部分。</span><span class="sxs-lookup"><span data-stu-id="1bb90-518">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="1bb90-519">當掃瞄啟動且例如進度列指示器會停止時，便會進行通訊。</span><span class="sxs-lookup"><span data-stu-id="1bb90-519">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="1bb90-520">使用在掃描期間之網狀結構的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="1bb90-520">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="1bb90-521">提供視覺與音訊提示，可鼓勵使用者尋找並聊天室四處移動。</span><span class="sxs-lookup"><span data-stu-id="1bb90-521">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="1bb90-522">通知使用者前往改善資料的位置。</span><span class="sxs-lookup"><span data-stu-id="1bb90-522">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="1bb90-523">在許多情況下，可能是最理想的做法，告訴使用者他們需要執行 （例如查看最高限度，查看 furniture 後面），以取得必要的掃描品質。</span><span class="sxs-lookup"><span data-stu-id="1bb90-523">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="1bb90-524">資源</span><span class="sxs-lookup"><span data-stu-id="1bb90-524">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="1bb90-525">文件</span><span class="sxs-lookup"><span data-stu-id="1bb90-525">Documentation</span></span>

* [<span data-ttu-id="1bb90-526">空間位置掃描視覺效果</span><span class="sxs-lookup"><span data-stu-id="1bb90-526">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="1bb90-527">案例研究：展開 HoloLens 空間的對應的功能</span><span class="sxs-lookup"><span data-stu-id="1bb90-527">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="1bb90-528">案例研究：空間設計完善的 HoloTour</span><span class="sxs-lookup"><span data-stu-id="1bb90-528">Case study: Spatial sound design for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="1bb90-529">案例研究：在片段中建立沉浸式體驗</span><span class="sxs-lookup"><span data-stu-id="1bb90-529">Case study: Creating an immersive experience in Fragments</span></span>](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="1bb90-530">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="1bb90-530">Tools and tutorials</span></span>

* [<span data-ttu-id="1bb90-531">混合的實境工具組-UX</span><span class="sxs-lookup"><span data-stu-id="1bb90-531">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="1bb90-532">方向性指標</span><span class="sxs-lookup"><span data-stu-id="1bb90-532">Directional indicators</span></span>

<span data-ttu-id="1bb90-533">在混合的實境應用程式中，內容可能位於檢視欄位之外，或阻擋真實世界的物件。</span><span class="sxs-lookup"><span data-stu-id="1bb90-533">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="1bb90-534">設計良好的應用程式會方便使用者尋找不可見的內容。</span><span class="sxs-lookup"><span data-stu-id="1bb90-534">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="1bb90-535">方向性指標警示使用者重要的內容，並提供指引，以相對於使用者的位置內容。</span><span class="sxs-lookup"><span data-stu-id="1bb90-535">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="1bb90-536">不可見內容的指導方針可以達到這種音效的 fixit 發出器、 方向性箭號或直接的視覺提示。</span><span class="sxs-lookup"><span data-stu-id="1bb90-536">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="1bb90-537">裝置的影響</span><span class="sxs-lookup"><span data-stu-id="1bb90-537">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="1bb90-538"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1bb90-538"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1bb90-539"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="1bb90-539"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="1bb90-540">✔️</span><span class="sxs-lookup"><span data-stu-id="1bb90-540">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="1bb90-541">✔️</span><span class="sxs-lookup"><span data-stu-id="1bb90-541">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="1bb90-542">品質準則</span><span class="sxs-lookup"><span data-stu-id="1bb90-542">Quality criteria</span></span>

|  <span data-ttu-id="1bb90-543">最佳</span><span class="sxs-lookup"><span data-stu-id="1bb90-543">Best</span></span>  |  <span data-ttu-id="1bb90-544">符合</span><span class="sxs-lookup"><span data-stu-id="1bb90-544">Meets</span></span> |  <span data-ttu-id="1bb90-545">失敗</span><span class="sxs-lookup"><span data-stu-id="1bb90-545">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="1bb90-546">視覺與音訊提示直接引導使用者檢視欄位以外的相關內容。</span><span class="sxs-lookup"><span data-stu-id="1bb90-546">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="1bb90-547">箭號或某些指標，指向使用者內容的一般方向。</span><span class="sxs-lookup"><span data-stu-id="1bb90-547">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="1bb90-548">相關內容之外視野，並不佳，或沒有位置指引提供給使用者。</span><span class="sxs-lookup"><span data-stu-id="1bb90-548">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="1bb90-549">如何測量</span><span class="sxs-lookup"><span data-stu-id="1bb90-549">How to measure</span></span>

* <span data-ttu-id="1bb90-550">外部使用者的檢視相關的內容是透過視覺化及 （或） 音訊提示可探索。</span><span class="sxs-lookup"><span data-stu-id="1bb90-550">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="1bb90-551">建議</span><span class="sxs-lookup"><span data-stu-id="1bb90-551">Recommendations</span></span>

* <span data-ttu-id="1bb90-552">外部使用者的視野相關內容時，使用方向性指標和音訊提示來引導使用者的內容。</span><span class="sxs-lookup"><span data-stu-id="1bb90-552">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="1bb90-553">在許多情況下，直接的視覺輔助線是偏好透過方向性箭號。</span><span class="sxs-lookup"><span data-stu-id="1bb90-553">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="1bb90-554">方向性指標應該不會內建資料指標。</span><span class="sxs-lookup"><span data-stu-id="1bb90-554">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="1bb90-555">資源</span><span class="sxs-lookup"><span data-stu-id="1bb90-555">Resources</span></span>

* [<span data-ttu-id="1bb90-556">全像攝影框架</span><span class="sxs-lookup"><span data-stu-id="1bb90-556">Holographic frame</span></span>](holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="1bb90-557">載入資料</span><span class="sxs-lookup"><span data-stu-id="1bb90-557">Data loading</span></span>

<span data-ttu-id="1bb90-558">進度控制項為使用者提供回饋，告知正在進行長時間執行的操作。</span><span class="sxs-lookup"><span data-stu-id="1bb90-558">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="1bb90-559">它可以表示進度列指示器是可見的也可以指定等候時間可能長時，無法與應用程式互動使用者。</span><span class="sxs-lookup"><span data-stu-id="1bb90-559">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="1bb90-560">裝置的影響</span><span class="sxs-lookup"><span data-stu-id="1bb90-560">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="1bb90-561"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1bb90-561"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1bb90-562"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="1bb90-562"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="1bb90-563">✔️</span><span class="sxs-lookup"><span data-stu-id="1bb90-563">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="1bb90-564">✔️</span><span class="sxs-lookup"><span data-stu-id="1bb90-564">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="1bb90-565">品質準則</span><span class="sxs-lookup"><span data-stu-id="1bb90-565">Quality criteria</span></span>

|  <span data-ttu-id="1bb90-566">最佳</span><span class="sxs-lookup"><span data-stu-id="1bb90-566">Best</span></span>  |  <span data-ttu-id="1bb90-567">符合</span><span class="sxs-lookup"><span data-stu-id="1bb90-567">Meets</span></span> |  <span data-ttu-id="1bb90-568">失敗</span><span class="sxs-lookup"><span data-stu-id="1bb90-568">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="1bb90-569">在進度列或在任何資料載入或處理期間顯示進度環表單中的視覺指標以動畫顯示。</span><span class="sxs-lookup"><span data-stu-id="1bb90-569">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="1bb90-570">視覺指示器多少時間等候可能是提供指引。</span><span class="sxs-lookup"><span data-stu-id="1bb90-570">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="1bb90-571">載入資料進行中，但不會表示的時間等候可能是，會通知使用者。</span><span class="sxs-lookup"><span data-stu-id="1bb90-571">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="1bb90-572">沒有資料載入或處理程序耗時超過 5 秒的工作的指標。</span><span class="sxs-lookup"><span data-stu-id="1bb90-572">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="1bb90-573">如何測量</span><span class="sxs-lookup"><span data-stu-id="1bb90-573">How to measure</span></span>

* <span data-ttu-id="1bb90-574">在資料載入期間確認沒有空白狀態的時間超過 5 秒。</span><span class="sxs-lookup"><span data-stu-id="1bb90-574">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="1bb90-575">建議</span><span class="sxs-lookup"><span data-stu-id="1bb90-575">Recommendations</span></span>

* <span data-ttu-id="1bb90-576">提供進度顯示在任何情況下，當使用者可能會感覺此應用程式已停止，或當機資料載入動畫。</span><span class="sxs-lookup"><span data-stu-id="1bb90-576">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="1bb90-577">合理的經驗法則是任何 '載入' 的活動，花費時間超過 5 秒。</span><span class="sxs-lookup"><span data-stu-id="1bb90-577">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="1bb90-578">資源</span><span class="sxs-lookup"><span data-stu-id="1bb90-578">Resources</span></span>

* [<span data-ttu-id="1bb90-579">顯示進度</span><span class="sxs-lookup"><span data-stu-id="1bb90-579">Displaying progress</span></span>](progress.md)
