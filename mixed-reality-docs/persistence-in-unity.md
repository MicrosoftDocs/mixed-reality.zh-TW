---
title: 在 Unity 中的持續性
description: 持續性可讓您釘選個別全像投影或工作區，然後再尋找他們所預期的位置上有許多使用您的應用程式，他們要的位置的使用者。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens，持續性，Unity
ms.openlocfilehash: b6a67e52b3a5ce724a90eb1a479c5eda74b0c4cb
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2019
ms.locfileid: "59597115"
---
# <a name="persistence-in-unity"></a>在 Unity 中的持續性

**命名空間：** *UnityEngine.XR.WSA.Persistence*<br>
**類別：** *WorldAnchorStore*

WorldAnchorStore 是建立全像攝影版的體驗的關鍵，全像投影在特定的實際位置在保持應用程式的執行個體。 這樣，您的使用者或釘選個別全像投影的工作區中想要的話，並找出於稍後在他們想透過您的應用程式的許多用途。

## <a name="how-to-persist-holograms-across-sessions"></a>如何在工作階段之間保存全像投影

WorldAnchorStore 可讓您保存跨工作階段的 WorldAnchor 的位置。 若要實際在工作階段之間保存全像投影，您必須來個別追蹤您使用特定的世界錨點的 Gameobject。 通常是合理建立 GameObject 根與世界錨點，且有子系至全像投影錨定它使用本機位置的位移。

若要從先前的工作階段中載入全像投影：
1. 取得 WorldAnchorStore
2. 載入與世界錨點可 world 錨點識別碼相關的應用程式資料
3. 從其識別碼載入世界錨點

若要供未來工作階段儲存全像投影：
1. 取得 WorldAnchorStore
2. 儲存指定 id 的世界錨點
3. 儲存與世界錨點識別碼以及相關的應用程式資料

### <a name="getting-the-worldanchorstore"></a>取得 WorldAnchorStore

我們想要保留周圍 WorldAnchorStore 的參考，讓我們知道我們已準備好移當我們想要執行的作業。 由於這是非同步呼叫時，可能會立即開始，我們想要呼叫

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

StoreLoaded 在此情況下是我們的處理常式，如 WorldAnchorStore 完成載入時：

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

我們現在有 WorldAnchorStore，我們將用來儲存及載入特定的世界起點的參考。

### <a name="saving-a-worldanchor"></a>正在儲存 WorldAnchor

若要儲存，我們只需要什麼我們儲存，且傳入我們想要儲存時，我們取得之前 WorldAnchor 命名。 注意： 嘗試將兩個錨點儲存到相同的字串將會失敗 （存放區。儲存會傳回 false）。 您需要刪除之前先儲存新的上一個儲存：

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

### <a name="loading-a-worldanchor"></a>正在載入 WorldAnchor

並載入：

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

我們另外可以使用存放區。若要移除我們先前儲存的錨點的 delete （） 和存放區。若要移除先前儲存的所有資料的 clear （)。

### <a name="enumerating-existing-anchors"></a>列舉現有的錨點

若要探索先前儲存的錨點，呼叫 GetAllIds。

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>針對多個裝置保存全像投影

您可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間的錨點</a>從本機的 WorldAnchor，您的應用程式可以再找出跨多個 HoloLens、 iOS 和 Android 裝置，即使這些裝置不存在一起同時建立持久的雲端錨點時間。  雲端錨點是持續性，因為經過一段時間的多個裝置每個所見呈現相對於該相同的實體位置中的錨點的內容。

若要開始建置 Unity 中的共用的體驗，試用 5 分鐘<a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">空間錨點 Unity Azure 快速入門</a>。

一旦您啟動並執行 Azure 空間的起點，您可以接著<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">建立，並找出在 Unity 中的錨點</a>。

## <a name="see-also"></a>另請參閱
* [空間的錨點的持續性](coordinate-systems.md#spatial-anchor-persistence)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間的錨點</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure 的空間錨點適用於 Unity SDK</a>
