---
title: MR 學習基本模組 - 登月小艇組立範例體驗
description: 在本課程中，我們將會結合從先前課程中所學習到的多個概念，以建立獨特的範例體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 8a2f388e842d521f991203916177e3dac15769eb
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730851"
---
# <a name="mr-learning-base-module---lunar-module-assembly-sample-experience"></a><span data-ttu-id="804a7-104">MR 學習基本模組 - 登月小艇組立範例體驗</span><span class="sxs-lookup"><span data-stu-id="804a7-104">MR Learning Base Module - Lunar Module Assembly Sample Experience</span></span>

<span data-ttu-id="804a7-105">在本課程中，我們將會結合從先前課程中所學習到的多個概念，以建立獨特的範例體驗。</span><span class="sxs-lookup"><span data-stu-id="804a7-105">In this lesson, we will combine multiple concepts learned from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="804a7-106">我們將會建立登月小艇組立應用程式；在此應用程式中，使用者必須使用被追蹤的手掌來撿起登月小艇組件，並嘗試組立登月小艇。</span><span class="sxs-lookup"><span data-stu-id="804a7-106">We will create a lunar module assembly application whereby a user will need to use tracked hands to pick up lunar module parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="804a7-107">我們將會使用可點按的按鈕來切換放置提示、重設體驗，以及將登月小艇發射到太空中！</span><span class="sxs-lookup"><span data-stu-id="804a7-107">We will use pressable buttons to toggle placement hints, to reset our experience, and to launch our lunar module into space!</span></span> <span data-ttu-id="804a7-108">在未來的教學課程中，我們將以此體驗作為基礎持續建置，其中包括能運用 Azure Spatial Anchors 來取得空間錨點的強大多使用者使用案例。</span><span class="sxs-lookup"><span data-stu-id="804a7-108">In future tutorials, we will continue to build upon this experience, including powerful multi-user use-cases that leverages Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="804a7-109">目標</span><span class="sxs-lookup"><span data-stu-id="804a7-109">Objectives</span></span>

- <span data-ttu-id="804a7-110">結合來自先前課程的多個概念以建立獨特體驗</span><span class="sxs-lookup"><span data-stu-id="804a7-110">Combine multiple concepts from previous lessons to create a unique experience</span></span>
- <span data-ttu-id="804a7-111">了解如何切換物件</span><span class="sxs-lookup"><span data-stu-id="804a7-111">Learn how to toggle objects</span></span>
- <span data-ttu-id="804a7-112">使用可點按的按鈕來觸發複雜事件</span><span class="sxs-lookup"><span data-stu-id="804a7-112">Trigger complex events using pressable buttons</span></span>
- <span data-ttu-id="804a7-113">使用 rigidbody 物理特性和力</span><span class="sxs-lookup"><span data-stu-id="804a7-113">Use rigidbody physics and forces</span></span>
- <span data-ttu-id="804a7-114">探索工具提示的使用</span><span class="sxs-lookup"><span data-stu-id="804a7-114">Explore the use of tool tips</span></span>

## <a name="instructions"></a><span data-ttu-id="804a7-115">指示</span><span class="sxs-lookup"><span data-stu-id="804a7-115">Instructions</span></span>

### <a name="configuring-the-lunar-module"></a><span data-ttu-id="804a7-116">設定登月小艇</span><span class="sxs-lookup"><span data-stu-id="804a7-116">Configuring the Lunar Module</span></span>

<span data-ttu-id="804a7-117">在本章中，我們將會介紹建立範例體驗所需的各種元件。</span><span class="sxs-lookup"><span data-stu-id="804a7-117">In this chapter, we will be introduced to the various components needed to create our sample experience.</span></span>

1. <span data-ttu-id="804a7-118">將登月小艇組立預製加入至您的基底場景。</span><span class="sxs-lookup"><span data-stu-id="804a7-118">Add the lunar module assembly prefab to your Base Scene.</span></span> <span data-ttu-id="804a7-119">若要這麼做，請在專案索引標籤中搜尋 "Rocket Launcher_Tutorial"。</span><span class="sxs-lookup"><span data-stu-id="804a7-119">To do this, in your project tab, search for "Rocket Launcher_Tutorial."</span></span> <span data-ttu-id="804a7-120">您也可以在 Assets>BaseModuleAssets>Prefabs 中找到該預製。</span><span class="sxs-lookup"><span data-stu-id="804a7-120">You may also find the prefab in Assets>BaseModuleAssets>Prefabs.</span></span> <span data-ttu-id="804a7-121">您可能會看見兩個火箭發射器預製，一個名為 "tutorial"，另一個則名為 "complete"。</span><span class="sxs-lookup"><span data-stu-id="804a7-121">You may see two rocket launcher prefabs; one with the name "tutorial" and another with the name "complete."</span></span> <span data-ttu-id="804a7-122">請將 "Rocket Launcher_Tutorial" 預製拖曳到您的基底場景。</span><span class="sxs-lookup"><span data-stu-id="804a7-122">Drag the "Rocket Launcher_Tutorial" prefab to your Base Scene.</span></span> <span data-ttu-id="804a7-123">您可以將預製置於場景中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="804a7-123">Feel free to position the placement of the prefab in your scene.</span></span>
   <span data-ttu-id="804a7-124">注意："Rocket Launcher_Complete" 預製是已完成的發射器，供您參考使用。</span><span class="sxs-lookup"><span data-stu-id="804a7-124">Note: The "Rocket Launcher_Complete" prefab is the completed launcher, provided for reference.</span></span> 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

<span data-ttu-id="804a7-126">如果您在階層中展開 "Rocket Launcher_Tutorial" 遊戲物件，並進一步展開 "Lunar Module" 物件，您將會看到具有名為 "x-ray" 之材質的數個子物件。</span><span class="sxs-lookup"><span data-stu-id="804a7-126">If you expand the "Rocket Launcher_Tutorial" game object in your hierarchy, and further expand the "Lunar Module" object, you will see several child objects that have a material called "x-ray."</span></span> <span data-ttu-id="804a7-127">"x-ray" 材質可提供些微半透明的色彩，而我們會將它用於提供給使用者的放置提示。</span><span class="sxs-lookup"><span data-stu-id="804a7-127">The "x-ray" material allows for a slightly translucent color which we will use as placement hints for the user.</span></span> 

<span data-ttu-id="804a7-128">![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) 登月小艇有五個使用者會進行互動的部分，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="804a7-128">![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) There are five parts to the lunar module that the user is going to interact with, as shown in the image below:</span></span>

1.  <span data-ttu-id="804a7-129">月球車外殼</span><span class="sxs-lookup"><span data-stu-id="804a7-129">The Rover Enclosure</span></span>
2.  <span data-ttu-id="804a7-130">油箱</span><span class="sxs-lookup"><span data-stu-id="804a7-130">The Fuel Tank</span></span>
3.  <span data-ttu-id="804a7-131">能量電池</span><span class="sxs-lookup"><span data-stu-id="804a7-131">The Energy Cell</span></span>
4.  <span data-ttu-id="804a7-132">泊接座</span><span class="sxs-lookup"><span data-stu-id="804a7-132">The Docking Portal</span></span> 
5.  <span data-ttu-id="804a7-133">外部感應器</span><span class="sxs-lookup"><span data-stu-id="804a7-133">The External sensor</span></span>

![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> <span data-ttu-id="804a7-135">注意：您在基底場景階層中看見的遊戲物件名稱並不會與場景中的物件名稱相對應。</span><span class="sxs-lookup"><span data-stu-id="804a7-135">Note: The game object names that you see in your base scene hierarchy do not correspond to the names of the objects in the scene.</span></span>

<span data-ttu-id="804a7-136">步驟 2：將音訊來源加入至登月小艇。</span><span class="sxs-lookup"><span data-stu-id="804a7-136">Step 2: Add an audio source to the lunar module.</span></span> <span data-ttu-id="804a7-137">確定您已選取基底場景中的登月小艇，然後按一下 [Add Component] \(新增元件\)。</span><span class="sxs-lookup"><span data-stu-id="804a7-137">Make sure the lunar module is selected in your base scene hierarchy and click "Add Component."</span></span> <span data-ttu-id="804a7-138">搜尋 "Audio Source" 然後將它加入至物件。</span><span class="sxs-lookup"><span data-stu-id="804a7-138">Search for "Audio Source" and add it to the object.</span></span> <span data-ttu-id="804a7-139">暫時將它保留空白。</span><span class="sxs-lookup"><span data-stu-id="804a7-139">Leave it blank for now.</span></span> <span data-ttu-id="804a7-140">我們稍後將會用它來播放發射音效。</span><span class="sxs-lookup"><span data-stu-id="804a7-140">We will use this to play the launching sound later.</span></span>
 <span data-ttu-id="804a7-141">![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG) 步驟 3：加入指令碼 "toggle placement hints"。</span><span class="sxs-lookup"><span data-stu-id="804a7-141">![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG) Step 3: Add the script "toggle placement hints."</span></span> <span data-ttu-id="804a7-142">按一下 [Add Component] \(新增元件\)，然後搜尋 "Toggle Placement Hints"。</span><span class="sxs-lookup"><span data-stu-id="804a7-142">Click "Add Component" and search for "Toggle Placement Hints."</span></span> <span data-ttu-id="804a7-143">這個自訂指令碼可讓您開啟和關閉稍早所述的半透明提示 (具有 x-ray 材質的物件)。</span><span class="sxs-lookup"><span data-stu-id="804a7-143">This is a custom script that allows you to turn on and off the translucent hints (objects with the x-ray material) mentioned earlier.</span></span> 
<span data-ttu-id="804a7-144">![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG) 步驟 4：由於我們有 5 個物件，請針對遊戲物件陣列大小輸入 "5"。</span><span class="sxs-lookup"><span data-stu-id="804a7-144">![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG) Step 4: Since we have 5 objects, type in "5" for the game object array size.</span></span> <span data-ttu-id="804a7-145">您應該會看見出現 5 個新的元素。</span><span class="sxs-lookup"><span data-stu-id="804a7-145">Then you should see 5 new elements appear.</span></span> 

![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

<span data-ttu-id="804a7-147">將每個半透明物件拖曳到顯示 [None (Game Object)] \(無 (遊戲物件)\) 的方塊。</span><span class="sxs-lookup"><span data-stu-id="804a7-147">Drag each of the translucent objects into the boxes that say "None (Game Object)."</span></span> <span data-ttu-id="804a7-148">將下列物件從登月小艇拖曳到基底場景中：</span><span class="sxs-lookup"><span data-stu-id="804a7-148">Drag the following objects from the lunar module in your base scene:</span></span> 

<span data-ttu-id="804a7-149">•   Backpack</span><span class="sxs-lookup"><span data-stu-id="804a7-149">•   Backpack</span></span>

<span data-ttu-id="804a7-150">•   GasTank</span><span class="sxs-lookup"><span data-stu-id="804a7-150">•   GasTank</span></span>

<span data-ttu-id="804a7-151">•   Topleftbody</span><span class="sxs-lookup"><span data-stu-id="804a7-151">•   Topleftbody</span></span>

<span data-ttu-id="804a7-152">•   Nose</span><span class="sxs-lookup"><span data-stu-id="804a7-152">•   Nose</span></span>

<span data-ttu-id="804a7-153">•   LeftTwirler</span><span class="sxs-lookup"><span data-stu-id="804a7-153">•   LeftTwirler</span></span>

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

<span data-ttu-id="804a7-155">您已設定好 "toggle placement hints" 指令碼。</span><span class="sxs-lookup"><span data-stu-id="804a7-155">Now the "toggle placement hints" script is configured.</span></span> <span data-ttu-id="804a7-156">這可讓我們開啟和關閉提示。</span><span class="sxs-lookup"><span data-stu-id="804a7-156">This will allow us to turn the hints on and off.</span></span>

<span data-ttu-id="804a7-157">步驟 5：加入 "launch lunar module" 指令碼。</span><span class="sxs-lookup"><span data-stu-id="804a7-157">Step 5: Add the "launch lunar module" script.</span></span> <span data-ttu-id="804a7-158">按一下 [Add Component] \(新增元件\)，搜尋 "launch lunar module" 並選取它。</span><span class="sxs-lookup"><span data-stu-id="804a7-158">Click the "Add Component" button, search for "launch lunar module" and select it.</span></span> <span data-ttu-id="804a7-159">此指令碼將會負責發射登月小艇。</span><span class="sxs-lookup"><span data-stu-id="804a7-159">This script will be responsible for launching the lunar module.</span></span> <span data-ttu-id="804a7-160">當我們按下已設定的按鈕時，它會將向上力加入至登月小艇的 rigidbody 元件，並會使小艇向上發射。</span><span class="sxs-lookup"><span data-stu-id="804a7-160">When we press a configured button, it will add an upward force to the lunar module's rigid body component and will cause the module to launch upwards.</span></span> <span data-ttu-id="804a7-161">如果您位於室內，登月小艇可能會撞擊您的天花板網格。</span><span class="sxs-lookup"><span data-stu-id="804a7-161">If you are indoors, the lunar module may crash against your ceiling mesh.</span></span> <span data-ttu-id="804a7-162">但如果您位於室外，它將會無限制地飛向太空。</span><span class="sxs-lookup"><span data-stu-id="804a7-162">But if you are outdoors, it will fly in to space indefinitely.</span></span> 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

<span data-ttu-id="804a7-164">步驟 6：調整推力來使登月小艇能優雅地向上升起。</span><span class="sxs-lookup"><span data-stu-id="804a7-164">Step 6: Adjust the thrust so that the lunar module will fly up gracefully.</span></span> <span data-ttu-id="804a7-165">試試使用 0.01 的值。</span><span class="sxs-lookup"><span data-stu-id="804a7-165">Try a value of 0.01.</span></span> <span data-ttu-id="804a7-166">將 [Rb] 欄位保留空白。</span><span class="sxs-lookup"><span data-stu-id="804a7-166">Leave the "Rb" field blank.</span></span> <span data-ttu-id="804a7-167">Rb 代表 rigidbody，因此系統將會在執行階段自動填入此欄位。</span><span class="sxs-lookup"><span data-stu-id="804a7-167">Rb stands for rigid body, and this field will be automatically populated during runtime.</span></span>

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a><span data-ttu-id="804a7-169">登月小艇組件概觀</span><span class="sxs-lookup"><span data-stu-id="804a7-169">Lunar Module Parts Overview</span></span>
<span data-ttu-id="804a7-170">登月小艇組件父物件是使用者會互動之物件的集合。</span><span class="sxs-lookup"><span data-stu-id="804a7-170">The Lunar Module parts parent object is the collection of the objects that the user will interact with.</span></span> <span data-ttu-id="804a7-171">下列清單提供遊戲物件名稱 (並於後方以括號註明場景標示名稱)：</span><span class="sxs-lookup"><span data-stu-id="804a7-171">The game object names (with scene labeled names in paretheses) are provided in the list below:</span></span>

- <span data-ttu-id="804a7-172">Backpack (Fuel Tank)</span><span class="sxs-lookup"><span data-stu-id="804a7-172">Backpack (Fuel Tank)</span></span>
- <span data-ttu-id="804a7-173">GasTank (Energy Cell)</span><span class="sxs-lookup"><span data-stu-id="804a7-173">GasTank (Energy Cell)</span></span>
- <span data-ttu-id="804a7-174">TopLeftBody (Rover Enclosure)</span><span class="sxs-lookup"><span data-stu-id="804a7-174">TopLeftBody (Rover Enclosure)</span></span>
- <span data-ttu-id="804a7-175">Nose (Docking Portal)</span><span class="sxs-lookup"><span data-stu-id="804a7-175">Nose (Docking Portal)</span></span>
- <span data-ttu-id="804a7-176">LeftTwirler (External Sensor)</span><span class="sxs-lookup"><span data-stu-id="804a7-176">LeftTwirler (External Sensor)</span></span>

<span data-ttu-id="804a7-177">請注意，這些物件都具有操作處理常式，如第 4 課中所述。</span><span class="sxs-lookup"><span data-stu-id="804a7-177">Notice that each of these objects has the manipulation handler, as discussed in lesson 4.</span></span> <span data-ttu-id="804a7-178">透過使用操作處理常式，使用者將能抓住並操作物件。</span><span class="sxs-lookup"><span data-stu-id="804a7-178">With the manipulation handler, users are able to grab and manipulate the object.</span></span> <span data-ttu-id="804a7-179">同時請注意，[two handed manipulation type] \(兩手操作類型\) 設定已設定為 [move and rotate] \(移動和旋轉\)。</span><span class="sxs-lookup"><span data-stu-id="804a7-179">Also note that the setting "two handed manipulation type" is set to "move and rotate."</span></span> <span data-ttu-id="804a7-180">這僅會允許使用者移動物件，而不會讓他們變更其大小；此為組成應用程式的所需功能。</span><span class="sxs-lookup"><span data-stu-id="804a7-180">This only permits the user to move the object and not change its size, which is the desired functionality for an assembly application.</span></span>
<span data-ttu-id="804a7-181">此外，遠方操作已被取消選取，以僅允許與小艇組件直接互動。</span><span class="sxs-lookup"><span data-stu-id="804a7-181">In addition, far manipulation is unchecked to allow only for direct interaction of module parts.</span></span>

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

<span data-ttu-id="804a7-183">組件組立示範指令碼 (如上所示) 是管理要由使用者放置到登月小艇上之物件的指令碼。</span><span class="sxs-lookup"><span data-stu-id="804a7-183">The part assembly demo script (shown above) is the scrip that manages the objects to be placed on to the lunar module by the user.</span></span> 

<span data-ttu-id="804a7-184">[Object To Place] \(要放置的物件\) 欄位是所選取的轉換項目 (針對上面的影像則為 backpack/fuel tank)，搭配其能連線的物件。</span><span class="sxs-lookup"><span data-stu-id="804a7-184">The "Object To Place" field is the transform that is selected (n the case of the image above, the backpack/fuel tank) with the object that it can connect to.</span></span> 

<span data-ttu-id="804a7-185">[Near Distance] \(近距離\) 和 [Far Distance] \(遠距離\) 設定負責決定物件會貼齊至定位或分離的距離。</span><span class="sxs-lookup"><span data-stu-id="804a7-185">The "Near Distance" and "Far Distance" settings are responsible for determining the proximity to which parts will snap in place or be released.</span></span> <span data-ttu-id="804a7-186">例如，backpack/fuel tank 必須位於距離登月小艇 0.1 單位以內的位置才會貼齊至定位。</span><span class="sxs-lookup"><span data-stu-id="804a7-186">For example, the backpack/fuel tank would need to be 0.1 units away from the lunar module to snap into place.</span></span> <span data-ttu-id="804a7-187">[Far Distance] \(遠距離\) 會設定物件要距離登月小艇多遠才會與其分離。</span><span class="sxs-lookup"><span data-stu-id="804a7-187">The "Far Distance" sets the location where the object needs to be to detach from the lunar module.</span></span> <span data-ttu-id="804a7-188">在此情況下，使用者的手必須抓住 backpack/fuel tank，並將它拖曳至距離登月小艇 0.2 單位的距離，才能將它從原本的定位移除。</span><span class="sxs-lookup"><span data-stu-id="804a7-188">In this case, the user’s hand must grab the backpack/fuel tank and pull it 0.2 units away from the lunar module to remove it from snapping back into place.</span></span>

<span data-ttu-id="804a7-189">[Tool Tip Object] \(工具提示物件\) 是場景中的工具提示標籤。</span><span class="sxs-lookup"><span data-stu-id="804a7-189">The "Tool Tip Object" is the tool tip label in the scene.</span></span> <span data-ttu-id="804a7-190">當物件貼齊至定位時，系統便會停用標籤。</span><span class="sxs-lookup"><span data-stu-id="804a7-190">When the objects are snapped in place, the label will be disabled.</span></span> 

<span data-ttu-id="804a7-191">系統將會自動抓取音訊來源。</span><span class="sxs-lookup"><span data-stu-id="804a7-191">The Audio Source will be automatically grabbed.</span></span> 

### <a name="placement-hints-buttons"></a><span data-ttu-id="804a7-192">放置提示按鈕</span><span class="sxs-lookup"><span data-stu-id="804a7-192">Placement Hints Buttons</span></span>
<span data-ttu-id="804a7-193">在[第 2 課](mrlearning-base-ch2.md)中，您已了解如何放置按鈕並設定它以變更項目色彩，或是在按下時播放音效等功能。</span><span class="sxs-lookup"><span data-stu-id="804a7-193">In [Lesson 2](mrlearning-base-ch2.md), you learned how to place and configure buttons to do things like change the color of an item or make it play a sound when it is pushed.</span></span> <span data-ttu-id="804a7-194">我們將會繼續使用那些原則來設定按鈕以切換放置提示。</span><span class="sxs-lookup"><span data-stu-id="804a7-194">We will continue to use those principles as we configure our buttons for toggling placement hints.</span></span> 

<span data-ttu-id="804a7-195">我們的目標是將按鈕設定為每當使用者按下放置提示按鈕時，它便會切換半透明放置提示的可見性。</span><span class="sxs-lookup"><span data-stu-id="804a7-195">The goal is to configure our button so that every time the user presses the placement hint button, it will toggle visibility of the translucent placement hints.</span></span> 

<span data-ttu-id="804a7-196">步驟 1：在已選取基底場景階層中的 Placement Hints 物件的同時，將登月小艇移至偵測程式面板中的空白 [runtime only] \(僅限執行階段\) 位置。</span><span class="sxs-lookup"><span data-stu-id="804a7-196">Step 1: Move the Lunar Module to the empty "runtime only" slot in the inspector panel while the Placement Hints object is selected in your base scene hierarchy.</span></span> 
 <span data-ttu-id="804a7-197">![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) 步驟 2：按一下顯示 [no function] \(無功能\) 的下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="804a7-197">![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) Step 2: Now click the dropdown list where it says, "no function."</span></span> <span data-ttu-id="804a7-198">移至 [TogglePlacementHints]，然後在該功能表底下，選取 [ToggleGameObjects()]。</span><span class="sxs-lookup"><span data-stu-id="804a7-198">Go down to "TogglePlacementHints," and under that menu select "ToggleGameObjects ()."</span></span> <span data-ttu-id="804a7-199">[ToggleGameObjects()] 會將放置提示開啟和關閉，使它們會在按鈕被按下時變成可見或不可見。</span><span class="sxs-lookup"><span data-stu-id="804a7-199">ToggleGameObjects() will toggle the placement hints on and off so that they are visible or invisible every time the button is pressed.</span></span>
 <span data-ttu-id="804a7-200">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="804a7-200">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span></span>

### <a name="configuring-the-reset-button"></a><span data-ttu-id="804a7-201">設定重設按鈕</span><span class="sxs-lookup"><span data-stu-id="804a7-201">Configuring the Reset Button</span></span>

<span data-ttu-id="804a7-202">使用者可能會犯錯或意外地將物件丟到無法觸及的位置，或是只想要重設整個體驗。</span><span class="sxs-lookup"><span data-stu-id="804a7-202">There will be situations where the user makes a mistake, or accidently throws the object away, or just wants to rest the experience.</span></span> <span data-ttu-id="804a7-203">重設按鈕將能提供重設體驗的能力。</span><span class="sxs-lookup"><span data-stu-id="804a7-203">The reset button will add the ability to restart the experience.</span></span> 

<span data-ttu-id="804a7-204">步驟 1：選取重設按鈕。</span><span class="sxs-lookup"><span data-stu-id="804a7-204">Step 1: Select the reset button.</span></span> <span data-ttu-id="804a7-205">在基底場景中，它名為 "ResetRoundButton"。</span><span class="sxs-lookup"><span data-stu-id="804a7-205">In the base scene, it’s named "ResetRoundButton."</span></span> 

<span data-ttu-id="804a7-206">步驟 2：將登月小艇從基底場景階層中拖曳到偵測程式面板中 [button pressed] \(按下按鈕\) 底下的空白位置。</span><span class="sxs-lookup"><span data-stu-id="804a7-206">Step 2: Drag the lunar module from the base scene hierarchy into the empty slot under "button pressed" the inspector panel.</span></span>
 <span data-ttu-id="804a7-207">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="804a7-207">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span></span>

<span data-ttu-id="804a7-208">步驟 3：選取顯示為 [no function] \(無功能\) 的下拉式功能表，然後暫留在 [LaunchLunarModule] 上方。</span><span class="sxs-lookup"><span data-stu-id="804a7-208">Step 3: Select the dropdown menu that says, "no function" and hover over "LaunchLunarModule."</span></span> <span data-ttu-id="804a7-209">現在請選取 [resetModule ()]。</span><span class="sxs-lookup"><span data-stu-id="804a7-209">Now select "resetModule ()."</span></span>

![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> <span data-ttu-id="804a7-211">注意：您將會注意到 [GameObject.BroadcastMessage] 預設會被設定為 "ResetPlacement"。</span><span class="sxs-lookup"><span data-stu-id="804a7-211">Note: You will notice that by default the "GameObject.BroadcastMessage" is configured to "ResetPlacement."</span></span> <span data-ttu-id="804a7-212">這將會針對 RocketLauncher_Tutorial 的每個子物件廣播稱為 "ResetPlacement" 的訊息。</span><span class="sxs-lookup"><span data-stu-id="804a7-212">This will broadcast a message called "ResetPlacement" for every child object of RocketLauncher_Tutorial.</span></span> <span data-ttu-id="804a7-213">任何具有 "ResetPlacement()" 之方法的物件，都會重設其位置來回應該訊息。</span><span class="sxs-lookup"><span data-stu-id="804a7-213">Any object that has a method for "ResetPlacement()" will respond to that message by resetting it's position.</span></span> 

### <a name="launching-the-lunar-module"></a><span data-ttu-id="804a7-214">發射登月小艇</span><span class="sxs-lookup"><span data-stu-id="804a7-214">Launching the Lunar Module</span></span>
<span data-ttu-id="804a7-215">在本章中，我們將會設定發射按鈕。</span><span class="sxs-lookup"><span data-stu-id="804a7-215">This chapter we will be configuring the launch button.</span></span> <span data-ttu-id="804a7-216">這能讓使用者按下按鈕，並將登月小艇發射到太空中。</span><span class="sxs-lookup"><span data-stu-id="804a7-216">This will permit the user to press the button and launch the Lunar Module into space.</span></span>

<span data-ttu-id="804a7-217">步驟 1：選取發射按鈕 (它在基底場景中名叫 "LaunchRoundButton")。</span><span class="sxs-lookup"><span data-stu-id="804a7-217">Step 1: Select the launch button (in the base scene it’s named "LaunchRoundButton").</span></span> <span data-ttu-id="804a7-218">將登月小艇拖曳到偵測程式面板中 [Touch End] \(觸控結束\) 底下的空白位置。</span><span class="sxs-lookup"><span data-stu-id="804a7-218">Drag the Lunar Module to the empty slot under "Touch End" in the inspector panel.</span></span>
 <span data-ttu-id="804a7-219">![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) 步驟 2：選取顯示為 [no function] \(無功能\) 的下拉式功能表。</span><span class="sxs-lookup"><span data-stu-id="804a7-219">![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) Step 2: Select the dropdown menu that says, "no function."</span></span> <span data-ttu-id="804a7-220">暫留在 [LaunchLunarModule] 上方並選取 [StopThruster()]。</span><span class="sxs-lookup"><span data-stu-id="804a7-220">Hover over "LaunchLunarModule" and select "StopThruster ()."</span></span> <span data-ttu-id="804a7-221">這能讓使用者控制要提供給登月小艇的推力多寡。</span><span class="sxs-lookup"><span data-stu-id="804a7-221">This will control how much thrust the user wants to give to the Lunar Module.</span></span> 
 <span data-ttu-id="804a7-222">![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG) 步驟 3：在 [ButtonPressed()] 底下，將登月小艇 (按一下，按住並拖曳) 加入至空白位置。</span><span class="sxs-lookup"><span data-stu-id="804a7-222">![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG) Step 3: Under "ButtonPressed()", add the Lunar Module (click, hold, and drag) to the empty slot.</span></span> 

<span data-ttu-id="804a7-223">步驟 4：按一下顯示為 [no function] \(無功能\) 的下拉式功能表，然後暫留在 [LaunchLunarModule] 上方並選取 [StartThruster()]。</span><span class="sxs-lookup"><span data-stu-id="804a7-223">Step 4: Click the dropdown menu that says, "no function" and hover over "LaunchLunarModule" and select "StartThruster ()."</span></span> 
 <span data-ttu-id="804a7-224">![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG) 步驟 5：將音樂加入至登月小艇，使音樂會在火箭發射時播放。</span><span class="sxs-lookup"><span data-stu-id="804a7-224">![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG) Step 5: Add music to the Lunar Module so that when the rocket takes off, the music will play.</span></span> <span data-ttu-id="804a7-225">若要這麼做，請將登月小艇拖曳到 [Button Pressed()] 底下的下一個空白位置。</span><span class="sxs-lookup"><span data-stu-id="804a7-225">To do this, drag the Lunar Module to the next empty slot under "Button Pressed()".</span></span>

<span data-ttu-id="804a7-226">步驟 6：選取顯示為 [no function] \(無功能\) 的下拉式功能表，然後暫留在 [AudioSource] 上方並選取 [PlayOneShot (AudioClip)]。</span><span class="sxs-lookup"><span data-stu-id="804a7-226">Step 6: Select the dropdown menu that says, "no function" and hover over "AudioSource" and select "PlayOneShot (AudioClip)."</span></span> <span data-ttu-id="804a7-227">您可以自行探索包含在 MRTK 中的各種音效。</span><span class="sxs-lookup"><span data-stu-id="804a7-227">Feel free to explore the variety of sounds included with the MRTK.</span></span> <span data-ttu-id="804a7-228">在此範例中，我們會使用 "MRTK_Gem"。</span><span class="sxs-lookup"><span data-stu-id="804a7-228">For this example, we are going to stick with "MRTK_Gem."</span></span>
 <span data-ttu-id="804a7-229">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span><span class="sxs-lookup"><span data-stu-id="804a7-229">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span></span>


### <a name="congratulations"></a><span data-ttu-id="804a7-230">恭喜</span><span class="sxs-lookup"><span data-stu-id="804a7-230">Congratulations</span></span> 
<span data-ttu-id="804a7-231">您已完整地設定好這個應用程式！</span><span class="sxs-lookup"><span data-stu-id="804a7-231">You have fully configured this application!</span></span> <span data-ttu-id="804a7-232">現在當您開始進行遊戲時，便可以完整組立登月小艇、切換提示、發射登月小艇，以及重設以重新進行一遍。</span><span class="sxs-lookup"><span data-stu-id="804a7-232">Now when you press play, you can fully assemble the Lunar Module, toggle hints, launch the Lunar Module, and reset it to do it all over again.</span></span>
