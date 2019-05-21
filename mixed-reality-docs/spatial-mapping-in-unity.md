---
title: 在 Unity 中的空間對應
description: 轉譯和碰撞的真實世界中的幾何周圍 Unity。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、 空間的對應、 轉譯器，collider、 網狀結構、 掃描、 元件
ms.openlocfilehash: f938f5921cb2c06342a9ebcd376d690c10584df9
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2019
ms.locfileid: "59597147"
---
# <a name="spatial-mapping-in-unity"></a><span data-ttu-id="d187e-104">在 Unity 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="d187e-104">Spatial mapping in Unity</span></span>

<span data-ttu-id="d187e-105">本主題描述如何使用[空間對應](spatial-mapping.md)在 Unity 專案中，擷取三角網格，代表在世界各地的 HoloLens 裝置、 位置、 阻擋、 空間分析和更多功能的介面。</span><span class="sxs-lookup"><span data-stu-id="d187e-105">This topic describes how to use [spatial mapping](spatial-mapping.md) in your Unity project, retrieving triangle meshes that represent the surfaces in the world around a HoloLens device, for placement, occlusion, room analysis and more.</span></span>

<span data-ttu-id="d187e-106">Unity 包含空間的對應，以下列方式公開給開發人員的完整支援：</span><span class="sxs-lookup"><span data-stu-id="d187e-106">Unity includes full support for spatial mapping, which is exposed to developers in the following ways:</span></span>
1. <span data-ttu-id="d187e-107">空間對應 MixedRealityToolkit 中可用的元件，提供方便且快速路徑空間的對應使用者入門</span><span class="sxs-lookup"><span data-stu-id="d187e-107">Spatial mapping components available in the MixedRealityToolkit, which provide a convenient and rapid path for getting started with spatial mapping</span></span>
2. <span data-ttu-id="d187e-108">較低層級空間的對應 Api，提供完整控制，並啟用更複雜的應用程式特定的自訂</span><span class="sxs-lookup"><span data-stu-id="d187e-108">Lower-level spatial mapping APIs, which provide full control and enable more sophisticated application specific customization</span></span>

<span data-ttu-id="d187e-109">若要在您的應用程式中使用空間的對應，spatialPerception 功能必須在您 AppxManifest 中設定。</span><span class="sxs-lookup"><span data-stu-id="d187e-109">To use spatial mapping in your app, the spatialPerception capability needs to be set in your AppxManifest.</span></span>

## <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="d187e-110">設定 SpatialPerception 功能</span><span class="sxs-lookup"><span data-stu-id="d187e-110">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="d187e-111">為了讓應用程式來使用空間的對應資料，必須啟用 SpatialPerception 功能。</span><span class="sxs-lookup"><span data-stu-id="d187e-111">In order for an app to consume spatial mapping data, the SpatialPerception capability must be enabled.</span></span>

<span data-ttu-id="d187e-112">如何啟用 SpatialPerception 功能：</span><span class="sxs-lookup"><span data-stu-id="d187e-112">How to enable the SpatialPerception capability:</span></span>
1. <span data-ttu-id="d187e-113">在 Unity 編輯器中，開啟 **[播放程式設定]** 窗格 (編輯 > 專案設定 > 播放器)</span><span class="sxs-lookup"><span data-stu-id="d187e-113">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="d187e-114">按一下 [ **「 Windows 市集 」** ] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="d187e-114">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="d187e-115">依序展開 **「 發佈設定 」** ，並檢查 **"SpatialPerception 」** 中的功能 **「 功能 」** 清單</span><span class="sxs-lookup"><span data-stu-id="d187e-115">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

<span data-ttu-id="d187e-116">請注意，是否您已匯出您的 Unity 專案加入 Visual Studio 方案，您必須匯出新的資料夾或以手動方式[設定這項功能在 Visual Studio 中，AppxManifest](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)。</span><span class="sxs-lookup"><span data-stu-id="d187e-116">Note that if you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

<span data-ttu-id="d187e-117">空間對應也需要至少 10.0.10586.0 的 MaxVersionTested:</span><span class="sxs-lookup"><span data-stu-id="d187e-117">Spatial mapping also requires a MaxVersionTested of at least 10.0.10586.0:</span></span>
1. <span data-ttu-id="d187e-118">在 Visual Studio 中，以滑鼠右鍵按一下**Package.appxmanifest**方案總管 中選取**檢視程式碼**</span><span class="sxs-lookup"><span data-stu-id="d187e-118">In Visual Studio, right click on **Package.appxmanifest** in the Solution Explorer and select **View Code**</span></span>
2. <span data-ttu-id="d187e-119">尋找列指定**TargetDeviceFamily**並變更**MaxVersionTested ="10.0.10240.0 」** 到**MaxVersionTested"uwp,version=10.0.10586.0 」**</span><span class="sxs-lookup"><span data-stu-id="d187e-119">Find the line specifying **TargetDeviceFamily** and change **MaxVersionTested="10.0.10240.0"** to **MaxVersionTested="10.0.10586.0"**</span></span>
3. <span data-ttu-id="d187e-120">**儲存**Package.appxmanifest。</span><span class="sxs-lookup"><span data-stu-id="d187e-120">**Save** the Package.appxmanifest.</span></span>

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a><span data-ttu-id="d187e-121">開始使用 Unity 的內建空間的對應元件</span><span class="sxs-lookup"><span data-stu-id="d187e-121">Getting started with Unity's built-in spatial mapping components</span></span>

<span data-ttu-id="d187e-122">Unity 提供 2 個元件，輕鬆地將空間的對應新增至您的應用程式**空間的對應轉譯器**並**空間的對應 Collider**。</span><span class="sxs-lookup"><span data-stu-id="d187e-122">Unity offers 2 components for easily adding spatial mapping to your app, **Spatial Mapping Renderer** and **Spatial Mapping Collider**.</span></span>

### <a name="spatial-mapping-renderer"></a><span data-ttu-id="d187e-123">空間對應的轉譯器</span><span class="sxs-lookup"><span data-stu-id="d187e-123">Spatial Mapping Renderer</span></span>

<span data-ttu-id="d187e-124">空間對應轉譯器可讓您的空間對應網狀結構的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="d187e-124">The Spatial Mapping Renderer allows for visualization of the spatial mapping mesh.</span></span>

![在 Unity 中的空間對應轉譯器](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a><span data-ttu-id="d187e-126">空間對應 Collider</span><span class="sxs-lookup"><span data-stu-id="d187e-126">Spatial Mapping Collider</span></span>

<span data-ttu-id="d187e-127">空間對應 Collider 能進行全像攝影版的內容 （字元） 互動，例如物理條件，與空間對應網格。</span><span class="sxs-lookup"><span data-stu-id="d187e-127">The Spatial Mapping Collider allows for holographic content (or character) interaction, such as physics, with the spatial mapping mesh.</span></span>

![在 Unity 中的空間對應 Collider](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a><span data-ttu-id="d187e-129">使用內建空間的對應元件</span><span class="sxs-lookup"><span data-stu-id="d187e-129">Using the built-in spatial mapping components</span></span>

<span data-ttu-id="d187e-130">如果您想要以視覺化方式檢視和互動實體介面，您可以將這兩個元件新增至您的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="d187e-130">You may add both components to your app if you'd like to both visualize and interact with physical surfaces.</span></span>

<span data-ttu-id="d187e-131">若要在您的 Unity 應用程式中使用這兩個元件：</span><span class="sxs-lookup"><span data-stu-id="d187e-131">To use these two components in your Unity app:</span></span>
1. <span data-ttu-id="d187e-132">選取您想要偵測空間介面網格所在區域的中心 GameObject。</span><span class="sxs-lookup"><span data-stu-id="d187e-132">Select a GameObject at the center of the area in which you'd like to detect spatial surface meshes.</span></span>
2. <span data-ttu-id="d187e-133">在 [偵測器] 視窗中，**新增元件** > **XR** > **空間的對應 Collider** 或**空間對應的轉譯器**。</span><span class="sxs-lookup"><span data-stu-id="d187e-133">In the Inspector window, **Add Component** > **XR** > **Spatial Mapping Collider** or **Spatial Mapping Renderer**.</span></span>

<span data-ttu-id="d187e-134">您可以深入了解如何使用這些元件<a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity 文件網站</a>。</span><span class="sxs-lookup"><span data-stu-id="d187e-134">You can find more details on how to use these components at the <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity documentation site</a>.</span></span>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a><span data-ttu-id="d187e-135">超越內建空間的對應元件</span><span class="sxs-lookup"><span data-stu-id="d187e-135">Going beyond the built-in spatial mapping components</span></span>

<span data-ttu-id="d187e-136">這些元件讓拖放輕鬆開始使用空間的對應。</span><span class="sxs-lookup"><span data-stu-id="d187e-136">These components make it drag-and-drop easy to get started with Spatial Mapping.</span></span> <span data-ttu-id="d187e-137"> 當您想要更進一步時，有兩個主要路徑來瀏覽：</span><span class="sxs-lookup"><span data-stu-id="d187e-137"> When you want to go further, there are two main paths to explore:</span></span>
* <span data-ttu-id="d187e-138">若要執行您自己的較低層級網格處理，請參閱下節的低層級的空間對應指令碼 API。</span><span class="sxs-lookup"><span data-stu-id="d187e-138">To do your own lower-level mesh processing, see the section below about the low-level Spatial Mapping script API.</span></span>
* <span data-ttu-id="d187e-139">若要進行更高層級的網狀結構分析時，請參閱下一節中的 SpatialUnderstanding 程式庫的相關<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>。</span><span class="sxs-lookup"><span data-stu-id="d187e-139">To do higher-level mesh analysis, see the section below about the SpatialUnderstanding library in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span></span>

## <a name="using-the-low-level-unity-spatial-mapping-api"></a><span data-ttu-id="d187e-140">使用低層級 Unity 空間對應 API</span><span class="sxs-lookup"><span data-stu-id="d187e-140">Using the low-level Unity Spatial Mapping API</span></span>

<span data-ttu-id="d187e-141">如果您需要更多的控制權比您獲得的空間對應的轉譯器和空間的對應 Collider 元件時，您可以使用低層級的空間對應指令碼 Api。</span><span class="sxs-lookup"><span data-stu-id="d187e-141">If you need more control than you get from the Spatial Mapping Renderer and Spatial Mapping Collider components, you can use the low-level Spatial Mapping script APIs.</span></span>

<span data-ttu-id="d187e-142">**命名空間：** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="d187e-142">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="d187e-143">**型別**:*SurfaceObserver*， *SurfaceChange*， *SurfaceData*， *SurfaceId*</span><span class="sxs-lookup"><span data-stu-id="d187e-143">**Types**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span></span>

<span data-ttu-id="d187e-144">以下是使用空間的對應 Api 的應用程式的建議流程的大綱。</span><span class="sxs-lookup"><span data-stu-id="d187e-144">The following is an outline of the suggested flow for an application that uses the spatial mapping APIs.</span></span>

### <a name="set-up-the-surfaceobservers"></a><span data-ttu-id="d187e-145">設定 SurfaceObserver(s)</span><span class="sxs-lookup"><span data-stu-id="d187e-145">Set up the SurfaceObserver(s)</span></span>

<span data-ttu-id="d187e-146">具現化一個 SurfaceObserver 物件所需空間的對應資料空間的每個應用程式定義的區域。</span><span class="sxs-lookup"><span data-stu-id="d187e-146">Instantiate one SurfaceObserver object for each application-defined region of space that you need spatial mapping data for.</span></span>

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

<span data-ttu-id="d187e-147">指定的區域的每個 SurfaceObserver 物件會藉由呼叫 SetVolumeAsSphere、 SetVolumeAsAxisAlignedBox、 SetVolumeAsOrientedBox，還是 SetVolumeAsFrustum 提供資料的空間。</span><span class="sxs-lookup"><span data-stu-id="d187e-147">Specify the region of space that each SurfaceObserver object will provide data for by calling either SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, or SetVolumeAsFrustum.</span></span> <span data-ttu-id="d187e-148">您可以再次呼叫其中一個方法，以重新定義空間在未來的區域。</span><span class="sxs-lookup"><span data-stu-id="d187e-148">You can redefine the region of space in the future by simply calling one of these methods again.</span></span>

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

<span data-ttu-id="d187e-149">當您呼叫 SurfaceObserver.Update() 時，您必須提供處理常式的空間的對應系統具有新資訊的空間 SurfaceObserver 的區域中每個空間的介面。</span><span class="sxs-lookup"><span data-stu-id="d187e-149">When you call SurfaceObserver.Update(), you must provide a handler for each spatial surface in the SurfaceObserver's region of space that the spatial mapping system has new information for.</span></span> <span data-ttu-id="d187e-150">接收處理常式的一個空間介面：</span><span class="sxs-lookup"><span data-stu-id="d187e-150">The handler receives, for one spatial surface:</span></span>

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a><span data-ttu-id="d187e-151">處理介面的變更</span><span class="sxs-lookup"><span data-stu-id="d187e-151">Handling Surface Changes</span></span>

<span data-ttu-id="d187e-152">有數個主要的案例來處理。</span><span class="sxs-lookup"><span data-stu-id="d187e-152">There are several main cases to handle.</span></span> <span data-ttu-id="d187e-153">新增與更新可以使用相同的程式碼的路徑和已移除。</span><span class="sxs-lookup"><span data-stu-id="d187e-153">Added & Updated which can use the same code path and Removed.</span></span>
* <span data-ttu-id="d187e-154">在此範例中新增和 Updated 情況下，我們要新增或取得 GameObject，代表這 mesh 從字典，建立 SurfaceData 結構以所需的元件，然後呼叫以填入與網狀結構資料 GameObject RequestMeshDataAsync 和定位在場景中。</span><span class="sxs-lookup"><span data-stu-id="d187e-154">In the Added & Updated cases in the example, we add or get the GameObject representing this mesh from the dictionary, create a SurfaceData struct with the necessary components, then call RequestMeshDataAsync to populate the GameObject with the mesh data and position in the scene.</span></span>
* <span data-ttu-id="d187e-155">在已移除的案例中，我們可以移除從字典中代表此網格 GameObject 並終結它。</span><span class="sxs-lookup"><span data-stu-id="d187e-155">In the Removed case, we remove the GameObject representing this mesh from the dictionary and destroy it.</span></span>

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

### <a name="handling-data-ready"></a><span data-ttu-id="d187e-156">具備處理資料</span><span class="sxs-lookup"><span data-stu-id="d187e-156">Handling Data Ready</span></span>

<span data-ttu-id="d187e-157">OnDataReady 處理常式會接收 SurfaceData 物件。</span><span class="sxs-lookup"><span data-stu-id="d187e-157">The OnDataReady handler receives a SurfaceData object.</span></span> <span data-ttu-id="d187e-158">WorldAnchor、 MeshFilter 及 （選擇性） 其包含的 MeshCollider 物件會反映相關聯的空間表面的最新狀態。</span><span class="sxs-lookup"><span data-stu-id="d187e-158">The WorldAnchor, MeshFilter and (optionally) MeshCollider objects it contains reflect the latest state of the associated spatial surface.</span></span> <span data-ttu-id="d187e-159">（選擇性） 執行分析和/或[處理](spatial-mapping.md#mesh-processing)藉由存取 MeshFilter 物件的網狀結構成員的網格資料。</span><span class="sxs-lookup"><span data-stu-id="d187e-159">Optionally perform analysis and/or [processing](spatial-mapping.md#mesh-processing) of the mesh data by accessing the Mesh member of the MeshFilter object.</span></span> <span data-ttu-id="d187e-160">呈現與最新的網格空間的介面和 （選擇性） 將它用於物理衝突，raycasts。</span><span class="sxs-lookup"><span data-stu-id="d187e-160">Render the spatial surface with the latest mesh and (optionally) use it for physics collisions and raycasts.</span></span> <span data-ttu-id="d187e-161">請務必確認 SurfaceData 的內容不是 null。</span><span class="sxs-lookup"><span data-stu-id="d187e-161">It's important to confirm that the contents of the SurfaceData are not null.</span></span>

### <a name="start-processing-on-updates"></a><span data-ttu-id="d187e-162">開始處理更新</span><span class="sxs-lookup"><span data-stu-id="d187e-162">Start processing on updates</span></span>

<span data-ttu-id="d187e-163">應該在延遲，而不是每個畫面呼叫 SurfaceObserver.Update()。</span><span class="sxs-lookup"><span data-stu-id="d187e-163">SurfaceObserver.Update() should be called on a delay, not every frame.</span></span>

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

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a><span data-ttu-id="d187e-164">較高層級的網狀結構分析：SpatialUnderstanding</span><span class="sxs-lookup"><span data-stu-id="d187e-164">Higher-level mesh analysis: SpatialUnderstanding</span></span>

<span data-ttu-id="d187e-165"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>是建置在全像攝影版的 Unity Api 的全像攝影版開發的實用公用程式程式碼的集合。</span><span class="sxs-lookup"><span data-stu-id="d187e-165">The <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> is a collection of helpful utility code for holographic development built upon the holographic Unity APIs.</span></span>

### <a name="spatial-understanding"></a><span data-ttu-id="d187e-166">了解空間</span><span class="sxs-lookup"><span data-stu-id="d187e-166">Spatial Understanding</span></span>

<span data-ttu-id="d187e-167">放置在真實世界的全像投影時通常會前往超出空間對應的網狀結構，並呈現平面。</span><span class="sxs-lookup"><span data-stu-id="d187e-167">When placing holograms in the physical world it is often desirable to go beyond spatial mapping’s mesh and surface planes.</span></span> <span data-ttu-id="d187e-168">放置可循序完成之後，較高層級的環境了解將是理想。</span><span class="sxs-lookup"><span data-stu-id="d187e-168">When placement is done procedurally, a higher level of environmental understanding is desirable.</span></span> <span data-ttu-id="d187e-169">這通常需要制定有關什麼是 floor、 ceiling 和牆。</span><span class="sxs-lookup"><span data-stu-id="d187e-169">This usually requires making decisions about what is floor, ceiling, and walls.</span></span> <span data-ttu-id="d187e-170">此外，針對至決定的全像攝影版的物件最迫切需要的實體位置的放置條件約束一組最佳化的能力。</span><span class="sxs-lookup"><span data-stu-id="d187e-170">In addition, the ability to optimize against a set of placement constraints to determining the most desirable physical locations for holographic objects.</span></span>

<span data-ttu-id="d187e-171">在開發期間的 Young Conker 和片段，Asobo Studios 會面臨這個問題標頭，針對此目的開發的空間規劃求解。</span><span class="sxs-lookup"><span data-stu-id="d187e-171">During the development of Young Conker and Fragments, Asobo Studios faced this problem head on, developing a room solver for this purpose.</span></span> <span data-ttu-id="d187e-172">每個遊戲遊戲的特定需求，但它們共用核心空間的了解技術。</span><span class="sxs-lookup"><span data-stu-id="d187e-172">Each of these games had game specific needs, but they shared core spatial understanding technology.</span></span> <span data-ttu-id="d187e-173">程式庫封裝這項技術，可讓您快速尋找空白空間上牆壁，讓物件上，找出 HoloToolkit.SpatialUnderstanding 放置要坐著，字元和各種其他空間的了解查詢。</span><span class="sxs-lookup"><span data-stu-id="d187e-173">The HoloToolkit.SpatialUnderstanding library encapsulates this technology, allowing you to quickly find empty spaces on the walls, place objects on the ceiling, identify placed for character to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="d187e-174">所有來源的程式碼，會包含可讓您根據您的需求進行自訂，並與社群分享您的增強功能。</span><span class="sxs-lookup"><span data-stu-id="d187e-174">All of the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="d187e-175">程式碼C++規劃求解已包裝成 UWP dll 並公開到 Unity prefab 內含 MixedRealityToolkit 下降。</span><span class="sxs-lookup"><span data-stu-id="d187e-175">The code for the C++ solver has been wrapped into a UWP dll and exposed to Unity with a drop in prefab contained within the MixedRealityToolkit.</span></span>

### <a name="understanding-modules"></a><span data-ttu-id="d187e-176">了解模組</span><span class="sxs-lookup"><span data-stu-id="d187e-176">Understanding Modules</span></span>

<span data-ttu-id="d187e-177">有三個模組所公開的主要介面： 簡單的介面和空間查詢、 物體偵測的圖形和物件放置求解器為基礎的條件約束放置物件集的拓撲。</span><span class="sxs-lookup"><span data-stu-id="d187e-177">There are three primary interfaces exposed by the module: topology for simple surface and spatial queries, shape for object detection, and the object placement solver for constraint based placement of object sets.</span></span> <span data-ttu-id="d187e-178">每一種是如下所述。</span><span class="sxs-lookup"><span data-stu-id="d187e-178">Each of these is described below.</span></span> <span data-ttu-id="d187e-179">除了三個主要模組介面中，光跡轉型介面可用來擷取已加上標記的介面型別和自訂 watertight playspace 網格可以複製出來。</span><span class="sxs-lookup"><span data-stu-id="d187e-179">In addition to the three primary module interfaces, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="d187e-180">光跡轉型</span><span class="sxs-lookup"><span data-stu-id="d187e-180">Ray Casting</span></span>

<span data-ttu-id="d187e-181">聊天室已進行掃描而且已完成之後，標籤是內部產生的介面，例如 floor、 ceiling 和牆上。</span><span class="sxs-lookup"><span data-stu-id="d187e-181">After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="d187e-182">「 PlayspaceRaycast"函式會採用無限遠的光線，並傳回如果光線衝突與已知的介面，而且如果是這樣，該介面的 「 RaycastResult"形式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d187e-182">The “PlayspaceRaycast” function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a “RaycastResult”.</span></span>

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

<span data-ttu-id="d187e-183">就內部而言，raycast 會計算針對 playspace 計算立方的 8 cm voxel 表示法。</span><span class="sxs-lookup"><span data-stu-id="d187e-183">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="d187e-184">每個 voxel 包含一組已處理的拓撲資料 (也稱為 surfels) 的介面項目。</span><span class="sxs-lookup"><span data-stu-id="d187e-184">Each voxel contains a set of surface elements with processed topology data (aka surfels).</span></span> <span data-ttu-id="d187e-185">比較交集的 voxel 資料格內所含 surfels 和最符合項目用來查閱拓撲資訊。</span><span class="sxs-lookup"><span data-stu-id="d187e-185">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="d187e-186">此拓撲的資料包含標記傳回 「 SurfaceTypes"列舉的形式，以及在交集的介面的介面區。</span><span class="sxs-lookup"><span data-stu-id="d187e-186">This topology data contains the labeling returned in the form of the “SurfaceTypes” enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="d187e-187">在 Unity 範例中，資料指標會轉換每個畫面格無限遠的光線。</span><span class="sxs-lookup"><span data-stu-id="d187e-187">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="d187e-188">首先，針對 Unity colliders。</span><span class="sxs-lookup"><span data-stu-id="d187e-188">First, against Unity’s colliders.</span></span> <span data-ttu-id="d187e-189">第二，針對了解模組的世界表示法。</span><span class="sxs-lookup"><span data-stu-id="d187e-189">Second, against the understanding module’s world representation.</span></span> <span data-ttu-id="d187e-190">與最後一次 UI 項目。</span><span class="sxs-lookup"><span data-stu-id="d187e-190">And finally, again UI elements.</span></span> <span data-ttu-id="d187e-191">在此應用程式中，UI 取得優先順序，接著了解結果，和最後，Unity colliders。</span><span class="sxs-lookup"><span data-stu-id="d187e-191">In this application, UI gets priority, next the understanding result, and lastly, Unity’s colliders.</span></span> <span data-ttu-id="d187e-192">SurfaceType 會回報為游標後面的文字。</span><span class="sxs-lookup"><span data-stu-id="d187e-192">The SurfaceType is reported as text next to the cursor.</span></span>

<span data-ttu-id="d187e-193">![介面的型別會標示為游標](images/su-raycastresults-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="d187e-193">![Surface type is labeled next to the cursor](images/su-raycastresults-300px.jpg)</span></span><br>
<span data-ttu-id="d187e-194">*介面的型別會標示為游標*</span><span class="sxs-lookup"><span data-stu-id="d187e-194">*Surface type is labeled next to the cursor*</span></span>

### <a name="topology-queries"></a><span data-ttu-id="d187e-195">查詢拓撲</span><span class="sxs-lookup"><span data-stu-id="d187e-195">Topology Queries</span></span>

<span data-ttu-id="d187e-196">Dll 拓樸管理員會處理環境的標記。</span><span class="sxs-lookup"><span data-stu-id="d187e-196">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="d187e-197">如先前所述，大部分的資料會儲存在 surfels，內含 voxel 磁碟區。</span><span class="sxs-lookup"><span data-stu-id="d187e-197">As mentioned above, much of the data is stored within surfels, contained within a voxel volume.</span></span> <span data-ttu-id="d187e-198">此外，「 PlaySpaceInfos 」 結構用以儲存 playspace，包括 world 對齊 （下文詳細資料）、 floor、 ceiling 高度與相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d187e-198">In addition, the “PlaySpaceInfos” structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span> <span data-ttu-id="d187e-199">啟發學習法用於決定 floor、 ceiling 和牆。</span><span class="sxs-lookup"><span data-stu-id="d187e-199">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="d187e-200">比方說，有超過 1 m2 介面區的最大值與最低的水平的介面會被視為最低限度值。</span><span class="sxs-lookup"><span data-stu-id="d187e-200">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="d187e-201">請注意，在掃描程序期間的相機路徑也會在此程序。</span><span class="sxs-lookup"><span data-stu-id="d187e-201">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="d187e-202">子集拓樸管理員所公開的查詢會透過 dll 公開出。</span><span class="sxs-lookup"><span data-stu-id="d187e-202">A subset of the queries exposed by the Topology manager are exposed out through the dll.</span></span> <span data-ttu-id="d187e-203">公開的拓樸查詢如下所示。</span><span class="sxs-lookup"><span data-stu-id="d187e-203">The exposed topology queries are as follows.</span></span>

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

<span data-ttu-id="d187e-204">每個查詢都有特定查詢型別參數組。</span><span class="sxs-lookup"><span data-stu-id="d187e-204">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="d187e-205">在下列範例中，使用者會指定最小高度和寬度所需的磁碟區、 樓層、 窗格和前面的磁碟區的許可的最小數量的最小的放置高度。</span><span class="sxs-lookup"><span data-stu-id="d187e-205">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="d187e-206">所有度量均是以公尺為單位。</span><span class="sxs-lookup"><span data-stu-id="d187e-206">All measurements are in meters.</span></span>

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="d187e-207">這些查詢會取得預先配置的陣列 」 TopologyResult 」 結構。</span><span class="sxs-lookup"><span data-stu-id="d187e-207">Each of these queries takes a pre-allocated array of “TopologyResult” structures.</span></span> <span data-ttu-id="d187e-208">「 LocationCount"參數指定傳入的陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="d187e-208">The “locationCount” parameter specifies the length of the passed in array.</span></span> <span data-ttu-id="d187e-209">傳回值會報告傳回的位置數目。</span><span class="sxs-lookup"><span data-stu-id="d187e-209">The return value reports the number of returned locations.</span></span> <span data-ttu-id="d187e-210">這個數字絕不會大於傳遞"locationCount"參數中。</span><span class="sxs-lookup"><span data-stu-id="d187e-210">This number is never greater than the passed in “locationCount” parameter.</span></span>

<span data-ttu-id="d187e-211">「 TopologyResult 」 包含傳回的磁碟區、 面向的方向 （也就是一般） 和維度的找到空間的中心位置。</span><span class="sxs-lookup"><span data-stu-id="d187e-211">The “TopologyResult” contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

<span data-ttu-id="d187e-212">請注意，在 Unity 範例中，這些查詢連結至虛擬 UI 面板中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="d187e-212">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="d187e-213">硬碟的範例程式碼參數，這些查詢能夠合理值的每個。</span><span class="sxs-lookup"><span data-stu-id="d187e-213">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="d187e-214">如需其他範例的程式碼範例，請參閱 SpaceVisualizer.cs。</span><span class="sxs-lookup"><span data-stu-id="d187e-214">See SpaceVisualizer.cs in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="d187e-215">圖形查詢</span><span class="sxs-lookup"><span data-stu-id="d187e-215">Shape Queries</span></span>

<span data-ttu-id="d187e-216">Dll 時，在圖形分析器 (「 ShapeAnalyzer_W") 會使用拓撲分析器来比對由使用者定義的自訂圖形。</span><span class="sxs-lookup"><span data-stu-id="d187e-216">Inside of the dll, the shape analyzer (“ShapeAnalyzer_W”) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="d187e-217">Unity 範例會定義一組圖形，並公開傳出結果，透過應用程式內的查詢 功能表的 圖形 索引標籤內。目的是使用者可以定義自己的物件圖形查詢，並讓使用，視其應用程式。</span><span class="sxs-lookup"><span data-stu-id="d187e-217">The Unity sample defines a set of shapes and exposes the results out through the in-app query menu, within the shape tab. The intention is that the user can define their own object shape queries and make use of those, as needed by their application.</span></span>

<span data-ttu-id="d187e-218">請注意，水平介面僅適用於圖形分析。</span><span class="sxs-lookup"><span data-stu-id="d187e-218">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="d187e-219">沙發上，比方說，是由一般基座介面和一般頂端的沙發上一步的定義。</span><span class="sxs-lookup"><span data-stu-id="d187e-219">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="d187e-220">Shape 查詢會尋找的特定大小、 頁高及長寬範圍，以對齊，且已連線的兩個介面的兩個介面。</span><span class="sxs-lookup"><span data-stu-id="d187e-220">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="d187e-221">使用 Api 術語，沙發基座] 及 [上一步上是圖形的元件和對齊需求是圖形元件的限制。</span><span class="sxs-lookup"><span data-stu-id="d187e-221">Using the APIs terminology, the couch seat and back top are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="d187e-222">在 Unity 範例 (ShapeDefinition.cs)，定義"sittable 」 物件的範例查詢如下所示。</span><span class="sxs-lookup"><span data-stu-id="d187e-222">An example query defined in the Unity sample (ShapeDefinition.cs), for “sittable” objects is as follows.</span></span>

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

<span data-ttu-id="d187e-223">每個圖形查詢由一組圖形元件，各有一組元件條件約束和一組圖形的條件約束定義其列出元件之間的相依性。</span><span class="sxs-lookup"><span data-stu-id="d187e-223">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which listing dependencies between the components.</span></span> <span data-ttu-id="d187e-224">此範例包含三個條件約束的單一元件定義及元件之間沒有任何圖形條件約束 （因為只有一個元件）。</span><span class="sxs-lookup"><span data-stu-id="d187e-224">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="d187e-225">相反地，沙發圖形有兩個圖形的元件和四個圖形的條件約束。</span><span class="sxs-lookup"><span data-stu-id="d187e-225">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="d187e-226">請注意，（0 到 1，在此範例中），使用者的元件清單中的其索引所識別的元件。</span><span class="sxs-lookup"><span data-stu-id="d187e-226">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

<span data-ttu-id="d187e-227">在 Unity 模組提供包裝函式函數，讓您輕鬆建立自訂圖形定義。</span><span class="sxs-lookup"><span data-stu-id="d187e-227">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="d187e-228">元件和圖形的條件約束的完整清單位於 「 SpatialUnderstandingDll.cs"內"ShapeComponentConstraint"和"ShapeConstraint 」 結構。</span><span class="sxs-lookup"><span data-stu-id="d187e-228">The full list of component and shape constraints can be found in “SpatialUnderstandingDll.cs” within the “ShapeComponentConstraint” and the “ShapeConstraint” structures.</span></span>

<span data-ttu-id="d187e-229">![此介面上會出現的矩形圖案](images/su-shapequery-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="d187e-229">![Rectangle shape is found on this surface](images/su-shapequery-300px.jpg)</span></span><br>
<span data-ttu-id="d187e-230">*此介面上會出現的矩形圖案*</span><span class="sxs-lookup"><span data-stu-id="d187e-230">*Rectangle shape is found on this surface*</span></span>

### <a name="object-placement-solver"></a><span data-ttu-id="d187e-231">物件放置規劃求解</span><span class="sxs-lookup"><span data-stu-id="d187e-231">Object Placement Solver</span></span>

<span data-ttu-id="d187e-232">物件放置求解器可用來識別要放置您的物件的實體空間中的理想位置。</span><span class="sxs-lookup"><span data-stu-id="d187e-232">The object placement solver can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="d187e-233">求解器將找到最適合指定物件的規則和條件約束的位置。</span><span class="sxs-lookup"><span data-stu-id="d187e-233">The solver will find the best fit location given the object rules and constraints.</span></span> <span data-ttu-id="d187e-234">此外，物件查詢會持續到物件中已移除 」 Solver_RemoveObject"或"Solver_RemoveAllObjects 」 呼叫，允許限制多的物件位置。</span><span class="sxs-lookup"><span data-stu-id="d187e-234">In addition, object queries persist until the object is removed with “Solver_RemoveObject” or “Solver_RemoveAllObjects” calls, allowing constrained multi-object placement.</span></span> <span data-ttu-id="d187e-235">物件放置查詢是由三個部分所組成： 參數、 一份規則與條件約束清單的位置類型。</span><span class="sxs-lookup"><span data-stu-id="d187e-235">Objects placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="d187e-236">若要執行查詢時，使用下列的 API。</span><span class="sxs-lookup"><span data-stu-id="d187e-236">To run a query, use the following API.</span></span>

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

<span data-ttu-id="d187e-237">此函數會接受物件名稱、 位置定義和規則和條件約束的清單。</span><span class="sxs-lookup"><span data-stu-id="d187e-237">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="d187e-238">C#包裝函式提供的建構可讓您輕鬆的規則和條件約束建構的 helper 函式。</span><span class="sxs-lookup"><span data-stu-id="d187e-238">The C# wrappers provides construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="d187e-239">放置定義包含查詢類型 – 也就是下列其中之一。</span><span class="sxs-lookup"><span data-stu-id="d187e-239">The placement definition contains the query type – that is, one of the following.</span></span>

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

<span data-ttu-id="d187e-240">每個位置型別具有一組唯一類型的參數。</span><span class="sxs-lookup"><span data-stu-id="d187e-240">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="d187e-241">「 ObjectPlacementDefinition 」 結構包含一組靜態的 helper 函式來建立這些定義。</span><span class="sxs-lookup"><span data-stu-id="d187e-241">The “ObjectPlacementDefinition” structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="d187e-242">例如，若要尋找之處，將物件放在地板上，您可以使用下列函式。</span><span class="sxs-lookup"><span data-stu-id="d187e-242">For example, to find a place to put an object on the floor, you can use the following function.</span></span> <span data-ttu-id="d187e-243">公用靜態 ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) 除了之外的位置類型，您可以提供一組規則和條件約束。</span><span class="sxs-lookup"><span data-stu-id="d187e-243">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="d187e-244">不能違反規則。</span><span class="sxs-lookup"><span data-stu-id="d187e-244">Rules cannot be violated.</span></span> <span data-ttu-id="d187e-245">針對條件約束的集合，就可以選取最佳的放置位置然後最佳化滿足的類型與規則的可能的放置位置。</span><span class="sxs-lookup"><span data-stu-id="d187e-245">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints in order to select the optimal placement location.</span></span> <span data-ttu-id="d187e-246">每個規則和條件約束可以提供靜態建立函式所建立。</span><span class="sxs-lookup"><span data-stu-id="d187e-246">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="d187e-247">如下所示的範例規則和條件約束建構函式。</span><span class="sxs-lookup"><span data-stu-id="d187e-247">An example rule and constraint construction function is provided below.</span></span>

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="d187e-248">物件的下面放置查詢會尋找放介面的邊緣，一半的計量 cube、 遠離其他先前放置物件及附近的聊天室中央的地方。</span><span class="sxs-lookup"><span data-stu-id="d187e-248">The below object placement query is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>

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

<span data-ttu-id="d187e-249">如果成功，"ObjectPlacementResult 」 結構，包含放置位置中，維度和方向會傳回。</span><span class="sxs-lookup"><span data-stu-id="d187e-249">If successful, a “ObjectPlacementResult” structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="d187e-250">此外，位置會加入 dll 的內部放置的物件清單。</span><span class="sxs-lookup"><span data-stu-id="d187e-250">In addition, the placement is added to the dll’s internal list of placed objects.</span></span> <span data-ttu-id="d187e-251">後續的放置查詢會將此物件納入考量。</span><span class="sxs-lookup"><span data-stu-id="d187e-251">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="d187e-252">在 Unity 範例中的"LevelSolver.cs"檔案包含更多的範例查詢。</span><span class="sxs-lookup"><span data-stu-id="d187e-252">The “LevelSolver.cs” file in the Unity sample contains more example queries.</span></span>

<span data-ttu-id="d187e-253">![物件位置的結果](images/su-objectplacement-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="d187e-253">![Results of object placement](images/su-objectplacement-1000px.jpg)</span></span><br>
<span data-ttu-id="d187e-254">*圖 3:藍色方塊如何樓層的三個位置的結果查詢與離開觀景窗位置規則*</span><span class="sxs-lookup"><span data-stu-id="d187e-254">*Figure 3: The blue boxes how the result from three place on floor queries with away from camera position rules*</span></span>

<span data-ttu-id="d187e-255">解決層級或應用程式的案例所需的多個物件的放置位置，先解決不可或缺和大型物件空間，您可以找到的機率最大化的順序。</span><span class="sxs-lookup"><span data-stu-id="d187e-255">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects in order to maximizing the probability that a space can be found.</span></span> <span data-ttu-id="d187e-256">放置順序非常重要。</span><span class="sxs-lookup"><span data-stu-id="d187e-256">Placement order is important.</span></span> <span data-ttu-id="d187e-257">如果找不到物件的位置，請嘗試較不受條件約束的組態。</span><span class="sxs-lookup"><span data-stu-id="d187e-257">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="d187e-258">後援設定一組非常重要跨許多空間組態支援的功能。</span><span class="sxs-lookup"><span data-stu-id="d187e-258">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="d187e-259">聊天室掃描程序</span><span class="sxs-lookup"><span data-stu-id="d187e-259">Room Scanning Process</span></span>

<span data-ttu-id="d187e-260">雖然 HoloLens 所提供的空間對應解決方案設計為泛型程度足以符合完整的問題空間一系列的需求，以支援的兩個特定的遊戲需要建置空間的了解模組。</span><span class="sxs-lookup"><span data-stu-id="d187e-260">While the spatial mapping solution provided by the HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="d187e-261">其解決方案被圍繞的特定處理程序和的假設，以下摘要說明的設定。</span><span class="sxs-lookup"><span data-stu-id="d187e-261">Its solution is structured around a specific process and set of assumptions, summarized below.</span></span>

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

<span data-ttu-id="d187e-262">使用者導向 playspace"繪製 」 – 在掃描階段中，使用者移動，並尋找周圍所扮演的腳步，有效地繪製應該包含的區域。</span><span class="sxs-lookup"><span data-stu-id="d187e-262">User driven playspace “painting” – During the scanning phase, the user moves and looks around the plays pace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="d187e-263">產生的網狀結構，務必在這個階段期間提供使用者意見反應。</span><span class="sxs-lookup"><span data-stu-id="d187e-263">The generated mesh is important to provide user feedback during this phase.</span></span> <span data-ttu-id="d187e-264">室內首頁，或安裝的 office 程式 – 的查詢函式專為一般的介面及背景牆直角。</span><span class="sxs-lookup"><span data-stu-id="d187e-264">Indoors home or office setup – The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="d187e-265">這是軟性限制。</span><span class="sxs-lookup"><span data-stu-id="d187e-265">This is a soft limitation.</span></span> <span data-ttu-id="d187e-266">不過，在掃描階段中，主座標軸分析會完成最佳化網狀結構鑲嵌式主要和次要軸。</span><span class="sxs-lookup"><span data-stu-id="d187e-266">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span> <span data-ttu-id="d187e-267">包含的 SpatialUnderstanding.cs 檔案管理掃描階段的程序。</span><span class="sxs-lookup"><span data-stu-id="d187e-267">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="d187e-268">它會呼叫下列函式。</span><span class="sxs-lookup"><span data-stu-id="d187e-268">It calls the following functions.</span></span>

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

<span data-ttu-id="d187e-269">掃描流程，並由 「 SpatialUnderstanding 」 行為會呼叫 InitScan，則 UpdateScan 每個畫面格。</span><span class="sxs-lookup"><span data-stu-id="d187e-269">The scanning flow, driven by the “SpatialUnderstanding” behavior calls InitScan, then UpdateScan each frame.</span></span> <span data-ttu-id="d187e-270">當統計資料的查詢報告合理的涵蓋範圍時，允許使用者 airtap 呼叫 RequestFinish 表示 「 掃描 」 階段的結束。</span><span class="sxs-lookup"><span data-stu-id="d187e-270">When the statistics query reports reasonable coverage, the user is allowed to airtap to call RequestFinish to indicate the end of the scanning phase.</span></span> <span data-ttu-id="d187e-271">UpdateScan 會繼續呼叫傳回之前的值會指出 dll 已完成處理。</span><span class="sxs-lookup"><span data-stu-id="d187e-271">UpdateScan continues to be called until it’s return value indicates that the dll has completed processing.</span></span>

### <a name="understanding-mesh"></a><span data-ttu-id="d187e-272">了解網格</span><span class="sxs-lookup"><span data-stu-id="d187e-272">Understanding Mesh</span></span>

<span data-ttu-id="d187e-273">了解 dll 在內部儲存 playspace，以調整大小的 8 cm voxel cube 的方格。</span><span class="sxs-lookup"><span data-stu-id="d187e-273">The understanding dll internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="d187e-274">在掃描的初始部分，主要元件分析完成來決定座標軸的聊天室。</span><span class="sxs-lookup"><span data-stu-id="d187e-274">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="d187e-275">就內部而言，它會儲存這些軸對齊其 voxel 空間。</span><span class="sxs-lookup"><span data-stu-id="d187e-275">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="d187e-276">網格會產生大約每秒擷取 isosurface voxel 磁碟區。</span><span class="sxs-lookup"><span data-stu-id="d187e-276">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span> 

<span data-ttu-id="d187e-277">![產生的網格所產生的 voxel 磁碟區](images/su-custommesh.jpg)</span><span class="sxs-lookup"><span data-stu-id="d187e-277">![Generated mesh produced from the voxel volume](images/su-custommesh.jpg)</span></span><br>
<span data-ttu-id="d187e-278">*產生的網格所產生的 voxel 磁碟區*</span><span class="sxs-lookup"><span data-stu-id="d187e-278">*Generated mesh produced from the voxel volume*</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="d187e-279">疑難排解</span><span class="sxs-lookup"><span data-stu-id="d187e-279">Troubleshooting</span></span>
* <span data-ttu-id="d187e-280">請確定您已設定[SpatialPerception](#setting-the-spatialperception-capability)功能</span><span class="sxs-lookup"><span data-stu-id="d187e-280">Ensure you have set the [SpatialPerception](#setting-the-spatialperception-capability) capability</span></span>
* <span data-ttu-id="d187e-281">追蹤遺失時下, 一步 OnSurfaceChanged 事件將會移除所有的網格。</span><span class="sxs-lookup"><span data-stu-id="d187e-281">When tracking is lost, the next OnSurfaceChanged event will remove all meshes.</span></span>

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a><span data-ttu-id="d187e-282">混合的實境工具組中的空間對應</span><span class="sxs-lookup"><span data-stu-id="d187e-282">Spatial Mapping in Mixed Reality Toolkit</span></span>
<span data-ttu-id="d187e-283">如需有關使用混合實境 Toolkit v2 中使用 空間對應的詳細資訊，請參閱<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">空間感知區段</a>MRTK 文件。</span><span class="sxs-lookup"><span data-stu-id="d187e-283">For more information on using Spatial Mapping with Mixed Reality Toolkit v2, see the <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Spatial Awareness section</a> of the MRTK docs.</span></span>

## <a name="see-also"></a><span data-ttu-id="d187e-284">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d187e-284">See also</span></span>
* [<span data-ttu-id="d187e-285">MR 空間 230:空間對應</span><span class="sxs-lookup"><span data-stu-id="d187e-285">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="d187e-286">座標系統</span><span class="sxs-lookup"><span data-stu-id="d187e-286">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="d187e-287">在 Unity 中的座標系統</span><span class="sxs-lookup"><span data-stu-id="d187e-287">Coordinate systems in Unity</span></span>](coordinate-systems-in-unity.md)
* <span data-ttu-id="d187e-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span><span class="sxs-lookup"><span data-stu-id="d187e-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span></span>
* <span data-ttu-id="d187e-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span><span class="sxs-lookup"><span data-stu-id="d187e-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span></span>
* <span data-ttu-id="d187e-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span><span class="sxs-lookup"><span data-stu-id="d187e-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span></span>
* <span data-ttu-id="d187e-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span><span class="sxs-lookup"><span data-stu-id="d187e-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span></span>
