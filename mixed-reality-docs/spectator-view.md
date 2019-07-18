---
title: Spectator 視圖
description: 將來自外部裝置的全息影像視覺化, 做為在外部顯示或錄製混合現實體驗的影片時, 展現混合現實體驗的方法。
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: Spectator View、iPhone、iOS、iPad、OpenCV、攝影機、ARKit、HoloLens、Mixed Reality、MixedRealityToolkit、示範、記錄
ms.openlocfilehash: 02088d7b218a25c72f2eb98ae24c85a90e6e5b86
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293611"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a>HoloLens 和 HoloLens 2 的 Spectator 視圖

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a>總覽

當您戴 HoloLens 時, 我們通常會忘記不具有該功能的人員無法體驗我們可以世界真奇妙的情況。 Spectator View 可讓其他人在2D 螢幕上看到 HoloLens 使用者在世界中看到的內容。
Spectator View 提供快速且實惠的方法, 讓您以行動裝置錄製 HD 中的全息影像。 它也提供 DSLR 攝影機的全像攝影的專業品質錄影。

## <a name="key-resources"></a>重要資源

* [**GitHub 上的 Spectator 視圖**](https://github.com/microsoft/MixedReality-SpectatorView)
* [**結構**](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Architecture.md)
* [**範例**](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)
* [**行動設定指示**](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Setup.md)
* [**DSLR 設定指示**](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Setup.DSLR.md)

## <a name="use-cases"></a>使用案例
* 您可以使用 iPhone 或 Android 裝置記錄混合現實體驗。 以全 HD 記錄, 並將消除鋸齒功能套用到全息影像, 甚至是陰影。 這是一種符合成本效益且快速的方式, 可讓您掌握全息影像的影片。
* 直接從您的 iPhone 或 iPad 將即時混合現實體驗串流至 Apple 電視, 並延後免費!
* 分享來賓的體驗:讓非 HoloLens 使用者直接從他們的手機或平板電腦體驗全息影像。

## <a name="current-features"></a>目前的功能

* 全息影像的空間同步處理, 因此每個人都能在完全相同的位置看到全像投影。
* iOS (啟用 ARKit 的裝置) 和 Android (啟用 ARCore 的裝置) 支援。
多個 iOS 來賓。
影片錄製 + 全像投影 + 環境音效 + 全息影像音效。
共用工作表, 讓您可以儲存影片、透過電子郵件傳送, 或與其他支援的應用程式共用。

![](images/SpecViewPhoneDemo.jpg)
標記標記![標記](images/hololensspectatorview-500px.jpg) ![](images/spectatorview-300px.png)

下表顯示不同的 Spectator View 功能及其功能。 選擇最適合您影片錄製需求的選項:

|                                      | 行動訊息                  |                    DSLR 攝影機              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| HD 品質                           |         全 HD         |        專業品質 filming (由 DSLR 決定)      |
| 輕鬆移動相機                 |            ✔            |                      ✔                      |
| 第三個人檢視                    |            ✔            |                      ✔                      |
| 可以串流至螢幕           |            ✔            |                      ✔                      |
| 台                             |            ✔            |                                             |
| 無線                             |            ✔            |                                             |
| 其他必要的硬體         |     Android 手機、iPhone    | HoloLens + Rig + 架 + DSLR + PC + Unity |
| 硬體投資                  |           低            |                     高                    |
| 跨平台                       |           Android、iOS   |                                             |
| 已同步處理的內容                 |            ✔            |                      ✔                      |
| 執行時間安裝期間               |         暫態          |                     慢速                    |
## <a name="see-also"></a>另請參閱

* [混合實境擷取](mixed-reality-capture.md) 
* [適用於開發人員的混合實境擷取](mixed-reality-capture-for-developers.md)
* [混合實境中的共用體驗](shared-experiences-in-mixed-reality.md)
