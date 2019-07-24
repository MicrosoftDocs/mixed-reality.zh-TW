---
title: MR 學習基本模組 - 3D 物件互動
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: d47f2940ad741cb436322a824a67f54bb6376c55
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387699"
---
# <a name="5-interacting-with-3d-objects"></a>5.與3D 物件互動

在本教學課程中, 我們將瞭解基本的3D 內容和使用者體驗。 我們將深入瞭解: 
* 將3D 物件組織成集合的一部分。
* 基本操作的周框方塊。
* 近乎即時的互動。
* 觸控和抓取手勢, 並使用手動追蹤。 

## <a name="objectives"></a>目標

* 瞭解如何使用 MRTK 的方格物件集合來組織3D 內容
* 實作週框方塊
* 設定3D 物件進行基本操作--移動、旋轉和縮放
* 探索遠近互動
* 深入瞭解其他的右手邊追蹤手勢, 例如「抓取」和「觸控」

## <a name="instructions"></a>指示

### <a name="organizing-3d-objects-in-a-collection"></a>組織集合中的 3D 物件

1. 以滑鼠右鍵按一下您的階層, 然後選取 [建立空的]。 這會建立空的遊戲物件。 將它重新命名為3DObjectCollection。 這是我們放置所有 3D 物件的地方。 確定集合的位置設定為 x = 0、y = 0 且 z = 0。

![Lesson4 Chapter1 Step1im](images/Lesson4_Chapter1_step1im.PNG)

2. 使用相同的指示匯入 BaseModule 資產, 以匯入[tut1-lesson1-step3](mrlearning-base-ch1.md)中所述的自訂套件。 BaseModule 資產包含3D 模組, 以及在本教學課程中使用的其他實用腳本。 您可以在這裡找到 BaseModule Unity 封裝:<https://github.com/Microsoft/MixedRealityLearning/releases/tag/V1.1>

3. 咖啡杯預製物件可以透過旁邊的藍色立方體辨識。 請勿選取具有藍色立方體和小型白色紙張的咖啡杯, 因為這代表原始的3D 模型, 而不是 prefab。) 

![Lesson4 Chapter1 Noteaim](images/Lesson4_chapter1_noteaim.PNG)

4. 將您選擇的咖啡杯 prefab 拖曳至步驟1中的3DObjectCollection 遊戲物件。 咖啡杯現在是該集合的子系。

![Lesson4 Chapter1 Step4ima](images/Lesson4_chapter1_step4ima.PNG)

5. 接下來，我們將新增更多的 3D 物件至場景。 以下是我們將在此範例中新增的物件清單。 當您新增物件時, 您可能會發現它們以各種大小出現在場景中。 調整 [偵測器] 面板中 [轉換設定] 下每個3D 模型的尺規。 以下的物件列出了此範例的建議調整。 在 [專案] 面板的 [搜尋] 方塊中搜尋這些單字, 然後將3D 物件 prefab 拖曳到類似上一個步驟的3DObjectCollection 物件中。 您會在 [資產] 中找到這些 prefabs 的集合 > BaseModuleAssets > 基底模組 Prefabs
- 搜尋 TheModule_BaseModuleIncomplete。 拖曳至場景。 將比例設置為 x = 0.03、y = 0.03、z = 0.03。 
- 搜尋 Octa_BaseModuleIncomplete。 拖曳至場景。 將比例設置為 x = 0.13、 y = 0.13、z =0.13。
- 搜尋 EarthCore_BaseModuleIncomplete。 拖曳至場景。 將比例設置為 x = 50.0、y = 50.0、z = 50.0。
- 搜尋 Cheese_BaseModuleIncomplete。 拖曳至場景。 將比例設置為 x = 0.05、y = 0.05、z = 0.05。
- 搜尋 Model_Platonic_BaseModuleIncomplete。 拖曳至場景。 將比例設置為 x = 0.13、y = 0.13、z = 0.13。

![Lesson4 Chapter1 Step5im](images/Lesson4_Chapter1_step5im.PNG)

6. 將三個 cube 新增至您的場景。 以滑鼠右鍵按一下 [3DObjectCollection] 物件, 選取 [3D 物件], 然後選取 [Cube]。 將比例設置為 x = 0.14、y = 0.14 且 z = 0.14。 重複此步驟兩次, 以建立總共三個 cube。 或者, 您可以將 cube 複製兩次, 共三個 cube。 您也可以選擇使用 Assets>BaseModuleAssets>Base Module Prefabs 中三個已備妥的立方體預製物件，並選取 GreenCube_BaseModuleIncomplete、BlueCube_BaseModuleIncomplete 和 OrangeCube_BaseModuleIncomplete。

![Lesson4 Chapter1 Step6im](images/Lesson4_Chapter1_step6im.PNG)

7. 使用 MRTK 的方格物件集合中的[第 2 課](mrlearning-base-ch2.md)中所述的程序，組織您的物件集合以形成方格。 請參閱下圖，查看在 3x3 方格中設定物件的範例。

![Lesson4 Chapter1 Notebim](images/Lesson4_chapter1_notebim.PNG)

>注意:您可能會注意到有些物件是停在中心, 例如上圖中的物件。 這是因為預製物件或物件可能具有未對齊的子物件。 隨意對物件位置或子物件位置進行必要的調整，以實現完善對齊的方格。


### <a name="manipulating-3d-objects"></a>操作 3D 物件
1. 新增可操作立方體的功能。 若要新增操作3D 物件的功能, 請執行下列動作:
-   選取您想要在階層中操作的3D 物件, 也就是您的其中一個 cube。
-   按一下 [新增元件]。 
-   搜尋操作。
-   選取 [操作處理常式]。
-   針對3DObjectCollection 物件下的所有3D 物件重複執行, 但不針對3DObjectCollection 本身。
-   確定所有3D 物件都有碰撞或方塊碰撞 (新增元件 > 方塊碰撞)。

![Lesson4 Chapter2 Step1im](images/Lesson4_chapter2_step1im.PNG)

>操作處理常式是一種元件, 可讓您調整物件在操作時的行為方式設定。 這包括在特定軸上旋轉、縮放、移動和限制移動。 

2. 限制一個立方體，使其只能縮放。 在3DObjectCollection 物件中選取一個 cube。 在 [偵測器] 面板中, 按一下 [兩個操作類型] 旁的下拉式功能表, 然後選取 [調整]。 這使得使用者只能變更立方體的大小。

![Lesson4 Chapter2 Step2im](images/Lesson4_Chapter2_step2im.PNG)

3. 變更每個立方體的色彩，以便我們可以區分它們。 
-   移至 [專案] 面板並向下 MixedRealityToolkit, 直到您看到 [SDK], 然後選取它。
-   選取 [標準資產] 資料夾。
-   按一下 [材質] 資料夾。
-   將不同的材質拖曳到每個立方體上。 

>注意:您可以為立方體選擇任何色彩。 在我們的範例中, 我們將使用 glowingcyan、glowingorange 和綠色。 請隨意試驗不同的色彩。 若要將色彩加入 cube 中, 請按一下您要變更的 cube, 然後將材質拖曳至 cube 的 [偵測器] 面板中的網格轉譯器的 [材質] 欄位。 

![Lesson4 Chapter2 Step3im](images/Lesson4_Chapter2_step3im.PNG)

4. 選取3DObjectCollection 物件中的另一個 cube, 並將它的移動限制為來自 head 的固定距離。 若要這麼做, 請在 [移動標籤上的條件約束] 右邊, 按一下下拉式功能表, 然後選取 [修正與 Head 的距離]。 這使得使用者只能在其視野內移動立方體。 

![Lesson4 Chapter2 Step4im](images/Lesson4_chapter2_step4im.PNG)

接下來幾個步驟的目標是要啟用抓取並與我們的3D 物件互動, 以及套用不同的操作設定。

5. 選取 [乳酪] 物件, 然後按一下 [偵測器] 面板中的 [新增元件]。 

6. 在搜尋方塊中搜尋近乎互動的 Grabbable, 然後選取腳本。 此元件可讓使用者使用已追蹤的手來觸及和抓取物件。 物件也可以從距離進行操作, 除非取消核取 [允許最大操作] 核取方塊, 如下圖中的綠色圓形所表示。

![Lesson4 Chapter2 Step6im](images/Lesson4_Chapter2_step6im.PNG)

7. 在這些物件上重複步驟5和 6, 以將近乎互動的 Grabbable 新增至顆 octa 物件、Platonic 物件、地球核心、陰曆模組和咖啡杯。

8. 從八邊形物件中移除遠距操作的能力。 若要這麼做, 請選取階層中的顆 octa, 並取消核取 [允許最大的操作] 核取方塊 (以綠色圓圈標示)。 這使得使用者只能使用手部追蹤直接與八邊形互動。

>注意:如需操作處理常式元件及其相關設定的完整文件，請參閱 [MRTK 文件](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)。

9. 請確定已將近距離互動 Grabbable 元件新增到地球核心、農曆模組和咖啡杯 (請參閱步驟 7)。

10. 針對農曆模組, 請變更操作處理常式設定, 讓它針對接近和遠的互動旋轉物件中心, 如下圖所示。

![Lesson4 Chapter2 Step10im](images/Lesson4_chapter2_step10im.PNG)

11.針對地球核心, 將發行行為變更為 [無]。 如此一來, 當地球核心從使用者的理解中放開之後, 就不會繼續移動。 

![Lesson4 Chapter2 Step11im](images/Lesson4_Chapter2_step11im.PNG)

> 注意:此設定對於建立可以投擲的球等場景非常有用。 保持速度和角度的速度, 讓它在球放開之後, 會繼續在其發行的速度上移動, 類似于實體球的行為。

### <a name="adding-bounding-boxes"></a>新增週框方塊
週框方塊讓您更輕鬆且更直覺地以一隻手操作物件，可用於直接操作 (近距互動) 和射線操作 (遠距互動)。周框方塊提供的控制碼可用於在特定軸上縮放和旋轉物件。
>注意:在您可以將周框方塊加入物件之前, 您必須先在物件 (例如, 方塊碰撞) 上具有碰撞, 如同我們先前在本課程中所做的一樣。 可以透過選取物件來新增碰撞器，並在物件的 [Inspector] 面板中選取 [Add Component] > [Box Collider] \([新增元件] > [方塊碰撞器]\)。
>

1. 將 box 碰撞項新增至地球核心物件 (如果尚未存在)。 若依照給定的指示使用基本模組的 [資產] 資料夾中提供的 prefab, 則不需要 box 碰撞和設定。 在地球核心的案例中, 我們已將方塊碰撞項新增至地球核心底下的 node_id30 物件, 如下圖所示。 從物件的 [偵測器] 索引標籤中選取 [node_id30], 按一下 [新增元件], 然後搜尋方塊碰撞器。 

![Lesson4 Chapter3 Step1im](images/Lesson4_Chapter3_step1im.PNG)

![Lesson4 Chapter3 Step2im](images/Lesson4_chapter3_step2im.PNG)

> 注意:請確定您已調整方塊的碰撞器大小, 使其變得太大或太小。 它的大小應與它周圍的物件大致相同 (在本例中為地核)。 選取方塊碰撞器中的 [編輯碰撞器] 選項, 視需要調整方塊碰撞器。 您可以變更 [x]、[y] 和 [z] 值, 或在編輯器場景視窗中拖曳周框方塊處理常式。 

![Lesson4 Chapter3 Noteim](images/Lesson4_Chapter3_noteim.PNG)

2. 將周框方塊新增至地球核心的 node_id30 物件。 若要這樣做, 請從3DObjectCollection 選取 node_id30 物件。 在 [偵測器] 索引標籤中, 按一下 [加入元件], 然後搜尋周框方塊。 請確定週框方塊、方塊碰撞器和操作指令碼 (Manipulation Handler、Near Interaction Grabbable) 都在同一個遊戲物件上。

3.  在周框方塊的 [行為] 區段中, 從 [啟用] 下拉式清單選取 [啟動時啟用]。 若要檢閱有關各種啟用選項和其他週框方塊選項的其他詳細資料，請參閱 [MRTK 的週框方塊文件](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>) \(英文\)

   

   *在接下來的幾個步驟中, 我們也會變更周框方塊的外觀, 方法是調整預設的方塊材質、抓取的資料, 以及角落和邊控點的視覺效果。MRTK 包含幾個用於自訂週框方塊的選項。*

4. 在 [專案] 面板中, 搜尋 boundingbox, 您會在搜尋結果中看到藍色球體所表示的材質清單, 如下圖所示。 

5. 將 boundingbox 材質拖曳至周框方塊元件上的方塊材質位置。 同時抓取 boundingboxgrabbed 的資料, 並將其放在 [周框方塊] 元件上的 [可抓取材料位置] 方塊中。

6. 將 [MRTK_BoundingBox_ScaleWidget] prefab 拖曳至 [周框方塊] 元件上的 [縮放控點] prefab 位置。 

7. 將 [MRTK_BoundingBox_RotateWidget prefab] 拖曳到 [結合] 方塊元件上的 [旋轉控點] 插槽。

![Lesson4 Chapter3 Step4 7Im](images/Lesson4_chapter3_step4-7im.PNG)

8. 請確定週框方塊的目標是正確的物件。 在 [周框方塊] 元件中, 有 [目標物件] 和 [界限覆寫] 腳本。 請務必將具有週框方塊的物件拖曳至這兩個位置中。 在此範例中, 將 node_id30 物件拖曳到這兩個位置, 如下圖所示。

> 當您啟動或播放應用程式時, 您的物件將會以藍色框架括住。 您可以拖曳該框架的角來調整物件的大小。 如果您想要縮放控點和旋轉控點變得更大且更可見, 則建議使用預設周框方塊設定 (避免步驟4到 7)。 

![Lesson4 Chapter3 Step8im](images/Lesson4_Chapter3_step8im.PNG)

9. 若要返回預設周框方塊視覺效果, 請在周框方塊物件的 [偵測器] 面板中選取 [旋轉控點] prefab, 然後按 [刪除]。 您會看到如下圖所示的周框方塊視覺效果。 注意：週框方塊視覺效果僅在播放模式中顯示。

![Lesson4 Chapter3 Step9im](images/Lesson4_chapter3_step9im.PNG)

### <a name="adding-touch-effects"></a>新增觸控效果
在此範例中，當您用手觸控物件時，我們將播放音效。

1. 將音訊來源元件新增至遊戲物件中。 選取場景階層中的 [顆 octa] 物件。 在 [偵測器] 面板中, 按一下 [新增元件] 按鈕, 搜尋並選取 [音訊來源]。 我們將在後續步驟中使用此音訊來源播放音效。 

>注意:請確定顆 octa 物件上有方塊碰撞器。

2. 新增附近的互動 Touchable 元件。 按一下 [偵測器] 面板中的 [新增元件] 按鈕, 並搜尋近乎互動 touchable。 選取它以新增元件。 

>注意:在過去, 我們新增了近乎互動的 grabbable。 此互動和近距離互動 touchable 之間的差異在於, grabbable 互動的目的是要讓物件能夠抓取並與互動。 Touchable 元件適用于要觸及的物件。 這兩個元件可以作為互動組合一起使用。

![Lesson4 Chapter4 Step1 2Im](images/Lesson4_chapter4_step1-2im.PNG)

3. 在手互動觸控腳本中加入。 請注意, 此腳本包含在您匯入做為此示範一部分的 Unity 場景中, 而且不會包含在原始 MRTK 中。 就像上一個步驟一樣, 按一下 [新增元件], 然後搜尋 [手動互動觸控] 將其新增。

>請注意, 您有三個使用腳本的選項: 

>   - 觸碰已完成:當您接觸並釋放物件時觸發
>   - 開始觸控時:觸及物件時觸發
>   - 已更新的觸控:當您的手中觸及物件時, 定期觸發

>   在此範例中, 我們將使用 [啟動觸控] 設定。

4. 按一下 [On Touch 已啟動] 選項上的 [+] 按鈕, 如下圖所示。 將顆 octa 物件拖曳至空白欄位。 

5. 在顯示 [沒有函式 (下圖中的綠色矩形)] 的下拉式方塊中, 選取 [Spatialize-> PlayOneShot]。 我們將使用下列概念為此欄位新增音訊剪輯：

   - MRTK 確實提供了一小部分音訊剪輯。 您可以在 [Project] 面板中隨意探索這些內容。 您會在 [MixedRealityToolkit] 資料夾下找到這些專案, 然後按 [標準資產] 資料夾。 您會在那裡看到所有音訊剪輯所在的音訊資料夾。
   - 在此範例中, 我們將使用 MRTK_Gem 音訊剪輯。 
   - 若要新增音訊剪輯，只需將所需的剪輯從 [Project] 面板拖曳至 [Inspector] 面板中的 AudioSource.PlayOneShot (在上述範例中以綠色方塊標示)。

   現在當使用者到達並觸及顆 octa 物件時, 將會播放音訊追蹤 MRTK_Gem。 觸碰互動觸控腳本也會在觸碰時調整物件的色彩。 

![Lesson4 Chapter4 Step3 5 Noteim](images/Lesson4_chapter4_step3-5-noteim.PNG)

### <a name="congratulations"></a>恭喜！ 
在本教學課程中, 您已學到如何在方格集合中組織3D 物件, 以及如何使用近距離互動 (直接抓取手) 和即時互動 (使用注視光線或手片) 來操作3D 物件 (縮放、旋轉和移動)。 您也學到如何將周框方塊放在3D 物件周圍, 學習如何使用和自訂周框方塊上的 gizmos。 最後，您學習到觸控物件時如何觸發事件。

[下一課：進階輸入](mrlearning-base-ch5.md)

