---
title: OpenXR 最佳作法
description: 瞭解 OpenXR 應用程式的視覺品質、穩定性和效能最佳做法。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR，Khronos，BasicXRApp，DirectX，原生，原生應用程式，自訂引擎，中介軟體，最佳做法，效能，品質，穩定性
ms.openlocfilehash: 0a0bbd37521be52ec328b4f32e53969c0ec7fef4
ms.sourcegitcommit: 46bd1a56d272a5880f410751fa8429d65d816431
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2020
ms.locfileid: "80549362"
---
# <a name="openxr-app-best-practices"></a><span data-ttu-id="ecf65-104">OpenXR 應用程式最佳做法</span><span class="sxs-lookup"><span data-stu-id="ecf65-104">OpenXR app best practices</span></span>

<span data-ttu-id="ecf65-105">您可以在<a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>的 OpenXRProgram .cpp 檔案中查看下列最佳做法的範例。</span><span class="sxs-lookup"><span data-stu-id="ecf65-105">You can see an example of the best practices below in <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>'s OpenXRProgram.cpp file.</span></span> <span data-ttu-id="ecf65-106">開頭的 Run （）函式會從初始化到事件和轉譯迴圈，捕獲一般的 OpenXR 應用程式代碼流程。</span><span class="sxs-lookup"><span data-stu-id="ecf65-106">The Run() function at the beginning captures a typical OpenXR app code flow from initialization to the event and rendering loop.</span></span>

## <a name="best-practices-for-visual-quality-and-stability"></a><span data-ttu-id="ecf65-107">視覺品質和穩定性的最佳做法</span><span class="sxs-lookup"><span data-stu-id="ecf65-107">Best practices for visual quality and stability</span></span>

<span data-ttu-id="ecf65-108">本節中的最佳作法說明如何在任何 OpenXR 應用程式中取得最佳的視覺品質和穩定性。</span><span class="sxs-lookup"><span data-stu-id="ecf65-108">The best practices in this section describe how to get the best visual quality and stability in any OpenXR application.</span></span>

<span data-ttu-id="ecf65-109">如需 HoloLens 2 特定的進一步效能建議，請參閱下面的[hololens 2 的最佳效能做法](#best-practices-for-performance-on-hololens-2)一節。</span><span class="sxs-lookup"><span data-stu-id="ecf65-109">For further performance recommendations specific to HoloLens 2, see the [Best practices for performance on HoloLens 2](#best-practices-for-performance-on-hololens-2) section below.</span></span>

### <a name="gamma-correct-rendering"></a><span data-ttu-id="ecf65-110">Gamma-正確呈現</span><span class="sxs-lookup"><span data-stu-id="ecf65-110">Gamma-correct rendering</span></span>

<span data-ttu-id="ecf65-111">請務必小心，以確保您的轉譯管線是 gamma 正確的。</span><span class="sxs-lookup"><span data-stu-id="ecf65-111">Care must be taken to ensure that your rendering pipeline is gamma-correct.</span></span> <span data-ttu-id="ecf65-112">當轉譯為 swapchain 時，轉譯目標視圖格式應符合 swapchain 格式（例如，swapchain 格式和轉譯目標視圖的 `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB`）。</span><span class="sxs-lookup"><span data-stu-id="ecf65-112">When rendering to a swapchain, the render-target view format should match the swapchain format (e.g. `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` for both the swapchain format and the render-target view).</span></span>
<span data-ttu-id="ecf65-113">例外狀況是，如果應用程式的轉譯管線在著色器程式碼中執行手動的 sRGB 轉換，在這種情況下，應用程式應該要求 sRGB swapchain 格式，但針對轉譯目標視圖使用線性格式（例如，要求 `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` 做為 swapchain 格式，但使用 `DXGI_FORMAT_B8G8R8A8_UNORM` 做為轉譯目標視圖），以避免將內容的雙 gamma 更正。</span><span class="sxs-lookup"><span data-stu-id="ecf65-113">The exception is if the app's rendering pipeline does a manual sRGB conversion in shader code, in which case the app should request an sRGB swapchain format but use the linear format for the render-target view (e.g. request `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` as the swapchain format but use `DXGI_FORMAT_B8G8R8A8_UNORM` as the render-target view) to prevent content from being double-gamma corrected.</span></span>

### <a name="submit-depth-buffer-for-projection-layers"></a><span data-ttu-id="ecf65-114">提交預測層的深度緩衝區</span><span class="sxs-lookup"><span data-stu-id="ecf65-114">Submit depth buffer for projection layers</span></span>

<span data-ttu-id="ecf65-115">提交框架以 `xrEndFrame`時，請一律使用 `XR_KHR_composition_layer_depth` 延伸模組，並連同投影層一起提交深度緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ecf65-115">Always use `XR_KHR_composition_layer_depth` extension and submit the depth buffer together with the projection layer when submitting a frame to `xrEndFrame`.</span></span>
<span data-ttu-id="ecf65-116">這會藉由啟用 HoloLens 2 上的硬體深度 reprojection，來改善全像全息的穩定性。</span><span class="sxs-lookup"><span data-stu-id="ecf65-116">This improves hologram stability by enabling hardware depth reprojection on HoloLens 2.</span></span>

### <a name="choose-a-reasonable-depth-range"></a><span data-ttu-id="ecf65-117">選擇合理的深度範圍</span><span class="sxs-lookup"><span data-stu-id="ecf65-117">Choose a reasonable depth range</span></span>

<span data-ttu-id="ecf65-118">偏好較窄的深度範圍來界定虛擬內容的範圍，以協助在 HoloLens 上進行全息的穩定性。</span><span class="sxs-lookup"><span data-stu-id="ecf65-118">Prefer a narrower depth range to scope the virtual content to help hologram stability on HoloLens.</span></span>
<span data-ttu-id="ecf65-119">例如，OpenXrProgram 的範例是使用0.1 到20的計量。</span><span class="sxs-lookup"><span data-stu-id="ecf65-119">For example, the OpenXrProgram.cpp sample is using 0.1 to 20 meters.</span></span>
<span data-ttu-id="ecf65-120">使用[反向-Z](https://developer.nvidia.com/content/depth-precision-visualized)可取得更統一的深度解析。</span><span class="sxs-lookup"><span data-stu-id="ecf65-120">Use [reversed-Z](https://developer.nvidia.com/content/depth-precision-visualized) for a more uniform depth resolution.</span></span>
<span data-ttu-id="ecf65-121">請注意，在 HoloLens 2 上，使用慣用的 `DXGI_FORMAT_D16_UNORM` 深度格式將有助於達到更佳的畫面播放速率和效能，雖然16位深度緩衝區比24位深度緩衝區提供的深度解析度較少。</span><span class="sxs-lookup"><span data-stu-id="ecf65-121">Note that, on HoloLens 2, using the preferred `DXGI_FORMAT_D16_UNORM` depth format will help achieve better frame rate and performance, although 16-bit depth buffers provide less depth resolution than 24-bit depth buffers.</span></span>
<span data-ttu-id="ecf65-122">因此，遵循這些最佳作法來充分利用深度解析，會變得更重要。</span><span class="sxs-lookup"><span data-stu-id="ecf65-122">Therefore, following these best practices to make best use of the depth resolution becomes more important.</span></span>

### <a name="prepare-for-different-environment-blend-modes"></a><span data-ttu-id="ecf65-123">為不同的環境 blend 模式做好準備</span><span class="sxs-lookup"><span data-stu-id="ecf65-123">Prepare for different environment blend modes</span></span>

<span data-ttu-id="ecf65-124">如果您的應用程式也會在完全封鎖世界的沉浸式耳機上執行，請務必使用 `xrEnumerateEnvironmentBlendModes` API 列舉支援的環境 blend 模式，並據以準備您的轉譯內容。</span><span class="sxs-lookup"><span data-stu-id="ecf65-124">If your application will also run on immersive headsets that completely block out the world, be sure to enumerate supported environment blend modes using `xrEnumerateEnvironmentBlendModes` API, and prepare your rendering content accordingly.</span></span>
<span data-ttu-id="ecf65-125">例如，對於具有 `XR_ENVIRONMENT_BLEND_MODE_ADDITIVE` 的系統（例如 HoloLens），應用程式應該使用透明的色彩，而針對具有 `XR_ENVIRONMENT_BLEND_MODE_OPAQUE`的系統，應用程式應該在背景轉譯一些不透明的色彩或部分虛擬空間。</span><span class="sxs-lookup"><span data-stu-id="ecf65-125">For example, for a system with `XR_ENVIRONMENT_BLEND_MODE_ADDITIVE` such as the HoloLens, the app should use transparent as the clear color, while for a system with `XR_ENVIRONMENT_BLEND_MODE_OPAQUE`, the app should render some opaque color or some virtual room in the background.</span></span>

### <a name="choose-unbounded-reference-space-as-applications-root-space"></a><span data-ttu-id="ecf65-126">選擇未系結的參考空間作為應用程式的根空間</span><span class="sxs-lookup"><span data-stu-id="ecf65-126">Choose unbounded reference space as application's root space</span></span>

<span data-ttu-id="ecf65-127">應用程式通常會建立一些根全局座標空間，以將視圖、動作和全息合併連接在一起。</span><span class="sxs-lookup"><span data-stu-id="ecf65-127">Applications typically establish some root world coordinate space to connect views, actions and holograms together.</span></span>
<span data-ttu-id="ecf65-128">當支援擴充功能來建立[全球規模座標系統](coordinate-systems.md#building-a-world-scale-experience)時，請使用 `XR_REFERENCE_SPACE_TYPE_UNBOUNDED_MSFT`，讓您的應用程式避免在使用者從應用程式啟動的位置往上移動（例如5米）時，不希望的全息影像漂移。</span><span class="sxs-lookup"><span data-stu-id="ecf65-128">Use `XR_REFERENCE_SPACE_TYPE_UNBOUNDED_MSFT` when the extension is supported to establish a [world-scale coordinate system](coordinate-systems.md#building-a-world-scale-experience), enabling your app to avoid undesired hologram drift when the user moves far (e.g. 5 meters away) from where the app starts.</span></span>
<span data-ttu-id="ecf65-129">如果未受限制的空間延伸模組不存在，請使用 `XR_REFERENCE_SPACE_TYPE_LOCAL` 做為回復。</span><span class="sxs-lookup"><span data-stu-id="ecf65-129">Use `XR_REFERENCE_SPACE_TYPE_LOCAL` as a fallback if the unbounded space extension doesn't exist.</span></span>

### <a name="associate-hologram-with-spatial-anchor"></a><span data-ttu-id="ecf65-130">將全息影像與空間錨點建立關聯</span><span class="sxs-lookup"><span data-stu-id="ecf65-130">Associate hologram with spatial anchor</span></span>

<span data-ttu-id="ecf65-131">使用未系結的參考空間時，您直接放在該參考空間中的全息影像，[可能會在使用者進入遙遠的房間時漂移，然後再回來](coordinate-systems.md#building-a-world-scale-experience)。</span><span class="sxs-lookup"><span data-stu-id="ecf65-131">When using an unbounded reference space, holograms you place directly in that reference space [may drift as the user walks to distant rooms and then comes back](coordinate-systems.md#building-a-world-scale-experience).</span></span>
<span data-ttu-id="ecf65-132">對於全息影像使用者，請使用 `xrCreateSpatialAnchorSpaceMSFT` 擴充功能來[建立空間錨點](spatial-anchors.md#best-practices)，並在其原點位置放置全息影像。</span><span class="sxs-lookup"><span data-stu-id="ecf65-132">For hologram users place at a discrete location in the world, [create a spatial anchor](spatial-anchors.md#best-practices) using the `xrCreateSpatialAnchorSpaceMSFT` extension function and position the hologram at its origin.</span></span>
<span data-ttu-id="ecf65-133">這會在一段時間後，讓該全息影像獨立穩定。</span><span class="sxs-lookup"><span data-stu-id="ecf65-133">That will keep that hologram independently stable over time.</span></span>

### <a name="support-mixed-reality-capture"></a><span data-ttu-id="ecf65-134">支援混合現實 capture</span><span class="sxs-lookup"><span data-stu-id="ecf65-134">Support mixed reality capture</span></span>

<span data-ttu-id="ecf65-135">雖然 HoloLens 2 的主要顯示器會使用加總的環境混合，當使用者起始[混合現實捕捉](mixed-reality-capture-for-developers.md)時，應用程式的轉譯內容會與環境影片串流進行 Alpha 混合。</span><span class="sxs-lookup"><span data-stu-id="ecf65-135">Although HoloLens 2's primary display uses additive environment blending, when the user initiates [mixed reality capture](mixed-reality-capture-for-developers.md), the app's rendering content will be alpha-blended with the environment video stream.</span></span>
<span data-ttu-id="ecf65-136">若要在混合現實 capture 影片中達到最佳的視覺品質，最好是在投影層的 `layerFlags`中設定 `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT`。</span><span class="sxs-lookup"><span data-stu-id="ecf65-136">To achieve the best visual quality in mixed reality capture videos, it's best to set the `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT` in your projection layer's `layerFlags`.</span></span>

## <a name="best-practices-for-performance-on-hololens-2"></a><span data-ttu-id="ecf65-137">HoloLens 2 上效能的最佳做法</span><span class="sxs-lookup"><span data-stu-id="ecf65-137">Best practices for performance on HoloLens 2</span></span>

<span data-ttu-id="ecf65-138">作為具有硬體 reprojection 支援的行動裝置，HoloLens 2 會有更嚴格的需求，以取得最佳效能。</span><span class="sxs-lookup"><span data-stu-id="ecf65-138">As a mobile device with hardware reprojection support, HoloLens 2 has stricter requirements to obtain optimal performance.</span></span>  <span data-ttu-id="ecf65-139">有數種方式可透過 `xrEndFrame` 提交組合資料，而這會導致後續處理，因而影響效能。</span><span class="sxs-lookup"><span data-stu-id="ecf65-139">There are a number of ways to submit composition data through `xrEndFrame` which will result in post-processing that will have a noticeable performance penalty.</span></span>

### <a name="select-a-swapchain-format"></a><span data-ttu-id="ecf65-140">選取 swapchain 格式</span><span class="sxs-lookup"><span data-stu-id="ecf65-140">Select a swapchain format</span></span>

<span data-ttu-id="ecf65-141">請一律使用 `xrEnumerateSwapchainFormats`列舉支援的像素格式，並從應用程式支援的執行時間選擇第一個色彩和深度像素格式，因為這是執行時間慣用的最佳效能。</span><span class="sxs-lookup"><span data-stu-id="ecf65-141">Always enumerate supported pixel formats using `xrEnumerateSwapchainFormats`, and choose the first color and depth pixel format from the runtime that the app supports, because that's what the runtime prefers for optimal performance.</span></span> <span data-ttu-id="ecf65-142">請注意，在 HoloLens 2 上，`DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` 和 `DXGI_FORMAT_D16_UNORM` 通常是達到更佳轉譯效能的第一種選擇。</span><span class="sxs-lookup"><span data-stu-id="ecf65-142">Note, on HoloLens 2, `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` and `DXGI_FORMAT_D16_UNORM` is typically the first choice to achieve better rendering performance.</span></span> <span data-ttu-id="ecf65-143">在桌上型電腦上執行的 VR 耳機上可能會有不同的喜好設定，其中24位深度緩衝區會降低效能影響。</span><span class="sxs-lookup"><span data-stu-id="ecf65-143">This preference can be different on VR headsets running on a Desktop PC, where 24-bit depth buffers have less of a performance impact.</span></span>
  
<span data-ttu-id="ecf65-144">**效能警告：** 使用主要 swapchain 色彩格式以外的格式會導致執行時間後置處理，這會造成顯著的效能影響。</span><span class="sxs-lookup"><span data-stu-id="ecf65-144">**Performance Warning:** Using a format other than the primary swapchain color format will result in runtime post-processing which comes at a significant performance penalty.</span></span>

### <a name="render-with-recommended-rendering-parameters-and-frame-timing"></a><span data-ttu-id="ecf65-145">使用建議的呈現參數和畫面格時間進行轉譯</span><span class="sxs-lookup"><span data-stu-id="ecf65-145">Render with recommended rendering parameters and frame timing</span></span>

<span data-ttu-id="ecf65-146">一律使用建議的視圖設定寬度/高度（`recommendedImageRectWidth` 和 `recommendedImageRectHeight` 從 `XrViewConfigurationView`）進行轉譯，並一律使用 `xrLocateViews` API 來查詢建議的視圖姿勢、fov 和其他轉譯參數，然後再呈現。</span><span class="sxs-lookup"><span data-stu-id="ecf65-146">Always render with the recommended view configuration width/height (`recommendedImageRectWidth` and `recommendedImageRectHeight` from `XrViewConfigurationView`), and always use `xrLocateViews` API to query for the recommended view pose, fov, and other rendering parameters before rendering.</span></span>
<span data-ttu-id="ecf65-147">查詢姿勢和 views 時，請一律使用最新 `xrWaitFrame` 呼叫中的 `XrFrameEndInfo.predictedDisplayTime`。</span><span class="sxs-lookup"><span data-stu-id="ecf65-147">Always use the `XrFrameEndInfo.predictedDisplayTime` from the latest `xrWaitFrame` call when querying for poses and views.</span></span>
<span data-ttu-id="ecf65-148">這可讓 HoloLens 針對正在戴 HoloLens 的人員調整呈現和優化視覺品質。</span><span class="sxs-lookup"><span data-stu-id="ecf65-148">This allows HoloLens to adjust rendering and optimize visual quality for the person who is wearing the HoloLens.</span></span>

### <a name="use-a-single-projection-layer"></a><span data-ttu-id="ecf65-149">使用單一投影圖層</span><span class="sxs-lookup"><span data-stu-id="ecf65-149">Use a single projection layer</span></span>

<span data-ttu-id="ecf65-150">HoloLens 2 的 GPU 電源有限，可讓應用程式轉譯內容和針對單一投影層優化的硬體組合器。</span><span class="sxs-lookup"><span data-stu-id="ecf65-150">HoloLens 2 has limited GPU power for applications to render content and a hardware compositor optimized for a single projection layer.</span></span>
<span data-ttu-id="ecf65-151">一律使用單一投影層可以協助應用程式的畫面播放速率、全息圖形穩定性和視覺品質。</span><span class="sxs-lookup"><span data-stu-id="ecf65-151">Always using a single projection layer can help the application's framerate, hologram stability and visual quality.</span></span>  
  
<span data-ttu-id="ecf65-152">**效能警告：** 提交任何專案，但單一保護層會導致執行時間後置處理，這會造成顯著的效能影響。</span><span class="sxs-lookup"><span data-stu-id="ecf65-152">**Performance Warning:** Submitting anything but a single protection layer will result in runtime post-processing which comes at a significant performance penalty.</span></span>

### <a name="render-with-texture-array-and-vprt"></a><span data-ttu-id="ecf65-153">使用材質陣列和 VPRT 呈現</span><span class="sxs-lookup"><span data-stu-id="ecf65-153">Render with texture array and VPRT</span></span>

<span data-ttu-id="ecf65-154">使用色彩 swapchain 的 `arraySize=2`，同時建立一個 `xrSwapchain` 以進行左右排列，另一種是深度。</span><span class="sxs-lookup"><span data-stu-id="ecf65-154">Create one `xrSwapchain` for both left and right eye using `arraySize=2` for color swapchain, and one for depth.</span></span>
<span data-ttu-id="ecf65-155">將視覺呈現到配量0，並將適當的眼轉譯為配量1。</span><span class="sxs-lookup"><span data-stu-id="ecf65-155">Render the left eye into slice 0 and the right eye into slice 1.</span></span>
<span data-ttu-id="ecf65-156">使用著色器搭配 VPRT 和實例繪製呼叫來進行 stereoscopic 轉譯，以將 GPU 負載降至最低。</span><span class="sxs-lookup"><span data-stu-id="ecf65-156">Use a shader with VPRT and instanced draw calls for stereoscopic rendering to minimize GPU load.</span></span>
<span data-ttu-id="ecf65-157">這也可讓執行時間的優化在 HoloLens 2 上達到最佳效能。</span><span class="sxs-lookup"><span data-stu-id="ecf65-157">This also enables the runtime's optimization to achieve the best performance on HoloLens 2.</span></span>
<span data-ttu-id="ecf65-158">使用材質陣列的替代方案（例如，每眼的雙重轉譯或個別的 swapchain）會導致執行時間後置處理，這會造成顯著的效能影響。</span><span class="sxs-lookup"><span data-stu-id="ecf65-158">Alternatives to using a texture array, such as double-wide rendering or a separate swapchain per eye, will result in runtime post-processing which comes at a significant performance penalty.</span></span>

### <a name="avoid-quad-layers"></a><span data-ttu-id="ecf65-159">避免四層</span><span class="sxs-lookup"><span data-stu-id="ecf65-159">Avoid quad layers</span></span>

<span data-ttu-id="ecf65-160">不是以 `XrCompositionLayerQuad`的組合層來提交四層，而是直接將四個內容轉譯成投射 swapchain。</span><span class="sxs-lookup"><span data-stu-id="ecf65-160">Rather than submitting quad layers as composition layers with `XrCompositionLayerQuad`, render the quad content directly into the projection swapchain.</span></span>

<span data-ttu-id="ecf65-161">**效能警告：** 提供超出單一預測層的額外層級（例如四層），會導致執行時間後置處理，而產生顯著的效能影響。</span><span class="sxs-lookup"><span data-stu-id="ecf65-161">**Performance Warning:** Providing additional layers beyond a single projection layer, such as quad layers, will result in runtime post-processing which comes at a significant performance penalty.</span></span>