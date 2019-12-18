---
title: 原生開發總覽
description: 直接使用 Windows Mixed Reality Api，建立以 DirectX 為基礎的混合現實引擎。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX，全像攝影轉譯，原生，原生應用程式，WinRT，WinRT 應用程式，平臺 Api，自訂引擎，中介軟體
ms.openlocfilehash: 06227b41dde69e6610b151f3b27a3800e76431bd
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181898"
---
# <a name="native-development-overview"></a><span data-ttu-id="e6547-104">原生開發總覽</span><span class="sxs-lookup"><span data-stu-id="e6547-104">Native development overview</span></span>

<span data-ttu-id="e6547-105">Windows Mixed Reality 應用程式使用下列 Api 來打造適用于 HoloLens 和其他沉浸式耳機的[混合現實](mixed-reality.md)體驗：</span><span class="sxs-lookup"><span data-stu-id="e6547-105">Windows Mixed Reality applications use the following APIs to build [mixed-reality](mixed-reality.md) experiences for HoloLens and other immersive headsets:</span></span>

 - [<span data-ttu-id="e6547-106">全像攝影的呈現</span><span class="sxs-lookup"><span data-stu-id="e6547-106">Holographic rendering</span></span>](rendering.md)
 - [<span data-ttu-id="e6547-107">目光</span><span class="sxs-lookup"><span data-stu-id="e6547-107">Gaze</span></span>](gaze-and-commit.md)
 - [<span data-ttu-id="e6547-108">#</span><span class="sxs-lookup"><span data-stu-id="e6547-108">Gesture</span></span>](gaze-and-commit.md#composite-gestures)
 - [<span data-ttu-id="e6547-109">動作控制器</span><span class="sxs-lookup"><span data-stu-id="e6547-109">Motion controller</span></span>](motion-controllers.md)
 - [<span data-ttu-id="e6547-110">語音</span><span class="sxs-lookup"><span data-stu-id="e6547-110">Voice</span></span>](voice-input.md)
 - [<span data-ttu-id="e6547-111">空間對應</span><span class="sxs-lookup"><span data-stu-id="e6547-111">Spatial mapping</span></span>](spatial-mapping.md)

<span data-ttu-id="e6547-112">您可以使用3D 引擎（例如[Unity](unity-development-overview.md)）來建立混合現實應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6547-112">You can create mixed reality applications by using a 3D engine, such as [Unity](unity-development-overview.md).</span></span> <span data-ttu-id="e6547-113">或者，您可以使用 DirectX 11 或 DirectX 12，直接將程式碼撰寫到 Windows Mixed Reality Api。</span><span class="sxs-lookup"><span data-stu-id="e6547-113">Or you can directly code to the Windows Mixed Reality APIs by using DirectX 11 or DirectX 12.</span></span> <span data-ttu-id="e6547-114">如果您直接運用平臺，基本上就是建立自己的中介軟體或架構。</span><span class="sxs-lookup"><span data-stu-id="e6547-114">If you leverage the platform directly, you essentially build your own middleware or framework.</span></span> <span data-ttu-id="e6547-115">Windows Api 支援以C++和C#撰寫的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6547-115">The Windows APIs support applications that are written in both C++ and C#.</span></span> <span data-ttu-id="e6547-116">如果您使用C#，您的應用程式可以運用[SharpDX](https://sharpdx.org/)開放原始碼軟體程式庫。</span><span class="sxs-lookup"><span data-stu-id="e6547-116">If you use C#, your application can leverage the [SharpDX](https://sharpdx.org/) open source software library.</span></span>

<span data-ttu-id="e6547-117">Windows Mixed Reality 支援[兩種類型的應用程式](app-views.md)：</span><span class="sxs-lookup"><span data-stu-id="e6547-117">Windows Mixed Reality supports [two kinds of apps](app-views.md):</span></span>
* <span data-ttu-id="e6547-118">**混合現實應用程式**（UWP 或 Win32），使用[HolographicSpace API](getting-a-holographicspace.md)將[沉浸式視圖](app-views.md)呈現給填滿耳機顯示的使用者</span><span class="sxs-lookup"><span data-stu-id="e6547-118">**Mixed-reality applications** (UWP or Win32) that use the [HolographicSpace API](getting-a-holographicspace.md) to render an [immersive view](app-views.md) to the user that fills the headset display</span></span>
* <span data-ttu-id="e6547-119">使用 DirectX、XAML 或其他架構的**2d 應用程式**（UWP），在 Windows Mixed Reality 首頁的平板上呈現[2d 視圖](app-views.md#2d-views)</span><span class="sxs-lookup"><span data-stu-id="e6547-119">**2D apps** (UWP) that use DirectX, XAML, or another framework to render [2D views](app-views.md#2d-views) on slates in the Windows Mixed Reality home</span></span>

<span data-ttu-id="e6547-120">[2d 視圖和沉浸式視圖](app-views.md)的 DirectX 開發之間的差異主要涉及全像攝影轉譯和空間輸入。</span><span class="sxs-lookup"><span data-stu-id="e6547-120">The differences between DirectX development for [2D views and immersive views](app-views.md) primarily concern holographic rendering and spatial input.</span></span> <span data-ttu-id="e6547-121">您的 UWP 應用程式的[IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx)或 Win32 應用程式的 HWND 是必要的，而且兩者的存留程度都相同。</span><span class="sxs-lookup"><span data-stu-id="e6547-121">Your UWP application's [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) or your Win32 application's HWND are required and remain largely the same.</span></span> <span data-ttu-id="e6547-122">適用于您應用程式的 WinRT Api 也是如此。</span><span class="sxs-lookup"><span data-stu-id="e6547-122">The same is true for the WinRT APIs that are available to your app.</span></span> <span data-ttu-id="e6547-123">但您必須使用這些 Api 的不同子集，才能利用全像攝影功能。</span><span class="sxs-lookup"><span data-stu-id="e6547-123">But you must use a different subset of these APIs to take advantage of holographic features.</span></span> <span data-ttu-id="e6547-124">例如，交換鏈是由全像攝影應用程式的系統所管理。</span><span class="sxs-lookup"><span data-stu-id="e6547-124">For example, the swap chain is managed by the system for holographic applications.</span></span> <span data-ttu-id="e6547-125">而且您會使用 HolographicSpace API，而不是 DXGI 來[呈現畫面](rendering-in-directx.md)格。</span><span class="sxs-lookup"><span data-stu-id="e6547-125">And you use the HolographicSpace API rather than DXGI to [present frames](rendering-in-directx.md).</span></span>

<span data-ttu-id="e6547-126">若要開始開發沉浸式應用程式：</span><span class="sxs-lookup"><span data-stu-id="e6547-126">To begin developing immersive applications:</span></span>
* <span data-ttu-id="e6547-127">針對**UWP 應用程式**，請[使用 Visual Studio 中的範本來建立新的 uwp 專案](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="e6547-127">For **UWP apps**, [use the templates in Visual Studio to create a new UWP project](creating-a-holographic-directx-project.md).</span></span> <span data-ttu-id="e6547-128">根據您的語言、視覺C++效果或C#視覺效果，尋找**Windows 通用** > 全像攝影**版中的**UWP 範本。</span><span class="sxs-lookup"><span data-stu-id="e6547-128">Based on your language, Visual C++ or Visual C#, find the UWP templates under **Windows Universal** > **Holographic**.</span></span>
* <span data-ttu-id="e6547-129">針對**win32 應用程式**，請[從*BasicHologram* Win32 範例開始](creating-a-holographic-directx-project.md#creating-a-win32-project)。</span><span class="sxs-lookup"><span data-stu-id="e6547-129">For **Win32 applications**, [start from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project).</span></span>

<span data-ttu-id="e6547-130">這個步驟很適合用來取得您所需的程式碼，以便將全像攝影轉譯支援新增至現有的應用程式或引擎。</span><span class="sxs-lookup"><span data-stu-id="e6547-130">This step is a great way to get the code that you need to add holographic rendering support to an existing application or engine.</span></span> <span data-ttu-id="e6547-131">程式碼和概念在範本中的呈現方式，對任何即時互動式軟體發展人員而言都很熟悉。</span><span class="sxs-lookup"><span data-stu-id="e6547-131">The code and concepts are presented in the template in a way that's familiar to any developer of real-time interactive software.</span></span>

## <a name="get-started"></a><span data-ttu-id="e6547-132">入門</span><span class="sxs-lookup"><span data-stu-id="e6547-132">Get started</span></span>

<span data-ttu-id="e6547-133">下列主題說明當您將 Windows Mixed Reality 支援新增至以 DirectX 為基礎的中介軟體時的基本需求。</span><span class="sxs-lookup"><span data-stu-id="e6547-133">The following topics describe the base requirements when you add Windows Mixed Reality support to DirectX-based middleware.</span></span>

* <span data-ttu-id="e6547-134">建立全像的[DirectX 專案](creating-a-holographic-directx-project.md)：與檔結合的全像攝影應用程式範本會顯示與您習慣的差異。</span><span class="sxs-lookup"><span data-stu-id="e6547-134">[Create a holographic DirectX project](creating-a-holographic-directx-project.md): The holographic application template coupled with the documentation shows the differences compared to what you're used to.</span></span> <span data-ttu-id="e6547-135">它也會描述裝置的特殊需求，而此裝置的設計可在您的前端上運作。</span><span class="sxs-lookup"><span data-stu-id="e6547-135">It also describes the special requirements for a device that's designed to function while resting on your head.</span></span>
* <span data-ttu-id="e6547-136">[取得 HolographicSpace](getting-a-holographicspace.md)：您必須先建立 HolographicSpace，為應用程式提供一系列 HolographicFrame 物件，代表您將呈現的每個標頭位置。</span><span class="sxs-lookup"><span data-stu-id="e6547-136">[Get a HolographicSpace](getting-a-holographicspace.md): You first need to create a HolographicSpace that gives your application the sequence of HolographicFrame objects that represent each head position from which you'll render.</span></span>
* <span data-ttu-id="e6547-137">[在 DirectX 中](rendering-in-directx.md)轉譯：因為全像攝影交換鏈有兩個轉譯目標，所以您必須對應用程式轉譯的方式進行一些變更。</span><span class="sxs-lookup"><span data-stu-id="e6547-137">[Render in DirectX](rendering-in-directx.md): Because a holographic swap chain has two render targets, you must make some changes to the way your app renders.</span></span>
* <span data-ttu-id="e6547-138">[在 DirectX 中協調系統](coordinate-systems-in-directx.md)： Windows Mixed Reality 會在使用者逐步解說的同時，學習並更新其對世界的瞭解。</span><span class="sxs-lookup"><span data-stu-id="e6547-138">[Coordinate systems in DirectX](coordinate-systems-in-directx.md): Windows Mixed Reality learns and updates its understanding of the world as the user walks around.</span></span> <span data-ttu-id="e6547-139">這會提供應用程式使用的空間座標系統，以因應使用者的周圍的原因，包括空間錨點和使用者定義的空間階段。</span><span class="sxs-lookup"><span data-stu-id="e6547-139">This provides spatial coordinate systems that applications use to reason about the user's surroundings, including spatial anchors and the user's defined spatial stage.</span></span>

## <a name="add-mixed-reality-capabilities-and-inputs"></a><span data-ttu-id="e6547-140">新增混合現實功能和輸入</span><span class="sxs-lookup"><span data-stu-id="e6547-140">Add mixed reality capabilities and inputs</span></span>

<span data-ttu-id="e6547-141">若要為您的沉浸式應用程式使用者提供最佳的體驗，您應該支援下列重要的建立區塊：</span><span class="sxs-lookup"><span data-stu-id="e6547-141">To provide the best possible experience for users of your immersive app, you should support the following key building blocks:</span></span>

* [<span data-ttu-id="e6547-142">DirectX 中的頭部和眼睛目光</span><span class="sxs-lookup"><span data-stu-id="e6547-142">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="e6547-143">DirectX 中的手部和運動控制器</span><span class="sxs-lookup"><span data-stu-id="e6547-143">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="e6547-144">DirectX 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="e6547-144">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="e6547-145">空間音效</span><span class="sxs-lookup"><span data-stu-id="e6547-145">Spatial sound</span></span>](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)
* [<span data-ttu-id="e6547-146">DirectX 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="e6547-146">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)

<span data-ttu-id="e6547-147">這些是許多沉浸式應用程式所使用的其他重要功能，也會公開給 DirectX 應用程式：</span><span class="sxs-lookup"><span data-stu-id="e6547-147">These are other key features that many immersive applications use that are also exposed to DirectX applications:</span></span>

* [<span data-ttu-id="e6547-148">DirectX 中的共用空間錨點</span><span class="sxs-lookup"><span data-stu-id="e6547-148">Shared spatial anchors in DirectX</span></span>](shared-spatial-anchors-in-directx.md)
* [<span data-ttu-id="e6547-149">DirectX 中的鍵盤、滑鼠及控制器輸入</span><span class="sxs-lookup"><span data-stu-id="e6547-149">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard-mouse-and-controller-input-in-directx.md)

## <a name="see-also"></a><span data-ttu-id="e6547-150">請參閱</span><span class="sxs-lookup"><span data-stu-id="e6547-150">See also</span></span>
* [<span data-ttu-id="e6547-151">應用程式模型</span><span class="sxs-lookup"><span data-stu-id="e6547-151">App model</span></span>](app-model.md)
* [<span data-ttu-id="e6547-152">應用程式檢視</span><span class="sxs-lookup"><span data-stu-id="e6547-152">App views</span></span>](app-views.md)
