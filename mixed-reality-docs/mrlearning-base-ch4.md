---
title: 入門教學課程 - 5。 與 3D 物件互動
description: 了解基本 3D 內容和使用者體驗，例如針對基本操作組織 3D 物件和周框方塊。
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: b807ac7e51e4009d2c44d3b7c67fbdf3488ccbd9
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604989"
---
# <a name="5-interacting-with-3d-objects"></a><span data-ttu-id="facd4-105">5.與 3D 物件互動</span><span class="sxs-lookup"><span data-stu-id="facd4-105">5. Interacting with 3D objects</span></span>

<span data-ttu-id="facd4-106">在本教學課程中，您將了解基本的 3D 內容和使用者體驗，例如將 3D 物件組織為集合的一部分、基本操作所需的周框方塊、遠近互動，以及手部追蹤的觸控和抓取手勢。</span><span class="sxs-lookup"><span data-stu-id="facd4-106">In this tutorial, you will learn about basic 3D content and user experience, such as organizing 3D objects as part of a collection, bounding boxes for basic manipulation, near and far interaction, and touch and grab gestures with hand tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="facd4-107">目標</span><span class="sxs-lookup"><span data-stu-id="facd4-107">Objectives</span></span>

* <span data-ttu-id="facd4-108">建立將用於其他學習目標的 3D 物件面板</span><span class="sxs-lookup"><span data-stu-id="facd4-108">Create a panel of 3D objects which will be used for the other learning objectives</span></span>
* <span data-ttu-id="facd4-109">實作週框方塊</span><span class="sxs-lookup"><span data-stu-id="facd4-109">Implement bounding boxes</span></span>
* <span data-ttu-id="facd4-110">設定 3D 物件以進行基本操作 (例如移動、旋轉和縮放)</span><span class="sxs-lookup"><span data-stu-id="facd4-110">Configure 3D objects for basic manipulation such as move, rotate, and scale</span></span>
* <span data-ttu-id="facd4-111">探索遠近互動</span><span class="sxs-lookup"><span data-stu-id="facd4-111">Explore near and far interaction</span></span>
* <span data-ttu-id="facd4-112">了解其他手部追蹤手勢，例如抓取和觸控</span><span class="sxs-lookup"><span data-stu-id="facd4-112">Learn about additional hand tracking gestures, such as grab and touch</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="facd4-113">匯入教學課程資產</span><span class="sxs-lookup"><span data-stu-id="facd4-113">Importing the tutorial assets</span></span>

<span data-ttu-id="facd4-114">下載並匯入 Unity 自訂套件：</span><span class="sxs-lookup"><span data-stu-id="facd4-114">Download and import the Unity custom package:</span></span>

* [<span data-ttu-id="facd4-115">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="facd4-115">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)

<span data-ttu-id="facd4-116">匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：</span><span class="sxs-lookup"><span data-stu-id="facd4-116">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="facd4-118">如需有關如何匯入 Unity 自訂套件的提示，您可以參閱[匯入混合實境工具組](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) 的指示。</span><span class="sxs-lookup"><span data-stu-id="facd4-118">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="decluttering-the-scene-view"></a><span data-ttu-id="facd4-119">整理場景檢視</span><span class="sxs-lookup"><span data-stu-id="facd4-119">Decluttering the scene view</span></span>

<span data-ttu-id="facd4-120">若要更簡便地使用場景，請按一下**立方體**和 **ButtonCollection** 物件左邊的**眼睛**圖示，將這些項目的**場景可見度**設為關閉。</span><span class="sxs-lookup"><span data-stu-id="facd4-120">To make it easier to work with your scene, set the **scene visibility** for the **Cube** and **ButtonCollection** objects to off by clicking the **eye** icon to the left of the objects.</span></span> <span data-ttu-id="facd4-121">這會在場景視窗中隱藏物件，而不會變更其遊戲內的可見度：</span><span class="sxs-lookup"><span data-stu-id="facd4-121">This hides the object in the Scene window without changing their in-game visibility:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="facd4-123">若要深入了解場景可見度的控制項，以及如何使用其來最佳化場景檢視和工作流程，您可以瀏覽 Unity 的<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">場景可見度</a>文件。</span><span class="sxs-lookup"><span data-stu-id="facd4-123">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can visit Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

## <a name="organizing-3d-objects-in-a-collection"></a><span data-ttu-id="facd4-124">組織集合中的 3D 物件</span><span class="sxs-lookup"><span data-stu-id="facd4-124">Organizing 3D objects in a collection</span></span>

<span data-ttu-id="facd4-125">您將在本節建立 3D 物件的面板，並在本教學課程的後續各節中，使用此面板來探索與 3D 物件互動的各種方式。</span><span class="sxs-lookup"><span data-stu-id="facd4-125">In this section, you will create a panel of 3D objects which you will use when exploring various ways of interacting with 3D objects in the following sections of this tutorial.</span></span> <span data-ttu-id="facd4-126">具體而言，您會將 3D 物件的位置設定在 3 x 3 的方格上。</span><span class="sxs-lookup"><span data-stu-id="facd4-126">Specifically, you will configure the 3D objects to be positioned on a 3 x 3 grid.</span></span>

<span data-ttu-id="facd4-127">與[建立按鈕面板](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection)時類似，達成此動作所需採取的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="facd4-127">Similarly to when you [created a panel of buttons](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), the main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="facd4-128">使 3D 物件歸屬於父物件</span><span class="sxs-lookup"><span data-stu-id="facd4-128">Parent the 3D objects to a parent object</span></span>
2. <span data-ttu-id="facd4-129">新增和設定 Grid Object Collection (指令碼) 元件</span><span class="sxs-lookup"><span data-stu-id="facd4-129">Add and configure the Grid Object Collection (Script) component</span></span>

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a><span data-ttu-id="facd4-130">1.使 3D 物件歸屬於父物件</span><span class="sxs-lookup"><span data-stu-id="facd4-130">1. Parent the 3D objects to a parent object</span></span>

<span data-ttu-id="facd4-131">在 [階層] 視窗中，**建立空白物件**、提供適當的名稱 (例如 **3DObjectCollection**)，然後將其放在適當的位置，例如 X = 0、Y =-0.2、Z = 2。</span><span class="sxs-lookup"><span data-stu-id="facd4-131">In the Hierarchy window, **create an empty object**, give it a suitable name, for example, **3DObjectCollection**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

<span data-ttu-id="facd4-132">在 [專案] 視窗中，瀏覽至 [資產]   > [MRTK.Tutorials.GettingStarted]   > [Prefabs]  ，然後使 **3DObjectCollection** 成為下列 Prefab 的**父系**：</span><span class="sxs-lookup"><span data-stu-id="facd4-132">In the Project window, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**, then **parent** the following prefabs to the **3DObjectCollection**:</span></span>

* <span data-ttu-id="facd4-133">Cheese</span><span class="sxs-lookup"><span data-stu-id="facd4-133">Cheese</span></span>
* <span data-ttu-id="facd4-134">CoffeeCup</span><span class="sxs-lookup"><span data-stu-id="facd4-134">CoffeeCup</span></span>
* <span data-ttu-id="facd4-135">EarthCore</span><span class="sxs-lookup"><span data-stu-id="facd4-135">EarthCore</span></span>
* <span data-ttu-id="facd4-136">Octa</span><span class="sxs-lookup"><span data-stu-id="facd4-136">Octa</span></span>
* <span data-ttu-id="facd4-137">Platonic</span><span class="sxs-lookup"><span data-stu-id="facd4-137">Platonic</span></span>
* <span data-ttu-id="facd4-138">TheModule</span><span class="sxs-lookup"><span data-stu-id="facd4-138">TheModule</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

<span data-ttu-id="facd4-140">在 [階層] 視窗中，**建立三個立方體**來作為 **3DObjectCollection** 的子物件，並將其變形**縮放**調整為 X = 0.15，Y = 0.15，Z = 0.15：</span><span class="sxs-lookup"><span data-stu-id="facd4-140">In the Hierarchy window, **create three cubes** as a child objects of the **3DObjectCollection** and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="facd4-142">如需如何執行上述步驟的提示，您可以參閱[建立使用者介面和設定混合實境工具組](mrlearning-base-ch2.md)教學課程。</span><span class="sxs-lookup"><span data-stu-id="facd4-142">For a reminder on how to do the steps listed above, you can refer to the [Creating user interface and configure Mixed Reality Toolkit](mrlearning-base-ch2.md) tutorial.</span></span>

<span data-ttu-id="facd4-143">重新調整立方體的位置，讓您可以看到每個立方體：</span><span class="sxs-lookup"><span data-stu-id="facd4-143">Reposition the cubes so you can see each cube:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

<span data-ttu-id="facd4-145">在 [專案] 視窗中，瀏覽至 [資產]   > [MixedRealityToolkit]   > [StandardAssets]   > [材質]  ，以查看 MRTK 所提供的材質。</span><span class="sxs-lookup"><span data-stu-id="facd4-145">In the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Materials** to see materials provided with the MRTK.</span></span>

<span data-ttu-id="facd4-146">**按一下並拖曳**適當材質到每個立方體網格轉譯器的  「元素 0」屬性，例如：</span><span class="sxs-lookup"><span data-stu-id="facd4-146">**Click-and-drag** a suitable material on to each cube's Mesh Renderer **Materials** Element 0 property, for example:</span></span>

* <span data-ttu-id="facd4-147">MRTK_Standard_GlowingCyan</span><span class="sxs-lookup"><span data-stu-id="facd4-147">MRTK_Standard_GlowingCyan</span></span>
* <span data-ttu-id="facd4-148">MRTK_Standard_GlowingOrange</span><span class="sxs-lookup"><span data-stu-id="facd4-148">MRTK_Standard_GlowingOrange</span></span>
* <span data-ttu-id="facd4-149">MRTK_Standard_Green</span><span class="sxs-lookup"><span data-stu-id="facd4-149">MRTK_Standard_Green</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="facd4-151">2.新增和設定 Grid Object Collection (指令碼) 元件</span><span class="sxs-lookup"><span data-stu-id="facd4-151">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="facd4-152">將 **Grid Object Collection (指令碼)** 元件新增至 **3DObjectCollection** 物件，並依照下列方式進行設定：</span><span class="sxs-lookup"><span data-stu-id="facd4-152">Add a **Grid Object Collection (Script)** component to the **3DObjectCollection** object, and configure it as follows:</span></span>

* <span data-ttu-id="facd4-153">將**排序類型**變更為**子系順序**，以確保子物件會依照您將其放在父物件底下的順序排序</span><span class="sxs-lookup"><span data-stu-id="facd4-153">Change **Sort Type** to **Child Order** to ensure the child objects are sorted in the order you have placed them under the parent object</span></span>

<span data-ttu-id="facd4-154">然後按一下 [更新集合]  按鈕以套用新的設定：</span><span class="sxs-lookup"><span data-stu-id="facd4-154">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a><span data-ttu-id="facd4-156">操作 3D 物件</span><span class="sxs-lookup"><span data-stu-id="facd4-156">Manipulating 3D objects</span></span>

<span data-ttu-id="facd4-157">在本節中，您將新增一個功能，也就是您可以在上一節建立的面板中操作所有 3D 物件。</span><span class="sxs-lookup"><span data-stu-id="facd4-157">In this section, you will add the ability to manipulate all the 3D objects in the panel you created in the previous section.</span></span> <span data-ttu-id="facd4-158">此外，針對 Prefab 物件，您可以讓使用者透過追蹤的手部來觸及並抓取這些物件。</span><span class="sxs-lookup"><span data-stu-id="facd4-158">Additionally, for the prefab objects, you will enable users to reach out and grab these objects with tracked hands.</span></span> <span data-ttu-id="facd4-159">然後您會探索幾個可套用至物件的操作行為。</span><span class="sxs-lookup"><span data-stu-id="facd4-159">Then you will explore a few manipulation behaviors that you can apply to your objects.</span></span>

<span data-ttu-id="facd4-160">達成此動作所需採取的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="facd4-160">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="facd4-161">將 Manipulation Handler (指令碼) 元件新增至所有物件</span><span class="sxs-lookup"><span data-stu-id="facd4-161">Add the Manipulation Handler (Script) component to all the objects</span></span>
2. <span data-ttu-id="facd4-162">將 Near Interaction Grabbable (指令碼) 元件新增至 Prefab 物件</span><span class="sxs-lookup"><span data-stu-id="facd4-162">Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>
3. <span data-ttu-id="facd4-163">設定 Manipulation Handler (指令碼) 元件</span><span class="sxs-lookup"><span data-stu-id="facd4-163">Configure the Manipulation Handler (Script) component</span></span>

> [!IMPORTANT]
> <span data-ttu-id="facd4-164">若要能夠**操作物件**，該物件必須具有下列元件：</span><span class="sxs-lookup"><span data-stu-id="facd4-164">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="facd4-165">**Collider** 元件，例如 Box Collider</span><span class="sxs-lookup"><span data-stu-id="facd4-165">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="facd4-166">**Manipulation Handler (指令碼)** 元件</span><span class="sxs-lookup"><span data-stu-id="facd4-166">**Manipulation Handler (Script)** component</span></span>
>
> <span data-ttu-id="facd4-167">若要能夠以追蹤的手部**操作**及**抓取物件**，該物件必須具有下列元件：</span><span class="sxs-lookup"><span data-stu-id="facd4-167">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="facd4-168">**Collider** 元件，例如 Box Collider</span><span class="sxs-lookup"><span data-stu-id="facd4-168">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="facd4-169">**Manipulation Handler (指令碼)** 元件</span><span class="sxs-lookup"><span data-stu-id="facd4-169">**Manipulation Handler (Script)** component</span></span>
> * <span data-ttu-id="facd4-170">**Near Interaction Grabbable (指令碼)** 元件</span><span class="sxs-lookup"><span data-stu-id="facd4-170">**Near Interaction Grabbable (Script)** component</span></span>

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a><span data-ttu-id="facd4-171">1.將 Manipulation Handler (指令碼) 元件新增至所有物件</span><span class="sxs-lookup"><span data-stu-id="facd4-171">1. Add the Manipulation Handler (Script) component to all the objects</span></span>

<span data-ttu-id="facd4-172">在 [階層] 視窗中，選取 **Cheese** 物件，按住 **Shift** 鍵，然後選取**Cube () 2** 物件，並將 **Manipulation Handler (指令碼)** 元件新增至所有物件：</span><span class="sxs-lookup"><span data-stu-id="facd4-172">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **Cube () 2** object and add the **Manipulation Handler (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="facd4-174">基於本教學課程的目的，碰撞器 (Collider) 已新增至 Prefab。</span><span class="sxs-lookup"><span data-stu-id="facd4-174">For the purpose of this tutorial, colliders have already been added to the prefabs.</span></span> <span data-ttu-id="facd4-175">針對 Unity 基本類型 (例如立方體物件)，Collider 元件會在物件建立時自動新增。</span><span class="sxs-lookup"><span data-stu-id="facd4-175">For Unity primitives, such as the Cube objects, the Collider component is automatically added when the object is created.</span></span> <span data-ttu-id="facd4-176">在上圖中，碰撞器是以綠色外框表示。</span><span class="sxs-lookup"><span data-stu-id="facd4-176">In the image above, the colliders are represented by the green outlines.</span></span> <span data-ttu-id="facd4-177">若要深入了解碰撞器，您可以造訪 Unity 的<a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">碰撞器 (Collider)</a> 文件。</span><span class="sxs-lookup"><span data-stu-id="facd4-177">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a><span data-ttu-id="facd4-178">2.將 Near Interaction Grabbable (指令碼) 元件新增至 Prefab 物件</span><span class="sxs-lookup"><span data-stu-id="facd4-178">2. Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>

<span data-ttu-id="facd4-179">在 [階層] 視窗中，選取 **Cheese** 物件，按住 **Shift** 鍵，然後選取 **TheModule** 物件，並將 **Near Interaction Grabbable (指令碼)** 元件新增至所有物件：</span><span class="sxs-lookup"><span data-stu-id="facd4-179">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **TheModule** object and add the **Near Interaction Grabbable (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a><span data-ttu-id="facd4-181">3.設定 Manipulation Handler (指令碼) 元件</span><span class="sxs-lookup"><span data-stu-id="facd4-181">3. Configure the Manipulation Handler (Script) component</span></span>

#### <a name="default-manipulation"></a><span data-ttu-id="facd4-182">預設操作</span><span class="sxs-lookup"><span data-stu-id="facd4-182">Default manipulation</span></span>

<span data-ttu-id="facd4-183">針對**立方體**物件，請保留所有預設屬性，以體驗預設的操作行為：</span><span class="sxs-lookup"><span data-stu-id="facd4-183">For the **Cube** object, leave all properties at default, to experience the default manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> <span data-ttu-id="facd4-185">若要將元件重設為預設值，您可以選取元件的 [設定] 圖示，然後選取 [重設]。</span><span class="sxs-lookup"><span data-stu-id="facd4-185">To reset a component to its default values, you can select the component's Settings icon and select Reset.</span></span>

#### <a name="restrict-manipulation-to-scale-only"></a><span data-ttu-id="facd4-186">將操作限制為僅限縮放</span><span class="sxs-lookup"><span data-stu-id="facd4-186">Restrict manipulation to scale only</span></span>

<span data-ttu-id="facd4-187">針對 **Cube (1)** 物件，請將**縮放**的**兩手操作類型**變更為只允許使用者變更物件的大小：</span><span class="sxs-lookup"><span data-stu-id="facd4-187">For the **Cube (1)** object, change **Two Handed Manipulation Type** to **Scale** to only allow the user to change the object's size:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a><span data-ttu-id="facd4-189">將移動限制為與使用者的固定距離</span><span class="sxs-lookup"><span data-stu-id="facd4-189">Constrain the movement to a fixed distance from the user</span></span>

<span data-ttu-id="facd4-190">針對 **Cube (2)** 物件，請將 [移動限制]  變更為**與手部的固定距離**，如此一來，當物件移動時，物件就會與使用者保持相同的距離：</span><span class="sxs-lookup"><span data-stu-id="facd4-190">For the **Cube (2)** object, change **Constraint On Movement** to **Fix Distance From Head** so that when the object is moved, it stays at the same distance from the user:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a><span data-ttu-id="facd4-192">預設抓取操作</span><span class="sxs-lookup"><span data-stu-id="facd4-192">Default grabbable manipulation</span></span>

<span data-ttu-id="facd4-193">針對 **Cheese**、**CoffeCup**和 **EarthCore** 物件，請保留所有預設屬性，以體驗預設的抓取操作行為：</span><span class="sxs-lookup"><span data-stu-id="facd4-193">For the **Cheese**, **CoffeCup**, and **EarthCore** objects, leave all properties at default, to experience the default grabbable manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a><span data-ttu-id="facd4-195">移除遠端操作的能力</span><span class="sxs-lookup"><span data-stu-id="facd4-195">Remove the ability of far manipulation</span></span>

<span data-ttu-id="facd4-196">針對 **Octa** 物件，請取消勾選 [允許遠端操作]  核取方塊，讓使用者只能使用追蹤的手部直接與物件互動：</span><span class="sxs-lookup"><span data-stu-id="facd4-196">For the **Octa** object, un-check the **Allow Far Manipulation** checkbox to make it so the user can only interact with the object directly using tracked hands:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a><span data-ttu-id="facd4-198">使物件繞著中心旋轉</span><span class="sxs-lookup"><span data-stu-id="facd4-198">Make an object rotate around its center</span></span>

<span data-ttu-id="facd4-199">針對 **Platonic** 物件，請將**近處單手旋轉模式**和**遠處單手旋轉模式**變更為**繞著物件中心旋轉**，讓使用者以單手旋轉物件時，物件能繞著其中心旋轉：</span><span class="sxs-lookup"><span data-stu-id="facd4-199">For the **Platonic** object, change **One Hand Rotation Mode Near** and **One Hand Rotation Mode Far** to **Rotate About Object Center** to make it so when the user rotates the object with one hand, it rotates around the object's center:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="keep-movement-after-object-is-released"></a><span data-ttu-id="facd4-201">物件釋放後繼續移動</span><span class="sxs-lookup"><span data-stu-id="facd4-201">Keep movement after object is released</span></span>

<span data-ttu-id="facd4-202">針對 **TheModule** 物件，新增 **Rigidbody** 元件以啟用物理特性，然後取消核取 [使用引力]  核取方塊，讓物件不會受到引力的影響：</span><span class="sxs-lookup"><span data-stu-id="facd4-202">For the **TheModule** object, add a **Rigidbody** component to enable physics, and then un-check the **Use Gravity** checkbox so the object is not affected by gravity:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

<span data-ttu-id="facd4-204">回到 Manipulation Handler (指令碼) 元件，確認 [放開行為]  已設定為 [保持速度]  和 [保持角速度]  ，如此一來，物件從使用者的手中放開時，仍會繼續移動：</span><span class="sxs-lookup"><span data-stu-id="facd4-204">Back on the Manipulation Handler (Script) component, verify that the **Release Behavior** is set to both **Keep Velocity** and **Keep Angular Velocity** so that once the object is released from the user's hand, it continues to move:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-8.png)

<span data-ttu-id="facd4-206">若要深入了解操作處理器元件及其相關聯的屬性，您可以瀏覽 [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[操作處理器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) 指南。</span><span class="sxs-lookup"><span data-stu-id="facd4-206">To learn more about the Manipulation handler component and its associated properties, you can visit the [Manipulation handler](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="facd4-207">新增週框方塊</span><span class="sxs-lookup"><span data-stu-id="facd4-207">Adding bounding boxes</span></span>

<span data-ttu-id="facd4-208">周框方塊藉由提供可用於縮放和旋轉的控點，讓您能夠更輕鬆且更直覺地以單手操作可遠近互動的物件。</span><span class="sxs-lookup"><span data-stu-id="facd4-208">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="facd4-209">在此範例中，您會將周框方塊新增至 EarthCore 物件，讓此物件現在可以使用您在上一節中設定的物件操作來與之互動，以及使用周框方塊控點來縮放和旋轉。</span><span class="sxs-lookup"><span data-stu-id="facd4-209">In this example, you will add a bounding box to the EarthCore object so this object can now be interacted with using the object manipulation you configured in the previous section, as well as, scaled and rotated using the bounding box handles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="facd4-210">若要能夠使用**周框方塊**，該物件必須具有下列元件：</span><span class="sxs-lookup"><span data-stu-id="facd4-210">To be able to use a **bounding box**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="facd4-211">**Collider** 元件，例如 Box Collider</span><span class="sxs-lookup"><span data-stu-id="facd4-211">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="facd4-212">**Bounding Box (指令碼)** 元件</span><span class="sxs-lookup"><span data-stu-id="facd4-212">**Bounding Box (Script)** component</span></span>

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a><span data-ttu-id="facd4-213">1.將 Bounding Box (指令碼) 元件新增至 EarthCore 物件</span><span class="sxs-lookup"><span data-stu-id="facd4-213">1. Add the Bounding Box (Script) component to the EarthCore object</span></span>

<span data-ttu-id="facd4-214">在 [偵測器] 視窗中，選取 **EarthCore** 物件，並將 **Bounding Box (指令碼)** 元件新增至 EarthCore 物件：</span><span class="sxs-lookup"><span data-stu-id="facd4-214">In the Inspector window, select the **EarthCore** object and add the **Bounding Box (Script)** component to the EarthCore object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> <span data-ttu-id="facd4-216">周框方塊視覺效果會在執行階段中建立，因此在您進入遊戲模式之前看不到該效果。</span><span class="sxs-lookup"><span data-stu-id="facd4-216">The Bounding Box visualizations is created at run time and therefore not visible before you enter Game mode.</span></span>

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a><span data-ttu-id="facd4-217">2.使用編輯器內模擬來視覺化和測試周框方塊</span><span class="sxs-lookup"><span data-stu-id="facd4-217">2. Visualize and test the bounding box using the in-editor simulation</span></span>

<span data-ttu-id="facd4-218">按下 [開始遊戲] 按鈕進入遊戲模式。</span><span class="sxs-lookup"><span data-stu-id="facd4-218">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="facd4-219">然後按住空格鍵以顯示手部，並使用滑鼠來與周框方塊互動：</span><span class="sxs-lookup"><span data-stu-id="facd4-219">Then press and hold the spacebar to bring up the hand and use the mouse to interact with the bounding box:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

<span data-ttu-id="facd4-221">若要深入了解 Bounding Box 元件和其相關聯的屬性，您可以瀏覽 [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[周框方塊](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)指南。</span><span class="sxs-lookup"><span data-stu-id="facd4-221">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-touch-effects"></a><span data-ttu-id="facd4-222">新增觸控效果</span><span class="sxs-lookup"><span data-stu-id="facd4-222">Adding touch effects</span></span>

<span data-ttu-id="facd4-223">在此範例中，您將會啟用當您以手部觸碰物件時所要觸發的事件。</span><span class="sxs-lookup"><span data-stu-id="facd4-223">In this example, you will enable events to be triggered when you touch an object with your hand.</span></span> <span data-ttu-id="facd4-224">具體而言，您會將 Octa 物件設定為在使用者與之接觸時播放音效。</span><span class="sxs-lookup"><span data-stu-id="facd4-224">Specifically, you will configure the Octa object to play a sound effect when the user touches it.</span></span>

<span data-ttu-id="facd4-225">達成此動作所需採取的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="facd4-225">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="facd4-226">將音訊來源元件新增至物件中</span><span class="sxs-lookup"><span data-stu-id="facd4-226">Add an Audio Source component to the object</span></span>
2. <span data-ttu-id="facd4-227">將 Near Interaction Touchable (指令碼) 元件新增至物件</span><span class="sxs-lookup"><span data-stu-id="facd4-227">Add the Near Interaction Touchable (Script) component to the object</span></span>
3. <span data-ttu-id="facd4-228">將 Hand Interaction Touch (指令碼) 元件新增至物件</span><span class="sxs-lookup"><span data-stu-id="facd4-228">Add the Hand Interaction Touch (Script) component to the object</span></span>
4. <span data-ttu-id="facd4-229">執行 On Touch Started 事件</span><span class="sxs-lookup"><span data-stu-id="facd4-229">Implement the On Touch Started event</span></span>
5. <span data-ttu-id="facd4-230">使用編輯器內的模擬來測試觸控互動</span><span class="sxs-lookup"><span data-stu-id="facd4-230">Test the touch interaction using the in-editor simulation</span></span>

> [!IMPORTANT]
> <span data-ttu-id="facd4-231">若要能夠**觸發觸控事件**，該物件必須具有下列元件：</span><span class="sxs-lookup"><span data-stu-id="facd4-231">To be able to **trigger touch events**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="facd4-232">**Collider** 元件，最好是 Box Collider</span><span class="sxs-lookup"><span data-stu-id="facd4-232">**Collider** component, preferably a Box Collider</span></span>
> * <span data-ttu-id="facd4-233">**Near Interaction Touchable (指令碼)** 元件</span><span class="sxs-lookup"><span data-stu-id="facd4-233">**Near Interaction Touchable (Script)** component</span></span>
> * <span data-ttu-id="facd4-234">**Hand Interaction Touch (指令碼)** 元件</span><span class="sxs-lookup"><span data-stu-id="facd4-234">**Hand Interaction Touch (Script)** component</span></span>

> [!NOTE]
> <span data-ttu-id="facd4-235">Hand Interaction Touch (指令碼) 元件不是 MRTK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="facd4-235">The Hand Interaction Touch (Script) component is not part of MRTK.</span></span> <span data-ttu-id="facd4-236">該元件隨著本教學課程的資產一起匯入，原本是 MixedReality 工具組 Unity 範例的一部份。</span><span class="sxs-lookup"><span data-stu-id="facd4-236">It was imported with this tutorial's assets and originally part of the MixedReality Toolkit Unity Examples.</span></span>

### <a name="1-add-an-audio-source-component-to-the-object"></a><span data-ttu-id="facd4-237">1.將音訊來源元件新增至物件中</span><span class="sxs-lookup"><span data-stu-id="facd4-237">1. Add an Audio Source component to the object</span></span>

<span data-ttu-id="facd4-238">在 [階層] 視窗中，選取 **Octa** 物件，將**音訊來源**元件新增至顆 Octa 物件，然後將**空間混合**變更為 1，以啟用空間音訊：</span><span class="sxs-lookup"><span data-stu-id="facd4-238">In the Hierarchy window, select the **Octa** object, add an **Audio Source** component to the Octa object, and then change **Spatial Blend** to 1 to enable spatial audio:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a><span data-ttu-id="facd4-240">2.將 Near Interaction Touchable (指令碼) 元件新增至物件</span><span class="sxs-lookup"><span data-stu-id="facd4-240">2. Add the Near Interaction Touchable (Script) component to the object</span></span>

<span data-ttu-id="facd4-241">在仍選取 **Octa** 物件的情況下，將 **Near Interaction Touchable (指令碼)** 元件新增至 Octa 物件，然後按一下 [修正周框]  和 [修正中心]  按鈕，以更新 Near Interaction Touchable (指令碼) 的區域中心和界限屬性來符合 BoxCollider：</span><span class="sxs-lookup"><span data-stu-id="facd4-241">With the **Octa** object still selected, add the **Near Interaction Touchable (Script)** component to the Octa object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a><span data-ttu-id="facd4-243">3.將 Hand Interaction Touch (指令碼) 元件新增至物件</span><span class="sxs-lookup"><span data-stu-id="facd4-243">3. Add the Hand Interaction Touch (Script) component to the object</span></span>

<span data-ttu-id="facd4-244">在仍選取 **Octa** 物件的情況下，將 **Hand Interaction Touch (指令碼)** 元件新增至 Octa 物件：</span><span class="sxs-lookup"><span data-stu-id="facd4-244">With the **Octa** object still selected, add the **Hand Interaction Touch (Script)** component to the Octa object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a><span data-ttu-id="facd4-246">4.執行 On Touch Started 事件</span><span class="sxs-lookup"><span data-stu-id="facd4-246">4. Implement the On Touch Started event</span></span>

<span data-ttu-id="facd4-247">在 **Hand Interaction Touch (指令碼)** 元件上按一下小的 **[+]** 圖示，即可建立新的 **On Touch Started ()** 事件。</span><span class="sxs-lookup"><span data-stu-id="facd4-247">On the **Hand Interaction Touch (Script)** component, click the small **+** icon to create a new **On Touch Started ()** event.</span></span> <span data-ttu-id="facd4-248">然後設定 **Octa** 物件以接收事件，並將 **AudioSource.PlayOneShot** 定義為要觸發的動作：</span><span class="sxs-lookup"><span data-stu-id="facd4-248">Then configure the **Octa** object to receive the event and define **AudioSource.PlayOneShot** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

<span data-ttu-id="facd4-250">瀏覽至 [資產]   > [MixedRealityToolkit.SDK]   > [StandardAssets]   > [音訊]  材質，以查看 MRTK 所提供的音訊片段，然後將適當的音訊片段指派給 [音訊片段]  欄位，例如 MRTK_Gem 音訊片段：</span><span class="sxs-lookup"><span data-stu-id="facd4-250">Navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Audio** to see audio clips provided with the MRTK, and then assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> <span data-ttu-id="facd4-252">如需有關如何實作事件的提示，您可以參閱[手部追蹤手勢和可互動按鈕](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)的指示。</span><span class="sxs-lookup"><span data-stu-id="facd4-252">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a><span data-ttu-id="facd4-253">5.使用編輯器內的模擬來測試觸控互動</span><span class="sxs-lookup"><span data-stu-id="facd4-253">5. Test the touch interaction using the in-editor simulation</span></span>

<span data-ttu-id="facd4-254">按下 [開始遊戲] 按鈕進入遊戲模式。</span><span class="sxs-lookup"><span data-stu-id="facd4-254">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="facd4-255">然後按住空格鍵以顯示手部，並使用滑鼠來碰觸 Octa 物件及觸發音效：</span><span class="sxs-lookup"><span data-stu-id="facd4-255">Then press and hold the spacebar to bring up the hand and use the mouse to touch the Octa object and trigger the sound effect:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> <span data-ttu-id="facd4-257">如上圖所示，當您在測試觸控互動時，您會看到 Octa 物件的顏色閃爍。</span><span class="sxs-lookup"><span data-stu-id="facd4-257">As you saw when testing the touch interaction, and as shown in the image above, the Octa object color pulsated while it was touched.</span></span> <span data-ttu-id="facd4-258">此效果已硬式編碼到 Hand Interaction Touch (指令碼) 元件中，而不是您在上述步驟中完成的事件設定結果。</span><span class="sxs-lookup"><span data-stu-id="facd4-258">This effect is hard coded into the Hand Interaction Touch (Script) component and not a result of the event configuration you completed in the steps above.</span></span>
>
> <span data-ttu-id="facd4-259">如果您想要停用此效果，您可以在第 32 行上加上 'TargetRenderer = GetComponentInChildren<Renderer>();' 註解，這會使得 TargetRenderer 保持 Null，並讓色彩不會閃爍。</span><span class="sxs-lookup"><span data-stu-id="facd4-259">If you want to disable this effect, you can, for example, comment out or line 32 'TargetRenderer = GetComponentInChildren<Renderer>();' which will result in the TargetRenderer remaining null and the color not pulsating.</span></span>

## <a name="congratulations"></a><span data-ttu-id="facd4-260">恭喜！</span><span class="sxs-lookup"><span data-stu-id="facd4-260">Congratulations</span></span>

<span data-ttu-id="facd4-261">在本教學課程中，您已了解如何在方格集合中組織 3D 物件以及如何使用近距互動 (使用手部追蹤直接抓取) 和遠距互動 (使用目光或手動光線) 來操作這些物件 (縮放、旋轉和移動)。</span><span class="sxs-lookup"><span data-stu-id="facd4-261">In this tutorial, you learned how to organize 3D objects in a grid collection and how to manipulate these objects (scaling, rotating, and moving) using near interaction (directly grabbing with tracked hands) and far interaction (using gaze rays or hand rays).</span></span> <span data-ttu-id="facd4-262">您也已了解如何在 3D 物件周圍放置週框方塊，並了解如何在週框方塊上使用和自訂控點。</span><span class="sxs-lookup"><span data-stu-id="facd4-262">You also learned how to put bounding boxes around 3D objects, and learned how to use and customize the handles on the bounding boxes.</span></span> <span data-ttu-id="facd4-263">最後，您學習到觸控物件時如何觸發事件。</span><span class="sxs-lookup"><span data-stu-id="facd4-263">Finally, you learned how to trigger events when touching an object.</span></span>

[<span data-ttu-id="facd4-264">下一課：6.探索進階的輸入選項</span><span class="sxs-lookup"><span data-stu-id="facd4-264">Next Lesson: 6. Exploring advanced input options</span></span>](mrlearning-base-ch5.md)
