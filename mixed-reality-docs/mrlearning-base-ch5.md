---
title: 快速入門教學課程-6。 探索先進的輸入選項
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: aaa02ce118fd051d94311e837b143affc96ff72b
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77554254"
---
# <a name="6-exploring-advanced-input-options"></a>6. 探索 advanced 輸入選項

在本教學課程中，您將探索 HoloLens 2 的幾個先進輸入選項，包括使用語音命令、移動流覽手勢和眼睛追蹤。

## <a name="objectives"></a>目標

* 使用語音命令和關鍵字觸發事件
* 使用追蹤的手平移材質和3D 物件
* 利用 HoloLens 2 眼追蹤功能來選取物件

## <a name="enabling-voice-commands"></a>啟用語音命令
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

在本節中，您將會執行語音命令，讓使用者在顆 octa 物件上播放音效。 為此，您將建立新的語音命令，然後設定事件，讓它在說話語音命令關鍵字時觸發所需的動作。

達成此目標所需採取的主要步驟如下：

1. 複製預設輸入系統設定檔
2. 複製預設的語音命令設定檔
3. 建立新的語音命令
4. 新增和設定語音輸入處理常式（腳本）元件
5. 執行語音命令的回應事件

### <a name="1-clone-the-default-input-system-profile"></a>1. 複製預設輸入系統設定檔

在 [階層] 視窗中，選取 [ **MixedRealityToolkit** ] 物件，然後在 [偵測器] 視窗中選取 [**輸入**] 索引標籤，然後複製**DefaultHoloLens2InputSystemProfile** ，將它取代為您自己可自訂的**輸入系統設定檔**：

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> 如需有關如何複製 MRTK 設定檔的提醒，您可以參閱[如何設定混合現實工具組設定檔](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)的指示。

### <a name="2-clone-the-default-speech-commands-profile"></a>2. 複製預設的語音命令設定檔

展開 [**語音**] 區段並複製**DefaultMixedRealitySpeechCommandsProfile** ，將它取代為您自己的可自訂**語音命令設定檔**：

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a>3. 建立新的語音命令

在 [**語音命令**] 區段中，按一下 [ **+ 新增語音命令**] 按鈕，將新的語音命令新增至現有語音命令清單的底部，然後在 [**關鍵字**] 欄位中輸入適當的單字或片語，例如 [**播放音樂**]：

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> 如果您的電腦沒有麥克風，而您想要使用編輯器內模擬來測試語音命令，您可以將 KeyCode 指派給語音命令，讓您在按下對應的按鍵時觸發它。

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a>4. 新增和設定語音輸入處理常式（腳本）元件

在 [階層] 視窗中，選取 [**顆 octa** ] 物件，並將 [**語音輸入處理常式（腳本）** ] 元件新增至顆 octa 物件。 然後取消核取 [**需要焦點**] 核取方塊，讓使用者不需要查看顆 octa 物件來觸發語音命令：

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a>5. 執行語音命令的回應事件

在 [語音輸入處理常式（腳本）] 元件上，按一下 [小型 **+** ] 按鈕，將關鍵字元素新增至關鍵字清單：

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

按一下新建立的專案**0**將它展開，然後從 [**關鍵字**] 下拉式清單中，選擇您稍早建立的 [**播放音樂**] 關鍵字：

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!NOTE]
> [關鍵字] 下拉式清單中的關鍵字會根據語音命令設定檔中的 [語音命令] 清單中定義的關鍵字來填入。

建立新的**回應（）** 事件、設定**顆 octa**物件以接收事件、將**spatialize**定義為要觸發的動作，並將適當的音訊剪輯指派給**音訊剪輯**欄位（例如，MRTK_Gem 音訊剪輯）：

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-3.png)

> [!TIP]
> 如需有關如何執行事件和指派音訊剪輯的提醒，您可以參閱[執行觸控式已啟動事件](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event)指示。

## <a name="the-pan-gesture"></a>平移手勢

當您使用手指或手來滾動內容時，移動流覽手勢非常有用。 在此範例中，您會先瞭解如何滾動 2D UI，然後再展開它，以便能夠在3D 物件的集合上進行滾動。

達成此目標所需採取的主要步驟如下：

1. 建立可用於移動的四個物件
2. 新增近乎互動 Touchable （腳本）元件
3. 新增手互動平移縮放（腳本）元件
4. 新增要滾動的2D 內容
5. 新增要滾動的3D 內容
6. 新增 Move With Pan （Script）元件

> [!NOTE]
> Move With Pan （Script）元件不是 MRTK 的一部分。 本教學課程的資產提供此說明。

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a>1. 建立可用於移動的四個物件

在 [階層] 視窗中，以滑鼠右鍵按一下空白區域，然後選取 [ **3D 物件** > **四**個]，將四個新增至您的場景。 為它提供適當的名稱（例如， **PanGesture**），並將它放在適當的位置，例如 X = 0、Y =-0.2、Z = 2。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> 如需有關如何將 Unity 基本專案（例如3D 四）新增至場景的提醒，您可以參考將[Cube 新增至場景](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene)指示。

如同任何其他互動，平移手勢也需要碰撞。 根據預設，四個具有網格碰撞器。 不過，網格碰撞的情況並不理想，因為它非常精簡。 為了讓使用者更容易與碰撞程式互動，我們將以方塊碰撞程式來取代網格碰撞。

在仍選取 PanGesture 物件的情況下，按一下**網格碰撞**器元件的 [**設定**] 圖示，然後選取 [**移除元件**] 以移除網格碰撞器：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

在 [偵測器] 視窗中，使用 [**加入元件**] 按鈕加入方塊**碰撞**器，然後將方塊碰撞器**大小**Z 變更為0.15，以增加方塊碰撞器的粗細：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a>2. 新增近乎互動 Touchable （腳本）元件

在仍選取**PanGesture**物件的情況下，將**近乎互動 Touchable （腳本）** 元件新增至 PanGesture 物件，然後按一下 [**修正界限**] 和 [**修正中心**] 按鈕，將近端互動 Touchable （腳本）的本機中心和界限屬性更新為符合 BoxCollider：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a>3. 新增手互動平移縮放（腳本）元件

在仍選取**PanGesture**物件的情況下，將 [**手互動] [平移縮放（腳本）** ] 元件新增至 PanGesture 物件，然後勾選 [**鎖定水準**] 核取方塊，只允許垂直捲動：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a>4. 新增要滾動的2D 內容

在 [專案] 面板中，搜尋**PanContent**材質，然後按一下並將它拖曳至**PanGesture**物件的網格轉譯器**材質**元素0屬性：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

在 [偵測器] 視窗中，展開新增的 [ **PanContent**材質] 元件，然後將它從 **[Y]** 值切換為 [0.5]，使其符合 X 值，而磚出現正方形：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

如果您現在進入遊戲模式，您可以使用編輯器內模擬中的移動流覽手勢來測試2D 內容的滾動圖：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a>5. 新增要滾動的3D 內容

在 [階層] 視窗中，**建立四個 cube**做為**PanGesture**物件的子物件，並將其轉換**比例**設定為 X = 0.15、Y = 0.15、Z = 0.15：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

若要平均地將 cube 隔開，並節省一些時間，請將**Grid 物件集合（腳本）** 元件加入 cube 的父物件（也就是**PanGesture**物件），並設定 Grid 物件集合（腳本），如下所示：

* 將 [Num] 資料**列**變更為 [1]，讓所有 cube 對齊一個單一資料列
* 將資料**格寬度**變更為0.25，以將資料列中的 cube 空間縮小

然後按一下 [**更新集合**] 按鈕以套用新的設定：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a>6. 新增 Move With Pan （Script）元件

在 [階層] 視窗中，選取所有**Cube 子物件**，然後在 [偵測器] 視窗中，使用 [**加入元件**] 按鈕，將 [**使用移動流覽（腳本）** ] 元件新增至所有 cube：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> 如需有關如何在 [階層] 視窗中選取多個物件的提醒，tou 可以參考[將操作處理常式（腳本）元件加入至所有物件](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects)指示。

在仍選取所有 cube 的情況下，按一下-並將**PanGesture**物件拖曳至 [**平移輸入來源**] 欄位：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> 每個 cube 上的 Move With Pan （Script）元件會接聽 PanGesture 物件（您在上述步驟中指派為平移輸入來源）的 HandInteractionPanZoom （腳本）元件所傳送的 Pan 更新事件，並更新每個 cube 的位置。會.

在 [階層] 視窗中，選取 [ **PanGesture** ] 物件，然後在 [偵測器 **] 中** **取消勾選**[網格轉譯器] 核取方塊，以停用網格轉譯器元件：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

如果您現在進入遊戲模式，您可以使用編輯器內模擬中的移動流覽手勢來測試3D 內容的滾動功能：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a>眼球追蹤

在本節中，您將探索如何在專案中啟用眼睛追蹤。 在此範例中，您將會執行一些功能，讓3DObjectCollection 中的每個物件在查看使用者眼睛時慢慢旋轉，以及在查看的物件是由 [按下] 或 [語音] 命令選取時觸發中斷效果。

達成此目標所需採取的主要步驟如下：

1. 將眼睛追蹤目標（腳本）元件新增至所有目標物件
2. 將眼睛追蹤教學課程示範（腳本）元件新增至所有目標物件
3. 在查看目標事件時執行
4. 在選取的事件上執行
5. 針對編輯器內的模擬啟用模擬的監看式追蹤
6. 在 Visual Studio 專案的應用程式功能中啟用注視輸入

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a>1. 將眼睛追蹤目標（腳本）元件新增至所有目標物件

在 [階層] 視窗中，展開 [ **3DObjectCollection** ] 物件並選取所有**子物件**，然後在 [偵測器] 視窗中，使用 [**加入元件**] 按鈕，將**眼睛追蹤目標（腳本）** 元件新增至所有子物件：

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

在仍選取所有**子物件**的情況下，設定**眼睛追蹤目標（腳本）** 元件，如下所示：

* 將 [**選取動作**] 變更為 [**選取**]，將此物件的 [按下] 動作定義為 [選取]
* 展開 [**語音選取**] 並將語音命令清單**大小**設定為1，然後在出現的 [新增專案] 清單中，將**元素 0**變更為 [**選取**]，以將此物件的語音命令動作定義為 [選取]

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a>2. 將眼睛追蹤教學課程示範（腳本）元件新增至所有目標物件

若仍然選取所有**子物件**，請使用 [**新增元件**] 按鈕，將**眼睛追蹤教學課程示範（腳本）** 元件新增至所有子物件：

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> 眼睛追蹤目標（腳本）元件不是 MRTK 的一部分。 本教學課程的資產提供此說明。

### <a name="3-implement-the-while-looking-at-target-event"></a>3. 在查看目標事件時執行

在 [階層] 視窗中，選取 [**乳酪**] 物件，然後在**查看 [目標（）** ] 事件時建立新的，將 [**乳酪**] 物件設定為接收事件，並將**EyeTrackingTutorialDemo**定義為要觸發的動作：

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

針對3DObjectCollection 中的每個子物件**重複**此動作。

> [!TIP]
> 如需如何執行事件的提醒，您可以參考[手追蹤手勢和可互動按鈕](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)的指示。

### <a name="4-implement-the-on-selected-event"></a>4. 在選取的事件上執行

在 [階層] 視窗中，選取 [**乳酪**] 物件，然後在 **[選取的（）** ] 事件上建立新的、設定 [**乳酪**] 物件以接收事件，並定義**EyeTrackingTutorialDemo BlipTarget**作為要觸發的動作：

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

針對3DObjectCollection 中的每個子物件**重複**此動作。

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a>5. 為編輯器內的模擬啟用模擬的監看式追蹤

在 [階層] 視窗中，選取 [ **MixedRealityToolkit** ] 物件，然後在 [偵測器] 視窗中，選取 [**輸入**] 索引標籤，然後依序展開 [**輸入資料提供者**] 區段和 [**輸入模擬服務**] 區段，然後再複製**DefaultMixedRealityInputSimulationProfile** ，將其取代為您自己可自訂的**輸入模擬配置**

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> 如需有關如何複製 MRTK 設定檔的提醒，您可以參閱[如何設定混合現實工具組設定檔](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)的指示。

在 [**眼睛模擬**] 區段中，核取 [**模擬眼睛位置**] 核取方塊以啟用眼睛追蹤模擬：

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

如果您現在進入遊戲模式，可以藉由調整視圖來測試您所執行的微調和中斷效果，讓游標到達其中一個物件，並使用 [手動互動] 或 [語音] 命令來選取物件：

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> 如果您未使用 DefaultHoloLens2ConfigurationProfile 來複製可自訂的 MRTK 設定檔，請依照[設定混合現實工具](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)組指示中的指示進行，您的專案中可能不會啟用眼睛追蹤，而且必須啟用。 為此，您可以參閱 MRTK 指示[中的開始使用](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html)監看追蹤。

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a>6. 在 Visual Studio 專案的應用程式功能中啟用注視輸入

從 Visual Studio 建立應用程式並將其部署到您的裝置之前，您必須先在專案的應用程式功能中啟用注視輸入。 為此，您可以依照[HoloLens 2 指示來測試 Unity 應用程式](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2)。

## <a name="congratulations"></a>恭喜

您已成功將基本眼追蹤功能新增至您的應用程式。 這些動作只是眼球追蹤功能無限可能性的開端。 在本教學課程中，您也會瞭解其他的「高級輸入」功能，例如語音命令和移動流覽手勢。

[下一課： 7. 建立農曆模組範例應用程式](mrlearning-base-ch6.md)
