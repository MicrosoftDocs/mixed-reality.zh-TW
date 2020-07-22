---
title: 手部直接操作
description: 直接操作輸入模型概觀
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境, 注視, 定向注視, 互動, 設計, 手部接近, HoloLens
ms.openlocfilehash: 2a63f53464e354ae49f8c63fafbf592508bd5e3b
ms.sourcegitcommit: 0eb99fae933d4374af2c032af4e9ceda1807e532
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86156779"
---
# <a name="direct-manipulation-with-hands"></a><span data-ttu-id="031a7-104">手部直接操作</span><span class="sxs-lookup"><span data-stu-id="031a7-104">Direct manipulation with hands</span></span>

![按鈕](images/UX/UX_Hero_Manipulation.jpg)

<span data-ttu-id="031a7-106">直接操作是直接以雙手觸控全像投影的輸入模型。</span><span class="sxs-lookup"><span data-stu-id="031a7-106">Direct manipulation is an input model that involves touching holograms directly with your hands.</span></span> <span data-ttu-id="031a7-107">這個概念背後的構想是要讓物件如同在真實環境中作動。</span><span class="sxs-lookup"><span data-stu-id="031a7-107">The idea behind this concept is that objects behave just as they would in the real world.</span></span> <span data-ttu-id="031a7-108">按鈕只要按下即可啟用、物件可藉由抓取來選取，2D 內容的行為則類似於虛擬觸控螢幕。</span><span class="sxs-lookup"><span data-stu-id="031a7-108">Buttons can be activated simply by pressing them, objects can be picked up by grabbing them, and 2D content behaves like a virtual touchscreen.</span></span> <span data-ttu-id="031a7-109">因此，直接操作很容易上手，而且很有趣。</span><span class="sxs-lookup"><span data-stu-id="031a7-109">This makes direct manipulation easy for users to learn, and fun.</span></span> <span data-ttu-id="031a7-110">我們將直接操作視為「近距離」輸入模型，因為它最適合用於伸手可及範圍內的內容互動。</span><span class="sxs-lookup"><span data-stu-id="031a7-110">It's considered a "near" input model in that it's best used for interacting with content within arms reach.</span></span>

<span data-ttu-id="031a7-111">直接操作以能供性為基礎，這表示它很容易使用。</span><span class="sxs-lookup"><span data-stu-id="031a7-111">Direct manipulation is affordance-based, meaning it's user friendly.</span></span> <span data-ttu-id="031a7-112">使用者不需學習任何象徵性的手勢。</span><span class="sxs-lookup"><span data-stu-id="031a7-112">There are no symbolic gestures to teach users.</span></span> <span data-ttu-id="031a7-113">所有互動都是以您可觸摸或抓取的視覺化元素為基礎。</span><span class="sxs-lookup"><span data-stu-id="031a7-113">All interactions are built around a visual element that you can touch or grab.</span></span>

## <a name="device-support"></a><span data-ttu-id="031a7-114">裝置支援</span><span class="sxs-lookup"><span data-stu-id="031a7-114">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="031a7-115"><strong>輸入模型</strong></span><span class="sxs-lookup"><span data-stu-id="031a7-115"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="031a7-116"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="031a7-116"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="031a7-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="031a7-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="031a7-118"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="031a7-118"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="031a7-119">手部直接操作</span><span class="sxs-lookup"><span data-stu-id="031a7-119">Direct manipulation with hands</span></span></td>
     <td><span data-ttu-id="031a7-120">❌ 未支援</span><span class="sxs-lookup"><span data-stu-id="031a7-120">❌ Not supported</span></span></td>
     <td><span data-ttu-id="031a7-121">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="031a7-121">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="031a7-122">➕ 支援。</span><span class="sxs-lookup"><span data-stu-id="031a7-122">➕ Supported.</span></span>  <span data-ttu-id="031a7-123">針對 UI，建議您改為使用<a href="point-and-commit.md">手部指向和行動</a>。</span><span class="sxs-lookup"><span data-stu-id="031a7-123">For UI, we recommend <a href="point-and-commit.md">point and commit with hands</a> instead.</span></span></td>
    
</tr>
</table>


<span data-ttu-id="031a7-124">直接操作是 HoloLens 2 的主要輸入模型，HoloLens 2 使用新式連貫手部追蹤系統。</span><span class="sxs-lookup"><span data-stu-id="031a7-124">Direct manipulation is a primary input model on HoloLens 2, which uses the new articulated hand-tracking system.</span></span> <span data-ttu-id="031a7-125">輸入模型也可透過運動控制器的使用在沉浸式頭戴裝置上運作，但對於物件操作以外的互動，不建議以此作為主要機制。</span><span class="sxs-lookup"><span data-stu-id="031a7-125">The input model is also available on immersive headsets through the use of motion controllers, but is not recommended as a primary means of interaction outside of object manipulation.</span></span> <span data-ttu-id="031a7-126">在 HoloLens (第 1 代) 上無法進行直接操作。</span><span class="sxs-lookup"><span data-stu-id="031a7-126">Direct manipulation is not available on HoloLens (1st gen).</span></span>

<br>

---

## <a name="collidable-fingertip"></a><span data-ttu-id="031a7-127">可碰撞的指尖</span><span class="sxs-lookup"><span data-stu-id="031a7-127">Collidable fingertip</span></span>

<span data-ttu-id="031a7-128">在 HoloLens 2 上，使用者的雙手會被辨識和解譯為左右兩手的架構模型。</span><span class="sxs-lookup"><span data-stu-id="031a7-128">On HoloLens 2, the user's hands are recognized and interpreted as left and right hand skeletal models.</span></span> <span data-ttu-id="031a7-129">若要實作直接以雙手觸控全像投影的概念，在理想情況下，五個 collider 可以連結至左右兩手架構模型的五個指尖。</span><span class="sxs-lookup"><span data-stu-id="031a7-129">To implement the idea of touching holograms directly with hands, ideally, five colliders could be attached to the five fingertips of each hand skeletal model.</span></span> <span data-ttu-id="031a7-130">但由於缺少觸覺反饋能力，十個可碰撞的指尖可能對全像投影造成非預期且無法預測的衝突。</span><span class="sxs-lookup"><span data-stu-id="031a7-130">However, due to the lack of tactile feedback, ten collidable fingertips can cause unexpected and unpredictable collisions with holograms.</span></span> 

<span data-ttu-id="031a7-131">因此，我們建議僅將 collider 放在兩手的食指上。</span><span class="sxs-lookup"><span data-stu-id="031a7-131">Hence, we suggest only putting a collider on each index finger.</span></span> <span data-ttu-id="031a7-132">可碰撞的食指指尖也可供需與其他手指搭配的各種觸控手勢作為有效觸控點，例如一指點按、一指點選、二指點按、五指點按，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="031a7-132">The collidable index fingertips can still serve as active touch points for diverse touch gestures involving other fingers, such as One-finger press, One-finger tap, Two-finger press and Five-finger press, as shown in the image below.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="031a7-133">![可碰撞的指尖](images/Collidable-Fingertip.jpg)</span><span class="sxs-lookup"><span data-stu-id="031a7-133">![collidable fingertip](images/Collidable-Fingertip.jpg)</span></span><br>
       <span data-ttu-id="031a7-134">**可碰撞的指尖**</span><span class="sxs-lookup"><span data-stu-id="031a7-134">**Collidable fingertip**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="031a7-135">![一指點按](images/Collidable-Fingertip-1-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="031a7-135">![One-finger press](images/Collidable-Fingertip-1-finger-press.jpg)</span></span><br>
        <span data-ttu-id="031a7-136">**一指點按**</span><span class="sxs-lookup"><span data-stu-id="031a7-136">**One-finger press**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="031a7-137">![一指點選](images/Collidable-Fingertip-1-finger-tap.jpg)</span><span class="sxs-lookup"><span data-stu-id="031a7-137">![One-finger tap](images/Collidable-Fingertip-1-finger-tap.jpg)</span></span><br>
       <span data-ttu-id="031a7-138">**一指點選**</span><span class="sxs-lookup"><span data-stu-id="031a7-138">**One-finger tap**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="031a7-139">![五指點按](images/Collidable-Fingertip-5-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="031a7-139">![Five-finger press](images/Collidable-Fingertip-5-finger-press.jpg)</span></span><br>
       <span data-ttu-id="031a7-140">**五指點按**</span><span class="sxs-lookup"><span data-stu-id="031a7-140">**Five-finger press**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="sphere-collider"></a><span data-ttu-id="031a7-141">球體 collider</span><span class="sxs-lookup"><span data-stu-id="031a7-141">Sphere collider</span></span>

<span data-ttu-id="031a7-142">建議您不要使用隨機的一般形狀，而應使用球體 collider。</span><span class="sxs-lookup"><span data-stu-id="031a7-142">Instead of using a random generic shape, we suggest you use a sphere collider.</span></span> <span data-ttu-id="031a7-143">然後，您可以用視覺化的方式加以呈現，為近距離目標鎖定提供明確的提示。</span><span class="sxs-lookup"><span data-stu-id="031a7-143">Then you can visually render it to provide better cues for near targeting.</span></span> <span data-ttu-id="031a7-144">球體的直徑應符合食指的粗細，以提高觸控的正確性。</span><span class="sxs-lookup"><span data-stu-id="031a7-144">The sphere's diameter should match the thickness of the index finger to increase touch accuracy.</span></span> <span data-ttu-id="031a7-145">呼叫手部 API，更容易擷取手指粗細的變數。</span><span class="sxs-lookup"><span data-stu-id="031a7-145">It's easier to retrieve the variable of finger thickness by calling the hand API.</span></span>

### <a name="fingertip-cursor"></a><span data-ttu-id="031a7-146">指尖游標</span><span class="sxs-lookup"><span data-stu-id="031a7-146">Fingertip cursor</span></span>

<span data-ttu-id="031a7-147">除了在食指指尖上顯示可碰撞的球體以外，我們也建立了進階的指尖游標，以提供更好的近距離目標鎖定互動體驗。</span><span class="sxs-lookup"><span data-stu-id="031a7-147">In addition to rendering a collidable sphere on the index fingertip, we've created an advanced fingertip cursor to interactively achieve a better near-targeting experience.</span></span> <span data-ttu-id="031a7-148">這是連結至食指指尖的一個環狀游標。</span><span class="sxs-lookup"><span data-stu-id="031a7-148">It is a donut-shaped cursor attached to the index fingertip.</span></span> <span data-ttu-id="031a7-149">它會根據鄰近性，在方向和大小方面動態回應目標，詳述如下：</span><span class="sxs-lookup"><span data-stu-id="031a7-149">According to proximity, it dynamically reacts to a target in terms of orientation and size as detailed below:</span></span>

* <span data-ttu-id="031a7-150">當食指移向全像投影時，游標一律會與全像投影的表面平行，且其大小會隨之逐漸縮減。</span><span class="sxs-lookup"><span data-stu-id="031a7-150">When an index finger moves toward a hologram, the cursor is always parallel to the hologram's surface and gradually shrinks its size accordingly.</span></span>
* <span data-ttu-id="031a7-151">當手指接觸到表面時，游標會縮減為一個點，並發出觸控事件。</span><span class="sxs-lookup"><span data-stu-id="031a7-151">As soon as the finger touches the surface, the cursor shrinks into a dot and emits a touch event.</span></span>

<span data-ttu-id="031a7-152">透過互動式反饋，使用者可執行高精確度的近距離目標鎖定工作，例如觸發超連結或按下按鈕，如下所示。</span><span class="sxs-lookup"><span data-stu-id="031a7-152">With interactive feedback, users can achieve high precision near-targeting tasks, such as triggering a hyperlink or pressing a button as shown below.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="031a7-153">![指尖游標遠距](images/Fingertip-cursor-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="031a7-153">![Fingertip cursor far](images/Fingertip-cursor-far.jpg)</span></span><br>
       <span data-ttu-id="031a7-154">**指尖游標遠距**</span><span class="sxs-lookup"><span data-stu-id="031a7-154">**Fingertip cursor far**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="031a7-155">![指尖游標近距](images/Fingertip-cursor-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="031a7-155">![Fingertip cursor near](images/Fingertip-cursor-near.jpg)</span></span><br>
        <span data-ttu-id="031a7-156">**指尖游標近距**</span><span class="sxs-lookup"><span data-stu-id="031a7-156">**Fingertip cursor near**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="031a7-157">![指尖游標接觸](images/Fingertip-cursor-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="031a7-157">![Fingertip cursor contact](images/Fingertip-cursor-contact.jpg)</span></span><br>
       <span data-ttu-id="031a7-158">**指尖游標接觸**</span><span class="sxs-lookup"><span data-stu-id="031a7-158">**Fingertip cursor contact**</span></span><br>
    :::column-end:::
:::row-end:::

<br>



## <a name="bounding-box-with-proximity-shader"></a><span data-ttu-id="031a7-159">週框方塊與近接著色器</span><span class="sxs-lookup"><span data-stu-id="031a7-159">Bounding box with proximity shader</span></span>

<span data-ttu-id="031a7-160">全像投影本身也須具備提供視覺和聽覺反饋的能力，以彌補觸覺反饋能力的不足。</span><span class="sxs-lookup"><span data-stu-id="031a7-160">The hologram itself also requires the ability to provide both visual and audio feedback to compensate the lack of tactile feedback.</span></span> <span data-ttu-id="031a7-161">為此，我們設計了週框方塊與近接著色器的概念。</span><span class="sxs-lookup"><span data-stu-id="031a7-161">For that, we generate the concept of a bounding box with a proximity shader.</span></span> <span data-ttu-id="031a7-162">週框方塊是足以包覆一個 3D 物件的最小體積區域。</span><span class="sxs-lookup"><span data-stu-id="031a7-162">A bounding box is a minimum volumetric area that encloses a 3D object.</span></span> <span data-ttu-id="031a7-163">週框方塊具有互動式呈現機制，名為近接著色器。</span><span class="sxs-lookup"><span data-stu-id="031a7-163">The bounding box has an interactive rendering mechanism called a proximity shader.</span></span> <span data-ttu-id="031a7-164">近接著色器的行為如下：</span><span class="sxs-lookup"><span data-stu-id="031a7-164">The proximity shader behaves:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="031a7-165">![暫留 (遠距) 視覺化回饋](images/bounding-box-with-proximity-shader-hover-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="031a7-165">![Hover (far) with visual feedback](images/bounding-box-with-proximity-shader-hover-far.jpg)</span></span><br>
       <span data-ttu-id="031a7-166">**暫留 (遠距)**</span><span class="sxs-lookup"><span data-stu-id="031a7-166">**Hover (far)**</span></span><br>
       <span data-ttu-id="031a7-167">當食指進入範圍內時，手指焦點即會投射在週框方塊的表面。</span><span class="sxs-lookup"><span data-stu-id="031a7-167">When the index finger is within a range, a fingertip spotlight is cast on the surface of the bounding box.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="031a7-168">![暫留 (近距) 視覺化回饋](images/bounding-box-with-proximity-shader-hover-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="031a7-168">![Hover (near) with visual feedback](images/bounding-box-with-proximity-shader-hover-near.jpg)</span></span><br>
        <span data-ttu-id="031a7-169">**暫留 (近距)**</span><span class="sxs-lookup"><span data-stu-id="031a7-169">**Hover (near)**</span></span><br>
        <span data-ttu-id="031a7-170">當指尖越來越接近表面時，焦點會隨之逐漸縮小。</span><span class="sxs-lookup"><span data-stu-id="031a7-170">When the fingertip gets closer to the surface, the spotlight shrinks accordingly.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="031a7-171">![接觸開始](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="031a7-171">![Contact begins](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span></span><br>
       <span data-ttu-id="031a7-172">**接觸開始**</span><span class="sxs-lookup"><span data-stu-id="031a7-172">**Contact begins**</span></span><br>
       <span data-ttu-id="031a7-173">手指一碰到表面時，整個週框方塊就會變色，或產生視覺效果以反映觸碰狀態。</span><span class="sxs-lookup"><span data-stu-id="031a7-173">As soon as the fingertip touches the surface, the entire bounding box changes color or generates visual effects to reflect the touch state.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="031a7-174">![接觸結束](images/bounding-box-with-proximity-shader-end-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="031a7-174">![Contact ends](images/bounding-box-with-proximity-shader-end-contact.jpg)</span></span><br>
       <span data-ttu-id="031a7-175">**接觸結束**</span><span class="sxs-lookup"><span data-stu-id="031a7-175">**Contact ends**</span></span><br>
       <span data-ttu-id="031a7-176">此外也可以啟用音效來補強視覺的觸碰反饋。</span><span class="sxs-lookup"><span data-stu-id="031a7-176">A sound effect can also be activated to enhance the visual touch feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="pressable-button"></a><span data-ttu-id="031a7-177">可點按的按鈕</span><span class="sxs-lookup"><span data-stu-id="031a7-177">Pressable button</span></span>

<span data-ttu-id="031a7-178">有了可碰撞的指尖，使用者即可與基本的全像攝影 UI 元件互動，例如可點按的按鈕。</span><span class="sxs-lookup"><span data-stu-id="031a7-178">With a collidable fingertip, users are now ready to interact with a fundamental holographic UI component, such as a pressable button.</span></span> <span data-ttu-id="031a7-179">可點按的按鈕是專為直接手指點按設計的全像攝影按鈕。</span><span class="sxs-lookup"><span data-stu-id="031a7-179">A pressable button is a holographic button tailored for a direct finger press.</span></span> <span data-ttu-id="031a7-180">同樣地，由於缺少觸覺反饋，可點按的按鈕也設有若干機制來處理觸覺反饋的相關問題。</span><span class="sxs-lookup"><span data-stu-id="031a7-180">Again, due to the lack of tactile feedback, a pressable button equips a couple mechanisms to tackle tactile feedback-related issues.</span></span>

* <span data-ttu-id="031a7-181">第一項機制是具有近接著色器的週框方塊，其詳細說明請見上一節。</span><span class="sxs-lookup"><span data-stu-id="031a7-181">The first mechanism is a bounding box with a proximity shader, which is detailed in the previous section.</span></span> <span data-ttu-id="031a7-182">它可讓使用者在接近及觸碰按鈕時更能清楚感知鄰近性。</span><span class="sxs-lookup"><span data-stu-id="031a7-182">It gives users a better sense of proximity when they approach and make contact with a button.</span></span>
* <span data-ttu-id="031a7-183">第二項機制是下壓。</span><span class="sxs-lookup"><span data-stu-id="031a7-183">The second mechanism is depression.</span></span> <span data-ttu-id="031a7-184">下壓會在指尖接觸到按鈕後，產生按下的感覺。</span><span class="sxs-lookup"><span data-stu-id="031a7-184">Depression creates a sense of pressing down after a fingertip contacts a button.</span></span> <span data-ttu-id="031a7-185">此機制能確保按鈕會緊隨著指尖沿深度軸移動。</span><span class="sxs-lookup"><span data-stu-id="031a7-185">The mechanism ensures that the button tightly moves with the fingertip along the depth axis.</span></span> <span data-ttu-id="031a7-186">在按鈕達到指定的深度 (按下) 或離開該深度 (放開) 之後，就會觸發按鈕。</span><span class="sxs-lookup"><span data-stu-id="031a7-186">The button can be triggered when it reaches a designated depth (on press) or leaves the depth (on release) after passing through it.</span></span>
* <span data-ttu-id="031a7-187">在觸發按鈕時應加上音效以增強反饋。</span><span class="sxs-lookup"><span data-stu-id="031a7-187">The sound effect should be added to enhance feedback when the button is triggered.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="031a7-188">![可點按的按鈕遠距](images/pressable-button-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="031a7-188">![pressable button far](images/pressable-button-far.jpg)</span></span><br>
       <span data-ttu-id="031a7-189">**手指遠離**</span><span class="sxs-lookup"><span data-stu-id="031a7-189">**Finger is far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="031a7-190">![可點按的按鈕近距](images/pressable-button-approach.jpg)</span><span class="sxs-lookup"><span data-stu-id="031a7-190">![pressable button near](images/pressable-button-approach.jpg)</span></span><br>
        <span data-ttu-id="031a7-191">**手指靠近**</span><span class="sxs-lookup"><span data-stu-id="031a7-191">**Finger approaches**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="031a7-192">![可點按的按鈕接觸開始](images/pressable-button-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="031a7-192">![pressable button contact begins](images/pressable-button-contact.jpg)</span></span><br>
       <span data-ttu-id="031a7-193">**接觸開始**</span><span class="sxs-lookup"><span data-stu-id="031a7-193">**Contact begins**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="031a7-194">![可點按的按鈕點按](images/pressable-button-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="031a7-194">![pressable button press](images/pressable-button-press.jpg)</span></span><br>
       <span data-ttu-id="031a7-195">**按下**</span><span class="sxs-lookup"><span data-stu-id="031a7-195">**Press down**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="031a7-196">2D 平板互動</span><span class="sxs-lookup"><span data-stu-id="031a7-196">2D slate interaction</span></span>

<span data-ttu-id="031a7-197">2D [平板](slate.md)是用來裝載 2D 應用程式內容 (例如網頁瀏覽器) 的全像攝影容器。</span><span class="sxs-lookup"><span data-stu-id="031a7-197">A 2D [slate](slate.md) is a holographic container used to host 2D app content, such as a web browser.</span></span> <span data-ttu-id="031a7-198">透過直接操作與 2D 平板互動的設計概念，是運用與實體觸控螢幕互動的心智模型。</span><span class="sxs-lookup"><span data-stu-id="031a7-198">The design concept for interacting with a 2D slate via direct manipulation is to leverage the mental model of interacting with a physical touch screen.</span></span>

### <a name="to-interact-with-the-slate-contact"></a><span data-ttu-id="031a7-199">與觸控平板互動</span><span class="sxs-lookup"><span data-stu-id="031a7-199">To interact with the slate contact</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="031a7-200">![觸控](images/2d-slate-interaction-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="031a7-200">![Touch](images/2d-slate-interaction-touch.jpg)</span></span><br>
       <span data-ttu-id="031a7-201">**觸控**</span><span class="sxs-lookup"><span data-stu-id="031a7-201">**Touch**</span></span><br>
       <span data-ttu-id="031a7-202">以食指按下超連結或按鈕。</span><span class="sxs-lookup"><span data-stu-id="031a7-202">Use an index finger to press a hyperlink or a button.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="031a7-203">![捲動](images/2d-slate-interaction-scroll2.jpg)</span><span class="sxs-lookup"><span data-stu-id="031a7-203">![Scroll](images/2d-slate-interaction-scroll2.jpg)</span></span><br>
        <span data-ttu-id="031a7-204">**捲動**</span><span class="sxs-lookup"><span data-stu-id="031a7-204">**Scroll**</span></span><br>
        <span data-ttu-id="031a7-205">以食指向上和向下捲動平板內容。</span><span class="sxs-lookup"><span data-stu-id="031a7-205">Use an index finger to scroll a slate content up and down.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="031a7-206">![縮放](images/2d-slate-interaction-zoom2.jpg)</span><span class="sxs-lookup"><span data-stu-id="031a7-206">![Zoom](images/2d-slate-interaction-zoom2.jpg)</span></span><br>
       <span data-ttu-id="031a7-207">**縮放**</span><span class="sxs-lookup"><span data-stu-id="031a7-207">**Zoom**</span></span><br>
       <span data-ttu-id="031a7-208">使用者可用兩根食指，根據手指的相對移動來放大和縮小平板內容。</span><span class="sxs-lookup"><span data-stu-id="031a7-208">The user's two index fingers are used to zoom in and out of the slate content, according to the relative motion of the fingers.</span></span>
    :::column-end:::
:::row-end:::


### <a name="for-manipulating-the-2d-slate-itself"></a><span data-ttu-id="031a7-209">操作 2D 平板本身</span><span class="sxs-lookup"><span data-stu-id="031a7-209">For manipulating the 2D slate itself</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="031a7-210">![移動](images/manipulate-2d-slate-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="031a7-210">![Move](images/manipulate-2d-slate-move.jpg)</span></span><br>
       <span data-ttu-id="031a7-211">**移動**</span><span class="sxs-lookup"><span data-stu-id="031a7-211">**Move**</span></span><br>
       <span data-ttu-id="031a7-212">將手靠近角落或邊緣時，可顯示最接近的操作能供性。</span><span class="sxs-lookup"><span data-stu-id="031a7-212">Move your hands toward corners and edges to reveal the closest manipulation affordances.</span></span> <span data-ttu-id="031a7-213">抓取 2D 平板上方的 holobar，可以移動整個平板。</span><span class="sxs-lookup"><span data-stu-id="031a7-213">Grab the Holobar at the top of the 2D slate, which lets you move the whole slate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="031a7-214">![縮放比例](images/manipulate-2d-slate-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="031a7-214">![Scale](images/manipulate-2d-slate-scale.jpg)</span></span><br>
        <span data-ttu-id="031a7-215">**縮放比例**</span><span class="sxs-lookup"><span data-stu-id="031a7-215">**Scale**</span></span><br>
        <span data-ttu-id="031a7-216">抓取操作能供性，並透過角落能供性執行統一尺寸調整。</span><span class="sxs-lookup"><span data-stu-id="031a7-216">Grab the manipulation affordances and perform uniform scaling through the corner affordances.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="031a7-217">![自動重排](images/manipulate-2d-slate-reflow.jpg)</span><span class="sxs-lookup"><span data-stu-id="031a7-217">![Reflow](images/manipulate-2d-slate-reflow.jpg)</span></span><br>
       <span data-ttu-id="031a7-218">**自動重排**</span><span class="sxs-lookup"><span data-stu-id="031a7-218">**Reflow**</span></span><br>
       <span data-ttu-id="031a7-219">抓取操作能供性，透過邊緣能供性進行自動重排。</span><span class="sxs-lookup"><span data-stu-id="031a7-219">Grab the manipulation affordances and perform reflow via the edge affordances.</span></span>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="3d-object-manipulation"></a><span data-ttu-id="031a7-220">3D 物件操作</span><span class="sxs-lookup"><span data-stu-id="031a7-220">3D object manipulation</span></span>

<span data-ttu-id="031a7-221">HoloLens 2 可讓使用者將週框方塊套用至每個 3D 物件，以便用手指引及操作 3D 全像攝影物件。</span><span class="sxs-lookup"><span data-stu-id="031a7-221">HoloLens 2 lets users enable their hands to direct and manipulate 3D holographic objects by applying a bounding box to each 3D object.</span></span> <span data-ttu-id="031a7-222">週框方塊可透過其近接著色器提供更確切的深度認知。</span><span class="sxs-lookup"><span data-stu-id="031a7-222">The bounding box provides better depth perception through its proximity shader.</span></span> <span data-ttu-id="031a7-223">週框方塊衍生出兩種 3D 物件操作方法。</span><span class="sxs-lookup"><span data-stu-id="031a7-223">With the bounding box, there are two design approaches for 3D object manipulation.</span></span>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="031a7-224">能供性操作</span><span class="sxs-lookup"><span data-stu-id="031a7-224">Affordance-based manipulation</span></span>

<span data-ttu-id="031a7-225">能供性操作可讓您透過週框方塊及其周圍的操作能供性來操作 3D 物件。</span><span class="sxs-lookup"><span data-stu-id="031a7-225">Affordance-base manipulation lets you manipulate the 3D object through a bounding box along with the manipulation affordances around it.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="031a7-226">![移動](images/3d-object-manipulation-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="031a7-226">![Move](images/3d-object-manipulation-move.jpg)</span></span><br>
       <span data-ttu-id="031a7-227">**移動**</span><span class="sxs-lookup"><span data-stu-id="031a7-227">**Move**</span></span><br>
       <span data-ttu-id="031a7-228">當使用者的手接近 3D 物件時，就會顯示週框方塊和最接近的能供性。</span><span class="sxs-lookup"><span data-stu-id="031a7-228">As soon as a user's hand is close to a 3D object, the bounding box and the nearest affordance are revealed.</span></span> <span data-ttu-id="031a7-229">使用者可以抓取週框方塊來移動整個物件。</span><span class="sxs-lookup"><span data-stu-id="031a7-229">Users can grab the bounding box to move the whole object.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="031a7-230">![旋轉](images/3d-object-manipulation-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="031a7-230">![Rotate](images/3d-object-manipulation-rotate.jpg)</span></span><br>
        <span data-ttu-id="031a7-231">**旋轉**</span><span class="sxs-lookup"><span data-stu-id="031a7-231">**Rotate**</span></span><br>
        <span data-ttu-id="031a7-232">使用者可以抓取邊緣能供性來進行旋轉。</span><span class="sxs-lookup"><span data-stu-id="031a7-232">Users can grab the edge affordances to rotate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="031a7-233">![縮放比例](images/3d-object-manipulation-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="031a7-233">![Scale](images/3d-object-manipulation-scale.jpg)</span></span><br>
       <span data-ttu-id="031a7-234">**縮放比例**</span><span class="sxs-lookup"><span data-stu-id="031a7-234">**Scale**</span></span><br>
       <span data-ttu-id="031a7-235">使用者可以抓取角落能供性來執行統一尺寸調整。</span><span class="sxs-lookup"><span data-stu-id="031a7-235">Users can grab the corner affordances to scale uniformly.</span></span>
    :::column-end:::
:::row-end:::

<br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="031a7-236">非能供性操作</span><span class="sxs-lookup"><span data-stu-id="031a7-236">Non-affordance based manipulation</span></span>

<span data-ttu-id="031a7-237">非能供性操作不會將能供性連結至週框方塊。</span><span class="sxs-lookup"><span data-stu-id="031a7-237">Non-affordance-based manipulation does not attach affordance to the bounding box.</span></span> <span data-ttu-id="031a7-238">使用者只能顯示週框方塊，然後直接與它互動。</span><span class="sxs-lookup"><span data-stu-id="031a7-238">Users can only reveal the bounding box, then directly interact with it.</span></span> <span data-ttu-id="031a7-239">若以一隻手抓住週框方塊，物件的轉譯和旋轉會與那隻手的動作和方向相關聯。</span><span class="sxs-lookup"><span data-stu-id="031a7-239">If the bounding box is grabbed with one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="031a7-240">以雙手抓住物件時，使用者可以根據兩隻手的相對動作來轉譯、縮放及旋轉物件。</span><span class="sxs-lookup"><span data-stu-id="031a7-240">When the object is grabbed with two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span>

<span data-ttu-id="031a7-241">特定操作需要精確度。</span><span class="sxs-lookup"><span data-stu-id="031a7-241">Specific manipulation requires precision.</span></span> <span data-ttu-id="031a7-242">建議您使用**能供性操作**，因為它可提供高層級的細微性。</span><span class="sxs-lookup"><span data-stu-id="031a7-242">We recommend that you use **affordance-based manipulation** because it provides a high level of granularity.</span></span> <span data-ttu-id="031a7-243">針對彈性操作，建議您使用**非能供性操作**，因為它可帶來即時而有趣的體驗。</span><span class="sxs-lookup"><span data-stu-id="031a7-243">For flexible manipulation, we recommend you use **non-affordance manipulation** as it allows for instant and playful experiences.</span></span>

<br>

---


## <a name="instinctual-gestures"></a><span data-ttu-id="031a7-244">本能手勢</span><span class="sxs-lookup"><span data-stu-id="031a7-244">Instinctual gestures</span></span>

<span data-ttu-id="031a7-245">在 HoloLens (第 1 代) 推出時，我們曾教過使用者幾個預先定義的手勢，例如綻開和空中點選。</span><span class="sxs-lookup"><span data-stu-id="031a7-245">With HoloLens (1st gen), we taught users a couple of predefined gestures, such as bloom and air tap.</span></span> <span data-ttu-id="031a7-246">而在使用 HoloLens 2 時，使用者並不需要記住任何象徵性的手勢。</span><span class="sxs-lookup"><span data-stu-id="031a7-246">For HoloLens 2, we don't ask users to memorize any symbolic gestures.</span></span> <span data-ttu-id="031a7-247">使用者與全像投影和內容互動時所需使用的所有必要手勢，都是符合本能的。</span><span class="sxs-lookup"><span data-stu-id="031a7-247">All required user gestures, where users need to interact with holograms and content, are instinctual.</span></span> <span data-ttu-id="031a7-248">協助使用者透過 UI 能供性的設計執行手勢，他們就能學會本能手勢。</span><span class="sxs-lookup"><span data-stu-id="031a7-248">The way to achieve instinctual gestures is to help users perform gestures through the design of UI affordances.</span></span>

<span data-ttu-id="031a7-249">例如，如果我們引導使用者以兩指捏合抓取某個物件或控制點，表示該物件或控制點應該很小。</span><span class="sxs-lookup"><span data-stu-id="031a7-249">For example, if we encourage the user to grab an object or a control point with a two finger pinch, the object or the control point should be small.</span></span> <span data-ttu-id="031a7-250">如果我們要使用者執行五指抓取，表示該物件或控制點應該較大。</span><span class="sxs-lookup"><span data-stu-id="031a7-250">If we want the user to perform five finger grab, the object or the control point should be relatively large.</span></span> <span data-ttu-id="031a7-251">和按鈕一樣，小按鈕就必須以單指點按，而對於大按鈕，使用者就應該用手掌來按壓。</span><span class="sxs-lookup"><span data-stu-id="031a7-251">Similar to buttons, a tiny button would limit users to press it with a single finger; a large button would encourage users to press it with their palms.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="031a7-252">![移動](images/instinctual-gestures-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="031a7-252">![Move](images/instinctual-gestures-smallobject.jpg)</span></span><br>
       <span data-ttu-id="031a7-253">**小型物件**</span><span class="sxs-lookup"><span data-stu-id="031a7-253">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="031a7-254">![旋轉](images/instinctual-gestures-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="031a7-254">![Rotate](images/instinctual-gestures-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="031a7-255">**中型物件**</span><span class="sxs-lookup"><span data-stu-id="031a7-255">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="031a7-256">![縮放比例](images/instinctual-gestures-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="031a7-256">![Scale](images/instinctual-gestures-largeobject.jpg)</span></span><br>
       <span data-ttu-id="031a7-257">**大型物件**</span><span class="sxs-lookup"><span data-stu-id="031a7-257">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---

<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a><span data-ttu-id="031a7-258">手部與 6 DoF 控制器之間的對稱設計</span><span class="sxs-lookup"><span data-stu-id="031a7-258">Symmetric design between hands and 6 DoF controllers</span></span>

<span data-ttu-id="031a7-259">您可能已經注意到，AR 中的手勢與 VR 中的運動控制器在互動方式上有其相似之處。</span><span class="sxs-lookup"><span data-stu-id="031a7-259">You may have noticed that there are interaction parallels we can draw between hands in AR and motion controllers in VR.</span></span> <span data-ttu-id="031a7-260">這兩種輸入在其各自的環境中都可用來觸發直接操作。</span><span class="sxs-lookup"><span data-stu-id="031a7-260">Both inputs can be used to trigger direct manipulations in their respective environments.</span></span> <span data-ttu-id="031a7-261">在 HoloLens 2 中，近距離以手抓取並拖曳的效用，非常類似於 WMR 運動控制器上的抓取按鈕所能做到的。</span><span class="sxs-lookup"><span data-stu-id="031a7-261">In HoloLens 2, grabbing and dragging with hands at a close distance works much the same way as the grab button does on WMR motion controllers.</span></span> <span data-ttu-id="031a7-262">這種相似性可讓使用者在兩種平台上都能採用熟悉的互動方式，且若您決定將應用程式移轉至另一個平台，這一點可能也有幫助。</span><span class="sxs-lookup"><span data-stu-id="031a7-262">This provides users with interaction familiarity between the two platforms, which might prove useful if you ever decide to port your application from one to the other.</span></span>

<br>

---

## <a name="optimize-with-eye-tracking"></a><span data-ttu-id="031a7-263">透過眼球追蹤達到最佳效果</span><span class="sxs-lookup"><span data-stu-id="031a7-263">Optimize with eye tracking</span></span>

<span data-ttu-id="031a7-264">直接操作若能如預期運作，將可達到奇妙的效果。</span><span class="sxs-lookup"><span data-stu-id="031a7-264">Direct manipulation can feel magical if it works as intended.</span></span> <span data-ttu-id="031a7-265">但若無法順利將手移到想要的位置，而老是無意中觸發全像投影，就會出現挫敗感。</span><span class="sxs-lookup"><span data-stu-id="031a7-265">But it can also become frustrating if you can’t move your hand anywhere without unintentionally triggering a hologram.</span></span> <span data-ttu-id="031a7-266">眼球追蹤或許有助於判斷使用者真正的意圖。</span><span class="sxs-lookup"><span data-stu-id="031a7-266">Eye tracking potentially helps to better identify what the user’s intent is.</span></span>

* <span data-ttu-id="031a7-267">**時機**：避免無意中觸發操作回應。</span><span class="sxs-lookup"><span data-stu-id="031a7-267">**When**: Reduce unintentionally triggering a manipulation response.</span></span> <span data-ttu-id="031a7-268">眼球追蹤有助於了解使用者目前從事的活動。</span><span class="sxs-lookup"><span data-stu-id="031a7-268">Eye tracking allows for better understanding what a user is currently engaged with.</span></span>
<span data-ttu-id="031a7-269">例如，想像您在閱讀全像攝影 (指示) 文件時，您伸手要去拿實際環境中的工具。</span><span class="sxs-lookup"><span data-stu-id="031a7-269">For example, imagine you are reading through a holographic (instructional) text when reaching over to grab you real-world work tool.</span></span>

<span data-ttu-id="031a7-270">此時，您的手不小心劃過某個您根本沒留意過的互動式全像攝影按鈕 (例如該按鈕可能不在使用者的視野 (FoV) 內)。</span><span class="sxs-lookup"><span data-stu-id="031a7-270">By doing so, you accidentally move your hand across some interactive holographic buttons that you hadn't even noticed before (e.g. it  may be outside the user's field-of-view (FoV)).</span></span>

  <span data-ttu-id="031a7-271">長話短說：如果使用者已有一段時間未注視某個全像投影，系統也未偵測到其觸碰或抓取事件，表示使用者可能並非真正想要與該全像投影互動。</span><span class="sxs-lookup"><span data-stu-id="031a7-271">Long story short: If the user hasn't looked at a hologram for a while, yet a touch or grasp event has been detected for it, it is likely that the user wasn't actually intending to interact with that hologram.</span></span>

* <span data-ttu-id="031a7-272">**標的**：除了處理誤判的啟用以外，它還有助於判斷所應抓取或觸碰的全像投影，因為從您的視角可能無法看出精準的交叉點，尤其是有數個全像投影的位置彼此十分靠近時。</span><span class="sxs-lookup"><span data-stu-id="031a7-272">**Which one**:  Aside from addressing false positive activations, another example includes better identifying which holograms to grab or poke as the precise intersection point may not be clear from your perspective, especially if several holograms are positioned close to each other.</span></span>

  <span data-ttu-id="031a7-273">雖然 HoloLens 2 的眼球追蹤在判斷眼睛視線時會因其精準度而有所限制，但對近距離互動而言仍不失為有利的工具，因為透過手部輸入互動時，會有深度的差異。</span><span class="sxs-lookup"><span data-stu-id="031a7-273">While eye tracking on HoloLens 2 has limitations based on how accurately it can determine your eye gaze, this can still be very helpful for near interactions due to depth disparity when interacting with hand input.</span></span> <span data-ttu-id="031a7-274">這表示，要判斷您的手是在全像投影的後面還是前面，而精確地抓取操作工具 (舉例而言)，有時是很困難的。</span><span class="sxs-lookup"><span data-stu-id="031a7-274">This means that it is sometimes difficult to determine whether your hand is behind or in front of a hologram to precisely grab a manipulation widget, for example.</span></span>

* <span data-ttu-id="031a7-275">**目的地**：運用使用者在執行快速拋投手勢時看往何處的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="031a7-275">**Where to**: Use information about what a user is looking at with quick-throwing gestures.</span></span> <span data-ttu-id="031a7-276">抓取全像投影並約略拋向您要的目的地。</span><span class="sxs-lookup"><span data-stu-id="031a7-276">Grab a hologram and roughly toss it toward your intended destination.</span></span>  

    <span data-ttu-id="031a7-277">雖然這有時行得通，但快速執行手勢可能會導致目的地嚴重失準。</span><span class="sxs-lookup"><span data-stu-id="031a7-277">While this sometimes works, quickly performing hand gestures may result in highly inaccurate destinations.</span></span> <span data-ttu-id="031a7-278">不過，同時運用眼球追蹤或可改善手勢的準確度。</span><span class="sxs-lookup"><span data-stu-id="031a7-278">However, eye tracking could improve the accuracy of the gesture.</span></span>

<br>

---

## <a name="manipulation-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="031a7-279">MRTK (混合實境工具組) 中適用於 Unity 的操作</span><span class="sxs-lookup"><span data-stu-id="031a7-279">Manipulation in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="031a7-280">透過 **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** ，您可以使用指令碼 **ObjectManipulator** 輕鬆執行常見的操作行為。</span><span class="sxs-lookup"><span data-stu-id="031a7-280">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily achieve common manipulation behavior using the script **ObjectManipulator**.</span></span> <span data-ttu-id="031a7-281">使用 ObjectManipulator，您可以直接用手或透過手部射線來抓取和移動物件。</span><span class="sxs-lookup"><span data-stu-id="031a7-281">With ObjectManipulator, you can grab and move objects directly with hands or with hand ray.</span></span> <span data-ttu-id="031a7-282">它也支援雙手操作來縮放和旋轉物件。</span><span class="sxs-lookup"><span data-stu-id="031a7-282">It also supports two-handed manipulation for scaling and rotating an object.</span></span>

* [<span data-ttu-id="031a7-283">MRTK - 操作</span><span class="sxs-lookup"><span data-stu-id="031a7-283">MRTK - Manipulation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)


---

## <a name="see-also"></a><span data-ttu-id="031a7-284">另請參閱</span><span class="sxs-lookup"><span data-stu-id="031a7-284">See also</span></span>

* [<span data-ttu-id="031a7-285">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="031a7-285">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="031a7-286">手部指向和行動</span><span class="sxs-lookup"><span data-stu-id="031a7-286">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="031a7-287">本能互動</span><span class="sxs-lookup"><span data-stu-id="031a7-287">Instinctual interactions</span></span>](interaction-fundamentals.md)
