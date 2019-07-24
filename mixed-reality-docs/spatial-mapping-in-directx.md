---
title: DirectX 中的空間對應
description: 說明如何在 DirectX 應用程式中執行空間對應。 這包括通用 Windows 平臺 SDK 隨附之空間對應範例應用程式的詳細說明。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows mixed reality, 空間對應, 環境, 互動, directx, winrt, api, 範例程式碼, UWP, SDK, 逐步解說
ms.openlocfilehash: db3f1464158c04127e456cadd5fb633336909344
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63550699"
---
# <a name="spatial-mapping-in-directx"></a><span data-ttu-id="bfd78-105">DirectX 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="bfd78-105">Spatial mapping in DirectX</span></span>

<span data-ttu-id="bfd78-106">本主題說明如何在您的 DirectX 應用程式中執行[空間對應](spatial-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="bfd78-106">This topic describes how to implement [spatial mapping](spatial-mapping.md) in your DirectX app.</span></span> <span data-ttu-id="bfd78-107">這包括通用 Windows 平臺 SDK 隨附之空間對應範例應用程式的詳細說明。</span><span class="sxs-lookup"><span data-stu-id="bfd78-107">This includes a detailed explanation of the spatial mapping sample application that is included with the Universal Windows Platform SDK.</span></span>

<span data-ttu-id="bfd78-108">本主題使用來自[HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP 程式碼範例的程式碼。</span><span class="sxs-lookup"><span data-stu-id="bfd78-108">This topic uses code from the [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP code sample.</span></span>

>[!NOTE]
><span data-ttu-id="bfd78-109">本文中的程式碼片段目前示範如何使用C++/cx, C++ [ C++ ](creating-a-holographic-directx-project.md)而不是 C + 17 相容的/WinRT, 如全像攝影專案範本中所使用。</span><span class="sxs-lookup"><span data-stu-id="bfd78-109">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="bfd78-110">概念相當於C++/WinRT 專案, 但您必須轉譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="bfd78-110">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="directx-development-overview"></a><span data-ttu-id="bfd78-111">DirectX 開發總覽</span><span class="sxs-lookup"><span data-stu-id="bfd78-111">DirectX development overview</span></span>

<span data-ttu-id="bfd78-112">適用于空間對應的原生應用程式開發會使用[Windows 感知.](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)空間命名空間下的 api。</span><span class="sxs-lookup"><span data-stu-id="bfd78-112">Native application development for spatial mapping uses the APIs under the [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) namespace.</span></span> <span data-ttu-id="bfd78-113">這些 Api 提供空間對應功能的完整控制權, 其方式與[Unity](spatial-mapping-in-unity.md)所公開的空間對應 api 直接類似。</span><span class="sxs-lookup"><span data-stu-id="bfd78-113">These APIs provide full control of spatial mapping functionality, in a manner directly analogous to the spatial mapping APIs exposed by [Unity](spatial-mapping-in-unity.md).</span></span>

### <a name="perception-apis"></a><span data-ttu-id="bfd78-114">認知 Api</span><span class="sxs-lookup"><span data-stu-id="bfd78-114">Perception APIs</span></span>

<span data-ttu-id="bfd78-115">為空間對應開發提供的主要類型如下所示:</span><span class="sxs-lookup"><span data-stu-id="bfd78-115">The primary types provided for spatial mapping development are as follows:</span></span>
* <span data-ttu-id="bfd78-116">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)會以 SpatialSurfaceInfo 物件的形式, 提供應用程式在使用者附近空間的指定區域中的表面相關資訊。</span><span class="sxs-lookup"><span data-stu-id="bfd78-116">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) provides information about surfaces in application-specified regions of space near the user, in the form of SpatialSurfaceInfo objects.</span></span>
* <span data-ttu-id="bfd78-117">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx)描述單一否則空間介面, 包括唯一的識別碼、界限磁片區和上次變更的時間。</span><span class="sxs-lookup"><span data-stu-id="bfd78-117">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) describes a single extant spatial surface, including a unique ID, bounding volume and time of last change.</span></span> <span data-ttu-id="bfd78-118">它會在要求時以非同步方式提供 SpatialSurfaceMesh。</span><span class="sxs-lookup"><span data-stu-id="bfd78-118">It will provide a SpatialSurfaceMesh asynchronously upon request.</span></span>
* <span data-ttu-id="bfd78-119">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx)包含用來自訂 SpatialSurfaceInfo 所要求之 SpatialSurfaceMesh 物件的參數。</span><span class="sxs-lookup"><span data-stu-id="bfd78-119">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contains parameters used to customize the SpatialSurfaceMesh objects requested from SpatialSurfaceInfo.</span></span>
* <span data-ttu-id="bfd78-120">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx)代表單一空間表面的網格資料。</span><span class="sxs-lookup"><span data-stu-id="bfd78-120">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) represents the mesh data for a single spatial surface.</span></span> <span data-ttu-id="bfd78-121">頂點位置、頂點法線和三角形索引的資料會包含在成員 SpatialSurfaceMeshBuffer 物件中。</span><span class="sxs-lookup"><span data-stu-id="bfd78-121">The data for vertex positions, vertex normals and triangle indices is contained in member SpatialSurfaceMeshBuffer objects.</span></span>
* <span data-ttu-id="bfd78-122">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx)會包裝單一類型的網格資料。</span><span class="sxs-lookup"><span data-stu-id="bfd78-122">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) wraps a single type of mesh data.</span></span>

<span data-ttu-id="bfd78-123">使用這些 Api 開發應用程式時, 您的基本程式流程看起來會像這樣 (如以下所述的範例應用程式所示):</span><span class="sxs-lookup"><span data-stu-id="bfd78-123">When developing an application using these APIs, your basic program flow will look like this (as demonstrated in the sample application described below):</span></span>
- <span data-ttu-id="bfd78-124">**設定您的 SpatialSurfaceObserver**</span><span class="sxs-lookup"><span data-stu-id="bfd78-124">**Set up your SpatialSurfaceObserver**</span></span>
  - <span data-ttu-id="bfd78-125">呼叫[RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), 以確保使用者已取得應用程式的許可權, 以使用裝置的空間對應功能。</span><span class="sxs-lookup"><span data-stu-id="bfd78-125">Call [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), to ensure that the user has given permission for your application to use the device's spatial mapping capabilities.</span></span>
  - <span data-ttu-id="bfd78-126">具現化 SpatialSurfaceObserver 物件。</span><span class="sxs-lookup"><span data-stu-id="bfd78-126">Instantiate a SpatialSurfaceObserver object.</span></span>
  - <span data-ttu-id="bfd78-127">呼叫[SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx)來指定您要在其中顯示空間表面相關資訊的區域。</span><span class="sxs-lookup"><span data-stu-id="bfd78-127">Call [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) to specify the regions of space in which you want information about spatial surfaces.</span></span> <span data-ttu-id="bfd78-128">只要再次呼叫此函式, 您就可以在未來修改這些區域。</span><span class="sxs-lookup"><span data-stu-id="bfd78-128">You may modify these regions in the future by simply calling this function again.</span></span> <span data-ttu-id="bfd78-129">每個區域都是使用[SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx)所指定。</span><span class="sxs-lookup"><span data-stu-id="bfd78-129">Each region is specified using a [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span></span>
  - <span data-ttu-id="bfd78-130">註冊[ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx)事件, 這會在您所指定空間區域中的空間表面有新資訊可用時引發。</span><span class="sxs-lookup"><span data-stu-id="bfd78-130">Register for the [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) event, which will fire whenever new information is available about the spatial surfaces in the regions of space you have specified.</span></span>
- <span data-ttu-id="bfd78-131">**處理 ObservedSurfacesChanged 事件**</span><span class="sxs-lookup"><span data-stu-id="bfd78-131">**Process ObservedSurfacesChanged events**</span></span>
  - <span data-ttu-id="bfd78-132">在您的事件處理常式中, 呼叫[GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx)以接收 SpatialSurfaceInfo 物件的對應。</span><span class="sxs-lookup"><span data-stu-id="bfd78-132">In your event handler, call [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) to receive a map of SpatialSurfaceInfo objects.</span></span> <span data-ttu-id="bfd78-133">使用此地圖, 您可以更新[使用者環境中有](spatial-mapping.md#mesh-caching)哪些空間表面的記錄。</span><span class="sxs-lookup"><span data-stu-id="bfd78-133">Using this map, you can update your records of which spatial surfaces [exist in the user's environment](spatial-mapping.md#mesh-caching).</span></span>
  - <span data-ttu-id="bfd78-134">針對每個 SpatialSurfaceInfo 物件, 您可以查詢[TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx)來判斷介面的空間範圍 (以您選擇的[空間座標系統](coordinate-systems.md)表示)。</span><span class="sxs-lookup"><span data-stu-id="bfd78-134">For each SpatialSurfaceInfo object, you may query [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) to determine the spatial extents of the surface, expressed in a [spatial coordinate system](coordinate-systems.md) of your choosing.</span></span>
  - <span data-ttu-id="bfd78-135">如果您決定要求網格空間介面, 請呼叫[TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx)。</span><span class="sxs-lookup"><span data-stu-id="bfd78-135">If you decide to request mesh for a spatial surface, call [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span></span> <span data-ttu-id="bfd78-136">您可以提供選項來指定所需的三角形密度, 以及所傳回網格資料的格式。</span><span class="sxs-lookup"><span data-stu-id="bfd78-136">You may provide options specifying the desired density of triangles, and the format of the returned mesh data.</span></span>
- <span data-ttu-id="bfd78-137">**接收和處理網格**</span><span class="sxs-lookup"><span data-stu-id="bfd78-137">**Receive and process mesh**</span></span>
  - <span data-ttu-id="bfd78-138">TryComputeLatestMeshAsync 的每個呼叫都會 aysnchronously 傳回一個 SpatialSurfaceMesh 物件。</span><span class="sxs-lookup"><span data-stu-id="bfd78-138">Each call to TryComputeLatestMeshAsync will aysnchronously return one SpatialSurfaceMesh object.</span></span>
  - <span data-ttu-id="bfd78-139">您可以從這個物件存取包含的 SpatialSurfaceMeshBuffer 物件, 以便存取三角形索引、頂點位置以及網格的 (如果要求) 頂點法線。</span><span class="sxs-lookup"><span data-stu-id="bfd78-139">From this object you can access the contained SpatialSurfaceMeshBuffer objects in order to access the triangle indices, vertex positions and (if requested) vertex normals of the mesh.</span></span> <span data-ttu-id="bfd78-140">此資料的格式會與用來轉譯網格的[Direct3D 11 api](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx)直接相容。</span><span class="sxs-lookup"><span data-stu-id="bfd78-140">This data will be in a format directly compatible with the [Direct3D 11 APIs](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) used for rendering meshes.</span></span>
  - <span data-ttu-id="bfd78-141">從這裡, 您的應用程式可以選擇性地執行網格資料的分析或[處理](spatial-mapping.md#mesh-processing), 並使用它來[呈現](spatial-mapping.md#rendering)和物理[raycasting 和衝突](spatial-mapping.md#raycasting-and-collision)。</span><span class="sxs-lookup"><span data-stu-id="bfd78-141">From here your application can optionally perform analysis or [processing](spatial-mapping.md#mesh-processing) of the mesh data, and use it for [rendering](spatial-mapping.md#rendering) and physics [raycasting and collision](spatial-mapping.md#raycasting-and-collision).</span></span>
  - <span data-ttu-id="bfd78-142">要注意的一個重要詳細資料, 就是您必須將縮放比例套用至網格頂點位置 (例如, 在用來轉譯網格的頂點著色器中), 將它們從儲存在緩衝區中的優化整數單位轉換成計量。</span><span class="sxs-lookup"><span data-stu-id="bfd78-142">One important detail to note is that you must apply a scale to the mesh vertex positions (for example in the vertex shader used for rendering the meshes), to convert them from the optimized integer units in which they are stored in the buffer, to meters.</span></span> <span data-ttu-id="bfd78-143">您可以藉由呼叫[VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)來取得這項調整。</span><span class="sxs-lookup"><span data-stu-id="bfd78-143">You can retrieve this scale by calling [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span></span>

### <a name="troubleshooting"></a><span data-ttu-id="bfd78-144">疑難排解</span><span class="sxs-lookup"><span data-stu-id="bfd78-144">Troubleshooting</span></span>
* <span data-ttu-id="bfd78-145">別忘了使用 SpatialSurfaceMesh 所傳回的小數值, 來調整頂點著色器中的網格頂點位置[。 VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span><span class="sxs-lookup"><span data-stu-id="bfd78-145">Don't forget to scale mesh vertex positions in your vertex shader, using the scale returned by [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span></span>

## <a name="spatial-mapping-code-sample-walkthrough"></a><span data-ttu-id="bfd78-146">空間對應程式碼範例逐步解說</span><span class="sxs-lookup"><span data-stu-id="bfd78-146">Spatial Mapping code sample walkthrough</span></span>

<span data-ttu-id="bfd78-147">「全像[空間對應](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping)」程式碼範例包含您可以用來開始將 surface 網格載入應用程式的程式碼, 包括用於管理和呈現 surface 網格的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="bfd78-147">The [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample includes code that you can use to get started loading surface meshes into your app, including infrastructure for managing and rendering surface meshes.</span></span>

<span data-ttu-id="bfd78-148">現在, 我們將逐步解說如何將介面對應功能新增至您的 DirectX 應用程式。</span><span class="sxs-lookup"><span data-stu-id="bfd78-148">Now, we walk through how to add surface mapping capability to your DirectX app.</span></span> <span data-ttu-id="bfd78-149">您可以將此程式碼新增至您的 Windows 全像攝影[應用程式範本](creating-a-holographic-directx-project.md)專案, 或透過流覽上述的程式碼範例來追蹤。</span><span class="sxs-lookup"><span data-stu-id="bfd78-149">You can add this code to your [Windows Holographic app template](creating-a-holographic-directx-project.md) project, or you can follow along by browsing through the code sample mentioned above.</span></span> <span data-ttu-id="bfd78-150">這個程式碼範例是以 Windows 全像應用程式範本為基礎。</span><span class="sxs-lookup"><span data-stu-id="bfd78-150">This code sample is based on the Windows Holographic app template.</span></span>

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="bfd78-151">設定應用程式以使用 spatialPerception 功能</span><span class="sxs-lookup"><span data-stu-id="bfd78-151">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="bfd78-152">您的應用程式必須能夠使用空間對應功能。</span><span class="sxs-lookup"><span data-stu-id="bfd78-152">Your app must be able to use the spatial mapping capability.</span></span> <span data-ttu-id="bfd78-153">這是必要的, 因為空間網格表示使用者的環境, 這可能會被視為私用資料。</span><span class="sxs-lookup"><span data-stu-id="bfd78-153">This is necessary because the spatial mesh is a representation of the user's environment, which may be considered private data.</span></span> <span data-ttu-id="bfd78-154">在您應用程式的 package.appxmanifest.xml 檔案中宣告這項功能。</span><span class="sxs-lookup"><span data-stu-id="bfd78-154">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="bfd78-155">以下為範例：</span><span class="sxs-lookup"><span data-stu-id="bfd78-155">Here's an example:</span></span>

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="bfd78-156">這項功能來自**uap2**命名空間。</span><span class="sxs-lookup"><span data-stu-id="bfd78-156">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="bfd78-157">若要在資訊清單中取得這個命名空間的存取權, 請將它當做&lt;xlmns 屬性包含在封裝 > 元素中。</span><span class="sxs-lookup"><span data-stu-id="bfd78-157">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="bfd78-158">以下為範例：</span><span class="sxs-lookup"><span data-stu-id="bfd78-158">Here's an example:</span></span>

```xml
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a><span data-ttu-id="bfd78-159">檢查空間對應功能支援</span><span class="sxs-lookup"><span data-stu-id="bfd78-159">Check for spatial mapping feature support</span></span>

<span data-ttu-id="bfd78-160">Windows Mixed Reality 支援各式各樣的裝置, 包括不支援空間對應的裝置。</span><span class="sxs-lookup"><span data-stu-id="bfd78-160">Windows Mixed Reality supports a wide range of devices, including devices which do not support spatial mapping.</span></span> <span data-ttu-id="bfd78-161">如果您的應用程式可以使用空間對應, 或必須使用空間對應來提供功能, 則應該先檢查以確定是否支援空間對應, 再嘗試使用它。</span><span class="sxs-lookup"><span data-stu-id="bfd78-161">If your app can use spatial mapping, or must use spatial mapping, to provide functionality, it should check to make sure that spatial mapping is supported before trying to use it.</span></span> <span data-ttu-id="bfd78-162">例如, 如果您的混合現實應用程式需要空間對應, 當使用者嘗試在沒有空間對應的裝置上執行它時, 應該會顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="bfd78-162">For example, if spatial mapping is required by your mixed reality app, it should display a message to that effect if a user tries running it on a device without spatial mapping.</span></span> <span data-ttu-id="bfd78-163">或者, 您的應用程式可能可以呈現自己的虛擬環境來取代使用者的環境, 提供的體驗類似于可用空間對應時所發生的情況。</span><span class="sxs-lookup"><span data-stu-id="bfd78-163">Or, your app may be able to render its own virtual environment in place of the user's environment, providing an experience that is similar to what would happen if spatial mapping were available.</span></span> <span data-ttu-id="bfd78-164">在任何事件中, 此 API 可讓您的應用程式知道何時不會取得空間對應資料, 並以適當的方式回應。</span><span class="sxs-lookup"><span data-stu-id="bfd78-164">In any event, this API allows your app to be aware of when it will not get spatial mapping data and respond in the appropriate way.</span></span>

<span data-ttu-id="bfd78-165">若要檢查目前的裝置是否有空間對應支援, 請先確定 UWP 合約位於層級4或更高, 然後呼叫 SpatialSurfaceObserver:: IsSupported ()。</span><span class="sxs-lookup"><span data-stu-id="bfd78-165">To check the current device for spatial mapping support, first make sure the UWP contract is at level 4 or greater and then call SpatialSurfaceObserver::IsSupported().</span></span> <span data-ttu-id="bfd78-166">以下是如何在「全像攝影[空間對應](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping)」程式碼範例的內容中執行這項操作的方法。</span><span class="sxs-lookup"><span data-stu-id="bfd78-166">Here's how to do so in the context of the [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample.</span></span> <span data-ttu-id="bfd78-167">只有在要求存取權之前, 才會檢查支援。</span><span class="sxs-lookup"><span data-stu-id="bfd78-167">Support is checked just before requesting access.</span></span>

<span data-ttu-id="bfd78-168">從 SDK 15063 版開始, 提供 SpatialSurfaceObserver:: IsSupported () API。</span><span class="sxs-lookup"><span data-stu-id="bfd78-168">The SpatialSurfaceObserver::IsSupported() API is available starting in SDK version 15063.</span></span> <span data-ttu-id="bfd78-169">如有需要, 請在使用此 API 之前, 將專案的目標重定為平臺版本15063。</span><span class="sxs-lookup"><span data-stu-id="bfd78-169">If necessary, retarget your project to platform version 15063 before using this API.</span></span>

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

<span data-ttu-id="bfd78-170">請注意, 當 UWP 合約小於層級4時, 應用程式應該繼續執行, 就像裝置能夠執行空間對應一樣。</span><span class="sxs-lookup"><span data-stu-id="bfd78-170">Note that when the UWP contract is less than level 4, the app should proceed as though the device is capable of doing spatial mapping.</span></span>

### <a name="request-access-to-spatial-mapping-data"></a><span data-ttu-id="bfd78-171">要求存取空間對應資料</span><span class="sxs-lookup"><span data-stu-id="bfd78-171">Request access to spatial mapping data</span></span>

<span data-ttu-id="bfd78-172">您的應用程式必須先要求許可權才能存取空間對應資料, 然後再嘗試建立任何 surface 觀察者。</span><span class="sxs-lookup"><span data-stu-id="bfd78-172">Your app needs to request permission to access spatial mapping data before trying to create any surface observers.</span></span> <span data-ttu-id="bfd78-173">以下是以我們的表面對應程式碼範例為基礎的範例, 此頁面稍後會提供更多詳細資料:</span><span class="sxs-lookup"><span data-stu-id="bfd78-173">Here's an example based upon our Surface Mapping code sample, with more details provided later on this page:</span></span>

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

### <a name="create-a-surface-observer"></a><span data-ttu-id="bfd78-174">建立 surface 觀察者</span><span class="sxs-lookup"><span data-stu-id="bfd78-174">Create a surface observer</span></span>

<span data-ttu-id="bfd78-175">**Windows::P erception:: namespace::** surface 命名空間包含[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)類別, 它會觀察您在[SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx)中指定的一或多個磁片區。</span><span class="sxs-lookup"><span data-stu-id="bfd78-175">The **Windows::Perception::Spatial::Surfaces** namespace includes the [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) class, which observes one or more volumes that you specify in a [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span></span> <span data-ttu-id="bfd78-176">使用[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)實例即時存取 surface 網格資料。</span><span class="sxs-lookup"><span data-stu-id="bfd78-176">Use a [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) instance to access surface mesh data in real time.</span></span>

<span data-ttu-id="bfd78-177">從**AppMain**:</span><span class="sxs-lookup"><span data-stu-id="bfd78-177">From **AppMain.h**:</span></span>

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

<span data-ttu-id="bfd78-178">如上一節所述, 您必須先要求存取空間對應資料, 您的應用程式才能使用它。</span><span class="sxs-lookup"><span data-stu-id="bfd78-178">As noted in the previous section, you must request access to spatial mapping data before your app can use it.</span></span> <span data-ttu-id="bfd78-179">此存取權會在 HoloLens 上自動授與。</span><span class="sxs-lookup"><span data-stu-id="bfd78-179">This access is granted automatically on the HoloLens.</span></span>

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

<span data-ttu-id="bfd78-180">接下來, 您必須設定介面觀察器以觀察特定的周框磁片區。</span><span class="sxs-lookup"><span data-stu-id="bfd78-180">Next, you need to configure the surface observer to observe a specific bounding volume.</span></span> <span data-ttu-id="bfd78-181">在這裡, 我們觀察到一個20x20x5 計量的方塊, 以座標系統的原點為中心。</span><span class="sxs-lookup"><span data-stu-id="bfd78-181">Here, we observe a box that is 20x20x5 meters, centered at the origin of the coordinate system.</span></span>

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

<span data-ttu-id="bfd78-182">請注意, 您可以改為設定多個界限磁片區。</span><span class="sxs-lookup"><span data-stu-id="bfd78-182">Note that you can set multiple bounding volumes instead.</span></span>

<span data-ttu-id="bfd78-183">*這是虛擬代碼:*</span><span class="sxs-lookup"><span data-stu-id="bfd78-183">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

<span data-ttu-id="bfd78-184">您也可以使用其他的周框形狀 (例如, 視圖截圖), 或不對齊軸的周框方塊。</span><span class="sxs-lookup"><span data-stu-id="bfd78-184">It is also possible to use other bounding shapes - such as a view frustum, or a bounding box that is not axis aligned.</span></span>

<span data-ttu-id="bfd78-185">*這是虛擬代碼:*</span><span class="sxs-lookup"><span data-stu-id="bfd78-185">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

<span data-ttu-id="bfd78-186">如果您的應用程式在表面對應資料無法使用時, 需要以不同的方式執行任何動作, 您可以撰寫程式碼來回應不**允許** [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx)的情況, 例如, 不允許在具有沉浸式的電腦上使用。已連接的裝置, 因為這些裝置沒有空間對應的硬體。</span><span class="sxs-lookup"><span data-stu-id="bfd78-186">If your app needs to do anything differently when surface mapping data is not available, you can write code to respond to the case where the [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) is not **Allowed** - for example, it will not be allowed on PCs with immersive devices attached because those devices don't have hardware for spatial mapping.</span></span> <span data-ttu-id="bfd78-187">針對這些裝置, 您應該改為依賴空間階段, 以取得使用者環境和裝置設定的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="bfd78-187">For these devices, you should instead rely on the spatial stage for information about the user's environment and device configuration.</span></span>

### <a name="initialize-and-update-the-surface-mesh-collection"></a><span data-ttu-id="bfd78-188">初始化和更新 surface 網狀集合</span><span class="sxs-lookup"><span data-stu-id="bfd78-188">Initialize and update the surface mesh collection</span></span>

<span data-ttu-id="bfd78-189">如果表面觀察器建立成功, 我們可以繼續初始化 surface 網狀集合。</span><span class="sxs-lookup"><span data-stu-id="bfd78-189">If the surface observer was successfully created, we can proceed to initialize our surface mesh collection.</span></span> <span data-ttu-id="bfd78-190">在這裡, 我們會使用提取模型 API 立即取得目前觀察到的表面集:</span><span class="sxs-lookup"><span data-stu-id="bfd78-190">Here, we use the pull model API to get the current set of observed surfaces right away:</span></span>

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

<span data-ttu-id="bfd78-191">也有可用來取得 surface 網格資料的推播模型。</span><span class="sxs-lookup"><span data-stu-id="bfd78-191">There is also a push model available to get surface mesh data.</span></span> <span data-ttu-id="bfd78-192">如果您選擇, 您可以自由地將應用程式設計成隻使用提取模型, 在這種情況下, 您會每隔一段時間 (例如, 每個畫面格) 或特定期間 (如遊戲設定期間) 輪詢資料。</span><span class="sxs-lookup"><span data-stu-id="bfd78-192">You are free to design your app to use only the pull model if you choose, in which case you'll poll for data every so often - say, once per frame - or during a specific time period, such as during game setup.</span></span> <span data-ttu-id="bfd78-193">若是如此, 您需要的就是上述程式碼。</span><span class="sxs-lookup"><span data-stu-id="bfd78-193">If so, the above code is what you need.</span></span>

<span data-ttu-id="bfd78-194">在我們的程式碼範例中, 我們選擇示範這兩種模型的使用方式, 以供 pedagogical 之用。</span><span class="sxs-lookup"><span data-stu-id="bfd78-194">In our code sample, we chose to demonstrate the use of both models for pedagogical purposes.</span></span> <span data-ttu-id="bfd78-195">在此, 我們會訂閱事件, 以便在系統辨識變更時接收最新的介面網格資料。</span><span class="sxs-lookup"><span data-stu-id="bfd78-195">Here, we subscribe to an event to receive up-to-date surface mesh data whenever the system recognizes a change.</span></span>

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

<span data-ttu-id="bfd78-196">我們的程式碼範例也設定為回應這些事件。</span><span class="sxs-lookup"><span data-stu-id="bfd78-196">Our code sample is also configured to respond to these events.</span></span> <span data-ttu-id="bfd78-197">讓我們逐步解說如何執行此動作。</span><span class="sxs-lookup"><span data-stu-id="bfd78-197">Let's walk through how we do this.</span></span>

<span data-ttu-id="bfd78-198">**注意：** 這可能不是您的應用程式處理網格資料最有效率的方式。</span><span class="sxs-lookup"><span data-stu-id="bfd78-198">**NOTE:** This might not be the most efficient way for your app to handle mesh data.</span></span> <span data-ttu-id="bfd78-199">這段程式碼是為了清楚起見而撰寫的, 並不會進行優化。</span><span class="sxs-lookup"><span data-stu-id="bfd78-199">This code is written for clarity and is not optimized.</span></span>

<span data-ttu-id="bfd78-200">Surface 網格資料是在唯讀對應中提供, 會使用[Platform:: guid](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx)作為索引鍵值來儲存[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx)物件。</span><span class="sxs-lookup"><span data-stu-id="bfd78-200">The surface mesh data is provided in a read-only map that stores [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) objects using [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) as key values.</span></span>

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

<span data-ttu-id="bfd78-201">若要處理這項資料, 我們會先找出不在集合中的索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="bfd78-201">To process this data, we look first for key values that aren't in our collection.</span></span> <span data-ttu-id="bfd78-202">本主題稍後會介紹如何將資料儲存在我們的範例應用程式中的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="bfd78-202">Details on how the data is stored in our sample app will be presented later in this topic.</span></span>

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

<span data-ttu-id="bfd78-203">我們也必須移除表面網格集合中的表面網格, 但這不在系統集合中。</span><span class="sxs-lookup"><span data-stu-id="bfd78-203">We also have to remove surface meshes that are in our surface mesh collection, but that aren't in the system collection anymore.</span></span> <span data-ttu-id="bfd78-204">若要這麼做, 我們需要執行類似于我們剛才示範的內容, 以新增和更新網格;我們會在應用程式的集合上迴圈, 並檢查我們的**Guid**是否在系統集合中。</span><span class="sxs-lookup"><span data-stu-id="bfd78-204">To do so, we need to do something akin to the opposite of what we just showed for adding and updating meshes; we loop on our app's collection, and check to see if the **Guid** we have is in the system collection.</span></span> <span data-ttu-id="bfd78-205">如果不在系統集合中, 我們會將它從我們移除。</span><span class="sxs-lookup"><span data-stu-id="bfd78-205">If it's not in the system collection, we remove it from ours.</span></span>

<span data-ttu-id="bfd78-206">從 AppMain 中的事件處理常式:</span><span class="sxs-lookup"><span data-stu-id="bfd78-206">From our event handler in AppMain.cpp:</span></span>

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

<span data-ttu-id="bfd78-207">在 RealtimeSurfaceMeshRenderer 中執行網格剪除:</span><span class="sxs-lookup"><span data-stu-id="bfd78-207">The implementation of mesh pruning in RealtimeSurfaceMeshRenderer.cpp:</span></span>

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

### <a name="acquire-and-use-surface-mesh-data-buffers"></a><span data-ttu-id="bfd78-208">取得和使用 surface 網格資料緩衝區</span><span class="sxs-lookup"><span data-stu-id="bfd78-208">Acquire and use surface mesh data buffers</span></span>

<span data-ttu-id="bfd78-209">取得 surface 網格資訊就像提取資料收集和處理該集合的更新一樣簡單。</span><span class="sxs-lookup"><span data-stu-id="bfd78-209">Getting the surface mesh information was as easy as pulling a data collection and processing updates to that collection.</span></span> <span data-ttu-id="bfd78-210">現在, 我們將詳細說明您可以如何使用資料。</span><span class="sxs-lookup"><span data-stu-id="bfd78-210">Now, we'll go into detail on how you can use the data.</span></span>

<span data-ttu-id="bfd78-211">在我們的程式碼範例中, 我們選擇使用 surface 網格來呈現。</span><span class="sxs-lookup"><span data-stu-id="bfd78-211">In our code example, we chose to use the surface meshes for rendering.</span></span> <span data-ttu-id="bfd78-212">這是在真實世界表面 occluding 全息影像的常見案例。</span><span class="sxs-lookup"><span data-stu-id="bfd78-212">This is a common scenario for occluding holograms behind real-world surfaces.</span></span> <span data-ttu-id="bfd78-213">您也可以轉譯網格, 或轉譯其已處理的版本, 以便在您開始提供應用程式或遊戲功能之前, 向使用者顯示要掃描的房間區域。</span><span class="sxs-lookup"><span data-stu-id="bfd78-213">You can also render the meshes, or render processed versions of them, to show the user what areas of the room are scanned before you start providing app or game functionality.</span></span>

<span data-ttu-id="bfd78-214">程式碼範例會在從上一節所述的事件處理常式接收 surface 網格更新時啟動進程。</span><span class="sxs-lookup"><span data-stu-id="bfd78-214">The code sample starts the process when it receives surface mesh updates from the event handler that we described in the previous section.</span></span> <span data-ttu-id="bfd78-215">此函式中的重要程式程式碼是更新 surface*網格*的呼叫: 這次我們已經處理過網格資訊, 而我們即將取得要使用的頂點和索引資料, 如我們所見。</span><span class="sxs-lookup"><span data-stu-id="bfd78-215">The important line of code in this function is the call to update the surface *mesh*: by this time we have already processed the mesh info, and we are about to get the vertex and index data for use as we see fit.</span></span>

<span data-ttu-id="bfd78-216">從 RealtimeSurfaceMeshRenderer:</span><span class="sxs-lookup"><span data-stu-id="bfd78-216">From RealtimeSurfaceMeshRenderer.cpp:</span></span>

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

<span data-ttu-id="bfd78-217">我們的範例程式碼的設計, 是為了讓資料類別 ( **SurfaceMesh**) 處理網格資料處理和呈現。</span><span class="sxs-lookup"><span data-stu-id="bfd78-217">Our sample code is designed so that a data class, **SurfaceMesh**, handles mesh data processing and rendering.</span></span> <span data-ttu-id="bfd78-218">這些網格是**RealtimeSurfaceMeshRenderer**實際上會保留對應的內容。</span><span class="sxs-lookup"><span data-stu-id="bfd78-218">These meshes are what the **RealtimeSurfaceMeshRenderer** actually keeps a map of.</span></span> <span data-ttu-id="bfd78-219">每一個都有其來源 SpatialSurfaceMesh 的參考, 而我們會在需要存取網格頂點或索引緩衝區時使用它, 或取得網格的轉換。</span><span class="sxs-lookup"><span data-stu-id="bfd78-219">Each one has a reference to the SpatialSurfaceMesh it came from, and we use it any time that we need to access the mesh vertex or index buffers, or get a transform for the mesh.</span></span> <span data-ttu-id="bfd78-220">目前, 我們會將網格標示為需要更新。</span><span class="sxs-lookup"><span data-stu-id="bfd78-220">For now, we flag the mesh as needing an update.</span></span>

<span data-ttu-id="bfd78-221">從 SurfaceMesh:</span><span class="sxs-lookup"><span data-stu-id="bfd78-221">From SurfaceMesh.cpp:</span></span>

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

<span data-ttu-id="bfd78-222">下一次要求網格繪製其本身時, 它會先檢查旗標。</span><span class="sxs-lookup"><span data-stu-id="bfd78-222">Next time the mesh is asked to draw itself, it will check the flag first.</span></span> <span data-ttu-id="bfd78-223">如果需要更新, 則會在 GPU 上更新頂點和索引緩衝區。</span><span class="sxs-lookup"><span data-stu-id="bfd78-223">If an update is needed, the vertex and index buffers will be updated on the GPU.</span></span>

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

<span data-ttu-id="bfd78-224">首先, 我們會取得原始資料緩衝區:</span><span class="sxs-lookup"><span data-stu-id="bfd78-224">First, we acquire the raw data buffers:</span></span>

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

<span data-ttu-id="bfd78-225">然後, 我們會使用 HoloLens 所提供的網格資料來建立 Direct3D 裝置緩衝區:</span><span class="sxs-lookup"><span data-stu-id="bfd78-225">Then, we create Direct3D device buffers with the mesh data provided by the HoloLens:</span></span>

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

<span data-ttu-id="bfd78-226">**注意：** 如需上一個程式碼片段中使用的 CreateDirectXBuffer helper 函式, 請參閱介面對應程式碼範例:SurfaceMesh .cpp, GetDataFromIBuffer. h。</span><span class="sxs-lookup"><span data-stu-id="bfd78-226">**NOTE:** For the CreateDirectXBuffer helper function used in the previous snippet, see the Surface Mapping code sample: SurfaceMesh.cpp, GetDataFromIBuffer.h.</span></span> <span data-ttu-id="bfd78-227">現在裝置資源建立已完成, 且網格已被視為已載入, 並可供更新和呈現。</span><span class="sxs-lookup"><span data-stu-id="bfd78-227">Now the device resource creation is complete, and the mesh is considered to be loaded and ready for update and render.</span></span>

### <a name="update-and-render-surface-meshes"></a><span data-ttu-id="bfd78-228">更新和呈現 surface 網格</span><span class="sxs-lookup"><span data-stu-id="bfd78-228">Update and render surface meshes</span></span>

<span data-ttu-id="bfd78-229">我們的 SurfaceMesh 類別具有特製化的更新函數。</span><span class="sxs-lookup"><span data-stu-id="bfd78-229">Our SurfaceMesh class has a specialized update function.</span></span> <span data-ttu-id="bfd78-230">每個[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx)都有自己的轉換, 而我們的範例會使用目前的座標系統, 讓我們的**SpatialStationaryReferenceFrame**取得轉換。</span><span class="sxs-lookup"><span data-stu-id="bfd78-230">Each [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) has its own transform, and our sample uses the current coordinate system for our **SpatialStationaryReferenceFrame** to acquire the transform.</span></span> <span data-ttu-id="bfd78-231">然後, 它會更新 GPU 上的模型常數緩衝區。</span><span class="sxs-lookup"><span data-stu-id="bfd78-231">Then it updates the model constant buffer on the GPU.</span></span>

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

<span data-ttu-id="bfd78-232">當轉譯 surface 網格時, 我們會先執行一些準備工作, 再轉譯集合。</span><span class="sxs-lookup"><span data-stu-id="bfd78-232">When it's time to render surface meshes, we do some prep work before rendering the collection.</span></span> <span data-ttu-id="bfd78-233">我們為目前的轉譯設定設定了著色器管線, 並設定了輸入組合語言階段。</span><span class="sxs-lookup"><span data-stu-id="bfd78-233">We set up the shader pipeline for the current rendering configuration, and we set up the input assembler stage.</span></span> <span data-ttu-id="bfd78-234">請注意, 全像攝影攝影機協助程式類別**CameraResources**現在已經設定了 view/投射常數緩衝區。</span><span class="sxs-lookup"><span data-stu-id="bfd78-234">Note that the holographic camera helper class **CameraResources.cpp** already has set up the view/projection constant buffer by now.</span></span>

<span data-ttu-id="bfd78-235">從**RealtimeSurfaceMeshRenderer:: Render**:</span><span class="sxs-lookup"><span data-stu-id="bfd78-235">From **RealtimeSurfaceMeshRenderer::Render**:</span></span>

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

<span data-ttu-id="bfd78-236">完成這項作業之後, 我們會在我們的網格上迴圈, 並告訴每一個都要自行繪製。</span><span class="sxs-lookup"><span data-stu-id="bfd78-236">Once this is done, we loop on our meshes and tell each one to draw itself.</span></span> <span data-ttu-id="bfd78-237">**注意：** 此範例程式碼未優化, 無法使用任何類型的截量剔除, 但您應該在應用程式中包含這項功能。</span><span class="sxs-lookup"><span data-stu-id="bfd78-237">**NOTE:** This sample code is not optimized to use any sort of frustum culling, but you should include this feature in your app.</span></span>

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

<span data-ttu-id="bfd78-238">個別的網格會負責設定頂點和索引緩衝區、stride 和模型轉換常數緩衝區。</span><span class="sxs-lookup"><span data-stu-id="bfd78-238">The individual meshes are responsible for setting up the vertex and index buffer, stride, and model transform constant buffer.</span></span> <span data-ttu-id="bfd78-239">如同 Windows 全像攝影應用程式範本中的旋轉 cube, 我們使用實例轉譯為 stereoscopic 緩衝區。</span><span class="sxs-lookup"><span data-stu-id="bfd78-239">As with the spinning cube in the Windows Holographic app template, we render to stereoscopic buffers using instancing.</span></span>

<span data-ttu-id="bfd78-240">從**SurfaceMesh::D raw**:</span><span class="sxs-lookup"><span data-stu-id="bfd78-240">From **SurfaceMesh::Draw**:</span></span>

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

### <a name="rendering-choices-with-surface-mapping"></a><span data-ttu-id="bfd78-241">使用表面對應呈現選擇</span><span class="sxs-lookup"><span data-stu-id="bfd78-241">Rendering choices with Surface Mapping</span></span>

<span data-ttu-id="bfd78-242">「介面對應」程式碼範例提供僅限遮蔽呈現 surface 網格資料的程式碼, 以及用於呈現 surface 網格資料的螢幕。</span><span class="sxs-lookup"><span data-stu-id="bfd78-242">The Surface Mapping code sample offers code for occlusion-only rendering of surface mesh data, and for on-screen rendering of surface mesh data.</span></span> <span data-ttu-id="bfd78-243">您選擇的路徑-或兩者-取決於您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="bfd78-243">Which path you choose - or both - depends on your application.</span></span> <span data-ttu-id="bfd78-244">我們將在本檔中逐步解說這兩項設定。</span><span class="sxs-lookup"><span data-stu-id="bfd78-244">We'll walk through both configurations in this document.</span></span>

<span data-ttu-id="bfd78-245">**呈現全像攝影效果的遮蔽緩衝區**</span><span class="sxs-lookup"><span data-stu-id="bfd78-245">**Rendering occlusion buffers for holographic effect**</span></span>

<span data-ttu-id="bfd78-246">從清除目前虛擬攝影機的呈現目標視圖開始。</span><span class="sxs-lookup"><span data-stu-id="bfd78-246">Start by clearing the render target view for the current virtual camera.</span></span>

<span data-ttu-id="bfd78-247">從 AppMain:</span><span class="sxs-lookup"><span data-stu-id="bfd78-247">From AppMain.cpp:</span></span>

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

<span data-ttu-id="bfd78-248">這是「預先呈現」階段。</span><span class="sxs-lookup"><span data-stu-id="bfd78-248">This is a "pre-rendering" pass.</span></span> <span data-ttu-id="bfd78-249">在這裡, 我們會要求網格轉譯器只呈現深度, 藉以建立遮蔽緩衝區。</span><span class="sxs-lookup"><span data-stu-id="bfd78-249">Here, we create an occlusion buffer by asking the mesh renderer to render only depth.</span></span> <span data-ttu-id="bfd78-250">在此設定中, 我們不會附加轉譯目標視圖, 而網格轉譯器會將圖元著色器階段設定為**nullptr** , 讓 GPU 不會干擾繪製圖元。</span><span class="sxs-lookup"><span data-stu-id="bfd78-250">In this configuration, we don't attach a render target view, and the mesh renderer sets the pixel shader stage to **nullptr** so that the GPU doesn't bother to draw pixels.</span></span> <span data-ttu-id="bfd78-251">幾何會柵格化至深度緩衝區, 而圖形管線會在該處停止。</span><span class="sxs-lookup"><span data-stu-id="bfd78-251">The geometry will be rasterized to the depth buffer, and the graphics pipeline will stop there.</span></span>

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

<span data-ttu-id="bfd78-252">我們可以在表面對應遮蔽緩衝區中, 以額外的深度測試來繪製全息影像。</span><span class="sxs-lookup"><span data-stu-id="bfd78-252">We can draw holograms with an extra depth test against the Surface Mapping occlusion buffer.</span></span> <span data-ttu-id="bfd78-253">在此程式碼範例中, 我們會以不同的色彩呈現 cube 上的圖元 (如果它們位於表面後面)。</span><span class="sxs-lookup"><span data-stu-id="bfd78-253">In this code sample, we render pixels on the cube a different color if they are behind a surface.</span></span>

<span data-ttu-id="bfd78-254">從 AppMain:</span><span class="sxs-lookup"><span data-stu-id="bfd78-254">From AppMain.cpp:</span></span>

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

<span data-ttu-id="bfd78-255">以 SpecialEffectPixelShader 的程式碼為基礎。 hlsl:</span><span class="sxs-lookup"><span data-stu-id="bfd78-255">Based on code from SpecialEffectPixelShader.hlsl:</span></span>

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

<span data-ttu-id="bfd78-256">**注意：** 針對我們的**GatherDepthLess**常式, 請參閱表面對應程式碼範例:SpecialEffectPixelShader. hlsl。</span><span class="sxs-lookup"><span data-stu-id="bfd78-256">**Note:** For our **GatherDepthLess** routine, see the Surface Mapping code sample: SpecialEffectPixelShader.hlsl.</span></span>

<span data-ttu-id="bfd78-257">**將 surface 網格資料轉譯為顯示**</span><span class="sxs-lookup"><span data-stu-id="bfd78-257">**Rendering surface mesh data to the display**</span></span>

<span data-ttu-id="bfd78-258">我們也可以只將 surface 網格繪製到身歷聲顯示器緩衝區。</span><span class="sxs-lookup"><span data-stu-id="bfd78-258">We can also just draw the surface meshes to the stereo display buffers.</span></span> <span data-ttu-id="bfd78-259">我們選擇以光源繪製完整的臉部, 但是您可以自由繪製線框、在轉譯前處理網格、套用材質圖等等。</span><span class="sxs-lookup"><span data-stu-id="bfd78-259">We chose to draw full faces with lighting, but you're free to draw wireframe, process meshes before rendering, apply a texture map, and so on.</span></span>

<span data-ttu-id="bfd78-260">在這裡, 我們的程式碼範例會指示網格轉譯器繪製集合。</span><span class="sxs-lookup"><span data-stu-id="bfd78-260">Here, our code sample tells the mesh renderer to draw the collection.</span></span> <span data-ttu-id="bfd78-261">這次我們不指定深度專用的階段, 因此它會附加圖元著色器, 並使用我們為目前虛擬攝影機指定的目標來完成轉譯管線。</span><span class="sxs-lookup"><span data-stu-id="bfd78-261">This time we don't specify a depth-only pass, so it will attach a pixel shader and complete the rendering pipeline using the targets that we specified for the current virtual camera.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="bfd78-262">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bfd78-262">See also</span></span>
* [<span data-ttu-id="bfd78-263">建立全像攝影 DirectX 專案</span><span class="sxs-lookup"><span data-stu-id="bfd78-263">Creating a holographic DirectX project</span></span>](creating-a-holographic-directx-project.md)
* [<span data-ttu-id="bfd78-264">Windows 感知空間 API</span><span class="sxs-lookup"><span data-stu-id="bfd78-264">Windows.Perception.Spatial API</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
