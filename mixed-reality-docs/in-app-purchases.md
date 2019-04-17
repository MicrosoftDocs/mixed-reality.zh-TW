---
title: 在應用程式內購買
description: 在應用程式內購買支援混合的實境應用程式，還有一些工作，來設定它們。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 在應用程式內購買 hololens
ms.openlocfilehash: bc96893d1777e94295285736982fd9a7167240a4
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595780"
---
# <a name="in-app-purchases"></a><span data-ttu-id="da420-104">在應用程式內購買</span><span class="sxs-lookup"><span data-stu-id="da420-104">In-app purchases</span></span>

<span data-ttu-id="da420-105">HoloLens，支援應用程式內購買，但有一些工作，來設定它們。</span><span class="sxs-lookup"><span data-stu-id="da420-105">In-app purchases are supported in HoloLens, but there is some work to set them up.</span></span>

<span data-ttu-id="da420-106">若要使用中的應用程式購買功能，您必須：</span><span class="sxs-lookup"><span data-stu-id="da420-106">In order to leverage the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="da420-107">建立 XAML [2D 檢視](app-views.md)顯示為靜態圖像</span><span class="sxs-lookup"><span data-stu-id="da420-107">Create a XAML [2D view](app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="da420-108">切換至該啟動離開沈浸式檢視的位置</span><span class="sxs-lookup"><span data-stu-id="da420-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="da420-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="da420-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="da420-110">此 API 會顯示內建 Windows OS 快顯視窗會顯示在應用程式內購買名稱、 描述和價格。</span><span class="sxs-lookup"><span data-stu-id="da420-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="da420-111">接著，使用者可以選擇購買選項。</span><span class="sxs-lookup"><span data-stu-id="da420-111">The user can then choose purchase options.</span></span> <span data-ttu-id="da420-112">完成此動作之後，應用程式都必須顯示 UI 讓使用者切換回其[沈浸式檢視](app-views.md)。</span><span class="sxs-lookup"><span data-stu-id="da420-112">Once the action is completed, the app will need to present UI which allows the user to switch back to its [immersive view](app-views.md).</span></span>

<span data-ttu-id="da420-113">針對以桌面為基礎的 「 Windows Mixed Reality 沈浸式耳機為目標的應用程式，它不需要手動切換到 [XAML] 檢視，然後再呼叫 RequestProductPurchaseAsync API。</span><span class="sxs-lookup"><span data-stu-id="da420-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it is not required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
