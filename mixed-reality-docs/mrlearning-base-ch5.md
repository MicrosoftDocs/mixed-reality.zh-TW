---
title: 入門教學課程 - 6。 探索進階的輸入選項
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: ec078015304e1cddc9b042fb5e94cf1904a302cb
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376085"
---
# <a name="6-exploring-advanced-input-options"></a><span data-ttu-id="a2c20-105">6.探索進階的輸入選項</span><span class="sxs-lookup"><span data-stu-id="a2c20-105">6. Exploring advanced input options</span></span>

<span data-ttu-id="a2c20-106">在本教學課程中，我們將探討 HoloLens 2 的幾個進階輸入選項，包括使用語音命令、平移手勢和眼球追蹤。</span><span class="sxs-lookup"><span data-stu-id="a2c20-106">In this tutorial, you will explore a few advanced input options for HoloLens 2, including the use of voice commands, panning gesture, and eye tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="a2c20-107">目標</span><span class="sxs-lookup"><span data-stu-id="a2c20-107">Objectives</span></span>

* <span data-ttu-id="a2c20-108">使用語音命令和關鍵字觸發事件</span><span class="sxs-lookup"><span data-stu-id="a2c20-108">Trigger events using voice commands and keywords</span></span>
* <span data-ttu-id="a2c20-109">使用手部追蹤來平移紋理和 3D 物件</span><span class="sxs-lookup"><span data-stu-id="a2c20-109">Use tracked hands to pan textures and 3D objects with tracked hands</span></span>
* <span data-ttu-id="a2c20-110">利用 HoloLens 2 的眼球追蹤功能來選取物件</span><span class="sxs-lookup"><span data-stu-id="a2c20-110">Leverage HoloLens 2 eye tracking capabilities to select objects</span></span>

## <a name="enabling-voice-commands"></a><span data-ttu-id="a2c20-111">啟用語音命令</span><span class="sxs-lookup"><span data-stu-id="a2c20-111">Enabling Voice Commands</span></span>
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

<span data-ttu-id="a2c20-112">您將在本節中實作語音命令，讓使用者可以在 Octa 物件上播放音效。</span><span class="sxs-lookup"><span data-stu-id="a2c20-112">In this section, you will implement a speech command to let the user play a sound on the Octa object.</span></span> <span data-ttu-id="a2c20-113">為此，您將建立新的語音命令，然後設定事件，讓您在說出語音命令關鍵字時，即可觸發所需的動作。</span><span class="sxs-lookup"><span data-stu-id="a2c20-113">For this, you will create a new speech command and then configure the event so it triggers the desired action when the speech command keyword is spoken.</span></span>

<span data-ttu-id="a2c20-114">達成此動作所需採取的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="a2c20-114">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="a2c20-115">複製預設的輸入系統設定檔</span><span class="sxs-lookup"><span data-stu-id="a2c20-115">Clone the default Input System Profile</span></span>
2. <span data-ttu-id="a2c20-116">複製預設的語音命令設定檔</span><span class="sxs-lookup"><span data-stu-id="a2c20-116">Clone the default Speech Commands Profile</span></span>
3. <span data-ttu-id="a2c20-117">建立新的語音命令</span><span class="sxs-lookup"><span data-stu-id="a2c20-117">Create a new speech command</span></span>
4. <span data-ttu-id="a2c20-118">新增和設定 Speech Input Handler (指令碼) 元件</span><span class="sxs-lookup"><span data-stu-id="a2c20-118">Add and configure the Speech Input Handler (Script) component</span></span>
5. <span data-ttu-id="a2c20-119">實作語音命令的回應事件</span><span class="sxs-lookup"><span data-stu-id="a2c20-119">Implement the Response event for the speech command</span></span>

### <a name="1-clone-the-default-input-system-profile"></a><span data-ttu-id="a2c20-120">1.複製預設的輸入系統設定檔</span><span class="sxs-lookup"><span data-stu-id="a2c20-120">1. Clone the default Input System Profile</span></span>

<span data-ttu-id="a2c20-121">在 [階層] 視窗中，選取 **MixedRealityToolkit** 物件，然後在 [偵測器] 視窗中選取 [輸入]  索引標籤，複製 **DefaultHoloLens2InputSystemProfile** 來將其取代為您自己可自訂的**輸入系統設定檔**：</span><span class="sxs-lookup"><span data-stu-id="a2c20-121">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab and clone the **DefaultHoloLens2InputSystemProfile** to replace it with your own customizable **Input System Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="a2c20-123">如需有關如何複製 MRTK 設定檔的提示，您可以參閱[如何設定混合實境工具組設定檔](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)的指示。</span><span class="sxs-lookup"><span data-stu-id="a2c20-123">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

### <a name="2-clone-the-default-speech-commands-profile"></a><span data-ttu-id="a2c20-124">2.複製預設的語音命令設定檔</span><span class="sxs-lookup"><span data-stu-id="a2c20-124">2. Clone the default Speech Commands Profile</span></span>

<span data-ttu-id="a2c20-125">展開 [語音]  區段，然後複製 **DefaultMixedRealitySpeechCommandsProfile** 來將其取代為您自己可自訂的**語音命令設定檔**：</span><span class="sxs-lookup"><span data-stu-id="a2c20-125">Expand the **Speech** section and clone the **DefaultMixedRealitySpeechCommandsProfile** to replace it with your own customizable **Speech Commands Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a><span data-ttu-id="a2c20-127">3.建立新的語音命令</span><span class="sxs-lookup"><span data-stu-id="a2c20-127">3. Create a new speech command</span></span>

<span data-ttu-id="a2c20-128">在 [語音命令]  區段中按一下 [+ 新增語音命令]  按鈕，將新的語音命令新增至現有語音命令清單的底部，然後在 [關鍵字]  欄位中輸入適當的單字或片語，例如 **Play Music** (播放音樂)：</span><span class="sxs-lookup"><span data-stu-id="a2c20-128">In the **Speech Commands** section, click the **+ Add a New Speech Command** button to add a new speech command to the bottom of the list of existing speech commands, then in the **Keyword** field enter a suitable word or phrase, for example **Play Music**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> <span data-ttu-id="a2c20-130">如果您的電腦沒有麥克風，而您想要使用編輯器內的模擬來測試語音命令，您可以將 KeyCode 指派給語音命令，此方式可讓您在按下對應的按鍵時觸發語音命令。</span><span class="sxs-lookup"><span data-stu-id="a2c20-130">If your computer doesn't have a microphone and you would like to test the speech command using the in-editor simulation, you can assign a KeyCode to the speech command which will let you trigger it when the corresponding key is pressed.</span></span>

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a><span data-ttu-id="a2c20-131">4.新增和設定 Speech Input Handler (指令碼) 元件</span><span class="sxs-lookup"><span data-stu-id="a2c20-131">4. Add and configure the Speech Input Handler (Script) component</span></span>

<span data-ttu-id="a2c20-132">在 [階層] 視窗中，選取 **Octa** 物件，並將 **Speech Input Handler (指令碼)** 元件新增至 Octa 物件。</span><span class="sxs-lookup"><span data-stu-id="a2c20-132">In the Hierarchy window, select the **Octa** object and add the **Speech Input Handler (Script)** component to the Octa object.</span></span> <span data-ttu-id="a2c20-133">然後取消核取 [需要對焦]  核取方塊，如此使用者就不需要看著 Octa 物件來觸發語音命令：</span><span class="sxs-lookup"><span data-stu-id="a2c20-133">Then uncheck the **Is Focus Required** checkbox so the user is not required to look at the Octa object to trigger the speech command:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a><span data-ttu-id="a2c20-135">5.實作語音命令的回應事件</span><span class="sxs-lookup"><span data-stu-id="a2c20-135">5. Implement the Response event for the speech command</span></span>

<span data-ttu-id="a2c20-136">在 Speech Input Handler (指令碼) 元件上，按一下小的 **[+]** 按鈕，將關鍵字元素新增至關鍵字清單：</span><span class="sxs-lookup"><span data-stu-id="a2c20-136">On the Speech Input Handler (Script) component, click the small **+** button to add a keyword element to the list of keywords:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

<span data-ttu-id="a2c20-138">按一下新建立的**元素 0** 來將其展開，然後從 [關鍵字]  下拉式清單中，選擇您稍早建立的 [Play Music]  關鍵字：</span><span class="sxs-lookup"><span data-stu-id="a2c20-138">Click the newly created **Element 0** to expand it, and then, from the **Keyword** dropdown, choose the **Play Music** keyword you created earlier:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!NOTE]
> <span data-ttu-id="a2c20-140">在關鍵字下拉式清單中填入的關鍵字，是以語音命令設定檔中「語音命令」清單上定義的關鍵字為基礎。</span><span class="sxs-lookup"><span data-stu-id="a2c20-140">The keywords in the Keyword dropdown are populated based on the keywords defined in the Speech Commands list in the Speech Commands Profile.</span></span>

<span data-ttu-id="a2c20-141">建立新的 **Response ()** 事件、設定 **Octa** 物件以接收事件、將 **AudioSource.PlayOneShot** 定義為要觸發的動作，並將適當的音訊片段指派給 [音訊片段]  欄位，例如 MRTK_Gem 音訊片段：</span><span class="sxs-lookup"><span data-stu-id="a2c20-141">Create a new **Response ()** event, configure the **Octa** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-3.png)

> [!TIP]
> <span data-ttu-id="a2c20-143">如需有關如何實作事件和指派音訊片段的提示，您可以參閱[實作 On Touch Started 事件](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event)的指示。</span><span class="sxs-lookup"><span data-stu-id="a2c20-143">For a reminder on how to implement events and assign an audio clip, you can refer to the [Implement the On Touch Started event](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) instructions.</span></span>

## <a name="the-pan-gesture"></a><span data-ttu-id="a2c20-144">平移手勢</span><span class="sxs-lookup"><span data-stu-id="a2c20-144">The Pan Gesture</span></span>

<span data-ttu-id="a2c20-145">平移手勢可用於捲動項目 (使用您的手指或手捲動內容)。</span><span class="sxs-lookup"><span data-stu-id="a2c20-145">The pan gesture is useful for scrolling by using your finger or hand to scroll through content.</span></span> <span data-ttu-id="a2c20-146">在此範例中，您會先了解如何捲動 2D UI，然後再擴展為能夠在3D 物件的集合上捲動項目。</span><span class="sxs-lookup"><span data-stu-id="a2c20-146">In this example, you will first learn how to scroll a 2D UI and then expand on that to be able to scroll through a collection of 3D objects.</span></span>

<span data-ttu-id="a2c20-147">達成此動作所需採取的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="a2c20-147">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="a2c20-148">建立可用於平移的 Quad (四邊形) 物件</span><span class="sxs-lookup"><span data-stu-id="a2c20-148">Create a Quad object that can be used for panning</span></span>
2. <span data-ttu-id="a2c20-149">新增 Near Interaction Touchable (指令碼) 元件</span><span class="sxs-lookup"><span data-stu-id="a2c20-149">Add the Near Interaction Touchable (Script) component</span></span>
3. <span data-ttu-id="a2c20-150">新增 Hand Interaction Pan Zoom (指令碼) 元件</span><span class="sxs-lookup"><span data-stu-id="a2c20-150">Add the Hand Interaction Pan Zoom (Script) component</span></span>
4. <span data-ttu-id="a2c20-151">新增要捲動的 2D 內容</span><span class="sxs-lookup"><span data-stu-id="a2c20-151">Add 2D content to be scrolled</span></span>
5. <span data-ttu-id="a2c20-152">新增要捲動的 3D 內容</span><span class="sxs-lookup"><span data-stu-id="a2c20-152">Add 3D content to be scrolled</span></span>
6. <span data-ttu-id="a2c20-153">新增 Move With Pan (指令碼) 元件</span><span class="sxs-lookup"><span data-stu-id="a2c20-153">Add the Move With Pan (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="a2c20-154">Move With Pan (指令碼) 元件不是 MRTK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="a2c20-154">The Move With Pan (Script) component is not part of MRTK.</span></span> <span data-ttu-id="a2c20-155">這是本教學課程資產隨附的元件。</span><span class="sxs-lookup"><span data-stu-id="a2c20-155">It was provided with this tutorial's assets.</span></span>

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a><span data-ttu-id="a2c20-156">1.建立可用於平移的 Quad (四邊形) 物件</span><span class="sxs-lookup"><span data-stu-id="a2c20-156">1. Create a Quad object that can be used for panning</span></span>

<span data-ttu-id="a2c20-157">在 [階層] 視窗中，以滑鼠右鍵按一下空白區域，然後選取 [3D 物件]   > [Quad]  ，將一個四邊形新增至您的場景。</span><span class="sxs-lookup"><span data-stu-id="a2c20-157">In the Hierarchy window, right-click at an empty area and select **3D Object** > **Quad** to add a quad to your scene.</span></span> <span data-ttu-id="a2c20-158">為其指定一個適當的名稱 (例如 **PanGesture**)，然後放在適當的位置，例如 X = 0、Y = -0.2、Z = 2。</span><span class="sxs-lookup"><span data-stu-id="a2c20-158">Give it a suitable name, for example, **PanGesture**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="a2c20-160">如需有關如何將 Unity 基本項目 (例如 3D 四邊形) 新增至場景的提示，您可以參閱[將立方體新增至場景](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene)的指示。</span><span class="sxs-lookup"><span data-stu-id="a2c20-160">For a reminder on how to add Unity primitives, such as a 3D quad, to your scene, you can refer to the [Add a cube to the scene](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) instructions.</span></span>

<span data-ttu-id="a2c20-161">如同任何其他互動，平移手勢也需要碰撞器。</span><span class="sxs-lookup"><span data-stu-id="a2c20-161">As with any other interaction, the the pan gesture also requires a collider.</span></span> <span data-ttu-id="a2c20-162">根據預設，Quad 具有網格碰撞器 (Mesh Collider)。</span><span class="sxs-lookup"><span data-stu-id="a2c20-162">By default, a Quad has a mesh collider.</span></span> <span data-ttu-id="a2c20-163">然而，網格碰撞器並不理想，因為其非常薄。</span><span class="sxs-lookup"><span data-stu-id="a2c20-163">However, the mesh collider is not ideal because it is extremely thin.</span></span> <span data-ttu-id="a2c20-164">為了讓使用者更容易與碰撞器互動，我們將以方塊碰撞器來取代網格碰撞器。</span><span class="sxs-lookup"><span data-stu-id="a2c20-164">To make it easier for the user to interact with the collider, we will replace the mesh collider with a box collider.</span></span>

<span data-ttu-id="a2c20-165">在仍選取 PanGesture 物件的情況下，按一下 **網格碰撞器** 元件的 [設定]  圖示，然後選取 [移除元件]  來移除網格碰撞器：</span><span class="sxs-lookup"><span data-stu-id="a2c20-165">With the PanGesture object still selected, click the **Mesh Collider** component's **Settings** icon and select **Remove Component** to remove the Mesh Collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

<span data-ttu-id="a2c20-167">在 [偵測器] 視窗中，使用 [新增元件]  按鈕來新增**方塊碰撞器**，然後將方塊碰撞器**大小** 的 Z 變更為 0.15，以增加方塊碰撞器的厚度：</span><span class="sxs-lookup"><span data-stu-id="a2c20-167">In the Inspector window, use the **Add Component** button to add a **Box Collider**, then change the Box Collider **Size** Z to 0.15 to increase the thickness of the box collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a><span data-ttu-id="a2c20-169">2.新增 Near Interaction Touchable (指令碼) 元件</span><span class="sxs-lookup"><span data-stu-id="a2c20-169">2. Add the Near Interaction Touchable (Script) component</span></span>

<span data-ttu-id="a2c20-170">在仍選取 **PanGesture** 物件的情況下，將 **Near Interaction Touchable (指令碼)** 元件新增至 PanGesture 物件，然後按一下 [修正周框]  和 [修正中心]  按鈕，以更新 Near Interaction Touchable (指令碼) 的區域中心和界限屬性來符合 BoxCollider：</span><span class="sxs-lookup"><span data-stu-id="a2c20-170">With the **PanGesture** object still selected, add the **Near Interaction Touchable (Script)** component to the PanGesture object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a><span data-ttu-id="a2c20-172">3.新增 Hand Interaction Pan Zoom (指令碼) 元件</span><span class="sxs-lookup"><span data-stu-id="a2c20-172">3. Add the Hand Interaction Pan Zoom (Script) component</span></span>

<span data-ttu-id="a2c20-173">在仍選取 PanGesture  物件的情況下，將 **Hand Interaction Pan Zoom (指令碼)** 元件新增至 PanGesture 物件，然後勾選 [鎖定水平方向]  核取方塊來僅限垂直捲動：</span><span class="sxs-lookup"><span data-stu-id="a2c20-173">With the **PanGesture** object still selected, add the **Hand Interaction Pan Zoom (Script)** component to the PanGesture object, and then check the **Lock Horizontal** checkbox to allow vertical scrolling only:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a><span data-ttu-id="a2c20-175">4.新增要捲動的 2D 內容</span><span class="sxs-lookup"><span data-stu-id="a2c20-175">4. Add 2D content to be scrolled</span></span>

<span data-ttu-id="a2c20-176">在 [專案] 面板中，搜尋 **PanContent** 材質，然後按一下該材質並將其拖曳至 **PanGesture** 物件的網格轉譯器**材質**的元素 0 屬性：</span><span class="sxs-lookup"><span data-stu-id="a2c20-176">In the Project panel, search for the **PanContent** material and then click-and-drag it on to the **PanGesture** object's Mesh Renderer **Material** Element 0 property:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

<span data-ttu-id="a2c20-178">在 [偵測器] 視窗中，展開新增的 **PanContent** 材質元件，然後將**拼接**的 Y 值變更為 0.5 以符合 X 值，而磚現在會呈現正方形：</span><span class="sxs-lookup"><span data-stu-id="a2c20-178">In the Inspector window, expand the newly added **PanContent** material component, and then change it's **Tiling** Y value to 0.5 so it matches the X value and the tiles appear square:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

<span data-ttu-id="a2c20-180">如果您現在進入遊戲模式，您可以在編輯器內的模擬中使用平移手勢來嘗試捲動 2D 內容：</span><span class="sxs-lookup"><span data-stu-id="a2c20-180">If you now enter Game mode, you can test scrolling the 2D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a><span data-ttu-id="a2c20-182">5.新增要捲動的 3D 內容</span><span class="sxs-lookup"><span data-stu-id="a2c20-182">5. Add 3D content to be scrolled</span></span>

<span data-ttu-id="a2c20-183">在 [階層] 視窗中，**建立四個立方體**來作為 **PanGesture** 的子物件，並將其變形**縮放**調整為 X = 0.15，Y = 0.15，Z = 0.15：</span><span class="sxs-lookup"><span data-stu-id="a2c20-183">In the Hierarchy window, **create four cubes** as a child objects of the **PanGesture** object and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

<span data-ttu-id="a2c20-185">若要將立方體平均隔開，並節省一些時間，請將 **Grid Object Collection (指令碼)** 元件新增至立方體的父物件 (也就是 **PanGesture** 物件)，然後設定 Grid Object Collection (指令碼)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a2c20-185">To space the cubes out evenly, and save some time, add the **Grid Object Collection (Script)** component, to the cubes' parent object, i.e. the **PanGesture** object, and configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="a2c20-186">將 [資料列數目]  變更為 1，使所有立方體對齊一個單一資料列</span><span class="sxs-lookup"><span data-stu-id="a2c20-186">Change **Num Rows** to 1 to have all the cubes aligned on one single row</span></span>
* <span data-ttu-id="a2c20-187">將 [儲存格寬度]  變更為 0.25，以拉開資料列內的立方體距離</span><span class="sxs-lookup"><span data-stu-id="a2c20-187">Change **Cell Width** to 0.25 to space out the cubes within the row</span></span>

<span data-ttu-id="a2c20-188">然後按一下 [更新集合]  按鈕以套用新的設定：</span><span class="sxs-lookup"><span data-stu-id="a2c20-188">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a><span data-ttu-id="a2c20-190">6.新增 Move With Pan (指令碼) 元件</span><span class="sxs-lookup"><span data-stu-id="a2c20-190">6. Add the Move With Pan (Script) component</span></span>

<span data-ttu-id="a2c20-191">在 [階層] 視窗中，選取所有**立方體子物件**，然後在 [偵測器] 視窗中，使用 [新增元件]  按鈕，將 **Move With Pan (指令碼)** 元件新增至所有立方體：</span><span class="sxs-lookup"><span data-stu-id="a2c20-191">In the Hierarchy window, select all the **Cube child objects**, then in the Inspector window, use the **Add Component** button to add the **Move With Pan (Script)** component to all the cubes:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> <span data-ttu-id="a2c20-193">如需有關如何在 [階層] 視窗中選取多個物件的提示，您可以參閱[將 Manipulation Handler (指令碼) 元件新增至所有物件](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects)的指示。</span><span class="sxs-lookup"><span data-stu-id="a2c20-193">For a reminder on how to select multiple objects in the Hierarchy window, tou can refer to the [Add the Manipulation Handler (Script) component to all the objects](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) instructions.</span></span>

<span data-ttu-id="a2c20-194">在仍選取所有立方體的情況下，按一下 **PanGesture** 物件並將其拖曳至 [平移輸入來源]  欄位：</span><span class="sxs-lookup"><span data-stu-id="a2c20-194">With all the cubes still selected, click-and-drag the **PanGesture** object to the **Pan Input Source** field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> <span data-ttu-id="a2c20-196">每個立方體上的 Move With Pan (指令碼) 元件都會接聽 PanGesture 物件 (已在上個步驟指派為 Pan Input Source) 上 HandInteractionPanZoom (指令碼) 元件所傳送的 Pan Updated 事件，並據以更新每個立方體的位置。</span><span class="sxs-lookup"><span data-stu-id="a2c20-196">The Move With Pan (Script) component on each cube listens for the Pan Updated event sent by the HandInteractionPanZoom (Script) component on the PanGesture object, which you assigned as the Pan Input Source in the step above, and updates each cube's position accordingly.</span></span>

<span data-ttu-id="a2c20-197">在 [階層] 視窗中，選取 **PanGesture** 物件，然後在偵測器中**取消核取** [網格轉譯器]  核取方塊，以停用網格轉譯器元件：</span><span class="sxs-lookup"><span data-stu-id="a2c20-197">In the Hierarchy window, select the **PanGesture** object, then in the inspector **un-check** the **Mesh Renderer** checkbox to disable the Mesh Renderer component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

<span data-ttu-id="a2c20-199">如果您現在進入遊戲模式，您可以在編輯器內的模擬中使用平移手勢來嘗試捲動 3D 內容：</span><span class="sxs-lookup"><span data-stu-id="a2c20-199">If you now enter Game mode, you can test scrolling the 3D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a><span data-ttu-id="a2c20-201">眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="a2c20-201">Eye Tracking</span></span>

<span data-ttu-id="a2c20-202">在本節中，您將探索如何在專案中啟用眼球追蹤。</span><span class="sxs-lookup"><span data-stu-id="a2c20-202">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="a2c20-203">在此範例中，您將會實作一些功能，讓 3DObjectCollection 中的每個物件能在使用者眼睛的注視下慢慢旋轉，以及當注視的物件透過空中點選或語音命令選取時觸發光點效果。</span><span class="sxs-lookup"><span data-stu-id="a2c20-203">For this example, you will implement functionality to make each object in the 3DObjectCollection spin slowly while being looked at by the user's eye gaze, as well as, trigger a blip effect when the object being looked at is selected by air-tap or speech command.</span></span>

<span data-ttu-id="a2c20-204">達成此動作所需採取的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="a2c20-204">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="a2c20-205">將 Eye Tracking Target (指令碼) 元件新增至目標物件</span><span class="sxs-lookup"><span data-stu-id="a2c20-205">Add the Eye Tracking Target (Script) component to all target objects</span></span>
2. <span data-ttu-id="a2c20-206">將 Eye Tracking Tutorial Demo (指令碼) 元件新增至所有目標物件</span><span class="sxs-lookup"><span data-stu-id="a2c20-206">Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>
3. <span data-ttu-id="a2c20-207">實作「注視目標時」(While Looking At Target) 事件</span><span class="sxs-lookup"><span data-stu-id="a2c20-207">Implement the While Looking At Target event</span></span>
4. <span data-ttu-id="a2c20-208">實作「選取時」(On Selected) 事件</span><span class="sxs-lookup"><span data-stu-id="a2c20-208">Implement the On Selected event</span></span>
5. <span data-ttu-id="a2c20-209">針對編輯器內的模擬啟用模擬的眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="a2c20-209">Enable simulated eye tracking for in-editor simulations</span></span>
6. <span data-ttu-id="a2c20-210">在 Visual Studio 專案的應用程式功能中啟用注視輸入</span><span class="sxs-lookup"><span data-stu-id="a2c20-210">Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a><span data-ttu-id="a2c20-211">1.將 Eye Tracking Target (指令碼) 元件新增至目標物件</span><span class="sxs-lookup"><span data-stu-id="a2c20-211">1. Add the Eye Tracking Target (Script) component to all target objects</span></span>

<span data-ttu-id="a2c20-212">在 [階層] 視窗中，展開 **3DObjectCollection** 物件，並選取所有**子物件**，然後在 [偵測器] 視窗中，使用 [新增元件]  按鈕，將 **Eye Tracking Target (指令碼)** 元件新增至所有子物件：</span><span class="sxs-lookup"><span data-stu-id="a2c20-212">In the Hierarchy window, expand the **3DObjectCollection** object and select all the **child objects**, then in the Inspector window, use the **Add Component** button to add the **Eye Tracking Target (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

<span data-ttu-id="a2c20-214">在仍然選取所有**子物件**的情況下，設定 **Eye Tracking Target (指令碼)** 元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a2c20-214">With all the **child objects** still selected, configure the **Eye Tracking Target (Script)** component as follows:</span></span>

* <span data-ttu-id="a2c20-215">將 [選取動作]  變更為 [選取]  ，即可將此物件的空中點選動作定義為「選取」</span><span class="sxs-lookup"><span data-stu-id="a2c20-215">Change **Select Action** to **Select**, to define the air-tap action for this object as Select</span></span>
* <span data-ttu-id="a2c20-216">展開 [語音選取]  ，並將語音命令清單的**大小**設為 1，然後在出現的新元素清單中，將 **元素 0** 變更為 [選取]  ，以將此物件的語音命令動作定義為「選取」</span><span class="sxs-lookup"><span data-stu-id="a2c20-216">Expand **Voice Select** and set the voice command list **Size** to 1, and then, in the new element list that appear, change **Element 0** to **Select**, to define the speech command action for this object as Select</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a><span data-ttu-id="a2c20-218">2.將 Eye Tracking Tutorial Demo (指令碼) 元件新增至所有目標物件</span><span class="sxs-lookup"><span data-stu-id="a2c20-218">2. Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>

<span data-ttu-id="a2c20-219">在仍選取所有**子物件**的情況下，使用 [新增元件]  按鈕，將 **Eye Tracking Tutorial Demo (指令碼)** 元件新增至所有子物件：</span><span class="sxs-lookup"><span data-stu-id="a2c20-219">With all the **child objects** still selected, use the **Add Component** button to add the **Eye Tracking Tutorial Demo (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> <span data-ttu-id="a2c20-221">The Eye Tracking Target (指令碼) 元件不是 MRTK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="a2c20-221">The Eye Tracking Target (Script) component is not part of MRTK.</span></span> <span data-ttu-id="a2c20-222">這是本教學課程資產隨附的元件。</span><span class="sxs-lookup"><span data-stu-id="a2c20-222">It was provided with this tutorial's assets.</span></span>

### <a name="3-implement-the-while-looking-at-target-event"></a><span data-ttu-id="a2c20-223">3.實作「注視目標時」(While Looking At Target) 事件</span><span class="sxs-lookup"><span data-stu-id="a2c20-223">3. Implement the While Looking At Target event</span></span>

<span data-ttu-id="a2c20-224">在 [階層] 視窗中，選取 **Cheese** 物件，然後建立新的 **While Looking At Target ()** 事件，並設定 **Cheese** 物件來接收事件，以及將 **EyeTrackingTutorialDemo.RotateTarget** 定義為要觸發的動作：</span><span class="sxs-lookup"><span data-stu-id="a2c20-224">In the Hierarchy window, select the **Cheese** object, then create a new **While Looking At Target ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.RotateTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

<span data-ttu-id="a2c20-226">針對 3DObjectCollection 中的每個子物件**重複**這些動作。</span><span class="sxs-lookup"><span data-stu-id="a2c20-226">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

> [!TIP]
> <span data-ttu-id="a2c20-227">如需有關如何實作事件的提示，您可以參閱[手部追蹤手勢和可互動按鈕](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)的指示。</span><span class="sxs-lookup"><span data-stu-id="a2c20-227">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="4-implement-the-on-selected-event"></a><span data-ttu-id="a2c20-228">4.實作「選取時」(On Selected) 事件</span><span class="sxs-lookup"><span data-stu-id="a2c20-228">4. Implement the On Selected event</span></span>

<span data-ttu-id="a2c20-229">在 [階層] 視窗中，選取 **Cheese** 物件，然後建立新的 **On Selected ()** 事件，並設定 **Cheese** 物件來接收事件，以及將 **EyeTrackingTutorialDemo.BlipTarget** 定義為要觸發的動作：</span><span class="sxs-lookup"><span data-stu-id="a2c20-229">In the Hierarchy window, select the **Cheese** object, then create a new **On Selected ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.BlipTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

<span data-ttu-id="a2c20-231">針對 3DObjectCollection 中的每個子物件**重複**這些動作。</span><span class="sxs-lookup"><span data-stu-id="a2c20-231">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a><span data-ttu-id="a2c20-232">5.針對編輯器內的模擬啟用模擬的眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="a2c20-232">5. Enable simulated eye tracking for in-editor simulations</span></span>

<span data-ttu-id="a2c20-233">在 [階層] 視窗中，選取 **MixedRealityToolkit** 物件，然後在 [偵測器] 視窗中，選取 [輸入]  索引標籤並依序展開 [輸入資料提供者]  區段和 [輸入模擬服務]  區段，然後複製 **DefaultMixedRealityInputSimulationProfile** 來將其取代為您自己可自訂的**輸入模擬設定檔**：</span><span class="sxs-lookup"><span data-stu-id="a2c20-233">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab, expand the **Input Data Providers** section and then the **Input Simulation Service** section, and clone the **DefaultMixedRealityInputSimulationProfile** to replace it with your own customizable **Input Simulation Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> <span data-ttu-id="a2c20-235">如需有關如何複製 MRTK 設定檔的提示，您可以參閱[如何設定混合實境工具組設定檔](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)的指示。</span><span class="sxs-lookup"><span data-stu-id="a2c20-235">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

<span data-ttu-id="a2c20-236">在 [眼球模擬]  區段中，核取 [模擬眼球位置]  核取方塊，以啟用眼球追蹤模擬：</span><span class="sxs-lookup"><span data-stu-id="a2c20-236">In the **Eye Simulation** section, check the **Simulate Eye Position** checkbox to enable eye tracking simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

<span data-ttu-id="a2c20-238">如果您現在進入遊戲模式，可以藉由調整視圖來測試您所實作的旋轉和光點效果，讓游標點擊其中一個物件，並使用手部互動或語音命令來選取物件：</span><span class="sxs-lookup"><span data-stu-id="a2c20-238">If you now enter Game mode, you can test the spin and blip effects you implemented by adjusting the view so the cursor hits one of the objects and using hand interaction or speech command to select the object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> <span data-ttu-id="a2c20-240">如果您未使用 DefaultHoloLens2ConfigurationProfile 來複製可自訂的 MRTK 組態設定檔 (如[設定混合實境工具組](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)中所述的指示)，您的專案中可能不會啟用眼球追蹤，而這必須啟用。</span><span class="sxs-lookup"><span data-stu-id="a2c20-240">If you did not use the DefaultHoloLens2ConfigurationProfile to clone your customizable MRTK configuration profile, as instructed in the [Configure the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) instructions, eye tracking may not be enable in your project and will need to be enabled.</span></span> <span data-ttu-id="a2c20-241">為此，您可以參閱[開始在 MRTK 中使用眼球追蹤](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html)的指示。</span><span class="sxs-lookup"><span data-stu-id="a2c20-241">For that, you can refer to the [Getting started with eye tracking in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) instructions.</span></span>

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a><span data-ttu-id="a2c20-242">6.在 Visual Studio 專案的應用程式功能中啟用注視輸入</span><span class="sxs-lookup"><span data-stu-id="a2c20-242">6. Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

<span data-ttu-id="a2c20-243">從 Visual Studio 中建立應用程式並將其部署到您的裝置之前，您必須先在專案的應用程式功能中啟用注視輸入。</span><span class="sxs-lookup"><span data-stu-id="a2c20-243">Before building and deploying your app from Visual Studio to your device, Gaze Input has to been enabled in the project's app capabilities.</span></span> <span data-ttu-id="a2c20-244">為此，您可以遵循[在 HoloLens 2 上測試 Unity 應用程式](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2)的指示來進行。</span><span class="sxs-lookup"><span data-stu-id="a2c20-244">For this, you can follow the [Testing your Unity app on a HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="a2c20-245">恭喜！</span><span class="sxs-lookup"><span data-stu-id="a2c20-245">Congratulations</span></span>

<span data-ttu-id="a2c20-246">您已成功為應用程式新增了基本的眼球追蹤功能。</span><span class="sxs-lookup"><span data-stu-id="a2c20-246">You have successfully added basic eye tracking capabilities to your application.</span></span> <span data-ttu-id="a2c20-247">這些動作只是眼球追蹤功能無限可能性的開端。</span><span class="sxs-lookup"><span data-stu-id="a2c20-247">These actions are only the beginning of a world of possibilities with eye tracking.</span></span> <span data-ttu-id="a2c20-248">在本教學課程中，您也了解了其他進階級輸入功能，例如語音命令和平移手勢。</span><span class="sxs-lookup"><span data-stu-id="a2c20-248">In this tutorial, you also learned about other advanced input features, such as voice commands and panning gestures.</span></span>

[<span data-ttu-id="a2c20-249">下一課：7.建立登月小艇應用程式範例</span><span class="sxs-lookup"><span data-stu-id="a2c20-249">Next Lesson: 7. Creating a Lunar Module sample application</span></span>](mrlearning-base-ch6.md)
