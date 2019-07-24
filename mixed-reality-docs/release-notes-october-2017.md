---
title: 版本資訊-2017 年10月
description: Windows 10 秋季建立者更新的 windows Mixed Reality 版本資訊 (2017 年10月)。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 版本資訊, 版本, windows 10, 組建, rs3, os
ms.openlocfilehash: 7274dcf1db449fa35981eb72192fea9873fcc90a
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524094"
---
# <a name="release-notes---october-2017"></a>版本資訊-2017 年10月

Windows 歡迎畫面 Mixed Reality! 新版 **[Windows 10 Fall Creators Update](https://blogs.windows.com/windowsexperience/2017/10/17/whats-new-windows-10-fall-creators-update/)** 導入了新的支援 [Windows Mixed Reality 沈浸式耳機](immersive-headset-hardware-details.md)並[動作控制站](motion-controllers.md)，讓您得以探索新的環境，玩 VR 遊戲，並體驗沈浸式娛樂，當連接到[Windows Mixed Reality 相容電腦](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)。

Windows Mixed Reality 耳機和運動控制器的發行, 是大規模小組工作的高潮, 以及[Windows Mixed reality 平臺](mixed-reality.md)(包括[Microsoft HoloLens](hololens-hardware-details.md)) 的主要步驟。 雖然 HoloLens 並未收到 Windows 10 秋季建立者更新版本的更新, 但請注意, 在 HoloLens 上的工作尚未停止;我們將會提供許多學習和深入解析, 以在整個 Windows Mixed Reality 的最新工作中申請。 事實上, Windows Mixed Reality 沉浸式耳機和運動控制器也代表 HoloLens 開發的絕佳進入點, 因為相同的 Api、工具和概念也適用于兩者。

若要更新每個裝置的最新版本, 請開啟 [**設定**] 應用程式, 移至 [**更新 & 安全性**], 然後選取 [**檢查更新**] 按鈕。 在 Windows 10 電腦上, 您也可以使用[windows media 建立工具](https://www.microsoft.com/software-download/windows10), 手動安裝 Windows 10 秋季建立者更新。

 **Desktop 的最新版本:** Windows 10 Desktop 2017 年10月 (**10.0.16299.15**, Windows 10 秋季建立者更新)<br>
 **HoloLens 的最新版本:** [2016 年8月的 Windows 10](release-notes-august-2016.md)全像攝影(**10.0.14393.0**, Windows 10 年度更新版)

>[!VIDEO https://www.youtube.com/embed/YBcLy1lkegg]

## <a name="introducing-windows-mixed-reality"></a>Windows Mixed Reality 簡介

Windows 10 秋季建立者更新正式引進了 Windows Mixed Reality 耳機和運動控制器的支援, 以及讓 Windows 10 成為世界的第一個空間作業系統。 重點如下:
* **[各種耳機](https://blogs.windows.com/windowsexperience/2017/10/03/how-to-pre-order-your-windows-mixed-reality-headset/)** -Windows Mixed Reality 讓合作夥伴能夠提供各種耳機, 從 $399 美元起與運動控制器配套。
* **[運動控制器](motion-controllers.md)** -Windows Mixed Reality 運動控制器透過藍牙與您的電腦進行無線配對, 並提供六個自由度的追蹤、大量輸入方法和 IMUs。
* **[輕鬆的設定和可攜性](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)** -設定並在10分鐘內開始使用。 沉浸式耳機使用向外追蹤來追蹤您的移動和您的動作控制器, 並具有六個自由度。 不需要外部相機或燈塔標記!
* **[支援更廣泛的電腦](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)** -Windows Mixed Reality 可讓更多人體驗桌面 VR, 而不支援從 $499 美元開始的選取整合式圖形配接器和電腦。
* **[Windows Mixed Reality 首頁](navigating-the-windows-mixed-reality-home.md)** -全球的第一個空間作業系統提供熟悉的家庭環境, 讓您使用2d 應用程式進行多工處理、啟動 VR 遊戲和應用程式, 以及放置裝飾的全息影像。
* **[Microsoft Store 中的絕佳的 VR 遊戲和應用程式](https://www.microsoft.com/store/collections/MR-All-ImmersiveContent/)** -從像是 Hulu VR 和 360 video 的沉浸式娛樂, 乃至 SUPERHOT VR 和亞利桑那州的神奇遊戲, Microsoft Store 都有各種內容可在 Windows Mixed Reality 中體驗。
* **[SteamVR 早期存取](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)** -Windows 10 秋季建立者更新可讓您使用 Windows mixed reality 耳機和控制器來播放 SteamVR 標題, 使 VR 標題的最大類別目錄可供 Windows mixed reality 使用者使用。

## <a name="known-issues"></a>已知問題

我們致力於提供絕佳的 Windows Mixed Reality 經驗, 但我們仍在追蹤一些已知問題。 如果您發現其他人, 請[提供意見反應給我們](give-us-feedback.md)。

### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>Windows Mixed Reality 首頁中的桌面應用程式
* 剪取工具無法在桌面應用程式中運作。
* 桌面應用程式不會在重新開機時保存設定。
* 如果您在桌面上使用混合現實入口網站預覽, 在 Windows Mixed Reality 首頁中開啟桌面應用程式時, 可能會注意到無限的鏡像效果。 
* 執行桌面應用程式可能會造成非 Ultra Windows Mixed Reality 電腦上的效能問題;不建議使用此選項。  
* 桌面應用程式可能會自動啟動, 因為桌面上的不可見視窗有焦點。 
* 桌面使用者帳戶控制提示會使耳機顯示黑色, 直到提示完成為止。

### <a name="windows-mixed-reality-setup"></a>Windows Mixed Reality 設定
* 當設定具有耳機連線的 Windows 時, 您的電腦監視器可能會空白。 拔下頭戴式裝置以啟用電腦監視器的輸出, 以完成 Windows 安裝程式。
* 建立界限時, 追蹤可能會失敗。 若是如此, 請再試一次, 因為系統會在一段時間後深入瞭解您的空間。
* 如果您在 Windows Mixed Reality 設定期間開啟或關閉 Cortana, 此變更將會套用至您的桌面 Cortana 設定。
* 如果您沒有連接耳機, 當您第一次造訪 Windows Mixed Reality 首頁時, 可能會錯過其他秘訣。
* Bluetooth 耳機可能會導致與移動控制器的干擾。 我們建議在 Windows Mixed Reality 會話期間取消配對或關閉藍牙控制器。

### <a name="games-and-apps-from-windows-store"></a>Windows Store 的遊戲和應用程式
* 有些以圖形化的遊戲 (例如 Forza Motorsports 6) 可能會在 Windows Mixed Reality 內播放時, 造成效能問題在支援較少的電腦上。

### <a name="audio"></a>音訊
* 如先前所述, 藍牙音訊周邊無法與 Windows Mixed Reality 語音和空間音效體驗搭配運作。 它們也可能會對您的動作控制器體驗造成負面影響。 我們不建議在 Windows Mixed Reality 中使用藍牙音訊耳機。
* 當裝置未磨損時, 您無法使用連接到 (或部分) 耳機的音訊裝置來播放音訊。 如果您只有一個音訊耳機, 您可能會想要將音訊耳機連接到主機電腦, 而不是耳機。 若是如此, 您必須關閉 [**設定** > ] [**混合現實** > ] [**音訊和語音**] 中的 [切換到耳機音訊]。
* 某些應用程式 (包括許多透過 SteamVR 所啟動的) 可能會在您啟動或停止混合現實入口網站時, 因為音訊裝置變更而失去音訊或停止回應。 在您開啟混合現實入口網站應用程式以更正此情況之後, 請重新開機應用程式。
* 如果您在使用 Windows Mixed Reality 耳機之前, 已在您的主機電腦上啟用 Cortana, 您可能會遺失在 Windows Mixed Reality 首頁上所放置的應用程式所套用的空間音效模擬。 解決的辦法是在連接到您電腦的所有音訊裝置上啟用「Windows Sonic for 耳機」, 甚至是您的耳機連線音訊裝置:
   1. 以滑鼠左鍵按一下桌面工作列上的 [喇叭] 圖示, 然後選取 [從音訊裝置清單]。
   2. 以滑鼠右鍵按一下桌面工作列上的 [喇叭] 圖示, 然後在 [說話者設定] 功能表中選取 [Windows Sonic for 耳機]。
   3. 針對所有音訊裝置 (端點) 重複上述步驟。
>[!NOTE]
> - 由於連接到頭戴式裝置的耳機/喇叭不會出現, 除非您佩戴它, 否則您必須在 Windows Mixed Reality 首頁的桌面應用程式視窗中執行此動作, 才能將這項設定套用到連接到耳機的音訊裝置 (或整合式進入頭戴式裝置。
> - 另一個選項是在啟動 Windows Mixed Reality 之前, 關閉桌面上**設定** >  **cortana**中的「讓 cortana 回應您的 cortana」。

* 當另一個多媒體 USB 裝置 (例如網路凸輪) 與 Windows Mixed Reality 耳機共用相同的 USB 集線器 (外部或在您的電腦內) 時, 在罕見的情況下, 耳機的音訊插座/耳機可能會有一聲聲或完全沒有音訊。 您可以將您的耳機修正為 USB 埠, 而該埠不會與其他裝置共用相同的中樞, 或中斷連線/停用其他 USB 多媒體裝置。
* 在極罕見的情況下, 主機電腦的 USB 集線器無法提供足夠的電源給 Windows Mixed Reality 頭戴式裝置, 而您可能會注意到連接到耳機的耳機突然激增。

### <a name="speech"></a>語音
* Cortana 可能無法播放她的音訊提示, 以接聽/思考和命令的音訊回應。
* 中國與日本市場的 cortana 在使用時, 不會正確地顯示 Cortana circle 底下的文字。
* Cortana 在混合現實入口網站會話中第一次叫用時, 可能會變慢。 若要解決此情況, 請在 [**cortana**  > **與 cortana 交談**] 的 [**設定** > ] 下, 確定已啟用 [讓 cortana 回應您的 cortana]。
* 在非 Windows Mixed Reality Ultra 電腦的電腦上, Cortana 的執行速度可能較慢。
* 當您的系統鍵盤設定為與 Windows Mixed Reality 中的 UI 語言不同的語言時, 在 Windows Mixed Reality 中使用鍵盤上的聽寫將會導致錯誤對話方塊, 表示聽寫無法運作, 因為沒有 Wi-fi 連線。 若要修正此問題, 請直接確定系統鍵盤語言符合 Windows Mixed Reality UI 語言。
* 西班牙無法正確辨識為 Windows Mixed Reality 啟用語音的市場。

### <a name="holograms"></a>全息
* 如果您在 Windows Mixed Reality 首頁中放置了大量的全息影像, 有些可能會在您進行流覽時消失並重新出現。 若要避免這種情況, 請在 Windows Mixed Reality 首頁的該區域中移除部分全息影像。

### <a name="motion-controllers"></a>運動控制器
* 有時候, 如果您按一下 Edge 中的網頁, 內容將會縮放, 而不是按一下。
* 有時當您按一下 Edge 中的連結時, 選取專案將無法使用。

## <a name="prior-release-notes"></a>先前的版本資訊
* [版本資訊 - 2016 年 8 月](release-notes-august-2016.md)
* [版本資訊 - 2016 年 5 月](release-notes-may-2016.md)
* [版本資訊 - 2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>另請參閱
* [沉浸式耳機支援 (外部連結)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [HoloLens 的已知問題](hololens-known-issues.md)
* [安裝工具](install-the-tools.md)
* [提供意見反應給我們](give-us-feedback.md)
