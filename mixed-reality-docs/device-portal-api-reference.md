---
title: 裝置入口網站 API 參照
description: HoloLens 上 Windows 裝置入口網站的 API 參考
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens，Windows 裝置入口網站，API
ms.openlocfilehash: 8c9d60f458cddd3ba258aed0ee82f7aa16c10ba6
ms.sourcegitcommit: 6d9d01d53137435c787f247f095d5255581695fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83227950"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="07554-104">裝置入口網站 API 參照</span><span class="sxs-lookup"><span data-stu-id="07554-104">Device portal API reference</span></span>

<span data-ttu-id="07554-105">[Windows 裝置入口網站](using-the-windows-device-portal.md)中的所有專案都是以 REST API 為基礎，您可以用它來存取資料並以程式設計方式控制您的裝置。</span><span class="sxs-lookup"><span data-stu-id="07554-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="07554-106">應用程式部署常見問題</span><span class="sxs-lookup"><span data-stu-id="07554-106">App deloyment</span></span>

<span data-ttu-id="07554-107">**/api/app/packagemanager/package （DELETE）**</span><span class="sxs-lookup"><span data-stu-id="07554-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="07554-108">卸載應用程式</span><span class="sxs-lookup"><span data-stu-id="07554-108">Uninstalls an app</span></span>

<span data-ttu-id="07554-109">參數</span><span class="sxs-lookup"><span data-stu-id="07554-109">Parameters</span></span>
* <span data-ttu-id="07554-110">package：要卸載之封裝的檔案名。</span><span class="sxs-lookup"><span data-stu-id="07554-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="07554-111">**/api/app/packagemanager/package （POST）**</span><span class="sxs-lookup"><span data-stu-id="07554-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="07554-112">安裝應用程式</span><span class="sxs-lookup"><span data-stu-id="07554-112">Installs an App</span></span>

<span data-ttu-id="07554-113">參數</span><span class="sxs-lookup"><span data-stu-id="07554-113">Parameters</span></span>
* <span data-ttu-id="07554-114">package：要安裝之封裝的檔案名。</span><span class="sxs-lookup"><span data-stu-id="07554-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="07554-115">Payload</span><span class="sxs-lookup"><span data-stu-id="07554-115">Payload</span></span>
* <span data-ttu-id="07554-116">多部分符合的 HTTP 主體</span><span class="sxs-lookup"><span data-stu-id="07554-116">multi-part conforming http body</span></span>

<span data-ttu-id="07554-117">**/api/app/packagemanager/packages （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="07554-118">抓取系統上已安裝的應用程式清單，並提供詳細資料</span><span class="sxs-lookup"><span data-stu-id="07554-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="07554-119">傳回資料</span><span class="sxs-lookup"><span data-stu-id="07554-119">Return data</span></span>
* <span data-ttu-id="07554-120">包含詳細資料的已安裝套件清單</span><span class="sxs-lookup"><span data-stu-id="07554-120">List of installed packages with details</span></span>

<span data-ttu-id="07554-121">**/api/app/packagemanager/state （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="07554-122">取得進行中應用程式安裝的狀態</span><span class="sxs-lookup"><span data-stu-id="07554-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="07554-123">傾印集合</span><span class="sxs-lookup"><span data-stu-id="07554-123">Dump collection</span></span>

<span data-ttu-id="07554-124">**/api/debug/dump/usermode/crashcontrol （DELETE）**</span><span class="sxs-lookup"><span data-stu-id="07554-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="07554-125">停用側載應用程式的損毀傾印集合</span><span class="sxs-lookup"><span data-stu-id="07554-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="07554-126">參數</span><span class="sxs-lookup"><span data-stu-id="07554-126">Parameters</span></span>
* <span data-ttu-id="07554-127">packageFullname：封裝名稱</span><span class="sxs-lookup"><span data-stu-id="07554-127">packageFullname : package name</span></span>

<span data-ttu-id="07554-128">**/api/debug/dump/usermode/crashcontrol （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="07554-129">取得側載 apps 損毀傾印集合的設定</span><span class="sxs-lookup"><span data-stu-id="07554-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="07554-130">參數</span><span class="sxs-lookup"><span data-stu-id="07554-130">Parameters</span></span>
* <span data-ttu-id="07554-131">packageFullname：封裝名稱</span><span class="sxs-lookup"><span data-stu-id="07554-131">packageFullname : package name</span></span>

<span data-ttu-id="07554-132">**/api/debug/dump/usermode/crashcontrol （POST）**</span><span class="sxs-lookup"><span data-stu-id="07554-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="07554-133">啟用和設定側載應用程式的傾印控制設定</span><span class="sxs-lookup"><span data-stu-id="07554-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="07554-134">參數</span><span class="sxs-lookup"><span data-stu-id="07554-134">Parameters</span></span>
* <span data-ttu-id="07554-135">packageFullname：封裝名稱</span><span class="sxs-lookup"><span data-stu-id="07554-135">packageFullname : package name</span></span>

<span data-ttu-id="07554-136">**/api/debug/dump/usermode/crashdump （DELETE）**</span><span class="sxs-lookup"><span data-stu-id="07554-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="07554-137">刪除側載應用程式的損毀傾印</span><span class="sxs-lookup"><span data-stu-id="07554-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="07554-138">參數</span><span class="sxs-lookup"><span data-stu-id="07554-138">Parameters</span></span>
* <span data-ttu-id="07554-139">packageFullname：封裝名稱</span><span class="sxs-lookup"><span data-stu-id="07554-139">packageFullname : package name</span></span>
* <span data-ttu-id="07554-140">檔案名：傾印檔案名</span><span class="sxs-lookup"><span data-stu-id="07554-140">fileName : dump file name</span></span>

<span data-ttu-id="07554-141">**/api/debug/dump/usermode/crashdump （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="07554-142">抓取側載應用程式的損毀傾印</span><span class="sxs-lookup"><span data-stu-id="07554-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="07554-143">參數</span><span class="sxs-lookup"><span data-stu-id="07554-143">Parameters</span></span>
* <span data-ttu-id="07554-144">packageFullname：封裝名稱</span><span class="sxs-lookup"><span data-stu-id="07554-144">packageFullname : package name</span></span>
* <span data-ttu-id="07554-145">檔案名：傾印檔案名</span><span class="sxs-lookup"><span data-stu-id="07554-145">fileName : dump file name</span></span>

<span data-ttu-id="07554-146">傳回資料</span><span class="sxs-lookup"><span data-stu-id="07554-146">Return data</span></span>
* <span data-ttu-id="07554-147">傾印檔案。</span><span class="sxs-lookup"><span data-stu-id="07554-147">Dump file.</span></span> <span data-ttu-id="07554-148">使用 WinDbg 或 Visual Studio 檢查</span><span class="sxs-lookup"><span data-stu-id="07554-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="07554-149">**/api/debug/dump/usermode/dumps （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="07554-150">傳回側載應用程式的所有損毀傾印清單</span><span class="sxs-lookup"><span data-stu-id="07554-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="07554-151">傳回資料</span><span class="sxs-lookup"><span data-stu-id="07554-151">Return data</span></span>
* <span data-ttu-id="07554-152">每一端已載入應用程式的損毀傾印清單</span><span class="sxs-lookup"><span data-stu-id="07554-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="07554-153">ETW</span><span class="sxs-lookup"><span data-stu-id="07554-153">ETW</span></span>

<span data-ttu-id="07554-154">**/api/etw/providers （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="07554-155">列舉已註冊的提供者</span><span class="sxs-lookup"><span data-stu-id="07554-155">Enumerates registered providers</span></span>

<span data-ttu-id="07554-156">傳回資料</span><span class="sxs-lookup"><span data-stu-id="07554-156">Return data</span></span>
* <span data-ttu-id="07554-157">提供者清單、易記名稱和 GUID</span><span class="sxs-lookup"><span data-stu-id="07554-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="07554-158">**/api/etw/session/realtime （GET/WebSocket）**</span><span class="sxs-lookup"><span data-stu-id="07554-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="07554-159">建立即時 ETW 會話;透過 websocket 管理。</span><span class="sxs-lookup"><span data-stu-id="07554-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="07554-160">傳回資料</span><span class="sxs-lookup"><span data-stu-id="07554-160">Return data</span></span>
* <span data-ttu-id="07554-161">來自已啟用提供者的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="07554-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="07554-162">全像攝影版 OS</span><span class="sxs-lookup"><span data-stu-id="07554-162">Holographic OS</span></span>

<span data-ttu-id="07554-163">**/api/holographic/os/etw/customproviders （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="07554-164">傳回未向系統註冊的 HoloLens 特定 ETW 提供者清單</span><span class="sxs-lookup"><span data-stu-id="07554-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="07554-165">**/api/holographic/os/services （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="07554-166">傳回所有執行中服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="07554-166">Returns the states of all services running.</span></span>

<span data-ttu-id="07554-167">**/api/holographic/os/settings/ipd （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="07554-168">取得以毫米為單位的儲存 IPD （Interpupillary 距離）</span><span class="sxs-lookup"><span data-stu-id="07554-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="07554-169">**/api/holographic/os/settings/ipd （POST）**</span><span class="sxs-lookup"><span data-stu-id="07554-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="07554-170">設定 IPD</span><span class="sxs-lookup"><span data-stu-id="07554-170">Sets the IPD</span></span>

<span data-ttu-id="07554-171">參數</span><span class="sxs-lookup"><span data-stu-id="07554-171">Parameters</span></span>
* <span data-ttu-id="07554-172">ipd：要以毫米設定的新 IPD 值</span><span class="sxs-lookup"><span data-stu-id="07554-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="07554-173">**/api/holographic/os/webmanagement/settings/HTTPs （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="07554-174">取得裝置入口網站的 HTTPS 需求</span><span class="sxs-lookup"><span data-stu-id="07554-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="07554-175">**/api/holographic/os/webmanagement/settings/HTTPs （POST）**</span><span class="sxs-lookup"><span data-stu-id="07554-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="07554-176">設定裝置入口網站的 HTTPS 需求</span><span class="sxs-lookup"><span data-stu-id="07554-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="07554-177">參數</span><span class="sxs-lookup"><span data-stu-id="07554-177">Parameters</span></span>
* <span data-ttu-id="07554-178">必要：是，否或預設值</span><span class="sxs-lookup"><span data-stu-id="07554-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="07554-179">全像攝影</span><span class="sxs-lookup"><span data-stu-id="07554-179">Holographic Perception</span></span>

<span data-ttu-id="07554-180">**/api/holographic/perception/client （GET/WebSocket）**</span><span class="sxs-lookup"><span data-stu-id="07554-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="07554-181">接受 websocket 升級，並執行將更新以 30 fps 傳送的感知用戶端。</span><span class="sxs-lookup"><span data-stu-id="07554-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="07554-182">參數</span><span class="sxs-lookup"><span data-stu-id="07554-182">Parameters</span></span>
* <span data-ttu-id="07554-183">clientmode：「作用中」會在無法被動建立時強制執行視覺化追蹤模式</span><span class="sxs-lookup"><span data-stu-id="07554-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="07554-184">全像熱</span><span class="sxs-lookup"><span data-stu-id="07554-184">Holographic Thermal</span></span>

<span data-ttu-id="07554-185">**/api/holographic/thermal/stage （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="07554-186">取得裝置的散熱階段（0個正常、1個暖、2個重大）</span><span class="sxs-lookup"><span data-stu-id="07554-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="07554-187">認知模擬控制</span><span class="sxs-lookup"><span data-stu-id="07554-187">Perception Simulation Control</span></span>

<span data-ttu-id="07554-188">**/api/holographic/simulation/control/mode （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="07554-189">取得模擬模式</span><span class="sxs-lookup"><span data-stu-id="07554-189">Get the simulation mode</span></span>

<span data-ttu-id="07554-190">**/api/holographic/simulation/control/mode （POST）**</span><span class="sxs-lookup"><span data-stu-id="07554-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="07554-191">設定模擬模式</span><span class="sxs-lookup"><span data-stu-id="07554-191">Set the simulation mode</span></span>

<span data-ttu-id="07554-192">參數</span><span class="sxs-lookup"><span data-stu-id="07554-192">Parameters</span></span>
* <span data-ttu-id="07554-193">模式：模擬模式：預設、模擬、遠端、舊版</span><span class="sxs-lookup"><span data-stu-id="07554-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="07554-194">**/api/holographic/simulation/control/stream （DELETE）**</span><span class="sxs-lookup"><span data-stu-id="07554-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="07554-195">刪除控制資料流程。</span><span class="sxs-lookup"><span data-stu-id="07554-195">Delete a control stream.</span></span>

<span data-ttu-id="07554-196">**/api/holographic/simulation/control/stream （GET/WebSocket）**</span><span class="sxs-lookup"><span data-stu-id="07554-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="07554-197">開啟控制項資料流程的 web 通訊端連接。</span><span class="sxs-lookup"><span data-stu-id="07554-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="07554-198">**/api/holographic/simulation/control/stream （POST）**</span><span class="sxs-lookup"><span data-stu-id="07554-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="07554-199">建立控制資料流程（需要優先權）或將資料張貼到建立的資料流程（需要 streamId）。</span><span class="sxs-lookup"><span data-stu-id="07554-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="07554-200">張貼的資料應該是「應用程式/八位串流」類型。</span><span class="sxs-lookup"><span data-stu-id="07554-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="07554-201">**/api/holographic/simulation/display/stream （GET/WebSocket）**</span><span class="sxs-lookup"><span data-stu-id="07554-201">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="07554-202">要求模擬影片串流，其中包含在「模擬」模式下呈現給系統顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="07554-202">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="07554-203">簡單的格式描述元標頭會一開始傳送，後面接著 h.264 編碼材質，每一個標頭前面會加上指示眼睛索引和材質大小的標題。</span><span class="sxs-lookup"><span data-stu-id="07554-203">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="07554-204">認知模擬播放</span><span class="sxs-lookup"><span data-stu-id="07554-204">Perception Simulation Playback</span></span>

<span data-ttu-id="07554-205">**/api/holographic/simulation/playback/file （DELETE）**</span><span class="sxs-lookup"><span data-stu-id="07554-205">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="07554-206">刪除錄製。</span><span class="sxs-lookup"><span data-stu-id="07554-206">Delete a recording.</span></span>

<span data-ttu-id="07554-207">參數</span><span class="sxs-lookup"><span data-stu-id="07554-207">Parameters</span></span>
* <span data-ttu-id="07554-208">錄製：要刪除的記錄名稱。</span><span class="sxs-lookup"><span data-stu-id="07554-208">recording : Name of recording to delete.</span></span>

<span data-ttu-id="07554-209">**/api/holographic/simulation/playback/file （POST）**</span><span class="sxs-lookup"><span data-stu-id="07554-209">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="07554-210">上傳記錄。</span><span class="sxs-lookup"><span data-stu-id="07554-210">Upload a recording.</span></span>

<span data-ttu-id="07554-211">**/api/holographic/simulation/playback/files （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-211">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="07554-212">取得所有錄製。</span><span class="sxs-lookup"><span data-stu-id="07554-212">Get all recordings.</span></span>

<span data-ttu-id="07554-213">**/api/holographic/simulation/playback/session （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-213">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="07554-214">取得錄製的目前播放狀態。</span><span class="sxs-lookup"><span data-stu-id="07554-214">Get the current playback state of a recording.</span></span>

<span data-ttu-id="07554-215">參數</span><span class="sxs-lookup"><span data-stu-id="07554-215">Parameters</span></span>
* <span data-ttu-id="07554-216">錄製：錄製的名稱。</span><span class="sxs-lookup"><span data-stu-id="07554-216">recording : Name of recording.</span></span>

<span data-ttu-id="07554-217">**/api/holographic/simulation/playback/session/file （DELETE）**</span><span class="sxs-lookup"><span data-stu-id="07554-217">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="07554-218">卸載記錄。</span><span class="sxs-lookup"><span data-stu-id="07554-218">Unload a recording.</span></span>

<span data-ttu-id="07554-219">參數</span><span class="sxs-lookup"><span data-stu-id="07554-219">Parameters</span></span>
* <span data-ttu-id="07554-220">錄製：要卸載的記錄名稱。</span><span class="sxs-lookup"><span data-stu-id="07554-220">recording : Name of recording to unload.</span></span>

<span data-ttu-id="07554-221">**/api/holographic/simulation/playback/session/file （POST）**</span><span class="sxs-lookup"><span data-stu-id="07554-221">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="07554-222">載入錄製。</span><span class="sxs-lookup"><span data-stu-id="07554-222">Load a recording.</span></span>

<span data-ttu-id="07554-223">參數</span><span class="sxs-lookup"><span data-stu-id="07554-223">Parameters</span></span>
* <span data-ttu-id="07554-224">錄製：要載入的記錄名稱。</span><span class="sxs-lookup"><span data-stu-id="07554-224">recording : Name of recording to load.</span></span>

<span data-ttu-id="07554-225">**/api/holographic/simulation/playback/session/files （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-225">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="07554-226">取得所有已載入的錄製。</span><span class="sxs-lookup"><span data-stu-id="07554-226">Get all loaded recordings.</span></span>

<span data-ttu-id="07554-227">**/api/holographic/simulation/playback/session/pause （POST）**</span><span class="sxs-lookup"><span data-stu-id="07554-227">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="07554-228">暫停錄製。</span><span class="sxs-lookup"><span data-stu-id="07554-228">Pause a recording.</span></span>

<span data-ttu-id="07554-229">參數</span><span class="sxs-lookup"><span data-stu-id="07554-229">Parameters</span></span>
* <span data-ttu-id="07554-230">錄製：錄製的名稱。</span><span class="sxs-lookup"><span data-stu-id="07554-230">recording : Name of recording.</span></span>

<span data-ttu-id="07554-231">**/api/holographic/simulation/playback/session/play （POST）**</span><span class="sxs-lookup"><span data-stu-id="07554-231">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="07554-232">播放錄製。</span><span class="sxs-lookup"><span data-stu-id="07554-232">Play a recording.</span></span>

<span data-ttu-id="07554-233">參數</span><span class="sxs-lookup"><span data-stu-id="07554-233">Parameters</span></span>
* <span data-ttu-id="07554-234">錄製：錄製的名稱。</span><span class="sxs-lookup"><span data-stu-id="07554-234">recording : Name of recording.</span></span>

<span data-ttu-id="07554-235">**/api/holographic/simulation/playback/session/stop （POST）**</span><span class="sxs-lookup"><span data-stu-id="07554-235">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="07554-236">停止錄製。</span><span class="sxs-lookup"><span data-stu-id="07554-236">Stop a recording.</span></span>

<span data-ttu-id="07554-237">參數</span><span class="sxs-lookup"><span data-stu-id="07554-237">Parameters</span></span>
* <span data-ttu-id="07554-238">錄製：錄製的名稱。</span><span class="sxs-lookup"><span data-stu-id="07554-238">recording : Name of recording.</span></span>

<span data-ttu-id="07554-239">**/api/holographic/simulation/playback/session/types （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-239">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="07554-240">取得已載入記錄中的資料類型。</span><span class="sxs-lookup"><span data-stu-id="07554-240">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="07554-241">參數</span><span class="sxs-lookup"><span data-stu-id="07554-241">Parameters</span></span>
* <span data-ttu-id="07554-242">錄製：錄製的名稱。</span><span class="sxs-lookup"><span data-stu-id="07554-242">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="07554-243">認知模擬記錄</span><span class="sxs-lookup"><span data-stu-id="07554-243">Perception Simulation Recording</span></span>

<span data-ttu-id="07554-244">**/api/holographic/simulation/recording/start （POST）**</span><span class="sxs-lookup"><span data-stu-id="07554-244">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="07554-245">開始錄製。</span><span class="sxs-lookup"><span data-stu-id="07554-245">Start a recording.</span></span> <span data-ttu-id="07554-246">一次只能有一個使用中的錄製。</span><span class="sxs-lookup"><span data-stu-id="07554-246">Only a single recording can be active at once.</span></span> <span data-ttu-id="07554-247">必須設定 head、手、spatialMapping 或環境之一。</span><span class="sxs-lookup"><span data-stu-id="07554-247">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="07554-248">參數</span><span class="sxs-lookup"><span data-stu-id="07554-248">Parameters</span></span>
* <span data-ttu-id="07554-249">head：設定為1以記錄 head 資料。</span><span class="sxs-lookup"><span data-stu-id="07554-249">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="07554-250">實習：設定為1以記錄手資料。</span><span class="sxs-lookup"><span data-stu-id="07554-250">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="07554-251">spatialMapping：設定為1以記錄空間對應。</span><span class="sxs-lookup"><span data-stu-id="07554-251">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="07554-252">環境：設定為1以記錄環境資料。</span><span class="sxs-lookup"><span data-stu-id="07554-252">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="07554-253">名稱：記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="07554-253">name : Name of the recording.</span></span>
* <span data-ttu-id="07554-254">singleSpatialMappingFrame：設定為1，只記錄一個空間對應框架。</span><span class="sxs-lookup"><span data-stu-id="07554-254">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="07554-255">**/api/holographic/simulation/recording/status （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-255">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="07554-256">取得錄製狀態。</span><span class="sxs-lookup"><span data-stu-id="07554-256">Get recording state.</span></span>

<span data-ttu-id="07554-257">**/api/holographic/simulation/recording/stop （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-257">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="07554-258">停止目前的錄製。</span><span class="sxs-lookup"><span data-stu-id="07554-258">Stop the current recording.</span></span> <span data-ttu-id="07554-259">記錄將會以檔案的形式傳回。</span><span class="sxs-lookup"><span data-stu-id="07554-259">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="07554-260">混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="07554-260">Mixed Reality Capture</span></span>

<span data-ttu-id="07554-261">**/api/holographic/mrc/file （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-261">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="07554-262">從裝置下載混合的現實檔案。</span><span class="sxs-lookup"><span data-stu-id="07554-262">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="07554-263">使用 op = 資料流程查詢參數進行串流處理。</span><span class="sxs-lookup"><span data-stu-id="07554-263">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="07554-264">參數</span><span class="sxs-lookup"><span data-stu-id="07554-264">Parameters</span></span>
* <span data-ttu-id="07554-265">filename：要取得之影片檔案的名稱、hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="07554-265">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="07554-266">op：資料流程</span><span class="sxs-lookup"><span data-stu-id="07554-266">op : stream</span></span>

<span data-ttu-id="07554-267">**/api/holographic/mrc/file （DELETE）**</span><span class="sxs-lookup"><span data-stu-id="07554-267">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="07554-268">從裝置中刪除混合現實記錄。</span><span class="sxs-lookup"><span data-stu-id="07554-268">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="07554-269">參數</span><span class="sxs-lookup"><span data-stu-id="07554-269">Parameters</span></span>
* <span data-ttu-id="07554-270">filename：要刪除之檔案的名稱、hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="07554-270">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="07554-271">**/api/holographic/mrc/files （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-271">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="07554-272">傳回儲存在裝置上的混合 reality 檔案清單</span><span class="sxs-lookup"><span data-stu-id="07554-272">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="07554-273">**/api/holographic/mrc/photo （POST）**</span><span class="sxs-lookup"><span data-stu-id="07554-273">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="07554-274">採用混合的現實相片，並在裝置上建立檔案</span><span class="sxs-lookup"><span data-stu-id="07554-274">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="07554-275">參數</span><span class="sxs-lookup"><span data-stu-id="07554-275">Parameters</span></span>
* <span data-ttu-id="07554-276">hololens： capture 全息影像： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="07554-276">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="07554-277">pv： capture PV 攝影機： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="07554-277">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="07554-278">RenderFromCamera：（僅限 HoloLens 2）從相片/攝影機的觀點呈現： true 或 false （預設為 true）</span><span class="sxs-lookup"><span data-stu-id="07554-278">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="07554-279">**/api/holographic/mrc/settings （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-279">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="07554-280">取得預設的混合現實捕捉設定</span><span class="sxs-lookup"><span data-stu-id="07554-280">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="07554-281">**/api/holographic/mrc/settings （POST）**</span><span class="sxs-lookup"><span data-stu-id="07554-281">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="07554-282">設定預設的混合現實捕捉設定。</span><span class="sxs-lookup"><span data-stu-id="07554-282">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="07554-283">其中部分設定會套用至系統的 MRC 相片和影片捕獲。</span><span class="sxs-lookup"><span data-stu-id="07554-283">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="07554-284">**/api/holographic/mrc/status （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-284">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="07554-285">取得已記錄之混合事實的狀態（執行中、已停止）</span><span class="sxs-lookup"><span data-stu-id="07554-285">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="07554-286">**/api/holographic/mrc/thumbnail （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-286">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="07554-287">取得指定檔案的縮圖影像。</span><span class="sxs-lookup"><span data-stu-id="07554-287">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="07554-288">參數</span><span class="sxs-lookup"><span data-stu-id="07554-288">Parameters</span></span>
* <span data-ttu-id="07554-289">檔案名：要為其要求縮圖之檔案的名稱、hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="07554-289">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="07554-290">**/api/holographic/mrc/video/control/start （POST）**</span><span class="sxs-lookup"><span data-stu-id="07554-290">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="07554-291">開始進行混合的事實記錄</span><span class="sxs-lookup"><span data-stu-id="07554-291">Starts a mixed reality recording</span></span>

<span data-ttu-id="07554-292">參數</span><span class="sxs-lookup"><span data-stu-id="07554-292">Parameters</span></span>
* <span data-ttu-id="07554-293">hololens： capture 全息影像： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="07554-293">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="07554-294">pv： capture PV 攝影機： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="07554-294">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="07554-295">mic： capture 麥克風： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="07554-295">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="07554-296">回送：捕獲應用程式音訊： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="07554-296">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="07554-297">RenderFromCamera：（僅限 HoloLens 2）從相片/攝影機的觀點呈現： true 或 false （預設為 true）</span><span class="sxs-lookup"><span data-stu-id="07554-297">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="07554-298">vstab：（僅限 HoloLens 2）啟用影片穩定： true 或 false （預設為 true）</span><span class="sxs-lookup"><span data-stu-id="07554-298">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="07554-299">vstabbuffer：（僅限 HoloLens 2）影片穩定緩衝區延遲：0到30個框架（預設為15個畫面）</span><span class="sxs-lookup"><span data-stu-id="07554-299">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="07554-300">**/api/holographic/mrc/video/control/stop （POST）**</span><span class="sxs-lookup"><span data-stu-id="07554-300">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="07554-301">停止目前的混合現實記錄</span><span class="sxs-lookup"><span data-stu-id="07554-301">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="07554-302">混合現實串流</span><span class="sxs-lookup"><span data-stu-id="07554-302">Mixed Reality Streaming</span></span>

<span data-ttu-id="07554-303">HoloLens 支援透過區塊下載的分散的方式，即時預覽混合現實。</span><span class="sxs-lookup"><span data-stu-id="07554-303">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="07554-304">混合的事實資料流會共用一組相同的參數，以控制已捕捉的內容：</span><span class="sxs-lookup"><span data-stu-id="07554-304">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="07554-305">hololens： capture 全息影像： true 或 false</span><span class="sxs-lookup"><span data-stu-id="07554-305">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="07554-306">pv：捕捉 PV 攝影機： true 或 false</span><span class="sxs-lookup"><span data-stu-id="07554-306">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="07554-307">mic：捕捉麥克風： true 或 false</span><span class="sxs-lookup"><span data-stu-id="07554-307">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="07554-308">回送：捕獲應用程式音訊： true 或 false</span><span class="sxs-lookup"><span data-stu-id="07554-308">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="07554-309">如果未指定這些內容：將會捕捉到全息影像、相片/攝影機和應用程式音訊</span><span class="sxs-lookup"><span data-stu-id="07554-309">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="07554-310">如果指定了任何值：未指定的參數將預設為 false</span><span class="sxs-lookup"><span data-stu-id="07554-310">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="07554-311">選擇性參數（僅限 HoloLens 2）</span><span class="sxs-lookup"><span data-stu-id="07554-311">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="07554-312">RenderFromCamera：從相片/攝影機的角度呈現： true 或 false （預設為 true）</span><span class="sxs-lookup"><span data-stu-id="07554-312">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="07554-313">vstab：啟用影片穩定： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="07554-313">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="07554-314">vstabbuffer：視頻穩定緩衝區延遲：0到30的框架（預設為15個框架）</span><span class="sxs-lookup"><span data-stu-id="07554-314">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="07554-315">**/api/holographic/stream/live.mp4 （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-315">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="07554-316">解析度為 1280x720p 30fps 5Mbit 串流。</span><span class="sxs-lookup"><span data-stu-id="07554-316">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="07554-317">**/api/holographic/stream/live_high. （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-317">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="07554-318">解析度為 1280x720p 30fps 5Mbit 串流。</span><span class="sxs-lookup"><span data-stu-id="07554-318">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="07554-319">**/api/holographic/stream/live_med. （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-319">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="07554-320">854x480p 30fps 2.5 Mbit 串流。</span><span class="sxs-lookup"><span data-stu-id="07554-320">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="07554-321">**/api/holographic/stream/live_low. （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-321">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="07554-322">428x240p 15fps 0.6 Mbit 串流。</span><span class="sxs-lookup"><span data-stu-id="07554-322">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="07554-323">網路功能</span><span class="sxs-lookup"><span data-stu-id="07554-323">Networking</span></span>

<span data-ttu-id="07554-324">**/api/networking/ipconfig （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-324">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="07554-325">取得目前的 ip 設定</span><span class="sxs-lookup"><span data-stu-id="07554-325">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="07554-326">作業系統資訊</span><span class="sxs-lookup"><span data-stu-id="07554-326">OS Information</span></span>

<span data-ttu-id="07554-327">**/api/os/info （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-327">**/api/os/info (GET)**</span></span>

<span data-ttu-id="07554-328">取得作業系統資訊</span><span class="sxs-lookup"><span data-stu-id="07554-328">Gets operating system information</span></span>

<span data-ttu-id="07554-329">**/api/os/machinename （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-329">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="07554-330">取得電腦名稱稱</span><span class="sxs-lookup"><span data-stu-id="07554-330">Gets the machine name</span></span>

<span data-ttu-id="07554-331">**/api/os/machinename （POST）**</span><span class="sxs-lookup"><span data-stu-id="07554-331">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="07554-332">設定電腦名稱稱</span><span class="sxs-lookup"><span data-stu-id="07554-332">Sets the machine name</span></span>

<span data-ttu-id="07554-333">參數</span><span class="sxs-lookup"><span data-stu-id="07554-333">Parameters</span></span>
* <span data-ttu-id="07554-334">名稱：新的電腦名稱稱，hex64 編碼，設定為</span><span class="sxs-lookup"><span data-stu-id="07554-334">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="07554-335">效能資料</span><span class="sxs-lookup"><span data-stu-id="07554-335">Performance data</span></span>

<span data-ttu-id="07554-336">**/api/resourcemanager/processes （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-336">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="07554-337">傳回執行中進程的清單，並提供詳細資料</span><span class="sxs-lookup"><span data-stu-id="07554-337">Returns the list of running processes with details</span></span>

<span data-ttu-id="07554-338">傳回資料</span><span class="sxs-lookup"><span data-stu-id="07554-338">Return data</span></span>
* <span data-ttu-id="07554-339">JSON，內含進程的清單和每個進程的詳細資料</span><span class="sxs-lookup"><span data-stu-id="07554-339">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="07554-340">**/api/resourcemanager/systemperf （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-340">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="07554-341">傳回系統效能統計資料（i/o 讀取/寫入、記憶體統計等）。</span><span class="sxs-lookup"><span data-stu-id="07554-341">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="07554-342">傳回資料</span><span class="sxs-lookup"><span data-stu-id="07554-342">Return data</span></span>
* <span data-ttu-id="07554-343">具有系統資訊的 JSON： CPU、GPU、記憶體、網路、IO</span><span class="sxs-lookup"><span data-stu-id="07554-343">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="07554-344">Power</span><span class="sxs-lookup"><span data-stu-id="07554-344">Power</span></span>

<span data-ttu-id="07554-345">**/api/power/battery （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-345">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="07554-346">取得目前的電池狀態</span><span class="sxs-lookup"><span data-stu-id="07554-346">Gets the current battery state</span></span>

<span data-ttu-id="07554-347">**/api/power/state （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-347">**/api/power/state (GET)**</span></span>

<span data-ttu-id="07554-348">檢查系統是否處於低電源狀態</span><span class="sxs-lookup"><span data-stu-id="07554-348">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="07554-349">遠端控制</span><span class="sxs-lookup"><span data-stu-id="07554-349">Remote Control</span></span>

<span data-ttu-id="07554-350">**/api/control/restart （POST）**</span><span class="sxs-lookup"><span data-stu-id="07554-350">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="07554-351">重新開機目標裝置</span><span class="sxs-lookup"><span data-stu-id="07554-351">Restarts the target device</span></span>

<span data-ttu-id="07554-352">**/api/control/shutdown （POST）**</span><span class="sxs-lookup"><span data-stu-id="07554-352">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="07554-353">關閉目標裝置</span><span class="sxs-lookup"><span data-stu-id="07554-353">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="07554-354">工作管理員</span><span class="sxs-lookup"><span data-stu-id="07554-354">Task Manager</span></span>

<span data-ttu-id="07554-355">**/api/taskmanager/app （DELETE）**</span><span class="sxs-lookup"><span data-stu-id="07554-355">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="07554-356">停止現代化應用程式</span><span class="sxs-lookup"><span data-stu-id="07554-356">Stops a modern app</span></span>

<span data-ttu-id="07554-357">參數</span><span class="sxs-lookup"><span data-stu-id="07554-357">Parameters</span></span>
* <span data-ttu-id="07554-358">package：應用程式套件的完整名稱，hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="07554-358">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="07554-359">forcestop：強制停止所有進程（= 是）</span><span class="sxs-lookup"><span data-stu-id="07554-359">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="07554-360">**/api/taskmanager/app （POST）**</span><span class="sxs-lookup"><span data-stu-id="07554-360">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="07554-361">啟動現代化應用程式</span><span class="sxs-lookup"><span data-stu-id="07554-361">Starts a modern app</span></span>

<span data-ttu-id="07554-362">參數</span><span class="sxs-lookup"><span data-stu-id="07554-362">Parameters</span></span>
* <span data-ttu-id="07554-363">appid：要啟動之應用程式的 PRAID，hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="07554-363">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="07554-364">package：應用程式套件的完整名稱，hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="07554-364">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="07554-365">WiFi 管理</span><span class="sxs-lookup"><span data-stu-id="07554-365">WiFi Management</span></span>

<span data-ttu-id="07554-366">**/api/wifi/interfaces （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-366">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="07554-367">列舉無線網路介面</span><span class="sxs-lookup"><span data-stu-id="07554-367">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="07554-368">傳回資料</span><span class="sxs-lookup"><span data-stu-id="07554-368">Return data</span></span>
* <span data-ttu-id="07554-369">具有詳細資料的無線介面清單（GUID、描述等等）</span><span class="sxs-lookup"><span data-stu-id="07554-369">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="07554-370">**/api/wifi/network （DELETE）**</span><span class="sxs-lookup"><span data-stu-id="07554-370">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="07554-371">刪除與指定之介面上的網路相關聯的設定檔</span><span class="sxs-lookup"><span data-stu-id="07554-371">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="07554-372">參數</span><span class="sxs-lookup"><span data-stu-id="07554-372">Parameters</span></span>
* <span data-ttu-id="07554-373">介面：網路介面 guid</span><span class="sxs-lookup"><span data-stu-id="07554-373">interface : network interface guid</span></span>
* <span data-ttu-id="07554-374">設定檔：設定檔名稱</span><span class="sxs-lookup"><span data-stu-id="07554-374">profile : profile name</span></span>

<span data-ttu-id="07554-375">**/api/wifi/networks （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-375">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="07554-376">列舉指定網路介面上的無線網路</span><span class="sxs-lookup"><span data-stu-id="07554-376">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="07554-377">參數</span><span class="sxs-lookup"><span data-stu-id="07554-377">Parameters</span></span>
* <span data-ttu-id="07554-378">介面：網路介面 guid</span><span class="sxs-lookup"><span data-stu-id="07554-378">interface : network interface guid</span></span>

<span data-ttu-id="07554-379">傳回資料</span><span class="sxs-lookup"><span data-stu-id="07554-379">Return data</span></span>
* <span data-ttu-id="07554-380">在網路介面上找到的無線網路清單，並提供詳細資料</span><span class="sxs-lookup"><span data-stu-id="07554-380">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="07554-381">**/api/wifi/network （POST）**</span><span class="sxs-lookup"><span data-stu-id="07554-381">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="07554-382">連接或中斷連線到指定介面上的網路</span><span class="sxs-lookup"><span data-stu-id="07554-382">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="07554-383">參數</span><span class="sxs-lookup"><span data-stu-id="07554-383">Parameters</span></span>
* <span data-ttu-id="07554-384">介面：網路介面 guid</span><span class="sxs-lookup"><span data-stu-id="07554-384">interface : network interface guid</span></span>
* <span data-ttu-id="07554-385">ssid：用來連線到的 ssid （hex64 編碼）</span><span class="sxs-lookup"><span data-stu-id="07554-385">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="07554-386">op：連接或中斷連線</span><span class="sxs-lookup"><span data-stu-id="07554-386">op : connect or disconnect</span></span>
* <span data-ttu-id="07554-387">createprofile：是或否</span><span class="sxs-lookup"><span data-stu-id="07554-387">createprofile : yes or no</span></span>
* <span data-ttu-id="07554-388">金鑰：共用金鑰，hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="07554-388">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="07554-389">Windows Performance Recorder</span><span class="sxs-lookup"><span data-stu-id="07554-389">Windows Performance Recorder</span></span>

<span data-ttu-id="07554-390">**/api/wpr/customtrace （POST）**</span><span class="sxs-lookup"><span data-stu-id="07554-390">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="07554-391">上傳 WPR 設定檔，並使用上傳的設定檔開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="07554-391">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="07554-392">Payload</span><span class="sxs-lookup"><span data-stu-id="07554-392">Payload</span></span>
* <span data-ttu-id="07554-393">多部分符合的 HTTP 主體</span><span class="sxs-lookup"><span data-stu-id="07554-393">multi-part conforming http body</span></span>

<span data-ttu-id="07554-394">傳回資料</span><span class="sxs-lookup"><span data-stu-id="07554-394">Return data</span></span>
* <span data-ttu-id="07554-395">傳回 WPR 會話狀態。</span><span class="sxs-lookup"><span data-stu-id="07554-395">Returns the WPR session status.</span></span>

<span data-ttu-id="07554-396">**/api/wpr/status （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-396">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="07554-397">抓取 WPR 會話的狀態</span><span class="sxs-lookup"><span data-stu-id="07554-397">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="07554-398">傳回資料</span><span class="sxs-lookup"><span data-stu-id="07554-398">Return data</span></span>
* <span data-ttu-id="07554-399">WPR 會話狀態。</span><span class="sxs-lookup"><span data-stu-id="07554-399">WPR session status.</span></span>

<span data-ttu-id="07554-400">**/api/wpr/trace （GET）**</span><span class="sxs-lookup"><span data-stu-id="07554-400">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="07554-401">停止 WPR （效能）追蹤會話</span><span class="sxs-lookup"><span data-stu-id="07554-401">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="07554-402">傳回資料</span><span class="sxs-lookup"><span data-stu-id="07554-402">Return data</span></span>
* <span data-ttu-id="07554-403">傳回追蹤 ETL 檔案</span><span class="sxs-lookup"><span data-stu-id="07554-403">Returns the trace ETL file</span></span>

<span data-ttu-id="07554-404">**/api/wpr/trace （POST）**</span><span class="sxs-lookup"><span data-stu-id="07554-404">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="07554-405">啟動 WPR （效能）追蹤會話</span><span class="sxs-lookup"><span data-stu-id="07554-405">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="07554-406">參數</span><span class="sxs-lookup"><span data-stu-id="07554-406">Parameters</span></span>
* <span data-ttu-id="07554-407">設定檔：設定檔名稱。</span><span class="sxs-lookup"><span data-stu-id="07554-407">profile : Profile name.</span></span> <span data-ttu-id="07554-408">可用的設定檔會儲存在 perfprofiles/profiles 中。 json</span><span class="sxs-lookup"><span data-stu-id="07554-408">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="07554-409">傳回資料</span><span class="sxs-lookup"><span data-stu-id="07554-409">Return data</span></span>
* <span data-ttu-id="07554-410">在啟動時，會傳回 WPR 會話狀態。</span><span class="sxs-lookup"><span data-stu-id="07554-410">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="07554-411">請參閱</span><span class="sxs-lookup"><span data-stu-id="07554-411">See also</span></span>
* [<span data-ttu-id="07554-412">使用 Windows 裝置入口網站</span><span class="sxs-lookup"><span data-stu-id="07554-412">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="07554-413">裝置入口網站核心 API 參考（UWP）</span><span class="sxs-lookup"><span data-stu-id="07554-413">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
