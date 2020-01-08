---
title: 語音命令
description: 注視、手勢和語音 (GGV) 是 HoloLens 上的主要互動方法。 本文會針對語音設計提供縝密的指導方針。
author: shengkait
ms.author: shentan
ms.date: 04/21/2019
ms.topic: article
keywords: Windows Mixed Reality, 設計, 互動, 語音
ms.openlocfilehash: 66afa24699ed22fb17ab36818ba67a526f4c5618
ms.sourcegitcommit: 7e8b9de561cbc8483e84511f3e9cbd779f3a999f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/27/2019
ms.locfileid: "75502639"
---
# <a name="voice-commanding"></a>語音命令

使用語音命令時，注視通常用來作為目的機制，也就是指標（"select"），或是將您的命令導向應用程式（「看它，說它」）。 當然，有些語音命令完全不需要目標，例如「移至開始」或「嗨，Cortana」。


## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>語音命令</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (連結頭戴式裝置)</td>
    </tr>
</table>



## <a name="how-to-use-voice"></a>如何使用語音

請考慮對您所建置的任何體驗新增語音命令。 Voice 是控制系統和應用程式的強大且方便的方式。 因為使用者說話時的語調和口音各異，適當選擇語音關鍵字才能確保系統會分毫不差地解讀出使用者的命令。

### <a name="best-practices"></a>最佳做法

以下是有助於順利辨識語音的一些做法。
* **使用精簡的命令** - 盡可能選擇有兩個以上音節的關鍵字。 口音不同的人在說單音節的單字時往往會使用不同的元音。 範例：「播放影片」比「播放目前選取的影片」好
* **使用簡單詞彙**-範例：「顯示便箋」比「顯示牌子」好
* **確定命令不具破壞性** - 確定可透過語音命令來採取的動作不具破壞性，如果使用者附近有其他人不小心觸發命令，也可以輕鬆地加以復原。
* **避免類似發音的命令** - 避免註冊多個聽起來非常類似的語音命令。 範例：「顯示更多」和「Show store」可能會有非常相似的發音。
* **將未使用的應用程式取消註冊** - 當應用程式並非處在會讓特定語音命令生效的狀態時，請考慮將其取消註冊，以免該命令與其他命令混淆。
* **使用不同口音進行測試** - 請使用不同口音的使用者測試應用程式。
* **讓語音命令保持一致** - 如果 "Go back" 會回到上一頁，請在應用程式中保持這個行為。
* **避免使用系統命令** - 下列語音命令已保留給系統使用。 應用程式請勿使用這些命令。
   * "Hey Cortana"
   * "Select"

### <a name="select"></a>"Select"

在任何時候說出 "Select"，都會啟用注視游標所指的目標。 

>注意：在 HoloLens 2 中，您必須先說出「select」這個字來叫用注視游標。 再次說出 [選取] 以啟用。 若要隱藏注視游標，只需使用您的手來 airtap 或觸控物件。 

### <a name="see-it-say-it"></a>看到什麼就說什麼

Windows Mixed Reality 採用「看到什麼就說什麼」語音模型，**按鈕上的標籤會與相關聯的語音命令完全相同**。 因為標籤和語音命令沒有任何不一致，使用者會更加了解要說什麼才能控制系統。 為了強化這一項功能，當您停駐在某個按鈕上時，便會出現 **「語音停駐提示」** ，來讓您知道哪些按鈕有語音功能。


![看到什麼就說什麼的範例 1](images/voice-seeitsayit1-640px.jpg)

![看到什麼就說什麼的範例 2](images/voice-seeitsayit2-640px.jpg)<br>
「看到什麼就說什麼」的範例

### <a name="voices-strengths"></a>語音的優點

語音輸入是很自然的意圖溝通方式。 語音在介面**周遊**上特別有用，因為它可以協助使用者剪下介面的多個步驟（使用者可能會在查看網頁時說「返回」，而不需要在應用程式中按一下 [上一頁] 按鈕）。 這項小型節省時間對於使用者對體驗的認知具有強大的**情緒效果**，並提供少量的增強。 當我們無法騰出雙手或是在執行**多工**處理時，使用語音也是很方便的輸入方法。 在輸入鍵盤的裝置上很容易，**語音聽寫**可以是一種有效率且替代的輸入方式。 最後，在某些情況下，當注視和手勢的**精確度範圍**有限時，語音可能是使用者唯一受信任的輸入方法。

**使用語音如何讓使用者受益**
* 減少時間 - 語音應該會讓最終目標更有效率。
* 最不費力 - 語音應該會讓工作變得更為流暢且更不費力。
* 降低認知負荷 - 語音既直覺、易於了解且容易記住。
* 符合社交規範 - 語音應該會符合社會行為規範。
* 語音很平常 - 語音隨時可以變成慣常行為。

### <a name="voices-weaknesses"></a>語音的缺點

語音也有一些缺點。 缺點之一就是細微控制。 （例如，使用者可能會說「過多」，但無法說出多少。 「一點」是不容易量化的詞。 使用語音來移動或縮放物體也很困難 (語音不會提供控制項的細微性)。 語音也有缺陷。 有時候，語音系統會誤判命令，或無法聽到命令。 不管什麼介面都很難從這類錯誤改正回來。 最後，在公開場合中，使用者可能不方便發出聲音， 或者有一些不能或不應該說的話。 遇到這樣的困境時，語音就能發揮所長，無往不利。

### <a name="voice-feedback-states"></a>語音反饋狀態

當語音正確套用時，使用者會了解**他們能說什麼並獲得清楚的反饋**而知道系統**正確聽懂他們的語音**。 這兩個訊號會讓使用者有信心，確信他們可以使用語音作為主要輸入方式。 下圖顯示的是當系統辨識到語音輸入時會有什麼情形，以及系統會如何讓使用者知道這一點。

![游標的語音反饋狀態](images/voicefeedbackstates.png)<br>
*游標的語音反饋狀態*

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a>針對混合實境中的「語音」，使用者最應該了解的事
* 在鎖定按鈕時說出 **"Select"** (您可以在任何地方使用這個命令來按一下按鈕)。
* 在某些應用程式中，您可以說出**應用程式列按鈕的標籤名稱**來採取動作。 例如，在查看應用程式的同時，使用者可以說出「Remove」命令來從該世界中移除應用程式 (這可省下必須用手按一下按鈕的時間)。
* 您可以說 **「嗨 Cortana」** 讓 Cortana 開始聽取命令。 您可以詢問自己的問題（「嗨，Cortana，Eiffel 塔的高度如何？」），告訴她開啟應用程式（「嗨，Cortana，open Netflix」），或告訴她如何顯示 [開始] 功能表（"嗨 Cortana，take home"）等等。

## <a name="common-questions-and-concerns-users-have-about-voice"></a>使用者會有的語音相關常見問題和疑慮
* 我可以說什麼？
* 如何知道系統沒有聽錯？
   * 系統一直聽錯我的語音命令。
   * 我提供了語音命令，系統卻沒有反應。
* 我提供了語音命令，系統卻做出錯誤反應。
* 如何讓我的語音以特定應用程式或應用程式命令作為目標？
* 在 HoloLens 上的全像攝影畫面外，是否可以使用語音來命令物件？

## <a name="see-also"></a>請參閱
* [筆勢](gaze-and-commit.md#composite-gestures)
* [頭部目光和停駐](gaze-and-dwell.md)
