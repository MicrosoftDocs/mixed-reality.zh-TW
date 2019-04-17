---
title: 為目標的視線
description: 使用者能夠針對他們想要進行互動，無論輸入強制回應性的項目所建立的所有互動。
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 混合實境、 視線、 視線目標，就會有互動，設計
ms.openlocfilehash: c3225e27331f8afcda65469eb84fe5470bf6ee8c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592084"
---
# <a name="gaze-targeting"></a>為目標的視線

使用者能夠針對他們想要進行互動，無論輸入強制回應性的項目所建立的所有互動。 在 Windows Mixed Reality，這通常是使用使用者的視線。

若要啟用的使用者，才能順利運作的體驗，系統的導出了解使用者的意圖，以及使用者的實際的意圖，必須為儘可能密集地對齊。 程度系統解譯使用者的預定的動作正確，增加滿意度和效能改善。

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>功能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens （第 1 代）</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td> 為目標的視線</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;">✔️ </td>
</tr><tr>
<td> 眼睛目標</td><td style="text-align: center;"></td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

> [!NOTE]
> HoloLens 2 的特定的詳細指引[即將推出](index.md#news-and-notes)。

## <a name="target-sizing-and-feedback"></a>目標大小和意見反應

視線向量可能會重複用來順利的目標，但通常最適合 gross 目標 （取得較大目標）。 1 到 1.5 度的最小目標大小應該在大部分情況下，允許成功的使用者動作，但目標 3 度通常可讓較快的速度。 請注意，使用者目標實際上是 3D 元素--即使 2D 區域的大小任何投影面向它們應該將目標設為區域。 提供一些主要的項目是 「 作用中 」 （該使用者以其為目標） 的提示會非常有用-這可能包括經過處理，例如顯示 「 暫留 」 效果、 音效反白顯示或需按幾下，或清除元素的資料指標的對齊方式。

![2 個計量表距離的最佳目標大小](images/gazetargeting-size-1000px.jpg)<br>
*2 個計量表距離的最佳目標大小*

![舉例來說，反白顯示的視線目標的物件](images/gazetargeting-highlighting-640px.jpg)<br>
*舉例來說，反白顯示的視線目標的物件*

## <a name="target-placement"></a>目標位置

使用者將通常無法找到位於很高或極低的 UI 項目中的視角，將焦點放在周圍 （通常大約是眼睛層級） 及其主要焦點區域注意大多。 將大部分的目標放在一些合理的頻外，周圍視覺層級可以幫助。 指定使用者傾向專注於相對較小視覺效果區域 （願景 attentional 圓錐圖是大約 10 度），隨時分組的 UI 項目程度它們在概念上相關可以利用注意鏈結的行為項目到項目以使用者身分將其視線通過區域。 在設計 UI 時，請記住視野 HoloLens 和沈浸式耳機之間的潛在大變異。

![舉例而言，更輕鬆的視線 Galaxy 檔案總管中的目標群組的 UI 項目](images/gazetargeting-grouping-1000px.jpg)<br>
*舉例而言，更輕鬆的視線 Galaxy 檔案總管中的目標群組的 UI 項目*

## <a name="improving-targeting-behaviors"></a>改善目標的行為

如果使用者意圖為目標的項目可以決定 （或接近近似），它可以接受"near miss"會嘗試在互動，如同它們已正確目標很有幫助。 有少數幾個成功的方法，可以將其納入混合的實境體驗：

### <a name="gaze-stabilization-gravity-wells"></a>視線穩定 (「 重力 wells")

這應該開啟大部分/所有的時間。 這項技術會移除使用者可能有自然的前端/頸部做法。 也因為尋找/談到的行為而移動。

### <a name="closest-link-algorithms"></a>最接近的連結演算法

這些最適合疏鬆的互動式內容區域中。 如果有較高的機率，您可以決定使用者已嘗試進行互動，您可以只假設某些層級的意圖來補充其目標的能力。

### <a name="backdatingpostdating-actions"></a>Backdating/postdating 動作

這項機制可用於需要速度的工作。 當使用者是透過一系列的目標/啟用調動的速度移動時，它可用來假設某些意圖，並允許*錯過步驟*目標使用者是否具有焦點稍微之前或之後點選 （稍微採取動作50 毫秒前/後為有效的早期測試）。

### <a name="smoothing"></a>平滑處理

這項機制可用於路徑移動，減少些許抖動/搖晃因為自然磁頭移動特性。 當透過 smooth 大小/距離的移動，而不是經過一段時間的路徑動作平滑處理

### <a name="magnetism"></a>磁場

這項機制可以視為 「 最接近連結 」 演算法-繪製為目標，向資料指標，或 （不論明顯與否），只需增加 hitboxes 的較通用版本使用者達到可能的目標，使用互動式的版面配置，以一些知識使用者意圖更好的方法。 這可以是特別強大，小型的目標。

### <a name="focus-stickiness"></a>焦點黏著度

當判斷哪些焦點提供給互動項目附近，會提供目前焦點的項目偏差。 這有助於減少不穩定的焦點時具有自然雜訊的兩個項目之間的中間點在浮動切換行為。

## <a name="see-also"></a>另請參閱
* [筆勢](gestures.md)
* [語音設計](voice-design.md)
* [資料指標](cursors.md)
