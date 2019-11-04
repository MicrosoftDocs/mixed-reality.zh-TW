---
title: 快速入門教學課程-5。 與3D 物件互動
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: ba1fae751874ad6b24592b2987a7a41c9ce5703b
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437765"
---
# <a name="5-interacting-with-3d-objects"></a><span data-ttu-id="29487-104">5. 與3D 物件互動</span><span class="sxs-lookup"><span data-stu-id="29487-104">5. Interacting with 3D objects</span></span>

<span data-ttu-id="29487-105">在本教學課程中，您將瞭解基本的3D 內容和使用者體驗，例如：</span><span class="sxs-lookup"><span data-stu-id="29487-105">In this tutorial, you will learn about basic 3D content and user experience, such as:</span></span> 
* <span data-ttu-id="29487-106">將3D 物件當做集合的一部分來組織</span><span class="sxs-lookup"><span data-stu-id="29487-106">Organizing 3D objects as part of a collection</span></span>
* <span data-ttu-id="29487-107">基本操作的周框方塊</span><span class="sxs-lookup"><span data-stu-id="29487-107">Bounding boxes for basic manipulation</span></span>
* <span data-ttu-id="29487-108">近與遠互動</span><span class="sxs-lookup"><span data-stu-id="29487-108">Near and far interaction</span></span>
* <span data-ttu-id="29487-109">觸控和抓取筆勢與手勢追蹤</span><span class="sxs-lookup"><span data-stu-id="29487-109">Touch and grab gestures with hand tracking</span></span> 

## <a name="objectives"></a><span data-ttu-id="29487-110">目標</span><span class="sxs-lookup"><span data-stu-id="29487-110">Objectives</span></span>

* <span data-ttu-id="29487-111">瞭解如何使用 MRTK 的方格物件集合來組織3D 內容</span><span class="sxs-lookup"><span data-stu-id="29487-111">Learn how to organize 3D content with MRTK's grid object collection</span></span>
* <span data-ttu-id="29487-112">實作週框方塊</span><span class="sxs-lookup"><span data-stu-id="29487-112">Implement bounding boxes</span></span>
* <span data-ttu-id="29487-113">設定3D 物件進行基本操作--移動、旋轉和縮放</span><span class="sxs-lookup"><span data-stu-id="29487-113">Configure 3D objects for basic manipulation--move, rotate, and scale</span></span>
* <span data-ttu-id="29487-114">探索遠近互動</span><span class="sxs-lookup"><span data-stu-id="29487-114">Explore near and far interaction</span></span>
* <span data-ttu-id="29487-115">深入瞭解其他的右手邊追蹤手勢，例如「抓取」和「觸控」</span><span class="sxs-lookup"><span data-stu-id="29487-115">Learn about additional hand tracking gestures, such as grab and touch</span></span>

## <a name="instructions"></a><span data-ttu-id="29487-116">指示</span><span class="sxs-lookup"><span data-stu-id="29487-116">Instructions</span></span>

### <a name="organizing-3d-objects-in-a-collection"></a><span data-ttu-id="29487-117">組織集合中的 3D 物件</span><span class="sxs-lookup"><span data-stu-id="29487-117">Organizing 3D Objects in a Collection</span></span>

1. <span data-ttu-id="29487-118">以滑鼠右鍵按一下您的階層，然後選取 [建立空的] 以建立空白遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="29487-118">Right-click on your hierarchy and select Create Empty to create an empty game object.</span></span> <span data-ttu-id="29487-119">將它重新命名為3DObjectCollection。</span><span class="sxs-lookup"><span data-stu-id="29487-119">Rename it to 3DObjectCollection.</span></span> <span data-ttu-id="29487-120">這是我們放置所有 3D 物件的地方。</span><span class="sxs-lookup"><span data-stu-id="29487-120">This is where we will put all of our 3D Objects.</span></span> <span data-ttu-id="29487-121">確定集合的位置設定為 x = 0、y = 0 且 z = 0。</span><span class="sxs-lookup"><span data-stu-id="29487-121">Make sure the collection’s positioning is set at x = 0, y = 0, and z = 0.</span></span>

![Lesson4 Chapter1 Step1im](images/Lesson4_Chapter1_step1im.PNG)

2. <span data-ttu-id="29487-123">使用相同的指示匯入 BaseModule 的資產，以匯入[tut1-lesson1-step3](mrlearning-base-ch1.md)中所述的自訂套件。</span><span class="sxs-lookup"><span data-stu-id="29487-123">Import BaseModule assets using the same instructions, to import custom packages outlined in [Lesson1](mrlearning-base-ch1.md).</span></span> <span data-ttu-id="29487-124">BaseModule 資產包含3D 模組，以及在本教學課程中使用的其他實用腳本。</span><span class="sxs-lookup"><span data-stu-id="29487-124">The BaseModule assets include 3D modules and other useful scripts that are used throughout this tutorial.</span></span> <span data-ttu-id="29487-125">您可以在這裡找到 BaseModule Unity 封裝： <https://github.com/Microsoft/MixedRealityLearning/releases/tag/V1.1></span><span class="sxs-lookup"><span data-stu-id="29487-125">The BaseModule Unity package can be found here: <https://github.com/Microsoft/MixedRealityLearning/releases/tag/V1.1></span></span>

3. <span data-ttu-id="29487-126">咖啡杯預製物件可以透過旁邊的藍色立方體辨識。</span><span class="sxs-lookup"><span data-stu-id="29487-126">The coffee cup prefab can be recognized by a blue cube next to it.</span></span> <span data-ttu-id="29487-127">請勿選取具有藍色立方體和小型白色紙張的咖啡杯，因為這代表原始的3D 模型，而不是 prefab。）</span><span class="sxs-lookup"><span data-stu-id="29487-127">Do not select the coffee cup with the blue cube and small white paper because this denotes the original 3D model and not the prefab.)</span></span> 

![Lesson4 Chapter1 Noteaim](images/Lesson4_chapter1_noteaim.PNG)

4. <span data-ttu-id="29487-129">將您選擇的咖啡杯 prefab 拖曳至步驟1中的3DObjectCollection 遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="29487-129">Drag the coffee cup prefab of your choice into the 3DObjectCollection game object from Step 1.</span></span> <span data-ttu-id="29487-130">咖啡杯現在是該集合的子系。</span><span class="sxs-lookup"><span data-stu-id="29487-130">The coffee cup is now a child of the collection.</span></span>

![Lesson4 Chapter1 Step4ima](images/Lesson4_chapter1_step4ima.PNG)

5. <span data-ttu-id="29487-132">接下來，您將在場景中新增更多3D 物件。</span><span class="sxs-lookup"><span data-stu-id="29487-132">Next, you'll add more 3D objects into our scene.</span></span> <span data-ttu-id="29487-133">以下是要在此範例中新增的物件清單。</span><span class="sxs-lookup"><span data-stu-id="29487-133">Below is a list of objects to add in this example.</span></span> <span data-ttu-id="29487-134">當您新增物件時，您可能會發現它們以各種大小出現在場景中。</span><span class="sxs-lookup"><span data-stu-id="29487-134">As you add the objects, you might find they appear in your scene in various sizes.</span></span> <span data-ttu-id="29487-135">調整 [偵測器] 面板中 [轉換設定] 下每個3D 模型的尺規。</span><span class="sxs-lookup"><span data-stu-id="29487-135">Adjust the scale of each 3D model under Transform Setting in the Inspector panel.</span></span> <span data-ttu-id="29487-136">以下的物件列出了此範例的建議調整。</span><span class="sxs-lookup"><span data-stu-id="29487-136">Recommended adjustments for this example are listed with the objects below.</span></span> <span data-ttu-id="29487-137">在 [專案] 面板的 [搜尋] 方塊中搜尋這些單字，然後將3D 物件 prefab 拖曳到類似上一個步驟的3DObjectCollection 物件中。</span><span class="sxs-lookup"><span data-stu-id="29487-137">Search these words in the Search box in your project panel and drag the 3D object prefab into the 3DObjectCollection object similar to the previous step.</span></span> <span data-ttu-id="29487-138">您會在 [資產] 中找到這些 prefabs 的集合 > BaseModuleAssets > 基底模組 Prefabs</span><span class="sxs-lookup"><span data-stu-id="29487-138">You will find these collections of prefabs in Assets>BaseModuleAssets>Base Module Prefabs</span></span>
- <span data-ttu-id="29487-139">搜尋 TheModule_BaseModuleIncomplete。</span><span class="sxs-lookup"><span data-stu-id="29487-139">Search for TheModule_BaseModuleIncomplete.</span></span> <span data-ttu-id="29487-140">拖曳至場景。</span><span class="sxs-lookup"><span data-stu-id="29487-140">Drag into scene.</span></span> <span data-ttu-id="29487-141">將比例設置為 x = 0.03、y = 0.03、z = 0.03。</span><span class="sxs-lookup"><span data-stu-id="29487-141">Set the scale to x = 0.03, y = 0.03, z = 0.03.</span></span> 
- <span data-ttu-id="29487-142">搜尋 Octa_BaseModuleIncomplete。</span><span class="sxs-lookup"><span data-stu-id="29487-142">Search for Octa_BaseModuleIncomplete.</span></span> <span data-ttu-id="29487-143">拖曳至場景。</span><span class="sxs-lookup"><span data-stu-id="29487-143">Drag into scene.</span></span> <span data-ttu-id="29487-144">將比例設置為 x = 0.13、</span><span class="sxs-lookup"><span data-stu-id="29487-144">Set the scale to x = 0.13.</span></span> <span data-ttu-id="29487-145">y = 0.13、z =0.13。</span><span class="sxs-lookup"><span data-stu-id="29487-145">y = 0.13, z =0.13.</span></span>
- <span data-ttu-id="29487-146">搜尋 EarthCore_BaseModuleIncomplete。</span><span class="sxs-lookup"><span data-stu-id="29487-146">Search for EarthCore_BaseModuleIncomplete.</span></span> <span data-ttu-id="29487-147">拖曳至場景。</span><span class="sxs-lookup"><span data-stu-id="29487-147">Drag into scene.</span></span> <span data-ttu-id="29487-148">將比例設置為 x = 50.0、y = 50.0、z = 50.0。</span><span class="sxs-lookup"><span data-stu-id="29487-148">Set the scale to x = 50.0 y = 50.0, z = 50.0.</span></span>
- <span data-ttu-id="29487-149">搜尋 Cheese_BaseModuleIncomplete。</span><span class="sxs-lookup"><span data-stu-id="29487-149">Search for Cheese_BaseModuleIncomplete.</span></span> <span data-ttu-id="29487-150">拖曳至場景。</span><span class="sxs-lookup"><span data-stu-id="29487-150">Drag into scene.</span></span> <span data-ttu-id="29487-151">將比例設置為 x = 0.05、y = 0.05、z = 0.05。</span><span class="sxs-lookup"><span data-stu-id="29487-151">Set the scale to x = 0.05, y = 0.05, z = 0.05.</span></span>
- <span data-ttu-id="29487-152">搜尋 Model_Platonic_BaseModuleIncomplete。</span><span class="sxs-lookup"><span data-stu-id="29487-152">Search for Model_Platonic_BaseModuleIncomplete.</span></span> <span data-ttu-id="29487-153">拖曳至場景。</span><span class="sxs-lookup"><span data-stu-id="29487-153">Drag into scene.</span></span> <span data-ttu-id="29487-154">將比例設置為 x = 0.13、y = 0.13、z = 0.13。</span><span class="sxs-lookup"><span data-stu-id="29487-154">Set the scale to x = 0.13, y = 0.13, z = 0.13.</span></span>

![Lesson4 Chapter1 Step5im](images/Lesson4_Chapter1_step5im.PNG)

6. <span data-ttu-id="29487-156">將三個 cube 新增至您的場景。</span><span class="sxs-lookup"><span data-stu-id="29487-156">Add three cubes into your scene.</span></span> <span data-ttu-id="29487-157">以滑鼠右鍵按一下 [3DObjectCollection] 物件，選取 [3D 物件]，然後選取 [Cube]。</span><span class="sxs-lookup"><span data-stu-id="29487-157">Right-click the 3DObjectCollection object, select 3D Object, then select Cube.</span></span> <span data-ttu-id="29487-158">將比例設置為 x = 0.14、y = 0.14 且 z = 0.14。</span><span class="sxs-lookup"><span data-stu-id="29487-158">Set the scale to x = 0.14, y = 0.14, and z = 0.14.</span></span> <span data-ttu-id="29487-159">重複此步驟兩次，以建立總共三個 cube。</span><span class="sxs-lookup"><span data-stu-id="29487-159">Repeat this step two additional times to create a total of three cubes.</span></span> <span data-ttu-id="29487-160">或者，您可以將 cube 複製兩次，共三個 cube。</span><span class="sxs-lookup"><span data-stu-id="29487-160">Alternatively, you can duplicate the cube twice for a total of three cubes.</span></span> <span data-ttu-id="29487-161">您也可以選擇使用 Assets>BaseModuleAssets>Base Module Prefabs 中三個已備妥的立方體預製物件，並選取 GreenCube_BaseModuleIncomplete、BlueCube_BaseModuleIncomplete 和 OrangeCube_BaseModuleIncomplete。</span><span class="sxs-lookup"><span data-stu-id="29487-161">You may also choose to use the three prepared cube prefabs from Assets>BaseModuleAssets>Base Module Prefabs and select GreenCube_BaseModuleIncomplete, BlueCube_BaseModuleIncomplete and OrangeCube_BaseModuleIncomplete.</span></span>

![Lesson4 Chapter1 Step6im](images/Lesson4_Chapter1_step6im.PNG)

7. <span data-ttu-id="29487-163">使用 MRTK 的 Grid 物件集合，透過[第2課](mrlearning-base-ch2.md)中所述的程式，組織您的物件集合以形成方格。</span><span class="sxs-lookup"><span data-stu-id="29487-163">Organize your collection of objects to form a grid, via the procedure described in [Lesson 2](mrlearning-base-ch2.md), using the MRTK’s Grid Object Collection.</span></span> <span data-ttu-id="29487-164">如需在3x3 方格中設定物件的範例，請參閱下圖。</span><span class="sxs-lookup"><span data-stu-id="29487-164">Refer to the image below, for an example of configuring the objects in a 3x3 grid.</span></span>

![Lesson4 Chapter1 Notebim](images/Lesson4_chapter1_notebim.PNG)

><span data-ttu-id="29487-166">注意：您可能會注意到某些物件是停在中心，例如上圖中的物件。</span><span class="sxs-lookup"><span data-stu-id="29487-166">Note: You might notice that some of the objects are off-center, such as the objects in the image above.</span></span> <span data-ttu-id="29487-167">這是因為預製物件或物件可能具有未對齊的子物件。</span><span class="sxs-lookup"><span data-stu-id="29487-167">This is because prefabs or objects may have child objects that are not aligned.</span></span> <span data-ttu-id="29487-168">隨意對物件位置或子物件位置進行必要的調整，以實現完善對齊的方格。</span><span class="sxs-lookup"><span data-stu-id="29487-168">Feel free to make any necessary adjustments to object positions or child object positions to achieve a well-aligned grid.</span></span>


### <a name="manipulating-3d-objects"></a><span data-ttu-id="29487-169">操作 3D 物件</span><span class="sxs-lookup"><span data-stu-id="29487-169">Manipulating 3D Objects</span></span>
1. <span data-ttu-id="29487-170">新增可操作立方體的功能。</span><span class="sxs-lookup"><span data-stu-id="29487-170">Add the ability to manipulate a cube.</span></span> <span data-ttu-id="29487-171">若要新增操作3D 物件的功能，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="29487-171">To add the ability to manipulate 3D objects, do the following:</span></span>
-   <span data-ttu-id="29487-172">選取您想要在階層中操作的3D 物件（亦即您的其中一個 cube）。</span><span class="sxs-lookup"><span data-stu-id="29487-172">Select the 3D object you want to manipulate in your hierarchy (i.e. one of your cubes).</span></span>
-   <span data-ttu-id="29487-173">按一下 [新增元件]</span><span class="sxs-lookup"><span data-stu-id="29487-173">Click Add Component</span></span> 
-   <span data-ttu-id="29487-174">搜尋操作</span><span class="sxs-lookup"><span data-stu-id="29487-174">Search for manipulation</span></span>
-   <span data-ttu-id="29487-175">選取操作處理常式</span><span class="sxs-lookup"><span data-stu-id="29487-175">Select Manipulation Handler</span></span>
-   <span data-ttu-id="29487-176">針對3DObjectCollection 物件下的所有3D 物件重複執行，但不針對3DObjectCollection 本身。</span><span class="sxs-lookup"><span data-stu-id="29487-176">Repeat for all 3D objects under the 3DObjectCollection object, but not the 3DObjectCollection itself.</span></span>
-   <span data-ttu-id="29487-177">確定所有3D 物件都有碰撞或箱碰撞件（新增元件 > 方塊碰撞）。</span><span class="sxs-lookup"><span data-stu-id="29487-177">Ensure that all 3D objects have a collider or box collider (Add Component>Box Collider).</span></span>

![Lesson4 Chapter2 Step1im](images/Lesson4_chapter2_step1im.PNG)

><span data-ttu-id="29487-179">操作處理常式是一種元件，可讓您調整物件在操作時的行為方式設定。</span><span class="sxs-lookup"><span data-stu-id="29487-179">The manipulation handler is a component that lets you adjust settings for how objects behave when manipulated.</span></span> <span data-ttu-id="29487-180">這包括在特定軸上旋轉、縮放、移動和限制移動。</span><span class="sxs-lookup"><span data-stu-id="29487-180">This includes rotation, scaling, moving, and constraining movement on a specific axis.</span></span> 

2. <span data-ttu-id="29487-181">限制一個立方體，使其只能縮放。</span><span class="sxs-lookup"><span data-stu-id="29487-181">Restrict one cube so that it can only be scaled.</span></span> <span data-ttu-id="29487-182">在3DObjectCollection 物件中選取一個 cube。</span><span class="sxs-lookup"><span data-stu-id="29487-182">Select one cube in the 3DObjectCollection object.</span></span> <span data-ttu-id="29487-183">在 [偵測器] 面板中，按一下 [兩個操作類型] 旁的下拉式功能表，然後選取 [調整]。</span><span class="sxs-lookup"><span data-stu-id="29487-183">In the Inspector panel, next to Two Handed Manipulation Type, click the drop-down menu and select Scale.</span></span> <span data-ttu-id="29487-184">這使得使用者只能變更立方體的大小。</span><span class="sxs-lookup"><span data-stu-id="29487-184">This makes it so that the user can only change the cube’s size.</span></span>

![Lesson4 Chapter2 Step2im](images/Lesson4_Chapter2_step2im.PNG)

3. <span data-ttu-id="29487-186">變更每個立方體的色彩，以便我們可以區分它們。</span><span class="sxs-lookup"><span data-stu-id="29487-186">Change the color of each cube so that we can differentiate between them.</span></span> 
-   <span data-ttu-id="29487-187">移至 [專案] 面板並向下 MixedRealityToolkit，直到您看到 [SDK]，然後選取它。</span><span class="sxs-lookup"><span data-stu-id="29487-187">Go to the Project panel and scroll down until you see MixedRealityToolkit.SDK, then select it.</span></span>
-   <span data-ttu-id="29487-188">選取 [標準資產] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="29487-188">Select the Standard Assets folder.</span></span>
-   <span data-ttu-id="29487-189">按一下 [材質] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="29487-189">Click the Materials folder.</span></span>
-   <span data-ttu-id="29487-190">將不同的材質拖曳到每個立方體上。</span><span class="sxs-lookup"><span data-stu-id="29487-190">Drag a different material onto each of your cubes.</span></span> 

><span data-ttu-id="29487-191">注意：您可以選擇 cube 的任何色彩。</span><span class="sxs-lookup"><span data-stu-id="29487-191">Note: You can choose any color for your cubes.</span></span> <span data-ttu-id="29487-192">在此範例中，會使用 glowingcyan、glowingorange 和綠色。</span><span class="sxs-lookup"><span data-stu-id="29487-192">For this example, glowingcyan, glowingorange and green are used.</span></span> <span data-ttu-id="29487-193">請隨意試驗不同的色彩。</span><span class="sxs-lookup"><span data-stu-id="29487-193">Feel free to experiment with different colors.</span></span> <span data-ttu-id="29487-194">若要將色彩加入 cube 中，請按一下您要變更的 cube，然後將材質拖曳至 cube 的 [偵測器] 面板中的網格轉譯器的 [材質] 欄位。</span><span class="sxs-lookup"><span data-stu-id="29487-194">To add the color to the cube, click the cube you want to change, then drag the material to the mesh renderer's material field in the cube's Inspector panel.</span></span> 

![Lesson4 Chapter2 Step3im](images/Lesson4_Chapter2_step3im.PNG)

4. <span data-ttu-id="29487-196">選取3DObjectCollection 物件中的另一個 cube，並將它的移動限制為來自 head 的固定距離。</span><span class="sxs-lookup"><span data-stu-id="29487-196">Select another cube in the 3DObjectCollection object and make it so that its movement is constrained to a fixed distance from the head.</span></span> <span data-ttu-id="29487-197">若要這麼做，請在 [移動標籤上的條件約束] 右邊，按一下下拉式功能表，然後選取 [修正與 Head 的距離]。</span><span class="sxs-lookup"><span data-stu-id="29487-197">To do this, to the right of Constraint on Movement label, click the drop-down menu and select Fix Distance from the Head.</span></span> <span data-ttu-id="29487-198">這會將 cube 調整為其願景領域內。</span><span class="sxs-lookup"><span data-stu-id="29487-198">This adjusts the cube to be within their field of vision.</span></span> 

![Lesson4 Chapter2 Step4im](images/Lesson4_chapter2_step4im.PNG)

<span data-ttu-id="29487-200">下列幾個步驟的目標是要啟用抓取並與我們的3D 物件互動，以及套用不同的操作設定。</span><span class="sxs-lookup"><span data-stu-id="29487-200">The goal of the following few steps is to enable grabbing and interacting with our 3D objects and applying different manipulation settings.</span></span>

5. <span data-ttu-id="29487-201">選取 [乳酪] 物件，然後按一下 [偵測器] 面板中的 [新增元件]。</span><span class="sxs-lookup"><span data-stu-id="29487-201">Select the Cheese object, then click Add Component from the Inspector panel.</span></span> 

6. <span data-ttu-id="29487-202">在搜尋方塊中搜尋近乎互動的 Grabbable，然後選取腳本。</span><span class="sxs-lookup"><span data-stu-id="29487-202">Search in the search box for Near Interaction Grabbable and select the script.</span></span> <span data-ttu-id="29487-203">此元件可讓使用者使用已追蹤的手來觸及和抓取物件。</span><span class="sxs-lookup"><span data-stu-id="29487-203">This component enables users to reach out and grab objects with tracked hands.</span></span> <span data-ttu-id="29487-204">物件也可以從距離進行操作，除非取消核取 [允許最遠操作] 核取方塊，如下列影像中的綠色圓圈所表示。</span><span class="sxs-lookup"><span data-stu-id="29487-204">Objects can also be manipulated from a distance, unless the Allow Far Manipulation checkbox is unchecked as denoted by a green circle in the image below.</span></span>

![Lesson4 Chapter2 Step6im](images/Lesson4_Chapter2_step6im.PNG)

7. <span data-ttu-id="29487-206">在這些物件上重複步驟5和6，以將近乎互動的 Grabbable 新增至顆 octa 物件、Platonic 物件、地球核心、陰曆模組和咖啡杯。</span><span class="sxs-lookup"><span data-stu-id="29487-206">Add Near Interaction Grabbable to the Octa object, Platonic object, Earth Core, Lunar Module, and Coffee Cup by repeating Steps 5 and 6 on those objects.</span></span>

8. <span data-ttu-id="29487-207">從八邊形物件中移除遠距操作的能力。</span><span class="sxs-lookup"><span data-stu-id="29487-207">Remove the ability of far manipulation from the Octa object.</span></span> <span data-ttu-id="29487-208">若要這麼做，請選取階層中的顆 octa，並取消核取 [允許最大的操作] 核取方塊（以綠色圓圈標示）。</span><span class="sxs-lookup"><span data-stu-id="29487-208">To do this, select the Octa in the hierarchy and uncheck the Allow far Manipulation checkbox (marked by a green circle).</span></span> <span data-ttu-id="29487-209">這使得使用者只能使用追蹤的手直接與顆 octa 互動。</span><span class="sxs-lookup"><span data-stu-id="29487-209">This makes it so users can only interact with the octa directly using tracked hands.</span></span>

><span data-ttu-id="29487-210">注意：如需操作處理常式元件和其相關設定的完整檔，請參閱[MRTK 檔](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)。</span><span class="sxs-lookup"><span data-stu-id="29487-210">Note: For the full documentation of the manipulation handler component and it's associated settings, refer to the [MRTK Documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html).</span></span>

9. <span data-ttu-id="29487-211">請確定已將近距離互動 Grabbable 元件新增到地球核心、農曆模組和咖啡杯（請參閱步驟7）。</span><span class="sxs-lookup"><span data-stu-id="29487-211">Ensure that the Near Interaction Grabbable component has been added to the earth core, the lunar module and the coffee cup (see Step 7).</span></span>

10. <span data-ttu-id="29487-212">針對農曆模組，變更操作處理常式設定，使其在物件的中心前後旋轉，以進行近和遠的互動，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="29487-212">For the lunar module, change the Manipulation Handler settings so that it rotates around the object's center for both near and far interaction, as shown in the image below.</span></span>

![Lesson4 Chapter2 Step10im](images/Lesson4_chapter2_step10im.PNG)

<span data-ttu-id="29487-214">11：在地球核心中，將發行行為變更為 [無]。</span><span class="sxs-lookup"><span data-stu-id="29487-214">11: For the earth core, change the release behavior to nothing.</span></span> <span data-ttu-id="29487-215">如此一來，當地球核心從使用者的理解中放開之後，就不會繼續移動。</span><span class="sxs-lookup"><span data-stu-id="29487-215">This makes it so that once the earth core is released from the user's grasp, it doesn’t continue to move.</span></span> 

![Lesson4 Chapter2 Step11im](images/Lesson4_Chapter2_step11im.PNG)

> <span data-ttu-id="29487-217">注意：此設定適用于案例，例如建立您可以擲回的球。</span><span class="sxs-lookup"><span data-stu-id="29487-217">Note: This setting is useful for scenarios, such as creating a ball that you can throw.</span></span> <span data-ttu-id="29487-218">保持適當的速度和角度速度，以確保在球放開後，它會繼續在其發行的速度移動;類似于實體球的行為。</span><span class="sxs-lookup"><span data-stu-id="29487-218">Keeping the appropriate velocity and angular velocity to ensure that once the ball is released, it will continue to move at the velocity it was released at; similar to how a physical ball would behave.</span></span>

### <a name="adding-bounding-boxes"></a><span data-ttu-id="29487-219">新增週框方塊</span><span class="sxs-lookup"><span data-stu-id="29487-219">Adding Bounding Boxes</span></span>
<span data-ttu-id="29487-220">周框方塊可讓您更輕鬆且更直覺地操作物件，以進行直接操作（近乎互動）和以光線為基礎的操作（遠比互動）。周框方塊提供的控制碼可用於在特定軸上縮放和旋轉物件。</span><span class="sxs-lookup"><span data-stu-id="29487-220">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both direct manipulation (near interaction) and ray-based manipulation (far interaction.) Bounding boxes provide handles that can be grabbed for scaling and rotating objects along a specific axis.</span></span>
><span data-ttu-id="29487-221">注意：在您可以將周框方塊加入物件之前，您必須先在物件上具有碰撞器（例如，方塊碰撞器），如本課程先前所述。</span><span class="sxs-lookup"><span data-stu-id="29487-221">Note: Before you can add a bounding box to an object, you first need to have a collider on the object (e.g., a box collider), as was covered previously in this lesson.</span></span> <span data-ttu-id="29487-222">您可以選取物件，然後在物件的 [偵測器] 面板中選取 [新增元件 > 方塊碰撞器] 來新增 Colliders。</span><span class="sxs-lookup"><span data-stu-id="29487-222">Colliders can be added by selecting the object and in the object's inspector panel selecting Add Component>Box Collider.</span></span>
>

1. <span data-ttu-id="29487-223">將 box 碰撞項新增至地球核心物件（如果尚未存在）。</span><span class="sxs-lookup"><span data-stu-id="29487-223">Add a box collider to the Earth Core object if one does not already exist.</span></span> <span data-ttu-id="29487-224">如果根據給定的指示使用 [基本模組資產] 資料夾中提供的 prefab，則不需要箱碰撞和設定。</span><span class="sxs-lookup"><span data-stu-id="29487-224">The box collider and setup are not required, if using the prefab provided in the Base Module Assets folder per the instructions given.</span></span> <span data-ttu-id="29487-225">在地球核心的案例中，我們已將方塊碰撞項新增至地球核心底下的、node_id30、物件，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="29487-225">In the case of the earth core, we added the box collider to the, node_id30, object underneath the earth core, as shown in the image below.</span></span> <span data-ttu-id="29487-226">從物件的 [偵測器] 索引標籤中選取 [node_id30]，按一下 [新增元件]，然後搜尋方塊碰撞。</span><span class="sxs-lookup"><span data-stu-id="29487-226">Select node_id30 from the object's Inspector tab, click Add Component, and search for box collider.</span></span> 

![Lesson4 Chapter3 Step1im](images/Lesson4_Chapter3_step1im.PNG)

![Lesson4 Chapter3 Step2im](images/Lesson4_chapter3_step2im.PNG)

> <span data-ttu-id="29487-229">注意：請確定您已調整方塊的碰撞器大小，使其變得太大或太小。</span><span class="sxs-lookup"><span data-stu-id="29487-229">Note: Make sure that you size the box collider so that it’s not too big or too small.</span></span> <span data-ttu-id="29487-230">它的大小應與它周圍的物件大致相同 (在本例中為地核)。</span><span class="sxs-lookup"><span data-stu-id="29487-230">It should be roughly the same size as the object it’s surrounding (in this example, the earth core).</span></span> <span data-ttu-id="29487-231">選取方塊碰撞器中的 [編輯碰撞器] 選項，視需要調整方塊碰撞器。</span><span class="sxs-lookup"><span data-stu-id="29487-231">Adjust the box collider as needed by selecting the Edit Collider option in the box collider.</span></span> <span data-ttu-id="29487-232">您可以變更 [x]、[y] 和 [z] 值，或在編輯器場景視窗中拖曳周框方塊處理常式。</span><span class="sxs-lookup"><span data-stu-id="29487-232">You can either changing the x, y, and z values or drag the bounding box handlers in the Editor Scene window.</span></span> 

![Lesson4 Chapter3 Noteim](images/Lesson4_Chapter3_noteim.PNG)

2. <span data-ttu-id="29487-234">將周框方塊新增至地球核心的 node_id30 物件。</span><span class="sxs-lookup"><span data-stu-id="29487-234">Add a bounding box to the earth core's node_id30 object.</span></span> <span data-ttu-id="29487-235">若要這樣做，請從3DObjectCollection 中選取 node_id30 物件。</span><span class="sxs-lookup"><span data-stu-id="29487-235">To do this, select the node_id30 object from the 3DObjectCollection.</span></span> <span data-ttu-id="29487-236">在 [偵測器] 索引標籤中，按一下 [加入元件]，然後搜尋周框方塊。</span><span class="sxs-lookup"><span data-stu-id="29487-236">In the inspector tab, click Add Component, and search for bounding box.</span></span> <span data-ttu-id="29487-237">請確定週框方塊、方塊碰撞器和操作指令碼 (Manipulation Handler、Near Interaction Grabbable) 都在同一個遊戲物件上。</span><span class="sxs-lookup"><span data-stu-id="29487-237">Ensure that the bounding box, box collider, and manipulation scripts (manipulation handler, near interaction grabbable) are all on the same game object.</span></span>

3.  <span data-ttu-id="29487-238">在周框方塊的 [行為] 區段中，從 [啟用] 下拉式清單選取 [啟動時啟用]。</span><span class="sxs-lookup"><span data-stu-id="29487-238">In the bounding box's Behavior section, select Activate on Start from the Activation drop-down list.</span></span> <span data-ttu-id="29487-239">若要查看有關各種啟用選項和其他周框方塊選項的其他詳細資料，請參閱[MRTK 的周框方塊檔](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>)</span><span class="sxs-lookup"><span data-stu-id="29487-239">To review additional details regarding the various activation options and other bounding box options, see the [MRTK's bounding box documentation](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>)</span></span>

   

   <span data-ttu-id="29487-240">*在接下來的幾個步驟中，我們也會變更周框方塊的外觀，方法是調整預設的方塊材質、抓取的資料，以及角落和邊控點的視覺效果。MRTK 包含數個選項可自訂周框方塊。*</span><span class="sxs-lookup"><span data-stu-id="29487-240">*In the next few steps, we will also change how the bounding box looks by adjusting the default box material, the material while it’s being grabbed as well as the visualization of the corner and side handles. The MRTK contains several options to customize the bounding box.*</span></span>

4. <span data-ttu-id="29487-241">在 [專案] 面板中，搜尋 boundingbox，您會在搜尋結果中看到以藍色球體表示的材質清單，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="29487-241">In the Project panel, search for boundingbox and you’ll see a list of materials denoted by a blue sphere in the search results as shown in the image below.</span></span> 

5. <span data-ttu-id="29487-242">將 boundingbox 材質拖曳至周框方塊元件上的方塊材質位置。</span><span class="sxs-lookup"><span data-stu-id="29487-242">Drag the boundingbox material into the box material slot on the bounding box component.</span></span> <span data-ttu-id="29487-243">此外，請抓取 boundingboxgrabbed 的資料，並將其放在 [周框方塊] 元件上的 [將其抓取材質] 方塊中</span><span class="sxs-lookup"><span data-stu-id="29487-243">Also grab the boundingboxgrabbed material and put that in the box grabbed material slot on the bounding box component.</span></span>

6. <span data-ttu-id="29487-244">將 MRTK_BoundingBox_ScaleWidget prefab 拖曳至周框方塊元件上的縮放控點 prefab 位置。</span><span class="sxs-lookup"><span data-stu-id="29487-244">Drag the MRTK_BoundingBox_ScaleWidget prefab into the scale handle prefab slot on the bounding box component.</span></span> 

7. <span data-ttu-id="29487-245">將 [MRTK_BoundingBox_RotateWidget prefab] 拖曳到 [結合] 方塊元件上的 [旋轉控點] 插槽。</span><span class="sxs-lookup"><span data-stu-id="29487-245">Drag the MRTK_BoundingBox_RotateWidget prefab into the rotation handle slot on the bonding box component.</span></span>

![Lesson4 Chapter3 Step4 7Im](images/Lesson4_chapter3_step4-7im.PNG)

8. <span data-ttu-id="29487-247">請確定週框方塊的目標是正確的物件。</span><span class="sxs-lookup"><span data-stu-id="29487-247">Make sure the bounding box is targeting the right object.</span></span> <span data-ttu-id="29487-248">在 [周框方塊] 元件中，有 [目標物件] 和 [界限覆寫] 腳本。</span><span class="sxs-lookup"><span data-stu-id="29487-248">In the bounding box component, there is the target object and bounds override scripts.</span></span> <span data-ttu-id="29487-249">將具有周框方塊的物件拖曳到這兩個位置。</span><span class="sxs-lookup"><span data-stu-id="29487-249">Drag the object that has the bounding box around it to both of these slots.</span></span> <span data-ttu-id="29487-250">在此範例中，將 node_id30 物件拖曳到這兩個位置，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="29487-250">In this example, drag the node_id30 object to both of these slots, as shown in the image below.</span></span>

> <span data-ttu-id="29487-251">當您啟動或播放應用程式時，您的物件將會以藍色框架括住。</span><span class="sxs-lookup"><span data-stu-id="29487-251">When you start or play the application, your object will be surrounded by a blue frame.</span></span> <span data-ttu-id="29487-252">您可以拖曳該框架的角來調整物件的大小。</span><span class="sxs-lookup"><span data-stu-id="29487-252">You’re welcome to drag the corners of that frame to resize the object.</span></span> <span data-ttu-id="29487-253">如果您想要縮放控點和旋轉控點變得更大且更可見，則建議使用預設周框方塊設定（避免步驟4到7）。</span><span class="sxs-lookup"><span data-stu-id="29487-253">If you want the scaling handles and the rotation handles to be larger and more visible, it is recommend using the default bounding box settings (avoiding Steps 4 -through 7.)</span></span> 

![Lesson4 Chapter3 Step8im](images/Lesson4_Chapter3_step8im.PNG)

9. <span data-ttu-id="29487-255">若要返回預設周框方塊視覺效果，請在周框方塊物件的 [偵測器] 面板中選取 [旋轉控點] prefab，然後按 [刪除]。</span><span class="sxs-lookup"><span data-stu-id="29487-255">To return to the default bounding box visualization, in the Inspector panel of the bounding box's object, select the rotation handle prefab and press Delete.</span></span> <span data-ttu-id="29487-256">您會看到如下圖所示的周框方塊視覺效果。</span><span class="sxs-lookup"><span data-stu-id="29487-256">You will see a bounding box visualization similar to the image below.</span></span> <span data-ttu-id="29487-257">注意：周框方塊視覺效果只會在處於播放模式時出現。</span><span class="sxs-lookup"><span data-stu-id="29487-257">Note: the bounding box visualizations only appear when in play mode.</span></span>

![Lesson4 Chapter3 Step9im](images/Lesson4_chapter3_step9im.PNG)

### <a name="adding-touch-effects"></a><span data-ttu-id="29487-259">新增觸控效果</span><span class="sxs-lookup"><span data-stu-id="29487-259">Adding touch effects</span></span>
<span data-ttu-id="29487-260">在此範例中，當您用手觸控物件時，我們將播放音效。</span><span class="sxs-lookup"><span data-stu-id="29487-260">In this example, we are going to play a sound effect when you touch an object with your hand.</span></span>

1. <span data-ttu-id="29487-261">將音訊來源元件新增至遊戲物件中。</span><span class="sxs-lookup"><span data-stu-id="29487-261">Add an audio source component to your game object.</span></span> <span data-ttu-id="29487-262">選取場景階層中的 [顆 octa] 物件。</span><span class="sxs-lookup"><span data-stu-id="29487-262">Select the Octa object in your scene hierarchy.</span></span> <span data-ttu-id="29487-263">在 [偵測器] 面板中，按一下 [新增元件] 按鈕，搜尋並選取 [音訊來源]。</span><span class="sxs-lookup"><span data-stu-id="29487-263">In the inspector panel, click the Add Component button, search for and select audio source.</span></span> <span data-ttu-id="29487-264">我們將在後續步驟中使用此音訊來源播放音效。</span><span class="sxs-lookup"><span data-stu-id="29487-264">We’ll use this audio source to play a sound effect in a later step.</span></span> 

><span data-ttu-id="29487-265">注意：請確定顆 octa 物件上有方塊碰撞器。</span><span class="sxs-lookup"><span data-stu-id="29487-265">Note: Ensure that the Octa object has a box collider on it.</span></span>

2. <span data-ttu-id="29487-266">新增附近的互動 Touchable 元件。</span><span class="sxs-lookup"><span data-stu-id="29487-266">Add the Near Interaction Touchable component.</span></span> <span data-ttu-id="29487-267">按一下 [偵測器] 面板中的 [新增元件] 按鈕，並搜尋近乎互動 touchable。</span><span class="sxs-lookup"><span data-stu-id="29487-267">Click the Add Component button in the Inspector panel and search for near interaction touchable.</span></span> <span data-ttu-id="29487-268">選取它以新增元件。</span><span class="sxs-lookup"><span data-stu-id="29487-268">Select it to add the component.</span></span> 

><span data-ttu-id="29487-269">注意：先前我們新增了近乎互動的 grabbable。</span><span class="sxs-lookup"><span data-stu-id="29487-269">Note: Previously, we added near interaction grabbable.</span></span> <span data-ttu-id="29487-270">此互動和近距離互動 touchable 之間的差異在於，grabbable 互動的目的是要讓物件能夠抓取並與互動。</span><span class="sxs-lookup"><span data-stu-id="29487-270">The difference between this and near interaction touchable is that the grabbable interaction is intended for an object to be grabbed and interacted with.</span></span> <span data-ttu-id="29487-271">Touchable 元件適用于要觸及的物件。</span><span class="sxs-lookup"><span data-stu-id="29487-271">The touchable component is intended for the object to be touched.</span></span> <span data-ttu-id="29487-272">這兩個元件可以作為互動組合一起使用。</span><span class="sxs-lookup"><span data-stu-id="29487-272">Both components can be used together for a combination of interactions.</span></span>

![Lesson4 Chapter4 Step1 2Im](images/Lesson4_chapter4_step1-2im.PNG)

3. <span data-ttu-id="29487-274">在手互動觸控腳本中加入。</span><span class="sxs-lookup"><span data-stu-id="29487-274">Add in the Hand Interaction Touch script.</span></span> <span data-ttu-id="29487-275">請注意，此腳本包含在您匯入做為此示範一部分的 Unity 場景中，而且不會包含在原始 MRTK 中。</span><span class="sxs-lookup"><span data-stu-id="29487-275">Note that this script is included with the Unity scene that you imported as part of this demo, and it is not included in the original MRTK.</span></span> <span data-ttu-id="29487-276">就像上一個步驟一樣，按一下 [新增元件]，然後搜尋 [手動互動觸控] 將它加入。</span><span class="sxs-lookup"><span data-stu-id="29487-276">Just like the previous step, click Add Component and search for hand interaction touch to add it.</span></span>

><span data-ttu-id="29487-277">請注意，您有三個使用腳本的選項：</span><span class="sxs-lookup"><span data-stu-id="29487-277">Notice that you have three options with the script:</span></span> 

>   - <span data-ttu-id="29487-278">觸控完成：當您接觸並釋放物件時觸發程式</span><span class="sxs-lookup"><span data-stu-id="29487-278">On Touch Completed: Triggers when you touch and release the object</span></span>
>   - <span data-ttu-id="29487-279">開始觸控時：觸及物件時觸發</span><span class="sxs-lookup"><span data-stu-id="29487-279">On Touch Started: Triggers when the object is touched</span></span>
>   - <span data-ttu-id="29487-280">觸控更新：當您的手中觸及物件時，定期觸發程式</span><span class="sxs-lookup"><span data-stu-id="29487-280">On Touch Updated: Triggers periodically while your hand is touching the object</span></span>

>   <span data-ttu-id="29487-281">在此範例中，我們將使用 [啟動觸控] 設定。</span><span class="sxs-lookup"><span data-stu-id="29487-281">For this example, we will be working with the On Touch Started setting.</span></span>

4. <span data-ttu-id="29487-282">按一下 [On Touch 已啟動] 選項上的 [+] 按鈕，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="29487-282">Click the + button on the On Touch Started option as shown in the image below.</span></span> <span data-ttu-id="29487-283">將顆 octa 物件拖曳至空白欄位。</span><span class="sxs-lookup"><span data-stu-id="29487-283">Drag the Octa object into the empty field.</span></span> 

5. <span data-ttu-id="29487-284">在顯示 [沒有函式（下圖中的綠色矩形）] 的下拉式方塊中，選取 [Spatialize-> PlayOneShot]。</span><span class="sxs-lookup"><span data-stu-id="29487-284">In the drop-down that says No Function (above green rectangle in the image below), select AudioSource->PlayOneShot.</span></span> <span data-ttu-id="29487-285">我們將使用下列概念為此欄位新增音訊剪輯：</span><span class="sxs-lookup"><span data-stu-id="29487-285">We will add an audio clip to this field using the concepts below:</span></span>

   - <span data-ttu-id="29487-286">MRTK 確實提供了一小部分音訊剪輯。</span><span class="sxs-lookup"><span data-stu-id="29487-286">The MRTK does provide a small list of audio clips.</span></span> <span data-ttu-id="29487-287">您可以在 [Project] 面板中隨意探索這些內容。</span><span class="sxs-lookup"><span data-stu-id="29487-287">Feel free to explore these in your project panel.</span></span> <span data-ttu-id="29487-288">您會在 [MixedRealityToolkit] 資料夾下找到這些專案，然後按 [標準資產] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="29487-288">You will find them under the MixedRealityToolkit.SDK folder and then the Standard Assets folder.</span></span> <span data-ttu-id="29487-289">在這裡，您會看到所有音訊剪輯所在的音訊資料夾。</span><span class="sxs-lookup"><span data-stu-id="29487-289">There, you will see an Audio folder where all the audio clips are.</span></span>
   - <span data-ttu-id="29487-290">在此範例中，我們將使用 MRTK_Gem 音訊剪輯。</span><span class="sxs-lookup"><span data-stu-id="29487-290">For this example, we are going to use the MRTK_Gem audio clip.</span></span> 
   - <span data-ttu-id="29487-291">若要新增音訊剪輯，只需將您想要的剪輯從 [專案] 面板拖曳至 [檢查] 面板中的 [Spatialize] PlayOneShot （以上述範例中的綠色方塊標示）。</span><span class="sxs-lookup"><span data-stu-id="29487-291">To add an audio clip, simply drag the clip you want from the project panel into the AudioSource.PlayOneShot (marked by a green box in the example above) in the inspector panel.</span></span>

   <span data-ttu-id="29487-292">現在，當使用者到達並觸及顆 octa 物件時，就會播放音訊軌 MRTK_Gem。</span><span class="sxs-lookup"><span data-stu-id="29487-292">Now, when the user reaches out and touches the Octa object, the audio track MRTK_Gem will play.</span></span> <span data-ttu-id="29487-293">觸碰互動觸控腳本也會在觸及時調整物件的色彩。</span><span class="sxs-lookup"><span data-stu-id="29487-293">The Hand Interaction Touch script will also adjust the color of the object, when touched.</span></span> 

![Lesson4 Chapter4 Step3 5 Noteim](images/Lesson4_chapter4_step3-5-noteim.PNG)

## <a name="congratulations"></a><span data-ttu-id="29487-295">恭喜您</span><span class="sxs-lookup"><span data-stu-id="29487-295">Congratulations</span></span> 
<span data-ttu-id="29487-296">在本教學課程中，您已瞭解如何在方格集合中組織3D 物件，以及如何使用近距離互動（直接抓取和旋轉）和即時互動（使用注視光線或手片）來操作這些物件（縮放、旋轉和移動）。</span><span class="sxs-lookup"><span data-stu-id="29487-296">In this tutorial, you learned how to organize 3D objects in a grid collection and how to manipulate these objects (scaling, rotating, and moving) using near interaction (directly grabbing with tracked hands) and far interaction (using gaze rays or hand rays).</span></span> <span data-ttu-id="29487-297">您也學到如何將周框方塊放在3D 物件周圍，學習如何使用和自訂周框方塊上的 gizmos。</span><span class="sxs-lookup"><span data-stu-id="29487-297">You also learned how to put bounding boxes around 3D objects, and learned how to use and customize the gizmos on the bounding boxes.</span></span> <span data-ttu-id="29487-298">最後，您學習到觸控物件時如何觸發事件。</span><span class="sxs-lookup"><span data-stu-id="29487-298">Finally, you learned how to trigger events when touching an object.</span></span>

[<span data-ttu-id="29487-299">下一課： 6. 探索 advanced 輸入選項</span><span class="sxs-lookup"><span data-stu-id="29487-299">Next Lesson: 6. Exploring advanced input options</span></span>](mrlearning-base-ch5.md)

