---
title: 注視和停留
description: （眼睛/head）注視和停留輸入模型的一般總覽
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Mixed Reality，注視，停留，互動，設計，眼睛追蹤，head 追蹤
ms.openlocfilehash: d87406d0b2695cd86c40f27cb132af54ed525b25
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435361"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="a9ca2-104">注視和停留</span><span class="sxs-lookup"><span data-stu-id="a9ca2-104">Gaze and dwell</span></span>

<span data-ttu-id="a9ca2-105">當手上拿著工具和組件時，手勢可以很繁瑣或不可能進行。</span><span class="sxs-lookup"><span data-stu-id="a9ca2-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="a9ca2-106">語音命令在某些內容中可能也不可靠，例如在過高的情況下。</span><span class="sxs-lookup"><span data-stu-id="a9ca2-106">Voice commands may also be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="a9ca2-107">注視和停留提供了一種熟悉且簡單的機制，可讓您在 HoloLens 上運作並無需實際操作。</span><span class="sxs-lookup"><span data-stu-id="a9ca2-107">Gaze and dwell offers a familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="a9ca2-108">此外，注視和停留是一個絕佳的回溯，與作業環境中的干擾干擾或無聲條件約束無關。</span><span class="sxs-lookup"><span data-stu-id="a9ca2-108">Additionally, gaze and dwell is a great fallback which is independent of noise interference or silence constraints in the operating environment.</span></span>
<span data-ttu-id="a9ca2-109">我們區分兩種看眼_和停留_的變化：[頭部眼和停留](gaze-and-dwell-head.md)，以及監看[式和停留](gaze-and-dwell-eyes.md)。</span><span class="sxs-lookup"><span data-stu-id="a9ca2-109">We distinguish two variants of _gaze and dwell_: [Head-gaze and dwell](gaze-and-dwell-head.md) and [Eye-gaze and dwell](gaze-and-dwell-eyes.md).</span></span>

## <a name="scenarios"></a><span data-ttu-id="a9ca2-110">案例</span><span class="sxs-lookup"><span data-stu-id="a9ca2-110">Scenarios</span></span>

<span data-ttu-id="a9ca2-111">在某人的手中使用其他工作的情況下，注視並停留擅長，而語音不會因為環境或社交條件約束而處於100% 可靠或可供使用。</span><span class="sxs-lookup"><span data-stu-id="a9ca2-111">Gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or available due to environmental or social constraints.</span></span> <span data-ttu-id="a9ca2-112">穿戴 HoloLens 的人員在修理汽車引擎時覆疊參考資訊就是個不錯的範例。</span><span class="sxs-lookup"><span data-stu-id="a9ca2-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="a9ca2-113">他們的雙手忙著拿起工具，或在靠向引擎室時支撐其身體。</span><span class="sxs-lookup"><span data-stu-id="a9ca2-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="a9ca2-114">車庫空間很吵雜，充斥著工具的碰撞和唧唧聲，讓語音命令變得難以使用。</span><span class="sxs-lookup"><span data-stu-id="a9ca2-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="a9ca2-115">注視和停留可讓使用 HoloLens 的人安心地流覽其參考資料，而不會中斷工作流程。</span><span class="sxs-lookup"><span data-stu-id="a9ca2-115">Gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="a9ca2-116">裝置支援</span><span class="sxs-lookup"><span data-stu-id="a9ca2-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a9ca2-117"><strong>輸入模型</strong></span><span class="sxs-lookup"><span data-stu-id="a9ca2-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="a9ca2-118"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="a9ca2-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="a9ca2-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="a9ca2-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="a9ca2-120"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="a9ca2-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a9ca2-121">頭部注視並佇留</span><span class="sxs-lookup"><span data-stu-id="a9ca2-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="a9ca2-122">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="a9ca2-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="a9ca2-123">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="a9ca2-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="a9ca2-124">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="a9ca2-124">✔️ Recommended</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a9ca2-125">眼睛與停留</span><span class="sxs-lookup"><span data-stu-id="a9ca2-125">Eye-gaze and dwell</span></span></td>
        <td><span data-ttu-id="a9ca2-126">❌ 無法使用</span><span class="sxs-lookup"><span data-stu-id="a9ca2-126">❌ Not available</span></span></td>
        <td><span data-ttu-id="a9ca2-127">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="a9ca2-127">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="a9ca2-128">❌ 無法使用</span><span class="sxs-lookup"><span data-stu-id="a9ca2-128">❌ Not available</span></span></td>
    </tr>
</table>


<br>

---
 
 ## <a name="see-also"></a><span data-ttu-id="a9ca2-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="a9ca2-129">See also</span></span>
* [<span data-ttu-id="a9ca2-130">目視互動</span><span class="sxs-lookup"><span data-stu-id="a9ca2-130">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="a9ca2-131">HoloLens 2 上的眼睛追蹤</span><span class="sxs-lookup"><span data-stu-id="a9ca2-131">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="a9ca2-132">注視和認可</span><span class="sxs-lookup"><span data-stu-id="a9ca2-132">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="a9ca2-133">直接操作</span><span class="sxs-lookup"><span data-stu-id="a9ca2-133">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="a9ca2-134">實習手勢</span><span class="sxs-lookup"><span data-stu-id="a9ca2-134">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="a9ca2-135">實際操作和認可</span><span class="sxs-lookup"><span data-stu-id="a9ca2-135">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="a9ca2-136">本能互動</span><span class="sxs-lookup"><span data-stu-id="a9ca2-136">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="a9ca2-137">語音輸入</span><span class="sxs-lookup"><span data-stu-id="a9ca2-137">Voice input</span></span>](voice-input.md)
