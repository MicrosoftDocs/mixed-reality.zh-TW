---
title: 在 DirectX 中轉譯
description: 說明適用于 Windows Mixed Reality 的全像攝影轉譯。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，全息影像，轉譯，3D 圖形，HolographicFrame，轉譯迴圈，更新迴圈，逐步解說，範例程式碼，Direct3D
ms.openlocfilehash: 6b2e2dca9115d7093e94019d5ed91201f6ee3424
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375975"
---
# <a name="rendering-in-directx"></a><span data-ttu-id="63f0c-104">在 DirectX 中轉譯</span><span class="sxs-lookup"><span data-stu-id="63f0c-104">Rendering in DirectX</span></span>

<span data-ttu-id="63f0c-105">Windows Mixed Reality 建基於 DirectX，為使用者產生豐富的3D 圖形化體驗。</span><span class="sxs-lookup"><span data-stu-id="63f0c-105">Windows Mixed Reality is built on DirectX to produce rich, 3D graphical experiences for users.</span></span> <span data-ttu-id="63f0c-106">轉譯抽象化的功能就是 DirectX，讓應用程式有一或多個全像攝影場景的觀察者的位置和方向，如同系統所預測。</span><span class="sxs-lookup"><span data-stu-id="63f0c-106">The rendering abstraction sits just above DirectX and lets an app reason about the position and orientation of one or more observers of a holographic scene, as predicted by the system.</span></span> <span data-ttu-id="63f0c-107">然後，開發人員可以找到相對於每個相機的全息影像，讓應用程式在使用者四處移動時，在各種空間座標系統中轉譯這些全息影像。</span><span class="sxs-lookup"><span data-stu-id="63f0c-107">The developer can then locate their holograms relative to each camera, letting the app render these holograms in various spatial coordinate systems as the user moves around.</span></span>

<span data-ttu-id="63f0c-108">注意：本逐步解說說明 Direct3D 11 中的全像攝影轉譯。</span><span class="sxs-lookup"><span data-stu-id="63f0c-108">Note: This walkthrough describes holographic rendering in Direct3D 11.</span></span> <span data-ttu-id="63f0c-109">Direct3D 12 Windows Mixed Reality 應用程式範本也隨附于 Mixed Reality 應用程式範本延伸模組。</span><span class="sxs-lookup"><span data-stu-id="63f0c-109">A Direct3D 12 Windows Mixed Reality app template is also supplied with the Mixed Reality app templates extension.</span></span>

## <a name="update-for-the-current-frame"></a><span data-ttu-id="63f0c-110">目前畫面格的更新</span><span class="sxs-lookup"><span data-stu-id="63f0c-110">Update for the current frame</span></span>

<span data-ttu-id="63f0c-111">若要更新全息影像的應用程式狀態，每個畫面格一次，應用程式將會：</span><span class="sxs-lookup"><span data-stu-id="63f0c-111">To update the application state for holograms, once per frame the app will:</span></span>
* <span data-ttu-id="63f0c-112">從顯示管理系統取得<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 。</span><span class="sxs-lookup"><span data-stu-id="63f0c-112">Get a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> from the display management system.</span></span>
* <span data-ttu-id="63f0c-113">以目前的預測來更新場景，其中的相機視圖會在轉譯完成時顯示。</span><span class="sxs-lookup"><span data-stu-id="63f0c-113">Update the scene with the current prediction of where the camera view will be when render is completed.</span></span> <span data-ttu-id="63f0c-114">請注意，全像攝影場景可以有一個以上的相機。</span><span class="sxs-lookup"><span data-stu-id="63f0c-114">Note, there can be more than one camera for the holographic scene.</span></span>

<span data-ttu-id="63f0c-115">若要轉譯成全像攝影相機視圖，每個畫面格一次，應用程式將會：</span><span class="sxs-lookup"><span data-stu-id="63f0c-115">To render to holographic camera views, once per frame the app will:</span></span>
* <span data-ttu-id="63f0c-116">針對每個相機，使用系統中的相機視圖和投影矩陣，呈現目前框架的場景。</span><span class="sxs-lookup"><span data-stu-id="63f0c-116">For each camera, render the scene for the current frame, using the camera view and projection matrices from the system.</span></span>

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a><span data-ttu-id="63f0c-117">建立新的全像攝影框架並取得其預測</span><span class="sxs-lookup"><span data-stu-id="63f0c-117">Create a new holographic frame and get its prediction</span></span>

<span data-ttu-id="63f0c-118"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>包含應用程式所需的資訊，以便更新和呈現目前的框架。</span><span class="sxs-lookup"><span data-stu-id="63f0c-118">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> has information that the app needs in order to update and render the current frame.</span></span> <span data-ttu-id="63f0c-119">應用程式會藉由呼叫**CreateNextFrame**方法，開始每個新的框架。</span><span class="sxs-lookup"><span data-stu-id="63f0c-119">The app begins each new frame by calling the **CreateNextFrame** method.</span></span> <span data-ttu-id="63f0c-120">呼叫這個方法時，會使用最新可用的感應器資料進行預測，並封裝在**CurrentPrediction**物件中。</span><span class="sxs-lookup"><span data-stu-id="63f0c-120">When this method is called, predictions are made using the latest sensor data available, and encapsulated in **CurrentPrediction** object.</span></span>

<span data-ttu-id="63f0c-121">針對每個呈現的框架，必須使用新的框架物件，因為它只適用于即時時間。</span><span class="sxs-lookup"><span data-stu-id="63f0c-121">A new frame object must be used for each rendered frame as it is only valid for an instant in time.</span></span> <span data-ttu-id="63f0c-122">**CurrentPrediction**屬性包含相機位置等資訊。</span><span class="sxs-lookup"><span data-stu-id="63f0c-122">The **CurrentPrediction** property contains information such as the camera position.</span></span> <span data-ttu-id="63f0c-123">這項資訊會推入到使用者應該看到框架的確切時間點。</span><span class="sxs-lookup"><span data-stu-id="63f0c-123">The information is extrapolated to the exact moment in time when the frame is expected to be visible to the user.</span></span>

<span data-ttu-id="63f0c-124">下列程式碼是從**AppMain：： Update**摘錄自：</span><span class="sxs-lookup"><span data-stu-id="63f0c-124">The following code is excerpted from **AppMain::Update**:</span></span>

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a><span data-ttu-id="63f0c-125">處理相機更新</span><span class="sxs-lookup"><span data-stu-id="63f0c-125">Process camera updates</span></span>

<span data-ttu-id="63f0c-126">背景緩衝區可以從框架變更為框架。</span><span class="sxs-lookup"><span data-stu-id="63f0c-126">Back buffers can change from frame to frame.</span></span> <span data-ttu-id="63f0c-127">您的應用程式需要驗證每個相機的後端緩衝區，並視需要釋放和重新建立資源檢視和深度緩衝區。</span><span class="sxs-lookup"><span data-stu-id="63f0c-127">Your app needs to validate the back buffer for each camera, and release and recreate resource views and depth buffers as needed.</span></span> <span data-ttu-id="63f0c-128">請注意，預測中的一組姿勢是目前框架中所使用之相機的授權清單。</span><span class="sxs-lookup"><span data-stu-id="63f0c-128">Notice that the set of poses in the prediction is the authoritative list of cameras being used in the current frame.</span></span> <span data-ttu-id="63f0c-129">通常，您會使用這份清單來逐一查看相機集合。</span><span class="sxs-lookup"><span data-stu-id="63f0c-129">Usually, you use this list to iterate on the set of cameras.</span></span>

<span data-ttu-id="63f0c-130">從**AppMain：： Update**：</span><span class="sxs-lookup"><span data-stu-id="63f0c-130">From **AppMain::Update**:</span></span>

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

<span data-ttu-id="63f0c-131">From **DeviceResources：： EnsureCameraResources**：</span><span class="sxs-lookup"><span data-stu-id="63f0c-131">From **DeviceResources::EnsureCameraResources**:</span></span>

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a><span data-ttu-id="63f0c-132">取得要作為轉譯基礎的座標系統</span><span class="sxs-lookup"><span data-stu-id="63f0c-132">Get the coordinate system to use as a basis for rendering</span></span>

<span data-ttu-id="63f0c-133">Windows Mixed Reality 可讓您的應用程式視需要建立各種[座標系統](coordinate-systems-in-directx.md)，例如，附加的參考框架和固定的參考框架，以追蹤實體世界中的位置。</span><span class="sxs-lookup"><span data-stu-id="63f0c-133">Windows Mixed Reality lets your app create various [coordinate systems](coordinate-systems-in-directx.md) as needed, such as the attached reference frame and the stationary reference frame, that track locations in the physical world.</span></span> <span data-ttu-id="63f0c-134">然後，您的應用程式就可以使用這些座標系統，以瞭解在何處呈現每個畫面格的全息影像。</span><span class="sxs-lookup"><span data-stu-id="63f0c-134">Your app can then use these coordinate systems to reason about where to render holograms each frame.</span></span> <span data-ttu-id="63f0c-135">當您從 API 要求座標時，一律會傳入您想要在其中表示這些座標的<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> 。</span><span class="sxs-lookup"><span data-stu-id="63f0c-135">When requesting coordinates from an API, you will always pass in the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> within which you want those coordinates to be expressed.</span></span>

<span data-ttu-id="63f0c-136">從**AppMain：： Update**：</span><span class="sxs-lookup"><span data-stu-id="63f0c-136">From **AppMain::Update**:</span></span>

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

<span data-ttu-id="63f0c-137">然後，這些座標系統可在呈現場景中的內容時，用來產生身歷聲視圖矩陣。</span><span class="sxs-lookup"><span data-stu-id="63f0c-137">These coordinate systems can then be used to generate stereo view matrices when rendering the content in your scene.</span></span>

<span data-ttu-id="63f0c-138">From **CameraResources：： UpdateViewProjectionBuffer**：</span><span class="sxs-lookup"><span data-stu-id="63f0c-138">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a><span data-ttu-id="63f0c-139">處理注視和手勢輸入</span><span class="sxs-lookup"><span data-stu-id="63f0c-139">Process gaze and gesture input</span></span>

<span data-ttu-id="63f0c-140">[注視](gaze-in-directx.md)和[手寫](hands-and-motion-controllers-in-directx.md)輸入不是以時間為基礎，因此不需要在**StepTimer**函數中更新。</span><span class="sxs-lookup"><span data-stu-id="63f0c-140">[Gaze](gaze-in-directx.md) and [hand](hands-and-motion-controllers-in-directx.md) input are not time-based and thus do not have to update in the **StepTimer** function.</span></span> <span data-ttu-id="63f0c-141">不過，此輸入是應用程式需要查看每個畫面格的內容。</span><span class="sxs-lookup"><span data-stu-id="63f0c-141">However this input is something that the app needs to look at each frame.</span></span>

### <a name="process-time-based-updates"></a><span data-ttu-id="63f0c-142">處理以時間為基礎的更新</span><span class="sxs-lookup"><span data-stu-id="63f0c-142">Process time-based updates</span></span>

<span data-ttu-id="63f0c-143">任何即時轉譯應用程式都需要某種方式來處理以時間為基礎的更新;我們提供一種方法，可透過**StepTimer**的執行方式在 Windows 全像應用程式範本中執行此動作。</span><span class="sxs-lookup"><span data-stu-id="63f0c-143">Any real-time rendering app will need some way to process time-based updates; we provide a way to do this in the Windows Holographic app template via a **StepTimer** implementation.</span></span> <span data-ttu-id="63f0c-144">這類似于 DirectX 11 UWP 應用程式範本中提供的 StepTimer，因此，如果您已經看過該範本，您應該會在熟悉的基礎上。</span><span class="sxs-lookup"><span data-stu-id="63f0c-144">This is similar to the StepTimer provided in the DirectX 11 UWP app template, so if you already have looked at that template you should be on familiar ground.</span></span> <span data-ttu-id="63f0c-145">這個 StepTimer 範例 helper 類別可以提供固定的時間步驟更新，以及可變的時間步驟更新，而預設模式是可變的時間步驟。</span><span class="sxs-lookup"><span data-stu-id="63f0c-145">This StepTimer sample helper class is able to provide fixed time-step updates, as well as variable time-step updates, and the default mode is variable time steps.</span></span>

<span data-ttu-id="63f0c-146">在全像攝影轉譯的情況下，我們特別選擇不要將太多放入計時器函式中。</span><span class="sxs-lookup"><span data-stu-id="63f0c-146">In the case of holographic rendering, we've specifically chosen not to put too much into the timer function.</span></span> <span data-ttu-id="63f0c-147">這是因為您可以將它設定為固定的時間步驟，在這種情況下，每個畫面上可能會多次呼叫一次（或根本不會針對某些框架），而我們的全像攝影資料更新應該會針對每個畫面格進行一次。</span><span class="sxs-lookup"><span data-stu-id="63f0c-147">This is because you can configure it to be a fixed time step, in which case it might get called more than once per frame – or not at all, for some frames – and our holographic data updates should happen once per frame.</span></span>


<span data-ttu-id="63f0c-148">從**AppMain：： Update**：</span><span class="sxs-lookup"><span data-stu-id="63f0c-148">From **AppMain::Update**:</span></span>

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a><span data-ttu-id="63f0c-149">在座標系統中放置和旋轉全息影像</span><span class="sxs-lookup"><span data-stu-id="63f0c-149">Position and rotate holograms in your coordinate system</span></span>

<span data-ttu-id="63f0c-150">如果您是在單一座標系統中操作，當範本使用**SpatialStationaryReferenceFrame**時，此程式與您在3d 圖形中所使用的不同。</span><span class="sxs-lookup"><span data-stu-id="63f0c-150">If you are operating in a single coordinate system, as the template does with the **SpatialStationaryReferenceFrame**, this process isn't different from what you're otherwise used to in 3D graphics.</span></span> <span data-ttu-id="63f0c-151">在這裡，我們會旋轉 cube，並將模型矩陣設定為相對於固定座標系統中的位置。</span><span class="sxs-lookup"><span data-stu-id="63f0c-151">Here, we rotate the cube and set the model matrix relative to the position in the stationary coordinate system.</span></span>

<span data-ttu-id="63f0c-152">從**SpinningCubeRenderer：： Update**：</span><span class="sxs-lookup"><span data-stu-id="63f0c-152">From **SpinningCubeRenderer::Update**:</span></span>

```cpp
// Rotate the cube.
// Convert degrees to radians, then convert seconds to rotation angle.
const float    radiansPerSecond = XMConvertToRadians(m_degreesPerSecond);
const double   totalRotation = timer.GetTotalSeconds() * radiansPerSecond;
const float    radians = static_cast<float>(fmod(totalRotation, XM_2PI));
const XMMATRIX modelRotation = XMMatrixRotationY(-radians);

// Position the cube.
const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

// Multiply to get the transform matrix.
// Note that this transform does not enforce a particular coordinate system. The calling
// class is responsible for rendering this content in a consistent manner.
const XMMATRIX modelTransform = XMMatrixMultiply(modelRotation, modelTranslation);

// The view and projection matrices are provided by the system; they are associated
// with holographic cameras, and updated on a per-camera basis.
// Here, we provide the model transform for the sample hologram. The model transform
// matrix is transposed to prepare it for the shader.
XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(modelTransform));
```

<span data-ttu-id="63f0c-153">**有關 advanced 案例的注意事項：** 旋轉 cube 是一個非常簡單的範例，說明如何在單一參考框架內放置全息影像。</span><span class="sxs-lookup"><span data-stu-id="63f0c-153">**Note about advanced scenarios:** The spinning cube is a very simple example of how to position a hologram within a single reference frame.</span></span> <span data-ttu-id="63f0c-154">同時，也可以在相同的轉譯框架中同時[使用多個 SpatialCoordinateSystems](coordinate-systems-in-directx.md) 。</span><span class="sxs-lookup"><span data-stu-id="63f0c-154">It's also possible to [use multiple SpatialCoordinateSystems](coordinate-systems-in-directx.md) in the same rendered frame, at the same time.</span></span>

### <a name="update-constant-buffer-data"></a><span data-ttu-id="63f0c-155">更新常數緩衝區資料</span><span class="sxs-lookup"><span data-stu-id="63f0c-155">Update constant buffer data</span></span>

<span data-ttu-id="63f0c-156">內容的模型轉換會如往常般更新。</span><span class="sxs-lookup"><span data-stu-id="63f0c-156">Model transforms for content are updated as usual.</span></span> <span data-ttu-id="63f0c-157">現在，您將會針對要在其中轉譯的座標系統，計算出有效的轉換。</span><span class="sxs-lookup"><span data-stu-id="63f0c-157">By now, you will have computed valid transforms for the coordinate system you'll be rendering in.</span></span>

<span data-ttu-id="63f0c-158">從**SpinningCubeRenderer：： Update**：</span><span class="sxs-lookup"><span data-stu-id="63f0c-158">From **SpinningCubeRenderer::Update**:</span></span>

```cpp
// Update the model transform buffer for the hologram.
context->UpdateSubresource(
    m_modelConstantBuffer.Get(),
    0,
    nullptr,
    &m_modelConstantBufferData,
    0,
    0
);
```

<span data-ttu-id="63f0c-159">那麼視圖和投射的轉換呢？</span><span class="sxs-lookup"><span data-stu-id="63f0c-159">What about view and projection transforms?</span></span> <span data-ttu-id="63f0c-160">為了獲得最佳結果，我們想要等到幾乎準備好進行繪製呼叫，然後才取得這些。</span><span class="sxs-lookup"><span data-stu-id="63f0c-160">For best results, we want to wait until we're almost ready for our draw calls before we get these.</span></span>

## <a name="render-the-current-frame"></a><span data-ttu-id="63f0c-161">呈現目前的框架</span><span class="sxs-lookup"><span data-stu-id="63f0c-161">Render the current frame</span></span>

<span data-ttu-id="63f0c-162">在 Windows Mixed Reality 上轉譯與在 2D mono 顯示器上轉譯的方式不同，但有一些需要注意的差異：</span><span class="sxs-lookup"><span data-stu-id="63f0c-162">Rendering on Windows Mixed Reality is not much different from rendering on a 2D mono display, but there are some differences you need to be aware of:</span></span>
* <span data-ttu-id="63f0c-163">全像攝影的畫面預測很重要。</span><span class="sxs-lookup"><span data-stu-id="63f0c-163">Holographic frame predictions are important.</span></span> <span data-ttu-id="63f0c-164">當您的畫面格呈現時，預測愈接近，您的全息影像外觀就愈好。</span><span class="sxs-lookup"><span data-stu-id="63f0c-164">The closer the prediction is to when your frame is presented, the better your holograms will look.</span></span>
* <span data-ttu-id="63f0c-165">Windows Mixed Reality 控制相機的視圖。</span><span class="sxs-lookup"><span data-stu-id="63f0c-165">Windows Mixed Reality controls the camera views.</span></span> <span data-ttu-id="63f0c-166">您必須轉譯成每一個，因為全像攝影畫面將會在稍後呈現。</span><span class="sxs-lookup"><span data-stu-id="63f0c-166">You need to render to each one because the holographic frame will be presenting them for you later.</span></span>
* <span data-ttu-id="63f0c-167">建議使用「實例繪製」來完成身歷聲轉譯，以呈現目標陣列。</span><span class="sxs-lookup"><span data-stu-id="63f0c-167">Stereo rendering is recommended to be accomplished using instanced drawing to a render target array.</span></span> <span data-ttu-id="63f0c-168">「全像攝影應用程式」範本會使用建議的具現化方法來繪製到轉譯目標陣列，這會使用轉譯目標視圖在**Texture2DArray**上。</span><span class="sxs-lookup"><span data-stu-id="63f0c-168">The holographic app template uses the recommended approach of instanced drawing to a render target array, which uses a render target view onto a **Texture2DArray**.</span></span>
* <span data-ttu-id="63f0c-169">如果您想要轉譯而不使用身歷聲實例，您必須建立兩個非陣列 RenderTargetViews （每一眼一個），每個都參考從系統提供給應用程式的**Texture2DArray**中兩個配量的其中一個。</span><span class="sxs-lookup"><span data-stu-id="63f0c-169">If you want to render without using stereo instancing, you will need to create two non-array RenderTargetViews (one for each eye) that each reference one of the two slices in the **Texture2DArray** provided to the app from the system.</span></span> <span data-ttu-id="63f0c-170">這不是建議的作法，因為它的速度通常會比使用實例慢很多。</span><span class="sxs-lookup"><span data-stu-id="63f0c-170">This is not recommended, as it is typically significantly slower than using instancing.</span></span>

### <a name="get-an-updated-holographicframe-prediction"></a><span data-ttu-id="63f0c-171">取得更新的 HolographicFrame 預測</span><span class="sxs-lookup"><span data-stu-id="63f0c-171">Get an updated HolographicFrame prediction</span></span>

<span data-ttu-id="63f0c-172">更新框架預測可增強影像穩定的效率，並可讓您更精確地放置全息的位置，因為預測之間的時間較短，且使用者可以看到畫面格。</span><span class="sxs-lookup"><span data-stu-id="63f0c-172">Updating the frame prediction enhances the effectiveness of image stabilization and allows for more accurate positioning of holograms due to the shorter time between the prediction and when the frame is visible to the user.</span></span> <span data-ttu-id="63f0c-173">理想的情況是在呈現之前更新您的框架預測。</span><span class="sxs-lookup"><span data-stu-id="63f0c-173">Ideally update your frame prediction just before rendering.</span></span>

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a><span data-ttu-id="63f0c-174">呈現到每個相機</span><span class="sxs-lookup"><span data-stu-id="63f0c-174">Render to each camera</span></span>

<span data-ttu-id="63f0c-175">一組相機上的迴圈會在預測中產生，並轉譯成此集合中的每個相機。</span><span class="sxs-lookup"><span data-stu-id="63f0c-175">Loop on the set of camera poses in the prediction, and render to each camera in this set.</span></span>

<span data-ttu-id="63f0c-176">**設定轉譯階段**</span><span class="sxs-lookup"><span data-stu-id="63f0c-176">**Set up your rendering pass**</span></span>

<span data-ttu-id="63f0c-177">Windows Mixed Reality 會使用 stereoscopic 轉譯來增強深度的幻影並轉譯 stereoscopically，因此左側和右側顯示都是作用中狀態。</span><span class="sxs-lookup"><span data-stu-id="63f0c-177">Windows Mixed Reality uses stereoscopic rendering to enhance the illusion of depth and to render stereoscopically, so both the left and the right display are active.</span></span> <span data-ttu-id="63f0c-178">使用 stereoscopic 轉譯時，兩個顯示器之間會有一個位移，大腦可以將其視為實際深度。</span><span class="sxs-lookup"><span data-stu-id="63f0c-178">With stereoscopic rendering there is an offset between the two displays, which the brain can reconcile as actual depth.</span></span> <span data-ttu-id="63f0c-179">本節說明如何使用 Windows 全像應用程式範本中的程式碼，透過實例進行 stereoscopic 轉譯。</span><span class="sxs-lookup"><span data-stu-id="63f0c-179">This section covers stereoscopic rendering using instancing, using code from the Windows Holographic app template.</span></span>

<span data-ttu-id="63f0c-180">每個攝影機都有自己的呈現目標（背景緩衝區）和視圖和投影矩陣，以全像攝影空間。</span><span class="sxs-lookup"><span data-stu-id="63f0c-180">Each camera has its own render target (back buffer), and view and projection matrices, into the holographic space.</span></span> <span data-ttu-id="63f0c-181">您的應用程式將需要建立任何其他以相機為基礎的資源，例如每個攝影機的深度緩衝區。</span><span class="sxs-lookup"><span data-stu-id="63f0c-181">Your app will need to create any other camera-based resources - such as the depth buffer - on a per-camera basis.</span></span> <span data-ttu-id="63f0c-182">在 Windows 全像攝影應用程式範本中，我們提供 helper 類別，將這些資源組合在 DX：： CameraResources 中。</span><span class="sxs-lookup"><span data-stu-id="63f0c-182">In the Windows Holographic app template, we provide a helper class to bundle these resources together in DX::CameraResources.</span></span> <span data-ttu-id="63f0c-183">從設定轉譯目標視圖開始：</span><span class="sxs-lookup"><span data-stu-id="63f0c-183">Start by setting up the render target views:</span></span>

<span data-ttu-id="63f0c-184">從**AppMain：： Render**：</span><span class="sxs-lookup"><span data-stu-id="63f0c-184">From **AppMain::Render**:</span></span>

```cpp
// This represents the device-based resources for a HolographicCamera.
DX::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

// Get the device context.
const auto context = m_deviceResources->GetD3DDeviceContext();
const auto depthStencilView = pCameraResources->GetDepthStencilView();

// Set render targets to the current holographic camera.
ID3D11RenderTargetView *const targets[1] =
    { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, depthStencilView);

// Clear the back buffer and depth stencil view.
if (m_canGetHolographicDisplayForCamera &&
    cameraPose.HolographicCamera().Display().IsOpaque())
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::CornflowerBlue);
}
else
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::Transparent);
}
context->ClearDepthStencilView(
    depthStencilView, D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);
```

<span data-ttu-id="63f0c-185">**使用預測來取得相機的視圖和投影矩陣**</span><span class="sxs-lookup"><span data-stu-id="63f0c-185">**Use the prediction to get the view and projection matrices for the camera**</span></span>

<span data-ttu-id="63f0c-186">每個全像攝影攝影機的視圖和投影矩陣都會隨著每個畫面格而變更。</span><span class="sxs-lookup"><span data-stu-id="63f0c-186">The view and projection matrices for each holographic camera will change with every frame.</span></span> <span data-ttu-id="63f0c-187">重新整理每個全像攝影攝影機的常數緩衝區中的資料。</span><span class="sxs-lookup"><span data-stu-id="63f0c-187">Refresh the data in the constant buffer for each holographic camera.</span></span> <span data-ttu-id="63f0c-188">在您更新預測之後，以及對該攝影機進行任何繪製呼叫之前，請執行此動作。</span><span class="sxs-lookup"><span data-stu-id="63f0c-188">Do this after you updated the prediction, and before you make any draw calls for that camera.</span></span>

<span data-ttu-id="63f0c-189">從**AppMain：： Render**：</span><span class="sxs-lookup"><span data-stu-id="63f0c-189">From **AppMain::Render**:</span></span>

```cpp
// The view and projection matrices for each holographic camera will change
// every frame. This function refreshes the data in the constant buffer for
// the holographic camera indicated by cameraPose.
if (m_stationaryReferenceFrame)
{
    pCameraResources->UpdateViewProjectionBuffer(
        m_deviceResources, cameraPose, m_stationaryReferenceFrame.CoordinateSystem());
}

// Attach the view/projection constant buffer for this camera to the graphics pipeline.
bool cameraActive = pCameraResources->AttachViewProjectionBuffer(m_deviceResources);
```

<span data-ttu-id="63f0c-190">在這裡，我們會示範如何從相機姿勢取得矩陣。</span><span class="sxs-lookup"><span data-stu-id="63f0c-190">Here, we show how the matrices are acquired from the camera pose.</span></span> <span data-ttu-id="63f0c-191">在此過程中，我們也會取得相機的目前區。</span><span class="sxs-lookup"><span data-stu-id="63f0c-191">During this process we also obtain the current viewport for the camera.</span></span> <span data-ttu-id="63f0c-192">請注意我們如何提供座標系統：這是我們用來瞭解注視的相同座標系統，而且與我們用來定位旋轉 cube 的相同。</span><span class="sxs-lookup"><span data-stu-id="63f0c-192">Note how we provide a coordinate system: this is the same coordinate system we used to understand gaze, and it's the same one we used to position the spinning cube.</span></span>


<span data-ttu-id="63f0c-193">From **CameraResources：： UpdateViewProjectionBuffer**：</span><span class="sxs-lookup"><span data-stu-id="63f0c-193">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// The system changes the viewport on a per-frame basis for system optimizations.
auto viewport = cameraPose.Viewport();
m_d3dViewport = CD3D11_VIEWPORT(
    viewport.X,
    viewport.Y,
    viewport.Width,
    viewport.Height
);

// The projection transform for each frame is provided by the HolographicCameraPose.
HolographicStereoTransform cameraProjectionTransform = cameraPose.ProjectionTransform();

// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);

// If TryGetViewTransform returns a null pointer, that means the pose and coordinate
// system cannot be understood relative to one another; content cannot be rendered
// in this coordinate system for the duration of the current frame.
// This usually means that positional tracking is not active for the current frame, in
// which case it is possible to use a SpatialLocatorAttachedFrameOfReference to render
// content that is not world-locked instead.
DX::ViewProjectionConstantBuffer viewProjectionConstantBufferData;
bool viewTransformAcquired = viewTransformContainer != nullptr;
if (viewTransformAcquired)
{
    // Otherwise, the set of view transforms can be retrieved.
    HolographicStereoTransform viewCoordinateSystemTransform = viewTransformContainer.Value();

    // Update the view matrices. Holographic cameras (such as Microsoft HoloLens) are
    // constantly moving relative to the world. The view matrices need to be updated
    // every frame.
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[0],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Left) *
            XMLoadFloat4x4(&cameraProjectionTransform.Left))
    );
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[1],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Right) *
            XMLoadFloat4x4(&cameraProjectionTransform.Right))
    );
}
```

<span data-ttu-id="63f0c-194">應該設定每個框架的視口。</span><span class="sxs-lookup"><span data-stu-id="63f0c-194">The viewport should be set each frame.</span></span> <span data-ttu-id="63f0c-195">您的頂點著色器（至少）通常會需要存取視圖/投射資料。</span><span class="sxs-lookup"><span data-stu-id="63f0c-195">Your vertex shader (at least) will generally need access to the view/projection data.</span></span>


<span data-ttu-id="63f0c-196">From **CameraResources：： AttachViewProjectionBuffer**：</span><span class="sxs-lookup"><span data-stu-id="63f0c-196">From **CameraResources::AttachViewProjectionBuffer**:</span></span>

```cpp
// Set the viewport for this camera.
context->RSSetViewports(1, &m_d3dViewport);

// Send the constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    1,
    1,
    m_viewProjectionConstantBuffer.GetAddressOf()
);
```

<span data-ttu-id="63f0c-197">**呈現到相機背面緩衝區，並認可深度緩衝區**：</span><span class="sxs-lookup"><span data-stu-id="63f0c-197">**Render to the camera back buffer and commit the depth buffer**:</span></span>

<span data-ttu-id="63f0c-198">最好先檢查**TryGetViewTransform**是否成功，再嘗試使用視圖/投射資料，因為如果無法定位座標系統（例如，追蹤已中斷），您的應用程式無法使用該框架來呈現它。</span><span class="sxs-lookup"><span data-stu-id="63f0c-198">It's a good idea to check that **TryGetViewTransform** succeeded before trying to use the view/projection data, because if the coordinate system is not locatable (e.g., tracking was interrupted) your app cannot render with it for that frame.</span></span> <span data-ttu-id="63f0c-199">如果**CameraResources**類別指出成功的更新，此範本只會呼叫旋轉 cube 上的**呈現**。</span><span class="sxs-lookup"><span data-stu-id="63f0c-199">The template only calls **Render** on the spinning cube if the **CameraResources** class indicates a successful update.</span></span>

<span data-ttu-id="63f0c-200">為了讓開發人員或使用者將其放在世界各地，Windows Mixed Reality 包含影像[穩定](hologram-stability.md)的功能。</span><span class="sxs-lookup"><span data-stu-id="63f0c-200">To keep holograms where a developer or a user puts them in the world, Windows Mixed Reality includes features for [image stabilization](hologram-stability.md).</span></span> <span data-ttu-id="63f0c-201">影像穩定有助於隱藏轉譯管線中固有的延遲，以確保最適合使用者的全像攝影體驗;您可以指定焦點，以進一步增強影像的穩定，也可以提供深度緩衝區來即時計算優化的影像穩定。</span><span class="sxs-lookup"><span data-stu-id="63f0c-201">Image stabilization helps hide the latency inherent in a rendering pipeline to ensure the best holographic experiences for users; a focus point may be specified to enhance image stabilization even further, or a depth buffer may be provided to compute optimized image stabilization in real time.</span></span>

<span data-ttu-id="63f0c-202">為了獲得最佳結果，您的應用程式應該使用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API 提供深度緩衝區。</span><span class="sxs-lookup"><span data-stu-id="63f0c-202">For best results, your app should provide a depth buffer using the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API.</span></span> <span data-ttu-id="63f0c-203">Windows Mixed Reality 接著可以使用深度緩衝區的幾何資訊，即時優化影像穩定。</span><span class="sxs-lookup"><span data-stu-id="63f0c-203">Windows Mixed Reality can then use geometry information from the depth buffer to optimize image stabilization in real time.</span></span> <span data-ttu-id="63f0c-204">Windows 全像應用程式範本預設會認可應用程式的深度緩衝區，以協助優化全息影像的穩定性。</span><span class="sxs-lookup"><span data-stu-id="63f0c-204">The Windows Holographic app template commits the app's depth buffer by default, helping optimize hologram stability.</span></span>

<span data-ttu-id="63f0c-205">從**AppMain：： Render**：</span><span class="sxs-lookup"><span data-stu-id="63f0c-205">From **AppMain::Render**:</span></span>

```cpp
// Only render world-locked content when positional tracking is active.
if (cameraActive)
{
    // Draw the sample hologram.
    m_spinningCubeRenderer->Render();
    if (m_canCommitDirect3D11DepthBuffer)
    {
        // On versions of the platform that support the CommitDirect3D11DepthBuffer API, we can 
        // provide the depth buffer to the system, and it will use depth information to stabilize 
        // the image at a per-pixel level.
        HolographicCameraRenderingParameters renderingParameters =
            holographicFrame.GetRenderingParameters(cameraPose);
        
        IDirect3DSurface interopSurface =
            DX::CreateDepthTextureInteropObject(pCameraResources->GetDepthStencilTexture2D());

        // Calling CommitDirect3D11DepthBuffer causes the system to queue Direct3D commands to 
        // read the depth buffer. It will then use that information to stabilize the image as
        // the HolographicFrame is presented.
        renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
    }
}
```

>[!NOTE]
><span data-ttu-id="63f0c-206">Windows 將會在 GPU 上處理您的深度材質，因此必須使用您的深度緩衝區做為著色器資源。</span><span class="sxs-lookup"><span data-stu-id="63f0c-206">Windows will process your depth texture on the GPU, so it must be possible to use your depth buffer as a shader resource.</span></span> <span data-ttu-id="63f0c-207">您所建立的 ID3D11Texture2D 應該是無類型的格式，而且應該系結為著色器資源檢視。</span><span class="sxs-lookup"><span data-stu-id="63f0c-207">The ID3D11Texture2D that you create should be in a typeless format and it should be bound as a shader resource view.</span></span> <span data-ttu-id="63f0c-208">以下範例說明如何建立可針對影像穩定認可的深度材質。</span><span class="sxs-lookup"><span data-stu-id="63f0c-208">Here is an example of how to create a depth texture that can be committed for image stabilization.</span></span>

<span data-ttu-id="63f0c-209">針對**CommitDirect3D11DepthBuffer 建立深度緩衝區資源的**程式碼：</span><span class="sxs-lookup"><span data-stu-id="63f0c-209">Code for **Depth buffer resource creation for CommitDirect3D11DepthBuffer**:</span></span>

```cpp
// Create a depth stencil view for use with 3D rendering if needed.
CD3D11_TEXTURE2D_DESC depthStencilDesc(
    DXGI_FORMAT_R16_TYPELESS,
    static_cast<UINT>(m_d3dRenderTargetSize.Width),
    static_cast<UINT>(m_d3dRenderTargetSize.Height),
    m_isStereo ? 2 : 1, // Create two textures when rendering in stereo.
    1, // Use a single mipmap level.
    D3D11_BIND_DEPTH_STENCIL | D3D11_BIND_SHADER_RESOURCE
);

winrt::check_hresult(
    device->CreateTexture2D(
        &depthStencilDesc,
        nullptr,
        &m_d3dDepthStencil
    ));

CD3D11_DEPTH_STENCIL_VIEW_DESC depthStencilViewDesc(
    m_isStereo ? D3D11_DSV_DIMENSION_TEXTURE2DARRAY : D3D11_DSV_DIMENSION_TEXTURE2D,
    DXGI_FORMAT_D16_UNORM
);
winrt::check_hresult(
    device->CreateDepthStencilView(
        m_d3dDepthStencil.Get(),
        &depthStencilViewDesc,
        &m_d3dDepthStencilView
    ));
```

<span data-ttu-id="63f0c-210">**繪製全像攝影內容**</span><span class="sxs-lookup"><span data-stu-id="63f0c-210">**Draw holographic content**</span></span>

<span data-ttu-id="63f0c-211">Windows 全像應用程式範本會使用將具現化幾何繪製為大小 2 Texture2DArray 的建議技術，將內容轉譯成身歷聲。</span><span class="sxs-lookup"><span data-stu-id="63f0c-211">The Windows Holographic app template renders content in stereo by using the recommended technique of drawing instanced geometry to a Texture2DArray of size 2.</span></span> <span data-ttu-id="63f0c-212">我們來看一下這個的實例部分，以及它如何在 Windows Mixed Reality 上運作。</span><span class="sxs-lookup"><span data-stu-id="63f0c-212">Let's look at the instancing part of this, and how it works on Windows Mixed Reality.</span></span>

<span data-ttu-id="63f0c-213">從**SpinningCubeRenderer：： Render**：</span><span class="sxs-lookup"><span data-stu-id="63f0c-213">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

<span data-ttu-id="63f0c-214">每個實例會從常數緩衝區存取不同的視圖/投影矩陣。</span><span class="sxs-lookup"><span data-stu-id="63f0c-214">Each instance accesses a different view/projection matrix from the constant buffer.</span></span> <span data-ttu-id="63f0c-215">以下是常數緩衝區結構，這只是2個矩陣的陣列。</span><span class="sxs-lookup"><span data-stu-id="63f0c-215">Here's the constant buffer structure, which is just an array of 2 matrices.</span></span>

<span data-ttu-id="63f0c-216">From **VertexShaderShared. hlsl**，包含**VPRTVertexShader. hlsl**：</span><span class="sxs-lookup"><span data-stu-id="63f0c-216">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

<span data-ttu-id="63f0c-217">必須為每個圖元設定轉譯目標陣列索引。</span><span class="sxs-lookup"><span data-stu-id="63f0c-217">The render target array index must be set for each pixel.</span></span> <span data-ttu-id="63f0c-218">在下列程式碼片段中，viewId 會對應至**SV_RenderTargetArrayIndex**語義。</span><span class="sxs-lookup"><span data-stu-id="63f0c-218">In the following snippet, output.viewId is mapped to the **SV_RenderTargetArrayIndex** semantic.</span></span> <span data-ttu-id="63f0c-219">請注意，這需要支援選擇性的 Direct3D 11.3 功能，以允許從任何著色器階段設定轉譯目標陣列索引的語義。</span><span class="sxs-lookup"><span data-stu-id="63f0c-219">Note that this requires support for an optional Direct3D 11.3 feature, which allows the render target array index semantic to be set from any shader stage.</span></span>

<span data-ttu-id="63f0c-220">From **VPRTVertexShader. hlsl**：</span><span class="sxs-lookup"><span data-stu-id="63f0c-220">From **VPRTVertexShader.hlsl**:</span></span>

```HLSL    
// Per-vertex data passed to the geometry shader.
struct VertexShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;

    // The render target array index is set here in the vertex shader.
    uint        viewId  : SV_RenderTargetArrayIndex;
};
```

<span data-ttu-id="63f0c-221">From **VertexShaderShared. hlsl**，包含**VPRTVertexShader. hlsl**：</span><span class="sxs-lookup"><span data-stu-id="63f0c-221">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// Per-vertex data used as input to the vertex shader.
struct VertexShaderInput
{
    min16float3 pos     : POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : SV_InstanceID;
};

// Simple shader to do vertex processing on the GPU.
VertexShaderOutput main(VertexShaderInput input)
{
    VertexShaderOutput output;
    float4 pos = float4(input.pos, 1.0f);

    // Note which view this vertex has been sent to. Used for matrix lookup.
    // Taking the modulo of the instance ID allows geometry instancing to be used
    // along with stereo instanced drawing; in that case, two copies of each 
    // instance would be drawn, one for left and one for right.
    int idx = input.instId % 2;

    // Transform the vertex position into world space.
    pos = mul(pos, model);

    // Correct for perspective and project the vertex position onto the screen.
    pos = mul(pos, viewProjection[idx]);
    output.pos = (min16float4)pos;

    // Pass the color through without modification.
    output.color = input.color;

    // Set the render target array index.
    output.viewId = idx;

    return output;
}
```

<span data-ttu-id="63f0c-222">如果您想要使用現有的具現化繪圖技巧，並將此方法繪製到身歷聲轉譯目標陣列，您只需要繪製兩次您平常擁有的實例數目。</span><span class="sxs-lookup"><span data-stu-id="63f0c-222">If you want to use your existing instanced drawing techniques with this method of drawing to a stereo render target array, all you have to do is draw twice the number of instances you normally have.</span></span> <span data-ttu-id="63f0c-223">在著色器中，將**d**除以2，以取得原始實例識別碼，這可以編制索引為每個物件資料的緩衝區（例如）： `int actualIdx = input.instId / 2;`</span><span class="sxs-lookup"><span data-stu-id="63f0c-223">In the shader, divide **input.instId** by 2 to get the original instance ID, which can be indexed into (for example) a buffer of per-object data: `int actualIdx = input.instId / 2;`</span></span>

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a><span data-ttu-id="63f0c-224">有關在 HoloLens 上呈現身歷聲內容的重要注意事項</span><span class="sxs-lookup"><span data-stu-id="63f0c-224">Important note about rendering stereo content on HoloLens</span></span>

<span data-ttu-id="63f0c-225">Windows Mixed Reality 支援從任何著色器階段設定轉譯目標陣列索引的功能;一般來說，這是只能在幾何著色器階段中完成的工作，因為已針對 Direct3D 11 定義此語義的方式。</span><span class="sxs-lookup"><span data-stu-id="63f0c-225">Windows Mixed Reality supports the ability to set the render target array index from any shader stage; normally, this is a task that could only be done in the geometry shader stage due to the way the semantic is defined for Direct3D 11.</span></span> <span data-ttu-id="63f0c-226">在這裡，我們將示範如何只設定頂點和圖元著色器階段，來設定轉譯管線的完整範例。</span><span class="sxs-lookup"><span data-stu-id="63f0c-226">Here, we show a complete example of how to set up a rendering pipeline with just the vertex and pixel shader stages set.</span></span> <span data-ttu-id="63f0c-227">著色器程式碼如下所述。</span><span class="sxs-lookup"><span data-stu-id="63f0c-227">The shader code is as described above.</span></span>

<span data-ttu-id="63f0c-228">從**SpinningCubeRenderer：： Render**：</span><span class="sxs-lookup"><span data-stu-id="63f0c-228">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
const auto context = m_deviceResources->GetD3DDeviceContext();

// Each vertex is one instance of the VertexPositionColor struct.
const UINT stride = sizeof(VertexPositionColor);
const UINT offset = 0;
context->IASetVertexBuffers(
    0,
    1,
    m_vertexBuffer.GetAddressOf(),
    &stride,
    &offset
);
context->IASetIndexBuffer(
    m_indexBuffer.Get(),
    DXGI_FORMAT_R16_UINT, // Each index is one 16-bit unsigned integer (short).
    0
);
context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach the vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
);
// Apply the model constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    0,
    1,
    m_modelConstantBuffer.GetAddressOf()
);

// Attach the pixel shader.
context->PSSetShader(
    m_pixelShader.Get(),
    nullptr,
    0
);

// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

### <a name="important-note-about-rendering-on-non-hololens-devices"></a><span data-ttu-id="63f0c-229">在非 HoloLens 裝置上呈現的重要注意事項</span><span class="sxs-lookup"><span data-stu-id="63f0c-229">Important note about rendering on non-HoloLens devices</span></span>

<span data-ttu-id="63f0c-230">若要在頂點著色器中設定轉譯目標陣列索引，圖形驅動程式必須支援選擇性的 Direct3D 11.3 功能，亦即 HoloLens 支援。</span><span class="sxs-lookup"><span data-stu-id="63f0c-230">Setting the render target array index in the vertex shader requires that the graphics driver supports an optional Direct3D 11.3 feature, which HoloLens does support.</span></span> <span data-ttu-id="63f0c-231">您的應用程式或許能夠安全地執行轉譯的技巧，而且所有的需求都符合在 Microsoft HoloLens 上執行。</span><span class="sxs-lookup"><span data-stu-id="63f0c-231">Your app may be able to safely implement just that technique for rendering, and all requirements will be met for running on the Microsoft HoloLens.</span></span>

<span data-ttu-id="63f0c-232">在此情況下，您可能會想要使用 HoloLens 模擬器，這可以是適用于全像攝影應用程式的強大開發工具，並支援連接到 Windows 10 電腦的 Windows Mixed Reality 沉浸式耳機裝置。</span><span class="sxs-lookup"><span data-stu-id="63f0c-232">It may be the case that you want to use the HoloLens emulator as well, which can be a powerful development tool for your holographic app - and support Windows Mixed Reality immersive headset devices that are attached to Windows 10 PCs.</span></span> <span data-ttu-id="63f0c-233">對非 HoloLens 轉譯路徑的支援-因此，對於所有的 Windows Mixed Reality 而言，也都內建于 Windows 全像應用程式範本中。</span><span class="sxs-lookup"><span data-stu-id="63f0c-233">Support for the non-HoloLens rendering path - and therefore, for all of Windows Mixed Reality - is also built into the Windows Holographic app template.</span></span> <span data-ttu-id="63f0c-234">在範本程式碼中，您將找到可讓全像攝影應用程式在開發電腦上的 GPU 上執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="63f0c-234">In the template code, you will find code to enable your holographic app to run on the GPU in your development PC.</span></span> <span data-ttu-id="63f0c-235">以下是**DeviceResources**類別如何檢查這項選擇性功能支援的方式。</span><span class="sxs-lookup"><span data-stu-id="63f0c-235">Here is how the **DeviceResources** class checks for this optional feature support.</span></span>

<span data-ttu-id="63f0c-236">From **DeviceResources：： CreateDeviceResources**：</span><span class="sxs-lookup"><span data-stu-id="63f0c-236">From **DeviceResources::CreateDeviceResources**:</span></span>

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

<span data-ttu-id="63f0c-237">若要支援不使用此選擇性功能的轉譯，您的應用程式必須使用幾何著色器來設定轉譯目標陣列索引。</span><span class="sxs-lookup"><span data-stu-id="63f0c-237">To support rendering without this optional feature, your app must use a geometry shader to set the render target array index.</span></span> <span data-ttu-id="63f0c-238">此程式碼片段會在*after* **VSSetConstantBuffers**之後，以及上一節所示的程式碼範例中的**pssetshade** *之前*新增，說明如何在 HoloLens 上呈現身歷聲。</span><span class="sxs-lookup"><span data-stu-id="63f0c-238">This snippet would be added *after* **VSSetConstantBuffers**, and *before* **PSSetShader** in the code example shown in the previous section that explains how to render stereo on HoloLens.</span></span>

<span data-ttu-id="63f0c-239">從**SpinningCubeRenderer：： Render**：</span><span class="sxs-lookup"><span data-stu-id="63f0c-239">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
if (!m_usingVprtShaders)
{
    // On devices that do not support the D3D11_FEATURE_D3D11_OPTIONS3::
    // VPAndRTArrayIndexFromAnyShaderFeedingRasterizer optional feature,
    // a pass-through geometry shader is used to set the render target 
    // array index.
    context->GSSetShader(
        m_geometryShader.Get(),
        nullptr,
        0
    );
}
```

<span data-ttu-id="63f0c-240">**HLSL 注意**：在此情況下，您也必須載入稍微修改的端點著色器，以使用一律允許的著色器語義（例如 TEXCOORD0），將轉譯目標陣列索引傳遞至幾何著色器。</span><span class="sxs-lookup"><span data-stu-id="63f0c-240">**HLSL NOTE**: In this case, you must also load a slightly modified vertex shader that passes the render target array index to the geometry shader using an always-allowed shader semantic, such as TEXCOORD0.</span></span> <span data-ttu-id="63f0c-241">幾何著色器不需要執行任何工作;範本幾何著色器會傳遞所有資料，但呈現目標陣列索引除外，這是用來設定 SV_RenderTargetArrayIndex 語義。</span><span class="sxs-lookup"><span data-stu-id="63f0c-241">The geometry shader does not have to do any work; the template geometry shader passes through all data, with the exception of the render target array index, which is used to set the SV_RenderTargetArrayIndex semantic.</span></span>

<span data-ttu-id="63f0c-242">適用于 GeometryShader 的應用程式範本代碼 **。 hlsl**：</span><span class="sxs-lookup"><span data-stu-id="63f0c-242">App template code for **GeometryShader.hlsl**:</span></span>

```HLSL
// Per-vertex data from the vertex shader.
struct GeometryShaderInput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : TEXCOORD0;
};

// Per-vertex data passed to the rasterizer.
struct GeometryShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint        rtvId   : SV_RenderTargetArrayIndex;
};

// This geometry shader is a pass-through that leaves the geometry unmodified 
// and sets the render target array index.
[maxvertexcount(3)]
void main(triangle GeometryShaderInput input[3], inout TriangleStream<GeometryShaderOutput> outStream)
{
    GeometryShaderOutput output;
    [unroll(3)]
    for (int i = 0; i < 3; ++i)
    {
        output.pos   = input[i].pos;
        output.color = input[i].color;
        output.rtvId = input[i].instId;
        outStream.Append(output);
    }
}
```

## <a name="present"></a><span data-ttu-id="63f0c-243">存在</span><span class="sxs-lookup"><span data-stu-id="63f0c-243">Present</span></span>

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a><span data-ttu-id="63f0c-244">讓全像攝影畫面呈現交換鏈</span><span class="sxs-lookup"><span data-stu-id="63f0c-244">Enable the holographic frame to present the swap chain</span></span>

<span data-ttu-id="63f0c-245">在 Windows Mixed Reality 中，系統會控制交換鏈。</span><span class="sxs-lookup"><span data-stu-id="63f0c-245">With Windows Mixed Reality, the system controls the swap chain.</span></span> <span data-ttu-id="63f0c-246">系統接著會管理對每個全像攝影攝影機呈現畫面格，以確保高品質的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="63f0c-246">The system then manages presenting frames to each holographic camera to ensure a high quality user experience.</span></span> <span data-ttu-id="63f0c-247">它也會為每個攝影機提供一個視口更新每個畫面格，以將系統的各個層面優化，例如影像穩定或混合現實 Capture。</span><span class="sxs-lookup"><span data-stu-id="63f0c-247">It also provides a viewport update each frame, for each camera, to optimize aspects of the system such as image stabilization or Mixed Reality Capture.</span></span> <span data-ttu-id="63f0c-248">因此，使用 DirectX 的全像攝影應用程式不會在 DXGI 交換**鏈上呼叫**。</span><span class="sxs-lookup"><span data-stu-id="63f0c-248">So, a holographic app using DirectX doesn't call **Present** on a DXGI swap chain.</span></span> <span data-ttu-id="63f0c-249">相反地，您可以使用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>類別，在繪圖完成繪製之後，呈現框架的所有 swapchains。</span><span class="sxs-lookup"><span data-stu-id="63f0c-249">Instead, you use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class to present all swapchains for a frame once you're done drawing it.</span></span>

<span data-ttu-id="63f0c-250">從**DeviceResources：:P 重發**：</span><span class="sxs-lookup"><span data-stu-id="63f0c-250">From **DeviceResources::Present**:</span></span>

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

<span data-ttu-id="63f0c-251">根據預設，此 API 會等待框架完成後再傳回。</span><span class="sxs-lookup"><span data-stu-id="63f0c-251">By default, this API waits for the frame to finish before it returns.</span></span> <span data-ttu-id="63f0c-252">全像攝影應用程式應該等待前一個畫面完成，才能在新的畫面上開始工作，因為這樣可減少延遲，並讓全像框預測的結果變得更好。</span><span class="sxs-lookup"><span data-stu-id="63f0c-252">Holographic apps should wait for the previous frame to finish before starting work on a new frame, because this reduces latency and allows for better results from holographic frame predictions.</span></span> <span data-ttu-id="63f0c-253">這不是一項困難的規則，如果您的畫面格需要超過一螢幕重新整理來轉譯，可以將 HolographicFramePresentWaitBehavior 參數傳遞給<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>來停用此等候。</span><span class="sxs-lookup"><span data-stu-id="63f0c-253">This isn't a hard rule, and if you have frames that take longer than one screen refresh to render you can disable this wait by passing the HolographicFramePresentWaitBehavior parameter to <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span></span> <span data-ttu-id="63f0c-254">在此情況下，您可能會使用非同步轉譯執行緒，以維護 GPU 上的連續負載。</span><span class="sxs-lookup"><span data-stu-id="63f0c-254">In this case, you would likely use an asynchronous rendering thread in order to maintain a continuous load on the GPU.</span></span> <span data-ttu-id="63f0c-255">請注意，HoloLens 裝置的重新整理頻率是60hz，其中一個框架的持續時間大約為16毫秒。</span><span class="sxs-lookup"><span data-stu-id="63f0c-255">Note that the refresh rate of the HoloLens device is 60hz, where one frame has a duration of approximately 16 ms.</span></span> <span data-ttu-id="63f0c-256">沉浸式耳機裝置的範圍可以從60hz 到 90hz;在 90 hz 重新整理顯示時，每個畫面格的持續時間大約為11毫秒。</span><span class="sxs-lookup"><span data-stu-id="63f0c-256">Immersive headset devices can range from 60hz to 90hz; when refreshing the display at 90 hz, each frame will have a duration of approximately 11 ms.</span></span>

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a><span data-ttu-id="63f0c-257">處理與 HolographicFrame 合作的 DeviceLost 案例</span><span class="sxs-lookup"><span data-stu-id="63f0c-257">Handle DeviceLost scenarios in cooperation with the HolographicFrame</span></span>

<span data-ttu-id="63f0c-258">DirectX 11 應用程式通常會想要檢查 DXGI 交換鏈的**現有**函式所傳回的 HRESULT，找出是否有**DeviceLost**錯誤。</span><span class="sxs-lookup"><span data-stu-id="63f0c-258">DirectX 11 apps would typically want to check the HRESULT returned by the DXGI swap chain's **Present** function to find out if there was a **DeviceLost** error.</span></span> <span data-ttu-id="63f0c-259"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>類別會為您處理這種情況。</span><span class="sxs-lookup"><span data-stu-id="63f0c-259">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class handles this for you.</span></span> <span data-ttu-id="63f0c-260">檢查它所傳回的<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> ，以瞭解您是否需要發行並重新建立 Direct3D 裝置和裝置型資源。</span><span class="sxs-lookup"><span data-stu-id="63f0c-260">Inspect the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> it returns to find out if you need to release and recreate the Direct3D device and device-based resources.</span></span>

```cpp
// The PresentUsingCurrentPrediction API will detect when the graphics device
// changes or becomes invalid. When this happens, it is considered a Direct3D
// device lost scenario.
if (presentResult == HolographicFramePresentResult::DeviceRemoved)
{
    // The Direct3D device, context, and resources should be recreated.
    HandleDeviceLost();
}
```

<span data-ttu-id="63f0c-261">請注意，如果 Direct3D 裝置遺失，而您已重新建立它，您必須告訴<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>開始使用新的裝置。</span><span class="sxs-lookup"><span data-stu-id="63f0c-261">Note that if the Direct3D device was lost, and you did recreate it, you have to tell the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> to start using the new device.</span></span> <span data-ttu-id="63f0c-262">將會重新建立此裝置的交換鏈。</span><span class="sxs-lookup"><span data-stu-id="63f0c-262">The swap chain will be recreated for this device.</span></span>

<span data-ttu-id="63f0c-263">From **DeviceResources：： InitializeUsingHolographicSpace**：</span><span class="sxs-lookup"><span data-stu-id="63f0c-263">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

<span data-ttu-id="63f0c-264">畫面出現之後，您可以回到主要程式迴圈，讓它繼續進入下一個畫面。</span><span class="sxs-lookup"><span data-stu-id="63f0c-264">Once your frame is presented, you can return back to the main program loop and allow it to continue to the next frame.</span></span>

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a><span data-ttu-id="63f0c-265">混合式圖形電腦和混合現實應用程式</span><span class="sxs-lookup"><span data-stu-id="63f0c-265">Hybrid graphics PCs and mixed reality applications</span></span>

<span data-ttu-id="63f0c-266">Windows 10 建立者更新電腦可以**同時**設定獨立和整合式 gpu。</span><span class="sxs-lookup"><span data-stu-id="63f0c-266">Windows 10 Creators Update PCs may be configured with **both** discrete and integrated GPUs.</span></span> <span data-ttu-id="63f0c-267">使用這些類型的電腦時，Windows 會選擇耳機所連線的介面卡。</span><span class="sxs-lookup"><span data-stu-id="63f0c-267">With these types of computers, Windows will choose the adapter the headset is connected to.</span></span> <span data-ttu-id="63f0c-268">應用程式必須確定它所建立的 DirectX 裝置使用相同的介面卡。</span><span class="sxs-lookup"><span data-stu-id="63f0c-268">Applications must ensure the DirectX device it creates uses the same adapter.</span></span>

<span data-ttu-id="63f0c-269">最常見的 Direct3D 範例程式碼示範如何使用預設硬體介面卡建立 DirectX 裝置，在混合式系統上，它可能與用於耳機的不同。</span><span class="sxs-lookup"><span data-stu-id="63f0c-269">Most general Direct3D sample code demonstrates creating a DirectX device using the default hardware adapter, which on a hybrid system may not be the same as the one used for the headset.</span></span>

<span data-ttu-id="63f0c-270">若要解決這可能造成的任何問題，請使用任一<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>的<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> 。PrimaryAdapterId （）或<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>。AdapterId （）。</span><span class="sxs-lookup"><span data-stu-id="63f0c-270">To work around any issues this may cause, use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> from either <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>.PrimaryAdapterId() or <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>.AdapterId().</span></span> <span data-ttu-id="63f0c-271">接著，您可以使用這個 adapterId 來選取使用 IDXGIFactory4 EnumAdapterByLuid 的正確 DXGIAdapter。</span><span class="sxs-lookup"><span data-stu-id="63f0c-271">This adapterId can then be used to select the right DXGIAdapter using IDXGIFactory4.EnumAdapterByLuid.</span></span>

<span data-ttu-id="63f0c-272">From **DeviceResources：： InitializeUsingHolographicSpace**：</span><span class="sxs-lookup"><span data-stu-id="63f0c-272">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```cpp
// The holographic space might need to determine which adapter supports
// holograms, in which case it will specify a non-zero PrimaryAdapterId.
LUID id =
{
    m_holographicSpace.PrimaryAdapterId().LowPart,
    m_holographicSpace.PrimaryAdapterId().HighPart
};

// When a primary adapter ID is given to the app, the app should find
// the corresponding DXGI adapter and use it to create Direct3D devices
// and device contexts. Otherwise, there is no restriction on the DXGI
// adapter the app can use.
if ((id.HighPart != 0) || (id.LowPart != 0))
{
    UINT createFlags = 0;

    // Create the DXGI factory.
    ComPtr<IDXGIFactory1> dxgiFactory;
    winrt::check_hresult(
        CreateDXGIFactory2(
            createFlags,
            IID_PPV_ARGS(&dxgiFactory)
        ));
    ComPtr<IDXGIFactory4> dxgiFactory4;
    winrt::check_hresult(dxgiFactory.As(&dxgiFactory4));

    // Retrieve the adapter specified by the holographic space.
    winrt::check_hresult(
        dxgiFactory4->EnumAdapterByLuid(
            id,
            IID_PPV_ARGS(&m_dxgiAdapter)
        ));
}
else
{
    m_dxgiAdapter.Reset();
}
```

<span data-ttu-id="63f0c-273">用來**更新 DeviceResources：： CreateDeviceResources 以使用 IDXGIAdapter 的**程式碼</span><span class="sxs-lookup"><span data-stu-id="63f0c-273">Code to **update DeviceResources::CreateDeviceResources to use IDXGIAdapter**</span></span>

```cpp
// Create the Direct3D 11 API device object and a corresponding context.
ComPtr<ID3D11Device> device;
ComPtr<ID3D11DeviceContext> context;

const D3D_DRIVER_TYPE driverType = m_dxgiAdapter == nullptr ? D3D_DRIVER_TYPE_HARDWARE : D3D_DRIVER_TYPE_UNKNOWN;
const HRESULT hr = D3D11CreateDevice(
    m_dxgiAdapter.Get(),        // Either nullptr, or the primary adapter determined by Windows Holographic.
    driverType,                 // Create a device using the hardware graphics driver.
    0,                          // Should be 0 unless the driver is D3D_DRIVER_TYPE_SOFTWARE.
    creationFlags,              // Set debug and Direct2D compatibility flags.
    featureLevels,              // List of feature levels this app can support.
    ARRAYSIZE(featureLevels),   // Size of the list above.
    D3D11_SDK_VERSION,          // Always set this to D3D11_SDK_VERSION for Windows Runtime apps.
    &device,                    // Returns the Direct3D device created.
    &m_d3dFeatureLevel,         // Returns feature level of device created.
    &context                    // Returns the device immediate context.
);
```

<span data-ttu-id="63f0c-274">**混合式圖形和媒體基礎**</span><span class="sxs-lookup"><span data-stu-id="63f0c-274">**Hybrid graphics and Media Foundation**</span></span>

<span data-ttu-id="63f0c-275">在混合式系統上使用媒體基礎可能會導致影片無法轉譯或視頻材質已損毀的問題。</span><span class="sxs-lookup"><span data-stu-id="63f0c-275">Using Media Foundation on hybrid systems may cause issues where video will not render or video texture is corrupt.</span></span> <span data-ttu-id="63f0c-276">發生這種情況的原因可能是媒體基礎預設為先前所述的系統行為。</span><span class="sxs-lookup"><span data-stu-id="63f0c-276">This can occur because Media Foundation is defaulting to a system behavior as mentioned above.</span></span> <span data-ttu-id="63f0c-277">在某些情況下，需要建立個別的 ID3D11Device 來支援多執行緒處理，並設定正確的建立旗標。</span><span class="sxs-lookup"><span data-stu-id="63f0c-277">In some scenarios, creating a separate ID3D11Device is required to support multi-threading and the correct creation flags are set.</span></span>

<span data-ttu-id="63f0c-278">初始化 ID3D11Device 時，必須將 D3D11_CREATE_DEVICE_VIDEO_SUPPORT 旗標定義為 D3D11_CREATE_DEVICE_FLAG 的一部分。</span><span class="sxs-lookup"><span data-stu-id="63f0c-278">When initializing the ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT flag must be defined as part of the D3D11_CREATE_DEVICE_FLAG.</span></span> <span data-ttu-id="63f0c-279">一旦建立裝置和內容，請呼叫<a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a>來啟用多執行緒處理。</span><span class="sxs-lookup"><span data-stu-id="63f0c-279">Once the device and context is created, call <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> to enable multithreading.</span></span> <span data-ttu-id="63f0c-280">若要將裝置與<a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>建立關聯，請使用<a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager：： ResetDevice</a>函式。</span><span class="sxs-lookup"><span data-stu-id="63f0c-280">To associate the device with the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, use the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> function.</span></span>

<span data-ttu-id="63f0c-281">將**ID3D11Device 與 IMFDXGIDeviceManager 產生關聯的**程式碼：</span><span class="sxs-lookup"><span data-stu-id="63f0c-281">Code to **associate a ID3D11Device with IMFDXGIDeviceManager**:</span></span>

```cpp
// create dx device for media pipeline
winrt::com_ptr<ID3D11Device> spMediaDevice;

// See above. Also make sure to enable the following flags on the D3D11 device:
//   * D3D11_CREATE_DEVICE_VIDEO_SUPPORT
//   * D3D11_CREATE_DEVICE_BGRA_SUPPORT
if (FAILED(CreateMediaDevice(spAdapter.get(), &spMediaDevice)))
    return;                                                     

// Turn multithreading on 
winrt::com_ptr<ID3D10Multithread> spMultithread;
if (spContext.try_as(spMultithread))
{
    spMultithread->SetMultithreadProtected(TRUE);
}

// lock the shared dxgi device manager
// call MFUnlockDXGIDeviceManager when no longer needed
UINT uiResetToken;
winrt::com_ptr<IMFDXGIDeviceManager> spDeviceManager;
hr = MFLockDXGIDeviceManager(&uiResetToken, spDeviceManager.put());
if (FAILED(hr))
    return hr;
    
// associate the device with the manager
hr = spDeviceManager->ResetDevice(spMediaDevice.get(), uiResetToken);
if (FAILED(hr))
    return hr;
```

## <a name="see-also"></a><span data-ttu-id="63f0c-282">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63f0c-282">See also</span></span>
* [<span data-ttu-id="63f0c-283">DirectX 中的座標系統</span><span class="sxs-lookup"><span data-stu-id="63f0c-283">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="63f0c-284">使用 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="63f0c-284">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
