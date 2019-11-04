---
title: 使用者入門教學課程-7。 建立農曆模組範例應用程式
description: 在這一課，您將結合從先前課程中學到的多個概念，以建立獨特的範例體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: a4f405b29ac87945a8585beeed83c1beb450eb0e
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437752"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="80745-105">7. 建立農曆模組範例應用程式</span><span class="sxs-lookup"><span data-stu-id="80745-105">7. Creating a Lunar Module sample application</span></span>

<span data-ttu-id="80745-106">在本教學課程中，會將多個概念與前一課結合，以建立獨特的範例體驗。</span><span class="sxs-lookup"><span data-stu-id="80745-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="80745-107">您將瞭解如何建立一個陰曆模組元件應用程式，讓使用者必須使用追蹤的手來挑選陰曆模組零件，並嘗試組合陰曆模組。</span><span class="sxs-lookup"><span data-stu-id="80745-107">You will learn how to create a lunar module assembly application whereby a user needs to use tracked hands to pick up lunar module parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="80745-108">我們會使用 [pressable] 按鈕來切換放置提示、重設我們的體驗，以及啟動我們的陰曆模組來進行空間！</span><span class="sxs-lookup"><span data-stu-id="80745-108">We use pressable buttons to toggle placement hints, to reset our experience, and to launch our lunar module into space!</span></span> <span data-ttu-id="80745-109">在未來的教學課程中，我們將繼續以這項體驗為基礎，其中包含強大的多使用者使用案例，可運用 Azure 空間錨點來進行空間對齊。</span><span class="sxs-lookup"><span data-stu-id="80745-109">In future tutorials, we will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="80745-110">目標</span><span class="sxs-lookup"><span data-stu-id="80745-110">Objectives</span></span>

- <span data-ttu-id="80745-111">結合來自先前課程的多個概念以建立獨特體驗</span><span class="sxs-lookup"><span data-stu-id="80745-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
- <span data-ttu-id="80745-112">了解如何切換物件</span><span class="sxs-lookup"><span data-stu-id="80745-112">Learn how to toggle objects</span></span>
- <span data-ttu-id="80745-113">使用可點按的按鈕來觸發複雜事件</span><span class="sxs-lookup"><span data-stu-id="80745-113">Trigger complex events using pressable buttons</span></span>
- <span data-ttu-id="80745-114">使用 rigidbody 物理特性和力</span><span class="sxs-lookup"><span data-stu-id="80745-114">Use rigidbody physics and forces</span></span>
- <span data-ttu-id="80745-115">探索工具提示的使用</span><span class="sxs-lookup"><span data-stu-id="80745-115">Explore the use of tool tips</span></span>

## <a name="instructions"></a><span data-ttu-id="80745-116">指示</span><span class="sxs-lookup"><span data-stu-id="80745-116">Instructions</span></span>

### <a name="configuring-the-lunar-module"></a><span data-ttu-id="80745-117">設定登月小艇</span><span class="sxs-lookup"><span data-stu-id="80745-117">Configuring the Lunar Module</span></span>

<span data-ttu-id="80745-118">在本節中，我們將介紹建立範例體驗所需的各種元件。</span><span class="sxs-lookup"><span data-stu-id="80745-118">In this section, we introduce the various components needed to create our sample experience.</span></span>

1. <span data-ttu-id="80745-119">將 [農曆模組元件] prefab 新增至您的基礎場景。</span><span class="sxs-lookup"><span data-stu-id="80745-119">Add the Lunar Module Assembly prefab to your base scene.</span></span> <span data-ttu-id="80745-120">若要這麼做，請在 專案 索引標籤中搜尋 Rocket Launcher_Tutorial。在 資產 中尋找 prefab-> BaseModuleAssets-> Prefabs。</span><span class="sxs-lookup"><span data-stu-id="80745-120">To do this, search for the Rocket Launcher_Tutorial in the Project tab. Find the prefab in Assets->BaseModuleAssets->Prefabs.</span></span> <span data-ttu-id="80745-121">您也會看到兩個 rocket 啟動器 prefabs;一個名稱為 "教學課程"，另一個名稱為 "complete"。</span><span class="sxs-lookup"><span data-stu-id="80745-121">You'll also see two rocket launcher prefabs; one with the name "tutorial" and the other with the name "complete".</span></span> <span data-ttu-id="80745-122">將 [Rocket Launcher_Tutorial prefab] 拖曳至您的基礎場景，並依您想要的位置。</span><span class="sxs-lookup"><span data-stu-id="80745-122">Drag the Rocket Launcher_Tutorial prefab to your base scene, and position as you wish.</span></span>
<span data-ttu-id="80745-123">注意： Rocket Launcher_Complete prefab 是已完成的啟動器，提供供參考之用。</span><span class="sxs-lookup"><span data-stu-id="80745-123">Note: The Rocket Launcher_Complete prefab is the completed launcher, provided for reference.</span></span> 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

<span data-ttu-id="80745-125">如果您展開階層中的 [Rocket Launcher_Tutorial 遊戲] 物件，並進一步展開 [陰曆] 模組物件，您會發現有數個子物件具有稱為「x-光線」的材質。</span><span class="sxs-lookup"><span data-stu-id="80745-125">If you expand the Rocket Launcher_Tutorial game object in your hierarchy and further expand the Lunar Module object, you find several child objects that have a material called "x-ray."</span></span> <span data-ttu-id="80745-126">「X 光線」材質允許使用稍微半透明的色彩，做為使用者的放置提示。</span><span class="sxs-lookup"><span data-stu-id="80745-126">The "x-ray" material allows for a slightly translucent color that will be used as placement hints for the user.</span></span> 

<span data-ttu-id="80745-127">![第6課 Chapter1.txt Noteaim](images/Lesson6_Chapter1_noteaim.PNG) 使用者將與其互動的陰曆模組有五個部分，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="80745-127">![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) There are five parts to the lunar module that the user will interact with, as shown in the image below:</span></span>

1.  <span data-ttu-id="80745-128">月球車外殼</span><span class="sxs-lookup"><span data-stu-id="80745-128">The Rover Enclosure</span></span>
2.  <span data-ttu-id="80745-129">油箱</span><span class="sxs-lookup"><span data-stu-id="80745-129">The Fuel Tank</span></span>
3.  <span data-ttu-id="80745-130">能量電池</span><span class="sxs-lookup"><span data-stu-id="80745-130">The Energy Cell</span></span>
4.  <span data-ttu-id="80745-131">泊接座</span><span class="sxs-lookup"><span data-stu-id="80745-131">The Docking Portal</span></span> 
5.  <span data-ttu-id="80745-132">外部感應器</span><span class="sxs-lookup"><span data-stu-id="80745-132">The External sensor</span></span>

![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> <span data-ttu-id="80745-134">注意：您在基底場景階層中看到的遊戲物件名稱不會對應到場景中的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="80745-134">Note: The Game object names that you see in your base scene hierarchy do not correspond to the names of the objects in the scene.</span></span>

<span data-ttu-id="80745-135">步驟2：將音訊來源新增至農曆模組。</span><span class="sxs-lookup"><span data-stu-id="80745-135">Step 2: Add an audio source to the lunar module.</span></span> <span data-ttu-id="80745-136">請確定已在您的基底場景階層中選取 [陰曆] 模組，然後按一下 [新增元件]。</span><span class="sxs-lookup"><span data-stu-id="80745-136">Make sure the lunar module is selected in your base scene hierarchy and click Add Component.</span></span> <span data-ttu-id="80745-137">搜尋 [音訊來源]，並將它新增至物件。</span><span class="sxs-lookup"><span data-stu-id="80745-137">Search for Audio Source and add it to the object.</span></span> <span data-ttu-id="80745-138">現在請將它保留為空白，但按一下 [Spatialize] 核取方塊以啟用空間音訊。</span><span class="sxs-lookup"><span data-stu-id="80745-138">Leave it blank for now, but click the "Spatialize" checkbox to enable spatial audio.</span></span> <span data-ttu-id="80745-139">稍後您將使用此來播放啟動音效。</span><span class="sxs-lookup"><span data-stu-id="80745-139">You will use this to play the launching sound later.</span></span>

 ![第6課 Chapter1.txt Step2im](images/Lesson6_Chapter1_step2im.PNG)  
<span data-ttu-id="80745-141">步驟3：加入腳本切換位置提示。</span><span class="sxs-lookup"><span data-stu-id="80745-141">Step 3: Add the script Toggle Placement Hints.</span></span> <span data-ttu-id="80745-142">按一下 [新增元件]，並搜尋切換位置提示。</span><span class="sxs-lookup"><span data-stu-id="80745-142">Click Add Component and search for Toggle Placement Hints.</span></span> <span data-ttu-id="80745-143">這是自訂腳本，可讓您開啟和關閉半透明提示（具有 x 光線材質的物件），如先前所述。</span><span class="sxs-lookup"><span data-stu-id="80745-143">This is a custom script that lets you turn on and off the translucent hints (objects with the x-ray material), as mentioned earlier.</span></span>  
![第6課 Chapter1.txt Step3im](images/Lesson6_Chapter1_step3im.PNG)  
<span data-ttu-id="80745-145">步驟4：因為我們有五個物件，請輸入 "5" 作為遊戲物件陣列大小。</span><span class="sxs-lookup"><span data-stu-id="80745-145">Step 4: Since we have five objects, type "5" for the game object array size.</span></span> <span data-ttu-id="80745-146">您接著會看到五個新的元素。</span><span class="sxs-lookup"><span data-stu-id="80745-146">You'll then see five new elements appear.</span></span>  


![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

<span data-ttu-id="80745-148">將每個半透明物件拖曳到所有名稱（遊戲物件）方塊中。</span><span class="sxs-lookup"><span data-stu-id="80745-148">Drag each of the translucent objects into all the Name (Game Obect) boxes.</span></span>
<span data-ttu-id="80745-149">將下列物件從登月小艇拖曳到基底場景中：</span><span class="sxs-lookup"><span data-stu-id="80745-149">Drag the following objects from the lunar module in your base scene:</span></span> 

<span data-ttu-id="80745-150">•   Backpack</span><span class="sxs-lookup"><span data-stu-id="80745-150">•   Backpack</span></span>

<span data-ttu-id="80745-151">•   GasTank</span><span class="sxs-lookup"><span data-stu-id="80745-151">•   GasTank</span></span>

<span data-ttu-id="80745-152">•   Topleftbody</span><span class="sxs-lookup"><span data-stu-id="80745-152">•   Topleftbody</span></span>

<span data-ttu-id="80745-153">•   Nose</span><span class="sxs-lookup"><span data-stu-id="80745-153">•   Nose</span></span>

<span data-ttu-id="80745-154">•   LeftTwirler</span><span class="sxs-lookup"><span data-stu-id="80745-154">•   LeftTwirler</span></span>

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

<span data-ttu-id="80745-156">現在已設定了切換位置提示腳本，可讓我們開啟和關閉提示。</span><span class="sxs-lookup"><span data-stu-id="80745-156">The Toggle Placement Hints script is now configured, which allows us to turn hints on and off.</span></span>

<span data-ttu-id="80745-157">步驟5：新增啟動陰曆模組腳本。</span><span class="sxs-lookup"><span data-stu-id="80745-157">Step 5: Add the Launch Lunar Module script.</span></span> <span data-ttu-id="80745-158">按一下 [新增元件] 按鈕，搜尋「啟動陰曆模組」並加以選取。</span><span class="sxs-lookup"><span data-stu-id="80745-158">Click the Add Component button, search for "launch lunar module" and select it.</span></span> <span data-ttu-id="80745-159">此腳本會啟動農曆模組。</span><span class="sxs-lookup"><span data-stu-id="80745-159">This script launches the lunar module.</span></span> <span data-ttu-id="80745-160">當我們按下設定的按鈕時，它會將向上的力新增至農曆模組的固定主體元件，並使模組向上啟動。</span><span class="sxs-lookup"><span data-stu-id="80745-160">When we press a configured button, it adds an upward force to the lunar module's rigid body component and causes the module to launch upwards.</span></span> <span data-ttu-id="80745-161">如果您位於室內，登月小艇可能會撞擊您的天花板網格。</span><span class="sxs-lookup"><span data-stu-id="80745-161">If you are indoors, the lunar module may crash against your ceiling mesh.</span></span> <span data-ttu-id="80745-162">如果您所在的區域具有高上限或沒有上限，農曆模組會無限期地進入空間。</span><span class="sxs-lookup"><span data-stu-id="80745-162">If you are in an area with high ceilings or no ceilings, the lunar module will fly into space indefinitely.</span></span> 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

<span data-ttu-id="80745-164">步驟6：調整天生，讓陰曆模組能夠正常運作。</span><span class="sxs-lookup"><span data-stu-id="80745-164">Step 6: Adjust the thrust so that the lunar module will fly up gracefully.</span></span> <span data-ttu-id="80745-165">試試使用 0.01 的值。</span><span class="sxs-lookup"><span data-stu-id="80745-165">Try a value of 0.01.</span></span> <span data-ttu-id="80745-166">將 [Rb] 欄位保留空白。</span><span class="sxs-lookup"><span data-stu-id="80745-166">Leave the "Rb" field blank.</span></span> <span data-ttu-id="80745-167">Rb 代表固定主體，而此欄位將會在執行時間自動填入。</span><span class="sxs-lookup"><span data-stu-id="80745-167">Rb stands for Rigid body and this field will be automatically populated during runtime.</span></span>

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a><span data-ttu-id="80745-169">陰曆模組元件總覽</span><span class="sxs-lookup"><span data-stu-id="80745-169">Lunar Module Parts overview</span></span>
<span data-ttu-id="80745-170">陰曆模組元件父物件是使用者與之互動物件的集合。</span><span class="sxs-lookup"><span data-stu-id="80745-170">The Lunar Module Parts parent object is the collection of the objects that the user interacts with.</span></span> <span data-ttu-id="80745-171">下列清單會提供遊戲物件名稱，其中包含 paretheses 中標示為名稱的場景：</span><span class="sxs-lookup"><span data-stu-id="80745-171">The Game object names with scene labeled names in paretheses, are provided in the list below:</span></span>

- <span data-ttu-id="80745-172">Backpack (Fuel Tank)</span><span class="sxs-lookup"><span data-stu-id="80745-172">Backpack (Fuel Tank)</span></span>
- <span data-ttu-id="80745-173">GasTank (Energy Cell)</span><span class="sxs-lookup"><span data-stu-id="80745-173">GasTank (Energy Cell)</span></span>
- <span data-ttu-id="80745-174">TopLeftBody (Rover Enclosure)</span><span class="sxs-lookup"><span data-stu-id="80745-174">TopLeftBody (Rover Enclosure)</span></span>
- <span data-ttu-id="80745-175">Nose (Docking Portal)</span><span class="sxs-lookup"><span data-stu-id="80745-175">Nose (Docking Portal)</span></span>
- <span data-ttu-id="80745-176">LeftTwirler (External Sensor)</span><span class="sxs-lookup"><span data-stu-id="80745-176">LeftTwirler (External Sensor)</span></span>

<span data-ttu-id="80745-177">請注意，每個物件都有操作處理常式，如第4課中所述。</span><span class="sxs-lookup"><span data-stu-id="80745-177">Notice that each of these objects has a manipulation handler, as explained in Lesson 4.</span></span> <span data-ttu-id="80745-178">這項功能可讓使用者抓取和操作物件。</span><span class="sxs-lookup"><span data-stu-id="80745-178">This feature enables users to grab and manipulate the object.</span></span> <span data-ttu-id="80745-179">另請注意，設定 [雙向操作類型] 設定為 [移動並旋轉]。</span><span class="sxs-lookup"><span data-stu-id="80745-179">Also note that the setting, Two Handed Manipulation Type, is set to Move and Rotate.</span></span> <span data-ttu-id="80745-180">此選項只允許使用者移動物件，而不會變更其大小，這是元件應用程式所需的功能。</span><span class="sxs-lookup"><span data-stu-id="80745-180">This option only permits the user to move the object and not change its size, which is the desired functionality for an assembly application.</span></span>
<span data-ttu-id="80745-181">此外，會取消選取 [目前的操作]，只允許模組元件的直接互動。</span><span class="sxs-lookup"><span data-stu-id="80745-181">In addition, Far Manipulation is unchecked to allow only for direct interaction of module parts.</span></span>

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

<span data-ttu-id="80745-183">部分元件示範腳本（如上所示）是用來管理使用者在陰曆模組上由使用者放置之物件的腳本。</span><span class="sxs-lookup"><span data-stu-id="80745-183">The Part Assembly Demo script (shown above) is the script that manages the objects that the user places on the lunar module by the user.</span></span> 

<span data-ttu-id="80745-184">[要放置的物件] 欄位是已選取的轉換，如上圖所示，與所連接之物件相關聯的死忠/燃料箱。</span><span class="sxs-lookup"><span data-stu-id="80745-184">The Object To Place field is the transform that is selected, as shown in the image above, the backpack/fuel tank associated with the object that it connects to.</span></span> 

<span data-ttu-id="80745-185">[近乎距離] 和 [距離距離] 設定會決定要放置或釋放的部分。</span><span class="sxs-lookup"><span data-stu-id="80745-185">The Near Distance and Far Distance settings determine the proximity to which parts snap in place or can be released.</span></span> <span data-ttu-id="80745-186">例如，死忠/燃料箱必須是0.1 單位，而不是陰曆模組，才會貼齊位置。</span><span class="sxs-lookup"><span data-stu-id="80745-186">For example, the backpack/fuel tank needs to be 0.1 units away from the lunar module before it will snap into place.</span></span> <span data-ttu-id="80745-187">[最遠距離] 設定會設定物件可以從農曆模組卸離之前的位置。</span><span class="sxs-lookup"><span data-stu-id="80745-187">The Far Distance setting sets the location where the object can be before it can detach from the lunar module.</span></span> <span data-ttu-id="80745-188">在此情況下，使用者的手必須抓住 backpack/fuel tank，並將它拖曳至距離登月小艇 0.2 單位的距離，才能將它從原本的定位移除。</span><span class="sxs-lookup"><span data-stu-id="80745-188">In this case, the user’s hand must grab the backpack/fuel tank and pull it 0.2 units away from the lunar module to remove it from snapping back into place.</span></span>

<span data-ttu-id="80745-189">工具提示物件是場景中的工具提示標籤。</span><span class="sxs-lookup"><span data-stu-id="80745-189">The Tool Tip Object is the tool tip label in the scene.</span></span> <span data-ttu-id="80745-190">當物件準備就緒時，會停用標籤。</span><span class="sxs-lookup"><span data-stu-id="80745-190">When the objects are snapped in place, the label is disabled.</span></span> 

<span data-ttu-id="80745-191">音訊來源會自動抓取。</span><span class="sxs-lookup"><span data-stu-id="80745-191">The Audio Source is automatically grabbed.</span></span> 

### <a name="placement-hints-buttons"></a><span data-ttu-id="80745-192">放置提示按鈕</span><span class="sxs-lookup"><span data-stu-id="80745-192">Placement Hints buttons</span></span>
<span data-ttu-id="80745-193">在[第2課](mrlearning-base-ch2.md)中，您已瞭解如何放置和設定按鈕來執行一些動作，例如變更專案的色彩，或讓它在推送時播放音效。</span><span class="sxs-lookup"><span data-stu-id="80745-193">In [Lesson 2](mrlearning-base-ch2.md), you learned how to place and configure buttons to do things like change the color of an item or make it play a sound when pushed.</span></span> <span data-ttu-id="80745-194">我們將會繼續使用那些原則來設定按鈕以切換放置提示。</span><span class="sxs-lookup"><span data-stu-id="80745-194">We will continue to use those principles as we configure our buttons for toggling placement hints.</span></span> 

<span data-ttu-id="80745-195">其目標是設定按鈕，讓每次使用者按下 [放置提示] 按鈕時，都會切換半透明放置提示的可見度。</span><span class="sxs-lookup"><span data-stu-id="80745-195">The goal is to configure our button so that every time the user presses the Placement hint button, it toggles the visibility of the translucent placement hints.</span></span> 

<span data-ttu-id="80745-196">步驟1：將 [陰曆] 模組移至 [偵測器] 面板中的 [僅限空白執行時間] 位置，同時在您的基底場景階層中選取放置提示物件。</span><span class="sxs-lookup"><span data-stu-id="80745-196">Step 1: Move the lunar module to the empty Runtime Only slot in the inspector panel while the Placement Hints object is selected in your base scene hierarchy.</span></span> 
 <span data-ttu-id="80745-197">![第6課 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) 步驟2：按一下 [沒有函數] 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="80745-197">![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) Step 2: Click the No Function dropdown list.</span></span> <span data-ttu-id="80745-198">向下 TogglePlacementHints，然後選取該功能表下的 [ToggleGameObjects （）]。</span><span class="sxs-lookup"><span data-stu-id="80745-198">Go down to TogglePlacementHints and select ToggleGameObjects () under that menu.</span></span> <span data-ttu-id="80745-199">ToggleGameObjects （）會開啟和關閉放置提示，使其在每次按下按鈕時都可見或隱藏。</span><span class="sxs-lookup"><span data-stu-id="80745-199">ToggleGameObjects() toggles the placement hints on and off so that they are visible or invisible each time the button is pressed.</span></span>  
 <span data-ttu-id="80745-200">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="80745-200">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span></span>

### <a name="configuring-the-reset-button"></a><span data-ttu-id="80745-201">設定重設按鈕</span><span class="sxs-lookup"><span data-stu-id="80745-201">Configuring the Reset button</span></span>

<span data-ttu-id="80745-202">在某些情況下，使用者會犯錯誤，意外地擲回物件，或只是想要重設體驗。</span><span class="sxs-lookup"><span data-stu-id="80745-202">There will be situations where the user makes a mistake, accidently throws the object away or just wants to reset the experience.</span></span> <span data-ttu-id="80745-203">[重設] 按鈕會新增重新開機體驗的功能。</span><span class="sxs-lookup"><span data-stu-id="80745-203">The Reset button adds the ability to restart the experience.</span></span> 

<span data-ttu-id="80745-204">步驟1：選取 [重設] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="80745-204">Step 1: Select the Reset button.</span></span> <span data-ttu-id="80745-205">在基底場景中，其名稱為 ResetRoundButton。</span><span class="sxs-lookup"><span data-stu-id="80745-205">In the base scene, it’s named ResetRoundButton.</span></span> 

<span data-ttu-id="80745-206">步驟2：將 [陰曆] 模組從 [基底場景] 階層拖曳至 [偵測器] 面板上按下按鈕底下的空插槽。</span><span class="sxs-lookup"><span data-stu-id="80745-206">Step 2: Drag the lunar module from the base scene hierarchy into the empty slot under Button Pressed on the inspector panel.</span></span>
 <span data-ttu-id="80745-207">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="80745-207">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span></span>

<span data-ttu-id="80745-208">步驟3：選取 [沒有函式] 下拉式功能表，並將滑鼠停留在 [LaunchLunarModule] 上，然後選取 [resetModule （）]。</span><span class="sxs-lookup"><span data-stu-id="80745-208">Step 3: Select the No Function dropdown menu and hover over LaunchLunarModule, then select resetModule ().</span></span>

![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> <span data-ttu-id="80745-210">注意：請注意，根據預設，GameObject. BroadcastMessage 會設定為 ResetPlacement。</span><span class="sxs-lookup"><span data-stu-id="80745-210">Note: Notice that by default, the GameObject.BroadcastMessage is configured to ResetPlacement.</span></span> <span data-ttu-id="80745-211">這會為 RocketLauncher_Tutorial 的每個子物件廣播一則名為 ResetPlacement 的訊息。</span><span class="sxs-lookup"><span data-stu-id="80745-211">This broadcasts a message called ResetPlacement for every child object of the RocketLauncher_Tutorial.</span></span> <span data-ttu-id="80745-212">具有 ResetPlacement （）方法的任何物件都會藉由重設其位置來回應該訊息。</span><span class="sxs-lookup"><span data-stu-id="80745-212">Any object that has a method for ResetPlacement() responds to that message by resetting its position.</span></span> 

### <a name="launching-the-lunar-module"></a><span data-ttu-id="80745-213">啟動農曆模組</span><span class="sxs-lookup"><span data-stu-id="80745-213">Launching the lunar module</span></span>
<span data-ttu-id="80745-214">本節說明如何設定 [啟動] 按鈕，讓使用者按下按鈕，並將 [陰曆] 模組啟動到空間。</span><span class="sxs-lookup"><span data-stu-id="80745-214">This section explains how to configure the Launch button, which permits the user to press the button and launch the lunar module into space.</span></span>

<span data-ttu-id="80745-215">步驟1：選取 [啟動] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="80745-215">Step 1: Select the Launch button.</span></span> <span data-ttu-id="80745-216">在基底場景中，它稱為 LaunchRoundButton。</span><span class="sxs-lookup"><span data-stu-id="80745-216">In the base scene, it’s called LaunchRoundButton.</span></span> <span data-ttu-id="80745-217">將 [陰曆] 模組拖曳至 [偵測器] 面板中 [Touch End] 底下的空插槽。</span><span class="sxs-lookup"><span data-stu-id="80745-217">Drag the lunar module to the empty slot under Touch End in the Inspector panel.</span></span>
 <span data-ttu-id="80745-218">![第6課 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) 步驟2：選取 [沒有函式] 下拉式功能表，並將滑鼠停留在 LaunchLunarModule 上，然後選取 [StopThruster （）]。</span><span class="sxs-lookup"><span data-stu-id="80745-218">![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) Step 2: Select the No Function dropdown menu and hover over LaunchLunarModule, and select StopThruster ().</span></span> <span data-ttu-id="80745-219">這會控制使用者想要提供給陰曆模組的天生量。</span><span class="sxs-lookup"><span data-stu-id="80745-219">This controls how much thrust the user wants to give to the lunar module.</span></span> 
 <span data-ttu-id="80745-220">![第6課 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="80745-220">![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)</span></span>  
<span data-ttu-id="80745-221">步驟3：在 [ButtonPressed （）] 底下，將 [農曆] 模組（按一下、按住和拖曳）新增至空白位置。</span><span class="sxs-lookup"><span data-stu-id="80745-221">Step 3: Under ButtonPressed(), add the lunar module (click, hold, and drag) to the empty slot.</span></span> 

<span data-ttu-id="80745-222">步驟4：按一下 [沒有函式] 下拉式功能表，將滑鼠停留在 LaunchLunarModule 上，然後選取 [StartThruster （）]。</span><span class="sxs-lookup"><span data-stu-id="80745-222">Step 4: Click the No function dropdown menu, hover over LaunchLunarModule and select StartThruster ().</span></span> 
 <span data-ttu-id="80745-223">![第6課 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)</span><span class="sxs-lookup"><span data-stu-id="80745-223">![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)</span></span>  
<span data-ttu-id="80745-224">步驟5：將音樂新增至農曆模組，以便在 rocket 時播放音樂。</span><span class="sxs-lookup"><span data-stu-id="80745-224">Step 5: Add music to the lunar module so that music plays when the rocket takes off.</span></span> <span data-ttu-id="80745-225">若要這麼做，請將 [陰曆] 模組拖曳至 [按下的按鈕] 下的下一個空白插槽（）。</span><span class="sxs-lookup"><span data-stu-id="80745-225">To do this, drag the lunar module to the next empty slot under Button Pressed().</span></span>

<span data-ttu-id="80745-226">步驟6：選取 [無函式] 下拉式功能表，將滑鼠停留在 Spatialize 上，然後選取 [PlayOneShot （AudioClip）]。</span><span class="sxs-lookup"><span data-stu-id="80745-226">Step 6: Select the No Function dropdown menu, hover over AudioSource and select PlayOneShot (AudioClip).</span></span> <span data-ttu-id="80745-227">您可以自行探索包含在 MRTK 中的各種音效。</span><span class="sxs-lookup"><span data-stu-id="80745-227">Feel free to explore the variety of sounds included with the MRTK.</span></span> <span data-ttu-id="80745-228">在此範例中，我們將使用「MRTK_Gem」。</span><span class="sxs-lookup"><span data-stu-id="80745-228">In this example, we'll use "MRTK_Gem."</span></span>
 <span data-ttu-id="80745-229">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span><span class="sxs-lookup"><span data-stu-id="80745-229">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span></span>


### <a name="congratulations"></a><span data-ttu-id="80745-230">恭喜您</span><span class="sxs-lookup"><span data-stu-id="80745-230">Congratulations</span></span> 
<span data-ttu-id="80745-231">您已完全設定此應用程式。</span><span class="sxs-lookup"><span data-stu-id="80745-231">You have fully configured this application.</span></span> <span data-ttu-id="80745-232">現在，當您按下 [播放] 時，您可以完整組合陰曆模組、切換提示、啟動陰曆模組，然後將它重設為重新啟動。</span><span class="sxs-lookup"><span data-stu-id="80745-232">Now, when you press play, you can fully assemble the lunar module, toggle hints, launch the lunar module and reset it to start again.</span></span>
