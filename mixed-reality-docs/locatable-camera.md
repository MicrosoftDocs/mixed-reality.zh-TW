---
title: 之外的可尋獲相機
description: HoloLens 前方相機、 其運作方式，和設定檔的一般資訊和開發人員可使用的解決方式。
author: wguyman
ms.author: wguyman
ms.date: 06/12/2019
ms.topic: article
keywords: 相機、 hololens、 色彩相機、 面向、 hololens 2，cv，電腦視覺，fiducial 前端、 標記、 qr 代碼、 qr、 相片、 視訊
ms.openlocfilehash: cadcd0762b8adf1001896c614451d2e1c9776c65
ms.sourcegitcommit: 79398a6b5b7037babcb05d86a5bcc336fd089ea0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2019
ms.locfileid: "67028609"
---
# <a name="locatable-camera"></a><span data-ttu-id="e678f-104">之外的可尋獲相機</span><span class="sxs-lookup"><span data-stu-id="e678f-104">Locatable camera</span></span>

<span data-ttu-id="e678f-105">HoloLens 包含可讓應用程式，以查看使用者會看到裝置的正面掛接世界相機。</span><span class="sxs-lookup"><span data-stu-id="e678f-105">HoloLens includes a world-facing camera mounted on the front of the device which enables apps to see what the user sees.</span></span> <span data-ttu-id="e678f-106">開發人員可以存取及控制相機，就像智慧型手機、 portables 或桌上型電腦上的色彩相機。</span><span class="sxs-lookup"><span data-stu-id="e678f-106">Developers have access to and control of the camera just as they would for color cameras on smartphones, portables, or desktops.</span></span> <span data-ttu-id="e678f-107">相同的通用 windows[媒體擷取](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx)和 HoloLens 上的 windows 媒體基礎作用於行動和桌面的 Api 運作。</span><span class="sxs-lookup"><span data-stu-id="e678f-107">The same universal windows [media capture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) and windows media foundation APIs that work on mobile and desktop work on HoloLens.</span></span> <span data-ttu-id="e678f-108">Unity[也已包裝這些 windows Api](locatable-camera-in-unity.md)抽取 HoloLens 上的相機，進行工作，例如採用一般的相片和視訊 （不論有無全像投影），並尋找中的鏡頭位置和檢視方塊上的簡單使用方式場景。</span><span class="sxs-lookup"><span data-stu-id="e678f-108">Unity [has also wrapped these windows APIs](locatable-camera-in-unity.md) to abstract simple usage of the camera on HoloLens for tasks such as taking regular photos and videos (with or without holograms) and locating the camera's position in and perspective on the scene.</span></span>

## <a name="device-camera-information"></a><span data-ttu-id="e678f-109">裝置相機資訊</span><span class="sxs-lookup"><span data-stu-id="e678f-109">Device camera information</span></span>

### <a name="hololens-first-generation"></a><span data-ttu-id="e678f-110">HoloLens （第一代）</span><span class="sxs-lookup"><span data-stu-id="e678f-110">HoloLens (first-generation)</span></span>

* <span data-ttu-id="e678f-111">已修正的焦點相片/影片 (PV) 相機白色自動平衡、 自動曝光，與完整的映像處理管線。</span><span class="sxs-lookup"><span data-stu-id="e678f-111">Fixed focus photo/video (PV) camera with auto white balance, auto exposure, and full image processing pipeline.</span></span>
* <span data-ttu-id="e678f-112">面向世界的白色隱私權 LED 將會位於相機作用中時</span><span class="sxs-lookup"><span data-stu-id="e678f-112">White Privacy LED facing the world will illuminate whenever the camera is active</span></span>
* <span data-ttu-id="e678f-113">相機支援下列模式 （所有模式都是 16:9 外觀比例） 在 30、 24、 20、 15 及 5 的 fps:</span><span class="sxs-lookup"><span data-stu-id="e678f-113">The camera supports the following modes (all modes are 16:9 aspect ratio) at 30, 24, 20, 15, and 5 fps:</span></span>

  |  <span data-ttu-id="e678f-114">視訊</span><span class="sxs-lookup"><span data-stu-id="e678f-114">Video</span></span>  |  <span data-ttu-id="e678f-115">預覽</span><span class="sxs-lookup"><span data-stu-id="e678f-115">Preview</span></span>  |  <span data-ttu-id="e678f-116">仍</span><span class="sxs-lookup"><span data-stu-id="e678f-116">Still</span></span>  |  <span data-ttu-id="e678f-117">水平視野 (H FOV)</span><span class="sxs-lookup"><span data-stu-id="e678f-117">Horizontal Field of View (H-FOV)</span></span> |  <span data-ttu-id="e678f-118">建議的用法</span><span class="sxs-lookup"><span data-stu-id="e678f-118">Suggested usage</span></span> | 
  |----------|----------|----------|----------|----------|
  |  <span data-ttu-id="e678f-119">1280x720</span><span class="sxs-lookup"><span data-stu-id="e678f-119">1280x720</span></span> |  <span data-ttu-id="e678f-120">1280x720</span><span class="sxs-lookup"><span data-stu-id="e678f-120">1280x720</span></span> |  <span data-ttu-id="e678f-121">1280x720</span><span class="sxs-lookup"><span data-stu-id="e678f-121">1280x720</span></span> |  <span data-ttu-id="e678f-122">45deg</span><span class="sxs-lookup"><span data-stu-id="e678f-122">45deg</span></span>  |  <span data-ttu-id="e678f-123">（透過視訊穩定功能的預設模式）</span><span class="sxs-lookup"><span data-stu-id="e678f-123">(default mode with video stabilization)</span></span> | 
  |  <span data-ttu-id="e678f-124">N/A</span><span class="sxs-lookup"><span data-stu-id="e678f-124">N/A</span></span> |  <span data-ttu-id="e678f-125">N/A</span><span class="sxs-lookup"><span data-stu-id="e678f-125">N/A</span></span> |  <span data-ttu-id="e678f-126">2048x1152</span><span class="sxs-lookup"><span data-stu-id="e678f-126">2048x1152</span></span> |  <span data-ttu-id="e678f-127">67deg</span><span class="sxs-lookup"><span data-stu-id="e678f-127">67deg</span></span> |  <span data-ttu-id="e678f-128">最高的解析度靜止影像</span><span class="sxs-lookup"><span data-stu-id="e678f-128">Highest resolution still image</span></span> | 
  |  <span data-ttu-id="e678f-129">1408x792</span><span class="sxs-lookup"><span data-stu-id="e678f-129">1408x792</span></span> |  <span data-ttu-id="e678f-130">1408x792</span><span class="sxs-lookup"><span data-stu-id="e678f-130">1408x792</span></span> |  <span data-ttu-id="e678f-131">1408x792</span><span class="sxs-lookup"><span data-stu-id="e678f-131">1408x792</span></span> |  <span data-ttu-id="e678f-132">48deg</span><span class="sxs-lookup"><span data-stu-id="e678f-132">48deg</span></span> |  <span data-ttu-id="e678f-133">溢出掃描 （填補） 解析度視訊穩定功能之前</span><span class="sxs-lookup"><span data-stu-id="e678f-133">Overscan (padding) resolution before video stabilization</span></span> | 
  |  <span data-ttu-id="e678f-134">1344x756</span><span class="sxs-lookup"><span data-stu-id="e678f-134">1344x756</span></span> |  <span data-ttu-id="e678f-135">1344x756</span><span class="sxs-lookup"><span data-stu-id="e678f-135">1344x756</span></span> |  <span data-ttu-id="e678f-136">1344x756</span><span class="sxs-lookup"><span data-stu-id="e678f-136">1344x756</span></span> |  <span data-ttu-id="e678f-137">67deg</span><span class="sxs-lookup"><span data-stu-id="e678f-137">67deg</span></span> |  <span data-ttu-id="e678f-138">使用溢出掃描大型 FOV 視訊模式</span><span class="sxs-lookup"><span data-stu-id="e678f-138">Large FOV video mode with overscan</span></span> | 
  |  <span data-ttu-id="e678f-139">896x504</span><span class="sxs-lookup"><span data-stu-id="e678f-139">896x504</span></span> |  <span data-ttu-id="e678f-140">896x504</span><span class="sxs-lookup"><span data-stu-id="e678f-140">896x504</span></span> |  <span data-ttu-id="e678f-141">896x504</span><span class="sxs-lookup"><span data-stu-id="e678f-141">896x504</span></span> |  <span data-ttu-id="e678f-142">48deg</span><span class="sxs-lookup"><span data-stu-id="e678f-142">48deg</span></span> |  <span data-ttu-id="e678f-143">低電源 / 映像的低解析度模式處理工作</span><span class="sxs-lookup"><span data-stu-id="e678f-143">Low power / Low resolution mode for image processing tasks</span></span> | 

### <a name="hololens-2"></a><span data-ttu-id="e678f-144">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e678f-144">HoloLens 2</span></span>

* <span data-ttu-id="e678f-145">自動焦點相片/影片 (PV) 相機白色自動平衡、 自動曝光，與完整的映像處理管線。</span><span class="sxs-lookup"><span data-stu-id="e678f-145">Auto-focus photo/video (PV) camera with auto white balance, auto exposure, and full image processing pipeline.</span></span>
* <span data-ttu-id="e678f-146">觀景窗作用中時，會位於面向世界的白色隱私權 LED。</span><span class="sxs-lookup"><span data-stu-id="e678f-146">White Privacy LED facing the world will illuminate whenever the camera is active.</span></span>
* <span data-ttu-id="e678f-147">HoloLens 2 支援不同的相機設定檔。</span><span class="sxs-lookup"><span data-stu-id="e678f-147">HoloLens 2 supports different camera profiles.</span></span> <span data-ttu-id="e678f-148">了解如何[探索並選取相機功能](https://docs.microsoft.com/en-us/windows/uwp/audio-video-camera/camera-profiles)。</span><span class="sxs-lookup"><span data-stu-id="e678f-148">Learn how to [discover and select camera capabilities](https://docs.microsoft.com/en-us/windows/uwp/audio-video-camera/camera-profiles).</span></span>
* <span data-ttu-id="e678f-149">相機支援下列設定檔和 （所有的視訊模式是 16:9 外觀比例） 的解決方法：</span><span class="sxs-lookup"><span data-stu-id="e678f-149">The camera supports the following profiles and resolutions (all video modes are 16:9 aspect ratio):</span></span>
  
  | <span data-ttu-id="e678f-150">設定檔</span><span class="sxs-lookup"><span data-stu-id="e678f-150">Profile</span></span>                                         | <span data-ttu-id="e678f-151">視訊</span><span class="sxs-lookup"><span data-stu-id="e678f-151">Video</span></span>     | <span data-ttu-id="e678f-152">預覽</span><span class="sxs-lookup"><span data-stu-id="e678f-152">Preview</span></span>   | <span data-ttu-id="e678f-153">仍</span><span class="sxs-lookup"><span data-stu-id="e678f-153">Still</span></span>     | <span data-ttu-id="e678f-154">畫面播放速率</span><span class="sxs-lookup"><span data-stu-id="e678f-154">Frame rates</span></span> | <span data-ttu-id="e678f-155">水平視野 (H FOV)</span><span class="sxs-lookup"><span data-stu-id="e678f-155">Horizontal Field of View (H-FOV)</span></span> | <span data-ttu-id="e678f-156">建議的用法</span><span class="sxs-lookup"><span data-stu-id="e678f-156">Suggested usage</span></span>                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | <span data-ttu-id="e678f-157">Legacy,0  BalancedVideoAndPhoto,100</span><span class="sxs-lookup"><span data-stu-id="e678f-157">Legacy,0  BalancedVideoAndPhoto,100</span></span>             | <span data-ttu-id="e678f-158">2272x1278</span><span class="sxs-lookup"><span data-stu-id="e678f-158">2272x1278</span></span> | <span data-ttu-id="e678f-159">2272x1278</span><span class="sxs-lookup"><span data-stu-id="e678f-159">2272x1278</span></span> |           | <span data-ttu-id="e678f-160">15,30</span><span class="sxs-lookup"><span data-stu-id="e678f-160">15,30</span></span>       | <span data-ttu-id="e678f-161">64.69</span><span class="sxs-lookup"><span data-stu-id="e678f-161">64.69</span></span>                            | <span data-ttu-id="e678f-162">高品質的視訊錄製</span><span class="sxs-lookup"><span data-stu-id="e678f-162">High quality video recording</span></span>                |
  | <span data-ttu-id="e678f-163">Legacy,0  BalancedVideoAndPhoto,100</span><span class="sxs-lookup"><span data-stu-id="e678f-163">Legacy,0  BalancedVideoAndPhoto,100</span></span>             |           |           | <span data-ttu-id="e678f-164">3904x2196</span><span class="sxs-lookup"><span data-stu-id="e678f-164">3904x2196</span></span> |             | <span data-ttu-id="e678f-165">64.69</span><span class="sxs-lookup"><span data-stu-id="e678f-165">64.69</span></span>                            | <span data-ttu-id="e678f-166">高品質拍攝相片</span><span class="sxs-lookup"><span data-stu-id="e678f-166">High quality photo capture</span></span>                  |
  | <span data-ttu-id="e678f-167">BalancedVideoAndPhoto,120</span><span class="sxs-lookup"><span data-stu-id="e678f-167">BalancedVideoAndPhoto,120</span></span>                       | <span data-ttu-id="e678f-168">1952x1100</span><span class="sxs-lookup"><span data-stu-id="e678f-168">1952x1100</span></span> | <span data-ttu-id="e678f-169">1952x1100</span><span class="sxs-lookup"><span data-stu-id="e678f-169">1952x1100</span></span> | <span data-ttu-id="e678f-170">1952x1100</span><span class="sxs-lookup"><span data-stu-id="e678f-170">1952x1100</span></span> | <span data-ttu-id="e678f-171">15,30</span><span class="sxs-lookup"><span data-stu-id="e678f-171">15,30</span></span>       | <span data-ttu-id="e678f-172">64.69</span><span class="sxs-lookup"><span data-stu-id="e678f-172">64.69</span></span>                            | <span data-ttu-id="e678f-173">持續時間較長的案例</span><span class="sxs-lookup"><span data-stu-id="e678f-173">Long duration scenarios</span></span>                     |
  | <span data-ttu-id="e678f-174">BalancedVideoAndPhoto,120</span><span class="sxs-lookup"><span data-stu-id="e678f-174">BalancedVideoAndPhoto,120</span></span>                       | <span data-ttu-id="e678f-175">1504x846</span><span class="sxs-lookup"><span data-stu-id="e678f-175">1504x846</span></span>  | <span data-ttu-id="e678f-176">1504x846</span><span class="sxs-lookup"><span data-stu-id="e678f-176">1504x846</span></span>  |           | <span data-ttu-id="e678f-177">15,30</span><span class="sxs-lookup"><span data-stu-id="e678f-177">15,30</span></span>       | <span data-ttu-id="e678f-178">64.69</span><span class="sxs-lookup"><span data-stu-id="e678f-178">64.69</span></span>                            | <span data-ttu-id="e678f-179">持續時間較長的案例</span><span class="sxs-lookup"><span data-stu-id="e678f-179">Long duration scenarios</span></span>                     |
  | <span data-ttu-id="e678f-180">視訊會議 100</span><span class="sxs-lookup"><span data-stu-id="e678f-180">VideoConferencing,100</span></span>                           | <span data-ttu-id="e678f-181">1952x1100</span><span class="sxs-lookup"><span data-stu-id="e678f-181">1952x1100</span></span> | <span data-ttu-id="e678f-182">1952x1100</span><span class="sxs-lookup"><span data-stu-id="e678f-182">1952x1100</span></span> | <span data-ttu-id="e678f-183">1952x1100</span><span class="sxs-lookup"><span data-stu-id="e678f-183">1952x1100</span></span> | <span data-ttu-id="e678f-184">15,30,60</span><span class="sxs-lookup"><span data-stu-id="e678f-184">15,30,60</span></span>    | <span data-ttu-id="e678f-185">64.69</span><span class="sxs-lookup"><span data-stu-id="e678f-185">64.69</span></span>                            | <span data-ttu-id="e678f-186">視訊會議，持續時間較長的案例</span><span class="sxs-lookup"><span data-stu-id="e678f-186">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="e678f-187">視訊會議 100</span><span class="sxs-lookup"><span data-stu-id="e678f-187">Videoconferencing,100</span></span>                           | <span data-ttu-id="e678f-188">1504x846</span><span class="sxs-lookup"><span data-stu-id="e678f-188">1504x846</span></span>  | <span data-ttu-id="e678f-189">1504x846</span><span class="sxs-lookup"><span data-stu-id="e678f-189">1504x846</span></span>  |           | <span data-ttu-id="e678f-190">5,15,30,60</span><span class="sxs-lookup"><span data-stu-id="e678f-190">5,15,30,60</span></span>  | <span data-ttu-id="e678f-191">64.69</span><span class="sxs-lookup"><span data-stu-id="e678f-191">64.69</span></span>                            | <span data-ttu-id="e678f-192">視訊會議，持續時間較長的案例</span><span class="sxs-lookup"><span data-stu-id="e678f-192">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="e678f-193">視訊會議，100 BalancedVideoAndPhoto 120</span><span class="sxs-lookup"><span data-stu-id="e678f-193">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="e678f-194">1920x1080</span><span class="sxs-lookup"><span data-stu-id="e678f-194">1920x1080</span></span> | <span data-ttu-id="e678f-195">1920x1080</span><span class="sxs-lookup"><span data-stu-id="e678f-195">1920x1080</span></span> | <span data-ttu-id="e678f-196">1920x1080</span><span class="sxs-lookup"><span data-stu-id="e678f-196">1920x1080</span></span> | <span data-ttu-id="e678f-197">15,30</span><span class="sxs-lookup"><span data-stu-id="e678f-197">15,30</span></span>       | <span data-ttu-id="e678f-198">64.69</span><span class="sxs-lookup"><span data-stu-id="e678f-198">64.69</span></span>                            | <span data-ttu-id="e678f-199">視訊會議，持續時間較長的案例</span><span class="sxs-lookup"><span data-stu-id="e678f-199">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="e678f-200">視訊會議，100 BalancedVideoAndPhoto 120</span><span class="sxs-lookup"><span data-stu-id="e678f-200">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="e678f-201">1280x720</span><span class="sxs-lookup"><span data-stu-id="e678f-201">1280x720</span></span>  | <span data-ttu-id="e678f-202">1280x720</span><span class="sxs-lookup"><span data-stu-id="e678f-202">1280x720</span></span>  | <span data-ttu-id="e678f-203">1280x720</span><span class="sxs-lookup"><span data-stu-id="e678f-203">1280x720</span></span>  | <span data-ttu-id="e678f-204">15,30</span><span class="sxs-lookup"><span data-stu-id="e678f-204">15,30</span></span>       | <span data-ttu-id="e678f-205">64.69</span><span class="sxs-lookup"><span data-stu-id="e678f-205">64.69</span></span>                            | <span data-ttu-id="e678f-206">視訊會議，持續時間較長的案例</span><span class="sxs-lookup"><span data-stu-id="e678f-206">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="e678f-207">視訊會議，100 BalancedVideoAndPhoto 120</span><span class="sxs-lookup"><span data-stu-id="e678f-207">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="e678f-208">1128x635</span><span class="sxs-lookup"><span data-stu-id="e678f-208">1128x635</span></span>  |           |           | <span data-ttu-id="e678f-209">15,30</span><span class="sxs-lookup"><span data-stu-id="e678f-209">15,30</span></span>       | <span data-ttu-id="e678f-210">64.69</span><span class="sxs-lookup"><span data-stu-id="e678f-210">64.69</span></span>                            | <span data-ttu-id="e678f-211">視訊會議，持續時間較長的案例</span><span class="sxs-lookup"><span data-stu-id="e678f-211">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="e678f-212">視訊會議，100 BalancedVideoAndPhoto 120</span><span class="sxs-lookup"><span data-stu-id="e678f-212">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="e678f-213">960x540</span><span class="sxs-lookup"><span data-stu-id="e678f-213">960x540</span></span>   |           |           | <span data-ttu-id="e678f-214">15,30</span><span class="sxs-lookup"><span data-stu-id="e678f-214">15,30</span></span>       | <span data-ttu-id="e678f-215">64.69</span><span class="sxs-lookup"><span data-stu-id="e678f-215">64.69</span></span>                            | <span data-ttu-id="e678f-216">視訊會議，持續時間較長的案例</span><span class="sxs-lookup"><span data-stu-id="e678f-216">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="e678f-217">視訊會議，100 BalancedVideoAndPhoto 120</span><span class="sxs-lookup"><span data-stu-id="e678f-217">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="e678f-218">760x428</span><span class="sxs-lookup"><span data-stu-id="e678f-218">760x428</span></span>   |           |           | <span data-ttu-id="e678f-219">15,30</span><span class="sxs-lookup"><span data-stu-id="e678f-219">15,30</span></span>       | <span data-ttu-id="e678f-220">64.69</span><span class="sxs-lookup"><span data-stu-id="e678f-220">64.69</span></span>                            | <span data-ttu-id="e678f-221">視訊會議，持續時間較長的案例</span><span class="sxs-lookup"><span data-stu-id="e678f-221">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="e678f-222">視訊會議，100 BalancedVideoAndPhoto 120</span><span class="sxs-lookup"><span data-stu-id="e678f-222">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="e678f-223">640x360</span><span class="sxs-lookup"><span data-stu-id="e678f-223">640x360</span></span>   |           |           | <span data-ttu-id="e678f-224">15,30</span><span class="sxs-lookup"><span data-stu-id="e678f-224">15,30</span></span>       | <span data-ttu-id="e678f-225">64.69</span><span class="sxs-lookup"><span data-stu-id="e678f-225">64.69</span></span>                            | <span data-ttu-id="e678f-226">視訊會議，持續時間較長的案例</span><span class="sxs-lookup"><span data-stu-id="e678f-226">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="e678f-227">視訊會議，100 BalancedVideoAndPhoto 120</span><span class="sxs-lookup"><span data-stu-id="e678f-227">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="e678f-228">500x282</span><span class="sxs-lookup"><span data-stu-id="e678f-228">500x282</span></span>   |           |           | <span data-ttu-id="e678f-229">15,30</span><span class="sxs-lookup"><span data-stu-id="e678f-229">15,30</span></span>       | <span data-ttu-id="e678f-230">64.69</span><span class="sxs-lookup"><span data-stu-id="e678f-230">64.69</span></span>                            | <span data-ttu-id="e678f-231">視訊會議，持續時間較長的案例</span><span class="sxs-lookup"><span data-stu-id="e678f-231">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="e678f-232">視訊會議，100 BalancedVideoAndPhoto 120</span><span class="sxs-lookup"><span data-stu-id="e678f-232">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="e678f-233">424x240</span><span class="sxs-lookup"><span data-stu-id="e678f-233">424x240</span></span>   |           |           | <span data-ttu-id="e678f-234">15,30</span><span class="sxs-lookup"><span data-stu-id="e678f-234">15,30</span></span>       | <span data-ttu-id="e678f-235">64.69</span><span class="sxs-lookup"><span data-stu-id="e678f-235">64.69</span></span>                            | <span data-ttu-id="e678f-236">視訊會議，持續時間較長的案例</span><span class="sxs-lookup"><span data-stu-id="e678f-236">Video conferencing, long duration scenarios</span></span> |

>[!NOTE]
><span data-ttu-id="e678f-237">客戶可以利用[混合實境擷取](mixed-reality-capture.md)拍攝影片或應用程式，包括全像投影和視訊穩定的相片。</span><span class="sxs-lookup"><span data-stu-id="e678f-237">Customers can leverage [mixed reality capture](mixed-reality-capture.md) to take videos or photos of your app, which include holograms and video stabilization.</span></span>
>
><span data-ttu-id="e678f-238">身為開發人員，有一些您應該考慮建立您的應用程式，如果您想要客戶擷取內容時的外觀可能不如時的考量。</span><span class="sxs-lookup"><span data-stu-id="e678f-238">As a developer, there are considerations you should take into account when creating your app if you want it to look as good as possible when a customer captures content.</span></span> <span data-ttu-id="e678f-239">您可以也啟用 （和自訂） 直接在您的應用程式內的混合的實境擷取。</span><span class="sxs-lookup"><span data-stu-id="e678f-239">You can also enable (and customize) mixed reality capture from directly within your app.</span></span> <span data-ttu-id="e678f-240">深入了解[開發人員的混合實境擷取](mixed-reality-capture-for-developers.md)。</span><span class="sxs-lookup"><span data-stu-id="e678f-240">Learn more at [mixed reality capture for developers](mixed-reality-capture-for-developers.md).</span></span>

## <a name="locating-the-device-camera-in-the-world"></a><span data-ttu-id="e678f-241">尋找裝置相機在全局</span><span class="sxs-lookup"><span data-stu-id="e678f-241">Locating the Device Camera in the World</span></span>

<span data-ttu-id="e678f-242">當 HoloLens 將相片和視訊時，擷取的畫面格會包含世界裡，以及將觀景窗的遠近景深投射觀景窗的位置。</span><span class="sxs-lookup"><span data-stu-id="e678f-242">When HoloLens takes photos and videos, the captured frames include the location of the camera in the world, as well as the perspective projection of the camera.</span></span> <span data-ttu-id="e678f-243">如此應用程式的原因需觀景窗的位置，在真實世界的增強型映像的案例。</span><span class="sxs-lookup"><span data-stu-id="e678f-243">This allows applications to reason about the position of the camera in the real world for augmented imaging scenarios.</span></span> <span data-ttu-id="e678f-244">開發人員更多時間可以復原自己的案例使用其慣用的映像處理或自訂電腦視覺文件庫。</span><span class="sxs-lookup"><span data-stu-id="e678f-244">Developers can creatively roll their own scenarios using their favorite image processing or custom computer vision libraries.</span></span>

<span data-ttu-id="e678f-245">「 虛擬遊戲觀景窗 」 （位在範圍的應用程式呈現給） 可能參考 「 攝影機 」 HoloLens 文件中的其他位置。</span><span class="sxs-lookup"><span data-stu-id="e678f-245">"Camera" elsewhere in HoloLens documentation may refer to the "virtual game camera" (the frustum the app renders to).</span></span> <span data-ttu-id="e678f-246">否則表示，除非此頁面上的"相機 」 指的是實際 RGB 色彩相機。</span><span class="sxs-lookup"><span data-stu-id="e678f-246">Unless denoted otherwise, "camera" on this page refers to the real-world RGB color camera.</span></span>

<span data-ttu-id="e678f-247">在此頁面的外殼的詳細資料[Media Foundation 屬性](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx)，不過也有提取相機內建函式使用的 Api [WinRT Api](https://msdn.microsoft.com/library/windows/apps/windows.media.devices.core.cameraintrinsics)。</span><span class="sxs-lookup"><span data-stu-id="e678f-247">The details on this page cover [Media Foundation Attributes](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx), however there are also APIs to pull camera intrinsics using [WinRT APIs](https://msdn.microsoft.com/library/windows/apps/windows.media.devices.core.cameraintrinsics).</span></span>  

### <a name="images-with-coordinate-systems"></a><span data-ttu-id="e678f-248">與座標系統的映像</span><span class="sxs-lookup"><span data-stu-id="e678f-248">Images with Coordinate Systems</span></span>

<span data-ttu-id="e678f-249">每個影像框架 (是否相片或視訊) 包含座標系統，以及兩個重要的轉換。</span><span class="sxs-lookup"><span data-stu-id="e678f-249">Each image frame (whether photo or video) includes a coordinate system, as well as two important transforms.</span></span> <span data-ttu-id="e678f-250">「 檢視 」 轉換從數位相機，以提供的座標系統的對應和相機中的 「 投射 」 對應至映像中的像素。</span><span class="sxs-lookup"><span data-stu-id="e678f-250">The "view" transform maps from the provided coordinate system to the camera, and the "projection" maps from the camera to pixels in the image.</span></span> <span data-ttu-id="e678f-251">在一起，這些轉換定義每個像素無限遠的光線表示所產生的像素 photons 採取的路徑的 3D 空間中。</span><span class="sxs-lookup"><span data-stu-id="e678f-251">Together, these transforms define for each pixel a ray in 3D space representing the path taken by the photons that produced the pixel.</span></span> <span data-ttu-id="e678f-252">這些光線可以藉由從畫面格的座標系統中取得轉換至其他的座標系統相關的應用程式中的其他內容 (例如從[靜態參考座標系](coordinate-systems.md#stationary-frame-of-reference))。</span><span class="sxs-lookup"><span data-stu-id="e678f-252">These rays can be related to other content in the app by obtaining the transform from the frame's coordinate system to some other coordinate system (e.g. from a [stationary frame of reference](coordinate-systems.md#stationary-frame-of-reference)).</span></span> <span data-ttu-id="e678f-253">總結來說，每個影像框架提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="e678f-253">To summarize, each image frame provides the following:</span></span>
* <span data-ttu-id="e678f-254">像素格式的資料 （RGB/NV12 JPEG/等等）</span><span class="sxs-lookup"><span data-stu-id="e678f-254">Pixel Data (in RGB/NV12/JPEG/etc. format)</span></span>
* <span data-ttu-id="e678f-255">中繼資料的 3 個片段 (儲存為[IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx))，讓每個畫面格 」 之外的可尋獲 」:</span><span class="sxs-lookup"><span data-stu-id="e678f-255">3 pieces of metadata (stored as [IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx)) that make each frame "locatable":</span></span>

|  <span data-ttu-id="e678f-256">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="e678f-256">Attribute name</span></span>  |  <span data-ttu-id="e678f-257">類型</span><span class="sxs-lookup"><span data-stu-id="e678f-257">Type</span></span>  |  <span data-ttu-id="e678f-258">GUID</span><span class="sxs-lookup"><span data-stu-id="e678f-258">GUID</span></span>  |  <span data-ttu-id="e678f-259">描述</span><span class="sxs-lookup"><span data-stu-id="e678f-259">Description</span></span> | 
|----------|----------|----------|----------|
|  <span data-ttu-id="e678f-260">MFSampleExtension_Spatial_CameraCoordinateSystem</span><span class="sxs-lookup"><span data-stu-id="e678f-260">MFSampleExtension_Spatial_CameraCoordinateSystem</span></span>  |  <span data-ttu-id="e678f-261">IUnknown ([SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx))</span><span class="sxs-lookup"><span data-stu-id="e678f-261">IUnknown ([SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx))</span></span>  |  <span data-ttu-id="e678f-262">{9D13C82F-2199-4E67-91CD-D1A4181F2534}</span><span class="sxs-lookup"><span data-stu-id="e678f-262">{9D13C82F-2199-4E67-91CD-D1A4181F2534}</span></span>  |  <span data-ttu-id="e678f-263">存放區[座標系統](coordinate-systems-in-directx.md)的擷取的畫面格</span><span class="sxs-lookup"><span data-stu-id="e678f-263">Stores the [coordinate system](coordinate-systems-in-directx.md) of the captured frame</span></span> | 
|  <span data-ttu-id="e678f-264">MFSampleExtension_Spatial_CameraViewTransform</span><span class="sxs-lookup"><span data-stu-id="e678f-264">MFSampleExtension_Spatial_CameraViewTransform</span></span>  |  <span data-ttu-id="e678f-265">Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))</span><span class="sxs-lookup"><span data-stu-id="e678f-265">Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))</span></span>  |  <span data-ttu-id="e678f-266">{4E251FA4-830F-4770-859A-4B8D99AA809B}</span><span class="sxs-lookup"><span data-stu-id="e678f-266">{4E251FA4-830F-4770-859A-4B8D99AA809B}</span></span>  |  <span data-ttu-id="e678f-267">將相機的外建轉換存放在座標系統</span><span class="sxs-lookup"><span data-stu-id="e678f-267">Stores the camera's extrinsic transform in the coordinate system</span></span> | 
|  <span data-ttu-id="e678f-268">MFSampleExtension_Spatial_CameraProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="e678f-268">MFSampleExtension_Spatial_CameraProjectionTransform</span></span>  |  <span data-ttu-id="e678f-269">Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))</span><span class="sxs-lookup"><span data-stu-id="e678f-269">Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))</span></span>  |  <span data-ttu-id="e678f-270">{47F9FCB5-2A02-4F26-A477-792FDF95886A}</span><span class="sxs-lookup"><span data-stu-id="e678f-270">{47F9FCB5-2A02-4F26-A477-792FDF95886A}</span></span>  |  <span data-ttu-id="e678f-271">將相機的投影轉換</span><span class="sxs-lookup"><span data-stu-id="e678f-271">Stores the camera's projection transform</span></span> | 

<span data-ttu-id="e678f-272">投影轉換表示對應到從-1 延伸至 + 1 X 和 Y 軸中的映像平面 功能濾鏡的內建屬性 （焦距，投射的中心扭曲）。</span><span class="sxs-lookup"><span data-stu-id="e678f-272">The projection transform represents the intrinsic properties (focal length, center of projection, skew) of the lens mapped onto an image plane that extends from -1 to +1 in both the X and Y axis.</span></span>

```
Matrix4x4 format          Terms
   m11 m12 m13 m14      fx    0   0   0
   m21 m22 m23 m24     skew  fy   0   0
   m31 m32 m33 m34      cx   cy   A  -1
   m41 m42 m43 m44       0    0   B   0
```

<span data-ttu-id="e678f-273">不同的應用程式會有不同的座標系統。</span><span class="sxs-lookup"><span data-stu-id="e678f-273">Different applications will have different coordinate systems.</span></span> <span data-ttu-id="e678f-274">以下是流程的要找出相機像素的單一應用程式概觀：</span><span class="sxs-lookup"><span data-stu-id="e678f-274">Here's an overview of the flow to locate a camera pixel for a single application:</span></span>

![轉換套用到數位相機座標系統](images/pvcameratransform5-500px.png)

### <a name="camera-to-application-specified-coordinate-system"></a><span data-ttu-id="e678f-276">應用程式指定的座標系統的相機</span><span class="sxs-lookup"><span data-stu-id="e678f-276">Camera to Application-specified Coordinate System</span></span>

<span data-ttu-id="e678f-277">若要從 'CameraView' 和 'CameraCoordinateSystem' 前往您的應用程式/全局座標系統，您將需要下列項目：</span><span class="sxs-lookup"><span data-stu-id="e678f-277">To go from the 'CameraView' and 'CameraCoordinateSystem' to your application/world coordinate system, you'll need the following:</span></span>

<span data-ttu-id="e678f-278">[在 Unity 中的可以找到相機](locatable-camera-in-unity.md):CameraToWorldMatrix 自動 PhotoCaptureFrame 類別提供 （因此您不需要擔心 CameraCoordinateSystem 轉換）。</span><span class="sxs-lookup"><span data-stu-id="e678f-278">[Locatable camera in Unity](locatable-camera-in-unity.md): CameraToWorldMatrix is automatically provided by PhotoCaptureFrame class(so you don't need to worry about the CameraCoordinateSystem transforms).</span></span>

<span data-ttu-id="e678f-279">[DirectX 之外的可尋獲觀景窗](locatable-camera-in-directx.md):顯示相機的座標系統與您自己的應用程式 coordinate system(s) 之間轉換的查詢相當簡單的方式。</span><span class="sxs-lookup"><span data-stu-id="e678f-279">[Locatable camera in DirectX](locatable-camera-in-directx.md): Shows the fairly straightforward way to query for the transform between the camera's coordinate system and your own application coordinate system(s).</span></span>

### <a name="application-specified-coordinate-system-to-pixel-coordinates"></a><span data-ttu-id="e678f-280">應用程式指定座標系統，以像素座標</span><span class="sxs-lookup"><span data-stu-id="e678f-280">Application-specified Coordinate System to Pixel Coordinates</span></span>

<span data-ttu-id="e678f-281">例如，假設您想要尋找] 或 [繪製在指定的 3d 位置上的相機映像：</span><span class="sxs-lookup"><span data-stu-id="e678f-281">Let's say you wanted to find or draw at a specific 3d location on a camera image:</span></span>

<span data-ttu-id="e678f-282">檢視和投影轉換，這兩個的 4x4 矩陣時需要使用方式稍有不同。</span><span class="sxs-lookup"><span data-stu-id="e678f-282">The view and projection transforms, while both 4x4 matrices, need to be utilized slightly differently.</span></span> <span data-ttu-id="e678f-283">也就是之後執行投影，其中會 「 正規化的 w 」，這個額外的步驟，在投射中模擬如何將多個不同的 3d 位置的最後可能會做為相同的 2d 位置 （也就是沿著某些光線的任何項目會顯示在相同的像素） 在螢幕上。</span><span class="sxs-lookup"><span data-stu-id="e678f-283">Namely after performing the Projection, one would 'normalize by w', this extra step in the projection simulates how multiple different 3d locations can end up as the same 2d location on a screen (i.e. anything along a certain ray will show up on the same pixel).</span></span> <span data-ttu-id="e678f-284">因此重點 （在著色器程式碼）：</span><span class="sxs-lookup"><span data-stu-id="e678f-284">So key points (in shader code):</span></span>

```
// Usual 3d math:
 float4x4 WorldToCamera = inverse( CameraToWorld );
 float4 CameraSpacePos = mul( WorldToCamera, float4( WorldSpacePos.xyz, 1 ) ); // use 1 as the W component
 // Projection math:
 float4 ImagePosUnnormalized = mul( CameraProjection, float4( CameraSpacePos.xyz, 1 ) ); // use 1 as the W component
 float2 ImagePosProjected = ImagePosUnnormalized.xy / ImagePosUnnormalized.w; // normalize by W, gives -1 to 1 space
 float2 ImagePosZeroToOne = ( ImagePosProjected * 0.5 ) + float2( 0.5, 0.5 ); // good for GPU textures
 int2 PixelPos = int2( ImagePosZeroToOne.x * ImageWidth, ( 1 - ImagePosZeroToOne.y ) * ImageHeight ); // good for CPU textures
```

### <a name="pixel-to-application-specified-coordinate-system"></a><span data-ttu-id="e678f-285">應用程式指定的座標系統的像素</span><span class="sxs-lookup"><span data-stu-id="e678f-285">Pixel to Application-specified Coordinate System</span></span>

<span data-ttu-id="e678f-286">要全局座標從像素就比較困難：</span><span class="sxs-lookup"><span data-stu-id="e678f-286">Going from pixel to world coordinates is a little trickier:</span></span>

```
float2 ImagePosZeroToOne = float2( PixelPos.x / ImageWidth, 1.0 - (PixelPos.y / ImageHeight ) );
 float2 ImagePosProjected = ( ( ImagePosZeroToOne * 2.0 ) - float2(1,1) ); // -1 to 1 space
 float3 CameraSpacePos = UnProjectVector( Projection, float3( ImagePosProjected, 1) );
 float3 WorldSpaceRayPoint1 = mul( CameraToWorld, float4(0,0,0,1) ); // camera location in world space
 float3 WorldSpaceRayPoint2 = mul( CameraToWorld, CameraSpacePos ); // ray point in world space
```

<span data-ttu-id="e678f-287">我們在其中定義為 UnProject:</span><span class="sxs-lookup"><span data-stu-id="e678f-287">Where we define UnProject as:</span></span>

```
public static Vector3 UnProjectVector(Matrix4x4 proj, Vector3 to)
 {
   Vector3 from = new Vector3(0, 0, 0);
   var axsX = proj.GetRow(0);
   var axsY = proj.GetRow(1);
   var axsZ = proj.GetRow(2);
   from.z = to.z / axsZ.z;
   from.y = (to.y - (from.z * axsY.z)) / axsY.y;
   from.x = (to.x - (from.z * axsX.z)) / axsX.x;
   return from;
 }
```

<span data-ttu-id="e678f-288">若要尋找某個點的實際世界位置，您將需要： 兩個世界光線並尋找其交集，或是已知的點的大小。</span><span class="sxs-lookup"><span data-stu-id="e678f-288">To find the actual world location of a point, you'll need either: two world rays and find their intersection, or a known size of the points.</span></span>

### <a name="distortion-error"></a><span data-ttu-id="e678f-289">扭曲錯誤</span><span class="sxs-lookup"><span data-stu-id="e678f-289">Distortion Error</span></span>

<span data-ttu-id="e678f-290">上 HoloLens、 影片和仍然影像資料流是 undistorted 系統的映像處理管線中之前的畫面格都會提供給應用程式 （預覽資料流包含原始的扭曲的框架）。</span><span class="sxs-lookup"><span data-stu-id="e678f-290">On HoloLens, the video and still image streams are undistorted in the system's image processing pipeline before the frames are made available to the application (the preview stream contains the original distorted frames).</span></span> <span data-ttu-id="e678f-291">投影矩陣可供使用，因為應用程式必須假設影像框架代表完美 pinhole 相機，不過 undistortion 函式中的映像處理器可能仍保留最多 10 個像素為單位的錯誤時使用投影矩陣中框架的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e678f-291">Because only the projection matrix is made available, applications must assume image frames represent a perfect pinhole camera, however the undistortion function in the image processor may still leave an error of up to 10 pixels when using the projection matrix in the frame metadata.</span></span> <span data-ttu-id="e678f-292">在許多使用案例，此錯誤就不重要，但如果您對齊全像投影至真實世界海報/標記，比方說，而且您會注意到 < 10px 位移 (大致上位於遠 2 公尺全像投影 11 mm) 此扭曲錯誤可能是原因。</span><span class="sxs-lookup"><span data-stu-id="e678f-292">In many use cases, this error will not matter, but if you are aligning holograms to real world posters/markers, for example, and you notice a <10px offset (roughly 11mm for holograms positioned 2 meters away) this distortion error could be the cause.</span></span>

## <a name="locatable-camera-usage-scenarios"></a><span data-ttu-id="e678f-293">之外的可尋獲相機使用方式案例</span><span class="sxs-lookup"><span data-stu-id="e678f-293">Locatable Camera Usage Scenarios</span></span>

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a><span data-ttu-id="e678f-294">顯示相片或視訊擷取世界</span><span class="sxs-lookup"><span data-stu-id="e678f-294">Show a photo or video in the world where it was captured</span></span>

<span data-ttu-id="e678f-295">裝置相機框架隨附的"相機來 World 」 轉換，可用來顯示完全裝置的擷取映像時。</span><span class="sxs-lookup"><span data-stu-id="e678f-295">The Device Camera frames come with a "Camera To World" transform, that can be used to show exactly where the device was when the image was taken.</span></span> <span data-ttu-id="e678f-296">比方說您無法放置小型全像攝影版圖示，此位置 （CameraToWorld.MultiplyPoint(Vector3.zero)) 和甚至是繪製方向，相機當時正面臨 (CameraToWorld.MultiplyVector(Vector3.forward)) 小箭號。</span><span class="sxs-lookup"><span data-stu-id="e678f-296">For example you could position a small holographic icon at this location (CameraToWorld.MultiplyPoint(Vector3.zero)) and even draw a little arrow in the direction that the camera was facing (CameraToWorld.MultiplyVector(Vector3.forward)).</span></span>

### <a name="painting-the-world-using-a-camera-shader"></a><span data-ttu-id="e678f-297">繪製世界使用相機著色器</span><span class="sxs-lookup"><span data-stu-id="e678f-297">Painting the world using a camera shader</span></span>

<span data-ttu-id="e678f-298">這一節我們將建立材料 '著色器' 世界為基礎，它顯示在裝置相機的檢視中的色彩。</span><span class="sxs-lookup"><span data-stu-id="e678f-298">In this section we'll create a material 'shader' that colors the world based on where it showed up in a device camera's view.</span></span> <span data-ttu-id="e678f-299">我們要有效地為每個頂點會找出其與數位相機，相對的位置，然後每個像素會利用投影矩陣圖放大哪一個映像相關聯的材質。</span><span class="sxs-lookup"><span data-stu-id="e678f-299">Effectively what we'll do is that every vertex will figure out its location relative to the camera, and then every pixel will utilize the 'projection matrix' to figure out which image texel it is associated with.</span></span> <span data-ttu-id="e678f-300">最後，並選擇性地，我們會淡出的映像，讓它顯示更多類似的夢想的記憶體：</span><span class="sxs-lookup"><span data-stu-id="e678f-300">Lastly, and optionally, we'll fade out the corners of the image to make it appear more as a dream-like memory:</span></span>

```
// In the vertex shader:
 float4 worldSpace = mul( ObjectToWorld, float4( vertexPos.xyz, 1));
 float4 cameraSpace = mul( CameraWorldToLocal, float4(worldSpace.xyz, 1));

 // In the pixel shader:
 float4 unprojectedTex = mul( CameraProjection, float4( cameraSpace .xyz, 1));
 float2 projectedTex = (unprojectedTex.xy / unprojectedTex.w);
 float2 unitTexcoord = ((projectedTex * 0.5) + float4(0.5, 0.5, 0, 0));
 float4 cameraTextureColor = tex2D(_CameraTex, unitTexcoord);
 // Fade out edges for better look:
 float pctInView = saturate((1.0 - length(projectedTex.xy)) * 3.0);
 float4 finalColor = float4( cameraTextureColor.rgb, pctInView );
```

### <a name="tag--pattern--poster--object-tracking"></a><span data-ttu-id="e678f-301">標記 / 模式 / 海報 / 物件追蹤</span><span class="sxs-lookup"><span data-stu-id="e678f-301">Tag / Pattern / Poster / Object Tracking</span></span>

<span data-ttu-id="e678f-302">許多混合的實境應用程式會使用可辨識的映像或視覺化模式在空間上建立可追蹤點。</span><span class="sxs-lookup"><span data-stu-id="e678f-302">Many mixed reality applications use a recognizable image or visual pattern to create a trackable point in space.</span></span> <span data-ttu-id="e678f-303">這再用來呈現物件的相對點，或建立一個已知的位置。</span><span class="sxs-lookup"><span data-stu-id="e678f-303">This is then used to render objects relative to that point or create a known location.</span></span> <span data-ttu-id="e678f-304">HoloLens 的部分用法包括的尋找真實世界物件加上 fiducials （例如有 QR 代碼的電視監視器）、 透過 fiducials，放置全像投影和視覺上已安裝程式，以透過 HoloLens 與通訊的平板電腦等的非 HoloLens 裝置配對Wi-fi。</span><span class="sxs-lookup"><span data-stu-id="e678f-304">Some uses for HoloLens include finding a real world object tagged with fiducials (e.g. a TV monitor with a QR code), placing holograms over fiducials, and visually pairing with non-HoloLens devices like tablets that have been setup to communicate with HoloLens via Wi-Fi.</span></span>

<span data-ttu-id="e678f-305">若要識別其視覺化的模式，並再將該物件放在應用程式世界空間，您將需要幾件事：</span><span class="sxs-lookup"><span data-stu-id="e678f-305">To recognize a visual pattern, and then place that object in the applications world space, you'll need a few things:</span></span>
1. <span data-ttu-id="e678f-306">映像模式辨識工具組，例如 QR 代碼、 AR 標記、 臉部 finder、 圓形追蹤器、 OCR 等等。</span><span class="sxs-lookup"><span data-stu-id="e678f-306">An image pattern recognition toolkit, such as QR code, AR tags, face finder, circle trackers, OCR etc.</span></span>
2. <span data-ttu-id="e678f-307">收集的影像框架，在執行階段，並將其傳遞至辨識層</span><span class="sxs-lookup"><span data-stu-id="e678f-307">Collect image frames at runtime, and pass them to the recognition layer</span></span>
3. <span data-ttu-id="e678f-308">Unproject 回世界位置或可能的世界光線其映像位置。</span><span class="sxs-lookup"><span data-stu-id="e678f-308">Unproject their image locations back into world positions, or likely world rays.</span></span> <span data-ttu-id="e678f-309">請參閱</span><span class="sxs-lookup"><span data-stu-id="e678f-309">See</span></span>
4. <span data-ttu-id="e678f-310">將您的虛擬模型放在這些全球位置</span><span class="sxs-lookup"><span data-stu-id="e678f-310">Position your virtual models over these world locations</span></span>

<span data-ttu-id="e678f-311">一些重要的映像處理的連結：</span><span class="sxs-lookup"><span data-stu-id="e678f-311">Some important image processing links:</span></span>
* [<span data-ttu-id="e678f-312">OpenCV</span><span class="sxs-lookup"><span data-stu-id="e678f-312">OpenCV</span></span>](http://opencv.org/)
* [<span data-ttu-id="e678f-313">QR 標記</span><span class="sxs-lookup"><span data-stu-id="e678f-313">QR Tags</span></span>](https://en.wikipedia.org/wiki/QR_code)
* [<span data-ttu-id="e678f-314">FaceSDK</span><span class="sxs-lookup"><span data-stu-id="e678f-314">FaceSDK</span></span>](http://research.microsoft.com/projects/facesdk/)
* [<span data-ttu-id="e678f-315">Microsoft Translator</span><span class="sxs-lookup"><span data-stu-id="e678f-315">Microsoft Translator</span></span>](https://www.microsoft.com/translator/business)

<span data-ttu-id="e678f-316">保留的互動式應用程式畫面播放速率很重要，特別是在處理長時間執行影像辨識演算法。</span><span class="sxs-lookup"><span data-stu-id="e678f-316">Keeping an interactive application frame-rate is critical, especially when dealing with long-running image recognition algorithms.</span></span> <span data-ttu-id="e678f-317">因此我們通常會使用下列模式：</span><span class="sxs-lookup"><span data-stu-id="e678f-317">For this reason we commonly use the following pattern:</span></span>
1. <span data-ttu-id="e678f-318">主執行緒： 管理相機物件</span><span class="sxs-lookup"><span data-stu-id="e678f-318">Main Thread: manages the camera object</span></span>
2. <span data-ttu-id="e678f-319">主執行緒： 要求新的框架 （非同步）</span><span class="sxs-lookup"><span data-stu-id="e678f-319">Main Thread: requests new frames (async)</span></span>
3. <span data-ttu-id="e678f-320">主執行緒： 將新的畫面格傳遞給追蹤的執行緒</span><span class="sxs-lookup"><span data-stu-id="e678f-320">Main Thread: pass new frames to tracking thread</span></span>
4. <span data-ttu-id="e678f-321">追蹤執行緒： 處理序映像，以收集關鍵點</span><span class="sxs-lookup"><span data-stu-id="e678f-321">Tracking Thread: processes image to collect key points</span></span>
5. <span data-ttu-id="e678f-322">主執行緒： 移動的虛擬模式，以符合找到的關鍵點</span><span class="sxs-lookup"><span data-stu-id="e678f-322">Main Thread: moves virtual model to match found key points</span></span>
6. <span data-ttu-id="e678f-323">重複步驟 2 中的主執行緒：</span><span class="sxs-lookup"><span data-stu-id="e678f-323">Main Thread: repeat from step 2</span></span>

<span data-ttu-id="e678f-324">有些映像標記系統僅提供單一像素的位置 (其他人提供完整的轉換在此情況下這一節將不需要)，這等同於無限遠的光線可能的位置。</span><span class="sxs-lookup"><span data-stu-id="e678f-324">Some image marker systems only provide a single pixel location (others provide the full transform in which case this section will not be needed), which equates to a ray of possible locations.</span></span> <span data-ttu-id="e678f-325">若要移至單一的 3d 位置我們可以利用多個光線並尋找其大約的交集的最終結果。</span><span class="sxs-lookup"><span data-stu-id="e678f-325">To get to a single 3d location we can then leverage multiple rays and find the final result by their approximate intersection.</span></span> <span data-ttu-id="e678f-326">若要這樣做您將需要：</span><span class="sxs-lookup"><span data-stu-id="e678f-326">To do this you'll need to:</span></span>
1. <span data-ttu-id="e678f-327">取得迴圈會收集多個相機的映像</span><span class="sxs-lookup"><span data-stu-id="e678f-327">Get a loop going collecting multiple camera images</span></span>
2. <span data-ttu-id="e678f-328">尋找[相關聯的功能點](#pixel-to-application-specified-coordinate-system)，和他們的世界光線</span><span class="sxs-lookup"><span data-stu-id="e678f-328">Find the [associated feature points](#pixel-to-application-specified-coordinate-system), and their world rays</span></span>
3. <span data-ttu-id="e678f-329">當您有的功能，每個都有多個世界的光線，字典時您可以使用下列程式碼來解決這些光線交集：</span><span class="sxs-lookup"><span data-stu-id="e678f-329">When you have a dictionary of features, each with multiple world rays, you can use the following code to solve for the intersection of those rays:</span></span>

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```

<span data-ttu-id="e678f-330">您可以指定兩個或多個追蹤的標記位置，來定位 modelled 的場景依據使用者目前的案例。</span><span class="sxs-lookup"><span data-stu-id="e678f-330">Given two or more tracked tag locations, you can position a modelled scene to fit the users current scenario.</span></span> <span data-ttu-id="e678f-331">如果您不能假設重力，您將需要三個標記位置。</span><span class="sxs-lookup"><span data-stu-id="e678f-331">If you can't assume gravity, then you'll need three tag locations.</span></span> <span data-ttu-id="e678f-332">在許多情況下，我們會使用簡單的色彩配置，其中的白色置放的球體表示即時追蹤標記的位置，藍色置放的球體代表模型化的標記的位置，這可讓使用者以視覺方式量測計的對齊方式的品質。</span><span class="sxs-lookup"><span data-stu-id="e678f-332">In many cases we use a simple color scheme where white spheres represent real-time tracked tag locations, and blue spheres represent modelled tag locations, this allows the user to visually gauge the alignment quality.</span></span> <span data-ttu-id="e678f-333">我們假設我們所有的應用程式中的下列設定：</span><span class="sxs-lookup"><span data-stu-id="e678f-333">We assume the following setup in all our applications:</span></span>
* <span data-ttu-id="e678f-334">兩個或多個模型化的標籤位置</span><span class="sxs-lookup"><span data-stu-id="e678f-334">Two or more modelled tag locations</span></span>
* <span data-ttu-id="e678f-335">其中一個 「 敃櫆空間 」，也在場景中就是父項的標記</span><span class="sxs-lookup"><span data-stu-id="e678f-335">One 'calibration space' which in the scene is the parent of the tags</span></span>
* <span data-ttu-id="e678f-336">相機功能識別項</span><span class="sxs-lookup"><span data-stu-id="e678f-336">Camera feature identifier</span></span>
* <span data-ttu-id="e678f-337">移動對齊 （很謹慎地移動父空間，而不 modelled 標記本身，因為其他 connect 是相對於它們的位置） 的即時標記 modelled 的標記的校正空間的行為。</span><span class="sxs-lookup"><span data-stu-id="e678f-337">Behavior which moves the calibration space to align the modelled tags with the real-time tags (we are careful to move the parent space, not the modelled markers themselves, because other connect is positions relative to them).</span></span>

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="render-holograms-from-the-cameras-position"></a><span data-ttu-id="e678f-338">呈現全像投影從相機的位置</span><span class="sxs-lookup"><span data-stu-id="e678f-338">Render holograms from the Camera's position</span></span>

<span data-ttu-id="e678f-339">注意:如果您嘗試建立您自己[混合實境擷取 (MRC)](mixed-reality-capture.md)，其中混合使用相機的資料流全像投影，您可以使用[MRC 效果](mixed-reality-capture-for-developers.md)] 或 [啟用中的 showHolograms 屬性[在 Unity 中的可以找到相機](locatable-camera-in-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="e678f-339">Note: If you are trying to create your own [Mixed reality capture (MRC)](mixed-reality-capture.md), which blends holograms with the Camera stream, you can use the [MRC effects](mixed-reality-capture-for-developers.md) or enable the showHolograms property in [Locatable camera in Unity](locatable-camera-in-unity.md).</span></span>

<span data-ttu-id="e678f-340">如果您想要直接在 RGB 相機串流上的特殊轉譯，就可以呈現全像投影觀景窗的位置從空間中的視訊摘要與同步，以提供自訂的全像錄製/即時預覽。</span><span class="sxs-lookup"><span data-stu-id="e678f-340">If you'd like to do a special render directly on the RGB Camera stream, it's possible to render holograms in space from the Camera's position in sync with a video feed in order to provide a custom hologram recording/live preview.</span></span>

<span data-ttu-id="e678f-341">Skype，目的是要顯示遠端用戶端 HoloLens 使用者所查看的內容，並允許它們與相同全像投影互動。</span><span class="sxs-lookup"><span data-stu-id="e678f-341">In Skype, we do this to show the remote client what the HoloLens user is seeing and allow them to interact with the same holograms.</span></span> <span data-ttu-id="e678f-342">在傳送之前透過 Skype 服務每個視訊的範圍內，我們抓取每個畫面格的相對應的相機資料。</span><span class="sxs-lookup"><span data-stu-id="e678f-342">Before sending over each video frame through the Skype service, we grab each frame's corresponding camera data.</span></span> <span data-ttu-id="e678f-343">我們接著，封裝使用視訊畫面格相機的外建和內建函式中繼資料，然後透過 Skype 服務。</span><span class="sxs-lookup"><span data-stu-id="e678f-343">We then package the camera's extrinsic and intrinsic metadata with the video frame and then send it over the Skype service.</span></span>

<span data-ttu-id="e678f-344">在接收端，使用 Unity，我們已同步處理所有全像投影中使用相同的座標系統的 HoloLens 使用者的空間。</span><span class="sxs-lookup"><span data-stu-id="e678f-344">On the receiving side, using Unity, we've already synced all of the holograms in the HoloLens user's space using the same coordinate system.</span></span> <span data-ttu-id="e678f-345">這可讓我們使用相機的外建中繼資料來將 Unity 數位相機放在 HoloLens 使用者已釐時擷取視訊框架，（相對於全像投影的其餘部分） 世界中的確切位置，並使用相機內建函式的資訊來請確定檢視相同。</span><span class="sxs-lookup"><span data-stu-id="e678f-345">This allows us to use the camera's extrinsic metadata to place the Unity camera in the exact place in the world (relative to the rest of the holograms) that the HoloLens user was standing when that video frame was captured, and use the camera intrinsic information to ensure the view is the same.</span></span>

<span data-ttu-id="e678f-346">一旦擁有已正確地設定網路攝影機，我們會結合觀景窗會看到我們收到來自 Skype，建立的混合的實境檢視 HoloLens 使用者會看到使用 Graphics.Blit 框架到何種全像投影。</span><span class="sxs-lookup"><span data-stu-id="e678f-346">Once we have the camera set up properly, we combine what holograms the camera sees onto the frame we received from Skype, creating a mixed reality view of what the HoloLens user sees using Graphics.Blit.</span></span>

```cs
private void OnFrameReceived(Texture frameTexture, Vector3 cameraPosition, Quaternion cameraRotation, Matrix4x4 cameraProjectionMatrix)
{
    //set material that will be blitted onto the RenderTexture
    this.compositeMaterial.SetTexture(CompositeRenderer.CameraTextureMaterialProperty, frameTexture);
    //set the camera to be that of the HoloLens's device camera
    this.Camera.transform.position = cameraPosition;
    this.Camera.transform.rotation = cameraRotation;
    this.Camera.projectionMatrix = cameraProjectionMatrix;
    //trigger the Graphics's Blit now that the frame and camera are set up
    this.TextureReady = false;
}
private void OnRenderImage(RenderTexture source, RenderTexture destination)
{
    if (!this.TextureReady)
    {
        Graphics.Blit(source, destination, this.compositeMaterial);
        this.TextureReady = true;
    }
}
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a><span data-ttu-id="e678f-347">追蹤或識別標記的靜止或移動真實世界物件/字體使用 Led 或辨識器的其他程式庫</span><span class="sxs-lookup"><span data-stu-id="e678f-347">Track or Identify Tagged Stationary or Moving real-world objects/faces using LEDs or other recognizer libraries</span></span>

<span data-ttu-id="e678f-348">範例：</span><span class="sxs-lookup"><span data-stu-id="e678f-348">Examples:</span></span>
* <span data-ttu-id="e678f-349">工業機器人，各有 Led （或緩慢移動的 QR 代碼的物件）</span><span class="sxs-lookup"><span data-stu-id="e678f-349">Industrial robots with LEDs (or QR codes for slower moving objects)</span></span>
* <span data-ttu-id="e678f-350">找出並辨識在聊天室中的物件</span><span class="sxs-lookup"><span data-stu-id="e678f-350">Identify and recognize objects in the room</span></span>
* <span data-ttu-id="e678f-351">找出並辨識空間 （例如進行全像攝影版連絡人卡片透過臉部） 中的人員</span><span class="sxs-lookup"><span data-stu-id="e678f-351">Identify and recognize people in the room (e.g. place holographic contact cards over faces)</span></span>

## <a name="see-also"></a><span data-ttu-id="e678f-352">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e678f-352">See also</span></span>
* [<span data-ttu-id="e678f-353">DirectX 中的定位相機</span><span class="sxs-lookup"><span data-stu-id="e678f-353">Locatable camera in DirectX</span></span>](locatable-camera-in-directx.md)
* [<span data-ttu-id="e678f-354">Unity 中的定位相機</span><span class="sxs-lookup"><span data-stu-id="e678f-354">Locatable camera in Unity</span></span>](locatable-camera-in-unity.md)
* [<span data-ttu-id="e678f-355">混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="e678f-355">Mixed reality capture</span></span>](mixed-reality-capture.md)
* [<span data-ttu-id="e678f-356">適用於開發人員的混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="e678f-356">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="e678f-357">媒體擷取簡介</span><span class="sxs-lookup"><span data-stu-id="e678f-357">Media capture introduction</span></span>](https://msdn.microsoft.com/library/windows/apps/mt243896.aspx)
