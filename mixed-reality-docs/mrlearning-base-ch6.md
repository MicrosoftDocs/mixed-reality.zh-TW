---
title: MR 學習基底模組-農曆模組組件範例體驗
description: 在這一課中，我們會結合多個從先前的課程，以建立唯一的範例經驗學到的概念。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合的實境，unity 教學課程 hololens
ms.openlocfilehash: 303ed17724ba8799490aa7bca7a60600f6e5349b
ms.sourcegitcommit: a32f673814a6cd6ff00f936f448885788b3b882c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "64929607"
---
# <a name="mr-learning-base-module---lunar-module-assembly-sample-experience"></a>MR 學習基底模組-農曆模組組件範例體驗

在這一課中，我們會結合多個從先前的課程，以建立唯一的範例經驗學到的概念。 我們將建立農曆模組組件的應用程式，因此使用者必須使用追蹤的手拿起農曆模組組件，並嘗試組合農曆模組。 我們將使用 pressable 按鈕來切換位置提示，重設我們的經驗，並在啟動我們農曆模組到空間 ！ 在未來教學課程中，我們會繼續這項體驗，包括功能強大多使用者的使用案例，利用 Azure 空間的錨點 」 來提供空間的對齊方式為基礎。

## <a name="objectives"></a>目標

- 結合多個概念，從先前的課程，以創造獨特體驗
- 了解如何切換物件
- 觸發程序的複雜事件使用 pressable 按鈕
- 使用 rigidbody 物理和強制
- 探索如何使用工具提示

## <a name="instructions"></a>指示

### <a name="configuring-the-lunar-module"></a>設定農曆模組

在本章中，我們將介紹建立我們的範例體驗所需的各種元件。

1. 加入基底場景農曆模組組件 prefab。 若要這樣做，請在您的專案 索引標籤中，搜尋"Rocket Launcher_Tutorial。 」 您也可能會在資產中發現 prefab > BaseModuleAssets > Prefabs。 您可能會看到兩個 rocket 啟動器 prefabs;一個具有名稱為 「 教學課程 」，另一個名稱 「 完成 」。 將"Rocket Launcher_Tutorial"prefab 拖曳至基底場景。 請隨意放置在場景中 prefab 的位置。
   注意："Rocket Launcher_Complete"prefab 是已完成的啟動器，供參考。 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

如果您在您階層中，展開 「 Rocket Launcher_Tutorial 」 遊戲物件，並進一步展開 「 農曆模組 」 物件，您會看到數個子物件的材質，稱為 「 雷射。 」 "X 光 」 資料可讓您，我們將使用作為放置提示使用者的稍有半透明色彩。 

![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG)有五個部分農曆模組使用者即將進行互動，如下圖所示：

1.  Rover 機箱
2.  油箱
3.  能源儲存格
4.  停駐的入口網站 
5.  外部感應器

![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> 注意：您會看到您的基底的場景階層中的遊戲的物件名稱未對應到場景中物件的名稱。

步驟 2：將音訊來源加入農曆模組。 請確定選取農曆模組基底的場景階層中，然後按一下 [新增元件]。 搜尋 「 音訊來源 」，並將它新增至物件。 保留空白目前。 我們將使用此稍後播放啟動聲音。
 ![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG)步驟 3:新增指令碼 「 切換位置提示 」。 按一下 [新增元件]，並搜尋 「 切換位置提示 」。 這是自訂的指令碼，可讓您開啟和關閉半透明提示 （x 光資料的物件） 先前所述。 
![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG)步驟 4:由於我們有 5 個物件時，輸入"5"的遊戲物件的陣列大小。 然後您應該會看到出現的 5 個新項目。 

![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

每個的半透明物件拖曳至適當的方塊，說出 「 無 （遊戲物件）。 」 拖曳農曆模組基底場景中的下列物件： 

• 背包

• GasTank

• Topleftbody

• 鼻子

•   LeftTwirler

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

現在已設定 「 切換位置提示"指令碼。 這可讓我們開啟和關閉的提示。

步驟 5：新增 「 啟動農曆模組 」 的指令碼。 按一下 [新增元件] 按鈕，搜尋 「 啟動農曆模組 」，並加以選取。 此指令碼會負責啟動農曆模組。 當我們按下 [設定] 按鈕時，它會將向上強制農曆模組的固定的主體元件，並會往上啟動模組。 如果您是室內，農曆模組可能會針對最高限度網格損毀。 但是，如果您是戶外活動，它會飛抵中空間無限期。 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

步驟 6：調整主要目的是讓農曆模組會依正常程序的飛出。 請試著 0.01 的值。 將 「 Rb"欄位保留空白。 Rb 代表固定的內文，並在執行階段會自動填入這個欄位。

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a>農曆模組組件概觀
農曆模組組件的父物件是使用者互動的物件集合。 下列清單提供遊戲的物件名稱 （使用場景標示為 paretheses 中的名稱）：

- 背包 （油箱）
- GasTank （能源儲存格）
- TopLeftBody （Rover 機箱）
- 鼻子 （停駐的入口網站）
- LeftTwirler （外部感應器）

請注意，每個物件會有操作處理常式中，第 4 課中所述。 使用操作處理常式中，使用者可擷取及管理的物件。 也請注意，「 兩個右手的操作類型 」 設定為 「 移動和旋轉 」。 這只允許使用者移動物件，並不會變更其大小，也就是組件應用程式所需的功能。
此外，遠的操作未以只允許模組組件的直接互動。

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

部分組件的示範指令碼 （如上所示） 是管理使用者所放入農曆模組物件的指令碼。 

選取 (n 上面的影像，背包/油箱的大小寫) 與可連線至的物件轉換為 「 物件至位置 」 欄位。 

「 近距離 」 和 「 遠距離 」 設定負責決定的相近的組件會貼齊就地或釋出。 比方說，背包/油箱必須離開的地方貼齊農曆模組 0.1 的單位。 「 遠距離 」 設定為以中斷連結農曆模組需要物件的位置。 在此情況下，使用者的手必須抓取背包/油箱，然後將它 0.2 單位遠離農曆模組，以移除回貼齊定位。

「 工具提示物件 」 是在場景中的工具提示標籤。 當物件會就地貼齊時，標籤將會停用。 

音訊來源會自動抓取。 

### <a name="placement-hints-buttons"></a>放置提示按鈕
在 [第 2 課](mrlearning-base-ch2.md)，您已了解如何放置與設定按鈕，執行下列動作變更項目的色彩，或讓它推送時播放音效。 我們將繼續使用這些原則，當我們設定切換位置提示按鈕。 

目標是要設定我們的按鈕，以便每次使用者按下位置提示按鈕，它會切換可見性的半透明的位置提示。 

步驟 1：基底的場景階層中選取的位置提示物件時，請將農曆模組移到空 「 僅顯示 runtime 」 位置，在 [偵測器] 面板中。 
 ![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG)步驟 2:現在，按一下下拉式清單中，該處會指示，「 沒有函式 」。 移至 「 TogglePlacementHints"，以及該功能表下選取 「"ToggleGameObjects （）。 ToggleGameObjects() 將切換位置提示開啟和關閉，使其可見或不可見每次按下按鈕時。
 ![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a>設定重設 按鈕

會發生錯誤或意外地擲回物件，或只想要 rest 經驗的使用者可讓的情況。 重設 按鈕將能夠重新啟動的經驗。 

步驟 1：選取 [重設] 按鈕。 在基底的場景，它會命名為"ResetRoundButton。 」 

步驟 2：農曆模組會從基底的場景階層拖曳至 「 按下按鈕 」 下的空插槽偵測器 面板。
 ![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

步驟 3：選取下拉式功能表中，指出 「 沒有函式 」，並停留在 「 LaunchLunarModule。 」 現在選取 "resetModule （）"。

![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> 注意：您會注意到，根據預設"GameObject.BroadcastMessage 」 設定為"ResetPlacement。 」 這會廣播訊息，稱為 「 ResetPlacement"RocketLauncher_Tutorial 的每一個子物件。 該訊息會回應具有 「 ResetPlacement() 」 方法的任何物件重設它的位置。 

### <a name="launching-the-lunar-module"></a>啟動農曆模組
這一章，我們將設定 [啟動] 按鈕。 這將允許使用者按下按鈕，並啟動農曆模組到空間。

步驟 1：選取 [啟動] 按鈕 （基底的場景中它稱為 「 LaunchRoundButton"）。 將農曆模組拖曳至 「 觸控 End 」 下的空插槽中，在 [偵測器] 面板。
 ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG)步驟 2:選取下拉式功能表中，指出 「 沒有函式 」。 「 LaunchLunarModule 「 暫留並選取"StopThruster （）"。 這會控制多少使用者想要提供給農曆模組的主要目的是。 
 ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)步驟 3:「 ButtonPressed() 」，將農曆模組 （按一下、 按住不放，並拖曳） 新增至空的插槽。 

步驟 4：按一下下拉式功能表，指出 「 沒有函式 」 和 「 LaunchLunarModule 「 暫留，然後選取"StartThruster （）"。 
 ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)步驟 5:將音樂新增至農曆模組，讓當 rocket 將時，會播放音樂。 若要這樣做，請拖曳農曆模組到 」 按鈕 Pressed() 」 底下的下一步 的空插槽。

步驟 6：選取下拉式功能表中，指出 「 沒有函式 」"AudioSource 「 暫留並選取 「 PlayOneShot (AudioClip) 」。 請盡情探索各種 MRTK 所隨附的音效。 此範例中，我們要堅持使用"MRTK_Gem。 」
 ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)


### <a name="congratulations"></a>恭喜您 
您完整設定此應用程式 ！ 現在當您按下 播放，您可以完全組合農曆模組、 切換提示、 啟動農曆模組，並將它做過一次重設。
