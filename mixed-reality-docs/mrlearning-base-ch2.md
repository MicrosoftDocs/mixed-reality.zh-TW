---
title: MR 學習基底模組-使用者介面手動追蹤及混合實境工具組組態
description: 完成這個課程來了解如何在混合的實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合的實境，unity 教學課程 hololens
ms.openlocfilehash: 1800d36b7292b9cb53b09fdd4b9c4fb763d49e79
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730945"
---
# <a name="mr-learning-base-module---user-interface-hand-tracking-and-mixed-reality-toolkit-configuration"></a>MR 學習基底模組-使用者介面手動追蹤及混合實境工具組組態

上一課，您已了解一些 MRTK 所提供，啟動 HoloLens 2 的第一個應用程式的功能。 在下一課，您將學習如何建立並組織以及 UI 文字面板的按鈕，並使用預設互動 （觸控） 與每個按鈕互動。 此外，您還將探索加入簡單的動作和效果，例如變更大小、 音效和物件的色彩。 此模組將介紹如何修改 MRTK 設定檔，啟動與關閉空間網狀結構的視覺效果的基本概念。 

## <a name="objectives"></a>目標

* 自訂和設定混合實境工具組設定檔
* 互動使用的 UI 項目和按鈕全像投影
* 基本的手動追蹤輸入和互動

## <a name="instructions"></a>指示

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>如何設定混合實境工具組設定檔 （變更空間感知顯示選項）
在本節中您會了解如何自訂及設定預設的混合實境工具組設定檔，藉由調整 [顯示] 選項的空間感知網狀結構。 您可以遵循這些相同的原則適用於調整任何設定或 MRTK 設定檔中的值。

1. 混合實境工具組 (MRTK) 從階層中選取 「 BaseScene"。 在 [偵測器] 面板中，尋找 「 混合實境 Toolkit 指令碼 」 並選取 「 作用中設定檔 」 下, 圖所示。 按兩下以開啟它。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step1im.PNG)

>注意：根據預設，將無法編輯 MRTK 設定檔。 這些是您可以從中複製，及自訂的預設設定檔範本。 有數個層級的自訂與設定檔，因此標準做法是複製和自訂數個設定檔，設定一或多個設定時。
>
>若要深入了解 MRTK 設定檔和其架構，請造訪[MRTK 文件](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>)。

2. 建立一份預設的設定檔來自訂它。 若要複製的預設設定檔，按一下 」 複製和自訂 」 按鈕 （請見圖）。 這會建立一份 MRTK 設定檔。 使用您自己的 MRTK 設定檔的複本，您現在可以自訂此設定檔中的任何設定。 您也必須在任何其他的設定檔，這個設定檔，之下巢狀的重複複本/自訂的步驟，後續步驟中所述。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step2im.PNG)

3. 停用空間感知網狀結構的可見性。 若要這樣做，請尋找 [空間感知系統設定]，如圖所示。 按一下 「 複製 」 按鈕右邊的 「 空間感知系統設定檔 」 來取代預設的設定檔的可自訂的複本。 如果快顯視窗隨即出現，請按 「 複製 」 按鈕，在第二個圖中所示。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3im.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3bim.jpg)

4. 建立自訂預設混合實境空間 Mesh 觀察者的複本。 按一下 「 Windows 混合實境空間 Mesh 觀察者 」 以查看其他選項旁邊的向下箭號。 在這些選項中，您會看到 「 預設混合實境空間 Mesh 觀察者 」 會出現呈現灰色 （無法編輯）。 因此您可以編輯它，您必須以可自訂的複本取代此預設設定檔。 按一下右邊 （標示綠色箭頭） 按鈕來複製複本。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step4im.PNG)

5. 接下來，您將在其中調整說: 「 阻擋。 」 的 [顯示] 選項的設定 這可讓空間網格看不見，但仍然遊戲物件後方空間網狀結構 （這稱為的阻擋物。）

![MR213_BuildSettings](images/mrlearning-base-ch2-1step5im.PNG)

>注意：看不到空間對應網格，仍存在而您可以與它互動。 由於 occlusion 設定任何全像投影背後空間對應網格 （例如背後可見的牆上雷射） 將不會顯示。

恭喜您！ 您剛剛了解如何修改 MRTK 設定檔中的設定。 如您所見，若要修改 MRTK 設定您要建立的預設設定檔的複本，以便您可以編輯它們。 您一定會預設設定檔 （這是不能編輯） 若要返回以如果您想要使用新的設定，建立設定檔，或參閱回預設設定檔。 有許多您可以調整的設定。 如 MRTK 的設定檔的完整參考，請參閱 MRTK 這裡的文件： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html

### <a name="hand-tracking-gestures-and-interactable-buttons"></a>追蹤手勢和互動的按鈕
在本節中，您將學習如何使用追蹤來按下的 [互動] 按鈕的游標。

1. 從 [專案] 資料夾中，選取 「 資產 」。

2. 輸入在搜尋列中，「 pressablebutton。 」

![MR213_BuildSettings](images/mrlearning-base-ch2-2step1im.PNG)

3. 將名為"PressableButton"prefab （以藍色方塊表示） 拖曳到您的階層。 

   > 注意：如果您收到訊息的相關 「 匯入 TMP Essentials 」 請它匯入這一次。 如果 TMP Essentials 還沒有專案的一部分，您可能需要重複此步驟之後匯入 TMP Essentials，否則為按鈕文字可能不會出現。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step3im.PNG)

4. 按兩下 「 PressableButton 」 遊戲物件 （這現在應該位於 BaseScene 階層） 若要檢視您的場景，請在下面的影像 （按鈕圖形可能會出現不同於下圖） 中所示。 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step4im.PNG)

5. 在 [偵測器] 面板中，按一下 「 加入事件 」 事件，以推送時回應給按鈕。 在隨即出現選項中，選取下拉式選單。 選取 「 InteractableOnPressReciever。 」 這可讓按鈕已按下的事件追蹤的手按下按鈕時回應。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step5im.PNG)

6. 您可以將立方體加入場景。 以滑鼠右鍵按一下 [階層] 區域，選取 3D 物件，然後按一下 「 cube 」。 現在，cube 應該在您的顯示。 它會非常大，因此調整座標 （在"cube"已選取 [階層] 區域中） 來減少大小。 標尺值設定為 x = 0.1，y = 0.1 和 z = 0.1。 是確定位置附近 pressable 的按鈕，將它放入場景中的 cube，但不是重疊與按鈕。 在下圖中，cube 的位置是 x = 0，y = 0.2 和 z = 1。 

   > 注意：一般情況下，在 Unity 中的 1 個單位是大致上相當於在真實世界的 1 公尺。 沒有例外狀況，例如，當物件子系的縮放物件時。
   
   ![MR213_BuildSettings](images/mrlearning-base-ch2-1step6ima.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-2step6imb.PNG)

7. 在此步驟中您會設定來變更色彩，在按下按鈕時的 cube。 您可以選取 PressableButton"BaseScene 」 功能表中。 在 [偵測器] 面板中，在 [選取事件類型] 方塊中，按一下"+"按鈕。 拖曳至"cube"從"BaseScene 」 功能表 僅執行階段 方塊中，如下圖所示

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7ima.PNG)

按一下下拉式清單中，指出 「 沒有函式 」。 選取 「 MeshRenderer"，然後選取"材料 material"。 這可讓您按下按鈕時，變更資料。 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imb.PNG)

請移至 [專案] 面板，並在搜尋您想要將它變更為資料。 您要用於此範例中的資料 」 MRTK_Standard_Cyan"，找到以"青色 」 （MRTK 包含許多資料與可從中選擇的色彩）。 [專案] 索引標籤的搜尋列中輸入將資料拖曳至 「 MeshRenderer.material。 」 底下的方塊 MRTK 資料可在資產 > MixedRealityToolkit.SDK > StandardAssets > 的資料。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imbb.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step7imc.PNG)

此事件現在已設定，讓 cube 按下按鈕時，會變更根據您指定的材質的色彩。 在此範例中，cube 會變更為青色色。

8. 接下來您要設定發行動作，以便在版本中，按鈕會恢復為其預設色彩。 重複執行步驟 7 （上一個步驟），但這次使用 「 OnRelease 」 事件，而非"OnPress 」 事件，如下圖所示。

9.  在 專案 面板中，搜尋 按鈕時釋放的預設值之 cube 的資料 （在本例中，我們選擇 MRTK_Standard_LightGray。）將資料拖曳至 「 MeshRenderer.material"欄位下方的方塊。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step8im.PNG)

現在按下按鈕時，它應該將它變更為新的色彩 (例如青色) 在放開按鍵時它應該將它變更回您所指定的預設色彩 （例如，淺灰色。）按下 「 播放 」 按鈕，現在就試試看在編輯器中，或部署到您要測試的 HoloLens 2 在螢幕上方 ！ 若要深入了解在編輯器中模擬，包括讀取手動模擬[MRTK 的模擬文件頁面](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>)。 

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>建立使用 MRTK 的格線物件集合的按鈕面板

在本節中，您將學習如何自動對齊多個按鈕，到使用 MRTK GridObjectCollection 工具的簡潔使用者介面。

1. 除非您有 5 個按鈕，請重複上一節中的按鈕。 有數種方式可以執行這項操作：
- 按鈕上按一下滑鼠右鍵並按一下 「 複製 」，然後移至按鈕下方並再次以滑鼠右鍵按一下，按一下 「 貼上 」。 
- 以滑鼠右鍵按一下按鈕，按一下 「 重複 」。 
- 按一下 cube 並按下的 「 ctrl D"鍵盤上使用鍵盤命令。

除非您有 5 個 （請參閱下面的影像中的 5 個紅色箭號） 的總按鈕重複此步驟。

![Mrlearning 基底 Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. 空白的父遊戲物件底下按鈕群組。 為了方格集合中有 [] 按鈕，您必須將您常用的父物件底下的按鈕。 Hiearachy 中以滑鼠右鍵按一下並按一下 [建立空白]。 這會建立要將所有按鈕都放在新的空白遊戲物件。 它會顯示為 「 gameObject。 」 以滑鼠右鍵按一下，並將它重新命名為"ButtonCollection。 」

![Mrlearning 基底 Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. 將所有按鈕都移至新的集合。 是，在您 heirarch 選取全部五個按鈕物件並拖曳它們全部都是在 「 ButtonCollection 」 遊戲物件，如下圖所示。 提示： 所選取項目時按住 ctrl 鍵選取多個項目。

![Mrlearning 基底 Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. MRTK 的 「 方格物件的集合 」 將元件新增至按鈕集合。  若要這樣做，請選取 「 ButtonCollection"父物件並在偵測器 面板中，按一下 新增元件 按鈕。 然後在 [搜尋] 列中搜尋 「 方格物件的集合 」，它必須出現在清單中選取它。

![Mrlearning 基底 Ch2 3Step4im](images/mrlearning-base-ch2-3step4im.PNG)

格線物件集合的元件可讓您將按鈕或任何組織的一組很棒的資料列、 資料行或方格中的物件。 這是您提供快速且簡單的方式，來建立美觀的使用者介面 MRTK 所提供的建置組塊。

5. 設定格線物件集合。 若要確保所有按鈕所面臨的使用者，選取 「 引導類型 」，然後按 「 面臨父轉寄 」 （如圖所示。）接下來，將變更儲存格大小來設定您的按鈕之間的間距。 開始 gt;=0.12 單位 gt;=0.12 的單位儲存格的寬度和儲存格的高度，如下圖所示。 您可能需要調整這些值，根據選擇的物件/按鈕資產。 請確定 「 資料列 」 設定為 1。 然後按一下 [更新集合]，並在場景應該看起來如下圖。 


![Mrlearning 基底 Ch2 3Step5im](images/mrlearning-base-ch2-3step5im.PNG)

>注意：根據父物件之子物件的方向，您可能需要調整設定以不同的方式，在未來的專案中的方向。 儲存格的寬度和儲存格的高度欄位可能也需要以不同的方式，定義您的集合中物件的大小而定。

### <a name="adding-text-into-your-scene"></a>將文字新增至場景

在本節中，您將學習如何新增和編輯您的混合的實境體驗的文字。 如果您還沒有這麼做，請確定您有啟用在 Unity 中的指示 TextMeshPro[此處](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation)。

1. 選取 「 ButtonCollection"父物件，並以滑鼠右鍵按一下集合。 在下拉式功能表中，展開 「 3D 物件 」，然後選取"TextMeshPro-Text"。 下圖所示，您應該看到按鈕集合中下, 一個 TextMeshPro 物件。

![第 2 課 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG)
![第 2 課 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)

2. 在 TextMeshPro 元件的文字欄位中 （位於 [偵測器] 面板中，如下所示），輸入 「 按鈕集合文字 」。 文字會出現在場景，但它會隱藏之後的按鈕和/或大小不正確。

![第 2 課 Chapter4 步驟 2](images/Lesson2_Chapter4_Step2.JPG)

3. 若要改善的文字大小和位置，以增加可讀性，調整 「 字型大小 」 元件中欄位 TextMeshPro 若要變更字型的大小。 您也必須調整"Rect Transform"位置和小數位數，如下圖所示。 請參閱下方的映像，我們的文字設定的值，並歡迎您使用這些值做為起點要進一步改善的大小和位置的文字欄位。

![第 2 課 Chapter4 Step3](images/Lesson2_Chapter4_Step3.JPG)
![第 2 課 Chapter4 步驟 4](images/Lesson2_Chapter4_Step4.JPG)

5. 若要修改的按鈕物件上的文字值，請按一下即可展開它，並瀏覽至"SeeItSayItLabel 」 物件的任何按鈕旁的箭號，然後瀏覽至"TextMeshPro 」，您可以在其中您如上述步驟中所述的按鈕來編輯文字。

![第 2 課 Chapter4 步驟 5](images/Lesson2_Chapter4_Step5.JPG)

### <a name="congratulations"></a>恭喜您
在這一課，您已了解如何複製、 自訂和設定 MRTK 設定檔設定 （亦即，空間感知網狀結構的可見度。）您也學到如何使用追蹤的指針 HoloLens 2 上的觸發程序事件的按鈕與互動。 最後，您已了解如何建立簡單的 UI 介面，使用 Unity 的文字 Mesh Pro MRTK 的格線物件集合的元件。

[下一課：動態內容的位置和解](mrlearning-base-ch3.md)

