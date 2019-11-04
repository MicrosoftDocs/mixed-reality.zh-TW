---
title: 案例研究-擴充 HoloLens 的空間對應功能
description: 建立 Microsoft HoloLens 的第一個應用程式時，我們正積極看到我們可以在裝置上推送空間對應界限的程度。
author: jevertt
ms.author: jemccull
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、空間對應
ms.openlocfilehash: 5142cb383d4408b29eb17eb5ede84d19b2533dc4
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436729"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a>案例研究-擴充 HoloLens 的空間對應功能

建立 Microsoft HoloLens 的第一個應用程式時，我們正積極看到我們可以在裝置上推送空間對應界限的程度。 Jeff Evertt 是 Microsoft 工作室的軟體工程師，說明如何開發新的技術，以更充分掌控在使用者的真實世界環境中如何放置全息影像。

> [!NOTE]
> HoloLens 2 實行新的[場景理解運行](scene-understanding.md)時間，為混合現實開發人員提供結構化的高階環境標記法，其設計目的是為了讓環保感知應用程式的開發更加直覺。 

## <a name="watch-the-video"></a>觀看影片

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a>超出空間對應

雖然我們正在處理[片段](https://www.microsoft.com/p/fragments/9nblggh5ggm8)和[年輕 Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1)，但我們發現 HoloLens 的第一場遊戲，在實際執行的是在實體世界中進行全息的程式化時，我們需要更深入瞭解使用者的環境. 每個遊戲都有自己特定的位置需求：在片段中，我們想要能夠區別不同的表面（例如樓層或資料表），以將線索放在相關的位置。 我們也想要能夠找出生活大小的全像是沙發或椅子的表面。 在年輕的 Conker 中，我們希望 Conker 和他的對手能夠在玩家的房間中，以平臺的形式使用凸起的表面。

[Asobo 工作室](https://www.asobostudio.com/index.html)是適用于這些遊戲的開發合作夥伴，面對這個問題所在，並建立了一項技術來擴充 HoloLens 的空間對應功能。 使用這種方式，我們可以分析玩家的房間，並找出牆、表格、椅子和樓層等表面。 它也讓我們能夠優化一組條件約束，以判斷全像攝影物件的最佳位置。

## <a name="the-spatial-understanding-code"></a>空間理解程式碼

我們採用 Asobo 的原始程式碼，並建立封裝這項技術的程式庫。 Microsoft 和 Asobo 現已開放原始碼，並將其提供給[MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) ，供您在自己的專案中使用。 包含所有原始程式碼，讓您可以依據自己的需求進行自訂，並與您的社區分享您的改進。 此C++規劃求解的程式碼已包裝成 UWP DLL，並使用[包含在 MixedRealityToolkit 內的下拉式 Prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding)公開至 Unity。

Unity 範例中包含許多有用的查詢，可讓您在牆上尋找空的空間、將物件放在最上方或較大的空間上、找出要放置的字元位置，以及其他許多空間理解查詢。

雖然 HoloLens 提供的空間對應解決方案的設計是為了符合整個範圍問題空間的需求，但空間理解模組是為了支援兩個特定遊戲的需求而打造。 因此，其解決方案的結構是以特定的程式和假設的集合為根據：
* **固定大小 playspace**：使用者指定 init 呼叫中的最大 playspace 大小。
* 單次掃描程式：此程式需要一**段**獨立的掃描階段，使用者會在此逐步解說，定義 playspace。 在完成掃描之後，查詢函數才會運作。
* **使用者導向的 playspace 「繪製**」：在掃描階段，使用者會移動並尋找 playspace，有效地繪製應該包含的區域。 產生的網格非常重要，可在此階段提供使用者意見反應。
* **室內家用或 office 安裝程式**：查詢函式是以適當角度針對平面和牆而設計的。 這是一項軟性限制。 不過，在掃描階段，主要軸分析會完成，以優化主要和次要軸的網格鑲嵌。

### <a name="room-scanning-process"></a>房間掃描程式

當您載入空間理解模組時，您要做的第一件事就是掃描您的空間，如此一來，所有可用的表面（例如樓層、上限和牆）都會被識別和標示。 在掃描過程中，您會尋找您的聊天室，並「繪製」應該包含在掃描中的區域。

在這個階段中看到的網格是一項很重要的視覺化意見反應，可讓使用者知道房間的哪些部分正在進行掃描。 空間理解模組的 DLL 會在內部將 playspace 儲存為8cm 大小體素 cube 的方格。 在掃描的初始部分期間，主要元件分析會完成以判斷房間的軸。 就內部而言，它會儲存其對應至這些座標軸的體素空間。 從體素磁片區解壓縮 isosurface，大約每秒會產生一次網格。

![空間對應網格（白色）和瞭解 playspace 網格（綠色）](images/spatial-mapping-500px.png)

空間對應網格（白色）和瞭解 playspace 網格（綠色）



內含的 SpatialUnderstanding.cs 檔案會管理掃描階段程式。 它會呼叫下列函數：
* **SpatialUnderstanding_Init**：在開始時呼叫一次。
* **GeneratePlayspace_InitScan**：表示掃描階段應開始。
* **GeneratePlayspace_UpdateScan_DynamicScan**：呼叫每個畫面格，以更新掃描程式。 相機位置和方向會傳入，並用於 playspace 繪製進程，如上所述。
* **GeneratePlayspace_RequestFinish**：呼叫以完成 playspace。 這會使用掃描階段期間「已繪製」的區域來定義和鎖定 playspace。 應用程式可以在掃描階段查詢統計資料，以及查詢自訂網格以提供使用者意見反應。
* **Import_UnderstandingMesh**：在掃描期間，模組所提供並放在「瞭解」 Prefab 的**SpatialUnderstandingCustomMesh**行為，會定期查詢進程所產生的自訂網格。 此外，這項作業會在完成掃描之後再進行一次。

**SpatialUnderstanding**行為所驅動的掃描流程會呼叫**InitScan**，然後**UpdateScan**每個畫面格。 當統計資料查詢報告合理的涵蓋範圍時，使用者可以 airtap 呼叫**RequestFinish**來表示掃描階段結束。 **UpdateScan**會繼續呼叫，直到它的傳回值指出 DLL 已完成處理。

## <a name="the-queries"></a>查詢

掃描完成之後，您將能夠在介面中存取三種不同類型的查詢：
* **拓撲查詢**：這些是根據掃描聊天室拓撲的快速查詢。
* **成形查詢**：這些會利用拓撲查詢的結果來尋找與您定義的自訂圖形非常相符的水準表面。
* **物件放置查詢**：這些是更複雜的查詢，可根據物件的一組規則和條件約束，尋找最適合的位置。

除了三個主要查詢以外，還有一個 raycasting 介面可用來取出標記的表面類型，而自訂的防水室網格則可以複製出來。

### <a name="topology-queries"></a>拓撲查詢

在 DLL 中，拓撲管理員會處理環境的標籤。 如先前所述，大部分的資料會儲存在 surfels 中，並包含在體素磁片區中。 此外， **PlaySpaceInfos**結構是用來儲存 playspace 的相關資訊，包括世界對齊（更多詳細資料，如下所示）、樓層和上限高度。

啟發學習法是用來決定樓層、上限和牆。 例如，具有大於1個 m2 介面區的最大和最低水準表面會視為樓層。 請注意，在掃描過程中的相機路徑也會在此程式中使用。

拓撲管理員所公開的查詢子集會透過 DLL 公開。 公開的拓撲查詢如下所示：
* QueryTopology_FindPositionsOnWalls
* QueryTopology_FindLargePositionsOnWalls
* QueryTopology_FindLargestWall
* QueryTopology_FindPositionsOnFloor
* QueryTopology_FindLargestPositionsOnFloor
* QueryTopology_FindPositionsSittable

每個查詢都有一組參數，特定于查詢類型。 在下列範例中，使用者會指定所需磁片區的最小高度 & 寬度、樓層上方的最小放置高度，以及該磁片區前方的最小間隙量。 所有的測量單位都是計量。




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

這些查詢都會接受預先配置的**TopologyResult**結構陣列。 **LocationCount**參數會指定傳入陣列的長度。 傳回值會報告傳回位置的數目。 這個數位絕不會大於傳入的**locationCount**參數。

**TopologyResult**包含所傳回之磁片區的中心位置、面向的方向（也就是一般），以及所找到空間的尺寸。




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

請注意，在 Unity 範例中，每個查詢都會連結到虛擬 UI 面板中的按鈕。 範例會將這些查詢的參數硬編碼成合理的值。 如需更多範例，請參閱範例程式碼中的*SpaceVisualizer.cs* 。

### <a name="shape-queries"></a>圖形查詢

在 DLL 內，「圖形分析器」（**ShapeAnalyzer_W**）會使用「拓撲分析器」比對使用者所定義的自訂圖形。 Unity 範例具有一組預先定義的圖形，會顯示在 [圖形] 索引標籤上的 [查詢] 功能表中。

請注意，圖形分析僅適用于水準表面。 例如，沙發是由平面上表面和沙發的平面上方所定義。 圖形查詢會尋找指定大小、高度和外觀範圍的兩個表面，並對齊並連接兩個表面。 使用 Api 詞彙，沙發基座和沙發背面是圖形元件，而對齊需求是圖形元件條件約束。

在 Unity 範例（**ShapeDefinition.cs**）中定義的範例查詢，適用于 "sittable" 物件，如下所示：




```
shapeComponents = new List<ShapeComponent>()
     {
          new ShapeComponent(
               new List<ShapeComponentConstraint>()
               {
                    ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
                    ShapeComponentConstraint.Create_SurfaceCount_Min(1),
                    ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
               }),
     };
     AddShape("Sittable", shapeComponents);
```

每個形狀查詢都是由一組圖形元件所定義，每個都有一組元件條件約束和一組圖形條件約束，以列出元件之間的相依性。 這個範例包含單一元件定義中的三個條件約束，而且元件之間沒有任何圖形條件約束（因為只有一個元件）。

相反地，「沙發」圖形有兩個「圖形」元件和四個「形狀」條件約束。 請注意，元件是由使用者的元件清單中的索引所識別（在此範例中為0和1）。




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

Unity 模組中提供了包裝函式，可讓您輕鬆地建立自訂圖形定義。 元件和圖形條件約束的完整清單可在**ShapeComponentConstraint**和**ShapeConstraint**結構內的**SpatialUnderstandingDll.cs**中找到。

![藍色矩形會反白顯示「椅子圖形」查詢的結果。](images/chair-shape-query-500px.png)

藍色矩形會反白顯示「椅子圖形」查詢的結果。



### <a name="object-placement-solver"></a>物件放置規劃求解

物件放置查詢可以用來識別實體空間中的理想位置，以放置您的物件。 在指定物件規則和條件約束的情況下，此規劃求解會尋找最適合的位置。 此外，物件查詢會持續存在，直到使用**Solver_RemoveObject**或**Solver_RemoveAllObjects**呼叫移除物件為止，允許受限制的多物件放置。

物件放置查詢包含三個部分：具有參數的放置類型、規則清單和條件約束清單。 若要執行查詢，請使用下列 API：




```
public static int Solver_PlaceObject(
                [In] string objectName,
                [In] IntPtr placementDefinition,    // ObjectPlacementDefinition
                [In] int placementRuleCount,
                [In] IntPtr placementRules,         // ObjectPlacementRule
                [In] int constraintCount,
                [In] IntPtr placementConstraints,   // ObjectPlacementConstraint
                [Out] IntPtr placementResult)
```
此函式會接受物件名稱、位置定義，以及規則和條件約束的清單。 包裝C#函式提供了結構協助程式函式，讓規則和條件約束結構更輕鬆。 放置定義包含查詢類型，也就是下列其中一項：




```
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

每個放置類型都具有類型特有的一組參數。 **ObjectPlacementDefinition**結構包含一組用來建立這些定義的靜態 helper 函式。 例如，若要尋找將物件放在樓層的位置，您可以使用下列函數： 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

除了放置類型之外，您還可以提供一組規則和條件約束。 無法違反規則。 接著，符合類型和規則的可能位置位置會根據條件約束的集合進行優化，以選取最佳的放置位置。 每個規則和條件約束都可以由提供的靜態建立函式來建立。 以下提供範例規則和條件約束結構函數。




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

下面的物件放置查詢會尋找一個位置，將半計量 cube 放在表面的邊緣，而不是從其他先前放置的物件，靠近房間的中心。




```
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

如果成功，則會傳回包含放置位置、維度和方向的**ObjectPlacementResult**結構。 此外，放置會加入至 DLL 的已放置物件的內部清單。 後續的放置查詢將會將此物件列入考慮。 Unity 範例中的**LevelSolver.cs**檔案包含更多範例查詢。

![藍色方塊會顯示三個位置查詢的結果，其中包含「遠離相機位置」規則。](images/away-from-camera-position-500px.png)

藍色方塊會顯示三個位置查詢的結果，其中包含「遠離相機位置」規則。


**各種**
* 解決層級或應用程式案例所需之多個物件的放置位置時，首先要解決不可或缺和大型的物件，以最大化找出空間的機率。
* 放置順序很重要。 如果找不到物件位置，請嘗試較不受限制的設定。 具有一組回溯設定對於跨多個房間設定支援功能非常重要。

### <a name="ray-casting"></a>光線轉換

除了三個主要查詢以外，光線轉型介面可以用來抓取已標記的表面型別，而自訂的防水 playspace 網格可以在掃描完房間之後複製出來，而標籤則會在內部為表面產生，如下圖所示：樓層、上限和牆。 **PlayspaceRaycast**函式會採用光線，並在光線與已知表面衝突時傳回，如果是，則會傳回該介面的相關資訊（以**RaycastResult**的形式呈現）。 


```
struct RaycastResult
     {
          enum SurfaceTypes
          {
               Invalid, // No intersection
               Other,
               Floor,
               FloorLike,         // Not part of the floor topology, 
                                  //     but close to the floor and looks like the floor
               Platform,          // Horizontal platform between the ground and 
                                  //     the ceiling
               Ceiling,
               WallExternal,
               WallLike,          // Not part of the external wall surface, 
                                  //     but vertical surface that looks like a 
                                  //    wall structure
               };
               SurfaceTypes SurfaceType;
               float SurfaceArea;   // Zero if unknown 
                                        //  (i.e. if not part of the topology analysis)
               DirectX::XMFLOAT3 IntersectPoint;
               DirectX::XMFLOAT3 IntersectNormal;
     };
```

就內部而言，會針對 playspace 的計算8cm 立方體素標記法來計算 raycast。 每個體素都包含一組具有已處理拓撲資料的 surface 元素（也稱為 surfels）。 交集的體素資料格內所包含的 surfels 會進行比較，並使用最符合的方式來查閱拓撲資訊。 此拓撲資料包含以**SurfaceTypes**列舉的形式傳回的標籤，以及交集資料表面的介面區。

在 Unity 範例中，游標會將光線轉換成每個畫面格。 首先，針對 Unity 的 colliders;第二，針對瞭解模組的世界標記法;最後，針對 UI 元素。 在此應用程式中，UI 會取得優先順序，然後是瞭解結果，最後是 Unity 的 colliders。 **SurfaceType**會回報為游標旁的文字。

![Raycast 與樓層的結果報告交集。](images/raycast-result-500px.jpg)

Raycast 與樓層的結果報告交集。


## <a name="get-the-code"></a>取得程式碼

[MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)中提供開放原始碼程式碼。 如果您使用專案中的程式碼，請在[HoloLens 開發人員論壇](https://forums.hololens.com/)上讓我們知道。 我們無法等您瞭解如何處理！

## <a name="about-the-author"></a>關於作者

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <b>Jeff Evertt</b>是一家從 incubation 到經驗開發以來，曾經開始使用 HoloLens 的軟體工程組長。 在 HoloLens 之前，他曾在各種平臺和遊戲的 Xbox Kinect 和遊戲產業中工作。 Jeff 的熱衷於是關於機器人、圖形和亮色燈的問題。 他喜歡學習新事物，以及處理軟體、硬體，尤其是在這兩個交集的空間中。</td>
</tr>
</table>



## <a name="see-also"></a>請參閱
* [空間對應](spatial-mapping.md)
* [場景理解](scene-understanding.md)
* [空間位置掃描視覺效果](room-scan-visualization.md)
* [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Asobo Studio： HoloLens 開發第一線的課程](https://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
