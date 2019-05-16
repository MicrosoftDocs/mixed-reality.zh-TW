---
title: 在 DirectX 中轉譯
description: 說明 Windows Mixed Reality 全像攝影版的呈現方式。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，全像投影、 轉譯、 3D 圖形，HolographicFrame，轉譯迴圈、 更新迴圈、 逐步解說、 範例程式碼
ms.openlocfilehash: 6edcaf808f2d7d48f480169e5579adb8984678a0
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629039"
---
# <a name="rendering-in-directx"></a><span data-ttu-id="45ca7-104">在 DirectX 中轉譯</span><span class="sxs-lookup"><span data-stu-id="45ca7-104">Rendering in DirectX</span></span>

<span data-ttu-id="45ca7-105">Windows Mixed Reality 以產生豐富的 DirectX，3D 圖形化使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="45ca7-105">Windows Mixed Reality is built on DirectX to produce rich, 3D graphical experiences for users.</span></span> <span data-ttu-id="45ca7-106">轉譯抽象位於 DirectX 的正上方，並讓理解的位置和方向的全像攝影版的場景，系統所預測的一或多個觀察者之間的應用程式。</span><span class="sxs-lookup"><span data-stu-id="45ca7-106">The rendering abstraction sits just above DirectX and lets an app reason about the position and orientation of one or more observers of a holographic scene, as predicted by the system.</span></span> <span data-ttu-id="45ca7-107">開發人員可以再找出其全像投影相對於每個網路攝影機，讓應用程式呈現這些全像投影在各種不同的空間座標系統中，當使用者移動。</span><span class="sxs-lookup"><span data-stu-id="45ca7-107">The developer can then locate their holograms relative to each camera, letting the app render these holograms in various spatial coordinate systems as the user moves around.</span></span>

## <a name="update-for-the-current-frame"></a><span data-ttu-id="45ca7-108">更新目前畫面格</span><span class="sxs-lookup"><span data-stu-id="45ca7-108">Update for the current frame</span></span>

<span data-ttu-id="45ca7-109">若要更新全像投影的應用程式狀態，之後每個畫面應用程式將會：</span><span class="sxs-lookup"><span data-stu-id="45ca7-109">To update the application state for holograms, once per frame the app will:</span></span>
* <span data-ttu-id="45ca7-110">取得<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>從顯示的管理系統。</span><span class="sxs-lookup"><span data-stu-id="45ca7-110">Get a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> from the display management system.</span></span>
* <span data-ttu-id="45ca7-111">使用目前的位置 [相機] 檢視時，會轉譯完成預測來更新場景。</span><span class="sxs-lookup"><span data-stu-id="45ca7-111">Update the scene with the current prediction of where the camera view will be when render is completed.</span></span> <span data-ttu-id="45ca7-112">請注意，可以有多個相機在全像攝影版的場景。</span><span class="sxs-lookup"><span data-stu-id="45ca7-112">Note, there can be more than one camera for the holographic scene.</span></span>

<span data-ttu-id="45ca7-113">若要轉譯到全像攝影版的相機的檢視，一次每個畫面應用程式將會：</span><span class="sxs-lookup"><span data-stu-id="45ca7-113">To render to holographic camera views, once per frame the app will:</span></span>
* <span data-ttu-id="45ca7-114">為每部相機，轉譯場景目前畫面格，使用系統從相機檢視和投影矩陣。</span><span class="sxs-lookup"><span data-stu-id="45ca7-114">For each camera, render the scene for the current frame, using the camera view and projection matrices from the system.</span></span>

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a><span data-ttu-id="45ca7-115">建立新的全像攝影版框架，並取得其預測</span><span class="sxs-lookup"><span data-stu-id="45ca7-115">Create a new holographic frame and get its prediction</span></span>

<span data-ttu-id="45ca7-116"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>應用程式能夠更新，並呈現目前的畫面格的資訊。</span><span class="sxs-lookup"><span data-stu-id="45ca7-116">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> has information that the app needs in order to update and render the current frame.</span></span> <span data-ttu-id="45ca7-117">應用程式會開始每個新的畫面格，藉由呼叫**CreateNextFrame**方法。</span><span class="sxs-lookup"><span data-stu-id="45ca7-117">The app begins each new frame by calling the **CreateNextFrame** method.</span></span> <span data-ttu-id="45ca7-118">呼叫這個方法時，做出的預測會使用最新的感應器資料可用，且封裝中**CurrentPrediction**物件。</span><span class="sxs-lookup"><span data-stu-id="45ca7-118">When this method is called, predictions are made using the latest sensor data available, and encapsulated in **CurrentPrediction** object.</span></span>

<span data-ttu-id="45ca7-119">新的框架物件必須用於每個呈現的畫面格，因為它只適用於針對即時的時間。</span><span class="sxs-lookup"><span data-stu-id="45ca7-119">A new frame object must be used for each rendered frame as it is only valid for an instant in time.</span></span> <span data-ttu-id="45ca7-120">**CurrentPrediction**屬性包含觀景窗位置等資訊。</span><span class="sxs-lookup"><span data-stu-id="45ca7-120">The **CurrentPrediction** property contains information such as the camera position.</span></span> <span data-ttu-id="45ca7-121">資訊會推斷為確切的時間擷取的框架時預期會向使用者顯示的時間。</span><span class="sxs-lookup"><span data-stu-id="45ca7-121">The information is extrapolated to the exact moment in time when the frame is expected to be visible to the user.</span></span>

<span data-ttu-id="45ca7-122">下列程式碼摘錄自**AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="45ca7-122">The following code is excerpted from **AppMain::Update**:</span></span>

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a><span data-ttu-id="45ca7-123">處理序相機更新</span><span class="sxs-lookup"><span data-stu-id="45ca7-123">Process camera updates</span></span>

<span data-ttu-id="45ca7-124">背景緩衝區可以變更框架框架。</span><span class="sxs-lookup"><span data-stu-id="45ca7-124">Back buffers can change from frame to frame.</span></span> <span data-ttu-id="45ca7-125">您的應用程式需求，來驗證上一步為每部相機，緩衝處理和發行，並視需要重新建立資源檢視與深度緩衝區。</span><span class="sxs-lookup"><span data-stu-id="45ca7-125">Your app needs to validate the back buffer for each camera, and release and recreate resource views and depth buffers as needed.</span></span> <span data-ttu-id="45ca7-126">請注意，在預測中帶來一組的目前框架中正在使用的數位相機的授權清單。</span><span class="sxs-lookup"><span data-stu-id="45ca7-126">Notice that the set of poses in the prediction is the authoritative list of cameras being used in the current frame.</span></span> <span data-ttu-id="45ca7-127">通常，您可以使用這份清單的數位相機上逐一查看。</span><span class="sxs-lookup"><span data-stu-id="45ca7-127">Usually, you use this list to iterate on the set of cameras.</span></span>

<span data-ttu-id="45ca7-128">從**AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="45ca7-128">From **AppMain::Update**:</span></span>

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

<span data-ttu-id="45ca7-129">從**DeviceResources::EnsureCameraResources**:</span><span class="sxs-lookup"><span data-stu-id="45ca7-129">From **DeviceResources::EnsureCameraResources**:</span></span>

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a><span data-ttu-id="45ca7-130">取得要用於轉譯做為基礎的座標系統</span><span class="sxs-lookup"><span data-stu-id="45ca7-130">Get the coordinate system to use as a basis for rendering</span></span>

<span data-ttu-id="45ca7-131">Windows Mixed Reality 可讓您建立各種不同的應用程式[座標系統](coordinate-systems-in-directx.md)，如有需要例如附加的參考框架和靜態參考框架中，追蹤在真實世界的位置。</span><span class="sxs-lookup"><span data-stu-id="45ca7-131">Windows Mixed Reality lets your app create various [coordinate systems](coordinate-systems-in-directx.md) as needed, such as the attached reference frame and the stationary reference frame, that track locations in the physical world.</span></span> <span data-ttu-id="45ca7-132">您的應用程式接著可以使用這些座標系統，原因有關呈現全像投影每個畫面格的何處。</span><span class="sxs-lookup"><span data-stu-id="45ca7-132">Your app can then use these coordinate systems to reason about where to render holograms each frame.</span></span> <span data-ttu-id="45ca7-133">當要求座標，從 API，您將會永遠傳入<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>內您想要用來表示這些座標。</span><span class="sxs-lookup"><span data-stu-id="45ca7-133">When requesting coordinates from an API, you will always pass in the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> within which you want those coordinates to be expressed.</span></span>

<span data-ttu-id="45ca7-134">從**AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="45ca7-134">From **AppMain::Update**:</span></span>

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

<span data-ttu-id="45ca7-135">這些座標系統可用來轉譯場景中的內容時，產生立體聲的檢視矩陣。</span><span class="sxs-lookup"><span data-stu-id="45ca7-135">These coordinate systems can then be used to generate stereo view matrices when rendering the content in your scene.</span></span>

<span data-ttu-id="45ca7-136">從**CameraResources::UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="45ca7-136">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a><span data-ttu-id="45ca7-137">處理序視線和輸入筆勢</span><span class="sxs-lookup"><span data-stu-id="45ca7-137">Process gaze and gesture input</span></span>

<span data-ttu-id="45ca7-138">[視線](gaze-in-directx.md)並[手](hands-and-motion-controllers-in-directx.md)輸入不是以時間為基礎，因此不需要在更新**StepTimer**函式。</span><span class="sxs-lookup"><span data-stu-id="45ca7-138">[Gaze](gaze-in-directx.md) and [hand](hands-and-motion-controllers-in-directx.md) input are not time-based and thus do not have to update in the **StepTimer** function.</span></span> <span data-ttu-id="45ca7-139">不過這項輸入是應用程式需要查看每個畫面格的項目。</span><span class="sxs-lookup"><span data-stu-id="45ca7-139">However this input is something that the app needs to look at each frame.</span></span>

### <a name="process-time-based-updates"></a><span data-ttu-id="45ca7-140">處理時間為基礎的更新</span><span class="sxs-lookup"><span data-stu-id="45ca7-140">Process time-based updates</span></span>

<span data-ttu-id="45ca7-141">任何即時轉譯應用程式將會需要某種方式來處理時間為基礎的更新;我們會提供方法來執行這項操作的 Windows 全像攝影版的應用程式範本，透過**StepTimer**實作。</span><span class="sxs-lookup"><span data-stu-id="45ca7-141">Any real-time rendering app will need some way to process time-based updates; we provide a way to do this in the Windows Holographic app template via a **StepTimer** implementation.</span></span> <span data-ttu-id="45ca7-142">提供在 DirectX 11 UWP 應用程式範本中，因此如果您已經看過該範本您應該在熟悉的基礎，這是類似於 StepTimer。</span><span class="sxs-lookup"><span data-stu-id="45ca7-142">This is similar to the StepTimer provided in the DirectX 11 UWP app template, so if you already have looked at that template you should be on familiar ground.</span></span> <span data-ttu-id="45ca7-143">此 StepTimer 範例協助程式類別能夠提供固定的時間步驟更新，以及變數的時間步驟更新，而預設模式是可變的時間步驟。</span><span class="sxs-lookup"><span data-stu-id="45ca7-143">This StepTimer sample helper class is able to provide fixed time-step updates, as well as variable time-step updates, and the default mode is variable time steps.</span></span>

<span data-ttu-id="45ca7-144">在全像攝影版的呈現方式，我們特別選擇不將放入計時器函式太多。</span><span class="sxs-lookup"><span data-stu-id="45ca7-144">In the case of holographic rendering, we've specifically chosen not to put too much into the timer function.</span></span> <span data-ttu-id="45ca7-145">這是因為您可以將它設定為固定的時間步驟就是，在此情況下可能會取得呼叫它一次以上每個畫面 – 或完全沒有，一些畫面格 – 而且我們全像攝影版的資料更新應該一次發生的每個畫面。</span><span class="sxs-lookup"><span data-stu-id="45ca7-145">This is because you can configure it to be a fixed time step, in which case it might get called more than once per frame – or not at all, for some frames – and our holographic data updates should happen once per frame.</span></span>


<span data-ttu-id="45ca7-146">從**AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="45ca7-146">From **AppMain::Update**:</span></span>

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a><span data-ttu-id="45ca7-147">位置和旋轉全像投影座標系統中</span><span class="sxs-lookup"><span data-stu-id="45ca7-147">Position and rotate holograms in your coordinate system</span></span>

<span data-ttu-id="45ca7-148">如果您在範本會執行與單一的座標系統中，在操作**SpatialStationaryReferenceFrame**，此程序不是不同於您是否則用於 3D 圖形。</span><span class="sxs-lookup"><span data-stu-id="45ca7-148">If you are operating in a single coordinate system, as the template does with the **SpatialStationaryReferenceFrame**, this process isn't different from what you're otherwise used to in 3D graphics.</span></span> <span data-ttu-id="45ca7-149">在這裡，我們會旋轉 cube 和相對靜態的座標系統中設定的模型矩陣。</span><span class="sxs-lookup"><span data-stu-id="45ca7-149">Here, we rotate the cube and set the model matrix relative to the position in the stationary coordinate system.</span></span>

<span data-ttu-id="45ca7-150">從**SpinningCubeRenderer::Update**:</span><span class="sxs-lookup"><span data-stu-id="45ca7-150">From **SpinningCubeRenderer::Update**:</span></span>

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

<span data-ttu-id="45ca7-151">**請注意進階案例相關：** 旋轉立方體是如何定位雷射單一參考範圍內的一個非常簡單的範例。</span><span class="sxs-lookup"><span data-stu-id="45ca7-151">**Note about advanced scenarios:** The spinning cube is a very simple example of how to position a hologram within a single reference frame.</span></span> <span data-ttu-id="45ca7-152">它也可[使用多個 SpatialCoordinateSystems](coordinate-systems-in-directx.md)在同一個轉譯框架中，在相同的時間。</span><span class="sxs-lookup"><span data-stu-id="45ca7-152">It's also possible to [use multiple SpatialCoordinateSystems](coordinate-systems-in-directx.md) in the same rendered frame, at the same time.</span></span>

### <a name="update-constant-buffer-data"></a><span data-ttu-id="45ca7-153">更新常數緩衝區的資料</span><span class="sxs-lookup"><span data-stu-id="45ca7-153">Update constant buffer data</span></span>

<span data-ttu-id="45ca7-154">模型內容的轉換會如往常般更新。</span><span class="sxs-lookup"><span data-stu-id="45ca7-154">Model transforms for content are updated as usual.</span></span> <span data-ttu-id="45ca7-155">到目前為止，您將計算座標系統中，您會在轉譯的有效的轉換。</span><span class="sxs-lookup"><span data-stu-id="45ca7-155">By now, you will have computed valid transforms for the coordinate system you'll be rendering in.</span></span>

<span data-ttu-id="45ca7-156">從**SpinningCubeRenderer::Update**:</span><span class="sxs-lookup"><span data-stu-id="45ca7-156">From **SpinningCubeRenderer::Update**:</span></span>

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

<span data-ttu-id="45ca7-157">檢視和投影轉換呢？</span><span class="sxs-lookup"><span data-stu-id="45ca7-157">What about view and projection transforms?</span></span> <span data-ttu-id="45ca7-158">為了獲得最佳結果，我們想要等到之前我們啟用這些我們幾乎準備好我們的繪製呼叫。</span><span class="sxs-lookup"><span data-stu-id="45ca7-158">For best results, we want to wait until we're almost ready for our draw calls before we get these.</span></span>

## <a name="render-the-current-frame"></a><span data-ttu-id="45ca7-159">呈現目前的框架</span><span class="sxs-lookup"><span data-stu-id="45ca7-159">Render the current frame</span></span>

<span data-ttu-id="45ca7-160">轉譯 Windows Mixed reality 沒有太大差異呈現 2D mono 在顯示上，但有一些要注意的差異：</span><span class="sxs-lookup"><span data-stu-id="45ca7-160">Rendering on Windows Mixed Reality is not much different from rendering on a 2D mono display, but there are some differences you need to be aware of:</span></span>
* <span data-ttu-id="45ca7-161">全像攝影版的框架預測很重要。</span><span class="sxs-lookup"><span data-stu-id="45ca7-161">Holographic frame predictions are important.</span></span> <span data-ttu-id="45ca7-162">接近預測可看到您的畫面格時，您全像投影起來愈好。</span><span class="sxs-lookup"><span data-stu-id="45ca7-162">The closer the prediction is to when your frame is presented, the better your holograms will look.</span></span>
* <span data-ttu-id="45ca7-163">Windows Mixed Reality 控制相機檢視。</span><span class="sxs-lookup"><span data-stu-id="45ca7-163">Windows Mixed Reality controls the camera views.</span></span> <span data-ttu-id="45ca7-164">您要轉譯為每一項，因為全像攝影版的框架將會呈現為您更新版本。</span><span class="sxs-lookup"><span data-stu-id="45ca7-164">You need to render to each one because the holographic frame will be presenting them for you later.</span></span>
* <span data-ttu-id="45ca7-165">立體聲的轉譯，建議使用執行個體的繪製到轉譯目標陣列來完成。</span><span class="sxs-lookup"><span data-stu-id="45ca7-165">Stereo rendering is recommended to be accomplished using instanced drawing to a render target array.</span></span> <span data-ttu-id="45ca7-166">全像攝影版的應用程式範本使用的執行個體繪製到轉譯目標陣列，它會使用到的轉譯目標檢視建議的方法**Texture2DArray**。</span><span class="sxs-lookup"><span data-stu-id="45ca7-166">The holographic app template uses the recommended approach of instanced drawing to a render target array, which uses a render target view onto a **Texture2DArray**.</span></span>
* <span data-ttu-id="45ca7-167">如果您想要呈現而不需使用立體聲的執行個體，您必須建立兩個非陣列 RenderTargetViews （一個眼睛） 中的每個參考其中的兩個配量所**Texture2DArray**從系統提供的應用程式。</span><span class="sxs-lookup"><span data-stu-id="45ca7-167">If you want to render without using stereo instancing, you will need to create two non-array RenderTargetViews (one for each eye) that each reference one of the two slices in the **Texture2DArray** provided to the app from the system.</span></span> <span data-ttu-id="45ca7-168">這不是建議，因為它通常是顯著低於使用執行個體。</span><span class="sxs-lookup"><span data-stu-id="45ca7-168">This is not recommended, as it is typically significantly slower than using instancing.</span></span>

### <a name="get-an-updated-holographicframe-prediction"></a><span data-ttu-id="45ca7-169">取得已更新的 HolographicFrame 預測</span><span class="sxs-lookup"><span data-stu-id="45ca7-169">Get an updated HolographicFrame prediction</span></span>

<span data-ttu-id="45ca7-170">更新框架預測增強影像穩定的效率，而且允許更精確的定位，因為較短的時間之間的預測和框架時向使用者顯示全像投影。</span><span class="sxs-lookup"><span data-stu-id="45ca7-170">Updating the frame prediction enhances the effectiveness of image stabilization and allows for more accurate positioning of holograms due to the shorter time between the prediction and when the frame is visible to the user.</span></span> <span data-ttu-id="45ca7-171">在理想情況下更新之前呈現在框架預測。</span><span class="sxs-lookup"><span data-stu-id="45ca7-171">Ideally update your frame prediction just before rendering.</span></span>

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a><span data-ttu-id="45ca7-172">轉譯為每部相機</span><span class="sxs-lookup"><span data-stu-id="45ca7-172">Render to each camera</span></span>

<span data-ttu-id="45ca7-173">上的相機會帶來在預測中，集合執行迴圈，並轉譯為每個在此集合中的相機。</span><span class="sxs-lookup"><span data-stu-id="45ca7-173">Loop on the set of camera poses in the prediction, and render to each camera in this set.</span></span>

<span data-ttu-id="45ca7-174">**設定轉譯階段**</span><span class="sxs-lookup"><span data-stu-id="45ca7-174">**Set up your rendering pass**</span></span>

<span data-ttu-id="45ca7-175">Windows Mixed Reality 使用立體視覺呈現來增強深度的幻影並呈現 stereoscopically，因此左邊和右邊顯示作用中。</span><span class="sxs-lookup"><span data-stu-id="45ca7-175">Windows Mixed Reality uses stereoscopic rendering to enhance the illusion of depth and to render stereoscopically, so both the left and the right display are active.</span></span> <span data-ttu-id="45ca7-176">使用立體視覺呈現位移之間沒有兩部顯示器，大腦可以協調為實際的深度。</span><span class="sxs-lookup"><span data-stu-id="45ca7-176">With stereoscopic rendering there is an offset between the two displays, which the brain can reconcile as actual depth.</span></span> <span data-ttu-id="45ca7-177">此章節涵蓋 stereoscopic 轉譯使用執行個體中，使用程式碼的 Windows 全像攝影版的應用程式範本。</span><span class="sxs-lookup"><span data-stu-id="45ca7-177">This section covers stereoscopic rendering using instancing, using code from the Windows Holographic app template.</span></span>

<span data-ttu-id="45ca7-178">每部相機有它自己的轉譯目標 （背景緩衝區），以及檢視和投影矩陣，到全像攝影版的空間。</span><span class="sxs-lookup"><span data-stu-id="45ca7-178">Each camera has its own render target (back buffer), and view and projection matrices, into the holographic space.</span></span> <span data-ttu-id="45ca7-179">您的應用程式必須建立任何其他觀景窗基礎資源，例如深度緩衝區，以每個數位相機為基礎。</span><span class="sxs-lookup"><span data-stu-id="45ca7-179">Your app will need to create any other camera-based resources - such as the depth buffer - on a per-camera basis.</span></span> <span data-ttu-id="45ca7-180">在 Windows 全像攝影版的應用程式範本中，我們提供 DX::CameraResources 中一起結合這些資源的協助程式類別。</span><span class="sxs-lookup"><span data-stu-id="45ca7-180">In the Windows Holographic app template, we provide a helper class to bundle these resources together in DX::CameraResources.</span></span> <span data-ttu-id="45ca7-181">著手設定呈現目標檢視：</span><span class="sxs-lookup"><span data-stu-id="45ca7-181">Start by setting up the render target views:</span></span>

<span data-ttu-id="45ca7-182">從**AppMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="45ca7-182">From **AppMain::Render**:</span></span>

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

<span data-ttu-id="45ca7-183">**使用預測獲得相機中的檢視和投影矩陣**</span><span class="sxs-lookup"><span data-stu-id="45ca7-183">**Use the prediction to get the view and projection matrices for the camera**</span></span>

<span data-ttu-id="45ca7-184">每個畫面格會變更每個全像攝影版的相機的檢視和投影矩陣。</span><span class="sxs-lookup"><span data-stu-id="45ca7-184">The view and projection matrices for each holographic camera will change with every frame.</span></span> <span data-ttu-id="45ca7-185">重新整理每個全像攝影版的相機的常數緩衝區中的資料。</span><span class="sxs-lookup"><span data-stu-id="45ca7-185">Refresh the data in the constant buffer for each holographic camera.</span></span> <span data-ttu-id="45ca7-186">這樣做，更新預測之後，而且會在進行之前任何繪製呼叫該相機。</span><span class="sxs-lookup"><span data-stu-id="45ca7-186">Do this after you updated the prediction, and before you make any draw calls for that camera.</span></span>

<span data-ttu-id="45ca7-187">從**AppMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="45ca7-187">From **AppMain::Render**:</span></span>

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

<span data-ttu-id="45ca7-188">在這裡，我們會示範如何從相機姿勢取得矩陣。</span><span class="sxs-lookup"><span data-stu-id="45ca7-188">Here, we show how the matrices are acquired from the camera pose.</span></span> <span data-ttu-id="45ca7-189">在此過程中我們也會取得目前的檢視區的相機。</span><span class="sxs-lookup"><span data-stu-id="45ca7-189">During this process we also obtain the current viewport for the camera.</span></span> <span data-ttu-id="45ca7-190">請注意我們如何提供座標系統： 這是我們用來了解視線，相同的座標系統，而且同一個我們用來定位的旋轉立方體。</span><span class="sxs-lookup"><span data-stu-id="45ca7-190">Note how we provide a coordinate system: this is the same coordinate system we used to understand gaze, and it's the same one we used to position the spinning cube.</span></span>


<span data-ttu-id="45ca7-191">從**CameraResources::UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="45ca7-191">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

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

<span data-ttu-id="45ca7-192">檢視區應該設定為每個畫面格。</span><span class="sxs-lookup"><span data-stu-id="45ca7-192">The viewport should be set each frame.</span></span> <span data-ttu-id="45ca7-193">頂點著色器 （至少） 通常需要檢視/投影資料的存取權。</span><span class="sxs-lookup"><span data-stu-id="45ca7-193">Your vertex shader (at least) will generally need access to the view/projection data.</span></span>


<span data-ttu-id="45ca7-194">從**CameraResources::AttachViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="45ca7-194">From **CameraResources::AttachViewProjectionBuffer**:</span></span>

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

<span data-ttu-id="45ca7-195">**轉譯為相機背景緩衝區，並認可深度緩衝區**:</span><span class="sxs-lookup"><span data-stu-id="45ca7-195">**Render to the camera back buffer and commit the depth buffer**:</span></span>

<span data-ttu-id="45ca7-196">它是個不錯的主意，以確認**TryGetViewTransform**成功 」，才能嘗試使用 檢視/預估的資料，因為如果找不到 座標系統 （例如，追蹤已中斷） 您的應用程式無法與它轉譯，框架。</span><span class="sxs-lookup"><span data-stu-id="45ca7-196">It's a good idea to check that **TryGetViewTransform** succeeded before trying to use the view/projection data, because if the coordinate system is not locatable (e.g., tracking was interrupted) your app cannot render with it for that frame.</span></span> <span data-ttu-id="45ca7-197">範本只會呼叫**呈現**上的旋轉立方體如果**CameraResources**類別會指出成功的更新。</span><span class="sxs-lookup"><span data-stu-id="45ca7-197">The template only calls **Render** on the spinning cube if the **CameraResources** class indicates a successful update.</span></span>

<span data-ttu-id="45ca7-198">若要保留全像投影，開發人員或使用者將它們放在世界中，Windows Mixed Reality 包含的功能[映像穩定](hologram-stability.md)。</span><span class="sxs-lookup"><span data-stu-id="45ca7-198">To keep holograms where a developer or a user puts them in the world, Windows Mixed Reality includes features for [image stabilization](hologram-stability.md).</span></span> <span data-ttu-id="45ca7-199">映像穩定協助隱藏轉譯管線，以確保最佳的使用者; 全像攝影版體驗中固有的延遲增強影像穩定進一步延伸，可指定婧鎏鶗懘或深度緩衝區可能會計算最佳化的映像穩定，即時提供。</span><span class="sxs-lookup"><span data-stu-id="45ca7-199">Image stabilization helps hide the latency inherent in a rendering pipeline to ensure the best holographic experiences for users; a focus point may be specified to enhance image stabilization even further, or a depth buffer may be provided to compute optimized image stabilization in real time.</span></span>

<span data-ttu-id="45ca7-200">為了獲得最佳結果，您的應用程式應該提供使用深度緩衝區<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API。</span><span class="sxs-lookup"><span data-stu-id="45ca7-200">For best results, your app should provide a depth buffer using the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API.</span></span> <span data-ttu-id="45ca7-201">Windows Mixed Reality 然後可以使用幾何資訊從深度緩衝區來最佳化即時的映像穩定。</span><span class="sxs-lookup"><span data-stu-id="45ca7-201">Windows Mixed Reality can then use geometry information from the depth buffer to optimize image stabilization in real time.</span></span> <span data-ttu-id="45ca7-202">Windows 全像攝影版的應用程式範本會根據預設，協助最佳化全像穩定性認可應用程式的深度緩衝區。</span><span class="sxs-lookup"><span data-stu-id="45ca7-202">The Windows Holographic app template commits the app's depth buffer by default, helping optimize hologram stability.</span></span>

<span data-ttu-id="45ca7-203">從**AppMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="45ca7-203">From **AppMain::Render**:</span></span>

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
><span data-ttu-id="45ca7-204">Windows 會處理您深度紋理，GPU 上的，因此您必須能夠深度緩衝區做為著色器資源。</span><span class="sxs-lookup"><span data-stu-id="45ca7-204">Windows will process your depth texture on the GPU, so it must be possible to use your depth buffer as a shader resource.</span></span> <span data-ttu-id="45ca7-205">無類型的格式應為您建立 ID3D11Texture2D，應該做為著色器資源檢視繫結。</span><span class="sxs-lookup"><span data-stu-id="45ca7-205">The ID3D11Texture2D that you create should be in a typeless format and it should be bound as a shader resource view.</span></span> <span data-ttu-id="45ca7-206">以下是如何建立能認可的映像穩定的深度材質的範例。</span><span class="sxs-lookup"><span data-stu-id="45ca7-206">Here is an example of how to create a depth texture that can be committed for image stabilization.</span></span>

<span data-ttu-id="45ca7-207">程式碼**CommitDirect3D11DepthBuffer 深度緩衝區資源建立**:</span><span class="sxs-lookup"><span data-stu-id="45ca7-207">Code for **Depth buffer resource creation for CommitDirect3D11DepthBuffer**:</span></span>

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

<span data-ttu-id="45ca7-208">**繪製全像攝影版的內容**</span><span class="sxs-lookup"><span data-stu-id="45ca7-208">**Draw holographic content**</span></span>

<span data-ttu-id="45ca7-209">Windows 全像攝影版的應用程式範本使用的執行個體的幾何繪製 Texture2DArray 的大小為 2 的建議的技術，以呈現立體聲中的內容。</span><span class="sxs-lookup"><span data-stu-id="45ca7-209">The Windows Holographic app template renders content in stereo by using the recommended technique of drawing instanced geometry to a Texture2DArray of size 2.</span></span> <span data-ttu-id="45ca7-210">讓我們看看此範例和 Windows Mixed reality 的運作方式的執行個體部分。</span><span class="sxs-lookup"><span data-stu-id="45ca7-210">Let's look at the instancing part of this, and how it works on Windows Mixed Reality.</span></span>

<span data-ttu-id="45ca7-211">從**SpinningCubeRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="45ca7-211">From **SpinningCubeRenderer::Render**:</span></span>

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

<span data-ttu-id="45ca7-212">每個執行個體從常數緩衝區中存取不同的檢視/投影矩陣。</span><span class="sxs-lookup"><span data-stu-id="45ca7-212">Each instance accesses a different view/projection matrix from the constant buffer.</span></span> <span data-ttu-id="45ca7-213">以下是常數緩衝區結構，也就是只要 2 個矩陣的陣列。</span><span class="sxs-lookup"><span data-stu-id="45ca7-213">Here's the constant buffer structure, which is just an array of 2 matrices.</span></span>

<span data-ttu-id="45ca7-214">從**VertexShaderShared.hlsl**，以包含**VPRTVertexShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="45ca7-214">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

<span data-ttu-id="45ca7-215">呈現目標陣列索引必須為每個像素。</span><span class="sxs-lookup"><span data-stu-id="45ca7-215">The render target array index must be set for each pixel.</span></span> <span data-ttu-id="45ca7-216">在下列程式碼片段，output.viewId 會對應至**SV_RenderTargetArrayIndex**語意。</span><span class="sxs-lookup"><span data-stu-id="45ca7-216">In the following snippet, output.viewId is mapped to the **SV_RenderTargetArrayIndex** semantic.</span></span> <span data-ttu-id="45ca7-217">請注意，這需要支援選擇性的 Direct3D 11.3 功能，可呈現目標陣列索引語意從任何著色器階段進行設定。</span><span class="sxs-lookup"><span data-stu-id="45ca7-217">Note that this requires support for an optional Direct3D 11.3 feature, which allows the render target array index semantic to be set from any shader stage.</span></span>

<span data-ttu-id="45ca7-218">從**VPRTVertexShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="45ca7-218">From **VPRTVertexShader.hlsl**:</span></span>

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

<span data-ttu-id="45ca7-219">從**VertexShaderShared.hlsl**，以包含**VPRTVertexShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="45ca7-219">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

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

<span data-ttu-id="45ca7-220">如果您想要使用您現有的執行個體使用此方法的繪圖至立體音響的繪圖技術呈現目標陣列，您只需要繪製兩次您通常需要的執行個體數目。</span><span class="sxs-lookup"><span data-stu-id="45ca7-220">If you want to use your existing instanced drawing techniques with this method of drawing to a stereo render target array, all you have to do is draw twice the number of instances you normally have.</span></span> <span data-ttu-id="45ca7-221">在 著色器，將分割**input.instId** 2 取得的原始執行個體識別碼，這可以編製索引 （舉例來說） 每個物件資料的緩衝區： `int actualIdx = input.instId / 2;`</span><span class="sxs-lookup"><span data-stu-id="45ca7-221">In the shader, divide **input.instId** by 2 to get the original instance ID, which can be indexed into (for example) a buffer of per-object data: `int actualIdx = input.instId / 2;`</span></span>

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a><span data-ttu-id="45ca7-222">呈現 HoloLens 上的是立體聲內容的重要注意事項</span><span class="sxs-lookup"><span data-stu-id="45ca7-222">Important note about rendering stereo content on HoloLens</span></span>

<span data-ttu-id="45ca7-223">Windows Mixed Reality 能夠從任何的著色器階段; 設定的轉譯目標陣列索引一般來說，這是只能在幾何著色器階段中，因為語意定義適用於 Direct3D 11 的方式工作。</span><span class="sxs-lookup"><span data-stu-id="45ca7-223">Windows Mixed Reality supports the ability to set the render target array index from any shader stage; normally, this is a task that could only be done in the geometry shader stage due to the way the semantic is defined for Direct3D 11.</span></span> <span data-ttu-id="45ca7-224">在這裡，我們會示範如何設定端點和像素著色器階段組合作為轉譯管線的完整範例。</span><span class="sxs-lookup"><span data-stu-id="45ca7-224">Here, we show a complete example of how to set up a rendering pipeline with just the vertex and pixel shader stages set.</span></span> <span data-ttu-id="45ca7-225">著色器程式碼是上面所述。</span><span class="sxs-lookup"><span data-stu-id="45ca7-225">The shader code is as described above.</span></span>

<span data-ttu-id="45ca7-226">從**SpinningCubeRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="45ca7-226">From **SpinningCubeRenderer::Render**:</span></span>

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

### <a name="important-note-about-rendering-on-non-hololens-devices"></a><span data-ttu-id="45ca7-227">關於非 HoloLens 裝置上轉譯的重要注意事項</span><span class="sxs-lookup"><span data-stu-id="45ca7-227">Important note about rendering on non-HoloLens devices</span></span>

<span data-ttu-id="45ca7-228">在 端點著色器中設定的轉譯目標陣列索引需要圖形驅動程式支援的選用的 Direct3D 11.3 功能，支援 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="45ca7-228">Setting the render target array index in the vertex shader requires that the graphics driver supports an optional Direct3D 11.3 feature, which HoloLens does support.</span></span> <span data-ttu-id="45ca7-229">您的應用程式可以安全地實作該技術進行轉譯，並在 Microsoft HoloLens 上執行，將會符合所有需求。</span><span class="sxs-lookup"><span data-stu-id="45ca7-229">Your app may be able to safely implement just that technique for rendering, and all requirements will be met for running on the Microsoft HoloLens.</span></span>

<span data-ttu-id="45ca7-230">可能的情況下，您想要使用 HoloLens 模擬器，這可以是您全像攝影版的應用程式-功能強大的開發工具，並支援連接至 Windows 10 電腦的 Windows Mixed Reality 沈浸式耳機裝置。</span><span class="sxs-lookup"><span data-stu-id="45ca7-230">It may be the case that you want to use the HoloLens emulator as well, which can be a powerful development tool for your holographic app - and support Windows Mixed Reality immersive headset devices that are attached to Windows 10 PCs.</span></span> <span data-ttu-id="45ca7-231">因此，所有的 Windows Mixed Reality-也會內建的 Windows 全像攝影版的應用程式範本和支援非 HoloLens 轉譯路徑。</span><span class="sxs-lookup"><span data-stu-id="45ca7-231">Support for the non-HoloLens rendering path - and therefore, for all of Windows Mixed Reality - is also built into the Windows Holographic app template.</span></span> <span data-ttu-id="45ca7-232">在範本程式碼中，您會發現程式碼，讓您全像攝影版的應用程式在開發電腦中，於 GPU 上執行。</span><span class="sxs-lookup"><span data-stu-id="45ca7-232">In the template code, you will find code to enable your holographic app to run on the GPU in your development PC.</span></span> <span data-ttu-id="45ca7-233">以下是如何**DeviceResources**類別檢查這項選擇性功能支援。</span><span class="sxs-lookup"><span data-stu-id="45ca7-233">Here is how the **DeviceResources** class checks for this optional feature support.</span></span>

<span data-ttu-id="45ca7-234">從**DeviceResources::CreateDeviceResources**:</span><span class="sxs-lookup"><span data-stu-id="45ca7-234">From **DeviceResources::CreateDeviceResources**:</span></span>

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

<span data-ttu-id="45ca7-235">若要支援轉譯，而不需要此選擇性功能，您的應用程式必須使用幾何著色器設定的轉譯目標陣列索引。</span><span class="sxs-lookup"><span data-stu-id="45ca7-235">To support rendering without this optional feature, your app must use a geometry shader to set the render target array index.</span></span> <span data-ttu-id="45ca7-236">會加入此程式碼片段*之後* **VSSetConstantBuffers**，並*之前* **Pssetshade**先前所示的程式碼範例說明如何呈現 HoloLens 上的立體聲的區段。</span><span class="sxs-lookup"><span data-stu-id="45ca7-236">This snippet would be added *after* **VSSetConstantBuffers**, and *before* **PSSetShader** in the code example shown in the previous section that explains how to render stereo on HoloLens.</span></span>

<span data-ttu-id="45ca7-237">從**SpinningCubeRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="45ca7-237">From **SpinningCubeRenderer::Render**:</span></span>

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

<span data-ttu-id="45ca7-238">**HLSL 注意**:在此情況下，您也必須載入稍經修改的端點著色器給使用一律允許著色器語意，例如 TEXCOORD0 幾何著色器的轉譯目標陣列索引。</span><span class="sxs-lookup"><span data-stu-id="45ca7-238">**HLSL NOTE**: In this case, you must also load a slightly modified vertex shader that passes the render target array index to the geometry shader using an always-allowed shader semantic, such as TEXCOORD0.</span></span> <span data-ttu-id="45ca7-239">幾何著色器沒有執行任何工作;範本幾何著色器通過所有的資料，除了用來設定 SV_RenderTargetArrayIndex 語意的轉譯目標陣列索引。</span><span class="sxs-lookup"><span data-stu-id="45ca7-239">The geometry shader does not have to do any work; the template geometry shader passes through all data, with the exception of the render target array index, which is used to set the SV_RenderTargetArrayIndex semantic.</span></span>

<span data-ttu-id="45ca7-240">應用程式範本程式碼**GeometryShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="45ca7-240">App template code for **GeometryShader.hlsl**:</span></span>

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

## <a name="present"></a><span data-ttu-id="45ca7-241">目前</span><span class="sxs-lookup"><span data-stu-id="45ca7-241">Present</span></span>

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a><span data-ttu-id="45ca7-242">啟用全像攝影版的畫面格呈現交換鏈結</span><span class="sxs-lookup"><span data-stu-id="45ca7-242">Enable the holographic frame to present the swap chain</span></span>

<span data-ttu-id="45ca7-243">使用 Windows Mixed Reality，系統會控制交換鏈結。</span><span class="sxs-lookup"><span data-stu-id="45ca7-243">With Windows Mixed Reality, the system controls the swap chain.</span></span> <span data-ttu-id="45ca7-244">系統接著會管理做簡報的畫面格數到每個全像攝影版的攝影機，以確保高品質使用者經驗。</span><span class="sxs-lookup"><span data-stu-id="45ca7-244">The system then manages presenting frames to each holographic camera to ensure a high quality user experience.</span></span> <span data-ttu-id="45ca7-245">它也提供的檢視區的更新，請在每個畫面格，為每部相機，以最佳化例如映像穩定或混合實境擷取系統的層面。</span><span class="sxs-lookup"><span data-stu-id="45ca7-245">It also provides a viewport update each frame, for each camera, to optimize aspects of the system such as image stabilization or Mixed Reality Capture.</span></span> <span data-ttu-id="45ca7-246">因此，使用 DirectX 的全像攝影版的應用程式並不會呼叫**存在**DXGI 上交換鏈結。</span><span class="sxs-lookup"><span data-stu-id="45ca7-246">So, a holographic app using DirectX doesn't call **Present** on a DXGI swap chain.</span></span> <span data-ttu-id="45ca7-247">相反地，您使用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>類別來呈現畫面格的所有交換鏈結，一旦您完成繪製它。</span><span class="sxs-lookup"><span data-stu-id="45ca7-247">Instead, you use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class to present all swapchains for a frame once you're done drawing it.</span></span>

<span data-ttu-id="45ca7-248">從**DeviceResources::Present**:</span><span class="sxs-lookup"><span data-stu-id="45ca7-248">From **DeviceResources::Present**:</span></span>

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

<span data-ttu-id="45ca7-249">根據預設，此 API 會等到完成後，才能傳回框架。</span><span class="sxs-lookup"><span data-stu-id="45ca7-249">By default, this API waits for the frame to finish before it returns.</span></span> <span data-ttu-id="45ca7-250">全像攝影版的應用程式應該等待前一個畫面格，才能開始新的框架的工作，因為這可減少延遲，並從全像攝影版的框架預測更好的結果是用來完成。</span><span class="sxs-lookup"><span data-stu-id="45ca7-250">Holographic apps should wait for the previous frame to finish before starting work on a new frame, because this reduces latency and allows for better results from holographic frame predictions.</span></span> <span data-ttu-id="45ca7-251">這不是永久的規則，以及如果您有畫面格所花費時間超過一個畫面重新整理，以呈現您可以停用這項等候傳遞的 HolographicFramePresentWaitBehavior 參數<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>。</span><span class="sxs-lookup"><span data-stu-id="45ca7-251">This isn't a hard rule, and if you have frames that take longer than one screen refresh to render you can disable this wait by passing the HolographicFramePresentWaitBehavior parameter to <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span></span> <span data-ttu-id="45ca7-252">在此情況下，您可能會維持在 GPU 上的連續載入中使用非同步轉譯執行緒。</span><span class="sxs-lookup"><span data-stu-id="45ca7-252">In this case, you would likely use an asynchronous rendering thread in order to maintain a continuous load on the GPU.</span></span> <span data-ttu-id="45ca7-253">請注意 HoloLens 裝置的重新整理頻率是 60 赫茲，其中一個畫面有大約 16 毫秒的持續時間。</span><span class="sxs-lookup"><span data-stu-id="45ca7-253">Note that the refresh rate of the HoloLens device is 60hz, where one frame has a duration of approximately 16 ms.</span></span> <span data-ttu-id="45ca7-254">沈浸式耳機裝置的範圍可從 60 赫茲到 90 hz;重新整理時在畫面上 90 hz，每個畫面格會有約 11 毫秒的持續時間。</span><span class="sxs-lookup"><span data-stu-id="45ca7-254">Immersive headset devices can range from 60hz to 90hz; when refreshing the display at 90 hz, each frame will have a duration of approximately 11 ms.</span></span>

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a><span data-ttu-id="45ca7-255">處理與 HolographicFrame DeviceLost 案例</span><span class="sxs-lookup"><span data-stu-id="45ca7-255">Handle DeviceLost scenarios in cooperation with the HolographicFrame</span></span>

<span data-ttu-id="45ca7-256">DirectX 11 應用程式通常會想要檢查的 DXGI 交換鏈結所傳回的 HRESULT**存在**函式，以找出有沒有**DeviceLost**時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="45ca7-256">DirectX 11 apps would typically want to check the HRESULT returned by the DXGI swap chain's **Present** function to find out if there was a **DeviceLost** error.</span></span> <span data-ttu-id="45ca7-257"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>類別會為您處理這。</span><span class="sxs-lookup"><span data-stu-id="45ca7-257">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class handles this for you.</span></span> <span data-ttu-id="45ca7-258">檢查<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a>它會傳回以找出您要發行並重新建立的 Direct3D 裝置和裝置為基礎的資源。</span><span class="sxs-lookup"><span data-stu-id="45ca7-258">Inspect the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> it returns to find out if you need to release and recreate the Direct3D device and device-based resources.</span></span>

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

<span data-ttu-id="45ca7-259">請注意，是否 Direct3D 裝置已遺失，而且您並未重新建立它，您必須告訴<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>若要開始使用新的裝置。</span><span class="sxs-lookup"><span data-stu-id="45ca7-259">Note that if the Direct3D device was lost, and you did recreate it, you have to tell the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> to start using the new device.</span></span> <span data-ttu-id="45ca7-260">交換鏈結將會重建此裝置。</span><span class="sxs-lookup"><span data-stu-id="45ca7-260">The swap chain will be recreated for this device.</span></span>

<span data-ttu-id="45ca7-261">從**DeviceResources::InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="45ca7-261">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

<span data-ttu-id="45ca7-262">一旦您的畫面格呈現時，您可以回到主要程式迴圈，並讓它繼續執行到下一個畫面格。</span><span class="sxs-lookup"><span data-stu-id="45ca7-262">Once your frame is presented, you can return back to the main program loop and allow it to continue to the next frame.</span></span>

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a><span data-ttu-id="45ca7-263">混合式圖形 Pc 及混合的實境應用程式</span><span class="sxs-lookup"><span data-stu-id="45ca7-263">Hybrid graphics PCs and mixed reality applications</span></span>

<span data-ttu-id="45ca7-264">Windows 10 Creators Update 的電腦可能設有**兩者**離散和整合式的 Gpu。</span><span class="sxs-lookup"><span data-stu-id="45ca7-264">Windows 10 Creators Update PCs may be configured with **both** discrete and integrated GPUs.</span></span> <span data-ttu-id="45ca7-265">使用這些類型的電腦，Windows 會選擇耳機連接的介面卡。</span><span class="sxs-lookup"><span data-stu-id="45ca7-265">With these types of computers, Windows will choose the adapter the headset is connected to.</span></span> <span data-ttu-id="45ca7-266">應用程式必須確定它會建立 DirectX 裝置會使用相同的介面卡。</span><span class="sxs-lookup"><span data-stu-id="45ca7-266">Applications must ensure the DirectX device it creates uses the same adapter.</span></span>

<span data-ttu-id="45ca7-267">最常見的 Direct3D 範例程式碼示範如何建立使用預設的硬體配接器，這在混合式系統上可能不是所使用的耳機與相同的 DirectX 裝置。</span><span class="sxs-lookup"><span data-stu-id="45ca7-267">Most general Direct3D sample code demonstrates creating a DirectX device using the default hardware adapter, which on a hybrid system may not be the same as the one used for the headset.</span></span>

<span data-ttu-id="45ca7-268">若要解決這可能會造成任何問題，請使用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a>從其中<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>。PrimaryAdapterId() 或<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>。AdapterId()。</span><span class="sxs-lookup"><span data-stu-id="45ca7-268">To work around any issues this may cause, use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> from either <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>.PrimaryAdapterId() or <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>.AdapterId().</span></span> <span data-ttu-id="45ca7-269">此 adapterId 可用來選取正確的 DXGIAdapter 使用 IDXGIFactory4.EnumAdapterByLuid。</span><span class="sxs-lookup"><span data-stu-id="45ca7-269">This adapterId can then be used to select the right DXGIAdapter using IDXGIFactory4.EnumAdapterByLuid.</span></span>

<span data-ttu-id="45ca7-270">從**DeviceResources::InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="45ca7-270">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

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

<span data-ttu-id="45ca7-271">程式碼**更新使用 IDXGIAdapter DeviceResources::CreateDeviceResources**</span><span class="sxs-lookup"><span data-stu-id="45ca7-271">Code to **update DeviceResources::CreateDeviceResources to use IDXGIAdapter**</span></span>

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

<span data-ttu-id="45ca7-272">**混合式圖形和媒體基礎**</span><span class="sxs-lookup"><span data-stu-id="45ca7-272">**Hybrid graphics and Media Foundation**</span></span>

<span data-ttu-id="45ca7-273">使用混合式系統上的媒體基礎，可能會造成的問題，將不會轉譯視訊或影片的紋理已損毀。</span><span class="sxs-lookup"><span data-stu-id="45ca7-273">Using Media Foundation on hybrid systems may cause issues where video will not render or video texture is corrupt.</span></span> <span data-ttu-id="45ca7-274">這可能是因為如先前所述的系統行為預設的媒體基礎。</span><span class="sxs-lookup"><span data-stu-id="45ca7-274">This can occur because Media Foundation is defaulting to a system behavior as mentioned above.</span></span> <span data-ttu-id="45ca7-275">在某些情況下，建立個別的 ID3D11Device 是必須支援多執行緒處理，並正確設定旗標的建立。</span><span class="sxs-lookup"><span data-stu-id="45ca7-275">In some scenarios, creating a separate ID3D11Device is required to support multi-threading and the correct creation flags are set.</span></span>

<span data-ttu-id="45ca7-276">當初始化 ID3D11Device，D3D11_CREATE_DEVICE_VIDEO_SUPPORT 旗標必須定義 D3D11_CREATE_DEVICE_FLAG 的一部分。</span><span class="sxs-lookup"><span data-stu-id="45ca7-276">When initializing the ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT flag must be defined as part of the D3D11_CREATE_DEVICE_FLAG.</span></span> <span data-ttu-id="45ca7-277">在裝置與內容建立之後，呼叫<a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a>啟用多執行緒處理。</span><span class="sxs-lookup"><span data-stu-id="45ca7-277">Once the device and context is created, call <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> to enable multithreading.</span></span> <span data-ttu-id="45ca7-278">若要建立關聯的裝置<a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>，使用<a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a>函式。</span><span class="sxs-lookup"><span data-stu-id="45ca7-278">To associate the device with the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, use the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> function.</span></span>

<span data-ttu-id="45ca7-279">程式碼**ID3D11Device 關聯 IMFDXGIDeviceManager**:</span><span class="sxs-lookup"><span data-stu-id="45ca7-279">Code to **associate a ID3D11Device with IMFDXGIDeviceManager**:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="45ca7-280">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45ca7-280">See also</span></span>
* [<span data-ttu-id="45ca7-281">DirectX 中的座標系統</span><span class="sxs-lookup"><span data-stu-id="45ca7-281">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="45ca7-282">使用 HoloLens 模擬器</span><span class="sxs-lookup"><span data-stu-id="45ca7-282">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
