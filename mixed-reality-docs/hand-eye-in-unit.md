---
title: Unity 中的清楚表達手勢和眼睛追蹤
description: 有兩種主要方式可對您在 Unity、右手手勢和動作控制器的注視採取動作。
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: 手勢, 動作控制器, unity, 注視, 輸入
ms.openlocfilehash: 13016879e47b3b61eb417ce9425e48ea56c1b726
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2019
ms.locfileid: "64580836"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Unity 中的清楚表達手勢和眼睛追蹤

HoloLens 2 引進了一些嶄新的令人興奮的功能: 明確表達的手和眼睛追蹤。

利用 Unity 中的新功能, 最簡單的方式是透過 MRTK v2。 還有一些範例場景可協助您開始著手。 

* [開始使用 MRTK v2 中的清楚表達](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSystem/HandTracking.html)
* [開始使用 MRTK v2 中的眼睛追蹤](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)


# <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk-v2"></a>在 MRTK v2 中支援手、眼睛和其他元素的建築組塊

MRTK v2 提供一組 UI 控制項和建立區塊, 協助您加速開發工作。 

|  [![按鈕](images/MRTK_Button_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) [按鈕](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) | 周框方塊周[框](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)方塊[ ![ ](images/MRTK_BoundingBox_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) | 操作處理常式[操作處理常式](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) [ ![ ](images/MRTK_Manipulation_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) |
|:--- | :--- | :--- |
| 支援各種輸入法的按鈕控制項, 包括 HoloLens2's 的表達手勢 | 在3D 空間中操作物件的標準 UI | 用一或兩個手操作物件的腳本 |
|  平板電腦[平板](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html)電腦[ ![ ](images/MRTK_Slate_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html) | 系統鍵盤[系統鍵盤](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) [ ![ ](images/MRTK_SystemKeyboard_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) | [![可互動](images/InteractableExamples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)[可互動](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) |
| 2D 樣式平面, 支援以明確的手寫輸入進行滾動 | 在 Unity 中使用系統鍵盤的範例腳本  | 讓物件以視覺狀態和主題支援可互動的腳本 |
|  規劃求解[規劃](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) [ ![ ](images/MRTK_Solver_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) | 物件集合[物件集合](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) [ ![ ](images/MRTK_ObjectCollection_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) | 工具提示[工具提示](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) [ ![ ](images/MRTK_Tooltip_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) |
| 各種物件定位行為, 例如標記、主體鎖定、常數視圖大小和表面磁性 | 以三維圖形設定物件陣列的腳本 | 具有彈性錨點/pivot 系統的注釋 UI, 可用於標記動作控制器和物件。 |
|  應用程式行[應用程式行](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) [ ![ ](images/MRTK_AppBar_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) | [![指標](images/MRTK_Pointer_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html) [指標](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html) | Fingertip 視覺效果[Fingertip 視覺效果](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) [ ![ ](images/MRTK_FingertipVisualization_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) |
| 周框方塊手動啟用的 UI | 瞭解各種類型的指標 | Fingertip 上的視覺效果 affordance, 可改善直接互動的信心 |
|  [![目視追蹤:目標選擇](images/mrtk_et_targetselect.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) [眼追蹤:目標選取範圍](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) | [![目視追蹤:](images/mrtk_et_navigation.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) 流覽[眼追蹤:導覽](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) | [![目視追蹤:熱度圖](images/mrtk_et_heatmaps.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) [眼追蹤:熱度圖](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) |
| 結合眼睛、語音和手輸入, 快速輕鬆地在場景中選取全息影像 | 瞭解如何根據您要查看的內容, 自動滾動文字或流暢縮放為焦點內容| 記錄、載入和視覺化使用者在您的應用程式中所看到之內容的範例 |

# <a name="example-scenes"></a>範例場景
探索 MRTK 在[此範例場景](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)中的各種互動和 UI 控制項。

您可以在 [**資產/MixedRealityToolkit**] 下的[混合現實工具組 GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)中找到其他範例場景。

[![範例場景](images/MRTK_Examples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)

## <a name="see-also"></a>另請參閱

* [筆勢](gestures.md)
* [運動控制器](motion-controllers.md)
* [UnityEngine. XR. WSA. 輸入](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
