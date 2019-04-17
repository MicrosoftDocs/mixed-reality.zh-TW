---
title: 可互動的物件
description: 按鈕長久以來所用的觸發事件 2D 抽象全球隱喻。 在三維的混合的現實世界中，我們沒有不再侷限於這個抽象層再的世界。
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 混合的實境、 控制項、 互動、 ui、 ux
ms.openlocfilehash: f349d21707375690e00b0f7e465634c62be1537e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594760"
---
# <a name="interactable-object"></a>可互動的物件

按鈕長久以來所用的觸發事件 2D 抽象全球隱喻。 在三維的混合的現實世界中，我們沒有不再侷限於這個抽象層再的世界。 任何能**互動的物件**觸發事件。 可互動的物件可以表示為任何項目從咖啡杯資料表在空中浮在球形文字說明。 我們仍執行能用在某些情況下這類對話方塊 UI 如同傳統的按鈕。 按鈕的視覺表示方式取決於內容。

![Interactible 物件英雄影像](images/640px-interactibleobject-hero-640px.jpg)


在  **[混合實境 Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)**，我們建立了一系列的 Unity 指令碼和 prefabs，可協助您建立可互動的物件。 您可以使用這些來建立任何類型的使用者可以與之互動，使用這些標準的互動狀態的物件： 觀察，設為目標，並按下。 您可以輕鬆自訂視覺效果的設計，與您自己的資產。 詳細的動畫可以自訂所建立，並指派對應的動畫剪輯，在 Unity 的 [動畫] 控制器中的互動狀態，或使用 offset 和小數位數。 


## <a name="visual-feedback-for-the-different-input-interaction-states"></a>針對不同的輸入的互動狀態的視覺回饋

在混合實境，全像攝影版的物件會混合使用真實世界的環境，因為它可能會難以了解哪些物件是可互動。 在您的經驗中任何可互動的物件，請務必提供差異化的視覺化回饋，針對每個輸入的狀態。 這可協助使用者了解您的使用經驗的哪個部分是可互動，並使用一致的互動方法，讓使用者有信心。

任何物件該使用者可以與互動，我們建議使用有不同的視覺回饋，針對這三個輸入狀態：
* **觀察**:預設的閒置狀態的物件。
* **目標**:當物件的目標與視線指標時，手指鄰近性或動作控制器的指標。
* **按下**:當物件已按下使用空中點選手勢、 手指按或動作控制器的 [選取] 按鈕。

![全像攝影版的按鈕](images/640px-interactibleobject-holographicbutton-650px.jpg)<br>
*觀察狀態設為目標的狀態，並按下狀態*

在 Windows Mixed Reality，您可以找到視覺化不同輸入的狀態，在 [開始] 功能表和應用程式列按鈕的範例。 您可以使用的技術，例如反白顯示或縮放比例提供視覺化回應使用者輸入的狀態。

在 HoloLens 2 中，因為它支援完全相互連貫的手動追蹤輸入，我們可以提供根據傳遞給鄰近的額外提供。 [HoloLens 2 中的按鈕](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)顯示此範例。

![Pressable 按鈕](images/640px-interactibleobject-pressablebutton-650px.jpg)<br>




## <a name="interactable-object-samples"></a>可互動的物件範例

### <a name="mesh-button"></a>網狀結構按鈕

![網狀結構按鈕](images/640px-interactibleobject-meshbutton.jpg)

這些是可互動的物件為使用基本類型和匯入的 3D 網格的範例。 您可以輕鬆地指派不同的規模、 位移和色彩值來回應每個輸入的互動狀態。

### <a name="toolbar"></a>工具列

![工具列](images/640px-interactibleobject-toolbar.jpg)

工具列是廣泛使用的模式，在混合的實境體驗中。 它是簡單的按鈕與其他的行為集合，例如[Billboarding 和 tag-along](billboarding-and-tag-along.md)。 此範例會使用從 MixedRealityToolkit Billboarding 和 tag-along 指令碼。 您可以控制詳細的行為，包括距離，移動速度和臨界值。

### <a name="traditional-button"></a>傳統的按鈕

![傳統的按鈕](images/640px-interactibleobject-traditionalbutton.jpg)

此範例顯示傳統的 2D 樣式 按鈕。 每個輸入的狀態具有稍有不同的深度和動畫屬性。

### <a name="other-examples"></a>其他範例

![推播 按鈕](images/640px-interactibleobject-pushbutton.jpg)<br>
*推播 按鈕*
<br>
![真實生活物件](images/640px-interactibleobject-reallifeobject.jpg)<br>
*真實物件*

使用 HoloLens，您可以利用的實體空間。 想像一下全像攝影版的按鈕，在實體的塗鴉牆上。 或如何在實際的資料表上的咖啡 cup？ 使用從模型化軟體匯入的 3D 模型，我們可以建立可互動的物件，類似於現實生活中的物件。 因為它是數位物件時，我們可以新增神奇的互動。

## <a name="interactable-object-in-mixed-reality-toolkit"></a>混合實境工具組中的互動物件
您可以找到[Interactable 範例物件混合實境工具組中](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)


## <a name="see-also"></a>另請參閱
* [在混合的實境 Toolkit Unity pressable 按鈕](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [物件集合](object-collection.md)
* [告示板和 tag-along](billboarding-and-tag-along.md)
