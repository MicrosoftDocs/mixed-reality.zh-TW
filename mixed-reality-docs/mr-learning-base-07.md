---
title: 入門教學課程 - 7。 與 3D 物件互動
description: 本課程說明如何使用混合實境工具組 (MRTK) 來建立混合實境應用程式。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: f02780a1b9421b814242727ce92311d62b5e3461
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376420"
---
# <a name="7-interacting-with-3d-objects"></a><span data-ttu-id="c4739-105">7.與 3D 物件互動</span><span class="sxs-lookup"><span data-stu-id="c4739-105">7. Interacting with 3D objects</span></span>

<span data-ttu-id="c4739-106">在本教學課程中，您將了解如何對 3D 物件進行遠近操作，並限制允許的操作類型。</span><span class="sxs-lookup"><span data-stu-id="c4739-106">In this tutorial, you will learn how to enable near and far manipulation of 3D objects and limit the allowed types of manipulation.</span></span> <span data-ttu-id="c4739-107">您也將了解如何在3D 物件周圍加入週框方塊，讓您更輕鬆地控制物件操作。</span><span class="sxs-lookup"><span data-stu-id="c4739-107">You will also learn how to add bounding boxes around 3D objects to make it easier to control the object manipulation.</span></span>

## <a name="objectives"></a><span data-ttu-id="c4739-108">目標</span><span class="sxs-lookup"><span data-stu-id="c4739-108">Objectives</span></span>

* <span data-ttu-id="c4739-109">了解如何設定3D 物件，使其能夠進行互動</span><span class="sxs-lookup"><span data-stu-id="c4739-109">Learn how to configure 3D objects so they can be interacted with</span></span>
* <span data-ttu-id="c4739-110">了解如何將週框方塊加入 3D 物件</span><span class="sxs-lookup"><span data-stu-id="c4739-110">Learn how to add bounding boxes to 3D objects</span></span>

## <a name="manipulating-3d-objects"></a><span data-ttu-id="c4739-111">操作 3D 物件</span><span class="sxs-lookup"><span data-stu-id="c4739-111">Manipulating 3D objects</span></span>

<span data-ttu-id="c4739-112">在本節中，您將加入可操作所有 Rover 零件的能力，也就是您在[將物件置放在場景中](mr-learning-base-04.md)的教學課程中，於桌面上組織的所有 Rover 零件。</span><span class="sxs-lookup"><span data-stu-id="c4739-112">In this section, you will add the ability to manipulate all the Rover parts you organized on the table during the [Positioning objects in the scene](mr-learning-base-04.md) tutorial.</span></span>

<span data-ttu-id="c4739-113">達成此動作所需採取的主要步驟如下：</span><span class="sxs-lookup"><span data-stu-id="c4739-113">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="c4739-114">將 Object Manipulator (指令碼) 元件新增至所有零件物件</span><span class="sxs-lookup"><span data-stu-id="c4739-114">Add the Object Manipulator (Script) component to all the part objects</span></span>
2. <span data-ttu-id="c4739-115">將 NearInteractionGrabbable 元件新增至所有零件物件</span><span class="sxs-lookup"><span data-stu-id="c4739-115">Add the NearInteractionGrabbable component to all the part objects</span></span>
3. <span data-ttu-id="c4739-116">設定 Object Manipulator (指令碼) 元件</span><span class="sxs-lookup"><span data-stu-id="c4739-116">Configure the Object Manipulator (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="c4739-117">若要能夠**操作物件**，該物件必須具有下列元件：</span><span class="sxs-lookup"><span data-stu-id="c4739-117">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="c4739-118">**Collider** 元件，例如 Box Collider</span><span class="sxs-lookup"><span data-stu-id="c4739-118">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="c4739-119">**Object Manipulator (指令碼)** 元件</span><span class="sxs-lookup"><span data-stu-id="c4739-119">**Object Manipulator (Script)** component</span></span>
>
> <span data-ttu-id="c4739-120">若要能夠以追蹤的手部**操作**及**抓取物件**，該物件必須具有下列元件：</span><span class="sxs-lookup"><span data-stu-id="c4739-120">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="c4739-121">**Collider** 元件，例如 Box Collider</span><span class="sxs-lookup"><span data-stu-id="c4739-121">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="c4739-122">**Object Manipulator (指令碼)** 元件</span><span class="sxs-lookup"><span data-stu-id="c4739-122">**Object Manipulator (Script)** component</span></span>
> * <span data-ttu-id="c4739-123">**NearInteractionGrabbable** 元件</span><span class="sxs-lookup"><span data-stu-id="c4739-123">**NearInteractionGrabbable** component</span></span>

<span data-ttu-id="c4739-124">此外，您將設定 Rover Explorer，讓您可以將 Rover 零件放在 Rover 上，使其成為完整的 Rover 組件。</span><span class="sxs-lookup"><span data-stu-id="c4739-124">Additionally, you will configure the Rover Explorer so that you can place the rover parts on to the Rover to make it a complete rover assembly.</span></span>

<span data-ttu-id="c4739-125">在 [階層] 視窗中，展開 RoverExplorer > **RoverParts** 物件，並選取其所有子 Rover 零件物件和 **RoverAssembly** 物件，然後在 [偵測器] 視窗中，使用 [新增元件] 按鈕將下列元件新增至所有選取的物件：</span><span class="sxs-lookup"><span data-stu-id="c4739-125">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects and the **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="c4739-126">**Object Manipulator (指令碼)** 元件</span><span class="sxs-lookup"><span data-stu-id="c4739-126">**Object Manipulator (Script)** component</span></span>
* <span data-ttu-id="c4739-127">**NearInteractionGrabbable** 元件</span><span class="sxs-lookup"><span data-stu-id="c4739-127">**NearInteractionGrabbable** component</span></span>
* <span data-ttu-id="c4739-128">**Part Assembly Controller (指令碼)** 元件</span><span class="sxs-lookup"><span data-stu-id="c4739-128">**Part Assembly Controller (Script)** component</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="c4739-130">若要選取非連續的多個物件，請按住 CTRL 鍵並使用滑鼠選取任何物件。</span><span class="sxs-lookup"><span data-stu-id="c4739-130">To select multiple objects that are not next to each other, press-and-hold the CTRL key while using the mouse to select any object.</span></span>

> [!NOTE]
> <span data-ttu-id="c4739-131">基於本教學課程的目的，碰撞器 (Collider) 已新增至 Rover 零件。</span><span class="sxs-lookup"><span data-stu-id="c4739-131">For the purpose of this tutorial, colliders have already been added to the rover parts.</span></span> <span data-ttu-id="c4739-132">若要深入了解碰撞器，您可以造訪 Unity 的<a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">碰撞器 (Collider)</a> 文件。</span><span class="sxs-lookup"><span data-stu-id="c4739-132">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="c4739-133">Part Assembly Controller (指令碼) 不是 MRTK 的一部分，但已包含在教學課程資產中。</span><span class="sxs-lookup"><span data-stu-id="c4739-133">The Part Assembly Controller (Script) is not part of the MRTK but was included with the tutorial assets.</span></span>

<span data-ttu-id="c4739-134">在仍選取所有 Rover 零件物件和 RoverAssembly 物件的情況下，在 [偵測器] 視窗中，設定 **Object Manipulator (指令碼)** 元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c4739-134">With all the rover part objects and the RoverAssembly object still selected, in the Inspector window, configure the **Object Manipulator (Script)** component as follows:</span></span>

* <span data-ttu-id="c4739-135">從 [兩手操作類型] 下拉式清單中，取消核取 [縮放]，只啟用 [移動] 和 [選轉]</span><span class="sxs-lookup"><span data-stu-id="c4739-135">From the **Two Handed Manipulation Type** dropdown, uncheck the Scale, so only **Move** and **Rotate** is enabled</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> <span data-ttu-id="c4739-137">此時，您已針對所有 Rover 零件物件和 RoverAssembly 物件啟用物件操作。</span><span class="sxs-lookup"><span data-stu-id="c4739-137">At this point, you have enabled object manipulation for all the rover part objects and the RoverAssembly object.</span></span>

<span data-ttu-id="c4739-138">在 [專案] 視窗中，瀏覽至 [資產] > [MRTK] > [SDK] > [StandardAssets] > [Audio] 資料夾，以找出音訊剪輯：</span><span class="sxs-lookup"><span data-stu-id="c4739-138">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Audio** folder to locate the audio clips:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-3.png)

<span data-ttu-id="c4739-140">在 [階層] 視窗中，重新選取所有 **Rover 零件物件**，然後在 [偵測器] 視窗中，使用 [新增元件] 按鈕來新增**音訊來源**元件，並進行以下設定：</span><span class="sxs-lookup"><span data-stu-id="c4739-140">In the Hierarchy window, reselect all the **rover part objects**, then in the Inspector window, use the **Add Component** button to add the **Audio Sources** component and configure it as follows:</span></span>

* <span data-ttu-id="c4739-141">將 **MRTK_Scale_Start** 音訊剪輯指派給 **AudioClip** 欄位</span><span class="sxs-lookup"><span data-stu-id="c4739-141">Assign the **MRTK_Scale_Start** audio clip to the **AudioClip** field</span></span>
* <span data-ttu-id="c4739-142">取消核取 [喚醒時播放] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="c4739-142">Uncheck the **Play On Awake** checkbox</span></span>
* <span data-ttu-id="c4739-143">將 [空間混合] 變更為 1</span><span class="sxs-lookup"><span data-stu-id="c4739-143">Change **Spatial Blend** to 1</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-4.png)

<span data-ttu-id="c4739-145">在 [階層] 視窗中，展開 RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** 物件，以顯示所有位置提示物件，選取第一個 Rover 零件 RoverParts > **Camera_Part**，然後設定 **Part Assembly Controller (指令碼)** 元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c4739-145">In the Hierarchy window, expand the RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** object to reveal all of the placement hint objects, then select the first rover part, RoverParts > **Camera_Part**, and configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="c4739-146">將 **Camera_PlacementHint** 物件指派給 [要放置的位置] 欄位</span><span class="sxs-lookup"><span data-stu-id="c4739-146">Assign the **Camera_PlacementHint** object to the **Location To Place** field</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-5.png)

<span data-ttu-id="c4739-148">針對其餘每個 Rover 零件物件和 RoverAssembly 物件**重複**此步驟，以設定 **Part Assembly Controller (指令碼)** 元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c4739-148">**Repeat** this step for each of the remaining rover part objects and the RoverAssembly object to configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="c4739-149">針對 **Generator_Part**，將 **Generator_PlacementHint** 物件指派給 [要放置的位置] 欄位</span><span class="sxs-lookup"><span data-stu-id="c4739-149">For the **Generator_Part**, assign the **Generator_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="c4739-150">針對 **Lights_Part**，將 **Lights_PlacementHint** 物件指派給 [要放置的位置] 欄位</span><span class="sxs-lookup"><span data-stu-id="c4739-150">For the **Lights_Part**, assign the **Lights_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="c4739-151">針對 **UHFAntenna_Part**，將 **UHFAntenna_PlacementHint** 物件指派給 [要放置的位置] 欄位</span><span class="sxs-lookup"><span data-stu-id="c4739-151">For the **UHFAntenna_Part**, assign the **UHFAntenna_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="c4739-152">針對 **Spectrometer_Part**，將 **Spectrometer_PlacementHint** 物件指派給 [要放置的位置] 欄位</span><span class="sxs-lookup"><span data-stu-id="c4739-152">For the **Spectrometer_Part**, assign the **Spectrometer_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="c4739-153">針對 **RoverAssembly**，將物件本身 (也就是相同的 **RoverAssembly** 物件) 指派給 [要放置的位置] 欄位</span><span class="sxs-lookup"><span data-stu-id="c4739-153">For the **RoverAssembly**, assign the object itself, i.e. the same **RoverAssembly** object, to the **Location To Place** field</span></span>

<span data-ttu-id="c4739-154">在 [階層] 視窗中，選取 [RoverExplorer] > [按鈕] > [重設] 按鈕物件，然後在 [偵測器] 視窗中，設定可互動的 **OnClick ()** 事件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c4739-154">In the Hierarchy window, select the RoverExplorer > Buttons > **Reset** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="c4739-155">將 **RoverAssembly** 物件指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="c4739-155">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="c4739-156">從 [沒有函式] 下拉式清單中，選取 [PartAssemblyController] > [ResetPlacement ()]，以將此函式設定為觸發事件時所要執行的動作</span><span class="sxs-lookup"><span data-stu-id="c4739-156">From the **No Function** dropdown, select **PartAssemblyController** > **ResetPlacement ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-6.png)

<span data-ttu-id="c4739-158">如果您現在進入遊戲模式，您可以使用近或遠的互動來將 Rover 零件放在 Rover 上。</span><span class="sxs-lookup"><span data-stu-id="c4739-158">If you now enter Game mode, you can use near or far interaction to place the rover parts on to the Rover.</span></span> <span data-ttu-id="c4739-159">零件會在接近對應的放置提示時，貼齊位置並成為 Rover 的一部分。</span><span class="sxs-lookup"><span data-stu-id="c4739-159">Once the part is close to the corresponding placement hint, it will snap into place and become part of the Rover.</span></span> <span data-ttu-id="c4739-160">若要重設放置位置，您可以按下 [重設] 按鈕：</span><span class="sxs-lookup"><span data-stu-id="c4739-160">To reset the placements, you can press the Reset button:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-7.png)

<span data-ttu-id="c4739-162">若要深入了解 Object Manipulator (物件操作工具) 元件及其相關聯的屬性，您可以瀏覽 [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的 [Object Manipulator (物件操作工具)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) 指南。</span><span class="sxs-lookup"><span data-stu-id="c4739-162">To learn more about the Object Manipulator component and its associated properties, you can visit the [Object Manipulator](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="c4739-163">新增週框方塊</span><span class="sxs-lookup"><span data-stu-id="c4739-163">Adding bounding boxes</span></span>

<span data-ttu-id="c4739-164">周框方塊藉由提供可用於縮放和旋轉的控點，讓您能夠更輕鬆且更直覺地以單手操作可遠近互動的物件。</span><span class="sxs-lookup"><span data-stu-id="c4739-164">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="c4739-165">在此範例中，您會將週框方塊新增至 RoverExplorer 物件，以便您在整個體驗中可以輕鬆地移動、旋轉和縮放。</span><span class="sxs-lookup"><span data-stu-id="c4739-165">In this example, you will add a bounding box to the RoverExplorer object so the whole experience can easily be moved, rotated, and scaled.</span></span> <span data-ttu-id="c4739-166">此外，您將設定「功能表」，讓您可以開啟和關閉週框方塊。</span><span class="sxs-lookup"><span data-stu-id="c4739-166">Additionally, you will configure the Menu so you can turn the Bounding Box on and off.</span></span>

<span data-ttu-id="c4739-167">在 [階層] 視窗中，選取 **RoverExplorer** 物件，然後在 [偵測器] 視窗中，使用 [新增元件] 按鈕來新增下列元件：</span><span class="sxs-lookup"><span data-stu-id="c4739-167">In the Hierarchy window, select the **RoverExplorer** object, then in the Inspector window, use the **Add Component** button to add the following components:</span></span>

* <span data-ttu-id="c4739-168">**BoundingBox** 元件</span><span class="sxs-lookup"><span data-stu-id="c4739-168">**BoundingBox** component</span></span>
* <span data-ttu-id="c4739-169">**Object Manipulator (指令碼)** 元件</span><span class="sxs-lookup"><span data-stu-id="c4739-169">**Object Manipulator (Script)** component</span></span>

<span data-ttu-id="c4739-170">然後**取消核取**這兩個元件旁的核取方塊，使其預設為**停用**：</span><span class="sxs-lookup"><span data-stu-id="c4739-170">Then **uncheck** the checkbox next to both components to make them **disabled** by default:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="c4739-172">週框方塊視覺效果會在執行階段中建立，因此在您進入遊戲模式之前看不到該效果。</span><span class="sxs-lookup"><span data-stu-id="c4739-172">The Bounding Box visualization is created at runtime and, therefore, not visible before you enter Game mode.</span></span>

> [!NOTE]
> <span data-ttu-id="c4739-173">BoundingBox 元件將會在執行階段尚自動新增 NearInteractionGrabbable 元件。</span><span class="sxs-lookup"><span data-stu-id="c4739-173">The BoundingBox component will automatically add the NearInteractionGrabbable component at runtime.</span></span> <span data-ttu-id="c4739-174">因此，我們不需要新增此元件，就能以追蹤的手部抓取框起來的物件。</span><span class="sxs-lookup"><span data-stu-id="c4739-174">Therefore, we do not need to add this component to grab the enclosed objects with tracked hands.</span></span>

<span data-ttu-id="c4739-175">在 [階層] 視窗中，展開功能表 > **ButtonCollection** 物件以顯示四個按鈕，並將第三個按鈕重新命名為 **BoundingBox_Enable**，然後在 [偵測器] 視窗中，設定 **Button Config Helper (指令碼)** 元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c4739-175">In the Hierarchy window, expand the Menu > **ButtonCollection** object to reveal the four buttons and rename the third button to **BoundingBox_Enable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="c4739-176">將 [主要標籤文字] 變更為 [啟用]</span><span class="sxs-lookup"><span data-stu-id="c4739-176">Change the **Main Label Text** to **Enable**</span></span>
* <span data-ttu-id="c4739-177">將 **RoverExplorer** 物件指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="c4739-177">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="c4739-178">從 [沒有函式] 下拉式清單中，選取 [BoundingBox] >  [bool Enabled] 以在觸發事件時更新此屬性值</span><span class="sxs-lookup"><span data-stu-id="c4739-178">From the **No Function** dropdown, select **BoundingBox** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="c4739-179">確認**已核取**引數核取方塊</span><span class="sxs-lookup"><span data-stu-id="c4739-179">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="c4739-180">按一下小型 **+** 圖示，以新增另一個事件</span><span class="sxs-lookup"><span data-stu-id="c4739-180">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="c4739-181">將 **RoverExplorer** 物件指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="c4739-181">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="c4739-182">從 [沒有函式] 下拉式清單中，選取 [ObjectManipulator] > [bool Enabled] 以在觸發事件時更新此屬性值</span><span class="sxs-lookup"><span data-stu-id="c4739-182">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="c4739-183">確認**已核取**引數核取方塊</span><span class="sxs-lookup"><span data-stu-id="c4739-183">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="c4739-184">將**圖示**保留為 [具有週框的立方體] 圖示</span><span class="sxs-lookup"><span data-stu-id="c4739-184">Leave the **Icon** as the 'cube with bounding box' icon</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-2.png)

<span data-ttu-id="c4739-186">將第四個 (也就是最後一個) 按鈕重新命名為 **BoundingBox_Disable**，然後在 [偵測器] 視窗中，設定 **Button Config Helper (Script)** 元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c4739-186">Rename the forth and last button to **BoundingBox_Disable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="c4739-187">將 [主要標籤文字] 變更為 [停用]</span><span class="sxs-lookup"><span data-stu-id="c4739-187">Change the **Main Label Text** to **Disable**</span></span>
* <span data-ttu-id="c4739-188">將 **RoverExplorer** 物件指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="c4739-188">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="c4739-189">從 [沒有函式] 下拉式清單中，選取 [BoundingBox] >  [bool Enabled] 以在觸發事件時更新此屬性值</span><span class="sxs-lookup"><span data-stu-id="c4739-189">From the **No Function** dropdown, select **BoundingBox** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="c4739-190">確認**未核取**引數核取方塊</span><span class="sxs-lookup"><span data-stu-id="c4739-190">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="c4739-191">按一下小型 **+** 圖示，以新增另一個事件</span><span class="sxs-lookup"><span data-stu-id="c4739-191">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="c4739-192">將 **RoverExplorer** 物件指派給 [無 (物件)] 欄位</span><span class="sxs-lookup"><span data-stu-id="c4739-192">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="c4739-193">從 [沒有函式] 下拉式清單中，選取 [ObjectManipulator] > [bool Enabled] 以在觸發事件時更新此屬性值</span><span class="sxs-lookup"><span data-stu-id="c4739-193">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="c4739-194">確認**未核取**引數核取方塊</span><span class="sxs-lookup"><span data-stu-id="c4739-194">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="c4739-195">將**圖示**變更為 [具有週框的立方體] 圖示</span><span class="sxs-lookup"><span data-stu-id="c4739-195">Change the **Icon** to the 'cube with bounding box" icon</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-3.png)

<span data-ttu-id="c4739-197">如果您現在進入遊戲模式，並按一下 [啟用] 按鈕來啟用週框方塊，您就可以使用近或遠的互動來移動、旋轉和縮放週框方塊，然後使用 [停用] 按鈕再次停用週框方塊：</span><span class="sxs-lookup"><span data-stu-id="c4739-197">If you now enter Game mode and enable the Bounding Box by clicking the Enable button, you can use near or far interaction to move, rotate, and scale the Bounding Box, and use the Disable button to disable the Bounding Box again:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-4.png)

<span data-ttu-id="c4739-199">若要深入了解 Bounding Box 元件和其相關聯的屬性，您可以瀏覽 [MRTK 文件入口網站](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[周框方塊](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)指南。</span><span class="sxs-lookup"><span data-stu-id="c4739-199">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="congratulations"></a><span data-ttu-id="c4739-200">恭喜！</span><span class="sxs-lookup"><span data-stu-id="c4739-200">Congratulations</span></span>

<span data-ttu-id="c4739-201">在本教學課程中，您已了解如何啟用 3D 物件的遠近操作，以及如何限制允許的操作類型。</span><span class="sxs-lookup"><span data-stu-id="c4739-201">In this tutorial, you learned how to enable near and far manipulation for 3D objects and how to limit the allowed types of manipulation.</span></span> <span data-ttu-id="c4739-202">您也了解如何在 3D 物件周圍加入週框方塊，讓您更輕鬆地控制物件操作。</span><span class="sxs-lookup"><span data-stu-id="c4739-202">You also learned how to add bounding boxes around 3D objects to make it easier to control the object manipulation.</span></span>

[<span data-ttu-id="c4739-203">下一個教學課程：8.使用眼球追蹤</span><span class="sxs-lookup"><span data-stu-id="c4739-203">Next Tutorial: 8. Using eye-tracking</span></span>](mr-learning-base-08.md)
