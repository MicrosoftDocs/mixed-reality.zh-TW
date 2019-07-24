---
title: Unity 中的本機錨點傳輸
description: 在 Unity 應用程式中的多個 HoloLens 裝置之間傳輸錨點。
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: 共用, 錨點, WorldAnchor, MR 分享 250, WorldAnchorTransferBatch, SpatialPerception, 傳輸, 本機錨點傳輸, 錨點匯出, 錨點匯入
ms.openlocfilehash: 82bcd07417fd5aa1b265ebc3c8edc939101dd783
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516132"
---
# <a name="local-anchor-transfers-in-unity"></a>Unity 中的本機錨點傳輸

在無法使用<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間錨點</a>的情況下, 本機錨點傳輸可讓一個 hololens 裝置匯出錨點, 以供第二個 hololens 裝置匯入。

>[!NOTE]
>本機錨點傳輸提供較不健全的錨點回收, 而不是使用<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間錨點</a>, 而且此方法不支援 IOS 和 Android 裝置。

### <a name="setting-the-spatialperception-capability"></a>設定 SpatialPerception 功能

為了讓應用程式能夠傳輸空間錨點, 必須啟用*SpatialPerception*功能。

如何啟用*SpatialPerception*功能:
1. 在 Unity 編輯器中, 開啟 [ **Player 設定**] 窗格 (編輯 > 專案設定 > Player)
2. 按一下 [ **Windows Store** ] 索引標籤
3. 展開 [**發行設定]** , 然後檢查 [**功能]** 清單中的 [ **SpatialPerception]** 功能

>[!NOTE]
>如果您已經將 Unity 專案匯出至 Visual Studio 方案, 您必須匯出至新資料夾, 或在[Visual Studio 的 package.appxmanifest.xml 中手動設定這項功能](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)。

### <a name="anchor-transfer"></a>錨點轉移

**命名空間：**  *UnityEngine.XR.WSA.Sharing*<br>
**類型**：*WorldAnchorTransferBatch*

若要傳送[WorldAnchor](coordinate-systems-in-unity.md), 必須建立要傳送的錨點。 一個 HoloLens 的使用者會掃描其環境, 並手動或以程式設計方式選擇空間, 以作為共用體驗的錨點。 表示此點的資料接著可以序列化並傳送至體驗中共用的其他裝置。 然後, 每個裝置都會將錨定資料還原序列化, 並嘗試找出該點的空間。 為了讓錨點傳輸正常執行, 每個裝置都必須在足夠的環境中掃描, 如此才能識別錨點所代表的點。

### <a name="setup"></a>安裝程式

此頁面上的範例程式碼有幾個需要初始化的欄位:
1. *GameObject rootGameObject*是 Unity 中的*GameObject* , 其中具有*WorldAnchor*元件。 共用體驗中的一位使用者會將此*GameObject* , 並將資料匯出給其他使用者。
2. *WorldAnchor gameRootAnchor*是*WorldAnchor*上的*UnityEngine. XR. rootGameObject* 。
3. *byte [] importedData*是一種位元組陣列, 適用于每個用戶端透過網路接收的序列化錨點。

```
public GameObject rootGameObject;
private UnityEngine.XR.WSA.WorldAnchor gameRootAnchor;

void Start ()
{
    gameRootAnchor = rootGameObject.GetComponent<UnityEngine.XR.WSA.WorldAnchor>();

    if (gameRootAnchor == null)
    {
        gameRootAnchor = rootGameObject.AddComponent<UnityEngine.XR.WSA.WorldAnchor>();
    }
}
```

### <a name="exporting"></a>導

若要匯出, 我們只需要一個*WorldAnchor* , 並知道我們將會呼叫它, 讓它對接收應用程式很有意義。 共用體驗中的一個用戶端會執行下列步驟, 以匯出共用的錨點:
1. 建立*WorldAnchorTransferBatch*
2. 新增要傳送的*WorldAnchors*
3. 開始匯出
4. 當資料變成可用時, 處理*OnExportDataAvailable*事件
5. 處理*OnExportComplete*事件

我們會建立*WorldAnchorTransferBatch*來封裝我們將要傳輸的內容, 然後將它匯出成位元組:

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

當資料可供使用時, 將位元組傳送至用戶端或緩衝區, 因為資料區段可供使用, 並透過任何所需的方式傳送:

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

匯出完成後, 如果我們已傳輸資料, 而且序列化失敗, 請告知用戶端捨棄資料。 如果序列化成功, 請告知用戶端已傳送所有資料, 且匯入可以啟動:

```
private void OnExportComplete(SerializationCompletionReason completionReason)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        SendExportFailedToClient();
    }
    else
    {
        SendExportSucceededToClient();
    }
}
```

### <a name="importing"></a>導

接收寄件者的所有位元組之後, 我們可以將資料匯回*WorldAnchorTransferBatch* , 並將我們的根遊戲物件鎖定到相同的實體位置。 注意: 匯入有時會暫時失敗, 而且需要重試:

```
// This byte array should have been updated over the network from TransferDataToClient
private byte[] importedData;
private int retryCount = 3;

private void ImportRootGameObject()
{
    WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
}

private void OnImportComplete(SerializationCompletionReason completionReason, WorldAnchorTransferBatch deserializedTransferBatch)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        Debug.Log("Failed to import: " + completionReason.ToString());
        if (retryCount > 0)
        {
            retryCount--;
            WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
        }
        return;
    }

    this.gameRootAnchor = deserializedTransferBatch.LockObject("gameRoot", this.rootGameObject);
}
```

透過*LockObject*呼叫鎖定*GameObject*之後, 它會有一個*WorldAnchor* , 它會將它保留在世界中相同的實體位置, 但它可能位於 Unity 座標空間中的其他位置, 而不是其他使用者。

