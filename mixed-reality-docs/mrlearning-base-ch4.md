---
title: 入門教學課程 - 5。 與 3D 物件互動
description: 了解基本 3D 內容和使用者體驗，例如針對基本操作組織 3D 物件和周框方塊。
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 65bcef6a7c10450816d7a928302b0b266b132f0f
ms.sourcegitcommit: 536fd45b48a70bbeca1454cef517ae007225e533
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80362068"
---
# <a name="5-interacting-with-3d-objects"></a>5.與 3D 物件互動

在本教學課程中，您將了解基本的 3D 內容和使用者體驗，例如將 3D 物件組織為集合的一部分、基本操作所需的周框方塊、遠近互動，以及手部追蹤的觸控和抓取手勢。

## <a name="objectives"></a>目標

* 建立將用於其他學習目標的 3D 物件面板
* 實作週框方塊
* 設定 3D 物件以進行基本操作 (例如移動、旋轉和縮放)
* 探索遠近互動
* 了解其他手部追蹤手勢，例如抓取和觸控

## <a name="importing-the-tutorial-assets"></a>匯入教學課程資產

下載並匯入 Unity 自訂套件：

* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)

匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> 如需有關如何匯入 Unity 自訂套件的提示，您可以參閱[匯入混合實境工具組](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) 的指示。

## <a name="decluttering-the-scene-view"></a>整理場景檢視

若要更簡便地使用場景，請按一下**立方體**和 **ButtonCollection** 物件左邊的**眼睛**圖示，將這些項目的**場景可見度**設為關閉。 這會在場景視窗中隱藏物件，而不會變更其遊戲內的可見度：

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> 若要深入了解場景可見度的控制項，以及如何使用其來最佳化場景檢視和工作流程，您可以瀏覽 Unity 的<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">場景可見度</a>文件。

## <a name="organizing-3d-objects-in-a-collection"></a>組織集合中的 3D 物件

您將在本節建立 3D 物件的面板，並在本教學課程的後續各節中，使用此面板來探索與 3D 物件互動的各種方式。 具體而言，您會將 3D 物件的位置設定在 3 x 3 的方格上。

與[建立按鈕面板](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection)時類似，達成此動作所需採取的主要步驟如下：

1. 使 3D 物件歸屬於父物件
2. 新增和設定 Grid Object Collection (指令碼) 元件

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a>1.使 3D 物件歸屬於父物件

在 [階層] 視窗中，**建立空白物件**、提供適當的名稱 (例如 **3DObjectCollection**)，然後將其放在適當的位置，例如 X = 0、Y =-0.2、Z = 2。

在 [專案] 視窗中，瀏覽至 [資產]   > [MRTK.Tutorials.GettingStarted]   > [Prefabs]  ，然後使 **3DObjectCollection** 成為下列 Prefab 的**父系**：

* Cheese
* CoffeeCup
* EarthCore
* Octa
* Platonic
* TheModule

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

在 [階層] 視窗中，**建立三個立方體**來作為 **3DObjectCollection** 的子物件，並將其變形**縮放**調整為 X = 0.15，Y = 0.15，Z = 0.15：

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

> [!TIP]
> 如需如何執行上述步驟的提示，您可以參閱[建立使用者介面和設定混合實境工具組](mrlearning-base-ch2.md)教學課程。

重新調整立方體的位置，讓您可以看到每個立方體：

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

在 [專案] 視窗中，瀏覽至 [資產]   > [MixedRealityToolkit]   > [StandardAssets]   > [材質]  ，以查看 MRTK 所提供的材質。

**按一下並拖曳**適當材質到每個立方體網格轉譯器的  「元素 0」屬性，例如：

* MRTK_Standard_GlowingCyan
* MRTK_Standard_GlowingOrange
* MRTK_Standard_Green

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2.新增和設定 Grid Object Collection (指令碼) 元件

將 **Grid Object Collection (指令碼)** 元件新增至 **3DObjectCollection** 物件，並依照下列方式進行設定：

* 將**排序類型**變更為**子系順序**，以確保子物件會依照您將其放在父物件底下的順序排序

然後按一下 [更新集合]  按鈕以套用新的設定：

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a>操作 3D 物件

在本節中，您將新增一個功能，也就是您可以在上一節建立的面板中操作所有 3D 物件。 此外，針對 Prefab 物件，您可以讓使用者透過追蹤的手部來觸及並抓取這些物件。 然後您會探索幾個可套用至物件的操作行為。

達成此動作所需採取的主要步驟如下：

1. 將 Manipulation Handler (指令碼) 元件新增至所有物件
2. 將 Near Interaction Grabbable (指令碼) 元件新增至 Prefab 物件
3. 設定 Manipulation Handler (指令碼) 元件

> [!IMPORTANT]
> 若要能夠**操作物件**，該物件必須具有下列元件：
>
> * **Collider** 元件，例如 Box Collider
> * **Manipulation Handler (指令碼)** 元件
>
> 若要能夠以追蹤的手部**操作**及**抓取物件**，該物件必須具有下列元件：
>
> * **Collider** 元件，例如 Box Collider
> * **Manipulation Handler (指令碼)** 元件
> * **Near Interaction Grabbable (指令碼)** 元件

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a>1.將 Manipulation Handler (指令碼) 元件新增至所有物件

在 [階層] 視窗中，選取 **Cheese** 物件，按住 **Shift** 鍵，然後選取**Cube () 2** 物件，並將 **Manipulation Handler (指令碼)** 元件新增至所有物件：

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> 基於本教學課程的目的，碰撞器 (Collider) 已新增至 Prefab。 針對 Unity 基本類型 (例如立方體物件)，Collider 元件會在物件建立時自動新增。 在上圖中，碰撞器是以綠色外框表示。 若要深入了解碰撞器，您可以造訪 Unity 的<a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">碰撞器 (Collider)</a> 文件。

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a>2.將 Near Interaction Grabbable (指令碼) 元件新增至 Prefab 物件

在 [階層] 視窗中，選取 **Cheese** 物件，按住 **Shift** 鍵，然後選取 **TheModule** 物件，並將 **Near Interaction Grabbable (指令碼)** 元件新增至所有物件：

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a>3.設定 Manipulation Handler (指令碼) 元件

#### <a name="default-manipulation"></a>預設操作

針對**立方體**物件，請保留所有預設屬性，以體驗預設的操作行為：

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> 若要將元件重設為預設值，您可以選取元件的 [設定] 圖示，然後選取 [重設]。

#### <a name="restrict-manipulation-to-scale-only"></a>將操作限制為僅限縮放

針對 **Cube (1)** 物件，請將**縮放**的**兩手操作類型**變更為只允許使用者變更物件的大小：

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a>將移動限制為與使用者的固定距離

針對 **Cube (2)** 物件，請將 [移動限制]  變更為**與手部的固定距離**，如此一來，當物件移動時，物件就會與使用者保持相同的距離：

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a>預設抓取操作

針對 **Cheese**、**CoffeCup**和 **EarthCore** 物件，請保留所有預設屬性，以體驗預設的抓取操作行為：

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a>移除遠端操作的能力

針對 **Octa** 物件，請取消勾選 [允許遠端操作]  核取方塊，讓使用者只能使用追蹤的手部直接與物件互動：

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a>使物件繞著中心旋轉

針對 **Platonic** 物件，請將**近處單手旋轉模式**和**遠處單手旋轉模式**變更為**繞著物件中心旋轉**，讓使用者以單手旋轉物件時，物件能繞著其中心旋轉：

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="keep-movement-after-object-is-released"></a>物件釋放後繼續移動

針對 **TheModule** 物件，新增 **Rigidbody** 元件以啟用物理特性，然後取消核取 [使用引力]  核取方塊，讓物件不會受到引力的影響：

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

回到 Manipulation Handler (指令碼) 元件，確認 [放開行為]  已設定為 [保持速度]  和 [保持角速度]  ，如此一來，物件從使用者的手中放開時，仍會繼續移動：

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-8.png)

若要深入了解操作處理器元件及其相關聯的屬性，您可以瀏覽 [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[操作處理器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) 指南。

## <a name="adding-bounding-boxes"></a>新增週框方塊

周框方塊藉由提供可用於縮放和旋轉的控點，讓您能夠更輕鬆且更直覺地以單手操作可遠近互動的物件。

在此範例中，您會將周框方塊新增至 EarthCore 物件，讓此物件現在可以使用您在上一節中設定的物件操作來與之互動，以及使用周框方塊控點來縮放和旋轉。

> [!IMPORTANT]
> 若要能夠使用**周框方塊**，該物件必須具有下列元件：
>
> * **Collider** 元件，例如 Box Collider
> * **Bounding Box (指令碼)** 元件

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a>1.將 Bounding Box (指令碼) 元件新增至 EarthCore 物件

在 [偵測器] 視窗中，選取 **EarthCore** 物件，並將 **Bounding Box (指令碼)** 元件新增至 EarthCore 物件：

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> 周框方塊視覺效果會在執行階段中建立，因此在您進入遊戲模式之前看不到該效果。

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a>2.使用編輯器內模擬來視覺化和測試周框方塊

按下 [開始遊戲] 按鈕進入遊戲模式。 然後按住空格鍵以顯示手部，並使用滑鼠來與周框方塊互動：

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

若要深入了解 Bounding Box 元件和其相關聯的屬性，您可以瀏覽 [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[周框方塊](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)指南。

## <a name="adding-touch-effects"></a>新增觸控效果

在此範例中，您將會啟用當您以手部觸碰物件時所要觸發的事件。 具體而言，您會將 Octa 物件設定為在使用者與之接觸時播放音效。

達成此動作所需採取的主要步驟如下：

1. 將音訊來源元件新增至物件中
2. 將 Near Interaction Touchable (指令碼) 元件新增至物件
3. 將 Hand Interaction Touch (指令碼) 元件新增至物件
4. 執行 On Touch Started 事件
5. 使用編輯器內的模擬來測試觸控互動

> [!IMPORTANT]
> 若要能夠**觸發觸控事件**，該物件必須具有下列元件：
>
> * **Collider** 元件，最好是 Box Collider
> * **Near Interaction Touchable (指令碼)** 元件
> * **Hand Interaction Touch (指令碼)** 元件

> [!NOTE]
> Hand Interaction Touch (指令碼) 元件不是 MRTK 的一部分。 該元件隨著本教學課程的資產一起匯入，原本是 MixedReality 工具組 Unity 範例的一部份。

### <a name="1-add-an-audio-source-component-to-the-object"></a>1.將音訊來源元件新增至物件中

在 [階層] 視窗中，選取 **Octa** 物件，將**音訊來源**元件新增至顆 Octa 物件，然後將**空間混合**變更為 1，以啟用空間音訊：

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a>2.將 Near Interaction Touchable (指令碼) 元件新增至物件

在仍選取 **Octa** 物件的情況下，將 **Near Interaction Touchable (指令碼)** 元件新增至 Octa 物件，然後按一下 [修正周框]  和 [修正中心]  按鈕，以更新 Near Interaction Touchable (指令碼) 的區域中心和界限屬性來符合 BoxCollider：

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a>3.將 Hand Interaction Touch (指令碼) 元件新增至物件

在仍選取 **Octa** 物件的情況下，將 **Hand Interaction Touch (指令碼)** 元件新增至 Octa 物件：

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a>4.執行 On Touch Started 事件

在 **Hand Interaction Touch (指令碼)** 元件上按一下小的 **[+]** 圖示，即可建立新的 **On Touch Started ()** 事件。 然後設定 **Octa** 物件以接收事件，並將 **AudioSource.PlayOneShot** 定義為要觸發的動作：

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

瀏覽至 [資產]   > [MixedRealityToolkit.SDK]   > [StandardAssets]   > [音訊]  材質，以查看 MRTK 所提供的音訊片段，然後將適當的音訊片段指派給 [音訊片段]  欄位，例如 MRTK_Gem 音訊片段：

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> 如需有關如何實作事件的提示，您可以參閱[手部追蹤手勢和可互動按鈕](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)的指示。

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a>5.使用編輯器內的模擬來測試觸控互動

按下 [開始遊戲] 按鈕進入遊戲模式。 然後按住空格鍵以顯示手部，並使用滑鼠來碰觸 Octa 物件及觸發音效：

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> 如上圖所示，當您在測試觸控互動時，您會看到 Octa 物件的顏色閃爍。 此效果已硬式編碼到 Hand Interaction Touch (指令碼) 元件中，而不是您在上述步驟中完成的事件設定結果。
>
> 如果您想要停用此效果，您可以在第 32 行上加上 'TargetRenderer = GetComponentInChildren<Renderer>();' 註解，這會使得 TargetRenderer 保持 Null，並讓色彩不會閃爍。

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已了解如何在方格集合中組織 3D 物件以及如何使用近距互動 (使用手部追蹤直接抓取) 和遠距互動 (使用目光或手動光線) 來操作這些物件 (縮放、旋轉和移動)。 您也已了解如何在 3D 物件周圍放置週框方塊，並了解如何在週框方塊上使用和自訂控點。 最後，您學習到觸控物件時如何觸發事件。

[下一課：6.探索進階的輸入選項](mrlearning-base-ch5.md)
