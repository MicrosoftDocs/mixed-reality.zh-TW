---
title: 案例研究-Lowe 廚房的課程
description: HoloLens 小組想要分享一些衍生自 Lowe 的 HoloLens 專案的最佳作法。
author: BrandonBray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Lowe, HoloLens, 廚房, 個案研究
ms.openlocfilehash: 24759f90b8b84ec19e644fb8dff44f64c3ab81d2
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522340"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a><span data-ttu-id="d0fa3-104">案例研究-Lowe 廚房的課程</span><span class="sxs-lookup"><span data-stu-id="d0fa3-104">Case study - Lessons from the Lowe's kitchen</span></span>

<span data-ttu-id="d0fa3-105">HoloLens 小組想要分享一些衍生自 Lowe 的 HoloLens 專案的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="d0fa3-105">The HoloLens team wants to share some of the best practices that were derived from the Lowe's HoloLens project.</span></span> <span data-ttu-id="d0fa3-106">以下是 Lowe 的 HoloLens 投影影片, 示範于 Satya 的 2016 Ignite 專題主題。</span><span class="sxs-lookup"><span data-stu-id="d0fa3-106">Below is a video of the Lowe's HoloLens projected demonstrated at Satya's 2016 Ignite keynote.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a><span data-ttu-id="d0fa3-107">Lowe 的 HoloLens 最佳做法</span><span class="sxs-lookup"><span data-stu-id="d0fa3-107">Lowe's HoloLens Best Practices</span></span>

<span data-ttu-id="d0fa3-108">這兩段影片涵蓋的最佳作法是衍生自 Lowe 的 HoloLens 試驗, 這是從2016年4月起在兩個 Lowe 的商店中。</span><span class="sxs-lookup"><span data-stu-id="d0fa3-108">The two videos cover best practices that were derived from the Lowe's HoloLens Pilot that has been in two Lowe's stores since April 2016.</span></span> <span data-ttu-id="d0fa3-109">主要主題如下:</span><span class="sxs-lookup"><span data-stu-id="d0fa3-109">The key topics are:</span></span>
* <span data-ttu-id="d0fa3-110">最大化行動裝置的效能</span><span class="sxs-lookup"><span data-stu-id="d0fa3-110">Maximize performance for a mobile device</span></span>
* <span data-ttu-id="d0fa3-111">建立具有完整全像攝影畫面的 UX 方法 (第二個說話)</span><span class="sxs-lookup"><span data-stu-id="d0fa3-111">Create UX methods with a full holographic frame (2nd talk)</span></span>
* <span data-ttu-id="d0fa3-112">精確度對齊 (第二次交談)</span><span class="sxs-lookup"><span data-stu-id="d0fa3-112">Precision alignment (2nd talk)</span></span>
* <span data-ttu-id="d0fa3-113">共用的全像攝影體驗 (第二談)</span><span class="sxs-lookup"><span data-stu-id="d0fa3-113">Shared holographic experiences (2nd talk)</span></span>
* <span data-ttu-id="d0fa3-114">與客戶互動 (第二談)</span><span class="sxs-lookup"><span data-stu-id="d0fa3-114">Interacting with customers (2nd talk)</span></span>

## <a name="video-1"></a><span data-ttu-id="d0fa3-115">影片1</span><span class="sxs-lookup"><span data-stu-id="d0fa3-115">Video 1</span></span>

<span data-ttu-id="d0fa3-116">**最大化行動裝置的效能**HoloLens 是非網路共用裝置, 在裝置中進行所有處理。</span><span class="sxs-lookup"><span data-stu-id="d0fa3-116">**Maximize performance for a mobile device** HoloLens is an untethered device with all the processing taking place in the device.</span></span> <span data-ttu-id="d0fa3-117">這需要行動平臺, 而且需要類似于建立行動應用程式的思維方式。</span><span class="sxs-lookup"><span data-stu-id="d0fa3-117">This requires a mobile platform and requires a mindset similar to creating mobile applications.</span></span> <span data-ttu-id="d0fa3-118">Microsoft 建議您的 HoloLens 應用程式維護 60FPS, 為您的使用者提供美味體驗。</span><span class="sxs-lookup"><span data-stu-id="d0fa3-118">Microsoft recommends that your HoloLens application maintain 60FPS to provide a delicious experience for your users.</span></span> <span data-ttu-id="d0fa3-119">具有低 FPS 會導致不穩定的全息影像。</span><span class="sxs-lookup"><span data-stu-id="d0fa3-119">Having low FPS can result in unstable holograms.</span></span>

<span data-ttu-id="d0fa3-120">使用自訂著色器 (可在[Hololens 工具](https://github.com/Microsoft/HoloToolkit-Unity)組中免費取得), 在 HoloLens 上進行開發時, 應查看的一些最重要的事項是資產優化/減去。</span><span class="sxs-lookup"><span data-stu-id="d0fa3-120">Some of the most important things to look at when developing on HoloLens is asset optimization/decimation, using custom shaders (available for free in the [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)).</span></span> <span data-ttu-id="d0fa3-121">另一個重要的考慮是從專案的一開始測量畫面播放速率。</span><span class="sxs-lookup"><span data-stu-id="d0fa3-121">Another important consideration is to measure the frame rate from the very beginning of your project.</span></span> <span data-ttu-id="d0fa3-122">視專案而定, 顯示資產的順序也可能是一個很大的參與者</span><span class="sxs-lookup"><span data-stu-id="d0fa3-122">Depending on the project, the order of displaying your assets can also be a big contributor</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a><span data-ttu-id="d0fa3-123">影片2</span><span class="sxs-lookup"><span data-stu-id="d0fa3-123">Video 2</span></span>

<span data-ttu-id="d0fa3-124">**建立具有完整全像攝影畫面的 UX 方法**請務必瞭解在實體世界中的全息影像位置。</span><span class="sxs-lookup"><span data-stu-id="d0fa3-124">**Create UX methods with a full holographic frame** It's important to understand the placement of holograms in a physical world.</span></span> <span data-ttu-id="d0fa3-125">在 Lowe 中, 我們討論了各種不同的 UX 方法, 可協助使用者體驗清理, 同時仍然看到最大的全息影像環境。</span><span class="sxs-lookup"><span data-stu-id="d0fa3-125">With Lowe's we talk about different UX methods that help users experience holograms up close while still seeing the larger environment of holograms.</span></span>

<span data-ttu-id="d0fa3-126">**精確度對齊**在 Lowe 的案例中, 最重要的是將全息的全像投影至實體廚房的體驗。</span><span class="sxs-lookup"><span data-stu-id="d0fa3-126">**Precision alignment** For the Lowe's scenario, it was paramount to the experience to have precision alignment of the holograms to the physical kitchen.</span></span> <span data-ttu-id="d0fa3-127">我們會討論一些技術, 協助確保說服使用者實體環境已變更的經驗。</span><span class="sxs-lookup"><span data-stu-id="d0fa3-127">We discuss techniques helps ensure an experience that convinces users that their physical environment has changed.</span></span>

<span data-ttu-id="d0fa3-128">**共用**的全像攝影體驗「耦合」是使用 Lowe 體驗的主要方式。</span><span class="sxs-lookup"><span data-stu-id="d0fa3-128">**Shared holographic experiences** Couples are the primary way that the Lowe's experience is consumed.</span></span> <span data-ttu-id="d0fa3-129">一個人可以變更檯面, 而另一人會看到變更。</span><span class="sxs-lookup"><span data-stu-id="d0fa3-129">One person can change the countertop and the other person will see the changes.</span></span> <span data-ttu-id="d0fa3-130">我們稱之為「共用體驗」。</span><span class="sxs-lookup"><span data-stu-id="d0fa3-130">We called this "shared experiences".</span></span>

<span data-ttu-id="d0fa3-131">**與客戶互動**Lowe 的設計人員不會使用 HoloLens, 但需要查看客戶看到的內容。</span><span class="sxs-lookup"><span data-stu-id="d0fa3-131">**Interacting with customers** Lowe's designers are not using a HoloLens, but they need to see what the customers are seeing.</span></span> <span data-ttu-id="d0fa3-132">我們會示範如何在 UWP 應用程式上捕捉客戶看到的內容。</span><span class="sxs-lookup"><span data-stu-id="d0fa3-132">We show how to capture what the customer is seeing on a UWP application.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
