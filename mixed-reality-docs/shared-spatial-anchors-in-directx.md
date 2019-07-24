---
title: DirectX 中的共用空間錨點
description: 說明如何藉由共用空間錨點來同步處理兩部 HoloLens 裝置。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, 同步處理, 空間錨點, 傳輸, 多人遊戲, 視圖, 案例, 逐步解說, 範例程式碼, Azure, Azure 空間錨點, ASA
ms.openlocfilehash: 190d3dfb3eec3fd1a57d2713850a7778a4a71de9
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516883"
---
# <a name="shared-experiences-in-directx"></a><span data-ttu-id="3154f-104">DirectX 中的共用體驗</span><span class="sxs-lookup"><span data-stu-id="3154f-104">Shared experiences in DirectX</span></span>

<span data-ttu-id="3154f-105">共用體驗是指有多個使用者, 每個使用者都有自己的 HoloLens、iOS 或 Android 裝置, 並與位於空間固定點的同一個全息圖進行互動。</span><span class="sxs-lookup"><span data-stu-id="3154f-105">A shared experience is one where multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram which is positioned at a fixed point in space.</span></span> <span data-ttu-id="3154f-106">這是透過空間錨點共用來完成。</span><span class="sxs-lookup"><span data-stu-id="3154f-106">This is accomplished through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="3154f-107">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="3154f-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="3154f-108">您可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a>來建立長期雲端備份的空間錨點, 然後您的應用程式可以在多個 HoloLens、IOS 和 Android 裝置上尋找。</span><span class="sxs-lookup"><span data-stu-id="3154f-108">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="3154f-109">藉由共用多個裝置上的通用空間錨點, 每個使用者都可以看到相對於相同實體位置中的錨點所呈現的內容。</span><span class="sxs-lookup"><span data-stu-id="3154f-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="3154f-110">這可提供即時共用體驗。</span><span class="sxs-lookup"><span data-stu-id="3154f-110">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="3154f-111">您也可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> 跨 HoloLens、iOS 和 Android 裝置取得非同步全像投影持久性。</span><span class="sxs-lookup"><span data-stu-id="3154f-111">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="3154f-112">藉由共用持久的雲端空間錨點，多個裝置就能觀察相同的已保存全像投影一段時間，即使那些裝置並未同時存在。</span><span class="sxs-lookup"><span data-stu-id="3154f-112">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="3154f-113">若要開始在 HoloLens 應用程式中建立共用體驗, 請嘗試5分鐘的<a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure 空間錨點 HoloLens 快速入門</a>。</span><span class="sxs-lookup"><span data-stu-id="3154f-113">To get started building shared experiences in your HoloLens app, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchors HoloLens quickstart</a>.</span></span>

<span data-ttu-id="3154f-114">當您使用 Azure 空間錨點啟動並執行時, 您可以接著在<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">HoloLens 上建立和尋找錨點</a>。</span><span class="sxs-lookup"><span data-stu-id="3154f-114">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">create and locate anchors on HoloLens</a>.</span></span>  <span data-ttu-id="3154f-115">逐步解說也適用于<a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android 和 iOS</a> , 可讓您在所有裝置上共用相同的錨點。</span><span class="sxs-lookup"><span data-stu-id="3154f-115">Walkthroughs are available for <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android and iOS</a> as well, enabling you to share the same anchors on all devices.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="3154f-116">本機錨點傳輸</span><span class="sxs-lookup"><span data-stu-id="3154f-116">Local anchor transfers</span></span>

<span data-ttu-id="3154f-117">在無法使用 Azure 空間錨點的情況下,[本機錨點傳輸](local-anchor-transfers-in-directx.md)可讓一個 hololens 裝置匯出錨點, 以供第二個 hololens 裝置匯入。</span><span class="sxs-lookup"><span data-stu-id="3154f-117">In situations where you cannot use Azure Spatial Anchors, [local anchor transfers](local-anchor-transfers-in-directx.md) enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>  <span data-ttu-id="3154f-118">請注意, 這種方法比起 Azure 空間錨點提供較不健全的錨點回收, 且此方法不支援 iOS 和 Android 裝置。</span><span class="sxs-lookup"><span data-stu-id="3154f-118">Note that this approach provides less robust anchor recall than Azure Spatial Anchors, and iOS and Android devices are not supported by this approach.</span></span>

## <a name="see-also"></a><span data-ttu-id="3154f-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3154f-119">See also</span></span>
* [<span data-ttu-id="3154f-120">混合實境中的共用體驗</span><span class="sxs-lookup"><span data-stu-id="3154f-120">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="3154f-121"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="3154f-121"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="3154f-122"><a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">適用于 HoloLens 的 Azure 空間錨點 SDK</a></span><span class="sxs-lookup"><span data-stu-id="3154f-122"><a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">Azure Spatial Anchors SDK for HoloLens</a></span></span>