---
title: 使用者入門教學課程-4。 放置動態內容並使用解析器
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 5463f363291790fd5e5d76ffa322a61ca7bf8e31
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553866"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4. 放置動態內容並使用解析器
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

在 HoloLens 2 中，當您以直覺方式追蹤使用者，並將其放在實體環境中，讓互動順暢且簡潔時，就能開始使用全息。 在本教學課程中，我們會探索如何使用 MRTK 的可用位置工具（稱為解析器）來動態地放置全息影像，以解決複雜的空間放置案例。 在 MRTK 中，解析器是一種腳本和行為的系統，可用來允許 UI 專案在場景中追蹤您、使用者或其他遊戲物件。 也可用來快速對齊特定位置，讓您的應用程式更具直覺性。

## <a name="objectives"></a>目標

* 引進 MRTK 的解析器
* 使用解析器讓按鈕集合跟隨使用者
* 使用解析器讓遊戲物件遵循使用者的追蹤手

## <a name="location-of-solvers-in-the-mrtk"></a>MRTK 中的解析器位置

 MRTK 的解析器位於 MRTK SDK 資料夾中。 若要查看專案中的可用解析器，請在 [專案] 視窗中，流覽至 [**資產**] [ > **MixedRealityToolkit** ] [ > **功能**] > [**公用程式**] > **解析器**：

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

在本教學課程中，我們將探討 Orbital 規劃求解和星形視圖規劃求解的執行。 若要深入瞭解 MRTK 中提供的完整解析器，您可以流覽[MRTK 檔入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[解析器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)指南。

## <a name="use-a-solver-to-follow-the-user"></a>使用規劃人員追蹤使用者
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

在本節中，您將增強在上一個教學課程中建立的按鈕集合，使其遵循使用者的注視方向。 此外，您也會設定 [規劃求解]，讓按鈕集合一律為：

* 對使用者的閱讀方向進行的平行旋轉，以自然的向右閱讀
* 位置稍微低於使用者水準外觀，因此不會阻礙您稍後將在本教學課程中新增的其他物件。
* 接近使用者的一半 arm 長度，因此可以輕鬆按下按鈕

為此，您將使用**Orbital 的規劃求解**，將物件從參考的物件鎖定到指定的位置和位移。

### <a name="1-add-the-orbital-solver"></a>1. 加入 Orbital 規劃求解

在 [階層] 視窗中，選取 [ **ButtonCollection** ] 物件，然後在 [偵測器] 視窗中，使用 [**加入元件**] 按鈕將**Orbital （腳本）** 元件新增至 ButtonCollection 物件。

> [!NOTE]
> 當您加入規劃求解時（在此案例中為 Orbital （Script）元件），會自動加入「規劃求解處理常式」（腳本）元件，因為它是規劃求解所需。

### <a name="2-configure-the-orbital-solver"></a>2. 設定 Orbital 規劃求解

設定 [**規劃求解處理常式（腳本）** ] 元件：

* 確認 [**追蹤的目標型別**] 設定為 [ **Head** ]

設定**Orbital （腳本）** 元件：

* 確認 [**方向類型**] 設定為 [**跟隨追蹤的物件**]
* 將**區域位移**重設為 X = 0、Y = 0、Z = 0
* 將**世界位移**變更為 X = 0，Y =-0.4，Z = 0。3

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a>3. 使用編輯器內模擬來測試 Orbital 規劃求解

按下 [播放] 按鈕進入遊戲模式，然後按住滑鼠右鍵以旋轉您的注視方向，並注意下列事項：

* ButtonCollection 的轉換位置現在是由 [規劃求解] 設定所驅動
* 不受規劃求解影響的 Cube 會保留在相同的位置

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> 如果您沒有在場景視窗中看到相機光線，請確定已啟用 [Gizmos] 功能表。 若要深入瞭解 [Gizmos] 功能表，以及如何使用它來優化場景視圖，您可以造訪 Unity 的 [ <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos] 功能表</a>檔。
>
> 若要並排顯示場景和遊戲視窗（如上圖所示），只需將遊戲視窗拖曳至場景視窗的右邊。 若要深入瞭解如何自訂您的工作區，您可以造訪 Unity 的<a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">自訂工作區</a>檔。

## <a name="enabling-objects-to-follow-tracked-hands"></a>讓物件遵循追蹤的手

在本節中，您將設定您在上一個教學課程中建立的 Cube 物件，使其遵循使用者的追蹤手，特別是右邊的手腕。 此外，您也會將此規劃求解設定為 cube：

* 變更其與使用者的旋轉方向
* 放在使用者的手腕上

為此，您將使用星形**視圖規劃求解**，將物件保留在視圖中，並由參考的物件轉換。

### <a name="1-add-the-radial-view-solver"></a>1. 加入星形視圖規劃求解

在 [階層] 視窗中，選取**Cube**物件，然後在 [偵測器] 視窗中，使用 [**加入元件**] 按鈕來加入星形**視圖（腳本）** 元件 Cube 物件。

### <a name="2-configure-the-radial-view-solver"></a>2. 設定放射狀視圖的規劃求解

設定 [**規劃求解處理常式（腳本）** ] 元件：

* 將**追蹤的目標型別**變更為**手動聯合**
* 將**追蹤的 Handness**變更為**右方**
* 將**追蹤的接頭**變更為**手腕**

設定**放射狀視圖（腳本）** 元件：

* 將 [**參考方向**] 變更為 [**物件導向**]，然後選取 [**朝向參考方向**] 核取方塊
* 將 [**最小距離**] 和 [**最大距離**] 變更為0

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a>3. 使用編輯器內模擬來測試星形視圖規劃

按下 [播放] 按鈕進入遊戲模式，然後按住空格鍵以顯示手。 將滑鼠游標移到周圍以移動手，然後按住滑鼠左鍵以旋轉手：

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a>恭喜

在本教學課程中，您已瞭解如何使用 MRTK 的解析器，讓 UI 直覺地跟隨使用者。 您也已瞭解如何將規劃求解附加至物件（例如 cube），以遵循使用者的追蹤手。 若要深入瞭解 MRTK 隨附的這些和其他解析器，您可以流覽[MRTK 檔入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[解析器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)指南。

[下一個教學課程： 5. 與3D 物件互動](mrlearning-base-ch4.md)
