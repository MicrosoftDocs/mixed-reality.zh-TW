---
title: 告示板和 tag-along
description: 告示板物件一律導向本身所面臨的使用者。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，告示板 tag-along
ms.openlocfilehash: e33ab0121398742b2e48553c9cbf2c1debdc6abf
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974781"
---
# <a name="billboarding-and-tag-along"></a>告示板和 tag-along

告示板是一種行為的概念，可以在混合實境中套用至物件。 告示板物件一律導向本身所面臨的使用者。 這點格外有用的文字和靜態物件 （世界鎖定） 的使用者的環境中的放置位置的施展空間系統經過不易辨認或無法讀取，如果使用者四處移動。

![HoloLens 觀點來看的功能表系統，永遠會面臨使用者](images/billboarding-fragments.gif)<br>
*HoloLens 觀點來看的功能表系統，永遠會面臨使用者*

具有告示板 已啟用的物件可以自由地旋轉，在使用者的環境中。 它們也可以限制為根據的設計考量之單一軸。 請記住，billboarded 的物件可能會裁剪或 occlude 本身，如果它們位於太接近其他物件，或在 HoloLens，太靠近掃描介面。 若要避免這個問題，請思考的總使用量啟用告示板軸上旋轉時，可能會產生物件。

## <a name="what-is-a-tag-along"></a>什麼是 tag-along？

Tag-along 是一種行為的概念，可以新增到全像投影，包括 billboarded 的物件。 此互動是更自然易懂的方式達到 head 鎖定內容的效果。 Tag-along 物件會嘗試絕不能離開使用者的檢視。 這可讓使用者自由與之際，也仍然全像投影其直接檢視之外的最上層的互動。

![HoloLens pin 面板是 tag-along 的運作方式的絕佳範例](images/tagalong-1000px.jpg)<br>
*HoloLens 開始功能表是 tag-along 行為的絕佳範例*

Tag-along 物件都有參數，來調整它們的行為的方式。 內容可以是流入或流出使用者的直視視使用者移動其環境時。 當使用者移動時，內容會嘗試將朝向檢視的邊緣滑動以保持使用者位於周邊視覺範圍內，視使用者移動的速度可能會導致暫時超出檢視的內容。 當使用者 gazes 朝向 tag-along 物件時，它進入更完整檢視。 將一律正在 「 一目瞭然消失 」，讓使用者永遠不會忘記其內容是在何種方向的內容。

其他參數可以讓覺得附加至使用者的標頭的拖放矩形 tag-along 物件。 抑制加速或減速的權數來讓它認為更實際存在的物件。 此 spring 行為是功能可協助使用者建置 tag-along 的運作方式的精確心智模型的可見性。 音訊可協助使用者在 tag-along 模式中有物件時，提供額外提供的。 音訊都應該強化的速度移動;快速前端輪應該提供更顯著的音效，而逐一查看以自然的速度應該完全最小的音訊，如果有任何效果。

就像真正的 head 鎖定的內容，充斥或 nauseating 如果它們之間移動，或年春季太多的使用者檢視，可以證明 tag-along 物件。 因為的使用者看起來，然後快速地停止，其選擇題告訴他們，他們已停止。 其平衡會通知他們，其標頭已停止微調，以及其願景所看到開啟的世界停駐點。 不過，如果使用者已停止時，會保留在移動 tag-along，它可能會混淆其角度來看。

## <a name="see-also"></a>另請參閱
* [游標](cursors.md)
* [本能互動](interaction-fundamentals.md)
* [舒適度](comfort.md)
