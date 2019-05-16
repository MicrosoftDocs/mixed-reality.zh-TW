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
# <a name="coordinate-systems-in-directx"></a><span data-ttu-id="67f1d-104">DirectX 中的座標系統</span><span class="sxs-lookup"><span data-stu-id="67f1d-104">Coordinate systems in DirectX</span></span>

<span data-ttu-id="67f1d-105">[座標系統](coordinate-systems.md)形成基礎的 Windows Mixed Reality Api 所提供的空間的了解。</span><span class="sxs-lookup"><span data-stu-id="67f1d-105">[Coordinate systems](coordinate-systems.md) form the basis for spatial understanding offered by Windows Mixed Reality APIs.</span></span>

<span data-ttu-id="67f1d-106">現今的插入擴充槽 VR 或單一空間 VR 裝置建立一個主要的座標系統表示其追蹤的空間。</span><span class="sxs-lookup"><span data-stu-id="67f1d-106">Today's seated VR or single-room VR devices establish one primary coordinate system to represent their tracked space.</span></span> <span data-ttu-id="67f1d-107">Windows Mixed Reality 裝置例如 HoloLens 專為在整個大型未定義的環境，探索及了解其周圍環境中，為使用者的裝置將逐步引導周圍。</span><span class="sxs-lookup"><span data-stu-id="67f1d-107">Windows Mixed Reality devices such as HoloLens are designed to be used throughout large undefined environments, with the device discovering and learning about its surroundings as the user walks around.</span></span> <span data-ttu-id="67f1d-108">這可讓裝置，以配合持續改進使用者的聊天室，但結果中，將其關聯性至另一部應用程式的存留期內的座標系統的相關知識。</span><span class="sxs-lookup"><span data-stu-id="67f1d-108">This allows the device to adapt to continually-improving knowledge about the user's rooms, but results in coordinate systems that will change their relationship to one another through the lifetime of the app.</span></span> <span data-ttu-id="67f1d-109">Windows Mixed Reality 支援廣泛的裝置，範圍從安置的沈浸式耳機到全球附加的參考畫面格。</span><span class="sxs-lookup"><span data-stu-id="67f1d-109">Windows Mixed Reality supports a wide spectrum of devices, ranging from seated immersive headsets through world-attached reference frames.</span></span>

>[!NOTE]
><span data-ttu-id="67f1d-110">目前在這篇文章中的程式碼片段示範如何使用C++/CX 而不是 C + + 17 相容C++中所使用的 /WinRT [ C++全像攝影版的專案範本](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="67f1d-110">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="67f1d-111">概念是相等的C++/WinRT 專案，但您必須將轉譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="67f1d-111">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="spatial-coordinate-systems-in-windows"></a><span data-ttu-id="67f1d-112">在 Windows 中的空間座標系統</span><span class="sxs-lookup"><span data-stu-id="67f1d-112">Spatial coordinate systems in Windows</span></span>

<span data-ttu-id="67f1d-113">用來在 Windows 中的真實世界座標系統的理解的核心型別是<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>。</span><span class="sxs-lookup"><span data-stu-id="67f1d-113">The core type used to reason about real-world coordinate systems in Windows is the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>.</span></span> <span data-ttu-id="67f1d-114">此類型的執行個體代表任意的座標系統，並提供方法來取得您可以使用兩個座標系統，而不了解每個詳細資料之間轉換的轉換矩陣。</span><span class="sxs-lookup"><span data-stu-id="67f1d-114">An instance of this type represents an arbitrary coordinate system and provides a method to get a transformation matrix that you can use to transform between two coordinate systems without understanding the details of each.</span></span>

<span data-ttu-id="67f1d-115">傳回表示為點、 光線或在使用者的恍神的磁碟區的空間資訊的方法會接受 SpatialCoordinateSystem 參數讓您決定它是最適合這些座標來傳回座標系統。</span><span class="sxs-lookup"><span data-stu-id="67f1d-115">Methods that return spatial information, represented as points, rays, or volumes in the user's surroundings, will accept a SpatialCoordinateSystem parameter to let you decide the coordinate system in which it's most useful for those coordinates to be returned.</span></span> <span data-ttu-id="67f1d-116">這些座標的單位一律會以公尺為單位。</span><span class="sxs-lookup"><span data-stu-id="67f1d-116">The units for these coordinates will always be in meters.</span></span>

<span data-ttu-id="67f1d-117">SpatialCoordinateSystem 具有動態的關聯性，與其他的座標系統，包括代表裝置的位置。</span><span class="sxs-lookup"><span data-stu-id="67f1d-117">A SpatialCoordinateSystem has a dynamic relationship with other coordinate systems, including those that represent the device's position.</span></span> <span data-ttu-id="67f1d-118">在任何時間點，可能找不到某些座標系統並不會針對其他裝置。</span><span class="sxs-lookup"><span data-stu-id="67f1d-118">At any point in time, the device may be able to locate some coordinate systems and not others.</span></span> <span data-ttu-id="67f1d-119">對於大多數的座標系統中，您的應用程式必須準備好處理一段期間它們找不到的時間。</span><span class="sxs-lookup"><span data-stu-id="67f1d-119">For most coordinate systems, your app must be ready to handle periods of time during which they cannot be located.</span></span>

<span data-ttu-id="67f1d-120">您的應用程式應該不會直接 SpatialCoordinateSystems 建立-而是它們應該取用透過 Perception Api。</span><span class="sxs-lookup"><span data-stu-id="67f1d-120">Your application should not create SpatialCoordinateSystems directly - rather they should be consumed via the Perception APIs.</span></span> <span data-ttu-id="67f1d-121">有三個主要的來源座標系統在 Perception Api 中，每個所述的概念的地圖[座標系統](coordinate-systems.md)頁面：</span><span class="sxs-lookup"><span data-stu-id="67f1d-121">There are three primary sources of coordinate systems in the Perception APIs, each of which map to a concept described on the [Coordinate systems](coordinate-systems.md) page:</span></span>
* <span data-ttu-id="67f1d-122">若要取得靜態參考座標系，請建立<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a>或取得目前<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>。</span><span class="sxs-lookup"><span data-stu-id="67f1d-122">To get a stationary frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> or obtain one from the current <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>.</span></span>
* <span data-ttu-id="67f1d-123">若要取得空間的錨點，請建立<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>。</span><span class="sxs-lookup"><span data-stu-id="67f1d-123">To get a spatial anchor, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.</span></span>
* <span data-ttu-id="67f1d-124">若要取得附加的畫面格的參考，建立<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>。</span><span class="sxs-lookup"><span data-stu-id="67f1d-124">To get an attached frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.</span></span>

<span data-ttu-id="67f1d-125">所有這些物件所傳回的座標系統是右手性，以 + y、 + x 右邊和 + z 回溯。</span><span class="sxs-lookup"><span data-stu-id="67f1d-125">All of the coordinate systems returned by these objects are right-handed, with +y up, +x to the right and +z backwards.</span></span> <span data-ttu-id="67f1d-126">您可以記住正 z 軸點上按一下滑鼠正 x 方向指向您的左邊或右邊的手指 curling 它們到正 y 方向的方向。</span><span class="sxs-lookup"><span data-stu-id="67f1d-126">You can remember which direction the positive z-axis points by pointing the fingers of either your left or right hand in the positive x direction and curling them into the positive y direction.</span></span> <span data-ttu-id="67f1d-127">您拇指所指的方向，不論是指向您或指向您的反方向，即是該座標系統正 z 軸所指的方向。</span><span class="sxs-lookup"><span data-stu-id="67f1d-127">The direction your thumb points, either toward or away from you, is the direction that the positive z-axis points for that coordinate system.</span></span> <span data-ttu-id="67f1d-128">下圖顯示這兩個座標系統。</span><span class="sxs-lookup"><span data-stu-id="67f1d-128">The following illustration shows these two coordinate systems.</span></span>

<span data-ttu-id="67f1d-129">![左側和右側的座標系統](images/left-hand-right-hand.gif)</span><span class="sxs-lookup"><span data-stu-id="67f1d-129">![Left-hand and right-hand coordinate systems](images/left-hand-right-hand.gif)</span></span><br>
<span data-ttu-id="67f1d-130">*左側和右側的座標系統*</span><span class="sxs-lookup"><span data-stu-id="67f1d-130">*Left-hand and right-hand coordinate systems*</span></span>

<span data-ttu-id="67f1d-131">若要啟動到 SpatialCoordinateSystem HoloLens 位置為基礎，使用<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>類別來建立任一附加或靜態參考座標系，如下列各節中所述。</span><span class="sxs-lookup"><span data-stu-id="67f1d-131">To bootstrap into a SpatialCoordinateSystem based on the position of a HoloLens, use the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> class to create either an attached or stationary frame of reference, as described in the sections below.</span></span>

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a><span data-ttu-id="67f1d-132">全像投影置於世界的使用空間的階段</span><span class="sxs-lookup"><span data-stu-id="67f1d-132">Place holograms in the world using a spatial stage</span></span>

<span data-ttu-id="67f1d-133">使用靜態存取座標系統的不透明的 Windows Mixed Reality 沈浸式耳機<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a>屬性。</span><span class="sxs-lookup"><span data-stu-id="67f1d-133">The coordinate system for opaque Windows Mixed Reality immersive headsets is accessed using the static <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a> property.</span></span> <span data-ttu-id="67f1d-134">此 API 提供的行動裝置、 播放程式是否四處跑的座標系統的相關資訊是否置於播放程式或行動裝置、 安全區域的界限，並指出耳機是方向性。</span><span class="sxs-lookup"><span data-stu-id="67f1d-134">This API provides a coordinate system, information about whether the player is seated or mobile, the boundary of a safe area for walking around if the player is mobile, and an indication of whether or not the headset is directional.</span></span> <span data-ttu-id="67f1d-135">另外還有空間階段更新的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="67f1d-135">There is also an event handler for updates to the spatial stage.</span></span>

<span data-ttu-id="67f1d-136">首先，我們會取得空間的階段，並訂閱更新：</span><span class="sxs-lookup"><span data-stu-id="67f1d-136">First, we get the spatial stage and subscribe for updates to it:</span></span> 

<span data-ttu-id="67f1d-137">程式碼**空間階段初始化**</span><span class="sxs-lookup"><span data-stu-id="67f1d-137">Code for **Spatial stage initialization**</span></span>

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

<span data-ttu-id="67f1d-138">在 OnCurrentChanged 方法中，您的應用程式應該檢查空間的階段，並據以更新玩家體驗。</span><span class="sxs-lookup"><span data-stu-id="67f1d-138">In the OnCurrentChanged method, your app should inspect the spatial stage and update the player experience accordingly.</span></span> <span data-ttu-id="67f1d-139">在此範例中，我們提供階段界限，以及使用者和檢視階段的範圍和範圍的移動屬性所指定的起始位置的視覺的效果。</span><span class="sxs-lookup"><span data-stu-id="67f1d-139">In this example, we provide a visualization of the stage boundary, as well as the start position specified by the user and the stage's range of view and range of movement properties.</span></span> <span data-ttu-id="67f1d-140">我們也改為使用自己 「 定態的座標系統中，無法提供階段時。</span><span class="sxs-lookup"><span data-stu-id="67f1d-140">We also fall back to our own stationary coordinate system, when a stage cannot be provided.</span></span>


<span data-ttu-id="67f1d-141">程式碼**空間階段更新**</span><span class="sxs-lookup"><span data-stu-id="67f1d-141">Code for **Spatial stage update**</span></span>

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

<span data-ttu-id="67f1d-142">以順時針順序提供的定義階段界限的頂點集合。</span><span class="sxs-lookup"><span data-stu-id="67f1d-142">The set of vertices that define the stage boundary are provided in clockwise order.</span></span> <span data-ttu-id="67f1d-143">Windows Mixed Reality shell 範圍的界限時繪製使用者接近它;您可能想要供您自己 triangularize 查核的區域。</span><span class="sxs-lookup"><span data-stu-id="67f1d-143">The Windows Mixed Reality shell draws a fence at the boundary when the user approaches it; you may wish to triangularize the walkable area for your own purposes.</span></span> <span data-ttu-id="67f1d-144">可以使用下列演算法，以 triangularize 階段。</span><span class="sxs-lookup"><span data-stu-id="67f1d-144">The following algorithm can be used to triangularize the stage.</span></span>


<span data-ttu-id="67f1d-145">程式碼**空間階段 triangularization**</span><span class="sxs-lookup"><span data-stu-id="67f1d-145">Code for **Spatial stage triangularization**</span></span>

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

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a><span data-ttu-id="67f1d-146">使用靜態參考座標系世界中放置全像投影</span><span class="sxs-lookup"><span data-stu-id="67f1d-146">Place holograms in the world using a stationary frame of reference</span></span>

<span data-ttu-id="67f1d-147">[SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx)類別表示的框架參考該[維持不動](coordinate-systems.md#stationary-frame-of-reference)相對於使用者的使用者身分的周圍環境移動。</span><span class="sxs-lookup"><span data-stu-id="67f1d-147">The [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) class represents a frame of reference that [remains stationary](coordinate-systems.md#stationary-frame-of-reference) relative to the user's surroundings as the user moves around.</span></span> <span data-ttu-id="67f1d-148">此參考架構會優先選擇維持穩定裝置附近的座標。</span><span class="sxs-lookup"><span data-stu-id="67f1d-148">This frame of reference prioritizes keeping coordinates stable near the device.</span></span> <span data-ttu-id="67f1d-149">SpatialStationaryFrameOfReference 一個主要用法是做為基礎的全局座標系統中的轉譯引擎，呈現全像投影時。</span><span class="sxs-lookup"><span data-stu-id="67f1d-149">One key use of a SpatialStationaryFrameOfReference is to act as the underlying world coordinate system within a rendering engine when rendering holograms.</span></span>

<span data-ttu-id="67f1d-150">若要取得 SpatialStationaryFrameOfReference，請使用[SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx)類別，並呼叫[CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx)。</span><span class="sxs-lookup"><span data-stu-id="67f1d-150">To get a SpatialStationaryFrameOfReference, use the [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) class and call [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).</span></span>

<span data-ttu-id="67f1d-151">從 Windows 全像攝影版的應用程式範本程式碼：</span><span class="sxs-lookup"><span data-stu-id="67f1d-151">From the Windows Holographic app template code:</span></span>

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* <span data-ttu-id="67f1d-152">靜態參考框架專為提供的自動調整的位置，相對於整體的空間。</span><span class="sxs-lookup"><span data-stu-id="67f1d-152">Stationary reference frames are designed to provide a best-fit position relative to the overall space.</span></span> <span data-ttu-id="67f1d-153">在該參考框架內的個別位置都可以稍微漂移。</span><span class="sxs-lookup"><span data-stu-id="67f1d-153">Individual positions within that reference frame are allowed to drift slightly.</span></span> <span data-ttu-id="67f1d-154">這是正常現象，因為裝置知道更多的環境。</span><span class="sxs-lookup"><span data-stu-id="67f1d-154">This is normal as the device learns more about the environment.</span></span>
* <span data-ttu-id="67f1d-155">需要個別全像投影的精確位置時，SpatialAnchor 應該用來錨定在個別的全像真實世界中的位置-例如，點使用者表示特別感興趣的。</span><span class="sxs-lookup"><span data-stu-id="67f1d-155">When precise placement of individual holograms is required, a SpatialAnchor should be used to anchor the individual hologram to a position in the real world - for example, a point the user indicates to be of special interest.</span></span> <span data-ttu-id="67f1d-156">錨點位置不漂移，但您可以更正;錨點將會使用已更正之後更正發生在下一個畫面格開始的位置。</span><span class="sxs-lookup"><span data-stu-id="67f1d-156">Anchor positions do not drift, but can be corrected; the anchor will use the corrected position starting in the next frame after the correction has occurred.</span></span>

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a><span data-ttu-id="67f1d-157">全像投影置於使用空間的錨點的世界</span><span class="sxs-lookup"><span data-stu-id="67f1d-157">Place holograms in the world using spatial anchors</span></span>

<span data-ttu-id="67f1d-158">[空間的錨點](coordinate-systems.md#spatial-anchors)很適合用來將全像投影放在真實世界中的特定位置，與系統確保錨點保留在原地經過一段時間。</span><span class="sxs-lookup"><span data-stu-id="67f1d-158">[Spatial anchors](coordinate-systems.md#spatial-anchors) are a great way to place holograms at a specific place in the real world, with the system ensuring the anchor stays in place over time.</span></span> <span data-ttu-id="67f1d-159">本主題說明如何建立和使用錨點，以及如何使用錨點的資料。</span><span class="sxs-lookup"><span data-stu-id="67f1d-159">This topic explains how to create and use an anchor, and how to work with anchor data.</span></span>

<span data-ttu-id="67f1d-160">您可以在任何位置和方向 SpatialCoordinateSystem 內您所選擇的建立 SpatialAnchor。</span><span class="sxs-lookup"><span data-stu-id="67f1d-160">You can create a SpatialAnchor at any position and orientation within the SpatialCoordinateSystem of your choosing.</span></span> <span data-ttu-id="67f1d-161">裝置必須能夠找到該座標系統，此時，，而且系統必須未達到其限制的空間的錨點。</span><span class="sxs-lookup"><span data-stu-id="67f1d-161">The device must be able to locate that coordinate system at the moment, and the system must not have reached its limit of spatial anchors.</span></span>

<span data-ttu-id="67f1d-162">定義好之後，SpatialAnchor 座標系統將持續調整，以保留的精確位置和方向其初始位置。</span><span class="sxs-lookup"><span data-stu-id="67f1d-162">Once defined, the coordinate system of a SpatialAnchor adjusts continually to retain the precise position and orientation of its initial location.</span></span> <span data-ttu-id="67f1d-163">此 SpatialAnchor 接著可用來呈現全像投影會出現在使用者的恍神該確切的位置固定。</span><span class="sxs-lookup"><span data-stu-id="67f1d-163">You can then use this SpatialAnchor to render holograms that will appear fixed in the user's surroundings at that exact location.</span></span>

<span data-ttu-id="67f1d-164">做為錨點增加從距離更被明顯的就地保留錨點的調整效果。</span><span class="sxs-lookup"><span data-stu-id="67f1d-164">The effects of the adjustments that keep the anchor in place are magnified as distance from the anchor increases.</span></span> <span data-ttu-id="67f1d-165">因此，您應該避免超過約 3 個計量會錨定的原始的錨點相對的呈現內容。</span><span class="sxs-lookup"><span data-stu-id="67f1d-165">Therefore, you should avoid rendering content relative to an anchor that is more than about 3 meters from that anchor's origin.</span></span>

<span data-ttu-id="67f1d-166">[CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx)屬性會取得一個座標系統，可讓您放置相對於錨點，內容加/減速套用時裝置調整錨點的確切位置。</span><span class="sxs-lookup"><span data-stu-id="67f1d-166">The [CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) property gets a coordinate system that lets you place content relative to the anchor, with easing applied when the device adjusts the anchor's precise location.</span></span>

<span data-ttu-id="67f1d-167">使用[RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx)屬性和對應[RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx)自行管理這些調整的事件。</span><span class="sxs-lookup"><span data-stu-id="67f1d-167">Use the [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) property and the corresponding [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) event to manage these adjustments yourself.</span></span>

### <a name="persist-and-share-spatial-anchors"></a><span data-ttu-id="67f1d-168">保存和共用空間的錨點</span><span class="sxs-lookup"><span data-stu-id="67f1d-168">Persist and share spatial anchors</span></span>

<span data-ttu-id="67f1d-169">您可以保存在本機使用 SpatialAnchor [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)類別，然後將它取得上一步在未來的應用程式工作階段中相同的 HoloLens 裝置上。</span><span class="sxs-lookup"><span data-stu-id="67f1d-169">You can persist a SpatialAnchor locally using the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) class and then get it back in a future app session on the same HoloLens device.</span></span>

<span data-ttu-id="67f1d-170">藉由使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間的錨點</a>，您可以從本機的 SpatialAnchor，然後會跨多個 HoloLens、 iOS 和 Android 裝置可以找出您的應用程式建立持久的雲端錨點。</span><span class="sxs-lookup"><span data-stu-id="67f1d-170">By using <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>, you can create a durable cloud anchor from a local SpatialAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="67f1d-171">藉由跨多個裝置共用常見的空間錨點，每位使用者都可以看到相對於該錨點相同的實體位置中呈現內容。</span><span class="sxs-lookup"><span data-stu-id="67f1d-171">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="67f1d-172">這可讓您即時分享經驗。</span><span class="sxs-lookup"><span data-stu-id="67f1d-172">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="67f1d-173">您也可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間的錨點</a>非同步闀持續性跨 HoloLens、 iOS 和 Android 裝置。</span><span class="sxs-lookup"><span data-stu-id="67f1d-173">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="67f1d-174">藉由共用持久的雲端空間錨點，多個裝置可以觀察相同的保存全像經過一段時間，即使這些裝置不存在一起在相同的時間。</span><span class="sxs-lookup"><span data-stu-id="67f1d-174">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="67f1d-175">若要開始建置 HoloLens 應用程式中的共用的體驗，試用 5 分鐘<a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">空間錨點 HoloLens Azure 快速入門</a>。</span><span class="sxs-lookup"><span data-stu-id="67f1d-175">To get started building shared experiences in your HoloLens app, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchors HoloLens quickstart</a>.</span></span>

<span data-ttu-id="67f1d-176">一旦您啟動並執行 Azure 空間的起點，您可以接著<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">建立和 HoloLens 上尋找起點</a>。</span><span class="sxs-lookup"><span data-stu-id="67f1d-176">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">create and locate anchors on HoloLens</a>.</span></span>  <span data-ttu-id="67f1d-177">皆有逐步解說<a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android 和 iOS</a> ，讓您能夠共用相同的錨點，在所有裝置上。</span><span class="sxs-lookup"><span data-stu-id="67f1d-177">Walkthroughs are available for <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android and iOS</a> as well, enabling you to share the same anchors on all devices.</span></span>

### <a name="create-spatialanchors-for-holographic-content"></a><span data-ttu-id="67f1d-178">建立 SpatialAnchors 全像攝影版的內容</span><span class="sxs-lookup"><span data-stu-id="67f1d-178">Create SpatialAnchors for holographic content</span></span>

<span data-ttu-id="67f1d-179">此程式碼範例中，我們修改 Windows 全像攝影版的應用程式範本來建立錨定的時機**Pressed**偵測到筆勢時。</span><span class="sxs-lookup"><span data-stu-id="67f1d-179">For this code sample, we modified the Windows Holographic app template to create anchors when the **Pressed** gesture is detected.</span></span> <span data-ttu-id="67f1d-180">呈現階段期間，該 cube 然後會放在錨點。</span><span class="sxs-lookup"><span data-stu-id="67f1d-180">The cube is then placed at the anchor during the render pass.</span></span>

<span data-ttu-id="67f1d-181">協助程式類別支援多個錨點，因為我們可以將多個 cube，因為我們想使用此程式碼範例 ！</span><span class="sxs-lookup"><span data-stu-id="67f1d-181">Since multiple anchors are supported by the helper class, we can place as many cubes as we want using this code sample!</span></span>

<span data-ttu-id="67f1d-182">附註的錨點識別碼是您在您的應用程式中控制的項目。</span><span class="sxs-lookup"><span data-stu-id="67f1d-182">Note that the IDs for anchors are something you control in your app.</span></span> <span data-ttu-id="67f1d-183">在此範例中，我們已建立為循序的目前儲存的錨點的應用程式的集合中的錨點數目為基礎的命名配置。</span><span class="sxs-lookup"><span data-stu-id="67f1d-183">In this example, we have created a naming scheme that is sequential based on the number of anchors currently stored in the app's collection of anchors.</span></span>

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

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a><span data-ttu-id="67f1d-184">以非同步方式載入和快取，SpatialAnchorStore</span><span class="sxs-lookup"><span data-stu-id="67f1d-184">Asynchronously load, and cache, the SpatialAnchorStore</span></span>

<span data-ttu-id="67f1d-185">我們來看看如何撰寫 SampleSpatialAnchorHelper 類別，可協助處理此持續性，包括：</span><span class="sxs-lookup"><span data-stu-id="67f1d-185">Let's see how to write a SampleSpatialAnchorHelper class that helps handle this persistence, including:</span></span>
* <span data-ttu-id="67f1d-186">將儲存於記憶體中的錨點的集合，編製索引的 platform:: string 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="67f1d-186">Storing a collection of in-memory anchors, indexed by a Platform::String key.</span></span>
* <span data-ttu-id="67f1d-187">從系統的 SpatialAnchorStore 中載入的錨點，這是與分開本機記憶體中的集合。</span><span class="sxs-lookup"><span data-stu-id="67f1d-187">Loading anchors from the system's SpatialAnchorStore, which is kept separate from the local in-memory collection.</span></span>
* <span data-ttu-id="67f1d-188">若要這樣做選擇的應用程式時，請將本機記憶體中集合的錨點儲存到 SpatialAnchorStore 」。</span><span class="sxs-lookup"><span data-stu-id="67f1d-188">Saving the local in-memory collection of anchors to the SpatialAnchorStore when the app chooses to do so.</span></span>

<span data-ttu-id="67f1d-189">以下是如何儲存[SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx)中的物件[SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)。</span><span class="sxs-lookup"><span data-stu-id="67f1d-189">Here's how to save [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) objects in the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="67f1d-190">當類別已啟動時，我們要求 SpatialAnchorStore 以非同步的方式。</span><span class="sxs-lookup"><span data-stu-id="67f1d-190">When the class starts up, we request the SpatialAnchorStore asynchronously.</span></span> <span data-ttu-id="67f1d-191">這牽涉到系統 I/O API 載入錨點存放區中，以及此 API 使非同步 I/O 未封鎖。</span><span class="sxs-lookup"><span data-stu-id="67f1d-191">This involves system I/O as the API loads the anchor store, and this API is made asynchronous so that the I/O is non-blocking.</span></span>

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

<span data-ttu-id="67f1d-192">您將會提供您可用來儲存錨點 SpatialAnchorStore。</span><span class="sxs-lookup"><span data-stu-id="67f1d-192">You will be given a SpatialAnchorStore that you can use to save the anchors.</span></span> <span data-ttu-id="67f1d-193">這是將是字串，與 SpatialAnchors 資料值的索引鍵值 Imapview<k。</span><span class="sxs-lookup"><span data-stu-id="67f1d-193">This is an IMapView that associates key values that are Strings, with data values that are SpatialAnchors.</span></span> <span data-ttu-id="67f1d-194">在我們的範例程式碼，我們將這儲存在私用類別成員變數，可透過我們的協助程式類別的公用函式存取。</span><span class="sxs-lookup"><span data-stu-id="67f1d-194">In our sample code, we store this in a private class member variable that is accessible through a public function of our helper class.</span></span>

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
><span data-ttu-id="67f1d-195">別忘了連結暫止/繼續事件，來儲存及載入錨點存放區。</span><span class="sxs-lookup"><span data-stu-id="67f1d-195">Don't forget to hook up the suspend/resume events to save and load the anchor store.</span></span>

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

### <a name="save-content-to-the-anchor-store"></a><span data-ttu-id="67f1d-196">將內容儲存至錨點存放區</span><span class="sxs-lookup"><span data-stu-id="67f1d-196">Save content to the anchor store</span></span>

<span data-ttu-id="67f1d-197">當系統暫止您的應用程式時，您需要儲存空間的錨點到錨點存放區。</span><span class="sxs-lookup"><span data-stu-id="67f1d-197">When the system suspends your app, you need to save your spatial anchors to the anchor store.</span></span> <span data-ttu-id="67f1d-198">當您發現必須存在才能讓您的應用程式實作，您也可以選擇在其他時候，儲存到錨點存放區的錨點。</span><span class="sxs-lookup"><span data-stu-id="67f1d-198">You may also choose to save anchors to the anchor store at other times, as you find to be necessary for your app's implementation.</span></span>

<span data-ttu-id="67f1d-199">當您準備好要試著以 SpatialAnchorStore 儲存於記憶體中的錨點時，您可以您的集合執行迴圈，然後再次嘗試儲存每一個。</span><span class="sxs-lookup"><span data-stu-id="67f1d-199">When you're ready to try saving the in-memory anchors to the SpatialAnchorStore, you can loop through your collection and try to save each one.</span></span>

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

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a><span data-ttu-id="67f1d-200">應用程式會繼續執行時，從錨點存放區載入內容</span><span class="sxs-lookup"><span data-stu-id="67f1d-200">Load content from the anchor store when the app resumes</span></span>

<span data-ttu-id="67f1d-201">當您的應用程式會繼續時，或在您的應用程式 implementaiton 」 所需的任何其他時間，您可以還原已藉由將它們從錨點存放區的 Imapview<k 傳送到您自己的記憶體中資料庫的 SpatialAnchors 先前儲存至 AnchorStore 的錨點。</span><span class="sxs-lookup"><span data-stu-id="67f1d-201">When your app resumes, or at any other time necessary for your app's implementaiton, you can restore anchors that were previously saved to the AnchorStore by transferring them from the anchor store's IMapView to your own in-memory database of SpatialAnchors.</span></span>

<span data-ttu-id="67f1d-202">若要從 SpatialAnchorStore 還原錨點，還原有興趣加入記憶體中集合的每個。</span><span class="sxs-lookup"><span data-stu-id="67f1d-202">To restore anchors from the SpatialAnchorStore, restore each one that you are interested in to your own in-memory collection.</span></span>

<span data-ttu-id="67f1d-203">您需要自己的記憶體中資料庫的 SpatialAnchors;將字串與您建立 SpatialAnchors 某種方式。</span><span class="sxs-lookup"><span data-stu-id="67f1d-203">You need your own in-memory database of SpatialAnchors; some way to associate Strings with the SpatialAnchors that you create.</span></span> <span data-ttu-id="67f1d-204">在我們的範例程式碼，我們選擇使用 Windows::Foundation::Collections::IMap 儲存錨點，讓您輕鬆地針對 SpatialAnchorStore 使用相同的索引鍵和資料值。</span><span class="sxs-lookup"><span data-stu-id="67f1d-204">In our sample code, we choose to use a Windows::Foundation::Collections::IMap to store the anchors, which makes it easy to use the same key and data value for the SpatialAnchorStore.</span></span>

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
><span data-ttu-id="67f1d-205">還原的錨點可能無法之外的可尋獲立即。</span><span class="sxs-lookup"><span data-stu-id="67f1d-205">An anchor that is restored might not be locatable right away.</span></span> <span data-ttu-id="67f1d-206">比方說，它可能在不同房間內或不同建置完全的錨點。</span><span class="sxs-lookup"><span data-stu-id="67f1d-206">For example, it might be an anchor in a separate room or in a different building altogether.</span></span> <span data-ttu-id="67f1d-207">Locatability 應該經過 AnchorStore 從擷取的錨點才能使用。</span><span class="sxs-lookup"><span data-stu-id="67f1d-207">Anchors retrieved from the AnchorStore should be tested for locatability before using them.</span></span>

<br>

>[!NOTE]
><span data-ttu-id="67f1d-208">在此範例程式碼中，我們會從 AnchorStore 擷取所有的錨點。</span><span class="sxs-lookup"><span data-stu-id="67f1d-208">In this example code, we retrieve all anchors from the AnchorStore.</span></span> <span data-ttu-id="67f1d-209">這不是需求;您的應用程式可能也挑選起點子集使用對您的實作有意義的字串索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="67f1d-209">This is not a requirement; your app could just as well pick and choose a certain subset of anchors by using String key values that are meaningful to your implementation.</span></span>

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

### <a name="clear-the-anchor-store-when-needed"></a><span data-ttu-id="67f1d-210">需要時清除錨點存放區</span><span class="sxs-lookup"><span data-stu-id="67f1d-210">Clear the anchor store, when needed</span></span>

<span data-ttu-id="67f1d-211">有時候，您要清除應用程式狀態，並寫入新的資料。</span><span class="sxs-lookup"><span data-stu-id="67f1d-211">Sometimes, you need to clear app state and write new data.</span></span> <span data-ttu-id="67f1d-212">以下是您如何執行動作，使用[SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)。</span><span class="sxs-lookup"><span data-stu-id="67f1d-212">Here's how you do that with the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="67f1d-213">使用我們的 helper 類別，就幾乎不需要將包裝的清楚的函式。</span><span class="sxs-lookup"><span data-stu-id="67f1d-213">Using our helper class, it's almost unnecessary to wrap the Clear function.</span></span> <span data-ttu-id="67f1d-214">我們選擇這麼做在我們的範例實作，因為我們的協助程式類別提供擁有 SpatialAnchorStore 執行個體的責任。</span><span class="sxs-lookup"><span data-stu-id="67f1d-214">We choose to do so in our sample implementation, because our helper class is given the responsibility of owning the SpatialAnchorStore instance.</span></span>

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

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a><span data-ttu-id="67f1d-215">範例：與靜態參考畫面格的座標系統中的錨點的座標系統</span><span class="sxs-lookup"><span data-stu-id="67f1d-215">Example: Relating anchor coordinate systems to stationary reference frame coordinate systems</span></span>

<span data-ttu-id="67f1d-216">假設您有錨點，而您想要與您已在使用適用於大部分的其他內容 SpatialStationaryReferenceFrame 錨點的座標系統中的項目。</span><span class="sxs-lookup"><span data-stu-id="67f1d-216">Let's say that you have an anchor, and you want to relate something in your anchor's coordinate system to the SpatialStationaryReferenceFrame that you’re already using for most of your other content.</span></span> <span data-ttu-id="67f1d-217">您可以使用[TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx)以取得轉換的錨點的座標系統的靜態參考框架：</span><span class="sxs-lookup"><span data-stu-id="67f1d-217">You can use [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) to obtain a transform from the anchor’s coordinate system to that of the stationary reference frame:</span></span>

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

<span data-ttu-id="67f1d-218">此程序是適合您有兩種：</span><span class="sxs-lookup"><span data-stu-id="67f1d-218">This process is useful to you in two ways:</span></span>
1. <span data-ttu-id="67f1d-219">它會告訴您如果兩個參考框架相對於另一個，就可以了解和;</span><span class="sxs-lookup"><span data-stu-id="67f1d-219">It tells you if the two reference frames can be understood relative to one another, and;</span></span>
2. <span data-ttu-id="67f1d-220">如果是的話，它提供您直接從一個座標系統移至其他轉換。</span><span class="sxs-lookup"><span data-stu-id="67f1d-220">If so, it provides you a transform to go directly from one coordinate system to the other.</span></span>

<span data-ttu-id="67f1d-221">利用此資訊，您會了解空間之間的關聯性的兩個參考畫面格之間的物件。</span><span class="sxs-lookup"><span data-stu-id="67f1d-221">With this information, you have an understanding of the spatial relation between objects between the two reference frames.</span></span>

<span data-ttu-id="67f1d-222">進行轉譯中,，您通常可以藉由群組根據其原始的參考框架 」 或 「 錨點的物件，以取得更好的結果。</span><span class="sxs-lookup"><span data-stu-id="67f1d-222">For rendering, you can often obtain better results by grouping objects according to their original reference frame or anchor.</span></span> <span data-ttu-id="67f1d-223">每個群組執行獨立的繪圖行程。</span><span class="sxs-lookup"><span data-stu-id="67f1d-223">Perform a separate drawing pass for each group.</span></span> <span data-ttu-id="67f1d-224">檢視矩陣會變得更精確物件模型轉換會建立一開始使用相同的座標系統。</span><span class="sxs-lookup"><span data-stu-id="67f1d-224">The view matrices are more accurate for objects with model transforms that are created initially using the same coordinate system.</span></span>

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a><span data-ttu-id="67f1d-225">建立使用裝置連接參考框架的全像投影</span><span class="sxs-lookup"><span data-stu-id="67f1d-225">Create holograms using a device-attached frame of reference</span></span>

<span data-ttu-id="67f1d-226">有些的時候，當您想要呈現雷射所[會保持附加狀態](coordinate-systems.md#attached-frame-of-reference)到裝置的位置，例如進行偵錯資訊或資訊訊息時，才能夠判斷其方向裝置面板和不在中的位置空間。</span><span class="sxs-lookup"><span data-stu-id="67f1d-226">There are times when you want to render a hologram that [remains attached](coordinate-systems.md#attached-frame-of-reference) to the device's location, for example a panel with debugging information or an informational message when the device is only able to determine its orientation and not its position in space.</span></span> <span data-ttu-id="67f1d-227">為了達成此目的，我們會使用附加的畫面格的參考。</span><span class="sxs-lookup"><span data-stu-id="67f1d-227">To accomplish this, we use an attached frame of reference.</span></span>

<span data-ttu-id="67f1d-228">SpatialLocatorAttachedFrameOfReference 類別定義是相對於裝置，而不是真實世界的座標系統。</span><span class="sxs-lookup"><span data-stu-id="67f1d-228">The SpatialLocatorAttachedFrameOfReference class defines coordinate systems which are relative to the device rather than to the real-world.</span></span> <span data-ttu-id="67f1d-229">此框架有固定的標題相對於指向方向使用者當時正面臨參考畫面格建立時的使用者的恍神。</span><span class="sxs-lookup"><span data-stu-id="67f1d-229">This frame has a fixed heading relative to the user's surroundings that points in the direction the user was facing when the reference frame was created.</span></span> <span data-ttu-id="67f1d-230">從那時起，在此參考架構中的所有方向都是相對於該固定的標題中是即使在使用者旋轉裝置。</span><span class="sxs-lookup"><span data-stu-id="67f1d-230">From then on, all orientations in this frame of reference are relative to that fixed heading, even as the user rotates the device.</span></span>

<span data-ttu-id="67f1d-231">HoloLens，針對此畫面格的座標系統的原點位於旋轉的中心點的使用者的標頭，使它的位置不會受到前端的旋轉。</span><span class="sxs-lookup"><span data-stu-id="67f1d-231">For HoloLens, the origin of this frame's coordinate system is located at the center of rotation of the user's head, so that its position is not affected by head rotation.</span></span> <span data-ttu-id="67f1d-232">您的應用程式可以指定相對於放置在使用者之前全像投影此點的位移。</span><span class="sxs-lookup"><span data-stu-id="67f1d-232">Your app can specify an offset relative to this point to position holograms in front of the user.</span></span>

<span data-ttu-id="67f1d-233">若要取得 SpatialLocatorAttachedFrameOfReference，使用 SpatialLocator 類別並呼叫 CreateAttachedFrameOfReferenceAtCurrentHeading。</span><span class="sxs-lookup"><span data-stu-id="67f1d-233">To get a SpatialLocatorAttachedFrameOfReference, use the SpatialLocator class and call CreateAttachedFrameOfReferenceAtCurrentHeading.</span></span>

<span data-ttu-id="67f1d-234">請注意，這適用於整個範圍的 Windows Mixed Reality 裝置。</span><span class="sxs-lookup"><span data-stu-id="67f1d-234">Note that this applies to the entire range of Windows Mixed Reality devices.</span></span>

### <a name="use-a-reference-frame-attached-to-the-device"></a><span data-ttu-id="67f1d-235">使用附加至裝置的參考框架</span><span class="sxs-lookup"><span data-stu-id="67f1d-235">Use a reference frame attached to the device</span></span>

<span data-ttu-id="67f1d-236">下列各節討論我們在 Windows 全像攝影版的應用程式範本，以啟用裝置附加參考框架的使用此 API 中的變更。</span><span class="sxs-lookup"><span data-stu-id="67f1d-236">These sections talk about what we changed in the Windows Holographic app template to enable a device-attached frame of reference using this API.</span></span> <span data-ttu-id="67f1d-237">請注意，此 「 附加 」 的全像將與靜態或錨定全像投影，一起運作，而且可能也在裝置暫時找不到在世界中的位置時才使用。</span><span class="sxs-lookup"><span data-stu-id="67f1d-237">Note that this "attached" hologram will work alongside stationary or anchored holograms, and may also be used when the device is temporarily unable to find its position in the world.</span></span>

<span data-ttu-id="67f1d-238">首先，我們會變更儲存而不是 SpatialStationaryFrameOfReference SpatialLocatorAttachedFrameOfReference 範本：</span><span class="sxs-lookup"><span data-stu-id="67f1d-238">First, we changed the template to store a SpatialLocatorAttachedFrameOfReference instead of a SpatialStationaryFrameOfReference:</span></span>

<span data-ttu-id="67f1d-239">從**HolographicTagAlongSampleMain.h**:</span><span class="sxs-lookup"><span data-stu-id="67f1d-239">From **HolographicTagAlongSampleMain.h**:</span></span>

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

<span data-ttu-id="67f1d-240">從**HolographicTagAlongSampleMain.cpp**:</span><span class="sxs-lookup"><span data-stu-id="67f1d-240">From **HolographicTagAlongSampleMain.cpp**:</span></span>

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

<span data-ttu-id="67f1d-241">在更新期間，我們現在會取得座標系統在取自與框架預測的時間戳記。</span><span class="sxs-lookup"><span data-stu-id="67f1d-241">During the update, we now obtain the coordinate system at the time stamp obtained from with the frame prediction.</span></span>

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a><span data-ttu-id="67f1d-242">取得指標空間姿勢，並依照使用者的視線</span><span class="sxs-lookup"><span data-stu-id="67f1d-242">Get a spatial pointer pose, and follow the user's Gaze</span></span>

<span data-ttu-id="67f1d-243">我們想要追蹤使用者的我們範例闀[視線](gaze.md)，類似於在全像攝影版的殼層如何依照使用者的視線。</span><span class="sxs-lookup"><span data-stu-id="67f1d-243">We want our example hologram to follow the user's [gaze](gaze.md), similar to how the holographic shell can follow the user's gaze.</span></span> <span data-ttu-id="67f1d-244">為此，我們需要 SpatialPointerPose 獲得相同的時間戳記。</span><span class="sxs-lookup"><span data-stu-id="67f1d-244">For this, we need to get the SpatialPointerPose from the same time stamp.</span></span>

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

<span data-ttu-id="67f1d-245">此 SpatialPointerPose 有位置根據全像所需的資訊[使用者的目前標題](gaze-in-directx.md)。</span><span class="sxs-lookup"><span data-stu-id="67f1d-245">This SpatialPointerPose has the information needed to position the hologram according to the [user's current heading](gaze-in-directx.md).</span></span>

<span data-ttu-id="67f1d-246">基於使用者的詳細資訊，我們會使用線性插補 (「 lerp") 平滑的位置變更，使得它經過一段時間，就會發生。</span><span class="sxs-lookup"><span data-stu-id="67f1d-246">For reasons of user comfort, we use linear interpolation ("lerp") to smooth the change in position such that it occurs over a period of time.</span></span> <span data-ttu-id="67f1d-247">這是使用者於鎖定至其視線闀更舒適。</span><span class="sxs-lookup"><span data-stu-id="67f1d-247">This is more comfortable for the user than locking the hologram to their gaze.</span></span> <span data-ttu-id="67f1d-248">Lerping tag-along 全像的位置也可讓我們依抑制移動; 穩定全像如果我們沒有這個抑制，使用者會看到全像圖抖動由於功能通常被視為是使用者的標頭的音調移動。</span><span class="sxs-lookup"><span data-stu-id="67f1d-248">Lerping the tag-along hologram's position also allows us to stabilize the hologram by dampening the movement; if we did not do this dampening, the user would see the hologram jitter because of what are normally considered to be imperceptible movements of the user's head.</span></span>

<span data-ttu-id="67f1d-249">從**StationaryQuadRenderer::PositionHologram**:</span><span class="sxs-lookup"><span data-stu-id="67f1d-249">From **StationaryQuadRenderer::PositionHologram**:</span></span>

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
><span data-ttu-id="67f1d-250">在偵錯的窗格中，您可以選擇調整有點位置關閉的側邊全像，使它不會阻擋您的檢視。</span><span class="sxs-lookup"><span data-stu-id="67f1d-250">In the case of a debugging panel, you might choose to reposition the hologram off to the side a little so that it does not obstruct your view.</span></span> <span data-ttu-id="67f1d-251">以下是如何，您可能會執行的範例。</span><span class="sxs-lookup"><span data-stu-id="67f1d-251">Here's an example of how you might do that.</span></span>

<span data-ttu-id="67f1d-252">針對**StationaryQuadRenderer::PositionHologram**:</span><span class="sxs-lookup"><span data-stu-id="67f1d-252">For **StationaryQuadRenderer::PositionHologram**:</span></span>

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

### <a name="rotate-the-hologram-to-face-the-camera"></a><span data-ttu-id="67f1d-253">旋轉面對相機全像</span><span class="sxs-lookup"><span data-stu-id="67f1d-253">Rotate the hologram to face the camera</span></span>

<span data-ttu-id="67f1d-254">並不夠，只是定位全像圖，在此情況下是四組數字;我們也必須旋轉面對使用者的物件。</span><span class="sxs-lookup"><span data-stu-id="67f1d-254">It is not enough to simply position the hologram, which in this case is a quad; we must also rotate the object to face the user.</span></span> <span data-ttu-id="67f1d-255">請注意，這種旋轉，就會發生在世界空間中，因為這種類型的告示板，可讓 「 保持使用者的環境的一部分全像。</span><span class="sxs-lookup"><span data-stu-id="67f1d-255">Note that this rotation occurs in world space, because this type of billboarding allows the hologram to remain a part of the user's environment.</span></span> <span data-ttu-id="67f1d-256">檢視空間告示板並不知道如何為因為全像變為鎖定狀態來顯示方向;在此情況下，您也必須以取得不會破壞立體聲的轉譯檢視空間告示板轉換左邊和右邊的檢視矩陣之間進行插補。</span><span class="sxs-lookup"><span data-stu-id="67f1d-256">View-space billboarding is not as comfortable because the hologram becomes locked to the display orientation; in that case, you would also have to interpolate between the left and right view matrices in order to acquire a view-space billboard transform that does not disrupt stereo rendering.</span></span> <span data-ttu-id="67f1d-257">在這裡，我們會旋轉面對使用者 X 和 Z 軸上。</span><span class="sxs-lookup"><span data-stu-id="67f1d-257">Here, we rotate on the X and Z axes to face the user.</span></span>

<span data-ttu-id="67f1d-258">從**StationaryQuadRenderer::Update**:</span><span class="sxs-lookup"><span data-stu-id="67f1d-258">From **StationaryQuadRenderer::Update**:</span></span>

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

### <a name="render-the-attached-hologram"></a><span data-ttu-id="67f1d-259">呈現連結的全像</span><span class="sxs-lookup"><span data-stu-id="67f1d-259">Render the attached hologram</span></span>

<span data-ttu-id="67f1d-260">針對此範例中，我們也會選擇將轉譯的座標系統中 SpatialLocatorAttachedReferenceFrame，全像圖也就是我們所在全像圖。</span><span class="sxs-lookup"><span data-stu-id="67f1d-260">For this example, we also choose to render the hologram in the coordinate system of the SpatialLocatorAttachedReferenceFrame, which is where we positioned the hologram.</span></span> <span data-ttu-id="67f1d-261">（如果我們決定使用另一個座標系統來呈現，我們需要取得從裝置連接的參考畫面格的座標系統轉換至該座標系統。）</span><span class="sxs-lookup"><span data-stu-id="67f1d-261">(If we had decided to render using another coordinate system, we would need to acquire a transform from the device-attached reference frame's coordinate system to that coordinate system.)</span></span>

<span data-ttu-id="67f1d-262">從**HolographicTagAlongSampleMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="67f1d-262">From **HolographicTagAlongSampleMain::Render**:</span></span>

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

<span data-ttu-id="67f1d-263">就這麼容易！</span><span class="sxs-lookup"><span data-stu-id="67f1d-263">That's it!</span></span> <span data-ttu-id="67f1d-264">全像圖會現在"追趕 」 使用者的視線方向前面 2 公尺的位置。</span><span class="sxs-lookup"><span data-stu-id="67f1d-264">The hologram will now "chase" a position that is 2 meters in front of the user's gaze direction.</span></span>

>[!NOTE]
><span data-ttu-id="67f1d-265">此範例也會載入額外的內容-請參閱 StationaryQuadRenderer.cpp。</span><span class="sxs-lookup"><span data-stu-id="67f1d-265">This example also loads additional content - see StationaryQuadRenderer.cpp.</span></span>

## <a name="handling-tracking-loss"></a><span data-ttu-id="67f1d-266">處理追蹤遺失</span><span class="sxs-lookup"><span data-stu-id="67f1d-266">Handling tracking loss</span></span>

<span data-ttu-id="67f1d-267">當裝置找不到本身的世界中時，應用程式就會發生 「 追蹤遺失 」。</span><span class="sxs-lookup"><span data-stu-id="67f1d-267">When the device cannot locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="67f1d-268">Windows Mixed Reality 應用程式應該能夠處理這類中斷的位置追蹤系統。</span><span class="sxs-lookup"><span data-stu-id="67f1d-268">Windows Mixed Reality apps should be able to handle such disruptions to the positional tracking system.</span></span> <span data-ttu-id="67f1d-269">可觀察這些中斷，並利用預設 SpatialLocator LocatabilityChanged 事件回應建立。</span><span class="sxs-lookup"><span data-stu-id="67f1d-269">These disruptions can be observed, and responses created, by using the LocatabilityChanged event on the default SpatialLocator.</span></span>

<span data-ttu-id="67f1d-270">從**AppMain::SetHolographicSpace:**</span><span class="sxs-lookup"><span data-stu-id="67f1d-270">From **AppMain::SetHolographicSpace:**</span></span>

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

<span data-ttu-id="67f1d-271">當您的應用程式收到 LocatabilityChanged 事件時，它可以視需要變更行為。</span><span class="sxs-lookup"><span data-stu-id="67f1d-271">When your app receives a LocatabilityChanged event, it can change behavior as needed.</span></span> <span data-ttu-id="67f1d-272">比方說，在 PositionalTrackingInhibited 狀態下，您的應用程式可以暫停正常操作並轉譯[tag-along 全像](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference)，會顯示一則警告訊息。</span><span class="sxs-lookup"><span data-stu-id="67f1d-272">For example, in the PositionalTrackingInhibited state, your app can pause normal operation and render a [tag-along hologram](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) that displays a warning message.</span></span>

<span data-ttu-id="67f1d-273">Windows 全像攝影版的應用程式範本隨附於已為您建立的 LocatabilityChanged 處理常式。</span><span class="sxs-lookup"><span data-stu-id="67f1d-273">The Windows Holographic app template comes with a LocatabilityChanged handler already created for you.</span></span> <span data-ttu-id="67f1d-274">根據預設，它會顯示一則警告偵錯主控台無法使用位置追蹤時。</span><span class="sxs-lookup"><span data-stu-id="67f1d-274">By default, it displays a warning in the debug console when positional tracking is unavailable.</span></span> <span data-ttu-id="67f1d-275">您可以將程式碼加入這個處理常式，來提供回應，視需要從您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="67f1d-275">You can add code to this handler to provide a response as needed from your app.</span></span>

<span data-ttu-id="67f1d-276">從**AppMain.cpp:**</span><span class="sxs-lookup"><span data-stu-id="67f1d-276">From **AppMain.cpp:**</span></span>

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

## <a name="spatial-mapping"></a><span data-ttu-id="67f1d-277">空間對應</span><span class="sxs-lookup"><span data-stu-id="67f1d-277">Spatial mapping</span></span>

<span data-ttu-id="67f1d-278">[空間對應](spatial-mapping-in-directx.md)Api 進行介面網狀結構取得模型轉換的座標系統的使用。</span><span class="sxs-lookup"><span data-stu-id="67f1d-278">The [spatial mapping](spatial-mapping-in-directx.md) APIs make use of coordinate systems to get model transforms for surface meshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="67f1d-279">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67f1d-279">See also</span></span>
* [<span data-ttu-id="67f1d-280">座標系統</span><span class="sxs-lookup"><span data-stu-id="67f1d-280">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="67f1d-281">空間錨點</span><span class="sxs-lookup"><span data-stu-id="67f1d-281">Spatial anchors</span></span>](spatial-anchors.md)
* <span data-ttu-id="67f1d-282"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="67f1d-282"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* [<span data-ttu-id="67f1d-283">DirectX 中的前端和眼睛視線</span><span class="sxs-lookup"><span data-stu-id="67f1d-283">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="67f1d-284">指針與 DirectX 中的動作控制站</span><span class="sxs-lookup"><span data-stu-id="67f1d-284">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="67f1d-285">DirectX 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="67f1d-285">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)
