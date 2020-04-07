---
title: 在混合現實應用程式中使用空間音效
description: 空間音效是功能強大的工具，可在混合現實應用程式中進行深度、協助工具和 UX 設計。
author: kegodin
ms.author: kegodin
ms.date: 11/02/2019
ms.topic: article
keywords: Windows Mixed Reality，空間音效，設計，樣式
ms.openlocfilehash: 08844f6d837407d52ad2ab84b78440ce856151fc
ms.sourcegitcommit: b1ca4194eff452804ce5852208cce9815c6a4500
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80677987"
---
# <a name="how-to-use-sound-in-mixed-reality-applications"></a>如何在混合現實應用程式中使用音效

您可以使用音效來通知和強化使用者對於應用程式狀態的心理模型。 適當時，請使用 spatialization，將音效放在混合現實世界中。 當您以這種方式連接聽覺和視覺效果時，您可以加深互動的直覺性質並增加使用者信心。
<br><br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="when-to-add-sounds"></a>新增聲音的時機
相較于2D 應用程式，混合現實應用程式通常會有更大的音效需求，因為它們缺乏觸覺介面。 當他們通知使用者或加強互動時，新增聲音。

### <a name="inform-and-reinforce"></a>通知和強化
* 對於不是由使用者起始的事件（例如通知），請使用音效來通知使用者發生變更。
* 互動可能會有數個階段。 使用音效來強化階段轉換。

請參閱下列互動、事件和建議音效特性的範例。

### <a name="exercise-restraint"></a>練習擋板
使用者對於音訊資訊沒有無限的容量。
* 每個音效都應該傳達特定且有價值的資訊。
* 當您的應用程式播放音效來通知使用者時，請暫時減少其他聲音的音量。
* 若為按鈕暫留音效（請參閱下列資訊），請新增時間延遲，以避免過多的聲音觸發。

### <a name="dont-rely-solely-on-sounds"></a>不要單獨依賴聲音
使用良好的音效對您的使用者很有價值。 但是，即使已關閉音效，也請確定您的應用程式可供使用。
* 使用者可能有聽力障礙。
* 您的應用程式可能會在較高的環境中使用。
* 使用者可能會有隱私權考慮或其他停用裝置音訊的原因。

## <a name="how-to-sonify-interactions"></a>如何 sonify 互動
混合現實中的互動類型包括手勢、直接操作和語音。 請使用下列建議的特性來選取或設計這些互動的聲音。

### <a name="gesture-interactions"></a>手勢互動
在混合的現實中，使用者可以使用滑鼠來與按鈕互動。 按鈕動作通常會在使用者放開時進行，而不是按下按鈕，讓使用者有機會取消互動。 使用音效來強化這些階段。 若要協助使用者以遠處按鈕為目標，也請考慮使用指標游標暫留音效。
* 按鈕-按下 [音效] 應該是簡短的觸覺，請按 [按一下]。<br/>範例： [MRTK_ButtonPress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* 按鈕-"unpress" 聽起來應該有類似的觸覺風格。 比按音效更高的音調會強調完成的意義。<br/>範例： [MRTK_ButtonUnpress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)
* 針對滑鼠停留音效，請考慮使用微妙且不會有危險的音效，例如低頻率 thud 或凹凸效果。

### <a name="direct-manipulation"></a>直接操作
在 HoloLens 2 上，明確表述的「手寫」追蹤支援使用者介面元素的直接操作。 當沒有其他實體意見反應時，聽起來很重要。

*按鈕按*音效在直接操作中很重要，因為使用者在到達按鍵筆觸的底部時，不會收到任何其他指示。 重要旅遊的音效指標可以是小型、微妙和 pixels occluded。 如同筆勢互動，按下按鈕應該會得到簡短的觸覺音效，像是按一下。 Unpresses 應該有類似的按一下音效，但有凸起的音調。
* 範例： [MRTK_ButtonPress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* 範例： [MRTK_ButtonUnpress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)

很難以以視覺方式確認抓取或發行動作。 使用者的手中通常會有任何視覺效果，而主體的物件則缺乏真實世界的「抓取」的視覺方式。 音效可以有效地溝通成功的抓取和發行互動。
* 抓取動作應該有一個簡短、有點 muffled 的觸覺音效，以 evokes 在物件周圍關閉的想法。 有時候也會有「竊竊私語」音效，會導致抓取音效傳達手的運動。<br/>範例： [MRTK_Move_Start .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_Move_Start.wav)
* 發行動作應該會得到類似的簡短和觸覺音效。 它通常會比捕捉音效更低，而且會以相反的順序出現，並會產生影響，然後再進行「竊竊私語」來溝通物件正在進行的情況。<br/>範例： [MRTK_Move_End .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_Move_End.wav)

*繪圖*互動應會取得持續的迴圈音效，其音量是由使用者的手移動所決定。 當使用者繼續進行時，應該以無訊息的方式進行，並在手上快速移動時 loudest。

### <a name="voice-interactions"></a>語音互動
語音互動通常會有細微的視覺元素。 使用音效來強化互動階段。 您可能會想要使用更多色調的音效來區別它們與手勢和直接操作的聲音。

* 使用語音命令*確認*的正發音語氣。 增加的色調與主要的音樂間隔是有效的。
* 針對語音命令*失敗*，請使用較短、較不正面的語氣。 避免出現負面的聲音。 相反地，請使用更 percussive 的中性音效來溝通應用程式從互動中移動的情況。
* 如果您的應用程式有喚醒字，則在裝置*開始接聽*時，請使用短暫且簡單的語調。 在*應用程式接聽時使用*細微迴圈音效。

### <a name="notifications"></a>通知
通知會傳達應用程式狀態變更和其他不是由使用者起始的事件，例如進程完成、訊息和通話。

在混合現實中，物件有時會移出使用者的視野欄位。 伴隨著移動具有 hrtf 音效的*動畫物件*，這取決於物件類型和動作速度。
* 它有助於在動畫尾端播放 hrtf 音效，以通知使用者物件的新位置。
* 若為漸進式移動，移動期間的「竊竊私語」音效可協助使用者追蹤物件。

*訊息通知*聲音可能會重複聽到，有時會快速地連續播放。 重要的是，它們不會脫離或不粗糙。 中等範圍的正面色調有效。

* 來電音效在行動電話鈴聲上應有類似的品質。 這些通常會迴圈播放，直到使用者接聽電話為止。
* 語音通訊連線和中斷連線應該會有簡短的色調音效。 連接音效應為正色調，表示連接成功。 中斷連線音效應為中性音效，表示呼叫完成。

## <a name="handle-spatialization"></a>處理 spatialization
Spatialization 使用身歷聲耳機或喇叭，將音效放在混合現實世界中。

### <a name="which-sounds-to-spatialize"></a>要 spatialize 的聲音
當音效與具有空間位置的事件產生關聯時，應該 hrtf。 這包括 UI、所包含的 AI 語音和視覺指示器。

Spatialize*使用者介面*元素，藉由限制聽到的身歷聲音效數目，協助清理使用者的 sonic 「空間」。 當 hrtf 音訊意見反應時，操作互動（例如觸及、抓取和放開）更為自然。 針對這些元素，請考慮下列關於距離衰減的資訊。

Spatialize*視覺*指標和具現性的*AI 語音*，以直覺方式通知使用者，這些專案都在視野範圍外。
    
相反地，請避免 spatialization *FACELESS AI 語音*和其他缺少妥善定義空間位置的元素。 沒有相關視覺元素的 Spatialization 可能會讓使用者覺得找不到視覺元素。

Spatialization 有一些 CPU 成本。 許多應用程式都有兩種同時播放的聲音。 在此情況下，spatialization 的成本可能會是可忽略的。 您可以使用 [MRTK 畫面播放速率] 監視器來判斷新增 spatialization 的影響。

### <a name="when-and-how-to-apply-distance-based-attenuation"></a>何時及如何套用以距離為基礎的衰減
在真實世界中，距離較遠的音效會更安靜。 您的音訊引擎可以根據來源距離來建立此衰減的模型。 在傳達相關資訊時，使用以距離為基礎的衰減。

*視覺*指標、*動畫全息影像*和其他資訊音效的距離通常與使用者相關。 使用以距離為基礎的衰減，以直覺的方式提供提示。

調整每個來源的衰減曲線，以符合您的混合現實世界空間大小。 您的音訊引擎的預設曲線通常適用于非常大的空間（最多半公里）。

加強按鈕動作和其他互動*之漸進階段*的音效，應該不會套用衰減。 這些音效的加強效果通常比與按鈕通訊的距離更重要。 當許多按鈕按下可能會連續聽到時，變化可能會有混亂，特別是鍵盤。

### <a name="which-spatialization-technology-to-use"></a>要使用的 spatialization 技術
透過耳機或 HoloLens 喇叭，使用標頭相關的傳送功能（HRTF）型 spatialization 技術。 這些技術會將音效散佈在實體世界的前端。 即使音效來源位於某一端的一端，音效還是會散佈到較遠的耳，並會有一些衰減和延遲。 相反地，說話者平移只會依賴衰減，並在左側的耳中套用總衰減（反之亦然）。 這項技術對於「正常的聽覺」接聽程式，以及在單一 ear 中有聽力障礙的接聽程式無法存取時，可能會感到不舒服。

## <a name="next-steps"></a>後續步驟
* [在 Unity 中使用空間音效](spatial-sound-in-unity.md)
* [Roboraid 案例研究](case-study-using-spatial-sound-in-roboraid.md)
* [HoloTour 案例研究](case-study-spatial-sound-design-for-holotour.md)
