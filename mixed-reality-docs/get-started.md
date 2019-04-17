---
title: 立即開始
description: 本指南概要說明最快的方法，以啟動並執行混合的實境開發。
author: mattzmsft
ms.author: mazeller
ms.date: 08/06/2018
ms.topic: article
keywords: 要開始，基本概念、 HoloLens、 沈浸式耳機、 ar、 vr、 unity、 visual studio、 快速入門中，如何
ms.openlocfilehash: 92fbc6eee227da571ff36401f84cf81a093062d7
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594861"
---
# <a name="get-started"></a>立即開始

歡迎來到混合的實境開發的世界 ！ 如果您還不熟悉 MR，本指南會啟動您的中樞，並盡快執行。 我們將協助您讓您的電腦集更適用於開發、 準備您的裝置，並安裝將會加速 MR 開發程序的工具。 

## <a name="intro-to-mixed-reality"></a>簡介混合實境

您可能會有一些疑問所熟知的 「 混合實境 」，以及它與要擴增實境 (AR) 和虛擬實境 (VR)。 簡單地說，混合的實境是混合，其與數位世界中，實體世界的範圍涵蓋所有項目從擴增實境，因此在真實世界中，虛擬實境，以您實際其中幾乎完全是放置數位內容由數位所取代。 

![支援 HoloLens 和沈浸式 (VR) 耳機 mixed 的 reality 應用程式的範例](images/mr-island.png)<br>
*HoloLens 和沈浸式 (VR) 耳機，可支援混合的實境應用程式*

我們建立 Windows Mixed Reality 做為單一的開發平台和 MR 範圍，就可以涵蓋的工具組，而且我們目前支援兩種裝置類型，其中涵蓋相同的範圍：[Microsoft HoloLens](https://www.microsoft.com/hololens)，全世界第一個獨立全像攝影版耳機，並[Windows Mixed Reality 沈浸式耳機和動作控制器](https://www.microsoft.com/windows/windows-mixed-reality)，連線至電腦上以功能強大的虛擬實境體驗。 您可以看看我們什麼 [混合實境？]（如果您想要更全面的回答的文章。

## <a name="choose-your-development-path"></a>選擇您開發的路徑

開發混合的實境應用程式的最簡單方式使用[Unity](https://unity3d.com)，通常用來開發遊戲的強大且受歡迎的中介軟體工具。 如果您想要使用自訂的引擎，您也可以[針對 DirectX 建置](directx-development-overview.md)，但大部分 MR 開發人員使用 Unity 進行其遊戲和應用程式。 使用 Unity，您將可以建立目標 HoloLens、 沈浸式 (VR) 耳機，或兩者的混合的實境應用程式 ！

## <a name="prepare-your-pc-and-devices-for-development"></a>準備您的電腦和裝置進行開發

不論您要建置以 HoloLens、 沈浸式 (VR) 耳機，或兩者為目標的混合的實境應用程式，您將使用一組常用的工具和 Api。 您也會想要確定您的電腦是強大的開發時要執行。 

>[!NOTE]
>您可以找到我們在開發電腦上的建議規格，支援的版本，每個軟體工具，以及相關設定附註中的 for each[安裝工具](install-the-tools.md)文章。 請安裝下列工具之前，檢閱該文章。

若要安裝的工具：
* [Unity](https://store.unity.com/download)
* [Visual Studio (使用 Windows 10 SDK)](https://developer.microsoft.com/windows/downloads)
* [混合的實境適用於 Unity 的工具組](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)

您也會想要[將您的目標裝置放入開發人員模式和設定 Visual Studio 的應用程式部署到目標裝置](using-visual-studio.md)。

### <a name="a-note-about-the-mixed-reality-toolkit-for-unity"></a>有關用於 Unity 的混合實境工具組的注意事項

![MRTK for Unity](images/mrtkandunity.png)<br>

***YOYO 請細節時，並告訴大家，為什麼 MRTK UNITY 是因此令人讚嘆且所有酷炫的內容有內:)***

混合實境工具組是指令碼的集合，而且元件能加速開發以 Microsoft HoloLens 與 Windows Mixed Reality 耳機為目標的應用程式。 專案被針對至項目，以建立混合的實境應用程式以及貢獻回饋給社群隨著我們越來越減少屏障。

## <a name="start-your-first-mr-project"></a>啟動您的第一個 MR 專案

現在，您的電腦和裝置設定，您即可建立在 Unity 中的第一個混合的實境專案。 遵循我們第一個 MR academy 課程[MR 基本概念 100:開始使用 Unity](holograms-100.md)，結束時，您將會擁有啟動並執行混合的實境耳機的 cube。

![混合的實境 Unity 專案中之 cube 的螢幕擷取畫面](images/mr-cube.PNG)<br>
*第一個混合的實境專案中 Unity-hello world ！*

## <a name="learn-more-and-get-help"></a>進一步了解，並取得協助

既然您已成功建立第一個 MR 專案，您可能飢餓了 ！ 以下是一些應該可以幫助的資源：
* [混合實境開發人員文件](mixed-reality.md)-您已經在這裡，但還有更多檢查，包括技術文件、 設計指引、 範例專案，以及案例研究。
* [混合的實境 academy](academy.md) -依照本教學課程涵蓋範圍從專案中，實作核心 MR 建置組塊所設定，來整合 Azure 雲端服務到 MR 應用程式。
* [了解 Unity](https://unity3d.com/learn) -Unity 的網站提供的教學課程、 專案和現場直播訓練工作階段建立者的每個階段的學習。

您也可以從這些絕佳的社群資源取得說明：
* [混合實境開發人員論壇](https://forums.hololens.com/)-混合的實境開發人員，可以詢問和回答問題，以及讀取 MR 開發人員新聞，直接從 Microsoft 的官方論壇。
* [HoloDevelopers Slack 通道](https://holodevelopersslack.azurewebsites.net/)-最強大且豐富的外部混合實境特有的開發人員通道; 這裡的開發人員都了解並有幫助。
* [Unity 論壇](https://forum.unity3d.com/)-Unity 的官方論壇。
