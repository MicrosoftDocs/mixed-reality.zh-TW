---
title: 語音輸入
description: 語音輸入是 HoloLens 和 Windows Mixed Reality 沉浸式耳機的核心輸入。 語音可以用於命令、聽寫、Cortana 等等。
author: hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: ggv、語音、cortana、語音、輸入
ms.openlocfilehash: 37364e90aa1d8a7b607a99f4c9b830972f7f80b3
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85441825"
---
# <a name="voice-input"></a>語音輸入

![語音輸入](images/UX/UX_Hero_VoiceCommand.jpg)

語音是 HoloLens 輸入的其中一種主要形式。 它可讓您直接命令全息影像，而不需要使用[右手手勢](gaze-and-commit.md#composite-gestures)。 語音輸入是溝通意圖的一種自然方式。 語音在遍歷複雜介面時特別有用，因為它可讓使用者使用一個命令來剪下嵌套的功能表。

語音輸入是由在所有其他_通用 Windows 應用程式_中支援語音的[相同引擎](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx)提供技術支援。 在 HoloLens 上，語音辨識一律會以 [設定] 中設定的 Windows 顯示語言運作。 

<br>

## <a name="voice-and-gaze"></a>語音和注視

使用語音命令時，（head 或眼睛）注視通常用來做為目的機制，不論使用游標（"select"），或將命令隱含地通道至您要查看的應用程式。 在此情況下，可能甚至不需要顯示任何看過的游標 _（「見它，說它」）_。 當然，有些語音命令根本不需要目標，例如「移至開始」或「嗨，Cortana」。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


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
        <td>語音輸入</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️（使用麥克風）</td>
    </tr>
</table>

## <a name="the-select-command"></a>"Select" 命令

**HoloLens (第 1 代)**

即使不特別將語音支援新增至您的應用程式，您的使用者只要說出系統語音命令「選取」，就可以啟動全息影像。 其行為與 HoloLens 上的[空中](gaze-and-commit.md#composite-gestures)按鍵、按下[hololens clicker](https://docs.microsoft.com/hololens/hololens1-clicker)上的 [選取] 按鈕，或在[Windows Mixed Reality 動作控制器](motion-controllers.md)上按下觸發程式一樣。 您會聽到音效，並看到包含 [選取] 的工具提示會顯示為 [確認]。 「選取」是由低乘冪關鍵字偵測演算法所啟用，因此隨時都可讓您以最少的電池壽命影響來表示，即使您的手中也一樣。

<br>

---

:::row:::
    :::column:::
        **HoloLens 2**<br><br>
        若要使用 HoloLens 2 中的「選取」語音命令，您必須先啟動注視游標以作為指標。 用來啟動它的命令很容易記住，只要說「select」就可以了。<br><br>
        若要結束模式，只要使用滑鼠按鍵、接近手指的按鈕，或使用系統手勢，就可以再次使用您的手。<br>
        <br>
        *影像：說「選取」以使用語音命令進行選取*
    :::column-end:::
        :::column:::
       ![使用者可以說「選取」，使用語音命令進行選取。](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="hey-cortana"></a>嗨 Cortana

您也可以說「嘿 Cortana」，隨時帶出 Cortana。 您不需要等待她繼續詢問您的問題或提供指示，例如，試著說「嘿，我的天氣是什麼？」 當做單一句子。 如需 Cortana 和您可以執行之動作的詳細資訊，請直接詢問她！ 說「嘿，我可以說什麼？」 她會提取一個工作和建議的命令清單。 如果您已經在 Cortana 應用程式中，也可以按一下 [ **？** ] 在提要欄位上拉出此相同功能表的圖示。

**HoloLens 特有的命令**
* 「我可以說什麼？」
* [移至開始]-而不是 [ [bloom](system-gesture.md#bloom) ] 以進入 [[開始] 功能表](navigating-the-windows-mixed-reality-home.md#start-menu)
* 「啟動 <app> 」
* 「移至 <app> 這裡」
* 「拍照」
* 「開始錄製」
* 「停止錄製」
* 「顯示手光線」
* 「隱藏手光線」
* 「增加亮度」
* 「降低亮度」
* 「增加音量」
* 「減少音量」
* 「靜音」或「取消靜音」
* 「關閉裝置」
* 「重新開機裝置」
* 「進入睡眠狀態」
* 「有什麼時間？」
* 「我剩多少電池？」



<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a>「見它」<br>
        HoloLens 有「看它，假設是語音輸入的模型」，其中標籤的按鈕會告訴使用者他們也可以說的語音命令。 例如，當您在 HoloLens （第1代）中查看應用程式視窗時，使用者可以在應用程式行中說出他們看到的「調整」命令，以調整應用程式在世界中的位置。<br>
        <br>
        *影像：使用者可以在應用程式行中顯示 [調整] 命令，以調整應用程式的位置*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
        ![查看應用程式視窗或全息影像時，使用者可以說出他們在應用程式行中看到的「調整」命令，以調整應用程式在世界中的位置。](images/microphone-600px.png)<br>
    :::column-end:::
:::row-end:::


<br>



:::row:::
    :::column:::
        當應用程式遵循此規則時，使用者可以輕鬆地瞭解如何控制系統。 為了強調此情況，當您在 HoloLens （第1代）中的按鈕上撥雲見日時，如果按鈕已啟用語音，並顯示要對其進行「按下」的命令，您就會看到一個「聲音停留」工具提示。 若要在 HoloLens 2 中顯示語音工具提示，請以「選取」或「我可以說」來顯示語音游標（請參閱影像）。 <br>
        <br>
        *影像：「見它，說它」命令出現在按鈕下方*
    :::column-end:::
        :::column:::
       ![查看它，假設命令出現在按鈕下方](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="voice-commands-for-fast-hologram-manipulation"></a>快速全息影像操作的語音命令

在撥雲見日時，您可以說出一些語音命令，以快速執行操作工作。 這些語音命令適用于應用程式視窗，以及您在世界中所放置的3D 物件。

**全息影像操作命令**
* 臉部我
* 較大 |增加
* 較小

在 HoloLens 2 上，您也可以結合眼睛來建立更自然的互動，以隱含地提供有關您所指的內容資訊。 例如，您可以直接查看全像投影，然後說「put_這個_」，然後查看要放置它的位置，然後說「到_這裡_」。
或者，您可以查看複雜電腦上的全像攝影元件，並說：「提供更多關於_此_的詳細資訊」。



## <a name="discovering-voice-commands"></a>探索語音命令

某些命令（例如上述快速操作的命令）可以隱藏起來。 若要深入瞭解您可以使用的命令，請看一個物件，並說「我可以說什麼？」。 可能會彈出的命令清單。 您也可以使用 head 注視游標來尋找並顯示您前面的每個按鈕的語音工具提示。 

如果您想要完整的清單，只要說「顯示所有命令」即可。 


## <a name="dictation"></a>聽寫

語音聽寫可以更有效率地在應用程式中輸入文字，而不是鍵入[空中](gaze-and-commit.md#composite-gestures)。 這可以大幅加速輸入，讓使用者的工作更少。

![語音聽寫一開始會選取 [麥克風] 按鈕](images/micbuttonfordictation.png)<br>
*語音聽寫一開始會選取鍵盤上的 [麥克風] 按鈕*

當全像攝影鍵盤在使用中時，您可以切換到聽寫模式，而不是輸入。 選取文字輸入方塊旁邊的麥克風以開始使用。


## <a name="adding-voice-commands-to-your-app"></a>將語音命令新增至您的應用程式

請考慮對您所建置的任何體驗新增語音命令。 語音是功能強大的方式，可方便您控制系統和應用程式。 因為使用者說話時的語調和口音各異，適當選擇語音關鍵字才能確保系統會分毫不差地解讀出使用者的命令。

### <a name="best-practices"></a>最佳作法

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
   * 「移至開始」

### <a name="advantages-of-voice-input"></a>語音輸入的優點

語音輸入是很自然的意圖溝通方式。 語音在介面**周遊**上特別有用，因為它可協助使用者剪下介面的多個步驟（使用者可能會在查看網頁時說「返回」，而不需要在應用程式中按 [上一步] 按鈕）。 這小段節省時間對於使用者對體驗的認知具有強大的**情緒效果**，並賦予他們少量的增強。 當我們無法騰出雙手或是在執行**多工**處理時，使用語音也是很方便的輸入方法。 在鍵盤上輸入的裝置很棘手，**語音聽寫**可以是輸入文字的有效替代方式。 最後，在某些情況下，當注視和手勢的**精確度範圍**受到限制時，voice 可以協助區分使用者的意圖。 

**使用語音如何讓使用者受益**
* 減少時間 - 語音應該會讓最終目標更有效率。
* 最不費力 - 語音應該會讓工作變得更為流暢且更不費力。
* 降低認知負荷 - 語音既直覺、易於了解且容易記住。
* 符合社交規範 - 語音應該會符合社會行為規範。
* 語音很平常 - 語音隨時可以變成慣常行為。

### <a name="challenges-for-voice-input"></a>語音輸入的挑戰

雖然語音輸入非常適用于許多不同的應用程式，但也面臨幾項挑戰。 瞭解語音輸入的優點和挑戰，可以讓應用程式開發人員針對使用語音輸入的方式和時機，以及為使用者建立絕佳體驗，提供更聰明的選擇。

**連續輸入控制項的語音輸入**精細的控制是其中一種。 例如，使用者可能會想要在其「音樂」應用程式中變更其磁片區。 她可以直接說「更高」，但並不清楚系統應該將磁片區設為多少。 使用者可能會說：「讓它變得更大」，但是「有點」難以量化。 使用語音移動或調整全息影像也很棘手。 

**語音輸入偵測的可靠性**雖然語音輸入系統變得更好且更好，但有時可能會不正確地聽到並解讀語音命令。
重點是要在系統接聽時提供意見反應給使用者，以及系統瞭解如何在正確瞭解使用者的潛在問題上建立清楚，以解決應用程式中的這項挑戰。  

**共用空間中的語音輸入**在您與其他人共用的空間中，語音可能無法社交接受。
以下是一些範例：
* 使用者可能不想干擾其他人（例如，在安靜程式庫或共用的辦公室）
* 使用者可能會覺得很難在公眾中看到自己的溝通，
* 當其他人正在接聽時，使用者可能會覺得不會聽寫個人或機密郵件（包括密碼）

**唯一或未知單字的語音輸入**語音輸入的困難也會在使用者聽寫可能對系統不明的字組（例如，昵稱、特定的俚語字組或縮寫）時出現。 

**學習語音命令**雖然最終目標是要與您的系統自然配合，但應用程式通常還是會依賴特定預先定義的語音命令。
與一組大量語音命令相關的挑戰，就是如何在不多載使用者的情況下教他們，以及如何協助使用者加以保留。 

<br>

---

### <a name="voice-feedback-states"></a>語音反饋狀態

當語音正確套用時，使用者會了解**他們能說什麼並獲得清楚的反饋**而知道系統**正確聽懂他們的語音**。 這兩個訊號會讓使用者有信心，確信他們可以使用語音作為主要輸入方式。 下圖顯示的是當系統辨識到語音輸入時會有什麼情形，以及系統會如何讓使用者知道這一點。


:::row:::
    :::column:::
       ![1. 一般資料指標狀態](images/voicefeedbackstates-regular.jpg)<br>
       **1. 一般資料指標狀態**<br>
    :::column-end:::
    :::column:::
       ![2. 傳達語音意見反應，然後消失](images/voicefeedbackstates-voice.jpg)<br>
        **2. 傳達語音意見反應，然後消失**<br>
    :::column-end:::
    :::column:::
       ![第. 一般游標狀態](images/voicefeedbackstates-regular.jpg)<br>
       **3. 回到一般游標狀態**<br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

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

## <a name="communication"></a>通訊

對於想要利用 HoloLens 所提供之自訂音訊輸入處理選項的應用程式，請務必瞭解您的應用程式可以使用的各種[音訊串流類別](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx)。 Windows 10 支援數種不同的串流類別和 HoloLens，使用其中三種來啟用自訂處理，以優化專為語音、通訊及其他的麥克風音訊品質，可用於環境的音訊捕捉（也就是「攝影機」）案例。
* [AudioCategory_Communications 串流] 類別是針對呼叫品質和旁白案例自訂，並為用戶端提供使用者語音的 Riff-16khz-16bit-mono-pcm 24bit mono 音訊串流
* [AudioCategory_Speech 串流] 類別是針對 HoloLens （Windows）語音引擎自訂，並提供該使用者語音的 Riff-16khz-16bit-mono-pcm 24bit mono 串流。 如有需要，可由協力廠商語音引擎使用此類別。
* [AudioCategory_Other 資料流程] 類別是針對環境環境音訊錄製而自訂，並提供 48kHz 24 位身歷聲音訊串流的用戶端。

所有此音訊處理都是硬體加速的，這表示在 HoloLens CPU 上進行相同的處理時，這些功能的耗電量會少很多。 避免在 CPU 上執行其他音訊輸入處理，以將系統電池壽命最大化，並利用內建的卸載音訊輸入處理。

## <a name="languages"></a>語言

HoloLens 2[支援多種語言](https://docs.microsoft.com/hololens/hololens2-language-support)。 請記住，即使已安裝多個鍵盤，或是應用程式嘗試以不同的語言建立語音辨識器，語音命令也一律會以系統的顯示語言執行。

## <a name="troubleshooting"></a>疑難排解

如果您在使用「選取」和「嘿 Cortana」時遇到任何問題，請嘗試移到更好的空間、離開雜訊來源，或說出更大的聲音。 目前，所有的 HoloLens 語音辨識都是針對美國英文的原生喇叭進行微調與優化。

對於 Windows Mixed Reality Developer Edition 版本2017，在初始 HMD 連線之後，音訊端點管理邏輯會正常執行（永遠）到電腦桌面。 在經過 WMR OOBE 之後，第一次登出/進入事件之前，使用者可能會遇到各種音訊功能問題，範圍從沒有音訊到音訊切換，這取決於第一次連線 HMD 之前設定系統的方式。

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a>適用于 Unity 的 MRTK （混合現實工具組）中的語音輸入
有了**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**，您就可以輕鬆地在任何物件上指派語音命令。 使用 MRTK 的**語音輸入設定檔**來定義您的關鍵字。 藉由指派**SpeechInputHandler**腳本，您可以讓任何物件回應語音輸入設定檔中所定義的關鍵字。 SpeechInputHandler 也提供語音確認標籤，以改善使用者的信心。

* [MRTK-Voice 命令](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html)


---

## <a name="see-also"></a>另請參閱
* [目光和行動](gaze-and-commit.md)
* [本能互動](interaction-fundamentals.md)
* [MR Input 212：語音](holograms-212.md)
* [DirectX 中的語音輸入](voice-input-in-directx.md)
* [Unity 中的語音輸入](voice-input-in-unity.md)
