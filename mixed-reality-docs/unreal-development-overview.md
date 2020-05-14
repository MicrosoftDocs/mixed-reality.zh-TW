---
title: Unreal 開發概觀
description: 使用 Unreal Engine 4 的混合實境開發概觀
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 串流, 遠端, 混合實境, 開發, 開始使用, 功能, 新專案, 模擬器, 文件, 指南, 功能, 全像投影
ms.openlocfilehash: 08ba760acc1a35d8f47de6a7bf6cbc020c8aca3f
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851562"
---
# <a name="unreal-development-overview"></a><span data-ttu-id="6e10c-104">Unreal 開發概觀</span><span class="sxs-lookup"><span data-stu-id="6e10c-104">Unreal development overview</span></span>

<span data-ttu-id="6e10c-105">Unreal Engine 4 現在完全支援 Windows Mixed Reality (VR) 和 HoloLens 2 (AR) 裝置的開發！</span><span class="sxs-lookup"><span data-stu-id="6e10c-105">Unreal Engine 4 now fully supports development for both Windows Mixed Reality (VR) and HoloLens 2 (AR) devices!</span></span> <span data-ttu-id="6e10c-106">如果您是 Unreal 開發的新手，<a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">開始使用 Unreal Engine 4</a> 是一個絕佳的探索頁面。</span><span class="sxs-lookup"><span data-stu-id="6e10c-106">If you're new to Unreal development, <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">Getting Started with Unreal Engine 4</a> is a great page to explore.</span></span> <span data-ttu-id="6e10c-107">如果您需要資產，Unreal 具有完整的 <a href="https://www.unrealengine.com/marketplace//store" target="_blank">Marketplace</a>。</span><span class="sxs-lookup"><span data-stu-id="6e10c-107">If you need assets, Unreal has a comprehensive <a href="https://www.unrealengine.com/marketplace//store" target="_blank">Marketplace</a>.</span></span> 

<span data-ttu-id="6e10c-108">在您取得 Unreal 開發的基本了解之後，請參閱下一節中的教學課程，以了解如何在 HoloLens 上建置及執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6e10c-108">Once you've gained a basic understanding of Unreal development, check out the tutorial in the next section to learn how to build and run your apps on HoloLens.</span></span> <span data-ttu-id="6e10c-109">請務必造訪 <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">Unreal 混合實境論壇</a>，與在 Unreal 中建置混合實境應用程式的社群進行互動。</span><span class="sxs-lookup"><span data-stu-id="6e10c-109">Be sure to visit the <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">Unreal Mixed Reality forums</a> to engage with the community building mixed reality apps in Unreal.</span></span> <span data-ttu-id="6e10c-110">這是尋找您可能遇到問題解決方案的絕佳位置。</span><span class="sxs-lookup"><span data-stu-id="6e10c-110">It's a great place to find solutions to problems you run into.</span></span>

## <a name="tutorial"></a><span data-ttu-id="6e10c-111">教學課程</span><span class="sxs-lookup"><span data-stu-id="6e10c-111">Tutorial</span></span>

<span data-ttu-id="6e10c-112">請遵循我們的端對端教學課程，以了解如何針對 HoloLens 2 [建置及部署簡單的國際象棋應用程式](unreal-uxt-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="6e10c-112">Learn how to [build and deploy a simple chess app](unreal-uxt-ch1.md) for HoloLens 2 by following our end-to-end tutorial.</span></span> <span data-ttu-id="6e10c-113">本教學課程使用 UX 工具外掛程式來加速使用互動式 UX 元件 (包括按鈕和操作工具) 開發應用程式。</span><span class="sxs-lookup"><span data-stu-id="6e10c-113">This tutorial uses the UX Tools plugin to accelerate developing apps with interactive UX components including a button and a manipulator.</span></span> <span data-ttu-id="6e10c-114">如需 UX 工具外掛程式的詳細資訊，請參閱下一節的 MRTK。</span><span class="sxs-lookup"><span data-stu-id="6e10c-114">For more information about UX Tools plugin, see the next section on MRTK.</span></span> 

## <a name="mixed-reality-toolkit-for-unreal"></a><span data-ttu-id="6e10c-115">適用於 Unreal 的混合實境工具組</span><span class="sxs-lookup"><span data-stu-id="6e10c-115">Mixed Reality Toolkit for Unreal</span></span>

<span data-ttu-id="6e10c-116">[適用於 Unreal 的混合實境工具組](https://github.com/microsoft/MixedRealityToolkit-Unreal)是一組元件，形式為外掛程式、範例和文件，其設計目的是加速使用 Unreal Engine 的混合實境應用程式開發。</span><span class="sxs-lookup"><span data-stu-id="6e10c-116">The [Mixed Reality Toolkit for Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) is a set of components, in the form of plugins, samples, and documentation, designed to accelerate the development of mixed reality applications using the Unreal Engine.</span></span> <span data-ttu-id="6e10c-117">此工具組中發行的第一個元件是[適用於 Unreal 的 UX 工具](https://github.com/microsoft/MixedReality-UXTools-Unreal)，這是可新增至 HoloLens 2 專案的外掛程式，為 HoloLens 2 應用程式提供 UX 功能。</span><span class="sxs-lookup"><span data-stu-id="6e10c-117">The first component released as part of this toolkit is the [UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal), a plugin that can be added to your HoloLens 2 project to provide UX features for HoloLens 2 applications.</span></span> <span data-ttu-id="6e10c-118">您可以在各自的 GitHub 存放庫中找到混合實境工具組和適用於 Unreal 的 UX 工具的文件。</span><span class="sxs-lookup"><span data-stu-id="6e10c-118">Documentation for the Mixed Reality Toolkit and UX Tools for Unreal can be found in their respective GitHub repositories.</span></span> 

## <a name="performance"></a><span data-ttu-id="6e10c-119">效能</span><span class="sxs-lookup"><span data-stu-id="6e10c-119">Performance</span></span>

<span data-ttu-id="6e10c-120">HoloLens 2 應用程式必須以每秒 60 格執行，才能讓全像投影穩定顯示並且看起來有回應。</span><span class="sxs-lookup"><span data-stu-id="6e10c-120">A HoloLens 2 app must run at 60 frames per second for holograms to appear stable and responsive.</span></span> <span data-ttu-id="6e10c-121">若要在您的應用程式中達到此目的，我們強烈建議您遵循我們[對 Unreal 的效能建議](performance-recommendations-for-unreal.md)。</span><span class="sxs-lookup"><span data-stu-id="6e10c-121">To achieve this in your app, we highly recommend following our [performance recommendations for Unreal](performance-recommendations-for-unreal.md).</span></span> 

## <a name="guides-to-specific-features"></a><span data-ttu-id="6e10c-122">特定功能的指南</span><span class="sxs-lookup"><span data-stu-id="6e10c-122">Guides to specific features</span></span>

<span data-ttu-id="6e10c-123">若要了解如何使用 Unreal 中的特定功能，請參閱下列指南：</span><span class="sxs-lookup"><span data-stu-id="6e10c-123">To learn how to use specific features in Unreal, check out the below guides:</span></span> 
* [<span data-ttu-id="6e10c-124">手勢追蹤</span><span class="sxs-lookup"><span data-stu-id="6e10c-124">Hand tracking</span></span>](unreal-hand-tracking.md)
* [<span data-ttu-id="6e10c-125">眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="6e10c-125">Eye tracking</span></span>](unreal-gaze-input.md)
* [<span data-ttu-id="6e10c-126">空間對應</span><span class="sxs-lookup"><span data-stu-id="6e10c-126">Spatial mapping</span></span>](unreal-spatial-mapping.md)
* [<span data-ttu-id="6e10c-127">空間錨點</span><span class="sxs-lookup"><span data-stu-id="6e10c-127">Spatial anchors</span></span>](unreal-spatial-anchors.md)
* [<span data-ttu-id="6e10c-128">語音輸入</span><span class="sxs-lookup"><span data-stu-id="6e10c-128">Voice input</span></span>](unreal-voice-input.md)
* [<span data-ttu-id="6e10c-129">HoloLens 相機</span><span class="sxs-lookup"><span data-stu-id="6e10c-129">HoloLens camera</span></span>](unreal-hololens-camera.md)
* [<span data-ttu-id="6e10c-130">QR 代碼</span><span class="sxs-lookup"><span data-stu-id="6e10c-130">QR codes</span></span>](unreal-qr-codes.md)

## <a name="supported-features"></a><span data-ttu-id="6e10c-131">支援的功能</span><span class="sxs-lookup"><span data-stu-id="6e10c-131">Supported Features</span></span>

| <span data-ttu-id="6e10c-132">HoloLens 2 功能</span><span class="sxs-lookup"><span data-stu-id="6e10c-132">HoloLens 2 Feature</span></span> | <span data-ttu-id="6e10c-133">最早支援的 Unreal Engine 版本</span><span class="sxs-lookup"><span data-stu-id="6e10c-133">Earliest Supported Unreal Engine Version</span></span> |
| ----------- | ----------- |
| <span data-ttu-id="6e10c-134">ARM64 支援</span><span class="sxs-lookup"><span data-stu-id="6e10c-134">ARM64 support</span></span> | <span data-ttu-id="6e10c-135">4.23</span><span class="sxs-lookup"><span data-stu-id="6e10c-135">4.23</span></span> |
| <span data-ttu-id="6e10c-136">來自電腦的串流</span><span class="sxs-lookup"><span data-stu-id="6e10c-136">Streaming from a PC</span></span> | <span data-ttu-id="6e10c-137">4.23</span><span class="sxs-lookup"><span data-stu-id="6e10c-137">4.23</span></span> |
| <span data-ttu-id="6e10c-138">空間對應</span><span class="sxs-lookup"><span data-stu-id="6e10c-138">Spatial mapping</span></span> | <span data-ttu-id="6e10c-139">4.23</span><span class="sxs-lookup"><span data-stu-id="6e10c-139">4.23</span></span> |
| <span data-ttu-id="6e10c-140">手部和關節追蹤</span><span class="sxs-lookup"><span data-stu-id="6e10c-140">Hand and joint tracking</span></span> | <span data-ttu-id="6e10c-141">4.23</span><span class="sxs-lookup"><span data-stu-id="6e10c-141">4.23</span></span> |
| <span data-ttu-id="6e10c-142">眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="6e10c-142">Eye tracking</span></span> | <span data-ttu-id="6e10c-143">4.23</span><span class="sxs-lookup"><span data-stu-id="6e10c-143">4.23</span></span> |
| <span data-ttu-id="6e10c-144">語音輸入</span><span class="sxs-lookup"><span data-stu-id="6e10c-144">Voice input</span></span> | <span data-ttu-id="6e10c-145">4.23</span><span class="sxs-lookup"><span data-stu-id="6e10c-145">4.23</span></span> |
| <span data-ttu-id="6e10c-146">空間錨點</span><span class="sxs-lookup"><span data-stu-id="6e10c-146">Spatial anchors</span></span> | <span data-ttu-id="6e10c-147">4.23</span><span class="sxs-lookup"><span data-stu-id="6e10c-147">4.23</span></span> |
| <span data-ttu-id="6e10c-148">相機存取</span><span class="sxs-lookup"><span data-stu-id="6e10c-148">Camera access</span></span> | <span data-ttu-id="6e10c-149">4.23</span><span class="sxs-lookup"><span data-stu-id="6e10c-149">4.23</span></span> |
| <span data-ttu-id="6e10c-150">QR 代碼</span><span class="sxs-lookup"><span data-stu-id="6e10c-150">QR codes</span></span> | <span data-ttu-id="6e10c-151">4.23</span><span class="sxs-lookup"><span data-stu-id="6e10c-151">4.23</span></span> |
| <span data-ttu-id="6e10c-152">空間音訊</span><span class="sxs-lookup"><span data-stu-id="6e10c-152">Spatial audio</span></span> | <span data-ttu-id="6e10c-153">4.23</span><span class="sxs-lookup"><span data-stu-id="6e10c-153">4.23</span></span> |
| <span data-ttu-id="6e10c-154">串流的觀眾螢幕支援</span><span class="sxs-lookup"><span data-stu-id="6e10c-154">Spectator Screen support for streaming</span></span> | <span data-ttu-id="6e10c-155">4.24</span><span class="sxs-lookup"><span data-stu-id="6e10c-155">4.24</span></span> |
| <span data-ttu-id="6e10c-156">透過串流的平面 LSR</span><span class="sxs-lookup"><span data-stu-id="6e10c-156">Planar LSR over streaming</span></span> | <span data-ttu-id="6e10c-157">4.24</span><span class="sxs-lookup"><span data-stu-id="6e10c-157">4.24</span></span> |
| <span data-ttu-id="6e10c-158">範例應用程式 ([HoloLens2Example](https://github.com/microsoft/MixedReality-Unreal-Samples) 和 [Mission AR](https://docs.unrealengine.com/en-US/Resources/Showcases/MissionAR/index.html))</span><span class="sxs-lookup"><span data-stu-id="6e10c-158">Sample apps ([HoloLens2Example](https://github.com/microsoft/MixedReality-Unreal-Samples) and [Mission AR](https://docs.unrealengine.com/en-US/Resources/Showcases/MissionAR/index.html))</span></span> | <span data-ttu-id="6e10c-159">4.24</span><span class="sxs-lookup"><span data-stu-id="6e10c-159">4.24</span></span> |
| <span data-ttu-id="6e10c-160">行動多重檢視：效能命中 60 fps</span><span class="sxs-lookup"><span data-stu-id="6e10c-160">Mobile multi-View: Performance hits 60 fps</span></span> | <span data-ttu-id="6e10c-161">4.25</span><span class="sxs-lookup"><span data-stu-id="6e10c-161">4.25</span></span> |
| <span data-ttu-id="6e10c-162">第三相機轉譯</span><span class="sxs-lookup"><span data-stu-id="6e10c-162">3rd camera render</span></span> | <span data-ttu-id="6e10c-163">4.25</span><span class="sxs-lookup"><span data-stu-id="6e10c-163">4.25</span></span> |
| <span data-ttu-id="6e10c-164">從已封裝的桌面應用程式串流</span><span class="sxs-lookup"><span data-stu-id="6e10c-164">Streaming from a packaged desktop app</span></span> | <span data-ttu-id="6e10c-165">4.25</span><span class="sxs-lookup"><span data-stu-id="6e10c-165">4.25</span></span> |
| <span data-ttu-id="6e10c-166">適用於 HoloLens 2 的 Azure Spatial Anchors 搶鮮版 (Beta)</span><span class="sxs-lookup"><span data-stu-id="6e10c-166">Azure Spatial Anchors for HoloLens 2 (beta)</span></span> | <span data-ttu-id="6e10c-167">4.25</span><span class="sxs-lookup"><span data-stu-id="6e10c-167">4.25</span></span> |
| <span data-ttu-id="6e10c-168">OpenXR 支援搶鮮版 (Beta)</span><span class="sxs-lookup"><span data-stu-id="6e10c-168">OpenXR support (beta)</span></span> | <span data-ttu-id="6e10c-169">4.25</span><span class="sxs-lookup"><span data-stu-id="6e10c-169">4.25</span></span> |
| <span data-ttu-id="6e10c-170">UX 工具支援 (0.8)</span><span class="sxs-lookup"><span data-stu-id="6e10c-170">UX Tools support (0.8)</span></span> | <span data-ttu-id="6e10c-171">4.25</span><span class="sxs-lookup"><span data-stu-id="6e10c-171">4.25</span></span> |
| <span data-ttu-id="6e10c-172">開發人員文件和教學課程</span><span class="sxs-lookup"><span data-stu-id="6e10c-172">Developer docs & tutorials</span></span> | <span data-ttu-id="6e10c-173">4.25</span><span class="sxs-lookup"><span data-stu-id="6e10c-173">4.25</span></span> |

## <a name="see-also"></a><span data-ttu-id="6e10c-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e10c-174">See also</span></span>
* <span data-ttu-id="6e10c-175"><a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">適用於串流、部署至模擬器和裝置的 Unreal 文件</a></span><span class="sxs-lookup"><span data-stu-id="6e10c-175"><a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">Unreal docs for streaming, deploying to emulator and device</a></span></span>
* <span data-ttu-id="6e10c-176"><a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">行動裝置的 Unreal 效能指導方針</a></span><span class="sxs-lookup"><span data-stu-id="6e10c-176"><a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">Unreal performance guidelines for mobile devices</a></span></span>
