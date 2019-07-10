---
title: 裝置入口網站的 API 參考
description: HoloLens 上 Windows Device Portal API 參考
author: JonMLyons
ms.author: JLyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、 Windows Device Portal，API
ms.openlocfilehash: 4b5b48c13b1b7ec8bfdf447f42097a8448b6a0e6
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694440"
---
# <a name="device-portal-api-reference"></a>裝置入口網站的 API 參考

中的所有項目[Windows Device Portal](using-the-windows-device-portal.md)為建置基礎 REST API 可用來存取資料，並以程式設計方式控制您的裝置。

## <a name="app-deloyment"></a>應用程式部署

**/api/app/packagemanager/package (DELETE)**

解除安裝應用程式

參數
* 封裝：要解除安裝之封裝的檔案名稱。

**/api/app/packagemanager/package (POST)**

安裝應用程式

參數
* 封裝：要安裝之封裝的檔案名稱。

承載
* 多部分符合的 http 內容

**/api/app/packagemanager/packages (GET)**

擷取已安裝的應用程式在系統上，詳細資料清單

傳回資料
* 列出已安裝的套件詳細資料

**/api/app/packagemanager/state (GET)**

取得中進行應用程式安裝狀態

## <a name="dump-collection"></a>傾印集合

**/api/debug/dump/usermode/crashcontrol (DELETE)**

停用的損毀傾印集合的側載應用程式

參數
* packageFullname： 封裝名稱

**/api/debug/dump/usermode/crashcontrol (GET)**

取得側載應用程式設定損毀傾印收集

參數
* packageFullname： 封裝名稱

**/api/debug/dump/usermode/crashcontrol (POST)**

啟用並設定側載應用程式的傾印控制項設定

參數
* packageFullname： 封裝名稱

**/api/debug/dump/usermode/crashdump (DELETE)**

刪除側載應用程式損毀傾印

參數
* packageFullname： 封裝名稱
* fileName： 傾印檔案名稱

**/api/debug/dump/usermode/crashdump (GET)**

擷取的側載應用程式損毀傾印

參數
* packageFullname： 封裝名稱
* fileName： 傾印檔案名稱

傳回資料
* 傾印檔案。 檢查使用 WinDbg 或 Visual Studio

**/api/debug/dump/usermode/dumps (GET)**

傳回清單的側載應用程式的所有損毀傾印

傳回資料
* 每個側邊載入應用程式的清單中的損毀傾印

## <a name="etw"></a>ETW

**/api/etw/providers (GET)**

列舉已註冊的提供者

傳回資料
* 提供者、 易記名稱和 GUID 的清單

**/api/etw/session/realtime (GET/WebSocket)**

建立即時的 ETW 工作階段;透過 websocket 的管理。

傳回資料
* 從啟用的提供者的 ETW 事件

## <a name="holographic-os"></a>全像攝影版 OS

**/api/holographic/os/etw/customproviders (GET)**

傳回一份 HoloLens 特定 ETW 提供者不會向系統

**/api/holographic/os/services (GET)**

傳回執行的所有服務的狀態。

**/api/holographic/os/settings/ipd (GET)**

取得在公釐為單位的預存的 IPD （Interpupillary 距離）

**/api/holographic/os/settings/ipd (POST)**

設定 IPD

參數
* ipd:若要設定以公釐新 IPD 值

**/api/holographic/os/webmanagement/settings/https (GET)**

取得 Device Portal 的 HTTPS 需求

**/api/holographic/os/webmanagement/settings/https (POST)**

設定裝置入口網站的 HTTPS 需求

參數
* 必要： yes、 no 或預設值

## <a name="holographic-perception"></a>全像攝影版的認知

**/api/holographic/perception/client (GET/WebSocket)**

接受 websocket 升級，並會將更新傳送 30fps 在 perception 用戶端執行。

參數
* clientmode: 「 作用中 」 時，會強制視覺追蹤模式無法被動地建立

## <a name="holographic-thermal"></a>全像攝影版的散熱

**/api/holographic/thermal/stage (GET)**

取得裝置 （1 暖，重要的 2 中的 0 的標準模式） 的熱階段

## <a name="perception-simulation-control"></a>Perception 模擬控制項

**/api/holographic/simulation/control/mode (GET)**

取得的模擬模式

**/api/holographic/simulation/control/mode (POST)**

設定模擬模式

參數
* 模式： 模擬模式： 預設、 模擬、 遠端，舊版

**/api/holographic/simulation/control/stream （刪除）**

刪除控制資料流。

**/api/holographic/simulation/control/stream (GET/WebSocket)**

開啟 web 通訊端連線控制資料流。

**/api/holographic/simulation/control/stream (POST)**

建立控制項的資料流 （優先順序是必要的） 或將資料公佈至建立的資料流 (所需的 streamId)。 張貼的資料應該是類型 ' 應用程式/八位元資料流 '。

## <a name="perception-simulation-playback"></a>Perception 模擬播放

**/api/holographic/simulation/playback/file (DELETE)**

刪除記錄。

參數
* 記錄：若要刪除記錄的名稱。

**/api/holographic/simulation/playback/file (POST)**

上傳的記錄。

**/api/holographic/simulation/playback/files (GET)**

取得所有記錄。

**/api/holographic/simulation/playback/session (GET)**

取得目前的錄製播放狀態。

參數
* 記錄：記錄的名稱。

**/api/holographic/simulation/playback/session/file (DELETE)**

卸載錄製。

參數
* 記錄：卸載所記錄的名稱。

**/api/holographic/simulation/playback/session/file (POST)**

載入記錄。

參數
* 記錄：載入記錄的名稱。

**/api/holographic/simulation/playback/session/files (GET)**

取得載入的所有記錄。

**/api/holographic/simulation/playback/session/pause (POST)**

暫停錄製。

參數
* 記錄：記錄的名稱。

**/api/holographic/simulation/playback/session/play (POST)**

播放錄製。

參數
* 記錄：記錄的名稱。

**/api/holographic/simulation/playback/session/stop (POST)**

停止錄製。

參數
* 記錄：記錄的名稱。

**/api/holographic/simulation/playback/session/types (GET)**

載入的記錄中取得資料的類型。

參數
* 記錄：記錄的名稱。

## <a name="perception-simulation-recording"></a>Perception 模擬記錄

**/api/holographic/simulation/recording/start (POST)**

開始錄製。 可同時處於作用中單一記錄。 必須設定其中一個標頭、 實際操作、 spatialMapping 或環境。

參數
* 前端：設定為 1，以記錄標頭的資料。
* 實際操作：記錄手動資料，請設定為 1。
* spatialMapping:記錄空間的對應，請設定為 1。
* 環境：若要記錄的環境資料，以設定為 1。
* 名稱：記錄的名稱。
* singleSpatialMappingFrame:記錄只有單一空間對應的框架，請設定為 1。

**/api/holographic/simulation/recording/status (GET)**

取得記錄狀態。

**/api/holographic/simulation/recording/stop (GET)**

停止目前的錄製。 為檔案，將會傳回記錄。

## <a name="mixed-reality-capture"></a>混合實境擷取

**/api/holographic/mrc/file (GET)**

從裝置的混合的實境檔案下載。 使用 op = 進行串流處理的資料流查詢參數。

參數
* 檔案名稱：編碼時，若要取得之視訊檔的名稱，hex64
* op： 資料流

**/api/holographic/mrc/file (DELETE)**

刪除混合的實境，從裝置記錄。

參數
* 檔案名稱：編碼時，要刪除之檔案的名稱，hex64

**/api/holographic/mrc/files (GET)**

傳回儲存在裝置上的混合的實境檔案清單

**/api/holographic/mrc/photo (POST)**

採用混合的實境相片，並建立該裝置上的檔案

參數
* holo： 擷取全像投影： true 或 false （預設為 false）
* pv： 擷取 PV 相機： true 或 false （預設為 false）
* RenderFromCamera:從相片/攝影機角度 (HoloLens 2) 轉譯： true 或 false （預設為 true）

**/api/holographic/mrc/settings (GET)**

取得預設的混合實境擷取設定

**/api/holographic/mrc/settings (POST)**

設定預設的混合實境擷取設定。  其中某些設定會套用至系統的 MRC 相片和視訊擷取。

**/api/holographic/mrc/status (GET)**

取得混合實境記錄 （執行、 已停止） 的狀態

**/api/holographic/mrc/thumbnail (GET)**

取得指定的檔案的縮圖影像。

參數
* 檔案名稱：編碼時，所要求的縮圖之檔案的名稱，hex64

**/api/holographic/mrc/video/control/start (POST)**

開始混合的實境錄音

參數
* holo： 擷取全像投影： true 或 false （預設為 false）
* pv： 擷取 PV 相機： true 或 false （預設為 false）
* mic： 擷取麥克風： true 或 false （預設為 false）
* 回送： 擷取應用程式音訊： true 或 false （預設為 false）
* RenderFromCamera:從相片/攝影機角度 (HoloLens 2) 轉譯： true 或 false （預設為 true）
* vstab:(HoloLens 2) 啟用視訊穩定功能： true 或 false （預設為 true）
* vstabbuffer:(HoloLens 2) 視訊穩定緩衝區延遲：0 到 30 個畫面格 （預設為 15 的畫面格）

**/api/holographic/mrc/video/control/stop (POST)**

停止目前的混合實境錄製

## <a name="mixed-reality-streaming"></a>資料流的混合的實境

HoloLens 支援混合實境透過區塊下載的分散 mp4 即時的預覽。

混合的實境資料流共用相同的參數來控制什麼擷取一組：
* holo： 擷取全像投影： true 或 false
* pv： 擷取 PV 相機： true 或 false
* mic： 擷取麥克風： true 或 false
* 回送： 擷取應用程式音訊： true 或 false

如果指定了其中一個項目： 將擷取全像投影、 相片或視訊攝影機和應用程式音訊<br>
如果指定了任何： 未指定的參數會預設為 false

選擇性參數 (HoloLens 2)
* RenderFromCamera: 從相片/影片相機的觀點來看，呈現: true 或 false （預設為 true）
* vstab： 啟用視訊穩定功能： true 或 false （預設為 false）
* vstabbuffer： 視訊穩定緩衝區延遲：0 到 30 個畫面格 （預設為 15 的畫面格）

**/api/holographic/stream/live.mp4 (GET)**

1280x720p 30fps 5Mbit 資料流。

**/api/holographic/stream/live_high.mp4 (GET)**

1280x720p 30fps 5Mbit 資料流。

**/api/holographic/stream/live_med.mp4 (GET)**

854x480p 30fps 2.5Mbit 資料流。

**/api/holographic/stream/live_low.mp4 (GET)**

428x240p 15 fps 0.6Mbit 資料流。

## <a name="networking"></a>網路功能

**/api/networking/ipconfig (GET)**

取得目前的 ip 組態

## <a name="os-information"></a>OS 資訊

**/api/os/info (GET)**

取得作業系統資訊

**/api/os/machinename (GET)**

取得電腦名稱

**/api/os/machinename (POST)**

設定電腦名稱

參數
* 名稱：新的機器名稱，hex64 編碼，將設定為

## <a name="performance-data"></a>效能資料

**/api/resourcemanager/processes (GET)**

傳回執行中處理序的詳細資料的清單

傳回資料
* JSON 與補充的處理序清單和每個處理序的詳細資料

**/api/resourcemanager/systemperf (GET)**

傳回系統效能統計資料 （讀取/寫入 I/O、 記憶體統計資料等等。

傳回資料
* JSON 與補充的系統資訊：CPU、 GPU、 記憶體、 網路、 IO

## <a name="power"></a>電源

**/api/power/battery (GET)**

取得目前的電池狀態

**/api/power/state (GET)**

檢查系統是否處於低電源狀態

## <a name="remote-control"></a>遠端控制

**/api/control/restart (POST)**

重新啟動目標裝置

**/api/control/shutdown （文章）**

關閉 目標裝置

## <a name="task-manager"></a>工作管理員

**/api/taskmanager/app (DELETE)**

停止現代化的應用程式

參數
* 封裝：完整的應用程式套件，hex64 編碼的名稱
* 強制停止：強制停止所有處理程序 （= yes）

**/api/taskmanager/app (POST)**

啟動新式應用程式

參數
* appid:若要啟動的應用程式 PRAID，hex64 編碼
* 封裝：完整的應用程式套件，hex64 編碼的名稱

## <a name="wifi-management"></a>WiFi 管理

**/api/wifi/interfaces (GET)**

列舉無線網路介面

傳回資料
* 詳細資料 （GUID、 描述等） 的無線介面清單

**/api/wifi/network (DELETE)**

刪除指定的介面上的網路相關聯的設定檔

參數
* 介面： 網路介面的 guid
* 設定檔： 設定檔名稱

**/api/wifi/networks (GET)**

列舉指定的網路介面上的無線網路

參數
* 介面： 網路介面的 guid

傳回資料
* 找到詳細資料的網路介面上的無線網路清單

**/api/wifi/network (POST)**

連線或中斷連線的指定介面上的網路

參數
* 介面： 網路介面的 guid
* ssid: ssid，hex64 編碼，來連接到
* op： 連接或中斷連接
* createprofile: yes 或 no
* 索引鍵： 共用的金鑰，hex64 編碼

## <a name="windows-performance-recorder"></a>Windows Performance Recorder

**/api/wpr/customtrace (POST)**

上傳 WPR 設定檔，並開始追蹤使用已上傳設定檔。

承載
* 多部分符合的 http 內容

傳回資料
* 傳回 WPR 工作階段狀態。

**/api/wpr/status (GET)**

擷取 WPR 工作階段狀態

傳回資料
* WPR 工作階段狀態。

**/api/wpr/trace (GET)**

停止 WPR （效能） 追蹤工作階段

傳回資料
* 傳回追蹤 ETL 檔案

**/api/wpr/trace (POST)**

啟動追蹤工作階段 WPR （效能）

參數
* 設定檔：設定檔名稱。 可用的設定檔會儲存在 perfprofiles/profiles.json

傳回資料
* 在啟動時，會傳回 WPR 工作階段狀態。

## <a name="see-also"></a>另請參閱
* [使用 Windows 裝置入口網站](using-the-windows-device-portal.md)
* [裝置入口網站 core API 參考 (UWP)](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
