---
title: 使用者入門教學課程-7。 建立農曆模組範例應用程式
description: 在這一課，您將結合從先前課程中學到的多個概念，以建立獨特的範例體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: b5b1bd0115822449bd6098f78cfc94d909169737
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129399"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="1e50a-105">7. 建立農曆模組範例應用程式</span><span class="sxs-lookup"><span data-stu-id="1e50a-105">7. Creating a Lunar Module sample application</span></span>
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

<span data-ttu-id="1e50a-106">在本教學課程中，會將多個概念與前一課結合，以建立獨特的範例體驗。</span><span class="sxs-lookup"><span data-stu-id="1e50a-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="1e50a-107">您將瞭解如何建立元件元件應用程式，讓使用者必須使用追蹤的手來挑選元件，並嘗試組合陰曆模組。</span><span class="sxs-lookup"><span data-stu-id="1e50a-107">You will learn how to create a part assembly application whereby a user needs to use tracked hands to pick up parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="1e50a-108">您將使用 [pressable] 按鈕來開啟和關閉放置提示、重設體驗，以及啟動農曆模組到空間中！</span><span class="sxs-lookup"><span data-stu-id="1e50a-108">You will use pressable buttons to toggle placement hints on and off, to reset the experience, and to launch the lunar module into space!</span></span>

<span data-ttu-id="1e50a-109">在未來的教學課程中，您將繼續以這項體驗為基礎，其中包含強大的多使用者使用案例，可運用 Azure 空間錨點進行空間對齊。</span><span class="sxs-lookup"><span data-stu-id="1e50a-109">In future tutorials, you will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="1e50a-110">目標</span><span class="sxs-lookup"><span data-stu-id="1e50a-110">Objectives</span></span>

* <span data-ttu-id="1e50a-111">結合來自先前課程的多個概念以建立獨特體驗</span><span class="sxs-lookup"><span data-stu-id="1e50a-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
* <span data-ttu-id="1e50a-112">了解如何切換物件</span><span class="sxs-lookup"><span data-stu-id="1e50a-112">Learn how to toggle objects</span></span>
* <span data-ttu-id="1e50a-113">使用可點按的按鈕來觸發複雜事件</span><span class="sxs-lookup"><span data-stu-id="1e50a-113">Trigger complex events using pressable buttons</span></span>
* <span data-ttu-id="1e50a-114">使用 rigidbody 物理特性和力</span><span class="sxs-lookup"><span data-stu-id="1e50a-114">Use rigidbody physics and forces</span></span>
* <span data-ttu-id="1e50a-115">探索工具提示的使用</span><span class="sxs-lookup"><span data-stu-id="1e50a-115">Explore the use of tool tips</span></span>

## <a name="lunar-module-parts-overview"></a><span data-ttu-id="1e50a-116">陰曆模組元件總覽</span><span class="sxs-lookup"><span data-stu-id="1e50a-116">Lunar Module Parts overview</span></span>
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

<span data-ttu-id="1e50a-117">在本節中，您將建立一個簡單的部分元件挑戰，使用者的目標是要將在該資料表上散佈的五個部分放在農曆模組的正確位置。</span><span class="sxs-lookup"><span data-stu-id="1e50a-117">In this section, you will create a simple part assembly challenge where the user's goal is to place five parts that are spread out on the table at the correct location on the Lunar Module.</span></span>

<span data-ttu-id="1e50a-118">達成此目標所需採取的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="1e50a-118">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="1e50a-119">將 Rocket 啟動器 prefab 新增至場景</span><span class="sxs-lookup"><span data-stu-id="1e50a-119">Add the Rocket Launcher prefab to the scene</span></span>
2. <span data-ttu-id="1e50a-120">啟用所有元件的物件操作</span><span class="sxs-lookup"><span data-stu-id="1e50a-120">Enable object manipulation for all the parts</span></span>
3. <span data-ttu-id="1e50a-121">新增和設定元件元件示範（腳本）元件</span><span class="sxs-lookup"><span data-stu-id="1e50a-121">Add and configure the Part Assembly Demo (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="1e50a-122">部分元件示範（腳本）元件不是 MRTK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="1e50a-122">The Part Assembly Demo (Script) component is not part of MRTK.</span></span> <span data-ttu-id="1e50a-123">本教學課程的資產提供此說明。</span><span class="sxs-lookup"><span data-stu-id="1e50a-123">It was provided with this tutorial's assets.</span></span>

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a><span data-ttu-id="1e50a-124">1. 將 Rocket 啟動器 prefab 新增至場景</span><span class="sxs-lookup"><span data-stu-id="1e50a-124">1. Add the Rocket Launcher prefab to the scene</span></span>

<span data-ttu-id="1e50a-125">在 [專案] 視窗中，流覽至 [**資產**] > **MRTK。GettingStarted** > **Prefabs** > **RocketLauncher**資料夾，將**RocketLauncher** prefab 拖曳到 [階層] 視窗中，將它新增至您的場景，然後將它放置在適當的位置，例如：</span><span class="sxs-lookup"><span data-stu-id="1e50a-125">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher** prefab into the Hierarchy window to add it to your scene, and then position it at a suitable location, for example:</span></span>

* <span data-ttu-id="1e50a-126">轉換位置 X = 1.5、Y =-0.4、Z = 0，使其位於 waist height 的使用者右方</span><span class="sxs-lookup"><span data-stu-id="1e50a-126">Transform Position X = 1.5, Y = -0.4, Z = 0, so it is positioned to the right of the user at waist height</span></span>
* <span data-ttu-id="1e50a-127">轉換旋轉 X = 0、Y = 180、Z = 0，因此體驗的主要功能會面對使用者</span><span class="sxs-lookup"><span data-stu-id="1e50a-127">Transform Rotation X = 0, Y = 180, Z = 0, so the main features of the experience faces the user</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a><span data-ttu-id="1e50a-129">2. 為所有元件啟用物件操作</span><span class="sxs-lookup"><span data-stu-id="1e50a-129">2. Enable object manipulation for all the parts</span></span>

<span data-ttu-id="1e50a-130">在 [階層] 視窗中，找出 RocketLauncher > **LunarModuleParts**物件，並選取所有**子物件**、新增**操作處理常式（腳本）** 元件和**近端互動 Grabbable （腳本）** 元件，然後設定操作處理常式（腳本），如下所示：</span><span class="sxs-lookup"><span data-stu-id="1e50a-130">In the Hierarchy window, locate the RocketLauncher > **LunarModuleParts** object and select all the **child objects**, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="1e50a-131">變更**兩個右手操作類型**以移動旋轉，以停用調整</span><span class="sxs-lookup"><span data-stu-id="1e50a-131">Change **Two Handed Manipulation Type** to Move Rotate so scaling is disabled</span></span>
* <span data-ttu-id="1e50a-132">取消核取 [**允許**最大操作] 核取方塊，只允許近乎互動</span><span class="sxs-lookup"><span data-stu-id="1e50a-132">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="1e50a-134">如需提醒，使用逐步指示，瞭解如何執行物件操作，您可以參考[處理3D 物件](mrlearning-base-ch4.md#manipulating-3d-objects)的指示。</span><span class="sxs-lookup"><span data-stu-id="1e50a-134">For a reminder, with step by step instructions, on how to implement object manipulation, you can refer to the [Manipulating 3D Objects](mrlearning-base-ch4.md#manipulating-3d-objects) instructions.</span></span>

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a><span data-ttu-id="1e50a-135">3. 新增和設定元件元件示範（腳本）元件</span><span class="sxs-lookup"><span data-stu-id="1e50a-135">3. Add and configure the Part Assembly Demo (Script) component</span></span>

<span data-ttu-id="1e50a-136">在仍選取所有 LunarModuleParts 子物件的情況下，新增**音訊來源**元件，然後進行設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1e50a-136">With all the LunarModuleParts child objects still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="1e50a-137">將適當的音訊剪輯指派給**AudioClip**欄位，例如，MRKT_Scale_Start</span><span class="sxs-lookup"><span data-stu-id="1e50a-137">Assign a suitable audio clip to the **AudioClip** field, for example, MRKT_Scale_Start</span></span>
* <span data-ttu-id="1e50a-138">取消勾選 [**在喚醒時播放**] 核取方塊，讓音訊剪輯不會在場景載入時自動播放</span><span class="sxs-lookup"><span data-stu-id="1e50a-138">Un-check the **Play On Awake** checkbox, so the audio clip does not automatically play when the scene loads</span></span>
* <span data-ttu-id="1e50a-139">將**空間 Blend**變更為1，以啟用空間音訊</span><span class="sxs-lookup"><span data-stu-id="1e50a-139">Change **Spatial Blend** to 1, to enable spatial audio</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial6-section1-step2-1.png)

<span data-ttu-id="1e50a-141">在仍選取所有 LunarModuleParts 子物件的情況下，新增元件元件**示範（腳本）** 元件：</span><span class="sxs-lookup"><span data-stu-id="1e50a-141">With all the LunarModuleParts child objects still selected, add the **Part Assembly Demo  (Script)** component:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial6-section1-step2-2.png)

<span data-ttu-id="1e50a-143">在 [階層] 視窗中，選取 [ **RoverEnclosure** ] 物件，並設定其 [元件元件**示範（腳本）** ] 元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1e50a-143">In the Hierarchy window, select the **RoverEnclosure** object and configure its **Part Assembly Demo (Script)** component as follows:</span></span>

* <span data-ttu-id="1e50a-144">在 [**要放置的物件**] 欄位中，指派物件本身，在此案例中為**RoverEnclosure**物件</span><span class="sxs-lookup"><span data-stu-id="1e50a-144">To the **Object To Place** field, assign the object itself, in this case, the **RoverEnclosure** object</span></span>
* <span data-ttu-id="1e50a-145">在 [**要放置的位置**] 欄位中，指派對應的 PlacementHints 物件（在此案例中為**RoverEnclosure_PlacementHints**物件）</span><span class="sxs-lookup"><span data-stu-id="1e50a-145">To the **Location To Place** field, assign the corresponding PlacementHints object, in this case, the **RoverEnclosure_PlacementHints** object</span></span>
* <span data-ttu-id="1e50a-146">在 [**工具提示物件**] 欄位中，指派對應的 ToolTipObject，在此案例中為**RoverEnclosure_ToolTip**物件</span><span class="sxs-lookup"><span data-stu-id="1e50a-146">To the **Tool Tip Object** field, assign the corresponding ToolTipObject, in this case, the **RoverEnclosure_ToolTip** object</span></span>
* <span data-ttu-id="1e50a-147">在 [**音訊來源**] 欄位中，指派物件本身，在此案例中為**RoverEnclosure**物件</span><span class="sxs-lookup"><span data-stu-id="1e50a-147">To the **Audio Source** field, assign the object itself, in this case, the **RoverEnclosure** object</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial6-section1-step2-3.png)

<span data-ttu-id="1e50a-149">針對每個其他 LunarModuleParts 子物件**重複**，亦即 FuelTank、EnergyCell、DockingPortal 和 ExternalSensor。</span><span class="sxs-lookup"><span data-stu-id="1e50a-149">**Repeat** for each of the other LunarModuleParts child objects, i.e. FuelTank, EnergyCell, DockingPortal, and ExternalSensor.</span></span>

<span data-ttu-id="1e50a-150">如果您現在進入遊戲模式，並將「物件」放在靠近其對應的「位置」，您會注意到：</span><span class="sxs-lookup"><span data-stu-id="1e50a-150">If you now enter Game mode and move an 'Object To Place' close to it's corresponding 'Location To Place' you will notice:</span></span>

* <span data-ttu-id="1e50a-151">物件將會貼齊位置，並在 LunarModule 物件下成為父代，使其成為陰曆模組的一部分</span><span class="sxs-lookup"><span data-stu-id="1e50a-151">The object will snap into place and be parented under the LunarModule object so it becomes part of the Lunar Module</span></span>
* <span data-ttu-id="1e50a-152">物件上的音訊來源會在物件的位置播放指派的音訊剪輯</span><span class="sxs-lookup"><span data-stu-id="1e50a-152">The Audio Source on the object will play the assigned Audio Clip at the location of the object</span></span>
* <span data-ttu-id="1e50a-153">對應的工具提示物件將會隱藏</span><span class="sxs-lookup"><span data-stu-id="1e50a-153">The corresponding Tool Tip object will be hidden</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> <span data-ttu-id="1e50a-155">如需有關如何使用編輯器內輸入模擬的提醒，您可以參考[MRTK 檔入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[使用編輯器內的手寫輸入模擬來測試場景](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)指南。</span><span class="sxs-lookup"><span data-stu-id="1e50a-155">For a reminder on how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="configuring-the-lunar-module"></a><span data-ttu-id="1e50a-156">設定登月小艇</span><span class="sxs-lookup"><span data-stu-id="1e50a-156">Configuring the Lunar Module</span></span>

<span data-ttu-id="1e50a-157">在本節中，您會將其他功能新增至 Rocket 啟動器應用程式，讓使用者可以：</span><span class="sxs-lookup"><span data-stu-id="1e50a-157">In this section, you will add additional features to the Rocket Launcher application so the user can:</span></span>

* <span data-ttu-id="1e50a-158">與陰曆模組互動</span><span class="sxs-lookup"><span data-stu-id="1e50a-158">Interact with the Lunar Module</span></span>
* <span data-ttu-id="1e50a-159">將農曆模組啟動到空間中，並在啟動時播放音效</span><span class="sxs-lookup"><span data-stu-id="1e50a-159">Launch the Lunar Module into space and play a sound when it is launched</span></span>
* <span data-ttu-id="1e50a-160">重設應用程式，使陰曆模組和所有元件都放回其原始位置</span><span class="sxs-lookup"><span data-stu-id="1e50a-160">Reset the application so the Lunar Module and all the part are placed back to their original position</span></span>
* <span data-ttu-id="1e50a-161">隱藏放置提示，使部分元件的挑戰變得更困難。</span><span class="sxs-lookup"><span data-stu-id="1e50a-161">Hide the placement hints to make the part assembly challenge more difficult.</span></span>

<span data-ttu-id="1e50a-162">達成此目標所需採取的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="1e50a-162">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="1e50a-163">啟用物件操作</span><span class="sxs-lookup"><span data-stu-id="1e50a-163">Enable object manipulation</span></span>
2. <span data-ttu-id="1e50a-164">啟用物理</span><span class="sxs-lookup"><span data-stu-id="1e50a-164">Enable physics</span></span>
3. <span data-ttu-id="1e50a-165">新增音訊來源元件</span><span class="sxs-lookup"><span data-stu-id="1e50a-165">Add an Audio Source component</span></span>
4. <span data-ttu-id="1e50a-166">新增和設定啟動陰曆模組（腳本）元件</span><span class="sxs-lookup"><span data-stu-id="1e50a-166">Add and configure the Launch Lunar Module (Script) component</span></span>
5. <span data-ttu-id="1e50a-167">新增和設定切換位置提示（腳本）元件</span><span class="sxs-lookup"><span data-stu-id="1e50a-167">Add and configure the Toggle Placement Hints (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="1e50a-168">啟動陰曆模組（腳本）元件和切換放置提示（腳本）元件不是 MRTK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="1e50a-168">The Launch Lunar Module (Script) component and the Toggle Placement Hints (Script) component are not part of MRTK.</span></span> <span data-ttu-id="1e50a-169">這是本教學課程的資產所提供的。</span><span class="sxs-lookup"><span data-stu-id="1e50a-169">They were provided with this tutorial's assets.</span></span>

### <a name="1-enable-object-manipulation"></a><span data-ttu-id="1e50a-170">1. 啟用物件操作</span><span class="sxs-lookup"><span data-stu-id="1e50a-170">1. Enable object manipulation</span></span>

<span data-ttu-id="1e50a-171">在 [階層] 視窗中，選取 RocketLauncher > **LunarModule**物件、新增**操作處理常式（腳本）** 元件和**近乎互動 Grabbable （腳本）** 元件，然後設定操作處理常式（腳本），如下所示：</span><span class="sxs-lookup"><span data-stu-id="1e50a-171">In the Hierarchy window, select the RocketLauncher > **LunarModule** object, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="1e50a-172">變更**兩個右手操作類型**以移動旋轉，以停用調整</span><span class="sxs-lookup"><span data-stu-id="1e50a-172">Change **Two Handed Manipulation Type** to Move Rotate so scaling is disabled</span></span>
* <span data-ttu-id="1e50a-173">取消核取 [**允許**最大操作] 核取方塊，只允許近乎互動</span><span class="sxs-lookup"><span data-stu-id="1e50a-173">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a><span data-ttu-id="1e50a-175">2. 啟用物理</span><span class="sxs-lookup"><span data-stu-id="1e50a-175">2. Enable physics</span></span>

<span data-ttu-id="1e50a-176">在仍選取 RocketLauncher > **LunarModule**物件的情況下，新增 Rigidbody 元件，然後進行設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1e50a-176">With the RocketLauncher > **LunarModule** object still selected, add a Rigidbody component and then configure it as follows:</span></span>

* <span data-ttu-id="1e50a-177">取消核取 [**使用重心**] 核取方塊，讓陰曆模組不會受到引力的影響</span><span class="sxs-lookup"><span data-stu-id="1e50a-177">Un-check the **Use Gravity** checkbox so the Lunar Module is not affected by gravity</span></span>
* <span data-ttu-id="1e50a-178">勾選 [**是運動學**] 核取方塊，讓陰曆模組一開始不會受到 physic 強制影響</span><span class="sxs-lookup"><span data-stu-id="1e50a-178">Check the **Is Kinematic** checkbox so the Lunar Module initially isn't affected by physic forces</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a><span data-ttu-id="1e50a-180">3. 新增音訊來源元件</span><span class="sxs-lookup"><span data-stu-id="1e50a-180">3. Add an Audio Source component</span></span>

<span data-ttu-id="1e50a-181">在仍選取 RocketLauncher > **LunarModule**物件的情況下，新增**音訊來源**元件，然後進行設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1e50a-181">With the RocketLauncher > **LunarModule** object still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="1e50a-182">將**空間 Blend**變更為1以啟用空間音訊</span><span class="sxs-lookup"><span data-stu-id="1e50a-182">Change **Spatial Blend** to 1 to enable spatial audio</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a><span data-ttu-id="1e50a-184">4. 新增和設定啟動陰曆模組（腳本）元件</span><span class="sxs-lookup"><span data-stu-id="1e50a-184">4. Add and configure the Launch Lunar Module (Script) component</span></span>

<span data-ttu-id="1e50a-185">在仍選取 RocketLauncher > **LunarModule**物件的情況下，新增 [**啟動陰曆模組（腳本）** ] 元件，然後進行設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1e50a-185">With the RocketLauncher > **LunarModule** object still selected, add the **Launch Lunar Module (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="1e50a-186">變更**天生**值，讓陰曆模組在啟動時正常運作，例如，到0.01</span><span class="sxs-lookup"><span data-stu-id="1e50a-186">Change **Thrust** value so the Lunar Module will fly up gracefully when launched, for example, to 0.01</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a><span data-ttu-id="1e50a-188">5. 新增和設定切換位置提示（腳本）元件</span><span class="sxs-lookup"><span data-stu-id="1e50a-188">5. Add and configure the Toggle Placement Hints (Script) component</span></span>

<span data-ttu-id="1e50a-189">在仍選取 RocketLauncher > **LunarModule**物件的情況下，新增**切換位置提示（腳本）** 元件，然後進行設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1e50a-189">With the RocketLauncher > **LunarModule** object still selected, add the **Toggle Placement Hints (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="1e50a-190">將 [遊戲物件陣列**大小**] 屬性設定為5</span><span class="sxs-lookup"><span data-stu-id="1e50a-190">Set the Game Object Array **Size** property to 5</span></span>
* <span data-ttu-id="1e50a-191">將每個**PlacementHints**物件的**子物件**指派給遊戲物件陣列中的**元素**欄位：</span><span class="sxs-lookup"><span data-stu-id="1e50a-191">Assign each of the **PlacementHints** object's **child objects** to the an **Element** field in the Game Object Array:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a><span data-ttu-id="1e50a-193">設定 [啟動] 按鈕</span><span class="sxs-lookup"><span data-stu-id="1e50a-193">Configuring the Launch button</span></span>

<span data-ttu-id="1e50a-194">在 階層 視窗中，選取 RocketLauncher > 按鈕 > **LaunchButton**物件，然後在  **Pressable 按鈕（腳本）** 元件上，建立已按下的新**按鈕（）** 事件、設定**LunarModule**物件以接收事件，並將**LaunchLunarModule**定義為要觸發的動作：</span><span class="sxs-lookup"><span data-stu-id="1e50a-194">In the Hierarchy window, select the RocketLauncher > Buttons > **LaunchButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StartThruster** as the action to be triggered:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="1e50a-196">如需如何執行事件的提醒，您可以參考[手追蹤手勢和可互動按鈕](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)的指示。</span><span class="sxs-lookup"><span data-stu-id="1e50a-196">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

<span data-ttu-id="1e50a-197">在 RocketLauncher > 按鈕 > 仍然選取 [ **LaunchButton**物件]，在 [ **Pressable] 按鈕（腳本）** 元件上，建立已**按下的新按鈕（）** 事件、設定**LunarModule**物件以接收事件、將**spatialize**定義為要觸發的動作，以及將適當的音訊剪輯指派給**音訊剪輯**欄位，例如 MRTK_Gem 的音訊剪輯：</span><span class="sxs-lookup"><span data-stu-id="1e50a-197">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial6-section3-step1-2.png)

<span data-ttu-id="1e50a-199">在 RocketLauncher > 按鈕 > 仍然選取 [ **LaunchButton**物件]，在 [ **Pressable] 按鈕（腳本）** 元件上，建立新的**觸控結束（）** 事件、設定**LunarModule**物件以接收事件，並將**LaunchLunarModule**定義為要觸發的動作：</span><span class="sxs-lookup"><span data-stu-id="1e50a-199">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Touch Ended ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StopThruster** as the action to be triggered:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial6-section3-step1-3.png)

<span data-ttu-id="1e50a-201">如果您現在進入遊戲模式，並按下 [啟動] 按鈕，您會聽到播放音訊剪輯，如果您將 [啟動] 按鈕按下大約一秒或更長的時間，就會看到 [陰曆] 模組啟動進入空間：</span><span class="sxs-lookup"><span data-stu-id="1e50a-201">If you now enter Game mode and press the Launch button, you will hear the audio clip play, and if you hold the Launch button down for about a second or longer, you will see the Lunar Module launch into space:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a><span data-ttu-id="1e50a-203">設定重設按鈕</span><span class="sxs-lookup"><span data-stu-id="1e50a-203">Configuring the Reset button</span></span>

<span data-ttu-id="1e50a-204">在 階層 視窗中，選取 RocketLauncher > 按鈕 > **ResetButton**物件，然後在  **Pressable 按鈕（腳本）** 元件上，建立已按下的新**按鈕（）** 事件、設定**LunarModule**物件以接收事件，並將**LaunchLunarModule**定義為要觸發的動作：</span><span class="sxs-lookup"><span data-stu-id="1e50a-204">In the Hierarchy window, select the RocketLauncher > Buttons > **ResetButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.ResetModule** as the action to be triggered:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial6-section4-step1-1.png)

<span data-ttu-id="1e50a-206">在 RocketLauncher > 按鈕 > 仍然選取 [ **ResetButton**物件]，在 [ **Pressable] 按鈕（腳本）** 元件上，建立已**按下的新按鈕（）** 事件、設定**RocketLauncher**物件以接收事件、將**GameObject**定義為要觸發的動作，並在 [訊息] 欄位中輸入**BroadcastMessage** ：</span><span class="sxs-lookup"><span data-stu-id="1e50a-206">With the RocketLauncher > Buttons > **ResetButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **RocketLauncher** object to receive the event, define **GameObject.BroadcastMessage** as the action to be triggered, and enter **ResetPlacement** in message field:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="1e50a-208">GameObject. BroadcastMessage 動作會將 ResetPlacement 訊息從 RocketLauncher 物件傳送到其所有的子物件。</span><span class="sxs-lookup"><span data-stu-id="1e50a-208">The GameObject.BroadcastMessage action sends the ResetPlacement message from the RocketLauncher object to all its child object.</span></span> <span data-ttu-id="1e50a-209">具有 ResetPlacement 函式的任何子物件（定義于您加入至所有 LunarModuleParts 子物件的元件示範（Script）元件中）都會叫用 ResetPlacement 函式，該函式會重設該子物件的位置。</span><span class="sxs-lookup"><span data-stu-id="1e50a-209">Any child object that has the ResetPlacement function, which is defined in the Part Assembly Demo (Script) component you added to all the LunarModuleParts child object, will invoke the ResetPlacement function which resets that child object's placement.</span></span>

<span data-ttu-id="1e50a-210">如果您現在進入遊戲模式，然後按下 [重設] 按鈕，就會聽到播放的音訊剪輯，並看到要啟動的陰曆模組：</span><span class="sxs-lookup"><span data-stu-id="1e50a-210">If you now enter Game mode and press the Reset button you will hear the audio clip being played and see the Lunar Module being launched into space:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="1e50a-212">設定放置提示按鈕</span><span class="sxs-lookup"><span data-stu-id="1e50a-212">Configuring the Placement Hints button</span></span>
<!-- TODO: Rename to 'Configuring the Hints button'-->

<span data-ttu-id="1e50a-213">在 階層 視窗中，選取 RocketLauncher > 按鈕 > **HintsButton**物件，然後在  **Pressable 按鈕（腳本）** 元件上，建立已按下的新**按鈕（）** 事件、設定**LunarModule**物件以接收事件，以及定義**TogglePlacementHints。 ToggleGameObjects**要觸發的動作：</span><span class="sxs-lookup"><span data-stu-id="1e50a-213">In the Hierarchy window, select the RocketLauncher > Buttons > **HintsButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **TogglePlacementHints.ToggleGameObjects** the action to be triggered:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial6-section5-step1-1.png)

<span data-ttu-id="1e50a-215">如果您現在進入遊戲模式，您會注意到，預設會停用半透明的放置提示，但是您可以按下 [提示] 按鈕，將它們切換為開啟或關閉：</span><span class="sxs-lookup"><span data-stu-id="1e50a-215">If you now enter Game mode you will notice that the translucent placement hints are disabled by default, but that you can toggle them on and off by pressing the Hints button:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="1e50a-217">恭喜</span><span class="sxs-lookup"><span data-stu-id="1e50a-217">Congratulations</span></span>

<span data-ttu-id="1e50a-218">您已完全設定此應用程式。</span><span class="sxs-lookup"><span data-stu-id="1e50a-218">You have fully configured this application.</span></span> <span data-ttu-id="1e50a-219">現在，您的應用程式可讓使用者完整組合陰曆模組、啟動陰曆模組、切換提示，然後將應用程式重設為重新啟動。</span><span class="sxs-lookup"><span data-stu-id="1e50a-219">Now, your application allows users to fully assemble the Lunar Module, launch the Lunar Module, toggle hints, and reset the application to start again.</span></span>
