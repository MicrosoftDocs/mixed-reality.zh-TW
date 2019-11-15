---
title: 可互動物件
description: 一個按鈕很長的比喻，是用來觸發2D 抽象世界中的事件。 在三維混合現實世界中，我們不再需要局限于此抽象概念。
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: 混合的現實、控制項、互動、ui、ux
ms.openlocfilehash: 5305af97e9811134212fc6c730727962bb9e8353
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105790"
---
# <a name="interactable-object"></a>可互動物件

![Interactible 物件](images/UX/UX_Hero_Interactable.jpg)

一個按鈕很長的比喻，是用來觸發2D 抽象世界中的事件。 在三維混合現實世界中，我們不再需要局限于此抽象概念。 任何專案都可以是觸發事件的**可互動物件**。 可互動物件可以從資料表上的咖啡杯，呈現為以空中浮動的球形文字。 在某些情況下，我們仍會使用傳統按鈕，例如在對話方塊 UI 中。 按鈕的視覺表示方式取決於內容。

<br>

---


## <a name="important-properties-of-the-interactable-object"></a>可互動物件的重要屬性

### <a name="visual-cues"></a>視覺提示

視覺提示是以光線的形式收到的感應式提示，並在視覺認知期間由視覺系統處理。 由於視覺系統是許多物種的主要功能，特別是人類的視覺提示，是世界的認知方式的大量資訊來源。

由於「全像攝影」物件在混合現實中與真實世界的環境混合，因此可能很難以瞭解哪些物件可以互動。 針對您的體驗中的任何可互動物件，請務必為每個輸入狀態提供區分的視覺提示。 這可協助使用者瞭解您的經驗可互動，並使用一致的互動方法，讓使用者安心。

<br>

---

### <a name="far-interactions"></a>遠互動

對於使用者可以與注視、手光線和運動控制器光線互動的任何物件，我們建議您針對這三種輸入狀態有不同的視覺提示：

:::row:::
    :::column:::
       ![interactibleobject-狀態-預設](images/interactibleobject-states-default.jpg)<br>
       **預設（觀察）狀態**<br>
        物件的預設閒置狀態。
    游標不在物件上。 未偵測到手。
    :::column-end:::
    :::column:::
       ![interactibleobject 狀態-目標](images/interactibleobject-states-targeted.jpg)<br>
        **目標（暫留）狀態**<br>
        當物件以注視游標、手指鄰近或移動控制器的指標為目標時。
    游標位於物件上。 已偵測到手中，已備妥。
    :::column-end:::
    :::column:::
       ![interactibleobject 狀態-按下的](images/interactibleobject-states-pressed.jpg)<br>
       **已按下狀態**<br>
        當按下滑鼠按鍵時，手指按下或移動控制器的 [選取] 按鈕。
    游標位於物件上。 偵測到手中，按下 [空中]。
    :::column-end:::
:::row-end:::

<br>

---

您可以使用像是反白顯示或縮放等技術，為使用者的輸入狀態提供視覺提示。 在混合的現實中，您可以在 [開始] 功能表上找到視覺化不同輸入狀態的範例，以及使用應用程式列按鈕。 

以下是這些狀態在「全像攝影」**按鈕**上的外觀：

:::row:::
    :::column:::
       ![interactibleobject-狀態-預設](images/MRTK_InteractableState-default.jpg)<br>
       **預設（觀察）狀態**<br>
    :::column-end:::
    :::column:::
       ![interactibleobject 狀態-目標](images/MRTK_InteractableState-targeted.jpg)<br>
        **目標（暫留）狀態**<br>
    :::column-end:::
    :::column:::
       ![interactibleobject 狀態-按下的](images/MRTK_InteractableState-pressed.jpg)<br>
       **已按下狀態**<br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a>近乎互動（direct） 

HoloLens 2 支援明確的手寫追蹤輸入，可讓您與物件互動。 如果沒有 haptic 的意見反應和完美的深度認知，有時可能很難分辨出手距物件的距離，或您是否觸及它。 請務必提供足夠的視覺提示來傳達物件的狀態，特別是與該物件相關的實際操作狀態。

使用視覺效果意見反應來傳達下列內容：
* **預設值（觀察）** ：物件的預設閒置狀態。
* 暫**留：當**手近于全息影像時，將視覺效果變更為以全像投影來溝通。 
* **距離和互動點**：正如手中的「全像投影」，設計意見反應來傳達預定的互動點，以及從物件到手指的距離
* **連絡人開始**：變更視覺效果（淺色、色彩）以溝通觸控已發生
* **Grasped**： Grasped 物件時變更視覺效果（淺色、色彩）
* **連絡人結束**：觸控結束時變更視覺效果（淺色、色彩）

<br>

---

:::row:::
    :::column:::
        ![停留（目前）](images/640px-interactibleobject-states-near-hover.jpg)<br>
        **暫留（目前）**<br>
        根據手的鄰近程度來反白顯示。
    :::column-end:::
    :::column:::
        ![暫留（附近）](images/640px-interactibleobject-states-near-hovernear.jpg)<br>
        **暫留（接近）**<br>
        將大小變更反白顯示為根據手的距離。
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![觸控/按](images/640px-interactibleobject-states-near-press.jpg)<br>
        **觸控/按**<br>
        視覺效果加上音訊意見反應。
    :::column-end:::
    :::column:::
        ![抓住](images/640px-interactibleobject-states-near-grasp.jpg)<br>
        **領會**<br>
        視覺效果加上音訊意見反應。
    :::column-end:::
:::row-end:::

<br>

<br>

---

[HoloLens 2 上的按鈕](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)是如何視覺化不同輸入互動狀態的範例：

:::row:::
    :::column:::
        ![預設](images/640px-interactibleobject-pressablebutton-default.jpg)<br>
        **預設**<br>
    :::column-end:::
    :::column:::
        ![滑鼠停留](images/640px-interactibleobject-pressablebutton-hover.jpg)<br>
        **逐個**<br>
        顯示以鄰近性為基礎的光源效果。
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![觸控](images/640px-interactibleobject-pressablebutton-touch.jpg)<br>
        **觸控**<br>
        顯示 ripple 效果。
    :::column-end:::
    :::column:::
        ![按](images/640px-interactibleobject-pressablebutton-press.jpg)<br>
        **出版**<br>
        移動 front 盤子。
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a>HoloLens 2 上的「環形」視覺提示<br>
        在 HoloLens 2 上有其他視覺提示，可協助使用者深入瞭解。 當 fingertip 接近物件時，會顯示 fingertip 附近的環形並相應減少。 當到達已按下的狀態時，環形最後會聚合成一個點。 此視覺效果 affordance 可協助使用者瞭解他們與物件之間的距離。<br>
        <br>
        *影片迴圈：根據距離周框方塊的視覺效果意見反應範例*
    :::column-end:::
        :::column:::
        ![空間](images/spacer-20x582.png)<br>
       ![視覺效果意見反應](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a>音訊提示

對於直接的互動，適當的音訊意見反應可以大幅改善使用者體驗。 使用音訊意見反應來傳達下列內容：
* **連絡人開始**：觸控開始時播放音效
* **連絡人結束**：在觸控結束時播放音效
* **抓取開始**：抓取開始時播放音效
* **抓取結束**：抓取結束時播放音效

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a>語音命令<br>
        針對任何可互動物件，請務必支援替代互動選項。 根據預設，我們建議可互動的任何物件都支援[語音命令](voice-design.md)。 若要改善可搜尋性，您也可以在停留狀態期間提供工具提示。<br>
        <br>
        *影像：語音命令的工具提示*
    :::column-end:::
        :::column:::
       ![語音命令](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a>大小調整建議 

若要確保使用者可以輕鬆地觸及所有可互動物件，建議您根據其與使用者的距離，確定可互動符合最小大小（視覺效果的角度，通常以度為單位測量）。 視覺角度是以使用者眼和物件之間的距離為依據，並維持不變，而目標的實體大小可能會隨著使用者變更的距離而改變。 若要根據與使用者的距離來判斷物件的必要實體大小，請嘗試使用視覺角度計算機，例如[這一項](https://elvers.us/perception/visualAngle/)。

以下是最小可互動內容大小的建議。


### <a name="target-size-for-direct-hand-interaction"></a>直接操作的目標大小

| 長途電話 | 視角 | Size |
|---------|---------|---------|
| 45cm  | 不小於2° | 1.6 x 1.6 cm |

直接操作](images/TargetSizingNear.jpg) 的 ![目標大小<br>
*直接操作的目標大小*

<br>

### <a name="target-size-for-buttons"></a>按鈕的目標大小

建立直接互動的按鈕時，我們建議使用較大大小的最小值 3.2 x 3.2 cm，以確保有足夠的空間可包含圖示，而且可能會有一些文字。

| 長途電話 | 最小大小 |
|---------|---------|
| 45cm  | 3.2 x 3.2 cm |

![按鈕的目標大小](images/TargetSizingButtons.png)<br>
*按鈕的目標大小*

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>右手光線或注視互動的目標大小
| 長途電話 | 視角 | Size |
|---------|---------|---------|
| 2m  | 不小於1° | 3.5 x 3.5 cm |

![右手光線或注視互動](images/TargetSizingFar.jpg) 的目標大小<br>
*右手光線或注視互動的目標大小*


<br>

---


## <a name="interactable-object-in-mrtkmixed-reality-toolkit-for-unit"></a>適用于 Unit 的 MRTK （混合現實工具組）中的可互動物件

在 **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 中，您可以使用腳本[**可互動**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts)，讓物件回應各種類型的輸入互動狀態。 它支援各種類型的主題，可讓您藉由控制物件屬性（例如色彩、大小、材質和著色器）來定義視覺狀態。

* [可互動](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [Button](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [手動互動範例場景](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

MixedRealityToolkit 的標準著色器提供各種選項，例如**近光源**，可協助您建立視覺效果和音訊提示。
* [MRTK 標準著色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


<br>

---


## <a name="see-also"></a>請參閱

* [游標](cursors.md)
* [手型光線](point-and-commit.md)
* [Button](button.md)
* [可互動的物件](interactable-object.md)
* [週框方塊和應用程式列](app-bar-and-bounding-box.md)
* [處理](direct-manipulation.md)
* [手部功能表](hand-menu.md)
* [近端功能表](near-menu.md)
* [物件集合](object-collection.md)
* [語音命令](voice-input.md)
* [鍵盤](keyboard.md)
* [並用](tooltip.md)
* [石板](slate.md)
* [滑桿](slider.md)
* [佈告板和常駐標籤](billboarding-and-tag-along.md)
* [顯示進度](progress.md)
* [表面磁性](surface-magnetism.md)