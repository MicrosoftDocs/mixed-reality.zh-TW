---
title: 入門教學課程 - 7。 建立登月小艇應用程式範例
description: 在本課程中，您將會結合從先前課程中所學習到的多個概念，以建立獨特的範例體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7b432c5ba0ebee5199f5abb1c26715185fc0d70d
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031537"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="b49e5-105">7.建立登月小艇應用程式範例</span><span class="sxs-lookup"><span data-stu-id="b49e5-105">7. Creating a Lunar Module sample application</span></span>
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

<span data-ttu-id="b49e5-106">在本教學課程中，我們會結合先前課程中的多個概念來建立獨特範例體驗。</span><span class="sxs-lookup"><span data-stu-id="b49e5-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="b49e5-107">您將了解如何建立元件組合應用程式，讓使用者必須使用追蹤的手部來挑選元件，並嘗試組合登月小艇。</span><span class="sxs-lookup"><span data-stu-id="b49e5-107">You will learn how to create a part assembly application whereby a user needs to use tracked hands to pick up parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="b49e5-108">您將會使用可點按的按鈕來將放置提示切換為開或關、重設體驗，以及將登月小艇發射到太空中！</span><span class="sxs-lookup"><span data-stu-id="b49e5-108">You will use pressable buttons to toggle placement hints on and off, to reset the experience, and to launch the lunar module into space!</span></span>

<span data-ttu-id="b49e5-109">在未來的教學課程中，您將以此體驗作為基礎持續建置，其中包括能運用 Azure Spatial Anchors 來進行空間對齊的強大多使用者使用案例。</span><span class="sxs-lookup"><span data-stu-id="b49e5-109">In future tutorials, you will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="b49e5-110">目標</span><span class="sxs-lookup"><span data-stu-id="b49e5-110">Objectives</span></span>

* <span data-ttu-id="b49e5-111">結合來自先前課程的多個概念以建立獨特體驗</span><span class="sxs-lookup"><span data-stu-id="b49e5-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
* <span data-ttu-id="b49e5-112">了解如何切換物件</span><span class="sxs-lookup"><span data-stu-id="b49e5-112">Learn how to toggle objects</span></span>
* <span data-ttu-id="b49e5-113">使用可點按的按鈕來觸發複雜事件</span><span class="sxs-lookup"><span data-stu-id="b49e5-113">Trigger complex events using pressable buttons</span></span>
* <span data-ttu-id="b49e5-114">使用 rigidbody 物理特性和力</span><span class="sxs-lookup"><span data-stu-id="b49e5-114">Use rigidbody physics and forces</span></span>
* <span data-ttu-id="b49e5-115">探索工具提示的使用</span><span class="sxs-lookup"><span data-stu-id="b49e5-115">Explore the use of tool tips</span></span>

## <a name="lunar-module-parts-overview"></a><span data-ttu-id="b49e5-116">登月小艇組件概觀</span><span class="sxs-lookup"><span data-stu-id="b49e5-116">Lunar Module Parts overview</span></span>
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

<span data-ttu-id="b49e5-117">在本節中，您將建立一個簡單的元件組合挑戰，其中使用者的目標是要將散佈在資料表上的五個元件放在登月小艇的正確位置上。</span><span class="sxs-lookup"><span data-stu-id="b49e5-117">In this section, you will create a simple part assembly challenge where the user's goal is to place five parts that are spread out on the table at the correct location on the Lunar Module.</span></span>

<span data-ttu-id="b49e5-118">達成此動作所需採取的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="b49e5-118">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="b49e5-119">將火箭發射器的 Prefab 新增至場景</span><span class="sxs-lookup"><span data-stu-id="b49e5-119">Add the Rocket Launcher prefab to the scene</span></span>
2. <span data-ttu-id="b49e5-120">為所有元件啟用物件操作</span><span class="sxs-lookup"><span data-stu-id="b49e5-120">Enable object manipulation for all the parts</span></span>
3. <span data-ttu-id="b49e5-121">新增和設定 Part Assembly Demo (指令碼) 元件</span><span class="sxs-lookup"><span data-stu-id="b49e5-121">Add and configure the Part Assembly Demo (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="b49e5-122">Part Assembly Demo (指令碼) 元件不是 MRTK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="b49e5-122">The Part Assembly Demo (Script) component is not part of MRTK.</span></span> <span data-ttu-id="b49e5-123">這是本教學課程資產隨附的元件。</span><span class="sxs-lookup"><span data-stu-id="b49e5-123">It was provided with this tutorial's assets.</span></span>

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a><span data-ttu-id="b49e5-124">1.將火箭發射器的 Prefab 新增至場景</span><span class="sxs-lookup"><span data-stu-id="b49e5-124">1. Add the Rocket Launcher prefab to the scene</span></span>

<span data-ttu-id="b49e5-125">在 [專案] 視窗中，瀏覽至 [資產]   > [MRTK.Tutorials.GettingStarted]   > [Prefabs]   > [RocketLauncher]  資料夾，將 **RocketLauncher** Prefab 拖曳到 [階層] 視窗中以新增至場景，然後將其放在適當位置，例如：</span><span class="sxs-lookup"><span data-stu-id="b49e5-125">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher** prefab into the Hierarchy window to add it to your scene, and then position it at a suitable location, for example:</span></span>

* <span data-ttu-id="b49e5-126">變形位置 X = 1.5、Y =-0.4、Z = 0，使其位於使用者腰部高度的右方</span><span class="sxs-lookup"><span data-stu-id="b49e5-126">Transform Position X = 1.5, Y = -0.4, Z = 0, so it is positioned to the right of the user at waist height</span></span>
* <span data-ttu-id="b49e5-127">變形旋轉 X = 0、Y = 180、Z = 0，使體驗的主要功能面對使用者</span><span class="sxs-lookup"><span data-stu-id="b49e5-127">Transform Rotation X = 0, Y = 180, Z = 0, so the main features of the experience faces the user</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a><span data-ttu-id="b49e5-129">2.為所有元件啟用物件操作</span><span class="sxs-lookup"><span data-stu-id="b49e5-129">2. Enable object manipulation for all the parts</span></span>

<span data-ttu-id="b49e5-130">在 [階層] 視窗中，找出 RocketLauncher > **LunarModuleParts** 物件，然後選取所有**子物件**，並加入 **Manipulation Handler (指令碼)** 元件和 **Near Interaction Grabbable (指令碼)** 元件，然後設定 Manipulation Handler (指令碼)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b49e5-130">In the Hierarchy window, locate the RocketLauncher > **LunarModuleParts** object and select all the **child objects**, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="b49e5-131">取消核取 [允許遠端操作]  核取方塊，僅限進行近處互動</span><span class="sxs-lookup"><span data-stu-id="b49e5-131">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>
* <span data-ttu-id="b49e5-132">將**兩手操作類型**變更為「移動旋轉」  ，以停用縮放功能</span><span class="sxs-lookup"><span data-stu-id="b49e5-132">Change **Two Handed Manipulation Type** to **Move Rotate** so scaling is disabled</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="b49e5-134">如需了解如何實作物件操作的提示 (包含逐步指示)，您可以參考 [操作 3D 物件](mrlearning-base-ch4.md#manipulating-3d-objects)的指示。</span><span class="sxs-lookup"><span data-stu-id="b49e5-134">For a reminder, with step by step instructions, on how to implement object manipulation, you can refer to the [Manipulating 3D Objects](mrlearning-base-ch4.md#manipulating-3d-objects) instructions.</span></span>

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a><span data-ttu-id="b49e5-135">3.新增和設定 Part Assembly Demo (指令碼) 元件</span><span class="sxs-lookup"><span data-stu-id="b49e5-135">3. Add and configure the Part Assembly Demo (Script) component</span></span>

<span data-ttu-id="b49e5-136">在仍選取所有 LunarModuleParts 子物件的情況下，新增 **Audio Source** 元件，然後進行設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b49e5-136">With all the LunarModuleParts child objects still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="b49e5-137">將適當的音訊片段指派給 [AudioClip]  欄位，例如 MRKT_Scale_Start</span><span class="sxs-lookup"><span data-stu-id="b49e5-137">Assign a suitable audio clip to the **AudioClip** field, for example, MRKT_Scale_Start</span></span>
* <span data-ttu-id="b49e5-138">取消核取 [喚醒時播放]  核取方塊，讓音訊片段不會在場景載入時自動播放</span><span class="sxs-lookup"><span data-stu-id="b49e5-138">Un-check the **Play On Awake** checkbox, so the audio clip does not automatically play when the scene loads</span></span>
* <span data-ttu-id="b49e5-139">將**空間混合**變更為 1，以啟用空間音訊</span><span class="sxs-lookup"><span data-stu-id="b49e5-139">Change **Spatial Blend** to 1, to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

<span data-ttu-id="b49e5-141">在仍選取所有 LunarModuleParts 子物件的情況下，新增 **Part Assembly Demo (指令碼)** 元件：</span><span class="sxs-lookup"><span data-stu-id="b49e5-141">With all the LunarModuleParts child objects still selected, add the **Part Assembly Demo  (Script)** component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

<span data-ttu-id="b49e5-143">在 [階層] 視窗中，選取 **RoverEnclosure** 物件，並設定其 **Part Assembly Demo (指令碼)** 元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b49e5-143">In the Hierarchy window, select the **RoverEnclosure** object and configure its **Part Assembly Demo (Script)** component as follows:</span></span>

* <span data-ttu-id="b49e5-144">針對 [要放置的物件]  欄位，請指派物件**本身**，在此案例中為 RoverEnclosure 物件</span><span class="sxs-lookup"><span data-stu-id="b49e5-144">To the **Object To Place** field, assign the object **itself**, in this case, the RoverEnclosure object</span></span>
* <span data-ttu-id="b49e5-145">針對 [要放置的位置]  欄位，請指派對應的 **PlacementHints** 物件，在此案例中為 RoverEnclosure_PlacementHint 物件</span><span class="sxs-lookup"><span data-stu-id="b49e5-145">To the **Location To Place** field, assign the corresponding **PlacementHints** object, in this case, the RoverEnclosure_PlacementHint object</span></span>
* <span data-ttu-id="b49e5-146">針對 [工具提示物件]  欄位，請指派對應的 **ToolTip**，在此案例中為 RoverEnclosure_ToolTip 物件</span><span class="sxs-lookup"><span data-stu-id="b49e5-146">To the **Tool Tip Object** field, assign the corresponding **ToolTip**, in this case, the RoverEnclosure_ToolTip object</span></span>
* <span data-ttu-id="b49e5-147">針對 [音訊來源]  欄位，請指派物件**本身**，在此案例中為 RoverEnclosure 物件</span><span class="sxs-lookup"><span data-stu-id="b49e5-147">To the **Audio Source** field, assign the object **itself**, in this case, the RoverEnclosure object</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

<span data-ttu-id="b49e5-149">針對其他每個 LunarModuleParts 子物件 (例如 FuelTank、EnergyCell、DockingPortal 和 ExternalSensor)，**重複**這些步驟。</span><span class="sxs-lookup"><span data-stu-id="b49e5-149">**Repeat** for each of the other LunarModuleParts child objects, i.e. FuelTank, EnergyCell, DockingPortal, and ExternalSensor.</span></span>

<span data-ttu-id="b49e5-150">如果您現在進入遊戲模式，並將「要放置的物件」移到靠近其對應的「位置」，您會注意到：</span><span class="sxs-lookup"><span data-stu-id="b49e5-150">If you now enter Game mode and move an 'Object To Place' close to it's corresponding 'Location To Place' you will notice:</span></span>

* <span data-ttu-id="b49e5-151">物件將會貼齊位置，並在 LunarModule 物件下成為子系，使其成為登月小艇的一部分</span><span class="sxs-lookup"><span data-stu-id="b49e5-151">The object will snap into place and be parented under the LunarModule object so it becomes part of the Lunar Module</span></span>
* <span data-ttu-id="b49e5-152">物件上的音訊來源會在物件位置上播放指派的音訊片段</span><span class="sxs-lookup"><span data-stu-id="b49e5-152">The Audio Source on the object will play the assigned Audio Clip at the location of the object</span></span>
* <span data-ttu-id="b49e5-153">對應的工具提示物件將會隱藏</span><span class="sxs-lookup"><span data-stu-id="b49e5-153">The corresponding Tool Tip object will be hidden</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> <span data-ttu-id="b49e5-155">如需如何使用編輯器內的輸入模擬的提示，您可以參考 [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[使用編輯器內的手動輸入模擬來測試場景](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)。</span><span class="sxs-lookup"><span data-stu-id="b49e5-155">For a reminder on how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="configuring-the-lunar-module"></a><span data-ttu-id="b49e5-156">設定登月小艇</span><span class="sxs-lookup"><span data-stu-id="b49e5-156">Configuring the Lunar Module</span></span>

<span data-ttu-id="b49e5-157">在本節中，您會將其他功能新增至火箭發射器應用程式，讓使用者可以：</span><span class="sxs-lookup"><span data-stu-id="b49e5-157">In this section, you will add additional features to the Rocket Launcher application so the user can:</span></span>

* <span data-ttu-id="b49e5-158">與登月小艇互動</span><span class="sxs-lookup"><span data-stu-id="b49e5-158">Interact with the Lunar Module</span></span>
* <span data-ttu-id="b49e5-159">將登月小艇發射到太空中，並在發射時播放音效</span><span class="sxs-lookup"><span data-stu-id="b49e5-159">Launch the Lunar Module into space and play a sound when it is launched</span></span>
* <span data-ttu-id="b49e5-160">重設應用程式，讓登月小艇和所有元件都放回其原本位置</span><span class="sxs-lookup"><span data-stu-id="b49e5-160">Reset the application so the Lunar Module and all the parts are placed back to their original position</span></span>
* <span data-ttu-id="b49e5-161">隱藏放置提示，使元件組合的挑戰變得更困難。</span><span class="sxs-lookup"><span data-stu-id="b49e5-161">Hide the placement hints to make the part assembly challenge more difficult.</span></span>

<span data-ttu-id="b49e5-162">達成此動作所需採取的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="b49e5-162">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="b49e5-163">啟用物件操作</span><span class="sxs-lookup"><span data-stu-id="b49e5-163">Enable object manipulation</span></span>
2. <span data-ttu-id="b49e5-164">啟用物理特性</span><span class="sxs-lookup"><span data-stu-id="b49e5-164">Enable physics</span></span>
3. <span data-ttu-id="b49e5-165">新增音訊來源元件</span><span class="sxs-lookup"><span data-stu-id="b49e5-165">Add an Audio Source component</span></span>
4. <span data-ttu-id="b49e5-166">新增和設定啟動 Launch Lunar Module (指令碼) 元件</span><span class="sxs-lookup"><span data-stu-id="b49e5-166">Add and configure the Launch Lunar Module (Script) component</span></span>
5. <span data-ttu-id="b49e5-167">新增和設定 Toggle Placement Hints (指令碼) 元件</span><span class="sxs-lookup"><span data-stu-id="b49e5-167">Add and configure the Toggle Placement Hints (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="b49e5-168">Launch Lunar Module (指令碼) 元件和 Toggle Placement Hints (指令碼) 元件不是 MRTK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="b49e5-168">The Launch Lunar Module (Script) component and the Toggle Placement Hints (Script) component are not part of MRTK.</span></span> <span data-ttu-id="b49e5-169">這些是本教學課程資產隨附的元件。</span><span class="sxs-lookup"><span data-stu-id="b49e5-169">They were provided with this tutorial's assets.</span></span>

### <a name="1-enable-object-manipulation"></a><span data-ttu-id="b49e5-170">1.啟用物件操作</span><span class="sxs-lookup"><span data-stu-id="b49e5-170">1. Enable object manipulation</span></span>

<span data-ttu-id="b49e5-171">在 [階層] 視窗中，選取 RocketLauncher > **LunarModule** 物件，新增 **Manipulation Handler (指令碼)** 元件和 **Near Interaction Grabbable (指令碼)** 元件，然後設定 Manipulation Handler (指令碼)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b49e5-171">In the Hierarchy window, select the RocketLauncher > **LunarModule** object, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="b49e5-172">取消核取 [允許遠端操作]  核取方塊，僅限進行近處互動</span><span class="sxs-lookup"><span data-stu-id="b49e5-172">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>
* <span data-ttu-id="b49e5-173">將**兩手操作類型**變更為「移動旋轉」，以停用縮放功能</span><span class="sxs-lookup"><span data-stu-id="b49e5-173">Change **Two Handed Manipulation Type** to Move Rotate so scaling is disabled</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a><span data-ttu-id="b49e5-175">2.啟用物理特性</span><span class="sxs-lookup"><span data-stu-id="b49e5-175">2. Enable physics</span></span>

<span data-ttu-id="b49e5-176">在仍選取 RocketLauncher  > **LunarModule** 物件的情況下，新增 **Rigidbody** 元件，然後依照下列方式進行設定：</span><span class="sxs-lookup"><span data-stu-id="b49e5-176">With the RocketLauncher > **LunarModule** object still selected, add a **Rigidbody** component and then configure it as follows:</span></span>

* <span data-ttu-id="b49e5-177">取消核取 [使用引力]  核取方塊，讓登月小艇不會受到引力的影響</span><span class="sxs-lookup"><span data-stu-id="b49e5-177">Un-check the **Use Gravity** checkbox so the Lunar Module is not affected by gravity</span></span>
* <span data-ttu-id="b49e5-178">核取 [使用運動學]  核取方塊，讓登月小艇一開始不會受到物理力的影響</span><span class="sxs-lookup"><span data-stu-id="b49e5-178">Check the **Is Kinematic** checkbox so the Lunar Module initially isn't affected by physic forces</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a><span data-ttu-id="b49e5-180">3.新增音訊來源元件</span><span class="sxs-lookup"><span data-stu-id="b49e5-180">3. Add an Audio Source component</span></span>

<span data-ttu-id="b49e5-181">在仍選取 RocketLauncher > **LunarModule** 物件的情況下，新增 **Audio Source** 元件，然後進行設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b49e5-181">With the RocketLauncher > **LunarModule** object still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="b49e5-182">將**空間混合**變更為 1，以啟用空間音訊</span><span class="sxs-lookup"><span data-stu-id="b49e5-182">Change **Spatial Blend** to 1 to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a><span data-ttu-id="b49e5-184">4.新增和設定啟動 Launch Lunar Module (指令碼) 元件</span><span class="sxs-lookup"><span data-stu-id="b49e5-184">4. Add and configure the Launch Lunar Module (Script) component</span></span>

<span data-ttu-id="b49e5-185">在仍選取 RocketLauncher > **LunarModule** 物件的情況下，新增 **Launch Lunar Module (指令碼)** 元件，然後依照下列方式進行設定：</span><span class="sxs-lookup"><span data-stu-id="b49e5-185">With the RocketLauncher > **LunarModule** object still selected, add the **Launch Lunar Module (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="b49e5-186">變更 [推力]  的值，讓登月小艇在發射時緩緩飛起，例如，變更為 0.01</span><span class="sxs-lookup"><span data-stu-id="b49e5-186">Change **Thrust** value so the Lunar Module will fly up gracefully when launched, for example, to 0.01</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a><span data-ttu-id="b49e5-188">5.新增和設定 Toggle Placement Hints (指令碼) 元件</span><span class="sxs-lookup"><span data-stu-id="b49e5-188">5. Add and configure the Toggle Placement Hints (Script) component</span></span>

<span data-ttu-id="b49e5-189">在仍選取 RocketLauncher > **LunarModule** 物件的情況下，新增 **Toggle Placement Hints (指令碼)** 元件，然後依照下列方式進行設定：</span><span class="sxs-lookup"><span data-stu-id="b49e5-189">With the RocketLauncher > **LunarModule** object still selected, add the **Toggle Placement Hints (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="b49e5-190">將遊戲物件陣列的**大小**屬性設定為 5</span><span class="sxs-lookup"><span data-stu-id="b49e5-190">Set the Game Object Array **Size** property to 5</span></span>
* <span data-ttu-id="b49e5-191">將每個 RocketLauncher > LunarModule > **PlacementHints** 物件的**子物件**指派至遊戲物件陣列中的 [元素]  欄位：</span><span class="sxs-lookup"><span data-stu-id="b49e5-191">Assign each of the RocketLauncher > LunarModule > **PlacementHints** object's **child objects** to the an **Element** field in the Game Object Array:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a><span data-ttu-id="b49e5-193">設定發射按鈕</span><span class="sxs-lookup"><span data-stu-id="b49e5-193">Configuring the Launch button</span></span>

<span data-ttu-id="b49e5-194">在 [階層] 視窗中，選取 RocketLauncher > Buttons > **LaunchButton** 物件，然後在 **Pressable Button (指令碼)** 元件上，建立新的 **Button Pressed ()** 事件、設定 **LunarModule** 物件以接收事件，並將 **LaunchLunarModule.StartThruster** 定義為要觸發的動作：</span><span class="sxs-lookup"><span data-stu-id="b49e5-194">In the Hierarchy window, select the RocketLauncher > Buttons > **LaunchButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StartThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="b49e5-196">如需有關如何實作事件的提示，您可以參閱[手部追蹤手勢和可互動按鈕](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)的指示。</span><span class="sxs-lookup"><span data-stu-id="b49e5-196">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

<span data-ttu-id="b49e5-197">在仍選取 RocketLauncher > Buttons > **LaunchButton** 物件的情況下，於 **Pressable Button (指令碼)** 元件上建立新的 **Button Pressed ()** 事件、設定 **LunarModule** 物件以接收事件、將 **AudioSource.PlayOneShot** 定義為要觸發的動作，然後對 [音訊片段]  欄位指派合適的音訊片段，例如 MRTK_Gem 音訊片段：</span><span class="sxs-lookup"><span data-stu-id="b49e5-197">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

<span data-ttu-id="b49e5-199">在仍選取 RocketLauncher > Buttons > **LaunchButton**物件的情況下，於 **Pressable Button (指令碼)** 元件上建立新的 **Touch End ()** 事件、設定 **LunarModule** 物件以接收事件，並將 **LaunchLunarModule.StopThruster** 定義為要觸發的動作：</span><span class="sxs-lookup"><span data-stu-id="b49e5-199">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Touch End ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StopThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

<span data-ttu-id="b49e5-201">如果您現在進入遊戲模式，並按下 [發射] 按鈕，您會聽到播放的音訊片段，如果您將 [發射] 按鈕按下大約一秒或更長的時間，就會看到登月小艇發射到太空中：</span><span class="sxs-lookup"><span data-stu-id="b49e5-201">If you now enter Game mode and press the Launch button, you will hear the audio clip play, and if you hold the Launch button down for about a second or longer, you will see the Lunar Module launch into space:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a><span data-ttu-id="b49e5-203">設定重設按鈕</span><span class="sxs-lookup"><span data-stu-id="b49e5-203">Configuring the Reset button</span></span>

<span data-ttu-id="b49e5-204">在 [階層] 視窗中，選取 RocketLauncher > Buttons > **ResetButton** 物件，然後在 **Pressable Button (指令碼)** 元件上，建立新的 **Button Pressed ()** 事件、設定 **LunarModule** 物件以接收事件，並將 **LaunchLunarModule.ResetModule** 定義為要觸發的動作：</span><span class="sxs-lookup"><span data-stu-id="b49e5-204">In the Hierarchy window, select the RocketLauncher > Buttons > **ResetButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.ResetModule** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

<span data-ttu-id="b49e5-206">在仍選取 RocketLauncher > Buttons > **ResetButton** 物件的情況下，於 **Pressable Button (指令碼)** 元件上建立新的 **Button Pressed ()** 事件、設定 **RocketLauncher** 以接收事件、將 **GameObject.BroadcastMessage** 定義為要觸發的動作，然後在訊息欄位中輸入 **ResetPlacement**：</span><span class="sxs-lookup"><span data-stu-id="b49e5-206">With the RocketLauncher > Buttons > **ResetButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **RocketLauncher** object to receive the event, define **GameObject.BroadcastMessage** as the action to be triggered, and enter **ResetPlacement** in message field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="b49e5-208">GameObject.BroadcastMessage 動作會將 ResetPlacement 訊息從 RocketLauncher 物件傳送到其所有子物件。</span><span class="sxs-lookup"><span data-stu-id="b49e5-208">The GameObject.BroadcastMessage action sends the ResetPlacement message from the RocketLauncher object to all its child object.</span></span> <span data-ttu-id="b49e5-209">在您新增至所有 LunarModuleParts 子物件的 Part Assembly Demo (指令碼) 元件中，已定義為具有 ResetPlacement 函式的任何子物件都可叫用 ResetPlacement 函式來重設該子物件的位置。</span><span class="sxs-lookup"><span data-stu-id="b49e5-209">Any child object that has the ResetPlacement function, which is defined in the Part Assembly Demo (Script) component you added to all the LunarModuleParts child object, will invoke the ResetPlacement function which resets that child object's placement.</span></span>

<span data-ttu-id="b49e5-210">如果您現在進入遊戲模式，移動部分元件和/或發射登月小艇，然後按下 [重設] 按鈕，您將會看到元件和/或登月小艇重設至其原本位置：</span><span class="sxs-lookup"><span data-stu-id="b49e5-210">If you now enter Game mode, move some parts and/or launch the Lunar Module, and then press the Reset button you will see the parts and/or the Lunar Module being reset to their original position:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="b49e5-212">設定放置提示按鈕</span><span class="sxs-lookup"><span data-stu-id="b49e5-212">Configuring the Placement Hints button</span></span>
<!-- TODO: Rename to 'Configuring the Hints button'-->

<span data-ttu-id="b49e5-213">在 [階層] 視窗中，選取 RocketLauncher > Buttons > **HintsButton** 物件，然後在 **Pressable Button (指令碼)** 元件上，建立新的 **Button Pressed ()** 事件、設定 **LunarModule** 物件以接收事件，並將 **TogglePlacementHints.ToggleGameObjects** 定義為要觸發的動作：</span><span class="sxs-lookup"><span data-stu-id="b49e5-213">In the Hierarchy window, select the RocketLauncher > Buttons > **HintsButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **TogglePlacementHints.ToggleGameObjects** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

<span data-ttu-id="b49e5-215">如果您現在進入遊戲模式，您會注意到，半透明的放置提示已預設為停用，但是您可以按下 [提示] 按鈕，將其切換為開啟或關閉：</span><span class="sxs-lookup"><span data-stu-id="b49e5-215">If you now enter Game mode you will notice that the translucent placement hints are disabled by default, but that you can toggle them on and off by pressing the Hints button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="b49e5-217">恭喜！</span><span class="sxs-lookup"><span data-stu-id="b49e5-217">Congratulations</span></span>

<span data-ttu-id="b49e5-218">您已完整地設定好這個應用程式。</span><span class="sxs-lookup"><span data-stu-id="b49e5-218">You have fully configured this application.</span></span> <span data-ttu-id="b49e5-219">現在，您的應用程式可讓使用者完整組合登月小艇、發射登月小艇、切換提示，然後將應用程式重設以重新開始。</span><span class="sxs-lookup"><span data-stu-id="b49e5-219">Now, your application allows users to fully assemble the Lunar Module, launch the Lunar Module, toggle hints, and reset the application to start again.</span></span>
