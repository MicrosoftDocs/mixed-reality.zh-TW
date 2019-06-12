---
title: MR 學習基本模組 - 登月小艇組立範例體驗
description: 在本課程中，我們將會結合從先前課程中所學習到的多個概念，以建立獨特的範例體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 8a2f388e842d521f991203916177e3dac15769eb
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730851"
---
# <a name="mr-learning-base-module---lunar-module-assembly-sample-experience"></a>MR 學習基本模組 - 登月小艇組立範例體驗

在本課程中，我們將會結合從先前課程中所學習到的多個概念，以建立獨特的範例體驗。 我們將會建立登月小艇組立應用程式；在此應用程式中，使用者必須使用被追蹤的手掌來撿起登月小艇組件，並嘗試組立登月小艇。 我們將會使用可點按的按鈕來切換放置提示、重設體驗，以及將登月小艇發射到太空中！ 在未來的教學課程中，我們將以此體驗作為基礎持續建置，其中包括能運用 Azure Spatial Anchors 來取得空間錨點的強大多使用者使用案例。

## <a name="objectives"></a>目標

- 結合來自先前課程的多個概念以建立獨特體驗
- 了解如何切換物件
- 使用可點按的按鈕來觸發複雜事件
- 使用 rigidbody 物理特性和力
- 探索工具提示的使用

## <a name="instructions"></a>指示

### <a name="configuring-the-lunar-module"></a>設定登月小艇

在本章中，我們將會介紹建立範例體驗所需的各種元件。

1. 將登月小艇組立預製加入至您的基底場景。 若要這麼做，請在專案索引標籤中搜尋 "Rocket Launcher_Tutorial"。 您也可以在 Assets>BaseModuleAssets>Prefabs 中找到該預製。 您可能會看見兩個火箭發射器預製，一個名為 "tutorial"，另一個則名為 "complete"。 請將 "Rocket Launcher_Tutorial" 預製拖曳到您的基底場景。 您可以將預製置於場景中的任何位置。
   注意："Rocket Launcher_Complete" 預製是已完成的發射器，供您參考使用。 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

如果您在階層中展開 "Rocket Launcher_Tutorial" 遊戲物件，並進一步展開 "Lunar Module" 物件，您將會看到具有名為 "x-ray" 之材質的數個子物件。 "x-ray" 材質可提供些微半透明的色彩，而我們會將它用於提供給使用者的放置提示。 

![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) 登月小艇有五個使用者會進行互動的部分，如下圖所示：

1.  月球車外殼
2.  油箱
3.  能量電池
4.  泊接座 
5.  外部感應器

![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> 注意：您在基底場景階層中看見的遊戲物件名稱並不會與場景中的物件名稱相對應。

步驟 2：將音訊來源加入至登月小艇。 確定您已選取基底場景中的登月小艇，然後按一下 [Add Component] \(新增元件\)。 搜尋 "Audio Source" 然後將它加入至物件。 暫時將它保留空白。 我們稍後將會用它來播放發射音效。
 ![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG) 步驟 3：加入指令碼 "toggle placement hints"。 按一下 [Add Component] \(新增元件\)，然後搜尋 "Toggle Placement Hints"。 這個自訂指令碼可讓您開啟和關閉稍早所述的半透明提示 (具有 x-ray 材質的物件)。 
![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG) 步驟 4：由於我們有 5 個物件，請針對遊戲物件陣列大小輸入 "5"。 您應該會看見出現 5 個新的元素。 

![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

將每個半透明物件拖曳到顯示 [None (Game Object)] \(無 (遊戲物件)\) 的方塊。 將下列物件從登月小艇拖曳到基底場景中： 

•   Backpack

•   GasTank

•   Topleftbody

•   Nose

•   LeftTwirler

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

您已設定好 "toggle placement hints" 指令碼。 這可讓我們開啟和關閉提示。

步驟 5：加入 "launch lunar module" 指令碼。 按一下 [Add Component] \(新增元件\)，搜尋 "launch lunar module" 並選取它。 此指令碼將會負責發射登月小艇。 當我們按下已設定的按鈕時，它會將向上力加入至登月小艇的 rigidbody 元件，並會使小艇向上發射。 如果您位於室內，登月小艇可能會撞擊您的天花板網格。 但如果您位於室外，它將會無限制地飛向太空。 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

步驟 6：調整推力來使登月小艇能優雅地向上升起。 試試使用 0.01 的值。 將 [Rb] 欄位保留空白。 Rb 代表 rigidbody，因此系統將會在執行階段自動填入此欄位。

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a>登月小艇組件概觀
登月小艇組件父物件是使用者會互動之物件的集合。 下列清單提供遊戲物件名稱 (並於後方以括號註明場景標示名稱)：

- Backpack (Fuel Tank)
- GasTank (Energy Cell)
- TopLeftBody (Rover Enclosure)
- Nose (Docking Portal)
- LeftTwirler (External Sensor)

請注意，這些物件都具有操作處理常式，如第 4 課中所述。 透過使用操作處理常式，使用者將能抓住並操作物件。 同時請注意，[two handed manipulation type] \(兩手操作類型\) 設定已設定為 [move and rotate] \(移動和旋轉\)。 這僅會允許使用者移動物件，而不會讓他們變更其大小；此為組成應用程式的所需功能。
此外，遠方操作已被取消選取，以僅允許與小艇組件直接互動。

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

組件組立示範指令碼 (如上所示) 是管理要由使用者放置到登月小艇上之物件的指令碼。 

[Object To Place] \(要放置的物件\) 欄位是所選取的轉換項目 (針對上面的影像則為 backpack/fuel tank)，搭配其能連線的物件。 

[Near Distance] \(近距離\) 和 [Far Distance] \(遠距離\) 設定負責決定物件會貼齊至定位或分離的距離。 例如，backpack/fuel tank 必須位於距離登月小艇 0.1 單位以內的位置才會貼齊至定位。 [Far Distance] \(遠距離\) 會設定物件要距離登月小艇多遠才會與其分離。 在此情況下，使用者的手必須抓住 backpack/fuel tank，並將它拖曳至距離登月小艇 0.2 單位的距離，才能將它從原本的定位移除。

[Tool Tip Object] \(工具提示物件\) 是場景中的工具提示標籤。 當物件貼齊至定位時，系統便會停用標籤。 

系統將會自動抓取音訊來源。 

### <a name="placement-hints-buttons"></a>放置提示按鈕
在[第 2 課](mrlearning-base-ch2.md)中，您已了解如何放置按鈕並設定它以變更項目色彩，或是在按下時播放音效等功能。 我們將會繼續使用那些原則來設定按鈕以切換放置提示。 

我們的目標是將按鈕設定為每當使用者按下放置提示按鈕時，它便會切換半透明放置提示的可見性。 

步驟 1：在已選取基底場景階層中的 Placement Hints 物件的同時，將登月小艇移至偵測程式面板中的空白 [runtime only] \(僅限執行階段\) 位置。 
 ![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) 步驟 2：按一下顯示 [no function] \(無功能\) 的下拉式清單。 移至 [TogglePlacementHints]，然後在該功能表底下，選取 [ToggleGameObjects()]。 [ToggleGameObjects()] 會將放置提示開啟和關閉，使它們會在按鈕被按下時變成可見或不可見。
 ![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a>設定重設按鈕

使用者可能會犯錯或意外地將物件丟到無法觸及的位置，或是只想要重設整個體驗。 重設按鈕將能提供重設體驗的能力。 

步驟 1：選取重設按鈕。 在基底場景中，它名為 "ResetRoundButton"。 

步驟 2：將登月小艇從基底場景階層中拖曳到偵測程式面板中 [button pressed] \(按下按鈕\) 底下的空白位置。
 ![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

步驟 3：選取顯示為 [no function] \(無功能\) 的下拉式功能表，然後暫留在 [LaunchLunarModule] 上方。 現在請選取 [resetModule ()]。

![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> 注意：您將會注意到 [GameObject.BroadcastMessage] 預設會被設定為 "ResetPlacement"。 這將會針對 RocketLauncher_Tutorial 的每個子物件廣播稱為 "ResetPlacement" 的訊息。 任何具有 "ResetPlacement()" 之方法的物件，都會重設其位置來回應該訊息。 

### <a name="launching-the-lunar-module"></a>發射登月小艇
在本章中，我們將會設定發射按鈕。 這能讓使用者按下按鈕，並將登月小艇發射到太空中。

步驟 1：選取發射按鈕 (它在基底場景中名叫 "LaunchRoundButton")。 將登月小艇拖曳到偵測程式面板中 [Touch End] \(觸控結束\) 底下的空白位置。
 ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) 步驟 2：選取顯示為 [no function] \(無功能\) 的下拉式功能表。 暫留在 [LaunchLunarModule] 上方並選取 [StopThruster()]。 這能讓使用者控制要提供給登月小艇的推力多寡。 
 ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG) 步驟 3：在 [ButtonPressed()] 底下，將登月小艇 (按一下，按住並拖曳) 加入至空白位置。 

步驟 4：按一下顯示為 [no function] \(無功能\) 的下拉式功能表，然後暫留在 [LaunchLunarModule] 上方並選取 [StartThruster()]。 
 ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG) 步驟 5：將音樂加入至登月小艇，使音樂會在火箭發射時播放。 若要這麼做，請將登月小艇拖曳到 [Button Pressed()] 底下的下一個空白位置。

步驟 6：選取顯示為 [no function] \(無功能\) 的下拉式功能表，然後暫留在 [AudioSource] 上方並選取 [PlayOneShot (AudioClip)]。 您可以自行探索包含在 MRTK 中的各種音效。 在此範例中，我們會使用 "MRTK_Gem"。
 ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)


### <a name="congratulations"></a>恭喜 
您已完整地設定好這個應用程式！ 現在當您開始進行遊戲時，便可以完整組立登月小艇、切換提示、發射登月小艇，以及重設以重新進行一遍。
