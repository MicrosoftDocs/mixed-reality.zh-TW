---
title: 使用者入門教學課程-4。 放置動態內容並使用解析器
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: ade7a839e03a306332bf18f1db49805f59c71429
ms.sourcegitcommit: f2b7c6381006fab6d0472fcaa680ff7fb79954d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2019
ms.locfileid: "74064262"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4. 放置動態內容並使用解析器

在 HoloLens 2 中，當您以直覺方式追蹤使用者，並將其放在實體環境中，讓互動順暢且簡潔時，就能開始使用全息。 在本教學課程中，我們會探索如何使用 MRTK 的可用位置工具（稱為解析器）來動態地放置全息影像，以解決複雜的空間放置案例。 在 MRTK 中，解析器是一種腳本和行為的系統，可用來允許 UI 專案在場景中追蹤您、使用者或其他遊戲物件。 也可用來快速對齊特定位置，讓您的應用程式更具直覺性。

## <a name="objectives"></a>目標

* 導入 MRTK 的解算器
* 使用解算器讓一組按鈕追蹤使用者
* 使用解算器讓遊戲物件跟隨追蹤的使用者手部

## <a name="instructions"></a>指示

### <a name="location-of-solvers-in-the-mrtk"></a>MRTK 中的解算器位置

 若要在您的專案中尋找可用的解析器，請查看 MRTK SDK 資料夾（MixedRealityToolkit. SDK 資料夾）。 在 [公用程式] 資料夾底下，您會看到 [解析器] 資料夾，如下圖所示。

![解算器](images/lesson3_chapter1_step1im.PNG)

>[!NOTE]
>在這一課，我們只會探討 Orbital 規劃求解和 RadialView 規劃求解的執行。 若要深入瞭解 MRTK 中提供的完整解析器範圍，請造訪： [https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

### <a name="use-a-solver-to-follow-the-user"></a>使用解算器追蹤使用者

本章的目標是要增強先前建立的按鈕集合，使其遵循使用者的注視方向。 在先前版本的 MRTK 和 HoloToolkit 中，這稱為 tagalong 功能。

1. 選取前一課中的「按鈕集合」父系物件。

    ![Lesson3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. 在 [偵測器] 面板中，按一下 [加入元件] 按鈕，然後搜尋 orbital。 應該會出現 Orbital 元件。 選取它以將 Orbital 元件新增至按鈕集合遊戲物件。

    ![Lesson3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

    >[!NOTE]
    >當您新增 Orbital 元件時，您會注意到系統也會新增 SolverHandler 元件，這是必要的元件。

3. 若要設定按鈕集合以遵循使用者，我們需要執行下列調整（請參閱下圖）：
    * 在 Orbital 腳本中，將 [方向類型] 下拉式清單設定為 [僅偏擺]。 這可讓集合在追蹤使用者時，只有一個物件的軸會旋轉。
    * 將所有軸上的區域位移設為 0。 將 [世界位移] 設定為 x = 0、y =-0.1 和 z = 0.6。 這會鎖定物件的移動，因此當使用者變更高度時，物件在實體環境中會維持固定的高度，而當使用者移至環境時，仍允許它追蹤使用者。 您可以調整這些值來達到各種不同的行為。
    * 針對下列行為，讓按鈕只會在使用者將其標題設為最遠之後追蹤使用者的觀點，您可以選取 [為全球位移使用角度逐步執行] 核取方塊（注意：在某些畫面上，此標題可能會被截斷，如下圖所示）。例如，若要讓物件只在每隔90度之後追蹤使用者，請將步驟數設定為等於4（以下列範例中的綠色箭號標示）。

    ![Lesson3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a>讓物件遵循追蹤的手

在本節中，我們將設定先前建立的 Cube 遊戲物件，以遵循使用 RadialView 求解的使用者追蹤手。

1. 選取 BaseScene 階層中的 Cube 物件。 按一下 [偵測器] 面板中的 [新增元件]。 在搜尋方塊中輸入 RadialView，然後選取 [RadialView] 元件，將它加入至 cube。 SolverHandler 元件也會自動加入至 cube。

    ![mrlearning-base-ch3-3-step3 .png](images/mrlearning-base-ch3-3-step1.png)

2. 若要將 RadialView 變更為追蹤，而不是標頭，請選取 [追蹤的目標型別] 選項旁邊的下拉式功能表，然後從功能表中選取 [手形聯合]。

    ![mrlearning-base-ch3-3-step2 .png](images/mrlearning-base-ch3-3-step2a.png)

    您現在會看到兩個新選項： [已追蹤] Handness 類型和 [已追蹤]。 在此範例中，您會讓 RadialView 遵循左側的手腕，如下圖所示。

    ![mrlearning-base-ch3-3-step2b .png](images/mrlearning-base-ch3-3-step2b.png)

3. 將星形視圖的最大和最小距離設定為0，讓 cube 與使用者手腕之間不會有任何距離。 設定好之後，該立方體會完全配合手腕。 您也可以調整 [參考方向] 欄位來調整 cube 的導向行為，例如，如果您想要允許物件透過將參考方向設定為物件導向來旋轉使用者的手腕。

    ![mrlearning-base-ch3-3-step3 .png](images/mrlearning-base-ch3-3-step3.png)

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已瞭解如何使用 MRTK 的解析器，讓 UI 直覺地跟隨使用者。 您也已了解如何將解算器連結到遊戲物件 (例如立方體)，以跟隨追蹤的使用者手部。 若要深入了解 MRTK 隨附的這些解算器和其他解算器，歡迎您瀏覽 [MRTK 解算器文件頁面](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)。

[下一課： 5. 與3D 物件互動](mrlearning-base-ch4.md)
