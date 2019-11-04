---
title: 快速入門教學課程-6。 探索先進的輸入選項
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: bb6aa620cebfda74b0b6b5f6ca04e1eeb68d9c7b
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438452"
---
# <a name="6-exploring-advanced-input-options"></a>6. 探索 advanced 輸入選項

在本教學課程中，會探索 HoloLens 2 的數個先進的輸入選項，包括使用語音命令、移動流覽手勢和眼睛追蹤。 

## <a name="objectives"></a>目標

- 使用語音命令和關鍵字觸發事件
- 使用追蹤的手平移材質和3D 物件
- 利用 HoloLens 2 眼追蹤功能來選取物件

## <a name="instructions"></a>指示

### <a name="enabling-voice-commands"></a>啟用語音命令

在本節中，會執行兩個語音命令。 首先，您可以藉由說「切換診斷」來引進切換畫面播放速率診斷面板的功能。 第二，會探索使用語音命令來播放音效的功能。 負責設定語音命令的 MRTK 設定檔和設定會先進行審核。 

1. 在 [基底場景階層] 中，選取 [MixedRealityToolkit]。 在 [偵測器] 面板中，向下流覽至 [輸入系統設定]。 按兩下以開啟 [輸入系統設定檔]。 複製輸入系統設定檔，使其可供編輯，如我們在[第1課](mrlearning-base-ch1.md)所學 

在輸入系統設定檔中，有各種不同的設定。 針對語音命令，請選取 [語音命令設定]。 

![Lesson5 Chapter1 Step2im](images/Lesson5_Chapter1_step2im.PNG)

2. 複製語音命令設定檔，使其可供編輯，如我們在[第1課](mrlearning-base-ch1.md)所學。 按兩下 [語音] 命令設定檔，您會在其中看到一系列設定。 如需這些設定的完整說明，請參閱[MRTK 語音檔](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>)。 

>注意：根據預設，一般行為會自動啟動。 如有需要，您可以將此變更為手動啟動。 但在此範例中，請將它保持在自動啟動。 MRTK 隨附數個預設語音命令，例如功能表、切換診斷和切換 profiler。 我們將使用關鍵字「切換診斷」，以開啟和關閉診斷的畫面播放速率計數器。 我們還將在下列步驟中加入新的語音命令。
>
> ![Lesson5 Chapter1 Noteim](images/Lesson5_chapter1_noteim.PNG)

3. 加入新的語音命令。 若要這樣做，請按一下 [+ 新增語音命令] 按鈕。 您會看到出現在現有語音命令清單下方的新行。 輸入您想要使用的語音命令。 在此範例中，使用「播放音樂」命令。

>秘訣：您也可以設定語音命令的 keycode。 這可讓語音命令在按下鍵盤按鍵時觸發事件。    

4. 新增回應語音命令的功能。 選取基底場景階層中沒有附加任何其他輸入腳本的任何物件（例如，沒有操作處理常式）。 在 [偵測器] 面板中，按一下 [新增元件]。 輸入「語音輸入處理常式」並加以選取。

   ![Lesson5 Chapter1.txt Step4im](images/Lesson5_chapter1_step4im.PNG)

   

根據預設，您會看到兩個核取方塊。 其中一個是 [需要焦點] 核取方塊。 因此，只要您是以光線眼、列印頭、控制器眼或手注視的方式來指向物件，就會觸發語音命令。 取消核取此核取方塊，讓使用者不需要查看物件即可使用語音命令。

5. 新增回應語音命令的功能。 若要這麼做，請在語音輸入處理常式中按一下 [+] 按鈕，然後選取您想要回應的關鍵字。

   > 注意：根據您在上一個步驟中編輯的設定檔，會填入這些關鍵字。

![Lesson5 Chapter1 Step5im](images/Lesson5_chapter1_step5im.PNG)

6. 在 [關鍵字] 旁，您會看到一個下拉式功能表。 選取 [切換診斷]，如此一來，每當使用者說出「切換診斷」片語時，它就會觸發動作。 請注意，您可能需要按下旁邊的箭號來展開元素0。

![Lesson5 Chapter1 Step6im](images/Lesson5_chapter1_step6im.PNG)

7. 新增診斷示範控制項腳本，以切換開啟和關閉的畫面播放速率計數器診斷。 若要這麼做，請按 [新增元件]，搜尋診斷示範控制項腳本，並從功能表中新增它。 此腳本可以加入至任何物件。 但為了簡單起見，我們會將它新增至與語音輸入處理常式相同的物件。 

   > 注意：此腳本只包含在這些模組中，而不是原始 MRTK。

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step7im.PNG)

8. 在語音輸入處理常式中加入新的回應。 若要這麼做，請按一下 [回應（）] 底下的 [+] 按鈕（以上圖中的綠色箭號標記）。

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step8.PNG)

9. 將具有診斷示範控制項腳本的物件拖曳至您剛才在步驟8中建立的新回應。
    ![Lesson5 Chapter1 Step9im](images/Lesson5_chapter1_step9im.PNG)

10. 選取 [沒有函式] 下拉式清單，然後選擇 [診斷示範控制項]。 然後選取 "On 切換診斷（）" 函式，此函式會開啟和關閉您的診斷。  ![Lesson5 Chapter1 Step10im](images/Lesson5_chapter1_step10im.PNG)
    
> 請注意，在建立您的裝置之前，您必須啟用 mic 設定。 若要這樣做，請按一下 [檔案] 並移至 [組建設定]、[播放程式設定]，並確定已設定麥克風功能。

接下來，使用顆 octa 物件新增播放音訊檔案的功能。 回想一下[第4課](mrlearning-base-ch4.md)，已新增播放音訊剪輯以觸及顆 octa 物件的能力。 我們將針對我們的音樂語音命令使用相同的音訊來源。

11. 選取 [基底場景] 階層中的 [顆 octa] 物件。

12. 新增另一個語音輸入處理常式（重複步驟4和5），但使用顆 octa 物件。 

13. 請新增 [播放音樂語音] 命令，而不是從步驟6新增 [切換診斷語音] 命令，如下圖所示。
    
     ![Lesson5 Chapter1 Step13im](images/Lesson5_chapter1_step13im.PNG)
    
    
    
14. 如同步驟8和9，加入新的回應，並將顆 octa 物件拖曳至空白回應位置。

15. 選取顯示 [沒有函數] 的下拉式功能表。 然後選取 [音訊來源]，後面接著 [PlayOneShot （AudioClip）]。

![Lesson5 Chapter1 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. 在此範例中，我們將使用[第4課](mrlearning-base-ch4.md)的相同音訊剪輯。 移至您的 [專案] 面板，搜尋 "MRTK_Gem" 音訊剪輯，並將它拖曳到音訊來源位置，如下圖所示。 現在，您的應用程式會回應語音命令「切換診斷」，以切換 [畫面播放速率計數器] 面板並播放音樂來播放 MRTK_Gem 的歌曲。
     ![Lesson5 Chapter1 Step16im](images/Lesson5_chapter1_step16im.PNG)


### <a name="the-pan-gesture"></a>平移手勢 

在本節中，您將瞭解如何使用平移手勢。 這適用于使用手指或手來滾動內容的捲軸。 您也可以使用平移手勢來旋轉物件、迴圈流覽3D 物件的集合，甚至是滾動 2D UI。 我們也會學習如何使用平移手勢來扭曲材質，以及如何移動3D 物件的集合。

1. 建立四邊形。 在您的基底場景階層中，以滑鼠右鍵按一下 [3D 物件]，然後選取 [四個]。

![Lesson5 Chapter2 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. 適當地重新置放四個。 在我們的範例中，我們將 x = 0、y = 0 和 z = 1.5 遠離相機，以取得 HoloLens 2 的舒適位置。

   > 注意：如果四個區塊或位於先前課程中的任何內容前方，請務必將其移動，使其不會封鎖任何其他物件。

3. 將材質套用至四邊形。 這份材料將是我們將透過移動流覽手勢來進行的動作。 

![Lesson5 Chapter2 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. 在 [專案] 面板的 [搜尋] 方塊中，輸入「pan 內容」。 將該材料拖曳到場景中的四個。 

> 注意： Pan 內容材料不會包含在 MRTK 中，而是此模組的資產套件中的資產，如先前課程中所匯入。 

> 注意：當您新增 [pan] 內容時，可能會看起來已伸展。 您可以藉由調整四邊形大小的 x、y 和 z 值來解決此問題，直到您對它的外觀感到滿意為止。

若要使用平移手勢，您需要在物件上使用碰撞器。 您可能會看到四邊形已經有一個網格碰撞器。 然而，網格碰撞器並不理想，因為它非常薄並且難以選取。 我們建議用方塊碰撞器取代網格碰撞器。

5. 以滑鼠右鍵按一下 [偵測器] 面板上 [四個] 的網格碰撞。 然後按一下 [移除元件] 將它移除。
    ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)
6. 現在，按一下 [新增元件] 並搜尋「方塊碰撞器」，以新增方塊碰撞器。 預設新增的方塊碰撞，仍然太精簡，因此請按一下 [編輯碰撞] 按鈕進行編輯。 按下它時，可以使用 x、y 和 z 值或場景編輯器中的元素調整大小。 針對我們的範例，我們希望將方塊碰撞器延伸到四邊形後面。 在場景編輯器中，從後面向外拖曳方塊碰撞器 (請參閱下圖)。 這可讓使用者不只使用手指，而是要滾動的全手勢。 
    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)
7. 使其具互動性。 因為我們想要直接與四個程式互動，所以我們想要使用我們在第4課用來從顆 octa 物件播放音樂的近距離互動 Touchable 元件。 按一下 [新增元件]，搜尋「接近互動 touchable」並加以選取，如下圖所示。 

8. 新增可辨識平移手勢的功能。 按一下 [新增元件]，然後輸入「手動互動 pan」。 您可以在手動光線 (允許您從遠處平移) 和食指之間進行選擇。 針對此範例，將其保留為食指。 
    ![Lesson5 Chapter2 Step7 8Im](images/Lesson5_chapter2_step7-8im.PNG)

![Lesson5 Chapter2 Step8im](images/Lesson5_chapter2_step8im.PNG)

9. 在 [手動互動] 移動流覽腳本中，鎖定 [水準] 和 [鎖定垂直] 核取方塊會分別鎖定移動。 包裝材質設定會使材質（材質對應）遵循使用者的移動流覽動作。 在此範例中，您將會勾選該方塊。 也有作用中的速度，如果未核取，則移動流覽手勢將無法執行。 也請核取此方塊。 現在您會有一個啟用 pan 的四個。

   

   接下來，我們將學習如何平移 3D 物件。 

10. 以滑鼠右鍵按一下 [四個物件]，選取 [3D 物件]，然後按一下 [Cube]。 縮放立方體，使其大致為 x = 0.1、y = 0.1 且 z = 0.1。 以滑鼠右鍵按一下 cube，然後按下 [複製]，或按 [控制]/[命令 D]，將 cube 複製三次。 您的場景看起來應該如下圖所示。

![Lesson5 Chapter2 Step10im](images/Lesson5_chapter2_step10im.PNG)







11. 再次選取 [4]，然後在 [手互動] pan 腳本底下，將 [移動流覽動作] 設定為每個 cube。 在 [移動流覽事件接收器] 底下，我們想要指定接收事件的物件數目。 因為有四個 cube，請輸入 "4"，然後按 Enter 鍵。 應該會出現四個空白欄位。


![Lesson5 Chapter2 Step11im](images/Lesson5_chapter2_step11im.PNG)



12. 將每個 cube 拖曳到每個空的元素位置。
     ![Lesson5 Chapter2 Step12im](images/Lesson5_chapter2_step12im.PNG)
    
13. 按住 control/command 並選取每個物件，以將 Move with Pan 腳本新增至所有 cube。 從 [偵測器] 面板中，按一下 [新增元件]，並搜尋「使用平移移動」。 按一下腳本，它就會加入至每個 cube。 現在，3D 物件將會隨著您的移動流覽手勢移動。 如果在四邊形上移除網格渲染器，則現在應該有一個不可見的四邊形，您可以在其中平移 3D 物件的清單。

### <a name="eye-tracking"></a>眼球追蹤

在本節中，我們將探討如何在我們的示範中啟用眼睛追蹤。 當您的眼睛 gazed 時，我們會慢慢旋轉3D 功能表項目。 當選取注視項目時，我們也會觸發有趣的效果。

1. 請確定已正確設定 MRTK 設定檔。 在撰寫本文時，混合實境工具組設定檔設定根據預設不包含眼球追蹤功能。 若要新增眼睛追蹤功能，請依照[混合現實工具組檔](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-the-mrtk-profiles-required-for-eye-tracking  )中所述的「設定眼睛追蹤所需的 MRTK 設定檔」一節中的指示進行。 請遵循上述檔連結中的任何剩餘步驟，確定已正確設定眼睛追蹤，包括在 GazeProvider （連接至相機的元件）中啟用眼睛追蹤，以及在 Unity 編輯器中啟用紅眼追蹤。 請注意，MRTK 的未來版本可能會包含預設的眼睛追蹤。

    上述連結提供下列事項的簡短指示：

    - 建立要在 MRTK 設定檔中使用的眼睛 Data Provider
    - 在 Gaze Provider 中啟用眼球追蹤
    - 在編輯器中設定眼睛追蹤模擬
    - 編輯 Visual Studio 解決方案的功能，以允許在建置的應用程式中進行眼球追蹤

2. 將眼球追蹤目標元件新增至目標物件。 若要讓物件回應眼睛眼事件，我們必須在每個想要使用眼睛互動的物件上新增 EyeTrackingTarget 元件。 將此元件新增至作為方格集合一部分之九個 3D 物件中的每一個。 提示：選取階層中的多個專案，以大量新增 EyeTrackingTarget 元件。
    ![Lesson5 Chapter3 Step2](images/Lesson5Chapter3Step2.JPG)

3. 接下來，我們會新增 EyeTrackingTutorialDemo 腳本來進行一些令人興奮的互動。 EyeTrackingTutorialDemo 腳本包含在本教學課程系列存放庫中。 預設不包含混合現實工具組。 針對方格集合中的每個3D 物件，藉由在 [加入元件] 功能表中搜尋元件來新增 EyeTrackingTutorialDemo 腳本。
   ![Lesson5 Chapter3 Step3](images/Lesson5Chapter3Step3.JPG)

4. 在注視目標時旋轉物件。 我們想要設定我們的3D 物件，以在我們查看時旋轉。 若要這麼做，請在查看 EyeTrackingTarget 元件的 Target （）區段時，在中插入新的欄位，如下圖所示。 

![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)
![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)



在新建立的欄位中，將目前的遊戲物件新增至空白欄位，然後選取 [EyeTrackingTutorialDemo > RotateTarget （）]，如下圖所示。 現在，3D 物件被設定為在透過眼球追蹤注視時旋轉。 

5. 加入「中斷目標」的功能，這是以點按方式選取，或說出「select」時所 gazed 的。 與步驟4類似，我們想要藉由將 EyeTrackingTutorialDemo 指派給 EyeTrackingTarget 元件的遊戲物件的 Select （）欄位來觸發 > BlipTarget （），如下圖所示。 現在設定完成後，每當您觸發選取動作（例如，按下點或語音命令「選取」）時，就會注意到遊戲物件有些許中斷。 
    ![Lesson5 Chapter3 Step5](images/Lesson5Chapter3Step5.JPG)
6. 在建置 HoloLens 2 之前，請確定已正確設定眼球追蹤功能。 在撰寫本文時，Unity 尚未能夠設定眼追蹤功能的注視輸入。 需要設定這項功能，眼睛追蹤才能在 HoloLens 2 中工作。 請遵循混合實境工具組文件中的這些指示，啟用注視輸入功能： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2 


## <a name="congratulations"></a>恭喜！

您已成功將基本眼追蹤功能新增至您的應用程式。 這些動作只是眼球追蹤功能無限可能性的開端。 本章也會在第5課結束，我們已瞭解先進的輸入功能，例如語音命令、移動流覽手勢和眼追蹤。 

[下一課： 7. 建立農曆模組範例應用程式](mrlearning-base-ch6.md)

