---
title: Unity 中的空間對應
description: 在 Unity 中呈現和與您在世界各地的真實幾何進行衝突。
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, 空間對應, 轉譯器, 碰撞器, 網格, 掃描, 元件
ms.openlocfilehash: 8f7bad1651ab31b2e83ad9d9c8f465547fbbdc5a
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148643"
---
# <a name="spatial-mapping-in-unity"></a><span data-ttu-id="29534-104">Unity 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="29534-104">Spatial mapping in Unity</span></span>

<span data-ttu-id="29534-105">本主題說明如何在您的 Unity 專案中使用[空間對應](spatial-mapping.md)、抓取代表 HoloLens 裝置周圍表面的三角形網格, 以進行放置、遮蔽、房間分析等等。</span><span class="sxs-lookup"><span data-stu-id="29534-105">This topic describes how to use [spatial mapping](spatial-mapping.md) in your Unity project, retrieving triangle meshes that represent the surfaces in the world around a HoloLens device, for placement, occlusion, room analysis and more.</span></span>

<span data-ttu-id="29534-106">Unity 包含空間對應的完整支援, 這會以下列方式公開給開發人員:</span><span class="sxs-lookup"><span data-stu-id="29534-106">Unity includes full support for spatial mapping, which is exposed to developers in the following ways:</span></span>
1. <span data-ttu-id="29534-107">MixedRealityToolkit 中可用的空間對應元件, 可為開始使用空間對應提供便利快速的路徑</span><span class="sxs-lookup"><span data-stu-id="29534-107">Spatial mapping components available in the MixedRealityToolkit, which provide a convenient and rapid path for getting started with spatial mapping</span></span>
2. <span data-ttu-id="29534-108">較低層級的空間對應 Api, 可提供完整控制, 並啟用更複雜的應用程式特定自訂</span><span class="sxs-lookup"><span data-stu-id="29534-108">Lower-level spatial mapping APIs, which provide full control and enable more sophisticated application specific customization</span></span>

<span data-ttu-id="29534-109">若要在您的應用程式中使用空間對應, 必須在您的 Package.appxmanifest.xml 中設定 spatialPerception 功能。</span><span class="sxs-lookup"><span data-stu-id="29534-109">To use spatial mapping in your app, the spatialPerception capability needs to be set in your AppxManifest.</span></span>

## <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="29534-110">設定 SpatialPerception 功能</span><span class="sxs-lookup"><span data-stu-id="29534-110">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="29534-111">為了讓應用程式使用空間對應資料, 必須啟用 SpatialPerception 功能。</span><span class="sxs-lookup"><span data-stu-id="29534-111">In order for an app to consume spatial mapping data, the SpatialPerception capability must be enabled.</span></span>

<span data-ttu-id="29534-112">如何啟用 SpatialPerception 功能:</span><span class="sxs-lookup"><span data-stu-id="29534-112">How to enable the SpatialPerception capability:</span></span>
1. <span data-ttu-id="29534-113">在 Unity 編輯器中, 開啟 [ **Player 設定**] 窗格 (編輯 > 專案設定 > Player)</span><span class="sxs-lookup"><span data-stu-id="29534-113">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="29534-114">按一下 [ **Windows Store** ] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="29534-114">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="29534-115">展開 [**發行設定]** , 然後檢查 [**功能]** 清單中的 [ **SpatialPerception]** 功能</span><span class="sxs-lookup"><span data-stu-id="29534-115">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

<span data-ttu-id="29534-116">請注意, 如果您已經將 Unity 專案匯出至 Visual Studio 方案, 您必須匯出到新的資料夾, 或在[Visual Studio 的 package.appxmanifest.xml 中手動設定這項功能](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)。</span><span class="sxs-lookup"><span data-stu-id="29534-116">Note that if you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

<span data-ttu-id="29534-117">空間對應也需要至少10.0.10586.0 的 MaxVersionTested:</span><span class="sxs-lookup"><span data-stu-id="29534-117">Spatial mapping also requires a MaxVersionTested of at least 10.0.10586.0:</span></span>
1. <span data-ttu-id="29534-118">在 Visual Studio 中, 以滑鼠右鍵按一下方案總管中的 [ **package.appxmanifest.xml** ], 然後選取 [**查看程式碼**]</span><span class="sxs-lookup"><span data-stu-id="29534-118">In Visual Studio, right click on **Package.appxmanifest** in the Solution Explorer and select **View Code**</span></span>
2. <span data-ttu-id="29534-119">找出指定**y**並將**MaxVersionTested = "10.0.10240.0"** 變更為**MaxVersionTested = "10.0.10586.0"** 的程式程式碼</span><span class="sxs-lookup"><span data-stu-id="29534-119">Find the line specifying **TargetDeviceFamily** and change **MaxVersionTested="10.0.10240.0"** to **MaxVersionTested="10.0.10586.0"**</span></span>
3. <span data-ttu-id="29534-120">**儲存**封裝. package.appxmanifest.xml。</span><span class="sxs-lookup"><span data-stu-id="29534-120">**Save** the Package.appxmanifest.</span></span>

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a><span data-ttu-id="29534-121">開始使用 Unity 的內建空間對應元件</span><span class="sxs-lookup"><span data-stu-id="29534-121">Getting started with Unity's built-in spatial mapping components</span></span>

<span data-ttu-id="29534-122">Unity 提供2個元件, 可讓您輕鬆地將空間對應新增至您的應用程式、**空間對應**轉譯器和**空間對應碰撞**器。</span><span class="sxs-lookup"><span data-stu-id="29534-122">Unity offers 2 components for easily adding spatial mapping to your app, **Spatial Mapping Renderer** and **Spatial Mapping Collider**.</span></span>

### <a name="spatial-mapping-renderer"></a><span data-ttu-id="29534-123">空間對應轉譯器</span><span class="sxs-lookup"><span data-stu-id="29534-123">Spatial Mapping Renderer</span></span>

<span data-ttu-id="29534-124">空間對應轉譯器可讓您呈現空間對應網格的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="29534-124">The Spatial Mapping Renderer allows for visualization of the spatial mapping mesh.</span></span>

![Unity 中的空間對應轉譯器](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a><span data-ttu-id="29534-126">空間對應碰撞</span><span class="sxs-lookup"><span data-stu-id="29534-126">Spatial Mapping Collider</span></span>

<span data-ttu-id="29534-127">空間對應碰撞程式可讓您使用空間對應網格, 進行全像物理的內容 (或字元) 互動。</span><span class="sxs-lookup"><span data-stu-id="29534-127">The Spatial Mapping Collider allows for holographic content (or character) interaction, such as physics, with the spatial mapping mesh.</span></span>

![Unity 中的空間對應碰撞](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a><span data-ttu-id="29534-129">使用內建空間對應元件</span><span class="sxs-lookup"><span data-stu-id="29534-129">Using the built-in spatial mapping components</span></span>

<span data-ttu-id="29534-130">如果您想要視覺化和互動實體表面, 可以將這兩個元件新增至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="29534-130">You may add both components to your app if you'd like to both visualize and interact with physical surfaces.</span></span>

<span data-ttu-id="29534-131">若要在 Unity 應用程式中使用這兩個元件:</span><span class="sxs-lookup"><span data-stu-id="29534-131">To use these two components in your Unity app:</span></span>
1. <span data-ttu-id="29534-132">在您要偵測空間表面網格的區域中央選取 GameObject。</span><span class="sxs-lookup"><span data-stu-id="29534-132">Select a GameObject at the center of the area in which you'd like to detect spatial surface meshes.</span></span>
2. <span data-ttu-id="29534-133">在 [偵測器] 視窗中,**新增元件** >  **XR**  > **空間對應碰撞** 器或**空間對應**轉譯器。</span><span class="sxs-lookup"><span data-stu-id="29534-133">In the Inspector window, **Add Component** > **XR** > **Spatial Mapping Collider** or **Spatial Mapping Renderer**.</span></span>

<span data-ttu-id="29534-134">您可以在<a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity 檔網站</a>找到如何使用這些元件的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="29534-134">You can find more details on how to use these components at the <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity documentation site</a>.</span></span>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a><span data-ttu-id="29534-135">超越內建的空間對應元件</span><span class="sxs-lookup"><span data-stu-id="29534-135">Going beyond the built-in spatial mapping components</span></span>

<span data-ttu-id="29534-136">這些元件可讓您輕鬆地拖放, 以開始使用空間對應。</span><span class="sxs-lookup"><span data-stu-id="29534-136">These components make it drag-and-drop easy to get started with Spatial Mapping.</span></span> <span data-ttu-id="29534-137"> 當您想要進一步瞭解時, 有兩個主要路徑可供探索:</span><span class="sxs-lookup"><span data-stu-id="29534-137"> When you want to go further, there are two main paths to explore:</span></span>
* <span data-ttu-id="29534-138">若要執行您自己的較低層級的網格處理, 請參閱下方關於低層級空間對應腳本 API 的小節。</span><span class="sxs-lookup"><span data-stu-id="29534-138">To do your own lower-level mesh processing, see the section below about the low-level Spatial Mapping script API.</span></span>
* <span data-ttu-id="29534-139">若要執行更高層級的網格分析, 請參閱下方有關<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>中 SpatialUnderstanding 程式庫的章節。</span><span class="sxs-lookup"><span data-stu-id="29534-139">To do higher-level mesh analysis, see the section below about the SpatialUnderstanding library in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span></span>

## <a name="using-the-low-level-unity-spatial-mapping-api"></a><span data-ttu-id="29534-140">使用低層級 Unity 空間對應 API</span><span class="sxs-lookup"><span data-stu-id="29534-140">Using the low-level Unity Spatial Mapping API</span></span>

<span data-ttu-id="29534-141">如果您需要更多的控制, 而不是從空間對應轉譯器和空間對應碰撞器元件取得, 您可以使用低層級的空間對應腳本 Api。</span><span class="sxs-lookup"><span data-stu-id="29534-141">If you need more control than you get from the Spatial Mapping Renderer and Spatial Mapping Collider components, you can use the low-level Spatial Mapping script APIs.</span></span>

<span data-ttu-id="29534-142">**命名空間：**  *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="29534-142">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="29534-143">**類型**:*SurfaceObserver*、 *SurfaceChange*、 *SurfaceData*、 *SurfaceId*</span><span class="sxs-lookup"><span data-stu-id="29534-143">**Types**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span></span>

<span data-ttu-id="29534-144">以下是使用空間對應 Api 之應用程式的建議流程概述。</span><span class="sxs-lookup"><span data-stu-id="29534-144">The following is an outline of the suggested flow for an application that uses the spatial mapping APIs.</span></span>

### <a name="set-up-the-surfaceobservers"></a><span data-ttu-id="29534-145">設定 SurfaceObserver</span><span class="sxs-lookup"><span data-stu-id="29534-145">Set up the SurfaceObserver(s)</span></span>

<span data-ttu-id="29534-146">針對您需要空間對應資料的每個應用程式定義區域, 具現化一個 SurfaceObserver 物件。</span><span class="sxs-lookup"><span data-stu-id="29534-146">Instantiate one SurfaceObserver object for each application-defined region of space that you need spatial mapping data for.</span></span>

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

<span data-ttu-id="29534-147">藉由呼叫 SetVolumeAsSphere、SetVolumeAsAxisAlignedBox、SetVolumeAsOrientedBox 或 SetVolumeAsFrustum, 指定每個 SurfaceObserver 物件將為其提供資料的空間區域。</span><span class="sxs-lookup"><span data-stu-id="29534-147">Specify the region of space that each SurfaceObserver object will provide data for by calling either SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, or SetVolumeAsFrustum.</span></span> <span data-ttu-id="29534-148">您只要再次呼叫其中一個方法, 就可以重新定義未來的空間區域。</span><span class="sxs-lookup"><span data-stu-id="29534-148">You can redefine the region of space in the future by simply calling one of these methods again.</span></span>

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

<span data-ttu-id="29534-149">當您呼叫 SurfaceObserver () 時, 您必須針對空間對應系統有新資訊的空間, 在 SurfaceObserver 區域中提供每個空間介面的處理常式。</span><span class="sxs-lookup"><span data-stu-id="29534-149">When you call SurfaceObserver.Update(), you must provide a handler for each spatial surface in the SurfaceObserver's region of space that the spatial mapping system has new information for.</span></span> <span data-ttu-id="29534-150">處理常式會接收一個空間介面的:</span><span class="sxs-lookup"><span data-stu-id="29534-150">The handler receives, for one spatial surface:</span></span>

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a><span data-ttu-id="29534-151">處理 Surface 變更</span><span class="sxs-lookup"><span data-stu-id="29534-151">Handling Surface Changes</span></span>

<span data-ttu-id="29534-152">有幾個主要案例需要處理。</span><span class="sxs-lookup"><span data-stu-id="29534-152">There are several main cases to handle.</span></span> <span data-ttu-id="29534-153">已新增 & 更新, 可使用相同的程式碼路徑並加以移除。</span><span class="sxs-lookup"><span data-stu-id="29534-153">Added & Updated which can use the same code path and Removed.</span></span>
* <span data-ttu-id="29534-154">在範例中新增的 & 更新案例中, 我們會從字典新增或取得代表此網格的 GameObject、使用必要的元件建立 SurfaceData 結構, 然後呼叫 RequestMeshDataAsync 將網格資料填入 GameObject 中, 然後場景中的位置。</span><span class="sxs-lookup"><span data-stu-id="29534-154">In the Added & Updated cases in the example, we add or get the GameObject representing this mesh from the dictionary, create a SurfaceData struct with the necessary components, then call RequestMeshDataAsync to populate the GameObject with the mesh data and position in the scene.</span></span>
* <span data-ttu-id="29534-155">在移除的案例中, 我們會從字典中移除代表此網格的 GameObject, 並將其終結。</span><span class="sxs-lookup"><span data-stu-id="29534-155">In the Removed case, we remove the GameObject representing this mesh from the dictionary and destroy it.</span></span>

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects = 
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

   private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
   {
       switch (changeType)
       {
           case SurfaceChange.Added:
           case SurfaceChange.Updated:
               if (!spatialMeshObjects.ContainsKey(surfaceId))
               {
                   spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                   spatialMeshObjects[surfaceId].transform.parent = this.transform;
                   spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
               }
               GameObject target = spatialMeshObjects[surfaceId];
               SurfaceData sd = new SurfaceData(
                   //the surface id returned from the system
                   surfaceId,
                   //the mesh filter that is populated with the spatial mapping data for this mesh
                   target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                   //the world anchor used to position the spatial mapping mesh in the world
                   target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                   //the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                   target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                   //triangles per cubic meter requested for this mesh
                   1000,
                   //bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                   true
                   );

               SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
               break;
           case SurfaceChange.Removed:
               var obj = spatialMeshObjects[surfaceId];
               spatialMeshObjects.Remove(surfaceId);
               if (obj != null)
               {
                   GameObject.Destroy(obj);
               }
               break;
           default:
               break;
       }
   }
```

### <a name="handling-data-ready"></a><span data-ttu-id="29534-156">處理資料就緒</span><span class="sxs-lookup"><span data-stu-id="29534-156">Handling Data Ready</span></span>

<span data-ttu-id="29534-157">OnDataReady 處理常式會接收 SurfaceData 物件。</span><span class="sxs-lookup"><span data-stu-id="29534-157">The OnDataReady handler receives a SurfaceData object.</span></span> <span data-ttu-id="29534-158">其所包含的 WorldAnchor、MeshFilter 和 (選擇性) MeshCollider 物件會反映相關聯空間介面的最新狀態。</span><span class="sxs-lookup"><span data-stu-id="29534-158">The WorldAnchor, MeshFilter and (optionally) MeshCollider objects it contains reflect the latest state of the associated spatial surface.</span></span> <span data-ttu-id="29534-159">藉由存取 MeshFilter 物件的網格成員, 選擇性地執行網格資料的分析和 (或)[處理](spatial-mapping.md#mesh-processing)。</span><span class="sxs-lookup"><span data-stu-id="29534-159">Optionally perform analysis and/or [processing](spatial-mapping.md#mesh-processing) of the mesh data by accessing the Mesh member of the MeshFilter object.</span></span> <span data-ttu-id="29534-160">使用最新的網格呈現空間介面, 並選擇性地使用它來進行物理衝突和 raycasts。</span><span class="sxs-lookup"><span data-stu-id="29534-160">Render the spatial surface with the latest mesh and (optionally) use it for physics collisions and raycasts.</span></span> <span data-ttu-id="29534-161">請務必確認 SurfaceData 的內容不是 null。</span><span class="sxs-lookup"><span data-stu-id="29534-161">It's important to confirm that the contents of the SurfaceData are not null.</span></span>

### <a name="start-processing-on-updates"></a><span data-ttu-id="29534-162">開始處理更新</span><span class="sxs-lookup"><span data-stu-id="29534-162">Start processing on updates</span></span>

<span data-ttu-id="29534-163">應該在延遲 (而非每個框架) 上呼叫 SurfaceObserver ()。</span><span class="sxs-lookup"><span data-stu-id="29534-163">SurfaceObserver.Update() should be called on a delay, not every frame.</span></span>

```cs
void Start () {
    ...
     StartCoroutine(UpdateLoop());
}

 IEnumerator UpdateLoop()
    {
        var wait = new WaitForSeconds(2.5f);
        while(true)
        {
            surfaceObserver.Update(OnSurfaceChanged);
            yield return wait;
        }
    }
```

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a><span data-ttu-id="29534-164">較高層級的網格分析:SpatialUnderstanding</span><span class="sxs-lookup"><span data-stu-id="29534-164">Higher-level mesh analysis: SpatialUnderstanding</span></span>

<span data-ttu-id="29534-165"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>是一組實用的公用程式程式碼, 適用于以全像攝影 Unity api 為基礎的全像攝影開發。</span><span class="sxs-lookup"><span data-stu-id="29534-165">The <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> is a collection of helpful utility code for holographic development built upon the holographic Unity APIs.</span></span>

### <a name="spatial-understanding"></a><span data-ttu-id="29534-166">空間理解</span><span class="sxs-lookup"><span data-stu-id="29534-166">Spatial Understanding</span></span>

<span data-ttu-id="29534-167">將全息影像放在實體世界中時, 通常會想要超越空間對應的網格和 surface 平面。</span><span class="sxs-lookup"><span data-stu-id="29534-167">When placing holograms in the physical world it is often desirable to go beyond spatial mapping’s mesh and surface planes.</span></span> <span data-ttu-id="29534-168">當放置完成 cti 時, 會需要更高層級的環境理解。</span><span class="sxs-lookup"><span data-stu-id="29534-168">When placement is done procedurally, a higher level of environmental understanding is desirable.</span></span> <span data-ttu-id="29534-169">這通常需要做出關於樓層、上限和牆的決策。</span><span class="sxs-lookup"><span data-stu-id="29534-169">This usually requires making decisions about what is floor, ceiling, and walls.</span></span> <span data-ttu-id="29534-170">此外, 也能夠優化一組放置條件約束, 以判斷全像攝影物件的最理想實體位置。</span><span class="sxs-lookup"><span data-stu-id="29534-170">In addition, the ability to optimize against a set of placement constraints to determining the most desirable physical locations for holographic objects.</span></span>

<span data-ttu-id="29534-171">在 Conker 和片段的開發期間, Asobo 工作室面臨此問題的原因, 開發出空間規劃求解以實現此目的。</span><span class="sxs-lookup"><span data-stu-id="29534-171">During the development of Young Conker and Fragments, Asobo Studios faced this problem head on, developing a room solver for this purpose.</span></span> <span data-ttu-id="29534-172">這些遊戲中的每一個都有遊戲特有的需求, 但它們分享了核心空間的理解技術。</span><span class="sxs-lookup"><span data-stu-id="29534-172">Each of these games had game specific needs, but they shared core spatial understanding technology.</span></span> <span data-ttu-id="29534-173">HoloToolkit. SpatialUnderstanding 程式庫會封裝這項技術, 讓您可以快速地在牆上尋找空的空間、將物件放在最上方、找出放置於字元的位置, 以及其他許多空間理解查詢。</span><span class="sxs-lookup"><span data-stu-id="29534-173">The HoloToolkit.SpatialUnderstanding library encapsulates this technology, allowing you to quickly find empty spaces on the walls, place objects on the ceiling, identify placed for character to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="29534-174">包含所有原始程式碼, 讓您可以依據自己的需求進行自訂, 並與您的社區分享您的改進。</span><span class="sxs-lookup"><span data-stu-id="29534-174">All of the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="29534-175">此C++規劃求解的程式碼已包裝成 UWP dll, 並使用包含在 MixedRealityToolkit 內的 prefab, 向 Unity 公開。</span><span class="sxs-lookup"><span data-stu-id="29534-175">The code for the C++ solver has been wrapped into a UWP dll and exposed to Unity with a drop in prefab contained within the MixedRealityToolkit.</span></span>

### <a name="understanding-modules"></a><span data-ttu-id="29534-176">瞭解模組</span><span class="sxs-lookup"><span data-stu-id="29534-176">Understanding Modules</span></span>

<span data-ttu-id="29534-177">模組所公開的主要介面有三個: 簡單表面和空間查詢的拓撲、物件偵測的圖形, 以及物件位置規劃求解, 用於以條件約束為基礎的物件集合位置。</span><span class="sxs-lookup"><span data-stu-id="29534-177">There are three primary interfaces exposed by the module: topology for simple surface and spatial queries, shape for object detection, and the object placement solver for constraint based placement of object sets.</span></span> <span data-ttu-id="29534-178">以下說明每一種。</span><span class="sxs-lookup"><span data-stu-id="29534-178">Each of these is described below.</span></span> <span data-ttu-id="29534-179">除了三個主要模組介面, 光線轉型介面可以用來取出標記的表面型別, 也可以將自訂的防水 playspace 網格複製出來。</span><span class="sxs-lookup"><span data-stu-id="29534-179">In addition to the three primary module interfaces, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="29534-180">光線轉換</span><span class="sxs-lookup"><span data-stu-id="29534-180">Ray Casting</span></span>

<span data-ttu-id="29534-181">在掃描完房間並完成後, 就會在內部為地面、上限和牆等表面產生標籤。</span><span class="sxs-lookup"><span data-stu-id="29534-181">After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="29534-182">"PlayspaceRaycast" 函式會採用光線, 並在光線與已知表面衝突時傳回, 如果是, 則會傳回該介面的相關資訊 (以 "RaycastResult" 為形式)。</span><span class="sxs-lookup"><span data-stu-id="29534-182">The “PlayspaceRaycast” function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a “RaycastResult”.</span></span>

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology, 
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and 
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface, 
                    //  but vertical surface that looks like a 
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown 
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

<span data-ttu-id="29534-183">就內部而言, 會針對 playspace 的計算8cm 立方體素標記法來計算 raycast。</span><span class="sxs-lookup"><span data-stu-id="29534-183">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="29534-184">每個體素都包含一組具有已處理拓撲資料的 surface 元素 (也稱為 surfels)。</span><span class="sxs-lookup"><span data-stu-id="29534-184">Each voxel contains a set of surface elements with processed topology data (aka surfels).</span></span> <span data-ttu-id="29534-185">交集的體素資料格內所包含的 surfels 會進行比較, 並使用最符合的方式來查閱拓撲資訊。</span><span class="sxs-lookup"><span data-stu-id="29534-185">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="29534-186">此拓撲資料包含以 "SurfaceTypes" 列舉形式傳回的標籤, 以及交集資料表面的介面區。</span><span class="sxs-lookup"><span data-stu-id="29534-186">This topology data contains the labeling returned in the form of the “SurfaceTypes” enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="29534-187">在 Unity 範例中, 游標會將光線轉換成每個畫面格。</span><span class="sxs-lookup"><span data-stu-id="29534-187">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="29534-188">首先, 針對 Unity 的 colliders。</span><span class="sxs-lookup"><span data-stu-id="29534-188">First, against Unity’s colliders.</span></span> <span data-ttu-id="29534-189">第二, 針對瞭解模組的世界標記法。</span><span class="sxs-lookup"><span data-stu-id="29534-189">Second, against the understanding module’s world representation.</span></span> <span data-ttu-id="29534-190">最後, 再按一次 UI 元素。</span><span class="sxs-lookup"><span data-stu-id="29534-190">And finally, again UI elements.</span></span> <span data-ttu-id="29534-191">在此應用程式中, UI 會取得優先順序, 接下來是瞭解結果, 最後是 Unity 的 colliders。</span><span class="sxs-lookup"><span data-stu-id="29534-191">In this application, UI gets priority, next the understanding result, and lastly, Unity’s colliders.</span></span> <span data-ttu-id="29534-192">SurfaceType 會回報為游標旁的文字。</span><span class="sxs-lookup"><span data-stu-id="29534-192">The SurfaceType is reported as text next to the cursor.</span></span>

<span data-ttu-id="29534-193">![介面類別型在游標旁標示](images/su-raycastresults-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="29534-193">![Surface type is labeled next to the cursor](images/su-raycastresults-300px.jpg)</span></span><br>
<span data-ttu-id="29534-194">*介面類別型在游標旁標示*</span><span class="sxs-lookup"><span data-stu-id="29534-194">*Surface type is labeled next to the cursor*</span></span>

### <a name="topology-queries"></a><span data-ttu-id="29534-195">拓撲查詢</span><span class="sxs-lookup"><span data-stu-id="29534-195">Topology Queries</span></span>

<span data-ttu-id="29534-196">在 DLL 中, 拓撲管理員會處理環境的標籤。</span><span class="sxs-lookup"><span data-stu-id="29534-196">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="29534-197">如先前所述, 大部分的資料會儲存在 surfels 內, 並包含在體素磁片區中。</span><span class="sxs-lookup"><span data-stu-id="29534-197">As mentioned above, much of the data is stored within surfels, contained within a voxel volume.</span></span> <span data-ttu-id="29534-198">此外, "PlaySpaceInfos" 結構是用來儲存 playspace 的相關資訊, 包括世界對齊 (更多詳細資料, 如下所示)、樓層和上限高度。</span><span class="sxs-lookup"><span data-stu-id="29534-198">In addition, the “PlaySpaceInfos” structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span> <span data-ttu-id="29534-199">啟發學習法是用來決定樓層、上限和牆。</span><span class="sxs-lookup"><span data-stu-id="29534-199">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="29534-200">例如, 具有大於1個 m2 介面區的最大和最低水準表面會視為樓層。</span><span class="sxs-lookup"><span data-stu-id="29534-200">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="29534-201">請注意, 在掃描過程中的相機路徑也會在此程式中使用。</span><span class="sxs-lookup"><span data-stu-id="29534-201">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="29534-202">拓撲管理員所公開的查詢子集會透過 dll 公開。</span><span class="sxs-lookup"><span data-stu-id="29534-202">A subset of the queries exposed by the Topology manager are exposed out through the dll.</span></span> <span data-ttu-id="29534-203">公開的拓撲查詢如下所示。</span><span class="sxs-lookup"><span data-stu-id="29534-203">The exposed topology queries are as follows.</span></span>

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

<span data-ttu-id="29534-204">每個查詢都有一組參數, 特定于查詢類型。</span><span class="sxs-lookup"><span data-stu-id="29534-204">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="29534-205">在下列範例中, 使用者會指定所需磁片區的最小高度 & 寬度、樓層上方的最小放置高度, 以及該磁片區前方的最小間隙量。</span><span class="sxs-lookup"><span data-stu-id="29534-205">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="29534-206">所有的測量單位都是計量。</span><span class="sxs-lookup"><span data-stu-id="29534-206">All measurements are in meters.</span></span>

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="29534-207">這些查詢都會接受預先配置的 "TopologyResult" 結構陣列。</span><span class="sxs-lookup"><span data-stu-id="29534-207">Each of these queries takes a pre-allocated array of “TopologyResult” structures.</span></span> <span data-ttu-id="29534-208">"LocationCount" 參數會指定傳入陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="29534-208">The “locationCount” parameter specifies the length of the passed in array.</span></span> <span data-ttu-id="29534-209">傳回值會報告傳回位置的數目。</span><span class="sxs-lookup"><span data-stu-id="29534-209">The return value reports the number of returned locations.</span></span> <span data-ttu-id="29534-210">這個數位絕不會大於傳入的 "locationCount" 參數。</span><span class="sxs-lookup"><span data-stu-id="29534-210">This number is never greater than the passed in “locationCount” parameter.</span></span>

<span data-ttu-id="29534-211">"TopologyResult" 包含所傳回之磁片區的中心位置、面向的方向 (也就是一般), 以及所找到空間的維度。</span><span class="sxs-lookup"><span data-stu-id="29534-211">The “TopologyResult” contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

<span data-ttu-id="29534-212">請注意, 在 Unity 範例中, 每個查詢都會連結到虛擬 UI 面板中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="29534-212">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="29534-213">範例會將這些查詢的參數硬編碼成合理的值。</span><span class="sxs-lookup"><span data-stu-id="29534-213">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="29534-214">如需更多範例, 請參閱範例程式碼中的 SpaceVisualizer.cs。</span><span class="sxs-lookup"><span data-stu-id="29534-214">See SpaceVisualizer.cs in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="29534-215">圖形查詢</span><span class="sxs-lookup"><span data-stu-id="29534-215">Shape Queries</span></span>

<span data-ttu-id="29534-216">在 dll 內, 圖形分析器 ("ShapeAnalyzer_W") 會使用拓撲分析器比對使用者所定義的自訂圖形。</span><span class="sxs-lookup"><span data-stu-id="29534-216">Inside of the dll, the shape analyzer (“ShapeAnalyzer_W”) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="29534-217">Unity 範例會定義一組圖案, 並透過 [圖形] 索引標籤內的 [應用程式內查詢] 功能表來公開結果。其目的在於, 使用者可以定義自己的物件圖形查詢, 並依其應用程式的需求來使用這些查詢。</span><span class="sxs-lookup"><span data-stu-id="29534-217">The Unity sample defines a set of shapes and exposes the results out through the in-app query menu, within the shape tab. The intention is that the user can define their own object shape queries and make use of those, as needed by their application.</span></span>

<span data-ttu-id="29534-218">請注意, 圖形分析僅適用于水準表面。</span><span class="sxs-lookup"><span data-stu-id="29534-218">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="29534-219">例如, 沙發是由平面上表面和沙發的平面上方所定義。</span><span class="sxs-lookup"><span data-stu-id="29534-219">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="29534-220">圖形查詢會尋找指定大小、高度和外觀範圍的兩個表面, 並對齊並連接兩個表面。</span><span class="sxs-lookup"><span data-stu-id="29534-220">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="29534-221">使用 Api 術語, 沙發基座和後端是圖形元件, 而對齊需求是圖形元件條件約束。</span><span class="sxs-lookup"><span data-stu-id="29534-221">Using the APIs terminology, the couch seat and back top are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="29534-222">在 Unity 範例 (ShapeDefinition.cs) 中定義的範例查詢, 適用于 "sittable" 物件, 如下所示。</span><span class="sxs-lookup"><span data-stu-id="29534-222">An example query defined in the Unity sample (ShapeDefinition.cs), for “sittable” objects is as follows.</span></span>

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

<span data-ttu-id="29534-223">每個形狀查詢都是由一組圖形元件所定義, 每個都有一組元件條件約束和一組圖形條件約束, 以列出元件之間的相依性。</span><span class="sxs-lookup"><span data-stu-id="29534-223">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which listing dependencies between the components.</span></span> <span data-ttu-id="29534-224">這個範例包含單一元件定義中的三個條件約束, 而且元件之間沒有任何圖形條件約束 (因為只有一個元件)。</span><span class="sxs-lookup"><span data-stu-id="29534-224">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="29534-225">相反地, 「沙發」圖形有兩個「圖形」元件和四個「形狀」條件約束。</span><span class="sxs-lookup"><span data-stu-id="29534-225">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="29534-226">請注意, 元件是由使用者的元件清單中的索引所識別 (在此範例中為0和 1)。</span><span class="sxs-lookup"><span data-stu-id="29534-226">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

<span data-ttu-id="29534-227">Unity 模組中提供了包裝函式, 可讓您輕鬆地建立自訂圖形定義。</span><span class="sxs-lookup"><span data-stu-id="29534-227">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="29534-228">元件和圖形條件約束的完整清單可在 "ShapeComponentConstraint" 和 "ShapeConstraint" 結構內的 "SpatialUnderstandingDll.cs" 中找到。</span><span class="sxs-lookup"><span data-stu-id="29534-228">The full list of component and shape constraints can be found in “SpatialUnderstandingDll.cs” within the “ShapeComponentConstraint” and the “ShapeConstraint” structures.</span></span>

<span data-ttu-id="29534-229">![在此介面上找到矩形圖形](images/su-shapequery-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="29534-229">![Rectangle shape is found on this surface](images/su-shapequery-300px.jpg)</span></span><br>
<span data-ttu-id="29534-230">*在此介面上找到矩形圖形*</span><span class="sxs-lookup"><span data-stu-id="29534-230">*Rectangle shape is found on this surface*</span></span>

### <a name="object-placement-solver"></a><span data-ttu-id="29534-231">物件放置規劃求解</span><span class="sxs-lookup"><span data-stu-id="29534-231">Object Placement Solver</span></span>

<span data-ttu-id="29534-232">物件放置規劃求解可用於識別實體空間中的理想位置, 以放置您的物件。</span><span class="sxs-lookup"><span data-stu-id="29534-232">The object placement solver can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="29534-233">在指定物件規則和條件約束的情況下, 規劃求解會尋找最適合的位置。</span><span class="sxs-lookup"><span data-stu-id="29534-233">The solver will find the best fit location given the object rules and constraints.</span></span> <span data-ttu-id="29534-234">此外, 物件查詢會持續存在, 直到使用 "Solver_RemoveObject" 或 "Solver_RemoveAllObjects" 呼叫移除物件為止, 允許受限制的多物件放置。</span><span class="sxs-lookup"><span data-stu-id="29534-234">In addition, object queries persist until the object is removed with “Solver_RemoveObject” or “Solver_RemoveAllObjects” calls, allowing constrained multi-object placement.</span></span> <span data-ttu-id="29534-235">物件放置查詢包含三個部分: 具有參數的放置類型、規則清單和條件約束清單。</span><span class="sxs-lookup"><span data-stu-id="29534-235">Objects placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="29534-236">若要執行查詢, 請使用下列 API。</span><span class="sxs-lookup"><span data-stu-id="29534-236">To run a query, use the following API.</span></span>

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

<span data-ttu-id="29534-237">此函式會接受物件名稱、位置定義, 以及規則和條件約束的清單。</span><span class="sxs-lookup"><span data-stu-id="29534-237">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="29534-238">C#包裝函式提供了結構協助程式函式, 讓規則和條件約束結構更輕鬆。</span><span class="sxs-lookup"><span data-stu-id="29534-238">The C# wrappers provides construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="29534-239">放置定義包含查詢類型, 也就是下列其中一項。</span><span class="sxs-lookup"><span data-stu-id="29534-239">The placement definition contains the query type – that is, one of the following.</span></span>

```cpp
public enum PlacementType
            {
                Place_OnFloor,
                Place_OnWall,
                Place_OnCeiling,
                Place_OnShape,
                Place_OnEdge,
                Place_OnFloorAndCeiling,
                Place_RandomInAir,
                Place_InMidAir,
                Place_UnderFurnitureEdge,
            };
```

<span data-ttu-id="29534-240">每個放置類型都具有類型特有的一組參數。</span><span class="sxs-lookup"><span data-stu-id="29534-240">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="29534-241">"ObjectPlacementDefinition" 結構包含一組用來建立這些定義的靜態 helper 函式。</span><span class="sxs-lookup"><span data-stu-id="29534-241">The “ObjectPlacementDefinition” structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="29534-242">例如, 若要尋找將物件放在樓層的位置, 您可以使用下列函數。</span><span class="sxs-lookup"><span data-stu-id="29534-242">For example, to find a place to put an object on the floor, you can use the following function.</span></span> <span data-ttu-id="29534-243">public static ObjectPlacementDefinition Create_OnFloor (Vector3 halfDims) 除了放置類型之外, 您還可以提供一組規則和條件約束。</span><span class="sxs-lookup"><span data-stu-id="29534-243">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="29534-244">無法違反規則。</span><span class="sxs-lookup"><span data-stu-id="29534-244">Rules cannot be violated.</span></span> <span data-ttu-id="29534-245">接著, 符合類型和規則的可能位置位置會針對條件約束集合進行優化, 以便選取最佳的放置位置。</span><span class="sxs-lookup"><span data-stu-id="29534-245">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints in order to select the optimal placement location.</span></span> <span data-ttu-id="29534-246">每個規則和條件約束都可以由提供的靜態建立函式來建立。</span><span class="sxs-lookup"><span data-stu-id="29534-246">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="29534-247">以下提供範例規則和條件約束結構函數。</span><span class="sxs-lookup"><span data-stu-id="29534-247">An example rule and constraint construction function is provided below.</span></span>

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="29534-248">下列物件放置查詢正在尋找一個位置, 將半計量 cube 放在表面的邊緣, 而不是從其他先前放置的物件, 靠近房間的中心。</span><span class="sxs-lookup"><span data-stu-id="29534-248">The below object placement query is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>

```cs
List<ObjectPlacementRule> rules = 
    new List<ObjectPlacementRule>() {
        ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
    };

List<ObjectPlacementConstraint> constraints = 
    new List<ObjectPlacementConstraint> {
        ObjectPlacementConstraint.Create_NearCenter(),
    };

Solver_PlaceObject(
    “MyCustomObject”,
    new ObjectPlacementDefinition.Create_OnEdge(
        new Vector3(0.25f, 0.25f, 0.25f), 
        new Vector3(0.25f, 0.25f, 0.25f)),
    rules.Count,
    UnderstandingDLL.PinObject(rules.ToArray()),
    constraints.Count,
    UnderstandingDLL.PinObject(constraints.ToArray()),
    UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

<span data-ttu-id="29534-249">如果成功, 則會傳回包含放置位置、維度和方向的 "ObjectPlacementResult" 結構。</span><span class="sxs-lookup"><span data-stu-id="29534-249">If successful, a “ObjectPlacementResult” structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="29534-250">此外, 放置會加入至 dll 的已放置物件的內部清單。</span><span class="sxs-lookup"><span data-stu-id="29534-250">In addition, the placement is added to the dll’s internal list of placed objects.</span></span> <span data-ttu-id="29534-251">後續的放置查詢將會將此物件列入考慮。</span><span class="sxs-lookup"><span data-stu-id="29534-251">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="29534-252">Unity 範例中的 "LevelSolver.cs" 檔案包含更多範例查詢。</span><span class="sxs-lookup"><span data-stu-id="29534-252">The “LevelSolver.cs” file in the Unity sample contains more example queries.</span></span>

<span data-ttu-id="29534-253">![物件位置的結果](images/su-objectplacement-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="29534-253">![Results of object placement](images/su-objectplacement-1000px.jpg)</span></span><br>
<span data-ttu-id="29534-254">*圖 3:藍色方塊從上三個位置查詢的結果, 與相機位置規則的距離*</span><span class="sxs-lookup"><span data-stu-id="29534-254">*Figure 3: The blue boxes how the result from three place on floor queries with away from camera position rules*</span></span>

<span data-ttu-id="29534-255">解決層級或應用程式案例所需之多個物件的放置位置時, 首先要解決不可或缺和大型的物件, 以達到最大的可找到空間的機率。</span><span class="sxs-lookup"><span data-stu-id="29534-255">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects in order to maximizing the probability that a space can be found.</span></span> <span data-ttu-id="29534-256">放置順序很重要。</span><span class="sxs-lookup"><span data-stu-id="29534-256">Placement order is important.</span></span> <span data-ttu-id="29534-257">如果找不到物件位置, 請嘗試較不受限制的設定。</span><span class="sxs-lookup"><span data-stu-id="29534-257">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="29534-258">具有一組回溯設定對於跨多個房間設定支援功能非常重要。</span><span class="sxs-lookup"><span data-stu-id="29534-258">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="29534-259">房間掃描程式</span><span class="sxs-lookup"><span data-stu-id="29534-259">Room Scanning Process</span></span>

<span data-ttu-id="29534-260">雖然 HoloLens 提供的空間對應解決方案的設計是為了符合整個範圍問題空間的需求, 但空間理解模組是為了支援兩個特定遊戲的需求而打造。</span><span class="sxs-lookup"><span data-stu-id="29534-260">While the spatial mapping solution provided by the HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="29534-261">其解決方案是以特定的程式和假設集為結構, 如下所示。</span><span class="sxs-lookup"><span data-stu-id="29534-261">Its solution is structured around a specific process and set of assumptions, summarized below.</span></span>

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

<span data-ttu-id="29534-262">使用者導向的 playspace 「繪製」–在掃描階段, 使用者移動並尋找播放步調, 有效地繪製應該包含的區域。</span><span class="sxs-lookup"><span data-stu-id="29534-262">User driven playspace “painting” – During the scanning phase, the user moves and looks around the plays pace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="29534-263">產生的網格非常重要, 可在此階段提供使用者意見反應。</span><span class="sxs-lookup"><span data-stu-id="29534-263">The generated mesh is important to provide user feedback during this phase.</span></span> <span data-ttu-id="29534-264">室內家用或 office 安裝程式–查詢函式是以適當角度針對平面和牆而設計的。</span><span class="sxs-lookup"><span data-stu-id="29534-264">Indoors home or office setup – The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="29534-265">這是一項軟性限制。</span><span class="sxs-lookup"><span data-stu-id="29534-265">This is a soft limitation.</span></span> <span data-ttu-id="29534-266">不過, 在掃描階段, 主要軸分析會完成, 以優化主要和次要軸的網格鑲嵌。</span><span class="sxs-lookup"><span data-stu-id="29534-266">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span> <span data-ttu-id="29534-267">內含的 SpatialUnderstanding.cs 檔案會管理掃描階段程式。</span><span class="sxs-lookup"><span data-stu-id="29534-267">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="29534-268">它會呼叫下列函數。</span><span class="sxs-lookup"><span data-stu-id="29534-268">It calls the following functions.</span></span>

```
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan – 
    Called each frame to update the scanning process. The camera position and 
    orientation is passed in and is used for the playspace painting process, 
    described above.

GeneratePlayspace_RequestFinish – 
    Called to finalize the playspace. This will use the areas “painted” during 
    the scan phase to define and lock the playspace. The application can query 
    statistics during the scanning phase as well as query the custom mesh for 
    providing user feedback.

Import_UnderstandingMesh – 
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by 
    the module and placed on the understanding prefab will periodically query the 
    custom mesh generated by the process. In addition, this is done once more 
    after scanning has been finalized.
```

<span data-ttu-id="29534-269">由 "SpatialUnderstanding" 行為驅動的掃描流程會呼叫 InitScan, 然後 UpdateScan 每個畫面格。</span><span class="sxs-lookup"><span data-stu-id="29534-269">The scanning flow, driven by the “SpatialUnderstanding” behavior calls InitScan, then UpdateScan each frame.</span></span> <span data-ttu-id="29534-270">當統計資料查詢報告合理的涵蓋範圍時, 允許使用者 airtap 呼叫 RequestFinish, 以指示掃描階段結束。</span><span class="sxs-lookup"><span data-stu-id="29534-270">When the statistics query reports reasonable coverage, the user is allowed to airtap to call RequestFinish to indicate the end of the scanning phase.</span></span> <span data-ttu-id="29534-271">UpdateScan 會繼續呼叫, 直到它的傳回值指出 dll 已完成處理。</span><span class="sxs-lookup"><span data-stu-id="29534-271">UpdateScan continues to be called until it’s return value indicates that the dll has completed processing.</span></span>

### <a name="understanding-mesh"></a><span data-ttu-id="29534-272">瞭解網格</span><span class="sxs-lookup"><span data-stu-id="29534-272">Understanding Mesh</span></span>

<span data-ttu-id="29534-273">瞭解 dll 會在內部將 playspace 儲存為8cm 大小體素 cube 的方格。</span><span class="sxs-lookup"><span data-stu-id="29534-273">The understanding dll internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="29534-274">在掃描的初始部分期間, 主要元件分析會完成以判斷房間的軸。</span><span class="sxs-lookup"><span data-stu-id="29534-274">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="29534-275">就內部而言, 它會儲存其對應至這些座標軸的體素空間。</span><span class="sxs-lookup"><span data-stu-id="29534-275">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="29534-276">從體素磁片區解壓縮 isosurface, 大約每秒會產生一次網格。</span><span class="sxs-lookup"><span data-stu-id="29534-276">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span> 

<span data-ttu-id="29534-277">![從體素磁片區產生的網格](images/su-custommesh.jpg)</span><span class="sxs-lookup"><span data-stu-id="29534-277">![Generated mesh produced from the voxel volume](images/su-custommesh.jpg)</span></span><br>
<span data-ttu-id="29534-278">*從體素磁片區產生的網格*</span><span class="sxs-lookup"><span data-stu-id="29534-278">*Generated mesh produced from the voxel volume*</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="29534-279">疑難排解</span><span class="sxs-lookup"><span data-stu-id="29534-279">Troubleshooting</span></span>
* <span data-ttu-id="29534-280">請確定您已設定[SpatialPerception](#setting-the-spatialperception-capability)功能</span><span class="sxs-lookup"><span data-stu-id="29534-280">Ensure you have set the [SpatialPerception](#setting-the-spatialperception-capability) capability</span></span>
* <span data-ttu-id="29534-281">當追蹤遺失時, 下一個 OnSurfaceChanged 事件將會移除所有的網格。</span><span class="sxs-lookup"><span data-stu-id="29534-281">When tracking is lost, the next OnSurfaceChanged event will remove all meshes.</span></span>

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a><span data-ttu-id="29534-282">混合現實工具組中的空間對應</span><span class="sxs-lookup"><span data-stu-id="29534-282">Spatial Mapping in Mixed Reality Toolkit</span></span>
<span data-ttu-id="29534-283">如需搭配使用空間對應與混合現實工具組 v2 的詳細資訊, 請參閱 MRTK 檔的<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">空間感知一節</a>。</span><span class="sxs-lookup"><span data-stu-id="29534-283">For more information on using Spatial Mapping with Mixed Reality Toolkit v2, see the <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Spatial Awareness section</a> of the MRTK docs.</span></span>

## <a name="see-also"></a><span data-ttu-id="29534-284">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29534-284">See also</span></span>
* [<span data-ttu-id="29534-285">MR Spatial 230：空間對應</span><span class="sxs-lookup"><span data-stu-id="29534-285">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="29534-286">座標系統</span><span class="sxs-lookup"><span data-stu-id="29534-286">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="29534-287">Unity 中的座標系統</span><span class="sxs-lookup"><span data-stu-id="29534-287">Coordinate systems in Unity</span></span>](coordinate-systems-in-unity.md)
* <span data-ttu-id="29534-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span><span class="sxs-lookup"><span data-stu-id="29534-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span></span>
* <span data-ttu-id="29534-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine. MeshFilter</a></span><span class="sxs-lookup"><span data-stu-id="29534-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span></span>
* <span data-ttu-id="29534-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine. MeshCollider</a></span><span class="sxs-lookup"><span data-stu-id="29534-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span></span>
* <span data-ttu-id="29534-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine. 界限</a></span><span class="sxs-lookup"><span data-stu-id="29534-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span></span>
