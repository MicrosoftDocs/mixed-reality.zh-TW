---
title: 應用程式檢視
description: Windows Mixed Reality 應用程式中的兩種視圖是沉浸式視圖和2D 視圖。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 沉浸式視圖、2D 視圖、平板電腦、應用程式
ms.openlocfilehash: 2cf65941616ac6906d40e4b4616311317ac705d3
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516907"
---
# <a name="app-views"></a>應用程式檢視

Windows 應用程式可以包含兩種類型的視圖:**沉浸式視圖**和**2d 視圖**。 應用程式可以在不同的沉浸式視圖和2D 視圖之間切換, 將其2D 視圖顯示在監視器上做為視窗或耳機做為平板電腦。 至少有一個沉浸式視圖的應用程式會分類為**混合現實應用程式**。 不具有沉浸式視圖的應用程式是**2d 應用程式**。

## <a name="immersive-views"></a>沉浸式視圖

沉浸式視圖可讓您的應用程式能夠在世界各地建立全像投影, 或在虛擬環境中 immerse 使用者。 當應用程式在沉浸式視圖中繪製時, 不會有任何其他應用程式同時&mdash;在多個應用程式中同時繪製, 而不會合成在一起。 藉由持續調整您的[應用程式呈現](rendering.md)其場景的觀點, 使其符合使用者的前端移動, 您的應用程式可以呈現[全球鎖定](coordinate-systems.md)的全息影像, 並留在真實世界中的固定點, 或轉譯虛擬世界來保存當使用者在其中移動時的位置。

![在沉浸式視圖中, 您可以將全息影像放在世界各地。](images/designoverview.jpg)<br>
*當您在沉浸式觀看時, 可以將全息影像放在世界各地*

在[HoloLens](hololens-hardware-details.md)上, 您的應用程式會在使用者的真實世界周圍呈現其全息影像。 在[Windows Mixed Reality 的沉浸式頭戴式](immersive-headset-hardware-details.md)裝置上, 使用者看不到真實世界, 因此您的應用程式必須轉譯使用者會看到的所有內容。

[Windows Mixed Reality 首頁](navigating-the-windows-mixed-reality-home.md)(包括您在環境中所放置的 [開始] 功能表和全息影像) 不會在沉浸式視圖中呈現。 在 HoloLens 上, 顯示沉浸式視圖時所發生的任何系統通知都會由 Cortana 語音, 而使用者可以使用語音輸入回應。

在沉浸式視圖中, 您的應用程式也會負責處理所有輸入。 Windows Mixed Reality 中的輸入是由[注視](gaze.md)、[手勢](gestures.md)(僅限 HoloLens)、[語音](voice-input.md)和[運動控制器](motion-controllers.md)(僅限沉浸式耳機) 所組成。

## <a name="2d-views"></a>2D 視圖

![在 Windows Mixed Reality 首頁上配置的多個2D 視圖](images/teleportation-640px.png)<br>
*具有2D 視圖的多個應用程式, 置於 Windows Mixed Reality 首頁的周圍*

具有2D 視圖的應用程式會在[Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) (有時稱為「shell」) 中顯示為虛擬的平板電腦, 並隨著應用程式啟動器和使用者在世界中放置的其他全息影像一起呈現。 使用者可以調整此平板電腦來移動和調整它的大小, 雖然它會維持固定解析度, 而不論其大小為何。 如果您應用程式的第一個視圖是2D 視圖, 則您的2D 內容會填滿用來啟動應用程式的相同平板電腦。

在桌面耳機中, 您可以立即執行在桌面監視器上執行的任何通用 Windows 平臺 (UWP) 應用程式。 這些應用程式目前已經呈現2D 視圖, 而其內容會在啟動時自動顯示在使用者世界的平板電腦上。 2D UWP 應用程式可以目標為**Windows 通用**裝置系列, 以便在桌面耳機和 HoloLens 上以平板的形式執行。

2D 視圖的其中一個主要用途, 就是顯示可以使用系統鍵盤的文字輸入表單。 因為 shell 無法在沉浸式視圖上轉譯, 所以應用程式必須切換至2D 視圖以顯示系統鍵盤。 想要接受文字輸入的應用程式可以使用文字方塊切換成2D 視圖。 當該文字方塊有焦點時, 系統會顯示系統鍵盤, 讓使用者可以輸入文字。

請注意, 在桌上型電腦上, 應用程式可以在桌面監視器和連接的頭戴式裝置上具有 2D views。 例如, 您可以使用其主要2D 視圖, 流覽桌上型電腦監視器上的 Edge, 以尋找360度的影片。 當您播放該影片時, Edge 會在耳機內啟動次要的沉浸式視圖, 以顯示沉浸式影片內容。

## <a name="see-also"></a>另請參閱

* [應用程式模型](app-model.md)
* [更新混合實境的 2D UWP 應用程式](building-2d-apps.md)
* [取得 HolographicSpace](getting-a-holographicspace.md)
* [瀏覽 Windows Mixed Reality 住家](navigating-the-windows-mixed-reality-home.md)
* [混合實境應用程式類型](types-of-mixed-reality-apps.md)
