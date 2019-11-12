---
title: 應用程式品質準則
description: 本檔說明影響混合現實應用程式品質的最大因素。
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: 應用程式品質準則，混合現實，混合現實應用程式
ms.openlocfilehash: d167e141b536f9247d22e40afefa718ecc399f5a
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926592"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="752d9-104">應用程式品質準則</span><span class="sxs-lookup"><span data-stu-id="752d9-104">App quality criteria</span></span>

<span data-ttu-id="752d9-105">本檔說明影響混合現實應用程式品質的最大因素。</span><span class="sxs-lookup"><span data-stu-id="752d9-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="752d9-106">針對每個因素，會提供下列資訊</span><span class="sxs-lookup"><span data-stu-id="752d9-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="752d9-107">總覽–「品質因素」和「重要性」的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="752d9-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="752d9-108">裝置影響-受影響的 Windows 混合現實裝置類型。</span><span class="sxs-lookup"><span data-stu-id="752d9-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="752d9-109">品質準則–如何評估品質因素。</span><span class="sxs-lookup"><span data-stu-id="752d9-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="752d9-110">如何測量–測量（或體驗）問題的方法。</span><span class="sxs-lookup"><span data-stu-id="752d9-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="752d9-111">建議事項–提供更佳使用者體驗的方法摘要。</span><span class="sxs-lookup"><span data-stu-id="752d9-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="752d9-112">資源-相關的開發人員和設計資源，有助於建立更佳的應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="752d9-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="752d9-113">畫面播放速率</span><span class="sxs-lookup"><span data-stu-id="752d9-113">Frame rate</span></span>

<span data-ttu-id="752d9-114">畫面播放速率是全息和使用者緩和的第一要件。</span><span class="sxs-lookup"><span data-stu-id="752d9-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="752d9-115">低於建議目標的畫面播放速率可能會使全息影像顯得抖動、對體驗的 believability 造成負面影響，並可能造成眼睛疲勞。</span><span class="sxs-lookup"><span data-stu-id="752d9-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="752d9-116">您在 Windows Mixed Reality 沉浸式耳機上體驗的目標畫面播放速率會是60Hz 或90Hz，視您想要支援的 Windows Mixed Reality 相容電腦而定。</span><span class="sxs-lookup"><span data-stu-id="752d9-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="752d9-117">若是 HoloLens，目標畫面播放速率為60Hz。</span><span class="sxs-lookup"><span data-stu-id="752d9-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="752d9-118">裝置影響</span><span class="sxs-lookup"><span data-stu-id="752d9-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="752d9-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="752d9-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="752d9-120"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="752d9-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="752d9-121">✔️</span><span class="sxs-lookup"><span data-stu-id="752d9-121">✔️</span></span></td>
        <td><span data-ttu-id="752d9-122">✔️</span><span class="sxs-lookup"><span data-stu-id="752d9-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="752d9-123">品質準則</span><span class="sxs-lookup"><span data-stu-id="752d9-123">Quality criteria</span></span>

|  <span data-ttu-id="752d9-124">效果</span><span class="sxs-lookup"><span data-stu-id="752d9-124">Best</span></span>  |  <span data-ttu-id="752d9-125">遇到</span><span class="sxs-lookup"><span data-stu-id="752d9-125">Meets</span></span> |  <span data-ttu-id="752d9-126">無法</span><span class="sxs-lookup"><span data-stu-id="752d9-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="752d9-127">應用程式一致符合目標裝置的每秒畫面格數（FPS）目標： HoloLens 上的 60fps;Ultra 電腦上的 90fps;和60fps 在主流電腦上。</span><span class="sxs-lookup"><span data-stu-id="752d9-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="752d9-128">應用程式的斷斷續續畫面不會阻礙核心體驗;或 FPS 一致地低於所需的目標，但不會妨礙應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="752d9-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="752d9-129">應用程式平均每十秒或更短的畫面播放速率下降。</span><span class="sxs-lookup"><span data-stu-id="752d9-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="752d9-130">如何測量</span><span class="sxs-lookup"><span data-stu-id="752d9-130">How to measure</span></span>

* <span data-ttu-id="752d9-131">[Windows 裝置入口網站](using-the-windows-device-portal.md#system-performance)會在 [系統效能] 下提供即時畫面播放速率圖表。</span><span class="sxs-lookup"><span data-stu-id="752d9-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="752d9-132">若是開發的偵錯工具，請在應用程式中新增 [畫面播放速率] 診斷計數器。</span><span class="sxs-lookup"><span data-stu-id="752d9-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="752d9-133">請參閱範例計數器的資源。</span><span class="sxs-lookup"><span data-stu-id="752d9-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="752d9-134">當應用程式正在執行時，畫面播放速率下降可能會在裝置上經歷，方法是將您的 head 從側邊移至一邊。</span><span class="sxs-lookup"><span data-stu-id="752d9-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="752d9-135">如果全像投影顯示非預期的抖動移動，則低畫面播放速率或穩定性平面可能是原因。</span><span class="sxs-lookup"><span data-stu-id="752d9-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="752d9-136">建議事項</span><span class="sxs-lookup"><span data-stu-id="752d9-136">Recommendations</span></span>

* <span data-ttu-id="752d9-137">在開發工作開始時新增畫面播放速率計數器。</span><span class="sxs-lookup"><span data-stu-id="752d9-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="752d9-138">會評估產生下降畫面播放速率的變更，並適當地解決為效能錯誤。</span><span class="sxs-lookup"><span data-stu-id="752d9-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="752d9-139">資源</span><span class="sxs-lookup"><span data-stu-id="752d9-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="752d9-140">文件</span><span class="sxs-lookup"><span data-stu-id="752d9-140">Documentation</span></span>

* [<span data-ttu-id="752d9-141">瞭解混合現實的效能</span><span class="sxs-lookup"><span data-stu-id="752d9-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="752d9-142">全息的穩定性和畫面播放速率</span><span class="sxs-lookup"><span data-stu-id="752d9-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="752d9-143">資產效能預算</span><span class="sxs-lookup"><span data-stu-id="752d9-143">Asset performance budget</span></span>](asset-creation-process.md)
* [<span data-ttu-id="752d9-144">對 Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="752d9-144">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="752d9-145">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="752d9-145">Tools and tutorials</span></span>

* [<span data-ttu-id="752d9-146">MRToolkit，FPS 計數器顯示</span><span class="sxs-lookup"><span data-stu-id="752d9-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="752d9-147">MRToolkit、著色器</span><span class="sxs-lookup"><span data-stu-id="752d9-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="752d9-148">外部參考</span><span class="sxs-lookup"><span data-stu-id="752d9-148">External references</span></span>

* [<span data-ttu-id="752d9-149">Unity，將行動應用程式優化</span><span class="sxs-lookup"><span data-stu-id="752d9-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="752d9-150">全息影像穩定性</span><span class="sxs-lookup"><span data-stu-id="752d9-150">Hologram stability</span></span>

<span data-ttu-id="752d9-151">穩定的全息影像會提高應用程式的可用性和 believability，並為使用者建立更舒適的觀看體驗。</span><span class="sxs-lookup"><span data-stu-id="752d9-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="752d9-152">全像投影穩定性的品質是良好應用程式開發的結果，以及裝置瞭解（追蹤）其環境的能力。</span><span class="sxs-lookup"><span data-stu-id="752d9-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="752d9-153">雖然畫面播放速率是穩定性的第一個要件，但其他因素可能會影響穩定性，包括：</span><span class="sxs-lookup"><span data-stu-id="752d9-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="752d9-154">使用穩定平面</span><span class="sxs-lookup"><span data-stu-id="752d9-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="752d9-155">距離空間錨點</span><span class="sxs-lookup"><span data-stu-id="752d9-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="752d9-156">修訂</span><span class="sxs-lookup"><span data-stu-id="752d9-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="752d9-157">裝置影響</span><span class="sxs-lookup"><span data-stu-id="752d9-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="752d9-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="752d9-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="752d9-159"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="752d9-159"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="752d9-160">✔️</span><span class="sxs-lookup"><span data-stu-id="752d9-160">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="752d9-161">品質準則</span><span class="sxs-lookup"><span data-stu-id="752d9-161">Quality criteria</span></span>

|  <span data-ttu-id="752d9-162">效果</span><span class="sxs-lookup"><span data-stu-id="752d9-162">Best</span></span>  |  <span data-ttu-id="752d9-163">遇到</span><span class="sxs-lookup"><span data-stu-id="752d9-163">Meets</span></span> |  <span data-ttu-id="752d9-164">無法</span><span class="sxs-lookup"><span data-stu-id="752d9-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="752d9-165">全息影像一致地顯示穩定。</span><span class="sxs-lookup"><span data-stu-id="752d9-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="752d9-166">次要內容表現出非預期的移動;或非預期的移動不會妨礙整體應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="752d9-166">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="752d9-167">框架中的主要內容展現了非預期的移動。</span><span class="sxs-lookup"><span data-stu-id="752d9-167">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="752d9-168">如何測量</span><span class="sxs-lookup"><span data-stu-id="752d9-168">How to measure</span></span>

<span data-ttu-id="752d9-169">在戴上裝置並觀看體驗時：</span><span class="sxs-lookup"><span data-stu-id="752d9-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="752d9-170">將您的 head 從側邊移到一邊，如果全息影像顯示非預期的移動，則不正確的畫面播放速率，或穩定性平面與焦點平面的不適當對齊可能是原因。</span><span class="sxs-lookup"><span data-stu-id="752d9-170">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="752d9-171">四處移動全息影像和環境，尋找像是 [泳道] 和 [jumpiness] 的行為。</span><span class="sxs-lookup"><span data-stu-id="752d9-171">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="752d9-172">這種動作可能是因為裝置未追蹤環境，或與空間錨點的距離所造成。</span><span class="sxs-lookup"><span data-stu-id="752d9-172">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="752d9-173">如果框架中有大型或多個全息影像，請觀察各種深度的全息影像行為，同時將您的頭部位置從側邊移至一邊，如果 shakiness 出現，這可能是穩定平面所造成。</span><span class="sxs-lookup"><span data-stu-id="752d9-173">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recommendations"></a><span data-ttu-id="752d9-174">建議事項</span><span class="sxs-lookup"><span data-stu-id="752d9-174">Recommendations</span></span>

* <span data-ttu-id="752d9-175">在開發工作開始時新增 [畫面播放速率] 計數器。</span><span class="sxs-lookup"><span data-stu-id="752d9-175">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="752d9-176">使用穩定平面。</span><span class="sxs-lookup"><span data-stu-id="752d9-176">Use the stabilization plane.</span></span>
* <span data-ttu-id="752d9-177">一律在其錨點的3個計量中轉譯錨定的全息影像。</span><span class="sxs-lookup"><span data-stu-id="752d9-177">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="752d9-178">請確定您的環境已設定適當的追蹤。</span><span class="sxs-lookup"><span data-stu-id="752d9-178">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="752d9-179">設計您的體驗，以避免框架內各種焦點深度層級的全息影像。</span><span class="sxs-lookup"><span data-stu-id="752d9-179">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="752d9-180">資源</span><span class="sxs-lookup"><span data-stu-id="752d9-180">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="752d9-181">文件</span><span class="sxs-lookup"><span data-stu-id="752d9-181">Documentation</span></span>

* [<span data-ttu-id="752d9-182">全息的穩定性和畫面播放速率</span><span class="sxs-lookup"><span data-stu-id="752d9-182">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="752d9-183">使用穩定平面的案例研究</span><span class="sxs-lookup"><span data-stu-id="752d9-183">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="752d9-184">瞭解混合現實的效能</span><span class="sxs-lookup"><span data-stu-id="752d9-184">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="752d9-185">對 Unity 的效能建議</span><span class="sxs-lookup"><span data-stu-id="752d9-185">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="752d9-186">空間錨點</span><span class="sxs-lookup"><span data-stu-id="752d9-186">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="752d9-187">處理追蹤錯誤</span><span class="sxs-lookup"><span data-stu-id="752d9-187">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="752d9-188">固定的參考框架</span><span class="sxs-lookup"><span data-stu-id="752d9-188">Stationary frame of reference</span></span>](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="752d9-189">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="752d9-189">Tools and tutorials</span></span>

* [<span data-ttu-id="752d9-190">MR 配套套件，Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="752d9-190">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="752d9-191">實際表面上的全息影像位置</span><span class="sxs-lookup"><span data-stu-id="752d9-191">Holograms position on real surfaces</span></span>

<span data-ttu-id="752d9-192">具有實體物件的全息影像不一致（如果要放在彼此之間的關聯性），可以清楚指出全息和真實世界的非聯合。</span><span class="sxs-lookup"><span data-stu-id="752d9-192">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="752d9-193">放置的精確度應該相對於案例的需求;例如，一般介面位置可以使用空間對應，但更精確的放置需要使用標記和校正。</span><span class="sxs-lookup"><span data-stu-id="752d9-193">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="752d9-194">裝置影響</span><span class="sxs-lookup"><span data-stu-id="752d9-194">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="752d9-195"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="752d9-195"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="752d9-196"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="752d9-196"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="752d9-197">✔️</span><span class="sxs-lookup"><span data-stu-id="752d9-197">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="752d9-198">品質準則</span><span class="sxs-lookup"><span data-stu-id="752d9-198">Quality criteria</span></span>

|  <span data-ttu-id="752d9-199">效果</span><span class="sxs-lookup"><span data-stu-id="752d9-199">Best</span></span>  |  <span data-ttu-id="752d9-200">遇到</span><span class="sxs-lookup"><span data-stu-id="752d9-200">Meets</span></span> |  <span data-ttu-id="752d9-201">無法</span><span class="sxs-lookup"><span data-stu-id="752d9-201">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="752d9-202">全像投影對齊表面，通常是以釐米到英寸的範圍。</span><span class="sxs-lookup"><span data-stu-id="752d9-202">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="752d9-203">如果需要更多的精確度，應用程式應該為所需的應用程式規格中的共同作業提供有效率的方式。</span><span class="sxs-lookup"><span data-stu-id="752d9-203">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="752d9-204">NA</span><span class="sxs-lookup"><span data-stu-id="752d9-204">NA</span></span> | <span data-ttu-id="752d9-205">全息影像會與實體目標物件顯示不對齊，方法是中斷表面平面，或顯示為遠離表面。</span><span class="sxs-lookup"><span data-stu-id="752d9-205">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="752d9-206">如果需要精確度，則全息影像應符合案例的近接規格。</span><span class="sxs-lookup"><span data-stu-id="752d9-206">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="752d9-207">如何測量</span><span class="sxs-lookup"><span data-stu-id="752d9-207">How to measure</span></span>

* <span data-ttu-id="752d9-208">放在空間地圖上的全息影像應該不會明顯地浮動在表面上方或下方。</span><span class="sxs-lookup"><span data-stu-id="752d9-208">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="752d9-209">需要精確放置的全息影像應具有某種形式的標記和校正系統，以精確因應案例的需求。</span><span class="sxs-lookup"><span data-stu-id="752d9-209">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="752d9-210">建議事項</span><span class="sxs-lookup"><span data-stu-id="752d9-210">Recommendations</span></span>

* <span data-ttu-id="752d9-211">當不需要有效位數時，空間對應適用于將物件放在介面上。</span><span class="sxs-lookup"><span data-stu-id="752d9-211">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="752d9-212">為了達到最佳精確度，請使用標記或海報來設定全息和 Xbox 控制器（或某種手動對齊機制），以進行最後的校正。</span><span class="sxs-lookup"><span data-stu-id="752d9-212">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="752d9-213">請考慮將多大的全息影像分解成邏輯部分，並將每個部分對齊介面。</span><span class="sxs-lookup"><span data-stu-id="752d9-213">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="752d9-214">不當設定的 interpupillary 距離（IPD）也會影響全息影像對齊。</span><span class="sxs-lookup"><span data-stu-id="752d9-214">Improperly set interpupillary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="752d9-215">請一律將 HoloLens 設定為使用者的 IPD。</span><span class="sxs-lookup"><span data-stu-id="752d9-215">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="752d9-216">資源</span><span class="sxs-lookup"><span data-stu-id="752d9-216">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="752d9-217">文件</span><span class="sxs-lookup"><span data-stu-id="752d9-217">Documentation</span></span>

* [<span data-ttu-id="752d9-218">空間對應位置</span><span class="sxs-lookup"><span data-stu-id="752d9-218">Spatial mapping placement</span></span>](spatial-mapping.md#placement)
* [<span data-ttu-id="752d9-219">房間掃描程式</span><span class="sxs-lookup"><span data-stu-id="752d9-219">Room scanning process</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="752d9-220">空間錨點最佳做法</span><span class="sxs-lookup"><span data-stu-id="752d9-220">Spatial anchors best practices</span></span>](spatial-anchors.md#best-practices)
* [<span data-ttu-id="752d9-221">處理追蹤錯誤</span><span class="sxs-lookup"><span data-stu-id="752d9-221">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="752d9-222">Unity 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="752d9-222">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="752d9-223">Vuforia 開發總覽</span><span class="sxs-lookup"><span data-stu-id="752d9-223">Vuforia development overview</span></span>](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="752d9-224">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="752d9-224">Tools and tutorials</span></span>

* [<span data-ttu-id="752d9-225">MR 空間230：空間對應</span><span class="sxs-lookup"><span data-stu-id="752d9-225">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="752d9-226">MR 工具組，空間對應程式庫</span><span class="sxs-lookup"><span data-stu-id="752d9-226">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="752d9-227">MR 配套套件，海報校正範例</span><span class="sxs-lookup"><span data-stu-id="752d9-227">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="752d9-228">MR 配套套件，Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="752d9-228">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="752d9-229">外部參考</span><span class="sxs-lookup"><span data-stu-id="752d9-229">External references</span></span>

* [<span data-ttu-id="752d9-230">Lowes 案例研究，精確度對齊</span><span class="sxs-lookup"><span data-stu-id="752d9-230">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="752d9-231">觀賞舒適的區域</span><span class="sxs-lookup"><span data-stu-id="752d9-231">Viewing zone of comfort</span></span>

<span data-ttu-id="752d9-232">應用程式開發人員可以在各種深度放置內容和全息影像，以控制使用者的眼睛。</span><span class="sxs-lookup"><span data-stu-id="752d9-232">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="752d9-233">戴 HoloLens 的使用者一律會容納到 2.0 m，以維護清楚的影像，因為 HoloLens 顯示器的固定距離使用者遠接近 2.0 m。</span><span class="sxs-lookup"><span data-stu-id="752d9-233">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="752d9-234">不當的內容深度可能會導致視覺 discomfort 或疲勞。</span><span class="sxs-lookup"><span data-stu-id="752d9-234">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="752d9-235">裝置影響</span><span class="sxs-lookup"><span data-stu-id="752d9-235">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="752d9-236"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="752d9-236"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="752d9-237"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="752d9-237"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="752d9-238">✔️</span><span class="sxs-lookup"><span data-stu-id="752d9-238">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="752d9-239">品質準則</span><span class="sxs-lookup"><span data-stu-id="752d9-239">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="752d9-240">效果</span><span class="sxs-lookup"><span data-stu-id="752d9-240">Best</span></span> </td><td><ul>
<li><span data-ttu-id="752d9-241">將內容放在2m。</span><span class="sxs-lookup"><span data-stu-id="752d9-241">Place content at 2m.</span></span></li><li><span data-ttu-id="752d9-242">當您無法避免在2m 時放置全息影像，而且無法避免聚合與住宿之間的衝突時，全像投影位置的最佳區域會介於 1.25 m 到5m 之間。</span><span class="sxs-lookup"><span data-stu-id="752d9-242">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="752d9-243">在每個案例中，設計人員都應該結構內容，以鼓勵使用者離開 1 + m （例如調整內容大小和預設位置參數）。</span><span class="sxs-lookup"><span data-stu-id="752d9-243">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="752d9-244">除非案例特別不需要，否則裁剪平面應該使用從1百萬開始的 fadeout 來執行。</span><span class="sxs-lookup"><span data-stu-id="752d9-244">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="752d9-245">如果需要更深入觀察 motionless 的全像投影，則內容不應該比50cm 更接近。</span><span class="sxs-lookup"><span data-stu-id="752d9-245">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="752d9-246">遇到</span><span class="sxs-lookup"><span data-stu-id="752d9-246">Meets</span></span></td><td> <span data-ttu-id="752d9-247">內容位於觀看和動作指引內，但不適當地使用或不使用裁剪平面。</span><span class="sxs-lookup"><span data-stu-id="752d9-247">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="752d9-248">無法</span><span class="sxs-lookup"><span data-stu-id="752d9-248">Fail</span></span> </td><td> <span data-ttu-id="752d9-249">內容的顯示太接近（通常是 &lt;1.25 m，或 &lt;50cm，針對需要更深入觀察的靜止全息影像）。</span><span class="sxs-lookup"><span data-stu-id="752d9-249">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="752d9-250">如何測量</span><span class="sxs-lookup"><span data-stu-id="752d9-250">How to measure</span></span>

* <span data-ttu-id="752d9-251">內容通常應該2m 在外，但不能接近1.25 或高於5m。</span><span class="sxs-lookup"><span data-stu-id="752d9-251">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="752d9-252">除了少數例外狀況之外，HoloLens 裁剪轉譯距離應該設定為. 85CM，fadeout 的內容是從1m 開始。</span><span class="sxs-lookup"><span data-stu-id="752d9-252">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="752d9-253">處理內容，並記下裁剪平面效果。</span><span class="sxs-lookup"><span data-stu-id="752d9-253">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="752d9-254">固定的內容應該不會接近50cm 的距離。</span><span class="sxs-lookup"><span data-stu-id="752d9-254">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="752d9-255">建議事項</span><span class="sxs-lookup"><span data-stu-id="752d9-255">Recommendations</span></span>

* <span data-ttu-id="752d9-256">設計內容以取得2m 的最佳觀賞距離。</span><span class="sxs-lookup"><span data-stu-id="752d9-256">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="752d9-257">使用從1m 開始的 fadeout 內容，將裁剪轉譯距離設定為85cm。</span><span class="sxs-lookup"><span data-stu-id="752d9-257">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="752d9-258">對於需要進一步觀賞的靜止全息影像，裁剪平面應該不會接近30cm，而 fadeout 應從裁剪平面開始至少10cm。</span><span class="sxs-lookup"><span data-stu-id="752d9-258">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="752d9-259">資源</span><span class="sxs-lookup"><span data-stu-id="752d9-259">Resources</span></span>

* [<span data-ttu-id="752d9-260">呈現距離</span><span class="sxs-lookup"><span data-stu-id="752d9-260">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="752d9-261">Unity 中的焦點</span><span class="sxs-lookup"><span data-stu-id="752d9-261">Focus point in Unity</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="752d9-262">使用 scale 進行實驗</span><span class="sxs-lookup"><span data-stu-id="752d9-262">Experimenting with scale</span></span>](scale.md#experimenting-with-scale)
* [<span data-ttu-id="752d9-263">文字、建議的字型大小</span><span class="sxs-lookup"><span data-stu-id="752d9-263">Text, Recommended font size</span></span>](typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="752d9-264">深度切換</span><span class="sxs-lookup"><span data-stu-id="752d9-264">Depth switching</span></span>

<span data-ttu-id="752d9-265">無論觀賞的緩和問題區域為何，使用者需要經常或快速地在接近和遠的焦點物件之間切換（包括全息影像和真實世界內容），可能會導致 oculomotor 疲勞和一般 discomfort。</span><span class="sxs-lookup"><span data-stu-id="752d9-265">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="752d9-266">裝置影響</span><span class="sxs-lookup"><span data-stu-id="752d9-266">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="752d9-267"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="752d9-267"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="752d9-268"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="752d9-268"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="752d9-269">✔️</span><span class="sxs-lookup"><span data-stu-id="752d9-269">✔️</span></span></td>
        <td><span data-ttu-id="752d9-270">✔️</span><span class="sxs-lookup"><span data-stu-id="752d9-270">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="752d9-271">品質準則</span><span class="sxs-lookup"><span data-stu-id="752d9-271">Quality criteria</span></span>

|  <span data-ttu-id="752d9-272">效果</span><span class="sxs-lookup"><span data-stu-id="752d9-272">Best</span></span>  |  <span data-ttu-id="752d9-273">遇到</span><span class="sxs-lookup"><span data-stu-id="752d9-273">Meets</span></span> |  <span data-ttu-id="752d9-274">無法</span><span class="sxs-lookup"><span data-stu-id="752d9-274">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="752d9-275">限制或自然深度切換，這不會造成使用者 unnaturally 將。</span><span class="sxs-lookup"><span data-stu-id="752d9-275">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="752d9-276">自然深度切換：這是核心並設計成應用程式體驗，或是因非預期的真實世界內容而造成的「突然深度」切換。</span><span class="sxs-lookup"><span data-stu-id="752d9-276">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="752d9-277">一致的深度切換，或不是必要或不是應用程式體驗核心的深入深度切換。</span><span class="sxs-lookup"><span data-stu-id="752d9-277">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="752d9-278">如何測量</span><span class="sxs-lookup"><span data-stu-id="752d9-278">How to measure</span></span>

* <span data-ttu-id="752d9-279">如果應用程式需要使用者一致且/或突然變更深度焦點，則會有深度切換問題。</span><span class="sxs-lookup"><span data-stu-id="752d9-279">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="752d9-280">建議事項</span><span class="sxs-lookup"><span data-stu-id="752d9-280">Recommendations</span></span>

* <span data-ttu-id="752d9-281">將主要內容保持在一致的焦點平面上，並確保穩定平面符合焦點平面。</span><span class="sxs-lookup"><span data-stu-id="752d9-281">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="752d9-282">這可減輕 oculomotor 的疲勞和非預期的全息影像移動。</span><span class="sxs-lookup"><span data-stu-id="752d9-282">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="752d9-283">資源</span><span class="sxs-lookup"><span data-stu-id="752d9-283">Resources</span></span>

* [<span data-ttu-id="752d9-284">呈現距離</span><span class="sxs-lookup"><span data-stu-id="752d9-284">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="752d9-285">Unity 中的焦點</span><span class="sxs-lookup"><span data-stu-id="752d9-285">Focus point in Unity</span></span>](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="752d9-286">使用空間音效</span><span class="sxs-lookup"><span data-stu-id="752d9-286">Use of spatial sound</span></span>

<span data-ttu-id="752d9-287">在 Windows Mixed Reality 中，音訊引擎提供混合現實體驗的以聽覺方式元件，方法是使用方向、距離和環境模擬來模擬3D 音效。</span><span class="sxs-lookup"><span data-stu-id="752d9-287">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="752d9-288">在應用程式中使用空間音效，可以讓開發人員 convincingly 在使用者周圍，以3維空間（球體）來放置聲音。</span><span class="sxs-lookup"><span data-stu-id="752d9-288">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="752d9-289">這些聽起來好像是來自實際的實體物件，或是使用者周圍的混合現實全息。</span><span class="sxs-lookup"><span data-stu-id="752d9-289">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="752d9-290">空間音效是強大的工具，可在混合現實應用程式中進行深度、協助工具及 UX 設計。</span><span class="sxs-lookup"><span data-stu-id="752d9-290">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="752d9-291">裝置影響</span><span class="sxs-lookup"><span data-stu-id="752d9-291">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="752d9-292"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="752d9-292"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="752d9-293"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="752d9-293"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="752d9-294">✔️</span><span class="sxs-lookup"><span data-stu-id="752d9-294">✔️</span></span></td>
        <td><span data-ttu-id="752d9-295">✔️</span><span class="sxs-lookup"><span data-stu-id="752d9-295">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="752d9-296">品質準則</span><span class="sxs-lookup"><span data-stu-id="752d9-296">Quality criteria</span></span>

|  <span data-ttu-id="752d9-297">效果</span><span class="sxs-lookup"><span data-stu-id="752d9-297">Best</span></span>  |  <span data-ttu-id="752d9-298">遇到</span><span class="sxs-lookup"><span data-stu-id="752d9-298">Meets</span></span> |  <span data-ttu-id="752d9-299">無法</span><span class="sxs-lookup"><span data-stu-id="752d9-299">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="752d9-300">音效會以邏輯方式 hrtf，而 UX 會適當地使用音效來協助物件探索和使用者意見反應。</span><span class="sxs-lookup"><span data-stu-id="752d9-300">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="752d9-301">音效是自然且與物件相關，並會在案例中正規化。</span><span class="sxs-lookup"><span data-stu-id="752d9-301">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="752d9-302">空間音訊會適當地用於 believability，但缺少以協助使用者提供意見反應和發現。</span><span class="sxs-lookup"><span data-stu-id="752d9-302">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="752d9-303">音效不會如預期般 hrtf，也不會有聲音可協助使用者在 UX 中。</span><span class="sxs-lookup"><span data-stu-id="752d9-303">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="752d9-304">或在案例的設計中未考慮或使用空間音訊。</span><span class="sxs-lookup"><span data-stu-id="752d9-304">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="752d9-305">如何測量</span><span class="sxs-lookup"><span data-stu-id="752d9-305">How to measure</span></span>

* <span data-ttu-id="752d9-306">一般情況下，相關的音效應該從目標的全息影像發出（例如，從全像攝影狗的吠聲）。</span><span class="sxs-lookup"><span data-stu-id="752d9-306">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="752d9-307">在整個 UX 中都應該使用音效提示，以協助使用者對全像攝影框架以外的動作提供意見反應或認知。</span><span class="sxs-lookup"><span data-stu-id="752d9-307">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="752d9-308">建議事項</span><span class="sxs-lookup"><span data-stu-id="752d9-308">Recommendations</span></span>

* <span data-ttu-id="752d9-309">使用空間音訊來協助物件探索和使用者介面。</span><span class="sxs-lookup"><span data-stu-id="752d9-309">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="752d9-310">真實音效的效果優於合成或非自然音效。</span><span class="sxs-lookup"><span data-stu-id="752d9-310">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="752d9-311">大部分的音效都應該 hrtf。</span><span class="sxs-lookup"><span data-stu-id="752d9-311">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="752d9-312">避免隱藏的發射器。</span><span class="sxs-lookup"><span data-stu-id="752d9-312">Avoid invisible emitters.</span></span>
* <span data-ttu-id="752d9-313">避免空間遮罩。</span><span class="sxs-lookup"><span data-stu-id="752d9-313">Avoid spatial masking.</span></span>
* <span data-ttu-id="752d9-314">標準化所有聲音。</span><span class="sxs-lookup"><span data-stu-id="752d9-314">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="752d9-315">資源</span><span class="sxs-lookup"><span data-stu-id="752d9-315">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="752d9-316">文件</span><span class="sxs-lookup"><span data-stu-id="752d9-316">Documentation</span></span>

* [<span data-ttu-id="752d9-317">空間音效</span><span class="sxs-lookup"><span data-stu-id="752d9-317">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="752d9-318">空間音效設計</span><span class="sxs-lookup"><span data-stu-id="752d9-318">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="752d9-319">Unity 中的空間音效</span><span class="sxs-lookup"><span data-stu-id="752d9-319">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="752d9-320">案例研究，HoloTour 的空間音效</span><span class="sxs-lookup"><span data-stu-id="752d9-320">Case study, Spatial sound for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="752d9-321">案例研究，使用 RoboRaid 中的空間音效</span><span class="sxs-lookup"><span data-stu-id="752d9-321">Case study, Using spatial sound in RoboRaid</span></span>](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="752d9-322">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="752d9-322">Tools and tutorials</span></span>

* [<span data-ttu-id="752d9-323">MR 空間220：空間音效</span><span class="sxs-lookup"><span data-stu-id="752d9-323">MR Spatial 220: Spatial sound</span></span>](holograms-220.md)
* [<span data-ttu-id="752d9-324">MRToolkit，空間音訊</span><span class="sxs-lookup"><span data-stu-id="752d9-324">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="752d9-325">專注于全像攝影框架（FOV）界限</span><span class="sxs-lookup"><span data-stu-id="752d9-325">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="752d9-326">設計良好的使用者體驗，可以建立和維護虛擬環境的實用內容，以延伸使用者。</span><span class="sxs-lookup"><span data-stu-id="752d9-326">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="752d9-327">緩和 FOV 界限的效果牽涉到內容規模和內容的精心設計，使用空間音訊、指引系統和使用者的位置。</span><span class="sxs-lookup"><span data-stu-id="752d9-327">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="752d9-328">如果正確，使用者會覺得 FOV 界限不會受到影響，同時具備舒適的應用程式體驗。</span><span class="sxs-lookup"><span data-stu-id="752d9-328">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="752d9-329">裝置影響</span><span class="sxs-lookup"><span data-stu-id="752d9-329">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="752d9-330"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="752d9-330"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="752d9-331"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="752d9-331"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="752d9-332">✔️</span><span class="sxs-lookup"><span data-stu-id="752d9-332">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="752d9-333">品質準則</span><span class="sxs-lookup"><span data-stu-id="752d9-333">Quality criteria</span></span>

|  <span data-ttu-id="752d9-334">效果</span><span class="sxs-lookup"><span data-stu-id="752d9-334">Best</span></span>  |  <span data-ttu-id="752d9-335">遇到</span><span class="sxs-lookup"><span data-stu-id="752d9-335">Meets</span></span> |  <span data-ttu-id="752d9-336">無法</span><span class="sxs-lookup"><span data-stu-id="752d9-336">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="752d9-337">使用者絕對不會失去內容，而且也很樂意進行觀看。</span><span class="sxs-lookup"><span data-stu-id="752d9-337">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="752d9-338">內容協助是針對大型物件所提供。</span><span class="sxs-lookup"><span data-stu-id="752d9-338">Context assistance is provided for large objects.</span></span> <span data-ttu-id="752d9-339">探索和流覽指引是針對框架外的物件所提供。</span><span class="sxs-lookup"><span data-stu-id="752d9-339">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="752d9-340">在一般情況下，動態影像的動作設計和縮放比例適用于熟悉的觀賞體驗。</span><span class="sxs-lookup"><span data-stu-id="752d9-340">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="752d9-341">使用者絕對不會失去內容，但是在有限的情況下可能需要額外的頸部動作。</span><span class="sxs-lookup"><span data-stu-id="752d9-341">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="752d9-342">在有限的情況下，調整會導致全息影像中斷垂直或水準框架，而導致一些頸部動作來觀看全息影像。</span><span class="sxs-lookup"><span data-stu-id="752d9-342">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="752d9-343">使用者可能會遺失內容和（或）一致的頸部動作，以查看全息影像。</span><span class="sxs-lookup"><span data-stu-id="752d9-343">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="752d9-344">大型的全像攝影物件沒有任何內容指引、在沒有發現性指引的框架外移動物件很容易遺失，或高度的全像投影需要週期性頸部動作來觀看。</span><span class="sxs-lookup"><span data-stu-id="752d9-344">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="752d9-345">如何測量</span><span class="sxs-lookup"><span data-stu-id="752d9-345">How to measure</span></span>

* <span data-ttu-id="752d9-346">（大型）全息的內容會因為在界限裁剪而遺失或無法瞭解。</span><span class="sxs-lookup"><span data-stu-id="752d9-346">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="752d9-347">因為缺乏注意的總監，或是快速移出全像攝影框架的內容，所以很難找到全息型的位置。</span><span class="sxs-lookup"><span data-stu-id="752d9-347">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="752d9-348">案例需要定期和重複的頭運動，才能完全看到全像疲勞的全息影像。</span><span class="sxs-lookup"><span data-stu-id="752d9-348">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="752d9-349">建議事項</span><span class="sxs-lookup"><span data-stu-id="752d9-349">Recommendations</span></span>

* <span data-ttu-id="752d9-350">以符合 FOV 的小型物件開始體驗，然後以視覺提示轉換成較大的版本。</span><span class="sxs-lookup"><span data-stu-id="752d9-350">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="752d9-351">使用空間音訊和注意總監，協助使用者尋找 FOV 外的內容。</span><span class="sxs-lookup"><span data-stu-id="752d9-351">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="752d9-352">盡可能避免以垂直方式裁剪 FOV 的全息影像。</span><span class="sxs-lookup"><span data-stu-id="752d9-352">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="752d9-353">提供使用者應用程式內的指引，以取得最佳的流覽位置。</span><span class="sxs-lookup"><span data-stu-id="752d9-353">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="752d9-354">資源</span><span class="sxs-lookup"><span data-stu-id="752d9-354">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="752d9-355">文件</span><span class="sxs-lookup"><span data-stu-id="752d9-355">Documentation</span></span>

* [<span data-ttu-id="752d9-356">全像攝影框架</span><span class="sxs-lookup"><span data-stu-id="752d9-356">Holographic frame</span></span>](holographic-frame.md)
* [<span data-ttu-id="752d9-357">案例研究，HoloStudio UI 和互動設計學習</span><span class="sxs-lookup"><span data-stu-id="752d9-357">Case Study, HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="752d9-358">物件和環境的規模</span><span class="sxs-lookup"><span data-stu-id="752d9-358">Scale of objects and environments</span></span>](scale.md)
* [<span data-ttu-id="752d9-359">游標，視覺提示</span><span class="sxs-lookup"><span data-stu-id="752d9-359">Cursors, Visual cues</span></span>](cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="752d9-360">外部參考</span><span class="sxs-lookup"><span data-stu-id="752d9-360">External references</span></span>

* [<span data-ttu-id="752d9-361">FOV 的許多 ado</span><span class="sxs-lookup"><span data-stu-id="752d9-361">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="752d9-362">使用者位置的內容反應</span><span class="sxs-lookup"><span data-stu-id="752d9-362">Content reacts to user position</span></span>

<span data-ttu-id="752d9-363">全息影像應該以「實際」物件的相同方式來回應使用者位置。</span><span class="sxs-lookup"><span data-stu-id="752d9-363">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="752d9-364">值得注意的設計考慮是 UI 元素，不一定會假設使用者的位置是固定的，而且會隨著使用者的動作而調整。</span><span class="sxs-lookup"><span data-stu-id="752d9-364">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="752d9-365">設計可正確適應使用者位置的應用程式，將會建立更可信的體驗，並讓您更容易使用。</span><span class="sxs-lookup"><span data-stu-id="752d9-365">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="752d9-366">裝置影響</span><span class="sxs-lookup"><span data-stu-id="752d9-366">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="752d9-367"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="752d9-367"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="752d9-368"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="752d9-368"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="752d9-369">✔️</span><span class="sxs-lookup"><span data-stu-id="752d9-369">✔️</span></span></td>
        <td><span data-ttu-id="752d9-370">✔️</span><span class="sxs-lookup"><span data-stu-id="752d9-370">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="752d9-371">品質準則</span><span class="sxs-lookup"><span data-stu-id="752d9-371">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="752d9-372">效果</span><span class="sxs-lookup"><span data-stu-id="752d9-372">Best</span></span> </td><td> <span data-ttu-id="752d9-373">內容和 UI 會適應使用者位置，讓使用者自然地與預期使用者移動範圍內的內容互動。</span><span class="sxs-lookup"><span data-stu-id="752d9-373">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="752d9-374">遇到</span><span class="sxs-lookup"><span data-stu-id="752d9-374">Meets</span></span> </td><td> <span data-ttu-id="752d9-375">UI 會配合使用者位置，但可能會妨礙需要使用者調整其位置的重要內容的觀點。</span><span class="sxs-lookup"><span data-stu-id="752d9-375">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="752d9-376">無法</span><span class="sxs-lookup"><span data-stu-id="752d9-376">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="752d9-377">UI 元素會在移動期間遺失或鎖定，導致使用者 unnaturally 返回（或尋找）控制項。</span><span class="sxs-lookup"><span data-stu-id="752d9-377">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="752d9-378">UI 元素會限制主要內容的顯示。</span><span class="sxs-lookup"><span data-stu-id="752d9-378">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="752d9-379">UI 移動不會針對觀看距離和動力而優化，特別是以<a href="billboarding-and-tag-along.md">標記為沿著</a>的 UI 元素。</span><span class="sxs-lookup"><span data-stu-id="752d9-379">UI movement is not optimized for viewing distance and momentum particularly with <a href="billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="752d9-380">如何測量</span><span class="sxs-lookup"><span data-stu-id="752d9-380">How to measure</span></span>

* <span data-ttu-id="752d9-381">所有的測量都應該在案例的合理範圍內完成。</span><span class="sxs-lookup"><span data-stu-id="752d9-381">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="752d9-382">雖然使用者移動會有所不同，但不會嘗試透過極端的使用者移動來誘騙應用程式。</span><span class="sxs-lookup"><span data-stu-id="752d9-382">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="752d9-383">針對 UI 元素，不論使用者移動為何，都應該可以使用相關的控制項。</span><span class="sxs-lookup"><span data-stu-id="752d9-383">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="752d9-384">例如，如果使用者正在觀看3D 地圖並使用 zoom 進行流覽，則無論位置為何，縮放控制項都應該隨時可供使用者使用。</span><span class="sxs-lookup"><span data-stu-id="752d9-384">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="752d9-385">建議事項</span><span class="sxs-lookup"><span data-stu-id="752d9-385">Recommendations</span></span>

* <span data-ttu-id="752d9-386">使用者是相機，並控制移動。</span><span class="sxs-lookup"><span data-stu-id="752d9-386">The user is the camera and they control the movement.</span></span> <span data-ttu-id="752d9-387">讓它們成為磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="752d9-387">Let them drive.</span></span>
* <span data-ttu-id="752d9-388">請考慮 billboarding 的文字和功能表系統，如果使用者想要四處移動，則會以世界鎖定或遮蔽的方式呈現。</span><span class="sxs-lookup"><span data-stu-id="752d9-388">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="752d9-389">針對需要追蹤使用者的內容使用標記，同時仍允許使用者查看其前面的內容。</span><span class="sxs-lookup"><span data-stu-id="752d9-389">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="752d9-390">資源</span><span class="sxs-lookup"><span data-stu-id="752d9-390">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="752d9-391">文件</span><span class="sxs-lookup"><span data-stu-id="752d9-391">Documentation</span></span>

* [<span data-ttu-id="752d9-392">互動設計</span><span class="sxs-lookup"><span data-stu-id="752d9-392">Interaction design</span></span>](hologram.md)
* [<span data-ttu-id="752d9-393">色彩、光線和材質</span><span class="sxs-lookup"><span data-stu-id="752d9-393">Color, light, and material</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="752d9-394">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="752d9-394">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="752d9-395">本能互動</span><span class="sxs-lookup"><span data-stu-id="752d9-395">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="752d9-396">自我移動和使用者 locomotion</span><span class="sxs-lookup"><span data-stu-id="752d9-396">Self-motion and user locomotion</span></span>](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="752d9-397">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="752d9-397">Tools and tutorials</span></span>

* [<span data-ttu-id="752d9-398">MR 輸入210：注視</span><span class="sxs-lookup"><span data-stu-id="752d9-398">MR Input 210: Gaze</span></span>](holograms-210.md)

## <a name="input-interaction-clarity"></a><span data-ttu-id="752d9-399">輸入互動清楚</span><span class="sxs-lookup"><span data-stu-id="752d9-399">Input interaction clarity</span></span>

<span data-ttu-id="752d9-400">輸入互動清楚是應用程式可用性的關鍵，並包含互動方法的輸入一致性、是多麼平易近人、可搜尋性。</span><span class="sxs-lookup"><span data-stu-id="752d9-400">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="752d9-401">使用者應該能夠在不重新的情況下，使用全平臺的通用互動。</span><span class="sxs-lookup"><span data-stu-id="752d9-401">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="752d9-402">如果應用程式具有自訂輸入，則應該清楚地溝通並示範。</span><span class="sxs-lookup"><span data-stu-id="752d9-402">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="752d9-403">裝置影響</span><span class="sxs-lookup"><span data-stu-id="752d9-403">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="752d9-404"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="752d9-404"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="752d9-405"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="752d9-405"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="752d9-406">✔️</span><span class="sxs-lookup"><span data-stu-id="752d9-406">✔️</span></span></td>
        <td><span data-ttu-id="752d9-407">✔️</span><span class="sxs-lookup"><span data-stu-id="752d9-407">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="752d9-408">品質準則</span><span class="sxs-lookup"><span data-stu-id="752d9-408">Quality criteria</span></span>

|  <span data-ttu-id="752d9-409">效果</span><span class="sxs-lookup"><span data-stu-id="752d9-409">Best</span></span>  |  <span data-ttu-id="752d9-410">遇到</span><span class="sxs-lookup"><span data-stu-id="752d9-410">Meets</span></span> |  <span data-ttu-id="752d9-411">無法</span><span class="sxs-lookup"><span data-stu-id="752d9-411">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="752d9-412">輸入互動方法與 Windows Mixed Reality 一致提供的[指引](interaction-fundamentals.md)。</span><span class="sxs-lookup"><span data-stu-id="752d9-412">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](interaction-fundamentals.md).</span></span> <span data-ttu-id="752d9-413">任何自訂輸入都不應該與標準輸入（而是使用標準互動）重複，而且必須清楚地傳達並向使用者示範。</span><span class="sxs-lookup"><span data-stu-id="752d9-413">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="752d9-414">與 [最佳] 類似，但自訂輸入與標準輸入方法是多餘的。</span><span class="sxs-lookup"><span data-stu-id="752d9-414">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="752d9-415">使用者仍可透過應用程式體驗達成目標和進度。</span><span class="sxs-lookup"><span data-stu-id="752d9-415">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="752d9-416">不易瞭解輸入法或按鈕對應。</span><span class="sxs-lookup"><span data-stu-id="752d9-416">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="752d9-417">輸入會經過大量自訂，不支援標準輸入、無指示，或可能導致疲勞和緩和問題。</span><span class="sxs-lookup"><span data-stu-id="752d9-417">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="752d9-418">如何測量</span><span class="sxs-lookup"><span data-stu-id="752d9-418">How to measure</span></span>

* <span data-ttu-id="752d9-419">應用程式會使用一致的[標準輸入方法。](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="752d9-419">The app uses consistent [standard input methods.](interaction-fundamentals.md)</span></span>
* <span data-ttu-id="752d9-420">如果應用程式具有自訂輸入，則會透過下列方式清楚地進行通訊：</span><span class="sxs-lookup"><span data-stu-id="752d9-420">If the app has custom input, it is clearly communicated through:</span></span>
* <span data-ttu-id="752d9-421">首次執行體驗</span><span class="sxs-lookup"><span data-stu-id="752d9-421">First-run experience</span></span>
* <span data-ttu-id="752d9-422">簡介畫面</span><span class="sxs-lookup"><span data-stu-id="752d9-422">Introductory screens</span></span>
* <span data-ttu-id="752d9-423">工具提示</span><span class="sxs-lookup"><span data-stu-id="752d9-423">Tooltips</span></span>
* <span data-ttu-id="752d9-424">手動教練</span><span class="sxs-lookup"><span data-stu-id="752d9-424">Hand coach</span></span>
* <span data-ttu-id="752d9-425">說明區段</span><span class="sxs-lookup"><span data-stu-id="752d9-425">Help section</span></span>
* <span data-ttu-id="752d9-426">聲音結束</span><span class="sxs-lookup"><span data-stu-id="752d9-426">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="752d9-427">建議事項</span><span class="sxs-lookup"><span data-stu-id="752d9-427">Recommendations</span></span>

* <span data-ttu-id="752d9-428">盡可能使用標準輸入方法。</span><span class="sxs-lookup"><span data-stu-id="752d9-428">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="752d9-429">提供非標準輸入法的示範、教學課程和工具提示。</span><span class="sxs-lookup"><span data-stu-id="752d9-429">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="752d9-430">在整個應用程式中使用一致的互動模型。</span><span class="sxs-lookup"><span data-stu-id="752d9-430">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="752d9-431">資源</span><span class="sxs-lookup"><span data-stu-id="752d9-431">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="752d9-432">文件</span><span class="sxs-lookup"><span data-stu-id="752d9-432">Documentation</span></span>

* [<span data-ttu-id="752d9-433">本能互動</span><span class="sxs-lookup"><span data-stu-id="752d9-433">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="752d9-434">可互動物件</span><span class="sxs-lookup"><span data-stu-id="752d9-434">Interactable objects</span></span>](interactable-object.md)
* [<span data-ttu-id="752d9-435">頭部目光和停駐</span><span class="sxs-lookup"><span data-stu-id="752d9-435">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="752d9-436">游標</span><span class="sxs-lookup"><span data-stu-id="752d9-436">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="752d9-437">舒適和注視</span><span class="sxs-lookup"><span data-stu-id="752d9-437">Comfort and gaze</span></span>](comfort.md#gaze-direction)
* [<span data-ttu-id="752d9-438">語音輸入</span><span class="sxs-lookup"><span data-stu-id="752d9-438">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="752d9-439">運動控制器</span><span class="sxs-lookup"><span data-stu-id="752d9-439">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="752d9-440">Unity 的輸入移植指南</span><span class="sxs-lookup"><span data-stu-id="752d9-440">Input porting guide for Unity</span></span>](input-porting-guide-for-unity.md)
* [<span data-ttu-id="752d9-441">Unity 中的鍵盤輸入</span><span class="sxs-lookup"><span data-stu-id="752d9-441">Keyboard input in Unity</span></span>](keyboard-input-in-unity.md)
* [<span data-ttu-id="752d9-442">Unity 中的目光</span><span class="sxs-lookup"><span data-stu-id="752d9-442">Gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="752d9-443">Unity 中的筆勢和運動控制器</span><span class="sxs-lookup"><span data-stu-id="752d9-443">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="752d9-444">Unity 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="752d9-444">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="752d9-445">DirectX 中的鍵盤、滑鼠及控制器輸入</span><span class="sxs-lookup"><span data-stu-id="752d9-445">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="752d9-446">DirectX 中的頭部和眼睛目光</span><span class="sxs-lookup"><span data-stu-id="752d9-446">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="752d9-447">DirectX 中的手部和運動控制器</span><span class="sxs-lookup"><span data-stu-id="752d9-447">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="752d9-448">DirectX 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="752d9-448">Voice input in DirectX</span></span>](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="752d9-449">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="752d9-449">Tools and tutorials</span></span>

* [<span data-ttu-id="752d9-450">案例研究：對更個人運算的追求</span><span class="sxs-lookup"><span data-stu-id="752d9-450">Case study: The pursuit of more personal computing</span></span>](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="752d9-451">轉換研究： HoloStudio UI 和互動設計學習</span><span class="sxs-lookup"><span data-stu-id="752d9-451">Cast study: HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="752d9-452">範例應用程式：元素的定期資料表</span><span class="sxs-lookup"><span data-stu-id="752d9-452">Sample app: Periodic table of the elements</span></span>](periodic-table-of-the-elements.md)
* [<span data-ttu-id="752d9-453">範例應用程式：農曆模組</span><span class="sxs-lookup"><span data-stu-id="752d9-453">Sample app: Lunar module</span></span>](lunar-module.md)
* [<span data-ttu-id="752d9-454">MR 輸入210：注視</span><span class="sxs-lookup"><span data-stu-id="752d9-454">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="752d9-455">MR 輸入211：手勢</span><span class="sxs-lookup"><span data-stu-id="752d9-455">MR Input 211: Gestures</span></span>](holograms-211.md)
* [<span data-ttu-id="752d9-456">MR 輸入212：語音</span><span class="sxs-lookup"><span data-stu-id="752d9-456">MR Input 212: Voice</span></span>](holograms-212.md)

## <a name="interactable-objects"></a><span data-ttu-id="752d9-457">可互動物件</span><span class="sxs-lookup"><span data-stu-id="752d9-457">Interactable objects</span></span>

<span data-ttu-id="752d9-458">一個按鈕很長的比喻，是用來觸發2D 抽象世界中的事件。</span><span class="sxs-lookup"><span data-stu-id="752d9-458">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="752d9-459">在三維混合現實世界中，我們不再需要局限于此抽象概念。</span><span class="sxs-lookup"><span data-stu-id="752d9-459">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="752d9-460">任何專案都可以是觸發事件的可互動物件。</span><span class="sxs-lookup"><span data-stu-id="752d9-460">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="752d9-461">可互動物件可以從資料表上的咖啡杯，呈現為以空中浮動的球形文字。</span><span class="sxs-lookup"><span data-stu-id="752d9-461">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="752d9-462">不論表單為何，使用者都應該透過視覺和音訊提示清楚地辨識可互動物件。</span><span class="sxs-lookup"><span data-stu-id="752d9-462">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="752d9-463">裝置影響</span><span class="sxs-lookup"><span data-stu-id="752d9-463">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="752d9-464"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="752d9-464"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="752d9-465"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="752d9-465"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="752d9-466">✔️</span><span class="sxs-lookup"><span data-stu-id="752d9-466">✔️</span></span></td>
        <td><span data-ttu-id="752d9-467">✔️</span><span class="sxs-lookup"><span data-stu-id="752d9-467">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="752d9-468">品質準則</span><span class="sxs-lookup"><span data-stu-id="752d9-468">Quality criteria</span></span>

|  <span data-ttu-id="752d9-469">效果</span><span class="sxs-lookup"><span data-stu-id="752d9-469">Best</span></span>  |  <span data-ttu-id="752d9-470">遇到</span><span class="sxs-lookup"><span data-stu-id="752d9-470">Meets</span></span> |  <span data-ttu-id="752d9-471">無法</span><span class="sxs-lookup"><span data-stu-id="752d9-471">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="752d9-472">不論何種形式，可互動物件都可以透過三個狀態的視覺和音訊提示來辨識： [閒置]、[目標] 和 [已選取]。</span><span class="sxs-lookup"><span data-stu-id="752d9-472">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="752d9-473">「瞭解這一點」在整個經驗中都是清楚且一致的使用方式。</span><span class="sxs-lookup"><span data-stu-id="752d9-473">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="752d9-474">系統會縮放並散佈物件，以允許錯誤的目標。</span><span class="sxs-lookup"><span data-stu-id="752d9-474">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="752d9-475">使用者可以透過音訊或視覺效果的意見反應，將物件辨識為可互動，並可將物件設為目標並啟動。</span><span class="sxs-lookup"><span data-stu-id="752d9-475">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="752d9-476">若未提供視覺或音訊提示，使用者就無法辨識可互動物件。</span><span class="sxs-lookup"><span data-stu-id="752d9-476">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="752d9-477">互動因物件縮放或物件之間的距離而容易出錯。</span><span class="sxs-lookup"><span data-stu-id="752d9-477">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="752d9-478">如何測量</span><span class="sxs-lookup"><span data-stu-id="752d9-478">How to measure</span></span>

* <span data-ttu-id="752d9-479">可互動物件可辨識為 ' 可互動 ';包括按鈕、功能表和應用程式特定內容。</span><span class="sxs-lookup"><span data-stu-id="752d9-479">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="752d9-480">根據經驗法則，在以可互動物件為目標時，應該會有視覺和音訊提示。</span><span class="sxs-lookup"><span data-stu-id="752d9-480">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="752d9-481">建議事項</span><span class="sxs-lookup"><span data-stu-id="752d9-481">Recommendations</span></span>

* <span data-ttu-id="752d9-482">使用視覺效果和音訊意見反應進行互動。</span><span class="sxs-lookup"><span data-stu-id="752d9-482">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="752d9-483">應針對每個輸入狀態（[閒置]、[目標]、[已選取]）區分視覺效果意見反應</span><span class="sxs-lookup"><span data-stu-id="752d9-483">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="752d9-484">可互動物件應調整並放置於錯誤的目標上。</span><span class="sxs-lookup"><span data-stu-id="752d9-484">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="752d9-485">群組的可互動物件（例如功能表列或清單）應具有適當的目標間距。</span><span class="sxs-lookup"><span data-stu-id="752d9-485">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="752d9-486">支援語音命令的按鈕和功能表應該提供命令關鍵字的文字標籤（「請參閱它」）</span><span class="sxs-lookup"><span data-stu-id="752d9-486">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="752d9-487">資源</span><span class="sxs-lookup"><span data-stu-id="752d9-487">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="752d9-488">文件</span><span class="sxs-lookup"><span data-stu-id="752d9-488">Documentation</span></span>

* [<span data-ttu-id="752d9-489">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="752d9-489">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="752d9-490">Unity 中的文字</span><span class="sxs-lookup"><span data-stu-id="752d9-490">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="752d9-491">週框方塊和應用程式列</span><span class="sxs-lookup"><span data-stu-id="752d9-491">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="752d9-492">語音輸入</span><span class="sxs-lookup"><span data-stu-id="752d9-492">Voice input</span></span>](voice-input.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="752d9-493">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="752d9-493">Tools and tutorials</span></span>

* [<span data-ttu-id="752d9-494">混合現實工具組-UX</span><span class="sxs-lookup"><span data-stu-id="752d9-494">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="752d9-495">房間掃描</span><span class="sxs-lookup"><span data-stu-id="752d9-495">Room scanning</span></span>

<span data-ttu-id="752d9-496">需要空間對應資料的應用程式會依賴裝置，在使用者探索其在使用中裝置的環境時，于一段時間內自動收集此資料。</span><span class="sxs-lookup"><span data-stu-id="752d9-496">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="752d9-497">此資料的完整性和品質取決於數個因素，包括使用者已完成的探索量、流覽後經過的時間，以及設備（例如傢俱和門）在掃描區域之後是否已移動。</span><span class="sxs-lookup"><span data-stu-id="752d9-497">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="752d9-498">許多應用程式會在體驗開始時分析空間對應資料，以判斷使用者是否應該執行額外的步驟來改善空間對應的完整性和品質。</span><span class="sxs-lookup"><span data-stu-id="752d9-498">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="752d9-499">如果需要使用者掃描環境，請在掃描體驗期間提供清楚的指引。</span><span class="sxs-lookup"><span data-stu-id="752d9-499">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="752d9-500">裝置影響</span><span class="sxs-lookup"><span data-stu-id="752d9-500">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="752d9-501"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="752d9-501"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="752d9-502"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="752d9-502"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="752d9-503">✔️</span><span class="sxs-lookup"><span data-stu-id="752d9-503">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="752d9-504">品質準則</span><span class="sxs-lookup"><span data-stu-id="752d9-504">Quality criteria</span></span>

|  <span data-ttu-id="752d9-505">效果</span><span class="sxs-lookup"><span data-stu-id="752d9-505">Best</span></span>  |  <span data-ttu-id="752d9-506">遇到</span><span class="sxs-lookup"><span data-stu-id="752d9-506">Meets</span></span> |  <span data-ttu-id="752d9-507">無法</span><span class="sxs-lookup"><span data-stu-id="752d9-507">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="752d9-508">空間網格的視覺效果會告訴使用者掃描正在進行中。</span><span class="sxs-lookup"><span data-stu-id="752d9-508">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="752d9-509">使用者清楚知道要執行的動作，以及掃描開始和停止的時間。</span><span class="sxs-lookup"><span data-stu-id="752d9-509">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="752d9-510">提供空間網格的視覺效果，但使用者可能無法清楚瞭解該怎麼做，而且不會提供任何進度資訊。</span><span class="sxs-lookup"><span data-stu-id="752d9-510">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="752d9-511">沒有網格的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="752d9-511">No visualization of mesh.</span></span> <span data-ttu-id="752d9-512">沒有提供指引資訊給使用者關於要查看的位置，或掃描開始/停止的時間。</span><span class="sxs-lookup"><span data-stu-id="752d9-512">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="752d9-513">如何測量</span><span class="sxs-lookup"><span data-stu-id="752d9-513">How to measure</span></span>

* <span data-ttu-id="752d9-514">在進行必要的房間掃描時，會提供視覺和音訊指引，指出要查看的位置，以及開始和停止掃描的時機。</span><span class="sxs-lookup"><span data-stu-id="752d9-514">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="752d9-515">建議事項</span><span class="sxs-lookup"><span data-stu-id="752d9-515">Recommendations</span></span>

* <span data-ttu-id="752d9-516">指出使用者鄰近範圍中的總數量必須是體驗的一部分。</span><span class="sxs-lookup"><span data-stu-id="752d9-516">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="752d9-517">當掃描開始並停止（例如進度指示器）時進行通訊。</span><span class="sxs-lookup"><span data-stu-id="752d9-517">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="752d9-518">在掃描期間使用網格的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="752d9-518">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="752d9-519">提供視覺和音訊提示，以鼓勵使用者在房間周圍尋找並移動。</span><span class="sxs-lookup"><span data-stu-id="752d9-519">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="752d9-520">通知使用者要在哪裡改善資料。</span><span class="sxs-lookup"><span data-stu-id="752d9-520">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="752d9-521">在許多情況下，最好告訴使用者需要執行的動作（例如，查看 [傢俱] 的上限），以便取得所需的掃描品質。</span><span class="sxs-lookup"><span data-stu-id="752d9-521">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="752d9-522">資源</span><span class="sxs-lookup"><span data-stu-id="752d9-522">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="752d9-523">文件</span><span class="sxs-lookup"><span data-stu-id="752d9-523">Documentation</span></span>

* [<span data-ttu-id="752d9-524">空間位置掃描視覺效果</span><span class="sxs-lookup"><span data-stu-id="752d9-524">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="752d9-525">案例研究：擴充 HoloLens 的空間對應功能</span><span class="sxs-lookup"><span data-stu-id="752d9-525">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="752d9-526">案例研究： HoloTour 的空間音效設計</span><span class="sxs-lookup"><span data-stu-id="752d9-526">Case study: Spatial sound design for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="752d9-527">案例研究：在片段中建立沉浸式體驗</span><span class="sxs-lookup"><span data-stu-id="752d9-527">Case study: Creating an immersive experience in Fragments</span></span>](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="752d9-528">工具和教學課程</span><span class="sxs-lookup"><span data-stu-id="752d9-528">Tools and tutorials</span></span>

* [<span data-ttu-id="752d9-529">混合現實工具組-UX</span><span class="sxs-lookup"><span data-stu-id="752d9-529">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="752d9-530">方向指標</span><span class="sxs-lookup"><span data-stu-id="752d9-530">Directional indicators</span></span>

<span data-ttu-id="752d9-531">在混合現實應用程式中，內容可能會在 pixels occluded 的欄位之外，或由真實世界的物件所組成。</span><span class="sxs-lookup"><span data-stu-id="752d9-531">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="752d9-532">設計良好的應用程式可讓使用者更輕鬆地尋找不可見的內容。</span><span class="sxs-lookup"><span data-stu-id="752d9-532">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="752d9-533">方向指標會向使用者通知重要內容，並提供相對於使用者位置的內容指引。</span><span class="sxs-lookup"><span data-stu-id="752d9-533">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="752d9-534">非可見內容的指引可以採用音效發射器、方向箭號或直接視覺提示的形式。</span><span class="sxs-lookup"><span data-stu-id="752d9-534">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="752d9-535">裝置影響</span><span class="sxs-lookup"><span data-stu-id="752d9-535">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="752d9-536"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="752d9-536"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="752d9-537"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="752d9-537"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="752d9-538">✔️</span><span class="sxs-lookup"><span data-stu-id="752d9-538">✔️</span></span></td>
        <td><span data-ttu-id="752d9-539">✔️</span><span class="sxs-lookup"><span data-stu-id="752d9-539">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="752d9-540">品質準則</span><span class="sxs-lookup"><span data-stu-id="752d9-540">Quality criteria</span></span>

|  <span data-ttu-id="752d9-541">效果</span><span class="sxs-lookup"><span data-stu-id="752d9-541">Best</span></span>  |  <span data-ttu-id="752d9-542">遇到</span><span class="sxs-lookup"><span data-stu-id="752d9-542">Meets</span></span> |  <span data-ttu-id="752d9-543">無法</span><span class="sxs-lookup"><span data-stu-id="752d9-543">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="752d9-544">視覺效果和音訊提示會直接引導使用者前往視圖欄位以外的相關內容。</span><span class="sxs-lookup"><span data-stu-id="752d9-544">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="752d9-545">箭號或某個指標，會以內容的一般方向來指向使用者。</span><span class="sxs-lookup"><span data-stu-id="752d9-545">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="752d9-546">相關內容不在視野的範圍內，也不會提供不佳的位置指引給使用者。</span><span class="sxs-lookup"><span data-stu-id="752d9-546">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="752d9-547">如何測量</span><span class="sxs-lookup"><span data-stu-id="752d9-547">How to measure</span></span>

* <span data-ttu-id="752d9-548">[使用者] 欄位以外的相關內容可透過視覺效果和/或音訊提示來進行探索。</span><span class="sxs-lookup"><span data-stu-id="752d9-548">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="752d9-549">建議事項</span><span class="sxs-lookup"><span data-stu-id="752d9-549">Recommendations</span></span>

* <span data-ttu-id="752d9-550">當相關內容超出使用者的視圖欄位時，請使用方向指標和音訊提示來引導使用者進行內容。</span><span class="sxs-lookup"><span data-stu-id="752d9-550">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="752d9-551">在許多情況下，直接視覺輔助線優先于方向箭號。</span><span class="sxs-lookup"><span data-stu-id="752d9-551">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="752d9-552">方向指標不應內建至游標處。</span><span class="sxs-lookup"><span data-stu-id="752d9-552">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="752d9-553">資源</span><span class="sxs-lookup"><span data-stu-id="752d9-553">Resources</span></span>

* [<span data-ttu-id="752d9-554">全像攝影框架</span><span class="sxs-lookup"><span data-stu-id="752d9-554">Holographic frame</span></span>](holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="752d9-555">資料載入</span><span class="sxs-lookup"><span data-stu-id="752d9-555">Data loading</span></span>

<span data-ttu-id="752d9-556">進度控制項為使用者提供回饋，告知正在進行長時間執行的操作。</span><span class="sxs-lookup"><span data-stu-id="752d9-556">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="752d9-557">這可能表示當進度指示器可見時，使用者無法與應用程式互動，也可以指出等候時間可能是多久。</span><span class="sxs-lookup"><span data-stu-id="752d9-557">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="752d9-558">裝置影響</span><span class="sxs-lookup"><span data-stu-id="752d9-558">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="752d9-559"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="752d9-559"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="752d9-560"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="752d9-560"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="752d9-561">✔️</span><span class="sxs-lookup"><span data-stu-id="752d9-561">✔️</span></span></td>
        <td><span data-ttu-id="752d9-562">✔️</span><span class="sxs-lookup"><span data-stu-id="752d9-562">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="752d9-563">品質準則</span><span class="sxs-lookup"><span data-stu-id="752d9-563">Quality criteria</span></span>

|  <span data-ttu-id="752d9-564">效果</span><span class="sxs-lookup"><span data-stu-id="752d9-564">Best</span></span>  |  <span data-ttu-id="752d9-565">遇到</span><span class="sxs-lookup"><span data-stu-id="752d9-565">Meets</span></span> |  <span data-ttu-id="752d9-566">無法</span><span class="sxs-lookup"><span data-stu-id="752d9-566">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="752d9-567">以進度列或環形形式呈現的動畫視覺指標，顯示任何資料載入或處理期間的進度。</span><span class="sxs-lookup"><span data-stu-id="752d9-567">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="752d9-568">視覺指標會提供等待時間長度的指引。</span><span class="sxs-lookup"><span data-stu-id="752d9-568">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="752d9-569">使用者會收到資料載入正在進行中的通知，但不會指出等候的時間長度。</span><span class="sxs-lookup"><span data-stu-id="752d9-569">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="752d9-570">工作所花費的時間超過5秒的資料載入或處理指示器。</span><span class="sxs-lookup"><span data-stu-id="752d9-570">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="752d9-571">如何測量</span><span class="sxs-lookup"><span data-stu-id="752d9-571">How to measure</span></span>

* <span data-ttu-id="752d9-572">在資料載入期間，確認不會有超過5秒的空白狀態。</span><span class="sxs-lookup"><span data-stu-id="752d9-572">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="752d9-573">建議事項</span><span class="sxs-lookup"><span data-stu-id="752d9-573">Recommendations</span></span>

* <span data-ttu-id="752d9-574">當使用者可能會感覺到此應用程式停止或損毀時，請提供資料載入 animator，以顯示任何情況下的進度。</span><span class="sxs-lookup"><span data-stu-id="752d9-574">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="752d9-575">合理的經驗法則是任何可能需要5秒以上的「載入」活動。</span><span class="sxs-lookup"><span data-stu-id="752d9-575">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="752d9-576">資源</span><span class="sxs-lookup"><span data-stu-id="752d9-576">Resources</span></span>

* [<span data-ttu-id="752d9-577">顯示進度</span><span class="sxs-lookup"><span data-stu-id="752d9-577">Displaying progress</span></span>](progress.md)
