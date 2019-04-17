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
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2019
ms.locfileid: "59597147"
---
# <a name="spatial-mapping-in-unity"></a>在 Unity 中的空間對應

本主題描述如何使用[空間對應](spatial-mapping.md)在 Unity 專案中，擷取三角網格，代表在世界各地的 HoloLens 裝置、 位置、 阻擋、 空間分析和更多功能的介面。

Unity 包含空間的對應，以下列方式公開給開發人員的完整支援：
1. 空間對應 MixedRealityToolkit 中可用的元件，提供方便且快速路徑空間的對應使用者入門
2. 較低層級空間的對應 Api，提供完整控制，並啟用更複雜的應用程式特定的自訂

若要在您的應用程式中使用空間的對應，spatialPerception 功能必須在您 AppxManifest 中設定。

## <a name="setting-the-spatialperception-capability"></a>設定 SpatialPerception 功能

為了讓應用程式來使用空間的對應資料，必須啟用 SpatialPerception 功能。

如何啟用 SpatialPerception 功能：
1. 在 Unity 編輯器中，開啟 **[播放程式設定]** 窗格 (編輯 > 專案設定 > 播放器)
2. 按一下 [ **「 Windows 市集 」** ] 索引標籤
3. 依序展開 **「 發佈設定 」** ，並檢查 **"SpatialPerception 」** 中的功能 **「 功能 」** 清單

請注意，是否您已匯出您的 Unity 專案加入 Visual Studio 方案，您必須匯出新的資料夾或以手動方式[設定這項功能在 Visual Studio 中，AppxManifest](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)。

空間對應也需要至少 10.0.10586.0 的 MaxVersionTested:
1. 在 Visual Studio 中，以滑鼠右鍵按一下**Package.appxmanifest**方案總管 中選取**檢視程式碼**
2. 尋找列指定**TargetDeviceFamily**並變更**MaxVersionTested ="10.0.10240.0 」** 到**MaxVersionTested"uwp,version=10.0.10586.0 」**
3. **儲存**Package.appxmanifest。

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>開始使用 Unity 的內建空間的對應元件

Unity 提供 2 個元件，輕鬆地將空間的對應新增至您的應用程式**空間的對應轉譯器**並**空間的對應 Collider**。

### <a name="spatial-mapping-renderer"></a>空間對應的轉譯器

空間對應轉譯器可讓您的空間對應網狀結構的視覺效果。

![在 Unity 中的空間對應轉譯器](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>空間對應 Collider

空間對應 Collider 能進行全像攝影版的內容 （字元） 互動，例如物理條件，與空間對應網格。

![在 Unity 中的空間對應 Collider](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>使用內建空間的對應元件

如果您想要以視覺化方式檢視和互動實體介面，您可以將這兩個元件新增至您的應用程式中。

若要在您的 Unity 應用程式中使用這兩個元件：
1. 選取您想要偵測空間介面網格所在區域的中心 GameObject。
2. 在 [偵測器] 視窗中，**新增元件** > **XR** > **空間的對應 Collider** 或**空間對應的轉譯器**。

您可以深入了解如何使用這些元件<a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity 文件網站</a>。

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>超越內建空間的對應元件

這些元件讓拖放輕鬆開始使用空間的對應。  當您想要更進一步時，有兩個主要路徑來瀏覽：
* 若要執行您自己的較低層級網格處理，請參閱下節的低層級的空間對應指令碼 API。
* 若要進行更高層級的網狀結構分析時，請參閱下一節中的 SpatialUnderstanding 程式庫的相關<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>。

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>使用低層級 Unity 空間對應 API

如果您需要更多的控制權比您獲得的空間對應的轉譯器和空間的對應 Collider 元件時，您可以使用低層級的空間對應指令碼 Api。

**命名空間：***UnityEngine.XR.WSA*<br>
**型別**:*SurfaceObserver*， *SurfaceChange*， *SurfaceData*， *SurfaceId*

以下是使用空間的對應 Api 的應用程式的建議流程的大綱。

### <a name="set-up-the-surfaceobservers"></a>設定 SurfaceObserver(s)

具現化一個 SurfaceObserver 物件所需空間的對應資料空間的每個應用程式定義的區域。

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

指定的區域的每個 SurfaceObserver 物件會藉由呼叫 SetVolumeAsSphere、 SetVolumeAsAxisAlignedBox、 SetVolumeAsOrientedBox，還是 SetVolumeAsFrustum 提供資料的空間。 您可以再次呼叫其中一個方法，以重新定義空間在未來的區域。

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

當您呼叫 SurfaceObserver.Update() 時，您必須提供處理常式的空間的對應系統具有新資訊的空間 SurfaceObserver 的區域中每個空間的介面。 接收處理常式的一個空間介面：

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a>處理介面的變更

有數個主要的案例來處理。 新增與更新可以使用相同的程式碼的路徑和已移除。
* 在此範例中新增和 Updated 情況下，我們要新增或取得 GameObject，代表這 mesh 從字典，建立 SurfaceData 結構以所需的元件，然後呼叫以填入與網狀結構資料 GameObject RequestMeshDataAsync 和定位在場景中。
* 在已移除的案例中，我們可以移除從字典中代表此網格 GameObject 並終結它。

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

### <a name="handling-data-ready"></a>具備處理資料

OnDataReady 處理常式會接收 SurfaceData 物件。 WorldAnchor、 MeshFilter 及 （選擇性） 其包含的 MeshCollider 物件會反映相關聯的空間表面的最新狀態。 （選擇性） 執行分析和/或[處理](spatial-mapping.md#mesh-processing)藉由存取 MeshFilter 物件的網狀結構成員的網格資料。 呈現與最新的網格空間的介面和 （選擇性） 將它用於物理衝突，raycasts。 請務必確認 SurfaceData 的內容不是 null。

### <a name="start-processing-on-updates"></a>開始處理更新

應該在延遲，而不是每個畫面呼叫 SurfaceObserver.Update()。

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

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a>較高層級的網狀結構分析：SpatialUnderstanding

<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>是建置在全像攝影版的 Unity Api 的全像攝影版開發的實用公用程式程式碼的集合。

### <a name="spatial-understanding"></a>了解空間

放置在真實世界的全像投影時通常會前往超出空間對應的網狀結構，並呈現平面。 放置可循序完成之後，較高層級的環境了解將是理想。 這通常需要制定有關什麼是 floor、 ceiling 和牆。 此外，針對至決定的全像攝影版的物件最迫切需要的實體位置的放置條件約束一組最佳化的能力。

在開發期間的 Young Conker 和片段，Asobo Studios 會面臨這個問題標頭，針對此目的開發的空間規劃求解。 每個遊戲遊戲的特定需求，但它們共用核心空間的了解技術。 程式庫封裝這項技術，可讓您快速尋找空白空間上牆壁，讓物件上，找出 HoloToolkit.SpatialUnderstanding 放置要坐著，字元和各種其他空間的了解查詢。

所有來源的程式碼，會包含可讓您根據您的需求進行自訂，並與社群分享您的增強功能。 程式碼C++規劃求解已包裝成 UWP dll 並公開到 Unity prefab 內含 MixedRealityToolkit 下降。

### <a name="understanding-modules"></a>了解模組

有三個模組所公開的主要介面： 簡單的介面和空間查詢、 物體偵測的圖形和物件放置求解器為基礎的條件約束放置物件集的拓撲。 每一種是如下所述。 除了三個主要模組介面中，光跡轉型介面可用來擷取已加上標記的介面型別和自訂 watertight playspace 網格可以複製出來。

### <a name="ray-casting"></a>光跡轉型

聊天室已進行掃描而且已完成之後，標籤是內部產生的介面，例如 floor、 ceiling 和牆上。 「 PlayspaceRaycast"函式會採用無限遠的光線，並傳回如果光線衝突與已知的介面，而且如果是這樣，該介面的 「 RaycastResult"形式的相關資訊。

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

就內部而言，raycast 會計算針對 playspace 計算立方的 8 cm voxel 表示法。 每個 voxel 包含一組已處理的拓撲資料 (也稱為 surfels) 的介面項目。 比較交集的 voxel 資料格內所含 surfels 和最符合項目用來查閱拓撲資訊。 此拓撲的資料包含標記傳回 「 SurfaceTypes"列舉的形式，以及在交集的介面的介面區。

在 Unity 範例中，資料指標會轉換每個畫面格無限遠的光線。 首先，針對 Unity colliders。 第二，針對了解模組的世界表示法。 與最後一次 UI 項目。 在此應用程式中，UI 取得優先順序，接著了解結果，和最後，Unity colliders。 SurfaceType 會回報為游標後面的文字。

![介面的型別會標示為游標](images/su-raycastresults-300px.jpg)<br>
*介面的型別會標示為游標*

### <a name="topology-queries"></a>查詢拓撲

Dll 拓樸管理員會處理環境的標記。 如先前所述，大部分的資料會儲存在 surfels，內含 voxel 磁碟區。 此外，「 PlaySpaceInfos 」 結構用以儲存 playspace，包括 world 對齊 （下文詳細資料）、 floor、 ceiling 高度與相關資訊。 啟發學習法用於決定 floor、 ceiling 和牆。 比方說，有超過 1 m2 介面區的最大值與最低的水平的介面會被視為最低限度值。 請注意，在掃描程序期間的相機路徑也會在此程序。

子集拓樸管理員所公開的查詢會透過 dll 公開出。 公開的拓樸查詢如下所示。

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

每個查詢都有特定查詢型別參數組。 在下列範例中，使用者會指定最小高度和寬度所需的磁碟區、 樓層、 窗格和前面的磁碟區的許可的最小數量的最小的放置高度。 所有度量均是以公尺為單位。

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

這些查詢會取得預先配置的陣列 」 TopologyResult 」 結構。 「 LocationCount"參數指定傳入的陣列的長度。 傳回值會報告傳回的位置數目。 這個數字絕不會大於傳遞"locationCount"參數中。

「 TopologyResult 」 包含傳回的磁碟區、 面向的方向 （也就是一般） 和維度的找到空間的中心位置。

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

請注意，在 Unity 範例中，這些查詢連結至虛擬 UI 面板中的按鈕。 硬碟的範例程式碼參數，這些查詢能夠合理值的每個。 如需其他範例的程式碼範例，請參閱 SpaceVisualizer.cs。

### <a name="shape-queries"></a>圖形查詢

Dll 時，在圖形分析器 (「 ShapeAnalyzer_W") 會使用拓撲分析器来比對由使用者定義的自訂圖形。 Unity 範例會定義一組圖形，並公開傳出結果，透過應用程式內的查詢 功能表的 圖形 索引標籤內。目的是使用者可以定義自己的物件圖形查詢，並讓使用，視其應用程式。

請注意，水平介面僅適用於圖形分析。 沙發上，比方說，是由一般基座介面和一般頂端的沙發上一步的定義。 Shape 查詢會尋找的特定大小、 頁高及長寬範圍，以對齊，且已連線的兩個介面的兩個介面。 使用 Api 術語，沙發基座] 及 [上一步上是圖形的元件和對齊需求是圖形元件的限制。

在 Unity 範例 (ShapeDefinition.cs)，定義"sittable 」 物件的範例查詢如下所示。

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

每個圖形查詢由一組圖形元件，各有一組元件條件約束和一組圖形的條件約束定義其列出元件之間的相依性。 此範例包含三個條件約束的單一元件定義及元件之間沒有任何圖形條件約束 （因為只有一個元件）。

相反地，沙發圖形有兩個圖形的元件和四個圖形的條件約束。 請注意，（0 到 1，在此範例中），使用者的元件清單中的其索引所識別的元件。

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

在 Unity 模組提供包裝函式函數，讓您輕鬆建立自訂圖形定義。 元件和圖形的條件約束的完整清單位於 「 SpatialUnderstandingDll.cs"內"ShapeComponentConstraint"和"ShapeConstraint 」 結構。

![此介面上會出現的矩形圖案](images/su-shapequery-300px.jpg)<br>
*此介面上會出現的矩形圖案*

### <a name="object-placement-solver"></a>物件放置規劃求解

物件放置求解器可用來識別要放置您的物件的實體空間中的理想位置。 求解器將找到最適合指定物件的規則和條件約束的位置。 此外，物件查詢會持續到物件中已移除 」 Solver_RemoveObject"或"Solver_RemoveAllObjects 」 呼叫，允許限制多的物件位置。 物件放置查詢是由三個部分所組成： 參數、 一份規則與條件約束清單的位置類型。 若要執行查詢時，使用下列的 API。

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

此函數會接受物件名稱、 位置定義和規則和條件約束的清單。 C#包裝函式提供的建構可讓您輕鬆的規則和條件約束建構的 helper 函式。 放置定義包含查詢類型 – 也就是下列其中之一。

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

每個位置型別具有一組唯一類型的參數。 「 ObjectPlacementDefinition 」 結構包含一組靜態的 helper 函式來建立這些定義。 例如，若要尋找之處，將物件放在地板上，您可以使用下列函式。 公用靜態 ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) 除了之外的位置類型，您可以提供一組規則和條件約束。 不能違反規則。 針對條件約束的集合，就可以選取最佳的放置位置然後最佳化滿足的類型與規則的可能的放置位置。 每個規則和條件約束可以提供靜態建立函式所建立。 如下所示的範例規則和條件約束建構函式。

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

物件的下面放置查詢會尋找放介面的邊緣，一半的計量 cube、 遠離其他先前放置物件及附近的聊天室中央的地方。

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

如果成功，"ObjectPlacementResult 」 結構，包含放置位置中，維度和方向會傳回。 此外，位置會加入 dll 的內部放置的物件清單。 後續的放置查詢會將此物件納入考量。 在 Unity 範例中的"LevelSolver.cs"檔案包含更多的範例查詢。

![物件位置的結果](images/su-objectplacement-1000px.jpg)<br>
*圖 3:藍色方塊如何樓層的三個位置的結果查詢與離開觀景窗位置規則*

解決層級或應用程式的案例所需的多個物件的放置位置，先解決不可或缺和大型物件空間，您可以找到的機率最大化的順序。 放置順序非常重要。 如果找不到物件的位置，請嘗試較不受條件約束的組態。 後援設定一組非常重要跨許多空間組態支援的功能。

### <a name="room-scanning-process"></a>聊天室掃描程序

雖然 HoloLens 所提供的空間對應解決方案設計為泛型程度足以符合完整的問題空間一系列的需求，以支援的兩個特定的遊戲需要建置空間的了解模組。 其解決方案被圍繞的特定處理程序和的假設，以下摘要說明的設定。

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

使用者導向 playspace"繪製 」 – 在掃描階段中，使用者移動，並尋找周圍所扮演的腳步，有效地繪製應該包含的區域。 產生的網狀結構，務必在這個階段期間提供使用者意見反應。 室內首頁，或安裝的 office 程式 – 的查詢函式專為一般的介面及背景牆直角。 這是軟性限制。 不過，在掃描階段中，主座標軸分析會完成最佳化網狀結構鑲嵌式主要和次要軸。 包含的 SpatialUnderstanding.cs 檔案管理掃描階段的程序。 它會呼叫下列函式。

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

掃描流程，並由 「 SpatialUnderstanding 」 行為會呼叫 InitScan，則 UpdateScan 每個畫面格。 當統計資料的查詢報告合理的涵蓋範圍時，允許使用者 airtap 呼叫 RequestFinish 表示 「 掃描 」 階段的結束。 UpdateScan 會繼續呼叫傳回之前的值會指出 dll 已完成處理。

### <a name="understanding-mesh"></a>了解網格

了解 dll 在內部儲存 playspace，以調整大小的 8 cm voxel cube 的方格。 在掃描的初始部分，主要元件分析完成來決定座標軸的聊天室。 就內部而言，它會儲存這些軸對齊其 voxel 空間。 網格會產生大約每秒擷取 isosurface voxel 磁碟區。 

![產生的網格所產生的 voxel 磁碟區](images/su-custommesh.jpg)<br>
*產生的網格所產生的 voxel 磁碟區*

## <a name="troubleshooting"></a>疑難排解
* 請確定您已設定[SpatialPerception](#setting-the-spatialperception-capability)功能
* 追蹤遺失時下, 一步 OnSurfaceChanged 事件將會移除所有的網格。

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a>混合的實境工具組中的空間對應
如需有關使用混合實境 Toolkit v2 中使用 空間對應的詳細資訊，請參閱<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">空間感知區段</a>MRTK 文件。

## <a name="see-also"></a>另請參閱
* [MR 空間 230:空間對應](holograms-230.md)
* [座標系統](coordinate-systems.md)
* [在 Unity 中的座標系統](coordinate-systems-in-unity.md)
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>
* <a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a>
* <a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a>
* <a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a>
