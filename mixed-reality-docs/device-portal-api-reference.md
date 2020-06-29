---
title: 裝置入口網站 API 參照
description: HoloLens 上 Windows 裝置入口網站的 API 參考
author: hamalawi
ms.author: moelhama
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens，Windows 裝置入口網站，API
ms.openlocfilehash: b9b9ada49b4f9810dc97c9da2873d4ccb60df424
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85441795"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="bd726-104">裝置入口網站 API 參照</span><span class="sxs-lookup"><span data-stu-id="bd726-104">Device portal API reference</span></span>

<span data-ttu-id="bd726-105">[Windows 裝置入口網站](using-the-windows-device-portal.md)中的所有專案都是以 REST API 為基礎，您可以用它來存取資料並以程式設計方式控制您的裝置。</span><span class="sxs-lookup"><span data-stu-id="bd726-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="bd726-106">應用程式部署常見問題</span><span class="sxs-lookup"><span data-stu-id="bd726-106">App deloyment</span></span>

<span data-ttu-id="bd726-107">**/api/app/packagemanager/package （DELETE）**</span><span class="sxs-lookup"><span data-stu-id="bd726-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="bd726-108">卸載應用程式</span><span class="sxs-lookup"><span data-stu-id="bd726-108">Uninstalls an app</span></span>

<span data-ttu-id="bd726-109">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-109">Parameters</span></span>
* <span data-ttu-id="bd726-110">package：要卸載之封裝的檔案名。</span><span class="sxs-lookup"><span data-stu-id="bd726-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="bd726-111">**/api/app/packagemanager/package （POST）**</span><span class="sxs-lookup"><span data-stu-id="bd726-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="bd726-112">安裝應用程式</span><span class="sxs-lookup"><span data-stu-id="bd726-112">Installs an App</span></span>

<span data-ttu-id="bd726-113">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-113">Parameters</span></span>
* <span data-ttu-id="bd726-114">package：要安裝之封裝的檔案名。</span><span class="sxs-lookup"><span data-stu-id="bd726-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="bd726-115">Payload</span><span class="sxs-lookup"><span data-stu-id="bd726-115">Payload</span></span>
* <span data-ttu-id="bd726-116">多部分符合的 HTTP 主體</span><span class="sxs-lookup"><span data-stu-id="bd726-116">multi-part conforming http body</span></span>

<span data-ttu-id="bd726-117">**/api/app/packagemanager/packages （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="bd726-118">抓取系統上已安裝的應用程式清單，並提供詳細資料</span><span class="sxs-lookup"><span data-stu-id="bd726-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="bd726-119">傳回資料</span><span class="sxs-lookup"><span data-stu-id="bd726-119">Return data</span></span>
* <span data-ttu-id="bd726-120">包含詳細資料的已安裝套件清單</span><span class="sxs-lookup"><span data-stu-id="bd726-120">List of installed packages with details</span></span>

<span data-ttu-id="bd726-121">**/api/app/packagemanager/state （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="bd726-122">取得進行中應用程式安裝的狀態</span><span class="sxs-lookup"><span data-stu-id="bd726-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="bd726-123">傾印集合</span><span class="sxs-lookup"><span data-stu-id="bd726-123">Dump collection</span></span>

<span data-ttu-id="bd726-124">**/api/debug/dump/usermode/crashcontrol （DELETE）**</span><span class="sxs-lookup"><span data-stu-id="bd726-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="bd726-125">停用側載應用程式的損毀傾印集合</span><span class="sxs-lookup"><span data-stu-id="bd726-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="bd726-126">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-126">Parameters</span></span>
* <span data-ttu-id="bd726-127">packageFullname：封裝名稱</span><span class="sxs-lookup"><span data-stu-id="bd726-127">packageFullname : package name</span></span>

<span data-ttu-id="bd726-128">**/api/debug/dump/usermode/crashcontrol （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="bd726-129">取得側載 apps 損毀傾印集合的設定</span><span class="sxs-lookup"><span data-stu-id="bd726-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="bd726-130">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-130">Parameters</span></span>
* <span data-ttu-id="bd726-131">packageFullname：封裝名稱</span><span class="sxs-lookup"><span data-stu-id="bd726-131">packageFullname : package name</span></span>

<span data-ttu-id="bd726-132">**/api/debug/dump/usermode/crashcontrol （POST）**</span><span class="sxs-lookup"><span data-stu-id="bd726-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="bd726-133">啟用和設定側載應用程式的傾印控制設定</span><span class="sxs-lookup"><span data-stu-id="bd726-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="bd726-134">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-134">Parameters</span></span>
* <span data-ttu-id="bd726-135">packageFullname：封裝名稱</span><span class="sxs-lookup"><span data-stu-id="bd726-135">packageFullname : package name</span></span>

<span data-ttu-id="bd726-136">**/api/debug/dump/usermode/crashdump （DELETE）**</span><span class="sxs-lookup"><span data-stu-id="bd726-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="bd726-137">刪除側載應用程式的損毀傾印</span><span class="sxs-lookup"><span data-stu-id="bd726-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="bd726-138">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-138">Parameters</span></span>
* <span data-ttu-id="bd726-139">packageFullname：封裝名稱</span><span class="sxs-lookup"><span data-stu-id="bd726-139">packageFullname : package name</span></span>
* <span data-ttu-id="bd726-140">檔案名：傾印檔案名</span><span class="sxs-lookup"><span data-stu-id="bd726-140">fileName : dump file name</span></span>

<span data-ttu-id="bd726-141">**/api/debug/dump/usermode/crashdump （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="bd726-142">抓取側載應用程式的損毀傾印</span><span class="sxs-lookup"><span data-stu-id="bd726-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="bd726-143">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-143">Parameters</span></span>
* <span data-ttu-id="bd726-144">packageFullname：封裝名稱</span><span class="sxs-lookup"><span data-stu-id="bd726-144">packageFullname : package name</span></span>
* <span data-ttu-id="bd726-145">檔案名：傾印檔案名</span><span class="sxs-lookup"><span data-stu-id="bd726-145">fileName : dump file name</span></span>

<span data-ttu-id="bd726-146">傳回資料</span><span class="sxs-lookup"><span data-stu-id="bd726-146">Return data</span></span>
* <span data-ttu-id="bd726-147">傾印檔案。</span><span class="sxs-lookup"><span data-stu-id="bd726-147">Dump file.</span></span> <span data-ttu-id="bd726-148">使用 WinDbg 或 Visual Studio 檢查</span><span class="sxs-lookup"><span data-stu-id="bd726-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="bd726-149">**/api/debug/dump/usermode/dumps （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="bd726-150">傳回側載應用程式的所有損毀傾印清單</span><span class="sxs-lookup"><span data-stu-id="bd726-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="bd726-151">傳回資料</span><span class="sxs-lookup"><span data-stu-id="bd726-151">Return data</span></span>
* <span data-ttu-id="bd726-152">每一端已載入應用程式的損毀傾印清單</span><span class="sxs-lookup"><span data-stu-id="bd726-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="bd726-153">ETW</span><span class="sxs-lookup"><span data-stu-id="bd726-153">ETW</span></span>

<span data-ttu-id="bd726-154">**/api/etw/providers （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="bd726-155">列舉已註冊的提供者</span><span class="sxs-lookup"><span data-stu-id="bd726-155">Enumerates registered providers</span></span>

<span data-ttu-id="bd726-156">傳回資料</span><span class="sxs-lookup"><span data-stu-id="bd726-156">Return data</span></span>
* <span data-ttu-id="bd726-157">提供者清單、易記名稱和 GUID</span><span class="sxs-lookup"><span data-stu-id="bd726-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="bd726-158">**/api/etw/session/realtime （GET/WebSocket）**</span><span class="sxs-lookup"><span data-stu-id="bd726-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="bd726-159">建立即時 ETW 會話;透過 websocket 管理。</span><span class="sxs-lookup"><span data-stu-id="bd726-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="bd726-160">傳回資料</span><span class="sxs-lookup"><span data-stu-id="bd726-160">Return data</span></span>
* <span data-ttu-id="bd726-161">來自已啟用提供者的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="bd726-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="bd726-162">全像攝影版 OS</span><span class="sxs-lookup"><span data-stu-id="bd726-162">Holographic OS</span></span>

<span data-ttu-id="bd726-163">**/api/holographic/os/etw/customproviders （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="bd726-164">傳回未向系統註冊的 HoloLens 特定 ETW 提供者清單</span><span class="sxs-lookup"><span data-stu-id="bd726-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="bd726-165">**/api/holographic/os/services （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="bd726-166">傳回所有執行中服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="bd726-166">Returns the states of all services running.</span></span>

<span data-ttu-id="bd726-167">**/api/holographic/os/settings/ipd （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="bd726-168">取得以毫米為單位的儲存 IPD （Interpupillary 距離）</span><span class="sxs-lookup"><span data-stu-id="bd726-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="bd726-169">**/api/holographic/os/settings/ipd （POST）**</span><span class="sxs-lookup"><span data-stu-id="bd726-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="bd726-170">設定 IPD</span><span class="sxs-lookup"><span data-stu-id="bd726-170">Sets the IPD</span></span>

<span data-ttu-id="bd726-171">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-171">Parameters</span></span>
* <span data-ttu-id="bd726-172">ipd：要以毫米設定的新 IPD 值</span><span class="sxs-lookup"><span data-stu-id="bd726-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="bd726-173">**/api/holographic/os/webmanagement/settings/HTTPs （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="bd726-174">取得裝置入口網站的 HTTPS 需求</span><span class="sxs-lookup"><span data-stu-id="bd726-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="bd726-175">**/api/holographic/os/webmanagement/settings/HTTPs （POST）**</span><span class="sxs-lookup"><span data-stu-id="bd726-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="bd726-176">設定裝置入口網站的 HTTPS 需求</span><span class="sxs-lookup"><span data-stu-id="bd726-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="bd726-177">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-177">Parameters</span></span>
* <span data-ttu-id="bd726-178">必要：是，否或預設值</span><span class="sxs-lookup"><span data-stu-id="bd726-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="bd726-179">全像攝影</span><span class="sxs-lookup"><span data-stu-id="bd726-179">Holographic Perception</span></span>

<span data-ttu-id="bd726-180">**/api/holographic/perception/client （GET/WebSocket）**</span><span class="sxs-lookup"><span data-stu-id="bd726-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="bd726-181">接受 websocket 升級，並執行將更新以 30 fps 傳送的感知用戶端。</span><span class="sxs-lookup"><span data-stu-id="bd726-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="bd726-182">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-182">Parameters</span></span>
* <span data-ttu-id="bd726-183">clientmode：「作用中」會在無法被動建立時強制執行視覺化追蹤模式</span><span class="sxs-lookup"><span data-stu-id="bd726-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="bd726-184">全像熱</span><span class="sxs-lookup"><span data-stu-id="bd726-184">Holographic Thermal</span></span>

<span data-ttu-id="bd726-185">**/api/holographic/thermal/stage （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="bd726-186">取得裝置的散熱階段（0個正常、1個暖、2個重大）</span><span class="sxs-lookup"><span data-stu-id="bd726-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="bd726-187">認知模擬控制</span><span class="sxs-lookup"><span data-stu-id="bd726-187">Perception Simulation Control</span></span>

<span data-ttu-id="bd726-188">**/api/holographic/simulation/control/mode （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="bd726-189">取得模擬模式</span><span class="sxs-lookup"><span data-stu-id="bd726-189">Get the simulation mode</span></span>

<span data-ttu-id="bd726-190">**/api/holographic/simulation/control/mode （POST）**</span><span class="sxs-lookup"><span data-stu-id="bd726-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="bd726-191">設定模擬模式</span><span class="sxs-lookup"><span data-stu-id="bd726-191">Set the simulation mode</span></span>

<span data-ttu-id="bd726-192">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-192">Parameters</span></span>
* <span data-ttu-id="bd726-193">模式：模擬模式：預設、模擬、遠端、舊版</span><span class="sxs-lookup"><span data-stu-id="bd726-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="bd726-194">**/api/holographic/simulation/control/stream （DELETE）**</span><span class="sxs-lookup"><span data-stu-id="bd726-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="bd726-195">刪除控制資料流程。</span><span class="sxs-lookup"><span data-stu-id="bd726-195">Delete a control stream.</span></span>

<span data-ttu-id="bd726-196">**/api/holographic/simulation/control/stream （GET/WebSocket）**</span><span class="sxs-lookup"><span data-stu-id="bd726-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="bd726-197">開啟控制項資料流程的 web 通訊端連接。</span><span class="sxs-lookup"><span data-stu-id="bd726-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="bd726-198">**/api/holographic/simulation/control/stream （POST）**</span><span class="sxs-lookup"><span data-stu-id="bd726-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="bd726-199">建立控制資料流程（需要優先權）或將資料張貼到建立的資料流程（需要 streamId）。</span><span class="sxs-lookup"><span data-stu-id="bd726-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="bd726-200">張貼的資料應該是「應用程式/八位串流」類型。</span><span class="sxs-lookup"><span data-stu-id="bd726-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="bd726-201">**/api/holographic/simulation/display/stream （GET/WebSocket）**</span><span class="sxs-lookup"><span data-stu-id="bd726-201">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="bd726-202">要求模擬影片串流，其中包含在「模擬」模式下呈現給系統顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="bd726-202">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="bd726-203">簡單的格式描述元標頭會一開始傳送，後面接著 h.264 編碼材質，每一個標頭前面會加上指示眼睛索引和材質大小的標題。</span><span class="sxs-lookup"><span data-stu-id="bd726-203">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="bd726-204">認知模擬播放</span><span class="sxs-lookup"><span data-stu-id="bd726-204">Perception Simulation Playback</span></span>

<span data-ttu-id="bd726-205">**/api/holographic/simulation/playback/file （DELETE）**</span><span class="sxs-lookup"><span data-stu-id="bd726-205">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="bd726-206">刪除錄製。</span><span class="sxs-lookup"><span data-stu-id="bd726-206">Delete a recording.</span></span>

<span data-ttu-id="bd726-207">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-207">Parameters</span></span>
* <span data-ttu-id="bd726-208">錄製：要刪除的記錄名稱。</span><span class="sxs-lookup"><span data-stu-id="bd726-208">recording : Name of recording to delete.</span></span>

<span data-ttu-id="bd726-209">**/api/holographic/simulation/playback/file （POST）**</span><span class="sxs-lookup"><span data-stu-id="bd726-209">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="bd726-210">上傳記錄。</span><span class="sxs-lookup"><span data-stu-id="bd726-210">Upload a recording.</span></span>

<span data-ttu-id="bd726-211">**/api/holographic/simulation/playback/files （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-211">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="bd726-212">取得所有錄製。</span><span class="sxs-lookup"><span data-stu-id="bd726-212">Get all recordings.</span></span>

<span data-ttu-id="bd726-213">**/api/holographic/simulation/playback/session （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-213">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="bd726-214">取得錄製的目前播放狀態。</span><span class="sxs-lookup"><span data-stu-id="bd726-214">Get the current playback state of a recording.</span></span>

<span data-ttu-id="bd726-215">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-215">Parameters</span></span>
* <span data-ttu-id="bd726-216">錄製：錄製的名稱。</span><span class="sxs-lookup"><span data-stu-id="bd726-216">recording : Name of recording.</span></span>

<span data-ttu-id="bd726-217">**/api/holographic/simulation/playback/session/file （DELETE）**</span><span class="sxs-lookup"><span data-stu-id="bd726-217">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="bd726-218">卸載記錄。</span><span class="sxs-lookup"><span data-stu-id="bd726-218">Unload a recording.</span></span>

<span data-ttu-id="bd726-219">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-219">Parameters</span></span>
* <span data-ttu-id="bd726-220">錄製：要卸載的記錄名稱。</span><span class="sxs-lookup"><span data-stu-id="bd726-220">recording : Name of recording to unload.</span></span>

<span data-ttu-id="bd726-221">**/api/holographic/simulation/playback/session/file （POST）**</span><span class="sxs-lookup"><span data-stu-id="bd726-221">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="bd726-222">載入錄製。</span><span class="sxs-lookup"><span data-stu-id="bd726-222">Load a recording.</span></span>

<span data-ttu-id="bd726-223">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-223">Parameters</span></span>
* <span data-ttu-id="bd726-224">錄製：要載入的記錄名稱。</span><span class="sxs-lookup"><span data-stu-id="bd726-224">recording : Name of recording to load.</span></span>

<span data-ttu-id="bd726-225">**/api/holographic/simulation/playback/session/files （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-225">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="bd726-226">取得所有已載入的錄製。</span><span class="sxs-lookup"><span data-stu-id="bd726-226">Get all loaded recordings.</span></span>

<span data-ttu-id="bd726-227">**/api/holographic/simulation/playback/session/pause （POST）**</span><span class="sxs-lookup"><span data-stu-id="bd726-227">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="bd726-228">暫停錄製。</span><span class="sxs-lookup"><span data-stu-id="bd726-228">Pause a recording.</span></span>

<span data-ttu-id="bd726-229">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-229">Parameters</span></span>
* <span data-ttu-id="bd726-230">錄製：錄製的名稱。</span><span class="sxs-lookup"><span data-stu-id="bd726-230">recording : Name of recording.</span></span>

<span data-ttu-id="bd726-231">**/api/holographic/simulation/playback/session/play （POST）**</span><span class="sxs-lookup"><span data-stu-id="bd726-231">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="bd726-232">播放錄製。</span><span class="sxs-lookup"><span data-stu-id="bd726-232">Play a recording.</span></span>

<span data-ttu-id="bd726-233">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-233">Parameters</span></span>
* <span data-ttu-id="bd726-234">錄製：錄製的名稱。</span><span class="sxs-lookup"><span data-stu-id="bd726-234">recording : Name of recording.</span></span>

<span data-ttu-id="bd726-235">**/api/holographic/simulation/playback/session/stop （POST）**</span><span class="sxs-lookup"><span data-stu-id="bd726-235">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="bd726-236">停止錄製。</span><span class="sxs-lookup"><span data-stu-id="bd726-236">Stop a recording.</span></span>

<span data-ttu-id="bd726-237">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-237">Parameters</span></span>
* <span data-ttu-id="bd726-238">錄製：錄製的名稱。</span><span class="sxs-lookup"><span data-stu-id="bd726-238">recording : Name of recording.</span></span>

<span data-ttu-id="bd726-239">**/api/holographic/simulation/playback/session/types （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-239">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="bd726-240">取得已載入記錄中的資料類型。</span><span class="sxs-lookup"><span data-stu-id="bd726-240">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="bd726-241">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-241">Parameters</span></span>
* <span data-ttu-id="bd726-242">錄製：錄製的名稱。</span><span class="sxs-lookup"><span data-stu-id="bd726-242">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="bd726-243">認知模擬記錄</span><span class="sxs-lookup"><span data-stu-id="bd726-243">Perception Simulation Recording</span></span>

<span data-ttu-id="bd726-244">**/api/holographic/simulation/recording/start （POST）**</span><span class="sxs-lookup"><span data-stu-id="bd726-244">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="bd726-245">開始錄製。</span><span class="sxs-lookup"><span data-stu-id="bd726-245">Start a recording.</span></span> <span data-ttu-id="bd726-246">一次只能有一個使用中的錄製。</span><span class="sxs-lookup"><span data-stu-id="bd726-246">Only a single recording can be active at once.</span></span> <span data-ttu-id="bd726-247">必須設定 head、手、spatialMapping 或環境之一。</span><span class="sxs-lookup"><span data-stu-id="bd726-247">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="bd726-248">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-248">Parameters</span></span>
* <span data-ttu-id="bd726-249">head：設定為1以記錄 head 資料。</span><span class="sxs-lookup"><span data-stu-id="bd726-249">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="bd726-250">實習：設定為1以記錄手資料。</span><span class="sxs-lookup"><span data-stu-id="bd726-250">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="bd726-251">spatialMapping：設定為1以記錄空間對應。</span><span class="sxs-lookup"><span data-stu-id="bd726-251">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="bd726-252">環境：設定為1以記錄環境資料。</span><span class="sxs-lookup"><span data-stu-id="bd726-252">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="bd726-253">名稱：記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="bd726-253">name : Name of the recording.</span></span>
* <span data-ttu-id="bd726-254">singleSpatialMappingFrame：設定為1，只記錄一個空間對應框架。</span><span class="sxs-lookup"><span data-stu-id="bd726-254">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="bd726-255">**/api/holographic/simulation/recording/status （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-255">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="bd726-256">取得錄製狀態。</span><span class="sxs-lookup"><span data-stu-id="bd726-256">Get recording state.</span></span>

<span data-ttu-id="bd726-257">**/api/holographic/simulation/recording/stop （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-257">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="bd726-258">停止目前的錄製。</span><span class="sxs-lookup"><span data-stu-id="bd726-258">Stop the current recording.</span></span> <span data-ttu-id="bd726-259">記錄將會以檔案的形式傳回。</span><span class="sxs-lookup"><span data-stu-id="bd726-259">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="bd726-260">混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="bd726-260">Mixed Reality Capture</span></span>

<span data-ttu-id="bd726-261">**/api/holographic/mrc/file （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-261">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="bd726-262">從裝置下載混合的現實檔案。</span><span class="sxs-lookup"><span data-stu-id="bd726-262">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="bd726-263">使用 op = 資料流程查詢參數進行串流處理。</span><span class="sxs-lookup"><span data-stu-id="bd726-263">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="bd726-264">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-264">Parameters</span></span>
* <span data-ttu-id="bd726-265">filename：要取得之影片檔案的名稱、hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="bd726-265">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="bd726-266">op：資料流程</span><span class="sxs-lookup"><span data-stu-id="bd726-266">op : stream</span></span>

<span data-ttu-id="bd726-267">**/api/holographic/mrc/file （DELETE）**</span><span class="sxs-lookup"><span data-stu-id="bd726-267">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="bd726-268">從裝置中刪除混合現實記錄。</span><span class="sxs-lookup"><span data-stu-id="bd726-268">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="bd726-269">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-269">Parameters</span></span>
* <span data-ttu-id="bd726-270">filename：要刪除之檔案的名稱、hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="bd726-270">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="bd726-271">**/api/holographic/mrc/files （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-271">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="bd726-272">傳回儲存在裝置上的混合 reality 檔案清單</span><span class="sxs-lookup"><span data-stu-id="bd726-272">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="bd726-273">**/api/holographic/mrc/photo （POST）**</span><span class="sxs-lookup"><span data-stu-id="bd726-273">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="bd726-274">採用混合的現實相片，並在裝置上建立檔案</span><span class="sxs-lookup"><span data-stu-id="bd726-274">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="bd726-275">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-275">Parameters</span></span>
* <span data-ttu-id="bd726-276">hololens： capture 全息影像： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="bd726-276">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="bd726-277">pv： capture PV 攝影機： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="bd726-277">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="bd726-278">RenderFromCamera：（僅限 HoloLens 2）從相片/攝影機的觀點呈現： true 或 false （預設為 true）</span><span class="sxs-lookup"><span data-stu-id="bd726-278">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="bd726-279">**/api/holographic/mrc/settings （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-279">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="bd726-280">取得預設的混合現實捕捉設定</span><span class="sxs-lookup"><span data-stu-id="bd726-280">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="bd726-281">**/api/holographic/mrc/settings （POST）**</span><span class="sxs-lookup"><span data-stu-id="bd726-281">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="bd726-282">設定預設的混合現實捕捉設定。</span><span class="sxs-lookup"><span data-stu-id="bd726-282">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="bd726-283">其中部分設定會套用至系統的 MRC 相片和影片捕獲。</span><span class="sxs-lookup"><span data-stu-id="bd726-283">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="bd726-284">**/api/holographic/mrc/status （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-284">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="bd726-285">取得 Windows 裝置入口網站中的混合現實 capture 的狀態。</span><span class="sxs-lookup"><span data-stu-id="bd726-285">Gets the state of mixed reality capture within the Windows Device Portal.</span></span>

<span data-ttu-id="bd726-286">***回應***</span><span class="sxs-lookup"><span data-stu-id="bd726-286">***Response***</span></span>

<span data-ttu-id="bd726-287">回應包含 JSON 屬性，指出 Windows 裝置入口網站是否正在錄製影片。</span><span class="sxs-lookup"><span data-stu-id="bd726-287">The response contains a JSON property indicating if Windows Device Portal is recording video or not.</span></span>

``` javascript
{"IsRecording" : boolean}
```

<span data-ttu-id="bd726-288">**/api/holographic/mrc/thumbnail （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-288">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="bd726-289">取得指定檔案的縮圖影像。</span><span class="sxs-lookup"><span data-stu-id="bd726-289">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="bd726-290">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-290">Parameters</span></span>
* <span data-ttu-id="bd726-291">檔案名：要為其要求縮圖之檔案的名稱、hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="bd726-291">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="bd726-292">**/api/holographic/mrc/video/control/start （POST）**</span><span class="sxs-lookup"><span data-stu-id="bd726-292">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="bd726-293">開始進行混合的事實記錄</span><span class="sxs-lookup"><span data-stu-id="bd726-293">Starts a mixed reality recording</span></span>

<span data-ttu-id="bd726-294">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-294">Parameters</span></span>
* <span data-ttu-id="bd726-295">hololens： capture 全息影像： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="bd726-295">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="bd726-296">pv： capture PV 攝影機： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="bd726-296">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="bd726-297">mic： capture 麥克風： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="bd726-297">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="bd726-298">回送：捕獲應用程式音訊： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="bd726-298">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="bd726-299">RenderFromCamera：（僅限 HoloLens 2）從相片/攝影機的觀點呈現： true 或 false （預設為 true）</span><span class="sxs-lookup"><span data-stu-id="bd726-299">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="bd726-300">vstab：（僅限 HoloLens 2）啟用影片穩定： true 或 false （預設為 true）</span><span class="sxs-lookup"><span data-stu-id="bd726-300">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="bd726-301">vstabbuffer：（僅限 HoloLens 2）影片穩定緩衝區延遲：0到30個框架（預設為15個畫面）</span><span class="sxs-lookup"><span data-stu-id="bd726-301">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="bd726-302">**/api/holographic/mrc/video/control/stop （POST）**</span><span class="sxs-lookup"><span data-stu-id="bd726-302">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="bd726-303">停止目前的混合現實記錄</span><span class="sxs-lookup"><span data-stu-id="bd726-303">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="bd726-304">混合現實串流</span><span class="sxs-lookup"><span data-stu-id="bd726-304">Mixed Reality Streaming</span></span>

<span data-ttu-id="bd726-305">HoloLens 支援透過區塊下載的分散的方式，即時預覽混合現實。</span><span class="sxs-lookup"><span data-stu-id="bd726-305">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="bd726-306">混合的事實資料流會共用一組相同的參數，以控制已捕捉的內容：</span><span class="sxs-lookup"><span data-stu-id="bd726-306">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="bd726-307">hololens： capture 全息影像： true 或 false</span><span class="sxs-lookup"><span data-stu-id="bd726-307">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="bd726-308">pv：捕捉 PV 攝影機： true 或 false</span><span class="sxs-lookup"><span data-stu-id="bd726-308">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="bd726-309">mic：捕捉麥克風： true 或 false</span><span class="sxs-lookup"><span data-stu-id="bd726-309">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="bd726-310">回送：捕獲應用程式音訊： true 或 false</span><span class="sxs-lookup"><span data-stu-id="bd726-310">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="bd726-311">如果未指定這些內容：將會捕捉到全息影像、相片/攝影機和應用程式音訊</span><span class="sxs-lookup"><span data-stu-id="bd726-311">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="bd726-312">如果指定了任何值：未指定的參數將預設為 false</span><span class="sxs-lookup"><span data-stu-id="bd726-312">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="bd726-313">選擇性參數（僅限 HoloLens 2）</span><span class="sxs-lookup"><span data-stu-id="bd726-313">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="bd726-314">RenderFromCamera：從相片/攝影機的角度呈現： true 或 false （預設為 true）</span><span class="sxs-lookup"><span data-stu-id="bd726-314">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="bd726-315">vstab：啟用影片穩定： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="bd726-315">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="bd726-316">vstabbuffer：視頻穩定緩衝區延遲：0到30的框架（預設為15個框架）</span><span class="sxs-lookup"><span data-stu-id="bd726-316">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="bd726-317">**/api/holographic/stream/live.mp4 （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-317">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="bd726-318">解析度為 1280x720p 30fps 5Mbit 串流。</span><span class="sxs-lookup"><span data-stu-id="bd726-318">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="bd726-319">**/api/holographic/stream/live_high.mp4 （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-319">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="bd726-320">解析度為 1280x720p 30fps 5Mbit 串流。</span><span class="sxs-lookup"><span data-stu-id="bd726-320">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="bd726-321">**/api/holographic/stream/live_med.mp4 （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-321">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="bd726-322">854x480p 30fps 2.5 Mbit 串流。</span><span class="sxs-lookup"><span data-stu-id="bd726-322">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="bd726-323">**/api/holographic/stream/live_low.mp4 （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-323">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="bd726-324">428x240p 15fps 0.6 Mbit 串流。</span><span class="sxs-lookup"><span data-stu-id="bd726-324">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="bd726-325">網路功能</span><span class="sxs-lookup"><span data-stu-id="bd726-325">Networking</span></span>

<span data-ttu-id="bd726-326">**/api/networking/ipconfig （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-326">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="bd726-327">取得目前的 ip 設定</span><span class="sxs-lookup"><span data-stu-id="bd726-327">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="bd726-328">作業系統資訊</span><span class="sxs-lookup"><span data-stu-id="bd726-328">OS Information</span></span>

<span data-ttu-id="bd726-329">**/api/os/info （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-329">**/api/os/info (GET)**</span></span>

<span data-ttu-id="bd726-330">取得作業系統資訊</span><span class="sxs-lookup"><span data-stu-id="bd726-330">Gets operating system information</span></span>

<span data-ttu-id="bd726-331">**/api/os/machinename （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-331">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="bd726-332">取得電腦名稱稱</span><span class="sxs-lookup"><span data-stu-id="bd726-332">Gets the machine name</span></span>

<span data-ttu-id="bd726-333">**/api/os/machinename （POST）**</span><span class="sxs-lookup"><span data-stu-id="bd726-333">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="bd726-334">設定電腦名稱稱</span><span class="sxs-lookup"><span data-stu-id="bd726-334">Sets the machine name</span></span>

<span data-ttu-id="bd726-335">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-335">Parameters</span></span>
* <span data-ttu-id="bd726-336">名稱：新的電腦名稱稱，hex64 編碼，設定為</span><span class="sxs-lookup"><span data-stu-id="bd726-336">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="bd726-337">效能資料</span><span class="sxs-lookup"><span data-stu-id="bd726-337">Performance data</span></span>

<span data-ttu-id="bd726-338">**/api/resourcemanager/processes （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-338">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="bd726-339">傳回執行中進程的清單，並提供詳細資料</span><span class="sxs-lookup"><span data-stu-id="bd726-339">Returns the list of running processes with details</span></span>

<span data-ttu-id="bd726-340">傳回資料</span><span class="sxs-lookup"><span data-stu-id="bd726-340">Return data</span></span>
* <span data-ttu-id="bd726-341">JSON，內含進程的清單和每個進程的詳細資料</span><span class="sxs-lookup"><span data-stu-id="bd726-341">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="bd726-342">**/api/resourcemanager/systemperf （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-342">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="bd726-343">傳回系統效能統計資料（i/o 讀取/寫入、記憶體統計等）。</span><span class="sxs-lookup"><span data-stu-id="bd726-343">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="bd726-344">傳回資料</span><span class="sxs-lookup"><span data-stu-id="bd726-344">Return data</span></span>
* <span data-ttu-id="bd726-345">具有系統資訊的 JSON： CPU、GPU、記憶體、網路、IO</span><span class="sxs-lookup"><span data-stu-id="bd726-345">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="bd726-346">電源</span><span class="sxs-lookup"><span data-stu-id="bd726-346">Power</span></span>

<span data-ttu-id="bd726-347">**/api/power/battery （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-347">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="bd726-348">取得目前的電池狀態</span><span class="sxs-lookup"><span data-stu-id="bd726-348">Gets the current battery state</span></span>

<span data-ttu-id="bd726-349">**/api/power/state （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-349">**/api/power/state (GET)**</span></span>

<span data-ttu-id="bd726-350">檢查系統是否處於低電源狀態</span><span class="sxs-lookup"><span data-stu-id="bd726-350">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="bd726-351">遠端控制</span><span class="sxs-lookup"><span data-stu-id="bd726-351">Remote Control</span></span>

<span data-ttu-id="bd726-352">**/api/control/restart （POST）**</span><span class="sxs-lookup"><span data-stu-id="bd726-352">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="bd726-353">重新開機目標裝置</span><span class="sxs-lookup"><span data-stu-id="bd726-353">Restarts the target device</span></span>

<span data-ttu-id="bd726-354">**/api/control/shutdown （POST）**</span><span class="sxs-lookup"><span data-stu-id="bd726-354">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="bd726-355">關閉目標裝置</span><span class="sxs-lookup"><span data-stu-id="bd726-355">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="bd726-356">工作管理員</span><span class="sxs-lookup"><span data-stu-id="bd726-356">Task Manager</span></span>

<span data-ttu-id="bd726-357">**/api/taskmanager/app （DELETE）**</span><span class="sxs-lookup"><span data-stu-id="bd726-357">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="bd726-358">停止現代化應用程式</span><span class="sxs-lookup"><span data-stu-id="bd726-358">Stops a modern app</span></span>

<span data-ttu-id="bd726-359">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-359">Parameters</span></span>
* <span data-ttu-id="bd726-360">package：應用程式套件的完整名稱，hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="bd726-360">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="bd726-361">forcestop：強制停止所有進程（= 是）</span><span class="sxs-lookup"><span data-stu-id="bd726-361">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="bd726-362">**/api/taskmanager/app （POST）**</span><span class="sxs-lookup"><span data-stu-id="bd726-362">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="bd726-363">啟動現代化應用程式</span><span class="sxs-lookup"><span data-stu-id="bd726-363">Starts a modern app</span></span>

<span data-ttu-id="bd726-364">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-364">Parameters</span></span>
* <span data-ttu-id="bd726-365">appid：要啟動之應用程式的 PRAID，hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="bd726-365">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="bd726-366">package：應用程式套件的完整名稱，hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="bd726-366">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="bd726-367">WiFi 管理</span><span class="sxs-lookup"><span data-stu-id="bd726-367">WiFi Management</span></span>

<span data-ttu-id="bd726-368">**/api/wifi/interfaces （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-368">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="bd726-369">列舉無線網路介面</span><span class="sxs-lookup"><span data-stu-id="bd726-369">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="bd726-370">傳回資料</span><span class="sxs-lookup"><span data-stu-id="bd726-370">Return data</span></span>
* <span data-ttu-id="bd726-371">具有詳細資料的無線介面清單（GUID、描述等等）</span><span class="sxs-lookup"><span data-stu-id="bd726-371">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="bd726-372">**/api/wifi/network （DELETE）**</span><span class="sxs-lookup"><span data-stu-id="bd726-372">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="bd726-373">刪除與指定之介面上的網路相關聯的設定檔</span><span class="sxs-lookup"><span data-stu-id="bd726-373">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="bd726-374">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-374">Parameters</span></span>
* <span data-ttu-id="bd726-375">介面：網路介面 guid</span><span class="sxs-lookup"><span data-stu-id="bd726-375">interface : network interface guid</span></span>
* <span data-ttu-id="bd726-376">設定檔：設定檔名稱</span><span class="sxs-lookup"><span data-stu-id="bd726-376">profile : profile name</span></span>

<span data-ttu-id="bd726-377">**/api/wifi/networks （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-377">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="bd726-378">列舉指定網路介面上的無線網路</span><span class="sxs-lookup"><span data-stu-id="bd726-378">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="bd726-379">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-379">Parameters</span></span>
* <span data-ttu-id="bd726-380">介面：網路介面 guid</span><span class="sxs-lookup"><span data-stu-id="bd726-380">interface : network interface guid</span></span>

<span data-ttu-id="bd726-381">傳回資料</span><span class="sxs-lookup"><span data-stu-id="bd726-381">Return data</span></span>
* <span data-ttu-id="bd726-382">在網路介面上找到的無線網路清單，並提供詳細資料</span><span class="sxs-lookup"><span data-stu-id="bd726-382">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="bd726-383">**/api/wifi/network （POST）**</span><span class="sxs-lookup"><span data-stu-id="bd726-383">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="bd726-384">連接或中斷連線到指定介面上的網路</span><span class="sxs-lookup"><span data-stu-id="bd726-384">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="bd726-385">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-385">Parameters</span></span>
* <span data-ttu-id="bd726-386">介面：網路介面 guid</span><span class="sxs-lookup"><span data-stu-id="bd726-386">interface : network interface guid</span></span>
* <span data-ttu-id="bd726-387">ssid：用來連線到的 ssid （hex64 編碼）</span><span class="sxs-lookup"><span data-stu-id="bd726-387">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="bd726-388">op：連接或中斷連線</span><span class="sxs-lookup"><span data-stu-id="bd726-388">op : connect or disconnect</span></span>
* <span data-ttu-id="bd726-389">createprofile：是或否</span><span class="sxs-lookup"><span data-stu-id="bd726-389">createprofile : yes or no</span></span>
* <span data-ttu-id="bd726-390">金鑰：共用金鑰，hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="bd726-390">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="bd726-391">Windows Performance Recorder</span><span class="sxs-lookup"><span data-stu-id="bd726-391">Windows Performance Recorder</span></span>

<span data-ttu-id="bd726-392">**/api/wpr/customtrace （POST）**</span><span class="sxs-lookup"><span data-stu-id="bd726-392">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="bd726-393">上傳 WPR 設定檔，並使用上傳的設定檔開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="bd726-393">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="bd726-394">Payload</span><span class="sxs-lookup"><span data-stu-id="bd726-394">Payload</span></span>
* <span data-ttu-id="bd726-395">多部分符合的 HTTP 主體</span><span class="sxs-lookup"><span data-stu-id="bd726-395">multi-part conforming http body</span></span>

<span data-ttu-id="bd726-396">傳回資料</span><span class="sxs-lookup"><span data-stu-id="bd726-396">Return data</span></span>
* <span data-ttu-id="bd726-397">傳回 WPR 會話狀態。</span><span class="sxs-lookup"><span data-stu-id="bd726-397">Returns the WPR session status.</span></span>

<span data-ttu-id="bd726-398">**/api/wpr/status （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-398">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="bd726-399">抓取 WPR 會話的狀態</span><span class="sxs-lookup"><span data-stu-id="bd726-399">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="bd726-400">傳回資料</span><span class="sxs-lookup"><span data-stu-id="bd726-400">Return data</span></span>
* <span data-ttu-id="bd726-401">WPR 會話狀態。</span><span class="sxs-lookup"><span data-stu-id="bd726-401">WPR session status.</span></span>

<span data-ttu-id="bd726-402">**/api/wpr/trace （GET）**</span><span class="sxs-lookup"><span data-stu-id="bd726-402">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="bd726-403">停止 WPR （效能）追蹤會話</span><span class="sxs-lookup"><span data-stu-id="bd726-403">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="bd726-404">傳回資料</span><span class="sxs-lookup"><span data-stu-id="bd726-404">Return data</span></span>
* <span data-ttu-id="bd726-405">傳回追蹤 ETL 檔案</span><span class="sxs-lookup"><span data-stu-id="bd726-405">Returns the trace ETL file</span></span>

<span data-ttu-id="bd726-406">**/api/wpr/trace （POST）**</span><span class="sxs-lookup"><span data-stu-id="bd726-406">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="bd726-407">啟動 WPR （效能）追蹤會話</span><span class="sxs-lookup"><span data-stu-id="bd726-407">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="bd726-408">參數</span><span class="sxs-lookup"><span data-stu-id="bd726-408">Parameters</span></span>
* <span data-ttu-id="bd726-409">設定檔：設定檔名稱。</span><span class="sxs-lookup"><span data-stu-id="bd726-409">profile : Profile name.</span></span> <span data-ttu-id="bd726-410">可用的設定檔會儲存在 perfprofiles/profiles.js</span><span class="sxs-lookup"><span data-stu-id="bd726-410">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="bd726-411">傳回資料</span><span class="sxs-lookup"><span data-stu-id="bd726-411">Return data</span></span>
* <span data-ttu-id="bd726-412">在啟動時，會傳回 WPR 會話狀態。</span><span class="sxs-lookup"><span data-stu-id="bd726-412">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="bd726-413">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd726-413">See also</span></span>
* [<span data-ttu-id="bd726-414">使用 Windows 裝置入口網站</span><span class="sxs-lookup"><span data-stu-id="bd726-414">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="bd726-415">裝置入口網站核心 API 參考（UWP）</span><span class="sxs-lookup"><span data-stu-id="bd726-415">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
