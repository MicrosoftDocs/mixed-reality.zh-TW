---
title: 入門教學課程 - 1。 簡介
description: 本課程說明如何使用混合實境工具組 (MRTK) 來建立混合實境應用程式。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 1ba98abe5de14c3e1aaf6164c19d3ca87da341d2
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304858"
---
# <a name="1-introduction"></a><span data-ttu-id="85e12-105">1.簡介</span><span class="sxs-lookup"><span data-stu-id="85e12-105">1. Introduction</span></span>

## <a name="overview"></a><span data-ttu-id="85e12-106">概觀</span><span class="sxs-lookup"><span data-stu-id="85e12-106">Overview</span></span>

<span data-ttu-id="85e12-107">歡迎使用入門教學課程系列！</span><span class="sxs-lookup"><span data-stu-id="85e12-107">Welcome to the Getting Started tutorial series!</span></span> <span data-ttu-id="85e12-108">在這些教學課程中，您將了解混合實境工具組 (MRTK) 及其所提供的一些功能。</span><span class="sxs-lookup"><span data-stu-id="85e12-108">Over the course of these tutorials, you'll learn about the Mixed Reality Toolkit (MRTK) and some of the features it has to offer.</span></span> <span data-ttu-id="85e12-109">您也會建立一個混合實境體驗，讓使用者可以探索模仿 NASA Mars Curiosity Rover (好奇號火星探測車) 的全像投影。</span><span class="sxs-lookup"><span data-stu-id="85e12-109">You'll also build a mixed reality experience where the user can explore a hologram modeled after NASA's Mars Curiosity Rover.</span></span> <span data-ttu-id="85e12-110">在此系列結束時，您將完全了解 MRTK，以及其如何加速您的開發流程。</span><span class="sxs-lookup"><span data-stu-id="85e12-110">By the end of this series, you'll have a firm grasp of MRTK and how it can speed up your development process.</span></span>

<span data-ttu-id="85e12-111">此系列中的教學課程都是連續的，因此請以正確的順序逐一查看：</span><span class="sxs-lookup"><span data-stu-id="85e12-111">Tutorials in this series are meant to be sequential, so please go through them in the correct order:</span></span>

1. [<span data-ttu-id="85e12-112">簡介</span><span class="sxs-lookup"><span data-stu-id="85e12-112">Introduction</span></span>](mr-learning-base-01.md)
2. [<span data-ttu-id="85e12-113">初始化您的專案並部署您的第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="85e12-113">Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
3. [<span data-ttu-id="85e12-114">設定 MRTK 設定檔</span><span class="sxs-lookup"><span data-stu-id="85e12-114">Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
4. [<span data-ttu-id="85e12-115">將物件置放在場景中</span><span class="sxs-lookup"><span data-stu-id="85e12-115">Positioning objects in the scene</span></span>](mr-learning-base-04.md)
5. [<span data-ttu-id="85e12-116">使用解析器建立動態內容</span><span class="sxs-lookup"><span data-stu-id="85e12-116">Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
6. [<span data-ttu-id="85e12-117">建立使用者介面</span><span class="sxs-lookup"><span data-stu-id="85e12-117">Creating user interfaces</span></span>](mr-learning-base-06.md)
7. [<span data-ttu-id="85e12-118">與 3D 物件互動</span><span class="sxs-lookup"><span data-stu-id="85e12-118">Interacting with 3D objects</span></span>](mr-learning-base-07.md)
8. [<span data-ttu-id="85e12-119">使用眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="85e12-119">Using eye-tracking</span></span>](mr-learning-base-08.md)
9. [<span data-ttu-id="85e12-120">使用語音命令</span><span class="sxs-lookup"><span data-stu-id="85e12-120">Using voice commands</span></span>](mr-learning-base-09.md)

## <a name="objectives"></a><span data-ttu-id="85e12-121">目標</span><span class="sxs-lookup"><span data-stu-id="85e12-121">Objectives</span></span>

* <span data-ttu-id="85e12-122">了解如何為 MRTK 設定 Unity</span><span class="sxs-lookup"><span data-stu-id="85e12-122">Learn how to configure Unity for MRTK</span></span>
* <span data-ttu-id="85e12-123">了解如何在您的裝置上建置和部署</span><span class="sxs-lookup"><span data-stu-id="85e12-123">Learn how to build and deploy to your device</span></span>
* <span data-ttu-id="85e12-124">了解如何使用 MRTK 的重要功能</span><span class="sxs-lookup"><span data-stu-id="85e12-124">Learn how to use some of MRTK's key features</span></span>
* <span data-ttu-id="85e12-125">建立完整的混合實境體驗</span><span class="sxs-lookup"><span data-stu-id="85e12-125">Create a complete mixed reality experience</span></span>

## <a name="prerequisites"></a><span data-ttu-id="85e12-126">必要條件</span><span class="sxs-lookup"><span data-stu-id="85e12-126">Prerequisites</span></span>

* <span data-ttu-id="85e12-127">已[安裝正確工具](install-the-tools.md)的 Windows 10 電腦</span><span class="sxs-lookup"><span data-stu-id="85e12-127">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="85e12-128">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 或更新版本</span><span class="sxs-lookup"><span data-stu-id="85e12-128">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 or later</span></span>
* <span data-ttu-id="85e12-129">已[針對開發而設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置</span><span class="sxs-lookup"><span data-stu-id="85e12-129">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="85e12-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，已安裝 Unity 2019.3.15，且已新增通用 Windows 平台組建支援模組</span><span class="sxs-lookup"><span data-stu-id="85e12-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="85e12-131">本教學課程系列的建議 MRTK 版本是 MRTK 2.4.0。</span><span class="sxs-lookup"><span data-stu-id="85e12-131">The recommended MRTK version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="85e12-132">本教學課程系列的建議 Unity 版本是 Unity 2019.3.15。</span><span class="sxs-lookup"><span data-stu-id="85e12-132">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="85e12-133">這個版本能取代上述連結必要條件中所述的任何 Unity 版本需求。</span><span class="sxs-lookup"><span data-stu-id="85e12-133">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="85e12-134">下一個教學課程：2.初始化您的專案並部署您的第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="85e12-134">Next Tutorial: 2. Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
