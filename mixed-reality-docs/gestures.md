---
title: 手勢
description: 手勢允許使用者在混合實境中採取的動作。
author: rwinj
ms.author: cmeekhof
ms.date: 02/24/2019
ms.topic: article
keywords: 混合的實境，手勢互動、 設計
ms.openlocfilehash: 8094caaf8a5d805606e9dac11ece56bc50122e5d
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829767"
---
# <a name="gestures"></a><span data-ttu-id="f0431-104">手勢</span><span class="sxs-lookup"><span data-stu-id="f0431-104">Gestures</span></span>

<span data-ttu-id="f0431-105">手勢允許混合實境中的使用者採取動作。</span><span class="sxs-lookup"><span data-stu-id="f0431-105">Hand gestures allow users take action in mixed reality.</span></span> <span data-ttu-id="f0431-106">互動根據**視線**為目標並**筆勢**或**語音**已針對任何項目採取動作。</span><span class="sxs-lookup"><span data-stu-id="f0431-106">Interaction is built on **gaze** to target and **gesture** or **voice** to act upon whatever element has been targeted.</span></span> <span data-ttu-id="f0431-107">手勢不提供確切的位置中的空間，但置於 HoloLens 和立即與內容互動的簡易性可讓使用者取得運作而不進行任何其他附屬應用程式。</span><span class="sxs-lookup"><span data-stu-id="f0431-107">Hand gestures do not provide a precise location in space, but the simplicity of putting on a HoloLens and immediately interacting with content allows users to get to work without any other accessories.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/kwn9Lh0E_vU]

## <a name="device-support"></a><span data-ttu-id="f0431-108">裝置支援</span><span class="sxs-lookup"><span data-stu-id="f0431-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f0431-109"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="f0431-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="f0431-110"><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="f0431-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="f0431-111"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="f0431-111"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="f0431-112"><a href="immersive-headset-hardware-details.md"><strong>沈浸式耳機</strong></a></span><span class="sxs-lookup"><span data-stu-id="f0431-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f0431-113">手勢</span><span class="sxs-lookup"><span data-stu-id="f0431-113">Gestures</span></span></td>
        <td><span data-ttu-id="f0431-114">✔️</span><span class="sxs-lookup"><span data-stu-id="f0431-114">✔️</span></span></td>
        <td><span data-ttu-id="f0431-115">✔️</span><span class="sxs-lookup"><span data-stu-id="f0431-115">✔️</span></span></td>
        <td><span data-ttu-id="f0431-116">❌</span><span class="sxs-lookup"><span data-stu-id="f0431-116">❌</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f0431-117">相互連貫的指針</span><span class="sxs-lookup"><span data-stu-id="f0431-117">Articulated hands</span></span></td>
        <td><span data-ttu-id="f0431-118">❌</span><span class="sxs-lookup"><span data-stu-id="f0431-118">❌</span></span></td>
        <td><span data-ttu-id="f0431-119">✔️</span><span class="sxs-lookup"><span data-stu-id="f0431-119">✔️</span></span></td>
        <td><span data-ttu-id="f0431-120">❌</span><span class="sxs-lookup"><span data-stu-id="f0431-120">❌</span></span></td>
    </tr>
</table>

> [!NOTE]
> <span data-ttu-id="f0431-121">HoloLens 2 的特定的詳細指引[即將推出](index.md#news-and-notes)。</span><span class="sxs-lookup"><span data-stu-id="f0431-121">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="gaze-and-commit"></a><span data-ttu-id="f0431-122">視線認可</span><span class="sxs-lookup"><span data-stu-id="f0431-122">Gaze-and-commit</span></span>

<span data-ttu-id="f0431-123">若要採取的動作，請送筆勢使用[前端的視線](gaze.md)做為目標的機制。</span><span class="sxs-lookup"><span data-stu-id="f0431-123">To take actions, hand gestures use [head gaze](gaze.md) as the targeting mechanism.</span></span> <span data-ttu-id="f0431-124">組合**視線**並**空中點選**軌跡導致**視線認可**互動。</span><span class="sxs-lookup"><span data-stu-id="f0431-124">The combination of **Gaze** and the **Air tap** gesture results in a **gaze-and-commit** interaction.</span></span> <span data-ttu-id="f0431-125">視線認可的替代方式是**點認可**，藉由已啟用[動作控制器](motion-controllers.md)。</span><span class="sxs-lookup"><span data-stu-id="f0431-125">An alternative to gaze-and-commit is **point-and-commit**, enabled by [motion controllers](motion-controllers.md).</span></span> <span data-ttu-id="f0431-126">HoloLens 執行的應用程式只需要支援視線認可，因為 HoloLens 不支援移動控制站。</span><span class="sxs-lookup"><span data-stu-id="f0431-126">Apps that run on HoloLens only need to support gaze-and-commit since HoloLens does not support motion controllers.</span></span> <span data-ttu-id="f0431-127">HoloLens 和沈浸式耳機執行的應用程式應支援視線驅動和指向導向的互動，讓使用者選擇他們使用何種輸入裝置中。</span><span class="sxs-lookup"><span data-stu-id="f0431-127">Apps that run on both HoloLens and immersive headsets should support both gaze-driven and pointing-driven interactions, to give users choice in what input device they use.</span></span>

## <a name="the-two-core-gestures-of-hololens"></a><span data-ttu-id="f0431-128">這兩個核心的 HoloLens 的筆勢</span><span class="sxs-lookup"><span data-stu-id="f0431-128">The two core gestures of HoloLens</span></span>

<span data-ttu-id="f0431-129">HoloLens 目前可辨識兩個核心元件筆勢-**空中點選**並**Bloom**。</span><span class="sxs-lookup"><span data-stu-id="f0431-129">HoloLens currently recognizes two core component gestures - **Air tap** and **Bloom**.</span></span> <span data-ttu-id="f0431-130">這些兩個核心互動都有空間開發人員可以存取的輸入資料的最低層級。</span><span class="sxs-lookup"><span data-stu-id="f0431-130">These two core interactions are the lowest level of spatial input data that a developer can access.</span></span> <span data-ttu-id="f0431-131">它們形成各種可能的使用者動作的基礎。</span><span class="sxs-lookup"><span data-stu-id="f0431-131">They form the foundation for a variety of possible user actions.</span></span>

### <a name="air-tap"></a><span data-ttu-id="f0431-132">空中點選</span><span class="sxs-lookup"><span data-stu-id="f0431-132">Air tap</span></span>

<span data-ttu-id="f0431-133">空中點選是與手持垂直，類似於按下滑鼠點選手勢，或選取。</span><span class="sxs-lookup"><span data-stu-id="f0431-133">Air tap is a tapping gesture with the hand held upright, similar to a mouse click or select.</span></span> <span data-ttu-id="f0431-134">這用於大部分的 HoloLens 體驗相當於 「 按一下 」 的 UI 元素之後對其具有[視線](gaze.md)。</span><span class="sxs-lookup"><span data-stu-id="f0431-134">This is used in most HoloLens experiences for the equivalent of a "click" on a UI element after targeting it with [Gaze](gaze.md).</span></span> <span data-ttu-id="f0431-135">它是通用的動作，您了解一次，，然後套用到您的所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="f0431-135">It is a universal action that you learn once and then apply across all your apps.</span></span> <span data-ttu-id="f0431-136">若要執行選取的其他方式所按下的單一按鈕[HoloLens Clicker](hardware-accessories.md#hololens-clicker)或透過說話語音命令"Select"。</span><span class="sxs-lookup"><span data-stu-id="f0431-136">Other ways to perform select are by pressing the single button on a [HoloLens Clicker](hardware-accessories.md#hololens-clicker) or by speaking the voice command "Select".</span></span>

<span data-ttu-id="f0431-137">![就緒狀態，以便在 HoloLens 上的手勢](images/image9.png)</span><span class="sxs-lookup"><span data-stu-id="f0431-137">![Ready state for hand gestures on HoloLens](images/image9.png)</span></span><br>
<span data-ttu-id="f0431-138">*空中點選 HoloLens 上的狀態。*</span><span class="sxs-lookup"><span data-stu-id="f0431-138">*Ready state for Air tap on HoloLens.*</span></span>

<span data-ttu-id="f0431-139">空中點選是離散的動作。</span><span class="sxs-lookup"><span data-stu-id="f0431-139">Air tap is a discrete gesture.</span></span> <span data-ttu-id="f0431-140">選取範圍已完成或不是，動作是或不在體驗中取出。</span><span class="sxs-lookup"><span data-stu-id="f0431-140">A selection is either completed or it is not, an action is or is not taken within an experience.</span></span> <span data-ttu-id="f0431-141">可能是，雖然不建議使用而不需要某些特定的目的，若要從主要的元件 （例如點選手勢，以表示點一下以外） 的組合建立其他不連續的筆勢。</span><span class="sxs-lookup"><span data-stu-id="f0431-141">It is possible, though not recommended without some specific purpose, to create other discrete gestures from combinations of the main components (e.g. a double-tap gesture to mean something different than a single-tap).</span></span>

<span data-ttu-id="f0431-142">![在準備好位置，然後點選或按一下 移動手指](images/readyandpress.jpg)</span><span class="sxs-lookup"><span data-stu-id="f0431-142">![Finger in the ready position and then a tap or click motion](images/readyandpress.jpg)</span></span><br>
<span data-ttu-id="f0431-143">*如何執行空中點選：引發食指就緒的位置、 按下點選或選取您的手指和釋放然後備份。*</span><span class="sxs-lookup"><span data-stu-id="f0431-143">*How to perform an Air tap: Raise your index finger to the ready position, press your finger down to tap or select and then back up to release.*</span></span>

### <a name="bloom"></a><span data-ttu-id="f0431-144">Bloom</span><span class="sxs-lookup"><span data-stu-id="f0431-144">Bloom</span></span>

<span data-ttu-id="f0431-145">Bloom 是 「 主要 」 手勢，並保留供，單獨。</span><span class="sxs-lookup"><span data-stu-id="f0431-145">Bloom is the "home" gesture and is reserved for that alone.</span></span> <span data-ttu-id="f0431-146">它是用來返回至 [開始] 功能表的特殊系統動作。</span><span class="sxs-lookup"><span data-stu-id="f0431-146">It is a special system action that is used to go back to the Start Menu.</span></span> <span data-ttu-id="f0431-147">它就相當於按下鍵盤或 Xbox 控制器上的 Xbox 按鈕上的 Windows 鍵。</span><span class="sxs-lookup"><span data-stu-id="f0431-147">It is equivalent to pressing the Windows key on a keyboard or the Xbox button on an Xbox controller.</span></span> <span data-ttu-id="f0431-148">使用者可以使用任一游標。</span><span class="sxs-lookup"><span data-stu-id="f0431-148">The user can use either hand.</span></span>

![HoloLens 上 bloom 筆勢](images/image10-640px.png)

<span data-ttu-id="f0431-150">若要執行 HoloLens 上的 bloom 筆勢，您的手鑑效，掌，使用隨手可得在一起。</span><span class="sxs-lookup"><span data-stu-id="f0431-150">To do the bloom gesture on HoloLens, hold out your hand, palm up, with your fingertips together.</span></span> <span data-ttu-id="f0431-151">然後開啟您的手。</span><span class="sxs-lookup"><span data-stu-id="f0431-151">Then open your hand.</span></span> <span data-ttu-id="f0431-152">請注意，您可以也一律回到開始說 「 嘿 Cortana，移至首頁 」。</span><span class="sxs-lookup"><span data-stu-id="f0431-152">Note, you can also always return to Start by saying "Hey Cortana, Go Home".</span></span> <span data-ttu-id="f0431-153">應用程式無法回應特別首頁的動作，因為這些會由系統處理。</span><span class="sxs-lookup"><span data-stu-id="f0431-153">Apps cannot react specifically to a home action, as these are handled by the system.</span></span>

<span data-ttu-id="f0431-154">![Bloom 筆勢](images/bloom-giphy.gif)</span><span class="sxs-lookup"><span data-stu-id="f0431-154">![Bloom gesture](images/bloom-giphy.gif)</span></span><br>
<span data-ttu-id="f0431-155">*如何執行 bloom 筆勢 HoloLens 上。*</span><span class="sxs-lookup"><span data-stu-id="f0431-155">*How to perform the bloom gesture on HoloLens.*</span></span>

## <a name="composite-gestures"></a><span data-ttu-id="f0431-156">複合的筆勢</span><span class="sxs-lookup"><span data-stu-id="f0431-156">Composite gestures</span></span>

<span data-ttu-id="f0431-157">應用程式，可以識別多個個別的點選。</span><span class="sxs-lookup"><span data-stu-id="f0431-157">Apps can recognize more than just individual taps.</span></span> <span data-ttu-id="f0431-158">結合點選，按住並釋放與左手邊移動，您可以執行更複雜的複合筆勢。</span><span class="sxs-lookup"><span data-stu-id="f0431-158">By combining tap, hold and release with the movement of the hand, more complex composite gestures can be performed.</span></span> <span data-ttu-id="f0431-159">低層級空間輸入資料 （從空中點選和 Bloom） 開發人員可以存取建置這些複合或高階的筆勢。</span><span class="sxs-lookup"><span data-stu-id="f0431-159">These composite or high-level gestures build on the low-level spatial input data (from Air tap and Bloom) that developers have access to.</span></span>

<table>
<tr>
<th> <span data-ttu-id="f0431-160">複合的筆勢</span><span class="sxs-lookup"><span data-stu-id="f0431-160">Composite gesture</span></span></th><th> <span data-ttu-id="f0431-161">如何套用</span><span class="sxs-lookup"><span data-stu-id="f0431-161">How to apply</span></span></th>
</tr><tr>
<td><span data-ttu-id="f0431-162">空中點選</span><span class="sxs-lookup"><span data-stu-id="f0431-162">Air tap</span></span></td><td><span data-ttu-id="f0431-163">空中點選手勢 （以及下列其他筆勢） 只回應特定的點選。</span><span class="sxs-lookup"><span data-stu-id="f0431-163">The Air tap gesture (as well as the other gestures below) reacts only to a specific tap.</span></span> <span data-ttu-id="f0431-164">若要偵測其他點選動作，例如功能表或掌握，您的應用程式必須直接使用兩個主要元件筆勢上一節中所述的較低層級互動。</span><span class="sxs-lookup"><span data-stu-id="f0431-164">To detect other taps, such as Menu or Grasp, your app must directly use the lower-level interactions described in two key component gestures section above.</span></span></td>
</tr><tr>
<td><span data-ttu-id="f0431-165">Tap and hold</span><span class="sxs-lookup"><span data-stu-id="f0431-165">Tap and hold</span></span></td><td><p><span data-ttu-id="f0431-166">保留只維護空中點選向下指位置。</span><span class="sxs-lookup"><span data-stu-id="f0431-166">Hold is simply maintaining the downward finger position of the air tap.</span></span> <span data-ttu-id="f0431-167">空中點選並按住的組合讓各種不同的更複雜&quot;按一下並拖曳&quot;互動結合 arm 挑出的物件，而非啟用它，例如移動或&quot;mousedown&quot;次要的互動，例如顯示操作功能表。</span><span class="sxs-lookup"><span data-stu-id="f0431-167">The combination of air tap and hold allows for a variety of more complex &quot;click and drag&quot; interactions when combined with arm movement such as picking up an object instead of activating it or &quot;mousedown&quot; secondary interactions such as showing a context menu.</span></span></p><p><span data-ttu-id="f0431-168">不過，為使用者設計這個筆勢很容易就能在任何擴充筆勢的過程中放寬他們手 postures 時，應注意。</span><span class="sxs-lookup"><span data-stu-id="f0431-168">Caution should be used when designing for this gesture however, as users can be prone to relaxing their hand postures during the course of any extended gesture.</span></span></p></td>
</tr><tr>
<td><span data-ttu-id="f0431-169">操作</span><span class="sxs-lookup"><span data-stu-id="f0431-169">Manipulation</span></span></td><td><p><span data-ttu-id="f0431-170">操作筆勢可以用來移動、 調整大小或旋轉雷射，當您想回應給使用者的 1:1 全像&#39;s 手動移動。</span><span class="sxs-lookup"><span data-stu-id="f0431-170">Manipulation gestures can be used to move, resize or rotate a hologram when you want the hologram to react 1:1 to the user&#39;s hand movements.</span></span> <span data-ttu-id="f0431-171">這類的 1 對 1 移動的用法之一是讓使用者繪製或繪製世界中。</span><span class="sxs-lookup"><span data-stu-id="f0431-171">One use for such 1:1 movements is to let the user draw or paint in the world.</span></span></p><p><span data-ttu-id="f0431-172">操作筆勢的初始目標應該視線或指向所完成。</span><span class="sxs-lookup"><span data-stu-id="f0431-172">The initial targeting for a manipulation gesture should be done by gaze or pointing.</span></span> <span data-ttu-id="f0431-173">一旦在點選並按住物件的任何操作啟動，然後處理以手動方式移動，讓使用者看著，而這些操作。</span><span class="sxs-lookup"><span data-stu-id="f0431-173">Once the tap and hold starts, any manipulation of the object is then handled by hand movements, freeing the user to look around while they manipulate.</span></span></p></td>
</tr><tr>
<td><span data-ttu-id="f0431-174">巡覽</span><span class="sxs-lookup"><span data-stu-id="f0431-174">Navigation</span></span></td><td><p><span data-ttu-id="f0431-175">瀏覽筆勢的運作方式如同虛擬搖桿，而且可用來瀏覽 UI 的小工具，例如放射狀功能表。</span><span class="sxs-lookup"><span data-stu-id="f0431-175">Navigation gestures operate like a virtual joystick, and can be used to navigate UI widgets, such as radial menus.</span></span> <span data-ttu-id="f0431-176">您點選並按住啟動筆勢，然後移動 您的手在正規化 3D cube 中，以初始按下時。</span><span class="sxs-lookup"><span data-stu-id="f0431-176">You tap and hold to start the gesture and then move your hand within a normalized 3D cube, centered around the initial press.</span></span> <span data-ttu-id="f0431-177">設為 1，其中 0 表示的起始點，您可以從-1 值移動您的手沿著 X、 Y 或 Z 軸。</span><span class="sxs-lookup"><span data-stu-id="f0431-177">You can move your hand along the X, Y or Z axis from a value of -1 to 1, with 0 being the starting point.</span></span></p><p><span data-ttu-id="f0431-178">瀏覽可用來建置速度為基礎連續捲動或縮放筆勢，類似於按一下滑鼠中間按鈕，然後再移動滑鼠向上和向下捲動 2D 的 UI。</span><span class="sxs-lookup"><span data-stu-id="f0431-178">Navigation can be used to build velocity-based continuous scrolling or zooming gestures, similar to scrolling a 2D UI by clicking the middle mouse button and then moving the mouse up and down.</span></span></p><p><span data-ttu-id="f0431-179">巡覽及 rails 指的是辨識特定座標軸內移動，直到該軸上達到特定臨界值。</span><span class="sxs-lookup"><span data-stu-id="f0431-179">Navigation with rails refers to the ability of recognizing movements in certain axis until certain threshold is reached on that axis.</span></span> <span data-ttu-id="f0431-180">這只時很有用，在多個軸中的移動已啟用應用程式中由開發人員，例如應用程式是設定為可辨識之間的瀏覽筆勢，X，Y 軸，但也指定如果 X 軸 rails 使用。</span><span class="sxs-lookup"><span data-stu-id="f0431-180">This is only useful, when movement in more than one axis is enabled in an application by the developer, e.g. if an application is configured to recognize navigation gestures across X, Y axis but also specified X axis with rails.</span></span> <span data-ttu-id="f0431-181">在此情況下系統將會在 X 軸的手移動，只要它們都保留在虛數 rails （輔助線） 在 X 軸，如果辨識手動移動，也會發生 Y 軸。</span><span class="sxs-lookup"><span data-stu-id="f0431-181">In this case system will recognize hand movements across X axis as long as they remain within an imaginary rails (guide) on X axis, if hand movement also occurs Y axis.</span></span></p><p><span data-ttu-id="f0431-182">在 2D 應用程式，使用者可以捲動、 放大，或在應用程式內拖曳使用垂直巡覽筆勢。</span><span class="sxs-lookup"><span data-stu-id="f0431-182">Within 2D apps, users can use vertical navigation gestures to scroll, zoom, or drag inside the app.</span></span> <span data-ttu-id="f0431-183">這會插入虛擬的手指修飾，以模擬觸控筆勢相同類型的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f0431-183">This injects virtual finger touches to the app to simulate touch gestures of the same type.</span></span> <span data-ttu-id="f0431-184">使用者可以選取其中一個這些動作上方應用程式，藉由選取按鈕，或說出的列上的工具之間切換會發生&#39;&lt;捲 /token&gt 拖曳/縮放&gt;工具&#39;。</span><span class="sxs-lookup"><span data-stu-id="f0431-184">Users can select which of these actions take place by toggling between the tools on the bar above the app, either by selecting the button or saying &#39;&lt;Scroll/Drag/Zoom&gt; Tool&#39;.</span></span></p></td>
</tr>
</table>



### <a name="gesture-recognizers"></a><span data-ttu-id="f0431-185">筆勢辨識器</span><span class="sxs-lookup"><span data-stu-id="f0431-185">Gesture recognizers</span></span>

<span data-ttu-id="f0431-186">使用筆勢辨識的其中一個優點是，您可以設定只針對目前的目標全像圖可接受的筆勢筆勢辨識器。</span><span class="sxs-lookup"><span data-stu-id="f0431-186">One benefit of using gesture recognition is that you can configure a gesture recognizer just for the gestures the currently targeted hologram can accept.</span></span> <span data-ttu-id="f0431-187">平台即可只去除混淆為了區分這些特定的支援的筆勢。</span><span class="sxs-lookup"><span data-stu-id="f0431-187">The platform will do only the disambiguation necessary to distinguish those particular supported gestures.</span></span> <span data-ttu-id="f0431-188">如此一來，只支援空中點選全像圖可以接受任何按下及放開之間的時間長度，在全像圖時，支援同時點選並按住可以點選，按住不放以完成後升級保留時間臨界值。</span><span class="sxs-lookup"><span data-stu-id="f0431-188">That way, a hologram that just supports air tap can accept any length of time between press and release, while a hologram that supports both tap and hold can promote the tap to a hold after the hold time threshold.</span></span>

## <a name="hand-recognition"></a><span data-ttu-id="f0431-189">手狀辨識</span><span class="sxs-lookup"><span data-stu-id="f0431-189">Hand recognition</span></span>

<span data-ttu-id="f0431-190">HoloLens 辨識手勢，藉由追蹤或兩個都看得到裝置的實際操作的位置。</span><span class="sxs-lookup"><span data-stu-id="f0431-190">HoloLens recognizes hand gestures by tracking the position of either or both hands that are visible to the device.</span></span> <span data-ttu-id="f0431-191">HoloLens 會看到實際操作的其中一個**就緒狀態**（背面朝您與食指的手） 或**按下狀態**（背面手形朝您食指下）。</span><span class="sxs-lookup"><span data-stu-id="f0431-191">HoloLens sees hands when they are in either the **ready state** (back of the hand facing you with index finger up) or the **pressed state** (back of the hand facing you with the index finger down).</span></span> <span data-ttu-id="f0431-192">當其他會帶來在手，HoloLens 將會忽略它們。</span><span class="sxs-lookup"><span data-stu-id="f0431-192">When hands are in other poses, the HoloLens will ignore them.</span></span>

<span data-ttu-id="f0431-193">針對每一個指針的 HoloLens 偵測，您可以存取它的位置 （不含方向） 和其已按下的狀態。</span><span class="sxs-lookup"><span data-stu-id="f0431-193">For each hand that HoloLens detects, you can access its position (without orientation) and its pressed state.</span></span> <span data-ttu-id="f0431-194">因為手形接近筆勢框架邊緣時，也會提供方向向量，您可以讓他們了解如何移動其手拿回 HoloLens 可以看到顯示給使用者。</span><span class="sxs-lookup"><span data-stu-id="f0431-194">As the hand nears the edge of the gesture frame, you're also provided with a direction vector, which you can show to the user so they know how to move their hand to get it back where HoloLens can see it.</span></span>

## <a name="gesture-frame"></a><span data-ttu-id="f0431-195">筆勢框架</span><span class="sxs-lookup"><span data-stu-id="f0431-195">Gesture frame</span></span>

<span data-ttu-id="f0431-196">手形 HoloLens 上的手勢，必須是"筆勢範圍內"，範圍中之筆勢感應數位相機中所見適當 （非常大約鼻子機身，來回大任之間）。</span><span class="sxs-lookup"><span data-stu-id="f0431-196">For gestures on HoloLens, the hand must be within a “gesture frame”, in a range that the gesture-sensing cameras can see appropriately (very roughly from nose to waist, and between the shoulders).</span></span> <span data-ttu-id="f0431-197">使用者需要辨識動作的成功和自己的緩和 （筆勢框架必須透過 HoloLens、 其檢視內，並保留其手臂 uncomfortably 以便進行互動，則有許多使用者會一開始假設） 的這個區域進行定型。</span><span class="sxs-lookup"><span data-stu-id="f0431-197">Users need to be trained on this area of recognition both for success of action and for their own comfort (many users will initially assume that the gesture frame must be within their view through HoloLens, and hold their arms up uncomfortably in order to interact).</span></span> <span data-ttu-id="f0431-198">當使用 HoloLens Clicker，雙手不需要筆勢框架內。</span><span class="sxs-lookup"><span data-stu-id="f0431-198">When using the HoloLens Clicker, your hands do not need to be within the gesture frame.</span></span>

<span data-ttu-id="f0431-199">在連續的筆勢的情況下特別的是，會有些風險的使用者移動板中間的筆勢 （例如移動某個全像攝影版的物件） 時中的筆勢框架外部，並會遺失其預期的結果。</span><span class="sxs-lookup"><span data-stu-id="f0431-199">In the case of continuous gestures in particular, there is some risk of users moving their hands outside of the gesture frame while in mid-gesture (while moving some holographic object, for example), and losing their intended outcome.</span></span>

<span data-ttu-id="f0431-200">有三個您應該考慮的事項：</span><span class="sxs-lookup"><span data-stu-id="f0431-200">There are three things that you should consider:</span></span>
* <span data-ttu-id="f0431-201">使用者教育筆勢畫面格的存在和大約界限 （這教授 HoloLens 安裝期間）。</span><span class="sxs-lookup"><span data-stu-id="f0431-201">User education on the gesture frame's existence and approximate boundaries (this is taught during HoloLens setup).</span></span>
* <span data-ttu-id="f0431-202">當其筆勢是接近/重大筆勢框架界限，應用程式內，不想要的結果會導致遺失的筆勢的程度，請通知使用者。</span><span class="sxs-lookup"><span data-stu-id="f0431-202">Notifying users when their gestures are nearing/breaking the gesture frame boundaries within an application, to the degree that a lost gesture will lead to undesired outcomes.</span></span> <span data-ttu-id="f0431-203">研究顯示的這類通知系統中，索引鍵的品質和 HoloLens 殼層提供這種類型的通知 （視覺效果，集中的資料指標，指出哪一個界限中跨越正在進行的方向） 的良好範例。</span><span class="sxs-lookup"><span data-stu-id="f0431-203">Research has shown the key qualities of such a notification system, and the HoloLens shell provides a good example of this type of notification (visual, on the central cursor, indicating the direction in which boundary crossing is taking place).</span></span>
* <span data-ttu-id="f0431-204">中斷筆勢框架界限的結果應該降到最低。</span><span class="sxs-lookup"><span data-stu-id="f0431-204">Consequences of breaking the gesture frame boundaries should be minimized.</span></span> <span data-ttu-id="f0431-205">一般情況下，這表示應該停止的界限上，動作的結果，但不是會反轉。</span><span class="sxs-lookup"><span data-stu-id="f0431-205">In general, this means that the outcome of a gesture should be stopped at the boundary, but not reversed.</span></span> <span data-ttu-id="f0431-206">例如，如果使用者移動一些全像攝影版的物件之間的空間，移動時，應該停止的筆勢框架遭到入侵，但**不**傳回給起始點。</span><span class="sxs-lookup"><span data-stu-id="f0431-206">For example, if a user is moving some holographic object across a room, movement should stop when the gesture frame is breached, but **not** be returned to the starting point.</span></span> <span data-ttu-id="f0431-207">使用者可能會遇到一些挫折然後，但可能更快速地了解界限，並不需要每次重新啟動其完整的預定的動作。</span><span class="sxs-lookup"><span data-stu-id="f0431-207">The user may experience some frustration then, but may more quickly understand the boundaries, and not have to restart their full intended actions each time.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0431-208">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0431-208">See also</span></span>
* [<span data-ttu-id="f0431-209">頭部目光和停駐</span><span class="sxs-lookup"><span data-stu-id="f0431-209">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="f0431-210">語音設計</span><span class="sxs-lookup"><span data-stu-id="f0431-210">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="f0431-211">MR Input 211：筆勢</span><span class="sxs-lookup"><span data-stu-id="f0431-211">MR Input 211: Gesture</span></span>](holograms-211.md)
* [<span data-ttu-id="f0431-212">Unity 中的筆勢和運動控制器</span><span class="sxs-lookup"><span data-stu-id="f0431-212">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="f0431-213">DirectX 中的手部和運動控制器</span><span class="sxs-lookup"><span data-stu-id="f0431-213">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="f0431-214">運動控制器</span><span class="sxs-lookup"><span data-stu-id="f0431-214">Motion controllers</span></span>](motion-controllers.md)
