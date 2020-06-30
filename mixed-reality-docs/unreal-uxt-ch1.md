---
title: 1. 開始使用
description: 教學課程系列的第 1 部分 (共有 6 部分)，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置簡單的國際象棋應用程式
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件
ms.openlocfilehash: 39e4e7218341dcc69eacf01f43b5e0721e76031b
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720374"
---
# <a name="1-getting-started"></a><span data-ttu-id="900ff-104">1.開始使用</span><span class="sxs-lookup"><span data-stu-id="900ff-104">1. Getting started</span></span>

<span data-ttu-id="900ff-105">無論您是混合實境的新手還是經驗豐富的專業人員，都可以從 [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) 和 [Unreal Engine](https://www.unrealengine.com/en-US/) 開始著手進行。</span><span class="sxs-lookup"><span data-stu-id="900ff-105">Whether you're new to mixed reality or a seasoned pro, this is the place to start your journey with [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) and [Unreal Engine](https://www.unrealengine.com/en-US/).</span></span> <span data-ttu-id="900ff-106">本教學課程系列將提供逐步指南，說明如何使用 [UX 工具外掛程式](https://github.com/microsoft/MixedReality-UXTools-Unreal)建立互動式的國際象棋應用程式 - 這是[適用於 Unreal 的混合實境工具組](https://github.com/microsoft/MixedRealityToolkit-Unreal)的一部分。</span><span class="sxs-lookup"><span data-stu-id="900ff-106">This tutorial series will give you a step by step guide on how to build an interactive chess app with the [UX Tools plugin](https://github.com/microsoft/MixedReality-UXTools-Unreal) - part of the [Mixed Reality Toolkit for Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span></span> <span data-ttu-id="900ff-107">此外掛程式可協助您使用程式碼、藍圖和範例，將常用的 UX 功能新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="900ff-107">The plugin will help you add common UX features to your projects with code, blueprints, and examples.</span></span> 

![檢視區中的最終場景](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="900ff-109">在系列結束時，您將擁有以下的實際操作體驗：</span><span class="sxs-lookup"><span data-stu-id="900ff-109">By the end of the series you'll have hands-on experience with:</span></span>
* <span data-ttu-id="900ff-110">開始新專案</span><span class="sxs-lookup"><span data-stu-id="900ff-110">Starting a new project</span></span>
* <span data-ttu-id="900ff-111">設定混合實境</span><span class="sxs-lookup"><span data-stu-id="900ff-111">Setting up for mixed reality</span></span>
* <span data-ttu-id="900ff-112">處理使用者輸入</span><span class="sxs-lookup"><span data-stu-id="900ff-112">Working with user input</span></span>
* <span data-ttu-id="900ff-113">新增按鈕</span><span class="sxs-lookup"><span data-stu-id="900ff-113">Adding buttons</span></span>
* <span data-ttu-id="900ff-114">在模擬器或裝置上播放</span><span class="sxs-lookup"><span data-stu-id="900ff-114">Playing on an emulator or device</span></span>

<span data-ttu-id="900ff-115">如有任何疑問，請參閱我們的 [Unreal 開發概觀](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview)。</span><span class="sxs-lookup"><span data-stu-id="900ff-115">If you have any questions, check out our [Unreal development overview](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="900ff-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="900ff-116">Prerequisites</span></span>
<span data-ttu-id="900ff-117">在進行之前，請先確定您已符合下列需求：</span><span class="sxs-lookup"><span data-stu-id="900ff-117">Make sure you've met the following requirements before jumping in:</span></span>
* <span data-ttu-id="900ff-118">Windows 10 1809 或更新版本</span><span class="sxs-lookup"><span data-stu-id="900ff-118">Windows 10 1809 or later</span></span>
* <span data-ttu-id="900ff-119">Windows 10 SDK 10.0.18362.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="900ff-119">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="900ff-120">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 或更新版本</span><span class="sxs-lookup"><span data-stu-id="900ff-120">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 or later</span></span>
* <span data-ttu-id="900ff-121">[針對開發而設定](using-visual-studio.md#enabling-developer-mode)的 Microsoft HoloLens 2 裝置或模擬器</span><span class="sxs-lookup"><span data-stu-id="900ff-121">Microsoft HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode) or Emulator</span></span>
* <span data-ttu-id="900ff-122">Visual Studio 2019 與下列工作負載</span><span class="sxs-lookup"><span data-stu-id="900ff-122">Visual Studio 2019 with the workloads below</span></span>

### <a name="installing-visual-studio-2019"></a><span data-ttu-id="900ff-123">安裝 Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="900ff-123">Installing Visual Studio 2019</span></span>
<span data-ttu-id="900ff-124">最後一個步驟是設定 Visual Studio，如下所示：</span><span class="sxs-lookup"><span data-stu-id="900ff-124">The last step is to setup Visual Studio as follows:</span></span>
1. <span data-ttu-id="900ff-125">安裝最新版 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span><span class="sxs-lookup"><span data-stu-id="900ff-125">Install the latest version of [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span></span>
2. <span data-ttu-id="900ff-126">安裝下列[工作負載](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-workloads)：</span><span class="sxs-lookup"><span data-stu-id="900ff-126">Install the following [workloads](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-workloads):</span></span>
    * <span data-ttu-id="900ff-127">使用 C++ 的傳統型開發</span><span class="sxs-lookup"><span data-stu-id="900ff-127">Desktop development with C++</span></span>
    * <span data-ttu-id="900ff-128">.NET 桌面開發</span><span class="sxs-lookup"><span data-stu-id="900ff-128">.NET desktop development</span></span>
    * <span data-ttu-id="900ff-129">通用 Windows 平台開發</span><span class="sxs-lookup"><span data-stu-id="900ff-129">Universal Windows Platform development</span></span>

3. <span data-ttu-id="900ff-130">安裝下列[元件](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-individual-components)：</span><span class="sxs-lookup"><span data-stu-id="900ff-130">Install the following [components](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-individual-components):</span></span>
    * <span data-ttu-id="900ff-131">編譯器、建置工具與執行階段 > MSVC v142 - VS 2019 C++ ARM64 建置工具 (最新版本)</span><span class="sxs-lookup"><span data-stu-id="900ff-131">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

<span data-ttu-id="900ff-132">這樣就完成了！</span><span class="sxs-lookup"><span data-stu-id="900ff-132">That's it!</span></span> <span data-ttu-id="900ff-133">您已準備好繼續著手進行國際象棋應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="900ff-133">You're all set to move on to starting the chess app project.</span></span>

[<span data-ttu-id="900ff-134">下一節：2.初始化您的專案和第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="900ff-134">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)