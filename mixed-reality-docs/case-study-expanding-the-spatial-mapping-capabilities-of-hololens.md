---
title: 案例研究-擴展 HoloLens 空間對應功能
description: 當建立我們的第一個應用程式的 Microsoft HoloLens，我們想要看到我們可以就遠推送空間對應的界限在裝置上。
author: jevertt
ms.author: jevertt
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，HoloLens，空間對應
ms.openlocfilehash: 602b629afa5900ff34c28b3a3a32725af06590b7
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595755"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a>案例研究-擴展 HoloLens 空間對應功能

當建立我們的第一個應用程式的 Microsoft HoloLens，我們想要看到我們可以就遠推送空間對應的界限在裝置上。 Jeff Evertt，Microsoft Studios 的軟體工程師會說明如何從需要更充分掌控全像投影會放在使用者的實際操作環境的方式開發新的技術。

## <a name="watch-the-video"></a>觀看影片

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a>超出空間對應

雖然我們已努力[片段](https://www.microsoft.com/p/fragments/9nblggh5ggm8)並[Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1)、 兩個 HoloLens 的第一個遊戲，我們發現當我們的全像投影在真實世界的程序位置，我們需要更高的層級了解使用者的環境。 每個遊戲都有它自己的特定位置需求：片段，比方說，我們想要能夠區分不同的介面 — 例如最低限度值或資料表，將相關的位置中的線索。 我們也想要能夠識別介面，例如沙發或椅子，坐 life-size 全像攝影版的字元。 在 Young Conker 我們想 Conker 和他的對手，若要能夠在玩家的房間內引發的介面作為平台。

[Asobo Studios](http://www.asobostudio.com/index.html)，適用於這些遊戲中，我們開發的合作夥伴來解決標題面臨這個問題，並建立擴充的 HoloLens 空間的對應功能的技術。 使用這種情況，我們就可以分析玩家的空間，並識別介面，例如牆壁、 資料表、 椅子和樓層。 它也讓我們能夠最佳化對一組條件約束，來判斷最佳放置全像攝影版的物件。

## <a name="the-spatial-understanding-code"></a>空間的了解程式碼

我們花了 Asobo 的原始程式碼，並建立封裝這項技術的文件庫。 Microsoft Asobo 現在開放原始碼這段程式碼，以及擁有上開放[MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping)供您使用您自己的專案中。 所有的原始程式碼，會包含可讓您根據您的需求進行自訂，並與社群分享您的增強功能。 程式碼C++已經包裝成 UWP DLL 並公開至 Unity 中使用求解[掉落 prefab 內含 MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding)。

有許多有用的查詢包含在 Unity 範例可讓您尋找在牆上的空白空間，將物件放上或在地板上的大型空間上，找出的字元坐著和各種其他空間的了解查詢的位置。

雖然 HoloLens 所提供的空間對應解決方案設計為泛型程度足以符合完整的問題空間一系列的需求，以支援的兩個特定的遊戲需要建置空間的了解模組。 因此，其解決方案被圍繞的特定處理程序和假設組：
* **固定大小 playspace**:使用者初始呼叫中指定的最大 playspace 大小。
* **單次掃描處理序**:此程序需要離散掃描的階段的使用者將周圍的引導，定義 playspace。 掃描已完成之後，查詢函數將不會運作之前。
* **使用者導向 playspace"繪圖"**:在掃描階段中，使用者會移動，並尋找周圍 playspace，有效地繪製應該包含的區域。 產生的網狀結構，務必在這個階段期間提供使用者意見反應。
* **室內住家或辦公室安裝**:查詢函式被專為一般的介面及背景牆直角。 這是軟性限制。 不過，在掃描階段中，主座標軸分析會完成最佳化網狀結構鑲嵌式主要和次要軸。

### <a name="room-scanning-process"></a>聊天室掃描程序

當您載入的空間的了解模組時，您將會的先掃描您的空間，因此，所有可用的介面 — 例如 floor、 ceiling 和牆，識別出並標示為。 在掃描過程中，您看一下您的會議室和 「 小畫家 ' 應該在掃描中包含的區域。

在這個階段期間看到網格就是聊天室的一項重要的視覺回饋，可讓使用者知道正被掃描的哪些部分。 空間的了解模組 DLL 在內部儲存 playspace，以調整大小的 8 cm voxel cube 的方格。 在掃描的初始部分，主要元件分析完成來決定座標軸的聊天室。 就內部而言，它會儲存這些軸對齊其 voxel 空間。 網格會產生大約每秒擷取 isosurface voxel 磁碟區。

![空間對應以白色的網狀結構和了解 playspace mesh 中綠色](images/spatial-mapping-500px.png)

空間對應以白色的網狀結構和了解 playspace mesh 中綠色



包含的 SpatialUnderstanding.cs 檔案管理掃描階段的程序。 它會呼叫下列函數：
* **SpatialUnderstanding_Init**:在開始時，請呼叫一次。
* **GeneratePlayspace_InitScan**:指出應該開始掃描階段。
* **GeneratePlayspace_UpdateScan_DynamicScan**:每個畫面呼叫來更新掃描程序。 鏡頭位置和方向傳遞，且用於 playspace 繪製程序，上面所述。
* **GeneratePlayspace_RequestFinish**:呼叫以完成 playspace。 這將使用 「 繪製 「 掃描階段期間的區域，以定義並鎖定 playspace。 應用程式可以查詢統計資料期間掃描階段，以及查詢自訂的網狀結構，提供使用者意見反應。
* **Import_UnderstandingMesh**:在掃描期間， **SpatialUnderstandingCustomMesh**模組所提供，並放在了解 prefab 的行為會定期查詢自訂處理序所產生的網格。 此外，這是一次之後掃描已完成。

掃描流程，由驅動**SpatialUnderstanding**行為會呼叫**InitScan**，然後**UpdateScan**每個畫面格。 當統計資料的查詢報告合理的涵蓋範圍時，使用者可以呼叫 airtap **RequestFinish**表示 「 掃描 」 階段的結束。 **UpdateScan**呼叫傳回之前會繼續值會指出 DLL 已完成處理。

## <a name="the-queries"></a>查詢

掃描完成之後，您將能夠存取的介面中查詢的三種不同類型：
* **拓撲查詢**:這些是房間的快速掃描的拓撲為基礎的查詢。
* **圖形查詢**:這些會利用拓撲查詢來尋找水平的介面，會以您定義的自訂圖形完全相符的結果。
* **物件放置查詢**:這些是更複雜的查詢尋找一組規則和條件約束的物件為基礎的自動調整的位置。

除了三個主要的查詢，raycasting 介面可用來擷取已加上標記的介面型別和自訂 watertight 聊天室網格可以複製出來。

### <a name="topology-queries"></a>查詢拓撲

Dll 拓樸管理員會處理環境的標記。 如先前所述，大部分的資料會儲存在 surfels，內含 voxel 磁碟區。 颾魤 ㄛ **PlaySpaceInfos**結構用來儲存 playspace，包括 world 對齊 （下文詳細資料）、 floor、 ceiling 高度與相關資訊。

啟發學習法用於決定 floor、 ceiling 和牆。 比方說，有超過 1 m2 介面區的最大值與最低的水平的介面會被視為最低限度值。 請注意，在掃描程序期間的相機路徑也會在此程序。

子集拓樸管理員所公開的查詢會透過 DLL 公開出。 公開的拓樸查詢如下所示：
* QueryTopology_FindPositionsOnWalls
* QueryTopology_FindLargePositionsOnWalls
* QueryTopology_FindLargestWall
* QueryTopology_FindPositionsOnFloor
* QueryTopology_FindLargestPositionsOnFloor
* QueryTopology_FindPositionsSittable

每個查詢都有特定查詢型別參數組。 在下列範例中，使用者會指定最小高度和寬度所需的磁碟區、 樓層、 窗格和前面的磁碟區的許可的最小數量的最小的放置高度。 所有度量均是以公尺為單位。




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

這些查詢會取得預先配置的陣列**TopologyResult**結構。 **LocationCount**參數會指定傳入之陣列的長度。 傳回值會報告傳回的位置數目。 這個數字絕不會大於傳入**locationCount**參數。

**TopologyResult**包含傳回的磁碟區、 面向的方向 （也就是一般） 和維度的找到空間的中心位置。




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

請注意，在 Unity 範例中，這些查詢連結至虛擬 UI 面板中的按鈕。 硬碟的範例程式碼參數，這些查詢能夠合理值的每個。 請參閱*SpaceVisualizer.cs*範例程式碼，如需其他範例。

### <a name="shape-queries"></a>圖形查詢

DLL 時，圖形分析器內 (**ShapeAnalyzer_W**) 要比對由使用者定義的自訂圖形會使用拓撲分析器。 Unity 範例有一組預先定義的圖形查詢 功能表的 圖形 索引標籤上所示。

請注意，水平介面僅適用於圖形分析。 沙發上，比方說，是由一般基座介面和一般頂端的沙發上一步的定義。 Shape 查詢會尋找的特定大小、 頁高及長寬範圍，以對齊，且已連線的兩個介面的兩個介面。 使用 Api 術語，沙發車座和沙發背面的頂端是圖案元件與需求的對齊圖形元件的限制。

Unity 範例中定義的範例查詢 (**ShapeDefinition.cs**)、 「 sittable"物件如下所示：




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

每個圖形查詢是由一組圖形元件，各有一組元件條件約束和一組列出元件之間的相依性圖形的條件約束的定義。 此範例包含三個條件約束的單一元件定義及元件之間沒有任何圖形條件約束 （因為只有一個元件）。

相反地，沙發圖形有兩個圖形的元件和四個圖形的條件約束。 請注意，（0 到 1，在此範例中），使用者的元件清單中的其索引所識別的元件。




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

在 Unity 模組提供包裝函式函數，讓您輕鬆建立自訂圖形定義。 元件和圖形的條件約束的完整清單可在**SpatialUnderstandingDll.cs**內**ShapeComponentConstraint**並**ShapeConstraint**結構。

![藍色矩形反白顯示椅子 shape 查詢的結果。](images/chair-shape-query-500px.png)

藍色矩形反白顯示椅子 shape 查詢的結果。



### <a name="object-placement-solver"></a>物件放置規劃求解

物件放置查詢可用來識別要放置您的物件的實體空間中的理想位置。 求解器將會尋找指定物件的規則和條件約束的自動調整的位置。 此外，物件查詢會一直保存到該物件中已移除**Solver_RemoveObject**或是**Solver_RemoveAllObjects**呼叫，允許限制多的物件位置。

物件放置查詢是由三個部分所組成： 參數、 一份規則與條件約束清單的位置類型。 若要執行查詢時，使用下列 API:




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
此函數會接受物件名稱、 位置定義和規則和條件約束的清單。 C#包裝函式提供的建構可讓您輕鬆的規則和條件約束建構的 helper 函式。 放置定義包含查詢型別 — 也就是下列其中之一：




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

每個位置型別具有一組唯一類型的參數。 **ObjectPlacementDefinition**結構包含一組靜態的 helper 函式來建立這些定義。 例如，若要尋找之處，將物件放在地板上，您可以使用下列函式： 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

除了放置型別中，您可以提供一組規則和條件約束。 不能違反規則。 選取最佳的放置位置的條件約束的集合針對最適合然後滿足的類型與規則的可能的放置位置。 每個規則和條件約束可以提供靜態建立函式所建立。 如下所示的範例規則和條件約束建構函式。




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

下列物件放置查詢會尋找放介面的邊緣，一半的計量 cube、 遠離其他先前放置物件及附近的聊天室中央的地方。




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

如果成功， **ObjectPlacementResult**傳回結構，包含放置位置、 維度和方向。 此外，位置會加入 DLL 的內部放置的物件清單。 後續的放置查詢會將此物件納入考量。 **LevelSolver.cs** Unity 範例中的檔案包含更多的範例查詢。

![藍色方塊會顯示 立即從觀景窗位置 」 規則的三個位置上 Floor 查詢的結果。](images/away-from-camera-position-500px.png)

藍色方塊會顯示 立即從觀景窗位置 」 規則的三個位置上 Floor 查詢的結果。


**秘訣：**
* 解決層級或應用程式的案例所需的多個物件的放置位置，先解決不可或缺和大型物件，來最大化的空間，您可以找到的機率。
* 放置順序非常重要。 如果找不到物件的位置，請嘗試較不受條件約束的組態。 後援設定一組非常重要跨許多空間組態支援的功能。

### <a name="ray-casting"></a>光跡轉型

除了三個主要的查詢，光跡轉型介面可以用來擷取已加上標記的介面型別，而且可以複製自訂 watertight playspace 網狀結構出聊天室已進行掃描而且已完成之後, 標籤內部產生介面之類的floor、 ceiling，以及背景牆。 **PlayspaceRaycast**函式會採用無限遠的光線，並傳回如果光線衝突與已知的介面，而且如果是的話，該介面的表單中的相關資訊**RaycastResult**。 


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

就內部而言，raycast 會計算針對 playspace 計算立方的 8 cm voxel 表示法。 每個 voxel 包含一組已處理的拓撲資料 (也稱為 surfels) 的介面項目。 比較交集的 voxel 資料格內所含 surfels 和最符合項目用來查閱拓撲資訊。 此拓撲的資料包含標記的形式傳回**SurfaceTypes**列舉，以及在交集的介面的介面區。

在 Unity 範例中，資料指標會轉換每個畫面格無限遠的光線。 首先，針對 Unity colliders;第二，針對了解模組的世界表示法;而最後，針對 UI 項目。 在此應用程式中，UI 會取得優先權，了解結果，然後最後，Unity colliders。 **SurfaceType**回報為游標後面的文字。

![Raycast 結果報告使用最低限度值的交集。](images/raycast-result-500px.jpg)

Raycast 結果報告使用最低限度值的交集。


## <a name="get-the-code"></a>取得程式碼

開放原始碼程式碼位於[MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)。 讓我們知道[HoloLens 的開發人員論壇](https://forums.hololens.com/)如果您的專案中使用的程式碼。 期待看看您如何使用它 ！

## <a name="about-the-author"></a>關於作者

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <b>Jeff Evertt</b>是軟體工程潛在客戶曾 HoloLens 上早期以來，從 incubation 體驗開發。 HoloLens 之前, 他曾在 Xbox Kinect 上和在遊戲產業中，在各種不同的平台和遊戲。 Jeff 是熱衷於機器人、 圖形及亮色移嗶聲的號誌的事。 他喜歡學習新事物，並使用軟體，硬體，而且特別是在兩個相交所在的空間。</td>
</tr>
</table>



## <a name="see-also"></a>另請參閱
* [空間對應](spatial-mapping.md)
* [空間對應設計](spatial-mapping-design.md)
* [聊天室掃描視覺效果](room-scan-visualization.md)
* [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Asobo Studio:從 HoloLens 開發的 frontline 課程](http://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
