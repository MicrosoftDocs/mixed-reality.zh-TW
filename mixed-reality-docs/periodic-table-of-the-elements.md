---
title: 元素週期表
description: 專案的定期資料表是來自 Microsoft Mixed Reality 設計實驗室的開放原始碼範例應用程式, 您可以在其中瞭解如何使用物件集合, 在3D 空間中配置具有各種介面類別型的物件陣列。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、設計、範例應用程式、控制項
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525293"
---
# <a name="periodic-table-of-the-elements"></a>元素週期表

>[!NOTE]
>本文討論我們在[混合現實設計實驗室](https://github.com/Microsoft/MRDesignLabs_Unity)中建立的探索範例, 這是我們分享我們學習的相關資訊, 並提供混合現實應用程式開發的建議。 我們的設計相關文章和程式碼將會隨著我們進行新的探索而演進。

[元素的定期資料表](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)是來自 Microsoft 混合現實設計實驗室的開放原始碼範例應用程式。 與此專案中，您可以了解如何使用各種使用的介面型別來配置在 3D 空間中物件的陣列 **[物件集合](object-collection.md)** 。 另請瞭解如何建立可回應 HoloLens 標準輸入的可互動物件。 您可以使用這個專案的元件來建立自己的混合現實應用程式體驗。

![Elements 應用程式的期間資料表](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a>關於應用程式

專案的定期資料表會在3D 空間中將化學元素和其每個屬性視覺化。 它結合了 HoloLens 的基本互動, 例如注視和空中。 使用者可以瞭解具有動畫3D 模型的元素。 他們可以視覺化方式瞭解元素的 electron shell 和其系統核心, 這是由 protons 和 neutrons 所組成。

## <a name="background"></a>背景

在我第一次體驗 HoloLens 之後, 週期性資料表應用程式就是我知道, 我想要在混合現實中進行實驗。 由於每個元素都有許多以文字顯示的資料點, 因此我認為在3D 空間中探索印刷樣式是很重要的主題。 能夠將元素的 electron 模型視覺化, 是這個專案的另一個有趣的部分。

## <a name="design"></a>設計

就定期資料表的預設觀點而言, 我想到了三維方塊, 其中包含每個元素的 electron 模型。 每個方塊的表面都是半透明的, 讓使用者能夠大致瞭解元素的磁片區。 有了注視和空中碰, 使用者就可以開啟每個元素的詳細觀點。 為了讓資料表視圖和詳細資料檢視之間的轉換順暢且自然, 我使其類似于在真實生活中開啟的實際互動。

![設計草圖](images/640px-sketch20170406.jpg)<br>
*設計草圖*

在詳細資料檢視中, 我想要使用3D 空間中的精美轉譯文字, 將每個元素的資訊視覺化。 動畫 3D electron 模型會顯示在中央區域, 而且可以從不同角度來查看。

![互動](images/640px-periodictable-interaction.jpg)

![@](images/640px-periodictable-prototypes.jpg)<br>
*互動原型*

使用者可以藉由使用下表底部的按鈕來變更表面類型-它們可以在平面、圓柱、球面和散佈圖之間切換。

## <a name="common-controls-and-patterns-used-in-this-app"></a>此應用程式中使用的通用控制項和模式

### <a name="interactable-object-button"></a>可互動物件 (按鈕)

[可互動物件](interactable-object.md)是可回應基本 HoloLens 輸入的物件。 它是以 prefab/腳本的形式提供, 您可以輕鬆地將它套用至任何物件。 例如, 您可以在場景中可互動, 並回應像是注視、空中碰、導覽和操作手勢等輸入。 [深入了解](interactable-object.md)

![nteractable 物件](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>物件集合

[物件集合](object-collection.md)是一種物件, 可協助您在各種不同的圖形中配置多個物件。 它支援平面、圓柱、球面和散佈圖。 您可以設定其他屬性, 例如 radius、資料列數目和間距。 [深入了解](object-collection.md)

![物件集合](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a>Fitbox

根據預設, 在應用程式啟動時, 會將全息影像放在撥雲見日使用者的位置。 這有時會導致不想要的結果, 例如將全息影像放在牆後方或在資料表的中間。 Fitbox 可讓使用者使用注視來決定要放置全息的位置。 這是使用簡單的 PNG 影像材質所建立, 您可以使用自己的影像或3D 物件輕鬆地自訂它。

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a>技術詳細資料

您可以在[混合現實設計實驗室 GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)上找到適用于 Elements 應用程式的定期資料表的腳本和 prefabs。

## <a name="application-examples"></a>應用程式範例

以下是您可以利用此專案中的元件來建立的一些概念。

### <a name="stock-data-visualization-app"></a>股票資料視覺效果應用程式

使用與專案範例的定期資料表相同的控制項和互動模型, 您可以建立可將股票市場資料視覺化的應用程式。 這個範例會使用物件集合控制項來配置球面圖形中的股票資料。 您可以想像一下詳細資料檢視, 其中每個股票的其他資訊可能會以有趣的方式顯示。

![應用程式範例:財務 (1/3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![應用程式範例:財務 (2/3)](images/640px-periodictable-applicationexamples-finance2.jpg)

![應用程式範例:財務 (3/3)](images/640px-periodictable-applicationexamples-finance3.jpg)<br>
*如何在財務應用程式中使用在專案範例應用程式的定期資料表中使用的物件集合範例*

### <a name="sports-app"></a>運動應用程式

這是使用專案範例應用程式的定期資料表中的物件集合和其他元件來視覺化運動資料的範例。

![應用程式範例:運動 (1/3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![應用程式範例:運動 (2/3)](images/640px-periodictable-applicationexamples-sports1.jpg)

![應用程式範例:運動 (3/3)](images/640px-periodictable-applicationexamples-sports3.jpg)<br>
*如何在運動應用程式中使用 appcould 元素範例的定期資料表中所使用的物件集合範例*

## <a name="about-the-author"></a>關於作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>盾 Yoon 公園</b><br>UX 設計工具@Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>另請參閱

* [可互動的物件](interactable-object.md)
* [物件集合](object-collection.md)
