---
title: Unreal 開發概觀
description: 開始在 Unreal 中建置混合實境應用程式。
author: sw5813
ms.author: suwu
ms.date: 10/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, beta, 串流, 遠端, 混合實境, 開發, 開始使用, 新專案, 模擬器, 文件
ms.openlocfilehash: 96b0259e4ac567389f999d3a453fb68bb848b266
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491177"
---
# <a name="unreal-development-overview"></a>Unreal 開發概觀

Unreal Engine 4 的混合實境支援現在是搶鮮版！ 如果您是 Unreal 開發的新手，<a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">開始使用 Unreal Engine 4</a> 是一個絕佳的探索頁面。 如果您需要資產，Unreal 具有完整的 <a href="https://www.unrealengine.com/marketplace//store" target="_blank">Marketplace</a>。 

在您具備 Unreal Engine 4 的基本了解之後，您可以造訪 Unreal Engine 文件網站上的 <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">Microsoft HoloLens 開發</a>頁面，以了解如何在 HoloLens 上建置及執行您的應用程式。 請務必造訪 <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">Unreal 混合實境論壇</a>，與在 Unreal 中建置混合實境應用程式的社群進行互動。 這是尋找您可能遇到問題解決方案的絕佳位置。

## <a name="installing-the-prerequisites"></a>安裝必要條件

若要開始在 Unreal 中建置 HoloLens 2 應用程式，您需要 [HoloLens 2 模擬器](using-the-hololens-emulator.md)或 HoloLens 頭戴式裝置。 您也需要安裝最新版本的 Visual Studio，其中包含<a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/Prerequisites/index.html" target="_blank">適用於 Unreal 的 HoloLens 2 必要條件</a>中列出的工作負載和元件。

## <a name="building-and-running-your-unreal-app"></a>建置並執行您的 Unreal 應用程式

首先，<a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/HowTo/PackageApp/index.html" target="_blank">封裝您的 HoloLens 2 應用程式</a>。 接下來，選擇您想要部署套件的位置：
* <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartEmulator/index.html" target="_blank">部署至 HoloLens 2 模擬器</a>
* <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartDevice/index.html" target="_blank">部署至 HoloLens 2 頭戴式裝置</a>

## <a name="streaming-your-app-to-a-headset-via-the-holographic-remoting-player"></a>透過全像攝影遠端處理播放器將您的應用程式串流至頭戴式裝置

將您的應用程式從桌面串流至 HoloLens 頭戴式裝置上的全像攝影遠端處理播放器應用程式有兩個主要優點： 
* 加速開發，讓您不需要在每次進行變更時重新封裝及上傳您的應用程式
* 利用桌面的功能，讓您可以轉譯成桌面 GPU 所允許的多個多邊形，而不受頭戴式裝置上可用電腦的限制

若要開始使用串流，請參閱 <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartStreaming/index.html" target="_blank">HoloLens 2 串流快速入門</a>[]()。

## <a name="see-also"></a>請參閱
* <a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">行動裝置的 Unreal 效能指導方針</a>
