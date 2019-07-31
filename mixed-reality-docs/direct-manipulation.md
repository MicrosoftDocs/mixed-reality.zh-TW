---
title: 手部直接操作
description: 直接操作輸入模型概觀
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境, 注視, 定向注視, 互動, 設計, 手部接近, HoloLens
ms.openlocfilehash: 8047d7549309d293b805dc43e44da99f9139e5c6
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414441"
---
# <a name="direct-manipulation-with-hands"></a><span data-ttu-id="0d190-104">手部直接操作</span><span class="sxs-lookup"><span data-stu-id="0d190-104">Direct manipulation with hands</span></span>
<span data-ttu-id="0d190-105">直接操作是直接以雙手觸控全像投影的輸入模型。</span><span class="sxs-lookup"><span data-stu-id="0d190-105">Direct manipulation is an input model that involves touching holograms directly with your hands.</span></span> <span data-ttu-id="0d190-106">直接操作背後的概念是要讓物件如同在真實環境中作動。</span><span class="sxs-lookup"><span data-stu-id="0d190-106">The idea behind direct manipulation is that objects behave just as they would in the real world.</span></span> <span data-ttu-id="0d190-107">按鈕只要按下即可啟用、物件可藉由抓取來選取，2D 內容的行為則類似於虛擬觸控螢幕。</span><span class="sxs-lookup"><span data-stu-id="0d190-107">Buttons can be activated simply by pressing them, objects can be picked up by grabbing them, and 2D content behaves like a virtual touchscreen.</span></span> <span data-ttu-id="0d190-108">因此，直接操作很容易上手，而且很有趣。</span><span class="sxs-lookup"><span data-stu-id="0d190-108">This makes direct manipulation is easy for users to learn, and fun.</span></span> <span data-ttu-id="0d190-109">我們將直接操作視為「近距離」輸入模型，因為它最適合用於伸手可及範圍內的內容互動。</span><span class="sxs-lookup"><span data-stu-id="0d190-109">Direct manipulation is considered a "near" input model in that it's best used for interacting with content within arms reach.</span></span>

<span data-ttu-id="0d190-110">直接操作以能供性為基礎，這表示它很容易使用。</span><span class="sxs-lookup"><span data-stu-id="0d190-110">Direct manipulation is affordance-based, meaning it's user friendly.</span></span> <span data-ttu-id="0d190-111">使用者不需學習任何象徵性的手勢。</span><span class="sxs-lookup"><span data-stu-id="0d190-111">There are no symbolic gestures to teach users.</span></span> <span data-ttu-id="0d190-112">所有互動都是以您可觸摸或抓取的視覺化元素為基礎。</span><span class="sxs-lookup"><span data-stu-id="0d190-112">All interactions are built around a visual element that you can touch or grab.</span></span>

## <a name="device-support"></a><span data-ttu-id="0d190-113">裝置支援</span><span class="sxs-lookup"><span data-stu-id="0d190-113">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="0d190-114"><strong>輸入模型</strong></span><span class="sxs-lookup"><span data-stu-id="0d190-114"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="0d190-115"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="0d190-115"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="0d190-116"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="0d190-116"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="0d190-117"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="0d190-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="0d190-118">手部直接操作</span><span class="sxs-lookup"><span data-stu-id="0d190-118">Direct manipulation with hands</span></span></td>
     <td><span data-ttu-id="0d190-119">❌ 不支援</span><span class="sxs-lookup"><span data-stu-id="0d190-119">❌ Not supported</span></span></td>
     <td><span data-ttu-id="0d190-120">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="0d190-120">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="0d190-121">➕ 建議使用替代方案<a href="point-and-commit.md">手部指向和行動</a>。</span><span class="sxs-lookup"><span data-stu-id="0d190-121">➕ An alternative, <a href="point-and-commit.md">point and commit with hands</a> is recommended.</span></span></td>
    
</tr>
</table>


<span data-ttu-id="0d190-122">直接操作是 HoloLens 2 的主要輸入模型，採用新式連貫手部追蹤系統。</span><span class="sxs-lookup"><span data-stu-id="0d190-122">Direct manipulation is a primary input model on HoloLens 2, and utilizes the new articulated hand-tracking system.</span></span> <span data-ttu-id="0d190-123">輸入模型也可透過運動控制器的使用在沉浸式頭戴裝置上運作，但對於物件操作以外的互動，不建議以此作為主要機制。</span><span class="sxs-lookup"><span data-stu-id="0d190-123">The input model is also available on immersive headsets through the use of motion controllers, but is not recommended as a primary means of interaction outside of object manipulation.</span></span> <span data-ttu-id="0d190-124">在 HoloLens (第 1 代) 上無法進行直接操作。</span><span class="sxs-lookup"><span data-stu-id="0d190-124">Direct manipluation is not available on HoloLens (1st gen).</span></span>


## <a name="collidable-fingertip"></a><span data-ttu-id="0d190-125">可碰撞的指尖</span><span class="sxs-lookup"><span data-stu-id="0d190-125">Collidable fingertip</span></span>

<span data-ttu-id="0d190-126">在 HoloLens 2 上，使用者的雙手會被辨識和解譯為左右兩手的架構模型。</span><span class="sxs-lookup"><span data-stu-id="0d190-126">On HoloLens 2, the user's hands are recognized and interpreted as left and right hand skeletal models.</span></span> <span data-ttu-id="0d190-127">若要實作直接以雙手觸控全像投影的概念，在理想情況下，五個 collider 可以連結至左右兩手架構模型的五個指尖。</span><span class="sxs-lookup"><span data-stu-id="0d190-127">To implement the idea of touching holograms directly with hands, ideally, five colliders could be attached to the five fingertips of each hand skeletal model.</span></span> <span data-ttu-id="0d190-128">但由於缺少觸覺反饋能力，十個可碰撞的指尖可能對全像投影造成非預期且無法預測的衝突。</span><span class="sxs-lookup"><span data-stu-id="0d190-128">However, due to the lack of tactile feedback, ten collidable fingertips can cause unexpected and unpredictable collisions with holograms.</span></span> 

<span data-ttu-id="0d190-129">因此，我們建議僅將 collider 放在兩手的食指上。</span><span class="sxs-lookup"><span data-stu-id="0d190-129">Hence, we suggest to only put a collider on each index finger.</span></span> <span data-ttu-id="0d190-130">可碰撞的食指指尖也可供需與其他手指搭配的各種觸控手勢作為有效觸控點，例如 1 指點按、1 指點選、2 指點按和 5 指點按，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="0d190-130">The collidable index fingertips can still serve as active touch points for diverse touch gestures involving other fingers, such as 1-finger press, 1-finger tap, 2-finger press and 5-finger press, as shown in the image below.</span></span>

![可碰撞的指尖圖](images/Collidable-Fingertip-720px.jpg)

### <a name="sphere-collider"></a><span data-ttu-id="0d190-132">球體 collider</span><span class="sxs-lookup"><span data-stu-id="0d190-132">Sphere collider</span></span>

<span data-ttu-id="0d190-133">建議您不要使用隨機的一般形狀，而應使用球體 collider。</span><span class="sxs-lookup"><span data-stu-id="0d190-133">Instead of using a random generic shape, we suggest you use a sphere collider.</span></span> <span data-ttu-id="0d190-134">然後，以視覺化方式加以呈現，為近距離目標鎖定提供明確的提示。</span><span class="sxs-lookup"><span data-stu-id="0d190-134">Then visually render it to provide better cues for near targeting.</span></span> <span data-ttu-id="0d190-135">球體的直徑應符合食指的粗細，以提高觸控的正確性。</span><span class="sxs-lookup"><span data-stu-id="0d190-135">The sphere's diameter should match the thickness of the index finger to increase touch accuracy.</span></span> <span data-ttu-id="0d190-136">呼叫手部 API，更容易擷取手指粗細的變數。</span><span class="sxs-lookup"><span data-stu-id="0d190-136">It easier to retrieve the variable of finger thickness by calling the hand API.</span></span>

### <a name="fingertip-cursor"></a><span data-ttu-id="0d190-137">指尖游標</span><span class="sxs-lookup"><span data-stu-id="0d190-137">Fingertip cursor</span></span>

<span data-ttu-id="0d190-138">除了在食指指尖上顯示可碰撞的球體以外，我們也建立了進階的指尖游標，以提供更好的近距離目標鎖定互動體驗。</span><span class="sxs-lookup"><span data-stu-id="0d190-138">In addition to rendering a collidable sphere on the index fingertip, we've created an advanced fingertip cursor to interactively achieve a better near-targeting experience.</span></span> <span data-ttu-id="0d190-139">這是連結至食指指尖的一個環狀游標。</span><span class="sxs-lookup"><span data-stu-id="0d190-139">It is a donut-shaped cursor attached to the index fingertip.</span></span> <span data-ttu-id="0d190-140">它會根據鄰近性，在方向和大小方面動態回應目標，詳述如下：</span><span class="sxs-lookup"><span data-stu-id="0d190-140">According to proximity, it dynamically reacts to a target in terms of orientation and size as detailed below:</span></span>

* <span data-ttu-id="0d190-141">當食指移向全像投影時，游標一律會與全像投影的表面平行，且其大小會隨之逐漸縮減。</span><span class="sxs-lookup"><span data-stu-id="0d190-141">When an index finger moves toward a hologram, the cursor is always parallel to the hologram's surface and gradually shrinks its size accordingly.</span></span>
* <span data-ttu-id="0d190-142">當手指接觸到表面時，游標會縮減為一個點，並發出觸控事件。</span><span class="sxs-lookup"><span data-stu-id="0d190-142">As soon as the finger touches the surface, the cursor shrinks into a dot and emits a touch event.</span></span>

<span data-ttu-id="0d190-143">透過互動式反饋，使用者可執行高精確度的近距離目標鎖定工作，例如觸發超連結或按下按鈕，如下所示。</span><span class="sxs-lookup"><span data-stu-id="0d190-143">With interactive feedback, users can achieve high precision near-targeting tasks, such as triggering a hyperlink or pressing a button as shown below.</span></span> 

![指尖游標圖](images/Fingertip-Cursor-720px.jpg)

## <a name="bounding-box-with-proximity-shader"></a><span data-ttu-id="0d190-145">週框方塊與近接著色器</span><span class="sxs-lookup"><span data-stu-id="0d190-145">Bounding box with proximity shader</span></span>

<span data-ttu-id="0d190-146">全像投影本身也須具備提供視覺和聽覺反饋的能力，以彌補觸覺反饋能力的不足。</span><span class="sxs-lookup"><span data-stu-id="0d190-146">The hologram itself also requires the ability to provide both visual and audio feedback to compensate the lack of tactile feedback.</span></span> <span data-ttu-id="0d190-147">為此，我們設計了週框方塊與近接著色器的概念。</span><span class="sxs-lookup"><span data-stu-id="0d190-147">For that, we generate the concept of a bounding box with a proximity shader.</span></span> <span data-ttu-id="0d190-148">週框方塊是足以包覆一個 3D 物件的最小體積區域。</span><span class="sxs-lookup"><span data-stu-id="0d190-148">A bounding box is a minimum volumetric area that encloses a 3D object.</span></span> <span data-ttu-id="0d190-149">週框方塊具有互動式呈現機制，名為近接著色器。</span><span class="sxs-lookup"><span data-stu-id="0d190-149">The bounding box has an interactive rendering mechanism called a proximity shader.</span></span> <span data-ttu-id="0d190-150">近接著色器的行為如下：</span><span class="sxs-lookup"><span data-stu-id="0d190-150">The proximity shader behaves:</span></span>

* <span data-ttu-id="0d190-151">當食指進入範圍內時，手指焦點即會投射在週框方塊的表面。</span><span class="sxs-lookup"><span data-stu-id="0d190-151">When the index finger is within a range, a fingertip spotlight is cast on the surface of the bounding box.</span></span>
* <span data-ttu-id="0d190-152">當指尖越來越接近表面時，焦點會隨之逐漸縮小。</span><span class="sxs-lookup"><span data-stu-id="0d190-152">When the fingertip gets closer to the surface, the spotlight shrinks accordingly.</span></span>
* <span data-ttu-id="0d190-153">手指一碰到表面時，整個週框方塊就會變色，或產生視覺效果以反映觸碰狀態。</span><span class="sxs-lookup"><span data-stu-id="0d190-153">As soon as the fingertip touches the surface, the entire bounding box changes color or generates visual effects to reflect the touch state.</span></span>
* <span data-ttu-id="0d190-154">此外也可以啟用音效來補強視覺的觸碰反饋。</span><span class="sxs-lookup"><span data-stu-id="0d190-154">A sound effect can also be activated to enhance the visual touch feedback.</span></span>

![週框方塊與近接著色器圖](images/Bounding-Box-With-Proximity-Shader-720px.jpg)

## <a name="pressable-button"></a><span data-ttu-id="0d190-156">可點按的按鈕</span><span class="sxs-lookup"><span data-stu-id="0d190-156">Pressable button</span></span>

<span data-ttu-id="0d190-157">有了可碰撞的指尖，使用者即可與基本的全像攝影 UI 元件互動，例如可點按的按鈕。</span><span class="sxs-lookup"><span data-stu-id="0d190-157">With a collidable fingertip, users are now ready to interact with the fundamental holographic UI component, sucha as a pressable button.</span></span> <span data-ttu-id="0d190-158">可點按的按鈕是專為直接手指點按設計的全像攝影按鈕。</span><span class="sxs-lookup"><span data-stu-id="0d190-158">A pressable button is a holographic button tailored for a direct finger press.</span></span> <span data-ttu-id="0d190-159">同樣地，由於缺少觸覺反饋，可點按的按鈕也設有若干機制來處理觸覺反饋的相關問題。</span><span class="sxs-lookup"><span data-stu-id="0d190-159">Again, due to the lack of tactile feedback, a pressable button equips a couple mechanisms to tackle tactile feedback-related issues.</span></span>

* <span data-ttu-id="0d190-160">第一項機制是具有近接著色器的週框方塊，其詳細說明請見上一節。</span><span class="sxs-lookup"><span data-stu-id="0d190-160">The first mechanism is a bounding box with a proximity shader, which isdetailed in the previous section.</span></span> <span data-ttu-id="0d190-161">它可讓使用者在接近及觸碰按鈕時更能清楚感知鄰近性。</span><span class="sxs-lookup"><span data-stu-id="0d190-161">It give users a better sense of proximity when as approach and make contact with a button.</span></span>
* <span data-ttu-id="0d190-162">第二項機制是下壓。</span><span class="sxs-lookup"><span data-stu-id="0d190-162">The second mechanism is depression.</span></span> <span data-ttu-id="0d190-163">下壓會在指尖接觸到按鈕後，產生按下的感覺。</span><span class="sxs-lookup"><span data-stu-id="0d190-163">Depression creates a sense of pressing down after a fingertip contacts a button.</span></span> <span data-ttu-id="0d190-164">此機制的運作方式是，按鈕會緊隨著指尖沿深度軸移動。</span><span class="sxs-lookup"><span data-stu-id="0d190-164">The mechanism is that the button tightly moves with the fingertip along the depth axis.</span></span> <span data-ttu-id="0d190-165">在按鈕達到指定的深度 (按下) 或離開該深度 (放開) 之後，就會觸發按鈕。</span><span class="sxs-lookup"><span data-stu-id="0d190-165">The button can be triggered when it reaches a designated depth (on press) or leaves the depth (on release) after passing through it.</span></span>
* <span data-ttu-id="0d190-166">在觸發按鈕時應加上音效以增強反饋。</span><span class="sxs-lookup"><span data-stu-id="0d190-166">The sound effect should be added to enhance feedback when the button is triggered.</span></span>

![可點按的按鈕圖](images/Pressable-Button-720px.jpg)

## <a name="2d-slate-interaction"></a><span data-ttu-id="0d190-168">2D 平板互動</span><span class="sxs-lookup"><span data-stu-id="0d190-168">2D slate interaction</span></span>

<span data-ttu-id="0d190-169">2D 平板是裝載 2D 應用程式內容 (例如網頁瀏覽器) 的全像攝影容器。</span><span class="sxs-lookup"><span data-stu-id="0d190-169">A 2D slate is a holographic container hosting 2D app contents, such as web browser.</span></span> <span data-ttu-id="0d190-170">透過直接操作與 2D 平板互動的設計概念，是運用與實體觸控螢幕互動的心智模型。</span><span class="sxs-lookup"><span data-stu-id="0d190-170">The design concept for interacting with a 2D slate via direct manipulation is to leverage the mental model of interacting with a physical touch screen.</span></span>

<span data-ttu-id="0d190-171">若要與觸控平板互動：</span><span class="sxs-lookup"><span data-stu-id="0d190-171">To interact with the slate contact:</span></span>

* <span data-ttu-id="0d190-172">以食指按下超連結或按鈕。</span><span class="sxs-lookup"><span data-stu-id="0d190-172">Use an index finger to press a hyperlink or a button.</span></span>
* <span data-ttu-id="0d190-173">以食指向上和向下捲動平板內容。</span><span class="sxs-lookup"><span data-stu-id="0d190-173">Use an index finger to scroll a slate content up and down.</span></span>
* <span data-ttu-id="0d190-174">使用者可用兩根食指，根據手指的相對移動來放大和縮小平板內容。</span><span class="sxs-lookup"><span data-stu-id="0d190-174">The user's two index fingers are used to zoom in and out of the slate content, according to the relative motion of the fingers.</span></span>

![2D 平板影像](images/2D-Slate-Interaction-720px.jpg)

<span data-ttu-id="0d190-176">操作 2D 平板本身：</span><span class="sxs-lookup"><span data-stu-id="0d190-176">For manipulating the 2D slate itself:</span></span>

* <span data-ttu-id="0d190-177">將手指向角落或邊緣時，可顯示最接近的操作能供性。</span><span class="sxs-lookup"><span data-stu-id="0d190-177">Approach your hands toward corners and edges to reveal the closest manipulation affordances.</span></span>
* <span data-ttu-id="0d190-178">抓取操作能供性，並透過角落能供性執行統一尺寸調整，以及透過邊緣能供性進行自動重排。</span><span class="sxs-lookup"><span data-stu-id="0d190-178">Grab the manipulation affordances, and perform uniform scaling through the corner affordances, and reflow via the edge affordances.</span></span>
* <span data-ttu-id="0d190-179">抓取 2D 平板上方的 holobar，可以移動整個平板。</span><span class="sxs-lookup"><span data-stu-id="0d190-179">Grab the holobar at the top of the 2D slate, which lets you move the whole slate.</span></span>

![平板操作圖](images/Manipulate-2d-slate-720px.jpg)

## <a name="3d-object-manipulation"></a><span data-ttu-id="0d190-181">3D 物件操作</span><span class="sxs-lookup"><span data-stu-id="0d190-181">3D object manipulation</span></span>

<span data-ttu-id="0d190-182">HoloLens 2 可讓使用者將週框方塊套用至每個 3D 物件，以便用手直接操作 3D 全像攝影物件。</span><span class="sxs-lookup"><span data-stu-id="0d190-182">HoloLens 2 lets lets users enable their hands to direct manipulate 3D holographic objects by applying a bounding box to each 3D object.</span></span> <span data-ttu-id="0d190-183">週框方塊可透過其近接著色器提供更確切的深度認知。</span><span class="sxs-lookup"><span data-stu-id="0d190-183">The bounding box provides better depth perception through its proximity shader.</span></span> <span data-ttu-id="0d190-184">週框方塊衍生出兩種 3D 物件操作方法。</span><span class="sxs-lookup"><span data-stu-id="0d190-184">With the bounding box, there are two design approaches for 3D object manipulation.</span></span>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="0d190-185">能供性操作</span><span class="sxs-lookup"><span data-stu-id="0d190-185">Affordance-based manipulation</span></span>

<span data-ttu-id="0d190-186">能供性操作可讓您透過週框方塊及其周圍的操作能供性來操作 3D 物件。</span><span class="sxs-lookup"><span data-stu-id="0d190-186">Affordance-base manipulation lets you manipulate the 3D object through a bounding box along with the manipulation affordances around it.</span></span> <span data-ttu-id="0d190-187">當使用者的手接近 3D 物件時，就會顯示週框方塊和最接近的能供性。</span><span class="sxs-lookup"><span data-stu-id="0d190-187">As soon as a user's hand is close to a 3D object, the bounding box and the nearest affordance are revealed.</span></span> <span data-ttu-id="0d190-188">使用者可以抓住週框方塊以移動整個物件，抓住邊緣能供性以旋轉物件，和抓住角落能供性以統一調整物件大小。</span><span class="sxs-lookup"><span data-stu-id="0d190-188">Users can grab the bounding box to move the whole object, the edge affordances to rotate and the corner affordances to scale uniformly.</span></span>

![3D 物件操作圖](images/3D-Object-Manipulation-720px.jpg)

### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="0d190-190">非能供性操作</span><span class="sxs-lookup"><span data-stu-id="0d190-190">Non-affordance based manipulation</span></span>

<span data-ttu-id="0d190-191">非能供性操作不會將能供性連結至週框方塊。</span><span class="sxs-lookup"><span data-stu-id="0d190-191">Non-affordance-based manipulation does not attach affordance to the bounding box.</span></span> <span data-ttu-id="0d190-192">使用者只能顯示週框方塊，然後直接與它互動。</span><span class="sxs-lookup"><span data-stu-id="0d190-192">Users can only reveal the bounding box, then directly interact with it.</span></span> <span data-ttu-id="0d190-193">若以一隻手抓住週框方塊，物件的轉譯和旋轉會與那隻手的動作和方向相關聯。</span><span class="sxs-lookup"><span data-stu-id="0d190-193">If the bounding box is grabbed with one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="0d190-194">以雙手抓住物件時，使用者可以根據兩隻手的相對動作來轉譯、縮放及旋轉物件。</span><span class="sxs-lookup"><span data-stu-id="0d190-194">When the object is grabbed with two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span>

<span data-ttu-id="0d190-195">特定操作需要精確度。</span><span class="sxs-lookup"><span data-stu-id="0d190-195">Specific manipulation requires precision.</span></span> <span data-ttu-id="0d190-196">建議您使用**能供性操作**，因為它可提供高層級的細微性。</span><span class="sxs-lookup"><span data-stu-id="0d190-196">We recommend that you use **affordance-based manipulation** because it provides a high level of granularity.</span></span> <span data-ttu-id="0d190-197">針對彈性操作，建議您使用**非能供性操作**，因為它可帶來即時而有趣的體驗。</span><span class="sxs-lookup"><span data-stu-id="0d190-197">For flexible manipulation, we recommend you use **non-affordance manipulation** as it allows for instant and playful experiences.</span></span>

## <a name="instinctual-gestures"></a><span data-ttu-id="0d190-198">本能手勢</span><span class="sxs-lookup"><span data-stu-id="0d190-198">Instinctual gestures</span></span>

<span data-ttu-id="0d190-199">在 HoloLens (第 1 代) 推出時，我們曾教過使用者幾個預先定義的手勢，例如綻開和空中點選。</span><span class="sxs-lookup"><span data-stu-id="0d190-199">With HoloLens (1st Gen), we taught users a couple predefined gestures, such as bloom and air tap.</span></span> <span data-ttu-id="0d190-200">而在使用 HoloLens 2 時，使用者並不需要記住任何象徵性的手勢。</span><span class="sxs-lookup"><span data-stu-id="0d190-200">For HoloLens 2, we don't ask users to memorize any symbolic gestures.</span></span> <span data-ttu-id="0d190-201">使用者與全像投影和內容互動時所需使用的所有必要手勢，都是符合本能的。</span><span class="sxs-lookup"><span data-stu-id="0d190-201">All required user gestures--where users need to interact with holograms and content--are instinctual.</span></span> <span data-ttu-id="0d190-202">協助使用者透過 UI 能供性的設計執行手勢，他們就能學會本能手勢。</span><span class="sxs-lookup"><span data-stu-id="0d190-202">The way to achieve instinctual gestures is to help users perform gestures through the design of UI affordances.</span></span>

<span data-ttu-id="0d190-203">例如，如果我們引導使用者以兩指捏合抓取某個物件或控制點，表示該物件或控制點應該很小。</span><span class="sxs-lookup"><span data-stu-id="0d190-203">For example, if we encourage the user to grab an object or a control point with a two finger pinch, the object or the control point should be small.</span></span> <span data-ttu-id="0d190-204">如果我們要使用者執行五指抓取，表示該物件或控制點應該較大。</span><span class="sxs-lookup"><span data-stu-id="0d190-204">If we want the user to perform five finger grab, the object or the control point should be relatively large.</span></span> <span data-ttu-id="0d190-205">和按鈕一樣，小按鈕就必須以單指點按，而對於大按鈕，使用者就應該用手掌來按壓。</span><span class="sxs-lookup"><span data-stu-id="0d190-205">Similar to buttons, a tiny button would limit users to press it with a single finger; a large button would encourage users to press it with their palms.</span></span>

![](images/Instinctual-Gestures-720px.jpg)

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a><span data-ttu-id="0d190-206">手部與 6 DoF 控制器之間的對稱設計</span><span class="sxs-lookup"><span data-stu-id="0d190-206">Symmetric design between hands and 6 DoF controllers</span></span>

<span data-ttu-id="0d190-207">您可能已經注意到，AR 中的手勢與 VR 中的運動控制器在互動方式上有其相似之處。</span><span class="sxs-lookup"><span data-stu-id="0d190-207">You may have noticed that there are interaction parallels that we can draw between hands in AR and motion controllers in VR.</span></span> <span data-ttu-id="0d190-208">這兩種輸入在其各自的環境中都可用來觸發直接操作。</span><span class="sxs-lookup"><span data-stu-id="0d190-208">Both inputs can be used to trigger direct manipulations in their respective environments.</span></span> <span data-ttu-id="0d190-209">在 HoloLens 2 中，近距離以手抓取並拖曳的效用，非常類似於 WMR 運動控制器上的抓取按鈕所能做到的。</span><span class="sxs-lookup"><span data-stu-id="0d190-209">In HoloLens 2, grabbing and dragging with hands at a close distance works much the same way as the grab button does on WMR motion controllers.</span></span> <span data-ttu-id="0d190-210">這種相似性可讓使用者在兩種平台上都能採用熟悉的互動方式，且若您決定將應用程式移轉至另一個平台，這一點可能也有幫助。</span><span class="sxs-lookup"><span data-stu-id="0d190-210">This provides users with interaction familiarity between the two platforms, and might prove useful should you ever decide to port your application from one to the other.</span></span>

## <a name="optimize-with-eye-tracking"></a><span data-ttu-id="0d190-211">透過眼球追蹤達到最佳效果</span><span class="sxs-lookup"><span data-stu-id="0d190-211">Optimize with eye tracking</span></span>

<span data-ttu-id="0d190-212">直接操作若能如預期運作，將可達到奇妙的效果。</span><span class="sxs-lookup"><span data-stu-id="0d190-212">Direct manipulation can feel magical if it works as intended.</span></span> <span data-ttu-id="0d190-213">但若無法順利將手移到想要的位置，而老是無意中觸發全像投影，挫敗感很快就會出現。</span><span class="sxs-lookup"><span data-stu-id="0d190-213">But can also quickly become frustrating if you can’t move your hand anywhere without unintentionally triggering a hologram.</span></span> <span data-ttu-id="0d190-214">眼球追蹤或許有助於判斷使用者真正的意圖。</span><span class="sxs-lookup"><span data-stu-id="0d190-214">Eye tracking can potentially help in better identifying what the user’s intent is.</span></span>

* <span data-ttu-id="0d190-215">**時機**：避免無意中觸發操作回應。</span><span class="sxs-lookup"><span data-stu-id="0d190-215">**When**: Reduce unintentionally triggering a manipulation response.</span></span> <span data-ttu-id="0d190-216">眼球追蹤有助於了解使用者目前從事的活動。</span><span class="sxs-lookup"><span data-stu-id="0d190-216">Eye tracking allows for better understanding what a user is currently engaged with.</span></span>
<span data-ttu-id="0d190-217">例如，想像您在閱讀全像攝影 (指示) 文件時，您伸手要去拿實際環境中的工具。</span><span class="sxs-lookup"><span data-stu-id="0d190-217">For example, imagine you are reading through a holographic (instructional) text when reaching over to grab you real-world work tool.</span></span>

<span data-ttu-id="0d190-218">此時，您的手不小心劃過某個您根本沒留意過的互動式全像攝影按鈕 (該按鈕可能甚至不在使用者的視野 (FoV) 內)。</span><span class="sxs-lookup"><span data-stu-id="0d190-218">By doing so, you accidentally move your hand across some interactive holographic buttons that you hadn't even noticed before (maybe it even was outside of the user's field-of-view (FoV)).</span></span>

  <span data-ttu-id="0d190-219">長話短說：如果使用者已有一段時間未注視某個全像投影，系統也未偵測到其觸碰或抓取事件，表示使用者可能並非真正想要與該全像投影互動。</span><span class="sxs-lookup"><span data-stu-id="0d190-219">Long story short: If the user hasn't looked at a hologram for a while, yet a touch or grasp event has been detected for it, it is likely that the user wasn't actually intending to interact with that hologram.</span></span>

* <span data-ttu-id="0d190-220">**標的**：除了處理誤判的啟用以外，它還有助於判斷所應抓取或觸碰的全像投影，因為從您的視角可能無法看出精準的交叉點，尤其是有數個全像投影的位置彼此十分靠近時。</span><span class="sxs-lookup"><span data-stu-id="0d190-220">**Which one**:  Aside from addressing false positive activations, another example includes better identifying which holograms to grab or poke as the precise intersection point may not be clear from your perspective, especially if several holograms are positioned close to each other.</span></span>

  <span data-ttu-id="0d190-221">雖然 HoloLens 2 的眼球追蹤在判斷眼睛視線的精準度方面有其特定限制，但對近距離互動而言仍不失為有利的工具，因為透過手部輸入互動時，會有深度的差異。</span><span class="sxs-lookup"><span data-stu-id="0d190-221">While eye tracking on HoloLens 2 has a certain limitation on how accurately it can determine you eye gaze, this can still be very helpful for near interactions due to depth disparity when interacting with hand input.</span></span> <span data-ttu-id="0d190-222">這表示，要判斷您的手是在全像投影的後面還是前面，而精確地抓取操作工具 (舉例而言)，有時是很困難的。</span><span class="sxs-lookup"><span data-stu-id="0d190-222">This means that it is sometimes difficult to determine whether your hand is behind or in front of a hologram to precisely grab a manipulation widget, for example.</span></span>

* <span data-ttu-id="0d190-223">**目的地**：運用使用者在執行快速拋投手勢時看往何處的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0d190-223">**Where to**: Use information about what a user is looking at with quick-throwing gestures.</span></span> <span data-ttu-id="0d190-224">抓取全像投影並約略拋向您要的目的地。</span><span class="sxs-lookup"><span data-stu-id="0d190-224">Grab a hologram and roughly toss it toward your intended destination.</span></span>  

    <span data-ttu-id="0d190-225">雖然這有時行得通，但快速執行手勢可能會導致目的地嚴重失準。</span><span class="sxs-lookup"><span data-stu-id="0d190-225">While this sometimes works, quickly performing hand gestures may result in highly inaccurate destinations.</span></span> <span data-ttu-id="0d190-226">在此情況下，同時運用眼球追蹤或可改善手勢的準確度。</span><span class="sxs-lookup"><span data-stu-id="0d190-226">In this scenario including eye tracking could improve the accuracy of the gesture.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d190-227">請參閱</span><span class="sxs-lookup"><span data-stu-id="0d190-227">See also</span></span>

* [<span data-ttu-id="0d190-228">頭部注視並認可</span><span class="sxs-lookup"><span data-stu-id="0d190-228">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="0d190-229">手部指向和行動</span><span class="sxs-lookup"><span data-stu-id="0d190-229">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="0d190-230">本能互動</span><span class="sxs-lookup"><span data-stu-id="0d190-230">Instinctual interactions</span></span>](interaction-fundamentals.md)

