---
title: 快速入門教學課程-3。 建立使用者介面和設定混合現實工具組
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 067832a130f130ffbaa8d455007b8e77e1b13671
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77130511"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3. 建立使用者介面和設定混合現實工具組
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

在上一個教學課程中，您已瞭解混合現實工具組（MRTK）透過啟動第一個 HoloLens 的應用程式所提供的一些功能。 在本教學課程中，您將學習如何建立和組織按鈕以及 UI 文字面板，並使用預設互動（觸控）與每個按鈕互動。 此外，您還會探索如何新增簡單的動作和效果，例如變更物件的大小、音效和色彩。 本課程模組將介紹有關修改 MRTK 設定檔的基本概念，從關閉[空間對應](spatial-mapping.md)網格視覺效果開始。

## <a name="objectives"></a>目標

* 自訂和設定混合實境工具組設定檔
* 使用 UI 元素和按鈕與全息影像互動
* 基本的「手部追蹤」輸入和互動

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>如何設定混合現實工具組設定檔（變更空間感知顯示選項）
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

在本節中，您將瞭解如何自訂和設定預設的 MRTK 設定檔。

此特定範例將示範如何藉由變更空間網格觀察者的設定，來隱藏空間感知網格。 不過，您可以遵循這些相同的原則，自訂 MRTK 設定檔中的任何設定或值。

隱藏空間感知網格所需採取的主要步驟如下：

1. 複製預設設定設定檔
2. 啟用空間感知系統
3. 複製預設空間感知系統設定檔
4. 複製預設空間感知網格觀察者設定檔
5. 變更空間感知網格的可見度

> [!NOTE]
> 根據預設，您無法編輯 MRTK 設定檔。 這些是預設設定檔範本，您必須先加以複製，才能進行編輯。 有數個嵌套的設定檔層。 因此，在設定一或多個設定時，通常會複製並編輯數個設定檔。

### <a name="1-clone-the-default-configuration-profile"></a>1. 複製預設設定設定檔

> [!NOTE]
> 設定設定檔是最上層的設定檔。 因此，若要能夠編輯任何其他設定檔，您必須先複製設定設定檔。

在 [階層] 視窗中選取**MixedRealityToolkit**物件之後，在 [偵測器] 視窗中，按一下 [**複製 & 自訂**] 按鈕，以開啟 [複製設定檔] 視窗：

![mrlearning-基底](images/mrlearning-base/tutorial2-section1-step1-1.png)

在 [複製設定檔] 視窗中，按一下 [**複製**] 按鈕，以建立**DefaultHololens2ConfigurationProfile**的可編輯複本：

![mrlearning-基底](images/mrlearning-base/tutorial2-section1-step1-2.png)

新建立的設定檔現在已指派為您場景的設定檔：

![mrlearning-基底](images/mrlearning-base/tutorial2-section1-step1-3.png)

在 Unity 功能表中 **，選取** 檔案 > **儲存** 以儲存場景。

> [!TIP]
> 請記得在整個教學課程中儲存工作。

### <a name="2-enable-the-spatial-awareness-system"></a>2. 啟用空間感知系統

在 [階層] 視窗中仍然選取**MixedRealityToolkit**物件，在 [偵測器] 視窗中，選取 [**空間感知**] 索引標籤，然後核取 [**啟用空間感知系統**] 核取方塊：

![mrlearning-基底](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. 複製預設空間感知系統設定檔

在 [**空間感知**] 索引標籤中，按一下 [**複製**] 按鈕以開啟 [複製設定檔] 視窗：

![mrlearning-基底](images/mrlearning-base/tutorial2-section1-step3-1.png)

在 [複製設定檔] 視窗中，按一下 [**複製**] 按鈕，以建立**DefaultMixedRealitySpatialAwarenessSystemProfile**的可編輯複本：

![mrlearning-基底](images/mrlearning-base/tutorial2-section1-step3-2.png)

新建立的空間感知系統設定檔現在會自動指派給您的設定設定檔：

![mrlearning-基底](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. 複製預設空間感知網格觀察者設定檔

在仍選取 [**空間感知**] 索引標籤的情況下，展開 [ **Windows Mixed Reality 空間網格觀察**者] 區段，然後按一下 [**複製**] 按鈕以開啟 [複製設定檔] 視窗：

![mrlearning-基底](images/mrlearning-base/tutorial2-section1-step4-1.png)

在 [複製設定檔] 視窗中，按一下 [**複製**] 按鈕，以建立**DefaultMixedRealitySpatialAwarenessMeshObserverProfile**的可編輯複本：

![mrlearning-基底](images/mrlearning-base/tutorial2-section1-step4-2.png)

新建立的空間感知網格觀察者設定檔現在會自動指派給您的空間感知系統設定檔：

![mrlearning-基底](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. 變更空間感知網格的可見度

在 [**空間網格觀察**者] 設定中，將 [**顯示] 選項**變更為 [**遮蔽**]，讓空間對應網格在正常運作時不可見：

![mrlearning-基底](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> 雖然空間對應網格看不到，但仍存在且正常運作。 例如，空間對應網格背後的任何全息影像（例如，實體牆後方的全息圖）將不會顯示。

您方才已了解如何修改 MRTK 設定檔中的設定。 如您所見，為了自訂 MRTK 設定，您必須先建立預設設定檔的複本。 由於預設設定檔無法編輯，因此如果您想要還原為預設設定，則一律會將它們當做參考。 若要深入瞭解 MRTK 設定檔及其架構，您可以造訪[MRTK 檔入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[混合現實工具組設定檔設定指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)。

## <a name="hand-tracking-gestures-and-interactable-buttons"></a>手形追蹤筆勢和可互動按鈕

在本節中，您將瞭解如何使用「手動追蹤」來按下按鈕並觸發事件，以在按下按鈕時引發動作。

此特定範例將示範如何在按下按鈕時變更 cube 的色彩，並在放開按鈕時，將它變更回原始色彩。 不過，您可以遵循這些相同的原則來建立其他事件。

您需要變更 cube 色彩的主要步驟如下：

1. 將 pressable 按鈕 prefab 新增至場景
2. 將 cube 新增至場景
3. 設定 InteractableOnPressReceiver 事件種類
4. 設定 cube 以在按下事件時接收
5. 定義要在按下事件時觸發的動作
6. 設定 cube 以接收發行前事件
7. 定義要由「發行」事件觸發的動作
8. 使用編輯器內模擬來測試按鈕

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a>1. 將 pressable 按鈕 prefab 新增至場景

> [!TIP]
> <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">Prefab</a>是預先設定的 GameObject，儲存為 Unity 資產，並可在整個專案中重複使用。

在 [**專案] 視窗**中，搜尋**PressableButtonHoloLens2**以找出您將在此範例中使用的 prefab：

![mrlearning-基底](images/mrlearning-base/tutorial2-section2-step1-1.png)

在**搜尋**結果中，選取 [ **PressableButtonHoloLens2** ] prefab，並**將它拖曳** **至 [階層] 視窗，將**它新增至您的場景：

![mrlearning-基底](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> 若要顯示您的場景（如下圖所示），請按兩下 [階層] 視窗中的 [PressableButtonHoloLens2] 物件，使其成為焦點，然後使用場景<a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Gizmo</a>（位於場景視窗的右上角），將視角調整為沿著正向 Z 軸。

在仍選取 PressableButtonHoloLens2 物件的情況下，在 [偵測**器**] 視窗中：

* 變更其 [轉換**位置**]，使其定位於位於來源的相機前方，例如 x = 0、y = 0 和 z = 0。5

![mrlearning-基底](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> 一般而言，Unity 中的1個位置單位大致等同于實體世界中的1個計量。 不過，這有一些例外狀況，例如，當物件是縮放物件的子系時。

### <a name="2-add-a-cube-to-the-scene"></a>2. 將 cube 新增至場景

以滑鼠右鍵按一下 [階層] 視窗內的空白位置，然後選取 [ **3D 物件** > **Cube** ]，將 cube 新增至您的場景：

![mrlearning-基底](images/mrlearning-base/tutorial2-section2-step2-1.png)

在仍選取 Cube 物件的情況下，在 [偵測**器**] 視窗中：

* 變更其轉換**位置**，使其位於 [pressable] 按鈕附近，但不會與它重迭，例如 x = 0、y = 0.04 和 z = 0。5
* 將其轉換**調整**為適當的大小，例如 x = 0.02、y = 0.02 和 z = 0.02

![mrlearning-基底](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a>3. 設定 InteractableOnPressReceiver 事件種類

在 [階層] 視窗中選取 PressableButtonHoloLens2 物件之後，在 [偵測**器**視窗]**漢堡功能表**中，選取 [ **Collaps 所有元件**] 以取得此物件上所有元件的總覽：

![mrlearning-基底](images/mrlearning-base/tutorial2-section2-step3-1.png)

展開 [**可互動（腳本）** ] 元件，然後找出並展開 [**事件** > **接收者**] 區段：

![mrlearning-基底](images/mrlearning-base/tutorial2-section2-step3-2.png)

針對 [事件接收器類型**InteractableOnPressReceiver**]，將 [**互動] 篩選**變更為 [**近到目前**]：

![mrlearning-基底](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> 名為 InteractableOnPressReceiver 的事件接收器型別，可讓按鈕在追蹤的手按下按鈕時，回應按下的事件。

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a>4. 設定 cube 以在按下事件時接收

從 [階層] 視窗中，**按一下並將** **cube**拖曳至 [**按下（）** ] 事件的 [**事件**內容] 物件欄位中，將 cube 指派為按下（）事件的接收者：

![mrlearning-基底](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a>5. 定義要在按下事件時觸發的動作

按一下 [動作] 下拉式清單（目前**未指派任何**函式），然後選取 [ **MeshRenderer** > **材質材質**]，將 Cube 的材質屬性設定為在觸發 On 按（）事件時變更：

![mrlearning-基底](images/mrlearning-base/tutorial2-section2-step5-1.png)

按一下 [材質] 欄位旁的小**圓圈**圖示，目前已填入 [**無（材質）** ]，以開啟 [選取材質] 視窗：

![mrlearning-基底](images/mrlearning-base/tutorial2-section2-step5-2.png)

在 [選取材質] 視窗中，**搜尋** **MRTK_Standard**並選取適當的資料，例如， **MRTK_Standard_Cyan**因此當按下按鈕時，Cube 的色彩會變更為青色：

![mrlearning-基底](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a>6. 設定 cube 以接收發行前事件

**重複**「發行時」事件的步驟4，將 Cube 指派為「On 發行」（）事件的接收者。

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a>7. 定義要由「發行」事件觸發的動作

**重複**[On Release] 事件的步驟5，但選擇 [ **MRTK_Standard_LightGray** ] 材質，讓 Cube 的色彩在放開按鈕時回到其原始的淺灰色色彩：

![mrlearning-基底](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a>8. 使用編輯器內模擬來測試按鈕

按下 [**播放**] 按鈕進入遊戲模式，並使用編輯器內的輸入模擬來測試新設定的按鈕。

未按下按鈕（空格鍵 + 滑鼠滾輪向後回溯）：

![mrlearning-基底](images/mrlearning-base/tutorial2-section2-step8-1.png)

已按下按鈕（空格鍵 + 滑鼠滾輪向前滾動）：

![mrlearning-基底](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> 若要瞭解如何使用編輯器內的輸入模擬，您可以參考[MRTK 檔入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[使用編輯器中的手寫輸入模擬來測試場景](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)指南。

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>使用 MRTK 的方格物件集合來建立按鈕面板

在本節中，您將學習如何使用 MRTK 的 Grid 物件集合工具，自動將多個按鈕對齊整齊的使用者介面。

此特定範例將示範如何建立一個水準對齊五個按鈕的面板。 不過，您可以遵循這些相同的原則來建立其他版面配置。

達成此目標所需採取的主要步驟如下：

1. 父系按鈕物件至父物件
2. 加入和設定 Grid 物件集合（腳本）元件
3. 使用編輯器內模擬來測試按鈕

### <a name="1-parent-the-button-objects-to-a-parent-object"></a>1. 將按鈕物件父系到父物件

以滑鼠右鍵按一下 [階層] 視窗內的空白位置，然後選取 [**建立空**的]：

![mrlearning-基底](images/mrlearning-base/tutorial2-section3-step1-1.png)

以滑鼠右鍵按一下新建立的物件，並選取 [**重新命名**]，然後指定適當的名稱，例如**ButtonCollection**：

![mrlearning-基底](images/mrlearning-base/tutorial2-section3-step1-2.png)

選取**PressableButtonHoloLens2**物件，並**將它拖曳**至**ButtonCollection**物件的上方，使其成為 ButtonCollection 物件的子系：

![mrlearning-基底](images/mrlearning-base/tutorial2-section3-step1-3.png)

在**PressableButtonHoloLens2**物件上按一下滑鼠右鍵，然後選取 [**複製**]，以建立其複本：

![mrlearning-基底](images/mrlearning-base/tutorial2-section3-step1-4.png)

**重複**此步驟四次，直到總共有五個 PressableButtonHoloLens2 物件為止。

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2. 加入及設定 Grid 物件集合（腳本）元件

在 [階層] 視窗中選取 ButtonCollection 物件之後，在 [偵測器] 視窗中，按一下 [**加入元件**] 按鈕，然後搜尋並選取 [**方格物件集合**]，將 Grid 物件集合（腳本）元件加入至 ButtonCollection 物件：

![mrlearning-基底](images/mrlearning-base/tutorial2-section3-step2-1.png)

設定 Grid 物件集合（腳本），如下所示：

* 將 [Num] 資料**列**變更為 [1]，讓所有按鈕對齊一個單一資料列
* 將資料**格寬度**變更為0.05，以將資料列內的按鈕變成空白

然後按一下 [**更新集合**] 按鈕以套用新的設定：

![mrlearning-基底](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> 您剛才套用的設定變更代表達到將按鈕放在單一資料列的目標所需的最小變更。 不過，在未來的專案中，視因素（例如，父系和子物件的方向）而定，您可能需要調整其他設定（例如，方向類型）。 若要深入瞭解 MRTK 的方格物件集合，您可以造訪[MRTK 檔入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[物件集合腳本](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts)指南。

在 [階層] 視窗中仍然選取 ButtonCollection 物件時，在 [偵測器] 視窗中，變更 ButtonCollection 物件的轉換**位置**，讓其子按鈕物件位於相機前方，例如 x = 0、y = 0 和 z = 0.5：

![mrlearning-基底](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> 當您第一次將 PressableButtonHoloLens2 prefab 新增至上方的 [[右手追蹤筆勢] 和 [可互動按鈕](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)] 區段中的場景時，您會將它放在相機前方。 不過，由於 Grid 物件集合會控制其直屬子物件的位置，因此根據格線物件集合的預設距離0的父代值，PressableButtonHoloLens2 子物件的 Z 位置已重設為0。 這是為了讓父/子位置的關聯性保持組織，這就是為什麼我們會將父 ButtonCollection 物件的位置向前移動，而不是設定從父系值到向前移動 PressableButtonHoloLens2 子物件的距離。

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a>3. 使用編輯器內模擬來測試按鈕

按下 [播放] 按鈕進入遊戲模式，並使用編輯器內的輸入模擬來測試新建立的按鈕面板中的每個按鈕：

![mrlearning-基底](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> 目前，當您按五個按鈕的任一個時，cube 色彩會變更為青色。 若要讓體驗更加有趣，請使用您剛學習的內容，設定每個按鈕將 cube 變更為不同的色彩。

## <a name="adding-text-into-your-scene"></a>將文字新增至您的場景

在本節中，您將瞭解如何使用 Unity 的 TextMesh Pro （您在上一個教學課程的匯[入 TextMesh Pro 基本資源](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)一節中所準備），將文字新增至您的混合現實體驗。

在此特定範例中，您會在上一節中建立的按鈕集合底下新增一個簡單標籤。

以滑鼠右鍵按一下 [ButtonCollection] 物件，然後選取 [ **3D 物件**] > [ **TextMeshPro** ]，將 TextMeshPro 物件建立為 ButtonCollection 物件的子系：

![mrlearning-基底](images/mrlearning-base/tutorial2-section4-step1-1.png)

當新建立的 TextMeshPro 物件（名為 Text （TMP））仍為選取狀態時，在 [偵測器] 視窗中，變更其位置和大小，讓標籤整齊地放在按鈕集合底下，例如：

* 將矩形轉換**Pos Y**變更為-0.0425
* 將 [矩形轉換**寬度**] 變更為0.24
* 將矩形轉換**高度**變更為0.024

然後更新文字以反映標籤的用途，並選擇 [字型屬性]，讓文字元合標籤，例如：

* 將文本網格 Pro （腳本）**文字**變更為按鈕集合
* 將文本網格 Pro （腳本）**字型樣式**變更為粗體
* 將文本網格 Pro （腳本）**字型大小**變更為0。2
* 將文本網格 Pro （腳本）**對齊**變更為置中和中間

![mrlearning-基底](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a>恭喜

在本教學課程中，您已瞭解如何複製、自訂和設定 MRTK 設定檔設定。 您也已瞭解如何與按鈕互動，以使用 HoloLens 2 上的追蹤來觸發事件。 最後，您已瞭解如何使用 MRTK 的 Grid 物件集合元件和 Unity 的文本網格 Pro 來建立簡單的 UI 介面。

[下一個教學課程： 4. 放置動態內容並使用解析器](mrlearning-base-ch3.md)
