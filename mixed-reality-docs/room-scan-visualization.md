---
title: 聊天室掃描視覺效果
description: 需要空間的對應資料的應用程式依賴自動收集一段時間的這項資料的裝置，並以使用者的工作階段之間探索其環境與作用中裝置。
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，應用程式模式、 設計、 HoloLens、 聊天室掃描，空間的對應，介面重構，網格
ms.openlocfilehash: 09df4464ea4dac01dfad637886b07b861f468d4d
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829910"
---
# <a name="room-scan-visualization"></a>聊天室掃描視覺效果

需要空間的對應資料的應用程式依賴自動收集一段時間的這項資料的裝置，並以使用者的工作階段之間探索其環境與作用中裝置。 完整性和品質的這項資料取決於許多因素，包括使用者已完成探勘數量、 瀏覽過多少時間，以及是否物件，例如 furniture 和機門已因為裝置掃描區域。

若要確保有用空間的對應資料，應用程式開發人員會有數個選項：
* 依賴功能可能已收集。 一開始這項資料可能會不完整。
* 要求使用者使用 bloom 筆勢來取得 Windows Mixed Reality 家用，然後瀏覽他們想要使用體驗的區域。 若要確認所有必要的區域已知的裝置，他們可以使用空中點選。
* 建置自訂的探索體驗，在他們自己的應用程式中。

請注意，在所有這些情況下在探索期間蒐集的實際資料儲存系統應用程式不需要執行這項操作。

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
        <td><a href="immersive-headset-hardware-details.md"><strong>沈浸式耳機</strong></a></td>
    </tr>
     <tr>
        <td>聊天室掃描視覺效果</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a>建置自訂的掃描體驗

應用程式可能會決定要分析空間的對應資料，判斷他們是否想讓使用者執行其他步驟，以改善其完整性和品質經驗的開頭。 如果分析指出應該改善品質，開發人員應該提供視覺效果，以指出世界上的覆疊：
* 在使用者附近的總磁碟區中有多少必須能夠體驗的一部分
* 使用者應該前往改善資料

使用者不知道如何成為 「 良好 」 的掃描。 他們需要顯示或告知要尋找的如果它們就必須評估掃描 – 扁平度，實際的牆、 從距離等等。開發人員應該實作的意見反應迴圈，其中包含重新整理掃描或瀏覽階段期間的空間的對應資料。

在許多情況下，可能是最理想的做法，告訴使用者他們需要執行 （例如查看最高限度，查看 furniture 後面），以取得必要的掃描品質。

## <a name="cached-versus-continuous-spatial-mapping"></a>快取與連續空間對應

空間對應的資料是資料來源的應用程式可以使用最高負載。 若要避免效能問題，例如畫面或間斷的情形，這項資料的耗用量必須小心執行。

作用中的掃描，體驗期間可以幫助或不利，開發人員必須決定要使用哪個方法經驗為基礎。

### <a name="cached-spatial-mapping"></a>快取空間的對應

如果快取空間的對應，是應用程式，通常空間的對應資料的快照，並體驗的持續期間使用此快照集。

**權益**
* 額外負荷降低系統上體驗大幅的乘冪，熱執行前置及 cpu 效能提升時。
* 主要的體驗，因為它不會因空間資料變更的簡單實作。
* 單一成本物理、 圖形和其他用途的空間資料的任何後續處理上一次。

**缺點**
* 快取的資料不會反映的真實世界物件或人員的移動。 例如 應用程式可能會考慮機門開啟實際上現在關閉時。
* 可能有更多應用程式的記憶體以維持資料的快取的版本。

理想的情況下，這個方法是受控制的環境或資料表頂端遊戲。

### <a name="continuous-spatial-mapping"></a>連續空間對應

特定的應用程式可能會依賴上會繼續掃描以重新整理空間對應的資料。

**權益**
* 您不需要建置個別掃描或瀏覽體驗預先在您的應用程式。
* 遊戲時，可以反映的真實世界物件移動但仍會有一些延遲。

**缺點**
* 主要的經驗的實作中較高的複雜性。
* 如圖形或物理做的變更需要以累加方式擷取這些系統的額外處理的潛在的額外負荷。
* 較高的電源、 散熱和 CPU 衝擊。

理想的情況下，這個方法會是其中一個互動移動物件，例如地板上的磁碟機可能會想要正確碰到取決於它是否已開啟或關閉門全像攝影版的汽車中有到全像投影。

## <a name="see-also"></a>另請參閱
* [空間對應設計](spatial-mapping-design.md)
* [座標系統](coordinate-systems.md)
* [空間音效設計](spatial-sound-design.md)
