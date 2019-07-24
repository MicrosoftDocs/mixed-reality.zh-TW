---
title: 顯示進度
description: 進度控制項為使用者提供回饋，告知正在進行長時間執行的操作。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 設計, 控制項, ui, ux
ms.openlocfilehash: 84853a23a73bbece30c1f96b83e586642f3ab762
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523259"
---
# <a name="displaying-progress"></a>顯示進度

進度控制項為使用者提供回饋，告知正在進行長時間執行的操作。 根據所使用的指示器，它可以表示在進度指示器可見的時候，使用者無法與 App 互動，也可以指示可能需要等待多久的時間。

![HoloLens 中的進度環形範例](images/HoloLens2_Loader.gif)<br>
*HoloLens 中的進度環形範例*

## <a name="types-of-progress"></a>進度的類型

請務必提供有關發生什麼情況的使用者資訊。 在混合現實中, 如果您的應用程式沒有提供良好的視覺效果意見反應, 實體環境或物件就可以輕鬆地將使用者工作。 針對需要幾秒鐘的情況, 例如資料載入或場景正在更新時, 最好是顯示視覺指標。 有兩個選項可顯示作業正在進行中的使用者–一個**進度**列或一個**進度環**。

### <a name="progress-bar"></a>進度列

![HoloLens 中的進度列範例](images/640px-progressbar.jpg)

進度列會顯示工作已完成的百分比。 它應該在持續時間已知的作業期間使用 (確定), 但其進度不應封鎖使用者與應用程式的互動。

### <a name="progress-ring"></a>進度環

![HoloLens 中的進度環形範例](images/640px-progressring.jpg)

進度環僅具有不定狀態, 而且應該在作業完成之前封鎖任何進一步的使用者互動時使用。

### <a name="progress-with-a-custom-object"></a>使用自訂物件的進度

![HoloLens 中的自訂網格範例進度](images/640px-progresscustom.jpg)

您可以使用自己的自訂 2D/3D 物件自訂進度控制項, 以加入應用程式的個人化和品牌身分識別。

## <a name="best-practices"></a>最佳作法
* 將[billboarding 或標記](billboarding-and-tag-along.md)緊密地放在進度的顯示中, 因為使用者可以輕鬆地將其標頭移至空白空間並遺失內容。 如果使用者無法看到任何專案, 您的應用程式可能看起來好像已當機。 Billboarding 和標記會內建在進度 prefab 中。
* 提供使用者所發生狀況的狀態資訊, 是很好的。 [進度] prefab 提供各種視覺化樣式, 包括提供狀態的 Windows 標準環形類型進度。 如果您想要讓進度的樣式符合應用程式的品牌, 您也可以使用自訂網格搭配動畫。

## <a name="see-also"></a>另請參閱
* [混合現實工具組上的進度腳本和 prefabs](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [周框方塊](app-bar-and-bounding-box.md)
* [可互動的物件](interactable-object.md)
* [物件集合](object-collection.md)
* [佈告板和常駐標籤](billboarding-and-tag-along.md)
