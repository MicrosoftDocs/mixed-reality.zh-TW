---
title: 在應用程式內購買
description: 混合現實應用程式支援應用程式內購買, 但有一些工作需要進行設定。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 應用程式內購買、hololens
ms.openlocfilehash: bc96893d1777e94295285736982fd9a7167240a4
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515298"
---
# <a name="in-app-purchases"></a><span data-ttu-id="f2e40-104">在應用程式內購買</span><span class="sxs-lookup"><span data-stu-id="f2e40-104">In-app purchases</span></span>

<span data-ttu-id="f2e40-105">HoloLens 支援應用程式內購買, 但有一些工作需要進行設定。</span><span class="sxs-lookup"><span data-stu-id="f2e40-105">In-app purchases are supported in HoloLens, but there is some work to set them up.</span></span>

<span data-ttu-id="f2e40-106">為了利用應用程式購買功能, 您必須:</span><span class="sxs-lookup"><span data-stu-id="f2e40-106">In order to leverage the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="f2e40-107">建立 XAML [2d 視圖](app-views.md)以顯示為平板電腦</span><span class="sxs-lookup"><span data-stu-id="f2e40-107">Create a XAML [2D view](app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="f2e40-108">切換至該位置以啟用放置, 這會離開沉浸式視圖</span><span class="sxs-lookup"><span data-stu-id="f2e40-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="f2e40-109">呼叫 API: await [CurrentApp. RequestProductPurchaseAsync ("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="f2e40-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="f2e40-110">此 API 將會顯示 [內建 Windows OS] 快顯視窗, 其中顯示應用程式內購買名稱、描述和價格。</span><span class="sxs-lookup"><span data-stu-id="f2e40-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="f2e40-111">然後, 使用者可以選擇 [購買選項]。</span><span class="sxs-lookup"><span data-stu-id="f2e40-111">The user can then choose purchase options.</span></span> <span data-ttu-id="f2e40-112">動作完成後, 應用程式將需要呈現 UI, 讓使用者切換回其[沉浸式視圖](app-views.md)。</span><span class="sxs-lookup"><span data-stu-id="f2e40-112">Once the action is completed, the app will need to present UI which allows the user to switch back to its [immersive view](app-views.md).</span></span>

<span data-ttu-id="f2e40-113">針對以桌面為基礎之 Windows Mixed Reality 沉浸式耳機的應用程式, 在呼叫 RequestProductPurchaseAsync API 之前, 不需要手動切換至 XAML 視圖。</span><span class="sxs-lookup"><span data-stu-id="f2e40-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it is not required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
