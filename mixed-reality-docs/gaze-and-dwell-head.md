---
title: 頭部注視並佇留
description: 頭部注視並佇留輸入模型的概觀
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
keywords: Mixed Reality, 注視, 佇留, 互動, 設計
ms.openlocfilehash: 6d209d3cc91ceecb4b9feef2925f093288c9f8ac
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439309"
---
# <a name="head-gaze-and-dwell"></a>頭部注視並佇留

當手上拿著工具和組件時，手勢可以很繁瑣或不可能進行。 語音命令 (例如手勢) 在特定情境 (例如極度喧噪的情況) 中可能不大可靠。 此外，使用語音來控制電腦並不十分普遍，但的確可取得資料流！ 「頭部注視並佇留」提供最熟悉且容易掌握的機制，可在 HoloLens 上以抬頭和免持式運作。 此外，「頭部注視並佇留」 100% 可靠，完全不受雜訊干擾，而且在作業環境中也沒有靜音限制。

## <a name="scenarios"></a>案例

列印頭和停留擅長在某人的手中與其他工作忙碌的案例中，而且因為環境或社交條件約束，所以語音不是100% 可靠或無法使用。 穿戴 HoloLens 的人員在修理汽車引擎時覆疊參考資訊就是個不錯的範例。 他們的雙手忙著拿起工具，或在靠向引擎室時支撐其身體。 車庫空間很吵雜，充斥著工具的碰撞和唧唧聲，讓語音命令變得難以使用。 列印頭和停留可讓使用 HoloLens 的人安心地流覽其參考資料，而不會中斷工作流程。 

## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>輸入模型</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>頭部注視並佇留</td>
        <td>✔️ 建議使用</td>
        <td>✔️ 建議使用</td>
        <td>✔️ 建議使用</td>
    </tr>
</table>


## <a name="design-principles"></a>設計原則

**避免「注視武器」**

「頭部注視並佇留」需要直覺式視覺化回饋，但是太多回饋可能會引起焦慮。 回饋應協助使用者知道他們所定向的目標，但不會針對其意圖予以自動選取。 讀取文字、圖示和標籤需要額外的考量，在選取之前為人員提供吸收資訊的空間。
    
**搜尋 Goldilocks 速度**
    
佇留互動可根據瀏覽的影響而有不同的計時器 - 較多常用功能通常受益於更快速的填滿時間，而較多衍生性功能則可受益於較長的填滿時間。 使用填滿效果來顯示這些計時器時，填滿色彩的動畫曲線對於較快速填滿時間的感覺有正面影響。 應可慮讓使用者決定快速/中等/緩慢填滿速度覆寫。
    
**假設不是-yo 的效果**

溜溜球效應是當內容和「頭部注視並佇留」控制項的放置方式強迫人們要不斷地重複仰視和俯視時，可能出現的不舒適頭部移動模式。 例如，底部有 [中] 和 [停留] 按鈕的清單導覽，會引發一個迴圈，並顯示 [停留]、[查看結果]、[停留于]、[停止顯示] 等等。這個產生的模式不舒服，應避免將導覽控制項放在需要較少來回的集中式位置。 與效應相關的佇留按鈕放置方式，對於舒適度而言很重要。

<br>

---


## <a name="ux-guidelines-and-best-practices"></a>UX 指導方針和最佳作法

### <a name="target-sizes"></a>目標大小
  為了方便存取，頭眼和停留目標必須夠大，才能輕鬆查看，並在指定的時間在目標上保留一部穩定的標頭。 我們建議的最小目標大小為2度，以達到最舒適的體驗。 

### <a name="visual-feedback"></a>視覺回饋

使用放射狀填滿來表示佇留計時器時，從按鈕中心開始。 相較於不同按鈕上的所有不同方向，一致的回應比較不容易混淆。 

  * 有方向的互動 (例如，向上/向下/左/右瀏覽等) 可以打破此規則。 例如，Microsoft Dynamics 365 Guides 讓「下一頁/上一頁」成為左右填滿則屬例外狀況。
  * 在關閉按鈕等情境下，請考慮從外部反轉放射狀填滿。 按壓按鈕的反向感覺是可維護的良好視覺模式。 

### <a name="progressive-disclosure"></a>漸進式揭露

漸進式揭露表示只有盡可能詳細顯示與互動的每個階段相關。 對於佇留，這表示佇留目標會顯現於醒目提示 (例如，在清單控制項中)。

 ### <a name="oversized-targets"></a>過大的目標
佇留區域可大於非使用中的圖示，使其更容易使用，例如 Microsoft Dynamics 365 Guides 中的 [上一頁] 按鈕。

### <a name="prevent-flickering-with-delayed-feedback"></a>使用延遲回饋防止閃爍
在開始視覺化回饋前使用短暫延遲，可避免有人經過佇留目標時發生閃爍。
* 對於經常互動的按鈕，請讓延遲變得非常短，讓應用程式感覺為被動。
* 對於不常進行互動的按鈕，較長的延遲可能會適當地避免介面感覺 twitchy。


<br>

---

## <a name="ui-patterns"></a>UI 模式

### <a name="high-frequency-buttons"></a>高頻率按鈕

:::row:::
    :::column:::
        高頻率按鈕是常用於整個應用程式的按鈕。 Microsoft Dynamics 365 Guides 中的下一頁和上一頁按鈕都是不錯的範例。<br>
        <br>
        **相關**<br>
  * 高頻率的按鈕應該很大，使用 head
  * 保持近乎眼的高度，以避免人體工學。<br>
        <br>
*影像： Microsoft Dynamics 365 guide [下一步] 按鈕*
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 指南 [下一步] 按鈕](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a>低頻率按鈕
低頻率按鈕是整個應用程式中不會定期互動的按鈕。 可存取 [設定] 功能表的按鈕，或可清除所有工作的按鈕都是不錯的範例。

* 嘗試讓這些按鈕不在常用的頭部注視路徑中，以免意外啟動。 

<br>

---

### <a name="confirmations"></a>確認

:::row:::
    :::column:::
        當某個動作有重大影響時 (例如收費、刪除工作或開始長時間處理)，最好確認個人要選取按鈕。<br>
        <br>
        **相關**<br>
  * 在主要按鈕上顯示選取醒目提示。
  * 與選取醒目提示同時顯示佇留目標。
  * 對於次要按鈕，顯示頭部注視的佇留目標。<br>
        <br>
*影像： Microsoft Dynamics 365 指南確認對話方塊*
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 指南確認對話方塊](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a>切換按鈕
切換按鈕需要一些微妙的邏輯，才能正常運作。 當人員佇留在切換按鈕並啟動它時，他們需要結束按鈕，然後回頭重新啟動佇留邏輯。 切換按鈕會有清楚的作用與非作用中狀態很重要。 

<br>

---

### <a name="list-views"></a>清單檢視

:::row:::
    :::column:::
        清單視圖會針對 head 注視和停留輸入呈現特定挑戰。 人們需要能夠掃描內容，而不覺得必須偷偷摸摸地環顧佇留目標。<br>
        <br>
**相關**<br>
  * 當 head gazed 時，會將整個資料列醒目提示，但不會開始停留，除非您在特定的停留目標上出現 head 注視。
  * 只有在資料列反白顯示時，才會顯示停留目標，以在視覺效果雜訊上減少。
  * 請清楚，並與停留目標的位置保持一致。
  * 不要同時顯示所有的停留目標，以避免重複的 UI。
  * 盡可能重複使用相同的模式，以建立 UX 的熟悉度。<br>
        <br>
*映射： Microsoft Dynamics 365 指南清單*
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 指南清單](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a>請參閱
* [注視和認可](gaze-and-commit.md)
* [直接操作](direct-manipulation.md)
* [實習手勢](gaze-and-commit.md#composite-gestures)
* [實際操作和認可](point-and-commit.md)
* [本能互動](interaction-fundamentals.md)
* [語音輸入](voice-input.md)
