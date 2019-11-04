---
title: 快速入門教學課程-3。 建立使用者介面和設定混合現實工具組
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 6ce5d96e98fd5489632f942c9b9f4885a7aa1480
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437774"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3. 建立使用者介面和設定混合現實工具組 

在上一課中，您已瞭解混合現實工具組（MRTK）針對 HoloLens 2 啟動第一個應用程式所提供的一些功能。 在下一課中，您將學習如何建立和組織按鈕以及 UI 文字面板，並使用預設互動（觸控）與每個按鈕互動。 此外，您還會探索如何新增簡單的動作和效果，例如變更物件的大小、音效和色彩。 本課程模組將介紹有關修改 MRTK 設定檔的基本概念，從關閉[空間對應](spatial-mapping.md)網格視覺效果開始。 

## <a name="objectives"></a>目標

* 自訂和設定混合實境工具組設定檔
* 使用 UI 元素和按鈕與全息影像互動
* 基本的「手部追蹤」輸入和互動

## <a name="instructions"></a>指示

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>如何設定混合實境工具組設定檔 (變更空間感知顯示選項)
在本節中，您將瞭解如何藉由調整空間感知網格的顯示選項來自訂和設定預設的 MRTK 設定檔。 您可以遵循下列和在調整 MRTK 設定檔中的任何設定或值時相同的原則。

1. 從 BaseScene 階層中選取 [混合現實工具組（MRTK）]。 在 [偵測器] 面板中，尋找 Mixed Reality 工具組腳本，並選取使用中的設定檔，如下圖所示。 按兩下來加以開啟。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step1im.PNG)

>注意：根據預設，MRTK 設定檔是無法編輯的。 這些是您可以複製和自訂的預設設定檔範本。 有數個層級的自訂和設定檔。 因此，在設定一個或多個設定時，複製和自訂數個設定檔是標準作法。
>
>若要深入瞭解 MRTK 設定檔及其架構，請造訪[MRTK 檔](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html>)。

2. 建立一份預設設定檔來進行自訂。 若要複製預設設定檔，請按一下 [複製] & 自訂（請參閱影像）。 這會建立一份 MRTK 設定檔。 有了自己的 MRTK 設定檔後，您現在就能自訂此設定檔中的任何設定。 您也必須針對此設定檔下的任何其他設定檔，重複複製並自訂步驟，如後續步驟所述。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step2im.PNG)

3. 停用空間感知網格的顯示。 若要這樣做，請尋找空間感知系統設定，如下圖所示。 按一下 [空間感知] 系統設定檔右邊的 [複製] 按鈕，以可自訂的複本取代預設設定檔。 如果出現快顯視窗，請按下 [複製] 按鈕，如下圖中的第二個影像所示。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3im.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3bim.jpg)

4. 建立「預設混合實境空間網格觀察者」的自訂複本。 按一下 [Windows Mixed Reality 空間網格觀察者] 旁邊的向下箭號，以查看其他選項。 在這些選項中，您會看到呈現灰色的預設混合現實空間網格觀察者（無法編輯）。 您必須使用可自訂複本來取代此預設設定檔，以便能夠進行編輯。 按一下右側的按鈕（以綠色箭號標示）以複製複本。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step4im.PNG)

5. 接下來，您會將 [顯示選項] 的設定調整為 [遮蔽]。 這會使空間對應網格可見，但仍會隱藏空間對應網格背後的遊戲物件，也稱為遮蔽。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step5im.PNG)

>注意：雖然空間對應網格未顯示，但仍存在，而且您可以與它互動。 空間對應網格背後的任何全息影像（例如您可見牆後方的全息影像）將不會顯示，因為遮蔽設定。

恭喜！ 您方才已了解如何修改 MRTK 設定檔中的設定。 如您所見，若要修改 MRTK 設定，您必須建立預設設定檔複本，以便能夠加以編輯。 如果您想要使用新的設定建立設定檔，或者您可以回頭參考預設設定檔，則一律會有無法編輯的預設設定檔。 您可以調整的設定很多。 如需 MRTK 設定檔設定的完整參考，請參閱此處的 MRTK 文件： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html

### <a name="hand-tracking-gestures-and-interactable-buttons"></a>手部追蹤手勢和可互動的按鈕
在本節中，您將瞭解如何使用 [手動追蹤] 來按下 [pressable] 按鈕。

1. 從 [專案] 資料夾選取 [資產]。

2. 在搜尋列中輸入 "pressablebutton"。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step1im.PNG)

3. 將名為 "PressableButton" 的 Prefab (以藍色方塊表示) 拖曳至您的階層。 

   > 注意：如果您收到有關「匯入 TMP Essentials」的訊息，此時請將它匯入。 如果您的專案尚未包含 TMP Essentials，您可能需要在匯入 TMP Essentials 後重複此步驟，否則可能不會出現按鈕文字。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step3im.PNG)

4. 按兩下 [PressableButton 遊戲] 物件（現在應位於您的 BaseScene 階層中），以在場景中進行觀看，如下圖所示。 您的按鈕圖形可能會與下圖不同。 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step4im.PNG)

5. 從 [偵測器] 面板中，按一下 [新增事件]，為按鈕提供在推送時回應的事件。 在出現的選項中，選取下拉式功能表，然後選取 [InteractableOnPressReciever]。 在追蹤的手部按下按鈕時，這可讓按鈕回應按下事件。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step5im.PNG)

6. 在場景中新增立方體。 以滑鼠右鍵按一下 [階層] 區域，選取3D 物件，然後按一下 [Cube]。 現在，立方體應該會在您的顯示區域內。 它會非常大。 您可以調整座標（在 [階層] 區域中仍然選取 [Cube]）來減少大小。 將縮放值設定為 x = 0.1、y = 0.1 和 z = 0.1。 請務必讓立方體定位在場景中，將其置於可按按鈕附近，但不要與該按鈕重疊。 在下圖中，立方體的位置是 x = 0、y = 0.2 和 z = 1。 

   > 注意：一般而言，Unity 中的1個單位大致等同于實體世界中的1個計量。 但有例外狀況，例如，當物件是所縮放物件的子系時。
   
   ![MR213_BuildSettings](images/mrlearning-base-ch2-1step6ima.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-2step6imb.PNG)

7. 在此步驟中，您會設定讓立方體在使用者按下按鈕時變更色彩。 選取 [BaseScene] 功能表中的 [PressableButton]。 從 [偵測器] 面板的 [選取事件種類] 方塊底下，按一下 [+] 按鈕。 將 cube 從 [BaseScene] 功能表拖曳到 [僅限執行時間] 方塊中，如下圖所示

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7ima.PNG)

按一下顯示 [沒有函數] 的下拉式清單。 選取 [MeshRenderer]，然後選取 [材質材質]。 這可讓您在按下按鈕時變更材質。 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imb.PNG)

移至 [專案] 面板，並搜尋您想要變更的資料。 在 [專案] 索引標籤的搜尋列中輸入「青色」，您將使用此範例中的材料 MRTK_Standard_Cyan。 （MRTK 包含許多材質和色彩可供選擇）。將材質拖曳至 [MeshRenderer] 下方的方塊。 MRTK 材質可於 Assets>MixedRealityToolkit.SDK>StandardAssets>Materials 中找到。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step7imc.PNG)

此事件現在已設定好，因此在按下按鈕時，立方體便會根據您指定的材質變更色彩。 在此範例中，立方體會變更為青色。

8. 接下來，您會設定放開動作，以便在放開時，按鈕會回復為其預設色彩。 重複上述的步驟7。 但這次使用 OnRelease 事件而非 OnPress 事件，如下圖所示。

9.  在 [專案] 面板中，搜尋要在按鈕發行時預設為的 cube 材質。 在此情況下，我們選擇 [MRTK_Standard_LightGray]。 將材質拖曳到 [MeshRenderer] 欄位下方的方塊中。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step8im.PNG)

現在當按下按鈕時，它會變更為新的色彩 [青色]。 釋放按鈕時，它會變更回您指定的預設色彩（例如淺灰色）。按下畫面頂端的 [播放] 按鈕，在編輯器中試用，或部署至您的 HoloLens 2 進行測試。 若要深入瞭解在編輯器中的模擬，包括手動模擬，請閱讀[MRTK 的模擬檔頁面](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>)。 

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>使用 MRTK 的方格物件集合來建立按鈕面板

在本節中，您將瞭解如何使用 MRTK 的 GridObjectCollection 工具，將多個按鈕自動對齊整齊的使用者介面。

1. 複製上一節中的按鈕，直到您有五個按鈕為止。 有數種方式可以執行這項作業：
- 以滑鼠右鍵按一下按鈕，然後按一下 [複製]。 然後移至按鈕下方，再以滑鼠右鍵按一下，再按一下 [貼上]。 
- 以滑鼠右鍵按一下按鈕，然後按一下 [複製]。 
- 按一下 cube，然後按下鍵盤上的 Ctrl D，以使用鍵盤命令。

重複此動作，直到您有五個按鈕為止;請參閱下圖中的五個紅色箭號。

![Mrlearning Base Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. 將按鈕群組到空白的父遊戲物件底下。 若要在方格集合中具有按鈕，您必須將按鈕分組在一般父物件底下。 在 hiearachy 上按一下滑鼠右鍵，然後按一下 [建立空的]。 這會建立新的空白遊戲物件供您放入所有按鈕。 它會顯示為 gameObject。 以滑鼠右鍵按一下，並將它重新命名為 ButtonCollection。

![Mrlearning Base Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. 將所有按鈕移至新的集合。 若要這麼做，請選取階層中的所有五個按鈕物件，並將其全部拖曳到 [ButtonCollection 遊戲物件] 底下，如下圖所示。 提示：按住 Ctrl 鍵並選取專案，以選取多個專案。

![Mrlearning Base Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. 將 MRTK 的 Grid 物件集合元件新增至按鈕集合。 若要這麼做，請選取 [ButtonCollection] 父物件。 從 [偵測器] 面板中，按一下 [新增元件] 按鈕。 在搜尋列中搜尋 Grid 物件集合，並在清單中出現它時加以選取。

![Mrlearning Base Ch2 3Step4im](images/mrlearning-base-ch2-3step4im.PNG)

Grid 物件集合元件可讓您在整齊的資料列、資料行或方格中組織按鈕或任何一組物件。 這是 MRTK 所提供的其中一個建立區塊，可讓您快速且輕鬆地建立吸引人的使用者介面。

5. 設定方格物件集合。 若要確保所有按鈕都能面對使用者，請選取 [方向類型]。 然後選取 [臉部父系轉寄]，如下圖所示。 接下來，變更儲存格大小來設定按鈕間距。 針對儲存格寬度和儲存格高度，從0.12 個單位開始，以0.12 單元為單位，如下圖所示。 視所選的物件和按鈕資產而定，您可能需要調整這些值。 請確定 [資料列] 設定為1。 按一下 [更新集合]。 場景看起來會類似下圖。 


![Mrlearning Base Ch2 3Step5im](images/mrlearning-base-ch2-3step5im.PNG)

>注意：視子物件或父物件的方向而定，您可能需要在未來的專案中調整方向設定的不同。 根據集合中物件的大小，[儲存格寬度] 和 [儲存格高度] 欄位可能也需要以不同的方式定義。

### <a name="adding-text-into-your-scene"></a>在場景中新增文字

在本節中，您會了解如何在混合實境體驗中新增和編輯文字。 請遵循[此處](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation)的指示來確定您已在 Unity 中啟用 TextMeshPro (如果您還沒有這麼做)。

1. 選取 [ButtonCollection] 父物件，然後以滑鼠右鍵按一下集合。 展開下拉式功能表中的 [3D 物件]。 然後選取 [TextMeshPro-Text]。 您應該會在按鈕集合底下看到 TextMeshPro 物件，如下圖所示。

![Lesson2 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG)
![Lesson2 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)

2. 若要改善可讀性的文字大小和位置，請調整 [TextMeshPro] 元件中的 [字型大小] 欄位，以變更字型的大小。 您也需要調整矩形轉換位置和尺規，如下圖所示。 請參閱下列影像，以瞭解用於文字設定的值。 您可以隨意使用這些值做為起點，進一步改善文字欄位的大小和位置。

![第2課 Chapter4 步驟3](images/Lesson2_Chapter4_Step3.JPG)

3. 在 [偵測器] 面板的 [TextMeshPro] 元件的 [文字] 欄位中，如下所示。 輸入按鈕集合文字。 文字會出現在場景中，但會隱藏在按鈕和/或錯誤的大小後面。

![第2課 Chapter4 步驟 2](images/Lesson2_Chapter4_Step2.JPG)
![第2課 Chapter4 步驟 4](images/Lesson2_Chapter4_Step4.JPG)

4. 若要修改按鈕物件上的文字值，請按一下任何按鈕旁的箭號將其展開，然後流覽至 SeeItSayItLabel 物件。 流覽至 TextMeshPro，您可以在其中編輯按鈕的文字，如上述步驟所述。

![Lesson2 Chapter4 Step5](images/Lesson2_Chapter4_Step5.JPG)

## <a name="congratulations"></a>恭喜您
在這一課，您已瞭解如何複製、自訂和設定 MRTK 設定檔設定（也就是空間感知網格可見度）。您也已瞭解如何與按鈕互動，以在 HoloLens 2 上使用追蹤來觸發事件。 最後，您已了解如何使用 Unity 的 Text Mesh Pro 和 MRTK 的方格物件集合元件來建立簡單的 UI 介面。

[下一課： 4. 放置動態內容並使用解析器](mrlearning-base-ch3.md)

