---
title: 快速入門教學課程-5。 與3D 物件互動
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: a1b26d56b4693ef23f2d77ba53e0961693489a3a
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77130237"
---
# <a name="5-interacting-with-3d-objects"></a>5. 與3D 物件互動

在本教學課程中，您將瞭解基本的3D 內容和使用者體驗，例如將3D 物件組織為集合的一部分、進行基本操作的周框方塊、近遠的互動，以及觸控和抓取手勢與手動追蹤。

## <a name="objectives"></a>目標

* 建立將用於其他學習目標的3D 物件面板
* 實作週框方塊
* 設定3D 物件進行基本操作，例如移動、旋轉和縮放
* 探索遠近互動
* 深入瞭解其他的右手邊追蹤手勢，例如「抓取」和「觸控」

## <a name="importing-the-tutorial-assets"></a>匯入教學課程資產

下載並匯入 Unity 自訂套件：

* [MRTK.HoloLens2 GettingStarted. 2.2.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.2.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.2.0.0.unitypackage)

匯入教學課程資產之後，您的 [專案] 視窗看起來應該如下所示：

![mrlearning-基底](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> 如需有關如何匯入 Unity 自訂套件的提醒，您可以參閱匯[入混合現實工具](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)組指示。

## <a name="decluttering-the-scene-view"></a>Decluttering 場景視圖

若要讓您更輕鬆地使用場景，請按一下物件左側的**眼睛**圖示，將 Cube 和 ButtonCollection 物件的**場景可見度**設定為 [關閉]。 這會在場景視窗中隱藏物件，而不會變更其遊戲內可見度：

![mrlearning-基底](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> 若要深入瞭解場景可見度控制項，以及如何使用它們來優化場景視圖和工作流程，您可以造訪 Unity 的<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">場景可見度</a>檔。

## <a name="organizing-3d-objects-in-a-collection"></a>組織集合中的3D 物件

在本節中，您將建立3D 物件的面板，當您在本教學課程的下列各節中探索與3D 物件互動的各種方式時，將會用到它。 具體而言，您會將3D 物件設定為置於 3 x 3 方格上。

類似于當您[建立按鈕的面板](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection)時，要達到此目標所要採取的主要步驟如下：

1. 將3D 物件父系到父物件
2. 加入和設定 Grid 物件集合（腳本）元件

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a>1. 將3D 物件父系到父物件

在 [階層] 視窗中，**建立空的物件**、提供適當的名稱（例如**3DObjectCollection**），並將它放在適當的位置，例如 X = 0、Y =-0.2、Z = 2。

在 [專案] 視窗中，流覽至 [**資產**] [ > **MRTK]。GettingStarted** > **Prefabs**，然後將下列 Prefabs 的**父系**加入**3DObjectCollection**：

* 比薩餅
* CoffeeCup
* EarthCore
* 顆 octa
* Platonic
* TheModule

![mrlearning-基底](images/mrlearning-base/tutorial4-section3-step1-1.png)

在 [階層] 視窗中，**建立三個 cube**做為**3DObjectCollection**的子物件，並將其轉換**規模**設定為 X = 0.15、Y = 0.15、Z = 0.15：

![mrlearning-基底](images/mrlearning-base/tutorial4-section3-step1-2.png)

<!-- TODO: Finish -->
> [!TIP]
> 如需有關如何執行上述步驟的提醒，您可以參閱[建立使用者介面和設定混合現實工具](mrlearning-base-ch2.md)組教學課程。

重新調整 cube 的位置，讓您可以看到每個 cube：

![mrlearning-基底](images/mrlearning-base/tutorial4-section3-step1-3.png)

在 [專案] 視窗中，流覽至 [**資產**] [ > **MixedRealityToolkit** ] [ > **StandardAssets** > **材質**]，以查看 MRTK 所提供的材質。

**按一下並拖曳**適當的資料到每個 Cube 的網格轉譯器**材質**元素0屬性，例如：

* MRTK_Standard_GlowingCyan
* MRTK_Standard_GlowingOrange
* MRTK_Standard_Green：

![mrlearning-基底](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2. 加入及設定 Grid 物件集合（腳本）元件

將**Grid 物件集合（腳本）** 元件新增至3DObjectCollection 物件，並將其設定如下：

* 將 [**排序類型**] 變更為 [子順序]，以確保子物件會依照您放在父物件底下的順序排序

然後按一下 [**更新集合**] 按鈕以套用新的設定：

![mrlearning-基底](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a>操作3D 物件

在本節中，您將新增在上一節中建立的面板中操作所有3D 物件的功能。 此外，針對 prefab 物件，您可以讓使用者透過追蹤的手觸達這些物件，並將其抓取。 然後您會探索幾個可套用至物件的操作行為。

達成此目標所需採取的主要步驟如下：

1. 將操作處理常式（腳本）元件新增至所有物件
2. 將近乎互動 Grabbable （腳本）元件新增至 prefab 物件
3. 設定操作處理常式（腳本）元件

> [!IMPORTANT]
> 若要能夠**操作物件**，物件必須具有下列元件：
>
> * **碰撞**元件，例如 Box 碰撞
> * **操作處理常式（腳本）** 元件
>
> 若要能夠**操作**和**抓取具有已追蹤手的物件**，物件必須具有下列元件：
>
> * **碰撞**元件，例如 Box 碰撞
> * **操作處理常式（腳本）** 元件
> * **近乎互動 Grabbable （腳本）** 元件

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a>1. 將操作處理常式（腳本）元件加入至所有物件

在 [階層] 視窗中，選取 [**乳酪**] 物件，按住**Shift**鍵，然後選取**Cube （）** 物件，並將**操作處理常式（腳本）** 元件加入至所有物件：

![mrlearning-基底](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> 基於本教學課程的目的，colliders 已新增至 prefabs。 對於 Unity 基本類型（例如 Cube 物件），當建立物件時，會自動新增碰撞元件。 在上圖中，colliders 是以綠色外框表示。 若要深入瞭解 colliders，您可以造訪 Unity 的<a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">碰撞</a>器檔。

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a>2. 將近乎互動 Grabbable （腳本）元件新增至 prefab 物件

在 [階層] 視窗中，選取 [**乳酪**] 物件，按住**Shift**鍵，然後選取 [ **TheModule** ] 物件，並將**近端互動 Grabbable （腳本）** 元件新增至所有物件：

![mrlearning-基底](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a>3. 設定操作處理常式（腳本）元件

#### <a name="default-manipulation"></a>預設操作

若為**Cube**物件，請保留所有屬性，以體驗預設的操作行為：

![mrlearning-基底](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> 若要將元件重設為預設值，您可以選取元件的 [設定] 圖示，然後選取 [重設]。

#### <a name="restrict-manipulation-to-scale-only"></a>將操作限制為僅限縮放

針對**Cube （1）** 物件，將**兩個右手操作類型**變更為 [調整]，只允許使用者變更物件的大小：

![mrlearning-基底](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a>將移動限制為與使用者的固定距離

針對**Cube （2）** 物件，變更**移動上的條件約束**以修正與 Head 的距離，如此一來，當物件移動時，它就會與使用者保持相同的距離：

![mrlearning-基底](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a>預設 grabbable 操作

針對 [**乳酪**]、[ **CoffeCup**] 和 [ **EarthCore** ] 物件，保留 [所有屬性]，以體驗預設的 grabbable 操作行為：

![mrlearning-基底](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a>移除目前操作的能力

針對**顆 octa**物件，取消核取 [允許最大**操作**] 核取方塊，讓使用者只能使用追蹤的手直接與物件互動：

![mrlearning-基底](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a>使物件繞著中心旋轉

針對**Platonic**物件，請將**一次**左右旋轉模式變更為接近，而在**一種旋轉模式**中旋轉，讓它在使用者手上旋轉物件時，旋轉物件中心：

![mrlearning-基底](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="prevent-movement-after-object-is-released"></a>避免物件釋放後移動

針對**TheModule**物件，將 [**發行行為**] 變更為 [無]，以便在物件從使用者手中釋放之後，不會繼續移動：

![mrlearning-基底](images/mrlearning-base/tutorial4-section4-step3-7.png)

若要深入瞭解操作處理常式元件及其相關聯的屬性，您可以造訪[MRTK 檔入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[操作處理常式](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)指南。

## <a name="adding-bounding-boxes"></a>加入周框方塊

周框方塊藉由提供可用於縮放和旋轉的控制碼，讓您更輕鬆且更直覺地操作物件。

在此範例中，您會將周框方塊新增至 EarthCore 物件，因此這個物件現在可以使用您在上一節中設定的物件操作進行互動，以及使用周框方塊控點來縮放和旋轉。

> [!IMPORTANT]
> 若要能夠使用周**框**方塊，物件必須具有下列元件：
>
> * **碰撞**元件，例如 Box 碰撞
> * 周**框方塊（腳本）** 元件

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a>1. 將周框方塊（腳本）元件新增至 EarthCore 物件

在 [偵測器] 視窗中，選取**EarthCore**物件，並將周**框方塊（腳本）** 元件新增至 EarthCore 物件：

![mrlearning-基底](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> 周框方塊視覺效果是在執行時間建立，因此在您進入遊戲模式之前看不到。

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a>2. 使用編輯器內模擬來視覺化和測試周框方塊

按下 [播放] 按鈕進入遊戲模式。 然後按住空格鍵以顯示手，並使用滑鼠來與周框方塊互動：

![mrlearning-基底](images/mrlearning-base/tutorial4-section5-step2-1.png)

若要深入瞭解周框方塊元件和其相關聯的屬性，您可以造訪[MRTK 檔入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的周[框](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)方塊指南。

## <a name="adding-touch-effects"></a>新增觸控效果

在此範例中，您將會啟用當您以手觸碰物件時所要觸發的事件。 具體而言，您會將顆 octa 物件設定為在使用者接觸時播放音效效果。

達成此目標所需採取的主要步驟如下：

1. 將音訊來源元件新增至物件
2. 將近乎互動 Touchable （腳本）元件新增至物件
3. 將手互動觸控（腳本）元件新增至物件
4. 執行觸控開始事件
5. 使用編輯器內模擬來測試觸控互動

> [!IMPORTANT]
> 若要能夠**觸發觸控事件**，物件必須具有下列元件：
>
> * **碰撞**元件，最好是 Box 碰撞
> * **近乎互動 Touchable （腳本）** 元件
> * **手動互動觸控（腳本）** 元件

> [!NOTE]
> 「手互動觸控」（Script）元件不是 MRTK 的一部分。 本教學課程的資產和原始部分的 MixedReality 工具組 Unity 範例已匯入它。

### <a name="1-add-an-audio-source-component-to-the-object"></a>1. 將音訊來源元件新增至物件

在 [階層] 視窗中，選取 [**顆 octa** ] 物件，將 [**音訊來源**] 元件新增至顆 octa 物件，然後將 [**空間 Blend** ] 變更為1以啟用空間音訊：

![mrlearning-基底](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a>2. 將近乎互動 Touchable （腳本）元件新增至物件

在仍選取**顆 octa**物件的情況下，將**近乎互動 Touchable （腳本）** 元件新增至顆 octa 物件，然後按一下 [**修正界限**] 和 [**修正中心**] 按鈕，將近端互動 Touchable （腳本）的本機中心和界限屬性更新為符合 BoxCollider：

![mrlearning-基底](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a>3. 將手互動觸控（腳本）元件新增至物件

在仍選取**顆 octa**物件的情況下，將「**手動互動觸控」（Script）** 元件新增至顆 octa 物件：

![mrlearning-基底](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a>4. 執行 Touch 已啟動事件

在 [手動互動觸控（腳本）] 元件上，按一下 [小型 **+** ] 圖示，以建立新**的 [觸控已啟動（）** ] 事件。 然後設定**顆 octa**物件以接收事件，並將**spatialize**定義為要觸發的動作：

![mrlearning-基底](images/mrlearning-base/tutorial4-section6-step4-1.png)

流覽至 **資產**  > **MixedRealityToolkit**  > **StandardAssets** > 材質，以查看 MRTK 所提供的音訊剪輯，然後將適當的音訊剪輯指派給 **音訊剪輯** 欄位，例如 MRTK_Gem 的音訊剪輯：

![mrlearning-基底](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> 如需如何執行事件的提醒，您可以參考[手追蹤手勢和可互動按鈕](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)的指示。

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a>5. 使用編輯器內模擬來測試觸控互動

按下 [播放] 按鈕進入遊戲模式。 然後按住空格鍵以帶出手，並使用滑鼠來碰觸顆 octa 物件，並觸發音效效果：

![mrlearning-基底](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> 如上圖所示，當您在測試觸控互動時看到顆 octa 物件色彩 pulsated。 這項效果已硬式編碼到「手互動觸控」（腳本）元件中，而不是您在上述步驟中完成的事件設定結果。
>
> 例如，如果您想要停用此效果，您可以將批註 out 或行 32 ' TargetRenderer = GetComponentInChildren<Renderer>（）; '，這會導致 TargetRenderer 剩餘的 null 和色彩不 pulsating。

## <a name="congratulations"></a>恭喜

在本教學課程中，您已瞭解如何在方格集合中組織3D 物件，以及如何使用近距離互動（直接抓取和旋轉）和即時互動（使用注視光線或手片）來操作這些物件（縮放、旋轉和移動）。 您也學到如何將周框方塊放在3D 物件周圍，學習如何使用和自訂周框方塊上的控點。 最後，您學習到觸控物件時如何觸發事件。

[下一課： 6. 探索 advanced 輸入選項](mrlearning-base-ch5.md)
