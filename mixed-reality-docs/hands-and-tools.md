---
title: 指針 」 和 「 動作控制站
description: 指針 」 和 「 動作控制站互動的概觀
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: 混合實境，實際操作、 移動控制站、 互動，設計
ms.openlocfilehash: 583d284ee98b8ccbc0a9c2c8670551d0a7397074
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873989"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="29a04-104">指針 」 和 「 動作控制站</span><span class="sxs-lookup"><span data-stu-id="29a04-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="29a04-105">案例</span><span class="sxs-lookup"><span data-stu-id="29a04-105">Scenarios</span></span>
<span data-ttu-id="29a04-106">如果您選擇採用此互動模型，在讀取後[設計指導方針](interaction-fundamentals.md)，這表示您正在開發應用程式要求使用者使用兩個實際操作與全像攝影版的世界互動。</span><span class="sxs-lookup"><span data-stu-id="29a04-106">If you choose to adopt this interaction model after reading the [design guidelines](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="29a04-107">您的應用程式即將達到的目的是移除虛擬與實體之間的界限。</span><span class="sxs-lookup"><span data-stu-id="29a04-107">Your application is going to achieve the goal of removing the boundry between virtual and physical.</span></span>

<span data-ttu-id="29a04-108">某些特定情況下可能是：</span><span class="sxs-lookup"><span data-stu-id="29a04-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="29a04-109">提供資訊工作者 2D vitual 畫面和 Ui 顯示及控制內容</span><span class="sxs-lookup"><span data-stu-id="29a04-109">Providing information workers 2D vitual screens and UIs to display and control contents</span></span>
* <span data-ttu-id="29a04-110">提供第一列的背景工作角色教學課程和處理站生產線中的指南</span><span class="sxs-lookup"><span data-stu-id="29a04-110">Providing first line workers tutorials and guides in factory assembly lines</span></span>
* <span data-ttu-id="29a04-111">開發專業的工具，協助和教育醫療專業人員</span><span class="sxs-lookup"><span data-stu-id="29a04-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="29a04-112">使用 3D 虛擬物件，來裝飾現實世界裡，或建立第二個的世界</span><span class="sxs-lookup"><span data-stu-id="29a04-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="29a04-113">建立位置為基礎的服務以及做為背景使用真實世界的遊戲</span><span class="sxs-lookup"><span data-stu-id="29a04-113">Creating location based services and games using the real world as background</span></span>

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="29a04-114">雙手及動作控制器的型態</span><span class="sxs-lookup"><span data-stu-id="29a04-114">Hands and motion controllers modalities</span></span>
### <a name="direct-manipulation-near-hand-interactiondirect-manipulationmd"></a>[<span data-ttu-id="29a04-115">直接操作 （靠近手動互動）</span><span class="sxs-lookup"><span data-stu-id="29a04-115">Direct manipulation (Near hand interaction)</span></span>](direct-manipulation.md)
<span data-ttu-id="29a04-116">這是指針，與使用者相關能夠觸碰並直接操作全像投影的強大的強制回應性。</span><span class="sxs-lookup"><span data-stu-id="29a04-116">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="29a04-117">由 leaveraging 日常生活體驗，以及提供適當的視覺化提供，使用者就能夠使用相同的方式管理真實世界物件的互動以虛擬的。</span><span class="sxs-lookup"><span data-stu-id="29a04-117">By leaveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world obejcts to interact with virtual ones.</span></span>   

### <a name="point-and-commit-far-hand-interactionpoint-and-commitmd"></a>[<span data-ttu-id="29a04-118">點和認可 （Far 手動互動）</span><span class="sxs-lookup"><span data-stu-id="29a04-118">Point and commit (Far hand interaction)</span></span>](point-and-commit.md)
<span data-ttu-id="29a04-119">此樣式會提供使用者互動距離全像投影的進階電源。</span><span class="sxs-lookup"><span data-stu-id="29a04-119">This modality provides users super power to interact with holograms in a distance.</span></span> <span data-ttu-id="29a04-120">它可讓使用者能夠發揮最大的周圍的設定。</span><span class="sxs-lookup"><span data-stu-id="29a04-120">It enables users to make the best use of setting of surrounding.</span></span> <span data-ttu-id="29a04-121">使用者可以任意位置放置全像投影，並仍可以存取這些從任何的距離。</span><span class="sxs-lookup"><span data-stu-id="29a04-121">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="29a04-122">心智模型和手勢，來控制及管理 2D 和 3D 全像投影為高度同步與直接操作。</span><span class="sxs-lookup"><span data-stu-id="29a04-122">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>

### <a name="motion-controllersmotion-controllersmd"></a>[<span data-ttu-id="29a04-123">運動控制器</span><span class="sxs-lookup"><span data-stu-id="29a04-123">Motion controllers</span></span>](motion-controllers.md)
<span data-ttu-id="29a04-124">動作控制站都是藉由大型距離範圍擴及提供精確的互動，同時使用一或兩個實際操作擴充使用者的實體功能的工具。</span><span class="sxs-lookup"><span data-stu-id="29a04-124">Motion controllers are tools that extend the users' physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="29a04-125">這些硬體附屬應用程式提供許多常用的互動，並提供 surefooted、 tactile 意見反應的各種動作的捷徑。</span><span class="sxs-lookup"><span data-stu-id="29a04-125">These hardware accessories provide shortcuts to many commonly-used interactions and gives surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="29a04-126">動作控制站目前只適用於 WMR 案例。</span><span class="sxs-lookup"><span data-stu-id="29a04-126">Currently, motion controllers are only available for WMR scenarios.</span></span> 

![](images/Hands-and-controllers-720px.jpg)<br>

## <a name="see-also"></a><span data-ttu-id="29a04-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29a04-127">See also</span></span>
* [<span data-ttu-id="29a04-128">視線與認可</span><span class="sxs-lookup"><span data-stu-id="29a04-128">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="29a04-129">直接操作 （靠近手動互動）</span><span class="sxs-lookup"><span data-stu-id="29a04-129">Direct manipulation (Near hand interaction)</span></span>](direct-manipulation.md)
* [<span data-ttu-id="29a04-130">點和認可 （Far 手動互動）</span><span class="sxs-lookup"><span data-stu-id="29a04-130">Point and commit (Far hand interaction)</span></span>](point-and-commit.md)
* [<span data-ttu-id="29a04-131">Hands-free</span><span class="sxs-lookup"><span data-stu-id="29a04-131">Hands-free</span></span>](hands-free.md)
* [<span data-ttu-id="29a04-132">目光目標</span><span class="sxs-lookup"><span data-stu-id="29a04-132">Gaze targeting</span></span>](gaze-targeting.md)
