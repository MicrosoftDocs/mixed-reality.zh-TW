---
title: 使用者入門教學課程-4。 放置動態內容並使用解析器
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 8275d5a97d7827d34ed3926cabe4032cc7f4cfac
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129309"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a><span data-ttu-id="626d3-105">4. 放置動態內容並使用解析器</span><span class="sxs-lookup"><span data-stu-id="626d3-105">4. Placing dynamic content and using Solvers</span></span>
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

<span data-ttu-id="626d3-106">在 HoloLens 2 中，當您以直覺方式追蹤使用者，並將其放在實體環境中，讓互動順暢且簡潔時，就能開始使用全息。</span><span class="sxs-lookup"><span data-stu-id="626d3-106">Holograms come to life in HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="626d3-107">在本教學課程中，我們會探索如何使用 MRTK 的可用位置工具（稱為解析器）來動態地放置全息影像，以解決複雜的空間放置案例。</span><span class="sxs-lookup"><span data-stu-id="626d3-107">In this tutorial, we explore ways to dynamically place holograms using the MRTK’s available placement tools, known as Solvers, to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="626d3-108">在 MRTK 中，解析器是一種腳本和行為的系統，可用來允許 UI 專案在場景中追蹤您、使用者或其他遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="626d3-108">In the MRTK, Solvers are a system of scripts and behaviors that are used to allow UI elements to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="626d3-109">也可用來快速對齊特定位置，讓您的應用程式更具直覺性。</span><span class="sxs-lookup"><span data-stu-id="626d3-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="626d3-110">目標</span><span class="sxs-lookup"><span data-stu-id="626d3-110">Objectives</span></span>

* <span data-ttu-id="626d3-111">引進 MRTK 的解析器</span><span class="sxs-lookup"><span data-stu-id="626d3-111">Introduce the MRTK's Solvers</span></span>
* <span data-ttu-id="626d3-112">使用解析器讓按鈕集合跟隨使用者</span><span class="sxs-lookup"><span data-stu-id="626d3-112">Use Solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="626d3-113">使用解析器讓遊戲物件遵循使用者的追蹤手</span><span class="sxs-lookup"><span data-stu-id="626d3-113">Use Solvers to have a game object follow the user's tracked hands</span></span>

## <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="626d3-114">MRTK 中的解析器位置</span><span class="sxs-lookup"><span data-stu-id="626d3-114">Location of Solvers in the MRTK</span></span>

 <span data-ttu-id="626d3-115">MRTK 的解析器位於 MRTK SDK 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="626d3-115">The MRTK's Solvers are located in the MRTK SDK folder.</span></span> <span data-ttu-id="626d3-116">若要查看專案中的可用解析器，請在 [專案] 視窗中，流覽至 [**資產**] [ > **MixedRealityToolkit** ] [ > **功能**] > [**公用程式**] > **解析器**：</span><span class="sxs-lookup"><span data-stu-id="626d3-116">To see the available Solvers in your project, in the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **Features** > **Utilities** > **Solvers**:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial3-section1-step1-1.png)

<span data-ttu-id="626d3-118">在本教學課程中，我們將探討 Orbital 規劃求解和星形視圖規劃求解的執行。</span><span class="sxs-lookup"><span data-stu-id="626d3-118">In this tutorial, we will review the implementation of the Orbital Solver and the Radial View Solver.</span></span> <span data-ttu-id="626d3-119">若要深入瞭解 MRTK 中提供的完整解析器，您可以流覽[MRTK 檔入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[解析器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)指南。</span><span class="sxs-lookup"><span data-stu-id="626d3-119">To learn more about the full range of Solvers available in the MRTK, you can visit the the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="626d3-120">使用規劃人員追蹤使用者</span><span class="sxs-lookup"><span data-stu-id="626d3-120">Use a Solver to follow the user</span></span>
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

<span data-ttu-id="626d3-121">在本節中，您將增強在上一個教學課程中建立的按鈕集合，使其遵循使用者的注視方向。</span><span class="sxs-lookup"><span data-stu-id="626d3-121">In this section, you will enhance the button collection you created in the previous tutorial so it follows the user’s gaze direction.</span></span> <span data-ttu-id="626d3-122">此外，您也會設定 [規劃求解]，讓按鈕集合一律為：</span><span class="sxs-lookup"><span data-stu-id="626d3-122">Additionally, you will also configure the Solver so the button collection is always:</span></span>

* <span data-ttu-id="626d3-123">對使用者的閱讀方向進行的平行旋轉，以自然的向右閱讀</span><span class="sxs-lookup"><span data-stu-id="626d3-123">Rotated parallel to the user's reading direction, for natural left to right reading</span></span>
* <span data-ttu-id="626d3-124">位置稍微低於使用者水準外觀，因此不會阻礙您稍後將在本教學課程中新增的其他物件。</span><span class="sxs-lookup"><span data-stu-id="626d3-124">Positioned slightly below the user horizontal gaze direction, so it's not obstructing the other objects you will add later in this tutorial</span></span>
* <span data-ttu-id="626d3-125">接近使用者的一半 arm 長度，因此可以輕鬆按下按鈕</span><span class="sxs-lookup"><span data-stu-id="626d3-125">Positioned approximately a half arm's-length from the user, so the buttons can easily be pressed</span></span>

<span data-ttu-id="626d3-126">為此，您將使用**Orbital 的規劃求解**，將物件從參考的物件鎖定到指定的位置和位移。</span><span class="sxs-lookup"><span data-stu-id="626d3-126">For this, you will use the **Orbital Solver** which locks the object to a specified position and offset from the referenced object.</span></span>

### <a name="1-add-the-orbital-solver"></a><span data-ttu-id="626d3-127">1. 加入 Orbital 規劃求解</span><span class="sxs-lookup"><span data-stu-id="626d3-127">1. Add the Orbital Solver</span></span>

<span data-ttu-id="626d3-128">在 [階層] 視窗中，選取 [ **ButtonCollection** ] 物件，然後在 [偵測器] 視窗中，使用 [**加入元件**] 按鈕將**Orbital （腳本）** 元件新增至 ButtonCollection 物件。</span><span class="sxs-lookup"><span data-stu-id="626d3-128">In the Hierarchy window, select the **ButtonCollection** object, then in the Inspector window, use the **Add Component** button to add the **Orbital (Script)** component to the ButtonCollection object.</span></span>

> [!NOTE]
> <span data-ttu-id="626d3-129">當您加入規劃求解時（在此案例中為 Orbital （Script）元件），會自動加入「規劃求解處理常式」（腳本）元件，因為它是規劃求解所需。</span><span class="sxs-lookup"><span data-stu-id="626d3-129">When you add a Solver, in this case the Orbital (Script) component, the Solver Handler (Script) component is automatically added because it is required by the Solver.</span></span>

### <a name="2-configure-the-orbital-solver"></a><span data-ttu-id="626d3-130">2. 設定 Orbital 規劃求解</span><span class="sxs-lookup"><span data-stu-id="626d3-130">2. Configure the Orbital Solver</span></span>

<span data-ttu-id="626d3-131">設定 [**規劃求解處理常式（腳本）** ] 元件：</span><span class="sxs-lookup"><span data-stu-id="626d3-131">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="626d3-132">確認 [**追蹤的目標型別**] 設定為 [ **Head** ]</span><span class="sxs-lookup"><span data-stu-id="626d3-132">Verify that **Tracked Target Type**  is set to **Head**</span></span>

<span data-ttu-id="626d3-133">設定**Orbital （腳本）** 元件：</span><span class="sxs-lookup"><span data-stu-id="626d3-133">Configure the **Orbital (Script)** component:</span></span>

* <span data-ttu-id="626d3-134">將**方向類型**變更為**跟隨追蹤的物件**</span><span class="sxs-lookup"><span data-stu-id="626d3-134">Change **Orientation Type** to **Follow Tracked Object**</span></span>
* <span data-ttu-id="626d3-135">將**區域位移**重設為 X = 0、Y = 0、Z = 0</span><span class="sxs-lookup"><span data-stu-id="626d3-135">Reset **Local Offset** to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="626d3-136">將**世界位移**變更為 X = 0，Y =-0.4，Z = 0。3</span><span class="sxs-lookup"><span data-stu-id="626d3-136">Change **World Offset** to X = 0, Y = -0.4, Z = 0.3</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a><span data-ttu-id="626d3-138">3. 使用編輯器內模擬來測試 Orbital 規劃求解</span><span class="sxs-lookup"><span data-stu-id="626d3-138">3. Test the Orbital Solver using the in-editor simulation</span></span>

<span data-ttu-id="626d3-139">按下 [播放] 按鈕進入遊戲模式，然後按住滑鼠右鍵以旋轉您的注視方向，並注意下列事項：</span><span class="sxs-lookup"><span data-stu-id="626d3-139">Press the Play button to enter Game mode and press and hold the right mouse button to rotate your gaze direction, and notice the following:</span></span>

* <span data-ttu-id="626d3-140">ButtonCollection 的轉換位置現在是由 [規劃求解] 設定所驅動</span><span class="sxs-lookup"><span data-stu-id="626d3-140">The ButtonCollection's Transform Position is now driven by the Solver settings</span></span>
* <span data-ttu-id="626d3-141">不受規劃求解影響的 Cube 會保留在相同的位置</span><span class="sxs-lookup"><span data-stu-id="626d3-141">The Cube, which is not affected by the Solver, remains in the same position</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> <span data-ttu-id="626d3-143">如果您沒有在場景視窗中看到相機光線，請確定已啟用 [Gizmos] 功能表。</span><span class="sxs-lookup"><span data-stu-id="626d3-143">If you don't see the camera ray in your Scene window, make sure your Gizmos menu is enabled.</span></span> <span data-ttu-id="626d3-144">若要深入瞭解 [Gizmos] 功能表，以及如何使用它來優化場景視圖，您可以造訪 Unity 的 [ <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos] 功能表</a>檔。</span><span class="sxs-lookup"><span data-stu-id="626d3-144">To learn more about the Gizmos menu and how you can use it to optimize your scene view, you can visit Unity's <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos menu</a> documentation.</span></span>
>
> <span data-ttu-id="626d3-145">若要並排顯示場景和遊戲視窗（如上圖所示），只需將遊戲視窗拖曳至場景視窗的右邊。</span><span class="sxs-lookup"><span data-stu-id="626d3-145">To display your Scene and Game window side by side as shown in the image above, simply drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="626d3-146">若要深入瞭解如何自訂您的工作區，您可以造訪 Unity 的<a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">自訂工作區</a>檔。</span><span class="sxs-lookup"><span data-stu-id="626d3-146">To learn more about customizing your workspace, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

## <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="626d3-147">讓物件遵循追蹤的手</span><span class="sxs-lookup"><span data-stu-id="626d3-147">Enabling objects to follow tracked hands</span></span>

<span data-ttu-id="626d3-148">在本節中，您將設定您在上一個教學課程中建立的 Cube 物件，使其遵循使用者的追蹤手，特別是右邊的手腕。</span><span class="sxs-lookup"><span data-stu-id="626d3-148">In this section, you will configure the Cube object you created in the previous tutorial so it follows the user’s tracked hands, specifically the right hand wrist.</span></span> <span data-ttu-id="626d3-149">此外，您也會將此規劃求解設定為 cube：</span><span class="sxs-lookup"><span data-stu-id="626d3-149">Additionally, you will also configure the Solver so the cube:</span></span>

* <span data-ttu-id="626d3-150">變更其與使用者的旋轉方向</span><span class="sxs-lookup"><span data-stu-id="626d3-150">Changes it's orientation with the user's hand rotation</span></span>
* <span data-ttu-id="626d3-151">放在使用者的手腕上</span><span class="sxs-lookup"><span data-stu-id="626d3-151">Positioned on the user's wrist</span></span>

<span data-ttu-id="626d3-152">為此，您將使用星形**視圖規劃求解**，將物件保留在視圖中，並由參考的物件轉換。</span><span class="sxs-lookup"><span data-stu-id="626d3-152">For this, you will use the **Radial View Solver** which keeps the object within a view cone cast by the referenced object.</span></span>

### <a name="1-add-the-radial-view-solver"></a><span data-ttu-id="626d3-153">1. 加入星形視圖規劃求解</span><span class="sxs-lookup"><span data-stu-id="626d3-153">1. Add the Radial View Solver</span></span>

<span data-ttu-id="626d3-154">在 [階層] 視窗中，選取**Cube**物件，然後在 [偵測器] 視窗中，使用 [**加入元件**] 按鈕來加入星形**視圖（腳本）** 元件 Cube 物件。</span><span class="sxs-lookup"><span data-stu-id="626d3-154">In the Hierarchy window, select the **Cube** object, then in the Inspector window, use the **Add Component** button to add the **Radial View (Script)** component Cube object.</span></span>

### <a name="2-configure-the-radial-view-solver"></a><span data-ttu-id="626d3-155">2. 設定放射狀視圖的規劃求解</span><span class="sxs-lookup"><span data-stu-id="626d3-155">2. Configure the Radial View Solver</span></span>

<span data-ttu-id="626d3-156">設定 [**規劃求解處理常式（腳本）** ] 元件：</span><span class="sxs-lookup"><span data-stu-id="626d3-156">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="626d3-157">將**追蹤的目標型別**變更為**手動聯合**</span><span class="sxs-lookup"><span data-stu-id="626d3-157">Change **Tracked Target Type** to **Hand Joint**</span></span>
* <span data-ttu-id="626d3-158">將**追蹤的 Handness**變更為**右方**</span><span class="sxs-lookup"><span data-stu-id="626d3-158">Change **Tracked Handness** to **Right**</span></span>
* <span data-ttu-id="626d3-159">將**追蹤的接頭**變更為**手腕**</span><span class="sxs-lookup"><span data-stu-id="626d3-159">Change **Tracked Hand Joint** to **Wrist**</span></span>

<span data-ttu-id="626d3-160">設定**放射狀視圖（腳本）** 元件：</span><span class="sxs-lookup"><span data-stu-id="626d3-160">Configure the **Radial View (Script)** component:</span></span>

* <span data-ttu-id="626d3-161">將 [**參考方向**] 變更為 [**物件導向**]，然後選取 [**朝向參考方向**] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="626d3-161">Change **Reference Direction** to **Object Oriented**, then check the **Orient To Reference Direction** checkbox</span></span>
* <span data-ttu-id="626d3-162">將 [**最小距離**] 和 [**最大距離**] 變更為0</span><span class="sxs-lookup"><span data-stu-id="626d3-162">Change **Min Distance** and **Max Distance** to 0</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a><span data-ttu-id="626d3-164">3. 使用編輯器內模擬來測試星形視圖規劃</span><span class="sxs-lookup"><span data-stu-id="626d3-164">3. Test the Radial View Solver using the in-editor simulation</span></span>

<span data-ttu-id="626d3-165">按下 [播放] 按鈕進入遊戲模式，然後按住空格鍵以顯示手。</span><span class="sxs-lookup"><span data-stu-id="626d3-165">Press the Play button to enter Game mode and then press and hold the spacebar to bring up the hand.</span></span> <span data-ttu-id="626d3-166">將滑鼠游標移到周圍以移動手，然後按住滑鼠左鍵以旋轉手：</span><span class="sxs-lookup"><span data-stu-id="626d3-166">Move the mouse cursor around to move the hand, and click and hold the left mouse button to rotate the hand:</span></span>

![mrlearning-基底](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a><span data-ttu-id="626d3-168">恭喜</span><span class="sxs-lookup"><span data-stu-id="626d3-168">Congratulations</span></span>

<span data-ttu-id="626d3-169">在本教學課程中，您已瞭解如何使用 MRTK 的解析器，讓 UI 直覺地跟隨使用者。</span><span class="sxs-lookup"><span data-stu-id="626d3-169">In this tutorial, you learned how to use the MRTK’s solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="626d3-170">您也已瞭解如何將規劃求解附加至物件（例如 cube），以遵循使用者的追蹤手。</span><span class="sxs-lookup"><span data-stu-id="626d3-170">You also learned how to attach a Solver to an object (i.e., cube) to follow the user’s tracked hands.</span></span> <span data-ttu-id="626d3-171">若要深入瞭解 MRTK 隨附的這些和其他解析器，您可以流覽[MRTK 檔入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[解析器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)指南。</span><span class="sxs-lookup"><span data-stu-id="626d3-171">To learn more about these and other solvers included with the MRTK,  you can visit the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

[<span data-ttu-id="626d3-172">下一個教學課程： 5. 與3D 物件互動</span><span class="sxs-lookup"><span data-stu-id="626d3-172">Next Tutorial: 5. Interacting with 3D objects</span></span>](mrlearning-base-ch4.md)
