---
title: Unity 中的共用體驗
description: 在 Unity 應用程式中的多個使用者之間共用相同的全息影像。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 共用, 錨點, WorldAnchor, MR 分享 250, WorldAnchorTransferBatch, SpatialPerception, Azure, Azure 空間錨點, ASA
ms.openlocfilehash: fe755c15d942660b1e16b2335db28d3d7ce72816
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516799"
---
# <a name="shared-experiences-in-unity"></a>Unity 中的共用體驗

共用體驗是指有多個使用者, 每個使用者都有自己的 HoloLens、iOS 或 Android 裝置, 並與位於空間固定點的同一個全息圖進行互動。 這是透過空間錨點共用來完成。

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

您可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a>來建立長期雲端備份的空間錨點, 然後您的應用程式可以在多個 HoloLens、IOS 和 Android 裝置上尋找。  藉由共用多個裝置上的通用空間錨點, 每個使用者都可以看到相對於相同實體位置中的錨點所呈現的內容。  這可提供即時共用體驗。

您也可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> 跨 HoloLens、iOS 和 Android 裝置取得非同步全像投影持久性。  藉由共用持久的雲端空間錨點，多個裝置就能觀察相同的已保存全像投影一段時間，即使那些裝置並未同時存在。

若要開始在 Unity 中建立共用體驗, 請嘗試5分鐘的<a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 空間錨點 Unity 快速入門</a>。

當您使用 Azure 空間錨點啟動並執行之後, 就可以<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中建立和尋找錨點</a>。

## <a name="local-anchor-transfers"></a>本機錨點傳輸

在無法使用 Azure 空間錨點的情況下,[本機錨點傳輸](local-anchor-transfers-in-unity.md)可讓一個 hololens 裝置匯出錨點, 以供第二個 hololens 裝置匯入。  請注意, 這種方法比起 Azure 空間錨點提供較不健全的錨點回收, 且此方法不支援 iOS 和 Android 裝置。

## <a name="see-also"></a>另請參閱
* [混合實境中的共用體驗](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">適用于 Unity 的 Azure 空間錨點 SDK</a>