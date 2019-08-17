---
title: 使用者入門教學課程-7。 建立農曆模組範例應用程式
description: 在本課程中，我們將會結合從先前課程中所學習到的多個概念，以建立獨特的範例體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: f45aa7e2f07a8a67cd56f0aae140de3a68afc918
ms.sourcegitcommit: e9a55528965048ce34f8247ef6e544f9f432ee37
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2019
ms.locfileid: "69559896"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="8ba19-105">7.建立農曆模組範例應用程式</span><span class="sxs-lookup"><span data-stu-id="8ba19-105">7. Creating a Lunar Module sample application</span></span>

<span data-ttu-id="8ba19-106">在本教學課程中, 我們結合了先前課程中所呈現的多個概念, 以建立獨特的範例體驗。</span><span class="sxs-lookup"><span data-stu-id="8ba19-106">In this tutorial, we combine multiple concepts presented in the previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="8ba19-107">我們將建立一個陰曆模組元件應用程式, 讓使用者必須使用追蹤的手來挑選陰曆模組零件, 並嘗試組合陰曆模組。</span><span class="sxs-lookup"><span data-stu-id="8ba19-107">We will create a lunar module assembly application whereby a user needs to use tracked hands to pick up lunar module parts, and attempt to assemble a lunar module.</span></span> <span data-ttu-id="8ba19-108">我們會使用 [pressable] 按鈕來切換放置提示、重設我們的體驗, 以及啟動我們的陰曆模組來進行空間!</span><span class="sxs-lookup"><span data-stu-id="8ba19-108">We use pressable buttons to toggle placement hints, to reset our experience, and to launch our lunar module into space!</span></span> <span data-ttu-id="8ba19-109">在未來的教學課程中, 我們將繼續以這項體驗為基礎, 其中包含強大的多使用者使用案例, 可運用 Azure 空間錨點來進行空間對齊。</span><span class="sxs-lookup"><span data-stu-id="8ba19-109">In future tutorials, we will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="8ba19-110">目標</span><span class="sxs-lookup"><span data-stu-id="8ba19-110">Objectives</span></span>

- <span data-ttu-id="8ba19-111">結合來自先前課程的多個概念以建立獨特體驗</span><span class="sxs-lookup"><span data-stu-id="8ba19-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
- <span data-ttu-id="8ba19-112">了解如何切換物件</span><span class="sxs-lookup"><span data-stu-id="8ba19-112">Learn how to toggle objects</span></span>
- <span data-ttu-id="8ba19-113">使用可點按的按鈕來觸發複雜事件</span><span class="sxs-lookup"><span data-stu-id="8ba19-113">Trigger complex events using pressable buttons</span></span>
- <span data-ttu-id="8ba19-114">使用 rigidbody 物理特性和力</span><span class="sxs-lookup"><span data-stu-id="8ba19-114">Use rigidbody physics and forces</span></span>
- <span data-ttu-id="8ba19-115">探索工具提示的使用</span><span class="sxs-lookup"><span data-stu-id="8ba19-115">Explore the use of tool tips</span></span>

## <a name="instructions"></a><span data-ttu-id="8ba19-116">指示</span><span class="sxs-lookup"><span data-stu-id="8ba19-116">Instructions</span></span>

### <a name="configuring-the-lunar-module"></a><span data-ttu-id="8ba19-117">設定登月小艇</span><span class="sxs-lookup"><span data-stu-id="8ba19-117">Configuring the Lunar Module</span></span>

<span data-ttu-id="8ba19-118">在本節中, 我們將介紹建立範例體驗所需的各種元件。</span><span class="sxs-lookup"><span data-stu-id="8ba19-118">In this section, we introduce the various components needed to create our sample experience.</span></span>

1. <span data-ttu-id="8ba19-119">將 [農曆模組元件] prefab 新增至您的基礎場景。</span><span class="sxs-lookup"><span data-stu-id="8ba19-119">Add the Lunar Module Assembly prefab to your base scene.</span></span> <span data-ttu-id="8ba19-120">若要這麼做, 請在 [專案] 索引標籤中搜尋 Rocket Launcher_Tutorial。</span><span class="sxs-lookup"><span data-stu-id="8ba19-120">To do this, from the Project tab, search for Rocket Launcher_Tutorial.</span></span> 
<span data-ttu-id="8ba19-121">在資產中尋找 prefab-> BaseModuleAssets-> Prefabs。</span><span class="sxs-lookup"><span data-stu-id="8ba19-121">Find the prefab in Assets->BaseModuleAssets->Prefabs.</span></span> <span data-ttu-id="8ba19-122">您也會看到兩個 rocket 啟動器 prefabs;一個名稱為 "教學課程", 另一個名稱為 "complete"。</span><span class="sxs-lookup"><span data-stu-id="8ba19-122">You'll also see two rocket launcher prefabs; one with the name "tutorial" and the other with the name "complete".</span></span> <span data-ttu-id="8ba19-123">將 [Rocket Launcher_Tutorial] prefab 拖曳至您的基礎場景, 並依您想要的位置。</span><span class="sxs-lookup"><span data-stu-id="8ba19-123">Drag the Rocket Launcher_Tutorial prefab to your base scene, and position as you wish.</span></span>
   <span data-ttu-id="8ba19-124">注意:Rocket Launcher_Complete prefab 是已完成的啟動器, 提供供參考之用。</span><span class="sxs-lookup"><span data-stu-id="8ba19-124">Note: The Rocket Launcher_Complete prefab is the completed launcher, provided for reference.</span></span> 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

<span data-ttu-id="8ba19-126">如果您在階層中展開 Rocket Launcher_Tutorial 遊戲物件, 並進一步展開 [陰曆] 模組物件, 您會發現有數個子物件具有稱為「x-光線」的材質。</span><span class="sxs-lookup"><span data-stu-id="8ba19-126">If you expand the Rocket Launcher_Tutorial game object in your hierarchy, and further expand the Lunar Module object, you find several child objects that have a material called, "x-ray."</span></span> <span data-ttu-id="8ba19-127">「X 光線」材質可提供稍微半透明的色彩, 供我們用來做為使用者的放置提示。</span><span class="sxs-lookup"><span data-stu-id="8ba19-127">The "x-ray" material allows for a slightly translucent color that we will use as placement hints for the user.</span></span> 

<span data-ttu-id="8ba19-128">![第6課 chapter1.txt Noteaim](images/Lesson6_Chapter1_noteaim.PNG)有五個部分可供使用者將與之進行互動的陰曆模組中, 如下圖所示:</span><span class="sxs-lookup"><span data-stu-id="8ba19-128">![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) There are five parts to the lunar module that the user will interact with as shown in the image below:</span></span>

1.  <span data-ttu-id="8ba19-129">月球車外殼</span><span class="sxs-lookup"><span data-stu-id="8ba19-129">The Rover Enclosure</span></span>
2.  <span data-ttu-id="8ba19-130">油箱</span><span class="sxs-lookup"><span data-stu-id="8ba19-130">The Fuel Tank</span></span>
3.  <span data-ttu-id="8ba19-131">能量電池</span><span class="sxs-lookup"><span data-stu-id="8ba19-131">The Energy Cell</span></span>
4.  <span data-ttu-id="8ba19-132">泊接座</span><span class="sxs-lookup"><span data-stu-id="8ba19-132">The Docking Portal</span></span> 
5.  <span data-ttu-id="8ba19-133">外部感應器</span><span class="sxs-lookup"><span data-stu-id="8ba19-133">The External sensor</span></span>

![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> <span data-ttu-id="8ba19-135">注意:您在基底場景階層中看到的遊戲物件名稱, 並不會對應到場景中的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="8ba19-135">Note: The Game object names that you see in your base scene hierarchy do not correspond to the names of the objects in the scene.</span></span>

<span data-ttu-id="8ba19-136">步驟 2:將音訊來源加入至登月小艇。</span><span class="sxs-lookup"><span data-stu-id="8ba19-136">Step 2: Add an audio source to the lunar module.</span></span> <span data-ttu-id="8ba19-137">請確定已在您的基底場景階層中選取 [陰曆] 模組, 然後按一下 [新增元件]。</span><span class="sxs-lookup"><span data-stu-id="8ba19-137">Make sure the lunar module is selected in your base scene hierarchy, and click Add Component.</span></span> <span data-ttu-id="8ba19-138">搜尋 [音訊來源], 並將它新增至物件。</span><span class="sxs-lookup"><span data-stu-id="8ba19-138">Search for Audio Source, and add it to the object.</span></span> <span data-ttu-id="8ba19-139">現在請將其保留為空白, 但請務必按一下 [Spatialize] 核取方塊以啟用空間音訊。</span><span class="sxs-lookup"><span data-stu-id="8ba19-139">Leave it blank for now, but make sure to click the "Spatialize" checkbox to enable spatial audio.</span></span> <span data-ttu-id="8ba19-140">我們稍後將會用它來播放發射音效。</span><span class="sxs-lookup"><span data-stu-id="8ba19-140">We will use this to play the launching sound later.</span></span>

 ![第6課 Chapter1.txt Step2im](images/Lesson6_Chapter1_step2im.PNG)  
<span data-ttu-id="8ba19-142">步驟 3：新增腳本, 切換放置提示。</span><span class="sxs-lookup"><span data-stu-id="8ba19-142">Step 3: Add the script, Toggle Placement Hints.</span></span> <span data-ttu-id="8ba19-143">按一下 [新增元件], 然後搜尋 [切換位置提示]。</span><span class="sxs-lookup"><span data-stu-id="8ba19-143">Click Add Component, and search for Toggle Placement Hints.</span></span> <span data-ttu-id="8ba19-144">這是自訂腳本, 可讓您開啟和關閉稍早所述的半透明提示 (具有 x 光線材質的物件)。</span><span class="sxs-lookup"><span data-stu-id="8ba19-144">This is a custom script that lets you turn on and off the translucent hints (objects with the x-ray material) mentioned earlier.</span></span>  
![第6課 Chapter1.txt Step3im](images/Lesson6_Chapter1_step3im.PNG)  
<span data-ttu-id="8ba19-146">步驟 4：因為我們有五個物件, 請輸入 "5" 作為遊戲物件陣列大小。</span><span class="sxs-lookup"><span data-stu-id="8ba19-146">Step 4: Since we have five objects, type in "5" for the game object array size.</span></span> <span data-ttu-id="8ba19-147">您接著會看到五個新的元素。</span><span class="sxs-lookup"><span data-stu-id="8ba19-147">You'll then see five new elements appear.</span></span>  


![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

<span data-ttu-id="8ba19-149">將每個半透明物件拖曳到所有名稱 (遊戲物件) 方塊中。</span><span class="sxs-lookup"><span data-stu-id="8ba19-149">Drag each of the translucent objects into all the Name (Game Obect) boxes.</span></span>
<span data-ttu-id="8ba19-150">將下列物件從登月小艇拖曳到基底場景中：</span><span class="sxs-lookup"><span data-stu-id="8ba19-150">Drag the following objects from the lunar module in your base scene:</span></span> 

<span data-ttu-id="8ba19-151">•   Backpack</span><span class="sxs-lookup"><span data-stu-id="8ba19-151">•   Backpack</span></span>

<span data-ttu-id="8ba19-152">•   GasTank</span><span class="sxs-lookup"><span data-stu-id="8ba19-152">•   GasTank</span></span>

<span data-ttu-id="8ba19-153">•   Topleftbody</span><span class="sxs-lookup"><span data-stu-id="8ba19-153">•   Topleftbody</span></span>

<span data-ttu-id="8ba19-154">•   Nose</span><span class="sxs-lookup"><span data-stu-id="8ba19-154">•   Nose</span></span>

<span data-ttu-id="8ba19-155">•   LeftTwirler</span><span class="sxs-lookup"><span data-stu-id="8ba19-155">•   LeftTwirler</span></span>

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

<span data-ttu-id="8ba19-157">現在已設定切換位置提示腳本。</span><span class="sxs-lookup"><span data-stu-id="8ba19-157">Now the Toggle Placement Hints script is configured.</span></span> <span data-ttu-id="8ba19-158">這可讓我們開啟和關閉提示。</span><span class="sxs-lookup"><span data-stu-id="8ba19-158">This allow us to turn hints on and off.</span></span>

<span data-ttu-id="8ba19-159">步驟 5：新增 [啟動陰曆模組] 腳本。</span><span class="sxs-lookup"><span data-stu-id="8ba19-159">Step 5: Add the Launch Lunar Module script.</span></span> <span data-ttu-id="8ba19-160">按一下 [新增元件] 按鈕, 搜尋「啟動陰曆模組」, 然後選取它。</span><span class="sxs-lookup"><span data-stu-id="8ba19-160">Click the Add Component button, search for "launch lunar module", and select it.</span></span> <span data-ttu-id="8ba19-161">此腳本會啟動農曆模組。</span><span class="sxs-lookup"><span data-stu-id="8ba19-161">This script launches the lunar module.</span></span> <span data-ttu-id="8ba19-162">當我們按下已設定的按鈕時, 它會將向上強制新增至農曆模組的固定主體元件, 並使模組向上啟動。</span><span class="sxs-lookup"><span data-stu-id="8ba19-162">When we press a configured button, it adds an upward force to the lunar module's rigid body component, and causes the module to launch upwards.</span></span> <span data-ttu-id="8ba19-163">如果您位於室內，登月小艇可能會撞擊您的天花板網格。</span><span class="sxs-lookup"><span data-stu-id="8ba19-163">If you are indoors, the lunar module may crash against your ceiling mesh.</span></span> <span data-ttu-id="8ba19-164">但如果您位於室外，它將會無限制地飛向太空。</span><span class="sxs-lookup"><span data-stu-id="8ba19-164">But if you are outdoors, it will fly in to space indefinitely.</span></span> 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

<span data-ttu-id="8ba19-166">步驟 6：調整推力來使登月小艇能優雅地向上升起。</span><span class="sxs-lookup"><span data-stu-id="8ba19-166">Step 6: Adjust the thrust so that the lunar module will fly up gracefully.</span></span> <span data-ttu-id="8ba19-167">試試使用 0.01 的值。</span><span class="sxs-lookup"><span data-stu-id="8ba19-167">Try a value of 0.01.</span></span> <span data-ttu-id="8ba19-168">將 [Rb] 欄位保留空白。</span><span class="sxs-lookup"><span data-stu-id="8ba19-168">Leave the "Rb" field blank.</span></span> <span data-ttu-id="8ba19-169">Rb 代表 rigidbody，因此系統將會在執行階段自動填入此欄位。</span><span class="sxs-lookup"><span data-stu-id="8ba19-169">Rb stands for rigid body, and this field will be automatically populated during runtime.</span></span>

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a><span data-ttu-id="8ba19-171">陰曆模組元件總覽</span><span class="sxs-lookup"><span data-stu-id="8ba19-171">Lunar Module Parts overview</span></span>
<span data-ttu-id="8ba19-172">陰曆模組元件父物件是使用者與之互動物件的集合。</span><span class="sxs-lookup"><span data-stu-id="8ba19-172">The Lunar Module Parts parent object is the collection of the objects that the user interacts with.</span></span> <span data-ttu-id="8ba19-173">下列清單提供遊戲物件名稱, 加上標記為 paretheses 的場景名稱:</span><span class="sxs-lookup"><span data-stu-id="8ba19-173">The Game object names, with scene labeled names in paretheses, are provided in the list below:</span></span>

- <span data-ttu-id="8ba19-174">Backpack (Fuel Tank)</span><span class="sxs-lookup"><span data-stu-id="8ba19-174">Backpack (Fuel Tank)</span></span>
- <span data-ttu-id="8ba19-175">GasTank (Energy Cell)</span><span class="sxs-lookup"><span data-stu-id="8ba19-175">GasTank (Energy Cell)</span></span>
- <span data-ttu-id="8ba19-176">TopLeftBody (Rover Enclosure)</span><span class="sxs-lookup"><span data-stu-id="8ba19-176">TopLeftBody (Rover Enclosure)</span></span>
- <span data-ttu-id="8ba19-177">Nose (Docking Portal)</span><span class="sxs-lookup"><span data-stu-id="8ba19-177">Nose (Docking Portal)</span></span>
- <span data-ttu-id="8ba19-178">LeftTwirler (External Sensor)</span><span class="sxs-lookup"><span data-stu-id="8ba19-178">LeftTwirler (External Sensor)</span></span>

<span data-ttu-id="8ba19-179">請注意, 每個物件都有操作處理常式, 如第4課所述。</span><span class="sxs-lookup"><span data-stu-id="8ba19-179">Notice that each of these objects has a manipulation handler as discussed in Lesson 4.</span></span> <span data-ttu-id="8ba19-180">使用者可以使用操作處理常式來抓取和操作物件。</span><span class="sxs-lookup"><span data-stu-id="8ba19-180">With the manipulation handler, users can grab and manipulate the object.</span></span> <span data-ttu-id="8ba19-181">另請注意, 設定 [雙向操作類型] 設定為 [移動並旋轉]。</span><span class="sxs-lookup"><span data-stu-id="8ba19-181">Also note that the setting, Two Handed Manipulation Type is set to Move and Rotate.</span></span> <span data-ttu-id="8ba19-182">這僅會允許使用者移動物件，而不會讓他們變更其大小；此為組成應用程式的所需功能。</span><span class="sxs-lookup"><span data-stu-id="8ba19-182">This only permits the user to move the object and not change its size, which is the desired functionality for an assembly application.</span></span>
<span data-ttu-id="8ba19-183">此外, 會取消選取 [目前的操作], 只允許模組元件的直接互動。</span><span class="sxs-lookup"><span data-stu-id="8ba19-183">In addition, Far Manipulation is unchecked to allow only for direct interaction of module parts.</span></span>

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

<span data-ttu-id="8ba19-185">部分元件示範腳本 (如上所示) 是用來管理使用者在陰曆模組上由使用者放置之物件的腳本。</span><span class="sxs-lookup"><span data-stu-id="8ba19-185">The Part Assembly Demo script (shown above) is the script that manages the objects that the user places on the lunar module by the user.</span></span> 

<span data-ttu-id="8ba19-186">[要放置的物件] 欄位是已選取的轉換, 如上圖所示, 與所連接之物件相關聯的死忠/燃料箱。</span><span class="sxs-lookup"><span data-stu-id="8ba19-186">The Object To Place field is the transform that is selected, as shown in the image above, the backpack/fuel tank associated with the object that it connects to.</span></span> 

<span data-ttu-id="8ba19-187">[近乎距離] 和 [距離距離] 設定會決定要放置或釋放的部分。</span><span class="sxs-lookup"><span data-stu-id="8ba19-187">The Near Distance and Far Distance settings determine the proximity to which parts snap in place or can be released.</span></span> <span data-ttu-id="8ba19-188">例如, 死忠/燃料箱必須是0.1 單位, 而不是陰曆模組, 才會貼齊位置。</span><span class="sxs-lookup"><span data-stu-id="8ba19-188">For example, the backpack/fuel tank needs to be 0.1 units away from the lunar module before it will snap into place.</span></span> <span data-ttu-id="8ba19-189">[最遠距離] 設定會設定物件可以從農曆模組卸離之前的位置。</span><span class="sxs-lookup"><span data-stu-id="8ba19-189">The Far Distance setting sets the location where the object can be before it can detach from the lunar module.</span></span> <span data-ttu-id="8ba19-190">在此情況下，使用者的手必須抓住 backpack/fuel tank，並將它拖曳至距離登月小艇 0.2 單位的距離，才能將它從原本的定位移除。</span><span class="sxs-lookup"><span data-stu-id="8ba19-190">In this case, the user’s hand must grab the backpack/fuel tank and pull it 0.2 units away from the lunar module to remove it from snapping back into place.</span></span>

<span data-ttu-id="8ba19-191">工具提示物件是場景中的工具提示標籤。</span><span class="sxs-lookup"><span data-stu-id="8ba19-191">The Tool Tip Object is the tool tip label in the scene.</span></span> <span data-ttu-id="8ba19-192">當物件準備就緒時, 會停用標籤。</span><span class="sxs-lookup"><span data-stu-id="8ba19-192">When the objects are snapped in place, the label is disabled.</span></span> 

<span data-ttu-id="8ba19-193">音訊來源會自動抓取。</span><span class="sxs-lookup"><span data-stu-id="8ba19-193">The Audio Source is automatically grabbed.</span></span> 

### <a name="placement-hints-buttons"></a><span data-ttu-id="8ba19-194">放置提示按鈕</span><span class="sxs-lookup"><span data-stu-id="8ba19-194">Placement Hints buttons</span></span>
<span data-ttu-id="8ba19-195">在[第 2 課](mrlearning-base-ch2.md)中，您已了解如何放置按鈕並設定它以變更項目色彩，或是在按下時播放音效等功能。</span><span class="sxs-lookup"><span data-stu-id="8ba19-195">In [Lesson 2](mrlearning-base-ch2.md), you learned how to place and configure buttons to do things like change the color of an item or make it play a sound when it is pushed.</span></span> <span data-ttu-id="8ba19-196">我們將會繼續使用那些原則來設定按鈕以切換放置提示。</span><span class="sxs-lookup"><span data-stu-id="8ba19-196">We will continue to use those principles as we configure our buttons for toggling placement hints.</span></span> 

<span data-ttu-id="8ba19-197">其目標是設定按鈕, 讓每次使用者按下 [放置提示] 按鈕時, 都會切換半透明放置提示的可見度。</span><span class="sxs-lookup"><span data-stu-id="8ba19-197">The goal is to configure our button so that every time the user presses the Placement hint button, it toggles the visibility of the translucent placement hints.</span></span> 

<span data-ttu-id="8ba19-198">步驟 1:將 [陰曆] 模組移至 [偵測器] 面板中的 [僅限空白執行時間] 插槽, 同時在您的基底場景階層中選取放置提示物件。</span><span class="sxs-lookup"><span data-stu-id="8ba19-198">Step 1: Move the lunar module to the empty Runtime Only slot in the inspector panel while the Placement Hints object is selected in your base scene hierarchy.</span></span> 
 <span data-ttu-id="8ba19-199">![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) 步驟 2：現在, 按一下 [沒有函數] 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="8ba19-199">![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) Step 2: Now click the No Function dropdown list.</span></span> <span data-ttu-id="8ba19-200">移至 [TogglePlacementHints], 然後在該功能表下選取 [ToggleGameObjects ()]。</span><span class="sxs-lookup"><span data-stu-id="8ba19-200">Go down to TogglePlacementHints, and under that menu select ToggleGameObjects ().</span></span> <span data-ttu-id="8ba19-201">ToggleGameObjects () 會開啟和關閉放置提示, 使其在每次按下按鈕時都可見或隱藏。</span><span class="sxs-lookup"><span data-stu-id="8ba19-201">ToggleGameObjects() toggles the placement hints on and off so that they are visible or invisible each time the button is pressed.</span></span>  
 <span data-ttu-id="8ba19-202">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="8ba19-202">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span></span>

### <a name="configuring-the-reset-button"></a><span data-ttu-id="8ba19-203">設定重設按鈕</span><span class="sxs-lookup"><span data-stu-id="8ba19-203">Configuring the Reset button</span></span>

<span data-ttu-id="8ba19-204">在某些情況下, 使用者會犯錯誤, 或意外地擲回物件, 或只是想要重設體驗。</span><span class="sxs-lookup"><span data-stu-id="8ba19-204">There will be situations where the user makes a mistake, or accidently throws the object away, or just wants to reset the experience.</span></span> <span data-ttu-id="8ba19-205">[重設] 按鈕會新增重新開機體驗的功能。</span><span class="sxs-lookup"><span data-stu-id="8ba19-205">The Reset button adds the ability to restart the experience.</span></span> 

<span data-ttu-id="8ba19-206">步驟 1:選取 [重設] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="8ba19-206">Step 1: Select the Reset button.</span></span> <span data-ttu-id="8ba19-207">在基底場景中, 其名稱為 ResetRoundButton。</span><span class="sxs-lookup"><span data-stu-id="8ba19-207">In the base scene, it’s named, ResetRoundButton.</span></span> 

<span data-ttu-id="8ba19-208">步驟 2:將 [陰曆] 模組從 [基底場景] 階層拖曳至 [按鈕] 底下的空白插槽中, 按下 [檢查] 面板</span><span class="sxs-lookup"><span data-stu-id="8ba19-208">Step 2: Drag the lunar module from the base scene hierarchy into the empty slot under Button Pressed the inspector panel.</span></span>
 <span data-ttu-id="8ba19-209">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="8ba19-209">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span></span>

<span data-ttu-id="8ba19-210">步驟 3：選取 [沒有函式] 下拉式功能表, 並將滑鼠停留在 [LaunchLunarModule] 上, 選取 [resetModule ()]。</span><span class="sxs-lookup"><span data-stu-id="8ba19-210">Step 3: Select the No Function dropdown menu, and hover over LaunchLunarModule,  select resetModule ().</span></span>

![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> <span data-ttu-id="8ba19-212">注意:請注意, 根據預設, GameObject. BroadcastMessage 會設定為 ResetPlacement。</span><span class="sxs-lookup"><span data-stu-id="8ba19-212">Note: Notice that by default, the GameObject.BroadcastMessage is configured to ResetPlacement.</span></span> <span data-ttu-id="8ba19-213">這會針對 RocketLauncher_Tutorial 的每個子物件廣播名為 ResetPlacement 的訊息。</span><span class="sxs-lookup"><span data-stu-id="8ba19-213">This broadcasts a message called, ResetPlacement for every child object of the RocketLauncher_Tutorial.</span></span> <span data-ttu-id="8ba19-214">具有 ResetPlacement () 方法的任何物件, 都會藉由重設其位置來回應該訊息。</span><span class="sxs-lookup"><span data-stu-id="8ba19-214">Any object that has a method for ResetPlacement() responds to that message by resetting it's position.</span></span> 

### <a name="launching-the-lunar-module"></a><span data-ttu-id="8ba19-215">啟動農曆模組</span><span class="sxs-lookup"><span data-stu-id="8ba19-215">Launching the lunar module</span></span>
<span data-ttu-id="8ba19-216">本節 explaings 如何設定 [啟動] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="8ba19-216">This section explaings how to configure the Launch button.</span></span> <span data-ttu-id="8ba19-217">這可讓使用者按下按鈕, 並將陰曆模組啟動到空間。</span><span class="sxs-lookup"><span data-stu-id="8ba19-217">This permits the user to press the button and launch the lunar module into space.</span></span>

<span data-ttu-id="8ba19-218">步驟 1:選取 [啟動] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="8ba19-218">Step 1: Select the Launch button.</span></span> <span data-ttu-id="8ba19-219">在基底場景中, 其名為 LaunchRoundButton。</span><span class="sxs-lookup"><span data-stu-id="8ba19-219">In the base scene it’s called, LaunchRoundButton.</span></span> <span data-ttu-id="8ba19-220">將 [陰曆] 模組拖曳至 [偵測器] 面板中 [Touch End] 底下的空插槽。</span><span class="sxs-lookup"><span data-stu-id="8ba19-220">Drag the lunar module to the empty slot under Touch End in the Inspector panel.</span></span>
 <span data-ttu-id="8ba19-221">![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) 步驟 2：選取 [沒有函式] 下拉式功能表, 將滑鼠停留在 [LaunchLunarModule] 上, 然後選取 [StopThruster ()]。</span><span class="sxs-lookup"><span data-stu-id="8ba19-221">![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) Step 2: Select the No Function dropdown menu, and hover over LaunchLunarModule, and select StopThruster ().</span></span> <span data-ttu-id="8ba19-222">這會控制使用者想要提供給陰曆模組的天生量。</span><span class="sxs-lookup"><span data-stu-id="8ba19-222">This controls how much thrust the user wants to give to the lunar module.</span></span> 
 <span data-ttu-id="8ba19-223">![第6課 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="8ba19-223">![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)</span></span>  
<span data-ttu-id="8ba19-224">步驟 3：在 [ButtonPressed ()] 底下, 將 [農曆] 模組 (按一下、按住和拖曳) 新增至空白位置。</span><span class="sxs-lookup"><span data-stu-id="8ba19-224">Step 3: Under ButtonPressed(), add the lunar module (click, hold, and drag) to the empty slot.</span></span> 

<span data-ttu-id="8ba19-225">步驟 4：按一下 [沒有函式] 下拉式功能表, 將滑鼠停留在 [LaunchLunarModule] 上, 然後選取 [StartThruster ()]。</span><span class="sxs-lookup"><span data-stu-id="8ba19-225">Step 4: Click the No function dropdown menu, and hover over LaunchLunarModule, and select StartThruster ().</span></span> 
 <span data-ttu-id="8ba19-226">![第6課 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)</span><span class="sxs-lookup"><span data-stu-id="8ba19-226">![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)</span></span>  
<span data-ttu-id="8ba19-227">步驟 5：將音樂新增至農曆模組, 以便在 rocket 時播放音樂。</span><span class="sxs-lookup"><span data-stu-id="8ba19-227">Step 5: Add music to the lunar module so that music plays when the rocket takes off.</span></span> <span data-ttu-id="8ba19-228">若要這麼做, 請將 [陰曆] 模組拖曳至 [按下的按鈕] 下的下一個空白插槽 ()。</span><span class="sxs-lookup"><span data-stu-id="8ba19-228">To do this, drag the lunar module to the next empty slot under Button Pressed().</span></span>

<span data-ttu-id="8ba19-229">步驟 6：選取 [沒有函式] 下拉式功能表, 將滑鼠停留在 [Spatialize] 上, 然後選取 [PlayOneShot (AudioClip)]。</span><span class="sxs-lookup"><span data-stu-id="8ba19-229">Step 6: Select the No Function dropdown menu, hover over AudioSource, and select PlayOneShot (AudioClip).</span></span> <span data-ttu-id="8ba19-230">您可以自行探索包含在 MRTK 中的各種音效。</span><span class="sxs-lookup"><span data-stu-id="8ba19-230">Feel free to explore the variety of sounds included with the MRTK.</span></span> <span data-ttu-id="8ba19-231">在此範例中, 我們將使用 "MRTK_Gem"。</span><span class="sxs-lookup"><span data-stu-id="8ba19-231">For this example, we'll use "MRTK_Gem."</span></span>
 <span data-ttu-id="8ba19-232">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span><span class="sxs-lookup"><span data-stu-id="8ba19-232">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span></span>


### <a name="congratulations"></a><span data-ttu-id="8ba19-233">恭喜！</span><span class="sxs-lookup"><span data-stu-id="8ba19-233">Congratulations</span></span> 
<span data-ttu-id="8ba19-234">您已完全設定此應用程式。</span><span class="sxs-lookup"><span data-stu-id="8ba19-234">You have fully configured this application.</span></span> <span data-ttu-id="8ba19-235">現在, 當您按下 [播放] 時, 您可以完整組合陰曆模組、切換提示、啟動陰曆模組, 然後重設為重新開始。</span><span class="sxs-lookup"><span data-stu-id="8ba19-235">Now, when you press play, you can fully assemble the lunar module, toggle hints, launch the lunar module, and reset it to start all over again.</span></span>
