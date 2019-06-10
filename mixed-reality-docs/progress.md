---
title: 顯示進度
description: 進度控制項為使用者提供回饋，告知正在進行長時間執行的操作。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，設計、 控制項、 ui、 ux
ms.openlocfilehash: d62d86c690233f351b6c156c66eba33cb2687ea6
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813741"
---
# <a name="displaying-progress"></a><span data-ttu-id="e07ad-104">顯示進度</span><span class="sxs-lookup"><span data-stu-id="e07ad-104">Displaying progress</span></span>

<span data-ttu-id="e07ad-105">進度控制項為使用者提供回饋，告知正在進行長時間執行的操作。</span><span class="sxs-lookup"><span data-stu-id="e07ad-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="e07ad-106">根據所使用的指示器，它可以表示在進度指示器可見的時候，使用者無法與 App 互動，也可以指示可能需要等待多久的時間。</span><span class="sxs-lookup"><span data-stu-id="e07ad-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<span data-ttu-id="e07ad-107">![HoloLens 進度環範例](images/HoloLens2_Loader.gif)</span><span class="sxs-lookup"><span data-stu-id="e07ad-107">![Progress ring example in HoloLens](images/HoloLens2_Loader.gif)</span></span><br>
<span data-ttu-id="e07ad-108">*HoloLens 進度環範例*</span><span class="sxs-lookup"><span data-stu-id="e07ad-108">*Progress ring example in HoloLens*</span></span>

## <a name="types-of-progress"></a><span data-ttu-id="e07ad-109">進度的類型</span><span class="sxs-lookup"><span data-stu-id="e07ad-109">Types of progress</span></span>

<span data-ttu-id="e07ad-110">請務必提供有關最新動態的使用者資訊。</span><span class="sxs-lookup"><span data-stu-id="e07ad-110">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="e07ad-111">在混合實境中使用者可以被輕易地閃閃實體環境或物件如果您的應用程式不提供良好的視覺回應。</span><span class="sxs-lookup"><span data-stu-id="e07ad-111">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="e07ad-112">需要幾秒鐘的情況下，例如當資料載入或場景，正在更新，它是個不錯的主意，若要顯示的視覺指標。</span><span class="sxs-lookup"><span data-stu-id="e07ad-112">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="e07ad-113">有兩個選項，讓使用者有作業正在進行中-正在**進度列**或是**進度環**。</span><span class="sxs-lookup"><span data-stu-id="e07ad-113">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

### <a name="progress-bar"></a><span data-ttu-id="e07ad-114">進度列</span><span class="sxs-lookup"><span data-stu-id="e07ad-114">Progress bar</span></span>

![HoloLens 進度列範例](images/640px-progressbar.jpg)

<span data-ttu-id="e07ad-116">進度列會顯示工作的完成百分比。</span><span class="sxs-lookup"><span data-stu-id="e07ad-116">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="e07ad-117">它應該在其持續時間稱為 （確定），作業期間使用，但其進度應該不會封鎖應用程式的使用者的互動。</span><span class="sxs-lookup"><span data-stu-id="e07ad-117">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span>

### <a name="progress-ring"></a><span data-ttu-id="e07ad-118">進度環</span><span class="sxs-lookup"><span data-stu-id="e07ad-118">Progress ring</span></span>

![HoloLens 進度環範例](images/640px-progressring.jpg)

<span data-ttu-id="e07ad-120">進度環只有不定狀態，而且任何進一步的使用者互動會被封鎖，直到作業完成時，應使用。</span><span class="sxs-lookup"><span data-stu-id="e07ad-120">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span>

### <a name="progress-with-a-custom-object"></a><span data-ttu-id="e07ad-121">使用自訂物件的進度</span><span class="sxs-lookup"><span data-stu-id="e07ad-121">Progress with a custom object</span></span>

![使用中 HoloLens 的自訂網狀範例的進度](images/640px-progresscustom.jpg)

<span data-ttu-id="e07ad-123">您可以藉由自訂進度控制項，以您自己自訂的 2D/3D 物件新增至您的應用程式的個性和葺爦蜞頇。</span><span class="sxs-lookup"><span data-stu-id="e07ad-123">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span>

## <a name="best-practices"></a><span data-ttu-id="e07ad-124">最佳作法</span><span class="sxs-lookup"><span data-stu-id="e07ad-124">Best practices</span></span>
* <span data-ttu-id="e07ad-125">緊密結合[告示板或 tag-along](billboarding-and-tag-along.md)進度，因為使用者可以輕鬆地將其標頭移至空白空間，並遺失內容的顯示。</span><span class="sxs-lookup"><span data-stu-id="e07ad-125">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="e07ad-126">您的應用程式可能會在它已損毀，如果使用者無法看到任何項目外觀。</span><span class="sxs-lookup"><span data-stu-id="e07ad-126">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="e07ad-127">進度 prefab 是內建 billboarding 和 tag-along。</span><span class="sxs-lookup"><span data-stu-id="e07ad-127">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="e07ad-128">最好一律以提供有關最新動態給使用者的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="e07ad-128">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="e07ad-129">進度 prefab 提供不同的視覺樣式，包括 Windows 標準的信號類型進行提供狀態。</span><span class="sxs-lookup"><span data-stu-id="e07ad-129">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="e07ad-130">您也可以使用動畫使用自訂的網狀結構，如果您想要您的進度，以與您的應用程式的品牌保持一致的樣式。</span><span class="sxs-lookup"><span data-stu-id="e07ad-130">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

## <a name="see-also"></a><span data-ttu-id="e07ad-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e07ad-131">See also</span></span>
* [<span data-ttu-id="e07ad-132">進行指令碼及混合實境 toolkit prefabs</span><span class="sxs-lookup"><span data-stu-id="e07ad-132">Progress scripts and prefabs on Mixed Reality Toolkit</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [<span data-ttu-id="e07ad-133">週框方塊</span><span class="sxs-lookup"><span data-stu-id="e07ad-133">Bounding Box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="e07ad-134">可互動的物件</span><span class="sxs-lookup"><span data-stu-id="e07ad-134">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="e07ad-135">物件集合</span><span class="sxs-lookup"><span data-stu-id="e07ad-135">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="e07ad-136">佈告板和常駐標籤</span><span class="sxs-lookup"><span data-stu-id="e07ad-136">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
