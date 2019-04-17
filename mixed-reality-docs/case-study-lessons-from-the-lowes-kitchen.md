---
title: 案例研究-從 Lowe 廚房的課程
description: HoloLens 小組想要分享一些衍生自 Lowe 的 HoloLens 專案的最佳作法。
author: BrandonBray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、 Lowe 的、 HoloLens、 廚房、 案例研究
ms.openlocfilehash: 24759f90b8b84ec19e644fb8dff44f64c3ab81d2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591751"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a><span data-ttu-id="793c3-104">案例研究-從 Lowe 廚房的課程</span><span class="sxs-lookup"><span data-stu-id="793c3-104">Case study - Lessons from the Lowe's kitchen</span></span>

<span data-ttu-id="793c3-105">HoloLens 小組想要分享一些衍生自 Lowe 的 HoloLens 專案的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="793c3-105">The HoloLens team wants to share some of the best practices that were derived from the Lowe's HoloLens project.</span></span> <span data-ttu-id="793c3-106">下面 Lowe 的 HoloLens 投射的影片示範了在 Satya 的 2016 Ignite 重點演說中。</span><span class="sxs-lookup"><span data-stu-id="793c3-106">Below is a video of the Lowe's HoloLens projected demonstrated at Satya's 2016 Ignite keynote.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a><span data-ttu-id="793c3-107">Lowe 的 HoloLens 最佳做法</span><span class="sxs-lookup"><span data-stu-id="793c3-107">Lowe's HoloLens Best Practices</span></span>

<span data-ttu-id="793c3-108">兩段影片討論的衍生自具有兩個 Lowe 存放區中已自 2016 年 4 月的 Lowe 的 HoloLens 試驗的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="793c3-108">The two videos cover best practices that were derived from the Lowe's HoloLens Pilot that has been in two Lowe's stores since April 2016.</span></span> <span data-ttu-id="793c3-109">索引鍵的主題包括：</span><span class="sxs-lookup"><span data-stu-id="793c3-109">The key topics are:</span></span>
* <span data-ttu-id="793c3-110">將行動裝置的效能最大化</span><span class="sxs-lookup"><span data-stu-id="793c3-110">Maximize performance for a mobile device</span></span>
* <span data-ttu-id="793c3-111">使用完整全像攝影版的畫面格建立 UX 方法 (第 2 個 talk)</span><span class="sxs-lookup"><span data-stu-id="793c3-111">Create UX methods with a full holographic frame (2nd talk)</span></span>
* <span data-ttu-id="793c3-112">有效位數的對齊方式 (第 2 個 talk)</span><span class="sxs-lookup"><span data-stu-id="793c3-112">Precision alignment (2nd talk)</span></span>
* <span data-ttu-id="793c3-113">共用全像攝影版的體驗 (第 2 個 talk)</span><span class="sxs-lookup"><span data-stu-id="793c3-113">Shared holographic experiences (2nd talk)</span></span>
* <span data-ttu-id="793c3-114">與客戶互動 (第 2 個 talk)</span><span class="sxs-lookup"><span data-stu-id="793c3-114">Interacting with customers (2nd talk)</span></span>

## <a name="video-1"></a><span data-ttu-id="793c3-115">影片 1</span><span class="sxs-lookup"><span data-stu-id="793c3-115">Video 1</span></span>

<span data-ttu-id="793c3-116">**將行動裝置的效能最大化**HoloLens 是 untethered 的裝置將會在裝置的所有處理。</span><span class="sxs-lookup"><span data-stu-id="793c3-116">**Maximize performance for a mobile device** HoloLens is an untethered device with all the processing taking place in the device.</span></span> <span data-ttu-id="793c3-117">這需要的行動平台，而且需要一種心態類似於建立行動應用程式。</span><span class="sxs-lookup"><span data-stu-id="793c3-117">This requires a mobile platform and requires a mindset similar to creating mobile applications.</span></span> <span data-ttu-id="793c3-118">Microsoft 建議您 HoloLens 的應用程式維持 60 FPS 美味的體驗提供您的使用者。</span><span class="sxs-lookup"><span data-stu-id="793c3-118">Microsoft recommends that your HoloLens application maintain 60FPS to provide a delicious experience for your users.</span></span> <span data-ttu-id="793c3-119">由低 FPS，可能會造成不穩定全像投影。</span><span class="sxs-lookup"><span data-stu-id="793c3-119">Having low FPS can result in unstable holograms.</span></span>

<span data-ttu-id="793c3-120">一些最重要的是，要看看當 HoloLens 上進行開發時資產最佳化/減去，使用自訂著色器 (免費提供[HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity))。</span><span class="sxs-lookup"><span data-stu-id="793c3-120">Some of the most important things to look at when developing on HoloLens is asset optimization/decimation, using custom shaders (available for free in the [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)).</span></span> <span data-ttu-id="793c3-121">另一個重要考量是專案的測量從您一開始的畫面播放速率。</span><span class="sxs-lookup"><span data-stu-id="793c3-121">Another important consideration is to measure the frame rate from the very beginning of your project.</span></span> <span data-ttu-id="793c3-122">根據專案中，顯示您的資產的順序也可以是大型的參與者</span><span class="sxs-lookup"><span data-stu-id="793c3-122">Depending on the project, the order of displaying your assets can also be a big contributor</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a><span data-ttu-id="793c3-123">影片 2</span><span class="sxs-lookup"><span data-stu-id="793c3-123">Video 2</span></span>

<span data-ttu-id="793c3-124">**使用完整全像攝影版的畫面格建立 UX 方法**務必要了解全像投影在真實世界中的位置。</span><span class="sxs-lookup"><span data-stu-id="793c3-124">**Create UX methods with a full holographic frame** It's important to understand the placement of holograms in a physical world.</span></span> <span data-ttu-id="793c3-125">使用 Lowe 的討論不同的 UX 方法可協助的使用者註冊體驗全像投影關閉之際，仍然全像投影的較大的環境。</span><span class="sxs-lookup"><span data-stu-id="793c3-125">With Lowe's we talk about different UX methods that help users experience holograms up close while still seeing the larger environment of holograms.</span></span>

<span data-ttu-id="793c3-126">**有效位數對齊**如 Lowe 的案例中，它是最重要的體驗必須實體廚房的全像投影的有效位數對齊方式。</span><span class="sxs-lookup"><span data-stu-id="793c3-126">**Precision alignment** For the Lowe's scenario, it was paramount to the experience to have precision alignment of the holograms to the physical kitchen.</span></span> <span data-ttu-id="793c3-127">我們會討論可協助確保說服他們的實體環境已變更的使用者經驗的技術。</span><span class="sxs-lookup"><span data-stu-id="793c3-127">We discuss techniques helps ensure an experience that convinces users that their physical environment has changed.</span></span>

<span data-ttu-id="793c3-128">**共用全像攝影版的體驗**會結合是 Lowe 的經驗取用的主要方式。</span><span class="sxs-lookup"><span data-stu-id="793c3-128">**Shared holographic experiences** Couples are the primary way that the Lowe's experience is consumed.</span></span> <span data-ttu-id="793c3-129">一個人可以變更檯面，另一個人會看到所做的變更。</span><span class="sxs-lookup"><span data-stu-id="793c3-129">One person can change the countertop and the other person will see the changes.</span></span> <span data-ttu-id="793c3-130">我們會呼叫這個 「 共用體驗 」。</span><span class="sxs-lookup"><span data-stu-id="793c3-130">We called this "shared experiences".</span></span>

<span data-ttu-id="793c3-131">**與客戶互動**Lowe 的設計工具不使用 HoloLens，但他們需要看到客戶會看到。</span><span class="sxs-lookup"><span data-stu-id="793c3-131">**Interacting with customers** Lowe's designers are not using a HoloLens, but they need to see what the customers are seeing.</span></span> <span data-ttu-id="793c3-132">我們會示範如何擷取客戶會看到在 UWP 應用程式。</span><span class="sxs-lookup"><span data-stu-id="793c3-132">We show how to capture what the customer is seeing on a UWP application.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
