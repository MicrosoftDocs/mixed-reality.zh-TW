---
title: 周框方塊和應用程式行
description: 應用程式行是一個物件層級的功能表, 其中包含一系列的按鈕, 可顯示在全息圖界限的下邊緣。
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, 應用程式行, 周框方塊
ms.openlocfilehash: d289be31129324c6ff419b69dbce52bd8f62eb64
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829681"
---
# <a name="bounding-box-and-app-bar"></a>周框方塊和應用程式行
![周框是混合現實中物件操作的標準介面。](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a>什麼是周框方塊？

周框是混合現實中物件操作的標準介面。 它會為使用者提供物件目前可調整的 affordance。 角落會告訴使用者, 物件也可以調整。 此視覺效果 affordance 會顯示使用者物件的總區域, 即使它在調整模式之外看不到也一樣。 這點特別重要, 因為如果不存在, 則將物件貼齊至另一個物件或表面時, 其行為可能會與不應存在的空間相同。 在 HoloLens 2 上, 周框方塊適用于直接操作, 並會回應使用者的 finger's 鄰近性。 它會顯示視覺化的意見反應, 以協助使用者感知物件的距離。 

![HoloLens 透過周框方塊縮放物件的觀點](images/HoloLens2_BoundingBox.gif)<br>
*透過周框方塊縮放物件*

周框方塊角落的控點會遵循廣泛瞭解的調整尺規模式。 

![透過周框方塊旋轉物件的 HoloLens 觀點](images/HoloLens2_BoundingBox_Rotate.gif)<br>
*透過周框方塊旋轉物件*


![視覺效果意見反應關於手近](images/HoloLens2_Proximity.gif)<br>
*以鄰近性為基礎的視覺效果意見反應*

周框方塊邊緣的垂直矩形 affordances 是旋轉指示器。 這可讓使用者更精細地調整其放入的全息影像。 不僅可以調整和縮放, 而且現在也會旋轉。

* 針對 Unity 應用程式開發, 請參閱[混合現實工具組上的周框方塊-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)



## <a name="what-is-the-app-bar"></a>什麼是應用程式行？

應用程式行是一個物件層級的功能表, 其中包含一系列的按鈕, 可顯示在全息圖界限的下邊緣。 此模式通常用來提供使用者移除和調整全息影像的能力。

由於此模式會與世界鎖定的物件搭配使用, 因此當使用者四處移動物件時, 應用程式行一律會顯示在最靠近使用者的物件端。 雖然這不是 billboarding 的, 但實際上會達到相同的結果;防止使用者的位置遮蔽或封鎖在其環境中不同位置可能會提供的功能。

![四處流覽全像投影。 應用程式行如下。](images/HoloLens2_AppBarFollowing.gif)<br>
*流覽全像投影, 應用程式行如下*

應用程式行主要是用來在使用者環境中管理放置物件的一種方式。 與周框方塊結合, 使用者可以完全掌控物件在混合現實中的方向和方式。

* 針對 Unity 應用程式開發, 請參閱[混合現實工具組上的應用程式行-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)

## <a name="see-also"></a>另請參閱
* [可互動的物件](interactable-object.md)
* [Unity 中的文字](text-in-unity.md)
* [物件集合](object-collection.md)
* [顯示進度](progress.md)
