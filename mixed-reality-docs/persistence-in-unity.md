---
title: Unity 中的持續性
description: 持續性可讓您的使用者在他們想要的地方釘選個別的全息影像或工作區, 然後在您的應用程式有許多使用方式之後, 再尋找它。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens、持續性、Unity
ms.openlocfilehash: b6a67e52b3a5ce724a90eb1a479c5eda74b0c4cb
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524782"
---
# <a name="persistence-in-unity"></a>Unity 中的持續性

**命名空間：** *UnityEngine. XR. WSA. 持續性*<br>
**類別：** *WorldAnchorStore*

WorldAnchorStore 是建立全像全球化體驗的關鍵, 其中的全息影像會在應用程式的實例之間保持在特定的實際位置。 這可讓您的使用者在他們想要的地方釘選個別的全息影像或工作區, 然後在您的應用程式有許多用途的情況下找到它。

## <a name="how-to-persist-holograms-across-sessions"></a>如何跨會話保存全息影像

WorldAnchorStore 可讓您跨會話保存 WorldAnchor 的位置。 若要實際跨會話保存全像投影, 您必須分別追蹤使用特定世界錨點的 Gameobject。 建立具有世界錨點的 GameObject 根, 並讓子系以局部位置位移進行錨定, 通常是很合理的做法。

若要從先前的會話載入全息影像:
1. 取得 WorldAnchorStore
2. 載入與世界錨點相關的應用程式資料, 以提供您世界錨點的識別碼
3. 從識別碼載入世界錨點

若要為未來的會話儲存全息影像:
1. 取得 WorldAnchorStore
2. 儲存指定識別碼的世界錨點
3. 儲存與世界錨點相關的應用程式資料以及識別碼

### <a name="getting-the-worldanchorstore"></a>取得 WorldAnchorStore

我們想要保留對 WorldAnchorStore 的參考, 讓我們知道當我們想要執行作業時, 我們已準備好繼續進行。 因為這是非同步呼叫, 可能會在啟動後立即呼叫

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

在此情況下, StoreLoaded 是 WorldAnchorStore 完成載入時的處理常式:

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

我們現在有 WorldAnchorStore 的參考, 我們將用它來儲存和載入特定的世界錨點。

### <a name="saving-a-worldanchor"></a>儲存 WorldAnchor

若要儲存, 我們只需要命名我們要儲存的內容, 並將它傳遞至我們想要儲存的 WorldAnchor。 注意: 嘗試將兩個錨點儲存至相同的字串將會失敗 (儲存。儲存會傳回 false)。 您必須先刪除先前的儲存, 然後再儲存新的:

```
private void SaveGame()
{
       // Save data about holograms positioned by this world anchor
       if (!this.savedRoot) // Only Save the root once
       {
              this.savedRoot = this.store.Save("rootGameObject", anchor);
              Assert(this.savedRoot);
       }
}
```

### <a name="loading-a-worldanchor"></a>載入 WorldAnchor

和以載入:

```
private void LoadGame()
{
       // Save data about holograms positioned by this world anchor
       this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
       if (!this.savedRoot)
       {
              // We didn't actually have the game root saved! We have to re-place our objects or start over
       }
}
```

我們還可以使用 store。刪除 () 以移除先前儲存並儲存的錨點。清除 () 以移除所有先前儲存的資料。

### <a name="enumerating-existing-anchors"></a>列舉現有的錨點

若要探索先前儲存的錨點, 請呼叫 GetAllIds。

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>保存多個裝置的全息影像

您可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a>, 從本機 WorldAnchor 建立長期雲端錨點, 讓您的應用程式可以在多個 HoloLens、IOS 和 Android 裝置上尋找, 即使這些裝置不會同時出現在同一時間。  由於雲端錨點是持續性的, 因此一段時間的多個裝置可以看到相對於相同實體位置中的錨點呈現的內容。

若要開始在 Unity 中建立共用體驗, 請嘗試5分鐘的<a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 空間錨點 Unity 快速入門</a>。

當您使用 Azure 空間錨點啟動並執行之後, 就可以<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中建立和尋找錨點</a>。

## <a name="see-also"></a>另請參閱
* [空間錨點持續性](coordinate-systems.md#spatial-anchor-persistence)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">適用于 Unity 的 Azure 空間錨點 SDK</a>
