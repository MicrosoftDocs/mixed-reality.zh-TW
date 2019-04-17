---
title: 應用程式列和週框方塊
description: 應用程式列是物件層級功能表，其中包含一系列的下邊緣的雷射的界限會顯示的按鈕。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，橫條圖、 週框方塊的應用程式
ms.openlocfilehash: bdce92e00193230d1f7a487f11ef0487f1d6657c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595300"
---
# <a name="bounding-box-and-app-bar"></a>週框方塊以及應用程式列
![週框是在混合實境中的物件操作的標準介面。](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a>什麼是框方塊？

週框是在混合實境中的物件操作的標準介面。 它會提供使用者功能的物件是目前可調整的可見性。 邊角，告訴使用者也可以調整的物件。 此視覺化功能可見性即使看不見的調整模式之外，顯示使用者物件 – 的總面積。 這是特別重要，因為如果不是那麼有，都會移動到另一個物件或介面的物件可能會出現，彷彿其周圍不應該有的空間。 HoloLens 2 週框方塊會回應使用者的手指相近。 它會顯示視覺的意見反應，以協助察覺物件之間的距離。 

![HoloLens-的-觀點來調整物件透過週框方塊](images/bounding-box-scale.gif)<br>
*調整物件透過週框方塊*

週框方塊類似 cube 的邊角遵循廣泛了解適用於調整規模模式。 結合使用明確的動作，將物件放入 」 調整模式 」 的是可以同時移動物件，但也在其環境中調整它清除。

![HoloLens-的-觀點來旋轉物件透過週框方塊](images/bounding-box-rotate.gif)<br>
*旋轉物件透過週框方塊*

週框方塊的邊緣上更低的球面的提供是旋轉指標。 這會讓使用者更多的細緻調整透過其放置全像投影。 不只可以調整及縮放，但現在也旋轉。

* 開發 Unity 應用程式，請參閱[框方塊上混合實境工具組-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="what-is-the-app-bar"></a>什麼是應用程式列？

應用程式列是物件層級功能表，其中包含一系列的下邊緣的雷射的界限會顯示的按鈕。 此模式通常會用來讓使用者能夠移除，並調整全像投影中。

因為此模式會鎖定，世界，當使用者移動應用程式列一律會顯示在最接近使用者的物件端的物件周圍的物件。 雖然這不告示板中，有效地達成相同的結果;防止使用者的位置向 occlude 或會使用從他們的環境中的不同位置的區塊功能。

![雷射四處跑。 應用程式列後面。](images/holobar-followuser.gif)<br>
*雷射四處跑，遵循應用程式列*

應用程式列中的設計主要是做為管理使用者的環境中放置的物件的方式。 搭配週框方塊，使用者可以完全控制在混合實境中何處以及如何為導向的物件。

* 開發 Unity 應用程式，請參閱[應用程式列上混合實境工具組-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)

## <a name="see-also"></a>另請參閱
* [週框方塊上混合實境工具組-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)
* [應用程式列上混合實境工具組-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)
* [可互動的物件](interactable-object.md)
* [在 Unity 中的文字](text-in-unity.md)
* [物件集合](object-collection.md)
* [顯示進度](progress.md)
