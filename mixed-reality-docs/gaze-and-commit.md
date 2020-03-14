---
title: 注視和認可
description: 「注視和認可」輸入模型的一般總覽-使用眼睛或 head 輸入。
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Mixed Reality，注視，注視目標，互動，設計，眼睛追蹤，head 追蹤
ms.openlocfilehash: df152f6a3a6e4ae2d6c32a0c56fbb615bcfa7aa8
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375845"
---
# <a name="gaze-and-commit"></a><span data-ttu-id="3fbc7-104">注視和認可</span><span class="sxs-lookup"><span data-stu-id="3fbc7-104">Gaze and commit</span></span>

<span data-ttu-id="3fbc7-105">_注視和認可_是一種基本的輸入模型，與我們使用滑鼠進行互動的方式密切相關： _Point & 按一下_。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-105">_Gaze and commit_ is a fundamental input model that is closely related with the way we're interacting with our computers using the mouse: _Point & click_.</span></span>
<span data-ttu-id="3fbc7-106">在此頁面上，我們引進兩種類型的注視輸入（head 和眼睛）和不同類型的認可動作。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-106">On this page, we introduce two types of gaze input (head- and eye-gaze) and different types of commit actions.</span></span> 
<span data-ttu-id="3fbc7-107">_注視和認可_會被視為具有間接操作的輸入模型。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-107">_Gaze and commit_ is considered a far input model with indirect manipulation.</span></span>
<span data-ttu-id="3fbc7-108">這表示它最適合用來與不在手中的全像攝影內容互動。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-108">This means it is best used for interacting with holographic content that is out of reach.</span></span>

<span data-ttu-id="3fbc7-109">混合現實耳機可以使用使用者頭部的位置和方向來判斷其前端方向向量。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-109">Mixed reality headsets can use the position and orientation of the user's head to determine their head direction vector.</span></span> <span data-ttu-id="3fbc7-110">您可以將此視為直接從使用者的雙眼之間向前直指的雷射。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-110">You can think of this as a laser that points straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="3fbc7-111">這是相當粗略的使用者觀看位置概算。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-111">This is a fairly coarse approximation of where the user is looking.</span></span> <span data-ttu-id="3fbc7-112">您的應用程式可以將此光線與虛擬或真實世界的物件相交，並在該位置繪製游標，讓使用者知道它們目前的目標為何。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-112">Your application can intersect this ray with virtual or real-world objects, and draw a cursor at that location to let the user know what they are currently targeting.</span></span>

<span data-ttu-id="3fbc7-113">除了眼睛外，某些混合現實耳機（如 HoloLens 2）包含了產生眼睛向量的監看式追蹤系統。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-113">In addition to head gaze, some mixed reality headsets, such as HoloLens 2, include eye tracking systems that produce an eye-gaze vector.</span></span> <span data-ttu-id="3fbc7-114">這會對使用者觀看的位置提供精細的測量。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-114">This provides a fine-grained measurement of where the user is looking.</span></span> <span data-ttu-id="3fbc7-115">在這兩種情況下，注視代表使用者意圖的重要信號。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-115">In both cases, the gaze represents an important signal for the user's intent.</span></span> <span data-ttu-id="3fbc7-116">系統能夠解讀和預測使用者的期望動作，使用者滿意度增加並提升效能。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-116">The better the system can interpret and predict the user's intended actions, user satisfaction increases and performance improves.</span></span>

<span data-ttu-id="3fbc7-117">以下幾個範例會說明如何讓混合現實開發人員受益于 head 或眼睛：</span><span class="sxs-lookup"><span data-stu-id="3fbc7-117">Below are a few examples for how you as a mixed reality developer can benefit from head- or eye-gaze:</span></span>
* <span data-ttu-id="3fbc7-118">您的應用程式可以與場景中的全息影像相交，以判斷使用者注意的位置（更精確的眼睛）。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-118">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is (more precise with eye-gaze).</span></span>
* <span data-ttu-id="3fbc7-119">您的應用程式可以根據使用者的注視來進行通道手勢和控制器按下動作，讓使用者順暢地選取、啟動、抓取、滾動，或以其他方式與其全息影像互動。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-119">Your app can channel gestures and controller presses based on the user's gaze, letting the user seamlessly select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="3fbc7-120">您的應用程式可讓使用者在真實世界的表面上放置全息影像，方法是將其注視光線與空間對應網格相交。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-120">Your app can let the user place holograms on real-world surfaces by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="3fbc7-121">您的應用程式可以知道使用者何時看*不*到重要物件的方向，這可能會導致您的應用程式提供視覺和音訊提示來轉向該物件。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-121">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

<br>


## <a name="device-support"></a><span data-ttu-id="3fbc7-122">裝置支援</span><span class="sxs-lookup"><span data-stu-id="3fbc7-122">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="3fbc7-123"><strong>輸入模型</strong></span><span class="sxs-lookup"><span data-stu-id="3fbc7-123"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="3fbc7-124"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="3fbc7-124"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="3fbc7-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="3fbc7-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="3fbc7-126"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="3fbc7-126"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="3fbc7-127">頭部注視並認可</span><span class="sxs-lookup"><span data-stu-id="3fbc7-127">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="3fbc7-128">✔️ 建議使用</span><span class="sxs-lookup"><span data-stu-id="3fbc7-128">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="3fbc7-129">✔️ 建議使用 (第三個選擇 - <a href="interaction-fundamentals.md">查看其他選項</a>)</span><span class="sxs-lookup"><span data-stu-id="3fbc7-129">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="3fbc7-130">➕ 替代選項</span><span class="sxs-lookup"><span data-stu-id="3fbc7-130">➕ Alternate option</span></span></td>
    </tr>
         <tr>
        <td><span data-ttu-id="3fbc7-131">眼部注視並認可</span><span class="sxs-lookup"><span data-stu-id="3fbc7-131">Eye-gaze and commit</span></span></td>
        <td><span data-ttu-id="3fbc7-132">❌ 無法使用</span><span class="sxs-lookup"><span data-stu-id="3fbc7-132">❌ Not available</span></span></td>
        <td><span data-ttu-id="3fbc7-133">✔️ 建議使用 (第三個選擇 - <a href="interaction-fundamentals.md">查看其他選項</a>)</span><span class="sxs-lookup"><span data-stu-id="3fbc7-133">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="3fbc7-134">❌ 無法使用</span><span class="sxs-lookup"><span data-stu-id="3fbc7-134">❌ Not available</span></span></td>
    </tr>
</table>


## <a name="gaze"></a><span data-ttu-id="3fbc7-135">注視</span><span class="sxs-lookup"><span data-stu-id="3fbc7-135">Gaze</span></span>

### <a name="eye--or-head-gaze"></a><span data-ttu-id="3fbc7-136">眼睛或列印頭？</span><span class="sxs-lookup"><span data-stu-id="3fbc7-136">Eye- or head-gaze?</span></span>
<span data-ttu-id="3fbc7-137">當您遇到問題時，應該考慮幾個考慮，不論您是否應該使用「眼睛與認可」或「列印頭和認可」輸入模型。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-137">There are several considerations to take into account when faced with the question whether you should use the "eye-gaze and commit" or "head-gaze and commit" input model.</span></span> <span data-ttu-id="3fbc7-138">如果您是針對沉浸式耳機或 HoloLens （第1代）進行開發，則選擇很簡單： Head 注視和認可。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-138">If you're developing for an immersive headset or for HoloLens (1st gen) then the choice is simple: Head-gaze and commit.</span></span> <span data-ttu-id="3fbc7-139">如果您是針對 HoloLens 2 進行開發，則選擇會變得有點困難，這就是了解每一項的優點和挑戰的重要性。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-139">If you're developing for HoloLens 2, the choice becomes a little harder which is why it's important to understand the advantages and challenges that come with each of them.</span></span>
<span data-ttu-id="3fbc7-140">我們在下表中編譯了一些廣泛的 pro 和 con，以對比「前端與眼睛」目標。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-140">We compiled some broad pro's and con's in the table below to contrast head- vs. eye-gaze targeting.</span></span> <span data-ttu-id="3fbc7-141">這不是完整的，因此我們建議您在這裡瞭解混合現實中的眼睛目標：</span><span class="sxs-lookup"><span data-stu-id="3fbc7-141">This is far from complete and we suggest learning more about eye-gaze targeting in mixed reality here:</span></span>
* <span data-ttu-id="3fbc7-142">[Hololens 上的眼睛追蹤 2](eye-tracking.md)：在 hololens 2 上引進新眼追蹤功能的一般簡介，包括一些開發人員指引。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-142">[Eye tracking on HoloLens 2](eye-tracking.md): General introduction of our new eye tracking capability on HoloLens 2 including some developer guidance.</span></span> 
* <span data-ttu-id="3fbc7-143">[眼睛互動](eye-gaze-interaction.md)：規劃使用眼睛追蹤做為輸入時的設計考慮和建議。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-143">[Eye-gaze interaction](eye-gaze-interaction.md): Design considerations and recommendations when planning to use eye tracking as an input.</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><span data-ttu-id="3fbc7-144"><strong>眼睛目標</strong></span><span class="sxs-lookup"><span data-stu-id="3fbc7-144"><strong>Eye-gaze targeting</strong></span></span></td>
        <td><span data-ttu-id="3fbc7-145"><strong>頭部注視目標</strong></span><span class="sxs-lookup"><span data-stu-id="3fbc7-145"><strong>Head-gaze targeting</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="3fbc7-146">地!</span><span class="sxs-lookup"><span data-stu-id="3fbc7-146">Fast!</span></span></td>
        <td><span data-ttu-id="3fbc7-147">一點</span><span class="sxs-lookup"><span data-stu-id="3fbc7-147">Slower</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="3fbc7-148">低度（幾乎所有的主體移動都是必要的）</span><span class="sxs-lookup"><span data-stu-id="3fbc7-148">Low effort (barely any body movements necessary)</span></span></td>
        <td><span data-ttu-id="3fbc7-149">可能是 fatiguing 的 discomfort （例如，頸部壓力）</span><span class="sxs-lookup"><span data-stu-id="3fbc7-149">Can be fatiguing - Possible discomfort (e.g., neck strain)</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="3fbc7-150">不需要資料指標，但建議使用細微的意見反應</span><span class="sxs-lookup"><span data-stu-id="3fbc7-150">Does not require a cursor, but subtle feedback is recommended</span></span></td>
        <td><span data-ttu-id="3fbc7-151">需要顯示資料指標</span><span class="sxs-lookup"><span data-stu-id="3fbc7-151">Requires to show a cursor</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="3fbc7-152">不會順暢地移動–例如，不適合繪製</span><span class="sxs-lookup"><span data-stu-id="3fbc7-152">No smooth eye movements – e.g., not good for drawing</span></span></td>
        <td><span data-ttu-id="3fbc7-153">更具控制和明確</span><span class="sxs-lookup"><span data-stu-id="3fbc7-153">More controlled and explicit</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="3fbc7-154">非常小的目標很困難（例如，小按鈕或 weblinks）</span><span class="sxs-lookup"><span data-stu-id="3fbc7-154">Difficult for very small targets (e.g., tiny buttons or weblinks)</span></span></td>
        <td><span data-ttu-id="3fbc7-155">可靠!</span><span class="sxs-lookup"><span data-stu-id="3fbc7-155">Reliable!</span></span> <span data-ttu-id="3fbc7-156">絕佳的回復！</span><span class="sxs-lookup"><span data-stu-id="3fbc7-156">Great fallback!</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="3fbc7-157">...</span><span class="sxs-lookup"><span data-stu-id="3fbc7-157">...</span></span></td>
        <td><span data-ttu-id="3fbc7-158">...</span><span class="sxs-lookup"><span data-stu-id="3fbc7-158">...</span></span></td>
    </tr>
</table>

<span data-ttu-id="3fbc7-159">不論您使用的是注視或監看式輸入模型，都隨附不同的設計條件約束集合，這些限制將會分別涵蓋在[眼睛和認可](gaze-and-commit-eyes.md)和[認可](gaze-and-commit-head.md)文章中。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-159">Whether you use head-gaze or eye-gaze for your gaze-and-commit input model comes with different sets of design constraints, which will be covered separately in the [eye-gaze and commit](gaze-and-commit-eyes.md) and [head-gaze and commit](gaze-and-commit-head.md) articles.</span></span>

<br>

---

### <a name="cursor"></a><span data-ttu-id="3fbc7-160">游標</span><span class="sxs-lookup"><span data-stu-id="3fbc7-160">Cursor</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="3fbc7-161">對於列印頭，大部分的應用程式都應該使用[游標](cursors.md)（或其他聽覺/視覺指示），讓使用者能夠信賴他們要與之互動的物件。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-161">For head gaze, most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="3fbc7-162">您通常會將此游標置於世界中，其前端光線會先與物件相交，這可能是全息影像或真實世界表面。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-162">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span><br>
        <br>
        <span data-ttu-id="3fbc7-163">就眼睛而言，我們通常建議*不要*顯示游標，因為這可能會很快就會變得令人困擾，而且不會讓使用者雜亂。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-163">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="3fbc7-164">相反地，反白顯示視覺效果目標，或使用非常不好的眼游標，讓您安心瞭解使用者的互動方式。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-164">Instead subtly highlight visual targets or use a very faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="3fbc7-165">如需詳細資訊，請查看我們在 HoloLens 2 上[以眼睛為基礎之輸入的設計指引](eye-tracking.md)。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-165">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="3fbc7-166">![視覺效果游標的範例，以顯示注視](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="3fbc7-166">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
       <span data-ttu-id="3fbc7-167">*影像：顯示注視的視覺化游標範例*</span><span class="sxs-lookup"><span data-stu-id="3fbc7-167">*Image: An example visual cursor to show gaze*</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a><span data-ttu-id="3fbc7-168">認可</span><span class="sxs-lookup"><span data-stu-id="3fbc7-168">Commit</span></span>
<span data-ttu-id="3fbc7-169">_在談到某個_目標的不同方式之後，讓我們更進一步討論_注視和認可_的_認可_部分。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-169">After talking about different ways to _gaze_ at a target, let's talk a bit more about the _commit_ part in _gaze and commit_.</span></span>
<span data-ttu-id="3fbc7-170">以物件或 UI 元素為目標之後，使用者可以使用次要輸入進行互動或按一下。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-170">After targeting an object or UI element, the user can interact or click on it using a secondary input.</span></span> <span data-ttu-id="3fbc7-171">這就是所謂的輸入模型認可步驟。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-171">This is known as the commit step of the input model.</span></span> 

<span data-ttu-id="3fbc7-172">支援的認可方法如下：</span><span class="sxs-lookup"><span data-stu-id="3fbc7-172">The following commit methods are supported:</span></span>
- <span data-ttu-id="3fbc7-173">點按手勢（也就是在您的前方舉手，並結合您的食指和拇指）</span><span class="sxs-lookup"><span data-stu-id="3fbc7-173">Air tap hand gesture (i.e., raise your hand in front of you and bring together your index finger and thumb)</span></span>
- <span data-ttu-id="3fbc7-174">說「 _select_ 」或其中一個目標語音命令</span><span class="sxs-lookup"><span data-stu-id="3fbc7-174">Say _"select"_ or one of the targeted voice commands</span></span>
- <span data-ttu-id="3fbc7-175">在[HoloLens Clicker](hardware-accessories.md#hololens-clicker)上按一個按鈕</span><span class="sxs-lookup"><span data-stu-id="3fbc7-175">Press a single button on a [HoloLens Clicker](hardware-accessories.md#hololens-clicker)</span></span>
- <span data-ttu-id="3fbc7-176">按下 Xbox 遊戲台上的 [A] 按鈕</span><span class="sxs-lookup"><span data-stu-id="3fbc7-176">Press the 'A' button on an Xbox gamepad</span></span>
- <span data-ttu-id="3fbc7-177">按 Xbox 調適型控制器上的 [A] 按鈕</span><span class="sxs-lookup"><span data-stu-id="3fbc7-177">Press the 'A' button on an Xbox adaptive controller</span></span>

### <a name="gaze-and-air-tap-gesture"></a><span data-ttu-id="3fbc7-178">注視和碰點手勢</span><span class="sxs-lookup"><span data-stu-id="3fbc7-178">Gaze and air tap gesture</span></span>
<span data-ttu-id="3fbc7-179">空中點選是手部直立的點選手勢。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-179">Air tap is a tapping gesture with the hand held upright.</span></span> <span data-ttu-id="3fbc7-180">若要執行點一下，請將您的索引指向準備好的位置，然後將您的 thumb 縮小，然後將索引手指的備份提升至發行。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-180">To perform an air tap, raise your index finger to the ready position, then pinch with your thumb, and raise your index finger back up to release.</span></span> <span data-ttu-id="3fbc7-181">在 HoloLens （第1代）上，空中碰是最常見的次要輸入。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-181">On HoloLens (1st gen), air tap is the most common secondary input.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="3fbc7-182">在 [就緒] 位置中 ![手指](images/readyandpress-ready.jpg)</span><span class="sxs-lookup"><span data-stu-id="3fbc7-182">![Finger in the ready position](images/readyandpress-ready.jpg)</span></span><br>
       <span data-ttu-id="3fbc7-183">**觸達就緒位置**</span><span class="sxs-lookup"><span data-stu-id="3fbc7-183">**Finger in the ready position**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="3fbc7-184">![按向下鍵以點擊或按一下](images/readyandpress-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="3fbc7-184">![Press finger down to tap or click](images/readyandpress-press.jpg)</span></span><br>
        <span data-ttu-id="3fbc7-185">**按下手指以點按或按一下**</span><span class="sxs-lookup"><span data-stu-id="3fbc7-185">**Press finger down to tap or click**</span></span><br>
    :::column-end:::
:::row-end:::


<span data-ttu-id="3fbc7-186">您也可以在 HoloLens 2 上使用空中按鍵功能。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-186">Air tap is also available on HoloLens 2.</span></span> <span data-ttu-id="3fbc7-187">它已從原始版本中放寬。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-187">It has been relaxed from the original version.</span></span> <span data-ttu-id="3fbc7-188">幾乎所有類型的 pinches 現在都可支援，只要手是直立的，而且仍然保留。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-188">Nearly all types of pinches are now supported as long as the hand is upright and holding still.</span></span> <span data-ttu-id="3fbc7-189">這可讓使用者更容易了解和執行手勢。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-189">This makes it much easier for users to learn and perform the gesture.</span></span> <span data-ttu-id="3fbc7-190">這個新的空中點會透過相同的 API 取代舊的，因此現有的應用程式會在重新編譯 HoloLens 2 之後自動擁有新的行為。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-190">This new air tap replaces the old one through the same API, so existing applications will have the new behavior automatically after recompiling for HoloLens 2.</span></span>

<br>

---

### <a name="gaze-and-select-voice-command"></a><span data-ttu-id="3fbc7-191">注視和「選取」語音命令</span><span class="sxs-lookup"><span data-stu-id="3fbc7-191">Gaze and "Select" voice command</span></span>
<span data-ttu-id="3fbc7-192">語音命令是混合現實中的其中一種主要互動方法。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-192">Voice commanding is one of the primary interaction methods in mixed reality.</span></span> <span data-ttu-id="3fbc7-193">它提供了一種非常強大的無人參與機制來控制系統。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-193">It provides a very powerful hands-free mechanism to control the system.</span></span> <span data-ttu-id="3fbc7-194">語音互動模型有不同的類型：</span><span class="sxs-lookup"><span data-stu-id="3fbc7-194">There are different types of voice interaction models:</span></span>

- <span data-ttu-id="3fbc7-195">執行 click actuation 或 commit 做為次要輸入的泛型 "Select" 命令。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-195">The generic "Select" command that performs a click actuation or commit as a secondary input.</span></span>
- <span data-ttu-id="3fbc7-196">物件命令（例如「關閉」或「使它變大」）會執行並認可動作做為次要輸入。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-196">Object commands (e.g., "Close" or "Make it bigger") perform and commit to an action as a secondary input.</span></span>
- <span data-ttu-id="3fbc7-197">全域命令（例如「移至開始」）不需要目標。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-197">Global commands (e.g., "Go to start") don't require a target.</span></span>
- <span data-ttu-id="3fbc7-198">對話使用者介面或 Cortana 等實體具有 AI 自然語言功能。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-198">Conversation user interfaces or entities like Cortana have an AI natural language capability.</span></span>
- <span data-ttu-id="3fbc7-199">自訂語音命令</span><span class="sxs-lookup"><span data-stu-id="3fbc7-199">Custom voice commands</span></span>

<span data-ttu-id="3fbc7-200">若要瞭解更多詳細資料以及可用語音命令的完整清單，以及如何使用它們，請參閱我們的[語音命令](voice-design.md)指引。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-200">To find out more details as well as a comprehensive list of available voice commands and how to use them, check out our [voice commanding](voice-design.md) guidance.</span></span>

<br>

---


### <a name="gaze-and-hololens-clicker"></a><span data-ttu-id="3fbc7-201">注視和 HoloLens Clicker</span><span class="sxs-lookup"><span data-stu-id="3fbc7-201">Gaze and HoloLens Clicker</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="3fbc7-202">HoloLens Clicker 是專為 HoloLens 建立的第一個週邊裝置。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-202">The HoloLens Clicker is the first peripheral device built specifically for HoloLens.</span></span> <span data-ttu-id="3fbc7-203">它隨附在 HoloLens （第1代）開發版本中。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-203">It is included with HoloLens (1st gen) Development Edition.</span></span> <span data-ttu-id="3fbc7-204">HoloLens Clicker 可讓使用者按一下最少的手運動，並認可為次要輸入。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-204">The HoloLens Clicker lets a user click with minimal hand motion, and commit as a secondary input.</span></span> <span data-ttu-id="3fbc7-205">HoloLens Clicker 會使用藍牙低功耗（BTLE）連接到 HoloLens （第1代）或 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-205">The HoloLens Clicker connects to HoloLens (1st gen) or HoloLens 2 using Bluetooth Low Energy (BTLE).</span></span><br>
        <br>
        [<span data-ttu-id="3fbc7-206">配對裝置的詳細資訊和指示</span><span class="sxs-lookup"><span data-stu-id="3fbc7-206">More information and instructions to pair the device</span></span>](hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="3fbc7-207">*映射： HoloLens Clicker*</span><span class="sxs-lookup"><span data-stu-id="3fbc7-207">*Image: HoloLens Clicker*</span></span>
    :::column-end:::
        :::column:::
       ![HoloLens Clicker](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a><span data-ttu-id="3fbc7-209">注視和 Xbox 無線控制器</span><span class="sxs-lookup"><span data-stu-id="3fbc7-209">Gaze and Xbox Wireless Controller</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="3fbc7-210">Xbox 無線控制器會使用 [A] 按鈕，以次要輸入的形式執行按一下 actuation。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-210">The Xbox Wireless Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="3fbc7-211">裝置會對應至一組預設的動作，以協助流覽和控制系統。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-211">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="3fbc7-212">如果您想要自訂控制器，請使用 Xbox 配件應用程式來設定您的 Xbox 無線控制器。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-212">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Wireless Controller.</span></span><br>
        <br>
        [<span data-ttu-id="3fbc7-213">如何將 Xbox 控制器與您的電腦配對</span><span class="sxs-lookup"><span data-stu-id="3fbc7-213">How to pair an Xbox controller with your PC</span></span>](hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="3fbc7-214">*映射： Xbox 無線控制器*</span><span class="sxs-lookup"><span data-stu-id="3fbc7-214">*Image: Xbox Wireless Controller*</span></span>
    :::column-end:::
        :::column:::
       ![Xbox 無線控制器](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a><span data-ttu-id="3fbc7-216">注視和 Xbox 適應性控制器</span><span class="sxs-lookup"><span data-stu-id="3fbc7-216">Gaze and Xbox Adaptive Controller</span></span>
<span data-ttu-id="3fbc7-217">Xbox 調調適型控制器是主要為了滿足行動裝置的需求，而這是一種整合式集線器，可協助讓混合現實更容易存取。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-217">Designed primarily to meet the needs of gamers with limited mobility, the Xbox Adaptive Controller is a unified hub for devices that helps make mixed reality more accessible.</span></span>

<span data-ttu-id="3fbc7-218">Xbox 調適型控制器會使用 [A] 按鈕，以次要輸入的形式執行按一下 actuation。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-218">The Xbox Adaptive Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="3fbc7-219">裝置會對應至一組預設的動作，以協助流覽和控制系統。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-219">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="3fbc7-220">如果您想要自訂控制器，請使用 Xbox 配件應用程式來設定 Xbox 調適型控制器。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-220">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Adaptive Controller.</span></span>

<span data-ttu-id="3fbc7-221">![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span><span class="sxs-lookup"><span data-stu-id="3fbc7-221">![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span></span><br>
<span data-ttu-id="3fbc7-222">*Xbox Adaptive Controller*</span><span class="sxs-lookup"><span data-stu-id="3fbc7-222">*Xbox Adaptive Controller*</span></span>

<span data-ttu-id="3fbc7-223">連接外部裝置（例如交換器、按鈕、掛接和搖桿），以建立唯一的自訂控制器體驗。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-223">Connect external devices such as switches, buttons, mounts, and joysticks to create a custom controller experience that is uniquely yours.</span></span> <span data-ttu-id="3fbc7-224">按鈕、操縱杆和觸發程式輸入都是由透過 3.5 mm 插座和 USB 埠連線的輔助裝置所控制。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-224">Button, thumbstick, and trigger inputs are controlled with assistive devices connected through 3.5mm jacks and USB ports.</span></span>

<span data-ttu-id="3fbc7-225">![Xbox Adaptive Controller 連接埠](images/xbox-adaptive-controller-ports.jpg)</span><span class="sxs-lookup"><span data-stu-id="3fbc7-225">![Xbox Adaptive Controller ports](images/xbox-adaptive-controller-ports.jpg)</span></span><br>
<span data-ttu-id="3fbc7-226">*Xbox Adaptive Controller 連接埠*</span><span class="sxs-lookup"><span data-stu-id="3fbc7-226">*Xbox Adaptive Controller ports*</span></span>

[<span data-ttu-id="3fbc7-227">裝置配對指示</span><span class="sxs-lookup"><span data-stu-id="3fbc7-227">Instructions to pair the device</span></span>](hardware-accessories.md#pairing-bluetooth-accessories)

<span data-ttu-id="3fbc7-228"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>在 Xbox 網站上可取得更多資訊</a></span><span class="sxs-lookup"><span data-stu-id="3fbc7-228"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>More info available on the Xbox site</a></span></span>

<br>

---

## <a name="composite-gestures"></a><span data-ttu-id="3fbc7-229">複合手勢</span><span class="sxs-lookup"><span data-stu-id="3fbc7-229">Composite gestures</span></span>

### <a name="air-tap"></a><span data-ttu-id="3fbc7-230">空中點選</span><span class="sxs-lookup"><span data-stu-id="3fbc7-230">Air tap</span></span>
<span data-ttu-id="3fbc7-231">[空中] 手勢（以及下面的其他手勢）只會對特定點碰做出回應。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-231">The air tap gesture (as well as the other gestures below) reacts only to a specific tap.</span></span> <span data-ttu-id="3fbc7-232">您的應用程式必須直接使用上述兩個主要元件手勢一節中所述的較低層級互動，以偵測其他功能表或抓住。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-232">To detect other taps, such as Menu or Grasp, your application must directly use the lower-level interactions described in the two key component gestures section above.</span></span>

### <a name="tap-and-hold"></a><span data-ttu-id="3fbc7-233">點一下並按住</span><span class="sxs-lookup"><span data-stu-id="3fbc7-233">Tap and hold</span></span>
<span data-ttu-id="3fbc7-234">按住只是維持空中點選的手指朝下位置。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-234">Hold is simply maintaining the downward finger position of the air tap.</span></span> <span data-ttu-id="3fbc7-235">結合 [按下] 和 [按住]，可讓您在結合 arm 動作（例如，挑選物件，而不是啟動它或 mousedown 次要互動，例如顯示操作功能表）時，使用各種較複雜的「按一下並拖曳」互動。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-235">The combination of air tap and hold allows for a variety of more complex "click and drag" interactions when combined with arm movement such as picking up an object instead of activating it or mousedown secondary interactions such as showing a context menu.</span></span>
<span data-ttu-id="3fbc7-236">不過，針對這個手勢進行設計時應格外小心，因為使用者很容易在任何延伸手勢的過程中放鬆其手勢。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-236">Caution should be used when designing for this gesture however, as users can be prone to relaxing their hand postures during the course of any extended gesture.</span></span>

### <a name="manipulation"></a><span data-ttu-id="3fbc7-237">操作</span><span class="sxs-lookup"><span data-stu-id="3fbc7-237">Manipulation</span></span>
<span data-ttu-id="3fbc7-238">當您想要讓全像投影對使用者的移動進行1:1 回應時，可以使用操作手勢來移動、調整大小或旋轉全息形狀。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-238">Manipulation gestures can be used to move, resize, or rotate a hologram when you want the hologram to react 1:1 to the user's hand movements.</span></span> <span data-ttu-id="3fbc7-239">這類 1:1 移動的用途之一是要讓使用者可以實際繪圖。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-239">One use for such 1:1 movements is to let the user draw or paint in the world.</span></span>
<span data-ttu-id="3fbc7-240">操作手勢的初始定向應經由注視或指向來完成。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-240">The initial targeting for a manipulation gesture should be done by gaze or pointing.</span></span> <span data-ttu-id="3fbc7-241">當點一下和按住開始時，物件的任何操作都是由手動移動處理，讓使用者在操作時能夠四處尋找。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-241">Once the tap and hold starts, any manipulation of the object is handled by hand movements, freeing the user to look around while they manipulate.</span></span>

### <a name="navigation"></a><span data-ttu-id="3fbc7-242">瀏覽</span><span class="sxs-lookup"><span data-stu-id="3fbc7-242">Navigation</span></span>
<span data-ttu-id="3fbc7-243">瀏覽手勢的運作方式如同虛擬搖桿，可用來瀏覽 UI 小工具，例如放射狀功能表。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-243">Navigation gestures operate like a virtual joystick, and can be used to navigate UI widgets, such as radial menus.</span></span> <span data-ttu-id="3fbc7-244">您可點選並按住來啟動手勢，然後在標準化 3D Cube (在初次按壓時置中) 中移動您的手。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-244">You tap and hold to start the gesture and then move your hand within a normalized 3D cube, centered around the initial press.</span></span> <span data-ttu-id="3fbc7-245">您可以將您的手沿著 X、 Y 或 Z 軸從值 -1 移到 1 (而 0 表示起點)。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-245">You can move your hand along the X, Y or Z axis from a value of -1 to 1, with 0 being the starting point.</span></span>
<span data-ttu-id="3fbc7-246">瀏覽可用來建置以速度為基礎的連續捲動或縮放手勢，類似於藉由按一下滑鼠中間按鈕，然後上下移動滑鼠來捲動 2D UI。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-246">Navigation can be used to build velocity-based continuous scrolling or zooming gestures, similar to scrolling a 2D UI by clicking the middle mouse button and then moving the mouse up and down.</span></span>

<span data-ttu-id="3fbc7-247">與 rails 的導覽指的是在特定軸中辨識移動的能力，直到達到該軸上的特定臨界值為止。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-247">Navigation with rails refers to the ability of recognizing movements in certain axis until a certain threshold is reached on that axis.</span></span> <span data-ttu-id="3fbc7-248">這僅適用于開發人員在應用程式中啟用多個軸的移動時，例如，如果應用程式設定為在 X、Y 軸上辨識導覽手勢，但也使用 rails 指定 X 軸。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-248">This is only useful when movement in more than one axis is enabled in an application by the developer, such as if an application is configured to recognize navigation gestures across X, Y axis but also specified X axis with rails.</span></span> <span data-ttu-id="3fbc7-249">在此情況下，如果 Y 軸上也發生手移動，系統將會辨識 X 軸上的手上移動，前提是它們會保留在 X 軸上的虛數滑軌（guide）中。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-249">In this case the system will recognize hand movements across X axis as long as they remain within an imaginary rails (guide) on the X axis, if hand movement also occurs on the Y axis.</span></span>

<span data-ttu-id="3fbc7-250">在 2D 應用程式內，使用者可以使用垂直瀏覽手勢在應用程式內捲動、縮放或拖曳。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-250">Within 2D apps, users can use vertical navigation gestures to scroll, zoom, or drag inside the app.</span></span> <span data-ttu-id="3fbc7-251">這會在應用程式中插入虛擬手指觸控，以模擬同類型的觸控手勢。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-251">This injects virtual finger touches to the app to simulate touch gestures of the same type.</span></span> <span data-ttu-id="3fbc7-252">使用者可以藉由選取按鈕或說「< Scroll/拖曳/縮放 > 工具」，在應用程式上方的工具之間切換，藉以選取要執行的動作。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-252">Users can select which of these actions take place by toggling between the tools on the bar above the application, either by selecting the button or saying '<Scroll/Drag/Zoom> Tool'.</span></span>

[<span data-ttu-id="3fbc7-253">複合手勢的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="3fbc7-253">More info on composite gestures</span></span>](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a><span data-ttu-id="3fbc7-254">手勢辨識器</span><span class="sxs-lookup"><span data-stu-id="3fbc7-254">Gesture recognizers</span></span>

<span data-ttu-id="3fbc7-255">使用手勢辨識的其中一個優點是，您可以只針對目前目標的全息影像可以接受的手勢設定手勢辨識器。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-255">One benefit of using gesture recognition is that you can configure a gesture recognizer only for the gestures the currently targeted hologram can accept.</span></span> <span data-ttu-id="3fbc7-256">平臺只會視需要去除混淆，以區別那些特定支援的手勢。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-256">The platform only does disambiguation as necessary to distinguish those particular supported gestures.</span></span> <span data-ttu-id="3fbc7-257">如此一來，只支援「點按」的全像投影可以接受按下和放開之間的任何時間長度，而支援兩個點按和按住的全像投影則可以在按住時間臨界值之後，將點擊次數提升至保留。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-257">In this way, a hologram that just supports air tap can accept any length of time between press and release, while a hologram that supports both tap and hold can promote the tap to a hold after the hold time threshold.</span></span>

## <a name="hand-recognition"></a><span data-ttu-id="3fbc7-258">手部辨識</span><span class="sxs-lookup"><span data-stu-id="3fbc7-258">Hand recognition</span></span>
<span data-ttu-id="3fbc7-259">HoloLens 可藉由追蹤裝置可見的任一手或雙手位置來辨識手勢。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-259">HoloLens recognizes hand gestures by tracking the position of either or both hands that are visible to the device.</span></span> <span data-ttu-id="3fbc7-260">當手部處於就緒狀態 (手背朝向您且食指朝上) 或按下狀態 (手背朝向您且食指朝下) 時，HoloLens 就會看見手部。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-260">HoloLens sees hands when they are in either the ready state (back of the hand facing you with index finger up) or the pressed state (back of the hand facing you with the index finger down).</span></span> <span data-ttu-id="3fbc7-261">當手上有其他人時，HoloLens 會忽略它們。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-261">When hands are in other poses, HoloLens ignores them.</span></span>
<span data-ttu-id="3fbc7-262">對於 HoloLens 偵測到的每一手勢，您都可以存取其位置，而不需要方向和其按下狀態。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-262">For each hand that HoloLens detects, you can access its position without orientation and its pressed state.</span></span> <span data-ttu-id="3fbc7-263">當手部接近手勢框架邊緣時，您也會取得方向向量，而您可對使用者顯示該向量，讓他們知道如何移動其手部以回到 HoloLens 可看見手部的位置。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-263">As the hand nears the edge of the gesture frame, you're also provided with a direction vector, which you can show to the user so they know how to move their hand to get it back where HoloLens can see it.</span></span>

## <a name="gesture-frame"></a><span data-ttu-id="3fbc7-264">手勢框架</span><span class="sxs-lookup"><span data-stu-id="3fbc7-264">Gesture frame</span></span>
<span data-ttu-id="3fbc7-265">對於 HoloLens 上的手勢，手必須位於手勢框架內，筆勢檢測攝影機可以適當地查看，從鼻子到 waist，以及在肩膀之間。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-265">For gestures on HoloLens, the hand must be within a gesture frame, in a range that the gesture-sensing cameras can see appropriately,  from nose to waist and between the shoulders.</span></span> <span data-ttu-id="3fbc7-266">使用者必須在此辨識區域上訓練，以進行動作的成功並讓自己的緩和。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-266">Users need to be trained on this area of recognition both for success of action and for their own comfort.</span></span> <span data-ttu-id="3fbc7-267">許多使用者一開始會假設筆勢框架必須透過 HoloLens 在其觀看範圍內，並將其 uncomfortably 以進行互動。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-267">Many users will initially assume that the gesture frame must be within their view through HoloLens, and hold their arms up uncomfortably in order to interact.</span></span> <span data-ttu-id="3fbc7-268">使用 HoloLens Clicker 時，不需要將手放在筆勢框架中。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-268">When using the HoloLens Clicker, it's not necessary for hands to be within the gesture frame.</span></span>

<span data-ttu-id="3fbc7-269">特別是在連續手勢的情況下，使用者在移動全像投影物件時，會有一些風險會將其手移至手勢框架外，例如，並失去其預期的結果。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-269">In the case of continuous gestures in particular, there is some risk of users moving their hands outside of the gesture frame while in mid-gesture when moving a holographic object, for example, and losing their intended outcome.</span></span>

<span data-ttu-id="3fbc7-270">您應該考量下列三個事項：</span><span class="sxs-lookup"><span data-stu-id="3fbc7-270">There are three things that you should consider:</span></span>

- <span data-ttu-id="3fbc7-271">筆勢框架的存在和大致界限的使用者教育。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-271">User education on the gesture frame's existence and approximate boundaries.</span></span> <span data-ttu-id="3fbc7-272">這會在 HoloLens 設定期間進行講授。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-272">This is taught during HoloLens setup.</span></span>

- <span data-ttu-id="3fbc7-273">當使用者的手勢接近或中斷應用程式內的手勢框架邊界時，會通知他們，而失去的手勢會導致不想要的結果。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-273">Notifying users when their gestures are nearing or breaking the gesture frame boundaries within an application to the degree that a lost gesture leads to undesired outcomes.</span></span> <span data-ttu-id="3fbc7-274">研究已顯示這類通知系統的重要品質。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-274">Research has shown the key qualities of such a notification system.</span></span> <span data-ttu-id="3fbc7-275">HoloLens shell 會在中央游標上提供這種類型通知的良好範例--視覺效果，指出發生邊界相交的方向。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-275">The HoloLens shell provides a good example of this type of notification--visual, on the central cursor, indicating the direction in which boundary crossing is taking place.</span></span>

- <span data-ttu-id="3fbc7-276">您應該將突破手勢框架界限的後果最小化。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-276">Consequences of breaking the gesture frame boundaries should be minimized.</span></span> <span data-ttu-id="3fbc7-277">一般來說，這表示手勢的結果應該在界限停止，而不是反轉。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-277">In general, this means that the outcome of a gesture should be stopped at the boundary, and not reversed.</span></span> <span data-ttu-id="3fbc7-278">例如，如果使用者在房間內移動一些全像攝影物件，則在軌跡框架遭到入侵時，移動應該會停止，而不會傳回至起點。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-278">For example, if a user is moving some holographic object across a room, the movement should stop when the gesture frame is breached, and not returned to the starting point.</span></span> <span data-ttu-id="3fbc7-279">使用者可能會遇到一些挫折，但可能會更快速地瞭解界限，而不必每次都重新開機其完整的預期動作。</span><span class="sxs-lookup"><span data-stu-id="3fbc7-279">The user might experience some frustration, but might more quickly understand the boundaries, and not have to restart their full intended actions each time.</span></span>



## <a name="see-also"></a><span data-ttu-id="3fbc7-280">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fbc7-280">See also</span></span>
* [<span data-ttu-id="3fbc7-281">眼動式互動</span><span class="sxs-lookup"><span data-stu-id="3fbc7-281">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="3fbc7-282">HoloLens 2 的眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="3fbc7-282">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="3fbc7-283">目光和停駐</span><span class="sxs-lookup"><span data-stu-id="3fbc7-283">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="3fbc7-284">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="3fbc7-284">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="3fbc7-285">手 - 手勢</span><span class="sxs-lookup"><span data-stu-id="3fbc7-285">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="3fbc7-286">手 - 指向和行動</span><span class="sxs-lookup"><span data-stu-id="3fbc7-286">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="3fbc7-287">本能互動</span><span class="sxs-lookup"><span data-stu-id="3fbc7-287">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="3fbc7-288">語音輸入</span><span class="sxs-lookup"><span data-stu-id="3fbc7-288">Voice input</span></span>](voice-input.md)

