---
title: 版本資訊-2018 年10月
description: 適用于 Windows 10 2018 年10月更新的 HoloLens 和 Windows Mixed Reality 版本資訊 (也稱為 RS5)。
author: mattzmsft
ms.author: mazeller
ms.date: 10/02/2018
ms.topic: article
keywords: 版本資訊, 版本, windows 10, 組建, rs5, os
ms.openlocfilehash: 794050910be40e7f98d0a1f67c2e1cf6963305dd
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524241"
---
# <a name="release-notes---october-2018"></a>版本資訊-2018 年10月

**[Windows 10 2018 年10月更新](https://blogs.windows.com/windowsexperience/2018/10/02/find-out-whats-new-in-windows-and-office-in-october/)** (也稱為 RS5) 包含與電腦連線的 HoloLens 和 Windows Mixed Reality 沉浸式耳機的新功能。 

若要更新至 HoloLens 或 PC 上的最新版本 (適用于 Windows Mixed Reality 沉浸式 (VR) 耳機), 請開啟 [**設定**] 應用程式, 移至 [**更新 & 安全性**], 然後選取 [**檢查更新**] 按鈕。 在 Windows 10 電腦上, 您也可以使用[windows media 建立工具](https://www.microsoft.com/software-download/windows10), 手動安裝 windows 10 2018 年10月更新。

**Desktop 的最新版本:** Windows 10 2018 年10月更新 (**10.0.17763.107**)<br>
**HoloLens 的最新版本:** Windows 10 2018 年10月更新 (**10.0.17763.134**)<br>

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Windows Mixed Reality 沉浸式耳機的新功能

Windows 10 2018 年10月更新包含許多在桌上型電腦上使用 Windows Mixed Reality 沉浸 (VR) 耳機的改良功能。

### <a name="for-everyone"></a>適用于每個人

* **混合現實**的解決方式-在現實世界中開啟入口網站以尋找您的鍵盤、查看附近的某人, 或查看您的環境, 而不需要移除您的頭戴式裝置! 您可以從 [開始] 功能表開啟 [混合現實], 方法是在您的動作控制器上按 Windows + [抓取], 或說出 [開/關]。 以您想要查看的方向來指向您的控制器, 例如使用深色的一個。

    ![混合現實的](images/mr-flashlight.png)

* **新的應用程式和在混合現實首頁中啟動內容的方式**
    * 如果您使用[Windows Mixed Reality 進行 SteamVR](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality), 您的 SteamVR 標題現在會顯示在 [開始] 功能表中, 而適用于每個的應用程式啟動器會放在混合現實首頁。
    
        ![SteamVR 應用程式啟動器](images/steamvr-launchers.png)
        
    * 新的*360*影片應用程式, 可用於探索定期策劃的360度影片選擇。
    * 新的*WebVR 展示*應用程式, 可用於探索定期策劃的 WebVR 經驗選擇。
    * 第一次的 Windows Mixed Reality 客戶將進入 Cliff 房屋, 併發現它已針對一些我最愛的沉浸式應用程式和 Microsoft Store 的遊戲, 預先填入3D 應用程式啟動器。
    * Microsoft Edge windows 現在包含 [*共用*] 按鈕。
* [**快速動作] 功能表**-從沉浸式混合現實應用程式中, 您可以按 [Windows] 按鈕存取新的 [快速動作] 功能表, 輕鬆存取 [ *SteamVR] 功能表*、 [*相片/影片*]、[下] 和 [*首頁*]。
* **支援死忠電腦**-Windows Mixed Reality 沉浸 (VR) 耳機會在死忠電腦上執行, 而在安裝程式完成之後, 不需要顯示模擬器。
* **新的音訊功能**-您現在可以將音訊從 Windows Mixed Reality 體驗鏡像到耳機中的音訊插頭 (或耳機) *, 以及*連接到您電腦的音訊裝置 (如外部喇叭)。 我們也在頭戴式裝置的顯示器中新增了音量層級的視覺指標。
* **其他改良功能**
    * 混合現實入口網站更新現在透過 Microsoft Store 提供, 可讓您在主要 Windows 版本之間進行更快速的更新。 請注意, 這只適用于桌面應用程式, 而 Windows Mixed Reality 耳機體驗仍然會隨著作業系統更新。 
    * 當耳機進入睡眠狀態時, Windows Mixed Reality 應用程式會暫停而不是終止 (直到混合現實入口網站關閉為止)。
    
### <a name="for-developers"></a>適用於開發人員

* **[Qr 代碼追蹤](qr-code-tracking.md)** -在您的混合現實應用程式中啟用 QR 代碼追蹤, 讓 Windows mixed reality 沉浸式 (VR) 耳機能夠掃描 QR 代碼, 並回報給感興趣的應用程式。
* **沉浸式應用程式的硬體 DRM 支援**-開發人員現在可以要求硬體保護的 backbuffer 紋理 (如果顯示硬體支援的話), 讓應用程式可以從來源 (例如 PlayReady) 使用受硬體保護的內容。
* 將 **[混合現實 CAPTURE Ui 整合到沉浸式應用程式中](mixed-reality-capture-for-developers.md#integrating-mrc-functionality-from-within-your-app)** -開發人員可以使用內建的 Windows[攝影機 capture UI](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) , 只需要幾行程式碼, 就能將混合現實 capture 整合到自己的應用程式中。

## <a name="new-features-for-hololens"></a>HoloLens 的新功能

Windows 10 2018 年10月更新已公開提供給所有 HoloLens 客戶, 其中包含一些改良功能, 例如:

### <a name="for-everyone"></a>適用于每個人

* [**快速動作] 功能表**-從沉浸式混合現實應用程式中, 您可以按 Windows 按鈕存取新的 [快速動作] 功能表, 並輕鬆地*開始錄製影片*、*拍攝圖片*、*混合現實首頁*、*變更[磁片*區 *] 和 [連線]* 。
* **從 [開始] 或 [快速動作] 功能表啟動/停止影片捕捉**-如果您從 [開始] 功能表或 [快速動作] 功能表啟動 [影片捕捉], 就可以從相同的位置停止錄製。 (別忘了, 您也可以使用語音命令來執行此動作)。
* 將**專案加入支援 miracast 的裝置**-將您的 HoloLens 內容投影到附近的表面裝置或電視/監視器 (如果使用支援 Miracast 的顯示或介面卡)。
* **新通知**-在 HoloLens 上查看和回應通知, 就像您在電腦上所做的一樣。  
* **沉浸式混合現實應用程式中的有用**重迭-使用沉浸式混合現實應用程式時, 您現在會看到重迭, 例如鍵盤、對話方塊、檔案選擇器等等。
* **磁片區變更的視覺指示器**-當您使用 HoloLens 上的 [音量向上/向下] 按鈕時, 您會在耳機中看到音量層級的視覺指示器。
* **裝置開機的新視覺效果**-在開機程式期間新增了載入指示器, 以提供系統正在載入的視覺回應。
* **鄰近分享**-Windows 鄰近分享體驗可讓您與附近的 windows 裝置共用捕捉。  
* **從 Microsoft Edge 共用**-microsoft edge 現在包含 [*共用*] 按鈕。 

### <a name="for-developers"></a>適用於開發人員

* 將 **[混合現實 CAPTURE Ui 整合到沉浸式應用程式中](mixed-reality-capture-for-developers.md#integrating-mrc-functionality-from-within-your-app)** -開發人員可以使用內建的 Windows[攝影機 capture UI](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) , 只需要幾行程式碼, 就能將混合現實 capture 整合到自己的應用程式中。

### <a name="for-commercial-customers"></a>適用于商業客戶

* **啟用安裝後**布建-您現在可以使用設定隨時套用執行時間布建套件。
* **指派 Azure AD 群組的存取權**-您現在可以使用 Azure AD 群組來設定 Windows 指派的存取權, 以設定單一或多個應用程式的 kiosk 設定。
* **在設定檔交換器上從登入畫面進行 pin 登入**-pin 登入現在可供登入畫面上的 [其他使用者] 使用。 
* **透過 Mdm 讀取裝置硬體資訊**-IT 系統管理員可以在其 MDM 主控台中查看和追蹤裝置序號的 HoloLens。
* **透過 mdm (重新命名) 設定 hololens 裝置名稱**-IT 系統管理員可以在其 MDM 主控台中查看和重新命名 hololens 裝置。

### <a name="for-international-customers"></a>適用于國際客戶

您現在可以將 HoloLens 與當地語系化的使用者介面搭配使用, 以進行簡體中文或日文, 包括當地語系化的拼音鍵盤、聽寫、文字轉換語音 (TTS) 和語音命令。

## <a name="known-issues"></a>已知問題

我們致力於提供絕佳的 Windows Mixed Reality 經驗, 但我們仍在追蹤一些已知問題。 如果您發現其他人, 請[提供意見反應給我們](https://docs.microsoft.com/windows/mixed-reality/give-us-feedback)。

### <a name="hololens"></a>HoloLens
 
#### <a name="after-update"></a>更新之後
在您的 HoloLens 上使用 Windows 10 2018 年10月更新時, 您可能會注意到下列問題:
* **從通知啟動時, 應用程式可能會在登入迴圈中結束**–某些需要登入的應用程式可能會在從通知啟動時以無限的登入迴圈結束。 例如, 從 Microsoft Store 安裝 Microsoft 公司入口網站應用程式, 並從安裝完成通知啟動之後, 就會發生這種情況。
* **應用程式登入頁面可使用空白頁面完成**–在某些情況下, 當登入提示顯示您的應用程式時, 登入頁面不會關閉, 而是會顯示空白 (黑色) 頁面。 您可以關閉空白頁面, 或將它移動以找出下的應用程式。 例如, 從 [設定] 應用程式進行 MDM 註冊期間的登入時, 可能會發生這種情況。 

## <a name="provide-feedback-and-report-issues"></a>提供意見反應和報告問題

請[在 HoloLens 或 Windows 10 電腦上使用意見反應中樞應用程式](give-us-feedback.md), 以提供意見反應並回報問題。 使用意見反應中樞可確保包含所有必要的診斷資訊, 以協助我們的工程師快速地進行分析並解決問題。

>[!NOTE]
>請務必接受提示, 詢問您是否希望意見反應中樞存取您的 [檔] 資料夾 (出現提示時選取 **[是]** )。

## <a name="prior-release-notes"></a>先前的版本資訊

* [版本資訊 - 2018 年 4 月](release-notes-april-2018.md)
* [版本資訊 - 2017 年 10 月](release-notes-october-2017.md)
* [版本資訊 - 2016 年 8 月](release-notes-august-2016.md)
* [版本資訊 - 2016 年 5 月](release-notes-may-2016.md)
* [版本資訊 - 2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>另請參閱
* [沉浸式耳機支援 (外部連結)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [HoloLens 支援 (外部連結)](https://support.microsoft.com/products/hololens)
* [安裝工具](install-the-tools.md)
* [提供意見反應給我們](give-us-feedback.md)

