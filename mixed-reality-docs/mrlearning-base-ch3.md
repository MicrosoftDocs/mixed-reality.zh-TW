---
title: 入門教學課程 - 4。 放置動態內容並使用解算器
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 8a85ab560d0e6b36b589970b4d5b8a441ed2bbe2
ms.sourcegitcommit: 536fd45b48a70bbeca1454cef517ae007225e533
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80362035"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4.放置動態內容並使用解算器
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

在 HoloLens 2 中，當全像投影以直覺方式追蹤使用者，並且透過讓互動流暢及簡潔的方式放置在實體環境中時，全像投影就會變得栩栩如生。 在本教學課程中，我們會探索如何使用 MRTK 的可用放置工具 (也就是解算器) 來動態地放置全像投影，以解決複雜的空間放置案例。 在 MRTK 中，解算器是指令碼和行為的系統，用來允許 UI 元素在場景中追蹤您、使用者或其他遊戲物件。 也可用來快速對齊特定位置，讓您的應用程式更具直覺性。

## <a name="objectives"></a>目標

* 導入 MRTK 的解算器
* 使用解算器讓一組按鈕追蹤使用者
* 使用解算器讓遊戲物件跟隨追蹤的使用者手部

## <a name="location-of-solvers-in-the-mrtk"></a>MRTK 中的解算器位置

 MRTK 的解算器位於 MRTK SDK 資料夾中。 若要查看專案中的可用解算器，請在 [專案] 視窗中瀏覽至 [資產]   > [MixedRealityToolkit.SDK]   > [功能]   > [公用程式]   > [解算器]  ：

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

在本教學課程中，我們將檢閱「軌道解算器」和「光線檢視解算器」的實作。 若要深入了解 MRTK 中可用的完整解算器範圍，您可以瀏覽 [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[解算器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)指南。

## <a name="use-a-solver-to-follow-the-user"></a>使用解算器追蹤使用者
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

在本節中，您將增強上一個教學課程中建立的按鈕集合，使其遵循使用者的注視方向。 此外，您也會設定解算器，讓按鈕集合一律具有下列特性：

* 對使用者的閱讀方向進行平行旋轉，以自然地由左向右閱讀
* 位置低於使用者的水平注視方向，使其不會阻礙您稍後將在本教學課程中新增的其他物件
* 位置距離使用者大約半個手臂長，讓使用者可以輕鬆按下按鈕

為此，您將使用**軌道解算器**，將物件鎖定在特定位置，並從參考物件進行位移。

### <a name="1-add-the-orbital-solver"></a>1.新增軌道解算器

在 [階層] 視窗中選取 **ButtonCollection** 物件，然後在 [偵測器] 視窗中使用 [新增元件]  按鈕來將 **Orbital (指令碼)** 元件新增至 ButtonCollection 物件。

> [!NOTE]
> 當您加入解算器時 (在此案例中為 Orbital (指令碼) 元件)，Solver Handler (指令碼) 元件也會自動加入，因為解算器需要此元件。

### <a name="2-configure-the-orbital-solver"></a>2.設定軌道解算器

設定 **Solver Handler (指令碼)** 元件：

* 確認**追蹤的目標類型**已設定為 [標頭] 

設定 **Orbital (指令碼)** 元件：

* 確認**方向類型**已設定為 [跟隨追蹤的物件] 
* 將**局部位移**重設為 X = 0、Y = 0、Z = 0
* 將**全局位移**變更為 X = 0，Y = -0.4，Z = 0.3

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a>3.使用編輯器內模擬來測試軌道解算器

按下 [開始遊戲] 按鈕進入遊戲模式，並按住滑鼠右鍵來旋轉您的注視方向，同時注意下列事項：

* ButtonCollection 的變形位置現在是由解算器設定所驅動
* 不受解算器影響的立方體仍會在相同位置

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> 如果您沒有在場景視窗中看到相機光線，請確定您已啟用 [Gizmos] 功能表。 若要深入了解 Gizmos 功能表，以及如何使用其來最佳化場景檢視，您可以造訪 Unity 的 <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos 功能表</a>文件。
>
> 若要並排顯示場景和遊戲視窗 (如上圖所示)，只需將遊戲視窗拖曳至場景視窗的右邊即可。 若要深入了解如何自訂您的工作區，您可以造訪 Unity 的<a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">自訂您的工作區</a>文件。

## <a name="enabling-objects-to-follow-tracked-hands"></a>讓物件能夠跟隨追蹤的手部

在本節中，您將設定上一個教學課程中建立的立方體物件，使其跟隨使用者的追蹤手部，特別是右手腕。 此外，您也會設定解算器，讓立方體：

* 透過使用者的手部旋轉來變更其方向
* 放在使用者的手腕上

為此，您將使用**光線檢視解算器**，將物件保留在由參考物件所投射的檢視圓錐中。

### <a name="1-add-the-radial-view-solver"></a>1.新增光線檢視解算器

在 [階層] 視窗中，選取**立方體**子物件，然後在 [偵測器] 視窗中，使用 [新增元件]  按鈕來新增 **Radial View (指令碼)** 元件的立方體物件。

### <a name="2-configure-the-radial-view-solver"></a>2.設定光線檢視解算器

設定 **Solver Handler (指令碼)** 元件：

* 將**追蹤的目標類型**變更為**手部關節**
* 將**追蹤的手部**變更為**右手**
* 將**追蹤的手部關節**變更為**手腕**

設定 **Radial View (指令碼)** 元件：

* 將**參考方向**變更為**物件導向**，然後核取 [指向參考方向]  核取方塊
* 將**最小距離**和 **最大距離**變更為 0

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a>3.使用編輯器內模擬來測試光線檢視解算器

按下 [開始遊戲] 按鈕進入遊戲模式，然後按住空格鍵以顯示手部。 四處移動滑鼠游標來移動手部，然後按住滑鼠左鍵以旋轉手部：

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a>恭喜！

在此教學課程中，您已了解如何使用 MRTK 解算器讓 UI 直覺式地追蹤使用者。 您也已了解如何將解算器連結到物件 (例如立方體)，以跟隨追蹤的使用者手部。 若要深入了解 MRTK 隨附的這些解算器和其他解算器，您可以瀏覽 [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)的[解算器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)指南。

[下一個教學課程：5.與 3D 物件互動](mrlearning-base-ch4.md)
