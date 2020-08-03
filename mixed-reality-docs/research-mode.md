---
title: HoloLens 研究模式
description: 使用 HoloLens 的 Research 模式，應用程式可以存取金鑰裝置感應器串流（深度、環境追蹤和 IR-反射率）。
author: hferrone
ms.author: v-haferr
ms.date: 07/31/2020
ms.topic: article
keywords: 研究模式，cv，rs4，電腦視覺，research，HoloLens，HoloLens 2
ms.openlocfilehash: dd49186d1218b6a6a6c9a8d5943159daad3bcefb
ms.sourcegitcommit: 36316e2658d3dfa804d798b9f4fb2f9186052144
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2020
ms.locfileid: "87507692"
---
# <a name="hololens-research-mode"></a>HoloLens 研究模式

Research 模式是在第1代 HoloLens 中引進，可讓您存取裝置上的主要感應器，特別是針對不適合部署的研究應用程式。  HoloLens 2 的研究模式保留 HoloLens 1 的功能，並新增額外串流的存取權：

* **可見的光線環境追蹤攝影機**-系統用於 head 追蹤和地圖建築物的灰階相機。
* **深度相機**–以兩種模式運作：  
    + 用於手動追蹤的 AHAT、高頻率（45 FPS）近深度檢測。 與第1版的簡短擲回模式不同的是，AHAT 提供的虛擬深度與1個計量以外的階段換行。 
    + [空間對應](spatial-mapping.md)所使用的長時間擲回、低頻率（1-5 FPS）深度感應

* **兩個版本的 IR 反射率串流**-由 HoloLens 用來計算深度。 這些映射是由紅外線所照亮，並不會受到環境可見光線的影響。

如果您使用 HoloLens 2，您也可以存取下列其他輸入：

* **加速**計–系統用來判斷沿著 X、Y 和 Z 軸和引力的線性加速。
* **Gyro** –由系統用來判斷旋轉。
* **磁力計**–由系統用來估計絕對方向。

> [!IMPORTANT]
> Research 模式目前為公開預覽狀態。 HoloLens 2 範例、教學課程和完整 API 檔將在[ECCV 2020](https://eccv2020.eu/
 )的 Research 模式 Git 存放庫中提供。

![研究模式應用程式螢幕擷取畫面](images/sensor-stream-viewer.jpg)<br>
*測試應用程式的混合現實捕捉，會顯示 Research 模式中提供的八個感應器串流*

## <a name="usage"></a>使用量

研究模式是針對在電腦視覺和機器人領域中探索新想法的學術和產業研究人員所設計。  它不適用於部署在企業環境中的應用程式，或透過 Microsoft Store 或其他散發通道提供。

此外，Microsoft 不保證未來的硬體或作業系統更新將會支援研究模式或對等功能。 不過，這不應該阻止您使用它來開發和測試新的想法！

## <a name="security-and-performance"></a>安全性與效能

請注意，啟用 Research 模式比在正常情況下使用 HoloLens 2 的電池電力更高。 即使使用研究模式功能的應用程式不在執行中，也是如此。  啟用此模式也可以降低裝置的整體安全性，因為應用程式可能會誤用感應器資料。  您可以在[HoloLens 安全性常見問題](https://docs.microsoft.com/hololens/hololens-faq-security)中找到更多有關裝置安全性的資訊。  

## <a name="device-support"></a>裝置支援
<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens (第 1 代)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></td>
    </tr>
     <tr>
        <td>Head 追蹤攝影機</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>深度 & IR 相機</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>加速計</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>迴轉儀</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>磁力計</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-1st-gen-and-hololens-2"></a>啟用研究模式（HoloLens 第1代和 HoloLens 2）

Research 模式是「開發人員模式」的延伸模組。 開始之前，必須先啟用裝置的開發人員功能，才能存取 Research 模式設定： 

* 開啟 [**開始] 功能表 > 設定**]，然後選取 [**更新**]。
* **為開發人員**選取並啟用**開發人員模式**。
* 向下捲動並啟用**裝置入口網站**。

啟用開發人員功能之後，請[連接到裝置入口網站](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens)以啟用研究模式功能：

* 前往**裝置入口網站**中的 [**系統 > 研究模式]** 。
* 選取 [**允許存取感應器串流**]。
* 從頁面頂端的 [**電源**] 功能表項目重新開機裝置。

一旦您重新開機裝置，透過**裝置入口網站**載入的應用程式就可以存取研究模式串流。

![HoloLens 裝置入口網站的 [研究模式] 索引標籤](images/ResearchModeDevPortal.png)<br>
*HoloLens 裝置入口網站中的 Research 強制回應視窗*

> [!IMPORTANT]
> 從組建19041.1356 開始提供 HoloLens 2 的研究模式。 如果您需要在先前的組建中存取，請註冊我們的[Insider preview](https://docs.microsoft.com/hololens/hololens-insider)計畫。

### <a name="using-sensor-data-in-your-apps"></a>在您的應用程式中使用感應器資料

應用程式可以使用透過[媒體基礎](https://msdn.microsoft.com/library/windows/desktop/ms694197)存取相片和攝影機串流的相同方式來存取感應器串流資料。 

所有適用于 HoloLens 開發的 Api 也會以 Research 模式提供。 特別是，應用程式會確切知道 HoloLens 在每個感應器框架捕獲時間的6DoF 空間。

您可以找到如何存取各種研究模式串流的範例應用程式、如何使用[內建函式和 extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)，以及如何在[HoloLensForCV GitHub](https://github.com/Microsoft/HoloLensForCV)存放庫存放庫中記錄串流。

 > [!NOTE]
 > 目前，HoloLensForCV 範例不適用於 HoloLens 2。

## <a name="support"></a>支援

請使用 HoloLensForCV 存放庫中的[問題追蹤](https://github.com/Microsoft/HololensForCV/issues)器來張貼意見反應，並追蹤已知的問題。

## <a name="see-also"></a>請參閱

* [Microsoft 媒體基礎](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [HoloLensForCV GitHub 存放庫](https://github.com/Microsoft/HoloLensForCV)
* [使用 Windows 裝置入口網站](using-the-windows-device-portal.md)
