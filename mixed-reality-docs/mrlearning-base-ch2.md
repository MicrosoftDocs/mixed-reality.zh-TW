---
title: MR 學習基底模組-使用者介面手動追蹤及混合實境工具組組態
description: 完成這個課程來了解如何在混合的實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合的實境，unity 教學課程 hololens
ms.openlocfilehash: 1800d36b7292b9cb53b09fdd4b9c4fb763d49e79
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730945"
---
# <a name="mr-learning-base-module---user-interface-hand-tracking-and-mixed-reality-toolkit-configuration"></a><span data-ttu-id="d7d4b-104">MR 學習基底模組-使用者介面手動追蹤及混合實境工具組組態</span><span class="sxs-lookup"><span data-stu-id="d7d4b-104">MR Learning Base Module - User Interface, Hand Tracking, and Mixed Reality Toolkit Configuration</span></span>

<span data-ttu-id="d7d4b-105">上一課，您已了解一些 MRTK 所提供，啟動 HoloLens 2 的第一個應用程式的功能。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-105">In the previous lesson, you learned some of the capabilities the MRTK has to offer, by starting your first application for the HoloLens 2.</span></span> <span data-ttu-id="d7d4b-106">在下一課，您將學習如何建立並組織以及 UI 文字面板的按鈕，並使用預設互動 （觸控） 與每個按鈕互動。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-106">In this next lesson you will learn how to create and organize buttons along with UI text panels and use default interaction (touch) to interact with each button.</span></span> <span data-ttu-id="d7d4b-107">此外，您還將探索加入簡單的動作和效果，例如變更大小、 音效和物件的色彩。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-107">You will also explore the addition of simple actions and effects, such as changing the size, sound and color of objects.</span></span> <span data-ttu-id="d7d4b-108">此模組將介紹如何修改 MRTK 設定檔，啟動與關閉空間網狀結構的視覺效果的基本概念。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-108">This module will introduce basic concepts on how to modify MRTK profiles, starting with turning off the visualization of the spatial mesh.</span></span> 

## <a name="objectives"></a><span data-ttu-id="d7d4b-109">目標</span><span class="sxs-lookup"><span data-stu-id="d7d4b-109">Objectives</span></span>

* <span data-ttu-id="d7d4b-110">自訂和設定混合實境工具組設定檔</span><span class="sxs-lookup"><span data-stu-id="d7d4b-110">Customize and configure Mixed Reality Toolkit profiles</span></span>
* <span data-ttu-id="d7d4b-111">互動使用的 UI 項目和按鈕全像投影</span><span class="sxs-lookup"><span data-stu-id="d7d4b-111">Interacting with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="d7d4b-112">基本的手動追蹤輸入和互動</span><span class="sxs-lookup"><span data-stu-id="d7d4b-112">Basic hand-tracking input and interactions</span></span>

## <a name="instructions"></a><span data-ttu-id="d7d4b-113">指示</span><span class="sxs-lookup"><span data-stu-id="d7d4b-113">Instructions</span></span>

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a><span data-ttu-id="d7d4b-114">如何設定混合實境工具組設定檔 （變更空間感知顯示選項）</span><span class="sxs-lookup"><span data-stu-id="d7d4b-114">How to Configure the Mixed-Reality Toolkit Profiles (Change Spatial Awareness Display Option)</span></span>
<span data-ttu-id="d7d4b-115">在本節中您會了解如何自訂及設定預設的混合實境工具組設定檔，藉由調整 [顯示] 選項的空間感知網狀結構。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-115">In this section you will learn how to customize and configure the default Mixed Reality Toolkit profiles by adjusting the display option of the spatial awareness mesh.</span></span> <span data-ttu-id="d7d4b-116">您可以遵循這些相同的原則適用於調整任何設定或 MRTK 設定檔中的值。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-116">You may follow these same principles for adjusting any settings or values in the MRTK profiles.</span></span>

1. <span data-ttu-id="d7d4b-117">混合實境工具組 (MRTK) 從階層中選取 「 BaseScene"。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-117">Select Mixed-Reality Toolkit (MRTK) from the “BaseScene” hierarchy.</span></span> <span data-ttu-id="d7d4b-118">在 [偵測器] 面板中，尋找 「 混合實境 Toolkit 指令碼 」 並選取 「 作用中設定檔 」 下, 圖所示。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-118">In the inspector panel, look for the “Mixed Reality Toolkit Script” and select the “active profile” as shown in the figure below.</span></span> <span data-ttu-id="d7d4b-119">按兩下以開啟它。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-119">Double click to open it.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-1step1im.PNG)

><span data-ttu-id="d7d4b-121">注意：根據預設，將無法編輯 MRTK 設定檔。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-121">Note: By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="d7d4b-122">這些是您可以從中複製，及自訂的預設設定檔範本。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-122">These are default profile templates from which you can copy and customize.</span></span> <span data-ttu-id="d7d4b-123">有數個層級的自訂與設定檔，因此標準做法是複製和自訂數個設定檔，設定一或多個設定時。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-123">There are several layers of customization and profiles, so it is standard practice to copy and customize several profiles when configuring one or more settings.</span></span>
>
><span data-ttu-id="d7d4b-124">若要深入了解 MRTK 設定檔和其架構，請造訪[MRTK 文件](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>)。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-124">To discover more about MRTK profiles and their architecture, please visit the [MRTK documentation](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>).</span></span>

2. <span data-ttu-id="d7d4b-125">建立一份預設的設定檔來自訂它。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-125">Create a copy of the default profile to customize it.</span></span> <span data-ttu-id="d7d4b-126">若要複製的預設設定檔，按一下 」 複製和自訂 」 按鈕 （請見圖）。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-126">To copy a default profile, click the “Copy & Customize” button (see image).</span></span> <span data-ttu-id="d7d4b-127">這會建立一份 MRTK 設定檔。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-127">This creates a copy of the MRTK profile.</span></span> <span data-ttu-id="d7d4b-128">使用您自己的 MRTK 設定檔的複本，您現在可以自訂此設定檔中的任何設定。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-128">With your own copy of the MRTK profile, you now have the ability customize any settings in this profile.</span></span> <span data-ttu-id="d7d4b-129">您也必須在任何其他的設定檔，這個設定檔，之下巢狀的重複複本/自訂的步驟，後續步驟中所述。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-129">You will also need to repeat the copy/customize step for any additional profiles nested under this profile, as described in the subsequent steps.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-1step2im.PNG)

3. <span data-ttu-id="d7d4b-131">停用空間感知網狀結構的可見性。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-131">Disable the visibility of the spatial awareness mesh.</span></span> <span data-ttu-id="d7d4b-132">若要這樣做，請尋找 [空間感知系統設定]，如圖所示。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-132">To do this, find “Spatial Awareness System Settings” as shown in the image.</span></span> <span data-ttu-id="d7d4b-133">按一下 「 複製 」 按鈕右邊的 「 空間感知系統設定檔 」 來取代預設的設定檔的可自訂的複本。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-133">Click the "clone" button to the right of the the “Spatial Awareness System Profile” to replace the default profile with a customizable copy.</span></span> <span data-ttu-id="d7d4b-134">如果快顯視窗隨即出現，請按 「 複製 」 按鈕，在第二個圖中所示。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-134">If a pop-up window appears, press the "Clone" button, as shown in the second image below.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3im.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3bim.jpg)

4. <span data-ttu-id="d7d4b-137">建立自訂預設混合實境空間 Mesh 觀察者的複本。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-137">Create a custom copy of the Default Mixed Reality Spatial Mesh Observer.</span></span> <span data-ttu-id="d7d4b-138">按一下 「 Windows 混合實境空間 Mesh 觀察者 」 以查看其他選項旁邊的向下箭號。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-138">Click the down arrow next to “Windows Mixed Reality Spatial Mesh Observer” to see additional options.</span></span> <span data-ttu-id="d7d4b-139">在這些選項中，您會看到 「 預設混合實境空間 Mesh 觀察者 」 會出現呈現灰色 （無法編輯）。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-139">In these options, you will see the “Default Mixed Reality Spatial Mesh Observer” which appears greyed (not editable).</span></span> <span data-ttu-id="d7d4b-140">因此您可以編輯它，您必須以可自訂的複本取代此預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-140">You must replace this default profile with a customizable copy so you can edit it.</span></span> <span data-ttu-id="d7d4b-141">按一下右邊 （標示綠色箭頭） 按鈕來複製複本。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-141">Click the button to the right (marked by green arrow) to clone a copy.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-1step4im.PNG)

5. <span data-ttu-id="d7d4b-143">接下來，您將在其中調整說: 「 阻擋。 」 的 [顯示] 選項的設定</span><span class="sxs-lookup"><span data-stu-id="d7d4b-143">Next, you will adjust the settings for the display option to say “occlusion.”</span></span> <span data-ttu-id="d7d4b-144">這可讓空間網格看不見，但仍然遊戲物件後方空間網狀結構 （這稱為的阻擋物。）</span><span class="sxs-lookup"><span data-stu-id="d7d4b-144">This makes the spatial mesh invisible, but still hide game objects behind the spatial mesh (this is known as occlusion.)</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-1step5im.PNG)

><span data-ttu-id="d7d4b-146">注意：看不到空間對應網格，仍存在而您可以與它互動。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-146">Note: While the spatial mapping mesh is not visible, it is still present and you can interact with it.</span></span> <span data-ttu-id="d7d4b-147">由於 occlusion 設定任何全像投影背後空間對應網格 （例如背後可見的牆上雷射） 將不會顯示。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-147">Any holograms behind the spatial mapping mesh (e.g. A hologram behind your visible wall) will not be visible because of the occlusion setting.</span></span>

<span data-ttu-id="d7d4b-148">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="d7d4b-148">Congratulations!</span></span> <span data-ttu-id="d7d4b-149">您剛剛了解如何修改 MRTK 設定檔中的設定。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-149">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="d7d4b-150">如您所見，若要修改 MRTK 設定您要建立的預設設定檔的複本，以便您可以編輯它們。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-150">As you can see, in order to modify MRTK settings you need to create copies of the default profiles so that you can edit them.</span></span> <span data-ttu-id="d7d4b-151">您一定會預設設定檔 （這是不能編輯） 若要返回以如果您想要使用新的設定，建立設定檔，或參閱回預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-151">You will always have the default profiles (which are not editable) to go back to if you wanted to create a profile with new settings, or refer back to the default profiles.</span></span> <span data-ttu-id="d7d4b-152">有許多您可以調整的設定。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-152">There are numerous settings that you can adjust.</span></span> <span data-ttu-id="d7d4b-153">如 MRTK 的設定檔的完整參考，請參閱 MRTK 這裡的文件： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html</span><span class="sxs-lookup"><span data-stu-id="d7d4b-153">For full reference to MRTK profile settings, refer to the MRTK documentation here: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html</span></span>

### <a name="hand-tracking-gestures-and-interactable-buttons"></a><span data-ttu-id="d7d4b-154">追蹤手勢和互動的按鈕</span><span class="sxs-lookup"><span data-stu-id="d7d4b-154">Hand Tracking Gestures and Interactable buttons</span></span>
<span data-ttu-id="d7d4b-155">在本節中，您將學習如何使用追蹤來按下的 [互動] 按鈕的游標。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-155">In this section, you will learn how to use hand tracking to press an interactable button.</span></span>

1. <span data-ttu-id="d7d4b-156">從 [專案] 資料夾中，選取 「 資產 」。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-156">Select “Assets” from the projects folder.</span></span>

2. <span data-ttu-id="d7d4b-157">輸入在搜尋列中，「 pressablebutton。 」</span><span class="sxs-lookup"><span data-stu-id="d7d4b-157">Type in the search bar, “pressablebutton.”</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-2step1im.PNG)

3. <span data-ttu-id="d7d4b-159">將名為"PressableButton"prefab （以藍色方塊表示） 拖曳到您的階層。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-159">Drag the prefab (represented by a blue box) named "PressableButton" into your hierarchy.</span></span> 

   > <span data-ttu-id="d7d4b-160">注意：如果您收到訊息的相關 「 匯入 TMP Essentials 」 請它匯入這一次。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-160">Note: If you get a message about “importing TMP Essentials” please import it at this time.</span></span> <span data-ttu-id="d7d4b-161">如果 TMP Essentials 還沒有專案的一部分，您可能需要重複此步驟之後匯入 TMP Essentials，否則為按鈕文字可能不會出現。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-161">If TMP Essentials was not already part of your project, you may need to repeat this step after importing TMP Essentials, otherwise button text may not appear.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-2step3im.PNG)

4. <span data-ttu-id="d7d4b-163">按兩下 「 PressableButton 」 遊戲物件 （這現在應該位於 BaseScene 階層） 若要檢視您的場景，請在下面的影像 （按鈕圖形可能會出現不同於下圖） 中所示。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-163">Double click the “PressableButton” game object (which should now be in your BaseScene hierarchy) to view it in your scene, as shown in the image below (your button graphics may appear different than the image below).</span></span> 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step4im.PNG)

5. <span data-ttu-id="d7d4b-165">在 [偵測器] 面板中，按一下 「 加入事件 」 事件，以推送時回應給按鈕。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-165">In the inspector panel, click “Add Event” to give the button an event to respond to when pushed.</span></span> <span data-ttu-id="d7d4b-166">在隨即出現選項中，選取下拉式選單。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-166">In the option that appears, select the drop-down menu.</span></span> <span data-ttu-id="d7d4b-167">選取 「 InteractableOnPressReciever。 」</span><span class="sxs-lookup"><span data-stu-id="d7d4b-167">Select “InteractableOnPressReciever.”</span></span> <span data-ttu-id="d7d4b-168">這可讓按鈕已按下的事件追蹤的手按下按鈕時回應。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-168">This allows the button to respond to a pressed event when a tracked hand presses the button.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-2step5im.PNG)

6. <span data-ttu-id="d7d4b-170">您可以將立方體加入場景。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-170">Add a cube to the scene.</span></span> <span data-ttu-id="d7d4b-171">以滑鼠右鍵按一下 [階層] 區域，選取 3D 物件，然後按一下 「 cube 」。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-171">Right click on the hierarchy area, select 3D object, then click on “cube.”</span></span> <span data-ttu-id="d7d4b-172">現在，cube 應該在您的顯示。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-172">Now, a cube should be in your display.</span></span> <span data-ttu-id="d7d4b-173">它會非常大，因此調整座標 （在"cube"已選取 [階層] 區域中） 來減少大小。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-173">It will appear very large, so adjust the coordinates (while “cube” is still selected in the hierarchy area) to decrease the size.</span></span> <span data-ttu-id="d7d4b-174">標尺值設定為 x = 0.1，y = 0.1 和 z = 0.1。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-174">Set the scale values to x = 0.1, y = 0.1 and z = 0.1.</span></span> <span data-ttu-id="d7d4b-175">是確定位置附近 pressable 的按鈕，將它放入場景中的 cube，但不是重疊與按鈕。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-175">Be sure to position the cube in your scene to place it near the pressable button, but not overlapping with the button.</span></span> <span data-ttu-id="d7d4b-176">在下圖中，cube 的位置是 x = 0，y = 0.2 和 z = 1。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-176">In the image below, the cube’s position is x = 0, y = 0.2, and z = 1.</span></span> 

   > <span data-ttu-id="d7d4b-177">注意：一般情況下，在 Unity 中的 1 個單位是大致上相當於在真實世界的 1 公尺。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-177">Note: In general, 1 unit in Unity is roughly equivalent to 1 meter in the physical world.</span></span> <span data-ttu-id="d7d4b-178">沒有例外狀況，例如，當物件子系的縮放物件時。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-178">There are exceptions to this, for example when objects are children of scaled objects.</span></span>
   
   ![MR213_BuildSettings](images/mrlearning-base-ch2-1step6ima.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-2step6imb.PNG)

7. <span data-ttu-id="d7d4b-181">在此步驟中您會設定來變更色彩，在按下按鈕時的 cube。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-181">In this step you will set up the cube to change color when your button is pressed.</span></span> <span data-ttu-id="d7d4b-182">您可以選取 PressableButton"BaseScene 」 功能表中。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-182">Select the PressableButton in the “BaseScene” menu.</span></span> <span data-ttu-id="d7d4b-183">在 [偵測器] 面板中，在 [選取事件類型] 方塊中，按一下"+"按鈕。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-183">In the inspector panel, under the “Select Event Type” box, click the “+” button.</span></span> <span data-ttu-id="d7d4b-184">拖曳至"cube"從"BaseScene 」 功能表 僅執行階段 方塊中，如下圖所示</span><span class="sxs-lookup"><span data-stu-id="d7d4b-184">Drag the “cube” from the “BaseScene” menu into the “Runtime Only” box, as shown in the image below</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7ima.PNG)

<span data-ttu-id="d7d4b-186">按一下下拉式清單中，指出 「 沒有函式 」。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-186">Click the dropdown list that says “No Function.”</span></span> <span data-ttu-id="d7d4b-187">選取 「 MeshRenderer"，然後選取"材料 material"。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-187">Select “MeshRenderer” then select “Material material.”</span></span> <span data-ttu-id="d7d4b-188">這可讓您按下按鈕時，變更資料。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-188">This will allow you to change the material when the button is pressed.</span></span> 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imb.PNG)

<span data-ttu-id="d7d4b-190">請移至 [專案] 面板，並在搜尋您想要將它變更為資料。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-190">Go to the project panel and search for the material you wish to change it to.</span></span> <span data-ttu-id="d7d4b-191">您要用於此範例中的資料 」 MRTK_Standard_Cyan"，找到以"青色 」 （MRTK 包含許多資料與可從中選擇的色彩）。 [專案] 索引標籤的搜尋列中輸入將資料拖曳至 「 MeshRenderer.material。 」 底下的方塊</span><span class="sxs-lookup"><span data-stu-id="d7d4b-191">You are going to use the material “MRTK_Standard_Cyan” for this example, found by typing in “cyan” in the project tab’s search bar (The MRTK includes many materials and colors to choose from.) Drag the material to the box underneath “MeshRenderer.material.”</span></span> <span data-ttu-id="d7d4b-192">MRTK 資料可在資產 > MixedRealityToolkit.SDK > StandardAssets > 的資料。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-192">The MRTK materials can be found in Assets>MixedRealityToolkit.SDK>StandardAssets>Materials.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imbb.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step7imc.PNG)

<span data-ttu-id="d7d4b-195">此事件現在已設定，讓 cube 按下按鈕時，會變更根據您指定的材質的色彩。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-195">The event is now set so that when the button is pressed, the cube will change color based on the material you specified.</span></span> <span data-ttu-id="d7d4b-196">在此範例中，cube 會變更為青色色。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-196">In this example, the cube will change to the cyan color.</span></span>

8. <span data-ttu-id="d7d4b-197">接下來您要設定發行動作，以便在版本中，按鈕會恢復為其預設色彩。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-197">Next you are going to set up the release action so that upon release, the button will go back to its default color.</span></span> <span data-ttu-id="d7d4b-198">重複執行步驟 7 （上一個步驟），但這次使用 「 OnRelease 」 事件，而非"OnPress 」 事件，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-198">Repeat Step 7 (the previous step) but this time with the “OnRelease” event instead of the “OnPress” event, as shown in the image below.</span></span>

9.  <span data-ttu-id="d7d4b-199">在 專案 面板中，搜尋 按鈕時釋放的預設值之 cube 的資料 （在本例中，我們選擇 MRTK_Standard_LightGray。）將資料拖曳至 「 MeshRenderer.material"欄位下方的方塊。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-199">In the project panel, search for a material for the cube to default to upon button release (in our case, we chose MRTK_Standard_LightGray.) Drag the material into the box below the “MeshRenderer.material” field.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-2step8im.PNG)

<span data-ttu-id="d7d4b-201">現在按下按鈕時，它應該將它變更為新的色彩 (例如青色) 在放開按鍵時它應該將它變更回您所指定的預設色彩 （例如，淺灰色。）按下 「 播放 」 按鈕，現在就試試看在編輯器中，或部署到您要測試的 HoloLens 2 在螢幕上方 ！</span><span class="sxs-lookup"><span data-stu-id="d7d4b-201">Now when the button is pressed, it should change to a new color (e.g., cyan) and when the button is released it should change back to the default color you specified (e.g., light gray.) Press the “play” button on the top of the screen to try it out in the editor or deploy to your HoloLens 2 to test!</span></span> <span data-ttu-id="d7d4b-202">若要深入了解在編輯器中模擬，包括讀取手動模擬[MRTK 的模擬文件頁面](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>)。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-202">To learn more about in-editor simulation, including hand simulation read the [MRTK's simulation documentation page](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>).</span></span> 

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a><span data-ttu-id="d7d4b-203">建立使用 MRTK 的格線物件集合的按鈕面板</span><span class="sxs-lookup"><span data-stu-id="d7d4b-203">Creating a panel of buttons using MRTK’s Grid Object Collection</span></span>

<span data-ttu-id="d7d4b-204">在本節中，您將學習如何自動對齊多個按鈕，到使用 MRTK GridObjectCollection 工具的簡潔使用者介面。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-204">In this section, you will learn how to automatically align multiple buttons into a neat user interface using the MRTK’s GridObjectCollection tool.</span></span>

1. <span data-ttu-id="d7d4b-205">除非您有 5 個按鈕，請重複上一節中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-205">Duplicate the button from the previous section until you have 5 buttons.</span></span> <span data-ttu-id="d7d4b-206">有數種方式可以執行這項操作：</span><span class="sxs-lookup"><span data-stu-id="d7d4b-206">There are several ways to do this:</span></span>
- <span data-ttu-id="d7d4b-207">按鈕上按一下滑鼠右鍵並按一下 「 複製 」，然後移至按鈕下方並再次以滑鼠右鍵按一下，按一下 「 貼上 」。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-207">Right click on the button and click “copy,” then go down to below the button and right click again and click “paste.”</span></span> 
- <span data-ttu-id="d7d4b-208">以滑鼠右鍵按一下按鈕，按一下 「 重複 」。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-208">Right click on the button and click “duplicate.”</span></span> 
- <span data-ttu-id="d7d4b-209">按一下 cube 並按下的 「 ctrl D"鍵盤上使用鍵盤命令。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-209">Use the keyboard command by clicking on the cube and pressing “ctrl D” on your keyboard.</span></span>

<span data-ttu-id="d7d4b-210">除非您有 5 個 （請參閱下面的影像中的 5 個紅色箭號） 的總按鈕重複此步驟。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-210">Repeat this until you have 5 total buttons (see 5 red arrows in image below).</span></span>

![Mrlearning 基底 Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. <span data-ttu-id="d7d4b-212">空白的父遊戲物件底下按鈕群組。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-212">Group the buttons under an empty parent game object.</span></span> <span data-ttu-id="d7d4b-213">為了方格集合中有 [] 按鈕，您必須將您常用的父物件底下的按鈕。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-213">In order to have the buttons in grid collection, you need to group your buttons under a common parent object.</span></span> <span data-ttu-id="d7d4b-214">Hiearachy 中以滑鼠右鍵按一下並按一下 [建立空白]。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-214">Right click in the hiearachy and click “create empty.”</span></span> <span data-ttu-id="d7d4b-215">這會建立要將所有按鈕都放在新的空白遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-215">This creates a new empty game object for you to put all the buttons in.</span></span> <span data-ttu-id="d7d4b-216">它會顯示為 「 gameObject。 」</span><span class="sxs-lookup"><span data-stu-id="d7d4b-216">It will show up as “gameObject.”</span></span> <span data-ttu-id="d7d4b-217">以滑鼠右鍵按一下，並將它重新命名為"ButtonCollection。 」</span><span class="sxs-lookup"><span data-stu-id="d7d4b-217">Right click and rename it to “ButtonCollection.”</span></span>

![Mrlearning 基底 Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. <span data-ttu-id="d7d4b-219">將所有按鈕都移至新的集合。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-219">Move all the buttons into the new collection.</span></span> <span data-ttu-id="d7d4b-220">是，在您 heirarch 選取全部五個按鈕物件並拖曳它們全部都是在 「 ButtonCollection 」 遊戲物件，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-220">Do this by selecting all five of the button objects in your heirarch and drag them all under “ButtonCollection” game object, as shown in the image below.</span></span> <span data-ttu-id="d7d4b-221">提示： 所選取項目時按住 ctrl 鍵選取多個項目。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-221">Tip: select multiple items by holding the ctrl key while selecting items.</span></span>

![Mrlearning 基底 Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. <span data-ttu-id="d7d4b-223">MRTK 的 「 方格物件的集合 」 將元件新增至按鈕集合。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-223">Add MRTK’s “Grid Object Collection” component to the button collection.</span></span>  <span data-ttu-id="d7d4b-224">若要這樣做，請選取 「 ButtonCollection"父物件並在偵測器 面板中，按一下 新增元件 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-224">To do this, select the “ButtonCollection” parent object and in the inspector panel, click the “Add Component” button.</span></span> <span data-ttu-id="d7d4b-225">然後在 [搜尋] 列中搜尋 「 方格物件的集合 」，它必須出現在清單中選取它。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-225">Then search for “Grid Object Collection” in the search bar and select it when it appears in the list.</span></span>

![Mrlearning 基底 Ch2 3Step4im](images/mrlearning-base-ch2-3step4im.PNG)

<span data-ttu-id="d7d4b-227">格線物件集合的元件可讓您將按鈕或任何組織的一組很棒的資料列、 資料行或方格中的物件。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-227">The Grid Object Collection component allows you to organize buttons or any set of objects in a neat row, column, or grid.</span></span> <span data-ttu-id="d7d4b-228">這是您提供快速且簡單的方式，來建立美觀的使用者介面 MRTK 所提供的建置組塊。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-228">This is one of the building blocks provided by the MRTK that provides you with a quick and simple way to create beautiful user interfaces.</span></span>

5. <span data-ttu-id="d7d4b-229">設定格線物件集合。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-229">Configure the grid object collection.</span></span> <span data-ttu-id="d7d4b-230">若要確保所有按鈕所面臨的使用者，選取 「 引導類型 」，然後按 「 面臨父轉寄 」 （如圖所示。）接下來，將變更儲存格大小來設定您的按鈕之間的間距。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-230">To ensure all the buttons face the user, select “orient type” and then select “face parent forward” (as shown in the image.) Next, change the cell size to set the space between your buttons.</span></span> <span data-ttu-id="d7d4b-231">開始 gt;=0.12 單位 gt;=0.12 的單位儲存格的寬度和儲存格的高度，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-231">Start with 0.12 units by 0.12 units for the Cell Width and Cell Height, as shown in the image below.</span></span> <span data-ttu-id="d7d4b-232">您可能需要調整這些值，根據選擇的物件/按鈕資產。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-232">You may need to adjust these values, depending on object/button assets chosen.</span></span> <span data-ttu-id="d7d4b-233">請確定 「 資料列 」 設定為 1。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-233">Make sure "Rows" is set to 1.</span></span> <span data-ttu-id="d7d4b-234">然後按一下 [更新集合]，並在場景應該看起來如下圖。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-234">Then click “Update Collection” and the scene should look like the picture below.</span></span> 


![Mrlearning 基底 Ch2 3Step5im](images/mrlearning-base-ch2-3step5im.PNG)

><span data-ttu-id="d7d4b-236">注意：根據父物件之子物件的方向，您可能需要調整設定以不同的方式，在未來的專案中的方向。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-236">Note: Depending on the orientation of the child objects or parent object, you will likely need to adjust the orientation setting differently in future projects.</span></span> <span data-ttu-id="d7d4b-237">儲存格的寬度和儲存格的高度欄位可能也需要以不同的方式，定義您的集合中物件的大小而定。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-237">The Cell Width and the Cell Height fields may also need to be defined differently, depending on the size of the objects in your collection.</span></span>

### <a name="adding-text-into-your-scene"></a><span data-ttu-id="d7d4b-238">將文字新增至場景</span><span class="sxs-lookup"><span data-stu-id="d7d4b-238">Adding Text into Your Scene</span></span>

<span data-ttu-id="d7d4b-239">在本節中，您將學習如何新增和編輯您的混合的實境體驗的文字。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-239">In this section, you will learn how to add and edit text to your mixed reality experiences.</span></span> <span data-ttu-id="d7d4b-240">如果您還沒有這麼做，請確定您有啟用在 Unity 中的指示 TextMeshPro[此處](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation)。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-240">If you haven’t already, please ensure you have TextMeshPro enabled in Unity by following the instructions [here](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation).</span></span>

1. <span data-ttu-id="d7d4b-241">選取 「 ButtonCollection"父物件，並以滑鼠右鍵按一下集合。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-241">Select the “ButtonCollection” parent object and right click the collection.</span></span> <span data-ttu-id="d7d4b-242">在下拉式功能表中，展開 「 3D 物件 」，然後選取"TextMeshPro-Text"。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-242">Expand "3D object" in the dropdown menu, then select "TextMeshPro - Text".</span></span> <span data-ttu-id="d7d4b-243">下圖所示，您應該看到按鈕集合中下, 一個 TextMeshPro 物件。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-243">You should see a TextMeshPro object under the button collection, as shown in the image below.</span></span>

<span data-ttu-id="d7d4b-244">![第 2 課 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG)
![第 2 課 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)</span><span class="sxs-lookup"><span data-stu-id="d7d4b-244">![Lesson2 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG)
![Lesson2 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)</span></span>

2. <span data-ttu-id="d7d4b-245">在 TextMeshPro 元件的文字欄位中 （位於 [偵測器] 面板中，如下所示），輸入 「 按鈕集合文字 」。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-245">In the TextMeshPro component’s Text field (located in the inspector panel, as shown below), type in “Button Collection Text.”</span></span> <span data-ttu-id="d7d4b-246">文字會出現在場景，但它會隱藏之後的按鈕和/或大小不正確。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-246">The text will appear in the scene, but it will be hidden behind the buttons and/or the wrong size.</span></span>

![第 2 課 Chapter4 步驟 2](images/Lesson2_Chapter4_Step2.JPG)

3. <span data-ttu-id="d7d4b-248">若要改善的文字大小和位置，以增加可讀性，調整 「 字型大小 」 元件中欄位 TextMeshPro 若要變更字型的大小。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-248">To improve the text size and placement for readability, adjust the “font size” field in the TextMeshPro component to change the size of the font.</span></span> <span data-ttu-id="d7d4b-249">您也必須調整"Rect Transform"位置和小數位數，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-249">You will also need to adjust the “Rect Transform” position and scale as shown in the image below.</span></span> <span data-ttu-id="d7d4b-250">請參閱下方的映像，我們的文字設定的值，並歡迎您使用這些值做為起點要進一步改善的大小和位置的文字欄位。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-250">See the images below for values used for our text configuration, and feel free to use these values as a starting point from which to further improve the size and placement of your text field.</span></span>

<span data-ttu-id="d7d4b-251">![第 2 課 Chapter4 Step3](images/Lesson2_Chapter4_Step3.JPG)
![第 2 課 Chapter4 步驟 4](images/Lesson2_Chapter4_Step4.JPG)</span><span class="sxs-lookup"><span data-stu-id="d7d4b-251">![Lesson2 Chapter4 Step3](images/Lesson2_Chapter4_Step3.JPG)
![Lesson2 Chapter4 Step4](images/Lesson2_Chapter4_Step4.JPG)</span></span>

5. <span data-ttu-id="d7d4b-252">若要修改的按鈕物件上的文字值，請按一下即可展開它，並瀏覽至"SeeItSayItLabel 」 物件的任何按鈕旁的箭號，然後瀏覽至"TextMeshPro 」，您可以在其中您如上述步驟中所述的按鈕來編輯文字。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-252">To modify the text values on the button objects, click the arrow next to any button to expand it and navigate to the “SeeItSayItLabel” object, then navigate to “TextMeshPro,” where you can edit the text to your buttons as described in the steps above.</span></span>

![第 2 課 Chapter4 步驟 5](images/Lesson2_Chapter4_Step5.JPG)

### <a name="congratulations"></a><span data-ttu-id="d7d4b-254">恭喜您</span><span class="sxs-lookup"><span data-stu-id="d7d4b-254">Congratulations</span></span>
<span data-ttu-id="d7d4b-255">在這一課，您已了解如何複製、 自訂和設定 MRTK 設定檔設定 （亦即，空間感知網狀結構的可見度。）您也學到如何使用追蹤的指針 HoloLens 2 上的觸發程序事件的按鈕與互動。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-255">In this lesson, you learned how to copy, customize, and configure an MRTK profile setting (i.e., spatial awareness mesh visibility.) You also learned how to interact with a button to trigger events using tracked hands on the HoloLens 2.</span></span> <span data-ttu-id="d7d4b-256">最後，您已了解如何建立簡單的 UI 介面，使用 Unity 的文字 Mesh Pro MRTK 的格線物件集合的元件。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-256">Finally, you learned how to create a simple UI interface using Unity's Text Mesh Pro the MRTK's Grid Object Collection component.</span></span>

[<span data-ttu-id="d7d4b-257">下一課：動態內容的位置和解</span><span class="sxs-lookup"><span data-stu-id="d7d4b-257">Next Lesson: Dynamic Content Placement and Solvers</span></span>](mrlearning-base-ch3.md)

