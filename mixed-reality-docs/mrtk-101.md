---
title: MRTK 101-如何使用混合現實工具組 Unity 進行基本互動（HoloLens 2、HoloLens、Windows Mixed Reality、Open VR）
description: 如何使用混合現實工具組 Unity 進行基本互動（HoloLens 2、HoloLens、Windows Mixed Reality、Open VR）
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens，MRTK，混合現實工具組，Windows Mixed Reality，設計，範例應用程式，控制項
ms.openlocfilehash: ad9d2755522c2610ae051fa61f96605e49404d2d
ms.sourcegitcommit: 5054f5c23965ce56599cb29ac9d9c6e48812dabd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2020
ms.locfileid: "75623501"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a><span data-ttu-id="ded99-104">MRTK 101：如何使用混合現實工具組 Unity 進行基本互動（HoloLens 2、HoloLens、Windows Mixed Reality、Open VR）</span><span class="sxs-lookup"><span data-stu-id="ded99-104">MRTK 101: How to use Mixed Reality Toolkit Unity for Basic Interactions (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)</span></span>

![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="ded99-106">瞭解如何使用 MRTK 來達到混合現實中一些最普遍使用的常見互動模式。</span><span class="sxs-lookup"><span data-stu-id="ded99-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="ded99-107">如何在 Unity 編輯器中模擬輸入互動？</span><span class="sxs-lookup"><span data-stu-id="ded99-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="ded99-108">如何抓取和移動物件？</span><span class="sxs-lookup"><span data-stu-id="ded99-108">How to grab and move an object?</span></span>
- <span data-ttu-id="ded99-109">如何調整物件大小？</span><span class="sxs-lookup"><span data-stu-id="ded99-109">How to resize an object?</span></span>
- <span data-ttu-id="ded99-110">如何以精確度移動或旋轉物件？</span><span class="sxs-lookup"><span data-stu-id="ded99-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="ded99-111">如何讓物件回應輸入事件？</span><span class="sxs-lookup"><span data-stu-id="ded99-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="ded99-112">如何新增視覺效果意見反應？</span><span class="sxs-lookup"><span data-stu-id="ded99-112">How to add visual feedback?</span></span>
- <span data-ttu-id="ded99-113">如何新增音訊意見反應？</span><span class="sxs-lookup"><span data-stu-id="ded99-113">How to add audio feedback?</span></span>
- <span data-ttu-id="ded99-114">如何使用 HoloLens 2 樣式按鈕 prefabs？</span><span class="sxs-lookup"><span data-stu-id="ded99-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="ded99-115">如何讓物件符合您的需要？</span><span class="sxs-lookup"><span data-stu-id="ded99-115">How to make an object follow you?</span></span>
- <span data-ttu-id="ded99-116">如何讓物件臉部？</span><span class="sxs-lookup"><span data-stu-id="ded99-116">How to make an object face you?</span></span>

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a><span data-ttu-id="ded99-117">如何在 Unity 編輯器中模擬輸入互動？</span><span class="sxs-lookup"><span data-stu-id="ded99-117">How to simulate input interactions in Unity editor?</span></span>
<span data-ttu-id="ded99-118">MRTK 支援編輯器內的輸入模擬。</span><span class="sxs-lookup"><span data-stu-id="ded99-118">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="ded99-119">只要按一下 Unity 的 [播放] 按鈕，即可執行場景。</span><span class="sxs-lookup"><span data-stu-id="ded99-119">Simply run your scene by clicking Unity's play button.</span></span> <span data-ttu-id="ded99-120">使用這些金鑰來模擬輸入。</span><span class="sxs-lookup"><span data-stu-id="ded99-120">Use these keys to simulate input.</span></span>
<span data-ttu-id="ded99-121">按 W、A、S、D 鍵來移動相機。</span><span class="sxs-lookup"><span data-stu-id="ded99-121">Press W, A, S, D keys to move the camera.</span></span>
<span data-ttu-id="ded99-122">按住滑鼠右鍵並移動滑鼠來尋找。</span><span class="sxs-lookup"><span data-stu-id="ded99-122">Hold the right mouse button and move the mouse to look around.</span></span>
<span data-ttu-id="ded99-123">若要啟動模擬的手，請按空格鍵（右手）或左 Shift 鍵（左手邊），將模擬的手放在視圖中，按 T 或 Y 鍵以旋轉模擬手，按 Q 或 E （水準）/R 或 F （垂直）</span><span class="sxs-lookup"><span data-stu-id="ded99-123">To bring up the simulated hands, press Space bar(Right hand) or left Shift key(Left hand) To keep simulated hands in the view, press T or Y key To rotate simulated hands, press Q or E(horizontal) / R or F(vertical)</span></span>

- [<span data-ttu-id="ded99-124">在 MRTK 檔中深入瞭解輸入模擬</span><span class="sxs-lookup"><span data-stu-id="ded99-124">Learn more about Input Simulation in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a><span data-ttu-id="ded99-125">如何抓取和移動物件？</span><span class="sxs-lookup"><span data-stu-id="ded99-125">How to grab and move an object?</span></span>
<span data-ttu-id="ded99-126">若要讓物件 grabbable，請指派這兩個腳本： ManipulationHandler.cs 和 NearInteractionGrabbable （適用于具有明確表達之手寫輸入的直接抓取） ManipulationHandler 同時支援近乎和遠處的互動。</span><span class="sxs-lookup"><span data-stu-id="ded99-126">To make an object grabbable, assign these two scripts: ManipulationHandler.cs and NearInteractionGrabbable.cs(for direct grab with articulated hand tracking input) ManipulationHandler supports both near and far interactions.</span></span> <span data-ttu-id="ded99-127">您可以使用 HoloLens 2 的明確的手勢追蹤輸入（接近）、手中的光線（遠）、運動控制器的橫樑（遠）、HoloLens 注視游標 & 按下（遠）來抓取和移動物件。</span><span class="sxs-lookup"><span data-stu-id="ded99-127">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), HoloLens gaze cursor & air-tap(far).</span></span>

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a><span data-ttu-id="ded99-128">如何調整物件大小？</span><span class="sxs-lookup"><span data-stu-id="ded99-128">How to resize an object?</span></span>
<span data-ttu-id="ded99-129">ManipulationHandler.cs 支援兩個右手的縮放/旋轉。</span><span class="sxs-lookup"><span data-stu-id="ded99-129">ManipulationHandler.cs supports two-handed scale/rotation.</span></span> <span data-ttu-id="ded99-130">這適用于各種輸入類型，例如 HoloLens 2 的清楚手寫輸入、HoloLens 1 的注視 + 手勢輸入，以及 Windows Mixed Reality 沉浸式耳機的動作控制器輸入。</span><span class="sxs-lookup"><span data-stu-id="ded99-130">This works with various input types such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="ded99-131">若要深入瞭解如何操作處理常式，請參閱 MRTK 檔</span><span class="sxs-lookup"><span data-stu-id="ded99-131">Learn more about Manipulation Handler in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="ded99-132">如何以精確度移動或旋轉物件？</span><span class="sxs-lookup"><span data-stu-id="ded99-132">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="ded99-133">將 BoundingBox.cs 指派給物件，以使用周框方塊，這是用來縮放和旋轉物件的介面。</span><span class="sxs-lookup"><span data-stu-id="ded99-133">Assign BoundingBox.cs to an object to use Bounding Box which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="ded99-134">根據預設，它會顯示 HoloLens 1 樣式藍色控點和電線。</span><span class="sxs-lookup"><span data-stu-id="ded99-134">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="ded99-135">若要使用 HoloLens 2 樣式的鄰近動畫控點，您必須指派 prefabs 和材質。</span><span class="sxs-lookup"><span data-stu-id="ded99-135">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> <span data-ttu-id="ded99-136">如需設定詳細資料，請參閱周[框方塊檔](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)和 BoundingBoxExamples 場景。</span><span class="sxs-lookup"><span data-stu-id="ded99-136">Please refer to [Bounding Box documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) and the BoundingBoxExamples.unity scene for the configuration details.</span></span>

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [<span data-ttu-id="ded99-137">深入瞭解 MRTK 檔中的周框方塊</span><span class="sxs-lookup"><span data-stu-id="ded99-137">Learn more about Bounding Box in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a><span data-ttu-id="ded99-138">如何讓物件回應輸入事件？</span><span class="sxs-lookup"><span data-stu-id="ded99-138">How to make an object respond to input events?</span></span>
<span data-ttu-id="ded99-139">將 PointerHandler.cs 指派給物件。</span><span class="sxs-lookup"><span data-stu-id="ded99-139">Assign PointerHandler.cs to an object.</span></span> <span data-ttu-id="ded99-140">在偵測器中，您可以使用事件 OnPointerDown （）、OnPointerUp （）、OnPointerClicked （）、OnPointerDragged （），以在腳本中使用這些事件，並執行 IMixedRealityPointerHandler。</span><span class="sxs-lookup"><span data-stu-id="ded99-140">In the inspector, you will be able to use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement IMixedRealityPointerHandler.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="ded99-141">在 MRTK 檔中深入瞭解輸入系統</span><span class="sxs-lookup"><span data-stu-id="ded99-141">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="ded99-142">如何新增視覺效果意見反應？</span><span class="sxs-lookup"><span data-stu-id="ded99-142">How to add visual feedback?</span></span>
<span data-ttu-id="ded99-143">將 Interactable.cs 指派給物件。</span><span class="sxs-lookup"><span data-stu-id="ded99-143">Assign Interactable.cs to an object.</span></span> <span data-ttu-id="ded99-144">在偵測器中，建立新的主題。</span><span class="sxs-lookup"><span data-stu-id="ded99-144">In the inspector, create a new theme.</span></span> <span data-ttu-id="ded99-145">您可以使用可互動的主題設定檔，輕鬆地在所有可用的輸入互動狀態中新增視覺效果的意見反應。</span><span class="sxs-lookup"><span data-stu-id="ded99-145">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="ded99-146">可互動提供各種類型的主題，包括著色器主題，可讓您控制每個互動狀態的著色器屬性。</span><span class="sxs-lookup"><span data-stu-id="ded99-146">Interactable provides various types of themes including the shader theme which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="ded99-147">在 MRTK 檔中深入瞭解可互動</span><span class="sxs-lookup"><span data-stu-id="ded99-147">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="ded99-148">視覺化意見反應的另一個重要建立區塊是 MRTK 標準著色器。</span><span class="sxs-lookup"><span data-stu-id="ded99-148">Another important building block for visual feedback is the MRTK Standard Shader.</span></span> <span data-ttu-id="ded99-149">有了 MRTK Standard 著色器，您就可以輕鬆地加入視覺效果的意見反應，例如暫留光線和近光源。</span><span class="sxs-lookup"><span data-stu-id="ded99-149">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="ded99-150">由於 MRTK 標準著色器執行的計算比 Unity Standard 著色器少很多，因此您可以建立高效能的體驗。</span><span class="sxs-lookup"><span data-stu-id="ded99-150">Since MRTK Standard shader performs significantly less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="ded99-151">建立新的材料，然後選取著色器的混合現實工具組 > 標準。</span><span class="sxs-lookup"><span data-stu-id="ded99-151">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="ded99-152">或者，您可以挑選其中一個使用 MRTK 標準著色器的現有材質。</span><span class="sxs-lookup"><span data-stu-id="ded99-152">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="ded99-153">在 MRTK 檔中深入瞭解 MRTK 標準著色器</span><span class="sxs-lookup"><span data-stu-id="ded99-153">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="ded99-154">如何新增音訊意見反應？</span><span class="sxs-lookup"><span data-stu-id="ded99-154">How to add audio feedback?</span></span>
<span data-ttu-id="ded99-155">將 Spatialize 新增至物件。</span><span class="sxs-lookup"><span data-stu-id="ded99-155">Add AudioSource to an object.</span></span> <span data-ttu-id="ded99-156">然後，在公開輸入事件（例如 Interactable.cs 或 PointerHandler.cs）的腳本中，將物件指派給事件，然後選取 [Spatialize PlayOneShot （）]。</span><span class="sxs-lookup"><span data-stu-id="ded99-156">Then, in the scripts that exposes input events(e.g. Interactable.cs or PointerHandler.cs), assign the object to the event and select AudioSource.PlayOneShot().</span></span> <span data-ttu-id="ded99-157">您可以使用您的音訊剪輯，或從 MRTK 的音訊資產中選擇它。</span><span class="sxs-lookup"><span data-stu-id="ded99-157">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a><span data-ttu-id="ded99-158">如何使用 HoloLens 2 樣式按鈕 prefabs？</span><span class="sxs-lookup"><span data-stu-id="ded99-158">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="ded99-159">MRTK 提供各種類型的 HoloLens 2 shell （OS）樣式按鈕。</span><span class="sxs-lookup"><span data-stu-id="ded99-159">MRTK provides various types of HoloLens 2's shell(OS) style buttons.</span></span> <span data-ttu-id="ded99-160">它提供複雜的視覺效果意見反應，例如 [近光源]、[壓縮] 方塊和 [按鈕] 介面上的 ripple 效果。</span><span class="sxs-lookup"><span data-stu-id="ded99-160">It provides sophisticated visual feedbacks such as proximity light, compressing box, and a ripple effect on the button surface.</span></span>

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="ded99-161">只要將其中一個 HoloLens 2 樣式的 pressable 按鈕拖放到您的場景中即可。</span><span class="sxs-lookup"><span data-stu-id="ded99-161">Simply drag and drop one of the HoloLens 2 style pressable button prefab into your scene.</span></span> <span data-ttu-id="ded99-162">Prefab 會使用上面引進的 Interactable.cs。</span><span class="sxs-lookup"><span data-stu-id="ded99-162">The prefab uses Interactable.cs which is introduced above.</span></span> <span data-ttu-id="ded99-163">您可以在可互動中使用公開的事件（例如 OnClick （））來觸發動作。</span><span class="sxs-lookup"><span data-stu-id="ded99-163">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="ded99-164">深入瞭解 MRTK 檔中的按鈕 prefabs</span><span class="sxs-lookup"><span data-stu-id="ded99-164">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a><span data-ttu-id="ded99-165">如何讓物件符合您的需要？</span><span class="sxs-lookup"><span data-stu-id="ded99-165">How to make an object follow you?</span></span>
<span data-ttu-id="ded99-166">將 RadialView.cs 腳本指派給物件。</span><span class="sxs-lookup"><span data-stu-id="ded99-166">Assign RadialView.cs script to an object.</span></span> <span data-ttu-id="ded99-167">它是規劃求解腳本系列的一部分，可讓您在3D 空間中達到各種類型的物件定位。</span><span class="sxs-lookup"><span data-stu-id="ded99-167">It is part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="ded99-168">SolverHandler.cs 將會自動新增。</span><span class="sxs-lookup"><span data-stu-id="ded99-168">SolverHandler.cs will be automatically added.</span></span>
<span data-ttu-id="ded99-169">以下是 RadialView 設定的範例，以達到「延遲遵循」標記的行為，就像是 HoloLens shell 中的 [開始] 功能表。</span><span class="sxs-lookup"><span data-stu-id="ded99-169">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="ded99-170">您可以指定最小/最大距離和最小/最大視圖度。</span><span class="sxs-lookup"><span data-stu-id="ded99-170">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="ded99-171">下列範例顯示在15°內，將物件放置在 0.4 m 和 0.8 m 的範圍之間。</span><span class="sxs-lookup"><span data-stu-id="ded99-171">The example below shows positioning the object between 0.4m and 0.8m range within 15°.</span></span> <span data-ttu-id="ded99-172">調整 Lerp 時間值，讓位置更新的速度更快或更慢。</span><span class="sxs-lookup"><span data-stu-id="ded99-172">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="ded99-173">在 MRTK 檔中深入瞭解解析器</span><span class="sxs-lookup"><span data-stu-id="ded99-173">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a><span data-ttu-id="ded99-174">如何讓物件臉部？</span><span class="sxs-lookup"><span data-stu-id="ded99-174">How to make an object face you?</span></span>
<span data-ttu-id="ded99-175">將 Billboard.cs 腳本指派給物件。</span><span class="sxs-lookup"><span data-stu-id="ded99-175">Assign Billboard.cs script to an object.</span></span> <span data-ttu-id="ded99-176">無論您的位置為何，它一律會面對您。</span><span class="sxs-lookup"><span data-stu-id="ded99-176">It will always face you, regardless of your position.</span></span> <span data-ttu-id="ded99-177">您可以指定 [pivot 軸] 選項。</span><span class="sxs-lookup"><span data-stu-id="ded99-177">You can specify the pivot axis option.</span></span>

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="ded99-178">準備好建立混合現實的絕佳體驗嗎？</span><span class="sxs-lookup"><span data-stu-id="ded99-178">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="ded99-179">請流覽下列頁面，並深入瞭解 MRTK 和 mixed reality。</span><span class="sxs-lookup"><span data-stu-id="ded99-179">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="ded99-180">關於作者</span><span class="sxs-lookup"><span data-stu-id="ded99-180">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="ded99-181"><b>盾 Yoon 公園</b></span><span class="sxs-lookup"><span data-stu-id="ded99-181"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="ded99-182">UX 設計工具 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="ded99-182">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="ded99-183">請參閱</span><span class="sxs-lookup"><span data-stu-id="ded99-183">See also</span></span>

* [<span data-ttu-id="ded99-184">混合現實工具組-Unity （MRTK） GitHub</span><span class="sxs-lookup"><span data-stu-id="ded99-184">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="ded99-185">MRTK 檔入口網站</span><span class="sxs-lookup"><span data-stu-id="ded99-185">MRTK Documentation Portal</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="ded99-186">使用 MRTK 消費者入門</span><span class="sxs-lookup"><span data-stu-id="ded99-186">Getting Started with MRTK</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="ded99-187">HoloToolkit 至 MRTK 移植指導方針</span><span class="sxs-lookup"><span data-stu-id="ded99-187">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
