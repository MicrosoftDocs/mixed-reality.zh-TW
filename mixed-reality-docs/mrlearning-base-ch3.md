---
title: MR 學習基本模組 - 動態內容放置和解算器
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 401c667ef80042da9182b7f4e065dfd6884cf061
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485694"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4.放置動態內容並使用解析器

在 HoloLens 2 中，當全像投影以直覺方式追蹤使用者，並且透過讓互動流暢及簡潔的方式放置在實體環境中時，全像投影就會變得栩栩如生。 在本教學課程中, 我們將探索使用 MRTK 的可用放置工具動態地放置全息影像的方式, 也稱為解析器, 以解決複雜的空間放置案例。 在 MRTK 中, 解析器是一種腳本和行為的系統, 可用來允許 UI 專案在場景中追蹤您、使用者或其他遊戲物件。 也可用來快速對齊特定位置，讓您的應用程式更具直覺性。 

## <a name="objectives"></a>目標

* 導入 MRTK 的解算器
* 使用解算器讓一組按鈕追蹤使用者
* 使用解算器讓遊戲物件跟隨追蹤的使用者手部

## <a name="instructions"></a>指示

### <a name="location-of-solvers-in-the-mrtk"></a>MRTK 中的解算器位置
 若要尋找您專案中可用的解算器，請查看 MRTK SDK 資料夾 (MixedRealityToolkit.SDK 資料夾)，然後在公用程式資料夾底下，您會看到解算器資料夾，如下圖所示。

![解算器](images/lesson3_chapter1_step1im.PNG)

>注意:在這一課, 我們只會探討 Orbital 規劃求解和 RadialView 規劃求解的實施。 若要深入了解 MRTK 中可用解算器的完整範圍，請瀏覽： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html

### <a name="use-a-solver-to-follow-the-user"></a>使用解算器追蹤使用者
本章的目標是要增強先前建立的按鈕集合, 使其遵循使用者的注視方向。 在舊版的 MRTK 和 HoloToolkit 中, 這稱為 tagalong 功能。

1. 選取前一課中的「按鈕集合」父系物件。

![Lesson3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. 在 [偵測器] 面板中, 按一下 [加入元件] 按鈕, 然後搜尋 orbital。 orbital 元件應該會隨即出現。 將其選取，並將 orbital 元件新增至「按鈕集合」遊戲物件。

![Lesson3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

>注意:新增元件時，您會發現系統在作為必要元件的偵測程式索引標籤中，加入orbital 指令碼和解算器處理常式指令碼。 

3. 若要設定按鈕集合以遵循使用者, 我們需要執行下列調整 (請參閱下圖):
- 在 Orbital 腳本中, 將 [方向類型] 下拉式清單設定為 [僅偏擺]。 這可讓集合在追蹤使用者時，只有一個物件的軸會旋轉。
- 將所有軸上的區域位移設為 0。 將全局位移設為 x = 0、y =-0.1 及 z = 0.6。 這會鎖定物件的移動，當使用者變更高度時，實體環境中的物件會維持固定高度，但同時仍會允許物件追蹤在環境中移動的使用者。 您可以調整這些值來達到各種不同的行為。
- 針對下列行為, 讓按鈕只會在使用者將其移到最遠的位置之後追蹤使用者的觀點, 您可以選取 [為全球位移使用角度逐步執行] 核取方塊 (注意:此標題可能會在某些在畫面上遭到截斷，如下圖中所示)。例如，若要讓物件只在每 90 度時追蹤使用者，則將步階的數目設為 4 (在範例中以朝向左側的綠色箭號標記)。 

![Lesson3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a>讓物件遵循追蹤的手

在本節中，我們將設定先前建立的立方體遊戲物件，以使用 RadialView 解算器來跟隨追蹤的使用者手部。

1. 選取 BaseScene 階層中的立方體物件。 按一下 [偵測器] 面板中的 [新增元件]。 

![Lesson3 Chapter3 Step1im](images/Lesson3_Chapter3_step1im.PNG)

2. 在搜尋方塊中輸入 RadialView, 然後選取 [RadialView] 元件, 將它加入至 cube。 解算器處理常式元件也會自動新增至立方體。

3. 將放射檢視變更為不要追蹤頭部，而是追蹤左手。 選取 [要參考的追蹤物件] 選項旁邊的下拉式功能表。 然後選取功能表中的 [向左接點]。

![Lesson3 Chapter3 Step3im](images/Lesson3_chapter3_step3im.PNG)

4. 選取手部後，您就可以選擇要讓立方體追蹤的手部位置。 在此範例中，我們要使用手腕。 在 [追蹤的接頭] 旁選取下拉式功能表, 然後選取 [手腕]。 

![Lesson3 Chapter3 Step4im](images/Lesson3_chapter3_step4im.PNG)

5. 將最大和最小距離設定為 0，讓立方體與使用者手腕之間沒有任何距離。 設定好之後，該立方體會完全配合手腕。 您也可以調整 [參考方向] 欄位來調整 cube 的導向行為, 例如, 如果您想要允許物件以使用者的手腕旋轉, 請將參考方向設定為 [追蹤物件的方向]。

![Lesson3 Chapter3 Step5im](images/Lesson3_chapter3_step5im.PNG)

## <a name="congratulations"></a>恭喜！
在本教學課程中, 您已瞭解如何使用 MRTK 的解析器, 讓 UI 直覺地跟隨使用者。 您也已了解如何將解算器連結到遊戲物件 (例如立方體)，以跟隨追蹤的使用者手部。 若要深入了解 MRTK 隨附的這些解算器和其他解算器，歡迎您瀏覽 [MRTK 解算器文件頁面](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)。

[下一課：5.  與 3D 物件互動](mrlearning-base-ch4.md)

