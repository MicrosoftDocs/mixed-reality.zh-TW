---
title: 周框方塊和應用程式行
description: 應用程式行是一個物件層級的功能表，其中包含一系列的按鈕，可顯示在全息圖界限的下邊緣。
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality，應用程式行，周框方塊
ms.openlocfilehash: dab41207c2558fe8bb3fe07fca666cb2668f4e45
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723197"
---
# <a name="bounding-box-and-app-bar"></a>周框方塊和應用程式行
![界限是混合現實中物件操作的標準介面。](images/UX/UX_Hero_BoundingBox.jpg)<br>
<br>

## <a name="what-is-the-bounding-box"></a>什麼是周框方塊？

周框是混合現實中物件操作的標準介面。 它會為使用者提供物件目前可調整的 affordance。 在 HoloLens 2 上，周框方塊適用于直接操作，並會回應使用者的 finger's 鄰近性。 它會顯示視覺化的意見反應，以協助使用者感知物件的距離。

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a>縮放物件<br>
        周框方塊的角落告訴使用者該物件可以調整。 控點會遵循廣泛瞭解的調整尺規模式。 此視覺效果 affordance 會顯示使用者物件的總區域，即使它在調整模式之外看不到也一樣。 這點特別重要，因為如果不存在，則將物件貼齊至另一個物件或表面時，其行為可能會與不應存在的空間相同。<br>
        <br>
        *影片迴圈：透過周框方塊縮放物件*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens 透過周框方塊縮放物件的觀點](images/HoloLens2_BoundingBox.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a>旋轉物件<br>
        周框方塊邊緣的垂直矩形 affordances 是旋轉指示器。 這可讓使用者更精細地調整其放入的全息影像。 不僅可以調整和縮放，而且現在也會旋轉。<br>
        <br>
        *影片迴圈：透過周框方塊旋轉物件*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens 透過周框方塊旋轉物件](images/HoloLens2_BoundingBox_Rotate.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a>HoloLens 2 上有關手近距離的視覺回饋<br>
        在 HoloLens 2 上有其他視覺提示，可協助使用者深入瞭解。 當 fingertip 接近物件時，會顯示 fingertip 附近的環形並相應減少。 當到達已按下的狀態時，環形最後會聚合成一個點。 此視覺效果 affordance 可協助使用者瞭解他們與物件之間的距離。<br>
        <br>
        *影片迴圈：根據距離周框方塊的視覺效果意見反應範例*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![視覺效果意見反應](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::

<br>

**針對 Unity 應用程式開發，請參閱[混合現實工具組-Unity 中的周框方塊。](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**

<br>

---

## <a name="what-is-the-app-bar"></a>什麼是應用程式行？

應用程式行是一個物件層級的功能表，其中包含一系列的按鈕，可顯示在全息圖界限的下邊緣。 此模式通常用來提供使用者移除和調整全息影像的能力。 應用程式行主要是用來在使用者環境中管理放置物件的一種方式。 與周框方塊結合，使用者可以完全掌控物件在混合現實中的方向和方式。

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a>應用程式行會遵循使用者<br>
        由於此模式會與世界鎖定的物件搭配使用，因此當使用者四處移動物件時，應用程式行一律會顯示在最靠近使用者的物件端。 雖然這不是 billboarding 的，但實際上會達到相同的結果;防止使用者的位置遮蔽或封鎖在其環境中不同位置可能會提供的功能。 <br>
        <br>
        *影片迴圈：四處流覽全像投影，應用程式行如下*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![四處流覽全像投影。 應用程式行如下。](images/HoloLens2_AppBarFollowing.gif)<br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a>適用于 Unity 的 MRTK （混合現實工具組）中的周框方塊
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 會針對周框方塊和應用程式行提供腳本和 prefabs。 只要將 BoundingBox.cs 腳本指派至任何物件，就可以新增周框方塊。

* [MRTK-周框方塊](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)


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
