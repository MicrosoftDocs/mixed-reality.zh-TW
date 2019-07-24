---
title: HoloLens 研究模式
description: 使用 HoloLens 的 Research 模式, 應用程式可以存取金鑰裝置感應器串流 (深度、環境追蹤和 IR-反射率)。
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: 研究模式, cv, rs4, 電腦視覺, research, HoloLens
ms.openlocfilehash: e9a7683f8d582b459185066e74655e8f2b236db4
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829927"
---
# <a name="hololens-research-mode"></a>HoloLens 研究模式

> [!NOTE]
> 這項功能已新增為 HoloLens 的[Windows 10 2018 年4月更新](release-notes-april-2018.md)的一部分, 且在舊版中無法使用。

Research 模式是 HoloLens 的新功能, 可讓應用程式存取裝置上的重要感應器。 它們包括：
- 系統使用的四個環境追蹤攝影機, 用於地圖建立和標題追蹤。
- 兩個版本的深度相機資料–一個用於高頻率 (30 FPS) 近深度檢測, 通常用於手動追蹤, 另一個用於較低頻率 (1 FPS) 的深度感應, 目前用於空間對應,
- 有兩個版本的 IR 反射率串流, 由 HoloLens 用來計算深度, 但有價值, 因為這些影像會從 HoloLens 照亮, 而且會受到環境光線的適當影響。

![研究模式應用程式螢幕擷取畫面](images/sensor-stream-viewer.jpg)<br>
*測試應用程式的混合現實捕捉, 會顯示 Research 模式中提供的八個感應器串流*

## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>研究模式</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-using-research-mode"></a>使用研究模式之前

研究模式的命名良好: 它適用于學術和產業研究人員在電腦視覺和機器人領域中嘗試新構想。  研究模式不適用於將在企業中部署或可在 Microsoft Store 中使用的應用程式。 這是因為研究模式會降低裝置的安全性, 而且耗用的電池電力遠高於正常作業。 Microsoft 不會承諾在任何未來的裝置上支援此模式。 因此, 我們建議您使用它來開發和測試新的想法;不過, 您將無法廣泛部署使用研究模式的應用程式, 也無法保證它會繼續在未來的硬體上工作。

## <a name="enabling-research-mode"></a>啟用研究模式

Research 模式是開發人員模式的子模式。 您必須先在 設定 應用程式中啟用開發人員模式 (**設定 > 適用于開發人員的 更新 & 安全性 >** ):

1. 將 [使用開發人員功能] 設定為 [**開啟**]
2. 將 [啟用裝置入口網站] 設定為 [**開啟**]

然後使用連線到與 HoloLens 相同之 Wi-fi 網路的網頁瀏覽器, 流覽至 HoloLens 的 IP 位址 (透過 [**設定] > [網路 &] [網際網路] > [wi-fi > 硬體**內容]) 來取得。 這是[裝置入口網站](using-the-windows-device-portal.md), 您會在入口網站的 [系統] 區段中找到 [研究模式] 頁面:

![HoloLens 裝置入口網站的 [研究模式] 索引標籤](images/ResearchModeDevPortal.png)<br>
*HoloLens 裝置入口網站中的研究模式*

選取 [**允許存取感應器串流**] 之後, 您將需要重新開機 HoloLens。 您可以從裝置入口網站, 在頁面頂端的 [電源] 功能表項目底下執行此動作。

一旦您的裝置重新開機, 透過裝置入口網站載入的應用程式應該能夠存取研究模式串流。

## <a name="using-sensor-data-in-your-apps"></a>在您的應用程式中使用感應器資料

應用程式可以藉由以存取相片/視頻相機串流的相同方式, 開啟[媒體基礎](https://msdn.microsoft.com/library/windows/desktop/ms694197)串流來存取感應器串流資料。 

在研究模式下也可以使用適用于 HoloLens 開發的所有 Api。 特別是, 應用程式可以確切知道 HoloLens 在每個感應器框架捕獲時間的6DoF 空間。

範例應用程式會顯示如何存取各種研究模式串流、如何使用內建函式和 extrinsics, 以及如何記錄串流, 可在[HoloLensForCV GitHub](https://github.com/Microsoft/HoloLensForCV)存放庫中取得。

## <a name="known-issues"></a>已知問題

請參閱 HoloLensForCV 存放庫中的[問題追蹤](https://github.com/Microsoft/HololensForCV/issues)器。

## <a name="see-also"></a>另請參閱

* [Microsoft 媒體基礎](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [HoloLensForCV GitHub 存放庫](https://github.com/Microsoft/HoloLensForCV)
* [使用 Windows 裝置入口網站](using-the-windows-device-portal.md)
