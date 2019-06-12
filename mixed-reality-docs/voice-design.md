---
title: 語音命令
description: 注視、手勢和語音 (GGV) 是 HoloLens 上的主要互動方法。 本文會針對語音設計提供縝密的指導方針。
author: shentan
ms.author: shentan
ms.date: 04/21/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, 設計, 互動, 語音
ms.openlocfilehash: f2362400cba2946c3e97a7128c410ddcd17b4362
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66402373"
---
# <a name="voice-commanding"></a>語音命令

使用語音命令時，一般會使用注視來作為鎖定機制，無論是要作為指標 (「選取」) 還是用來對應用程式指示命令 (「看到什麼就說什麼」)。 當然，有些語音命令完全不需要目標，例如「移至開始」或「嗨，Cortana」。


## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>功能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (第 1 代)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td>語音命令</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️ (連結頭戴式裝置)</td>
</tr>
</table>



## <a name="how-to-use-voice"></a>如何使用語音

請考慮對您所建置的任何體驗新增語音命令。 語音是功能強大的方式，可方便您控制系統和應用程式。 因為使用者說話時的語調和口音各異，適當選擇語音關鍵字才能確保系統會分毫不差地解讀出使用者的命令。

### <a name="best-practices"></a>最佳作法

以下是有助於順利辨識語音的一些做法。
* **使用精簡的命令** - 盡可能選擇有兩個以上音節的關鍵字。 口音不同的人在說單音節的單字時往往會使用不同的元音。 範例："Play video" 優於 "Play the currently selected video"
* **使用簡單的字彙** - 範例："Show note" 優於 "Show placard"
* **確定命令不具破壞性** - 確定可透過語音命令來採取的動作不具破壞性，如果使用者附近有其他人不小心觸發命令，也可以輕鬆地加以復原。
* **避免類似發音的命令** - 避免註冊多個聽起來非常類似的語音命令。 範例："Show more" 和 "Show store" 的發音會非常類似。
* **將未使用的應用程式取消註冊** - 當應用程式並非處在會讓特定語音命令生效的狀態時，請考慮將其取消註冊，以免該命令與其他命令混淆。
* **使用不同口音進行測試** - 請使用不同口音的使用者測試應用程式。
* **讓語音命令保持一致** - 如果 "Go back" 會回到上一頁，請在應用程式中保持這個行為。
* **避免使用系統命令** - 下列語音命令已保留給系統使用。 應用程式請勿使用這些命令。
   * "Hey Cortana"
   * "Select"

### <a name="select"></a>"Select"

在任何時候說出 "Select"，都會啟用注視游標所指的目標。 

>注意：在 HoloLens 2 中，必須先說出 "Select" 一詞來叫用注視游標。 再次說出 "Select" 便能啟用。 若要隱藏注視游標，使用雙手就可以 - 空中點選或觸碰物件。 

### <a name="see-it-say-it"></a>看到什麼就說什麼

Windows Mixed Reality 採用「看到什麼就說什麼」語音模型，**按鈕上的標籤會與相關聯的語音命令完全相同**。 因為標籤和語音命令沒有任何不一致，使用者會更加了解要說什麼才能控制系統。 為了強化這一項功能，當您停駐在某個按鈕上時，便會出現 **「語音停駐提示」** ，來讓您知道哪些按鈕有語音功能。


![看到什麼就說什麼的範例 1](images/voice-seeitsayit1-640px.jpg)

![看到什麼就說什麼的範例 2](images/voice-seeitsayit2-640px.jpg)<br>
「看到什麼就說什麼」的範例 

### <a name="voices-strengths"></a>語音的優點

語音輸入是很自然的意圖溝通方式。 語音特別適合用於介面的**周遊**，因為這種方式可以幫助使用者跳過介面的多個步驟 (使用者可以在看網頁時說 "go back"，而不必上移再點擊應用程式中的 [上一頁] 按鈕)。 這種方式雖然只節省了一點時間，卻會對使用者感覺到的體驗產生**情感效應**，讓使用者獲得一點超能力。 當我們無法騰出雙手或是在執行**多工**處理時，使用語音也是很方便的輸入方法。 在不方便使用鍵盤來輸入的裝置上，**語音聽寫**會是很有效率的替代輸入方式。 最後，在某些注視和手勢的**精確範圍**不高的情況下，使用者可能只會信任語音輸入方法。

**使用語音如何讓使用者受益**
* 減少時間 - 語音應該會讓最終目標更有效率。
* 最不費力 - 語音應該會讓工作變得更為流暢且更不費力。
* 降低認知負荷 - 語音既直覺、易於了解且容易記住。
* 符合社交規範 - 語音應該會符合社會行為規範。
* 語音很平常 - 語音隨時可以變成慣常行為。

### <a name="voices-weaknesses"></a>語音的缺點

語音也有一些缺點。 缺點之一就是細微控制。 (例如，使用者可能會說：「大聲點」，但不會說出大多少。 「一點」是不容易量化的詞。 使用語音來移動或縮放物體也很困難 (語音不會提供控制項的細微性)。 語音也有缺陷。 有時候，語音系統會誤判命令，或無法聽到命令。 不管什麼介面都很難從這類錯誤改正回來。 最後，在公開場合中，使用者可能不方便發出聲音， 或者有一些不能或不應該說的話。 遇到這樣的困境時，語音就能發揮所長，無往不利。

### <a name="voice-feedback-states"></a>語音反饋狀態

當語音正確套用時，使用者會了解**他們能說什麼並獲得清楚的反饋**而知道系統**正確聽懂他們的語音**。 這兩個訊號會讓使用者有信心，確信他們可以使用語音作為主要輸入方式。 下圖顯示的是當系統辨識到語音輸入時會有什麼情形，以及系統會如何讓使用者知道這一點。

![游標的語音反饋狀態](images/voicefeedbackstates.png)<br>
*游標的語音反饋狀態*

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a>針對混合實境中的「語音」，使用者最應該了解的事
* 在鎖定按鈕時說出 **"Select"** (您可以在任何地方使用這個命令來按一下按鈕)。
* 在某些應用程式中，您可以說出**應用程式列按鈕的標籤名稱**來採取動作。 例如，在查看應用程式的同時，使用者可以說出「Remove」命令來從該世界中移除應用程式 (這可省下必須用手按一下按鈕的時間)。
* 您可以說 **「嗨 Cortana」** 讓 Cortana 開始聽取命令。 您可以向她問問題 (「嗨 Cortana，艾菲爾鐵塔有多高」)、請她開啟應用程式 (「嗨 Cortana，開啟 Netflix」)，或請她顯示 [開始] 功能表 (「嗨 Cortana，回到首頁」) 等等。

## <a name="common-questions-and-concerns-users-have-about-voice"></a>使用者會有的語音相關常見問題和疑慮
* 我可以說什麼？
* 如何知道系統沒有聽錯？
   * 系統一直聽錯我的語音命令。
   * 我提供了語音命令，系統卻沒有反應。
* 我提供了語音命令，系統卻做出錯誤反應。
* 如何讓我的語音以特定應用程式或應用程式命令作為目標？
* 在 HoloLens 上的全像攝影畫面外，是否可以使用語音來命令物件？

## <a name="see-also"></a>請參閱
* [筆勢](gestures.md)
* [頭部目光和停駐](gaze-and-dwell.md)
