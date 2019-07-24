---
title: Unity 中的座標系統
description: 瞭解如何在 Unity 中建立站上、中度、會議室和全球規模的混合現實體驗。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 座標系統, 空間座標系統, 僅限方向, 固定規模, 大規模, 室內規模, 世界級, 360 度, 站, 室內, 房間, 世界, 縮放, 位置, 方向, Unity, 錨點, 空間錨點, 世界錨點, 世界鎖定,世界-鎖定, 內文鎖定, 內文鎖定, 追蹤遺失, locatability, 界限, recenter
ms.openlocfilehash: 36d74488b23587e5c89b40faf97921a10be7473b
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525968"
---
# <a name="coordinate-systems-in-unity"></a>Unity 中的座標系統

Windows Mixed Reality 支援各種[經驗調整](coordinate-systems.md)的應用程式, 從僅限方向的應用程式, 以及透過會議室規模應用程式來擴充的上移。 在 HoloLens 上, 您可以進一步建立全球規模的應用程式, 讓使用者不超過5計量, 探索大樓的整個樓層。

在 Unity 中建立混合現實體驗的第一個步驟, 是要判斷您的應用程式將會以何種方式[調整](coordinate-systems.md)您的 app 目標。

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>建立僅限方向或固定規模的體驗

**命名空間：** *UnityEngine.XR*<br>
**類型：**  *XRDevice*

若要建立**僅限方向**或**固定大小的體驗**, 您必須將 Unity 設定為固定的追蹤空間類型。 這會設定 Unity 的全局座標系統, 以追蹤[固定的參考框架](coordinate-systems.md#spatial-coordinate-systems)。 在「固定」追蹤模式中, 放在編輯器中的內容, 就像是在相機的預設位置前方 ([轉寄] 為-Z), 會在應用程式啟動時顯示在使用者的前方。

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**命名空間：** *UnityEngine.XR*<br>
**類型：** *InputTracking*

如需純**方向的體驗**, 例如360度的影片檢視器 (位置標頭更新會破壞此假像), 您可以接著設定[XR。InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html)為 true:

```cs
InputTracking.disablePositionalTracking = true;
```

針對**固定規模的體驗**, 若要讓使用者稍後 recenter 已放置的來源, 您可以呼叫[XR。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)方法:

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a>建立大規模或會議室的體驗

**命名空間：** *UnityEngine.XR*<br>
**類型：**  *XRDevice*

針對**大規模**或**會議室的體驗**, 您將需要放置相對於樓層的內容。 您會理解使用者的 floor 使用 **[空間階段](coordinate-systems.md#spatial-coordinate-systems)** 、 樓層來源和選擇性空間界限代表使用者的定義、 設定期間第一次執行。

為確保 Unity 與其在樓層層級的全局座標系統運作, 您可以將 Unity 設定為 RoomScale 追蹤空間類型, 並確定設定成功:

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
* 如果 SetTrackingSpaceType 傳回 true, Unity 已成功切換其全局座標系統, 以追蹤[參考的階段框架](coordinate-systems.md#spatial-coordinate-systems)。
* 如果 SetTrackingSpaceType 傳回 false, 則 Unity 無法切換至參考的階段框架, 可能是因為使用者尚未在其環境中設定。 這並不常見, 但如果階段是在不同的房間內設定, 而裝置已移至目前的房間, 而沒有使用者設定新的階段, 則可能會發生這種情況。

一旦您的應用程式成功設定 RoomScale 追蹤空間類型, 放置在 y = 0 平面上的內容就會出現在樓層上。 位於 (0, 0, 0) 的原點會是在室內設定期間使用者勇敢面對考驗的特定位置, 其中-Z 代表在安裝期間所面臨的正向方向。

**命名空間：** *UnityEngine。 XR*<br>
**類型：** *範圍*

在腳本程式碼中, 您可以在上呼叫 TryGetGeometry 方法, 以取得界限多邊形, 並指定 TrackedArea 的界限類型。 如果使用者定義界限 (您會取得頂點清單), 您就知道可以安全地提供**會議室規模的體驗**給使用者, 讓他們能在其中四處流覽您建立的場景。

請注意, 當使用者對邊界進行方法時, 系統將會自動呈現界限。 您的應用程式不需要使用此多邊形來呈現界限本身。 不過, 您可以選擇使用此界限多邊形來配置場景物件, 以確保使用者可以在不 teleporting 的情況下, 實際觸及那些物件:

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a>建立全球規模的體驗

**命名空間：**  *UnityEngine.XR.WSA*<br>
**類型：** *WorldAnchor*

如需 HoloLens 的真實**全球化體驗**, 讓使用者穿梭超過5計量, 您將需要新的技術, 超越用於會議室規模的經驗。 您將使用的一項重要技巧, 就是建立[空間錨點](coordinate-systems.md#spatial-anchors), 以在實體世界中精確地鎖定全像位置的全息影像叢集, 而不論使用者已漫遊的距離為何, 然後[在後續的會話中再次尋找那些全息影像](coordinate-systems.md#spatial-anchor-persistence)。

在 Unity 中, 您可以藉由將**WorldAnchor** Unity 元件新增至 GameObject 來建立空間錨點。

### <a name="adding-a-world-anchor"></a>新增世界錨點

若要新增世界錨點, 請<WorldAnchor>使用您想要錨定在真實世界中的轉換, 在遊戲物件上呼叫 AddComponent ()。

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

就這麼容易！ 這個遊戲物件現在會錨定在實體世界中的目前位置, 您可能會看到其 Unity world 座標會稍微調整一段時間, 以確保實體對齊。 使用[持續](persistence-in-unity.md)性, 以在未來的應用程式會話中再次尋找此錨定位置。

### <a name="removing-a-world-anchor"></a>移除世界錨點

如果您不想再讓 GameObject 鎖定到實體世界位置, 而不打算將它移到此框架, 則您可以直接在「世界錨點」元件上呼叫摧毀。

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

如果您想要移動 GameObject 此框架, 您必須改為呼叫 DestroyImmediate。

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>移動世界錨定的 GameObject

當世界錨點在 GameObject 時, 無法移動。 如果您需要將 GameObject 移到此框架, 您必須:
1. DestroyImmediate 世界錨點元件
2. 移動 GameObject
3. 將新的「世界錨點」元件新增至 GameObject。

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>處理 Locatability 變更

實體世界中的某個時間點可能不會有 WorldAnchor。 如果發生這種情況, Unity 將不會更新已錨定物件的轉換。 當應用程式正在執行時, 這也會變更。 無法處理 locatability 中的變更, 會導致物件不會出現在世界中正確的實體位置。

若要收到有關 locatability 變更的通知:
1. 訂閱 OnTrackingChanged 事件
2. 處理事件

每當基礎空間錨點在要找出的狀態與未被定位之間變更時, 就會呼叫**OnTrackingChanged**事件。

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

然後處理事件:

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

有時錨點會立即找到。 在此情況下, 當 AddComponent<WorldAnchor>() 傳回時, 錨點的這個 isLocated 屬性會設定為 true。 因此, 將不會觸發 OnTrackingChanged 事件。 全新的模式是在附加錨點之後, 以初始 IsLocated 狀態呼叫 OnTrackingChanged 處理常式。

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a>跨裝置共用錨點

您可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a>, 從本機 WorldAnchor 建立長期雲端錨點, 然後您的應用程式可以在多個 HoloLens、IOS 和 Android 裝置上尋找。  藉由共用多個裝置上的通用空間錨點, 每個使用者都可以看到相對於相同實體位置中的錨點所呈現的內容。  這可提供即時共用體驗。

若要開始在 Unity 中建立共用體驗, 請嘗試5分鐘的<a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 空間錨點 Unity 快速入門</a>。

當您使用 Azure 空間錨點啟動並執行之後, 就可以<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中建立和尋找錨點</a>。

## <a name="see-also"></a>另請參閱
* [經驗調整](coordinate-systems.md#mixed-reality-experience-scales)
* [空間階段](coordinate-systems.md#stage-frame-of-reference)
* [Unity 中的追蹤遺失](tracking-loss-in-unity.md)
* [空間錨點](spatial-anchors.md)
* [Unity 中的持續性](persistence-in-unity.md)
* [Unity 中的共用體驗](shared-experiences-in-unity.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">適用于 Unity 的 Azure 空間錨點 SDK</a>