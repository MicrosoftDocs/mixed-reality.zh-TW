---
title: Unity 中的手勢和運動控制器
description: 有兩種主要方式可對您在 Unity、右手手勢和動作控制器的注視採取動作。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 手勢，動作控制器，unity，注視，輸入
ms.openlocfilehash: a85797bfb443f33147c116e90a02c88abda63c67
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926568"
---
# <a name="gestures-and-motion-controllers-in-unity"></a><span data-ttu-id="a993e-104">Unity 中的手勢和運動控制器</span><span class="sxs-lookup"><span data-stu-id="a993e-104">Gestures and motion controllers in Unity</span></span>

<span data-ttu-id="a993e-105">有兩個主要的方式可[對您的](gaze-in-unity.md)目光採取行動，包括 HoloLens 和沉浸式 HMD 中的[右手手勢](gaze-and-commit.md#composite-gestures)和[運動控制器](motion-controllers.md)。</span><span class="sxs-lookup"><span data-stu-id="a993e-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](gaze-and-commit.md#composite-gestures) and [motion controllers](motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="a993e-106">您可以透過 Unity 中的相同 Api，存取這兩個空間輸入來源的資料。</span><span class="sxs-lookup"><span data-stu-id="a993e-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="a993e-107">Unity 提供兩種主要方式來存取適用于 Windows Mixed Reality 的空間輸入資料、共同的*GetButton/GetAxis* api，可跨多個 Unity XR sdk 執行，以及特定的*InteractionManager/GestureRecognizer* apiWindows Mixed Reality，會公開可用的完整空間輸入資料集。</span><span class="sxs-lookup"><span data-stu-id="a993e-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality, the common *Input.GetButton/Input.GetAxis* APIs that work across multiple Unity XR SDKs, and an *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality that exposes the full set of spatial input data available.</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="a993e-108">Unity 按鈕/軸對應表</span><span class="sxs-lookup"><span data-stu-id="a993e-108">Unity button/axis mapping table</span></span>

<span data-ttu-id="a993e-109">在 Windows Mixed Reality 運動控制器的 Unity 輸入管理員中，透過*GetButton/GetAxis* api 支援下表中的按鈕和軸識別碼，而「windows MR-特定」資料行則是指可從下列位置取得的屬性：*InteractionSourceState*類型。</span><span class="sxs-lookup"><span data-stu-id="a993e-109">The button and axis IDs in the table below are supported in Unity's Input Manager for Windows Mixed Reality motion controllers through the *Input.GetButton/GetAxis* APIs, while the "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="a993e-110">下列各節將詳細說明每個 Api。</span><span class="sxs-lookup"><span data-stu-id="a993e-110">Each of these APIs are described in detail in the sections below.</span></span>

<span data-ttu-id="a993e-111">Windows Mixed Reality 的按鈕/軸識別碼對應通常符合 Oculus go 按鈕/軸識別碼。</span><span class="sxs-lookup"><span data-stu-id="a993e-111">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="a993e-112">Windows Mixed Reality 的按鈕/軸識別碼對應與 OpenVR 的對應有兩種不同之處：</span><span class="sxs-lookup"><span data-stu-id="a993e-112">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="a993e-113">對應會使用與操縱杆不同的觸控板識別碼，以支援具有 thumbsticks 和 touchpads 的控制器。</span><span class="sxs-lookup"><span data-stu-id="a993e-113">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="a993e-114">對應可避免將功能表按鈕的 A 和 X 按鈕識別碼多載，讓實體的 ABXY 按鈕可以使用。</span><span class="sxs-lookup"><span data-stu-id="a993e-114">The mapping avoids overloading the A and X button IDs for the Menu buttons, to leave those available for physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="a993e-115">Input</span><span class="sxs-lookup"><span data-stu-id="a993e-115">Input</span></span> </th><th colspan="2"><span data-ttu-id="a993e-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">通用 Unity Api</a></span><span class="sxs-lookup"><span data-stu-id="a993e-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="a993e-117">（輸入. GetButton/GetAxis）</span><span class="sxs-lookup"><span data-stu-id="a993e-117">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="a993e-118"><a href="gestures-and-motion-controllers-in-unity.md#">Windows MR 特有的輸入 API</a></span><span class="sxs-lookup"><span data-stu-id="a993e-118"><a href="gestures-and-motion-controllers-in-unity.md#">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="a993e-119">XR.WSA.源</span><span class="sxs-lookup"><span data-stu-id="a993e-119">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="a993e-120">左手</span><span class="sxs-lookup"><span data-stu-id="a993e-120">Left hand</span></span> </th><th> <span data-ttu-id="a993e-121">右手</span><span class="sxs-lookup"><span data-stu-id="a993e-121">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="a993e-122">已按下選取觸發程式</span><span class="sxs-lookup"><span data-stu-id="a993e-122">Select trigger pressed</span></span> </td><td> <span data-ttu-id="a993e-123">軸 9 = 1。0</span><span class="sxs-lookup"><span data-stu-id="a993e-123">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="a993e-124">軸 10 = 1。0</span><span class="sxs-lookup"><span data-stu-id="a993e-124">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="a993e-125">selectPressed</span><span class="sxs-lookup"><span data-stu-id="a993e-125">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a993e-126">選取觸發程式類比值</span><span class="sxs-lookup"><span data-stu-id="a993e-126">Select trigger analog value</span></span> </td><td> <span data-ttu-id="a993e-127">軸9</span><span class="sxs-lookup"><span data-stu-id="a993e-127">Axis 9</span></span> </td><td> <span data-ttu-id="a993e-128">軸10</span><span class="sxs-lookup"><span data-stu-id="a993e-128">Axis 10</span></span> </td><td> <span data-ttu-id="a993e-129">selectPressedAmount</span><span class="sxs-lookup"><span data-stu-id="a993e-129">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a993e-130">選取 [觸發部分已按下]</span><span class="sxs-lookup"><span data-stu-id="a993e-130">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="a993e-131">按鈕 14 <i>（遊戲台相容性）</i> </span><span class="sxs-lookup"><span data-stu-id="a993e-131">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="a993e-132">按鈕 15 <i>（遊戲台相容性）</i> </span><span class="sxs-lookup"><span data-stu-id="a993e-132">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="a993e-133">selectPressedAmount &gt; 0。0</span><span class="sxs-lookup"><span data-stu-id="a993e-133">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a993e-134">已按下功能表按鈕</span><span class="sxs-lookup"><span data-stu-id="a993e-134">Menu button pressed</span></span> </td><td> <span data-ttu-id="a993e-135">按鈕 6 \*</span><span class="sxs-lookup"><span data-stu-id="a993e-135">Button 6\*</span></span> </td><td> <span data-ttu-id="a993e-136">按鈕 7 \*</span><span class="sxs-lookup"><span data-stu-id="a993e-136">Button 7\*</span></span> </td><td> <span data-ttu-id="a993e-137">menuPressed</span><span class="sxs-lookup"><span data-stu-id="a993e-137">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a993e-138">已按下手柄按鈕</span><span class="sxs-lookup"><span data-stu-id="a993e-138">Grip button pressed</span></span> </td><td> <span data-ttu-id="a993e-139">軸 11 = 1.0 （沒有類比值）</span><span class="sxs-lookup"><span data-stu-id="a993e-139">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="a993e-140">按鈕 4 <i>（遊戲台相容性）</i> </span><span class="sxs-lookup"><span data-stu-id="a993e-140">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="a993e-141">軸 12 = 1.0 （沒有類比值）</span><span class="sxs-lookup"><span data-stu-id="a993e-141">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="a993e-142">按鈕 5 <i>（遊戲台相容性）</i> </span><span class="sxs-lookup"><span data-stu-id="a993e-142">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="a993e-143">grasped</span><span class="sxs-lookup"><span data-stu-id="a993e-143">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a993e-144">操縱杆 X <i>（左：-1.0，右：1.0）</i> </span><span class="sxs-lookup"><span data-stu-id="a993e-144">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="a993e-145">軸1</span><span class="sxs-lookup"><span data-stu-id="a993e-145">Axis 1</span></span> </td><td> <span data-ttu-id="a993e-146">軸4</span><span class="sxs-lookup"><span data-stu-id="a993e-146">Axis 4</span></span> </td><td> <span data-ttu-id="a993e-147">thumbstickPosition. x</span><span class="sxs-lookup"><span data-stu-id="a993e-147">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a993e-148">操縱杆 Y <i>（上：-1.0，下：1.0）</i> </span><span class="sxs-lookup"><span data-stu-id="a993e-148">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="a993e-149">軸2</span><span class="sxs-lookup"><span data-stu-id="a993e-149">Axis 2</span></span> </td><td> <span data-ttu-id="a993e-150">軸5</span><span class="sxs-lookup"><span data-stu-id="a993e-150">Axis 5</span></span> </td><td> <span data-ttu-id="a993e-151">thumbstickPosition. y</span><span class="sxs-lookup"><span data-stu-id="a993e-151">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a993e-152">已按下操縱杆</span><span class="sxs-lookup"><span data-stu-id="a993e-152">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="a993e-153">按鈕8</span><span class="sxs-lookup"><span data-stu-id="a993e-153">Button 8</span></span> </td><td> <span data-ttu-id="a993e-154">按鈕9</span><span class="sxs-lookup"><span data-stu-id="a993e-154">Button 9</span></span> </td><td> <span data-ttu-id="a993e-155">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="a993e-155">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a993e-156">觸達 X <i>（左：-1.0，右：1.0）</i> </span><span class="sxs-lookup"><span data-stu-id="a993e-156">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="a993e-157">軸 17 \*</span><span class="sxs-lookup"><span data-stu-id="a993e-157">Axis 17\*</span></span> </td><td> <span data-ttu-id="a993e-158">軸 19 \*</span><span class="sxs-lookup"><span data-stu-id="a993e-158">Axis 19\*</span></span> </td><td> <span data-ttu-id="a993e-159">touchpadPosition. x</span><span class="sxs-lookup"><span data-stu-id="a993e-159">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a993e-160">觸控板 Y <i>（上方：-1.0、下：1.0）</i> </span><span class="sxs-lookup"><span data-stu-id="a993e-160">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="a993e-161">軸 18 \*</span><span class="sxs-lookup"><span data-stu-id="a993e-161">Axis 18\*</span></span> </td><td> <span data-ttu-id="a993e-162">軸 20 \*</span><span class="sxs-lookup"><span data-stu-id="a993e-162">Axis 20\*</span></span> </td><td> <span data-ttu-id="a993e-163">touchpadPosition. y</span><span class="sxs-lookup"><span data-stu-id="a993e-163">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a993e-164">觸及觸控板</span><span class="sxs-lookup"><span data-stu-id="a993e-164">Touchpad touched</span></span> </td><td> <span data-ttu-id="a993e-165">按鈕 18 \*</span><span class="sxs-lookup"><span data-stu-id="a993e-165">Button 18\*</span></span> </td><td> <span data-ttu-id="a993e-166">按鈕 19 \*</span><span class="sxs-lookup"><span data-stu-id="a993e-166">Button 19\*</span></span> </td><td> <span data-ttu-id="a993e-167">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="a993e-167">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a993e-168">已按下觸控板</span><span class="sxs-lookup"><span data-stu-id="a993e-168">Touchpad pressed</span></span> </td><td> <span data-ttu-id="a993e-169">按鈕 16 \*</span><span class="sxs-lookup"><span data-stu-id="a993e-169">Button 16\*</span></span> </td><td> <span data-ttu-id="a993e-170">按鈕 17 \*</span><span class="sxs-lookup"><span data-stu-id="a993e-170">Button 17\*</span></span> </td><td> <span data-ttu-id="a993e-171">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="a993e-171">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a993e-172">6DoF 底框姿勢或指標姿勢</span><span class="sxs-lookup"><span data-stu-id="a993e-172">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="a993e-173">僅限<i>握</i>姿勢： <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR。InputTracking. GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="a993e-173"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="a993e-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="a993e-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="a993e-175">傳遞<i>手柄</i>或<i>指標</i>做為引數： SourceState. sourcePose. TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="a993e-175">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="a993e-176">sourceState.sourcePose.TryGetRotation</span><span class="sxs-lookup"><span data-stu-id="a993e-176">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="a993e-177">追蹤狀態</span><span class="sxs-lookup"><span data-stu-id="a993e-177">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="a993e-178"><i>位置精確度和來源遺失風險僅可透過 MR 特定 API</i>取得 </span><span class="sxs-lookup"><span data-stu-id="a993e-178"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="a993e-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span><span class="sxs-lookup"><span data-stu-id="a993e-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="a993e-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState. properties. sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="a993e-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="a993e-181">這些按鈕/軸識別碼與 Unity 用於 OpenVR 的識別碼不同，因為遊戲台、Oculus go Touch 和 OpenVR 所使用的對應發生衝突。</span><span class="sxs-lookup"><span data-stu-id="a993e-181">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="a993e-182">抓握姿勢與指標姿勢</span><span class="sxs-lookup"><span data-stu-id="a993e-182">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="a993e-183">Windows Mixed Reality 支援各種外型規格中的動作控制器，而每個控制器的設計都不同于使用者的手位置與自然「正向」方向之間的關聯性，應用程式應該在呈現時使用指標控制器.</span><span class="sxs-lookup"><span data-stu-id="a993e-183">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="a993e-184">為了更清楚地表示這些控制站，您可以針對每個互動來源來調查兩種類型的姿勢，**抓住姿勢**和**指標姿勢**。</span><span class="sxs-lookup"><span data-stu-id="a993e-184">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="a993e-185">「手柄姿勢」和「指標姿勢」座標都會以全域 Unity 全局座標中的所有 Unity Api 表示。</span><span class="sxs-lookup"><span data-stu-id="a993e-185">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="a993e-186">抓握姿勢</span><span class="sxs-lookup"><span data-stu-id="a993e-186">Grip pose</span></span>

<span data-ttu-id="a993e-187">「**抓握姿勢**」代表 HoloLens 偵測到的掌上的位置，或用來存放運動控制器的 palm。</span><span class="sxs-lookup"><span data-stu-id="a993e-187">The **grip pose** represents the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>

<span data-ttu-id="a993e-188">在沉浸式耳機上，抓握姿勢最適合用來**轉譯使用者手**或**使用者手中所持有的物件**，例如寶劍或機槍。</span><span class="sxs-lookup"><span data-stu-id="a993e-188">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span> <span data-ttu-id="a993e-189">當視覺化動作控制器時，也會使用「底框姿勢」，因為適用于動作控制器的 Windows 所提供的**呈現模型**會使用「手柄姿勢」作為其原點和旋轉中心。</span><span class="sxs-lookup"><span data-stu-id="a993e-189">The grip pose is also used when visualizing a motion controller, as the **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="a993e-190">抓握姿勢的定義方式如下：</span><span class="sxs-lookup"><span data-stu-id="a993e-190">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="a993e-191">**抓握位置**：以自然的來保存控制器時的 palm 距心，向左或右調整以置中的位置。</span><span class="sxs-lookup"><span data-stu-id="a993e-191">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="a993e-192">在 Windows Mixed Reality 動作控制器上，此位置通常會與 [抓住] 按鈕對齊。</span><span class="sxs-lookup"><span data-stu-id="a993e-192">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="a993e-193">**抓握方向的右軸**：當您完全開啟手來形成一般的5方姿勢時，您的掌上的光線（從左 palm 向前、向右的 palm）</span><span class="sxs-lookup"><span data-stu-id="a993e-193">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="a993e-194">**抓握方向的正向軸**：當您局部關閉手（如同按住控制器）時，會透過非拇指手指所形成的電子管「轉寄」光線。</span><span class="sxs-lookup"><span data-stu-id="a993e-194">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="a993e-195">**抓握方向的向上軸**：右邊和後向定義所隱含的向上軸。</span><span class="sxs-lookup"><span data-stu-id="a993e-195">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="a993e-196">您可以透過 Unity 的跨廠商輸入 API （XR）來存取底框姿勢 *[。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/輪替*），或透過 WINDOWS MR 特定 API （*SourceState. SourcePose. TryGetPosition/輪替*，要求「底框 **」節點的**姿勢資料）。</span><span class="sxs-lookup"><span data-stu-id="a993e-196">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="a993e-197">指標姿勢</span><span class="sxs-lookup"><span data-stu-id="a993e-197">Pointer pose</span></span>

<span data-ttu-id="a993e-198">**指標姿勢**代表指向轉寄的控制器秘訣。</span><span class="sxs-lookup"><span data-stu-id="a993e-198">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="a993e-199">當您**呈現控制器模型本身**時，系統提供的指標姿勢最適合用來 raycast。</span><span class="sxs-lookup"><span data-stu-id="a993e-199">The system-provided pointer pose is best used to raycast when you are **rendering the controller model itself**.</span></span> <span data-ttu-id="a993e-200">如果您要呈現某個其他虛擬物件來取代控制器（例如虛擬機器槍），您應該指向該虛擬物件最自然的光線，例如沿著應用程式定義的機槍模型的桶移動的光線。</span><span class="sxs-lookup"><span data-stu-id="a993e-200">If you are rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that is most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="a993e-201">由於使用者可以看到虛擬物件，而不是實體控制器，因此使用您的應用程式時，指向虛擬物件的方式可能會更自然。</span><span class="sxs-lookup"><span data-stu-id="a993e-201">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="a993e-202">目前，指標姿勢僅適用于 Unity 中的 Windows MR 特定 API *sourcePose. TryGetPosition/輪替*，傳入*InteractionSourceNode*做為引數。</span><span class="sxs-lookup"><span data-stu-id="a993e-202">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="a993e-203">控制器追蹤狀態</span><span class="sxs-lookup"><span data-stu-id="a993e-203">Controller tracking state</span></span>

<span data-ttu-id="a993e-204">就像耳機一樣，Windows Mixed Reality 運動控制器不需要設定外部追蹤感應器。</span><span class="sxs-lookup"><span data-stu-id="a993e-204">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="a993e-205">而是由耳機本身的感應器來追蹤控制器。</span><span class="sxs-lookup"><span data-stu-id="a993e-205">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="a993e-206">如果使用者將控制器移出頭戴式裝置的視野，在大部分情況下，Windows 會繼續推斷控制器位置並提供給應用程式。</span><span class="sxs-lookup"><span data-stu-id="a993e-206">If the user moves the controllers out of the headset's field of view, in most cases Windows will continue to infer controller positions and provide them to the app.</span></span> <span data-ttu-id="a993e-207">當控制器已夠長的視覺效果追蹤時，控制器的位置將會降到近似的精確度位置。</span><span class="sxs-lookup"><span data-stu-id="a993e-207">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="a993e-208">此時，系統會將控制器鎖定給使用者，並在移動時追蹤使用者的位置，同時仍然使用其內部方向感應器來公開控制器的真正方向。</span><span class="sxs-lookup"><span data-stu-id="a993e-208">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="a993e-209">許多使用控制器來指向並啟動 UI 元素的應用程式，都可以正常運作，但不會察覺到使用者的精確度。</span><span class="sxs-lookup"><span data-stu-id="a993e-209">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="a993e-210">瞭解這一點的最佳方式，就是親自試試看。</span><span class="sxs-lookup"><span data-stu-id="a993e-210">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="a993e-211">請參閱這段影片，其中包含可在各種追蹤狀態下搭配運動控制器使用的沉浸式內容範例：</span><span class="sxs-lookup"><span data-stu-id="a993e-211">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="a993e-212">明確追蹤狀態的推理</span><span class="sxs-lookup"><span data-stu-id="a993e-212">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="a993e-213">如果應用程式想要根據追蹤狀態以不同的方式來處理位置，可能會進一步進行，並檢查控制器狀態的屬性，例如*SourceLossRisk*和*PositionAccuracy*：</span><span class="sxs-lookup"><span data-stu-id="a993e-213">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="a993e-214">追蹤狀態</span><span class="sxs-lookup"><span data-stu-id="a993e-214">Tracking state</span></span> </th><th> <span data-ttu-id="a993e-215">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="a993e-215">SourceLossRisk</span></span> </th><th> <span data-ttu-id="a993e-216">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="a993e-216">PositionAccuracy</span></span> </th><th> <span data-ttu-id="a993e-217">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="a993e-217">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="a993e-218"><b>高準確度</b> </span><span class="sxs-lookup"><span data-stu-id="a993e-218"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="a993e-219">&lt; 1。0</span><span class="sxs-lookup"><span data-stu-id="a993e-219">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="a993e-220">[高]</span><span class="sxs-lookup"><span data-stu-id="a993e-220">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="a993e-221">true</span><span class="sxs-lookup"><span data-stu-id="a993e-221">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a993e-222"><b>高精確度（有遺失的風險）</b> </span><span class="sxs-lookup"><span data-stu-id="a993e-222"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="a993e-223">= = 1。0</span><span class="sxs-lookup"><span data-stu-id="a993e-223">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="a993e-224">[高]</span><span class="sxs-lookup"><span data-stu-id="a993e-224">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="a993e-225">true</span><span class="sxs-lookup"><span data-stu-id="a993e-225">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a993e-226"><b>估計精確度</b> </span><span class="sxs-lookup"><span data-stu-id="a993e-226"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="a993e-227">= = 1。0</span><span class="sxs-lookup"><span data-stu-id="a993e-227">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="a993e-228">大約</span><span class="sxs-lookup"><span data-stu-id="a993e-228">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="a993e-229">true</span><span class="sxs-lookup"><span data-stu-id="a993e-229">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a993e-230"><b>沒有位置</b> </span><span class="sxs-lookup"><span data-stu-id="a993e-230"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="a993e-231">= = 1。0</span><span class="sxs-lookup"><span data-stu-id="a993e-231">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="a993e-232">大約</span><span class="sxs-lookup"><span data-stu-id="a993e-232">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="a993e-233">false</span><span class="sxs-lookup"><span data-stu-id="a993e-233">false</span></span></td>
</tr>
</table>

<span data-ttu-id="a993e-234">這些動作控制器的追蹤狀態定義如下：</span><span class="sxs-lookup"><span data-stu-id="a993e-234">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="a993e-235">**高精確度：** 雖然動作控制器是在耳機的視野中，但它通常會根據視覺效果追蹤來提供高精確度的位置。</span><span class="sxs-lookup"><span data-stu-id="a993e-235">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="a993e-236">請注意，移動控制器會暫時離開此欄位，或從耳機感應器暫時遮蔽（例如，使用者的另一方面），會根據控制站的慣性追蹤，以較短的時間繼續傳回高準確度的姿勢直接.</span><span class="sxs-lookup"><span data-stu-id="a993e-236">Note that a moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="a993e-237">**高精確度（有遺失的風險）：** 當使用者將動作控制器移到耳機的視野邊緣上方時，耳機很快就無法以視覺方式追蹤控制器的位置。</span><span class="sxs-lookup"><span data-stu-id="a993e-237">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="a993e-238">應用程式會透過看到**SourceLossRisk**觸達1.0，得知控制器已達到此 FOV 界限。</span><span class="sxs-lookup"><span data-stu-id="a993e-238">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="a993e-239">此時，應用程式可能會選擇暫停需要穩定串流高品質姿勢的控制器手勢。</span><span class="sxs-lookup"><span data-stu-id="a993e-239">At that point, the app may choose to pause controller gestures that require a steady stream of very high-quality poses.</span></span>
* <span data-ttu-id="a993e-240">**估計精確度：** 當控制器已夠長的視覺效果追蹤時，控制器的位置將會降到近似的精確度位置。</span><span class="sxs-lookup"><span data-stu-id="a993e-240">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="a993e-241">此時，系統會將控制器鎖定給使用者，並在移動時追蹤使用者的位置，同時仍然使用其內部方向感應器來公開控制器的真正方向。</span><span class="sxs-lookup"><span data-stu-id="a993e-241">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="a993e-242">許多使用控制器來指向並啟動 UI 元素的應用程式，都可以正常運作，而不會察覺到使用者注意到的精確度。</span><span class="sxs-lookup"><span data-stu-id="a993e-242">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="a993e-243">具有較**高**輸入需求的應用程式可能會選擇透過檢查**PositionAccuracy**屬性（例如，讓使用者在螢幕上的目標上有更大的 Hitbox），從高度準確度中瞭解這項下降**的準確度。** 在這段期間內。</span><span class="sxs-lookup"><span data-stu-id="a993e-243">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="a993e-244">**沒有位置：** 雖然控制器可以在大概的精確度內正常運作，但有時系統會知道即使是主體鎖定的位置也不會有意義。</span><span class="sxs-lookup"><span data-stu-id="a993e-244">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position is not meaningful at the moment.</span></span> <span data-ttu-id="a993e-245">例如，剛開啟的控制器可能從未以視覺化方式觀察到，或使用者可能會關閉某個控制器，然後由其他人挑選。</span><span class="sxs-lookup"><span data-stu-id="a993e-245">For example, a controller that was just turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="a993e-246">在這些時間，系統不會提供任何位置給應用程式，而且*TryGetPosition*會傳回 false。</span><span class="sxs-lookup"><span data-stu-id="a993e-246">At those times, the system will not provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="a993e-247">通用 Unity Api （輸入. GetButton/GetAxis）</span><span class="sxs-lookup"><span data-stu-id="a993e-247">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="a993e-248">**命名空間：** *UnityEngine*、 *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="a993e-248">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="a993e-249">**類型**： *Input*、 *XR。InputTracking*</span><span class="sxs-lookup"><span data-stu-id="a993e-249">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="a993e-250">Unity 目前使用其一般*輸入 GetButton/GetAxis* api 來公開[Oculus go SDK](https://docs.unity3d.com/Manual/OculusControllers.html)、 [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)和 Windows Mixed Reality 的輸入，包括手和運動控制器。</span><span class="sxs-lookup"><span data-stu-id="a993e-250">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="a993e-251">如果您的應用程式使用這些 Api 來進行輸入，它可以輕鬆地支援跨多個 XR Sdk 的運動控制器，包括 Windows Mixed Reality。</span><span class="sxs-lookup"><span data-stu-id="a993e-251">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="a993e-252">取得邏輯按鈕的已按下狀態</span><span class="sxs-lookup"><span data-stu-id="a993e-252">Getting a logical button's pressed state</span></span>

<span data-ttu-id="a993e-253">若要使用一般 Unity 輸入 Api，您通常會先將按鈕和軸連接到[Unity 輸入管理員](https://docs.unity3d.com/Manual/ConventionalGameInput.html)中的邏輯名稱，並將按鈕或軸識別碼系結至每個名稱。</span><span class="sxs-lookup"><span data-stu-id="a993e-253">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="a993e-254">接著，您可以撰寫參考該邏輯按鈕/軸名稱的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a993e-254">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="a993e-255">例如，若要將左側動作控制器的 [觸發程式] 按鈕對應至 [提交] 動作，請移至 [**編輯] > [專案設定] >** Unity 內的輸入，然後展開 [軸] 底下 [提交] 區段的屬性。</span><span class="sxs-lookup"><span data-stu-id="a993e-255">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="a993e-256">將**正按鈕**或**Alt 正按鈕**屬性變更為閱讀**搖桿按鈕 14**，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a993e-256">Change the **Positive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="a993e-257">![Unity 的 InputManager](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="a993e-257">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="a993e-258">*Unity InputManager*</span><span class="sxs-lookup"><span data-stu-id="a993e-258">*Unity InputManager*</span></span>

<span data-ttu-id="a993e-259">接著，您的腳本可以使用*GetButton*檢查提交動作：</span><span class="sxs-lookup"><span data-stu-id="a993e-259">Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="a993e-260">您可以藉由變更 [**軸**] 底下的 [**大小**] 屬性來新增更多邏輯按鈕。</span><span class="sxs-lookup"><span data-stu-id="a993e-260">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="a993e-261">直接取得實體按鈕的已按下狀態</span><span class="sxs-lookup"><span data-stu-id="a993e-261">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="a993e-262">您也可以使用*GetKey*，以其完整名稱來手動存取按鈕：</span><span class="sxs-lookup"><span data-stu-id="a993e-262">You can also access buttons manually by their fully-qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="a993e-263">取得手或運動控制器的姿勢</span><span class="sxs-lookup"><span data-stu-id="a993e-263">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="a993e-264">您可以使用 XR 來存取控制器的位置和旋轉 *。InputTracking*：</span><span class="sxs-lookup"><span data-stu-id="a993e-264">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

<span data-ttu-id="a993e-265">請注意，這代表控制器的底框姿勢（使用者保有控制器的位置），這適用于在使用者手中呈現寶劍或機槍，或控制器本身的模型。</span><span class="sxs-lookup"><span data-stu-id="a993e-265">Note that this represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>

<span data-ttu-id="a993e-266">請注意，此底框和指標（控制器的秘訣指向的位置）之間的關聯性可能會在不同的控制器之間有所不同。</span><span class="sxs-lookup"><span data-stu-id="a993e-266">Note that the relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="a993e-267">目前，只有透過 MR 特定的輸入 API （如下列各節所述），才可以存取控制器的指標姿勢。</span><span class="sxs-lookup"><span data-stu-id="a993e-267">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="a993e-268">Windows 特定的 Api （XR。WSA.源</span><span class="sxs-lookup"><span data-stu-id="a993e-268">Windows-specific APIs (XR.WSA.Input)</span></span>

<span data-ttu-id="a993e-269">**命名空間：** *UnityEngine. XR. WSA. 輸入*</span><span class="sxs-lookup"><span data-stu-id="a993e-269">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="a993e-270">**類型**： *InteractionManager*、 *InteractionSourceState*、 *InteractionSource*、 *InteractionSourceProperties*、 *InteractionSourceKind*、 *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="a993e-270">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="a993e-271">若要取得有關 Windows Mixed Reality 手寫輸入（適用于 HoloLens）和動作控制器的更詳細資訊，您可以選擇使用*UnityEngine. XR*命名空間下的 windows 特定空間輸入 api。</span><span class="sxs-lookup"><span data-stu-id="a993e-271">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="a993e-272">這可讓您存取其他資訊，例如位置精確度或來源種類，讓您可以讓手和控制器分開。</span><span class="sxs-lookup"><span data-stu-id="a993e-272">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="a993e-273">輪詢實習和運動控制器的狀態</span><span class="sxs-lookup"><span data-stu-id="a993e-273">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="a993e-274">您可以使用*GetCurrentReading*方法，針對每個互動來源（手或動作控制器）輪詢此畫面格的狀態。</span><span class="sxs-lookup"><span data-stu-id="a993e-274">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="a993e-275">您取回的每個*InteractionSourceState*都代表目前當時的互動來源。</span><span class="sxs-lookup"><span data-stu-id="a993e-275">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="a993e-276">*InteractionSourceState*會公開如下的資訊：</span><span class="sxs-lookup"><span data-stu-id="a993e-276">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="a993e-277">發生的[按下類型](motion-controllers.md)（選取/功能表/抓住/觸控板/操縱杆）</span><span class="sxs-lookup"><span data-stu-id="a993e-277">Which [kinds of presses](motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="a993e-278">動作控制器特定的其他資料，例如觸控板和/或操縱杆的 XY 座標和觸及狀態</span><span class="sxs-lookup"><span data-stu-id="a993e-278">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* <span data-ttu-id="a993e-279">要知道來源是手或動作控制器的 InteractionSourceKind</span><span class="sxs-lookup"><span data-stu-id="a993e-279">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="a993e-280">輪詢正向預測呈現的姿勢</span><span class="sxs-lookup"><span data-stu-id="a993e-280">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="a993e-281">當您輪詢來自手和控制器的互動來源資料時，您所得到的會是向前預測，這是在此框架的光子到達使用者眼的時間點。</span><span class="sxs-lookup"><span data-stu-id="a993e-281">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="a993e-282">這些向前預測的姿勢最適合**用來轉譯**控制器或每個框架的保留物件。</span><span class="sxs-lookup"><span data-stu-id="a993e-282">These forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="a993e-283">如果您以具有控制器的特定按或發行為目標，如果您使用下面所述的歷程記錄事件 Api，這會是最精確的方式。</span><span class="sxs-lookup"><span data-stu-id="a993e-283">If you are targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="a993e-284">您也可以取得這個目前框架的正向預測 head 姿勢。</span><span class="sxs-lookup"><span data-stu-id="a993e-284">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="a993e-285">就像來源姿勢一樣，這對於轉譯資料指標很有用，但如果您使用下面所述的歷程記錄事件 Api，**則以指定**的長按或版本為目標會最為精確。</span><span class="sxs-lookup"><span data-stu-id="a993e-285">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="a993e-286">處理互動來源事件</span><span class="sxs-lookup"><span data-stu-id="a993e-286">Handling interaction source events</span></span>

<span data-ttu-id="a993e-287">若要在輸入事件發生時處理其正確的歷程記錄姿勢資料，您可以處理互動來源事件，而不是輪詢。</span><span class="sxs-lookup"><span data-stu-id="a993e-287">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="a993e-288">若要處理互動來源事件：</span><span class="sxs-lookup"><span data-stu-id="a993e-288">To handle interaction source events:</span></span>
* <span data-ttu-id="a993e-289">註冊*InteractionManager*輸入事件。</span><span class="sxs-lookup"><span data-stu-id="a993e-289">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="a993e-290">針對您感興趣的每一種互動事件，您必須訂閱它。</span><span class="sxs-lookup"><span data-stu-id="a993e-290">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* <span data-ttu-id="a993e-291">處理事件。</span><span class="sxs-lookup"><span data-stu-id="a993e-291">Handle the event.</span></span> <span data-ttu-id="a993e-292">當您訂閱互動事件之後，您將會在適當時取得回呼。</span><span class="sxs-lookup"><span data-stu-id="a993e-292">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="a993e-293">在*SourcePressed*範例中，這會在偵測到來源之後，以及釋放或遺失之前。</span><span class="sxs-lookup"><span data-stu-id="a993e-293">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;
       
       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="a993e-294">如何停止處理事件</span><span class="sxs-lookup"><span data-stu-id="a993e-294">How to stop handling an event</span></span>

<span data-ttu-id="a993e-295">當您不再對事件感興趣，或正在終結已訂閱事件的物件時，您必須停止處理事件。</span><span class="sxs-lookup"><span data-stu-id="a993e-295">You need to stop handling an event when you are no longer interested in the event or you are destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="a993e-296">若要停止處理事件，請取消訂閱事件。</span><span class="sxs-lookup"><span data-stu-id="a993e-296">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="a993e-297">互動來源事件的清單</span><span class="sxs-lookup"><span data-stu-id="a993e-297">List of interaction source events</span></span>

<span data-ttu-id="a993e-298">可用的互動來源事件如下：</span><span class="sxs-lookup"><span data-stu-id="a993e-298">The available interaction source events are:</span></span>
* <span data-ttu-id="a993e-299">*InteractionSourceDetected* （來源變成作用中狀態）</span><span class="sxs-lookup"><span data-stu-id="a993e-299">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="a993e-300">*InteractionSourceLost* （變成非作用中）</span><span class="sxs-lookup"><span data-stu-id="a993e-300">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="a993e-301">*InteractionSourcePressed* （點一下、按下按鈕或 "Select" 從未提到）</span><span class="sxs-lookup"><span data-stu-id="a993e-301">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="a993e-302">*InteractionSourceReleased* （點一下、放開的按鈕，或 "Select" 從未提到的結尾）</span><span class="sxs-lookup"><span data-stu-id="a993e-302">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="a993e-303">*InteractionSourceUpdated* （移動或以其他方式變更某個狀態）</span><span class="sxs-lookup"><span data-stu-id="a993e-303">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="a993e-304">歷程記錄目標的事件，最精確地符合「按下」或「發行」</span><span class="sxs-lookup"><span data-stu-id="a993e-304">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="a993e-305">稍早所述的輪詢 Api 會提供您的應用程式向前預測的姿勢。</span><span class="sxs-lookup"><span data-stu-id="a993e-305">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="a993e-306">雖然這些預測的姿勢最適合用來呈現控制器或虛擬掌上型物件，但基於兩個主要原因，未來的姿勢並不是最佳目標：</span><span class="sxs-lookup"><span data-stu-id="a993e-306">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses are not optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="a993e-307">當使用者按下控制器上的按鈕時，可能會有大約20毫秒的無線延遲，然後系統才會收到按下。</span><span class="sxs-lookup"><span data-stu-id="a993e-307">When the user presses a button on a controller, there can be about 20ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="a993e-308">然後，如果您要使用正向預測的姿勢，則會有另一個 10 20 毫秒的正向預測，目標是目前框架的光子會到達使用者眼睛的時間。</span><span class="sxs-lookup"><span data-stu-id="a993e-308">Then, if you are using a forward-predicted pose, there would be another 10-20ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="a993e-309">這表示輪詢會提供來源姿勢或 head 姿勢，這是從使用者的前端和手中，在發生按下或發行時實際回到的40毫秒。</span><span class="sxs-lookup"><span data-stu-id="a993e-309">This means that polling gives you a source pose or head pose that is 30-40ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="a993e-310">針對 HoloLens 手寫輸入，雖然沒有無線傳輸延遲，但有類似的處理延遲可偵測按下。</span><span class="sxs-lookup"><span data-stu-id="a993e-310">For HoloLens hand input, while there's no wireless transmission delay, there is a similar processing delay to detect the press.</span></span>

<span data-ttu-id="a993e-311">若要根據使用者的原始意圖或控制器按下正確目標，您應該使用來自該*InteractionSourcePressed*或*InteractionSourceReleased*輸入事件的歷程記錄來源姿勢或 head 姿勢。</span><span class="sxs-lookup"><span data-stu-id="a993e-311">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="a993e-312">您可以使用來自使用者前端或其控制器的歷程記錄姿勢資料，以按下或發行為目標：</span><span class="sxs-lookup"><span data-stu-id="a993e-312">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="a993e-313">當手勢或控制器按下時的 head 姿勢，可以用來決定要[撥雲見日](gaze-and-commit.md)使用者的**目標**：</span><span class="sxs-lookup"><span data-stu-id="a993e-313">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](gaze-and-commit.md) at:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* <span data-ttu-id="a993e-314">當發生動作控制器按下時的來源姿勢，可以用來做為**目標**，以判斷使用者指向控制器的位置。</span><span class="sxs-lookup"><span data-stu-id="a993e-314">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="a993e-315">這會是經歷按下的控制器狀態。</span><span class="sxs-lookup"><span data-stu-id="a993e-315">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="a993e-316">如果您要轉譯控制器本身，您可以要求指標姿勢，而不是抓握姿勢，以從使用者會考慮該呈現控制器之自然提示的目標光線：</span><span class="sxs-lookup"><span data-stu-id="a993e-316">If you are rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a><span data-ttu-id="a993e-317">事件處理常式範例</span><span class="sxs-lookup"><span data-stu-id="a993e-317">Event handlers example</span></span>

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is 
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point. 
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="a993e-318">高階複合手勢 Api （GestureRecognizer）</span><span class="sxs-lookup"><span data-stu-id="a993e-318">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="a993e-319">**命名空間：** *UnityEngine. XR. WSA. 輸入*</span><span class="sxs-lookup"><span data-stu-id="a993e-319">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="a993e-320">**類型**： *GestureRecognizer*、 *GestureSettings*、 *InteractionSourceKind*</span><span class="sxs-lookup"><span data-stu-id="a993e-320">**Types**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span></span>

<span data-ttu-id="a993e-321">您的應用程式也可以辨識空間輸入來源、點按、按住、操作和導覽手勢的更高層級複合手勢。</span><span class="sxs-lookup"><span data-stu-id="a993e-321">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation and Navigation gestures.</span></span> <span data-ttu-id="a993e-322">您可以使用 GestureRecognizer，在[手](gaze-and-commit.md#composite-gestures)和[運動控制器](motion-controllers.md)上辨識這些複合手勢。</span><span class="sxs-lookup"><span data-stu-id="a993e-322">You can recognize these composite gestures across both [hands](gaze-and-commit.md#composite-gestures) and [motion controllers](motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="a993e-323">GestureRecognizer 上的每個手勢事件都會提供輸入的 SourceKind，以及事件當時的目標 head 光線。</span><span class="sxs-lookup"><span data-stu-id="a993e-323">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="a993e-324">某些事件會提供其他內容特定資訊。</span><span class="sxs-lookup"><span data-stu-id="a993e-324">Some events provide additional context specific information.</span></span>

<span data-ttu-id="a993e-325">使用手勢辨識器來捕獲手勢時，只需要幾個步驟：</span><span class="sxs-lookup"><span data-stu-id="a993e-325">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="a993e-326">建立新的手勢辨識器</span><span class="sxs-lookup"><span data-stu-id="a993e-326">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="a993e-327">指定要監看的手勢</span><span class="sxs-lookup"><span data-stu-id="a993e-327">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="a993e-328">訂閱這些手勢的事件</span><span class="sxs-lookup"><span data-stu-id="a993e-328">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="a993e-329">開始捕獲手勢</span><span class="sxs-lookup"><span data-stu-id="a993e-329">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="a993e-330">建立新的手勢辨識器</span><span class="sxs-lookup"><span data-stu-id="a993e-330">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="a993e-331">若要使用*GestureRecognizer*，您必須已建立*GestureRecognizer*：</span><span class="sxs-lookup"><span data-stu-id="a993e-331">To use the *GestureRecognizer*, you must have created a *GestureRecognizer*:</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="a993e-332">指定要監看的手勢</span><span class="sxs-lookup"><span data-stu-id="a993e-332">Specify which gestures to watch for</span></span>

<span data-ttu-id="a993e-333">透過*SetRecognizableGestures （）* 指定您感興趣的手勢：</span><span class="sxs-lookup"><span data-stu-id="a993e-333">Specify which gestures you are interested in via *SetRecognizableGestures()*:</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="a993e-334">訂閱這些手勢的事件</span><span class="sxs-lookup"><span data-stu-id="a993e-334">Subscribe to events for those gestures</span></span>

<span data-ttu-id="a993e-335">針對您感興趣的手勢訂閱事件。</span><span class="sxs-lookup"><span data-stu-id="a993e-335">Subscribe to events for the gestures you are interested in.</span></span>

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
><span data-ttu-id="a993e-336">導覽和動作筆勢在*GestureRecognizer*的實例上是互斥的。</span><span class="sxs-lookup"><span data-stu-id="a993e-336">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer*.</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="a993e-337">開始捕獲手勢</span><span class="sxs-lookup"><span data-stu-id="a993e-337">Start capturing gestures</span></span>

<span data-ttu-id="a993e-338">根據預設，在呼叫*StartCapturingGestures （）* 之前， *GestureRecognizer*不會監視輸入。</span><span class="sxs-lookup"><span data-stu-id="a993e-338">By default, a *GestureRecognizer* does not monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="a993e-339">如果在處理*StopCapturingGestures （）* 的框架之前執行了輸入，則在呼叫*StopCapturingGestures （）* 之後，可能會產生手勢事件。</span><span class="sxs-lookup"><span data-stu-id="a993e-339">It is possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="a993e-340">*GestureRecognizer*會記住在上一段實際發生的情況下，它是開啟還是關閉的，因此，根據這個畫面格的注視目標來啟動和停止手勢監視是很可靠的。</span><span class="sxs-lookup"><span data-stu-id="a993e-340">The *GestureRecognizer* will remember whether it was on or off during the previous frame in which the gesture actually occurred, and so it is reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="a993e-341">停止捕獲手勢</span><span class="sxs-lookup"><span data-stu-id="a993e-341">Stop capturing gestures</span></span>

<span data-ttu-id="a993e-342">若要停止手勢識別：</span><span class="sxs-lookup"><span data-stu-id="a993e-342">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="a993e-343">移除手勢辨識器</span><span class="sxs-lookup"><span data-stu-id="a993e-343">Removing a gesture recognizer</span></span>

<span data-ttu-id="a993e-344">請記得先取消訂閱已訂閱的事件，再終結*GestureRecognizer*物件。</span><span class="sxs-lookup"><span data-stu-id="a993e-344">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="a993e-345">在 Unity 中呈現動作控制器模型</span><span class="sxs-lookup"><span data-stu-id="a993e-345">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="a993e-346">![動作控制器模型和 teleportation](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="a993e-346">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="a993e-347">*運動控制器模型和 teleportation*</span><span class="sxs-lookup"><span data-stu-id="a993e-347">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="a993e-348">若要在您的應用程式中轉譯符合您的使用者所持有之實體控制器的運動控制器，並在按下各種按鈕時進行轉譯，您可以使用[Mixed Reality 工具](https://github.com/Microsoft/MixedRealityToolkit-Unity/)組中的**MotionController prefab** 。</span><span class="sxs-lookup"><span data-stu-id="a993e-348">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="a993e-349">這個 prefab 會從系統已安裝的動作控制器驅動程式，在執行時間動態載入正確的 glTF 模型。</span><span class="sxs-lookup"><span data-stu-id="a993e-349">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="a993e-350">請務必以動態方式載入這些模型，而不是在編輯器中手動加以匯入，如此一來，您的應用程式就會針對您的使用者可能會有的任何目前和未來的控制器，顯示實際精確的3D 模型。</span><span class="sxs-lookup"><span data-stu-id="a993e-350">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="a993e-351">遵循[消費者入門](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)的指示下載混合的現實工具組，並將其新增至您的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="a993e-351">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="a993e-352">如果您在消費者入門步驟中將相機取代為*MixedRealityCameraParent* prefab，您就可以開始使用！</span><span class="sxs-lookup"><span data-stu-id="a993e-352">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="a993e-353">該 prefab 包含動作控制器呈現。</span><span class="sxs-lookup"><span data-stu-id="a993e-353">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="a993e-354">否則，請從 [專案] 窗格將 [*資產]/[HoloToolkit]/[輸入/Prefabs]/[MotionControllers* ] 新增至您的場景。</span><span class="sxs-lookup"><span data-stu-id="a993e-354">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="a993e-355">當使用者在場景中 teleports 時，您會想要將該 prefab 新增為任何父物件的子系，以用來移動相機，讓控制器與使用者一起使用。</span><span class="sxs-lookup"><span data-stu-id="a993e-355">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="a993e-356">如果您的應用程式不牽涉到 teleporting，只需在您場景的根目錄新增 prefab。</span><span class="sxs-lookup"><span data-stu-id="a993e-356">If your app does not involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="a993e-357">擲回物件</span><span class="sxs-lookup"><span data-stu-id="a993e-357">Throwing objects</span></span>

<span data-ttu-id="a993e-358">在虛擬實境中擲回物件是較困難的問題，因此可能一開始就會出現。</span><span class="sxs-lookup"><span data-stu-id="a993e-358">Throwing objects in virtual reality is a harder problem then it may at first seem.</span></span> <span data-ttu-id="a993e-359">如同大部分的實際互動，當遊戲中擲回時，它會立即明顯地中斷深度。</span><span class="sxs-lookup"><span data-stu-id="a993e-359">As with most physically based interactions, when throwing in game acts in an unexpected way, it is immediately obvious and breaks immersion.</span></span> <span data-ttu-id="a993e-360">我們花了一些時間來思考如何代表實際的正確擲回行為，並提供一些指導方針，並透過我們的平臺更新而啟用，我們想要與您分享。</span><span class="sxs-lookup"><span data-stu-id="a993e-360">We have spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="a993e-361">您可以在[這裡](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)找到建議如何執行的範例。</span><span class="sxs-lookup"><span data-stu-id="a993e-361">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="a993e-362">這個範例會遵循下列四個指導方針：</span><span class="sxs-lookup"><span data-stu-id="a993e-362">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="a993e-363">**使用控制器的*速度*而不是位置**。</span><span class="sxs-lookup"><span data-stu-id="a993e-363">**Use the controller’s *velocity* instead of position**.</span></span> <span data-ttu-id="a993e-364">在 Windows 的11月更新中，我們在[' ' 近似 ' ' 位置追蹤狀態](motion-controllers.md#controller-tracking-state)中引進了行為變更。</span><span class="sxs-lookup"><span data-stu-id="a993e-364">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="a993e-365">處於此狀態時，將會繼續回報關於控制器的速度資訊，只要我們認為它是高精確度，通常比位置保持高的精確度長。</span><span class="sxs-lookup"><span data-stu-id="a993e-365">When in this state, velocity information about the controller will continue to be reported for as long as we believe it is high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="a993e-366">**納入控制器的\*角度速度**\* 。</span><span class="sxs-lookup"><span data-stu-id="a993e-366">**Incorporate the *angular velocity* of the controller**.</span></span> <span data-ttu-id="a993e-367">這個邏輯全部包含在 `GetThrownObjectVelAngVel` 靜態方法的 `throwing.cs` 檔案中，在上述連結的封裝內：</span><span class="sxs-lookup"><span data-stu-id="a993e-367">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="a993e-368">隨著角度的速度 conserved，所擲回的物件必須維持與擲回時相同的角度速度： `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="a993e-368">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="a993e-369">因為擲回物件的範圍可能不是在抓握姿勢的原點，所以它可能會有不同的速度，而在使用者參考的框架中，控制器的速度也不一樣。</span><span class="sxs-lookup"><span data-stu-id="a993e-369">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity then that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="a993e-370">以這種方式貢獻的物件速度部分，是在控制器原點周圍，所擲回物件的即時相切速度。</span><span class="sxs-lookup"><span data-stu-id="a993e-370">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="a993e-371">此相切速度是控制器角度速度的交叉乘積，其向量代表控制器原點與所擲回物件之大量的中心之間的距離。</span><span class="sxs-lookup"><span data-stu-id="a993e-371">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. <span data-ttu-id="a993e-372">所擲回物件的總速度就是控制器的速度和此相切速度的總和： `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="a993e-372">The total velocity of the thrown object is thus the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="a993e-373">請**密切注意我們套用速度的\*時間**\* 。</span><span class="sxs-lookup"><span data-stu-id="a993e-373">**Pay close attention to the *time* at which we apply the velocity**.</span></span> <span data-ttu-id="a993e-374">按下按鈕時，最多可能需要20毫秒該事件，才能透過藍牙向上到作業系統。</span><span class="sxs-lookup"><span data-stu-id="a993e-374">When a button is pressed, it can take up to 20ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="a993e-375">這表示，如果您輪詢控制器狀態變更，使其無法按下，或反之亦然，控制器會使用您所取得的資訊，實際上會在這項變更的狀態之前。</span><span class="sxs-lookup"><span data-stu-id="a993e-375">This means that if you poll for a controller state change from pressed to not pressed or vice versa, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="a993e-376">此外，我們的輪詢 API 所呈現的控制器會向前預測，以反映在畫面顯示時可能會有的姿勢，未來可能會有更多的20毫秒。</span><span class="sxs-lookup"><span data-stu-id="a993e-376">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more then 20ms in the future.</span></span> <span data-ttu-id="a993e-377">這適合用來*呈現*持有的物件，但是會在使用者釋放其擲回的時間點時，將我們的目標問題放在我們的*目標*物件上。</span><span class="sxs-lookup"><span data-stu-id="a993e-377">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released their throw.</span></span> <span data-ttu-id="a993e-378">幸運的是，在11月更新中，當*InteractionSourcePressed*或*InteractionSourceReleased*等 Unity 事件傳送時，狀態會在按鈕實際按下或放開時，包含背景的歷程記錄資料。</span><span class="sxs-lookup"><span data-stu-id="a993e-378">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was actually pressed or released.</span></span>  <span data-ttu-id="a993e-379">若要在擲回時取得最精確的控制器轉譯和控制器目標，您必須適當地使用輪詢和事件：</span><span class="sxs-lookup"><span data-stu-id="a993e-379">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="a993e-380">對於**呈現**每個畫面格的控制器，您的應用程式應該將控制器的*GameObject*置於目前框架 photon 時間的正向預測控制器上。</span><span class="sxs-lookup"><span data-stu-id="a993e-380">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="a993e-381">您會從 Unity 輪詢 Api （例如 XR）取得此資料 *[。InputTracking. GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* 或 *[XR。WSA.輸入. InteractionManager. GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)* 。</span><span class="sxs-lookup"><span data-stu-id="a993e-381">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span></span>
   * <span data-ttu-id="a993e-382">針對以按下或發行為**目標的控制器**，您的應用程式應該根據該按下或釋放事件的歷程控制器姿勢來 raycast 和計算軌跡。</span><span class="sxs-lookup"><span data-stu-id="a993e-382">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="a993e-383">您會從 Unity 事件 Api 取得此資料，例如 *[InteractionManager. InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* 。</span><span class="sxs-lookup"><span data-stu-id="a993e-383">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span></span>
* <span data-ttu-id="a993e-384">**使用抓握姿勢**。</span><span class="sxs-lookup"><span data-stu-id="a993e-384">**Use the grip pose**.</span></span> <span data-ttu-id="a993e-385">角度的速度和速度會相對於抓握姿勢（而不是指標姿勢）來報告。</span><span class="sxs-lookup"><span data-stu-id="a993e-385">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="a993e-386">擲回會繼續改善未來的 Windows 更新，您可以在這裡找到更多相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a993e-386">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="gesture-and-motion-controllers-in-mrtk-v2"></a><span data-ttu-id="a993e-387">MRTK v2 中的手勢和運動控制器</span><span class="sxs-lookup"><span data-stu-id="a993e-387">Gesture and Motion Controllers in MRTK v2</span></span>

<span data-ttu-id="a993e-388">您可以從輸入管理員存取手勢和動作控制器。</span><span class="sxs-lookup"><span data-stu-id="a993e-388">You can access gesture and motion controller from the input Manager.</span></span> 
* [<span data-ttu-id="a993e-389">MRTK v2 中的手勢</span><span class="sxs-lookup"><span data-stu-id="a993e-389">Gesture in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Gestures.html)
* [<span data-ttu-id="a993e-390">MRTK v2 中的運動控制器</span><span class="sxs-lookup"><span data-stu-id="a993e-390">Motion Controller in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html)


## <a name="follow-along-with-tutorials"></a><span data-ttu-id="a993e-391">遵循教學課程</span><span class="sxs-lookup"><span data-stu-id="a993e-391">Follow along with tutorials</span></span>

<span data-ttu-id="a993e-392">混合現實學術提供逐步教學課程，其中包含更詳細的自訂範例：</span><span class="sxs-lookup"><span data-stu-id="a993e-392">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="a993e-393">MR 輸入211：手勢</span><span class="sxs-lookup"><span data-stu-id="a993e-393">MR Input 211: Gesture</span></span>](holograms-211.md)
- [<span data-ttu-id="a993e-394">MR 輸入213：動作控制器</span><span class="sxs-lookup"><span data-stu-id="a993e-394">MR Input 213: Motion controllers</span></span>](mixed-reality-213.md)

<span data-ttu-id="a993e-395">[![MR 輸入 213-運動控制器](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="a993e-395">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="a993e-396">*MR 輸入 213-運動控制器*</span><span class="sxs-lookup"><span data-stu-id="a993e-396">*MR Input 213 - Motion controller*</span></span>

## <a name="see-also"></a><span data-ttu-id="a993e-397">請參閱</span><span class="sxs-lookup"><span data-stu-id="a993e-397">See also</span></span>

* [<span data-ttu-id="a993e-398">頭部目光和行動</span><span class="sxs-lookup"><span data-stu-id="a993e-398">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="a993e-399">運動控制器</span><span class="sxs-lookup"><span data-stu-id="a993e-399">Motion controllers</span></span>](motion-controllers.md)


