---
title: 應用程式檢視
description: 這兩種 Windows Mixed Reality 應用程式中的檢視是沈浸式的檢視和 2D 檢視。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 沈浸式檢視，2D 檢視，平板電腦、 應用程式
ms.openlocfilehash: 2cf65941616ac6906d40e4b4616311317ac705d3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596978"
---
# <a name="app-views"></a>應用程式檢視

Windows 應用程式可以包含兩種類型的檢視**沈浸式檢視**並**2D 檢視**。 應用程式可以其各種不同的沈浸式的檢視和做為視窗或做為靜態圖像耳機的監視器上顯示其 2D 檢視的 2D 檢視之間切換。 已將至少一個的沈浸式檢視的應用程式分類為**混合現實應用程式**。 永遠不會有的沈浸式檢視的應用程式受到**2D 應用程式**。

## <a name="immersive-views"></a>沈浸式檢視

沈浸式的檢視可讓您的應用程式建立全像投影您週遭的世界中，或虛擬環境中的使用者將可享有的能力。 當應用程式在沉浸式檢視中繪圖時，沒有任何其他應用程式繪製在同一時間&mdash;全像投影從多個應用程式不是複合在一起。 藉由持續調整它的檢視方塊您[應用程式所轉譯](rendering.md)其場景方向，以符合使用者的前端移動，您的應用程式可以轉譯[世界鎖定](coordinate-systems.md)全像投影保持固定，真正的中點世界中，也可以轉譯的虛擬環境中，當使用者移動其內保存它的位置。

![在沉浸式檢視中，全像投影，可以放在您的世界中。](images/designoverview.jpg)<br>
*在沉浸式檢視中，全像投影可以放在您的世界*

在  [HoloLens](hololens-hardware-details.md)，您的應用程式呈現其全像投影在使用者的實際恍神之上。 在  [Windows Mixed Reality 沈浸式耳機](immersive-headset-hardware-details.md)，使用者無法看到真實世界中，並讓您的應用程式必須呈現的所有項目，使用者會看到。

[Windows Mixed Reality 家用](navigating-the-windows-mixed-reality-home.md)（包括 [開始] 功能表和周圍環境放入全像投影） 不會呈現在沈浸式檢視其中一個。 在 HoloLens，會輪流轉送時發生的沈浸式的檢視會顯示任何系統通知，cortana，然後使用者可以使用語音輸入回應。

雖然在沉浸式檢視中，您的應用程式也會負責處理所有的輸入。 輸入 Windows Mixed Reality 組成[視線](gaze.md)，[筆勢](gestures.md)(HoloLens 只)，[語音](voice-input.md)並[動作控制器](motion-controllers.md)（沈浸式耳機只）。

## <a name="2d-views"></a>2D 檢視

![多個 2D 檢視配置周圍家用的 Windows Mixed Reality](images/teleportation-640px.png)<br>
*多個應用程式的 2D 檢視周圍家用的 Windows Mixed Reality*

應用程式的 2D 檢視會出現在[Windows Mixed Reality 家用](navigating-the-windows-mixed-reality-home.md)（有時稱為 「 殼層 」） 為虛擬的 slate，轉譯、 應用程式啟動器，以及當使用者在他們的世界中提出其他全像投影。 使用者可以調整此 slate 移動和調整，但它會保持固定的解析度，不論其大小。 如果 2D 檢視您的應用程式的第一個檢視，2D 內容將會填滿用來啟動應用程式相同的候選影片。

在桌面的耳機，您可以執行任何立即執行您桌面的監視器的通用 Windows 平台 (UWP) 應用程式。 這些應用程式目前已呈現 2D 檢視，和其內容會自動出現在啟動時，使用者的世界中的候選影片。 2D 的 UWP 應用程式可以為目標**Windows.Universal**裝置系列為靜態圖像的 HoloLens 和這兩個桌面耳機上執行。

其中一個索引鍵使用的 2D 檢視是顯示文字的項目表單，可讓使用系統鍵盤。 因為殼層無法轉譯之上的沈浸式檢視中，應用程式必須切換到 2D 的檢視，以顯示系統鍵盤。 想要接受文字輸入的應用程式可以切換到文字方塊中的 2D 檢視。 該文字方塊具有焦點，而系統將會顯示系統鍵盤，讓使用者輸入的文字。

請注意，在桌面的電腦上的應用程式可以在桌上型監視器和附加的耳機的 2D 檢視。 比方說，您可以您桌面的監視器，請使用其主要的 2D 檢視來尋找 360 度的視訊上瀏覽 Edge。 當您播放該視訊時，邊緣會啟動次要的沈浸式檢視，顯示擬真視訊內容耳機內。

## <a name="see-also"></a>另請參閱

* [應用程式模型](app-model.md)
* [更新混合實境的 2D UWP 應用的程式](building-2d-apps.md)
* [取得 HolographicSpace](getting-a-holographicspace.md)
* [瀏覽家用的 Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
* [混合的實境應用程式類型](types-of-mixed-reality-apps.md)
