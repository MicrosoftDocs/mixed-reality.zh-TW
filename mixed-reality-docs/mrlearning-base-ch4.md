---
title: MR 學習基本模組 - 3D 物件互動
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 45e772de0825fe2161f880a165d6c75c755b849e
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730911"
---
# <a name="mr-learning-base-module---3d-object-interaction"></a>MR 學習基本模組 - 3D 物件互動

在本課程中，我們將探討基本的 3D 內容和使用者體驗。 我們將了解如何將 3D 物件組織為集合的一部分、了解基本操作的週框方塊、了解遠近互動，以及使用手部追蹤了解觸控和抓取手勢。 

## <a name="objectives"></a>目標

* 了解如何使用 MRTK 的格線物件集合來組織 3D 內容
* 實作週框方塊
* 設定 3D 物件以進行基本操作 (移動、旋轉和縮放)
* 探索遠近互動
* 了解其他手部追蹤手勢，例如抓取和觸控

## <a name="instructions"></a>指示

### <a name="organizing-3d-objects-in-a-collection"></a>組織集合中的 3D 物件

1. 以滑鼠右鍵按一下您的階層，然後選取 [Create Empty] \(建立空白項目\)。 這會建立空的遊戲物件。 將它重新命名為 "3DObjectCollection"。 這是我們放置所有 3D 物件的地方。 確定集合的位置設定為 x = 0、y = 0 且 z = 0。

![Lesson4 Chapter1 Step1im](images/Lesson4_Chapter1_step1im.PNG)

2. 匯入 BaseModule 資產使用相同的指示匯入[第 1 課](mrlearning-base-ch1.md)中所述的自訂套件。 BaseModule 資產包括將在本教學課程中使用的 3D 模組和其他實用的指令碼。 BaseModule Unity 套件可以在這裡找到：<https://github.com/Microsoft/MixedRealityLearning/releases/tag/V1.1>

3. 咖啡杯預製物件可以透過旁邊的藍色立方體辨識。 請勿選取包含藍色立方體和小白紙的咖啡杯 (表示原始的 3D 模型而不是預製物件。) 

![Lesson4 Chapter1 Noteaim](images/Lesson4_chapter1_noteaim.PNG)

4. 將您選擇的咖啡杯預製物件拖曳至步驟 1 中的 "3DObjectCollection" 遊戲物件。 咖啡杯現在是該集合的子系。

![Lesson4 Chapter1 Step4ima](images/Lesson4_chapter1_step4ima.PNG)

5. 接下來，我們將新增更多的 3D 物件至場景。 以下是我們將在此範例中新增的物件清單。 在新增物件時，您可能會發現它們以各種大小顯示在場景中。 在 [Inspector] \(屬性編輯器\) 面板中的轉換設定下調整每個 3D 模型的比例。 以下的物件列出了此範例的建議調整。 在 [Project] \(專案\) 面板的搜尋方塊中搜尋這些字，然後將 3D 物件預製物件拖曳至類似於上一步的 "3DObjectCollection" 物件中。 您可以在 Assets>BaseModuleAssets>Base Module Prefabs 中找到這些預製物件集合
- 搜尋 "TheModule_BaseModuleIncomplete"。 拖曳至場景。 將比例設置為 x = 0.03、y = 0.03、z = 0.03。 
- 搜尋 "Octa_BaseModuleIncomplete"。 拖曳至場景。 將比例設置為 x = 0.13、 y = 0.13、z =0.13。
- 搜尋 "EarthCore_BaseModuleIncomplete"。 拖曳至場景。 將比例設置為 x = 50.0、y = 50.0、z = 50.0。
- 搜尋 "Cheese_BaseModuleIncomplete"。 拖曳至場景。 將比例設置為 x = 0.05、y = 0.05、z = 0.05。
- 搜尋 "Model_Platonic_BaseModuleIncomplete"。 拖曳至場景。 將比例設置為 x = 0.13、y = 0.13、z = 0.13。
- 搜尋 "CoffeeCup_BaseModuleIncomplete"。 拖曳至場景。

![Lesson4 Chapter1 Step5im](images/Lesson4_Chapter1_step5im.PNG)

6. 在場景中新增 3 個立方體。 以滑鼠右鍵按一下 [3DObjectCollection] 物件，選取 [3D Object] \(3D 物件\)，然後選取 [Cube] \(立方體\)。 將比例設置為 x = 0.14、y = 0.14 且 z = 0.14。 另外重複此步驟 2 次，以建立總計 3 個立方體。 或者，您可以複製立方體兩次，總計 3 個立方體。 您也可以選擇使用 Assets>BaseModuleAssets>Base Module Prefabs 中三個已備妥的立方體預製物件，並選取 GreenCube_BaseModuleIncomplete、BlueCube_BaseModuleIncomplete 和 OrangeCube_BaseModuleIncomplete。

![Lesson4 Chapter1 Step6im](images/Lesson4_Chapter1_step6im.PNG)

7. 使用 MRTK 的方格物件集合中的[第 2 課](mrlearning-base-ch2.md)中所述的程序，組織您的物件集合以形成方格。 請參閱下圖，查看在 3x3 方格中設定物件的範例。

![Lesson4 Chapter1 Notebim](images/Lesson4_chapter1_notebim.PNG)

>注意：您可能會注意到某些物件偏離中心，例如上圖中的物件。 這是因為預製物件或物件可能具有未對齊的子物件。 隨意對物件位置或子物件位置進行必要的調整，以實現完善對齊的方格。


### <a name="manipulating-3d-objects"></a>操作 3D 物件
1. 新增可操作立方體的功能。 若要新增操縱 3D 物件的功能，您必須執行下列動作：
-   選取要在階層中操作的 3D 物件 (在此範例中為您的其中一個立方體)。
-   按一下 [Add Component] \(新增元件\)。 
-   搜尋 "manipulation"。
-   選取 [Manipulation Handler] \(操作處理常式\)。
-   針對 "3DObjectCollection" 物件下的所有 3D 物件重複，而不是 "3DObjectCollection" 本身。
-   請確定所有的 3D 物件都具有 Collider 或 Box Collider ([Add Component] > [Box Collider]) \([新增元件] > [方塊碰撞器]\)。

![Lesson4 Chapter2 Step1im](images/Lesson4_chapter2_step1im.PNG)

>操作處理常式是一個元件，允許您調整物件在操作時的行為。 這包括在特定軸上旋轉、縮放、移動和約束移動。 

2. 限制一個立方體，使其只能縮放。 在 "3DObjectCollection" 物件中選取一個立方體。 在 [Inspector] 面板中，在 [Two Handed Manipulation Type] \(雙手操作類型\) 旁邊，按一下下拉功能表並選取 [Scale] \(縮放\)。 這使得使用者只能變更立方體的大小。

![Lesson4 Chapter2 Step2im](images/Lesson4_Chapter2_step2im.PNG)

3. 變更每個立方體的色彩，以便我們可以區分它們。 
-   移至 [Project] 面板並向下捲動，直到您看到 "MixedRealityToolkit.SDK"，然後選取它。
-   選取 [Standard Assets] \(標準資產\) 資料夾。
-   按一下 [Materials] \(材質\) 資料夾。
-   將不同的材質拖曳到每個立方體上。 

>注意：您可以為立方體選擇任何色彩。 針對我們的範例，我們將使用 "glowingcyan"、"glowingorange" 和 "green"。 請隨意試驗不同的色彩。 若要將色彩新增到立方體，請按一下要變更其色彩的立方體，然後將該材質拖曳到該立方體之 [Inspector] 面板中的網格渲染器材質欄位。 

![Lesson4 Chapter2 Step3im](images/Lesson4_Chapter2_step3im.PNG)

4. 在 “3DObjectCollection” 物件中選取另一個立方體，並讓其移動受限於到頂部的固定距離。 若要這樣做，在 [Constraint On Movement] \(約束移動\)的右側，按一下下拉式功能表，然後選取 [Fix Distance From Head] \(固定頂部距離\)。 這使得使用者只能在其視野內移動立方體。 

![Lesson4 Chapter2 Step4im](images/Lesson4_chapter2_step4im.PNG)

接下來幾個步驟的目標：我們將啟用抓取，並與 3D 物件互動。 我們將套用不同的操作設定 

5. 選取起司物件，然後在 [Inspector] 面板中按一下 [Add Component]。 

6. 在搜尋方塊中搜尋 "Near Interaction Grabbable" \(可近距離抓取\) 並選取指令碼。 此元件可讓使用者透過手部追蹤伸出並抓住物體。 除非取消選取 [Allow Far Manipulation] \(允許遠距操作\) 核取方塊 (在下列影像中以綠色圓圈表示)，否則也允許從遠處操作物件。

![Lesson4 Chapter2 Step6im](images/Lesson4_Chapter2_step6im.PNG)

7. 透過在這些物件上重複步驟 5 和 6，將 "Near Interaction Grabbable" 新增至八邊形物件、柏拉圖立體物件、地核、登月艙和咖啡杯中。

8. 從八邊形物件中移除遠距操作的能力。 若要這樣做，請在階層中選取 [Octa] \(八邊形\)，然後取消選取 [Allow Far Manipulation] 核取方塊 (以綠色圓圈標記)。 這使得使用者只能使用手部追蹤直接與八邊形互動。

>注意：如需操作處理常式元件及其相關設定的完整文件，請參閱 [MRTK 文件](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)。

9. 請確定已將 [Near Interaction Grabbable] 元件新增至地核、登月艙和咖啡杯中 (請參閱步驟 7)。

10. 針對登月艙，請變更 [Manipulation Handler] 設定，使其圍繞物件的中心旋轉，以進行近距離和遠距離互動，如下圖所示。

![Lesson4 Chapter2 Step10im](images/Lesson4_chapter2_step10im.PNG)

11.針對地核，將釋放行為變更為 "nothing" \(無\)。 這使得地核一旦從使用者掌握中釋放時，它不會持續移動。 

![Lesson4 Chapter2 Step11im](images/Lesson4_Chapter2_step11im.PNG)

> 注意：此設定對於建立可以投擲的球等場景非常有用。 保留速度和角速度，使得球一旦被釋放，它將繼續以其釋放的速度移動，類似於實體球的行為方式。

### <a name="adding-bounding-boxes"></a>新增週框方塊
週框方塊讓您更輕鬆且更直覺地以一隻手操作物件，可用於直接操作 (近距互動) 和射線操作 (遠距互動)。週框方塊提供「控點」，可以抓取以沿著特定座標軸縮放和旋轉物件。
>注意：在向物件新增週框方塊之前，首先需要在物件上有碰撞器 (例如，方塊碰撞器)。如同我們先前在本課中所做的那樣。 可以透過選取物件來新增碰撞器，並在物件的 [Inspector] 面板中選取 [Add Component] > [Box Collider] \([新增元件] > [方塊碰撞器]\)。
>

1. 如果方塊碰撞器不存在的話，則將其新增至地核物件 (如果使用 [Base Module Assets] 資料夾中提供的預製物件，則根據提供的指示不需要方塊碰撞器和設定。)在地核的情況下，我們需要將方塊碰撞器新增至地核下的 "node_id30" 物件，如下圖所示。 選取 node_id30 並在物件的 [Inspector] 索引標籤上，按一下 [Add Component]，然後搜尋 "box collider"。 

![Lesson4 Chapter3 Step1im](images/Lesson4_Chapter3_step1im.PNG)

![Lesson4 Chapter3 Step2im](images/Lesson4_chapter3_step2im.PNG)

> 注意：請確定您將方塊碰撞器視覺化，使其不會太大或太小。 它的大小應與它周圍的物件大致相同 (在本例中為地核)。 藉由選取方塊碰撞器中的 [Edit Collider] \(編輯碰撞器\) 選項，視需要調整方塊碰撞器。 您可以變更 x、y 和 z 值，也可以在編輯器場景視窗中拖曳週框方塊處理常式。 

![Lesson4 Chapter3 Noteim](images/Lesson4_Chapter3_noteim.PNG)

2. 將週框方塊新增至地核的 "node_id30" 物件。 若要這樣做，請從 "3DObjectCollection" 中選取 "node_id30" 物件。 在 [Inspector] 索引標籤中，按一下 [Add Component]，然後搜尋 "bounding box"。 請確定週框方塊、方塊碰撞器和操作指令碼 (Manipulation Handler、Near Interaction Grabbable) 都在同一個遊戲物件上。

3.  在週框方塊的 [Behavior] \(行為\) 區段中，從 [Activation] \(啟用\) 下拉式清單中選取 [Activate On Start] \(啟動時啟用\)。 若要檢閱有關各種啟用選項和其他週框方塊選項的其他詳細資料，請參閱 [MRTK 的週框方塊文件](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>) \(英文\)

   

   *在接下來的幾個步驟中，我們還將藉由調整預設方塊材質、抓取方塊時的材質，以及控點 (角和側邊控點) 的視覺效果來變更週框方塊的外觀。MRTK 包含幾個用於自訂週框方塊的選項。*

4. 在 [Project] 面板中，搜尋 "boundingbox"，您將在搜尋結果中看到由藍色球體表示的材質清單，如下圖所示。 

5. 將 "boundingbox" 材質拖曳至週框方塊元件上的方塊材質位置中。 同時抓取 "boundingboxgrabbed" 材質，並將其放在週框方塊元件上的方塊抓取材質位置中。

6. 將 "MRTK_BoundingBox_ScaleWidget" 材質拖曳至週框方塊元件上的縮放控點預製物件位置中。 

7. 將 "MRTK_BoundingBox_RotateWidget" 材質拖曳至週框方塊元件上的旋轉控點位置中。

![Lesson4 Chapter3 Step4 7Im](images/Lesson4_chapter3_step4-7im.PNG)

8. 請確定週框方塊的目標是正確的物件。 在週框方塊元件中，有 [Target Object] \(目標物件\)和 [Bounds Override] \(範圍覆寫\) 指令碼。 請務必將具有週框方塊的物件拖曳至這兩個位置中。 在此範例中，請將 "node_id30" 物件拖曳至這兩個位置中，如下圖所示。

> 當您啟動或播放應用程式時，您的物件現在將被藍色框架包圍。 您可以拖曳該框架的角來調整物件的大小。 如果我們希望縮放控點和旋轉控點更大且更明顯，我們建議使用預設的週框方塊設定 (避免步驟 4-7)。 

![Lesson4 Chapter3 Step8im](images/Lesson4_Chapter3_step8im.PNG)

9. 若要回到預設的週框方塊視覺效果，請在週框方塊物件的 [Inspector] 面板中，選取旋轉控點預製物件並按下 Delete 鍵，您現在會看到類似下圖的週框方塊視覺效果。 注意：週框方塊視覺效果僅在播放模式中顯示。

![Lesson4 Chapter3 Step9im](images/Lesson4_chapter3_step9im.PNG)

### <a name="adding-touch-effects"></a>新增觸控效果
在此範例中，當您用手觸控物件時，我們將播放音效。

1. 將音訊來源元件新增至遊戲物件中。 選取場景階層中的 "octa" 物件。 在 [Inspector] 面板中，按一下 [Add Component] 按鈕並搜尋並選取 [Audio Source] \(音訊來源\)。 我們將在後續步驟中使用此音訊來源播放音效。 

>注意：請確定 "Octa" 物件上有方塊碰撞器。

2. 新增 [Near Interaction Touchable] \(可近距觸控互動\) 元件。 按一下 [Inspector] 面板中的 [Add Component] 按鈕，然後搜尋 "near interaction touchable"。 選取它以新增元件。 注意：修正螢幕擷取畫面以醒目提示我們正在新增該元件，而不僅僅是醒目提示方塊碰撞器。

>注意：之前我們新增了 [Near Interaction Grabbable]。 這與 [Near Interaction Touchable] 之間的區別在於，[Grabbable] 互動適用於可抓取與互動的物件。 [Touchable] 元件旨在用於可觸控的物件。 這兩個元件可以作為互動組合一起使用。

![Lesson4 Chapter4 Step1 2Im](images/Lesson4_chapter4_step1-2im.PNG)

3. 新增 [Hand Interaction Touch] \(手部觸控互動\) 指令碼。 請注意，此指令碼隨附於您作為此示範套件之一部分匯入的 Unity 場景中，且它不包含在原始 MRTK 中。 就像前一個步驟，按一下 [Add Component]，並搜尋 "hand interaction touch" 以新增它。 
   請注意，該指令碼有 3 個選項： 

   - [On touch completed] \(完成觸控時\)。 觸控並釋放物件時會觸發此動作。 
   - [On touch started] \(啟動觸控時\)。 觸控物件時會觸發此動作。 
   - [On touch updated] \(更新觸控時\)。 當您的手正在觸控物件時，會定期觸發此動作。 

   針對此範例，我們將使用 [On Touch Started] 設定。

4. 按一下 [On Touch Started] 選項上的 [+] 按鈕，如下圖所示。 將八邊形物件拖曳至空白的欄位中。 

5. 在顯示 [No Function] \(無功能\) 的下拉式清單 (下圖中的綠色矩形上方) 中，選取 [AudioSource] > [PlayOneShot]。 我們將使用下列概念為此欄位新增音訊剪輯：

   - MRTK 確實提供了一小部分音訊剪輯。 您可以在 [Project] 面板中隨意探索這些內容。 您可以在 [MixedRealityToolkit.SDK] 資料夾下的 [Standard Assets] 資料夾找到它們。 您在那裡會看到一個 [Audio] 資料夾，其中包含所有音訊剪輯。
   - 在此範例中，我們要使用 "MRTK_Gem" 音訊剪輯。 
   - 若要新增音訊剪輯，只需將所需的剪輯從 [Project] 面板拖曳至 [Inspector] 面板中的 AudioSource.PlayOneShot (在上述範例中以綠色方塊標示)。

   現在當使用者伸出手並觸控八邊形物件時，就會播放曲目 "MRTK_Gem"。 "Hand Interaction Touch" 指令碼還會在觸控時調整物件的顏色。 

![Lesson4 Chapter4 Step3 5 Noteim](images/Lesson4_chapter4_step3-5-noteim.PNG)

### <a name="congratulations"></a>恭喜！ 
在本課程中，您已了解如何在方格集合中組織 3D 物件以及如何使用近距互動 (使用手部追蹤直接抓取) 和遠距互動 (使用目光或手動光線) 來操作 3D 物件 (縮放、旋轉和移動)。您也已了解如何在 3D 物件周圍放置週框方塊，並了解如何在週框方塊上使用和自訂小工具。 最後，您學習到觸控物件時如何觸發事件。

[下一課：進階輸入](mrlearning-base-ch5.md)

