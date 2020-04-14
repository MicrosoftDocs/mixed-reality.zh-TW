---
title: 將 XAML 與全像的 DirectX 應用程式搭配使用
description: 說明在 2D XAML 視圖和 DirectX 應用程式中的沉浸式視圖之間切換的影響，以及如何有效率地使用 XAML 視圖和沉浸式視圖。
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: windows mixed reality，UWP，應用程式視圖管理，xaml，鍵盤，逐步解說，DirectX
ms.openlocfilehash: 4136e674cfc1737dba9dcc1f70bd68edd4e95a41
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277956"
---
# <a name="using-xaml-with-holographic-directx-apps"></a><span data-ttu-id="33b0b-104">將 XAML 與全像的 DirectX 應用程式搭配使用</span><span class="sxs-lookup"><span data-stu-id="33b0b-104">Using XAML with holographic DirectX apps</span></span>

<span data-ttu-id="33b0b-105">本主題說明在 DirectX 應用程式中切換[2D XAML 視圖和沉浸式](app-views.md)流覽的影響，以及如何有效率地使用 XAML 視圖和沉浸式視圖。</span><span class="sxs-lookup"><span data-stu-id="33b0b-105">This topic explains the impact of switching between [2D XAML views and immersive views](app-views.md) in your DirectX app, and how to make efficient use of both a XAML view and immersive view.</span></span>

## <a name="xaml-view-switching-overview"></a><span data-ttu-id="33b0b-106">XAML 視圖切換總覽</span><span class="sxs-lookup"><span data-stu-id="33b0b-106">XAML view switching overview</span></span>

<span data-ttu-id="33b0b-107">在 HoloLens 上，通常會顯示 2D XAML 視圖的一般沉浸式應用程式必須先初始化該 XAML 視圖，然後立即從該處切換到沉浸式視圖。</span><span class="sxs-lookup"><span data-stu-id="33b0b-107">On HoloLens, a generally immersive app that may later display a 2D XAML view must initialize that XAML view first and immediately switch to an immersive view from there.</span></span> <span data-ttu-id="33b0b-108">這表示在您的應用程式可以執行任何動作之前，會載入 XAML。</span><span class="sxs-lookup"><span data-stu-id="33b0b-108">This means XAML will load before your app can do anything.</span></span> <span data-ttu-id="33b0b-109">如此一來，啟動時間會變小，而且 XAML 會在應用程式進程位於背景時繼續佔用記憶體空間;啟動延遲和記憶體使用量的數量取決於您的應用程式在切換到原生視圖之前，會如何處理 XAML。</span><span class="sxs-lookup"><span data-stu-id="33b0b-109">As a result, there will be a small increase in your startup time, and XAML will continue to occupy memory space in your app process while it resides in the background; the amount of startup delay and memory usage depends on what your app does with XAML before switching to the native view.</span></span> <span data-ttu-id="33b0b-110">如果您沒有在 XAML 中執行任何動作，請先啟動程式碼，除非開始您的沉浸式視圖，否則影回應該很小。</span><span class="sxs-lookup"><span data-stu-id="33b0b-110">If you do nothing in your XAML start up code at first except start your immersive view, the impact should be minor.</span></span> <span data-ttu-id="33b0b-111">此外，由於您的全像攝影轉譯是直接對沉浸式視圖進行，因此您可以避免任何有關該呈現的 XAML 相關限制。</span><span class="sxs-lookup"><span data-stu-id="33b0b-111">Also, because your holographic rendering is done directly to the immersive view, you will avoid any XAML-related restrictions on that rendering.</span></span>

<span data-ttu-id="33b0b-112">請注意，記憶體使用量會計入 CPU 和 GPU。</span><span class="sxs-lookup"><span data-stu-id="33b0b-112">Note that the memory usage counts for both CPU and GPU.</span></span> <span data-ttu-id="33b0b-113">Direct3D 11 可以交換虛擬圖形記憶體，但它可能無法交換部分或所有的 XAML GPU 資源，而且可能會有明顯的效能影響。</span><span class="sxs-lookup"><span data-stu-id="33b0b-113">Direct3D 11 is able to swap virtual graphics memory, but it might not be able to swap out some or all of the XAML GPU resources, and there might be a noticeable performance hit.</span></span> <span data-ttu-id="33b0b-114">不論是哪一種方式，都不會載入您的應用程式所需的任何 XAML 功能，並提供更好的體驗。</span><span class="sxs-lookup"><span data-stu-id="33b0b-114">Either way, not loading any XAML features you don't need will leave more room for your app and provide a better experience.</span></span>

## <a name="xaml-view-switching-workflow"></a><span data-ttu-id="33b0b-115">XAML 視圖切換工作流程</span><span class="sxs-lookup"><span data-stu-id="33b0b-115">XAML view switching workflow</span></span>

<span data-ttu-id="33b0b-116">直接從 XAML 進入沉浸式模式之應用程式的工作流程，如下所示：</span><span class="sxs-lookup"><span data-stu-id="33b0b-116">The workflow for an app that goes directly from XAML to immersive mode is like so:</span></span>
* <span data-ttu-id="33b0b-117">應用程式會在 2D XAML 視圖中啟動。</span><span class="sxs-lookup"><span data-stu-id="33b0b-117">The app starts up in the 2D XAML view.</span></span>
* <span data-ttu-id="33b0b-118">應用程式的 XAML 啟動順序會偵測目前的系統是否支援全像攝影轉譯：</span><span class="sxs-lookup"><span data-stu-id="33b0b-118">The app’s XAML startup sequence detects if the current system supports holographic rendering:</span></span>
* <span data-ttu-id="33b0b-119">若是如此，應用程式會建立沉浸式視圖，並立即將其帶到前景。</span><span class="sxs-lookup"><span data-stu-id="33b0b-119">If so, the app creates the immersive view and brings it to the foreground right away.</span></span> <span data-ttu-id="33b0b-120">Windows Mixed Reality 裝置上不需要的任何專案都會略過 XAML 載入，包括 XAML 視圖中的任何轉譯類別和資產載入。</span><span class="sxs-lookup"><span data-stu-id="33b0b-120">XAML loading is skipped for anything not necessary on Windows Mixed Reality devices, including any rendering classes and asset loading in the XAML view.</span></span> <span data-ttu-id="33b0b-121">如果應用程式使用 XAML 來進行鍵盤輸入，則仍應建立該輸入頁面。</span><span class="sxs-lookup"><span data-stu-id="33b0b-121">If the app is using XAML for keyboard input, that input page should still be created.</span></span>
* <span data-ttu-id="33b0b-122">如果沒有，XAML 視圖可以照常繼續業務。</span><span class="sxs-lookup"><span data-stu-id="33b0b-122">If not, the XAML view can proceed with business as usual.</span></span>

## <a name="tip-for-rendering-graphics-across-both-views"></a><span data-ttu-id="33b0b-123">跨兩個視圖呈現圖形的秘訣</span><span class="sxs-lookup"><span data-stu-id="33b0b-123">Tip for rendering graphics across both views</span></span>

<span data-ttu-id="33b0b-124">如果您的應用程式需要在 DirectX 中為 Windows Mixed Reality 的 XAML 視圖實行某種程度的轉譯，最好的做法是建立一個可與這兩個視圖搭配使用的轉譯器。</span><span class="sxs-lookup"><span data-stu-id="33b0b-124">If your app needs to implement some amount of rendering in DirectX for the XAML view in Windows Mixed Reality, your best bet is to create one renderer that can work with both views.</span></span> <span data-ttu-id="33b0b-125">轉譯器應該是一個可以從兩個視圖存取的實例，而且應該能夠在2D 和全像攝影轉譯之間切換。</span><span class="sxs-lookup"><span data-stu-id="33b0b-125">The renderer should be one instance that can be accessed from both views, and it should be able to switch between 2D and holographic rendering.</span></span> <span data-ttu-id="33b0b-126">如此一來，就只會載入一次 GPU 資產，這可減少載入時間、記憶體影響，以及切換視圖時要交換的資源量。</span><span class="sxs-lookup"><span data-stu-id="33b0b-126">That way GPU assets are only loaded once - this reduces load times, memory impact, and the amount of resources to be swapped when switching views.</span></span>
