---
title: Unity 中的清楚表達手勢和眼睛追蹤
description: 有兩種主要方式可對您在 Unity、右手手勢和動作控制器的注視採取動作。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 手勢，動作控制器，unity，注視，輸入
ms.openlocfilehash: b83c4904031338fd6f3e8457238bb76f1c7e7eff
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181948"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Unity 中的清楚表達手勢和眼睛追蹤

HoloLens 2 引進了一些嶄新的令人興奮的功能：明確表達的手和眼睛追蹤。

利用 Unity 中的新功能，最簡單的方式是透過 MRTK v2。 還有一些範例場景可協助您開始著手。

* [開始使用 MRTK v2 中的清楚表達](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/HandTracking.html)
* [開始使用 MRTK v2 中的眼睛追蹤](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)

## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk-v2"></a>在 MRTK v2 中支援手、眼睛和其他元素的建築組塊

MRTK v2 提供一組 UI 控制項和建立區塊，協助您加速開發工作。

|  [![按鈕](images/MRTK_Button_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) [按鈕](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) | [![周框](images/MRTK_BoundingBox_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)方塊周[框](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)方塊 | [![操作處理常式](images/MRTK_Manipulation_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)[操作處理常式](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) |
|:--- | :--- | :--- |
| 支援各種輸入法的按鈕控制項，包括 HoloLens2's 的表達手勢 | 在3D 空間中操作物件的標準 UI | 用一或兩個手操作物件的腳本 |
|  [![平板](images/MRTK_Slate_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html)電腦[平板](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html)電腦 | [![系統鍵盤](images/MRTK_SystemKeyboard_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html)[系統鍵盤](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) | [![可互動](images/InteractableExamples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)[可互動](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) |
| 2D 樣式平面，支援以明確的手寫輸入進行滾動 | 在 Unity 中使用系統鍵盤的範例腳本  | 讓物件以視覺狀態和主題支援可互動的腳本 |
|  [![的規劃](images/MRTK_Solver_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)[求解](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) | [![物件集合](images/MRTK_ObjectCollection_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)[物件集合](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) | [![工具](images/MRTK_Tooltip_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html)提示[工具提示](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) |
| 各種物件定位行為，例如標記、主體鎖定、常數視圖大小和表面磁性 | 以三維圖形設定物件陣列的腳本 | 具有彈性錨點/pivot 系統的注釋 UI，可用於標記動作控制器和物件。 |
|  [![應用程式行](images/MRTK_AppBar_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)[應用程式行](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) | [![指標](images/MRTK_Pointer_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html) [指標](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html) | [![Fingertip 視覺化](images/MRTK_FingertipVisualization_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) [Fingertip 視覺效果](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) |
| 周框方塊手動啟用的 UI | 瞭解各種類型的指標 | Fingertip 上的視覺效果 affordance，可改善直接互動的信心 |
|  [![眼追蹤：目標選取範圍](images/mrtk_et_targetselect.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html)[眼追蹤：目標選取範圍](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) | [![眼追蹤：導覽](images/mrtk_et_navigation.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html)[眼追蹤：導覽](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) | [![眼追蹤：熱度圖](images/mrtk_et_heatmaps.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html)[眼睛追蹤：熱度圖](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) |
| 結合眼睛、語音和手輸入，快速輕鬆地在場景中選取全息影像 | 瞭解如何根據您要查看的內容，自動滾動文字或流暢縮放為焦點內容| 記錄、載入和視覺化使用者在您的應用程式中所看到之內容的範例 |

## <a name="example-scenes"></a>範例場景

探索 MRTK 在[此範例場景](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)中的各種互動和 UI 控制項。

您可以在 [**資產/MixedRealityToolkit**] 下的[混合現實工具組 GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)中找到其他範例場景。

[![範例場景](images/MRTK_Examples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)

## <a name="see-also"></a>請參閱

* [眼動式互動] (eye-gaze-interaction.md)
* [HoloLens 2 的眼球追蹤] (eye-tracking.md)
* [目光和行動](gaze-and-commit.md)
* [手 - 直接操作](direct-manipulation.md)
* [手 - 手勢](gaze-and-commit.md#composite-gestures)
* [手 - 指向和行動](point-and-commit.md)
* [本能互動](interaction-fundamentals.md)
* [運動控制器](motion-controllers.md)
* [UnityEngine. XR. WSA. 輸入](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
