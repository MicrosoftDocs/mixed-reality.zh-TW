---
title: 眼球追蹤
description: HoloLens 2 將全像攝影體驗的內容和人類理解能力帶入了新境界；它讓開發人員能夠運用使用者視線方向的相關資訊。
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: 眼睛追蹤，混合現實，輸入，眼睛眼，校正
ms.openlocfilehash: 60de5ceb9f55ca7e2f74856af9bd75567763e382
ms.sourcegitcommit: a5dc182da237f63f0487d40a2e11894027208b6c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2019
ms.locfileid: "73441114"
---
# <a name="eye-tracking-on-hololens-2"></a>HoloLens 2 的眼球追蹤

![MRTK 中的眼睛追蹤示範](images/mrtk_et_scenemenu.jpg)

HoloLens 2 將全像攝影體驗的內容和人類理解能力帶入了新境界；它讓開發人員能夠運用使用者視線方向的相關資訊。 本頁概述開發人員和設計人員如何從各種使用案例和基本開發人員指引的眼睛追蹤中獲益的新功能。 


## <a name="calibration"></a>效果 
為了讓眼追蹤能夠準確地工作，每位使用者都必須經歷[眼睛追蹤使用者校正](calibration.md)，使用者必須查看一組全像攝影目標。 這可讓裝置調整系統，讓使用者能夠更舒適且更高品質的觀賞體驗，並確保同時精確地追蹤。 眼睛追蹤應該適用于大部分的使用者，但在少數情況下，使用者可能無法成功校準。
若要深入瞭解校正以及如何確保順暢的體驗，請查看我們的[眼睛追蹤使用者校準](calibration.md)頁面。


## <a name="device-support"></a>裝置支援
<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>特徵</strong></td>
     <td><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
</tr>
<tr>
     <td>眼睛</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

## <a name="available-eye-tracking-data"></a>可用的眼睛追蹤資料
在深入瞭解眼睛輸入的特定使用案例之前，我們想要簡要指出 HoloLens 2[眼追蹤 API](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose)所提供的功能。 開發人員可以在大約_30 FPS （30 Hz）_ 的情況中，存取單一眼睛光線（注視原點和方向）。
如需有關如何存取眼睛追蹤資料的詳細資訊，請參閱我們的開發人員指南，以瞭解如何使用[DirectX 中的眼睛](gaze-in-directx.md)和[Unity 中的眼睛](https://aka.ms/mrtk-eyes)。

預測的眼睛大約是在實際目標周圍以視覺角度的1.5 度為單位（請參閱下圖）。 由於預期會有些許 imprecisions，因此開發人員應該規劃此下限值的某些邊界（例如，2.0-3.0 度可能會導致更舒適的體驗）。 我們將在下面詳細說明如何解決選取的小型目標。 為了讓眼球追蹤精準運作，每個使用者都必須接受眼球追蹤使用者校正。 

![距離 2 公尺的最佳目標大小](images/gazetargeting-size-1000px.jpg)<br>
*雙計量距離的最佳目標大小*

<br>

## <a name="use-cases"></a>使用案例
眼球追蹤可讓應用程式即時追蹤使用者的視線方向。 下列使用案例說明在 HoloLens 2 上，混合現實中可能會有的一些互動。
請注意，這些使用案例尚未包含在全像攝影介面的體驗中（也就是當您啟動 HoloLens 2 時所看到的介面）。
您可以在[Mixed Reality 工具](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)組中試用其中一些專案，其中提供幾個有趣且強大的範例來使用眼睛追蹤，例如快速且輕鬆地支援的目標選取，以及自動以文字為基礎的滾動使用者查看的內容。 

### <a name="user-intent"></a>使用者意圖    
使用者查看位置和內容的相關資訊，可**為其他輸入**（例如語音、手和控制器）提供強大的內容。
這可以運用在各種不同的工作上。
例如，只要查看全像投影並說「*選取*」（也請參閱[注視和認可](gaze-and-commit.md)），或說出「 *put this ...* 」，然後查看使用者的位置，就可以在整個場景中快速且輕鬆地**設定其目標**。想要放置全息的影像，並說「 *。其中有*「。 您可以在[混合實境工具組 - 視線導向目標選取](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html)和[混合實境工具組 - 視線導向目標定位](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Positioning.html)中找到相關範例。

此外，使用者意圖的範例可能包括使用使用者查看的相關資訊，以強化與虛擬代理程式和互動式全息式的資料的互動。 比方說，虛擬代理程式可能會根據目前所看到的內容，調整可用的選項及其行為。 

### <a name="implicit-actions"></a>隱含動作
隱含動作的類別與使用者意圖有密切的關係。
其概念是，全息影像或使用者介面專案會以本能的方式回應，這可能不會覺得使用者與系統互動，而是讓系統和使用者保持同步。其中一個範例是以**眼睛為基礎的自動滾動**，其中使用者可以讀取長文字，當使用者到達文字方塊底部時，會自動開始滾動，讓使用者不需要進入手指就能繼續閱讀。  
重點是，捲動速度會適應使用者的閱讀速度。
另一個例子是，**眼睛支援的縮放和平移**，讓使用者可以感受到他或她專注于的樣子。 觸發縮放和控制縮放速度可以透過語音或手寫輸入來控制，這對於提供使用者感覺控制，同時避免被淹沒的情況很重要。 我們將在下面詳細說明這些設計考慮。 一旦放大之後，使用者就可以順暢地遵循，例如，使用眼睛眼來探索他的鄰近地區。
您可以在[混合實境工具組 - 視線導向瀏覽](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html)範例中找到這類互動的示範。

_隱含動作_的其他使用案例可能包括：
- **智慧型通知：** 在您要尋找的位置，感到苦惱的通知會立即出現嗎？ 考慮到使用者所需注意的事項，您可以藉由抵銷使用者目前撥雲見日的通知，讓這項體驗更好。 這會限制分散注意力，並在使用者完成讀取之後自動予以關閉。 
- **用心的全息影像：** 在 gazed 時，會稍微反應的全息影像。 其範圍從稍微照亮的 UI 元素，到虛擬狗的緩慢綻放花卉，一開始會回頭查看使用者並 wagging 其結尾。 這項互動可能會在您的應用程式中提供有意義的連線和滿意度。

### <a name="attention-tracking"></a>注意力追蹤   
使用者查看位置或內容的相關資訊是一種功能強大的工具，可評估設計的可用性，並找出有效率的工作流程中的問題。 目視追蹤視覺效果和分析是各種應用程式領域中的常見做法。 在 HoloLens 2 中，我們會提供新的維度給這項瞭解，因為3D 的全息影像可以放在真實世界的內容中，並據此進行評估。 [Mixed Reality 工具](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)組提供記錄和載入眼睛追蹤資料的基本範例，以及如何將其視覺化。

同屬此領域的其他應用程式包括： 
-   **遠端眼式視覺效果：** 視覺化遠端共同作業者正在查看哪些內容來增加共用的瞭解。
-   **使用者研究研究：** 注意追蹤可協助您進一步瞭解我們如何認知並與我們的環境互動，這可能有助於更本能的人類電腦互動。 
-   **訓練：** 改善新手的訓練，進一步瞭解專家的視覺效果搜尋模式，以及其對複雜工作的操作方式，例如分析醫療資料或在作業機械。
-   **設計評估和市場研究：** 目視追蹤是在評估網站和產品設計時，用於市場研究的常用工具。 使用 HoloLens 2，我們可以合併數位產品設計變化與實體環境，將此延伸至3D 空間。 

### <a name="additional-use-cases"></a>其他使用案例
- **遊戲：** 您是否想要超能力？ 機會來了！ 您可以透過開始來 levitate 全像投影。 從眼睛中取得鐳射字形狀-試試[RoboRaid 中的 HoloLens 2](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)。
將敵人變成石頭，或將其凍結。 您可以用 X 光視線掃描建築物。 您想得到的都行！
請注意，使用者不會太多-若要深入瞭解，請參閱我們的[眼睛型輸入設計指導方針](eye-gaze-interaction.md)。

- **表達虛擬人偶：** 眼睛追蹤有助於更具表達性的3D 虛擬人偶，方法是使用即時監看追蹤資料，以動畫顯示使用者正在查看的內容。 

- **文字輸入：** 眼睛追蹤可用來做為低度文字輸入的替代專案，特別是當語音或手不方便使用時。 

<br>

## <a name="using-eye-gaze-for-interaction"></a>使用眼睛來互動
建立利用快速移動眼目標的互動可能是一項挑戰。
一方面，眼睛的移動速度很快，因此您必須小心瞭解如何使用眼睛眼輸入，因為其他使用者可能會發現這種體驗很龐大或混亂。 另一方面，您也可以建立真正的神奇體驗，以激發您的使用者！ 為協助您，請查看我們的重要優點、挑戰和設計建議，以瞭解[互動](eye-gaze-interaction.md)。 

<br>
 
## <a name="dev-guidance-what-if-eye-tracking-is-not-available"></a>開發人員指導方針：如果無法使用眼睛追蹤，該怎麼辦？
在某些情況下，您的應用程式可能不會因為各種原因而收到任何眼睛追蹤資料，包括但不限於：
* 使用者已略過眼睛追蹤校準。
* 使用者已校正，但決定不授與您的應用程式使用其眼追蹤資料的許可權。
* 使用者具有獨特的眼鏡，或系統尚不支援的一些眼睛狀況。
* 外部因素會抑制可靠的眼睛追蹤，例如 HoloLens 面板或眼鏡上的塗抹、強烈的直接陽光與遮蔽，因為眼睛前方的頭髮。

身為應用程式開發人員，這表示您必須考慮如何支援可能無法使用眼追蹤資料的使用者。 我們會先說明如何偵測眼追蹤是否可用，以及如何解決不同應用程式無法使用的情況。

### <a name="1-how-to-detect-that-eye-tracking-is-available"></a>1. 如何偵測是否有可用的眼睛追蹤
有幾個檢查可判斷是否可以使用眼睛追蹤資料。 檢查是否 。
* ...系統完全支援眼追蹤。 呼叫下列*方法*： [EyesPose. IsSupported （）](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)

* ...使用者已校正。 呼叫下列*屬性*： [EyesPose. IsCalibrationValid](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)

* ...使用者已提供您的應用程式許可權來使用其眼追蹤資料：取出目前的 _' GazeInputAccessStatus '_ 。 如需如何執行此動作的範例，請前往[要求存取注視輸入](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input)。

此外，您可能會想要藉由在收到的眼睛追蹤資料更新之間加上超時時間來檢查您的眼睛追蹤資料是否過時，如下所述。 

如上所述，有幾個原因可能無法使用眼睛追蹤資料。 雖然有些使用者可能會基本思考模式決定撤銷其眼追蹤資料的存取權，而且可以將較差的使用者體驗取捨到不提供存取其眼追蹤資料的隱私權，在某些情況下，這可能是不慎的。 因此，如果您的應用程式使用眼追蹤，而且這是經驗的重要部分，我們建議您清楚地與使用者溝通。 請通知使用者，追蹤對您的應用程式很重要的原因（甚至是列出一些增強的功能），您的應用程式可能會有充分的潛能，協助使用者進一步瞭解所放棄的內容。 協助使用者識別眼睛追蹤可能無法運作的原因（根據上述檢查），並提供一些建議以快速疑難排解可能的問題。 例如，如果您可以偵測到系統支援監看追蹤，則使用者會經過校正，甚至也會獲得其許可權，但不會收到任何其他問題，例如一些其他問題，像是塗抹或 pixels occluded 的眼睛。 請注意，在少數情況下，使用者可能會無法正常執行眼追蹤。 因此，請重視，允許關閉或甚至停用提醒，以在應用程式中啟用眼睛追蹤。

### <a name="2-fallback-for-apps-using-eye-gaze-as-a-primary-input-pointer"></a>2. 使用眼睛作為主要輸入指標的應用程式的 Fallback
如果您的應用程式使用眼睛眼做為指標輸入，以快速選取場景中的全像投影，但眼睛追蹤資料無法使用，建議您回到前端，並開始顯示列印頭游標。 我們建議使用 timeout （例如500–1500毫秒）來判斷是否要切換。 這是為了避免每次系統因快速監看或動畫快遞而短暫遺失追蹤時，都要清除游標。 如果您是 Unity 開發人員，則已在混合現實工具組中處理自動回復為頭部。 如果您是 DirectX 開發人員，您必須自行處理此交換器。

### <a name="3-fallback-for-other-eye-tracking-specific-applications"></a>3. 針對其他眼睛追蹤特定應用程式的回退
您的應用程式可能會以專為眼睛量身打造的獨特方式來使用眼睛，例如，用來製作圖片的外觀，或是以眼睛為基礎的注意熱度圖依賴視覺效果的精確資訊。 在此情況下，沒有任何明確的回溯。 如果無法使用眼睛追蹤，可能只需要停用這些功能。
同樣地，我們建議您與不知道功能無法運作的使用者清楚溝通。

<br>

這個頁面希望能讓您開始瞭解 HoloLens 2 的眼睛追蹤和眼睛輸入的角色。 若要開始進行開發，請查看我們的資訊，[瞭解如何與全息影像互動](eye-gaze-interaction.md)、 [Unity 中的眼睛](https://aka.ms/mrtk-eyes)，以及[DirectX 中的眼睛](gaze-in-directx.md)。


## <a name="see-also"></a>請參閱
* [校正](calibration.md)
* [舒適度](comfort.md)
* [眼睛眼的互動](eye-gaze-interaction.md)
* [在 DirectX 中的眼睛](gaze-in-directx.md)
* [Unity 中的眼睛（混合現實工具組）](https://aka.ms/mrtk-eyes)
* [注視和認可](gaze-and-commit.md)
* [語音輸入](voice-design.md)


