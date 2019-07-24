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
# <a name="getting-started-with-mrtk-v2"></a><span data-ttu-id="26522-104">開始使用 MRTK v2</span><span class="sxs-lookup"><span data-stu-id="26522-104">Getting started with MRTK v2</span></span>

## <a name="mrtk-getting-started-guide"></a><span data-ttu-id="26522-105">MRTK 消費者入門指南</span><span class="sxs-lookup"><span data-stu-id="26522-105">MRTK Getting Started Guide</span></span>
<span data-ttu-id="26522-106">如需開始使用 MRTK V2 的資訊, 請參閱[MRTK 快速入門手冊](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)。</span><span class="sxs-lookup"><span data-stu-id="26522-106">See the [MRTK getting started guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) for information on getting started with MRTK V2.</span></span>

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="26522-107">什麼是混合現實工具組 (MRTK)？</span><span class="sxs-lookup"><span data-stu-id="26522-107">What is Mixed Reality Toolkit (MRTK)?</span></span>
<span data-ttu-id="26522-108">MRTK 是一項令人驚奇的開放原始碼工具組, 自 HoloLens 首次發行之後就已經存在, 而不是我們的開發人員社區的困難工作。</span><span class="sxs-lookup"><span data-stu-id="26522-108">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="26522-109">過去3年來, 我們聽取了開發人員社區的意見反應, 並已建立 MRTK v2 來考慮最大的顧慮。</span><span class="sxs-lookup"><span data-stu-id="26522-109">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="26522-110">MRTK v2 與 Unity 是適用于混合現實應用程式的開放原始碼跨平臺開發工具組。</span><span class="sxs-lookup"><span data-stu-id="26522-110">The MRTK v2 with Unity is an open source cross-platform development kit for mixed reality applications.</span></span>  <span data-ttu-id="26522-111">MRTK 第2版的目的是要加速開發以 Microsoft HoloLens、Windows Mixed Reality 沉浸 (VR) 耳機和 OpenVR 平臺為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="26522-111">MRTK version 2 is intended to accelerate development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="26522-112">此專案的目標是減少建立混合實境應用程式的進入障礙，以及回饋伴著我們成長的社群。</span><span class="sxs-lookup"><span data-stu-id="26522-112">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span> 


<span data-ttu-id="26522-113">若要深入瞭解, 請參閱[MRTK 檔入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)。</span><span class="sxs-lookup"><span data-stu-id="26522-113">See the [MRTK documentation portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) to learn more.</span></span>

## <a name="feature-areas"></a><span data-ttu-id="26522-114">功能區</span><span class="sxs-lookup"><span data-stu-id="26522-114">Feature areas</span></span>

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="輸入系統" width="105"> <span data-ttu-id="26522-116">輸入系統</span><span class="sxs-lookup"><span data-stu-id="26522-116">Input System</span></span> 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="手動追蹤 (HoloLens 2)" width="105"> <span data-ttu-id="26522-118">手動追蹤 (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="26522-118">Hand Tracking (HoloLens 2)</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="眼睛追蹤 (HoloLens 2)" width="105">
    <span data-ttu-id="26522-120">眼睛追蹤 (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="26522-120">Eye Tracking (HoloLens 2)</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="語音命令" width="105"> <span data-ttu-id="26522-122">語音命令</span><span class="sxs-lookup"><span data-stu-id="26522-122">Voice Commanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="注視 + 選取 (HoloLens (第1代))" width="105">
    <span data-ttu-id="26522-124">注視 + 選取 (HoloLens (第1代))</span><span class="sxs-lookup"><span data-stu-id="26522-124">Gaze + Select (HoloLens (1st gen))</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="Teleportation" width="105"> <span data-ttu-id="26522-126">Teleportation</span><span class="sxs-lookup"><span data-stu-id="26522-126">Teleportation</span></span>
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="UI 控制項" width="105"> <span data-ttu-id="26522-128">UI 控制項</span><span class="sxs-lookup"><span data-stu-id="26522-128">UI Controls</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="規劃求解和互動" width="105"> <span data-ttu-id="26522-130">規劃求解和互動</span><span class="sxs-lookup"><span data-stu-id="26522-130">Solver and Interactions</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="控制器視覺效果" width="105"> <span data-ttu-id="26522-132">控制器視覺效果</span><span class="sxs-lookup"><span data-stu-id="26522-132">Controller Visualization</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="空間理解" width="105"> <span data-ttu-id="26522-134">空間理解</span><span class="sxs-lookup"><span data-stu-id="26522-134">Spatial Understanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="診斷工具" width="105"> <span data-ttu-id="26522-136">診斷工具</span><span class="sxs-lookup"><span data-stu-id="26522-136">Diagnostic Tool</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="MRTK 標準著色器" width="105"> <span data-ttu-id="26522-138">MRTK 標準著色器</span><span class="sxs-lookup"><span data-stu-id="26522-138">MRTK Standard Shader</span></span>
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a><span data-ttu-id="26522-139">UI 和互動建立區塊</span><span class="sxs-lookup"><span data-stu-id="26522-139">UI and Interaction Building blocks</span></span>

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="按鈕" width="250"><br>
    <span data-ttu-id="26522-141">**Button**</span><span class="sxs-lookup"><span data-stu-id="26522-141">**Button**</span></span><br>
    <span data-ttu-id="26522-142">一種按鈕控制項, 支援各種輸入法, 包括 HoloLens 2 的清楚表達手勢<a/></span><span class="sxs-lookup"><span data-stu-id="26522-142">A button control which supports various input methods including HoloLens 2's articulated hand <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="周框方塊" width="250"><br>
    <span data-ttu-id="26522-144">**周框方塊**</span><span class="sxs-lookup"><span data-stu-id="26522-144">**Bounding Box**</span></span><br>
    <span data-ttu-id="26522-145">在3D 空間中操作物件的標準 UI<a/></span><span class="sxs-lookup"><span data-stu-id="26522-145">Standard UI for manipulating objects in 3D space <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="操作處理常式" width="250"><br>
    <span data-ttu-id="26522-147">**操作處理常式**</span><span class="sxs-lookup"><span data-stu-id="26522-147">**Manipulation Handler**</span></span><br>
    <span data-ttu-id="26522-148">用一或兩個手操作物件的腳本<a/></span><span class="sxs-lookup"><span data-stu-id="26522-148">Script for manipulating objects with one or two hands <a/></span></span>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="石板" width="250"><br>
    <span data-ttu-id="26522-150">**石板**</span><span class="sxs-lookup"><span data-stu-id="26522-150">**Slate**</span></span> <br>
    <span data-ttu-id="26522-151">2D 樣式平面, 支援以明確的手寫輸入進行滾動<a/></span><span class="sxs-lookup"><span data-stu-id="26522-151">2D style plane which supports scrolling with articulated hand input <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="系統鍵盤" width="250"><br>
    <span data-ttu-id="26522-153">**系統鍵盤**</span><span class="sxs-lookup"><span data-stu-id="26522-153">**System Keyboard**</span></span><br>
    <span data-ttu-id="26522-154">在 Unity 中使用系統鍵盤的範例腳本<a/></span><span class="sxs-lookup"><span data-stu-id="26522-154">Example script of using the system keyboard in Unity <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="可互動" width="250"><br>
     <span data-ttu-id="26522-156">**可互動**</span><span class="sxs-lookup"><span data-stu-id="26522-156">**Interactable**</span></span> <br>
     <span data-ttu-id="26522-157">讓物件以視覺狀態和主題支援可互動的腳本<a/></span><span class="sxs-lookup"><span data-stu-id="26522-157">A script for making objects interactable with visual states and theme support <a/></span></span>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="規劃" width="250"><br>
    <span data-ttu-id="26522-159">**規劃**</span><span class="sxs-lookup"><span data-stu-id="26522-159">**Solver**</span></span> <br>
    <span data-ttu-id="26522-160">各種物件定位行為, 例如標記、主體鎖定、常數視圖大小和表面磁性<a/></span><span class="sxs-lookup"><span data-stu-id="26522-160">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="物件集合" width="250"><br>
    <span data-ttu-id="26522-162">**物件集合**</span><span class="sxs-lookup"><span data-stu-id="26522-162">**Object Collection**</span></span><br>
    <span data-ttu-id="26522-163">以三維圖形設定物件陣列的腳本<a/></span><span class="sxs-lookup"><span data-stu-id="26522-163">Script for lay out an array of objects in a three-dimensional shape <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="工具提示" width="250">  <br>
    <span data-ttu-id="26522-165">**並用**</span><span class="sxs-lookup"><span data-stu-id="26522-165">**Tooltip**</span></span><br>
    <span data-ttu-id="26522-166">具有彈性錨點/pivot 系統的注釋 UI, 可用於標記動作控制器和物件<a/></span><span class="sxs-lookup"><span data-stu-id="26522-166">Annotation UI with flexible anchor/pivot system which can be used for labeling motion controllers and object <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="應用程式行" width="250"><br>
    <span data-ttu-id="26522-168">**應用程式行**</span><span class="sxs-lookup"><span data-stu-id="26522-168">**App Bar**</span></span><br>
    <span data-ttu-id="26522-169">周框方塊手動啟用的 UI<a/></span><span class="sxs-lookup"><span data-stu-id="26522-169">UI for Bounding Box's manual activation <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="指標" width="250"><br>
    <span data-ttu-id="26522-171">**線索**</span><span class="sxs-lookup"><span data-stu-id="26522-171">**Pointers**</span></span><br>
    <span data-ttu-id="26522-172">瞭解各種類型的指標<a/></span><span class="sxs-lookup"><span data-stu-id="26522-172">Learn about various types of pointers <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="Fingertip 視覺效果" width="250"><br>
     <span data-ttu-id="26522-174">**Fingertip 視覺效果**</span><span class="sxs-lookup"><span data-stu-id="26522-174">**Fingertip Visualization**</span></span><br>
     <span data-ttu-id="26522-175">Fingertip 上的視覺效果 affordance, 可改善直接互動的信心<a/></span><span class="sxs-lookup"><span data-stu-id="26522-175">Visual affordance on the fingertip which improves the confidence for the direct interaction <a/></span></span>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="滑桿" width="250"><br>
    <span data-ttu-id="26522-177">**Slider**</span><span class="sxs-lookup"><span data-stu-id="26522-177">**Slider**</span></span><br>
    <span data-ttu-id="26522-178">調整支援直接右手追蹤互動之值的滑杆 UI<a/></span><span class="sxs-lookup"><span data-stu-id="26522-178">Slider UI for adjusting values supporting direct hand tracking interaction <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="MRTK 標準著色器" width="250"><br>
    <span data-ttu-id="26522-180">**MRTK 標準著色器**</span><span class="sxs-lookup"><span data-stu-id="26522-180">**MRTK Standard Shader**</span></span><br>
    <span data-ttu-id="26522-181">MRTK 的標準著色器支援各種流暢的設計項目與效能<a/></span><span class="sxs-lookup"><span data-stu-id="26522-181">MRTK's Standard shader supports various Fluent design elements with performance <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="手形聯合 Chaser" width="250"><br>
     <span data-ttu-id="26522-183">**手形聯合 Chaser**</span><span class="sxs-lookup"><span data-stu-id="26522-183">**Hand Joint Chaser**</span></span><br>
     <span data-ttu-id="26522-184">示範如何使用 [規劃] 將物件附加至手指<a/></span><span class="sxs-lookup"><span data-stu-id="26522-184">Demonstrates how to use Solver to attach objects to the hand joints <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="目視追蹤:目標選取範圍" width="250"><br>
    <span data-ttu-id="26522-186">**目視追蹤:目標選取範圍**</span><span class="sxs-lookup"><span data-stu-id="26522-186">**Eye Tracking: Target Selection**</span></span><br>
    <span data-ttu-id="26522-187">結合眼睛、語音和手輸入, 快速輕鬆地在場景中選取全息影像<a/></span><span class="sxs-lookup"><span data-stu-id="26522-187">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="目視追蹤:巡覽" width="250"><br>
    <span data-ttu-id="26522-189">**目視追蹤:導覽**</span><span class="sxs-lookup"><span data-stu-id="26522-189">**Eye Tracking: Navigation**</span></span><br>
    <span data-ttu-id="26522-190">瞭解如何根據您要查看的內容, 自動滾動文字或流暢縮放為焦點內容<a/></span><span class="sxs-lookup"><span data-stu-id="26522-190">Learn how to auto scroll text or fluently zoom into focused content based on what you are looking at <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="目視追蹤:熱度圖" width="250"><br>
    <span data-ttu-id="26522-192">**目視追蹤:熱度圖**</span><span class="sxs-lookup"><span data-stu-id="26522-192">**Eye Tracking: Heat Map**</span></span><br>
    <span data-ttu-id="26522-193">記錄、載入和視覺化使用者在您的應用程式中所看到之內容的範例<a/></span><span class="sxs-lookup"><span data-stu-id="26522-193">Examples for logging, loading and visualizing what users have been looking at in your app <a/></span></span>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a><span data-ttu-id="26522-194">MRTK v2 的最低需求</span><span class="sxs-lookup"><span data-stu-id="26522-194">Minimum Requirement for MRTK v2</span></span>
* <span data-ttu-id="26522-195">Unity 2018.3.x</span><span class="sxs-lookup"><span data-stu-id="26522-195">Unity 2018.3.x</span></span>
* <span data-ttu-id="26522-196">Microsoft Visual Studio 2017 或更新版本</span><span class="sxs-lookup"><span data-stu-id="26522-196">Microsoft Visual Studio 2017 or later</span></span>
* <span data-ttu-id="26522-197">Windows SDK 18362 +</span><span class="sxs-lookup"><span data-stu-id="26522-197">Windows SDK 18362+</span></span> 
* <span data-ttu-id="26522-198">Windows 10 1803 或更新版本</span><span class="sxs-lookup"><span data-stu-id="26522-198">Windows 10 1803 or later</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="26522-199">MRTK v2 的新版本</span><span class="sxs-lookup"><span data-stu-id="26522-199">New with MRTK v2</span></span>
<span data-ttu-id="26522-200">我們想要強調我們對這些平臺工具的承諾。</span><span class="sxs-lookup"><span data-stu-id="26522-200">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="26522-201">事實上, 我們利用 MRTK 第2版來開發收件匣的經驗, 例如安裝體驗 (OOBE) 和我們的混合現實學習應用程式。</span><span class="sxs-lookup"><span data-stu-id="26522-201">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="26522-202">您也可以預期新的 HoloLens 2 功能會先透過 MRTK 公開, 因為我們認為這是在我們的平臺上進行開發的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="26522-202">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="26522-203">採用</span><span class="sxs-lookup"><span data-stu-id="26522-203">Modular</span></span>
<span data-ttu-id="26522-204">我們以模組化的方式建立了它, 因此您不需要將每個工具組放在您的專案中。</span><span class="sxs-lookup"><span data-stu-id="26522-204">We have built it in a modular way, so that you do not need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="26522-205">這其實有幾個優點。</span><span class="sxs-lookup"><span data-stu-id="26522-205">There are actually a few benefits to this.</span></span>  <span data-ttu-id="26522-206">它可以讓您的專案大小變小, 也更容易管理。</span><span class="sxs-lookup"><span data-stu-id="26522-206">It keeps your project size smaller, as well as makes it easier to manage.</span></span>  <span data-ttu-id="26522-207">除此之外, 因為它是使用可編寫腳本的物件所建立, 而且是介面驅動的, 所以您也可以取代自己所包含的元件, 以支援其他服務、系統和平臺。</span><span class="sxs-lookup"><span data-stu-id="26522-207">On top of that, because it’s built with scriptable objects and is interface driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>


### <a name="cross-platform"></a><span data-ttu-id="26522-208">跨平台</span><span class="sxs-lookup"><span data-stu-id="26522-208">Cross-platform</span></span>
<span data-ttu-id="26522-209">說到其他平臺, 它有跨平臺支援。</span><span class="sxs-lookup"><span data-stu-id="26522-209">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="26522-210">雖然這並不代表每個平臺都有現成的支援, 但我們確保當您將組建目標切換至其他平臺時, 沒有任何工具組程式碼會中斷。</span><span class="sxs-lookup"><span data-stu-id="26522-210">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="26522-211">模組化設計的健全性和擴充性, 讓您能夠以良好的路徑來支援多個平臺, 例如 ARCore、ARKit 和 OpenVR。</span><span class="sxs-lookup"><span data-stu-id="26522-211">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>


### <a name="performant"></a><span data-ttu-id="26522-212">性能</span><span class="sxs-lookup"><span data-stu-id="26522-212">Performant</span></span>
<span data-ttu-id="26522-213">使用行動平臺時, 我們會考慮到效能。</span><span class="sxs-lookup"><span data-stu-id="26522-213">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="26522-214">這是非常重要的, 我們想要確保工具不會對您工作。</span><span class="sxs-lookup"><span data-stu-id="26522-214">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>


## <a name="see-also"></a><span data-ttu-id="26522-215">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26522-215">See also</span></span>
* [<span data-ttu-id="26522-216">MRTK 入門指南</span><span class="sxs-lookup"><span data-stu-id="26522-216">MRTK getting started guide</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="26522-217">MRTK 檔首頁</span><span class="sxs-lookup"><span data-stu-id="26522-217">MRTK documentation home</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="26522-218">安裝工具</span><span class="sxs-lookup"><span data-stu-id="26522-218">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="26522-219">從 HTK/MRTK 移植到 MRTK 第2版</span><span class="sxs-lookup"><span data-stu-id="26522-219">Porting from HTK/MRTK to MRTK version 2</span></span>](mrtk-porting-guide.md)
