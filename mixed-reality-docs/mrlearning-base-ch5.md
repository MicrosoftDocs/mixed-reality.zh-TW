---
title: MR 學習基底模組-進階輸入
description: 完成這個課程來了解如何在混合的實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合的實境，unity 教學課程 hololens
ms.openlocfilehash: c28b607e3532a7c964ab74fdb7a7d514c9293579
ms.sourcegitcommit: a32f673814a6cd6ff00f936f448885788b3b882c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "64929571"
---
# <a name="mr-learning-base-module---advanced-input"></a>MR 學習基底模組-進階輸入

在這一課中，我們將探討 HoloLens 2，包括語音命令、 移動軌跡，以及追蹤使用的數個輸入進階的選項。 

## <a name="objectives"></a>目標

- 了解如何使用語音命令和關鍵字的事件觸發程序
- 使用追蹤的指針移動瀏覽的材質和 3D 物件
- 利用追蹤功能，可選取物件的 HoloLens 2 的眼睛

## <a name="instructions"></a>指示

### <a name="enabling-voice-commands"></a>啟用語音命令

在本節中，我們會實作兩個語音命令。 首先，能夠切換畫面格速率診斷面板所說 「 切換診斷 」。 其次，若要播放的音效以語音命令的能力。 我們先將探討 MRTK 設定檔和設定負責設定語音命令。 

1. 基底場景階層中選取 「 MixedRealityToolkit。 」 在 [偵測器] 面板中，向下輸入的系統設定中捲動。 按兩下以開啟 設定檔輸入的系統。 複製輸入的系統設定檔，以便可以進行編輯，因為我們了解在[第 1 課](mrlearning-base-ch1.md) 

在輸入的系統設定檔中，您會看到各種設定。 語音命令，針對往下移到其中註明，< 語音命令設定 >。 

![Lesson5 Chapter1 Step2im](images/Lesson5_Chapter1_step2im.PNG)

2. 複製語音命令設定檔，以便可以進行編輯，因為我們了解在[第 1 課](mrlearning-base-ch1.md)。 按兩下語音命令設定檔，您將會注意到一系列的設定。 如需這些設定的完整說明，請參閱[MRTK 語音文件](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>)。 

>注意：根據預設，一般行為會自動啟動。 這是可以變更為手動啟動如有需要，但此範例中我們要將它保存在自動啟動。 MRTK 隨附數個預設語音命令 （例如功能表、 切換診斷，以及切換程式碼剖析工具）。 我們將使用的關鍵字 「 切換診斷 」 才能開啟和關閉診斷畫面播放速率計數器。 我們也會在下列步驟中加入新的語音命令。
>
> ![Lesson5 Chapter1 Noteim](images/Lesson5_chapter1_noteim.PNG)

3. 加入新的語音命令。 若要加入新的語音命令，按一下 [+ 加入新的語音命令] 按鈕，以及您會看到新的一行下方所顯示向下現有的語音命令的清單。 輸入您想要使用語音命令。 在此範例 musicample 我們要使用命令"播放音樂 」。

>秘訣：您也可以設定語音命令的按鍵的代碼。 這可讓您在按下鍵盤按鍵時觸發的語音命令。   

4. 新增回應語音命令的能力。 選取任何物件基底的場景階層中沒有任何其他輸入指令碼附加到它 （例如，沒有操作處理常式。）在 [偵測器] 面板中，按一下 [新增元件]。 輸入 「 語音輸入的處理常式 」。 請選取它。
   ![Lesson5 Chapter1 Step4im](images/Lesson5_chapter1_step4im.PNG)

   

根據預設，您會看到 2 個核取方塊，其中一個是 「 」 所需的焦點 核取方塊。 這表示，只要您指向的物件與視線光線、 （眼睛視線、 head 視線、 控制站-視線或手動視線），就會觸發語音命令。 取消核取此核取方塊，這樣使用者就不必查看使用語音命令的物件。

5. 新增回應語音命令的功能。 若要這樣做，請按一下"+"按鈕是語音輸入處理常式，並選取您想要回應的關鍵字。

   > 注意：這些關鍵字會填入您在上一個步驟中編輯過的設定檔。

![Lesson5 Chapter1 Step5im](images/Lesson5_chapter1_step5im.PNG)

6. 「 關鍵字 」 旁邊，您會看到下拉式功能表。 選取 「 切換診斷 」。 因此，每當使用者所講的片語，"切換診斷 」 時，它就會觸發動作，這會讓它。 請注意，您可能需要按下它旁邊的箭號展開 「 項目 0 」。

![Lesson5 Chapter1 Step6im](images/Lesson5_chapter1_step6im.PNG)

7. 新增 「 診斷示範控制指令碼 」 來切換開啟和關閉的畫面播放速率計數器診斷。 若要這樣做，請按 [新增元件] 按鈕並搜尋 「 診斷示範控制指令碼 」，然後從功能表將其新增。 此指令碼可以新增至任何物件，但為了簡單起見，我們會將其加入語音輸入處理常式的相同物件。 

   > 注意： 此指令碼才會包含這些模組中，不會包含原始 MRTK。

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step7im.PNG)

8. 語音輸入處理常式中加入新的回應。 這按一下底下其中註明"回應 （）"（在上圖中的綠色箭號標示）"+"按鈕。

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step8.PNG)

9. 將具有您在步驟 8 中建立新的回應診斷示範控制項指令碼的物件。
    ![Lesson5 Chapter1 Step9im](images/Lesson5_chapter1_step9im.PNG)

10. 現在選取 「 沒有函式 」 下拉式清單中，選取診斷示範控制項、 然後 」"上切換診斷 （）。 此函式會切換開啟和關閉您的診斷。  ![Lesson5 Chapter1 Step10im](images/Lesson5_chapter1_step10im.PNG)
    
> 請注意到您的裝置的建置前需要啟用 mic 設定。 若要這樣做，該檔案上的按一下，請移至組建設定，從該處，播放程式設定，並確認設定麥克風功能。

接下來，我們要新增播放音訊檔使用 「 顆 octa 」 物件的語音命令的能力。 回想一下[第 4 課](mrlearning-base-ch4.md)，我們已新增要播放的音訊剪輯不碰觸顆 octa 物件的能力。 我們將會利用這個相同的音訊來源，我們的音樂語音命令。

11. 選取顆 octa 物件階層中的基底的場景。

12. 新增另一個語音輸入處理常式 （重複步驟 4 和 5)，但與顆 octa 物件。 

13. 而不是從步驟 6 中新增 「 切換診斷 」 語音命令，新增 「 播放音樂"語音命令，如下圖所示。
    
     ![Lesson5 Chapter1 Step13im](images/Lesson5_chapter1_step13im.PNG)
    
    
    
14. 如同步驟 8 和 9，加入新的回應，並拖曳顆 octa 的空插槽上回應。

15. 選取下拉式功能表中，指出 「 沒有函式，」 選取 「 音訊來源，」，然後選取 「 PlayOneShot (AudioClip)。 」

![Lesson5 Chapter1 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. 的音訊剪輯，此範例中我們將使用從相同的音訊剪輯[第 4 課](mrlearning-base-ch4.md)。 進入您的 [專案] 面板中，搜尋"MRTK_Gem 」 的音訊剪輯並將它拖曳到音訊來源位置，如下圖所示。 現在您的應用程式應該能夠回應語音命令 「 切換診斷 」 切換畫面格速率計數器面板來 「 播放音樂 」 播放 MRTK_Gem 歌曲。
     ![Lesson5 Chapter1 Step16im](images/Lesson5_chapter1_step16im.PNG)


### <a name="the-pan-gesture"></a>移動瀏覽軌跡 

在本章中，我們將學習如何使用移動瀏覽軌跡。 它可用於捲動 （使用您的手指或手動捲動內容）。您也可以使用 pan 筆勢來旋轉物件，以循環 3D 物件或甚至是捲動 2D UI 的集合。 我們將學習如何使用移動瀏覽軌跡 warp 材質。 我們也將探討如何移動 3D 物件的集合。

1. 建立四組數字。 在基底的場景階層中，以滑鼠右鍵按一下，選取 「 3D 物件 」，然後選取 「 四組數字 」。

![Lesson5 Chapter2 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. 調整為適當的四組數字的位置。 我們的範例中，我們會設定 x = 0，y = 0 且 z = 1.5 離開舒適的位置從 HoloLens 2 相機。

   > 注意：如果四個區塊 （是的 infront） 任何內容，從先前的課程，請務必移動它，使它不會封鎖任何其他物件。

3. 將材質套用至四組數字。 這份資料將會是我們將會使用捲動取景位置調整動作的內容。 

![Lesson5 Chapter2 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. 在您的專案 面板中，輸入在搜尋方塊中 「 取景位置調整內容 」。 將該資料拖曳到場景中四組數字。 

> 注意：「 取景位置調整的內容 」 的資料不會納入 MRTK，但在此模組之資產套件中，資產匯入在上一課。 

> 注意：當您新增的移動瀏覽內容時，可能會看起來延伸。 您可以藉由調整 x、 y 和 z 值大小的四組數字的值，直到您滿意其外觀的方式來修正此問題。

若要使用移動瀏覽鍵筆勢，您必須 collider 上您的物件。 您可能會看到四組數字已網狀結構 collider。 不過，在網狀結構 collider 並不理想，因為它是極精簡且更難選取。 我們建議在網狀結構 collider 取代方塊 collider。

5. 四組數字 （在 [偵測器] 面板中） 是網狀結構 collider 上按一下滑鼠右鍵，然後將它移除依序按一下 [移除元件]。 
   ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)

6. 現在加入方塊 collider，按一下 [新增元件]，然後搜尋 「 box collider。 」 預設值可讓您新增方塊 collider 仍然是太精簡，因此請按一下 [編輯 collider] 按鈕來編輯它。 它在按下時，您可以調整大小在場景編輯器中使用 x、 y 和 z 值或項目。 我們的範例中，我們想要四組數字後面有點擴充方塊 collider。 在場景編輯器 中，拖曳方塊 collider 從備份中，向外套用 （請參閱下圖）。 這會做的就是讓使用者不只使用他們的手指，但其整個手動捲動。 
    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)
7. 讓具互動性。 因為我們想要直接互動的四組數字，我們想要使用 （我們也使用這第 4 課的播放音樂從顆 octa） 的 < 近乎互動 touchable 」 元件。 按一下 [新增元件] 並搜尋 「 接近互動 touchable 」 並選取它，如下列影像所示。 

8. 新增可辨識取景位置調整動作的能力。 按一下 [新增元件]，然後輸入 「 送互動取景位置調整 」。 您必須手動光線 （可讓您移動瀏覽距離） 和食指之間選擇。 此範例中，將其保持在索引的手指。 
    ![Lesson5 Chapter2 步驟 7 8Im](images/Lesson5_chapter2_step7-8im.PNG)

![Lesson5 Chapter2 Step8im](images/Lesson5_chapter2_step8im.PNG)

9. 在手動互動取景位置調整指令碼中，[鎖定水平] 和 [垂直鎖定] 核取方塊將會鎖定移動，分別。 自動換行紋理設定將紋理 （紋理對應） 依照使用者的移動瀏覽移動。 針對此範例中，我們要核取該方塊。 另外還有"velocity 作用中 」 的移動瀏覽動作如果未選取，將無法運作。 核取此方塊以及。 現在您應該已啟用移動瀏覽的四組數字。

   

   接下來，我們將了解如何移動瀏覽 3D 物件。 

10. 四個物件上按一下滑鼠右鍵，選取 3D 物件然後按一下 「 cube 」。 相應的 cube，使它大致上是 x = 0.1，y = 0.1 和 z = 0.1。 複製該 cube 3 次 （透過以滑鼠右鍵按一下 cube，然後按 重複，或按下控制項/命令 D）。 分隔平均。 場景看起來應該如下列圖片所示。

![Lesson5 Chapter2 Step10im](images/Lesson5_chapter2_step10im.PNG)







11. 同樣地，選取四組數字和下手動互動取景位置調整指令碼中，我們想要之 cube 的每個設定的移動瀏覽動作。 在 「 取景位置調整事件接收器 」 下我們想要指定會接收事件的物件數目。 由於有 4 個 cube，型別"4"，然後按 enter。 4 個空的欄位應該會出現。


![Lesson5 Chapter2 Step11im](images/Lesson5_chapter2_step11im.PNG)



12. 將每一個 cube 中拖曳至每個空白項目位置。
     ![Lesson5 Chapter2 Step12im](images/Lesson5_chapter2_step12im.PNG)
    
13. 將 「 移動 」 與 「 取景位置調整 「 指令碼新增至所有的 cube。 若要這樣做，按住滑鼠控制/命令並選取每個物件。 然後，在 [偵測器] 面板中，按一下 [新增元件]，並搜尋 「 移動使用 pan。 」 按一下 指令碼，它會新增至每個 cube。 現在會移動 3D 物件，與取景位置調整筆勢 ！ 如果您移除網格轉譯在您的四組數字，您現在應該有不可見四組數字，您可以平移 3D 物件的清單。

### <a name="eye-tracking"></a>追蹤

在本章中，我們將探討如何啟用眼睛追蹤，在我們的示範。 時它們會被 gazed 時與眼睛視線，我們會緩慢旋轉我們 3D 的功能表項目。 我們也會觸發一個有趣效果選取 gazed 時項目時。

1. 請確定已正確設定的混合實境工具組設定檔。 撰寫本文時，混合的實境工具組設定檔設定不包含預設追蹤功能。 若要加入追蹤功能，請遵循 「 設定所需的眼睛追蹤 MRTK 設定檔 」 一節中的指示中所述[混合實境 Toolkit 文件](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-the-mrtk-profiles-required-for-eye-tracking  )。 請確定追蹤該眼睛的設定正確遵循所有剩餘的步驟在文件上列連結，包括啟用 GazeProvider （觀景窗附加元件） 中的紅眼追蹤，以及啟用的追蹤在 Unity 編輯器中的模擬。 請注意 MRTK 的未來版本可能包含預設的眼睛追蹤。

    上述連結提供簡短的指示：

    - 建立眼睛視線資料提供者用於 MRTK 設定檔中
    - 啟用視線提供者中的紅眼追蹤
    - 模擬在編輯器中的追蹤設定
    - 編輯 Visual Studio 方案的功能，以允許在建置的應用程式中的紅眼追蹤

2. 將眼睛追蹤目標元件新增至目標物件。 若要讓物件回應眼睛視線事件，我們必須加入 EyeTrackingTarget 元件，我們想要使用的眼睛視線互動的每個物件上。 將此元件新增至每個方格集合一部分的九個 3D 物件。 提示： 選取要大量新增 EyeTrackingTarget 元件階層中的多個項目。
    ![Lesson5 Chapter3 步驟 2](images/Lesson5Chapter3Step2.JPG)

3. 接下來我們將新增一些令人興奮的互動的 EyeTrackingTutorialDemo 指令碼。 EyeTrackingTutorialDemo 指令碼是本教學課程系列的儲存機制的一部分，而且不會包含預設混合實境工具組。 方格集合中每一個 3D 物件，新增 EyeTrackingTutorialDemo 指令碼搜尋在 [新增元件] 功能表中的元件。
   ![Lesson5 Chapter3 步驟 3](images/Lesson5Chapter3Step3.JPG)

   4. 尋找目標時啟動的物件。 我們想要設定啟動時，我們看看它要我們 3D 物件。 若要這樣做，如下圖所示，在 EyeTrackingTarget 元件的 「 時尋找在目標 」 一節中插入新的欄位。 

![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)
![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)



在新建立的欄位中，將目前的遊戲物件新增至空的欄位，然後選取 EyeTrackingTutorialDemo > RotateTarget() 如下圖所示。 現在的 3D 物件被設定為啟動時它正在 gazed 時眼睛追蹤。 

5. 在功能中加入 「 中斷目標 」 在 選取 （空中點選，或說出"select"） 時 gazed 在。 我們所要觸發 EyeTrackingTutorialDemo 類似步驟 4，> BlipTarget() 將它指派給 EyeTrackingTarget 元件的遊戲物件的 「 select 」 欄位，如下圖所示。 這現在已設定，您會注意到些微中斷遊戲物件的值時觸發選取的動作，例如空中點選或語音命令中 [選取]。 
    ![Lesson5 Chapter3 步驟 5](images/Lesson5Chapter3Step5.JPG)
6. 請確定眼睛追蹤功能已正確設定建置以 HoloLens 2 之前。 撰寫本文時，Unity 還沒有設定視線輸入 （適用於眼睛追蹤） 功能的能力。 HoloLens 2 上運作的眼睛追蹤需要設定這項功能。 請遵循這些指示在混合的實境 toolkit 文件來啟用視線輸入的功能： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2 


### <a name="congratulations"></a>恭喜您！ 
您已成功新增至應用程式追蹤功能的基本眼睛。 這些動作是的可能性，並追蹤世界的開端。 本章也會結束第 5 課，其中我們已了解進階的輸入功能，例如語音命令移動瀏覽筆勢及眼睛追蹤。 

[下一課：農曆模組組件範例體驗](mrlearning-base-ch6.md)

