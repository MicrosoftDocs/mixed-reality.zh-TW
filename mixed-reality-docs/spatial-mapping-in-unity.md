---
title: Unity 中的空間對應
description: 在 Unity 中呈現和與您在世界各地的真實幾何進行衝突。
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity，空間對應，轉譯器，碰撞器，網格，掃描，元件
ms.openlocfilehash: 452e629a877df585ffbc0a6466ffeb2588b66ecf
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438041"
---
# <a name="spatial-mapping-in-unity"></a>Unity 中的空間對應

本主題說明如何在您的 Unity 專案中使用[空間對應](spatial-mapping.md)、抓取代表 HoloLens 裝置周圍表面的三角形網格，以進行放置、遮蔽、房間分析等等。

Unity 包含空間對應的完整支援，這會以下列方式公開給開發人員：
1. MixedRealityToolkit 中可用的空間對應元件，可為開始使用空間對應提供便利快速的路徑
2. 較低層級的空間對應 Api，可提供完整控制，並啟用更複雜的應用程式特定自訂

若要在您的應用程式中使用空間對應，必須在您的 Package.appxmanifest.xml 中設定 spatialPerception 功能。

## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>特徵</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>空間對應</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="setting-the-spatialperception-capability"></a>設定 SpatialPerception 功能

為了讓應用程式使用空間對應資料，必須啟用 SpatialPerception 功能。

如何啟用 SpatialPerception 功能：
1. 在 Unity 編輯器中，開啟 [ **Player 設定**] 窗格（編輯 > 專案設定 > Player）
2. 按一下 [ **Windows Store** ] 索引標籤
3. 展開 [**發行設定]** ，然後檢查 [**功能]** 清單中的 [ **SpatialPerception]** 功能

請注意，如果您已經將 Unity 專案匯出至 Visual Studio 方案，您必須匯出到新的資料夾，或在[Visual Studio 的 package.appxmanifest.xml 中手動設定這項功能](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)。

空間對應也需要至少10.0.10586.0 的 MaxVersionTested：
1. 在 Visual Studio 中，以滑鼠右鍵按一下方案總管中的 [ **package.appxmanifest.xml** ]，然後選取 [**查看程式碼**]
2. 找出指定**y**並將**MaxVersionTested = "10.0.10240.0"** 變更為**MaxVersionTested = "10.0.10586.0"** 的程式程式碼
3. **儲存**封裝. package.appxmanifest.xml。

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>開始使用 Unity 的內建空間對應元件

Unity 提供2個元件，可讓您輕鬆地將空間對應新增至您的應用程式、**空間對應**轉譯器和**空間對應碰撞**器。

### <a name="spatial-mapping-renderer"></a>空間對應轉譯器

空間對應轉譯器可讓您呈現空間對應網格的視覺效果。

![Unity 中的空間對應轉譯器](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>空間對應碰撞

空間對應碰撞程式可讓您使用空間對應網格，進行全像物理的內容（或字元）互動。

![Unity 中的空間對應碰撞](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>使用內建空間對應元件

如果您想要視覺化和互動實體表面，可以將這兩個元件新增至您的應用程式。

若要在 Unity 應用程式中使用這兩個元件：
1. 在您要偵測空間表面網格的區域中央選取 GameObject。
2. 在 [偵測器] 視窗中，**新增元件** > **XR** > **空間對應碰撞**器 或**空間對應**轉譯器。

您可以在<a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity 檔網站</a>找到如何使用這些元件的詳細資訊。

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>超越內建的空間對應元件

這些元件可讓您輕鬆地拖放，以開始使用空間對應。  當您想要進一步瞭解時，有兩個主要路徑可供探索：
* 若要執行您自己的較低層級的網格處理，請參閱下方關於低層級空間對應腳本 API 的小節。
* 若要執行更高層級的網格分析，請參閱下方有關<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>中 SpatialUnderstanding 程式庫的章節。

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>使用低層級 Unity 空間對應 API

如果您需要更多的控制，而不是從空間對應轉譯器和空間對應碰撞器元件取得，您可以使用低層級的空間對應腳本 Api。

**命名空間：** *UnityEngine. XR. WSA*<br>
**類型**： *SurfaceObserver*、 *SurfaceChange*、 *SurfaceData*、 *SurfaceId*

以下是使用空間對應 Api 之應用程式的建議流程概述。

### <a name="set-up-the-surfaceobservers"></a>設定 SurfaceObserver

針對您需要空間對應資料的每個應用程式定義區域，具現化一個 SurfaceObserver 物件。

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

藉由呼叫 SetVolumeAsSphere、SetVolumeAsAxisAlignedBox、SetVolumeAsOrientedBox 或 SetVolumeAsFrustum，指定每個 SurfaceObserver 物件將為其提供資料的空間區域。 您只要再次呼叫其中一個方法，就可以重新定義未來的空間區域。

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

當您呼叫 SurfaceObserver （）時，您必須針對空間對應系統有新資訊的空間，在 SurfaceObserver 區域中提供每個空間介面的處理常式。 處理常式會接收一個空間介面的：

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a>處理 Surface 變更

有幾個主要案例需要處理。 已新增 & 更新，可使用相同的程式碼路徑並加以移除。
* 在範例中新增的 & 更新案例中，我們會從字典新增或取得代表此網格的 GameObject、使用必要的元件建立 SurfaceData 結構，然後呼叫 RequestMeshDataAsync 將網格資料填入 GameObject 中，然後場景中的位置。
* 在移除的案例中，我們會從字典中移除代表此網格的 GameObject，並將其終結。

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

### <a name="handling-data-ready"></a>處理資料就緒

OnDataReady 處理常式會接收 SurfaceData 物件。 其所包含的 WorldAnchor、MeshFilter 和（選擇性） MeshCollider 物件會反映相關聯空間介面的最新狀態。 藉由存取 MeshFilter 物件的網格成員，選擇性地執行網格資料的分析和（或）[處理](spatial-mapping.md#mesh-processing)。 使用最新的網格呈現空間介面，並選擇性地使用它來進行物理衝突和 raycasts。 請務必確認 SurfaceData 的內容不是 null。

### <a name="start-processing-on-updates"></a>開始處理更新

應該在延遲（而非每個框架）上呼叫 SurfaceObserver （）。

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

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a>較高層級的網格分析： SpatialUnderstanding

<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>是一組實用的公用程式程式碼，適用于以全像攝影 Unity api 為基礎的全像攝影開發。

### <a name="spatial-understanding"></a>空間理解

將全息影像放在實體世界中時，通常會想要超越空間對應的網格和 surface 平面。 當放置完成 cti 時，會需要更高層級的環境理解。 這通常需要做出關於樓層、上限和牆的決策。 此外，也能夠優化一組放置條件約束，以判斷全像攝影物件的最理想實體位置。

在 Conker 和片段的開發期間，Asobo 工作室面臨此問題的原因，開發出空間規劃求解以實現此目的。 這些遊戲中的每一個都有遊戲特有的需求，但它們分享了核心空間的理解技術。 HoloToolkit. SpatialUnderstanding 程式庫會封裝這項技術，讓您可以快速地在牆上尋找空的空間、將物件放在最上方、找出放置於字元的位置，以及其他許多空間理解查詢。

包含所有原始程式碼，讓您可以依據自己的需求進行自訂，並與您的社區分享您的改進。 此C++規劃求解的程式碼已包裝成 UWP dll，並使用包含在 MixedRealityToolkit 內的 prefab，向 Unity 公開。

### <a name="understanding-modules"></a>瞭解模組

模組所公開的主要介面有三個：簡單表面和空間查詢的拓撲、物件偵測的圖形，以及物件位置規劃求解，用於以條件約束為基礎的物件集合位置。 以下說明每一種。 除了三個主要模組介面，光線轉型介面可以用來取出標記的表面型別，也可以將自訂的防水 playspace 網格複製出來。

### <a name="ray-casting"></a>光線轉換

在掃描完房間並完成後，就會在內部為地面、上限和牆等表面產生標籤。 "PlayspaceRaycast" 函式會採用光線，並在光線與已知表面衝突時傳回，如果是，則會傳回該介面的相關資訊（以 "RaycastResult" 為形式）。

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

就內部而言，會針對 playspace 的計算8cm 立方體素標記法來計算 raycast。 每個體素都包含一組具有已處理拓撲資料的 surface 元素（也稱為 surfels）。 交集的體素資料格內所包含的 surfels 會進行比較，並使用最符合的方式來查閱拓撲資訊。 此拓撲資料包含以 "SurfaceTypes" 列舉形式傳回的標籤，以及交集資料表面的介面區。

在 Unity 範例中，游標會將光線轉換成每個畫面格。 首先，針對 Unity 的 colliders。 第二，針對瞭解模組的世界標記法。 最後，再按一次 UI 元素。 在此應用程式中，UI 會取得優先順序，接下來是瞭解結果，最後是 Unity 的 colliders。 SurfaceType 會回報為游標旁的文字。

![介面類別型會標示為游標旁](images/su-raycastresults-300px.jpg)<br>
*介面類別型在游標旁標示*

### <a name="topology-queries"></a>拓撲查詢

在 DLL 中，拓撲管理員會處理環境的標籤。 如先前所述，大部分的資料會儲存在 surfels 內，並包含在體素磁片區中。 此外，"PlaySpaceInfos" 結構是用來儲存 playspace 的相關資訊，包括世界對齊（更多詳細資料，如下所示）、樓層和上限高度。 啟發學習法是用來決定樓層、上限和牆。 例如，具有大於1個 m2 介面區的最大和最低水準表面會視為樓層。 請注意，在掃描過程中的相機路徑也會在此程式中使用。

拓撲管理員所公開的查詢子集會透過 dll 公開。 公開的拓撲查詢如下所示。

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

每個查詢都有一組參數，特定于查詢類型。 在下列範例中，使用者會指定所需磁片區的最小高度 & 寬度、樓層上方的最小放置高度，以及該磁片區前方的最小間隙量。 所有的測量單位都是計量。

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

這些查詢都會接受預先配置的 "TopologyResult" 結構陣列。 "LocationCount" 參數會指定傳入陣列的長度。 傳回值會報告傳回位置的數目。 這個數位絕不會大於傳入的 "locationCount" 參數。

"TopologyResult" 包含所傳回之磁片區的中心位置、面向的方向（也就是一般），以及所找到空間的維度。

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

請注意，在 Unity 範例中，每個查詢都會連結到虛擬 UI 面板中的按鈕。 範例會將這些查詢的參數硬編碼成合理的值。 如需更多範例，請參閱範例程式碼中的 SpaceVisualizer.cs。

### <a name="shape-queries"></a>圖形查詢

在 dll 內，圖形分析器（"ShapeAnalyzer_W"）會使用拓撲分析器來比對使用者所定義的自訂圖形。 Unity 範例會定義一組圖案，並透過 [圖形] 索引標籤內的 [應用程式內查詢] 功能表來公開結果。其目的在於，使用者可以定義自己的物件圖形查詢，並依其應用程式的需求來使用這些查詢。

請注意，圖形分析僅適用于水準表面。 例如，沙發是由平面上表面和沙發的平面上方所定義。 圖形查詢會尋找指定大小、高度和外觀範圍的兩個表面，並對齊並連接兩個表面。 使用 Api 術語，沙發基座和後端是圖形元件，而對齊需求是圖形元件條件約束。

在 Unity 範例（ShapeDefinition.cs）中定義的範例查詢，適用于 "sittable" 物件，如下所示。

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

每個形狀查詢都是由一組圖形元件所定義，每個都有一組元件條件約束和一組圖形條件約束，以列出元件之間的相依性。 這個範例包含單一元件定義中的三個條件約束，而且元件之間沒有任何圖形條件約束（因為只有一個元件）。

相反地，「沙發」圖形有兩個「圖形」元件和四個「形狀」條件約束。 請注意，元件是由使用者的元件清單中的索引所識別（在此範例中為0和1）。

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

Unity 模組中提供了包裝函式，可讓您輕鬆地建立自訂圖形定義。 元件和圖形條件約束的完整清單可在 "ShapeComponentConstraint" 和 "ShapeConstraint" 結構內的 "SpatialUnderstandingDll.cs" 中找到。

在此介面上找到 ![矩形圖形](images/su-shapequery-300px.jpg)<br>
*在此介面上找到矩形圖形*

### <a name="object-placement-solver"></a>物件放置規劃求解

物件放置規劃求解可用於識別實體空間中的理想位置，以放置您的物件。 在指定物件規則和條件約束的情況下，規劃求解會尋找最適合的位置。 此外，物件查詢會持續存在，直到移除具有 "Solver_RemoveObject" 或 "Solver_RemoveAllObjects" 呼叫的物件為止，允許限制多物件放置。 物件放置查詢包含三個部分：具有參數的放置類型、規則清單和條件約束清單。 若要執行查詢，請使用下列 API。

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

此函式會接受物件名稱、位置定義，以及規則和條件約束的清單。 C#包裝函式提供了結構協助程式函式，讓規則和條件約束結構更輕鬆。 放置定義包含查詢類型，也就是下列其中一項。

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

每個放置類型都具有類型特有的一組參數。 "ObjectPlacementDefinition" 結構包含一組用來建立這些定義的靜態 helper 函式。 例如，若要尋找將物件放在樓層的位置，您可以使用下列函數。 public static ObjectPlacementDefinition Create_OnFloor （Vector3 halfDims）除了放置類型之外，您還可以提供一組規則和條件約束。 無法違反規則。 接著，符合類型和規則的可能位置位置會針對條件約束集合進行優化，以便選取最佳的放置位置。 每個規則和條件約束都可以由提供的靜態建立函式來建立。 以下提供範例規則和條件約束結構函數。

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

下列物件放置查詢正在尋找一個位置，將半計量 cube 放在表面的邊緣，而不是從其他先前放置的物件，靠近房間的中心。

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

如果成功，則會傳回包含放置位置、維度和方向的 "ObjectPlacementResult" 結構。 此外，放置會加入至 dll 的已放置物件的內部清單。 後續的放置查詢將會將此物件列入考慮。 Unity 範例中的 "LevelSolver.cs" 檔案包含更多範例查詢。

![物件位置的結果](images/su-objectplacement-1000px.jpg)<br>
*圖3：藍色方塊如何從相機位置規則的三個位置查詢結果*

解決層級或應用程式案例所需之多個物件的放置位置時，首先要解決不可或缺和大型的物件，以達到最大的可找到空間的機率。 放置順序很重要。 如果找不到物件位置，請嘗試較不受限制的設定。 具有一組回溯設定對於跨多個房間設定支援功能非常重要。

### <a name="room-scanning-process"></a>房間掃描程式

雖然 HoloLens 提供的空間對應解決方案的設計是為了符合整個範圍問題空間的需求，但空間理解模組是為了支援兩個特定遊戲的需求而打造。 其解決方案是以特定的程式和假設集為結構，如下所示。

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

使用者導向的 playspace 「繪製」–在掃描階段，使用者移動並尋找播放步調，有效地繪製應該包含的區域。 產生的網格非常重要，可在此階段提供使用者意見反應。 室內家用或 office 安裝程式–查詢函式是以適當角度針對平面和牆而設計的。 這是一項軟性限制。 不過，在掃描階段，主要軸分析會完成，以優化主要和次要軸的網格鑲嵌。 內含的 SpatialUnderstanding.cs 檔案會管理掃描階段程式。 它會呼叫下列函數。

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

由 "SpatialUnderstanding" 行為驅動的掃描流程會呼叫 InitScan，然後 UpdateScan 每個畫面格。 當統計資料查詢報告合理的涵蓋範圍時，允許使用者 airtap 呼叫 RequestFinish，以指示掃描階段結束。 UpdateScan 會繼續呼叫，直到它的傳回值指出 dll 已完成處理。

### <a name="understanding-mesh"></a>瞭解網格

瞭解 dll 會在內部將 playspace 儲存為8cm 大小體素 cube 的方格。 在掃描的初始部分期間，主要元件分析會完成以判斷房間的軸。 就內部而言，它會儲存其對應至這些座標軸的體素空間。 從體素磁片區解壓縮 isosurface，大約每秒會產生一次網格。 

從體素磁片區產生的 ![產生的網格](images/su-custommesh.jpg)<br>
*從體素磁片區產生的網格*

## <a name="troubleshooting"></a>[疑難排解]
* 請確定您已設定[SpatialPerception](#setting-the-spatialperception-capability)功能
* 當追蹤遺失時，下一個 OnSurfaceChanged 事件將會移除所有的網格。

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a>混合現實工具組中的空間對應
如需搭配使用空間對應與混合現實工具組 v2 的詳細資訊，請參閱 MRTK 檔的<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">空間感知一節</a>。

## <a name="see-also"></a>請參閱
* [MR 空間230：空間對應](holograms-230.md)
* [座標系統](coordinate-systems.md)
* [Unity 中的座標系統](coordinate-systems-in-unity.md)
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>
* <a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine. MeshFilter</a>
* <a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine. MeshCollider</a>
* <a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine. 界限</a>
