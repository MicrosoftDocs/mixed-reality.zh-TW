---
title: 共用 DirectX 中的空間錨點
description: 說明如何同步處理兩個的 HoloLens 裝置共用空間的錨點。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens，同步處理，空間的錨點、 傳輸、 多人遊戲，檢視、 案例、 逐步解說、 範例程式碼，Azure，Azure 空間的錨點，ASA
ms.openlocfilehash: 190d3dfb3eec3fd1a57d2713850a7778a4a71de9
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2019
ms.locfileid: "59597110"
---
# <a name="shared-experiences-in-directx"></a><span data-ttu-id="9cafc-104">DirectX 中的共用的體驗</span><span class="sxs-lookup"><span data-stu-id="9cafc-104">Shared experiences in DirectX</span></span>

<span data-ttu-id="9cafc-105">分享的經驗，是指多個使用者，各有自己的 HoloLens、 iOS 或 Android 裝置上，共同檢視和互動相同的全像它位於固定的點，在空間中。</span><span class="sxs-lookup"><span data-stu-id="9cafc-105">A shared experience is one where multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram which is positioned at a fixed point in space.</span></span> <span data-ttu-id="9cafc-106">這是透過共用空間的錨點來完成。</span><span class="sxs-lookup"><span data-stu-id="9cafc-106">This is accomplished through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="9cafc-107">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="9cafc-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="9cafc-108">您可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間的錨點</a>建立長期雲端備份空間錨點，然後會跨多個 HoloLens、 iOS 和 Android 裝置可以找出您的應用程式的。</span><span class="sxs-lookup"><span data-stu-id="9cafc-108">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="9cafc-109">藉由跨多個裝置共用常見的空間錨點，每位使用者都可以看到相對於該錨點相同的實體位置中呈現內容。</span><span class="sxs-lookup"><span data-stu-id="9cafc-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="9cafc-110">這可讓您即時分享經驗。</span><span class="sxs-lookup"><span data-stu-id="9cafc-110">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="9cafc-111">您也可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間的錨點</a>非同步闀持續性跨 HoloLens、 iOS 和 Android 裝置。</span><span class="sxs-lookup"><span data-stu-id="9cafc-111">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="9cafc-112">藉由共用持久的雲端空間錨點，多個裝置可以觀察相同的保存全像經過一段時間，即使這些裝置不存在一起在相同的時間。</span><span class="sxs-lookup"><span data-stu-id="9cafc-112">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="9cafc-113">若要開始建置 HoloLens 應用程式中的共用的體驗，試用 5 分鐘<a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">空間錨點 HoloLens Azure 快速入門</a>。</span><span class="sxs-lookup"><span data-stu-id="9cafc-113">To get started building shared experiences in your HoloLens app, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchors HoloLens quickstart</a>.</span></span>

<span data-ttu-id="9cafc-114">一旦您啟動並執行 Azure 空間的起點，您可以接著<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">建立和 HoloLens 上尋找起點</a>。</span><span class="sxs-lookup"><span data-stu-id="9cafc-114">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">create and locate anchors on HoloLens</a>.</span></span>  <span data-ttu-id="9cafc-115">皆有逐步解說<a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android 和 iOS</a> ，讓您能夠共用相同的錨點，在所有裝置上。</span><span class="sxs-lookup"><span data-stu-id="9cafc-115">Walkthroughs are available for <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android and iOS</a> as well, enabling you to share the same anchors on all devices.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="9cafc-116">本機的錨點傳輸</span><span class="sxs-lookup"><span data-stu-id="9cafc-116">Local anchor transfers</span></span>

<span data-ttu-id="9cafc-117">在您無法在此使用 Azure 空間錨點的情況下[本機的錨點傳輸](local-anchor-transfers-in-directx.md)啟用一個 HoloLens 裝置匯出要匯入第二個的 HoloLens 裝置所錨點。</span><span class="sxs-lookup"><span data-stu-id="9cafc-117">In situations where you cannot use Azure Spatial Anchors, [local anchor transfers](local-anchor-transfers-in-directx.md) enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>  <span data-ttu-id="9cafc-118">請注意，此方法提供較不強大的錨點重新叫用比 Azure 空間的錨點，iOS 和 Android 裝置不支援這種方法。</span><span class="sxs-lookup"><span data-stu-id="9cafc-118">Note that this approach provides less robust anchor recall than Azure Spatial Anchors, and iOS and Android devices are not supported by this approach.</span></span>

## <a name="see-also"></a><span data-ttu-id="9cafc-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9cafc-119">See also</span></span>
* [<span data-ttu-id="9cafc-120">在混合實境中共用體驗</span><span class="sxs-lookup"><span data-stu-id="9cafc-120">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="9cafc-121"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間的錨點</a></span><span class="sxs-lookup"><span data-stu-id="9cafc-121"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="9cafc-122"><a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">Azure 的空間錨點 HoloLens 的 SDK</a></span><span class="sxs-lookup"><span data-stu-id="9cafc-122"><a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">Azure Spatial Anchors SDK for HoloLens</a></span></span>