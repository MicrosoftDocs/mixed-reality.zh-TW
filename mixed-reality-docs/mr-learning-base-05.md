---
title: 入門教學課程 - 5。 使用解算器建立動態內容
description: 本課程說明如何使用混合實境工具組 (MRTK) 來建立混合實境應用程式。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 1a5017d8bc18ef239db88ee62cb2b65c77b2ab6f
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376610"
---
# <a name="5-creating-dynamic-content-using-solvers"></a>5.使用解算器建立動態內容

## <a name="overview"></a>概觀

在本教學課程中，您將會探索如何使用 MRTK 的可用放置工具 (也就是解算器) 來動態地放置全像投影，以解決複雜的空間放置案例。 在 MRTK 中，解算器是指令碼和行為的系統，用來允許物件在場景中追蹤您、使用者或其他遊戲物件。 也可用來對齊特定位置，讓您的應用程式更具直覺性。

## <a name="objectives"></a>目標

* 導入 MRTK 的解算器
* 了解如何使用解算器將使用者引導至物件
* 了解如何使用解算器來重新放置物件

## <a name="location-of-solvers-in-the-mrtk"></a>MRTK 中的解算器位置

 MRTK 的解算器位於 MRTK SDK 資料夾中。 若要查看專案中的可用解算器，請在 [專案] 視窗中瀏覽至 [資產]  >  [MRTK]  >  [SDK]  >  [功能]  >  [公用程式] >  [解算器]：

![mr-learning-base](images/mr-learning-base/base-05-section1-step1-1.png)

在本教學課程中，我們將檢閱「方向性指標解算器」和「點選放置解算器」的實作。 若要深入了解 MRTK 中可用的完整解算器範圍，您可以參閱 [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[解算器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)指南。

> [!NOTE]
> 「方向性指標解算器」不會位於以上參考的 [解算器] 資料夾中，而是在 [資產] > [MRTK] > [SDK] > [實驗] > [功能] > [公用程式] 資料夾中，因為該解算器是實驗功能。

## <a name="using-the-directional-indicator-solver-to-direct-the-user-to-objects"></a>使用「方向性指標解算器」將使用者導向至物件

在 [專案] 視窗中，瀏覽至 [資產]  >  [MRTK.Tutorials.GettingStarted]  >  [Prefabs] 資料夾，按一下 [Chevron] Prefab 並將其拖曳至 [階層] 視窗，將其轉換 [位置] 設定為 X = 0、Y = 0、Z = 2，以將其放在 RoverExplorer 物件附近：

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-1.png)

> [!TIP]
> 如果您發現場景中的相機或任何其他圖示隱藏了物件，或造成混亂，您可以藉由<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">切換 Gizmos</a> 為關閉位置來隱藏這些物件，如上圖所示。 若要深入了解 Gizmos 功能表，以及如何使用其來最佳化場景檢視，您可以參閱 Unity 的 <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos 功能表</a>文件。

將新增的 Chevron 物件**指標**重新命名，然後在 [偵測器] 視窗中，使用 [新增元件] 按鈕來新增 **DirectionalIndicator** 和 **Directional Indicator Controller (指令碼)** 元件：

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-2.png)

> [!NOTE]
> 當您新增解算器時 (在此案例中為 DirectionalIndicator 元件)，Solver Handler 元件也會自動新增，因為解算器需要此元件。

> [!NOTE]
> Directional Indicator Controller (指令碼) 不是 MRTK 的一部分，但已包含在教學課程資產中。

設定 DirectionalIndicator 和 SolverHandler 元件，如下所示：

* 確認 **SolverHandler** 元件的 [追蹤目標類型] 設定為 [頭部]
* 藉由將其從 [階層] 視窗拖曳至 [無 (轉換)]  欄位，將 **RoverExplorer** 指派至 **DirectionalIndicator** 元件的**方向目標**
* 將 [檢視位移] 變更為 0.2

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-3.png)

按下 [開始遊戲] 按鈕進入遊戲模式，在向左或向右移動滑鼠時按住滑鼠右鍵來旋轉您的注視方向，同時注意下列事項：

* 當您查看 RoverExplorer 物件時，指標物件會出現並指向 RoverExplorer 物件

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-4.png)

> [!NOTE]
> 如果您沒有在場景視窗中看到相機光線，請確定您已啟用 [Gizmos] 功能表，如上圖中所示。

> [!TIP]
> 若要了解如何使用編輯器內的輸入模擬，您可以參考 [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[使用編輯器內的手動輸入模擬來測試場景](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)。

> [!TIP]
> 如果您的電腦有麥克風，您可以使用語音命令「切換診斷」，輕鬆地切換出現在 [遊戲] 視窗中的 [診斷] 面板作用中狀態。 或者，您也可以在 [MRTK 組態設定檔] > [診斷] > [啟用診斷系統] 中加以停用。 不過，通常建議您在開發期間讓診斷系統保持作用中狀態。

## <a name="using-the-tap-to-place-solver-to-reposition-objects"></a>使用「點選放置解算器」來調整物件的位置

在 [階層] 視窗中選取 [RoverExplorer] > **RoverAssembly** 物件，然後在 [偵測器] 視窗中使用 [新增元件] 按鈕來新增 **Tap To Place (指令碼)** 元件，並進行以下設定：

* 確認 **SolverHandler** 元件的 [追蹤目標類型] 設定為 [頭部]
* 勾選 [保持垂直方向] 核取方塊
* 從 [磁性表面]  >  [元素 0] 下拉式清單中，取消選取 [空間感知] 以外的所有選項

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-1.png)

> [!NOTE]
> [磁性表面] 設定會決定放置物件時，Tap To Place (指令碼) 元件可以偵測哪些物件。 藉由將設定變更為僅限 [空間感知]，Tap To Place (指令碼) 元件就只能將 Rover 放在名為「空間感知」的 Unity 層物件上，其預設為 HoloLens 所產生的空間感知網格。
>
>若要深入了解層級，您可以參閱 Unity 的<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">層</a>文件。

> [!TIP]
> 如果您想要在 HoloLens 上測試「點選放置」功能時查看「空間感知網格」，您可以暫時將空間網格觀察器的顯示選項設定為 [可見]。 如需有關如何變更顯示選項的提醒，您可以參閱[變更空間感知顯示選項](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)指示。

在 [階層] 視窗中，保持選取 RoverAssembly 物件，在 [偵測器] 視窗中，找出 [On Placing Started ()] 事件，然後按一下 **+** 圖示，以新增新的事件：

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-2.png)

設定事件，如下所示：

* 藉由從 [階層] 視窗將 **RoverAssembly** 物件拖曳至 [無 (物件)] 欄位，將其指派為 On Placing Started () 事件的接聽程式
* 從 [沒有函式] 下拉式清單中，選取 [TapToPlace]  >  [float SurfaceNormalOffset]，以在觸發事件時更新 SurfaceNormalOffset 屬性值
* 確認引數已設定為 **0**

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-3.png)

在 [階層] 視窗中，以滑鼠右鍵按一下空的位置，然後選取 [3D 物件]  >  [Cube]，以建立代表地面的暫存物件，並設定 [Transform] 元件，如下所示：

* **位置**：X = 0、Y = -1.65、Z = 6
* **旋轉**：X = 0、Y = 0、Z = 0
* **縮放比例**：X = 10、Y = 0.2、Z = 10

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-4.png)

在 [階層] 視窗中保持選取暫存 Cube，在 [偵測器] 視窗中使用 [層] 下拉式清單，將 Cube 的圖層設定變更為包含**空間感知**層：

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-5.png)

按下 [開始遊戲] 按鈕進入遊戲模式，然後在往下移動滑鼠時按住滑鼠右鍵，直到注視 RoverAssembly 物件為止：

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-6.png)

按一下滑鼠左鍵以啟動點選放置程序：

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-7.png)

在向左或向右移動滑鼠時按住滑鼠右鍵來旋轉您的注視方向，當您對放置位置感到滿意時，按一下滑鼠左鍵：

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-8.png)

在遊戲模式中完成功能的測試之後，以滑鼠右鍵按一下 Cube 物件，然後選取 [刪除] 將其從場景中移除：

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-9.png)

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已了解如何使用 MRTK 的方向性指標解算器，讓 UI 元素以直覺方式將使用者導向至物件。 您也了解如何使用點選放置解算器，輕易地調整物件的位置。

若要深入了解 MRTK 隨附的這些解算器和其他解算器，您可以參閱 [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)的[解算器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)指南。

[下一個教學課程：6.建立使用者介面](mr-learning-base-06.md)
