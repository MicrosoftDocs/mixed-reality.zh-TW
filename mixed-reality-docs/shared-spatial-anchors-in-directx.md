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
# <a name="shared-experiences-in-directx"></a>DirectX 中的共用體驗

共用體驗是指有多個使用者, 每個使用者都有自己的 HoloLens、iOS 或 Android 裝置, 並與位於空間固定點的同一個全息圖進行互動。 這是透過空間錨點共用來完成。

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

您可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間錨點</a>來建立長期雲端備份的空間錨點, 然後您的應用程式可以在多個 HoloLens、IOS 和 Android 裝置上尋找。  藉由共用多個裝置上的通用空間錨點, 每個使用者都可以看到相對於相同實體位置中的錨點所呈現的內容。  這可提供即時共用體驗。

您也可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> 跨 HoloLens、iOS 和 Android 裝置取得非同步全像投影持久性。  藉由共用持久的雲端空間錨點，多個裝置就能觀察相同的已保存全像投影一段時間，即使那些裝置並未同時存在。

若要開始在 HoloLens 應用程式中建立共用體驗, 請嘗試5分鐘的<a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure 空間錨點 HoloLens 快速入門</a>。

當您使用 Azure 空間錨點啟動並執行時, 您可以接著在<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">HoloLens 上建立和尋找錨點</a>。  逐步解說也適用于<a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android 和 iOS</a> , 可讓您在所有裝置上共用相同的錨點。

## <a name="local-anchor-transfers"></a>本機錨點傳輸

在無法使用 Azure 空間錨點的情況下,[本機錨點傳輸](local-anchor-transfers-in-directx.md)可讓一個 hololens 裝置匯出錨點, 以供第二個 hololens 裝置匯入。  請注意, 這種方法比起 Azure 空間錨點提供較不健全的錨點回收, 且此方法不支援 iOS 和 Android 裝置。

## <a name="see-also"></a>另請參閱
* [混合實境中的共用體驗](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">適用于 HoloLens 的 Azure 空間錨點 SDK</a>