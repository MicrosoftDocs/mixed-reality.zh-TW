---
title: 舒服
description: 在自然觀賞期間，人為視覺系統會依賴多個資訊來源，或「提示」來解讀3D 形狀和物件的相對位置。
author: erickjpaul
ms.author: erpau
ms.date: 04/5/2019
ms.topic: article
keywords: 混合現實、設計、舒適、HoloLens 2、HoloLens （第1代）
ms.openlocfilehash: e71b8d73a37a5d10a07d37d91cf14c88b7a85687
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436391"
---
# <a name="comfort"></a>舒服

在自然觀賞期間，人為視覺系統會依賴多個資訊來源，或「提示」來解讀3D 形狀和物件的相對位置。 有些提示只依賴單一眼（monocular 提示），包括[線性觀點](https://en.wikipedia.org/wiki/Perspective_(graphical))、熟悉的[大小](https://en.wikipedia.org/wiki/Size#Perception_of_size)、遮蔽、[深度的模糊](https://en.wikipedia.org/wiki/Depth_of_field)和[住宿](https://en.wikipedia.org/wiki/Accommodation_(eye))。 其他提示則依賴兩個眼睛（binocular 提示），並包含[vergence](https://en.wikipedia.org/wiki/Vergence) （基本上是查看物件所需之眼睛的相對旋轉）和[binocular 差異](https://en.wikipedia.org/wiki/Stereopsis)（場景在兩眼的背面）。 為了確保頭戴顯示器的最大舒適度，設計人員和開發人員必須以模擬這些提示在自然世界中運行的方式來建立和呈現內容。 從實體的觀點來看，設計不需要頸部或臂 fatiguing 運動的內容也很重要。 在本文中，我們將討論重要的考慮，以確保達到這些目標。

## <a name="vergence-accommodation-conflict"></a>Vergence-住宿衝突

若要清楚地觀賞物件，人類必須[配合](https://en.wikipedia.org/wiki/Accommodation_%28eye%29)物件的距離，或將其眼睛的焦點調整至物件。 同時，這兩個眼睛的旋轉必須[收斂](https://en.wikipedia.org/wiki/Convergence_(eye))于物件的距離，以避免看到雙重影像。 在自然觀賞中，會連結 vergence 和住宿。 當您觀賞附近的東西（例如靠近鼻子的 housefly）時，您的眼睛會交叉並配合接近點。 相反地，如果您以光學無限大（大約是從6m 開始，或針對一般視覺）來查看，您的眼睛就會變得平行，而您的眼睛鏡頭會被無限大。 

在大部分的前端掛接顯示器中，使用者一律會配合顯示的邊緣距離（以取得清晰的影像），但會收斂到感興趣物件的距離（以取得單一影像）。 當使用者配合並融合到不同的距離時，兩個提示之間的自然連結必須中斷，而這可能會導致視覺 discomfort 或疲勞。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/-606oZKLa_s" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### <a name="guidance-for-holographic-devices"></a>全像攝影裝置的指引

HoloLens 顯示器的固定距離與使用者相距大約 2.0 m。 因此，使用者永遠都必須容納近 2.0 m，才能在裝置中維護清楚的影像。 應用程式開發人員可以在各種深度放置內容和全息影像，以引導使用者的眼睛融合。 Discomfort 自 vergence-住宿衝突可以避免或最小化，方法是保留使用者盡可能接近 2.0 m 的內容（亦即在有許多深度的場景中，盡可能將感興趣的區域放在使用者附近）。 當內容無法放在 2.0 m 附近時，當使用者的注視在不同距離之間來回切換時，從 vergence-住宿衝突中 discomfort 是最大的。 換句話說，要查看一段時間內遠離您的全像投影50cm 的全像50cm，可以更輕鬆地查看靜止的全息影像。

![從使用者處放置全息影像的最佳距離。](images/distanceguiderendering-950px.png)<br>
*從使用者處放置全息影像的最佳距離*

### <a name="best-practices-for-hololens-1st-gen-and-hololens-2"></a>HoloLens （第1代）和 HoloLens 2 的最佳作法

為獲得最大的緩和度，全像投影**位置的最佳區域是介於 1.25 m 和5m 之間**。 在每一種情況下，設計人員都應該嘗試結構內容場景，以鼓勵使用者與內容互動（例如，調整[內容大小和預設位置參數](gaze-and-commit.md)）。 

雖然內容可能偶爾會顯示在1百萬的附近，但我們建議您不要呈現比40cm 更接近的全息影像。 因此，建議您開始在**40cm 淡出內容，並將轉譯裁剪平面放在 30cm** ，以避免任何接近的物件。

因為 vergence-便利的衝突，而移動深度的物件比固定物件更有可能產生 discomfort。 同樣地，要求使用者在接近焦點和最上層之間快速切換（例如，因為需要直接互動的快顯全息物）可能會導致視覺 discomfort 和疲勞。 因此，**應採取額外的小心，將使用者的頻率降到最低：觀看深度移動的內容; 或快速切換鄰近的全像投影之間的焦點**。 

### <a name="additional-considerations-for-hololens-2-and-near-interaction-distances"></a>HoloLens 2 和接近互動距離的其他考慮

在為 HoloLens 2 中的直接（近）互動設計內容時，或**在內容必須放在更接近1百萬的任何應用程式中，請特別小心，以確保使用者的緩和**度。 因 vergence-住宿衝突而造成 discomfort 的機率，會以減少的觀賞距離呈指數方式增加。 此外，使用者在接近互動距離觀看內容時，可能會遇到 blurriness 增加的情況，因此建議您測試在最佳全息全像位置的區域中轉譯的內容，以及更靠近的範圍（少於 1.0 m 到裁剪平面）確保它保持清楚且舒適的觀看。 

**針對應用程式，建議您根據使用者預期的時間量來查看接近的內容（少於 1.0 m）並深入移動，以建立「深度預算**」。 其中一個範例是避免使用者在這些情況下，超過25% 的時間。 如果超過深度預算，我們建議謹慎地進行使用者測試，以確保它仍然是熟悉的體驗。 

一般來說，我們也建議您仔細測試，以確保幾乎互動距離的任何互動需求（例如，移動速度、可連線性等）都能讓使用者感到滿意。 


### <a name="guidance-for-immersive-devices"></a>沉浸式裝置的指引

對於沉浸式裝置，HoloLens 的指導方針和最佳作法仍然適用，但緩和區域的特定值會根據與顯示器的邊緣距離而移動。 一般而言，這些顯示的焦點距離介於 1.25 m-2.5 m 之間。 若不確定，請避免將感興趣的物件呈現給使用者附近，並改為嘗試將大部分的內容保留為1m 或更遠的地方。

## <a name="interpupillary-distance-and-vertical-offset"></a>Interpupillary 距離和垂直位移

在前端掛接的顯示器上觀看數位內容時（HMD），檢視器的眼睛相對於數位內容的顯示位置是很重要的。 具體來說，interpupillary 距離（[IPD](https://en.wikipedia.org/wiki/Pupillary_distance)）和垂直位移（VO）對於熟悉 hmd 中的數位內容非常重要。 

IPD 指的是個人眼的瞳孔或中心之間的距離。 [VO] 是指數位內容的可能垂直位移，相對於檢視器眼的水準軸（尤其是，這與水準位移不相同，或 binocular 差異）。 將這兩個因素之一或兩者都不正確地對應到個別使用者，可以惡化 discomfort 因 vergence 住宿衝突而造成的影響，但它甚至可能會造成 discomfort 的衝突降到最低（例如，針對 2.0 m 焦點顯示的內容）。HoloLens 的距離。 

### <a name="guidance-for-holographic-devices"></a>全像攝影裝置的指引

#### <a name="hololens-1st-gen"></a>HoloLens (第 1 代)

若是 HoloLens （第1代），IPD 會在裝置[校正](calibration.md)期間進行預估和設定。 針對已設定裝置的新使用者，必須執行校正，或者必須手動設定 IPD。 VO 完全取決於裝置的大小。 具體來說，若要將 VO 降到最低，裝置必須停留在使用者的前端，讓顯示器與其眼睛的軸保持層級。 

#### <a name="hololens-2"></a>HoloLens 2

若是 HoloLens 2，IPD 會在眼睛/裝置[校正](calibration.md)期間進行預估和設定。 針對已設定裝置的新使用者，必須執行校正以確保已正確設定 IPD。 在 HoloLens 2 中，會自動將 VO 納入考慮。 

### <a name="guidance-for-immersive-devices"></a>沉浸式裝置的指引

Windows Mixed Reality 沉浸式 Hmd 沒有 IPD 或 VO 的自動校正。 IPD 可以在軟體中手動設定（在混合現實入口網站設定底下，請參閱[校正](calibration.md)），或某些 hmd 具有機械滑杆，可讓使用者將鏡頭的間距調整為舒適的位置（亦即，大致符合其 IPD）。 

## <a name="rendering-rates"></a>轉譯速率

混合現實應用程式是唯一的，因為使用者可以自由地在世界各地移動，並與虛擬內容互動，就像是真正的物件一樣。 若要維護這項印象，請務必轉譯全像投影，使其在世界中看起來穩定，並以順暢的動畫呈現。 轉譯時，[每秒最少60個畫面（FPS）](understanding-performance-for-mixed-reality.md)可協助達成此目標。 有一些混合現實裝置支援在高於 60 FPS 的 framerates 轉譯，而在這些裝置上，強烈建議您在較高的 framerates 轉譯，以提供最佳的使用者體驗。

**深入探討**

若要繪製全息影像，使[其在真實或虛擬世界中看起來很穩定](hologram-stability.md)，應用程式必須從使用者的位置呈現影像。 由於影像轉譯需要時間，因此 HoloLens 和其他 Windows Mixed Reality 裝置會預測使用者的標頭在顯示畫面中顯示的位置。 這個預測演算法是近似值。 Windows Mixed Reality 演算法和硬體會調整轉譯的影像，以考慮預測的標頭位置與實際的頭部位置之間的差異。 此程式會讓使用者看到的影像看起來就像是從正確的位置轉譯，而全息全像是穩定的。 更新最適用于前端位置的小變更，而且無法完全考慮某些呈現的影像差異，例如視差所造成的差異。

**藉由以 60 FPS 的最小畫面播放速率轉譯，您會做兩件事來協助進行穩定的全息：**
1. 減少 judder 的外觀，這是以不平均的運動和雙影像為特色。 更快的全息影像動作和較低的轉譯率會與更明顯的 judder 相關聯。 因此，致力於一律維持 60 FPS （或您裝置的最大轉譯速率），有助於避免 judder 移動全息影像。
2. 將整體延遲降到最低。 在具有遊戲執行緒和在密集建置中執行之轉譯執行緒的引擎中，于30FPS 執行的會加入 33.3 ms 的額外延遲。 藉由減少延遲，這會減少預測錯誤，並增加全息影像的穩定性。

**效能分析**

您可以使用各種不同的工具來對應用程式框架速率進行基準測試，例如：
* GPUView
* Visual Studio 圖形偵錯工具
* 內建于3D 引擎中的分析工具，例如 Unity 中的框架偵錯工具

## <a name="self-motion-and-user-locomotion"></a>自我移動和使用者 locomotion

唯一的限制是您的實體空間大小;如果您想要讓使用者在虛擬環境中比在實際房間內更遠地移動，則必須執行單純的虛擬動作形式。 不過，持續的虛擬動作若不符合使用者真正的實際動作，通常會引發動作 sickness。 此結果是因為來自*虛擬世界*的自我動作*視覺提示*，與來自*真實世界*的自我運動[vestibular 提示](https://en.wikipedia.org/wiki/Vestibular_system)衝突。

幸運的是，有一些執行使用者 locomotion 的秘訣可以協助避免這個問題：
* 一律讓使用者控制其移動;非預期的自我動作特別有問題
* 人類對重心的方向非常敏感。 因此，應避免非使用者起始的垂直動作。

### <a name="guidance-for-holographic-devices"></a>全像攝影裝置的指引

允許使用者移至大型虛擬環境中另一個位置的方法之一，是讓他們在場景中移動小型物件的印象。 這種效果的實現方式如下：
   1. 提供介面，讓使用者可以在虛擬環境中選取想要移動的位置。
   2. 選取時，將場景向下縮小到所需位置周圍的磁片。
   3. 當您保留選取的位置時，允許使用者將它移出，就像是小型物件一樣。 然後使用者可以將選取範圍移到其墊腳附近。
   4. 在 deselection 時，繼續呈現整個場景。

### <a name="guidance-for-immersive-devices"></a>沉浸式裝置的指引

上述的全像攝影裝置方法在沉浸式裝置中也無法運作，因為它需要應用程式在移動「磁片」時轉譯大型黑色失效或另一個預設的環境。 這項處理會干擾深度的意義。 在沉浸式耳機中，使用者 locomotion 的一項技巧是「閃爍」的方法。 這種實現方式可讓使用者控制其動作，並提供簡單的移動印象，但讓使用者不太可能覺得單純的虛擬自我動作來 disoriented：
   1. 提供介面，讓使用者可以在虛擬環境中選取想要移動的位置。
   2. 選取時，開始對該位置進行非常快速的模擬（100 9.81/s）動作，同時快速地淡出呈現。
   3. 完成翻譯之後，請將轉譯淡入回去。

## <a name="heads-up-displays"></a>列印頭顯示

在第一員射擊的 videogames 中，會在螢幕上直接顯示（HUDs）持續呈現的資訊，例如玩家健康情況、迷你地圖和清查。 HUDs 能妥善通知玩家，而不侵遊戲經驗。 在混合現實的體驗中，HUDs 可能會造成顯著的 discomfort，而且必須調整為更沉浸的內容。 具體而言，對使用者的標頭而言，嚴格鎖定的 HUDs 可能會產生 discomfort。 如果應用程式需要抬頭顯示器，建議使用*主體*鎖定，而不是 head 鎖定。 這項處理可以實作為一組會立即與使用者一起轉譯的顯示，但是在達到旋轉的臨界值之前，不會以使用者的標頭旋轉。 一旦達成該旋轉，抬頭顯示器可能會重設，以顯示使用者的視圖欄位內的資訊。 應一律避免執行1:1 抬頭顯示器相對於使用者前端運動的旋轉和轉譯。

## <a name="text-legibility"></a>文字可讀性

最佳文字可讀性有助於降低眼睛，並維護使用者的舒適，特別是在需要使用者在 HMD 時閱讀的應用程式或案例。 文字可讀性取決於各種因素，包括各種不同的顯示內容（例如圖元密度、亮度、對比）、鏡頭屬性（例如彩色 aberration）和文字/字型屬性（例如，特定字型權數、間距、襯線等特性、字型色彩、背景色彩）。  

一般來說，我們建議您測試特定應用程式的可讀性，並讓字型大小變大，使其可用於熟悉的體驗。 我們在下面提供一般指引，做為開發的起點。 請注意，所有字型大小都會以[視覺角度](https://en.wikipedia.org/wiki/Visual_angle)的角度來報告，而不是特定的實體大小，這會提供最佳全息表位置的區域中任何距離的指引，因為它會同時包含文字大小和距離會出現在檢視器中。 

如需更詳細的指導方針，請參閱[Unity 頁面中](text-in-unity.md)的[印刷](typography.md)樣式和文字。

### <a name="guidance-for-holographic-devices"></a>全像攝影裝置的指引

對於全像攝影裝置，在白色/淺背景上轉譯黑色/深色文字會提供最一致的對比比例，因為背景會從呈現後的真實世界中遮蔽干擾。 在黑色/深色背景上轉譯白色/淺文字，可讓您透過更多真實世界的環境來顯示，這可能會干擾文字的可讀性。 

#### <a name="hololens-1st-gen"></a>HoloLens (第 1 代)

最小清晰的字型大小（從字型基準測量到 ascender）大約是0.35 °，而舒適的字型大小至少是0.5 °，以讀取與使用者2m 距離的內容。 

#### <a name="hololens-2"></a>HoloLens 2

最小清晰的字型大小（從字型基準測量到 ascender）至少是： 
   - 0.4 °-0.5 °于45cm （直接操作距離） 
   - 0.35 °-0.4 °，位於 2.0 m
   
可輕鬆辨認的字型大小（從字型基準測量到 ascender）至少是： 
   - 45cm 的0.65 °-0.8 °（直接操作距離）
   - 0.6 °-0.75 °，位於 2.0 m

請注意，在直接操作距離上，文字的字型大小必須稍微大一點，因為上面所述的 vergence-住宿衝突（使用者眼會在 HoloLens 顯示器上以 2.0 m 的距離來容納，因此內容會呈現在，例如45cm使用者可能會更模糊）。 

### <a name="guidance-for-immersive-devices"></a>沉浸式裝置的指引

由於外部環境的完整遮蔽，沉浸式裝置通常會有較高的對比比例，但因為鏡頭在顯示器前方的縮放比例，部分可能會有較低的有效圖元密度。 

對於 Windows Mixed Reality 沉浸式 Hmd，最小清晰的垂直字型大小（從字型基準測量到 ascender）約為 0.7-0.9 °，而慣用的垂直字型大小大約為1.0 °，用於讀取以2m 距離呈現的內容使用者.

## <a name="gaze-direction"></a>注視方向

為了避免眼和頸部的內容，應該設計成能避免過度眼睛和頸部的移動。
* **避免**在水準上方超過10度的注視角度（垂直移動）
* **避免**橫向角度超過60度（垂直移動）
* **避免**頸部旋轉超過45度-中心（水準移動）

最佳（下）的注視角度會被視為水準的10-20 度，因為前端傾向于稍微向下傾斜，特別是在活動期間。

![允許的視圖欄位（FOV），由頸部的運動範圍決定](images/optimal-field-of-view-2.png)<br>
*允許的視圖欄位（FOV），由頸部的移動範圍決定*

## <a name="arm-positions"></a>Arm 位置

當使用者預期會在經驗的持續期間內保持手時，肌肉疲勞可能會累積。 您也可以 fatiguing 它，要求使用者在長時間內重複進行空中碰手勢。 因此，我們建議體驗避免需要常數、重複的手勢輸入。 這專案標可以藉由合併短斷線或提供手勢和語音輸入的混合來與應用程式互動來達到。

## <a name="see-also"></a>請參閱
* [目光](gaze-and-commit.md)
* [全像投影穩定性](hologram-stability.md)
* [本能互動](interaction-fundamentals.md)
* [全像攝影框架](holographic-frame.md)
* [校正](calibration.md)
