---
title: 版本資訊-5 月2016
description: Windows 全像2016年5月版的 HoloLens 版本資訊更新。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, 版本資訊, os, 功能, 組建, 平臺
ms.openlocfilehash: bc4e09c36a3ab6643be1144873a624fc5ed66e37
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524554"
---
# <a name="release-notes---may-2016"></a>版本資訊-5 月2016

HoloLens 小組致力於提供您最新功能開發的更新, 以及透過 Windows 測試人員計畫的主要修正程式。 感謝您所有的建議, 我們會將您的意見反應提供給您。 請透過意見反應中樞、[開發人員論壇](https://forums.hololens.com) [ @HoloLens和 Twitter ](https://twitter.com/hololens), 繼續[提供意見](give-us-feedback.md)反應給我們。

**發行版本:** Windows 全像5月2016更新 (**10.0.14342.1016**)

>[!VIDEO https://www.youtube.com/embed/XM5OHHrOGqQ]

若要更新為目前的版本, 請開啟 [*設定*] 應用程式, 移至 [*更新 & 安全性*], 然後選取 [*檢查更新*] 按鈕。

## <a name="new-features"></a>新功能

* 您現在可以**同時在2d 視圖中執行最多三個應用程式**。 這可讓 HoloLens 中的多工使用案例無限。 在探索此航班的新功能時, 讓新的意見反應中樞具有探索」的清單。

  ![HoloLens 可以同時執行三個應用程式](images/img-3625-400px.jpg)<br>
  同時在2D 視圖中執行最多三個應用程式

* 我們已新增**語音命令**:
   * 請嘗試查看全像投影, 並說「臉部我」來旋轉
   * 藉由說出「大」或「較小」來變更其大小
   * 藉由說「嘿 Cortana, 將*應用程式名稱*移到這裡」來移動應用程式。
* 我們已**更輕鬆地在 HoloLens 上進行開發**。 您現在可以透過[Windows 裝置入口網站](using-the-windows-device-portal.md)流覽、上傳和下載檔案。 您可以存取 [檔] 資料夾、[圖片] 資料夾, 以及任何您透過 Visual Studio 側載或部署之應用程式的本機儲存體。
* **模擬器現在支援以 Microsoft 帳戶登入**, 就像您在實際的 HoloLens 上所做的一樣。 您可以從 [其他工具] 功能表 [> >] 加以啟用。
* **2D 應用程式現在會在觀賞全螢幕影片時隱藏應用程式行和游標**, 以避免干擾。 透過這種方式, 您的影片觀賞體驗在 HoloLens 上會更有樂趣。
* 您也可以**釘選相片, 而不需要您世界中的應用程式行**。

  ![針對2D 應用程式 (例如相片), 可以隱藏應用程式行](images/img-3626-400px.jpg)<br>
  應用程式行可針對具有2D 視圖的應用程式隱藏, 例如相片
  
* 檔案**選擇器**的運作方式就如同您在 HoloLens 上所預期的一樣。
* 已更新**Edge 瀏覽器**來對應與桌面和手機一致的使用者體驗。 我們在新視窗中啟用了多個瀏覽器實例、自訂 HoloLens 新索引標籤頁、索引標籤查看和開啟, 以及 power & 效能改進。
* **Groove 音樂**應用程式現在已在 HoloLens 上。 請造訪 store 進行下載, 然後在背景嘗試播放。
* 您可以輕鬆地自訂應用程式在世界中的相片順序。 只要按一下並拖曳中間垂直框線中的 circle, 即可嘗試在調整模式中**旋轉您的全息影像**。 您可能會注意到, 全息影像的**邊界方塊較緊密**, 以確保最大化的互動。 您也可以垂直調整所有平面應用程式的大小 (相片和全息影像應用程式除外)。

  ![將影像放在世界上之後, 可以旋轉全像投影](images/img-3627-400px.jpg)<br>
  將全息影像放在世界上之後旋轉

* 我們在此航班中做了許多**輸入改善**。 您可以將一般藍牙滑鼠連線到 HoloLens。 Clicker 已經過微調, 可讓您調整使用 clicker 移動全息影像的大小 &。 鍵盤的執行效果也比以往更好。
* 現在您只要按下音量並同時往下移動, 就可以採用**混合的現實圖片**。 您也可以將您混合現實的相片 & 影片分享到 Facebook、Twitter 和 YouTube。
* **混合現實**影片的記錄長度上限已增加到五分鐘。
* **相片應用程式**現在會從 OneDrive 串流影片, 而不需要在播放前下載整段影片。
* 我們已改善您**的全息影像在您離開時的位置**。 您也會看到重新連線至 Wi-fi 的選項, 並在 HoloLens 無法偵測到其所在位置時再試一次。
* 鍵盤具有改良的版面配置, 可讓您使用金鑰來輸入**電子郵件地址**, 以便您只需按一下就能進入最受歡迎的電子郵件網域。
* 在 OOBE 期間, 更快的**應用程式註冊**和**時間區域自動偵測**, 為您提供最佳的第一個使用者體驗。
* **儲存體感知**可讓您透過 [設定] 應用程式中的系統和應用程式, 來查看剩餘和已使用的磁碟空間。
* 我們已將「融合式意見反應」應用程式和內部中樞納入單一應用程式**意見反應中樞**, 這是可**提供意見**反應的「前往」工具、您喜愛的功能、不需要的功能, 或有可能更好的東西。 當您加入測試人員計畫時, 您可以隨時掌握**取得最新的 insider 新聞**、**評分組建**, 以及從意見反應中樞**探索」意見**反應。
* 我們也[發佈了已更新的 HoloLens 模擬器](install-the-tools.md)組建。
* 您的混合現實影片現在看起來較佳, 因為它是自動的**視頻穩定**。

## <a name="major-fixes"></a>主要修正

我們已修正空格會變慢或偵測不正確的全息圖空間問題。 我們已修正關機問題, 這可能會在關機期間繼續嘗試啟動 shell。

我們已修正問題
* 這會封鎖繼續 XAML 應用程式的功能。
* 當損毀時, 會留下黑色畫面和一些不規則線條。
* 使用某些應用程式時, 滾動有時會導致不正確的方向。
* 電源 Led 可能表示裝置仍開啟時處於關閉狀態。
* 從待命狀態繼續後, WiFi 可能會關閉。
* Xbox 身分識別提供者會提供玩家代號設定, 然後停滯在迴圈中。
* 在 OneDrive 檔案選擇器中選取下載的檔案時, Shell 偶爾會損毀。
* 按住連結, 有時會開啟一個新的已中斷索引標籤, 並開啟內容功能表。
* 其中 windows 裝置入口網站不允許從50到80的 IPD 調整

我們已修正相片的問題, 其中
* 影像偶爾會因為忽略 [EXIF 方向] 屬性而顯示 [旋轉]。
* 它可能會在已釘選的相片上啟動時損毀。
* 影片會在暫停後重新開機, 而不是從上次暫停的位置繼續。
* 共用影片的重新執行可能會在播放時共用。
* 混合現實捕捉記錄的開頭為 0.5-1 秒的僅音訊摘要。
* [同步處理] 按鈕會在初始 OneDrive 同步期間消失。

我們已修正設定的問題, 其中
* 環境變更時, 需要重新整理。
* 鍵盤上的 ' Enter ' 不會像在某些對話方塊中按一下 [下一步] 一樣。
* 很難得知 clicker 的配對何時失敗。
* 它可能會因為 WiFi 中斷連線和連線而變得沒有回應。

我們已修正 Cortana 的問題, 其中
* 它可能會停滯, 而無法顯示接聽 UI。
* 如果您對結束應用程式的要求可能是或否, 詢問「您的 Cortana, 我可以從獨佔模式應用程式取得哪些內容」會停滯。
* 如果您要求 Cortana 進入睡眠狀態, 然後繼續進行, Cortana 接聽 UI 就不會正確地繼續。
* 查詢「我連接到什麼網路？」 「我已連線嗎？」 當第一個網路設定檔回傳而沒有連線能力時, 可能會失敗。
* UI 旁邊在「接聽」, 但結束應用程式時, 會立即開始執行語音辨識。
* 在登出 Cortana 應用程式的情況下, 您將無法重新登入, 直到重新開機為止。
* 當混合現實 Capture UI 為作用中時, 不會啟動它。

我們已修正 Visual Studio 的問題, 其中
* 背景工作的調試失敗。
* 圖形偵錯工具中的框架分析無法正常執行。
* 除非您的專案 TargetPlatformVersion 設定為 10240, 否則 HoloLens 模擬器不會出現在 Visual Studio 的下拉式清單中。

## <a name="changes-from-previous-release"></a>先前版本的變更
* Cortana 命令 [您**好的 cortana], 重新開機裝置**無法運作。 使用者可以說**cortana、restart**或**你好的 cortana, 重新開機裝置**。
* 已從產品移除 Kiosk 模式。

## <a name="prior-release-notes"></a>先前的版本資訊
* [版本資訊 - 2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>另請參閱
* [HoloLens 的已知問題](hololens-known-issues.md)
* [安裝工具](install-the-tools.md)
* [Shell](navigating-the-windows-mixed-reality-home.md)
* [更新混合實境的 2D UWP 應用程式](building-2d-apps.md)
* [硬體配件](hardware-accessories.md)
* [混合實境擷取](mixed-reality-capture.md)
* [語音輸入](voice-input.md)
* [將應用程式提交到 Windows Store](submitting-an-app-to-the-microsoft-store.md)
* [使用 HoloLens 模擬器](using-the-hololens-emulator.md)
