---
title: 開始使用
description: 本指南概述啟動和執行混合現實開發的最快方式。
author: mattzmsft
ms.author: mazeller
ms.date: 08/06/2018
ms.topic: article
keywords: 開始使用, 基本, HoloLens, 沉浸式耳機, ar, vr, unity, visual studio, 快速入門, 如何
ms.openlocfilehash: 4277de37ffe4a7ab03f382626452b96bf9157634
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873964"
---
# <a name="get-started"></a>開始使用

歡迎來到混合現實開發的世界! 如果您不熟悉 MR, 本指南將會讓您的中樞儘快啟動並執行。 我們將協助您設定電腦以進行開發、準備好您的裝置, 以及安裝可加速 MR 開發流程的工具。 

## <a name="intro-to-mixed-reality"></a>混合現實簡介

您可能會有一些關於所謂「mixed reality」的問題, 以及它如何與增強的現實 (AR) 和虛擬實境 (VR) 有關。 簡單地說, 混合現實是實體世界與數位世界的混合, 所以它是一種涵蓋所有內容的範圍, 從增強的現實中, 數位內容放在真實世界, 到虛擬實境, 而現實世界幾乎完全已由數位取代。 

![支援 HoloLens 和沉浸式 (VR) 耳機的混合現實應用程式範例](images/mr-island.png)<br>
*混合現實應用程式可以同時支援 HoloLens 和沉浸式 (VR) 耳機*

我們建立了 Windows Mixed Reality 做為單一開發平臺和一組可涵蓋 MR 頻譜的工具, 我們目前支援兩種涵蓋相同頻譜的裝置類型:[Microsoft HoloLens](https://www.microsoft.com/hololens)、全球第一部獨立的全像耳機, 以及[Windows Mixed Reality 的沉浸式耳機和運動控制器](https://www.microsoft.com/windows/windows-mixed-reality), 這些都是連接到電腦以提供強大的虛擬實境體驗。 您可以查看我們的 [mixed reality？](如果您有興趣, 請參閱文章以取得更完整的答案。

## <a name="choose-your-development-path"></a>選擇您的開發路徑

開發混合現實應用程式最簡單的方式是使用[Unity](https://unity3d.com), 這是一種功能強大且常用的中介軟體工具, 通常用於遊戲開發。 如果您想要使用自訂引擎, 也可以[針對 DirectX 建立](directx-development-overview.md), 但大部分的 MR 開發人員會針對其遊戲和應用程式使用 Unity。 有了 Unity, 您就能夠建立以 HoloLens、沉浸式 (VR) 耳機或兩者為目標的混合現實應用程式!

## <a name="prepare-your-pc-and-devices-for-development"></a>準備您的電腦和裝置以進行開發

無論您是否正在建立以 HoloLens、沉浸式 (VR) 耳機為目標的混合現實應用程式, 您都將使用一組常用的工具和 Api。 您也會想要確定您的電腦功能強大, 可用於您要進行的開發。 

>[!NOTE]
>您可以在開發電腦規格、每個軟體工具的支援版本, 以及每個[安裝工具](install-the-tools.md)一文中的相關設定或設定注意事項中找到我們的建議。 請先參閱該文章, 再安裝下列工具。

要安裝的工具:
* [Unity](https://store.unity.com/download)
* [Visual Studio (含 Windows 10 SDK)](https://developer.microsoft.com/windows/downloads)
* [Unity 的混合現實工具組](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)

您也會想要[讓目標裝置進入開發人員模式, 並設定 Visual Studio 將應用程式部署到目標裝置](using-visual-studio.md)。

### <a name="a-note-about-the-mixed-reality-toolkit-for-unity"></a>Unity 混合現實工具組的相關注意事項

![適用于 Unity 的 MRTK](images/mrtkandunity.png)<br>

***YOYO 請充實這項功能, 告訴每個人為什麼 MRTK-UNITY 非常令人驚奇, 而且它裡面的所有酷炫東西:)***

Mixed Reality 工具組是腳本和元件的集合, 目的是要加速以 Microsoft HoloLens 和 Windows Mixed Reality 耳機為目標的應用程式開發。 此專案的目標是減少建立混合實境應用程式的進入障礙，以及回饋伴著我們成長的社群。

## <a name="start-your-first-mr-project"></a>開始您的第一個 MR 專案

既然您的電腦和裝置已設定完成, 您就可以開始在 Unity 中建立第一個混合現實專案。 遵循我們的第一位 mr 學術課程[, mr 基本概念 100:開始使用 Unity](holograms-100.md), 最後您將會在混合現實頭戴式裝置上啟動並執行 cube。

![混合現實 Unity 專案中 cube 的螢幕擷取畫面](images/mr-cube.PNG)<br>
*您在 Unity 中的第一個混合現實專案-hello world!*

## <a name="learn-more-and-get-help"></a>深入瞭解並取得協助

既然您已成功建立第一個 MR 專案, 您可能會有更多的需求。 以下是一些應協助的資源:
* [Mixed reality 開發人員檔](mixed-reality.md)-您已經在這裡, 但還有更多的資訊可以查看, 包括技術檔、設計指引、範例專案, 以及案例研究。
* [混合的現實教學](tutorials.md)課程-遵循涵蓋所有內容的教學課程, 包括設定專案、執行核心 MR 建築組塊、將 Azure 雲端服務整合到您的 MR 應用程式。
* [瞭解 unity](https://unity3d.com/learn) -unity 的網站提供教學課程、專案, 以及每個學習階段之建立者的即時訓練課程。

您也可以從這些絕佳的社區資源取得協助:
* [Mixed reality 開發人員論壇](https://forums.hololens.com/)-適用于混合現實開發人員的官方論壇, 可詢問和回答問題, 以及直接閱讀 MICROSOFT 的 MR 開發新聞。
* [HoloDevelopers 時差頻道](https://holodevelopersslack.azurewebsites.net/)-最健全且資源的外部混合現實特定開發人員通道;這裡的開發人員十分熟悉, 而且很有説明。
* [Unity 論壇](https://forum.unity3d.com/)-unity 的官方論壇。
