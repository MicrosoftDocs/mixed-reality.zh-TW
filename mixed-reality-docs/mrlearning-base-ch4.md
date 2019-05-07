---
title: MR 學習基底模組-3D 物件互動
description: 完成這個課程來了解如何在混合的實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合的實境，unity 教學課程 hololens
ms.openlocfilehash: 344b3bc892839bc22445e10af644771bc7008ac3
ms.sourcegitcommit: a32f673814a6cd6ff00f936f448885788b3b882c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "64929587"
---
# <a name="mr-learning-base-module---3d-object-interaction"></a>MR 學習基底模組-3D 物件互動

在這一課中，我們將探討基本的 3D 內容和使用者體驗。 我們將了解如何組織集合中的 3D 物件、 了解週框方塊的基本操作、 遠近互動，了解和深入了解觸控和追蹤的手中抓取筆勢。 

## <a name="objectives"></a>目標

* 了解如何組織使用 MRTK 的格線物件集合的 3D 內容
* 週框方塊的實作
* 設定基本操作 （旋轉、 移動和小數位數） 的 3D 物件
* 瀏覽遠近互動
* 深入了解其他手動追蹤抓取等觸控筆勢

## <a name="instructions"></a>指示

### <a name="organizing-3d-objects-in-a-collection"></a>組織集合中的 3D 物件

1. 以滑鼠右鍵按一下您的階層，選取 [建立] 空白。 這會建立空的遊戲物件。 重新命名為"3DObjectCollection。 」 這是我們將會放置所有 3D 物件。 請確定在集合的位置設定為 x = 0，y = 0，且 z = 0。

![Lesson4 Chapter1 Step1im](images/Lesson4_Chapter1_step1im.PNG)

2. 匯入 BaseModule 資產使用相同的指示來匯入自訂套件中所述[Lesson1](mrlearning-base-ch1.md)。 BaseModule 資產包括 3D 的模組和其他實用的指令碼將用於本教學課程。 BaseModule unity 套件可以在這裡找到： <https://github.com/Microsoft/MixedRealityLearning/releases/tag/V1.1>

3. Prefab 的咖啡 cup 可以辨識的藍色的立方體旁邊。 請勿選取咖啡創意盃，藍色的立方體與小型的白皮書 （表示原始的 3D 模型和不 prefab。） 

![Lesson4 Chapter1 Noteaim](images/Lesson4_chapter1_noteaim.PNG)

4. 拖曳"3DObjectCollection 」 遊戲物件至您選擇的咖啡 cup prefab 來自步驟 1。 咖啡 cup 現在是集合的子系。

![Lesson4 Chapter1 Step4ima](images/Lesson4_chapter1_step4ima.PNG)

5. 接下來，我們將新增更多的 3D 物件至場景。 以下是我們將在此範例中新增的物件清單。 當您加入的物件可能會發現，它們會出現在場景中各種大小。 調整 [偵測器] 面板中的 [轉換] 設定下的每一個 3D 模型的大小。 建議的調整，此範例中會列出以下的物件。 在您的 [專案] 面板中的 [搜尋] 方塊中搜尋這些字組和 3D 物件 prefab 拖曳至 「 3DObjectCollection"物件類似於上一個步驟。 您會發現這些集合的 prefabs 在資產中 > BaseModuleAssets > 基底模組 Prefabs
- 搜尋"TheModule_BaseModuleIncomplete。 」 拖曳至場景。 設定標尺為 x = 0.03，y = 0.03，z = 0.03。 
- 搜尋"Octa_BaseModuleIncomplete。 」 拖曳至場景。 設定標尺為 x = $0.13。 y = 0.13, z =0.13.
- 搜尋"EarthCore_BaseModuleIncomplete。 」 拖曳至場景。 設定標尺為 x = 50.0 y = 50.0，z = 50.0。
- 搜尋"Cheese_BaseModuleIncomplete。 」 拖曳至場景。 設定標尺為 x = 0.05，y = 0.05，z = 0.05。
- 搜尋"Model_Platonic_BaseModuleIncomplete。 」 拖曳至場景。 設定標尺為 x = $0.13，y = $0.13，z = $0.13。
- 搜尋"CoffeeCup_BaseModuleIncomplete。 」 拖曳至場景。

![Lesson4 Chapter1 Step5im](images/Lesson4_Chapter1_step5im.PNG)

6. 您在場景中新增 3 個 cube。 以滑鼠右鍵按一下 「 3DObjectCollection"物件選取 「 3D 物件 」，然後選取 「 Cube 」。 設定標尺為 x = $0.14 元，y = $0.14 元，而 z = $0.14 元。 重複此步驟 2 再多建立 3 個 cube 的總計。 或者，您可能會重複兩次共 3 個 cube 的 cube。 您也可以選擇使用三個已備妥的 cube prefabs 從資產 > BaseModuleAssets > 基底模組 Prefabs 和選取 GreenCube_BaseModuleIncomplete、 BlueCube_BaseModuleIncomplete 和 OrangeCube_BaseModuleIncomplete。

![Lesson4 Chapter1 Step6im](images/Lesson4_Chapter1_step6im.PNG)

7. 組織您的集合的物件，以便使用中所述的程序的方格[第 2 課](mrlearning-base-ch2.md)使用 MRTK 的格線物件集合。 請參閱 3x3 的方格中設定之物件的範例，請參閱下圖。

![Lesson4 Chapter1 Notebim](images/Lesson4_chapter1_notebim.PNG)

>注意：您可能會發現某些物件會關閉中心，例如在上圖中的物件。 這是因為 prefabs 或物件可能未對齊的子物件。 歡迎對物件的位置或子系物件位置，以達到完善對齊的格線中的任何必要的調整。


### <a name="manipulating-3d-objects"></a>操作 3D 物件
1. 新增可操作 cube 的功能。 若要新增的功能，來操作 3D 物件，您必須執行下列動作：
-   選取您想要管理您的階層 （在此範例中，您的 cube 的其中一個） 中的 3D 物件。
-   按一下 [新增元件]。 
-   搜尋 「 操作 」。
-   選取 「 操作處理常式。 」
-   針對"3DObjectCollection 」 物件但不是"3DObjectCollection 」 底下的所有 3D 物件本身。
-   請確定所有的 3D 物件都具有 collider 或方塊 collider (新增元件 > 方塊 collider)。

![Lesson4 Chapter2 Step1im](images/Lesson4_chapter2_step1im.PNG)

>操作處理常式是一種元件，可讓您調整的設定物件所操作的行為。 這包括旋轉、 縮放、 移動和在特定軸上的條件約束移動。 

2. 限制一個 cube，使它只能調整。 選取一個 cube"3DObjectCollection 」 物件中。 在偵測器 面板中，兩個右手的操作類型 旁按一下下拉功能表並選取 「 延展 」。 這使得，讓使用者只能變更 cube 的大小。

![Lesson4 Chapter2 Step2im](images/Lesson4_Chapter2_step2im.PNG)

3. 變更每個 cube 的色彩，讓我們可以區分它們。 
-   移至 [專案] 面板，並向下捲動直到您看到 「 MixedRealityToolkit.SDK"，然後選取它。
-   選取 「 標準資產 」 資料夾。
-   按一下 「 資料 」 資料夾。
-   將不同的材料拖曳到每個 cube。 

>注意：針對您的 cube，您可以選擇任何色彩。 我們的範例中，我們將使用 「 glowingcyan"，"glowingorange 」，和 「 綠色 」。 請放心試驗不同的色彩。 若要將色彩加入 cube，按一下您想要變更的色彩，此的 cube，然後將資料拖曳到網格轉譯器的材料的欄位，在 cube 的偵測器窗格中。 

![Lesson4 Chapter2 Step3im](images/Lesson4_Chapter2_step3im.PNG)

4. 選取另一個 cube"3DObjectCollection 」 物件中，讓其移動受限於修正距離從標頭。 若要這樣做，在右邊的 「 條件約束對於移動 」 中，按一下下拉式功能表，然後選取 「 修正從標頭的距離。 」 這使得，讓使用者只能移動在其視野 cube。 

![Lesson4 Chapter2 Step4im](images/Lesson4_chapter2_step4im.PNG)

接下來的幾個步驟的目標：我們將啟用拿了就與我們的 3D 物件的互動。 我們將會套用不同的操作設定 

5. 選取起司物件，然後在 [偵測器] 面板中，按一下 [新增元件]。 

6. 搜尋在搜尋方塊中的 「 接近互動 Grabbable 」 並選取指令碼。 此元件可讓使用者連絡，並擷取追蹤的實際操作的物件。 物件也可操作的距離，除非 「 允許到目前為止操作 」 的核取方塊未核取 （以綠色的圓形，在下列影像中表示）。

![Lesson4 Chapter2 Step6im](images/Lesson4_Chapter2_step6im.PNG)

7. 「 接近互動 Grabbable"顆 Octa 物件、 柏拉圖物件、 地球核心、 農曆模組和 coffee cup 重複新增這些物件的步驟 5 和 6。

8. 從顆 Octa 物件中移除遠端操作的功能。 若要這樣做，請選取顆 Octa 在階層中，然後取消核取 [允許遠端操作] 核取方塊 （綠色圓形標記）。 這使得，讓使用者可以只會與直接使用追蹤的指針顆 octa 的方式互動。

>注意：如操作處理常式元件和它的完整文件都有相關聯的設定，請參閱[MRTK 文件](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)。

9. 確定 「 近互動 Grabbable"的元件具有已新增至地球核心、 農曆模組和 coffee cup （請參閱步驟 7）。

10. 農曆模組中，變更操作處理常式設定，讓其旋轉物件的同時附近的中心和遠端互動，如下圖所示。

![Lesson4 Chapter2 Step10im](images/Lesson4_chapter2_step10im.PNG)

11:地球核心中，將變更發行行為，以"nothing"。 這使得這樣之後從使用者掌握釋放地球核心時，它不會持續移動。 

![Lesson4 Chapter2 Step11im](images/Lesson4_Chapter2_step11im.PNG)

> 注意：此設定可用於使用案例，例如建立球，您可以擲回。 保留的速度和角速度將它，因此一旦球解除它將會繼續移動的速度是在已發行，類似於實體的球會行為方式。

### <a name="adding-bounding-boxes"></a>新增週框方塊
週框方塊讓您更輕鬆且更直覺地操作物件，以一隻手 （靠近互動） 的直接操作和射線操作 （遠端互動）。週框方塊提供 「 handles 」，可以抓取的縮放和旋轉物件沿著特定座標軸。
>注意：您可以加入物件中的週框方塊之前必須先有 collider 上的物件 (例如，方塊 collider。)如同我們先前在這一課。 選取物件，並在物件的偵測器窗格中選取 新增元件，可以加入 colliders > 方塊 Collider。
>

1. 加入方塊 collider 地球核心物件，如果不存在的話 （方塊 collider 而且不需要使用 [基底模組 Assets] 資料夾中，每個所提供的指示中所提供的 prefab 如果的安裝程式）。在地球核心，我們會需要將方塊 collider"node_id30"下方物件地球核心，如下圖所示。 選取 node_id30 和中物件的 [偵測器] 索引標籤上，按一下 [新增元件]，然後搜尋 「 box collider。 」 

![Lesson4 Chapter3 Step1im](images/Lesson4_Chapter3_step1im.PNG)

![Lesson4 Chapter3 Step2im](images/Lesson4_chapter3_step2im.PNG)

> 注意：請確定您視覺化方塊 collider，使它不是太大或太小。 它應該大約是 （在此範例中，地球核心），它周圍的物件相同的大小。 選取編輯 collider 選項方塊 collider 中視需要調整方塊 collider。 您可以變更 x、 y 和 z 值或拖曳編輯器場景視窗中的週框方塊處理常式。 

![Lesson4 Chapter3 Noteim](images/Lesson4_Chapter3_noteim.PNG)

2. 加入地球核心"node_id30 」 物件的週框方塊。 若要這樣做，請選取 "node_id30 」 物件，從 「 3DObjectCollection。 」 在 [inspector] 索引標籤中，按一下 [新增元件]，並搜尋 「 週框方塊 」。 請確定的週框方塊，方塊 collider 和操作指令碼 （操作處理常式，互動 grabbable 附近） 全都集中在同一遊戲物件。

3.  週框方塊的 「 行為 」 區段中，選取 啟用 開始 從下拉式清單中啟用。 若要檢閱有關的各種不同的啟用選項和其他的週框方塊選項的相關詳細資料，請參閱[MRTK 的週框方塊的文件](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>)

   

   *在接下來的步驟，我們也會變更藉由調整預設方塊材質、 材質時它正在捕捉，以及視覺效果的控制代碼 （角和側邊控點） 的週框方塊的外觀。MRTK 包含數個選項可自訂的週框方塊。*

4. 在 [專案] 面板中，如下圖所示適用於 「 boundingbox 」 以及您搜尋時，會看到藍色的球體，在搜尋結果中，以表示資料的清單。 

5. 週框方塊元件上拖曳方塊材料位置 」 boundingbox 」 資料。 也抓取"boundingboxgrabbed 」 資料，並將它放在方塊材質的位置中，週框方塊元件上。

6. 週框方塊元件上拖曳縮放控點 prefab 位置 」 MRTK_BoundingBox_ScaleWidget 」 資料。 

7. 拖曳旋轉控點位置的 「 MRTK_BoundingBox_RotateWidget"材料 bonding 方塊元件上。

![Lesson4 Chapter3 步驟 4 7Im](images/Lesson4_chapter3_step4-7im.PNG)

8. 請確定週框方塊的目標正確的物件。 在週框方塊元件中，沒有 「 目標物件 」 和 「 範圍覆寫 「 指令碼。 請務必將具有用於這些位置的週框方塊周圍的物件。 在此範例中，請將"node_id30 」 物件拖曳到這些兩個位置，如下圖所示。

> 當您啟動，或播放應用程式時，您的物件會現在括住的藍色外框。 歡迎您拖曳調整大小之物件的該框架的邊角。 如果我們想要調整的控制代碼和較大且更明顯可見的旋轉控點，我們建議使用預設的週框方塊的設定 （避免步驟 4-7）。 

![Lesson4 Chapter3 Step8im](images/Lesson4_Chapter3_step8im.PNG)

9. 若要返回預設值週框方塊的視覺效果，在偵測器窗格中的週框方塊的物件選取旋轉控點 prefab 並按下 delete 鍵，您現在會看到類似下面的影像的週框方塊 」 視覺效果。 注意： 只出現在播放模式中的週框方塊的視覺效果。

![Lesson4 Chapter3 Step9im](images/Lesson4_chapter3_step9im.PNG)

### <a name="adding-touch-effects"></a>加入觸控效果
在此範例中，我們即將播放的音效，當您使用您的手在同一個物件。

1. 將音訊來源元件新增至您遊戲的物件。 選取場景階層中的"顆 octa 」 物件。 在 [偵測器] 面板中，按一下 [新增元件] 按鈕，搜尋並選取 「 音訊來源 」。 若要播放的音效，在稍後的步驟，我們將使用此音訊來源。 

>注意：請確定 「 顆 Octa 」 物件上有方塊 collider。

2. 新增 < 近乎互動 touchable 」 元件。 按一下 新增元件 按鈕，在偵測器 面板並搜尋"近乎 touchable 互動。 」 請選取要新增的元件。 注意： 修正螢幕擷取畫面，反白顯示，我們要加入該元件，並不只反白顯示方塊 collider。

>注意：我們先前新增的 「 幾近互動 grabbable。 」 差異，以及 < 近乎互動 touchable 」 之間這會是"grabbable 」 互動，適用於捕捉和互動的物件。 「 Touchable"的元件被為了要觸及的物件。 這兩個元件可以互動的組合一起使用。

![Lesson4 Chapter4 Step1 2Im](images/Lesson4_chapter4_step1-2im.PNG)

3. 新增 「 送互動觸控 」 指令碼中。 請注意，此指令碼是隨附於 unity 場景，您匯入此示範套件的一部分，它不會納入原始 MRTK。 就像前一個步驟中，按一下 [新增元件]，並搜尋 「 手動互動接觸 」 將它加入。 
   請注意，您會有 3 個選項，使用指令碼： 

   - 「 在接觸已完成。 」 這會觸發觸控和釋放物件時。 
   - 「 在觸控已啟動。 」 這會觸發時所觸及的物件。 
   - 「 在觸控式更新。 」 這會定期將會觸發時手會觸碰物件。 

   針對此範例中，我們會使用"上啟動的接觸 」 設定。

4. 下圖所示，請按一下"上啟動的接觸 」 選項，"+"按鈕。 顆 octa 物件拖曳至空白的欄位。 

5. 在下拉式清單中，指出 「 沒有函式 」 （上述在下圖中的綠色矩形），選取 AudioSource > PlayOneShot。 我們會將音訊剪輯，加入這個欄位，使用下列概念：

   - MRTK 提供小型清單的音訊剪輯。 請隨意探索這些程式的 [專案] 面板中。 您會在 「 MixedRealityToolkit.SDK"資料夾，然後再 「 標準資產 」 資料夾下找到它們。 您會看到所有音訊剪輯是"audio"的資料夾。
   - 針對此範例中，我們要使用 「 MRTK_Gem"音訊剪輯。 
   - 若要新增的音訊剪輯，只要拖曳至您想要的剪輯從 [專案] 面板 AudioSource.PlayOneShot （在上述範例中的綠色方塊標示） 在 [偵測器] 面板。

   現在當使用者向外連並接觸顆 octa 物件時，就會播放音訊資料軌 「 MRTK_Gem"。 「 手動互動觸控 」 指令碼也會調整的色彩時接觸到的物件。 

![步驟 3-Chapter4 Lesson4 5 Noteim](images/Lesson4_chapter4_step3-5-noteim.PNG)

### <a name="congratulations"></a>恭喜您 
在這一課，您已了解如何組織方格集合中的 3D 物件，以及如何操作 （縮放、 旋轉和移動） 的 3D 物件使用附近 （直接抓取與追蹤的指針） 的互動以及遠端互動 （使用視線光線或手動光線）。您也已了解如何將 3D 物件周圍的週框方塊，並了解如何使用和自訂週框方塊的 gizmo。 最後，您已了解如何觸發事件時碰觸的物件。

[下一課：進階的輸入](mrlearning-base-ch5.md)

