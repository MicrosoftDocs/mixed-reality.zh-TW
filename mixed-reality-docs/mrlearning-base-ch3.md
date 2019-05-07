---
title: MR 學習基底模組-動態內容的位置和解
description: 完成這個課程來了解如何在混合的實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合的實境，unity 教學課程 hololens
ms.openlocfilehash: b212812beeff54bb1f92ccbcc923ab9c301945b7
ms.sourcegitcommit: a32f673814a6cd6ff00f936f448885788b3b882c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "64929551"
---
# <a name="mr-learning-base-module---dynamic-content-placement-and-solvers"></a>MR 學習基底模組-動態內容的位置和解

全像投影結果出現在 HoloLens 2 時直接易懂的方式追蹤使用者，會放在實際環境中，可順暢且簡潔的互動的方式。 在第 3 課中，我們將探討如何動態地全像投影使用 MRTK 的可用位置工具，稱為 「 解。 」 它們稱為 「 解 」 來解決複雜的空間放置演算法的方式。 在 MRTK，解都是指令碼和行為，我們要能夠允許 UI 項目，請遵循您，使用者或其他遊戲場景中的物件所使用的系統。 它們也可用來快速貼齊至特定位置讓您的應用程式更具直覺性。 

## <a name="objectives"></a>目標

* 導入 MRTK 解
* 有一組按鈕使用解關注的使用者
* 有遊戲物件使用解依照使用者的追蹤實際操作

## <a name="instructions"></a>指示

### <a name="location-of-solvers-in-the-mrtk"></a>解 MRTK 中的位置
 若要在您的專案中尋找可用的解，請查看 MRTK SDK 資料夾 （MixedRealityToolkit.SDK 資料夾），然後在 [公用程式] 資料夾中會看到 [解] 資料夾中，如下圖所示。

![解](images/lesson3_chapter1_step1im.PNG)

>注意：在本課程中我們將只介紹"軌道"求解器和 「 RadialView"規劃求解的實作。 若要深入了解 MRTK 中可用之完整範圍的詳細，請瀏覽： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html

### <a name="use-a-solver-to-follow-the-user"></a>若要追蹤使用者使用規劃求解
本指南的目標是提升我們先前所建立，它會依照使用者的視線方向的按鈕集合。 前一版的 MRTK 和 HoloToolkit 的詳細資訊，這被指 「 taglong 」 功能。

1. 從上一課中，選取的按鈕集合的父物件。

![Lesson3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. 在 [偵測器] 面板中，按一下 [新增元件] 按鈕並搜尋"軌道。 」 軌道元件應該會出現。 請選取要新增的按鈕集合的遊戲物件的軌道的元件。

![Lesson3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

>注意：當您新增元件時，您會發現，系統會將新增軌道的指令碼，並規劃求解的處理常式指令碼偵測器索引標籤中，這是必要的元件。 

3. 若要設定按鈕的集合，以追蹤使用者，我們必須實作下列調整 （另請參閱下面的影像）：
- 在軌道的指令碼中，設定 [方向類型] 下拉式清單，以 「 繞只。 」 這可讓物件的該只有一個軸旋轉，它如下所示的使用者。
- 設定區域的位移為 0，所有軸上。 設定全局的位移為 x = 0，y =-0.1 和 z = 0.6。 因此，當使用者變更高度，固定的高度，在實際環境中，將會維持物件同時仍然允許它追蹤使用者，當使用者移動的環境相關，這會鎖定移動物件。 可調整這些值，以達到 wade 範圍的行為。
- 針對後續行為，藉此按鈕才需依照使用者的檢視之後使用者開啟他或她的頭夠遠，您可以選取的 「 使用角度逐步執行程式碼的世界位移 」 核取方塊 (請注意：這個項目可能會截斷某些在畫面上，在下圖中所顯示的原狀。）比方說，若要追蹤使用者只能每隔 90 度的物件，設定步驟的數目等於 4 （在範例中，左邊的綠色箭號標記）。 

![Lesson3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a>讓物件能夠遵循追蹤的指針

在本節中，我們將設定 cube 遊戲物件，使用先前建立依照使用者的追蹤使用 RadialView 規劃求解的手。

1. BaseScene 階層中選取的 cube 物件。 按一下 [偵測器] 面板中的 [新增元件]。 

![Lesson3 Chapter3 Step1im](images/Lesson3_Chapter3_step1im.PNG)

2. 在搜尋方塊中輸入 「 RadialView"，然後選取 RadialView 元件，將它加入至 cube。 求解器處理常式元件也會自動加入至 cube。

3. 變更未遵循標頭，但請遵循在左邊的星形檢視。 選取 「 追蹤物件以參考 」 選項旁的下拉式功能表。 然後"交給剩餘的聯合 」 從功能表中選取。

![Lesson3 Chapter3 Step3im](images/Lesson3_chapter3_step3im.PNG)

4. 一旦您選取手動聯結時，您可以選擇您想要的 cube，就可以遵循的左手邊的哪個部分。 針對此範例中，我們要使用 手腕。 選項旁 」 追蹤的手動接合 」 選取下拉式功能表中，然後選取 手腕也一樣。 

![Lesson3 Chapter3 Step4im](images/Lesson3_chapter3_step4im.PNG)

5. 設定為 0，讓 cube 不會有任何它與使用者的手腕之間的距離的最大和最小距離。 設定之後，該 cube 會完全配合手腕。 此外，您也可以調整 「 參考方向 」 欄位，來調整此 cube 有何導向 （例如，如果您想要允許使用使用者的手腕旋轉，請將 「 Box-orient 與追蹤物件 」 參考方向的物件） 的行為

![Lesson3 Chapter3 Step5im](images/Lesson3_chapter3_step5im.PNG)

### <a name="congratulations"></a>恭喜您
恭喜您！ 在這一課，您已了解如何使用 MRTK 解具有直覺的方式追蹤使用者的 UI。 您也學到如何附加規劃求解遊戲物件 (例如 cube)，以依照使用者的追蹤實際操作。 若要深入了解這些和其他解隨附 MRTK，歡迎您瀏覽[MRTK 解文件頁面](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)。

[下一課：3D 物件互動](mrlearning-base-ch4.md)

