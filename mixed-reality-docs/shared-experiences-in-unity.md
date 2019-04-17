---
title: 在 Unity 中的共用的體驗
description: 共用相同的 Unity 應用程式中的多個使用者之間全像投影。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 共用、 錨點、 WorldAnchor、 MR 共用 250 WorldAnchorTransferBatch，SpatialPerception、 Azure、 Azure 空間的錨點，ASA
ms.openlocfilehash: fe755c15d942660b1e16b2335db28d3d7ce72816
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2019
ms.locfileid: "59597114"
---
# <a name="shared-experiences-in-unity"></a>在 Unity 中的共用的體驗

分享的經驗，是指多個使用者，各有自己的 HoloLens、 iOS 或 Android 裝置上，共同檢視和互動相同的全像它位於固定的點，在空間中。 這是透過共用空間的錨點來完成。

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

您可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間的錨點</a>建立長期雲端備份空間錨點，然後會跨多個 HoloLens、 iOS 和 Android 裝置可以找出您的應用程式的。  藉由跨多個裝置共用常見的空間錨點，每位使用者都可以看到相對於該錨點相同的實體位置中呈現內容。  這可讓您即時分享經驗。

您也可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間的錨點</a>非同步闀持續性跨 HoloLens、 iOS 和 Android 裝置。  藉由共用持久的雲端空間錨點，多個裝置可以觀察相同的保存全像經過一段時間，即使這些裝置不存在一起在相同的時間。

若要開始建置 Unity 中的共用的體驗，試用 5 分鐘<a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">空間錨點 Unity Azure 快速入門</a>。

一旦您啟動並執行 Azure 空間的起點，您可以接著<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">建立，並找出在 Unity 中的錨點</a>。

## <a name="local-anchor-transfers"></a>本機的錨點傳輸

在您無法在此使用 Azure 空間錨點的情況下[本機的錨點傳輸](local-anchor-transfers-in-unity.md)啟用一個 HoloLens 裝置匯出要匯入第二個的 HoloLens 裝置所錨點。  請注意，此方法提供較不強大的錨點重新叫用比 Azure 空間的錨點，iOS 和 Android 裝置不支援這種方法。

## <a name="see-also"></a>另請參閱
* [在混合實境中共用體驗](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間的錨點</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure 的空間錨點適用於 Unity SDK</a>