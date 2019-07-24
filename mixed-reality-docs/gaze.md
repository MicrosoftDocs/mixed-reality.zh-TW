---
title: 注視
description: 注視是第一種形式的輸入, 是混合現實中的主要目標形式。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Mixed reality, 注視, 互動, 設計
ms.openlocfilehash: 7e65d26d3e9edabbd01d35a887ffc8622a3c6337
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414374"
---
# <a name="gaze"></a><span data-ttu-id="8fb90-104">注視</span><span class="sxs-lookup"><span data-stu-id="8fb90-104">Gaze</span></span>

<span data-ttu-id="8fb90-105">**注視**是第一種形式的輸入, 是混合現實中的主要目標形式。</span><span class="sxs-lookup"><span data-stu-id="8fb90-105">**Gaze** is the first form of input and is a primary form of targeting within mixed reality.</span></span> <span data-ttu-id="8fb90-106">注視會告訴您使用者在世界中的所在位置, 並可讓您判斷其意圖。</span><span class="sxs-lookup"><span data-stu-id="8fb90-106">Gaze tells you where the user is looking in the world and lets you determine their intent.</span></span> <span data-ttu-id="8fb90-107">在真實世界中, 您通常會查看想要與之互動的物件。</span><span class="sxs-lookup"><span data-stu-id="8fb90-107">In the real world, you'll typically look at an object that you intend to interact with.</span></span> <span data-ttu-id="8fb90-108">這與注視相同。</span><span class="sxs-lookup"><span data-stu-id="8fb90-108">This is the same with gaze.</span></span>

<span data-ttu-id="8fb90-109">混合現實耳機會使用您使用者的前端位置和方向來判斷其 head 的注視向量。</span><span class="sxs-lookup"><span data-stu-id="8fb90-109">Mixed reality headsets use the position and orientation of your user's head to determine their head gaze vector.</span></span> <span data-ttu-id="8fb90-110">您可以直接從使用者的眼睛, 將此向量視為鐳射指標。</span><span class="sxs-lookup"><span data-stu-id="8fb90-110">You can think of this vector as a laser pointer straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="8fb90-111">當使用者查看房間時, 您的應用程式可以與此光線相交, 這兩者都有自己的全息影像和[空間對應](spatial-mapping.md)網格, 以判斷您的使用者可能會查看的虛擬或真實世界物件。</span><span class="sxs-lookup"><span data-stu-id="8fb90-111">As the user looks around the room, your application can intersect this ray, both with its own holograms and with the [spatial mapping](spatial-mapping.md) mesh to determine what virtual or real-world object your user may be looking at.</span></span>

<span data-ttu-id="8fb90-112">在 HoloLens 2 上, 互動的目標可能是使用者的前端、眼睛眼, 或接近或遠的手間互動。</span><span class="sxs-lookup"><span data-stu-id="8fb90-112">On HoloLens 2, interactions can be targeted by either the user's head gaze, eye gaze or through near or far hand interactions.</span></span>
<span data-ttu-id="8fb90-113">在 HoloLens (第1代) 上, 互動通常會從使用者的前端衍生其目標, 而不是嘗試直接在手中呈現或互動。</span><span class="sxs-lookup"><span data-stu-id="8fb90-113">On HoloLens (1st gen), interactions should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="8fb90-114">互動開始之後, 手的相對運動可能會用來控制[手勢](gestures.md), 如同[操作或導覽](gestures.md#composite-gestures)手勢。</span><span class="sxs-lookup"><span data-stu-id="8fb90-114">Once an interaction has started, relative motions of the hand may be used to control the [gesture](gestures.md), as with the [manipulation or navigation](gestures.md#composite-gestures) gesture.</span></span> <span data-ttu-id="8fb90-115">有了沉浸式耳機, 您就可以使用頭部注視或可支援指標的[運動控制器](motion-controllers.md)作為目標。</span><span class="sxs-lookup"><span data-stu-id="8fb90-115">With immersive headsets, you can target using either head gaze or pointing-capable [motion controllers](motion-controllers.md).</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a><span data-ttu-id="8fb90-116">裝置支援</span><span class="sxs-lookup"><span data-stu-id="8fb90-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="8fb90-117"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="8fb90-117"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="8fb90-118"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="8fb90-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="8fb90-119"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="8fb90-119"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="8fb90-120"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="8fb90-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8fb90-121">頭部注視</span><span class="sxs-lookup"><span data-stu-id="8fb90-121">Head gaze</span></span></td>
        <td><span data-ttu-id="8fb90-122">✔️</span><span class="sxs-lookup"><span data-stu-id="8fb90-122">✔️</span></span></td>
        <td><span data-ttu-id="8fb90-123">✔️</span><span class="sxs-lookup"><span data-stu-id="8fb90-123">✔️</span></span></td>
        <td><span data-ttu-id="8fb90-124">✔️</span><span class="sxs-lookup"><span data-stu-id="8fb90-124">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8fb90-125">眼睛</span><span class="sxs-lookup"><span data-stu-id="8fb90-125">Eye gaze</span></span></td>
        <td><span data-ttu-id="8fb90-126">❌</span><span class="sxs-lookup"><span data-stu-id="8fb90-126">❌</span></span></td>
        <td><span data-ttu-id="8fb90-127">✔️</span><span class="sxs-lookup"><span data-stu-id="8fb90-127">✔️</span></span></td>
        <td><span data-ttu-id="8fb90-128">❌</span><span class="sxs-lookup"><span data-stu-id="8fb90-128">❌</span></span></td>
    </tr>
</table>

> [!NOTE]
> <span data-ttu-id="8fb90-129">[即將推出](index.md#news-and-notes)更多 HoloLens 2 特定指引。</span><span class="sxs-lookup"><span data-stu-id="8fb90-129">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>


## <a name="uses-of-gaze"></a><span data-ttu-id="8fb90-130">注視的使用</span><span class="sxs-lookup"><span data-stu-id="8fb90-130">Uses of gaze</span></span>

<span data-ttu-id="8fb90-131">身為混合現實的開發人員, 您可以使用 head 或眼睛來進行許多動作:</span><span class="sxs-lookup"><span data-stu-id="8fb90-131">As a mixed reality developer, you can do a lot with head or eye gaze:</span></span>
* <span data-ttu-id="8fb90-132">您的應用程式可以與場景中的全息影像相交, 以判斷使用者的注意位置。</span><span class="sxs-lookup"><span data-stu-id="8fb90-132">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is.</span></span>
* <span data-ttu-id="8fb90-133">您的應用程式可以根據使用者的注視來鎖定手勢和控制器按下, 讓使用者選取、啟動、抓取、滾動, 或以其他方式與其全息影像互動。</span><span class="sxs-lookup"><span data-stu-id="8fb90-133">Your app can target gestures and controller presses based on the user's gaze, letting the user select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="8fb90-134">您的應用程式可以讓使用者將全息影像放在真實世界的表面上, 並將其注視光線與空間對應網格相交。</span><span class="sxs-lookup"><span data-stu-id="8fb90-134">Your app can let the user place holograms on real-world surfaces, by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="8fb90-135">您的應用程式可以知道使用者何時看*不*到重要物件的方向, 這可能會導致您的應用程式提供視覺和音訊提示來轉向該物件。</span><span class="sxs-lookup"><span data-stu-id="8fb90-135">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

## <a name="cursor"></a><span data-ttu-id="8fb90-136">資料指標</span><span class="sxs-lookup"><span data-stu-id="8fb90-136">Cursor</span></span>

<span data-ttu-id="8fb90-137">對於列印頭, 大部分的應用程式都應該使用[游標](cursors.md)(或其他聽覺/視覺指示), 讓使用者能夠信賴他們要與之互動的物件。</span><span class="sxs-lookup"><span data-stu-id="8fb90-137">For head gaze, most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="8fb90-138">您通常會將此游標置於世界中, 其前端光線會先與物件相交, 這可能是全息影像或真實世界表面。</span><span class="sxs-lookup"><span data-stu-id="8fb90-138">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span>

<span data-ttu-id="8fb90-139">![顯示注視的視覺化游標範例](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="8fb90-139">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
<span data-ttu-id="8fb90-140">*顯示注視的視覺化游標範例*</span><span class="sxs-lookup"><span data-stu-id="8fb90-140">*An example visual cursor to show gaze*</span></span>

<span data-ttu-id="8fb90-141">就眼睛而言, 我們通常建議*不要*顯示游標, 因為這可能會很快就會變得令人困擾, 而且不會讓使用者雜亂。</span><span class="sxs-lookup"><span data-stu-id="8fb90-141">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="8fb90-142">相反地, 反白顯示視覺效果目標, 或使用非常不好的眼游標, 讓您安心瞭解使用者的互動方式。</span><span class="sxs-lookup"><span data-stu-id="8fb90-142">Instead subtly highlight visual targets or use a very faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="8fb90-143">如需詳細資訊, 請查看我們在 HoloLens 2 上[以眼睛為基礎之輸入的設計指引](eye-tracking.md)。</span><span class="sxs-lookup"><span data-stu-id="8fb90-143">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>

## <a name="giving-action-to-the-users-gaze"></a><span data-ttu-id="8fb90-144">對使用者的注視提供動作</span><span class="sxs-lookup"><span data-stu-id="8fb90-144">Giving action to the user's gaze</span></span>

<span data-ttu-id="8fb90-145">一旦使用者使用其注視來鎖定全息影像或真實世界物件, 下一步就是對該物件採取動作。</span><span class="sxs-lookup"><span data-stu-id="8fb90-145">Once the user has targeted a hologram or real-world object using their gaze, their next step is to take action on that object.</span></span> <span data-ttu-id="8fb90-146">使用者採取動作的主要方式是透過[手勢](gestures.md)、[動作控制器](motion-controllers.md)和[語音](voice-input.md)。</span><span class="sxs-lookup"><span data-stu-id="8fb90-146">The primary ways for a user to take action are through [gestures](gestures.md), [motion controllers](motion-controllers.md) and [voice](voice-input.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8fb90-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8fb90-147">See also</span></span>
* [<span data-ttu-id="8fb90-148">MR Input 210：頭部注視</span><span class="sxs-lookup"><span data-stu-id="8fb90-148">MR Input 210: Head gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="8fb90-149">DirectX 中的頭部和眼睛目光</span><span class="sxs-lookup"><span data-stu-id="8fb90-149">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="8fb90-150">Unity 中的頭注視</span><span class="sxs-lookup"><span data-stu-id="8fb90-150">Head gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="8fb90-151">HoloLens 2 上的眼睛</span><span class="sxs-lookup"><span data-stu-id="8fb90-151">Eye-gaze on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="8fb90-152">Unity 使用混合現實工具組的眼睛</span><span class="sxs-lookup"><span data-stu-id="8fb90-152">Eye gaze in Unity using Mixed Reality Toolkit</span></span>](https://aka.ms/mrtk-eyes)
