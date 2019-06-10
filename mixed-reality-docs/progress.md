---
title: 顯示進度
description: 進度控制項為使用者提供回饋，告知正在進行長時間執行的操作。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，設計、 控制項、 ui、 ux
ms.openlocfilehash: d62d86c690233f351b6c156c66eba33cb2687ea6
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813741"
---
# <a name="displaying-progress"></a>顯示進度

進度控制項為使用者提供回饋，告知正在進行長時間執行的操作。 根據所使用的指示器，它可以表示在進度指示器可見的時候，使用者無法與 App 互動，也可以指示可能需要等待多久的時間。

![HoloLens 進度環範例](images/HoloLens2_Loader.gif)<br>
*HoloLens 進度環範例*

## <a name="types-of-progress"></a>進度的類型

請務必提供有關最新動態的使用者資訊。 在混合實境中使用者可以被輕易地閃閃實體環境或物件如果您的應用程式不提供良好的視覺回應。 需要幾秒鐘的情況下，例如當資料載入或場景，正在更新，它是個不錯的主意，若要顯示的視覺指標。 有兩個選項，讓使用者有作業正在進行中-正在**進度列**或是**進度環**。

### <a name="progress-bar"></a>進度列

![HoloLens 進度列範例](images/640px-progressbar.jpg)

進度列會顯示工作的完成百分比。 它應該在其持續時間稱為 （確定），作業期間使用，但其進度應該不會封鎖應用程式的使用者的互動。

### <a name="progress-ring"></a>進度環

![HoloLens 進度環範例](images/640px-progressring.jpg)

進度環只有不定狀態，而且任何進一步的使用者互動會被封鎖，直到作業完成時，應使用。

### <a name="progress-with-a-custom-object"></a>使用自訂物件的進度

![使用中 HoloLens 的自訂網狀範例的進度](images/640px-progresscustom.jpg)

您可以藉由自訂進度控制項，以您自己自訂的 2D/3D 物件新增至您的應用程式的個性和葺爦蜞頇。

## <a name="best-practices"></a>最佳作法
* 緊密結合[告示板或 tag-along](billboarding-and-tag-along.md)進度，因為使用者可以輕鬆地將其標頭移至空白空間，並遺失內容的顯示。 您的應用程式可能會在它已損毀，如果使用者無法看到任何項目外觀。 進度 prefab 是內建 billboarding 和 tag-along。
* 最好一律以提供有關最新動態給使用者的狀態資訊。 進度 prefab 提供不同的視覺樣式，包括 Windows 標準的信號類型進行提供狀態。 您也可以使用動畫使用自訂的網狀結構，如果您想要您的進度，以與您的應用程式的品牌保持一致的樣式。

## <a name="see-also"></a>另請參閱
* [進行指令碼及混合實境 toolkit prefabs](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [週框方塊](app-bar-and-bounding-box.md)
* [可互動的物件](interactable-object.md)
* [物件集合](object-collection.md)
* [佈告板和常駐標籤](billboarding-and-tag-along.md)
