---
title: 應用程式品質準則
description: 本檔說明影響混合現實應用程式品質的最大因素。
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: 應用程式品質準則, 混合現實, 混合現實應用程式
ms.openlocfilehash: 8e635585c0981d81bf71fb5577232af28f2a0fdd
ms.sourcegitcommit: 150d258a23130026c8792da383a3993657841fb4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024491"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="b4822-104">應用程式品質準則</span><span class="sxs-lookup"><span data-stu-id="b4822-104">App quality criteria</span></span>

<span data-ttu-id="b4822-105">本檔說明影響混合現實應用程式品質的最大因素。</span><span class="sxs-lookup"><span data-stu-id="b4822-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="b4822-106">針對每個因素, 會提供下列資訊</span><span class="sxs-lookup"><span data-stu-id="b4822-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="b4822-107">總覽–「品質因素」和「重要性」的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="b4822-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="b4822-108">裝置影響-受影響的 Windows 混合現實裝置類型。</span><span class="sxs-lookup"><span data-stu-id="b4822-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="b4822-109">品質準則–如何評估品質因素。</span><span class="sxs-lookup"><span data-stu-id="b4822-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="b4822-110">如何測量–測量 (或體驗) 問題的方法。</span><span class="sxs-lookup"><span data-stu-id="b4822-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="b4822-111">建議事項–提供更佳使用者體驗的方法摘要。</span><span class="sxs-lookup"><span data-stu-id="b4822-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="b4822-112">資源-相關的開發人員和設計資源, 有助於建立更佳的應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="b4822-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="b4822-113">畫面播放速率</span><span class="sxs-lookup"><span data-stu-id="b4822-113">Frame rate</span></span>

<span data-ttu-id="b4822-114">畫面播放速率是全息和使用者緩和的第一要件。</span><span class="sxs-lookup"><span data-stu-id="b4822-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="b4822-115">低於建議目標的畫面播放速率可能會使全息影像顯得抖動、對體驗的 believability 造成負面影響, 並可能造成眼睛疲勞。</span><span class="sxs-lookup"><span data-stu-id="b4822-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="b4822-116">您在 Windows Mixed Reality 沉浸式耳機上體驗的目標畫面播放速率會是60Hz 或 90Hz, 視您想要支援的 Windows Mixed Reality 相容電腦而定。</span><span class="sxs-lookup"><span data-stu-id="b4822-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="b4822-117">若是 HoloLens, 目標畫面播放速率為60Hz。</span><span class="sxs-lookup"><span data-stu-id="b4822-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="b4822-118">裝置影響</span><span class="sxs-lookup"><span data-stu-id="b4822-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b4822-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4822-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b4822-120"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4822-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b4822-121">✔️</span><span class="sxs-lookup"><span data-stu-id="b4822-121">✔️</span></span></td>
        <td><span data-ttu-id="b4822-122">✔️</span><span class="sxs-lookup"><span data-stu-id="b4822-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="b4822-123">品質準則</span><span class="sxs-lookup"><span data-stu-id="b4822-123">Quality criteria</span></span>

|  <span data-ttu-id="b4822-124">效果</span><span class="sxs-lookup"><span data-stu-id="b4822-124">Best</span></span>  |  <span data-ttu-id="b4822-125">遇到</span><span class="sxs-lookup"><span data-stu-id="b4822-125">Meets</span></span> |  <span data-ttu-id="b4822-126">無法</span><span class="sxs-lookup"><span data-stu-id="b4822-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="b4822-127">應用程式一致符合目標裝置的每秒畫面格數 (FPS) 目標:HoloLens 上的 60fps;Ultra 電腦上的 90fps;和60fps 在主流電腦上。</span><span class="sxs-lookup"><span data-stu-id="b4822-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="b4822-128">應用程式的斷斷續續畫面不會阻礙核心體驗;或 FPS 一致地低於所需的目標, 但不會妨礙應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="b4822-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="b4822-129">應用程式平均每十秒或更短的畫面播放速率下降。</span><span class="sxs-lookup"><span data-stu-id="b4822-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="b4822-130">如何測量</span><span class="sxs-lookup"><span data-stu-id="b4822-130">How to measure</span></span>

* <span data-ttu-id="b4822-131">[Windows 裝置入口網站](using-the-windows-device-portal.md#system-performance)會在 [系統效能] 下提供即時畫面播放速率圖表。</span><span class="sxs-lookup"><span data-stu-id="b4822-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="b4822-132">若是開發的偵錯工具, 請在應用程式中新增 [畫面播放速率] 診斷計數器。</span><span class="sxs-lookup"><span data-stu-id="b4822-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="b4822-133">請參閱範例計數器的資源。</span><span class="sxs-lookup"><span data-stu-id="b4822-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="b4822-134">當應用程式正在執行時, 畫面播放速率下降可能會在裝置上經歷, 方法是將您的 head 從側邊移至一邊。</span><span class="sxs-lookup"><span data-stu-id="b4822-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="b4822-135">如果全像投影顯示非預期的抖動移動, 則低畫面播放速率或穩定性平面可能是原因。</span><span class="sxs-lookup"><span data-stu-id="b4822-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="b4822-136">建議</span><span class="sxs-lookup"><span data-stu-id="b4822-136">Recommendations</span></span>

* <span data-ttu-id="b4822-137">在開發工作開始時新增畫面播放速率計數器。</span><span class="sxs-lookup"><span data-stu-id="b4822-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="b4822-138">會評估產生下降畫面播放速率的變更, 並適當地解決為效能錯誤。</span><span class="sxs-lookup"><span data-stu-id="b4822-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="b4822-139">資源</span><span class="sxs-lookup"><span data-stu-id="b4822-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="b4822-140">文件</span><span class="sxs-lookup"><span data-stu-id="b4822-140">Documentation</span></span>

* [<span data-ttu-id="b4822-141">瞭解混合現實的效能</span><span class="sxs-lookup"><span data-stu-id="b4822-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="b4822-142">全息的穩定性和畫面播放速率</span><span class="sxs-lookup"><span data-stu-id="b4822-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="b4822-143">資產效能預算</span><span class="sxs-lookup"><span data-stu-id="b4822-143">Asset performance budget</span></span>](asset-creation-process.md)
* [<span data-ttu-id="b4822-144">對 Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="b4822-144">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="b4822-145">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="b4822-145">Tools and tutorials</span></span>

* [<span data-ttu-id="b4822-146">MRToolkit, FPS 計數器顯示</span><span class="sxs-lookup"><span data-stu-id="b4822-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="b4822-147">MRToolkit、著色器</span><span class="sxs-lookup"><span data-stu-id="b4822-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="b4822-148">外部參考</span><span class="sxs-lookup"><span data-stu-id="b4822-148">External references</span></span>

* [<span data-ttu-id="b4822-149">Unity, 將行動應用程式優化</span><span class="sxs-lookup"><span data-stu-id="b4822-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="b4822-150">全息影像穩定性</span><span class="sxs-lookup"><span data-stu-id="b4822-150">Hologram stability</span></span>

<span data-ttu-id="b4822-151">穩定的全息影像會提高應用程式的可用性和 believability, 並為使用者建立更舒適的觀看體驗。</span><span class="sxs-lookup"><span data-stu-id="b4822-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="b4822-152">全像投影穩定性的品質是良好應用程式開發的結果, 以及裝置瞭解 (追蹤) 其環境的能力。</span><span class="sxs-lookup"><span data-stu-id="b4822-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="b4822-153">雖然畫面播放速率是穩定性的第一個要件, 但其他因素可能會影響穩定性, 包括:</span><span class="sxs-lookup"><span data-stu-id="b4822-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="b4822-154">使用穩定平面</span><span class="sxs-lookup"><span data-stu-id="b4822-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="b4822-155">距離空間錨點</span><span class="sxs-lookup"><span data-stu-id="b4822-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="b4822-156">修訂</span><span class="sxs-lookup"><span data-stu-id="b4822-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="b4822-157">裝置影響</span><span class="sxs-lookup"><span data-stu-id="b4822-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b4822-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4822-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b4822-159"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4822-159"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b4822-160">✔️</span><span class="sxs-lookup"><span data-stu-id="b4822-160">✔️</span></span></td>
        <td><span data-ttu-id="b4822-161">❌</span><span class="sxs-lookup"><span data-stu-id="b4822-161">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="b4822-162">品質準則</span><span class="sxs-lookup"><span data-stu-id="b4822-162">Quality criteria</span></span>

|  <span data-ttu-id="b4822-163">效果</span><span class="sxs-lookup"><span data-stu-id="b4822-163">Best</span></span>  |  <span data-ttu-id="b4822-164">遇到</span><span class="sxs-lookup"><span data-stu-id="b4822-164">Meets</span></span> |  <span data-ttu-id="b4822-165">無法</span><span class="sxs-lookup"><span data-stu-id="b4822-165">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="b4822-166">全息影像一致地顯示穩定。</span><span class="sxs-lookup"><span data-stu-id="b4822-166">Holograms consistently appear stable.</span></span> | <span data-ttu-id="b4822-167">次要內容表現出非預期的移動;或非預期的移動不會妨礙整體應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="b4822-167">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="b4822-168">框架中的主要內容展現了非預期的移動。</span><span class="sxs-lookup"><span data-stu-id="b4822-168">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="b4822-169">如何測量</span><span class="sxs-lookup"><span data-stu-id="b4822-169">How to measure</span></span>

<span data-ttu-id="b4822-170">在戴上裝置並觀看體驗時:</span><span class="sxs-lookup"><span data-stu-id="b4822-170">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="b4822-171">將您的 head 從側邊移到一邊, 如果全息影像顯示非預期的移動, 則不正確的畫面播放速率, 或穩定性平面與焦點平面的不適當對齊可能是原因。</span><span class="sxs-lookup"><span data-stu-id="b4822-171">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="b4822-172">四處移動全息影像和環境, 尋找像是 [泳道] 和 [jumpiness] 的行為。</span><span class="sxs-lookup"><span data-stu-id="b4822-172">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="b4822-173">這種動作可能是因為裝置未追蹤環境, 或與空間錨點的距離所造成。</span><span class="sxs-lookup"><span data-stu-id="b4822-173">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="b4822-174">如果框架中有大型或多個全息影像, 請觀察各種深度的全息影像行為, 同時將您的頭部位置從側邊移至一邊, 如果 shakiness 出現, 這可能是穩定平面所造成。</span><span class="sxs-lookup"><span data-stu-id="b4822-174">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recomendations"></a><span data-ttu-id="b4822-175">建議</span><span class="sxs-lookup"><span data-stu-id="b4822-175">Recomendations</span></span>

* <span data-ttu-id="b4822-176">在開發工作開始時新增 [畫面播放速率] 計數器。</span><span class="sxs-lookup"><span data-stu-id="b4822-176">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="b4822-177">使用穩定平面。</span><span class="sxs-lookup"><span data-stu-id="b4822-177">Use the stabilization plane.</span></span>
* <span data-ttu-id="b4822-178">一律在其錨點的3個計量中轉譯錨定的全息影像。</span><span class="sxs-lookup"><span data-stu-id="b4822-178">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="b4822-179">請確定您的環境已設定適當的追蹤。</span><span class="sxs-lookup"><span data-stu-id="b4822-179">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="b4822-180">設計您的體驗, 以避免框架內各種焦點深度層級的全息影像。</span><span class="sxs-lookup"><span data-stu-id="b4822-180">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="b4822-181">資源</span><span class="sxs-lookup"><span data-stu-id="b4822-181">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="b4822-182">文件</span><span class="sxs-lookup"><span data-stu-id="b4822-182">Documentation</span></span>

* [<span data-ttu-id="b4822-183">全息的穩定性和畫面播放速率</span><span class="sxs-lookup"><span data-stu-id="b4822-183">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="b4822-184">使用穩定平面的案例研究</span><span class="sxs-lookup"><span data-stu-id="b4822-184">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="b4822-185">瞭解混合現實的效能</span><span class="sxs-lookup"><span data-stu-id="b4822-185">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="b4822-186">對 Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="b4822-186">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="b4822-187">空間錨點</span><span class="sxs-lookup"><span data-stu-id="b4822-187">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="b4822-188">處理追蹤錯誤</span><span class="sxs-lookup"><span data-stu-id="b4822-188">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="b4822-189">固定的參考框架</span><span class="sxs-lookup"><span data-stu-id="b4822-189">Stationary frame of reference</span></span>](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="b4822-190">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="b4822-190">Tools and tutorials</span></span>

* [<span data-ttu-id="b4822-191">MR 配套套件, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="b4822-191">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="b4822-192">實際表面上的全息影像位置</span><span class="sxs-lookup"><span data-stu-id="b4822-192">Holograms position on real surfaces</span></span>

<span data-ttu-id="b4822-193">具有實體物件的全息影像不一致 (如果要放在彼此之間的關聯性), 可以清楚指出全息和真實世界的非聯合。</span><span class="sxs-lookup"><span data-stu-id="b4822-193">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="b4822-194">放置的精確度應該相對於案例的需求;例如, 一般介面位置可以使用空間對應, 但更精確的放置需要使用標記和校正。</span><span class="sxs-lookup"><span data-stu-id="b4822-194">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="b4822-195">裝置影響</span><span class="sxs-lookup"><span data-stu-id="b4822-195">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b4822-196"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4822-196"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b4822-197"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4822-197"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b4822-198">✔️</span><span class="sxs-lookup"><span data-stu-id="b4822-198">✔️</span></span></td>
        <td><span data-ttu-id="b4822-199">❌</span><span class="sxs-lookup"><span data-stu-id="b4822-199">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="b4822-200">品質準則</span><span class="sxs-lookup"><span data-stu-id="b4822-200">Quality criteria</span></span>

|  <span data-ttu-id="b4822-201">效果</span><span class="sxs-lookup"><span data-stu-id="b4822-201">Best</span></span>  |  <span data-ttu-id="b4822-202">遇到</span><span class="sxs-lookup"><span data-stu-id="b4822-202">Meets</span></span> |  <span data-ttu-id="b4822-203">無法</span><span class="sxs-lookup"><span data-stu-id="b4822-203">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="b4822-204">全像投影對齊表面, 通常是以釐米到英寸的範圍。</span><span class="sxs-lookup"><span data-stu-id="b4822-204">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="b4822-205">如果需要更多的精確度, 應用程式應該為所需的應用程式規格中的共同作業提供有效率的方式。</span><span class="sxs-lookup"><span data-stu-id="b4822-205">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="b4822-206">NA</span><span class="sxs-lookup"><span data-stu-id="b4822-206">NA</span></span> | <span data-ttu-id="b4822-207">全息影像會與實體目標物件顯示不對齊, 方法是中斷表面平面, 或顯示為遠離表面。</span><span class="sxs-lookup"><span data-stu-id="b4822-207">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="b4822-208">如果需要精確度, 則全息影像應符合案例的近接規格。</span><span class="sxs-lookup"><span data-stu-id="b4822-208">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="b4822-209">如何測量</span><span class="sxs-lookup"><span data-stu-id="b4822-209">How to measure</span></span>

* <span data-ttu-id="b4822-210">放在空間地圖上的全息影像應該不會明顯地浮動在表面上方或下方。</span><span class="sxs-lookup"><span data-stu-id="b4822-210">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="b4822-211">需要精確放置的全息影像應具有某種形式的標記和校正系統, 以精確因應案例的需求。</span><span class="sxs-lookup"><span data-stu-id="b4822-211">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="b4822-212">建議</span><span class="sxs-lookup"><span data-stu-id="b4822-212">Recommendations</span></span>

* <span data-ttu-id="b4822-213">當不需要有效位數時, 空間對應適用于將物件放在介面上。</span><span class="sxs-lookup"><span data-stu-id="b4822-213">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="b4822-214">為了達到最佳精確度, 請使用標記或海報來設定全息和 Xbox 控制器 (或某種手動對齊機制), 以進行最後的校正。</span><span class="sxs-lookup"><span data-stu-id="b4822-214">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="b4822-215">請考慮將多大的全息影像分解成邏輯部分, 並將每個部分對齊介面。</span><span class="sxs-lookup"><span data-stu-id="b4822-215">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="b4822-216">不當設定的 interpupilary 距離 (IPD) 也會影響全息影像對齊。</span><span class="sxs-lookup"><span data-stu-id="b4822-216">Improperly set interpupilary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="b4822-217">請一律將 HoloLens 設定為使用者的 IPD。</span><span class="sxs-lookup"><span data-stu-id="b4822-217">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="b4822-218">資源</span><span class="sxs-lookup"><span data-stu-id="b4822-218">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="b4822-219">文件</span><span class="sxs-lookup"><span data-stu-id="b4822-219">Documentation</span></span>

* [<span data-ttu-id="b4822-220">空間對應位置</span><span class="sxs-lookup"><span data-stu-id="b4822-220">Spatial mapping placement</span></span>](spatial-mapping.md#placement)
* [<span data-ttu-id="b4822-221">房間掃描程式</span><span class="sxs-lookup"><span data-stu-id="b4822-221">Room scanning process</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="b4822-222">空間錨點最佳做法</span><span class="sxs-lookup"><span data-stu-id="b4822-222">Spatial anchors best practices</span></span>](spatial-anchors.md#best-practices)
* [<span data-ttu-id="b4822-223">處理追蹤錯誤</span><span class="sxs-lookup"><span data-stu-id="b4822-223">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="b4822-224">Unity 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="b4822-224">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="b4822-225">Vuforia 開發總覽</span><span class="sxs-lookup"><span data-stu-id="b4822-225">Vuforia development overview</span></span>](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="b4822-226">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="b4822-226">Tools and tutorials</span></span>

* [<span data-ttu-id="b4822-227">MR Spatial 230：空間對應</span><span class="sxs-lookup"><span data-stu-id="b4822-227">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="b4822-228">MR 工具組, 空間對應程式庫</span><span class="sxs-lookup"><span data-stu-id="b4822-228">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="b4822-229">MR 配套套件, 海報校正範例</span><span class="sxs-lookup"><span data-stu-id="b4822-229">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="b4822-230">MR 配套套件, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="b4822-230">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="b4822-231">外部參考</span><span class="sxs-lookup"><span data-stu-id="b4822-231">External references</span></span>

* [<span data-ttu-id="b4822-232">Lowes 案例研究, 精確度對齊</span><span class="sxs-lookup"><span data-stu-id="b4822-232">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="b4822-233">觀賞舒適的區域</span><span class="sxs-lookup"><span data-stu-id="b4822-233">Viewing zone of comfort</span></span>

<span data-ttu-id="b4822-234">應用程式開發人員可以在各種深度放置內容和全息影像, 以控制使用者的眼睛。</span><span class="sxs-lookup"><span data-stu-id="b4822-234">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="b4822-235">戴 HoloLens 的使用者一律會容納到 2.0 m, 以維護清楚的影像, 因為 HoloLens 顯示器的固定距離使用者遠接近 2.0 m。</span><span class="sxs-lookup"><span data-stu-id="b4822-235">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="b4822-236">不當的內容深度可能會導致視覺 discomfort 或疲勞。</span><span class="sxs-lookup"><span data-stu-id="b4822-236">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="b4822-237">裝置影響</span><span class="sxs-lookup"><span data-stu-id="b4822-237">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b4822-238"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4822-238"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b4822-239"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4822-239"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b4822-240">✔️</span><span class="sxs-lookup"><span data-stu-id="b4822-240">✔️</span></span></td>
        <td><span data-ttu-id="b4822-241">❌</span><span class="sxs-lookup"><span data-stu-id="b4822-241">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="b4822-242">品質準則</span><span class="sxs-lookup"><span data-stu-id="b4822-242">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="b4822-243">效果</span><span class="sxs-lookup"><span data-stu-id="b4822-243">Best</span></span> </td><td><ul>
<li><span data-ttu-id="b4822-244">將內容放在2m。</span><span class="sxs-lookup"><span data-stu-id="b4822-244">Place content at 2m.</span></span></li><li><span data-ttu-id="b4822-245">當您無法避免在2m 時放置全息影像, 而且無法避免聚合與住宿之間的衝突時, 全像投影位置的最佳區域會介於 1.25 m 到5m 之間。</span><span class="sxs-lookup"><span data-stu-id="b4822-245">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="b4822-246">在每個案例中, 設計人員都應該結構內容, 以鼓勵使用者離開 1 + m (例如調整內容大小和預設位置參數)。</span><span class="sxs-lookup"><span data-stu-id="b4822-246">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="b4822-247">除非案例特別不需要, 否則裁剪平面應該使用從1百萬開始的 fadeout 來執行。</span><span class="sxs-lookup"><span data-stu-id="b4822-247">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="b4822-248">如果需要更深入觀察 motionless 的全像投影, 則內容不應該比50cm 更接近。</span><span class="sxs-lookup"><span data-stu-id="b4822-248">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="b4822-249">遇到</span><span class="sxs-lookup"><span data-stu-id="b4822-249">Meets</span></span></td><td> <span data-ttu-id="b4822-250">內容位於觀看和動作指引內, 但不適當地使用或不使用裁剪平面。</span><span class="sxs-lookup"><span data-stu-id="b4822-250">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b4822-251">無法</span><span class="sxs-lookup"><span data-stu-id="b4822-251">Fail</span></span> </td><td> <span data-ttu-id="b4822-252">內容的顯示太接近 (通常&lt;是 1.25 m, &lt;或50cm 用於需要進一步觀察的靜止全息影像)。</span><span class="sxs-lookup"><span data-stu-id="b4822-252">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="b4822-253">如何測量</span><span class="sxs-lookup"><span data-stu-id="b4822-253">How to measure</span></span>

* <span data-ttu-id="b4822-254">內容通常應該2m 在外, 但不能接近1.25 或高於5m。</span><span class="sxs-lookup"><span data-stu-id="b4822-254">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="b4822-255">除了少數例外狀況之外, HoloLens 裁剪轉譯距離應該設定為. 85CM, fadeout 的內容是從1m 開始。</span><span class="sxs-lookup"><span data-stu-id="b4822-255">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="b4822-256">處理內容, 並記下裁剪平面效果。</span><span class="sxs-lookup"><span data-stu-id="b4822-256">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="b4822-257">固定的內容應該不會接近50cm 的距離。</span><span class="sxs-lookup"><span data-stu-id="b4822-257">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="b4822-258">建議</span><span class="sxs-lookup"><span data-stu-id="b4822-258">Recommendations</span></span>

* <span data-ttu-id="b4822-259">設計內容以取得2m 的最佳觀賞距離。</span><span class="sxs-lookup"><span data-stu-id="b4822-259">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="b4822-260">使用從1m 開始的 fadeout 內容, 將裁剪轉譯距離設定為85cm。</span><span class="sxs-lookup"><span data-stu-id="b4822-260">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="b4822-261">對於需要進一步觀賞的靜止全息影像, 裁剪平面應該不會接近 30cm, 而 fadeout 應從裁剪平面開始至少10cm。</span><span class="sxs-lookup"><span data-stu-id="b4822-261">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="b4822-262">資源</span><span class="sxs-lookup"><span data-stu-id="b4822-262">Resources</span></span>

* [<span data-ttu-id="b4822-263">呈現距離</span><span class="sxs-lookup"><span data-stu-id="b4822-263">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="b4822-264">Unity 中的焦點</span><span class="sxs-lookup"><span data-stu-id="b4822-264">Focus point in Unity</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="b4822-265">使用 scale 進行實驗</span><span class="sxs-lookup"><span data-stu-id="b4822-265">Experimenting with scale</span></span>](scale.md#experimenting-with-scale)
* [<span data-ttu-id="b4822-266">文字、建議的字型大小</span><span class="sxs-lookup"><span data-stu-id="b4822-266">Text, Recommended font size</span></span>](typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="b4822-267">深度切換</span><span class="sxs-lookup"><span data-stu-id="b4822-267">Depth switching</span></span>

<span data-ttu-id="b4822-268">無論觀賞的緩和問題區域為何, 使用者需要經常或快速地在接近和遠的焦點物件之間切換 (包括全息影像和真實世界內容), 可能會導致 oculomotor 疲勞和一般 discomfort。</span><span class="sxs-lookup"><span data-stu-id="b4822-268">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="b4822-269">裝置影響</span><span class="sxs-lookup"><span data-stu-id="b4822-269">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b4822-270"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4822-270"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b4822-271"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4822-271"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b4822-272">✔️</span><span class="sxs-lookup"><span data-stu-id="b4822-272">✔️</span></span></td>
        <td><span data-ttu-id="b4822-273">✔️</span><span class="sxs-lookup"><span data-stu-id="b4822-273">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="b4822-274">品質準則</span><span class="sxs-lookup"><span data-stu-id="b4822-274">Quality criteria</span></span>

|  <span data-ttu-id="b4822-275">效果</span><span class="sxs-lookup"><span data-stu-id="b4822-275">Best</span></span>  |  <span data-ttu-id="b4822-276">遇到</span><span class="sxs-lookup"><span data-stu-id="b4822-276">Meets</span></span> |  <span data-ttu-id="b4822-277">無法</span><span class="sxs-lookup"><span data-stu-id="b4822-277">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="b4822-278">限制或自然深度切換, 這不會造成使用者 unnaturally 將。</span><span class="sxs-lookup"><span data-stu-id="b4822-278">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="b4822-279">自然深度切換: 這是核心並設計成應用程式體驗, 或是因非預期的真實世界內容而造成的「突然深度」切換。</span><span class="sxs-lookup"><span data-stu-id="b4822-279">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="b4822-280">一致的深度切換, 或不是必要或不是應用程式體驗核心的深入深度切換。</span><span class="sxs-lookup"><span data-stu-id="b4822-280">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="b4822-281">如何測量</span><span class="sxs-lookup"><span data-stu-id="b4822-281">How to measure</span></span>

* <span data-ttu-id="b4822-282">如果應用程式需要使用者一致且/或突然變更深度焦點, 則會有深度切換問題。</span><span class="sxs-lookup"><span data-stu-id="b4822-282">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="b4822-283">建議</span><span class="sxs-lookup"><span data-stu-id="b4822-283">Recommendations</span></span>

* <span data-ttu-id="b4822-284">將主要內容保持在一致的焦點平面上, 並確保穩定平面符合焦點平面。</span><span class="sxs-lookup"><span data-stu-id="b4822-284">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="b4822-285">這可減輕 oculomotor 的疲勞和非預期的全息影像移動。</span><span class="sxs-lookup"><span data-stu-id="b4822-285">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="b4822-286">資源</span><span class="sxs-lookup"><span data-stu-id="b4822-286">Resources</span></span>

* [<span data-ttu-id="b4822-287">呈現距離</span><span class="sxs-lookup"><span data-stu-id="b4822-287">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="b4822-288">Unity 中的焦點</span><span class="sxs-lookup"><span data-stu-id="b4822-288">Focus point in Unity</span></span>](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="b4822-289">使用空間音效</span><span class="sxs-lookup"><span data-stu-id="b4822-289">Use of spatial sound</span></span>

<span data-ttu-id="b4822-290">在 Windows Mixed Reality 中, 音訊引擎提供混合現實體驗的以聽覺方式元件, 方法是使用方向、距離和環境模擬來模擬3D 音效。</span><span class="sxs-lookup"><span data-stu-id="b4822-290">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="b4822-291">在應用程式中使用空間音效, 可以讓開發人員 convincingly 在使用者周圍, 以3維空間 (球體) 來放置聲音。</span><span class="sxs-lookup"><span data-stu-id="b4822-291">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="b4822-292">這些聽起來好像是來自實際的實體物件, 或是使用者周圍的混合現實全息。</span><span class="sxs-lookup"><span data-stu-id="b4822-292">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="b4822-293">空間音效是強大的工具, 可在混合現實應用程式中進行深度、協助工具及 UX 設計。</span><span class="sxs-lookup"><span data-stu-id="b4822-293">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="b4822-294">裝置影響</span><span class="sxs-lookup"><span data-stu-id="b4822-294">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b4822-295"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4822-295"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b4822-296"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4822-296"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b4822-297">✔️</span><span class="sxs-lookup"><span data-stu-id="b4822-297">✔️</span></span></td>
        <td><span data-ttu-id="b4822-298">✔️</span><span class="sxs-lookup"><span data-stu-id="b4822-298">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="b4822-299">品質準則</span><span class="sxs-lookup"><span data-stu-id="b4822-299">Quality criteria</span></span>

|  <span data-ttu-id="b4822-300">效果</span><span class="sxs-lookup"><span data-stu-id="b4822-300">Best</span></span>  |  <span data-ttu-id="b4822-301">遇到</span><span class="sxs-lookup"><span data-stu-id="b4822-301">Meets</span></span> |  <span data-ttu-id="b4822-302">無法</span><span class="sxs-lookup"><span data-stu-id="b4822-302">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="b4822-303">音效會以邏輯方式 hrtf, 而 UX 會適當地使用音效來協助物件探索和使用者意見反應。</span><span class="sxs-lookup"><span data-stu-id="b4822-303">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="b4822-304">音效是自然且與物件相關, 並會在案例中正規化。</span><span class="sxs-lookup"><span data-stu-id="b4822-304">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="b4822-305">空間音訊會適當地用於 believability, 但缺少以協助使用者提供意見反應和發現。</span><span class="sxs-lookup"><span data-stu-id="b4822-305">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="b4822-306">音效不會如預期般 hrtf, 也不會有聲音可協助使用者在 UX 中。</span><span class="sxs-lookup"><span data-stu-id="b4822-306">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="b4822-307">或在案例的設計中未考慮或使用空間音訊。</span><span class="sxs-lookup"><span data-stu-id="b4822-307">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="b4822-308">如何測量</span><span class="sxs-lookup"><span data-stu-id="b4822-308">How to measure</span></span>

* <span data-ttu-id="b4822-309">一般情況下, 相關的音效應該從目標的全息影像發出 (例如, 從全像攝影狗的吠聲)。</span><span class="sxs-lookup"><span data-stu-id="b4822-309">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="b4822-310">在整個 UX 中都應該使用音效提示, 以協助使用者對全像攝影框架以外的動作提供意見反應或認知。</span><span class="sxs-lookup"><span data-stu-id="b4822-310">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="b4822-311">建議</span><span class="sxs-lookup"><span data-stu-id="b4822-311">Recommendations</span></span>

* <span data-ttu-id="b4822-312">使用空間音訊來協助物件探索和使用者介面。</span><span class="sxs-lookup"><span data-stu-id="b4822-312">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="b4822-313">真實音效的效果優於合成或非自然音效。</span><span class="sxs-lookup"><span data-stu-id="b4822-313">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="b4822-314">大部分的音效都應該 hrtf。</span><span class="sxs-lookup"><span data-stu-id="b4822-314">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="b4822-315">避免隱藏的發射器。</span><span class="sxs-lookup"><span data-stu-id="b4822-315">Avoid invisible emitters.</span></span>
* <span data-ttu-id="b4822-316">避免空間遮罩。</span><span class="sxs-lookup"><span data-stu-id="b4822-316">Avoid spatial masking.</span></span>
* <span data-ttu-id="b4822-317">標準化所有聲音。</span><span class="sxs-lookup"><span data-stu-id="b4822-317">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="b4822-318">資源</span><span class="sxs-lookup"><span data-stu-id="b4822-318">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="b4822-319">文件</span><span class="sxs-lookup"><span data-stu-id="b4822-319">Documentation</span></span>

* [<span data-ttu-id="b4822-320">空間音效</span><span class="sxs-lookup"><span data-stu-id="b4822-320">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="b4822-321">空間音效設計</span><span class="sxs-lookup"><span data-stu-id="b4822-321">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="b4822-322">Unity 中的空間音效</span><span class="sxs-lookup"><span data-stu-id="b4822-322">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="b4822-323">案例研究, HoloTour 的空間音效</span><span class="sxs-lookup"><span data-stu-id="b4822-323">Case study, Spatial sound for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="b4822-324">案例研究, 使用 RoboRaid 中的空間音效</span><span class="sxs-lookup"><span data-stu-id="b4822-324">Case study, Using spatial sound in RoboRaid</span></span>](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="b4822-325">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="b4822-325">Tools and tutorials</span></span>

* [<span data-ttu-id="b4822-326">MR Spatial 220：空間音效</span><span class="sxs-lookup"><span data-stu-id="b4822-326">MR Spatial 220: Spatial sound</span></span>](holograms-220.md)
* [<span data-ttu-id="b4822-327">MRToolkit, 空間音訊</span><span class="sxs-lookup"><span data-stu-id="b4822-327">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="b4822-328">專注于全像攝影框架 (FOV) 界限</span><span class="sxs-lookup"><span data-stu-id="b4822-328">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="b4822-329">設計良好的使用者體驗, 可以建立和維護虛擬環境的實用內容, 以延伸使用者。</span><span class="sxs-lookup"><span data-stu-id="b4822-329">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="b4822-330">緩和 FOV 界限的效果牽涉到內容規模和內容的精心設計, 使用空間音訊、指引系統和使用者的位置。</span><span class="sxs-lookup"><span data-stu-id="b4822-330">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="b4822-331">如果正確, 使用者會覺得 FOV 界限不會受到影響, 同時具備舒適的應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="b4822-331">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="b4822-332">裝置影響</span><span class="sxs-lookup"><span data-stu-id="b4822-332">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b4822-333"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4822-333"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b4822-334"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4822-334"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b4822-335">✔️</span><span class="sxs-lookup"><span data-stu-id="b4822-335">✔️</span></span></td>
        <td><span data-ttu-id="b4822-336">❌</span><span class="sxs-lookup"><span data-stu-id="b4822-336">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="b4822-337">品質準則</span><span class="sxs-lookup"><span data-stu-id="b4822-337">Quality criteria</span></span>

|  <span data-ttu-id="b4822-338">效果</span><span class="sxs-lookup"><span data-stu-id="b4822-338">Best</span></span>  |  <span data-ttu-id="b4822-339">遇到</span><span class="sxs-lookup"><span data-stu-id="b4822-339">Meets</span></span> |  <span data-ttu-id="b4822-340">無法</span><span class="sxs-lookup"><span data-stu-id="b4822-340">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="b4822-341">使用者絕對不會失去內容, 而且也很樂意進行觀看。</span><span class="sxs-lookup"><span data-stu-id="b4822-341">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="b4822-342">內容協助是針對大型物件所提供。</span><span class="sxs-lookup"><span data-stu-id="b4822-342">Context assistance is provided for large objects.</span></span> <span data-ttu-id="b4822-343">探索和流覽指引是針對框架外的物件所提供。</span><span class="sxs-lookup"><span data-stu-id="b4822-343">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="b4822-344">在一般情況下, 動態影像的動作設計和縮放比例適用于熟悉的觀賞體驗。</span><span class="sxs-lookup"><span data-stu-id="b4822-344">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="b4822-345">使用者絕對不會失去內容, 但是在有限的情況下可能需要額外的頸部動作。</span><span class="sxs-lookup"><span data-stu-id="b4822-345">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="b4822-346">在有限的情況下, 調整會導致全息影像中斷垂直或水準框架, 而導致一些頸部動作來觀看全息影像。</span><span class="sxs-lookup"><span data-stu-id="b4822-346">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="b4822-347">使用者可能會遺失內容和 (或) 一致的頸部動作, 以查看全息影像。</span><span class="sxs-lookup"><span data-stu-id="b4822-347">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="b4822-348">大型的全像攝影物件沒有任何內容指引、在沒有發現性指引的框架外移動物件很容易遺失, 或高度的全像投影需要週期性頸部動作來觀看。</span><span class="sxs-lookup"><span data-stu-id="b4822-348">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="b4822-349">如何測量</span><span class="sxs-lookup"><span data-stu-id="b4822-349">How to measure</span></span>

* <span data-ttu-id="b4822-350">(大型) 全息的內容會因為在界限裁剪而遺失或無法瞭解。</span><span class="sxs-lookup"><span data-stu-id="b4822-350">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="b4822-351">因為缺乏注意的總監, 或是快速移出全像攝影框架的內容, 所以很難找到全息型的位置。</span><span class="sxs-lookup"><span data-stu-id="b4822-351">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="b4822-352">案例需要定期和重複的頭運動, 才能完全看到全像疲勞的全息影像。</span><span class="sxs-lookup"><span data-stu-id="b4822-352">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="b4822-353">建議</span><span class="sxs-lookup"><span data-stu-id="b4822-353">Recommendations</span></span>

* <span data-ttu-id="b4822-354">以符合 FOV 的小型物件開始體驗, 然後以視覺提示轉換成較大的版本。</span><span class="sxs-lookup"><span data-stu-id="b4822-354">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="b4822-355">使用空間音訊和注意總監, 協助使用者尋找 FOV 外的內容。</span><span class="sxs-lookup"><span data-stu-id="b4822-355">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="b4822-356">盡可能避免以垂直方式裁剪 FOV 的全息影像。</span><span class="sxs-lookup"><span data-stu-id="b4822-356">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="b4822-357">提供使用者應用程式內的指引, 以取得最佳的流覽位置。</span><span class="sxs-lookup"><span data-stu-id="b4822-357">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="b4822-358">資源</span><span class="sxs-lookup"><span data-stu-id="b4822-358">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="b4822-359">文件</span><span class="sxs-lookup"><span data-stu-id="b4822-359">Documentation</span></span>

* [<span data-ttu-id="b4822-360">全像攝影框架</span><span class="sxs-lookup"><span data-stu-id="b4822-360">Holographic frame</span></span>](holographic-frame.md)
* [<span data-ttu-id="b4822-361">案例研究, HoloStudio UI 和互動設計學習</span><span class="sxs-lookup"><span data-stu-id="b4822-361">Case Study, HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="b4822-362">物件和環境的規模</span><span class="sxs-lookup"><span data-stu-id="b4822-362">Scale of objects and environments</span></span>](scale.md)
* [<span data-ttu-id="b4822-363">游標, 視覺提示</span><span class="sxs-lookup"><span data-stu-id="b4822-363">Cursors, Visual cues</span></span>](cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="b4822-364">外部參考</span><span class="sxs-lookup"><span data-stu-id="b4822-364">External references</span></span>

* [<span data-ttu-id="b4822-365">FOV 的許多 ado</span><span class="sxs-lookup"><span data-stu-id="b4822-365">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="b4822-366">使用者位置的內容反應</span><span class="sxs-lookup"><span data-stu-id="b4822-366">Content reacts to user position</span></span>

<span data-ttu-id="b4822-367">全息影像應該以「實際」物件的相同方式來回應使用者位置。</span><span class="sxs-lookup"><span data-stu-id="b4822-367">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="b4822-368">值得注意的設計考慮是 UI 元素, 不一定會假設使用者的位置是固定的, 而且會隨著使用者的動作而調整。</span><span class="sxs-lookup"><span data-stu-id="b4822-368">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="b4822-369">設計可正確適應使用者位置的應用程式, 將會建立更可信的體驗, 並讓您更容易使用。</span><span class="sxs-lookup"><span data-stu-id="b4822-369">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="b4822-370">裝置影響</span><span class="sxs-lookup"><span data-stu-id="b4822-370">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b4822-371"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4822-371"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b4822-372"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4822-372"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b4822-373">✔️</span><span class="sxs-lookup"><span data-stu-id="b4822-373">✔️</span></span></td>
        <td><span data-ttu-id="b4822-374">✔️</span><span class="sxs-lookup"><span data-stu-id="b4822-374">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="b4822-375">品質準則</span><span class="sxs-lookup"><span data-stu-id="b4822-375">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="b4822-376">效果</span><span class="sxs-lookup"><span data-stu-id="b4822-376">Best</span></span> </td><td> <span data-ttu-id="b4822-377">內容和 UI 會適應使用者位置, 讓使用者自然地與預期使用者移動範圍內的內容互動。</span><span class="sxs-lookup"><span data-stu-id="b4822-377">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b4822-378">遇到</span><span class="sxs-lookup"><span data-stu-id="b4822-378">Meets</span></span> </td><td> <span data-ttu-id="b4822-379">UI 會配合使用者位置, 但可能會妨礙需要使用者調整其位置的重要內容的觀點。</span><span class="sxs-lookup"><span data-stu-id="b4822-379">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="b4822-380">無法</span><span class="sxs-lookup"><span data-stu-id="b4822-380">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="b4822-381">UI 元素會在移動期間遺失或鎖定, 導致使用者 unnaturally 返回 (或尋找) 控制項。</span><span class="sxs-lookup"><span data-stu-id="b4822-381">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="b4822-382">UI 元素會限制主要內容的顯示。</span><span class="sxs-lookup"><span data-stu-id="b4822-382">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="b4822-383">UI 移動不會針對觀看距離和動力而優化, 特別是以<a href="billboarding-and-tag-along.md">標記為沿著</a>的 UI 元素。</span><span class="sxs-lookup"><span data-stu-id="b4822-383">UI movement is not optimized for viewing distance and momentum particularly with <a href="billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="b4822-384">如何測量</span><span class="sxs-lookup"><span data-stu-id="b4822-384">How to measure</span></span>

* <span data-ttu-id="b4822-385">所有的測量都應該在案例的合理範圍內完成。</span><span class="sxs-lookup"><span data-stu-id="b4822-385">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="b4822-386">雖然使用者移動會有所不同, 但不會嘗試透過極端的使用者移動來誘騙應用程式。</span><span class="sxs-lookup"><span data-stu-id="b4822-386">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="b4822-387">針對 UI 元素, 不論使用者移動為何, 都應該可以使用相關的控制項。</span><span class="sxs-lookup"><span data-stu-id="b4822-387">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="b4822-388">例如, 如果使用者正在觀看3D 地圖並使用 zoom 進行流覽, 則無論位置為何, 縮放控制項都應該隨時可供使用者使用。</span><span class="sxs-lookup"><span data-stu-id="b4822-388">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="b4822-389">建議</span><span class="sxs-lookup"><span data-stu-id="b4822-389">Recommendations</span></span>

* <span data-ttu-id="b4822-390">使用者是相機, 並控制移動。</span><span class="sxs-lookup"><span data-stu-id="b4822-390">The user is the camera and they control the movement.</span></span> <span data-ttu-id="b4822-391">讓它們成為磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="b4822-391">Let them drive.</span></span>
* <span data-ttu-id="b4822-392">請考慮 billboarding 的文字和功能表系統, 如果使用者想要四處移動, 則會以世界鎖定或遮蔽的方式呈現。</span><span class="sxs-lookup"><span data-stu-id="b4822-392">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="b4822-393">針對需要追蹤使用者的內容使用標記, 同時仍允許使用者查看其前面的內容。</span><span class="sxs-lookup"><span data-stu-id="b4822-393">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="b4822-394">資源</span><span class="sxs-lookup"><span data-stu-id="b4822-394">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="b4822-395">文件</span><span class="sxs-lookup"><span data-stu-id="b4822-395">Documentation</span></span>

* [<span data-ttu-id="b4822-396">互動設計</span><span class="sxs-lookup"><span data-stu-id="b4822-396">Interaction design</span></span>](hologram.md)
* [<span data-ttu-id="b4822-397">色彩、光線和材質</span><span class="sxs-lookup"><span data-stu-id="b4822-397">Color, light, and material</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="b4822-398">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="b4822-398">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="b4822-399">本能互動</span><span class="sxs-lookup"><span data-stu-id="b4822-399">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="b4822-400">自我移動和使用者 locomotion</span><span class="sxs-lookup"><span data-stu-id="b4822-400">Self-motion and user locomotion</span></span>](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="b4822-401">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="b4822-401">Tools and tutorials</span></span>

* [<span data-ttu-id="b4822-402">MR Input 210：目光</span><span class="sxs-lookup"><span data-stu-id="b4822-402">MR Input 210: Gaze</span></span>](holograms-210.md)

## <a name="input-interaction-clarity"></a><span data-ttu-id="b4822-403">輸入互動清楚</span><span class="sxs-lookup"><span data-stu-id="b4822-403">Input interaction clarity</span></span>

<span data-ttu-id="b4822-404">輸入互動清楚是應用程式可用性的關鍵, 並包含互動方法的輸入一致性、是多麼平易近人、可搜尋性。</span><span class="sxs-lookup"><span data-stu-id="b4822-404">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="b4822-405">使用者應該能夠在不重新的情況下, 使用全平臺的通用互動。</span><span class="sxs-lookup"><span data-stu-id="b4822-405">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="b4822-406">如果應用程式具有自訂輸入, 則應該清楚地溝通並示範。</span><span class="sxs-lookup"><span data-stu-id="b4822-406">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="b4822-407">裝置影響</span><span class="sxs-lookup"><span data-stu-id="b4822-407">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b4822-408"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4822-408"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b4822-409"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4822-409"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b4822-410">✔️</span><span class="sxs-lookup"><span data-stu-id="b4822-410">✔️</span></span></td>
        <td><span data-ttu-id="b4822-411">✔️</span><span class="sxs-lookup"><span data-stu-id="b4822-411">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="b4822-412">品質準則</span><span class="sxs-lookup"><span data-stu-id="b4822-412">Quality criteria</span></span>

|  <span data-ttu-id="b4822-413">效果</span><span class="sxs-lookup"><span data-stu-id="b4822-413">Best</span></span>  |  <span data-ttu-id="b4822-414">遇到</span><span class="sxs-lookup"><span data-stu-id="b4822-414">Meets</span></span> |  <span data-ttu-id="b4822-415">無法</span><span class="sxs-lookup"><span data-stu-id="b4822-415">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="b4822-416">輸入互動方法與 Windows Mixed Reality 一致提供的[指引](interaction-fundamentals.md)。</span><span class="sxs-lookup"><span data-stu-id="b4822-416">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](interaction-fundamentals.md).</span></span> <span data-ttu-id="b4822-417">任何自訂輸入都不應該與標準輸入 (而是使用標準互動) 重複, 而且必須清楚地傳達並向使用者示範。</span><span class="sxs-lookup"><span data-stu-id="b4822-417">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="b4822-418">與 [最佳] 類似, 但自訂輸入與標準輸入方法是多餘的。</span><span class="sxs-lookup"><span data-stu-id="b4822-418">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="b4822-419">使用者仍可透過應用程式體驗達成目標和進度。</span><span class="sxs-lookup"><span data-stu-id="b4822-419">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="b4822-420">不易瞭解輸入法或按鈕對應。</span><span class="sxs-lookup"><span data-stu-id="b4822-420">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="b4822-421">輸入會經過大量自訂, 不支援標準輸入、無指示, 或可能導致疲勞和緩和問題。</span><span class="sxs-lookup"><span data-stu-id="b4822-421">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="b4822-422">如何測量</span><span class="sxs-lookup"><span data-stu-id="b4822-422">How to measure</span></span>

* <span data-ttu-id="b4822-423">應用程式會使用一致的[標準輸入方法。](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="b4822-423">The app uses consistent [standard input methods.](interaction-fundamentals.md)</span></span>
* <span data-ttu-id="b4822-424">如果應用程式有領域輸入, 則會透過下列方式清楚地進行通訊:</span><span class="sxs-lookup"><span data-stu-id="b4822-424">If the app has custome input, it is clearly communicated through:</span></span>
* <span data-ttu-id="b4822-425">首次執行體驗</span><span class="sxs-lookup"><span data-stu-id="b4822-425">First-run experience</span></span>
* <span data-ttu-id="b4822-426">簡介畫面</span><span class="sxs-lookup"><span data-stu-id="b4822-426">Introductory screens</span></span>
* <span data-ttu-id="b4822-427">工具提示</span><span class="sxs-lookup"><span data-stu-id="b4822-427">Tooltips</span></span>
* <span data-ttu-id="b4822-428">手動教練</span><span class="sxs-lookup"><span data-stu-id="b4822-428">Hand coach</span></span>
* <span data-ttu-id="b4822-429">說明區段</span><span class="sxs-lookup"><span data-stu-id="b4822-429">Help section</span></span>
* <span data-ttu-id="b4822-430">聲音結束</span><span class="sxs-lookup"><span data-stu-id="b4822-430">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="b4822-431">建議</span><span class="sxs-lookup"><span data-stu-id="b4822-431">Recommendations</span></span>

* <span data-ttu-id="b4822-432">盡可能使用標準輸入方法。</span><span class="sxs-lookup"><span data-stu-id="b4822-432">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="b4822-433">提供非標準輸入法的示範、教學課程和工具提示。</span><span class="sxs-lookup"><span data-stu-id="b4822-433">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="b4822-434">在整個應用程式中使用一致的互動模型。</span><span class="sxs-lookup"><span data-stu-id="b4822-434">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="b4822-435">資源</span><span class="sxs-lookup"><span data-stu-id="b4822-435">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="b4822-436">文件</span><span class="sxs-lookup"><span data-stu-id="b4822-436">Documentation</span></span>

* [<span data-ttu-id="b4822-437">本能互動</span><span class="sxs-lookup"><span data-stu-id="b4822-437">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="b4822-438">可互動物件</span><span class="sxs-lookup"><span data-stu-id="b4822-438">Interactable objects</span></span>](interactable-object.md)
* [<span data-ttu-id="b4822-439">頭部目光和停駐</span><span class="sxs-lookup"><span data-stu-id="b4822-439">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="b4822-440">游標</span><span class="sxs-lookup"><span data-stu-id="b4822-440">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="b4822-441">舒適和注視</span><span class="sxs-lookup"><span data-stu-id="b4822-441">Comfort and gaze</span></span>](comfort.md#gaze-direction)
* [<span data-ttu-id="b4822-442">筆勢</span><span class="sxs-lookup"><span data-stu-id="b4822-442">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="b4822-443">語音輸入</span><span class="sxs-lookup"><span data-stu-id="b4822-443">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="b4822-444">語音命令</span><span class="sxs-lookup"><span data-stu-id="b4822-444">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="b4822-445">運動控制器</span><span class="sxs-lookup"><span data-stu-id="b4822-445">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="b4822-446">Unity 的輸入移植指南</span><span class="sxs-lookup"><span data-stu-id="b4822-446">Input porting guide for Unity</span></span>](input-porting-guide-for-unity.md)
* [<span data-ttu-id="b4822-447">Unity 中的鍵盤輸入</span><span class="sxs-lookup"><span data-stu-id="b4822-447">Keyboard input in Unity</span></span>](keyboard-input-in-unity.md)
* [<span data-ttu-id="b4822-448">Unity 中的目光</span><span class="sxs-lookup"><span data-stu-id="b4822-448">Gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="b4822-449">Unity 中的筆勢和運動控制器</span><span class="sxs-lookup"><span data-stu-id="b4822-449">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="b4822-450">Unity 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="b4822-450">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="b4822-451">DirectX 中的鍵盤、滑鼠及控制器輸入</span><span class="sxs-lookup"><span data-stu-id="b4822-451">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="b4822-452">DirectX 中的頭部和眼睛目光</span><span class="sxs-lookup"><span data-stu-id="b4822-452">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="b4822-453">DirectX 中的手部和運動控制器</span><span class="sxs-lookup"><span data-stu-id="b4822-453">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="b4822-454">DirectX 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="b4822-454">Voice input in DirectX</span></span>](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="b4822-455">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="b4822-455">Tools and tutorials</span></span>

* [<span data-ttu-id="b4822-456">案例研究:追求更個人運算的能力</span><span class="sxs-lookup"><span data-stu-id="b4822-456">Case study: The pursuit of more personal computing</span></span>](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="b4822-457">轉換研究:HoloStudio UI 和互動設計學習</span><span class="sxs-lookup"><span data-stu-id="b4822-457">Cast study: HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="b4822-458">範例應用程式:元素的定期資料表</span><span class="sxs-lookup"><span data-stu-id="b4822-458">Sample app: Periodic table of the elements</span></span>](periodic-table-of-the-elements.md)
* [<span data-ttu-id="b4822-459">範例應用程式:陰曆模組</span><span class="sxs-lookup"><span data-stu-id="b4822-459">Sample app: Lunar module</span></span>](lunar-module.md)
* [<span data-ttu-id="b4822-460">MR Input 210：目光</span><span class="sxs-lookup"><span data-stu-id="b4822-460">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="b4822-461">MR Input 211：動作</span><span class="sxs-lookup"><span data-stu-id="b4822-461">MR Input 211: Gestures</span></span>](holograms-211.md)
* [<span data-ttu-id="b4822-462">MR Input 212：語音</span><span class="sxs-lookup"><span data-stu-id="b4822-462">MR Input 212: Voice</span></span>](holograms-212.md)

## <a name="interactable-objects"></a><span data-ttu-id="b4822-463">可互動物件</span><span class="sxs-lookup"><span data-stu-id="b4822-463">Interactable objects</span></span>

<span data-ttu-id="b4822-464">一個按鈕很長的比喻, 是用來觸發2D 抽象世界中的事件。</span><span class="sxs-lookup"><span data-stu-id="b4822-464">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="b4822-465">在三維混合現實世界中, 我們不再需要局限于此抽象概念。</span><span class="sxs-lookup"><span data-stu-id="b4822-465">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="b4822-466">任何專案都可以是觸發事件的可互動物件。</span><span class="sxs-lookup"><span data-stu-id="b4822-466">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="b4822-467">可互動物件可以從資料表上的咖啡杯, 呈現為以空中浮動的球形文字。</span><span class="sxs-lookup"><span data-stu-id="b4822-467">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="b4822-468">不論表單為何, 使用者都應該透過視覺和音訊提示清楚地辨識可互動物件。</span><span class="sxs-lookup"><span data-stu-id="b4822-468">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="b4822-469">裝置影響</span><span class="sxs-lookup"><span data-stu-id="b4822-469">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b4822-470"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4822-470"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b4822-471"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4822-471"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b4822-472">✔️</span><span class="sxs-lookup"><span data-stu-id="b4822-472">✔️</span></span></td>
        <td><span data-ttu-id="b4822-473">✔️</span><span class="sxs-lookup"><span data-stu-id="b4822-473">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="b4822-474">品質準則</span><span class="sxs-lookup"><span data-stu-id="b4822-474">Quality criteria</span></span>

|  <span data-ttu-id="b4822-475">效果</span><span class="sxs-lookup"><span data-stu-id="b4822-475">Best</span></span>  |  <span data-ttu-id="b4822-476">遇到</span><span class="sxs-lookup"><span data-stu-id="b4822-476">Meets</span></span> |  <span data-ttu-id="b4822-477">無法</span><span class="sxs-lookup"><span data-stu-id="b4822-477">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="b4822-478">不論何種形式, 可互動物件都可以透過三個狀態的視覺和音訊提示來辨識: [閒置]、[目標] 和 [已選取]。</span><span class="sxs-lookup"><span data-stu-id="b4822-478">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="b4822-479">「瞭解這一點」在整個經驗中都是清楚且一致的使用方式。</span><span class="sxs-lookup"><span data-stu-id="b4822-479">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="b4822-480">系統會縮放並散佈物件, 以允許錯誤的目標。</span><span class="sxs-lookup"><span data-stu-id="b4822-480">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="b4822-481">使用者可以透過音訊或視覺效果的意見反應, 將物件辨識為可互動, 並可將物件設為目標並啟動。</span><span class="sxs-lookup"><span data-stu-id="b4822-481">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="b4822-482">若未提供視覺或音訊提示, 使用者就無法辨識可互動物件。</span><span class="sxs-lookup"><span data-stu-id="b4822-482">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="b4822-483">互動因物件縮放或物件之間的距離而容易出錯。</span><span class="sxs-lookup"><span data-stu-id="b4822-483">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="b4822-484">如何測量</span><span class="sxs-lookup"><span data-stu-id="b4822-484">How to measure</span></span>

* <span data-ttu-id="b4822-485">可互動物件可辨識為 ' 可互動 ';包括按鈕、功能表和應用程式特定內容。</span><span class="sxs-lookup"><span data-stu-id="b4822-485">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="b4822-486">根據經驗法則, 在以可互動物件為目標時, 應該會有視覺和音訊提示。</span><span class="sxs-lookup"><span data-stu-id="b4822-486">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="b4822-487">建議</span><span class="sxs-lookup"><span data-stu-id="b4822-487">Recommendations</span></span>

* <span data-ttu-id="b4822-488">使用視覺效果和音訊意見反應進行互動。</span><span class="sxs-lookup"><span data-stu-id="b4822-488">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="b4822-489">應針對每個輸入狀態 ([閒置]、[目標]、[已選取]) 區分視覺效果意見反應</span><span class="sxs-lookup"><span data-stu-id="b4822-489">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="b4822-490">可互動物件應調整並放置於錯誤的目標上。</span><span class="sxs-lookup"><span data-stu-id="b4822-490">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="b4822-491">群組的可互動物件 (例如功能表列或清單) 應具有適當的目標間距。</span><span class="sxs-lookup"><span data-stu-id="b4822-491">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="b4822-492">支援語音命令的按鈕和功能表應該提供命令關鍵字的文字標籤 (「請參閱它」)</span><span class="sxs-lookup"><span data-stu-id="b4822-492">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="b4822-493">資源</span><span class="sxs-lookup"><span data-stu-id="b4822-493">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="b4822-494">文件</span><span class="sxs-lookup"><span data-stu-id="b4822-494">Documentation</span></span>

* [<span data-ttu-id="b4822-495">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="b4822-495">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="b4822-496">Unity 中的文字</span><span class="sxs-lookup"><span data-stu-id="b4822-496">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="b4822-497">週框方塊和應用程式列</span><span class="sxs-lookup"><span data-stu-id="b4822-497">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="b4822-498">語音命令</span><span class="sxs-lookup"><span data-stu-id="b4822-498">Voice commanding</span></span>](voice-design.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="b4822-499">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="b4822-499">Tools and tutorials</span></span>

* [<span data-ttu-id="b4822-500">混合現實工具組-UX</span><span class="sxs-lookup"><span data-stu-id="b4822-500">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="b4822-501">房間掃描</span><span class="sxs-lookup"><span data-stu-id="b4822-501">Room scanning</span></span>

<span data-ttu-id="b4822-502">需要空間對應資料的應用程式會依賴裝置, 在使用者探索其在使用中裝置的環境時, 于一段時間內自動收集此資料。</span><span class="sxs-lookup"><span data-stu-id="b4822-502">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="b4822-503">此資料的完整性和品質取決於數個因素, 包括使用者已完成的探索量、流覽後經過的時間, 以及設備 (例如傢俱和門) 在掃描區域之後是否已移動。</span><span class="sxs-lookup"><span data-stu-id="b4822-503">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="b4822-504">許多應用程式會在體驗開始時分析空間對應資料, 以判斷使用者是否應該執行額外的步驟來改善空間對應的完整性和品質。</span><span class="sxs-lookup"><span data-stu-id="b4822-504">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="b4822-505">如果需要使用者掃描環境, 請在掃描體驗期間提供清楚的指引。</span><span class="sxs-lookup"><span data-stu-id="b4822-505">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="b4822-506">裝置影響</span><span class="sxs-lookup"><span data-stu-id="b4822-506">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b4822-507"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4822-507"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b4822-508"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4822-508"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b4822-509">✔️</span><span class="sxs-lookup"><span data-stu-id="b4822-509">✔️</span></span></td>
        <td><span data-ttu-id="b4822-510">❌</span><span class="sxs-lookup"><span data-stu-id="b4822-510">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="b4822-511">品質準則</span><span class="sxs-lookup"><span data-stu-id="b4822-511">Quality criteria</span></span>

|  <span data-ttu-id="b4822-512">效果</span><span class="sxs-lookup"><span data-stu-id="b4822-512">Best</span></span>  |  <span data-ttu-id="b4822-513">遇到</span><span class="sxs-lookup"><span data-stu-id="b4822-513">Meets</span></span> |  <span data-ttu-id="b4822-514">無法</span><span class="sxs-lookup"><span data-stu-id="b4822-514">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="b4822-515">空間網格的視覺效果會告訴使用者掃描正在進行中。</span><span class="sxs-lookup"><span data-stu-id="b4822-515">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="b4822-516">使用者清楚知道要執行的動作, 以及掃描開始和停止的時間。</span><span class="sxs-lookup"><span data-stu-id="b4822-516">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="b4822-517">提供空間網格的視覺效果, 但使用者可能無法清楚瞭解該怎麼做, 而且不會提供任何進度資訊。</span><span class="sxs-lookup"><span data-stu-id="b4822-517">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="b4822-518">沒有網格的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="b4822-518">No visualization of mesh.</span></span> <span data-ttu-id="b4822-519">沒有提供指引資訊給使用者關於要查看的位置, 或掃描開始/停止的時間。</span><span class="sxs-lookup"><span data-stu-id="b4822-519">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="b4822-520">如何測量</span><span class="sxs-lookup"><span data-stu-id="b4822-520">How to measure</span></span>

* <span data-ttu-id="b4822-521">在進行必要的房間掃描時, 會提供視覺和音訊指引, 指出要查看的位置, 以及開始和停止掃描的時機。</span><span class="sxs-lookup"><span data-stu-id="b4822-521">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="b4822-522">建議</span><span class="sxs-lookup"><span data-stu-id="b4822-522">Recommendations</span></span>

* <span data-ttu-id="b4822-523">指出使用者鄰近範圍中的總數量必須是體驗的一部分。</span><span class="sxs-lookup"><span data-stu-id="b4822-523">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="b4822-524">當掃描開始並停止 (例如進度指示器) 時進行通訊。</span><span class="sxs-lookup"><span data-stu-id="b4822-524">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="b4822-525">在掃描期間使用網格的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="b4822-525">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="b4822-526">提供視覺和音訊提示, 以鼓勵使用者在房間周圍尋找並移動。</span><span class="sxs-lookup"><span data-stu-id="b4822-526">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="b4822-527">通知使用者要在哪裡改善資料。</span><span class="sxs-lookup"><span data-stu-id="b4822-527">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="b4822-528">在許多情況下, 最好告訴使用者需要執行的動作 (例如, 查看 [傢俱] 的上限), 以便取得所需的掃描品質。</span><span class="sxs-lookup"><span data-stu-id="b4822-528">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="b4822-529">資源</span><span class="sxs-lookup"><span data-stu-id="b4822-529">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="b4822-530">文件</span><span class="sxs-lookup"><span data-stu-id="b4822-530">Documentation</span></span>

* [<span data-ttu-id="b4822-531">空間位置掃描視覺效果</span><span class="sxs-lookup"><span data-stu-id="b4822-531">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="b4822-532">案例研究:擴充 HoloLens 的空間對應功能</span><span class="sxs-lookup"><span data-stu-id="b4822-532">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="b4822-533">案例研究:適用于 HoloTour 的空間音效設計</span><span class="sxs-lookup"><span data-stu-id="b4822-533">Case study: Spatial sound design for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="b4822-534">案例研究:在片段中建立沉浸式體驗</span><span class="sxs-lookup"><span data-stu-id="b4822-534">Case study: Creating an immersive experience in Fragments</span></span>](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="b4822-535">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="b4822-535">Tools and tutorials</span></span>

* [<span data-ttu-id="b4822-536">混合現實工具組-UX</span><span class="sxs-lookup"><span data-stu-id="b4822-536">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="b4822-537">方向指標</span><span class="sxs-lookup"><span data-stu-id="b4822-537">Directional indicators</span></span>

<span data-ttu-id="b4822-538">在混合現實應用程式中, 內容可能會在 pixels occluded 的欄位之外, 或由真實世界的物件所組成。</span><span class="sxs-lookup"><span data-stu-id="b4822-538">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="b4822-539">設計良好的應用程式可讓使用者更輕鬆地尋找不可見的內容。</span><span class="sxs-lookup"><span data-stu-id="b4822-539">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="b4822-540">方向指標會向使用者通知重要內容, 並提供相對於使用者位置的內容指引。</span><span class="sxs-lookup"><span data-stu-id="b4822-540">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="b4822-541">非可見內容的指引可以採用音效發射器、方向箭號或直接視覺提示的形式。</span><span class="sxs-lookup"><span data-stu-id="b4822-541">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="b4822-542">裝置影響</span><span class="sxs-lookup"><span data-stu-id="b4822-542">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b4822-543"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4822-543"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b4822-544"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4822-544"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b4822-545">✔️</span><span class="sxs-lookup"><span data-stu-id="b4822-545">✔️</span></span></td>
        <td><span data-ttu-id="b4822-546">✔️</span><span class="sxs-lookup"><span data-stu-id="b4822-546">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="b4822-547">品質準則</span><span class="sxs-lookup"><span data-stu-id="b4822-547">Quality criteria</span></span>

|  <span data-ttu-id="b4822-548">效果</span><span class="sxs-lookup"><span data-stu-id="b4822-548">Best</span></span>  |  <span data-ttu-id="b4822-549">遇到</span><span class="sxs-lookup"><span data-stu-id="b4822-549">Meets</span></span> |  <span data-ttu-id="b4822-550">無法</span><span class="sxs-lookup"><span data-stu-id="b4822-550">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="b4822-551">視覺效果和音訊提示會直接引導使用者前往視圖欄位以外的相關內容。</span><span class="sxs-lookup"><span data-stu-id="b4822-551">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="b4822-552">箭號或某個指標, 會以內容的一般方向來指向使用者。</span><span class="sxs-lookup"><span data-stu-id="b4822-552">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="b4822-553">相關內容不在視野的範圍內, 也不會提供不佳的位置指引給使用者。</span><span class="sxs-lookup"><span data-stu-id="b4822-553">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="b4822-554">如何測量</span><span class="sxs-lookup"><span data-stu-id="b4822-554">How to measure</span></span>

* <span data-ttu-id="b4822-555">[使用者] 欄位以外的相關內容可透過視覺效果和/或音訊提示來進行探索。</span><span class="sxs-lookup"><span data-stu-id="b4822-555">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="b4822-556">建議</span><span class="sxs-lookup"><span data-stu-id="b4822-556">Recommendations</span></span>

* <span data-ttu-id="b4822-557">當相關內容超出使用者的視圖欄位時, 請使用方向指標和音訊提示來引導使用者進行內容。</span><span class="sxs-lookup"><span data-stu-id="b4822-557">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="b4822-558">在許多情況下, 直接視覺輔助線優先于方向箭號。</span><span class="sxs-lookup"><span data-stu-id="b4822-558">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="b4822-559">方向指標不應內建至游標處。</span><span class="sxs-lookup"><span data-stu-id="b4822-559">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="b4822-560">資源</span><span class="sxs-lookup"><span data-stu-id="b4822-560">Resources</span></span>

* [<span data-ttu-id="b4822-561">全像攝影框架</span><span class="sxs-lookup"><span data-stu-id="b4822-561">Holographic frame</span></span>](holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="b4822-562">資料載入</span><span class="sxs-lookup"><span data-stu-id="b4822-562">Data loading</span></span>

<span data-ttu-id="b4822-563">進度控制項為使用者提供回饋，告知正在進行長時間執行的操作。</span><span class="sxs-lookup"><span data-stu-id="b4822-563">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="b4822-564">這可能表示當進度指示器可見時, 使用者無法與應用程式互動, 也可以指出等候時間可能是多久。</span><span class="sxs-lookup"><span data-stu-id="b4822-564">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="b4822-565">裝置影響</span><span class="sxs-lookup"><span data-stu-id="b4822-565">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b4822-566"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4822-566"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="b4822-567"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4822-567"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b4822-568">✔️</span><span class="sxs-lookup"><span data-stu-id="b4822-568">✔️</span></span></td>
        <td><span data-ttu-id="b4822-569">✔️</span><span class="sxs-lookup"><span data-stu-id="b4822-569">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="b4822-570">品質準則</span><span class="sxs-lookup"><span data-stu-id="b4822-570">Quality criteria</span></span>

|  <span data-ttu-id="b4822-571">效果</span><span class="sxs-lookup"><span data-stu-id="b4822-571">Best</span></span>  |  <span data-ttu-id="b4822-572">遇到</span><span class="sxs-lookup"><span data-stu-id="b4822-572">Meets</span></span> |  <span data-ttu-id="b4822-573">無法</span><span class="sxs-lookup"><span data-stu-id="b4822-573">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="b4822-574">以進度列或環形形式呈現的動畫視覺指標, 顯示任何資料載入或處理期間的進度。</span><span class="sxs-lookup"><span data-stu-id="b4822-574">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="b4822-575">視覺指標會提供等待時間長度的指引。</span><span class="sxs-lookup"><span data-stu-id="b4822-575">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="b4822-576">使用者會收到資料載入正在進行中的通知, 但不會指出等候的時間長度。</span><span class="sxs-lookup"><span data-stu-id="b4822-576">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="b4822-577">工作所花費的時間超過5秒的資料載入或處理指示器。</span><span class="sxs-lookup"><span data-stu-id="b4822-577">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="b4822-578">如何測量</span><span class="sxs-lookup"><span data-stu-id="b4822-578">How to measure</span></span>

* <span data-ttu-id="b4822-579">在資料載入期間, 確認不會有超過5秒的空白狀態。</span><span class="sxs-lookup"><span data-stu-id="b4822-579">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="b4822-580">建議</span><span class="sxs-lookup"><span data-stu-id="b4822-580">Recommendations</span></span>

* <span data-ttu-id="b4822-581">當使用者可能會感覺到此應用程式停止或損毀時, 請提供資料載入 animator, 以顯示任何情況下的進度。</span><span class="sxs-lookup"><span data-stu-id="b4822-581">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="b4822-582">合理的經驗法則是任何可能需要5秒以上的「載入」活動。</span><span class="sxs-lookup"><span data-stu-id="b4822-582">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="b4822-583">資源</span><span class="sxs-lookup"><span data-stu-id="b4822-583">Resources</span></span>

* [<span data-ttu-id="b4822-584">顯示進度</span><span class="sxs-lookup"><span data-stu-id="b4822-584">Displaying progress</span></span>](progress.md)
