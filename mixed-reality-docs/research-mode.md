---
title: HoloLens 研究模式
description: 使用 HoloLens 的 Research 模式，應用程式可以存取金鑰裝置感應器串流（深度、環境追蹤和 IR-反射率）。
author: hferrone
ms.author: v-haferr
ms.date: 05/03/2018
ms.topic: article
keywords: 研究模式，cv，rs4，電腦視覺，research，HoloLens，HoloLens 2
ms.openlocfilehash: ec6f7b73a1f25932f10c10a7f0daaf78e536c0c4
ms.sourcegitcommit: 7f50210b71a65631fd1bc3fdb215064e0db34333
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84533100"
---
# <a name="hololens-research-mode"></a>HoloLens 研究模式

## <a name="overview"></a>概觀

Research 模式是在第1代 HoloLens 中引進，可讓您存取裝置上的主要感應器，特別是針對不適合部署的研究應用程式。 您現在可以從下列輸入收集資料：

* **可見的光線環境追蹤攝影機**-供系統用來進行頭追蹤和地圖建築物。
* **深度相機**–以兩種模式運作：  
    + 短期擲回、高頻率（30 FPS）用於[手動追蹤](interaction-fundamentals.md)的近深度檢測
    + [空間對應](spatial-mapping.md)所使用的長時間擲回、低頻率（1-5 FPS）深度感應
* **兩個版本的 IR 反射率串流**-由 HoloLens 用來計算深度。 這些映射是由紅外線所照亮，並不會受到環境可見光線的影響。

如果您使用 HoloLens 2，您也可以存取下列輸入：

* **加速**計–系統用來判斷沿著 X、Y 和 Z 軸和引力的線性加速。
* **Gyro** –由系統用來判斷旋轉。
* **磁力計**–由系統用來估計絕對方向。

![研究模式應用程式螢幕擷取畫面](images/sensor-stream-viewer.jpg)<br>
*測試應用程式的混合現實捕捉，會顯示 Research 模式中提供的八個感應器串流*

> [!NOTE]
> Research 模式功能已新增為 HoloLens 的[Windows 10 2018 年4月更新](release-notes-april-2018.md)的一部分，且在舊版中無法使用。

## <a name="usage"></a>使用方式

研究模式是針對在電腦視覺和機器人領域中探索新想法的學術和產業研究人員所設計。  它不適用於部署在企業環境中的應用程式，或透過 Microsoft Store 或其他散發通道提供。

此外，Microsoft 不保證未來的硬體或作業系統更新將會支援研究模式或對等功能。 不過，這不應該阻止您使用它來開發和測試新的想法！

## <a name="security-and-performance"></a>安全性與效能

請注意，啟用 research 模式比在正常情況下使用 HoloLens 2 的電池電力更高。 即使使用研究模式功能的應用程式不在執行中，也是如此。  啟用此模式也可以降低裝置的整體安全性，因為應用程式可能會誤用感應器資料。  您可以在[HoloLens 安全性常見問題](https://docs.microsoft.com/hololens/hololens-faq-security)中找到更多有關裝置安全性的資訊。  


## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    <!-- <col width="33%" /> -->
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens 第1代</strong></a></td>
        <!-- <td><a href="hololens2-hardware.md"><strong>HoloLens 2</strong></a></td> -->
    </tr>
     <tr>
        <td>Head 追蹤攝影機</td>
        <td>✔️</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>深度 & IR 相機</td>
        <td>✔️</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>加速計</td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>迴轉儀</td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>磁力計</td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
</table>

> [!IMPORTANT]
> HoloLens 2 的 Research 模式支援預計會在2020年7月提供公開預覽，並將包含上述所有功能。 請回來查看以取得詳細資訊。 

## <a name="enabling-research-mode"></a>啟用研究模式

Research 模式是「開發人員模式」的延伸模組。 開始之前，必須先啟用裝置的開發人員功能，才能存取 research 模式設定： 

* 開啟 [**開始] 功能表 > 設定**]，然後選取 [**更新**]。
* **為開發人員**選取並啟用**開發人員模式**。
* 向下滾動並啟用 [**裝置入口網站**]。

啟用開發人員功能之後，請[連接到裝置入口網站](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens)以啟用研究模式功能。

在*HoloLens 第1代*上：

* 前往**裝置入口網站**中的 [**系統 > 研究模式]** 。
* 選取 [**允許存取感應器串流**]。
* 從頁面頂端的 [**電源**] 功能表項目重新開機裝置。

一旦您重新開機裝置，透過**裝置入口網站**載入的應用程式就可以存取研究模式串流。

![HoloLens 裝置入口網站的 [研究模式] 索引標籤](images/ResearchModeDevPortal.png)<br>
*HoloLens 裝置入口網站中的 Research 強制回應視窗*

## <a name="using-sensor-data-in-your-apps"></a>在您的應用程式中使用感應器資料

*HoloLens 第1代*

應用程式可以使用透過[媒體基礎](https://msdn.microsoft.com/library/windows/desktop/ms694197)存取相片和攝影機串流的相同方式來存取感應器串流資料。 

所有適用于 HoloLens 開發的 Api 也會以 Research 模式提供。 特別是，應用程式會確切知道 HoloLens 在每個感應器框架捕獲時間的6DoF 空間。

您可以找到如何存取各種研究模式串流的範例應用程式、如何使用[內建函式和 extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)，以及如何在[HoloLensForCV GitHub](https://github.com/Microsoft/HoloLensForCV)存放庫存放庫中記錄串流。

 > [!NOTE]
 > 目前，HoloLensForCV 範例不適用於 HoloLens 2。

## <a name="known-issues"></a>已知問題

您可以使用 HoloLensForCV 存放庫中的[問題追蹤](https://github.com/Microsoft/HololensForCV/issues)程式來遵循已知問題。

## <a name="see-also"></a>另請參閱

* [Microsoft 媒體基礎](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [HoloLensForCV GitHub 存放庫](https://github.com/Microsoft/HoloLensForCV)
* [使用 Windows 裝置入口網站](using-the-windows-device-portal.md)
