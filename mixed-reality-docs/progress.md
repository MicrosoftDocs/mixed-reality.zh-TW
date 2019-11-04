---
title: 顯示進度
description: 進度控制項為使用者提供回饋，告知正在進行長時間執行的操作。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，設計，控制項，ui，ux
ms.openlocfilehash: 43b4802e7c821c98c847509ace950f381da12f95
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437535"
---
# <a name="displaying-progress"></a><span data-ttu-id="fe492-104">顯示進度</span><span class="sxs-lookup"><span data-stu-id="fe492-104">Displaying progress</span></span>

<br>

<img src="images/HoloLens2_Loader.gif" alt="Progress ring example in HoloLens" width="940px">

<span data-ttu-id="fe492-105">進度控制項為使用者提供回饋，告知正在進行長時間執行的操作。</span><span class="sxs-lookup"><span data-stu-id="fe492-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="fe492-106">根據所使用的指示器，它可以表示在進度指示器可見的時候，使用者無法與 App 互動，也可以指示可能需要等待多久的時間。</span><span class="sxs-lookup"><span data-stu-id="fe492-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<br>

---

## <a name="types-of-progress"></a><span data-ttu-id="fe492-107">進度的類型</span><span class="sxs-lookup"><span data-stu-id="fe492-107">Types of progress</span></span>

<span data-ttu-id="fe492-108">請務必提供有關發生什麼情況的使用者資訊。</span><span class="sxs-lookup"><span data-stu-id="fe492-108">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="fe492-109">在混合現實中，如果您的應用程式沒有提供良好的視覺效果意見反應，實體環境或物件就可以輕鬆地將使用者工作。</span><span class="sxs-lookup"><span data-stu-id="fe492-109">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="fe492-110">針對需要幾秒鐘的情況，例如資料載入或場景正在更新時，最好是顯示視覺指標。</span><span class="sxs-lookup"><span data-stu-id="fe492-110">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="fe492-111">有兩個選項可顯示作業正在進行中的使用者–一個**進度**列或一個**進度環**。</span><span class="sxs-lookup"><span data-stu-id="fe492-111">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a><span data-ttu-id="fe492-112">進度列</span><span class="sxs-lookup"><span data-stu-id="fe492-112">Progress bar</span></span><br>
        <span data-ttu-id="fe492-113">進度列會顯示工作已完成的百分比。</span><span class="sxs-lookup"><span data-stu-id="fe492-113">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="fe492-114">它應該在持續時間已知的作業期間使用（確定），但其進度不應封鎖使用者與應用程式的互動。</span><span class="sxs-lookup"><span data-stu-id="fe492-114">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span><br>
        <br>
        <span data-ttu-id="fe492-115">*影像： HoloLens 中的進度列範例*</span><span class="sxs-lookup"><span data-stu-id="fe492-115">*Image: Progress bar example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="fe492-116">![空間](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="fe492-116">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="fe492-117">HoloLens](images/640px-progressbar.jpg) 中 ![的進度列範例</span><span class="sxs-lookup"><span data-stu-id="fe492-117">![Progress bar example in HoloLens](images/640px-progressbar.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a><span data-ttu-id="fe492-118">進度環</span><span class="sxs-lookup"><span data-stu-id="fe492-118">Progress ring</span></span><br>
        <span data-ttu-id="fe492-119">進度環僅具有不定狀態，而且應該在作業完成之前封鎖任何進一步的使用者互動時使用。</span><span class="sxs-lookup"><span data-stu-id="fe492-119">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span><br>
        <br>
        <span data-ttu-id="fe492-120">*影像： HoloLens 中的進度環形範例*</span><span class="sxs-lookup"><span data-stu-id="fe492-120">*Image: Progress ring example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="fe492-121">![空間](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="fe492-121">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="fe492-122">HoloLens 中 ![的進度環形範例](images/640px-progressring.jpg)</span><span class="sxs-lookup"><span data-stu-id="fe492-122">![Progress ring example in HoloLens](images/640px-progressring.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a><span data-ttu-id="fe492-123">使用自訂物件的進度</span><span class="sxs-lookup"><span data-stu-id="fe492-123">Progress with a custom object</span></span><br>
        <span data-ttu-id="fe492-124">您可以使用自己的自訂 2D/3D 物件自訂進度控制項，以加入應用程式的個人化和品牌身分識別。</span><span class="sxs-lookup"><span data-stu-id="fe492-124">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span><br>
        <br>
        <span data-ttu-id="fe492-125">*影像：在 HoloLens 中使用自訂網格範例的進度*</span><span class="sxs-lookup"><span data-stu-id="fe492-125">*Image: Progress with custom mesh example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="fe492-126">![空間](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="fe492-126">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="fe492-127">使用 HoloLens 中的自訂網格範例 ![進度](images/640px-progresscustom.jpg)</span><span class="sxs-lookup"><span data-stu-id="fe492-127">![Progress with custom mesh example in HoloLens](images/640px-progresscustom.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a><span data-ttu-id="fe492-128">最佳做法</span><span class="sxs-lookup"><span data-stu-id="fe492-128">Best practices</span></span>
* <span data-ttu-id="fe492-129">將[billboarding 或標記](billboarding-and-tag-along.md)緊密地放在進度的顯示中，因為使用者可以輕鬆地將其標頭移至空白空間並遺失內容。</span><span class="sxs-lookup"><span data-stu-id="fe492-129">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="fe492-130">如果使用者無法看到任何專案，您的應用程式可能看起來好像已當機。</span><span class="sxs-lookup"><span data-stu-id="fe492-130">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="fe492-131">Billboarding 和標記會內建在進度 prefab 中。</span><span class="sxs-lookup"><span data-stu-id="fe492-131">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="fe492-132">提供使用者所發生狀況的狀態資訊，是很好的。</span><span class="sxs-lookup"><span data-stu-id="fe492-132">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="fe492-133">[進度] prefab 提供各種視覺化樣式，包括提供狀態的 Windows 標準環形類型進度。</span><span class="sxs-lookup"><span data-stu-id="fe492-133">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="fe492-134">如果您想要讓進度的樣式符合應用程式的品牌，您也可以使用自訂網格搭配動畫。</span><span class="sxs-lookup"><span data-stu-id="fe492-134">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="fe492-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="fe492-135">See also</span></span>
* [<span data-ttu-id="fe492-136">混合現實工具組上的進度腳本和 prefabs</span><span class="sxs-lookup"><span data-stu-id="fe492-136">Progress scripts and prefabs on Mixed Reality Toolkit</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [<span data-ttu-id="fe492-137">周框方塊</span><span class="sxs-lookup"><span data-stu-id="fe492-137">Bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="fe492-138">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="fe492-138">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="fe492-139">物件集合</span><span class="sxs-lookup"><span data-stu-id="fe492-139">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="fe492-140">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="fe492-140">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
