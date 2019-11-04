---
title: 手形功能表
description: 快顯功能表可讓使用者快速地為常用的函式帶出手動連接的 UI。 這些是我們的最佳做法和功能表的建議。
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: 手形、功能表、按鈕、快速存取、版面配置
ms.openlocfilehash: ee958806ac462535b33164bb4faa4bf1aa29e709
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439249"
---
# <a name="hand-menu"></a>手形功能表

![Ulnar 端位置](images/MRTK_UX_HandMenu.png)

快顯功能表可讓使用者快速地為常用的函式帶出手動連接的 UI。 

以下是我們在功能表中找到的最佳作法。 您也可以在[MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup)中找到示範 [手形] 功能表的範例場景。

<br>

---

## <a name="behavior-best-practices"></a>行為最佳做法
**答：將按鈕數目保持**在最小的範圍 . 因為手鎖住的功能表和眼睛之間的距離，以及使用者傾向于隨時專注于相對較小的視覺區域（視覺的 attentional 錐形大約是10度），我們建議讓按鈕數目保持小。 根據我們的探索，即使使用者將其手移至 FOV 的中心，還有三個按鈕的資料行，都能妥善運作。 

**B. 利用快顯功能表進行快速動作：** 引發 arm 並維護位置，很容易就會造成 arm 疲勞。 針對需要短暫互動的功能表，使用手動鎖定的方法。 如果您的功能表很複雜，而且需要擴充的互動時間，請考慮改為使用世界鎖定或主體鎖定。 

**C. 按鈕/面板角度：** 功能表應朝向相反的肩和中間點：這可讓自然手移動以相反的方式與功能表互動，並避免觸及時的任何笨拙或不舒服的位置。滑鼠鍵. 

**D. 考慮支援一次性或無人參與**的作業：不假設這兩個使用者都一律可以使用。 當一或兩個手無法使用時，請考慮各種內容，並確定您的設計帳戶適用于這些情況。 若要支援單次功能表，您可以嘗試將功能表位置從 [手動鎖定] 轉換為 [世界鎖定] （當手翻轉時）。 針對無人參與的情況，請考慮使用語音命令來叫用快顯功能表按鈕。

**E. 兩步驟的**叫用：如果您只使用 palm 作為事件來觸發快顯功能表，當您不需要時，可能會不小心出現這種情況，因為人們會刻意移動，以進行通訊和物件操作和不小心。 如果您的應用程式中遇到誤報，請考慮新增額外的步驟（除了 palm 事件以外），以叫用右手邊的功能表，例如完全開啟的手指。

**F. 避免在手腕（系統首頁按鈕）附近新增按鈕：** 如果功能表按鈕太靠近 [首頁] 按鈕，則在與 [快顯功能表] 互動時，可能會意外觸發。

**G. 測試、測試、測試：** 人員有不同的主體，而且有不同的臨界值來緩和和 discomfort 等等。請務必測試您的設計，並取得來自各種人的意見反應。

<br>

---

## <a name="hand-menu-placement-best-practices"></a>手形功能表位置最佳做法

在「人為剖析」中，ulnar nerve 是在 ulna 骨骼附近執行的 nerve。 Ulna 是在 forearm 中找到的長型骨骼，會從肘形延伸到最小的手指。

以下是根據我們的探勘所建議的2個位置：


:::row:::
    :::column:::
        ![Ulnar 的側邊位置](images/UlnarSideHandMenu.gif)<br>
        **Ulnar 內部 palm**<br>
        這個位置是可靠的，因為手不會彼此重迭。 這對於精確的手勢偵測和追蹤非常重要。
    :::column-end:::
    :::column:::
        ![Ulnar 的側邊位置](images/UlnarAboveHandMenu.gif)<br>
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
        ![上述 arm](images/AboveArm.gif)<br>
        **Arm 之上**<br>
        1-不容易維護良好的手追蹤<br>
        2-因非自然位置而造成使用者疲勞
    :::column-end:::
    :::column:::
        ![以上的手指](images/AboveFingers.gif)<br>
        **上手指**<br>
        1-疲勞，因為有長時間的手中<br>
        2-追蹤索引和中間接頭的問題
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
        ![Top Fingertip](images/TopFingerTip.gif)**熱門 Fingertip**<br>
        1-手追蹤問題<br>
        2-手疲勞保持在正常狀態<br>
        3-因手指之間的空間有限而導致按下其他手指的按鈕時發生問題
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Arm](images/BackOfTheArm.gif) 的背面<br>
        **Arm 背面**<br>
        1-不小心可以觸發 [首頁] 按鈕<br>
        2-不是使用者的自然或舒適位置
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---


## <a name="see-also"></a>請參閱

* [可互動的物件](interactable-object.md)
* [手部直接操作](direct-manipulation.md)
* [手部和運動控制器](hands-and-tools.md)
