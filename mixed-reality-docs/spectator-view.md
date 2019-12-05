---
title: 觀眾檢視
description: 將來自外部裝置的全像投影視覺化，作為在外部顯示器上示範混合實境體驗，或錄製混合實境體驗影片的方法。
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 觀眾檢視, iPhone, iOS, iPad, OpenCV, 相機, ARKit, HoloLens, 混合實境, MixedRealityToolkit, 示範, 錄製
ms.openlocfilehash: 9bc1c2809c7d780d439d9efb58f464b41de3dccd
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491168"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a>HoloLens 和 HoloLens 2 的觀眾檢視

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a>概觀

戴上 HoloLens 時，我們通常會忘記沒有穿戴裝置的人無法體驗我們所體驗的奧妙。 觀眾檢視可以讓其他人在 2D 螢幕上看到 HoloLens 使用者在他們的世界中所看到的內容。
觀眾檢視提供快速且實惠的方法，讓您使用行動裝置以 HD 錄製全像投影。 它也提供透過攝影機的全像投影專業品質錄影。

## <a name="key-resources"></a>主要資源

* [**GitHub 上的觀眾檢視**](https://github.com/microsoft/MixedReality-SpectatorView)
* [**觀眾檢視文件**](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [**觀眾檢視範例**](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a>使用案例
* 您可以使用 iPhone 或 Android 裝置錄製混合實境體驗。 以 Full HD 錄製，對全像投影甚至是陰影套用消除鋸齒功能。 這是擷取全像投影影片的符合成本效益且快速的方式。
* 直接從您的 iPhone 或 iPad 將即時混合實境體驗串流至 Apple TV，沒有延遲！
* 與來賓分享體驗：讓非 HoloLens 使用者直接從他們的手機或平板電腦體驗全像投影。

## <a name="current-features"></a>目前的功能

* 全像投影的空間同步處理，因此每個人都能在完全相同的位置看到全像投影。
* 支援 iOS (已啟用 ARKit 的裝置) 和 Android (已啟用 ARCore 的裝置)。
多個 iOS 來賓。
影片錄製 + 全像投影 + 環境音效 + 全像投影音效。
共用工作表，讓您可以儲存影片、透過電子郵件傳送，或與其他支援的應用程式共用。

![標記](images/SpecViewPhoneDemo.jpg)
![標記](images/hololensspectatorview-500px.jpg) ![標記](images/spectatorview-300px.png)

下表顯示不同的觀眾檢視功能及其功能。 選擇最適合您影片錄製需求的選項：

|                                      | 行動裝置                  |                    攝影機              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| HD 品質                           |         Full HD         |        專業品質攝影 (由攝影機決定)      |
| 簡易相機移動                 |            ✔            |                      ✔                      |
| 第三人稱視角                    |            ✔            |                      ✔                      |
| 可以串流至螢幕           |            ✔            |                      ✔                      |
| 可攜式                             |            ✔            |                                             |
| 無線                             |            ✔            |                                             |
| 其他必要硬體         |     Android 手機、iPhone    | HoloLens + Rig + 三腳架 + 攝影機 + PC + Unity |
| 硬體投資                  |           低            |                     高                    |
| 跨平台                       |           Android、iOS   |                                             |
| 同步處理的內容                 |            ✔            |                      ✔                      |
| 執行階段安裝持續時間               |         立即          |                     慢速                    |
## <a name="see-also"></a>請參閱

* [混合實境擷取](mixed-reality-capture.md) 
* [適用於開發人員的混合實境擷取](mixed-reality-capture-for-developers.md)
* [混合實境中的共用體驗](shared-experiences-in-mixed-reality.md)
