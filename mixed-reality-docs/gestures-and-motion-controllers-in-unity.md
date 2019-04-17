---
title: 筆勢和 Unity 中的動作控制站
description: 有兩種主要的方式，在您的視線 Unity、 手勢和動作控制站上採取動作。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 筆勢、 動作控制站、 unity、 視線，輸入
ms.openlocfilehash: d98590f9a6c40336a13cb75e8050e13edfaa2a6c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591149"
---
# <a name="gestures-and-motion-controllers-in-unity"></a><span data-ttu-id="7ffa3-104">筆勢和 Unity 中的動作控制站</span><span class="sxs-lookup"><span data-stu-id="7ffa3-104">Gestures and motion controllers in Unity</span></span>

<span data-ttu-id="7ffa3-105">有兩種主要的方式採取行動您[視線中 Unity](gaze-in-unity.md)，[交給筆勢](gestures.md)並[動作控制器](motion-controllers.md)。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](gestures.md) and [motion controllers](motion-controllers.md).</span></span> <span data-ttu-id="7ffa3-106">您透過相同的 Api，在 Unity 中存取這兩個來源的空間的輸入資料。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="7ffa3-107">Unity 提供兩種主要的方式來存取空間的輸入的資料的 Windows Mixed Reality，常見*Input.GetButton/Input.GetAxis*可跨多個 Unity XR Sdk，Api 和*InteractionManager /GestureRecognizer*公開可用的空間輸入資料的一組完整的 Windows Mixed Reality 專屬的 API。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality, the common *Input.GetButton/Input.GetAxis* APIs that work across multiple Unity XR SDKs, and an *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality that exposes the full set of spatial input data available.</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="7ffa3-108">Unity 按鈕/軸對應表</span><span class="sxs-lookup"><span data-stu-id="7ffa3-108">Unity button/axis mapping table</span></span>

<span data-ttu-id="7ffa3-109">下表中的按鈕和軸識別碼支援 Unity 的輸入管理員 中的 Windows Mixed Reality 動作控制站*Input.GetButton/GetAxis* Api，而 「 Windows MR 專屬"的資料行參考屬性都*InteractionSourceState*型別。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-109">The button and axis IDs in the table below are supported in Unity's Input Manager for Windows Mixed Reality motion controllers through the *Input.GetButton/GetAxis* APIs, while the "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="7ffa3-110">在下列各節中詳細說明每個這些 Api。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-110">Each of these APIs are described in detail in the sections below.</span></span>

<span data-ttu-id="7ffa3-111">Windows Mixed Reality 的按鈕/軸識別碼對應通常會符合 Oculus 按鈕/軸識別碼。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-111">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="7ffa3-112">Windows Mixed Reality 的按鈕/軸識別碼對應不同 OpenVR 的對應，有兩種：</span><span class="sxs-lookup"><span data-stu-id="7ffa3-112">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="7ffa3-113">對應會使用觸控板 Id 不同於搖桿，來支援使用搖桿和跳動的控制站。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-113">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="7ffa3-114">對應可避免多載 A 和 X 按鈕的功能表按鈕時，若要讓這些可用的實體 ABXY 按鈕的識別碼。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-114">The mapping avoids overloading the A and X button IDs for the Menu buttons, to leave those available for physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="7ffa3-115">Input</span><span class="sxs-lookup"><span data-stu-id="7ffa3-115">Input</span></span> </th><th colspan="2"><span data-ttu-id="7ffa3-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">常見的 Unity Api</a></span><span class="sxs-lookup"><span data-stu-id="7ffa3-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="7ffa3-117">(Input.GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="7ffa3-117">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="7ffa3-118"><a href="gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xr.wsa.input">Windows MR 特定輸入的 API</a></span><span class="sxs-lookup"><span data-stu-id="7ffa3-118"><a href="gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xr.wsa.input">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="7ffa3-119">(XR.WSA.Input)</span><span class="sxs-lookup"><span data-stu-id="7ffa3-119">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="7ffa3-120">左邊</span><span class="sxs-lookup"><span data-stu-id="7ffa3-120">Left hand</span></span> </th><th> <span data-ttu-id="7ffa3-121">右下</span><span class="sxs-lookup"><span data-stu-id="7ffa3-121">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="7ffa3-122">按下選取的觸發程序</span><span class="sxs-lookup"><span data-stu-id="7ffa3-122">Select trigger pressed</span></span> </td><td> <span data-ttu-id="7ffa3-123">軸 9 = 1.0</span><span class="sxs-lookup"><span data-stu-id="7ffa3-123">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="7ffa3-124">軸 10 = 1.0</span><span class="sxs-lookup"><span data-stu-id="7ffa3-124">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="7ffa3-125">selectPressed</span><span class="sxs-lookup"><span data-stu-id="7ffa3-125">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ffa3-126">選取觸發程序類比值</span><span class="sxs-lookup"><span data-stu-id="7ffa3-126">Select trigger analog value</span></span> </td><td> <span data-ttu-id="7ffa3-127">軸 9</span><span class="sxs-lookup"><span data-stu-id="7ffa3-127">Axis 9</span></span> </td><td> <span data-ttu-id="7ffa3-128">軸 10</span><span class="sxs-lookup"><span data-stu-id="7ffa3-128">Axis 10</span></span> </td><td> <span data-ttu-id="7ffa3-129">selectPressedAmount</span><span class="sxs-lookup"><span data-stu-id="7ffa3-129">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ffa3-130">選取部分已按下的觸發程序</span><span class="sxs-lookup"><span data-stu-id="7ffa3-130">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="7ffa3-131">按鈕 14 <i>（遊戲台相容性）</i> </span><span class="sxs-lookup"><span data-stu-id="7ffa3-131">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="7ffa3-132">按鈕 15 <i>（遊戲台相容性）</i> </span><span class="sxs-lookup"><span data-stu-id="7ffa3-132">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="7ffa3-133">selectPressedAmount &gt; 0.0</span><span class="sxs-lookup"><span data-stu-id="7ffa3-133">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ffa3-134">已按下功能表按鈕</span><span class="sxs-lookup"><span data-stu-id="7ffa3-134">Menu button pressed</span></span> </td><td> <span data-ttu-id="7ffa3-135">按鈕 6 \*</span><span class="sxs-lookup"><span data-stu-id="7ffa3-135">Button 6\*</span></span> </td><td> <span data-ttu-id="7ffa3-136">按鈕 7 \*</span><span class="sxs-lookup"><span data-stu-id="7ffa3-136">Button 7\*</span></span> </td><td> <span data-ttu-id="7ffa3-137">menuPressed</span><span class="sxs-lookup"><span data-stu-id="7ffa3-137">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ffa3-138">已按下的底框按鈕</span><span class="sxs-lookup"><span data-stu-id="7ffa3-138">Grip button pressed</span></span> </td><td> <span data-ttu-id="7ffa3-139">11 = 1.0 （未類比的值） 軸</span><span class="sxs-lookup"><span data-stu-id="7ffa3-139">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="7ffa3-140">按鈕 4 <i>（遊戲台相容性）</i> </span><span class="sxs-lookup"><span data-stu-id="7ffa3-140">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="7ffa3-141">12 = 1.0 （未類比的值） 軸</span><span class="sxs-lookup"><span data-stu-id="7ffa3-141">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="7ffa3-142">按鈕 5 <i>（遊戲台相容性）</i> </span><span class="sxs-lookup"><span data-stu-id="7ffa3-142">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="7ffa3-143">grasped</span><span class="sxs-lookup"><span data-stu-id="7ffa3-143">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ffa3-144">搖桿 X <i>(左:-1.0，正確：1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="7ffa3-144">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="7ffa3-145">軸 1</span><span class="sxs-lookup"><span data-stu-id="7ffa3-145">Axis 1</span></span> </td><td> <span data-ttu-id="7ffa3-146">軸 4</span><span class="sxs-lookup"><span data-stu-id="7ffa3-146">Axis 4</span></span> </td><td> <span data-ttu-id="7ffa3-147">thumbstickPosition.x</span><span class="sxs-lookup"><span data-stu-id="7ffa3-147">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ffa3-148">搖桿 Y <i>(top:-1.0，底部：1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="7ffa3-148">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="7ffa3-149">軸 2</span><span class="sxs-lookup"><span data-stu-id="7ffa3-149">Axis 2</span></span> </td><td> <span data-ttu-id="7ffa3-150">軸 5</span><span class="sxs-lookup"><span data-stu-id="7ffa3-150">Axis 5</span></span> </td><td> <span data-ttu-id="7ffa3-151">thumbstickPosition.y</span><span class="sxs-lookup"><span data-stu-id="7ffa3-151">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ffa3-152">按下的搖桿</span><span class="sxs-lookup"><span data-stu-id="7ffa3-152">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="7ffa3-153">按鈕 8</span><span class="sxs-lookup"><span data-stu-id="7ffa3-153">Button 8</span></span> </td><td> <span data-ttu-id="7ffa3-154">按鈕 9</span><span class="sxs-lookup"><span data-stu-id="7ffa3-154">Button 9</span></span> </td><td> <span data-ttu-id="7ffa3-155">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="7ffa3-155">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ffa3-156">觸控板 X <i>(左:-1.0，正確：1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="7ffa3-156">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="7ffa3-157">軸 17 \*</span><span class="sxs-lookup"><span data-stu-id="7ffa3-157">Axis 17\*</span></span> </td><td> <span data-ttu-id="7ffa3-158">軸 19 \*</span><span class="sxs-lookup"><span data-stu-id="7ffa3-158">Axis 19\*</span></span> </td><td> <span data-ttu-id="7ffa3-159">touchpadPosition.x</span><span class="sxs-lookup"><span data-stu-id="7ffa3-159">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ffa3-160">觸控板 Y <i>(top:-1.0，底部：1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="7ffa3-160">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="7ffa3-161">軸 18 \*</span><span class="sxs-lookup"><span data-stu-id="7ffa3-161">Axis 18\*</span></span> </td><td> <span data-ttu-id="7ffa3-162">軸 20 \*</span><span class="sxs-lookup"><span data-stu-id="7ffa3-162">Axis 20\*</span></span> </td><td> <span data-ttu-id="7ffa3-163">touchpadPosition.y</span><span class="sxs-lookup"><span data-stu-id="7ffa3-163">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ffa3-164">接觸到的觸控板</span><span class="sxs-lookup"><span data-stu-id="7ffa3-164">Touchpad touched</span></span> </td><td> <span data-ttu-id="7ffa3-165">按鈕 18 \*</span><span class="sxs-lookup"><span data-stu-id="7ffa3-165">Button 18\*</span></span> </td><td> <span data-ttu-id="7ffa3-166">按鈕 19 \*</span><span class="sxs-lookup"><span data-stu-id="7ffa3-166">Button 19\*</span></span> </td><td> <span data-ttu-id="7ffa3-167">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="7ffa3-167">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ffa3-168">按下觸控板</span><span class="sxs-lookup"><span data-stu-id="7ffa3-168">Touchpad pressed</span></span> </td><td> <span data-ttu-id="7ffa3-169">按鈕 16 \*</span><span class="sxs-lookup"><span data-stu-id="7ffa3-169">Button 16\*</span></span> </td><td> <span data-ttu-id="7ffa3-170">按鈕 17 \*</span><span class="sxs-lookup"><span data-stu-id="7ffa3-170">Button 17\*</span></span> </td><td> <span data-ttu-id="7ffa3-171">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="7ffa3-171">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ffa3-172">6DoF 底框姿勢或指標姿勢</span><span class="sxs-lookup"><span data-stu-id="7ffa3-172">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="7ffa3-173"><i>調整底框</i>只造成：<a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="7ffa3-173"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="7ffa3-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="7ffa3-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="7ffa3-175">傳遞<i>底框</i>或是<i>指標</i>做為引數： sourceState.sourcePose.TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="7ffa3-175">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="7ffa3-176">sourceState.sourcePose.TryGetRotation</span><span class="sxs-lookup"><span data-stu-id="7ffa3-176">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="7ffa3-177">追蹤狀態</span><span class="sxs-lookup"><span data-stu-id="7ffa3-177">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="7ffa3-178"><i>位置精確度和來源遺失風險只能透過 MR 特定 API</i> </span><span class="sxs-lookup"><span data-stu-id="7ffa3-178"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="7ffa3-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span><span class="sxs-lookup"><span data-stu-id="7ffa3-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="7ffa3-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="7ffa3-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="7ffa3-181">這些按鈕/軸識別碼不同於 Unity 使用 OpenVR 因為舵 Oculus 觸控和 OpenVR 所使用的對應發生衝突的識別碼。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-181">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="7ffa3-182">指標的姿勢與的底框姿勢</span><span class="sxs-lookup"><span data-stu-id="7ffa3-182">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="7ffa3-183">Windows Mixed Reality 支援各種不同的外型規格中的動作控制站，與每個控制站設計不同使用者的手狀位置和 「 轉送 」 方向該應用程式的自然之間關聯性的相對值應該使用指出呈現時控制站。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-183">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="7ffa3-184">為了更能代表這些控制站，有兩種您可以調查每個互動來源，會帶來**底框姿勢**並**指標姿勢**。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-184">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="7ffa3-185">全域 Unity 的全局座標中的所有 Unity Api 來表示這兩個的底框姿勢和指標姿勢座標。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-185">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="7ffa3-186">調整底框姿勢</span><span class="sxs-lookup"><span data-stu-id="7ffa3-186">Grip pose</span></span>

<span data-ttu-id="7ffa3-187">**底框姿勢**表示偵測到的 HoloLens，一隻手的或翲保存動作控制器的位置。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-187">The **grip pose** represents the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>

<span data-ttu-id="7ffa3-188">沈浸式耳機，在底框姿勢最適合用來呈現**使用者的手**或是**物件保留在使用者的手**劍或槍等。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-188">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span> <span data-ttu-id="7ffa3-189">將顯示為動作控制站時，也會使用的底框姿勢**可呈現模型**提供所移動的 Windows 控制站，請使用做為其原始並旋轉的中心點的底框姿勢。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-189">The grip pose is also used when visualizing a motion controller, as the **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="7ffa3-190">調整底框姿勢定義具體來說，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7ffa3-190">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="7ffa3-191">**抓住位置**:Palm 距心自然，保留控制器時調整左邊或右邊，置中的底框的位置。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-191">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="7ffa3-192">在 Windows Mixed Reality 動作控制站，這個位置通常配合掌握 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-192">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="7ffa3-193">**抓住方向的右座標軸**:當您完全開啟以形成平坦的 5 手指姿勢手時，光線，一般是您 palm （從左 palm、 從右 palm 回溯順向）</span><span class="sxs-lookup"><span data-stu-id="7ffa3-193">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="7ffa3-194">**抓住方向的順向軸**:當您關閉您的手部分 （如同保存在控制站）、"forward"tube 透過由非 thumb 手指點光線。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-194">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="7ffa3-195">**抓住方向的總軸**:隱含的權限和轉送的定義總軸。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-195">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="7ffa3-196">您可以透過任一 Unity 的跨銷售商輸入的 API 來存取的底框姿勢 (*[XR。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/Rotation*) 或透過 Windows MR 特定 API (*sourceState.sourcePose.TryGetPosition/Rotation*，要求會造成資料**底框**節點)。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-196">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="7ffa3-197">指標姿勢</span><span class="sxs-lookup"><span data-stu-id="7ffa3-197">Pointer pose</span></span>

<span data-ttu-id="7ffa3-198">**指標姿勢**表示向前指的控制站的提示。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-198">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="7ffa3-199">系統提供的指標姿勢最適合用於 raycast 完**轉譯控制器模型本身**。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-199">The system-provided pointer pose is best used to raycast when you are **rendering the controller model itself**.</span></span> <span data-ttu-id="7ffa3-200">如果您要呈現其他某些虛擬物件，來控制站，例如虛擬的砲，取代您應該點是最方便的該虛擬物件，例如傳輸的應用程式定義槍模型鸃庢餂沿著光線的光線。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-200">If you are rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that is most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="7ffa3-201">因為使用者可以看到虛擬物件並不是實體的控制器，指向與虛擬物件可能會對於使用您的應用程式更自然。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-201">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="7ffa3-202">指標姿勢目前可在 Unity 中只透過 Windows MR 特定 API *sourceState.sourcePose.TryGetPosition/Rotation*，並傳入*InteractionSourceNode.Pointer*為引數。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-202">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="7ffa3-203">控制器追蹤狀態</span><span class="sxs-lookup"><span data-stu-id="7ffa3-203">Controller tracking state</span></span>

<span data-ttu-id="7ffa3-204">耳機，像是 Windows Mixed Reality 動作控制站不需要任何設定的外部追蹤感應器。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-204">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="7ffa3-205">相反地，控制器會追蹤耳機本身中的感應器。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-205">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="7ffa3-206">如果使用者移出耳機的視野，控制站，在大部分情況下 Windows 會推斷控制站的位置，並將其提供給應用程式繼續。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-206">If the user moves the controllers out of the headset's field of view, in most cases Windows will continue to infer controller positions and provide them to the app.</span></span> <span data-ttu-id="7ffa3-207">當控制器失去 visual 追蹤身體力行，控制站的位置將會卸除到近似精確度的位置。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-207">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="7ffa3-208">此時，系統會主體鎖定給使用者時，追蹤使用者的位置，同時仍公開使用其內部的方向感應器的控制站，則為 true 的方向移動，控制站。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-208">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="7ffa3-209">許多應用程式會使用控制器，以指向，並啟用 UI 項目可以正常運作近似值的精確度在使用者的演算法而不會。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-209">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="7ffa3-210">若要瞭解這個，最好是親自試試看。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-210">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="7ffa3-211">請參閱這段影片中使用控制器動作適用於各種追蹤狀態的沈浸式內容的範例：</span><span class="sxs-lookup"><span data-stu-id="7ffa3-211">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="7ffa3-212">明確地追蹤狀態的來龍去脈</span><span class="sxs-lookup"><span data-stu-id="7ffa3-212">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="7ffa3-213">想要將位置根據追蹤狀態的應用程式可能可以更進一步，並檢查控制器的狀態的屬性，例如*SourceLossRisk*並*PositionAccuracy*:</span><span class="sxs-lookup"><span data-stu-id="7ffa3-213">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="7ffa3-214">追蹤狀態</span><span class="sxs-lookup"><span data-stu-id="7ffa3-214">Tracking state</span></span> </th><th> <span data-ttu-id="7ffa3-215">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="7ffa3-215">SourceLossRisk</span></span> </th><th> <span data-ttu-id="7ffa3-216">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="7ffa3-216">PositionAccuracy</span></span> </th><th> <span data-ttu-id="7ffa3-217">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="7ffa3-217">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="7ffa3-218"><b>高精確度</b> </span><span class="sxs-lookup"><span data-stu-id="7ffa3-218"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="7ffa3-219">&lt; 1.0</span><span class="sxs-lookup"><span data-stu-id="7ffa3-219">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="7ffa3-220">高</span><span class="sxs-lookup"><span data-stu-id="7ffa3-220">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="7ffa3-221">true</span><span class="sxs-lookup"><span data-stu-id="7ffa3-221">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ffa3-222"><b>（有遺失資料的風險） 的高精確度</b> </span><span class="sxs-lookup"><span data-stu-id="7ffa3-222"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="7ffa3-223">== 1.0</span><span class="sxs-lookup"><span data-stu-id="7ffa3-223">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="7ffa3-224">高</span><span class="sxs-lookup"><span data-stu-id="7ffa3-224">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="7ffa3-225">true</span><span class="sxs-lookup"><span data-stu-id="7ffa3-225">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ffa3-226"><b>近似值的精確度</b> </span><span class="sxs-lookup"><span data-stu-id="7ffa3-226"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="7ffa3-227">== 1.0</span><span class="sxs-lookup"><span data-stu-id="7ffa3-227">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="7ffa3-228">大約</span><span class="sxs-lookup"><span data-stu-id="7ffa3-228">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="7ffa3-229">true</span><span class="sxs-lookup"><span data-stu-id="7ffa3-229">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="7ffa3-230"><b>沒有位置</b> </span><span class="sxs-lookup"><span data-stu-id="7ffa3-230"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="7ffa3-231">== 1.0</span><span class="sxs-lookup"><span data-stu-id="7ffa3-231">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="7ffa3-232">大約</span><span class="sxs-lookup"><span data-stu-id="7ffa3-232">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="7ffa3-233">false</span><span class="sxs-lookup"><span data-stu-id="7ffa3-233">false</span></span></td>
</tr>
</table>

<span data-ttu-id="7ffa3-234">這些動作的控制器追蹤狀態定義，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7ffa3-234">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="7ffa3-235">**高精確度：** 耳機的視野內移動控制站時，它通常會提供高精確度的位置，以視覺化的追蹤。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-235">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="7ffa3-236">請注意，移動的控制站，會暫時離開檢視欄位或暫時遮蔽耳機感應器 (例如，藉由使用者的相反) 會繼續傳回高精確度會帶來一小段時間，以控制站的慣性追蹤它本身。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-236">Note that a moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="7ffa3-237">**（有遺失資料的風險） 的高精確度：** 當使用者移動超過的耳機的視野邊緣的移動控制站時，耳機將推出無法以視覺方式追蹤控制站的位置。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-237">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="7ffa3-238">應用程式可讓您知道當控制器時，已藉由查看達到此 FOV 界限**SourceLossRisk**觸達 1.0。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-238">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="7ffa3-239">此時，應用程式可以選擇暫停需要非常高品質會帶來的穩定資料流的控制站筆勢。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-239">At that point, the app may choose to pause controller gestures that require a steady stream of very high-quality poses.</span></span>
* <span data-ttu-id="7ffa3-240">**近似值的精確度：** 當控制器失去 visual 追蹤身體力行，控制站的位置將會卸除到近似精確度的位置。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-240">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="7ffa3-241">此時，系統會主體鎖定給使用者時，追蹤使用者的位置，同時仍公開使用其內部的方向感應器的控制站，則為 true 的方向移動，控制站。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-241">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="7ffa3-242">許多應用程式會使用控制器，以指向，並啟用 UI 項目可以做為一般的時間近似值的精確度在使用者的演算法而不會。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-242">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="7ffa3-243">較輸入需求的應用程式可能會選擇感測從這個下拉式**高**精確度**近似**藉由檢查精確度**PositionAccuracy**屬性，如讓使用者更多的 hitbox 幕外的目標在這段時間的範例。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-243">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="7ffa3-244">**不到位置：** 控制器可長時間操作近似值的精確度，而有時系統知道，甚至主體鎖定的位置目前不具意義。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-244">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position is not meaningful at the moment.</span></span> <span data-ttu-id="7ffa3-245">例如，只是開啟的控制站可能永遠不會觀察到在視覺上，或使用者可能會讓下一個控制站，然後挑選其他人。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-245">For example, a controller that was just turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="7ffa3-246">在這些時間，系統將不會提供任何位置，應用程式，並*TryGetPosition*會傳回 false。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-246">At those times, the system will not provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="7ffa3-247">常見的 Unity Api (Input.GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="7ffa3-247">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="7ffa3-248">\**命名空間：\*\*\*UnityEngine*， *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="7ffa3-248">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="7ffa3-249">**型別**:*輸入*， *XR。InputTracking*</span><span class="sxs-lookup"><span data-stu-id="7ffa3-249">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="7ffa3-250">Unity 目前使用其一般*Input.GetButton/Input.GetAxis* Api 來公開 （expose） 輸入[Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html)， [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)和 Windows Mixed Reality，包括雙手及動作控制站。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-250">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="7ffa3-251">如果您的應用程式會使用這些 Api 的輸入，它可以輕鬆地跨多個 XR Sdk，包括 Windows Mixed Reality 中支援動作控制站。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-251">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="7ffa3-252">取得邏輯按鈕已按下的狀態</span><span class="sxs-lookup"><span data-stu-id="7ffa3-252">Getting a logical button's pressed state</span></span>

<span data-ttu-id="7ffa3-253">若要使用一般的 Unity 輸入 Api，您將一開始通常會連接按鈕和中的邏輯名稱的座標軸[Unity 輸入管理員](https://docs.unity3d.com/Manual/ConventionalGameInput.html)，繫結至每個名稱的軸識別碼或按鈕。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-253">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="7ffa3-254">然後，您可以撰寫程式碼，是指該邏輯的按鈕軸名稱。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-254">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="7ffa3-255">例如，若要對應左的動作控制器的觸發程序] 按鈕送出動作，請前往**編輯 > 專案設定 > 輸入**Unity 內展開的送出區段的 [軸屬性。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-255">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="7ffa3-256">變更**正值按鈕**或**Alt 正按鈕**屬性，以讀取**搖桿按鈕 14**，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7ffa3-256">Change the **Postive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="7ffa3-257">![Unity 的 InputManager](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="7ffa3-257">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="7ffa3-258">*Unity InputManager*</span><span class="sxs-lookup"><span data-stu-id="7ffa3-258">*Unity InputManager*</span></span>

<span data-ttu-id="7ffa3-259">提交動作使用，可以接著選取您的指令碼*Input.GetButton*:</span><span class="sxs-lookup"><span data-stu-id="7ffa3-259">Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="7ffa3-260">您可以加入多個邏輯的按鈕，變更**大小**下方的屬性**軸**。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-260">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="7ffa3-261">直接取得的實體按鈕已按下的狀態</span><span class="sxs-lookup"><span data-stu-id="7ffa3-261">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="7ffa3-262">您也可以存取按鈕以手動方式由其完整名稱，並使用*Input.GetKey*:</span><span class="sxs-lookup"><span data-stu-id="7ffa3-262">You can also access buttons manually by their fully-qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="7ffa3-263">取得手形或動作控制器的姿勢</span><span class="sxs-lookup"><span data-stu-id="7ffa3-263">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="7ffa3-264">您可以存取的位置和旋轉的控制器，使用*XR。InputTracking*:</span><span class="sxs-lookup"><span data-stu-id="7ffa3-264">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

<span data-ttu-id="7ffa3-265">請注意，這代表控制器的底框姿勢 （使用者按住控制器），這很適合用於轉譯的拉鋸或槍中使用者的手的形狀或控制站本身的模型。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-265">Note that this represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>

<span data-ttu-id="7ffa3-266">請注意，此調整底框姿勢 （其中指控制站的提示） 的指標姿勢之間的關聯性可能不同於各控制站。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-266">Note that the relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="7ffa3-267">目前，存取控制器的指標姿勢才可以透過 MR 特有的輸入下列各節中所述的 API。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-267">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="7ffa3-268">Windows 特定的 Api (XR。WSA。輸入）</span><span class="sxs-lookup"><span data-stu-id="7ffa3-268">Windows-specific APIs (XR.WSA.Input)</span></span>

<span data-ttu-id="7ffa3-269">\**命名空間：\*\*\*UnityEngine.XR.WSA.Input*</span><span class="sxs-lookup"><span data-stu-id="7ffa3-269">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="7ffa3-270">**型別**:*InteractionManager*， *InteractionSourceState*， *InteractionSource*， *InteractionSourceProperties*， *InteractionSourceKind*， *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="7ffa3-270">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="7ffa3-271">若要取得在 Windows Mixed Reality 手動輸入 （HoloLens) 和動作控制器的詳細資訊，，您可以在其中選擇 Windows 專屬空間輸入的 Api 之下*UnityEngine.XR.WSA.Input*命名空間。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-271">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="7ffa3-272">這可讓您存取其他資訊，例如位置精確度或的來源類型，可讓您告訴雙手及控制站的位置。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-272">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="7ffa3-273">輪詢雙手及動作控制器的狀態</span><span class="sxs-lookup"><span data-stu-id="7ffa3-273">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="7ffa3-274">您可以針對每個互動來源 （手動或動作的控制器） 使用此畫面格的狀態來輪詢*GetCurrentReading*方法。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-274">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="7ffa3-275">每個*InteractionSourceState*您取得上一步 表示的互動來源在目前時間的時間。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-275">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="7ffa3-276">*InteractionSourceState*公開資訊，例如：</span><span class="sxs-lookup"><span data-stu-id="7ffa3-276">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="7ffa3-277">這[種類的按下](motion-controllers.md)發生 （選取/功能表/掌握/觸控板/搖）</span><span class="sxs-lookup"><span data-stu-id="7ffa3-277">Which [kinds of presses](motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="7ffa3-278">其他資料特定動作控制站，這類觸控板和/或搖桿的 XY 座標和接觸的狀態</span><span class="sxs-lookup"><span data-stu-id="7ffa3-278">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* <span data-ttu-id="7ffa3-279">若要知道來源是否為手形或移動控制站 InteractionSourceKind</span><span class="sxs-lookup"><span data-stu-id="7ffa3-279">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="7ffa3-280">正向預測的轉譯會帶來輪詢</span><span class="sxs-lookup"><span data-stu-id="7ffa3-280">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="7ffa3-281">輪詢互動來源資料是來自雙手及控制站，您取得帶來時轉寄預測帶來的此框架 photons 當觸達使用者的眼睛的時間。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-281">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="7ffa3-282">這些順向預測會帶來最適合用於**轉譯**控制器或保留物件的每個畫面格。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-282">These forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="7ffa3-283">如果您要為目標指定按下或釋放與控制站，這會是最精確，如果您使用歷程記錄的事件如下所述的 Api。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-283">If you are targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="7ffa3-284">您也可以取得順向預測前端姿勢這個目前的框架。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-284">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="7ffa3-285">因為與來源姿勢中，這是適用於**轉譯**的資料指標，雖然會最精確，如果您使用歷程記錄的事件如下所述的 Api 以指定按下或版本為目標。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-285">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="7ffa3-286">處理互動來源事件</span><span class="sxs-lookup"><span data-stu-id="7ffa3-286">Handling interaction source events</span></span>

<span data-ttu-id="7ffa3-287">若要處理輸入的事件，與其正確的歷程記錄姿勢資料發生時，您可以處理互動來源事件，而非輪詢。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-287">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="7ffa3-288">若要處理互動來源事件：</span><span class="sxs-lookup"><span data-stu-id="7ffa3-288">To handle interaction source events:</span></span>
* <span data-ttu-id="7ffa3-289">報名*InteractionManager*輸入的事件。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-289">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="7ffa3-290">每一種您感興趣的互動事件中，您需要訂閱。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-290">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* <span data-ttu-id="7ffa3-291">處理事件。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-291">Handle the event.</span></span> <span data-ttu-id="7ffa3-292">一旦您已訂閱互動事件，您會在適當的回呼。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-292">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="7ffa3-293">在  *SourcePressed*範例中，這將會偵測到來源後之前它會釋出或遺失。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-293">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

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

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="7ffa3-294">如何停止處理事件</span><span class="sxs-lookup"><span data-stu-id="7ffa3-294">How to stop handling an event</span></span>

<span data-ttu-id="7ffa3-295">您需要停止處理的事件，當您不再感興趣的事件，或已終結訂閱事件的物件。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-295">You need to stop handling an event when you are no longer interested in the event or you are destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="7ffa3-296">若要停止處理事件，您取消訂閱事件。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-296">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="7ffa3-297">互動來源事件清單</span><span class="sxs-lookup"><span data-stu-id="7ffa3-297">List of interaction source events</span></span>

<span data-ttu-id="7ffa3-298">可用的互動來源事件如下：</span><span class="sxs-lookup"><span data-stu-id="7ffa3-298">The available interaction source events are:</span></span>
* <span data-ttu-id="7ffa3-299">*InteractionSourceDetected* （來源成為使用中）</span><span class="sxs-lookup"><span data-stu-id="7ffa3-299">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="7ffa3-300">*InteractionSourceLost* （變成非使用中）</span><span class="sxs-lookup"><span data-stu-id="7ffa3-300">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="7ffa3-301">*InteractionSourcePressed* （點選、 按下按鈕，或"Select"玩具店）</span><span class="sxs-lookup"><span data-stu-id="7ffa3-301">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="7ffa3-302">*InteractionSourceReleased* （結尾點選、 按鈕釋放或 「 Select 」 您知道的結尾）</span><span class="sxs-lookup"><span data-stu-id="7ffa3-302">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="7ffa3-303">*InteractionSourceUpdated* （移動或變更某些狀態）</span><span class="sxs-lookup"><span data-stu-id="7ffa3-303">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="7ffa3-304">歷程記錄的目標會帶來最能精確符合在按下或發行的事件</span><span class="sxs-lookup"><span data-stu-id="7ffa3-304">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="7ffa3-305">稍早所述的輪詢 Api 可讓您的應用程式正向預測會帶來。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-305">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="7ffa3-306">這些預測會帶來最適合呈現的控制器或虛擬的掌上型物件時，未來會帶來並非最適合用於搜尋的目標，兩個索引鍵的原因：</span><span class="sxs-lookup"><span data-stu-id="7ffa3-306">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses are not optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="7ffa3-307">當使用者按下按鈕，控制站上時，可能會有約 20 毫秒的延遲無線透過藍牙之前，系統即會按。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-307">When the user presses a button on a controller, there can be about 20ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="7ffa3-308">接著，如果您使用順向預測的姿勢，那里會向前預測的另一個 10-20 毫秒套用至目標目前的框架 photons 當觸達使用者的眼睛的時間。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-308">Then, if you are using a forward-predicted pose, there would be another 10-20ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="7ffa3-309">這表示輪詢可讓您的來源姿勢，或標頭會造成也就是從使用者的前端和指針實際所在回發生在按下或發行的 30 40 毫秒正向。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-309">This means that polling gives you a source pose or head pose that is 30-40ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="7ffa3-310">HoloLens 手動輸入，雖然沒有任何無線傳輸的延遲，沒有類似的處理延遲，以偵測按。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-310">For HoloLens hand input, while there's no wireless transmission delay, there is a similar processing delay to detect the press.</span></span>

<span data-ttu-id="7ffa3-311">至正確的目標根據使用者的原意，手動或控制站的按下，您應該使用歷程記錄的來源姿勢或從該前端姿勢*InteractionSourcePressed*或*InteractionSourceReleased*輸入的事件。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-311">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="7ffa3-312">您可以按下的目標或發行來自使用者的大腦或其控制站的歷程記錄的姿勢資料：</span><span class="sxs-lookup"><span data-stu-id="7ffa3-312">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="7ffa3-313">發生在動作或控制器按時間前端的姿勢，它可以用於**目標**來判斷使用者的已[gazing](gaze.md)在：</span><span class="sxs-lookup"><span data-stu-id="7ffa3-313">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](gaze.md) at:</span></span>

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

* <span data-ttu-id="7ffa3-314">發生在當按下動作控制站時間來源姿勢，它可以用於**目標**來判斷哪些使用者指位於的控制站。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-314">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="7ffa3-315">這會發生按下控制器的狀態。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-315">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="7ffa3-316">如果您要轉譯控制器本身，您可以要求指標姿勢，而不是調整底框姿勢，以傳送目標的光跡從哪些使用者會考慮呈現控制器的自然提示：</span><span class="sxs-lookup"><span data-stu-id="7ffa3-316">If you are rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

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

### <a name="event-handlers-example"></a><span data-ttu-id="7ffa3-317">事件處理常式範例</span><span class="sxs-lookup"><span data-stu-id="7ffa3-317">Event handlers example</span></span>

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

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="7ffa3-318">高階複合筆勢 Api (GestureRecognizer)</span><span class="sxs-lookup"><span data-stu-id="7ffa3-318">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="7ffa3-319">\**命名空間：\*\*\*UnityEngine.XR.WSA.Input*</span><span class="sxs-lookup"><span data-stu-id="7ffa3-319">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="7ffa3-320">**型別**:*GestureRecognizer*， *GestureSettings*， *InteractionSourceKind*</span><span class="sxs-lookup"><span data-stu-id="7ffa3-320">**Types**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span></span>

<span data-ttu-id="7ffa3-321">您的應用程式，也可以識別較高層級的空間輸入的來源，點選，按住不放、 操作和瀏覽筆勢的複合筆勢。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-321">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation and Navigation gestures.</span></span> <span data-ttu-id="7ffa3-322">您可以將這些複合的筆勢辨識在兩者之間[手](gestures.md)並[動作控制器](motion-controllers.md)使用 GestureRecognizer。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-322">You can recognize these composite gestures across both [hands](gestures.md) and [motion controllers](motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="7ffa3-323">GestureRecognizer 上的每個動作事件會提供輸入為目標的前端光線 SourceKind，當時的事件。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-323">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="7ffa3-324">某些事件提供額外內容的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-324">Some events provide additional context specific information.</span></span>

<span data-ttu-id="7ffa3-325">有只擷取筆勢使用筆勢辨識器所需的幾個步驟：</span><span class="sxs-lookup"><span data-stu-id="7ffa3-325">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="7ffa3-326">建立新的筆勢辨識器</span><span class="sxs-lookup"><span data-stu-id="7ffa3-326">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="7ffa3-327">指定要監看的筆勢</span><span class="sxs-lookup"><span data-stu-id="7ffa3-327">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="7ffa3-328">訂閱事件，這些筆勢</span><span class="sxs-lookup"><span data-stu-id="7ffa3-328">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="7ffa3-329">開始擷取筆勢</span><span class="sxs-lookup"><span data-stu-id="7ffa3-329">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="7ffa3-330">建立新的筆勢辨識器</span><span class="sxs-lookup"><span data-stu-id="7ffa3-330">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="7ffa3-331">若要使用*GestureRecognizer*，您必須建立*GestureRecognizer*:</span><span class="sxs-lookup"><span data-stu-id="7ffa3-331">To use the *GestureRecognizer*, you must have created a *GestureRecognizer*:</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="7ffa3-332">指定要監看的筆勢</span><span class="sxs-lookup"><span data-stu-id="7ffa3-332">Specify which gestures to watch for</span></span>

<span data-ttu-id="7ffa3-333">指定您感興趣透過的筆勢*SetRecognizableGestures()*:</span><span class="sxs-lookup"><span data-stu-id="7ffa3-333">Specify which gestures you are interested in via *SetRecognizableGestures()*:</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="7ffa3-334">訂閱事件，這些筆勢</span><span class="sxs-lookup"><span data-stu-id="7ffa3-334">Subscribe to events for those gestures</span></span>

<span data-ttu-id="7ffa3-335">訂閱手勢您感興趣的事件。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-335">Subscribe to events for the gestures you are interested in.</span></span>

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
><span data-ttu-id="7ffa3-336">瀏覽和操作筆勢是互斥的執行個體上*GestureRecognizer*。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-336">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer*.</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="7ffa3-337">開始擷取筆勢</span><span class="sxs-lookup"><span data-stu-id="7ffa3-337">Start capturing gestures</span></span>

<span data-ttu-id="7ffa3-338">根據預設， *GestureRecognizer*不會監視輸入直到*StartCapturingGestures()* 呼叫。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-338">By default, a *GestureRecognizer* does not monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="7ffa3-339">很可能筆勢事件可能會產生後*StopCapturingGestures()* 若輸入執行之前框架則會呼叫所在*StopCapturingGestures()* 已處理。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-339">It is possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="7ffa3-340">*GestureRecognizer*是否筆勢實際發生的在 previou 畫面格期間是開啟或關閉因此很可靠地啟動及停止筆勢監視根據目標設為此框架的視線會記住。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-340">The *GestureRecognizer* will remember whether it was on or off during the previou frame in which the gesture actually occurred, and so it is reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="7ffa3-341">停止擷取筆勢</span><span class="sxs-lookup"><span data-stu-id="7ffa3-341">Stop capturing gestures</span></span>

<span data-ttu-id="7ffa3-342">若要停止建置手勢辨識：</span><span class="sxs-lookup"><span data-stu-id="7ffa3-342">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="7ffa3-343">移除的筆勢辨識器</span><span class="sxs-lookup"><span data-stu-id="7ffa3-343">Removing a gesture recognizer</span></span>

<span data-ttu-id="7ffa3-344">請務必從訂閱的事件取消訂閱，然後再終結*GestureRecognizer*物件。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-344">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="7ffa3-345">轉譯在 Unity 中的移動控制器模型</span><span class="sxs-lookup"><span data-stu-id="7ffa3-345">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="7ffa3-346">![動作控制器模型和屏障](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="7ffa3-346">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="7ffa3-347">*動作控制器模型和屏障*</span><span class="sxs-lookup"><span data-stu-id="7ffa3-347">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="7ffa3-348">若要轉譯符合實體的控制站，您的使用者會保存，並且清楚表達如不同按鈕按下您的應用程式中的動作控制站，您可以使用**MotionController prefab**在[混合實境工具組](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span><span class="sxs-lookup"><span data-stu-id="7ffa3-348">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="7ffa3-349">此 prefab 會從系統的安裝的動作控制器的驅動程式，以動態方式載入正確 glTF 模型，在執行階段。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-349">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="7ffa3-350">請務必以動態方式載入這些模型，而不是手動匯入它們在編輯器中，這樣您的應用程式會顯示實際的精確的 3D 模型，任何目前和未來的控制站，您的使用者可能會有。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-350">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="7ffa3-351">請遵循[開始使用](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)指示下載混合實境工具組，並將它新增至您的 Unity 專案。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-351">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="7ffa3-352">如果您更換使用相機*MixedRealityCameraParent* prefab 的快速入門步驟的一部分，您已就緒 ！</span><span class="sxs-lookup"><span data-stu-id="7ffa3-352">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="7ffa3-353">該 prefab 包含移動控制站的轉譯。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-353">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="7ffa3-354">否則，請新增*Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab*您從 [專案] 窗格在場景。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-354">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="7ffa3-355">您會想要新增為任何父物件的子系 prefab 您用來移動相機繞著時使用者 teleports 內場景，以便控制站附隨的使用者。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-355">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="7ffa3-356">如果您的應用程式並不包含 teleporting，只要新增 prefab 場景的根目錄。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-356">If your app does not involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="7ffa3-357">擲回物件</span><span class="sxs-lookup"><span data-stu-id="7ffa3-357">Throwing objects</span></span>

<span data-ttu-id="7ffa3-358">在虛擬實境中擲回物件是困難的問題，則一開始看起來似乎。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-358">Throwing objects in virtual reality is a harder problem then it may at first seem.</span></span> <span data-ttu-id="7ffa3-359">如同最實際根據互動，以預期的方式在遊戲會擲回時，它會立即一目暸然，並且中斷訓練活動。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-359">As with most physically based interactions, when throwing in game acts in an unexpected way, it is immediately obvious and breaks immersion.</span></span> <span data-ttu-id="7ffa3-360">我們花了一些時間來思考深如何代表實體上正確的擲回行為，並提供一些指導方針，啟用透過我們的平台，我們想要與您共用的更新。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-360">We have spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="7ffa3-361">您可以找到舉例來說，我們建議您如何實作擲回[此處](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-361">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="7ffa3-362">此範例會遵循下列四個的指導方針：</span><span class="sxs-lookup"><span data-stu-id="7ffa3-362">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="7ffa3-363">**使用控制器*速度*而不是位置**。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-363">**Use the controller’s *velocity* instead of position**.</span></span> <span data-ttu-id="7ffa3-364">在 Windows 的 11 月更新，我們引進了行為的變更在['近似' 位置追蹤狀態](motion-controllers.md#controller-tracking-state)。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-364">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="7ffa3-365">處於此狀態時，速度控制器的相關的資訊會繼續報告，只要我們相信它是高精確度，這通常是超過會保持高精確度的位置。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-365">When in this state, velocity information about the controller will continue to be reported for as long as we believe it is high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="7ffa3-366">**併入*角速度*控制站的**。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-366">**Incorporate the *angular velocity* of the controller**.</span></span> <span data-ttu-id="7ffa3-367">此邏輯都包含在`throwing.cs`檔案中`GetThrownObjectVelAngVel`上述連結的套件內的靜態方法：</span><span class="sxs-lookup"><span data-stu-id="7ffa3-367">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="7ffa3-368">因為角速度是節約，擲回的物件必須維持相同的 angular 速度，因為它會擲回目前有： `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="7ffa3-368">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="7ffa3-369">因為可能不在底框姿勢原點，可能有不同的速度的話，則的控制站在使用者的參照時，會擲回物件的中心的大量。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-369">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity then that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="7ffa3-370">以這種方式提供的物件的部分是大量的速度的擲回物件控制器原點為中心的中心的即時略微相關速度。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-370">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="7ffa3-371">此略微相關的速度是物件的角速度控制站，與代表控制器原點及中央的大型的擲回之間的距離的向量的交叉乘積。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-371">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. <span data-ttu-id="7ffa3-372">擲回總數速度，因此是物件的控制站的速度和此略微相關的速度的總和： `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="7ffa3-372">The total velocity of the thrown object is thus the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="7ffa3-373">**密切注意*時間*我們可以在其中套用速度**。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-373">**Pay close attention to the *time* at which we apply the velocity**.</span></span> <span data-ttu-id="7ffa3-374">按下按鈕時，可能需要針對該事件，以反昇，以透過藍芽作業系統最多 20 毫秒。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-374">When a button is pressed, it can take up to 20ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="7ffa3-375">這表示，如果未按下按下的輪詢從控制器狀態變更或控制站的姿勢資訊您開始之前的狀態這項變更將相反的情況，會。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-375">This means that if you poll for a controller state change from pressed to not pressed or vice versa, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="7ffa3-376">此外，以反映在框架將會顯示在未來可能在多個然後 20 毫秒的時間可能姿勢向前預測我們輪詢 API 所提供的控制器姿勢。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-376">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more then 20ms in the future.</span></span> <span data-ttu-id="7ffa3-377">這適用於*轉譯*持有的物件，但複合的時間問題*目標*物件，我們目前為止計算軌跡使用者發行其擲回。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-377">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released their throw.</span></span> <span data-ttu-id="7ffa3-378">幸運的是，使用年 11 月更新時，Unity 事件何時*InteractionSourcePressed*或*InteractionSourceReleased*傳送，狀態包括歷程記錄的姿勢資料從備份時的按鈕已實際已按下或發行。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-378">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was actually pressed or released.</span></span>  <span data-ttu-id="7ffa3-379">若要取得最精確的控制站呈現和期間擲回的控制站為目標，您正確地必須適當地使用輪詢和事件處理:</span><span class="sxs-lookup"><span data-stu-id="7ffa3-379">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="7ffa3-380">針對**控制器轉譯**每個畫面中，您的應用程式應該放置控制器的*GameObject*轉寄預測控制站會造成目前的框架 photon 時間。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-380">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="7ffa3-381">您可以取得這項資料從輪詢的 Api，例如的 Unity *[XR。InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* 或是 *[XR。WSA。Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-381">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span></span>
   * <span data-ttu-id="7ffa3-382">針對**控制器目標**在按下或版本中，您的應用程式應該 raycast 並計算滴下根據歷程記錄的控制器姿勢，按下] 或 [發行事件。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-382">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="7ffa3-383">您收到這項資料從 Unity 事件處理 Api，例如 *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-383">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span></span>
* <span data-ttu-id="7ffa3-384">**使用調整底框姿勢**。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-384">**Use the grip pose**.</span></span> <span data-ttu-id="7ffa3-385">角速度和速度會報告相對於底框姿勢，而不是指標姿勢。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-385">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="7ffa3-386">擲回將繼續改善未來的 Windows 更新，並取得更多有關它以下時，您可以預期。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-386">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="accelerate-development-with-mixed-reality-toolkit"></a><span data-ttu-id="7ffa3-387">利用混合實境 Toolkit 加速開發</span><span class="sxs-lookup"><span data-stu-id="7ffa3-387">Accelerate development with Mixed Reality Toolkit</span></span>

<span data-ttu-id="7ffa3-388">有關於 InputManager 和 MotionController Unity 中的兩個範例場景。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-388">There are two example scenes about InputManager and MotionController in Unity.</span></span> <span data-ttu-id="7ffa3-389">透過這些場景中，您可以了解如何使用 MRTK 的 InputManager 和從動作控制器按鈕存取的資料處理事件。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-389">Through these scenes, you can learn how to use MRTK's InputManager and access data handle events from the motion controller buttons.</span></span>

- [<span data-ttu-id="7ffa3-390">HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity</span><span class="sxs-lookup"><span data-stu-id="7ffa3-390">HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity)
- [<span data-ttu-id="7ffa3-391">HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity</span><span class="sxs-lookup"><span data-stu-id="7ffa3-391">HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity)
- [<span data-ttu-id="7ffa3-392">讀我檔案的技術詳細資料</span><span class="sxs-lookup"><span data-stu-id="7ffa3-392">Technical details README File</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input)

<span data-ttu-id="7ffa3-393">![輸入的範例 MRTK 場景](images/MRTK_ExampleScene_Input.png)</span><span class="sxs-lookup"><span data-stu-id="7ffa3-393">![Input example scenes in MRTK](images/MRTK_ExampleScene_Input.png)</span></span><br>
<span data-ttu-id="7ffa3-394">*輸入的範例 MRTK 場景*</span><span class="sxs-lookup"><span data-stu-id="7ffa3-394">*Input example scenes in MRTK*</span></span>

### <a name="automatic-scene-setup"></a><span data-ttu-id="7ffa3-395">自動的場景設定</span><span class="sxs-lookup"><span data-stu-id="7ffa3-395">Automatic scene setup</span></span>

<span data-ttu-id="7ffa3-396">當您匯入[MRTK 發行 Unity 套件](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)或從專案複製[GitHub 存放庫](https://github.com/Microsoft/MixedRealityToolkit-Unity)，您要在 Unity 中尋找新的功能表 ' 混合實境 Toolkit'。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-396">When you import [MRTK release Unity packages](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) or clone the project from the [GitHub repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), you are going to find a new menu 'Mixed Reality Toolkit' in Unity.</span></span> <span data-ttu-id="7ffa3-397">在 [設定] 功能表上，您會看到功能表 [適用於混合實境場景設定]。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-397">Under 'Configure' menu, you will see the menu 'Apply Mixed Reality Scene Settings'.</span></span> <span data-ttu-id="7ffa3-398">當您按一下它時，它會移除預設相機，並新增基本元件- [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab)， [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab)，並[DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab)。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-398">When you click it, it removes the default camera and adds foundational components - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), and [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span></span>

<span data-ttu-id="7ffa3-399">![MRTK 場景設定功能表](images/MRTK_Input_Menu.png)</span><span class="sxs-lookup"><span data-stu-id="7ffa3-399">![MRTK Menu for scene setup](images/MRTK_Input_Menu.png)</span></span><br>
<span data-ttu-id="7ffa3-400">*MRTK 場景設定功能表*</span><span class="sxs-lookup"><span data-stu-id="7ffa3-400">*MRTK Menu for scene setup*</span></span>

<span data-ttu-id="7ffa3-401">![自動的場景中 MRTK 的安裝程式](images/MRTK_HowTo_Input1.png)</span><span class="sxs-lookup"><span data-stu-id="7ffa3-401">![Automatic scene setup in MRTK](images/MRTK_HowTo_Input1.png)</span></span><br>
<span data-ttu-id="7ffa3-402">*自動的場景中 MRTK 的安裝程式*</span><span class="sxs-lookup"><span data-stu-id="7ffa3-402">*Automatic scene setup in MRTK*</span></span>

### <a name="mixedrealitycamera-prefab"></a><span data-ttu-id="7ffa3-403">MixedRealityCamera prefab</span><span class="sxs-lookup"><span data-stu-id="7ffa3-403">MixedRealityCamera prefab</span></span>

<span data-ttu-id="7ffa3-404">您可以手動新增這些從 [專案] 面板。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-404">You can also manually add these from the project panel.</span></span> <span data-ttu-id="7ffa3-405">您可以找到 prefabs 這些元件。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-405">You can find these components as prefabs.</span></span> <span data-ttu-id="7ffa3-406">當您搜尋**MixedRealityCamera**，您將能夠看到兩個不同的數位相機 prefabs。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-406">When you search **MixedRealityCamera**, you will be able to see two different camera prefabs.</span></span> <span data-ttu-id="7ffa3-407">差別在於**MixedRealityCamera**才相機 prefab 而**MixedRealityCameraParent**包含沈浸式耳機，例如屏障，動作的其他元件控制器和，界限。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-407">The difference is, **MixedRealityCamera** is the camera only prefab whereas, **MixedRealityCameraParent** includes additional components for the immersive headsets such as Teleportation, Motion Controller and, Boundary.</span></span>

<span data-ttu-id="7ffa3-408">![在 MRTK 相機 prefabs](images/MRTK_HowTo_Input2.png)</span><span class="sxs-lookup"><span data-stu-id="7ffa3-408">![Camera prefabs in MRTK](images/MRTK_HowTo_Input2.png)</span></span><br>
<span data-ttu-id="7ffa3-409">*在 MRTK 相機 prefabs*</span><span class="sxs-lookup"><span data-stu-id="7ffa3-409">*Camera prefabs in MRTK*</span></span>

<span data-ttu-id="7ffa3-410">**MixedRealtyCamera**支援 HoloLens 和沈浸式耳機。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-410">**MixedRealtyCamera** supports both HoloLens and immersive headset.</span></span> <span data-ttu-id="7ffa3-411">它會偵測到的裝置類型，並最佳化清除旗標和天空盒等屬性。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-411">It detects the device type and optimizes the properties such as clear flags and Skybox.</span></span> <span data-ttu-id="7ffa3-412">以下您可以找到一些有用的屬性，您可以自訂游標，移動控制器模型，例如自訂和樓層。</span><span class="sxs-lookup"><span data-stu-id="7ffa3-412">Below you can find some of the useful properties you can customize such as custom Cursor, Motion Controller models, and Floor.</span></span>

<span data-ttu-id="7ffa3-413">![屬性的動作控制站中，資料指標和樓層](images/MRTK_HowTo_Input3.png)</span><span class="sxs-lookup"><span data-stu-id="7ffa3-413">![Properties for the Motion controller, Cursor and Floor](images/MRTK_HowTo_Input3.png)</span></span><br>
<span data-ttu-id="7ffa3-414">*屬性的動作控制站中，資料指標和樓層*</span><span class="sxs-lookup"><span data-stu-id="7ffa3-414">*Properties for the Motion controller, Cursor and Floor*</span></span>

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="7ffa3-415">依照本教學課程</span><span class="sxs-lookup"><span data-stu-id="7ffa3-415">Follow along with tutorials</span></span>

<span data-ttu-id="7ffa3-416">逐步教學課程中，使用更詳細的自訂範例，可在混合實境 Academy:</span><span class="sxs-lookup"><span data-stu-id="7ffa3-416">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="7ffa3-417">MR 輸入 211:筆勢</span><span class="sxs-lookup"><span data-stu-id="7ffa3-417">MR Input 211: Gesture</span></span>](holograms-211.md)
- [<span data-ttu-id="7ffa3-418">MR 輸入 213:動作控制站</span><span class="sxs-lookup"><span data-stu-id="7ffa3-418">MR Input 213: Motion controllers</span></span>](mixed-reality-213.md)

<span data-ttu-id="7ffa3-419">[![MR 輸入 213-動作控制站](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="7ffa3-419">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="7ffa3-420">*MR 輸入 213-動作控制站*</span><span class="sxs-lookup"><span data-stu-id="7ffa3-420">*MR Input 213 - Motion controller*</span></span>

## <a name="see-also"></a><span data-ttu-id="7ffa3-421">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ffa3-421">See also</span></span>

* [<span data-ttu-id="7ffa3-422">筆勢</span><span class="sxs-lookup"><span data-stu-id="7ffa3-422">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="7ffa3-423">動作控制站</span><span class="sxs-lookup"><span data-stu-id="7ffa3-423">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="7ffa3-424">UnityEngine.XR.WSA.Input</span><span class="sxs-lookup"><span data-stu-id="7ffa3-424">UnityEngine.XR.WSA.Input</span></span>](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [<span data-ttu-id="7ffa3-425">UnityEngine.XR.InputTracking</span><span class="sxs-lookup"><span data-stu-id="7ffa3-425">UnityEngine.XR.InputTracking</span></span>](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [<span data-ttu-id="7ffa3-426">InteractionInputSource.cs MixedRealityToolkit Unity 中</span><span class="sxs-lookup"><span data-stu-id="7ffa3-426">InteractionInputSource.cs in MixedRealityToolkit-Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/InputSources/InteractionInputSource.cs)
