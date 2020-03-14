---
title: 在 DirectX 中協調系統
description: 說明如何使用 Windows Mixed Reality 空間定位器、參考框架、空間錨點和座標系統、如何使用 SpatialStage、如何處理追蹤遺失、如何儲存和載入錨點，以及如何執行影像穩定。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Mixed Reality，空間定位器，空間參考框架，空間座標系統，空間階段，範例程式碼，影像穩定，空間錨點，空間錨點存放區，追蹤遺失，逐步解說
ms.openlocfilehash: a0bce897c1982715af24f0bf7c398cdee10f017f
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375615"
---
# <a name="coordinate-systems-in-directx"></a>在 DirectX 中協調系統

[座標系統](coordinate-systems.md)會形成 Windows Mixed Reality api 所提供空間理解的基礎。

今天的固定的 VR 或單一空間 VR 裝置會建立一個主要座標系統來代表其追蹤的空間。 Windows Mixed Reality 裝置（如 HoloLens）是設計用來在大型未定義的環境中使用，裝置會在使用者流覽時探索並瞭解其周圍的範圍。 這可讓裝置調整以持續改善使用者聊天室的知識，但會導致協調系統在應用程式的存留期內變更彼此的關聯性。 Windows Mixed Reality 支援各式各樣的裝置，範圍從固定的沉浸式耳機到全球附加的參考框架。

>[!NOTE]
>本文中的程式碼片段目前示範如何使用C++/cx， C++ [ C++ ](creating-a-holographic-directx-project.md)而不是 C + 17 相容的/WinRT，如全像攝影專案範本中所使用。  概念相當於C++/WinRT 專案，但您必須轉譯程式碼。

## <a name="spatial-coordinate-systems-in-windows"></a>Windows 中的空間座標系統

用來因應 Windows 中真實全局座標系統原因的核心類型是<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>。 這個類型的實例代表任意座標系統，並提供方法來取得轉換矩陣，您可以在兩個座標系統之間進行轉換，而不需要瞭解每個座標系統的詳細資料。

傳回空間資訊（以點、光線或使用者環境中的磁片區表示）的方法將會接受 SpatialCoordinateSystem 參數，讓您決定其最適用于傳回這些座標的座標系統。 這些座標的單位將一律為計量。

SpatialCoordinateSystem 與其他座標系統有動態關聯性，包括代表裝置位置的關係。 在任何時間點，裝置都可能找不到某些座標系統，而不能找到其他。 對於大部分的座標系統，您的應用程式必須準備好處理找不到它們的時間週期。

您的應用程式不應該直接建立 SpatialCoordinateSystems，而是應該透過認知 Api 使用。 在認知 Api 中有三個主要的座標系統來源，每個都對應到 [[座標系統](coordinate-systems.md)] 頁面上所述的概念：
* 若要取得固定的參考框架，請建立<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> ，或從目前的<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>取得一個。
* 若要取得空間錨點，請建立<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>。
* 若要取得附加的參考框架，請建立<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>。

這些物件所傳回的所有座標系統都是右手的，其中 + y 向上、+ x 向右和 + z 向後。 您可以記住正 Z 軸點的方向，其方式是將左或右手指指向正 x 方向，並將其 curling 為正 y 方向。 您拇指所指的方向，不論是指向您或指向您的反方向，即是該座標系統正 z 軸所指的方向。 下圖顯示這兩個座標系統。

![左手邊和右手座標系統](images/left-hand-right-hand.gif)<br>
*左手邊和右手座標系統*

若要根據 HoloLens 的位置啟動至 SpatialCoordinateSystem，請使用<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>類別來建立附加或固定的參考框架，如下列各節所述。

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a>使用空間階段將全息影像放在世界中

不透明的 Windows Mixed Reality 沉浸式耳機的座標系統是使用靜態<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference：： Current</a>屬性來存取。 此 API 會提供座標系統、有關播放程式是否為「上一部」或「行動裝置」的資訊、可用於流覽玩家是否行動的安全區域界限，以及是否有耳機方向的指示。 也有一個事件處理常式可更新空間階段。

首先，我們會取得空間階段並訂閱其更新： 

**空間階段初始化**的程式碼

```
SpatialStageManager::SpatialStageManager(
    const std::shared_ptr<DX::DeviceResources>& deviceResources, 
    const std::shared_ptr<SceneController>& sceneController)
    : m_deviceResources(deviceResources), m_sceneController(sceneController)
{
    // Get notified when the stage is updated.
    m_spatialStageChangedEventToken = SpatialStageFrameOfReference::CurrentChanged +=
        ref new EventHandler<Object^>(std::bind(&SpatialStageManager::OnCurrentChanged, this, _1));

    // Make sure to get the current spatial stage.
    OnCurrentChanged(nullptr);
}
```

在 OnCurrentChanged 方法中，您的應用程式應該檢查空間階段，並據此更新玩家體驗。 在此範例中，我們提供階段界限的視覺效果，以及使用者所指定的開始位置，以及階段的視圖範圍和移動屬性的範圍。 當無法提供階段時，我們也會回到自己的固定座標系統。


**空間階段更新**的程式碼

```
void SpatialStageManager::OnCurrentChanged(Object^ /*o*/)
{
    // The event notifies us that a new stage is available.
    // Get the current stage.
    m_currentStage = SpatialStageFrameOfReference::Current;

    // Clear previous content.
    m_sceneController->ClearSceneObjects();

    if (m_currentStage != nullptr)
    {
        // Obtain stage geometry.
        auto stageCoordinateSystem = m_currentStage->CoordinateSystem;
        auto boundsVertexArray = m_currentStage->TryGetMovementBounds(stageCoordinateSystem);

        // Visualize the area where the user can move around.
        std::vector<float3> boundsVertices;
        boundsVertices.resize(boundsVertexArray->Length);
        memcpy(boundsVertices.data(), boundsVertexArray->Data, boundsVertexArray->Length * sizeof(float3));
        std::vector<unsigned short> indices = TriangulatePoints(boundsVertices);
        m_stageBoundsShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(boundsVertices),
                    indices,
                    XMFLOAT3(DirectX::Colors::SeaGreen),
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageBoundsShape);

        // In this sample, we draw a visual indicator for some spatial stage properties.
        // If the view is forward-only, the indicator is a half circle pointing forward - otherwise, it
        // is a full circle.
        // If the user can walk around, the indicator is blue. If the user is seated, it is red.

        // The indicator is rendered at the origin - which is where the user declared the center of the
        // stage to be during setup - above the plane of the stage bounds object.
        float3 visibleAreaCenter = float3(0.f, 0.001f, 0.f);

        // Its shape depends on the look direction range.
        std::vector<float3> visibleAreaIndicatorVertices;
        if (m_currentStage->LookDirectionRange == SpatialLookDirectionRange::ForwardOnly)
        {
            // Half circle for forward-only look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 9, XM_PI);
        }
        else
        {
            // Full circle for omnidirectional look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 16, XM_2PI);
        }

        // Its color depends on the movement range.
        XMFLOAT3 visibleAreaColor;
        if (m_currentStage->MovementRange == SpatialMovementRange::NoMovement)
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::OrangeRed);
        }
        else
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::Aqua);
        }

        std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);

        // Visualize the look direction range.
        m_stageVisibleAreaIndicatorShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    visibleAreaColor,
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
    }
    else
    {
        // No spatial stage was found.
        // Fall back to a stationary coordinate system.
        auto locator = SpatialLocator::GetDefault();
        if (locator)
        {
            m_stationaryFrameOfReference = locator->CreateStationaryFrameOfReferenceAtCurrentLocation();

            // Render an indicator, so that we know we fell back to a mode without a stage.
            std::vector<float3> visibleAreaIndicatorVertices;
            float3 visibleAreaCenter = float3(0.f, -2.0f, 0.f);
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.125f, 16, XM_2PI);
            std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);
            m_stageVisibleAreaIndicatorShape =
                std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    XMFLOAT3(DirectX::Colors::LightSlateGray),
                    m_stationaryFrameOfReference->CoordinateSystem);
            m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
        }
    }
}
```

定義階段界限的一組頂點會以順時針順序提供。 當使用者使用時，Windows Mixed Reality shell 會在界限上繪製一個範圍;基於您的目的，您可能會想要 triangularize walkable 區域。 下列演算法可以用來 triangularize 階段。


**空間階段 triangularization**的程式碼

```
std::vector<unsigned short> SpatialStageManager::TriangulatePoints(std::vector<float3> const& vertices)
{
    size_t const& vertexCount = vertices.size();

    // Segments of the shape are removed as they are triangularized.
    std::vector<bool> vertexRemoved;
    vertexRemoved.resize(vertexCount, false);
    unsigned int vertexRemovedCount = 0;

    // Indices are used to define triangles.
    std::vector<unsigned short> indices;

    // Decompose into convex segments.
    unsigned short currentVertex = 0;
    while (vertexRemovedCount < (vertexCount - 2))
    {
        // Get next triangle:
        // Start with the current vertex.
        unsigned short index1 = currentVertex;

        // Get the next available vertex.
        unsigned short index2 = index1 + 1;

        // This cycles to the next available index.
        auto CycleIndex = [=](unsigned short indexToCycle, unsigned short stopIndex)
        {
            // Make sure the index does not exceed bounds.
            if (indexToCycle >= unsigned short(vertexCount))
            {
                indexToCycle -= unsigned short(vertexCount);
            }

            while (vertexRemoved[indexToCycle])
            {
                // If the vertex is removed, go to the next available one.
                ++indexToCycle;

                // Make sure the index does not exceed bounds.
                if (indexToCycle >= unsigned short(vertexCount))
                {
                    indexToCycle -= unsigned short(vertexCount);
                }

                // Prevent cycling all the way around.
                // Should not be needed, as we limit with the vertex count.
                if (indexToCycle == stopIndex)
                {
                    break;
                }
            }

            return indexToCycle;
        };
        index2 = CycleIndex(index2, index1);

        // Get the next available vertex after that.
        unsigned short index3 = index2 + 1;
        index3 = CycleIndex(index3, index1);

        // Vertices that may define a triangle inside the 2D shape.
        auto& v1 = vertices[index1];
        auto& v2 = vertices[index2];
        auto& v3 = vertices[index3];

        // If the projection of the first segment (in clockwise order) onto the second segment is 
        // positive, we know that the clockwise angle is less than 180 degrees, which tells us 
        // that the triangle formed by the two segments is contained within the bounding shape.
        auto v2ToV1 = v1 - v2;
        auto v2ToV3 = v3 - v2;
        float3 normalToV2ToV3 = { -v2ToV3.z, 0.f, v2ToV3.x };
        float projectionOntoNormal = dot(v2ToV1, normalToV2ToV3);
        if (projectionOntoNormal >= 0)
        {
            // Triangle is contained within the 2D shape.

            // Remove peak vertex from the list.
            vertexRemoved[index2] = true;
            ++vertexRemovedCount;

            // Create the triangle.
            indices.push_back(index1);
            indices.push_back(index2);
            indices.push_back(index3);

            // Continue on to the next outer triangle.
            currentVertex = index3;
        }
        else
        {
            // Triangle is a cavity in the 2D shape.
            // The next triangle starts at the inside corner.
            currentVertex = index2;
        }
    }

    indices.shrink_to_fit();
    return indices;
}
```

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a>使用固定的參考框架，將全息影像放在世界各地

[SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx)類別代表在使用者四處移動時，[相對於](coordinate-systems.md#stationary-frame-of-reference)使用者周圍範圍的參考框架。 此參考框架會優先保留裝置附近的穩定座標。 SpatialStationaryFrameOfReference 的其中一個主要用途，就是在呈現全息影像時，做為轉譯引擎內的基礎全局座標系統。

若要取得 SpatialStationaryFrameOfReference，請使用[SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx)類別並呼叫[CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx)。

從 Windows 全像應用程式範本：

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* 固定的參考框架是設計來提供相對於整體空間的最佳調整位置。 該參考框架內的個別位置可以稍微漂移。 當裝置學習更多有關環境的資訊時，這是正常現象。
* 當需要精確放置個別的全息影像時，應該使用 SpatialAnchor 將個別的全息影像錨定到真實世界中的某個位置，例如，使用者表示特別感興趣的點。 錨點位置不會漂移，但可以加以更正;錨點會在更正發生後，使用下一個畫面中的已更正位置開始。

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a>使用空間錨點將全息影像放在世界中

[空間錨點](coordinate-systems.md#spatial-anchors)是將全息影像放在真實世界中特定位置的絕佳方式，而系統可確保錨點會在一段時間內保持不變。 本主題說明如何建立和使用錨點，以及如何使用錨點資料。

您可以在所選擇的 SpatialCoordinateSystem 內，于任何位置和方向建立 SpatialAnchor。 裝置目前必須能夠找出該座標系統，而且系統不能達到其空間錨點的限制。

一旦定義之後，SpatialAnchor 的座標系統會持續調整，以保留其初始位置的精確位置和方向。 接著，您可以使用此 SpatialAnchor 來轉譯在該確切位置上，會在使用者的環境中出現固定的全息影像。

保留錨點的調整效果會隨著距離錨點增加而放大。 因此，您應該避免轉譯相對於錨點來源大約3個計量的內容。

[CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx)屬性會取得座標系統，讓您放置相對於錨點的內容，並在裝置調整錨點的精確位置時套用緩時套用。

使用[RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx)屬性和對應的[RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx)事件，自行管理這些調整。

### <a name="persist-and-share-spatial-anchors"></a>保存和共用空間錨點

您可以使用[SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)類別在本機保存 SpatialAnchor，然後在相同 HoloLens 裝置上的未來應用程式會話中取回。

藉由使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a>，您可以從本機 SpatialAnchor 建立長期雲端錨點，然後您的應用程式可以在多個 HoloLens、IOS 和 Android 裝置上尋找。  藉由共用多個裝置上的通用空間錨點，每個使用者都可以看到相對於相同實體位置中的錨點所呈現的內容。  這可提供即時共用體驗。

您也可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> 跨 HoloLens、iOS 和 Android 裝置取得非同步全像投影持久性。  藉由共用持久的雲端空間錨點，多個裝置就能觀察相同的已保存全像投影一段時間，即使那些裝置並未同時存在。

若要開始在 HoloLens 應用程式中建立共用體驗，請嘗試5分鐘的<a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure 空間錨點 HoloLens 快速入門</a>。

當您使用 Azure 空間錨點啟動並執行時，您可以接著在<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">HoloLens 上建立和尋找錨點</a>。  逐步解說也適用于<a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android 和 iOS</a> ，可讓您在所有裝置上共用相同的錨點。

### <a name="create-spatialanchors-for-holographic-content"></a>建立全像攝影內容的 SpatialAnchors

在此程式碼範例中，我們已修改 Windows 全像投影應用程式範本，以在偵測到**按下**的手勢時建立錨點。 接著，cube 會放在轉譯行程期間的錨點。

由於協助程式類別支援多個錨點，因此我們可以使用此程式碼範例，將多個 cube 放在同一個位置！

請注意，錨點的識別碼是您在應用程式中控制的東西。 在此範例中，我們已根據目前儲存在應用程式錨點集合中的錨點數目，建立一個依序排列的命名配置。

```
   // Check for new input state since the last frame.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   if (pointerState != nullptr)
   {
       // Try to get the pointer pose relative to the SpatialStationaryReferenceFrame.
       SpatialPointerPose^ pointerPose = pointerState->TryGetPointerPose(currentCoordinateSystem);
       if (pointerPose != nullptr)
       {
           // When a Pressed gesture is detected, the anchor will be created two meters in front of the user.

           // Get the gaze direction relative to the given coordinate system.
           const float3 headPosition = pointerPose->Head->Position;
           const float3 headDirection = pointerPose->Head->ForwardDirection;

           // The anchor position in the StationaryReferenceFrame.
           static const float distanceFromUser = 2.0f; // meters
           const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

           // Create the anchor at position.
           SpatialAnchor^ anchor = SpatialAnchor::TryCreateRelativeTo(currentCoordinateSystem, gazeAtTwoMeters);

           if ((anchor != nullptr) && (m_spatialAnchorHelper != nullptr))
           {
               // In this example, we store the anchor in an IMap.
               auto anchorMap = m_spatialAnchorHelper->GetAnchorMap();

               // Create an identifier for the anchor.
               String^ id = ref new String(L"HolographicSpatialAnchorStoreSample_Anchor") + anchorMap->Size;

               anchorMap->Insert(id->ToString(), anchor);
           }
       }
   }
```

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a>以非同步方式載入和快取，SpatialAnchorStore

讓我們看看如何撰寫可協助處理此持續性的 SampleSpatialAnchorHelper 類別，包括：
* 儲存記憶體內部錨點的集合，並以 Platform：： String 索引鍵編制索引。
* 從系統的 SpatialAnchorStore 載入錨點，這會與本機記憶體中的集合保持分開。
* 當應用程式選擇執行這項操作時，將本機記憶體中的錨點集合儲存至 SpatialAnchorStore。

以下說明如何將[SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx)物件儲存在[SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)中。

當類別啟動時，我們會以非同步方式要求 SpatialAnchorStore。 這牽涉到系統 i/o，因為 API 會載入錨點存放區，而此 API 會設為非同步，讓 i/o 不會封鎖。

```
   // Request the spatial anchor store, which is the WinRT object that will accept the imported anchor data.
   return create_task(SpatialAnchorManager::RequestStoreAsync())
       .then([](task<SpatialAnchorStore^> previousTask)
   {
       std::shared_ptr<SampleSpatialAnchorHelper> newHelper = nullptr;

       try
       {
           SpatialAnchorStore^ anchorStore = previousTask.get();

           // Once the SpatialAnchorStore has been loaded by the system, we can create our helper class.

           // Using "new" to access private constructor
           newHelper = std::shared_ptr<SampleSpatialAnchorHelper>(new SampleSpatialAnchorHelper(anchorStore));

           // Now we can load anchors from the store.
           newHelper->LoadFromAnchorStore();
       }
       catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while loading the anchor store: ") +
               exception->Message->Data() +
               L"\n"
               );
       }

       // Return the initialized class instance.
       return newHelper;
   });
```

系統會提供您可用來儲存錨點的 SpatialAnchorStore。 這是一個 IMapView，它會將字串的索引鍵值（也就是 SpatialAnchors 的資料值）產生關聯。 在我們的範例程式碼中，我們會將它儲存在可透過協助程式類別的公用函式存取的私用類別成員變數中。

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
>別忘了連結暫止/繼續事件，以儲存和載入錨定存放區。

```
   void HolographicSpatialAnchorStoreSampleMain::SaveAppState()
   {
       // For example, store information in the SpatialAnchorStore.
       if (m_spatialAnchorHelper != nullptr)
       {
           m_spatialAnchorHelper->TrySaveToAnchorStore();
       }
   }
```

```
   void HolographicSpatialAnchorStoreSampleMain::LoadAppState()
   {
       // For example, load information from the SpatialAnchorStore.
       LoadAnchorStore();
   }
```

### <a name="save-content-to-the-anchor-store"></a>將內容儲存至錨點存放區

當系統暫停您的應用程式時，您需要將空間錨點儲存至錨點存放區。 您也可以選擇在其他時間將錨點儲存至錨點存放區，因為您會發現應用程式的實作為必要。

當您準備好要嘗試將記憶體中的錨點儲存至 SpatialAnchorStore 時，您可以對集合執行迴圈，並嘗試儲存每一個。

```
   // TrySaveToAnchorStore: Stores all anchors from memory into the app's anchor store.
   //
   // For each anchor in memory, this function tries to store it in the app's AnchorStore. The operation will fail if
   // the anchor store already has an anchor by that name.
   //
   bool SampleSpatialAnchorHelper::TrySaveToAnchorStore()
   {
       // This function returns true if all the anchors in the in-memory collection are saved to the anchor
       // store. If zero anchors are in the in-memory collection, we will still return true because the
       // condition has been met.
       bool success = true;

       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           for each (auto& pair in m_anchorMap)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;

               // Try to save the anchors.
               if (!m_anchorStore->TrySave(id, anchor))
               {
                   // This may indicate the anchor ID is taken, or the anchor limit is reached for the app.
                   success=false;
               }
           }
       }

       return success;
   }
```

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a>當應用程式繼續時，從錨點存放區載入內容

當您的應用程式繼續進行，或在您應用程式 implementaiton 所需的任何其他時間時，您可以將先前儲存至 AnchorStore 的錨點，從錨點存放區的 IMapView 傳送到您自己的 SpatialAnchors 記憶體內部資料庫。

若要還原 SpatialAnchorStore 的錨點，請將您感興趣的每一個都還原至您自己的記憶體中集合。

您需要自己的記憶體內部資料庫 SpatialAnchors;將字串與您建立的 SpatialAnchors 建立關聯的一些方式。 在我們的範例程式碼中，我們選擇使用 Windows：： Foundation：： collection：： IMap 來儲存錨點，這可讓您輕鬆地針對 SpatialAnchorStore 使用相同的索引鍵和資料值。

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
>可能無法立即找出已還原的錨點。 例如，它可能是個別房間或不同建築物中的錨點。 從 AnchorStore 中抓取的錨點應該先測試 locatability，再加以使用。

<br>

>[!NOTE]
>在此範例程式碼中，我們會從 AnchorStore 中取出所有錨點。 這不是必要條件，您的應用程式也可以挑選特定的錨點子集，方法是使用對您的執行有意義的字串索引鍵值。

```
   // LoadFromAnchorStore: Loads all anchors from the app's anchor store into memory.
   //
   // The anchors are stored in memory using an IMap, which stores anchors using a string identifier. Any string can be used as
   // the identifier; it can have meaning to the app, such as "Game_Leve1_CouchAnchor," or it can be a GUID that is generated
   // by the app.
   //
   void SampleSpatialAnchorHelper::LoadFromAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Get all saved anchors.
           auto anchorMapView = m_anchorStore->GetAllSavedAnchors();
           for each (auto const& pair in anchorMapView)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;
               m_anchorMap->Insert(id, anchor);
           }
       }
   }
```

### <a name="clear-the-anchor-store-when-needed"></a>視需要清除錨定存放區

有時候，您需要清除應用程式狀態並寫入新的資料。 以下是使用[SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)執行此動作的方式。

使用我們的 helper 類別，幾乎不需要包裝 Clear 函式。 我們選擇在範例執行中這麼做，因為我們的協助程式類別是擁有 SpatialAnchorStore 實例的責任。

```
   // ClearAnchorStore: Clears the AnchorStore for the app.
   //
   // This function clears the AnchorStore. It has no effect on the anchors stored in memory.
   //
   void SampleSpatialAnchorHelper::ClearAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Clear all anchors from the store.
           m_anchorStore->Clear();
       }
   }
```

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a>範例：將錨點座標系統與固定的參考框架座標系統相關聯

假設您有一個錨點，而您想要將錨點座標系統中的某個專案與您在大部分其他內容中使用的 SpatialStationaryReferenceFrame 產生關聯。 您可以使用[TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx)從錨點的座標系統取得轉換，使其成為固定的參考框架：

```
   // In this code snippet, someAnchor is a SpatialAnchor^ that has been initialized and is valid in the current environment.
   float4x4 anchorSpaceToCurrentCoordinateSystem;
   SpatialCoordinateSystem^ anchorSpace = someAnchor->CoordinateSystem;
   const auto tryTransform = anchorSpace->TryGetTransformTo(currentCoordinateSystem);
   if (tryTransform != nullptr)
   {
       anchorSpaceToCurrentCoordinateSystem = tryTransform->Value;
   }
```

此程式對您有兩種説明：
1. 它會告訴您，這兩個參考框架是否可以彼此瞭解，以及
2. 若是如此，它會提供您直接從一個座標系統轉換至另一個座標系統的轉換。

有了這項資訊，您就能瞭解兩個參考框架之間物件之間的空間關聯性。

針對轉譯，您通常可以根據物件的原始參考框架或錨點來分組，以取得更好的結果。 針對每個群組執行個別的繪圖階段。 針對具有使用相同座標系統一開始所建立之模型轉換的物件，視圖矩陣會更正確。

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a>使用裝置附加的參考框架建立全息影像

有時候您會想要轉譯[保留連接](coordinate-systems.md#attached-frame-of-reference)至裝置位置的全息影像，例如，具有偵錯工具資訊的面板，或當裝置只能判斷其方向，而不是其在空間中的位置時的參考訊息。 為了達成此目的，我們使用了附加的參考框架。

SpatialLocatorAttachedFrameOfReference 類別會定義相對於裝置而非真實世界的座標系統。 此框架的固定標題相對於使用者的周圍，其指向建立參考框架時所面臨的方向。 從 then 開始，此參考框架中的所有方向都會相對於該固定標題，即使使用者旋轉裝置也是如此。

若是 HoloLens，此框架座標系統的原點位於使用者的頭部旋轉中心，因此其位置不受前端旋轉的影響。 您的應用程式可以指定相對於此點的位移，將全息影像放在使用者之前。

若要取得 SpatialLocatorAttachedFrameOfReference，請使用 SpatialLocator 類別並呼叫 CreateAttachedFrameOfReferenceAtCurrentHeading。

請注意，這適用于整個範圍的 Windows Mixed Reality 裝置。

### <a name="use-a-reference-frame-attached-to-the-device"></a>使用連接至裝置的參考框架

這些章節會討論我們在 Windows 全像應用程式範本中變更的內容，以使用此 API 啟用裝置附加的參考框架。 請注意，此「附加」的全息影像會與固定或錨定的全像投影一起使用，也可能在裝置暫時無法在世界中找到其位置時使用。

首先，我們變更了範本來儲存 SpatialLocatorAttachedFrameOfReference，而不是 SpatialStationaryFrameOfReference：

從**HolographicTagAlongSampleMain**：

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

從**HolographicTagAlongSampleMain**：

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

在更新期間，我們現在會從使用框架預測取得的時間戳記取得座標系統。

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a>取得空間指標姿勢，並遵循使用者的注視

我們希望我們的範例全息影像會遵循使用者的[注視](gaze-and-commit.md)，類似于「全像攝影」 shell 如何追蹤使用者的注視。 為此，我們需要從相同的時間戳記取得 SpatialPointerPose。

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

此 SpatialPointerPose 包含根據[使用者目前的標題](gaze-in-directx.md)來放置全息影像所需的資訊。

基於使用者的緩和原因，我們會使用線性插補（"lerp"）來平滑位置變更，使其在一段時間內發生。 對使用者而言，這比鎖定全息的全像目光更熟悉。 Lerping 標記式的全息影像位置也可讓我們藉由抑制移動來使全息影像變得穩定;如果我們未執行此抑制，使用者會看到全像投影抖動，因為通常會被視為使用者的 imperceptible 移動。

從**StationaryQuadRenderer：:P ositionhologram**：

```
   const float& dtime = static_cast<float>(timer.GetElapsedSeconds());

   if (pointerPose != nullptr)
   {
       // Get the gaze direction relative to the given coordinate system.
       const float3 headPosition  = pointerPose->Head->Position;
       const float3 headDirection = pointerPose->Head->ForwardDirection;

       // The tag-along hologram follows a point 2.0m in front of the user's gaze direction.
       static const float distanceFromUser = 2.0f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

       // Lerp the position, to keep the hologram comfortably stable.
       auto lerpedPosition = lerp(m_position, gazeAtTwoMeters, dtime * c_lerpRate);

       // This will be used as the translation component of the hologram's
       // model transform.
       SetPosition(lerpedPosition);
   }
```

>[!NOTE]
>在 [偵錯工具] 面板的案例中，您可以選擇將全息影像重新放置到較小的一邊，讓它不會妨礙您的觀點。 以下是您可能會執行這項操作的範例。

針對**StationaryQuadRenderer：:P ositionhologram**：

```
       // If you're making a debug view, you might not want the tag-along to be directly in the
       // center of your field of view. Use this code to position the hologram to the right of
       // the user's gaze direction.
       /*
       const float3 offset = float3(0.13f, 0.0f, 0.f);
       static const float distanceFromUser = 2.2f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * (headDirection + offset));
       */
```

### <a name="rotate-the-hologram-to-face-the-camera"></a>旋轉全息影像以臉部相機

只是放置全息影像，在此案例中是一個四個，我們也必須將物件旋轉以面對使用者。 請注意，這項旋轉會在世界空間中發生，因為這種類型的 billboarding 允許全息影像保留在使用者環境中。 視圖空間 billboarding 並不熟悉，因為全像投影會鎖定顯示方向;在這種情況下，您也必須在左右視圖矩陣之間插補，才能取得不會干擾身歷聲轉譯的視圖空間佈告欄轉換。 在這裡，我們會旋轉 X 和 Z 軸來面對使用者。

從**StationaryQuadRenderer：： Update**：

```
   // Seconds elapsed since previous frame.
   const float& dTime = static_cast<float>(timer.GetElapsedSeconds());

   // Create a direction normal from the hologram's position to the origin of person space.
   // This is the z-axis rotation.
   XMVECTOR facingNormal = XMVector3Normalize(-XMLoadFloat3(&m_position));

   // Rotate the x-axis around the y-axis.
   // This is a 90-degree angle from the normal, in the xz-plane.
   // This is the x-axis rotation.
   XMVECTOR xAxisRotation = XMVector3Normalize(XMVectorSet(XMVectorGetZ(facingNormal), 0.f, -XMVectorGetX(facingNormal), 0.f));

   // Create a third normal to satisfy the conditions of a rotation matrix.
   // The cross product  of the other two normals is at a 90-degree angle to
   // both normals. (Normalize the cross product to avoid floating-point math
   // errors.)
   // Note how the cross product will never be a zero-matrix because the two normals
   // are always at a 90-degree angle from one another.
   XMVECTOR yAxisRotation = XMVector3Normalize(XMVector3Cross(facingNormal, xAxisRotation));

   // Construct the 4x4 rotation matrix.

   // Rotate the quad to face the user.
   XMMATRIX rotationMatrix = XMMATRIX(
       xAxisRotation,
       yAxisRotation,
       facingNormal,
       XMVectorSet(0.f, 0.f, 0.f, 1.f)
       );

   // Position the quad.
   const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

   // The view and projection matrices are provided by the system; they are associated
   // with holographic cameras, and updated on a per-camera basis.
   // Here, we provide the model transform for the sample hologram. The model transform
   // matrix is transposed to prepare it for the shader.
   XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(rotationMatrix * modelTranslation));
```

### <a name="render-the-attached-hologram"></a>呈現附加的全息影像

在此範例中，我們也選擇在 SpatialLocatorAttachedReferenceFrame 的座標系統中轉譯全息影像，這是我們放置全息的位置。 （如果我們決定使用另一個座標系統轉譯，則必須從裝置附加的參考框架座標系統取得轉換到該座標系統）。

從**HolographicTagAlongSampleMain：： Render**：

```
   // The view and projection matrices for each holographic camera will change
   // every frame. This function refreshes the data in the constant buffer for
   // the holographic camera indicated by cameraPose.
   pCameraResources->UpdateViewProjectionBuffer(
       m_deviceResources,
       cameraPose,
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp)
       );
```

這樣就完成了！ 全像投影現在會在使用者的注視方向前面「調整」為2計量的位置。

>[!NOTE]
>這個範例也會載入其他內容，請參閱 StationaryQuadRenderer。

## <a name="handling-tracking-loss"></a>處理追蹤遺失

當裝置無法在世界中找到自己時，應用程式就會遇到「追蹤遺失」的情況。 Windows Mixed Reality 應用程式應該能夠處理位置追蹤系統的這類中斷。 藉由在預設 SpatialLocator 上使用 LocatabilityChanged 事件，可以觀察到這些中斷，並建立回應。

From **AppMain：： SetHolographicSpace：**

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

當您的應用程式收到 LocatabilityChanged 事件時，它可以視需要變更行為。 例如，在 PositionalTrackingInhibited 狀態中，您的應用程式可以暫停正常作業，並轉譯顯示警告訊息的[標記沿著全](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference)像投影。

Windows 全像攝影應用程式範本隨附已為您建立的 LocatabilityChanged 處理常式。 根據預設，當位置追蹤無法使用時，它會在 [偵錯工具] 主控台中顯示警告。 您可以將程式碼加入此處理程式，以視需要從您的應用程式提供回應。

從**AppMain：**

```
   void HolographicApp1Main::OnLocatabilityChanged(SpatialLocator^ sender, Object^ args)
   {
       switch (sender->Locatability)
       {
       case SpatialLocatability::Unavailable:
           // Holograms cannot be rendered.
           {
               String^ message = L"Warning! Positional tracking is " +
                                           sender->Locatability.ToString() + L".\n";
               OutputDebugStringW(message->Data());
           }
           break;

       // In the following three cases, it is still possible to place holograms using a
       // SpatialLocatorAttachedFrameOfReference.
       case SpatialLocatability::PositionalTrackingActivating:
           // The system is preparing to use positional tracking.

       case SpatialLocatability::OrientationOnly:
           // Positional tracking has not been activated.

       case SpatialLocatability::PositionalTrackingInhibited:
           // Positional tracking is temporarily inhibited. User action may be required
           // in order to restore positional tracking.
           break;

       case SpatialLocatability::PositionalTrackingActive:
           // Positional tracking is active. World-locked content can be rendered.
           break;
       }
   }
```

## <a name="spatial-mapping"></a>空間對應

[空間對應](spatial-mapping-in-directx.md)api 會使用座標系統來取得 surface 網格的模型轉換。

## <a name="see-also"></a>另請參閱
* [座標系統](coordinate-systems.md)
* [空間錨點](spatial-anchors.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* [DirectX 中的頭部和眼睛目光](gaze-in-directx.md)
* [DirectX 中的手部和運動控制器](hands-and-motion-controllers-in-directx.md)
* [DirectX 中的空間對應](spatial-mapping-in-directx.md)
