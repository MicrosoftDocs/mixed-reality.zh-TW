---
title: 案例研究-RoboRaid 中使用空間的音效
description: 空間的聲音是其中一項最令人興奮的功能的 Microsoft HoloLens，提供一種方式，讓使用者察覺發生什麼情況其周圍當物件不符合的視野。
author: mattzmsft
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，HoloLens，RoboRaid，空間的音效
ms.openlocfilehash: 4bb050b4a4051c121c488ea38e150a8973bd7c04
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592124"
---
# <a name="case-study---using-spatial-sound-in-roboraid"></a>案例研究-RoboRaid 中使用空間的音效

Charles Sinex，音訊的潛在客戶，Microsoft HoloLens Experience 小組，談論他發現時建立音訊的獨特的挑戰[RoboRaid](https://www.microsoft.com/en-us/p/roboraid/9nblggh5fv3j)，混合的實境第一人稱射擊。

## <a name="the-tech"></a>技術

[空間音效](spatial-sound.md)是其中一項最令人興奮的功能的 Microsoft HoloLens，提供一種方式，讓使用者察覺發生什麼情況其周圍當物件不符合的視野。

在 RoboRaid，最明顯且有效的使用空間是聲音的警示事情外部使用者的周邊視覺將播放程式。 比方說，Breacher 可以輸入從任何空間，請在掃描牆，但如果您不會遇到進入其中的位置，您可能會遺失。 若要提醒您此入侵，您將聽取不同的位元的音訊輸出來自其中 Breacher 輸入時，可讓您知道您要迅速採取行動，以將它停止。

## <a name="behind-the-scenes"></a>幕後

建立空間音效 HoloLens 的應用程式的程序讓新的且唯一，而且缺乏過去的專案，以做為參考可能會導致大量的標頭時遇到問題，正準備碰上。 希望這些範例的音訊的挑戰我們面臨著讓 RoboRaid 將可協助您建立您自己的應用程式的 音訊。

### <a name="be-mindful-of-taxing-the-cpu"></a>請注意的消耗 CPU

空間的聲音可能很嚴苛，而在 CPU 上。 對於忙碌的體驗，像是 RoboRaid 則是保留的空間音效在任何給定時間的八個執行個體的重要項目。 大部分的情況下，很簡單，只要設定不同的音訊事件的執行個體的限制，如此會終止之後達到限制時所發生的任何執行個體。 比方說，當無人機繁衍 （spawn），其 screams 僅限於三個執行個體在任何指定時間。 只有約四個無人機可以繁衍 （spawn） 一次，考量三個 screams 很因為沒有任何方法，您的大腦可追蹤的許多發音相似的音訊事件。 這釋出了資源的其他空間之音效的事件，例如敵人爆炸或準備要傳送的敵人。

### <a name="rewarding-a-successful-dodge"></a>奬勵成功閃避

Dodging 技師修理是遊戲的其中一個最重要的層面中 RoboRaid，和我們認為 HoloLens 體驗真正特有的項目。 因此，我們希望成功加亮獲益匪淺給播放器。 我們 Doppler"whizz-著 「 聽起來很早在開發吸引人。 我的計劃一開始是使用迴圈和操作即時使用磁碟區、 音調、 和篩選。 此實作將會非常複雜，因此認可可以真正開始建置此資源之前，我們建立便宜原型使用的資產 Doppler 效果現成只是為了了解它實情 *。 使此 whizz 的資產會播放完全 0.7 秒彈藥將已過玩家的 ear 和認為真的令人驚奇的結果之前，我們有天份的開發人員成功了 ！ 不用說，我們會拋棄了底線的更複雜的解決方案，並實作原型。

* * (如果您想要建立具有內建的 Doppler 效果的音訊資產的詳細資訊，請參閱 Charles Deenan 呼叫音效的設計工具的文章[在 2 分鐘內的 100 Whooshes](http://designingsound.org/2010/02/charles-deenen-special-100-whooshes-in-2-minutes/)。) *
<br>
![已成功躲過敵人的彈藥獎勵滿足 whizz 的音效播放程式。](images/successful-dodge-roboraid-500px.jpg)

### <a name="ditching-ineffective-sounds"></a>無效的音效的拋棄

一開始，我們有想要播放遽增背後播放音效，一旦他們已成功 dodged 敵人的彈藥，但是我們決定拋棄這有幾個原因。 首先，不認為不如我們用於閃避 whizz 由 SFX。 彈藥叫用您背後的牆上的時間，其他項目會發生在遊戲中會很多音效的遮罩。 其次，我們沒有衝突上下限，因此我們無法取得播放彈藥叫用最低限度值，而不是背景牆時遽增。 但最後，有空間音效的 CPU 成本。 Elite Scorpion 敵人 （一牆內可以搜耙） 都有特殊的攻擊，這大約八個投擲。 不只您在混合中，讓大型的混亂，它也導入了個三長兩爆因為它已達到 CPU 太難。

### <a name="communicating-a-hit"></a>叫用的通訊

有趣的問題，在我們認為是唯一的 HoloLens 體驗，這是有效到播放程式通訊，它們具有已達到的困難度。 混合的實境體驗成功是劇本會發生您感覺。 這表示您所認為自己客廳中對抗外星人機器人的入侵。

播放程式顯然不會覺得任何項目時就會叫用，因此我們必須找到真正說服播放程式的方法有不良有 happed 給他們。 在傳統的遊戲中，您可能會看到可能有點 grunt 的動畫，可讓您知道您的字元已叫用，或畫面可能會閃爍紅色和您的字元。 由於這種提示沒有作用中的混合的實境體驗，因此我們決定結合真的誇張的音效，指出您的視覺提示已損毀。 建立巨量的音效，並使得它 ducked 所有項目向下混合中那麼顯著。 然後，若要讓它更引人注目，我們新增簡短的警告音效彷彿已接收的核能 sub。 
<br>
![當播放程式取得 RoboRaid 中叫用的時它們會視覺提示，請參閱 <，但也會取得誇張音訊提示，告知他們已損毀。](images/player-hit-roboraid-500px.jpg)

### <a name="getting-big-sound-from-small-speakers"></a>從小型的主講人取得巨量的音效

HoloLens 主講人是裝置的小型且需求，因此您不能預期聽到太多低階淺。 類似於針對智慧型手機或手持式遊戲裝置、 音訊設計師與作曲者一定要留意其音訊的頻率內容開發。 我一律設計音效，或寫入完整的頻率範圍的音樂，因為頭戴耳機是使用者的選項。 不過，為了確保與 HoloLens 演講者之間的相容性，我執行測試偶爾將 EQ 放在我工作就會發生任何 DAW master 中。 EQ 設定組成高通篩選條件 （不會有太的陡峭） 約 600 到 700 Hz 和低通篩選在大約 10 K （非常陡峭）。 這將使您的約略想法您聽起來如何將裝置上的播放。

如果您依賴在低音提供變更音樂中的同步選取的意義，您可能會發現在套用此 EQ 設定時，您的音樂完全失去根的意義。 若要解決此問題，我是一個 octave 更高版本 （具有某些豐富諧波） 低音中加入另一個圖層中，混合，以取得根後的意義。 有時候，使用向上諧波 amp 的扭曲，會提供足夠的頻率內容中較高的範圍，讓我們認為有一點底下的大腦。 這適用於 SFX 影響、 爆炸，或音效的特殊分鐘的時間，例如主管的進階攻擊。 您真的不能依賴低階讓播放程式的影響或加權。 如同音樂扭曲提供少量無暇絕對協助。

### <a name="making-your-audio-cues-stand-out"></a>讓您脫穎而出的音訊提示

當然，所有團隊成員想 bombastic 音樂、 雲端主張，以及 瘋狂爆炸;但是他們也想要能夠聽到 voiceover 或任何其他關鍵遊戲音效提示。

主控台遊戲的頻率的完整範圍，您會有更多的選項，將頻率，視聲音的重要性而定。 RoboRaid，不過，我已有限制範圍的頻率，我無法從音效出曲線的數目。 比方說，如果您使用低通濾波器和從高階的範圍太多出的曲線，就沒有剩餘的聲音，因為沒有更低階的任何項目。

為了讓 RoboRaid 音效最大的大小會在裝置上，我們必須降低的完整體驗的動態範圍，而且廣泛使用的 「 迴避 」 藉由建立清楚的階層架構的不同類型的音效的重要性。 我將 「 迴避 」 從-2-6 db 根據重要性而定。 我個人不喜歡明顯避遊戲，因此我花了很多時間微調淡出輸入/輸出執行時間和磁碟區衰減數量。 我們設定空間音效、 非空間音效、 VO，和不音樂、 殘響器 dry 匯流排的不同匯流排上，然後建立非常高的優先順序，嚴重且非關鍵匯流排。 資產接著已移至其適當的匯流排上設定。

我希望有音訊專業人員必須盡可能狂歡依照我從事 RoboRaid 處理自己的應用程式。 我無法等候了 （並聽聽 ！） 什麼 Microsoft 外部洋溢的人會擬定的 HoloLens。

## <a name="do-it-yourself"></a>自行進行此作業

我發現特定事件 （例如爆炸） 聽起來 「 更大 」 的一個技巧 — 像是他們要填滿的空間，是要建立此空間的聲音 mono 資產，並混合與 2D 的立體聲資產，以 3D 中播放。 它確實承擔一些調整，因為是立體聲的內容中有太多的資訊將會降低 mono 的資產的方向。 不過，讓正確的平衡會導致龐大的音效，可讓玩家開啟它們的頭正確的方向。

您可以嘗試自行使用下列的音訊資產：

**案例 1**
1. 下載[roboraid_enemy_explo_mono.wav](images/roboraid-enemy-explo-mono.wav)和設定為透過空間音效的播放，並將它指派到的事件。
2. 下載[roboraid_enemy_explo_stereo.wav](images/roboraid-enemy-explo-stereo.wav)並設定為在 2D 劇院中播放，並將指派給與上述相同的事件。 因為這些資產會正規化為 Unity，契比雪夫這兩項資產的磁碟的區，讓它不裁剪。
3. 同時扮演這兩種音效。 移動您腦子大約覺得它聽如何空間。

**案例 2**
1. 下載[roboraid_enemy_explo_summed.wav](images/roboraid-enemy-explo-summed.wav)透過空間音效的播放設定並指派到的事件。
2. 播放此資產本身，然後比較案例 1 中的事件。
3. 請嘗試不同的資產負債的 mono 和立體聲的檔案。

## <a name="about-the-author"></a>關於作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Charles Sinex" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Charles Sinex</b><br>音訊的工程師 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>另請參閱
* [空間的音效](spatial-sound.md)
* [Microsoft HoloLens 的 RoboRaid](https://www.microsoft.com/en-us/p/roboraid/9nblggh5fv3j)
