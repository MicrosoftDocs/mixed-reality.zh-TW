---
title: 點和認可
description: 點和認可輸入模型的概觀
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
keywords: 混合實境，互動，設計
ms.openlocfilehash: e0e9c97053734ac0125fce40be7ffe9afbd2dd68
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2019
ms.locfileid: "64581308"
---
# <a name="point-and-commit"></a>點和認可
點和認可是輸入的模型可讓使用者為目標、 選取和操作內容 2D 和 3D 物件的距離。 這個 「 Far"互動技術是 navel 的互動式體驗，人為的是不需要在每日與真實世界互動期間。 比方說，在進階的 hero 電影，Mo 能夠的觸角和操作遠的物件，透過實際操作的距離，但人們在實際上無法做到。 在 Microsoft HoloLens (AR) 和 Microsoft 混合實境 (VR) 中，我們讓使用者這個神奇的電源中斷不只是為了讓愉悅的經驗，使用全像攝影版的內容，但讓互動更有效率的真實世界的實體條件約束和有效的。

## <a name="device-support"></a>裝置支援
<table>
    <colgroup>
    <col width="40%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    </colgroup>
    <tr>
        <td><strong>輸入的模型</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沈浸式耳機</strong></a></td>
    </tr>
     <tr>
        <td>點和認可 （最手動互動）</td>
        <td>不支援的 ❌</td>
        <td>建議的 ✔️</td>
        <td>建議的 ✔️</td>
    </tr>
</table>
<br>
點和認可已 HoloLens 2，利用新的相互連貫的手動追蹤系統上的主要輸入模型的其中一個。 這個輸入的模型也是透過移動控制站使用的沈浸式耳機的主要輸入的模型。 點和認可是我們建議您將前端視線輸入的模型和 HoloLens 上認可 （第 1 代）。 

## <a name="hand-rays"></a>手動光線
HoloLens 2 上，我們會建立疑難排解從 palm 中央手光線。 與射線會被視為指針的延伸模組。 環圈圖的圖形資料指標會附加結尾的光線，暗示與命中物件中的光線交集的位置。 資料指標進入物件會接收來自手形的 gestural 的命令。 

非常基本的 gestural 命令就會觸發使用姆指與食指執行空中點選手勢。 藉由使用手動光線單點及空中點選來認可，使用者可以啟動按鈕或 web 內容上的超連結。 更多的複合筆勢，使用者就能夠瀏覽的網頁內容和管理 3D 物件的距離。 手動光線的視覺化設計也應該回應點，並認可狀態： <br>
* 在指標的狀態，光線 dash 分行、 且資料指標是環圈圖的圖形。
* 在認可的狀態，光線變成一條實線，而游標會壓縮成一個點。<br><br>
![](images/Hand-Rays-720px.jpg)<br>

## <a name="transition-between-near-and-far"></a>和最接近之間轉換
而不是使用特定的筆勢，例如指向食指導向無限遠的光線，與我們設計來自中心的 palm、 光線，釋出和保留的多個 gestural 操作的五個指。 因此，HoloLens 2 支援幾近和遠端互動完全相同的一組手勢。 從靠近最互動，以及反向傳輸的使用者時，就不需要任何其他的學習。 使用者可以使用相同的抓取筆勢來操作物件在不同的距離。 光線的引動過程是自動和架構的鄰近性： <br>
* 在 arm 達到距離 (大約 50 cm) 物件時，光線會關閉自動鼓勵幾近互動。 
* 太遠超過 50 cm 物件時，會開啟光線。

這項機制會使轉換順利且流暢地。<br>
![](images/Transition-Between-Near-And-Far-720px.jpg)<br>

## <a name="2d-slate-interaction"></a>2D 平板電腦的互動
2D slate 是全像攝影版的容器，裝載 2D 應用程式的內容，例如網頁瀏覽器。 到目前為止與 2D 平板式互動的設計概念是單點及空中點選來認可使用手動光線。<br>

如果需要互動的平板電腦的常數：<br>

* 使用者可以在超連結或按鈕，然後才能加以啟動空中點選點。 
* 若要執行以向上和向下捲動平板電腦的內容瀏覽動作時，使用者可以使用一隻手。 
* 使用者可以使用兩個實際操作，來執行瀏覽手勢來縮放 in 和 out 平板電腦的內容。<br><br>

![](images/2D-Slate-Interaction-Far-720px.jpg)<br>

操作 2D slate 本身：<br>

* 使用者點 gmail.comray.djajadinata 角落或以顯示最接近的操作功能可見性的邊緣之間的手。 
* 藉由套用操作軌跡上的功能可見性，使用者可以執行統一的縮放，透過角功能可見性，而且可以自動重排 slate 透過 edge 功能可見性。 
* 藉由在頂端的 2D slate holobar 套用操作筆勢，使用者可以移動整個 slate。<br>

<br>

## <a name="3d-object-manipulation"></a>3D 物件操作
在直接管理，有兩種方式來操作 3D 物件的使用者功能可見性基礎操作和非 affordnace 基礎操作。 在點和認可的模型中，使用者都能達到完全相同的工作透過手動光線。 不需要任何其他的學習。<br>

### <a name="affordance-based-manipulation"></a>基礎功能的可見性操作
使用者會使用點，且顯示週框方塊和操作提供手動光線。 使用者可以套用操作手勢，來移動整個物件的週框方塊，來旋轉邊緣提供和上 coner 提供一致的方式調整。 <br>

![](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a>非功能可見性根據的操作
使用者點顯示週框方塊，然後直接在其上套用操作筆勢的手光線。 與某一方面，轉譯和旋轉的物件相關聯動作和左手邊的方向。 與兩個實際操作，使用者可以轉譯、 縮放和旋轉根據相對的兩個實際操作的動作。<br>

<br>

## <a name="instinctual-gesturers"></a>Instinctual gesturers
點及認可 instinctual 筆勢的概念是同步槲臗懟。 假設的 3D 物件上執行的筆勢使用者會引導您的 UI 提供的設計。 小型的控制點會鼓勵使用者時的大型物件，讓使用者能夠抓取 5 食指姆指與食指，以縮小。

![](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>指針與 6 DoF 控制站之間的對稱式設計 
首先建立並定義為混合實境入口網站 (MRP)，其中使用者 wear 沈浸式耳機並與其互動的 3d 物件透過移動控制站進行遠端互動點和認可模型的概念。 動作控制站疑難排解出指向及管理遠端物件的光線。 有進一步認可不同功能的控制站上的按鈕。 我們運用光線的互動模型，並將它們連接在這兩個手上。 透過此對稱的設計，MRP 熟悉的使用者不需要了解另一個用於目前指向及操作時使用 HoloLen 2 的第一次的互動模型，反之亦然。    

![](images/Symmetric-Design-For-Rays-720px.jpg)<br>


## <a name="see-also"></a>另請參閱
* [視線與認可](gaze-and-commit.md)
* [直接操作](direct-manipulation.md)
* [互動基本概念](interaction-fundamentals.md)
