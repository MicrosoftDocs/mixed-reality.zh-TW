---
title: 1. 開始使用
description: 教學課程的第 1 部分，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置簡單的國際象棋應用程式
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件
ms.openlocfilehash: 3ca47cfe7bb0a733932f3777cc8b531ef9df8e71
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840127"
---
# <a name="1-getting-started"></a><span data-ttu-id="a36b6-104">1.開始使用</span><span class="sxs-lookup"><span data-stu-id="a36b6-104">1. Getting started</span></span>

<span data-ttu-id="a36b6-105">這是逐步教學課程，將會示範如何使用 Unreal Engine 4 來建置互動式 HoloLens 2 國際象棋應用程式。</span><span class="sxs-lookup"><span data-stu-id="a36b6-105">This is a step by step tutorial that will show you how to build an interactive HoloLens 2 chess app using Unreal Engine 4.</span></span> <span data-ttu-id="a36b6-106">您也將了解如何使用適用於 Unreal 的混合實境工具組中的 UX 工具外掛程式來加速開發。</span><span class="sxs-lookup"><span data-stu-id="a36b6-106">You will also learn how to use the UX Tools plugin from the Mixed Reality Toolkit for Unreal to speed up development.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="a36b6-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="a36b6-107">Prerequisites</span></span>

* <span data-ttu-id="a36b6-108">Windows 10 1809 或更新版本</span><span class="sxs-lookup"><span data-stu-id="a36b6-108">Windows 10 1809 or later</span></span>
* <span data-ttu-id="a36b6-109">Windows 10 SDK 10.0.18362.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="a36b6-109">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="a36b6-110">Unreal Engine 4.25 或更新版本</span><span class="sxs-lookup"><span data-stu-id="a36b6-110">Unreal Engine 4.25 or later</span></span>
* <span data-ttu-id="a36b6-111">[針對開發而設定](using-visual-studio.md#enabling-developer-mode)的 Microsoft HoloLens 2 裝置或模擬器</span><span class="sxs-lookup"><span data-stu-id="a36b6-111">Microsoft HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode) or Emulator</span></span>
* <span data-ttu-id="a36b6-112">Visual Studio 2019 (具有下列工作負載和元件)</span><span class="sxs-lookup"><span data-stu-id="a36b6-112">Visual Studio 2019 (with below workloads and components)</span></span>

### <a name="installing-visual-studio-2019-workloads-and-components"></a><span data-ttu-id="a36b6-113">安裝 Visual Studio 2019、工作負載和元件</span><span class="sxs-lookup"><span data-stu-id="a36b6-113">Installing Visual Studio 2019, workloads, and components</span></span>
1. <span data-ttu-id="a36b6-114">安裝和更新至最新版的 Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="a36b6-114">Install or and update to the latest version of Visual Studio 2019</span></span>
* [<span data-ttu-id="a36b6-115">下載 Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="a36b6-115">Download Visual Studio 2019</span></span>](https://visualstudio.microsoft.com/downloads/)
2. <span data-ttu-id="a36b6-116">安裝下列工作負載：</span><span class="sxs-lookup"><span data-stu-id="a36b6-116">Install the following workloads:</span></span>
* <span data-ttu-id="a36b6-117">使用 C++ 的傳統型開發</span><span class="sxs-lookup"><span data-stu-id="a36b6-117">Desktop development with C++</span></span>
* <span data-ttu-id="a36b6-118">.NET 桌面開發</span><span class="sxs-lookup"><span data-stu-id="a36b6-118">.NET desktop development</span></span>
* <span data-ttu-id="a36b6-119">通用 Windows 平台開發</span><span class="sxs-lookup"><span data-stu-id="a36b6-119">Universal Windows Platform development</span></span>
3. <span data-ttu-id="a36b6-120">安裝下列個別元件：</span><span class="sxs-lookup"><span data-stu-id="a36b6-120">Install the following individual components:</span></span>
* <span data-ttu-id="a36b6-121">編譯器、建置工具與執行階段 > MSVC v142 - VS 2019 C++ ARM64 建置工具 (最新版本)</span><span class="sxs-lookup"><span data-stu-id="a36b6-121">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

[<span data-ttu-id="a36b6-122">下一節：2.初始化您的專案和第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="a36b6-122">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)