---
title: MR 學習基本模組 - 使用者介面、手部追蹤及混合實境工具組設定
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 1800d36b7292b9cb53b09fdd4b9c4fb763d49e79
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730945"
---
# <a name="mr-learning-base-module---user-interface-hand-tracking-and-mixed-reality-toolkit-configuration"></a><span data-ttu-id="e6f00-104">MR 學習基本模組 - 使用者介面、手部追蹤及混合實境工具組設定</span><span class="sxs-lookup"><span data-stu-id="e6f00-104">MR Learning Base Module - User Interface, Hand Tracking, and Mixed Reality Toolkit Configuration</span></span>

<span data-ttu-id="e6f00-105">在上一堂課，您已藉由啟動 HoloLens 2 的第一個應用程式來了解 MRTK 所必須提供的一些功能。</span><span class="sxs-lookup"><span data-stu-id="e6f00-105">In the previous lesson, you learned some of the capabilities the MRTK has to offer, by starting your first application for the HoloLens 2.</span></span> <span data-ttu-id="e6f00-106">接下來這一堂課，您將了解如何建立和組織按鈕以及 UI 文字面板，並且會使用預設互動方式 (觸控) 來與每個按鈕互動。</span><span class="sxs-lookup"><span data-stu-id="e6f00-106">In this next lesson you will learn how to create and organize buttons along with UI text panels and use default interaction (touch) to interact with each button.</span></span> <span data-ttu-id="e6f00-107">此外，您還會探索如何新增簡單的動作和效果，例如變更物件的大小、音效和色彩。</span><span class="sxs-lookup"><span data-stu-id="e6f00-107">You will also explore the addition of simple actions and effects, such as changing the size, sound and color of objects.</span></span> <span data-ttu-id="e6f00-108">此模組將會從關閉空間網格的視覺效果來開始，介紹一些如何修改 MRTK 設定檔的基本概念。</span><span class="sxs-lookup"><span data-stu-id="e6f00-108">This module will introduce basic concepts on how to modify MRTK profiles, starting with turning off the visualization of the spatial mesh.</span></span> 

## <a name="objectives"></a><span data-ttu-id="e6f00-109">目標</span><span class="sxs-lookup"><span data-stu-id="e6f00-109">Objectives</span></span>

* <span data-ttu-id="e6f00-110">自訂和設定混合實境工具組設定檔</span><span class="sxs-lookup"><span data-stu-id="e6f00-110">Customize and configure Mixed Reality Toolkit profiles</span></span>
* <span data-ttu-id="e6f00-111">使用 UI 元素和按鈕來與全像投影互動</span><span class="sxs-lookup"><span data-stu-id="e6f00-111">Interacting with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="e6f00-112">基本的「手部追蹤」輸入和互動</span><span class="sxs-lookup"><span data-stu-id="e6f00-112">Basic hand-tracking input and interactions</span></span>

## <a name="instructions"></a><span data-ttu-id="e6f00-113">指示</span><span class="sxs-lookup"><span data-stu-id="e6f00-113">Instructions</span></span>

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a><span data-ttu-id="e6f00-114">如何設定混合實境工具組設定檔 (變更空間感知顯示選項)</span><span class="sxs-lookup"><span data-stu-id="e6f00-114">How to Configure the Mixed-Reality Toolkit Profiles (Change Spatial Awareness Display Option)</span></span>
<span data-ttu-id="e6f00-115">在本節中，您將會藉由調整空間感知網格的顯示選項，來了解如何自訂和設定預設的混合實境工具組設定檔。</span><span class="sxs-lookup"><span data-stu-id="e6f00-115">In this section you will learn how to customize and configure the default Mixed Reality Toolkit profiles by adjusting the display option of the spatial awareness mesh.</span></span> <span data-ttu-id="e6f00-116">您可以遵循下列和在調整 MRTK 設定檔中的任何設定或值時相同的原則。</span><span class="sxs-lookup"><span data-stu-id="e6f00-116">You may follow these same principles for adjusting any settings or values in the MRTK profiles.</span></span>

1. <span data-ttu-id="e6f00-117">從 [BaseScene] 階層中選取 [混合實境工具組 (MRTK)]。</span><span class="sxs-lookup"><span data-stu-id="e6f00-117">Select Mixed-Reality Toolkit (MRTK) from the “BaseScene” hierarchy.</span></span> <span data-ttu-id="e6f00-118">在偵測程式面板中尋找 [混合實境工具組指令碼]，然後選取 [作用中設定檔]，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="e6f00-118">In the inspector panel, look for the “Mixed Reality Toolkit Script” and select the “active profile” as shown in the figure below.</span></span> <span data-ttu-id="e6f00-119">按兩下來加以開啟。</span><span class="sxs-lookup"><span data-stu-id="e6f00-119">Double click to open it.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-1step1im.PNG)

><span data-ttu-id="e6f00-121">注意：根據預設，您無法編輯 MRTK 設定檔。</span><span class="sxs-lookup"><span data-stu-id="e6f00-121">Note: By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="e6f00-122">這些是可供您複製和自訂的預設設定檔範本。</span><span class="sxs-lookup"><span data-stu-id="e6f00-122">These are default profile templates from which you can copy and customize.</span></span> <span data-ttu-id="e6f00-123">自訂和設定檔有數個層級，因此在設定一或多個設定時，標準做法是複製和自訂數個設定檔。</span><span class="sxs-lookup"><span data-stu-id="e6f00-123">There are several layers of customization and profiles, so it is standard practice to copy and customize several profiles when configuring one or more settings.</span></span>
>
><span data-ttu-id="e6f00-124">若要深入探索 MRTK 設定檔和其架構，請瀏覽 [MRTK 文件](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>)。</span><span class="sxs-lookup"><span data-stu-id="e6f00-124">To discover more about MRTK profiles and their architecture, please visit the [MRTK documentation](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>).</span></span>

2. <span data-ttu-id="e6f00-125">建立一份預設設定檔來進行自訂。</span><span class="sxs-lookup"><span data-stu-id="e6f00-125">Create a copy of the default profile to customize it.</span></span> <span data-ttu-id="e6f00-126">若要複製預設設定檔，請按一下 [複製和自訂] 按鈕 (見下圖)。</span><span class="sxs-lookup"><span data-stu-id="e6f00-126">To copy a default profile, click the “Copy & Customize” button (see image).</span></span> <span data-ttu-id="e6f00-127">這會建立一份 MRTK 設定檔。</span><span class="sxs-lookup"><span data-stu-id="e6f00-127">This creates a copy of the MRTK profile.</span></span> <span data-ttu-id="e6f00-128">有了自己的 MRTK 設定檔後，您現在就能自訂此設定檔中的任何設定。</span><span class="sxs-lookup"><span data-stu-id="e6f00-128">With your own copy of the MRTK profile, you now have the ability customize any settings in this profile.</span></span> <span data-ttu-id="e6f00-129">您還必須針對此設定檔底下的任何其他巢狀設定檔重複執行複製/自訂步驟，如後續步驟所述。</span><span class="sxs-lookup"><span data-stu-id="e6f00-129">You will also need to repeat the copy/customize step for any additional profiles nested under this profile, as described in the subsequent steps.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-1step2im.PNG)

3. <span data-ttu-id="e6f00-131">停用空間感知網格的顯示。</span><span class="sxs-lookup"><span data-stu-id="e6f00-131">Disable the visibility of the spatial awareness mesh.</span></span> <span data-ttu-id="e6f00-132">若要這樣做，請尋找 [空間感知系統設定]，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="e6f00-132">To do this, find “Spatial Awareness System Settings” as shown in the image.</span></span> <span data-ttu-id="e6f00-133">按一下 [空間感知系統設定檔] 右邊的 [複製] 按鈕，以使用可自訂複本來取代預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="e6f00-133">Click the "clone" button to the right of the the “Spatial Awareness System Profile” to replace the default profile with a customizable copy.</span></span> <span data-ttu-id="e6f00-134">如果出現快顯視窗，請按 [複製] 按鈕，如下面第二個圖所示。</span><span class="sxs-lookup"><span data-stu-id="e6f00-134">If a pop-up window appears, press the "Clone" button, as shown in the second image below.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3im.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3bim.jpg)

4. <span data-ttu-id="e6f00-137">建立「預設混合實境空間網格觀察者」的自訂複本。</span><span class="sxs-lookup"><span data-stu-id="e6f00-137">Create a custom copy of the Default Mixed Reality Spatial Mesh Observer.</span></span> <span data-ttu-id="e6f00-138">按一下 [Windows 混合實境空間網格觀察者] 旁邊的向下箭號來查看其他選項。</span><span class="sxs-lookup"><span data-stu-id="e6f00-138">Click the down arrow next to “Windows Mixed Reality Spatial Mesh Observer” to see additional options.</span></span> <span data-ttu-id="e6f00-139">在這些選項中，您會看到 [預設混合實境空間網格觀察者] 呈現灰色 (無法編輯)。</span><span class="sxs-lookup"><span data-stu-id="e6f00-139">In these options, you will see the “Default Mixed Reality Spatial Mesh Observer” which appears greyed (not editable).</span></span> <span data-ttu-id="e6f00-140">您必須使用可自訂複本來取代此預設設定檔，以便能夠進行編輯。</span><span class="sxs-lookup"><span data-stu-id="e6f00-140">You must replace this default profile with a customizable copy so you can edit it.</span></span> <span data-ttu-id="e6f00-141">按一下右邊的按鈕 (標有綠色箭頭) 來複製複本。</span><span class="sxs-lookup"><span data-stu-id="e6f00-141">Click the button to the right (marked by green arrow) to clone a copy.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-1step4im.PNG)

5. <span data-ttu-id="e6f00-143">接下來，您會將 [顯示選項] 的設定調整為 [遮蔽]。</span><span class="sxs-lookup"><span data-stu-id="e6f00-143">Next, you will adjust the settings for the display option to say “occlusion.”</span></span> <span data-ttu-id="e6f00-144">這可讓您無法看見空間網格，但仍將遊戲物件隱藏在空間網格後方 (這稱為遮蔽)。</span><span class="sxs-lookup"><span data-stu-id="e6f00-144">This makes the spatial mesh invisible, but still hide game objects behind the spatial mesh (this is known as occlusion.)</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-1step5im.PNG)

><span data-ttu-id="e6f00-146">注意：雖然您看不見空間對應網格，但其仍然存在，而且可與之互動。</span><span class="sxs-lookup"><span data-stu-id="e6f00-146">Note: While the spatial mapping mesh is not visible, it is still present and you can interact with it.</span></span> <span data-ttu-id="e6f00-147">由於有遮蔽設定，您將看不見空間對應網格背後的全像投影 (例如，可見牆背後的全像投影)。</span><span class="sxs-lookup"><span data-stu-id="e6f00-147">Any holograms behind the spatial mapping mesh (e.g. A hologram behind your visible wall) will not be visible because of the occlusion setting.</span></span>

<span data-ttu-id="e6f00-148">恭喜！</span><span class="sxs-lookup"><span data-stu-id="e6f00-148">Congratulations!</span></span> <span data-ttu-id="e6f00-149">您方才已了解如何修改 MRTK 設定檔中的設定。</span><span class="sxs-lookup"><span data-stu-id="e6f00-149">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="e6f00-150">如您所見，若要修改 MRTK 設定，您必須建立預設設定檔複本，以便能夠加以編輯。</span><span class="sxs-lookup"><span data-stu-id="e6f00-150">As you can see, in order to modify MRTK settings you need to create copies of the default profiles so that you can edit them.</span></span> <span data-ttu-id="e6f00-151">您一定會有在想要建立有新設定的設定檔或回頭參閱預設設定檔時能夠回頭使用的預設設定檔 (無法加以編輯)。</span><span class="sxs-lookup"><span data-stu-id="e6f00-151">You will always have the default profiles (which are not editable) to go back to if you wanted to create a profile with new settings, or refer back to the default profiles.</span></span> <span data-ttu-id="e6f00-152">您可以調整的設定很多。</span><span class="sxs-lookup"><span data-stu-id="e6f00-152">There are numerous settings that you can adjust.</span></span> <span data-ttu-id="e6f00-153">如需 MRTK 設定檔設定的完整參考，請參閱此處的 MRTK 文件： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html</span><span class="sxs-lookup"><span data-stu-id="e6f00-153">For full reference to MRTK profile settings, refer to the MRTK documentation here: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html</span></span>

### <a name="hand-tracking-gestures-and-interactable-buttons"></a><span data-ttu-id="e6f00-154">手部追蹤手勢和可互動的按鈕</span><span class="sxs-lookup"><span data-stu-id="e6f00-154">Hand Tracking Gestures and Interactable buttons</span></span>
<span data-ttu-id="e6f00-155">在本節中，您會了解如何使用手部追蹤來按可互動按鈕。</span><span class="sxs-lookup"><span data-stu-id="e6f00-155">In this section, you will learn how to use hand tracking to press an interactable button.</span></span>

1. <span data-ttu-id="e6f00-156">從 [專案] 資料夾中選取 [資產]。</span><span class="sxs-lookup"><span data-stu-id="e6f00-156">Select “Assets” from the projects folder.</span></span>

2. <span data-ttu-id="e6f00-157">在搜尋列中輸入 "pressablebutton"。</span><span class="sxs-lookup"><span data-stu-id="e6f00-157">Type in the search bar, “pressablebutton.”</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-2step1im.PNG)

3. <span data-ttu-id="e6f00-159">將名為 "PressableButton" 的 Prefab (以藍色方塊表示) 拖曳至您的階層。</span><span class="sxs-lookup"><span data-stu-id="e6f00-159">Drag the prefab (represented by a blue box) named "PressableButton" into your hierarchy.</span></span> 

   > <span data-ttu-id="e6f00-160">注意：如果您收到關於「匯入 TMP Essentials」的訊息，請在此時匯入。</span><span class="sxs-lookup"><span data-stu-id="e6f00-160">Note: If you get a message about “importing TMP Essentials” please import it at this time.</span></span> <span data-ttu-id="e6f00-161">如果 TMP Essentials 還未成為專案一部分，請在匯入 TMP Essentials 之後重複此步驟，否則按鈕文字可能不會出現。</span><span class="sxs-lookup"><span data-stu-id="e6f00-161">If TMP Essentials was not already part of your project, you may need to repeat this step after importing TMP Essentials, otherwise button text may not appear.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-2step3im.PNG)

4. <span data-ttu-id="e6f00-163">按兩下 "PressableButton" 遊戲物件 (現在應該位於 BaseScene 階層中) 以在您的場景中進行檢視，如下圖所示 (您出現的按鈕圖形可能會和下圖不同)。</span><span class="sxs-lookup"><span data-stu-id="e6f00-163">Double click the “PressableButton” game object (which should now be in your BaseScene hierarchy) to view it in your scene, as shown in the image below (your button graphics may appear different than the image below).</span></span> 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step4im.PNG)

5. <span data-ttu-id="e6f00-165">在偵測程式面板中，按一下 [新增事件] 來為按鈕提供要在使用者按下時回應的事件。</span><span class="sxs-lookup"><span data-stu-id="e6f00-165">In the inspector panel, click “Add Event” to give the button an event to respond to when pushed.</span></span> <span data-ttu-id="e6f00-166">在出現的選項中，選取下拉式功能表。</span><span class="sxs-lookup"><span data-stu-id="e6f00-166">In the option that appears, select the drop-down menu.</span></span> <span data-ttu-id="e6f00-167">選取 [InteractableOnPressReciever]。</span><span class="sxs-lookup"><span data-stu-id="e6f00-167">Select “InteractableOnPressReciever.”</span></span> <span data-ttu-id="e6f00-168">在追蹤的手部按下按鈕時，這可讓按鈕回應按下事件。</span><span class="sxs-lookup"><span data-stu-id="e6f00-168">This allows the button to respond to a pressed event when a tracked hand presses the button.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-2step5im.PNG)

6. <span data-ttu-id="e6f00-170">在場景中新增立方體。</span><span class="sxs-lookup"><span data-stu-id="e6f00-170">Add a cube to the scene.</span></span> <span data-ttu-id="e6f00-171">以滑鼠右鍵按一下階層區域、選取 3D 物件，然後按一下 [立方體]。</span><span class="sxs-lookup"><span data-stu-id="e6f00-171">Right click on the hierarchy area, select 3D object, then click on “cube.”</span></span> <span data-ttu-id="e6f00-172">現在，立方體應該會在您的顯示區域內。</span><span class="sxs-lookup"><span data-stu-id="e6f00-172">Now, a cube should be in your display.</span></span> <span data-ttu-id="e6f00-173">其大小會非常大，因此請調整座標 (在「立方體」仍於階層區域中保持選取時) 來減少大小。</span><span class="sxs-lookup"><span data-stu-id="e6f00-173">It will appear very large, so adjust the coordinates (while “cube” is still selected in the hierarchy area) to decrease the size.</span></span> <span data-ttu-id="e6f00-174">將縮放值設定為 x = 0.1、y = 0.1 和 z = 0.1。</span><span class="sxs-lookup"><span data-stu-id="e6f00-174">Set the scale values to x = 0.1, y = 0.1 and z = 0.1.</span></span> <span data-ttu-id="e6f00-175">請務必讓立方體定位在場景中，將其置於可按按鈕附近，但不要與該按鈕重疊。</span><span class="sxs-lookup"><span data-stu-id="e6f00-175">Be sure to position the cube in your scene to place it near the pressable button, but not overlapping with the button.</span></span> <span data-ttu-id="e6f00-176">在下圖中，立方體的位置是 x = 0、y = 0.2 和 z = 1。</span><span class="sxs-lookup"><span data-stu-id="e6f00-176">In the image below, the cube’s position is x = 0, y = 0.2, and z = 1.</span></span> 

   > <span data-ttu-id="e6f00-177">注意：一般情況下，Unity 中的 1 個單位會大致等於真實世界的 1 公尺。</span><span class="sxs-lookup"><span data-stu-id="e6f00-177">Note: In general, 1 unit in Unity is roughly equivalent to 1 meter in the physical world.</span></span> <span data-ttu-id="e6f00-178">但有例外狀況，例如，當物件是所縮放物件的子系時。</span><span class="sxs-lookup"><span data-stu-id="e6f00-178">There are exceptions to this, for example when objects are children of scaled objects.</span></span>
   
   ![MR213_BuildSettings](images/mrlearning-base-ch2-1step6ima.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-2step6imb.PNG)

7. <span data-ttu-id="e6f00-181">在此步驟中，您會設定讓立方體在使用者按下按鈕時變更色彩。</span><span class="sxs-lookup"><span data-stu-id="e6f00-181">In this step you will set up the cube to change color when your button is pressed.</span></span> <span data-ttu-id="e6f00-182">在 [BaseScene] 功能表中選取 [PressableButton]。</span><span class="sxs-lookup"><span data-stu-id="e6f00-182">Select the PressableButton in the “BaseScene” menu.</span></span> <span data-ttu-id="e6f00-183">在偵測程式面板中，按一下 [選取事件類型] 方塊底下的 [+] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e6f00-183">In the inspector panel, under the “Select Event Type” box, click the “+” button.</span></span> <span data-ttu-id="e6f00-184">將立方體從 [BaseScene] 功能表拖曳至 [僅執行階段] 方塊，如下圖所示</span><span class="sxs-lookup"><span data-stu-id="e6f00-184">Drag the “cube” from the “BaseScene” menu into the “Runtime Only” box, as shown in the image below</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7ima.PNG)

<span data-ttu-id="e6f00-186">按一下名為 [無功能] 的下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="e6f00-186">Click the dropdown list that says “No Function.”</span></span> <span data-ttu-id="e6f00-187">選取 [MeshRenderer]，然後選取 [Material material]。</span><span class="sxs-lookup"><span data-stu-id="e6f00-187">Select “MeshRenderer” then select “Material material.”</span></span> <span data-ttu-id="e6f00-188">這可讓您在按下按鈕時變更材質。</span><span class="sxs-lookup"><span data-stu-id="e6f00-188">This will allow you to change the material when the button is pressed.</span></span> 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imb.PNG)

<span data-ttu-id="e6f00-190">移至 [專案] 面板，並搜尋想要在變更後使用的材質。</span><span class="sxs-lookup"><span data-stu-id="e6f00-190">Go to the project panel and search for the material you wish to change it to.</span></span> <span data-ttu-id="e6f00-191">在此範例中，您會使用 "MRTK_Standard_Cyan" 材質，若要尋找，請在 [專案] 索引標籤的搜尋列中輸入「青色」 (MRTK 包含許多材質和色彩可供選擇)。將材質拖曳至 [MeshRenderer.material] 底下的方塊。</span><span class="sxs-lookup"><span data-stu-id="e6f00-191">You are going to use the material “MRTK_Standard_Cyan” for this example, found by typing in “cyan” in the project tab’s search bar (The MRTK includes many materials and colors to choose from.) Drag the material to the box underneath “MeshRenderer.material.”</span></span> <span data-ttu-id="e6f00-192">MRTK 材質可於 Assets>MixedRealityToolkit.SDK>StandardAssets>Materials 中找到。</span><span class="sxs-lookup"><span data-stu-id="e6f00-192">The MRTK materials can be found in Assets>MixedRealityToolkit.SDK>StandardAssets>Materials.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imbb.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step7imc.PNG)

<span data-ttu-id="e6f00-195">此事件現在已設定好，因此在按下按鈕時，立方體便會根據您指定的材質變更色彩。</span><span class="sxs-lookup"><span data-stu-id="e6f00-195">The event is now set so that when the button is pressed, the cube will change color based on the material you specified.</span></span> <span data-ttu-id="e6f00-196">在此範例中，立方體會變更為青色。</span><span class="sxs-lookup"><span data-stu-id="e6f00-196">In this example, the cube will change to the cyan color.</span></span>

8. <span data-ttu-id="e6f00-197">接下來，您會設定放開動作，以便在放開時，按鈕會回復為其預設色彩。</span><span class="sxs-lookup"><span data-stu-id="e6f00-197">Next you are going to set up the release action so that upon release, the button will go back to its default color.</span></span> <span data-ttu-id="e6f00-198">重複執行步驟 7 (上一個步驟)，但這次使用 [OnRelease] 事件而非 [OnPress] 事件，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="e6f00-198">Repeat Step 7 (the previous step) but this time with the “OnRelease” event instead of the “OnPress” event, as shown in the image below.</span></span>

9.  <span data-ttu-id="e6f00-199">在 [專案] 面板中，搜尋要在立方體放開按鈕時作為預設值的材質 (在本例中，我們選擇 MRTK_Standard_LightGray)。將材質拖曳至 [MeshRenderer.material] 欄位下面的方塊中。</span><span class="sxs-lookup"><span data-stu-id="e6f00-199">In the project panel, search for a material for the cube to default to upon button release (in our case, we chose MRTK_Standard_LightGray.) Drag the material into the box below the “MeshRenderer.material” field.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-2step8im.PNG)

<span data-ttu-id="e6f00-201">現在當按下按鈕時，其應該會變更為新的色彩 (例如青色)，而在放開按鈕時，其應該會變更回您所指定的預設色彩 (例如，淺灰色)。請按下畫面頂端的 [播放] 按鈕以在編輯器中試用，或部署至 HoloLens 2 來進行測試！</span><span class="sxs-lookup"><span data-stu-id="e6f00-201">Now when the button is pressed, it should change to a new color (e.g., cyan) and when the button is released it should change back to the default color you specified (e.g., light gray.) Press the “play” button on the top of the screen to try it out in the editor or deploy to your HoloLens 2 to test!</span></span> <span data-ttu-id="e6f00-202">若要深入了解如何在編輯器中進行模擬 (包括手部模擬)，請閱讀 [MRTK 的模擬文件頁面](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>)。</span><span class="sxs-lookup"><span data-stu-id="e6f00-202">To learn more about in-editor simulation, including hand simulation read the [MRTK's simulation documentation page](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>).</span></span> 

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a><span data-ttu-id="e6f00-203">使用 MRTK 的方格物件集合來建立按鈕面板</span><span class="sxs-lookup"><span data-stu-id="e6f00-203">Creating a panel of buttons using MRTK’s Grid Object Collection</span></span>

<span data-ttu-id="e6f00-204">在本節中，您會了解如何使用 MRTK 的 GridObjectCollection 工具，讓多個按鈕自動排列成整齊的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="e6f00-204">In this section, you will learn how to automatically align multiple buttons into a neat user interface using the MRTK’s GridObjectCollection tool.</span></span>

1. <span data-ttu-id="e6f00-205">複製上一節的按鈕直到您有 5 個按鈕。</span><span class="sxs-lookup"><span data-stu-id="e6f00-205">Duplicate the button from the previous section until you have 5 buttons.</span></span> <span data-ttu-id="e6f00-206">有數種方式可以執行這項作業：</span><span class="sxs-lookup"><span data-stu-id="e6f00-206">There are several ways to do this:</span></span>
- <span data-ttu-id="e6f00-207">對按鈕按一下滑鼠右鍵，再按一下 [複製]，然後往下移至按鈕下方，於再次按一下滑鼠右鍵後按一下 [貼上]。</span><span class="sxs-lookup"><span data-stu-id="e6f00-207">Right click on the button and click “copy,” then go down to below the button and right click again and click “paste.”</span></span> 
- <span data-ttu-id="e6f00-208">對按鈕按一下滑鼠右鍵，然後按一下 [複製]。</span><span class="sxs-lookup"><span data-stu-id="e6f00-208">Right click on the button and click “duplicate.”</span></span> 
- <span data-ttu-id="e6f00-209">按一下立方體並按下鍵盤上的 "ctrl D"，來使用鍵盤命令。</span><span class="sxs-lookup"><span data-stu-id="e6f00-209">Use the keyboard command by clicking on the cube and pressing “ctrl D” on your keyboard.</span></span>

<span data-ttu-id="e6f00-210">重複此步驟直到您總共有 5 個按鈕 (請見下圖中的 5 個紅色箭號)。</span><span class="sxs-lookup"><span data-stu-id="e6f00-210">Repeat this until you have 5 total buttons (see 5 red arrows in image below).</span></span>

![Mrlearning Base Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. <span data-ttu-id="e6f00-212">將按鈕群組到空白的父遊戲物件底下。</span><span class="sxs-lookup"><span data-stu-id="e6f00-212">Group the buttons under an empty parent game object.</span></span> <span data-ttu-id="e6f00-213">為了讓按鈕進入方格集合中，您必須將按鈕群組到常用的父物件底下。</span><span class="sxs-lookup"><span data-stu-id="e6f00-213">In order to have the buttons in grid collection, you need to group your buttons under a common parent object.</span></span> <span data-ttu-id="e6f00-214">在階層中按一下滑鼠右鍵，然後按一下 [建立空白]。</span><span class="sxs-lookup"><span data-stu-id="e6f00-214">Right click in the hiearachy and click “create empty.”</span></span> <span data-ttu-id="e6f00-215">這會建立新的空白遊戲物件供您放入所有按鈕。</span><span class="sxs-lookup"><span data-stu-id="e6f00-215">This creates a new empty game object for you to put all the buttons in.</span></span> <span data-ttu-id="e6f00-216">其會顯示為 "gameObject"。</span><span class="sxs-lookup"><span data-stu-id="e6f00-216">It will show up as “gameObject.”</span></span> <span data-ttu-id="e6f00-217">對其按一下滑鼠右鍵並加以重新命名為 "ButtonCollection"。</span><span class="sxs-lookup"><span data-stu-id="e6f00-217">Right click and rename it to “ButtonCollection.”</span></span>

![Mrlearning Base Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. <span data-ttu-id="e6f00-219">將所有按鈕移至新的集合。</span><span class="sxs-lookup"><span data-stu-id="e6f00-219">Move all the buttons into the new collection.</span></span> <span data-ttu-id="e6f00-220">若要這麼做，請將階層中的五個按鈕物件全都選取，並將其全都拖曳至 "ButtonCollection」" 物件底下，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="e6f00-220">Do this by selecting all five of the button objects in your heirarch and drag them all under “ButtonCollection” game object, as shown in the image below.</span></span> <span data-ttu-id="e6f00-221">提示：按住 Ctrl 鍵同時選取項目，即可選取多個項目。</span><span class="sxs-lookup"><span data-stu-id="e6f00-221">Tip: select multiple items by holding the ctrl key while selecting items.</span></span>

![Mrlearning Base Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. <span data-ttu-id="e6f00-223">將 MRTK 的「方格物件集合」元件新增至按鈕集合。</span><span class="sxs-lookup"><span data-stu-id="e6f00-223">Add MRTK’s “Grid Object Collection” component to the button collection.</span></span>  <span data-ttu-id="e6f00-224">若要這樣做，請選取 "ButtonCollection" 父物件，並在偵測程式面板中，按一下 [新增元件] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e6f00-224">To do this, select the “ButtonCollection” parent object and in the inspector panel, click the “Add Component” button.</span></span> <span data-ttu-id="e6f00-225">然後在搜尋列中搜尋「方格物件集合」，並於出現在清單時加以選取。</span><span class="sxs-lookup"><span data-stu-id="e6f00-225">Then search for “Grid Object Collection” in the search bar and select it when it appears in the list.</span></span>

![Mrlearning Base Ch2 3Step4im](images/mrlearning-base-ch2-3step4im.PNG)

<span data-ttu-id="e6f00-227">「方格物件集合」元件可讓您將按鈕或任何一組物件組織在整齊的資料列、資料行或方格中。</span><span class="sxs-lookup"><span data-stu-id="e6f00-227">The Grid Object Collection component allows you to organize buttons or any set of objects in a neat row, column, or grid.</span></span> <span data-ttu-id="e6f00-228">這是 MRTK 所提供的其中一個建置組塊，可讓您以快速且簡單的方式建立美觀的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="e6f00-228">This is one of the building blocks provided by the MRTK that provides you with a quick and simple way to create beautiful user interfaces.</span></span>

5. <span data-ttu-id="e6f00-229">設定方格物件集合。</span><span class="sxs-lookup"><span data-stu-id="e6f00-229">Configure the grid object collection.</span></span> <span data-ttu-id="e6f00-230">為了確保所有按鈕都會面對使用者，請依序選取 [方位類型] 和 [向前面向父系] (如下圖所示)。接下來，變更儲存格大小來設定按鈕間距。</span><span class="sxs-lookup"><span data-stu-id="e6f00-230">To ensure all the buttons face the user, select “orient type” and then select “face parent forward” (as shown in the image.) Next, change the cell size to set the space between your buttons.</span></span> <span data-ttu-id="e6f00-231">從 [儲存格寬度] 和 [儲存格高度] 為 0.12 單位乘 0.12 單位來開始，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="e6f00-231">Start with 0.12 units by 0.12 units for the Cell Width and Cell Height, as shown in the image below.</span></span> <span data-ttu-id="e6f00-232">您可能需要根據所選擇的物件/按鈕資產來調整這些值。</span><span class="sxs-lookup"><span data-stu-id="e6f00-232">You may need to adjust these values, depending on object/button assets chosen.</span></span> <span data-ttu-id="e6f00-233">請確定 [資料列] 設定為 1。</span><span class="sxs-lookup"><span data-stu-id="e6f00-233">Make sure "Rows" is set to 1.</span></span> <span data-ttu-id="e6f00-234">然後按一下 [更新集合]，然後場景應該會看起來如下圖。</span><span class="sxs-lookup"><span data-stu-id="e6f00-234">Then click “Update Collection” and the scene should look like the picture below.</span></span> 


![Mrlearning Base Ch2 3Step5im](images/mrlearning-base-ch2-3step5im.PNG)

><span data-ttu-id="e6f00-236">注意：根據子物件或父物件的方向，您可能需要在未來的專案中以不同的方式調整方向設定。</span><span class="sxs-lookup"><span data-stu-id="e6f00-236">Note: Depending on the orientation of the child objects or parent object, you will likely need to adjust the orientation setting differently in future projects.</span></span> <span data-ttu-id="e6f00-237">根據集合中物件的大小，[儲存格寬度] 和 [儲存格高度] 欄位可能也需要以不同的方式定義。</span><span class="sxs-lookup"><span data-stu-id="e6f00-237">The Cell Width and the Cell Height fields may also need to be defined differently, depending on the size of the objects in your collection.</span></span>

### <a name="adding-text-into-your-scene"></a><span data-ttu-id="e6f00-238">在場景中新增文字</span><span class="sxs-lookup"><span data-stu-id="e6f00-238">Adding Text into Your Scene</span></span>

<span data-ttu-id="e6f00-239">在本節中，您會了解如何在混合實境體驗中新增和編輯文字。</span><span class="sxs-lookup"><span data-stu-id="e6f00-239">In this section, you will learn how to add and edit text to your mixed reality experiences.</span></span> <span data-ttu-id="e6f00-240">請遵循[此處](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation)的指示來確定您已在 Unity 中啟用 TextMeshPro (如果您還沒有這麼做)。</span><span class="sxs-lookup"><span data-stu-id="e6f00-240">If you haven’t already, please ensure you have TextMeshPro enabled in Unity by following the instructions [here](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation).</span></span>

1. <span data-ttu-id="e6f00-241">選取 [ButtonCollection] 父物件，並以滑鼠右鍵按一下集合。</span><span class="sxs-lookup"><span data-stu-id="e6f00-241">Select the “ButtonCollection” parent object and right click the collection.</span></span> <span data-ttu-id="e6f00-242">在下拉式功能表中展開 [3D 物件]，然後選取 [TextMeshPro - 文字]。</span><span class="sxs-lookup"><span data-stu-id="e6f00-242">Expand "3D object" in the dropdown menu, then select "TextMeshPro - Text".</span></span> <span data-ttu-id="e6f00-243">您應該會在按鈕集合底下看到 TextMeshPro 物件，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="e6f00-243">You should see a TextMeshPro object under the button collection, as shown in the image below.</span></span>

<span data-ttu-id="e6f00-244">![Lesson2 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG)
![Lesson2 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)</span><span class="sxs-lookup"><span data-stu-id="e6f00-244">![Lesson2 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG)
![Lesson2 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)</span></span>

2. <span data-ttu-id="e6f00-245">在 TextMeshPro 元件的 [文字] 欄位中 (位於偵測程式面板中，如下圖所示)，輸入「按鈕集合文字」。</span><span class="sxs-lookup"><span data-stu-id="e6f00-245">In the TextMeshPro component’s Text field (located in the inspector panel, as shown below), type in “Button Collection Text.”</span></span> <span data-ttu-id="e6f00-246">文字便會出現在場景中，但會隱藏在按鈕之後且/或大小會不正確。</span><span class="sxs-lookup"><span data-stu-id="e6f00-246">The text will appear in the scene, but it will be hidden behind the buttons and/or the wrong size.</span></span>

![Lesson2 Chapter4 Step2](images/Lesson2_Chapter4_Step2.JPG)

3. <span data-ttu-id="e6f00-248">若要改善文字大小和位置以方便閱讀，請調整 TextMeshPro 元件中的 [字型大小] 欄位，以變更字型的大小。</span><span class="sxs-lookup"><span data-stu-id="e6f00-248">To improve the text size and placement for readability, adjust the “font size” field in the TextMeshPro component to change the size of the font.</span></span> <span data-ttu-id="e6f00-249">您也必須調整 [矩形轉換] 的位置和刻度，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="e6f00-249">You will also need to adjust the “Rect Transform” position and scale as shown in the image below.</span></span> <span data-ttu-id="e6f00-250">請參閱下圖來了解我們的文字設定所使用的值，並歡迎您使用這些值作為起點，來進一步改善您文字欄位的大小和位置。</span><span class="sxs-lookup"><span data-stu-id="e6f00-250">See the images below for values used for our text configuration, and feel free to use these values as a starting point from which to further improve the size and placement of your text field.</span></span>

<span data-ttu-id="e6f00-251">![Lesson2 Chapter4 Step3](images/Lesson2_Chapter4_Step3.JPG)
![Lesson2 Chapter4 Step4](images/Lesson2_Chapter4_Step4.JPG)</span><span class="sxs-lookup"><span data-stu-id="e6f00-251">![Lesson2 Chapter4 Step3](images/Lesson2_Chapter4_Step3.JPG)
![Lesson2 Chapter4 Step4](images/Lesson2_Chapter4_Step4.JPG)</span></span>

5. <span data-ttu-id="e6f00-252">若要修改按鈕物件上的文字值，請按一下任何按鈕旁的箭號來加以展開，並瀏覽至 [SeeItSayItLabel] 物件，然後瀏覽至 [TextMeshPro] 以在其中編輯按鈕的文字，如上述步驟所述。</span><span class="sxs-lookup"><span data-stu-id="e6f00-252">To modify the text values on the button objects, click the arrow next to any button to expand it and navigate to the “SeeItSayItLabel” object, then navigate to “TextMeshPro,” where you can edit the text to your buttons as described in the steps above.</span></span>

![Lesson2 Chapter4 Step5](images/Lesson2_Chapter4_Step5.JPG)

### <a name="congratulations"></a><span data-ttu-id="e6f00-254">恭喜您</span><span class="sxs-lookup"><span data-stu-id="e6f00-254">Congratulations</span></span>
<span data-ttu-id="e6f00-255">在這一堂課中，您已了解如何複製、自訂和設定 MRTK 設定檔設定 (亦即，空間感知網格的顯示)。您也已經了解如何在 HoloLens 2 上使用追蹤的手部來與按鈕互動以觸發事件。</span><span class="sxs-lookup"><span data-stu-id="e6f00-255">In this lesson, you learned how to copy, customize, and configure an MRTK profile setting (i.e., spatial awareness mesh visibility.) You also learned how to interact with a button to trigger events using tracked hands on the HoloLens 2.</span></span> <span data-ttu-id="e6f00-256">最後，您已了解如何使用 Unity 的 Text Mesh Pro 和 MRTK 的方格物件集合元件來建立簡單的 UI 介面。</span><span class="sxs-lookup"><span data-stu-id="e6f00-256">Finally, you learned how to create a simple UI interface using Unity's Text Mesh Pro the MRTK's Grid Object Collection component.</span></span>

[<span data-ttu-id="e6f00-257">下一課：動態內容放置和解算器</span><span class="sxs-lookup"><span data-stu-id="e6f00-257">Next Lesson: Dynamic Content Placement and Solvers</span></span>](mrlearning-base-ch3.md)

