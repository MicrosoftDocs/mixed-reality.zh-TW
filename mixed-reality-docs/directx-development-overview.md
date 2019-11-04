---
title: DirectX 開發總覽
description: 直接使用 Windows Mixed Reality Api 建立 DirectX 為基礎的混合現實引擎。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX，全像攝影轉譯，原生，原生應用程式，WinRT，WinRT 應用程式，平臺 Api，自訂引擎，中介軟體
ms.openlocfilehash: 698ccb57a39189b9c0634c47ad6cbd6325c06caa
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435583"
---
# <a name="directx-development-overview"></a><span data-ttu-id="8e291-104">DirectX 開發總覽</span><span class="sxs-lookup"><span data-stu-id="8e291-104">DirectX development overview</span></span>


<span data-ttu-id="8e291-105">Windows Mixed Reality 應用程式使用全像攝影[轉譯、](rendering.md)[注視](gaze-and-commit.md)、[手勢](gaze-and-commit.md#composite-gestures)、[運動控制器](motion-controllers.md)、[語音](voice-input.md)和[空間對應](spatial-mapping.md)api 來打造 HoloLens 的[混合現實](mixed-reality.md)體驗，以及沉浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="8e291-105">Windows Mixed Reality applications use the [holographic rendering](rendering.md), [gaze](gaze-and-commit.md), [gesture](gaze-and-commit.md#composite-gestures), [motion controller](motion-controllers.md), [voice](voice-input.md), and [spatial mapping](spatial-mapping.md) APIs to build [mixed reality](mixed-reality.md) experiences for HoloLens and immersive headsets.</span></span> <span data-ttu-id="8e291-106">您可以使用3D 引擎（例如[Unity](unity-development-overview.md)）來建立混合現實應用程式，也可以使用 directx 11 或 directx 12 直接對 Windows Mixed reality api 進行程式碼撰寫。</span><span class="sxs-lookup"><span data-stu-id="8e291-106">You can create mixed reality applications using a 3D engine, such as [Unity](unity-development-overview.md), or you can directly code to the Windows Mixed Reality APIs using DirectX 11 or DirectX 12.</span></span> <span data-ttu-id="8e291-107">如果您直接運用平臺，基本上就是建立自己的中介軟體或架構。</span><span class="sxs-lookup"><span data-stu-id="8e291-107">If you are leveraging the platform directly, you'll essentially be building your own middleware or framework.</span></span> <span data-ttu-id="8e291-108">Windows Api 支援以C++和C#撰寫的應用程式。</span><span class="sxs-lookup"><span data-stu-id="8e291-108">The Windows APIs support applications written in both C++ and C#.</span></span> <span data-ttu-id="8e291-109">如果您選擇使用C#，您的應用程式可以運用[SharpDX](https://sharpdx.org/)開放原始碼軟體程式庫。</span><span class="sxs-lookup"><span data-stu-id="8e291-109">If you choose to use C#, your application can leverage the [SharpDX](https://sharpdx.org/) open source software library.</span></span>


<span data-ttu-id="8e291-110">Windows Mixed Reality 支援[兩種類型的應用程式](app-views.md)：</span><span class="sxs-lookup"><span data-stu-id="8e291-110">Windows Mixed Reality supports [two kinds of apps](app-views.md):</span></span>
* <span data-ttu-id="8e291-111">**混合現實應用程式**（UWP 或 Win32），使用[HolographicSpace API](getting-a-holographicspace.md)將[沉浸式視圖](app-views.md)呈現給填滿耳機顯示的使用者。</span><span class="sxs-lookup"><span data-stu-id="8e291-111">**Mixed reality applications** (UWP or Win32) that use the [HolographicSpace API](getting-a-holographicspace.md) to render an [immersive view](app-views.md) to the user that fills the headset display.</span></span>
* <span data-ttu-id="8e291-112">使用 DirectX、XAML 或其他架構的**2d 應用程式**（UWP），以在 Windows Mixed Reality 首頁的平板上轉譯[2d views](app-views.md#2d-views) 。</span><span class="sxs-lookup"><span data-stu-id="8e291-112">**2D apps** (UWP) that use DirectX, XAML, or other frameworks to render [2D views](app-views.md#2d-views) on slates in the Windows Mixed Reality home.</span></span>


<span data-ttu-id="8e291-113">[2d 視圖和沉浸式視圖](app-views.md)的 DirectX 開發之間的差異主要與全像攝影轉譯和空間輸入有關。</span><span class="sxs-lookup"><span data-stu-id="8e291-113">The differences between DirectX development for [2D views and immersive views](app-views.md) are primarily related to holographic rendering and spatial input.</span></span> <span data-ttu-id="8e291-114">您的 UWP 應用程式的[IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx)或 Win32 應用程式的 HWND 是必要的，而且與您的應用程式可使用的 WinRT api 一樣，也會維持不變。</span><span class="sxs-lookup"><span data-stu-id="8e291-114">Your UWP application's [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) or your Win32 application's HWND are required, and remain largely the same, as do the WinRT APIs available to your application.</span></span> <span data-ttu-id="8e291-115">不過，您必須使用這些 Api 的不同子集，才能利用全像攝影功能。</span><span class="sxs-lookup"><span data-stu-id="8e291-115">However, you must use a different subset of these APIs to take advantage of holographic features.</span></span> <span data-ttu-id="8e291-116">例如，交換鏈是由全像攝影應用程式的系統所管理。</span><span class="sxs-lookup"><span data-stu-id="8e291-116">For example, the swap chain is managed by the system for holographic applications.</span></span> <span data-ttu-id="8e291-117">您可以使用 HolographicSpace API，而不是 DXGI 來[呈現畫面](rendering-in-directx.md)格。</span><span class="sxs-lookup"><span data-stu-id="8e291-117">You work with the HolographicSpace API rather than DXGI to [present frames](rendering-in-directx.md).</span></span>

<span data-ttu-id="8e291-118">若要開始開發沉浸式應用程式：</span><span class="sxs-lookup"><span data-stu-id="8e291-118">To begin developing immersive applications:</span></span>
* <span data-ttu-id="8e291-119">針對**UWP 應用程式**，請[使用 Visual Studio 中的範本來建立新的 UWP 專案](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="8e291-119">For **UWP apps**, [create a new UWP project using the templates in Visual Studio](creating-a-holographic-directx-project.md).</span></span> <span data-ttu-id="8e291-120">根據您的語言、**視覺C++效果**或**視覺效果C#** ，您可以在**Windows 通用** \*\* > 全\*\*像攝影底下找到 UWP 範本。</span><span class="sxs-lookup"><span data-stu-id="8e291-120">Based on your language, **Visual C++** or **Visual C#**, you can find the UWP templates under **Windows Universal** > **Holographic**.</span></span>
* <span data-ttu-id="8e291-121">針對**win32 應用程式**，請[從*BasicHologram* Win32 範例開始](creating-a-holographic-directx-project.md#creating-a-win32-project)。</span><span class="sxs-lookup"><span data-stu-id="8e291-121">For **Win32 applications**, [start from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project).</span></span>

<span data-ttu-id="8e291-122">這是取得在現有應用程式或引擎中新增全像攝影轉譯支援所需程式碼的絕佳方式。</span><span class="sxs-lookup"><span data-stu-id="8e291-122">This is a great way to get the code that you need to add holographic rendering support to an existing application or engine.</span></span> <span data-ttu-id="8e291-123">程式碼和概念在範本中的呈現方式，對於即時互動式軟體的任何開發人員而言都很熟悉。</span><span class="sxs-lookup"><span data-stu-id="8e291-123">Code and concepts are presented in the template in a way that's familiar to any developer of real-time interactive software.</span></span>


## <a name="getting-started"></a><span data-ttu-id="8e291-124">開始使用</span><span class="sxs-lookup"><span data-stu-id="8e291-124">Getting started</span></span>

<span data-ttu-id="8e291-125">下列主題討論將 Windows Mixed Reality 支援新增至以 DirectX 為基礎的中介軟體的基本需求：</span><span class="sxs-lookup"><span data-stu-id="8e291-125">The following topics discuss the base requirements of adding Windows Mixed Reality support to DirectX-based middleware:</span></span>

* <span data-ttu-id="8e291-126">[建立全像製作的 DirectX 專案](creating-a-holographic-directx-project.md)：全像投影應用程式範本與檔，會顯示您所使用的差異，以及專為運作而設計的裝置所引進的特殊需求停留在您的頭部。</span><span class="sxs-lookup"><span data-stu-id="8e291-126">[Creating a holographic DirectX project](creating-a-holographic-directx-project.md): The holographic application template coupled with the documentation shows you the differences between what you're used to as well as the special requirements introduced by a device that's designed to function while resting on your head.</span></span>
* <span data-ttu-id="8e291-127">[取得 HolographicSpace](getting-a-holographicspace.md)：您必須先建立 HolographicSpace，它會提供應用程式 HolographicFrame 物件的順序，代表您要呈現的每個標頭位置。</span><span class="sxs-lookup"><span data-stu-id="8e291-127">[Getting a HolographicSpace](getting-a-holographicspace.md): You'll first need to create a HolographicSpace that will provide your application the sequence of HolographicFrame objects that represent each head position from which you'll render.</span></span>
* <span data-ttu-id="8e291-128">[在 DirectX 中](rendering-in-directx.md)轉譯：因為全像攝影交換鏈有兩個轉譯目標，所以您必須對應用程式呈現的方式進行一些變更。</span><span class="sxs-lookup"><span data-stu-id="8e291-128">[Rendering in DirectX](rendering-in-directx.md): Since a holographic swap chain has two render targets, you'll need to make some changes to the way your application renders.</span></span>
* <span data-ttu-id="8e291-129">[在 DirectX 中協調系統](coordinate-systems-in-directx.md)： Windows Mixed Reality 會在使用者逐步解說的同時，學習並更新其對世界的瞭解。</span><span class="sxs-lookup"><span data-stu-id="8e291-129">[Coordinate systems in DirectX](coordinate-systems-in-directx.md): Windows Mixed Reality learns and updates its understanding of the world as the user walks around.</span></span> <span data-ttu-id="8e291-130">這會提供應用程式使用的空間座標系統，以因應使用者的周圍的原因，包括空間錨點和使用者定義的空間階段。</span><span class="sxs-lookup"><span data-stu-id="8e291-130">This provides spatial coordinate systems that applications use to reason about the user's surroundings, including spatial anchors and the user's defined spatial stage.</span></span>

## <a name="adding-mixed-reality-capabilities-and-inputs"></a><span data-ttu-id="8e291-131">新增混合現實功能和輸入</span><span class="sxs-lookup"><span data-stu-id="8e291-131">Adding mixed reality capabilities and inputs</span></span>

<span data-ttu-id="8e291-132">若要為您的沉浸式 appslication 使用者提供最佳的體驗，您會想要支援下列重要的建立區塊：</span><span class="sxs-lookup"><span data-stu-id="8e291-132">To enable the best possible experience for users of your immersive appslication, you'll want to support the following key building blocks:</span></span>

* [<span data-ttu-id="8e291-133">DirectX 中的頭部和眼睛目光</span><span class="sxs-lookup"><span data-stu-id="8e291-133">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="8e291-134">DirectX 中的手部和運動控制器</span><span class="sxs-lookup"><span data-stu-id="8e291-134">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="8e291-135">DirectX 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="8e291-135">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="8e291-136">DirectX 中的空間音效</span><span class="sxs-lookup"><span data-stu-id="8e291-136">Spatial sound in DirectX</span></span>](spatial-sound-in-directx.md)
* [<span data-ttu-id="8e291-137">DirectX 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="8e291-137">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)


<span data-ttu-id="8e291-138">還有許多沉浸式應用程式會想要使用的重要功能，也會公開給 DirectX 應用程式：</span><span class="sxs-lookup"><span data-stu-id="8e291-138">There are other key features that many immersive applications will want to use that are also exposed to DirectX applicaitons:</span></span>

* [<span data-ttu-id="8e291-139">DirectX 中的共用空間錨點</span><span class="sxs-lookup"><span data-stu-id="8e291-139">Shared spatial anchors in DirectX</span></span>](shared-spatial-anchors-in-directx.md)
* [<span data-ttu-id="8e291-140">DirectX 中的鍵盤、滑鼠及控制器輸入</span><span class="sxs-lookup"><span data-stu-id="8e291-140">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a><span data-ttu-id="8e291-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="8e291-141">See also</span></span>
* [<span data-ttu-id="8e291-142">應用程式模型</span><span class="sxs-lookup"><span data-stu-id="8e291-142">App model</span></span>](app-model.md)
* [<span data-ttu-id="8e291-143">應用程式檢視</span><span class="sxs-lookup"><span data-stu-id="8e291-143">App views</span></span>](app-views.md)
