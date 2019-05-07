---
title: 開發概觀
description: 本文章概述開發 Windows Mixed Reality 應用程式的基本建置組塊。
author: mattzmsft
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: 取得已啟動，基本概念、 HoloLens、 HoloLens 2 沈浸式耳機、 unity / visual studio
ms.openlocfilehash: 23bd173f89a468b4403d44236534bfe811a968dd
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873982"
---
# <a name="development-overview"></a>開發概觀

混合的實境應用程式可以使用各種不同的開發人員技術進行開發。  HoloLens 執行建立的應用程式[通用 Windows 平台](https://dev.windows.com/getstarted)。  執行通用 Windows 平台應用程式，以及您在 Win32 應用程式的沈浸式耳機。
藉由取得熟悉 Unity 這類的中介軟體工具，您可以開始的建置混合的實境體驗今天。  利用開放原始碼[混合實境 Toolkit](install-the-tools.md)來快速上手。
<a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">混合實境 services</a>，這類<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間的錨點</a>，有各種跨平台開發人員技術也可以整合的 Sdk。

>[!VIDEO https://www.youtube.com/embed/A784OdX8xzI]

## <a name="basics-of-mixed-reality-development"></a>混合的實境開發的基本概念

[混合實境](mixed-reality.md)體驗會啟用環境的了解新的 Windows 功能。 這些可讓開發人員来放置[全像](hologram.md)在真實世界中，並可讓使用者透過數位世界之間移動解譯為常值逐一查看相關。 

以下是混合的實境開發的核心建置組塊：

<table>
<tr>
<th>Input</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens （第 1 代）</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td> <a href="gaze.md">Head 視線</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="gaze.md">眼睛視線</a></td><td></td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> 指針 /<a href="gestures.md">筆勢</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="voice-input.md">Voice</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="hardware-accessories.md">Gamepad</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="motion-controllers.md">運動控制器</a></td><td></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th> 認知和空間的功能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens （第 1 代）</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td> <a href="coordinate-systems.md">全局座標</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-sound.md">空間音效</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-mapping.md">空間對應</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr>
</table>



基本互動模型[HoloLens](hololens-hardware-details.md)是[視線](gaze.md)，[筆勢](gestures.md)，以及[語音](voice-input.md)，有時又稱為*GGV*. [Windows Mixed Reality 沈浸式耳機](immersive-headset-hardware-details.md)也使用視線和語音，但交換[動作控制器](motion-controllers.md)手勢。


所有以 Windows 為基礎的混合的實境裝置受益到 Windows，包括滑鼠、 鍵盤、 遊戲台，於輸入的生態系統。 HoloLens，與[硬體附屬應用程式](hardware-accessories.md)透過藍牙連線。 使用沈浸式耳機，附屬應用程式連線到主機電腦透過藍芽、 USB、 和其他支援的通訊協定。

環境的了解功能，像是[座標](coordinate-systems.md)，[空間音效](spatial-sound.md)，並[空間對應](spatial-mapping.md)混合實境中提供所需的功能。 空間對應是 HoloLens，唯一的並可讓使用者和實體世界互動全像投影。 座標系統可讓使用者移動，以影響數位世界中的移動。

[全像投影](hologram.md)組成光線] 與 [音效，依賴[全像攝影版的轉譯](rendering.md)。 了解放置和持續性的體驗，如所示[Windows Mixed Reality 家用](navigating-the-windows-mixed-reality-home.md)（有時稱為 「 殼層 」） 很大的方式讓自己的使用者經驗。

## <a name="tools-for-developing-for-mixed-reality"></a>混合實境開發工具

您所使用的工具取決於[樣式的應用程式](app-views.md)您想要建置。
* [應用程式的 2D 檢視](building-2d-apps.md)運用的工具，如建置通用 Windows 平台應用程式適用於 Windows Phone、 個人電腦和平板電腦等的環境。 這些應用程式會放在家中的 Windows Mixed Reality 2D 投影為經驗豐富，而且可以作用於多個裝置類型 （包括電腦及手機）。
* 沈浸式和全像攝影版的應用程式必須設計成可利用 Windows Mixed Reality api 的工具。 我們[建議使用 Unity](unity-development-overview.md)建置混合的實境應用程式。 開發人員想要建置自己的引擎可以[使用 DirectX 和其他 Windows Api](directx-development-overview.md)。

不論您要建置的應用程式的類型，這些工具會協助您的應用程式的開發經驗：
* [Visual Studio 和 Windows SDK](using-visual-studio.md)
* [Windows 裝置入口網站](using-the-windows-device-portal.md)
* [HoloLens 模擬器](using-the-hololens-emulator.md)（即將推出的 HoloLens 2 模擬器）
* [Windows Mixed Reality 模擬器](using-the-windows-mixed-reality-simulator.md)
* [應用程式品質準則](app-quality-criteria.md)

## <a name="see-also"></a>另請參閱
* [安裝工具](install-the-tools.md)
* <a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">混合的實境服務</a>
* [混合的實境教學課程](tutorials.md)
* [開放原始碼專案](open-source-projects.md)
* [MR Basics 100：開始使用 Unity](holograms-100.md)
* [Windows Mixed Reality 最小電腦的硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [提交至 Windows 市集應用程式](submitting-an-app-to-the-microsoft-store.md)
