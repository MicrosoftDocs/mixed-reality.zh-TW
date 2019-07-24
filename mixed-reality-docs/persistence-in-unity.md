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
# <a name="persistence-in-unity"></a><span data-ttu-id="629cd-104">Unity 中的持續性</span><span class="sxs-lookup"><span data-stu-id="629cd-104">Persistence in Unity</span></span>

<span data-ttu-id="629cd-105">**命名空間：** *UnityEngine. XR. WSA. 持續性*</span><span class="sxs-lookup"><span data-stu-id="629cd-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="629cd-106">**類別：** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="629cd-106">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="629cd-107">WorldAnchorStore 是建立全像全球化體驗的關鍵, 其中的全息影像會在應用程式的實例之間保持在特定的實際位置。</span><span class="sxs-lookup"><span data-stu-id="629cd-107">The WorldAnchorStore is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="629cd-108">這可讓您的使用者在他們想要的地方釘選個別的全息影像或工作區, 然後在您的應用程式有許多用途的情況下找到它。</span><span class="sxs-lookup"><span data-stu-id="629cd-108">This lets your users pin individual holograms or a workspace wherever they want it, and then find it later where they expect over many uses of your app.</span></span>

## <a name="how-to-persist-holograms-across-sessions"></a><span data-ttu-id="629cd-109">如何跨會話保存全息影像</span><span class="sxs-lookup"><span data-stu-id="629cd-109">How to persist holograms across sessions</span></span>

<span data-ttu-id="629cd-110">WorldAnchorStore 可讓您跨會話保存 WorldAnchor 的位置。</span><span class="sxs-lookup"><span data-stu-id="629cd-110">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="629cd-111">若要實際跨會話保存全像投影, 您必須分別追蹤使用特定世界錨點的 Gameobject。</span><span class="sxs-lookup"><span data-stu-id="629cd-111">To actually persist holograms across sessions, you will need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="629cd-112">建立具有世界錨點的 GameObject 根, 並讓子系以局部位置位移進行錨定, 通常是很合理的做法。</span><span class="sxs-lookup"><span data-stu-id="629cd-112">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="629cd-113">若要從先前的會話載入全息影像:</span><span class="sxs-lookup"><span data-stu-id="629cd-113">To load holograms from previous sessions:</span></span>
1. <span data-ttu-id="629cd-114">取得 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="629cd-114">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="629cd-115">載入與世界錨點相關的應用程式資料, 以提供您世界錨點的識別碼</span><span class="sxs-lookup"><span data-stu-id="629cd-115">Load app data relating to the world anchor which gives you the id of the world anchor</span></span>
3. <span data-ttu-id="629cd-116">從識別碼載入世界錨點</span><span class="sxs-lookup"><span data-stu-id="629cd-116">Load a world anchor from its id</span></span>

<span data-ttu-id="629cd-117">若要為未來的會話儲存全息影像:</span><span class="sxs-lookup"><span data-stu-id="629cd-117">To save holograms for future sessions:</span></span>
1. <span data-ttu-id="629cd-118">取得 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="629cd-118">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="629cd-119">儲存指定識別碼的世界錨點</span><span class="sxs-lookup"><span data-stu-id="629cd-119">Save a world anchor specifying an id</span></span>
3. <span data-ttu-id="629cd-120">儲存與世界錨點相關的應用程式資料以及識別碼</span><span class="sxs-lookup"><span data-stu-id="629cd-120">Save app data relating to the world anchor along with an id</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="629cd-121">取得 WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="629cd-121">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="629cd-122">我們想要保留對 WorldAnchorStore 的參考, 讓我們知道當我們想要執行作業時, 我們已準備好繼續進行。</span><span class="sxs-lookup"><span data-stu-id="629cd-122">We will want to keep a reference to the WorldAnchorStore around so we know we are ready to go when we want to perform an operation.</span></span> <span data-ttu-id="629cd-123">因為這是非同步呼叫, 可能會在啟動後立即呼叫</span><span class="sxs-lookup"><span data-stu-id="629cd-123">Since this is an async call, potentially as soon as start up, we want to call</span></span>

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="629cd-124">在此情況下, StoreLoaded 是 WorldAnchorStore 完成載入時的處理常式:</span><span class="sxs-lookup"><span data-stu-id="629cd-124">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

<span data-ttu-id="629cd-125">我們現在有 WorldAnchorStore 的參考, 我們將用它來儲存和載入特定的世界錨點。</span><span class="sxs-lookup"><span data-stu-id="629cd-125">We now have a reference to the WorldAnchorStore which we will use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="629cd-126">儲存 WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="629cd-126">Saving a WorldAnchor</span></span>

<span data-ttu-id="629cd-127">若要儲存, 我們只需要命名我們要儲存的內容, 並將它傳遞至我們想要儲存的 WorldAnchor。</span><span class="sxs-lookup"><span data-stu-id="629cd-127">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="629cd-128">注意: 嘗試將兩個錨點儲存至相同的字串將會失敗 (儲存。儲存會傳回 false)。</span><span class="sxs-lookup"><span data-stu-id="629cd-128">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="629cd-129">您必須先刪除先前的儲存, 然後再儲存新的:</span><span class="sxs-lookup"><span data-stu-id="629cd-129">You need to Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="629cd-130">載入 WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="629cd-130">Loading a WorldAnchor</span></span>

<span data-ttu-id="629cd-131">和以載入:</span><span class="sxs-lookup"><span data-stu-id="629cd-131">And to load:</span></span>

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

<span data-ttu-id="629cd-132">我們還可以使用 store。刪除 () 以移除先前儲存並儲存的錨點。清除 () 以移除所有先前儲存的資料。</span><span class="sxs-lookup"><span data-stu-id="629cd-132">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="629cd-133">列舉現有的錨點</span><span class="sxs-lookup"><span data-stu-id="629cd-133">Enumerating Existing Anchors</span></span>

<span data-ttu-id="629cd-134">若要探索先前儲存的錨點, 請呼叫 GetAllIds。</span><span class="sxs-lookup"><span data-stu-id="629cd-134">To discover previously stored anchors, call GetAllIds.</span></span>

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="629cd-135">保存多個裝置的全息影像</span><span class="sxs-lookup"><span data-stu-id="629cd-135">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="629cd-136">您可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a>, 從本機 WorldAnchor 建立長期雲端錨點, 讓您的應用程式可以在多個 HoloLens、IOS 和 Android 裝置上尋找, 即使這些裝置不會同時出現在同一時間。</span><span class="sxs-lookup"><span data-stu-id="629cd-136">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices are not present together at the same time.</span></span>  <span data-ttu-id="629cd-137">由於雲端錨點是持續性的, 因此一段時間的多個裝置可以看到相對於相同實體位置中的錨點呈現的內容。</span><span class="sxs-lookup"><span data-stu-id="629cd-137">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="629cd-138">若要開始在 Unity 中建立共用體驗, 請嘗試5分鐘的<a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 空間錨點 Unity 快速入門</a>。</span><span class="sxs-lookup"><span data-stu-id="629cd-138">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="629cd-139">當您使用 Azure 空間錨點啟動並執行之後, 就可以<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中建立和尋找錨點</a>。</span><span class="sxs-lookup"><span data-stu-id="629cd-139">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="629cd-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="629cd-140">See Also</span></span>
* [<span data-ttu-id="629cd-141">空間錨點持續性</span><span class="sxs-lookup"><span data-stu-id="629cd-141">Spatial anchor persistence</span></span>](coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="629cd-142"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="629cd-142"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="629cd-143"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">適用于 Unity 的 Azure 空間錨點 SDK</a></span><span class="sxs-lookup"><span data-stu-id="629cd-143"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
