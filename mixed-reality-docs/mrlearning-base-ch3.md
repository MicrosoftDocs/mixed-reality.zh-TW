---
title: MR 學習基底模組-動態內容的位置和解
description: 完成這個課程來了解如何在混合的實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合的實境，unity 教學課程 hololens
ms.openlocfilehash: 6f05b2cecd388b1b2f13e7e5228bc90091eee3bd
ms.sourcegitcommit: aba33a8ad1416f7598048ac35ae9ab1734bd5c37
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2019
ms.locfileid: "66270404"
---
# <a name="mr-learning-base-module---dynamic-content-placement-and-solvers"></a><span data-ttu-id="796c7-104">MR 學習基底模組-動態內容的位置和解</span><span class="sxs-lookup"><span data-stu-id="796c7-104">MR Learning Base Module - Dynamic Content Placement and Solvers</span></span>

<span data-ttu-id="796c7-105">全像投影結果出現在 HoloLens 2 時直接易懂的方式追蹤使用者，會放在實際環境中，可順暢且簡潔的互動的方式。</span><span class="sxs-lookup"><span data-stu-id="796c7-105">Holograms come to life in the HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="796c7-106">在第 3 課中，我們將探討如何動態地全像投影使用 MRTK 的可用位置工具，稱為 「 解。 」</span><span class="sxs-lookup"><span data-stu-id="796c7-106">In Lesson 3, we will explore ways to dynamically place holograms using the MRTK’s available placement tools, known as "solvers."</span></span> <span data-ttu-id="796c7-107">它們稱為 「 解 」 來解決複雜的空間放置演算法的方式。</span><span class="sxs-lookup"><span data-stu-id="796c7-107">They are known as "solvers" for the way they solve complex spatial placement algorithms.</span></span> <span data-ttu-id="796c7-108">在 MRTK，解都是指令碼和行為，我們要能夠允許 UI 項目，請遵循您，使用者或其他遊戲場景中的物件所使用的系統。</span><span class="sxs-lookup"><span data-stu-id="796c7-108">In the MRTK, solvers are a system of scripts and behaviors that we use to be able to allow UI elements to follow you, the user or other game objects in the scene.</span></span> <span data-ttu-id="796c7-109">它們也可用來快速貼齊至特定位置讓您的應用程式更具直覺性。</span><span class="sxs-lookup"><span data-stu-id="796c7-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span> 

## <a name="objectives"></a><span data-ttu-id="796c7-110">目標</span><span class="sxs-lookup"><span data-stu-id="796c7-110">Objectives</span></span>

* <span data-ttu-id="796c7-111">導入 MRTK 解</span><span class="sxs-lookup"><span data-stu-id="796c7-111">Introduce the MRTK's solvers</span></span>
* <span data-ttu-id="796c7-112">有一組按鈕使用解關注的使用者</span><span class="sxs-lookup"><span data-stu-id="796c7-112">Use solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="796c7-113">有遊戲物件使用解依照使用者的追蹤實際操作</span><span class="sxs-lookup"><span data-stu-id="796c7-113">Use solvers to have a game object follow the user's tracked hands</span></span>

## <a name="instructions"></a><span data-ttu-id="796c7-114">指示</span><span class="sxs-lookup"><span data-stu-id="796c7-114">Instructions</span></span>

### <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="796c7-115">解 MRTK 中的位置</span><span class="sxs-lookup"><span data-stu-id="796c7-115">Location of solvers in the MRTK</span></span>
 <span data-ttu-id="796c7-116">若要在您的專案中尋找可用的解，請查看 MRTK SDK 資料夾 （MixedRealityToolkit.SDK 資料夾），然後在 [公用程式] 資料夾中會看到 [解] 資料夾中，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="796c7-116">To find the available solvers in your project, look in the MRTK SDK folder (MixedRealityToolkit.SDK folder), then under the utilities folder you will see the solvers folder, as shown in the image below.</span></span>

![解](images/lesson3_chapter1_step1im.PNG)

><span data-ttu-id="796c7-118">注意:在本課程中我們將只介紹"軌道"求解器和 「 RadialView"規劃求解的實作。</span><span class="sxs-lookup"><span data-stu-id="796c7-118">Note: In this lesson we will only go over implementation of the "Orbital" solver and the "RadialView" solver.</span></span> <span data-ttu-id="796c7-119">若要深入了解 MRTK 中可用之完整範圍的詳細，請瀏覽： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html</span><span class="sxs-lookup"><span data-stu-id="796c7-119">To learn more about the full range of solvers available in the MRTK, please visit: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html</span></span>

### <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="796c7-120">若要追蹤使用者使用規劃求解</span><span class="sxs-lookup"><span data-stu-id="796c7-120">Use a Solver to Follow the User</span></span>
<span data-ttu-id="796c7-121">本指南的目標是提升我們先前所建立，它會依照使用者的視線方向的按鈕集合。</span><span class="sxs-lookup"><span data-stu-id="796c7-121">The goal of this chapter is to enhance the button collection we previously created such that it follows the user’s gaze direction.</span></span> <span data-ttu-id="796c7-122">前一版的 MRTK 和 HoloToolkit 的詳細資訊，這被指 「 taglong 」 功能。</span><span class="sxs-lookup"><span data-stu-id="796c7-122">In previous version of the MRTK and HoloToolkit, this was referred to as a "taglong" functionality.</span></span>

1. <span data-ttu-id="796c7-123">從上一課中，選取的按鈕集合的父物件。</span><span class="sxs-lookup"><span data-stu-id="796c7-123">Select the Button Collection parent object from the previous lesson.</span></span>

![Lesson3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. <span data-ttu-id="796c7-125">在 [偵測器] 面板中，按一下 [新增元件] 按鈕並搜尋"軌道。 」</span><span class="sxs-lookup"><span data-stu-id="796c7-125">In the inspector panel, click the "add component" button and search for "orbital."</span></span> <span data-ttu-id="796c7-126">軌道元件應該會出現。</span><span class="sxs-lookup"><span data-stu-id="796c7-126">The orbital component should appear.</span></span> <span data-ttu-id="796c7-127">請選取要新增的按鈕集合的遊戲物件的軌道的元件。</span><span class="sxs-lookup"><span data-stu-id="796c7-127">Select it to add the orbital component to the Button Collection game object.</span></span>

![Lesson3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

><span data-ttu-id="796c7-129">注意:當您新增元件時，您會發現，系統會將新增軌道的指令碼，並規劃求解的處理常式指令碼偵測器索引標籤中，這是必要的元件。</span><span class="sxs-lookup"><span data-stu-id="796c7-129">Note: When you add the component you will notice that the system adds the orbital script and the solver handler script in the inspector tab, which is a required component.</span></span> 

3. <span data-ttu-id="796c7-130">若要設定按鈕的集合，以追蹤使用者，我們必須實作下列調整 （另請參閱下面的影像）：</span><span class="sxs-lookup"><span data-stu-id="796c7-130">In order to configure the button collection to follow the user, we need to implement the following adjustments (please also refer to the image below):</span></span>
- <span data-ttu-id="796c7-131">在軌道的指令碼中，設定 [方向類型] 下拉式清單，以 「 繞只。 」</span><span class="sxs-lookup"><span data-stu-id="796c7-131">In the Orbital script, set the "orientation type" drop-down list to "Yaw Only."</span></span> <span data-ttu-id="796c7-132">這可讓物件的該只有一個軸旋轉，它如下所示的使用者。</span><span class="sxs-lookup"><span data-stu-id="796c7-132">This makes it so that only one axis of the object rotates as it follows the user.</span></span>
- <span data-ttu-id="796c7-133">設定區域的位移為 0，所有軸上。</span><span class="sxs-lookup"><span data-stu-id="796c7-133">Set the local offset to 0 on all axes.</span></span> <span data-ttu-id="796c7-134">設定全局的位移為 x = 0，y =-0.1 和 z = 0.6。</span><span class="sxs-lookup"><span data-stu-id="796c7-134">Set the World Offset to x = 0, y = -0.1 and z = 0.6.</span></span> <span data-ttu-id="796c7-135">因此，當使用者變更高度，固定的高度，在實際環境中，將會維持物件同時仍然允許它追蹤使用者，當使用者移動的環境相關，這會鎖定移動物件。</span><span class="sxs-lookup"><span data-stu-id="796c7-135">This locks movement of the object such that when the user changes height, the object will remain at a fixed height in the physical environment, while still allowing it to follow the user as the user moves about the environment.</span></span> <span data-ttu-id="796c7-136">若要達成各種不同的行為，您可以調整這些值。</span><span class="sxs-lookup"><span data-stu-id="796c7-136">These values may be adjusted to achieve a wide range of behaviors.</span></span>
- <span data-ttu-id="796c7-137">針對後續行為，藉此按鈕才需依照使用者的檢視之後使用者開啟他或她的頭夠遠，您可以選取的 「 使用角度逐步執行程式碼的世界位移 」 核取方塊 (請注意：這個項目可能會截斷某些在畫面上，在下圖中所顯示的原狀。）比方說，若要追蹤使用者只能每隔 90 度的物件，設定步驟的數目等於 4 （在範例中，左邊的綠色箭號標記）。</span><span class="sxs-lookup"><span data-stu-id="796c7-137">For a follow behavior whereby the buttons only follow the user’s view after the user turns his or her head sufficiently far, you could select the "Use Angle Stepping for world offset" checkbox (Note: This title may be truncated on some screens, as it is in the image below.) For example, to have the object follow the user only every 90 degrees, set the number of steps equal to 4 (marked by a green arrow in the example to the left).</span></span> 

![Lesson3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="796c7-139">讓物件能夠遵循追蹤的指針</span><span class="sxs-lookup"><span data-stu-id="796c7-139">Enabling Objects to Follow Tracked Hands</span></span>

<span data-ttu-id="796c7-140">在本節中，我們將設定 cube 遊戲物件，使用先前建立依照使用者的追蹤使用 RadialView 規劃求解的手。</span><span class="sxs-lookup"><span data-stu-id="796c7-140">In this section, we will configure the cube game object previously created to follow the user’s tracked hands using the RadialView solver.</span></span>

1. <span data-ttu-id="796c7-141">BaseScene 階層中選取的 cube 物件。</span><span class="sxs-lookup"><span data-stu-id="796c7-141">Select the cube object in the BaseScene hierarchy.</span></span> <span data-ttu-id="796c7-142">按一下 [偵測器] 面板中的 [新增元件]。</span><span class="sxs-lookup"><span data-stu-id="796c7-142">Click "add component" in the inspector panel.</span></span> 

![Lesson3 Chapter3 Step1im](images/Lesson3_Chapter3_step1im.PNG)

2. <span data-ttu-id="796c7-144">在搜尋方塊中輸入 「 RadialView"，然後選取 RadialView 元件，將它加入至 cube。</span><span class="sxs-lookup"><span data-stu-id="796c7-144">Type in "RadialView" in the search box and select the RadialView component to add it to the cube.</span></span> <span data-ttu-id="796c7-145">求解器處理常式元件也會自動加入至 cube。</span><span class="sxs-lookup"><span data-stu-id="796c7-145">The solver handler component will also be automatically added to the cube.</span></span>

3. <span data-ttu-id="796c7-146">變更未遵循標頭，但請遵循在左邊的星形檢視。</span><span class="sxs-lookup"><span data-stu-id="796c7-146">Change the radial view to not follow the head but follow the left hand.</span></span> <span data-ttu-id="796c7-147">選取 「 追蹤物件以參考 」 選項旁的下拉式功能表。</span><span class="sxs-lookup"><span data-stu-id="796c7-147">Select the dropdown menu next to the "tracked object to reference" option.</span></span> <span data-ttu-id="796c7-148">然後"交給剩餘的聯合 」 從功能表中選取。</span><span class="sxs-lookup"><span data-stu-id="796c7-148">Then select "hand joint left" from the menu.</span></span>

![Lesson3 Chapter3 Step3im](images/Lesson3_chapter3_step3im.PNG)

4. <span data-ttu-id="796c7-150">一旦您選取手動聯結時，您可以選擇您想要的 cube，就可以遵循的左手邊的哪個部分。</span><span class="sxs-lookup"><span data-stu-id="796c7-150">Once you select the hand joint, you can choose which part of the hand you want the cube to follow.</span></span> <span data-ttu-id="796c7-151">針對此範例中，我們要使用 手腕。</span><span class="sxs-lookup"><span data-stu-id="796c7-151">For this example, we are going to use the wrist.</span></span> <span data-ttu-id="796c7-152">選項旁 」 追蹤的手動接合 」 選取下拉式功能表中，然後選取 手腕也一樣。</span><span class="sxs-lookup"><span data-stu-id="796c7-152">Next to the option "tracked hand joint" select the dropdown menu and select wrist.</span></span> 

![Lesson3 Chapter3 Step4im](images/Lesson3_chapter3_step4im.PNG)

5. <span data-ttu-id="796c7-154">設定為 0，讓 cube 不會有任何它與使用者的手腕之間的距離的最大和最小距離。</span><span class="sxs-lookup"><span data-stu-id="796c7-154">Set the maximum and minimum distances to 0 so that the cube will not have any distance between it and the user’s wrist.</span></span> <span data-ttu-id="796c7-155">設定之後，該 cube 會完全配合手腕。</span><span class="sxs-lookup"><span data-stu-id="796c7-155">Once set, the cube will be perfectly aligned with the wrist.</span></span> <span data-ttu-id="796c7-156">此外，您也可以調整 「 參考方向 」 欄位，來調整此 cube 有何導向 （例如，如果您想要允許使用使用者的手腕旋轉，請將 「 Box-orient 與追蹤物件 」 參考方向的物件） 的行為</span><span class="sxs-lookup"><span data-stu-id="796c7-156">You may also adjust the "Reference Direction" field to adjust the behavior of how the cube is oriented (e.g., if you would like to allow the object to rotate with the user's wrist, set the reference direction to "Orient with Tracked Object")</span></span>

![Lesson3 Chapter3 Step5im](images/Lesson3_chapter3_step5im.PNG)

### <a name="congratulations"></a><span data-ttu-id="796c7-158">恭喜您</span><span class="sxs-lookup"><span data-stu-id="796c7-158">Congratulations</span></span>
<span data-ttu-id="796c7-159">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="796c7-159">Congratulations!</span></span> <span data-ttu-id="796c7-160">在這一課，您已了解如何使用 MRTK 解具有直覺的方式追蹤使用者的 UI。</span><span class="sxs-lookup"><span data-stu-id="796c7-160">In this lesson, you learned how to use the MRTK’s solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="796c7-161">您也學到如何附加規劃求解遊戲物件 (例如 cube)，以依照使用者的追蹤實際操作。</span><span class="sxs-lookup"><span data-stu-id="796c7-161">You also learned how to attach a solver to a game object (i.e., cube) to follow the user’s tracked hands.</span></span> <span data-ttu-id="796c7-162">若要深入了解這些和其他解隨附 MRTK，歡迎您瀏覽[MRTK 解文件頁面](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)。</span><span class="sxs-lookup"><span data-stu-id="796c7-162">To learn more about these and other solvers included with the MRTK, feel free to visit the [MRTK solvers documentation page](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).</span></span>

[<span data-ttu-id="796c7-163">下一課：3D 物件互動</span><span class="sxs-lookup"><span data-stu-id="796c7-163">Next Lesson: 3D Object Interaction</span></span>](mrlearning-base-ch4.md)

