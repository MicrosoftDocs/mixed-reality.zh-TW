---
title: DirectX 開發總覽
description: 直接使用 Windows Mixed Reality Api 建立以 DirectX 為基礎的混合現實引擎。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX, 全像攝影轉譯, 原生, 原生應用程式, WinRT, WinRT 應用程式, 平臺 Api, 自訂引擎, 中介軟體
ms.openlocfilehash: 58b311038633dc325cc2c5425fd09b9a0192b161
ms.sourcegitcommit: 4ac761fed7a9570977f6d031ba4f870585d6630a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68861700"
---
# <a name="directx-development-overview"></a><span data-ttu-id="e47a8-104">DirectX 開發總覽</span><span class="sxs-lookup"><span data-stu-id="e47a8-104">DirectX development overview</span></span>


<span data-ttu-id="e47a8-105">Windows Mixed Reality 應用程式使用[全像攝影轉譯](rendering.md)、[注視](gaze.md)、[手勢](gestures.md)、[運動控制器](motion-controllers.md)、[語音](voice-input.md)和[空間對應](spatial-mapping.md)api 來打造 HoloLens 的[混合現實](mixed-reality.md)體驗, 以及沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="e47a8-105">Windows Mixed Reality applications use the [holographic rendering](rendering.md), [gaze](gaze.md), [gesture](gestures.md), [motion controller](motion-controllers.md), [voice](voice-input.md), and [spatial mapping](spatial-mapping.md) APIs to build [mixed reality](mixed-reality.md) experiences for HoloLens and immersive headsets.</span></span> <span data-ttu-id="e47a8-106">您可以使用3D 引擎 (例如[Unity](unity-development-overview.md)) 來建立混合現實應用程式, 也可以使用 directx 11 或 directx 12 直接對 Windows Mixed reality api 進行程式碼撰寫。</span><span class="sxs-lookup"><span data-stu-id="e47a8-106">You can create mixed reality applications using a 3D engine, such as [Unity](unity-development-overview.md), or you can directly code to the Windows Mixed Reality APIs using DirectX 11 or DirectX 12.</span></span> <span data-ttu-id="e47a8-107">如果您直接運用平臺, 基本上就是建立自己的中介軟體或架構。</span><span class="sxs-lookup"><span data-stu-id="e47a8-107">If you are leveraging the platform directly, you'll essentially be building your own middleware or framework.</span></span> <span data-ttu-id="e47a8-108">Windows Api 支援以C++和C#撰寫的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e47a8-108">The Windows APIs support applications written in both C++ and C#.</span></span> <span data-ttu-id="e47a8-109">如果您選擇使用C#, 您的應用程式可以運用[SharpDX](http://sharpdx.org/)開放原始碼軟體程式庫。</span><span class="sxs-lookup"><span data-stu-id="e47a8-109">If you choose to use C#, your application can leverage the [SharpDX](http://sharpdx.org/) open source software library.</span></span>


<span data-ttu-id="e47a8-110">Windows Mixed Reality 支援[兩種類型的應用程式](app-views.md):</span><span class="sxs-lookup"><span data-stu-id="e47a8-110">Windows Mixed Reality supports [two kinds of apps](app-views.md):</span></span>
* <span data-ttu-id="e47a8-111">**混合現實應用程式**(UWP 或 Win32), 使用[HOLOGRAPHICSPACE API](getting-a-holographicspace.md)向使用者呈現可填滿頭戴式裝置顯示器的[沉浸式視圖](app-views.md)。</span><span class="sxs-lookup"><span data-stu-id="e47a8-111">**Mixed reality applications** (UWP or Win32) that use the [HolographicSpace API](getting-a-holographicspace.md) to render an [immersive view](app-views.md) to the user that fills the headset display.</span></span>
* <span data-ttu-id="e47a8-112">**2d 應用程式**(UWP) 使用 DirectX、XAML 或其他架構在 Windows Mixed Reality home 的平板上轉譯[2d views](app-views.md#2d-views) 。</span><span class="sxs-lookup"><span data-stu-id="e47a8-112">**2D apps** (UWP) that use DirectX, XAML, or other frameworks to render [2D views](app-views.md#2d-views) on slates in the Windows Mixed Reality home.</span></span>


<span data-ttu-id="e47a8-113">[2d 視圖和沉浸式視圖](app-views.md)的 DirectX 開發之間的差異主要與全像攝影轉譯和空間輸入有關。</span><span class="sxs-lookup"><span data-stu-id="e47a8-113">The differences between DirectX development for [2D views and immersive views](app-views.md) are primarily related to holographic rendering and spatial input.</span></span> <span data-ttu-id="e47a8-114">您的 UWP 應用程式的[IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx)或 Win32 應用程式的 HWND 是必要的, 而且與您的應用程式可使用的 WinRT api 一樣, 也會維持不變。</span><span class="sxs-lookup"><span data-stu-id="e47a8-114">Your UWP application's [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) or your Win32 application's HWND are required, and remain largely the same, as do the WinRT APIs available to your application.</span></span> <span data-ttu-id="e47a8-115">不過, 您必須使用這些 Api 的不同子集, 才能利用全像攝影功能。</span><span class="sxs-lookup"><span data-stu-id="e47a8-115">However, you must use a different subset of these APIs to take advantage of holographic features.</span></span> <span data-ttu-id="e47a8-116">例如, 交換鏈會由系統管理, 以進行全像攝影 appslications。</span><span class="sxs-lookup"><span data-stu-id="e47a8-116">For example, the swap chain is managed by the system for holographic appslications.</span></span> <span data-ttu-id="e47a8-117">您可以使用 HolographicSpace API, 而不是 DXGI 來[呈現畫面](rendering-in-directx.md)格。</span><span class="sxs-lookup"><span data-stu-id="e47a8-117">You work with the HolographicSpace API rather than DXGI to [present frames](rendering-in-directx.md).</span></span>

<span data-ttu-id="e47a8-118">若要開始開發沉浸式應用程式:</span><span class="sxs-lookup"><span data-stu-id="e47a8-118">To begin developing immersive applications:</span></span>
* <span data-ttu-id="e47a8-119">針對**UWP 應用程式**, 請[使用 Visual Studio 中的範本來建立新的 UWP 專案](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="e47a8-119">For **UWP apps**, [create a new UWP project using the templates in Visual Studio](creating-a-holographic-directx-project.md).</span></span> <span data-ttu-id="e47a8-120">根據您的語言、**視覺C++效果**或**視覺效果C#** , 您可以在 **Windows 通用** > 全像攝影底下找到 UWP 範本。</span><span class="sxs-lookup"><span data-stu-id="e47a8-120">Based on your language, **Visual C++** or **Visual C#**, you can find the UWP templates under **Windows Universal** > **Holographic**.</span></span>
* <span data-ttu-id="e47a8-121">針對**win32 應用程式**, 請[從*BasicHologram* Win32 範例開始](creating-a-holographic-directx-project.md#creating-a-win32-project)。</span><span class="sxs-lookup"><span data-stu-id="e47a8-121">For **Win32 applications**, [start from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project).</span></span>

<span data-ttu-id="e47a8-122">這是取得在現有應用程式或引擎中新增全像攝影轉譯支援所需程式碼的絕佳方式。</span><span class="sxs-lookup"><span data-stu-id="e47a8-122">This is a great way to get the code that you need to add holographic rendering support to an existing application or engine.</span></span> <span data-ttu-id="e47a8-123">程式碼和概念在範本中的呈現方式, 對於即時互動式軟體的任何開發人員而言都很熟悉。</span><span class="sxs-lookup"><span data-stu-id="e47a8-123">Code and concepts are presented in the template in a way that's familiar to any developer of real-time interactive software.</span></span>


## <a name="getting-started"></a><span data-ttu-id="e47a8-124">使用者入門</span><span class="sxs-lookup"><span data-stu-id="e47a8-124">Getting started</span></span>

<span data-ttu-id="e47a8-125">下列主題討論將 Windows Mixed Reality 支援新增至以 DirectX 為基礎的中介軟體的基本需求:</span><span class="sxs-lookup"><span data-stu-id="e47a8-125">The following topics discuss the base requirements of adding Windows Mixed Reality support to DirectX-based middleware:</span></span>

* <span data-ttu-id="e47a8-126">[建立全像製作的 DirectX 專案](creating-a-holographic-directx-project.md):與檔結合的全像攝影應用程式範本, 會顯示您所使用的差異, 以及裝置在離開前端時所引進的特殊需求。</span><span class="sxs-lookup"><span data-stu-id="e47a8-126">[Creating a holographic DirectX project](creating-a-holographic-directx-project.md): The holographic application template coupled with the documentation shows you the differences between what you're used to as well as the special requirements introduced by a device that's designed to function while resting on your head.</span></span>
* <span data-ttu-id="e47a8-127">[取得 HolographicSpace](getting-a-holographicspace.md):您必須先建立 HolographicSpace, 以提供應用程式 HolographicFrame 物件的順序, 代表您將呈現的每個標頭位置。</span><span class="sxs-lookup"><span data-stu-id="e47a8-127">[Getting a HolographicSpace](getting-a-holographicspace.md): You'll first need to create a HolographicSpace That will provide your application the sequence of HolographicFrame objects that represent each head position from which you'll render.</span></span>
* <span data-ttu-id="e47a8-128">[在 DirectX 中](rendering-in-directx.md)轉譯:因為全像攝影交換鏈有兩個轉譯目標, 所以您必須對應用程式轉譯的方式進行一些變更。</span><span class="sxs-lookup"><span data-stu-id="e47a8-128">[Rendering in DirectX](rendering-in-directx.md): Since a holographic swap chain has two render targets, you'll need to make some changes to the way your application renders.</span></span>
* <span data-ttu-id="e47a8-129">[在 DirectX 中協調系統](coordinate-systems-in-directx.md):Windows Mixed Reality 會在使用者逐步解說的同時, 學習並更新對世界的瞭解。</span><span class="sxs-lookup"><span data-stu-id="e47a8-129">[Coordinate systems in DirectX](coordinate-systems-in-directx.md): Windows Mixed Reality learns and updates its understanding of the world as the user walks around.</span></span> <span data-ttu-id="e47a8-130">這會提供應用程式使用的空間座標系統, 以因應使用者的周圍的原因, 包括空間錨點和使用者定義的空間階段。</span><span class="sxs-lookup"><span data-stu-id="e47a8-130">This provides spatial coordinate systems that applications use to reason about the user's surroundings, including spatial anchors and the user's defined spatial stage.</span></span>

## <a name="adding-mixed-reality-capabilities-and-inputs"></a><span data-ttu-id="e47a8-131">新增混合現實功能和輸入</span><span class="sxs-lookup"><span data-stu-id="e47a8-131">Adding mixed reality capabilities and inputs</span></span>

<span data-ttu-id="e47a8-132">若要為您的沉浸式 appslication 使用者提供最佳的體驗, 您會想要支援下列重要的建立區塊:</span><span class="sxs-lookup"><span data-stu-id="e47a8-132">To enable the best possible experience for users of your immersive appslication, you'll want to support the following key building blocks:</span></span>

* [<span data-ttu-id="e47a8-133">DirectX 中的頭部和眼睛目光</span><span class="sxs-lookup"><span data-stu-id="e47a8-133">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="e47a8-134">DirectX 中的手部和運動控制器</span><span class="sxs-lookup"><span data-stu-id="e47a8-134">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="e47a8-135">DirectX 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="e47a8-135">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="e47a8-136">DirectX 中的空間音效</span><span class="sxs-lookup"><span data-stu-id="e47a8-136">Spatial sound in DirectX</span></span>](spatial-sound-in-directx.md)
* [<span data-ttu-id="e47a8-137">DirectX 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="e47a8-137">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)


<span data-ttu-id="e47a8-138">還有許多沉浸式應用程式會想要使用的重要功能, 也會公開給 DirectX 應用程式:</span><span class="sxs-lookup"><span data-stu-id="e47a8-138">There are other key features that many immersive applications will want to use that are also exposed to DirectX applicaitons:</span></span>

* [<span data-ttu-id="e47a8-139">DirectX 中的共用空間錨點</span><span class="sxs-lookup"><span data-stu-id="e47a8-139">Shared spatial anchors in DirectX</span></span>](shared-spatial-anchors-in-directx.md)
* [<span data-ttu-id="e47a8-140">DirectX 中的鍵盤、滑鼠及控制器輸入</span><span class="sxs-lookup"><span data-stu-id="e47a8-140">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a><span data-ttu-id="e47a8-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e47a8-141">See also</span></span>
* [<span data-ttu-id="e47a8-142">應用程式模型</span><span class="sxs-lookup"><span data-stu-id="e47a8-142">App model</span></span>](app-model.md)
* [<span data-ttu-id="e47a8-143">應用程式檢視</span><span class="sxs-lookup"><span data-stu-id="e47a8-143">App views</span></span>](app-views.md)
