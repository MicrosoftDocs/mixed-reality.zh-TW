---
title: 在 DirectX 中協調系統
description: 說明如何使用 Windows Mixed Reality 空間定位器、參考框架、空間錨點和座標系統、如何使用 SpatialStage、如何處理追蹤遺失、如何儲存和載入錨點, 以及如何執行影像穩定。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Mixed Reality, 空間定位器, 空間參考框架, 空間座標系統, 空間階段, 範例程式碼, 影像穩定, 空間錨點, 空間錨點存放區, 追蹤遺失, 逐步解說
ms.openlocfilehash: 5a48e0a829ba8647718e28ec20760d8a764b13fe
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65628977"
---
# <a name="coordinate-systems-in-directx"></a><span data-ttu-id="72f32-104">在 DirectX 中協調系統</span><span class="sxs-lookup"><span data-stu-id="72f32-104">Coordinate systems in DirectX</span></span>

<span data-ttu-id="72f32-105">[座標系統](coordinate-systems.md)會形成 Windows Mixed Reality api 所提供空間理解的基礎。</span><span class="sxs-lookup"><span data-stu-id="72f32-105">[Coordinate systems](coordinate-systems.md) form the basis for spatial understanding offered by Windows Mixed Reality APIs.</span></span>

<span data-ttu-id="72f32-106">今天的固定的 VR 或單一空間 VR 裝置會建立一個主要座標系統來代表其追蹤的空間。</span><span class="sxs-lookup"><span data-stu-id="72f32-106">Today's seated VR or single-room VR devices establish one primary coordinate system to represent their tracked space.</span></span> <span data-ttu-id="72f32-107">Windows Mixed Reality 裝置 (如 HoloLens) 是設計用來在大型未定義的環境中使用, 裝置會在使用者流覽時探索並瞭解其周圍的範圍。</span><span class="sxs-lookup"><span data-stu-id="72f32-107">Windows Mixed Reality devices such as HoloLens are designed to be used throughout large undefined environments, with the device discovering and learning about its surroundings as the user walks around.</span></span> <span data-ttu-id="72f32-108">這可讓裝置調整以持續改善使用者聊天室的知識, 但會導致協調系統在應用程式的存留期內變更彼此的關聯性。</span><span class="sxs-lookup"><span data-stu-id="72f32-108">This allows the device to adapt to continually-improving knowledge about the user's rooms, but results in coordinate systems that will change their relationship to one another through the lifetime of the app.</span></span> <span data-ttu-id="72f32-109">Windows Mixed Reality 支援各式各樣的裝置, 範圍從固定的沉浸式耳機到全球附加的參考框架。</span><span class="sxs-lookup"><span data-stu-id="72f32-109">Windows Mixed Reality supports a wide spectrum of devices, ranging from seated immersive headsets through world-attached reference frames.</span></span>

>[!NOTE]
><span data-ttu-id="72f32-110">本文中的程式碼片段目前示範如何使用C++/cx, C++ [ C++ ](creating-a-holographic-directx-project.md)而不是 C + 17 相容的/WinRT, 如全像攝影專案範本中所使用。</span><span class="sxs-lookup"><span data-stu-id="72f32-110">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="72f32-111">概念相當於C++/WinRT 專案, 但您必須轉譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="72f32-111">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="spatial-coordinate-systems-in-windows"></a><span data-ttu-id="72f32-112">Windows 中的空間座標系統</span><span class="sxs-lookup"><span data-stu-id="72f32-112">Spatial coordinate systems in Windows</span></span>

<span data-ttu-id="72f32-113">用來因應 Windows 中真實全局座標系統原因的核心類型是<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>。</span><span class="sxs-lookup"><span data-stu-id="72f32-113">The core type used to reason about real-world coordinate systems in Windows is the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>.</span></span> <span data-ttu-id="72f32-114">這個類型的實例代表任意座標系統, 並提供方法來取得轉換矩陣, 您可以在兩個座標系統之間進行轉換, 而不需要瞭解每個座標系統的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="72f32-114">An instance of this type represents an arbitrary coordinate system and provides a method to get a transformation matrix that you can use to transform between two coordinate systems without understanding the details of each.</span></span>

<span data-ttu-id="72f32-115">傳回空間資訊 (以點、光線或使用者環境中的磁片區表示) 的方法將會接受 SpatialCoordinateSystem 參數, 讓您決定其最適用于傳回這些座標的座標系統。</span><span class="sxs-lookup"><span data-stu-id="72f32-115">Methods that return spatial information, represented as points, rays, or volumes in the user's surroundings, will accept a SpatialCoordinateSystem parameter to let you decide the coordinate system in which it's most useful for those coordinates to be returned.</span></span> <span data-ttu-id="72f32-116">這些座標的單位將一律為計量。</span><span class="sxs-lookup"><span data-stu-id="72f32-116">The units for these coordinates will always be in meters.</span></span>

<span data-ttu-id="72f32-117">SpatialCoordinateSystem 與其他座標系統有動態關聯性, 包括代表裝置位置的關係。</span><span class="sxs-lookup"><span data-stu-id="72f32-117">A SpatialCoordinateSystem has a dynamic relationship with other coordinate systems, including those that represent the device's position.</span></span> <span data-ttu-id="72f32-118">在任何時間點, 裝置都可能找不到某些座標系統, 而不能找到其他。</span><span class="sxs-lookup"><span data-stu-id="72f32-118">At any point in time, the device may be able to locate some coordinate systems and not others.</span></span> <span data-ttu-id="72f32-119">對於大部分的座標系統, 您的應用程式必須準備好處理找不到它們的時間週期。</span><span class="sxs-lookup"><span data-stu-id="72f32-119">For most coordinate systems, your app must be ready to handle periods of time during which they cannot be located.</span></span>

<span data-ttu-id="72f32-120">您的應用程式不應該直接建立 SpatialCoordinateSystems, 而是應該透過認知 Api 使用。</span><span class="sxs-lookup"><span data-stu-id="72f32-120">Your application should not create SpatialCoordinateSystems directly - rather they should be consumed via the Perception APIs.</span></span> <span data-ttu-id="72f32-121">在認知 Api 中有三個主要的座標系統來源, 每個都對應到 [[座標系統](coordinate-systems.md)] 頁面上所述的概念:</span><span class="sxs-lookup"><span data-stu-id="72f32-121">There are three primary sources of coordinate systems in the Perception APIs, each of which map to a concept described on the [Coordinate systems](coordinate-systems.md) page:</span></span>
* <span data-ttu-id="72f32-122">若要取得固定的參考框架, 請建立<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> , 或從目前的<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>取得一個。</span><span class="sxs-lookup"><span data-stu-id="72f32-122">To get a stationary frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> or obtain one from the current <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>.</span></span>
* <span data-ttu-id="72f32-123">若要取得空間錨點, 請建立<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>。</span><span class="sxs-lookup"><span data-stu-id="72f32-123">To get a spatial anchor, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.</span></span>
* <span data-ttu-id="72f32-124">若要取得附加的參考框架, 請建立<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>。</span><span class="sxs-lookup"><span data-stu-id="72f32-124">To get an attached frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.</span></span>

<span data-ttu-id="72f32-125">這些物件所傳回的所有座標系統都是右手的, 其中 + y 向上、+ x 向右和 + z 向後。</span><span class="sxs-lookup"><span data-stu-id="72f32-125">All of the coordinate systems returned by these objects are right-handed, with +y up, +x to the right and +z backwards.</span></span> <span data-ttu-id="72f32-126">您可以記住正 Z 軸點的方向, 其方式是將左或右手指指向正 x 方向, 並將其 curling 為正 y 方向。</span><span class="sxs-lookup"><span data-stu-id="72f32-126">You can remember which direction the positive z-axis points by pointing the fingers of either your left or right hand in the positive x direction and curling them into the positive y direction.</span></span> <span data-ttu-id="72f32-127">您拇指所指的方向，不論是指向您或指向您的反方向，即是該座標系統正 z 軸所指的方向。</span><span class="sxs-lookup"><span data-stu-id="72f32-127">The direction your thumb points, either toward or away from you, is the direction that the positive z-axis points for that coordinate system.</span></span> <span data-ttu-id="72f32-128">下圖顯示這兩個座標系統。</span><span class="sxs-lookup"><span data-stu-id="72f32-128">The following illustration shows these two coordinate systems.</span></span>

<span data-ttu-id="72f32-129">![左手邊和右手座標系統](images/left-hand-right-hand.gif)</span><span class="sxs-lookup"><span data-stu-id="72f32-129">![Left-hand and right-hand coordinate systems](images/left-hand-right-hand.gif)</span></span><br>
<span data-ttu-id="72f32-130">*左手邊和右手座標系統*</span><span class="sxs-lookup"><span data-stu-id="72f32-130">*Left-hand and right-hand coordinate systems*</span></span>

<span data-ttu-id="72f32-131">若要根據 HoloLens 的位置啟動至 SpatialCoordinateSystem, 請使用<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>類別來建立附加或固定的參考框架, 如下列各節所述。</span><span class="sxs-lookup"><span data-stu-id="72f32-131">To bootstrap into a SpatialCoordinateSystem based on the position of a HoloLens, use the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> class to create either an attached or stationary frame of reference, as described in the sections below.</span></span>

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a><span data-ttu-id="72f32-132">使用空間階段將全息影像放在世界中</span><span class="sxs-lookup"><span data-stu-id="72f32-132">Place holograms in the world using a spatial stage</span></span>

<span data-ttu-id="72f32-133">不透明的 Windows Mixed Reality 沉浸式耳機的座標系統是使用靜態<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference:: Current</a>屬性來存取。</span><span class="sxs-lookup"><span data-stu-id="72f32-133">The coordinate system for opaque Windows Mixed Reality immersive headsets is accessed using the static <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a> property.</span></span> <span data-ttu-id="72f32-134">此 API 會提供座標系統、有關播放程式是否為「上一部」或「行動裝置」的資訊、可用於流覽玩家是否行動的安全區域界限, 以及是否有耳機方向的指示。</span><span class="sxs-lookup"><span data-stu-id="72f32-134">This API provides a coordinate system, information about whether the player is seated or mobile, the boundary of a safe area for walking around if the player is mobile, and an indication of whether or not the headset is directional.</span></span> <span data-ttu-id="72f32-135">也有一個事件處理常式可更新空間階段。</span><span class="sxs-lookup"><span data-stu-id="72f32-135">There is also an event handler for updates to the spatial stage.</span></span>

<span data-ttu-id="72f32-136">首先, 我們會取得空間階段並訂閱其更新:</span><span class="sxs-lookup"><span data-stu-id="72f32-136">First, we get the spatial stage and subscribe for updates to it:</span></span> 

<span data-ttu-id="72f32-137">**空間階段初始化**的程式碼</span><span class="sxs-lookup"><span data-stu-id="72f32-137">Code for **Spatial stage initialization**</span></span>

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

<span data-ttu-id="72f32-138">在 OnCurrentChanged 方法中, 您的應用程式應該檢查空間階段, 並據此更新玩家體驗。</span><span class="sxs-lookup"><span data-stu-id="72f32-138">In the OnCurrentChanged method, your app should inspect the spatial stage and update the player experience accordingly.</span></span> <span data-ttu-id="72f32-139">在此範例中, 我們提供階段界限的視覺效果, 以及使用者所指定的開始位置, 以及階段的視圖範圍和移動屬性的範圍。</span><span class="sxs-lookup"><span data-stu-id="72f32-139">In this example, we provide a visualization of the stage boundary, as well as the start position specified by the user and the stage's range of view and range of movement properties.</span></span> <span data-ttu-id="72f32-140">當無法提供階段時, 我們也會回到自己的固定座標系統。</span><span class="sxs-lookup"><span data-stu-id="72f32-140">We also fall back to our own stationary coordinate system, when a stage cannot be provided.</span></span>


<span data-ttu-id="72f32-141">**空間階段更新**的程式碼</span><span class="sxs-lookup"><span data-stu-id="72f32-141">Code for **Spatial stage update**</span></span>

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

<span data-ttu-id="72f32-142">定義階段界限的一組頂點會以順時針順序提供。</span><span class="sxs-lookup"><span data-stu-id="72f32-142">The set of vertices that define the stage boundary are provided in clockwise order.</span></span> <span data-ttu-id="72f32-143">當使用者使用時, Windows Mixed Reality shell 會在界限上繪製一個範圍;基於您的目的, 您可能會想要 triangularize walkable 區域。</span><span class="sxs-lookup"><span data-stu-id="72f32-143">The Windows Mixed Reality shell draws a fence at the boundary when the user approaches it; you may wish to triangularize the walkable area for your own purposes.</span></span> <span data-ttu-id="72f32-144">下列演算法可以用來 triangularize 階段。</span><span class="sxs-lookup"><span data-stu-id="72f32-144">The following algorithm can be used to triangularize the stage.</span></span>


<span data-ttu-id="72f32-145">**空間階段 triangularization**的程式碼</span><span class="sxs-lookup"><span data-stu-id="72f32-145">Code for **Spatial stage triangularization**</span></span>

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

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a><span data-ttu-id="72f32-146">使用固定的參考框架, 將全息影像放在世界各地</span><span class="sxs-lookup"><span data-stu-id="72f32-146">Place holograms in the world using a stationary frame of reference</span></span>

<span data-ttu-id="72f32-147">[SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx)類別代表在使用者四處移動時, 相對於[保持靜止](coordinate-systems.md#stationary-frame-of-reference)的使用者周圍範圍的參考框架。</span><span class="sxs-lookup"><span data-stu-id="72f32-147">The [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) class represents a frame of reference that [remains stationary](coordinate-systems.md#stationary-frame-of-reference) relative to the user's surroundings as the user moves around.</span></span> <span data-ttu-id="72f32-148">此參考框架會優先保留裝置附近的穩定座標。</span><span class="sxs-lookup"><span data-stu-id="72f32-148">This frame of reference prioritizes keeping coordinates stable near the device.</span></span> <span data-ttu-id="72f32-149">SpatialStationaryFrameOfReference 的其中一個主要用途, 就是在呈現全息影像時, 做為轉譯引擎內的基礎全局座標系統。</span><span class="sxs-lookup"><span data-stu-id="72f32-149">One key use of a SpatialStationaryFrameOfReference is to act as the underlying world coordinate system within a rendering engine when rendering holograms.</span></span>

<span data-ttu-id="72f32-150">若要取得 SpatialStationaryFrameOfReference, 請使用[SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx)類別並呼叫[CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx)。</span><span class="sxs-lookup"><span data-stu-id="72f32-150">To get a SpatialStationaryFrameOfReference, use the [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) class and call [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).</span></span>

<span data-ttu-id="72f32-151">從 Windows 全像應用程式範本:</span><span class="sxs-lookup"><span data-stu-id="72f32-151">From the Windows Holographic app template code:</span></span>

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* <span data-ttu-id="72f32-152">固定的參考框架是設計來提供相對於整體空間的最佳調整位置。</span><span class="sxs-lookup"><span data-stu-id="72f32-152">Stationary reference frames are designed to provide a best-fit position relative to the overall space.</span></span> <span data-ttu-id="72f32-153">該參考框架內的個別位置可以稍微漂移。</span><span class="sxs-lookup"><span data-stu-id="72f32-153">Individual positions within that reference frame are allowed to drift slightly.</span></span> <span data-ttu-id="72f32-154">當裝置學習更多有關環境的資訊時, 這是正常現象。</span><span class="sxs-lookup"><span data-stu-id="72f32-154">This is normal as the device learns more about the environment.</span></span>
* <span data-ttu-id="72f32-155">當需要精確放置個別的全息影像時, 應該使用 SpatialAnchor 將個別的全息影像錨定到真實世界中的某個位置, 例如, 使用者表示特別感興趣的點。</span><span class="sxs-lookup"><span data-stu-id="72f32-155">When precise placement of individual holograms is required, a SpatialAnchor should be used to anchor the individual hologram to a position in the real world - for example, a point the user indicates to be of special interest.</span></span> <span data-ttu-id="72f32-156">錨點位置不會漂移, 但可以加以更正;錨點會在更正發生後, 使用下一個畫面中的已更正位置開始。</span><span class="sxs-lookup"><span data-stu-id="72f32-156">Anchor positions do not drift, but can be corrected; the anchor will use the corrected position starting in the next frame after the correction has occurred.</span></span>

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a><span data-ttu-id="72f32-157">使用空間錨點將全息影像放在世界中</span><span class="sxs-lookup"><span data-stu-id="72f32-157">Place holograms in the world using spatial anchors</span></span>

<span data-ttu-id="72f32-158">[空間錨點](coordinate-systems.md#spatial-anchors)是將全息影像放在真實世界中特定位置的絕佳方式, 而系統可確保錨點會在一段時間內保持不變。</span><span class="sxs-lookup"><span data-stu-id="72f32-158">[Spatial anchors](coordinate-systems.md#spatial-anchors) are a great way to place holograms at a specific place in the real world, with the system ensuring the anchor stays in place over time.</span></span> <span data-ttu-id="72f32-159">本主題說明如何建立和使用錨點, 以及如何使用錨點資料。</span><span class="sxs-lookup"><span data-stu-id="72f32-159">This topic explains how to create and use an anchor, and how to work with anchor data.</span></span>

<span data-ttu-id="72f32-160">您可以在所選擇的 SpatialCoordinateSystem 內, 于任何位置和方向建立 SpatialAnchor。</span><span class="sxs-lookup"><span data-stu-id="72f32-160">You can create a SpatialAnchor at any position and orientation within the SpatialCoordinateSystem of your choosing.</span></span> <span data-ttu-id="72f32-161">裝置目前必須能夠找出該座標系統, 而且系統不能達到其空間錨點的限制。</span><span class="sxs-lookup"><span data-stu-id="72f32-161">The device must be able to locate that coordinate system at the moment, and the system must not have reached its limit of spatial anchors.</span></span>

<span data-ttu-id="72f32-162">一旦定義之後, SpatialAnchor 的座標系統會持續調整, 以保留其初始位置的精確位置和方向。</span><span class="sxs-lookup"><span data-stu-id="72f32-162">Once defined, the coordinate system of a SpatialAnchor adjusts continually to retain the precise position and orientation of its initial location.</span></span> <span data-ttu-id="72f32-163">接著, 您可以使用此 SpatialAnchor 來轉譯在該確切位置上, 會在使用者的環境中出現固定的全息影像。</span><span class="sxs-lookup"><span data-stu-id="72f32-163">You can then use this SpatialAnchor to render holograms that will appear fixed in the user's surroundings at that exact location.</span></span>

<span data-ttu-id="72f32-164">保留錨點的調整效果會隨著距離錨點增加而放大。</span><span class="sxs-lookup"><span data-stu-id="72f32-164">The effects of the adjustments that keep the anchor in place are magnified as distance from the anchor increases.</span></span> <span data-ttu-id="72f32-165">因此, 您應該避免轉譯相對於錨點來源大約3個計量的內容。</span><span class="sxs-lookup"><span data-stu-id="72f32-165">Therefore, you should avoid rendering content relative to an anchor that is more than about 3 meters from that anchor's origin.</span></span>

<span data-ttu-id="72f32-166">[CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx)屬性會取得座標系統, 讓您放置相對於錨點的內容, 並在裝置調整錨點的精確位置時套用緩時套用。</span><span class="sxs-lookup"><span data-stu-id="72f32-166">The [CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) property gets a coordinate system that lets you place content relative to the anchor, with easing applied when the device adjusts the anchor's precise location.</span></span>

<span data-ttu-id="72f32-167">使用[RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx)屬性和對應的[RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx)事件, 自行管理這些調整。</span><span class="sxs-lookup"><span data-stu-id="72f32-167">Use the [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) property and the corresponding [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) event to manage these adjustments yourself.</span></span>

### <a name="persist-and-share-spatial-anchors"></a><span data-ttu-id="72f32-168">保存和共用空間錨點</span><span class="sxs-lookup"><span data-stu-id="72f32-168">Persist and share spatial anchors</span></span>

<span data-ttu-id="72f32-169">您可以使用[SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)類別在本機保存 SpatialAnchor, 然後在相同 HoloLens 裝置上的未來應用程式會話中取回。</span><span class="sxs-lookup"><span data-stu-id="72f32-169">You can persist a SpatialAnchor locally using the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) class and then get it back in a future app session on the same HoloLens device.</span></span>

<span data-ttu-id="72f32-170">藉由使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a>, 您可以從本機 SpatialAnchor 建立長期雲端錨點, 然後您的應用程式可以在多個 HoloLens、IOS 和 Android 裝置上尋找。</span><span class="sxs-lookup"><span data-stu-id="72f32-170">By using <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>, you can create a durable cloud anchor from a local SpatialAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="72f32-171">藉由共用多個裝置上的通用空間錨點, 每個使用者都可以看到相對於相同實體位置中的錨點所呈現的內容。</span><span class="sxs-lookup"><span data-stu-id="72f32-171">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="72f32-172">這可提供即時共用體驗。</span><span class="sxs-lookup"><span data-stu-id="72f32-172">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="72f32-173">您也可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> 跨 HoloLens、iOS 和 Android 裝置取得非同步全像投影持久性。</span><span class="sxs-lookup"><span data-stu-id="72f32-173">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="72f32-174">藉由共用持久的雲端空間錨點，多個裝置就能觀察相同的已保存全像投影一段時間，即使那些裝置並未同時存在。</span><span class="sxs-lookup"><span data-stu-id="72f32-174">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="72f32-175">若要開始在 HoloLens 應用程式中建立共用體驗, 請嘗試5分鐘的<a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure 空間錨點 HoloLens 快速入門</a>。</span><span class="sxs-lookup"><span data-stu-id="72f32-175">To get started building shared experiences in your HoloLens app, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchors HoloLens quickstart</a>.</span></span>

<span data-ttu-id="72f32-176">當您使用 Azure 空間錨點啟動並執行時, 您可以接著在<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">HoloLens 上建立和尋找錨點</a>。</span><span class="sxs-lookup"><span data-stu-id="72f32-176">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">create and locate anchors on HoloLens</a>.</span></span>  <span data-ttu-id="72f32-177">逐步解說也適用于<a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android 和 iOS</a> , 可讓您在所有裝置上共用相同的錨點。</span><span class="sxs-lookup"><span data-stu-id="72f32-177">Walkthroughs are available for <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android and iOS</a> as well, enabling you to share the same anchors on all devices.</span></span>

### <a name="create-spatialanchors-for-holographic-content"></a><span data-ttu-id="72f32-178">建立全像攝影內容的 SpatialAnchors</span><span class="sxs-lookup"><span data-stu-id="72f32-178">Create SpatialAnchors for holographic content</span></span>

<span data-ttu-id="72f32-179">在此程式碼範例中, 我們已修改 Windows 全像投影應用程式範本, 以在偵測到**按下**的手勢時建立錨點。</span><span class="sxs-lookup"><span data-stu-id="72f32-179">For this code sample, we modified the Windows Holographic app template to create anchors when the **Pressed** gesture is detected.</span></span> <span data-ttu-id="72f32-180">接著, cube 會放在轉譯行程期間的錨點。</span><span class="sxs-lookup"><span data-stu-id="72f32-180">The cube is then placed at the anchor during the render pass.</span></span>

<span data-ttu-id="72f32-181">由於協助程式類別支援多個錨點, 因此我們可以使用此程式碼範例, 將多個 cube 放在同一個位置!</span><span class="sxs-lookup"><span data-stu-id="72f32-181">Since multiple anchors are supported by the helper class, we can place as many cubes as we want using this code sample!</span></span>

<span data-ttu-id="72f32-182">請注意, 錨點的識別碼是您在應用程式中控制的東西。</span><span class="sxs-lookup"><span data-stu-id="72f32-182">Note that the IDs for anchors are something you control in your app.</span></span> <span data-ttu-id="72f32-183">在此範例中, 我們已根據目前儲存在應用程式錨點集合中的錨點數目, 建立一個依序排列的命名配置。</span><span class="sxs-lookup"><span data-stu-id="72f32-183">In this example, we have created a naming scheme that is sequential based on the number of anchors currently stored in the app's collection of anchors.</span></span>

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

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a><span data-ttu-id="72f32-184">以非同步方式載入和快取, SpatialAnchorStore</span><span class="sxs-lookup"><span data-stu-id="72f32-184">Asynchronously load, and cache, the SpatialAnchorStore</span></span>

<span data-ttu-id="72f32-185">讓我們看看如何撰寫可協助處理此持續性的 SampleSpatialAnchorHelper 類別, 包括:</span><span class="sxs-lookup"><span data-stu-id="72f32-185">Let's see how to write a SampleSpatialAnchorHelper class that helps handle this persistence, including:</span></span>
* <span data-ttu-id="72f32-186">儲存記憶體內部錨點的集合, 並以 Platform:: String 索引鍵編制索引。</span><span class="sxs-lookup"><span data-stu-id="72f32-186">Storing a collection of in-memory anchors, indexed by a Platform::String key.</span></span>
* <span data-ttu-id="72f32-187">從系統的 SpatialAnchorStore 載入錨點, 這會與本機記憶體中的集合保持分開。</span><span class="sxs-lookup"><span data-stu-id="72f32-187">Loading anchors from the system's SpatialAnchorStore, which is kept separate from the local in-memory collection.</span></span>
* <span data-ttu-id="72f32-188">當應用程式選擇執行這項操作時, 將本機記憶體中的錨點集合儲存至 SpatialAnchorStore。</span><span class="sxs-lookup"><span data-stu-id="72f32-188">Saving the local in-memory collection of anchors to the SpatialAnchorStore when the app chooses to do so.</span></span>

<span data-ttu-id="72f32-189">以下說明如何將[SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx)物件儲存在[SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)中。</span><span class="sxs-lookup"><span data-stu-id="72f32-189">Here's how to save [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) objects in the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="72f32-190">當類別啟動時, 我們會以非同步方式要求 SpatialAnchorStore。</span><span class="sxs-lookup"><span data-stu-id="72f32-190">When the class starts up, we request the SpatialAnchorStore asynchronously.</span></span> <span data-ttu-id="72f32-191">這牽涉到系統 i/o, 因為 API 會載入錨點存放區, 而此 API 會設為非同步, 讓 i/o 不會封鎖。</span><span class="sxs-lookup"><span data-stu-id="72f32-191">This involves system I/O as the API loads the anchor store, and this API is made asynchronous so that the I/O is non-blocking.</span></span>

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

<span data-ttu-id="72f32-192">系統會提供您可用來儲存錨點的 SpatialAnchorStore。</span><span class="sxs-lookup"><span data-stu-id="72f32-192">You will be given a SpatialAnchorStore that you can use to save the anchors.</span></span> <span data-ttu-id="72f32-193">這是一個 IMapView, 它會將字串的索引鍵值 (也就是 SpatialAnchors 的資料值) 產生關聯。</span><span class="sxs-lookup"><span data-stu-id="72f32-193">This is an IMapView that associates key values that are Strings, with data values that are SpatialAnchors.</span></span> <span data-ttu-id="72f32-194">在我們的範例程式碼中, 我們會將它儲存在可透過協助程式類別的公用函式存取的私用類別成員變數中。</span><span class="sxs-lookup"><span data-stu-id="72f32-194">In our sample code, we store this in a private class member variable that is accessible through a public function of our helper class.</span></span>

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
><span data-ttu-id="72f32-195">別忘了連結暫止/繼續事件, 以儲存和載入錨定存放區。</span><span class="sxs-lookup"><span data-stu-id="72f32-195">Don't forget to hook up the suspend/resume events to save and load the anchor store.</span></span>

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

### <a name="save-content-to-the-anchor-store"></a><span data-ttu-id="72f32-196">將內容儲存至錨點存放區</span><span class="sxs-lookup"><span data-stu-id="72f32-196">Save content to the anchor store</span></span>

<span data-ttu-id="72f32-197">當系統暫停您的應用程式時, 您需要將空間錨點儲存至錨點存放區。</span><span class="sxs-lookup"><span data-stu-id="72f32-197">When the system suspends your app, you need to save your spatial anchors to the anchor store.</span></span> <span data-ttu-id="72f32-198">您也可以選擇在其他時間將錨點儲存至錨點存放區, 因為您會發現應用程式的實作為必要。</span><span class="sxs-lookup"><span data-stu-id="72f32-198">You may also choose to save anchors to the anchor store at other times, as you find to be necessary for your app's implementation.</span></span>

<span data-ttu-id="72f32-199">當您準備好要嘗試將記憶體中的錨點儲存至 SpatialAnchorStore 時, 您可以對集合執行迴圈, 並嘗試儲存每一個。</span><span class="sxs-lookup"><span data-stu-id="72f32-199">When you're ready to try saving the in-memory anchors to the SpatialAnchorStore, you can loop through your collection and try to save each one.</span></span>

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

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a><span data-ttu-id="72f32-200">當應用程式繼續時, 從錨點存放區載入內容</span><span class="sxs-lookup"><span data-stu-id="72f32-200">Load content from the anchor store when the app resumes</span></span>

<span data-ttu-id="72f32-201">當您的應用程式繼續進行, 或在您應用程式 implementaiton 所需的任何其他時間時, 您可以將先前儲存至 AnchorStore 的錨點, 從錨點存放區的 IMapView 傳送到您自己的 SpatialAnchors 記憶體內部資料庫。</span><span class="sxs-lookup"><span data-stu-id="72f32-201">When your app resumes, or at any other time necessary for your app's implementaiton, you can restore anchors that were previously saved to the AnchorStore by transferring them from the anchor store's IMapView to your own in-memory database of SpatialAnchors.</span></span>

<span data-ttu-id="72f32-202">若要還原 SpatialAnchorStore 的錨點, 請將您感興趣的每一個都還原至您自己的記憶體中集合。</span><span class="sxs-lookup"><span data-stu-id="72f32-202">To restore anchors from the SpatialAnchorStore, restore each one that you are interested in to your own in-memory collection.</span></span>

<span data-ttu-id="72f32-203">您需要自己的記憶體內部資料庫 SpatialAnchors;將字串與您建立的 SpatialAnchors 建立關聯的一些方式。</span><span class="sxs-lookup"><span data-stu-id="72f32-203">You need your own in-memory database of SpatialAnchors; some way to associate Strings with the SpatialAnchors that you create.</span></span> <span data-ttu-id="72f32-204">在我們的範例程式碼中, 我們選擇使用 Windows:: Foundation:: collection:: IMap 來儲存錨點, 這可讓您輕鬆地針對 SpatialAnchorStore 使用相同的索引鍵和資料值。</span><span class="sxs-lookup"><span data-stu-id="72f32-204">In our sample code, we choose to use a Windows::Foundation::Collections::IMap to store the anchors, which makes it easy to use the same key and data value for the SpatialAnchorStore.</span></span>

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
><span data-ttu-id="72f32-205">可能無法立即找出已還原的錨點。</span><span class="sxs-lookup"><span data-stu-id="72f32-205">An anchor that is restored might not be locatable right away.</span></span> <span data-ttu-id="72f32-206">例如, 它可能是個別房間或不同建築物中的錨點。</span><span class="sxs-lookup"><span data-stu-id="72f32-206">For example, it might be an anchor in a separate room or in a different building altogether.</span></span> <span data-ttu-id="72f32-207">從 AnchorStore 中抓取的錨點應該先測試 locatability, 再加以使用。</span><span class="sxs-lookup"><span data-stu-id="72f32-207">Anchors retrieved from the AnchorStore should be tested for locatability before using them.</span></span>

<br>

>[!NOTE]
><span data-ttu-id="72f32-208">在此範例程式碼中, 我們會從 AnchorStore 中取出所有錨點。</span><span class="sxs-lookup"><span data-stu-id="72f32-208">In this example code, we retrieve all anchors from the AnchorStore.</span></span> <span data-ttu-id="72f32-209">這不是必要條件,您的應用程式也可以挑選特定的錨點子集, 方法是使用對您的執行有意義的字串索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="72f32-209">This is not a requirement; your app could just as well pick and choose a certain subset of anchors by using String key values that are meaningful to your implementation.</span></span>

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

### <a name="clear-the-anchor-store-when-needed"></a><span data-ttu-id="72f32-210">視需要清除錨定存放區</span><span class="sxs-lookup"><span data-stu-id="72f32-210">Clear the anchor store, when needed</span></span>

<span data-ttu-id="72f32-211">有時候, 您需要清除應用程式狀態並寫入新的資料。</span><span class="sxs-lookup"><span data-stu-id="72f32-211">Sometimes, you need to clear app state and write new data.</span></span> <span data-ttu-id="72f32-212">以下是使用[SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)執行此動作的方式。</span><span class="sxs-lookup"><span data-stu-id="72f32-212">Here's how you do that with the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="72f32-213">使用我們的 helper 類別, 幾乎不需要包裝 Clear 函式。</span><span class="sxs-lookup"><span data-stu-id="72f32-213">Using our helper class, it's almost unnecessary to wrap the Clear function.</span></span> <span data-ttu-id="72f32-214">我們選擇在範例執行中這麼做, 因為我們的協助程式類別是擁有 SpatialAnchorStore 實例的責任。</span><span class="sxs-lookup"><span data-stu-id="72f32-214">We choose to do so in our sample implementation, because our helper class is given the responsibility of owning the SpatialAnchorStore instance.</span></span>

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

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a><span data-ttu-id="72f32-215">範例：將錨點座標系統與固定的參考框架座標系統相關聯</span><span class="sxs-lookup"><span data-stu-id="72f32-215">Example: Relating anchor coordinate systems to stationary reference frame coordinate systems</span></span>

<span data-ttu-id="72f32-216">假設您有一個錨點, 而您想要將錨點座標系統中的某個專案與您在大部分其他內容中使用的 SpatialStationaryReferenceFrame 產生關聯。</span><span class="sxs-lookup"><span data-stu-id="72f32-216">Let's say that you have an anchor, and you want to relate something in your anchor's coordinate system to the SpatialStationaryReferenceFrame that you’re already using for most of your other content.</span></span> <span data-ttu-id="72f32-217">您可以使用[TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx)從錨點的座標系統取得轉換, 使其成為固定的參考框架:</span><span class="sxs-lookup"><span data-stu-id="72f32-217">You can use [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) to obtain a transform from the anchor’s coordinate system to that of the stationary reference frame:</span></span>

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

<span data-ttu-id="72f32-218">此程式對您有兩種説明:</span><span class="sxs-lookup"><span data-stu-id="72f32-218">This process is useful to you in two ways:</span></span>
1. <span data-ttu-id="72f32-219">它會告訴您, 這兩個參考框架是否可以彼此瞭解, 以及</span><span class="sxs-lookup"><span data-stu-id="72f32-219">It tells you if the two reference frames can be understood relative to one another, and;</span></span>
2. <span data-ttu-id="72f32-220">若是如此, 它會提供您直接從一個座標系統轉換至另一個座標系統的轉換。</span><span class="sxs-lookup"><span data-stu-id="72f32-220">If so, it provides you a transform to go directly from one coordinate system to the other.</span></span>

<span data-ttu-id="72f32-221">有了這項資訊, 您就能瞭解兩個參考框架之間物件之間的空間關聯性。</span><span class="sxs-lookup"><span data-stu-id="72f32-221">With this information, you have an understanding of the spatial relation between objects between the two reference frames.</span></span>

<span data-ttu-id="72f32-222">針對轉譯, 您通常可以根據物件的原始參考框架或錨點來分組, 以取得更好的結果。</span><span class="sxs-lookup"><span data-stu-id="72f32-222">For rendering, you can often obtain better results by grouping objects according to their original reference frame or anchor.</span></span> <span data-ttu-id="72f32-223">針對每個群組執行個別的繪圖階段。</span><span class="sxs-lookup"><span data-stu-id="72f32-223">Perform a separate drawing pass for each group.</span></span> <span data-ttu-id="72f32-224">針對具有使用相同座標系統一開始所建立之模型轉換的物件, 視圖矩陣會更正確。</span><span class="sxs-lookup"><span data-stu-id="72f32-224">The view matrices are more accurate for objects with model transforms that are created initially using the same coordinate system.</span></span>

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a><span data-ttu-id="72f32-225">使用裝置附加的參考框架建立全息影像</span><span class="sxs-lookup"><span data-stu-id="72f32-225">Create holograms using a device-attached frame of reference</span></span>

<span data-ttu-id="72f32-226">有時候, 您會想要轉譯[保留連接](coordinate-systems.md#attached-frame-of-reference)至裝置位置的全息影像, 例如, 具有偵錯工具資訊的面板, 或當裝置只能判斷其方向, 而不是在中的位置時的參考訊息space.</span><span class="sxs-lookup"><span data-stu-id="72f32-226">There are times when you want to render a hologram that [remains attached](coordinate-systems.md#attached-frame-of-reference) to the device's location, for example a panel with debugging information or an informational message when the device is only able to determine its orientation and not its position in space.</span></span> <span data-ttu-id="72f32-227">為了達成此目的, 我們使用了附加的參考框架。</span><span class="sxs-lookup"><span data-stu-id="72f32-227">To accomplish this, we use an attached frame of reference.</span></span>

<span data-ttu-id="72f32-228">SpatialLocatorAttachedFrameOfReference 類別會定義相對於裝置而非真實世界的座標系統。</span><span class="sxs-lookup"><span data-stu-id="72f32-228">The SpatialLocatorAttachedFrameOfReference class defines coordinate systems which are relative to the device rather than to the real-world.</span></span> <span data-ttu-id="72f32-229">此框架的固定標題相對於使用者的周圍, 其指向建立參考框架時所面臨的方向。</span><span class="sxs-lookup"><span data-stu-id="72f32-229">This frame has a fixed heading relative to the user's surroundings that points in the direction the user was facing when the reference frame was created.</span></span> <span data-ttu-id="72f32-230">從 then 開始, 此參考框架中的所有方向都會相對於該固定標題, 即使使用者旋轉裝置也是如此。</span><span class="sxs-lookup"><span data-stu-id="72f32-230">From then on, all orientations in this frame of reference are relative to that fixed heading, even as the user rotates the device.</span></span>

<span data-ttu-id="72f32-231">若是 HoloLens, 此框架座標系統的原點位於使用者的頭部旋轉中心, 因此其位置不受前端旋轉的影響。</span><span class="sxs-lookup"><span data-stu-id="72f32-231">For HoloLens, the origin of this frame's coordinate system is located at the center of rotation of the user's head, so that its position is not affected by head rotation.</span></span> <span data-ttu-id="72f32-232">您的應用程式可以指定相對於此點的位移, 將全息影像放在使用者之前。</span><span class="sxs-lookup"><span data-stu-id="72f32-232">Your app can specify an offset relative to this point to position holograms in front of the user.</span></span>

<span data-ttu-id="72f32-233">若要取得 SpatialLocatorAttachedFrameOfReference, 請使用 SpatialLocator 類別並呼叫 CreateAttachedFrameOfReferenceAtCurrentHeading。</span><span class="sxs-lookup"><span data-stu-id="72f32-233">To get a SpatialLocatorAttachedFrameOfReference, use the SpatialLocator class and call CreateAttachedFrameOfReferenceAtCurrentHeading.</span></span>

<span data-ttu-id="72f32-234">請注意, 這適用于整個範圍的 Windows Mixed Reality 裝置。</span><span class="sxs-lookup"><span data-stu-id="72f32-234">Note that this applies to the entire range of Windows Mixed Reality devices.</span></span>

### <a name="use-a-reference-frame-attached-to-the-device"></a><span data-ttu-id="72f32-235">使用連接至裝置的參考框架</span><span class="sxs-lookup"><span data-stu-id="72f32-235">Use a reference frame attached to the device</span></span>

<span data-ttu-id="72f32-236">這些章節會討論我們在 Windows 全像應用程式範本中變更的內容, 以使用此 API 啟用裝置附加的參考框架。</span><span class="sxs-lookup"><span data-stu-id="72f32-236">These sections talk about what we changed in the Windows Holographic app template to enable a device-attached frame of reference using this API.</span></span> <span data-ttu-id="72f32-237">請注意, 此「附加」的全息影像會與固定或錨定的全像投影一起使用, 也可能在裝置暫時無法在世界中找到其位置時使用。</span><span class="sxs-lookup"><span data-stu-id="72f32-237">Note that this "attached" hologram will work alongside stationary or anchored holograms, and may also be used when the device is temporarily unable to find its position in the world.</span></span>

<span data-ttu-id="72f32-238">首先, 我們變更了範本來儲存 SpatialLocatorAttachedFrameOfReference, 而不是 SpatialStationaryFrameOfReference:</span><span class="sxs-lookup"><span data-stu-id="72f32-238">First, we changed the template to store a SpatialLocatorAttachedFrameOfReference instead of a SpatialStationaryFrameOfReference:</span></span>

<span data-ttu-id="72f32-239">從**HolographicTagAlongSampleMain**:</span><span class="sxs-lookup"><span data-stu-id="72f32-239">From **HolographicTagAlongSampleMain.h**:</span></span>

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

<span data-ttu-id="72f32-240">從**HolographicTagAlongSampleMain**:</span><span class="sxs-lookup"><span data-stu-id="72f32-240">From **HolographicTagAlongSampleMain.cpp**:</span></span>

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

<span data-ttu-id="72f32-241">在更新期間, 我們現在會從使用框架預測取得的時間戳記取得座標系統。</span><span class="sxs-lookup"><span data-stu-id="72f32-241">During the update, we now obtain the coordinate system at the time stamp obtained from with the frame prediction.</span></span>

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a><span data-ttu-id="72f32-242">取得空間指標姿勢, 並遵循使用者的注視</span><span class="sxs-lookup"><span data-stu-id="72f32-242">Get a spatial pointer pose, and follow the user's Gaze</span></span>

<span data-ttu-id="72f32-243">我們希望我們的範例全息影像會遵循使用者的[注視](gaze.md), 類似于「全像攝影」 shell 如何追蹤使用者的注視。</span><span class="sxs-lookup"><span data-stu-id="72f32-243">We want our example hologram to follow the user's [gaze](gaze.md), similar to how the holographic shell can follow the user's gaze.</span></span> <span data-ttu-id="72f32-244">為此, 我們需要從相同的時間戳記取得 SpatialPointerPose。</span><span class="sxs-lookup"><span data-stu-id="72f32-244">For this, we need to get the SpatialPointerPose from the same time stamp.</span></span>

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

<span data-ttu-id="72f32-245">此 SpatialPointerPose 包含根據[使用者目前的標題](gaze-in-directx.md)來放置全息影像所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="72f32-245">This SpatialPointerPose has the information needed to position the hologram according to the [user's current heading](gaze-in-directx.md).</span></span>

<span data-ttu-id="72f32-246">基於使用者的緩和原因, 我們會使用線性插補 ("lerp") 來平滑位置變更, 使其在一段時間內發生。</span><span class="sxs-lookup"><span data-stu-id="72f32-246">For reasons of user comfort, we use linear interpolation ("lerp") to smooth the change in position such that it occurs over a period of time.</span></span> <span data-ttu-id="72f32-247">對使用者而言, 這比鎖定全息的全像目光更熟悉。</span><span class="sxs-lookup"><span data-stu-id="72f32-247">This is more comfortable for the user than locking the hologram to their gaze.</span></span> <span data-ttu-id="72f32-248">Lerping 標記式的全息影像位置也可讓我們藉由抑制移動來使全息影像變得穩定;如果我們未執行此抑制, 使用者會看到全像投影抖動, 因為通常會被視為使用者的 imperceptible 移動。</span><span class="sxs-lookup"><span data-stu-id="72f32-248">Lerping the tag-along hologram's position also allows us to stabilize the hologram by dampening the movement; if we did not do this dampening, the user would see the hologram jitter because of what are normally considered to be imperceptible movements of the user's head.</span></span>

<span data-ttu-id="72f32-249">從**StationaryQuadRenderer::P ositionhologram**:</span><span class="sxs-lookup"><span data-stu-id="72f32-249">From **StationaryQuadRenderer::PositionHologram**:</span></span>

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
><span data-ttu-id="72f32-250">在 [偵錯工具] 面板的案例中, 您可以選擇將全息影像重新放置到較小的一邊, 讓它不會妨礙您的觀點。</span><span class="sxs-lookup"><span data-stu-id="72f32-250">In the case of a debugging panel, you might choose to reposition the hologram off to the side a little so that it does not obstruct your view.</span></span> <span data-ttu-id="72f32-251">以下是您可能會執行這項操作的範例。</span><span class="sxs-lookup"><span data-stu-id="72f32-251">Here's an example of how you might do that.</span></span>

<span data-ttu-id="72f32-252">針對**StationaryQuadRenderer::P ositionhologram**:</span><span class="sxs-lookup"><span data-stu-id="72f32-252">For **StationaryQuadRenderer::PositionHologram**:</span></span>

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

### <a name="rotate-the-hologram-to-face-the-camera"></a><span data-ttu-id="72f32-253">旋轉全息影像以臉部相機</span><span class="sxs-lookup"><span data-stu-id="72f32-253">Rotate the hologram to face the camera</span></span>

<span data-ttu-id="72f32-254">只是放置全息影像, 在此案例中是一個四個,我們也必須將物件旋轉以面對使用者。</span><span class="sxs-lookup"><span data-stu-id="72f32-254">It is not enough to simply position the hologram, which in this case is a quad; we must also rotate the object to face the user.</span></span> <span data-ttu-id="72f32-255">請注意, 這項旋轉會在世界空間中發生, 因為這種類型的 billboarding 允許全息影像保留在使用者環境中。</span><span class="sxs-lookup"><span data-stu-id="72f32-255">Note that this rotation occurs in world space, because this type of billboarding allows the hologram to remain a part of the user's environment.</span></span> <span data-ttu-id="72f32-256">視圖空間 billboarding 並不熟悉, 因為全像投影會鎖定顯示方向;在這種情況下, 您也必須在左右視圖矩陣之間插補, 才能取得不會干擾身歷聲轉譯的視圖空間佈告欄轉換。</span><span class="sxs-lookup"><span data-stu-id="72f32-256">View-space billboarding is not as comfortable because the hologram becomes locked to the display orientation; in that case, you would also have to interpolate between the left and right view matrices in order to acquire a view-space billboard transform that does not disrupt stereo rendering.</span></span> <span data-ttu-id="72f32-257">在這裡, 我們會旋轉 X 和 Z 軸來面對使用者。</span><span class="sxs-lookup"><span data-stu-id="72f32-257">Here, we rotate on the X and Z axes to face the user.</span></span>

<span data-ttu-id="72f32-258">從**StationaryQuadRenderer:: Update**:</span><span class="sxs-lookup"><span data-stu-id="72f32-258">From **StationaryQuadRenderer::Update**:</span></span>

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

### <a name="render-the-attached-hologram"></a><span data-ttu-id="72f32-259">呈現附加的全息影像</span><span class="sxs-lookup"><span data-stu-id="72f32-259">Render the attached hologram</span></span>

<span data-ttu-id="72f32-260">在此範例中, 我們也選擇在 SpatialLocatorAttachedReferenceFrame 的座標系統中轉譯全息影像, 這是我們放置全息的位置。</span><span class="sxs-lookup"><span data-stu-id="72f32-260">For this example, we also choose to render the hologram in the coordinate system of the SpatialLocatorAttachedReferenceFrame, which is where we positioned the hologram.</span></span> <span data-ttu-id="72f32-261">(如果我們決定使用另一個座標系統轉譯, 則必須從裝置附加的參考框架座標系統取得轉換到該座標系統)。</span><span class="sxs-lookup"><span data-stu-id="72f32-261">(If we had decided to render using another coordinate system, we would need to acquire a transform from the device-attached reference frame's coordinate system to that coordinate system.)</span></span>

<span data-ttu-id="72f32-262">從**HolographicTagAlongSampleMain:: Render**:</span><span class="sxs-lookup"><span data-stu-id="72f32-262">From **HolographicTagAlongSampleMain::Render**:</span></span>

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

<span data-ttu-id="72f32-263">就這麼容易！</span><span class="sxs-lookup"><span data-stu-id="72f32-263">That's it!</span></span> <span data-ttu-id="72f32-264">全像投影現在會在使用者的注視方向前面「調整」為2計量的位置。</span><span class="sxs-lookup"><span data-stu-id="72f32-264">The hologram will now "chase" a position that is 2 meters in front of the user's gaze direction.</span></span>

>[!NOTE]
><span data-ttu-id="72f32-265">這個範例也會載入其他內容, 請參閱 StationaryQuadRenderer。</span><span class="sxs-lookup"><span data-stu-id="72f32-265">This example also loads additional content - see StationaryQuadRenderer.cpp.</span></span>

## <a name="handling-tracking-loss"></a><span data-ttu-id="72f32-266">處理追蹤遺失</span><span class="sxs-lookup"><span data-stu-id="72f32-266">Handling tracking loss</span></span>

<span data-ttu-id="72f32-267">當裝置無法在世界中找到自己時, 應用程式就會遇到「追蹤遺失」的情況。</span><span class="sxs-lookup"><span data-stu-id="72f32-267">When the device cannot locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="72f32-268">Windows Mixed Reality 應用程式應該能夠處理位置追蹤系統的這類中斷。</span><span class="sxs-lookup"><span data-stu-id="72f32-268">Windows Mixed Reality apps should be able to handle such disruptions to the positional tracking system.</span></span> <span data-ttu-id="72f32-269">藉由在預設 SpatialLocator 上使用 LocatabilityChanged 事件, 可以觀察到這些中斷, 並建立回應。</span><span class="sxs-lookup"><span data-stu-id="72f32-269">These disruptions can be observed, and responses created, by using the LocatabilityChanged event on the default SpatialLocator.</span></span>

<span data-ttu-id="72f32-270">From **AppMain:: SetHolographicSpace:**</span><span class="sxs-lookup"><span data-stu-id="72f32-270">From **AppMain::SetHolographicSpace:**</span></span>

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

<span data-ttu-id="72f32-271">當您的應用程式收到 LocatabilityChanged 事件時, 它可以視需要變更行為。</span><span class="sxs-lookup"><span data-stu-id="72f32-271">When your app receives a LocatabilityChanged event, it can change behavior as needed.</span></span> <span data-ttu-id="72f32-272">例如, 在 PositionalTrackingInhibited 狀態中, 您的應用程式可以暫停正常作業, 並轉譯顯示警告訊息的[標記沿著全](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference)像投影。</span><span class="sxs-lookup"><span data-stu-id="72f32-272">For example, in the PositionalTrackingInhibited state, your app can pause normal operation and render a [tag-along hologram](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) that displays a warning message.</span></span>

<span data-ttu-id="72f32-273">Windows 全像攝影應用程式範本隨附已為您建立的 LocatabilityChanged 處理常式。</span><span class="sxs-lookup"><span data-stu-id="72f32-273">The Windows Holographic app template comes with a LocatabilityChanged handler already created for you.</span></span> <span data-ttu-id="72f32-274">根據預設, 當位置追蹤無法使用時, 它會在 [偵錯工具] 主控台中顯示警告。</span><span class="sxs-lookup"><span data-stu-id="72f32-274">By default, it displays a warning in the debug console when positional tracking is unavailable.</span></span> <span data-ttu-id="72f32-275">您可以將程式碼加入此處理程式, 以視需要從您的應用程式提供回應。</span><span class="sxs-lookup"><span data-stu-id="72f32-275">You can add code to this handler to provide a response as needed from your app.</span></span>

<span data-ttu-id="72f32-276">從**AppMain:**</span><span class="sxs-lookup"><span data-stu-id="72f32-276">From **AppMain.cpp:**</span></span>

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

## <a name="spatial-mapping"></a><span data-ttu-id="72f32-277">空間對應</span><span class="sxs-lookup"><span data-stu-id="72f32-277">Spatial mapping</span></span>

<span data-ttu-id="72f32-278">[空間對應](spatial-mapping-in-directx.md)api 會使用座標系統來取得 surface 網格的模型轉換。</span><span class="sxs-lookup"><span data-stu-id="72f32-278">The [spatial mapping](spatial-mapping-in-directx.md) APIs make use of coordinate systems to get model transforms for surface meshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="72f32-279">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72f32-279">See also</span></span>
* [<span data-ttu-id="72f32-280">座標系統</span><span class="sxs-lookup"><span data-stu-id="72f32-280">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="72f32-281">空間錨點</span><span class="sxs-lookup"><span data-stu-id="72f32-281">Spatial anchors</span></span>](spatial-anchors.md)
* <span data-ttu-id="72f32-282"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="72f32-282"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* [<span data-ttu-id="72f32-283">DirectX 中的頭部和眼睛目光</span><span class="sxs-lookup"><span data-stu-id="72f32-283">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="72f32-284">DirectX 中的手部和運動控制器</span><span class="sxs-lookup"><span data-stu-id="72f32-284">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="72f32-285">DirectX 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="72f32-285">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)
