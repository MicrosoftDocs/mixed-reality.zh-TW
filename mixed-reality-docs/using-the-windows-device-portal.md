---
title: 使用 Windows Device Portal
description: Windows Device Portal，如 HoloLens 可讓您設定及從遠端管理您的裝置，透過 Wi-fi 或 USB。 Device Portal 是您 HoloLens 上的網頁伺服器，您可以從電腦上的網頁瀏覽器與它連線。 裝置入口網站包含許多可協助您管理您的 HoloLens 和偵錯及最佳化您的應用程式的工具。
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: Windows Device Portal HoloLens
ms.openlocfilehash: 8b9935d6b64abfd22e2e856e0142c953a6366008
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594633"
---
# <a name="using-the-windows-device-portal"></a>使用 Windows Device Portal

<table>
<tr>
<th>功能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens （第 1 代）</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td> Windows Device Portal</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

Windows Device Portal，如 HoloLens 可讓您設定及從遠端管理您的裝置，透過 Wi-fi 或 USB。 Device Portal 是您 HoloLens 上的網頁伺服器，您可以從電腦上的網頁瀏覽器與它連線。 裝置入口網站包含許多可協助您管理您的 HoloLens 和偵錯及最佳化您的應用程式的工具。

這份文件是特別關於為 HoloLens Windows Device Portal。 若要使用 desktop （包括 Windows Mixed Reality） 的 Windows 裝置入口網站，請參閱[Windows Device Portal 概觀](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)

## <a name="setting-up-hololens-to-use-windows-device-portal"></a>若要使用 Windows Device Portal HoloLens 的設定

1. 開啟您的 HoloLens 並將裝置戴上。
2. 做出[盛開](gestures.md#bloom)手勢來啟動主功能表。
3. 注視**設定**圖格，並執行[空中點選](gestures.md#air-tap)筆勢。 執行第二個空中點選来放在您的環境中的應用程式。 當您放置 [設定] App 之後，該 App 便會啟動。
4. 選取 [更新] 功能表項目。
5. 選取 [適用於開發人員] 功能表項目。
6. 啟用 [開發人員模式]。
7. [向下捲動](gestures.md#composite-gestures)並啟用**裝置入口網站**。
8. 如果您要設定 Windows Device Portal，因此可以透過 USB 或 Wifi 將應用程式部署到此 HoloLens，按一下**配對**要[產生配對的 pin 碼](using-visual-studio.md#pairing-your-device-hololens)。 直到您輸入 pin 碼到 Visual Studio 在您第一次部署期間，則您可以保留釘選快顯視窗設定應用程式。

   ![在 [設定] 應用程式，適用於 Windows Holographic 的啟用開發人員模式](images/deviceportalsettings.png)

## <a name="connecting-over-wi-fi"></a>透過 Wi-fi 連線

1. [您的 HoloLens 連線至 Wi-fi](connecting-to-wi-fi-on-hololens.md)。
2. 查閱您的裝置 IP 位址。
   * 在裝置上找到的 IP 位址**設定 > 網路和網際網路 > Wi-fi > 進階選項**。
3. 從您的電腦上的瀏覽器，前往 https://<YOUR_HOLOLENS_IP_ADDRESS>
   * 瀏覽器會顯示下列訊息：「 沒有這個網站的安全性憑證有問題 」。 這是因為核發給 Device Portal 的憑證是測試憑證。 您可以暫時略過這個憑證錯誤並繼續。

## <a name="connecting-over-usb"></a>透過 USB 連線

1. [安裝工具](install-the-tools.md)藉此確定您有 Visual Studio Update 1 安裝在您的電腦上的 Windows 10 開發人員工具。 這將能啟用 USB 連線能力。
2. 透過 Micro-USB 纜線將您的 HoloLens 與電腦連接。
3. 從您電腦上的網頁瀏覽器，移至 http://127.0.0.1:10080。

## <a name="connecting-to-an-emulator"></a>連接到模擬器

您也可以透過模擬器使用 Device Portal。 若要連接到裝置入口網站，使用[工具列](using-the-hololens-emulator.md#anatomy-of-the-hololens-emulator)。 按一下這個圖示：![開啟 [裝置入口網站] 圖示](images/emulator-deviceportal.png)**開啟裝置入口網站**:開啟 Windows Device Portal HoloLens os 在模擬器中。

## <a name="creating-a-username-and-password"></a>建立使用者名稱和密碼

![設定 Windows Device Portal 的存取](images/windows-device-portal-credentials-reset-page-1000px.png)<br>
*設定 Windows Device Portal 的存取*

首次在 HoloLens 上連線到 Device Portal 時，您必須建立使用者名稱和密碼。
1. 在您電腦上的網頁瀏覽器中，輸入 HoloLens 的 IP 位址。 [設定存取] 頁面將會開啟。
2. 按一下或點選**要求 pin**並查看 HoloLens 顯示畫面來取得產生的 PIN。
3. 輸入中的釘選**顯示您的裝置上的 pin 碼**文字方塊中。
4. 輸入您會用來連線到 Device Portal 的使用者名稱。 它並不需要是 Microsoft 帳戶 (MSA) 或網域名稱。
5. 輸入密碼並確認它。 密碼長度必須至少為七個字元。 它並不需要是 MSA 或網域密碼。
6. 按一下 **配對**連接到 HoloLens 上的 Windows Device Portal。

如果您想要隨時變更此使用者名稱或密碼，您可以重複此程序造訪 [裝置安全性] 頁面，按一下**安全性**靠右或巡覽至上方的連結： https://<YOUR_HOLOLENS_IP_位址 > / devicesecurity.htm。

## <a name="security-certificate"></a>安全性憑證

如果您在瀏覽器中看見「憑證錯誤」，您可以透過和裝置建立信任關係來修正它。

每個 HoloLens 都會為其 SSL 連線產生唯一的自我簽署憑證。 根據預設，此憑證並不會受到您電腦的網頁瀏覽器信任，因此您可能會收到「憑證錯誤」。 藉由從您的 HoloLens 下載此憑證 (透過 USB 或您信任的 Wi-Fi 網路)，並在電腦上信任它，您便能安全地連線到您的裝置。
1. **請確定您是在安全的網路 （USB 或您信任的 Wi-fi 網路）。**
2. 從裝置入口網站的 [安全性] 頁面下載此裝置的憑證。
   * 按一下 **安全性**從最上層的正確清單圖示的連結，或瀏覽至： https://<YOUR_HOLOLENS_IP_ADDRESS>/devicesecurity.htm
3. 安裝在 「 受信任的根憑證授權 」 儲存在您的電腦的憑證。
   * 從 [Windows] 功能表中，輸入：管理電腦憑證，並啟動小程式。
   * 依序展開**信任的根憑證授權單位**資料夾。
   * 按一下 **憑證**資料夾。
   * 從 [動作] 功能表中，選取：所有的工作 > 匯入...
   * 使用您從 Device Portal 下載的憑證檔案完成憑證匯入精靈。
4. 重新啟動瀏覽器。

## <a name="device-portal-pages"></a>Device Portal 頁面

### <a name="home"></a>首頁

![Windows Device Portal 首頁上，在 Microsoft HoloLens 上](images/windows-device-portal-home-page-1000px.png)<br>
*Windows Device Portal 首頁上，在 Microsoft HoloLens 上*

您的 Device Portal 工作階段從首頁開始。 從首頁左側的瀏覽列中存取其他頁面。

頁面頂端的工具列能讓您存取常用狀態與功能。
* **線上**:指出裝置是否連線至 Wi-fi。
* **關閉**:關閉裝置。
* **重新啟動**:在裝置上的循環電源。
* **安全性**:開啟 [裝置安全性] 頁面。
* **非經常性存取**:指出裝置的溫度。
* **使燈光**:指出是否已插入裝置並收費。
* **協助**:開啟 REST 介面文件頁面。

首頁將顯示下列資訊：
* **裝置狀態：** 監視您的裝置的健全狀況，並報告重大錯誤。
* **Windows 資訊：** 顯示 HoloLens 的名稱和目前安裝的 Windows 版本。
* [喜好設定] 區段包含下列設定：
   * **IPD**:設定 interpupillary 距離 (IPD)，也就是之間的距離，以公釐，使用者的 pupils 時直接長遠的中央之間。 此設定會立即生效。 預設值會在您設定裝置時自動計算。
   * **裝置名稱**:指派名稱給 HoloLens。 在變更此值之後，必須重新啟動裝置才能生效。 按一下後**儲存**，對話方塊會詢問您是否要立即重新啟動裝置，或稍後重新開機。
   * **睡眠設定**:設定裝置進入睡眠狀態時它已插入電源之前，並在使用電池時的等待時間長度。

### <a name="3d-view"></a>3D 檢視

![在 Microsoft HoloLens 上的 Windows Device Portal 中的 3D 檢視頁面](images/3dview-1000px.png)<br>
*在 Microsoft HoloLens 上的 Windows Device Portal 中的 3D 檢視頁面*

使用 [3D 檢視] 頁面來查看 HoloLens 解譯您周遭環境的方式。 使用滑鼠來瀏覽檢視：
* 輪替： 按一下滑鼠左鍵 + 滑鼠;
* 按一下 + 滑鼠;，以滑鼠右鍵移動瀏覽：
* 縮放︰ 滑鼠捲軸。
* **追蹤選項**
   * 藉由檢查開啟連續 visual 追蹤**強制 visual 追蹤**。 
   * **暫停**停止 visual 的追蹤。
* **檢視選項**:3D 檢視上的設定選項：
  * **追蹤**:表示 visual 追蹤是否為作用中。
  * **顯示 floor**:會顯示在棋盤式的 floor 平面。
  * **顯示範圍**:顯示檢視範圍。
  * **顯示穩定平面**:顯示 HoloLens 使用穩定影片的平面。
  * **顯示網狀結構**:顯示空間對應網狀結構，表示周圍環境。
  * **顯示空間的錨點**:顯示作用中的應用程式空間的錨點。 您必須按一下 [更新] 按鈕，以取得及重新整理的錨點。
  * **顯示詳細資料**:即時變更時，顯示會送位置 」、 「 前端旋轉的四元數和 「 裝置來源向量。
  * **全螢幕按鈕**:以全螢幕模式顯示 3D 檢視。 按下 ESC 以離開全螢幕檢視。
* **介面重構**:按一下或點選**更新**顯示從裝置的最新的空間對應網狀結構。 可能需要花費一些時間 (最多幾秒鐘) 才能完成完整作業。 網狀結構不會在 3D 檢視中，會自動更新，然後您必須手動按一下**更新**從裝置取得最新的網格。 按一下 **儲存**為 obj 檔案在您的電腦上儲存目前的空間對應網狀結構。
* **空間的錨點**:按一下 顯示或更新為使用中的應用程式空間的錨點的更新。

### <a name="mixed-reality-capture"></a>混合實境擷取

![在 Microsoft HoloLens 上的 Windows Device Portal 中的混合的實境擷取頁面](images/windows-device-portal-mixed-reality-capture-page-1000px.png)<br>
*在 Microsoft HoloLens 上的 Windows Device Portal 中的混合的實境擷取頁面*

使用[混合實境擷取](mixed-reality-capture.md)頁面，即可從 HoloLens 儲存媒體資料流。
* **設定**:控制的媒體資料流，會擷取藉由檢查下列設定：
  * **全像投影**:擷取視訊資料流中全像攝影版的內容。 全像投影是以單聲道進行轉譯，而非立體聲。
  * **PV 相機**:擷取相片或視訊攝影機的視訊資料流。
  * **Mic 音訊**:會擷取從麥克風陣列的音訊。
  * **應用程式音訊**:會擷取從目前正在執行的應用程式的音訊。
  * **即時預覽品質**:選取螢幕解析度、 畫面播放速率和串流處理速率的即時預覽。
* 按一下或點選**即時預覽** 按鈕，顯示擷取的資料流。 **停止即時預覽**停止擷取資料流。
* 按一下或點選**記錄**開始錄製的混合實境資料流中，使用指定的設定。 **停止錄製**結束錄製，並將它儲存。
* 按一下或點選**Take 相片**才靜止影像會從擷取的資料流。
* **影片和相片**:顯示一份該裝置採取了視訊和相片的擷取。

請注意，HoloLens App 無法在您正在從 Device Portal 錄製或串流即時預覽時，擷取 MRC 相片或視訊。

### <a name="performance-tracing"></a>效能追蹤

![追蹤 Microsoft HoloLens 上的 Windows Device Portal 中頁面的效能](images/windows-device-portal-performance-tracing-page-1000px.png)<br>
*追蹤 Microsoft HoloLens 上的 Windows Device Portal 中頁面的效能*

擷取[Windows Performance Recorder](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) (WPR) 追蹤從您的 HoloLens。
* **可用的設定檔**:從下拉式清單中，然後按一下或點選 選取 WPR 設定檔**啟動**若要開始追蹤。
* **自訂設定檔**:按一下或點選**瀏覽**選擇 WPR 設定檔從您的電腦。 按一下或點選 [上傳並開始] 以開始追蹤。

若要停止追蹤，按一下 [停止] 連結。 下載完成的追蹤檔之前，請停留在此頁面。

擷取的 ETL 檔案可以在 [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx) 中開啟以進行分析。

### <a name="processes"></a>處理程序

![在 Microsoft HoloLens 上的 Windows Device Portal 中的程序頁面](images/windows-device-portal-running-processes-page-1000px.png)<br>
*在 Microsoft HoloLens 上的 Windows Device Portal 中的程序頁面*

顯示有關目前正在執行之處理程序的詳細資訊。 這包括 App 與系統處理程序。

### <a name="system-performance"></a>系統效能

![在 Microsoft HoloLens 上的 Windows Device Portal 中的系統效能 頁面](images/windows-device-portal-system-performance-page-1000px.png)<br>
*在 Microsoft HoloLens 上的 Windows Device Portal 中的系統效能 頁面*

顯示系統診斷資訊的即時圖表，例如電源使用量、畫面播放速率與 CPU 負載。

下列為可用的衡量標準：
* **SoC power**:即時系統晶片上的電源耗用量，平均超過一分鐘
* **系統電源**:即時系統的電源耗用量，平均每一分鐘
* **畫面播放速率**:每秒畫面格數錯過每秒的 VBlanks 和連續錯過的 VBlanks
* **GPU**:GPU 引擎使用率、 可用的總計百分比
* **CPU**： 可用的總計百分比
* **I/O**:讀取和寫入
* **網路**：接收和傳送
* **記憶體**:總計，在使用中，認可，分頁和非分頁

### <a name="apps"></a>應用程式

![在 Microsoft HoloLens 上的 Windows Device Portal 中的 [應用程式] 頁面](images/windows-device-portal-apps-page-1000px.png)<br>
*在 Microsoft HoloLens 上的 Windows Device Portal 中的 [應用程式] 頁面*

管理 HoloLens 所安裝的應用程式。
* **安裝的應用程式**:移除，然後啟動應用程式。
* **執行應用程式**:列出目前正在執行的應用程式。
* **安裝應用程式**:從您的電腦/網路上的資料夾中，選取安裝的應用程式套件。
* **相依性**:新增您要安裝的應用程式的相依性。
* **部署**:將選取的應用程式 + 相依性部署 HoloLens。

### <a name="app-crash-dumps"></a>應用程式損毀傾印

![在 Microsoft HoloLens 上的 Windows Device Portal 中的 應用程式損毀傾印頁面](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)<br>
*在 Microsoft HoloLens 上的 Windows Device Portal 中的 應用程式損毀傾印頁面*

此頁面可讓您收集側載 App 的損毀傾印。 請檢查**損毀傾印啟用**核取方塊，每個應用程式，您想要收集損毀傾印。 返回此頁面以收集損毀傾印。 傾印檔案可能[進行偵錯 Visual Studio 中開啟](https://msdn.microsoft.com/library/d5zhxt22.aspx)。

### <a name="file-explorer"></a>檔案總管

![在 Microsoft HoloLens 上的 Windows Device Portal 中的檔案總管頁面](images/fileexplorer-1000px.png)<br>
*在 Microsoft HoloLens 上的 Windows Device Portal 中的檔案總管頁面*

您可以使用檔案總管 來瀏覽、 上傳及下載檔案。 您可以使用您從 Visual Studio 或裝置入口網站部署的應用程式檔案的本機儲存體資料夾和文件 資料夾的 圖片 資料夾中。

### <a name="kiosk-mode"></a>Kiosk 模式

>[!NOTE]
>Kiosk 模式 」 僅適用於[Commercial Suite 時，Microsoft HoloLens](commercial-features.md)。

請檢查[kiosk 模式設定 HoloLens](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) Windows IT Pro Center 中的發行項，如需啟用透過 Windows Device Portal 的 kiosk 模式的最新指示。

### <a name="logging"></a>記錄

![在 Microsoft HoloLens 上的 Windows Device Portal 中的 [記錄] 頁面](images/windows-device-portal-logging-page-1000px.png)<br>
*在 Microsoft HoloLens 上的 Windows Device Portal 中的 [記錄] 頁面*

管理即時事件追蹤的 Windows (ETW) HoloLens 上。

請檢查**隱藏提供者**以顯示**事件**只列出。
* **註冊提供者**:選取的 ETW 提供者 」 和 「 追蹤層級。 追蹤等級是下列其中一個值 ︰
   1. 異常結束或終止
   2. 嚴重錯誤
   3. 警告
   4. 非錯誤警告

按一下或點選 [啟用] 以開始追蹤。 提供者已新增到 [啟用的提供者] 下拉式清單中。
* **自訂提供者**:選取自訂的 ETW 提供者 」 和 「 追蹤層級。 依 GUID 識別提供者。 不要在 GUID 中包含括號。
* **啟用的提供者**:列出已啟用的提供者。 從下拉式清單選取提供者，然後按一下或點選 [停用] 以停止追蹤。 按一下或點選 [全部停止] 以暫停所有追蹤。
* **提供者記錄**:顯示目前的工作階段期間啟用啟用的 ETW 提供者。 按一下或點選 [啟用] 以啟用已停用的提供者。 按一下或點選 [清除] 以清除歷程記錄。
* **事件**:列出所選的提供者，以資料表格式的 ETW 事件。 此表格會即時更新。 下方資料表中，按一下**清除** 按鈕，從資料表中刪除所有 ETW 事件。 這不會停用任何提供者。 您可以按一下 **\[儲存到檔案\]**，將目前收集的 ETW 事件匯出到本機的 CSV 檔案。
* **篩選**:可讓您篩選識別碼、 關鍵字、 層級，提供者名稱、 工作名稱或文字所收集的 ETW 事件。 您可以一起結合數個準則：
   1. 準則套用至相同的屬性-事件可滿足這些條件的任何一個會顯示。
   2. 準則的事件必須滿足所有條件的都套用不同的屬性-

例如，您可以指定準則 *（工作名稱包含 'Foo' 列'） 和 （文字會包含 「 錯誤 」 或 「 警告 」）*

### <a name="simulation"></a>模擬

![在 Microsoft HoloLens 上的 Windows Device Portal 中的 [模擬] 頁面](images/windows-device-portal-simulation-page-1000px.png)<br>
*在 Microsoft HoloLens 上的 Windows Device Portal 中的 [模擬] 頁面*

允許您記錄並播放輸入資料以進行測試。
* **擷取聊天室**:用來下載包含如使用者的恍神空間對應網狀結構的模擬的空間檔案。 命名空間，然後按一下**擷取**為.xef 檔案在您的電腦上儲存的資料。 此房間檔案可以載入 HoloLens 模擬器。
* **錄製**:檢查資料流記錄，記錄，然後按一下或點選**記錄**開始錄製。 執行您的 HoloLens 的動作，然後按一下 **停止**為.xef 檔案在您的電腦上儲存的資料。 此檔案可以載入 HoloLens 模擬器或裝置。
* **播放**:按一下或點選**上傳記錄**選取 xef 檔案從您的電腦，並將資料傳送至 HoloLens。
* **控制項模式**:選取**預設**或是**模擬**從下拉式清單中，然後按一下或點選**設定**按鈕來選取 HoloLens 的模式。 選擇 [模擬] 將會停用 HoloLens 上實際的感應器，並改為使用已上傳的模擬資料。 如果您切換到 [模擬]，您的 HoloLens 將不會對真實使用者做出回應，直到您切換回 [預設] 為止。

### <a name="networking"></a>網路功能

![在 Microsoft HoloLens 上的 Windows Device Portal 中的 [網路功能] 頁面](images/windows-device-portal-networking-page-1000px.png)<br>
*在 Microsoft HoloLens 上的 Windows Device Portal 中的 [網路功能] 頁面*

管理 HoloLens 上的 Wi-fi 連線。
* **WiFi 配接器**:使用下拉式清單控制項選取 Wi-fi 配接器和設定檔。 按一下或點選**Connect**使用選取的配接器。
* **可用的網路**:列出 HoloLens 可以連線到 Wi-fi 網路。 按一下或點選**重新整理**更新清單。
* **IP 組態**:顯示的 IP 位址和網路連線的其他詳細資料。

### <a name="virtual-input"></a>虛擬輸入

![在 Microsoft HoloLens 上的 Windows Device Portal 中的虛擬輸入頁面](images/windows-device-portal-virtual-input-page-1000px.png)<br>
*在 Microsoft HoloLens 上的 Windows Device Portal 中的虛擬輸入頁面*

從遠端電腦傳送鍵盤輸入到 HoloLens。

按一下或點選下方的區域**虛擬鍵盤**以啟用傳送按鍵 HoloLens。 在中輸入**輸入文字**文字方塊中，按一下或點選**傳送**將按鍵傳送至作用中的應用程式。

## <a name="device-portal-rest-apis"></a>裝置入口網站的 REST API

在裝置入口網站中的所有項目為基礎建置的[REST API](device-portal-api-reference.md) ，您可以選擇性地使用，以存取資料，並以程式設計方式控制您的裝置。
