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
# <a name="persistence-in-unity"></a><span data-ttu-id="e1a66-104">在 Unity 中的持續性</span><span class="sxs-lookup"><span data-stu-id="e1a66-104">Persistence in Unity</span></span>

<span data-ttu-id="e1a66-105">**命名空間：** *UnityEngine.XR.WSA.Persistence*</span><span class="sxs-lookup"><span data-stu-id="e1a66-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="e1a66-106">**類別：** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="e1a66-106">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="e1a66-107">WorldAnchorStore 是建立全像攝影版的體驗的關鍵，全像投影在特定的實際位置在保持應用程式的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e1a66-107">The WorldAnchorStore is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="e1a66-108">這樣，您的使用者或釘選個別全像投影的工作區中想要的話，並找出於稍後在他們想透過您的應用程式的許多用途。</span><span class="sxs-lookup"><span data-stu-id="e1a66-108">This lets your users pin individual holograms or a workspace wherever they want it, and then find it later where they expect over many uses of your app.</span></span>

## <a name="how-to-persist-holograms-across-sessions"></a><span data-ttu-id="e1a66-109">如何在工作階段之間保存全像投影</span><span class="sxs-lookup"><span data-stu-id="e1a66-109">How to persist holograms across sessions</span></span>

<span data-ttu-id="e1a66-110">WorldAnchorStore 可讓您保存跨工作階段的 WorldAnchor 的位置。</span><span class="sxs-lookup"><span data-stu-id="e1a66-110">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="e1a66-111">若要實際在工作階段之間保存全像投影，您必須來個別追蹤您使用特定的世界錨點的 Gameobject。</span><span class="sxs-lookup"><span data-stu-id="e1a66-111">To actually persist holograms across sessions, you will need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="e1a66-112">通常是合理建立 GameObject 根與世界錨點，且有子系至全像投影錨定它使用本機位置的位移。</span><span class="sxs-lookup"><span data-stu-id="e1a66-112">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="e1a66-113">若要從先前的工作階段中載入全像投影：</span><span class="sxs-lookup"><span data-stu-id="e1a66-113">To load holograms from previous sessions:</span></span>
1. <span data-ttu-id="e1a66-114">取得 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="e1a66-114">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="e1a66-115">載入與世界錨點可 world 錨點識別碼相關的應用程式資料</span><span class="sxs-lookup"><span data-stu-id="e1a66-115">Load app data relating to the world anchor which gives you the id of the world anchor</span></span>
3. <span data-ttu-id="e1a66-116">從其識別碼載入世界錨點</span><span class="sxs-lookup"><span data-stu-id="e1a66-116">Load a world anchor from its id</span></span>

<span data-ttu-id="e1a66-117">若要供未來工作階段儲存全像投影：</span><span class="sxs-lookup"><span data-stu-id="e1a66-117">To save holograms for future sessions:</span></span>
1. <span data-ttu-id="e1a66-118">取得 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="e1a66-118">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="e1a66-119">儲存指定 id 的世界錨點</span><span class="sxs-lookup"><span data-stu-id="e1a66-119">Save a world anchor specifying an id</span></span>
3. <span data-ttu-id="e1a66-120">儲存與世界錨點識別碼以及相關的應用程式資料</span><span class="sxs-lookup"><span data-stu-id="e1a66-120">Save app data relating to the world anchor along with an id</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="e1a66-121">取得 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="e1a66-121">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="e1a66-122">我們想要保留周圍 WorldAnchorStore 的參考，讓我們知道我們已準備好移當我們想要執行的作業。</span><span class="sxs-lookup"><span data-stu-id="e1a66-122">We will want to keep a reference to the WorldAnchorStore around so we know we are ready to go when we want to perform an operation.</span></span> <span data-ttu-id="e1a66-123">由於這是非同步呼叫時，可能會立即開始，我們想要呼叫</span><span class="sxs-lookup"><span data-stu-id="e1a66-123">Since this is an async call, potentially as soon as start up, we want to call</span></span>

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="e1a66-124">StoreLoaded 在此情況下是我們的處理常式，如 WorldAnchorStore 完成載入時：</span><span class="sxs-lookup"><span data-stu-id="e1a66-124">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

<span data-ttu-id="e1a66-125">我們現在有 WorldAnchorStore，我們將用來儲存及載入特定的世界起點的參考。</span><span class="sxs-lookup"><span data-stu-id="e1a66-125">We now have a reference to the WorldAnchorStore which we will use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="e1a66-126">正在儲存 WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="e1a66-126">Saving a WorldAnchor</span></span>

<span data-ttu-id="e1a66-127">若要儲存，我們只需要什麼我們儲存，且傳入我們想要儲存時，我們取得之前 WorldAnchor 命名。</span><span class="sxs-lookup"><span data-stu-id="e1a66-127">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="e1a66-128">注意： 嘗試將兩個錨點儲存到相同的字串將會失敗 （存放區。儲存會傳回 false）。</span><span class="sxs-lookup"><span data-stu-id="e1a66-128">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="e1a66-129">您需要刪除之前先儲存新的上一個儲存：</span><span class="sxs-lookup"><span data-stu-id="e1a66-129">You need to Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="e1a66-130">正在載入 WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="e1a66-130">Loading a WorldAnchor</span></span>

<span data-ttu-id="e1a66-131">並載入：</span><span class="sxs-lookup"><span data-stu-id="e1a66-131">And to load:</span></span>

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

<span data-ttu-id="e1a66-132">我們另外可以使用存放區。若要移除我們先前儲存的錨點的 delete （） 和存放區。若要移除先前儲存的所有資料的 clear （)。</span><span class="sxs-lookup"><span data-stu-id="e1a66-132">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="e1a66-133">列舉現有的錨點</span><span class="sxs-lookup"><span data-stu-id="e1a66-133">Enumerating Existing Anchors</span></span>

<span data-ttu-id="e1a66-134">若要探索先前儲存的錨點，呼叫 GetAllIds。</span><span class="sxs-lookup"><span data-stu-id="e1a66-134">To discover previously stored anchors, call GetAllIds.</span></span>

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="e1a66-135">針對多個裝置保存全像投影</span><span class="sxs-lookup"><span data-stu-id="e1a66-135">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="e1a66-136">您可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間的錨點</a>從本機的 WorldAnchor，您的應用程式可以再找出跨多個 HoloLens、 iOS 和 Android 裝置，即使這些裝置不存在一起同時建立持久的雲端錨點時間。</span><span class="sxs-lookup"><span data-stu-id="e1a66-136">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices are not present together at the same time.</span></span>  <span data-ttu-id="e1a66-137">雲端錨點是持續性，因為經過一段時間的多個裝置每個所見呈現相對於該相同的實體位置中的錨點的內容。</span><span class="sxs-lookup"><span data-stu-id="e1a66-137">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="e1a66-138">若要開始建置 Unity 中的共用的體驗，試用 5 分鐘<a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">空間錨點 Unity Azure 快速入門</a>。</span><span class="sxs-lookup"><span data-stu-id="e1a66-138">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="e1a66-139">一旦您啟動並執行 Azure 空間的起點，您可以接著<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">建立，並找出在 Unity 中的錨點</a>。</span><span class="sxs-lookup"><span data-stu-id="e1a66-139">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1a66-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1a66-140">See Also</span></span>
* [<span data-ttu-id="e1a66-141">空間的錨點的持續性</span><span class="sxs-lookup"><span data-stu-id="e1a66-141">Spatial anchor persistence</span></span>](coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="e1a66-142"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間的錨點</a></span><span class="sxs-lookup"><span data-stu-id="e1a66-142"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="e1a66-143"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure 的空間錨點適用於 Unity SDK</a></span><span class="sxs-lookup"><span data-stu-id="e1a66-143"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
