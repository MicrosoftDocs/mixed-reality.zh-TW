---
title: 頭部注視並認可
description: 頭部注視並認可輸入模型的概觀
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Mixed Reality, 注視, 注視定向, 互動, 設計
ms.openlocfilehash: 5fef778dde6852222e098aeb1cbb41fe04e0b744
ms.sourcegitcommit: a5dc182da237f63f0487d40a2e11894027208b6c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2019
ms.locfileid: "73441093"
---
# <a name="head-gaze-and-commit"></a>頭部注視並認可
「_前端」和「認可_」是一種特殊的[注視和認可](gaze-and-commit.md)輸入模型，其中牽涉到以您的頭向後（head 方向）方向為物件的目標，然後使用次要輸入（例如手手勢空中）來進行動作。請敲擊或語音命令「選取」。 

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
        <td>頭部注視並認可</td>
        <td>✔️ 建議使用</td>
        <td>✔️ 建議使用 (第三個選擇 - <a href="interaction-fundamentals.md">查看其他選項</a>)</td>
        <td>➕ 替代選項</td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a>目標大小調整和回饋
列印頭的向量已重複顯示，可用於適當的目標，但通常最適合用於總目標--取得較大的目標。 在大部分情況下，最小的目標大小為1到1.5 度，允許成功的使用者動作，但3度的目標通常允許更快的速度。 請注意，使用者定向的大小實際上是 2D 區域 (即使是 3D 元素)，無論哪個投影面向他們都應該是可作為目標的區域。 提供某個元素為「作用中」的一些顯著提示（使用者以其為目標）非常有用。 這可能包括如可見的「暫留」效果、音訊反白顯示或點擊，或清除游標與專案的對齊。

![距離 2 公尺的最佳目標大小](images/gazetargeting-size-1000px.jpg)<br>
*距離 2 公尺的最佳目標大小*

<br>

![醒目提示注視目標物件的範例](images/gazetargeting-highlighting-940px.jpg)<br>
*醒目提示注視目標物件的範例*

## <a name="target-placement"></a>目標位置
使用者通常無法在其視野中找到位置非常高或非常低的 UI 元素，著重于其主要焦點附近的區域，這大約是眼睛。 將大部分的目標放在眼部水平周圍的合理頻帶會有所幫助。 假設使用者傾向於隨時將焦點放在相對較小的視覺區域 (視覺的注意視錐大約是 10 度)，將概念上相關的 UI 元素聚集在一起，可以在使用者目光掃過區域時運用逐一項目的注意鏈結行為。 在設計 UI 時，請記住 HoloLens 與沉浸式頭戴裝置之間的視野可能有很大的變化。

![方便在 Galaxy Explorer 中進行注視定向的分組 UI 元素範例](images/gazetargeting-grouping-1000px.jpg)<br>
*方便在 Galaxy Explorer 中進行注視定向的分組 UI 元素範例*

## <a name="improving-targeting-behaviors"></a>改善定向行為
如果使用者意圖是以某個專案為目標（或接近），則在互動時接受接近遺漏的嘗試，可能會很有説明，如同其目標正確。 以下是幾個成功的方法，可以併入混合現實體驗中：

### <a name="head-gaze-stabilization-gravity-wells"></a>頭部注視穩定 (「重力穴」)
這應該會在大部分或全時間開啟。 這項技術會移除使用者可能因外觀和說話行為而進行移動的自然頭和頸部起伏快速變換。

### <a name="closest-link-algorithms"></a>最接近的連結演算法
這些最適合用於具有疏鬆互動式內容的區域。 如果您可以判斷使用者嘗試與之互動的機率很高，則可以假設某種程度的意圖來補充其目標功能。

### <a name="backdating-and-postdating-actions"></a>Backdating 和 postdating 動作
這項機制對於要求速度的工作很實用。 當使用者透過一系列的目標和啟用調動快速移動時，假設有一些意圖，並允許遺漏的步驟，以使用者在點在點前後的焦點（50毫秒之前/之後）來採取目標rly 測試）。

### <a name="smoothing"></a>平滑處理
這種機制對於路徑移動很有用，因為自然的頭移動特性，減少輕微的抖動和 wobble。 平滑處理路徑動作時，會以移動的大小和距離來平滑，而不是一段時間。

### <a name="magnetism"></a>磁性
這項機制可以視為較通用的最接近連結演算法版本--將游標向目標繪製，或只是以明顯的方式增加 hitboxes （不論是否可見），因為使用者可能會藉由使用某些互動式版面配置知識更好方法使用者意圖。 這對於小型目標特別有效果。

### <a name="focus-stickiness"></a>焦點黏著度
在決定要將焦點放在哪些鄰近的互動式元素時，[焦點] 會向目前焦點的元素提供偏差。 當兩個專案之間的點浮動時，這有助於減少不穩定的焦點切換行為。


## <a name="see-also"></a>請參閱
* [目視互動](eye-gaze-interaction.md)
* [目光和停駐](gaze-and-dwell.md)
* [直接操作](direct-manipulation.md)
* [實習手勢](gaze-and-commit.md#composite-gestures)
* [實際操作和認可](point-and-commit.md)
* [本能互動](interaction-fundamentals.md)
* [語音輸入](voice-input.md)



