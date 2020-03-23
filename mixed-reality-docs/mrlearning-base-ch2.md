---
title: 入門教學課程 - 3。 建立使用者介面並設定混合實境工具組
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: c389c7a3d16770dcbf57d9acdcfd81c6507f7cd6
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376135"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3.建立使用者介面並設定混合實境工具組
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

在上一個教學課程中，您已藉由啟動 HoloLens 2 的第一個應用程式來了解混合實境工具組 (MRTK) 所必須提供的一些功能。 在此教學課程中，您將了解如何建立和組織按鈕及 UI 文字面板，並且會使用預設互動方式 (觸控) 來與每個按鈕互動。 此外，您還會探索如何新增簡單的動作和效果，例如變更物件的大小、音效和色彩。 此課程模組將會從關閉[空間對應](spatial-mapping.md)的網格視覺效果開始，介紹有關修改 MRTK 設定檔的基本概念。

## <a name="objectives"></a>目標

* 自訂和設定混合實境工具組設定檔
* 使用 UI 元素和按鈕來與全像投影互動
* 基本的「手部追蹤」輸入和互動

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>如何設定混合實境工具組設定檔 (變更空間感知顯示選項)
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

在本節中，您將了解如何自訂和設定預設的 MRTK 設定檔。

此特定範例將示範如何藉由變更空間網格觀察器的設定，來隱藏空間感知網格。 不過，您也可以遵循這些相同原則，自訂 MRTK 設定檔中的任何設定或值。

隱藏空間感知網格所需採取的主要步驟如下：

1. 複製預設的組態設定檔
2. 啟用空間感知系統
3. 複製預設的空間感知系統設定檔
4. 複製預設的空間感知網格觀察器設定檔
5. 變更空間感知網格的顯示

> [!NOTE]
> 根據預設，您無法編輯 MRTK 設定檔。 這些是預設的設定檔範本，您必須先加以複製，才能進行編輯。 其中有數個巢狀的設定檔層。 因此，在設定一個或多個設定時，通常會複製及編輯數個設定檔。

### <a name="1-clone-the-default-configuration-profile"></a>1.複製預設的組態設定檔

> [!NOTE]
> 組態設定檔是最上層的設定檔。 因此，若要編輯任何其他設定檔，您必須先複製組態設定檔。

在 [階層] 視窗中選取 **MixedRealityToolkit** 物件之後，於 [偵測器] 視窗中，將混合實境工具組的**組態設定檔**變更為 **DefaultHoloLens2ConfigurationProfile**：

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-1.png)

在仍選取 **MixedRealityToolkit** 物件的情況下，在 [偵測器] 視窗中按一下 [複製與自訂]  按鈕來開啟 [複製設定檔] 視窗：

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-2.png)

在 [複製設定檔] 視窗中，按一下 [複製]  按鈕來建立 **DefaultHololens2ConfigurationProfile** 的可編輯複本：

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-3.png)

新建立的組態設定檔現在已指派為您場景的組態設定檔：

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-4.png)

在 Unity 功能表中，選取 [檔案]   > [儲存]  ，即可儲存場景。

> [!TIP]
> 請記得在整個教學課程中儲存工作。

### <a name="2-enable-the-spatial-awareness-system"></a>2.啟用空間感知系統

在 [階層] 視窗中仍選取 **MixedRealityToolkit** 物件的情況下，於 [偵測器] 視窗中選取 [空間感知]  索引標籤，然後勾選 [啟用空間感知系統]  核取方塊：

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3.複製預設的空間感知系統設定檔

在 [空間感知]  索引標籤中，按一下 [複製]  按鈕以開啟 [複製設定檔] 視窗：

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-1.png)

在 [複製設定檔] 視窗中，按一下 [複製]  按鈕以建立 **DefaultMixedRealitySpatialAwarenessSystemProfile** 的可編輯複本：

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-2.png)

新建立的空間感知系統設定檔現在會自動指派給您的組態設定檔：

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4.複製預設的空間感知網格觀察器設定檔

在仍選取 [空間感知]  索引標籤的情況下，展開 [Windows Mixed Reality 空間網格觀察器]  區段，然後按一下 [複製]  按鈕來開啟 [複製設定檔] 視窗：

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-1.png)

在 [複製設定檔] 視窗中，按一下 [複製]  按鈕來建立 **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** 的可編輯複本：

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-2.png)

新建立的空間感知網格觀察器設定檔現在會自動指派給您的空間感知系統設定檔：

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5.變更空間感知網格的顯示

在 [空間網格觀察器設定]  中，將 [顯示選項]  變更為 [遮蔽]  ，以隱藏仍在運作的空間對應網格：

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> 雖然空間對應網格看不到，但仍存在且正常運作。 例如，空間對應網格後方的任何全像投影 (實體牆後方的全像投影等) 將不會顯示。

您方才已了解如何修改 MRTK 設定檔中的設定。 如您所見，為了自訂 MRTK 設定，您必須先建立預設設定檔的複本。 由於預設設定檔無法編輯，因此當您想要還原為預設設定時，一律可以參考這些設定。 若要深入了解 MRTK 設定檔及其架構，您可以瀏覽 [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[混合實境工具組設定檔設定指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)。

## <a name="hand-tracking-gestures-and-interactable-buttons"></a>手部追蹤手勢和可互動的按鈕

在本節中，您將了解如何使用手動追蹤來按下按鈕並觸發事件，讓您可以在按下按鈕時引發動作。

此特定範例將示範如何在按下按鈕時變更立方體的顏色，並在放開按鈕時變回原本顏色。 不過，您可以遵循這些相同原則來建立其他事件。

變更立方體顏色所需的主要步驟如下：

1. 將可點按的按鈕 Prefab 新增至場景
2. 在場景中新增立方體
3. 設定 InteractableOnPressReceiver 事件種類
4. 設定立方體來接收「按下」事件
5. 定義「按下」事件要觸發的動作
6. 設定立方體以接收「放開」事件
7. 定義「放開」事件要觸發的動作
8. 使用編輯器內模擬來測試按鈕

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a>1.將可點按的按鈕 Prefab 新增至場景

> [!TIP]
> <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">Prefab</a> 是預先設定且儲存為 Unity 資產的 GameObject，可以在整個專案中重複使用。

在**專案視窗**中搜尋 **PressableButtonHoloLens2**，以找出您將在此範例中使用的 Prefab：

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-1.png)

在**搜尋**結果中選取 **PressableButtonHoloLens2** Prefab，然後將其**拖曳**到 [階層]  視窗中來新增到場景中：

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> 若要顯示下圖所示的場景，請按兩下 [階層] 視窗中的 PressableButtonHoloLens2 物件，使其成為焦點，然後使用位於場景視窗右上角的<a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">場景 Gizmo</a>，將檢視角度調整為以 Z 軸為前方。

在仍選取 **PressableButtonHoloLens2** 物件的情況下，在 [偵測器]  視窗中：

* 變更其變形**位置**，使其位於位於相機前方 (也就是其原本位置)，例如，x = 0、y = 0 和 z = 0.5

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> 一般情況下，Unity 中的 1 個位置單位會大致等於真實世界的 1 公尺。 但有例外狀況，例如，當物件是所縮放物件的子系時。

### <a name="2-add-a-cube-to-the-scene"></a>2.在場景中新增立方體

以滑鼠右鍵按一下 [階層] 視窗內的空白位置，然後選取 [3D 物件]   > [立方體]  ，將立方體新增至您的場景：

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-1.png)

在仍選取**立方體**物件的情況下，在 [偵測器]  視窗中：

* 變更其變形**位置**，使其位於可點按的按鈕附近，但不與之重疊，例如 x = 0、y = 0.04 和 z = 0.5
* 將其變形**縮放**變更為適當大小，例如 x = 0.02、y = 0.02 和 z = 0.02

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a>3.設定 InteractableOnPressReceiver 事件種類

在 [階層] 視窗中選取 **PressableButtonHoloLens2** 物件，然後在 [偵測器]  視窗的**三條線功能表**中選取 [摺疊所有元件]  ，以取得此物件上所有元件的概觀：

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-1.png)

展開 [Interactable (指令碼)]  元件，然後找出並展開 [事件]   > [接收者]  區段：

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-2.png)

按一下 [新增事件]  按鈕，以建立事件接收器類型為 **InteractableOnPressReceiver** 的新事件接收器：

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> 名為 InteractableOnPressReceiver 的事件接收器類別可讓按鈕在追蹤的手部按下按鈕時，回應按下的事件。

針對新建立的事件接收器，將**互動篩選**變更為**近處或遠處**：

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-4.png)

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a>4.設定立方體來接收「按下」事件

在 [階層] 視窗中，**按一下並拖曳**立方體  至 **On Press ()** 事件的 [事件屬性]  物件欄位中，將立方體指派為 On Press () 事件的接收者：

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a>5.定義「按下」事件要觸發的動作

按一下動作下拉式清單 (目前指派內容為**無函式**)，然後選取 [MeshRenderer]   > [材質內容]  ，將立方體的材質屬性設定為在觸發 On Press () 事件時變更：

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-1.png)

按一下材質欄位旁的**圓型**小圖示 (目前已填入 [無 (材質)])  ，以開啟選取材質視窗：

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-2.png)

在 [選取材質] 視窗中，**搜尋** **MRTK_Standard** 並選取適當的材質，例如 **MRTK_Standard_Cyan**，如此一來，當您按下按鈕時，立方體的顏色會變更為青綠色：

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a>6.設定立方體以接收「放開」事件

針對「放開」事件**重複**步驟 4，即可將**立方體**指派為 **On Release ()** 事件的接收者。

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a>7.定義「放開」事件要觸發的動作

針對「放開」事件**重複**步驟 5，但選擇 [MRTK_Standard_LightGray]  材質，讓立方體的顏色在放開按鈕時回到其原本的淺灰色：

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a>8.使用編輯器內模擬來測試按鈕

按下 [開始遊戲]  按鈕進入遊戲模式，並使用編輯器內的輸入模擬來測試新設定的按鈕。

未按下按鈕 (空格鍵 + 向後轉動滑鼠滾輪)：

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-1.png)

已按下按鈕 (空格鍵 + 向前轉動滑鼠滾輪)：

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> 若要了解如何使用編輯器內的輸入模擬，您可以參考 [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[使用編輯器內的手動輸入模擬來測試場景](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)。

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>使用 MRTK 的方格物件集合來建立按鈕面板

在本節中，您會了解如何使用 MRTK 的方格物件集合工具，讓多個按鈕自動排列成整齊的使用者介面。

此特定範例將示範如何建立有五個按鈕水平對齊的面板。 不過，您也可以遵循這些相同原則來建立其他版面配置。

達成此動作所需採取的主要步驟如下：

1. 使按鈕物件歸屬於父物件
2. 新增和設定 Grid Object Collection (指令碼) 元件
3. 使用編輯器內的模擬來測試按鈕

### <a name="1-parent-the-button-objects-to-a-parent-object"></a>1.使按鈕物件歸屬於父物件

以滑鼠右鍵按一下 [階層] 視窗內的空白位置，然後選取 [建立空白物件]  ：

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-1.png)

以滑鼠右鍵按一下新建立的物件，選取 [重新命名]  並為其指定適當的名稱，例如 **ButtonCollection**：

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-2.png)

選取 **PressableButtonHoloLens2** 物件，然後將其**拖曳**到 **ButtonCollection** 物件的上方，使其成為 ButtonCollection 物件的子系：

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-3.png)

以滑鼠右鍵按一下 **PressableButtonHoloLens2** 物件，然後選取 [複製]  來建立其複本：

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-4.png)

再**重複**此步驟四次，直到總共有五個 PressableButtonHoloLens2 物件為止。

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2.新增和設定 Grid Object Collection (指令碼) 元件

在 [階層] 視窗中選取 ButtonCollection 物件之後，在 [偵測器] 視窗中按一下 [新增元件]  按鈕，然後搜尋並選取 [Grid Object Collection]  以將 Grid Object Collection (指令碼) 元件新增至 ButtonCollection 物件：

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-1.png)

設定 Grid Object Collection (指令碼)，如下所示：

* 將 [資料列數目]  變更為 1，使所有按鈕對齊一個單一資料列
* 將 [儲存格寬度]  變更為 0.05，以拉開資料列內的按鈕距離

然後按一下 [更新集合]  按鈕以套用新的設定：

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> 您剛才套用的設定變更代表為了將按鈕放在單一資料列中所需的最小變更。 不過，在未來的專案中，根據一些因素 (例如，父物件和子物件的方向)，您可能需要調整其他設定 (例如，方向類型)。 若要深入了解 MRTK 的 Grid Object Collection，您可以瀏覽 [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[物件集合指令碼](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts)指南。

在 [階層] 視窗中仍然選取 ButtonCollection 物件時，在 [偵測器] 視窗中變更 ButtonCollection 物件的變形**位置**，使其子按鈕物件位在相機前方 (也就是原本的位置)，例如 x = 0、y = 0 和 z = 0.5：

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> 當您第一次將 PressableButtonHoloLens2 Prefab 新增至上述[手部追蹤手勢和可互動的按鈕](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)區段中的場景時，您會將其放在相機前方。 不過，由於方格物件集合會控制其直屬子物件的位置，因此 PressableButtonHoloLens2 子物件的 Z 位置會因為方格物件集合的「與父系的距離」值預設為 0，而重設為0。 這就是為什麼我們會將父 ButtonCollection 物件的位置向前移動，而不是設定「與父系的距離」值來向前移動 PressableButtonHoloLens2 子物件，同時也是為了保持父/子位置關聯性的結構。

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a>3.使用編輯器內的模擬來測試按鈕

按下 [開始遊戲] 按鈕進入遊戲模式，並使用編輯器內的輸入模擬來測試新建立按鈕面板中的每個按鈕：

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> 目前，當您按下五個按鈕的其中一個時，立方體顏色會變更為青綠色。 若要讓體驗更加有趣，請使用您剛學到的內容來設定每個按鈕，將立方體變更為不同的顏色。

## <a name="adding-text-into-your-scene"></a>在場景中新增文字

在本節中，您將了解如何使用 Unity 的 TextMesh Pro (您已在上一個教學課程的[匯入 TextMesh Pro 基本資源](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)一節中有所準備)，將文字新增至您的混合實境體驗。

在此特定範例中，您會在上一節建立的按鈕集合底下新增一個簡單標籤。

以滑鼠右鍵按一下 ButtonCollection 物件，然後選取 [3D 物件]   > [文字 - TextMeshPro]  ，將 TextMeshPro 物件建立為 ButtonCollection 物件的子系：

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-1.png)

在新建立的 TextMeshPro 物件(名為 Text (TMP)) 仍為選取狀態時，在 [偵測器] 視窗中變更其位置和大小，讓標籤整齊地放在按鈕集合底下，例如：

* 將矩形變形**Y 位置**變更為 -0.0425
* 將矩形變形**寬度**變更為 0.24
* 將矩形變形**高度**變更為 0.024

然後更新文字以反映標籤的用途，並選擇字型屬性，讓文字適合放入標籤，例如：

* 將 Text Mesh Pro (指令碼) 的**文字**變更為按鈕集合
* 將 Text Mesh Pro (指令碼) 的**字型樣式**變更為粗體
* 將 Text Mesh Pro (指令碼) 的**字型大小**變更為 0.2
* 將 Text Mesh Pro (指令碼) 的**對齊**變更為置中和中間

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已了解如何複製、自訂和設定 MRTK 設定檔的設定。 您也已經了解如何在 HoloLens 2 上使用追蹤的手部來與按鈕互動以觸發事件。 最後，您已了解如何使用 MRTK 的方格物件集合元件和 Unity 的 Text Mesh Pro 來建立簡單的 UI 介面。

[下一個教學課程：4.放置動態內容並使用解算器](mrlearning-base-ch3.md)
