---
title: 入門教學課程 - 4。 將物件置放在場景中
description: 本課程說明如何使用混合實境工具組 (MRTK) 來建立混合實境應用程式。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 71990db23b5154de916f0eda86a978885ab53547
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376630"
---
# <a name="4-positioning-objects-in-the-scene"></a><span data-ttu-id="dd04b-105">4.將物件置放在場景中</span><span class="sxs-lookup"><span data-stu-id="dd04b-105">4. Positioning objects in the scene</span></span>

## <a name="overview"></a><span data-ttu-id="dd04b-106">概觀</span><span class="sxs-lookup"><span data-stu-id="dd04b-106">Overview</span></span>

<span data-ttu-id="dd04b-107">在本教學課程中，您將匯入教學課程資產，並將所提供的物件放置在場景中。</span><span class="sxs-lookup"><span data-stu-id="dd04b-107">In this tutorial, you will import the tutorial assets and position the provided objects in the scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="dd04b-108">目標</span><span class="sxs-lookup"><span data-stu-id="dd04b-108">Objectives</span></span>

* <span data-ttu-id="dd04b-109">了解如何將物件放置在場景中</span><span class="sxs-lookup"><span data-stu-id="dd04b-109">Learn how to position objects in the scene</span></span>
* <span data-ttu-id="dd04b-110">了解如何使用 MRTK 的網格物件集合功能</span><span class="sxs-lookup"><span data-stu-id="dd04b-110">Learn how to use MRTK's Grid Object Collection feature</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="dd04b-111">匯入教學課程資產</span><span class="sxs-lookup"><span data-stu-id="dd04b-111">Importing the tutorial assets</span></span>

<span data-ttu-id="dd04b-112">下載並匯入下列 Unity 自訂套件：</span><span class="sxs-lookup"><span data-stu-id="dd04b-112">Download and import the following Unity custom package:</span></span>

* [<span data-ttu-id="dd04b-113">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="dd04b-113">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)

<span data-ttu-id="dd04b-114">匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：</span><span class="sxs-lookup"><span data-stu-id="dd04b-114">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="dd04b-116">如需有關如何匯入 Unity 自訂套件的提示，您可以參閱[匯入 MRTK](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) 的指示。</span><span class="sxs-lookup"><span data-stu-id="dd04b-116">For a reminder on how to import a Unity custom package, you can refer to the [Importing the MRTK](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="creating-the-parent-object"></a><span data-ttu-id="dd04b-117">建立父物件</span><span class="sxs-lookup"><span data-stu-id="dd04b-117">Creating the parent object</span></span>

<span data-ttu-id="dd04b-118">在 [階層] 視窗中，以滑鼠右鍵按一下空的位置，然後選取 [建立空物件]，將空的物件新增至您的場景：</span><span class="sxs-lookup"><span data-stu-id="dd04b-118">In the Hierarchy window, right-click on an empty spot, and select **Create Empty** to add an empty object to your scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="dd04b-120">若要並排顯示場景和遊戲視窗 (如上圖所示)，將遊戲視窗拖曳至場景視窗的右邊即可。</span><span class="sxs-lookup"><span data-stu-id="dd04b-120">To display your Scene and Game window side by side as shown in the image above, drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="dd04b-121">若要深入了解如何自訂您的工作區，您可以參閱 Unity 的<a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">自訂您的工作區</a>文件。</span><span class="sxs-lookup"><span data-stu-id="dd04b-121">To learn more about customizing your workspace, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

<span data-ttu-id="dd04b-122">以滑鼠右鍵按一下新建立的物件並選取 [重新命名]，然後將名稱變更為 **RoverExplorer**：</span><span class="sxs-lookup"><span data-stu-id="dd04b-122">Right-click on the newly created object, select **Rename**, and change the name to **RoverExplorer**:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-2.png)

<span data-ttu-id="dd04b-124">在仍選取 RoverExplorer 物件的情況下，在 [偵測器] 視窗中設定**變形**元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dd04b-124">With the RoverExplorer object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="dd04b-125">**位置**：X = 0、Y = -0.6、Z = 2</span><span class="sxs-lookup"><span data-stu-id="dd04b-125">**Position**: X = 0, Y = -0.6, Z = 2</span></span>
* <span data-ttu-id="dd04b-126">**旋轉**：X = 0、Y = 0、Z = 0</span><span class="sxs-lookup"><span data-stu-id="dd04b-126">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="dd04b-127">**縮放**：X = 1、Y = 1、Z = 1</span><span class="sxs-lookup"><span data-stu-id="dd04b-127">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="dd04b-129">相機代表使用者頭部，位於原點：X = 0、Y = 0、Z = 0。</span><span class="sxs-lookup"><span data-stu-id="dd04b-129">The camera represents the users head and is positioned at origin, X = 0, Y = 0, Z = 0.</span></span> <span data-ttu-id="dd04b-130">一般情況下，Unity 中的 1 個單位大約是真實世界的 1 公尺。</span><span class="sxs-lookup"><span data-stu-id="dd04b-130">In general, 1 unit in Unity is roughly 1 meter in the physical world.</span></span> <span data-ttu-id="dd04b-131">但有例外狀況，例如，當物件是所縮放物件的子系時。</span><span class="sxs-lookup"><span data-stu-id="dd04b-131">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span> <span data-ttu-id="dd04b-132">在上述案例中，RoverExplorer 會放置在使用者頭部前方 2 公尺及下方 0.6 公尺處。</span><span class="sxs-lookup"><span data-stu-id="dd04b-132">In the scenario above, the RoverExplorer is positioned 2 meters in front of and 0.6 meters below the user's head.</span></span>

## <a name="adding-the-tutorial-prefabs"></a><span data-ttu-id="dd04b-133">新增教學課程 Prefab</span><span class="sxs-lookup"><span data-stu-id="dd04b-133">Adding the tutorial prefabs</span></span>

<span data-ttu-id="dd04b-134">在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.GettingStarted] > [Prefabs] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="dd04b-134">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="dd04b-136"><a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">Prefab</a> 是預先設定且儲存為 Unity 資產的 GameObject，可以在整個專案中重複使用。</span><span class="sxs-lookup"><span data-stu-id="dd04b-136">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="dd04b-137">在 [專案] 視窗中，按一下**資料表** Prefab 並拖曳至 **RoverExplorer** 物件上，使其成為 RoverExplorer 物件的子系，然後在 [偵測器] 視窗中設定**變形**元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dd04b-137">From the Project window, click-and-drag the **Table** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="dd04b-138">**位置**：X = 0、Y = -0.005、Z = 0</span><span class="sxs-lookup"><span data-stu-id="dd04b-138">**Position**: X = 0, Y = -0.005, Z = 0</span></span>
* <span data-ttu-id="dd04b-139">**旋轉**：X = 0、Y = 0、Z = 0</span><span class="sxs-lookup"><span data-stu-id="dd04b-139">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="dd04b-140">**縮放**：X = 1.2、Y = 0.01、Z = 1.2</span><span class="sxs-lookup"><span data-stu-id="dd04b-140">**Scale**: X = 1.2, Y = 0.01, Z = 1.2</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="dd04b-142">若要顯示您的場景 (如上圖所示)，請使用場景視窗右上角的<a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">場景 Gizmo</a>，將檢視角度調整為以 Z 軸為前方，並按兩下 MixedRealityPlayspace 物件將焦點放在相機上，然後視需要進行放大。</span><span class="sxs-lookup"><span data-stu-id="dd04b-142">To display your scene as shown in the image above, use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis, double-click the MixedRealityPlayspace object to focus on the camera, and zoom in as needed.</span></span>

<span data-ttu-id="dd04b-143">在 [專案] 視窗中，按一下 **[RoverAssembly]** Prefab 並拖曳至 **RoverExplorer** 物件，使其成為 RoverExplorer 物件的子系，然後在 [偵測器] 視窗中設定**變形**元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dd04b-143">From the Project window, click-and-drag the **RoverAssembly** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="dd04b-144">**位置**：X = -0.1、Y = 0、Z = 0</span><span class="sxs-lookup"><span data-stu-id="dd04b-144">**Position**: X = -0.1, Y = 0, Z = 0</span></span>
* <span data-ttu-id="dd04b-145">**旋轉**：X = 0、Y = -135、Z = 0</span><span class="sxs-lookup"><span data-stu-id="dd04b-145">**Rotation**: X = 0, Y = -135, Z = 0</span></span>
* <span data-ttu-id="dd04b-146">**縮放**：X = 1、Y = 1、Z = 1</span><span class="sxs-lookup"><span data-stu-id="dd04b-146">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a><span data-ttu-id="dd04b-148">組織集合中的 3D 物件</span><span class="sxs-lookup"><span data-stu-id="dd04b-148">Organizing objects in a collection</span></span>

<span data-ttu-id="dd04b-149">在 [階層] 視窗中，以滑鼠右鍵按一下 **RoverExplorer** 物件並選取 [建立空物件]，將空白物件新增為 RoverExplorer 的子系，然後將物件命名為 **RoverParts**，並設定**變形**元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dd04b-149">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **RoverParts**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="dd04b-150">**位置**：X = 0、Y = 0.06、Z = 0</span><span class="sxs-lookup"><span data-stu-id="dd04b-150">**Position**: X = 0, Y = 0.06, Z = 0</span></span>
* <span data-ttu-id="dd04b-151">**旋轉**：X = 0、Y = 90、Z = 0</span><span class="sxs-lookup"><span data-stu-id="dd04b-151">**Rotation**: X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="dd04b-152">**縮放**：X = 1、Y = 1、Z = 1</span><span class="sxs-lookup"><span data-stu-id="dd04b-152">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-1.png)

<span data-ttu-id="dd04b-154">在 [階層] 視窗中，選取所有 RoverExplorer > RoverAssembly > RoverModel > **Parts** 子物件，以滑鼠右鍵按一下這些子物件，然後選取 [複製]，為每個零件建立複本：</span><span class="sxs-lookup"><span data-stu-id="dd04b-154">In the Hierarchy window, select all the RoverExplorer > RoverAssembly > RoverModel > **Parts** child objects, right-click on them and select **Duplicate** to create a copy of each of the parts:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="dd04b-156">若要選取多個連續的物件，請按住 SHIFT 鍵，同時使用滑鼠來選取第一個和最後一個物件。</span><span class="sxs-lookup"><span data-stu-id="dd04b-156">To select multiple adjacent objects, press-and-hold the SHIFT key while using the mouse to select the first and last object.</span></span>

<span data-ttu-id="dd04b-157">繼續選取新複製的 Parts 子物件，按一下這些物件並拖曳至 **RoverParts** 物件，使其成為 RoverParts 物件的子物件：</span><span class="sxs-lookup"><span data-stu-id="dd04b-157">With the newly duplicated Parts child objects still selected, click-and-drag them on to the **RoverParts** object to make them child objects of the RoverParts object:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-3.png)

<span data-ttu-id="dd04b-159">為了讓您更輕鬆地使用場景，請在 [階層] 視窗中，按一下物件左邊的**眼睛**圖示，以將 **RoverExplorer** 物件的**場景可見度**切換為關閉。</span><span class="sxs-lookup"><span data-stu-id="dd04b-159">To make it easier to work with your scene, in the Hierarchy window, click the **eye** icon to the left of the object to toggle the **scene visibility** for the **RoverExplorer** object off.</span></span> <span data-ttu-id="dd04b-160">這會在場景視窗中隱藏物件，而不會變更其遊戲內的可見度：</span><span class="sxs-lookup"><span data-stu-id="dd04b-160">This hides the object in the Scene window without changing its in-game visibility:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-4.png)

> [!TIP]
> <span data-ttu-id="dd04b-162">若要深入了解場景可見度的控制項，以及如何使用其來最佳化場景檢視和工作流程，您可以參閱 Unity 的<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">場景可見度</a>文件。</span><span class="sxs-lookup"><span data-stu-id="dd04b-162">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

<span data-ttu-id="dd04b-163">在 [階層] 視窗中，將附加的 **(1)** 取代為 **_Part**，以清除 RoverParts 子物件的名稱：</span><span class="sxs-lookup"><span data-stu-id="dd04b-163">In the Hierarchy window, clean up the RoverParts child objects' names by replacing the appended **(1)** with **_Part**:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-5.png)

<span data-ttu-id="dd04b-165">在 [階層] 視窗中，選取 **RoverParts** 物件，然後在 [偵測器] 視窗中，按一下 [新增元件] 按鈕，搜尋並選取 [GridObjectCollection]，將 GridObjectCollection 元件新增至 RoverParts 物件：</span><span class="sxs-lookup"><span data-stu-id="dd04b-165">In the Hierarchy window, select the **RoverParts** object, then in the Inspector window, click the **Add Component** button, and search for and select **GridObjectCollection** to add the GridObjectCollection component to the RoverParts object:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-6.png)

<span data-ttu-id="dd04b-167">設定 **GridObjectCollection** 元件值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dd04b-167">Configure the **GridObjectCollection** component values as follows:</span></span>

* <span data-ttu-id="dd04b-168">**排序類型**：字母順序</span><span class="sxs-lookup"><span data-stu-id="dd04b-168">**Sort Type**: Alphabetic</span></span>
* <span data-ttu-id="dd04b-169">**版面配置**：水平</span><span class="sxs-lookup"><span data-stu-id="dd04b-169">**Layout**: Horizontal</span></span>
* <span data-ttu-id="dd04b-170">**儲存格寬度**：0.25</span><span class="sxs-lookup"><span data-stu-id="dd04b-170">**Cell Width**: 0.25</span></span>
* <span data-ttu-id="dd04b-171">**與父系的距離**：0.38</span><span class="sxs-lookup"><span data-stu-id="dd04b-171">**Distance from parent**: 0.38</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-7.png)

<span data-ttu-id="dd04b-173">然後按一下 [更新集合] 按鈕，以更新 RoverParts 子物件的位置：</span><span class="sxs-lookup"><span data-stu-id="dd04b-173">Then click the **Update Collection** button to update the position of the RoverParts child objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="dd04b-175">恭喜！</span><span class="sxs-lookup"><span data-stu-id="dd04b-175">Congratulations</span></span>

<span data-ttu-id="dd04b-176">在本教學課程中，您已了解如何將物件放置在場景中與使用者相對的位置，並使用 MRTK 的網格物件集合功能來組織集合中的物件。</span><span class="sxs-lookup"><span data-stu-id="dd04b-176">In this tutorial, you learned how to position objects in the scene relative to the user and use MRTK's Grid Object Collection feature to organize objects in a collection.</span></span>

[<span data-ttu-id="dd04b-177">下一個教學課程：5.使用解析器建立動態內容</span><span class="sxs-lookup"><span data-stu-id="dd04b-177">Next Tutorial: 5. Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
