---
title: 語音輸入
description: 語音輸入是 HoloLens 與 Windows Mixed Reality 沈浸式耳機的核心輸入。 語音可以用於命令、 聽寫、 Cortana 和更多功能。
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: ggv、 語音、 cortana、 語音、 輸入
ms.openlocfilehash: e21310b940e4a4c3019f61edea695b452e74ab62
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829955"
---
# <a name="voice-input"></a>語音輸入

語音是三個索引鍵形式的輸入上的 HoloLens。 它可讓您直接命令而不需要使用的 雷射[筆勢](gestures.md)。 您只要[視線](gaze.md)在全像並將您的命令。 語音輸入可以是以自然的方式，向您的意圖。 語音很特別適合周遊複雜的介面，因為它可讓使用者透過巢狀以一個命令的功能表剪下。

語音輸入由[相同的引擎](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx)語音支援在所有其他通用 Windows 應用程式。

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
        <td><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沈浸式耳機</strong></a></td>
    </tr>
     <tr>
        <td>語音輸入</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ （與麥克風）</td>
    </tr>
</table>

## <a name="the-select-command"></a>「 Select 」 命令

即使沒有特別將語音支援新增至您的應用程式中，您的使用者可以啟用全像投影，只要說 「 選取 」。 此行為與相同[空中點選](gestures.md#air-tap)HoloLens，在按下 [選取] 按鈕上[HoloLens clicker](hardware-accessories.md#hololens-clicker)，或按下上的觸發程序[Windows Mixed Reality 動作控制器](motion-controllers.md). 您會聽到聲音，請參閱 「 select 」 與工具提示會顯示為確認。 因此永遠都是可供您肯定地說隨時具有最小電池壽命的影響，即使在您這端雙手 「 選取 」 會啟用低電源關鍵字偵測演算法。

> [!NOTE]
> HoloLens 2 的特定的詳細指引[即將推出](index.md#news-and-notes)。

![輸入 「 select 」 用於選取的語音命令](images/kma-voice-select-00170-800px.png)<br>
*輸入 「 select 」 用於選取的語音命令*

## <a name="hey-cortana"></a>嗨 Cortana

您也可以說 「 嘿 Cortana 」，以隨時顯示 Cortana。 您不必等待她出現繼續要求您的問題，或讓她指令-例如，嘗試說: 「 嘿 Cortana 什麼是天氣？ 」 為單一的句子。 如需 Cortana 和用途的詳細資訊，只要問她 ！ 說出 「 嘿 Cortana 如何我嗎？ 」 她會提取的工作及建議的命令清單。 如果您已經在 Cortana 應用程式中您也可以按一下**嗎？** 在資訊看板，調出這個相同的功能表上的圖示。

**HoloLens 特有的命令**
* 「我可以說什麼？」
* 「 移首頁 」 或 「 移至 開始 「-而不是[bloom](gestures.md#bloom)以前往[[開始] 功能表](navigating-the-windows-mixed-reality-home.md#start-menu)
* 「 啟動<app>"
* 「 移動<app>這裡 」
* 「 拍照"
* [開始錄製]
* [停止錄製]
* "Increase 亮度"
* "Decrease 亮度"
* "Increase 磁碟區 」
* "Decrease 磁碟區 」
* 「 靜音 」 或者 「 取消靜音 」
* 「 關閉裝置 」
* [重新啟動裝置]
* [執行進入睡眠狀態]
* 「 什麼時候是什麼？ 」
* 「 還剩多少電池？ 」
* 「 呼叫<contact>」 （需要 Skype 的 HoloLens）

## <a name="see-it-say-it"></a>"看到它，它說出"

HoloLens 具有"看到它，它說出"的模型，如語音輸入，其中上按鈕的標籤會告知使用者他們也可以說出哪些語音命令。 比方說，2D 應用程式時，使用者就可以說 「 調整 」 命令，這個命令會在他們會看到應用程式列中調整應用程式的世界中的位置。

![使用者在 2D 應用程式或全像檢視，可以說他們看到的應用程式列中調整應用程式的位置，世界中的 「 調整 」 命令](images/microphone-600px.png)

當應用程式遵循這項規則時，使用者可以輕鬆地了解要說來控制系統的內容。 為了強化，同時 gazing 按鈕時，您會看到 「 語音詳述 「 工具提示，如果按鈕是語音功能，而且會顯示 「 按 」 它與交談的命令，會出現在一秒後。

![看到它，例如其命令會出現下方的按鈕](images/voice-seeitsayit-600px.png)<br>
*「 請查看它說它的項目 」 命令會出現下方的按鈕*

## <a name="voice-commands-for-fast-hologram-manipulation"></a>快速的全像操作的語音命令

另外還有幾個的語音命令可以說出時 gazing 在全像圖，快速地進行操作工作。 這些語音命令處理 2D 應用程式，以及您已置於世界的 3D 物件。

**全像操作命令**
* 面臨我
* 較大 |增強
* 較小

## <a name="dictation"></a>聽寫

而不是型別與[空中點選](gestures.md#air-tap)，語音表示可能會將文字輸入至應用程式更有效率。 這可以大幅加速使用者更不費力的輸入。

![語音表示一開始會選取 [麥克風] 按鈕](images/micbuttonfordictation.png)<br>
*語音表示一開始會選取鍵盤上的 [麥克風] 按鈕*

每當全像攝影版的鍵盤時作用中，您可以切換到聽寫模式，而不是輸入。 選取旁邊的文字輸入方塊，若要開始麥克風。

## <a name="communication"></a>通訊

應用程式想要利用自訂的音訊輸入處理 HoloLens 所提供的選項，請務必了解各種[音訊資料流類別](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx)可取用您的應用程式。 若要啟用自訂的處理最佳化量身打造的語音、 通訊以及其他可用環境的環境音訊的麥克風音訊品質，所使用的三個 Windows 10 支援數個不同的資料流的類別和 HoloLens 讓擷取 （也就是 「 攝錄影機"） 的案例。
* AudioCategory_Communications 資料流類別自訂的通話品質和旁白的案例，並為用戶端提供使用者的語音 16 kHz 24 位元單聲道音訊資料流
* AudioCategory_Speech 資料流類別自訂的 HoloLens (Windows) 的語音引擎，並提供使用者的語音 16 kHz 24 位元 mono 資料流。 可以由第 3 個合作對象語音引擎使用這個類別，如有需要。
* AudioCategory_Other 資料流類別自訂的環境的環境音訊錄製，並提供 48 kHz 24 位元是立體聲音訊資料流中的用戶端。

所有此音訊處理將會啟用硬體加速表示功能清空少很多比如果相同的處理已完成 HoloLens CPU 上的電源。 避免執行其他處理延長系統電池壽命，並利用內建在 CPU 上的音訊輸入中，卸載音訊的輸入的處理。

## <a name="troubleshooting"></a>疑難排解

如果您遇到任何問題，使用 「 選取 」 和 「 嘿 Cortana 」，請嘗試將移至更安靜的空間，並開啟遠離干擾，或透過說話大聲點的來源。 在此階段中，是調整 HoloLens 上所有的語音辨識，並將其最佳化是專為母語的英文 （美國） 中。

Windows Mixed Reality Developer Edition 版本 2017年中，音訊的端點管理邏輯將會正常運作 （永遠） 之後登入並回復在電腦桌面上初始 HMD 連接之後。 之前 out/上課 WMR OOBE 後的事件中的第一次登，使用者可能會遇到各種舉凡根據系統的設定方式的第一次連接 HMD 之前切換不含音訊不含音訊的音訊功能問題。

## <a name="see-also"></a>另請參閱
* [DirectX 中的語音輸入](voice-input-in-directx.md)
* [Unity 中的語音輸入](voice-input-in-unity.md)
* [MR Input 212：語音](holograms-212.md)
