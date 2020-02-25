---
title: 快速入門教學課程-5。 與3D 物件互動
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 7eb38e205237257e400550299fdeebb73ba746f1
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77555457"
---
# <a name="5-interacting-with-3d-objects"></a><span data-ttu-id="07522-104">5. 與3D 物件互動</span><span class="sxs-lookup"><span data-stu-id="07522-104">5. Interacting with 3D objects</span></span>

<span data-ttu-id="07522-105">在本教學課程中，您將瞭解基本的3D 內容和使用者體驗，例如將3D 物件組織為集合的一部分、進行基本操作的周框方塊、近遠的互動，以及觸控和抓取手勢與手動追蹤。</span><span class="sxs-lookup"><span data-stu-id="07522-105">In this tutorial, you will learn about basic 3D content and user experience, such as organizing 3D objects as part of a collection, bounding boxes for basic manipulation, near and far interaction, and touch and grab gestures with hand tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="07522-106">目標</span><span class="sxs-lookup"><span data-stu-id="07522-106">Objectives</span></span>

* <span data-ttu-id="07522-107">建立將用於其他學習目標的3D 物件面板</span><span class="sxs-lookup"><span data-stu-id="07522-107">Create a panel of 3D objects which will be used for the other learning objectives</span></span>
* <span data-ttu-id="07522-108">實作週框方塊</span><span class="sxs-lookup"><span data-stu-id="07522-108">Implement bounding boxes</span></span>
* <span data-ttu-id="07522-109">設定3D 物件進行基本操作，例如移動、旋轉和縮放</span><span class="sxs-lookup"><span data-stu-id="07522-109">Configure 3D objects for basic manipulation such as move, rotate, and scale</span></span>
* <span data-ttu-id="07522-110">探索遠近互動</span><span class="sxs-lookup"><span data-stu-id="07522-110">Explore near and far interaction</span></span>
* <span data-ttu-id="07522-111">深入瞭解其他的右手邊追蹤手勢，例如「抓取」和「觸控」</span><span class="sxs-lookup"><span data-stu-id="07522-111">Learn about additional hand tracking gestures, such as grab and touch</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="07522-112">匯入教學課程資產</span><span class="sxs-lookup"><span data-stu-id="07522-112">Importing the tutorial assets</span></span>

<span data-ttu-id="07522-113">下載並匯入 Unity 自訂套件：</span><span class="sxs-lookup"><span data-stu-id="07522-113">Download and import the Unity custom package:</span></span>

* [<span data-ttu-id="07522-114">MRTK.HoloLens2 GettingStarted. 2.3.0.2. unitypackage</span><span class="sxs-lookup"><span data-stu-id="07522-114">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)

<span data-ttu-id="07522-115">匯入教學課程資產之後，您的 [專案] 視窗看起來應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="07522-115">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="07522-117">如需有關如何匯入 Unity 自訂套件的提醒，您可以參閱匯[入混合現實工具](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)組指示。</span><span class="sxs-lookup"><span data-stu-id="07522-117">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="decluttering-the-scene-view"></a><span data-ttu-id="07522-118">Decluttering 場景視圖</span><span class="sxs-lookup"><span data-stu-id="07522-118">Decluttering the scene view</span></span>

<span data-ttu-id="07522-119">若要讓您更輕鬆地使用場景，請按一下物件左側的**眼睛**圖示，將**Cube**和**ButtonCollection**物件的**場景可見度**設定為 [關閉]。</span><span class="sxs-lookup"><span data-stu-id="07522-119">To make it easier to work with your scene, set the **scene visibility** for the **Cube** and **ButtonCollection** objects to off by clicking the **eye** icon to the left of the objects.</span></span> <span data-ttu-id="07522-120">這會在場景視窗中隱藏物件，而不會變更其遊戲內可見度：</span><span class="sxs-lookup"><span data-stu-id="07522-120">This hides the object in the Scene window without changing their in-game visibility:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="07522-122">若要深入瞭解場景可見度控制項，以及如何使用它們來優化場景視圖和工作流程，您可以造訪 Unity 的<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">場景可見度</a>檔。</span><span class="sxs-lookup"><span data-stu-id="07522-122">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can visit Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

## <a name="organizing-3d-objects-in-a-collection"></a><span data-ttu-id="07522-123">組織集合中的3D 物件</span><span class="sxs-lookup"><span data-stu-id="07522-123">Organizing 3D objects in a collection</span></span>

<span data-ttu-id="07522-124">在本節中，您將建立3D 物件的面板，當您在本教學課程的下列各節中探索與3D 物件互動的各種方式時，將會用到它。</span><span class="sxs-lookup"><span data-stu-id="07522-124">In this section, you will create a panel of 3D objects which you will use when exploring various ways of interacting with 3D objects in the following sections of this tutorial.</span></span> <span data-ttu-id="07522-125">具體而言，您會將3D 物件設定為置於 3 x 3 方格上。</span><span class="sxs-lookup"><span data-stu-id="07522-125">Specifically, you will configure the 3D objects to be positioned on a 3 x 3 grid.</span></span>

<span data-ttu-id="07522-126">類似于當您[建立按鈕的面板](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection)時，要達到此目標所要採取的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="07522-126">Similarly to when you [created a panel of buttons](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), the main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="07522-127">將3D 物件父系到父物件</span><span class="sxs-lookup"><span data-stu-id="07522-127">Parent the 3D objects to a parent object</span></span>
2. <span data-ttu-id="07522-128">加入和設定 Grid 物件集合（腳本）元件</span><span class="sxs-lookup"><span data-stu-id="07522-128">Add and configure the Grid Object Collection (Script) component</span></span>

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a><span data-ttu-id="07522-129">1. 將3D 物件父系到父物件</span><span class="sxs-lookup"><span data-stu-id="07522-129">1. Parent the 3D objects to a parent object</span></span>

<span data-ttu-id="07522-130">在 [階層] 視窗中，**建立空的物件**、提供適當的名稱（例如**3DObjectCollection**），並將它放在適當的位置，例如 X = 0、Y =-0.2、Z = 2。</span><span class="sxs-lookup"><span data-stu-id="07522-130">In the Hierarchy window, **create an empty object**, give it a suitable name, for example, **3DObjectCollection**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

<span data-ttu-id="07522-131">在 [專案] 視窗中，流覽至 [**資產**] [ > **MRTK]。GettingStarted** > **Prefabs**，然後將下列 Prefabs 的**父系**加入**3DObjectCollection**：</span><span class="sxs-lookup"><span data-stu-id="07522-131">In the Project window, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**, then **parent** the following prefabs to the **3DObjectCollection**:</span></span>

* <span data-ttu-id="07522-132">比薩餅</span><span class="sxs-lookup"><span data-stu-id="07522-132">Cheese</span></span>
* <span data-ttu-id="07522-133">CoffeeCup</span><span class="sxs-lookup"><span data-stu-id="07522-133">CoffeeCup</span></span>
* <span data-ttu-id="07522-134">EarthCore</span><span class="sxs-lookup"><span data-stu-id="07522-134">EarthCore</span></span>
* <span data-ttu-id="07522-135">顆 octa</span><span class="sxs-lookup"><span data-stu-id="07522-135">Octa</span></span>
* <span data-ttu-id="07522-136">Platonic</span><span class="sxs-lookup"><span data-stu-id="07522-136">Platonic</span></span>
* <span data-ttu-id="07522-137">TheModule</span><span class="sxs-lookup"><span data-stu-id="07522-137">TheModule</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

<span data-ttu-id="07522-139">在 [階層] 視窗中，**建立三個 cube**做為**3DObjectCollection**的子物件，並將其轉換**規模**設定為 X = 0.15、Y = 0.15、Z = 0.15：</span><span class="sxs-lookup"><span data-stu-id="07522-139">In the Hierarchy window, **create three cubes** as a child objects of the **3DObjectCollection** and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="07522-141">如需有關如何執行上述步驟的提醒，您可以參閱[建立使用者介面和設定混合現實工具](mrlearning-base-ch2.md)組教學課程。</span><span class="sxs-lookup"><span data-stu-id="07522-141">For a reminder on how to do the steps listed above, you can refer to the [Creating user interface and configure Mixed Reality Toolkit](mrlearning-base-ch2.md) tutorial.</span></span>

<span data-ttu-id="07522-142">重新調整 cube 的位置，讓您可以看到每個 cube：</span><span class="sxs-lookup"><span data-stu-id="07522-142">Reposition the cubes so you can see each cube:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

<span data-ttu-id="07522-144">在 [專案] 視窗中，流覽至 [**資產**] [ > **MixedRealityToolkit** ] [ > **StandardAssets** > **材質**]，以查看 MRTK 所提供的材質。</span><span class="sxs-lookup"><span data-stu-id="07522-144">In the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Materials** to see materials provided with the MRTK.</span></span>

<span data-ttu-id="07522-145">**按一下並拖曳**適當的資料到每個 Cube 的網格轉譯器**材質**元素0屬性，例如：</span><span class="sxs-lookup"><span data-stu-id="07522-145">**Click-and-drag** a suitable material on to each cube's Mesh Renderer **Materials** Element 0 property, for example:</span></span>

* <span data-ttu-id="07522-146">MRTK_Standard_GlowingCyan</span><span class="sxs-lookup"><span data-stu-id="07522-146">MRTK_Standard_GlowingCyan</span></span>
* <span data-ttu-id="07522-147">MRTK_Standard_GlowingOrange</span><span class="sxs-lookup"><span data-stu-id="07522-147">MRTK_Standard_GlowingOrange</span></span>
* <span data-ttu-id="07522-148">MRTK_Standard_Green</span><span class="sxs-lookup"><span data-stu-id="07522-148">MRTK_Standard_Green</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="07522-150">2. 加入及設定 Grid 物件集合（腳本）元件</span><span class="sxs-lookup"><span data-stu-id="07522-150">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="07522-151">將**Grid 物件集合（腳本）** 元件新增至**3DObjectCollection**物件，並將其設定如下：</span><span class="sxs-lookup"><span data-stu-id="07522-151">Add a **Grid Object Collection (Script)** component to the **3DObjectCollection** object, and configure it as follows:</span></span>

* <span data-ttu-id="07522-152">將 [**排序類型**] 變更為 [**子順序**]，以確保子物件會依照您放在父物件底下的順序排序</span><span class="sxs-lookup"><span data-stu-id="07522-152">Change **Sort Type** to **Child Order** to ensure the child objects are sorted in the order you have placed them under the parent object</span></span>

<span data-ttu-id="07522-153">然後按一下 [**更新集合**] 按鈕以套用新的設定：</span><span class="sxs-lookup"><span data-stu-id="07522-153">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a><span data-ttu-id="07522-155">操作3D 物件</span><span class="sxs-lookup"><span data-stu-id="07522-155">Manipulating 3D objects</span></span>

<span data-ttu-id="07522-156">在本節中，您將新增在上一節中建立的面板中操作所有3D 物件的功能。</span><span class="sxs-lookup"><span data-stu-id="07522-156">In this section, you will add the ability to manipulate all the 3D objects in the panel you created in the previous section.</span></span> <span data-ttu-id="07522-157">此外，針對 prefab 物件，您可以讓使用者透過追蹤的手觸達這些物件，並將其抓取。</span><span class="sxs-lookup"><span data-stu-id="07522-157">Additionally, for the prefab objects, you will enable users to reach out and grab these objects with tracked hands.</span></span> <span data-ttu-id="07522-158">然後您會探索幾個可套用至物件的操作行為。</span><span class="sxs-lookup"><span data-stu-id="07522-158">Then you will explore a few manipulation behaviors that you can apply to your objects.</span></span>

<span data-ttu-id="07522-159">達成此目標所需採取的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="07522-159">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="07522-160">將操作處理常式（腳本）元件新增至所有物件</span><span class="sxs-lookup"><span data-stu-id="07522-160">Add the Manipulation Handler (Script) component to all the objects</span></span>
2. <span data-ttu-id="07522-161">將近乎互動 Grabbable （腳本）元件新增至 prefab 物件</span><span class="sxs-lookup"><span data-stu-id="07522-161">Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>
3. <span data-ttu-id="07522-162">設定操作處理常式（腳本）元件</span><span class="sxs-lookup"><span data-stu-id="07522-162">Configure the Manipulation Handler (Script) component</span></span>

> [!IMPORTANT]
> <span data-ttu-id="07522-163">若要能夠**操作物件**，物件必須具有下列元件：</span><span class="sxs-lookup"><span data-stu-id="07522-163">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="07522-164">**碰撞**元件，例如 Box 碰撞</span><span class="sxs-lookup"><span data-stu-id="07522-164">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="07522-165">**操作處理常式（腳本）** 元件</span><span class="sxs-lookup"><span data-stu-id="07522-165">**Manipulation Handler (Script)** component</span></span>
>
> <span data-ttu-id="07522-166">若要能夠**操作**和**抓取具有已追蹤手的物件**，物件必須具有下列元件：</span><span class="sxs-lookup"><span data-stu-id="07522-166">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="07522-167">**碰撞**元件，例如 Box 碰撞</span><span class="sxs-lookup"><span data-stu-id="07522-167">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="07522-168">**操作處理常式（腳本）** 元件</span><span class="sxs-lookup"><span data-stu-id="07522-168">**Manipulation Handler (Script)** component</span></span>
> * <span data-ttu-id="07522-169">**近乎互動 Grabbable （腳本）** 元件</span><span class="sxs-lookup"><span data-stu-id="07522-169">**Near Interaction Grabbable (Script)** component</span></span>

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a><span data-ttu-id="07522-170">1. 將操作處理常式（腳本）元件加入至所有物件</span><span class="sxs-lookup"><span data-stu-id="07522-170">1. Add the Manipulation Handler (Script) component to all the objects</span></span>

<span data-ttu-id="07522-171">在 [階層] 視窗中，選取 [**乳酪**] 物件，按住**Shift**鍵，然後選取**Cube （） 2**物件，並將**操作處理常式（腳本）** 元件加入至所有物件：</span><span class="sxs-lookup"><span data-stu-id="07522-171">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **Cube () 2** object and add the **Manipulation Handler (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="07522-173">基於本教學課程的目的，colliders 已新增至 prefabs。</span><span class="sxs-lookup"><span data-stu-id="07522-173">For the purpose of this tutorial, colliders have already been added to the prefabs.</span></span> <span data-ttu-id="07522-174">對於 Unity 基本類型（例如 Cube 物件），當建立物件時，會自動新增碰撞元件。</span><span class="sxs-lookup"><span data-stu-id="07522-174">For Unity primitives, such as the Cube objects, the Collider component is automatically added when the object is created.</span></span> <span data-ttu-id="07522-175">在上圖中，colliders 是以綠色外框表示。</span><span class="sxs-lookup"><span data-stu-id="07522-175">In the image above, the colliders are represented by the green outlines.</span></span> <span data-ttu-id="07522-176">若要深入瞭解 colliders，您可以造訪 Unity 的<a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">碰撞</a>器檔。</span><span class="sxs-lookup"><span data-stu-id="07522-176">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a><span data-ttu-id="07522-177">2. 將近乎互動 Grabbable （腳本）元件新增至 prefab 物件</span><span class="sxs-lookup"><span data-stu-id="07522-177">2. Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>

<span data-ttu-id="07522-178">在 [階層] 視窗中，選取 [**乳酪**] 物件，按住**Shift**鍵，然後選取 [ **TheModule** ] 物件，並將**近端互動 Grabbable （腳本）** 元件新增至所有物件：</span><span class="sxs-lookup"><span data-stu-id="07522-178">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **TheModule** object and add the **Near Interaction Grabbable (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a><span data-ttu-id="07522-180">3. 設定操作處理常式（腳本）元件</span><span class="sxs-lookup"><span data-stu-id="07522-180">3. Configure the Manipulation Handler (Script) component</span></span>

#### <a name="default-manipulation"></a><span data-ttu-id="07522-181">預設操作</span><span class="sxs-lookup"><span data-stu-id="07522-181">Default manipulation</span></span>

<span data-ttu-id="07522-182">若為**Cube**物件，請保留所有屬性，以體驗預設的操作行為：</span><span class="sxs-lookup"><span data-stu-id="07522-182">For the **Cube** object, leave all properties at default, to experience the default manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> <span data-ttu-id="07522-184">若要將元件重設為預設值，您可以選取元件的 [設定] 圖示，然後選取 [重設]。</span><span class="sxs-lookup"><span data-stu-id="07522-184">To reset a component to its default values, you can select the component's Settings icon and select Reset.</span></span>

#### <a name="restrict-manipulation-to-scale-only"></a><span data-ttu-id="07522-185">將操作限制為僅限縮放</span><span class="sxs-lookup"><span data-stu-id="07522-185">Restrict manipulation to scale only</span></span>

<span data-ttu-id="07522-186">針對**Cube （1）** 物件，將**兩個右手操作類型**變更為 [**調整**]，只允許使用者變更物件的大小：</span><span class="sxs-lookup"><span data-stu-id="07522-186">For the **Cube (1)** object, change **Two Handed Manipulation Type** to **Scale** to only allow the user to change the object's size:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a><span data-ttu-id="07522-188">將移動限制為與使用者的固定距離</span><span class="sxs-lookup"><span data-stu-id="07522-188">Constrain the movement to a fixed distance from the user</span></span>

<span data-ttu-id="07522-189">針對**Cube （2）** 物件，變更**移動上的條件約束**以**修正與 Head 的距離**，如此一來，當物件移動時，它就會與使用者保持相同的距離：</span><span class="sxs-lookup"><span data-stu-id="07522-189">For the **Cube (2)** object, change **Constraint On Movement** to **Fix Distance From Head** so that when the object is moved, it stays at the same distance from the user:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a><span data-ttu-id="07522-191">預設 grabbable 操作</span><span class="sxs-lookup"><span data-stu-id="07522-191">Default grabbable manipulation</span></span>

<span data-ttu-id="07522-192">針對 [**乳酪**]、[ **CoffeCup**] 和 [ **EarthCore** ] 物件，保留 [所有屬性]，以體驗預設的 grabbable 操作行為：</span><span class="sxs-lookup"><span data-stu-id="07522-192">For the **Cheese**, **CoffeCup**, and **EarthCore** objects, leave all properties at default, to experience the default grabbable manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a><span data-ttu-id="07522-194">移除目前操作的能力</span><span class="sxs-lookup"><span data-stu-id="07522-194">Remove the ability of far manipulation</span></span>

<span data-ttu-id="07522-195">若為**顆 octa**物件，請取消勾選 [**允許**最大操作] 核取方塊，讓使用者只能使用追蹤的手直接與物件互動：</span><span class="sxs-lookup"><span data-stu-id="07522-195">For the **Octa** object, un-check the **Allow Far Manipulation** checkbox to make it so the user can only interact with the object directly using tracked hands:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a><span data-ttu-id="07522-197">使物件繞著中心旋轉</span><span class="sxs-lookup"><span data-stu-id="07522-197">Make an object rotate around its center</span></span>

<span data-ttu-id="07522-198">針對**Platonic**物件，請將**一次**左右旋轉模式變更為接近，而在**一種旋轉模式**中**旋轉**，讓它在使用者手上旋轉物件時，旋轉物件中心：</span><span class="sxs-lookup"><span data-stu-id="07522-198">For the **Platonic** object, change **One Hand Rotation Mode Near** and **One Hand Rotation Mode Far** to **Rotate About Object Center** to make it so when the user rotates the object with one hand, it rotates around the object's center:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="keep-movement-after-object-is-released"></a><span data-ttu-id="07522-200">物件釋放後繼續移動</span><span class="sxs-lookup"><span data-stu-id="07522-200">Keep movement after object is released</span></span>

<span data-ttu-id="07522-201">針對**TheModule**物件，新增**Rigidbody**元件以啟用物理，然後取消核取 [**使用重心**] 核取方塊，讓物件不會受到引力的影響：</span><span class="sxs-lookup"><span data-stu-id="07522-201">For the **TheModule** object, add a **Rigidbody** component to enable physics, and then un-check the **Use Gravity** checkbox so the object is not affected by gravity:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

<span data-ttu-id="07522-203">回到 [操作處理常式（腳本）] 元件，確認 [**發行行為**] 已設定為 [**保持速度**] 並**保持 [角度] 速度**，以便在物件從使用者手中釋放後，它會繼續移動：</span><span class="sxs-lookup"><span data-stu-id="07522-203">Back on the Manipulation Handler (Script) component, verify that the **Release Behavior** is set to both **Keep Velocity** and **Keep Angular Velocity** so that once the object is released from the user's hand, it continues to move:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-8.png)

<span data-ttu-id="07522-205">若要深入瞭解操作處理常式元件及其相關聯的屬性，您可以造訪[MRTK 檔入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[操作處理常式](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)指南。</span><span class="sxs-lookup"><span data-stu-id="07522-205">To learn more about the Manipulation handler component and its associated properties, you can visit the [Manipulation handler](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="07522-206">加入周框方塊</span><span class="sxs-lookup"><span data-stu-id="07522-206">Adding bounding boxes</span></span>

<span data-ttu-id="07522-207">周框方塊藉由提供可用於縮放和旋轉的控制碼，讓您更輕鬆且更直覺地操作物件。</span><span class="sxs-lookup"><span data-stu-id="07522-207">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="07522-208">在此範例中，您會將周框方塊新增至 EarthCore 物件，因此這個物件現在可以使用您在上一節中設定的物件操作進行互動，以及使用周框方塊控點來縮放和旋轉。</span><span class="sxs-lookup"><span data-stu-id="07522-208">In this example, you will add a bounding box to the EarthCore object so this object can now be interacted with using the object manipulation you configured in the previous section, as well as, scaled and rotated using the bounding box handles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="07522-209">若要能夠使用周**框**方塊，物件必須具有下列元件：</span><span class="sxs-lookup"><span data-stu-id="07522-209">To be able to use a **bounding box**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="07522-210">**碰撞**元件，例如 Box 碰撞</span><span class="sxs-lookup"><span data-stu-id="07522-210">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="07522-211">周**框方塊（腳本）** 元件</span><span class="sxs-lookup"><span data-stu-id="07522-211">**Bounding Box (Script)** component</span></span>

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a><span data-ttu-id="07522-212">1. 將周框方塊（腳本）元件新增至 EarthCore 物件</span><span class="sxs-lookup"><span data-stu-id="07522-212">1. Add the Bounding Box (Script) component to the EarthCore object</span></span>

<span data-ttu-id="07522-213">在 [偵測器] 視窗中，選取**EarthCore**物件，並將周**框方塊（腳本）** 元件新增至 EarthCore 物件：</span><span class="sxs-lookup"><span data-stu-id="07522-213">In the Inspector window, select the **EarthCore** object and add the **Bounding Box (Script)** component to the EarthCore object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> <span data-ttu-id="07522-215">周框方塊視覺效果是在執行時間建立，因此在您進入遊戲模式之前看不到。</span><span class="sxs-lookup"><span data-stu-id="07522-215">The Bounding Box visualizations is created at run time and therefore not visible before you enter Game mode.</span></span>

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a><span data-ttu-id="07522-216">2. 使用編輯器內模擬來視覺化和測試周框方塊</span><span class="sxs-lookup"><span data-stu-id="07522-216">2. Visualize and test the bounding box using the in-editor simulation</span></span>

<span data-ttu-id="07522-217">按下 [播放] 按鈕進入遊戲模式。</span><span class="sxs-lookup"><span data-stu-id="07522-217">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="07522-218">然後按住空格鍵以顯示手，並使用滑鼠來與周框方塊互動：</span><span class="sxs-lookup"><span data-stu-id="07522-218">Then press and hold the spacebar to bring up the hand and use the mouse to interact with the bounding box:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

<span data-ttu-id="07522-220">若要深入瞭解周框方塊元件和其相關聯的屬性，您可以造訪[MRTK 檔入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的周[框](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)方塊指南。</span><span class="sxs-lookup"><span data-stu-id="07522-220">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-touch-effects"></a><span data-ttu-id="07522-221">新增觸控效果</span><span class="sxs-lookup"><span data-stu-id="07522-221">Adding touch effects</span></span>

<span data-ttu-id="07522-222">在此範例中，您將會啟用當您以手觸碰物件時所要觸發的事件。</span><span class="sxs-lookup"><span data-stu-id="07522-222">In this example, you will enable events to be triggered when you touch an object with your hand.</span></span> <span data-ttu-id="07522-223">具體而言，您會將顆 octa 物件設定為在使用者接觸時播放音效效果。</span><span class="sxs-lookup"><span data-stu-id="07522-223">Specifically, you will configure the Octa object to play a sound effect when the user touches it.</span></span>

<span data-ttu-id="07522-224">達成此目標所需採取的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="07522-224">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="07522-225">將音訊來源元件新增至物件</span><span class="sxs-lookup"><span data-stu-id="07522-225">Add an Audio Source component to the object</span></span>
2. <span data-ttu-id="07522-226">將近乎互動 Touchable （腳本）元件新增至物件</span><span class="sxs-lookup"><span data-stu-id="07522-226">Add the Near Interaction Touchable (Script) component to the object</span></span>
3. <span data-ttu-id="07522-227">將手互動觸控（腳本）元件新增至物件</span><span class="sxs-lookup"><span data-stu-id="07522-227">Add the Hand Interaction Touch (Script) component to the object</span></span>
4. <span data-ttu-id="07522-228">執行觸控開始事件</span><span class="sxs-lookup"><span data-stu-id="07522-228">Implement the On Touch Started event</span></span>
5. <span data-ttu-id="07522-229">使用編輯器內模擬來測試觸控互動</span><span class="sxs-lookup"><span data-stu-id="07522-229">Test the touch interaction using the in-editor simulation</span></span>

> [!IMPORTANT]
> <span data-ttu-id="07522-230">若要能夠**觸發觸控事件**，物件必須具有下列元件：</span><span class="sxs-lookup"><span data-stu-id="07522-230">To be able to **trigger touch events**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="07522-231">**碰撞**元件，最好是 Box 碰撞</span><span class="sxs-lookup"><span data-stu-id="07522-231">**Collider** component, preferably a Box Collider</span></span>
> * <span data-ttu-id="07522-232">**近乎互動 Touchable （腳本）** 元件</span><span class="sxs-lookup"><span data-stu-id="07522-232">**Near Interaction Touchable (Script)** component</span></span>
> * <span data-ttu-id="07522-233">**手動互動觸控（腳本）** 元件</span><span class="sxs-lookup"><span data-stu-id="07522-233">**Hand Interaction Touch (Script)** component</span></span>

> [!NOTE]
> <span data-ttu-id="07522-234">「手互動觸控」（Script）元件不是 MRTK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="07522-234">The Hand Interaction Touch (Script) component is not part of MRTK.</span></span> <span data-ttu-id="07522-235">本教學課程的資產和原始部分的 MixedReality 工具組 Unity 範例已匯入它。</span><span class="sxs-lookup"><span data-stu-id="07522-235">It was imported with this tutorial's assets and originally part of the MixedReality Toolkit Unity Examples.</span></span>

### <a name="1-add-an-audio-source-component-to-the-object"></a><span data-ttu-id="07522-236">1. 將音訊來源元件新增至物件</span><span class="sxs-lookup"><span data-stu-id="07522-236">1. Add an Audio Source component to the object</span></span>

<span data-ttu-id="07522-237">在 [階層] 視窗中，選取 [**顆 octa** ] 物件，將 [**音訊來源**] 元件新增至顆 octa 物件，然後將 [**空間 Blend** ] 變更為1以啟用空間音訊：</span><span class="sxs-lookup"><span data-stu-id="07522-237">In the Hierarchy window, select the **Octa** object, add an **Audio Source** component to the Octa object, and then change **Spatial Blend** to 1 to enable spatial audio:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a><span data-ttu-id="07522-239">2. 將近乎互動 Touchable （腳本）元件新增至物件</span><span class="sxs-lookup"><span data-stu-id="07522-239">2. Add the Near Interaction Touchable (Script) component to the object</span></span>

<span data-ttu-id="07522-240">在仍選取**顆 octa**物件的情況下，將**近乎互動 Touchable （腳本）** 元件新增至顆 octa 物件，然後按一下 [**修正界限**] 和 [**修正中心**] 按鈕，將近端互動 Touchable （腳本）的本機中心和界限屬性更新為符合 BoxCollider：</span><span class="sxs-lookup"><span data-stu-id="07522-240">With the **Octa** object still selected, add the **Near Interaction Touchable (Script)** component to the Octa object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a><span data-ttu-id="07522-242">3. 將手互動觸控（腳本）元件新增至物件</span><span class="sxs-lookup"><span data-stu-id="07522-242">3. Add the Hand Interaction Touch (Script) component to the object</span></span>

<span data-ttu-id="07522-243">在仍選取**顆 octa**物件的情況下，將「**手動互動觸控」（Script）** 元件新增至顆 octa 物件：</span><span class="sxs-lookup"><span data-stu-id="07522-243">With the **Octa** object still selected, add the **Hand Interaction Touch (Script)** component to the Octa object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a><span data-ttu-id="07522-245">4. 執行 Touch 已啟動事件</span><span class="sxs-lookup"><span data-stu-id="07522-245">4. Implement the On Touch Started event</span></span>

<span data-ttu-id="07522-246">在 [**手動互動觸控（腳本）** ] 元件上，按一下 [小型 **+** ] 圖示，以建立新**的 [觸控已啟動（）** ] 事件。</span><span class="sxs-lookup"><span data-stu-id="07522-246">On the **Hand Interaction Touch (Script)** component, click the small **+** icon to create a new **On Touch Started ()** event.</span></span> <span data-ttu-id="07522-247">然後設定**顆 octa**物件以接收事件，並將**spatialize**定義為要觸發的動作：</span><span class="sxs-lookup"><span data-stu-id="07522-247">Then configure the **Octa** object to receive the event and define **AudioSource.PlayOneShot** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

<span data-ttu-id="07522-249">流覽至 **資產**  > **MixedRealityToolkit**  > **StandardAssets** > 材質，以查看 MRTK 所提供的音訊剪輯，然後將適當的音訊剪輯指派給 **音訊剪輯** 欄位，例如 MRTK_Gem 的音訊剪輯：</span><span class="sxs-lookup"><span data-stu-id="07522-249">Navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > Materials to see audio clips provided with the MRTK, and then assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> <span data-ttu-id="07522-251">如需如何執行事件的提醒，您可以參考[手追蹤手勢和可互動按鈕](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)的指示。</span><span class="sxs-lookup"><span data-stu-id="07522-251">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a><span data-ttu-id="07522-252">5. 使用編輯器內模擬來測試觸控互動</span><span class="sxs-lookup"><span data-stu-id="07522-252">5. Test the touch interaction using the in-editor simulation</span></span>

<span data-ttu-id="07522-253">按下 [播放] 按鈕進入遊戲模式。</span><span class="sxs-lookup"><span data-stu-id="07522-253">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="07522-254">然後按住空格鍵以帶出手，並使用滑鼠來碰觸顆 octa 物件，並觸發音效效果：</span><span class="sxs-lookup"><span data-stu-id="07522-254">Then press and hold the spacebar to bring up the hand and use the mouse to touch the Octa object and trigger the sound effect:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> <span data-ttu-id="07522-256">如上圖所示，當您在測試觸控互動時看到顆 octa 物件色彩 pulsated。</span><span class="sxs-lookup"><span data-stu-id="07522-256">As you saw when testing the touch interaction, and as shown in the image above, the Octa object color pulsated while it was touched.</span></span> <span data-ttu-id="07522-257">這項效果已硬式編碼到「手互動觸控」（腳本）元件中，而不是您在上述步驟中完成的事件設定結果。</span><span class="sxs-lookup"><span data-stu-id="07522-257">This effect is hard coded into the Hand Interaction Touch (Script) component and not a result of the event configuration you completed in the steps above.</span></span>
>
> <span data-ttu-id="07522-258">例如，如果您想要停用此效果，您可以將批註 out 或行 32 ' TargetRenderer = GetComponentInChildren<Renderer>（）; '，這會導致 TargetRenderer 剩餘的 null 和色彩不 pulsating。</span><span class="sxs-lookup"><span data-stu-id="07522-258">If you want to disable this effect, you can, for example, comment out or line 32 'TargetRenderer = GetComponentInChildren<Renderer>();' which will result in the TargetRenderer remaining null and the color not pulsating.</span></span>

## <a name="congratulations"></a><span data-ttu-id="07522-259">恭喜</span><span class="sxs-lookup"><span data-stu-id="07522-259">Congratulations</span></span>

<span data-ttu-id="07522-260">在本教學課程中，您已瞭解如何在方格集合中組織3D 物件，以及如何使用近距離互動（直接抓取和旋轉）和即時互動（使用注視光線或手片）來操作這些物件（縮放、旋轉和移動）。</span><span class="sxs-lookup"><span data-stu-id="07522-260">In this tutorial, you learned how to organize 3D objects in a grid collection and how to manipulate these objects (scaling, rotating, and moving) using near interaction (directly grabbing with tracked hands) and far interaction (using gaze rays or hand rays).</span></span> <span data-ttu-id="07522-261">您也學到如何將周框方塊放在3D 物件周圍，學習如何使用和自訂周框方塊上的控點。</span><span class="sxs-lookup"><span data-stu-id="07522-261">You also learned how to put bounding boxes around 3D objects, and learned how to use and customize the handles on the bounding boxes.</span></span> <span data-ttu-id="07522-262">最後，您學習到觸控物件時如何觸發事件。</span><span class="sxs-lookup"><span data-stu-id="07522-262">Finally, you learned how to trigger events when touching an object.</span></span>

[<span data-ttu-id="07522-263">下一課： 6. 探索 advanced 輸入選項</span><span class="sxs-lookup"><span data-stu-id="07522-263">Next Lesson: 6. Exploring advanced input options</span></span>](mrlearning-base-ch5.md)
