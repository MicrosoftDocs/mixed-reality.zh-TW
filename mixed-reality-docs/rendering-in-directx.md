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
# <a name="rendering-in-directx"></a>在 DirectX 中轉譯

Windows Mixed Reality 以產生豐富的 DirectX，3D 圖形化使用者體驗。 轉譯抽象位於 DirectX 的正上方，並讓理解的位置和方向的全像攝影版的場景，系統所預測的一或多個觀察者之間的應用程式。 開發人員可以再找出其全像投影相對於每個網路攝影機，讓應用程式呈現這些全像投影在各種不同的空間座標系統中，當使用者移動。

## <a name="update-for-the-current-frame"></a>更新目前畫面格

若要更新全像投影的應用程式狀態，之後每個畫面應用程式將會：
* 取得<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>從顯示的管理系統。
* 使用目前的位置 [相機] 檢視時，會轉譯完成預測來更新場景。 請注意，可以有多個相機在全像攝影版的場景。

若要轉譯到全像攝影版的相機的檢視，一次每個畫面應用程式將會：
* 為每部相機，轉譯場景目前畫面格，使用系統從相機檢視和投影矩陣。

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a>建立新的全像攝影版框架，並取得其預測

<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>應用程式能夠更新，並呈現目前的畫面格的資訊。 應用程式會開始每個新的畫面格，藉由呼叫**CreateNextFrame**方法。 呼叫這個方法時，做出的預測會使用最新的感應器資料可用，且封裝中**CurrentPrediction**物件。

新的框架物件必須用於每個呈現的畫面格，因為它只適用於針對即時的時間。 **CurrentPrediction**屬性包含觀景窗位置等資訊。 資訊會推斷為確切的時間擷取的框架時預期會向使用者顯示的時間。

下列程式碼摘錄自**AppMain::Update**:

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a>處理序相機更新

背景緩衝區可以變更框架框架。 您的應用程式需求，來驗證上一步為每部相機，緩衝處理和發行，並視需要重新建立資源檢視與深度緩衝區。 請注意，在預測中帶來一組的目前框架中正在使用的數位相機的授權清單。 通常，您可以使用這份清單的數位相機上逐一查看。

從**AppMain::Update**:

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

從**DeviceResources::EnsureCameraResources**:

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a>取得要用於轉譯做為基礎的座標系統

Windows Mixed Reality 可讓您建立各種不同的應用程式[座標系統](coordinate-systems-in-directx.md)，如有需要例如附加的參考框架和靜態參考框架中，追蹤在真實世界的位置。 您的應用程式接著可以使用這些座標系統，原因有關呈現全像投影每個畫面格的何處。 當要求座標，從 API，您將會永遠傳入<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>內您想要用來表示這些座標。

從**AppMain::Update**:

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

這些座標系統可用來轉譯場景中的內容時，產生立體聲的檢視矩陣。

從**CameraResources::UpdateViewProjectionBuffer**:

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a>處理序視線和輸入筆勢

[視線](gaze-in-directx.md)並[手](hands-and-motion-controllers-in-directx.md)輸入不是以時間為基礎，因此不需要在更新**StepTimer**函式。 不過這項輸入是應用程式需要查看每個畫面格的項目。

### <a name="process-time-based-updates"></a>處理時間為基礎的更新

任何即時轉譯應用程式將會需要某種方式來處理時間為基礎的更新;我們會提供方法來執行這項操作的 Windows 全像攝影版的應用程式範本，透過**StepTimer**實作。 提供在 DirectX 11 UWP 應用程式範本中，因此如果您已經看過該範本您應該在熟悉的基礎，這是類似於 StepTimer。 此 StepTimer 範例協助程式類別能夠提供固定的時間步驟更新，以及變數的時間步驟更新，而預設模式是可變的時間步驟。

在全像攝影版的呈現方式，我們特別選擇不將放入計時器函式太多。 這是因為您可以將它設定為固定的時間步驟就是，在此情況下可能會取得呼叫它一次以上每個畫面 – 或完全沒有，一些畫面格 – 而且我們全像攝影版的資料更新應該一次發生的每個畫面。


從**AppMain::Update**:

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a>位置和旋轉全像投影座標系統中

如果您在範本會執行與單一的座標系統中，在操作**SpatialStationaryReferenceFrame**，此程序不是不同於您是否則用於 3D 圖形。 在這裡，我們會旋轉 cube 和相對靜態的座標系統中設定的模型矩陣。

從**SpinningCubeRenderer::Update**:

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

**請注意進階案例相關：** 旋轉立方體是如何定位雷射單一參考範圍內的一個非常簡單的範例。 它也可[使用多個 SpatialCoordinateSystems](coordinate-systems-in-directx.md)在同一個轉譯框架中，在相同的時間。

### <a name="update-constant-buffer-data"></a>更新常數緩衝區的資料

模型內容的轉換會如往常般更新。 到目前為止，您將計算座標系統中，您會在轉譯的有效的轉換。

從**SpinningCubeRenderer::Update**:

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

檢視和投影轉換呢？ 為了獲得最佳結果，我們想要等到之前我們啟用這些我們幾乎準備好我們的繪製呼叫。

## <a name="render-the-current-frame"></a>呈現目前的框架

轉譯 Windows Mixed reality 沒有太大差異呈現 2D mono 在顯示上，但有一些要注意的差異：
* 全像攝影版的框架預測很重要。 接近預測可看到您的畫面格時，您全像投影起來愈好。
* Windows Mixed Reality 控制相機檢視。 您要轉譯為每一項，因為全像攝影版的框架將會呈現為您更新版本。
* 立體聲的轉譯，建議使用執行個體的繪製到轉譯目標陣列來完成。 全像攝影版的應用程式範本使用的執行個體繪製到轉譯目標陣列，它會使用到的轉譯目標檢視建議的方法**Texture2DArray**。
* 如果您想要呈現而不需使用立體聲的執行個體，您必須建立兩個非陣列 RenderTargetViews （一個眼睛） 中的每個參考其中的兩個配量所**Texture2DArray**從系統提供的應用程式。 這不是建議，因為它通常是顯著低於使用執行個體。

### <a name="get-an-updated-holographicframe-prediction"></a>取得已更新的 HolographicFrame 預測

更新框架預測增強影像穩定的效率，而且允許更精確的定位，因為較短的時間之間的預測和框架時向使用者顯示全像投影。 在理想情況下更新之前呈現在框架預測。

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a>轉譯為每部相機

上的相機會帶來在預測中，集合執行迴圈，並轉譯為每個在此集合中的相機。

**設定轉譯階段**

Windows Mixed Reality 使用立體視覺呈現來增強深度的幻影並呈現 stereoscopically，因此左邊和右邊顯示作用中。 使用立體視覺呈現位移之間沒有兩部顯示器，大腦可以協調為實際的深度。 此章節涵蓋 stereoscopic 轉譯使用執行個體中，使用程式碼的 Windows 全像攝影版的應用程式範本。

每部相機有它自己的轉譯目標 （背景緩衝區），以及檢視和投影矩陣，到全像攝影版的空間。 您的應用程式必須建立任何其他觀景窗基礎資源，例如深度緩衝區，以每個數位相機為基礎。 在 Windows 全像攝影版的應用程式範本中，我們提供 DX::CameraResources 中一起結合這些資源的協助程式類別。 著手設定呈現目標檢視：

從**AppMain::Render**:

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

**使用預測獲得相機中的檢視和投影矩陣**

每個畫面格會變更每個全像攝影版的相機的檢視和投影矩陣。 重新整理每個全像攝影版的相機的常數緩衝區中的資料。 這樣做，更新預測之後，而且會在進行之前任何繪製呼叫該相機。

從**AppMain::Render**:

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

在這裡，我們會示範如何從相機姿勢取得矩陣。 在此過程中我們也會取得目前的檢視區的相機。 請注意我們如何提供座標系統： 這是我們用來了解視線，相同的座標系統，而且同一個我們用來定位的旋轉立方體。


從**CameraResources::UpdateViewProjectionBuffer**:

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

檢視區應該設定為每個畫面格。 頂點著色器 （至少） 通常需要檢視/投影資料的存取權。


從**CameraResources::AttachViewProjectionBuffer**:

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

**轉譯為相機背景緩衝區，並認可深度緩衝區**:

它是個不錯的主意，以確認**TryGetViewTransform**成功 」，才能嘗試使用 檢視/預估的資料，因為如果找不到 座標系統 （例如，追蹤已中斷） 您的應用程式無法與它轉譯，框架。 範本只會呼叫**呈現**上的旋轉立方體如果**CameraResources**類別會指出成功的更新。

若要保留全像投影，開發人員或使用者將它們放在世界中，Windows Mixed Reality 包含的功能[映像穩定](hologram-stability.md)。 映像穩定協助隱藏轉譯管線，以確保最佳的使用者; 全像攝影版體驗中固有的延遲增強影像穩定進一步延伸，可指定婧鎏鶗懘或深度緩衝區可能會計算最佳化的映像穩定，即時提供。

為了獲得最佳結果，您的應用程式應該提供使用深度緩衝區<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API。 Windows Mixed Reality 然後可以使用幾何資訊從深度緩衝區來最佳化即時的映像穩定。 Windows 全像攝影版的應用程式範本會根據預設，協助最佳化全像穩定性認可應用程式的深度緩衝區。

從**AppMain::Render**:

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
>Windows 會處理您深度紋理，GPU 上的，因此您必須能夠深度緩衝區做為著色器資源。 無類型的格式應為您建立 ID3D11Texture2D，應該做為著色器資源檢視繫結。 以下是如何建立能認可的映像穩定的深度材質的範例。

程式碼**CommitDirect3D11DepthBuffer 深度緩衝區資源建立**:

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

**繪製全像攝影版的內容**

Windows 全像攝影版的應用程式範本使用的執行個體的幾何繪製 Texture2DArray 的大小為 2 的建議的技術，以呈現立體聲中的內容。 讓我們看看此範例和 Windows Mixed reality 的運作方式的執行個體部分。

從**SpinningCubeRenderer::Render**:

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

每個執行個體從常數緩衝區中存取不同的檢視/投影矩陣。 以下是常數緩衝區結構，也就是只要 2 個矩陣的陣列。

從**VertexShaderShared.hlsl**，以包含**VPRTVertexShader.hlsl**:

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

呈現目標陣列索引必須為每個像素。 在下列程式碼片段，output.viewId 會對應至**SV_RenderTargetArrayIndex**語意。 請注意，這需要支援選擇性的 Direct3D 11.3 功能，可呈現目標陣列索引語意從任何著色器階段進行設定。

從**VPRTVertexShader.hlsl**:

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

從**VertexShaderShared.hlsl**，以包含**VPRTVertexShader.hlsl**:

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

如果您想要使用您現有的執行個體使用此方法的繪圖至立體音響的繪圖技術呈現目標陣列，您只需要繪製兩次您通常需要的執行個體數目。 在 著色器，將分割**input.instId** 2 取得的原始執行個體識別碼，這可以編製索引 （舉例來說） 每個物件資料的緩衝區： `int actualIdx = input.instId / 2;`

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a>呈現 HoloLens 上的是立體聲內容的重要注意事項

Windows Mixed Reality 能夠從任何的著色器階段; 設定的轉譯目標陣列索引一般來說，這是只能在幾何著色器階段中，因為語意定義適用於 Direct3D 11 的方式工作。 在這裡，我們會示範如何設定端點和像素著色器階段組合作為轉譯管線的完整範例。 著色器程式碼是上面所述。

從**SpinningCubeRenderer::Render**:

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

### <a name="important-note-about-rendering-on-non-hololens-devices"></a>關於非 HoloLens 裝置上轉譯的重要注意事項

在 端點著色器中設定的轉譯目標陣列索引需要圖形驅動程式支援的選用的 Direct3D 11.3 功能，支援 HoloLens。 您的應用程式可以安全地實作該技術進行轉譯，並在 Microsoft HoloLens 上執行，將會符合所有需求。

可能的情況下，您想要使用 HoloLens 模擬器，這可以是您全像攝影版的應用程式-功能強大的開發工具，並支援連接至 Windows 10 電腦的 Windows Mixed Reality 沈浸式耳機裝置。 因此，所有的 Windows Mixed Reality-也會內建的 Windows 全像攝影版的應用程式範本和支援非 HoloLens 轉譯路徑。 在範本程式碼中，您會發現程式碼，讓您全像攝影版的應用程式在開發電腦中，於 GPU 上執行。 以下是如何**DeviceResources**類別檢查這項選擇性功能支援。

從**DeviceResources::CreateDeviceResources**:

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

若要支援轉譯，而不需要此選擇性功能，您的應用程式必須使用幾何著色器設定的轉譯目標陣列索引。 會加入此程式碼片段*之後* **VSSetConstantBuffers**，並*之前* **Pssetshade**先前所示的程式碼範例說明如何呈現 HoloLens 上的立體聲的區段。

從**SpinningCubeRenderer::Render**:

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

**HLSL 注意**:在此情況下，您也必須載入稍經修改的端點著色器給使用一律允許著色器語意，例如 TEXCOORD0 幾何著色器的轉譯目標陣列索引。 幾何著色器沒有執行任何工作;範本幾何著色器通過所有的資料，除了用來設定 SV_RenderTargetArrayIndex 語意的轉譯目標陣列索引。

應用程式範本程式碼**GeometryShader.hlsl**:

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

## <a name="present"></a>目前

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a>啟用全像攝影版的畫面格呈現交換鏈結

使用 Windows Mixed Reality，系統會控制交換鏈結。 系統接著會管理做簡報的畫面格數到每個全像攝影版的攝影機，以確保高品質使用者經驗。 它也提供的檢視區的更新，請在每個畫面格，為每部相機，以最佳化例如映像穩定或混合實境擷取系統的層面。 因此，使用 DirectX 的全像攝影版的應用程式並不會呼叫**存在**DXGI 上交換鏈結。 相反地，您使用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>類別來呈現畫面格的所有交換鏈結，一旦您完成繪製它。

從**DeviceResources::Present**:

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

根據預設，此 API 會等到完成後，才能傳回框架。 全像攝影版的應用程式應該等待前一個畫面格，才能開始新的框架的工作，因為這可減少延遲，並從全像攝影版的框架預測更好的結果是用來完成。 這不是永久的規則，以及如果您有畫面格所花費時間超過一個畫面重新整理，以呈現您可以停用這項等候傳遞的 HolographicFramePresentWaitBehavior 參數<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>。 在此情況下，您可能會維持在 GPU 上的連續載入中使用非同步轉譯執行緒。 請注意 HoloLens 裝置的重新整理頻率是 60 赫茲，其中一個畫面有大約 16 毫秒的持續時間。 沈浸式耳機裝置的範圍可從 60 赫茲到 90 hz;重新整理時在畫面上 90 hz，每個畫面格會有約 11 毫秒的持續時間。

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a>處理與 HolographicFrame DeviceLost 案例

DirectX 11 應用程式通常會想要檢查的 DXGI 交換鏈結所傳回的 HRESULT**存在**函式，以找出有沒有**DeviceLost**時發生錯誤。 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>類別會為您處理這。 檢查<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a>它會傳回以找出您要發行並重新建立的 Direct3D 裝置和裝置為基礎的資源。

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

請注意，是否 Direct3D 裝置已遺失，而且您並未重新建立它，您必須告訴<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>若要開始使用新的裝置。 交換鏈結將會重建此裝置。

從**DeviceResources::InitializeUsingHolographicSpace**:

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

一旦您的畫面格呈現時，您可以回到主要程式迴圈，並讓它繼續執行到下一個畫面格。

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a>混合式圖形 Pc 及混合的實境應用程式

Windows 10 Creators Update 的電腦可能設有**兩者**離散和整合式的 Gpu。 使用這些類型的電腦，Windows 會選擇耳機連接的介面卡。 應用程式必須確定它會建立 DirectX 裝置會使用相同的介面卡。

最常見的 Direct3D 範例程式碼示範如何建立使用預設的硬體配接器，這在混合式系統上可能不是所使用的耳機與相同的 DirectX 裝置。

若要解決這可能會造成任何問題，請使用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a>從其中<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>。PrimaryAdapterId() 或<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>。AdapterId()。 此 adapterId 可用來選取正確的 DXGIAdapter 使用 IDXGIFactory4.EnumAdapterByLuid。

從**DeviceResources::InitializeUsingHolographicSpace**:

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

程式碼**更新使用 IDXGIAdapter DeviceResources::CreateDeviceResources**

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

**混合式圖形和媒體基礎**

使用混合式系統上的媒體基礎，可能會造成的問題，將不會轉譯視訊或影片的紋理已損毀。 這可能是因為如先前所述的系統行為預設的媒體基礎。 在某些情況下，建立個別的 ID3D11Device 是必須支援多執行緒處理，並正確設定旗標的建立。

當初始化 ID3D11Device，D3D11_CREATE_DEVICE_VIDEO_SUPPORT 旗標必須定義 D3D11_CREATE_DEVICE_FLAG 的一部分。 在裝置與內容建立之後，呼叫<a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a>啟用多執行緒處理。 若要建立關聯的裝置<a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>，使用<a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a>函式。

程式碼**ID3D11Device 關聯 IMFDXGIDeviceManager**:

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

## <a name="see-also"></a>另請參閱
* [DirectX 中的座標系統](coordinate-systems-in-directx.md)
* [使用 HoloLens 模擬器](using-the-hololens-emulator.md)
