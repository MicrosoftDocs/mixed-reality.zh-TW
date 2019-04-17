---
title: Unity 遊戲模式
description: 使用 Unity 編輯器中的播放模式，而不需要部署應用程式中預覽您的裝置上的變更。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、 遠端、 全像攝影版的遠端處理、 全像攝影版的遠端播放程式
ms.openlocfilehash: c118c4af61c6eb2706ef851a6654c18ff7313453
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591183"
---
# <a name="unity-play-mode"></a>Unity 遊戲模式

在 Unity 專案上工作的快速方法是使用 「 播放模式 」。 這會執行您的應用程式在本機在 Unity 編輯器在您的電腦上。 Unity 提供快速的方式，來預覽您的內容，在實際的 HoloLens 裝置上使用全像攝影版的遠端執行功能。

## <a name="unity-play-mode-with-holographic-remoting"></a>使用全像攝影版的遠端執行功能的 unity 遊戲模式

使用全像攝影版的遠端執行功能，您可以在您的電腦上執行 Unity editor 中體驗 HoloLens，您的應用程式。 視線、 手勢、 語音和空間的對應輸入會傳送您 HoloLens 從您的電腦。 呈現的畫面，接著會傳送回到您 HoloLens。 這是適合用來快速偵錯應用程式，而不需要建置和部署完整的專案。
1. 在您的 HoloLens 上移至**Microsoft Store**並安裝**[全像攝影版的遠端播放程式](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 應用程式。
2. 在您的 HoloLens 上啟動**全像攝影版的遠端播放程式**應用程式。
3. 在 Unity 中，移至** 視窗**功能表，然後選取**全像攝影版的模擬**。
4. 設定**模擬模式**要**裝置的遠端**。
5. 針對**遠端機器**，輸入您的 HoloLens 的 IP 位址。
6. 按一下 **[連接]**。 您應該會看到**連線狀態**變更為**Connected**看到變成 HoloLens 在空白畫面。
7. 按一下 **播放**按鈕以啟動播放模式，並體驗您的 HoloLens 上的應用程式。

全像攝影版的遠端處理需要快速的 PC 和 Wi-fi 連線。 請參閱[全像攝影版的遠端播放程式](holographic-remoting-player.md)的完整詳細資料。

為了獲得最佳結果，確定您的應用程式正確地設定[專注點](focus-point-in-unity.md)。 這有助於全像攝影版的遠端執行功能最能適應您的場景方向，以您的無線連線的延遲。

## <a name="see-also"></a>另請參閱
* [全像攝影版的遠端播放程式](holographic-remoting-player.md)
