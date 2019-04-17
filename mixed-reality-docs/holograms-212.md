---
title: MR 輸入 212-語音
description: 請遵循此程式碼撰寫的逐步解說，使用 Unity、 Visual Studio 和 HoloLens，若要了解語音概念的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、 mixedrealitytoolkit、 mixedrealitytoolkit unity、 academy、 教學課程中，語音
ms.openlocfilehash: 7e792bf40c47d4e1d57898fbe75ad050a030b7e3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591403"
---
>[!NOTE]
>混合實境 Academy 教學課程的設計與 HoloLens （第 1 代） 及混合實境沈浸式耳機記住。  因此，我們覺得很重要的開發人員仍會尋找針對這些裝置進行開發的指引，讓這些教學課程中留在原處。  這些教學課程會**_不_** 使用最新的工具組或用於 HoloLens 2 的互動進行更新。  它們會繼續運作，支援的裝置上維護。 會有新教學課程系列，將會公佈在未來，將示範如何開發 HoloLens 2。  當他們回傳時，本聲明將會更新這些教學課程的連結。

<br>

# <a name="mr-input-212-voice"></a>MR 輸入 212:語音

[語音輸入](voice-input.md)提供另一種方式與我們全像投影互動。 語音命令運作非常自然且簡單的方式。 設計您的語音命令，使它們：

* 自然
* 容易記憶
* 適當的內容
* 足以區別相同內容中的其他選項

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

在  [MR 基本概念 101](holograms-101.md)，我們用 KeywordRecognizer 來建置兩個簡單的語音命令。 在 MR 輸入 212，我們將更深入了解，並了解如何：

* 設計最適合用於 HoloLens 語音引擎的語音命令。
* 讓使用者知道哪些語音命令的可用。
* 了解，我們得知使用者的語音命令。
* 了解使用者的是誰說，使用聽寫辨識器。
* 使用文法辨識器接聽 SRGS 或語音辨識文法規格，檔案為基礎的命令。

在此課程中，我們再探討模型總管 中，我們在建置[MR 輸入 210](holograms-210.md)並[MR 輸入 211](holograms-211.md)。

>[!IMPORTANT]
>使用 Unity 及混合實境 toolkit 的推出較舊的版本記錄中的下列章節的每個內嵌的影片。 雖然的逐步指示是準確且即時的您可能會看到指令碼和對應已過期的影片中的視覺效果。 影片仍包含 posterity，和因為概念涵蓋仍然適用。


## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>課程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td>MR 輸入 212:語音</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>開始之前

### <a name="prerequisites"></a>必要條件

* Windows 10 電腦的正確設定[安裝工具](install-the-tools.md)。
* 基本C#程式設計的能力。
* 您應已完成[MR 基本概念 101](holograms-101.md)。
* 您應已完成[MR 輸入 210](holograms-210.md)。
* 您應已完成[MR 輸入 211](holograms-211.md)。
* HoloLens 裝置[開發設定的](using-visual-studio.md#enabling-developer-mode)。

### <a name="project-files"></a>專案檔

* 下載[檔案](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip)專案所需。 需要 Unity 2017.2 或更新版本。
* 取消封存您的桌面或其他您輕鬆地連線到位置的檔案。

>[!NOTE]
>如果您想要查看原始程式碼，在下載之前，它有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice)。

### <a name="errata-and-notes"></a>偵錯 errata 和附註

* 若要停用 啟用 Just My Code 的需求 (*未核取*) 在 Visual Studio 的 工具-> 選項-> 偵錯以程式碼中設定中斷點。

## <a name="unity-setup"></a>Unity 安裝

### <a name="instructions"></a>指示

1. 啟動 Unity。
2. 選取 **開啟**。
3. 瀏覽至**HolographicAcademy 全像投影-212 語音**資料夾您先前未封存。
4. 尋找並選取**起始**/**模型總管**資料夾。
5. 按一下 [**選取資料夾**] 按鈕。
6. 在 [**專案**] 面板中，展開**場景**資料夾。
7. 按兩下**ModelExplorer**載入在 Unity 中的場景。

### <a name="building"></a>建置

1. 在 Unity 中，選取**檔案 > 組建設定**。
2. 如果**場景/ModelExplorer**中未列出**組建中的場景**，按一下 **加入開啟的場景**加入場景。
3. 如果您要特別開發的 HoloLens，設定**目標裝置**要**HoloLens**。 否則，將它保留在**任何裝置**。
4. 確保**建置型別**設為**D3D**並**SDK**設定為**最新安裝**（這應該可以 16299 或更新版本的 SDK）。
5. 按一下 [建置] 。
6. 建立**新的資料夾**名為 「 應用程式 」。
7. 只要按一下**應用程式**資料夾。
8. 按下**選取資料夾**，Unity 將會啟動 Visual studio 中建置專案。

Unity 完成時，會出現檔案總管 視窗。

1. 開啟**應用程式**資料夾。
2. 開啟**ModelExplorer Visual Studio 解決方案**。

如果將部署到 HoloLens:

1. 使用頂端的工具列，在 Visual Studio 中，從 偵錯，若要變更目標**Release**進出至 ARM **x86**。
2. 按一下下拉式清單 [本機電腦] 按鈕旁邊的箭號，然後選取**遠端機器**。
3. 請輸入**HoloLens 裝置的 IP 位址**並將驗證模式設定為**通用 （未加密的通訊協定）**。 按一下 **選取**。 如果您不知道您的裝置 IP 位址，查看**設定 > 網路和網際網路 > 進階選項**。
4. 在頂端功能表列中，按一下**偵錯]-> [啟動但不偵錯**或按**Ctrl + F5**。 如果這是第一次部署到您的裝置，您必須[與 Visual Studio 中配對](using-visual-studio.md#pairing-your-device-hololens)。
5. 當應用程式部署時，關閉**Fitbox**具有**選取 軌跡**。

如果將部署到擬真耳機：

1. 使用頂端的工具列，在 Visual Studio 中，從 偵錯，若要變更目標**Release**進出至 ARM **x64**。
2. 請確定部署目標設定為**本機電腦**。
3. 在頂端功能表列中，按一下**偵錯]-> [啟動但不偵錯**或按**Ctrl + F5**。
4. 當應用程式部署時，關閉**Fitbox**所提取的動作控制站上的觸發程序。

>[!NOTE]
>您可能會注意到一些紅色的錯誤，在 Visual Studio 的 [錯誤] 面板。 它可以安全地忽略它們。 切換至 [輸出] 面板，若要檢視實際組建進度。 在 [輸出] 面板中的錯誤會要求您修正 （最常在指令碼中發生錯誤所造成）。

## <a name="chapter-1---awareness"></a>第 1 章-感知

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a>目標

* 了解**守則**語音命令設計。
* 使用**KeywordRecognizer**將基礎的視線語音命令。
* 讓使用者使用資料指標的語音命令察覺**意見反應**。

### <a name="voice-command-design"></a>語音命令設計

在本章中，您將了解設計語音命令。 當建立語音命令：

#### <a name="do"></a>DO

* 建立精簡的命令。 您不想要 *「 遊戲的目前選取的視訊 」*，因為該命令不是精簡且容易會忘記使用者。 相反地，您應該使用：*「 播放的視訊"*，因為它是精確且有多個音節。
* 使用簡單的詞彙。 永遠嘗試使用常見的單字和片語，都能輕鬆地探索並記住使用者。 例如，如果您的應用程式有可能顯示或隱藏的附註物件，您可以不使用命令 *」 顯示牌子"*，因為 「 牌子 」 是一個很少使用的詞彙。 相反地，您可以使用命令：*「 顯示附註 」*，以顯示您的應用程式中的附註。
* 保持一致。 語音命令應該保持一致跨應用程式。 假設應用程式中有兩個場景，而這兩個場景包含按鈕以關閉應用程式。 如果第一個場景會使用命令 *"Exit"* 觸發按鈕，但第二個場景會使用命令 *「 關閉應用程式 」*，然後使用者要亂成一團了。 如果跨多個場景，保存相同的功能，則應該使用相同的語音命令觸發它。

#### <a name="dont"></a>不

* 使用單一音節命令。 例如，如果您所建立的語音命令，來播放視訊，您應該避免使用簡單的命令 *「 遊戲 」*，因為它是只有單一音節，輕鬆地可能遺漏的系統。 相反地，您應該使用：*「 播放的視訊"*，因為它是精確且有多個音節。
* 使用系統命令。 *"Select"* 命令已保留，由系統目前的焦點的物件的點選事件觸發程序。 不要重複使用 *"Select"* 命令中的關鍵字或片語，因為它可能無法運作如預期般。 比方說，如果應用程式中選取 cube 的語音命令已 *「 選取的 cube"*，但使用者想要球體時它們玩具店命令，則會改為選取的球體。 同樣的應用程式列命令是啟用的語音。 不在 corewindow 成為檢視中使用下列的語音命令：
    1. 返回
    2. 捲動工具
    3. 縮放工具
    4. 拖放工具
    5. Adjust
    6. 移除
* 使用類似的音效。 請盡量避免使用光的語音命令。 如果您已將購物應用程式支援 *「 顯示存放區 」* 並 *[顯示更多]* 做為語音命令，則您會想要其他正在使用中時，停用其中一個命令。 例如，您可以使用 *[顯示儲存]* 按鈕以開啟市集，並顯示存放區時，則停用該命令以便 *[顯示更多]* 命令可用來瀏覽。

### <a name="instructions"></a>指示

* 在 Unity**階層** 面板中，使用 「 搜尋 」 工具來尋找**holoComm_screen_mesh**物件。
* 按兩下**holoComm_screen_mesh**檢視中的物件**場景**。 這是太空人監看式，將會回我們的語音命令。
* 在 [ **Inspector** ] 面板中，找出**語音輸入來源 （指令碼）** 元件。
* 依序展開**關鍵字**區段可查看支援的語音命令：**開啟 Communicator**。
* 按一下至右邊的齒輪圖示，然後選取**編輯指令碼**。
* 瀏覽**SpeechInputSource.cs**若要了解如何使用**KeywordRecognizer**新增語音命令。

### <a name="build-and-deploy"></a>建置和部署

* 在 Unity 中，使用**檔案 > 組建設定**重建應用程式。
* 開啟**應用程式**資料夾。
* 開啟**ModelExplorer Visual Studio 解決方案**。

（如果您已經建置/部署此專案在 Visual Studio 設定期間，然後您可以開啟 VS 執行個體並按一下 [重新載入全部] 出現提示時）。

* 在 Visual Studio 中，按一下**偵錯]-> [啟動但不偵錯**或按**Ctrl + F5**。
* 應用程式部署到 HoloLens 之後，關閉 調整的方塊中，使用[空中點選](gestures.md#air-tap)筆勢。
* 注視太空人監看式。
* 當監看式有焦點時，請確認，游標會變成麥克風。 這會提供應用程式正在接聽的語音命令的意見反應。
* 請確認，工具提示會出現在 監看式。 這可協助使用者探索 *"開啟 Communicator"* 命令。
* 同時在監看式 gazing，說 *"開啟 Communicator"* 開啟 communicator 面板。

## <a name="chapter-2---acknowledgement"></a>第 2 章-通知

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a>目標

* 記錄使用麥克風輸入的訊息。
* 提供意見反應給使用者應用程式正在接聽其語音。

>[!NOTE]
>**麥克風**必須宣告功能，讓應用程式從麥克風錄製。 這是針對您已在 MR 輸入 212，但謹記在心，為您自己的專案。
>
>1. 瀏覽至 「 編輯 > 專案設定 > 播放程式 」 在 Unity 編輯器中，請移至播放程式設定
>2. 按一下 「 通用 Windows 平台 」 索引標籤
>3. 在 「 發行的設定 > 功能 」 區段中，檢查**麥克風**功能

### <a name="instructions"></a>指示

* 在 Unity**階層** 面板中，確認**holoComm_screen_mesh**選取物件。
* 在 [ **Inspector** ] 面板中，尋找**太空人監看式 （指令碼）** 元件。
* 按一下已設定的值為小型的藍色 cube **Communicator Prefab**屬性。
* 在 [**專案**] 面板中， **Communicator** prefab 現在應該有焦點。
* 按一下  **Communicator** prefab 中**專案**面板，以檢視及其元件**Inspector**。
* 看看**麥克風 Manager （指令碼）** 元件，這可讓我們來記錄使用者的語音。
* 請注意， **Communicator**物件具有**語音輸入處理常式 （指令碼）** 元件回應**傳送訊息**命令。
* 看看**Communicator （指令碼）** 元件，並按兩下要開啟 Visual Studio 中的指令碼。

Communicator.cs 負責 communicator 裝置上設定適當的按鈕狀態。 這可讓我們來記錄訊息、 播放它，並將訊息傳送至太空人的使用者。 它也會啟動並停止動畫的 wave 格式，以確認使用者語音已聽過。

* 在  **Communicator.cs**，從刪除下列幾行 （81 和 82）**開始**方法。 這可讓在 communicator 'Record' 按鈕。

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a>建置和部署

* 在 Visual Studio 中，重建您的應用程式並部署到裝置。
* 注視太空人監看式，並說 *"開啟 Communicator"* 顯示 communicator。
* 按下**記錄**按鈕 （麥克風） 開始的太空人錄製口說的訊息。
* 開始錄製，並確認 wave 動畫播放在 communicator，可提供給使用者的意見反應，要聽語音。
* 按下**停止**按鈕 （左上的方），並確認 wave 動畫停止執行。
* 按下**播放**播放錄製的訊息，並聆聽裝置上的按鈕 （右邊的三角形）。
* 按下**停止**按鈕 （右邊的正方形） 若要停止播放錄製的訊息。
* 假設 *[傳送訊息]* 關閉 communicator 並接收來自太空人 '收到的訊息' 的回應。

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a>第 3 章-了解和聽寫辨識器

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a>目標

* 您可以使用聽寫辨識器，使用者的語音轉換文字。
* Communicator 中會顯示聽寫辨識器虛無和最終結果。

在本章中，我們將使用聽寫辨識器為太空人建立一則訊息。 當使用聽寫辨識器，請注意下列事項：

* 您必須連線至 WiFi 聽寫辨識器運作。
* 在一段時間之後，就會發生逾時。 有兩個逾時，要注意的：
  * 如果辨識器啟動，且聽任何音訊第五秒，它就會逾時。
  * 如果辨識器已提供結果，但然後聽到 20 秒的無回應，它就會逾時。
* 只有一種類型的辨識器 （關鍵字或聽寫） 可以執行一次。

>[!NOTE]
>**麥克風**必須宣告功能，讓應用程式從麥克風錄製。 這是針對您已在 MR 輸入 212，但謹記在心，為您自己的專案。
>
>1. 瀏覽至 「 編輯 > 專案設定 > 播放程式 」 在 Unity 編輯器中，請移至播放程式設定
>2. 按一下 「 通用 Windows 平台 」 索引標籤
>3. 在 「 發行的設定 > 功能 」 區段中，檢查**麥克風**功能

### <a name="instructions"></a>指示

我們將編輯**MicrophoneManager.cs**使用聽寫辨識器。 這是我們將加入的項目：

1. 當**錄製 按鈕**是我們按下，將**開始 DictationRecognizer**。
2. 顯示**假設**的 DictationRecognizer 的瞭解。
3. 鎖住**結果**的 DictationRecognizer 的瞭解。
4. 檢查有從 DictationRecognizer 的逾時。
5. 當**停止 按鈕**按下時，或 mic 工作階段逾時，**停止 DictationRecognizer**。
6. 重新啟動**KeywordRecognizer**，用接聽**傳送訊息**命令。

那就開始吧。 完成 3.a 中的所有程式碼撰寫練習**MicrophoneManager.cs**，或複製並貼上完成的程式碼下方：

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using System.Collections;
using System.Text;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Windows.Speech;

namespace Academy
{
    public class MicrophoneManager : MonoBehaviour
    {
        [Tooltip("A text area for the recognizer to display the recognized strings.")]
        [SerializeField]
        private Text dictationDisplay;

        private DictationRecognizer dictationRecognizer;

        // Use this string to cache the text currently displayed in the text box.
        private StringBuilder textSoFar;

        // Using an empty string specifies the default microphone. 
        private static string deviceName = string.Empty;
        private int samplingRate;
        private const int messageLength = 10;

        // Use this to reset the UI once the Microphone is done recording after it was started.
        private bool hasRecordingStarted;

        void Awake()
        {
            /* TODO: DEVELOPER CODING EXERCISE 3.a */

            // 3.a: Create a new DictationRecognizer and assign it to dictationRecognizer variable.
            dictationRecognizer = new DictationRecognizer();

            // 3.a: Register for dictationRecognizer.DictationHypothesis and implement DictationHypothesis below
            // This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
            dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;

            // 3.a: Register for dictationRecognizer.DictationResult and implement DictationResult below
            // This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;

            // 3.a: Register for dictationRecognizer.DictationComplete and implement DictationComplete below
            // This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
            dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;

            // 3.a: Register for dictationRecognizer.DictationError and implement DictationError below
            // This event is fired when an error occurs.
            dictationRecognizer.DictationError += DictationRecognizer_DictationError;

            // Query the maximum frequency of the default microphone. Use 'unused' to ignore the minimum frequency.
            int unused;
            Microphone.GetDeviceCaps(deviceName, out unused, out samplingRate);

            // Use this string to cache the text currently displayed in the text box.
            textSoFar = new StringBuilder();

            // Use this to reset the UI once the Microphone is done recording after it was started.
            hasRecordingStarted = false;
        }

        void Update()
        {
            // 3.a: Add condition to check if dictationRecognizer.Status is Running
            if (hasRecordingStarted && !Microphone.IsRecording(deviceName) && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                // Reset the flag now that we're cleaning up the UI.
                hasRecordingStarted = false;

                // This acts like pressing the Stop button and sends the message to the Communicator.
                // If the microphone stops as a result of timing out, make sure to manually stop the dictation recognizer.
                // Look at the StopRecording function.
                SendMessage("RecordStop");
            }
        }

        /// <summary>
        /// Turns on the dictation recognizer and begins recording audio from the default microphone.
        /// </summary>
        /// <returns>The audio clip recorded from the microphone.</returns>
        public AudioClip StartRecording()
        {
            // 3.a Shutdown the PhraseRecognitionSystem. This controls the KeywordRecognizers
            PhraseRecognitionSystem.Shutdown();

            // 3.a: Start dictationRecognizer
            dictationRecognizer.Start();

            // 3.a Uncomment this line
            dictationDisplay.text = "Dictation is starting. It may take time to display your text the first time, but begin speaking now...";

            // Set the flag that we've started recording.
            hasRecordingStarted = true;

            // Start recording from the microphone for 10 seconds.
            return Microphone.Start(deviceName, false, messageLength, samplingRate);
        }

        /// <summary>
        /// Ends the recording session.
        /// </summary>
        public void StopRecording()
        {
            // 3.a: Check if dictationRecognizer.Status is Running and stop it if so
            if (dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                dictationRecognizer.Stop();
            }

            Microphone.End(deviceName);
        }

        /// <summary>
        /// This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
        /// </summary>
        /// <param name="text">The currently hypothesized recognition.</param>
        private void DictationRecognizer_DictationHypothesis(string text)
        {
            // 3.a: Set DictationDisplay text to be textSoFar and new hypothesized text
            // We don't want to append to textSoFar yet, because the hypothesis may have changed on the next event
            dictationDisplay.text = textSoFar.ToString() + " " + text + "...";
        }

        /// <summary>
        /// This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
        /// </summary>
        /// <param name="text">The text that was heard by the recognizer.</param>
        /// <param name="confidence">A representation of how confident (rejected, low, medium, high) the recognizer is of this recognition.</param>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // 3.a: Append textSoFar with latest text
            textSoFar.Append(text + ". ");

            // 3.a: Set DictationDisplay text to be textSoFar
            dictationDisplay.text = textSoFar.ToString();
        }

        /// <summary>
        /// This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
        /// Typically, this will simply return "Complete". In this case, we check to see if the recognizer timed out.
        /// </summary>
        /// <param name="cause">An enumerated reason for the session completing.</param>
        private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
        {
            // If Timeout occurs, the user has been silent for too long.
            // With dictation, the default timeout after a recognition is 20 seconds.
            // The default timeout with initial silence is 5 seconds.
            if (cause == DictationCompletionCause.TimeoutExceeded)
            {
                Microphone.End(deviceName);

                dictationDisplay.text = "Dictation has timed out. Please press the record button again.";
                SendMessage("ResetAfterTimeout");
            }
        }

        /// <summary>
        /// This event is fired when an error occurs.
        /// </summary>
        /// <param name="error">The string representation of the error reason.</param>
        /// <param name="hresult">The int representation of the hresult.</param>
        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            // 3.a: Set DictationDisplay text to be the error string
            dictationDisplay.text = error + "\nHRESULT: " + hresult;
        }

        /// <summary>
        /// The dictation recognizer may not turn off immediately, so this call blocks on
        /// the recognizer reporting that it has actually stopped.
        /// </summary>
        public IEnumerator WaitForDictationToStop()
        {
            while (dictationRecognizer != null && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                yield return null;
            }
        }
    }
}
```

### <a name="build-and-deploy"></a>建置和部署

* 在 Visual Studio 中重建並部署到您的裝置。
* 關閉 [調整] 方塊中的使用空中點選手勢。
* 注視太空人監看式，並說 *"開啟 Communicator"*。
* 選取 **記錄**按鈕 （麥克風） 來記錄您的訊息。
* 開始讀出。 **聽寫辨識器**會解譯您的語音，並在 communicator 顯示虛無的文字。
* 嘗試招呼語 *[傳送訊息]* 時記錄訊息。 請注意，**關鍵字的辨識器**不會回應，因為**聽寫辨識器**仍在作用中。
* 停止讀出幾秒鐘的時間。 觀看聽寫辨識器完成其假設，並顯示最終的結果。
* 開始讀出，然後暫停 20 秒。 這會導致**聽寫辨識器**逾時。
* 請注意，**關鍵字的辨識器**上述的逾時之後重新啟用。 Communicator 會立即回應語音命令。
* 假設 *[傳送訊息]* 太空人來傳送訊息。

## <a name="chapter-4---grammar-recognizer"></a>第 4 章-文法辨識器

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a>目標

* 使用文法辨識器辨識使用者的語音，依照 SRGS 或語音辨識文法規格的檔案。

>[!NOTE]
>**麥克風**必須宣告功能，讓應用程式從麥克風錄製。 這是針對您已在 MR 輸入 212，但謹記在心，為您自己的專案。
>
>1. 瀏覽至 「 編輯 > 專案設定 > 播放程式 」 在 Unity 編輯器中，請移至播放程式設定
>2. 按一下 「 通用 Windows 平台 」 索引標籤
>3. 在 「 發行的設定 > 功能 」 區段中，檢查**麥克風**功能

### <a name="instructions"></a>指示

1. 在 [**階層**] 面板中，搜尋**Jetpack_Center**並加以選取。
2. 尋求**Tagalong 動作**指令碼**Inspector**面板。
3. 按一下右邊的小圓圈**物件來標記沿著**欄位。
4. 在快顯視窗中，搜尋**SRGSToolbox**並從清單中選取。
5. 看看**SRGSColor.xml**中的檔案**StreamingAssets**資料夾。
* 請參閱 W3C 網站 SRGS 設計規格[此處](https://www.w3.org/TR/speech-grammar/)。
* 在我們 SRGS 檔案中，我們有三種類型的規則：
  * 可讓您說出十二個色彩的清單中的一個色彩規則。
  * 三個規則的接聽色彩規則和三個圖形的其中一個的組合。
  * 根規則 colorChooser，接聽的三個 「 色彩 + 圖形 」 規則的任何組合。 以任何順序，並在任何數量的只是其中所有三個可說是圖形。 這是唯一的規則會接聽該通訊埠，因為它已指定為初始中的檔案頂端的根規則&lt;文法&gt;標記。

### <a name="build-and-deploy"></a>建置和部署

* 重建應用程式在 Unity 中，然後建置並從 Visual Studio 體驗 HoloLens 上的應用程式部署。
* 關閉 [調整] 方塊中的使用空中點選手勢。
* 注視太空人 jetpack，並執行空中點選手勢。
* 開始讀出。 **文法辨識器**會解譯您的語音，並變更色彩的辨識為基礎的圖形。 命令的範例是 「 藍色圓形，黃色正方形 」。
* 執行以關閉工具箱 中的另一個空中點選手勢。

## <a name="the-end"></a>結束

恭喜您！ 您現在已完成**MR 輸入 212:語音**。

* 您知道守則的語音命令。
* 您已看到如何工具提示用來讓使用者知道的語音命令。
* 您看到了數種用來通知使用者的語音已聽過的意見反應。
* 您知道如何切換關鍵字辨識器與聽寫辨識器，以及這兩項功能如何了解和解譯您的聲音。
* 您已了解如何使用 語音辨識應用程式中的 SRGS 檔及文法辨識器。
