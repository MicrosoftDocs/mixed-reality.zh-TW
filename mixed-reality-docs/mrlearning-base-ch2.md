---
title: MR 學習基本模組 - 使用者介面、手部追蹤及混合實境工具組設定
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 1800d36b7292b9cb53b09fdd4b9c4fb763d49e79
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730945"
---
# <a name="mr-learning-base-module---user-interface-hand-tracking-and-mixed-reality-toolkit-configuration"></a>MR 學習基本模組 - 使用者介面、手部追蹤及混合實境工具組設定

在上一堂課，您已藉由啟動 HoloLens 2 的第一個應用程式來了解 MRTK 所必須提供的一些功能。 接下來這一堂課，您將了解如何建立和組織按鈕以及 UI 文字面板，並且會使用預設互動方式 (觸控) 來與每個按鈕互動。 此外，您還會探索如何新增簡單的動作和效果，例如變更物件的大小、音效和色彩。 此模組將會從關閉空間網格的視覺效果來開始，介紹一些如何修改 MRTK 設定檔的基本概念。 

## <a name="objectives"></a>目標

* 自訂和設定混合實境工具組設定檔
* 使用 UI 元素和按鈕來與全像投影互動
* 基本的「手部追蹤」輸入和互動

## <a name="instructions"></a>指示

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>如何設定混合實境工具組設定檔 (變更空間感知顯示選項)
在本節中，您將會藉由調整空間感知網格的顯示選項，來了解如何自訂和設定預設的混合實境工具組設定檔。 您可以遵循下列和在調整 MRTK 設定檔中的任何設定或值時相同的原則。

1. 從 [BaseScene] 階層中選取 [混合實境工具組 (MRTK)]。 在偵測程式面板中尋找 [混合實境工具組指令碼]，然後選取 [作用中設定檔]，如下圖所示。 按兩下來加以開啟。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step1im.PNG)

>注意：根據預設，您無法編輯 MRTK 設定檔。 這些是可供您複製和自訂的預設設定檔範本。 自訂和設定檔有數個層級，因此在設定一或多個設定時，標準做法是複製和自訂數個設定檔。
>
>若要深入探索 MRTK 設定檔和其架構，請瀏覽 [MRTK 文件](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>)。

2. 建立一份預設設定檔來進行自訂。 若要複製預設設定檔，請按一下 [複製和自訂] 按鈕 (見下圖)。 這會建立一份 MRTK 設定檔。 有了自己的 MRTK 設定檔後，您現在就能自訂此設定檔中的任何設定。 您還必須針對此設定檔底下的任何其他巢狀設定檔重複執行複製/自訂步驟，如後續步驟所述。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step2im.PNG)

3. 停用空間感知網格的顯示。 若要這樣做，請尋找 [空間感知系統設定]，如下圖所示。 按一下 [空間感知系統設定檔] 右邊的 [複製] 按鈕，以使用可自訂複本來取代預設設定檔。 如果出現快顯視窗，請按 [複製] 按鈕，如下面第二個圖所示。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3im.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3bim.jpg)

4. 建立「預設混合實境空間網格觀察者」的自訂複本。 按一下 [Windows 混合實境空間網格觀察者] 旁邊的向下箭號來查看其他選項。 在這些選項中，您會看到 [預設混合實境空間網格觀察者] 呈現灰色 (無法編輯)。 您必須使用可自訂複本來取代此預設設定檔，以便能夠進行編輯。 按一下右邊的按鈕 (標有綠色箭頭) 來複製複本。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step4im.PNG)

5. 接下來，您會將 [顯示選項] 的設定調整為 [遮蔽]。 這可讓您無法看見空間網格，但仍將遊戲物件隱藏在空間網格後方 (這稱為遮蔽)。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step5im.PNG)

>注意：雖然您看不見空間對應網格，但其仍然存在，而且可與之互動。 由於有遮蔽設定，您將看不見空間對應網格背後的全像投影 (例如，可見牆背後的全像投影)。

恭喜！ 您方才已了解如何修改 MRTK 設定檔中的設定。 如您所見，若要修改 MRTK 設定，您必須建立預設設定檔複本，以便能夠加以編輯。 您一定會有在想要建立有新設定的設定檔或回頭參閱預設設定檔時能夠回頭使用的預設設定檔 (無法加以編輯)。 您可以調整的設定很多。 如需 MRTK 設定檔設定的完整參考，請參閱此處的 MRTK 文件： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html

### <a name="hand-tracking-gestures-and-interactable-buttons"></a>手部追蹤手勢和可互動的按鈕
在本節中，您會了解如何使用手部追蹤來按可互動按鈕。

1. 從 [專案] 資料夾中選取 [資產]。

2. 在搜尋列中輸入 "pressablebutton"。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step1im.PNG)

3. 將名為 "PressableButton" 的 Prefab (以藍色方塊表示) 拖曳至您的階層。 

   > 注意：如果您收到關於「匯入 TMP Essentials」的訊息，請在此時匯入。 如果 TMP Essentials 還未成為專案一部分，請在匯入 TMP Essentials 之後重複此步驟，否則按鈕文字可能不會出現。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step3im.PNG)

4. 按兩下 "PressableButton" 遊戲物件 (現在應該位於 BaseScene 階層中) 以在您的場景中進行檢視，如下圖所示 (您出現的按鈕圖形可能會和下圖不同)。 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step4im.PNG)

5. 在偵測程式面板中，按一下 [新增事件] 來為按鈕提供要在使用者按下時回應的事件。 在出現的選項中，選取下拉式功能表。 選取 [InteractableOnPressReciever]。 在追蹤的手部按下按鈕時，這可讓按鈕回應按下事件。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step5im.PNG)

6. 在場景中新增立方體。 以滑鼠右鍵按一下階層區域、選取 3D 物件，然後按一下 [立方體]。 現在，立方體應該會在您的顯示區域內。 其大小會非常大，因此請調整座標 (在「立方體」仍於階層區域中保持選取時) 來減少大小。 將縮放值設定為 x = 0.1、y = 0.1 和 z = 0.1。 請務必讓立方體定位在場景中，將其置於可按按鈕附近，但不要與該按鈕重疊。 在下圖中，立方體的位置是 x = 0、y = 0.2 和 z = 1。 

   > 注意：一般情況下，Unity 中的 1 個單位會大致等於真實世界的 1 公尺。 但有例外狀況，例如，當物件是所縮放物件的子系時。
   
   ![MR213_BuildSettings](images/mrlearning-base-ch2-1step6ima.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-2step6imb.PNG)

7. 在此步驟中，您會設定讓立方體在使用者按下按鈕時變更色彩。 在 [BaseScene] 功能表中選取 [PressableButton]。 在偵測程式面板中，按一下 [選取事件類型] 方塊底下的 [+] 按鈕。 將立方體從 [BaseScene] 功能表拖曳至 [僅執行階段] 方塊，如下圖所示

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7ima.PNG)

按一下名為 [無功能] 的下拉式清單。 選取 [MeshRenderer]，然後選取 [Material material]。 這可讓您在按下按鈕時變更材質。 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imb.PNG)

移至 [專案] 面板，並搜尋想要在變更後使用的材質。 在此範例中，您會使用 "MRTK_Standard_Cyan" 材質，若要尋找，請在 [專案] 索引標籤的搜尋列中輸入「青色」 (MRTK 包含許多材質和色彩可供選擇)。將材質拖曳至 [MeshRenderer.material] 底下的方塊。 MRTK 材質可於 Assets>MixedRealityToolkit.SDK>StandardAssets>Materials 中找到。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imbb.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step7imc.PNG)

此事件現在已設定好，因此在按下按鈕時，立方體便會根據您指定的材質變更色彩。 在此範例中，立方體會變更為青色。

8. 接下來，您會設定放開動作，以便在放開時，按鈕會回復為其預設色彩。 重複執行步驟 7 (上一個步驟)，但這次使用 [OnRelease] 事件而非 [OnPress] 事件，如下圖所示。

9.  在 [專案] 面板中，搜尋要在立方體放開按鈕時作為預設值的材質 (在本例中，我們選擇 MRTK_Standard_LightGray)。將材質拖曳至 [MeshRenderer.material] 欄位下面的方塊中。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step8im.PNG)

現在當按下按鈕時，其應該會變更為新的色彩 (例如青色)，而在放開按鈕時，其應該會變更回您所指定的預設色彩 (例如，淺灰色)。請按下畫面頂端的 [播放] 按鈕以在編輯器中試用，或部署至 HoloLens 2 來進行測試！ 若要深入了解如何在編輯器中進行模擬 (包括手部模擬)，請閱讀 [MRTK 的模擬文件頁面](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>)。 

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>使用 MRTK 的方格物件集合來建立按鈕面板

在本節中，您會了解如何使用 MRTK 的 GridObjectCollection 工具，讓多個按鈕自動排列成整齊的使用者介面。

1. 複製上一節的按鈕直到您有 5 個按鈕。 有數種方式可以執行這項作業：
- 對按鈕按一下滑鼠右鍵，再按一下 [複製]，然後往下移至按鈕下方，於再次按一下滑鼠右鍵後按一下 [貼上]。 
- 對按鈕按一下滑鼠右鍵，然後按一下 [複製]。 
- 按一下立方體並按下鍵盤上的 "ctrl D"，來使用鍵盤命令。

重複此步驟直到您總共有 5 個按鈕 (請見下圖中的 5 個紅色箭號)。

![Mrlearning Base Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. 將按鈕群組到空白的父遊戲物件底下。 為了讓按鈕進入方格集合中，您必須將按鈕群組到常用的父物件底下。 在階層中按一下滑鼠右鍵，然後按一下 [建立空白]。 這會建立新的空白遊戲物件供您放入所有按鈕。 其會顯示為 "gameObject"。 對其按一下滑鼠右鍵並加以重新命名為 "ButtonCollection"。

![Mrlearning Base Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. 將所有按鈕移至新的集合。 若要這麼做，請將階層中的五個按鈕物件全都選取，並將其全都拖曳至 "ButtonCollection」" 物件底下，如下圖所示。 提示：按住 Ctrl 鍵同時選取項目，即可選取多個項目。

![Mrlearning Base Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. 將 MRTK 的「方格物件集合」元件新增至按鈕集合。  若要這樣做，請選取 "ButtonCollection" 父物件，並在偵測程式面板中，按一下 [新增元件] 按鈕。 然後在搜尋列中搜尋「方格物件集合」，並於出現在清單時加以選取。

![Mrlearning Base Ch2 3Step4im](images/mrlearning-base-ch2-3step4im.PNG)

「方格物件集合」元件可讓您將按鈕或任何一組物件組織在整齊的資料列、資料行或方格中。 這是 MRTK 所提供的其中一個建置組塊，可讓您以快速且簡單的方式建立美觀的使用者介面。

5. 設定方格物件集合。 為了確保所有按鈕都會面對使用者，請依序選取 [方位類型] 和 [向前面向父系] (如下圖所示)。接下來，變更儲存格大小來設定按鈕間距。 從 [儲存格寬度] 和 [儲存格高度] 為 0.12 單位乘 0.12 單位來開始，如下圖所示。 您可能需要根據所選擇的物件/按鈕資產來調整這些值。 請確定 [資料列] 設定為 1。 然後按一下 [更新集合]，然後場景應該會看起來如下圖。 


![Mrlearning Base Ch2 3Step5im](images/mrlearning-base-ch2-3step5im.PNG)

>注意：根據子物件或父物件的方向，您可能需要在未來的專案中以不同的方式調整方向設定。 根據集合中物件的大小，[儲存格寬度] 和 [儲存格高度] 欄位可能也需要以不同的方式定義。

### <a name="adding-text-into-your-scene"></a>在場景中新增文字

在本節中，您會了解如何在混合實境體驗中新增和編輯文字。 請遵循[此處](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation)的指示來確定您已在 Unity 中啟用 TextMeshPro (如果您還沒有這麼做)。

1. 選取 [ButtonCollection] 父物件，並以滑鼠右鍵按一下集合。 在下拉式功能表中展開 [3D 物件]，然後選取 [TextMeshPro - 文字]。 您應該會在按鈕集合底下看到 TextMeshPro 物件，如下圖所示。

![Lesson2 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG)
![Lesson2 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)

2. 在 TextMeshPro 元件的 [文字] 欄位中 (位於偵測程式面板中，如下圖所示)，輸入「按鈕集合文字」。 文字便會出現在場景中，但會隱藏在按鈕之後且/或大小會不正確。

![Lesson2 Chapter4 Step2](images/Lesson2_Chapter4_Step2.JPG)

3. 若要改善文字大小和位置以方便閱讀，請調整 TextMeshPro 元件中的 [字型大小] 欄位，以變更字型的大小。 您也必須調整 [矩形轉換] 的位置和刻度，如下圖所示。 請參閱下圖來了解我們的文字設定所使用的值，並歡迎您使用這些值作為起點，來進一步改善您文字欄位的大小和位置。

![Lesson2 Chapter4 Step3](images/Lesson2_Chapter4_Step3.JPG)
![Lesson2 Chapter4 Step4](images/Lesson2_Chapter4_Step4.JPG)

5. 若要修改按鈕物件上的文字值，請按一下任何按鈕旁的箭號來加以展開，並瀏覽至 [SeeItSayItLabel] 物件，然後瀏覽至 [TextMeshPro] 以在其中編輯按鈕的文字，如上述步驟所述。

![Lesson2 Chapter4 Step5](images/Lesson2_Chapter4_Step5.JPG)

### <a name="congratulations"></a>恭喜您
在這一堂課中，您已了解如何複製、自訂和設定 MRTK 設定檔設定 (亦即，空間感知網格的顯示)。您也已經了解如何在 HoloLens 2 上使用追蹤的手部來與按鈕互動以觸發事件。 最後，您已了解如何使用 Unity 的 Text Mesh Pro 和 MRTK 的方格物件集合元件來建立簡單的 UI 介面。

[下一課：動態內容放置和解算器](mrlearning-base-ch3.md)

