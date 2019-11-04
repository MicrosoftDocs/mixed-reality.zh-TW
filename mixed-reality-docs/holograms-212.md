---
title: MR 輸入 212-語音
description: 請遵循使用 Unity、Visual Studio 和 HoloLens 進行的編碼逐步解說，以瞭解語音概念的詳細資料。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit-unity、學院、教學課程、語音
ms.openlocfilehash: 9db503ea4c7db9a3eb272ad9663024ca3a407dda
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434595"
---
>[!NOTE]
>混合現實學術教學課程的設計是使用 HoloLens （第1代）和混合現實的沉浸式耳機。  因此，對於仍在尋找這些裝置開發指引的開發人員而言，我們覺得這些教學課程很重要。  這些教學課程 **_不_** 會以最新的工具組或用於 HoloLens 2 的互動進行更新。  系統會保留這些資訊，以繼續在支援的裝置上運作。 HoloLens 2 已張貼[一系列新的教學](mrlearning-base.md)課程。

<br>

# <a name="mr-input-212-voice"></a>MR 輸入212：語音

[語音輸入](voice-input.md)可讓我們以另一種方式與我們的全息影像互動。 語音命令以非常自然且簡單的方式工作。 設計您的語音命令，使其成為：

* 自然災害
* 容易記住
* 適當的內容
* 與相同內容中的其他選項有充分的區別

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

在[MR 基本概念 101](holograms-101.md)中，我們使用 KeywordRecognizer 來建立兩個簡單的語音命令。 在 MR 輸入212中，我們將深入探討並瞭解如何：

* 設計針對 HoloLens 語音引擎優化的語音命令。
* 讓使用者知道有哪些語音命令可供使用。
* 承認我們聽到了使用者的語音命令。
* 使用聽寫辨識器來瞭解使用者所說的意義。
* 使用文法辨識器，根據 SRGS 或語音辨識文法規格（file）接聽命令。

在本課程中，我們將重新探討 Model Explorer，我們在[Mr 輸入 210](holograms-210.md)和[mr 輸入 211](holograms-211.md)中建立。

>[!IMPORTANT]
>下列各章節所內嵌的影片，都是使用舊版 Unity 和混合現實工具組錄製的。 雖然逐步指示是正確且最新的，但您可能會在已過期的對應影片中看到腳本和視覺效果。 影片仍包含在 posterity 中，因為涵蓋的概念仍適用。


## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>粗</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td>MR 輸入212：語音</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>開始之前

### <a name="prerequisites"></a>必要條件

* [已安裝正確工具](install-the-tools.md)的 WINDOWS 10 電腦。
* 一些基本C#的程式設計能力。
* 您應已完成[MR 基本概念 101](holograms-101.md)。
* 您應已完成[MR 輸入 210](holograms-210.md)。
* 您應已完成[MR 輸入 211](holograms-211.md)。
* [為開發設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 裝置。

### <a name="project-files"></a>專案檔案

* 下載專案[所需的](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip)檔案。 需要 Unity 2017.2 或更新版本。
* 將檔案取消封存至您的桌面或其他容易到達的位置。

>[!NOTE]
>如果您想要在下載之前查看原始程式碼，可以[在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice)取得。

### <a name="errata-and-notes"></a>勘誤和注意事項

* 必須在 Visual Studio 下的 [工具]-[> 選項]-[> 的偵錯工具] 中停用（*取消*核取） [啟用 Just My Code]，才能在程式碼中叫用中斷點。

## <a name="unity-setup"></a>Unity 設定

### <a name="instructions"></a>指示

1. 啟動 Unity。
2. 選取 [**開啟**]。
3. 流覽至您先前取消封存的**HolographicAcademy-全息-212-Voice**資料夾。
4. 尋找並選取 [**開始**/**模型瀏覽器**] 資料夾。
5. 按一下 [**選取資料夾**] 按鈕。
6. 在 [**專案**] 面板中，展開 [**幕後**] 資料夾。
7. 按兩下 [ **ModelExplorer**場景]，將其載入 Unity。

### <a name="building"></a>建置

1. 在 Unity 中，選取 [檔案] **> [組建設定**]。
2. 如果 [**場景/ModelExplorer** ] 未在 [組建] 的**場景**中列出，請按一下 [**新增開啟場景**] 以加入場景。
3. 如果您是特別針對 HoloLens 進行開發，請將**目標裝置**設定為**hololens**。 否則，請將它保留在**任何裝置**上。
4. 確定 [**組建類型**] 設定為 [ **D3D** ]，並將 [ **sdk** ] 設定為 [**已安裝最新**版本] （應該是 SDK 16299 或更新版本）。
5. 按一下 [建置]。
6. 建立名為 "App" 的**新資料夾**。
7. 按一下 [**應用程式**] 資料夾。
8. 按下 [**選取資料夾**]，Unity 就會開始建立 Visual Studio 的專案。

當 Unity 完成時，將會出現 [檔案瀏覽器] 視窗。

1. 開啟**應用程式**資料夾。
2. 開啟**ModelExplorer Visual Studio 解決方案**。

如果部署至 HoloLens：

1. 使用 Visual Studio 中的頂端工具列，將目標從 [調試] 變更為 [**發行**]，將 [從 ARM] 變更為**x86**。
2. 按一下 [本機電腦] 按鈕旁的下拉式箭號，然後選取 [**遠端電腦**]。
3. 輸入**您的 HoloLens 裝置 IP 位址**，並將驗證模式設定為 **[通用（未加密的通訊協定）** ]。 按一下 [**選取**]。 如果您不知道您的裝置 IP 位址，請查看 [設定] [ **> Network & Internet] > [Advanced Options**]。
4. 在頂端功能表列中，按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。 如果這是您第一次部署至您的裝置，您必須將[它與 Visual Studio 配對](using-visual-studio.md#pairing-your-device)。
5. 應用程式部署完成後，請使用**select 手勢**來關閉**Fitbox** 。

如果部署到沉浸式耳機：

1. 使用 Visual Studio 中的頂端工具列，將目標從 [調試] 變更為 [**發行**]，將 [從 ARM] 變更為**x64**。
2. 請確定 [部署目標] 設定為 [**本機電腦**]。
3. 在頂端功能表列中，按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。
4. 應用程式部署完成後，請藉由在動作控制器上提取觸發程式來關閉**Fitbox** 。

>[!NOTE]
>在 [Visual Studio 錯誤] 面板中，您可能會注意到一些紅色錯誤。 可以放心地忽略它們。 切換至 [輸出] 面板以查看實際的組建進度。 [輸出] 面板中的錯誤會要求您進行修正（最常見的原因是腳本錯誤）。

## <a name="chapter-1---awareness"></a>第1章-認知

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a>目標

* 瞭解語音命令設計的**Dos 和非注意事項**。
* 使用**KeywordRecognizer**來新增注視型語音命令。
* 使用游標**意見**反應讓使用者知道語音命令。

### <a name="voice-command-design"></a>語音命令設計

在本章中，您將瞭解如何設計語音命令。 建立語音命令的時機：

#### <a name="do"></a>DO

* 建立簡潔的命令。 您不想使用 *[播放目前選取的影片]* ，因為該命令並不簡潔，而且使用者很容易就會忘記。 相反地，您應該使用：「*播放影片*」，因為它很簡潔，而且有多個音節。
* 使用簡單的詞彙。 請一律嘗試使用簡單的字詞和片語，讓使用者輕鬆探索並記住。 例如，如果您的應用程式具有可從 view 顯示或隱藏的記事物件，您就不會使用 " *Show 牌子"* 命令，因為 "牌子" 是很少使用的詞彙。 相反地，您會使用命令：「 *Show Note*」，在您的應用程式中顯示便箋。
* 保持一致。 語音命令在您的應用程式中應該保持一致。 假設您的應用程式中有兩個場景，而這兩個場景都包含一個用來關閉應用程式的按鈕。 如果第一個場景使用「結束」*命令來觸發*按鈕，但第二個場景使用「*關閉應用程式*」命令，那麼使用者就會變得非常困惑。 如果相同的功能跨多個場景持續存在，則應該使用相同的語音命令來觸發它。

#### <a name="dont"></a>不要

* 使用單一的音節命令。 例如，如果您要建立語音命令來播放影片，應該避免使用簡單的命令「*播放*」，因為它只是單一的音節，而且系統可能會輕易地錯過。 相反地，您應該使用：「*播放影片*」，因為它很簡潔，而且有多個音節。
* 使用系統命令。 系統會保留 *"Select"* 命令，以觸發目前焦點物件的攻絲事件。 請勿在關鍵字或片語中重複使用 *"Select"* 命令，因為它可能無法如您預期般運作。 例如，如果在應用程式中選取 cube 的語音命令是「*選取 cube*」，但使用者在從未提到命令時查看球體，則會改為選取球體。 同樣地，應用程式行命令也會啟用語音。 請勿在您的 CoreWindow 視圖中使用下列語音命令：
    1. 回去
    2. 捲軸工具
    3. 縮放工具
    4. 拖曳工具
    5. Adjust
    6. 移除
* 使用類似的聲音。 請嘗試避免使用 rhyme 的語音命令。 如果您的購物應用程式支援「*顯示存放區*」和「*顯示更多*」做為語音命令，則您會想要在另一個使用中時停用其中一個命令。 例如，您可以使用 [*顯示存放區]* 按鈕來開啟存放區，然後在顯示商店時停用該命令，讓 [*顯示更多]* 命令可以用於流覽。

### <a name="instructions"></a>指示

* 在**Unity 的 [** 階層] 面板中，使用 [搜尋] 工具來尋找**holoComm_screen_mesh**物件。
* 按兩下 [ **holoComm_screen_mesh** ] 物件，在**場景**中進行查看。 這是太空人的監看式，它會回應我們的語音命令。
* 在 [偵測**器**] 面板中，找出 [**語音輸入來源（腳本）** ] 元件。
* 展開 [**關鍵字**] 區段以查看支援的語音命令： [**開啟 Communicator**]。
* 按一下右側的 [齒輪]，然後選取 [**編輯腳本**]。
* 探索**SpeechInputSource.cs**以瞭解它如何使用**KeywordRecognizer**來新增語音命令。

### <a name="build-and-deploy"></a>組建和部署

* 在 Unity 中，使用檔案 **> 組建設定**來重建應用程式。
* 開啟**應用程式**資料夾。
* 開啟**ModelExplorer Visual Studio 解決方案**。

（如果您已經在安裝期間于 Visual Studio 內建立/部署此專案，則可以開啟 VS 的實例，然後在出現提示時按一下 [全部重載]）。

* 在 Visual Studio 中，按一下 [ **Debug-> 啟動但不進行調試**] 或按**Ctrl + F5**。
* 將應用程式部署至 HoloLens 之後，請[使用 [點按] 手勢關閉](gaze-and-commit.md#composite-gestures)[調整] 方塊。
* 觀賞太空人的監看。
* 當監看式具有焦點時，請確認游標變更為麥克風。 這會提供應用程式接聽語音命令的意見反應。
* 確認 [監看式] 上出現工具提示。 這可協助使用者探索 *"Open Communicator"* 命令。
* 在監看撥雲見日時，請說「*開啟 communicator* 」以開啟 communicator 面板。

## <a name="chapter-2---acknowledgement"></a>第2章-通知

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a>目標

* 使用麥克風輸入記錄訊息。
* 提供意見反應給應用程式正在接聽其語音的使用者。

>[!NOTE]
>必須針對要從麥克風錄製的應用程式宣告**麥克風**功能。 您已在 MR 輸入212中完成這項作業，但請記住您自己的專案。
>
>1. 在 Unity 編輯器中，流覽至 [編輯 > 專案設定 > Player]，移至播放程式設定
>2. 按一下 [通用 Windows 平臺] 索引標籤
>3. 在 [發佈設定 > 功能] 區段中，檢查**麥克風**功能

### <a name="instructions"></a>指示

* 在**Unity 的 [** 階層] 面板中，確認已選取 [ **holoComm_screen_mesh** ] 物件。
* 在 [偵測**器**] 面板中，尋找 [**太空人 Watch （腳本）]** 元件。
* 按一下已設定為**Communicator Prefab**屬性值的小型藍色 cube。
* 在 [**專案**] 面板中， **Communicator** prefab 現在應該會有焦點。
* 按一下 [**專案**] 面板中的 [ **Communicator** ] prefab，以在偵測**器**中查看其元件。
* 查看**麥克風管理員（腳本）** 元件，這可讓我們記錄使用者的聲音。
* 請注意， **Communicator**物件具有用來回應 [**傳送訊息**] 命令的**語音輸入處理常式（腳本）** 元件。
* 查看**Communicator （Script）** 元件，然後按兩下腳本以在 Visual Studio 中開啟它。

Communicator.cs 會負責在 communicator 裝置上設定適當的按鈕狀態。 這可讓我們的使用者記錄郵件、播放訊息，並將訊息傳送至太空人。 它也會啟動和停止動畫 wave 表單，以向使用者表示其聲音已聽到。

* 在**Communicator.cs**中，從**Start**方法刪除下列幾行（81和82）。 這會啟用 communicator 上的 [記錄] 按鈕。

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a>組建和部署

* 在 Visual Studio 中，重建您的應用程式並部署至裝置。
* 看一下太空人的監看，並說「*開啟 communicator* 」來顯示 Communicator。
* 按 [**錄製**] 按鈕（麥克風）開始錄製太空人的口頭訊息。
* 開始說話，並確認 wave 動畫在 communicator 上播放，這會提供意見反應給使用者聽到語音的聲音。
* 按下 [**停止**] 按鈕（左正方形），然後確認 wave 動畫停止執行。
* 按下 [**播放**] 按鈕（直角三角形）來播放錄製的訊息，並在裝置上聆聽。
* 按下 [**停止**] 按鈕（右方形）以停止播放已錄製的訊息。
* 說出「*傳送訊息*」，關閉 communicator 並接收來自太空人的「收到的訊息」回應。

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a>第3章-瞭解和聽寫辨識器

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a>目標

* 使用聽寫辨識器將使用者的語音轉換成文字。
* 在 communicator 中顯示聽寫辨識器的假設和最終結果。

在本章中，我們將使用聽寫辨識器來建立太空人的訊息。 使用聽寫辨識器時，請記住：

* 您必須連接到 WiFi，聽寫辨識器才能正常執行。
* 在設定的一段時間後發生超時。 有兩個要注意的超時：
  * 如果辨識器啟動且未在前五秒聽到任何音訊，則會超時。
  * 如果辨識器已指定結果，但接著會聽到24秒的無聲，則會超時。
* 一次只能執行一種類型的辨識器（關鍵字或聽寫）。

>[!NOTE]
>必須針對要從麥克風錄製的應用程式宣告**麥克風**功能。 您已在 MR 輸入212中完成這項作業，但請記住您自己的專案。
>
>1. 在 Unity 編輯器中，流覽至 [編輯 > 專案設定 > Player]，移至播放程式設定
>2. 按一下 [通用 Windows 平臺] 索引標籤
>3. 在 [發佈設定 > 功能] 區段中，檢查**麥克風**功能

### <a name="instructions"></a>指示

我們即將編輯**MicrophoneManager.cs**以使用聽寫辨識器。 這就是我們要加入的內容：

1. 按下 [**錄製] 按鈕**時，我們會**開始 DictationRecognizer**。
2. 顯示 DictationRecognizer 瞭解的**假設**。
3. 鎖定 DictationRecognizer 瞭解的**結果**。
4. 檢查 DictationRecognizer 的是否有超時。
5. 當按下 [**停止] 按鈕**或 mic 會話超時時，請**停止 DictationRecognizer**。
6. 重新開機**KeywordRecognizer**，這會接聽 [**傳送訊息**] 命令。

那就開始吧。 在**MicrophoneManager.cs**中完成所有的程式碼撰寫練習，或複製並貼上完成的程式碼，如下所示：

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

### <a name="build-and-deploy"></a>組建和部署

* 在 Visual Studio 中重建，並部署至您的裝置。
* 使用 [空中] 手勢關閉 [調整] 方塊。
* 觀賞太空人的監看，並說出「 *Open Communicator*」。
* 選取 [**錄製**] 按鈕（麥克風）以記錄您的訊息。
* 開始說話。 **聽寫辨識器**會解讀您的語音，並在 communicator 中顯示假設的文字。
* 當您錄製訊息時，請嘗試說出「*傳送訊息*」。 請注意，**關鍵字辨識器**不會回應，因為**聽寫辨識器**仍在作用中。
* 停止說話幾秒鐘的時間。 監看聽寫辨識器如何完成其假設，並顯示最終結果。
* 開始說話，然後暫停20秒。 這會導致**聽寫辨識器**超時。
* 請注意，在上述的超時之後，會重新啟用**關鍵字辨識器**。 Communicator 現在會回應語音命令。
* 說「*傳送訊息*」將訊息傳送至太空人。

## <a name="chapter-4---grammar-recognizer"></a>第4章-文法辨識器

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a>目標

* 使用文法辨識器，根據 SRGS 或語音辨識文法規格（file）識別使用者的語音。

>[!NOTE]
>必須針對要從麥克風錄製的應用程式宣告**麥克風**功能。 您已在 MR 輸入212中完成這項作業，但請記住您自己的專案。
>
>1. 在 Unity 編輯器中，流覽至 [編輯 > 專案設定 > Player]，移至播放程式設定
>2. 按一下 [通用 Windows 平臺] 索引標籤
>3. 在 [發佈設定 > 功能] 區段中，檢查**麥克風**功能

### <a name="instructions"></a>指示

1. **在 [階層**] 面板中，搜尋**Jetpack_Center**並加以選取。
2. 在 [偵測**器**] 面板中尋找**Tagalong 動作**腳本。
3. 按一下要**沿著欄位標記的物件**右邊的小圓圈。
4. 在快顯的視窗中，搜尋**SRGSToolbox** ，並從清單中選取它。
5. 請查看**StreamingAssets**資料夾中的**SRGSColor。**
    1. 您可以在[這裡](https://www.w3.org/TR/speech-grammar/)的 W3C 網站上找到 SRGS 設計規格。

在我們的 SRGS 檔案中，我們有三種類型的規則：

* 一種規則，可讓您從十二種色彩的清單中說出一種色彩。
* 這三個規則會接聽色彩規則和三個圖形其中之一的組合。
* 根規則 colorChooser，它會接聽三種「色彩和形狀」規則的任何組合。 這些圖形可以用任何順序來表示，而且從1到三的任何數量都是。 這是唯一接聽的規則，因為它是在初始 &lt;文法&gt; 標記中的檔案頂端指定為根規則。

### <a name="build-and-deploy"></a>組建和部署

* 在 Unity 中重建應用程式，然後從 Visual Studio 建立及部署，以在 HoloLens 上體驗應用程式。
* 使用 [空中] 手勢關閉 [調整] 方塊。
* 看一下太空人的 jetpack，並執行空中碰手勢。
* 開始說話。 **文法辨識器**會解讀您的語音，並根據辨識變更圖形的色彩。 範例命令為「藍色圓形、黃色正方形」。
* 執行另一個空中碰手勢來關閉 [工具箱]。

## <a name="the-end"></a>結束

恭喜！ 您現在已完成**MR 輸入212： Voice**。

* 您知道語音命令的 Dos 和注意事項。
* 您已瞭解如何運用工具提示，讓使用者知道語音命令。
* 您看到了數種類型的意見反應，用來確認使用者的語音已被聽到。
* 您知道如何在關鍵字辨識器和聽寫辨識器之間切換，以及這兩項功能如何瞭解和解讀您的聲音。
* 您已瞭解如何在應用程式中使用 SRGS 檔案和文法辨識器來進行語音辨識。
