---
title: 全像攝影遠端播放
description: 全像攝影遠端播放程式是一種隨附的應用程式, 可連接到支援全像攝影遠端的電腦應用程式和遊戲。 全像攝影遠端處理會使用 Wi-fi 連線, 即時將全像個人電腦的內容串流至您的 Microsoft HoloLens。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、遠端、全像攝影遠端
ms.openlocfilehash: b8354295f9752e73cc9b34c1769254e49808b63f
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813716"
---
# <a name="holographic-remoting-player"></a>全像攝影遠端播放

全像攝影遠端播放程式是一種隨附的應用程式, 可連接到支援全像攝影遠端的電腦應用程式和遊戲。 全像攝影遠端處理會使用 Wi-fi 連線, 即時將全像個人電腦的內容串流至您的 Microsoft HoloLens。

全像攝影遠端播放程式只能用於專為支援全像攝影遠端功能而設計的電腦應用程式。

全像是 HoloLens 和 HoloLens 2 都提供全像攝影遠端播放程式。  使用 HoloLens 支援全像攝影遠端功能的電腦應用程式必須更新, 以支援使用 HoloLens 2 的全像 Remtoing。  如果您對支援的版本有任何疑問, 請洽詢您的應用程式提供者。

## <a name="connecting-to-the-holographic-remoting-player"></a>連接到全像攝影遠端播放播放機

遵循您應用程式的指示, 連接到全像攝影的遠端播放播放機。 您將需要輸入 HoloLens 裝置的 IP 位址, 您可以在遠端播放程式的主畫面上看到它, 如下所示:

![全像攝影遠端播放](images/holographicremotingplayer.png)

當您看到主畫面時, 您會知道您沒有連線的應用程式。

請注意, 全像攝影遠端連線**不會加密**。 您應該一律在您信任的安全 Wi-fi 連線上使用全像攝影遠端。

## <a name="quality-and-performance"></a>品質和效能

您的體驗品質和效能會因三個因素而有所不同:
* **您**正在執行的全像攝影體驗-呈現高解析度或高度詳細內容的應用程式, 可能需要更快速的電腦或更快的無線連線。
* **您**的電腦硬體-您的電腦必須能夠在每秒60畫面上執行及編碼您的全像體驗。 針對圖形配接器, 我們通常建議使用 GeForce GTX 970 或 AMD Radeon R9 290 或更高的品質。 同樣地, 您的特定體驗可能需要較高或較低的卡片。
* **您的 wi-fi**連線-您的全像攝影體驗會透過 wi-fi 進行串流處理。 使用具有低擁塞的快速網路, 將品質最大化。 使用透過 Ethernet 纜線 (而非 Wi-fi) 連線的電腦, 也可以改善品質。

## <a name="diagnostics"></a>診斷

若要測量連線的品質, 請在全像攝影遠端播放程式的主畫面上說「**啟用診斷**」。 啟用診斷時, 應用程式會顯示:
* **FPS** -遠端播放者每秒接收和轉譯的轉譯框架平均數目。 理想的情況是 60 FPS。
* **延遲**-框架從您的電腦移至 HoloLens 所需的平均時間量。 越低越好。 這主要取決於您的 Wi-fi 網路。

在主畫面上, 您可以說「**停用診斷**」來關閉診斷。

## <a name="pc-system-requirements"></a>電腦系統需求
* 您的電腦**必須**執行 Windows 10 年度更新版或更新版本。
* 我們建議使用 GeForce GTX 970 或 AMD Radeon R9 290 或更好的圖形配接器。
* 我們建議您透過 ethernet 將電腦連線到您的網路, 以減少無線躍點的數目。

## <a name="see-also"></a>另請參閱
* [全像攝影遠端軟體授權條款](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隱私權聲明](https://go.microsoft.com/fwlink/?LinkId=521839)
