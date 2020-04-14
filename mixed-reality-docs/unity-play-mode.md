---
title: Unity 播放模式
description: 在 Unity 編輯器中使用 [播放] 模式，即可在不部署應用程式的情況下，預覽裝置上的變更。
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity，遠端，全像攝影遠端，全像攝影遠端播放
ms.openlocfilehash: dca7ffba1270802fcabed8a88fe7428ef2981553
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277556"
---
# <a name="unity-play-mode"></a>Unity 播放模式

處理 Unity 專案的快速方式是使用「播放模式」。 這會在您的電腦上，于 Unity 編輯器中本機執行您的應用程式。 Unity 使用全像攝影遠端來提供快速的方式，以在真實的 HoloLens 裝置上預覽內容。 播放模式也可以搭配連接至開發電腦的 Windows Mixed Reality 耳機使用。

## <a name="unity-play-mode-with-holographic-remoting"></a>使用全像攝影遠端的 Unity 播放模式

使用全像攝影遠端功能時，您可以在 HoloLens 上體驗應用程式，而在電腦上的 Unity 編輯器中執行。 「注視」、「手勢」、「語音」和「空間對應」輸入都會從您的 HoloLens 傳送到您的電腦。 轉譯後的框架會傳送回您的 HoloLens。 這是在無需建立和部署完整專案的情況下，快速地對應用程式進行錯用的絕佳方式。
1. 在您的 HoloLens 上，移至**Microsoft Store**並安裝全像攝影版的 **[遠端播放機](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 應用程式。
2. 在您的 HoloLens 上，啟動全像攝影版的**遠端播放機**應用程式。
3. 在 Unity 中，移至 [**視窗]** 功能表，然後選取 [全像**模擬**]。
4. 將**模擬模式**設定為 [**遠端至裝置**]。
5. 針對 [**遠端電腦**]，輸入 HOLOLENS 的 IP 位址。
6. 按一下 [連接]。 您應該會看到 [連線**狀態**] 變更為 [**已連接**]，並在 HoloLens 中看到畫面變成空白。
7. 按一下 [**播放**] 按鈕以啟動播放模式，並在 HoloLens 上體驗應用程式。

全像攝影遠端處理需要快速的電腦和 Wi-fi 連線。 如需完整詳細資料，請參閱全像攝影[遠端播放](holographic-remoting-player.md)程式。

為獲得最佳結果，請確定您的應用程式已正確設定[焦點點](focus-point-in-unity.md)。 這可協助全像攝影的遠端處理，以最符合您的無線連線延遲來調整您的場景。

## <a name="see-also"></a>另請參閱
* [全像攝影遠端播放程式](holographic-remoting-player.md)
