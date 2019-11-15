---
title: 游標
description: 目標向量的游標或指標會提供持續的意見反應，讓使用者瞭解 HoloLens 瞭解其意圖。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens （第1代），HoloLens 2，混合現實，游標，目標，注視，手勢
ms.openlocfilehash: 719e7a573e8c8bc682ec0f960d9f3c8f8c8e5a4a
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105745"
---
# <a name="cursors"></a><span data-ttu-id="d5ea7-104">游標</span><span class="sxs-lookup"><span data-stu-id="d5ea7-104">Cursors</span></span>

![游標](images/UX/UX_Hero_Cursor.jpg)

<span data-ttu-id="d5ea7-106">您目前目標向量的游標或指標，可提供持續的意見反應，讓使用者瞭解耳機在該時間的目前焦點。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-106">A cursor, or indicator of your current targeting vector, provides continuous feedback for the user to understand where the headset believes their current focus is at that time.</span></span> <span data-ttu-id="d5ea7-107">游標可讓使用者瞭解其目前的目標點並做為意見反應，以指出哪些區域、全息影像或點將回應輸入。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-107">The cursor allows the user to understand their current targeting point and acts as feedback to indicate what area, hologram, or point will respond to input.</span></span> <span data-ttu-id="d5ea7-108">此數位代表裝置瞭解使用者注意的位置（不過，這可能不會與決定其意圖的任何內容一樣）。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-108">It is the digital representation of where the device understands the user's attention to be (though that may not be the same as determining anything about their intentions).</span></span>

<span data-ttu-id="d5ea7-109">資料指標所提供的意見可讓使用者預測系統的回應方式、使用該信號作為意見反應，以更適當地將其意圖傳達給裝置，最後更有把握其互動。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-109">The feedback provided by the cursor offers users the ability to anticipate how the system will respond, use that signal as feedback to better communicate their intention to the device, and ultimately be more confident about their interactions.</span></span>

<span data-ttu-id="d5ea7-110">有3種類型的資料指標：**手指、光線**和**列印頭**。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-110">There are 3 kinds of cursors: **finger, ray**, and **head-gaze**.</span></span> <span data-ttu-id="d5ea7-111">這些指標游標在 HoloLens、HoloLens 2 和沉浸式耳機上使用不同的輸入形式。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-111">These pointing cursors work with different input modalities on HoloLens, HoloLens 2, and immersive headsets.</span></span> <span data-ttu-id="d5ea7-112">以下是每一種類型的耳機和互動模型所要使用之資料指標類型的指引。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-112">Below is guidance on which type of cursor to use for each type of headset and interaction model.</span></span> <span data-ttu-id="d5ea7-113">在混合式現實工具組（MRTK）中，我們建立了拖放資料指標模組，協助您建立正確的指標體驗。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-113">In the Mixed Reality Toolkit (MRTK), we've created drag-and-drop cursors modules to help you build the right pointing experience.</span></span>


## <a name="device-support"></a><span data-ttu-id="d5ea7-114">裝置支援</span><span class="sxs-lookup"><span data-stu-id="d5ea7-114">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d5ea7-115"><strong>特徵</strong></span><span class="sxs-lookup"><span data-stu-id="d5ea7-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="d5ea7-116"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="d5ea7-116"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="d5ea7-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="d5ea7-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="d5ea7-118"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="d5ea7-118"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d5ea7-119">手指游標</span><span class="sxs-lookup"><span data-stu-id="d5ea7-119">Finger cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="d5ea7-120">✔️</span><span class="sxs-lookup"><span data-stu-id="d5ea7-120">✔️</span></span></td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="d5ea7-121">光線游標</span><span class="sxs-lookup"><span data-stu-id="d5ea7-121">Ray cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="d5ea7-122">✔️</span><span class="sxs-lookup"><span data-stu-id="d5ea7-122">✔️</span></span></td>
        <td><span data-ttu-id="d5ea7-123">✔️</span><span class="sxs-lookup"><span data-stu-id="d5ea7-123">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="d5ea7-124">列印頭游標</span><span class="sxs-lookup"><span data-stu-id="d5ea7-124">Head-gaze cursor</span></span></td>
        <td><span data-ttu-id="d5ea7-125">✔️</span><span class="sxs-lookup"><span data-stu-id="d5ea7-125">✔️</span></span></td>
        <td><span data-ttu-id="d5ea7-126">✔️</span><span class="sxs-lookup"><span data-stu-id="d5ea7-126">✔️</span></span></td>
        <td><span data-ttu-id="d5ea7-127">✔️</span><span class="sxs-lookup"><span data-stu-id="d5ea7-127">✔️</span></span></td>
    </tr>
</table>

## <a name="finger-cursor"></a><span data-ttu-id="d5ea7-128">手指游標</span><span class="sxs-lookup"><span data-stu-id="d5ea7-128">Finger cursor</span></span>
<span data-ttu-id="d5ea7-129">手指游標僅適用于 HoloLens 2，以加強「[直接操作手](direct-manipulation.md)入」互動模式。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-129">The finger cursor is available only on the HoloLens 2 to enhance the "[direct manipulation with hands](direct-manipulation.md)" interaction mode.</span></span> <span data-ttu-id="d5ea7-130">為了進一步瞭解手指指向何處，我們已將環形連接到兩個索引手指的秘訣。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-130">To better understand where the finger is pointing, we have attached rings to the tips of both index fingers.</span></span> <span data-ttu-id="d5ea7-131">信號大小是以手指與 UI 介面的近距離為基礎（手指越接近，環形越小），當手指與 UI 接觸時，就會縮小為點形狀。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-131">The ring size is based on the proximity of the finger to the UI surface (the closer the finger, the smaller the ring) and will shrink to a dot shape when the finger makes contact with the UI.</span></span> <br>

<span data-ttu-id="d5ea7-132">![手指游標](images/finger-cursor.png)</span><span class="sxs-lookup"><span data-stu-id="d5ea7-132">![finger cursor](images/finger-cursor.png)</span></span><br>
<span data-ttu-id="d5ea7-133">**手指游標1的視覺意見反應狀態**：環形會縮小為點。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-133">**Visual feedback states of finger cursor** 1: The ring shrinks to a dot.</span></span> <span data-ttu-id="d5ea7-134">2：環形會與 surface 對齊。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-134">2: The ring aligns with surface.</span></span> <span data-ttu-id="d5ea7-135">3：環形會與手指向量垂直。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-135">3: The ring is perpendicular to finger vector.</span></span> <span data-ttu-id="d5ea7-136">4：無信號。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-136">4: No ring.</span></span>

## <a name="ray-cursor"></a><span data-ttu-id="d5ea7-137">光線游標</span><span class="sxs-lookup"><span data-stu-id="d5ea7-137">Ray cursor</span></span>
<span data-ttu-id="d5ea7-138">光線游標會附加到最接近的放射處，以允許操作不在手中的物件。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-138">Ray cursors attach to the end of far pointing rays to allow manipulation of objects that are out of hands-reach.</span></span> <span data-ttu-id="d5ea7-139">在沉浸式耳機中，光線會從動作控制器開始，並以點游標結束。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-139">In immersive headsets, the rays shoot out from motion controllers and end in dot cursors.</span></span> <span data-ttu-id="d5ea7-140">在 HoloLens 2 中，我們運用了這些運動控制器光線的心理模型，並設計出來自手掌和結尾的光線，而這些資料指標與直接操作中使用的手指游標一致。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-140">In HoloLens 2, we leverage the mental model of these motion controller rays and designed hand rays that originate from the palms and end in ring-shaped cursors that are consistent with finger cursors used in direct manipulation.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="d5ea7-141">![光線資料指標控制器](images/ray-cursor-controller.png)</span><span class="sxs-lookup"><span data-stu-id="d5ea7-141">![Ray cursor controller](images/ray-cursor-controller.png)</span></span><br>
        <span data-ttu-id="d5ea7-142">**動作控制器的光線游標**</span><span class="sxs-lookup"><span data-stu-id="d5ea7-142">**Ray cursors of motion controllers**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="d5ea7-143">![光線游標手](images/ray-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="d5ea7-143">![Ray cursor hand](images/ray-cursor-hand.png)</span></span><br>
        <span data-ttu-id="d5ea7-144">**手的光線游標**</span><span class="sxs-lookup"><span data-stu-id="d5ea7-144">**Ray cursors of hands**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="head-gaze-cursor"></a><span data-ttu-id="d5ea7-145">列印頭游標</span><span class="sxs-lookup"><span data-stu-id="d5ea7-145">Head-gaze cursor</span></span>
<span data-ttu-id="d5ea7-146">前端游標是一個點，它會附加至不可見的標頭注視向量的尾端，而這會使用標頭的位置和旋轉。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-146">The head-gaze cursor is a dot that attaches to the end of an invisible head-gaze vector that uses the position and rotation of the head to point.</span></span> <span data-ttu-id="d5ea7-147">若要執行動作，此指標會與各種認可輸入配對，例如空中碰、語音命令、停留和按下按鈕。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-147">To execute actions, this pointing cursor is paired with various commit inputs such as air tap, voice commands, dwell, and button press.</span></span> <span data-ttu-id="d5ea7-148">在 HoloLens 2 中，列印頭最適合與任何不是按下的認可輸入配對，因為在空中點與目前的手片之間會發生互動衝突。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-148">In HoloLens 2, head-gaze is best paired with any commit input that is not air tap, as there will be interaction conflict between air tap and far hand rays.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="d5ea7-149">![Head 注視游標手](images/head-gaze-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="d5ea7-149">![Head gaze cursor hand](images/head-gaze-cursor-hand.png)</span></span><br>
        <span data-ttu-id="d5ea7-150">**具有手形手勢的頭部注視游標**</span><span class="sxs-lookup"><span data-stu-id="d5ea7-150">**Head-gaze cursor with hand gesture**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="d5ea7-151">![Head 注視游標語音](images/head-gaze-cursor-voice.png)</span><span class="sxs-lookup"><span data-stu-id="d5ea7-151">![Head gaze cursor voice](images/head-gaze-cursor-voice.png)</span></span><br>
        <span data-ttu-id="d5ea7-152">**具有語音命令的頭部注視游標**</span><span class="sxs-lookup"><span data-stu-id="d5ea7-152">**Head-gaze cursor with voice command**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="cursor-customization-recommendations"></a><span data-ttu-id="d5ea7-153">資料指標自訂建議</span><span class="sxs-lookup"><span data-stu-id="d5ea7-153">Cursor customization recommendations</span></span>
<span data-ttu-id="d5ea7-154">如果您想要自訂資料指標的意見反應行為和外觀，以下是一些設計建議：</span><span class="sxs-lookup"><span data-stu-id="d5ea7-154">If you would like to customize the cursor feedback behaviors and appearances, here are some design recommendations:</span></span>

### <a name="cursor-scale"></a><span data-ttu-id="d5ea7-155">資料指標縮放</span><span class="sxs-lookup"><span data-stu-id="d5ea7-155">Cursor scale</span></span>
* <span data-ttu-id="d5ea7-156">游標不應大於可用的目標，讓使用者可以輕鬆地與內容互動並加以查看。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-156">The cursor should be no larger than the available targets, allowing users to easily interact with and view the content.</span></span>
* <span data-ttu-id="d5ea7-157">根據您所建立的經驗，在使用者查看時調整資料指標也是很重要的考慮。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-157">Depending on the experience you create, scaling the cursor as the user looks around is also an important consideration.</span></span> <span data-ttu-id="d5ea7-158">例如，當使用者進一步探討您的經驗時，游標應該不會變得太小，以致遺失。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-158">For example, as the user looks further away in your experience, the cursor should not become too small such that it's lost.</span></span>
* <span data-ttu-id="d5ea7-159">調整游標時，請考慮將軟動畫套用至它，因為它會調整以讓它成為一種有機的感覺。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-159">When scaling the cursor, consider applying a soft animation to it as it scales to give it an organic feeling.</span></span>
* <span data-ttu-id="d5ea7-160">避免阻礙內容。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-160">Avoid obstructing content.</span></span> <span data-ttu-id="d5ea7-161">全像投影是讓體驗更容易記住，而游標不應離開的情況。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-161">Holograms are what make the experience memorable and the cursor should not be taking away from them.</span></span>

### <a name="directionless-cursor-shape"></a><span data-ttu-id="d5ea7-162">Directionless cursor 圖形</span><span class="sxs-lookup"><span data-stu-id="d5ea7-162">Directionless cursor shape</span></span>
* <span data-ttu-id="d5ea7-163">雖然沒有一個右資料指標圖形，但我們建議您使用 directionless 圖形，例如圓環。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-163">Although there is no one right cursor shape, we recommend that you use a directionless shape like a torus.</span></span> <span data-ttu-id="d5ea7-164">指向某個方向的游標（例如，傳統箭號游標）可能會讓使用者感到困惑。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-164">A cursor that points in some direction (For example, a traditional arrow cursor) might confuse the user to always look that way.</span></span>
* <span data-ttu-id="d5ea7-165">當使用資料指標將互動指示傳達給使用者時，就會發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-165">An exception to this is when using the cursor to communicate interaction instruction to the user.</span></span> <span data-ttu-id="d5ea7-166">例如，在混合現實 OS 中調整全息影像時，游標會暫時包含箭號，以指示使用者如何移動其手來調整全息形狀。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-166">For example, when scaling holograms in the Mixed Reality OS, the cursor temporarily includes arrows that instructs the user on how to move their hand to scale the hologram.</span></span>

### <a name="look-and-feel"></a><span data-ttu-id="d5ea7-167">外觀與風格</span><span class="sxs-lookup"><span data-stu-id="d5ea7-167">Look and feel</span></span>
* <span data-ttu-id="d5ea7-168">環圈圖或環圈形的游標適用于許多應用程式。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-168">A donut or torus shaped cursor works for a lot of applications.</span></span>
* <span data-ttu-id="d5ea7-169">挑選最能代表您所建立之體驗的色彩和形狀。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-169">Pick a color and shape that best represents the experience you are creating.</span></span>
* <span data-ttu-id="d5ea7-170">資料指標特別容易[分色](hologram-stability.md#color-separation)。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-170">Cursors are especially prone to [color separation](hologram-stability.md#color-separation).</span></span>
* <span data-ttu-id="d5ea7-171">具有平衡之不透明度的小型資料指標會讓它具有資訊，而不會支配視覺階層。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-171">A small cursor with balanced opacity keeps it informative without dominating the visual hierarchy.</span></span>
* <span data-ttu-id="d5ea7-172">請 cognizant 在您的游標後方使用陰影或反白顯示，因為它們可能會妨礙內容，並會與手邊的工作進行干擾。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-172">Be cognizant of using shadows or highlights behind your cursor as they might obstruct content and distract from the task at hand.</span></span>
* <span data-ttu-id="d5ea7-173">游標應該對齊並在您的應用程式中將介面結合在一起，這會讓使用者覺得系統可以查看他們的外觀，但系統也知道其周圍的環境。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-173">Cursors should align to and hug the surfaces in your app, this will give the user a feeling that the system can see where they are looking, but also that the system is aware of their surroundings.</span></span> <span data-ttu-id="d5ea7-174">例如，在混合現實的作業系統中，游標會與使用者的世界表面一致，即使使用者不是直接在全息圖上，也能感受到世界的認知。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-174">For example, in the Mixed Reality OS, the cursor aligns to the surfaces of the user's world, creating a feeling of awareness of the world even when the user isn't looking directly at a hologram.</span></span>
* <span data-ttu-id="d5ea7-175">將游標移至接近近近的位置時，會將游標鎖定到互動式元素，有助於改善使用者在執行選取動作時與該元素互動的信心。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-175">Magnetically locking the cursor to an interactive element when it is within close proximity can help improve confidence that user will interact with that element when they perform a selection action.</span></span>

### <a name="visual-cues"></a><span data-ttu-id="d5ea7-176">視覺提示</span><span class="sxs-lookup"><span data-stu-id="d5ea7-176">Visual cues</span></span>
* <span data-ttu-id="d5ea7-177">如果您的經驗著重于單一的全息圖形，則您的游標應該只在您離開該全像投影時，才對齊和縮小全像投影和變更形狀。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-177">If your experience is focused on a single hologram, your cursor should align and hug only that hologram and change shape when you look away from that hologram.</span></span> <span data-ttu-id="d5ea7-178">這可以向使用者傳達可操作的全像投影，而且可以與它互動。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-178">This can convey to the user that the hologram is actionable and they can interact with it.</span></span>
* <span data-ttu-id="d5ea7-179">如果您的應用程式使用空間對應，則您的游標可以對齊它所看到的每個介面並對其進行結合。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-179">If your application uses spatial mapping, then your cursor could align and hug every surface it sees.</span></span> <span data-ttu-id="d5ea7-180">這會對 HoloLens 和您的應用程式可以查看其空間的使用者提供意見反應。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-180">This gives feedback to the users that HoloLens and your application can see their space.</span></span> <span data-ttu-id="d5ea7-181">這強調了全息影像在世界各地的真實情況，並協助填補 real 與 virtual 之間的橋樑。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-181">This reinforces the fact that holograms are real and in our world and helps bridge the gap between real and virtual.</span></span>
* <span data-ttu-id="d5ea7-182">瞭解游標在視圖中沒有任何全息影像或表面時應執行的動作。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-182">Have an idea of what the cursor should do when there are no holograms or surfaces in view.</span></span> <span data-ttu-id="d5ea7-183">將它放在使用者前方預先決定的距離，是一個選項。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-183">Placing it at a predetermined distance in front of the user is one option.</span></span>

### <a name="possible-actions"></a><span data-ttu-id="d5ea7-184">可能的動作</span><span class="sxs-lookup"><span data-stu-id="d5ea7-184">Possible actions</span></span>
* <span data-ttu-id="d5ea7-185">游標可以由不同的圖示表示，以傳達可執行檔動作，例如縮放或旋轉。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-185">The cursor can be represented by different icons to convey possible actions a hologram can perform, such as scaling or rotation.</span></span>
* <span data-ttu-id="d5ea7-186">只有在資料指標表示使用者的情況時，才將額外的資訊新增至游標處。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-186">Only add extra information on the cursor if it means something to the user.</span></span> <span data-ttu-id="d5ea7-187">否則，使用者可能不會注意到狀態變更或資料指標混淆。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-187">Otherwise, users might either not notice the state changes or get confused by the cursor.</span></span>

### <a name="input-state"></a><span data-ttu-id="d5ea7-188">輸入狀態</span><span class="sxs-lookup"><span data-stu-id="d5ea7-188">Input state</span></span>
* <span data-ttu-id="d5ea7-189">我們可以使用游標來顯示使用者的輸入狀態或意圖。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-189">We could use the cursor to display the user's input state or intent.</span></span> <span data-ttu-id="d5ea7-190">例如，我們可以顯示一個圖示，告訴使用者系統看到他們的手上狀態，而且應用程式知道他們已經準備好採取行動。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-190">For example, we could display an icon telling the user the system sees their hand state and that the application knows they are ready to take action.</span></span>
* <span data-ttu-id="d5ea7-191">我們也可以使用游標，向使用者顯示系統透過暫時的色彩變更聽到了語音命令</span><span class="sxs-lookup"><span data-stu-id="d5ea7-191">We could also use the cursor to show users that voice commands have been heard by the system via a momentary color chang</span></span>

* <span data-ttu-id="d5ea7-192">下列資料指標狀態可以用不同的方式來執行。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-192">The following cursor states can be implemented in different ways.</span></span> <span data-ttu-id="d5ea7-193">您可以藉由將資料指標模型化，例如狀態機器，來執行這些不同的狀態。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-193">You might implement these different states by modeling the cursor like a state machine.</span></span> <span data-ttu-id="d5ea7-194">例如：</span><span class="sxs-lookup"><span data-stu-id="d5ea7-194">For example:</span></span>
    * <span data-ttu-id="d5ea7-195">[閒置] 狀態是您在其中顯示預設資料指標的位置。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-195">Idle state is where you show the default cursor.</span></span>
    * <span data-ttu-id="d5ea7-196">[就緒] 狀態是在您偵測到使用者已準備就緒的位置時。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-196">Ready state is when you have detected the user's hand in the ready position.</span></span>
    * <span data-ttu-id="d5ea7-197">當使用者執行特定互動時，互動狀態就是。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-197">Interaction state is when the user is performing a particular interaction.</span></span>
    * <span data-ttu-id="d5ea7-198">當您傳達可在全像投影上執行的可能動作時，可能的動作狀態或暫留狀態。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-198">Possible Actions state or hover state is when you convey possible actions that can be performed on a hologram.</span></span>

<span data-ttu-id="d5ea7-199">您也可以採用外觀的方式來執行這些狀態，讓您可以在偵測到不同的狀態時顯示不同的藝術資產。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-199">You could also implement these states in a skin-able manner such that you can display different art assets when different states are detected.</span></span>

<br>

---


## <a name="going-cursor-free"></a><span data-ttu-id="d5ea7-200">進入「無資料指標」</span><span class="sxs-lookup"><span data-stu-id="d5ea7-200">Going "cursor-free"</span></span>
<span data-ttu-id="d5ea7-201">當深度的意義是經驗的重要元件，而且當指標互動（透過注視和手勢）不需要精確的精確度時，建議您使用不含資料指標的設計。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-201">Designing without a cursor is recommended when the sense of immersion is a key component of an experience and when pointing interactions (through gaze and gesture) do not require great precision.</span></span> <span data-ttu-id="d5ea7-202">系統仍然必須符合資料指標通常符合的需求，方法是提供使用者對其指標的持續意見反應，並協助他們安心地將其意圖傳達給系統。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-202">The system must still meet the needs that are normally met by a cursor by providing users with continuous feedback on the system's understanding of their pointing and helping them to confidently communicate their intentions to the system.</span></span> <span data-ttu-id="d5ea7-203">這可能會透過其他明顯的狀態變更來達成。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-203">This may be achievable through other noticeable state changes.</span></span>

<br>

---

## <a name="cursor-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="d5ea7-204">適用于 Unity 的 MRTK （混合現實工具組）中的游標</span><span class="sxs-lookup"><span data-stu-id="d5ea7-204">Cursor in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="d5ea7-205">根據預設， **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 會提供游標 Prefab （[DefaultCursor. prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)），其具有與 shell 的系統資料指標相同的視覺狀態。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-205">By default, **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides a cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) which has the same visual state as the shell's system cursor.</span></span> <span data-ttu-id="d5ea7-206">它會在 MRTK 的輸入設定檔的 [指標] 底下指派。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-206">It is assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="d5ea7-207">您可以為您的經驗取代/自訂此資料指標。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-207">You can replace/customize this cursor for your experience.</span></span> <span data-ttu-id="d5ea7-208">針對眼睛追蹤輸入的經驗，MRTK 也提供 EyeGazeCursor，其中具有微妙的視覺效果可將干擾降至最低。</span><span class="sxs-lookup"><span data-stu-id="d5ea7-208">For the experience with eye-tracking input, MRTK also provides EyeGazeCursor which has subtle visual to minimize the distraction.</span></span>

* [<span data-ttu-id="d5ea7-209">MRTK-指標設定檔</span><span class="sxs-lookup"><span data-stu-id="d5ea7-209">MRTK - Pointer profile</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [<span data-ttu-id="d5ea7-210">MRTK-輸入系統</span><span class="sxs-lookup"><span data-stu-id="d5ea7-210">MRTK - Input system</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [<span data-ttu-id="d5ea7-211">MRTK-指標</span><span class="sxs-lookup"><span data-stu-id="d5ea7-211">MRTK - Pointers</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)


---

## <a name="see-also"></a><span data-ttu-id="d5ea7-212">請參閱</span><span class="sxs-lookup"><span data-stu-id="d5ea7-212">See also</span></span>
* [<span data-ttu-id="d5ea7-213">筆勢</span><span class="sxs-lookup"><span data-stu-id="d5ea7-213">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="d5ea7-214">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="d5ea7-214">Head-gaze and commit</span></span>](gaze-and-commit.md)
