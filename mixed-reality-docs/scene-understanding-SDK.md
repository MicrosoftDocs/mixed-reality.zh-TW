---
title: 場景理解 SDK
description: 場景理解 SDK 的程式設計指南
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: 場景理解，空間對應，Windows Mixed Reality，Unity
ms.openlocfilehash: 2f958d45f72d6c39d4222840615c5b177db7c76f
ms.sourcegitcommit: 6d9d01d53137435c787f247f095d5255581695fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83228013"
---
# <a name="scene-understanding-sdk-overview"></a>場景理解 SDK 總覽

場景理解的目標是要轉換混合現實裝置所捕捉到的非結構化環境感應器資料，並將它轉換成可直覺且易於開發的功能強大但抽象化的標記法。 SDK 會作為應用程式與場景理解執行時間之間的通訊層。 其目的是要模擬現有的標準結構，例如3D 呈現的3D 場景圖形，以及2d 應用程式的2D 矩形和麵板。 雖然結構的場景理解模擬會對應到您可能使用的具體架構，但在一般的 SceneUnderstanding 中，不會有架構中立，允許在與它互動的不同架構之間進行交互操作。 隨著場景的理解發展，SDK 的角色是為了確保新的標記法和功能會繼續在統一的架構中公開。 在本檔中，我們會先引進高階概念，協助您熟悉開發環境/使用方式，然後針對特定的類別和結構提供更詳細的檔。

## <a name="where-do-i-get-the-sdk"></a>哪裡可以取得 SDK？

SceneUnderstanding SDK 可透過 NuGet 下載。

[SceneUnderstanding SDK](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

**注意：** 最新版本取決於預覽套件，而您必須啟用發行前版本套件才能看到它。

從版本 0.5.2022-rc，場景理解支援 c # 和 c + + 的語言投影，讓應用程式可以開發適用于 Win32 或 UWP 平臺的應用程式。 在此版本中，SceneUnderstanding 支援使用 unity 的編輯器支援，而使 SceneObserver 僅用於與 HoloLens2 通訊。 

SceneUnderstanding 需要18362或更高版本 Windows SDK。 

如果您在 Unity 專案中使用 SDK，請使用適用于[unity 的 NuGet](https://github.com/GlitchEnzo/NuGetForUnity)將套件安裝到您的專案中。

## <a name="conceptual-overview"></a>概觀說明

### <a name="the-scene"></a>場景

您的混合現實裝置會持續整合其在您環境中所見到的資訊。 場景瞭解漏斗圖所有這些資料來源，並產生一個單一的統一抽象概念。 場景理解會產生場景，這是代表單一事物（例如牆/天花板/樓層）實例的[SceneObjects](scene-understanding-SDK.md#sceneobjects)組合。場景物件本身是[SceneComponents](scene-understanding-SDK.md#scenecomponents)的組合，代表組成此 SceneObject 的更細微部分。 元件的範例包括四邊形和網格，但未來可能會代表周框方塊、碰撞網格、中繼資料等。

將原始感應器資料轉換成場景的程式，是可能耗費資源的作業，可能需要幾秒鐘的時間（約10x10m）到幾分鐘，才會有非常大的空間（~ 50x50m），因此不會在沒有應用程式要求的情況下，由裝置所計算的東西。 相反地，場景產生是由您的應用程式隨選觸發。 SceneObserver 類別具有可計算或還原序列化場景的靜態方法，您可以接著列舉/與之互動。 「計算」動作會隨選執行，並在 CPU 上執行，但在不同的進程（混合現實驅動程式）中執行。 不過，雖然我們會在另一個進程中計算，但產生的場景資料會儲存在應用程式的場景物件中並加以維護。 

以下圖表說明此流程流程，並顯示兩個應用程式與場景理解執行時間互動的範例。 

![處理圖表](images/SU-ProcessFlow.png)

左側是混合現實執行時間的圖表，它一律開啟並在自己的進程中執行。 此執行時間會負責執行裝置追蹤、空間對應，以及場景理解用來瞭解有關世界的原因的其他作業。 在圖表的右側，我們會顯示兩個理論上的應用程式，讓您使用場景理解。 第一個應用程式介面的 MRTK 會在內部使用場景理解 SDK，第二個應用程式會計算並使用兩個不同的場景實例。 此圖表中的所有3個場景都會產生不同的場景實例，而驅動程式不會追蹤全域狀態，而在某個場景中的應用程式和場景物件之間，則不會在另一個場景中找到。 場景理解提供一段時間的追蹤機制，但這是使用 SDK 來完成的，而執行這項追蹤的程式碼則是在應用程式的 SDK 中執行。

因為每個場景都會將它的資料儲存在您應用程式的記憶體空間中，所以您可以假設場景物件或其內部資料的所有函式一律會在應用程式的進程中執行。

### <a name="layout"></a>版面配置

若要使用場景理解，請務必瞭解並瞭解執行時間如何在邏輯上或實際地代表元件。 場景代表具有特定版面配置的資料，而該配置已選擇簡單，同時維持 pliable 以符合未來需求的基礎結構，而不需要主要的修訂。 此場景的運作方式是將所有元件（所有場景物件的建立區塊）儲存在一般清單中，並透過參考（其中特定元件會參考其他專案）來定義階層和組合。

在下方，我們以其平面和邏輯形式呈現結構的範例。

<table>
<tr><th>邏輯版面配置</th><th>實體配置</th></tr>
<tr>
<td>
<ul>
  場景
  <ul>
  <li>SceneObject_1
    <ul>
      <li>SceneMesh_1</li>
      <li>SceneQuad_1</li>
      <li>SceneQuad_2</li>
    </ul>
  </li>
  <li>SceneObject_2
    <ul>
      <li>SceneQuad_1</li>
      <li>SceneQuad_3</li>
      </li></ul>
  </li>
  <li>SceneObject_3
    <ul>
      <li>SceneMesh_3</li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li>SceneObject_1</li>
  <li>SceneObject_2</li>
  <li>SceneObject_3</li>
  <li>SceneQuad_1</li>
  <li>SceneQuad_2</li>
  <li>SceneQuad_3</li>
  <li>SceneMesh_1</li>
  <li>SceneMesh_2</li>
</ul>
</td>
</tr>
</table>

下圖將重點放在場景的實體和邏輯版面配置之間的差異。 在左側，我們會看到您的應用程式在列舉場景時所看到之資料的階層式配置。 在右側，我們看到場景實際上是由12個相異元件所組成，視需要個別存取。 在處理新場景時，我們預期應用程式會以邏輯方式將此階層引導，不過，在場景更新之間進行追蹤時，某些應用程式可能只會對以兩個場景之間共用的特定元件為目標感興趣。

## <a name="api-overview"></a>API 概觀

下一節提供場景理解中之結構的高階總覽。 閱讀本節可讓您瞭解場景的呈現方式，以及各種元件的用途/用途。 下一節將提供在此總覽中說明 mda 的具體程式碼範例和其他詳細資料。

以下所述的所有類型都位於 `Microsoft.MixedReality.SceneUnderstanding` 命名空間中。

### <a name="scenecomponents"></a>SceneComponents

現在您已瞭解幕後的邏輯版面配置，現在可以呈現 SceneComponents 的概念，以及如何使用它們來撰寫階層。 SceneComponents 是 SceneUnderstanding 中最細微的分解，代表單一核心的事物，例如網格或四個或周框方塊。 SceneComponents 是可以獨立更新並可由其他 SceneComponents 參考的專案，因此，它們有一個唯一識別碼的單一全域屬性，可允許這種類型的追蹤/參考機制。 識別碼用於場景階層的邏輯組合以及物件持續性（更新一個場景相對於另一個場景的動作）。 

如果您將每個新計算的場景都視為相異，而且只要列舉其中的所有資料，則識別碼對您而言都是透明的。 不過，如果您打算追蹤多個更新的元件，您會使用識別碼來編制索引，並尋找場景物件之間的 SceneComponents。

### <a name="sceneobjects"></a>SceneObjects

SceneObject 是一種 SceneComponent，代表「事物」的實例，例如牆、樓層、上限等等。以其 Kind 屬性工作表示。 SceneObjects 是幾何，因此具有在空間中代表其位置的函式和屬性，但不包含任何幾何或邏輯結構。 相反地，SceneObjects 參考其他 SceneComponents，特別是 SceneQuads 和 SceneMeshes，可提供系統支援的各種標記法。 計算新場景時，您的應用程式很可能會列舉場景的 SceneObjects 來處理其感興趣的內容。

SceneObjects 可以有下列任何一項：

<table>
<tr>
<th>SceneObjectKind</th> <th>說明</th>
</tr>
<tr><td>背景</td><td>已知 SceneObject<b>不</b>是其他可辨識類型的場景物件之一。 此類別不應與 [不明] 混淆，其中的背景已知不是牆/樓層/上限等等 .。。雖然不明尚未分類。</b></td></tr>
<tr><td>內牆</td><td>實體牆。 牆會假設為 immovable 環境結構。</td></tr>
<tr><td>樓層</td><td>樓層是其中一個可以進行的任何表面。 注意：樓梯不是樓層。 另請注意，該樓層會假設任何 walkable 介面，因此不會明確假設為單一樓層。 多層結構、斜坡等等 .。。全都分類為樓層。</td></tr>
<tr><td>Ceiling</td><td>房間的上方表面。</td></tr>
<tr><td>平台</td><td>您可以放置全息影像的大型平面。 這些通常會代表資料表、countertops 和其他大型水準表面。</td></tr>
<tr><td>World</td><td>標記不可知之幾何資料的保留標籤。 藉由設定 EnableWorldMesh 更新旗標所產生的網格會分類為「世界」。</td></tr>
<tr><td>Unknown</td><td>這個場景物件尚未分類並指派一種類型。 這不應該與背景混淆，因為此物件可能是任何專案，系統還不會為其提供強大的分類。</td></tr>
</tr>
</table>

### <a name="scenemesh"></a>SceneMesh

SceneMesh 是一種 SceneComponent，其使用三角形清單來接近任意幾何物件的幾何。 SceneMeshes 是用於數個不同的內容中，它們可以代表防水資料格結構的元件，或做為 WorldMesh，代表與場景相關聯的未系結空間對應網格。 每個網格所提供的索引和頂點資料，都會使用與用來在所有新式轉譯 Api 中呈現三角形網格的[頂點和索引緩衝區](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx)相同的熟悉配置。 請注意，在場景理解中，網格會使用32位索引，而且可能需要細分為特定轉譯引擎的區塊。

#### <a name="winding-order-and-coordinate-systems"></a>纏繞順序和座標系統

場景理解所產生的所有網格預期會使用順時針的纏繞順序，在右手座標系統中傳回網格。 

注意：191105之前的作業系統組建可能有已知的錯誤，其中「世界」網格已以逆時針的纏繞順序傳回，而後續已修正此問題。

### <a name="scenequad"></a>SceneQuad

SceneQuad 是代表佔據3d 世界之2d 表面的 SceneComponent。 SceneQuads 的使用方式類似于 ARKit ARPlaneAnchor 或 ARCore 平面，但它們提供更高階的功能，做為一般應用程式或增強 UX 所使用的2d 畫布。 2D 特定 Api 是針對讓放置和版面配置便於使用的四邊形所提供，而使用四邊形的開發（除了轉譯外）應該比使用3d 網格更類似于2d 畫布。

#### <a name="scenequad-shape"></a>SceneQuad 圖形

SceneQuads 定義2d 中的界限矩形介面。 不過，SceneQuads 是以任意且可能複雜的圖形（例如環圈形的形狀表）來代表表面。若要表示四個表面的複雜圖形，您可以使用 GetSurfaceMask API，將介面的形狀轉譯至您所提供的影像緩衝區。 如果具有四個的 SceneObject 也有網格，則網格三角形應該等同于此轉譯影像，而兩者都代表表面的真正幾何，只是2d 或3d 座標。

## <a name="scene-understanding-sdk-details-and-reference"></a>場景瞭解 SDK 詳細資料和參考

下一節將協助您熟悉 SceneUnderstanding 的基本概念。 這一節應該會提供您基本知識，此時您應該有足夠的內容可以流覽範例應用程式，以查看如何全面性地使用 SceneUnderstanding。

### <a name="initialization"></a>初始化

使用 SceneUnderstanding 的第一個步驟是讓您的應用程式取得場景物件的參考。 這可以透過兩種方式的其中一種來完成，也可以由驅動程式來計算場景，或在過去計算的現有場景可以取消序列化。 後者特別適用于在開發期間使用 SceneUnderstanding，其中應用程式和體驗可以在沒有混合現實裝置的情況下快速建立原型。

場景會使用 SceneObserver 來計算。 在建立場景之前，您的應用程式應該查詢您的裝置，以確保它支援 SceneUnderstanding，以及要求使用者存取 SceneUnderstanding 所需的資訊。

```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

如果未呼叫 RequestAccessAsync （），則計算新場景將會失敗。 接下來，我們將計算一個以混合現實耳機為基礎的新場景，並具有10個計量半徑。

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.ComputeAsync(querySettings, 10.0f).GetAwaiter().GetResult();
```

### <a name="initialization-from-data-aka-the-pc-path"></a>從資料初始化（也稱為 電腦路徑）

雖然可以針對直接耗用量來計算場景，但也可以使用序列化形式來計算，以供稍後使用。 這已證明在開發時非常有用，因為它可讓開發人員在不需要裝置的情況下工作並測試場景理解。 將場景序列化的動作和計算方式幾乎相同，資料會傳回到您的應用程式，而不是由 SDK 在本機進行還原序列化。 接著，您可以自行將其還原序列化，或儲存以供日後使用。

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneBlob for later
```

### <a name="sceneobject-enumeration"></a>SceneObject 列舉

既然您的應用程式有一個場景，您的應用程式就會查看 SceneObjects 並與之互動。 這是藉由存取**SceneObjects**屬性來完成：

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

### <a name="component-update-and-re-finding-components"></a>元件更新和重新尋找元件

還有另一個函式可抓取場景中稱為***sys.application.findcomponent***的元件。 當更新追蹤物件，並在後續的幕後尋找時，此函式會很有用。 下列程式碼會計算相對於前一個場景的新場景，然後在新場景中尋找樓層。

```cs
// Compute a new scene, and tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.ComputeAsync(querySettings, 10.0f, myScene).GetAwaiter().GetResult();

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attached to this floor transform
}
```

## <a name="accessing-meshes-and-quads-from-scene-objects"></a>從場景物件存取網格和四邊形

一旦找到 SceneObjects，您的應用程式很可能會想要存取包含在其所組成之四邊形/網格中的資料。 此資料會使用***四邊形***和***網格***屬性來存取。 下列程式碼將列舉 floor 物件的所有四邊形和網格。

```cs

// Get the transform for the SceneObject
System.Numerics.Matrix4x4 objectToSceneOrigin = firstFloor.GetLocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

請注意，它是具有相對於場景原點之轉換的 SceneObject。 這是因為 SceneObject 代表「事物」的實例，並且會在空間中定位，四邊形和網格代表相對於其父系的轉換幾何。 不同的 SceneObjects 可以參考相同的 SceneMesh/SceneQuad SceneComponents，也可能是 SceneObject 有一個以上的 SceneMesh/SceneQuad。

### <a name="dealing-with-transforms"></a>處理轉換

在處理轉換時，場景理解已刻意嘗試配合傳統的3D 場景標記法。 因此，每個場景會限制為單一座標系統，與最常見的3D 環境表示相同。 SceneObjects 每個都會提供其位置作為座標系統內的位置和方向。 如果您的應用程式正在處理的場景會延伸單一來源提供的限制，可將 SceneObjects 錨定至 SpatialAnchors，或產生數個場景並將它們合併在一起，但為了簡單起見，我們假設防水場景存在於其本身的原始來源中，而這些專案是由場景所定義的一個同位來當地語系化。 OriginSpatialGraphNodeId。

例如，下列 Unity 程式碼示範如何使用 Windows 認知和 Unity Api，將座標系統對齊在一起。 如需有關如何取得對應于 Unity 世界來源的 SpatialCoordinateSystem，以及在和之間進行轉換的擴充方法，請參閱[SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem)和[SpatialGraphInteropPreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) ，以取得有關 Windows 認知 api 的詳細資料，以及[Unity 中的混合現實原生物件](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) `.ToUnity()` `System.Numerics.Matrix4x4` `UnityEngine.Matrix4x4` 。

```cs
public class SceneRootComponent : MonoBehavior
{
    public SpatialCoordinateSystem worldOrigin;
    public Scene scene;
    SpatialCoordinateSystem sceneOrigin;
    
    void Start()
    {
        // Initialize a SpatialCoordinateSystem for the scene's node in the system's Spatial Graph.
        scene.origin = SpatialGraphInteropPreview.CreateCoordinateSystemForNode(scene.OriginSpatialGraphNodeId);
    }
    
    void Update()
    {
        // Try to get the current transform of the scene's spatial graph node.
        // This may not be available, e.g. when tracking has been lost.
        var sceneToWorld = sceneOrigin.TryGetTransformTo(worldOrigin);
        if (sceneToWorld.HasValue)
        {
            // Convert the transform to Unity numerics and update the game object.
            var sceneToWorldUnity = sceneToWorld.Value.ToUnity();
            this.gameObject.transform.SetPositionAndRotation(sceneToWorldUnity.GetColumn(3), sceneToWorldUnity.rotation);
        }
    }
}
```

每個 `SceneObject` 都有一個 `Position` 和 `Orientation` 屬性，可用來定位相對於包含之來源的對應內容 `Scene` 。 例如，下列範例假設遊戲是場景根目錄的子系，並指派其本機位置和旋轉以配合指定的 `SceneObject` ：

```cs
void SetLocalTransformFromSceneObject(GameObject gameObject, SceneObject sceneObject)
{
    gameObject.transform.localPosition = sceneObject.Position.ToUnity();
    gameObject.transform.localRotation = sceneObject.Orientation.ToUnity());
}
```

### <a name="quad"></a>&

四邊形的設計目的是為了加速2D 放置案例，而且應該將其視為2D 畫布 UX 元素的擴充。 雖然四邊形是 SceneObjects 的元件，而且可以在3D 中轉譯，但四個 Api 本身會假設四邊形是2D 結構。 它們提供一些資訊，例如範圍、圖形，以及提供放置的 Api。

四邊形有矩形範圍，但它們代表任意形狀的2D 介面。 若要在這些2D 介面上啟用放置，這些介面會與3D 環境四邊形供應專案公用程式互動，以實現這種互動。 目前場景理解提供兩個這類函數： **FindCentermostPlacement**和**GetOcclusionMask**。 FindCentermostPlacement 是高階 API，它會找出可放置物件的四個位置，並嘗試尋找您的物件的最佳位置，以確保您提供的周框方塊會位於基礎介面上。

下列範例顯示如何尋找 centermost 可放置位置，並將全息圖形錨定到四個。

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new game object for the quad itself as a child of the scene root
                // Step 2: Set the local transform from quads[0].Position and quads[0].Orientation
                // Step 3: Create your hologram and set it as a child of the quad's game object
                // Step 4: Set the hologram's local transform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

步驟1-4 高度相依于您的特定架構/執行，但主題應該類似。 請務必注意，四個部分只代表在空間中當地語系化的界限2D 平面。 藉由讓您的引擎/架構知道四個的位置，並將您的物件與四個相對應，您的全息影像將會正確地放在真實世界。 如需詳細資訊，請參閱四邊形上的範例，其中會顯示特定的實作為。

### <a name="mesh"></a>網狀

網格代表物件或環境的幾何標記法。 與[空間對應](spatial-mapping.md)一樣，每個空間 surface 網格提供的網格索引和頂點資料，都會使用與在所有新式轉譯 api 中用來呈現三角形網格的頂點和索引緩衝區相同的熟悉配置。 頂點位置會在的座標系統中提供 `Scene` 。 用來參考此資料的特定 Api 如下所示：

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

下列程式碼提供從網格結構產生三角形清單的範例：

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

索引/頂點緩衝區必須 >= 索引/頂點計數，否則可以任意調整大小，以便有效率地重複使用記憶體。

## <a name="developing-with-scene-understandings"></a>使用場景稍微瞭解進行開發

此時，您應該瞭解場景瞭解執行時間和 SDK 的核心建立區塊。 大部分的威力和複雜度都是在存取模式中、與3D 架構的互動，以及可以在這些 Api 之上撰寫的工具，以執行更先進的工作，例如空間規劃、房間分析、流覽、物理等。我們希望能夠以適當的方式來捕捉這些範例，以讓您的案例更有説明。 如果有範例/案例未解決，請讓我們知道，我們會嘗試記錄/原型您需要的內容。

### <a name="where-can-i-get-sample-code"></a>哪裡可以取得範例程式碼？

您可以在我們的[Unity 範例頁面](https://github.com/sceneunderstanding-microsoft/unitysample)頁面上找到適用于 unity 的場景範例程式碼。 此應用程式可讓您與您的裝置通訊並轉譯各種場景物件，或者，它可讓您在電腦上載入序列化的場景，並讓您在不使用裝置的情況下體驗到場景的瞭解。

### <a name="where-can-i-get-sample-scenes"></a>哪裡可以取得範例場景？

如果您有 HoloLens2，可以將 ComputeSerializedAsync 的輸出儲存至檔案，並以您自己的便利性將它還原序列化，以儲存您所捕捉到的任何場景。 

如果您沒有 HoloLens2 裝置，但想要使用場景理解來播放，您必須下載預先捕捉的場景。 場景理解範例目前隨附于序列化的幕後，可供您自行下載並使用。 您可以在這裡找到：

[場景瞭解範例場景](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples/tree/master/Assets/Resources/SerializedScenesForPCPath)

## <a name="see-also"></a>請參閱

* [空間對應](spatial-mapping.md)
* [場景理解](scene-understanding.md)
* [Unity 範例](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)
