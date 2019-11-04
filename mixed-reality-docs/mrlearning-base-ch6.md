---
title: 使用者入門教學課程-7。 建立農曆模組範例應用程式
description: 在這一課，您將結合從先前課程中學到的多個概念，以建立獨特的範例體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: a4f405b29ac87945a8585beeed83c1beb450eb0e
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437752"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7. 建立農曆模組範例應用程式

在本教學課程中，會將多個概念與前一課結合，以建立獨特的範例體驗。 您將瞭解如何建立一個陰曆模組元件應用程式，讓使用者必須使用追蹤的手來挑選陰曆模組零件，並嘗試組合陰曆模組。 我們會使用 [pressable] 按鈕來切換放置提示、重設我們的體驗，以及啟動我們的陰曆模組來進行空間！ 在未來的教學課程中，我們將繼續以這項體驗為基礎，其中包含強大的多使用者使用案例，可運用 Azure 空間錨點來進行空間對齊。

## <a name="objectives"></a>目標

- 結合來自先前課程的多個概念以建立獨特體驗
- 了解如何切換物件
- 使用可點按的按鈕來觸發複雜事件
- 使用 rigidbody 物理特性和力
- 探索工具提示的使用

## <a name="instructions"></a>指示

### <a name="configuring-the-lunar-module"></a>設定登月小艇

在本節中，我們將介紹建立範例體驗所需的各種元件。

1. 將 [農曆模組元件] prefab 新增至您的基礎場景。 若要這麼做，請在 專案 索引標籤中搜尋 Rocket Launcher_Tutorial。在 資產 中尋找 prefab-> BaseModuleAssets-> Prefabs。 您也會看到兩個 rocket 啟動器 prefabs;一個名稱為 "教學課程"，另一個名稱為 "complete"。 將 [Rocket Launcher_Tutorial prefab] 拖曳至您的基礎場景，並依您想要的位置。
注意： Rocket Launcher_Complete prefab 是已完成的啟動器，提供供參考之用。 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

如果您展開階層中的 [Rocket Launcher_Tutorial 遊戲] 物件，並進一步展開 [陰曆] 模組物件，您會發現有數個子物件具有稱為「x-光線」的材質。 「X 光線」材質允許使用稍微半透明的色彩，做為使用者的放置提示。 

![第6課 Chapter1.txt Noteaim](images/Lesson6_Chapter1_noteaim.PNG) 使用者將與其互動的陰曆模組有五個部分，如下圖所示：

1.  月球車外殼
2.  油箱
3.  能量電池
4.  泊接座 
5.  外部感應器

![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> 注意：您在基底場景階層中看到的遊戲物件名稱不會對應到場景中的物件名稱。

步驟2：將音訊來源新增至農曆模組。 請確定已在您的基底場景階層中選取 [陰曆] 模組，然後按一下 [新增元件]。 搜尋 [音訊來源]，並將它新增至物件。 現在請將它保留為空白，但按一下 [Spatialize] 核取方塊以啟用空間音訊。 稍後您將使用此來播放啟動音效。

 ![第6課 Chapter1.txt Step2im](images/Lesson6_Chapter1_step2im.PNG)  
步驟3：加入腳本切換位置提示。 按一下 [新增元件]，並搜尋切換位置提示。 這是自訂腳本，可讓您開啟和關閉半透明提示（具有 x 光線材質的物件），如先前所述。  
![第6課 Chapter1.txt Step3im](images/Lesson6_Chapter1_step3im.PNG)  
步驟4：因為我們有五個物件，請輸入 "5" 作為遊戲物件陣列大小。 您接著會看到五個新的元素。  


![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

將每個半透明物件拖曳到所有名稱（遊戲物件）方塊中。
將下列物件從登月小艇拖曳到基底場景中： 

•   Backpack

•   GasTank

•   Topleftbody

•   Nose

•   LeftTwirler

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

現在已設定了切換位置提示腳本，可讓我們開啟和關閉提示。

步驟5：新增啟動陰曆模組腳本。 按一下 [新增元件] 按鈕，搜尋「啟動陰曆模組」並加以選取。 此腳本會啟動農曆模組。 當我們按下設定的按鈕時，它會將向上的力新增至農曆模組的固定主體元件，並使模組向上啟動。 如果您位於室內，登月小艇可能會撞擊您的天花板網格。 如果您所在的區域具有高上限或沒有上限，農曆模組會無限期地進入空間。 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

步驟6：調整天生，讓陰曆模組能夠正常運作。 試試使用 0.01 的值。 將 [Rb] 欄位保留空白。 Rb 代表固定主體，而此欄位將會在執行時間自動填入。

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a>陰曆模組元件總覽
陰曆模組元件父物件是使用者與之互動物件的集合。 下列清單會提供遊戲物件名稱，其中包含 paretheses 中標示為名稱的場景：

- Backpack (Fuel Tank)
- GasTank (Energy Cell)
- TopLeftBody (Rover Enclosure)
- Nose (Docking Portal)
- LeftTwirler (External Sensor)

請注意，每個物件都有操作處理常式，如第4課中所述。 這項功能可讓使用者抓取和操作物件。 另請注意，設定 [雙向操作類型] 設定為 [移動並旋轉]。 此選項只允許使用者移動物件，而不會變更其大小，這是元件應用程式所需的功能。
此外，會取消選取 [目前的操作]，只允許模組元件的直接互動。

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

部分元件示範腳本（如上所示）是用來管理使用者在陰曆模組上由使用者放置之物件的腳本。 

[要放置的物件] 欄位是已選取的轉換，如上圖所示，與所連接之物件相關聯的死忠/燃料箱。 

[近乎距離] 和 [距離距離] 設定會決定要放置或釋放的部分。 例如，死忠/燃料箱必須是0.1 單位，而不是陰曆模組，才會貼齊位置。 [最遠距離] 設定會設定物件可以從農曆模組卸離之前的位置。 在此情況下，使用者的手必須抓住 backpack/fuel tank，並將它拖曳至距離登月小艇 0.2 單位的距離，才能將它從原本的定位移除。

工具提示物件是場景中的工具提示標籤。 當物件準備就緒時，會停用標籤。 

音訊來源會自動抓取。 

### <a name="placement-hints-buttons"></a>放置提示按鈕
在[第2課](mrlearning-base-ch2.md)中，您已瞭解如何放置和設定按鈕來執行一些動作，例如變更專案的色彩，或讓它在推送時播放音效。 我們將會繼續使用那些原則來設定按鈕以切換放置提示。 

其目標是設定按鈕，讓每次使用者按下 [放置提示] 按鈕時，都會切換半透明放置提示的可見度。 

步驟1：將 [陰曆] 模組移至 [偵測器] 面板中的 [僅限空白執行時間] 位置，同時在您的基底場景階層中選取放置提示物件。 
 ![第6課 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) 步驟2：按一下 [沒有函數] 下拉式清單。 向下 TogglePlacementHints，然後選取該功能表下的 [ToggleGameObjects （）]。 ToggleGameObjects （）會開啟和關閉放置提示，使其在每次按下按鈕時都可見或隱藏。  
 ![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a>設定重設按鈕

在某些情況下，使用者會犯錯誤，意外地擲回物件，或只是想要重設體驗。 [重設] 按鈕會新增重新開機體驗的功能。 

步驟1：選取 [重設] 按鈕。 在基底場景中，其名稱為 ResetRoundButton。 

步驟2：將 [陰曆] 模組從 [基底場景] 階層拖曳至 [偵測器] 面板上按下按鈕底下的空插槽。
 ![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

步驟3：選取 [沒有函式] 下拉式功能表，並將滑鼠停留在 [LaunchLunarModule] 上，然後選取 [resetModule （）]。

![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> 注意：請注意，根據預設，GameObject. BroadcastMessage 會設定為 ResetPlacement。 這會為 RocketLauncher_Tutorial 的每個子物件廣播一則名為 ResetPlacement 的訊息。 具有 ResetPlacement （）方法的任何物件都會藉由重設其位置來回應該訊息。 

### <a name="launching-the-lunar-module"></a>啟動農曆模組
本節說明如何設定 [啟動] 按鈕，讓使用者按下按鈕，並將 [陰曆] 模組啟動到空間。

步驟1：選取 [啟動] 按鈕。 在基底場景中，它稱為 LaunchRoundButton。 將 [陰曆] 模組拖曳至 [偵測器] 面板中 [Touch End] 底下的空插槽。
 ![第6課 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) 步驟2：選取 [沒有函式] 下拉式功能表，並將滑鼠停留在 LaunchLunarModule 上，然後選取 [StopThruster （）]。 這會控制使用者想要提供給陰曆模組的天生量。 
 ![第6課 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)  
步驟3：在 [ButtonPressed （）] 底下，將 [農曆] 模組（按一下、按住和拖曳）新增至空白位置。 

步驟4：按一下 [沒有函式] 下拉式功能表，將滑鼠停留在 LaunchLunarModule 上，然後選取 [StartThruster （）]。 
 ![第6課 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)  
步驟5：將音樂新增至農曆模組，以便在 rocket 時播放音樂。 若要這麼做，請將 [陰曆] 模組拖曳至 [按下的按鈕] 下的下一個空白插槽（）。

步驟6：選取 [無函式] 下拉式功能表，將滑鼠停留在 Spatialize 上，然後選取 [PlayOneShot （AudioClip）]。 您可以自行探索包含在 MRTK 中的各種音效。 在此範例中，我們將使用「MRTK_Gem」。
 ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)


### <a name="congratulations"></a>恭喜您 
您已完全設定此應用程式。 現在，當您按下 [播放] 時，您可以完整組合陰曆模組、切換提示、啟動陰曆模組，然後將它重設為重新啟動。
