---
title: 使用全像攝影版的 DirectX 應用程式中的 XAML
description: 說明 2D XAML 檢視與您的 DirectX 應用程式，以及如何有效率地使用 [XAML] 檢視和沈浸式檢視中的沈浸式檢視之間切換的影響。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: windows mixed 的 reality，UWP 應用程式檢視管理、 xaml、 鍵盤、 逐步解說中，DirectX
ms.openlocfilehash: 32b2feea0cb6b8aba972c1772451ca7b5b9946d5
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591355"
---
# <a name="using-xaml-with-holographic-directx-apps"></a><span data-ttu-id="6b359-104">使用全像攝影版的 DirectX 應用程式中的 XAML</span><span class="sxs-lookup"><span data-stu-id="6b359-104">Using XAML with holographic DirectX apps</span></span>

<span data-ttu-id="6b359-105">本主題說明切換的影響[2D 的 XAML 檢視和沈浸式檢視](app-views.md)DirectX 應用程式，以及如何有效率地使用 [XAML] 檢視和沈浸式檢視。</span><span class="sxs-lookup"><span data-stu-id="6b359-105">This topic explains the impact of switching between [2D XAML views and immersive views](app-views.md) in your DirectX app, and how to make efficient use of both a XAML view and immersive view.</span></span>

## <a name="xaml-view-switching-overview"></a><span data-ttu-id="6b359-106">XAML 檢視切換概觀</span><span class="sxs-lookup"><span data-stu-id="6b359-106">XAML view switching overview</span></span>

<span data-ttu-id="6b359-107">在 HoloLens，必須先初始化該 XAML 檢視更新的版本可能會顯示 2D 的 XAML 檢視通常沈浸式應用程式，並將其從該處立即切換的沈浸式檢視中。</span><span class="sxs-lookup"><span data-stu-id="6b359-107">On HoloLens, a generally immersive app that may later display a 2D XAML view must initialize that XAML view first and immediately switch to an immersive view from there.</span></span> <span data-ttu-id="6b359-108">這表示您的應用程式可以執行任何動作之前，會載入 XAML。</span><span class="sxs-lookup"><span data-stu-id="6b359-108">This means XAML will load before your app can do anything.</span></span> <span data-ttu-id="6b359-109">如此一來，會有少量增加您的啟動時間，以及 XAML 會繼續佔用您的應用程式處理序中的記憶體空間，而它位於背景;啟動延遲時間和使用方式取決於您的應用程式會使用 XAML 之前切換到原生檢視的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="6b359-109">As a result, there will be a small increase in your startup time, and XAML will continue to occupy memory space in your app process while it resides in the background; the amount of startup delay and memory usage depends on what your app does with XAML before switching to the native view.</span></span> <span data-ttu-id="6b359-110">如果您在程式碼一開始啟動您的沈浸式檢視，只不過您 XAML 開始執行任何動作，影響應該很小。</span><span class="sxs-lookup"><span data-stu-id="6b359-110">If you do nothing in your XAML start up code at first except start your immersive view, the impact should be minor.</span></span> <span data-ttu-id="6b359-111">此外，因為您全像攝影版的轉譯直接為了沈浸式檢視，您可避免該轉譯任何 XAML 相關限制。</span><span class="sxs-lookup"><span data-stu-id="6b359-111">Also, because your holographic rendering is done directly to the immersive view, you will avoid any XAML-related restrictions on that rendering.</span></span>

<span data-ttu-id="6b359-112">請注意，CPU 和 GPU 計算的記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="6b359-112">Note that the memory usage counts for both CPU and GPU.</span></span> <span data-ttu-id="6b359-113">Direct3D 11 是能夠交換虛擬圖形記憶體，它可能無法空出部分或所有 XAML GPU 的資源，但可能會有明顯的效能衝擊。</span><span class="sxs-lookup"><span data-stu-id="6b359-113">Direct3D 11 is able to swap virtual graphics memory, but it might not be able to swap out some or all of the XAML GPU resources, and there might be a noticeable performance hit.</span></span> <span data-ttu-id="6b359-114">無論如何，未載入任何 XAML 功能不需要將保留更多空間給您的應用程式，並提供更好的體驗。</span><span class="sxs-lookup"><span data-stu-id="6b359-114">Either way, not loading any XAML features you don't need will leave more room for your app and provide a better experience.</span></span>

## <a name="xaml-view-switching-workflow"></a><span data-ttu-id="6b359-115">切換工作流程的 XAML 檢視</span><span class="sxs-lookup"><span data-stu-id="6b359-115">XAML view switching workflow</span></span>

<span data-ttu-id="6b359-116">工作流程的應用程式當機時會直接從 XAML 至沈浸式模式，就像這樣：</span><span class="sxs-lookup"><span data-stu-id="6b359-116">The workflow for an app that goes directly from XAML to immersive mode is like so:</span></span>
* <span data-ttu-id="6b359-117">應用程式會啟動在 2D 的 [XAML] 檢視中。</span><span class="sxs-lookup"><span data-stu-id="6b359-117">The app starts up in the 2D XAML view.</span></span>
* <span data-ttu-id="6b359-118">應用程式的 XAML 啟動順序偵測到目前的系統是否支援全像攝影版的轉譯：</span><span class="sxs-lookup"><span data-stu-id="6b359-118">The app’s XAML startup sequence detects if the current system supports holographic rendering:</span></span>
* <span data-ttu-id="6b359-119">若是如此，應用程式建立的沈浸式檢視，並立即將它帶到前景。</span><span class="sxs-lookup"><span data-stu-id="6b359-119">If so, the app creates the immersive view and brings it to the foreground right away.</span></span> <span data-ttu-id="6b359-120">XAML 載入 Windows Mixed Reality 在裝置上，包括任何呈現類別和載入 XAML 檢視中的資產會略過不必要的項目。</span><span class="sxs-lookup"><span data-stu-id="6b359-120">XAML loading is skipped for anything not necessary on Windows Mixed Reality devices, including any rendering classes and asset loading in the XAML view.</span></span> <span data-ttu-id="6b359-121">如果應用程式使用 XAML 的鍵盤輸入，則應該仍會建立該輸入的頁面。</span><span class="sxs-lookup"><span data-stu-id="6b359-121">If the app is using XAML for keyboard input, that input page should still be created.</span></span>
* <span data-ttu-id="6b359-122">如果沒有，則 [XAML] 檢視可以像往常一樣繼續與企業。</span><span class="sxs-lookup"><span data-stu-id="6b359-122">If not, the XAML view can proceed with business as usual.</span></span>

## <a name="tip-for-rendering-graphics-across-both-views"></a><span data-ttu-id="6b359-123">在這兩個檢視提示轉譯圖形</span><span class="sxs-lookup"><span data-stu-id="6b359-123">Tip for rendering graphics across both views</span></span>

<span data-ttu-id="6b359-124">如果您的應用程式需要在 DirectX 中實作一定程度，XAML 檢視中 Windows Mixed Reality，最好是轉譯的建立一個可以使用這兩個檢視的轉譯器。</span><span class="sxs-lookup"><span data-stu-id="6b359-124">If your app needs to implement some amount of rendering in DirectX for the XAML view in Windows Mixed Reality, your best bet is to create one renderer that can work with both views.</span></span> <span data-ttu-id="6b359-125">轉譯器應該是您可以從這兩個檢視中，存取的一個執行個體，它應該能夠轉譯 2D 和全像攝影版之間切換。</span><span class="sxs-lookup"><span data-stu-id="6b359-125">The renderer should be one instance that can be accessed from both views, and it should be able to switch between 2D and holographic rendering.</span></span> <span data-ttu-id="6b359-126">如此一來 GPU 資產只能載入一次-這會減少載入時間、 記憶體衝擊，以及切換檢視時要交換的資源數量。</span><span class="sxs-lookup"><span data-stu-id="6b359-126">That way GPU assets are only loaded once - this reduces load times, memory impact, and the amount of resources to be swapped when switching views.</span></span>
