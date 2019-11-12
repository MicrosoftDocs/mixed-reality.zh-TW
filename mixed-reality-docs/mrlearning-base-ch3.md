---
title: 使用者入門教學課程-4。 放置動態內容並使用解析器
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 32a77d6032335ab3ae769b85c5f947440658743f
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913569"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a><span data-ttu-id="9412f-105">4. 放置動態內容並使用解析器</span><span class="sxs-lookup"><span data-stu-id="9412f-105">4. Placing dynamic content and using solvers</span></span>

<span data-ttu-id="9412f-106">在 HoloLens 2 中，當您以直覺方式追蹤使用者，並將其放在實體環境中，讓互動順暢且簡潔時，就能開始使用全息。</span><span class="sxs-lookup"><span data-stu-id="9412f-106">Holograms come to life in HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="9412f-107">在本教學課程中，我們會探索如何使用 MRTK 的可用位置工具（稱為解析器）來動態地放置全息影像，以解決複雜的空間放置案例。</span><span class="sxs-lookup"><span data-stu-id="9412f-107">In this tutorial, we explore ways to dynamically place holograms using the MRTK’s available placement tools (known as solvers) to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="9412f-108">在 MRTK 中，解析器是一種腳本和行為的系統，可用來允許 UI 專案在場景中追蹤您、使用者或其他遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="9412f-108">In the MRTK, solvers are a system of scripts and behaviors that are used to allow UI elements to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="9412f-109">也可用來快速對齊特定位置，讓您的應用程式更具直覺性。</span><span class="sxs-lookup"><span data-stu-id="9412f-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="9412f-110">目標</span><span class="sxs-lookup"><span data-stu-id="9412f-110">Objectives</span></span>

* <span data-ttu-id="9412f-111">導入 MRTK 的解算器</span><span class="sxs-lookup"><span data-stu-id="9412f-111">Introduce the MRTK's solvers</span></span>
* <span data-ttu-id="9412f-112">使用解算器讓一組按鈕追蹤使用者</span><span class="sxs-lookup"><span data-stu-id="9412f-112">Use solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="9412f-113">使用解算器讓遊戲物件跟隨追蹤的使用者手部</span><span class="sxs-lookup"><span data-stu-id="9412f-113">Use solvers to have a game object follow the user's tracked hands</span></span>

## <a name="instructions"></a><span data-ttu-id="9412f-114">指示</span><span class="sxs-lookup"><span data-stu-id="9412f-114">Instructions</span></span>

### <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="9412f-115">MRTK 中的解算器位置</span><span class="sxs-lookup"><span data-stu-id="9412f-115">Location of solvers in the MRTK</span></span>

 <span data-ttu-id="9412f-116">若要在您的專案中尋找可用的解析器，請查看 MRTK SDK 資料夾（MixedRealityToolkit. SDK 資料夾）。</span><span class="sxs-lookup"><span data-stu-id="9412f-116">To find the available solvers in your project, look in the MRTK SDK folder (MixedRealityToolkit.SDK folder).</span></span> <span data-ttu-id="9412f-117">在 [公用程式] 資料夾底下，您會看到 [解析器] 資料夾，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="9412f-117">Under the utilities folder, you will see the solvers folder, as shown in the image below.</span></span>

![解算器](images/lesson3_chapter1_step1im.PNG)

>[!NOTE]
><span data-ttu-id="9412f-119">在這一課，我們只會探討 Orbital 規劃求解和 RadialView 規劃求解的執行。</span><span class="sxs-lookup"><span data-stu-id="9412f-119">In this lesson, we will only review the implementation of the Orbital solver and the RadialView solver.</span></span> <span data-ttu-id="9412f-120">若要深入瞭解 MRTK 中提供的完整解析器範圍，請造訪： [https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)</span><span class="sxs-lookup"><span data-stu-id="9412f-120">To learn more about the full range of solvers available in the MRTK, visit: [https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)</span></span>

### <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="9412f-121">使用解算器追蹤使用者</span><span class="sxs-lookup"><span data-stu-id="9412f-121">Use a Solver to Follow the User</span></span>

<span data-ttu-id="9412f-122">本章的目標是要增強先前建立的按鈕集合，使其遵循使用者的注視方向。</span><span class="sxs-lookup"><span data-stu-id="9412f-122">The goal of this chapter is to enhance the button collection that was previously created so that it follows the user’s gaze direction.</span></span> <span data-ttu-id="9412f-123">在先前版本的 MRTK 和 HoloToolkit 中，這稱為 tagalong 功能。</span><span class="sxs-lookup"><span data-stu-id="9412f-123">In the previous version of the MRTK and HoloToolkit, this was referred to as a tagalong functionality.</span></span>

1. <span data-ttu-id="9412f-124">選取前一課中的「按鈕集合」父系物件。</span><span class="sxs-lookup"><span data-stu-id="9412f-124">Select the Button Collection parent object from the previous lesson.</span></span>

    ![Lesson3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. <span data-ttu-id="9412f-126">在 [偵測器] 面板中，按一下 [加入元件] 按鈕，然後搜尋 orbital。</span><span class="sxs-lookup"><span data-stu-id="9412f-126">In the Inspector panel, click the Add Component button and search for orbital.</span></span> <span data-ttu-id="9412f-127">應該會出現 Orbital 元件。</span><span class="sxs-lookup"><span data-stu-id="9412f-127">The Orbital component should appear.</span></span> <span data-ttu-id="9412f-128">選取它以將 Orbital 元件新增至按鈕集合遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="9412f-128">Select it to add the Orbital component to the Button Collection game object.</span></span>

    ![Lesson3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

    >[!NOTE]
    ><span data-ttu-id="9412f-130">當您新增 Orbital 元件時，您會注意到系統也會新增 SolverHandler 元件，這是必要的元件。</span><span class="sxs-lookup"><span data-stu-id="9412f-130">When you add the Orbital component you will notice that the system also adds the SolverHandler component, which is a required component.</span></span>

3. <span data-ttu-id="9412f-131">若要設定按鈕集合以遵循使用者，我們需要執行下列調整（請參閱下圖）：</span><span class="sxs-lookup"><span data-stu-id="9412f-131">In order to configure the Button Collection to follow the user, we need to implement the following adjustments (refer to the image below):</span></span>
    * <span data-ttu-id="9412f-132">在 Orbital 腳本中，將 [方向類型] 下拉式清單設定為 [僅偏擺]。</span><span class="sxs-lookup"><span data-stu-id="9412f-132">In the Orbital script, set the Orientation Type drop-down list to Yaw Only.</span></span> <span data-ttu-id="9412f-133">這可讓集合在追蹤使用者時，只有一個物件的軸會旋轉。</span><span class="sxs-lookup"><span data-stu-id="9412f-133">This makes it so that only one axis of the object rotates as it follows the user.</span></span>
    * <span data-ttu-id="9412f-134">將所有軸上的區域位移設為 0。</span><span class="sxs-lookup"><span data-stu-id="9412f-134">Set the local offset to 0 on all axes.</span></span> <span data-ttu-id="9412f-135">將 [世界位移] 設定為 x = 0、y =-0.1 和 z = 0.6。</span><span class="sxs-lookup"><span data-stu-id="9412f-135">Set the World Offset to x = 0, y = -0.1, and z = 0.6.</span></span> <span data-ttu-id="9412f-136">這會鎖定物件的移動，因此當使用者變更高度時，物件在實體環境中會維持固定的高度，而當使用者移至環境時，仍允許它追蹤使用者。</span><span class="sxs-lookup"><span data-stu-id="9412f-136">This locks movement of the object so that when the user changes height, the object will remain at a fixed height in the physical environment, while still allowing it to follow the user as the user moves about the environment.</span></span> <span data-ttu-id="9412f-137">您可以調整這些值來達到各種不同的行為。</span><span class="sxs-lookup"><span data-stu-id="9412f-137">These values may be adjusted to achieve a wide range of behaviors.</span></span>
    * <span data-ttu-id="9412f-138">針對下列行為，讓按鈕只會在使用者將其標題設為最遠之後追蹤使用者的觀點，您可以選取 [為全球位移使用角度逐步執行] 核取方塊（注意：在某些畫面上，此標題可能會被截斷，如下圖所示）。例如，若要讓物件只在每隔90度之後追蹤使用者，請將步驟數設定為等於4（以下列範例中的綠色箭號標示）。</span><span class="sxs-lookup"><span data-stu-id="9412f-138">For a follow behavior whereby the buttons only follow the user’s view after the user turns his or her head sufficiently far, you could select the Use Angle Stepping For World Offset checkbox (Note: This title may be truncated on some screens, as it is in the image below.) For example, to have the object follow the user only every 90 degrees, set the number of steps equal to 4 (marked by a green arrow in the example below).</span></span>

    ![Lesson3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="9412f-140">讓物件遵循追蹤的手</span><span class="sxs-lookup"><span data-stu-id="9412f-140">Enabling objects to follow tracked hands</span></span>

<span data-ttu-id="9412f-141">在本節中，我們將設定先前建立的 Cube 遊戲物件，以遵循使用 RadialView 求解的使用者追蹤手。</span><span class="sxs-lookup"><span data-stu-id="9412f-141">In this section, we will configure the Cube game object previously created to follow the user’s tracked hands using the RadialView solver.</span></span>

1. <span data-ttu-id="9412f-142">選取 BaseScene 階層中的 Cube 物件。</span><span class="sxs-lookup"><span data-stu-id="9412f-142">Select the Cube object in the BaseScene hierarchy.</span></span> <span data-ttu-id="9412f-143">按一下 [偵測器] 面板中的 [新增元件]。</span><span class="sxs-lookup"><span data-stu-id="9412f-143">Click Add Component in the Inspector panel.</span></span> <span data-ttu-id="9412f-144">在搜尋方塊中輸入 RadialView，然後選取 [RadialView] 元件，將它加入至 cube。</span><span class="sxs-lookup"><span data-stu-id="9412f-144">Type in RadialView in the search box and select the RadialView component to add it to the cube.</span></span> <span data-ttu-id="9412f-145">SolverHandler 元件也會自動加入至 cube。</span><span class="sxs-lookup"><span data-stu-id="9412f-145">The SolverHandler component will also be automatically added to the cube.</span></span>

    ![mrlearning-base-ch3-3-step3 .png](images/mrlearning-base-ch3-3-step1.png)

2. <span data-ttu-id="9412f-147">若要將 RadialView 變更為追蹤，而不是標頭，請選取 [追蹤的目標型別] 選項旁邊的下拉式功能表，然後從功能表中選取 [手形聯合]。</span><span class="sxs-lookup"><span data-stu-id="9412f-147">To change the RadialView to follow a hand instead of the head, select the dropdown menu next to the Tracked Target Type option and select Hand Joint from the menu.</span></span>

    ![mrlearning-base-ch3-3-step2 .png](images/mrlearning-base-ch3-3-step2a.png)

    <span data-ttu-id="9412f-149">您現在會看到兩個新選項： [已追蹤] Handness 類型和 [已追蹤]。</span><span class="sxs-lookup"><span data-stu-id="9412f-149">You will now see two new options, Tracked Handness Type and Tracked Hand Joint.</span></span> <span data-ttu-id="9412f-150">在此範例中，您會讓 RadialView 遵循左側的手腕，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="9412f-150">For this example, you will have the RadialView follow the wrist of the left hand as shown in the image below.</span></span>

    ![mrlearning-base-ch3-3-step2b .png](images/mrlearning-base-ch3-3-step2b.png)

3. <span data-ttu-id="9412f-152">將星形視圖的最大和最小距離設定為0，讓 cube 與使用者手腕之間不會有任何距離。</span><span class="sxs-lookup"><span data-stu-id="9412f-152">Set the maximum and minimum distances of the Radial View to 0 so that the cube will not have any distance between it and the user’s wrist.</span></span> <span data-ttu-id="9412f-153">設定好之後，該立方體會完全配合手腕。</span><span class="sxs-lookup"><span data-stu-id="9412f-153">Once set, the cube will be perfectly aligned with the wrist.</span></span> <span data-ttu-id="9412f-154">您也可以調整 [參考方向] 欄位來調整 cube 的導向行為，例如，如果您想要允許物件以使用者的手腕旋轉，請將參考方向設定為 [追蹤物件的方向]。</span><span class="sxs-lookup"><span data-stu-id="9412f-154">You might also adjust the Reference Direction field to adjust the behavior of how the cube is oriented, such as if you want to allow the object to rotate with the user's wrist by setting the Reference Direction to Orient with Tracked Object.</span></span>

    ![mrlearning-base-ch3-3-step3 .png](images/mrlearning-base-ch3-3-step3.png)

## <a name="congratulations"></a><span data-ttu-id="9412f-156">恭喜！</span><span class="sxs-lookup"><span data-stu-id="9412f-156">Congratulations</span></span>

<span data-ttu-id="9412f-157">在本教學課程中，您已瞭解如何使用 MRTK 的解析器，讓 UI 直覺地跟隨使用者。</span><span class="sxs-lookup"><span data-stu-id="9412f-157">In this tutorial, you learned how to use the MRTK’s solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="9412f-158">您也已了解如何將解算器連結到遊戲物件 (例如立方體)，以跟隨追蹤的使用者手部。</span><span class="sxs-lookup"><span data-stu-id="9412f-158">You also learned how to attach a solver to a game object (i.e., cube) to follow the user’s tracked hands.</span></span> <span data-ttu-id="9412f-159">若要深入了解 MRTK 隨附的這些解算器和其他解算器，歡迎您瀏覽 [MRTK 解算器文件頁面](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)。</span><span class="sxs-lookup"><span data-stu-id="9412f-159">To learn more about these and other solvers included with the MRTK, feel free to visit the [MRTK solvers documentation page](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).</span></span>

[<span data-ttu-id="9412f-160">下一課： 5. 與3D 物件互動</span><span class="sxs-lookup"><span data-stu-id="9412f-160">Next Lesson: 5. Interacting with 3D objects</span></span>](mrlearning-base-ch4.md)
