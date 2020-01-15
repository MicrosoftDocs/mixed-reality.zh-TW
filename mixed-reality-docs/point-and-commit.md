---
title: 手部指向和行動
description: 指向和行動輸入模型的概觀
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境, 互動, 設計, HoloLens, 手部, 遠方, 指向和行動
ms.openlocfilehash: d3f886fd8e892fe34116c3a1d601ae3a87d87a9b
ms.sourcegitcommit: 2bfe9b1af4ee2cc0d668caeccb8ebc3137cbc20b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901534"
---
# <a name="point-and-commit-with-hands"></a>手部指向和行動

![游標](images/UX/UX_Hero_HandRay.jpg)

手部指向和行動是輸入模型，可讓使用者鎖定目標、選取和操作可及範圍之外的 2D 內容與 3D 物件。 「遠方 (far)」互動技術是混合實境特有的技術，不是使用者與真實世界自然互動的方式。 例如，在超級英雄電影「X 戰警」  中，[萬磁王](https://en.wikipedia.org/wiki/Magneto_(comics))能夠使用他的手觸碰和操作遠方物件。 這不是人類在現實中可做到的事。 在 HoloLens (AR) 和混合實境 (MR) 中，我們會賦予使用者這個神奇的力量，來打破真實世界的實質限制，而且我們不只透過全像攝影來提供有趣的體驗，還會讓使用者互動變得更有效率。

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
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
</tr>
<tr>
     <td>手部指向和行動</td>
     <td>❌ 未支援</td>
     <td>✔️ 建議使用</td>
     <td>✔️ 建議使用</td>
</tr>
</table>


「指向和行動」  是利用新式關節手部追蹤系統的新功能之一。 透過運動控制器使用的沈浸式耳機也是以此輸入模型作為主要輸入模型。

<br>

---

## <a name="hand-rays"></a>手部光線 (Hand Ray)

在 HoloLens 2 上，我們已建立可從使用者手掌中央發射的手部光線。 此光線將視為手的延伸。 光線末端會附加環狀游標，以指出光線與目標物件交集的位置。 然後，游標所在的物件就能從手部接收手勢命令。

此基本手勢命令會藉由使用拇指與食指執行空中點選動作來觸發。 藉由使用手部光線進行指向及空中點選來行動，使用者就可以啟用按鈕或超連結。 藉由更多的複合手勢，使用者還能夠從遠處瀏覽網頁內容和操作 3D 物件。 手動光線的視覺化設計也會反應這些指向和行動狀態，請見下列圖示和說明： 

:::row:::
    :::column:::
        ![手部光線指向](images/hand-rays-pointing.jpg)<br>
        **指向狀態**<br>
        在「指向」  狀態時，光線呈虛線，而指標呈環狀。
    :::column-end:::
    :::column:::
        ![手部光線認可](images/hand-rays-commit.jpg)<br>
        **認可狀態**<br>
        在「行動」  狀態時，光線變成一條實線，而游標會壓縮成一個點。
    :::column-end:::
:::row-end:::

<br>

---


## <a name="transition-between-near-and-far"></a>遠近轉換

我們不是使用「以食指指向」之類的特定手勢來指引光線方向，而是設計讓光線從手掌發出，並釋出和保留五個手指頭來操作更多手勢，例如捏取和抓取。 透過這項設計，我們只需建立一個心智模型 - 針對遠近互動使用完全相同的一組手勢。 您可以使用相同的抓取手勢來操作不同距離的物件。 光線的引動過程會根據鄰近程度自動執行，如下所示：

:::row:::
    :::column:::
        ![近距操作](images/transition-near-manipulation.jpg)<br>
        **近距操作**<br>
        當物件位在手臂可及的範圍內 (大約 50 公分) 時，光線就會自動關閉，並建議您進行近距離互動。
    :::column-end:::
    :::column:::
        ![遠距操作](images/transition-far-manipulation.jpg)<br>
        **遠距操作**<br>
        物件距離超過 50 公分時，光線就會開啟。 此轉換會很順利且流暢。
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a>2D 平板互動

2D 平板是裝載 2D 應用程式內容 (例如網頁瀏覽器) 的全像攝影容器。 以 2D 平板進行遠端互動的設計概念是，使用手部光線來鎖定目標和使用空中點選來選取項目。 以手部光線鎖定目標後，使用者可以透過空中點選來觸發超連結或按鈕。 他們可使用一隻手來進行「空中點選和拖曳」，進而上下捲動平板內容。 使用兩隻手進行空中點選和拖曳的相對動作則可縮放平板內容。

將手部光線的目標鎖定在角落和邊緣會顯示最接近的操作能供性 (affordance)。 藉由「抓取並拖曳」操作能供性，使用者可以透過角落能供性執行統一的尺寸調整，以及可透過邊緣能供性來重排平板。 藉由抓取並拖曳 2D 平板上方的 holobar，使用者可以移動整個平板。

:::row:::
    :::column:::
       ![2D 平板互動按一下](images/2d-slate-interaction-click.jpg)<br>
       **按一下**<br>
    :::column-end:::
    :::column:::
       ![2D 平板互動捲動](images/2d-slate-interaction-scroll.jpg)<br>
        **捲動**<br>
    :::column-end:::
    :::column:::
       ![2D 平板互動縮放](images/2d-slate-interaction-zoom.jpg)<br>
       **縮放**<br>
    :::column-end:::
:::row-end:::

<br>

**操作 2D 平板**<br>

* 使用者將手部光線指向角落或邊緣時，可顯示最接近的操作能供性。 
* 藉由在能供性上套用操作手勢，使用者可以透過角落能供性執行統一的尺寸調整，以及可透過邊緣能供性來重排平板。 
* 藉由在 2D 平板頂端的 holobar 上套用操作手勢，使用者可以移動整個平板。<br>


<br>

---

## <a name="3d-object-manipulation"></a>3D 物件操作

在直接操作中，有兩種方法可讓使用者操作 3D 物件：能供性操作與非能供性操作。 在指向和行動模型中，使用者都能透過手部光線來完成完全相同的工作。 不需要進行任何其他學習。<br>

### <a name="affordance-based-manipulation"></a>能供性操作
使用者使用手部光線來指向並顯示週框方塊和操作能供性。 使用者可以將操作手勢套用到週框方塊來移動整個物件，套用到邊緣能供性可旋轉物件，套用到角落能供性可統一調整物件大小。 <br>

:::row:::
    :::column:::
       ![3D 物件操作遠距移動](images/3d-object-manipulation-far-move.jpg)<br>
       **移動**<br>
    :::column-end:::
    :::column:::
       ![3D 物件操作遠距旋轉](images/3d-object-manipulation-far-rotate.jpg)<br>
        **旋轉**<br>
    :::column-end:::
    :::column:::
       ![3D 物件操作遠距縮放](images/3d-object-manipulation-far-scale.jpg)<br>
       **縮放比例**<br>
    :::column-end:::
:::row-end:::


### <a name="non-affordance-based-manipulation"></a>非能供性操作
使用者透過手部光線指向來顯示週框方塊，然後直接在其上方套用操作手勢。 若使用一隻手，物件的轉譯和旋轉會與手的動作和方向相關聯。 若使用兩隻手，使用者可以根據兩隻手的相對動作來轉譯、縮放及旋轉週框方塊。<br>

<br>

---

## <a name="instinctual-gestures"></a>本能手勢
指向和行動的本能手勢基本上類似於[手部直接操作](direct-manipulation.md)。 使用者在 3D 物件上執行的手勢，皆由 UI 能供性的設計來引導。 例如，在使用者想使用五隻手指頭來抓取較大的物件時，小型控點可能會促使使用者運用其拇指與食指來捏取物件。

:::row:::
    :::column:::
       ![本能手勢遠距小型物件](images/instinctual-gestures-far-smallobject.jpg)<br>
       **小型物件**<br>
    :::column-end:::
    :::column:::
       ![本能手勢遠距中型物件](images/instinctual-gestures-far-mediumobject.jpg)<br>
        **中型物件**<br>
    :::column-end:::
    :::column:::
       ![本能手勢遠距大型物件](images/instinctual-gestures-far-largeobject.jpg)<br>
       **大型物件**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>手部與 6 DoF 控制器之間的對稱設計 

一開始，用於遠距互動的指向和行動概念是針對混合實境入口 (MRP) 所建立及定義，在該入口中，使用者會戴著沉浸式頭戴裝置，並透過運動控制器來與 3D 物件互動。 運動控制器會發射光線來指向及操作遠方物件。 控制器上有按鈕，可用來進一步執行不同動作。 我們運用光線的互動模型，並將其連結至雙手。 透過此對稱設計，熟悉 MRP 的使用者在使用 HoloLen 2 時，不需要學習另一個用於遠端指向及操作的互動模型，反之亦然。    

:::row:::
    :::column:::
        ![使用控制器的光線對稱式設計](images/symmetric-design-for-rays-controllers.jpg)<br>
        **控制器光線**<br>
    :::column-end:::
    :::column:::
        ![使用手部的光線對稱式設計](images/symmetric-design-for-rays-hands.jpg)<br>
        **手部光線**<br>
    :::column-end:::
:::row-end:::

<br>


---

## <a name="hand-ray-in-mrtk-mixed-reality-toolkit-for-unity"></a>MRTK (混合實境工具組) 中適用於 Unity 的手部射線
根據預設，MRTK 會提供一個手部射線 prefab ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers))，其與命令介面的系統手部射線具有相同視覺狀態。 它是在 MRTK 輸入設定檔的 [指標] 下進行指派。 在沉浸式頭戴裝置中，相同的光線會用於運動控制器。

* [MRTK - 指標設定檔](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [MRTK - 輸入系統](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [MRTK - 指標](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)


---

## <a name="see-also"></a>另請參閱
* [手部直接操作](direct-manipulation.md)
* [目光和行動](gaze-and-commit.md)
* [手 - 直接操作](direct-manipulation.md)
* [手 - 手勢](gaze-and-commit.md#composite-gestures)
* [本能互動](interaction-fundamentals.md)
