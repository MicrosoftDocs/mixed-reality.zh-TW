---
title: 手部功能表
description: 快顯功能表可讓使用者快速地為常用的函式帶出手動連接的 UI。 這些是我們的最佳做法和功能表的建議。
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: 手形、功能表、按鈕、快速存取、版面配置
ms.openlocfilehash: d1d15b36bab2ca2082ca4ba91b9c64862893f80c
ms.sourcegitcommit: fef42e2908e49822f2d13b05d2f9260bf0d72158
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "86061163"
---
# <a name="hand-menu"></a>手部功能表

![Ulnar 端位置](images/UX/UX_Hero_HandMenu.jpg)

[手形] 功能表是 HoloLens 2 中最獨特的 UX 模式之一。 它可讓您快速啟動右手附的 UI。 因為它可隨時存取，而且可以輕鬆地顯示及隱藏，所以很適合用於快速動作。

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

您會在下面的清單中找到使用 [手形] 功能表的建議最佳作法。 您也可以在[MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)中找到示範 [手形] 功能表的範例場景。

<br>


---

## <a name="best-practices"></a>最佳作法
**讓按鈕數目保持小** 

由於已鎖定的功能表和眼睛之間的距離，以及使用者傾向于隨時專注于相對較小的視覺區域（視覺效果的 attentional 錐形大約是10度），因此建議您將按鈕數目保持為小。 根據我們的探索，有三個按鈕的資料行，即使在使用者將其手移至 FOV 的中心時，也會將所有內容都保存在視野中（FOV）。 

**利用快顯功能表進行快速動作** 

引發 arm 並維護位置，很容易就會造成 arm 疲勞。 針對需要短暫互動的功能表，使用手動鎖定的方法。 如果您的功能表很複雜，而且需要擴充的互動時間，請考慮改為使用世界鎖定或主體鎖定。 

**按鈕/面板角度**

功能表應該以相反的肩和中間的方式來表示：這可讓自然手移動以相反的方式與功能表互動，並在觸及按鈕時避免任何不難或不舒服的位置。 

**考慮支援一次性或免手操作**

請勿假設這兩個使用者都一律可以使用。 當一或兩個手無法使用時，請考慮各種內容，並確定您的設計帳戶適用于這些情況。 若要支援單次功能表，您可以嘗試將功能表位置從 [手動鎖定] 轉換為 [世界鎖定] （當手翻轉時）。 針對無人參與的案例，請考慮使用語音命令來叫用快顯功能表。

**避免在手腕（系統首頁按鈕）附近新增按鈕**

如果功能表按鈕太靠近 [首頁] 按鈕，則在與 [滑鼠] 功能表互動時，可能會不小心觸發。

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a>具有大型和複雜 UI 控制項的快顯功能表
<img src="images/UX/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
建議您限制在連接功能表上的按鈕或 UI 控制項數目。 這是因為與大量 UI 元素的擴充互動可能會導致 arm 疲勞。 如果您的經驗需要大型功能表，請提供一種簡單的方式，讓使用者可以輕鬆地鎖定功能表。 我們建議的一項技巧，就是在手離開或翻轉使用者時，將功能表向外鎖定。 第二種方法是讓使用者直接抓取功能表。 當使用者放開功能表時，功能表應該是「世界鎖定」。 如此一來，使用者可以在一段頗長的時間內輕鬆且放心地與各種 UI 專案互動。 

當功能表為 [世界鎖定] 時，請務必提供一種方式來移動功能表，並在不再需要時關閉功能表。 藉由在功能表的側邊或頂端提供控點，讓功能表變成可移動。 新增 [關閉] 按鈕以允許關閉功能表。 [允許] 功能表在使用者手上臉部時，重新附加至手邊。 我們也建議要求使用者 gazes，以防止啟用錯誤（請參閱下文）。

**顯示可用性問題的大型功能表**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

**在手上的世界鎖定功能表**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

**手動抓取 & 提取至世界-鎖定功能表**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]


## <a name="how-to-prevent-false-activation"></a>如何防止啟用錯誤

如果您只使用 palm 作為事件來觸發快顯功能表，它可能會在您不需要時意外出現（誤報），因為人們會刻意（用於通訊和物件操作）和無意地移動其手。 若要減少錯誤的啟用，請新增一個額外的步驟，除了 palm 事件以外，叫用快顯功能表（例如完全開啟的手指，或使用者刻意撥雲見日的手勢）。

**需要一般 Palm**

藉由要求一般的開放式手勢，您可以防止在環境中進行通訊時，使用者操作物件或手勢時可能發生的錯誤啟用。 

**需要注視**

藉由要求使用者注視（使用眼睛眼或列印頭），它會防止錯誤的啟用，因為使用者必須故意將他們的注意力直接導向至第二個啟動步驟（使用可微調的距離閾值來允許使用者輕鬆）。  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a>手形功能表位置最佳做法

在「人為剖析」中，ulnar nerve 是在 ulna 骨骼附近執行的 nerve。 Ulna 是在 forearm 中找到的長型骨骼，會從肘形延伸到最小的手指。

以下是根據我們的探勘所建議的2個位置：


:::row:::
    :::column:::
        ![Ulnar 端位置](images/UlnarSideHandMenu.gif)<br>
        **Ulnar 內部 palm**<br>
        這個位置是可靠的，因為手不會彼此重迭。 這對於精確的手勢偵測和追蹤非常重要。
    :::column-end:::
    :::column:::
        ![Ulnar 端位置](images/UlnarAboveHandMenu.gif)<br>
        **B. Ulnar 以上的手勢**<br>
        這個位置非常適合使用者，因為他們不需要使其 arm 太多而無法與功能表進行互動。 建議您將功能表**13cm**放在 palm 上方，並對齊 ulnar palm 內的按鈕。 [閱讀更多最佳按鈕大小](interactable-object.md)<br>
        <br>
        基於技術原因，我們建議您使用一個必要的實作為此位置：開發人員必須凍結功能表一次，使用者的手勢才會與之互動。 這可避免 jitteriness 重迭手，同時也允許以更快的按鈕為目標。<br>
        <br>
        HoloLens 2 攝影機會在彼此分開時識別正確的手。 任何重迭的手可能會導致手中的功能表遠離錨點位置。<br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a>不建議的功能表位置
我們已使用不同的功能表配置和位置完成使用者研究，**不建議**使用下列功能表位置，尋找下列各項研究的缺點：


:::row:::
    :::column:::
        ![上方 arm](images/AboveArm.gif)<br>
        **Arm 之上**<br>
        1-不容易維護良好的手追蹤<br>
        2-因非自然位置而造成使用者疲勞
    :::column-end:::
    :::column:::
        ![上手指](images/AboveFingers.gif)<br>
        **上手指**<br>
        1-手疲勞，因為有長時間保留手<br>
        2-追蹤索引和中間手指的問題
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![上方的 palm](images/handCenter.gif)<br>
        **上方-中心 palm**<br>
        1-因手迭而發生的追蹤問題<br>
        2-手疲勞，因為長期保持手，以便與功能表互動
    :::column-end:::
    :::column:::
        ![熱門 Fingertip ](images/TopFingerTip.gif) **熱門 Fingertip**<br>
        1-手追蹤問題<br>
        2-從保持在正常狀態的手中疲勞<br>
        3-因手指之間的空間有限而導致按下其他手指的按鈕時發生問題
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Arm 背面](images/BackOfTheArm.gif)<br>
        **Arm 背面**<br>
        1-不小心可以觸發 [首頁] 按鈕<br>
        2-不是自然或舒適的位置
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a>適用于 Unity 的 MRTK （混合現實工具組）中的手形功能表
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 提供快顯功能表的腳本和範例場景。 HandConstraintPalmUp 規劃求解腳本可讓您使用各種可設定的選項，將任何物件附加至手中。 MRTK 的功能表範例包含有用的選項，例如可防止啟用 false 的一般 palm 和注視需求。

* [手形功能表檔](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)
* [手形功能表範例場景](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

您可以使用 MRTK 範例中樞應用程式來試用 HoloLens 2 中的功能表範例。 
* [MRTK 範例中樞中的手形功能表場景](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---


## <a name="see-also"></a>另請參閱

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
