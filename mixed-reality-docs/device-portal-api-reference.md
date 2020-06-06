---
title: 裝置入口網站 API 參照
description: HoloLens 上 Windows 裝置入口網站的 API 參考
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens，Windows 裝置入口網站，API
ms.openlocfilehash: 17268c9a20d3da0ee90e5d6cead4342d3badf800
ms.sourcegitcommit: f24ac845e184c2f90e8b15adab9addb913f5cb83
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "84451323"
---
# <a name="device-portal-api-reference"></a>裝置入口網站 API 參照

[Windows 裝置入口網站](using-the-windows-device-portal.md)中的所有專案都是以 REST API 為基礎，您可以用它來存取資料並以程式設計方式控制您的裝置。

## <a name="app-deloyment"></a>應用程式部署常見問題

**/api/app/packagemanager/package （DELETE）**

卸載應用程式

參數
* package：要卸載之封裝的檔案名。

**/api/app/packagemanager/package （POST）**

安裝應用程式

參數
* package：要安裝之封裝的檔案名。

Payload
* 多部分符合的 HTTP 主體

**/api/app/packagemanager/packages （GET）**

抓取系統上已安裝的應用程式清單，並提供詳細資料

傳回資料
* 包含詳細資料的已安裝套件清單

**/api/app/packagemanager/state （GET）**

取得進行中應用程式安裝的狀態

## <a name="dump-collection"></a>傾印集合

**/api/debug/dump/usermode/crashcontrol （DELETE）**

停用側載應用程式的損毀傾印集合

參數
* packageFullname：封裝名稱

**/api/debug/dump/usermode/crashcontrol （GET）**

取得側載 apps 損毀傾印集合的設定

參數
* packageFullname：封裝名稱

**/api/debug/dump/usermode/crashcontrol （POST）**

啟用和設定側載應用程式的傾印控制設定

參數
* packageFullname：封裝名稱

**/api/debug/dump/usermode/crashdump （DELETE）**

刪除側載應用程式的損毀傾印

參數
* packageFullname：封裝名稱
* 檔案名：傾印檔案名

**/api/debug/dump/usermode/crashdump （GET）**

抓取側載應用程式的損毀傾印

參數
* packageFullname：封裝名稱
* 檔案名：傾印檔案名

傳回資料
* 傾印檔案。 使用 WinDbg 或 Visual Studio 檢查

**/api/debug/dump/usermode/dumps （GET）**

傳回側載應用程式的所有損毀傾印清單

傳回資料
* 每一端已載入應用程式的損毀傾印清單

## <a name="etw"></a>ETW

**/api/etw/providers （GET）**

列舉已註冊的提供者

傳回資料
* 提供者清單、易記名稱和 GUID

**/api/etw/session/realtime （GET/WebSocket）**

建立即時 ETW 會話;透過 websocket 管理。

傳回資料
* 來自已啟用提供者的 ETW 事件

## <a name="holographic-os"></a>全像攝影版 OS

**/api/holographic/os/etw/customproviders （GET）**

傳回未向系統註冊的 HoloLens 特定 ETW 提供者清單

**/api/holographic/os/services （GET）**

傳回所有執行中服務的狀態。

**/api/holographic/os/settings/ipd （GET）**

取得以毫米為單位的儲存 IPD （Interpupillary 距離）

**/api/holographic/os/settings/ipd （POST）**

設定 IPD

參數
* ipd：要以毫米設定的新 IPD 值

**/api/holographic/os/webmanagement/settings/HTTPs （GET）**

取得裝置入口網站的 HTTPS 需求

**/api/holographic/os/webmanagement/settings/HTTPs （POST）**

設定裝置入口網站的 HTTPS 需求

參數
* 必要：是，否或預設值

## <a name="holographic-perception"></a>全像攝影

**/api/holographic/perception/client （GET/WebSocket）**

接受 websocket 升級，並執行將更新以 30 fps 傳送的感知用戶端。

參數
* clientmode：「作用中」會在無法被動建立時強制執行視覺化追蹤模式

## <a name="holographic-thermal"></a>全像熱

**/api/holographic/thermal/stage （GET）**

取得裝置的散熱階段（0個正常、1個暖、2個重大）

## <a name="perception-simulation-control"></a>認知模擬控制

**/api/holographic/simulation/control/mode （GET）**

取得模擬模式

**/api/holographic/simulation/control/mode （POST）**

設定模擬模式

參數
* 模式：模擬模式：預設、模擬、遠端、舊版

**/api/holographic/simulation/control/stream （DELETE）**

刪除控制資料流程。

**/api/holographic/simulation/control/stream （GET/WebSocket）**

開啟控制項資料流程的 web 通訊端連接。

**/api/holographic/simulation/control/stream （POST）**

建立控制資料流程（需要優先權）或將資料張貼到建立的資料流程（需要 streamId）。 張貼的資料應該是「應用程式/八位串流」類型。

**/api/holographic/simulation/display/stream （GET/WebSocket）**

要求模擬影片串流，其中包含在「模擬」模式下呈現給系統顯示的內容。  簡單的格式描述元標頭會一開始傳送，後面接著 h.264 編碼材質，每一個標頭前面會加上指示眼睛索引和材質大小的標題。

## <a name="perception-simulation-playback"></a>認知模擬播放

**/api/holographic/simulation/playback/file （DELETE）**

刪除錄製。

參數
* 錄製：要刪除的記錄名稱。

**/api/holographic/simulation/playback/file （POST）**

上傳記錄。

**/api/holographic/simulation/playback/files （GET）**

取得所有錄製。

**/api/holographic/simulation/playback/session （GET）**

取得錄製的目前播放狀態。

參數
* 錄製：錄製的名稱。

**/api/holographic/simulation/playback/session/file （DELETE）**

卸載記錄。

參數
* 錄製：要卸載的記錄名稱。

**/api/holographic/simulation/playback/session/file （POST）**

載入錄製。

參數
* 錄製：要載入的記錄名稱。

**/api/holographic/simulation/playback/session/files （GET）**

取得所有已載入的錄製。

**/api/holographic/simulation/playback/session/pause （POST）**

暫停錄製。

參數
* 錄製：錄製的名稱。

**/api/holographic/simulation/playback/session/play （POST）**

播放錄製。

參數
* 錄製：錄製的名稱。

**/api/holographic/simulation/playback/session/stop （POST）**

停止錄製。

參數
* 錄製：錄製的名稱。

**/api/holographic/simulation/playback/session/types （GET）**

取得已載入記錄中的資料類型。

參數
* 錄製：錄製的名稱。

## <a name="perception-simulation-recording"></a>認知模擬記錄

**/api/holographic/simulation/recording/start （POST）**

開始錄製。 一次只能有一個使用中的錄製。 必須設定 head、手、spatialMapping 或環境之一。

參數
* head：設定為1以記錄 head 資料。
* 實習：設定為1以記錄手資料。
* spatialMapping：設定為1以記錄空間對應。
* 環境：設定為1以記錄環境資料。
* 名稱：記錄的名稱。
* singleSpatialMappingFrame：設定為1，只記錄一個空間對應框架。

**/api/holographic/simulation/recording/status （GET）**

取得錄製狀態。

**/api/holographic/simulation/recording/stop （GET）**

停止目前的錄製。 記錄將會以檔案的形式傳回。

## <a name="mixed-reality-capture"></a>混合實境擷取

**/api/holographic/mrc/file （GET）**

從裝置下載混合的現實檔案。 使用 op = 資料流程查詢參數進行串流處理。

參數
* filename：要取得之影片檔案的名稱、hex64 編碼
* op：資料流程

**/api/holographic/mrc/file （DELETE）**

從裝置中刪除混合現實記錄。

參數
* filename：要刪除之檔案的名稱、hex64 編碼

**/api/holographic/mrc/files （GET）**

傳回儲存在裝置上的混合 reality 檔案清單

**/api/holographic/mrc/photo （POST）**

採用混合的現實相片，並在裝置上建立檔案

參數
* hololens： capture 全息影像： true 或 false （預設為 false）
* pv： capture PV 攝影機： true 或 false （預設為 false）
* RenderFromCamera：（僅限 HoloLens 2）從相片/攝影機的觀點呈現： true 或 false （預設為 true）

**/api/holographic/mrc/settings （GET）**

取得預設的混合現實捕捉設定

**/api/holographic/mrc/settings （POST）**

設定預設的混合現實捕捉設定。  其中部分設定會套用至系統的 MRC 相片和影片捕獲。

**/api/holographic/mrc/status （GET）**

取得 Windows 裝置入口網站中的混合現實 capture 的狀態。

***回應***

回應包含 JSON 屬性，指出 Windows 裝置入口網站是否正在錄製影片。

``` javascript
{"IsRecording" : boolean}
```

**/api/holographic/mrc/thumbnail （GET）**

取得指定檔案的縮圖影像。

參數
* 檔案名：要為其要求縮圖之檔案的名稱、hex64 編碼

**/api/holographic/mrc/video/control/start （POST）**

開始進行混合的事實記錄

參數
* hololens： capture 全息影像： true 或 false （預設為 false）
* pv： capture PV 攝影機： true 或 false （預設為 false）
* mic： capture 麥克風： true 或 false （預設為 false）
* 回送：捕獲應用程式音訊： true 或 false （預設為 false）
* RenderFromCamera：（僅限 HoloLens 2）從相片/攝影機的觀點呈現： true 或 false （預設為 true）
* vstab：（僅限 HoloLens 2）啟用影片穩定： true 或 false （預設為 true）
* vstabbuffer：（僅限 HoloLens 2）影片穩定緩衝區延遲：0到30個框架（預設為15個畫面）

**/api/holographic/mrc/video/control/stop （POST）**

停止目前的混合現實記錄

## <a name="mixed-reality-streaming"></a>混合現實串流

HoloLens 支援透過區塊下載的分散的方式，即時預覽混合現實。

混合的事實資料流會共用一組相同的參數，以控制已捕捉的內容：
* hololens： capture 全息影像： true 或 false
* pv：捕捉 PV 攝影機： true 或 false
* mic：捕捉麥克風： true 或 false
* 回送：捕獲應用程式音訊： true 或 false

如果未指定這些內容：將會捕捉到全息影像、相片/攝影機和應用程式音訊<br>
如果指定了任何值：未指定的參數將預設為 false

選擇性參數（僅限 HoloLens 2）
* RenderFromCamera：從相片/攝影機的角度呈現： true 或 false （預設為 true）
* vstab：啟用影片穩定： true 或 false （預設為 false）
* vstabbuffer：視頻穩定緩衝區延遲：0到30的框架（預設為15個框架）

**/api/holographic/stream/live.mp4 （GET）**

解析度為 1280x720p 30fps 5Mbit 串流。

**/api/holographic/stream/live_high. （GET）**

解析度為 1280x720p 30fps 5Mbit 串流。

**/api/holographic/stream/live_med. （GET）**

854x480p 30fps 2.5 Mbit 串流。

**/api/holographic/stream/live_low. （GET）**

428x240p 15fps 0.6 Mbit 串流。

## <a name="networking"></a>網路功能

**/api/networking/ipconfig （GET）**

取得目前的 ip 設定

## <a name="os-information"></a>作業系統資訊

**/api/os/info （GET）**

取得作業系統資訊

**/api/os/machinename （GET）**

取得電腦名稱稱

**/api/os/machinename （POST）**

設定電腦名稱稱

參數
* 名稱：新的電腦名稱稱，hex64 編碼，設定為

## <a name="performance-data"></a>效能資料

**/api/resourcemanager/processes （GET）**

傳回執行中進程的清單，並提供詳細資料

傳回資料
* JSON，內含進程的清單和每個進程的詳細資料

**/api/resourcemanager/systemperf （GET）**

傳回系統效能統計資料（i/o 讀取/寫入、記憶體統計等）。

傳回資料
* 具有系統資訊的 JSON： CPU、GPU、記憶體、網路、IO

## <a name="power"></a>電源

**/api/power/battery （GET）**

取得目前的電池狀態

**/api/power/state （GET）**

檢查系統是否處於低電源狀態

## <a name="remote-control"></a>遠端控制

**/api/control/restart （POST）**

重新開機目標裝置

**/api/control/shutdown （POST）**

關閉目標裝置

## <a name="task-manager"></a>工作管理員

**/api/taskmanager/app （DELETE）**

停止現代化應用程式

參數
* package：應用程式套件的完整名稱，hex64 編碼
* forcestop：強制停止所有進程（= 是）

**/api/taskmanager/app （POST）**

啟動現代化應用程式

參數
* appid：要啟動之應用程式的 PRAID，hex64 編碼
* package：應用程式套件的完整名稱，hex64 編碼

## <a name="wifi-management"></a>WiFi 管理

**/api/wifi/interfaces （GET）**

列舉無線網路介面

傳回資料
* 具有詳細資料的無線介面清單（GUID、描述等等）

**/api/wifi/network （DELETE）**

刪除與指定之介面上的網路相關聯的設定檔

參數
* 介面：網路介面 guid
* 設定檔：設定檔名稱

**/api/wifi/networks （GET）**

列舉指定網路介面上的無線網路

參數
* 介面：網路介面 guid

傳回資料
* 在網路介面上找到的無線網路清單，並提供詳細資料

**/api/wifi/network （POST）**

連接或中斷連線到指定介面上的網路

參數
* 介面：網路介面 guid
* ssid：用來連線到的 ssid （hex64 編碼）
* op：連接或中斷連線
* createprofile：是或否
* 金鑰：共用金鑰，hex64 編碼

## <a name="windows-performance-recorder"></a>Windows Performance Recorder

**/api/wpr/customtrace （POST）**

上傳 WPR 設定檔，並使用上傳的設定檔開始追蹤。

Payload
* 多部分符合的 HTTP 主體

傳回資料
* 傳回 WPR 會話狀態。

**/api/wpr/status （GET）**

抓取 WPR 會話的狀態

傳回資料
* WPR 會話狀態。

**/api/wpr/trace （GET）**

停止 WPR （效能）追蹤會話

傳回資料
* 傳回追蹤 ETL 檔案

**/api/wpr/trace （POST）**

啟動 WPR （效能）追蹤會話

參數
* 設定檔：設定檔名稱。 可用的設定檔會儲存在 perfprofiles/profiles 中。 json

傳回資料
* 在啟動時，會傳回 WPR 會話狀態。

## <a name="see-also"></a>另請參閱
* [使用 Windows 裝置入口網站](using-the-windows-device-portal.md)
* [裝置入口網站核心 API 參考（UWP）](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
