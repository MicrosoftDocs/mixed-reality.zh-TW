---
title: MRTK 101-如何使用混合現實工具組 Unity 進行基本互動（HoloLens 2、HoloLens、Windows Mixed Reality、Open VR）
description: 如何使用混合現實工具組 Unity 進行基本互動（HoloLens 2、HoloLens、Windows Mixed Reality、Open VR）
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens，MRTK，混合現實工具組，Windows Mixed Reality，設計，範例應用程式，控制項
ms.openlocfilehash: ad9d2755522c2610ae051fa61f96605e49404d2d
ms.sourcegitcommit: 5054f5c23965ce56599cb29ac9d9c6e48812dabd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2020
ms.locfileid: "75623501"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a>MRTK 101：如何使用混合現實工具組 Unity 進行基本互動（HoloLens 2、HoloLens、Windows Mixed Reality、Open VR）

![MRTK](images/MRTK101/MRTK101Cover.png)

瞭解如何使用 MRTK 來達到混合現實中一些最普遍使用的常見互動模式。

- 如何在 Unity 編輯器中模擬輸入互動？
- 如何抓取和移動物件？
- 如何調整物件大小？
- 如何以精確度移動或旋轉物件？
- 如何讓物件回應輸入事件？
- 如何新增視覺效果意見反應？
- 如何新增音訊意見反應？
- 如何使用 HoloLens 2 樣式按鈕 prefabs？
- 如何讓物件符合您的需要？
- 如何讓物件臉部？

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a>如何在 Unity 編輯器中模擬輸入互動？
MRTK 支援編輯器內的輸入模擬。 只要按一下 Unity 的 [播放] 按鈕，即可執行場景。 使用這些金鑰來模擬輸入。
按 W、A、S、D 鍵來移動相機。
按住滑鼠右鍵並移動滑鼠來尋找。
若要啟動模擬的手，請按空格鍵（右手）或左 Shift 鍵（左手邊），將模擬的手放在視圖中，按 T 或 Y 鍵以旋轉模擬手，按 Q 或 E （水準）/R 或 F （垂直）

- [在 MRTK 檔中深入瞭解輸入模擬](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a>如何抓取和移動物件？
若要讓物件 grabbable，請指派這兩個腳本： ManipulationHandler.cs 和 NearInteractionGrabbable （適用于具有明確表達之手寫輸入的直接抓取） ManipulationHandler 同時支援近乎和遠處的互動。 您可以使用 HoloLens 2 的明確的手勢追蹤輸入（接近）、手中的光線（遠）、運動控制器的橫樑（遠）、HoloLens 注視游標 & 按下（遠）來抓取和移動物件。

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a>如何調整物件大小？
ManipulationHandler.cs 支援兩個右手的縮放/旋轉。 這適用于各種輸入類型，例如 HoloLens 2 的清楚手寫輸入、HoloLens 1 的注視 + 手勢輸入，以及 Windows Mixed Reality 沉浸式耳機的動作控制器輸入。

- [若要深入瞭解如何操作處理常式，請參閱 MRTK 檔](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a>如何以精確度移動或旋轉物件？
將 BoundingBox.cs 指派給物件，以使用周框方塊，這是用來縮放和旋轉物件的介面。 根據預設，它會顯示 HoloLens 1 樣式藍色控點和電線。 若要使用 HoloLens 2 樣式的鄰近動畫控點，您必須指派 prefabs 和材質。 如需設定詳細資料，請參閱周[框方塊檔](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)和 BoundingBoxExamples 場景。

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [深入瞭解 MRTK 檔中的周框方塊](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a>如何讓物件回應輸入事件？
將 PointerHandler.cs 指派給物件。 在偵測器中，您可以使用事件 OnPointerDown （）、OnPointerUp （）、OnPointerClicked （）、OnPointerDragged （），以在腳本中使用這些事件，並執行 IMixedRealityPointerHandler。

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [在 MRTK 檔中深入瞭解輸入系統](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a>如何新增視覺效果意見反應？
將 Interactable.cs 指派給物件。 在偵測器中，建立新的主題。 您可以使用可互動的主題設定檔，輕鬆地在所有可用的輸入互動狀態中新增視覺效果的意見反應。

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


可互動提供各種類型的主題，包括著色器主題，可讓您控制每個互動狀態的著色器屬性。

- [在 MRTK 檔中深入瞭解可互動](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

視覺化意見反應的另一個重要建立區塊是 MRTK 標準著色器。 有了 MRTK Standard 著色器，您就可以輕鬆地加入視覺效果的意見反應，例如暫留光線和近光源。 由於 MRTK 標準著色器執行的計算比 Unity Standard 著色器少很多，因此您可以建立高效能的體驗。

建立新的材料，然後選取著色器的混合現實工具組 > 標準。 或者，您可以挑選其中一個使用 MRTK 標準著色器的現有材質。

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [在 MRTK 檔中深入瞭解 MRTK 標準著色器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a>如何新增音訊意見反應？
將 Spatialize 新增至物件。 然後，在公開輸入事件（例如 Interactable.cs 或 PointerHandler.cs）的腳本中，將物件指派給事件，然後選取 [Spatialize PlayOneShot （）]。 您可以使用您的音訊剪輯，或從 MRTK 的音訊資產中選擇它。

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a>如何使用 HoloLens 2 樣式按鈕 prefabs？
MRTK 提供各種類型的 HoloLens 2 shell （OS）樣式按鈕。 它提供複雜的視覺效果意見反應，例如 [近光源]、[壓縮] 方塊和 [按鈕] 介面上的 ripple 效果。

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

只要將其中一個 HoloLens 2 樣式的 pressable 按鈕拖放到您的場景中即可。 Prefab 會使用上面引進的 Interactable.cs。 您可以在可互動中使用公開的事件（例如 OnClick （））來觸發動作。

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [深入瞭解 MRTK 檔中的按鈕 prefabs](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a>如何讓物件符合您的需要？
將 RadialView.cs 腳本指派給物件。 它是規劃求解腳本系列的一部分，可讓您在3D 空間中達到各種類型的物件定位。 SolverHandler.cs 將會自動新增。
以下是 RadialView 設定的範例，以達到「延遲遵循」標記的行為，就像是 HoloLens shell 中的 [開始] 功能表。 您可以指定最小/最大距離和最小/最大視圖度。 下列範例顯示在15°內，將物件放置在 0.4 m 和 0.8 m 的範圍之間。 調整 Lerp 時間值，讓位置更新的速度更快或更慢。

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [在 MRTK 檔中深入瞭解解析器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a>如何讓物件臉部？
將 Billboard.cs 腳本指派給物件。 無論您的位置為何，它一律會面對您。 您可以指定 [pivot 軸] 選項。

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


準備好建立混合現實的絕佳體驗嗎？ 請流覽下列頁面，並深入瞭解 MRTK 和 mixed reality。

## <a name="about-the-author"></a>關於作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>盾 Yoon 公園</b><br>UX 設計工具 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>請參閱

* [混合現實工具組-Unity （MRTK） GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [MRTK 檔入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [使用 MRTK 消費者入門](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [HoloToolkit 至 MRTK 移植指導方針](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
