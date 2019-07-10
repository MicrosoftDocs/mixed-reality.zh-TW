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
# <a name="device-portal-api-reference"></a><span data-ttu-id="d5065-104">裝置入口網站的 API 參考</span><span class="sxs-lookup"><span data-stu-id="d5065-104">Device portal API reference</span></span>

<span data-ttu-id="d5065-105">中的所有項目[Windows Device Portal](using-the-windows-device-portal.md)為建置基礎 REST API 可用來存取資料，並以程式設計方式控制您的裝置。</span><span class="sxs-lookup"><span data-stu-id="d5065-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="d5065-106">應用程式部署</span><span class="sxs-lookup"><span data-stu-id="d5065-106">App deloyment</span></span>

<span data-ttu-id="d5065-107">**/api/app/packagemanager/package (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="d5065-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="d5065-108">解除安裝應用程式</span><span class="sxs-lookup"><span data-stu-id="d5065-108">Uninstalls an app</span></span>

<span data-ttu-id="d5065-109">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-109">Parameters</span></span>
* <span data-ttu-id="d5065-110">封裝：要解除安裝之封裝的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="d5065-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="d5065-111">**/api/app/packagemanager/package (POST)**</span><span class="sxs-lookup"><span data-stu-id="d5065-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="d5065-112">安裝應用程式</span><span class="sxs-lookup"><span data-stu-id="d5065-112">Installs an App</span></span>

<span data-ttu-id="d5065-113">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-113">Parameters</span></span>
* <span data-ttu-id="d5065-114">封裝：要安裝之封裝的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="d5065-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="d5065-115">承載</span><span class="sxs-lookup"><span data-stu-id="d5065-115">Payload</span></span>
* <span data-ttu-id="d5065-116">多部分符合的 http 內容</span><span class="sxs-lookup"><span data-stu-id="d5065-116">multi-part conforming http body</span></span>

<span data-ttu-id="d5065-117">**/api/app/packagemanager/packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="d5065-118">擷取已安裝的應用程式在系統上，詳細資料清單</span><span class="sxs-lookup"><span data-stu-id="d5065-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="d5065-119">傳回資料</span><span class="sxs-lookup"><span data-stu-id="d5065-119">Return data</span></span>
* <span data-ttu-id="d5065-120">列出已安裝的套件詳細資料</span><span class="sxs-lookup"><span data-stu-id="d5065-120">List of installed packages with details</span></span>

<span data-ttu-id="d5065-121">**/api/app/packagemanager/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="d5065-122">取得中進行應用程式安裝狀態</span><span class="sxs-lookup"><span data-stu-id="d5065-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="d5065-123">傾印集合</span><span class="sxs-lookup"><span data-stu-id="d5065-123">Dump collection</span></span>

<span data-ttu-id="d5065-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="d5065-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="d5065-125">停用的損毀傾印集合的側載應用程式</span><span class="sxs-lookup"><span data-stu-id="d5065-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="d5065-126">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-126">Parameters</span></span>
* <span data-ttu-id="d5065-127">packageFullname： 封裝名稱</span><span class="sxs-lookup"><span data-stu-id="d5065-127">packageFullname : package name</span></span>

<span data-ttu-id="d5065-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="d5065-129">取得側載應用程式設定損毀傾印收集</span><span class="sxs-lookup"><span data-stu-id="d5065-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="d5065-130">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-130">Parameters</span></span>
* <span data-ttu-id="d5065-131">packageFullname： 封裝名稱</span><span class="sxs-lookup"><span data-stu-id="d5065-131">packageFullname : package name</span></span>

<span data-ttu-id="d5065-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="d5065-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="d5065-133">啟用並設定側載應用程式的傾印控制項設定</span><span class="sxs-lookup"><span data-stu-id="d5065-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="d5065-134">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-134">Parameters</span></span>
* <span data-ttu-id="d5065-135">packageFullname： 封裝名稱</span><span class="sxs-lookup"><span data-stu-id="d5065-135">packageFullname : package name</span></span>

<span data-ttu-id="d5065-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="d5065-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="d5065-137">刪除側載應用程式損毀傾印</span><span class="sxs-lookup"><span data-stu-id="d5065-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="d5065-138">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-138">Parameters</span></span>
* <span data-ttu-id="d5065-139">packageFullname： 封裝名稱</span><span class="sxs-lookup"><span data-stu-id="d5065-139">packageFullname : package name</span></span>
* <span data-ttu-id="d5065-140">fileName： 傾印檔案名稱</span><span class="sxs-lookup"><span data-stu-id="d5065-140">fileName : dump file name</span></span>

<span data-ttu-id="d5065-141">**/api/debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="d5065-142">擷取的側載應用程式損毀傾印</span><span class="sxs-lookup"><span data-stu-id="d5065-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="d5065-143">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-143">Parameters</span></span>
* <span data-ttu-id="d5065-144">packageFullname： 封裝名稱</span><span class="sxs-lookup"><span data-stu-id="d5065-144">packageFullname : package name</span></span>
* <span data-ttu-id="d5065-145">fileName： 傾印檔案名稱</span><span class="sxs-lookup"><span data-stu-id="d5065-145">fileName : dump file name</span></span>

<span data-ttu-id="d5065-146">傳回資料</span><span class="sxs-lookup"><span data-stu-id="d5065-146">Return data</span></span>
* <span data-ttu-id="d5065-147">傾印檔案。</span><span class="sxs-lookup"><span data-stu-id="d5065-147">Dump file.</span></span> <span data-ttu-id="d5065-148">檢查使用 WinDbg 或 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d5065-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="d5065-149">**/api/debug/dump/usermode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="d5065-150">傳回清單的側載應用程式的所有損毀傾印</span><span class="sxs-lookup"><span data-stu-id="d5065-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="d5065-151">傳回資料</span><span class="sxs-lookup"><span data-stu-id="d5065-151">Return data</span></span>
* <span data-ttu-id="d5065-152">每個側邊載入應用程式的清單中的損毀傾印</span><span class="sxs-lookup"><span data-stu-id="d5065-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="d5065-153">ETW</span><span class="sxs-lookup"><span data-stu-id="d5065-153">ETW</span></span>

<span data-ttu-id="d5065-154">**/api/etw/providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="d5065-155">列舉已註冊的提供者</span><span class="sxs-lookup"><span data-stu-id="d5065-155">Enumerates registered providers</span></span>

<span data-ttu-id="d5065-156">傳回資料</span><span class="sxs-lookup"><span data-stu-id="d5065-156">Return data</span></span>
* <span data-ttu-id="d5065-157">提供者、 易記名稱和 GUID 的清單</span><span class="sxs-lookup"><span data-stu-id="d5065-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="d5065-158">**/api/etw/session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="d5065-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="d5065-159">建立即時的 ETW 工作階段;透過 websocket 的管理。</span><span class="sxs-lookup"><span data-stu-id="d5065-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="d5065-160">傳回資料</span><span class="sxs-lookup"><span data-stu-id="d5065-160">Return data</span></span>
* <span data-ttu-id="d5065-161">從啟用的提供者的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="d5065-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="d5065-162">全像攝影版 OS</span><span class="sxs-lookup"><span data-stu-id="d5065-162">Holographic OS</span></span>

<span data-ttu-id="d5065-163">**/api/holographic/os/etw/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="d5065-164">傳回一份 HoloLens 特定 ETW 提供者不會向系統</span><span class="sxs-lookup"><span data-stu-id="d5065-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="d5065-165">**/api/holographic/os/services (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="d5065-166">傳回執行的所有服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="d5065-166">Returns the states of all services running.</span></span>

<span data-ttu-id="d5065-167">**/api/holographic/os/settings/ipd (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="d5065-168">取得在公釐為單位的預存的 IPD （Interpupillary 距離）</span><span class="sxs-lookup"><span data-stu-id="d5065-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="d5065-169">**/api/holographic/os/settings/ipd (POST)**</span><span class="sxs-lookup"><span data-stu-id="d5065-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="d5065-170">設定 IPD</span><span class="sxs-lookup"><span data-stu-id="d5065-170">Sets the IPD</span></span>

<span data-ttu-id="d5065-171">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-171">Parameters</span></span>
* <span data-ttu-id="d5065-172">ipd:若要設定以公釐新 IPD 值</span><span class="sxs-lookup"><span data-stu-id="d5065-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="d5065-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="d5065-174">取得 Device Portal 的 HTTPS 需求</span><span class="sxs-lookup"><span data-stu-id="d5065-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="d5065-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span><span class="sxs-lookup"><span data-stu-id="d5065-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="d5065-176">設定裝置入口網站的 HTTPS 需求</span><span class="sxs-lookup"><span data-stu-id="d5065-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="d5065-177">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-177">Parameters</span></span>
* <span data-ttu-id="d5065-178">必要： yes、 no 或預設值</span><span class="sxs-lookup"><span data-stu-id="d5065-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="d5065-179">全像攝影版的認知</span><span class="sxs-lookup"><span data-stu-id="d5065-179">Holographic Perception</span></span>

<span data-ttu-id="d5065-180">**/api/holographic/perception/client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="d5065-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="d5065-181">接受 websocket 升級，並會將更新傳送 30fps 在 perception 用戶端執行。</span><span class="sxs-lookup"><span data-stu-id="d5065-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="d5065-182">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-182">Parameters</span></span>
* <span data-ttu-id="d5065-183">clientmode: 「 作用中 」 時，會強制視覺追蹤模式無法被動地建立</span><span class="sxs-lookup"><span data-stu-id="d5065-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="d5065-184">全像攝影版的散熱</span><span class="sxs-lookup"><span data-stu-id="d5065-184">Holographic Thermal</span></span>

<span data-ttu-id="d5065-185">**/api/holographic/thermal/stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="d5065-186">取得裝置 （1 暖，重要的 2 中的 0 的標準模式） 的熱階段</span><span class="sxs-lookup"><span data-stu-id="d5065-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="d5065-187">Perception 模擬控制項</span><span class="sxs-lookup"><span data-stu-id="d5065-187">Perception Simulation Control</span></span>

<span data-ttu-id="d5065-188">**/api/holographic/simulation/control/mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="d5065-189">取得的模擬模式</span><span class="sxs-lookup"><span data-stu-id="d5065-189">Get the simulation mode</span></span>

<span data-ttu-id="d5065-190">**/api/holographic/simulation/control/mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="d5065-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="d5065-191">設定模擬模式</span><span class="sxs-lookup"><span data-stu-id="d5065-191">Set the simulation mode</span></span>

<span data-ttu-id="d5065-192">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-192">Parameters</span></span>
* <span data-ttu-id="d5065-193">模式： 模擬模式： 預設、 模擬、 遠端，舊版</span><span class="sxs-lookup"><span data-stu-id="d5065-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="d5065-194">**/api/holographic/simulation/control/stream （刪除）**</span><span class="sxs-lookup"><span data-stu-id="d5065-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="d5065-195">刪除控制資料流。</span><span class="sxs-lookup"><span data-stu-id="d5065-195">Delete a control stream.</span></span>

<span data-ttu-id="d5065-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="d5065-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="d5065-197">開啟 web 通訊端連線控制資料流。</span><span class="sxs-lookup"><span data-stu-id="d5065-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="d5065-198">**/api/holographic/simulation/control/stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="d5065-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="d5065-199">建立控制項的資料流 （優先順序是必要的） 或將資料公佈至建立的資料流 (所需的 streamId)。</span><span class="sxs-lookup"><span data-stu-id="d5065-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="d5065-200">張貼的資料應該是類型 ' 應用程式/八位元資料流 '。</span><span class="sxs-lookup"><span data-stu-id="d5065-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="d5065-201">Perception 模擬播放</span><span class="sxs-lookup"><span data-stu-id="d5065-201">Perception Simulation Playback</span></span>

<span data-ttu-id="d5065-202">**/api/holographic/simulation/playback/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="d5065-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="d5065-203">刪除記錄。</span><span class="sxs-lookup"><span data-stu-id="d5065-203">Delete a recording.</span></span>

<span data-ttu-id="d5065-204">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-204">Parameters</span></span>
* <span data-ttu-id="d5065-205">記錄：若要刪除記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="d5065-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="d5065-206">**/api/holographic/simulation/playback/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="d5065-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="d5065-207">上傳的記錄。</span><span class="sxs-lookup"><span data-stu-id="d5065-207">Upload a recording.</span></span>

<span data-ttu-id="d5065-208">**/api/holographic/simulation/playback/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="d5065-209">取得所有記錄。</span><span class="sxs-lookup"><span data-stu-id="d5065-209">Get all recordings.</span></span>

<span data-ttu-id="d5065-210">**/api/holographic/simulation/playback/session (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="d5065-211">取得目前的錄製播放狀態。</span><span class="sxs-lookup"><span data-stu-id="d5065-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="d5065-212">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-212">Parameters</span></span>
* <span data-ttu-id="d5065-213">記錄：記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="d5065-213">recording : Name of recording.</span></span>

<span data-ttu-id="d5065-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="d5065-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="d5065-215">卸載錄製。</span><span class="sxs-lookup"><span data-stu-id="d5065-215">Unload a recording.</span></span>

<span data-ttu-id="d5065-216">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-216">Parameters</span></span>
* <span data-ttu-id="d5065-217">記錄：卸載所記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="d5065-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="d5065-218">**/api/holographic/simulation/playback/session/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="d5065-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="d5065-219">載入記錄。</span><span class="sxs-lookup"><span data-stu-id="d5065-219">Load a recording.</span></span>

<span data-ttu-id="d5065-220">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-220">Parameters</span></span>
* <span data-ttu-id="d5065-221">記錄：載入記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="d5065-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="d5065-222">**/api/holographic/simulation/playback/session/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="d5065-223">取得載入的所有記錄。</span><span class="sxs-lookup"><span data-stu-id="d5065-223">Get all loaded recordings.</span></span>

<span data-ttu-id="d5065-224">**/api/holographic/simulation/playback/session/pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="d5065-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="d5065-225">暫停錄製。</span><span class="sxs-lookup"><span data-stu-id="d5065-225">Pause a recording.</span></span>

<span data-ttu-id="d5065-226">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-226">Parameters</span></span>
* <span data-ttu-id="d5065-227">記錄：記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="d5065-227">recording : Name of recording.</span></span>

<span data-ttu-id="d5065-228">**/api/holographic/simulation/playback/session/play (POST)**</span><span class="sxs-lookup"><span data-stu-id="d5065-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="d5065-229">播放錄製。</span><span class="sxs-lookup"><span data-stu-id="d5065-229">Play a recording.</span></span>

<span data-ttu-id="d5065-230">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-230">Parameters</span></span>
* <span data-ttu-id="d5065-231">記錄：記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="d5065-231">recording : Name of recording.</span></span>

<span data-ttu-id="d5065-232">**/api/holographic/simulation/playback/session/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="d5065-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="d5065-233">停止錄製。</span><span class="sxs-lookup"><span data-stu-id="d5065-233">Stop a recording.</span></span>

<span data-ttu-id="d5065-234">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-234">Parameters</span></span>
* <span data-ttu-id="d5065-235">記錄：記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="d5065-235">recording : Name of recording.</span></span>

<span data-ttu-id="d5065-236">**/api/holographic/simulation/playback/session/types (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="d5065-237">載入的記錄中取得資料的類型。</span><span class="sxs-lookup"><span data-stu-id="d5065-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="d5065-238">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-238">Parameters</span></span>
* <span data-ttu-id="d5065-239">記錄：記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="d5065-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="d5065-240">Perception 模擬記錄</span><span class="sxs-lookup"><span data-stu-id="d5065-240">Perception Simulation Recording</span></span>

<span data-ttu-id="d5065-241">**/api/holographic/simulation/recording/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="d5065-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="d5065-242">開始錄製。</span><span class="sxs-lookup"><span data-stu-id="d5065-242">Start a recording.</span></span> <span data-ttu-id="d5065-243">可同時處於作用中單一記錄。</span><span class="sxs-lookup"><span data-stu-id="d5065-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="d5065-244">必須設定其中一個標頭、 實際操作、 spatialMapping 或環境。</span><span class="sxs-lookup"><span data-stu-id="d5065-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="d5065-245">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-245">Parameters</span></span>
* <span data-ttu-id="d5065-246">前端：設定為 1，以記錄標頭的資料。</span><span class="sxs-lookup"><span data-stu-id="d5065-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="d5065-247">實際操作：記錄手動資料，請設定為 1。</span><span class="sxs-lookup"><span data-stu-id="d5065-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="d5065-248">spatialMapping:記錄空間的對應，請設定為 1。</span><span class="sxs-lookup"><span data-stu-id="d5065-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="d5065-249">環境：若要記錄的環境資料，以設定為 1。</span><span class="sxs-lookup"><span data-stu-id="d5065-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="d5065-250">名稱：記錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="d5065-250">name : Name of the recording.</span></span>
* <span data-ttu-id="d5065-251">singleSpatialMappingFrame:記錄只有單一空間對應的框架，請設定為 1。</span><span class="sxs-lookup"><span data-stu-id="d5065-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="d5065-252">**/api/holographic/simulation/recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="d5065-253">取得記錄狀態。</span><span class="sxs-lookup"><span data-stu-id="d5065-253">Get recording state.</span></span>

<span data-ttu-id="d5065-254">**/api/holographic/simulation/recording/stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="d5065-255">停止目前的錄製。</span><span class="sxs-lookup"><span data-stu-id="d5065-255">Stop the current recording.</span></span> <span data-ttu-id="d5065-256">為檔案，將會傳回記錄。</span><span class="sxs-lookup"><span data-stu-id="d5065-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="d5065-257">混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="d5065-257">Mixed Reality Capture</span></span>

<span data-ttu-id="d5065-258">**/api/holographic/mrc/file (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="d5065-259">從裝置的混合的實境檔案下載。</span><span class="sxs-lookup"><span data-stu-id="d5065-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="d5065-260">使用 op = 進行串流處理的資料流查詢參數。</span><span class="sxs-lookup"><span data-stu-id="d5065-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="d5065-261">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-261">Parameters</span></span>
* <span data-ttu-id="d5065-262">檔案名稱：編碼時，若要取得之視訊檔的名稱，hex64</span><span class="sxs-lookup"><span data-stu-id="d5065-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="d5065-263">op： 資料流</span><span class="sxs-lookup"><span data-stu-id="d5065-263">op : stream</span></span>

<span data-ttu-id="d5065-264">**/api/holographic/mrc/file (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="d5065-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="d5065-265">刪除混合的實境，從裝置記錄。</span><span class="sxs-lookup"><span data-stu-id="d5065-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="d5065-266">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-266">Parameters</span></span>
* <span data-ttu-id="d5065-267">檔案名稱：編碼時，要刪除之檔案的名稱，hex64</span><span class="sxs-lookup"><span data-stu-id="d5065-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="d5065-268">**/api/holographic/mrc/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="d5065-269">傳回儲存在裝置上的混合的實境檔案清單</span><span class="sxs-lookup"><span data-stu-id="d5065-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="d5065-270">**/api/holographic/mrc/photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="d5065-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="d5065-271">採用混合的實境相片，並建立該裝置上的檔案</span><span class="sxs-lookup"><span data-stu-id="d5065-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="d5065-272">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-272">Parameters</span></span>
* <span data-ttu-id="d5065-273">holo： 擷取全像投影： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="d5065-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="d5065-274">pv： 擷取 PV 相機： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="d5065-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="d5065-275">RenderFromCamera:從相片/攝影機角度 (HoloLens 2) 轉譯： true 或 false （預設為 true）</span><span class="sxs-lookup"><span data-stu-id="d5065-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="d5065-276">**/api/holographic/mrc/settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="d5065-277">取得預設的混合實境擷取設定</span><span class="sxs-lookup"><span data-stu-id="d5065-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="d5065-278">**/api/holographic/mrc/settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="d5065-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="d5065-279">設定預設的混合實境擷取設定。</span><span class="sxs-lookup"><span data-stu-id="d5065-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="d5065-280">其中某些設定會套用至系統的 MRC 相片和視訊擷取。</span><span class="sxs-lookup"><span data-stu-id="d5065-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="d5065-281">**/api/holographic/mrc/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="d5065-282">取得混合實境記錄 （執行、 已停止） 的狀態</span><span class="sxs-lookup"><span data-stu-id="d5065-282">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="d5065-283">**/api/holographic/mrc/thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-283">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="d5065-284">取得指定的檔案的縮圖影像。</span><span class="sxs-lookup"><span data-stu-id="d5065-284">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="d5065-285">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-285">Parameters</span></span>
* <span data-ttu-id="d5065-286">檔案名稱：編碼時，所要求的縮圖之檔案的名稱，hex64</span><span class="sxs-lookup"><span data-stu-id="d5065-286">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="d5065-287">**/api/holographic/mrc/video/control/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="d5065-287">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="d5065-288">開始混合的實境錄音</span><span class="sxs-lookup"><span data-stu-id="d5065-288">Starts a mixed reality recording</span></span>

<span data-ttu-id="d5065-289">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-289">Parameters</span></span>
* <span data-ttu-id="d5065-290">holo： 擷取全像投影： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="d5065-290">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="d5065-291">pv： 擷取 PV 相機： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="d5065-291">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="d5065-292">mic： 擷取麥克風： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="d5065-292">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="d5065-293">回送： 擷取應用程式音訊： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="d5065-293">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="d5065-294">RenderFromCamera:從相片/攝影機角度 (HoloLens 2) 轉譯： true 或 false （預設為 true）</span><span class="sxs-lookup"><span data-stu-id="d5065-294">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="d5065-295">vstab:(HoloLens 2) 啟用視訊穩定功能： true 或 false （預設為 true）</span><span class="sxs-lookup"><span data-stu-id="d5065-295">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="d5065-296">vstabbuffer:(HoloLens 2) 視訊穩定緩衝區延遲：0 到 30 個畫面格 （預設為 15 的畫面格）</span><span class="sxs-lookup"><span data-stu-id="d5065-296">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="d5065-297">**/api/holographic/mrc/video/control/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="d5065-297">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="d5065-298">停止目前的混合實境錄製</span><span class="sxs-lookup"><span data-stu-id="d5065-298">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="d5065-299">資料流的混合的實境</span><span class="sxs-lookup"><span data-stu-id="d5065-299">Mixed Reality Streaming</span></span>

<span data-ttu-id="d5065-300">HoloLens 支援混合實境透過區塊下載的分散 mp4 即時的預覽。</span><span class="sxs-lookup"><span data-stu-id="d5065-300">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="d5065-301">混合的實境資料流共用相同的參數來控制什麼擷取一組：</span><span class="sxs-lookup"><span data-stu-id="d5065-301">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="d5065-302">holo： 擷取全像投影： true 或 false</span><span class="sxs-lookup"><span data-stu-id="d5065-302">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="d5065-303">pv： 擷取 PV 相機： true 或 false</span><span class="sxs-lookup"><span data-stu-id="d5065-303">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="d5065-304">mic： 擷取麥克風： true 或 false</span><span class="sxs-lookup"><span data-stu-id="d5065-304">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="d5065-305">回送： 擷取應用程式音訊： true 或 false</span><span class="sxs-lookup"><span data-stu-id="d5065-305">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="d5065-306">如果指定了其中一個項目： 將擷取全像投影、 相片或視訊攝影機和應用程式音訊</span><span class="sxs-lookup"><span data-stu-id="d5065-306">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="d5065-307">如果指定了任何： 未指定的參數會預設為 false</span><span class="sxs-lookup"><span data-stu-id="d5065-307">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="d5065-308">選擇性參數 (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="d5065-308">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="d5065-309">RenderFromCamera: 從相片/影片相機的觀點來看，呈現: true 或 false （預設為 true）</span><span class="sxs-lookup"><span data-stu-id="d5065-309">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="d5065-310">vstab： 啟用視訊穩定功能： true 或 false （預設為 false）</span><span class="sxs-lookup"><span data-stu-id="d5065-310">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="d5065-311">vstabbuffer： 視訊穩定緩衝區延遲：0 到 30 個畫面格 （預設為 15 的畫面格）</span><span class="sxs-lookup"><span data-stu-id="d5065-311">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="d5065-312">**/api/holographic/stream/live.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-312">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="d5065-313">1280x720p 30fps 5Mbit 資料流。</span><span class="sxs-lookup"><span data-stu-id="d5065-313">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="d5065-314">**/api/holographic/stream/live_high.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-314">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="d5065-315">1280x720p 30fps 5Mbit 資料流。</span><span class="sxs-lookup"><span data-stu-id="d5065-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="d5065-316">**/api/holographic/stream/live_med.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="d5065-317">854x480p 30fps 2.5Mbit 資料流。</span><span class="sxs-lookup"><span data-stu-id="d5065-317">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="d5065-318">**/api/holographic/stream/live_low.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-318">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="d5065-319">428x240p 15 fps 0.6Mbit 資料流。</span><span class="sxs-lookup"><span data-stu-id="d5065-319">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="d5065-320">網路功能</span><span class="sxs-lookup"><span data-stu-id="d5065-320">Networking</span></span>

<span data-ttu-id="d5065-321">**/api/networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-321">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="d5065-322">取得目前的 ip 組態</span><span class="sxs-lookup"><span data-stu-id="d5065-322">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="d5065-323">OS 資訊</span><span class="sxs-lookup"><span data-stu-id="d5065-323">OS Information</span></span>

<span data-ttu-id="d5065-324">**/api/os/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-324">**/api/os/info (GET)**</span></span>

<span data-ttu-id="d5065-325">取得作業系統資訊</span><span class="sxs-lookup"><span data-stu-id="d5065-325">Gets operating system information</span></span>

<span data-ttu-id="d5065-326">**/api/os/machinename (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-326">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="d5065-327">取得電腦名稱</span><span class="sxs-lookup"><span data-stu-id="d5065-327">Gets the machine name</span></span>

<span data-ttu-id="d5065-328">**/api/os/machinename (POST)**</span><span class="sxs-lookup"><span data-stu-id="d5065-328">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="d5065-329">設定電腦名稱</span><span class="sxs-lookup"><span data-stu-id="d5065-329">Sets the machine name</span></span>

<span data-ttu-id="d5065-330">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-330">Parameters</span></span>
* <span data-ttu-id="d5065-331">名稱：新的機器名稱，hex64 編碼，將設定為</span><span class="sxs-lookup"><span data-stu-id="d5065-331">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="d5065-332">效能資料</span><span class="sxs-lookup"><span data-stu-id="d5065-332">Performance data</span></span>

<span data-ttu-id="d5065-333">**/api/resourcemanager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-333">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="d5065-334">傳回執行中處理序的詳細資料的清單</span><span class="sxs-lookup"><span data-stu-id="d5065-334">Returns the list of running processes with details</span></span>

<span data-ttu-id="d5065-335">傳回資料</span><span class="sxs-lookup"><span data-stu-id="d5065-335">Return data</span></span>
* <span data-ttu-id="d5065-336">JSON 與補充的處理序清單和每個處理序的詳細資料</span><span class="sxs-lookup"><span data-stu-id="d5065-336">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="d5065-337">**/api/resourcemanager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-337">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="d5065-338">傳回系統效能統計資料 （讀取/寫入 I/O、 記憶體統計資料等等。</span><span class="sxs-lookup"><span data-stu-id="d5065-338">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="d5065-339">傳回資料</span><span class="sxs-lookup"><span data-stu-id="d5065-339">Return data</span></span>
* <span data-ttu-id="d5065-340">JSON 與補充的系統資訊：CPU、 GPU、 記憶體、 網路、 IO</span><span class="sxs-lookup"><span data-stu-id="d5065-340">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="d5065-341">電源</span><span class="sxs-lookup"><span data-stu-id="d5065-341">Power</span></span>

<span data-ttu-id="d5065-342">**/api/power/battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-342">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="d5065-343">取得目前的電池狀態</span><span class="sxs-lookup"><span data-stu-id="d5065-343">Gets the current battery state</span></span>

<span data-ttu-id="d5065-344">**/api/power/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-344">**/api/power/state (GET)**</span></span>

<span data-ttu-id="d5065-345">檢查系統是否處於低電源狀態</span><span class="sxs-lookup"><span data-stu-id="d5065-345">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="d5065-346">遠端控制</span><span class="sxs-lookup"><span data-stu-id="d5065-346">Remote Control</span></span>

<span data-ttu-id="d5065-347">**/api/control/restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="d5065-347">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="d5065-348">重新啟動目標裝置</span><span class="sxs-lookup"><span data-stu-id="d5065-348">Restarts the target device</span></span>

<span data-ttu-id="d5065-349">**/api/control/shutdown （文章）**</span><span class="sxs-lookup"><span data-stu-id="d5065-349">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="d5065-350">關閉 目標裝置</span><span class="sxs-lookup"><span data-stu-id="d5065-350">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="d5065-351">工作管理員</span><span class="sxs-lookup"><span data-stu-id="d5065-351">Task Manager</span></span>

<span data-ttu-id="d5065-352">**/api/taskmanager/app (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="d5065-352">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="d5065-353">停止現代化的應用程式</span><span class="sxs-lookup"><span data-stu-id="d5065-353">Stops a modern app</span></span>

<span data-ttu-id="d5065-354">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-354">Parameters</span></span>
* <span data-ttu-id="d5065-355">封裝：完整的應用程式套件，hex64 編碼的名稱</span><span class="sxs-lookup"><span data-stu-id="d5065-355">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="d5065-356">強制停止：強制停止所有處理程序 （= yes）</span><span class="sxs-lookup"><span data-stu-id="d5065-356">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="d5065-357">**/api/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="d5065-357">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="d5065-358">啟動新式應用程式</span><span class="sxs-lookup"><span data-stu-id="d5065-358">Starts a modern app</span></span>

<span data-ttu-id="d5065-359">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-359">Parameters</span></span>
* <span data-ttu-id="d5065-360">appid:若要啟動的應用程式 PRAID，hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="d5065-360">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="d5065-361">封裝：完整的應用程式套件，hex64 編碼的名稱</span><span class="sxs-lookup"><span data-stu-id="d5065-361">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="d5065-362">WiFi 管理</span><span class="sxs-lookup"><span data-stu-id="d5065-362">WiFi Management</span></span>

<span data-ttu-id="d5065-363">**/api/wifi/interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-363">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="d5065-364">列舉無線網路介面</span><span class="sxs-lookup"><span data-stu-id="d5065-364">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="d5065-365">傳回資料</span><span class="sxs-lookup"><span data-stu-id="d5065-365">Return data</span></span>
* <span data-ttu-id="d5065-366">詳細資料 （GUID、 描述等） 的無線介面清單</span><span class="sxs-lookup"><span data-stu-id="d5065-366">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="d5065-367">**/api/wifi/network (DELETE)**</span><span class="sxs-lookup"><span data-stu-id="d5065-367">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="d5065-368">刪除指定的介面上的網路相關聯的設定檔</span><span class="sxs-lookup"><span data-stu-id="d5065-368">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="d5065-369">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-369">Parameters</span></span>
* <span data-ttu-id="d5065-370">介面： 網路介面的 guid</span><span class="sxs-lookup"><span data-stu-id="d5065-370">interface : network interface guid</span></span>
* <span data-ttu-id="d5065-371">設定檔： 設定檔名稱</span><span class="sxs-lookup"><span data-stu-id="d5065-371">profile : profile name</span></span>

<span data-ttu-id="d5065-372">**/api/wifi/networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-372">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="d5065-373">列舉指定的網路介面上的無線網路</span><span class="sxs-lookup"><span data-stu-id="d5065-373">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="d5065-374">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-374">Parameters</span></span>
* <span data-ttu-id="d5065-375">介面： 網路介面的 guid</span><span class="sxs-lookup"><span data-stu-id="d5065-375">interface : network interface guid</span></span>

<span data-ttu-id="d5065-376">傳回資料</span><span class="sxs-lookup"><span data-stu-id="d5065-376">Return data</span></span>
* <span data-ttu-id="d5065-377">找到詳細資料的網路介面上的無線網路清單</span><span class="sxs-lookup"><span data-stu-id="d5065-377">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="d5065-378">**/api/wifi/network (POST)**</span><span class="sxs-lookup"><span data-stu-id="d5065-378">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="d5065-379">連線或中斷連線的指定介面上的網路</span><span class="sxs-lookup"><span data-stu-id="d5065-379">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="d5065-380">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-380">Parameters</span></span>
* <span data-ttu-id="d5065-381">介面： 網路介面的 guid</span><span class="sxs-lookup"><span data-stu-id="d5065-381">interface : network interface guid</span></span>
* <span data-ttu-id="d5065-382">ssid: ssid，hex64 編碼，來連接到</span><span class="sxs-lookup"><span data-stu-id="d5065-382">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="d5065-383">op： 連接或中斷連接</span><span class="sxs-lookup"><span data-stu-id="d5065-383">op : connect or disconnect</span></span>
* <span data-ttu-id="d5065-384">createprofile: yes 或 no</span><span class="sxs-lookup"><span data-stu-id="d5065-384">createprofile : yes or no</span></span>
* <span data-ttu-id="d5065-385">索引鍵： 共用的金鑰，hex64 編碼</span><span class="sxs-lookup"><span data-stu-id="d5065-385">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="d5065-386">Windows Performance Recorder</span><span class="sxs-lookup"><span data-stu-id="d5065-386">Windows Performance Recorder</span></span>

<span data-ttu-id="d5065-387">**/api/wpr/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="d5065-387">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="d5065-388">上傳 WPR 設定檔，並開始追蹤使用已上傳設定檔。</span><span class="sxs-lookup"><span data-stu-id="d5065-388">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="d5065-389">承載</span><span class="sxs-lookup"><span data-stu-id="d5065-389">Payload</span></span>
* <span data-ttu-id="d5065-390">多部分符合的 http 內容</span><span class="sxs-lookup"><span data-stu-id="d5065-390">multi-part conforming http body</span></span>

<span data-ttu-id="d5065-391">傳回資料</span><span class="sxs-lookup"><span data-stu-id="d5065-391">Return data</span></span>
* <span data-ttu-id="d5065-392">傳回 WPR 工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="d5065-392">Returns the WPR session status.</span></span>

<span data-ttu-id="d5065-393">**/api/wpr/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-393">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="d5065-394">擷取 WPR 工作階段狀態</span><span class="sxs-lookup"><span data-stu-id="d5065-394">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="d5065-395">傳回資料</span><span class="sxs-lookup"><span data-stu-id="d5065-395">Return data</span></span>
* <span data-ttu-id="d5065-396">WPR 工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="d5065-396">WPR session status.</span></span>

<span data-ttu-id="d5065-397">**/api/wpr/trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="d5065-397">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="d5065-398">停止 WPR （效能） 追蹤工作階段</span><span class="sxs-lookup"><span data-stu-id="d5065-398">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="d5065-399">傳回資料</span><span class="sxs-lookup"><span data-stu-id="d5065-399">Return data</span></span>
* <span data-ttu-id="d5065-400">傳回追蹤 ETL 檔案</span><span class="sxs-lookup"><span data-stu-id="d5065-400">Returns the trace ETL file</span></span>

<span data-ttu-id="d5065-401">**/api/wpr/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="d5065-401">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="d5065-402">啟動追蹤工作階段 WPR （效能）</span><span class="sxs-lookup"><span data-stu-id="d5065-402">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="d5065-403">參數</span><span class="sxs-lookup"><span data-stu-id="d5065-403">Parameters</span></span>
* <span data-ttu-id="d5065-404">設定檔：設定檔名稱。</span><span class="sxs-lookup"><span data-stu-id="d5065-404">profile : Profile name.</span></span> <span data-ttu-id="d5065-405">可用的設定檔會儲存在 perfprofiles/profiles.json</span><span class="sxs-lookup"><span data-stu-id="d5065-405">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="d5065-406">傳回資料</span><span class="sxs-lookup"><span data-stu-id="d5065-406">Return data</span></span>
* <span data-ttu-id="d5065-407">在啟動時，會傳回 WPR 工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="d5065-407">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="d5065-408">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5065-408">See also</span></span>
* [<span data-ttu-id="d5065-409">使用 Windows 裝置入口網站</span><span class="sxs-lookup"><span data-stu-id="d5065-409">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="d5065-410">裝置入口網站 core API 參考 (UWP)</span><span class="sxs-lookup"><span data-stu-id="d5065-410">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
