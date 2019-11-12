---
title: 眼球追蹤
description: HoloLens 2 讓開發人員能夠使用使用者所查看之內容的相關資訊，在全像攝影體驗中提供新的內容層級和人類認知。
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: 眼睛追蹤，混合現實，輸入，眼睛眼，校正
ms.openlocfilehash: 88c1827d3656ceb851e8f778daa2303b88dd17c8
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913218"
---
# <a name="eye-tracking-on-hololens-2"></a>HoloLens 2 的眼球追蹤

![MRTK 中的眼睛追蹤示範](images/mrtk_et_scenemenu.jpg)

HoloLens 2 讓開發人員能夠使用使用者所查看之內容的相關資訊，在全像攝影體驗中提供新的內容層級和人類認知。 本頁面會告訴開發人員如何從各種使用案例的眼睛追蹤中獲益，以及設計眼睛眼的使用者互動時的外觀。 

眼睛追蹤 API 已設計成使用者的隱私權，避免傳遞任何可識別的資訊，特別是任何生物識別。 對於具備目視追蹤功能的應用程式，使用者必須授與應用程式許可權，以使用目視追蹤資訊。 


### <a name="device-support"></a>裝置支援
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

<br>

## <a name="calibration"></a>效果 
為了讓眼追蹤能夠準確地工作，每位使用者都必須經歷[眼睛追蹤使用者校正](calibration.md)，使用者必須查看一組全像攝影目標。 這可讓裝置調整系統，讓使用者能夠更舒適且更高品質的觀賞體驗，並確保同時精確地追蹤。 

眼睛追蹤應該適用于大部分的使用者，但在少數情況下，使用者可能無法成功校準。 校正可能因各種原因而失敗，包括但不限於： 
* 使用者先前退出宣告校正程式
* 使用者有注意力，而未遵循校正目標
* 使用者有特定類型的 contact 鏡頭和眼鏡，但系統尚未支援 
* 使用者有特定的眼睛生理學、眼睛狀況或系統尚未支援的眼睛外科  
* 外部因素抑制了可靠的眼睛追蹤，例如 HoloLens 面板或眼鏡上的塗抹、強烈的直接陽光與遮蔽，因為眼睛前方的頭髮

開發人員應務必為可能無法使用眼追蹤資料的使用者提供適當的支援（無法成功校準）。 我們已在此頁面底部的一節中，提供回溯解決方案的建議。 

若要深入瞭解校正以及如何確保順暢的體驗，請查看我們的[眼睛追蹤使用者校準](calibration.md)頁面。

<br>

## <a name="available-eye-tracking-data"></a>可用的眼睛追蹤資料
在深入瞭解眼睛輸入的特定使用案例之前，我們想要簡要指出 HoloLens 2[眼追蹤 API](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose)所提供的功能。 開發人員可以在大約_30 FPS （30 Hz）_ 的情況中，存取單一眼睛光線（注視原點和方向）。
如需有關如何存取眼睛追蹤資料的詳細資訊，請參閱我們的開發人員指南，以瞭解如何使用[DirectX 中的眼睛](gaze-in-directx.md)和[Unity 中的眼睛](https://aka.ms/mrtk-eyes)。

預測的眼睛大約是在實際目標周圍以視覺角度的1.5 度為單位（請參閱下圖）。 由於預期會有些許 imprecisions，因此開發人員應該規劃此下限值的某些邊界（例如，2.0-3.0 度可能會導致更舒適的體驗）。 我們將在下面詳細說明如何解決選取的小型目標。 為了讓眼球追蹤精準運作，每個使用者都必須接受眼球追蹤使用者校正。 

![2 個計量表距離的最佳目標大小](images/gazetargeting-size-1000px.jpg)<br>
*雙計量距離的最佳目標大小*

<br>

## <a name="use-cases"></a>使用案例
眼球追蹤可讓應用程式即時追蹤使用者的視線方向。 下列使用案例說明在 HoloLens 2 上，混合現實中可能會有的一些互動。
請注意，這些使用案例尚未包含在全像攝影介面的體驗中（也就是當您啟動 HoloLens 2 時所看到的介面）。
您可以在[Mixed Reality 工具](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)組中試用其中一些專案，其中提供幾個有趣且強大的範例來使用眼睛追蹤，例如快速且輕鬆地支援的目標選取，以及自動以文字為基礎的滾動使用者查看的內容。 

### <a name="user-intent"></a>使用者意圖    
使用者查看位置和內容的相關資訊，可**為其他輸入**（例如語音、手和控制器）提供強大的內容。
這可以運用在各種不同的工作上。
例如，只要查看全像投影並說「*選取*」（也請參閱[注視和認可](gaze-and-commit.md)），或說出「 *put this ...* 」，然後查看使用者的位置，就可以在整個場景中快速且輕鬆地**設定其目標**。想要放置全息的影像，並說「 *.。。其中有*「。 您可以在[混合實境工具組 - 視線導向目標選取](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html)和[混合實境工具組 - 視線導向目標定位](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Positioning.html)中找到相關範例。

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
使用者查看位置或內容的相關資訊可以是功能強大的工具，它可以協助您評估設計的可用性，並找出工作流程中的問題，使其更有效率。
目視追蹤視覺效果和分析是各種應用程式領域中的常見做法。 在 HoloLens 2 中，我們會提供新的維度給這項瞭解，因為3D 的全息影像可以放在真實世界的內容中，並據此進行評估。 [Mixed Reality 工具](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)組提供記錄和載入眼睛追蹤資料的基本範例，以及如何將其視覺化。
Microsoft 致力於促進創新，同時確保使用者可以透過其眼追蹤資訊的使用方式，獲得提供通知和透明的體驗。  我們會與開發人員和 UX 小組合作，為協力廠商提供指引，確保體驗是以使用者為中心。  


同屬此領域的其他應用程式包括： 
-   **遠端眼式視覺效果：** 遠端監看式視覺效果：將遠端共同作業者正在查看的內容視覺化，以提供立即的意見反應，並加速更精確的資訊處理。
-   **使用者研究研究：** 注意追蹤可協助研究人員深入瞭解使用者如何察覺和與自然環境互動，而不會干擾，以設計更本能的人電腦互動。 眼睛追蹤可以提供研究中的參與者不直接表達的資訊，但研究員可能會很容易錯過。 
-   **定型和效能監視：** 藉由在執行流程中更有效率地識別瓶頸，來練習並優化工作的執行作業。 眼睛追蹤可以提供自然的即時和目標資訊，協助改善工作場所的訓練、生產力和安全性。 
-   **設計評估、行銷和消費者研究：** 眼睛追蹤讓商業公司能夠在實際環境中執行行銷和取用者研究，或分析哪些內容會吸引使用者注意，以改善產品或空間設計。 

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
 
## <a name="fallback-solutions-when-eye-tracking-is-not-available"></a>無法使用眼睛追蹤時的回溯解決方案

在罕見的情況下，可能無法使用目視追蹤資料。
這可能是因為以下列出最常見的不同原因：
* 系統無法[校正使用者](calibration.md)。
* 使用者已略過[校正](calibration.md)。   
* 使用者已校正，但決定不授與您的應用程式使用其眼追蹤資料的許可權。    
* 使用者具有獨特的眼鏡，或系統尚不支援的一些眼睛狀況。    
* 外部因素會抑制可靠的眼睛追蹤，例如 HoloLens 面板或眼鏡上的塗抹、強烈的直接陽光與遮蔽，因為眼睛前方的頭髮。   

因此，開發人員應該確保這些使用者有適當的回溯支援。 在 [ [DirectX 中](gaze-in-directx.md#fallback-when-eye-tracking-is-not-available)的監看追蹤] 頁面上，我們會說明偵測是否有可用的監看追蹤資料所需的 api。 

雖然有些使用者可能會基本思考模式決定撤銷其眼追蹤資料的存取權，而且可以將較差的使用者體驗取捨到不提供存取其眼追蹤資料的隱私權，在某些情況下，這可能是不慎的。  
因此，如果您的應用程式使用眼追蹤，而且這是經驗的重要部分，我們建議您清楚地與使用者溝通。     
請通知使用者，追蹤對您的應用程式很重要的原因（甚至是列出一些增強的功能），您的應用程式可能會有充分的潛能，協助使用者進一步瞭解所放棄的內容。    
協助使用者識別眼睛追蹤可能無法運作的原因（根據上述檢查），並提供一些建議以快速疑難排解可能的問題。  
例如，如果您可以偵測到系統支援監看追蹤，則使用者會經過校正，甚至也會獲得其許可權，但不會收到任何其他問題，例如一些其他問題，像是塗抹或 pixels occluded 的眼睛。    
請注意，在少數情況下，使用者可能會無法正常執行眼追蹤。    
因此，請重視，允許關閉或甚至停用提醒，以在應用程式中啟用眼睛追蹤。

### <a name="fallback-for-apps-using-eye-gaze-as-a-primary-input-pointer"></a>使用眼睛作為主要輸入指標的應用程式的 Fallback
如果您的應用程式使用眼睛眼做為指標輸入，以快速選取場景中的全像投影，但眼睛追蹤資料無法使用，建議您回到前端，並開始顯示列印頭游標。 我們建議使用 timeout （例如500–1500毫秒）來判斷是否要切換。 這是為了避免每次系統因快速監看或動畫快遞而短暫遺失追蹤時，都要清除游標。 如果您是 Unity 開發人員，則已在混合現實工具組中處理自動回復為頭部。 如果您是 DirectX 開發人員，您必須自行處理此交換器。

### <a name="fallback-for-other-eye-tracking-specific-applications"></a>其他眼睛追蹤特定應用程式的回退
您的應用程式可能會以專為眼睛量身打造的獨特方式來使用眼睛，例如，用來製作圖片的外觀，或是以眼睛為基礎的注意熱度圖依賴視覺效果的精確資訊。 在此情況下，沒有任何明確的回溯。 如果無法使用眼睛追蹤，可能只需要停用這些功能。
同樣地，我們建議您與不知道功能無法運作的使用者清楚溝通。

<br>

這個頁面希望能讓您開始瞭解 HoloLens 2 的眼睛追蹤和眼睛輸入的角色。 若要開始進行開發，請查看我們的資訊，[瞭解如何與全息影像互動](eye-gaze-interaction.md)、 [Unity 中的眼睛](https://aka.ms/mrtk-eyes)，以及[DirectX 中的眼睛](gaze-in-directx.md)。


## <a name="see-also"></a>請參閱
* [校正](calibration.md)
* [舒適度](comfort.md)
* [眼部目光導向的互動](eye-gaze-interaction.md)
* [在 DirectX 中的眼睛](gaze-in-directx.md)
* [Unity 中的眼睛（混合現實工具組）](https://aka.ms/mrtk-eyes)
* [目光和行動](gaze-and-commit.md)
* [語音輸入](voice-design.md)


