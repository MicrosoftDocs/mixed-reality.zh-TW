---
title: 直接操作
description: 直接操作輸入模型的概觀
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
keywords: 混合實境、 視線、 視線目標，就會有互動，設計、 附近，手 HoloLens
ms.openlocfilehash: 803157bb248a5541ed524ac4f828ccbba9d59ce1
ms.sourcegitcommit: 82d4e5cf4ad46bfdc44d0606844e28c75b6e67ce
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730504"
---
# <a name="direct-manipulation"></a><span data-ttu-id="1f928-104">直接操作</span><span class="sxs-lookup"><span data-stu-id="1f928-104">Direct Manipulation</span></span>

<span data-ttu-id="1f928-105">HoloLens 2 具有直接操作輸入的模型，可讓您接觸全像投影 dircly 雙手。</span><span class="sxs-lookup"><span data-stu-id="1f928-105">The HoloLens 2 has a direct manipulation input model that lets you touch holograms dircly with your hands.</span></span> <span data-ttu-id="1f928-106">直接操作的目標是的行為就如同真實世界中的物件。</span><span class="sxs-lookup"><span data-stu-id="1f928-106">The goal with direct manipulation is for objects to behave just as they do in the real world.</span></span> <span data-ttu-id="1f928-107">您可以啟動，只要按下的按鈕和甚至和挑選、 抓取，和移動物件。</span><span class="sxs-lookup"><span data-stu-id="1f928-107">You can activate buttons by simply pressing them, and even and pick up, grab, and move objects.</span></span> <span data-ttu-id="1f928-108">在這些情況下，2D 內容的行為類似虛擬觸控螢幕。</span><span class="sxs-lookup"><span data-stu-id="1f928-108">In these scenarios, 2D content behaves like a virtual touchscreen.</span></span>

<span data-ttu-id="1f928-109">直接操作很容易讓使用者了解，而且它有太有趣。</span><span class="sxs-lookup"><span data-stu-id="1f928-109">Direct manipulation is easy for users to learn, and it's fun too.</span></span> <span data-ttu-id="1f928-110">它會被視為 「 接近實際操作 」 輸入的模型，這表示它最適合用於 arm 的範圍內的內容與互動。</span><span class="sxs-lookup"><span data-stu-id="1f928-110">It is considered a "hands near" input model, meaning it's best used for interacting with content that is within an arm's reach.</span></span>

<span data-ttu-id="1f928-111">直接操作是功能可見性為基礎，這表示它的使用者易記。</span><span class="sxs-lookup"><span data-stu-id="1f928-111">Direct manipulation is affordance-based, meaning it's user friendly.</span></span> <span data-ttu-id="1f928-112">沒有符號的筆勢，以教導使用者。</span><span class="sxs-lookup"><span data-stu-id="1f928-112">There are no symbolic gestures to teach users.</span></span> <span data-ttu-id="1f928-113">所有的互動是以視覺化的項目，您可以接觸或抓取。</span><span class="sxs-lookup"><span data-stu-id="1f928-113">All interactions are built around a visual element that you can touch or grab.</span></span>

## <a name="device-support"></a><span data-ttu-id="1f928-114">裝置支援</span><span class="sxs-lookup"><span data-stu-id="1f928-114">Device support</span></span>

| <span data-ttu-id="1f928-115">輸入的模型</span><span class="sxs-lookup"><span data-stu-id="1f928-115">Input Model</span></span> | [<span data-ttu-id="1f928-116">HoloLens （第 1 代）</span><span class="sxs-lookup"><span data-stu-id="1f928-116">HoloLens (1st Gen)</span></span>](https://review.docs.microsoft.com/en-us/windows/mixed-reality/hololens-hardware-details?branch=master) | <span data-ttu-id="1f928-117">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="1f928-117">HoloLens 2</span></span> |[<span data-ttu-id="1f928-118">沈浸式耳機</span><span class="sxs-lookup"><span data-stu-id="1f928-118">Immersive Headsets</span></span>](https://review.docs.microsoft.com/en-us/windows/mixed-reality/immersive-headset-hardware-details?branch=master)|
|:-------- | :-------| :--------| :------------|
| <span data-ttu-id="1f928-119">直接操作</span><span class="sxs-lookup"><span data-stu-id="1f928-119">Direct manipulation</span></span> | <span data-ttu-id="1f928-120">不支援的 ❌</span><span class="sxs-lookup"><span data-stu-id="1f928-120">❌ Not supported</span></span> | <span data-ttu-id="1f928-121">建議的 ✔️</span><span class="sxs-lookup"><span data-stu-id="1f928-121">✔️ Recommended</span></span> | <span data-ttu-id="1f928-122">➕ 替代[點，並認可](https://review.docs.microsoft.com/en-us/windows/mixed-reality/point-and-commit?branch=master)建議。</span><span class="sxs-lookup"><span data-stu-id="1f928-122">➕ An alternative [point and commit](https://review.docs.microsoft.com/en-us/windows/mixed-reality/point-and-commit?branch=master) is recommended.</span></span>

<span data-ttu-id="1f928-123">直接操作是 HoloLens 2 上的主要輸入的模型，並利用新的相互連貫的手動追蹤系統。</span><span class="sxs-lookup"><span data-stu-id="1f928-123">Direct manipulation is a primary input model on HoloLens 2, and utilizes the new articulated hand-tracking system.</span></span> <span data-ttu-id="1f928-124">輸入的模型也會提供在透過移動控制站，使用擬真耳機，但不是建議做為主要物件操作之外的互動。</span><span class="sxs-lookup"><span data-stu-id="1f928-124">The input model is also available on immersive headsets through the use of motion controllers, but is not recommended as a primary means of interaction outside of object manipulation.</span></span>  <span data-ttu-id="1f928-125">無法使用 HoloLens 第 1 版上直接 manipluation。</span><span class="sxs-lookup"><span data-stu-id="1f928-125">Direct manipluation is not available on HoloLens v1.</span></span>

## <a name="collidable-fingertip"></a><span data-ttu-id="1f928-126">Collidable 寫寫看</span><span class="sxs-lookup"><span data-stu-id="1f928-126">Collidable fingertip</span></span>

<span data-ttu-id="1f928-127">HoloLens 2 上使用者的實際手被辨識和解譯為左邊和右邊的架構模型。</span><span class="sxs-lookup"><span data-stu-id="1f928-127">On HoloLens 2, user's real hands are recognized and interpreted as left and right hand skeletal models.</span></span> <span data-ttu-id="1f928-128">若要實作觸碰全像投影直接與實際操作的概念，在理想情況下，5 colliders 可以連接到每一個手動架構模型的 5 個手。</span><span class="sxs-lookup"><span data-stu-id="1f928-128">To implement the idea of touching holograms directly with hands, ideally, 5 colliders could be attached to 5 fingertips of each hand skeletal model.</span></span> <span data-ttu-id="1f928-129">不過，實際上，tactile 的意見反應的不足，10 collidable 握有一間功能造成非預期且無法預期的衝突與全像投影。</span><span class="sxs-lookup"><span data-stu-id="1f928-129">However, practically, due to the lack of tactile feedback, 10 collidable fingertips caused unexpected and unpredictable collisions with holograms.</span></span> 

<span data-ttu-id="1f928-130">因此，我們建議僅將 collider 放入每個索引的手指。</span><span class="sxs-lookup"><span data-stu-id="1f928-130">Hence, we suggest to only put a collider on each index finger.</span></span> <span data-ttu-id="1f928-131">下圖所示，則 collidable 索引握有一間功能仍然可做為涉及其他手指，例如 1 手指按、 1 手指點選、 2 手指按和 5 手指按各種不同的觸控筆勢的作用中觸控點。</span><span class="sxs-lookup"><span data-stu-id="1f928-131">The collidable index fingertips can still serve as active touch points for diverse touch gestures involving other fingers, such as 1-finger press, 1-finger tap, 2-finger press and 5-finger press, as shown in the image below.</span></span>

![Collidable 寫寫看映像](images/Collidable-Fingertip-720px.jpg)

### <a name="sphere-collider"></a><span data-ttu-id="1f928-133">球紋 collider</span><span class="sxs-lookup"><span data-stu-id="1f928-133">Sphere collider</span></span>

<span data-ttu-id="1f928-134">而不是使用隨機的一般形狀，我們建議使用球體 collider，並以視覺化方式呈現它為幾近目標提供更好的提示。</span><span class="sxs-lookup"><span data-stu-id="1f928-134">Instead of using a random generic shape, we suggest to use a sphere collider and to visually render it to provide better cues for near targeting.</span></span> <span data-ttu-id="1f928-135">球體的直徑應符合食指，以提高觸控的正確性的粗細。</span><span class="sxs-lookup"><span data-stu-id="1f928-135">The sphere's diameter should match the thickness of the index finger to increase touch accuracy.</span></span> <span data-ttu-id="1f928-136">它很容易就能藉由呼叫手形 API 擷取手指粗細的變數。</span><span class="sxs-lookup"><span data-stu-id="1f928-136">It will be easy to retrieve the variable of finger thickness by calling the hand API.</span></span>

### <a name="fingertip-cursor"></a><span data-ttu-id="1f928-137">用手指對資料指標</span><span class="sxs-lookup"><span data-stu-id="1f928-137">Fingertip cursor</span></span>

<span data-ttu-id="1f928-138">除了呈現 collidable 球體上索引寫寫看，我們提供了進階的解決方案，用手指對資料指標，以互動方式達成更好的附近為目標的體驗。</span><span class="sxs-lookup"><span data-stu-id="1f928-138">In addition to rendering a collidable sphere on the index fingertip, we've created an advanced solution, fingertip cursor, to achieve better near-targeting experience interactively.</span></span> <span data-ttu-id="1f928-139">它是附加在索引寫寫看圈資料指標。</span><span class="sxs-lookup"><span data-stu-id="1f928-139">It is a donut-shaped cursor attached on the index fingertip.</span></span> <span data-ttu-id="1f928-140">根據鄰近性，以動態方式回應方向和大小，如下所述的目標：</span><span class="sxs-lookup"><span data-stu-id="1f928-140">According to proximity, it dynamically reacts to a target in terms of orientation and size as detailed below:</span></span>

* <span data-ttu-id="1f928-141">當食指移到全像圖時，資料指標一律會平行至全像圖的介面，而逐漸隨之縮減其大小。</span><span class="sxs-lookup"><span data-stu-id="1f928-141">When an index finger moves toward a hologram, the cursor is always parallel to the hologram's surface  and gradually shrinks its size accordingly.</span></span>
* <span data-ttu-id="1f928-142">手指接觸到的表面，如資料指標會壓縮成一個點，並發出觸控事件。</span><span class="sxs-lookup"><span data-stu-id="1f928-142">As soon as the finger touches the surface, the cursor shrinks into a dot and emits a touch event.</span></span>

<span data-ttu-id="1f928-143">使用互動式的意見反應，使用者可達到接近目標工作，例如觸發的 web 內容的超連結或按下按鈕，如下所示，有效位數很高。</span><span class="sxs-lookup"><span data-stu-id="1f928-143">With the interactive feedback, users can achieve high precision near targeting tasks, such as triggering a hyperlink on web content or pressing a button, as shown, below.</span></span> 

![寫寫看游標影像](images/Fingertip-Cursor-720px.jpg)

## <a name="bounding-box-with-proximity-shader"></a><span data-ttu-id="1f928-145">週框方塊與鄰近著色器</span><span class="sxs-lookup"><span data-stu-id="1f928-145">Bounding box with proximity shader</span></span>

<span data-ttu-id="1f928-146">全像圖本身也必須能夠提供視覺與音訊來補償缺少 tactile 的意見反應的意見反應。</span><span class="sxs-lookup"><span data-stu-id="1f928-146">The hologram itself also requires the ability to provide both visual and audio feedback to compensate the lack of tactile feedback.</span></span> <span data-ttu-id="1f928-147">為此，我們可以產生週框方塊的概念與鄰近著色器。</span><span class="sxs-lookup"><span data-stu-id="1f928-147">For that, we generate the concept of a bounding box with proximity shader.</span></span> <span data-ttu-id="1f928-148">週框方塊是最小的體積型區域封入 3D 物件。</span><span class="sxs-lookup"><span data-stu-id="1f928-148">A bounding box is a minimum volumetric area that encloses a 3D object.</span></span> <span data-ttu-id="1f928-149">週框方塊有互動式轉譯機制稱為 「 鄰近著色器。</span><span class="sxs-lookup"><span data-stu-id="1f928-149">The bounding box has an interactive rendering mechanism called proximity shader.</span></span> <span data-ttu-id="1f928-150">鄰近著色器的行為：</span><span class="sxs-lookup"><span data-stu-id="1f928-150">The proximity shader behaves:</span></span>

* <span data-ttu-id="1f928-151">食指時在範圍內，會用手指對精選轉型之介面的週框方塊。</span><span class="sxs-lookup"><span data-stu-id="1f928-151">When the index finger is within a range, a fingertip spotlight is cast on the surface of bounding box.</span></span>
* <span data-ttu-id="1f928-152">當寫寫看表面接近，焦點就會據以總是。</span><span class="sxs-lookup"><span data-stu-id="1f928-152">When the fingertip gets closer to the surface, the spotlight condenses accordingly.</span></span>
* <span data-ttu-id="1f928-153">只要用手指對觸控式介面，整個週框方塊變更色彩，或產生以反映觸控狀態的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="1f928-153">As soon as the fingertip touch the surface, the whole bounding box changes the color or generate visual effect to reflect the touch state.</span></span>
* <span data-ttu-id="1f928-154">同時，就可以啟動的聲音效果來增強 visual 觸控意見反應。</span><span class="sxs-lookup"><span data-stu-id="1f928-154">Meanwhile, a sound effect can be activated to enhance the visual touch feedback.</span></span>

![使用鄰近著色器映像的週框方塊](images/Bounding-Box-With-Proximity-Shader-720px.jpg)

## <a name="pressable-button"></a><span data-ttu-id="1f928-156">Pressable 按鈕</span><span class="sxs-lookup"><span data-stu-id="1f928-156">Pressable button</span></span>

<span data-ttu-id="1f928-157">使用 collidable 用手指對使用者現在已準備好使用非常基本全像攝影版 UI 元件，pressable 按鈕互動。</span><span class="sxs-lookup"><span data-stu-id="1f928-157">With a collidable fingertip, users are now ready to interact with the very fundamental holographic UI component, pressable button.</span></span> <span data-ttu-id="1f928-158">Pressable 按鈕是針對直接手指按量身打造的全像攝影版按鈕。</span><span class="sxs-lookup"><span data-stu-id="1f928-158">A pressable button is a holographic button tailored for direct finger press.</span></span> <span data-ttu-id="1f928-159">同樣地，因為缺乏 tactile 的意見反應，pressable 按鈕會提供一些機制來因應 tactile 的意見反應相關問題。</span><span class="sxs-lookup"><span data-stu-id="1f928-159">Again, due to the lack of tactile feedback, a pressable button equips a couple mechanisms to tackle tactile feedback-related issues.</span></span>

* <span data-ttu-id="1f928-160">第一種機制是與鄰近著色器上, 一節中詳述的週框方塊。</span><span class="sxs-lookup"><span data-stu-id="1f928-160">The first mechanism is a bounding box with proximity shader, detailed in the previous section.</span></span> <span data-ttu-id="1f928-161">它可以提供更好的方法，並讓使用者的鄰近性概念連絡人與按鈕。</span><span class="sxs-lookup"><span data-stu-id="1f928-161">It serves to provide better sense of proximity for users to approach and make contact with a button.</span></span>
* <span data-ttu-id="1f928-162">第二個是 depression。</span><span class="sxs-lookup"><span data-stu-id="1f928-162">The second one is depression.</span></span> <span data-ttu-id="1f928-163">寫寫看連絡 按鈕之後，它會建立按下的意義。</span><span class="sxs-lookup"><span data-stu-id="1f928-163">It creates sense of press, after a fingertip contacts the button.</span></span> <span data-ttu-id="1f928-164">機制是按鈕緊密移動與深度軸寫寫看。</span><span class="sxs-lookup"><span data-stu-id="1f928-164">The mechanism is that the button tightly moves with the fingertip along the depth axis.</span></span> <span data-ttu-id="1f928-165">達到指定的深度 （在按下） 或離開的深度 （在發行） 之後傳遞給它時，可能會觸發按鈕。</span><span class="sxs-lookup"><span data-stu-id="1f928-165">The button can be triggered when it reaches a designated depth (on press) or leaves the depth (on release) after passing through it.</span></span>
* <span data-ttu-id="1f928-166">音效，應該將增強的意見反應，觸發按鈕時。</span><span class="sxs-lookup"><span data-stu-id="1f928-166">The sound effect should be added to enhance feedback, when the button is triggered.</span></span>

![Pressable 按鈕影像](images/Pressable-Button-720px.jpg)

## <a name="2d-slate-interaction"></a><span data-ttu-id="1f928-168">2D 平板電腦的互動</span><span class="sxs-lookup"><span data-stu-id="1f928-168">2D slate interaction</span></span>

<span data-ttu-id="1f928-169">2D slate 是全像攝影版的容器，裝載 2D 應用程式的內容，例如網頁瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="1f928-169">A 2D slate is a holographic container hosting 2D app contents, such as web browser.</span></span> <span data-ttu-id="1f928-170">透過直接操作 2D 靜態圖像與互動的設計概念是運用使用實體的觸控式螢幕進行互動的心智模型。</span><span class="sxs-lookup"><span data-stu-id="1f928-170">The design concept for interacting with a 2D slate via direct manipulation is to leverage the mental model of interacting with a physical touch screen.</span></span>

<span data-ttu-id="1f928-171">若要互動的平板電腦的連絡人：</span><span class="sxs-lookup"><span data-stu-id="1f928-171">To interact with the slate contact:</span></span>

* <span data-ttu-id="1f928-172">您可以使用食指，按下超連結或按鈕。</span><span class="sxs-lookup"><span data-stu-id="1f928-172">Use an index finger to press a hyperlink or a button.</span></span>
* <span data-ttu-id="1f928-173">向上和向下捲動平板電腦的內容使用索引的手指。</span><span class="sxs-lookup"><span data-stu-id="1f928-173">Use an index finger to scroll a slate content up and down.</span></span>
* <span data-ttu-id="1f928-174">使用者會使用兩個索引的手指來放大 in 和 out 根據相對的移動，指的平板電腦的內容。</span><span class="sxs-lookup"><span data-stu-id="1f928-174">Users use two index fingers to zoom in and out the slate content according to relative motion of fingers.</span></span>

![2D slate 映像](images/2D-Slate-Interaction-720px.jpg)

<span data-ttu-id="1f928-176">操作 2D slate 本身：</span><span class="sxs-lookup"><span data-stu-id="1f928-176">For manipulating the 2D slate itself:</span></span>

* <span data-ttu-id="1f928-177">接近邊角和邊緣，以顯示最接近的操作提供您手裡。</span><span class="sxs-lookup"><span data-stu-id="1f928-177">Approach your hands toward corners and edges to reveal the closest manipulation affordances.</span></span>
* <span data-ttu-id="1f928-178">抓取操作提供執行透過角提供統一縮放比例和自動重排透過邊緣提供。</span><span class="sxs-lookup"><span data-stu-id="1f928-178">Grab the manipulation affordances, and perform uniform scaling through the corner affordances and reflow via the edge affordances.</span></span>
* <span data-ttu-id="1f928-179">抓取頂端的 2D slate，可讓您移動整個 slate holobar。</span><span class="sxs-lookup"><span data-stu-id="1f928-179">Grab the holobar at the top of the 2D slate, which lets you move the whole slate.</span></span>

![平板電腦操作的映像](images/Manipulate-2d-slate-720px.jpg)

## <a name="3d-object-manipulation"></a><span data-ttu-id="1f928-181">3D 物件操作</span><span class="sxs-lookup"><span data-stu-id="1f928-181">3D object manipulation</span></span>

<span data-ttu-id="1f928-182">HoloLens 2 可讓可讓的使用者啟用導向其指針來操作 3D hologramphic 物件套用至每個 3D 物件的週框方塊。</span><span class="sxs-lookup"><span data-stu-id="1f928-182">HoloLens 2 lets lets users enable their hands to direct manipulate 3D hologramphic objects by applying a bounding box to each 3D object.</span></span> <span data-ttu-id="1f928-183">週框方塊會提供更好的深度認知，透過其鄰近著色器。</span><span class="sxs-lookup"><span data-stu-id="1f928-183">The bounding box provides better depth perception through its proximity shader.</span></span> <span data-ttu-id="1f928-184">週框方塊中，有兩個 3D 物件操作的設計方法。</span><span class="sxs-lookup"><span data-stu-id="1f928-184">With the bounding box, there are two design approaches for 3D object manipulation.</span></span>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="1f928-185">功能可見性為基礎的操作</span><span class="sxs-lookup"><span data-stu-id="1f928-185">Affordance-based manipulation</span></span>

<span data-ttu-id="1f928-186">這可讓您管理透過週框方塊和操作提供，其周圍的 3D 物件。</span><span class="sxs-lookup"><span data-stu-id="1f928-186">This lets you manipulate the 3D object through a bounding box and the manipulation affordances around it.</span></span> <span data-ttu-id="1f928-187">只要使用者的手很接近 3D 物件，會顯示週框方塊 」 和 「 最接近的功能可見性。</span><span class="sxs-lookup"><span data-stu-id="1f928-187">As soon as a user's hand is close to a 3D object, the bounding box and the nearest affordance are revealed.</span></span> <span data-ttu-id="1f928-188">使用者可以抓取移動整個物件、 旋轉邊緣提供和角提供一致的方式調整的週框方塊。</span><span class="sxs-lookup"><span data-stu-id="1f928-188">Users can grab the bounding box to move the whole object, the edge affordances to rotate and the corner affordances to scale uniformly.</span></span>

![3D 物件操作的映像](images/3D-Object-Manipulation-720px.jpg)

### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="1f928-190">非功能可見性根據的操作</span><span class="sxs-lookup"><span data-stu-id="1f928-190">Non-affordance based manipulation</span></span>

<span data-ttu-id="1f928-191">在此機制中，沒有功能可見性會附加至週框方塊。</span><span class="sxs-lookup"><span data-stu-id="1f928-191">In this mechanism, no affordance is attached to the bounding box.</span></span> <span data-ttu-id="1f928-192">使用者可以只顯示週框方塊，然後直接與它互動。</span><span class="sxs-lookup"><span data-stu-id="1f928-192">Users can only reveal the bounding box, then directly interact with it.</span></span> <span data-ttu-id="1f928-193">週框方塊以一隻手拿起，轉譯和旋轉的物件關聯到影片以及左手邊的方向。</span><span class="sxs-lookup"><span data-stu-id="1f928-193">If the bounding box is grabbed with one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="1f928-194">時物件會抓取具有兩個實際操作中，使用者可以轉譯、 縮放和旋轉根據相對的兩個實際操作的動作。</span><span class="sxs-lookup"><span data-stu-id="1f928-194">When the object is grabbed with two hands, users can translate, scale and rotate it according to relative motions of two hands.</span></span>

<span data-ttu-id="1f928-195">特定的操作需要有效位數，我們建議您使用**功能可見性為基礎的操作**，因為它提供高層級的資料粒度。</span><span class="sxs-lookup"><span data-stu-id="1f928-195">Specific manipulation requires precision, we recommend you use **affordance-based manipulation**, because it provides a high level of granularity.</span></span> <span data-ttu-id="1f928-196">彈性的操作，我們建議您會使用**非功能可見性操作**是因為它可讓您立即和 playful 體驗。</span><span class="sxs-lookup"><span data-stu-id="1f928-196">For flexible manipulation, we recommend you uses **non-affordance manipulation** is as it allows for instant and playful experiences.</span></span>

## <a name="instinctual-gestures"></a><span data-ttu-id="1f928-197">Instinctual 筆勢</span><span class="sxs-lookup"><span data-stu-id="1f928-197">Instinctual gestures</span></span>

<span data-ttu-id="1f928-198">不同於 HoloLens （第 1 代），我們教導使用者幾個預先定義的筆勢，例如 Bloom 和空中點選。</span><span class="sxs-lookup"><span data-stu-id="1f928-198">Unlike HoloLens (1st gen), we taught users a couple predefined gestures,such as Bloom and Air Tap.</span></span> <span data-ttu-id="1f928-199">HoloLens 2 中，我們不要求使用者記住任何符號的筆勢。</span><span class="sxs-lookup"><span data-stu-id="1f928-199">For HoloLens 2, we don't ask users to memorize any symbolic gestures.</span></span> <span data-ttu-id="1f928-200">所有必要的使用者筆勢，全像投影和內容互動的使用者必須是 instinctual。</span><span class="sxs-lookup"><span data-stu-id="1f928-200">All required user gestures, users need to interact with holograms and contents, are instinctual.</span></span> <span data-ttu-id="1f928-201">完成 instinctual 筆勢的方式是引導使用者來執行透過 UI 提供的設計的筆勢。</span><span class="sxs-lookup"><span data-stu-id="1f928-201">The way to achieve instinctual gesture is to guide users to perform gestures through the design of UI affordances.</span></span>

<span data-ttu-id="1f928-202">比方說，如果我們鼓勵您抓取的物件或使用兩個手指縮小的控點，該物件或控制項控點應該很小。</span><span class="sxs-lookup"><span data-stu-id="1f928-202">For example, if we encourage you to grab an object or a control point with two finger pinch, the object or the control point should be small.</span></span> <span data-ttu-id="1f928-203">如果我們想要執行五個手指抓取，表示物件或控制項控點應該相當大。</span><span class="sxs-lookup"><span data-stu-id="1f928-203">If we want you to perform five finger grab, the object or the control point should be relatively big.</span></span> <span data-ttu-id="1f928-204">類似於按鈕，小按鈕會限制使用者一根手指，以按龐大的按鈕會鼓勵使用者使用其手掌按它時。</span><span class="sxs-lookup"><span data-stu-id="1f928-204">Similar to buttons, a tiny button would limit users to press it with a single finger, while a huge button would encourage users to press it with their palms.</span></span>

![](images/Instinctual-Gestures-720px.jpg)

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a><span data-ttu-id="1f928-205">指針與 6 DoF 控制器之間的對稱式設計</span><span class="sxs-lookup"><span data-stu-id="1f928-205">Symmetric design between hands and 6 DoF controllers</span></span>

<span data-ttu-id="1f928-206">您可能已經注意到，現在有我們可繪製手中 VR AR 和移動控制站之間的互動 parallels。</span><span class="sxs-lookup"><span data-stu-id="1f928-206">You may have noticed that there are now interaction parallels we can draw between hands in AR and motion controllers in VR.</span></span> <span data-ttu-id="1f928-207">這兩個輸入可用來直接操作各自的環境中觸發程序。</span><span class="sxs-lookup"><span data-stu-id="1f928-207">Both inputs can be used to trigger direct manipulations in their respective environments.</span></span> <span data-ttu-id="1f928-208">HoloLens 2 抓取，然後拖曳手在關閉距離適用於使用許多相同的方式，為擷取按鈕會在影片中的控制站 WMR。</span><span class="sxs-lookup"><span data-stu-id="1f928-208">In HoloLens 2, grabbing and dragging with hands at a close distance works much in the same way as the grab button does on the motion controllers in WMR.</span></span> <span data-ttu-id="1f928-209">這會提供兩個平台之間的互動熟悉的使用者，並會派上用場應該您決定要從兩個不同的應用程式移植。</span><span class="sxs-lookup"><span data-stu-id="1f928-209">This provides users with interaction familiarity between the two platforms and may prove useful should you ever decide to port your app from one to the other.</span></span>

## <a name="optimize-with-eye-tracking"></a><span data-ttu-id="1f928-210">追蹤與最佳化</span><span class="sxs-lookup"><span data-stu-id="1f928-210">Optimize with eye tracking</span></span>

<span data-ttu-id="1f928-211">如果它運作正常，但可能也很快就會令人沮喪，如果您不能再移動手任何位置，而不會不小心觸發雷射，直接操作可以感覺神奇。</span><span class="sxs-lookup"><span data-stu-id="1f928-211">Direct manipulation can feel magical if it works as intended, but can also quickly become frustrating if you can’t move your hand anywhere anymore without unintentionally triggering a hologram.</span></span>
<span data-ttu-id="1f928-212">追蹤可能有助於更好用來識別使用者的目的什麼。</span><span class="sxs-lookup"><span data-stu-id="1f928-212">Eye tracking can potentially help in better identifying what the user’s intent is.</span></span>

* <span data-ttu-id="1f928-213">**當**:減少錯誤地觸發操作回應。</span><span class="sxs-lookup"><span data-stu-id="1f928-213">**When**: Reduce falsely triggering a manipulation response.</span></span> <span data-ttu-id="1f928-214">追蹤可讓您進一步了解哪些使用者目前可供使用。</span><span class="sxs-lookup"><span data-stu-id="1f928-214">Eye tracking allows for better understanding what a user is currently engaged with.</span></span>
<span data-ttu-id="1f928-215">例如，假設您正在閱讀透過全像攝影版 （指示） 的文字時達到超過擷取您的實際工作的工具。</span><span class="sxs-lookup"><span data-stu-id="1f928-215">For example, imagine you are reading through a holographic (instructional) text when reaching over to grab you real-world work tool.</span></span>

  <span data-ttu-id="1f928-216">如此一來，您不小心移動您的手跨您甚至還沒有發現之前 （甚至是外部使用者的欄位的-視角 (FOV) 或許） 一些互動式全像攝影版按鈕。</span><span class="sxs-lookup"><span data-stu-id="1f928-216">By doing so, you accidentally move your hand across some interactive holographic buttons that you hadn't even noticed before (maybe it even was outside of the user's Field-of-View (FOV)).</span></span>

  <span data-ttu-id="1f928-217">長話短說：如果使用者尚未看過全像一段時間，但它偵測觸控或掌握事件，它可能是使用者不實際想要進行互動，全像。</span><span class="sxs-lookup"><span data-stu-id="1f928-217">Long story short: If the user hasn't looked at a hologram for a while, yet a touch or grasp event has been detected for it, it is likely that the user wasn't actually intending to interact with that hologram.</span></span>

* <span data-ttu-id="1f928-218">**哪一個**:除了定址，則為 false 的正面啟用，另一個範例中會包含進一步識別哪一個擷取或逛為精確的交集點可能無法清除從您的觀點來看特別是當數個全像投影位於接近每個全像投影其他。</span><span class="sxs-lookup"><span data-stu-id="1f928-218">**Which one**:  Aside from addressing false positive activations, another example includes better identifying which holograms to grab or poke as the precise intersection point may not be clear from your perspective especially if several holograms are positioned close to each other.</span></span>

  <span data-ttu-id="1f928-219">雖然 HoloLens 2 上的眼睛追蹤有特定限制如何準確地它可以判斷眼睛視線，這仍然是非常有幫助附近因為深度差異的互動與輸入的手動互動時。</span><span class="sxs-lookup"><span data-stu-id="1f928-219">While eye tracking on HoloLens 2 has a certain limitation on how accurately it can determine you eye gaze, this can still be very helpful for near interactions due to depth disparity when interacting with hand input.</span></span>  <span data-ttu-id="1f928-220">這表示，它有時很難判斷您的手後面或前面雷射精確地抓取，例如操作小工具。</span><span class="sxs-lookup"><span data-stu-id="1f928-220">This means that it is sometimes difficult to determine whether your hand is behind or in front of a hologram to precisely grab a manipulation widget for example.</span></span>

* <span data-ttu-id="1f928-221">**如何**:使用資訊的使用者查看快速-擲回筆勢。</span><span class="sxs-lookup"><span data-stu-id="1f928-221">**Where to**: Use information about what a user is looking at with quick- throwing gestures.</span></span> <span data-ttu-id="1f928-222">抓取雷射，並大致上其投到桌子朝向您的目的端。</span><span class="sxs-lookup"><span data-stu-id="1f928-222">Grab a hologram and roughly toss it toward your intended destination.</span></span>  

    <span data-ttu-id="1f928-223">雖然這有時可能會運作正常，快速地執行手勢可能會導致高度不正確的目的地。</span><span class="sxs-lookup"><span data-stu-id="1f928-223">While this may sometimes works just fine, quickly performing hand gestures may result in highly inaccurate destinations.</span></span> <span data-ttu-id="1f928-224">這是追蹤可以幫助要借助交回擲回向量，以您想要的位置。</span><span class="sxs-lookup"><span data-stu-id="1f928-224">This is where eye tracking could help out to lean the hand throwing vector back to your intended position.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f928-225">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f928-225">See also</span></span>

* [<span data-ttu-id="1f928-226">視線與認可</span><span class="sxs-lookup"><span data-stu-id="1f928-226">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="1f928-227">指向和行動</span><span class="sxs-lookup"><span data-stu-id="1f928-227">Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="1f928-228">互動基本概念</span><span class="sxs-lookup"><span data-stu-id="1f928-228">Interaction fundamentals</span></span>](interaction-fundamentals.md)
