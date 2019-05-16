---
title: MR 學習基底模組-農曆模組組件範例體驗
description: 在這一課中，我們會結合多個從先前的課程，以建立唯一的範例經驗學到的概念。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合的實境，unity 教學課程 hololens
ms.openlocfilehash: 8a2f388e842d521f991203916177e3dac15769eb
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730851"
---
# <a name="mr-learning-base-module---lunar-module-assembly-sample-experience"></a><span data-ttu-id="000a1-104">MR 學習基底模組-農曆模組組件範例體驗</span><span class="sxs-lookup"><span data-stu-id="000a1-104">MR Learning Base Module - Lunar Module Assembly Sample Experience</span></span>

<span data-ttu-id="000a1-105">在這一課中，我們會結合多個從先前的課程，以建立唯一的範例經驗學到的概念。</span><span class="sxs-lookup"><span data-stu-id="000a1-105">In this lesson, we will combine multiple concepts learned from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="000a1-106">我們將建立農曆模組組件的應用程式，因此使用者必須使用追蹤的手拿起農曆模組組件，並嘗試組合農曆模組。</span><span class="sxs-lookup"><span data-stu-id="000a1-106">We will create a lunar module assembly application whereby a user will need to use tracked hands to pick up lunar module parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="000a1-107">我們將使用 pressable 按鈕來切換位置提示，重設我們的經驗，並在啟動我們農曆模組到空間 ！</span><span class="sxs-lookup"><span data-stu-id="000a1-107">We will use pressable buttons to toggle placement hints, to reset our experience, and to launch our lunar module into space!</span></span> <span data-ttu-id="000a1-108">在未來教學課程中，我們會繼續這項體驗，包括功能強大多使用者的使用案例，利用 Azure 空間的錨點 」 來提供空間的對齊方式為基礎。</span><span class="sxs-lookup"><span data-stu-id="000a1-108">In future tutorials, we will continue to build upon this experience, including powerful multi-user use-cases that leverages Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="000a1-109">目標</span><span class="sxs-lookup"><span data-stu-id="000a1-109">Objectives</span></span>

- <span data-ttu-id="000a1-110">結合多個概念，從先前的課程，以創造獨特體驗</span><span class="sxs-lookup"><span data-stu-id="000a1-110">Combine multiple concepts from previous lessons to create a unique experience</span></span>
- <span data-ttu-id="000a1-111">了解如何切換物件</span><span class="sxs-lookup"><span data-stu-id="000a1-111">Learn how to toggle objects</span></span>
- <span data-ttu-id="000a1-112">觸發程序的複雜事件使用 pressable 按鈕</span><span class="sxs-lookup"><span data-stu-id="000a1-112">Trigger complex events using pressable buttons</span></span>
- <span data-ttu-id="000a1-113">使用 rigidbody 物理和強制</span><span class="sxs-lookup"><span data-stu-id="000a1-113">Use rigidbody physics and forces</span></span>
- <span data-ttu-id="000a1-114">探索如何使用工具提示</span><span class="sxs-lookup"><span data-stu-id="000a1-114">Explore the use of tool tips</span></span>

## <a name="instructions"></a><span data-ttu-id="000a1-115">指示</span><span class="sxs-lookup"><span data-stu-id="000a1-115">Instructions</span></span>

### <a name="configuring-the-lunar-module"></a><span data-ttu-id="000a1-116">設定農曆模組</span><span class="sxs-lookup"><span data-stu-id="000a1-116">Configuring the Lunar Module</span></span>

<span data-ttu-id="000a1-117">在本章中，我們將介紹建立我們的範例體驗所需的各種元件。</span><span class="sxs-lookup"><span data-stu-id="000a1-117">In this chapter, we will be introduced to the various components needed to create our sample experience.</span></span>

1. <span data-ttu-id="000a1-118">加入基底場景農曆模組組件 prefab。</span><span class="sxs-lookup"><span data-stu-id="000a1-118">Add the lunar module assembly prefab to your Base Scene.</span></span> <span data-ttu-id="000a1-119">若要這樣做，請在您的專案 索引標籤中，搜尋"Rocket Launcher_Tutorial。 」</span><span class="sxs-lookup"><span data-stu-id="000a1-119">To do this, in your project tab, search for "Rocket Launcher_Tutorial."</span></span> <span data-ttu-id="000a1-120">您也可能會在資產中發現 prefab > BaseModuleAssets > Prefabs。</span><span class="sxs-lookup"><span data-stu-id="000a1-120">You may also find the prefab in Assets>BaseModuleAssets>Prefabs.</span></span> <span data-ttu-id="000a1-121">您可能會看到兩個 rocket 啟動器 prefabs;一個具有名稱為 「 教學課程 」，另一個名稱 「 完成 」。</span><span class="sxs-lookup"><span data-stu-id="000a1-121">You may see two rocket launcher prefabs; one with the name "tutorial" and another with the name "complete."</span></span> <span data-ttu-id="000a1-122">將"Rocket Launcher_Tutorial"prefab 拖曳至基底場景。</span><span class="sxs-lookup"><span data-stu-id="000a1-122">Drag the "Rocket Launcher_Tutorial" prefab to your Base Scene.</span></span> <span data-ttu-id="000a1-123">請隨意放置在場景中 prefab 的位置。</span><span class="sxs-lookup"><span data-stu-id="000a1-123">Feel free to position the placement of the prefab in your scene.</span></span>
   <span data-ttu-id="000a1-124">注意："Rocket Launcher_Complete"prefab 是已完成的啟動器，供參考。</span><span class="sxs-lookup"><span data-stu-id="000a1-124">Note: The "Rocket Launcher_Complete" prefab is the completed launcher, provided for reference.</span></span> 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

<span data-ttu-id="000a1-126">如果您在您階層中，展開 「 Rocket Launcher_Tutorial 」 遊戲物件，並進一步展開 「 農曆模組 」 物件，您會看到數個子物件的材質，稱為 「 雷射。 」</span><span class="sxs-lookup"><span data-stu-id="000a1-126">If you expand the "Rocket Launcher_Tutorial" game object in your hierarchy, and further expand the "Lunar Module" object, you will see several child objects that have a material called "x-ray."</span></span> <span data-ttu-id="000a1-127">"X 光 」 資料可讓您，我們將使用作為放置提示使用者的稍有半透明色彩。</span><span class="sxs-lookup"><span data-stu-id="000a1-127">The "x-ray" material allows for a slightly translucent color which we will use as placement hints for the user.</span></span> 

<span data-ttu-id="000a1-128">![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG)有五個部分農曆模組使用者即將進行互動，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="000a1-128">![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) There are five parts to the lunar module that the user is going to interact with, as shown in the image below:</span></span>

1.  <span data-ttu-id="000a1-129">Rover 機箱</span><span class="sxs-lookup"><span data-stu-id="000a1-129">The Rover Enclosure</span></span>
2.  <span data-ttu-id="000a1-130">油箱</span><span class="sxs-lookup"><span data-stu-id="000a1-130">The Fuel Tank</span></span>
3.  <span data-ttu-id="000a1-131">能源儲存格</span><span class="sxs-lookup"><span data-stu-id="000a1-131">The Energy Cell</span></span>
4.  <span data-ttu-id="000a1-132">停駐的入口網站</span><span class="sxs-lookup"><span data-stu-id="000a1-132">The Docking Portal</span></span> 
5.  <span data-ttu-id="000a1-133">外部感應器</span><span class="sxs-lookup"><span data-stu-id="000a1-133">The External sensor</span></span>

![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> <span data-ttu-id="000a1-135">注意：您會看到您的基底的場景階層中的遊戲的物件名稱未對應到場景中物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="000a1-135">Note: The game object names that you see in your base scene hierarchy do not correspond to the names of the objects in the scene.</span></span>

<span data-ttu-id="000a1-136">步驟 2：將音訊來源加入農曆模組。</span><span class="sxs-lookup"><span data-stu-id="000a1-136">Step 2: Add an audio source to the lunar module.</span></span> <span data-ttu-id="000a1-137">請確定選取農曆模組基底的場景階層中，然後按一下 [新增元件]。</span><span class="sxs-lookup"><span data-stu-id="000a1-137">Make sure the lunar module is selected in your base scene hierarchy and click "Add Component."</span></span> <span data-ttu-id="000a1-138">搜尋 「 音訊來源 」，並將它新增至物件。</span><span class="sxs-lookup"><span data-stu-id="000a1-138">Search for "Audio Source" and add it to the object.</span></span> <span data-ttu-id="000a1-139">保留空白目前。</span><span class="sxs-lookup"><span data-stu-id="000a1-139">Leave it blank for now.</span></span> <span data-ttu-id="000a1-140">我們將使用此稍後播放啟動聲音。</span><span class="sxs-lookup"><span data-stu-id="000a1-140">We will use this to play the launching sound later.</span></span>
 <span data-ttu-id="000a1-141">![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG)步驟 3:新增指令碼 「 切換位置提示 」。</span><span class="sxs-lookup"><span data-stu-id="000a1-141">![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG) Step 3: Add the script "toggle placement hints."</span></span> <span data-ttu-id="000a1-142">按一下 [新增元件]，並搜尋 「 切換位置提示 」。</span><span class="sxs-lookup"><span data-stu-id="000a1-142">Click "Add Component" and search for "Toggle Placement Hints."</span></span> <span data-ttu-id="000a1-143">這是自訂的指令碼，可讓您開啟和關閉半透明提示 （x 光資料的物件） 先前所述。</span><span class="sxs-lookup"><span data-stu-id="000a1-143">This is a custom script that allows you to turn on and off the translucent hints (objects with the x-ray material) mentioned earlier.</span></span> 
<span data-ttu-id="000a1-144">![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG)步驟 4:由於我們有 5 個物件時，輸入"5"的遊戲物件的陣列大小。</span><span class="sxs-lookup"><span data-stu-id="000a1-144">![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG) Step 4: Since we have 5 objects, type in "5" for the game object array size.</span></span> <span data-ttu-id="000a1-145">然後您應該會看到出現的 5 個新項目。</span><span class="sxs-lookup"><span data-stu-id="000a1-145">Then you should see 5 new elements appear.</span></span> 

![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

<span data-ttu-id="000a1-147">每個的半透明物件拖曳至適當的方塊，說出 「 無 （遊戲物件）。 」</span><span class="sxs-lookup"><span data-stu-id="000a1-147">Drag each of the translucent objects into the boxes that say "None (Game Object)."</span></span> <span data-ttu-id="000a1-148">拖曳農曆模組基底場景中的下列物件：</span><span class="sxs-lookup"><span data-stu-id="000a1-148">Drag the following objects from the lunar module in your base scene:</span></span> 

<span data-ttu-id="000a1-149">• 背包</span><span class="sxs-lookup"><span data-stu-id="000a1-149">•   Backpack</span></span>

<span data-ttu-id="000a1-150">• GasTank</span><span class="sxs-lookup"><span data-stu-id="000a1-150">•   GasTank</span></span>

<span data-ttu-id="000a1-151">• Topleftbody</span><span class="sxs-lookup"><span data-stu-id="000a1-151">•   Topleftbody</span></span>

<span data-ttu-id="000a1-152">• 鼻子</span><span class="sxs-lookup"><span data-stu-id="000a1-152">•   Nose</span></span>

<span data-ttu-id="000a1-153">•   LeftTwirler</span><span class="sxs-lookup"><span data-stu-id="000a1-153">•   LeftTwirler</span></span>

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

<span data-ttu-id="000a1-155">現在已設定 「 切換位置提示"指令碼。</span><span class="sxs-lookup"><span data-stu-id="000a1-155">Now the "toggle placement hints" script is configured.</span></span> <span data-ttu-id="000a1-156">這可讓我們開啟和關閉的提示。</span><span class="sxs-lookup"><span data-stu-id="000a1-156">This will allow us to turn the hints on and off.</span></span>

<span data-ttu-id="000a1-157">步驟 5：新增 「 啟動農曆模組 」 的指令碼。</span><span class="sxs-lookup"><span data-stu-id="000a1-157">Step 5: Add the "launch lunar module" script.</span></span> <span data-ttu-id="000a1-158">按一下 [新增元件] 按鈕，搜尋 「 啟動農曆模組 」，並加以選取。</span><span class="sxs-lookup"><span data-stu-id="000a1-158">Click the "Add Component" button, search for "launch lunar module" and select it.</span></span> <span data-ttu-id="000a1-159">此指令碼會負責啟動農曆模組。</span><span class="sxs-lookup"><span data-stu-id="000a1-159">This script will be responsible for launching the lunar module.</span></span> <span data-ttu-id="000a1-160">當我們按下 [設定] 按鈕時，它會將向上強制農曆模組的固定的主體元件，並會往上啟動模組。</span><span class="sxs-lookup"><span data-stu-id="000a1-160">When we press a configured button, it will add an upward force to the lunar module's rigid body component and will cause the module to launch upwards.</span></span> <span data-ttu-id="000a1-161">如果您是室內，農曆模組可能會針對最高限度網格損毀。</span><span class="sxs-lookup"><span data-stu-id="000a1-161">If you are indoors, the lunar module may crash against your ceiling mesh.</span></span> <span data-ttu-id="000a1-162">但是，如果您是戶外活動，它會飛抵中空間無限期。</span><span class="sxs-lookup"><span data-stu-id="000a1-162">But if you are outdoors, it will fly in to space indefinitely.</span></span> 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

<span data-ttu-id="000a1-164">步驟 6：調整主要目的是讓農曆模組會依正常程序的飛出。</span><span class="sxs-lookup"><span data-stu-id="000a1-164">Step 6: Adjust the thrust so that the lunar module will fly up gracefully.</span></span> <span data-ttu-id="000a1-165">請試著 0.01 的值。</span><span class="sxs-lookup"><span data-stu-id="000a1-165">Try a value of 0.01.</span></span> <span data-ttu-id="000a1-166">將 「 Rb"欄位保留空白。</span><span class="sxs-lookup"><span data-stu-id="000a1-166">Leave the "Rb" field blank.</span></span> <span data-ttu-id="000a1-167">Rb 代表固定的內文，並在執行階段會自動填入這個欄位。</span><span class="sxs-lookup"><span data-stu-id="000a1-167">Rb stands for rigid body, and this field will be automatically populated during runtime.</span></span>

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a><span data-ttu-id="000a1-169">農曆模組組件概觀</span><span class="sxs-lookup"><span data-stu-id="000a1-169">Lunar Module Parts Overview</span></span>
<span data-ttu-id="000a1-170">農曆模組組件的父物件是使用者互動的物件集合。</span><span class="sxs-lookup"><span data-stu-id="000a1-170">The Lunar Module parts parent object is the collection of the objects that the user will interact with.</span></span> <span data-ttu-id="000a1-171">下列清單提供遊戲的物件名稱 （使用場景標示為 paretheses 中的名稱）：</span><span class="sxs-lookup"><span data-stu-id="000a1-171">The game object names (with scene labeled names in paretheses) are provided in the list below:</span></span>

- <span data-ttu-id="000a1-172">背包 （油箱）</span><span class="sxs-lookup"><span data-stu-id="000a1-172">Backpack (Fuel Tank)</span></span>
- <span data-ttu-id="000a1-173">GasTank （能源儲存格）</span><span class="sxs-lookup"><span data-stu-id="000a1-173">GasTank (Energy Cell)</span></span>
- <span data-ttu-id="000a1-174">TopLeftBody （Rover 機箱）</span><span class="sxs-lookup"><span data-stu-id="000a1-174">TopLeftBody (Rover Enclosure)</span></span>
- <span data-ttu-id="000a1-175">鼻子 （停駐的入口網站）</span><span class="sxs-lookup"><span data-stu-id="000a1-175">Nose (Docking Portal)</span></span>
- <span data-ttu-id="000a1-176">LeftTwirler （外部感應器）</span><span class="sxs-lookup"><span data-stu-id="000a1-176">LeftTwirler (External Sensor)</span></span>

<span data-ttu-id="000a1-177">請注意，每個物件會有操作處理常式中，第 4 課中所述。</span><span class="sxs-lookup"><span data-stu-id="000a1-177">Notice that each of these objects has the manipulation handler, as discussed in lesson 4.</span></span> <span data-ttu-id="000a1-178">使用操作處理常式中，使用者可擷取及管理的物件。</span><span class="sxs-lookup"><span data-stu-id="000a1-178">With the manipulation handler, users are able to grab and manipulate the object.</span></span> <span data-ttu-id="000a1-179">也請注意，「 兩個右手的操作類型 」 設定為 「 移動和旋轉 」。</span><span class="sxs-lookup"><span data-stu-id="000a1-179">Also note that the setting "two handed manipulation type" is set to "move and rotate."</span></span> <span data-ttu-id="000a1-180">這只允許使用者移動物件，並不會變更其大小，也就是組件應用程式所需的功能。</span><span class="sxs-lookup"><span data-stu-id="000a1-180">This only permits the user to move the object and not change its size, which is the desired functionality for an assembly application.</span></span>
<span data-ttu-id="000a1-181">此外，遠的操作未以只允許模組組件的直接互動。</span><span class="sxs-lookup"><span data-stu-id="000a1-181">In addition, far manipulation is unchecked to allow only for direct interaction of module parts.</span></span>

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

<span data-ttu-id="000a1-183">部分組件的示範指令碼 （如上所示） 是管理使用者所放入農曆模組物件的指令碼。</span><span class="sxs-lookup"><span data-stu-id="000a1-183">The part assembly demo script (shown above) is the scrip that manages the objects to be placed on to the lunar module by the user.</span></span> 

<span data-ttu-id="000a1-184">選取 (n 上面的影像，背包/油箱的大小寫) 與可連線至的物件轉換為 「 物件至位置 」 欄位。</span><span class="sxs-lookup"><span data-stu-id="000a1-184">The "Object To Place" field is the transform that is selected (n the case of the image above, the backpack/fuel tank) with the object that it can connect to.</span></span> 

<span data-ttu-id="000a1-185">「 近距離 」 和 「 遠距離 」 設定負責決定的相近的組件會貼齊就地或釋出。</span><span class="sxs-lookup"><span data-stu-id="000a1-185">The "Near Distance" and "Far Distance" settings are responsible for determining the proximity to which parts will snap in place or be released.</span></span> <span data-ttu-id="000a1-186">比方說，背包/油箱必須離開的地方貼齊農曆模組 0.1 的單位。</span><span class="sxs-lookup"><span data-stu-id="000a1-186">For example, the backpack/fuel tank would need to be 0.1 units away from the lunar module to snap into place.</span></span> <span data-ttu-id="000a1-187">「 遠距離 」 設定為以中斷連結農曆模組需要物件的位置。</span><span class="sxs-lookup"><span data-stu-id="000a1-187">The "Far Distance" sets the location where the object needs to be to detach from the lunar module.</span></span> <span data-ttu-id="000a1-188">在此情況下，使用者的手必須抓取背包/油箱，然後將它 0.2 單位遠離農曆模組，以移除回貼齊定位。</span><span class="sxs-lookup"><span data-stu-id="000a1-188">In this case, the user’s hand must grab the backpack/fuel tank and pull it 0.2 units away from the lunar module to remove it from snapping back into place.</span></span>

<span data-ttu-id="000a1-189">「 工具提示物件 」 是在場景中的工具提示標籤。</span><span class="sxs-lookup"><span data-stu-id="000a1-189">The "Tool Tip Object" is the tool tip label in the scene.</span></span> <span data-ttu-id="000a1-190">當物件會就地貼齊時，標籤將會停用。</span><span class="sxs-lookup"><span data-stu-id="000a1-190">When the objects are snapped in place, the label will be disabled.</span></span> 

<span data-ttu-id="000a1-191">音訊來源會自動抓取。</span><span class="sxs-lookup"><span data-stu-id="000a1-191">The Audio Source will be automatically grabbed.</span></span> 

### <a name="placement-hints-buttons"></a><span data-ttu-id="000a1-192">放置提示按鈕</span><span class="sxs-lookup"><span data-stu-id="000a1-192">Placement Hints Buttons</span></span>
<span data-ttu-id="000a1-193">在 [第 2 課](mrlearning-base-ch2.md)，您已了解如何放置與設定按鈕，執行下列動作變更項目的色彩，或讓它推送時播放音效。</span><span class="sxs-lookup"><span data-stu-id="000a1-193">In [Lesson 2](mrlearning-base-ch2.md), you learned how to place and configure buttons to do things like change the color of an item or make it play a sound when it is pushed.</span></span> <span data-ttu-id="000a1-194">我們將繼續使用這些原則，當我們設定切換位置提示按鈕。</span><span class="sxs-lookup"><span data-stu-id="000a1-194">We will continue to use those principles as we configure our buttons for toggling placement hints.</span></span> 

<span data-ttu-id="000a1-195">目標是要設定我們的按鈕，以便每次使用者按下位置提示按鈕，它會切換可見性的半透明的位置提示。</span><span class="sxs-lookup"><span data-stu-id="000a1-195">The goal is to configure our button so that every time the user presses the placement hint button, it will toggle visibility of the translucent placement hints.</span></span> 

<span data-ttu-id="000a1-196">步驟 1：基底的場景階層中選取的位置提示物件時，請將農曆模組移到空 「 僅顯示 runtime 」 位置，在 [偵測器] 面板中。</span><span class="sxs-lookup"><span data-stu-id="000a1-196">Step 1: Move the Lunar Module to the empty "runtime only" slot in the inspector panel while the Placement Hints object is selected in your base scene hierarchy.</span></span> 
 <span data-ttu-id="000a1-197">![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG)步驟 2:現在，按一下下拉式清單中，該處會指示，「 沒有函式 」。</span><span class="sxs-lookup"><span data-stu-id="000a1-197">![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) Step 2: Now click the dropdown list where it says, "no function."</span></span> <span data-ttu-id="000a1-198">移至 「 TogglePlacementHints"，以及該功能表下選取 「"ToggleGameObjects （）。</span><span class="sxs-lookup"><span data-stu-id="000a1-198">Go down to "TogglePlacementHints," and under that menu select "ToggleGameObjects ()."</span></span> <span data-ttu-id="000a1-199">ToggleGameObjects() 將切換位置提示開啟和關閉，使其可見或不可見每次按下按鈕時。</span><span class="sxs-lookup"><span data-stu-id="000a1-199">ToggleGameObjects() will toggle the placement hints on and off so that they are visible or invisible every time the button is pressed.</span></span>
 <span data-ttu-id="000a1-200">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="000a1-200">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span></span>

### <a name="configuring-the-reset-button"></a><span data-ttu-id="000a1-201">設定重設 按鈕</span><span class="sxs-lookup"><span data-stu-id="000a1-201">Configuring the Reset Button</span></span>

<span data-ttu-id="000a1-202">會發生錯誤或意外地擲回物件，或只想要 rest 經驗的使用者可讓的情況。</span><span class="sxs-lookup"><span data-stu-id="000a1-202">There will be situations where the user makes a mistake, or accidently throws the object away, or just wants to rest the experience.</span></span> <span data-ttu-id="000a1-203">重設 按鈕將能夠重新啟動的經驗。</span><span class="sxs-lookup"><span data-stu-id="000a1-203">The reset button will add the ability to restart the experience.</span></span> 

<span data-ttu-id="000a1-204">步驟 1：選取 [重設] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="000a1-204">Step 1: Select the reset button.</span></span> <span data-ttu-id="000a1-205">在基底的場景，它會命名為"ResetRoundButton。 」</span><span class="sxs-lookup"><span data-stu-id="000a1-205">In the base scene, it’s named "ResetRoundButton."</span></span> 

<span data-ttu-id="000a1-206">步驟 2：農曆模組會從基底的場景階層拖曳至 「 按下按鈕 」 下的空插槽偵測器 面板。</span><span class="sxs-lookup"><span data-stu-id="000a1-206">Step 2: Drag the lunar module from the base scene hierarchy into the empty slot under "button pressed" the inspector panel.</span></span>
 <span data-ttu-id="000a1-207">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="000a1-207">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span></span>

<span data-ttu-id="000a1-208">步驟 3：選取下拉式功能表中，指出 「 沒有函式 」，並停留在 「 LaunchLunarModule。 」</span><span class="sxs-lookup"><span data-stu-id="000a1-208">Step 3: Select the dropdown menu that says, "no function" and hover over "LaunchLunarModule."</span></span> <span data-ttu-id="000a1-209">現在選取 "resetModule （）"。</span><span class="sxs-lookup"><span data-stu-id="000a1-209">Now select "resetModule ()."</span></span>

![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> <span data-ttu-id="000a1-211">注意：您會注意到，根據預設"GameObject.BroadcastMessage 」 設定為"ResetPlacement。 」</span><span class="sxs-lookup"><span data-stu-id="000a1-211">Note: You will notice that by default the "GameObject.BroadcastMessage" is configured to "ResetPlacement."</span></span> <span data-ttu-id="000a1-212">這會廣播訊息，稱為 「 ResetPlacement"RocketLauncher_Tutorial 的每一個子物件。</span><span class="sxs-lookup"><span data-stu-id="000a1-212">This will broadcast a message called "ResetPlacement" for every child object of RocketLauncher_Tutorial.</span></span> <span data-ttu-id="000a1-213">該訊息會回應具有 「 ResetPlacement() 」 方法的任何物件重設它的位置。</span><span class="sxs-lookup"><span data-stu-id="000a1-213">Any object that has a method for "ResetPlacement()" will respond to that message by resetting it's position.</span></span> 

### <a name="launching-the-lunar-module"></a><span data-ttu-id="000a1-214">啟動農曆模組</span><span class="sxs-lookup"><span data-stu-id="000a1-214">Launching the Lunar Module</span></span>
<span data-ttu-id="000a1-215">這一章，我們將設定 [啟動] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="000a1-215">This chapter we will be configuring the launch button.</span></span> <span data-ttu-id="000a1-216">這將允許使用者按下按鈕，並啟動農曆模組到空間。</span><span class="sxs-lookup"><span data-stu-id="000a1-216">This will permit the user to press the button and launch the Lunar Module into space.</span></span>

<span data-ttu-id="000a1-217">步驟 1：選取 [啟動] 按鈕 （基底的場景中它稱為 「 LaunchRoundButton"）。</span><span class="sxs-lookup"><span data-stu-id="000a1-217">Step 1: Select the launch button (in the base scene it’s named "LaunchRoundButton").</span></span> <span data-ttu-id="000a1-218">將農曆模組拖曳至 「 觸控 End 」 下的空插槽中，在 [偵測器] 面板。</span><span class="sxs-lookup"><span data-stu-id="000a1-218">Drag the Lunar Module to the empty slot under "Touch End" in the inspector panel.</span></span>
 <span data-ttu-id="000a1-219">![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG)步驟 2:選取下拉式功能表中，指出 「 沒有函式 」。</span><span class="sxs-lookup"><span data-stu-id="000a1-219">![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) Step 2: Select the dropdown menu that says, "no function."</span></span> <span data-ttu-id="000a1-220">「 LaunchLunarModule 「 暫留並選取"StopThruster （）"。</span><span class="sxs-lookup"><span data-stu-id="000a1-220">Hover over "LaunchLunarModule" and select "StopThruster ()."</span></span> <span data-ttu-id="000a1-221">這會控制多少使用者想要提供給農曆模組的主要目的是。</span><span class="sxs-lookup"><span data-stu-id="000a1-221">This will control how much thrust the user wants to give to the Lunar Module.</span></span> 
 <span data-ttu-id="000a1-222">![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)步驟 3:「 ButtonPressed() 」，將農曆模組 （按一下、 按住不放，並拖曳） 新增至空的插槽。</span><span class="sxs-lookup"><span data-stu-id="000a1-222">![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG) Step 3: Under "ButtonPressed()", add the Lunar Module (click, hold, and drag) to the empty slot.</span></span> 

<span data-ttu-id="000a1-223">步驟 4：按一下下拉式功能表，指出 「 沒有函式 」 和 「 LaunchLunarModule 「 暫留，然後選取"StartThruster （）"。</span><span class="sxs-lookup"><span data-stu-id="000a1-223">Step 4: Click the dropdown menu that says, "no function" and hover over "LaunchLunarModule" and select "StartThruster ()."</span></span> 
 <span data-ttu-id="000a1-224">![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)步驟 5:將音樂新增至農曆模組，讓當 rocket 將時，會播放音樂。</span><span class="sxs-lookup"><span data-stu-id="000a1-224">![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG) Step 5: Add music to the Lunar Module so that when the rocket takes off, the music will play.</span></span> <span data-ttu-id="000a1-225">若要這樣做，請拖曳農曆模組到 」 按鈕 Pressed() 」 底下的下一步 的空插槽。</span><span class="sxs-lookup"><span data-stu-id="000a1-225">To do this, drag the Lunar Module to the next empty slot under "Button Pressed()".</span></span>

<span data-ttu-id="000a1-226">步驟 6：選取下拉式功能表中，指出 「 沒有函式 」"AudioSource 「 暫留並選取 「 PlayOneShot (AudioClip) 」。</span><span class="sxs-lookup"><span data-stu-id="000a1-226">Step 6: Select the dropdown menu that says, "no function" and hover over "AudioSource" and select "PlayOneShot (AudioClip)."</span></span> <span data-ttu-id="000a1-227">請盡情探索各種 MRTK 所隨附的音效。</span><span class="sxs-lookup"><span data-stu-id="000a1-227">Feel free to explore the variety of sounds included with the MRTK.</span></span> <span data-ttu-id="000a1-228">此範例中，我們要堅持使用"MRTK_Gem。 」</span><span class="sxs-lookup"><span data-stu-id="000a1-228">For this example, we are going to stick with "MRTK_Gem."</span></span>
 <span data-ttu-id="000a1-229">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span><span class="sxs-lookup"><span data-stu-id="000a1-229">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span></span>


### <a name="congratulations"></a><span data-ttu-id="000a1-230">恭喜您</span><span class="sxs-lookup"><span data-stu-id="000a1-230">Congratulations</span></span> 
<span data-ttu-id="000a1-231">您完整設定此應用程式 ！</span><span class="sxs-lookup"><span data-stu-id="000a1-231">You have fully configured this application!</span></span> <span data-ttu-id="000a1-232">現在當您按下 播放，您可以完全組合農曆模組、 切換提示、 啟動農曆模組，並將它做過一次重設。</span><span class="sxs-lookup"><span data-stu-id="000a1-232">Now when you press play, you can fully assemble the Lunar Module, toggle hints, launch the Lunar Module, and reset it to do it all over again.</span></span>
