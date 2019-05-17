---
title: Head 視線和詳述
description: Head 視線和詳述輸入模型的概觀
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境，視線、 詳述、 互動，設計
ms.openlocfilehash: 05457b35c13422c8aa6663bdf52a489a4f5afdaa
ms.sourcegitcommit: b5bad4eeb5cdd0c2a7b639442656c306e8b5853b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2019
ms.locfileid: "65813986"
---
# <a name="head-gaze-and-dwell"></a>Head 視線和詳述

指針會佔用工具和組件，當筆勢可以很繁瑣或是不可能。 語音命令，例如筆勢，可以在特定內容中，例如在極大的情況下不可靠。 此外，使用語音來控制電腦不普遍常見，但它的確取得資料流 ！ Head 視線和詳述提供 heads-up 和免持聽筒 HoloLens 上工作的最熟悉且容易主要機制。 此外，head 視線，並詳述為 100%可靠與雜訊干擾或無回應中的條件約束的作業環境無關。

## <a name="scenarios"></a>案例

Head 視線和詳述的過人之處的人手正忙於處理其他工作，並語音未達到 100%可靠或可用由於環境或社交條件約束。 例如，穿著 HoloLens 重疊時修復汽車引擎的參考資訊的人員。 其指針是忙著處理工具或支援其主體，因為他們了解到引擎區間。 車庫空間是大了，常數 banging 和熱烈的工具，讓語音命令的變得困難。 Head 視線和詳述允許其工作流程的人員有自信地瀏覽其參考資料，而不需要 interupting HoloLens。 

## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>輸入的模型</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沈浸式耳機</strong></a></td>
    </tr>
     <tr>
        <td>Head 視線和詳述</td>
        <td>建議的 ✔️</td>
        <td>建議的 ✔️</td>
        <td>建議的 ✔️</td>
    </tr>
</table>

## <a name="goals"></a>目標

提供一種機制，完全免持聽筒互動，而不需使用語音。

## <a name="design-principles"></a>設計原則

1. 避免 「 視線作為武器 」

    Head 視線和詳述需要是直覺式的視覺回饋，但是太多的意見反應可以引發前。 意見反應應該協助使用者，知道什麼它們的目標，但不是自動選取它對其意圖。 讀取文字、 圖示和標籤需要額外的考量，以提供人員聊天室吸收之前選取的資訊。
    
2. 搜尋 Goldilocks 速度
    
    詳述的互動可以有不同的計時器為基礎的導覽的影響-較常使用的函式將通常受益於更快速的填滿時間，而更衍生性損害函式可能會受益於較長的填滿時間。 使用時填滿效果以顯示這些計時器，填滿色彩的動畫曲線可以正面影響更快速的填滿時間能的一目了然。 應該採取的考量，以讓使用者決定從快速/medium/緩慢填滿速度覆寫。
    
3. 假設 no-no 爬昇效果

    爬昇效果是磁頭移動時的內容和標頭視線詳述的控制項位置會強制要不斷地尋找重複向上和向下的人，可能會出現，只要不模式。 比方說，使用底部的 [標頭視線及詳述] 按鈕清單導覽會引發迴圈的-外觀下會探討，請在查詢結果，請查看要探討等。這個產生的模式時感到不舒服，及應避免將導覽控制項放在上一步往來需要較少的集中位置。 放置相對於其效果詳述按鈕變得很重要的緩和。

## <a name="ux-guidelines-and-best-practices"></a>UX 指導方針和最佳作法

### <a name="target-sizes"></a>目標大小
  若要更容易存取，head 視線和目標必須大到足以 comforatably 目標會探討並按住其中的標頭 stabily 目標規定的時間。 建議的最小目標大小的 2 個角度，以達到最熟悉的體驗。 

### <a name="visual-feedback"></a>視覺化回饋

當使用放射狀填滿代表詳述計時器，開始從按鈕的中心。 一致的回應是不同的按鈕上的所有不同方向比不容易產生混淆。 

  * 此規則可以中斷雖然方向互動 （例如，瀏覽向上/向下/左/右，等等）。 比方說，在下一步/背面的例外狀況的 Microsoft Dynamics 365 指南會停留右邊會填滿。
  * 請考慮反轉放射狀填滿從外部，適合進行關閉切換按鈕。 按下按鈕反掌控是維護良好的視覺化模式。 

### <a name="progressive-disclosure"></a>漸進式揭露

漸進式揭露表示只顯示盡可能詳細互動的每個階段無關。 詳述，這表示詳述目標介紹反白顯示 （例如，在清單控制項）。

 ### <a name="oversized-targets"></a>過大的目標
詳述區域可能大於非使用中的圖示，以讓它更容易使用，例如 Microsoft Dynamics 365 指南中的 [上一頁] 按鈕。

### <a name="prevent-flickering-with-delayed-feedback"></a>避免延遲的意見反應的閃爍
使用開始視覺化回應之前的短暫的延遲，可避免閃爍有人經過詳述目標時。
* 讓應用程式感覺反應式經常使用的按鈕 inteacted，保留很短的延遲。
* Infrequenctly 互動的按鈕更長的延遲可能 approprate 以避免覺得 twitchy 的介面。

## <a name="ui-patterns"></a>UI 模式

### <a name="high-frequency-buttons"></a>高頻率按鈕
![Microsoft Dynamics 365 指南下一步 按鈕](images/GuideNextButton.png "Microsoft Dynamics 365 指南下一步 按鈕")高頻率餂鈕蒻通常用整個應用程式。 良好的範例，這些是 Microsoft Dynamics 365 指南中的 下一步 和上一步 按鈕。

高頻率按鈕應該...
* 會比較容易遇到 head 視線較大的按鈕，
* 保持眼睛高度，以避免工學就附近。

### <a name="low-frequency-buttons"></a>低頻率按鈕
低頻率餂鈕蒻，不或與之互動，定期整個應用程式。 按鈕可存取 [設定] 功能表中或按鈕即可清除所有的工作，可能是不錯的範例。

* 嘗試將保留不頻繁的 head 視線路徑，以避免意外啟動妨礙這些按鈕。 

### <a name="confirmations"></a>確認
![Microsoft Dynamics 365 指南確認對話方塊](images/GuidesConfirmation.png "Microsoft Dynamics 365 指南確認對話方塊")

當動作有重大影響，例如收費 money、 刪除工作，或從較長的處理序中，最好確認個人要選取按鈕。 Head 視線和詳述有 Ui 會有一些模式和確認對話方塊的考量：

  * 顯示主要按鈕的選取項目反白顯示。
  * 顯示與選取項目醒目提示同時探討目標。
  * 次要的按鈕，會顯示在標頭視線詳述目標。
        
### <a name="toggle-buttons"></a>切換按鈕
切換按鈕都需要一些微妙的邏輯，才能正常運作。 當個人埋在切換按鈕和在職員工它時，他們就需要結束按鈕，然後再回頭重新啟動詳述邏輯。 很重要，可切換按鈕就會有清楚的作用與非作用中狀態。 

### <a name="list-views"></a>清單檢視
![Microsoft Dynamics 365 指南確認對話方塊](images/GuidesListView.png "Microsoft Dynamics 365 指南確認對話方塊")清單檢視呈現 head 視線的特定挑戰，並探討輸入。 人員需要能夠掃描內容而有 tiptoe 周圍詳述目標。 

設計清單檢視的一些秘訣：
* 具有標頭 gazed，但不開始詳述，head 視線除非特定詳述目標上時反白顯示的整個資料列。
* 若要減少視覺干擾也會反白顯示資料列時，只顯示詳述目標。
* 是清楚且一致的詳述目標位置。
* 不會顯示所有會探討目標一次，以避免重複的 UI
* 重新建立 UX 熟悉盡可能經常使用相同的模式
 
 ## <a name="see-also"></a>另請參閱
* [直接操作](direct-manipulation.md)
* [指向和行動](point-and-commit.md)
* [互動基本概念](interaction-fundamentals.md)
* [頭部目光和行動](gaze-and-commit.md)
* [目光和語音](voice-design.md)
