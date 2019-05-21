---
title: 定期的資料表的項目
description: 定期資料表項目是開放原始碼的範例應用程式從 Microsoft 的混合實境設計實驗室中，您可以了解如何使用各種使用的物件集合的介面型別來配置在 3D 空間中物件的陣列。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，設計，範例應用程式，控制項
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596692"
---
# <a name="periodic-table-of-the-elements"></a>定期的資料表的項目

>[!NOTE]
>這篇文章討論探勘的範例，我們已在中建立[混合實境設計實驗室](https://github.com/Microsoft/MRDesignLabs_Unity)，我們分享我們所獲得的經驗相關的位置和建議混合實境應用程式開發。 當我們新的探索，就會持續改進我們的設計相關的文章和程式碼。

[項目的周期資料表](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)是 Microsoft 的混合實境設計實驗室一個開放原始碼的範例應用程式。 與此專案中，您可以了解如何使用各種使用的介面型別來配置在 3D 空間中物件的陣列 **[物件集合](object-collection.md)** 。 也了解如何建立可互動回應 HoloLens 的標準輸入的物件。 您可以使用此專案的元件建立您自己也就是混合實境應用程式體驗。

![時段的資料表的項目應用程式](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a>關於應用程式

化學的項目和其屬性，在 3D 空間中的每個項目的周期資料表以視覺化方式呈現。 它會合併 HoloLens 基本互動，例如視線和空中點選。 使用者可以了解動畫效果的 3D 模型的項目。 它們以視覺化方式可以了解的項目 electron 殼層和其核心-質子與 neutrons 所組成。

## <a name="background"></a>背景

我第一次發生 HoloLens 之後，定期資料表 」 應用程式是我知道我想要在混合實境中進行實驗與了解。 因為每個項目會以文字顯示的許多資料點，我認為它是絕佳的主題來探索在 3D 空間中的印刷樣式組合。 正在將視覺化項目的 electron 模型是此專案的另一個有趣的部分。

## <a name="design"></a>設計

針對定期資料表的預設檢視，我想像的情況會包含每個元素的 electron 模型的立體方塊。 每個方塊的介面是半透明，讓使用者無法取得項目的磁碟區的約略的構念。 視線和空中點選一下，使用者可以開啟每個項目的詳細檢視。 若要讓資料表檢視和詳細資料檢視之間的轉換，平滑且自然，我進行類似的方塊，在現實生活中開啟實體互動。

![設計草圖](images/640px-sketch20170406.jpg)<br>
*設計草圖*

在詳細資料檢視中，我想要視覺化具有完美地呈現的文字在 3D 空間中的每個項目資訊。 動畫的 3D electron 模型會顯示在中心區域，並可從不同角度檢視。

![互動](images/640px-periodictable-interaction.jpg)

![Prototypes](images/640px-periodictable-prototypes.jpg)<br>
*互動原型*

使用者可以空中點選底部的資料表上的按鈕變更介面的類型-它們可以平面、 cylinder、 球體和散佈圖之間切換。

## <a name="common-controls-and-patterns-used-in-this-app"></a>常見控制項和使用此應用程式中的模式

### <a name="interactable-object-button"></a>可互動的物件 （按鈕）

[可互動的物件](interactable-object.md)是基本的 HoloLens 輸入可以回應的物件。 它可做為 prefab/指令碼可以輕鬆地套用至任何物件。 比方說，您可以讓場景的咖啡 cup 互動，並回應的輸入，例如視線、 空中點選瀏覽和操作的筆勢。 [深入了解](interactable-object.md)

![nteractable 物件](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>物件集合

[物件集合](object-collection.md)是一種物件，可協助您配置不同圖形中的多個物件。 它支援平面、 cylinder、 球體和散佈圖。 您可以設定其他屬性，例如半徑、 資料列數和間距。 [深入了解](object-collection.md)

![物件集合](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a>Fitbox

根據預設，全像投影會置於 gazing 使用者的所在位置目前啟動應用程式。 這有時會導致不想要的結果，例如背後牆或中間的資料表置入全像投影。 Fitbox 可讓使用者使用視線判斷全像放置的位置。 它會使用簡單的 PNG 影像材質可輕鬆地自訂您自己的映像或 3D 物件。

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a>技術詳細資料

您可以找到指令碼和 prefabs 定期資料表項目應用程式[混合實境設計 Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)。

## <a name="application-examples"></a>應用程式範例

以下是一些您可以利用此專案中的元件建立的想法。

### <a name="stock-data-visualization-app"></a>內建的資料視覺效果應用程式

您可以使用相同的控制項和互動模型做為定期資料表的項目範例，來建置應用程式以視覺化方式顯示股票市場資料。 此範例會使用物件集合的控制項來配置更低的球面的圖形中的內建資料。 您可以想像，無法顯示的每個股票的其他資訊以有趣的方式的詳細資料檢視。

![應用程式範例：財務 (3 之 1)](images/640px-periodictable-applicationexamples-finance1.jpg)

![應用程式範例：財務 (3 之 2)](images/640px-periodictable-applicationexamples-finance2.jpg)

![應用程式範例：財務 (3 之 3)](images/640px-periodictable-applicationexamples-finance3.jpg)<br>
*如何定期資料表的項目範例應用程式中使用的物件集合無法使用的財務應用程式中的範例*

### <a name="sports-app"></a>運動應用程式

這是視覺化使用物件集合和項目範例應用程式定期從其他元件的運動資料的範例。

![應用程式範例：運動 (3 之 1)](images/640px-periodictable-applicationexamples-sports0.jpg)

![應用程式範例：運動 (3 之 2)](images/640px-periodictable-applicationexamples-sports1.jpg)

![應用程式範例：運動 (3 之 3)](images/640px-periodictable-applicationexamples-sports3.jpg)<br>
*運動應用程式中使用的物件集合中的項目範例 appcould 定期資料表的使用方式範例*

## <a name="about-the-author"></a>關於作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>盾 Yoon Park</b><br>UX 設計工具 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>另請參閱

* [可互動的物件](interactable-object.md)
* [物件集合](object-collection.md)
