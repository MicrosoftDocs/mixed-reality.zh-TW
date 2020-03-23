---
title: MRTK 101 - 如何使用混合實境工具組 Unity 進行基本互動 (HoloLens 2、HoloLens、Windows Mixed Reality、Open VR)
description: 如何使用混合實境工具組 Unity 進行基本互動 (HoloLens 2、HoloLens、Windows Mixed Reality、Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, 混合實境工具組, Windows Mixed Reality, 設計, 範例應用程式, 控制項
ms.localizationpriority: high
ms.openlocfilehash: 4564e7a0c6a717452effacae2587461fe283cf0b
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/10/2020
ms.locfileid: "79028316"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a>MRTK 101：如何使用混合實境工具組 Unity 進行基本互動 (HoloLens 2、HoloLens、Windows Mixed Reality、Open VR)

![MRTK](images/MRTK101/MRTK101Cover.png)

了解如何使用 MRTK 來實現混合實境中一些最廣泛使用的常見互動模式。

- 如何在 Unity 編輯器中模擬輸入互動？
- 如何抓取和移動物件？
- 如何調整物件大小？
- 如何精確地移動或旋轉物件？
- 如何讓物件回應輸入事件？
- 如何新增視覺回饋？
- 如何新增音訊回饋？
- 如何使用 HoloLens 2 樣式的按鈕 Prefab？
- 如何讓物件跟著您移動？
- 如何讓物件面對您？

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a>如何在 Unity 編輯器中模擬輸入互動？
MRTK 支援編輯器內的輸入模擬。 只要按一下 Unity 的開始遊戲按鈕，即可執行場景。 使用這些按鍵來模擬輸入。
按 W、A、S、D 鍵來移動相機。
按住滑鼠右鍵並移動滑鼠來瀏覽。
若要顯示模擬的手部，請按空格鍵 (右手) 或左 Shift 鍵 (左手)；若要將模擬的手部放入視圖中，請按 T 或 Y 鍵；若要旋轉模擬的手部，請按 Q 或 E (水平) / R 或 F (垂直)

- [在 MRTK 文件中深入了解輸入模擬](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a>如何抓取和移動物件？
若要讓物件可供抓取，請指派這兩個指令碼：ManipulationHandler.cs 和 NearInteractionGrabbable.cs (適用於以接合手部追蹤輸入進行直接抓取) ManipulationHandler 可支援近處和遠處的互動。 您可以使用 HoloLens 2 的接合手部追蹤輸入 (近處)、手部射線 (遠處)、運動控制器的光束 (遠處)、HoloLens 注視游標與空間點選 (遠處) 來抓取和移動物件。

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a>如何調整物件大小？
ManipulationHandler.cs 支援兩手的縮放/旋轉。 這適用於各種輸入類型，例如 HoloLens 2 的接合手部輸入、HoloLens 1 的注視 + 手勢輸入，以及 Windows Mixed Reality 沉浸式頭戴裝置的動作控制器輸入。

- [在 MRTK 文件中深入了解操作處理器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a>如何精確地移動或旋轉物件？
將 BoundingBox.cs 指派給物件以使用周框方塊，也就是用來縮放和旋轉物件的介面。 根據預設，其會顯示 HoloLens 1 樣式的藍色控點和連接線。 若要使用 HoloLens 2 樣式的鄰近動畫控點，您必須指派 Prefab 和材質。 如需有關設定的詳細資料，請參閱[周框方塊文件](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)和 BBoundingBoxExamples.unity 場景。

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [在 MRTK 文件中深入了解周框方塊](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a>如何讓物件回應輸入事件？
將 PointerHandler.cs 指派給物件。 在偵測器中，您可以使用 OnPointerDown()、OnPointerUp()、OnPointerClicked()、OnPointerDragged() 事件。若要在指令碼中使用這些事件，請實作 IMixedRealityPointerHandler。

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [在 MRTK 文件中深入了解輸入系統](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a>如何新增視覺回饋？
將 Interactable.cs 指派給物件。 在偵測器中建立新的主題。 您可以使用 Interactable (可互動) 的主題設定檔，輕鬆地在所有可用的輸入互動狀態中新增視覺回饋。

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


Interactable 提供各種主題類型，包括著色器主題，該主題可讓您控制每個互動狀態的著色器屬性。

- [在 MRTK 文件中深入了解 Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

視覺化回饋的另一個重要組成要素是 MRTK 標準著色器。 透過 MRTK 標準著色器，您可以輕鬆地加入視覺回饋效果，例如暫留光源和鄰近光源。 由於 MRTK 標準著色器執行的計算比 Unity 標準著色器少很多，因此可讓您建立高效能的體驗。

建立新的材質，然後選取著色器的 [混合實境工具組] > [標準]。 或者，您可以挑選其中一個使用 MRTK 標準著色器的現有材質。

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [在 MRTK 文件中深入了解 MRTK 標準著色器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a>如何新增音訊回饋？
將 AudioSource 新增至物件。 然後，在公開輸入事件 (例如 Interactable.cs 或 PointerHandler.cs) 的指令碼中，將物件指派給事件，然後選取 [AudioSource.PlayOneShot()]。 您可以使用您的音訊片段，或從 MRTK 的音訊資產中選擇一個。

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a>如何使用 HoloLens 2 樣式的按鈕 Prefab？
MRTK 提供各類 HoloLens 2 命令介面 (OS) 樣式的按鈕。 其提供複雜的視覺回饋，例如，鄰近光源、壓縮方塊和按鈕表面上的漣波效果。

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

只要將其中一個 HoloLens 2 樣式的可點按按鈕拖放到您的場景中即可。 Prefab 會使用上方介紹的 Interactable.cs。 您可以在 Interactable 中使用公開的事件 例如 (OnClick()) 來觸發動作。

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [在 MRTK 文件中深入了解按鈕 Prefab](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a>如何讓物件跟著您移動？
將 RadialView.cs 指令碼指派給物件。 這是 Solver (解算器) 指令碼系列的一部分，可讓您在 3D 空間中實現各種物件類型的定位。 SolverHandler.cs 將會自動新增。
以下是使用 RadialView 設定達到 'lazy follow' 常駐標籤行為的範例，就像是 HoloLens 命令介面中的 [開始] 功能表。 您可以指定最小/最大距離和最小/最大檢視角度。 下列範例顯示物件在 0.4m 和 0.8m 範圍之間的 15° 檢視。 調整 Lerp 時間值，讓位置更新的速度更快或更慢。

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [在 MRTK 文件中深入了解 Solver](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a>如何讓物件面對您？
將 Billboard.cs 指令碼指派給物件。 無論您的位置為何，物件一律會面對您。 您可以指定樞紐軸選項。

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


準備好建立混合實境的絕佳體驗了嗎？ 請瀏覽下列頁面，並深入了解 MRTK 和混合實境。

## <a name="about-the-author"></a>關於作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>UX 設計者 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>另請參閱

* [混合實境工具組-Unity (MRTK) GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [開始使用 MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [HoloToolkit 至 MRTK 的移植指導方針](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
