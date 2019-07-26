---
title: MR 學習基本模組 - 動態內容放置和解算器
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 401c667ef80042da9182b7f4e065dfd6884cf061
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485694"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a><span data-ttu-id="0df91-104">4.放置動態內容並使用解析器</span><span class="sxs-lookup"><span data-stu-id="0df91-104">4. Placing dynamic content and using solvers</span></span>

<span data-ttu-id="0df91-105">在 HoloLens 2 中，當全像投影以直覺方式追蹤使用者，並且透過讓互動流暢及簡潔的方式放置在實體環境中時，全像投影就會變得栩栩如生。</span><span class="sxs-lookup"><span data-stu-id="0df91-105">Holograms come to life in the HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="0df91-106">在本教學課程中, 我們將探索使用 MRTK 的可用放置工具動態地放置全息影像的方式, 也稱為解析器, 以解決複雜的空間放置案例。</span><span class="sxs-lookup"><span data-stu-id="0df91-106">In this tutorial, we explore ways to dynamically place holograms using the MRTK’s available placement tools, known as solvers for the way they solve complex spatial placement scenarios.</span></span> <span data-ttu-id="0df91-107">在 MRTK 中, 解析器是一種腳本和行為的系統, 可用來允許 UI 專案在場景中追蹤您、使用者或其他遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="0df91-107">In the MRTK, solvers are a system of scripts and behaviors that are used to allow UI elements to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="0df91-108">也可用來快速對齊特定位置，讓您的應用程式更具直覺性。</span><span class="sxs-lookup"><span data-stu-id="0df91-108">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span> 

## <a name="objectives"></a><span data-ttu-id="0df91-109">目標</span><span class="sxs-lookup"><span data-stu-id="0df91-109">Objectives</span></span>

* <span data-ttu-id="0df91-110">導入 MRTK 的解算器</span><span class="sxs-lookup"><span data-stu-id="0df91-110">Introduce the MRTK's solvers</span></span>
* <span data-ttu-id="0df91-111">使用解算器讓一組按鈕追蹤使用者</span><span class="sxs-lookup"><span data-stu-id="0df91-111">Use solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="0df91-112">使用解算器讓遊戲物件跟隨追蹤的使用者手部</span><span class="sxs-lookup"><span data-stu-id="0df91-112">Use solvers to have a game object follow the user's tracked hands</span></span>

## <a name="instructions"></a><span data-ttu-id="0df91-113">指示</span><span class="sxs-lookup"><span data-stu-id="0df91-113">Instructions</span></span>

### <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="0df91-114">MRTK 中的解算器位置</span><span class="sxs-lookup"><span data-stu-id="0df91-114">Location of solvers in the MRTK</span></span>
 <span data-ttu-id="0df91-115">若要尋找您專案中可用的解算器，請查看 MRTK SDK 資料夾 (MixedRealityToolkit.SDK 資料夾)，然後在公用程式資料夾底下，您會看到解算器資料夾，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="0df91-115">To find the available solvers in your project, look in the MRTK SDK folder (MixedRealityToolkit.SDK folder), then under the utilities folder you will see the solvers folder, as shown in the image below.</span></span>

![解算器](images/lesson3_chapter1_step1im.PNG)

><span data-ttu-id="0df91-117">注意:在這一課, 我們只會探討 Orbital 規劃求解和 RadialView 規劃求解的實施。</span><span class="sxs-lookup"><span data-stu-id="0df91-117">Note: In this lesson we will only go over the implementation of the Orbital solver and the RadialView solver.</span></span> <span data-ttu-id="0df91-118">若要深入了解 MRTK 中可用解算器的完整範圍，請瀏覽： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html</span><span class="sxs-lookup"><span data-stu-id="0df91-118">To learn more about the full range of solvers available in the MRTK, please visit: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html</span></span>

### <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="0df91-119">使用解算器追蹤使用者</span><span class="sxs-lookup"><span data-stu-id="0df91-119">Use a Solver to Follow the User</span></span>
<span data-ttu-id="0df91-120">本章的目標是要增強先前建立的按鈕集合, 使其遵循使用者的注視方向。</span><span class="sxs-lookup"><span data-stu-id="0df91-120">The goal of this chapter is to enhance the button collection that was previously created so that it follows the user’s gaze direction.</span></span> <span data-ttu-id="0df91-121">在舊版的 MRTK 和 HoloToolkit 中, 這稱為 tagalong 功能。</span><span class="sxs-lookup"><span data-stu-id="0df91-121">In previous version of the MRTK and HoloToolkit, this was referred to as a tagalong functionality.</span></span>

1. <span data-ttu-id="0df91-122">選取前一課中的「按鈕集合」父系物件。</span><span class="sxs-lookup"><span data-stu-id="0df91-122">Select the Button Collection parent object from the previous lesson.</span></span>

![Lesson3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. <span data-ttu-id="0df91-124">在 [偵測器] 面板中, 按一下 [加入元件] 按鈕, 然後搜尋 orbital。</span><span class="sxs-lookup"><span data-stu-id="0df91-124">In the Inspector panel, click the Add Component button and search for orbital.</span></span> <span data-ttu-id="0df91-125">orbital 元件應該會隨即出現。</span><span class="sxs-lookup"><span data-stu-id="0df91-125">The orbital component should appear.</span></span> <span data-ttu-id="0df91-126">將其選取，並將 orbital 元件新增至「按鈕集合」遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="0df91-126">Select it to add the orbital component to the Button Collection game object.</span></span>

![Lesson3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

><span data-ttu-id="0df91-128">注意:新增元件時，您會發現系統在作為必要元件的偵測程式索引標籤中，加入orbital 指令碼和解算器處理常式指令碼。</span><span class="sxs-lookup"><span data-stu-id="0df91-128">Note: When you add the component you will notice that the system adds the orbital script and the solver handler script in the inspector tab, which is a required component.</span></span> 

3. <span data-ttu-id="0df91-129">若要設定按鈕集合以遵循使用者, 我們需要執行下列調整 (請參閱下圖):</span><span class="sxs-lookup"><span data-stu-id="0df91-129">In order to configure the button collection to follow the user, we need to implement the following adjustments (refer to the image below):</span></span>
- <span data-ttu-id="0df91-130">在 Orbital 腳本中, 將 [方向類型] 下拉式清單設定為 [僅偏擺]。</span><span class="sxs-lookup"><span data-stu-id="0df91-130">In the Orbital script, set the Orientation Type drop-down list to Yaw Only.</span></span> <span data-ttu-id="0df91-131">這可讓集合在追蹤使用者時，只有一個物件的軸會旋轉。</span><span class="sxs-lookup"><span data-stu-id="0df91-131">This makes it so that only one axis of the object rotates as it follows the user.</span></span>
- <span data-ttu-id="0df91-132">將所有軸上的區域位移設為 0。</span><span class="sxs-lookup"><span data-stu-id="0df91-132">Set the local offset to 0 on all axes.</span></span> <span data-ttu-id="0df91-133">將全局位移設為 x = 0、y =-0.1 及 z = 0.6。</span><span class="sxs-lookup"><span data-stu-id="0df91-133">Set the World Offset to x = 0, y = -0.1 and z = 0.6.</span></span> <span data-ttu-id="0df91-134">這會鎖定物件的移動，當使用者變更高度時，實體環境中的物件會維持固定高度，但同時仍會允許物件追蹤在環境中移動的使用者。</span><span class="sxs-lookup"><span data-stu-id="0df91-134">This locks movement of the object such that when the user changes height, the object will remain at a fixed height in the physical environment, while still allowing it to follow the user as the user moves about the environment.</span></span> <span data-ttu-id="0df91-135">您可以調整這些值來達到各種不同的行為。</span><span class="sxs-lookup"><span data-stu-id="0df91-135">These values may be adjusted to achieve a wide range of behaviors.</span></span>
- <span data-ttu-id="0df91-136">針對下列行為, 讓按鈕只會在使用者將其移到最遠的位置之後追蹤使用者的觀點, 您可以選取 [為全球位移使用角度逐步執行] 核取方塊 (注意:此標題可能會在某些在畫面上遭到截斷，如下圖中所示)。例如，若要讓物件只在每 90 度時追蹤使用者，則將步階的數目設為 4 (在範例中以朝向左側的綠色箭號標記)。</span><span class="sxs-lookup"><span data-stu-id="0df91-136">For a follow behavior whereby the buttons only follow the user’s view after the user turns his or her head sufficiently far, you could select the Use Angle Stepping for world offset checkbox (Note: This title may be truncated on some screens, as it is in the image below.) For example, to have the object follow the user only every 90 degrees, set the number of steps equal to 4 (marked by a green arrow in the example to the left).</span></span> 

![Lesson3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="0df91-138">讓物件遵循追蹤的手</span><span class="sxs-lookup"><span data-stu-id="0df91-138">Enabling objects to follow tracked hands</span></span>

<span data-ttu-id="0df91-139">在本節中，我們將設定先前建立的立方體遊戲物件，以使用 RadialView 解算器來跟隨追蹤的使用者手部。</span><span class="sxs-lookup"><span data-stu-id="0df91-139">In this section, we will configure the cube game object previously created to follow the user’s tracked hands using the RadialView solver.</span></span>

1. <span data-ttu-id="0df91-140">選取 BaseScene 階層中的立方體物件。</span><span class="sxs-lookup"><span data-stu-id="0df91-140">Select the cube object in the BaseScene hierarchy.</span></span> <span data-ttu-id="0df91-141">按一下 [偵測器] 面板中的 [新增元件]。</span><span class="sxs-lookup"><span data-stu-id="0df91-141">Click Add Component in the Inspector panel.</span></span> 

![Lesson3 Chapter3 Step1im](images/Lesson3_Chapter3_step1im.PNG)

2. <span data-ttu-id="0df91-143">在搜尋方塊中輸入 RadialView, 然後選取 [RadialView] 元件, 將它加入至 cube。</span><span class="sxs-lookup"><span data-stu-id="0df91-143">Type in RadialView in the search box and select the RadialView component to add it to the cube.</span></span> <span data-ttu-id="0df91-144">解算器處理常式元件也會自動新增至立方體。</span><span class="sxs-lookup"><span data-stu-id="0df91-144">The solver handler component will also be automatically added to the cube.</span></span>

3. <span data-ttu-id="0df91-145">將放射檢視變更為不要追蹤頭部，而是追蹤左手。</span><span class="sxs-lookup"><span data-stu-id="0df91-145">Change the radial view to not follow the head but follow the left hand.</span></span> <span data-ttu-id="0df91-146">選取 [要參考的追蹤物件] 選項旁邊的下拉式功能表。</span><span class="sxs-lookup"><span data-stu-id="0df91-146">Select the dropdown menu next to the Tracked Object to Reference option.</span></span> <span data-ttu-id="0df91-147">然後選取功能表中的 [向左接點]。</span><span class="sxs-lookup"><span data-stu-id="0df91-147">Then select Hand Joint Left from the menu.</span></span>

![Lesson3 Chapter3 Step3im](images/Lesson3_chapter3_step3im.PNG)

4. <span data-ttu-id="0df91-149">選取手部後，您就可以選擇要讓立方體追蹤的手部位置。</span><span class="sxs-lookup"><span data-stu-id="0df91-149">Once you select the hand joint, you can choose which part of the hand you want the cube to follow.</span></span> <span data-ttu-id="0df91-150">在此範例中，我們要使用手腕。</span><span class="sxs-lookup"><span data-stu-id="0df91-150">For this example, we are going to use the wrist.</span></span> <span data-ttu-id="0df91-151">在 [追蹤的接頭] 旁選取下拉式功能表, 然後選取 [手腕]。</span><span class="sxs-lookup"><span data-stu-id="0df91-151">Next to the option Tracked Hand Joint select the dropdown menu and select Wrist.</span></span> 

![Lesson3 Chapter3 Step4im](images/Lesson3_chapter3_step4im.PNG)

5. <span data-ttu-id="0df91-153">將最大和最小距離設定為 0，讓立方體與使用者手腕之間沒有任何距離。</span><span class="sxs-lookup"><span data-stu-id="0df91-153">Set the maximum and minimum distances to 0 so that the cube will not have any distance between it and the user’s wrist.</span></span> <span data-ttu-id="0df91-154">設定好之後，該立方體會完全配合手腕。</span><span class="sxs-lookup"><span data-stu-id="0df91-154">Once set, the cube will be perfectly aligned with the wrist.</span></span> <span data-ttu-id="0df91-155">您也可以調整 [參考方向] 欄位來調整 cube 的導向行為, 例如, 如果您想要允許物件以使用者的手腕旋轉, 請將參考方向設定為 [追蹤物件的方向]。</span><span class="sxs-lookup"><span data-stu-id="0df91-155">You might also adjust the Reference Direction field to adjust the behavior of how the cube is oriented, such as if you want to allow the object to rotate with the user's wrist by setting the reference direction to Orient with Tracked Object.</span></span>

![Lesson3 Chapter3 Step5im](images/Lesson3_chapter3_step5im.PNG)

## <a name="congratulations"></a><span data-ttu-id="0df91-157">恭喜！</span><span class="sxs-lookup"><span data-stu-id="0df91-157">Congratulations</span></span>
<span data-ttu-id="0df91-158">在本教學課程中, 您已瞭解如何使用 MRTK 的解析器, 讓 UI 直覺地跟隨使用者。</span><span class="sxs-lookup"><span data-stu-id="0df91-158">In this tutorial, you learned how to use the MRTK’s solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="0df91-159">您也已了解如何將解算器連結到遊戲物件 (例如立方體)，以跟隨追蹤的使用者手部。</span><span class="sxs-lookup"><span data-stu-id="0df91-159">You also learned how to attach a solver to a game object (i.e., cube) to follow the user’s tracked hands.</span></span> <span data-ttu-id="0df91-160">若要深入了解 MRTK 隨附的這些解算器和其他解算器，歡迎您瀏覽 [MRTK 解算器文件頁面](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)。</span><span class="sxs-lookup"><span data-stu-id="0df91-160">To learn more about these and other solvers included with the MRTK, feel free to visit the [MRTK solvers documentation page](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).</span></span>

[<span data-ttu-id="0df91-161">下一課：5.  與 3D 物件互動</span><span class="sxs-lookup"><span data-stu-id="0df91-161">Next Lesson: 5.    Interacting with 3D objects</span></span>](mrlearning-base-ch4.md)

