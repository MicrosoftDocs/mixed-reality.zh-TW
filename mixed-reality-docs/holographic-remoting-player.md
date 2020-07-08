---
title: 全像攝影遠端播放程式
description: 全像攝影遠端播放程式是一種隨附的應用程式，可連接到支援全像攝影遠端的電腦應用程式和遊戲。 全像攝影遠端處理會使用 Wi-fi 連線，即時將全像個人電腦的內容串流至您的 Microsoft HoloLens。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens、遠端、全像攝影遠端
ms.openlocfilehash: 8b1d58b2c2ce8f379a87059bb5add0f85f507259
ms.sourcegitcommit: fef42e2908e49822f2d13b05d2f9260bf0d72158
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "86061131"
---
# <a name="holographic-remoting-player"></a>全像攝影遠端播放程式

>[!IMPORTANT]
>HoloLens 2 的全像攝影遠端功能是主要的版本變更。 [ **Hololens （第1代）** 的遠端應用程式](add-holographic-remoting.md)必須使用 NuGet **1.x.x**套件1.x 版，而[ **hololens 2**的遠端應用程式](holographic-remoting-create-host.md)**必須使用 2.x. x.** x。 這表示針對 HoloLens 2 所撰寫的遠端應用程式與 HoloLens （第1代）不相容，反之亦然。

全像攝影[遠端播放](https://www.microsoft.com/p/holographic-remoting-player/9nblggh4sv40)程式是一種隨附的應用程式，可連接到支援全像攝影遠端的電腦應用程式和遊戲。 全像攝影遠端處理會使用 Wi-fi 連線，即時將全像個人電腦的內容串流至您的 Microsoft HoloLens。

全像攝影遠端播放程式只能用於專為支援全像攝影遠端功能而設計的電腦應用程式。

全像 HoloLens （第1代）和 HoloLens 2 都可使用全像攝影遠端播放程式。  支援使用 HoloLens 進行全像攝影遠端功能的電腦應用程式必須更新，以支援使用 HoloLens 2 的全像攝影遠端功能。 如果您對支援的版本有任何疑問，請洽詢您的應用程式提供者。

>[!TIP]
>從版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)開始，您也可以在執行[windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)的 windows 電腦上使用全像攝影遠端播放程式。

## <a name="connecting-to-the-holographic-remoting-player"></a>連接到全像攝影遠端播放播放機

遵循您應用程式的指示，連接到全像攝影的遠端播放播放機。 您將需要輸入 HoloLens 裝置的 IP 位址，您可以在遠端播放程式的主畫面上看到它，如下所示：

![全像攝影遠端播放程式](images/holographicremotingplayer.png)

當您看到主畫面時，您會知道您沒有連線的應用程式。

請注意，全像攝影遠端連線**不會加密**。 您應該一律在您信任的安全 Wi-fi 連線上使用全像攝影遠端。

## <a name="quality-and-performance"></a>品質和效能

您的體驗品質和效能會因三個因素而有所不同：
* **您**正在執行的全像攝影體驗-呈現高解析度或高度詳細內容的應用程式，可能需要更快速的電腦或更快的無線連線。
* **您**的電腦硬體-您的電腦必須能夠在每秒60畫面上執行及編碼您的全像體驗。 針對圖形配接器，我們通常建議使用 GeForce GTX 970 或 AMD Radeon R9 290 或更高的品質。 同樣地，您的特定體驗可能需要較高或較低的卡片。
* **您的 wi-fi**連線-您的全像攝影體驗會透過 wi-fi 進行串流處理。 使用具有低擁塞的快速網路，將品質最大化。 使用透過 Ethernet 纜線（而非 Wi-fi）連線的電腦，也可以改善品質。

## <a name="diagnostics"></a>診斷

若要測量連線的品質，請在全像攝影遠端播放程式的主畫面上說「**啟用診斷**」。 啟用診斷時，在**HoloLens （第1代）** 上，應用程式會顯示：

* **FPS** -遠端播放者每秒接收和轉譯的轉譯框架平均數目。 理想的情況是 60 FPS。
* **延遲**-框架從您的電腦移至 HoloLens 所需的平均時間量。 越低越好。 這主要取決於您的 Wi-fi 網路。

在**HoloLens 2**上，應用程式會顯示：

![全像攝影遠端播放程式診斷](images/holographicremotingplayer-diag.png)

* **Render** -在上一秒中，遠端播放玩家呈現的畫面格數目。 請注意，這與透過網路抵達的畫面格數目無關（請參閱**影片畫面**）。 此外，會顯示呈現的框架之間最後一秒的平均/最大轉譯差異時間（以毫秒為單位）。

* **影片畫面**格-第一個顯示的數位會略過影片畫面，第二個是重複使用的影片畫面，而第三個是收到的影片畫面。 所有數位代表上一秒的計數。
    * ```Received frames```這是上一秒抵達的影片畫面格數目。 在正常情況下，這應該是60，但如果不是，則表示可能因為網路問題而捨棄任何框架，或遠端/遠端端不會產生具有預期速率的畫面。
    * ```Reused frames```這是在上一秒使用超過一次的影片畫面格計數。 比方說，如果影片畫面遲到了，播放程式的轉譯迴圈仍會轉譯框架，但必須*重複*使用它已經用於上一個畫面格的影片畫面。
    * ```Skipped frames```這是播放程式轉譯迴圈尚未使用的影片畫面計數。 比方說，網路抖動的效果可能會使影片畫面格抵達的效果不再平均分佈。 例如，如果有一些延遲，而其他人有時間抵達，其結果是在以60Hz 執行時，其不會再有16.66 毫秒的差異。 在播放程式轉譯迴圈的兩個刻度之間，可能會出現一個以上的框架。 在此情況下，播放程式會*略過*一或多個畫面，因為它應該會一律顯示最新收到的影片畫面格。

    >[!NOTE]
    >面對網路抖動時，略過和重複使用的框架通常會有相同的資訊。 相反地，如果您只看到略過的畫面格，這就是播放程式未達到其目標畫面播放速率的指標。 在此情況下，您應該留意診斷問題時的最大轉譯差異時間。

* **影片畫面差異**-過去一秒內接收的影片畫面之間的最小/最大差異。 如果網路抖動所造成的問題，此數目通常會與略過/重複使用的框架相互關聯。
* **延遲**-上一秒的平均週期（以毫秒為單位）。 在此內容中，這表示從 HoloLens 傳送姿勢/感應器資料到遠端/遠端端的時間，直到顯示 HoloLens 顯示器上該姿勢/遙測資料的影片畫面為止。
* 已**捨棄的影片框架**-上一秒已捨棄的影片畫面數，以及自從建立連接後的數目。 捨棄之影片畫面格的主要原因是影片畫面格未按順序抵達，因此必須捨棄，因為已經有較新的版本。 這類似于已*捨棄的框架*，但原因是在遠端堆疊中較低的層級。 只有在網路狀況不佳的情況下，才需要捨棄的影片畫面。



在主畫面上，您可以說「**停用診斷**」來關閉診斷。

## <a name="pc-system-requirements"></a>電腦系統需求
* 您的電腦**必須**執行 Windows 10 年度更新版或更新版本。
* 我們建議使用 GeForce GTX 970 或 AMD Radeon R9 290 或更好的圖形配接器。
* 我們建議您透過 ethernet 將電腦連線到您的網路，以減少無線躍點的數目。

## <a name="see-also"></a>另請參閱
* [HoloLens （第1代）：新增全像攝影遠端](add-holographic-remoting.md)
* [HoloLens 2：撰寫全像攝影遠端應用程式](holographic-remoting-create-host.md)
* [全像攝影遠端軟體授權條款](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隱私權聲明](https://go.microsoft.com/fwlink/?LinkId=521839)
