---
title: 手勢
description: 手勢可讓使用者在混合現實中採取動作。
author: rwinj
ms.author: cmeekhof
ms.date: 02/24/2019
ms.topic: article
keywords: 混合現實、手勢、互動、設計
ms.openlocfilehash: ae8af8fdb0bd224d127092c6636d473f383ab6f9
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435204"
---
# <a name="gestures"></a><span data-ttu-id="82f78-104">手勢</span><span class="sxs-lookup"><span data-stu-id="82f78-104">Gestures</span></span>

<span data-ttu-id="82f78-105">手勢可讓使用者在混合現實中採取動作。</span><span class="sxs-lookup"><span data-stu-id="82f78-105">Hand gestures allow users to take action in mixed reality.</span></span> <span data-ttu-id="82f78-106">互動**是以 [** 目標] 和 [**手勢**] 或 [**聲音**] 為基礎，以根據任何專案的目標來採取動作。</span><span class="sxs-lookup"><span data-stu-id="82f78-106">Interaction is built on **gaze** to target and **gesture** or **voice** to act upon whatever element has been targeted.</span></span> <span data-ttu-id="82f78-107">右手手勢並不會在空間中提供精確的位置，但是放入 HoloLens 並立即與內容互動的簡單，可讓使用者在沒有任何其他配件的情況下工作。</span><span class="sxs-lookup"><span data-stu-id="82f78-107">Hand gestures do not provide a precise location in space, but the simplicity of putting on a HoloLens and immediately interacting with content allows users to get to work without any other accessories.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/kwn9Lh0E_vU]

## <a name="device-support"></a><span data-ttu-id="82f78-108">裝置支援</span><span class="sxs-lookup"><span data-stu-id="82f78-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="82f78-109"><strong>特徵</strong></span><span class="sxs-lookup"><span data-stu-id="82f78-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="82f78-110"><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="82f78-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="82f78-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="82f78-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="82f78-112"><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></span><span class="sxs-lookup"><span data-stu-id="82f78-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="82f78-113">手勢</span><span class="sxs-lookup"><span data-stu-id="82f78-113">Gestures</span></span></td>
        <td><span data-ttu-id="82f78-114">✔️</span><span class="sxs-lookup"><span data-stu-id="82f78-114">✔️</span></span></td>
        <td><span data-ttu-id="82f78-115">✔️</span><span class="sxs-lookup"><span data-stu-id="82f78-115">✔️</span></span></td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="82f78-116">清楚表達的手</span><span class="sxs-lookup"><span data-stu-id="82f78-116">Articulated hands</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="82f78-117">✔️</span><span class="sxs-lookup"><span data-stu-id="82f78-117">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

> [!NOTE]
> <span data-ttu-id="82f78-118">[即將推出](news.md)更多 HoloLens 2 特定指引。</span><span class="sxs-lookup"><span data-stu-id="82f78-118">More guidance specific to HoloLens 2 [coming soon](news.md).</span></span>

## <a name="gaze-and-commit"></a><span data-ttu-id="82f78-119">注視和認可</span><span class="sxs-lookup"><span data-stu-id="82f78-119">Gaze-and-commit</span></span>

<span data-ttu-id="82f78-120">若要採取動作，右手手勢會使用[head 注視](gaze-and-commit.md)作為目的機制。</span><span class="sxs-lookup"><span data-stu-id="82f78-120">To take actions, hand gestures use [head gaze](gaze-and-commit.md) as the targeting mechanism.</span></span> <span data-ttu-id="82f78-121">[**注視**] 和 [**空中**] 手勢的組合會導致**注視和認可**互動。</span><span class="sxs-lookup"><span data-stu-id="82f78-121">The combination of **Gaze** and the **Air tap** gesture results in a **gaze-and-commit** interaction.</span></span> <span data-ttu-id="82f78-122">[注視] 和 [認可] 的替代方法是 [**點和認可**]，由[動作控制器](motion-controllers.md)啟用。</span><span class="sxs-lookup"><span data-stu-id="82f78-122">An alternative to gaze-and-commit is **point-and-commit**, enabled by [motion controllers](motion-controllers.md).</span></span> <span data-ttu-id="82f78-123">在 HoloLens 上執行的應用程式只需要支援注視和認可，因為 HoloLens 並不支援動作控制器。</span><span class="sxs-lookup"><span data-stu-id="82f78-123">Apps that run on HoloLens only need to support gaze-and-commit since HoloLens does not support motion controllers.</span></span> <span data-ttu-id="82f78-124">在 HoloLens 和沉浸式頭戴式裝置上執行的應用程式，都應該支援注視驅動和指標驅動的互動，讓使用者選擇他們所使用的輸入裝置。</span><span class="sxs-lookup"><span data-stu-id="82f78-124">Apps that run on both HoloLens and immersive headsets should support both gaze-driven and pointing-driven interactions, to give users choice in what input device they use.</span></span>

## <a name="the-two-core-gestures-of-hololens"></a><span data-ttu-id="82f78-125">HoloLens 的兩個核心手勢</span><span class="sxs-lookup"><span data-stu-id="82f78-125">The two core gestures of HoloLens</span></span>

<span data-ttu-id="82f78-126">HoloLens 目前能夠辨識兩個核心元件手勢：**空中碰**和**Bloom**。</span><span class="sxs-lookup"><span data-stu-id="82f78-126">HoloLens currently recognizes two core component gestures - **Air tap** and **Bloom**.</span></span> <span data-ttu-id="82f78-127">這兩個核心互動是開發人員可以存取的最低空間輸入資料層級。</span><span class="sxs-lookup"><span data-stu-id="82f78-127">These two core interactions are the lowest level of spatial input data that a developer can access.</span></span> <span data-ttu-id="82f78-128">它們會形成各種可能的使用者動作的基礎。</span><span class="sxs-lookup"><span data-stu-id="82f78-128">They form the foundation for a variety of possible user actions.</span></span>

### <a name="air-tap"></a><span data-ttu-id="82f78-129">空中點選</span><span class="sxs-lookup"><span data-stu-id="82f78-129">Air tap</span></span>

<span data-ttu-id="82f78-130">「點按」是一種碰觸的手勢，類似于按一下滑鼠或選取。</span><span class="sxs-lookup"><span data-stu-id="82f78-130">Air tap is a tapping gesture with the hand held upright, similar to a mouse click or select.</span></span> <span data-ttu-id="82f78-131">這適用于大部分的 HoloLens 體驗，以在以[注視](gaze-and-commit.md)為目標之後，于 UI 專案上使用「按一下」。</span><span class="sxs-lookup"><span data-stu-id="82f78-131">This is used in most HoloLens experiences for the equivalent of a "click" on a UI element after targeting it with [Gaze](gaze-and-commit.md).</span></span> <span data-ttu-id="82f78-132">這是您一次學習的通用動作，然後適用于您所有的應用程式。</span><span class="sxs-lookup"><span data-stu-id="82f78-132">It is a universal action that you learn once and then apply across all your apps.</span></span> <span data-ttu-id="82f78-133">執行 select 的其他方式是在[HoloLens Clicker](hardware-accessories.md#hololens-clicker)上按單一按鈕，或說出語音命令「選取」。</span><span class="sxs-lookup"><span data-stu-id="82f78-133">Other ways to perform select are by pressing the single button on a [HoloLens Clicker](hardware-accessories.md#hololens-clicker) or by speaking the voice command "Select".</span></span>

<span data-ttu-id="82f78-134">在 HoloLens](images/image9.png) 上 ![右手手勢的準備狀態</span><span class="sxs-lookup"><span data-stu-id="82f78-134">![Ready state for hand gestures on HoloLens](images/image9.png)</span></span><br>
<span data-ttu-id="82f78-135">*適用于 HoloLens 的就緒狀態。*</span><span class="sxs-lookup"><span data-stu-id="82f78-135">*Ready state for Air tap on HoloLens.*</span></span>

<span data-ttu-id="82f78-136">「空中碰」是一種不連續的手勢。</span><span class="sxs-lookup"><span data-stu-id="82f78-136">Air tap is a discrete gesture.</span></span> <span data-ttu-id="82f78-137">選取範圍是 [已完成] 或 [不是]、[動作] 或 [不會在經驗中採取]。</span><span class="sxs-lookup"><span data-stu-id="82f78-137">A selection is either completed or it is not, an action is or is not taken within an experience.</span></span> <span data-ttu-id="82f78-138">雖然不建議使用某些特定用途，但還是可以從主要元件的組合建立其他離散手勢（例如，按兩下手勢來表示與單鍵不同的東西）。</span><span class="sxs-lookup"><span data-stu-id="82f78-138">It is possible, though not recommended without some specific purpose, to create other discrete gestures from combinations of the main components (e.g. a double-tap gesture to mean something different than a single-tap).</span></span>

<span data-ttu-id="82f78-139">在 [就緒] 位置中 ![手指，然後按一下或按一下 [動作]](images/readyandpress.jpg)</span><span class="sxs-lookup"><span data-stu-id="82f78-139">![Finger in the ready position and then a tap or click motion](images/readyandpress.jpg)</span></span><br>
<span data-ttu-id="82f78-140">*如何執行點擊動作：將您的索引指向準備好的位置，按下手指以點擊或選取，然後再備份至發行。*</span><span class="sxs-lookup"><span data-stu-id="82f78-140">*How to perform an Air tap: Raise your index finger to the ready position, press your finger down to tap or select and then back up to release.*</span></span>

### <a name="bloom"></a><span data-ttu-id="82f78-141">Bloom</span><span class="sxs-lookup"><span data-stu-id="82f78-141">Bloom</span></span>

<span data-ttu-id="82f78-142">Bloom 是「home」手勢，並會單獨保留給您。</span><span class="sxs-lookup"><span data-stu-id="82f78-142">Bloom is the "home" gesture and is reserved for that alone.</span></span> <span data-ttu-id="82f78-143">這是一種特殊的系統動作，可用來返回 [開始] 功能表。</span><span class="sxs-lookup"><span data-stu-id="82f78-143">It is a special system action that is used to go back to the Start Menu.</span></span> <span data-ttu-id="82f78-144">這等同于在鍵盤上按下 Windows 鍵，或在 Xbox 控制器上按 Xbox 按鈕。</span><span class="sxs-lookup"><span data-stu-id="82f78-144">It is equivalent to pressing the Windows key on a keyboard or the Xbox button on an Xbox controller.</span></span> <span data-ttu-id="82f78-145">使用者可以使用任一手勢。</span><span class="sxs-lookup"><span data-stu-id="82f78-145">The user can use either hand.</span></span>

![HoloLens 上的 Bloom 手勢](images/image10-640px.png)

<span data-ttu-id="82f78-147">若要在 HoloLens 上進行 bloom 手勢，請將您的手上移一處，並將您的使用方式放在一起。</span><span class="sxs-lookup"><span data-stu-id="82f78-147">To do the bloom gesture on HoloLens, hold out your hand, palm up, with your fingertips together.</span></span> <span data-ttu-id="82f78-148">然後開啟您的手。</span><span class="sxs-lookup"><span data-stu-id="82f78-148">Then open your hand.</span></span> <span data-ttu-id="82f78-149">請注意，您也可以說「嗨，Cortana，Go Home」來開始。</span><span class="sxs-lookup"><span data-stu-id="82f78-149">Note, you can also always return to Start by saying "Hey Cortana, Go Home".</span></span> <span data-ttu-id="82f78-150">應用程式無法特別回應 home 動作，因為這些是由系統處理。</span><span class="sxs-lookup"><span data-stu-id="82f78-150">Apps cannot react specifically to a home action, as these are handled by the system.</span></span>

<span data-ttu-id="82f78-151">![Bloom 手勢](images/bloom-giphy.gif)</span><span class="sxs-lookup"><span data-stu-id="82f78-151">![Bloom gesture](images/bloom-giphy.gif)</span></span><br>
<span data-ttu-id="82f78-152">*如何在 HoloLens 上執行 bloom 手勢。*</span><span class="sxs-lookup"><span data-stu-id="82f78-152">*How to perform the bloom gesture on HoloLens.*</span></span>

## <a name="composite-gestures"></a><span data-ttu-id="82f78-153">複合手勢</span><span class="sxs-lookup"><span data-stu-id="82f78-153">Composite gestures</span></span>

<span data-ttu-id="82f78-154">應用程式不只可以辨識個別的點選動作。</span><span class="sxs-lookup"><span data-stu-id="82f78-154">Apps can recognize more than just individual taps.</span></span> <span data-ttu-id="82f78-155">結合點選、按住和放開與手部移動，即可執行更複雜的複合手勢。</span><span class="sxs-lookup"><span data-stu-id="82f78-155">By combining tap, hold and release with the movement of the hand, more complex composite gestures can be performed.</span></span> <span data-ttu-id="82f78-156">這些複合或高階手勢是以開發人員可以存取的低階空間輸入資料 (來自空中點選和綻開) 為建置基礎。</span><span class="sxs-lookup"><span data-stu-id="82f78-156">These composite or high-level gestures build on the low-level spatial input data (from Air tap and Bloom) that developers have access to.</span></span>

<table>
<tr>
<th> <span data-ttu-id="82f78-157">複合手勢</span><span class="sxs-lookup"><span data-stu-id="82f78-157">Composite gesture</span></span></th><th> <span data-ttu-id="82f78-158">如何套用</span><span class="sxs-lookup"><span data-stu-id="82f78-158">How to apply</span></span></th>
</tr><tr>
<td><span data-ttu-id="82f78-159">空中點選</span><span class="sxs-lookup"><span data-stu-id="82f78-159">Air tap</span></span></td><td><span data-ttu-id="82f78-160">空中點選手勢 (以及下列其他手勢) 只會回應特定點選動作。</span><span class="sxs-lookup"><span data-stu-id="82f78-160">The Air tap gesture (as well as the other gestures below) reacts only to a specific tap.</span></span> <span data-ttu-id="82f78-161">若要偵測其他點選動作 (例如功能表或抓握)，您的應用程式必須直接使用上面兩個主要元件手勢一節中所述的較低層級互動。</span><span class="sxs-lookup"><span data-stu-id="82f78-161">To detect other taps, such as Menu or Grasp, your app must directly use the lower-level interactions described in two key component gestures section above.</span></span></td>
</tr><tr>
<td><span data-ttu-id="82f78-162">Tap and hold</span><span class="sxs-lookup"><span data-stu-id="82f78-162">Tap and hold</span></span></td><td><p><span data-ttu-id="82f78-163">按住只是維持空中點選的手指朝下位置。</span><span class="sxs-lookup"><span data-stu-id="82f78-163">Hold is simply maintaining the downward finger position of the air tap.</span></span> <span data-ttu-id="82f78-164">結合 [按下] 和 [按住]，可讓您在結合 arm 動作（例如挑選物件，而不是啟動或 &quot;mousedown&quot; 次要互動）時，&quot;按一下和拖曳&quot; 的互動例如顯示內容功能表。</span><span class="sxs-lookup"><span data-stu-id="82f78-164">The combination of air tap and hold allows for a variety of more complex &quot;click and drag&quot; interactions when combined with arm movement such as picking up an object instead of activating it or &quot;mousedown&quot; secondary interactions such as showing a context menu.</span></span></p><p><span data-ttu-id="82f78-165">不過，針對這個手勢進行設計時應格外小心，因為使用者很容易在任何延伸手勢的過程中放鬆其手勢。</span><span class="sxs-lookup"><span data-stu-id="82f78-165">Caution should be used when designing for this gesture however, as users can be prone to relaxing their hand postures during the course of any extended gesture.</span></span></p></td>
</tr><tr>
<td><span data-ttu-id="82f78-166">操作</span><span class="sxs-lookup"><span data-stu-id="82f78-166">Manipulation</span></span></td><td><p><span data-ttu-id="82f78-167">當您想要讓全像投影對使用者&#39;的手間移動做出1:1 回應時，可以使用操作手勢來移動、調整大小或旋轉全息形狀。</span><span class="sxs-lookup"><span data-stu-id="82f78-167">Manipulation gestures can be used to move, resize or rotate a hologram when you want the hologram to react 1:1 to the user&#39;s hand movements.</span></span> <span data-ttu-id="82f78-168">這類 1:1 移動的用途之一是要讓使用者可以實際繪圖。</span><span class="sxs-lookup"><span data-stu-id="82f78-168">One use for such 1:1 movements is to let the user draw or paint in the world.</span></span></p><p><span data-ttu-id="82f78-169">操作手勢的初始定向應經由注視或指向來完成。</span><span class="sxs-lookup"><span data-stu-id="82f78-169">The initial targeting for a manipulation gesture should be done by gaze or pointing.</span></span> <span data-ttu-id="82f78-170">一旦啟動點選並按住，任何物件操作都由手部移動接著處理，讓使用者在操作時有空四周環顧。</span><span class="sxs-lookup"><span data-stu-id="82f78-170">Once the tap and hold starts, any manipulation of the object is then handled by hand movements, freeing the user to look around while they manipulate.</span></span></p></td>
</tr><tr>
<td><span data-ttu-id="82f78-171">瀏覽</span><span class="sxs-lookup"><span data-stu-id="82f78-171">Navigation</span></span></td><td><p><span data-ttu-id="82f78-172">瀏覽手勢的運作方式如同虛擬搖桿，可用來瀏覽 UI 小工具，例如放射狀功能表。</span><span class="sxs-lookup"><span data-stu-id="82f78-172">Navigation gestures operate like a virtual joystick, and can be used to navigate UI widgets, such as radial menus.</span></span> <span data-ttu-id="82f78-173">您可點選並按住來啟動手勢，然後在標準化 3D Cube (在初次按壓時置中) 中移動您的手。</span><span class="sxs-lookup"><span data-stu-id="82f78-173">You tap and hold to start the gesture and then move your hand within a normalized 3D cube, centered around the initial press.</span></span> <span data-ttu-id="82f78-174">您可以將您的手沿著 X、 Y 或 Z 軸從值 -1 移到 1 (而 0 表示起點)。</span><span class="sxs-lookup"><span data-stu-id="82f78-174">You can move your hand along the X, Y or Z axis from a value of -1 to 1, with 0 being the starting point.</span></span></p><p><span data-ttu-id="82f78-175">瀏覽可用來建置以速度為基礎的連續捲動或縮放手勢，類似於藉由按一下滑鼠中間按鈕，然後上下移動滑鼠來捲動 2D UI。</span><span class="sxs-lookup"><span data-stu-id="82f78-175">Navigation can be used to build velocity-based continuous scrolling or zooming gestures, similar to scrolling a 2D UI by clicking the middle mouse button and then moving the mouse up and down.</span></span></p><p><span data-ttu-id="82f78-176">利用滑軌瀏覽就是指在達到特定座標軸上特定閾值前，辨識該座標軸內移動的功能。</span><span class="sxs-lookup"><span data-stu-id="82f78-176">Navigation with rails refers to the ability of recognizing movements in certain axis until certain threshold is reached on that axis.</span></span> <span data-ttu-id="82f78-177">只有當開發人員在應用程式中啟用多個座標軸移動時，這項功能才有用，例如將應用程式設定為可辨識遍及 X、Y 軸的瀏覽手勢，但也包含採用滑軌的指定 X 軸。</span><span class="sxs-lookup"><span data-stu-id="82f78-177">This is only useful, when movement in more than one axis is enabled in an application by the developer, e.g. if an application is configured to recognize navigation gestures across X, Y axis but also specified X axis with rails.</span></span> <span data-ttu-id="82f78-178">在此情況下，如果手部移動也會發生於 Y 軸，只要這些移動留在 X 軸上的虛構滑軌 (輔助線) 內，系統就會辨識遍及 X 軸的手部移動。</span><span class="sxs-lookup"><span data-stu-id="82f78-178">In this case system will recognize hand movements across X axis as long as they remain within an imaginary rails (guide) on X axis, if hand movement also occurs Y axis.</span></span></p><p><span data-ttu-id="82f78-179">在 2D 應用程式內，使用者可以使用垂直瀏覽手勢在應用程式內捲動、縮放或拖曳。</span><span class="sxs-lookup"><span data-stu-id="82f78-179">Within 2D apps, users can use vertical navigation gestures to scroll, zoom, or drag inside the app.</span></span> <span data-ttu-id="82f78-180">這會在應用程式中插入虛擬手指觸控，以模擬同類型的觸控手勢。</span><span class="sxs-lookup"><span data-stu-id="82f78-180">This injects virtual finger touches to the app to simulate touch gestures of the same type.</span></span> <span data-ttu-id="82f78-181">使用者可以藉由選取按鈕或說&#39;&lt;Scroll/拖曳/縮放&gt; 工具&#39;，在應用程式上方的工具之間切換，藉以選取要執行的動作。</span><span class="sxs-lookup"><span data-stu-id="82f78-181">Users can select which of these actions take place by toggling between the tools on the bar above the app, either by selecting the button or saying &#39;&lt;Scroll/Drag/Zoom&gt; Tool&#39;.</span></span></p></td>
</tr>
</table>



### <a name="gesture-recognizers"></a><span data-ttu-id="82f78-182">手勢辨識器</span><span class="sxs-lookup"><span data-stu-id="82f78-182">Gesture recognizers</span></span>

<span data-ttu-id="82f78-183">使用手勢辨識的其中一個優勢，就是您可以只針對目前定向的全像投影可接受的手勢，設定手勢辨識器。</span><span class="sxs-lookup"><span data-stu-id="82f78-183">One benefit of using gesture recognition is that you can configure a gesture recognizer just for the gestures the currently targeted hologram can accept.</span></span> <span data-ttu-id="82f78-184">此平台只會為了區分這些特定支援的手勢而進行必要的去除混淆。</span><span class="sxs-lookup"><span data-stu-id="82f78-184">The platform will do only the disambiguation necessary to distinguish those particular supported gestures.</span></span> <span data-ttu-id="82f78-185">如此一來，只支援空中點選的全像投影可以接受在按下與放開之間的任何時間長度，而同時支援點選和按住的全像投影可以在按住時間閾值後將點選提升為按住。</span><span class="sxs-lookup"><span data-stu-id="82f78-185">That way, a hologram that just supports air tap can accept any length of time between press and release, while a hologram that supports both tap and hold can promote the tap to a hold after the hold time threshold.</span></span>

## <a name="hand-recognition"></a><span data-ttu-id="82f78-186">手部辨識</span><span class="sxs-lookup"><span data-stu-id="82f78-186">Hand recognition</span></span>

<span data-ttu-id="82f78-187">HoloLens 可藉由追蹤裝置可見的任一手或雙手位置來辨識手勢。</span><span class="sxs-lookup"><span data-stu-id="82f78-187">HoloLens recognizes hand gestures by tracking the position of either or both hands that are visible to the device.</span></span> <span data-ttu-id="82f78-188">當 HoloLens 處於 [**就緒] 狀態**（您有食指的背面）或**按下的狀態**（向下鍵向下的背面）時，會看到手。</span><span class="sxs-lookup"><span data-stu-id="82f78-188">HoloLens sees hands when they are in either the **ready state** (back of the hand facing you with index finger up) or the **pressed state** (back of the hand facing you with the index finger down).</span></span> <span data-ttu-id="82f78-189">當手部為其他姿勢時，HoloLens 就會忽略手部。</span><span class="sxs-lookup"><span data-stu-id="82f78-189">When hands are in other poses, the HoloLens will ignore them.</span></span>

<span data-ttu-id="82f78-190">對於 HoloLens 偵測到的每隻手，您可以存取其位置 (不含方向) 及其按下狀態。</span><span class="sxs-lookup"><span data-stu-id="82f78-190">For each hand that HoloLens detects, you can access its position (without orientation) and its pressed state.</span></span> <span data-ttu-id="82f78-191">當手部接近手勢框架邊緣時，您也會取得方向向量，而您可對使用者顯示該向量，讓他們知道如何移動其手部以回到 HoloLens 可看見手部的位置。</span><span class="sxs-lookup"><span data-stu-id="82f78-191">As the hand nears the edge of the gesture frame, you're also provided with a direction vector, which you can show to the user so they know how to move their hand to get it back where HoloLens can see it.</span></span>

## <a name="gesture-frame"></a><span data-ttu-id="82f78-192">手勢框架</span><span class="sxs-lookup"><span data-stu-id="82f78-192">Gesture frame</span></span>

<span data-ttu-id="82f78-193">對於 HoloLens 上的手勢，手部必須在「手勢框架」內，也就是手勢感應攝影機可適度看見的範圍 (約略是從鼻子到腰部的範圍，且介於雙肩之間) 中。</span><span class="sxs-lookup"><span data-stu-id="82f78-193">For gestures on HoloLens, the hand must be within a “gesture frame”, in a range that the gesture-sensing cameras can see appropriately (very roughly from nose to waist, and between the shoulders).</span></span> <span data-ttu-id="82f78-194">使用者必須同時針對動作成功與其本身的舒適度，接受這個辨識範圍的訓練 (許多使用者一開始都假定手勢框架必定在其 HoloLens 視野內，且為了進行互動而不自在地高舉其手臂)。</span><span class="sxs-lookup"><span data-stu-id="82f78-194">Users need to be trained on this area of recognition both for success of action and for their own comfort (many users will initially assume that the gesture frame must be within their view through HoloLens, and hold their arms up uncomfortably in order to interact).</span></span> <span data-ttu-id="82f78-195">使用 HoloLens Clicker 時，您的手不需要在手勢框架內。</span><span class="sxs-lookup"><span data-stu-id="82f78-195">When using the HoloLens Clicker, your hands do not need to be within the gesture frame.</span></span>

<span data-ttu-id="82f78-196">尤其在連續手勢的情況下，在手勢過程 (例如在移動某個全像攝影物件時) 中將手部移出手勢框架的使用者會有些風險，並且會失去其預期的結果。</span><span class="sxs-lookup"><span data-stu-id="82f78-196">In the case of continuous gestures in particular, there is some risk of users moving their hands outside of the gesture frame while in mid-gesture (while moving some holographic object, for example), and losing their intended outcome.</span></span>

<span data-ttu-id="82f78-197">您應該考量下列三個事項：</span><span class="sxs-lookup"><span data-stu-id="82f78-197">There are three things that you should consider:</span></span>
* <span data-ttu-id="82f78-198">教育使用者有關手勢框架的存在性和大約界限 (這在 HoloLens 設定期間教導)。</span><span class="sxs-lookup"><span data-stu-id="82f78-198">User education on the gesture frame's existence and approximate boundaries (this is taught during HoloLens setup).</span></span>
* <span data-ttu-id="82f78-199">當手勢接近/突破應用程式內的手勢框架界限時，通知使用者，因為遺失手勢會導致不想要的結果。</span><span class="sxs-lookup"><span data-stu-id="82f78-199">Notifying users when their gestures are nearing/breaking the gesture frame boundaries within an application, to the degree that a lost gesture will lead to undesired outcomes.</span></span> <span data-ttu-id="82f78-200">研究已顯示這類通知系統的主要品質，而 HoloLens 殼層提供這類型通知的良好範例 (視覺化，位於中央游標，指出發生越界的方向)。</span><span class="sxs-lookup"><span data-stu-id="82f78-200">Research has shown the key qualities of such a notification system, and the HoloLens shell provides a good example of this type of notification (visual, on the central cursor, indicating the direction in which boundary crossing is taking place).</span></span>
* <span data-ttu-id="82f78-201">您應該將突破手勢框架界限的後果最小化。</span><span class="sxs-lookup"><span data-stu-id="82f78-201">Consequences of breaking the gesture frame boundaries should be minimized.</span></span> <span data-ttu-id="82f78-202">一般而言，這表示手勢的結果應止於界限，但不會反轉。</span><span class="sxs-lookup"><span data-stu-id="82f78-202">In general, this means that the outcome of a gesture should be stopped at the boundary, but not reversed.</span></span> <span data-ttu-id="82f78-203">例如，如果使用者要在房間間移動一些全像攝影物件，則當軌跡框架遭到入侵時，移動應該會停止，但**不**會傳回至起始點。</span><span class="sxs-lookup"><span data-stu-id="82f78-203">For example, if a user is moving some holographic object across a room, movement should stop when the gesture frame is breached, but **not** be returned to the starting point.</span></span> <span data-ttu-id="82f78-204">使用者可能遭遇一些挫敗，但可以更快了解界限，而不必每次重新開始其完整的預定動作。</span><span class="sxs-lookup"><span data-stu-id="82f78-204">The user may experience some frustration then, but may more quickly understand the boundaries, and not have to restart their full intended actions each time.</span></span>

## <a name="see-also"></a><span data-ttu-id="82f78-205">請參閱</span><span class="sxs-lookup"><span data-stu-id="82f78-205">See also</span></span>
* [<span data-ttu-id="82f78-206">頭部目光和停駐</span><span class="sxs-lookup"><span data-stu-id="82f78-206">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="82f78-207">語音設計</span><span class="sxs-lookup"><span data-stu-id="82f78-207">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="82f78-208">MR 輸入211：手勢</span><span class="sxs-lookup"><span data-stu-id="82f78-208">MR Input 211: Gesture</span></span>](holograms-211.md)
* [<span data-ttu-id="82f78-209">Unity 中的筆勢和運動控制器</span><span class="sxs-lookup"><span data-stu-id="82f78-209">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="82f78-210">DirectX 中的手部和運動控制器</span><span class="sxs-lookup"><span data-stu-id="82f78-210">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="82f78-211">運動控制器</span><span class="sxs-lookup"><span data-stu-id="82f78-211">Motion controllers</span></span>](motion-controllers.md)
