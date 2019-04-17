---
title: 在 Unity 中的座標系統
description: 了解如何建置讓您輕鬆工作，釐、 聊天室擴展和全球規模的混合實境體驗，在 Unity 中。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 座標系統、 空間座標系統、 方向、 插入擴充槽級別、 常設-小數位數的空間-調整、 全球規模，360 度，插入擴充槽，常設、 聊天室、 世界、 可調整、 位置、 方向、 Unity、 錨點、 空間的錨點、 世界錨點，世界鎖定世界鎖定，以鎖定主體，主體鎖定，追蹤遺失，locatability，範圍中，recenter
ms.openlocfilehash: 36d74488b23587e5c89b40faf97921a10be7473b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2019
ms.locfileid: "59597106"
---
# <a name="coordinate-systems-in-unity"></a>在 Unity 中的座標系統

Windows Mixed Reality 跨各種不同的支援應用程式[體驗標尺](coordinate-systems.md)，從僅限方向和插入擴充槽擴展應用程式向上透過空間調整應用程式。 上 HoloLens，您可以更進一步，和建置世界級應用程式，可讓使用者超過 5 公尺，逐步引導瀏覽整個樓層的建置和更新版本。

建置在 Unity 中的混合的實境體驗的第一個步驟是判斷哪些[體驗擴展](coordinate-systems.md)應用程式目標。

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>建立僅限方向或插入擴充槽-小數位數的體驗

**命名空間：***UnityEngine.XR*<br>
**類型：***XRDevice*

建置**僅限方向**或**插入擴充槽擴展經驗**，您必須設定 Unity 固定為追蹤的空間型別。 這會設定 Unity 的全局座標系統來追蹤[靜態參考座標系](coordinate-systems.md#spatial-coordinate-systems)。 在 「 定態的追蹤模式中，內容會放在編輯器中只前方相機的預設位置 （正向是-Z） 應用程式啟動時，會出現在使用者之前。

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**命名空間：***UnityEngine.XR*<br>
**類型：***InputTracking*

為純**僅限方向的體驗**例如 360 度視訊檢視器中 （其中位置標頭的更新會讓視覺效果），然後您可以設定[XR。InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html)設為 true:

```cs
InputTracking.disablePositionalTracking = true;
```

針對**安插擴展經驗**，以讓使用者稍後 recenter 安置的原點，您可以呼叫[XR。InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)方法：

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a>建置常設-小數位數或聊天室擴展經驗

**命名空間：***UnityEngine.XR*<br>
**類型：***XRDevice*

針對**常設擴展**或**聊天室擴展經驗**，您必須將內容放置相對於最低限度值。 您會理解使用者的 floor 使用**[空間階段](coordinate-systems.md#spatial-coordinate-systems)**、 樓層來源和選擇性空間界限代表使用者的定義、 設定期間第一次執行。

若要確保 Unity 使用其在 floor 層級的全局座標系統作業，您可以 Unity 設 RoomScale 追蹤空間類型，並確認集合成功：

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```
* Unity SetTrackingSpaceType 傳回 true，如果已順利切換來追蹤其全局座標系統[階段參照](coordinate-systems.md#spatial-coordinate-systems)。
* 如果 SetTrackingSpaceType 傳回 false，Unity 無法切換至階段參考框架，可能會因為使用者未設定即使在其環境中 floor 切換。 這並不常見，但如果階段已在不同房間內設定和裝置已移至目前的空間，而不需要新的階段中使用者的設定就會發生。

一旦您的應用程式已成功設定追蹤的空間型別，內容放在 y 軸上 RoomScale = 的 0 平面會出現在最低限度值。 （0，0，0） 處的原點，將會在最低限度值的空間在安裝期間，使用者名人-z 表示它們已在安裝期間對向的正向方向其中的特定位置。

**命名空間：***UnityEngine.Experimental.XR*<br>
**類型：***界限*

在指令碼，您可以呼叫您 TryGetGeometry 方法正在 UnityEngine.Experimental.XR.Boundary 型別，以取得界限的多邊形，然後指定 TrackedArea 界限類型。 如果使用者定義的界限 （得到頂點清單），您就會知道它是安全地傳遞**聊天室擴展經驗**給使用者，可以走的地方周圍場景您建立。

請注意，系統會自動轉譯界限使用者接近它時。 您的應用程式不需要使用此多邊形呈現本身的界限。 不過，您可以選擇使用此界限的多邊形，確保使用者可以實際連線到這些物件，而不需要 teleporting 場景物件的版面配置設定：

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a>建置全球規模的體驗

**命名空間：***UnityEngine.XR.WSA*<br>
**類型：***WorldAnchor*

代表 true**全球級別體驗**在讓使用者超過 5 公尺走廊的 HoloLens，您需要超過所使用的空間調整體驗的新技術。 您將使用的一個重要技術是建立[空間的錨點](coordinate-systems.md#spatial-anchors)鎖定精確地就地真實世界中，不論幅度有漫遊的使用者，在全像投影的叢集，然後[日後再次在尋找這些全像投影工作階段](coordinate-systems.md#spatial-anchor-persistence)。

在 Unity 中，您必須建立空間的錨點加入**WorldAnchor** Unity 元件的 GameObject。

### <a name="adding-a-world-anchor"></a>加入全球錨點

若要加入全球錨點，呼叫 AddComponent<WorldAnchor>遊戲和您想要將真實世界中的錨點的轉換物件上的 （)。

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

就這麼容易！ 此遊戲物件會立即錨定至真實世界的目前位置-您可能會看到一段時間，以確保該實體的對齊方式稍微調整其 Unity 全局座標。 使用[持續性](persistence-in-unity.md)可以找到此錨定位置一次在未來的應用程式工作階段。

### <a name="removing-a-world-anchor"></a>移除世界錨點

如果您不再想 GameObject 鎖定至真實世界的位置，而且不想要將它移至此框架，則您可以只需要呼叫終結世界錨定在元件上。

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

如果您想要移動 GameObject 此框架中，您需要改為呼叫 DestroyImmediate。

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>移動世界錨定 GameObject

世界錨定在其上時，不能移動 GameObject 的。 如果您要移動 GameObject 此框架時，您需要：
1. DestroyImmediate 世界錨點元件
2. 移動 GameObject
3. 將 World 錨點的新元件新增至 GameObject。

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>處理 Locatability 變更

WorldAnchor 可能無法之外的可尋獲在真實世界的某一點的時間。 如果發生此情況，Unity 將不會更新錨定的物件的轉換。 這也可以變更應用程式執行時。 Locatability 中處理此變更會導致不會出現在正確的實體位置的世界中的物件。

若要收到 locatability 變更：
1. 訂閱 OnTrackingChanged 事件
2. 處理事件

**OnTrackingChanged**基礎的空間錨點變更之間的狀態為正在之外的可尋獲與未之外的可尋獲時，就會呼叫事件。

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

然後處理事件：

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

有時候錨點位於立即。 在此情況下，此 isLocated 屬性的錨點會設定為 true 時 AddComponent<WorldAnchor>（） 傳回。 如此一來，就不會觸發 OnTrackingChanged 事件。 全新的模式是呼叫您初始的 IsLocated 狀態的 OnTrackingChanged 處理常式之後附加錨點。

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a>在裝置之間共用的錨點

您可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間的錨點</a>從本機的 WorldAnchor，然後會跨多個 HoloLens、 iOS 和 Android 裝置可以找出您的應用程式建立持久的雲端錨點。  藉由跨多個裝置共用常見的空間錨點，每位使用者都可以看到相對於該錨點相同的實體位置中呈現內容。  這可讓您即時分享經驗。

若要開始建置 Unity 中的共用的體驗，試用 5 分鐘<a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">空間錨點 Unity Azure 快速入門</a>。

一旦您啟動並執行 Azure 空間的起點，您可以接著<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">建立，並找出在 Unity 中的錨點</a>。

## <a name="see-also"></a>另請參閱
* [體驗標尺](coordinate-systems.md#mixed-reality-experience-scales)
* [空間的階段](coordinate-systems.md#stage-frame-of-reference)
* [追蹤 Unity 中的遺失](tracking-loss-in-unity.md)
* [空間的錨點](spatial-anchors.md)
* [在 Unity 中的持續性](persistence-in-unity.md)
* [在 Unity 中的共用的體驗](shared-experiences-in-unity.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間的錨點</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure 的空間錨點適用於 Unity SDK</a>