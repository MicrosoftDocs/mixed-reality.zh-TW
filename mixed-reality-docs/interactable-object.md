---
title: 可互動的物件
description: 按鈕長久以來所用的觸發事件 2D 抽象全球隱喻。 在三維的混合的現實世界中，我們沒有不再侷限於這個抽象層再的世界。
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: 混合的實境、 控制項、 互動、 ui、 ux
ms.openlocfilehash: b0397e00763f70e4caf55a84b6541085e56fafd4
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148747"
---
# <a name="interactable-object"></a>可互動的物件

按鈕長久以來所用的觸發事件 2D 抽象全球隱喻。 在三維的混合的現實世界中，我們沒有不再侷限於這個抽象層再的世界。 任何能**互動的物件**觸發事件。 可互動的物件可以表示為任何項目從咖啡杯資料表在空中浮在球形文字說明。 我們仍執行能用在某些情況下這類對話方塊 UI 如同傳統的按鈕。 按鈕的視覺表示方式取決於內容。

![Interactible 物件](images/640px-interactibleobject-hero-640px.jpg)


## <a name="important-properties-of-the-interactable-object"></a>可互動的物件的重要屬性

### <a name="visual-cue"></a>視覺提示

視覺提示是眼睛光線的形式接收，且 visual 系統處理期間視覺的感應式提示。 由於 visual 系統是主控在許多物種，尤其是人類的視覺提示是大型中發現世界的如何資訊。

在混合實境，全像攝影版的物件會混合使用真實世界的環境，因為它可能會難以了解哪些物件是可互動。 在您的經驗中任何可互動的物件，請務必提供差異化的視覺提示，針對每個輸入的狀態。 這可協助使用者了解您的使用經驗的哪個部分是可互動，並使用一致的互動方法，讓使用者有信心。

#### <a name="far-interactions"></a>遠的互動

任何物件該使用者可以互動視線、 手無限遠的光線，與動作控制器的光線，我們建議您有不同的視覺提示。 這三種輸入狀態：
* **預設值 （觀察）** :預設的閒置狀態的物件。
* **目標 （暫留）** :當物件的目標與視線指標時，手指鄰近性或動作控制器的指標。
* **按下**:當物件已按下使用空中點選手勢、 手指按或動作控制器的 [選取] 按鈕。

您可以使用的技術，例如反白顯示或縮放比例來提供視覺提示使用者輸入的狀態。 在 Windows Mixed Reality，您可以找到視覺化不同輸入的狀態，在 [開始] 功能表和應用程式列按鈕的範例。 

![目標狀態，與按下狀態的視覺化觀察狀態範例](images/640px-interactibleobject-states.png)<br>
*目標狀態，與按下狀態的視覺化觀察狀態範例*

![觀察狀態設為目標的狀態，並在全像攝影版的按鈕上按下狀態](images/MRTK_InteractableState.png)<br>
*觀察狀態設為目標的狀態，並在全像攝影版的按鈕上按下狀態*

#### <a name="neardirect-interactions"></a>Near(direct) 互動

HoloLens 2 支援相互連貫的手動追蹤可讓您與物件互動的輸入。 不含 haptic 意見反應和 perception 完美的深度，有時很難判斷您的手距離是從物件，或您是否會觸碰。 請務必提供足夠的視覺提示來溝通狀態的物件，特別在全像投影的關聯性中實際操作。

您可以使用視覺化回饋，通訊下列：
* **預設值 （觀察）** :預設的閒置狀態的物件。
* **將滑鼠移至**:手狀即將全像 」，這是進行通訊，手動變更視覺效果的目標全像圖。 
* **距離和的互動點**: 手狀接近全像圖時，設計通訊預計的互動點，以及如何遠離物件是指的意見反應
* **請連絡 Begin**:變更視覺效果 （光線，色彩） 進行通訊的觸控發生
* **Grasped**:變更視覺效果 （光線，色彩） grasped 物件的時機。
* **請連絡結束**:變更視覺效果 （光線，色彩） 觸控時結束。

![視覺化附近互動狀態範例](images/640px-interactibleobject-states-near.jpg)<br>
*視覺化附近互動狀態範例*

[HoloLens 2 中的按鈕](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)示範視覺化不同輸入的互動狀態。

![HoloLens 2 pressable 按鈕的範例](images/640px-interactibleobject-pressablebutton-650px2.jpg)<br>
*HoloLens 2 pressable 按鈕的範例*

HoloLens 2 中沒有可改善使用者的信心，深度認知上其他視覺提示。 上寫寫看信號出現，並相應減少，因為寫寫看即將來臨的物件。 按下狀態的一個點到最後聚合信號。 此視覺化功能可見性可協助使用者了解物件之間的距離。

![寫寫看環狀視覺效果](images/640px-interactibleobject-pressablebutton-650px3.jpg)<br>
*HoloLens 2 寫寫看環狀視覺效果*

![在手相近的視覺化回饋](images/HoloLens2_Proximity.gif)<br>
*根據鄰近-週框方塊的視覺化回饋的範例*


### <a name="audio-cue"></a>音訊提示
直接手動互動，適當的音訊意見反應可以大幅改善使用者體驗。 使用來傳達下列音訊意見反應：
* **請連絡開始**:觸控式開始時播放音效
* **連絡人的結束**:播放音效觸控端
* **抓取開始**:擷取啟動時播放音效
* **抓取結束**:播放音效抓取端

### <a name="voice-command"></a>語音命令
任何可互動的物件，請務必支援替代的互動選項。 在預設情況下，建議您使用支援語音命令是可互動的任何物件。 若要改善探索能力，您可以提供工具提示上暫留狀態。

<img src="images/640px-interactibleobject-voicecommand.jpg" alt="Tooltip for the voice command" title="語音命令的工具提示" width="350"><br/>*語音命令的工具提示*

## <a name="sizing"></a>調整大小
為了確保可互動的所有物件都可以輕鬆地都是觸及使用者建議確保可互動的符合根據它會放置在使用者的距離的最小大小 （通常以視覺化角度的度數為單位）。 Visual 角度的度數為單位根據使用者與物件之間的距離，並會保持不變，而目標的實體大小從使用者的變更，可能會變更為之間的距離。 若要判斷所需的實體大小，確定和程度的距離為基礎的物件視覺化的角度會嘗試使用計算機，例如： http://elvers.us/perception/visualAngle/

以下是可互動內容的最小大小的建議

### <a name="target-size-for-direct-hand-interaction"></a>直接手動互動的目標大小
| 距離 | 檢視角度 | 大小 |
|---------|---------|---------|
| 45 cm  | 不小於 2 ° | 1.6 x 1.6 cm |

![直接手動互動的目標大小](images/TargetSizingNear.jpg)<br>
*直接手動互動的目標大小*

在建立時直接互動的按鈕，我們建議您較大大小下限為 3.2 x 3.2 cm，以確保有足夠空間來容納圖示和潛在某些文字 * *

| 距離 | 最小大小 |
|---------|---------|
| 45 cm  | 3.2 x 3.2 cm |

![按鈕的目標大小](images/TargetSizingButtons.png)<br>
*按鈕的目標大小*


### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>目標手光線的大小或視線互動
| 距離 | 檢視角度 | 大小 |
|---------|---------|---------|
| 2m  | 不小於 1 ° | 3.5 x 3.5 cm |

![目標手光線的大小或視線互動](images/TargetSizingFar.jpg)<br>
*目標手光線的大小或視線互動*

## <a name="creating-interactable-object-with-mixed-reality-toolkit-mrtk"></a>建立可互動的物件與混合實境工具組 (MRTK)

在  **[混合實境 Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)** ，您可以找到 Unity 指令碼的一系列 prefabs，可協助您建立可互動的物件。 您可以使用這些物件的各種類型的輸入的互動狀態回應。

* [Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [Button](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [手動互動範例場景](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

提供各種選項，例如 MixedRealityToolkit 的標準著色器**鄰近 light**可協助您建立視覺與音訊提示。
* [MRTK 標準著色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


## <a name="see-also"></a>另請參閱

* [週框方塊](app-bar-and-bounding-box.md)
* [物件集合](object-collection.md)
* [佈告板和常駐標籤](billboarding-and-tag-along.md)