---
title: 在 Unity 中的本機的錨點傳輸
description: 在 Unity 應用程式中的多個 HoloLens 裝置之間傳輸的錨點。
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: 共用、 錨點、 WorldAnchor、 MR 共用 250、 WorldAnchorTransferBatch、 SpatialPerception、 傳輸、 本機的錨點傳輸，錨點匯出、 錨點匯入
ms.openlocfilehash: 82bcd07417fd5aa1b265ebc3c8edc939101dd783
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2019
ms.locfileid: "59597107"
---
# <a name="local-anchor-transfers-in-unity"></a>在 Unity 中的本機的錨點傳輸

在無法使用的情況下<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間的錨點</a>，本機的錨點傳輸啟用一個 HoloLens 裝置匯出要匯入第二個的 HoloLens 裝置所錨點。

>[!NOTE]
>本機的錨點傳輸提供較不強大的錨點重新叫用比<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間的錨點</a>，以及 iOS 和 Android 裝置不支援這種方法。

### <a name="setting-the-spatialperception-capability"></a>設定 SpatialPerception 功能

為了讓應用程式將傳送空間的錨點*SpatialPerception*必須啟用功能。

如何啟用*SpatialPerception*功能：
1. 在 Unity 編輯器中，開啟 **[播放程式設定]** 窗格 (編輯 > 專案設定 > 播放器)
2. 按一下 [ **「 Windows 市集 」** ] 索引標籤
3. 依序展開 **「 發佈設定 」** ，並檢查 **"SpatialPerception 」** 中的功能 **「 功能 」** 清單

>[!NOTE]
>如果您已匯出您的 Unity 專案加入 Visual Studio 方案，您必須匯出新的資料夾或以手動方式[設定這項功能在 Visual Studio 中，AppxManifest](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)。

### <a name="anchor-transfer"></a>錨點傳輸

**命名空間：***UnityEngine.XR.WSA.Sharing*<br>
**類型**：*WorldAnchorTransferBatch*

要傳送[WorldAnchor](coordinate-systems-in-unity.md)，其中必須建立要傳送的錨點。 一個 HoloLens 的使用者會掃描其環境，並以手動方式或以程式設計方式的點則會在 要共用經驗的錨點的空間中選擇。 可以序列化，代表此點的資料，然後傳送至共用體驗中的裝置。 然後每個裝置的錨點的資料還原序列化，並嘗試在空間中尋找該時間點。 為了讓錨點傳送工作，每個裝置必須已掃描足夠的環境中，可以識別代表錨點的指標。

### <a name="setup"></a>安裝程式

在此頁面上的範例程式碼有幾個需要初始化的欄位：
1. *GameObject rootGameObject*已*GameObject*在 Unity 中有*WorldAnchor*元件在其上。 共用經驗的一位使用者會將這*GameObject*並將資料匯出至其他使用者。
2. *WorldAnchor gameRootAnchor*已*UnityEngine.XR.WSA.WorldAnchor*上*rootGameObject*。
3. *byte [] importedData*是序列化的錨點，每個用戶端透過網路接收的位元組陣列。

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

### <a name="exporting"></a>匯出

若要匯出，我們只需要*WorldAnchor*和知道我們將就稱它使得它適合接收端應用程式。 共用經驗的一部用戶端會執行下列步驟來匯出共用的錨點：
1. 建立*WorldAnchorTransferBatch*
2. 新增*WorldAnchors*傳輸
3. 開始匯出
4. 處理*OnExportDataAvailable*做為資料的事件就會變成可用
5. 處理*OnExportComplete*事件

我們會建立*WorldAnchorTransferBatch*封裝功能，我們將會傳送，然後將其匯出至位元組：

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

有可用的資料時，傳送至用戶端或緩衝區的位元組，為提供資料的區段，並透過任何想要的方式傳送：

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

匯出完成後，如果我們有已傳輸資料，而序列化失敗，告訴用戶端捨棄的資料。 如果序列化成功，請在已傳送所有資料，並匯入可開始告訴用戶端：

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

### <a name="importing"></a>匯入

我們可以之後從寄件者收到的所有位元組時，匯入回資料*WorldAnchorTransferBatch*並鎖定我們根遊戲物件到相同的實體位置。 注意： 匯入 transiently 有時會失敗，而且需要重試：

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

在後*GameObject*鎖定透過*LockObject*呼叫時，它會有*WorldAnchor*其中會保存在相同的實體位置，在世界中，但它可能是在在 Unity 中的不同位置座標空間比其他使用者。

