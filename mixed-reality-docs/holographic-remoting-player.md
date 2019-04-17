---
title: 全像攝影版的遠端播放程式
description: 全像攝影版的遠端播放程式是小幫手應用程式連接到電腦的應用程式和支援全像攝影版的遠端執行功能的遊戲。 全像攝影版的遠端資料流全像攝影版內容從 PC 到您的 Microsoft HoloLens 中即時使用 Wi-fi 連線。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、 遠端處理，全像攝影版的遠端處理
ms.openlocfilehash: 16add6c72b594822cacbef6c92ce196ab9b13429
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597086"
---
# <a name="holographic-remoting-player"></a>全像攝影版的遠端播放程式

全像攝影版的遠端播放程式是小幫手應用程式連接到電腦的應用程式和支援全像攝影版的遠端執行功能的遊戲。 全像攝影版的遠端資料流全像攝影版內容從 PC 到您的 Microsoft HoloLens 中即時使用 Wi-fi 連線。

全像攝影版的遠端播放程式只能搭配專為支援全像攝影版的遠端執行功能的 PC 應用程式。

> [!NOTE]
> HoloLens 2 的特定的詳細指引[即將推出](index.md#news-and-notes)。

## <a name="connecting-to-the-holographic-remoting-player"></a>連接到全像攝影版的遠端播放程式

依照您的應用程式連接到全像攝影版的遠端播放程式的指示。 您必須輸入您可以在遠端處理播放程式的主畫面看到，如下所示的 HoloLens 裝置的 IP 位址：

![全像攝影版的遠端播放程式](images/holographicremotingplayer.png)

每當您看到主畫面中，您會知道您沒有連接的應用程式。

請注意，全像攝影版的遠端連線**不會加密**。 您應該一律使用全像攝影版的遠端處理，透過您信任的安全之 Wi-fi 連線。

## <a name="quality-and-performance"></a>品質和效能

品質和效能的經驗會有所不同三個因素：
* **您執行全像攝影版體驗**-轉譯高解析度或高詳細內容的應用程式可能需要更快的電腦或更快的無線連線。
* **您的電腦硬體**-您的個人電腦必須能夠執行，並編碼您全像攝影版的體驗，在每秒 60 畫面格數。 如圖形卡，我們通常建議 GeForce GTX 970 或 AMD Radeon R9 290 或高愈好。 同樣地，您的特定體驗可能需要較高或較低的卡片。
* **您的 Wi-fi 連線**-透過 Wi-fi 串流處理您全像攝影版的體驗。 使用低壅塞的高速網路可提高品質。 使用透過乙太網路纜線連接的電腦，而不是 Wi-fi，可能也提升品質。

## <a name="diagnostics"></a>診斷

若要測量您連線的品質，說 **[啟用診斷]** 在全像攝影版的遠端播放程式的主畫面。 當診斷啟用後時，應用程式會顯示您：
* **FPS** -呈現的畫面格的平均數目遠端處理播放程式會接收和每秒轉譯。 理想狀況是 60 FPS。
* **延遲**-平均的從您的電腦移至 HoloLens 的畫面格所花費的時間量。 愈低愈好。 這是多半取決於您的 Wi-fi 網路。

在 主畫面中，您可以說**停用 診斷**關閉診斷。

## <a name="pc-system-requirements"></a>電腦的系統需求
* 您的電腦**必須**執行 Windows 10 年度更新版。
* 我們建議 GeForce GTX 970 或 AMD Radeon R9 290 或更好的圖形卡。
* 我們建議您透過乙太網路，以減少無線躍點數目的網路連接您的電腦。

## <a name="see-also"></a>另請參閱
* [全像攝影版的遠端軟體授權條款](microsoft-holographic-remoting-software-license-terms.md)
* [Microsoft 隱私權聲明](https://go.microsoft.com/fwlink/?LinkId=521839)
