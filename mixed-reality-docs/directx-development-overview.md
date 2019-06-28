---
title: DirectX 開發概觀
description: 建置以 DirectX 為基礎的混合的實境引擎直接使用 Windows Mixed Reality Api。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX，全像攝影版轉譯，原生、 原生應用程式，WinRT，WinRT 應用程式中，平台 Api、 自訂引擎中, 介軟體
ms.openlocfilehash: da6beae6e256fef49481b581395e507b3f2acd04
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414378"
---
# <a name="directx-development-overview"></a><span data-ttu-id="148a7-104">DirectX 開發概觀</span><span class="sxs-lookup"><span data-stu-id="148a7-104">DirectX development overview</span></span>


<span data-ttu-id="148a7-105">使用 Windows Mixed Reality 應用程式[全像攝影版的轉譯](rendering.md)，[視線](gaze.md)，[筆勢](gestures.md)，[動作控制器](motion-controllers.md)， [語音](voice-input.md)，並[空間的對應](spatial-mapping.md)Api 建置[混合實境](mixed-reality.md)HoloLens 和耳機沉浸式體驗。</span><span class="sxs-lookup"><span data-stu-id="148a7-105">Windows Mixed Reality applications use the [holographic rendering](rendering.md), [gaze](gaze.md), [gesture](gestures.md), [motion controller](motion-controllers.md), [voice](voice-input.md), and [spatial mapping](spatial-mapping.md) APIs to build [mixed reality](mixed-reality.md) experiences for HoloLens and immersive headsets.</span></span> <span data-ttu-id="148a7-106">您可以建立混合的實境應用程式使用的 3D 的引擎，例如[Unity](unity-development-overview.md)，或您可以直接撰寫程式碼使用 DirectX 11 或 DirectX 12 Windows Mixed Reality api。</span><span class="sxs-lookup"><span data-stu-id="148a7-106">You can create mixed reality applications using a 3D engine, such as [Unity](unity-development-overview.md), or you can directly code to the Windows Mixed Reality APIs using DirectX 11 or DirectX 12.</span></span> <span data-ttu-id="148a7-107">如果您直接利用平台，您將實質上建置您自己的中介軟體或架構。</span><span class="sxs-lookup"><span data-stu-id="148a7-107">If you are leveraging the platform directly, you'll essentially be building your own middleware or framework.</span></span> <span data-ttu-id="148a7-108">Windows Api 支援在撰寫的應用程式C++和C#。</span><span class="sxs-lookup"><span data-stu-id="148a7-108">The Windows APIs support applications written in both C++ and C#.</span></span> <span data-ttu-id="148a7-109">如果您選擇使用C#，您的應用程式可以利用[SharpDX](http://sharpdx.org/)開放原始碼軟體程式庫。</span><span class="sxs-lookup"><span data-stu-id="148a7-109">If you choose to use C#, your application can leverage the [SharpDX](http://sharpdx.org/) open source software library.</span></span>


<span data-ttu-id="148a7-110">支援 Windows Mixed Reality[應用程式的兩種](app-views.md):</span><span class="sxs-lookup"><span data-stu-id="148a7-110">Windows Mixed Reality supports [two kinds of apps](app-views.md):</span></span>
* <span data-ttu-id="148a7-111">**混合實境應用程式**（UWP 或 Win32），使用[HolographicSpace API](getting-a-holographicspace.md)呈現[沈浸式檢視](app-views.md)填滿耳機顯示的使用者。</span><span class="sxs-lookup"><span data-stu-id="148a7-111">**Mixed reality applications** (UWP or Win32) that use the [HolographicSpace API](getting-a-holographicspace.md) to render an [immersive view](app-views.md) to the user that fills the headset display.</span></span>
* <span data-ttu-id="148a7-112">**2D 應用程式**(UWP)，使用 DirectX、 XAML 或其他架構來呈現[2D 檢視](app-views.md#2d-views)在家用的 Windows Mixed Reality 平板上。</span><span class="sxs-lookup"><span data-stu-id="148a7-112">**2D apps** (UWP) that use DirectX, XAML, or other frameworks to render [2D views](app-views.md#2d-views) on slates in the Windows Mixed Reality home.</span></span>


<span data-ttu-id="148a7-113">適用於 DirectX 開發之間的差異[2D 檢視和沈浸式檢視](app-views.md)主要是以全像攝影版相關的轉譯和空間的輸入。</span><span class="sxs-lookup"><span data-stu-id="148a7-113">The differences between DirectX development for [2D views and immersive views](app-views.md) are primarily related to holographic rendering and spatial input.</span></span> <span data-ttu-id="148a7-114">您的 UWP 應用程式[IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx)或 Win32 應用程式的 HWND 是必要的並會保留主要相同，為執行應用程式可用的 WinRT Api。</span><span class="sxs-lookup"><span data-stu-id="148a7-114">Your UWP application's [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) or your Win32 application's HWND are required, and remain largely the same, as do the WinRT APIs available to your application.</span></span> <span data-ttu-id="148a7-115">不過，您必須使用這些 Api 的不同子集，以善用全像攝影版的功能。</span><span class="sxs-lookup"><span data-stu-id="148a7-115">However, you must use a different subset of these APIs to take advantage of holographic features.</span></span> <span data-ttu-id="148a7-116">比方說，交換鏈結由全像攝影版 appslications 的系統管理。</span><span class="sxs-lookup"><span data-stu-id="148a7-116">For example, the swap chain is managed by the system for holographic appslications.</span></span> <span data-ttu-id="148a7-117">您使用 HolographicSpace API，而不是 DXGI[呈現畫面格](rendering-in-directx.md)。</span><span class="sxs-lookup"><span data-stu-id="148a7-117">You work with the HolographicSpace API rather than DXGI to [present frames](rendering-in-directx.md).</span></span>

<span data-ttu-id="148a7-118">若要開始開發沉浸式應用程式：</span><span class="sxs-lookup"><span data-stu-id="148a7-118">To begin developing immersive applications:</span></span>
* <span data-ttu-id="148a7-119">針對**UWP 應用程式**，[建立新的 UWP 專案使用 Visual Studio 中的範本](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="148a7-119">For **UWP apps**, [create a new UWP project using the templates in Visual Studio](creating-a-holographic-directx-project.md).</span></span> <span data-ttu-id="148a7-120">根據您的語言**Visual C++** 或**視覺化C#** ，您可以找到下的 UWP 範本**Windows 通用** >  **全像攝影版**。</span><span class="sxs-lookup"><span data-stu-id="148a7-120">Based on your language, **Visual C++** or **Visual C#**, you can find the UWP templates under **Windows Universal** > **Holographic**.</span></span>
* <span data-ttu-id="148a7-121">針對**Win32 應用程式**，[從開始*BasicHologram* Win32 範例](creating-a-holographic-directx-project.md#creating-a-win32-project)。</span><span class="sxs-lookup"><span data-stu-id="148a7-121">For **Win32 applications**, [start from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project).</span></span>

<span data-ttu-id="148a7-122">這是適合用來取得您需要將全像攝影版的呈現支援新增至現有的應用程式或引擎的程式碼。</span><span class="sxs-lookup"><span data-stu-id="148a7-122">This is a great way to get the code that you need to add holographic rendering support to an existing application or engine.</span></span> <span data-ttu-id="148a7-123">程式碼和概念會在範本中的即時互動式軟體的任何開發人員熟悉的方式。</span><span class="sxs-lookup"><span data-stu-id="148a7-123">Code and concepts are presented in the template in a way that's familiar to any developer of real-time interactive software.</span></span>


## <a name="getting-started"></a><span data-ttu-id="148a7-124">使用者入門</span><span class="sxs-lookup"><span data-stu-id="148a7-124">Getting started</span></span>

<span data-ttu-id="148a7-125">下列主題將討論 Windows Mixed Reality 支援加入以 DirectX 為基礎的中介軟體的基本需求：</span><span class="sxs-lookup"><span data-stu-id="148a7-125">The following topics discuss the base requirements of adding Windows Mixed Reality support to DirectX-based middleware:</span></span>

* <span data-ttu-id="148a7-126">[建立全像攝影版的 DirectX 專案](creating-a-holographic-directx-project.md):搭配文件的全像攝影版的應用程式範本會顯示您要用來與裝置，設計成函式時將滑鼠停在頭上導入的特殊需求之間的差異。</span><span class="sxs-lookup"><span data-stu-id="148a7-126">[Creating a holographic DirectX project](creating-a-holographic-directx-project.md): The holographic application template coupled with the documentation shows you the differences between what you're used to as well as the special requirements introduced by a device that's designed to function while resting on your head.</span></span>
* <span data-ttu-id="148a7-127">[取得 HolographicSpace](getting-a-holographicspace.md):您必須先建立將提供您的應用程式的 HolographicFrame 代表物件，從中您將轉譯的每個前端位置順序 HolographicSpace。</span><span class="sxs-lookup"><span data-stu-id="148a7-127">[Getting a HolographicSpace](getting-a-holographicspace.md): You'll first need to create a HolographicSpace That will provide your application the sequence of HolographicFrame objects that represent each head position from which you'll render.</span></span>
* <span data-ttu-id="148a7-128">[在 DirectX 中呈現](rendering-in-directx.md):因為全像攝影版的交換鏈結都有兩個呈現目標，您必須對您的應用程式呈現的方式進行一些變更。</span><span class="sxs-lookup"><span data-stu-id="148a7-128">[Rendering in DirectX](rendering-in-directx.md): Since a holographic swap chain has two render targets, you'll need to make some changes to the way your application renders.</span></span>
* <span data-ttu-id="148a7-129">[DirectX 中的座標系統](coordinate-systems-in-directx.md):Windows Mixed Reality 學習，並更新其了解世界隨著使用者周圍。</span><span class="sxs-lookup"><span data-stu-id="148a7-129">[Coordinate systems in DirectX](coordinate-systems-in-directx.md): Windows Mixed Reality learns and updates its understanding of the world as the user walks around.</span></span> <span data-ttu-id="148a7-130">這會提供空間座標系統應用程式會使用有關使用者的周圍環境，包括空間的錨點的原因，以及使用者定義的空間的階段。</span><span class="sxs-lookup"><span data-stu-id="148a7-130">This provides spatial coordinate systems that applications use to reason about the user's surroundings, including spatial anchors and the user's defined spatial stage.</span></span>

## <a name="adding-mixed-reality-capabilities-and-inputs"></a><span data-ttu-id="148a7-131">新增混合的實境功能和輸入</span><span class="sxs-lookup"><span data-stu-id="148a7-131">Adding mixed reality capabilities and inputs</span></span>

<span data-ttu-id="148a7-132">若要啟用您的沈浸式 appslication 的使用者最佳體驗，您會想要支援下列的主要建置組塊：</span><span class="sxs-lookup"><span data-stu-id="148a7-132">To enable the best possible experience for users of your immersive appslication, you'll want to support the following key building blocks:</span></span>

* [<span data-ttu-id="148a7-133">DirectX 中的頭部和眼睛目光</span><span class="sxs-lookup"><span data-stu-id="148a7-133">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="148a7-134">DirectX 中的手部和運動控制器</span><span class="sxs-lookup"><span data-stu-id="148a7-134">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="148a7-135">DirectX 中的語音輸入</span><span class="sxs-lookup"><span data-stu-id="148a7-135">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="148a7-136">DirectX 中的空間音效</span><span class="sxs-lookup"><span data-stu-id="148a7-136">Spatial sound in DirectX</span></span>](spatial-sound-in-directx.md)
* [<span data-ttu-id="148a7-137">DirectX 中的空間對應</span><span class="sxs-lookup"><span data-stu-id="148a7-137">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)


<span data-ttu-id="148a7-138">有其他重要功能，許多的沈浸式應用程式會想要使用的 DirectX 應用程式也會公開：</span><span class="sxs-lookup"><span data-stu-id="148a7-138">There are other key features that many immersive applications will want to use that are also exposed to DirectX applicaitons:</span></span>

* [<span data-ttu-id="148a7-139">DirectX 中的共用空間錨點</span><span class="sxs-lookup"><span data-stu-id="148a7-139">Shared spatial anchors in DirectX</span></span>](shared-spatial-anchors-in-directx.md)
* [<span data-ttu-id="148a7-140">DirectX 中的定位相機</span><span class="sxs-lookup"><span data-stu-id="148a7-140">Locatable camera in DirectX</span></span>](locatable-camera-in-directx.md)
* [<span data-ttu-id="148a7-141">DirectX 中的鍵盤、滑鼠及控制器輸入</span><span class="sxs-lookup"><span data-stu-id="148a7-141">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a><span data-ttu-id="148a7-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="148a7-142">See also</span></span>
* [<span data-ttu-id="148a7-143">應用程式模型</span><span class="sxs-lookup"><span data-stu-id="148a7-143">App model</span></span>](app-model.md)
* [<span data-ttu-id="148a7-144">應用程式檢視</span><span class="sxs-lookup"><span data-stu-id="148a7-144">App views</span></span>](app-views.md)
