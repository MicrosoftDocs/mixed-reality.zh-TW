---
title: 入門教學課程 - 6。 探索進階的輸入選項
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 9a19ad59e520a2743aafd954910f43c6f51d6c8a
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85441855"
---
# <a name="6-exploring-advanced-input-options"></a>6.探索進階的輸入選項

在本教學課程中，我們將探討 HoloLens 2 的幾個進階輸入選項，包括使用語音命令、平移手勢和眼球追蹤。

## <a name="objectives"></a>目標

* 使用語音命令和關鍵字觸發事件
* 使用手部追蹤來平移紋理和 3D 物件
* 利用 HoloLens 2 的眼球追蹤功能來選取物件

## <a name="enabling-voice-commands"></a>啟用語音命令
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

您將在本節中實作語音命令，讓使用者可以在 Octa 物件上播放音效。 為此，您將建立新的語音命令，然後設定事件，讓您在說出語音命令關鍵字時，即可觸發所需的動作。

達成此動作所需採取的主要步驟如下：

1. 複製預設的輸入系統設定檔
2. 複製預設的語音命令設定檔
3. 建立新的語音命令
4. 新增和設定 Speech Input Handler (指令碼) 元件
5. 實作語音命令的回應事件

### <a name="1-clone-the-default-input-system-profile"></a>1.複製預設的輸入系統設定檔
在 [階層] 視窗中，選取 **MixedRealityToolkit** 物件，然後在 [偵測器] 視窗中選取 [輸入] 索引標籤，複製 **DefaultHoloLens2InputSystemProfile** 來將其取代為您自己可自訂的**輸入系統設定檔**：

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!NOTE]
> 如果您使用 MRTK 2.4.0 或更新版本：
> * 從 [階層] 索引標籤中選取 **MixedRealityToolkit** 物件，然後按一下 [偵測器] 視窗中的 [輸入] 索引標籤，並展開 [指標] 區段。 
> * 複製 **DefaultMixedRealityInputPointerProfile**，並將其取代為您自己的可自訂**輸入指標設定檔**。
> * 在 [注視設定] 區段中檢查 [啟用眼睛追蹤] 是否為 true。 

> [!TIP]
> 如需有關如何複製 MRTK 設定檔的提示，您可以參閱[如何設定混合實境工具組設定檔](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)的指示。

### <a name="2-clone-the-default-speech-commands-profile"></a>2.複製預設的語音命令設定檔

展開 [語音] 區段，然後複製 **DefaultMixedRealitySpeechCommandsProfile** 來將其取代為您自己可自訂的**語音命令設定檔**：

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a>3.建立新的語音命令

在 [語音命令] 區段中按一下 [+ 新增語音命令] 按鈕，將新的語音命令新增至現有語音命令清單的底部，然後在 [關鍵字] 欄位中輸入適當的單字或片語，例如 **Play Music** (播放音樂)：

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> 如果您的電腦沒有麥克風，而您想要使用編輯器內的模擬來測試語音命令，您可以將 KeyCode 指派給語音命令，此方式可讓您在按下對應的按鍵時觸發語音命令。

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a>4.新增和設定 Speech Input Handler (指令碼) 元件

在 [階層] 視窗中，選取 **Octa** 物件，並將 **Speech Input Handler (指令碼)** 元件新增至 Octa 物件。 然後取消核取 [需要對焦] 核取方塊，如此使用者就不需要看著 Octa 物件來觸發語音命令：

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a>5.實作語音命令的回應事件

在 Speech Input Handler (指令碼) 元件上，按一下小的 **[+]** 按鈕，將關鍵字元素新增至關鍵字清單：

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

按一下新建立的**元素 0** 來將其展開，然後從 [關鍵字] 下拉式清單中，選擇您稍早建立的 [Play Music] 關鍵字：

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!NOTE]
> 在關鍵字下拉式清單中填入的關鍵字，是以語音命令設定檔中「語音命令」清單上定義的關鍵字為基礎。

建立新的 **Response ()** 事件、設定 **Octa** 物件以接收事件、將 **AudioSource.PlayOneShot** 定義為要觸發的動作，並將適當的音訊片段指派給 [音訊片段] 欄位，例如 MRTK_Gem 音訊片段：

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-3.png)

> [!TIP]
> 如需有關如何實作事件和指派音訊片段的提示，您可以參閱[實作 On Touch Started 事件](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event)的指示。

## <a name="the-pan-gesture"></a>平移手勢

平移手勢可用於捲動項目 (使用您的手指或手捲動內容)。 在此範例中，您會先了解如何捲動 2D UI，然後再擴展為能夠在3D 物件的集合上捲動項目。

達成此動作所需採取的主要步驟如下：

1. 建立可用於平移的 Quad (四邊形) 物件
2. 新增 Near Interaction Touchable (指令碼) 元件
3. 新增 Hand Interaction Pan Zoom (指令碼) 元件
4. 新增要捲動的 2D 內容
5. 新增要捲動的 3D 內容
6. 新增 Move With Pan (指令碼) 元件

> [!NOTE]
> Move With Pan (指令碼) 元件不是 MRTK 的一部分。 這是本教學課程資產隨附的元件。

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a>1.建立可用於平移的 Quad (四邊形) 物件

在 [階層] 視窗中，以滑鼠右鍵按一下空白區域，然後選取 [3D 物件] > [Quad]，將一個四邊形新增至您的場景。 為其指定一個適當的名稱 (例如 **PanGesture**)，然後放在適當的位置，例如 X = 0、Y = -0.2、Z = 2。

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> 如需有關如何將 Unity 基本項目 (例如 3D 四邊形) 新增至場景的提示，您可以參閱[將立方體新增至場景](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene)的指示。

如同任何其他互動，平移手勢也需要碰撞器。 根據預設，Quad 具有網格碰撞器 (Mesh Collider)。 然而，網格碰撞器並不理想，因為其非常薄。 為了讓使用者更容易與碰撞器互動，我們將以方塊碰撞器來取代網格碰撞器。

在仍選取 PanGesture 物件的情況下，按一下 **網格碰撞器** 元件的 [設定] 圖示，然後選取 [移除元件] 來移除網格碰撞器：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

在 [偵測器] 視窗中，使用 [新增元件] 按鈕來新增**方塊碰撞器**，然後將方塊碰撞器**大小** 的 Z 變更為 0.15，以增加方塊碰撞器的厚度：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a>2.新增 Near Interaction Touchable (指令碼) 元件

在仍選取 **PanGesture** 物件的情況下，將 **Near Interaction Touchable (指令碼)** 元件新增至 PanGesture 物件，然後按一下 [修正周框] 和 [修正中心] 按鈕，以更新 Near Interaction Touchable (指令碼) 的區域中心和界限屬性來符合 BoxCollider：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a>3.新增 Hand Interaction Pan Zoom (指令碼) 元件

在仍選取 PanGesture 物件的情況下，將 **Hand Interaction Pan Zoom (指令碼)** 元件新增至 PanGesture 物件，然後勾選 [鎖定水平方向] 核取方塊來僅限垂直捲動：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a>4.新增要捲動的 2D 內容

在 [專案] 面板中，搜尋 **PanContent** 材質，然後按一下該材質並將其拖曳至 **PanGesture** 物件的網格轉譯器**材質**的元素 0 屬性：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

在 [偵測器] 視窗中，展開新增的 **PanContent** 材質元件，然後將**拼接**的 Y 值變更為 0.5 以符合 X 值，而磚現在會呈現正方形：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

如果您現在進入遊戲模式，您可以在編輯器內的模擬中使用平移手勢來嘗試捲動 2D 內容：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a>5.新增要捲動的 3D 內容

在 [階層] 視窗中，**建立四個立方體**來作為 **PanGesture** 的子物件，並將其變形**縮放**調整為 X = 0.15，Y = 0.15，Z = 0.15：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

若要將立方體平均隔開，並節省一些時間，請將 **Grid Object Collection (指令碼)** 元件新增至立方體的父物件 (也就是 **PanGesture** 物件)，然後設定 Grid Object Collection (指令碼)，如下所示：

* 將 [資料列數目] 變更為 1，使所有立方體對齊一個單一資料列
* 將 [儲存格寬度] 變更為 0.25，以拉開資料列內的立方體距離

然後按一下 [更新集合] 按鈕以套用新的設定：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a>6.新增 Move With Pan (指令碼) 元件

在 [階層] 視窗中，選取所有**立方體子物件**，然後在 [偵測器] 視窗中，使用 [新增元件] 按鈕，將 **Move With Pan (指令碼)** 元件新增至所有立方體：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> 如需有關如何在 [階層] 視窗中選取多個物件的提示，您可以參閱[將 Manipulation Handler (指令碼) 元件新增至所有物件](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects)的指示。

在仍選取所有立方體的情況下，按一下 **PanGesture** 物件並將其拖曳至 [平移輸入來源] 欄位：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> 每個立方體上的 Move With Pan (指令碼) 元件都會接聽 PanGesture 物件 (已在上個步驟指派為 Pan Input Source) 上 HandInteractionPanZoom (指令碼) 元件所傳送的 Pan Updated 事件，並據以更新每個立方體的位置。

在 [階層] 視窗中，選取 **PanGesture** 物件，然後在偵測器中**取消核取** [網格轉譯器] 核取方塊，以停用網格轉譯器元件：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

如果您現在進入遊戲模式，您可以在編輯器內的模擬中使用平移手勢來嘗試捲動 3D 內容：

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a>眼球追蹤

在本節中，您將探索如何在專案中啟用眼球追蹤。 在此範例中，您將會實作一些功能，讓 3DObjectCollection 中的每個物件能在使用者眼睛的注視下慢慢旋轉，以及當注視的物件透過空中點選或語音命令選取時觸發光點效果。

達成此動作所需採取的主要步驟如下：

1. 將 Eye Tracking Target (指令碼) 元件新增至目標物件
2. 將 Eye Tracking Tutorial Demo (指令碼) 元件新增至所有目標物件
3. 實作「注視目標時」(While Looking At Target) 事件
4. 實作「選取時」(On Selected) 事件
5. 針對編輯器內的模擬啟用模擬的眼球追蹤
6. 在 Visual Studio 專案的應用程式功能中啟用注視輸入

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a>1.將 Eye Tracking Target (指令碼) 元件新增至目標物件

在 [階層] 視窗中，展開 **3DObjectCollection** 物件，並選取所有**子物件**，然後在 [偵測器] 視窗中，使用 [新增元件] 按鈕，將 **Eye Tracking Target (指令碼)** 元件新增至所有子物件：

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

在仍然選取所有**子物件**的情況下，設定 **Eye Tracking Target (指令碼)** 元件，如下所示：

* 將 [選取動作] 變更為 [選取]，即可將此物件的空中點選動作定義為「選取」
* 展開 [語音選取]，並將語音命令清單的**大小**設為 1，然後在出現的新元素清單中，將 **元素 0** 變更為 [選取]，以將此物件的語音命令動作定義為「選取」

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a>2.將 Eye Tracking Tutorial Demo (指令碼) 元件新增至所有目標物件

在仍選取所有**子物件**的情況下，使用 [新增元件] 按鈕，將 **Eye Tracking Tutorial Demo (指令碼)** 元件新增至所有子物件：

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> The Eye Tracking Target (指令碼) 元件不是 MRTK 的一部分。 這是本教學課程資產隨附的元件。

### <a name="3-implement-the-while-looking-at-target-event"></a>3.實作「注視目標時」(While Looking At Target) 事件

在 [階層] 視窗中，選取 **Cheese** 物件，然後建立新的 **While Looking At Target ()** 事件，並設定 **Cheese** 物件來接收事件，以及將 **EyeTrackingTutorialDemo.RotateTarget** 定義為要觸發的動作：

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

針對 3DObjectCollection 中的每個子物件**重複**這些動作。

> [!TIP]
> 如需有關如何實作事件的提示，您可以參閱[手部追蹤手勢和可互動按鈕](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)的指示。

### <a name="4-implement-the-on-selected-event"></a>4.實作「選取時」(On Selected) 事件

在 [階層] 視窗中，選取 **Cheese** 物件，然後建立新的 **On Selected ()** 事件，並設定 **Cheese** 物件來接收事件，以及將 **EyeTrackingTutorialDemo.BlipTarget** 定義為要觸發的動作：

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

針對 3DObjectCollection 中的每個子物件**重複**這些動作。

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a>5.針對編輯器內的模擬啟用模擬的眼球追蹤

在 [階層] 視窗中，選取 **MixedRealityToolkit** 物件，然後在 [偵測器] 視窗中，選取 [輸入] 索引標籤並依序展開 [輸入資料提供者] 區段和 [輸入模擬服務] 區段，然後複製 **DefaultMixedRealityInputSimulationProfile** 來將其取代為您自己可自訂的**輸入模擬設定檔**：

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> 如需有關如何複製 MRTK 設定檔的提示，您可以參閱[如何設定混合實境工具組設定檔](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)的指示。

在 [眼球模擬] 區段中，核取 [模擬眼球位置] 核取方塊，以啟用眼球追蹤模擬：

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

如果您現在進入遊戲模式，可以藉由調整視圖來測試您所實作的旋轉和光點效果，讓游標點擊其中一個物件，並使用手部互動或語音命令來選取物件：

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> 如果您未使用 DefaultHoloLens2ConfigurationProfile 來複製可自訂的 MRTK 組態設定檔 (如[設定混合實境工具組](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)中所述的指示)，您的專案中可能不會啟用眼球追蹤，而這必須啟用。 為此，您可以參閱[開始在 MRTK 中使用眼球追蹤](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html)的指示。

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a>6.在 Visual Studio 專案的應用程式功能中啟用注視輸入

從 Visual Studio 中建立應用程式並將其部署到您的裝置之前，您必須先在專案的應用程式功能中啟用注視輸入。 為此，您可以遵循[在 HoloLens 2 上測試 Unity 應用程式](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2)的指示來進行。

## <a name="congratulations"></a>恭喜！

您已成功為應用程式新增了基本的眼球追蹤功能。 這些動作只是眼球追蹤功能無限可能性的開端。 在本教學課程中，您也了解了其他進階級輸入功能，例如語音命令和平移手勢。

[下一課：7.建立月球模組應用程式範例](mrlearning-base-ch6.md)
