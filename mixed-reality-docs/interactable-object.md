---
title: 可互動物件
description: 一個按鈕很長的比喻, 是用來觸發2D 抽象世界中的事件。 在三維混合現實世界中, 我們不再需要局限于此抽象概念。
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: 混合的現實、控制項、互動、ui、ux
ms.openlocfilehash: 57299cbb758a69603fc68ad5d43af8f2216e5104
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415357"
---
# <a name="interactable-object"></a>可互動物件

一個按鈕很長的比喻, 是用來觸發2D 抽象世界中的事件。 在三維混合現實世界中, 我們不再需要局限于此抽象概念。 任何專案都可以是觸發事件的**可互動物件**。 可互動物件可以從資料表上的咖啡杯, 呈現為以空中浮動的球形文字。 在某些情況下, 我們仍會使用傳統按鈕, 例如在對話方塊 UI 中。 按鈕的視覺表示方式取決於內容。

![Interactible 物件](images/640px-interactibleobject-hero-640px.jpg)


## <a name="important-properties-of-the-interactable-object"></a>可互動物件的重要屬性

### <a name="visual-cue"></a>視覺提示

視覺提示是以光線的形式收到的感應式提示, 並在視覺認知期間由視覺系統處理。 由於視覺系統是許多物種的主要功能, 特別是人類的視覺提示, 是世界的認知方式的大量資訊來源。

在混合的現實中, 由於全像攝影物件與真實世界的環境混合, 因此可能很難以瞭解哪些物件是可互動的。 針對您的體驗中的任何可互動物件, 請務必提供每個輸入狀態的區分視覺提示。 這可協助使用者瞭解您的經驗可互動, 並讓使用者安心使用一致的互動方式。

#### <a name="far-interactions"></a>遠互動

對於使用者可以與注視、手光線和運動控制器光線互動的任何物件, 我們建議您針對這三種輸入狀態有不同的視覺提示:
* **預設值 (觀察)** :物件的預設閒置狀態。
* **目標 (滑鼠停留)** :當物件以注視游標、手指鄰近或移動控制器的指標為目標時。
* 已**按下**:當按下滑鼠按鍵時, 請按下或移動控制器的 [選取] 按鈕。

您可以使用反白顯示或調整之類的技術, 為使用者的輸入狀態提供視覺提示。 在 Windows Mixed Reality 中, 您可以找到在 [開始] 功能表和 [應用程式行] 按鈕上將不同輸入狀態視覺化的範例。 

![視覺化觀察狀態、目標狀態和按下狀態的範例](images/640px-interactibleobject-states.png)<br>
*視覺化觀察狀態、目標狀態和按下狀態的範例*

![全像攝影按鈕上的觀察狀態、目標狀態和按下狀態](images/MRTK_InteractableState.png)<br>
*全像攝影按鈕上的觀察狀態、目標狀態和按下狀態*

#### <a name="neardirect-interactions"></a>接近 (直接) 互動

HoloLens 2 支援明確的手寫追蹤輸入, 可讓您與物件互動。 如果沒有 haptic 的意見反應和完美的深度認知, 有時可能很難分辨出手距物件的距離, 或您是否觸及。 請務必提供足夠的視覺提示來傳達物件的狀態, 特別是與全息影像相關。

使用視覺效果意見反應來傳達下列內容:
* **預設值 (觀察)** :物件的預設閒置狀態。
* **滑鼠停留**:當手近于全息全像投影時, 請變更視覺效果來溝通該手的目標為全像投影。 
* **距離和互動點**: 身為手中的全像投影, 設計意見反應來傳達預定的互動點, 以及從物件到手指的距離
* **連絡人開始**:變更視覺效果 (淺色、色彩) 以溝通觸控已發生
* **Grasped**:在 grasped 物件時變更視覺效果 (淺色、色彩)。
* **連絡人端**:觸控結束時變更視覺效果 (淺色、色彩)。

![近乎互動狀態的視覺化範例](images/640px-interactibleobject-states-near.jpg)<br>
*近乎互動狀態的視覺化範例*

[HoloLens 2 中的按鈕](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)顯示將不同輸入互動狀態視覺化的範例。

![HoloLens 2 中的 [pressable] 按鈕範例](images/640px-interactibleobject-pressablebutton-650px2.jpg)<br>
*HoloLens 2 中的 [pressable] 按鈕範例*

在 HoloLens 2 中, 有一個額外的視覺提示, 可改善使用者對深度認知的信心。 當 fingertip 接近物件時, fingertip 上的環形會顯示並相應減少。 環形最後會在按下狀態時聚合到一個點。 此視覺 affordance 可協助使用者瞭解物件的距離。

![Fingertip 環形視覺效果](images/640px-interactibleobject-pressablebutton-650px3.jpg)<br>
*HoloLens 2 中的 Fingertip 環形視覺效果*

![視覺效果意見反應關於手近](images/HoloLens2_Proximity.gif)<br>
*以鄰近範圍方塊為基礎的視覺效果意見反應範例*


### <a name="audio-cue"></a>音訊提示
對於直接的互動, 適當的音訊意見反應可以大幅改善使用者體驗。 使用音訊意見反應來傳達下列內容:
* **連絡人開始**:開始觸控時播放音效
* **連絡人端**:在 touch 端播放音效
* **抓取開始**:抓取開始時播放音效
* **抓取結束**:在抓取結束時播放音效

### <a name="voice-command"></a>語音命令
針對任何可互動物件, 請務必支援替代互動選項。 在預設情況下, 建議您針對任何可互動的物件支援語音命令。 若要改善可搜尋性, 您可以提供滑鼠停留狀態的工具提示。

<img src="images/640px-interactibleobject-voicecommand.jpg" alt="Tooltip for the voice command" title="語音命令的工具提示" width="350"><br/>*語音命令的工具提示*

## <a name="sizing"></a>調整大小
若要確保使用者可以輕鬆地觸及所有可互動物件, 建議您根據其與使用者的距離, 確定可互動符合最小大小 (視覺效果的角度, 通常以度為單位測量)。 視覺角度是以使用者眼和物件之間的距離為依據, 並維持不變, 而目標的實體大小可能會隨著使用者變更的距離而改變。 若要根據與使用者的距離來判斷物件的必要實體大小, 請嘗試使用視覺角度計算機, 例如[這一項](http://elvers.us/perception/visualAngle/)。

以下是最小可互動內容大小的建議。

### <a name="target-size-for-direct-hand-interaction"></a>直接操作的目標大小
| 長途電話 | 視角 | Size |
|---------|---------|---------|
| 45cm  | 不小於2° | 1.6 x 1.6 cm |

![直接操作的目標大小](images/TargetSizingNear.jpg)<br>
*直接操作的目標大小*

建立直接互動的按鈕時, 我們建議使用較大大小的最小值 3.2 x 3.2 cm, 以確保有足夠的空間可包含圖示, 而且可能會有一些文字 * *

| 長途電話 | 最小大小 |
|---------|---------|
| 45cm  | 3.2 x 3.2 cm |

![按鈕的目標大小](images/TargetSizingButtons.png)<br>
*按鈕的目標大小*


### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>右手光線或注視互動的目標大小
| 長途電話 | 視角 | Size |
|---------|---------|---------|
| 2m  | 不小於1° | 3.5 x 3.5 cm |

![右手光線或注視互動的目標大小](images/TargetSizingFar.jpg)<br>
*右手光線或注視互動的目標大小*

## <a name="creating-interactable-object-with-mixed-reality-toolkit-mrtk"></a>使用混合現實工具組 (MRTK) 建立可互動物件

在 **[混合式現實工具](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 組中, 您可以找到可協助您建立可互動物件的一系列 Unity 腳本和 prefabs。 您可以使用這些來讓物件回應各種類型的輸入互動狀態。

* [可互動](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [Button](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [手動互動範例場景](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

MixedRealityToolkit 的標準著色器提供各種選項, 例如**近光源**, 可協助您建立視覺效果和音訊提示。
* [MRTK 標準著色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


## <a name="see-also"></a>另請參閱

* [周框方塊](app-bar-and-bounding-box.md)
* [物件集合](object-collection.md)
* [佈告板和常駐標籤](billboarding-and-tag-along.md)