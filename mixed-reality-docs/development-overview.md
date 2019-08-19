---
title: 開發總覽
description: 本文概述開發 Windows Mixed Reality 應用程式的基本構件。
author: mattzmsft
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: 入門, 基本, HoloLens, HoloLens 2, 沉浸式耳機, unity, visual studio
ms.openlocfilehash: 23bd173f89a468b4403d44236534bfe811a968dd
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873982"
---
# <a name="development-overview"></a>開發總覽

混合現實應用程式可以使用各種開發人員技術開發。  HoloLens 會執行以[通用 Windows 平臺](https://dev.windows.com/getstarted)建立的應用程式。  沉浸式耳機會執行通用 Windows 平臺應用程式以及 Win32 應用程式。
藉由熟悉中介軟體工具 (例如 Unity), 您可以立即開始打造混合現實體驗。  利用開放原始碼[混合現實工具](install-the-tools.md)組快速開始。
<a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">混合現實服務</a>(例如<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間錨點</a>) 也有可整合至各種跨平臺開發人員技術的 sdk。

>[!VIDEO https://www.youtube.com/embed/A784OdX8xzI]

## <a name="basics-of-mixed-reality-development"></a>混合實境開發的基本概念

[混合實境](mixed-reality.md)體驗可透過用於環境感知的 Windows 新功能啟用。 這些體驗可讓開發人員將[全像投影](hologram.md)放在真實世界中，並可讓使用者藉由實際走動的方式在數位世界中移動。 

以下是混合實境開發的核心基本要素：

<table>
<tr>
<th>Input</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (第 1 代)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td> <a href="gaze.md">頭部注視</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="gaze.md">眼睛目光</a></td><td></td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> 實習/<a href="gestures.md">手勢</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="voice-input.md">語音</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="hardware-accessories.md">遊戲台</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="motion-controllers.md">運動控制器</a></td><td></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th> 認知和空間功能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (第 1 代)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td> <a href="coordinate-systems.md">全局座標</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-sound.md">空間音效</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-mapping.md">空間對應</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr>
</table>



[HoloLens](hololens-hardware-details.md) 的基本互動模型是[視線](gaze.md)、[手勢](gestures.md)及[語音](voice-input.md)，有時稱為 "GGV"。 [Windows Mixed Reality 沉浸式頭戴裝置](immersive-headset-hardware-details.md)也使用視線和語音，但以[動作控制器](motion-controllers.md)取代手勢。


所有以 Windows 為基礎的混合現實裝置都能從適用于 Windows 的輸入生態系統中獲益, 包括滑鼠、鍵盤、遊戲台等等。 使用 HoloLens 時，您可以透過藍牙連接[硬體配件](hardware-accessories.md)。 使用沉浸式頭戴裝置時，您可以透過藍牙、USB 和其他支援的通訊協定，將配件連接到主機電腦。

環境感知功能 (例如[座標](coordinate-systems.md)、[空間音效](spatial-sound.md)和[空間對應](spatial-mapping.md)) 能為混合實境提供必要功能。 空間對應是 HoloLens 特有的功能，可讓全像投影與使用者和其周圍的實體世界互動。 座標系統可讓使用者的移動影響到數位世界中的移動。

[全像攝影](hologram.md)是以[全像攝影轉譯](rendering.md)的光線和音效來製作。 如 [Windows Mixed Reality 首頁](navigating-the-windows-mixed-reality-home.md) (有時稱為「殼層」) 所述，了解放置和持續性的體驗是為您建立使用者體驗基礎的絕佳方式。

## <a name="tools-for-developing-for-mixed-reality"></a>混合實境的開發工具

您所使用的工具取決於您要建置的[應用程式風格](app-views.md)。
* [搭配 2D 檢視的應用程式](building-2d-apps.md)會運用工具來建置適用於 Windows Phone、電腦和平板電腦等環境的通用 Windows 平台應用程式。 這些應用程式會放在 Windows Mixed Reality 首頁中作為 2D 投影體驗，而且可以作用於多個裝置類型 (包括手機及電腦)。
* 沈浸式和全像攝影應用程式需要可利用 Windows Mixed Reality API 的工具。 我們[建議使用 Unity](unity-development-overview.md) 來建置混合實境應用程式。 想要建置自有引擎的開發人員可以[使用 DirectX 和其他 Windows API](directx-development-overview.md)。

不論您要建置何種應用程式類型，這些工具都能為您的應用程式開發經驗提供協助：
* [Visual Studio 與 Windows SDK](using-visual-studio.md)
* [Windows 裝置入口網站](using-the-windows-device-portal.md)
* [HoloLens 模擬器](using-the-hololens-emulator.md)(即將推出 HoloLens 2 模擬器)
* [Windows Mixed Reality 模擬器](using-the-windows-mixed-reality-simulator.md)
* [應用程式品質準則](app-quality-criteria.md)

## <a name="see-also"></a>另請參閱
* [安裝工具](install-the-tools.md)
* <a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">混合現實服務</a>
* [混合現實教學課程](tutorials.md)
* [開放原始碼專案](open-source-projects.md)
* [MR Basics 100：開始使用 Unity](holograms-100.md)
* [Windows Mixed Reality 最低電腦硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [將應用程式提交到 Windows Store](submitting-an-app-to-the-microsoft-store.md)
