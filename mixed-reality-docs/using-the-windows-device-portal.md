---
title: 使用 Windows 裝置入口網站
description: 適用于 HoloLens 的 Windows 裝置入口網站可讓您透過 Wi-fi 或 USB 從遠端設定及管理您的裝置。 Device Portal 是您 HoloLens 上的網頁伺服器，您可以從電腦上的網頁瀏覽器與它連線。 裝置入口網站包含許多工具，可協助您管理 HoloLens 並對應用程式進行優化和優化。
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: Windows 裝置入口網站、HoloLens
ms.openlocfilehash: 43ecfead7d2882d3624809bc05184f74131b8594
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375785"
---
# <a name="using-the-windows-device-portal"></a>使用 Windows 裝置入口網站

<table>
<tr>
<th>功能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (第 1 代)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"><a href="immersive-headset-hardware-details.md">沉浸式頭戴裝置</a></th>
</tr><tr>
<td> Windows 裝置入口網站</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

適用于 HoloLens 的 Windows 裝置入口網站可讓您透過 Wi-fi 或 USB 從遠端設定及管理您的裝置。 Device Portal 是您 HoloLens 上的網頁伺服器，您可以從電腦上的網頁瀏覽器與它連線。 裝置入口網站包含許多工具，可協助您管理 HoloLens 並對應用程式進行優化和優化。

本檔特別說明適用于 HoloLens 的 Windows 裝置入口網站。 若要使用適用于桌面的 Windows 裝置入口網站（包括 Windows Mixed Reality），請參閱[Windows 裝置入口網站總覽](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)

## <a name="setting-up-hololens-to-use-windows-device-portal"></a>設定 HoloLens 以使用 Windows 裝置入口網站

1. 開啟您的 HoloLens 並將裝置戴上。
2. 在 HoloLens （第1代）上執行 HoloLens2 或[Bloom](https://docs.microsoft.com/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom)的[開始手勢](https://docs.microsoft.com/hololens/hololens2-basic-usage#start-gesture)，以啟動主功能表。 
3. 看一下 [**設定**] 圖格，然後在 hololens （第1代）上執行 [[空中](https://docs.microsoft.com/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap)操作] 手勢，或透過[觸碰或使用手光線](https://docs.microsoft.com/hololens/hololens2-basic-usage)在 hololens 2 上選取它。 
4. 選取 [更新] 功能表項目。
5. 選取 [適用於開發人員] 功能表項目。
6. 啟用 [開發人員模式]。
7. [向下滾動](gaze-and-commit.md#composite-gestures)並啟用 [**裝置入口網站**]。
8. 如果您要設定 Windows 裝置入口網站，讓您可以透過 USB 或 Wi-fi 將應用程式部署到此 HoloLens，請按一下 [**配對**] 以[產生配對 PIN](using-visual-studio.md)。 將 [設定] 應用程式保留在 [PIN] 快顯視窗中，直到您在第一次部署期間輸入 Visual Studio 的 PIN 為止。

   ![在 Windows 全像攝影版的 [設定] 應用程式中啟用開發人員模式](images/deviceportalsettings.png)

## <a name="connecting-over-wi-fi"></a>透過 Wi-fi 連接

1. [將 HoloLens 連接至 wi-fi](connecting-to-wi-fi-on-hololens.md)。
2. 查詢您裝置的 IP 位址。
   * 在 [設定] 底下的裝置上尋找 IP 位址 **> 網路 & 網際網路 > wi-fi > [Advanced Options**]。
3. 從您電腦上的網頁瀏覽器，移至 HTTPs：//< YOUR_HOLOLENS_IP_ADDRESS >
   * 瀏覽器將會顯示下列訊息：「此網站的安全性憑證有問題」。 這是因為核發給 Device Portal 的憑證是測試憑證。 您可以暫時略過這個憑證錯誤並繼續。

## <a name="connecting-over-usb"></a>透過 USB 連接

1. [安裝工具](install-the-tools.md)，以確定您已在電腦上安裝 Windows 10 開發人員工具來執行 Visual Studio Update 1。 這將能啟用 USB 連線能力。
2. 使用 hololens （第1代）的微 USB 纜線或 HoloLens 2 的 USB-C，將您的 HoloLens 連接到您的電腦。
3. 從您電腦上的網頁瀏覽器，移至 [ [https://127.0.0.1:10080](https://127.0.0.1:10080)]。

## <a name="connecting-to-an-emulator"></a>連接到模擬器

您也可以透過模擬器使用 Device Portal。 若要連接到裝置入口網站，請使用[工具列](using-the-hololens-emulator.md)。 按一下這個圖示：![開啟裝置入口網站 圖示，](images/emulator-deviceportal.png)**開啟 [裝置入口網站**]：在模擬器中開啟 HoloLens OS 的 Windows 裝置入口網站。

## <a name="creating-a-username-and-password"></a>建立使用者名稱和密碼

![設定 Windows 裝置入口網站](images/windows-device-portal-credentials-reset-page-1000px.png) 的存取權<br>
*設定 Windows 裝置入口網站的存取權*

首次在 HoloLens 上連線到 Device Portal 時，您必須建立使用者名稱和密碼。
1. 在您電腦上的網頁瀏覽器中，輸入 HoloLens 的 IP 位址。 [設定存取] 頁面將會開啟。
2. 按一下或點擊 [**要求 pin** ]，並查看 HoloLens 顯示以取得產生的 pin。
3. 在 [**您的裝置上顯示的 pin** ] 文字方塊中輸入 pin。
4. 輸入您會用來連線到 Device Portal 的使用者名稱。 它並不需要是 Microsoft 帳戶 (MSA) 或網域名稱。
5. 輸入密碼並確認它。 密碼長度必須至少為七個字元。 它並不需要是 MSA 或網域密碼。
6. 按一下 [**配對**] 以連線至 HoloLens 上的 Windows 裝置入口網站。

如果您想要隨時變更此使用者名稱或密碼，您可以流覽至： HTTPs：//< YOUR_HOLOLENS_IP_ADDRESS >/devicepair.htm.，藉此重複此程式。

## <a name="security-certificate"></a>安全性憑證

如果您在瀏覽器中看到「憑證錯誤」，您可以藉由建立與裝置的信任關係來修正此問題。

每個 HoloLens 都會為其 SSL 連線產生唯一的自我簽署憑證。 根據預設，此憑證並不會受到您電腦的網頁瀏覽器信任，因此您可能會收到「憑證錯誤」。 藉由從您的 HoloLens 下載此憑證 (透過 USB 或您信任的 Wi-Fi 網路)，並在電腦上信任它，您便能安全地連線到您的裝置。
1. **請確定您使用的是安全的網路（USB 或您信任的 Wi-fi 網路）。**
2. 從裝置入口網站上的 [安全性] 頁面下載此裝置的憑證。
   * 流覽至： HTTPs：//< YOUR_HOLOLENS_IP_ADDRESS >/devicepair.htm
   * 開啟 [系統 > 喜好設定] 的節點。 
   * 向下流覽至 [裝置安全性]，按一下 [下載此裝置的憑證] 按鈕。
3. 將憑證安裝在您電腦上的「受信任的根憑證授權」存放區中。
   * 從 [Windows] 功能表中，輸入：管理電腦憑證並啟動 applet。
   * 展開 [**信任的根憑證授權**單位] 資料夾。
   * 按一下 [**憑證**] 資料夾。
   * 從 [動作] 功能表中，選取：所有工作 > 匯入 。
   * 使用您從 Device Portal 下載的憑證檔案完成憑證匯入精靈。
4. 重新啟動瀏覽器。

>[!NOTE]
> 只有裝置才會信任此憑證，而使用者必須在裝置已閃時再次執行此程式。


## <a name="device-portal-pages"></a>Device Portal 頁面

### <a name="home"></a>首頁

![Windows 裝置入口網站首頁上的 Microsoft HoloLens](images/windows-device-portal-home-page-1000px.png)<br>
*Microsoft HoloLens 上的 Windows 裝置入口網站首頁*

您的 Device Portal 工作階段從首頁開始。 從首頁左側的瀏覽列中存取其他頁面。

頁面頂端的工具列能讓您存取常用狀態與功能。
* **線上**：指出裝置是否已連線至 Wi-fi。
* **關機**：關閉裝置。
* **重新開機**：迴圈裝置上的電源。
* **安全性**：開啟 [裝置安全性] 頁面。
* **酷炫**：表示裝置的溫度。
* **A/C**：指出裝置是否已插入並收費。
* **Help**說明：開啟 REST 介面檔頁面。

首頁將顯示下列資訊：
* **裝置狀態：** 監視裝置的健全狀況，並回報重大錯誤。
* **Windows 資訊：** 顯示 HoloLens 的名稱和目前安裝的 windows 版本。
* [喜好設定] 區段包含下列設定：
   * **IPD**：設定 interpupillary 距離（IPD），這是使用者的瞳孔在直接查看時的中心之間的距離（以毫米為單位）。 此設定會立即生效。 預設值會在您設定裝置時自動計算。
   * **裝置名稱**：將名稱指派給 HoloLens。 在變更此值之後，必須重新啟動裝置才能生效。 按一下 [**儲存**] 之後，對話方塊會詢問您是否要立即重新開機裝置，或稍後重新開機。
   * **睡眠設定**：設定當裝置插入電源且電池在使用中時，要等待的時間長度。

### <a name="3d-view"></a>3D 檢視

在 Microsoft HoloLens 上的 Windows 裝置入口網站中 ![3D 視圖頁面](images/3dview-1000px.png)<br>
*Microsoft HoloLens 上 Windows 裝置入口網站中的 3D View 頁面*

使用 [3D 檢視] 頁面來查看 HoloLens 解譯您周遭環境的方式。 使用滑鼠來瀏覽檢視：
* 旋轉：按滑鼠左鍵 + 滑鼠;
* Pan：以滑鼠右鍵按一下滑鼠;
* Zoom：滑鼠滾輪。
* **追蹤選項**
   * 藉由勾選 [**強制視覺效果追蹤**]，開啟連續視覺效果追蹤。 
   * [**暫停**] 會停止視覺效果追蹤。
* **視圖選項**：在3D 視圖上設定選項：
  * **追蹤**：指出視覺效果追蹤是否作用中。
  * **顯示樓層**：顯示棋盤地板平面。
  * **顯示截錐**：顯示視圖的「截錐」。
  * **顯示穩定平面**：顯示 HoloLens 用來進行穩定動作的平面。
  * **顯示網格**：顯示代表您周圍的空間對應網格。
  * **顯示空間錨點**：顯示作用中應用程式的空間錨點。 您必須按一下 [更新] 按鈕，才能取得並重新整理錨點。
  * **顯示詳細資料**：顯示手的位置、前端旋轉四元數，以及裝置原點向量（當它們即時變更時）。
  * **全螢幕按鈕**：以全螢幕模式顯示3D 視圖。 按下 ESC 以離開全螢幕檢視。
* **表面重建**：按一下或按 [**更新**]，以顯示裝置中最新的空間對應網格。 完整階段可能需要一些時間才能完成（最多幾秒鐘）。 網格不會在3D 視圖中自動更新，您必須手動按一下 [**更新**]，從裝置取得最新的網格。 按一下 [**儲存**]，將目前的空間對應網格儲存為電腦上的 obj 檔案。
* **空間錨點**：按一下 [更新] 以顯示或更新作用中應用程式的空間錨點。

### <a name="mixed-reality-capture"></a>混合實境擷取

在 Microsoft HoloLens 上的 Windows 裝置入口網站中 ![混合現實捕捉頁面](images/windows-device-portal-mixed-reality-capture-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 裝置入口網站中的混合現實 Capture 頁面*

使用 [混合實境擷取] 頁面來儲存來自 HoloLens 的媒體串流。
* **設定**：藉由檢查下列設定來控制所捕捉的媒體串流：
  * **全息影像**：在影片串流中捕捉全像攝影內容。 全像投影是以單聲道進行轉譯，而非立體聲。
  * **PV 攝影機**：從相片/攝影機捕捉影片串流。
  * **Mic 音訊**：從麥克風陣列捕捉音訊。
  * **應用程式音訊**：從目前執行中的應用程式捕捉音訊。
  * **從相機**轉譯：如果執行中的[應用程式支援](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)，則將捕捉從相片/攝影機的角度對齊（僅限 HoloLens 2）。
  * **Live preview 品質**：選取 [螢幕解析度]、[畫面播放速率] 和 [即時預覽的串流速率]。
* 按一下或點擊 [**即時預覽**] 按鈕以顯示 capture 串流。 [**停止即時預覽**] 會停止 capture 串流。
* 按一下或按下 [**記錄**]，以使用指定的設定開始記錄混合現實串流。 [**停止錄製**] 會結束錄製並加以儲存。
* 按一下或點擊 [**拍攝相片**]，從 capture 串流拍攝靜止的影像。
* 影片**和相片**：顯示在裝置上拍攝的影片和相片捕捉清單。

> [!NOTE]
> [同時 MRC 的限制](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations)如下：
> * 如果應用程式在 Windows 裝置入口網站錄製影片時嘗試存取相片/攝影機，影片錄製將會停止。
>   * 如果應用程式存取具有 SharedReadOnly 模式的相片/攝影機，則 HoloLens 2 不會停止錄製影片。
> * 如果應用程式正在使用相片/攝影機，Windows 裝置入口網站就能夠拍攝相片或錄製影片。
> * 即時串流：
>   * HoloLens （第1代）可防止應用程式在從 Windows 裝置入口網站即時串流時存取相片/攝影機。
>   * 如果應用程式正在使用相片/攝影機，HoloLens （第1代）將無法即時串流。
>   * 當應用程式嘗試以 ExclusiveControl 模式存取相片/攝影機時，HoloLens 2 會自動停止即時串流。
>   * 當應用程式主動使用 PV 攝影機時，HoloLens 2 可以啟動即時串流。

### <a name="performance-tracing"></a>效能追蹤

Microsoft HoloLens 上 Windows 裝置入口網站中的 ![效能追蹤] 頁面](images/windows-device-portal-performance-tracing-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 裝置入口網站中的效能追蹤頁面*

從 HoloLens 捕獲[Windows 效能錄製](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx)器（WPR）追蹤。
* **可用的設定檔**：從下拉式清單中選取 WPR 設定檔，然後按一下或按 [**啟動**] 開始追蹤。
* **自訂設定檔**：按一下或點擊 **[流覽]** ，從您的電腦選擇 WPR 設定檔。 按一下或點選 **\[上傳並開始\]** 以開始追蹤。

若要停止追蹤，請按一下 [停止] 連結。 在追蹤檔案下載完成之前，請停留在此頁面上。

擷取的 ETL 檔案可以在 [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx) 中開啟以進行分析。

### <a name="processes"></a>處理程序

Microsoft HoloLens 上 Windows 裝置入口網站中的 ![處理常式] 頁面](images/windows-device-portal-running-processes-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 裝置入口網站中的 [進程] 頁面*

顯示有關目前正在執行之處理程序的詳細資訊。 這包括 App 與系統處理程序。

### <a name="system-performance"></a>系統效能

Microsoft HoloLens 上 Windows 裝置入口網站中的 ![系統效能] 頁面](images/windows-device-portal-system-performance-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 裝置入口網站中的 [系統效能] 頁面*

顯示系統診斷資訊的即時圖表，例如電源使用量、畫面播放速率與 CPU 負載。

下列為可用的衡量標準：
* **SoC 電源**：瞬間的系統晶片電源使用率，平均超過一分鐘
* **系統電源**：瞬間系統電源使用率，平均超過一分鐘
* **畫面播放速率**：每秒畫面數、每秒錯過的 VBlanks，以及連續錯過的 VBlanks
* **GPU**：GPU 引擎使用率，總可用百分比
* **CPU**：可用總計的百分比
* **I/O**：讀取和寫入
* **網路**：已接收和已傳送
* **記憶體**：總計、使用中、已認可、已分頁和未分頁

### <a name="apps"></a>[App]

Microsoft HoloLens 上 Windows 裝置入口網站中的 ![應用程式] 頁面](images/windows-device-portal-apps-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 裝置入口網站中的應用程式頁面*

管理安裝在 HoloLens 上的應用程式。
* **已安裝的應用程式**：移除並啟動應用程式。
* **正在執行應用程式**：列出目前正在執行的應用程式。
* **安裝應用程式**：從您電腦/網路上的資料夾選取要安裝的應用程式套件。
* 相依**性：** 新增您即將安裝之應用程式的相依性。
* **部署**：將選取的應用程式 + 相依性部署至 HoloLens。

### <a name="app-crash-dumps"></a>應用程式損毀傾印

Microsoft HoloLens 上 Windows 裝置入口網站中的 ![應用程式損毀傾印頁面](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 裝置入口網站中的應用程式損毀傾印頁面*

此頁面可讓您收集側載 App 的損毀傾印。 針對您要收集損毀傾印的每個應用程式，核取 [損毀傾印**已啟用**] 核取方塊。 返回此頁面以收集損毀傾印。 可以[在 Visual Studio 中開啟傾印檔案以進行偵錯工具](https://msdn.microsoft.com/library/d5zhxt22.aspx)。

### <a name="file-explorer"></a>檔案總管

Microsoft HoloLens 上 Windows 裝置入口網站中的 ![檔案瀏覽器] 頁面](images/fileexplorer-1000px.png)<br>
*Microsoft HoloLens 上 Windows 裝置入口網站中的檔案瀏覽器頁面*

使用 [檔案瀏覽器] 流覽、上傳和下載檔案。 您可以針對從 Visual Studio 或裝置入口網站部署的應用程式，使用 [檔] 資料夾、[圖片] 資料夾和 [本機儲存體] 資料夾中的檔案。

### <a name="kiosk-mode"></a>Kiosk 模式

>[!NOTE]
>Kiosk 模式僅適用于[Microsoft HoloLens 商業套件](commercial-features.md)。

如需透過 Windows 裝置入口網站啟用 kiosk 模式的最新指示，請參閱 Windows IT Pro 中心的在[kiosk 模式中設定 HoloLens 一](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803)文。

### <a name="logging"></a>記錄

Microsoft HoloLens 上 Windows 裝置入口網站中的 ![記錄頁面](images/windows-device-portal-logging-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 裝置入口網站中的 [記錄] 頁面*

管理 HoloLens 上 Windows （ETW）的即時事件追蹤。

勾選 [**隱藏提供者**] 僅顯示**事件**清單。
* **已註冊的提供者**：選取 ETW 提供者和追蹤層級。 追蹤等級是下列其中一個值 ︰
   1. 異常結束或終止
   2. 嚴重錯誤
   3. 警告
   4. 非錯誤警告

按一下或點選 **\[啟用\]** 以開始追蹤。 提供者已新增到 **\[啟用的提供者\]** 下拉式清單中。
* **自訂提供者**：選取自訂 ETW 提供者和追蹤層級。 依 GUID 識別提供者。 不要在 GUID 中包含括號。
* **啟用的提供者**：列出已啟用的提供者。 從下拉式清單選取提供者，然後按一下或點選 **\[停用\]** 以停止追蹤。 按一下或點選 **\[全部停止\]** 以暫停所有追蹤。
* **提供者歷程記錄**：顯示目前會話期間已啟用的 ETW 提供者。 按一下或點選 **\[啟用\]** 以啟用已停用的提供者。 按一下或點選 **\[清除\]** 以清除歷程記錄。
* **事件**：以資料表格式列出來自所選提供者的 ETW 事件。 此表格會即時更新。 在表格下方，按一下 **\[清除\]** 按鈕以刪除表格中的所有 ETW 事件。 這不會停用任何提供者。 您可以按一下 **\[儲存到檔案\]** ，將目前收集的 ETW 事件匯出到本機的 CSV 檔案。
* **篩選器**：可讓您篩選識別碼、關鍵字、層級、提供者名稱、工作名稱或文字所收集的 ETW 事件。 您可以將數個準則結合在一起：
   1. 針對套用至相同屬性的準則，會顯示可滿足任一準則的事件。
   2. 針對套用至不同屬性的準則，事件必須滿足所有條件

例如，您可以指定準則 *（[工作名稱] 包含 [Foo] 或 [橫條]）和（文字包含 [錯誤] 或 [警告]）*

### <a name="simulation"></a>模擬

Microsoft HoloLens 上 Windows 裝置入口網站中的 ![模擬] 頁面](images/windows-device-portal-simulation-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 裝置入口網站中的模擬頁面*

允許您記錄並播放輸入資料以進行測試。
* **Capture 室**：用來下載模擬的會議室檔案，其中包含使用者周圍的空間對應網格。 為房間命名，然後按一下 [ **Capture** ]，將資料儲存為電腦上的 xef 檔案。 此房間檔案可以載入 HoloLens 模擬器。
* **記錄**：檢查要記錄的資料流程、將記錄命名為，然後按一下或按下 [**記錄**] 開始進行編碼。 使用 HoloLens 執行動作，然後按一下 [**停止**]，將資料儲存為電腦上的 xef 檔案。 此檔案可以載入 HoloLens 模擬器或裝置。
* **播放**：按一下或點擊 **[上傳記錄**]，從您的電腦選取 xef 檔案，並將資料傳送至 HoloLens。
* **控制模式**：從下拉式清單中選取 [**預設**] 或 [**模擬**]，然後按一下或點擊 [**設定**] 按鈕，以選取 HoloLens 上的模式。 選擇 [模擬] 將會停用 HoloLens 上實際的感應器，並改為使用已上傳的模擬資料。 如果您切換到 [模擬]，您的 HoloLens 將不會對真實使用者做出回應，直到您切換回 [預設] 為止。

### <a name="networking"></a>網路功能

Microsoft HoloLens 上 Windows 裝置入口網站中的 ![網路功能] 頁面](images/windows-device-portal-networking-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 裝置入口網站中的網路功能頁面*

管理 HoloLens 上的 Wi-fi 連線。
* **WiFi 介面卡**：使用下拉式清單控制項選取 Wi-fi 介面卡和設定檔。 按一下或點擊 **[連線]** 以使用選取的介面卡。
* **可用的網路**：列出 HoloLens 可以連接的 Wi-fi 網路。 按一下**或點擊 [** 重新整理] 以更新清單。
* **IP**設定：顯示網路連線的 IP 位址和其他詳細資料。

### <a name="virtual-input"></a>虛擬輸入

在 Microsoft HoloLens 上的 Windows 裝置入口網站中 ![虛擬輸入頁面](images/windows-device-portal-virtual-input-page-1000px.png)<br>
*Microsoft HoloLens 上 Windows 裝置入口網站中的虛擬輸入頁面*

從遠端電腦傳送鍵盤輸入到 HoloLens。

按一下或點擊 [**虛擬鍵盤**] 底下的區域，以啟用將按鍵傳送至 HoloLens。 在 [**輸入文字**] 文字方塊中輸入，然後按一下或按 [**傳送**]，將按鍵傳送至使用中的應用程式。

## <a name="device-portal-rest-apis"></a>裝置入口網站 REST API

裝置入口網站中的所有專案都是以[REST API](device-portal-api-reference.md)為基礎，您可以選擇性地使用它來存取資料，並以程式設計方式控制您的裝置。
