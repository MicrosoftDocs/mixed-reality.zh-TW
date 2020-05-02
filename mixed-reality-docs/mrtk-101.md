---
title: MRTK 101 - 如何使用混合實境工具組 Unity 進行基本互動 (HoloLens 2、HoloLens、Windows Mixed Reality、Open VR)
description: 如何使用混合實境工具組 Unity 進行基本互動 (HoloLens 2、HoloLens、Windows Mixed Reality、Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, 混合實境工具組, Windows Mixed Reality, 設計, 範例應用程式, 控制項
ms.localizationpriority: high
ms.openlocfilehash: 4564e7a0c6a717452effacae2587461fe283cf0b
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "79028316"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a><span data-ttu-id="8f9c3-104">MRTK 101：如何使用混合實境工具組 Unity 進行基本互動 (HoloLens 2、HoloLens、Windows Mixed Reality、Open VR)</span><span class="sxs-lookup"><span data-stu-id="8f9c3-104">MRTK 101: How to use Mixed Reality Toolkit Unity for Basic Interactions (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)</span></span>

![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="8f9c3-106">了解如何使用 MRTK 來實現混合實境中一些最廣泛使用的常見互動模式。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="8f9c3-107">如何在 Unity 編輯器中模擬輸入互動？</span><span class="sxs-lookup"><span data-stu-id="8f9c3-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="8f9c3-108">如何抓取和移動物件？</span><span class="sxs-lookup"><span data-stu-id="8f9c3-108">How to grab and move an object?</span></span>
- <span data-ttu-id="8f9c3-109">如何調整物件大小？</span><span class="sxs-lookup"><span data-stu-id="8f9c3-109">How to resize an object?</span></span>
- <span data-ttu-id="8f9c3-110">如何精確地移動或旋轉物件？</span><span class="sxs-lookup"><span data-stu-id="8f9c3-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="8f9c3-111">如何讓物件回應輸入事件？</span><span class="sxs-lookup"><span data-stu-id="8f9c3-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="8f9c3-112">如何新增視覺回饋？</span><span class="sxs-lookup"><span data-stu-id="8f9c3-112">How to add visual feedback?</span></span>
- <span data-ttu-id="8f9c3-113">如何新增音訊回饋？</span><span class="sxs-lookup"><span data-stu-id="8f9c3-113">How to add audio feedback?</span></span>
- <span data-ttu-id="8f9c3-114">如何使用 HoloLens 2 樣式的按鈕 Prefab？</span><span class="sxs-lookup"><span data-stu-id="8f9c3-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="8f9c3-115">如何讓物件跟著您移動？</span><span class="sxs-lookup"><span data-stu-id="8f9c3-115">How to make an object follow you?</span></span>
- <span data-ttu-id="8f9c3-116">如何讓物件面對您？</span><span class="sxs-lookup"><span data-stu-id="8f9c3-116">How to make an object face you?</span></span>

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a><span data-ttu-id="8f9c3-117">如何在 Unity 編輯器中模擬輸入互動？</span><span class="sxs-lookup"><span data-stu-id="8f9c3-117">How to simulate input interactions in Unity editor?</span></span>
<span data-ttu-id="8f9c3-118">MRTK 支援編輯器內的輸入模擬。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-118">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="8f9c3-119">只要按一下 Unity 的開始遊戲按鈕，即可執行場景。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-119">Simply run your scene by clicking Unity's play button.</span></span> <span data-ttu-id="8f9c3-120">使用這些按鍵來模擬輸入。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-120">Use these keys to simulate input.</span></span>
<span data-ttu-id="8f9c3-121">按 W、A、S、D 鍵來移動相機。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-121">Press W, A, S, D keys to move the camera.</span></span>
<span data-ttu-id="8f9c3-122">按住滑鼠右鍵並移動滑鼠來瀏覽。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-122">Hold the right mouse button and move the mouse to look around.</span></span>
<span data-ttu-id="8f9c3-123">若要顯示模擬的手部，請按空格鍵 (右手) 或左 Shift 鍵 (左手)；若要將模擬的手部放入視圖中，請按 T 或 Y 鍵；若要旋轉模擬的手部，請按 Q 或 E (水平) / R 或 F (垂直)</span><span class="sxs-lookup"><span data-stu-id="8f9c3-123">To bring up the simulated hands, press Space bar(Right hand) or left Shift key(Left hand) To keep simulated hands in the view, press T or Y key To rotate simulated hands, press Q or E(horizontal) / R or F(vertical)</span></span>

- [<span data-ttu-id="8f9c3-124">在 MRTK 文件中深入了解輸入模擬</span><span class="sxs-lookup"><span data-stu-id="8f9c3-124">Learn more about Input Simulation in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a><span data-ttu-id="8f9c3-125">如何抓取和移動物件？</span><span class="sxs-lookup"><span data-stu-id="8f9c3-125">How to grab and move an object?</span></span>
<span data-ttu-id="8f9c3-126">若要讓物件可供抓取，請指派這兩個指令碼：ManipulationHandler.cs 和 NearInteractionGrabbable.cs (適用於以接合手部追蹤輸入進行直接抓取) ManipulationHandler 可支援近處和遠處的互動。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-126">To make an object grabbable, assign these two scripts: ManipulationHandler.cs and NearInteractionGrabbable.cs(for direct grab with articulated hand tracking input) ManipulationHandler supports both near and far interactions.</span></span> <span data-ttu-id="8f9c3-127">您可以使用 HoloLens 2 的接合手部追蹤輸入 (近處)、手部射線 (遠處)、運動控制器的光束 (遠處)、HoloLens 注視游標與空間點選 (遠處) 來抓取和移動物件。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-127">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), HoloLens gaze cursor & air-tap(far).</span></span>

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a><span data-ttu-id="8f9c3-128">如何調整物件大小？</span><span class="sxs-lookup"><span data-stu-id="8f9c3-128">How to resize an object?</span></span>
<span data-ttu-id="8f9c3-129">ManipulationHandler.cs 支援兩手的縮放/旋轉。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-129">ManipulationHandler.cs supports two-handed scale/rotation.</span></span> <span data-ttu-id="8f9c3-130">這適用於各種輸入類型，例如 HoloLens 2 的接合手部輸入、HoloLens 1 的注視 + 手勢輸入，以及 Windows Mixed Reality 沉浸式頭戴裝置的動作控制器輸入。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-130">This works with various input types such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="8f9c3-131">在 MRTK 文件中深入了解操作處理器</span><span class="sxs-lookup"><span data-stu-id="8f9c3-131">Learn more about Manipulation Handler in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="8f9c3-132">如何精確地移動或旋轉物件？</span><span class="sxs-lookup"><span data-stu-id="8f9c3-132">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="8f9c3-133">將 BoundingBox.cs 指派給物件以使用周框方塊，也就是用來縮放和旋轉物件的介面。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-133">Assign BoundingBox.cs to an object to use Bounding Box which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="8f9c3-134">根據預設，其會顯示 HoloLens 1 樣式的藍色控點和連接線。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-134">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="8f9c3-135">若要使用 HoloLens 2 樣式的鄰近動畫控點，您必須指派 Prefab 和材質。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-135">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> <span data-ttu-id="8f9c3-136">如需有關設定的詳細資料，請參閱[周框方塊文件](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)和 BBoundingBoxExamples.unity 場景。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-136">Please refer to [Bounding Box documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) and the BoundingBoxExamples.unity scene for the configuration details.</span></span>

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [<span data-ttu-id="8f9c3-137">在 MRTK 文件中深入了解周框方塊</span><span class="sxs-lookup"><span data-stu-id="8f9c3-137">Learn more about Bounding Box in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a><span data-ttu-id="8f9c3-138">如何讓物件回應輸入事件？</span><span class="sxs-lookup"><span data-stu-id="8f9c3-138">How to make an object respond to input events?</span></span>
<span data-ttu-id="8f9c3-139">將 PointerHandler.cs 指派給物件。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-139">Assign PointerHandler.cs to an object.</span></span> <span data-ttu-id="8f9c3-140">在偵測器中，您可以使用 OnPointerDown()、OnPointerUp()、OnPointerClicked()、OnPointerDragged() 事件。若要在指令碼中使用這些事件，請實作 IMixedRealityPointerHandler。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-140">In the inspector, you will be able to use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement IMixedRealityPointerHandler.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="8f9c3-141">在 MRTK 文件中深入了解輸入系統</span><span class="sxs-lookup"><span data-stu-id="8f9c3-141">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="8f9c3-142">如何新增視覺回饋？</span><span class="sxs-lookup"><span data-stu-id="8f9c3-142">How to add visual feedback?</span></span>
<span data-ttu-id="8f9c3-143">將 Interactable.cs 指派給物件。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-143">Assign Interactable.cs to an object.</span></span> <span data-ttu-id="8f9c3-144">在偵測器中建立新的主題。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-144">In the inspector, create a new theme.</span></span> <span data-ttu-id="8f9c3-145">您可以使用 Interactable (可互動) 的主題設定檔，輕鬆地在所有可用的輸入互動狀態中新增視覺回饋。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-145">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="8f9c3-146">Interactable 提供各種主題類型，包括著色器主題，該主題可讓您控制每個互動狀態的著色器屬性。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-146">Interactable provides various types of themes including the shader theme which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="8f9c3-147">在 MRTK 文件中深入了解 Interactable</span><span class="sxs-lookup"><span data-stu-id="8f9c3-147">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="8f9c3-148">視覺化回饋的另一個重要組成要素是 MRTK 標準著色器。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-148">Another important building block for visual feedback is the MRTK Standard Shader.</span></span> <span data-ttu-id="8f9c3-149">透過 MRTK 標準著色器，您可以輕鬆地加入視覺回饋效果，例如暫留光源和鄰近光源。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-149">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="8f9c3-150">由於 MRTK 標準著色器執行的計算比 Unity 標準著色器少很多，因此可讓您建立高效能的體驗。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-150">Since MRTK Standard shader performs significantly less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="8f9c3-151">建立新的材質，然後選取著色器的 [混合實境工具組] > [標準]。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-151">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="8f9c3-152">或者，您可以挑選其中一個使用 MRTK 標準著色器的現有材質。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-152">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="8f9c3-153">在 MRTK 文件中深入了解 MRTK 標準著色器</span><span class="sxs-lookup"><span data-stu-id="8f9c3-153">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="8f9c3-154">如何新增音訊回饋？</span><span class="sxs-lookup"><span data-stu-id="8f9c3-154">How to add audio feedback?</span></span>
<span data-ttu-id="8f9c3-155">將 AudioSource 新增至物件。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-155">Add AudioSource to an object.</span></span> <span data-ttu-id="8f9c3-156">然後，在公開輸入事件 (例如 Interactable.cs 或 PointerHandler.cs) 的指令碼中，將物件指派給事件，然後選取 [AudioSource.PlayOneShot()]。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-156">Then, in the scripts that exposes input events(e.g. Interactable.cs or PointerHandler.cs), assign the object to the event and select AudioSource.PlayOneShot().</span></span> <span data-ttu-id="8f9c3-157">您可以使用您的音訊片段，或從 MRTK 的音訊資產中選擇一個。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-157">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a><span data-ttu-id="8f9c3-158">如何使用 HoloLens 2 樣式的按鈕 Prefab？</span><span class="sxs-lookup"><span data-stu-id="8f9c3-158">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="8f9c3-159">MRTK 提供各類 HoloLens 2 命令介面 (OS) 樣式的按鈕。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-159">MRTK provides various types of HoloLens 2's shell(OS) style buttons.</span></span> <span data-ttu-id="8f9c3-160">其提供複雜的視覺回饋，例如，鄰近光源、壓縮方塊和按鈕表面上的漣波效果。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-160">It provides sophisticated visual feedbacks such as proximity light, compressing box, and a ripple effect on the button surface.</span></span>

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="8f9c3-161">只要將其中一個 HoloLens 2 樣式的可點按按鈕拖放到您的場景中即可。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-161">Simply drag and drop one of the HoloLens 2 style pressable button prefab into your scene.</span></span> <span data-ttu-id="8f9c3-162">Prefab 會使用上方介紹的 Interactable.cs。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-162">The prefab uses Interactable.cs which is introduced above.</span></span> <span data-ttu-id="8f9c3-163">您可以在 Interactable 中使用公開的事件 例如 (OnClick()) 來觸發動作。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-163">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="8f9c3-164">在 MRTK 文件中深入了解按鈕 Prefab</span><span class="sxs-lookup"><span data-stu-id="8f9c3-164">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a><span data-ttu-id="8f9c3-165">如何讓物件跟著您移動？</span><span class="sxs-lookup"><span data-stu-id="8f9c3-165">How to make an object follow you?</span></span>
<span data-ttu-id="8f9c3-166">將 RadialView.cs 指令碼指派給物件。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-166">Assign RadialView.cs script to an object.</span></span> <span data-ttu-id="8f9c3-167">這是 Solver (解算器) 指令碼系列的一部分，可讓您在 3D 空間中實現各種物件類型的定位。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-167">It is part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="8f9c3-168">SolverHandler.cs 將會自動新增。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-168">SolverHandler.cs will be automatically added.</span></span>
<span data-ttu-id="8f9c3-169">以下是使用 RadialView 設定達到 'lazy follow' 常駐標籤行為的範例，就像是 HoloLens 命令介面中的 [開始] 功能表。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-169">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="8f9c3-170">您可以指定最小/最大距離和最小/最大檢視角度。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-170">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="8f9c3-171">下列範例顯示物件在 0.4m 和 0.8m 範圍之間的 15° 檢視。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-171">The example below shows positioning the object between 0.4m and 0.8m range within 15°.</span></span> <span data-ttu-id="8f9c3-172">調整 Lerp 時間值，讓位置更新的速度更快或更慢。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-172">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="8f9c3-173">在 MRTK 文件中深入了解 Solver</span><span class="sxs-lookup"><span data-stu-id="8f9c3-173">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a><span data-ttu-id="8f9c3-174">如何讓物件面對您？</span><span class="sxs-lookup"><span data-stu-id="8f9c3-174">How to make an object face you?</span></span>
<span data-ttu-id="8f9c3-175">將 Billboard.cs 指令碼指派給物件。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-175">Assign Billboard.cs script to an object.</span></span> <span data-ttu-id="8f9c3-176">無論您的位置為何，物件一律會面對您。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-176">It will always face you, regardless of your position.</span></span> <span data-ttu-id="8f9c3-177">您可以指定樞紐軸選項。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-177">You can specify the pivot axis option.</span></span>

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="8f9c3-178">準備好建立混合實境的絕佳體驗了嗎？</span><span class="sxs-lookup"><span data-stu-id="8f9c3-178">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="8f9c3-179">請瀏覽下列頁面，並深入了解 MRTK 和混合實境。</span><span class="sxs-lookup"><span data-stu-id="8f9c3-179">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="8f9c3-180">關於作者</span><span class="sxs-lookup"><span data-stu-id="8f9c3-180">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="8f9c3-181"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="8f9c3-181"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="8f9c3-182">UX 設計者 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="8f9c3-182">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="8f9c3-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f9c3-183">See also</span></span>

* [<span data-ttu-id="8f9c3-184">混合實境工具組-Unity (MRTK) GitHub</span><span class="sxs-lookup"><span data-stu-id="8f9c3-184">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="8f9c3-185">MRTK 文件入口網站</span><span class="sxs-lookup"><span data-stu-id="8f9c3-185">MRTK Documentation Portal</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="8f9c3-186">開始使用 MRTK</span><span class="sxs-lookup"><span data-stu-id="8f9c3-186">Getting Started with MRTK</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="8f9c3-187">HoloToolkit 至 MRTK 的移植指導方針</span><span class="sxs-lookup"><span data-stu-id="8f9c3-187">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
