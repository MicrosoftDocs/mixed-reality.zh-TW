---
title: 裝置入口網站 API 參考
description: HoloLens 上 Windows 裝置入口網站的 API 參考
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens，Windows 裝置入口網站，API
ms.openlocfilehash: 236de35c2c736fc5a0289b7be1f1548f0a08fa26
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278236"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="f4d94-104">裝置入口網站 API 參考</span><span class="sxs-lookup"><span data-stu-id="f4d94-104">Device portal API reference</span></span>

<span data-ttu-id="f4d94-105">[Windows 裝置入口網站](using-the-windows-device-portal.md)中的所有專案都是以 REST API 為基礎，您可以用它來存取資料並以程式設計方式控制您的裝置。</span><span class="sxs-lookup"><span data-stu-id="f4d94-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="f4d94-106">應用程式部署常見問題</span><span class="sxs-lookup"><span data-stu-id="f4d94-106">App deloyment</span></span>

<span data-ttu-id="f4d94-107">**/api/app/packagemanager/package （DELETE）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="f4d94-108">卸載應用程式</span><span class="sxs-lookup"><span data-stu-id="f4d94-108">Uninstalls an app</span></span>

<span data-ttu-id="f4d94-109">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-109">Parameters</span></span>
* <span data-ttu-id="f4d94-110">package：要卸載之封裝的檔案名。</span><span class="sxs-lookup"><span data-stu-id="f4d94-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="f4d94-111">**/api/app/packagemanager/package （POST）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="f4d94-112">安裝應用程式</span><span class="sxs-lookup"><span data-stu-id="f4d94-112">Installs an App</span></span>

<span data-ttu-id="f4d94-113">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-113">Parameters</span></span>
* <span data-ttu-id="f4d94-114">package：要安裝之封裝的檔案名。</span><span class="sxs-lookup"><span data-stu-id="f4d94-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="f4d94-115">裝載</span><span class="sxs-lookup"><span data-stu-id="f4d94-115">Payload</span></span>
* <span data-ttu-id="f4d94-116">多部分符合的 HTTP 主體</span><span class="sxs-lookup"><span data-stu-id="f4d94-116">multi-part conforming http body</span></span>

<span data-ttu-id="f4d94-117">**/api/app/packagemanager/packages （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="f4d94-118">抓取系統上已安裝的應用程式清單，並提供詳細資料</span><span class="sxs-lookup"><span data-stu-id="f4d94-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="f4d94-119">傳回資料</span><span class="sxs-lookup"><span data-stu-id="f4d94-119">Return data</span></span>
* <span data-ttu-id="f4d94-120">包含詳細資料的已安裝套件清單</span><span class="sxs-lookup"><span data-stu-id="f4d94-120">List of installed packages with details</span></span>

<span data-ttu-id="f4d94-121">**/api/app/packagemanager/state （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="f4d94-122">取得進行中應用程式安裝的狀態</span><span class="sxs-lookup"><span data-stu-id="f4d94-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="f4d94-123">傾印集合</span><span class="sxs-lookup"><span data-stu-id="f4d94-123">Dump collection</span></span>

<span data-ttu-id="f4d94-124">**/api/debug/dump/usermode/crashcontrol （DELETE）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="f4d94-125">停用側載應用程式的損毀傾印集合</span><span class="sxs-lookup"><span data-stu-id="f4d94-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="f4d94-126">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-126">Parameters</span></span>
* <span data-ttu-id="f4d94-127">packageFullname：封裝名稱</span><span class="sxs-lookup"><span data-stu-id="f4d94-127">packageFullname : package name</span></span>

<span data-ttu-id="f4d94-128">**/api/debug/dump/usermode/crashcontrol （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="f4d94-129">取得側載 apps 損毀傾印集合的設定</span><span class="sxs-lookup"><span data-stu-id="f4d94-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="f4d94-130">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-130">Parameters</span></span>
* <span data-ttu-id="f4d94-131">packageFullname：封裝名稱</span><span class="sxs-lookup"><span data-stu-id="f4d94-131">packageFullname : package name</span></span>

<span data-ttu-id="f4d94-132">**/api/debug/dump/usermode/crashcontrol （POST）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="f4d94-133">啟用和設定側載應用程式的傾印控制設定</span><span class="sxs-lookup"><span data-stu-id="f4d94-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="f4d94-134">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-134">Parameters</span></span>
* <span data-ttu-id="f4d94-135">packageFullname：封裝名稱</span><span class="sxs-lookup"><span data-stu-id="f4d94-135">packageFullname : package name</span></span>

<span data-ttu-id="f4d94-136">**/api/debug/dump/usermode/crashdump （DELETE）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="f4d94-137">刪除側載應用程式的損毀傾印</span><span class="sxs-lookup"><span data-stu-id="f4d94-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="f4d94-138">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-138">Parameters</span></span>
* <span data-ttu-id="f4d94-139">packageFullname：封裝名稱</span><span class="sxs-lookup"><span data-stu-id="f4d94-139">packageFullname : package name</span></span>
* <span data-ttu-id="f4d94-140">檔案名：傾印檔案名</span><span class="sxs-lookup"><span data-stu-id="f4d94-140">fileName : dump file name</span></span>

<span data-ttu-id="f4d94-141">**/api/debug/dump/usermode/crashdump （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="f4d94-142">抓取側載應用程式的損毀傾印</span><span class="sxs-lookup"><span data-stu-id="f4d94-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="f4d94-143">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-143">Parameters</span></span>
* <span data-ttu-id="f4d94-144">packageFullname：封裝名稱</span><span class="sxs-lookup"><span data-stu-id="f4d94-144">packageFullname : package name</span></span>
* <span data-ttu-id="f4d94-145">檔案名：傾印檔案名</span><span class="sxs-lookup"><span data-stu-id="f4d94-145">fileName : dump file name</span></span>

<span data-ttu-id="f4d94-146">傳回資料</span><span class="sxs-lookup"><span data-stu-id="f4d94-146">Return data</span></span>
* <span data-ttu-id="f4d94-147">傾印檔案。</span><span class="sxs-lookup"><span data-stu-id="f4d94-147">Dump file.</span></span> <span data-ttu-id="f4d94-148">使用 WinDbg 或 Visual Studio 檢查</span><span class="sxs-lookup"><span data-stu-id="f4d94-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="f4d94-149">**/api/debug/dump/usermode/dumps （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="f4d94-150">傳回側載應用程式的所有損毀傾印清單</span><span class="sxs-lookup"><span data-stu-id="f4d94-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="f4d94-151">傳回資料</span><span class="sxs-lookup"><span data-stu-id="f4d94-151">Return data</span></span>
* <span data-ttu-id="f4d94-152">每一端已載入應用程式的損毀傾印清單</span><span class="sxs-lookup"><span data-stu-id="f4d94-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="f4d94-153">ETW</span><span class="sxs-lookup"><span data-stu-id="f4d94-153">ETW</span></span>

<span data-ttu-id="f4d94-154">**/api/etw/providers （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="f4d94-155">列舉已註冊的提供者</span><span class="sxs-lookup"><span data-stu-id="f4d94-155">Enumerates registered providers</span></span>

<span data-ttu-id="f4d94-156">傳回資料</span><span class="sxs-lookup"><span data-stu-id="f4d94-156">Return data</span></span>
* <span data-ttu-id="f4d94-157">提供者清單、易記名稱和 GUID</span><span class="sxs-lookup"><span data-stu-id="f4d94-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="f4d94-158">**/api/etw/session/realtime （GET/WebSocket）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="f4d94-159">建立即時 ETW 會話;透過 websocket 管理。</span><span class="sxs-lookup"><span data-stu-id="f4d94-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="f4d94-160">傳回資料</span><span class="sxs-lookup"><span data-stu-id="f4d94-160">Return data</span></span>
* <span data-ttu-id="f4d94-161">來自已啟用提供者的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="f4d94-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="f4d94-162">全像攝影版 OS</span><span class="sxs-lookup"><span data-stu-id="f4d94-162">Holographic OS</span></span>

<span data-ttu-id="f4d94-163">**/api/holographic/os/etw/customproviders （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="f4d94-164">傳回未向系統註冊的 HoloLens 特定 ETW 提供者清單</span><span class="sxs-lookup"><span data-stu-id="f4d94-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="f4d94-165">**/api/holographic/os/services （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="f4d94-166">傳回所有執行中服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="f4d94-166">Returns the states of all services running.</span></span>

<span data-ttu-id="f4d94-167">**/api/holographic/os/settings/ipd （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="f4d94-168">取得以毫米為單位的儲存 IPD （Interpupillary 距離）</span><span class="sxs-lookup"><span data-stu-id="f4d94-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="f4d94-169">**/api/holographic/os/settings/ipd （POST）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="f4d94-170">設定 IPD</span><span class="sxs-lookup"><span data-stu-id="f4d94-170">Sets the IPD</span></span>

<span data-ttu-id="f4d94-171">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-171">Parameters</span></span>
* <span data-ttu-id="f4d94-172">ipd：要以毫米設定的新 IPD 值</span><span class="sxs-lookup"><span data-stu-id="f4d94-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="f4d94-173">**/api/holographic/os/webmanagement/settings/HTTPs （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="f4d94-174">取得 Device Portal 的 HTTPS 需求</span><span class="sxs-lookup"><span data-stu-id="f4d94-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="f4d94-175">**/api/holographic/os/webmanagement/settings/HTTPs （POST）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="f4d94-176">設定裝置入口網站的 HTTPS 需求</span><span class="sxs-lookup"><span data-stu-id="f4d94-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="f4d94-177">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-177">Parameters</span></span>
* <span data-ttu-id="f4d94-178">必要：是，否或預設值</span><span class="sxs-lookup"><span data-stu-id="f4d94-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="f4d94-179">全像攝影</span><span class="sxs-lookup"><span data-stu-id="f4d94-179">Holographic Perception</span></span>

<span data-ttu-id="f4d94-180">**/api/holographic/perception/client （GET/WebSocket）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="f4d94-181">接受 websocket 升級，並執行將更新以 30 fps 傳送的感知用戶端。</span><span class="sxs-lookup"><span data-stu-id="f4d94-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="f4d94-182">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-182">Parameters</span></span>
* <span data-ttu-id="f4d94-183">clientmode：「作用中」會在無法被動建立時強制執行視覺化追蹤模式</span><span class="sxs-lookup"><span data-stu-id="f4d94-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="f4d94-184">全像熱</span><span class="sxs-lookup"><span data-stu-id="f4d94-184">Holographic Thermal</span></span>

<span data-ttu-id="f4d94-185">**/api/holographic/thermal/stage （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="f4d94-186">取得裝置的散熱階段（0個正常、1個暖、2個重大）</span><span class="sxs-lookup"><span data-stu-id="f4d94-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="f4d94-187">認知模擬控制</span><span class="sxs-lookup"><span data-stu-id="f4d94-187">Perception Simulation Control</span></span>

<span data-ttu-id="f4d94-188">**/api/holographic/simulation/control/mode （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="f4d94-189">取得模擬模式</span><span class="sxs-lookup"><span data-stu-id="f4d94-189">Get the simulation mode</span></span>

<span data-ttu-id="f4d94-190">**/api/holographic/simulation/control/mode （POST）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="f4d94-191">設定模擬模式</span><span class="sxs-lookup"><span data-stu-id="f4d94-191">Set the simulation mode</span></span>

<span data-ttu-id="f4d94-192">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-192">Parameters</span></span>
* <span data-ttu-id="f4d94-193">模式：模擬模式：預設、模擬、遠端、舊版</span><span class="sxs-lookup"><span data-stu-id="f4d94-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="f4d94-194">**/api/holographic/simulation/control/stream （DELETE）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="f4d94-195">刪除控制資料流程。</span><span class="sxs-lookup"><span data-stu-id="f4d94-195">Delete a control stream.</span></span>

<span data-ttu-id="f4d94-196">**/api/holographic/simulation/control/stream （GET/WebSocket）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="f4d94-197">開啟控制項資料流程的 web 通訊端連接。</span><span class="sxs-lookup"><span data-stu-id="f4d94-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="f4d94-198">**/api/holographic/simulation/control/stream （POST）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="f4d94-199">建立控制資料流程（需要優先權）或將資料張貼到建立的資料流程（需要 streamId）。</span><span class="sxs-lookup"><span data-stu-id="f4d94-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="f4d94-200">張貼的資料應該是「應用程式/八位串流」類型。</span><span class="sxs-lookup"><span data-stu-id="f4d94-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="f4d94-201">認知模擬播放</span><span class="sxs-lookup"><span data-stu-id="f4d94-201">Perception Simulation Playback</span></span>

<span data-ttu-id="f4d94-202">**/api/holographic/simulation/playback/file （DELETE）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="f4d94-203">刪除錄製。</span><span class="sxs-lookup"><span data-stu-id="f4d94-203">Delete a recording.</span></span>

<span data-ttu-id="f4d94-204">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-204">Parameters</span></span>
* <span data-ttu-id="f4d94-205">錄製：要刪除的記錄名稱。</span><span class="sxs-lookup"><span data-stu-id="f4d94-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="f4d94-206">**/api/holographic/simulation/playback/file （POST）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="f4d94-207">上傳記錄。</span><span class="sxs-lookup"><span data-stu-id="f4d94-207">Upload a recording.</span></span>

<span data-ttu-id="f4d94-208">**/api/holographic/simulation/playback/files （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="f4d94-209">取得所有錄製。</span><span class="sxs-lookup"><span data-stu-id="f4d94-209">Get all recordings.</span></span>

<span data-ttu-id="f4d94-210">**/api/holographic/simulation/playback/session （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="f4d94-211">取得錄製的目前播放狀態。</span><span class="sxs-lookup"><span data-stu-id="f4d94-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="f4d94-212">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-212">Parameters</span></span>
* <span data-ttu-id="f4d94-213">錄製：錄製的名稱。</span><span class="sxs-lookup"><span data-stu-id="f4d94-213">recording : Name of recording.</span></span>

<span data-ttu-id="f4d94-214">**/api/holographic/simulation/playback/session/file （DELETE）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="f4d94-215">卸載記錄。</span><span class="sxs-lookup"><span data-stu-id="f4d94-215">Unload a recording.</span></span>

<span data-ttu-id="f4d94-216">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-216">Parameters</span></span>
* <span data-ttu-id="f4d94-217">錄製：要卸載的記錄名稱。</span><span class="sxs-lookup"><span data-stu-id="f4d94-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="f4d94-218">**/api/holographic/simulation/playback/session/file （POST）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="f4d94-219">載入錄製。</span><span class="sxs-lookup"><span data-stu-id="f4d94-219">Load a recording.</span></span>

<span data-ttu-id="f4d94-220">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-220">Parameters</span></span>
* <span data-ttu-id="f4d94-221">錄製：要載入的記錄名稱。</span><span class="sxs-lookup"><span data-stu-id="f4d94-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="f4d94-222">**/api/holographic/simulation/playback/session/files （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="f4d94-223">取得所有已載入的錄製。</span><span class="sxs-lookup"><span data-stu-id="f4d94-223">Get all loaded recordings.</span></span>

<span data-ttu-id="f4d94-224">**/api/holographic/simulation/playback/session/pause （POST）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="f4d94-225">暫停錄製。</span><span class="sxs-lookup"><span data-stu-id="f4d94-225">Pause a recording.</span></span>

<span data-ttu-id="f4d94-226">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-226">Parameters</span></span>
* <span data-ttu-id="f4d94-227">錄製：錄製的名稱。</span><span class="sxs-lookup"><span data-stu-id="f4d94-227">recording : Name of recording.</span></span>

<span data-ttu-id="f4d94-228">**/api/holographic/simulation/playback/session/play （POST）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="f4d94-229">播放錄製。</span><span class="sxs-lookup"><span data-stu-id="f4d94-229">Play a recording.</span></span>

<span data-ttu-id="f4d94-230">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-230">Parameters</span></span>
* <span data-ttu-id="f4d94-231">錄製：錄製的名稱。</span><span class="sxs-lookup"><span data-stu-id="f4d94-231">recording : Name of recording.</span></span>

<span data-ttu-id="f4d94-232">**/api/holographic/simulation/playback/session/stop （POST）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="f4d94-233">停止錄製。</span><span class="sxs-lookup"><span data-stu-id="f4d94-233">Stop a recording.</span></span>

<span data-ttu-id="f4d94-234">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-234">Parameters</span></span>
* <span data-ttu-id="f4d94-235">錄製：錄製的名稱。</span><span class="sxs-lookup"><span data-stu-id="f4d94-235">recording : Name of recording.</span></span>

<span data-ttu-id="f4d94-236">**/api/holographic/simulation/playback/session/types （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="f4d94-237">取得已載入記錄中的資料類型。</span><span class="sxs-lookup"><span data-stu-id="f4d94-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="f4d94-238">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-238">Parameters</span></span>
* <span data-ttu-id="f4d94-239">錄製：錄製的名稱。</span><span class="sxs-lookup"><span data-stu-id="f4d94-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="f4d94-240">認知模擬記錄</span><span class="sxs-lookup"><span data-stu-id="f4d94-240">Perception Simulation Recording</span></span>

<span data-ttu-id="f4d94-241">**/api/holographic/simulation/recording/start （POST）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="f4d94-242">開始錄製。</span><span class="sxs-lookup"><span data-stu-id="f4d94-242">Start a recording.</span></span> <span data-ttu-id="f4d94-243">一次只能有一個使用中的錄製。</span><span class="sxs-lookup"><span data-stu-id="f4d94-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="f4d94-244">必須設定 head、手、spatialMapping 或環境之一。</span><span class="sxs-lookup"><span data-stu-id="f4d94-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="f4d94-245">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-245">Parameters</span></span>
* <span data-ttu-id="f4d94-246">head：設定為1以記錄 head 資料。</span><span class="sxs-lookup"><span data-stu-id="f4d94-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="f4d94-247">實習：設定為1以記錄手資料。</span><span class="sxs-lookup"><span data-stu-id="f4d94-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="f4d94-248">spatialMapping：設定為1以記錄空間對應。</span><span class="sxs-lookup"><span data-stu-id="f4d94-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="f4d94-249">環境：設定為1以記錄環境資料。</span><span class="sxs-lookup"><span data-stu-id="f4d94-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="f4d94-250">名稱：記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="f4d94-250">name : Name of the recording.</span></span>
* <span data-ttu-id="f4d94-251">singleSpatialMappingFrame：設定為1，只記錄一個空間對應框架。</span><span class="sxs-lookup"><span data-stu-id="f4d94-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="f4d94-252">**/api/holographic/simulation/recording/status （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="f4d94-253">取得錄製狀態。</span><span class="sxs-lookup"><span data-stu-id="f4d94-253">Get recording state.</span></span>

<span data-ttu-id="f4d94-254">**/api/holographic/simulation/recording/stop （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="f4d94-255">停止目前的錄製。</span><span class="sxs-lookup"><span data-stu-id="f4d94-255">Stop the current recording.</span></span> <span data-ttu-id="f4d94-256">記錄將會以檔案的形式傳回。</span><span class="sxs-lookup"><span data-stu-id="f4d94-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="f4d94-257">混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="f4d94-257">Mixed Reality Capture</span></span>

<span data-ttu-id="f4d94-258">**/api/holographic/mrc/file （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="f4d94-259">從裝置下載混合的現實檔案。</span><span class="sxs-lookup"><span data-stu-id="f4d94-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="f4d94-260">使用 op = 資料流程查詢參數進行串流處理。</span><span class="sxs-lookup"><span data-stu-id="f4d94-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="f4d94-261">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-261">Parameters</span></span>
* <span data-ttu-id="f4d94-262">filename：要取得之影片檔案的名稱、hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="f4d94-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="f4d94-263">op：資料流程</span><span class="sxs-lookup"><span data-stu-id="f4d94-263">op : stream</span></span>

<span data-ttu-id="f4d94-264">**/api/holographic/mrc/file （DELETE）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="f4d94-265">從裝置中刪除混合現實記錄。</span><span class="sxs-lookup"><span data-stu-id="f4d94-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="f4d94-266">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-266">Parameters</span></span>
* <span data-ttu-id="f4d94-267">filename：要刪除之檔案的名稱、hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="f4d94-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="f4d94-268">**/api/holographic/mrc/files （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="f4d94-269">傳回儲存在裝置上的混合 reality 檔案清單</span><span class="sxs-lookup"><span data-stu-id="f4d94-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="f4d94-270">**/api/holographic/mrc/photo （POST）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="f4d94-271">採用混合的現實相片，並在裝置上建立檔案</span><span class="sxs-lookup"><span data-stu-id="f4d94-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="f4d94-272">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-272">Parameters</span></span>
* <span data-ttu-id="f4d94-273">hololens： capture 全息影像： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="f4d94-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="f4d94-274">pv： capture PV 攝影機： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="f4d94-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="f4d94-275">RenderFromCamera：（僅限 HoloLens 2）從相片/攝影機的觀點呈現： true 或 false （預設為 true）</span><span class="sxs-lookup"><span data-stu-id="f4d94-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="f4d94-276">**/api/holographic/mrc/settings （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="f4d94-277">取得預設的混合現實捕捉設定</span><span class="sxs-lookup"><span data-stu-id="f4d94-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="f4d94-278">**/api/holographic/mrc/settings （POST）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="f4d94-279">設定預設的混合現實捕捉設定。</span><span class="sxs-lookup"><span data-stu-id="f4d94-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="f4d94-280">其中部分設定會套用至系統的 MRC 相片和影片捕獲。</span><span class="sxs-lookup"><span data-stu-id="f4d94-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="f4d94-281">**/api/holographic/mrc/status （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="f4d94-282">取得已記錄之混合事實的狀態（執行中、已停止）</span><span class="sxs-lookup"><span data-stu-id="f4d94-282">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="f4d94-283">**/api/holographic/mrc/thumbnail （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-283">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="f4d94-284">取得指定檔案的縮圖影像。</span><span class="sxs-lookup"><span data-stu-id="f4d94-284">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="f4d94-285">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-285">Parameters</span></span>
* <span data-ttu-id="f4d94-286">檔案名：要為其要求縮圖之檔案的名稱、hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="f4d94-286">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="f4d94-287">**/api/holographic/mrc/video/control/start （POST）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-287">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="f4d94-288">開始進行混合的事實記錄</span><span class="sxs-lookup"><span data-stu-id="f4d94-288">Starts a mixed reality recording</span></span>

<span data-ttu-id="f4d94-289">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-289">Parameters</span></span>
* <span data-ttu-id="f4d94-290">hololens： capture 全息影像： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="f4d94-290">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="f4d94-291">pv： capture PV 攝影機： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="f4d94-291">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="f4d94-292">mic： capture 麥克風： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="f4d94-292">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="f4d94-293">回送：捕獲應用程式音訊： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="f4d94-293">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="f4d94-294">RenderFromCamera：（僅限 HoloLens 2）從相片/攝影機的觀點呈現： true 或 false （預設為 true）</span><span class="sxs-lookup"><span data-stu-id="f4d94-294">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="f4d94-295">vstab：（僅限 HoloLens 2）啟用影片穩定： true 或 false （預設為 true）</span><span class="sxs-lookup"><span data-stu-id="f4d94-295">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="f4d94-296">vstabbuffer：（僅限 HoloLens 2）影片穩定緩衝區延遲：0到30個框架（預設為15個畫面）</span><span class="sxs-lookup"><span data-stu-id="f4d94-296">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="f4d94-297">**/api/holographic/mrc/video/control/stop （POST）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-297">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="f4d94-298">停止目前的混合現實記錄</span><span class="sxs-lookup"><span data-stu-id="f4d94-298">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="f4d94-299">混合現實串流</span><span class="sxs-lookup"><span data-stu-id="f4d94-299">Mixed Reality Streaming</span></span>

<span data-ttu-id="f4d94-300">HoloLens 支援透過區塊下載的分散的方式，即時預覽混合現實。</span><span class="sxs-lookup"><span data-stu-id="f4d94-300">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="f4d94-301">混合的事實資料流會共用一組相同的參數，以控制已捕捉的內容：</span><span class="sxs-lookup"><span data-stu-id="f4d94-301">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="f4d94-302">hololens： capture 全息影像： true 或 false</span><span class="sxs-lookup"><span data-stu-id="f4d94-302">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="f4d94-303">pv：捕捉 PV 攝影機： true 或 false</span><span class="sxs-lookup"><span data-stu-id="f4d94-303">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="f4d94-304">mic：捕捉麥克風： true 或 false</span><span class="sxs-lookup"><span data-stu-id="f4d94-304">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="f4d94-305">回送：捕獲應用程式音訊： true 或 false</span><span class="sxs-lookup"><span data-stu-id="f4d94-305">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="f4d94-306">如果未指定這些內容：將會捕捉到全息影像、相片/攝影機和應用程式音訊</span><span class="sxs-lookup"><span data-stu-id="f4d94-306">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="f4d94-307">如果指定了任何值：未指定的參數將預設為 false</span><span class="sxs-lookup"><span data-stu-id="f4d94-307">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="f4d94-308">選擇性參數（僅限 HoloLens 2）</span><span class="sxs-lookup"><span data-stu-id="f4d94-308">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="f4d94-309">RenderFromCamera：從相片/攝影機的角度呈現： true 或 false （預設為 true）</span><span class="sxs-lookup"><span data-stu-id="f4d94-309">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="f4d94-310">vstab：啟用影片穩定： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="f4d94-310">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="f4d94-311">vstabbuffer：視頻穩定緩衝區延遲：0到30的框架（預設為15個框架）</span><span class="sxs-lookup"><span data-stu-id="f4d94-311">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="f4d94-312">**/api/holographic/stream/live.mp4 （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-312">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="f4d94-313">解析度為 1280x720p 30fps 5Mbit 串流。</span><span class="sxs-lookup"><span data-stu-id="f4d94-313">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="f4d94-314">**/api/holographic/stream/live_high. （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-314">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="f4d94-315">解析度為 1280x720p 30fps 5Mbit 串流。</span><span class="sxs-lookup"><span data-stu-id="f4d94-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="f4d94-316">**/api/holographic/stream/live_med. （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="f4d94-317">854x480p 30fps 2.5 Mbit 串流。</span><span class="sxs-lookup"><span data-stu-id="f4d94-317">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="f4d94-318">**/api/holographic/stream/live_low. （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-318">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="f4d94-319">428x240p 15fps 0.6 Mbit 串流。</span><span class="sxs-lookup"><span data-stu-id="f4d94-319">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="f4d94-320">網路功能</span><span class="sxs-lookup"><span data-stu-id="f4d94-320">Networking</span></span>

<span data-ttu-id="f4d94-321">**/api/networking/ipconfig （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-321">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="f4d94-322">取得目前的 ip 設定</span><span class="sxs-lookup"><span data-stu-id="f4d94-322">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="f4d94-323">作業系統資訊</span><span class="sxs-lookup"><span data-stu-id="f4d94-323">OS Information</span></span>

<span data-ttu-id="f4d94-324">**/api/os/info （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-324">**/api/os/info (GET)**</span></span>

<span data-ttu-id="f4d94-325">取得作業系統資訊</span><span class="sxs-lookup"><span data-stu-id="f4d94-325">Gets operating system information</span></span>

<span data-ttu-id="f4d94-326">**/api/os/machinename （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-326">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="f4d94-327">取得電腦名稱稱</span><span class="sxs-lookup"><span data-stu-id="f4d94-327">Gets the machine name</span></span>

<span data-ttu-id="f4d94-328">**/api/os/machinename （POST）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-328">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="f4d94-329">設定電腦名稱稱</span><span class="sxs-lookup"><span data-stu-id="f4d94-329">Sets the machine name</span></span>

<span data-ttu-id="f4d94-330">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-330">Parameters</span></span>
* <span data-ttu-id="f4d94-331">名稱：新的電腦名稱稱，hex64 編碼，設定為</span><span class="sxs-lookup"><span data-stu-id="f4d94-331">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="f4d94-332">效能資料</span><span class="sxs-lookup"><span data-stu-id="f4d94-332">Performance data</span></span>

<span data-ttu-id="f4d94-333">**/api/resourcemanager/processes （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-333">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="f4d94-334">傳回執行中進程的清單，並提供詳細資料</span><span class="sxs-lookup"><span data-stu-id="f4d94-334">Returns the list of running processes with details</span></span>

<span data-ttu-id="f4d94-335">傳回資料</span><span class="sxs-lookup"><span data-stu-id="f4d94-335">Return data</span></span>
* <span data-ttu-id="f4d94-336">JSON，內含進程的清單和每個進程的詳細資料</span><span class="sxs-lookup"><span data-stu-id="f4d94-336">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="f4d94-337">**/api/resourcemanager/systemperf （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-337">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="f4d94-338">傳回系統效能統計資料（i/o 讀取/寫入、記憶體統計等）。</span><span class="sxs-lookup"><span data-stu-id="f4d94-338">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="f4d94-339">傳回資料</span><span class="sxs-lookup"><span data-stu-id="f4d94-339">Return data</span></span>
* <span data-ttu-id="f4d94-340">具有系統資訊的 JSON： CPU、GPU、記憶體、網路、IO</span><span class="sxs-lookup"><span data-stu-id="f4d94-340">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="f4d94-341">電源</span><span class="sxs-lookup"><span data-stu-id="f4d94-341">Power</span></span>

<span data-ttu-id="f4d94-342">**/api/power/battery （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-342">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="f4d94-343">取得目前的電池狀態</span><span class="sxs-lookup"><span data-stu-id="f4d94-343">Gets the current battery state</span></span>

<span data-ttu-id="f4d94-344">**/api/power/state （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-344">**/api/power/state (GET)**</span></span>

<span data-ttu-id="f4d94-345">檢查系統是否處於低電源狀態</span><span class="sxs-lookup"><span data-stu-id="f4d94-345">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="f4d94-346">遠端控制</span><span class="sxs-lookup"><span data-stu-id="f4d94-346">Remote Control</span></span>

<span data-ttu-id="f4d94-347">**/api/control/restart （POST）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-347">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="f4d94-348">重新開機目標裝置</span><span class="sxs-lookup"><span data-stu-id="f4d94-348">Restarts the target device</span></span>

<span data-ttu-id="f4d94-349">**/api/control/shutdown （POST）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-349">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="f4d94-350">關閉目標裝置</span><span class="sxs-lookup"><span data-stu-id="f4d94-350">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="f4d94-351">工作管理員</span><span class="sxs-lookup"><span data-stu-id="f4d94-351">Task Manager</span></span>

<span data-ttu-id="f4d94-352">**/api/taskmanager/app （DELETE）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-352">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="f4d94-353">停止現代化應用程式</span><span class="sxs-lookup"><span data-stu-id="f4d94-353">Stops a modern app</span></span>

<span data-ttu-id="f4d94-354">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-354">Parameters</span></span>
* <span data-ttu-id="f4d94-355">package：應用程式套件的完整名稱，hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="f4d94-355">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="f4d94-356">forcestop：強制停止所有進程（= 是）</span><span class="sxs-lookup"><span data-stu-id="f4d94-356">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="f4d94-357">**/api/taskmanager/app （POST）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-357">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="f4d94-358">啟動現代化應用程式</span><span class="sxs-lookup"><span data-stu-id="f4d94-358">Starts a modern app</span></span>

<span data-ttu-id="f4d94-359">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-359">Parameters</span></span>
* <span data-ttu-id="f4d94-360">appid：要啟動之應用程式的 PRAID，hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="f4d94-360">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="f4d94-361">package：應用程式套件的完整名稱，hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="f4d94-361">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="f4d94-362">WiFi 管理</span><span class="sxs-lookup"><span data-stu-id="f4d94-362">WiFi Management</span></span>

<span data-ttu-id="f4d94-363">**/api/wifi/interfaces （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-363">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="f4d94-364">列舉無線網路介面</span><span class="sxs-lookup"><span data-stu-id="f4d94-364">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="f4d94-365">傳回資料</span><span class="sxs-lookup"><span data-stu-id="f4d94-365">Return data</span></span>
* <span data-ttu-id="f4d94-366">具有詳細資料的無線介面清單（GUID、描述等等）</span><span class="sxs-lookup"><span data-stu-id="f4d94-366">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="f4d94-367">**/api/wifi/network （DELETE）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-367">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="f4d94-368">刪除與指定之介面上的網路相關聯的設定檔</span><span class="sxs-lookup"><span data-stu-id="f4d94-368">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="f4d94-369">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-369">Parameters</span></span>
* <span data-ttu-id="f4d94-370">介面：網路介面 guid</span><span class="sxs-lookup"><span data-stu-id="f4d94-370">interface : network interface guid</span></span>
* <span data-ttu-id="f4d94-371">設定檔：設定檔名稱</span><span class="sxs-lookup"><span data-stu-id="f4d94-371">profile : profile name</span></span>

<span data-ttu-id="f4d94-372">**/api/wifi/networks （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-372">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="f4d94-373">列舉指定網路介面上的無線網路</span><span class="sxs-lookup"><span data-stu-id="f4d94-373">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="f4d94-374">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-374">Parameters</span></span>
* <span data-ttu-id="f4d94-375">介面：網路介面 guid</span><span class="sxs-lookup"><span data-stu-id="f4d94-375">interface : network interface guid</span></span>

<span data-ttu-id="f4d94-376">傳回資料</span><span class="sxs-lookup"><span data-stu-id="f4d94-376">Return data</span></span>
* <span data-ttu-id="f4d94-377">在網路介面上找到的無線網路清單，並提供詳細資料</span><span class="sxs-lookup"><span data-stu-id="f4d94-377">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="f4d94-378">**/api/wifi/network （POST）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-378">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="f4d94-379">連接或中斷連線到指定介面上的網路</span><span class="sxs-lookup"><span data-stu-id="f4d94-379">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="f4d94-380">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-380">Parameters</span></span>
* <span data-ttu-id="f4d94-381">介面：網路介面 guid</span><span class="sxs-lookup"><span data-stu-id="f4d94-381">interface : network interface guid</span></span>
* <span data-ttu-id="f4d94-382">ssid：用來連線到的 ssid （hex64 編碼）</span><span class="sxs-lookup"><span data-stu-id="f4d94-382">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="f4d94-383">op：連接或中斷連線</span><span class="sxs-lookup"><span data-stu-id="f4d94-383">op : connect or disconnect</span></span>
* <span data-ttu-id="f4d94-384">createprofile：是或否</span><span class="sxs-lookup"><span data-stu-id="f4d94-384">createprofile : yes or no</span></span>
* <span data-ttu-id="f4d94-385">金鑰：共用金鑰，hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="f4d94-385">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="f4d94-386">Windows Performance Recorder</span><span class="sxs-lookup"><span data-stu-id="f4d94-386">Windows Performance Recorder</span></span>

<span data-ttu-id="f4d94-387">**/api/wpr/customtrace （POST）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-387">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="f4d94-388">上傳 WPR 設定檔，並使用上傳的設定檔開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="f4d94-388">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="f4d94-389">裝載</span><span class="sxs-lookup"><span data-stu-id="f4d94-389">Payload</span></span>
* <span data-ttu-id="f4d94-390">多部分符合的 HTTP 主體</span><span class="sxs-lookup"><span data-stu-id="f4d94-390">multi-part conforming http body</span></span>

<span data-ttu-id="f4d94-391">傳回資料</span><span class="sxs-lookup"><span data-stu-id="f4d94-391">Return data</span></span>
* <span data-ttu-id="f4d94-392">傳回 WPR 會話狀態。</span><span class="sxs-lookup"><span data-stu-id="f4d94-392">Returns the WPR session status.</span></span>

<span data-ttu-id="f4d94-393">**/api/wpr/status （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-393">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="f4d94-394">抓取 WPR 會話的狀態</span><span class="sxs-lookup"><span data-stu-id="f4d94-394">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="f4d94-395">傳回資料</span><span class="sxs-lookup"><span data-stu-id="f4d94-395">Return data</span></span>
* <span data-ttu-id="f4d94-396">WPR 會話狀態。</span><span class="sxs-lookup"><span data-stu-id="f4d94-396">WPR session status.</span></span>

<span data-ttu-id="f4d94-397">**/api/wpr/trace （GET）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-397">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="f4d94-398">停止 WPR （效能）追蹤會話</span><span class="sxs-lookup"><span data-stu-id="f4d94-398">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="f4d94-399">傳回資料</span><span class="sxs-lookup"><span data-stu-id="f4d94-399">Return data</span></span>
* <span data-ttu-id="f4d94-400">傳回追蹤 ETL 檔案</span><span class="sxs-lookup"><span data-stu-id="f4d94-400">Returns the trace ETL file</span></span>

<span data-ttu-id="f4d94-401">**/api/wpr/trace （POST）**</span><span class="sxs-lookup"><span data-stu-id="f4d94-401">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="f4d94-402">啟動 WPR （效能）追蹤會話</span><span class="sxs-lookup"><span data-stu-id="f4d94-402">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="f4d94-403">參數</span><span class="sxs-lookup"><span data-stu-id="f4d94-403">Parameters</span></span>
* <span data-ttu-id="f4d94-404">設定檔：設定檔名稱。</span><span class="sxs-lookup"><span data-stu-id="f4d94-404">profile : Profile name.</span></span> <span data-ttu-id="f4d94-405">可用的設定檔會儲存在 perfprofiles/profiles 中。 json</span><span class="sxs-lookup"><span data-stu-id="f4d94-405">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="f4d94-406">傳回資料</span><span class="sxs-lookup"><span data-stu-id="f4d94-406">Return data</span></span>
* <span data-ttu-id="f4d94-407">在啟動時，會傳回 WPR 會話狀態。</span><span class="sxs-lookup"><span data-stu-id="f4d94-407">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="f4d94-408">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4d94-408">See also</span></span>
* [<span data-ttu-id="f4d94-409">使用 Windows 裝置入口網站</span><span class="sxs-lookup"><span data-stu-id="f4d94-409">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="f4d94-410">裝置入口網站核心 API 參考（UWP）</span><span class="sxs-lookup"><span data-stu-id="f4d94-410">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
