---
title: 互動的基本概念
description: 如我們所建置的體驗，跨 HoloLens （第 1 代）、 HoloLens 2 和沈浸式耳機，我們已經開始寫下可共用，我們發現的一些事項。
author: rwinj
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 混合實境，互動，設計
ms.openlocfilehash: d594126529b6314a4706f8b6b6af856058c3280a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591128"
---
# <a name="interaction-fundamentals"></a><span data-ttu-id="60c30-104">互動的基本概念</span><span class="sxs-lookup"><span data-stu-id="60c30-104">Interaction fundamentals</span></span>

<span data-ttu-id="60c30-105">如我們所建置的體驗，跨 HoloLens 和沈浸式耳機，我們已經開始寫下可共用，我們發現的一些事項。</span><span class="sxs-lookup"><span data-stu-id="60c30-105">As we've built experiences across HoloLens and immersive headsets, we've started writing down some things we found useful to share.</span></span> <span data-ttu-id="60c30-106">想像這是基本的建置組塊，混合的實境互動設計。</span><span class="sxs-lookup"><span data-stu-id="60c30-106">Think of these as the fundamental building blocks for mixed reality interaction design.</span></span>

## <a name="device-support"></a><span data-ttu-id="60c30-107">裝置支援</span><span class="sxs-lookup"><span data-stu-id="60c30-107">Device support</span></span>

<span data-ttu-id="60c30-108">以下是套用至已發佈的互動設計文件的裝置類型或類型的外框。</span><span class="sxs-lookup"><span data-stu-id="60c30-108">Here's an outline of the available Interaction design articles and which device type or types they apply to.</span></span>
<br>

<table>

<th>
<tr>

<td style="width:150px;"><span data-ttu-id="60c30-109"><strong>輸入</strong></span><span class="sxs-lookup"><span data-stu-id="60c30-109"><strong>Input</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="60c30-110"><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="60c30-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="60c30-111"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="60c30-111"><strong>HoloLens 2</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="60c30-112"><a href="immersive-headset-hardware-details.md"><strong>沈浸式耳機</strong></a></span><span class="sxs-lookup"><span data-stu-id="60c30-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
</th>
 
<tr>
<td> <span data-ttu-id="60c30-113"><a href="gestures.md">相互連貫的指針</a></span><span class="sxs-lookup"><span data-stu-id="60c30-113"><a href="gestures.md">Articulated hands</a></span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="60c30-114">✔️</span><span class="sxs-lookup"><span data-stu-id="60c30-114">✔️</span></span></td><td></td>

</tr><tr>
<td> <span data-ttu-id="60c30-115"><a href="gaze-targeting.md">眼睛目標</a></span><span class="sxs-lookup"><span data-stu-id="60c30-115"><a href="gaze-targeting.md">Eye targeting</a></span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="60c30-116">✔️</span><span class="sxs-lookup"><span data-stu-id="60c30-116">✔️</span></span></td><td style="text-align: center;"></td>
</tr><tr>
<td> <span data-ttu-id="60c30-117"><a href="gaze-targeting.md">為目標的視線</a></span><span class="sxs-lookup"><span data-stu-id="60c30-117"><a href="gaze-targeting.md">Gaze targeting</a></span></span></td><td style="text-align: center;"><span data-ttu-id="60c30-118">✔️</span><span class="sxs-lookup"><span data-stu-id="60c30-118">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="60c30-119">✔️</span><span class="sxs-lookup"><span data-stu-id="60c30-119">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="60c30-120">✔️</span><span class="sxs-lookup"><span data-stu-id="60c30-120">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="60c30-121"><a href="gestures.md">筆勢</a></span><span class="sxs-lookup"><span data-stu-id="60c30-121"><a href="gestures.md">Gestures</a></span></span></td><td style="text-align: center;"><span data-ttu-id="60c30-122">✔️</span><span class="sxs-lookup"><span data-stu-id="60c30-122">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="60c30-123">✔️</span><span class="sxs-lookup"><span data-stu-id="60c30-123">✔️</span></span></td><td></td>
</tr><tr>
<td> <span data-ttu-id="60c30-124"><a href="voice-design.md">語音設計</a></span><span class="sxs-lookup"><span data-stu-id="60c30-124"><a href="voice-design.md">Voice design</a></span></span></td><td style="text-align: center;"><span data-ttu-id="60c30-125">✔️</span><span class="sxs-lookup"><span data-stu-id="60c30-125">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="60c30-126">✔️</span><span class="sxs-lookup"><span data-stu-id="60c30-126">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="60c30-127">✔️</span><span class="sxs-lookup"><span data-stu-id="60c30-127">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="60c30-128">遊戲台</span><span class="sxs-lookup"><span data-stu-id="60c30-128">Gamepad</span></span></td><td style="text-align: center;"><span data-ttu-id="60c30-129">✔️</span><span class="sxs-lookup"><span data-stu-id="60c30-129">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="60c30-130">✔️</span><span class="sxs-lookup"><span data-stu-id="60c30-130">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="60c30-131">✔️</span><span class="sxs-lookup"><span data-stu-id="60c30-131">✔️</span></span></td>
</tr>
<tr>
<td> <span data-ttu-id="60c30-132"><a href="motion-controllers.md">動作控制站</a></span><span class="sxs-lookup"><span data-stu-id="60c30-132"><a href="motion-controllers.md">Motion controllers</a></span></span></td><td></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="60c30-133">✔️</span><span class="sxs-lookup"><span data-stu-id="60c30-133">✔️</span></span></td>

</tr>
<th>
<tr>
<td style="width:150px;"><span data-ttu-id="60c30-134"><strong>認知和空間的功能</strong></span><span class="sxs-lookup"><span data-stu-id="60c30-134"><strong>Perception and spatial features</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="60c30-135"><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="60c30-135"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="60c30-136"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="60c30-136"><strong>HoloLens 2</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="60c30-137"><a href="immersive-headset-hardware-details.md"><strong>沈浸式耳機</strong></a></span><span class="sxs-lookup"><span data-stu-id="60c30-137"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
</th>
<tr>

<td> <span data-ttu-id="60c30-138"><a href="spatial-sound-design.md">空間完善的設計</a></span><span class="sxs-lookup"><span data-stu-id="60c30-138"><a href="spatial-sound-design.md">Spatial sound design</a></span></span></td><td style="text-align: center;"><span data-ttu-id="60c30-139">✔️</span><span class="sxs-lookup"><span data-stu-id="60c30-139">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="60c30-140">✔️</span><span class="sxs-lookup"><span data-stu-id="60c30-140">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="60c30-141">✔️</span><span class="sxs-lookup"><span data-stu-id="60c30-141">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="60c30-142"><a href="spatial-mapping-design.md">空間對應設計</a></span><span class="sxs-lookup"><span data-stu-id="60c30-142"><a href="spatial-mapping-design.md">Spatial mapping design</a></span></span></td><td style="text-align: center;"><span data-ttu-id="60c30-143">✔️</span><span class="sxs-lookup"><span data-stu-id="60c30-143">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="60c30-144">✔️</span><span class="sxs-lookup"><span data-stu-id="60c30-144">✔️</span></span></td><td></td>
</tr><tr>
<td> <span data-ttu-id="60c30-145"><a href="hologram.md">全像投影</a></span><span class="sxs-lookup"><span data-stu-id="60c30-145"><a href="hologram.md">Holograms</a></span></span></td><td style="text-align: center;"><span data-ttu-id="60c30-146">✔️</span><span class="sxs-lookup"><span data-stu-id="60c30-146">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="60c30-147">✔️</span><span class="sxs-lookup"><span data-stu-id="60c30-147">✔️</span></span></td><td></td>
</tr>

</table>

## <a name="the-user-is-the-camera"></a><span data-ttu-id="60c30-148">使用者是觀景窗</span><span class="sxs-lookup"><span data-stu-id="60c30-148">The user is the camera</span></span>

![使用者是觀景窗](images/useriscamera-640px.jpg)

<span data-ttu-id="60c30-150">一定會想要針對使用者的觀點來看設計有關他們的實際及虛擬世界中移動。</span><span class="sxs-lookup"><span data-stu-id="60c30-150">Always think about design for your user's point of view as they move about their real and virtual worlds.</span></span>

<span data-ttu-id="60c30-151">**若要詢問的一些問題**</span><span class="sxs-lookup"><span data-stu-id="60c30-151">**Some questions to ask**</span></span>
* <span data-ttu-id="60c30-152">是使用者坐、 reclining、 固定，而且或步行時使用您的體驗嗎？</span><span class="sxs-lookup"><span data-stu-id="60c30-152">Is the user sitting, reclining, standing, or walking while using your experience?</span></span>
* <span data-ttu-id="60c30-153">您的內容如何調整到不同位置？</span><span class="sxs-lookup"><span data-stu-id="60c30-153">How does your content adjust to different positions?</span></span>
* <span data-ttu-id="60c30-154">可以 使用者會調整它嗎？</span><span class="sxs-lookup"><span data-stu-id="60c30-154">Can the user adjust it?</span></span>
* <span data-ttu-id="60c30-155">使用者會輕鬆自如地使用您的應用程式嗎？</span><span class="sxs-lookup"><span data-stu-id="60c30-155">Will the user be comfortable using your app?</span></span>

<span data-ttu-id="60c30-156">**最佳作法**</span><span class="sxs-lookup"><span data-stu-id="60c30-156">**Best practices**</span></span>
* <span data-ttu-id="60c30-157">使用者是數位相機，它們控制移動。</span><span class="sxs-lookup"><span data-stu-id="60c30-157">The user is the camera and they control the movement.</span></span> <span data-ttu-id="60c30-158">讓這些磁碟機。</span><span class="sxs-lookup"><span data-stu-id="60c30-158">Let them drive.</span></span>
* <span data-ttu-id="60c30-159">如果您需要以虛擬方式傳輸使用者時，很容易受 vestibular discomfort 相關問題。</span><span class="sxs-lookup"><span data-stu-id="60c30-159">If you need to virtually transport the user, be sensitive to issues around vestibular discomfort.</span></span>
* <span data-ttu-id="60c30-160">使用較短的動畫</span><span class="sxs-lookup"><span data-stu-id="60c30-160">Use shorter animations</span></span>
* <span data-ttu-id="60c30-161">建立動畫的來源清單/左/右或淡入，而不是 Z</span><span class="sxs-lookup"><span data-stu-id="60c30-161">Animate from down/left/right or fade in instead of Z</span></span>
* <span data-ttu-id="60c30-162">時間變慢</span><span class="sxs-lookup"><span data-stu-id="60c30-162">Slow down timing</span></span>
* <span data-ttu-id="60c30-163">允許使用者會看到在背景中 world</span><span class="sxs-lookup"><span data-stu-id="60c30-163">Allow user to see the world in the background</span></span>

<span data-ttu-id="60c30-164">**要避免的事項**</span><span class="sxs-lookup"><span data-stu-id="60c30-164">**What to avoid**</span></span>
* <span data-ttu-id="60c30-165">不要搖動相機或刻意將其鎖定以 3DOF 只方向 (未轉譯），它可以讓使用者感到不安。</span><span class="sxs-lookup"><span data-stu-id="60c30-165">Don't shake the camera or purposely lock it to 3DOF (only orientation, no translation), it can make users feel uncomfortable.</span></span>
* <span data-ttu-id="60c30-166">任何突然的移動。</span><span class="sxs-lookup"><span data-stu-id="60c30-166">No abrupt movement.</span></span> <span data-ttu-id="60c30-167">如果您需要將內容，或使用者，將它移緩慢且順暢地進行到它們的最大的緩和。</span><span class="sxs-lookup"><span data-stu-id="60c30-167">If you need to bring content to or from the user, move it slowly and smoothly toward them for maximum comfort.</span></span> <span data-ttu-id="60c30-168">即將在它們的大型功能表會因應使用者。</span><span class="sxs-lookup"><span data-stu-id="60c30-168">Users will react to large menus coming at them.</span></span>
* <span data-ttu-id="60c30-169">不能加快速度，或開啟使用者的相機。</span><span class="sxs-lookup"><span data-stu-id="60c30-169">Don't accelerate or turn the user's camera.</span></span> <span data-ttu-id="60c30-170">使用者是區分加速 （angular 和 translational）。</span><span class="sxs-lookup"><span data-stu-id="60c30-170">Users are sensitive to acceleration (both angular and translational).</span></span>

## <a name="leverage-the-users-perspective"></a><span data-ttu-id="60c30-171">利用使用者的觀點來看</span><span class="sxs-lookup"><span data-stu-id="60c30-171">Leverage the user's perspective</span></span>

<span data-ttu-id="60c30-172">使用者會看到沈浸式和全像攝影版的裝置上混合實境，透過顯示的世界。</span><span class="sxs-lookup"><span data-stu-id="60c30-172">Users see the world of mixed reality through displays on immersive and holographic devices.</span></span> <span data-ttu-id="60c30-173">HoloLens，在此顯示稱為[全像攝影版的框架](holographic-frame.md)。</span><span class="sxs-lookup"><span data-stu-id="60c30-173">On the HoloLens, this display is called the [holographic frame](holographic-frame.md).</span></span>

<span data-ttu-id="60c30-174">2D 開發，經常存取的內容和設定可能放個角落的畫面，使其更容易存取。</span><span class="sxs-lookup"><span data-stu-id="60c30-174">In 2D development, frequently accessed content and settings may be placed in the corners of a screen to make them easily accessible.</span></span> <span data-ttu-id="60c30-175">不過，在全像攝影版的應用程式，可能會不想存取的使用者檢視的邊角中的內容。</span><span class="sxs-lookup"><span data-stu-id="60c30-175">However, in holographic apps, content in the corners of the user's view may be uncomfortable to access.</span></span> <span data-ttu-id="60c30-176">在此情況下，全像攝影版的畫面格的中心是內容的主要位置。</span><span class="sxs-lookup"><span data-stu-id="60c30-176">In this case, the center of the holographic frame is the prime location for content.</span></span>

<span data-ttu-id="60c30-177">使用者可能需要指引以協助找出重要的事件或超過其立即檢視的物件。</span><span class="sxs-lookup"><span data-stu-id="60c30-177">The user may need to be guided to help locate important events or objects beyond their immediate view.</span></span> <span data-ttu-id="60c30-178">您可以使用箭號、 淺線索、 字元磁頭移動，思考泡泡、 指標、 空間音效以及語音提示，可協助引導您的應用程式中的重要內容的使用者。</span><span class="sxs-lookup"><span data-stu-id="60c30-178">You can use arrows, light trails, character head movement, thought bubbles, pointers, spatial sound, and voice prompts to help guide the user to important content in your app.</span></span>

<span data-ttu-id="60c30-179">建議您將未鎖定內容至使用者的緩和的畫面。</span><span class="sxs-lookup"><span data-stu-id="60c30-179">It is recommended to not lock content to the screen for the user's comfort.</span></span> <span data-ttu-id="60c30-180">如果您需要保留內容檢視中，將它放在世界各地，讓內容 「 tag-along"，例如 [開始] 功能表。</span><span class="sxs-lookup"><span data-stu-id="60c30-180">If you need to keep content in view, place it in the world and make the content "tag-along" like the Start menu.</span></span> <span data-ttu-id="60c30-181">取得使用者的觀點來看以及提取的內容會覺得在環境中更自然。</span><span class="sxs-lookup"><span data-stu-id="60c30-181">Content that gets pulled along with the user's perspective will feel more natural in the environment.</span></span>

<span data-ttu-id="60c30-182">![[開始] 功能表會到達框架邊緣時，所遵循的使用者檢視](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="60c30-182">![The start menu follows the user's view when it reaches the edge of the frame](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="60c30-183">*[開始] 功能表會到達框架邊緣時，所遵循的使用者檢視*</span><span class="sxs-lookup"><span data-stu-id="60c30-183">*The Start menu follows the user's view when it reaches the edge of the frame*</span></span>

<span data-ttu-id="60c30-184">在 HoloLens，因為沒有取得切掉符合全像攝影版的範圍內時，覺得真正全像投影。</span><span class="sxs-lookup"><span data-stu-id="60c30-184">On HoloLens, holograms feel real when they fit within the holographic frame since they don't get cut off.</span></span> <span data-ttu-id="60c30-185">使用者會移動才能看到雷射範圍內的界限。</span><span class="sxs-lookup"><span data-stu-id="60c30-185">Users will move in order to see the bounds of a hologram within the frame.</span></span> <span data-ttu-id="60c30-186">上 HoloLens，是簡化的使用者檢視，而且可以專注於主要動作上將使用者介面。</span><span class="sxs-lookup"><span data-stu-id="60c30-186">On HoloLens, it's important to simplify your UI to fit within the user's view and keep your focus on the main action.</span></span> <span data-ttu-id="60c30-187">沈浸式耳機，務必維護永續性虛擬世界內裝置的視野的假象。</span><span class="sxs-lookup"><span data-stu-id="60c30-187">For immersive headsets, it's important to maintain the illusion of a persistent virtual world within the device's field of view.</span></span>

## <a name="user-comfort"></a><span data-ttu-id="60c30-188">使用者</span><span class="sxs-lookup"><span data-stu-id="60c30-188">User comfort</span></span>

<span data-ttu-id="60c30-189">若要確保最大[緩和](comfort.md)上掛接標頭的顯示，是很重要的設計人員和開發人員建立，並以模擬人類如何解譯 3D 圖形和物件的相對位置，自然的方式呈現內容世界。</span><span class="sxs-lookup"><span data-stu-id="60c30-189">To ensure maximum [comfort](comfort.md) on head-mounted displays, it’s important for designers and developers to create and present content in a way that mimics how humans interpret 3D shapes and the relative position of objects in the natural world.</span></span> <span data-ttu-id="60c30-190">實體的觀點而言，也很重要的設計不需要的頸部或手臂 fatiguing 動作的內容。</span><span class="sxs-lookup"><span data-stu-id="60c30-190">From a physical perspective, it is also important to design content that does not require fatiguing motions of the neck or arms.</span></span>

<span data-ttu-id="60c30-191">不論開發 HoloLens 或沈浸式耳機，務必轉譯這兩個眼睛的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="60c30-191">Whether developing for HoloLens or immersive headsets, it is important to render visuals for both eyes.</span></span> <span data-ttu-id="60c30-192">轉譯平視顯示窗眼裡一個只可以讓介面難了解，以及造成使用者的注意和大腦 uneasiness。</span><span class="sxs-lookup"><span data-stu-id="60c30-192">Rendering a heads-up display in one eye only can make an interface hard to understand, as well as causing uneasiness to the user's eye and brain.</span></span>

## <a name="share-your-experience"></a><span data-ttu-id="60c30-193">分享您的體驗</span><span class="sxs-lookup"><span data-stu-id="60c30-193">Share your experience</span></span>

<span data-ttu-id="60c30-194">使用[混合實境擷取](mixed-reality-capture.md)，使用者可以擷取相片或視訊的使用者體驗，在任何時間。</span><span class="sxs-lookup"><span data-stu-id="60c30-194">Using [mixed reality capture](mixed-reality-capture.md), users can capture a photo or video of their experience at any time.</span></span> <span data-ttu-id="60c30-195">請考慮您可能要鼓勵快照集或視訊的應用程式中的體驗。</span><span class="sxs-lookup"><span data-stu-id="60c30-195">Consider experiences in your app where you may want to encourage snapshots or videos.</span></span>

## <a name="leverage-basic-ui-elements-of-the-windows-mixed-reality-home"></a><span data-ttu-id="60c30-196">運用基本家用的 Windows Mixed Reality UI 項目</span><span class="sxs-lookup"><span data-stu-id="60c30-196">Leverage basic UI elements of the Windows Mixed Reality home</span></span>

<span data-ttu-id="60c30-197">就像 Windows PC 體驗啟動與桌面時，Windows Mixed Reality，開始於首頁。</span><span class="sxs-lookup"><span data-stu-id="60c30-197">Just like the Windows PC experience starts with the desktop, Windows Mixed Reality starts with the home.</span></span> <span data-ttu-id="60c30-198">[Windows Mixed Reality 家用](navigating-the-windows-mixed-reality-home.md)運用我們對中炫耀都能夠了解，並瀏覽 3D 的地方。</span><span class="sxs-lookup"><span data-stu-id="60c30-198">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) leverages our innate ability to understand and navigate 3D places.</span></span> <span data-ttu-id="60c30-199">HoloLens，您的首頁是您的實體空間。</span><span class="sxs-lookup"><span data-stu-id="60c30-199">With HoloLens, your home is your physical space.</span></span> <span data-ttu-id="60c30-200">沈浸式耳機，與您的首頁會是虛擬的位置。</span><span class="sxs-lookup"><span data-stu-id="60c30-200">With immersive headsets, your home is a virtual place.</span></span>

<span data-ttu-id="60c30-201">您的首頁也是，您將使用 [開始] 功能表開啟，並將應用程式和內容。</span><span class="sxs-lookup"><span data-stu-id="60c30-201">Your home is also where you’ll use the Start menu to open and place apps and content.</span></span> <span data-ttu-id="60c30-202">您可以混合的實境內容中填入您的首頁和 multitask 同時使用多個應用程式。</span><span class="sxs-lookup"><span data-stu-id="60c30-202">You can fill your home with mixed reality content and multitask by using multiple apps at the same time.</span></span> <span data-ttu-id="60c30-203">您放置在您家中的項目留在那裡，即使您重新啟動您的裝置。</span><span class="sxs-lookup"><span data-stu-id="60c30-203">The things you place in your home stay there, even if you restart your device.</span></span>

## <a name="see-also"></a><span data-ttu-id="60c30-204">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60c30-204">See also</span></span>
* [<span data-ttu-id="60c30-205">為目標的視線</span><span class="sxs-lookup"><span data-stu-id="60c30-205">Gaze targeting</span></span>](gaze-targeting.md)
* [<span data-ttu-id="60c30-206">筆勢</span><span class="sxs-lookup"><span data-stu-id="60c30-206">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="60c30-207">語音設計</span><span class="sxs-lookup"><span data-stu-id="60c30-207">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="60c30-208">動作控制站</span><span class="sxs-lookup"><span data-stu-id="60c30-208">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="60c30-209">空間完善的設計</span><span class="sxs-lookup"><span data-stu-id="60c30-209">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="60c30-210">空間對應設計</span><span class="sxs-lookup"><span data-stu-id="60c30-210">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="60c30-211">Comfort</span><span class="sxs-lookup"><span data-stu-id="60c30-211">Comfort</span></span>](comfort.md)
* [<span data-ttu-id="60c30-212">瀏覽家用的 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="60c30-212">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
