---
title: 入門教學課程 - 4。 將物件置放在場景中
description: 本課程說明如何使用混合實境工具組 (MRTK) 來建立混合實境應用程式。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 71990db23b5154de916f0eda86a978885ab53547
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376630"
---
# <a name="4-positioning-objects-in-the-scene"></a>4.將物件置放在場景中

## <a name="overview"></a>概觀

在本教學課程中，您將匯入教學課程資產，並將所提供的物件放置在場景中。

## <a name="objectives"></a>目標

* 了解如何將物件放置在場景中
* 了解如何使用 MRTK 的網格物件集合功能

## <a name="importing-the-tutorial-assets"></a>匯入教學課程資產

下載並匯入下列 Unity 自訂套件：

* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)

匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：

![mr-learning-base](images/mr-learning-base/base-04-section1-step1-1.png)

> [!TIP]
> 如需有關如何匯入 Unity 自訂套件的提示，您可以參閱[匯入 MRTK](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) 的指示。

## <a name="creating-the-parent-object"></a>建立父物件

在 [階層] 視窗中，以滑鼠右鍵按一下空的位置，然後選取 [建立空物件]，將空的物件新增至您的場景：

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> 若要並排顯示場景和遊戲視窗 (如上圖所示)，將遊戲視窗拖曳至場景視窗的右邊即可。 若要深入了解如何自訂您的工作區，您可以參閱 Unity 的<a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">自訂您的工作區</a>文件。

以滑鼠右鍵按一下新建立的物件並選取 [重新命名]，然後將名稱變更為 **RoverExplorer**：

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-2.png)

在仍選取 RoverExplorer 物件的情況下，在 [偵測器] 視窗中設定**變形**元件，如下所示：

* **位置**：X = 0、Y = -0.6、Z = 2
* **旋轉**：X = 0、Y = 0、Z = 0
* **縮放**：X = 1、Y = 1、Z = 1

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-3.png)

> [!NOTE]
> 相機代表使用者頭部，位於原點：X = 0、Y = 0、Z = 0。 一般情況下，Unity 中的 1 個單位大約是真實世界的 1 公尺。 但有例外狀況，例如，當物件是所縮放物件的子系時。 在上述案例中，RoverExplorer 會放置在使用者頭部前方 2 公尺及下方 0.6 公尺處。

## <a name="adding-the-tutorial-prefabs"></a>新增教學課程 Prefab

在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.GettingStarted] > [Prefabs] 資料夾。

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-1.png)

> [!TIP]
> <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">Prefab</a> 是預先設定且儲存為 Unity 資產的 GameObject，可以在整個專案中重複使用。

在 [專案] 視窗中，按一下**資料表** Prefab 並拖曳至 **RoverExplorer** 物件上，使其成為 RoverExplorer 物件的子系，然後在 [偵測器] 視窗中設定**變形**元件，如下所示：

* **位置**：X = 0、Y = -0.005、Z = 0
* **旋轉**：X = 0、Y = 0、Z = 0
* **縮放**：X = 1.2、Y = 0.01、Z = 1.2

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> 若要顯示您的場景 (如上圖所示)，請使用場景視窗右上角的<a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">場景 Gizmo</a>，將檢視角度調整為以 Z 軸為前方，並按兩下 MixedRealityPlayspace 物件將焦點放在相機上，然後視需要進行放大。

在 [專案] 視窗中，按一下 **[RoverAssembly]** Prefab 並拖曳至 **RoverExplorer** 物件，使其成為 RoverExplorer 物件的子系，然後在 [偵測器] 視窗中設定**變形**元件，如下所示：

* **位置**：X = -0.1、Y = 0、Z = 0
* **旋轉**：X = 0、Y = -135、Z = 0
* **縮放**：X = 1、Y = 1、Z = 1

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a>組織集合中的 3D 物件

在 [階層] 視窗中，以滑鼠右鍵按一下 **RoverExplorer** 物件並選取 [建立空物件]，將空白物件新增為 RoverExplorer 的子系，然後將物件命名為 **RoverParts**，並設定**變形**元件，如下所示：

* **位置**：X = 0、Y = 0.06、Z = 0
* **旋轉**：X = 0、Y = 90、Z = 0
* **縮放**：X = 1、Y = 1、Z = 1

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-1.png)

在 [階層] 視窗中，選取所有 RoverExplorer > RoverAssembly > RoverModel > **Parts** 子物件，以滑鼠右鍵按一下這些子物件，然後選取 [複製]，為每個零件建立複本：

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-2.png)

> [!TIP]
> 若要選取多個連續的物件，請按住 SHIFT 鍵，同時使用滑鼠來選取第一個和最後一個物件。

繼續選取新複製的 Parts 子物件，按一下這些物件並拖曳至 **RoverParts** 物件，使其成為 RoverParts 物件的子物件：

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-3.png)

為了讓您更輕鬆地使用場景，請在 [階層] 視窗中，按一下物件左邊的**眼睛**圖示，以將 **RoverExplorer** 物件的**場景可見度**切換為關閉。 這會在場景視窗中隱藏物件，而不會變更其遊戲內的可見度：

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-4.png)

> [!TIP]
> 若要深入了解場景可見度的控制項，以及如何使用其來最佳化場景檢視和工作流程，您可以參閱 Unity 的<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">場景可見度</a>文件。

在 [階層] 視窗中，將附加的 **(1)** 取代為 **_Part**，以清除 RoverParts 子物件的名稱：

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-5.png)

在 [階層] 視窗中，選取 **RoverParts** 物件，然後在 [偵測器] 視窗中，按一下 [新增元件] 按鈕，搜尋並選取 [GridObjectCollection]，將 GridObjectCollection 元件新增至 RoverParts 物件：

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-6.png)

設定 **GridObjectCollection** 元件值，如下所示：

* **排序類型**：字母順序
* **版面配置**：水平
* **儲存格寬度**：0.25
* **與父系的距離**：0.38

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-7.png)

然後按一下 [更新集合] 按鈕，以更新 RoverParts 子物件的位置：

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-8.png)

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已了解如何將物件放置在場景中與使用者相對的位置，並使用 MRTK 的網格物件集合功能來組織集合中的物件。

[下一個教學課程：5.使用解析器建立動態內容](mr-learning-base-05.md)
