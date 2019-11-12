---
title: 快速入門教學課程-3。 建立使用者介面和設定混合現實工具組
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 0595010a0b443d88e3f208b785903e3f6cc99295
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926523"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a><span data-ttu-id="150f4-105">3. 建立使用者介面和設定混合現實工具組</span><span class="sxs-lookup"><span data-stu-id="150f4-105">3. Creating user interface and configure Mixed Reality Toolkit</span></span>

<span data-ttu-id="150f4-106">在上一課中，您已瞭解混合現實工具組（MRTK）針對 HoloLens 2 啟動第一個應用程式所提供的一些功能。</span><span class="sxs-lookup"><span data-stu-id="150f4-106">In the previous lesson, you learned about some of the capabilities the Mixed Reality Toolkit (MRTK) has to offer by starting your first application for the HoloLens 2.</span></span> <span data-ttu-id="150f4-107">在下一課中，您將學習如何建立和組織按鈕以及 UI 文字面板，並使用預設互動（觸控）與每個按鈕互動。</span><span class="sxs-lookup"><span data-stu-id="150f4-107">In this next lesson you'll learn how to create and organize buttons along with UI text panels, and use default interaction (touch) to interact with each button.</span></span> <span data-ttu-id="150f4-108">此外，您還會探索如何新增簡單的動作和效果，例如變更物件的大小、音效和色彩。</span><span class="sxs-lookup"><span data-stu-id="150f4-108">You will also explore the addition of simple actions and effects, such as changing the size, sound and color of objects.</span></span> <span data-ttu-id="150f4-109">本課程模組將介紹有關修改 MRTK 設定檔的基本概念，從關閉[空間對應](spatial-mapping.md)網格視覺效果開始。</span><span class="sxs-lookup"><span data-stu-id="150f4-109">This module will introduce basic concepts about modifying MRTK profiles, starting with turning off the [spatial mapping](spatial-mapping.md) mesh visualization.</span></span>

## <a name="objectives"></a><span data-ttu-id="150f4-110">目標</span><span class="sxs-lookup"><span data-stu-id="150f4-110">Objectives</span></span>

* <span data-ttu-id="150f4-111">自訂和設定混合實境工具組設定檔</span><span class="sxs-lookup"><span data-stu-id="150f4-111">Customize and configure Mixed Reality Toolkit profiles</span></span>
* <span data-ttu-id="150f4-112">使用 UI 元素和按鈕與全息影像互動</span><span class="sxs-lookup"><span data-stu-id="150f4-112">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="150f4-113">基本的「手部追蹤」輸入和互動</span><span class="sxs-lookup"><span data-stu-id="150f4-113">Basic hand-tracking input and interactions</span></span>

## <a name="instructions"></a><span data-ttu-id="150f4-114">指示</span><span class="sxs-lookup"><span data-stu-id="150f4-114">Instructions</span></span>

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a><span data-ttu-id="150f4-115">如何設定混合現實工具組設定檔（變更空間感知顯示選項）</span><span class="sxs-lookup"><span data-stu-id="150f4-115">How to Configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)</span></span>

<span data-ttu-id="150f4-116">在本節中，您將瞭解如何藉由調整空間感知網格的顯示選項來自訂和設定預設的 MRTK 設定檔。</span><span class="sxs-lookup"><span data-stu-id="150f4-116">In this section, you'll learn how to customize and configure the default MRTK profiles by adjusting the display option of the spatial awareness mesh.</span></span> <span data-ttu-id="150f4-117">您可以遵循下列和在調整 MRTK 設定檔中的任何設定或值時相同的原則。</span><span class="sxs-lookup"><span data-stu-id="150f4-117">You may follow these same principles for adjusting any settings or values in the MRTK profiles.</span></span>

1. <span data-ttu-id="150f4-118">從 BaseScene 階層中選取 [混合現實工具組（MRTK）]。</span><span class="sxs-lookup"><span data-stu-id="150f4-118">Select Mixed-Reality Toolkit (MRTK) from the BaseScene hierarchy.</span></span> <span data-ttu-id="150f4-119">在 [偵測器] 面板中，尋找 Mixed Reality 工具組腳本，並選取使用中的設定檔，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="150f4-119">In the inspector panel, look for the Mixed Reality Toolkit Script and select the active profile as shown in the figure below.</span></span> <span data-ttu-id="150f4-120">按兩下來加以開啟。</span><span class="sxs-lookup"><span data-stu-id="150f4-120">Double click to open it.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step1.png)

    >[!NOTE]
    ><span data-ttu-id="150f4-122">根據預設，您無法編輯 MRTK 設定檔。</span><span class="sxs-lookup"><span data-stu-id="150f4-122">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="150f4-123">這些是您可以複製和自訂的預設設定檔範本。</span><span class="sxs-lookup"><span data-stu-id="150f4-123">These are default profile templates that you can copy and customize.</span></span> <span data-ttu-id="150f4-124">有數個層級的自訂和設定檔。</span><span class="sxs-lookup"><span data-stu-id="150f4-124">There are several layers of customization and profiles.</span></span> <span data-ttu-id="150f4-125">因此，在設定一個或多個設定時，複製和自訂數個設定檔是標準作法。</span><span class="sxs-lookup"><span data-stu-id="150f4-125">So, it is standard practice to copy and customize several profiles when configuring one or more settings.</span></span>
    >
    ><span data-ttu-id="150f4-126">若要深入瞭解 MRTK 設定檔及其架構，請造訪[MRTK 檔](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html>)。</span><span class="sxs-lookup"><span data-stu-id="150f4-126">To discover more about MRTK profiles and their architecture, visit the [MRTK documentation](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html>).</span></span>

2. <span data-ttu-id="150f4-127">建立一份預設設定檔來進行自訂。</span><span class="sxs-lookup"><span data-stu-id="150f4-127">Create a copy of the default profile to customize it.</span></span> <span data-ttu-id="150f4-128">首先按一下 [**複製 & 自訂**]。</span><span class="sxs-lookup"><span data-stu-id="150f4-128">Start by clicking **Copy & Customize**.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step2a.png)

    <span data-ttu-id="150f4-130">這會開啟 [*複製設定檔*] 快顯視窗。</span><span class="sxs-lookup"><span data-stu-id="150f4-130">This will open the *Clone Profile* popup window.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step2b.png)

    <span data-ttu-id="150f4-132">按一下 [**複製**]，以建立 MRTK 設定檔的複本。</span><span class="sxs-lookup"><span data-stu-id="150f4-132">Click **Clone** to create a copy of the MRTK profile.</span></span> <span data-ttu-id="150f4-133">有了自己的 MRTK 設定檔後，您現在就能自訂此設定檔中的任何設定。</span><span class="sxs-lookup"><span data-stu-id="150f4-133">With your own copy of the MRTK profile, you now have the ability customize any settings in this profile.</span></span> <span data-ttu-id="150f4-134">您也必須針對此設定檔下的任何其他設定檔，重複複製並自訂步驟，如後續步驟所述。</span><span class="sxs-lookup"><span data-stu-id="150f4-134">You will also need to repeat the copy and customize step for any additional profiles nested under this profile as described in the subsequent steps.</span></span>

3. <span data-ttu-id="150f4-135">停用空間感知網格的顯示。</span><span class="sxs-lookup"><span data-stu-id="150f4-135">Disable the visibility of the spatial awareness mesh.</span></span> <span data-ttu-id="150f4-136">若要這樣做，請尋找空間感知系統設定，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="150f4-136">To do this, find Spatial Awareness system settings as shown in the image below.</span></span> <span data-ttu-id="150f4-137">請確定已核取 [**啟用空間感知系統**] 選項。</span><span class="sxs-lookup"><span data-stu-id="150f4-137">Make sure the **Enable Spatial Awareness System** option is checked.</span></span> <span data-ttu-id="150f4-138">按一下 [空間感知] 系統設定檔右邊的 [**複製**] 按鈕，以可自訂的複本取代預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="150f4-138">Click the **Clone** button to the right of the the Spatial Awareness System Profile to replace the default profile with a customizable copy.</span></span> <span data-ttu-id="150f4-139">在出現的快顯視窗中，按下 [**複製**] 按鈕，如下圖中的第二個影像所示。</span><span class="sxs-lookup"><span data-stu-id="150f4-139">In the popup window that appears, press the **Clone** button, as shown in the second image below.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step3a.png)

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step3b.png)

4. <span data-ttu-id="150f4-142">建立「預設混合實境空間網格觀察者」的自訂複本。</span><span class="sxs-lookup"><span data-stu-id="150f4-142">Create a custom copy of the Default Mixed Reality Spatial Mesh Observer.</span></span> <span data-ttu-id="150f4-143">按一下 [Windows Mixed Reality 空間網格觀察者] 旁邊的向下箭號，以查看其他選項。</span><span class="sxs-lookup"><span data-stu-id="150f4-143">Click the down arrow next to Windows Mixed Reality Spatial Mesh Observer to see additional options.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step4a.png)

    <span data-ttu-id="150f4-145">在這些選項中，您會看到呈現灰色的預設混合現實空間網格觀察者（無法編輯）。</span><span class="sxs-lookup"><span data-stu-id="150f4-145">In these options, you will see the Default Mixed Reality Spatial Mesh Observer that is greyed-out (not editable).</span></span> <span data-ttu-id="150f4-146">您必須使用可自訂複本來取代此預設設定檔，以便能夠進行編輯。</span><span class="sxs-lookup"><span data-stu-id="150f4-146">You must replace this default profile with a customizable copy so you can edit it.</span></span> <span data-ttu-id="150f4-147">如同您先前所做的，按一下 [**複製**] 按鈕，然後在出現的快顯視窗中按下 [**複製**] 按鈕，如下圖中的第二個影像所示。</span><span class="sxs-lookup"><span data-stu-id="150f4-147">As you did earlier, click the **Clone** button and then, in the popup window that appears, press the **Clone** button, as shown in the second image below.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step4b.png)

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step4c.png)

5. <span data-ttu-id="150f4-150">接下來，您會將 [顯示選項] 的設定調整為 [遮蔽]。</span><span class="sxs-lookup"><span data-stu-id="150f4-150">Next, you will adjust the settings for the display option to say “occlusion.”</span></span> <span data-ttu-id="150f4-151">這會使空間對應網格可見，但仍會隱藏空間對應網格背後的遊戲物件，也稱為遮蔽。</span><span class="sxs-lookup"><span data-stu-id="150f4-151">This makes the spatial mapping mesh invisible, but still hides game objects behind the spatial mapping mesh, also known as occlusion.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step5.png)

    >[!NOTE]
    ><span data-ttu-id="150f4-153">注意：雖然空間對應網格未顯示，但仍存在，而且您可以與它互動。</span><span class="sxs-lookup"><span data-stu-id="150f4-153">Note: While the spatial mapping mesh is not visible, it is still present and you can interact with it.</span></span> <span data-ttu-id="150f4-154">空間對應網格背後的任何全息影像（例如您可見牆後方的全息影像）將不會顯示，因為遮蔽設定。</span><span class="sxs-lookup"><span data-stu-id="150f4-154">Any holograms behind the spatial mapping mesh, such as a hologram behind your visible wall, will not be visible because of the occlusion setting.</span></span>

<span data-ttu-id="150f4-155">恭喜！</span><span class="sxs-lookup"><span data-stu-id="150f4-155">Congratulations!</span></span> <span data-ttu-id="150f4-156">您方才已了解如何修改 MRTK 設定檔中的設定。</span><span class="sxs-lookup"><span data-stu-id="150f4-156">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="150f4-157">如您所見，若要修改 MRTK 設定，您必須建立預設設定檔複本，以便能夠加以編輯。</span><span class="sxs-lookup"><span data-stu-id="150f4-157">As you can see, in order to modify MRTK settings you need to create copies of the default profiles so that you can edit them.</span></span> <span data-ttu-id="150f4-158">如果您想要使用新的設定建立設定檔，或者您可以回頭參考預設設定檔，則一律會有無法編輯的預設設定檔。</span><span class="sxs-lookup"><span data-stu-id="150f4-158">You will always have the default profiles, which are not editable, to go back to if you wanted to create a profile with new settings or you can refer back to the default profiles.</span></span> <span data-ttu-id="150f4-159">您可以調整的設定很多。</span><span class="sxs-lookup"><span data-stu-id="150f4-159">There are numerous settings that you can adjust.</span></span> <span data-ttu-id="150f4-160">如需 MRTK 設定檔設定的完整參考，請參閱這裡的 MRTK 檔： [https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)</span><span class="sxs-lookup"><span data-stu-id="150f4-160">For full reference to MRTK profile settings, refer to the MRTK documentation here: [https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)</span></span>

### <a name="hand-tracking-gestures-and-interactable-buttons"></a><span data-ttu-id="150f4-161">手部追蹤手勢和可互動的按鈕</span><span class="sxs-lookup"><span data-stu-id="150f4-161">Hand Tracking Gestures and Interactable buttons</span></span>

<span data-ttu-id="150f4-162">在本節中，您將瞭解如何使用 [手動追蹤] 來按下 [pressable] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="150f4-162">In this section, you will learn how to use hand tracking to press a pressable button.</span></span>

1. <span data-ttu-id="150f4-163">從 [專案] 資料夾選取 [資產]。</span><span class="sxs-lookup"><span data-stu-id="150f4-163">Select Assets from the projects folder.</span></span>

2. <span data-ttu-id="150f4-164">在搜尋列中輸入 "PressableButtonHoloLens2"。</span><span class="sxs-lookup"><span data-stu-id="150f4-164">Type "PressableButtonHoloLens2" in the search bar.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step2.png)

3. <span data-ttu-id="150f4-166">將名為 "PressableButtonHoloLens2" 的 prefab （以藍色方塊表示）拖曳至您的階層中，並將 [位置] 值設定為 x = 0、y = 0 和 z = 0.2，讓按鈕位於相機前方。</span><span class="sxs-lookup"><span data-stu-id="150f4-166">Drag the prefab (represented by a blue box) named "PressableButtonHoloLens2" into your hierarchy and set set the position values to x = 0, y = 0 and z = 0.2 so the button is in front of the camera.</span></span> <span data-ttu-id="150f4-167">（相機位於原始位置）。</span><span class="sxs-lookup"><span data-stu-id="150f4-167">(The camera is positioned at origin).</span></span>

    >[!NOTE]
    ><span data-ttu-id="150f4-168">如果您收到有關「匯入 TMP Essentials」的訊息，請在此時匯入。</span><span class="sxs-lookup"><span data-stu-id="150f4-168">If you get a message about “importing TMP Essentials”, import it at this time.</span></span> <span data-ttu-id="150f4-169">如果您的專案尚未包含 TMP Essentials，您可能需要在匯入 TMP Essentials 後重複此步驟，否則可能不會出現按鈕文字。</span><span class="sxs-lookup"><span data-stu-id="150f4-169">If TMP Essentials was not already part of your project, you might need to repeat this step after importing TMP Essentials, otherwise button text may not appear.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step3.png)

4. <span data-ttu-id="150f4-171">在場景中新增立方體。</span><span class="sxs-lookup"><span data-stu-id="150f4-171">Add a cube to the scene.</span></span> <span data-ttu-id="150f4-172">以滑鼠右鍵按一下 [階層] 區域，選取3D 物件，然後按一下 [Cube]。</span><span class="sxs-lookup"><span data-stu-id="150f4-172">Right click on the hierarchy area, select a 3D object, then click on Cube.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step6a.png)

    <span data-ttu-id="150f4-174">現在，立方體應該會在您的顯示區域內。</span><span class="sxs-lookup"><span data-stu-id="150f4-174">Now, a cube should be in your display.</span></span> <span data-ttu-id="150f4-175">它會非常大。</span><span class="sxs-lookup"><span data-stu-id="150f4-175">It will appear very large.</span></span> <span data-ttu-id="150f4-176">您可以調整座標（在 [階層] 區域中仍然選取 [Cube]）來減少大小。</span><span class="sxs-lookup"><span data-stu-id="150f4-176">You can adjust the coordinates (while Cube is still selected in the hierarchy area) to decrease the size.</span></span> <span data-ttu-id="150f4-177">將縮放值設定為 x = 0.02、y = 0.02 和 z = 0.02。</span><span class="sxs-lookup"><span data-stu-id="150f4-177">Set the scale values to x = 0.02, y = 0.02 and z = 0.02.</span></span> <span data-ttu-id="150f4-178">請務必將 cube 放在靠近按鈕的場景中，但不會與它重迭。</span><span class="sxs-lookup"><span data-stu-id="150f4-178">Be sure to position the cube in your scene near the button, but not overlapping with it.</span></span> <span data-ttu-id="150f4-179">在下圖中，cube 的位置是 x = 0、y = 0.4 和 z = 0.2。</span><span class="sxs-lookup"><span data-stu-id="150f4-179">In the image below, the cube’s position is x = 0, y = 0.4, and z = 0.2.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step6b.png)

    >[!NOTE]
    ><span data-ttu-id="150f4-181">一般情況下，Unity 中的 1 個單位會大致等於真實世界的 1 公尺。</span><span class="sxs-lookup"><span data-stu-id="150f4-181">In general, 1 unit in Unity is roughly equivalent to 1 meter in the physical world.</span></span> <span data-ttu-id="150f4-182">但有例外狀況，例如，當物件是所縮放物件的子系時。</span><span class="sxs-lookup"><span data-stu-id="150f4-182">There are exceptions to this, for example when objects are children of scaled objects.</span></span>

5. <span data-ttu-id="150f4-183">選取 [PressableButtonHoloLens2 遊戲] 物件後，在 [偵測器] 中向下滾動以尋找 [可互動（腳本）] 元件的 [事件] 區段。</span><span class="sxs-lookup"><span data-stu-id="150f4-183">With the PressableButtonHoloLens2 game object selected, in the Inspector scroll towards the bottom to locate the Events section of the Interactable (Script) component.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step4.png)

6. <span data-ttu-id="150f4-185">我們會修改現有的事件，讓按鈕在推送時提供回應事件。</span><span class="sxs-lookup"><span data-stu-id="150f4-185">We will modify the existing event to give the button an event to respond to when pushed.</span></span> <span data-ttu-id="150f4-186">如您所見，事件接收器類型設定為 InteractableOnPressReceiver。</span><span class="sxs-lookup"><span data-stu-id="150f4-186">As you can see, the Event Receiver Type is set to InteractableOnPressReceiver.</span></span> <span data-ttu-id="150f4-187">在追蹤的手部按下按鈕時，這可讓按鈕回應按下事件。</span><span class="sxs-lookup"><span data-stu-id="150f4-187">This allows the button to respond to a pressed event when a tracked hand presses the button.</span></span> <span data-ttu-id="150f4-188">此時，您也應該將互動篩選器變更為近到遠。</span><span class="sxs-lookup"><span data-stu-id="150f4-188">At this point you should also change the Interaction Filter to Near and Far.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step5.png)

7. <span data-ttu-id="150f4-190">在此步驟中，您會設定讓立方體在使用者按下按鈕時變更色彩。</span><span class="sxs-lookup"><span data-stu-id="150f4-190">In this step you will set up the cube to change color when your button is pressed.</span></span> <span data-ttu-id="150f4-191">選取 BaseScene 階層中的 [PressableButtonHoloLens2]，並將 [Cube 遊戲] 物件從 [BaseScene] 階層拖曳至 [僅限執行時間] 欄位，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="150f4-191">Select the PressableButtonHoloLens2 in the BaseScene hierarchy and drag the Cube game object from the BaseScene hierarchy into the Runtime Only field as shown in the image below.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step7a.png)

    <span data-ttu-id="150f4-193">按一下顯示 [沒有函數] 的下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="150f4-193">Click the dropdown list that says No Function.</span></span> <span data-ttu-id="150f4-194">選取 [MeshRenderer]，然後選取 [材質材質]。</span><span class="sxs-lookup"><span data-stu-id="150f4-194">Select MeshRenderer, then select Material material.</span></span> <span data-ttu-id="150f4-195">這可讓您在按下按鈕時變更材質。</span><span class="sxs-lookup"><span data-stu-id="150f4-195">This lets you change the material when the button is pressed.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step7b.png)

    <span data-ttu-id="150f4-197">按一下 [空白材質] 欄位旁的圓形，開啟 [選取材質] 快顯視窗。</span><span class="sxs-lookup"><span data-stu-id="150f4-197">Click the circle next to the empty material field to open the Select Material popup.</span></span> <span data-ttu-id="150f4-198">MRTK 包含許多材質和色彩可供選擇。</span><span class="sxs-lookup"><span data-stu-id="150f4-198">The MRTK includes many materials and colors to choose from.</span></span> <span data-ttu-id="150f4-199">在此範例中，您將使用在快顯搜尋列中輸入 "MRTK_Standard" 所找到的材質 MRTK_Standard_Cyan。</span><span class="sxs-lookup"><span data-stu-id="150f4-199">For this example, you are going to use the material, MRTK_Standard_Cyan, found by typing in "MRTK_Standard" in the popup search bar.</span></span> <span data-ttu-id="150f4-200">選取要填入 [材質] 欄位的 MRTK_Standard_Cyan 材質。</span><span class="sxs-lookup"><span data-stu-id="150f4-200">Select the MRTK_Standard_Cyan material to populate the material field.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step7c.png)

    <span data-ttu-id="150f4-202">此事件現在已設定好，因此在按下按鈕時，立方體便會根據您指定的材質變更色彩。</span><span class="sxs-lookup"><span data-stu-id="150f4-202">The event is now set so that when the button is pressed, the cube will change color based on the material you specified.</span></span> <span data-ttu-id="150f4-203">在此範例中，立方體會變更為青色。</span><span class="sxs-lookup"><span data-stu-id="150f4-203">In this example, the cube will change to the cyan color.</span></span>

8. <span data-ttu-id="150f4-204">接下來，您會設定放開動作，以便在放開時，按鈕會回復為其預設色彩。</span><span class="sxs-lookup"><span data-stu-id="150f4-204">Next you are going to set up the release action so that upon release, the button will go back to its default color.</span></span> <span data-ttu-id="150f4-205">重複上述的步驟7。</span><span class="sxs-lookup"><span data-stu-id="150f4-205">Repeat Step 7 above.</span></span> <span data-ttu-id="150f4-206">但這次使用 OnRelease 事件，而不是 OnPress MRTK_Standard_LightGray 材質，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="150f4-206">But this time with the OnRelease event instead of the OnPress MRTK_Standard_LightGray material as shown in the image below.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step8.png)

    <span data-ttu-id="150f4-208">現在當按下按鈕時，它會變更為新的色彩 [青色]。</span><span class="sxs-lookup"><span data-stu-id="150f4-208">Now when the button is pressed, it will change to a new color, cyan.</span></span> <span data-ttu-id="150f4-209">釋放按鈕時，它會變更回您指定的預設色彩（例如淺灰色）。按下畫面頂端的 [播放] 按鈕，在編輯器中試用，或部署至您的 HoloLens 2 進行測試。</span><span class="sxs-lookup"><span data-stu-id="150f4-209">When the button is released it will change back to the default color you specified (e.g., light gray.) Press the Play button on the top of the screen to try it out in the editor or deploy to your HoloLens 2 to test.</span></span> <span data-ttu-id="150f4-210">若要深入瞭解在編輯器中的模擬，包括手動模擬，請閱讀[MRTK 的模擬檔頁面](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>)。</span><span class="sxs-lookup"><span data-stu-id="150f4-210">To learn more about in-editor simulation, including hand simulation, read the [MRTK's simulation documentation page](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>).</span></span>

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a><span data-ttu-id="150f4-211">使用 MRTK 的方格物件集合來建立按鈕面板</span><span class="sxs-lookup"><span data-stu-id="150f4-211">Creating a panel of buttons using MRTK’s Grid Object Collection</span></span>

<span data-ttu-id="150f4-212">在本節中，您將瞭解如何使用 MRTK 的 GridObjectCollection 工具，將多個按鈕自動對齊整齊的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="150f4-212">In this section, you will learn how to automatically align multiple buttons into a neat user interface by using the MRTK’s GridObjectCollection tool.</span></span>

1. <span data-ttu-id="150f4-213">複製上一節中的按鈕，直到您有五個按鈕為止。</span><span class="sxs-lookup"><span data-stu-id="150f4-213">Duplicate the button from the previous section until you have five buttons.</span></span> <span data-ttu-id="150f4-214">有幾種方式可以執行這項操作：以滑鼠右鍵按一下按鈕，然後按一下 [複製]。</span><span class="sxs-lookup"><span data-stu-id="150f4-214">There are several ways to do this: -Right click on the button, and click Copy.</span></span> <span data-ttu-id="150f4-215">然後移至按鈕下方，再以滑鼠右鍵按一下，再按一下 [貼上]。</span><span class="sxs-lookup"><span data-stu-id="150f4-215">Then go down to below the button and right click again, and click Paste.</span></span>
    <span data-ttu-id="150f4-216">-以滑鼠右鍵按一下按鈕，然後按一下 [複製]。</span><span class="sxs-lookup"><span data-stu-id="150f4-216">-Right click on the button and click Duplicate.</span></span>
    <span data-ttu-id="150f4-217">-使用鍵盤命令，方法是按一下 cube，然後按下鍵盤上的 Ctrl D。</span><span class="sxs-lookup"><span data-stu-id="150f4-217">-Use the keyboard command by clicking on the cube, and pressing Ctrl D on your keyboard.</span></span>

    <span data-ttu-id="150f4-218">重複此動作，直到您有五個按鈕為止;請參閱下圖中的五個紅色箭號。</span><span class="sxs-lookup"><span data-stu-id="150f4-218">Repeat this until you have five buttons; see the five red arrows in image below.</span></span>

    ![Mrlearning Base Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. <span data-ttu-id="150f4-220">將按鈕群組到空白的父遊戲物件底下。</span><span class="sxs-lookup"><span data-stu-id="150f4-220">Group the buttons under an empty parent game object.</span></span> <span data-ttu-id="150f4-221">若要在方格集合中具有按鈕，您必須將按鈕分組在一般父物件底下。</span><span class="sxs-lookup"><span data-stu-id="150f4-221">In order to have the buttons in the grid collection, you need to group your buttons under a common parent object.</span></span> <span data-ttu-id="150f4-222">在 hiearachy 上按一下滑鼠右鍵，然後按一下 [建立空的]。</span><span class="sxs-lookup"><span data-stu-id="150f4-222">Right click in the hiearachy, and click Create Empty.</span></span> <span data-ttu-id="150f4-223">這會建立新的空白遊戲物件供您放入所有按鈕。</span><span class="sxs-lookup"><span data-stu-id="150f4-223">This creates a new empty game object for you to put all the buttons in.</span></span> <span data-ttu-id="150f4-224">它會顯示為 gameObject。</span><span class="sxs-lookup"><span data-stu-id="150f4-224">It shows up as gameObject.</span></span> <span data-ttu-id="150f4-225">以滑鼠右鍵按一下，並將它重新命名為 ButtonCollection。</span><span class="sxs-lookup"><span data-stu-id="150f4-225">Right click and rename it, ButtonCollection.</span></span>

    ![Mrlearning Base Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. <span data-ttu-id="150f4-227">將所有按鈕移至新的集合。</span><span class="sxs-lookup"><span data-stu-id="150f4-227">Move all the buttons into the new collection.</span></span> <span data-ttu-id="150f4-228">若要這麼做，請選取階層中的所有五個按鈕物件，並將其全部拖曳到 [ButtonCollection 遊戲物件] 底下，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="150f4-228">Do this by selecting all five of the button objects in your heirarchy, and drag them all under ButtonCollection game object as shown in the image below.</span></span> <span data-ttu-id="150f4-229">提示：按住 Ctrl 鍵並選取專案，以選取多個專案。</span><span class="sxs-lookup"><span data-stu-id="150f4-229">Tip: select multiple items by holding the Ctrl key while selecting items.</span></span>

    ![Mrlearning Base Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. <span data-ttu-id="150f4-231">將 MRTK 的 Grid 物件集合元件新增至按鈕集合。</span><span class="sxs-lookup"><span data-stu-id="150f4-231">Add MRTK’s Grid Object Collection component to the button collection.</span></span> <span data-ttu-id="150f4-232">若要這麼做，請選取 [ButtonCollection] 父物件。</span><span class="sxs-lookup"><span data-stu-id="150f4-232">To do this, select the ButtonCollection parent object.</span></span> <span data-ttu-id="150f4-233">從 [偵測器] 面板中，按一下 [新增元件] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="150f4-233">From the Inspector panel, click the Add Component button.</span></span> <span data-ttu-id="150f4-234">在搜尋列中搜尋 Grid 物件集合，並在清單中出現它時加以選取。</span><span class="sxs-lookup"><span data-stu-id="150f4-234">Search for Grid Object Collection in the search bar, and select it when it appears in the list.</span></span>

    ![Mrlearning Base Ch2 3Step4im](images/mrlearning-base-ch2-3-step4.png)

    <span data-ttu-id="150f4-236">Grid 物件集合元件可讓您在整齊的資料列、資料行或方格中組織按鈕或任何一組物件。</span><span class="sxs-lookup"><span data-stu-id="150f4-236">The Grid Object Collection component lets you organize buttons or any set of objects in a neat row, column, or grid.</span></span> <span data-ttu-id="150f4-237">這是 MRTK 所提供的其中一個建立區塊，可讓您快速且輕鬆地建立吸引人的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="150f4-237">This is one of the building blocks provided by the MRTK that gives you a quick and easy way to create enticing user interfaces.</span></span>

5. <span data-ttu-id="150f4-238">設定方格物件集合。</span><span class="sxs-lookup"><span data-stu-id="150f4-238">Configure the grid object collection.</span></span> <span data-ttu-id="150f4-239">若要確保所有按鈕都能面對使用者，請選取 [方向類型]。</span><span class="sxs-lookup"><span data-stu-id="150f4-239">To ensure all the buttons face the user, select Orient Type.</span></span> <span data-ttu-id="150f4-240">然後選取 [臉部父系轉寄]，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="150f4-240">Then select Face Parent Forward as shown in the image below.</span></span> <span data-ttu-id="150f4-241">接下來，變更儲存格大小來設定按鈕間距。</span><span class="sxs-lookup"><span data-stu-id="150f4-241">Next, change the cell size to set the space between your buttons.</span></span> <span data-ttu-id="150f4-242">針對儲存格寬度和儲存格高度，從0.05 個單位開始，以0.05 單元為單位，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="150f4-242">Start with 0.05 units by 0.05 units for the Cell Width and Cell Height as shown in the image below.</span></span> <span data-ttu-id="150f4-243">請確定 [距離] 設定為0，而 [資料列] 設定為1。</span><span class="sxs-lookup"><span data-stu-id="150f4-243">Make sure Distance is set to 0 and Rows is set to 1.</span></span> <span data-ttu-id="150f4-244">按一下 [更新集合]。</span><span class="sxs-lookup"><span data-stu-id="150f4-244">Click Update Collection.</span></span> <span data-ttu-id="150f4-245">場景看起來會類似下圖。</span><span class="sxs-lookup"><span data-stu-id="150f4-245">The scene will look similar to the picture below.</span></span>

    ![Mrlearning Base Ch2 3Step5im](images/mrlearning-base-ch2-3-step5.png)

    >[!NOTE]
    ><span data-ttu-id="150f4-247">根據子物件或父物件的方向，您可能需要在未來的專案中以不同的方式調整方向設定。</span><span class="sxs-lookup"><span data-stu-id="150f4-247">Depending on the orientation of the child objects or parent object, you will likely need to adjust the orientation setting differently in future projects.</span></span> <span data-ttu-id="150f4-248">根據集合中物件的大小，[儲存格寬度] 和 [儲存格高度] 欄位可能也需要以不同的方式定義。</span><span class="sxs-lookup"><span data-stu-id="150f4-248">The Cell Width and the Cell Height fields may also need to be defined differently, depending on the size of the objects in your collection.</span></span>

### <a name="adding-text-into-your-scene"></a><span data-ttu-id="150f4-249">在場景中新增文字</span><span class="sxs-lookup"><span data-stu-id="150f4-249">Adding Text into Your Scene</span></span>

<span data-ttu-id="150f4-250">在本節中，您會了解如何在混合實境體驗中新增和編輯文字。</span><span class="sxs-lookup"><span data-stu-id="150f4-250">In this section, you will learn how to add and edit text to your mixed reality experiences.</span></span> <span data-ttu-id="150f4-251">請遵循[此處](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation)的指示來確定您已在 Unity 中啟用 TextMeshPro (如果您還沒有這麼做)。</span><span class="sxs-lookup"><span data-stu-id="150f4-251">If you haven’t already, please ensure you have TextMeshPro enabled in Unity by following the instructions [here](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation).</span></span>

1. <span data-ttu-id="150f4-252">選取 [ButtonCollection] 父物件，然後以滑鼠右鍵按一下集合。</span><span class="sxs-lookup"><span data-stu-id="150f4-252">Select the ButtonCollection parent object, and right click the collection.</span></span> <span data-ttu-id="150f4-253">展開下拉式功能表中的 [3D 物件]。</span><span class="sxs-lookup"><span data-stu-id="150f4-253">Expand 3D object in the dropdown menu.</span></span> <span data-ttu-id="150f4-254">然後選取 [TextMeshPro-Text]。</span><span class="sxs-lookup"><span data-stu-id="150f4-254">Then select TextMeshPro - Text.</span></span> <span data-ttu-id="150f4-255">您應該會在按鈕集合底下看到 TextMeshPro 物件，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="150f4-255">You should see a TextMeshPro object under the button collection as shown in the image below.</span></span>

    <span data-ttu-id="150f4-256">![第2課 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG) ![第2課 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)</span><span class="sxs-lookup"><span data-stu-id="150f4-256">![Lesson2 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG) ![Lesson2 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)</span></span>

2. <span data-ttu-id="150f4-257">若要改善可讀性的文字大小和位置，請調整 [TextMeshPro] 元件中的 [字型大小] 欄位，以變更字型的大小。</span><span class="sxs-lookup"><span data-stu-id="150f4-257">To improve the text size and placement for readability, adjust the Font Size field in the TextMeshPro component to change the size of the font.</span></span> <span data-ttu-id="150f4-258">您也需要調整矩形轉換位置和尺規，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="150f4-258">You will also need to adjust the Rect Transform position and scale as shown in the image below.</span></span> <span data-ttu-id="150f4-259">請參閱下列影像，以瞭解用於文字設定的值。</span><span class="sxs-lookup"><span data-stu-id="150f4-259">See the images below for values used for our text configuration.</span></span> <span data-ttu-id="150f4-260">您可以隨意使用這些值做為起點，進一步改善文字欄位的大小和位置。</span><span class="sxs-lookup"><span data-stu-id="150f4-260">Feel free to use these values as a starting point to further improve the size and placement of your text field.</span></span>

    ![第2課 Chapter4 步驟3](images/mrlearning-base-ch2-4-step3.png)

3. <span data-ttu-id="150f4-262">在 [偵測器] 面板的 [TextMeshPro] 元件的 [文字] 欄位中，輸入「按鈕集合文字」，然後將對齊屬性調整為置中和靠上，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="150f4-262">In the TextMeshPro component’s text field in the Inspector panel, type in "Button Collection Text" and adjust the Alignment properties to be Center and Top as shown in the image below.</span></span>

    ![第2課 Chapter4 步驟4](images/mrlearning-base-ch2-4-step4.png)

4. <span data-ttu-id="150f4-264">若要修改按鈕物件上的文字值，請按一下任何按鈕旁的箭號將其展開，然後流覽至 SeeItSayItLabel 物件。</span><span class="sxs-lookup"><span data-stu-id="150f4-264">To modify the text values on the button objects, click the arrow next to any button to expand it and navigate to the SeeItSayItLabel object.</span></span> <span data-ttu-id="150f4-265">流覽至 TextMeshPro，您可以在其中編輯按鈕的文字，如上述步驟所述。</span><span class="sxs-lookup"><span data-stu-id="150f4-265">Navigate to TextMeshPro where you can edit the text to your buttons as described in the steps above.</span></span>

    ![Lesson2 Chapter4 Step5](images/Lesson2_Chapter4_Step5.JPG)

## <a name="congratulations"></a><span data-ttu-id="150f4-267">恭喜！</span><span class="sxs-lookup"><span data-stu-id="150f4-267">Congratulations</span></span>

<span data-ttu-id="150f4-268">在這一課，您已瞭解如何複製、自訂和設定 MRTK 設定檔設定（也就是空間感知網格可見度）。您也已瞭解如何與按鈕互動，以在 HoloLens 2 上使用追蹤來觸發事件。</span><span class="sxs-lookup"><span data-stu-id="150f4-268">In this lesson, you learned how to copy, customize, and configure an MRTK profile setting (i.e., spatial awareness mesh visibility.) You also learned how to interact with a button to trigger events using tracked hands on the HoloLens 2.</span></span> <span data-ttu-id="150f4-269">最後，您已瞭解如何使用 Unity 的文本網格 Pro 和 MRTK 的 Grid 物件集合元件來建立簡單的 UI 介面。</span><span class="sxs-lookup"><span data-stu-id="150f4-269">Finally, you learned how to create a simple UI interface using Unity's Text Mesh Pro and the MRTK's Grid Object Collection component.</span></span>

[<span data-ttu-id="150f4-270">下一課： 4. 放置動態內容並使用解析器</span><span class="sxs-lookup"><span data-stu-id="150f4-270">Next Lesson: 4. Placing dynamic content and using solvers</span></span>](mrlearning-base-ch3.md)
