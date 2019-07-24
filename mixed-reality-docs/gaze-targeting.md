---
title: 注視目標
description: 無論輸入形式為何，當使用者能夠瞄準他們想要進行互動的元素時，所有互動就已建立。
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Mixed Reality, 注視, 注視目標, 互動, 設計
ms.openlocfilehash: eddc832456b2ba0c6bc8955157d2c8e1a268e893
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829846"
---
# <a name="gaze-and-dwell"></a>注視和停留
有很多不同的方式可以確認_認可_, 例如結合注視與_聲音_或_手手勢_。
不過, 有數個使用者案例, 使用者的手中可能忙碌或無法追蹤 (例如, 背景工作的工作者人數過大的沉重)。 語音輸入也可能因為使用者喜好設定、社交內容或更高的環境而無法使用。
做為回溯解決方案, 另一個執行_認可_的選項, 就是將開始保留在我們稱為_停留_的 UI 元素上。
您可以使用 head 或眼睛來執行_停留_。 概念很簡單, 而且可以在下列階段中細分: 
1. 使用者在全像攝影按鈕上啟動撥雲見日

2. 在短暫的萌芽延遲 (例如, 150 毫秒) 之後, 會啟動一些視覺效果回饋動畫。 萌芽延遲是用來避免使用者立即隨時掌握意見反應。
    - 針對_眼睛眼_, 建議您將下列內容用於視覺監看意見反應的設計:
      - **Blend**:從一開始就看不到完全不透明的意見反應順暢地 blend。 這使得意見反應越不容易分散和 overwhleming, 並妥善配合系統有使用者真正想要與此按鈕互動的信心。
      - **將它提取到**:建立視覺效果的意見反應, 而不是縮小大小並移至目標中心, 並在使用者的視覺效果中提取。 

3. 在預先定義的停留時間 (例如, 800 毫秒) 之後, 停留完成並觸發相關聯的事件。
    - 提供一些最終的聽覺或視覺效果意見反應, 讓您現在可以選擇專案的首頁。

![停留狀態](images/eyes_dwellstate_recommendation.png)


# <a name="gaze-targeting"></a>注視目標

無論輸入形式為何，當使用者能夠瞄準他們想要進行互動的元素時，所有互動就已建立。 在 Windows Mixed Reality 中，這通常會使用使用者的注視進行。

若要讓使用者能夠順利體驗，系統導出的使用者意圖理解，以及使用者的實際意圖都必須儘可能相吻合。 系統儘可能正確解譯使用者的預定動作，所以滿意度提升且效能改善。

## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>注視目標</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>目視目標</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

> [!NOTE]
> [即將推出](index.md)更多 HoloLens 2 特定指引。

## <a name="target-sizing-and-feedback"></a>目標大小調整和回饋

雖已重複表示注視向量可用於細微定向，但通常最適合用於粗略定向 (取得較大的目標)。 在大部分情況下，1 到 1.5 度的最小目標大小應可達成成功的使用者動作，但是 3 度的目標通常可讓速度提升。 請注意，使用者定向的大小實際上是 2D 區域 (即使是 3D 元素)，無論哪個投影面向他們都應該是可作為目標的區域。 提供元素為「作用中」(使用者以其為目標) 的一些明顯線索非常有用 - 這可能包括視覺「暫留」效果、音訊醒目提示或點按，或游標與元素的清楚比對等處理。

![2 個計量表距離的最佳目標大小](images/gazetargeting-size-1000px.jpg)<br>
*2 個計量表距離的最佳目標大小*

![醒目提示注視目標物件的範例](images/gazetargeting-highlighting-640px.jpg)<br>
*醒目提示注視目標物件的範例*

## <a name="target-placement"></a>目標位置

使用者通常找不到其視野中位於很高或很低的 UI 元素，而將其大部分的注意力放在其主要焦點的四周 (通常大約在眼部水平高度)。 將大部分的目標放在眼部水平周圍的合理頻帶會有所幫助。 假設使用者傾向於隨時將焦點放在相對較小的視覺區域 (視覺的注意視錐大約是 10 度)，將概念上相關的 UI 元素聚集在一起，可以在使用者目光掃過區域時運用逐一項目的注意鏈結行為。 在設計 UI 時，請記住 HoloLens 與沉浸式頭戴裝置之間的視野可能有很大的變化。

![方便在 Galaxy Explorer 中進行注視定向的分組 UI 元素範例](images/gazetargeting-grouping-1000px.jpg)<br>
*方便在 Galaxy Explorer 中進行注視定向的分組 UI 元素範例*

## <a name="improving-targeting-behaviors"></a>改善定向行為

如果可以判定使用者瞄準某物的意圖 (或極為近似)，則接受互動時的「近似差錯」嘗試 (彷彿已正確瞄準) 很有幫助。 有少數幾個成功方法可以納入混合實境體驗：

### <a name="gaze-stabilization-gravity-wells"></a>注視穩定 ("引力 wells")

在大部分/所有的時間，應該開啟此功能。 這項技術會消除使用者可能會有的頭部/頸部緊張情形。 以及由於觀看/說話行為而造成的移動。

### <a name="closest-link-algorithms"></a>最接近的連結演算法

這些最適合用於具有疏鬆互動式內容的區域。 如果您非常可能判定使用者嘗試進行互動的項目，則只要假定某些層級的意圖，即可補充其定向能力。

### <a name="backdatingpostdating-actions"></a>回溯記日/事後記日動作

這項機制對於要求速度的工作很實用。 當使用者在一系列以速度為目標/啟用調動的過程中移動時, 可能會有一些意圖, 並允許*遺漏的步驟*來採取動作, 讓使用者在點按 (50 毫秒之前/之後) 稍早或稍微專注于目標在早期測試時生效)。

### <a name="smoothing"></a>平滑處理

這項機制可用於路徑移動，減少自然頭部移動特性所造成的些許抖動/搖晃。 平滑處理路徑移動時，請依照移動的大小/距離 (而非隨著時間) 進行平滑處理

### <a name="magnetism"></a>磁性

這項機制可以視為更普遍的「最接近連結」演算法版本 - 繪製指向目標的游標，或只要在使用者接近適當目標時增加命中框 (不論是否看得見)，使用互動式版面配置的一些知識更完善處理使用者意圖。 這對於小型目標特別有效果。

### <a name="focus-stickiness"></a>焦點黏著度

在判斷要聚焦在哪些附近互動式元素時，提供目前焦點所在元素的偏差。 這有助於在浮動於兩個具有自然雜訊的元素間中點時，減少不穩定的焦點切換行為。

## <a name="see-also"></a>另請參閱
* [筆勢](gestures.md)
* [語音命令](voice-design.md)
* [游標](cursors.md)
