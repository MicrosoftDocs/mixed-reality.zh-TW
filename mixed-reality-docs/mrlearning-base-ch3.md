---
title: MR 學習基本模組 - 動態內容放置和解算器
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 6f05b2cecd388b1b2f13e7e5228bc90091eee3bd
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66270404"
---
# <a name="mr-learning-base-module---dynamic-content-placement-and-solvers"></a><span data-ttu-id="22837-104">MR 學習基本模組 - 動態內容放置和解算器</span><span class="sxs-lookup"><span data-stu-id="22837-104">MR Learning Base Module - Dynamic Content Placement and Solvers</span></span>

<span data-ttu-id="22837-105">在 HoloLens 2 中，當全像投影以直覺方式追蹤使用者，並且透過讓互動流暢及簡潔的方式放置在實體環境中時，全像投影就會變得栩栩如生。</span><span class="sxs-lookup"><span data-stu-id="22837-105">Holograms come to life in the HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="22837-106">在第 3 課中，我們將探討如何使用 MRTK 的可用放置工具 (稱為「解算器」) 動態地放置全像投影。</span><span class="sxs-lookup"><span data-stu-id="22837-106">In Lesson 3, we will explore ways to dynamically place holograms using the MRTK’s available placement tools, known as "solvers."</span></span> <span data-ttu-id="22837-107">之所以稱為「解算器」，是因為這些是用來解決複雜空間放置演算法的工具。</span><span class="sxs-lookup"><span data-stu-id="22837-107">They are known as "solvers" for the way they solve complex spatial placement algorithms.</span></span> <span data-ttu-id="22837-108">在 MRTK 中，解算器是指令碼和行為的系統，用來允許 UI 元素在場景中追蹤您、使用者或其他遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="22837-108">In the MRTK, solvers are a system of scripts and behaviors that we use to be able to allow UI elements to follow you, the user or other game objects in the scene.</span></span> <span data-ttu-id="22837-109">也可用來快速對齊特定位置，讓您的應用程式更具直覺性。</span><span class="sxs-lookup"><span data-stu-id="22837-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span> 

## <a name="objectives"></a><span data-ttu-id="22837-110">目標</span><span class="sxs-lookup"><span data-stu-id="22837-110">Objectives</span></span>

* <span data-ttu-id="22837-111">導入 MRTK 的解算器</span><span class="sxs-lookup"><span data-stu-id="22837-111">Introduce the MRTK's solvers</span></span>
* <span data-ttu-id="22837-112">使用解算器讓一組按鈕追蹤使用者</span><span class="sxs-lookup"><span data-stu-id="22837-112">Use solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="22837-113">使用解算器讓遊戲物件跟隨追蹤的使用者手部</span><span class="sxs-lookup"><span data-stu-id="22837-113">Use solvers to have a game object follow the user's tracked hands</span></span>

## <a name="instructions"></a><span data-ttu-id="22837-114">指示</span><span class="sxs-lookup"><span data-stu-id="22837-114">Instructions</span></span>

### <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="22837-115">MRTK 中的解算器位置</span><span class="sxs-lookup"><span data-stu-id="22837-115">Location of solvers in the MRTK</span></span>
 <span data-ttu-id="22837-116">若要尋找您專案中可用的解算器，請查看 MRTK SDK 資料夾 (MixedRealityToolkit.SDK 資料夾)，然後在公用程式資料夾底下，您會看到解算器資料夾，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="22837-116">To find the available solvers in your project, look in the MRTK SDK folder (MixedRealityToolkit.SDK folder), then under the utilities folder you will see the solvers folder, as shown in the image below.</span></span>

![解算器](images/lesson3_chapter1_step1im.PNG)

><span data-ttu-id="22837-118">注意：在本課程中，我們將只介紹 "Orbital" 解算器和 "RadialView" 解算器的實作。</span><span class="sxs-lookup"><span data-stu-id="22837-118">Note: In this lesson we will only go over implementation of the "Orbital" solver and the "RadialView" solver.</span></span> <span data-ttu-id="22837-119">若要深入了解 MRTK 中可用解算器的完整範圍，請瀏覽： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html</span><span class="sxs-lookup"><span data-stu-id="22837-119">To learn more about the full range of solvers available in the MRTK, please visit: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html</span></span>

### <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="22837-120">使用解算器追蹤使用者</span><span class="sxs-lookup"><span data-stu-id="22837-120">Use a Solver to Follow the User</span></span>
<span data-ttu-id="22837-121">本章節的目標是提升我們先前建立的按鈕集合，讓其追蹤使用者的視線方向。</span><span class="sxs-lookup"><span data-stu-id="22837-121">The goal of this chapter is to enhance the button collection we previously created such that it follows the user’s gaze direction.</span></span> <span data-ttu-id="22837-122">在前一版的 MRTK 和 HoloToolkit 中，這稱為 "taglong" 功能。</span><span class="sxs-lookup"><span data-stu-id="22837-122">In previous version of the MRTK and HoloToolkit, this was referred to as a "taglong" functionality.</span></span>

1. <span data-ttu-id="22837-123">選取前一課中的「按鈕集合」父系物件。</span><span class="sxs-lookup"><span data-stu-id="22837-123">Select the Button Collection parent object from the previous lesson.</span></span>

![Lesson3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. <span data-ttu-id="22837-125">在偵測器程式面板中，按一下 [新增元件] 按鈕並搜尋 "orbital"。</span><span class="sxs-lookup"><span data-stu-id="22837-125">In the inspector panel, click the "add component" button and search for "orbital."</span></span> <span data-ttu-id="22837-126">orbital 元件應該會隨即出現。</span><span class="sxs-lookup"><span data-stu-id="22837-126">The orbital component should appear.</span></span> <span data-ttu-id="22837-127">將其選取，並將 orbital 元件新增至「按鈕集合」遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="22837-127">Select it to add the orbital component to the Button Collection game object.</span></span>

![Lesson3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

><span data-ttu-id="22837-129">注意：新增元件時，您會發現系統在作為必要元件的偵測程式索引標籤中，加入orbital 指令碼和解算器處理常式指令碼。</span><span class="sxs-lookup"><span data-stu-id="22837-129">Note: When you add the component you will notice that the system adds the orbital script and the solver handler script in the inspector tab, which is a required component.</span></span> 

3. <span data-ttu-id="22837-130">為了設定按鈕集合來追蹤使用者，我們必須實作下列調整 (請同時參照下面的影像)：</span><span class="sxs-lookup"><span data-stu-id="22837-130">In order to configure the button collection to follow the user, we need to implement the following adjustments (please also refer to the image below):</span></span>
- <span data-ttu-id="22837-131">在 Orbital 指令碼中，將 [方向類型] 下拉式清單設定為 [只繞 Y 軸旋轉]。</span><span class="sxs-lookup"><span data-stu-id="22837-131">In the Orbital script, set the "orientation type" drop-down list to "Yaw Only."</span></span> <span data-ttu-id="22837-132">這可讓集合在追蹤使用者時，只有一個物件的軸會旋轉。</span><span class="sxs-lookup"><span data-stu-id="22837-132">This makes it so that only one axis of the object rotates as it follows the user.</span></span>
- <span data-ttu-id="22837-133">將所有軸上的區域位移設為 0。</span><span class="sxs-lookup"><span data-stu-id="22837-133">Set the local offset to 0 on all axes.</span></span> <span data-ttu-id="22837-134">將全局位移設為 x = 0、y =-0.1 及 z = 0.6。</span><span class="sxs-lookup"><span data-stu-id="22837-134">Set the World Offset to x = 0, y = -0.1 and z = 0.6.</span></span> <span data-ttu-id="22837-135">這會鎖定物件的移動，當使用者變更高度時，實體環境中的物件會維持固定高度，但同時仍會允許物件追蹤在環境中移動的使用者。</span><span class="sxs-lookup"><span data-stu-id="22837-135">This locks movement of the object such that when the user changes height, the object will remain at a fixed height in the physical environment, while still allowing it to follow the user as the user moves about the environment.</span></span> <span data-ttu-id="22837-136">您可以調整這些值來達到各種不同的行為。</span><span class="sxs-lookup"><span data-stu-id="22837-136">These values may be adjusted to achieve a wide range of behaviors.</span></span>
- <span data-ttu-id="22837-137">若您需要的追蹤行為是，按鈕只在使用者將頭轉動到一個程度時，才追蹤使用者的視線，則您可以選取 [針對全局位移使用角度跨步] 核取方塊 (請注意：此標題可能會在某些在畫面上遭到截斷，如下圖中所示)。例如，若要讓物件只在每 90 度時追蹤使用者，則將步階的數目設為 4 (在範例中以朝向左側的綠色箭號標記)。</span><span class="sxs-lookup"><span data-stu-id="22837-137">For a follow behavior whereby the buttons only follow the user’s view after the user turns his or her head sufficiently far, you could select the "Use Angle Stepping for world offset" checkbox (Note: This title may be truncated on some screens, as it is in the image below.) For example, to have the object follow the user only every 90 degrees, set the number of steps equal to 4 (marked by a green arrow in the example to the left).</span></span> 

![Lesson3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="22837-139">讓物件能夠追蹤追蹤的手部</span><span class="sxs-lookup"><span data-stu-id="22837-139">Enabling Objects to Follow Tracked Hands</span></span>

<span data-ttu-id="22837-140">在本節中，我們將設定先前建立的立方體遊戲物件，以使用 RadialView 解算器來跟隨追蹤的使用者手部。</span><span class="sxs-lookup"><span data-stu-id="22837-140">In this section, we will configure the cube game object previously created to follow the user’s tracked hands using the RadialView solver.</span></span>

1. <span data-ttu-id="22837-141">選取 BaseScene 階層中的立方體物件。</span><span class="sxs-lookup"><span data-stu-id="22837-141">Select the cube object in the BaseScene hierarchy.</span></span> <span data-ttu-id="22837-142">按一下偵測程式面板中的 [新增元件]。</span><span class="sxs-lookup"><span data-stu-id="22837-142">Click "add component" in the inspector panel.</span></span> 

![Lesson3 Chapter3 Step1im](images/Lesson3_Chapter3_step1im.PNG)

2. <span data-ttu-id="22837-144">在搜尋方塊中輸入 "RadialView"，然後選取 RadialView 元件來將其新增至立方體。</span><span class="sxs-lookup"><span data-stu-id="22837-144">Type in "RadialView" in the search box and select the RadialView component to add it to the cube.</span></span> <span data-ttu-id="22837-145">解算器處理常式元件也會自動新增至立方體。</span><span class="sxs-lookup"><span data-stu-id="22837-145">The solver handler component will also be automatically added to the cube.</span></span>

3. <span data-ttu-id="22837-146">將放射檢視變更為不要追蹤頭部，而是追蹤左手。</span><span class="sxs-lookup"><span data-stu-id="22837-146">Change the radial view to not follow the head but follow the left hand.</span></span> <span data-ttu-id="22837-147">在 [要參照的已追蹤物件] 選項旁選取下拉式功能表。</span><span class="sxs-lookup"><span data-stu-id="22837-147">Select the dropdown menu next to the "tracked object to reference" option.</span></span> <span data-ttu-id="22837-148">然後從功能表中選取 [左手]。</span><span class="sxs-lookup"><span data-stu-id="22837-148">Then select "hand joint left" from the menu.</span></span>

![Lesson3 Chapter3 Step3im](images/Lesson3_chapter3_step3im.PNG)

4. <span data-ttu-id="22837-150">選取手部後，您就可以選擇要讓立方體追蹤的手部位置。</span><span class="sxs-lookup"><span data-stu-id="22837-150">Once you select the hand joint, you can choose which part of the hand you want the cube to follow.</span></span> <span data-ttu-id="22837-151">在此範例中，我們要使用手腕。</span><span class="sxs-lookup"><span data-stu-id="22837-151">For this example, we are going to use the wrist.</span></span> <span data-ttu-id="22837-152">在 [追蹤的手部] 旁選取下拉式功能表，然後選取手腕。</span><span class="sxs-lookup"><span data-stu-id="22837-152">Next to the option "tracked hand joint" select the dropdown menu and select wrist.</span></span> 

![Lesson3 Chapter3 Step4im](images/Lesson3_chapter3_step4im.PNG)

5. <span data-ttu-id="22837-154">將最大和最小距離設定為 0，讓立方體與使用者手腕之間沒有任何距離。</span><span class="sxs-lookup"><span data-stu-id="22837-154">Set the maximum and minimum distances to 0 so that the cube will not have any distance between it and the user’s wrist.</span></span> <span data-ttu-id="22837-155">設定好之後，該立方體會完全配合手腕。</span><span class="sxs-lookup"><span data-stu-id="22837-155">Once set, the cube will be perfectly aligned with the wrist.</span></span> <span data-ttu-id="22837-156">此外，您也可以調整「參考方向」欄位來調整立方體的轉向行為 (例如，如果您想要允許物件隨著使用者的手腕旋轉，請將參考方向設定為 [跟隨追蹤物件轉向])</span><span class="sxs-lookup"><span data-stu-id="22837-156">You may also adjust the "Reference Direction" field to adjust the behavior of how the cube is oriented (e.g., if you would like to allow the object to rotate with the user's wrist, set the reference direction to "Orient with Tracked Object")</span></span>

![Lesson3 Chapter3 Step5im](images/Lesson3_chapter3_step5im.PNG)

### <a name="congratulations"></a><span data-ttu-id="22837-158">恭喜</span><span class="sxs-lookup"><span data-stu-id="22837-158">Congratulations</span></span>
<span data-ttu-id="22837-159">恭喜！</span><span class="sxs-lookup"><span data-stu-id="22837-159">Congratulations!</span></span> <span data-ttu-id="22837-160">在這一課中，您已了解如何使用 MRTK 解算器讓 UI 直覺式地追蹤使用者。</span><span class="sxs-lookup"><span data-stu-id="22837-160">In this lesson, you learned how to use the MRTK’s solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="22837-161">您也已了解如何將解算器連結到遊戲物件 (例如立方體)，以跟隨追蹤的使用者手部。</span><span class="sxs-lookup"><span data-stu-id="22837-161">You also learned how to attach a solver to a game object (i.e., cube) to follow the user’s tracked hands.</span></span> <span data-ttu-id="22837-162">若要深入了解 MRTK 隨附的這些解算器和其他解算器，歡迎您瀏覽 [MRTK 解算器文件頁面](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)。</span><span class="sxs-lookup"><span data-stu-id="22837-162">To learn more about these and other solvers included with the MRTK, feel free to visit the [MRTK solvers documentation page](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).</span></span>

[<span data-ttu-id="22837-163">下一課：3D 物件互動</span><span class="sxs-lookup"><span data-stu-id="22837-163">Next Lesson: 3D Object Interaction</span></span>](mrlearning-base-ch4.md)

