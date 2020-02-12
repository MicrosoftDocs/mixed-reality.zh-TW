---
title: 快速入門教學課程-6。 探索先進的輸入選項
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 18bcbc95746a2e66b88d83f279603aa7f171bbcb
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129625"
---
# <a name="6-exploring-advanced-input-options"></a><span data-ttu-id="7f18c-105">6. 探索 advanced 輸入選項</span><span class="sxs-lookup"><span data-stu-id="7f18c-105">6. Exploring advanced input options</span></span>

<span data-ttu-id="7f18c-106">在本教學課程中，您將探索 HoloLens 2 的幾個先進輸入選項，包括使用語音命令、移動流覽手勢和眼睛追蹤。</span><span class="sxs-lookup"><span data-stu-id="7f18c-106">In this tutorial, you will explore a few advanced input options for HoloLens 2, including the use of voice commands, panning gesture, and eye tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="7f18c-107">目標</span><span class="sxs-lookup"><span data-stu-id="7f18c-107">Objectives</span></span>

* <span data-ttu-id="7f18c-108">使用語音命令和關鍵字觸發事件</span><span class="sxs-lookup"><span data-stu-id="7f18c-108">Trigger events using voice commands and keywords</span></span>
* <span data-ttu-id="7f18c-109">使用追蹤的手平移材質和3D 物件</span><span class="sxs-lookup"><span data-stu-id="7f18c-109">Use tracked hands to pan textures and 3D objects with tracked hands</span></span>
* <span data-ttu-id="7f18c-110">利用 HoloLens 2 眼追蹤功能來選取物件</span><span class="sxs-lookup"><span data-stu-id="7f18c-110">Leverage HoloLens 2 eye tracking capabilities to select objects</span></span>

## <a name="enabling-voice-commands"></a><span data-ttu-id="7f18c-111">啟用語音命令</span><span class="sxs-lookup"><span data-stu-id="7f18c-111">Enabling Voice Commands</span></span>
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

<span data-ttu-id="7f18c-112">在本節中，您將會執行語音命令，讓使用者在顆 octa 物件上播放音效。</span><span class="sxs-lookup"><span data-stu-id="7f18c-112">In this section, you will implement a speech command to let the user play a sound on the Octa object.</span></span> <span data-ttu-id="7f18c-113">為此，您將建立新的語音命令，然後設定事件，讓它在說話語音命令關鍵字時觸發所需的動作。</span><span class="sxs-lookup"><span data-stu-id="7f18c-113">For this, you will create a new speech command and then configure the event so it triggers the desired action when the speech command keyword is spoken.</span></span>

<span data-ttu-id="7f18c-114">達成此目標所需採取的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="7f18c-114">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="7f18c-115">複製預設輸入系統設定檔</span><span class="sxs-lookup"><span data-stu-id="7f18c-115">Clone the default Input System Profile</span></span>
2. <span data-ttu-id="7f18c-116">複製預設的語音命令設定檔</span><span class="sxs-lookup"><span data-stu-id="7f18c-116">Clone the default Speech Commands Profile</span></span>
3. <span data-ttu-id="7f18c-117">建立新的語音命令</span><span class="sxs-lookup"><span data-stu-id="7f18c-117">Create a new speech command</span></span>
4. <span data-ttu-id="7f18c-118">新增和設定語音輸入處理常式（腳本）元件</span><span class="sxs-lookup"><span data-stu-id="7f18c-118">Add and configure the Speech Input Handler (Script) component</span></span>
5. <span data-ttu-id="7f18c-119">執行語音命令的回應事件</span><span class="sxs-lookup"><span data-stu-id="7f18c-119">Implement the Response event for the speech command</span></span>

### <a name="1-clone-the-default-input-system-profile"></a><span data-ttu-id="7f18c-120">1. 複製預設輸入系統設定檔</span><span class="sxs-lookup"><span data-stu-id="7f18c-120">1. Clone the default Input System Profile</span></span>

<span data-ttu-id="7f18c-121">在 [階層] 視窗中，選取 [ **MixedRealityToolkit** ] 物件，然後在 [偵測器] 視窗中選取 [**輸入**] 索引標籤，然後複製**DefaultHoloLens2InputSystemProfile** ，將它取代為您自己可自訂的**輸入系統設定檔**：</span><span class="sxs-lookup"><span data-stu-id="7f18c-121">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab and clone the **DefaultHoloLens2InputSystemProfile** to replace it with your own customizable **Input System Profile**:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="7f18c-123">如需有關如何複製 MRTK 設定檔的提醒，您可以參閱[如何設定混合現實工具組設定檔](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)的指示。</span><span class="sxs-lookup"><span data-stu-id="7f18c-123">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

### <a name="2-clone-the-default-speech-commands-profile"></a><span data-ttu-id="7f18c-124">2. 複製預設的語音命令設定檔</span><span class="sxs-lookup"><span data-stu-id="7f18c-124">2. Clone the default Speech Commands Profile</span></span>

<span data-ttu-id="7f18c-125">展開 [**語音**] 區段並複製**DefaultMixedRealitySpeechCommandsProfile** ，將它取代為您自己的可自訂**語音命令設定檔**：</span><span class="sxs-lookup"><span data-stu-id="7f18c-125">Expand the **Speech** section and clone the **DefaultMixedRealitySpeechCommandsProfile** to replace it with your own customizable **Speech Commands Profile**:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a><span data-ttu-id="7f18c-127">3. 建立新的語音命令</span><span class="sxs-lookup"><span data-stu-id="7f18c-127">3. Create a new speech command</span></span>

<span data-ttu-id="7f18c-128">在 [**語音命令**] 區段中，按一下 [ **+ 新增語音命令**] 按鈕，將新的語音命令新增至現有語音命令清單的底部，然後在 [**關鍵字**] 欄位中輸入適當的單字或片語，例如 [**播放音樂**]：</span><span class="sxs-lookup"><span data-stu-id="7f18c-128">In the **Speech Commands** section, click the **+ Add a New Speech Command** button to add a new speech command to the bottom of the list of existing speech commands, then in the **Keyword** field enter a suitable word or phrase, for example **Play Music**:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> <span data-ttu-id="7f18c-130">如果您的電腦沒有麥克風，而您想要使用編輯器內模擬來測試語音命令，您可以將 KeyCode 指派給語音命令，讓您在按下對應的按鍵時觸發它。</span><span class="sxs-lookup"><span data-stu-id="7f18c-130">If your computer doesn't have a microphone and you would like to test the speech command using the in-editor simulation, you can assign a KeyCode to the speech command which will let you trigger it when the corresponding key is pressed.</span></span>

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a><span data-ttu-id="7f18c-131">4. 新增和設定語音輸入處理常式（腳本）元件</span><span class="sxs-lookup"><span data-stu-id="7f18c-131">4. Add and configure the Speech Input Handler (Script) component</span></span>

<span data-ttu-id="7f18c-132">在 [階層] 視窗中，選取 [**顆 octa** ] 物件，並將 [**語音輸入處理常式（腳本）** ] 元件新增至顆 octa 物件。</span><span class="sxs-lookup"><span data-stu-id="7f18c-132">In the Hierarchy window, select the **Octa** object and add the **Speech Input Handler (Script)** component to the Octa object.</span></span> <span data-ttu-id="7f18c-133">然後取消核取 [**需要焦點**] 核取方塊，讓使用者不需要查看顆 octa 物件來觸發語音命令：</span><span class="sxs-lookup"><span data-stu-id="7f18c-133">Then uncheck the **Is Focus Required** checkbox so the user is not required to look at the Octa object to trigger the speech command:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a><span data-ttu-id="7f18c-135">5. 執行語音命令的回應事件</span><span class="sxs-lookup"><span data-stu-id="7f18c-135">5. Implement the Response event for the speech command</span></span>

<span data-ttu-id="7f18c-136">在 [語音輸入處理常式（腳本）] 元件上，按一下 [小型 **+** ] 按鈕以新增關鍵字，然後從 [**關鍵字**] 下拉式清單中選擇您稍早建立的 [**播放音樂**] 關鍵字：</span><span class="sxs-lookup"><span data-stu-id="7f18c-136">On the Speech Input Handler (Script) component, click the small **+** button to add a keyword, and then, from the **Keyword** dropdown, choose the **Play Music** keyword you created earlier:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="7f18c-138">[關鍵字] 下拉式清單中的關鍵字會根據語音命令設定檔中的 [語音命令] 清單中定義的關鍵字來填入。</span><span class="sxs-lookup"><span data-stu-id="7f18c-138">The keywords in the Keyword dropdown are populated based on the keywords defined in the Speech Commands list in the Speech Commands Profile.</span></span>

<span data-ttu-id="7f18c-139">建立新的**回應（）** 事件、設定**顆 octa**物件以接收事件、將**spatialize**定義為要觸發的動作，並將適當的音訊剪輯指派給**音訊剪輯**欄位（例如，MRTK_Gem 音訊剪輯）：</span><span class="sxs-lookup"><span data-stu-id="7f18c-139">Create a new **Response ()** event, configure the **Octa** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!TIP]
> <span data-ttu-id="7f18c-141">如需有關如何執行事件和指派音訊剪輯的提醒，您可以參閱[執行觸控式已啟動事件](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event)指示。</span><span class="sxs-lookup"><span data-stu-id="7f18c-141">For a reminder on how to implement events and assign an audio clip, you can refer to the [Implement the On Touch Started event](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) instructions.</span></span>

## <a name="the-pan-gesture"></a><span data-ttu-id="7f18c-142">平移手勢</span><span class="sxs-lookup"><span data-stu-id="7f18c-142">The Pan Gesture</span></span>

<span data-ttu-id="7f18c-143">當您使用手指或手來滾動內容時，移動流覽手勢非常有用。</span><span class="sxs-lookup"><span data-stu-id="7f18c-143">The pan gesture is useful for scrolling by using your finger or hand to scroll through content.</span></span> <span data-ttu-id="7f18c-144">在此範例中，您會先瞭解如何滾動 2D UI，然後再展開它，以便能夠在3D 物件的集合上進行滾動。</span><span class="sxs-lookup"><span data-stu-id="7f18c-144">In this example, you will first learn how to scroll a 2D UI and then expand on that to be able to scroll through a collection of 3D objects.</span></span>

<span data-ttu-id="7f18c-145">達成此目標所需採取的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="7f18c-145">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="7f18c-146">建立可用於移動的四個物件</span><span class="sxs-lookup"><span data-stu-id="7f18c-146">Create a Quad object that can be used for panning</span></span>
2. <span data-ttu-id="7f18c-147">新增近乎互動 Touchable （腳本）元件</span><span class="sxs-lookup"><span data-stu-id="7f18c-147">Add the Near Interaction Touchable (Script) component</span></span>
3. <span data-ttu-id="7f18c-148">新增手互動平移縮放（腳本）元件</span><span class="sxs-lookup"><span data-stu-id="7f18c-148">Add the Hand Interaction Pan Zoom (Script) component</span></span>
4. <span data-ttu-id="7f18c-149">新增要滾動的2D 內容</span><span class="sxs-lookup"><span data-stu-id="7f18c-149">Add 2D content to be scrolled</span></span>
5. <span data-ttu-id="7f18c-150">新增要滾動的3D 內容</span><span class="sxs-lookup"><span data-stu-id="7f18c-150">Add 3D content to be scrolled</span></span>
6. <span data-ttu-id="7f18c-151">新增 Move With Pan （Script）元件</span><span class="sxs-lookup"><span data-stu-id="7f18c-151">Add the Move With Pan (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="7f18c-152">Move With Pan （Script）元件不是 MRTK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="7f18c-152">The Move With Pan (Script) component is not part of MRTK.</span></span> <span data-ttu-id="7f18c-153">本教學課程的資產提供此說明。</span><span class="sxs-lookup"><span data-stu-id="7f18c-153">It was provided with this tutorial's assets.</span></span>

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a><span data-ttu-id="7f18c-154">1. 建立可用於移動的四個物件</span><span class="sxs-lookup"><span data-stu-id="7f18c-154">1. Create a Quad object that can be used for panning</span></span>

<span data-ttu-id="7f18c-155">在 [階層] 視窗中，以滑鼠右鍵按一下空白區域，然後選取 [ **3D 物件** > **四**個]，將四個新增至您的場景。</span><span class="sxs-lookup"><span data-stu-id="7f18c-155">In the Hierarchy window, right-click at an empty area and select **3D Object** > **Quad** to add a quad to your scene.</span></span> <span data-ttu-id="7f18c-156">為它提供適當的名稱（例如， **PanGesture**），並將它放在適當的位置，例如 X = 0、Y =-0.2、Z = 2。</span><span class="sxs-lookup"><span data-stu-id="7f18c-156">Give it a suitable name, for example, **PanGesture**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="7f18c-158">如需有關如何將 Unity 基本專案（例如3D 四）新增至場景的提醒，您可以參考將[Cube 新增至場景](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene)指示。</span><span class="sxs-lookup"><span data-stu-id="7f18c-158">For a reminder on how to add Unity primitives, such as a 3D quad, to your scene, you can refer to the [Add a cube to the scene](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) instructions.</span></span>

<span data-ttu-id="7f18c-159">如同任何其他互動，平移手勢也需要碰撞。</span><span class="sxs-lookup"><span data-stu-id="7f18c-159">As with any other interaction, the the pan gesture also requires a collider.</span></span> <span data-ttu-id="7f18c-160">根據預設，四個具有網格碰撞器。</span><span class="sxs-lookup"><span data-stu-id="7f18c-160">By default, a Quad has a mesh collider.</span></span> <span data-ttu-id="7f18c-161">不過，網格碰撞的情況並不理想，因為它非常精簡。</span><span class="sxs-lookup"><span data-stu-id="7f18c-161">However, the mesh collider is not ideal because it is extremely thin.</span></span> <span data-ttu-id="7f18c-162">為了讓使用者更容易與碰撞程式互動，我們將以方塊碰撞程式來取代網格碰撞。</span><span class="sxs-lookup"><span data-stu-id="7f18c-162">To make it easier for the user to interact with the collider, we will replace the mesh collider with a box collider.</span></span>

<span data-ttu-id="7f18c-163">在仍選取 PanGesture 物件的情況下，按一下**網格碰撞**器元件的 [**設定**] 圖示，然後選取 [**移除元件**] 以移除網格碰撞器：</span><span class="sxs-lookup"><span data-stu-id="7f18c-163">With the PanGesture object still selected, click the **Mesh Collider** component's **Settings** icon and select **Remove Component** to remove the Mesh Collider:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section2-step1-2.png)

<span data-ttu-id="7f18c-165">在 [偵測器] 視窗中，使用 [**加入元件**] 按鈕加入方塊**碰撞**器，然後將方塊碰撞器**大小**Z 變更為0.15，以增加方塊碰撞器的粗細：</span><span class="sxs-lookup"><span data-stu-id="7f18c-165">In the Inspector window, use the **Add Component** button to add a **Box Collider**, then change the Box Collider **Size** Z to 0.15 to increase the thickness of the box collider:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a><span data-ttu-id="7f18c-167">2. 新增近乎互動 Touchable （腳本）元件</span><span class="sxs-lookup"><span data-stu-id="7f18c-167">2. Add the Near Interaction Touchable (Script) component</span></span>

<span data-ttu-id="7f18c-168">在仍選取**PanGesture**物件的情況下，將**近乎互動 Touchable （腳本）** 元件新增至 PanGesture 物件，然後按一下 [**修正界限**] 和 [**修正中心**] 按鈕，將近端互動 Touchable （腳本）的本機中心和界限屬性更新為符合 BoxCollider：</span><span class="sxs-lookup"><span data-stu-id="7f18c-168">With the **PanGesture** object still selected, add the **Near Interaction Touchable (Script)** component to the PanGesture object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a><span data-ttu-id="7f18c-170">3. 新增手互動平移縮放（腳本）元件</span><span class="sxs-lookup"><span data-stu-id="7f18c-170">3. Add the Hand Interaction Pan Zoom (Script) component</span></span>

<span data-ttu-id="7f18c-171">在仍選取**PanGesture**物件的情況下，將 [**手互動] [平移縮放（腳本）** ] 元件新增至 PanGesture 物件，然後勾選 [**鎖定水準**] 核取方塊，只允許垂直捲動：</span><span class="sxs-lookup"><span data-stu-id="7f18c-171">With the **PanGesture** object still selected, add the **Hand Interaction Pan Zoom (Script)** component to the PanGesture object, and then check the **Lock Horizontal** checkbox to allow vertical scrolling only:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a><span data-ttu-id="7f18c-173">4. 新增要滾動的2D 內容</span><span class="sxs-lookup"><span data-stu-id="7f18c-173">4. Add 2D content to be scrolled</span></span>

<span data-ttu-id="7f18c-174">在 [專案] 面板中，搜尋**PanContent**材質，然後按一下並將它拖曳至**PanGesture**物件的網格轉譯器**材質**元素0屬性：</span><span class="sxs-lookup"><span data-stu-id="7f18c-174">In the Project panel, search for the **PanContent** material and then click-and-drag it on to the **PanGesture** object's Mesh Renderer **Material** Element 0 property:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section2-step4-1.png)

<span data-ttu-id="7f18c-176">在 [偵測器] 視窗中，展開新增的 [ **PanContent**材質] 元件，然後將它從 **[Y]** 值切換為 [0.5]，使其符合 X 值，而磚出現正方形：</span><span class="sxs-lookup"><span data-stu-id="7f18c-176">In the Inspector window, expand the newly added **PanContent** material component, and then change it's **Tiling** Y value to 0.5 so it matches the X value and the tiles appear square:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section2-step4-2.png)

<span data-ttu-id="7f18c-178">如果您現在進入遊戲模式，您可以使用編輯器內模擬中的移動流覽手勢來測試2D 內容的滾動圖：</span><span class="sxs-lookup"><span data-stu-id="7f18c-178">If you now enter Game mode, you can test scrolling the 2D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a><span data-ttu-id="7f18c-180">5. 新增要滾動的3D 內容</span><span class="sxs-lookup"><span data-stu-id="7f18c-180">5. Add 3D content to be scrolled</span></span>

<span data-ttu-id="7f18c-181">在 [階層] 視窗中，**建立四個 cube**做為**PanContent**的子物件，並將其轉換**規模**設定為 X = 0.15、Y = 0.15、Z = 0.15：</span><span class="sxs-lookup"><span data-stu-id="7f18c-181">In the Hierarchy window, **create four cubes** as a child objects of the **PanContent** and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section2-step5-1.png)

<span data-ttu-id="7f18c-183">若要平均地將 cube 隔開，並節省一些時間，請將 Grid 物件集合（腳本）元件加入 cube 的父物件（也就是 PanGesture 物件），並設定 Grid 物件集合（腳本），如下所示：</span><span class="sxs-lookup"><span data-stu-id="7f18c-183">To space the cubes out evenly, and save some time, add the Grid Object Collection (Script) component, to the cubes' parent object, i.e. the PanGesture object, and configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="7f18c-184">將 [Num] 資料**列**變更為 [1]，讓所有 cube 對齊一個單一資料列</span><span class="sxs-lookup"><span data-stu-id="7f18c-184">Change **Num Rows** to 1 to have all the cubes aligned on one single row</span></span>
* <span data-ttu-id="7f18c-185">將資料**格寬度**變更為0.25，以將資料列中的 cube 空間縮小</span><span class="sxs-lookup"><span data-stu-id="7f18c-185">Change **Cell Width** to 0.25 to space out the cubes within the row</span></span>

<span data-ttu-id="7f18c-186">然後按一下 [**更新集合**] 按鈕以套用新的設定：</span><span class="sxs-lookup"><span data-stu-id="7f18c-186">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a><span data-ttu-id="7f18c-188">6. 新增 Move With Pan （Script）元件</span><span class="sxs-lookup"><span data-stu-id="7f18c-188">6. Add the Move With Pan (Script) component</span></span>

<span data-ttu-id="7f18c-189">在 [階層] 視窗中，選取所有**Cube 子物件**，然後在 [偵測器] 視窗中，使用 [**加入元件**] 按鈕，將 [**使用移動流覽（腳本）** ] 元件新增至所有 cube：</span><span class="sxs-lookup"><span data-stu-id="7f18c-189">In the Hierarchy window, select all the **Cube child objects**, then in the Inspector window, use the **Add Component** button to add the **Move With Pan (Script)** component to all the cubes:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> <span data-ttu-id="7f18c-191">如需有關如何在 [階層] 視窗中選取多個物件的提醒，tou 可以參考[將操作處理常式（腳本）元件加入至所有物件](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects)指示。</span><span class="sxs-lookup"><span data-stu-id="7f18c-191">For a reminder on how to select multiple objects in the Hierarchy window, tou can refer to the [Add the Manipulation Handler (Script) component to all the objects](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) instructions.</span></span>

<span data-ttu-id="7f18c-192">在仍選取所有 cube 的情況下，按一下-並將**PanGesture**物件拖曳至 [**平移輸入來源**] 欄位：</span><span class="sxs-lookup"><span data-stu-id="7f18c-192">With all the cubes still selected, click-and-drag the **PanGesture** object to the **Pan Input Source** field:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> <span data-ttu-id="7f18c-194">每個 cube 上的 Move With Pan （Script）元件會接聽 PanGesture 物件（您在上述步驟中指派為平移輸入來源）的 HandInteractionPanZoom （腳本）元件所傳送的 Pan 更新事件，並更新每個 cube 的位置。會.</span><span class="sxs-lookup"><span data-stu-id="7f18c-194">The Move With Pan (Script) component on each cube listens for the Pan Updated event sent by the HandInteractionPanZoom (Script) component on the PanGesture object, which you assigned as the Pan Input Source in the step above, and updates each cube's position accordingly.</span></span>

<span data-ttu-id="7f18c-195">在 [階層] 視窗中，選取 [ **PanGesture** ] 物件，然後在 [偵測器 **] 中** **取消勾選**[網格轉譯器] 核取方塊，以停用網格轉譯器元件：</span><span class="sxs-lookup"><span data-stu-id="7f18c-195">In the Hierarchy window, select the **PanGesture** object, then in the inspector **un-check** the **Mesh Renderer** checkbox to disable the Mesh Renderer component:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section2-step6-3.png)

<span data-ttu-id="7f18c-197">如果您現在進入遊戲模式，您可以使用編輯器內模擬中的移動流覽手勢來測試3D 內容的滾動功能：</span><span class="sxs-lookup"><span data-stu-id="7f18c-197">If you now enter Game mode, you can test scrolling the 3D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a><span data-ttu-id="7f18c-199">眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="7f18c-199">Eye Tracking</span></span>

<span data-ttu-id="7f18c-200">在本節中，您將探索如何在專案中啟用眼睛追蹤。</span><span class="sxs-lookup"><span data-stu-id="7f18c-200">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="7f18c-201">在此範例中，您將會執行一些功能，讓3DObjectCollection 中的每個物件在查看使用者眼睛時慢慢旋轉，以及在查看的物件是由 [按下] 或 [語音] 命令選取時觸發中斷效果。</span><span class="sxs-lookup"><span data-stu-id="7f18c-201">For this example, you will implement functionality to make each object in the 3DObjectCollection spin slowly while being looked at by the user's eye gaze, as well as, trigger a blip effect when the object being looked at is selected by air-tap or speech command.</span></span>

<span data-ttu-id="7f18c-202">達成此目標所需採取的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="7f18c-202">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="7f18c-203">將眼睛追蹤目標（腳本）元件新增至所有目標物件</span><span class="sxs-lookup"><span data-stu-id="7f18c-203">Add the Eye Tracking Target (Script) component to all target objects</span></span>
2. <span data-ttu-id="7f18c-204">將眼睛追蹤教學課程示範（腳本）元件新增至所有目標物件</span><span class="sxs-lookup"><span data-stu-id="7f18c-204">Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>
3. <span data-ttu-id="7f18c-205">在查看目標事件時執行</span><span class="sxs-lookup"><span data-stu-id="7f18c-205">Implement the While Looking At Target event</span></span>
4. <span data-ttu-id="7f18c-206">在選取的事件上執行</span><span class="sxs-lookup"><span data-stu-id="7f18c-206">Implement the On Selected event</span></span>
5. <span data-ttu-id="7f18c-207">針對編輯器內的模擬啟用模擬的監看式追蹤</span><span class="sxs-lookup"><span data-stu-id="7f18c-207">Enable simulated eye tracking for in-editor simulations</span></span>
6. <span data-ttu-id="7f18c-208">在 Visual Studio 專案的應用程式功能中啟用注視輸入</span><span class="sxs-lookup"><span data-stu-id="7f18c-208">Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a><span data-ttu-id="7f18c-209">1. 將眼睛追蹤目標（腳本）元件新增至所有目標物件</span><span class="sxs-lookup"><span data-stu-id="7f18c-209">1. Add the Eye Tracking Target (Script) component to all target objects</span></span>

<span data-ttu-id="7f18c-210">在 [階層] 視窗中，展開 [ **3DObjectCollection** ] 物件並選取所有**子物件**，然後在 [偵測器] 視窗中，使用 [**加入元件**] 按鈕，將**眼睛追蹤目標（腳本）** 元件新增至所有子物件：</span><span class="sxs-lookup"><span data-stu-id="7f18c-210">In the Hierarchy window, expand the **3DObjectCollection** object and select all the **child objects**, then in the Inspector window, use the **Add Component** button to add the **Eye Tracking Target (Script)** component to all the child objects:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section3-step1-1.png)

<span data-ttu-id="7f18c-212">在仍選取所有**子物件**的情況下，設定**眼睛追蹤目標（腳本）** 元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7f18c-212">With all the **child objects** still selected, configure the **Eye Tracking Target (Script)** component as follows:</span></span>

* <span data-ttu-id="7f18c-213">將 [**選取動作**] 變更為 [**選取**]，將此物件的 [按下] 動作定義為 [選取]</span><span class="sxs-lookup"><span data-stu-id="7f18c-213">Change **Select Action** to **Select**, to define the air-tap action for this object as Select</span></span>
* <span data-ttu-id="7f18c-214">展開 [**語音選取**] 並將語音命令清單**大小**設定為1，然後在出現的 [新增專案] 清單中，將**元素 0**變更為 [**選取**]，以將此物件的語音命令動作定義為 [選取]</span><span class="sxs-lookup"><span data-stu-id="7f18c-214">Expand **Voice Select** and set the voice command list **Size** to 1, and then, in the new element list that appear, change **Element 0** to **Select**, to define the speech command action for this object as Select</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a><span data-ttu-id="7f18c-216">2. 將眼睛追蹤教學課程示範（腳本）元件新增至所有目標物件</span><span class="sxs-lookup"><span data-stu-id="7f18c-216">2. Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>

<span data-ttu-id="7f18c-217">若仍然選取所有**子物件**，請使用 [**新增元件**] 按鈕，將**眼睛追蹤教學課程示範（腳本）** 元件新增至所有子物件：</span><span class="sxs-lookup"><span data-stu-id="7f18c-217">With all the **child objects** still selected, use the **Add Component** button to add the **Eye Tracking Tutorial Demo (Script)** component to all the child objects:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> <span data-ttu-id="7f18c-219">眼睛追蹤目標（腳本）元件不是 MRTK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="7f18c-219">The Eye Tracking Target (Script) component is not part of MRTK.</span></span> <span data-ttu-id="7f18c-220">本教學課程的資產提供此說明。</span><span class="sxs-lookup"><span data-stu-id="7f18c-220">It was provided with this tutorial's assets.</span></span>

### <a name="3-implement-the-while-looking-at-target-event"></a><span data-ttu-id="7f18c-221">3. 在查看目標事件時執行</span><span class="sxs-lookup"><span data-stu-id="7f18c-221">3. Implement the While Looking At Target event</span></span>

<span data-ttu-id="7f18c-222">在 [階層] 視窗中，選取 [**乳酪**] 物件，然後在**查看 [目標（）** ] 事件時建立新的，將 [**乳酪**] 物件設定為接收事件，並將**EyeTrackingTutorialDemo**定義為要觸發的動作：</span><span class="sxs-lookup"><span data-stu-id="7f18c-222">In the Hierarchy window, select the **Cheese** object, then create a new **While Looking At Target ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.RotateTarget** as the action to be triggered:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section3-step3-1.png)

<span data-ttu-id="7f18c-224">針對3DObjectCollection 中的每個子物件**重複**此動作。</span><span class="sxs-lookup"><span data-stu-id="7f18c-224">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

> [!TIP]
> <span data-ttu-id="7f18c-225">如需如何執行事件的提醒，您可以參考[手追蹤手勢和可互動按鈕](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)的指示。</span><span class="sxs-lookup"><span data-stu-id="7f18c-225">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="4-implement-the-on-selected-event"></a><span data-ttu-id="7f18c-226">4. 在選取的事件上執行</span><span class="sxs-lookup"><span data-stu-id="7f18c-226">4. Implement the On Selected event</span></span>

<span data-ttu-id="7f18c-227">在 [階層] 視窗中，選取 [**乳酪**] 物件，然後在 **[選取的（）** ] 事件上建立新的、設定 [**乳酪**] 物件以接收事件，並定義**EyeTrackingTutorialDemo RotateTarget**作為要觸發的動作：</span><span class="sxs-lookup"><span data-stu-id="7f18c-227">In the Hierarchy window, select the **Cheese** object, then create a new **On Selected ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.RotateTarget** as the action to be triggered:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section3-step4-1.png)

<span data-ttu-id="7f18c-229">針對3DObjectCollection 中的每個子物件**重複**此動作。</span><span class="sxs-lookup"><span data-stu-id="7f18c-229">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a><span data-ttu-id="7f18c-230">5. 為編輯器內的模擬啟用模擬的監看式追蹤</span><span class="sxs-lookup"><span data-stu-id="7f18c-230">5. Enable simulated eye tracking for in-editor simulations</span></span>

<span data-ttu-id="7f18c-231">在 [階層] 視窗中，選取 [ **MixedRealityToolkit** ] 物件，然後在 [偵測器] 視窗中，選取 [**輸入**] 索引標籤，然後依序展開 [**輸入資料提供者**] 區段和 [**輸入模擬服務**] 區段，然後再複製**DefaultMixedRealityInputSimulationProfile** ，將其取代為您自己可自訂的**輸入模擬配置**</span><span class="sxs-lookup"><span data-stu-id="7f18c-231">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab, expand the **Input Data Providers** section and then the **Input Simulation Service** section, and clone the **DefaultMixedRealityInputSimulationProfile** to replace it with your own customizable **Input Simulation Profile**:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> <span data-ttu-id="7f18c-233">如需有關如何複製 MRTK 設定檔的提醒，您可以參閱[如何設定混合現實工具組設定檔](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)的指示。</span><span class="sxs-lookup"><span data-stu-id="7f18c-233">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

<span data-ttu-id="7f18c-234">在 [**眼睛模擬**] 區段中，核取 [**模擬眼睛位置**] 核取方塊以啟用眼睛追蹤模擬：</span><span class="sxs-lookup"><span data-stu-id="7f18c-234">In the **Eye Simulation** section, check the **Simulate Eye Position** checkbox to enable eye tracking simulation:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section3-step5-2.png)

<span data-ttu-id="7f18c-236">如果您現在進入遊戲模式，可以藉由調整視圖來測試您所執行的微調和中斷效果，讓游標到達其中一個物件，並使用 [手動互動] 或 [語音] 命令來選取物件：</span><span class="sxs-lookup"><span data-stu-id="7f18c-236">If you now enter Game mode, you can test the spin and blip effects you implemented by adjusting the view so the cursor hits one of the objects and using hand interaction or speech command to select the object:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> <span data-ttu-id="7f18c-238">如果您未使用 DefaultHoloLens2ConfigurationProfile 來複製可自訂的 MRTK 設定檔，請依照[設定混合現實工具](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)組指示中的指示進行，您的專案中可能不會啟用眼睛追蹤，而且必須啟用。</span><span class="sxs-lookup"><span data-stu-id="7f18c-238">If you did not use the DefaultHoloLens2ConfigurationProfile to clone your customizable MRTK configuration profile, as instructed in the [Configure the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) instructions, eye tracking may not be enable in your project and will need to be enabled.</span></span> <span data-ttu-id="7f18c-239">為此，您可以參閱 MRTK 指示[中的開始使用](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html)監看追蹤。</span><span class="sxs-lookup"><span data-stu-id="7f18c-239">For that, you can refer to the [Getting started with eye tracking in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) instructions.</span></span>

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a><span data-ttu-id="7f18c-240">6. 在 Visual Studio 專案的應用程式功能中啟用注視輸入</span><span class="sxs-lookup"><span data-stu-id="7f18c-240">6. Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

<span data-ttu-id="7f18c-241">從 Visual Studio 建立應用程式並將其部署到您的裝置之前，您必須先在專案的應用程式功能中啟用注視輸入。</span><span class="sxs-lookup"><span data-stu-id="7f18c-241">Before building and deploying your app from Visual Studio to your device, Gaze Input has to been enabled in the project's app capabilities.</span></span> <span data-ttu-id="7f18c-242">為此，您可以依照[HoloLens 2 指示來測試 Unity 應用程式](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2)。</span><span class="sxs-lookup"><span data-stu-id="7f18c-242">For this, you can follow the [Testing your Unity app on a HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="7f18c-243">恭喜</span><span class="sxs-lookup"><span data-stu-id="7f18c-243">Congratulations</span></span>

<span data-ttu-id="7f18c-244">您已成功將基本眼追蹤功能新增至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7f18c-244">You have successfully added basic eye tracking capabilities to your application.</span></span> <span data-ttu-id="7f18c-245">這些動作只是眼球追蹤功能無限可能性的開端。</span><span class="sxs-lookup"><span data-stu-id="7f18c-245">These actions are only the beginning of a world of possibilities with eye tracking.</span></span> <span data-ttu-id="7f18c-246">在本教學課程中，您也會瞭解其他的「高級輸入」功能，例如語音命令和移動流覽手勢。</span><span class="sxs-lookup"><span data-stu-id="7f18c-246">In this tutorial, you also learned about other advanced input features, such as voice commands and panning gestures.</span></span>

[<span data-ttu-id="7f18c-247">下一課： 7. 建立農曆模組範例應用程式</span><span class="sxs-lookup"><span data-stu-id="7f18c-247">Next Lesson: 7. Creating a Lunar Module sample application</span></span>](mrlearning-base-ch6.md)
