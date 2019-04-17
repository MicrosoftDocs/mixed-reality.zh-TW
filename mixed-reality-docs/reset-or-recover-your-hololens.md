---
title: 重設或復原您的 HoloLens
description: 基本和進階重新啟動或重設您的 HoloLens 的指示。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 作法，請重新啟動、 重設、 復原，硬重設、 軟重設、 電源循環，HoloLens，關閉
ms.openlocfilehash: abf71a5f122b1c6f800bf970f51da11a34be956b
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591764"
---
# <a name="reset-or-recover-your-hololens"></a>重設或復原您的 HoloLens

如果您遇到您 HoloLens，您可能想要嘗試重新啟動的問題，請重設，或甚至重新 flash 與裝置復原。 本文件將引導您完成連續的建議步驟。

## <a name="perform-a-device-reboot"></a>執行裝置重新開機

如果您的 HoloLens 發生問題，或沒有回應，則先試著透過其中一種下列方法。

### <a name="perform-a-safe-reboot-via-cortana"></a>執行安全的重新開機，透過 Cortana

若要重新啟動 HoloLens 最安全的方法是透過 Cortana。 這通常是絕佳的第一個步驟時遇到的問題與 HoloLens:
1. 將放在您的裝置
2. 請確定開機、 登入的使用者和裝置未在等待密碼來解除鎖定。
3. 說 「 嘿 Cortana，重新啟動 」 或 「 嘿 Cortana，重新啟動。 」
4. 當她認可她將會要求您確認。 等候另一個則用於後完成她的問題，表示她用來接聽以您要播放的音效，然後說出"Yes"。
5. 裝置會立即重新開機/重新啟動。

### <a name="perform-a-safe-reboot-via-windows-device-portal"></a>執行 Windows Device Portal 透過安全的重新開機

如果上述無法運作，您可以嘗試重新啟動裝置，透過[Windows Device Portal](using-the-windows-device-portal.md)。 在右上角沒有重新開機/關機選項的裝置。

### <a name="perform-a-safe-reboot-via-the-power-button"></a>執行 [電源] 按鈕透過安全的重新開機

如果您仍無法重新啟動您的裝置，您可以嘗試發出透過 [電源] 按鈕重新開機：
1. 按住電源按鈕的 5 秒
   1. 1 秒之後, 您會看到所有 5 個 Led 照亮，然後慢慢關閉由右至左
   2. 在 5 秒之後, 所有的 Led 將會關閉，表示已成功發出關機命令
   3. 請注意，務必要停止所有的 Led 已關閉後立即按下按鈕
2. 等候 1 分鐘才能完全成功關閉。 請注意，關閉可能仍是進行中，即使會顯示已關閉
3. 透過按住電源按鈕 1 秒再次在裝置上的電源

### <a name="perform-an-unsafe-forced-reboot"></a>執行不安全的強制重新開機

如果上述方法都能夠成功地重新啟動您的裝置，您可以強制重新開機。 請注意，這個方法相當於從 HoloLens，提取電池，因此是危險的作業，而這可能導致您的裝置處於損毀的狀態。 

>[!WARNING]
>這是可能會造成損害的方法，且應該僅用於萬一上述的方法，沒有任何作用。

1. 按住不放在至少 10 秒的時間的電源按鈕
   * 可以在按住按鈕超過 10 秒
   * 它可以放心地忽略任何 LED 活動
2. 放開按鈕，等候 2-3 秒
3. 透過按住電源按鈕 1 秒再次在裝置上的電源

## <a name="reset-the-device-to-a-factory-clean-state"></a>將裝置重設為原廠的初始狀態

如果您 HoloLens 重新開機之後仍發生問題，您可以嘗試重設為原廠的初始狀態。 如果您重設您的裝置，所有您個人資料、 應用程式和設定將被清除。 重設只會安裝最新的 Windows 全像攝影版安裝的版本，您必須重做所有的初始化步驟 (校正、 連線到 WiFi、 建立使用者帳戶、 下載應用程式等等.)。
1. 啟動**設定**應用程式]-> [**更新** -> **重設**
2. 選取 **重設裝置**選項，然後讀取 確認 對話方塊
3. 如果您同意將裝置重設，裝置會重新啟動，並顯示一組旋轉 gears 一個進度列
4. 等候約 30 分鐘的時間才能完成此程序
5. 重設會完成，而且裝置會重新開機到全新體驗

## <a name="perform-a-full-device-recovery"></a>執行完整裝置復原

如果您的裝置是執行上述選項之後,**仍然**凍結，沒有回應，或未發生更新或軟體問題可以使用 Windows Device Recovery Tool 加以復原。 復原您的裝置是類似重設，因為它將會清除所有的使用者內容，在裝置上，包括應用程式、 遊戲、 相片、 使用者帳戶等。 可能的話，請備份您想要保留的任何資訊。

若要完全復原您的 HoloLens:
1. 中斷您的電腦上的所有電話和 Windows 裝置
2. 安裝並啟動[Windows Device Recovery Tool](https://support.microsoft.com/help/12379/windows-10-mobile-device-recovery-tool-faq) (WDRT) 在您的電腦上
3. 它隨附您電腦使用 micro USB 纜線連接您 HoloLens
   * 請注意，並非所有的 USB 纜線與眾不同之處。 即使您已使用另一個的纜線已成功，此流程會公開其中纜線可能沒那麼好的新狀態。 您 HoloLens 隨附的一個是最佳且最並經過充分測試的選項
4. 如果此工具會自動偵測您的裝置會顯示 HoloLens 圖格。 按一下它，然後遵循指示完成程序

>[!NOTE]
>WDRT 可能復原較舊版本的 Windows 全像攝影版; 您的裝置您可能需要安裝更新之後閃爍

如果無法自動偵測您的裝置，請嘗試下列工具：
1. 重新啟動您的電腦和重試一次 （這會修正大部分的問題）
2. 按一下 [**偵測不到我的裝置] 按鈕**，選擇**Microsoft HoloLens**，並遵循螢幕上指示的其餘部分
