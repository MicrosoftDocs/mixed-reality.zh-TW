---
title: MR 學習基本模組 - 進階輸入
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 32141aafd43c5d729919673509c93bb2014edd37
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66719893"
---
# <a name="mr-learning-base-module---advanced-input"></a>MR 學習基本模組 - 進階輸入

在本課程中，我們將探討 HoloLens 2 的幾個進階輸入選項，包括使用語音命令、平移手勢和眼球追蹤。 

## <a name="objectives"></a>目標

- 了解如何使用語音命令和關鍵字觸發事件
- 使用手部追蹤來平移紋理和 3D 物件
- 利用 HoloLens 2 的眼球追蹤功能來選取物件

## <a name="instructions"></a>指示

### <a name="enabling-voice-commands"></a>啟用語音命令

在本節中，我們會實作兩個語音命令。 第一，透過說出 "toggle diagnostics" \(切換診斷\) 來切換畫面播放速率診斷面板的功能。 第二，以語音命令播放音效的功能。 首先我們將探索負責設定語音命令的 MRTK 設定檔和設定。 

1. 在基底場景階層中，選取 "MixedRealityToolkit"。 在 [Inspector] 面板中，向下捲動至輸入系統設定。 按兩下以開啟輸入系統設定檔。 複製輸入系統設定檔，以便可以進行編輯，正如我們在[第 1 課](mrlearning-base-ch1.md)中所學的那樣 

在輸入系統設定檔中，您會看到各種設定。 針對語音命令，請移到標示 "Speech Command Settings" \(語音命令設定\) 的位置。 

![Lesson5 Chapter1 Step2im](images/Lesson5_Chapter1_step2im.PNG)

2. 複製語音命令設定檔，以便可以進行編輯，正如我們在[第 1 課](mrlearning-base-ch1.md)中所學的那樣。 按兩下語音命令設定檔，您將會注意到一系列的設定。 如需這些設定的完整說明，請參閱 [MRTK 語音文件](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>) \(英文\)。 

>注意：根據預設，一般行為是自動啟動。 如果需要，可以將其變更為手動啟動，但是此範例中我們將保持自動啟動。 MRTK 隨附數個預設語音命令 (例如 [Menu] \(功能表\)、[Toggle Diagnostics] \(切換診斷\) 和 [Toggle Profiler] \(切換程式碼剖析工具\))。 我們將使用關鍵字 "toggle diagnostics" 來開啟和關閉診斷畫面播放速率計數器。 我們還將在下列步驟中加入新的語音命令。
>
> ![Lesson5 Chapter1 Noteim](images/Lesson5_chapter1_noteim.PNG)

3. 加入新的語音命令。 若要加入新的語音命令，按一下 [+ Add a New Speech Command] \(+ 加入新的語音命令\) 按鈕，您會看到現有的語音命令清單下方顯示新的一行。 輸入您想要使用的語音命令。 在這個前音樂範例中，我們將使用 [Play Music] 命令。

>秘訣：您也可以為語音命令設定按鍵代碼。 這可讓您在按下鍵盤按鍵時觸發語音命令。   

4. 新增回應語音命令的功能。 選取基底場景階層中沒有附加任何其他輸入指令碼的任何物件 (例如，沒有操作處理常式)。按一下 [Inspector] 面板中的 [Add Component]。 輸入 "speech input handler"。 請選取它。
   ![Lesson5 Chapter1 Step4im](images/Lesson5_chapter1_step4im.PNG)

   

根據預設，您會看到 2 個核取方塊，其中一個是 [Is Focus Required] \(需要焦點\) 核取方塊。 這表示只要您以視線指向物件 (眼睛注視、頭部注視、控制器注視或手動注視)，就會觸發語音命令。 取消核取此核取方塊，這樣使用者就不必注視物件以使用語音命令。

5. 新增回應語音命令的功能。 若要這樣做，請按一下語音輸入處理常式中的 [+] 按鈕，然後選取您想要回應的關鍵字。

   > 注意：根據您在上一個步驟中編輯過的設定檔，將填入這些關鍵字。

![Lesson5 Chapter1 Step5im](images/Lesson5_chapter1_step5im.PNG)

6. 在 [Keyword] \(關鍵字\) 旁邊，您會看到下拉式功能表。 選取 [Toggle Diagnostics]。 這會讓使用者每次說出片語 "toggle diagnostics" 時，就會觸發動作。 請注意，您可能需要透過按下它旁邊的箭頭來展開 "element 0"。

![Lesson5 Chapter1 Step6im](images/Lesson5_chapter1_step6im.PNG)

7. 新增 [Diagnostics Demo Control] \(診斷示範控制\) 指令碼，以切換開啟和關閉畫面播放速率計數器診斷。 若要這樣做，請按 [Add Component] 按鈕並搜尋 "diagnostics demo control script"，然後從功能表將其新增。 此指令碼可以新增至任何物件，但為了簡單起見，我們將其新增至與語音輸入處理常式相同的物件中。 

   > 注意：此指令碼僅包含在這些模組中，不包含在原始 MRTK 中。

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step7im.PNG)

8. 在 Speech Input Handler \(語音輸入處理常式\) 中加入新的回應。 若要這樣做，請按一下 [response ()] (上圖中以綠色箭號標示) 下方的 [+] 按鈕。

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step8.PNG)

9. 將具有 [Diagnostics Demo Controls] \(診斷示範控制項\) 指令碼的物件，拖曳至剛剛在步驟 8 中建立的新回應。
    ![Lesson5 Chapter1 Step9im](images/Lesson5_chapter1_step9im.PNG)

10. 現在選取 [No Function] \(無功能\) 下拉式清單，選取 [Diagnostics Demo Controls]，然後選取 [OnToggleDiagnostics ()]。 此功能會切換開啟和關閉您的診斷。  ![Lesson5 Chapter1 Step10im](images/Lesson5_chapter1_step10im.PNG)
    
> 請注意，在建置您的裝置之前，您需要啟用麥克風設定。 若要這樣做，請按一下該檔案，移至建置設定，從該處找到播放程式設定，並確認麥克風功能已設定。

接下來，我們要新增使用 "octa" 物件從語音命令播放音訊檔的功能。 回想一下[第 4 課](mrlearning-base-ch4.md)，我們新增了透過觸控 octa 物件播放音訊剪輯的功能。 我們將針對我們的音樂語音命令使用相同的音訊來源。

11. 選取基底場景階層中的八邊形物件。

12. 新增另一個語音輸入處理常式 (重複步驟 4 和 5)，但使用八邊形物件。 

13. 不新增步驟 6 中的 [Toggle Diagnostics] 語音命令，而是新增 [Play Music] \(播放音樂\) 語音命令，如下圖所示。
    
     ![Lesson5 Chapter1 Step13im](images/Lesson5_chapter1_step13im.PNG)
    
    
    
14. 與步驟 8 和 9 一樣，加入新的回應，並在回應時將八邊形拖曳至空的位置。

15. 選取顯示為 [No Function] \(無功能\) 的下拉式功能表，選取 [Audio Source] \(音訊來源\)，然後選取 [PlayOneShot (AudioClip)]。

![Lesson5 Chapter1 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. 針對音訊剪輯，我們將在此範例中使用[第 4 課](mrlearning-base-ch4.md)的相同音訊剪輯。 進入您的 [Project] 面板，搜尋 "MRTK_Gem" 音訊剪輯並將其拖曳至音訊來源位置中，如下圖所示。 現在，您的應用程式應該能夠回應語音命令 "toggle diagnostics" 以切換畫面格速率計數器面板，以及 "play music" 以播放 MRTK_Gem 歌曲。
     ![Lesson5 Chapter1 Step16im](images/Lesson5_chapter1_step16im.PNG)


### <a name="the-pan-gesture"></a>平移手勢 

在本章中，我們將學習如何使用平移手勢。 它可用於捲動 (使用您的手指或手捲動內容)。您還可以使用平移手勢來旋轉物件、循環瀏覽 3D 物件集合，甚至捲動 2D UI。 我們將學習如何使用平移手勢來扭曲紋理。 我們也將探索如何移動 3D 物件的集合。

1. 建立四邊形。 在基底場景階層中，以滑鼠右鍵按一下，選取 [3D Object] \(3D 物件\)，然後選取 [Quad] \(四邊形\)。

![Lesson5 Chapter2 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. 根據需要重新調整四邊形的位置。 針對我們的範例，我們設定 x = 0、y = 0 且 z = 1.5 (遠離相機)，以取得 HoloLens 2 的舒適位置。

   > 注意：如果四邊形阻擋先前課程中的任何內容 (或在這些內容之前)，請務必移動它，使它不會阻擋任何其他物件。

3. 將材質套用至四邊形。 這個材質將是我們使用平移手勢捲動的材質。 

![Lesson5 Chapter2 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. 在您的 [Project] 面板中，在搜尋方塊中輸入 "pan content" \(平移內容\)。 將該材質拖曳至場景中的四邊形。 

> 注意：[PanContent] 材質不包含在 MRTK 中，但它是此模組資產套件中的一項資產，在先前的課程中已匯入。 

> 注意：當您新增平移內容時，看起來可能會很延伸。 您可以藉由調整四邊形大小的 x、y 和 z 值來解決此問題，直到您對它的外觀感到滿意為止。

若要使用平移手勢，您需要在物件上使用碰撞器。 您可能會看到四邊形已經有一個網格碰撞器。 然而，網格碰撞器並不理想，因為它非常薄並且難以選取。 我們建議用方塊碰撞器取代網格碰撞器。

5. 以滑鼠右鍵按一下四邊形上的網格碰撞器 (在 [Inspector] 面板中)，然後按一下 [Remove Component] \(移除元件\) 將它移除。 
   ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)

6. 現在透過按一下 [Add Component] 並搜尋 "box collider" 來新增方塊碰撞器。 新增的預設方塊碰撞器仍然太薄，因此請按一下 [Edit Collider] \(編輯碰撞器\) 按鈕來編輯它。 按下它時，可以使用 x、y 和 z 值或場景編輯器中的元素調整大小。 針對我們的範例，我們希望將方塊碰撞器延伸到四邊形後面。 在場景編輯器中，從後面向外拖曳方塊碰撞器 (請參閱下圖)。 這樣一來將允許使用者不僅使用他們的手指，而且允許使用他們的整個手來進行捲動。 
    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)
7. 使其具互動性。 由於我們想直接與四邊形互動，所以我們想要使用 [Near Interaction Touchable] 元件 (我們也在第 4 課中使用它來播放來自八邊形的音樂)。 按一下 [Add Component] 並搜尋 "near interaction touchable" 並選取它，如下列影像所示。 

8. 新增可辨識平移手勢的功能。 按一下 [Add Component]，然後輸入 "hand interaction pan" \(手部平移互動\)。 您可以在手動光線 (允許您從遠處平移) 和食指之間進行選擇。 針對此範例，將其保留為食指。 
    ![Lesson5 Chapter2 Step7 8Im](images/Lesson5_chapter2_step7-8im.PNG)

![Lesson5 Chapter2 Step8im](images/Lesson5_chapter2_step8im.PNG)

9. 在手部平移互動指令碼中，[Lock Horizontal] \(水平鎖定\) 和 [Lock Vertical] \(鎖定垂直\) 核取方塊將會分別鎖定移動。 [Wrap Texture] \(扭曲紋理\) 設定將使紋理 (紋理對應) 依照使用者的平移移動。 針對此範例，我們要核取該方塊。 還有 [Velocity Active] \(速度啟用\)，如果未選取，則平移手勢將無法運作。 也請核取此方塊。 現在您應該有一個已啟用平移的四邊形。

   

   接下來，我們將學習如何平移 3D 物件。 

10. 以滑鼠右鍵按一下四邊形物件、選取 3D 物件，然後按一下 [Cube]。 縮放立方體，使其大致為 x = 0.1、y = 0.1 且 z = 0.1。 複製該立方體 3 次 (通過以滑鼠右鍵按一下立方體並按 [Duplicate]，或按 Control/Command D)。 將它們平均分開。 您的場景看起來應該如下列圖片所示。

![Lesson5 Chapter2 Step10im](images/Lesson5_chapter2_step10im.PNG)







11. 再次選取四邊形，在手部平移互動指令碼下，我們希望為每個立方體設定平移動作。 在 [Pan Event Receivers] \(平移事件接收器\) 下，我們要指定接收事件的物件數目。 由於有 4 個立方體，請輸入 "4" 並按 Enter。 應該會出現 4 個空的欄位。


![Lesson5 Chapter2 Step11im](images/Lesson5_chapter2_step11im.PNG)



12. 將每個立方體拖曳至每個空白元素位置中。
     ![Lesson5 Chapter2 Step12im](images/Lesson5_chapter2_step12im.PNG)
    
13. 將 [Move With Pan] \(平移移動\) 指令碼新增至所有的立方體。 若要這樣做，請長按 Control/Command 並選取每個物件。 然後，在 [Inspector] 面板中，按一下 [Add Component] 並搜尋 "move with pan"。 按一下該指令碼，它會新增至每個立方體。 現在，3D 物件將隨著您的平移手勢移動！ 如果在四邊形上移除網格渲染器，則現在應該有一個不可見的四邊形，您可以在其中平移 3D 物件的清單。

### <a name="eye-tracking"></a>眼球追蹤

在本章中，我們將在我們的示範中探討如何啟用眼球追蹤。 當我們的 3D 功能表項目受到注視時，我們將慢慢旋轉它們。 當選取注視項目時，我們也會觸發有趣的效果。

1. 請確定已正確設定混合實境工具組設定檔。 在撰寫本文時，混合實境工具組設定檔設定根據預設不包含眼球追蹤功能。 若要加入眼球追蹤功能，請按照[混合實境工具組文件](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-the-mrtk-profiles-required-for-eye-tracking  ) \(英文\) 中所述之「設定眼球追蹤所需的 MRTK 設定檔」一節中的指示進行操作。 按照上述文件連結中的任何剩餘步驟，確保已正確設定眼球追蹤，包括在 GazeProvider (連接到相機的元件) 中啟用眼球追蹤，並在 Unity 編輯器中啟用眼球追蹤模擬。 請注意，MRTK 的未來版本預設情況下可能包含眼球追蹤。

    上述連結提供下列事項的簡短指示：

    - 建立 Eye Gaze Data Provider 以在 MRTK 設定檔中使用
    - 在 Gaze Provider 中啟用眼球追蹤
    - 針對在編輯器中模擬眼球追蹤進行設定
    - 編輯 Visual Studio 解決方案的功能，以允許在建置的應用程式中進行眼球追蹤

2. 將眼球追蹤目標元件新增至目標物件。 若要讓物件能夠回應眼睛注視事件，我們需要在我們希望使用眼睛注視與之互動的每個物件上，加入 EyeTrackingTarget 元件。 將此元件新增至作為方格集合一部分之九個 3D 物件中的每一個。 提示：選取階層中的多個項目以大量新增 EyeTrackingTarget 元件。
    ![Lesson5 Chapter3 Step2](images/Lesson5Chapter3Step2.JPG)

3. 接下來，我們將新增 EyeTrackingTutorialDemo 指令碼以進行一些令人興奮的互動。 EyeTrackingTutorialDemo 指令碼會作為本教學課程系列之存放庫的一部分包含在內，預設情況下不包含在混合實境工具組中。 對於方格集合中的每個 3D 物件，透過在 [Add Component] 功能表中搜尋元件來新增 EyeTrackingTutorialDemo 指令碼。
   ![Lesson5 Chapter3 Step3](images/Lesson5Chapter3Step3.JPG)

   4. 在注視目標時旋轉物件。 我們想要在我們注視時，將我們的 3D 物件設定為旋轉。 若要這樣做，請在 EyeTrackingTarget 元件的 [While Looking At Target] \(注視目標時\) 區段中插入一個新的欄位，如下圖所示。 

![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)
![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)



在新建立的欄位中，將目前的遊戲物件新增至空的欄位，然後選取 [EyeTrackingTutorialDemo] > [RotateTarget()]，如下圖所示。 現在，3D 物件被設定為在透過眼球追蹤注視時旋轉。 

5. 加入 [Blip Target] 功能，該功能可讓選取時 (空中點選，或說出 "select") 注視的目標產生光點。 與步驟 4 類似，我們希望透過 EyeTrackingTutorialDemo > BlipTarget()，將 BlipTarget() 指派給 EyeTrackingTarget 元件之遊戲物件的 [Select()] 欄位來觸發它，如下圖所示。 設定完成後，當您觸發一個選取動作時，您會注意到遊戲物件中有輕微的光點，例如空中點選或語音命令 "select"。 
    ![Lesson5 Chapter3 Step5](images/Lesson5Chapter3Step5.JPG)
6. 在建置 HoloLens 2 之前，請確定已正確設定眼球追蹤功能。 在撰寫本文時，Unity 還無法設定注視輸入 (用於眼球追蹤) 功能。 需要設定這項功能，眼球追蹤才能在 HoloLens 2 上運作。 請遵循混合實境工具組文件中的這些指示，啟用注視輸入功能： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2 


### <a name="congratulations"></a>恭喜！ 
您已成功為應用程式新增了基本的眼球追蹤功能。 這些動作只是眼球追蹤功能無限可能性的開端。 本章也為第 5 課做了總結，其中我們已學習了進階的輸入功能，例如語音命令、平移手勢和眼球追蹤。 

[下一課：登月艙組件範例體驗](mrlearning-base-ch6.md)

