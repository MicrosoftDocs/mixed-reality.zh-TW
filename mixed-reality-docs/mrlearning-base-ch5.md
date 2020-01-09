---
title: 快速入門教學課程-6。 探索先進的輸入選項
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 75a14697953026474d8ca00e6473145d7b12a482
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334352"
---
# <a name="6-exploring-advanced-input-options"></a>6. 探索 advanced 輸入選項

在本教學課程中，會探索 HoloLens 2 的數個先進的輸入選項，包括使用語音命令、移動流覽手勢和眼睛追蹤。 

## <a name="objectives"></a>目標

- 使用語音命令和關鍵字觸發事件
- 使用追蹤的手平移材質和3D 物件
- 利用 HoloLens 2 眼追蹤功能來選取物件

## <a name="enabling-voice-commands"></a>啟用語音命令

在本節中，會執行兩個語音命令。 首先，您可以藉由說「切換診斷」來引進切換畫面播放速率診斷面板的功能。 第二，會探索使用語音命令來播放音效的功能。 負責設定語音命令的 MRTK 設定檔和設定會先進行審核。

1. 在 BaseScene 階層中，選取 [MixedRealityToolkit]。 然後，在 [偵測器] 面板中選取 [輸入]，然後按一下 DefaultMixedRealityInputSystemProfile 左邊的小型 [複製] 按鈕，以開啟 [複製設定檔] 快顯視窗。 在快顯視窗中按一下 [複製]，以建立新的設定檔 MixedRealityInputSystemProfile。

    ![mrlearning-base-ch5-1-step1a .png](images/mrlearning-base-ch5-1-step1a.png)

    這也會使用新建立的 MixedRealityInputSystemProfile 自動填入 MixedRealityToolkitConfigurationProfile。

    ![mrlearning-base-ch5-1-step1b .png](images/mrlearning-base-ch5-1-step1b.png)

2. 在輸入系統設定檔中，有各種不同的設定。 針對語音命令，請展開 [語音] 區段，並遵循與上一個步驟相同的程式來複製 DefaultMixedRealitySpeechCommandsProfile，並將它取代為您自己的可編輯複本。

    ![mrlearning-base-ch5-1-step2 .png](images/mrlearning-base-ch5-1-step2.png)

    在語音命令設定檔中，您會注意到一系列的設定。 如需這些設定的完整說明，請參閱[MRTK 語音檔](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>)。

    根據預設，一般行為是自動啟動。 如有需要，您可以將此變更為手動啟動。 但在此範例中，請將它保持在自動啟動。 MRTK 隨附數個預設語音命令，例如功能表、切換診斷和切換 profiler。 我們將使用關鍵字「切換診斷」，以開啟和關閉診斷的畫面播放速率計數器。 我們還將在下列步驟中加入新的語音命令。

3. 加入新的語音命令。 若要這樣做，請按一下 [+ 新增語音命令] 按鈕。 您會看到出現在現有語音命令清單下方的新行。 輸入您想要使用的語音命令。 在此範例中，使用「播放音樂」命令。

    ![mrlearning-base-ch5-1-step3 .png](images/mrlearning-base-ch5-1-step3.png)

    >[!NOTE]
    >您也可以為語音命令設定按鍵代碼。 這可讓語音命令在按下鍵盤按鍵時觸發事件。

4. 新增回應語音命令的功能。 在 BaseScene 階層中選取任何未附加任何其他輸入腳本的物件，例如 MixedRealityPlayspace 遊戲物件。 在 [偵測器] 面板中，按一下 [新增元件]，搜尋 "speech"，然後選取語音輸入處理常式腳本。

    ![mrlearning-base-ch5-1-step4 .png](images/mrlearning-base-ch5-1-step4.png)

    根據預設，您會看到兩個核取方塊。 其中一個是 [需要焦點] 核取方塊。 因此，只要您是以光線眼、列印頭、控制器眼或手注視的方式來指向物件，就會觸發語音命令。 取消核取此核取方塊，讓使用者不需要查看物件即可使用語音命令。

5. 新增回應語音命令的功能。 若要這麼做，請按一下語音輸入處理常式中的 [+] 按鈕。

    ![mrlearning-base-ch5-1-step5 .png](images/mrlearning-base-ch5-1-step5.png)

6. 在 [關鍵字] 旁，您會看到一個下拉式功能表。 選取 [切換診斷]，如此一來，每當使用者說出「切換診斷」片語時，它就會觸發動作。 請注意，您可能需要按下旁邊的箭號來展開元素0。

    ![mrlearning-base-ch5-1-step6 .png](images/mrlearning-base-ch5-1-step6.png)

    >[!NOTE]
    >系統會根據您在步驟3中編輯的設定檔，填入這些關鍵字。

7. 新增診斷系統 Voice 控制項腳本，以切換開啟和關閉的畫面播放速率計數器診斷。 若要這麼做，請按 [新增元件]，搜尋 [診斷] [系統] [語音控制腳本]，然後從功能表中加以新增。 此指令碼可以新增至任何物件，但為了簡單起見，我們將其新增至與語音輸入處理常式相同的物件中。

    ![mrlearning-base-ch5-1-step7 .png](images/mrlearning-base-ch5-1-step7.png)

8. 在語音輸入處理常式中加入新的回應。 若要這麼做，請按一下 [+] 圖示，將新的回應新增至回應清單。

    ![mrlearning-base-ch5-1-step8 .png](images/mrlearning-base-ch5-1-step8.png)

9. 將具有「診斷系統聲音控制」腳本的物件拖曳至您剛才在上一個步驟中建立的新回應。

    ![mrlearning-base-ch5-1-step9 .png](images/mrlearning-base-ch5-1-step9.png)

10. 按一下 [函式] 下拉式清單（此處未顯示函式）、[診斷系統聲音控制]，然後選取將診斷切換為開啟和關閉的 ToggleDiagnostics （）函數。

    ![mrlearning-base-ch5-1-step10 .png](images/mrlearning-base-ch5-1-step10.png)

    >[!IMPORTANT]
    > 在建立您的裝置之前，您必須啟用 mic 設定。 若要這樣做，請按一下 [檔案] 並移至 [組建設定]、[播放程式設定]，並確定已設定麥克風功能。

    接下來，使用顆 octa 物件新增播放音訊檔案的功能。 回想一下[第4課](mrlearning-base-ch4.md)，已新增播放音訊剪輯以觸及顆 octa 物件的能力。 我們將針對我們的音樂語音命令使用相同的音訊來源。

11. 選取 [BaseScene] 階層中的 [顆 octa] 物件。

12. 新增另一個語音輸入處理常式（重複步驟4和5），但使用顆 octa 物件。

13. 請新增 [播放音樂語音] 命令，而不是從步驟6新增 [切換診斷語音] 命令，如下圖所示。

    ![mrlearning-base-ch5-1-step13 .png](images/mrlearning-base-ch5-1-step13.png)

14. 如同步驟8和9，加入新的回應，並將顆 octa 物件（包含診斷系統 Voice 控制項腳本的物件）拖曳至空白回應位置。

15. 選取顯示 [沒有函數] 的下拉式功能表。 然後選取 [音訊來源]，後面接著 [PlayOneShot （AudioClip）]。

    ![Lesson5 Chapter1 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. 在此範例中，我們將使用[第4課](mrlearning-base-ch4.md)的相同音訊剪輯。 移至您的 [專案] 面板，搜尋 "MRTK_Gem" 音訊剪輯，並將它拖曳到音訊來源位置，如下圖所示。 現在，您的應用程式會回應語音命令「切換診斷」，以切換 [畫面播放速率計數器] 面板並播放音樂來播放 MRTK_Gem 的歌曲。

    ![Lesson5 Chapter1.txt Step16im](images/Lesson5_chapter1_step16im.PNG)

## <a name="the-pan-gesture"></a>平移手勢

在本節中，您將瞭解如何使用平移手勢。 這適用于使用手指或手來滾動內容的捲軸。 您也可以使用平移手勢來旋轉物件、迴圈流覽3D 物件的集合，甚至是滾動 2D UI。

1. 建立四邊形。 在 BaseScene 階層中，以滑鼠右鍵按一下 [3D 物件]，然後選取 [四]。

    ![Lesson5 Chapter2 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. 適當地重新置放四個。 在我們的範例中，我們將 x = 0、y = 0 和 z = 1.5 遠離相機，以取得 HoloLens 2 的舒適位置。

    >[!NOTE]
    >如果四個區塊或位於先前課程中的任何內容前方，請務必將其移動，使其不會封鎖任何其他物件。

3. 將材質套用至四邊形。 這份材料將是我們將透過移動流覽手勢來進行的動作。

    ![Lesson5 Chapter2 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. 在 [專案] 面板的 [搜尋] 方塊中，輸入「pan 內容」。 將該材料拖曳到場景中的四個。

    >[!NOTE]
    >PanContent 材料不是 MRTK 的一部分，而是包含在上一課匯入的 BaseModuleAssets 資產中。

    若要使用平移手勢，您需要在物件上使用碰撞器。 您可能會看到四邊形已經有一個網格碰撞器。 然而，網格碰撞器並不理想，因為它非常薄並且難以選取。 我們建議用方塊碰撞器取代網格碰撞器。

5. 以滑鼠右鍵按一下 [偵測器] 面板上 [四個] 的網格碰撞。 然後按一下 [移除元件] 將它移除。

    ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)

6. 現在，按一下 [新增元件] 並搜尋「方塊碰撞器」，以新增方塊碰撞器。 預設新增的方塊碰撞，仍然太精簡，因此請按一下 [編輯碰撞] 按鈕進行編輯。 按下它時，可以使用 x、y 和 z 值或場景編輯器中的元素調整大小。 針對我們的範例，我們希望將方塊碰撞器延伸到四邊形後面。 在場景編輯器中，從後面向外拖曳方塊碰撞器 (請參閱下圖)。 這可讓使用者不只使用手指，而是要滾動的全手勢。

    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)

7. 使其具互動性。 因為我們想要直接與四個程式互動，所以我們想要使用我們在第4課用來從顆 octa 物件播放音樂的近距離互動 Touchable 元件。 按一下 [新增元件]，搜尋「接近互動 touchable」並加以選取，如下圖所示。

    ![mrlearning-base-ch5-2-step7a .png](images/mrlearning-base-ch5-2-step7a.png)

    如果您看到關於界限和/或中心不符合 BoxCollider 大小和/或中心的黃色警告，請按一下 [修正範圍] 和/或 [修正中心] 按鈕，以更新中間和界限值。

    ![mrlearning-base-ch5-2-step7b .png](images/mrlearning-base-ch5-2-step7b.png)

8. 新增可辨識平移手勢的功能。 按一下 [新增元件]，在 [搜尋] 欄位中輸入「手互動」，然後新增「手互動」的「流覽縮放腳本」元件。

    ![mrlearning-base-ch5-2-step8a .png](images/mrlearning-base-ch5-2-step8a.png)

    如此一來，您就有一個啟用 pan 的四個。

    如您所見，「手互動」的「流覽縮放腳本」元件具有各種設定，做為選擇性的練習，您可以自由地玩。

    ![mrlearning-base-ch5-2-step8b .png](images/mrlearning-base-ch5-2-step8b.png)

9. 接下來，我們將學習如何平移 3D 物件。

    在階層中，以滑鼠右鍵按一下 [四個物件]，以開啟關聯式快顯功能表，然後選取 [ **3D 物件** > **Cube** ]，將 cube 加入場景中。

    請確定 Cube 的**位置**設定為_0，0，0，_ 使其整齊地放在四個內。 將 Cube 相應縮小至_0.1、0.1、0.1_的**規模**。

    ![mrlearning-base-ch5-2-step9 .png](images/mrlearning-base-ch5-2-step9.png)

    將 Cube 複製三次，方法是以滑鼠右鍵按一下 Cube，開啟關聯式快顯功能表，然後選取 [**複製**]。

    將 cube 平均隔開。 您的場景看起來應該如下圖所示。

10. 按住 CTRL 鍵，同時選取 [階層] 面板中的每個**Cube**物件，以將 MoveWithPan 腳本新增至所有 cube。 在 [偵測器] 面板中，按一下 [加入元件]，然後搜尋並選取 [**使用平移腳本移動**]，將它新增至所有 cube。

    ![mrlearning-base-ch5-2-step10a .png](images/mrlearning-base-ch5-2-step10a.png)

    >[!NOTE]
    >MoveWithPan 腳本不是 MRTK 的一部分，而是包含在上一課匯入的 BaseModuleAssets 資產中。

    在仍選取 cube 的情況下，將**四**個物件從 [階層] 面板拖曳至 [**移動流覽**腳本] 元件的 [**平移輸入來源**] 欄位中。

    ![mrlearning-base-ch5-2-step10b .png](images/mrlearning-base-ch5-2-step10b.png)

    現在，cube 會隨著您的移動流覽手勢移動。

    >[!TIP]
    >每個 cube 上的 MoveWithPan 實例會接聽四個物件上的 HandInteractionPanZoom 實例所傳送的 PanUpdated 事件，我們已新增至每個 cube 上的 [移動流覽輸入來源] 欄位，並據以更新個別 cube 物件的位置。

    在仍選取 cube 的情況下，將它們沿著 Z 軸向後移動，讓每個 cube 的網格都在**四**個方塊的**碰撞**器內，方法是將其**位置 Z**值變更為_0.7_。

    ![mrlearning-base-ch5-2-step10c .png](images/mrlearning-base-ch5-2-step10c.png)

    現在，如果您在 [偵測器] 面板中取消核取，以停用**四**個**網格**轉譯器元件，您將會有一個不可見的四個，您可以在其中流覽3d 物件清單。

    ![mrlearning-base-ch5-2-step10d .png](images/mrlearning-base-ch5-2-step10d.png)

## <a name="eye-tracking"></a>眼球追蹤

在本節中，我們將探討如何在我們的示範中啟用眼睛追蹤。 當您的眼睛 gazed 時，我們會慢慢旋轉3D 功能表項目。 當選取注視項目時，我們也會觸發有趣的效果。

1. 請確定已正確設定 MRTK 設定檔以進行眼追蹤。 若要這麼做，請移至[MRTK 指示中的開始使用眼睛追蹤](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html)，並查看[設定眼追蹤逐步](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-eye-tracking-step-by-step)執行一節中的步驟，確認是否已正確設定眼睛追蹤。 完成檔中剩餘的步驟。

    >[!NOTE]
    >如果您使用 DefaultHoloLens2InputSystemProfile （如[設定混合現實工具](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#configure-the-mixed-reality-toolkit)組課程中所述）來複製您的自訂 MRTK 設定設定檔，則依預設會在 unity 專案中啟用監看追蹤，但您仍然必須設定 unity 編輯器的眼睛追蹤模擬，並設定 Visual Studio 以允許組建的眼追蹤。

    上述連結提供下列事項的簡短指示：

    - 建立要在 MRTK 設定檔中使用的 Windows Mixed Reality 眼注視 Data Provider
    - 在連接至相機的注視提供者中啟用眼睛追蹤
    - 在 Unity 編輯器中設定眼睛追蹤模擬
    - 編輯 Visual Studio 解決方案的功能，以允許在建置的應用程式中進行眼球追蹤

2. 將眼球追蹤目標元件新增至目標物件。 若要讓物件回應眼睛眼事件，我們必須在每個想要使用眼睛互動的物件上新增 EyeTrackingTarget 元件。 將此元件新增至作為方格集合一部分之九個 3D 物件中的每一個。

    >[!TIP]
    >您可以使用 Shift 和/或 CRTL 鍵選取階層中的多個專案，然後大量新增 EyeTrackingTarget 元件。

    ![Lesson5 Chapter3 步驟2](images/Lesson5Chapter3Step2.JPG)

3. 接下來，我們會新增 EyeTrackingTutorialDemo 腳本來進行一些令人興奮的互動。 針對方格集合中的每個3D 物件，藉由在 [加入元件] 功能表中搜尋元件來新增 EyeTrackingTutorialDemo 腳本。

    ![Lesson5 Chapter3 步驟3](images/Lesson5Chapter3Step3.JPG)

    >[!NOTE]
    >EyeTrackingTutorialDemo 腳本資料不是 MRTK 的一部分，而是包含在上一課匯入的 BaseModuleAssets 資產中。

4. 在注視目標時旋轉物件。 我們想要設定我們的3D 物件，以在我們查看時旋轉。 若要這麼做，請在查看 EyeTrackingTarget 元件的 Target （）區段時，在中插入新的欄位，如下圖所示。

    ![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)

    在新建立的欄位中，將目前的遊戲物件新增至空白欄位，然後選取 [EyeTrackingTutorialDemo > RotateTarget （）]，如下圖所示。 現在，3D 物件被設定為在透過眼球追蹤注視時旋轉。

    ![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)

5. 加入「中斷目標」的功能，這是以點按方式選取，或說出「select」時所 gazed 的。 與步驟4類似，我們想要藉由將 EyeTrackingTutorialDemo 指派給 EyeTrackingTarget 元件的遊戲物件的 Select （）欄位來觸發 > BlipTarget （），如下圖所示。 現在設定完成後，每當您觸發選取動作（例如，按下點或語音命令「選取」）時，就會注意到遊戲物件有些許中斷。

    ![Lesson5 Chapter3 步驟5](images/Lesson5Chapter3Step5.JPG)

6. 在建置 HoloLens 2 之前，請確定已正確設定眼球追蹤功能。 在撰寫本文時，Unity 尚未能夠設定眼追蹤功能的注視輸入。 需要設定這項功能，眼睛追蹤才能在 HoloLens 2 中工作。 請遵循在[HoloLens 2 上測試 Unity 應用程式](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2)的指示，以啟用注視輸入功能。

## <a name="congratulations"></a>恭喜您

您已成功將基本眼追蹤功能新增至您的應用程式。 這些動作只是眼球追蹤功能無限可能性的開端。 本章也會在第5課結束，我們已瞭解先進的輸入功能，例如語音命令、移動流覽手勢和眼追蹤。

[下一課： 7. 建立農曆模組範例應用程式](mrlearning-base-ch6.md)
