---
title: 在 DirectX 中轉譯
description: 說明適用于 Windows Mixed Reality 的全像攝影轉譯。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，全息影像，轉譯，3D 圖形，HolographicFrame，轉譯迴圈，更新迴圈，逐步解說，範例程式碼，Direct3D
ms.openlocfilehash: 6b2e2dca9115d7093e94019d5ed91201f6ee3424
ms.sourcegitcommit: f4812e1312c4751a22a2de56771c475b22a4ba24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2019
ms.locfileid: "74940866"
---
# <a name="rendering-in-directx"></a>在 DirectX 中轉譯

Windows Mixed Reality 建基於 DirectX，為使用者產生豐富的3D 圖形化體驗。 轉譯抽象化的功能就是 DirectX，讓應用程式有一或多個全像攝影場景的觀察者的位置和方向，如同系統所預測。 然後，開發人員可以找到相對於每個相機的全息影像，讓應用程式在使用者四處移動時，在各種空間座標系統中轉譯這些全息影像。

注意：本逐步解說說明 Direct3D 11 中的全像攝影轉譯。 Direct3D 12 Windows Mixed Reality 應用程式範本也隨附于 Mixed Reality 應用程式範本延伸模組。

## <a name="update-for-the-current-frame"></a>目前畫面格的更新

若要更新全息影像的應用程式狀態，每個畫面格一次，應用程式將會：
* 從顯示管理系統取得<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 。
* 以目前的預測來更新場景，其中的相機視圖會在轉譯完成時顯示。 請注意，全像攝影場景可以有一個以上的相機。

若要轉譯成全像攝影相機視圖，每個畫面格一次，應用程式將會：
* 針對每個相機，使用系統中的相機視圖和投影矩陣，呈現目前框架的場景。

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a>建立新的全像攝影框架並取得其預測

<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>包含應用程式所需的資訊，以便更新和呈現目前的框架。 應用程式會藉由呼叫**CreateNextFrame**方法，開始每個新的框架。 呼叫這個方法時，會使用最新可用的感應器資料進行預測，並封裝在**CurrentPrediction**物件中。

針對每個呈現的框架，必須使用新的框架物件，因為它只適用于即時時間。 **CurrentPrediction**屬性包含相機位置等資訊。 這項資訊會推入到使用者應該看到框架的確切時間點。

下列程式碼是從**AppMain：： Update**摘錄自：

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a>處理相機更新

背景緩衝區可以從框架變更為框架。 您的應用程式需要驗證每個相機的後端緩衝區，並視需要釋放和重新建立資源檢視和深度緩衝區。 請注意，預測中的一組姿勢是目前框架中所使用之相機的授權清單。 通常，您會使用這份清單來逐一查看相機集合。

從**AppMain：： Update**：

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

From **DeviceResources：： EnsureCameraResources**：

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a>取得要作為轉譯基礎的座標系統

Windows Mixed Reality 可讓您的應用程式視需要建立各種[座標系統](coordinate-systems-in-directx.md)，例如，附加的參考框架和固定的參考框架，以追蹤實體世界中的位置。 然後，您的應用程式就可以使用這些座標系統，以瞭解在何處呈現每個畫面格的全息影像。 當您從 API 要求座標時，一律會傳入您想要在其中表示這些座標的<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> 。

從**AppMain：： Update**：

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

然後，這些座標系統可在呈現場景中的內容時，用來產生身歷聲視圖矩陣。

From **CameraResources：： UpdateViewProjectionBuffer**：

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a>處理注視和手勢輸入

[注視](gaze-in-directx.md)和[手寫](hands-and-motion-controllers-in-directx.md)輸入不是以時間為基礎，因此不需要在**StepTimer**函數中更新。 不過，此輸入是應用程式需要查看每個畫面格的內容。

### <a name="process-time-based-updates"></a>處理以時間為基礎的更新

任何即時轉譯應用程式都需要某種方式來處理以時間為基礎的更新;我們提供一種方法，可透過**StepTimer**的執行方式在 Windows 全像應用程式範本中執行此動作。 這類似于 DirectX 11 UWP 應用程式範本中提供的 StepTimer，因此，如果您已經看過該範本，您應該會在熟悉的基礎上。 這個 StepTimer 範例 helper 類別可以提供固定的時間步驟更新，以及可變的時間步驟更新，而預設模式是可變的時間步驟。

在全像攝影轉譯的情況下，我們特別選擇不要將太多放入計時器函式中。 這是因為您可以將它設定為固定的時間步驟，在這種情況下，每個畫面上可能會多次呼叫一次（或根本不會針對某些框架），而我們的全像攝影資料更新應該會針對每個畫面格進行一次。


從**AppMain：： Update**：

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a>在座標系統中放置和旋轉全息影像

如果您是在單一座標系統中操作，當範本使用**SpatialStationaryReferenceFrame**時，此程式與您在3d 圖形中所使用的不同。 在這裡，我們會旋轉 cube，並將模型矩陣設定為相對於固定座標系統中的位置。

從**SpinningCubeRenderer：： Update**：

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

**有關 advanced 案例的注意事項：** 旋轉 cube 是一個非常簡單的範例，說明如何在單一參考框架內放置全息影像。 同時，也可以在相同的轉譯框架中同時[使用多個 SpatialCoordinateSystems](coordinate-systems-in-directx.md) 。

### <a name="update-constant-buffer-data"></a>更新常數緩衝區資料

內容的模型轉換會如往常般更新。 現在，您將會針對要在其中轉譯的座標系統，計算出有效的轉換。

從**SpinningCubeRenderer：： Update**：

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

那麼視圖和投射的轉換呢？ 為了獲得最佳結果，我們想要等到幾乎準備好進行繪製呼叫，然後才取得這些。

## <a name="render-the-current-frame"></a>呈現目前的框架

在 Windows Mixed Reality 上轉譯與在 2D mono 顯示器上轉譯的方式不同，但有一些需要注意的差異：
* 全像攝影的畫面預測很重要。 當您的畫面格呈現時，預測愈接近，您的全息影像外觀就愈好。
* Windows Mixed Reality 控制相機的視圖。 您必須轉譯成每一個，因為全像攝影畫面將會在稍後呈現。
* 建議使用「實例繪製」來完成身歷聲轉譯，以呈現目標陣列。 「全像攝影應用程式」範本會使用建議的具現化方法來繪製到轉譯目標陣列，這會使用轉譯目標視圖在**Texture2DArray**上。
* 如果您想要轉譯而不使用身歷聲實例，您必須建立兩個非陣列 RenderTargetViews （每一眼一個），每個都參考從系統提供給應用程式的**Texture2DArray**中兩個配量的其中一個。 這不是建議的作法，因為它的速度通常會比使用實例慢很多。

### <a name="get-an-updated-holographicframe-prediction"></a>取得更新的 HolographicFrame 預測

更新框架預測可增強影像穩定的效率，並可讓您更精確地放置全息的位置，因為預測之間的時間較短，且使用者可以看到畫面格。 理想的情況是在呈現之前更新您的框架預測。

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a>呈現到每個相機

一組相機上的迴圈會在預測中產生，並轉譯成此集合中的每個相機。

**設定轉譯階段**

Windows Mixed Reality 會使用 stereoscopic 轉譯來增強深度的幻影並轉譯 stereoscopically，因此左側和右側顯示都是作用中狀態。 使用 stereoscopic 轉譯時，兩個顯示器之間會有一個位移，大腦可以將其視為實際深度。 本節說明如何使用 Windows 全像應用程式範本中的程式碼，透過實例進行 stereoscopic 轉譯。

每個攝影機都有自己的呈現目標（背景緩衝區）和視圖和投影矩陣，以全像攝影空間。 您的應用程式將需要建立任何其他以相機為基礎的資源，例如每個攝影機的深度緩衝區。 在 Windows 全像攝影應用程式範本中，我們提供 helper 類別，將這些資源組合在 DX：： CameraResources 中。 從設定轉譯目標視圖開始：

從**AppMain：： Render**：

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

**使用預測來取得相機的視圖和投影矩陣**

每個全像攝影攝影機的視圖和投影矩陣都會隨著每個畫面格而變更。 重新整理每個全像攝影攝影機的常數緩衝區中的資料。 在您更新預測之後，以及對該攝影機進行任何繪製呼叫之前，請執行此動作。

從**AppMain：： Render**：

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

在這裡，我們會示範如何從相機姿勢取得矩陣。 在此過程中，我們也會取得相機的目前區。 請注意我們如何提供座標系統：這是我們用來瞭解注視的相同座標系統，而且與我們用來定位旋轉 cube 的相同。


From **CameraResources：： UpdateViewProjectionBuffer**：

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

應該設定每個框架的視口。 您的頂點著色器（至少）通常會需要存取視圖/投射資料。


From **CameraResources：： AttachViewProjectionBuffer**：

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

**呈現到相機背面緩衝區，並認可深度緩衝區**：

最好先檢查**TryGetViewTransform**是否成功，再嘗試使用視圖/投射資料，因為如果無法定位座標系統（例如，追蹤已中斷），您的應用程式無法使用該框架來呈現它。 如果**CameraResources**類別指出成功的更新，此範本只會呼叫旋轉 cube 上的**呈現**。

為了讓開發人員或使用者將其放在世界各地，Windows Mixed Reality 包含影像[穩定](hologram-stability.md)的功能。 影像穩定有助於隱藏轉譯管線中固有的延遲，以確保最適合使用者的全像攝影體驗;您可以指定焦點，以進一步增強影像的穩定，也可以提供深度緩衝區來即時計算優化的影像穩定。

為了獲得最佳結果，您的應用程式應該使用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API 提供深度緩衝區。 Windows Mixed Reality 接著可以使用深度緩衝區的幾何資訊，即時優化影像穩定。 Windows 全像應用程式範本預設會認可應用程式的深度緩衝區，以協助優化全息影像的穩定性。

從**AppMain：： Render**：

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
>Windows 將會在 GPU 上處理您的深度材質，因此必須使用您的深度緩衝區做為著色器資源。 您所建立的 ID3D11Texture2D 應該是無類型的格式，而且應該系結為著色器資源檢視。 以下範例說明如何建立可針對影像穩定認可的深度材質。

針對**CommitDirect3D11DepthBuffer 建立深度緩衝區資源的**程式碼：

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

**繪製全像攝影內容**

Windows 全像應用程式範本會使用將具現化幾何繪製為大小 2 Texture2DArray 的建議技術，將內容轉譯成身歷聲。 我們來看一下這個的實例部分，以及它如何在 Windows Mixed Reality 上運作。

從**SpinningCubeRenderer：： Render**：

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

每個實例會從常數緩衝區存取不同的視圖/投影矩陣。 以下是常數緩衝區結構，這只是2個矩陣的陣列。

From **VertexShaderShared. hlsl**，包含**VPRTVertexShader. hlsl**：

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

必須為每個圖元設定轉譯目標陣列索引。 在下列程式碼片段中，viewId 會對應至**SV_RenderTargetArrayIndex**語義。 請注意，這需要支援選擇性的 Direct3D 11.3 功能，以允許從任何著色器階段設定轉譯目標陣列索引的語義。

From **VPRTVertexShader. hlsl**：

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

From **VertexShaderShared. hlsl**，包含**VPRTVertexShader. hlsl**：

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

如果您想要使用現有的具現化繪圖技巧，並將此方法繪製到身歷聲轉譯目標陣列，您只需要繪製兩次您平常擁有的實例數目。 在著色器中，將**d**除以2，以取得原始實例識別碼，這可以編制索引為每個物件資料的緩衝區（例如）： `int actualIdx = input.instId / 2;`

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a>有關在 HoloLens 上呈現身歷聲內容的重要注意事項

Windows Mixed Reality 支援從任何著色器階段設定轉譯目標陣列索引的功能;一般來說，這是只能在幾何著色器階段中完成的工作，因為已針對 Direct3D 11 定義此語義的方式。 在這裡，我們將示範如何只設定頂點和圖元著色器階段，來設定轉譯管線的完整範例。 著色器程式碼如下所述。

從**SpinningCubeRenderer：： Render**：

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

### <a name="important-note-about-rendering-on-non-hololens-devices"></a>在非 HoloLens 裝置上呈現的重要注意事項

若要在頂點著色器中設定轉譯目標陣列索引，圖形驅動程式必須支援選擇性的 Direct3D 11.3 功能，亦即 HoloLens 支援。 您的應用程式或許能夠安全地執行轉譯的技巧，而且所有的需求都符合在 Microsoft HoloLens 上執行。

在此情況下，您可能會想要使用 HoloLens 模擬器，這可以是適用于全像攝影應用程式的強大開發工具，並支援連接到 Windows 10 電腦的 Windows Mixed Reality 沉浸式耳機裝置。 對非 HoloLens 轉譯路徑的支援-因此，對於所有的 Windows Mixed Reality 而言，也都內建于 Windows 全像應用程式範本中。 在範本程式碼中，您將找到可讓全像攝影應用程式在開發電腦上的 GPU 上執行的程式碼。 以下是**DeviceResources**類別如何檢查這項選擇性功能支援的方式。

From **DeviceResources：： CreateDeviceResources**：

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

若要支援不使用此選擇性功能的轉譯，您的應用程式必須使用幾何著色器來設定轉譯目標陣列索引。 此程式碼片段會在 **VSSetConstantBuffers**之後，以及上一節所示的程式碼範例中的**pssetshade** *之前*新增，說明如何在 HoloLens 上呈現身歷聲。

從**SpinningCubeRenderer：： Render**：

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

**HLSL 注意**：在此情況下，您也必須載入稍微修改的端點著色器，以使用一律允許的著色器語義（例如 TEXCOORD0），將轉譯目標陣列索引傳遞至幾何著色器。 幾何著色器不需要執行任何工作;範本幾何著色器會傳遞所有資料，但呈現目標陣列索引除外，這是用來設定 SV_RenderTargetArrayIndex 語義。

適用于 GeometryShader 的應用程式範本代碼 **。 hlsl**：

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

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a>讓全像攝影畫面呈現交換鏈

在 Windows Mixed Reality 中，系統會控制交換鏈。 系統接著會管理對每個全像攝影攝影機呈現畫面格，以確保高品質的使用者體驗。 它也會為每個攝影機提供一個視口更新每個畫面格，以將系統的各個層面優化，例如影像穩定或混合現實 Capture。 因此，使用 DirectX 的全像攝影應用程式不會在 DXGI 交換**鏈上呼叫**。 相反地，您可以使用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>類別，在繪圖完成繪製之後，呈現框架的所有 swapchains。

從**DeviceResources：:P 重發**：

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

根據預設，此 API 會等待框架完成後再傳回。 全像攝影應用程式應該等待前一個畫面完成，才能在新的畫面上開始工作，因為這樣可減少延遲，並讓全像框預測的結果變得更好。 這不是一項困難的規則，如果您的畫面格需要超過一螢幕重新整理來轉譯，可以將 HolographicFramePresentWaitBehavior 參數傳遞給<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>來停用此等候。 在此情況下，您可能會使用非同步轉譯執行緒，以維護 GPU 上的連續負載。 請注意，HoloLens 裝置的重新整理頻率是60hz，其中一個框架的持續時間大約為16毫秒。 沉浸式耳機裝置的範圍可以從60hz 到 90hz;在 90 hz 重新整理顯示時，每個畫面格的持續時間大約為11毫秒。

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a>處理與 HolographicFrame 合作的 DeviceLost 案例

DirectX 11 應用程式通常會想要檢查 DXGI 交換鏈的**現有**函式所傳回的 HRESULT，找出是否有**DeviceLost**錯誤。 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>類別會為您處理這種情況。 檢查它所傳回的<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> ，以瞭解您是否需要發行並重新建立 Direct3D 裝置和裝置型資源。

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

請注意，如果 Direct3D 裝置遺失，而您已重新建立它，您必須告訴<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>開始使用新的裝置。 將會重新建立此裝置的交換鏈。

From **DeviceResources：： InitializeUsingHolographicSpace**：

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

畫面出現之後，您可以回到主要程式迴圈，讓它繼續進入下一個畫面。

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a>混合式圖形電腦和混合現實應用程式

Windows 10 建立者更新電腦可以**同時**設定獨立和整合式 gpu。 使用這些類型的電腦時，Windows 會選擇耳機所連線的介面卡。 應用程式必須確定它所建立的 DirectX 裝置使用相同的介面卡。

最常見的 Direct3D 範例程式碼示範如何使用預設硬體介面卡建立 DirectX 裝置，在混合式系統上，它可能與用於耳機的不同。

若要解決這可能造成的任何問題，請使用任一<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>的<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> 。PrimaryAdapterId （）或<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>。AdapterId （）。 接著，您可以使用這個 adapterId 來選取使用 IDXGIFactory4 EnumAdapterByLuid 的正確 DXGIAdapter。

From **DeviceResources：： InitializeUsingHolographicSpace**：

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

用來**更新 DeviceResources：： CreateDeviceResources 以使用 IDXGIAdapter 的**程式碼

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

在混合式系統上使用媒體基礎可能會導致影片無法轉譯或視頻材質已損毀的問題。 發生這種情況的原因可能是媒體基礎預設為先前所述的系統行為。 在某些情況下，需要建立個別的 ID3D11Device 來支援多執行緒處理，並設定正確的建立旗標。

初始化 ID3D11Device 時，必須將 D3D11_CREATE_DEVICE_VIDEO_SUPPORT 旗標定義為 D3D11_CREATE_DEVICE_FLAG 的一部分。 一旦建立裝置和內容，請呼叫<a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a>來啟用多執行緒處理。 若要將裝置與<a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>建立關聯，請使用<a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager：： ResetDevice</a>函式。

將**ID3D11Device 與 IMFDXGIDeviceManager 產生關聯的**程式碼：

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

## <a name="see-also"></a>請參閱
* [DirectX 中的座標系統](coordinate-systems-in-directx.md)
* [使用 HoloLens 模擬器](using-the-hololens-emulator.md)
