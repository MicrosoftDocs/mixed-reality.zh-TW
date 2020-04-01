---
title: 入門教學課程 - 4。 放置動態內容並使用解算器
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 8a85ab560d0e6b36b589970b4d5b8a441ed2bbe2
ms.sourcegitcommit: 536fd45b48a70bbeca1454cef517ae007225e533
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80362035"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a><span data-ttu-id="94b28-105">4.放置動態內容並使用解算器</span><span class="sxs-lookup"><span data-stu-id="94b28-105">4. Placing dynamic content and using Solvers</span></span>
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

<span data-ttu-id="94b28-106">在 HoloLens 2 中，當全像投影以直覺方式追蹤使用者，並且透過讓互動流暢及簡潔的方式放置在實體環境中時，全像投影就會變得栩栩如生。</span><span class="sxs-lookup"><span data-stu-id="94b28-106">Holograms come to life in HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="94b28-107">在本教學課程中，我們會探索如何使用 MRTK 的可用放置工具 (也就是解算器) 來動態地放置全像投影，以解決複雜的空間放置案例。</span><span class="sxs-lookup"><span data-stu-id="94b28-107">In this tutorial, we explore ways to dynamically place holograms using the MRTK's available placement tools, known as Solvers, to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="94b28-108">在 MRTK 中，解算器是指令碼和行為的系統，用來允許 UI 元素在場景中追蹤您、使用者或其他遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="94b28-108">In the MRTK, Solvers are a system of scripts and behaviors that are used to allow UI elements to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="94b28-109">也可用來快速對齊特定位置，讓您的應用程式更具直覺性。</span><span class="sxs-lookup"><span data-stu-id="94b28-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="94b28-110">目標</span><span class="sxs-lookup"><span data-stu-id="94b28-110">Objectives</span></span>

* <span data-ttu-id="94b28-111">導入 MRTK 的解算器</span><span class="sxs-lookup"><span data-stu-id="94b28-111">Introduce the MRTK's Solvers</span></span>
* <span data-ttu-id="94b28-112">使用解算器讓一組按鈕追蹤使用者</span><span class="sxs-lookup"><span data-stu-id="94b28-112">Use Solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="94b28-113">使用解算器讓遊戲物件跟隨追蹤的使用者手部</span><span class="sxs-lookup"><span data-stu-id="94b28-113">Use Solvers to have a game object follow the user's tracked hands</span></span>

## <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="94b28-114">MRTK 中的解算器位置</span><span class="sxs-lookup"><span data-stu-id="94b28-114">Location of Solvers in the MRTK</span></span>

 <span data-ttu-id="94b28-115">MRTK 的解算器位於 MRTK SDK 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="94b28-115">The MRTK's Solvers are located in the MRTK SDK folder.</span></span> <span data-ttu-id="94b28-116">若要查看專案中的可用解算器，請在 [專案] 視窗中瀏覽至 [資產]   > [MixedRealityToolkit.SDK]   > [功能]   > [公用程式]   > [解算器]  ：</span><span class="sxs-lookup"><span data-stu-id="94b28-116">To see the available Solvers in your project, in the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **Features** > **Utilities** > **Solvers**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

<span data-ttu-id="94b28-118">在本教學課程中，我們將檢閱「軌道解算器」和「光線檢視解算器」的實作。</span><span class="sxs-lookup"><span data-stu-id="94b28-118">In this tutorial, we will review the implementation of the Orbital Solver and the Radial View Solver.</span></span> <span data-ttu-id="94b28-119">若要深入了解 MRTK 中可用的完整解算器範圍，您可以瀏覽 [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[解算器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)指南。</span><span class="sxs-lookup"><span data-stu-id="94b28-119">To learn more about the full range of Solvers available in the MRTK, you can visit the the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="94b28-120">使用解算器追蹤使用者</span><span class="sxs-lookup"><span data-stu-id="94b28-120">Use a Solver to follow the user</span></span>
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

<span data-ttu-id="94b28-121">在本節中，您將增強上一個教學課程中建立的按鈕集合，使其遵循使用者的注視方向。</span><span class="sxs-lookup"><span data-stu-id="94b28-121">In this section, you will enhance the button collection you created in the previous tutorial so it follows the user's gaze direction.</span></span> <span data-ttu-id="94b28-122">此外，您也會設定解算器，讓按鈕集合一律具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="94b28-122">Additionally, you will also configure the Solver so the button collection is always:</span></span>

* <span data-ttu-id="94b28-123">對使用者的閱讀方向進行平行旋轉，以自然地由左向右閱讀</span><span class="sxs-lookup"><span data-stu-id="94b28-123">Rotated parallel to the user's reading direction, for natural left to right reading</span></span>
* <span data-ttu-id="94b28-124">位置低於使用者的水平注視方向，使其不會阻礙您稍後將在本教學課程中新增的其他物件</span><span class="sxs-lookup"><span data-stu-id="94b28-124">Positioned below the user horizontal gaze direction, so it's not obstructing the other objects you will add later in this tutorial</span></span>
* <span data-ttu-id="94b28-125">位置距離使用者大約半個手臂長，讓使用者可以輕鬆按下按鈕</span><span class="sxs-lookup"><span data-stu-id="94b28-125">Positioned approximately a half arm's-length from the user, so the buttons can easily be pressed</span></span>

<span data-ttu-id="94b28-126">為此，您將使用**軌道解算器**，將物件鎖定在特定位置，並從參考物件進行位移。</span><span class="sxs-lookup"><span data-stu-id="94b28-126">For this, you will use the **Orbital Solver** which locks the object to a specified position and offset from the referenced object.</span></span>

### <a name="1-add-the-orbital-solver"></a><span data-ttu-id="94b28-127">1.新增軌道解算器</span><span class="sxs-lookup"><span data-stu-id="94b28-127">1. Add the Orbital Solver</span></span>

<span data-ttu-id="94b28-128">在 [階層] 視窗中選取 **ButtonCollection** 物件，然後在 [偵測器] 視窗中使用 [新增元件]  按鈕來將 **Orbital (指令碼)** 元件新增至 ButtonCollection 物件。</span><span class="sxs-lookup"><span data-stu-id="94b28-128">In the Hierarchy window, select the **ButtonCollection** object, then in the Inspector window, use the **Add Component** button to add the **Orbital (Script)** component to the ButtonCollection object.</span></span>

> [!NOTE]
> <span data-ttu-id="94b28-129">當您加入解算器時 (在此案例中為 Orbital (指令碼) 元件)，Solver Handler (指令碼) 元件也會自動加入，因為解算器需要此元件。</span><span class="sxs-lookup"><span data-stu-id="94b28-129">When you add a Solver, in this case the Orbital (Script) component, the Solver Handler (Script) component is automatically added because it is required by the Solver.</span></span>

### <a name="2-configure-the-orbital-solver"></a><span data-ttu-id="94b28-130">2.設定軌道解算器</span><span class="sxs-lookup"><span data-stu-id="94b28-130">2. Configure the Orbital Solver</span></span>

<span data-ttu-id="94b28-131">設定 **Solver Handler (指令碼)** 元件：</span><span class="sxs-lookup"><span data-stu-id="94b28-131">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="94b28-132">確認**追蹤的目標類型**已設定為 [標頭] </span><span class="sxs-lookup"><span data-stu-id="94b28-132">Verify that **Tracked Target Type** is set to **Head**</span></span>

<span data-ttu-id="94b28-133">設定 **Orbital (指令碼)** 元件：</span><span class="sxs-lookup"><span data-stu-id="94b28-133">Configure the **Orbital (Script)** component:</span></span>

* <span data-ttu-id="94b28-134">確認**方向類型**已設定為 [跟隨追蹤的物件] </span><span class="sxs-lookup"><span data-stu-id="94b28-134">Verify that **Orientation Type** is set to **Follow Tracked Object**</span></span>
* <span data-ttu-id="94b28-135">將**局部位移**重設為 X = 0、Y = 0、Z = 0</span><span class="sxs-lookup"><span data-stu-id="94b28-135">Reset **Local Offset** to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="94b28-136">將**全局位移**變更為 X = 0，Y = -0.4，Z = 0.3</span><span class="sxs-lookup"><span data-stu-id="94b28-136">Change **World Offset** to X = 0, Y = -0.4, Z = 0.3</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a><span data-ttu-id="94b28-138">3.使用編輯器內模擬來測試軌道解算器</span><span class="sxs-lookup"><span data-stu-id="94b28-138">3. Test the Orbital Solver using the in-editor simulation</span></span>

<span data-ttu-id="94b28-139">按下 [開始遊戲] 按鈕進入遊戲模式，並按住滑鼠右鍵來旋轉您的注視方向，同時注意下列事項：</span><span class="sxs-lookup"><span data-stu-id="94b28-139">Press the Play button to enter Game mode and press and hold the right mouse button to rotate your gaze direction, and notice the following:</span></span>

* <span data-ttu-id="94b28-140">ButtonCollection 的變形位置現在是由解算器設定所驅動</span><span class="sxs-lookup"><span data-stu-id="94b28-140">The ButtonCollection's Transform Position is now driven by the Solver settings</span></span>
* <span data-ttu-id="94b28-141">不受解算器影響的立方體仍會在相同位置</span><span class="sxs-lookup"><span data-stu-id="94b28-141">The Cube, which is not affected by the Solver, remains in the same position</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> <span data-ttu-id="94b28-143">如果您沒有在場景視窗中看到相機光線，請確定您已啟用 [Gizmos] 功能表。</span><span class="sxs-lookup"><span data-stu-id="94b28-143">If you don't see the camera ray in your Scene window, make sure your Gizmos menu is enabled.</span></span> <span data-ttu-id="94b28-144">若要深入了解 Gizmos 功能表，以及如何使用其來最佳化場景檢視，您可以造訪 Unity 的 <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos 功能表</a>文件。</span><span class="sxs-lookup"><span data-stu-id="94b28-144">To learn more about the Gizmos menu and how you can use it to optimize your scene view, you can visit Unity's <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos menu</a> documentation.</span></span>
>
> <span data-ttu-id="94b28-145">若要並排顯示場景和遊戲視窗 (如上圖所示)，只需將遊戲視窗拖曳至場景視窗的右邊即可。</span><span class="sxs-lookup"><span data-stu-id="94b28-145">To display your Scene and Game window side by side as shown in the image above, simply drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="94b28-146">若要深入了解如何自訂您的工作區，您可以造訪 Unity 的<a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">自訂您的工作區</a>文件。</span><span class="sxs-lookup"><span data-stu-id="94b28-146">To learn more about customizing your workspace, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

## <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="94b28-147">讓物件能夠跟隨追蹤的手部</span><span class="sxs-lookup"><span data-stu-id="94b28-147">Enabling objects to follow tracked hands</span></span>

<span data-ttu-id="94b28-148">在本節中，您將設定上一個教學課程中建立的立方體物件，使其跟隨使用者的追蹤手部，特別是右手腕。</span><span class="sxs-lookup"><span data-stu-id="94b28-148">In this section, you will configure the Cube object you created in the previous tutorial so it follows the user's tracked hands, specifically the right hand wrist.</span></span> <span data-ttu-id="94b28-149">此外，您也會設定解算器，讓立方體：</span><span class="sxs-lookup"><span data-stu-id="94b28-149">Additionally, you will also configure the Solver so the cube:</span></span>

* <span data-ttu-id="94b28-150">透過使用者的手部旋轉來變更其方向</span><span class="sxs-lookup"><span data-stu-id="94b28-150">Changes it's orientation with the user's hand rotation</span></span>
* <span data-ttu-id="94b28-151">放在使用者的手腕上</span><span class="sxs-lookup"><span data-stu-id="94b28-151">Positioned on the user's wrist</span></span>

<span data-ttu-id="94b28-152">為此，您將使用**光線檢視解算器**，將物件保留在由參考物件所投射的檢視圓錐中。</span><span class="sxs-lookup"><span data-stu-id="94b28-152">For this, you will use the **Radial View Solver** which keeps the object within a view cone cast by the referenced object.</span></span>

### <a name="1-add-the-radial-view-solver"></a><span data-ttu-id="94b28-153">1.新增光線檢視解算器</span><span class="sxs-lookup"><span data-stu-id="94b28-153">1. Add the Radial View Solver</span></span>

<span data-ttu-id="94b28-154">在 [階層] 視窗中，選取**立方體**子物件，然後在 [偵測器] 視窗中，使用 [新增元件]  按鈕來新增 **Radial View (指令碼)** 元件的立方體物件。</span><span class="sxs-lookup"><span data-stu-id="94b28-154">In the Hierarchy window, select the **Cube** object, then in the Inspector window, use the **Add Component** button to add the **Radial View (Script)** component Cube object.</span></span>

### <a name="2-configure-the-radial-view-solver"></a><span data-ttu-id="94b28-155">2.設定光線檢視解算器</span><span class="sxs-lookup"><span data-stu-id="94b28-155">2. Configure the Radial View Solver</span></span>

<span data-ttu-id="94b28-156">設定 **Solver Handler (指令碼)** 元件：</span><span class="sxs-lookup"><span data-stu-id="94b28-156">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="94b28-157">將**追蹤的目標類型**變更為**手部關節**</span><span class="sxs-lookup"><span data-stu-id="94b28-157">Change **Tracked Target Type** to **Hand Joint**</span></span>
* <span data-ttu-id="94b28-158">將**追蹤的手部**變更為**右手**</span><span class="sxs-lookup"><span data-stu-id="94b28-158">Change **Tracked Handness** to **Right**</span></span>
* <span data-ttu-id="94b28-159">將**追蹤的手部關節**變更為**手腕**</span><span class="sxs-lookup"><span data-stu-id="94b28-159">Change **Tracked Hand Joint** to **Wrist**</span></span>

<span data-ttu-id="94b28-160">設定 **Radial View (指令碼)** 元件：</span><span class="sxs-lookup"><span data-stu-id="94b28-160">Configure the **Radial View (Script)** component:</span></span>

* <span data-ttu-id="94b28-161">將**參考方向**變更為**物件導向**，然後核取 [指向參考方向]  核取方塊</span><span class="sxs-lookup"><span data-stu-id="94b28-161">Change **Reference Direction** to **Object Oriented**, then check the **Orient To Reference Direction** checkbox</span></span>
* <span data-ttu-id="94b28-162">將**最小距離**和 **最大距離**變更為 0</span><span class="sxs-lookup"><span data-stu-id="94b28-162">Change **Min Distance** and **Max Distance** to 0</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a><span data-ttu-id="94b28-164">3.使用編輯器內模擬來測試光線檢視解算器</span><span class="sxs-lookup"><span data-stu-id="94b28-164">3. Test the Radial View Solver using the in-editor simulation</span></span>

<span data-ttu-id="94b28-165">按下 [開始遊戲] 按鈕進入遊戲模式，然後按住空格鍵以顯示手部。</span><span class="sxs-lookup"><span data-stu-id="94b28-165">Press the Play button to enter Game mode and then press and hold the spacebar to bring up the hand.</span></span> <span data-ttu-id="94b28-166">四處移動滑鼠游標來移動手部，然後按住滑鼠左鍵以旋轉手部：</span><span class="sxs-lookup"><span data-stu-id="94b28-166">Move the mouse cursor around to move the hand, and click and hold the left mouse button to rotate the hand:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a><span data-ttu-id="94b28-168">恭喜！</span><span class="sxs-lookup"><span data-stu-id="94b28-168">Congratulations</span></span>

<span data-ttu-id="94b28-169">在此教學課程中，您已了解如何使用 MRTK 解算器讓 UI 直覺式地追蹤使用者。</span><span class="sxs-lookup"><span data-stu-id="94b28-169">In this tutorial, you learned how to use the MRTK's solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="94b28-170">您也已了解如何將解算器連結到物件 (例如立方體)，以跟隨追蹤的使用者手部。</span><span class="sxs-lookup"><span data-stu-id="94b28-170">You also learned how to attach a Solver to an object (i.e., cube) to follow the user's tracked hands.</span></span> <span data-ttu-id="94b28-171">若要深入了解 MRTK 隨附的這些解算器和其他解算器，您可以瀏覽 [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)的[解算器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)指南。</span><span class="sxs-lookup"><span data-stu-id="94b28-171">To learn more about these and other solvers included with the MRTK,  you can visit the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

[<span data-ttu-id="94b28-172">下一個教學課程：5.與 3D 物件互動</span><span class="sxs-lookup"><span data-stu-id="94b28-172">Next Tutorial: 5. Interacting with 3D objects</span></span>](mrlearning-base-ch4.md)
