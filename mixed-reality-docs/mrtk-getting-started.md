---
title: MRTK 第2版入門
description: 適用于想要利用 MRTK 的新開發人員
author: Yoyoz
ms.author: Yoyoz
ms.date: 05/15/19
ms.topic: article
keywords: Windows Mixed Reality、測試、混合現實工具組、MRTK 第2版、MRTK、工具、SDK、HoloLens、HoloLens 2
ms.openlocfilehash: 249a0ce0e608410983934b75e399d013e1ff1879
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750360"
---
# <a name="getting-started-with-mrtk-v2"></a>開始使用 MRTK v2

## <a name="mrtk-getting-started-guide"></a>MRTK 消費者入門指南
如需開始使用 MRTK V2 的資訊, 請參閱[MRTK 快速入門手冊](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)。

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>什麼是混合現實工具組 (MRTK)？
MRTK 是一項令人驚奇的開放原始碼工具組, 自 HoloLens 首次發行之後就已經存在, 而不是我們的開發人員社區的困難工作。 過去3年來, 我們聽取了開發人員社區的意見反應, 並已建立 MRTK v2 來考慮最大的顧慮。  

MRTK v2 與 Unity 是適用于混合現實應用程式的開放原始碼跨平臺開發工具組。  MRTK 第2版的目的是要加速開發以 Microsoft HoloLens、Windows Mixed Reality 沉浸 (VR) 耳機和 OpenVR 平臺為目標的應用程式。 此專案的目標是減少建立混合實境應用程式的進入障礙，以及回饋伴著我們成長的社群。 


若要深入瞭解, 請參閱[MRTK 檔入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)。

## <a name="feature-areas"></a>功能區

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="輸入系統" width="105"> 輸入系統 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="手動追蹤 (HoloLens 2)" width="105"> 手動追蹤 (HoloLens 2)
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="眼睛追蹤 (HoloLens 2)" width="105">
    眼睛追蹤 (HoloLens 2)
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="語音命令" width="105"> 語音命令
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="注視 + 選取 (HoloLens (第1代))" width="105">
    注視 + 選取 (HoloLens (第1代))
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="Teleportation" width="105"> Teleportation
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="UI 控制項" width="105"> UI 控制項
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="規劃求解和互動" width="105"> 規劃求解和互動
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="控制器視覺效果" width="105"> 控制器視覺效果
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="空間理解" width="105"> 空間理解
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="診斷工具" width="105"> 診斷工具
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="MRTK 標準著色器" width="105"> MRTK 標準著色器
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a>UI 和互動建立區塊

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="按鈕" width="250"><br>
    **Button**<br>
    一種按鈕控制項, 支援各種輸入法, 包括 HoloLens 2 的清楚表達手勢<a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="周框方塊" width="250"><br>
    **周框方塊**<br>
    在3D 空間中操作物件的標準 UI<a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="操作處理常式" width="250"><br>
    **操作處理常式**<br>
    用一或兩個手操作物件的腳本<a/>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="石板" width="250"><br>
    **石板** <br>
    2D 樣式平面, 支援以明確的手寫輸入進行滾動<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="系統鍵盤" width="250"><br>
    **系統鍵盤**<br>
    在 Unity 中使用系統鍵盤的範例腳本<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="可互動" width="250"><br>
     **可互動** <br>
     讓物件以視覺狀態和主題支援可互動的腳本<a/>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="規劃" width="250"><br>
    **規劃** <br>
    各種物件定位行為, 例如標記、主體鎖定、常數視圖大小和表面磁性<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="物件集合" width="250"><br>
    **物件集合**<br>
    以三維圖形設定物件陣列的腳本<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="工具提示" width="250">  <br>
    **並用**<br>
    具有彈性錨點/pivot 系統的注釋 UI, 可用於標記動作控制器和物件<a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="應用程式行" width="250"><br>
    **應用程式行**<br>
    周框方塊手動啟用的 UI<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="指標" width="250"><br>
    **線索**<br>
    瞭解各種類型的指標<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="Fingertip 視覺效果" width="250"><br>
     **Fingertip 視覺效果**<br>
     Fingertip 上的視覺效果 affordance, 可改善直接互動的信心<a/>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="滑桿" width="250"><br>
    **Slider**<br>
    調整支援直接右手追蹤互動之值的滑杆 UI<a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="MRTK 標準著色器" width="250"><br>
    **MRTK 標準著色器**<br>
    MRTK 的標準著色器支援各種流暢的設計項目與效能<a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="手形聯合 Chaser" width="250"><br>
     **手形聯合 Chaser**<br>
     示範如何使用 [規劃] 將物件附加至手指<a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="目視追蹤:目標選取範圍" width="250"><br>
    **目視追蹤:目標選取範圍**<br>
    結合眼睛、語音和手輸入, 快速輕鬆地在場景中選取全息影像<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="目視追蹤:巡覽" width="250"><br>
    **目視追蹤:導覽**<br>
    瞭解如何根據您要查看的內容, 自動滾動文字或流暢縮放為焦點內容<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="目視追蹤:熱度圖" width="250"><br>
    **目視追蹤:熱度圖**<br>
    記錄、載入和視覺化使用者在您的應用程式中所看到之內容的範例<a/>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a>MRTK v2 的最低需求
* Unity 2018.3.x
* Microsoft Visual Studio 2017 或更新版本
* Windows SDK 18362 + 
* Windows 10 1803 或更新版本

## <a name="new-with-mrtk-v2"></a>MRTK v2 的新版本
我們想要強調我們對這些平臺工具的承諾。  事實上, 我們利用 MRTK 第2版來開發收件匣的經驗, 例如安裝體驗 (OOBE) 和我們的混合現實學習應用程式。  您也可以預期新的 HoloLens 2 功能會先透過 MRTK 公開, 因為我們認為這是在我們的平臺上進行開發的最佳方式。 

### <a name="modular"></a>採用
我們以模組化的方式建立了它, 因此您不需要將每個工具組放在您的專案中。  這其實有幾個優點。  它可以讓您的專案大小變小, 也更容易管理。  除此之外, 因為它是使用可編寫腳本的物件所建立, 而且是介面驅動的, 所以您也可以取代自己所包含的元件, 以支援其他服務、系統和平臺。


### <a name="cross-platform"></a>跨平台
說到其他平臺, 它有跨平臺支援。  雖然這並不代表每個平臺都有現成的支援, 但我們確保當您將組建目標切換至其他平臺時, 沒有任何工具組程式碼會中斷。  模組化設計的健全性和擴充性, 讓您能夠以良好的路徑來支援多個平臺, 例如 ARCore、ARKit 和 OpenVR。


### <a name="performant"></a>性能
使用行動平臺時, 我們會考慮到效能。  這是非常重要的, 我們想要確保工具不會對您工作。


## <a name="see-also"></a>另請參閱
* [MRTK 入門指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [MRTK 檔首頁](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [安裝工具](install-the-tools.md)
* [從 HTK/MRTK 移植到 MRTK 第2版](mrtk-porting-guide.md)
