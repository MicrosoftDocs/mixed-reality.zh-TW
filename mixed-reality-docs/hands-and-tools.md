---
title: 實習和運動控制器
description: 實習與運動控制器互動的總覽
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: Mixed Reality, 實習, 運動控制器, 互動, 設計
ms.openlocfilehash: d0e54c71ab42a09f2f9c6063a85441b98e729af1
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039171"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="a193b-104">實習和運動控制器</span><span class="sxs-lookup"><span data-stu-id="a193b-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="a193b-105">案例</span><span class="sxs-lookup"><span data-stu-id="a193b-105">Scenarios</span></span>
<span data-ttu-id="a193b-106">如果您在閱讀[設計指導方針](interaction-fundamentals.md)之後選擇採用此互動模型, 就表示您正在開發的應用程式需要使用者使用兩個手來與全像攝影世界互動。</span><span class="sxs-lookup"><span data-stu-id="a193b-106">If you choose to adopt this interaction model after reading the [design guidelines](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="a193b-107">您的應用程式即將達到在虛擬與實體之間移除 boundry 的目標。</span><span class="sxs-lookup"><span data-stu-id="a193b-107">Your application is going to achieve the goal of removing the boundry between virtual and physical.</span></span>

<span data-ttu-id="a193b-108">某些特定案例可能是:</span><span class="sxs-lookup"><span data-stu-id="a193b-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="a193b-109">提供資訊工作者 2D vitual 畫面和 Ui 以顯示和控制內容</span><span class="sxs-lookup"><span data-stu-id="a193b-109">Providing information workers 2D vitual screens and UIs to display and control contents</span></span>
* <span data-ttu-id="a193b-110">在 factory 元件行中提供第一行工作者教學課程和指南</span><span class="sxs-lookup"><span data-stu-id="a193b-110">Providing first line workers tutorials and guides in factory assembly lines</span></span>
* <span data-ttu-id="a193b-111">開發專業工具來協助及教育醫療專業人員</span><span class="sxs-lookup"><span data-stu-id="a193b-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="a193b-112">使用3D 虛擬物件裝飾真實世界或建立第二個世界</span><span class="sxs-lookup"><span data-stu-id="a193b-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="a193b-113">使用真實世界作為背景來建立位置服務和遊戲</span><span class="sxs-lookup"><span data-stu-id="a193b-113">Creating location based services and games using the real world as background</span></span>

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="a193b-114">實習和運動控制器形式</span><span class="sxs-lookup"><span data-stu-id="a193b-114">Hands and motion controllers modalities</span></span>
### <a name="direct-manipulation-with-handsdirect-manipulationmd"></a>[<span data-ttu-id="a193b-115">手部直接操作</span><span class="sxs-lookup"><span data-stu-id="a193b-115">Direct manipulation with hands</span></span>](direct-manipulation.md)
<span data-ttu-id="a193b-116">這是運用手的功能, 可供使用者直接碰觸和操作全息影像。</span><span class="sxs-lookup"><span data-stu-id="a193b-116">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="a193b-117">藉由 leaveraging 每日生活經驗, 並提供適當的視覺 affordances, 使用者就能夠使用相同的方式來操作真實世界的物件, 以與虛擬化進行互動。</span><span class="sxs-lookup"><span data-stu-id="a193b-117">By leaveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>   

### <a name="point-and-commit-with-handspoint-and-commitmd"></a>[<span data-ttu-id="a193b-118">手部指向和行動</span><span class="sxs-lookup"><span data-stu-id="a193b-118">Point and commit with hands</span></span>](point-and-commit.md)
<span data-ttu-id="a193b-119">這種方式可讓使用者在某個距離內與全息影像互動。</span><span class="sxs-lookup"><span data-stu-id="a193b-119">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="a193b-120">它可讓使用者充分利用周圍的環境。</span><span class="sxs-lookup"><span data-stu-id="a193b-120">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="a193b-121">使用者可以將全息影像放在任何位置, 而且仍然可以從任何距離進行存取。</span><span class="sxs-lookup"><span data-stu-id="a193b-121">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="a193b-122">控制和操作2D 和3D 全像投影的心理模型和手勢, 與直接操作的程式高度同步。</span><span class="sxs-lookup"><span data-stu-id="a193b-122">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>

### <a name="motion-controllersmotion-controllersmd"></a>[<span data-ttu-id="a193b-123">運動控制器</span><span class="sxs-lookup"><span data-stu-id="a193b-123">Motion controllers</span></span>](motion-controllers.md)
<span data-ttu-id="a193b-124">「動作控制器」是一種工具, 藉由在使用一或兩個手間的精確互動, 來擴充使用者的實體功能。</span><span class="sxs-lookup"><span data-stu-id="a193b-124">Motion controllers are tools that extend the users' physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="a193b-125">這些硬體配件提供許多常用互動的快捷方式, 並提供 surefooted、觸覺各種動作的意見反應。</span><span class="sxs-lookup"><span data-stu-id="a193b-125">These hardware accessories provide shortcuts to many commonly-used interactions and gives surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="a193b-126">目前, 動作控制器僅適用于 WMR 案例。</span><span class="sxs-lookup"><span data-stu-id="a193b-126">Currently, motion controllers are only available for WMR scenarios.</span></span> 

![](images/Hands-and-controllers-720px.jpg)<br>

## <a name="see-also"></a><span data-ttu-id="a193b-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a193b-127">See also</span></span>
* [<span data-ttu-id="a193b-128">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="a193b-128">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="a193b-129">頭部目光和停駐</span><span class="sxs-lookup"><span data-stu-id="a193b-129">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="a193b-130">手部直接操作</span><span class="sxs-lookup"><span data-stu-id="a193b-130">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="a193b-131">手部指向和行動</span><span class="sxs-lookup"><span data-stu-id="a193b-131">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="a193b-132">免持式</span><span class="sxs-lookup"><span data-stu-id="a193b-132">Hands-free</span></span>](hands-free.md)
