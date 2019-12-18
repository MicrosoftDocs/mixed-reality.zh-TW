---
title: 案例研究-在 RoboRaid 中使用空間音效
description: 空間音效是 Microsoft HoloLens 其中一項最令人興奮的功能，可讓使用者在物件不在視線的同時，觀察其周圍的狀況。
author: mattzmsft
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、RoboRaid、空間音效
ms.openlocfilehash: 1482c914d261cae698a1460873b217b0683cd16b
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181938"
---
# <a name="case-study---using-spatial-sound-in-roboraid"></a>案例研究-在 RoboRaid 中使用空間音效

本文說明 Microsoft HoloLens 經驗小組在建立[RoboRaid](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)的音訊時所遇到的獨特挑戰，這是一位混合現實的射擊。

## <a name="the-tech"></a>技術

[空間音效](spatial-sound.md)是 Microsoft HoloLens 其中一項最令人興奮的功能，可讓使用者在物件不在視線的同時，觀察其周圍的狀況。

在 RoboRaid 中，最明顯且有效的空間音效用法，就是在使用者的周邊願景以外，提醒播放程式發生問題。 例如，Breacher 可以從房間內的任何掃描牆輸入，但如果您不是面對輸入的位置，您可能會錯過它。 若要提醒您此目睹，您會聽到 Breacher 輸入的不同位音訊，這可讓您知道您需要快速地採取行動來停止它。

## <a name="behind-the-scenes"></a>幕後

為 HoloLens 應用程式建立空間音效的過程是全新且唯一的，而且缺少過去用來參考的專案，可能會在您遇到問題時導致許多 head 抓著。 希望我們在進行 RoboRaid 時所面臨的音訊挑戰範例，會在您為自己的應用程式建立音訊時提供協助。

### <a name="be-mindful-of-taxing-the-cpu"></a>請留意 CPU 的負擔

空間音效可能會要求 CPU。 對於 RoboRaid 之類的忙碌體驗而言，將空間音效的實例保持在任何指定時間的八位之下是很重要的。 在大部分的情況下，您可以輕鬆地設定不同音訊事件的實例限制，以便在達到限制之後發生的任何實例終止。 例如，當無人機產生時，其 screams 會在任何指定時間限制為三個實例。 一次只考慮四個無人機，有三個 screams 是很好的，因為您的大腦無法追蹤許多類似發音的音訊事件。 這會釋出其他空間音效事件的資源，例如敵人爆炸或敵人準備要進行。

### <a name="rewarding-a-successful-dodge"></a>獎勵成功減淡

躲過技師修理是 RoboRaid 中游戲的其中一個最重要的層面，也是我們覺得真正獨特的 HoloLens 經驗。 因此，我們想要讓 dodges 對玩家的成功率非常有益。 在開發過程中，我們 Doppler 「whizz」聽起來非常吸引人。 一開始，我的計畫是使用迴圈，並使用磁片區、音調和篩選來即時操作。 這項作業的實現非常詳盡，因此在認可資源以實際建立之前，我們使用具有 Doppler 效果內建的資產建立了成本較低的原型，只是為了瞭解它覺得 *。 我們的開發人員使其成為 it，讓這項 whizz 的資產在 projectile 將由玩家的耳傳遞之前，只會在0.7 秒內播放一筆，而結果則令人驚訝！ 不用說，我們 ditched 了更複雜的解決方案，並實作為原型。

*（如需使用內建的 Doppler 效果建立音訊資產的詳細資訊，請參閱[2 分鐘內的 100 Whooshes](http://designingsound.org/2010/02/26/charles-deenen-special-100-whooshes-in-2-minutes/)）。*  
<br>
![成功躲過敵人的 projectile 以滿足 whizz 的音效來獎勵玩家。](images/successful-dodge-roboraid-500px.jpg)

### <a name="ditching-ineffective-sounds"></a>拋棄失效的音效

一開始，我們想要在玩家成功 dodged 敵人 projectile 後播放播放程式，但我們決定基於幾個原因而揚棄。 首先，它不會像我們用於減淡的 whizz 的 SFX 一樣有效。 在 projectile 觸及您背後的牆之後，遊戲中也會發生其他問題，而這聽起來會很容易遮蔽。 其次，我們不會發生衝突，因此無法在 projectile 達到地面而非牆時，讓我們無法播放。 最後，空間音效還有 CPU 成本。 Scorpion 的敵人（可以在牆內進行編目的）有一項特殊的攻擊，寄大約八炮彈。 這不僅會使混合變得很大，也引進了混亂的聲，因為它的 CPU 太困難。

### <a name="communicating-a-hit"></a>溝通點擊

我們遇到了一項有趣的問題，我們覺得這對 HoloLens 體驗而言是唯一的，這是很難有效地與他們所叫用的玩家溝通。 如何讓混合現實的體驗成功，正是您覺得這是您的故事。 這表示您必須在自己的生活中，相信您正在對抗一間的機器人目睹。

播放程式明顯不會感覺到任何事，因此我們必須找出一種方法，讓玩家相信 happed。 在傳統遊戲中，您可能會看到可讓您知道您的字元已被叫用的動畫，或螢幕可能會以紅色閃爍，而您的字元可能會 grunt 很少。 因為這些類型的提示在混合現實的體驗中無法使用，所以我們決定將視覺提示與真正放大的音效結合，以指出您已損毀。 我建立了一個很大的音效，讓它在混合中 ducked 所有專案。 然後，為了讓它更進一步，我們新增了一段簡短的警告音效，就像是在取得某個的「核用」。 
<br>
![在 RoboRaid 中叫用玩家時，他們會看到視覺提示，但也會取得放大的音訊提示，告訴他們已損毀。](images/player-hit-roboraid-500px.jpg)

### <a name="getting-big-sound-from-small-speakers"></a>從小型說話者取得大音效

HoloLens 喇叭的小型和光線會符合裝置的需求，因此您不會聽到太多的低端。 與智慧型手機或手持遊戲裝置的開發類似，音效設計人員和作曲家必須留意其音訊的頻率內容。 我一直都是以完整的頻率範圍來設計聲音或書寫音樂，因為戴耳機是使用者的選擇。 不過，為了確保與 HoloLens 喇叭的相容性，我偶爾會藉由將 EQ 放在我所處理的任何白苗文的主伺服器中，來執行測試。 EQ 設定是由高於600到 700 Hz （沒有太多）和低通濾波器（非常高）的高傳遞濾波器所組成。 這應該會讓您瞭解如何在裝置上播放聲音。

如果您依賴低音來對音樂中的弦進行變更，您可能會發現當您套用此 EQ 設定時，音樂完全失去了根目錄的意義。 為了解決這個問題，我將另一層新增至低音，這是一個 octave 較高（使用一些豐富的諧波），並將其混合以取得 root 的意義。 有時候，使用失真來 amp 諧波會在較高範圍提供足夠的頻率內容，讓我們的大腦覺得它底下有一些東西。 這適用于像是一段特殊時間的 SFX，像是影響、爆炸或音效，例如老闆的超級攻擊。 您真的無法依賴低端，讓玩家有意義的影響或權數。 就像使用音樂一樣，使用扭曲來提供一些借助電腦絕對有説明。

### <a name="making-your-audio-cues-stand-out"></a>讓您的音訊提示更醒目

當然，小組中的每個人都想要 bombastic 音樂、主張，以及令人不可思議的爆炸;但他們也希望能夠聽到 voiceover 或任何其他遊戲關鍵的音訊提示。

在具有完整範圍頻率的主控台遊戲上，您有更多選項可以根據音效的重要性來細分頻率。 不過，在 RoboRaid 中，我限制了我可以從音效彎曲的頻率範圍。 比方說，如果您使用低通濾波器，並從範圍較高的曲線向外彎曲，就不會有任何專案留在音效中，因為沒有太多的低端。

為了讓 RoboRaid 聽起來像是裝置上的最大，我們必須降低整個體驗的動態範圍，並藉由為不同類型的音效建立清楚的重要性階層，以充分運用回避。 我根據重要性設定-2 到-6 資料庫的回避。 我個人不喜歡遊戲中的明顯回避，因此我花了很多時間微調淡入/縮小時間和磁片區衰減量。 我們為空間音效、非空間音效、VO 和試匯流排設定不同的匯流排，而不會對音樂進行回音，然後建立非常高的優先順序、關鍵和非重大匯流排。 然後，我們會設定資產以移至適當的匯流排。

我希望音訊專業人員能夠在自己的應用程式上運作，因為我在 RoboRaid 上工作。 我看不到（聽過！） Microsoft 外部的人才會針對 HoloLens 提出哪些內容。

## <a name="do-it-yourself"></a>親自完成

我發現讓特定事件（例如爆炸）聽起來更大的一項技巧，像是填滿空間，就是為空間音效建立 mono 資產，並使用2D 身歷聲資產來重新播放3D。 它確實會進行一些微調，因為身歷聲內容中的資訊過多會降低 mono 資產的方向。 不過，取得平衡會產生很大的音效，讓玩家能夠以正確的方向來輪流列印頭。

您可以使用下列音訊資產自行嘗試：

**案例 1**
1. 下載[roboraid_enemy_explo_mono .wav](images/roboraid-enemy-explo-mono.wav)並將其設定為透過空間音效播放，並將其指派給事件。
2. 下載[roboraid_enemy_explo_stereo .wav](images/roboraid-enemy-explo-stereo.wav)並設定為在2d 身歷聲中播放，然後指派給與上述相同的事件。 因為這些資產會正規化為 Unity，所以 attenuate 這兩個資產的數量，使其不會進行裁剪。
3. 同時播放這兩個聲音。 四處移動您的頭部，感受它的外觀。

**案例 2**
1. 下載[roboraid_enemy_explo_summed .wav](images/roboraid-enemy-explo-summed.wav) ，並將其設定為透過空間音效播放並指派給事件。
2. 單獨播放此資產，然後與案例1中的事件進行比較。
3. 嘗試不同的 mono 和身歷聲檔案平衡。



## <a name="see-also"></a>請參閱
* [空間音效](spatial-sound.md)
* [適用于 Microsoft HoloLens 的 RoboRaid](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)
