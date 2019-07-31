---
title: 手部指向和行動
description: 指向和行動輸入模型的概觀
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境, 互動, 設計, hololens, 手部, 遠方, 指向和行動
ms.openlocfilehash: 4e19a7fd95bac42283ce3e3176a1363afda8f220
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414543"
---
# <a name="point-and-commit-with-hands"></a>手部指向和行動
手部指向和行動是輸入模型，可讓使用者鎖定目標、選取和操作遠方的 2D 內容與 3D 物件。 「遠方 (far)」互動技術是混合實境特有的技術，不是使用者與真實世界自然互動的方式。 例如，在超級英雄電影「X 戰警」  中，[萬磁王](https://en.wikipedia.org/wiki/Magneto_(comics))能夠使用他的手觸碰和操作遠方物件。 這不是人類在現實中可做到的事。 在 HoloLens (AR) 和混合實境 (MR) 中，我們會賦予使用者這個神奇的力量，來打破真實世界的實質限制，而且我們不只透過全像攝影來提供有趣的體驗，還會讓使用者互動變得更有效率。

## <a name="device-support"></a>裝置支援

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><strong>輸入模型</strong></td>
     <td><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></td>
     <td><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
</tr>
<tr>
     <td>手部指向和行動</td>
     <td>❌ 不支援</td>
     <td>✔️ 建議使用</td>
     <td>✔️ 建議使用</td>
</tr>
</table>


指向和行動 (也稱為 hands far) 是利用新式關節手部追蹤系統的新功能之一。 透過運動控制器使用的沈浸式耳機也是以此輸入模型作為主要輸入模型。

## <a name="hand-rays"></a>手部光線 (Hand Ray)

在 HoloLens 2 上，我們已建立可從使用者手掌中央發射的手部光線。 此光線將視為手的延伸。 光線末端會附加環狀游標，以指出光線與目標物件交集的位置。 然後，游標所在的物件就能從手部接收手勢命令。

此基本手勢命令會藉由使用拇指與食指執行空中點選動作來觸發。 藉由使用手部光線進行指向及空中點選來行動，使用者就可以啟用按鈕或超連結。 藉由更多的複合手勢，使用者還能夠從遠處瀏覽網頁內容和操作 3D 物件。 手動光線的視覺化設計也會反應這些指向和行動狀態，請見下列圖示和說明： 

* 在「指向」  狀態時，光線呈虛線，而指標呈環狀。
* 在「行動」  狀態時，光線變成一條實線，而游標會壓縮成一個點。

![手部光線的指向和行動狀態](images/Hand-Rays-720px.jpg)<br>
*手部光線的指向 (左) 和行動 (右) 狀態*

## <a name="transition-between-near-and-far"></a>遠近轉換

我們不是使用「以食指指向」之類的特定手勢來指引光線方向，而是設計讓光線從手掌發出，並釋出和保留五個手指頭來操作更多手勢，例如捏取和抓取。 透過這項設計，我們只需建立一個心智模型，即可針對遠近互動支援完全相同的一組手勢。 您可以使用相同的抓取手勢來操作不同距離的物件。 光線的引動過程會根據鄰近程度自動執行，如下所示：

*  當物件位在手臂可及的範圍內 (大約 50 公分) 時，光線就會自動關閉，並建議您進行近距離互動。
*  物件距離超過 50 公分時，光線就會開啟。 此轉換會很順利且流暢。

![遠近互動都使用同一組手勢](images/Transition-Between-Near-And-Far-720px.jpg)<br>
*遠近互動都使用同一組手勢。*

## <a name="2d-slate-interaction"></a>2D 平板互動

2D 平板是裝載 2D 應用程式內容 (例如網頁瀏覽器) 的全像攝影容器。 以 2D 平板進行遠端互動的設計概念是，使用手部光線來鎖定目標和使用空中點選來選取項目。 以手部光線鎖定目標後，使用者可以透過空中點選來觸發超連結或按鈕。 他們可使用一隻手來進行「空中點選和拖曳」，進而上下捲動平板內容。 使用兩隻手進行空中點選和拖曳的相對動作則可縮放平板內容。

將手部光線的目標鎖定在角落和邊緣會顯示最接近的操作能供性 (affordance)。 藉由「抓取並拖曳」操作能供性，使用者可以透過角落能供性執行統一的尺寸調整，以及可透過邊緣能供性來重排平板。 藉由抓取並拖曳 2D 平板上方的 holobar，使用者可以移動整個平板。

![2D 平板互動](images/2D-Slate-Interaction-Far-720px.jpg)

操作 2D 平板：<br>

* 使用者將手部光線指向角落或邊緣時，可顯示最接近的操作能供性。 
* 藉由在能供性上套用操作手勢，使用者可以透過角落能供性執行統一的尺寸調整，以及可透過邊緣能供性來重排平板。 
* 藉由在 2D 平板頂端的 holobar 上套用操作手勢，使用者可以移動整個平板。<br>

<br>

## <a name="3d-object-manipulation"></a>3D 物件操作

在直接操作中，有兩種方法可讓使用者操作 3D 物件：能供性操作與非能供性操作。 在指向和行動模型中，使用者都能透過手部光線來完成完全相同的工作。 不需要進行任何其他學習。<br>

### <a name="affordance-based-manipulation"></a>能供性操作
使用者使用手部光線來指向並顯示週框方塊和操作能供性。 使用者可以將操作手勢套用到週框方塊來移動整個物件，套用到邊緣能供性可旋轉物件，套用到角落能供性可統一調整物件大小。 <br>

![能供性操作](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a>非能供性操作
使用者透過手部光線指向來顯示週框方塊，然後直接在其上方套用操作手勢。 若使用一隻手，物件的轉譯和旋轉會與手的動作和方向相關聯。 若使用兩隻手，使用者可以根據兩隻手的相對動作來轉譯、縮放及旋轉週框方塊。<br>

<br>

## <a name="instinctual-gestures"></a>本能手勢
指向和行動的本能手勢基本上類似於[手部直接操作](direct-manipulation.md)。 使用者在 3D 物件上執行的手勢，皆由 UI 能供性的設計來引導。 例如，在使用者想使用五隻手指頭來抓取較大的物件時，小型控點可能會促使使用者運用其拇指與食指來捏取物件。

![本能手勢](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>手部與 6 DoF 控制器之間的對稱設計 
一開始，用於遠距互動的指向和行動概念是針對混合實境入口 (MRP) 所建立及定義，在該入口中，使用者會戴著沉浸式頭戴裝置，並透過運動控制器來與 3D 物件互動。 運動控制器會發射光線來指向及操作遠方物件。 控制器上有按鈕，可用來進一步執行不同動作。 我們運用光線的互動模型，並將其連結至雙手。 透過此對稱設計，熟悉 MRP 的使用者在使用 HoloLen 2 時，不需要學習另一個用於遠端指向及操作的互動模型，反之亦然。    

![手部與 6 DoF 控制器之間的對稱設計](images/Symmetric-Design-For-Rays-720px.jpg)<br>


## <a name="see-also"></a>請參閱
* [頭部注視並認可](gaze-and-commit.md)
* [手部直接操作](direct-manipulation.md)
* [本能互動](interaction-fundamentals.md)

