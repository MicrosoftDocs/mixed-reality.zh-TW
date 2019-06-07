---
title: 開始使用 MRTK 第 2 版
description: 適用於新的開發人員感興趣利用 MRTK
author: Yoyoz
ms.author: Yoyoz
ms.date: 05/15/19
ms.topic: article
keywords: Windows Mixed Reality，測試混合實境工具組、 MRTK 第 2 版、 MRTK、 工具、 SDK、 HoloLens、 HoloLens 2
ms.openlocfilehash: 249a0ce0e608410983934b75e399d013e1ff1879
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750360"
---
# <a name="getting-started-with-mrtk-v2"></a>開始使用 MRTK v2

## <a name="mrtk-getting-started-guide"></a>MRTK 入門指南
請參閱[MRTK 入門指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)MRTK V2 使用者入門資訊。

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>什麼是混合實境工具組 (MRTK)？
MRTK 是令人讚嘆的開放原始碼工具組，因為 HoloLens 首次發行，而且不會很今天不會導致我們開發人員社群的困難的工作已存在。 過去 3 年來，我們已聽到了我們的開發人員社群的意見反應，並建置 MRTK v2，需要考量的最大考量。  

使用 Unity MRTK v2 是開放原始碼跨平台開發套件的混合的實境應用程式。  MRTK 第 2 版被要加速開發以 Microsoft HoloLens，Windows Mixed Reality 沈浸式 (VR) 耳機和 OpenVR 平台為目標的應用程式。 專案被針對至項目，以建立混合的實境應用程式以及貢獻回饋給社群隨著我們越來越減少屏障。 


請參閱[MRTK 說明文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)若要深入了。

## <a name="feature-areas"></a>功能區

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="輸入的系統" width="105"> 輸入的系統 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="手動追蹤 (HoloLens 2)" width="105"> 手動追蹤 (HoloLens 2)
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="追蹤 (HoloLens 2)" width="105">
    追蹤 (HoloLens 2)
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="語音命令" width="105"> 語音命令
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="視線 + 選取 (HoloLens （第 1 代）)" width="105">
    視線 + 選取 (HoloLens （第 1 代）)
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="屏障" width="105"> 屏障
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="UI 控制項" width="105"> UI 控制項
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="求解器和互動" width="105"> 求解器和互動
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="控制器的視覺效果" width="105"> 控制器的視覺效果
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="了解空間" width="105"> 了解空間
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="診斷工具" width="105"> 診斷工具
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="MRTK 標準著色器" width="105"> MRTK 標準著色器
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a>UI 和互動的建置區塊

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="按鈕" width="250"><br>
    **Button**<br>
    按鈕控制項可支援各種輸入的方法，包括 HoloLens 2 相互連貫的手 <a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="週框方塊" width="250"><br>
    **週框方塊**<br>
    操作在 3D 空間中的物件的標準 UI <a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="操作處理常式" width="250"><br>
    **操作處理常式**<br>
    用於管理一或兩個實際操作物件的指令碼 <a/>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="候選影片" width="250"><br>
    **候選影片** <br>
    支援捲動相互連貫的手動輸入樣式 2D 平面 <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="系統鍵盤" width="250"><br>
    **系統鍵盤**<br>
    在 Unity 中使用系統鍵盤的範例指令碼 <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="互動" width="250"><br>
     **Interactable** <br>
     讓物件可透過視覺狀態和佈景主題支援互動的指令碼 <a/>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="規劃求解" width="250"><br>
    **Solver** <br>
    各種物件位置的行為，例如 tag-along、 主體鎖定、 常數的檢視大小和介面的磁場 <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="物件集合" width="250"><br>
    **物件集合**<br>
    3d 圖形中的物件陣列配置的指令碼 <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="工具提示" width="250">  <br>
    **Tooltip**<br>
    具有彈性的錨點/樞紐分析系統，可用來標記控制器動作和物件的註釋 UI <a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="應用程式列" width="250"><br>
    **App Bar**<br>
    週框方塊的手動啟動的 UI <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="指標" width="250"><br>
    **指標**<br>
    深入了解各種類型的指標 <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="用手指對視覺效果" width="250"><br>
     **用手指對視覺效果**<br>
     視覺化功能上改進了直接互動的信心寫寫看的可見性 <a/>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="滑桿" width="250"><br>
    **Slider**<br>
    滑桿 UI 調整值支援的直接手動追蹤互動 <a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="MRTK 標準著色器" width="250"><br>
    **MRTK 標準著色器**<br>
    MRTK 的標準著色器支援與效能的各種 Fluent 設計元素 <a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="手動聯結 Chaser" width="250"><br>
     **手動聯結 Chaser**<br>
     示範如何使用求解器將物件附加至手動接合 <a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="追蹤的眼睛：目標選取項目" width="250"><br>
    **追蹤的眼睛：目標選取項目**<br>
    結合眼睛、 語音及輸入以快速又輕鬆地在場景中選取全像投影的手 <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="追蹤的眼睛：巡覽" width="250"><br>
    **追蹤的眼睛：瀏覽**<br>
    了解如何自動捲動文字或焦點內容會根據您要尋找在流暢縮放 <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="追蹤的眼睛：熱度圖" width="250"><br>
    **追蹤的眼睛：熱度圖**<br>
    記錄的範例，載入和視覺化的哪些使用者有探討了在您的應用程式 <a/>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a>最低需求 MRTK v2
* Unity 2018.3.x
* Microsoft Visual Studio 2017 或更新版本
* Windows SDK 18362+ 
* Windows 10 1803年或更新版本

## <a name="new-with-mrtk-v2"></a>新 MRTK v2
我們想要強調致力於這些平台工具。  事實上，我們運用 MRTK 第 2 版來開發我們的收件匣體驗，例如安裝體驗 (OOBE) 及混合實境學習應用程式。  您也可以預期看到新的 HoloLens 2 功能，因為我們認為它可以在我們的平台上進行開發的最佳方式，先透過 MRTK。 

### <a name="modular"></a>模組化
我們已建置模組化的方式，使您不需要納入您的專案中的每個位元工具組。  有幾個優點實際上這個。  它會保留您專案的大小比較小，以及可讓您更容易管理。  除此之外，，因為它由可編寫指令碼物件所建立，並且遵守介面，它也是讓您將會包含以您自己的資源，以支援其他服務、 系統與平台的元件。


### <a name="cross-platform"></a>跨平台
它說到其他平台，提供跨平台支援。  這並不表示每個單一平台支援現成的雖然我們已經確定當您切換到其他平台的建置目標，工具組程式碼都將會中斷。  強固性和擴充性的模組化設計設定您要能夠支援多種平台，例如 ARCore、 ARKit，以及 OpenVR 良好的路徑上。


### <a name="performant"></a>高效能
使用行動裝置平台，我們就以建構效能考量。  這是非常重要的是，和我們想要確保，不會針對您的工具。


## <a name="see-also"></a>另請參閱
* [MRTK 入門指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [MRTK 文件首頁](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [安裝工具](install-the-tools.md)
* [從 HTK/MRTK 移植到 MRTK 第 2 版](mrtk-porting-guide.md)
