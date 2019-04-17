---
title: DirectX 中的空間對應
description: 說明如何在 DirectX 應用程式中實作空間的對應。 這包括通用 Windows 平台 SDK 隨附的空間的對應範例應用程式的詳細的說明。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows 混合實境、 空間的對應、 環境、 互動、 directx、 winrt、 api、 範例程式碼，UWP，SDK，逐步解說
ms.openlocfilehash: db3f1464158c04127e456cadd5fb633336909344
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2019
ms.locfileid: "59597139"
---
# <a name="spatial-mapping-in-directx"></a>DirectX 中的空間對應

本主題描述如何實作[空間對應](spatial-mapping.md)DirectX 應用程式中。 這包括通用 Windows 平台 SDK 隨附的空間的對應範例應用程式的詳細的說明。

本主題使用的程式碼[HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP 程式碼範例。

>[!NOTE]
>目前在這篇文章中的程式碼片段示範如何使用C++/CX 而不是 C + + 17 相容C++中所使用的 /WinRT [ C++全像攝影版的專案範本](creating-a-holographic-directx-project.md)。  概念是相等的C++/WinRT 專案，但您必須將轉譯程式碼。

## <a name="directx-development-overview"></a>DirectX 開發概觀

空間對應的原生應用程式開發使用的 Api 之下[Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)命名空間。 這些 Api 提供的空間的對應功能，直接對空間的對應所公開的 Api 類似的方式 完全控制[Unity](spatial-mapping-in-unity.md)。

### <a name="perception-apis"></a>Perception Api

空間對應開發所提供的主要類型如下所示：
* [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)提供應用程式指定區域中的空間接近 SpatialSurfaceInfo 物件形式的使用者介面的相關資訊。
* [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx)描述單一現有空間的介面，包括唯一識別碼、 磁碟區和上次變更時間的週框。 它會提供 SpatialSurfaceMesh 收到要求時以非同步的方式。
* [SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx)包含用於自訂要求從 SpatialSurfaceInfo SpatialSurfaceMesh 物件的參數。
* [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx)表示單一的空間表面的網格資料。 頂點位置、 頂點法線和三角形索引的資料被包含成員 SpatialSurfaceMeshBuffer 物件中。
* [SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx)包裝網狀結構資料單一類型。

在開發時使用這些 Api 的應用程式，您的基本程式流程看起來像這樣 （如以下所述的應用程式範例所示）：
- **設定您 SpatialSurfaceObserver**
  - 呼叫[RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx)，以確保使用者已獲得應用程式以使用裝置的空間的對應功能的權限。
  - 具現化 SpatialSurfaceObserver 物件。
  - 呼叫[SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx)來指定您想要空間介面的相關資訊的區域。 您可能只再次呼叫此函式來修改這些區域在未來。 使用指定每個區域[SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx)。
  - 報名[ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx)可用空間，您所指定的區域中的空間介面的相關新資訊時，會引發的事件。
- **處理序 ObservedSurfacesChanged 事件**
  - 在您的事件處理常式，呼叫[GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx)接收 SpatialSurfaceInfo 物件的對應。 使用此對應，您可以更新您記錄的空間表面[存在於使用者的環境](spatial-mapping.md#mesh-caching)。
  - 每個 SpatialSurfaceInfo 物件，您可能會查詢[TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx)來判斷介面上的空間範圍，以表示[空間座標系統](coordinate-systems.md)您選擇。
  - 如果您決定要求網格空間的介面，呼叫[TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx)。 您可能會提供指定所需的三角形，密度和傳回的網狀結構資料格式的選項。
- **接收和處理網格**
  - TryComputeLatestMeshAsync 將 aysnchronously 每次呼叫會傳回一個 SpatialSurfaceMesh 物件。
  - 您可以從這個物件存取包含的 SpatialSurfaceMeshBuffer 物件才能存取的三角形索引、 頂點位置 （如有要求） 和網格的頂點法線。 這項資料會在與直接相容的格式[Direct3D 11 Api](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx)用於呈現網格。
  - 從這裡您的應用程式可以選擇性地執行分析或[處理](spatial-mapping.md#mesh-processing)網狀結構資料，並將其用於[轉譯](spatial-mapping.md#rendering)物及物理學[raycasting 和衝突](spatial-mapping.md#raycasting-and-collision)。
  - 請注意一個重要的詳細資料是，您必須套用擴展至網狀結構頂點位置 （例如在端點著色器，用於呈現網格），將數值轉換在其中儲存在緩衝區中，為最佳化的整數單位測量。 您可以呼叫來擷取這個標尺[VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)。

### <a name="troubleshooting"></a>疑難排解
* 別忘了向網狀結構中端點著色器，使用所傳回的標尺的頂點位置[SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)

## <a name="spatial-mapping-code-sample-walkthrough"></a>空間對應的程式碼範例逐步解說

[全像攝影版的空間對應](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping)程式碼範例包含程式碼，可用來開始介面網格載入您的應用程式，包括基礎結構來管理及轉譯介面網狀結構。

現在，我們逐步解說如何將介面的對應功能新增至您的 DirectX 應用程式。 您可以新增下列程式碼您[Windows 全像攝影版的應用程式範本](creating-a-holographic-directx-project.md)專案，或您可以跟著瀏覽先前所述的程式碼範例。 此程式碼範例根據 Windows 全像攝影版的應用程式範本。

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>將您的應用程式設定為使用 spatialPerception 功能

您的應用程式必須能夠使用空間的對應功能。 這是環境的必要的因為空間的網格是環境的使用者，可能會被視為私用資料的表示法。 宣告您的應用程式的 package.appxmanifest 檔案中的這項功能。 以下為範例：

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

功能是來自**uap2**命名空間。 若要存取此命名空間資訊清單中，將它包含*xlmns*屬性中&lt;封裝 > 項目。 以下為範例：

```xml
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a>檢查有空間的對應功能的支援

Windows Mixed Reality 支援各種不同的裝置，包括裝置不支援空間對應。 如果您的應用程式可以使用空間的對應，或必須使用空間的對應，以提供的功能，它應該檢查以確定嘗試使用它之前，都支援空間對應。 比方說，如果您的混合的實境應用程式需要空間對應時，它應該先顯示一則訊息，如果使用者嘗試在沒有空間對應的裝置上執行它。 或者，您的應用程式可能能夠轉譯自己的虛擬環境來取代使用者的環境中，提供類似於可用空間的對應一樣，會發生什麼情況的體驗。 在任何情況下，此 API 可讓您的應用程式，要注意的是當它不會取得空間對應的資料和適當的方式回應。

若要檢查目前的裝置空間的對應支援，請先確定 UWP 合約位於層級等於或大於 4，然後呼叫 SpatialSurfaceObserver::IsSupported()。 以下是如何執行這項操作的內容中[全像攝影版的空間對應](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping)程式碼範例。 支援會檢查之前要求存取權。

可用以啟動 SDK 版本 15063 SpatialSurfaceObserver::IsSupported() API。 如有必要，設定目標平台版本 15063 專案，以使用此 API 之前。

```cpp
if (m_surfaceObserver == nullptr)
   {
       using namespace Windows::Foundation::Metadata;
       if (ApiInformation::IsApiContractPresent(L"Windows.Foundation.UniversalApiContract", 4))
       {
           if (!SpatialSurfaceObserver::IsSupported())
           {
               // The current system does not have spatial mapping capability.
               // Turn off spatial mapping.
               m_spatialPerceptionAccessRequested = true;
               m_surfaceAccessAllowed = false;
           }
       }

       if (!m_spatialPerceptionAccessRequested)
       {
           /// etc ...
```

請注意，當 UWP 合約層級 4，應用程式應該繼續如同裝置可以執行空間對應。

### <a name="request-access-to-spatial-mapping-data"></a>要求存取空間的對應資料

您的應用程式必須要求存取空間對應的資料，然後再嘗試建立任何介面的觀察者的權限。 詳細資訊，請在稍後提供此頁面，根據我們介面對應的程式碼範例，範例如下：

```cpp
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Create a surface observer.
    }
    else
    {
        // Handle spatial mapping unavailable.
    }
}
```

### <a name="create-a-surface-observer"></a>建立介面的觀察者

**Windows::Perception::Spatial::Surfaces**命名空間包含[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)類別，會遵守您在中指定的一或多個磁碟區[SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx)。 使用[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)即時存取介面的網格資料的執行個體。

從**AppMain.h**:

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

上一節所述，您必須先要求空間的對應資料的存取權，您的應用程式才能使用它。 此存取權授與自動 HoloLens。

```cpp
// The surface mapping API reads information about the user's environment. The user must
// grant permission to the app to use this capability of the Windows Mixed Reality device.
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // If status is allowed, we can create the surface observer.
        m_surfaceObserver = ref new SpatialSurfaceObserver();
```

接下來，您需要設定介面的觀察者来觀察特定的週框磁碟區。 在這裡，我們觀察到 20 x 20 x 5 公尺，座標系統的原點在置中的方塊。

```cpp
// The surface observer can now be configured as needed.

        // In this example, we specify one area to be observed using an axis-aligned
        // bounding box 20 meters in width and 5 meters in height and centered at the
        // origin.
        SpatialBoundingBox aabb =
        {
            { 0.f,  0.f, 0.f },
            {20.f, 20.f, 5.f },
        };

        SpatialBoundingVolume^ bounds = SpatialBoundingVolume::FromBox(coordinateSystem, aabb);
        m_surfaceObserver->SetBoundingVolume(bounds);
```

請注意，您可以設定多個週框的磁碟區。

*這是虛擬程式碼：*

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

您也可使用其他的週框圖案-例如檢視範圍，或不是軸的週框方塊對齊。

*這是虛擬程式碼：*

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

如果您的應用程式需要執行一些不同介面的對應資料尚未可用時，您可以撰寫程式碼來回應的大小寫所在[SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx)不是**允許**-例如，它將不被允許在電腦上的連接，因為這些裝置沒有可用的空間對應的硬體的沈浸式裝置。 對於這些裝置，您應該改為依賴使用者的環境和裝置組態資訊的空間階段。

### <a name="initialize-and-update-the-surface-mesh-collection"></a>初始化並更新介面網狀結構集合

如果介面的觀察者已成功建立，我們可以繼續進行初始化我們介面網狀結構的集合。 在這裡，我們會立即取得目前的觀察到的介面集使用提取模型 API:

```cpp
auto mapContainingSurfaceCollection = m_surfaceObserver->GetObservedSurfaces();
        for (auto& pair : mapContainingSurfaceCollection)
        {
            // Store the ID and metadata for each surface.
            auto const& id = pair->Key;
            auto const& surfaceInfo = pair->Value;
            m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
        }
```

另外還有可用來取得介面的網格資料推入模型。 您可以自由地設計您的應用程式使用提取模型，如果您選擇時，在此情況下您會進行資料輪詢不時-說車架-每一次，或在特定期間內，例如遊戲安裝程式期間。 如果是，上述程式碼會為您的需要。

在程式碼範例中，我們選擇示範這兩種模型用於教學用途。 在這裡，我們訂閱事件，以接收最新的 surface 網狀結構資料，每當系統能辨識的變更。

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

我們的程式碼範例也會設定為回應這些事件中。 讓我們逐步操作方式。

**注意：** 這可能不是最有效率的方式來處理網狀結構資料的應用程式。 此程式碼會寫入為了清楚起見，而不最佳化。

介面的網格中提供的資料存放區的唯讀對應[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx)物件，使用[Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx)做為索引鍵的值。

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

若要處理這項資料，我們不存在於集合中的索引鍵值的第一次。 本主題稍後會看到如何將資料儲存在我們的範例應用程式的詳細資訊。

```cpp
// Process surface adds and updates.
for (const auto& pair : surfaceCollection)
{
    auto id = pair->Key;
    auto surfaceInfo = pair->Value;

    if (m_meshCollection->HasSurface(id))
    {
        // Update existing surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
    else
    {
        // New surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
}
```

我們也必須移除介面網格介面網狀結構集合，但未再系統集合中。 若要這樣做，我們要做什麼我們剛剛展示的新增和更新網格; 相對於類似的項目我們在我們的應用程式集合，並檢查看看如果迴圈**Guid**我們會在系統集合中。 如果不是系統集合中，我們從我們移除它。

從我們 AppMain.cpp 中的事件處理常式：

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

網狀結構剪除 RealtimeSurfaceMeshRenderer.cpp 中的實作：

```cpp
void RealtimeSurfaceMeshRenderer::PruneMeshCollection(IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection)
{
    std::lock_guard<std::mutex> guard(m_meshCollectionLock);
    std::vector<Guid> idsToRemove;

    // Remove surfaces that moved out of the culling frustum or no longer exist.
    for (const auto& pair : m_meshCollection)
    {
        const auto& id = pair.first;
        if (!surfaceCollection->HasKey(id))
        {
            idsToRemove.push_back(id);
        }
    }

    for (const auto& id : idsToRemove)
    {
        m_meshCollection.erase(id);
    }
}
```

### <a name="acquire-and-use-surface-mesh-data-buffers"></a>取得和使用介面的網格資料緩衝區

取得介面的網狀結構資訊已與提取資料收集和處理該集合更新一樣容易。 現在，我們會詳細說明如何使用資料。

在程式碼範例中，我們選擇使用介面的網格轉譯。 這是真實世界介面背後 occluding 全像投影的常見案例。 您也可以轉譯網格，或呈現處理過的版本，其中，便要向使用者顯示的哪些地方開始提供應用程式或遊戲的功能之前，會掃描聊天室。

我們在上一節中所述的事件處理常式從接收介面網狀結構更新時，程式碼範例會啟動程序。 在此函式的程式碼的重要一行是呼叫更新介面*mesh*： 我們已將網狀結構資訊中，處理此時，我們即將使用取得的端點和索引的資料，依照我們。

From RealtimeSurfaceMeshRenderer.cpp:

```cpp
void RealtimeSurfaceMeshRenderer::AddOrUpdateSurface(Guid id, SpatialSurfaceInfo^ newSurface)
{
    auto options = ref new SpatialSurfaceMeshOptions();
    options->IncludeVertexNormals = true;

    auto createMeshTask = create_task(newSurface->TryComputeLatestMeshAsync(1000, options));
    createMeshTask.then([this, id](SpatialSurfaceMesh^ mesh)
    {
        if (mesh != nullptr)
        {
            std::lock_guard<std::mutex> guard(m_meshCollectionLock);
            '''m_meshCollection[id].UpdateSurface(mesh);'''
        }
    }, task_continuation_context::use_current());
}
```

我們的範例程式碼設計使資料類別**SurfaceMesh**、 處理和轉譯的控制代碼的網格資料。 這些網格是什麼**RealtimeSurfaceMeshRenderer**實際上會保留的對應。 每個的來源，SpatialSurfaceMesh 的參考，我們用它任何時候，我們需要存取網格的頂點或索引緩衝區，或取得網狀結構中的轉換。 現在，我們的旗標為需要更新網狀結構。

從 SurfaceMesh.cpp:

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

下一次，系統會要求網格繪製本身，它會檢查此旗標第一次。 如果需要更新時，將會在 GPU 上更新端點和索引緩衝區。

```cpp
void SurfaceMesh::CreateDeviceDependentResources(ID3D11Device* device)
{
    m_indexCount = m_surfaceMesh->TriangleIndices->ElementCount;
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }
```

首先，我們會取得未經處理資料緩衝區：

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

接著，我們會建立 Direct3D 裝置緩衝區 HoloLens 所提供的網狀結構資料：

```cpp
CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, positions, m_vertexPositions.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, normals,   m_vertexNormals.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_INDEX_BUFFER,  indices,   m_triangleIndices.GetAddressOf());

    // Create a constant buffer to control mesh position.
    CD3D11_BUFFER_DESC constantBufferDesc(sizeof(SurfaceTransforms), D3D11_BIND_CONSTANT_BUFFER);
    DX::ThrowIfFailed(
        device->CreateBuffer(
            &constantBufferDesc,
            nullptr,
            &m_modelTransformBuffer
            )
        );

    m_loadingComplete = true;
}
```

**注意：** CreateDirectXBuffer helper 函式，使用在先前的程式碼片段，請參閱介面對應的程式碼範例：SurfaceMesh.cpp GetDataFromIBuffer.h。 現在裝置資源建立完成，且網格會被視為可載入並準備好進行更新，並呈現。

### <a name="update-and-render-surface-meshes"></a>更新並呈現表面的網格

我們 SurfaceMesh 類別具有特製化的 update 函式。 每個[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx)有它自己的轉換，和我們的範例會使用目前座標系統為我們**SpatialStationaryReferenceFrame**取得轉換。 然後，它會更新模型常數緩衝區在 GPU 上。

```cpp
void SurfaceMesh::UpdateTransform(
    ID3D11DeviceContext* context,
    SpatialCoordinateSystem^ baseCoordinateSystem
    )
{
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }

    XMMATRIX transform = XMMatrixIdentity();

    auto tryTransform = m_surfaceMesh->CoordinateSystem->TryGetTransformTo(baseCoordinateSystem);
    if (tryTransform != nullptr)
    {
        transform = XMLoadFloat4x4(&tryTransform->Value);
    }

    XMMATRIX scaleTransform = XMMatrixScalingFromVector(XMLoadFloat3(&m_surfaceMesh->VertexPositionScale));

    XMStoreFloat4x4(
        &m_constantBufferData.vertexWorldTransform,
        XMMatrixTranspose(
            scaleTransform * transform
            )
        );

    // Normals don't need to be translated.
    XMMATRIX normalTransform = transform;
    normalTransform.r[3] = XMVectorSet(0.f, 0.f, 0.f, XMVectorGetW(normalTransform.r[3]));
    XMStoreFloat4x4(
        &m_constantBufferData.normalWorldTransform,
        XMMatrixTranspose(
            normalTransform
        )
        );

    if (!m_loadingComplete)
    {
        return;
    }

    context->UpdateSubresource(
        m_modelTransformBuffer.Get(),
        0,
        NULL,
        &m_constantBufferData,
        0,
        0
        );
}
```

呈現表面的網格時，我們會進行一些準備工作，然後才轉譯集合。 我們設定著色器管線。 目前的轉譯設定，以及我們設定的輸入組譯工具階段。 請注意，全像攝影版的相機協助程式類別**CameraResources.cpp**已經有設定檢視/投影常數緩衝區到目前為止。

從**RealtimeSurfaceMeshRenderer::Render**:

```cpp
auto context = m_deviceResources->GetD3DDeviceContext();

context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach our vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
    );

// The constant buffer is per-mesh, and will be set as such.

if (depthOnly)
{
    // Explicitly detach the later shader stages.
    context->GSSetShader(nullptr, nullptr, 0);
    context->PSSetShader(nullptr, nullptr, 0);
}
else
{
    if (!m_usingVprtShaders)
    {
        // Attach the passthrough geometry shader.
        context->GSSetShader(
            m_geometryShader.Get(),
            nullptr,
            0
            );
    }

    // Attach our pixel shader.
    context->PSSetShader(
        m_pixelShader.Get(),
        nullptr,
        0
        );
}
```

完成之後，我們會循環播放，在我們的網格上，並告知每個繪製本身。 **注意：** 此範例程式碼不會最佳化來使用任何類型的範圍剔除，但您應該將這項功能納入您的應用程式。

```cpp
std::lock_guard<std::mutex> guard(m_meshCollectionLock);

auto device = m_deviceResources->GetD3DDevice();

// Draw the meshes.
for (auto& pair : m_meshCollection)
{
    auto& id = pair.first;
    auto& surfaceMesh = pair.second;

    surfaceMesh.Draw(device, context, m_usingVprtShaders, isStereo);
}
```

個別的網格會負責設定端點和索引緩衝區、 stride 和模型轉換常數緩衝區。 如同 Windows 全像攝影版的應用程式範本中的旋轉立方體，我們會轉譯為 stereoscopic 緩衝區使用執行個體。

從**SurfaceMesh::Draw**:

```cpp
// The vertices are provided in {vertex, normal} format

const auto& vertexStride = m_surfaceMesh->VertexPositions->Stride;
const auto& normalStride = m_surfaceMesh->VertexNormals->Stride;

UINT strides [] = { vertexStride, normalStride };
UINT offsets [] = { 0, 0 };
ID3D11Buffer* buffers [] = { m_vertexPositions.Get(), m_vertexNormals.Get() };

context->IASetVertexBuffers(
    0,
    ARRAYSIZE(buffers),
    buffers,
    strides,
    offsets
    );

const auto& indexFormat = static_cast<DXGI_FORMAT>(m_surfaceMesh->TriangleIndices->Format);

context->IASetIndexBuffer(
    m_triangleIndices.Get(),
    indexFormat,
    0
    );

context->VSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

if (!usingVprtShaders)
{
    context->GSSetConstantBuffers(
        0,
        1,
        m_modelTransformBuffer.GetAddressOf()
        );
}

context->PSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

context->DrawIndexedInstanced(
    m_indexCount,       // Index count per instance.
    isStereo ? 2 : 1,   // Instance count.
    0,                  // Start index location.
    0,                  // Base vertex location.
    0                   // Start instance location.
    );
```

### <a name="rendering-choices-with-surface-mapping"></a>具有介面對應的轉譯選項

介面對應的程式碼範例提供介面的網狀結構的資料，僅會受阻擋的轉譯和螢幕上呈現表面的網狀結構資料的程式碼。 您選擇的路徑或兩者都仰賴您的應用程式。 我們將詳細說明這兩個組態，在這份文件中。

**全像攝影版的效果的轉譯會受阻擋緩衝區**

一開始先清除目前的虛擬觀景窗的呈現目標檢視。

從 AppMain.cpp:

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

這是 「 預先轉譯 」 階段。 此處，我們會要求網格轉譯器，來呈現只深度建立阻擋緩衝區。 在此組態中，我們不附加的轉譯目標檢視，和網格轉譯器會將像素著色器階段設定為**nullptr**以便 GPU 不麻煩繪製像素。 幾何會進行智慧型光柵化深度緩衝區中，與圖形管線會那里停止。

```cpp
// Pre-pass rendering: Create occlusion buffer from Surface Mapping data.
context->ClearDepthStencilView(pCameraResources->GetSurfaceDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to null, and set the depth target occlusion buffer.
// We will use this same buffer as a shader resource when drawing holograms.
context->OMSetRenderTargets(0, nullptr, pCameraResources->GetSurfaceOcclusionDepthStencilView());

// The first pass is a depth-only pass that generates an occlusion buffer we can use to know which
// hologram pixels are hidden behind surfaces in the environment.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), true);
```

我們可以與額外的深度測試的介面對應的阻擋物緩衝區對繪製全像投影。 在此程式碼範例中，我們在 cube 上的像素不同的色彩如果轉譯其位於介面。

從 AppMain.cpp:

```cpp
// Hologram rendering pass: Draw holographic content.
context->ClearDepthStencilView(pCameraResources->GetHologramDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target, and set the depth target drawing buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetHologramDepthStencilView());

// Render the scene objects.
// In this example, we draw a special effect that uses the occlusion buffer we generated in the
// Pre-Pass step to render holograms using X-Ray Vision when they are behind physical objects.
m_xrayCubeRenderer->Render(
    pCameraResources->IsRenderingStereoscopic(),
    pCameraResources->GetSurfaceOcclusionShaderResourceView(),
    pCameraResources->GetHologramOcclusionShaderResourceView(),
    pCameraResources->GetDepthTextureSamplerState()
    );
```

根據從 SpecialEffectPixelShader.hlsl 的程式碼：

```cpp
// Draw boundaries
min16int surfaceSum = GatherDepthLess(envDepthTex, uniSamp, input.pos.xy, pixelDepth, input.idx.x);

if (surfaceSum <= -maxSum)
{
    // The pixel and its neighbors are behind the surface.
    // Return the occluded 'X-ray' color.
    return min16float4(0.67f, 0.f, 0.f, 1.0f);
}
else if (surfaceSum < maxSum)
{
    // The pixel and its neighbors are a mix of in front of and behind the surface.
    // Return the silhouette edge color.
    return min16float4(1.f, 1.f, 1.f, 1.0f);
}
else
{
    // The pixel and its neighbors are all in front of the surface.
    // Return the color of the hologram.
    return min16float4(input.color, 1.0f);
}
```

**注意：** 如我們**GatherDepthLess**常式，請參閱介面對應的程式碼範例：SpecialEffectPixelShader.hlsl。

**呈現表面的網狀結構資料的顯示**

我們也可以繪製表面的網格是立體聲顯示緩衝區。 我們選擇要繪製的光線，與完整的臉部，但您可以隨意繪製框線、 處理網格轉譯之前，套用材質貼圖，等等。

在這裡，我們的程式碼範例會告知網格轉譯器繪製集合。 這次我們不指定僅限深度的階段，因此它會附加像素著色器，並完成轉譯管線使用目前的虛擬觀景窗我們指定的目標。

```cpp
// SR mesh rendering pass: Draw SR mesh over the world.
context->ClearDepthStencilView(pCameraResources->GetSurfaceOcclusionDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to the current holographic camera's back buffer, and set the depth buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetSurfaceDepthStencilView());

// This drawing pass renders the surface meshes to the stereoscopic display. The user will be
// able to see them while wearing the device.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), false);
```

## <a name="see-also"></a>另請參閱
* [建立全像攝影版的 DirectX 專案](creating-a-holographic-directx-project.md)
* [Windows.Perception.Spatial API](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
