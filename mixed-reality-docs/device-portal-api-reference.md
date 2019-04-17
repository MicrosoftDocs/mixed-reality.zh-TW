---
title: 裝置入口網站的 API 參考
description: HoloLens 上 Windows Device Portal API 參考
author: JonMLyons
ms.author: JLyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、 Windows Device Portal，API
ms.openlocfilehash: 507ab98734adea80d0aad41d99124e3d91846f28
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596067"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="1494e-104">裝置入口網站的 API 參考</span><span class="sxs-lookup"><span data-stu-id="1494e-104">Device portal API reference</span></span>

<span data-ttu-id="1494e-105">中的所有項目[Windows Device Portal](using-the-windows-device-portal.md)為建置基礎 REST API 可用來存取資料，並以程式設計方式控制您的裝置。</span><span class="sxs-lookup"><span data-stu-id="1494e-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="1494e-106">應用程式部署</span><span class="sxs-lookup"><span data-stu-id="1494e-106">App deloyment</span></span>

<span data-ttu-id="1494e-107">**/api/app/packagemanager/package (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="1494e-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="1494e-108">解除安裝應用程式</span><span class="sxs-lookup"><span data-stu-id="1494e-108">Uninstalls an app</span></span>

<span data-ttu-id="1494e-109">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-109">Parameters</span></span>
* <span data-ttu-id="1494e-110">封裝：要解除安裝之封裝的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="1494e-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="1494e-111">**/api/app/packagemanager/package (POST)**</span><span class="sxs-lookup"><span data-stu-id="1494e-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="1494e-112">安裝應用程式</span><span class="sxs-lookup"><span data-stu-id="1494e-112">Installs an App</span></span>

<span data-ttu-id="1494e-113">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-113">Parameters</span></span>
* <span data-ttu-id="1494e-114">封裝：要安裝之封裝的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="1494e-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="1494e-115">承載</span><span class="sxs-lookup"><span data-stu-id="1494e-115">Payload</span></span>
* <span data-ttu-id="1494e-116">多部分符合的 http 內容</span><span class="sxs-lookup"><span data-stu-id="1494e-116">multi-part conforming http body</span></span>

<span data-ttu-id="1494e-117">**/api/app/packagemanager/packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="1494e-118">擷取已安裝的應用程式在系統上，詳細資料清單</span><span class="sxs-lookup"><span data-stu-id="1494e-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="1494e-119">傳回資料</span><span class="sxs-lookup"><span data-stu-id="1494e-119">Return data</span></span>
* <span data-ttu-id="1494e-120">列出已安裝的套件詳細資料</span><span class="sxs-lookup"><span data-stu-id="1494e-120">List of installed packages with details</span></span>

<span data-ttu-id="1494e-121">**/api/app/packagemanager/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="1494e-122">取得中進行應用程式安裝狀態</span><span class="sxs-lookup"><span data-stu-id="1494e-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="1494e-123">傾印集合</span><span class="sxs-lookup"><span data-stu-id="1494e-123">Dump collection</span></span>

<span data-ttu-id="1494e-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="1494e-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="1494e-125">停用的損毀傾印集合的側載應用程式</span><span class="sxs-lookup"><span data-stu-id="1494e-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="1494e-126">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-126">Parameters</span></span>
* <span data-ttu-id="1494e-127">packageFullname： 封裝名稱</span><span class="sxs-lookup"><span data-stu-id="1494e-127">packageFullname : package name</span></span>

<span data-ttu-id="1494e-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="1494e-129">取得側載應用程式設定損毀傾印收集</span><span class="sxs-lookup"><span data-stu-id="1494e-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="1494e-130">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-130">Parameters</span></span>
* <span data-ttu-id="1494e-131">packageFullname： 封裝名稱</span><span class="sxs-lookup"><span data-stu-id="1494e-131">packageFullname : package name</span></span>

<span data-ttu-id="1494e-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="1494e-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="1494e-133">啟用並設定側載應用程式的傾印控制項設定</span><span class="sxs-lookup"><span data-stu-id="1494e-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="1494e-134">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-134">Parameters</span></span>
* <span data-ttu-id="1494e-135">packageFullname： 封裝名稱</span><span class="sxs-lookup"><span data-stu-id="1494e-135">packageFullname : package name</span></span>

<span data-ttu-id="1494e-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="1494e-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="1494e-137">刪除側載應用程式損毀傾印</span><span class="sxs-lookup"><span data-stu-id="1494e-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="1494e-138">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-138">Parameters</span></span>
* <span data-ttu-id="1494e-139">packageFullname： 封裝名稱</span><span class="sxs-lookup"><span data-stu-id="1494e-139">packageFullname : package name</span></span>
* <span data-ttu-id="1494e-140">fileName： 傾印檔案名稱</span><span class="sxs-lookup"><span data-stu-id="1494e-140">fileName : dump file name</span></span>

<span data-ttu-id="1494e-141">**/api/debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="1494e-142">擷取的側載應用程式損毀傾印</span><span class="sxs-lookup"><span data-stu-id="1494e-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="1494e-143">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-143">Parameters</span></span>
* <span data-ttu-id="1494e-144">packageFullname： 封裝名稱</span><span class="sxs-lookup"><span data-stu-id="1494e-144">packageFullname : package name</span></span>
* <span data-ttu-id="1494e-145">fileName： 傾印檔案名稱</span><span class="sxs-lookup"><span data-stu-id="1494e-145">fileName : dump file name</span></span>

<span data-ttu-id="1494e-146">傳回資料</span><span class="sxs-lookup"><span data-stu-id="1494e-146">Return data</span></span>
* <span data-ttu-id="1494e-147">傾印檔案。</span><span class="sxs-lookup"><span data-stu-id="1494e-147">Dump file.</span></span> <span data-ttu-id="1494e-148">檢查使用 WinDbg 或 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1494e-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="1494e-149">**/api/debug/dump/usermode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="1494e-150">傳回清單的側載應用程式的所有損毀傾印</span><span class="sxs-lookup"><span data-stu-id="1494e-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="1494e-151">傳回資料</span><span class="sxs-lookup"><span data-stu-id="1494e-151">Return data</span></span>
* <span data-ttu-id="1494e-152">每個側邊載入應用程式的清單中的損毀傾印</span><span class="sxs-lookup"><span data-stu-id="1494e-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="1494e-153">ETW</span><span class="sxs-lookup"><span data-stu-id="1494e-153">ETW</span></span>

<span data-ttu-id="1494e-154">**/api/etw/providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="1494e-155">列舉已註冊的提供者</span><span class="sxs-lookup"><span data-stu-id="1494e-155">Enumerates registered providers</span></span>

<span data-ttu-id="1494e-156">傳回資料</span><span class="sxs-lookup"><span data-stu-id="1494e-156">Return data</span></span>
* <span data-ttu-id="1494e-157">提供者、 易記名稱和 GUID 的清單</span><span class="sxs-lookup"><span data-stu-id="1494e-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="1494e-158">**/api/etw/session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="1494e-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="1494e-159">建立即時的 ETW 工作階段;透過 websocket 的管理。</span><span class="sxs-lookup"><span data-stu-id="1494e-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="1494e-160">傳回資料</span><span class="sxs-lookup"><span data-stu-id="1494e-160">Return data</span></span>
* <span data-ttu-id="1494e-161">從啟用的提供者的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="1494e-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="1494e-162">全像攝影版 OS</span><span class="sxs-lookup"><span data-stu-id="1494e-162">Holographic OS</span></span>

<span data-ttu-id="1494e-163">**/api/holographic/os/etw/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="1494e-164">傳回一份 HoloLens 特定 ETW 提供者不會向系統</span><span class="sxs-lookup"><span data-stu-id="1494e-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="1494e-165">**/api/holographic/os/services (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="1494e-166">傳回執行的所有服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="1494e-166">Returns the states of all services running.</span></span>

<span data-ttu-id="1494e-167">**/api/holographic/os/settings/ipd (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="1494e-168">取得在公釐為單位的預存的 IPD （Interpupillary 距離）</span><span class="sxs-lookup"><span data-stu-id="1494e-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="1494e-169">**/api/holographic/os/settings/ipd (POST)**</span><span class="sxs-lookup"><span data-stu-id="1494e-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="1494e-170">設定 IPD</span><span class="sxs-lookup"><span data-stu-id="1494e-170">Sets the IPD</span></span>

<span data-ttu-id="1494e-171">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-171">Parameters</span></span>
* <span data-ttu-id="1494e-172">ipd:若要設定以公釐新 IPD 值</span><span class="sxs-lookup"><span data-stu-id="1494e-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="1494e-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="1494e-174">取得 Device Portal 的 HTTPS 需求</span><span class="sxs-lookup"><span data-stu-id="1494e-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="1494e-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span><span class="sxs-lookup"><span data-stu-id="1494e-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="1494e-176">設定裝置入口網站的 HTTPS 需求</span><span class="sxs-lookup"><span data-stu-id="1494e-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="1494e-177">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-177">Parameters</span></span>
* <span data-ttu-id="1494e-178">必要： yes、 no 或預設值</span><span class="sxs-lookup"><span data-stu-id="1494e-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="1494e-179">全像攝影版的認知</span><span class="sxs-lookup"><span data-stu-id="1494e-179">Holographic Perception</span></span>

<span data-ttu-id="1494e-180">**/api/holographic/perception/client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="1494e-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="1494e-181">接受 websocket 升級，並會將更新傳送 30fps 在 perception 用戶端執行。</span><span class="sxs-lookup"><span data-stu-id="1494e-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="1494e-182">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-182">Parameters</span></span>
* <span data-ttu-id="1494e-183">clientmode: 「 作用中 」 時，會強制視覺追蹤模式無法被動地建立</span><span class="sxs-lookup"><span data-stu-id="1494e-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="1494e-184">全像攝影版的散熱</span><span class="sxs-lookup"><span data-stu-id="1494e-184">Holographic Thermal</span></span>

<span data-ttu-id="1494e-185">**/api/holographic/thermal/stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="1494e-186">取得裝置 （1 暖，重要的 2 中的 0 的標準模式） 的熱階段</span><span class="sxs-lookup"><span data-stu-id="1494e-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="1494e-187">Perception 模擬控制項</span><span class="sxs-lookup"><span data-stu-id="1494e-187">Perception Simulation Control</span></span>

<span data-ttu-id="1494e-188">**/api/holographic/simulation/control/mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="1494e-189">取得的模擬模式</span><span class="sxs-lookup"><span data-stu-id="1494e-189">Get the simulation mode</span></span>

<span data-ttu-id="1494e-190">**/api/holographic/simulation/control/mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="1494e-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="1494e-191">設定模擬模式</span><span class="sxs-lookup"><span data-stu-id="1494e-191">Set the simulation mode</span></span>

<span data-ttu-id="1494e-192">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-192">Parameters</span></span>
* <span data-ttu-id="1494e-193">模式： 模擬模式： 預設、 模擬、 遠端，舊版</span><span class="sxs-lookup"><span data-stu-id="1494e-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="1494e-194">**/api/holographic/simulation/control/stream （刪除）**</span><span class="sxs-lookup"><span data-stu-id="1494e-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="1494e-195">刪除控制資料流。</span><span class="sxs-lookup"><span data-stu-id="1494e-195">Delete a control stream.</span></span>

<span data-ttu-id="1494e-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="1494e-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="1494e-197">開啟 web 通訊端連線控制資料流。</span><span class="sxs-lookup"><span data-stu-id="1494e-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="1494e-198">**/api/holographic/simulation/control/stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="1494e-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="1494e-199">建立控制項的資料流 （優先順序是必要的） 或將資料公佈至建立的資料流 (所需的 streamId)。</span><span class="sxs-lookup"><span data-stu-id="1494e-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="1494e-200">張貼的資料應該是類型 ' 應用程式/八位元資料流 '。</span><span class="sxs-lookup"><span data-stu-id="1494e-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="1494e-201">Perception 模擬播放</span><span class="sxs-lookup"><span data-stu-id="1494e-201">Perception Simulation Playback</span></span>

<span data-ttu-id="1494e-202">**/api/holographic/simulation/playback/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="1494e-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="1494e-203">刪除記錄。</span><span class="sxs-lookup"><span data-stu-id="1494e-203">Delete a recording.</span></span>

<span data-ttu-id="1494e-204">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-204">Parameters</span></span>
* <span data-ttu-id="1494e-205">記錄：若要刪除記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="1494e-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="1494e-206">**/api/holographic/simulation/playback/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="1494e-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="1494e-207">上傳的記錄。</span><span class="sxs-lookup"><span data-stu-id="1494e-207">Upload a recording.</span></span>

<span data-ttu-id="1494e-208">**/api/holographic/simulation/playback/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="1494e-209">取得所有記錄。</span><span class="sxs-lookup"><span data-stu-id="1494e-209">Get all recordings.</span></span>

<span data-ttu-id="1494e-210">**/api/holographic/simulation/playback/session (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="1494e-211">取得目前的錄製播放狀態。</span><span class="sxs-lookup"><span data-stu-id="1494e-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="1494e-212">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-212">Parameters</span></span>
* <span data-ttu-id="1494e-213">記錄：記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="1494e-213">recording : Name of recording.</span></span>

<span data-ttu-id="1494e-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="1494e-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="1494e-215">卸載錄製。</span><span class="sxs-lookup"><span data-stu-id="1494e-215">Unload a recording.</span></span>

<span data-ttu-id="1494e-216">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-216">Parameters</span></span>
* <span data-ttu-id="1494e-217">記錄：卸載所記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="1494e-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="1494e-218">**/api/holographic/simulation/playback/session/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="1494e-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="1494e-219">載入記錄。</span><span class="sxs-lookup"><span data-stu-id="1494e-219">Load a recording.</span></span>

<span data-ttu-id="1494e-220">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-220">Parameters</span></span>
* <span data-ttu-id="1494e-221">記錄：載入記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="1494e-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="1494e-222">**/api/holographic/simulation/playback/session/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="1494e-223">取得載入的所有記錄。</span><span class="sxs-lookup"><span data-stu-id="1494e-223">Get all loaded recordings.</span></span>

<span data-ttu-id="1494e-224">**/api/holographic/simulation/playback/session/pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="1494e-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="1494e-225">暫停錄製。</span><span class="sxs-lookup"><span data-stu-id="1494e-225">Pause a recording.</span></span>

<span data-ttu-id="1494e-226">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-226">Parameters</span></span>
* <span data-ttu-id="1494e-227">記錄：記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="1494e-227">recording : Name of recording.</span></span>

<span data-ttu-id="1494e-228">**/api/holographic/simulation/playback/session/play (POST)**</span><span class="sxs-lookup"><span data-stu-id="1494e-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="1494e-229">播放錄製。</span><span class="sxs-lookup"><span data-stu-id="1494e-229">Play a recording.</span></span>

<span data-ttu-id="1494e-230">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-230">Parameters</span></span>
* <span data-ttu-id="1494e-231">記錄：記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="1494e-231">recording : Name of recording.</span></span>

<span data-ttu-id="1494e-232">**/api/holographic/simulation/playback/session/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="1494e-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="1494e-233">停止錄製。</span><span class="sxs-lookup"><span data-stu-id="1494e-233">Stop a recording.</span></span>

<span data-ttu-id="1494e-234">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-234">Parameters</span></span>
* <span data-ttu-id="1494e-235">記錄：記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="1494e-235">recording : Name of recording.</span></span>

<span data-ttu-id="1494e-236">**/api/holographic/simulation/playback/session/types (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="1494e-237">載入的記錄中取得資料的類型。</span><span class="sxs-lookup"><span data-stu-id="1494e-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="1494e-238">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-238">Parameters</span></span>
* <span data-ttu-id="1494e-239">記錄：記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="1494e-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="1494e-240">Perception 模擬記錄</span><span class="sxs-lookup"><span data-stu-id="1494e-240">Perception Simulation Recording</span></span>

<span data-ttu-id="1494e-241">**/api/holographic/simulation/recording/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="1494e-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="1494e-242">開始錄製。</span><span class="sxs-lookup"><span data-stu-id="1494e-242">Start a recording.</span></span> <span data-ttu-id="1494e-243">可同時處於作用中單一記錄。</span><span class="sxs-lookup"><span data-stu-id="1494e-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="1494e-244">必須設定其中一個標頭、 實際操作、 spatialMapping 或環境。</span><span class="sxs-lookup"><span data-stu-id="1494e-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="1494e-245">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-245">Parameters</span></span>
* <span data-ttu-id="1494e-246">前端：設定為 1，以記錄標頭的資料。</span><span class="sxs-lookup"><span data-stu-id="1494e-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="1494e-247">實際操作：記錄手動資料，請設定為 1。</span><span class="sxs-lookup"><span data-stu-id="1494e-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="1494e-248">spatialMapping:記錄空間的對應，請設定為 1。</span><span class="sxs-lookup"><span data-stu-id="1494e-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="1494e-249">環境：若要記錄的環境資料，以設定為 1。</span><span class="sxs-lookup"><span data-stu-id="1494e-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="1494e-250">名稱：記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="1494e-250">name : Name of the recording.</span></span>
* <span data-ttu-id="1494e-251">singleSpatialMappingFrame:記錄只有單一空間對應的框架，請設定為 1。</span><span class="sxs-lookup"><span data-stu-id="1494e-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="1494e-252">**/api/holographic/simulation/recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="1494e-253">取得記錄狀態。</span><span class="sxs-lookup"><span data-stu-id="1494e-253">Get recording state.</span></span>

<span data-ttu-id="1494e-254">**/api/holographic/simulation/recording/stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="1494e-255">停止目前的錄製。</span><span class="sxs-lookup"><span data-stu-id="1494e-255">Stop the current recording.</span></span> <span data-ttu-id="1494e-256">為檔案，將會傳回記錄。</span><span class="sxs-lookup"><span data-stu-id="1494e-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="1494e-257">混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="1494e-257">Mixed Reality Capture</span></span>

<span data-ttu-id="1494e-258">**/api/holographic/mrc/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="1494e-258">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="1494e-259">刪除混合的實境，從裝置記錄。</span><span class="sxs-lookup"><span data-stu-id="1494e-259">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="1494e-260">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-260">Parameters</span></span>
* <span data-ttu-id="1494e-261">檔案名稱：編碼時，要刪除之檔案的名稱，hex64</span><span class="sxs-lookup"><span data-stu-id="1494e-261">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="1494e-262">**/api/holographic/mrc/settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-262">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="1494e-263">取得預設的混合實境擷取設定</span><span class="sxs-lookup"><span data-stu-id="1494e-263">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="1494e-264">**/api/holographic/mrc/file (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-264">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="1494e-265">從裝置的混合的實境檔案下載。</span><span class="sxs-lookup"><span data-stu-id="1494e-265">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="1494e-266">使用 op = 進行串流處理的資料流查詢參數。</span><span class="sxs-lookup"><span data-stu-id="1494e-266">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="1494e-267">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-267">Parameters</span></span>
* <span data-ttu-id="1494e-268">檔案名稱：編碼時，若要取得之視訊檔的名稱，hex64</span><span class="sxs-lookup"><span data-stu-id="1494e-268">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="1494e-269">op： 資料流</span><span class="sxs-lookup"><span data-stu-id="1494e-269">op : stream</span></span>

<span data-ttu-id="1494e-270">**/api/holographic/mrc/thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-270">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="1494e-271">取得指定的檔案的縮圖影像。</span><span class="sxs-lookup"><span data-stu-id="1494e-271">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="1494e-272">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-272">Parameters</span></span>
* <span data-ttu-id="1494e-273">檔案名稱：編碼時，所要求的縮圖之檔案的名稱，hex64</span><span class="sxs-lookup"><span data-stu-id="1494e-273">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="1494e-274">**/api/holographic/mrc/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-274">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="1494e-275">取得混合實境記錄 （執行、 已停止） 的狀態</span><span class="sxs-lookup"><span data-stu-id="1494e-275">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="1494e-276">**/api/holographic/mrc/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-276">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="1494e-277">傳回儲存在裝置上的混合的實境檔案清單</span><span class="sxs-lookup"><span data-stu-id="1494e-277">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="1494e-278">**/api/holographic/mrc/settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="1494e-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="1494e-279">設定預設的混合實境擷取設定</span><span class="sxs-lookup"><span data-stu-id="1494e-279">Sets the default mixed reality capture settings</span></span>

<span data-ttu-id="1494e-280">**/api/holographic/mrc/video/control/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="1494e-280">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="1494e-281">開始混合的實境錄音</span><span class="sxs-lookup"><span data-stu-id="1494e-281">Starts a mixed reality recording</span></span>

<span data-ttu-id="1494e-282">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-282">Parameters</span></span>
* <span data-ttu-id="1494e-283">holo： 擷取全像投影： true 或 false</span><span class="sxs-lookup"><span data-stu-id="1494e-283">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="1494e-284">pv： 擷取 PV 相機： true 或 false</span><span class="sxs-lookup"><span data-stu-id="1494e-284">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="1494e-285">mic： 擷取麥克風： true 或 false</span><span class="sxs-lookup"><span data-stu-id="1494e-285">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="1494e-286">回送： 擷取應用程式音訊： true 或 false</span><span class="sxs-lookup"><span data-stu-id="1494e-286">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="1494e-287">**/api/holographic/mrc/video/control/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="1494e-287">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="1494e-288">停止目前的混合實境錄製</span><span class="sxs-lookup"><span data-stu-id="1494e-288">Stops the current mixed reality recording</span></span>

<span data-ttu-id="1494e-289">**/api/holographic/mrc/photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="1494e-289">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="1494e-290">採用混合的實境相片，並建立該裝置上的檔案</span><span class="sxs-lookup"><span data-stu-id="1494e-290">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="1494e-291">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-291">Parameters</span></span>
* <span data-ttu-id="1494e-292">holo： 擷取全像投影： true 或 false</span><span class="sxs-lookup"><span data-stu-id="1494e-292">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="1494e-293">pv： 擷取 PV 相機： true 或 false</span><span class="sxs-lookup"><span data-stu-id="1494e-293">pv : capture PV camera: true or false</span></span>

<span data-ttu-id="1494e-294">資料流的混合的實境</span><span class="sxs-lookup"><span data-stu-id="1494e-294">Mixed Reality Streaming</span></span>

<span data-ttu-id="1494e-295">**/api/holographic/stream/live.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-295">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="1494e-296">起始分段下載 mp4 片段</span><span class="sxs-lookup"><span data-stu-id="1494e-296">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="1494e-297">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-297">Parameters</span></span>
* <span data-ttu-id="1494e-298">holo： 擷取全像投影： true 或 false</span><span class="sxs-lookup"><span data-stu-id="1494e-298">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="1494e-299">pv： 擷取 PV 相機： true 或 false</span><span class="sxs-lookup"><span data-stu-id="1494e-299">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="1494e-300">mic： 擷取麥克風： true 或 false</span><span class="sxs-lookup"><span data-stu-id="1494e-300">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="1494e-301">回送： 擷取應用程式音訊： true 或 false</span><span class="sxs-lookup"><span data-stu-id="1494e-301">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="1494e-302">**/api/holographic/stream/live_high.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-302">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="1494e-303">起始分段下載 mp4 片段</span><span class="sxs-lookup"><span data-stu-id="1494e-303">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="1494e-304">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-304">Parameters</span></span>
* <span data-ttu-id="1494e-305">holo： 擷取全像投影： true 或 false</span><span class="sxs-lookup"><span data-stu-id="1494e-305">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="1494e-306">pv： 擷取 PV 相機： true 或 false</span><span class="sxs-lookup"><span data-stu-id="1494e-306">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="1494e-307">mic： 擷取麥克風： true 或 false</span><span class="sxs-lookup"><span data-stu-id="1494e-307">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="1494e-308">回送： 擷取應用程式音訊： true 或 false</span><span class="sxs-lookup"><span data-stu-id="1494e-308">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="1494e-309">**/api/holographic/stream/live_low.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-309">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="1494e-310">起始分段下載 mp4 片段</span><span class="sxs-lookup"><span data-stu-id="1494e-310">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="1494e-311">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-311">Parameters</span></span>
* <span data-ttu-id="1494e-312">holo： 擷取全像投影： true 或 false</span><span class="sxs-lookup"><span data-stu-id="1494e-312">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="1494e-313">pv： 擷取 PV 相機： true 或 false</span><span class="sxs-lookup"><span data-stu-id="1494e-313">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="1494e-314">mic： 擷取麥克風： true 或 false</span><span class="sxs-lookup"><span data-stu-id="1494e-314">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="1494e-315">回送： 擷取應用程式音訊： true 或 false</span><span class="sxs-lookup"><span data-stu-id="1494e-315">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="1494e-316">**/api/holographic/stream/live_med.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="1494e-317">起始分段下載 mp4 片段</span><span class="sxs-lookup"><span data-stu-id="1494e-317">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="1494e-318">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-318">Parameters</span></span>
* <span data-ttu-id="1494e-319">holo： 擷取全像投影： true 或 false</span><span class="sxs-lookup"><span data-stu-id="1494e-319">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="1494e-320">pv： 擷取 PV 相機： true 或 false</span><span class="sxs-lookup"><span data-stu-id="1494e-320">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="1494e-321">mic： 擷取麥克風： true 或 false</span><span class="sxs-lookup"><span data-stu-id="1494e-321">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="1494e-322">回送： 擷取應用程式音訊： true 或 false</span><span class="sxs-lookup"><span data-stu-id="1494e-322">loopback : capture app audio: true or false</span></span>

## <a name="networking"></a><span data-ttu-id="1494e-323">網路功能</span><span class="sxs-lookup"><span data-stu-id="1494e-323">Networking</span></span>

<span data-ttu-id="1494e-324">**/api/networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-324">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="1494e-325">取得目前的 ip 組態</span><span class="sxs-lookup"><span data-stu-id="1494e-325">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="1494e-326">OS 資訊</span><span class="sxs-lookup"><span data-stu-id="1494e-326">OS Information</span></span>

<span data-ttu-id="1494e-327">**/api/os/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-327">**/api/os/info (GET)**</span></span>

<span data-ttu-id="1494e-328">取得作業系統資訊</span><span class="sxs-lookup"><span data-stu-id="1494e-328">Gets operating system information</span></span>

<span data-ttu-id="1494e-329">**/api/os/machinename (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-329">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="1494e-330">取得電腦名稱</span><span class="sxs-lookup"><span data-stu-id="1494e-330">Gets the machine name</span></span>

<span data-ttu-id="1494e-331">**/api/os/machinename (POST)**</span><span class="sxs-lookup"><span data-stu-id="1494e-331">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="1494e-332">設定電腦名稱</span><span class="sxs-lookup"><span data-stu-id="1494e-332">Sets the machine name</span></span>

<span data-ttu-id="1494e-333">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-333">Parameters</span></span>
* <span data-ttu-id="1494e-334">名稱：新的機器名稱，hex64 編碼，將設定為</span><span class="sxs-lookup"><span data-stu-id="1494e-334">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="1494e-335">效能資料</span><span class="sxs-lookup"><span data-stu-id="1494e-335">Performance data</span></span>

<span data-ttu-id="1494e-336">**/api/resourcemanager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-336">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="1494e-337">傳回執行中處理序的詳細資料的清單</span><span class="sxs-lookup"><span data-stu-id="1494e-337">Returns the list of running processes with details</span></span>

<span data-ttu-id="1494e-338">傳回資料</span><span class="sxs-lookup"><span data-stu-id="1494e-338">Return data</span></span>
* <span data-ttu-id="1494e-339">JSON 與補充的處理序清單和每個處理序的詳細資料</span><span class="sxs-lookup"><span data-stu-id="1494e-339">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="1494e-340">**/api/resourcemanager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-340">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="1494e-341">傳回系統效能統計資料 （讀取/寫入 I/O、 記憶體統計資料等等。</span><span class="sxs-lookup"><span data-stu-id="1494e-341">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="1494e-342">傳回資料</span><span class="sxs-lookup"><span data-stu-id="1494e-342">Return data</span></span>
* <span data-ttu-id="1494e-343">JSON 與補充的系統資訊：CPU、 GPU、 記憶體、 網路、 IO</span><span class="sxs-lookup"><span data-stu-id="1494e-343">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="1494e-344">電源</span><span class="sxs-lookup"><span data-stu-id="1494e-344">Power</span></span>

<span data-ttu-id="1494e-345">**/api/power/battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-345">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="1494e-346">取得目前的電池狀態</span><span class="sxs-lookup"><span data-stu-id="1494e-346">Gets the current battery state</span></span>

<span data-ttu-id="1494e-347">**/api/power/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-347">**/api/power/state (GET)**</span></span>

<span data-ttu-id="1494e-348">檢查系統是否處於低電源狀態</span><span class="sxs-lookup"><span data-stu-id="1494e-348">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="1494e-349">遠端控制</span><span class="sxs-lookup"><span data-stu-id="1494e-349">Remote Control</span></span>

<span data-ttu-id="1494e-350">**/api/control/restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="1494e-350">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="1494e-351">重新啟動目標裝置</span><span class="sxs-lookup"><span data-stu-id="1494e-351">Restarts the target device</span></span>

<span data-ttu-id="1494e-352">**/api/control/shutdown （文章）**</span><span class="sxs-lookup"><span data-stu-id="1494e-352">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="1494e-353">關閉 目標裝置</span><span class="sxs-lookup"><span data-stu-id="1494e-353">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="1494e-354">工作管理員</span><span class="sxs-lookup"><span data-stu-id="1494e-354">Task Manager</span></span>

<span data-ttu-id="1494e-355">**/api/taskmanager/app (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="1494e-355">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="1494e-356">停止現代化的應用程式</span><span class="sxs-lookup"><span data-stu-id="1494e-356">Stops a modern app</span></span>

<span data-ttu-id="1494e-357">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-357">Parameters</span></span>
* <span data-ttu-id="1494e-358">封裝：完整的應用程式套件，hex64 編碼的名稱</span><span class="sxs-lookup"><span data-stu-id="1494e-358">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="1494e-359">強制停止：強制停止所有處理程序 （= yes）</span><span class="sxs-lookup"><span data-stu-id="1494e-359">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="1494e-360">**/api/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="1494e-360">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="1494e-361">啟動新式應用程式</span><span class="sxs-lookup"><span data-stu-id="1494e-361">Starts a modern app</span></span>

<span data-ttu-id="1494e-362">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-362">Parameters</span></span>
* <span data-ttu-id="1494e-363">appid:若要啟動的應用程式 PRAID，hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="1494e-363">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="1494e-364">封裝：完整的應用程式套件，hex64 編碼的名稱</span><span class="sxs-lookup"><span data-stu-id="1494e-364">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="1494e-365">WiFi 管理</span><span class="sxs-lookup"><span data-stu-id="1494e-365">WiFi Management</span></span>

<span data-ttu-id="1494e-366">**/api/wifi/interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-366">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="1494e-367">列舉無線網路介面</span><span class="sxs-lookup"><span data-stu-id="1494e-367">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="1494e-368">傳回資料</span><span class="sxs-lookup"><span data-stu-id="1494e-368">Return data</span></span>
* <span data-ttu-id="1494e-369">詳細資料 （GUID、 描述等） 的無線介面清單</span><span class="sxs-lookup"><span data-stu-id="1494e-369">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="1494e-370">**/api/wifi/network (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="1494e-370">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="1494e-371">刪除指定的介面上的網路相關聯的設定檔</span><span class="sxs-lookup"><span data-stu-id="1494e-371">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="1494e-372">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-372">Parameters</span></span>
* <span data-ttu-id="1494e-373">介面： 網路介面的 guid</span><span class="sxs-lookup"><span data-stu-id="1494e-373">interface : network interface guid</span></span>
* <span data-ttu-id="1494e-374">設定檔： 設定檔名稱</span><span class="sxs-lookup"><span data-stu-id="1494e-374">profile : profile name</span></span>

<span data-ttu-id="1494e-375">**/api/wifi/networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-375">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="1494e-376">列舉指定的網路介面上的無線網路</span><span class="sxs-lookup"><span data-stu-id="1494e-376">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="1494e-377">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-377">Parameters</span></span>
* <span data-ttu-id="1494e-378">介面： 網路介面的 guid</span><span class="sxs-lookup"><span data-stu-id="1494e-378">interface : network interface guid</span></span>

<span data-ttu-id="1494e-379">傳回資料</span><span class="sxs-lookup"><span data-stu-id="1494e-379">Return data</span></span>
* <span data-ttu-id="1494e-380">找到詳細資料的網路介面上的無線網路清單</span><span class="sxs-lookup"><span data-stu-id="1494e-380">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="1494e-381">**/api/wifi/network (POST)**</span><span class="sxs-lookup"><span data-stu-id="1494e-381">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="1494e-382">連線或中斷連線的指定介面上的網路</span><span class="sxs-lookup"><span data-stu-id="1494e-382">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="1494e-383">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-383">Parameters</span></span>
* <span data-ttu-id="1494e-384">介面： 網路介面的 guid</span><span class="sxs-lookup"><span data-stu-id="1494e-384">interface : network interface guid</span></span>
* <span data-ttu-id="1494e-385">ssid: ssid，hex64 編碼，來連接到</span><span class="sxs-lookup"><span data-stu-id="1494e-385">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="1494e-386">op： 連接或中斷連接</span><span class="sxs-lookup"><span data-stu-id="1494e-386">op : connect or disconnect</span></span>
* <span data-ttu-id="1494e-387">createprofile: yes 或 no</span><span class="sxs-lookup"><span data-stu-id="1494e-387">createprofile : yes or no</span></span>
* <span data-ttu-id="1494e-388">索引鍵： 共用的金鑰，hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="1494e-388">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="1494e-389">Windows Performance Recorder</span><span class="sxs-lookup"><span data-stu-id="1494e-389">Windows Performance Recorder</span></span>

<span data-ttu-id="1494e-390">**/api/wpr/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="1494e-390">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="1494e-391">上傳 WPR 設定檔，並開始追蹤使用已上傳設定檔。</span><span class="sxs-lookup"><span data-stu-id="1494e-391">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="1494e-392">承載</span><span class="sxs-lookup"><span data-stu-id="1494e-392">Payload</span></span>
* <span data-ttu-id="1494e-393">多部分符合的 http 內容</span><span class="sxs-lookup"><span data-stu-id="1494e-393">multi-part conforming http body</span></span>

<span data-ttu-id="1494e-394">傳回資料</span><span class="sxs-lookup"><span data-stu-id="1494e-394">Return data</span></span>
* <span data-ttu-id="1494e-395">傳回 WPR 工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="1494e-395">Returns the WPR session status.</span></span>

<span data-ttu-id="1494e-396">**/api/wpr/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-396">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="1494e-397">擷取 WPR 工作階段狀態</span><span class="sxs-lookup"><span data-stu-id="1494e-397">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="1494e-398">傳回資料</span><span class="sxs-lookup"><span data-stu-id="1494e-398">Return data</span></span>
* <span data-ttu-id="1494e-399">WPR 工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="1494e-399">WPR session status.</span></span>

<span data-ttu-id="1494e-400">**/api/wpr/trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="1494e-400">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="1494e-401">停止 WPR （效能） 追蹤工作階段</span><span class="sxs-lookup"><span data-stu-id="1494e-401">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="1494e-402">傳回資料</span><span class="sxs-lookup"><span data-stu-id="1494e-402">Return data</span></span>
* <span data-ttu-id="1494e-403">傳回追蹤 ETL 檔案</span><span class="sxs-lookup"><span data-stu-id="1494e-403">Returns the trace ETL file</span></span>

<span data-ttu-id="1494e-404">**/api/wpr/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="1494e-404">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="1494e-405">啟動追蹤工作階段 WPR （效能）</span><span class="sxs-lookup"><span data-stu-id="1494e-405">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="1494e-406">參數</span><span class="sxs-lookup"><span data-stu-id="1494e-406">Parameters</span></span>
* <span data-ttu-id="1494e-407">設定檔：設定檔名稱。</span><span class="sxs-lookup"><span data-stu-id="1494e-407">profile : Profile name.</span></span> <span data-ttu-id="1494e-408">可用的設定檔會儲存在 perfprofiles/profiles.json</span><span class="sxs-lookup"><span data-stu-id="1494e-408">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="1494e-409">傳回資料</span><span class="sxs-lookup"><span data-stu-id="1494e-409">Return data</span></span>
* <span data-ttu-id="1494e-410">在啟動時，會傳回 WPR 工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="1494e-410">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="1494e-411">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1494e-411">See also</span></span>
* [<span data-ttu-id="1494e-412">使用 Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="1494e-412">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="1494e-413">裝置入口網站 core API 參考 (UWP)</span><span class="sxs-lookup"><span data-stu-id="1494e-413">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
