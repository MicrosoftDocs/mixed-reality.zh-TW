---
title: 印刷樣式
description: 文字是在您的應用程式體驗中傳遞資訊的重要元素。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality，設計，風格，字型，印刷樣式，ui，ux
ms.openlocfilehash: 9664d355e941d800ac1ac862860fc5889b6b7686
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437414"
---
# <a name="typography"></a>印刷樣式

![HoloLens 中的印刷樣式範例](images/typography-cover.png)<br>


文字是在您的應用程式體驗中傳遞資訊的重要元素。 就像2D 螢幕上的印刷樣式一樣，目標是要清楚易懂。 有了混合實境的三維外觀比例，就有機會以更佳的方式來影響文字和整體使用者體驗。

當我們談論3D 中的類型時，通常會考慮體積型3D 文字。 除了部分商標設計和一些其他有限的應用程式以外，已延伸的文字通常會降低文字的可讀性。 雖然我們是設計3D 的經驗，但我們使用2D 做為型別，因為它比較容易閱讀，而且可讀性更高。

在 HoloLens 中，型別是根據加總色彩系統，使用淡入的影像來建立的。 就像其他的全息影像一樣，您可以將 type 放在實際環境中，而且可以從任何角度來觀察世界。 類型和環境之間的[視差](https://en.wikipedia.org/wiki/Parallax)效果也會增加體驗的深度。

## <a name="typography-in-mixed-reality"></a>混合現實中的印刷樣式

混合式現實中的印刷樣式規則與其他任何地方都沒有不同。 實體世界和虛擬世界中的文字都必須清晰易懂。 文字可以在牆上或疊加在實體物件上。 它可以與數位使用者介面一併浮動。 無論內容為何，我們會套用相同的印刷樣式規則來進行讀取和辨識。

### <a name="create-clear-hierarchy"></a>建立明確階層

使用不同的類型大小和加權來建立對比和階層。 在整個應用程式體驗中定義型別斜坡並遵循它，將會提供具有一致資訊階層的絕佳使用者體驗。

![型別](images/typography-ramp-1000px.jpg) 的範例<br>
*定義您的型別斜坡，並在整個應用程式體驗中追蹤*

### <a name="limit-your-fonts"></a>限制字型

避免在單一內容中使用兩個以上的不同字型系列。 這會破壞您的體驗的顏色和一致性，並使取用資訊變得更困難。 在 HoloLens 中，由於資訊會重迭到實體環境的頂端，因此使用太多字型樣式將會降低體驗。 Segoe UI 是所有 Microsoft 數位設計的字型。 它在 Windows Mixed Reality shell 中是以一致的方式使用。 您可以從[Windows 設計工具組頁面](https://docs.microsoft.com/windows/uwp/design-downloads/)下載 Segoe UI 字型檔案。

[Segoe UI 字樣的詳細資訊](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a>避免精簡字型粗細

請避免針對頁首建議42pt 下的類型大小使用 light 或 semilight 做字型粗細，因為精簡的垂直筆劃將會震動並降低可讀性。 具有足夠筆觸粗細的新式字型運作良好。 例如，在 HoloLens 中使用標準或粗權數時，Helvetica 和 Arial 會非常清晰。

### <a name="color"></a>色彩

在 HoloLens 中，因為全息影像是以加光源系統來建立，所以白色文字會非常清晰。 您可以在 [開始] 功能表和應用程式行上找到白色文字的範例。 即使在 HoloLens 上沒有背面的白色文字運作良好，但是複雜的實體背景可能會使型別難以閱讀。 若要改善使用者的焦點，並將實體背景的干擾降到最低，建議您在深色或彩色背景板上使用白色文字。

<br>


![建議您在深色或彩色背景板上使用白色文字。](images/typography-whiteonblack2-1000px.jpg)
*深色或彩色背板上的白色文字範例。*
<br>

若要使用深色文字，您應該使用明亮的背板讓它變成可讀取。 在 [加法色彩系統] 中，黑色會顯示為 [透明]。 這表示您將無法在沒有彩色背景板的情況下看到黑色文字。

:::row:::
    :::column:::
        ![黑色文字範例](images/typography-whiteonblack.png)<br>
        *黑色和黑白白色文字的白色範例*<br>
    :::column-end:::
    :::column:::
        ![黑色文字範例](images/640px-typography-blackonwhite.jpg)<br>
        *系統應用程式中的黑色文字範例-儲存和設定*<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="recommended-font-size"></a>建議的字型大小

如您所見，我們在 PC 或 tablet 裝置上使用的大小（通常介於12–32pt 填補之間）看起來相當小，距離2計量。 這取決於每個字型的特性，但一般來說，建議的最小觀賞角度和可讀性的字型高度是以我們的使用者研究研究為基礎的0.35 °-0.4 °/12.21-13.97mm。 大約 35-40pt，並在 Unity 頁面的[文字中](text-in-unity.md)引進縮放比例。 

若要在 0.45 m （45cm）附近互動，最小的可感知字型的視圖角度和高度是0.4 °-0.5 °/3.14 – 3.9 mm。 其大約是以 Unity 中的[文字](text-in-unity.md)引進的調整因數 9 12pt。

![近和遠互動範圍](images/typography-distance-1000px.jpg)
*內容*

### <a name="the-minimum-legible-font-size"></a>最小的清晰字型大小
| 長途電話 | 視角 | 文字高度 | 字型大小 * * |
|---------|---------|---------|---------|
| 45cm （直接操作距離） | 0.4 °-0.5 ° | 3.14 –3.9 毫米 | 8.9 – 11.13 pt |
| 2m | 0.35 °-0.4 ° | 12.21 – 13.97 mm | 34.63-39.58 pt |


### <a name="the-comfortably-legible-font-size"></a>舒適的字型大小
| 長途電話 | 視角 | 文字高度 | 字型大小 * * |
|---------|---------|---------|---------|
| 45cm （直接操作距離） | 0.65 °-0.8 ° | 5.1-6.3 mm | 14.47-17.8 pt |
| 2m | 0.6 °-0.75 ° | 20.9-26.2 mm | 59.4-74.2 pt |


Segoe UI （Windows 的預設字型）在大多數情況下都很好用。 不過，請避免使用大小較小的淡或半透明字型系列，因為精簡的垂直筆劃將會震動，且會降低可讀性。 具有足夠筆觸粗細的新式字型運作良好。 例如，Helvetica 和 Arial 的外觀美觀，在 HoloLens 中具有一般或粗權數。

**如需 Unity 中文字大小計算的詳細資訊，請參閱[unity 中的文字](text-in-unity.md)**

![視圖角度](images/Text_In_Unity_ViewingAngle.jpg)
*視圖距離、角度和文字高度*

<br>

---

## <a name="resources"></a>資源

:::row:::
    :::column:::
    ### <a name="segoe-fontshttpsdownloadmicrosoftcomdownload1bc1bcf071a-78ee-4968-acbe-15461c274b61segoe20fonts20v1705zipbr"></a>[Segoe 字型](https://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)<br>
    （Zip 檔案）<br>
    ### <a name="hololens-fonthttpsdownloadmicrosoftcomdownload38d38d659e2-4b9c-413a-b2e7-1956181dc427hololens20fontzipbr"></a>[HoloLens 字型](https://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)<br>
    （Zip 檔案）<br>
    <br>
    *影像： HoloLens 字型提供您在 Windows Mixed Reality 中使用的符號字元。*
    :::column-end:::
        :::column:::
        ![HoloLens 字型提供您在 Windows Mixed Reality 中使用的符號字元](images/hololensmdl2symbols.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="see-also"></a>請參閱
* [Unity 中的文字](text-in-unity.md)
* [色彩、光線和材質](color,-light-and-materials.md)
