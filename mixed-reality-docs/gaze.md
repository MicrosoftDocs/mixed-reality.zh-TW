---
title: 注視
description: 視線是第一種形式的輸入，而且是主要表單的目標在混合實境中。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 混合實境、 視線、 互動，設計
ms.openlocfilehash: e0c1a925f6faeb37ec35e511cef36f9c06672c8a
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829746"
---
# <a name="gaze"></a><span data-ttu-id="605c8-104">注視</span><span class="sxs-lookup"><span data-stu-id="605c8-104">Gaze</span></span>

<span data-ttu-id="605c8-105">**視線**是第一種形式的輸入，而且為混合實境中目標的主要表單。</span><span class="sxs-lookup"><span data-stu-id="605c8-105">**Gaze** is the first form of input and is a primary form of targeting within mixed reality.</span></span> <span data-ttu-id="605c8-106">視線會告訴您使用者尋找世界中的位置，並讓您判斷其意圖。</span><span class="sxs-lookup"><span data-stu-id="605c8-106">Gaze tells you where the user is looking in the world and lets you determine their intent.</span></span> <span data-ttu-id="605c8-107">在真實世界中，您將通常探討您想要與互動的物件。</span><span class="sxs-lookup"><span data-stu-id="605c8-107">In the real world, you'll typically look at an object that you intend to interact with.</span></span> <span data-ttu-id="605c8-108">這是相同的視線。</span><span class="sxs-lookup"><span data-stu-id="605c8-108">This is the same with gaze.</span></span>

<span data-ttu-id="605c8-109">混合的實境耳機使用位置和您的使用者標頭的方向，以判斷其前端的視線向量。</span><span class="sxs-lookup"><span data-stu-id="605c8-109">Mixed reality headsets use the position and orientation of your user's head to determine their head gaze vector.</span></span> <span data-ttu-id="605c8-110">您可以想像這個向量的雷射指標直接繼續從直接在使用者的眼睛之間。</span><span class="sxs-lookup"><span data-stu-id="605c8-110">You can think of this vector as a laser pointer straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="605c8-111">使用者看起來房間周圍，因為您的應用程式有交集使用它自己全像投影和與此光線[空間對應](spatial-mapping.md)網狀結構來判斷您的使用者可能會看到什麼虛擬或實際物件。</span><span class="sxs-lookup"><span data-stu-id="605c8-111">As the user looks around the room, your application can intersect this ray, both with its own holograms and with the [spatial mapping](spatial-mapping.md) mesh to determine what virtual or real-world object your user may be looking at.</span></span>

<span data-ttu-id="605c8-112">HoloLens 2 上的互動可以使用者的前端視線，眼睛視線的目標或透過附近或到目前為止送互動。</span><span class="sxs-lookup"><span data-stu-id="605c8-112">On HoloLens 2, interactions can be targeted by either the user's head gaze, eye gaze or through near or far hand interactions.</span></span>
<span data-ttu-id="605c8-113">HoloLens 上 （第 1 代），互動應該通常衍生其目標從使用者的前端的視線，而不是嘗試轉譯，或直接互動的游標位置。</span><span class="sxs-lookup"><span data-stu-id="605c8-113">On HoloLens (1st gen), interactions should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="605c8-114">一旦啟動互動，相對的左手邊的動作可能會用來控制[筆勢](gestures.md)，如同[操作或瀏覽](gestures.md#composite-gestures)筆勢。</span><span class="sxs-lookup"><span data-stu-id="605c8-114">Once an interaction has started, relative motions of the hand may be used to control the [gesture](gestures.md), as with the [manipulation or navigation](gestures.md#composite-gestures) gesture.</span></span> <span data-ttu-id="605c8-115">使用沈浸式耳機，您可以針對使用其中一個前端的視線或指向-能夠[動作控制器](motion-controllers.md)。</span><span class="sxs-lookup"><span data-stu-id="605c8-115">With immersive headsets, you can target using either head gaze or pointing-capable [motion controllers](motion-controllers.md).</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a><span data-ttu-id="605c8-116">裝置支援</span><span class="sxs-lookup"><span data-stu-id="605c8-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="605c8-117"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="605c8-117"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="605c8-118"><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="605c8-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="605c8-119"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="605c8-119"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="605c8-120"><a href="immersive-headset-hardware-details.md"><strong>沈浸式耳機</strong></a></span><span class="sxs-lookup"><span data-stu-id="605c8-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="605c8-121">Head 視線</span><span class="sxs-lookup"><span data-stu-id="605c8-121">Head gaze</span></span></td>
        <td><span data-ttu-id="605c8-122">✔️</span><span class="sxs-lookup"><span data-stu-id="605c8-122">✔️</span></span></td>
        <td><span data-ttu-id="605c8-123">✔️</span><span class="sxs-lookup"><span data-stu-id="605c8-123">✔️</span></span></td>
        <td><span data-ttu-id="605c8-124">✔️</span><span class="sxs-lookup"><span data-stu-id="605c8-124">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="605c8-125">眼睛視線</span><span class="sxs-lookup"><span data-stu-id="605c8-125">Eye gaze</span></span></td>
        <td><span data-ttu-id="605c8-126">❌</span><span class="sxs-lookup"><span data-stu-id="605c8-126">❌</span></span></td>
        <td><span data-ttu-id="605c8-127">✔️</span><span class="sxs-lookup"><span data-stu-id="605c8-127">✔️</span></span></td>
        <td><span data-ttu-id="605c8-128">❌</span><span class="sxs-lookup"><span data-stu-id="605c8-128">❌</span></span></td>
    </tr>
</table>

> [!NOTE]
> <span data-ttu-id="605c8-129">HoloLens 2 的特定的詳細指引[即將推出](index.md#news-and-notes)。</span><span class="sxs-lookup"><span data-stu-id="605c8-129">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>


## <a name="uses-of-gaze"></a><span data-ttu-id="605c8-130">視線的用途</span><span class="sxs-lookup"><span data-stu-id="605c8-130">Uses of gaze</span></span>

<span data-ttu-id="605c8-131">混合的實境開發人員，您可以執行許多與標頭或眼睛視線：</span><span class="sxs-lookup"><span data-stu-id="605c8-131">As a mixed reality developer, you can do a lot with head or eye gaze:</span></span>
* <span data-ttu-id="605c8-132">您的應用程式有交集視線全像投影場景中使用以判斷使用者的注意力所在。</span><span class="sxs-lookup"><span data-stu-id="605c8-132">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is.</span></span>
* <span data-ttu-id="605c8-133">您的應用程式筆勢和根據使用者的視線，讓使用者選取、 啟動、 擷取、 捲動，或否則互動及其全像投影的控制器動作目標。</span><span class="sxs-lookup"><span data-stu-id="605c8-133">Your app can target gestures and controller presses based on the user's gaze, letting the user select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="605c8-134">您的應用程式可以讓使用者加全像投影在真實世界表面上交集空間對應網狀結構其視線無限遠的光線。</span><span class="sxs-lookup"><span data-stu-id="605c8-134">Your app can let the user place holograms on real-world surfaces, by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="605c8-135">您的應用程式可以知道使用者何時*不*尋找重要的物件，可能會導致您的應用程式，提供視覺與音訊提示，可針對該物件所開啟的方向。</span><span class="sxs-lookup"><span data-stu-id="605c8-135">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

## <a name="cursor"></a><span data-ttu-id="605c8-136">資料指標</span><span class="sxs-lookup"><span data-stu-id="605c8-136">Cursor</span></span>

<span data-ttu-id="605c8-137">針對前端的視線，大部分的應用程式應該使用[游標](cursors.md)（或其他聽覺/visual 指示） 給使用者的信心，在他們要進行互動。</span><span class="sxs-lookup"><span data-stu-id="605c8-137">For head gaze, most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="605c8-138">您通常會放置在其前端的視線光線先相交的物件，可能是雷射或實際介面的世界中的這個資料指標。</span><span class="sxs-lookup"><span data-stu-id="605c8-138">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span>

<span data-ttu-id="605c8-139">![若要顯示視線範例視覺化資料指標](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="605c8-139">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
<span data-ttu-id="605c8-140">*若要顯示視線範例視覺化資料指標*</span><span class="sxs-lookup"><span data-stu-id="605c8-140">*An example visual cursor to show gaze*</span></span>

<span data-ttu-id="605c8-141">眼睛視線，我們通常建議*不*這可能使得和惱人的使用者很快就會顯示資料指標。</span><span class="sxs-lookup"><span data-stu-id="605c8-141">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="605c8-142">相反地稍微反白顯示視覺的目標，或使用非常模糊的眼睛資料指標來提供有關使用者是要互動的信心。</span><span class="sxs-lookup"><span data-stu-id="605c8-142">Instead subtly highlight visual targets or use a very faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="605c8-143">如需詳細資訊，請查看我們[的設計指引眼睛式輸入](eye-tracking.md)HoloLens 2 上。</span><span class="sxs-lookup"><span data-stu-id="605c8-143">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>

## <a name="giving-action-to-the-users-gaze"></a><span data-ttu-id="605c8-144">讓使用者的視線動作</span><span class="sxs-lookup"><span data-stu-id="605c8-144">Giving action to the user's gaze</span></span>

<span data-ttu-id="605c8-145">一旦使用者已針對全像或使用其視線的真實物件，其下一個步驟是該物件上採取動作。</span><span class="sxs-lookup"><span data-stu-id="605c8-145">Once the user has targeted a hologram or real-world object using their gaze, their next step is to take action on that object.</span></span> <span data-ttu-id="605c8-146">讓使用者以採取動作的主要方式是透過[筆勢](gestures.md)，[動作控制站](motion-controllers.md)並[語音](voice-input.md)。</span><span class="sxs-lookup"><span data-stu-id="605c8-146">The primary ways for a user to take action are through [gestures](gestures.md), [motion controllers](motion-controllers.md) and [voice](voice-input.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="605c8-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="605c8-147">See also</span></span>
* [<span data-ttu-id="605c8-148">MR Input 210：Head 視線</span><span class="sxs-lookup"><span data-stu-id="605c8-148">MR Input 210: Head gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="605c8-149">DirectX 中的頭部和眼睛目光</span><span class="sxs-lookup"><span data-stu-id="605c8-149">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="605c8-150">在 Unity 中的標頭視線</span><span class="sxs-lookup"><span data-stu-id="605c8-150">Head gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="605c8-151">HoloLens 2 上追蹤</span><span class="sxs-lookup"><span data-stu-id="605c8-151">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="605c8-152">在 Unity 中使用混合實境工具組的眼睛視線</span><span class="sxs-lookup"><span data-stu-id="605c8-152">Eye gaze in Unity using Mixed Reality Toolkit</span></span>](https://aka.ms/mrtk-eyes)
