---
title: 語音輸入
description: 語音輸入是 HoloLens 和 Windows Mixed Reality 沉浸式耳機的核心輸入。 語音可以用於命令、聽寫、Cortana 等等。
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: ggv、語音、cortana、語音、輸入
ms.openlocfilehash: e21310b940e4a4c3019f61edea695b452e74ab62
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829955"
---
# <a name="voice-input"></a>語音輸入

Voice 是 HoloLens 輸入的三種主要形式之一。 它可讓您直接命令全息影像, 而不需要使用[手勢](gestures.md)。 您只需要[注視](gaze.md)一個全息的程式, 就可以說出您的命令。 語音輸入可以是傳達您意圖的自然方式。 語音在遍歷複雜介面時特別有用, 因為它可讓使用者使用一個命令剪下嵌套功能表。

語音輸入是由在所有其他通用 Windows 應用程式中支援語音的[相同引擎](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx)提供技術支援。

<br>

>[!VIDEO https://www.youtube.com/embed/eHMkOpNUtR8]

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
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>語音輸入</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (使用麥克風)</td>
    </tr>
</table>

## <a name="the-select-command"></a>"Select" 命令

即使未特別將語音支援新增至您的應用程式, 您的使用者只要說出「select」, 就可以啟動全息影像。 其行為與 HoloLens 上的[空中](gestures.md#air-tap)按鍵、按下[hololens clicker](hardware-accessories.md#hololens-clicker)上的 [選取] 按鈕, 或在[Windows Mixed Reality 動作控制器](motion-controllers.md)上按下觸發程式一樣。 您會聽到音效, 並看到包含 [選取] 的工具提示會顯示為 [確認]。 「選取」是由低乘冪關鍵字偵測演算法所啟用, 因此隨時都可讓您以最少的電池壽命影響來表示, 即使您的手中也一樣。

> [!NOTE]
> [即將推出](index.md#news-and-notes)更多 HoloLens 2 特定指引。

![說「選取」以使用語音命令進行選取](images/kma-voice-select-00170-800px.png)<br>
*說「選取」以使用語音命令進行選取*

## <a name="hey-cortana"></a>嗨 Cortana

您也可以說「嘿 Cortana」, 隨時帶出 Cortana。 您不需要等待她繼續詢問您的問題或提供指示, 例如, 試著說「嘿, 我的天氣是什麼？」 當做單一句子。 如需 Cortana 和您可以執行之動作的詳細資訊, 請直接詢問她! 說「嘿, 我可以說什麼？」 她會提取一個工作和建議的命令清單。 如果您已經在 Cortana 應用程式中, 也可以按一下 [ **？** ] 在提要欄位上拉出此相同功能表的圖示。

**HoloLens 特有的命令**
* 「我可以說什麼？」
* "Go home" 或 "Go to Start"-而不是[bloom](gestures.md#bloom)以進入 [[開始] 功能表](navigating-the-windows-mixed-reality-home.md#start-menu)
* 「啟動<app>」
* 「移<app>至這裡」
* 「拍照」
* 「開始錄製」
* 「停止錄製」
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
* "Call <contact>" (需要 Skype for HoloLens)

## <a name="see-it-say-it"></a>「見它」

HoloLens 有「看它, 假設是語音輸入的模型」, 其中標籤的按鈕會告訴使用者他們也可以說的語音命令。 例如, 當查看2D 應用程式時, 使用者可以在應用程式行中說出他們看到的「調整」命令, 以調整應用程式在世界中的位置。

![查看2D 應用程式或全息影像時, 使用者可以說出他們在應用程式行中看到的「調整」命令, 以調整應用程式在世界中的位置。](images/microphone-600px.png)

當應用程式遵循此規則時, 使用者可以輕鬆地瞭解如何控制系統。 為了強調此動作, 當您在按鈕上撥雲見日時, 您會看到一個「聲音停留」工具提示, 如果按鈕已啟用語音, 則會在一秒後出現, 並顯示要說出的命令來「按」。

![查看它, 假設命令出現在按鈕下方](images/voice-seeitsayit-600px.png)<br>
*「看起來」命令會出現在按鈕下方*

## <a name="voice-commands-for-fast-hologram-manipulation"></a>快速全息影像操作的語音命令

此外, 您也可以在撥雲見日的全息圖中, 使用一些語音命令來快速執行操作工作。 這些語音命令適用于2D 應用程式以及您放在世界中的3D 物件。

**全息影像操作命令**
* 臉部我
* 較大 |增加
* 較小

## <a name="dictation"></a>聽寫

語音聽寫可以更有效率地在應用程式中輸入文字, 而不是鍵入[空中](gestures.md#air-tap)。 這可以大幅加速輸入, 讓使用者的工作更少。

![語音聽寫一開始會選取 [麥克風] 按鈕](images/micbuttonfordictation.png)<br>
*語音聽寫一開始會選取鍵盤上的 [麥克風] 按鈕*

當全像攝影鍵盤在使用中時, 您可以切換到聽寫模式, 而不是輸入。 選取文字輸入方塊旁邊的麥克風以開始使用。

## <a name="communication"></a>通訊

對於想要利用 HoloLens 所提供之自訂音訊輸入處理選項的應用程式, 請務必瞭解您的應用程式可以使用的各種[音訊串流類別](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx)。 Windows 10 支援數種不同的串流類別和 HoloLens, 利用其中三種來啟用自訂處理, 以優化專為語音、通訊及其他可用於環境音訊的麥克風音訊品質capture (亦即「攝影機」) 案例。
* AudioCategory_Communications 串流類別是針對呼叫品質和旁白案例自訂, 並為用戶端提供使用者語音的 Riff-16khz-16bit-mono-pcm 24bit mono 音訊串流
* [AudioCategory_Speech stream] 類別是針對 HoloLens (Windows) 語音引擎自訂, 並提供該使用者語音的 Riff-16khz-16bit-mono-pcm 24bit mono 串流。 如有需要, 可由協力廠商語音引擎使用此類別。
* [AudioCategory_Other stream] 類別是針對環境環境音訊錄製而自訂, 並提供用戶端 48kHz 24 位身歷聲音訊串流。

所有此音訊處理都是硬體加速的, 這表示在 HoloLens CPU 上進行相同的處理時, 這些功能的耗電量會少很多。 避免在 CPU 上執行其他音訊輸入處理, 以將系統電池壽命最大化, 並利用內建的卸載音訊輸入處理。

## <a name="troubleshooting"></a>疑難排解

如果您在使用「選取」和「嘿 Cortana」時遇到任何問題, 請嘗試移到更好的空間、離開雜訊來源, 或說出更大的聲音。 目前, 所有的 HoloLens 語音辨識都是針對美國英文的原生喇叭進行微調與優化。

對於 Windows Mixed Reality Developer Edition 版本 2017, 在初始 HMD 連線之後, 音訊端點管理邏輯會正常執行 (永遠) 到電腦桌面。 在經過 WMR OOBE 之後, 第一次登出/進入事件之前, 使用者可能會遇到各種音訊功能問題, 範圍從沒有音訊到音訊切換, 這取決於第一次連線 HMD 之前設定系統的方式。

## <a name="see-also"></a>另請參閱
* [DirectX 中的語音輸入](voice-input-in-directx.md)
* [Unity 中的語音輸入](voice-input-in-unity.md)
* [MR Input 212：語音](holograms-212.md)
