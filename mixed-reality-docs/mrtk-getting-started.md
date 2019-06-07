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
# <a name="getting-started-with-mrtk-v2"></a><span data-ttu-id="f5216-104">開始使用 MRTK v2</span><span class="sxs-lookup"><span data-stu-id="f5216-104">Getting started with MRTK v2</span></span>

## <a name="mrtk-getting-started-guide"></a><span data-ttu-id="f5216-105">MRTK 入門指南</span><span class="sxs-lookup"><span data-stu-id="f5216-105">MRTK Getting Started Guide</span></span>
<span data-ttu-id="f5216-106">請參閱[MRTK 入門指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)MRTK V2 使用者入門資訊。</span><span class="sxs-lookup"><span data-stu-id="f5216-106">See the [MRTK getting started guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) for information on getting started with MRTK V2.</span></span>

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="f5216-107">什麼是混合實境工具組 (MRTK)？</span><span class="sxs-lookup"><span data-stu-id="f5216-107">What is Mixed Reality Toolkit (MRTK)?</span></span>
<span data-ttu-id="f5216-108">MRTK 是令人讚嘆的開放原始碼工具組，因為 HoloLens 首次發行，而且不會很今天不會導致我們開發人員社群的困難的工作已存在。</span><span class="sxs-lookup"><span data-stu-id="f5216-108">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="f5216-109">過去 3 年來，我們已聽到了我們的開發人員社群的意見反應，並建置 MRTK v2，需要考量的最大考量。</span><span class="sxs-lookup"><span data-stu-id="f5216-109">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="f5216-110">使用 Unity MRTK v2 是開放原始碼跨平台開發套件的混合的實境應用程式。</span><span class="sxs-lookup"><span data-stu-id="f5216-110">The MRTK v2 with Unity is an open source cross-platform development kit for mixed reality applications.</span></span>  <span data-ttu-id="f5216-111">MRTK 第 2 版被要加速開發以 Microsoft HoloLens，Windows Mixed Reality 沈浸式 (VR) 耳機和 OpenVR 平台為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f5216-111">MRTK version 2 is intended to accelerate development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="f5216-112">專案被針對至項目，以建立混合的實境應用程式以及貢獻回饋給社群隨著我們越來越減少屏障。</span><span class="sxs-lookup"><span data-stu-id="f5216-112">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span> 


<span data-ttu-id="f5216-113">請參閱[MRTK 說明文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)若要深入了。</span><span class="sxs-lookup"><span data-stu-id="f5216-113">See the [MRTK documentation portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) to learn more.</span></span>

## <a name="feature-areas"></a><span data-ttu-id="f5216-114">功能區</span><span class="sxs-lookup"><span data-stu-id="f5216-114">Feature areas</span></span>

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="輸入的系統" width="105"> <span data-ttu-id="f5216-116">輸入的系統</span><span class="sxs-lookup"><span data-stu-id="f5216-116">Input System</span></span> 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="手動追蹤 (HoloLens 2)" width="105"> <span data-ttu-id="f5216-118">手動追蹤 (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="f5216-118">Hand Tracking (HoloLens 2)</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="追蹤 (HoloLens 2)" width="105">
    <span data-ttu-id="f5216-120">追蹤 (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="f5216-120">Eye Tracking (HoloLens 2)</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="語音命令" width="105"> <span data-ttu-id="f5216-122">語音命令</span><span class="sxs-lookup"><span data-stu-id="f5216-122">Voice Commanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="視線 + 選取 (HoloLens （第 1 代）)" width="105">
    <span data-ttu-id="f5216-124">視線 + 選取 (HoloLens （第 1 代）)</span><span class="sxs-lookup"><span data-stu-id="f5216-124">Gaze + Select (HoloLens (1st gen))</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="屏障" width="105"> <span data-ttu-id="f5216-126">屏障</span><span class="sxs-lookup"><span data-stu-id="f5216-126">Teleportation</span></span>
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="UI 控制項" width="105"> <span data-ttu-id="f5216-128">UI 控制項</span><span class="sxs-lookup"><span data-stu-id="f5216-128">UI Controls</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="求解器和互動" width="105"> <span data-ttu-id="f5216-130">求解器和互動</span><span class="sxs-lookup"><span data-stu-id="f5216-130">Solver and Interactions</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="控制器的視覺效果" width="105"> <span data-ttu-id="f5216-132">控制器的視覺效果</span><span class="sxs-lookup"><span data-stu-id="f5216-132">Controller Visualization</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="了解空間" width="105"> <span data-ttu-id="f5216-134">了解空間</span><span class="sxs-lookup"><span data-stu-id="f5216-134">Spatial Understanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="診斷工具" width="105"> <span data-ttu-id="f5216-136">診斷工具</span><span class="sxs-lookup"><span data-stu-id="f5216-136">Diagnostic Tool</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="MRTK 標準著色器" width="105"> <span data-ttu-id="f5216-138">MRTK 標準著色器</span><span class="sxs-lookup"><span data-stu-id="f5216-138">MRTK Standard Shader</span></span>
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a><span data-ttu-id="f5216-139">UI 和互動的建置區塊</span><span class="sxs-lookup"><span data-stu-id="f5216-139">UI and Interaction Building blocks</span></span>

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="按鈕" width="250"><br>
    <span data-ttu-id="f5216-141">**Button**</span><span class="sxs-lookup"><span data-stu-id="f5216-141">**Button**</span></span><br>
    <span data-ttu-id="f5216-142">按鈕控制項可支援各種輸入的方法，包括 HoloLens 2 相互連貫的手 <a/></span><span class="sxs-lookup"><span data-stu-id="f5216-142">A button control which supports various input methods including HoloLens 2's articulated hand <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="週框方塊" width="250"><br>
    <span data-ttu-id="f5216-144">**週框方塊**</span><span class="sxs-lookup"><span data-stu-id="f5216-144">**Bounding Box**</span></span><br>
    <span data-ttu-id="f5216-145">操作在 3D 空間中的物件的標準 UI <a/></span><span class="sxs-lookup"><span data-stu-id="f5216-145">Standard UI for manipulating objects in 3D space <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="操作處理常式" width="250"><br>
    <span data-ttu-id="f5216-147">**操作處理常式**</span><span class="sxs-lookup"><span data-stu-id="f5216-147">**Manipulation Handler**</span></span><br>
    <span data-ttu-id="f5216-148">用於管理一或兩個實際操作物件的指令碼 <a/></span><span class="sxs-lookup"><span data-stu-id="f5216-148">Script for manipulating objects with one or two hands <a/></span></span>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="候選影片" width="250"><br>
    <span data-ttu-id="f5216-150">**候選影片**</span><span class="sxs-lookup"><span data-stu-id="f5216-150">**Slate**</span></span> <br>
    <span data-ttu-id="f5216-151">支援捲動相互連貫的手動輸入樣式 2D 平面 <a/></span><span class="sxs-lookup"><span data-stu-id="f5216-151">2D style plane which supports scrolling with articulated hand input <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="系統鍵盤" width="250"><br>
    <span data-ttu-id="f5216-153">**系統鍵盤**</span><span class="sxs-lookup"><span data-stu-id="f5216-153">**System Keyboard**</span></span><br>
    <span data-ttu-id="f5216-154">在 Unity 中使用系統鍵盤的範例指令碼 <a/></span><span class="sxs-lookup"><span data-stu-id="f5216-154">Example script of using the system keyboard in Unity <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="互動" width="250"><br>
     <span data-ttu-id="f5216-156">**Interactable**</span><span class="sxs-lookup"><span data-stu-id="f5216-156">**Interactable**</span></span> <br>
     <span data-ttu-id="f5216-157">讓物件可透過視覺狀態和佈景主題支援互動的指令碼 <a/></span><span class="sxs-lookup"><span data-stu-id="f5216-157">A script for making objects interactable with visual states and theme support <a/></span></span>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="規劃求解" width="250"><br>
    <span data-ttu-id="f5216-159">**Solver**</span><span class="sxs-lookup"><span data-stu-id="f5216-159">**Solver**</span></span> <br>
    <span data-ttu-id="f5216-160">各種物件位置的行為，例如 tag-along、 主體鎖定、 常數的檢視大小和介面的磁場 <a/></span><span class="sxs-lookup"><span data-stu-id="f5216-160">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="物件集合" width="250"><br>
    <span data-ttu-id="f5216-162">**物件集合**</span><span class="sxs-lookup"><span data-stu-id="f5216-162">**Object Collection**</span></span><br>
    <span data-ttu-id="f5216-163">3d 圖形中的物件陣列配置的指令碼 <a/></span><span class="sxs-lookup"><span data-stu-id="f5216-163">Script for lay out an array of objects in a three-dimensional shape <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="工具提示" width="250">  <br>
    <span data-ttu-id="f5216-165">**Tooltip**</span><span class="sxs-lookup"><span data-stu-id="f5216-165">**Tooltip**</span></span><br>
    <span data-ttu-id="f5216-166">具有彈性的錨點/樞紐分析系統，可用來標記控制器動作和物件的註釋 UI <a/></span><span class="sxs-lookup"><span data-stu-id="f5216-166">Annotation UI with flexible anchor/pivot system which can be used for labeling motion controllers and object <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="應用程式列" width="250"><br>
    <span data-ttu-id="f5216-168">**App Bar**</span><span class="sxs-lookup"><span data-stu-id="f5216-168">**App Bar**</span></span><br>
    <span data-ttu-id="f5216-169">週框方塊的手動啟動的 UI <a/></span><span class="sxs-lookup"><span data-stu-id="f5216-169">UI for Bounding Box's manual activation <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="指標" width="250"><br>
    <span data-ttu-id="f5216-171">**指標**</span><span class="sxs-lookup"><span data-stu-id="f5216-171">**Pointers**</span></span><br>
    <span data-ttu-id="f5216-172">深入了解各種類型的指標 <a/></span><span class="sxs-lookup"><span data-stu-id="f5216-172">Learn about various types of pointers <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="用手指對視覺效果" width="250"><br>
     <span data-ttu-id="f5216-174">**用手指對視覺效果**</span><span class="sxs-lookup"><span data-stu-id="f5216-174">**Fingertip Visualization**</span></span><br>
     <span data-ttu-id="f5216-175">視覺化功能上改進了直接互動的信心寫寫看的可見性 <a/></span><span class="sxs-lookup"><span data-stu-id="f5216-175">Visual affordance on the fingertip which improves the confidence for the direct interaction <a/></span></span>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="滑桿" width="250"><br>
    <span data-ttu-id="f5216-177">**Slider**</span><span class="sxs-lookup"><span data-stu-id="f5216-177">**Slider**</span></span><br>
    <span data-ttu-id="f5216-178">滑桿 UI 調整值支援的直接手動追蹤互動 <a/></span><span class="sxs-lookup"><span data-stu-id="f5216-178">Slider UI for adjusting values supporting direct hand tracking interaction <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="MRTK 標準著色器" width="250"><br>
    <span data-ttu-id="f5216-180">**MRTK 標準著色器**</span><span class="sxs-lookup"><span data-stu-id="f5216-180">**MRTK Standard Shader**</span></span><br>
    <span data-ttu-id="f5216-181">MRTK 的標準著色器支援與效能的各種 Fluent 設計元素 <a/></span><span class="sxs-lookup"><span data-stu-id="f5216-181">MRTK's Standard shader supports various Fluent design elements with performance <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="手動聯結 Chaser" width="250"><br>
     <span data-ttu-id="f5216-183">**手動聯結 Chaser**</span><span class="sxs-lookup"><span data-stu-id="f5216-183">**Hand Joint Chaser**</span></span><br>
     <span data-ttu-id="f5216-184">示範如何使用求解器將物件附加至手動接合 <a/></span><span class="sxs-lookup"><span data-stu-id="f5216-184">Demonstrates how to use Solver to attach objects to the hand joints <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="追蹤的眼睛：目標選取項目" width="250"><br>
    <span data-ttu-id="f5216-186">**追蹤的眼睛：目標選取項目**</span><span class="sxs-lookup"><span data-stu-id="f5216-186">**Eye Tracking: Target Selection**</span></span><br>
    <span data-ttu-id="f5216-187">結合眼睛、 語音及輸入以快速又輕鬆地在場景中選取全像投影的手 <a/></span><span class="sxs-lookup"><span data-stu-id="f5216-187">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="追蹤的眼睛：巡覽" width="250"><br>
    <span data-ttu-id="f5216-189">**追蹤的眼睛：瀏覽**</span><span class="sxs-lookup"><span data-stu-id="f5216-189">**Eye Tracking: Navigation**</span></span><br>
    <span data-ttu-id="f5216-190">了解如何自動捲動文字或焦點內容會根據您要尋找在流暢縮放 <a/></span><span class="sxs-lookup"><span data-stu-id="f5216-190">Learn how to auto scroll text or fluently zoom into focused content based on what you are looking at <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="追蹤的眼睛：熱度圖" width="250"><br>
    <span data-ttu-id="f5216-192">**追蹤的眼睛：熱度圖**</span><span class="sxs-lookup"><span data-stu-id="f5216-192">**Eye Tracking: Heat Map**</span></span><br>
    <span data-ttu-id="f5216-193">記錄的範例，載入和視覺化的哪些使用者有探討了在您的應用程式 <a/></span><span class="sxs-lookup"><span data-stu-id="f5216-193">Examples for logging, loading and visualizing what users have been looking at in your app <a/></span></span>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a><span data-ttu-id="f5216-194">最低需求 MRTK v2</span><span class="sxs-lookup"><span data-stu-id="f5216-194">Minimum Requirement for MRTK v2</span></span>
* <span data-ttu-id="f5216-195">Unity 2018.3.x</span><span class="sxs-lookup"><span data-stu-id="f5216-195">Unity 2018.3.x</span></span>
* <span data-ttu-id="f5216-196">Microsoft Visual Studio 2017 或更新版本</span><span class="sxs-lookup"><span data-stu-id="f5216-196">Microsoft Visual Studio 2017 or later</span></span>
* <span data-ttu-id="f5216-197">Windows SDK 18362+</span><span class="sxs-lookup"><span data-stu-id="f5216-197">Windows SDK 18362+</span></span> 
* <span data-ttu-id="f5216-198">Windows 10 1803年或更新版本</span><span class="sxs-lookup"><span data-stu-id="f5216-198">Windows 10 1803 or later</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="f5216-199">新 MRTK v2</span><span class="sxs-lookup"><span data-stu-id="f5216-199">New with MRTK v2</span></span>
<span data-ttu-id="f5216-200">我們想要強調致力於這些平台工具。</span><span class="sxs-lookup"><span data-stu-id="f5216-200">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="f5216-201">事實上，我們運用 MRTK 第 2 版來開發我們的收件匣體驗，例如安裝體驗 (OOBE) 及混合實境學習應用程式。</span><span class="sxs-lookup"><span data-stu-id="f5216-201">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="f5216-202">您也可以預期看到新的 HoloLens 2 功能，因為我們認為它可以在我們的平台上進行開發的最佳方式，先透過 MRTK。</span><span class="sxs-lookup"><span data-stu-id="f5216-202">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="f5216-203">模組化</span><span class="sxs-lookup"><span data-stu-id="f5216-203">Modular</span></span>
<span data-ttu-id="f5216-204">我們已建置模組化的方式，使您不需要納入您的專案中的每個位元工具組。</span><span class="sxs-lookup"><span data-stu-id="f5216-204">We have built it in a modular way, so that you do not need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="f5216-205">有幾個優點實際上這個。</span><span class="sxs-lookup"><span data-stu-id="f5216-205">There are actually a few benefits to this.</span></span>  <span data-ttu-id="f5216-206">它會保留您專案的大小比較小，以及可讓您更容易管理。</span><span class="sxs-lookup"><span data-stu-id="f5216-206">It keeps your project size smaller, as well as makes it easier to manage.</span></span>  <span data-ttu-id="f5216-207">除此之外，，因為它由可編寫指令碼物件所建立，並且遵守介面，它也是讓您將會包含以您自己的資源，以支援其他服務、 系統與平台的元件。</span><span class="sxs-lookup"><span data-stu-id="f5216-207">On top of that, because it’s built with scriptable objects and is interface driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>


### <a name="cross-platform"></a><span data-ttu-id="f5216-208">跨平台</span><span class="sxs-lookup"><span data-stu-id="f5216-208">Cross-platform</span></span>
<span data-ttu-id="f5216-209">它說到其他平台，提供跨平台支援。</span><span class="sxs-lookup"><span data-stu-id="f5216-209">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="f5216-210">這並不表示每個單一平台支援現成的雖然我們已經確定當您切換到其他平台的建置目標，工具組程式碼都將會中斷。</span><span class="sxs-lookup"><span data-stu-id="f5216-210">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="f5216-211">強固性和擴充性的模組化設計設定您要能夠支援多種平台，例如 ARCore、 ARKit，以及 OpenVR 良好的路徑上。</span><span class="sxs-lookup"><span data-stu-id="f5216-211">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>


### <a name="performant"></a><span data-ttu-id="f5216-212">高效能</span><span class="sxs-lookup"><span data-stu-id="f5216-212">Performant</span></span>
<span data-ttu-id="f5216-213">使用行動裝置平台，我們就以建構效能考量。</span><span class="sxs-lookup"><span data-stu-id="f5216-213">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="f5216-214">這是非常重要的是，和我們想要確保，不會針對您的工具。</span><span class="sxs-lookup"><span data-stu-id="f5216-214">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>


## <a name="see-also"></a><span data-ttu-id="f5216-215">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5216-215">See also</span></span>
* [<span data-ttu-id="f5216-216">MRTK 入門指南</span><span class="sxs-lookup"><span data-stu-id="f5216-216">MRTK getting started guide</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="f5216-217">MRTK 文件首頁</span><span class="sxs-lookup"><span data-stu-id="f5216-217">MRTK documentation home</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="f5216-218">安裝工具</span><span class="sxs-lookup"><span data-stu-id="f5216-218">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="f5216-219">從 HTK/MRTK 移植到 MRTK 第 2 版</span><span class="sxs-lookup"><span data-stu-id="f5216-219">Porting from HTK/MRTK to MRTK version 2</span></span>](mrtk-porting-guide.md)
