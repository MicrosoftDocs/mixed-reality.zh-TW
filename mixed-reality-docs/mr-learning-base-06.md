---
title: 入門教學課程 - 6。 建立使用者介面
description: 本課程說明如何使用混合實境工具組 (MRTK) 來建立混合實境應用程式。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: a7c4ea140a9c27f1a92680da6bbe1fb3a4bdc233
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304615"
---
# <a name="6-creating-user-interfaces"></a><span data-ttu-id="dc7b5-105">6.建立使用者介面</span><span class="sxs-lookup"><span data-stu-id="dc7b5-105">6. Creating user interfaces</span></span>

## <a name="overview"></a><span data-ttu-id="dc7b5-106">概觀</span><span class="sxs-lookup"><span data-stu-id="dc7b5-106">Overview</span></span>

<span data-ttu-id="dc7b5-107">在本教學課程中，您將了解如何使用 MRTK 的按鈕和功能表預製物件以及 Unity 的 TextMeshPro 元件來建立簡單的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="dc7b5-107">In this tutorial, you will learn how to create a simple user interface using MRTK's button and menu prefabs alongside Unity's TextMeshPro component.</span></span> <span data-ttu-id="dc7b5-108">您也將了解如何設定按鈕來觸發事件，並新增動態工具提示 UI 元素，以提供使用者其他資訊。</span><span class="sxs-lookup"><span data-stu-id="dc7b5-108">You will also learn how to configure the buttons to trigger events and add dynamic tooltip UI elements to provide the user with additional information.</span></span>

## <a name="objectives"></a><span data-ttu-id="dc7b5-109">目標</span><span class="sxs-lookup"><span data-stu-id="dc7b5-109">Objectives</span></span>

* <span data-ttu-id="dc7b5-110">了解如何組織集合中的按鈕</span><span class="sxs-lookup"><span data-stu-id="dc7b5-110">Learn how to organize buttons in a collection</span></span>
* <span data-ttu-id="dc7b5-111">了解如何使用 MRTK 的功能表預製物件</span><span class="sxs-lookup"><span data-stu-id="dc7b5-111">Learn how to use MRTK's menu prefabs</span></span>
* <span data-ttu-id="dc7b5-112">了解如何使用 UI 功能表和按鈕來與全像投影互動</span><span class="sxs-lookup"><span data-stu-id="dc7b5-112">Learn how to interact with holograms using UI menus and buttons</span></span>
* <span data-ttu-id="dc7b5-113">瞭解如何新增文字元素</span><span class="sxs-lookup"><span data-stu-id="dc7b5-113">Learn how to add text elements</span></span>
* <span data-ttu-id="dc7b5-114">了解如何動態產生物件的工具提示</span><span class="sxs-lookup"><span data-stu-id="dc7b5-114">Learn how to spawn tooltips on objects dynamically</span></span>

## <a name="creating-a-static-panel-of-buttons"></a><span data-ttu-id="dc7b5-115">建立按鈕的靜態面板</span><span class="sxs-lookup"><span data-stu-id="dc7b5-115">Creating a static panel of buttons</span></span>

<span data-ttu-id="dc7b5-116">在階層視窗中，以滑鼠右鍵按一下 **RoverExplorer** 物件並選取 [建立空物件]，將空白物件新增為 RoverExplorer 的子系，然後將物件命名為 **Buttons**，並設定**變形**元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dc7b5-116">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **Buttons**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="dc7b5-117">**位置**：X = -0.6、Y = 0.036、Z = -0.5</span><span class="sxs-lookup"><span data-stu-id="dc7b5-117">**Position**: X = -0.6, Y = 0.036, Z = -0.5</span></span>
* <span data-ttu-id="dc7b5-118">**旋轉**：X = 90、Y = 0、Z = 0</span><span class="sxs-lookup"><span data-stu-id="dc7b5-118">**Rotation**: X = 90, Y = 0, Z = 0</span></span>
* <span data-ttu-id="dc7b5-119">**縮放比例**：X = 1、Y = 1、Z = 1</span><span class="sxs-lookup"><span data-stu-id="dc7b5-119">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-1.png)

<span data-ttu-id="dc7b5-121">在 [專案] 視窗中，瀏覽至**資產** > **MRTK.Tutorials.GettingStarted** > **預製物件**資料夾，按一下並將 **PressableRoundButton** 預製物件拖曳到 **Buttons** 物件，然後以滑鼠右鍵按一下 PressableRoundButton 並選取 [複製] 建立複本，重覆上述步驟直到完成三個 PressableRoundButton 物件為止：</span><span class="sxs-lookup"><span data-stu-id="dc7b5-121">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder, click-and-drag the **PressableRoundButton** prefab on to the **Buttons** object, then right-click on the PressableRoundButton and select **Duplicate** to create a copy, repeat until you have a total of three PressableRoundButton objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-2.png)

<span data-ttu-id="dc7b5-123">在階層視窗中選取 **Buttons** 物件，然後在偵測器視窗中使用 [新增元件] 按鈕來新增 **GridObjectCollection** 元件，並進行以下設定：</span><span class="sxs-lookup"><span data-stu-id="dc7b5-123">In the Hierarchy window, select the **Buttons** object, then in the Inspector window, use the **Add Component** button to add the **GridObjectCollection** component and configure it as follows:</span></span>

* <span data-ttu-id="dc7b5-124">**排序類型**：子順序</span><span class="sxs-lookup"><span data-stu-id="dc7b5-124">**Sort Type**: Child Order</span></span>
* <span data-ttu-id="dc7b5-125">**版面配置**：水平</span><span class="sxs-lookup"><span data-stu-id="dc7b5-125">**Layout**: Horizontal</span></span>
* <span data-ttu-id="dc7b5-126">**儲存格寬度**：0.2</span><span class="sxs-lookup"><span data-stu-id="dc7b5-126">**Cell Width**: 0.2</span></span>
* <span data-ttu-id="dc7b5-127">**錨點**：中間靠左對齊</span><span class="sxs-lookup"><span data-stu-id="dc7b5-127">**Anchor**: Middle Left</span></span>

<span data-ttu-id="dc7b5-128">然後按一下 [更新集合] 按鈕，以更新 Buttons 物件的子物件位置：</span><span class="sxs-lookup"><span data-stu-id="dc7b5-128">Then click the **Update Collection** button to update the position of the Buttons object's child objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-3.png)

<span data-ttu-id="dc7b5-130">在階層視窗中，將按鈕命名為**提示**、**分解**和**重設**。</span><span class="sxs-lookup"><span data-stu-id="dc7b5-130">In the Hierarchy window, name the buttons **Hints**, **Explode**, and **Reset**.</span></span>

<span data-ttu-id="dc7b5-131">為每個按鈕選取 **SeeItSayItLabel** > **TextMeshPro** 子物件，然後在 偵測器視窗中分別變更 **TextMeshPro - 文字**元件文字以符合按鈕名稱：</span><span class="sxs-lookup"><span data-stu-id="dc7b5-131">For each button, select the **SeeItSayItLabel** > **TextMeshPro** child object, then in the Inspector window, change the respective **TextMeshPro - Text** component text to match the button names:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-4.png)

<span data-ttu-id="dc7b5-133">完成後，摺疊 Buttons 物件的子物件。</span><span class="sxs-lookup"><span data-stu-id="dc7b5-133">Once done, collapse the Buttons object's child objects.</span></span>

<span data-ttu-id="dc7b5-134">在階層視窗中，選取 [提示] 按鈕物件，然後在偵測器視窗中，設定可互動的 **OnClick ()** 事件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dc7b5-134">In the Hierarchy window, select the **Hints** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="dc7b5-135">將 **RoverAssembly** 物件指派給**無 (物件)** 欄位</span><span class="sxs-lookup"><span data-stu-id="dc7b5-135">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="dc7b5-136">從**沒有函式**下拉式清單中，選取 **PartAssemblyController** > **TogglePlacementHints ()** ，以將此函式設定為觸發事件時所要執行的動作</span><span class="sxs-lookup"><span data-stu-id="dc7b5-136">From the **No Function** dropdown, select **PlacementHintsController** > **TogglePlacementHints ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-5.png)

<span data-ttu-id="dc7b5-138">在階層視窗中，選取 [分解] 按鈕物件，然後在偵測器視窗中，設定可互動的 **OnClick ()** 事件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dc7b5-138">In the Hierarchy window, select the **Explode** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="dc7b5-139">將 **RoverAssembly** 物件指派給**無 (物件)** 欄位</span><span class="sxs-lookup"><span data-stu-id="dc7b5-139">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="dc7b5-140">從**沒有函式**下拉式清單中，選取 **ExplodedViewController** > **ToggleExplodedView ()** ，以將此函式設定為觸發事件時所要執行的動作</span><span class="sxs-lookup"><span data-stu-id="dc7b5-140">From the **No Function** dropdown, select **ExplodedViewController** > **ToggleExplodedView ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-6.png)

<span data-ttu-id="dc7b5-142">按下開始遊戲按鈕進入遊戲模式，然後按住空格鍵按鈕來啟動手勢功能，並用滑鼠按下 [提示] 按鈕來切換放置提示物件的可見度：</span><span class="sxs-lookup"><span data-stu-id="dc7b5-142">Press the Play button to enter Game mode, then press-and-hold the space bar button to activate the hand and use the mouse to press the **Hints** button to toggle the visibility of the placement hint objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-7.png)

<span data-ttu-id="dc7b5-144">而**分解**按鈕可開啟和關閉分解檢視功能：</span><span class="sxs-lookup"><span data-stu-id="dc7b5-144">and the **Explode** button to toggle the exploded view on and off:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-8.png)

## <a name="creating-a-dynamic-menu-that-follows-the-user"></a><span data-ttu-id="dc7b5-146">建立會跟隨使用者的動態功能表</span><span class="sxs-lookup"><span data-stu-id="dc7b5-146">Creating a dynamic menu that follows the user</span></span>

<span data-ttu-id="dc7b5-147">在專案視窗中，瀏覽至**資產** > **MRTK** > **SDK** > **UX** > **預製物件** > **功能表**資料夾，按一下並將 **NearMenu4x1** 預製物件拖曳至階層視窗，將其轉換 **位置** 設為 X = 0、Y =-0.4、Z = 0，並依照下列方式進行設定：</span><span class="sxs-lookup"><span data-stu-id="dc7b5-147">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **UX** > **Prefabs** > **Menus** folder, click-and-drag the **NearMenu4x1** prefab into the Hierarchy window, set its Transform **Position** to X = 0, Y = -0.4, Z = 0 and configure it as follows:</span></span>

* <span data-ttu-id="dc7b5-148">確認 **SolverHandler** 元件的 [追蹤目標類型] 設定為**頭部**</span><span class="sxs-lookup"><span data-stu-id="dc7b5-148">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="dc7b5-149">核取 **RadialView** 規劃元件旁的核取方塊，使其預設為啟用</span><span class="sxs-lookup"><span data-stu-id="dc7b5-149">Check the checkbox next to the **RadialView** Solver component so it is enabled by default</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-1.png)

<span data-ttu-id="dc7b5-151">在階層視窗中，將物件重新命名為**功能表**，然後展開其 **ButtonCollection** 子物件，以顯示四個按鈕：</span><span class="sxs-lookup"><span data-stu-id="dc7b5-151">In the Hierarchy window, rename the object to **Menu**, then expand its **ButtonCollection** child object to reveal the four buttons:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-2.png)

<span data-ttu-id="dc7b5-153">將第一個按鈕重新命名為 **Indicator**，然後在 [偵測器] 視窗中，設定 **Button Config Helper (Script)** 元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dc7b5-153">Rename the first button to **Indicator**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="dc7b5-154">將**主要標籤文字**變更為符合按鈕的名稱</span><span class="sxs-lookup"><span data-stu-id="dc7b5-154">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="dc7b5-155">將 **Indicator** 物件指派給**無 (物件)** 欄位</span><span class="sxs-lookup"><span data-stu-id="dc7b5-155">Assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="dc7b5-156">從**沒有函式**下拉式清單中，選取 GameObject > SetActive (bool)，以將此函式設定為觸發事件時所要執行的動作</span><span class="sxs-lookup"><span data-stu-id="dc7b5-156">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="dc7b5-157">確認**已核取**引數核取方塊</span><span class="sxs-lookup"><span data-stu-id="dc7b5-157">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="dc7b5-158">將**圖示** 變更為「搜尋」圖示</span><span class="sxs-lookup"><span data-stu-id="dc7b5-158">Change the **Icon** to the 'search' icon</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-3.png)

<span data-ttu-id="dc7b5-160">在階層視窗中，選取 **Indicator** 物件，然後在偵測器視窗中，取消核取其名稱旁的核取方塊，使其預設為非作用中：</span><span class="sxs-lookup"><span data-stu-id="dc7b5-160">In the Hierarchy window, select the **Indicator** object, then in the Inspector window, uncheck the checkbox next to its name to make it inactive by default:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="dc7b5-162">現在，當應用程式啟動時，預設會停用指標，而且只要按下 [指標] 按鈕就能啟用。</span><span class="sxs-lookup"><span data-stu-id="dc7b5-162">Now, when the app starts, the Indicator is disabled by default and can be enabled by pressing the Indicator button.</span></span>

<span data-ttu-id="dc7b5-163">將第二個按鈕重新命名為**TapToPlace**，然後在 [偵測器] 視窗中，設定 **Button Config Helper (指令碼)** 元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dc7b5-163">Rename the second button to **TapToPlace**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="dc7b5-164">將**主要標籤文字**變更為符合按鈕的名稱</span><span class="sxs-lookup"><span data-stu-id="dc7b5-164">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="dc7b5-165">將 RoverExplorer > **RoverAssembly** 物件指派給**無 (物件)** 欄位</span><span class="sxs-lookup"><span data-stu-id="dc7b5-165">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="dc7b5-166">從 [沒有函式] 下拉式清單中，選取 **TapToPlace** > **bool enabled**，以在觸發事件時更新此屬性值</span><span class="sxs-lookup"><span data-stu-id="dc7b5-166">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="dc7b5-167">確認**已核取**引數核取方塊</span><span class="sxs-lookup"><span data-stu-id="dc7b5-167">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="dc7b5-168">將**圖示**變更為「手部發光」圖示</span><span class="sxs-lookup"><span data-stu-id="dc7b5-168">Change the **Icon** to the 'hand with ray' icon</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-5.png)

<span data-ttu-id="dc7b5-170">在階層視窗中，選取 **RoverAssembly** 物件，然後在偵測器視窗中設定**點選放置 (指令碼)** 元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dc7b5-170">In the Hierarchy window, select the **RoverAssembly** object, then in the Inspector window, configure the **Tap To Place (Script)** component as follows:</span></span>

* <span data-ttu-id="dc7b5-171">取消核取其名稱旁的核取方塊，使其預設為非作用中</span><span class="sxs-lookup"><span data-stu-id="dc7b5-171">Uncheck the checkbox next to its name to make it inactive by default</span></span>
* <span data-ttu-id="dc7b5-172">在 [**On Placing Started ()** ] 事件區段中，按一下 **+** 圖示，以新增新的事件：</span><span class="sxs-lookup"><span data-stu-id="dc7b5-172">In the **On Placing Started ()** event section, click the **+** icon to add a new event:</span></span>
* <span data-ttu-id="dc7b5-173">將 RoverExplorer > **RoverAssembly** 物件指派給**無 (物件)** 欄位</span><span class="sxs-lookup"><span data-stu-id="dc7b5-173">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="dc7b5-174">從 [沒有函式] 下拉式清單中，選取 **TapToPlace** > **bool enabled**，以在觸發事件時更新此屬性值</span><span class="sxs-lookup"><span data-stu-id="dc7b5-174">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="dc7b5-175">確認**未核取**引數核取方塊</span><span class="sxs-lookup"><span data-stu-id="dc7b5-175">Verify that the argument checkbox is **unchecked**</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-6.png)

> [!NOTE]
> <span data-ttu-id="dc7b5-177">現在，當應用程式啟動時，預設會停用點選放置功能，而且只要按下 [點選放置] 按鈕就能啟用。</span><span class="sxs-lookup"><span data-stu-id="dc7b5-177">Now, when the app starts, the Tap to Place functionality is disabled by default and can be enabled by pressing the Tap to Place button.</span></span> <span data-ttu-id="dc7b5-178">此外，當點選放置完成時，會自行停用。</span><span class="sxs-lookup"><span data-stu-id="dc7b5-178">Additionally, when the tap to place is completed, it will disable itself.</span></span>

## <a name="adding-text-to-the-scene"></a><span data-ttu-id="dc7b5-179">將文字加入場景</span><span class="sxs-lookup"><span data-stu-id="dc7b5-179">Adding text to the scene</span></span>

<span data-ttu-id="dc7b5-180">在階層視窗中，以滑鼠右鍵按一下**表格**物件，然後選取 **3D 物件** > **文字 -TextMeshPro**，將文字物件當作表格物件的子系新增，然後在偵測器視窗中，設定**矩形轉換**元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dc7b5-180">In the Hierarchy window, right-click on the **Table** object and select **3D Object** > **Text - TextMeshPro** to add a text object as a child of the Table object, then in the Inspector window, configure the **Rect Transform** component as follows:</span></span>

* <span data-ttu-id="dc7b5-181">將 **Pos Y** 變更為 1</span><span class="sxs-lookup"><span data-stu-id="dc7b5-181">Change **Pos Y** to 1</span></span>
* <span data-ttu-id="dc7b5-182">將**寬度**變更為 1</span><span class="sxs-lookup"><span data-stu-id="dc7b5-182">Change **Width** to 1</span></span>
* <span data-ttu-id="dc7b5-183">將**高度**變更為 1</span><span class="sxs-lookup"><span data-stu-id="dc7b5-183">Change **Height** to 1</span></span>
* <span data-ttu-id="dc7b5-184">將 **旋轉 X** 變更為 90</span><span class="sxs-lookup"><span data-stu-id="dc7b5-184">Change **Rotation X** to 90</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section3-step1-1.png)

<span data-ttu-id="dc7b5-186">然後設定 **TextMeshPro - 文字** 元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dc7b5-186">Then configure the **TextMeshPro - Text** component as follows::</span></span>

* <span data-ttu-id="dc7b5-187">將**文字**變更為 Rover Explorer</span><span class="sxs-lookup"><span data-stu-id="dc7b5-187">Change **Text** to Rover Explorer</span></span>
* <span data-ttu-id="dc7b5-188">將**字型樣式**變更為粗體</span><span class="sxs-lookup"><span data-stu-id="dc7b5-188">Change **Font Style** to Bold</span></span>
* <span data-ttu-id="dc7b5-189">將**字型大小**變更為 1</span><span class="sxs-lookup"><span data-stu-id="dc7b5-189">Change **Font Size** to 1</span></span>
* <span data-ttu-id="dc7b5-190">將其他設定 > **邊界** 變更為 0.03</span><span class="sxs-lookup"><span data-stu-id="dc7b5-190">Change Extra Settings > **Margins** to 0.03</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section3-step1-2.png)

## <a name="adding-tooltips"></a><span data-ttu-id="dc7b5-192">新增工具提示</span><span class="sxs-lookup"><span data-stu-id="dc7b5-192">Adding tooltips</span></span>

<span data-ttu-id="dc7b5-193">在專案視窗中，瀏覽至**資產** > **MRTK** > **SDK** > **功能** > **UX** > **預製物件** > **工具提示**資料夾以尋找具提示預製物件：</span><span class="sxs-lookup"><span data-stu-id="dc7b5-193">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-1.png)

<span data-ttu-id="dc7b5-195">在階層視窗中，展開 RoverExplorer > **RoverParts** 物件，並選取其所有子 Rover 組件物件，然後在偵測器視窗中，使用 [新增元件] 按鈕新增 **ToolTipSpawner**件並加以設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dc7b5-195">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects, then in the Inspector window, use the **Add Component** button to add the **ToolTipSpawner** component and configure it as follows:</span></span>

* <span data-ttu-id="dc7b5-196">確定已核取 [已啟用焦點] 核取方塊，以要求使用者看向要顯示工具提示的位置</span><span class="sxs-lookup"><span data-stu-id="dc7b5-196">Ensure the **Focus Enabled** checkbox is checked to require the user to look at the part for the tooltip to appear</span></span>
* <span data-ttu-id="dc7b5-197">從專案視窗中，將 **簡單線條工具提示**預製物件指派給**工具提示預製物件**欄位</span><span class="sxs-lookup"><span data-stu-id="dc7b5-197">Assign the **Simple Line ToolTip** prefab from the Project window to the **Tool Tip Prefab** field</span></span>
* <span data-ttu-id="dc7b5-198">將工具提示覆寫設定 > **設定模式** 變更為 **覆寫**</span><span class="sxs-lookup"><span data-stu-id="dc7b5-198">Change the ToolTip Override Settings > **Settings Mode** to **Override**</span></span>
* <span data-ttu-id="dc7b5-199">將工具提示覆寫設定 > **手動樞紐分析表位置 Y** 變更為 **1.5**</span><span class="sxs-lookup"><span data-stu-id="dc7b5-199">Change the ToolTip Override Settings > **Manual Pivot Location Position Y** to **1.5**</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-2.png)

<span data-ttu-id="dc7b5-201">在階層視窗中，選取第一個 Rover 元件、RoverParts > **Camera_Part**，然後設定 **ToolTipSpawner** 元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dc7b5-201">In the Hierarchy window, select the first rover part, RoverParts > **Camera_Part**, and configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="dc7b5-202">變更**工具提示文字**以反映組件的名稱，例如**攝影機**</span><span class="sxs-lookup"><span data-stu-id="dc7b5-202">Change **Tool Tip Text** to reflect the name of the part, i.e., **Camera**</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-3.png)

<span data-ttu-id="dc7b5-204">針對每個 Rover 組件物件**重複**此步驟，以設定 **ToolTipSpawner** 元件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dc7b5-204">**Repeat** this step for each of the rover part objects to configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="dc7b5-205">針對 **Generator_Part**，將**工具提示文字**變更為**產生器**</span><span class="sxs-lookup"><span data-stu-id="dc7b5-205">For the **Generator_Part**, change the **Tool Tip Text** to **Generator**</span></span>
* <span data-ttu-id="dc7b5-206">針對 **Lights_Part**，將**工具提示文字**變更為**光源**</span><span class="sxs-lookup"><span data-stu-id="dc7b5-206">For the **Lights_Part**, change the **Tool Tip Text** to **Lights**</span></span>
* <span data-ttu-id="dc7b5-207">針對 **UHFAntenna_Part**，將**工具提示文字**變更為 **UHF 天線**欄位</span><span class="sxs-lookup"><span data-stu-id="dc7b5-207">For the **UHFAntenna_Part**, change the **Tool Tip Text** to **UHF Antenna** field</span></span>
* <span data-ttu-id="dc7b5-208">針對 **Spectrometer_Part**，將**工具提示文字**變更為 **Spectrometer**</span><span class="sxs-lookup"><span data-stu-id="dc7b5-208">For the **Spectrometer_Part**, change the **Tool Tip Text** to **Spectrometer**</span></span>

<span data-ttu-id="dc7b5-209">按下 [開始遊戲] 按鈕進入遊戲模式，然後在往下移動滑鼠時按住滑鼠右鍵，直到目光對到其中一個組件且該組件的工具提示出現為止：</span><span class="sxs-lookup"><span data-stu-id="dc7b5-209">Press the Play button to enter Game mode, then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the parts and the tooltip for that part will be displayed:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="dc7b5-211">恭喜！</span><span class="sxs-lookup"><span data-stu-id="dc7b5-211">Congratulations</span></span>

<span data-ttu-id="dc7b5-212">在本教學課程中，您已了解如何使用 MRTK 提供的按鈕和功能表預製物件和 Unity 的 TextMeshPro 元件來建立簡單的使用者介面，以及如何設定按鈕以在按下時觸發事件。</span><span class="sxs-lookup"><span data-stu-id="dc7b5-212">In this tutorial, you learned how to create a simple user interface using MRTK's provided button and menu prefabs alongside Unity's TextMeshPro component and how to configure the buttons to trigger events when they are pressed.</span></span> <span data-ttu-id="dc7b5-213">您也已了解如何新增動態工具提示 UI 元素，以提供使用者其他資訊。</span><span class="sxs-lookup"><span data-stu-id="dc7b5-213">You also learned how to add dynamic tooltip UI elements to provide the user with additional information.</span></span>

[<span data-ttu-id="dc7b5-214">下一個教學課程：7.與 3D 物件互動</span><span class="sxs-lookup"><span data-stu-id="dc7b5-214">Next Tutorial: 7. Interacting with 3D objects</span></span>](mr-learning-base-07.md)
