---
title: 頭部注視並佇留
description: 頭部注視並佇留輸入模型的概觀
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 注視, 佇留, 互動, 設計
ms.openlocfilehash: 70b25949380679d2edc81b07ab54f24fa20e3f3d
ms.sourcegitcommit: 9b6949d7cd2e67e6bde9b32aebeaeea325baa6c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66516009"
---
# <a name="head-gaze-and-dwell"></a>頭部注視並佇留

當手上拿著工具和組件時，手勢可以很繁瑣或不可能進行。 語音命令 (例如手勢) 在特定情境 (例如極度喧噪的情況) 中可能不大可靠。 此外，使用語音來控制電腦並不十分普遍，但的確可取得資料流！ 「頭部注視並佇留」提供最熟悉且容易掌握的機制，可在 HoloLens 上以抬頭和免持式運作。 此外，「頭部注視並佇留」 100% 可靠，完全不受雜訊干擾，而且在作業環境中也沒有靜音限制。

## <a name="scenarios"></a>案例

當人員的雙手正忙於處理其他工作時，「頭部注視並佇留」十分出色，且由於環境或社交限制，語音並未達到 100% 可靠或可用。 穿戴 HoloLens 的人員在修理汽車引擎時覆疊參考資訊就是個不錯的範例。 他們的雙手忙著拿起工具，或在靠向引擎室時支撐其身體。 車庫空間很吵雜，充斥著工具的碰撞和唧唧聲，讓語音命令變得難以使用。 「頭部注視並佇留」可讓穿戴 HoloLens 的人員自信地瀏覽其參考資料，而不需中斷其工作流程。 

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
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>頭部注視並佇留</td>
        <td>✔️ 建議使用</td>
        <td>✔️ 建議使用</td>
        <td>✔️ 建議使用</td>
    </tr>
</table>

## <a name="goals"></a>目標

不需使用語音，提供完全免持式互動的機制。

## <a name="design-principles"></a>設計原則

1. 避免「使用注視作為手段」

    「頭部注視並佇留」需要直覺式視覺化回饋，但是太多回饋可能會引起焦慮。 回饋應協助使用者知道他們所定向的目標，但不會針對其意圖予以自動選取。 讀取文字、圖示和標籤需要額外的考量，在選取之前為人員提供吸收資訊的空間。
    
2. 追求 Goldilocks 速度
    
    佇留互動可根據瀏覽的影響而有不同的計時器 - 較多常用功能通常受益於更快速的填滿時間，而較多衍生性功能則可受益於較長的填滿時間。 使用填滿效果來顯示這些計時器時，填滿色彩的動畫曲線對於較快速填滿時間的感覺有正面影響。 應可慮讓使用者決定快速/中等/緩慢填滿速度覆寫。
    
3. Say no-no to yo-yo 效應

    溜溜球效應是當內容和「頭部注視並佇留」控制項的放置方式強迫人們要不斷地重複仰視和俯視時，可能出現的不舒適頭部移動模式。 比方說，使用底部的「頭部注視並佇留」按鈕進行清單瀏覽會引發以下迴圈：俯視佇留、仰視結果、俯視佇留等。所產生的這個模式並不舒適，應藉由將瀏覽控制項放在需要較少往返的集中位置加以避免。 與效應相關的佇留按鈕放置方式，對於舒適度而言很重要。

## <a name="ux-guidelines-and-best-practices"></a>UX 指導方針和最佳作法

### <a name="target-sizes"></a>目標大小
  為了要更容易存取，「頭部注視並佇留」目標必須大到足以舒適地定向，而且將頭部穩定地朝向目標並持續一段規定的時間。 建議的最小目標大小為 2 度，可達到最熟悉的舒適體驗。 

### <a name="visual-feedback"></a>視覺化回饋

使用放射狀填滿來表示佇留計時器時，從按鈕中心開始。 相較於不同按鈕上的所有不同方向，一致的回應比較不容易混淆。 

  * 有方向的互動 (例如，向上/向下/左/右瀏覽等) 可以打破此規則。 例如，Microsoft Dynamics 365 Guides 讓「下一頁/上一頁」成為左右填滿則屬例外狀況。
  * 在關閉按鈕等情境下，請考慮從外部反轉放射狀填滿。 按壓按鈕的反向感覺是可維護的良好視覺模式。 

### <a name="progressive-disclosure"></a>漸進式揭露

漸進式揭露表示只有盡可能詳細顯示與互動的每個階段相關。 對於佇留，這表示佇留目標會顯現於醒目提示 (例如，在清單控制項中)。

 ### <a name="oversized-targets"></a>過大的目標
佇留區域可大於非使用中的圖示，使其更容易使用，例如 Microsoft Dynamics 365 Guides 中的 [上一頁] 按鈕。

### <a name="prevent-flickering-with-delayed-feedback"></a>使用延遲回饋防止閃爍
在開始視覺化回饋前使用短暫延遲，可避免有人經過佇留目標時發生閃爍。
* 對於經常使用的按鈕，讓延遲保持非常短暫，應用程式就會覺得有反應。
* 對於不常使用的按鈕，較長的延遲可能不適合，以免介面感覺焦躁不安。

## <a name="ui-patterns"></a>UI 模式

### <a name="high-frequency-buttons"></a>高頻率按鈕
![Microsoft Dynamics 365 Guides 下一頁按鈕](images/GuideNextButton.png "Microsoft Dynamics 365 Guides 下一步按鈕") 高頻率按鈕就是常用於整個應用程式的按鈕。 Microsoft Dynamics 365 Guides 中的下一頁和上一頁按鈕都是不錯的範例。

高頻率按鈕應該...
* 是較大的按鈕，可輕易以頭部注視方式點擊
* 位置接近眼部高度，以免造成人體工學負擔。

### <a name="low-frequency-buttons"></a>低頻率按鈕
低頻率按鈕是整個應用程式中不會定期互動的按鈕。 可存取 [設定] 功能表的按鈕，或可清除所有工作的按鈕都是不錯的範例。

* 嘗試讓這些按鈕不在常用的頭部注視路徑中，以免意外啟動。 

### <a name="confirmations"></a>確認
![Microsoft Dynamics 365 Guides 確認對話方塊](images/GuidesConfirmation.png "Microsoft Dynamics 365 Guides 確認對話方塊")

當某個動作有重大影響時 (例如收費、刪除工作或開始長時間處理)，最好確認個人要選取按鈕。 對於「頭部注視並佇留」UI，確認對話方塊有一些模式和考量：

  * 在主要按鈕上顯示選取醒目提示。
  * 與選取醒目提示同時顯示佇留目標。
  * 對於次要按鈕，顯示頭部注視的佇留目標。
        
### <a name="toggle-buttons"></a>切換按鈕
切換按鈕需要一些微妙的邏輯，才能正常運作。 當人員佇留在切換按鈕並啟動它時，他們需要結束按鈕，然後回頭重新啟動佇留邏輯。 切換按鈕會有清楚的作用與非作用中狀態很重要。 

### <a name="list-views"></a>清單檢視
![Microsoft Dynamics 365 Guides 確認對話方塊](images/GuidesListView.png "Microsoft Dynamics 365 Guides 確認對話方塊")清單檢視呈現「頭部注視並佇留」輸入的特定挑戰。 人們需要能夠掃描內容，而不覺得必須偷偷摸摸地環顧佇留目標。 

設計清單檢視的一些秘訣：
* 使用頭部注視時整列醒目提示，但不會開始佇留，除非頭部注視位於特定佇留目標上。
* 醒目提示該列時，只顯示佇留目標，以降低視覺雜訊。
* 佇留目標的位置清楚而一致。
* 不要一次顯示所有佇留目標，以避免重複的 UI
* 盡可能重新使用相同的模式以便熟悉 UX
 
 ## <a name="see-also"></a>請參閱
* [手部直接操作](direct-manipulation.md)
* [手部指向和行動](point-and-commit.md)
* [本能互動](interaction-fundamentals.md)
* [頭部目光和行動](gaze-and-commit.md)
* [語音命令](voice-design.md)
