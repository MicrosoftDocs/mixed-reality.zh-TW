---
title: 在混合現實應用程式中使用音效
description: 空間音效是強大的工具，可在混合現實應用程式中進行深度、協助工具及 UX 設計。
author: kegodin
ms.author: kegodin
ms.date: 11/02/2019
ms.topic: article
keywords: Windows Mixed Reality，空間音效，設計，樣式
ms.openlocfilehash: c069095808eaa9d31b1ffa41dbaa29c9f635837b
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641057"
---
# <a name="using-sound-in-mixed-reality-applications"></a>在混合現實應用程式中使用音效

使用音效來通知並強化使用者對於應用程式狀態的心理模型。 適當時請使用 spatialization，將音效放在混合世界中。 以這種方式連接聽覺和視覺效果，是許多互動的直覺性質，進而提高使用者的信心。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="when-should-i-add-sounds"></a>何時應新增音效？
相較于2D 螢幕上的應用程式，混合現實應用程式通常會有更大的需求，因為缺乏實體介面。 當聲音通知使用者或加強互動時，應該加入音效。

### <a name="inform-and-reinforce"></a>通知和強化
* 對於不是由使用者起始的事件（例如通知），請考慮新增聲音以通知使用者發生變更。
* 互動可能會有數個階段。 請考慮使用音效來強化階段轉換。

如需互動、事件和建議的音效特性的範例，請參閱下文。

### <a name="exercise-restraint"></a>練習擋板
使用者對於音訊資訊沒有無限的容量：
* 每個音效都應該傳達特定、重要的資訊片段
* 播放聲音以通知使用者時，暫時減少其他聲音的音量
* 若為按鈕暫留音效（請參閱下方），請新增時間延遲，以避免過多觸發聲音

### <a name="dont-rely-solely-on-sounds"></a>不要單獨依賴聲音
當您的使用者可以聽到聲音時，使用的音效會很有價值，但請確定您的應用程式即使已關閉，仍然可以使用。
* 使用者可能有聽力障礙
* 您的應用程式可能會在更高的環境中使用
* 使用者可能有隱私權或其他停用裝置音訊的原因

## <a name="how-should-i-sonify-interactions"></a>我該如何 sonify 互動？
混合現實中的互動類型包括手勢、直接操作和語音。 請使用下列建議的特性來選取或設計這些互動的聲音。

### <a name="gesture-interactions"></a>手勢互動
在混合現實中，使用者可以使用資料指標與按鈕互動。 按鈕動作通常會在使用者放開按鈕時執行，而不是按下滑鼠按鍵時，讓使用者有機會取消互動。 使用音效來強化這些階段。 此外，為了協助使用者以遠處按鈕為目標，請考慮使用游標停留音效。
* 按鈕按下音效時，請按一下 [觸覺]。 範例： [MRTK_ButtonPress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* 按鈕 unpress 聽起來應該有類似的觸覺風格。 具有凸起的音調和按下音效會強化完成的意義。 範例： [MRTK_ButtonUnpress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)
* 針對滑鼠停留音效，請考慮使用微妙且不會有危險的音效，例如低頻率 thud 或凹凸效果。


### <a name="direct-manipulation"></a>直接操作
在 HoloLens 2 上，有清楚的手勢追蹤支援使用者介面元素的直接操作。 音效是缺少實體意見反應的重要取代專案。

**按鈕按**音效在直接操作中很重要，因為使用者在到達金鑰行進的底部時，不會有實際的指示。 主要旅遊的視覺指標可以是小型、微妙和 pixels occluded。 如同筆勢互動，按下按鈕應該會有一個簡短的觸覺音效，像是按一下，unpresses 應該會有類似的點擊，而且具有凸起的音調。
* 範例： [MRTK_ButtonPress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* 範例： [MRTK_ButtonUnpress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonUnpress)

確認直接操作中的**抓取**或**發行**很容易以視覺化方式進行通訊。 使用者的手中通常會有任何視覺效果，而主體的物件則缺乏真實世界的「抓取」視覺效果。 相較之下，音效可以有效地溝通成功的抓取和發行互動。
* 抓取動作應該有一個簡短、有點 muffled 的觸覺音效，以 evokes 在物件周圍關閉的想法。 有時候，這會伴隨「竊竊私語」音效，而這會造成音效在抓取時傳達手的運動。 範例： [MRTK_Move_Start .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_Move_Start.wav)
* 發行動作應具有類似的簡短和觸覺音效，通常會從抓取音效中細分，並以相反的時間順序出現，有影響，然後是「竊竊私語」，以便將已進行的物件進行通訊。 範例： [MRTK_Move_End .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_Move_End.wav)

**繪圖**互動應具有迴圈、持續音效，其音量是由使用者的移動所控制，而在使用者的手中，它是完全無訊息的，而且當使用者的手上快速移動時，它的最大音量也是如此。



### <a name="voice-interactions"></a>語音互動
語音互動通常會有細微的視覺元素。 使用音效來強化互動階段。 請考慮選擇更多色調音效來區別它們與手勢和直接操作音效。

* 使用語音命令**確認**的正發音語氣。 增加的色調與主要的音樂間隔會在此生效。
* 針對語音命令**失敗**，請使用較短、較不正面的發音。 避免負面音效;相反地，使用更 percussive 的中性音效來溝通應用程式正在互動的情況。
* 如果您的應用程式使用喚醒字，當裝置已**開始接聽**時，請使用短暫、微妙的語調，而當應用程式接聽時，則會有輕微的迴圈音效。 

### <a name="notifications"></a>通知
通知會傳達使用者未起始的應用程式狀態變更和其他事件，例如進程完成、訊息和呼叫。

在混合現實中，移動的物件可以移出使用者的視圖欄位。 伴隨具有 hrtf 音效的**動畫物件**，取決於物件和動作速度。
* 它也有助於在動畫尾端播放 hrtf 音效，以通知使用者有新的位置
* 若為漸進式移動，移動期間的「竊竊私語」音效將有助於使用者追蹤物件

**訊息通知**很可能會聽到數次，有時會快速地連續進行。 重要的是，它不會脫離或不粗糙。 中等範圍的正面色調在此有效。

* 呼叫的品質應該與行動電話鈴聲類似。 這些通常會迴圈播放，直到使用者接聽電話為止。
* 語音通訊連線和中斷連線應該會有簡短的色調音效。 連接音效應具有正的語氣，表示連線成功，而中斷連線的音效則是表示呼叫完成的中性音效。

## <a name="spatialization"></a>Spatialization
Spatialization 使用身歷聲耳機或喇叭將音效放在混合世界中。

### <a name="which-sounds-should-i-spatialize"></a>我應該 spatialize 哪些聲音？
當音效與具有空間位置的事件產生關聯時，應該 hrtf。 這包括 UI、所包含的 AI 語音和視覺指示器。

Spatializing**使用者介面**元素會限制鎖定為其標題的身歷聲音效數目，以協助清理使用者的 sonic 「空間」。 特別是在 hrtf 音訊意見反應時，直接操作互動、觸碰、抓取和釋放感覺更為自然。 不過，請參閱以下關于這些元素的距離衰減。

Spatializing**視覺**指標和可顯示的 **AI 語音**，以直覺方式在使用者超出視野的範圍時通知他們。
    
相反地，請避免 **_faceless_ AI 語音**的 spatialization，以及沒有妥善定義空間位置的其他元素。 沒有相關視覺元素的 Spatialization 可能會讓使用者覺得找不到視覺元素。

新增 spatialization 會產生一些 CPU 成本。 許多應用程式最多會有兩個音效同時播放。 在此情況下，spatialization 的成本可以是可忽略的。 您可以使用 [MRTK 畫面播放速率] 監視器來判斷新增 spatialization 的影響。 

### <a name="when-and-how-should-i-apply-distance-based-attenuation"></a>何時和如何套用以距離為基礎的衰減？
在真實世界中，距離較遠的音效會更安靜。 您的音訊引擎可以根據來源距離來建立此衰減的模型。 在傳達相關資訊時，使用以距離為基礎的衰減。

**視覺**指標、**動畫全息影像**和其他資訊音效的距離通常與使用者相關。 使用以距離為基礎的衰減，以直覺的方式提供此提示。
* 調整每個來源的衰減曲線，以符合混合世界空間的大小。 您的音訊引擎的預設曲線通常適用于非常大的空間（最多半公里）。

強調按鈕和其他互動**之漸進階段**的音效不應套用衰減。 這些音效的加強效果通常比與按鈕通訊的距離更重要。 變化可能會很雜亂，特別是鍵盤，其中會連續聽到許多按鈕的點擊。

### <a name="which-spatialization-technology-should-i-use"></a>應該使用哪一種 spatialization 技術？
使用耳機或 HoloLens 喇叭時，請使用 HRTF （標頭相關的傳輸功能）型 spatialization 技術。 它們會將音效散佈在實體世界的前端。 即使音效來源的一端很遠，音效還是會散佈到較遠的耳，並有一些衰減和延遲。 相反地，說話者平移只依賴衰減，而當音效在右側時，會在左邊的耳中套用總衰減（反之亦然）。 這可能會對一般聽力接聽程式感到不舒服，而且在單一 ear 中有聽力障礙的接聽程式無法存取。

## <a name="next-steps"></a>後續步驟
* [在 Unity 中使用空間音效](spatial-sound-in-unity.md)
* [Roboraid 案例研究](case-study-using-spatial-sound-in-roboraid.md)
* [HoloTour 案例研究](case-study-spatial-sound-design-for-holotour.md)

