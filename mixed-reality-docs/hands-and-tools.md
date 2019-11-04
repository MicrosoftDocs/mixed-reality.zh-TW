---
title: 實習和運動控制器
description: 實習與運動控制器互動的總覽
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: Mixed Reality，實習，運動控制器，互動，設計
ms.openlocfilehash: 395862fe987244e2af70bb6794caa91e243cd076
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435180"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="668c3-104">實習和運動控制器</span><span class="sxs-lookup"><span data-stu-id="668c3-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="668c3-105">案例</span><span class="sxs-lookup"><span data-stu-id="668c3-105">Scenarios</span></span>
<span data-ttu-id="668c3-106">如果您在閱讀[互動總覽](interaction-fundamentals.md)之後選擇採用此互動模型，就表示您正在開發的應用程式需要使用者使用兩個手來與全像攝影世界互動。</span><span class="sxs-lookup"><span data-stu-id="668c3-106">If you choose to adopt this interaction model after reading the [interaction overview](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="668c3-107">您的應用程式即將達到移除虛擬與實體之間界限的目標。</span><span class="sxs-lookup"><span data-stu-id="668c3-107">Your application is going to achieve the goal of removing the boundary between virtual and physical.</span></span>

<span data-ttu-id="668c3-108">某些特定案例可能是：</span><span class="sxs-lookup"><span data-stu-id="668c3-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="668c3-109">為資訊工作者提供2D 虛擬畫面與 UI affordances，以顯示和控制內容</span><span class="sxs-lookup"><span data-stu-id="668c3-109">Providing information workers 2D virtual screens with UI affordances to display and control content</span></span>
* <span data-ttu-id="668c3-110">提供 factory 元件線的第一行工作者教學課程和指南</span><span class="sxs-lookup"><span data-stu-id="668c3-110">Providing first line workers tutorials and guides for factory assembly lines</span></span>
* <span data-ttu-id="668c3-111">開發專業工具來協助及教育醫療專業人員</span><span class="sxs-lookup"><span data-stu-id="668c3-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="668c3-112">使用3D 虛擬物件裝飾真實世界或建立第二個世界</span><span class="sxs-lookup"><span data-stu-id="668c3-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="668c3-113">使用真實世界作為背景來建立位置服務和遊戲</span><span class="sxs-lookup"><span data-stu-id="668c3-113">Creating location based services and games using the real world as a background</span></span>

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="668c3-114">實習和運動控制器形式</span><span class="sxs-lookup"><span data-stu-id="668c3-114">Hands and motion controllers modalities</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="668c3-115">[使用手 ![直接操作](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span><span class="sxs-lookup"><span data-stu-id="668c3-115">[![Direct manipulation with hands](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span></span><br>
       ### <a name="direct-manipulation-with-handsdirect-manipulationmdbr"></a>[<span data-ttu-id="668c3-116">手部直接操作</span><span class="sxs-lookup"><span data-stu-id="668c3-116">Direct manipulation with hands</span></span>](direct-manipulation.md)<br>
       <span data-ttu-id="668c3-117">這是運用手的功能，可供使用者直接碰觸和操作全息影像。</span><span class="sxs-lookup"><span data-stu-id="668c3-117">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="668c3-118">藉由運用每日生活經驗並提供適當的視覺 affordances，使用者就能夠使用相同的方式來操作現實世界的物件，以便與虛擬化互動。</span><span class="sxs-lookup"><span data-stu-id="668c3-118">By leveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="668c3-119">[使用手的 ![點和認可](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="668c3-119">[![Point and commit with hands](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span></span><br>
        ### <a name="point-and-commit-with-handspoint-and-commitmdbr"></a>[<span data-ttu-id="668c3-120">手部指向和行動</span><span class="sxs-lookup"><span data-stu-id="668c3-120">Point and commit with hands</span></span>](point-and-commit.md)<br>
        <span data-ttu-id="668c3-121">這種方式可讓使用者在某個距離內與全息影像互動。</span><span class="sxs-lookup"><span data-stu-id="668c3-121">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="668c3-122">它可讓使用者充分利用周圍的環境。</span><span class="sxs-lookup"><span data-stu-id="668c3-122">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="668c3-123">使用者可以將全息影像放在任何位置，而且仍然可以從任何距離進行存取。</span><span class="sxs-lookup"><span data-stu-id="668c3-123">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="668c3-124">控制和操作2D 和3D 全像投影的心理模型和手勢，與直接操作的程式高度同步。</span><span class="sxs-lookup"><span data-stu-id="668c3-124">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="668c3-125">[![動作控制器](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span><span class="sxs-lookup"><span data-stu-id="668c3-125">[![Motion controllers](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span></span><br>
       ### <a name="motion-controllersmotion-controllersmdbr"></a>[<span data-ttu-id="668c3-126">運動控制器</span><span class="sxs-lookup"><span data-stu-id="668c3-126">Motion controllers</span></span>](motion-controllers.md)<br>
       <span data-ttu-id="668c3-127">「動作控制器」是一種工具，藉由在大量距離之間提供精確的互動，同時使用一或兩個手來擴充使用者的實體功能。</span><span class="sxs-lookup"><span data-stu-id="668c3-127">Motion controllers are tools that extend the user's physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="668c3-128">這些硬體配件提供許多常用互動的快捷方式，並提供 surefooted、觸覺各種動作的意見反應。</span><span class="sxs-lookup"><span data-stu-id="668c3-128">These hardware accessories provide shortcuts to many commonly-used interactions and provide surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="668c3-129">目前，動作控制器僅適用于 Windows Mixed Reality （WMR）案例。</span><span class="sxs-lookup"><span data-stu-id="668c3-129">Currently, motion controllers are only available for Windows Mixed Reality (WMR) scenarios.</span></span> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="668c3-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="668c3-130">See also</span></span>
* [<span data-ttu-id="668c3-131">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="668c3-131">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="668c3-132">頭部目光和停駐</span><span class="sxs-lookup"><span data-stu-id="668c3-132">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="668c3-133">手部直接操作</span><span class="sxs-lookup"><span data-stu-id="668c3-133">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="668c3-134">手部指向和行動</span><span class="sxs-lookup"><span data-stu-id="668c3-134">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="668c3-135">免持式</span><span class="sxs-lookup"><span data-stu-id="668c3-135">Hands-free</span></span>](hands-free.md)
