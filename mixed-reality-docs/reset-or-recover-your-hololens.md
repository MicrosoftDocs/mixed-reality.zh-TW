---
title: 重設或復原 HoloLens
description: 重新開機或重設 HoloLens 的基本和先進指示。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 操作說明、重新開機、重設、復原、硬重設、軟重設、電源週期、HoloLens、關機
ms.openlocfilehash: abf71a5f122b1c6f800bf970f51da11a34be956b
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524037"
---
# <a name="reset-or-recover-your-hololens"></a>重設或復原 HoloLens

如果您在 HoloLens 遇到問題, 您可能會想要嘗試重新開機、重設, 甚至是使用裝置復原來重新快閃。 本檔將會引導您連續完成建議的步驟。

## <a name="perform-a-device-reboot"></a>執行裝置重新開機

如果您的 HoloLens 發生問題或沒有回應, 請先嘗試透過下列其中一種方法將它重新開機。

### <a name="perform-a-safe-reboot-via-cortana"></a>透過 Cortana 執行安全重新開機

重新開機 HoloLens 的最安全方式是透過 Cortana。 這通常是在發生 HoloLens 問題時的絕佳第一個步驟:
1. 放在您的裝置上
2. 請確定其電源已開啟、使用者已登入, 且裝置未等待密碼解除鎖定。
3. 說「嗨, Cortana, 重新開機」或「嘿 Cortana, restart」。
4. 當她確認時, 會要求您進行確認。 等候第二個聲音在完成她的問題之後播放, 表示她正在接聽您, 然後說「是」。
5. 裝置現在將會重新開機/重新開機。

### <a name="perform-a-safe-reboot-via-windows-device-portal"></a>透過 Windows 裝置入口網站執行安全重新開機

如果上述無法解決問題, 您可以嘗試透過[Windows 裝置入口網站](using-the-windows-device-portal.md)重新開機裝置。 在右上角, 有一個選項可重新開機/關閉裝置。

### <a name="perform-a-safe-reboot-via-the-power-button"></a>透過 [電源] 按鈕執行安全重新開機

如果您仍然無法重新開機裝置, 您可以嘗試透過 [電源] 按鈕發出重新開機:
1. 按住電源按鈕5秒
   1. 1秒之後, 您會看到所有 5 Led 燈亮, 然後慢慢地從右至左關閉
   2. 5秒之後, 所有 Led 都會關閉, 表示已成功發出關機命令
   3. 請注意, 關閉所有 Led 後, 請務必立即停止按下按鈕
2. 請等候1分鐘, 讓關機完全成功。 請注意, 即使顯示器已關閉, 關機仍可能在進行中
3. 按住電源按鈕1秒, 再次開啟裝置電源

### <a name="perform-an-unsafe-forced-reboot"></a>執行不安全的強制重新開機

如果上述任何方法都無法成功地重新開機您的裝置, 您可以強制重新開機。 請注意, 此方法相當於從 HoloLens 取出電池, 因此, 這是一項危險的作業, 可能會讓您的裝置處於損毀狀態。 

>[!WARNING]
>這是可能有害的方法, 只有在上述方法都不適用的情況下才使用。

1. 按住電源按鈕至少10秒
   * 可以按住按鈕超過10秒
   * 可以放心地忽略任何 LED 活動
2. 放開按鈕並等候2-3 秒
3. 按住電源按鈕1秒, 再次開啟裝置電源

## <a name="reset-the-device-to-a-factory-clean-state"></a>將裝置重設為原廠清除狀態

如果您的 HoloLens 在重新開機後仍遇到問題, 您可以嘗試將它重設為原廠清除狀態。 如果您重設裝置, 將會清除您的所有個人資料、應用程式和設定。 重設只會安裝最新安裝的 Windows 全像版本, 您必須重做所有初始化步驟 (校準、連接到 WiFi、建立使用者帳戶、下載應用程式等)。
1. 啟動**設定**應用程式->**更新** -> **重設**
2. 選取 [**重設裝置**] 選項, 並閱讀確認對話方塊
3. 如果您同意重設裝置, 裝置將會重新開機, 並顯示一組旋轉的齒輪, 其中包含進度列
4. 等候大約30分鐘的時間, 讓此程式完成
5. 重設會完成, 且裝置將會重新開機為全新體驗

## <a name="perform-a-full-device-recovery"></a>執行完整的裝置復原

如果在執行上述選項之後, 您的裝置**仍**已凍結、沒有回應, 或發生更新或軟體問題, 您可以使用 Windows 裝置修復工具來復原它。 復原裝置的方式類似于將它重設, 因為它將會清除裝置上的所有使用者內容, 包括應用程式、遊戲、相片、使用者帳戶等等。 可能的話, 請備份您想要保留的任何資訊。

若要完整復原 HoloLens:
1. 中斷所有手機和 Windows 裝置與電腦的連線
2. 在您的電腦上安裝並啟動[Windows 裝置修復工具](https://support.microsoft.com/help/12379/windows-10-mobile-device-recovery-tool-faq)(WDRT)
3. 使用隨附的微 USB 纜線將 HoloLens 連接到您的電腦
   * 請注意, 並非所有的 USB 纜線都是以相等的建立。 即使您已成功使用另一條纜線, 此流程也會公開纜線可能無法執行的新狀態。 您的 HoloLens 隨附的是最佳且最妥善測試的選項
4. 如果此工具會自動偵測您的裝置, 則會顯示 HoloLens 磚。 按一下該檔案, 並遵循指示完成程式

>[!NOTE]
>WDRT 可能會將您的裝置復原到舊版的 Windows 全像攝影版;您可能需要在閃爍之後安裝更新

如果工具無法自動偵測您的裝置, 請嘗試下列步驟:
1. 重新開機您的電腦, 然後再試一次 (這會修正大部分的問題)
2. 按一下 [**未偵測到我的裝置] 按鈕**, 選擇 [ **Microsoft HoloLens**], 然後遵循畫面上的其餘指示
