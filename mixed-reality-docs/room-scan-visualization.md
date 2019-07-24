---
title: 房間掃描視覺效果
description: 需要空間對應資料的應用程式會依賴裝置, 在使用者探索其在使用中裝置的環境時, 于一段時間內自動收集此資料。
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 應用程式模式, 設計, HoloLens, 房間掃描, 空間對應, 表面重建, 網格
ms.openlocfilehash: 09df4464ea4dac01dfad637886b07b861f468d4d
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829910"
---
# <a name="room-scan-visualization"></a>房間掃描視覺效果

需要空間對應資料的應用程式會依賴裝置, 在使用者探索其在使用中裝置的環境時, 于一段時間內自動收集此資料。 此資料的完整性和品質取決於數個因素, 包括使用者已完成的探索量、流覽後經過的時間, 以及設備 (例如傢俱和門) 在掃描區域之後是否已移動。

為了確保有用的空間對應資料, 應用程式開發人員有數個選項:
* 依賴可能已收集的內容。 此資料一開始可能不完整。
* 要求使用者使用 bloom 手勢來進入 Windows Mixed Reality home, 然後探索他們想要用於體驗的領域。 他們可以使用 [按一下] 來確認裝置知道所有必要的區域。
* 在自己的應用程式中建立自訂探索體驗。

請注意, 在這些情況下, 探索期間所收集的實際資料會由系統儲存, 而應用程式不需要這麼做。

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
        <td>房間掃描視覺效果</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a>建立自訂掃描體驗

應用程式可能會決定在體驗開始時分析空間對應資料, 以判斷他們是否想要讓使用者執行額外的步驟來改善其完整性和品質。 如果分析指出應該改善品質, 開發人員應該提供視覺效果以在世界上重迭, 以指出:
* 使用者鄰近範圍中的總數量必須是經驗的一部分
* 使用者應該前往哪裡改善資料

使用者不知道什麼會進行「良好」掃描。 如果要求評估掃描– flatness、與實際牆的距離等等, 則需要顯示或告訴您要尋找的內容。開發人員應執行意見反應迴圈, 其中包括在掃描或流覽階段重新整理空間對應資料。

在許多情況下, 最好告訴使用者需要執行的動作 (例如, 查看 [傢俱] 的上限), 以便取得所需的掃描品質。

## <a name="cached-versus-continuous-spatial-mapping"></a>快取與連續空間對應

空間對應資料是最繁重的資料來源應用程式可使用的權數。 若要避免效能問題 (例如, 已卸載的框架或間斷情形), 應該小心地取用此資料。

在體驗期間進行主動掃描可能會有好處或不利, 而開發人員必須根據經驗決定要使用的方法。

### <a name="cached-spatial-mapping"></a>快取的空間對應

在快取空間對應的情況下, 應用程式通常會取得空間對應資料的快照, 並在體驗期間使用此快照集。

**權益**
* 降低系統的額外負荷, 同時體驗會大幅提升電力、冷卻和 cpu 效能。
* 較簡單的主要體驗執行, 因為空間資料的變更不會中斷。
* 針對物理、圖形和其他用途, 針對空間資料的任何後置處理進行單一時間成本。

**缺陷**
* 實際的物件或人員的移動不會反映在快取的資料上。 例如 應用程式在實際關閉時, 可能會將門視為已開啟。
* 可能會有更多應用程式記憶體來維護快取的資料版本。

這個方法有一個不錯的例子, 就是受控制的環境或資料表最熱門的遊戲。

### <a name="continuous-spatial-mapping"></a>連續空間對應

某些應用程式可能會依賴繼續掃描以重新整理空間對應資料。

**權益**
* 您不需要在應用程式中預先建立個別的掃描或探索體驗。
* 現實世界物件的移動可以由遊戲反映, 但有一些延遲。

**缺陷**
* 主要體驗的執行複雜度較高。
* 因為需要以累加方式內嵌這些系統的變更, 所以圖形或物理的額外處理可能會產生額外負荷。
* 較高的電源、熱和 CPU 的影響。

這種方法的理想情況是, 其中的全息影像應該與移動物件互動, 例如, 地面驅動的全像攝影車, 可能會想要根據它是開啟還是關閉來正確地增加到門中。

## <a name="see-also"></a>另請參閱
* [空間對應設計](spatial-mapping-design.md)
* [座標系統](coordinate-systems.md)
* [空間音效設計](spatial-sound-design.md)
