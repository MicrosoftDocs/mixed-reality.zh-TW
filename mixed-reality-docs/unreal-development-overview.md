---
title: Unreal 開發概觀
description: 使用 Unreal Engine 4 的混合實境開發概觀
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 串流, 遠端, 混合實境, 開發, 開始使用, 功能, 新專案, 模擬器, 文件, 指南, 功能, 全像投影, 遊戲開發
ms.openlocfilehash: 3e3862bd701d6e873f623abc9f9cda0b3085e753
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330155"
---
# <a name="unreal-development-overview"></a><span data-ttu-id="8aff7-104">Unreal 開發概觀</span><span class="sxs-lookup"><span data-stu-id="8aff7-104">Unreal Development Overview</span></span>

<span data-ttu-id="8aff7-105">開始使用 <a href="https://docs.microsoft.com/en-us/windows/mixed-reality" target="_blank" title="Mixed Reality Docs"> 混合實境應用程式</a>是一項大型工作。</span><span class="sxs-lookup"><span data-stu-id="8aff7-105">Getting started with <a href="https://docs.microsoft.com/en-us/windows/mixed-reality" target="_blank" title="Mixed Reality Docs"> mixed reality applications</a> is a big task.</span></span> <span data-ttu-id="8aff7-106">新的概念、平台和尖端硬體看起來可能像是障礙。</span><span class="sxs-lookup"><span data-stu-id="8aff7-106">New concepts, platforms, and cutting edge hardware can seem like barriers.</span></span> <span data-ttu-id="8aff7-107">不過，如果您是 Unreal 開發人員，很幸運。</span><span class="sxs-lookup"><span data-stu-id="8aff7-107">However, if you're an Unreal developer you're in luck.</span></span> <span data-ttu-id="8aff7-108">在 Unreal Engine 的最新 <a href="https://docs.unrealengine.com/en-US/Support/Builds/ReleaseNotes/4_25/index.html" target="_blank" title="Unreal Engine 4.25 版本資訊">版本</a>中，現在引進了 <a href="https://www.microsoft.com/en-us/windows/windows-mixed-reality" target="_blank" title="Windows Mixed Reality Docs">Windows Mixed Reality</a> (VR) 和 <a href="https://www.microsoft.com/en-us/hololens/hardware" target="_blank" title="HoloLens 2 Docs">HoloLens 2</a> (AR) 的支援。</span><span class="sxs-lookup"><span data-stu-id="8aff7-108">Support for <a href="https://www.microsoft.com/en-us/windows/windows-mixed-reality" target="_blank" title="Windows Mixed Reality Docs">Windows Mixed Reality</a> (VR) and <a href="https://www.microsoft.com/en-us/hololens/hardware" target="_blank" title="HoloLens 2 Docs">HoloLens 2</a> (AR) is now included in Unreal Engine's newest <a href="https://docs.unrealengine.com/en-US/Support/Builds/ReleaseNotes/4_25/index.html" target="_blank" title="Unreal Engine 4.25 release notes">release</a>.</span></span> <span data-ttu-id="8aff7-109">此更新包括：</span><span class="sxs-lookup"><span data-stu-id="8aff7-109">This update includes:</span></span>
* <span data-ttu-id="8aff7-110">混合實境 UX 工具外掛程式支援</span><span class="sxs-lookup"><span data-stu-id="8aff7-110">Mixed Reality UX Tools plugin support</span></span>
* <span data-ttu-id="8aff7-111">OpenXR 支援</span><span class="sxs-lookup"><span data-stu-id="8aff7-111">OpenXR support</span></span>
* <span data-ttu-id="8aff7-112">從傳統型應用程式進行的應用程式遠端處理</span><span class="sxs-lookup"><span data-stu-id="8aff7-112">App Remoting from a desktop app</span></span>
* <span data-ttu-id="8aff7-113">更好的效能</span><span class="sxs-lookup"><span data-stu-id="8aff7-113">Better performance</span></span>
* <span data-ttu-id="8aff7-114">混合實境擷取</span><span class="sxs-lookup"><span data-stu-id="8aff7-114">Mixed reality capture</span></span>
* <span data-ttu-id="8aff7-115">Azure Spatial Anchors 的初始支援</span><span class="sxs-lookup"><span data-stu-id="8aff7-115">Initial support for Azure Spatial Anchors</span></span>

<span data-ttu-id="8aff7-116">如果您不熟悉 Unreal 開發，請不要盲目跳入。</span><span class="sxs-lookup"><span data-stu-id="8aff7-116">If you're new to Unreal development don't jump in blind.</span></span> <span data-ttu-id="8aff7-117">探索 Unreal <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">教學課程系列</a>，以快速了解並尋找 Unreal <a href="https://www.unrealengine.com/marketplace//store" target="_blank">市集</a>和混合實境<a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">論壇</a>中的資產和支援。</span><span class="sxs-lookup"><span data-stu-id="8aff7-117">Explore the Unreal <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">tutorial series</a> to get up to speed and look for assets and support in the Unreal <a href="https://www.unrealengine.com/marketplace//store" target="_blank">marketplace</a> and mixed reality <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">forums</a>.</span></span> <span data-ttu-id="8aff7-118">這些資源可將您連結至今日混合實境市集中建置者和問題解決者的社群。</span><span class="sxs-lookup"><span data-stu-id="8aff7-118">These resources are your links to the community of builders and problem solvers in todays mixed reality market.</span></span>

## <a name="mixed-reality-toolkit-for-unreal"></a><span data-ttu-id="8aff7-119">適用於 Unreal 的混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="8aff7-119">Mixed Reality Toolkit for Unreal</span></span>

<span data-ttu-id="8aff7-120">[適用於 Unreal 的混合實境工具組](https://github.com/microsoft/MixedRealityToolkit-Unreal)是為了加速您在 Unreal 中進行開發而設計的一組元件。</span><span class="sxs-lookup"><span data-stu-id="8aff7-120">The [Mixed Reality Toolkit for Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) is a set of components designed to speed up your development in Unreal.</span></span> <span data-ttu-id="8aff7-121">每個元件都包含用於設定沉浸式體驗的外掛程式、範例和文件。</span><span class="sxs-lookup"><span data-stu-id="8aff7-121">Each component includes plugins, samples, and documentation for setting up immersive experiences.</span></span> 

<span data-ttu-id="8aff7-122">[適用於 Unreal 的 UX 工具](https://github.com/microsoft/MixedReality-UXTools-Unreal)是第一個要發行的元件，目前僅在 HoloLens 2 上提供支援。</span><span class="sxs-lookup"><span data-stu-id="8aff7-122">[UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal) is the first component to be released and is currently only supported on HoloLens 2.</span></span> <span data-ttu-id="8aff7-123">元件外掛程式包括常用 UX 功能的程式碼、藍圖和範例資產，包括：</span><span class="sxs-lookup"><span data-stu-id="8aff7-123">The component plugin includes code, blueprints, and example assets of common UX features including:</span></span>
* <span data-ttu-id="8aff7-124">輸入模擬</span><span class="sxs-lookup"><span data-stu-id="8aff7-124">Input simulation</span></span>
* <span data-ttu-id="8aff7-125">手部互動動作項目</span><span class="sxs-lookup"><span data-stu-id="8aff7-125">Hand interaction actor</span></span>
* <span data-ttu-id="8aff7-126">可點按的按鈕元件</span><span class="sxs-lookup"><span data-stu-id="8aff7-126">Pressable button component</span></span>
* <span data-ttu-id="8aff7-127">操作工具元件</span><span class="sxs-lookup"><span data-stu-id="8aff7-127">Manipulator component</span></span>
* <span data-ttu-id="8aff7-128">追蹤行為元件</span><span class="sxs-lookup"><span data-stu-id="8aff7-128">Follow behavior component</span></span>

<span data-ttu-id="8aff7-129">您可以深入了解[適用於 Unreal 的 UX 工具](https://github.com/microsoft/MixedReality-UXTools-Unreal) GitHub 存放庫，以取得功能詳細資料和設定專案的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8aff7-129">You can dive into the [UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal) GitHub repository for feature details and information on setting up your project.</span></span>

## <a name="tutorial"></a><span data-ttu-id="8aff7-130">教學課程</span><span class="sxs-lookup"><span data-stu-id="8aff7-130">Tutorial</span></span>

<span data-ttu-id="8aff7-131">使用您的雙手建置東西，是學習新技能的最佳方法。</span><span class="sxs-lookup"><span data-stu-id="8aff7-131">Building something with your own two hands is the best way to learn a new skill.</span></span> <span data-ttu-id="8aff7-132">了解如何使用 UX 工具外掛程式，為 HoloLens 2 [建置和部署簡單的國際象棋應用程式](unreal-uxt-ch1.md)，是很好的起點。</span><span class="sxs-lookup"><span data-stu-id="8aff7-132">Learning how to [build and deploy a simple chess app](unreal-uxt-ch1.md) for HoloLens 2 with the UX Tools plugin is a great way to start.</span></span> 

<span data-ttu-id="8aff7-133">端對端教學課程系列提供與常見互動式 UX 元件和案例的實際操作聯繫。</span><span class="sxs-lookup"><span data-stu-id="8aff7-133">The end-to-end tutorial series provides hands-on contact with common interactive UX components and scenarios.</span></span> <span data-ttu-id="8aff7-134">您將逐步完成專案設定、新增場景的互動，以及部署至裝置或模擬器。</span><span class="sxs-lookup"><span data-stu-id="8aff7-134">You'll work through the project setup, adding interactions to the scene, and deploying to a device or emulator.</span></span> <span data-ttu-id="8aff7-135">您只需要 Windows 10、模擬器和 Visual Studio 2019。</span><span class="sxs-lookup"><span data-stu-id="8aff7-135">All you need is Windows 10, an emulator, and Visual Studio 2019.</span></span>


## <a name="performance"></a><span data-ttu-id="8aff7-136">效能</span><span class="sxs-lookup"><span data-stu-id="8aff7-136">Performance</span></span>

<span data-ttu-id="8aff7-137">針對混合實境進行開發時，隨附依賴平台的效能檢查點。</span><span class="sxs-lookup"><span data-stu-id="8aff7-137">Developing for mixed reality comes with performance checkpoints that depend on the platform.</span></span> <span data-ttu-id="8aff7-138">HoloLens 2 應用程式必須以每秒 60 格執行，才能讓全像投影穩定顯示並且看起來有回應。</span><span class="sxs-lookup"><span data-stu-id="8aff7-138">A HoloLens 2 app must run at 60 frames per second for holograms to appear stable and responsive.</span></span> <span data-ttu-id="8aff7-139">幸好，Unreal 提供[效能建議](performance-recommendations-for-unreal.md)，以在您的應用程式中實現此目的。</span><span class="sxs-lookup"><span data-stu-id="8aff7-139">Luckily, Unreal provides [performance recommendations](performance-recommendations-for-unreal.md) for achieving this in your applications.</span></span>

## <a name="guides-to-specific-features"></a><span data-ttu-id="8aff7-140">特定功能的指南</span><span class="sxs-lookup"><span data-stu-id="8aff7-140">Guides to specific features</span></span>

<span data-ttu-id="8aff7-141">混合實境開發有幾個重要功能不在我們的教學課程系列討論範圍內。</span><span class="sxs-lookup"><span data-stu-id="8aff7-141">There are several key features of mixed reality development that our tutorial series doesn't cover.</span></span> <span data-ttu-id="8aff7-142">參閱下列指南以取得詳細資料和實用應用程式：</span><span class="sxs-lookup"><span data-stu-id="8aff7-142">Check out the following guides for details and practical applications:</span></span> 
* [<span data-ttu-id="8aff7-143">手勢追蹤</span><span class="sxs-lookup"><span data-stu-id="8aff7-143">Hand tracking</span></span>](unreal-hand-tracking.md)
* [<span data-ttu-id="8aff7-144">眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="8aff7-144">Eye tracking</span></span>](unreal-gaze-input.md)
* [<span data-ttu-id="8aff7-145">空間對應</span><span class="sxs-lookup"><span data-stu-id="8aff7-145">Spatial mapping</span></span>](unreal-spatial-mapping.md)
* [<span data-ttu-id="8aff7-146">空間錨點</span><span class="sxs-lookup"><span data-stu-id="8aff7-146">Spatial anchors</span></span>](unreal-spatial-anchors.md)
* [<span data-ttu-id="8aff7-147">語音輸入</span><span class="sxs-lookup"><span data-stu-id="8aff7-147">Voice input</span></span>](unreal-voice-input.md)
* [<span data-ttu-id="8aff7-148">HoloLens 相機</span><span class="sxs-lookup"><span data-stu-id="8aff7-148">HoloLens camera</span></span>](unreal-hololens-camera.md)
* [<span data-ttu-id="8aff7-149">QR 代碼</span><span class="sxs-lookup"><span data-stu-id="8aff7-149">QR codes</span></span>](unreal-qr-codes.md)


## <a name="supported-features"></a><span data-ttu-id="8aff7-150">支援的功能</span><span class="sxs-lookup"><span data-stu-id="8aff7-150">Supported Features</span></span>

| <span data-ttu-id="8aff7-151">HoloLens 2 功能</span><span class="sxs-lookup"><span data-stu-id="8aff7-151">HoloLens 2 Feature</span></span> | <span data-ttu-id="8aff7-152">最早支援的 Unreal Engine 版本</span><span class="sxs-lookup"><span data-stu-id="8aff7-152">Earliest Supported Unreal Engine Version</span></span> |
| ----------- | ----------- |
| <span data-ttu-id="8aff7-153">ARM64 支援</span><span class="sxs-lookup"><span data-stu-id="8aff7-153">ARM64 support</span></span> | <span data-ttu-id="8aff7-154">4.23</span><span class="sxs-lookup"><span data-stu-id="8aff7-154">4.23</span></span> |
| <span data-ttu-id="8aff7-155">來自電腦的串流</span><span class="sxs-lookup"><span data-stu-id="8aff7-155">Streaming from a PC</span></span> | <span data-ttu-id="8aff7-156">4.23</span><span class="sxs-lookup"><span data-stu-id="8aff7-156">4.23</span></span> |
| <span data-ttu-id="8aff7-157">空間對應</span><span class="sxs-lookup"><span data-stu-id="8aff7-157">Spatial mapping</span></span> | <span data-ttu-id="8aff7-158">4.23</span><span class="sxs-lookup"><span data-stu-id="8aff7-158">4.23</span></span> |
| <span data-ttu-id="8aff7-159">手部和關節追蹤</span><span class="sxs-lookup"><span data-stu-id="8aff7-159">Hand and joint tracking</span></span> | <span data-ttu-id="8aff7-160">4.23</span><span class="sxs-lookup"><span data-stu-id="8aff7-160">4.23</span></span> |
| <span data-ttu-id="8aff7-161">眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="8aff7-161">Eye tracking</span></span> | <span data-ttu-id="8aff7-162">4.23</span><span class="sxs-lookup"><span data-stu-id="8aff7-162">4.23</span></span> |
| <span data-ttu-id="8aff7-163">語音輸入</span><span class="sxs-lookup"><span data-stu-id="8aff7-163">Voice input</span></span> | <span data-ttu-id="8aff7-164">4.23</span><span class="sxs-lookup"><span data-stu-id="8aff7-164">4.23</span></span> |
| <span data-ttu-id="8aff7-165">空間錨點</span><span class="sxs-lookup"><span data-stu-id="8aff7-165">Spatial anchors</span></span> | <span data-ttu-id="8aff7-166">4.23</span><span class="sxs-lookup"><span data-stu-id="8aff7-166">4.23</span></span> |
| <span data-ttu-id="8aff7-167">相機存取</span><span class="sxs-lookup"><span data-stu-id="8aff7-167">Camera access</span></span> | <span data-ttu-id="8aff7-168">4.23</span><span class="sxs-lookup"><span data-stu-id="8aff7-168">4.23</span></span> |
| <span data-ttu-id="8aff7-169">QR 代碼</span><span class="sxs-lookup"><span data-stu-id="8aff7-169">QR codes</span></span> | <span data-ttu-id="8aff7-170">4.23</span><span class="sxs-lookup"><span data-stu-id="8aff7-170">4.23</span></span> |
| <span data-ttu-id="8aff7-171">空間音訊</span><span class="sxs-lookup"><span data-stu-id="8aff7-171">Spatial audio</span></span> | <span data-ttu-id="8aff7-172">4.23</span><span class="sxs-lookup"><span data-stu-id="8aff7-172">4.23</span></span> |
| <span data-ttu-id="8aff7-173">串流的觀眾螢幕支援</span><span class="sxs-lookup"><span data-stu-id="8aff7-173">Spectator Screen support for streaming</span></span> | <span data-ttu-id="8aff7-174">4.24</span><span class="sxs-lookup"><span data-stu-id="8aff7-174">4.24</span></span> |
| <span data-ttu-id="8aff7-175">透過串流的平面 LSR</span><span class="sxs-lookup"><span data-stu-id="8aff7-175">Planar LSR over streaming</span></span> | <span data-ttu-id="8aff7-176">4.24</span><span class="sxs-lookup"><span data-stu-id="8aff7-176">4.24</span></span> |
| <span data-ttu-id="8aff7-177">範例應用程式 ([HoloLens2Example](https://github.com/microsoft/MixedReality-Unreal-Samples) 和 [Mission AR](https://docs.unrealengine.com/en-US/Resources/Showcases/MissionAR/index.html))</span><span class="sxs-lookup"><span data-stu-id="8aff7-177">Sample apps ([HoloLens2Example](https://github.com/microsoft/MixedReality-Unreal-Samples) and [Mission AR](https://docs.unrealengine.com/en-US/Resources/Showcases/MissionAR/index.html))</span></span> | <span data-ttu-id="8aff7-178">4.24</span><span class="sxs-lookup"><span data-stu-id="8aff7-178">4.24</span></span> |
| <span data-ttu-id="8aff7-179">行動多重檢視：效能命中 60 fps</span><span class="sxs-lookup"><span data-stu-id="8aff7-179">Mobile multi-View: Performance hits 60 fps</span></span> | <span data-ttu-id="8aff7-180">4.25</span><span class="sxs-lookup"><span data-stu-id="8aff7-180">4.25</span></span> |
| <span data-ttu-id="8aff7-181">第三相機轉譯</span><span class="sxs-lookup"><span data-stu-id="8aff7-181">3rd camera render</span></span> | <span data-ttu-id="8aff7-182">4.25</span><span class="sxs-lookup"><span data-stu-id="8aff7-182">4.25</span></span> |
| <span data-ttu-id="8aff7-183">從已封裝的桌面應用程式串流</span><span class="sxs-lookup"><span data-stu-id="8aff7-183">Streaming from a packaged desktop app</span></span> | <span data-ttu-id="8aff7-184">4.25</span><span class="sxs-lookup"><span data-stu-id="8aff7-184">4.25</span></span> |
| <span data-ttu-id="8aff7-185">適用於 HoloLens 2 的 Azure Spatial Anchors 搶鮮版 (Beta)</span><span class="sxs-lookup"><span data-stu-id="8aff7-185">Azure Spatial Anchors for HoloLens 2 (beta)</span></span> | <span data-ttu-id="8aff7-186">4.25</span><span class="sxs-lookup"><span data-stu-id="8aff7-186">4.25</span></span> |
| <span data-ttu-id="8aff7-187">OpenXR 支援搶鮮版 (Beta)</span><span class="sxs-lookup"><span data-stu-id="8aff7-187">OpenXR support (beta)</span></span> | <span data-ttu-id="8aff7-188">4.25</span><span class="sxs-lookup"><span data-stu-id="8aff7-188">4.25</span></span> |
| <span data-ttu-id="8aff7-189">UX 工具支援 (0.8)</span><span class="sxs-lookup"><span data-stu-id="8aff7-189">UX Tools support (0.8)</span></span> | <span data-ttu-id="8aff7-190">4.25</span><span class="sxs-lookup"><span data-stu-id="8aff7-190">4.25</span></span> |
| <span data-ttu-id="8aff7-191">開發人員文件和教學課程</span><span class="sxs-lookup"><span data-stu-id="8aff7-191">Developer docs & tutorials</span></span> | <span data-ttu-id="8aff7-192">4.25</span><span class="sxs-lookup"><span data-stu-id="8aff7-192">4.25</span></span> |

## <a name="see-also"></a><span data-ttu-id="8aff7-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8aff7-193">See also</span></span>
* <span data-ttu-id="8aff7-194"><a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">適用於串流、部署至模擬器和裝置的 Unreal 文件</a></span><span class="sxs-lookup"><span data-stu-id="8aff7-194"><a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">Unreal docs for streaming, deploying to emulator and device</a></span></span>
* <span data-ttu-id="8aff7-195"><a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">行動裝置的 Unreal 效能指導方針</a></span><span class="sxs-lookup"><span data-stu-id="8aff7-195"><a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">Unreal performance guidelines for mobile devices</a></span></span>
