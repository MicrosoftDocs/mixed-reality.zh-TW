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
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2019
ms.locfileid: "59597107"
---
# <a name="local-anchor-transfers-in-unity"></a><span data-ttu-id="11301-104">在 Unity 中的本機的錨點傳輸</span><span class="sxs-lookup"><span data-stu-id="11301-104">Local anchor transfers in Unity</span></span>

<span data-ttu-id="11301-105">在無法使用的情況下<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間的錨點</a>，本機的錨點傳輸啟用一個 HoloLens 裝置匯出要匯入第二個的 HoloLens 裝置所錨點。</span><span class="sxs-lookup"><span data-stu-id="11301-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="11301-106">本機的錨點傳輸提供較不強大的錨點重新叫用比<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間的錨點</a>，以及 iOS 和 Android 裝置不支援這種方法。</span><span class="sxs-lookup"><span data-stu-id="11301-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

### <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="11301-107">設定 SpatialPerception 功能</span><span class="sxs-lookup"><span data-stu-id="11301-107">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="11301-108">為了讓應用程式將傳送空間的錨點*SpatialPerception*必須啟用功能。</span><span class="sxs-lookup"><span data-stu-id="11301-108">In order for an app to transfer spatial anchors, the *SpatialPerception* capability must be enabled.</span></span>

<span data-ttu-id="11301-109">如何啟用*SpatialPerception*功能：</span><span class="sxs-lookup"><span data-stu-id="11301-109">How to enable the *SpatialPerception* capability:</span></span>
1. <span data-ttu-id="11301-110">在 Unity 編輯器中，開啟 **[播放程式設定]** 窗格 (編輯 > 專案設定 > 播放器)</span><span class="sxs-lookup"><span data-stu-id="11301-110">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="11301-111">按一下 [ **「 Windows 市集 」** ] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="11301-111">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="11301-112">依序展開 **「 發佈設定 」** ，並檢查 **"SpatialPerception 」** 中的功能 **「 功能 」** 清單</span><span class="sxs-lookup"><span data-stu-id="11301-112">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

>[!NOTE]
><span data-ttu-id="11301-113">如果您已匯出您的 Unity 專案加入 Visual Studio 方案，您必須匯出新的資料夾或以手動方式[設定這項功能在 Visual Studio 中，AppxManifest](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)。</span><span class="sxs-lookup"><span data-stu-id="11301-113">If you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

### <a name="anchor-transfer"></a><span data-ttu-id="11301-114">錨點傳輸</span><span class="sxs-lookup"><span data-stu-id="11301-114">Anchor Transfer</span></span>

<span data-ttu-id="11301-115">**命名空間：**  *UnityEngine.XR.WSA.Sharing*</span><span class="sxs-lookup"><span data-stu-id="11301-115">**Namespace:** *UnityEngine.XR.WSA.Sharing*</span></span><br>
<span data-ttu-id="11301-116">**類型**：*WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="11301-116">**Type**: *WorldAnchorTransferBatch*</span></span>

<span data-ttu-id="11301-117">要傳送[WorldAnchor](coordinate-systems-in-unity.md)，其中必須建立要傳送的錨點。</span><span class="sxs-lookup"><span data-stu-id="11301-117">To transfer a [WorldAnchor](coordinate-systems-in-unity.md), one must establish the anchor to be transferred.</span></span> <span data-ttu-id="11301-118">一個 HoloLens 的使用者會掃描其環境，並以手動方式或以程式設計方式的點則會在 要共用經驗的錨點的空間中選擇。</span><span class="sxs-lookup"><span data-stu-id="11301-118">The user of one HoloLens scans their environment and either manually or programmatically chooses a point in space to be the Anchor for the shared experience.</span></span> <span data-ttu-id="11301-119">可以序列化，代表此點的資料，然後傳送至共用體驗中的裝置。</span><span class="sxs-lookup"><span data-stu-id="11301-119">The data that represents this point can then be serialized and transmitted to the other devices that are sharing in the experience.</span></span> <span data-ttu-id="11301-120">然後每個裝置的錨點的資料還原序列化，並嘗試在空間中尋找該時間點。</span><span class="sxs-lookup"><span data-stu-id="11301-120">Each device then de-serializes the anchor data and attempts to locate that point in space.</span></span> <span data-ttu-id="11301-121">為了讓錨點傳送工作，每個裝置必須已掃描足夠的環境中，可以識別代表錨點的指標。</span><span class="sxs-lookup"><span data-stu-id="11301-121">In order for Anchor Transfer to work, each device must have scanned in enough of the environment such that the point represented by the anchor can be identified.</span></span>

### <a name="setup"></a><span data-ttu-id="11301-122">安裝程式</span><span class="sxs-lookup"><span data-stu-id="11301-122">Setup</span></span>

<span data-ttu-id="11301-123">在此頁面上的範例程式碼有幾個需要初始化的欄位：</span><span class="sxs-lookup"><span data-stu-id="11301-123">The sample code on this page has a few fields that will need to be initialized:</span></span>
1. <span data-ttu-id="11301-124">*GameObject rootGameObject*已*GameObject*在 Unity 中有*WorldAnchor*元件在其上。</span><span class="sxs-lookup"><span data-stu-id="11301-124">*GameObject rootGameObject* is a *GameObject* in Unity that has a *WorldAnchor* Component on it.</span></span> <span data-ttu-id="11301-125">共用經驗的一位使用者會將這*GameObject*並將資料匯出至其他使用者。</span><span class="sxs-lookup"><span data-stu-id="11301-125">One user in the shared experience will place this *GameObject* and export the data to the other users.</span></span>
2. <span data-ttu-id="11301-126">*WorldAnchor gameRootAnchor*已*UnityEngine.XR.WSA.WorldAnchor*上*rootGameObject*。</span><span class="sxs-lookup"><span data-stu-id="11301-126">*WorldAnchor gameRootAnchor* is the *UnityEngine.XR.WSA.WorldAnchor* that is on *rootGameObject*.</span></span>
3. <span data-ttu-id="11301-127">*byte [] importedData*是序列化的錨點，每個用戶端透過網路接收的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="11301-127">*byte[] importedData* is a byte array for the serialized anchor each client is receiving over the network.</span></span>

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

### <a name="exporting"></a><span data-ttu-id="11301-128">匯出</span><span class="sxs-lookup"><span data-stu-id="11301-128">Exporting</span></span>

<span data-ttu-id="11301-129">若要匯出，我們只需要*WorldAnchor*和知道我們將就稱它使得它適合接收端應用程式。</span><span class="sxs-lookup"><span data-stu-id="11301-129">To export, we just need a *WorldAnchor* and to know what we will call it such that it makes sense for the receiving app.</span></span> <span data-ttu-id="11301-130">共用經驗的一部用戶端會執行下列步驟來匯出共用的錨點：</span><span class="sxs-lookup"><span data-stu-id="11301-130">One client in the shared experience will perform these steps to export the shared anchor:</span></span>
1. <span data-ttu-id="11301-131">建立*WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="11301-131">Create a *WorldAnchorTransferBatch*</span></span>
2. <span data-ttu-id="11301-132">新增*WorldAnchors*傳輸</span><span class="sxs-lookup"><span data-stu-id="11301-132">Add the *WorldAnchors* to transfer</span></span>
3. <span data-ttu-id="11301-133">開始匯出</span><span class="sxs-lookup"><span data-stu-id="11301-133">Begin the export</span></span>
4. <span data-ttu-id="11301-134">處理*OnExportDataAvailable*做為資料的事件就會變成可用</span><span class="sxs-lookup"><span data-stu-id="11301-134">Handle the *OnExportDataAvailable* event as data becomes available</span></span>
5. <span data-ttu-id="11301-135">處理*OnExportComplete*事件</span><span class="sxs-lookup"><span data-stu-id="11301-135">Handle the *OnExportComplete* event</span></span>

<span data-ttu-id="11301-136">我們會建立*WorldAnchorTransferBatch*封裝功能，我們將會傳送，然後將其匯出至位元組：</span><span class="sxs-lookup"><span data-stu-id="11301-136">We create a *WorldAnchorTransferBatch* to encapsulate what we will be transferring and then export that into bytes:</span></span>

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

<span data-ttu-id="11301-137">有可用的資料時，傳送至用戶端或緩衝區的位元組，為提供資料的區段，並透過任何想要的方式傳送：</span><span class="sxs-lookup"><span data-stu-id="11301-137">As data becomes available, send the bytes to the client or buffer as segments of data is available and send through whatever means desired:</span></span>

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

<span data-ttu-id="11301-138">匯出完成後，如果我們有已傳輸資料，而序列化失敗，告訴用戶端捨棄的資料。</span><span class="sxs-lookup"><span data-stu-id="11301-138">Once the export is complete, if we have been transferring data and serialization failed, tell the client to discard the data.</span></span> <span data-ttu-id="11301-139">如果序列化成功，請在已傳送所有資料，並匯入可開始告訴用戶端：</span><span class="sxs-lookup"><span data-stu-id="11301-139">If the serialization succeeded, tell the client that all data has been transferred and importing can start:</span></span>

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

### <a name="importing"></a><span data-ttu-id="11301-140">匯入</span><span class="sxs-lookup"><span data-stu-id="11301-140">Importing</span></span>

<span data-ttu-id="11301-141">我們可以之後從寄件者收到的所有位元組時，匯入回資料*WorldAnchorTransferBatch*並鎖定我們根遊戲物件到相同的實體位置。</span><span class="sxs-lookup"><span data-stu-id="11301-141">After receiving all of the bytes from the sender, we can import the data back into a *WorldAnchorTransferBatch* and lock our root game object into the same physical location.</span></span> <span data-ttu-id="11301-142">注意： 匯入 transiently 有時會失敗，而且需要重試：</span><span class="sxs-lookup"><span data-stu-id="11301-142">Note: import will sometimes transiently fail and needs to be retried:</span></span>

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

<span data-ttu-id="11301-143">在後*GameObject*鎖定透過*LockObject*呼叫時，它會有*WorldAnchor*其中會保存在相同的實體位置，在世界中，但它可能是在在 Unity 中的不同位置座標空間比其他使用者。</span><span class="sxs-lookup"><span data-stu-id="11301-143">After a *GameObject* is locked via the *LockObject* call, it will have a *WorldAnchor* which will keep it in the same physical position in the world, but it may be at a different location in the Unity coordinate space than other users.</span></span>

