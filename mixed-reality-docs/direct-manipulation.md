---
title: 手部直接操作
description: 直接操作輸入模型概觀
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境, 注視, 定向注視, 互動, 設計, 手部接近, HoloLens
ms.openlocfilehash: 6e3512eab4070680c48ee8e95240a17e9925822f
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66402386"
---
# <a name="direct-manipulation-with-hands"></a><span data-ttu-id="a56b5-104">手部直接操作</span><span class="sxs-lookup"><span data-stu-id="a56b5-104">Direct manipulation with hands</span></span>
<span data-ttu-id="a56b5-105">直接操作是直接以雙手觸控全像投影的輸入模型。</span><span class="sxs-lookup"><span data-stu-id="a56b5-105">Direct manipulation is an input model that involves touching holograms directly with your hands.</span></span> <span data-ttu-id="a56b5-106">直接操作的目標是讓物件如同在真實環境中作動。</span><span class="sxs-lookup"><span data-stu-id="a56b5-106">The goal with direct manipulation is that objects behave just as they do in the real world.</span></span> <span data-ttu-id="a56b5-107">按鈕只要按下即可啟用、物件可藉由抓取來選取，2D 內容的行為則類似於虛擬觸控螢幕。</span><span class="sxs-lookup"><span data-stu-id="a56b5-107">Buttons can be activated simply by pressing them, objects can be picked up by grabbing them, and 2D content behaves like a virtual touchscreen.</span></span>  <span data-ttu-id="a56b5-108">因此，直接操作很容易上手，而且很有趣。</span><span class="sxs-lookup"><span data-stu-id="a56b5-108">Because of this, direct manipulation is easy for users to learn, and it's fun too.</span></span>  <span data-ttu-id="a56b5-109">我們將其視為「近距離」輸入模型，這表示它最適合用於伸手可及範圍內的內容互動。</span><span class="sxs-lookup"><span data-stu-id="a56b5-109">It is considered a "near" input model, meaning it is best used for interacting with content that is within arms reach.</span></span>

<span data-ttu-id="a56b5-110">直接操作以能供性為基礎，這表示它很容易使用。</span><span class="sxs-lookup"><span data-stu-id="a56b5-110">Direct manipulation is affordance-based, meaning it's user friendly.</span></span> <span data-ttu-id="a56b5-111">使用者不需學習任何象徵性的手勢。</span><span class="sxs-lookup"><span data-stu-id="a56b5-111">There are no symbolic gestures to teach users.</span></span> <span data-ttu-id="a56b5-112">所有互動都是以您可觸摸或抓取的視覺化元素為基礎。</span><span class="sxs-lookup"><span data-stu-id="a56b5-112">All interactions are built around a visual element that you can touch or grab.</span></span>

## <a name="device-support"></a><span data-ttu-id="a56b5-113">裝置支援</span><span class="sxs-lookup"><span data-stu-id="a56b5-113">Device support</span></span>


| <span data-ttu-id="a56b5-114">輸入模型</span><span class="sxs-lookup"><span data-stu-id="a56b5-114">Input Model</span></span> | [<span data-ttu-id="a56b5-115">HoloLens (第 1 代)</span><span class="sxs-lookup"><span data-stu-id="a56b5-115">HoloLens (1st gen)</span></span>](hololens-hardware-details.md) | <span data-ttu-id="a56b5-116">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a56b5-116">HoloLens 2</span></span> |[<span data-ttu-id="a56b5-117">沉浸式頭戴裝置</span><span class="sxs-lookup"><span data-stu-id="a56b5-117">Immersive headsets</span></span>](immersive-headset-hardware-details.md)|
|:-------- | :-------| :--------| :------------|
| <span data-ttu-id="a56b5-118">手部直接操作</span><span class="sxs-lookup"><span data-stu-id="a56b5-118">Direct manipulation with hands</span></span> | <span data-ttu-id="a56b5-119">❌ 不支援</span><span class="sxs-lookup"><span data-stu-id="a56b5-119">❌ Not supported</span></span> | <span data-ttu-id="a56b5-120">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="a56b5-120">✔️ Recommended</span></span> | <span data-ttu-id="a56b5-121">➕ 建議使用替代方案[手部指向和行動](point-and-commit.md)。</span><span class="sxs-lookup"><span data-stu-id="a56b5-121">➕ An alternative, [point and commit with hands](point-and-commit.md) is recommended.</span></span>

<span data-ttu-id="a56b5-122">直接操作是 HoloLens 2 的主要輸入模型，採用新式連貫手部追蹤系統。</span><span class="sxs-lookup"><span data-stu-id="a56b5-122">Direct manipulation is a primary input model on HoloLens 2, and utilizes the new articulated hand-tracking system.</span></span> <span data-ttu-id="a56b5-123">輸入模型也可透過運動控制器的使用在沉浸式頭戴裝置上運作，但對於物件操作以外的互動，不建議以此作為主要機制。</span><span class="sxs-lookup"><span data-stu-id="a56b5-123">The input model is also available on immersive headsets through the use of motion controllers, but is not recommended as a primary means of interaction outside of object manipulation.</span></span>  <span data-ttu-id="a56b5-124">在 HoloLens (第 1 代) 上無法進行直接操作。</span><span class="sxs-lookup"><span data-stu-id="a56b5-124">Direct manipluation is not available on HoloLens (1st gen).</span></span>


## <a name="collidable-fingertip"></a><span data-ttu-id="a56b5-125">可碰撞的指尖</span><span class="sxs-lookup"><span data-stu-id="a56b5-125">Collidable fingertip</span></span>

<span data-ttu-id="a56b5-126">在 HoloLens 2 上，使用者實際的雙手會被辨識和解譯為左右兩手的架構模型。</span><span class="sxs-lookup"><span data-stu-id="a56b5-126">On HoloLens 2, the user's real hands are recognized and interpreted as left and right hand skeletal models.</span></span> <span data-ttu-id="a56b5-127">若要實作直接以雙手觸控全像投影的概念，在理想情況下，5 個 collider 可以連結至左右兩手架構模型的 5 個指尖。</span><span class="sxs-lookup"><span data-stu-id="a56b5-127">To implement the idea of touching holograms directly with hands, ideally, 5 colliders could be attached to 5 fingertips of each hand skeletal model.</span></span> <span data-ttu-id="a56b5-128">但實際上，由於缺少觸覺反饋能力，10 個可碰撞的指尖會對全像投影造成非預期且無法預測的衝突。</span><span class="sxs-lookup"><span data-stu-id="a56b5-128">However, practically, due to the lack of tactile feedback, 10 collidable fingertips caused unexpected and unpredictable collisions with holograms.</span></span> 

<span data-ttu-id="a56b5-129">因此，我們建議僅將 collider 放在兩手的食指上。</span><span class="sxs-lookup"><span data-stu-id="a56b5-129">Hence, we suggest to only put a collider on each index finger.</span></span> <span data-ttu-id="a56b5-130">可碰撞的食指指尖也可供需與其他手指搭配的各種觸控手勢作為有效觸控點，例如 1 指點按、1 指點選、2 指點按和 5 指點按，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="a56b5-130">The collidable index fingertips can still serve as active touch points for diverse touch gestures involving other fingers, such as 1-finger press, 1-finger tap, 2-finger press and 5-finger press, as shown in the image below.</span></span>

![可碰撞的指尖圖](images/Collidable-Fingertip-720px.jpg)

### <a name="sphere-collider"></a><span data-ttu-id="a56b5-132">球體 collider</span><span class="sxs-lookup"><span data-stu-id="a56b5-132">Sphere collider</span></span>

<span data-ttu-id="a56b5-133">我們建議不要使用隨機的一般形狀，而是使用球體 collider，並以視覺化方式加以呈現，為近距離目標鎖定提供明確的提示。</span><span class="sxs-lookup"><span data-stu-id="a56b5-133">Instead of using a random generic shape, we suggest to use a sphere collider and to visually render it to provide better cues for near targeting.</span></span> <span data-ttu-id="a56b5-134">球體的直徑應符合食指的粗細，以提高觸控的正確性。</span><span class="sxs-lookup"><span data-stu-id="a56b5-134">The sphere's diameter should match the thickness of the index finger to increase touch accuracy.</span></span> <span data-ttu-id="a56b5-135">只要呼叫手部 API 即可輕易擷取手指粗細的變數。</span><span class="sxs-lookup"><span data-stu-id="a56b5-135">It will be easy to retrieve the variable of finger thickness by calling the hand API.</span></span>

### <a name="fingertip-cursor"></a><span data-ttu-id="a56b5-136">指尖游標</span><span class="sxs-lookup"><span data-stu-id="a56b5-136">Fingertip cursor</span></span>

<span data-ttu-id="a56b5-137">除了在食指上顯示可碰撞的球體以外，我們也提供了指尖游標這個進階解決方案，以提供更好的近距離目標鎖定互動體驗。</span><span class="sxs-lookup"><span data-stu-id="a56b5-137">In addition to rendering a collidable sphere on the index fingertip, we've created an advanced solution, fingertip cursor, to achieve better near-targeting experience interactively.</span></span> <span data-ttu-id="a56b5-138">這是連結在食指上的一個環狀游標。</span><span class="sxs-lookup"><span data-stu-id="a56b5-138">It is a donut-shaped cursor attached on the index fingertip.</span></span> <span data-ttu-id="a56b5-139">它會根據鄰近性，在方向和大小方面動態回應目標，詳述如下：</span><span class="sxs-lookup"><span data-stu-id="a56b5-139">According to proximity, it dynamically reacts to a target in terms of orientation and size as detailed below:</span></span>

* <span data-ttu-id="a56b5-140">當食指移向全像投影時，游標一律會與全像投影的表面平行，並其大小會隨之逐漸縮減。</span><span class="sxs-lookup"><span data-stu-id="a56b5-140">When an index finger moves toward a hologram, the cursor is always parallel to the hologram's surface  and gradually shrinks its size accordingly.</span></span>
* <span data-ttu-id="a56b5-141">當手指接觸到表面時，游標會縮減為一個點，並發出觸控事件。</span><span class="sxs-lookup"><span data-stu-id="a56b5-141">As soon as the finger touches the surface, the cursor shrinks into a dot and emits a touch event.</span></span>

<span data-ttu-id="a56b5-142">透過互動式反饋，使用者可執行高精準度的近距離目標鎖定工作，例如觸發網頁內容的超連結或按下按鈕，如下所示。</span><span class="sxs-lookup"><span data-stu-id="a56b5-142">With the interactive feedback, users can achieve high precision near targeting tasks, such as triggering a hyperlink on web content or pressing a button, as shown, below.</span></span> 

![指尖游標圖](images/Fingertip-Cursor-720px.jpg)

## <a name="bounding-box-with-proximity-shader"></a><span data-ttu-id="a56b5-144">週框方塊與近接著色器</span><span class="sxs-lookup"><span data-stu-id="a56b5-144">Bounding box with proximity shader</span></span>

<span data-ttu-id="a56b5-145">全像投影本身也須具備提供視覺和聽覺反饋的能力，以彌補觸覺反饋能力的不足。</span><span class="sxs-lookup"><span data-stu-id="a56b5-145">The hologram itself also requires the ability to provide both visual and audio feedback to compensate the lack of tactile feedback.</span></span> <span data-ttu-id="a56b5-146">為此，我們設計了週框方塊與近接著色器的概念。</span><span class="sxs-lookup"><span data-stu-id="a56b5-146">For that, we generate the concept of a bounding box with proximity shader.</span></span> <span data-ttu-id="a56b5-147">週框方塊是足以包覆一個 3D 物件的最小體積區域。</span><span class="sxs-lookup"><span data-stu-id="a56b5-147">A bounding box is a minimum volumetric area that encloses a 3D object.</span></span> <span data-ttu-id="a56b5-148">週框方塊具有互動式呈現機制，名為近接著色器。</span><span class="sxs-lookup"><span data-stu-id="a56b5-148">The bounding box has an interactive rendering mechanism called proximity shader.</span></span> <span data-ttu-id="a56b5-149">近接著色器的行為如下：</span><span class="sxs-lookup"><span data-stu-id="a56b5-149">The proximity shader behaves:</span></span>

* <span data-ttu-id="a56b5-150">當食指進入範圍內時，手指焦點即會投射在週框方塊的表面。</span><span class="sxs-lookup"><span data-stu-id="a56b5-150">When the index finger is within a range, a fingertip spotlight is cast on the surface of bounding box.</span></span>
* <span data-ttu-id="a56b5-151">當指尖越來越接近表面時，焦點會隨之逐漸聚焦。</span><span class="sxs-lookup"><span data-stu-id="a56b5-151">When the fingertip gets closer to the surface, the spotlight condenses accordingly.</span></span>
* <span data-ttu-id="a56b5-152">手指一碰到表面時，整個週框方塊就會變色，或產生視覺效果以反映觸碰狀態。</span><span class="sxs-lookup"><span data-stu-id="a56b5-152">As soon as the fingertip touch the surface, the whole bounding box changes the color or generate visual effect to reflect the touch state.</span></span>
* <span data-ttu-id="a56b5-153">此外，也可以啟用音效來補強視覺的觸碰反饋。</span><span class="sxs-lookup"><span data-stu-id="a56b5-153">Meanwhile, a sound effect can be activated to enhance the visual touch feedback.</span></span>

![週框方塊與近接著色器圖](images/Bounding-Box-With-Proximity-Shader-720px.jpg)

## <a name="pressable-button"></a><span data-ttu-id="a56b5-155">可點按的按鈕</span><span class="sxs-lookup"><span data-stu-id="a56b5-155">Pressable button</span></span>

<span data-ttu-id="a56b5-156">有了可碰撞的指尖，使用者即可與非常基本的全像攝影 UI 元件互動，也就是可點按的按鈕。</span><span class="sxs-lookup"><span data-stu-id="a56b5-156">With a collidable fingertip, users are now ready to interact with the very fundamental holographic UI component, pressable button.</span></span> <span data-ttu-id="a56b5-157">可點按的按鈕是專為直接手指點按設計的全像攝影按鈕。</span><span class="sxs-lookup"><span data-stu-id="a56b5-157">A pressable button is a holographic button tailored for direct finger press.</span></span> <span data-ttu-id="a56b5-158">同樣地，由於缺少觸覺反饋，可點按的按鈕也設有若干機制來處理觸覺反饋的相關問題。</span><span class="sxs-lookup"><span data-stu-id="a56b5-158">Again, due to the lack of tactile feedback, a pressable button equips a couple mechanisms to tackle tactile feedback-related issues.</span></span>

* <span data-ttu-id="a56b5-159">第一項機制是具有近接著色器的週框方塊，其詳細說明請見上一節。</span><span class="sxs-lookup"><span data-stu-id="a56b5-159">The first mechanism is a bounding box with proximity shader, detailed in the previous section.</span></span> <span data-ttu-id="a56b5-160">它可讓使用者在接近及觸碰按鈕時更能清楚感知鄰近性。</span><span class="sxs-lookup"><span data-stu-id="a56b5-160">It serves to provide better sense of proximity for users to approach and make contact with a button.</span></span>
* <span data-ttu-id="a56b5-161">第二項機制是下壓。</span><span class="sxs-lookup"><span data-stu-id="a56b5-161">The second one is depression.</span></span> <span data-ttu-id="a56b5-162">它會在指尖接觸到按鈕後，產生按下的感覺。</span><span class="sxs-lookup"><span data-stu-id="a56b5-162">It creates sense of press, after a fingertip contacts the button.</span></span> <span data-ttu-id="a56b5-163">此機制的運作方式是，按鈕會緊隨著指尖沿深度軸移動。</span><span class="sxs-lookup"><span data-stu-id="a56b5-163">The mechanism is that the button tightly moves with the fingertip along the depth axis.</span></span> <span data-ttu-id="a56b5-164">在按鈕達到指定的深度 (按下) 或離開該深度 (放開) 之後，就會觸發按鈕。</span><span class="sxs-lookup"><span data-stu-id="a56b5-164">The button can be triggered when it reaches a designated depth (on press) or leaves the depth (on release) after passing through it.</span></span>
* <span data-ttu-id="a56b5-165">在觸發按鈕時，也應加上音效以增強反饋。</span><span class="sxs-lookup"><span data-stu-id="a56b5-165">The sound effect should be added to enhance feedback, when the button is triggered.</span></span>

![可點按的按鈕圖](images/Pressable-Button-720px.jpg)

## <a name="2d-slate-interaction"></a><span data-ttu-id="a56b5-167">2D 平板互動</span><span class="sxs-lookup"><span data-stu-id="a56b5-167">2D slate interaction</span></span>

<span data-ttu-id="a56b5-168">2D 平板是裝載 2D 應用程式內容 (例如網頁瀏覽器) 的全像攝影容器。</span><span class="sxs-lookup"><span data-stu-id="a56b5-168">A 2D slate is a holographic container hosting 2D app contents, such as web browser.</span></span> <span data-ttu-id="a56b5-169">透過直接操作與 2D 平板互動的設計概念，是運用與實體觸控螢幕互動的心智模型。</span><span class="sxs-lookup"><span data-stu-id="a56b5-169">The design concept for interacting with a 2D slate via direct manipulation is to leverage the mental model of interacting with a physical touch screen.</span></span>

<span data-ttu-id="a56b5-170">若要與觸控平板互動：</span><span class="sxs-lookup"><span data-stu-id="a56b5-170">To interact with the slate contact:</span></span>

* <span data-ttu-id="a56b5-171">以食指按下超連結或按鈕。</span><span class="sxs-lookup"><span data-stu-id="a56b5-171">Use an index finger to press a hyperlink or a button.</span></span>
* <span data-ttu-id="a56b5-172">以食指向上和向下捲動平板內容。</span><span class="sxs-lookup"><span data-stu-id="a56b5-172">Use an index finger to scroll a slate content up and down.</span></span>
* <span data-ttu-id="a56b5-173">使用者可用兩根食指，根據手指的相對移動放大和縮小平版內容。</span><span class="sxs-lookup"><span data-stu-id="a56b5-173">Users use two index fingers to zoom in and out the slate content according to relative motion of fingers.</span></span>

![2D 平板影像](images/2D-Slate-Interaction-720px.jpg)

<span data-ttu-id="a56b5-175">操作 2D 平板本身：</span><span class="sxs-lookup"><span data-stu-id="a56b5-175">For manipulating the 2D slate itself:</span></span>

* <span data-ttu-id="a56b5-176">將手指向角落或邊緣時，可顯示最接近的操作能供性。</span><span class="sxs-lookup"><span data-stu-id="a56b5-176">Approach your hands toward corners and edges to reveal the closest manipulation affordances.</span></span>
* <span data-ttu-id="a56b5-177">抓取操作能供性，並透過角落能供性執行統一尺寸調整，以及透過邊緣能供性進行自動重排。</span><span class="sxs-lookup"><span data-stu-id="a56b5-177">Grab the manipulation affordances, and perform uniform scaling through the corner affordances and reflow via the edge affordances.</span></span>
* <span data-ttu-id="a56b5-178">抓取 2D 平板上方的 holobar，可以移動整個平板。</span><span class="sxs-lookup"><span data-stu-id="a56b5-178">Grab the holobar at the top of the 2D slate, which lets you move the whole slate.</span></span>

![平板操作圖](images/Manipulate-2d-slate-720px.jpg)

## <a name="3d-object-manipulation"></a><span data-ttu-id="a56b5-180">3D 物件操作</span><span class="sxs-lookup"><span data-stu-id="a56b5-180">3D object manipulation</span></span>

<span data-ttu-id="a56b5-181">HoloLens 2 可讓使用者將週框方塊套用至每個 3D 物件，以便用手直接操作 3D 全像攝影物件。</span><span class="sxs-lookup"><span data-stu-id="a56b5-181">HoloLens 2 lets lets users enable their hands to direct manipulate 3D hologramphic objects by applying a bounding box to each 3D object.</span></span> <span data-ttu-id="a56b5-182">週框方塊可透過其近接著色器提供更確切的深度認知。</span><span class="sxs-lookup"><span data-stu-id="a56b5-182">The bounding box provides better depth perception through its proximity shader.</span></span> <span data-ttu-id="a56b5-183">週框方塊衍生出兩種 3D 物件操作方法。</span><span class="sxs-lookup"><span data-stu-id="a56b5-183">With the bounding box, there are two design approaches for 3D object manipulation.</span></span>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="a56b5-184">能供性操作</span><span class="sxs-lookup"><span data-stu-id="a56b5-184">Affordance-based manipulation</span></span>

<span data-ttu-id="a56b5-185">這種方法可讓您透過週框方塊及其周圍的操作能供性來操作 3D 物件。</span><span class="sxs-lookup"><span data-stu-id="a56b5-185">This lets you manipulate the 3D object through a bounding box and the manipulation affordances around it.</span></span> <span data-ttu-id="a56b5-186">當使用者的手接近 3D 物件時，就會顯示週框方塊和最接近的能供性。</span><span class="sxs-lookup"><span data-stu-id="a56b5-186">As soon as a user's hand is close to a 3D object, the bounding box and the nearest affordance are revealed.</span></span> <span data-ttu-id="a56b5-187">使用者可以抓住週框方塊以移動整個物件，抓住邊緣能供性以旋轉物件，和抓住角落能供性以統一調整物件大小。</span><span class="sxs-lookup"><span data-stu-id="a56b5-187">Users can grab the bounding box to move the whole object, the edge affordances to rotate and the corner affordances to scale uniformly.</span></span>

![3D 物件操作圖](images/3D-Object-Manipulation-720px.jpg)

### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="a56b5-189">非能供性操作</span><span class="sxs-lookup"><span data-stu-id="a56b5-189">Non-affordance based manipulation</span></span>

<span data-ttu-id="a56b5-190">在此機制中，週框方塊不會連結任何能供性。</span><span class="sxs-lookup"><span data-stu-id="a56b5-190">In this mechanism, no affordance is attached to the bounding box.</span></span> <span data-ttu-id="a56b5-191">使用者只能顯示週框方塊，然後直接與它互動。</span><span class="sxs-lookup"><span data-stu-id="a56b5-191">Users can only reveal the bounding box, then directly interact with it.</span></span> <span data-ttu-id="a56b5-192">若以一隻手抓住週框方塊，物件的轉譯和旋轉會與那隻手的動作和方向相關聯。</span><span class="sxs-lookup"><span data-stu-id="a56b5-192">If the bounding box is grabbed with one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="a56b5-193">以雙手抓住物件時，使用者可以根據兩隻手的相對動作來轉譯、縮放及旋轉物件。</span><span class="sxs-lookup"><span data-stu-id="a56b5-193">When the object is grabbed with two hands, users can translate, scale and rotate it according to relative motions of two hands.</span></span>

<span data-ttu-id="a56b5-194">針對需要精確性的特定操作，建議您使用**能供性操作**，因為它可提供高層級的細微性。</span><span class="sxs-lookup"><span data-stu-id="a56b5-194">Specific manipulation requires precision, we recommend you use **affordance-based manipulation**, because it provides a high level of granularity.</span></span> <span data-ttu-id="a56b5-195">針對彈性操作，建議您使用**非能供性操作**，因為它可帶來即時而有趣的體驗。</span><span class="sxs-lookup"><span data-stu-id="a56b5-195">For flexible manipulation, we recommend you uses **non-affordance manipulation** is as it allows for instant and playful experiences.</span></span>

## <a name="instinctual-gestures"></a><span data-ttu-id="a56b5-196">本能手勢</span><span class="sxs-lookup"><span data-stu-id="a56b5-196">Instinctual gestures</span></span>

<span data-ttu-id="a56b5-197">在 HoloLens (第 1 代) 推出時，我們曾教過使用者幾個預先定義的手勢，例如綻開和空中點選。</span><span class="sxs-lookup"><span data-stu-id="a56b5-197">With HoloLens (1st gen), we taught users a couple predefined gestures,such as Bloom and Air Tap.</span></span> <span data-ttu-id="a56b5-198">而在使用 HoloLens 2 時，使用者並不需要記住任何象徵性的手勢。</span><span class="sxs-lookup"><span data-stu-id="a56b5-198">For HoloLens 2, we don't ask users to memorize any symbolic gestures.</span></span> <span data-ttu-id="a56b5-199">使用者與全像投影和內容互動時所需使用的所有必要手勢，都是符合本能的。</span><span class="sxs-lookup"><span data-stu-id="a56b5-199">All required user gestures, users need to interact with holograms and contents, are instinctual.</span></span> <span data-ttu-id="a56b5-200">引導使用者透過 UI 能供性的設計執行手勢，他們就能學會本能手勢。</span><span class="sxs-lookup"><span data-stu-id="a56b5-200">The way to achieve instinctual gesture is to guide users to perform gestures through the design of UI affordances.</span></span>

<span data-ttu-id="a56b5-201">例如，如果我們引導您以兩指捏合抓取某個物件或控制點，表示該物件或控制點應該很小。</span><span class="sxs-lookup"><span data-stu-id="a56b5-201">For example, if we encourage you to grab an object or a control point with two finger pinch, the object or the control point should be small.</span></span> <span data-ttu-id="a56b5-202">如果我們要您執行五指抓取，表示該物件或控制點應該較大。</span><span class="sxs-lookup"><span data-stu-id="a56b5-202">If we want you to perform five finger grab, the object or the control point should be relatively big.</span></span> <span data-ttu-id="a56b5-203">和按鈕一樣，小按鈕就必須以單指點按，而對於較大的按鈕，使用者就應該用手掌來按壓。</span><span class="sxs-lookup"><span data-stu-id="a56b5-203">Similar to buttons, a tiny button would limit users to press it with a single finger, while a huge button would encourage users to press it with their palms.</span></span>

![](images/Instinctual-Gestures-720px.jpg)

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a><span data-ttu-id="a56b5-204">手部與 6 DoF 控制器之間的對稱設計</span><span class="sxs-lookup"><span data-stu-id="a56b5-204">Symmetric design between hands and 6 DoF controllers</span></span>

<span data-ttu-id="a56b5-205">您可能已經注意到，AR 中的手勢與 VR 中的運動控制器在互動方式上有其相似之處。</span><span class="sxs-lookup"><span data-stu-id="a56b5-205">You may have noticed that there are now interaction parallels we can draw between hands in AR and motion controllers in VR.</span></span> <span data-ttu-id="a56b5-206">這兩種輸入在其各自的環境中都可用來觸發直接操作。</span><span class="sxs-lookup"><span data-stu-id="a56b5-206">Both inputs can be used to trigger direct manipulations in their respective environments.</span></span> <span data-ttu-id="a56b5-207">在 HoloLens 2 中，近距離以手抓取並拖曳的效用，非常類似於運動控制器的抓取按鈕在 WMR 中所能做到的。</span><span class="sxs-lookup"><span data-stu-id="a56b5-207">In HoloLens 2, grabbing and dragging with hands at a close distance works much in the same way as the grab button does on the motion controllers in WMR.</span></span> <span data-ttu-id="a56b5-208">這種相似性可讓使用者在兩種平台上都能採用熟悉的互動方式，且若您決定將應用程式移轉至另一個平台，這一點可能也有幫助。</span><span class="sxs-lookup"><span data-stu-id="a56b5-208">This provides users with interaction familiarity between the two platforms and may prove useful should you ever decide to port your app from one to the other.</span></span>

## <a name="optimize-with-eye-tracking"></a><span data-ttu-id="a56b5-209">透過眼球追蹤達到最佳效果</span><span class="sxs-lookup"><span data-stu-id="a56b5-209">Optimize with eye tracking</span></span>

<span data-ttu-id="a56b5-210">直接操作若能如預期運作，將可達到奇妙的效果，但無法順利將手移到想要的位置，而老是無意中觸發全像投影，挫敗感很快就會出現。</span><span class="sxs-lookup"><span data-stu-id="a56b5-210">Direct manipulation can feel magical if it works as intended, but can also quickly become frustrating if you can’t move your hand anywhere anymore without unintentionally triggering a hologram.</span></span>
<span data-ttu-id="a56b5-211">眼球追蹤或許有助於判斷使用者真正的意圖。</span><span class="sxs-lookup"><span data-stu-id="a56b5-211">Eye tracking can potentially help in better identifying what the user’s intent is.</span></span>

* <span data-ttu-id="a56b5-212">**時機**：避免錯誤地觸發操作回應。</span><span class="sxs-lookup"><span data-stu-id="a56b5-212">**When**: Reduce falsely triggering a manipulation response.</span></span> <span data-ttu-id="a56b5-213">眼球追蹤有助於了解使用者目前從事的活動。</span><span class="sxs-lookup"><span data-stu-id="a56b5-213">Eye tracking allows for better understanding what a user is currently engaged with.</span></span>
<span data-ttu-id="a56b5-214">例如，想像您在閱讀全像攝影 (指示) 文件時，您伸手要去拿實際環境中的工具。</span><span class="sxs-lookup"><span data-stu-id="a56b5-214">For example, imagine you are reading through a holographic (instructional) text when reaching over to grab you real-world work tool.</span></span>

<span data-ttu-id="a56b5-215">此時，您的手不小心劃過某個您根本沒留意過的互動式全像攝影按鈕 (該按鈕甚至不在使用者的視野 (FOV) 內)。</span><span class="sxs-lookup"><span data-stu-id="a56b5-215">By doing so, you accidentally move your hand across some interactive holographic buttons that you hadn't even noticed before (maybe it even was outside of the user's Field-of-View (FOV)).</span></span>

  <span data-ttu-id="a56b5-216">長話短說：如果使用者已有一段時間未注視某個全像投影，系統也未偵測到其觸碰或抓取事件，表示使用者可能並非真正想要與該全像投影互動。</span><span class="sxs-lookup"><span data-stu-id="a56b5-216">Long story short: If the user hasn't looked at a hologram for a while, yet a touch or grasp event has been detected for it, it is likely that the user wasn't actually intending to interact with that hologram.</span></span>

* <span data-ttu-id="a56b5-217">**標的**：除了處理誤判的啟用以外，它還有助於判斷所應抓取或觸碰的全像投影，因為從您的視角可能無法看出精準的交叉點，尤其是有數個全像投影的位置彼此十分靠近時。</span><span class="sxs-lookup"><span data-stu-id="a56b5-217">**Which one**:  Aside from addressing false positive activations, another example includes better identifying which holograms to grab or poke as the precise intersection point may not be clear from your perspective especially if several holograms are positioned close to each other.</span></span>

  <span data-ttu-id="a56b5-218">雖然 HoloLens 2 的眼球追蹤在判斷眼睛視線的精準度方面有其特定限制，但對近距離互動而言仍不失為有利的工具，因為透過手部輸入互動時，會有深度的差異。</span><span class="sxs-lookup"><span data-stu-id="a56b5-218">While eye tracking on HoloLens 2 has a certain limitation on how accurately it can determine you eye gaze, this can still be very helpful for near interactions due to depth disparity when interacting with hand input.</span></span>  <span data-ttu-id="a56b5-219">這表示，要判斷您的手是在全像投影的後面還是前面，而精確地抓取操作工具 (舉例而言)，有時是很困難的。</span><span class="sxs-lookup"><span data-stu-id="a56b5-219">This means that it is sometimes difficult to determine whether your hand is behind or in front of a hologram to precisely grab a manipulation widget for example.</span></span>

* <span data-ttu-id="a56b5-220">**目的地**：運用使用者在執行快速拋投手勢時看往何處的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a56b5-220">**Where to**: Use information about what a user is looking at with quick- throwing gestures.</span></span> <span data-ttu-id="a56b5-221">抓取全像投影並約略拋向您要的目的地。</span><span class="sxs-lookup"><span data-stu-id="a56b5-221">Grab a hologram and roughly toss it toward your intended destination.</span></span>  

    <span data-ttu-id="a56b5-222">雖然這有時行得通，但快速執行手勢可能會導致目的地嚴重失準。</span><span class="sxs-lookup"><span data-stu-id="a56b5-222">While this may sometimes works just fine, quickly performing hand gestures may result in highly inaccurate destinations.</span></span> <span data-ttu-id="a56b5-223">此時眼球追蹤就可發揮效用，將手部拋投向量導正回您想要的位置。</span><span class="sxs-lookup"><span data-stu-id="a56b5-223">This is where eye tracking could help out to lean the hand throwing vector back to your intended position.</span></span>

## <a name="see-also"></a><span data-ttu-id="a56b5-224">請參閱</span><span class="sxs-lookup"><span data-stu-id="a56b5-224">See also</span></span>

* [<span data-ttu-id="a56b5-225">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="a56b5-225">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="a56b5-226">手部指向和行動</span><span class="sxs-lookup"><span data-stu-id="a56b5-226">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="a56b5-227">本能互動</span><span class="sxs-lookup"><span data-stu-id="a56b5-227">Instinctual interactions</span></span>](interaction-fundamentals.md)

