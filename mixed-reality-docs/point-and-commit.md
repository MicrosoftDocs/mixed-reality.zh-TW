---
title: 點與包含實際操作的認可
description: 點和認可輸入模型的概觀
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境，互動、 設計、 hololens、 實際操作，到目前為止，點並認可
ms.openlocfilehash: e69c8ff2091beff7d8fbbde4e6f24d909302290a
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730807"
---
# <a name="point-and-commit-with-hands"></a>點與包含實際操作的認可
點與包含實際操作的認可是輸入的模型，可讓使用者為目標、 選取和操作之距離的 2D 內容與 3D 物件。 「 目前 」 互動技術是混合實境特有而非方式讓使用者自然地與真實世界的 intereact。 例如，在進階的 hero 電影*X 男性*，字元[Mo](https://en.wikipedia.org/wiki/Magneto_(comics))能夠連絡和操作與他的實際操作之距離的最物件。 這不是人類可以這麼做實際上。 在 HoloLens (AR) 和混合實境 (VR) 中，我們會提供使用者這個神奇的電源中斷真實的世界有愉悅的經驗，使用全像攝影版的內容不僅讓互動更有效率且有效的實體條件約束。

## <a name="device-support"></a>裝置支援

輸入的模型 | [HoloLens （第 1 代）](https://docs.microsoft.com/en-us/windows/mixed-reality/hololens-hardware-details) | HoloLens 2 | [沈浸式耳機](https://docs.microsoft.com/en-us/windows/mixed-reality/immersive-headset-hardware-details) |
| ---------| -----| ----- | ---------|
點和認可 （最手動互動） | 不支援的 ❌ | 建議的 ✔️ | 建議的 ✔️

點與認可，也就是指針到目前為止，是利用新的相互連貫的手動追蹤系統的新功能。 這個輸入的模型也是透過移動控制站使用的沈浸式耳機的主要輸入的模型。

## <a name="hand-rays"></a>手動光線

HoloLens 2 上，我們會建立從 palm 中央弄手光線。 此光線會被視為指針的延伸模組。 環圈圖形狀的游標會附加至結尾的光線，以指出在與目標物件與光線交集的位置。 將游標放在物件然後可以接收 gestural 命令翻牌。

此基本 gestural 命令就會觸發使用姆指與食指執行空中點選動作。 藉由使用手動光線單點及空中點選來認可，使用者可以啟動按鈕或 web 內容上的超連結。 更多的複合筆勢，使用者就能夠瀏覽的網頁內容和管理 3D 物件的距離。 手動光線的視覺化設計還應該因應這些點和認可的狀態，如下所描述和如下所示： 

* 在 *指向*狀態時，光線虛線且資料指標的 「 甜甜圈 」 圖形。
* 在 *認可*狀態時，光線變成一條實線，而游標會壓縮成一個點。

![](images/Hand-Rays-720px.jpg)

## <a name="transition-between-near-and-far"></a>和最接近之間轉換

而不是使用特定的動作，例如 「 索引食指指向 」 將光線，我們設計即將出從 palm，釋出和保留更多的倒是手勢的五個指中心這類縮小和抓取光線。 與這個設計中，我們會建立只有一個的心智模型，支援完全相同的一組手勢近乎和遠端互動。 您可以使用相同的抓取筆勢來操作物件在不同的距離。 光線的引動過程是自動和架構的鄰近性：

*  在 arm 達到距離 (大約 50 cm) 物件時，光線會關閉自動鼓勵幾近互動。
*  太遠超過 50 cm 物件時，會開啟光線。 轉換時應順利且流暢地。

![](images/Transition-Between-Near-And-Far-720px.jpg)

## <a name="2d-slate-interaction"></a>2D 平板電腦的互動

2D Slate 是全像攝影版的容器，裝載 2D 應用程式的內容，例如網頁瀏覽器。 到目前為止與 2D 平板式互動的設計概念是要用來選取目標和空中點選來手動光線。 之後手動無限遠的光線與目標，使用者可以空中點選來觸發超連結或按鈕。 它們可用來 「 空中點選和拖曳 「 一方面向上和向下捲動平板電腦的內容。 使用兩個實際操作空中點選和拖曳的相對的影片可以縮放 in 和 out 平板電腦的內容。

目標 gmail.comray.djajadinata 角和邊緣之間的手上會顯示最接近的操作功能可見性。 藉由"抓取並拖曳 」 操作提供使用者可以執行統一透過角提供縮放比例以及可以自動重排 slate 透過邊緣提供。 抓取並拖曳上方的 2D slate holobar 使用者可以移動整個 slate。

![](images/2D-Slate-Interaction-Far-720px.jpg)

操作 2D slate 本身：<br>

* 使用者點 gmail.comray.djajadinata 角落或以顯示最接近的操作功能可見性的邊緣之間的手。 
* 藉由套用操作軌跡上的功能可見性，使用者可以執行統一的縮放，透過角功能可見性，而且可以自動重排 slate 透過 edge 功能可見性。 
* 藉由在頂端的 2D slate holobar 套用操作筆勢，使用者可以移動整個 slate。<br>

<br>

## <a name="3d-object-manipulation"></a>3D 物件操作

在直接管理，有兩種方法讓使用者管理 3D 物件、 功能可見性為基礎的管理和非功能可見性根據的操作。 在點和認可的模型中，使用者都能達到完全相同的工作透過手動光線。 不需要任何其他的學習。<br>

### <a name="affordance-based-manipulation"></a>功能可見性為基礎的操作
使用者會使用點，且顯示週框方塊和操作提供手動光線。 使用者可以套用操作手勢，來移動整個物件的週框方塊，來旋轉邊緣提供和上 coner 提供一致的方式調整。 <br>

![](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a>非功能可見性根據的操作
使用者點顯示週框方塊，然後直接在其上套用操作筆勢的手光線。 與某一方面，轉譯和旋轉的物件相關聯動作和左手邊的方向。 與兩個實際操作，使用者可以轉譯、 縮放和旋轉根據相對的兩個實際操作的動作。<br>

<br>

## <a name="instinctual-gesturers"></a>Instinctual gesturers
點及認可 instinctual 筆勢的概念是類似於直接操作。 使用者會假設在 3D 物件上執行的筆勢會程式設計的 UI 提供引導。 例如，小型的控制點可能鼓勵使用者使用其姆指與食指，縮小，雖然使用者可能會想要擷取的較大的物件，使用所有的 5 個手指。

![](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>指針與 6 DoF 控制站之間的對稱式設計 
一開始點和進行遠端互動的認可的概念已建立，並定義為混合實境入口網站 (MRP)，其中有很沈浸式耳機使用者，並透過移動控制站的 3D 物件進行互動。 動作控制站疑難排解出指向及管理遠端物件的光線。 有進一步認可不同動作的控制站上的按鈕。 我們運用光線的互動模型，並它們附加至這兩個實際操作。 透過此對稱的設計，MRP 熟悉的使用者不需要了解另一個用於目前指向及操作的互動模型，在使用 HoloLen 2 時，反之亦然。    

![](images/Symmetric-Design-For-Rays-720px.jpg)<br>

## <a name="instinctual-gestures"></a>Instinctual 筆勢

![](images/Instinctual-Gestures-Far-720px.jpg)

## <a name="see-also"></a>另請參閱
* [頭部目光和行動](gaze-and-commit.md)
* [指針的直接管理](direct-manipulation.md)
* [本能互動](interaction-fundamentals.md)

