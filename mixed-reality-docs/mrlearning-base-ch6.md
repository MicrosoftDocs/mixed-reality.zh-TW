---
title: 使用者入門教學課程-7。 建立農曆模組範例應用程式
description: 在這一課，您將結合從先前課程中學到的多個概念，以建立獨特的範例體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: b033e4f9a379fb1778da3d94da70262e073d141b
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926513"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="ee49f-105">7. 建立農曆模組範例應用程式</span><span class="sxs-lookup"><span data-stu-id="ee49f-105">7. Creating a Lunar Module sample application</span></span>

<span data-ttu-id="ee49f-106">在本教學課程中，會將多個概念與前一課結合，以建立獨特的範例體驗。</span><span class="sxs-lookup"><span data-stu-id="ee49f-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="ee49f-107">您將瞭解如何建立一個陰曆模組元件應用程式，讓使用者必須使用追蹤的手來挑選陰曆模組零件，並嘗試組合陰曆模組。</span><span class="sxs-lookup"><span data-stu-id="ee49f-107">You will learn how to create a lunar module assembly application whereby a user needs to use tracked hands to pick up lunar module parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="ee49f-108">我們會使用 [pressable] 按鈕來切換放置提示、重設我們的體驗，以及啟動我們的陰曆模組來進行空間！</span><span class="sxs-lookup"><span data-stu-id="ee49f-108">We use pressable buttons to toggle placement hints, to reset our experience, and to launch our lunar module into space!</span></span> <span data-ttu-id="ee49f-109">在未來的教學課程中，我們將繼續以這項體驗為基礎，其中包含強大的多使用者使用案例，可運用 Azure 空間錨點來進行空間對齊。</span><span class="sxs-lookup"><span data-stu-id="ee49f-109">In future tutorials, we will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="ee49f-110">目標</span><span class="sxs-lookup"><span data-stu-id="ee49f-110">Objectives</span></span>

- <span data-ttu-id="ee49f-111">結合來自先前課程的多個概念以建立獨特體驗</span><span class="sxs-lookup"><span data-stu-id="ee49f-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
- <span data-ttu-id="ee49f-112">了解如何切換物件</span><span class="sxs-lookup"><span data-stu-id="ee49f-112">Learn how to toggle objects</span></span>
- <span data-ttu-id="ee49f-113">使用可點按的按鈕來觸發複雜事件</span><span class="sxs-lookup"><span data-stu-id="ee49f-113">Trigger complex events using pressable buttons</span></span>
- <span data-ttu-id="ee49f-114">使用 rigidbody 物理特性和力</span><span class="sxs-lookup"><span data-stu-id="ee49f-114">Use rigidbody physics and forces</span></span>
- <span data-ttu-id="ee49f-115">探索工具提示的使用</span><span class="sxs-lookup"><span data-stu-id="ee49f-115">Explore the use of tool tips</span></span>

## <a name="instructions"></a><span data-ttu-id="ee49f-116">指示</span><span class="sxs-lookup"><span data-stu-id="ee49f-116">Instructions</span></span>

### <a name="configuring-the-lunar-module"></a><span data-ttu-id="ee49f-117">設定登月小艇</span><span class="sxs-lookup"><span data-stu-id="ee49f-117">Configuring the Lunar Module</span></span>

<span data-ttu-id="ee49f-118">在本節中，我們將介紹建立範例體驗所需的各種元件。</span><span class="sxs-lookup"><span data-stu-id="ee49f-118">In this section, we introduce the various components needed to create our sample experience.</span></span>

1. <span data-ttu-id="ee49f-119">將 [農曆模組元件] prefab 新增至您的基礎場景。</span><span class="sxs-lookup"><span data-stu-id="ee49f-119">Add the Lunar Module Assembly prefab to your base scene.</span></span> <span data-ttu-id="ee49f-120">若要這麼做，請在 [專案] 索引標籤中，流覽至 [資產] > BaseModuleAssets > Prefabs。</span><span class="sxs-lookup"><span data-stu-id="ee49f-120">To do this, in the Project tab navigate to Assets > BaseModuleAssets > Prefabs.</span></span> <span data-ttu-id="ee49f-121">您會看到兩個 rocket 啟動器 prefabs，將 Rocket Launcher_Tutorial prefab 拖曳到您的場景中，並依您想要的位置。</span><span class="sxs-lookup"><span data-stu-id="ee49f-121">You will see two rocket launcher prefabs, drag the Rocket Launcher_Tutorial prefab into your scene, and position as you wish.</span></span>

    >[!NOTE]
    ><span data-ttu-id="ee49f-122">Rocket Launcher_Complete prefab 是已完成的啟動器，提供供參考之用。</span><span class="sxs-lookup"><span data-stu-id="ee49f-122">The Rocket Launcher_Complete prefab is the completed launcher, provided for reference.</span></span>

    ![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

    <span data-ttu-id="ee49f-124">如果您展開階層中的 [Rocket Launcher_Tutorial 遊戲] 物件，並進一步展開 [陰曆] 模組物件，您會發現有數個子物件具有稱為「x-光線」的材質。</span><span class="sxs-lookup"><span data-stu-id="ee49f-124">If you expand the Rocket Launcher_Tutorial game object in your hierarchy and further expand the Lunar Module object, you find several child objects that have a material called "x-ray."</span></span> <span data-ttu-id="ee49f-125">「X 光線」材質允許使用稍微半透明的色彩，做為使用者的放置提示。</span><span class="sxs-lookup"><span data-stu-id="ee49f-125">The "x-ray" material allows for a slightly translucent color that will be used as placement hints for the user.</span></span> 

    ![第6課 Chapter1.txt Noteaim](images/Lesson6_Chapter1_noteaim.PNG)

    <span data-ttu-id="ee49f-127">在陰曆模組中，有五個部分會與使用者互動，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="ee49f-127">There are five parts to the lunar module that the user will interact with, as shown in the image below:</span></span>

    1. <span data-ttu-id="ee49f-128">月球車外殼</span><span class="sxs-lookup"><span data-stu-id="ee49f-128">The Rover Enclosure</span></span>
    2. <span data-ttu-id="ee49f-129">油箱</span><span class="sxs-lookup"><span data-stu-id="ee49f-129">The Fuel Tank</span></span>
    3. <span data-ttu-id="ee49f-130">能量電池</span><span class="sxs-lookup"><span data-stu-id="ee49f-130">The Energy Cell</span></span>
    4. <span data-ttu-id="ee49f-131">泊接座</span><span class="sxs-lookup"><span data-stu-id="ee49f-131">The Docking Portal</span></span>
    5. <span data-ttu-id="ee49f-132">外部感應器</span><span class="sxs-lookup"><span data-stu-id="ee49f-132">The External sensor</span></span>

    ![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

    >[!NOTE]
    ><span data-ttu-id="ee49f-134">您在基底場景階層中看見的遊戲物件名稱並不會與場景中的物件名稱相對應。</span><span class="sxs-lookup"><span data-stu-id="ee49f-134">The game object names that you see in your base scene hierarchy do not correspond to the names of the objects in the scene.</span></span>

2. <span data-ttu-id="ee49f-135">將音訊來源新增至 LunarModule 遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="ee49f-135">Add an audio source to the LunarModule game object.</span></span> <span data-ttu-id="ee49f-136">請確定已在場景階層中選取 LunarModule，然後按一下 [新增元件]。</span><span class="sxs-lookup"><span data-stu-id="ee49f-136">Make sure the LunarModule is selected in your scene hierarchy and click Add Component.</span></span> <span data-ttu-id="ee49f-137">搜尋 [音訊來源]，並將它新增至 [遊戲] 物件。</span><span class="sxs-lookup"><span data-stu-id="ee49f-137">Search for Audio Source and add it to the game object.</span></span> <span data-ttu-id="ee49f-138">現在將 [AudioClip] 欄位保留空白，但將特殊 Blend 設定從0變更為1，以啟用空間音訊。</span><span class="sxs-lookup"><span data-stu-id="ee49f-138">Leave the AudioClip field blank for now, but change the Special Blend setting from 0 to 1 so to enable spatial audio.</span></span> <span data-ttu-id="ee49f-139">您稍後將使用此音訊來源來播放啟動音效。</span><span class="sxs-lookup"><span data-stu-id="ee49f-139">You will use this audio source to play the launching sound later.</span></span>

    ![第6課 Chapter1.txt Step2im](images/Lesson6_Chapter1_step2im.PNG)

3. <span data-ttu-id="ee49f-141">新增腳本切換位置提示。</span><span class="sxs-lookup"><span data-stu-id="ee49f-141">Add the script Toggle Placement Hints.</span></span> <span data-ttu-id="ee49f-142">按一下 [新增元件]，並搜尋切換位置提示。</span><span class="sxs-lookup"><span data-stu-id="ee49f-142">Click Add Component and search for Toggle Placement Hints.</span></span> <span data-ttu-id="ee49f-143">這是自訂腳本，可讓您開啟和關閉半透明提示（具有 x 光線材質的物件），如先前所述。</span><span class="sxs-lookup"><span data-stu-id="ee49f-143">This is a custom script that lets you turn on and off the translucent hints (objects with the x-ray material), as mentioned earlier.</span></span>

    ![第6課 Chapter1.txt Step3im](images/Lesson6_Chapter1_step3im.PNG)

4. <span data-ttu-id="ee49f-145">因為我們有五個物件，所以請輸入 "5" 作為遊戲物件陣列大小。</span><span class="sxs-lookup"><span data-stu-id="ee49f-145">Since we have five objects, type "5" for the game object array size.</span></span> <span data-ttu-id="ee49f-146">您接著會看到五個新的元素。</span><span class="sxs-lookup"><span data-stu-id="ee49f-146">You will then see five new elements appear.</span></span>

    ![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

    <span data-ttu-id="ee49f-148">將每個半透明物件拖曳到所有 [名稱（遊戲物件）] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="ee49f-148">Drag each of the translucent objects into all the Name (Game Object) boxes.</span></span> <span data-ttu-id="ee49f-149">將下列物件從場景中的陰曆模組拖曳到 [物件陣列] 欄位中，如上圖所示：</span><span class="sxs-lookup"><span data-stu-id="ee49f-149">Drag the following objects from the lunar module in your scene into the object array fields as shown in the image above:</span></span>

    ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

    <span data-ttu-id="ee49f-151">現在已設定了切換位置提示腳本，可讓我們開啟和關閉提示。</span><span class="sxs-lookup"><span data-stu-id="ee49f-151">The Toggle Placement Hints script is now configured, which allows us to turn hints on and off.</span></span>

5. <span data-ttu-id="ee49f-152">新增 [啟動陰曆模組] 腳本。</span><span class="sxs-lookup"><span data-stu-id="ee49f-152">Add the Launch Lunar Module script.</span></span> <span data-ttu-id="ee49f-153">按一下 [新增元件] 按鈕，搜尋「啟動陰曆模組」並加以選取。</span><span class="sxs-lookup"><span data-stu-id="ee49f-153">Click the Add Component button, search for "launch lunar module" and select it.</span></span> <span data-ttu-id="ee49f-154">此腳本會啟動農曆模組。</span><span class="sxs-lookup"><span data-stu-id="ee49f-154">This script launches the lunar module.</span></span> <span data-ttu-id="ee49f-155">當我們按下設定的按鈕時，它會將向上的力新增至農曆模組的固定主體元件，並使模組向上啟動。</span><span class="sxs-lookup"><span data-stu-id="ee49f-155">When we press a configured button, it adds an upward force to the lunar module's rigid body component and causes the module to launch upwards.</span></span> <span data-ttu-id="ee49f-156">如果您位於室內，登月小艇可能會撞擊您的天花板網格。</span><span class="sxs-lookup"><span data-stu-id="ee49f-156">If you are indoors, the lunar module may crash against your ceiling mesh.</span></span> <span data-ttu-id="ee49f-157">如果您所在的區域具有高上限或沒有上限，農曆模組會無限期地進入空間。</span><span class="sxs-lookup"><span data-stu-id="ee49f-157">If you are in an area with high ceilings or no ceilings, the lunar module will fly into space indefinitely.</span></span>

    ![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

6. <span data-ttu-id="ee49f-159">調整推力來使登月小艇能優雅地向上升起。</span><span class="sxs-lookup"><span data-stu-id="ee49f-159">Adjust the thrust so that the lunar module will fly up gracefully.</span></span> <span data-ttu-id="ee49f-160">試試使用 0.01 的值。</span><span class="sxs-lookup"><span data-stu-id="ee49f-160">Try a value of 0.01.</span></span> <span data-ttu-id="ee49f-161">將 [Rb] 欄位保留空白。</span><span class="sxs-lookup"><span data-stu-id="ee49f-161">Leave the "Rb" field blank.</span></span> <span data-ttu-id="ee49f-162">Rb 代表固定主體，而此欄位將會在執行時間自動填入。</span><span class="sxs-lookup"><span data-stu-id="ee49f-162">Rb stands for Rigid body and this field will be automatically populated during runtime.</span></span>

    ![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a><span data-ttu-id="ee49f-164">陰曆模組元件總覽</span><span class="sxs-lookup"><span data-stu-id="ee49f-164">Lunar Module Parts overview</span></span>

<span data-ttu-id="ee49f-165">陰曆模組元件父物件是使用者與之互動物件的集合。</span><span class="sxs-lookup"><span data-stu-id="ee49f-165">The Lunar Module Parts parent object is the collection of the objects that the user interacts with.</span></span> <span data-ttu-id="ee49f-166">下列清單會提供遊戲物件名稱，加上括弧中標示為名稱的場景：</span><span class="sxs-lookup"><span data-stu-id="ee49f-166">The Game object names with scene labeled names in parentheses, are provided in the list below:</span></span>

- <span data-ttu-id="ee49f-167">死忠（能來源資料格）</span><span class="sxs-lookup"><span data-stu-id="ee49f-167">Backpack (Energy Cell)</span></span>
- <span data-ttu-id="ee49f-168">GasTank （燃料箱）</span><span class="sxs-lookup"><span data-stu-id="ee49f-168">GasTank (Fuel Tank)</span></span>
- <span data-ttu-id="ee49f-169">TopLeftBody (Rover Enclosure)</span><span class="sxs-lookup"><span data-stu-id="ee49f-169">TopLeftBody (Rover Enclosure)</span></span>
- <span data-ttu-id="ee49f-170">Nose (Docking Portal)</span><span class="sxs-lookup"><span data-stu-id="ee49f-170">Nose (Docking Portal)</span></span>
- <span data-ttu-id="ee49f-171">LeftTwirler (External Sensor)</span><span class="sxs-lookup"><span data-stu-id="ee49f-171">LeftTwirler (External Sensor)</span></span>

<span data-ttu-id="ee49f-172">請注意，每個物件都有操作處理常式，如第4課中所述。</span><span class="sxs-lookup"><span data-stu-id="ee49f-172">Notice that each of these objects has a manipulation handler, as explained in Lesson 4.</span></span> <span data-ttu-id="ee49f-173">這項功能可讓使用者抓取和操作物件。</span><span class="sxs-lookup"><span data-stu-id="ee49f-173">This feature enables users to grab and manipulate the object.</span></span> <span data-ttu-id="ee49f-174">另請注意，設定 [雙向操作類型] 設定為 [移動並旋轉]。</span><span class="sxs-lookup"><span data-stu-id="ee49f-174">Also note that the setting, Two Handed Manipulation Type, is set to Move and Rotate.</span></span> <span data-ttu-id="ee49f-175">此選項只允許使用者移動物件，而不會變更其大小，這是元件應用程式所需的功能。</span><span class="sxs-lookup"><span data-stu-id="ee49f-175">This option only permits the user to move the object and not change its size, which is the desired functionality for an assembly application.</span></span>
<span data-ttu-id="ee49f-176">此外，會取消選取 [目前的操作]，只允許模組元件的直接互動。</span><span class="sxs-lookup"><span data-stu-id="ee49f-176">In addition, Far Manipulation is unchecked to allow only for direct interaction of module parts.</span></span>

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

<span data-ttu-id="ee49f-178">部分元件示範腳本（如上所示）是用來管理使用者在陰曆模組上由使用者放置之物件的腳本。</span><span class="sxs-lookup"><span data-stu-id="ee49f-178">The Part Assembly Demo script (shown above) is the script that manages the objects that the user places on the lunar module by the user.</span></span>

<span data-ttu-id="ee49f-179">[要放置的物件] 欄位是已選取的轉換，如上圖所示，與所連接之物件相關聯的死忠/燃料箱。</span><span class="sxs-lookup"><span data-stu-id="ee49f-179">The Object To Place field is the transform that is selected, as shown in the image above, the backpack/fuel tank associated with the object that it connects to.</span></span>

<span data-ttu-id="ee49f-180">[近乎距離] 和 [距離距離] 設定會決定要放置或釋放的部分。</span><span class="sxs-lookup"><span data-stu-id="ee49f-180">The Near Distance and Far Distance settings determine the proximity to which parts snap in place or can be released.</span></span> <span data-ttu-id="ee49f-181">例如，死忠/燃料箱必須是0.1 單位，而不是陰曆模組，才會貼齊位置。</span><span class="sxs-lookup"><span data-stu-id="ee49f-181">For example, the backpack/fuel tank needs to be 0.1 units away from the lunar module before it will snap into place.</span></span> <span data-ttu-id="ee49f-182">[最遠距離] 設定會設定物件可以從農曆模組卸離之前的位置。</span><span class="sxs-lookup"><span data-stu-id="ee49f-182">The Far Distance setting sets the location where the object can be before it can detach from the lunar module.</span></span> <span data-ttu-id="ee49f-183">在此情況下，使用者的手必須抓住 backpack/fuel tank，並將它拖曳至距離登月小艇 0.2 單位的距離，才能將它從原本的定位移除。</span><span class="sxs-lookup"><span data-stu-id="ee49f-183">In this case, the user’s hand must grab the backpack/fuel tank and pull it 0.2 units away from the lunar module to remove it from snapping back into place.</span></span>

<span data-ttu-id="ee49f-184">工具提示物件是場景中的工具提示標籤。</span><span class="sxs-lookup"><span data-stu-id="ee49f-184">The Tool Tip Object is the tool tip label in the scene.</span></span> <span data-ttu-id="ee49f-185">當物件準備就緒時，會停用標籤。</span><span class="sxs-lookup"><span data-stu-id="ee49f-185">When the objects are snapped in place, the label is disabled.</span></span>

<span data-ttu-id="ee49f-186">音訊來源會自動抓取。</span><span class="sxs-lookup"><span data-stu-id="ee49f-186">The Audio Source is automatically grabbed.</span></span>

### <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="ee49f-187">設定放置提示按鈕</span><span class="sxs-lookup"><span data-stu-id="ee49f-187">Configuring the Placement Hints button</span></span>

<span data-ttu-id="ee49f-188">在[第2課](mrlearning-base-ch2.md)中，您已瞭解如何放置和設定按鈕來執行一些動作，例如變更專案的色彩，或讓它在推送時播放音效。</span><span class="sxs-lookup"><span data-stu-id="ee49f-188">In [Lesson 2](mrlearning-base-ch2.md), you learned how to place and configure buttons to do things like change the color of an item or make it play a sound when pushed.</span></span> <span data-ttu-id="ee49f-189">我們將會繼續使用那些原則來設定按鈕以切換放置提示。</span><span class="sxs-lookup"><span data-stu-id="ee49f-189">We will continue to use those principles as we configure our buttons for toggling placement hints.</span></span>

<span data-ttu-id="ee49f-190">其目標是設定按鈕，讓每次使用者按下 [放置提示] 按鈕時，都會切換半透明放置提示的可見度。</span><span class="sxs-lookup"><span data-stu-id="ee49f-190">The goal is to configure our button so that every time the user presses the Placement hint button, it toggles the visibility of the translucent placement hints.</span></span>

1. <span data-ttu-id="ee49f-191">將 [陰曆] 模組移至 [偵測器] 面板中的 [僅限空白執行時間] 插槽，同時在您的基底場景階層中選取放置提示物件。</span><span class="sxs-lookup"><span data-stu-id="ee49f-191">Move the lunar module to the empty Runtime Only slot in the inspector panel while the Placement Hints object is selected in your base scene hierarchy.</span></span>

    ![第6課 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG)

2. <span data-ttu-id="ee49f-193">按一下 [沒有函數] 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="ee49f-193">Click the No Function dropdown list.</span></span> <span data-ttu-id="ee49f-194">向下 TogglePlacementHints，然後選取該功能表下的 [ToggleGameObjects （）]。</span><span class="sxs-lookup"><span data-stu-id="ee49f-194">Go down to TogglePlacementHints and select ToggleGameObjects () under that menu.</span></span> <span data-ttu-id="ee49f-195">ToggleGameObjects （）會開啟和關閉放置提示，使其在每次按下按鈕時都可見或隱藏。</span><span class="sxs-lookup"><span data-stu-id="ee49f-195">ToggleGameObjects() toggles the placement hints on and off so that they are visible or invisible each time the button is pressed.</span></span>

    ![第6課 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a><span data-ttu-id="ee49f-197">設定重設按鈕</span><span class="sxs-lookup"><span data-stu-id="ee49f-197">Configuring the Reset button</span></span>

<span data-ttu-id="ee49f-198">在某些情況下，使用者會犯錯誤，不小心將物件擲回，或只是想要重設體驗。</span><span class="sxs-lookup"><span data-stu-id="ee49f-198">There will be situations where the user makes a mistake, accidentally throws the object away or just wants to reset the experience.</span></span> <span data-ttu-id="ee49f-199">[重設] 按鈕會新增重新開機體驗的功能。</span><span class="sxs-lookup"><span data-stu-id="ee49f-199">The Reset button adds the ability to restart the experience.</span></span>

1. <span data-ttu-id="ee49f-200">選取 [重設] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ee49f-200">Select the Reset button.</span></span> <span data-ttu-id="ee49f-201">在基底場景中，其名稱為 ResetRoundButton。</span><span class="sxs-lookup"><span data-stu-id="ee49f-201">In the base scene, it’s named ResetRoundButton.</span></span>

2. <span data-ttu-id="ee49f-202">將 [陰曆] 模組從 [基底場景] 階層拖曳至 [偵測器] 面板上按下按鈕底下的空插槽。</span><span class="sxs-lookup"><span data-stu-id="ee49f-202">Drag the lunar module from the base scene hierarchy into the empty slot under Button Pressed on the inspector panel.</span></span>

    ![第6課 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

3. <span data-ttu-id="ee49f-204">選取 [沒有函式] 下拉式功能表，並將滑鼠停留在 [LaunchLunarModule] 上，然後選取 [resetModule （）]。</span><span class="sxs-lookup"><span data-stu-id="ee49f-204">Select the No Function dropdown menu and hover over LaunchLunarModule, then select resetModule ().</span></span>

    ![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="ee49f-206">請注意，根據預設，GameObject. BroadcastMessage 會設定為 ResetPlacement。</span><span class="sxs-lookup"><span data-stu-id="ee49f-206">Notice that by default, the GameObject.BroadcastMessage is configured to ResetPlacement.</span></span> <span data-ttu-id="ee49f-207">這會為 RocketLauncher_Tutorial 的每個子物件廣播名為 ResetPlacement 的訊息。</span><span class="sxs-lookup"><span data-stu-id="ee49f-207">This broadcasts a message named ResetPlacement for every child object of the RocketLauncher_Tutorial.</span></span> <span data-ttu-id="ee49f-208">具有 ResetPlacement （）方法的任何物件，都會藉由重設其位置來回應該訊息。</span><span class="sxs-lookup"><span data-stu-id="ee49f-208">Any object that has a method for ResetPlacement() responds to that message by resetting it's position.</span></span>

### <a name="configuring-the-launch-button"></a><span data-ttu-id="ee49f-209">設定 [啟動] 按鈕</span><span class="sxs-lookup"><span data-stu-id="ee49f-209">Configuring the Launch button</span></span>

<span data-ttu-id="ee49f-210">本節說明如何設定 [啟動] 按鈕，讓使用者按下按鈕，並將 [陰曆] 模組啟動到空間。</span><span class="sxs-lookup"><span data-stu-id="ee49f-210">This section explains how to configure the Launch button, which permits the user to press the button and launch the lunar module into space.</span></span>

1. <span data-ttu-id="ee49f-211">選取 [啟動] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ee49f-211">Select the Launch button.</span></span> <span data-ttu-id="ee49f-212">在基底場景中，它稱為 LaunchRoundButton。</span><span class="sxs-lookup"><span data-stu-id="ee49f-212">In the base scene, it’s called LaunchRoundButton.</span></span> <span data-ttu-id="ee49f-213">將 [陰曆] 模組拖曳至 [偵測器] 面板中 [Touch End] 底下的空插槽。</span><span class="sxs-lookup"><span data-stu-id="ee49f-213">Drag the lunar module to the empty slot under Touch End in the Inspector panel.</span></span>

    ![第6課 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG)

2. <span data-ttu-id="ee49f-215">選取 [沒有函式] 下拉式功能表，並將滑鼠停留在 [LaunchLunarModule] 上，然後選取 [StopThruster （）]。</span><span class="sxs-lookup"><span data-stu-id="ee49f-215">Select the No Function dropdown menu and hover over LaunchLunarModule, and select StopThruster ().</span></span> <span data-ttu-id="ee49f-216">這會控制使用者想要提供給陰曆模組的天生量。</span><span class="sxs-lookup"><span data-stu-id="ee49f-216">This controls how much thrust the user wants to give to the lunar module.</span></span>

    ![第6課 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)

3. <span data-ttu-id="ee49f-218">將 [陰曆] 模組從 [基底場景] 階層拖曳至 [偵測器] 面板中所按下按鈕底下的空插槽。</span><span class="sxs-lookup"><span data-stu-id="ee49f-218">Drag the lunar module from the base scene hierarchy into the empty slot under Button Pressed in the inspector panel.</span></span>

4. <span data-ttu-id="ee49f-219">按一下 [沒有函式] 下拉式功能表，然後在 [LaunchLunarModule] 上選取 [StartThruster （）]。</span><span class="sxs-lookup"><span data-stu-id="ee49f-219">Click the No function dropdown menu and then on LaunchLunarModule and select StartThruster ().</span></span>

    ![第6課 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)

5. <span data-ttu-id="ee49f-221">將音樂新增至農曆模組，以便在 rocket 時播放音樂。</span><span class="sxs-lookup"><span data-stu-id="ee49f-221">Add music to the lunar module so that music plays when the rocket takes off.</span></span> <span data-ttu-id="ee49f-222">若要這麼做，請將 [陰曆] 模組拖曳至 [按下的按鈕] 下的下一個空白插槽（）。</span><span class="sxs-lookup"><span data-stu-id="ee49f-222">To do this, drag the lunar module to the next empty slot under Button Pressed().</span></span>

6. <span data-ttu-id="ee49f-223">選取 [沒有函式] 下拉式功能表，將滑鼠停留在 Spatialize 上，然後選取 [PlayOneShot （AudioClip）]。</span><span class="sxs-lookup"><span data-stu-id="ee49f-223">Select the No Function dropdown menu, hover over AudioSource and select PlayOneShot (AudioClip).</span></span> <span data-ttu-id="ee49f-224">您可以自行探索包含在 MRTK 中的各種音效。</span><span class="sxs-lookup"><span data-stu-id="ee49f-224">Feel free to explore the variety of sounds included with the MRTK.</span></span> <span data-ttu-id="ee49f-225">在此範例中，我們將使用「MRTK_Gem」。</span><span class="sxs-lookup"><span data-stu-id="ee49f-225">In this example, we'll use "MRTK_Gem."</span></span>

    ![第6課 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)

### <a name="congratulations"></a><span data-ttu-id="ee49f-227">恭喜！</span><span class="sxs-lookup"><span data-stu-id="ee49f-227">Congratulations</span></span>

<span data-ttu-id="ee49f-228">您已完全設定此應用程式。</span><span class="sxs-lookup"><span data-stu-id="ee49f-228">You have fully configured this application.</span></span> <span data-ttu-id="ee49f-229">現在，當您按下 [播放] 時，您可以完整組合陰曆模組、切換提示、啟動陰曆模組，然後將它重設為重新啟動。</span><span class="sxs-lookup"><span data-stu-id="ee49f-229">Now, when you press play, you can fully assemble the lunar module, toggle hints, launch the lunar module and reset it to start again.</span></span>
