---
title: DirectX 中的座標系統
description: 說明如何使用 Windows Mixed Reality 空間定位器，參考畫面格，空間的錨點和座標系統、 如何使用 SpatialStage、 追蹤遺失的處理方式、 如何儲存及載入錨點，以及如何進行影像穩定。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 混合實境，空間的定位器，空間的參考框架、 空間座標系統，空間的階段中，範例程式碼、 映像穩定、 空間的錨點、 空間錨點存放區、 追蹤遺失、 逐步解說
ms.openlocfilehash: 5a48e0a829ba8647718e28ec20760d8a764b13fe
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65628977"
---
# <a name="coordinate-systems-in-directx"></a>DirectX 中的座標系統

[座標系統](coordinate-systems.md)形成基礎的 Windows Mixed Reality Api 所提供的空間的了解。

現今的插入擴充槽 VR 或單一空間 VR 裝置建立一個主要的座標系統表示其追蹤的空間。 Windows Mixed Reality 裝置例如 HoloLens 專為在整個大型未定義的環境，探索及了解其周圍環境中，為使用者的裝置將逐步引導周圍。 這可讓裝置，以配合持續改進使用者的聊天室，但結果中，將其關聯性至另一部應用程式的存留期內的座標系統的相關知識。 Windows Mixed Reality 支援廣泛的裝置，範圍從安置的沈浸式耳機到全球附加的參考畫面格。

>[!NOTE]
>目前在這篇文章中的程式碼片段示範如何使用C++/CX 而不是 C + + 17 相容C++中所使用的 /WinRT [ C++全像攝影版的專案範本](creating-a-holographic-directx-project.md)。  概念是相等的C++/WinRT 專案，但您必須將轉譯程式碼。

## <a name="spatial-coordinate-systems-in-windows"></a>在 Windows 中的空間座標系統

用來在 Windows 中的真實世界座標系統的理解的核心型別是<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>。 此類型的執行個體代表任意的座標系統，並提供方法來取得您可以使用兩個座標系統，而不了解每個詳細資料之間轉換的轉換矩陣。

傳回表示為點、 光線或在使用者的恍神的磁碟區的空間資訊的方法會接受 SpatialCoordinateSystem 參數讓您決定它是最適合這些座標來傳回座標系統。 這些座標的單位一律會以公尺為單位。

SpatialCoordinateSystem 具有動態的關聯性，與其他的座標系統，包括代表裝置的位置。 在任何時間點，可能找不到某些座標系統並不會針對其他裝置。 對於大多數的座標系統中，您的應用程式必須準備好處理一段期間它們找不到的時間。

您的應用程式應該不會直接 SpatialCoordinateSystems 建立-而是它們應該取用透過 Perception Api。 有三個主要的來源座標系統在 Perception Api 中，每個所述的概念的地圖[座標系統](coordinate-systems.md)頁面：
* 若要取得靜態參考座標系，請建立<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a>或取得目前<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>。
* 若要取得空間的錨點，請建立<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>。
* 若要取得附加的畫面格的參考，建立<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>。

所有這些物件所傳回的座標系統是右手性，以 + y、 + x 右邊和 + z 回溯。 您可以記住正 z 軸點上按一下滑鼠正 x 方向指向您的左邊或右邊的手指 curling 它們到正 y 方向的方向。 您拇指所指的方向，不論是指向您或指向您的反方向，即是該座標系統正 z 軸所指的方向。 下圖顯示這兩個座標系統。

![左側和右側的座標系統](images/left-hand-right-hand.gif)<br>
*左側和右側的座標系統*

若要啟動到 SpatialCoordinateSystem HoloLens 位置為基礎，使用<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>類別來建立任一附加或靜態參考座標系，如下列各節中所述。

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a>全像投影置於世界的使用空間的階段

使用靜態存取座標系統的不透明的 Windows Mixed Reality 沈浸式耳機<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a>屬性。 此 API 提供的行動裝置、 播放程式是否四處跑的座標系統的相關資訊是否置於播放程式或行動裝置、 安全區域的界限，並指出耳機是方向性。 另外還有空間階段更新的事件處理常式。

首先，我們會取得空間的階段，並訂閱更新： 

程式碼**空間階段初始化**

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

在 OnCurrentChanged 方法中，您的應用程式應該檢查空間的階段，並據以更新玩家體驗。 在此範例中，我們提供階段界限，以及使用者和檢視階段的範圍和範圍的移動屬性所指定的起始位置的視覺的效果。 我們也改為使用自己 「 定態的座標系統中，無法提供階段時。


程式碼**空間階段更新**

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

以順時針順序提供的定義階段界限的頂點集合。 Windows Mixed Reality shell 範圍的界限時繪製使用者接近它;您可能想要供您自己 triangularize 查核的區域。 可以使用下列演算法，以 triangularize 階段。


程式碼**空間階段 triangularization**

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

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a>使用靜態參考座標系世界中放置全像投影

[SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx)類別表示的框架參考該[維持不動](coordinate-systems.md#stationary-frame-of-reference)相對於使用者的使用者身分的周圍環境移動。 此參考架構會優先選擇維持穩定裝置附近的座標。 SpatialStationaryFrameOfReference 一個主要用法是做為基礎的全局座標系統中的轉譯引擎，呈現全像投影時。

若要取得 SpatialStationaryFrameOfReference，請使用[SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx)類別，並呼叫[CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx)。

從 Windows 全像攝影版的應用程式範本程式碼：

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* 靜態參考框架專為提供的自動調整的位置，相對於整體的空間。 在該參考框架內的個別位置都可以稍微漂移。 這是正常現象，因為裝置知道更多的環境。
* 需要個別全像投影的精確位置時，SpatialAnchor 應該用來錨定在個別的全像真實世界中的位置-例如，點使用者表示特別感興趣的。 錨點位置不漂移，但您可以更正;錨點將會使用已更正之後更正發生在下一個畫面格開始的位置。

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a>全像投影置於使用空間的錨點的世界

[空間的錨點](coordinate-systems.md#spatial-anchors)很適合用來將全像投影放在真實世界中的特定位置，與系統確保錨點保留在原地經過一段時間。 本主題說明如何建立和使用錨點，以及如何使用錨點的資料。

您可以在任何位置和方向 SpatialCoordinateSystem 內您所選擇的建立 SpatialAnchor。 裝置必須能夠找到該座標系統，此時，，而且系統必須未達到其限制的空間的錨點。

定義好之後，SpatialAnchor 座標系統將持續調整，以保留的精確位置和方向其初始位置。 此 SpatialAnchor 接著可用來呈現全像投影會出現在使用者的恍神該確切的位置固定。

做為錨點增加從距離更被明顯的就地保留錨點的調整效果。 因此，您應該避免超過約 3 個計量會錨定的原始的錨點相對的呈現內容。

[CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx)屬性會取得一個座標系統，可讓您放置相對於錨點，內容加/減速套用時裝置調整錨點的確切位置。

使用[RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx)屬性和對應[RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx)自行管理這些調整的事件。

### <a name="persist-and-share-spatial-anchors"></a>保存和共用空間的錨點

您可以保存在本機使用 SpatialAnchor [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)類別，然後將它取得上一步在未來的應用程式工作階段中相同的 HoloLens 裝置上。

藉由使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間的錨點</a>，您可以從本機的 SpatialAnchor，然後會跨多個 HoloLens、 iOS 和 Android 裝置可以找出您的應用程式建立持久的雲端錨點。  藉由跨多個裝置共用常見的空間錨點，每位使用者都可以看到相對於該錨點相同的實體位置中呈現內容。  這可讓您即時分享經驗。

您也可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間的錨點</a>非同步闀持續性跨 HoloLens、 iOS 和 Android 裝置。  藉由共用持久的雲端空間錨點，多個裝置可以觀察相同的保存全像經過一段時間，即使這些裝置不存在一起在相同的時間。

若要開始建置 HoloLens 應用程式中的共用的體驗，試用 5 分鐘<a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">空間錨點 HoloLens Azure 快速入門</a>。

一旦您啟動並執行 Azure 空間的起點，您可以接著<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">建立和 HoloLens 上尋找起點</a>。  皆有逐步解說<a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android 和 iOS</a> ，讓您能夠共用相同的錨點，在所有裝置上。

### <a name="create-spatialanchors-for-holographic-content"></a>建立 SpatialAnchors 全像攝影版的內容

此程式碼範例中，我們修改 Windows 全像攝影版的應用程式範本來建立錨定的時機**Pressed**偵測到筆勢時。 呈現階段期間，該 cube 然後會放在錨點。

協助程式類別支援多個錨點，因為我們可以將多個 cube，因為我們想使用此程式碼範例 ！

附註的錨點識別碼是您在您的應用程式中控制的項目。 在此範例中，我們已建立為循序的目前儲存的錨點的應用程式的集合中的錨點數目為基礎的命名配置。

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

我們來看看如何撰寫 SampleSpatialAnchorHelper 類別，可協助處理此持續性，包括：
* 將儲存於記憶體中的錨點的集合，編製索引的 platform:: string 索引鍵。
* 從系統的 SpatialAnchorStore 中載入的錨點，這是與分開本機記憶體中的集合。
* 若要這樣做選擇的應用程式時，請將本機記憶體中集合的錨點儲存到 SpatialAnchorStore 」。

以下是如何儲存[SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx)中的物件[SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)。

當類別已啟動時，我們要求 SpatialAnchorStore 以非同步的方式。 這牽涉到系統 I/O API 載入錨點存放區中，以及此 API 使非同步 I/O 未封鎖。

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

您將會提供您可用來儲存錨點 SpatialAnchorStore。 這是將是字串，與 SpatialAnchors 資料值的索引鍵值 Imapview<k。 在我們的範例程式碼，我們將這儲存在私用類別成員變數，可透過我們的協助程式類別的公用函式存取。

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
>別忘了連結暫止/繼續事件，來儲存及載入錨點存放區。

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

當系統暫止您的應用程式時，您需要儲存空間的錨點到錨點存放區。 當您發現必須存在才能讓您的應用程式實作，您也可以選擇在其他時候，儲存到錨點存放區的錨點。

當您準備好要試著以 SpatialAnchorStore 儲存於記憶體中的錨點時，您可以您的集合執行迴圈，然後再次嘗試儲存每一個。

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

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a>應用程式會繼續執行時，從錨點存放區載入內容

當您的應用程式會繼續時，或在您的應用程式 implementaiton 」 所需的任何其他時間，您可以還原已藉由將它們從錨點存放區的 Imapview<k 傳送到您自己的記憶體中資料庫的 SpatialAnchors 先前儲存至 AnchorStore 的錨點。

若要從 SpatialAnchorStore 還原錨點，還原有興趣加入記憶體中集合的每個。

您需要自己的記憶體中資料庫的 SpatialAnchors;將字串與您建立 SpatialAnchors 某種方式。 在我們的範例程式碼，我們選擇使用 Windows::Foundation::Collections::IMap 儲存錨點，讓您輕鬆地針對 SpatialAnchorStore 使用相同的索引鍵和資料值。

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
>還原的錨點可能無法之外的可尋獲立即。 比方說，它可能在不同房間內或不同建置完全的錨點。 Locatability 應該經過 AnchorStore 從擷取的錨點才能使用。

<br>

>[!NOTE]
>在此範例程式碼中，我們會從 AnchorStore 擷取所有的錨點。 這不是需求;您的應用程式可能也挑選起點子集使用對您的實作有意義的字串索引鍵值。

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

### <a name="clear-the-anchor-store-when-needed"></a>需要時清除錨點存放區

有時候，您要清除應用程式狀態，並寫入新的資料。 以下是您如何執行動作，使用[SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)。

使用我們的 helper 類別，就幾乎不需要將包裝的清楚的函式。 我們選擇這麼做在我們的範例實作，因為我們的協助程式類別提供擁有 SpatialAnchorStore 執行個體的責任。

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

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a>範例：與靜態參考畫面格的座標系統中的錨點的座標系統

假設您有錨點，而您想要與您已在使用適用於大部分的其他內容 SpatialStationaryReferenceFrame 錨點的座標系統中的項目。 您可以使用[TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx)以取得轉換的錨點的座標系統的靜態參考框架：

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

此程序是適合您有兩種：
1. 它會告訴您如果兩個參考框架相對於另一個，就可以了解和;
2. 如果是的話，它提供您直接從一個座標系統移至其他轉換。

利用此資訊，您會了解空間之間的關聯性的兩個參考畫面格之間的物件。

進行轉譯中,，您通常可以藉由群組根據其原始的參考框架 」 或 「 錨點的物件，以取得更好的結果。 每個群組執行獨立的繪圖行程。 檢視矩陣會變得更精確物件模型轉換會建立一開始使用相同的座標系統。

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a>建立使用裝置連接參考框架的全像投影

有些的時候，當您想要呈現雷射所[會保持附加狀態](coordinate-systems.md#attached-frame-of-reference)到裝置的位置，例如進行偵錯資訊或資訊訊息時，才能夠判斷其方向裝置面板和不在中的位置空間。 為了達成此目的，我們會使用附加的畫面格的參考。

SpatialLocatorAttachedFrameOfReference 類別定義是相對於裝置，而不是真實世界的座標系統。 此框架有固定的標題相對於指向方向使用者當時正面臨參考畫面格建立時的使用者的恍神。 從那時起，在此參考架構中的所有方向都是相對於該固定的標題中是即使在使用者旋轉裝置。

HoloLens，針對此畫面格的座標系統的原點位於旋轉的中心點的使用者的標頭，使它的位置不會受到前端的旋轉。 您的應用程式可以指定相對於放置在使用者之前全像投影此點的位移。

若要取得 SpatialLocatorAttachedFrameOfReference，使用 SpatialLocator 類別並呼叫 CreateAttachedFrameOfReferenceAtCurrentHeading。

請注意，這適用於整個範圍的 Windows Mixed Reality 裝置。

### <a name="use-a-reference-frame-attached-to-the-device"></a>使用附加至裝置的參考框架

下列各節討論我們在 Windows 全像攝影版的應用程式範本，以啟用裝置附加參考框架的使用此 API 中的變更。 請注意，此 「 附加 」 的全像將與靜態或錨定全像投影，一起運作，而且可能也在裝置暫時找不到在世界中的位置時才使用。

首先，我們會變更儲存而不是 SpatialStationaryFrameOfReference SpatialLocatorAttachedFrameOfReference 範本：

從**HolographicTagAlongSampleMain.h**:

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

從**HolographicTagAlongSampleMain.cpp**:

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

在更新期間，我們現在會取得座標系統在取自與框架預測的時間戳記。

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a>取得指標空間姿勢，並依照使用者的視線

我們想要追蹤使用者的我們範例闀[視線](gaze.md)，類似於在全像攝影版的殼層如何依照使用者的視線。 為此，我們需要 SpatialPointerPose 獲得相同的時間戳記。

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

此 SpatialPointerPose 有位置根據全像所需的資訊[使用者的目前標題](gaze-in-directx.md)。

基於使用者的詳細資訊，我們會使用線性插補 (「 lerp") 平滑的位置變更，使得它經過一段時間，就會發生。 這是使用者於鎖定至其視線闀更舒適。 Lerping tag-along 全像的位置也可讓我們依抑制移動; 穩定全像如果我們沒有這個抑制，使用者會看到全像圖抖動由於功能通常被視為是使用者的標頭的音調移動。

從**StationaryQuadRenderer::PositionHologram**:

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
>在偵錯的窗格中，您可以選擇調整有點位置關閉的側邊全像，使它不會阻擋您的檢視。 以下是如何，您可能會執行的範例。

針對**StationaryQuadRenderer::PositionHologram**:

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

### <a name="rotate-the-hologram-to-face-the-camera"></a>旋轉面對相機全像

並不夠，只是定位全像圖，在此情況下是四組數字;我們也必須旋轉面對使用者的物件。 請注意，這種旋轉，就會發生在世界空間中，因為這種類型的告示板，可讓 「 保持使用者的環境的一部分全像。 檢視空間告示板並不知道如何為因為全像變為鎖定狀態來顯示方向;在此情況下，您也必須以取得不會破壞立體聲的轉譯檢視空間告示板轉換左邊和右邊的檢視矩陣之間進行插補。 在這裡，我們會旋轉面對使用者 X 和 Z 軸上。

從**StationaryQuadRenderer::Update**:

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

### <a name="render-the-attached-hologram"></a>呈現連結的全像

針對此範例中，我們也會選擇將轉譯的座標系統中 SpatialLocatorAttachedReferenceFrame，全像圖也就是我們所在全像圖。 （如果我們決定使用另一個座標系統來呈現，我們需要取得從裝置連接的參考畫面格的座標系統轉換至該座標系統。）

從**HolographicTagAlongSampleMain::Render**:

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

就這麼容易！ 全像圖會現在"追趕 」 使用者的視線方向前面 2 公尺的位置。

>[!NOTE]
>此範例也會載入額外的內容-請參閱 StationaryQuadRenderer.cpp。

## <a name="handling-tracking-loss"></a>處理追蹤遺失

當裝置找不到本身的世界中時，應用程式就會發生 「 追蹤遺失 」。 Windows Mixed Reality 應用程式應該能夠處理這類中斷的位置追蹤系統。 可觀察這些中斷，並利用預設 SpatialLocator LocatabilityChanged 事件回應建立。

從**AppMain::SetHolographicSpace:**

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

當您的應用程式收到 LocatabilityChanged 事件時，它可以視需要變更行為。 比方說，在 PositionalTrackingInhibited 狀態下，您的應用程式可以暫停正常操作並轉譯[tag-along 全像](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference)，會顯示一則警告訊息。

Windows 全像攝影版的應用程式範本隨附於已為您建立的 LocatabilityChanged 處理常式。 根據預設，它會顯示一則警告偵錯主控台無法使用位置追蹤時。 您可以將程式碼加入這個處理常式，來提供回應，視需要從您的應用程式。

從**AppMain.cpp:**

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

[空間對應](spatial-mapping-in-directx.md)Api 進行介面網狀結構取得模型轉換的座標系統的使用。

## <a name="see-also"></a>另請參閱
* [座標系統](coordinate-systems.md)
* [空間錨點](spatial-anchors.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* [DirectX 中的前端和眼睛視線](gaze-in-directx.md)
* [指針與 DirectX 中的動作控制站](hands-and-motion-controllers-in-directx.md)
* [DirectX 中的空間對應](spatial-mapping-in-directx.md)
