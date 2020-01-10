---
title: Billboarding 和標記-沿著
description: 具有 billboarding 的物件一律會向自己引導，以面對使用者。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，billboarding，加上標記
ms.openlocfilehash: 24c4ca8bdc3c6ea1081311102204d4a7f5a95425
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723177"
---
# <a name="billboarding-and-tag-along"></a>Billboarding 和標記-沿著

<br>

<img src="images/UX/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a>什麼是 billboarding？

Billboarding 是一種行為概念，可套用至混合現實中的物件。 具有 billboarding 的物件一律會向自己引導，以面對使用者。 這對於文字和功能表系統特別有説明，其中放置在使用者環境中的靜態物件（世界鎖定的）會在使用者四處移動時隱藏或無法讀取。

啟用 billboarding 的物件可以在使用者的環境中自由地旋轉。 視設計考慮而定，它們也可以限制為單一軸。 請記住，如果 billboarded 物件的位置太接近其他物件，或在 HoloLens 中太接近掃描的表面，則可能會裁剪或遮蔽本身。 若要避免這種情況，請考慮物件在已啟用 billboarding 的軸上旋轉時，可能會產生的總使用量。

<br>

---
## <a name="what-is-a-tag-along"></a>什麼是標記？

標記-沿著是可新增至全息影像的行為概念。 標記物件會嘗試停留在允許使用者輕鬆互動的範圍內。

![HoloLens pin 面板是如何進行標記的絕佳範例](images/tagalong-1000px.jpg)<br>
*HoloLens 的 [開始] 功能表是標記和行為的絕佳範例*

加上標籤的物件具有可以微調其行為方式的參數。 當使用者在其環境中移動時，可以視需要在使用者的視線中進入或登出內容。 當使用者移動時，內容會透過滑動到視野的邊緣來嘗試停留在使用者的其邊界中，視使用者移動的速度而定，可能會讓內容暫時消失。 當使用者 gazes 到標記物件時，它會有更完整的視野。 將內容視為「一目了然」，讓使用者不會忘記內容的方向。

其他參數可以讓以標籤為依據的物件，由橡皮區連接到使用者的前端。 抑制加速或減速會為物件提供權數，使其更實際呈現。 這個春季行為是一個 affordance，可協助使用者建立標記運作方式的精確心理模型。 當使用者在標記模式下具有物件時，音訊有助於提供額外的 affordances。 音訊應該會強化移動的速度;快速的前端應該提供更明顯的音效效果，而如果有任何影響，自然速度應該會有最小的音訊。

就像真正的前端鎖定內容一樣，如果在使用者的觀點裡經常移動或說得太多，標籤物件就可以證明很大或 nauseating。 當使用者查看並快速停止時，他們的分辨會告訴他們已停止。 其餘額會通知他們其前端已停止轉動，而其願景也會導致世界停止轉動。 不過，如果在使用者停止時，標記會繼續移動，可能會混淆其感知。

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a>適用于 Unity 的 Billboarding 和標記-MRTK （混合現實工具組）
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 提供 Billboarding 和標記的行為腳本。 只要將 Billboard.cs 腳本指派給任何物件，就可以加入 billboarding 行為，讓物件永遠都是您的臉。 若要新增標記和行為，請使用 RadialView.cs 腳本。 您可以調整各種選項，例如 lerping 時間、距離和程度。

* [MRTK-星形視圖規劃求解](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html#radialview)
* [MRTK-佈告欄腳本](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a>請參閱

* [游標](cursors.md)
* [手部光線](point-and-commit.md)
* [Button](button.md)
* [可互動的物件](interactable-object.md)
* [週框方塊和應用程式列](app-bar-and-bounding-box.md)
* [操作](direct-manipulation.md)
* [手部功能表](hand-menu.md)
* [近端功能表](near-menu.md)
* [物件集合](object-collection.md)
* [語音命令](voice-input.md)
* [鍵盤](keyboard.md)
* [工具提示](tooltip.md)
* [平板](slate.md)
* [滑桿](slider.md)
* [著色器](shader.md)
* [佈告板和常駐標籤](billboarding-and-tag-along.md)
* [顯示進度](progress.md)
* [表面磁性](surface-magnetism.md)
