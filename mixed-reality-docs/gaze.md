---
title: 注視
description: 視線是第一種形式的輸入，而且是主要表單的目標在混合實境中。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 混合實境、 視線、 互動，設計
ms.openlocfilehash: 9e50067f9dfeacf3dce5ea9a928990d1b142e4d0
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453713"
---
# <a name="gaze"></a><span data-ttu-id="479dd-104">注視</span><span class="sxs-lookup"><span data-stu-id="479dd-104">Gaze</span></span>

<span data-ttu-id="479dd-105">**視線**是第一種形式的輸入，而且為混合實境中目標的主要表單。</span><span class="sxs-lookup"><span data-stu-id="479dd-105">**Gaze** is the first form of input and is a primary form of targeting within mixed reality.</span></span> <span data-ttu-id="479dd-106">視線會告訴您使用者尋找世界中的位置，並讓您判斷其意圖。</span><span class="sxs-lookup"><span data-stu-id="479dd-106">Gaze tells you where the user is looking in the world and lets you determine their intent.</span></span> <span data-ttu-id="479dd-107">在真實世界中，您將通常探討您想要與互動的物件。</span><span class="sxs-lookup"><span data-stu-id="479dd-107">In the real world, you'll typically look at an object that you intend to interact with.</span></span> <span data-ttu-id="479dd-108">這是相同的視線。</span><span class="sxs-lookup"><span data-stu-id="479dd-108">This is the same with gaze.</span></span>

<span data-ttu-id="479dd-109">混合的實境耳機使用位置和您的使用者標頭的方向，以判斷其前端的視線向量。</span><span class="sxs-lookup"><span data-stu-id="479dd-109">Mixed reality headsets use the position and orientation of your user's head to determine their head gaze vector.</span></span> <span data-ttu-id="479dd-110">您可以想像這個向量的雷射指標直接繼續從直接在使用者的眼睛之間。</span><span class="sxs-lookup"><span data-stu-id="479dd-110">You can think of this vector as a laser pointer straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="479dd-111">使用者看起來房間周圍，因為您的應用程式有交集使用它自己全像投影和與此光線[空間對應](spatial-mapping.md)網狀結構來判斷您的使用者可能會看到什麼虛擬或實際物件。</span><span class="sxs-lookup"><span data-stu-id="479dd-111">As the user looks around the room, your application can intersect this ray, both with its own holograms and with the [spatial mapping](spatial-mapping.md) mesh to determine what virtual or real-world object your user may be looking at.</span></span>

<span data-ttu-id="479dd-112">HoloLens 2 上的互動可以使用者的前端視線，眼睛視線的目標或透過附近或到目前為止送互動。</span><span class="sxs-lookup"><span data-stu-id="479dd-112">On HoloLens 2, interactions can be targeted by either the user's head gaze, eye gaze or through near or far hand interactions.</span></span>
<span data-ttu-id="479dd-113">HoloLens 上 （第 1 代），互動應該通常衍生其目標從使用者的前端的視線，而不是嘗試轉譯，或直接互動的游標位置。</span><span class="sxs-lookup"><span data-stu-id="479dd-113">On HoloLens (1st gen), interactions should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="479dd-114">一旦啟動互動，相對的左手邊的動作可能會用來控制[筆勢](gestures.md)，如同[操作或瀏覽](gestures.md#composite-gestures)筆勢。</span><span class="sxs-lookup"><span data-stu-id="479dd-114">Once an interaction has started, relative motions of the hand may be used to control the [gesture](gestures.md), as with the [manipulation or navigation](gestures.md#composite-gestures) gesture.</span></span> <span data-ttu-id="479dd-115">使用沈浸式耳機，您可以針對使用其中一個前端的視線或指向-能夠[動作控制器](motion-controllers.md)。</span><span class="sxs-lookup"><span data-stu-id="479dd-115">With immersive headsets, you can target using either head gaze or pointing-capable [motion controllers](motion-controllers.md).</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a><span data-ttu-id="479dd-116">裝置支援</span><span class="sxs-lookup"><span data-stu-id="479dd-116">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="479dd-117">功能</span><span class="sxs-lookup"><span data-stu-id="479dd-117">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="479dd-118"><a href="hololens-hardware-details.md">HoloLens （第 1 代）</a></span><span class="sxs-lookup"><span data-stu-id="479dd-118"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="479dd-119">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="479dd-119">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="479dd-120"><a href="immersive-headset-hardware-details.md">沈浸式耳機</a></span><span class="sxs-lookup"><span data-stu-id="479dd-120"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="479dd-121">Head 視線</span><span class="sxs-lookup"><span data-stu-id="479dd-121">Head gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="479dd-122">✔️</span><span class="sxs-lookup"><span data-stu-id="479dd-122">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="479dd-123">✔️</span><span class="sxs-lookup"><span data-stu-id="479dd-123">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="479dd-124">✔️</span><span class="sxs-lookup"><span data-stu-id="479dd-124">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="479dd-125">眼睛視線</span><span class="sxs-lookup"><span data-stu-id="479dd-125">Eye gaze</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="479dd-126">✔️</span><span class="sxs-lookup"><span data-stu-id="479dd-126">✔️</span></span></td><td></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="479dd-127">HoloLens 2 的特定的詳細指引[即將推出](index.md#news-and-notes)。</span><span class="sxs-lookup"><span data-stu-id="479dd-127">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>


## <a name="uses-of-gaze"></a><span data-ttu-id="479dd-128">視線的用途</span><span class="sxs-lookup"><span data-stu-id="479dd-128">Uses of gaze</span></span>

<span data-ttu-id="479dd-129">混合的實境開發人員，您可以執行許多與標頭或眼睛視線：</span><span class="sxs-lookup"><span data-stu-id="479dd-129">As a mixed reality developer, you can do a lot with head or eye gaze:</span></span>
* <span data-ttu-id="479dd-130">您的應用程式有交集視線全像投影場景中使用以判斷使用者的注意力所在。</span><span class="sxs-lookup"><span data-stu-id="479dd-130">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is.</span></span>
* <span data-ttu-id="479dd-131">您的應用程式筆勢和根據使用者的視線，讓使用者選取、 啟動、 擷取、 捲動，或否則互動及其全像投影的控制器動作目標。</span><span class="sxs-lookup"><span data-stu-id="479dd-131">Your app can target gestures and controller presses based on the user's gaze, letting the user select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="479dd-132">您的應用程式可以讓使用者加全像投影在真實世界表面上交集空間對應網狀結構其視線無限遠的光線。</span><span class="sxs-lookup"><span data-stu-id="479dd-132">Your app can let the user place holograms on real-world surfaces, by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="479dd-133">您的應用程式可以知道使用者何時*不*尋找重要的物件，可能會導致您的應用程式，提供視覺與音訊提示，可針對該物件所開啟的方向。</span><span class="sxs-lookup"><span data-stu-id="479dd-133">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

## <a name="cursor"></a><span data-ttu-id="479dd-134">資料指標</span><span class="sxs-lookup"><span data-stu-id="479dd-134">Cursor</span></span>

<span data-ttu-id="479dd-135">針對前端的視線，大部分的應用程式應該使用[游標](cursors.md)（或其他聽覺/visual 指示） 給使用者的信心，在他們要進行互動。</span><span class="sxs-lookup"><span data-stu-id="479dd-135">For head gaze, most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="479dd-136">您通常會放置在其前端的視線光線先相交的物件，可能是雷射或實際介面的世界中的這個資料指標。</span><span class="sxs-lookup"><span data-stu-id="479dd-136">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span>

<span data-ttu-id="479dd-137">![若要顯示視線範例視覺化資料指標](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="479dd-137">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
<span data-ttu-id="479dd-138">*若要顯示視線範例視覺化資料指標*</span><span class="sxs-lookup"><span data-stu-id="479dd-138">*An example visual cursor to show gaze*</span></span>

<span data-ttu-id="479dd-139">眼睛視線，我們通常建議*不*這可能使得和惱人的使用者很快就會顯示資料指標。</span><span class="sxs-lookup"><span data-stu-id="479dd-139">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="479dd-140">相反地稍微反白顯示視覺的目標，或使用非常模糊的眼睛資料指標來提供有關使用者是要互動的信心。</span><span class="sxs-lookup"><span data-stu-id="479dd-140">Instead subtly highlight visual targets or use a very faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="479dd-141">如需詳細資訊，請查看我們[的設計指引眼睛式輸入](eye-tracking.md)HoloLens 2 上。</span><span class="sxs-lookup"><span data-stu-id="479dd-141">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>

## <a name="giving-action-to-the-users-gaze"></a><span data-ttu-id="479dd-142">讓使用者的視線動作</span><span class="sxs-lookup"><span data-stu-id="479dd-142">Giving action to the user's gaze</span></span>

<span data-ttu-id="479dd-143">一旦使用者已針對全像或使用其視線的真實物件，其下一個步驟是該物件上採取動作。</span><span class="sxs-lookup"><span data-stu-id="479dd-143">Once the user has targeted a hologram or real-world object using their gaze, their next step is to take action on that object.</span></span> <span data-ttu-id="479dd-144">讓使用者以採取動作的主要方式是透過[筆勢](gestures.md)，[動作控制站](motion-controllers.md)並[語音](voice-input.md)。</span><span class="sxs-lookup"><span data-stu-id="479dd-144">The primary ways for a user to take action are through [gestures](gestures.md), [motion controllers](motion-controllers.md) and [voice](voice-input.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="479dd-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="479dd-145">See also</span></span>
* [<span data-ttu-id="479dd-146">MR Input 210：Head 視線</span><span class="sxs-lookup"><span data-stu-id="479dd-146">MR Input 210: Head gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="479dd-147">DirectX 中的頭部和眼睛目光</span><span class="sxs-lookup"><span data-stu-id="479dd-147">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="479dd-148">在 Unity 中的標頭視線</span><span class="sxs-lookup"><span data-stu-id="479dd-148">Head gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="479dd-149">HoloLens 2 上追蹤</span><span class="sxs-lookup"><span data-stu-id="479dd-149">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="479dd-150">在 Unity 中使用混合實境工具組的眼睛視線</span><span class="sxs-lookup"><span data-stu-id="479dd-150">Eye gaze in Unity using Mixed Reality Toolkit</span></span>](https://aka.ms/mrtk-eyes)
