---
title: 2. 初始化您的專案和第一個應用程式
description: 教學課程系列的第 2 部分 (共有 6 部分)，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置簡單的國際象棋應用程式
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件
ms.openlocfilehash: e8f03a87ec6b92e4c62cf3f88f519146254e7387
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330329"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="f2caf-104">2.初始化您的專案和第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="f2caf-104">2. Initializing your project and first application</span></span>

## <a name="overview"></a><span data-ttu-id="f2caf-105">概觀</span><span class="sxs-lookup"><span data-stu-id="f2caf-105">Overview</span></span>

<span data-ttu-id="f2caf-106">在此第一個教學課程中，您將針對 HoloLens 2 開始使用新的 Unreal 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f2caf-106">In this first tutorial, you'll get started with a new Unreal application for HoloLens 2.</span></span> <span data-ttu-id="f2caf-107">這會包括新增 HoloLens 外掛程式、建立和照亮層級，以及在其中填入遊戲棋盤和象棋。</span><span class="sxs-lookup"><span data-stu-id="f2caf-107">This is going to include adding the HoloLens plugin, creating and lighting a level, and populating it with a game board and chess piece.</span></span> <span data-ttu-id="f2caf-108">您將針對3D 棋子和物件材質使用預先製作的資產，因此別擔心從頭開始建立任何項目的模型。</span><span class="sxs-lookup"><span data-stu-id="f2caf-108">You'll be using pre-made assets for the 3D chess piece and object materials, so don't worry about modeling anything from scratch.</span></span> <span data-ttu-id="f2caf-109">在本教學課程結束時，您將會有一個可供混合實境使用的空白畫布。</span><span class="sxs-lookup"><span data-stu-id="f2caf-109">By the end of this tutorial you'll have a blank canvas that's ready for mixed reality.</span></span>

<span data-ttu-id="f2caf-110">在繼續之前，請確定您擁有[入門](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch1)頁面中的所有必要條件。</span><span class="sxs-lookup"><span data-stu-id="f2caf-110">Before continuing, make sure you have all the prerequisite from the [Getting Started](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch1) page.</span></span>

## <a name="objectives"></a><span data-ttu-id="f2caf-111">目標</span><span class="sxs-lookup"><span data-stu-id="f2caf-111">Objectives</span></span>
* <span data-ttu-id="f2caf-112">設定 Unreal 專案進行 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="f2caf-112">Configuring an Unreal projet for HoloLens development</span></span>
* <span data-ttu-id="f2caf-113">匯入資產和設定場景</span><span class="sxs-lookup"><span data-stu-id="f2caf-113">Importing assets and setting up a scene</span></span>
* <span data-ttu-id="f2caf-114">使用藍圖建立動作項目和指令碼層級事件</span><span class="sxs-lookup"><span data-stu-id="f2caf-114">Creating Actors and script-level events with blueprints</span></span>

## <a name="creating-a-new-unreal-project"></a><span data-ttu-id="f2caf-115">建立新的 Unreal 專案</span><span class="sxs-lookup"><span data-stu-id="f2caf-115">Creating a new Unreal project</span></span>
<span data-ttu-id="f2caf-116">您需要的第一個項目是供您使用的專案。</span><span class="sxs-lookup"><span data-stu-id="f2caf-116">The first thing you need is a project to work with.</span></span>

1. <span data-ttu-id="f2caf-117">啟動 Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="f2caf-117">Launch Unreal Engine</span></span>

2. <span data-ttu-id="f2caf-118">在 [新增專案類別] 中選取 [遊戲]，然後按 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="f2caf-118">Select **Games** in **New Project Categories** and click **Next**.</span></span> 

![選取遊戲專案範本](images/unreal-uxt/2-gamestemplate.png)

3. <span data-ttu-id="f2caf-120">選取**空白**範本，然後按 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="f2caf-120">Select the **Blank** Template and click **Next**.</span></span> 

![選取空白範本](images/unreal-uxt/2-template.PNG)

4. <span data-ttu-id="f2caf-122">將 [C++]、[可縮放 3D 或 2D]、[行動裝置/平板電腦] 及 [無起始內容] 設為您的 [專案設定]。</span><span class="sxs-lookup"><span data-stu-id="f2caf-122">Set **C++**, **Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content** as your **Project Settings**.</span></span> 
    * <span data-ttu-id="f2caf-123">選擇儲存位置，然後按一下 [建立專案]。</span><span class="sxs-lookup"><span data-stu-id="f2caf-123">Choose a save location and click **Create Project**.</span></span> 

![初始專案設定](images/unreal-uxt/2-project-settings.PNG)

<span data-ttu-id="f2caf-125">專案應該會自動在 Unreal 編輯器中開啟，這表示您已準備好進行下一節。</span><span class="sxs-lookup"><span data-stu-id="f2caf-125">The project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="f2caf-126">啟用必要的外掛程式</span><span class="sxs-lookup"><span data-stu-id="f2caf-126">Enabling required plugins</span></span>
<span data-ttu-id="f2caf-127">在您開始將物件新增至場景之前，必須啟用兩個外掛程式。</span><span class="sxs-lookup"><span data-stu-id="f2caf-127">Before you start adding objects to the scene you'll need to enable two plugins.</span></span>

1. <span data-ttu-id="f2caf-128">開啟 [編輯] > [外掛程式]，然後從內建選項清單中選取 [擴增實境]。</span><span class="sxs-lookup"><span data-stu-id="f2caf-128">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="f2caf-129">向下捲動至 **HoloLens**，並勾選 [啟用]。</span><span class="sxs-lookup"><span data-stu-id="f2caf-129">Scroll down to **HoloLens** and check **Enabled**.</span></span> 

![啟用 HoloLens 外掛程式](images/unreal-uxt/2-plugins.PNG)

2. <span data-ttu-id="f2caf-131">從內建選項清單中選取 [虛擬實境]。</span><span class="sxs-lookup"><span data-stu-id="f2caf-131">Select **Virtual Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="f2caf-132">向下捲動至 **Microsoft Windows Mixed Reality**、勾選 [啟用]，然後重新啟動您的編輯器。</span><span class="sxs-lookup"><span data-stu-id="f2caf-132">Scroll down to **Microsoft Windows Mixed Reality**., check **Enabled**, and restart your editor.</span></span> 

![啟用 Windows Mixed Reality 外掛程式](images/unreal-uxt/2-virtual-reality-plugin.PNG)

> [!NOTE]
> <span data-ttu-id="f2caf-134">這兩個外掛程式都是進行 HoloLens 2 開發的必要項目。</span><span class="sxs-lookup"><span data-stu-id="f2caf-134">Both plugins are required for HoloLens 2 development.</span></span>

<span data-ttu-id="f2caf-135">這麼做之後，您的空白層級已備妥可供公司使用。</span><span class="sxs-lookup"><span data-stu-id="f2caf-135">With that done you're empty level is ready for company.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="f2caf-136">建立層級</span><span class="sxs-lookup"><span data-stu-id="f2caf-136">Creating a level</span></span>
<span data-ttu-id="f2caf-137">您的下一個工作是建立簡單的玩家設定，其中包含一個起點和一個用於參考和調整的立方體。</span><span class="sxs-lookup"><span data-stu-id="f2caf-137">Your next task is to create a simple player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="f2caf-138">選取 [檔案] > [新增層級]，然後選擇 [空白層級]。</span><span class="sxs-lookup"><span data-stu-id="f2caf-138">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="f2caf-139">檢視區中的預設場景現在應該是空白的。</span><span class="sxs-lookup"><span data-stu-id="f2caf-139">The default scene in the viewport should now be empty.</span></span>

2. <span data-ttu-id="f2caf-140">從 [模式] 索引標籤中選取 [基本]，然後將 **PlayerStart** 拖曳至場景。</span><span class="sxs-lookup"><span data-stu-id="f2caf-140">Select **Basic** from the **Modes** tab and drag **PlayerStart** into the scene.</span></span> 
    * <span data-ttu-id="f2caf-141">在 [詳細資料] 索引標籤中，將 [位置] 設定為 **X = 0**、**Y = 0** 和 **Z = 0**。這會在應用程式啟動時，將使用者設在場景中心。</span><span class="sxs-lookup"><span data-stu-id="f2caf-141">Set **Location** to **X = 0**, **Y = 0**, and **Z = 0** in the **Details** tab. This sets the user at the center of the scene when the app starts up.</span></span>

![具有 PlayerStart 的檢視區](images/unreal-uxt/2-playerstart.PNG)

3. <span data-ttu-id="f2caf-143">將 [立方體] 從 [基本] 索引標籤拖曳到場景。</span><span class="sxs-lookup"><span data-stu-id="f2caf-143">Drag a **Cube** from the **Basic** tab into the scene.</span></span> 
    * <span data-ttu-id="f2caf-144">將 [位置] 設定為 **X = 50**、**Y = 0** 和 **Z = 0**。</span><span class="sxs-lookup"><span data-stu-id="f2caf-144">Set **Location** to **X = 50**, **Y = 0**, and **Z = 0**.</span></span> <span data-ttu-id="f2caf-145">這會在開始時將立方體放在離玩家 50 公分處。</span><span class="sxs-lookup"><span data-stu-id="f2caf-145">This positions the cube 50 cm away from the player at start time.</span></span> 
    * <span data-ttu-id="f2caf-146">將 [縮放] 變更為 **X = 0.2**、**Y = 0.2** 和 **Z = 0.2**，以縮小立方體。</span><span class="sxs-lookup"><span data-stu-id="f2caf-146">Change **Scale** to **X = 0.2**, **Y = 0.2**, and **Z = 0.2** to shrink the cube down.</span></span> 

<span data-ttu-id="f2caf-147">您將無法看到立方體，除非您將光線新增至場景，這是測試場景前的最後一項工作。</span><span class="sxs-lookup"><span data-stu-id="f2caf-147">You won’t be able to see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="f2caf-148">切換至 [模式] 面板上的 [光線] 索引標籤，然後將 [定向光線] 拖曳至場景。</span><span class="sxs-lookup"><span data-stu-id="f2caf-148">Switch to the **Lights** tab in the **Modes** panel and drag a **Directional Light** into the scene.</span></span> <span data-ttu-id="f2caf-149">將光線放在 **PlayerStart** 上方，讓您可以看到。</span><span class="sxs-lookup"><span data-stu-id="f2caf-149">Position the light above **PlayerStart** so you can see it.</span></span>

![已新增光線的檢視區](images/unreal-uxt/2-light.PNG)

5. <span data-ttu-id="f2caf-151">移至 [檔案] > [儲存目前的]、將您的層級命名為 **Main**，然後按一下 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="f2caf-151">Go to **File > Save Current**, name your level **Main**, and click **Save**.</span></span> 

<span data-ttu-id="f2caf-152">設定場景後，請按下工具列中的 [播放]，以查看行動中的立方體！</span><span class="sxs-lookup"><span data-stu-id="f2caf-152">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="f2caf-153">當您完成工作的管理時，請按 **Esc** 以停止應用程式。</span><span class="sxs-lookup"><span data-stu-id="f2caf-153">When you're finished admiring your work, press **Esc** to stop the application.</span></span>

![檢視區中的立方體](images/unreal-uxt/2-cube.PNG)

<span data-ttu-id="f2caf-155">既然已設定場景，您就可以開始加入棋盤和棋子，以完善應用程式環境。</span><span class="sxs-lookup"><span data-stu-id="f2caf-155">Now that the scene is setup, you can start adding in the chess board and piece to round out the application environment.</span></span>

## <a name="importing-assets"></a><span data-ttu-id="f2caf-156">匯入資產</span><span class="sxs-lookup"><span data-stu-id="f2caf-156">Importing assets</span></span>
<span data-ttu-id="f2caf-157">場景目前看起來有點空，但是您會將現成的資產匯入專案，以修正此情況。</span><span class="sxs-lookup"><span data-stu-id="f2caf-157">The scene is looking a bit empty at the moment, but you'll fix that by importing the ready-made assets into the project.</span></span>

1. <span data-ttu-id="f2caf-158">下載並解壓縮 [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) 資產資料夾。</span><span class="sxs-lookup"><span data-stu-id="f2caf-158">Download and unzip the [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) assets folder.</span></span>

2. <span data-ttu-id="f2caf-159">從 [內容瀏覽器] 中按一下 [新增] > [新增資料夾]，並將其命名為 **ChessAssets**。</span><span class="sxs-lookup"><span data-stu-id="f2caf-159">Click **Add New > New Folder** from the **Content Browser** and name it **ChessAssets**.</span></span> 
    * <span data-ttu-id="f2caf-160">按兩下新資料夾 - 這是您將匯入3D 資產的位置。</span><span class="sxs-lookup"><span data-stu-id="f2caf-160">Double-click the new folder - this is where you'll import the 3D assets.</span></span>

![顯示或隱藏來源面板](images/unreal-uxt/2-showhidesources.PNG)

3. <span data-ttu-id="f2caf-162">從 [內容瀏覽器] 中按一下 [匯入]、選取解壓縮資產資料夾中的所有專案，然後按一下 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="f2caf-162">Click **Import** from the **Content Browser**, select all the items in the unzipped assets folder and click **Open**.</span></span> 
    * <span data-ttu-id="f2caf-163">此資料夾包含適用於棋盤和棋子並採用 FBX 格式的 3D 物件網格，以及將用於材質並採用 TGA 格式的紋理圖。</span><span class="sxs-lookup"><span data-stu-id="f2caf-163">This folder contains the 3D object meshes for the chess board and pieces in FBX format and texture maps in TGA format that you'll use to for materials.</span></span>  

4. <span data-ttu-id="f2caf-164">當 [FBX 匯入選項] 視窗快顯時，請展開 [材質] 區段，然後將 [材質匯入方法] 變更為 [不要建立材質]。</span><span class="sxs-lookup"><span data-stu-id="f2caf-164">When the FBX Import Options window pops up, expand the **Material** section and change **Material Import Method** to **Do Not Create Material**.</span></span>
    * <span data-ttu-id="f2caf-165">按一下 [全部匯入]。</span><span class="sxs-lookup"><span data-stu-id="f2caf-165">Click **Import All**.</span></span>

![匯入 FBX 選項](images/unreal-uxt/2-nocreatemat.PNG)

<span data-ttu-id="f2caf-167">您只需針對資產執行這個動作即可。</span><span class="sxs-lookup"><span data-stu-id="f2caf-167">That's all you need to do for the assets.</span></span> <span data-ttu-id="f2caf-168">您的下一組工作是使用藍圖來建立應用程式的建置區塊。</span><span class="sxs-lookup"><span data-stu-id="f2caf-168">Your next set of tasks is to create the building blocks of the application with blueprints.</span></span>

## <a name="adding-blueprints"></a><span data-ttu-id="f2caf-169">新增藍圖</span><span class="sxs-lookup"><span data-stu-id="f2caf-169">Adding blueprints</span></span>

1. <span data-ttu-id="f2caf-170">按一下 [內容瀏覽器] 中的 [新增] > [新增資料夾]，並將其命名為 **Content Browser**。</span><span class="sxs-lookup"><span data-stu-id="f2caf-170">Click **Add New > New Folder** in the **Content Browser** and name it **Content Browser**.</span></span> 

> [!NOTE]
> <span data-ttu-id="f2caf-171">如果您不熟悉[藍圖](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html)，這些藍圖是特殊資產，可提供節點型介面，用於建立新類型的動作項目和指令碼層級事件。</span><span class="sxs-lookup"><span data-stu-id="f2caf-171">If you're new to [blueprints](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html), they're special assets that provide a node-based interface for creating new types of Actors and script level events.</span></span> 

2. <span data-ttu-id="f2caf-172">按兩下 [藍圖] 資料夾，然後按一下滑鼠右鍵並選取 [藍圖類別]。</span><span class="sxs-lookup"><span data-stu-id="f2caf-172">Double-click into the **Blueprints** folder, then right-click and select **Blueprint Class**.</span></span>         
    * <span data-ttu-id="f2caf-173">選取 [動作項目]，並將藍圖命名為 **Board**。</span><span class="sxs-lookup"><span data-stu-id="f2caf-173">Select **Actor** and name the blueprint **Board**.</span></span> 

![選取您藍圖的父類別](images/unreal-uxt/2-bpparent.PNG)

<span data-ttu-id="f2caf-175">新的 **Board** 藍圖現在會顯示在 **Blueprints** 資料夾中，如下列螢幕擷取畫面中所看到。</span><span class="sxs-lookup"><span data-stu-id="f2caf-175">The new **Board** blueprint now shows up in the **Blueprints** folder as seen in the following screenshot.</span></span> 

![新的棋盤藍圖](images/unreal-uxt/2-bpboard.PNG)

<span data-ttu-id="f2caf-177">您已準備好開始將材質新增至所建立的物件。</span><span class="sxs-lookup"><span data-stu-id="f2caf-177">You're all set to start adding materials to the created objects.</span></span>

## <a name="working-with-materials"></a><span data-ttu-id="f2caf-178">使用材質</span><span class="sxs-lookup"><span data-stu-id="f2caf-178">Working with materials</span></span>
<span data-ttu-id="f2caf-179">您所建立的物件預設為灰色，這並不好查看。</span><span class="sxs-lookup"><span data-stu-id="f2caf-179">The objects you've created are default grey, which isn't much fun to look at.</span></span> <span data-ttu-id="f2caf-180">將材質和網格新增至您的物件是本教學課程中的最後一組工作。</span><span class="sxs-lookup"><span data-stu-id="f2caf-180">Adding materials and meshes to your objects is the last set of tasks in this tutorial.</span></span>

1. <span data-ttu-id="f2caf-181">按兩下 **Board** 以開啟藍圖編輯器。</span><span class="sxs-lookup"><span data-stu-id="f2caf-181">Double-click **Board** to open the blueprint editor.</span></span> 

2. <span data-ttu-id="f2caf-182">從 [元件] 面板中按一下 [新增元件] > [場景]，並將其命名為 **Root**。</span><span class="sxs-lookup"><span data-stu-id="f2caf-182">Click **Add Component > Scene** from the **Components** panel and name it **Root**.</span></span> <span data-ttu-id="f2caf-183">請注意，**Root** 會在下列螢幕擷取畫面中顯示為 **DefaultSceneRoot** 的子系：</span><span class="sxs-lookup"><span data-stu-id="f2caf-183">Notice that **Root** shows up as a child of **DefaultSceneRoot** in the screenshot below:</span></span>

![取代根項目](images/unreal-uxt/2-root-blueprint.PNG)


3. <span data-ttu-id="f2caf-185">按一下 **Root** 並將其拖曳至 **DefaultSceneRoot** 以進行取代，然後消除檢視區中的球體。</span><span class="sxs-lookup"><span data-stu-id="f2caf-185">Click-and-drag **Root** onto **DefaultSceneRoot** to replace it and get rid of the sphere in the viewport.</span></span> 

![取代根項目](images/unreal-uxt/2-root.PNG)


4. <span data-ttu-id="f2caf-187">從 [元件] 面板中按一下 [新增元件] > [靜態網格]，並將其命名為 **SM_Board**。</span><span class="sxs-lookup"><span data-stu-id="f2caf-187">Click **Add Component > Static Mesh** from the **Components** panel and name it **SM_Board**.</span></span> <span data-ttu-id="f2caf-188">其會在 **Root** 底下顯示為子物件。</span><span class="sxs-lookup"><span data-stu-id="f2caf-188">It will appear as a child object under **Root**.</span></span>

![新增靜態網格](images/unreal-uxt/2-sm-board.PNG)

4. <span data-ttu-id="f2caf-190">按一下 **SM_Board**、向下捲動至 [ 詳細資料] 面板的 [靜態網格] 區段，然後從下拉式清單中選取 **ChessBoard**。</span><span class="sxs-lookup"><span data-stu-id="f2caf-190">Click **SM_Board**, scroll down to the **Static Mesh** section of the **Details** panel, and select **ChessBoard** from the dropdown.</span></span> 

![檢視區中的棋盤網格](images/unreal-uxt/2-sm-board-view.PNG)

5.  <span data-ttu-id="f2caf-192">仍在 [詳細資料] 面板中，展開 [材質] 區段，然後從下拉式清單中按一下 [建立新資產] > [材質]。</span><span class="sxs-lookup"><span data-stu-id="f2caf-192">Still in the **Details** panel, expand the **Materials** section and click **Create New Asset > Material** from the dropdown.</span></span> 
    * <span data-ttu-id="f2caf-193">將材質命名為 **M_ChessBoard**，並將其儲存在 **ChessAssets** 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="f2caf-193">Name the material **M_ChessBoard** and save it to the **ChessAssets** folder.</span></span> 

![建立新的材質](images/unreal-uxt/2-newmat.PNG)

6.  <span data-ttu-id="f2caf-195">按兩下 **M_ChessBoard** 材質影像以開啟材質編輯器。</span><span class="sxs-lookup"><span data-stu-id="f2caf-195">Double-click the **M_ChessBoard** material imaged to open the Material Editor.</span></span> 

![開啟材質編輯器](images/unreal-uxt/2-material-editor.PNG)

7. <span data-ttu-id="f2caf-197">在材質編輯器中，按一下滑鼠右鍵，然後搜尋**紋理範例**。</span><span class="sxs-lookup"><span data-stu-id="f2caf-197">In the Material Editor, right-click and search for **Texture Sample**.</span></span> 
    * <span data-ttu-id="f2caf-198">展開 [詳細資料] 面板中的 [材質呈現紋理基底] 區段，然後將 [紋理] 設定為 **ChessBoard_Albedo**。</span><span class="sxs-lookup"><span data-stu-id="f2caf-198">Expand the **Material Expression Texture Base** section in the **Details** panel and set **Texture** to **ChessBoard_Albedo**.</span></span> 
    * <span data-ttu-id="f2caf-199">將 **RGB** 輸出釘選拖曳到 **M_ChessBoard** 的 [基本色彩] 釘選。</span><span class="sxs-lookup"><span data-stu-id="f2caf-199">Drag the **RGB** output pin to the Base Color pin of **M_ChessBoard**.</span></span> 

![設定基本色彩](images/unreal-uxt/2-boardalbedomat.PNG)

8.  <span data-ttu-id="f2caf-201">再重複四次上述步驟，使用下列設定再建立四個**紋理範例**節點：</span><span class="sxs-lookup"><span data-stu-id="f2caf-201">Repeat the previous step four more times to create four more **Texture Sample** nodes with the following settings:</span></span>
    * <span data-ttu-id="f2caf-202">將 [材質] 設定為 **ChessBoard_AO**，並將 **RGB** 連結至 [環境光遮蔽] 釘選。</span><span class="sxs-lookup"><span data-stu-id="f2caf-202">Set **Texture** to **ChessBoard_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="f2caf-203">將 [材質] 設定為 **ChessBoard_Metal**，並將 **RGB** 連結至 [金屬] 釘選。</span><span class="sxs-lookup"><span data-stu-id="f2caf-203">Set **Texture** to **ChessBoard_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="f2caf-204">將 [材質] 設定為 **ChessBoard_Normal**，並將 **RGB** 連結至 [一般] 釘選。</span><span class="sxs-lookup"><span data-stu-id="f2caf-204">Set **Texture** to **ChessBoard_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="f2caf-205">將 [材質] 設定為 **ChessBoard_Rough**，並將 **RGB** 連結至 [粗糙度] 釘選。</span><span class="sxs-lookup"><span data-stu-id="f2caf-205">Set **Texture** to **ChessBoard_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="f2caf-206">按一下 **[儲存]** 。</span><span class="sxs-lookup"><span data-stu-id="f2caf-206">Click **Save**.</span></span> 

![連結其餘紋理](images/unreal-uxt/2-boardmat.PNG)

<span data-ttu-id="f2caf-208">請先確定您的材質設定看起來像是上述螢幕擷取畫面，再繼續進行。</span><span class="sxs-lookup"><span data-stu-id="f2caf-208">Make sure the your material setup looks like the above screenshot before continuing.</span></span>

## <a name="populating-the-scene"></a><span data-ttu-id="f2caf-209">填入場景</span><span class="sxs-lookup"><span data-stu-id="f2caf-209">Populating the scene</span></span>
<span data-ttu-id="f2caf-210">如果回到 **Board** 藍圖，您會看到已套用您剛建立的材質。</span><span class="sxs-lookup"><span data-stu-id="f2caf-210">If you go back to the **Board** blueprint, you'll see that the material you just created has been applied.</span></span> <span data-ttu-id="f2caf-211">剩下的就是設定場景！</span><span class="sxs-lookup"><span data-stu-id="f2caf-211">All that's left is setting up the scene!</span></span> <span data-ttu-id="f2caf-212">首先，變更下列屬性，以確保棋盤在放入場景時大小合理，且角度正確：</span><span class="sxs-lookup"><span data-stu-id="f2caf-212">First, change the following properties to make sure the board is a reasonable size and angled correctly when it's placed in the scene:</span></span>
1.  <span data-ttu-id="f2caf-213">將 [縮放] 設定為 **(0.05, 0.05, 0.05)** ，並將 [Z 旋轉] 設定為 **90**。</span><span class="sxs-lookup"><span data-stu-id="f2caf-213">Set **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span> 
    * <span data-ttu-id="f2caf-214">按一下頂端工具列中的 [編譯]，然後按一下 [儲存] 並返回主視窗。</span><span class="sxs-lookup"><span data-stu-id="f2caf-214">Click **Compile** in the top toolbar, then **Save** and return to the Main window.</span></span> 

![已套用材質的棋盤](images/unreal-uxt/2-chessboard.PNG)

2.  <span data-ttu-id="f2caf-216">以滑鼠右鍵按一下 [立方體] > [編輯] > [刪除]，然後將 [棋盤] 從 [內容瀏覽器] 拖曳至檢視區。</span><span class="sxs-lookup"><span data-stu-id="f2caf-216">Right-click **Cube > Edit > Delete** and drag **Board** from the **Content Browser** into the viewport.</span></span> 
    * <span data-ttu-id="f2caf-217">將 [位置] 設定為 **X = 80**、**Y = 0** 和 **Z = 20**。</span><span class="sxs-lookup"><span data-stu-id="f2caf-217">Set **Location** to **X = 80**, **Y = 0**, and **Z = -20**.</span></span> 

3.  <span data-ttu-id="f2caf-218">按一下 [播放] 按鈕，以在層級中檢視您的新棋盤。</span><span class="sxs-lookup"><span data-stu-id="f2caf-218">Click the **Play** button to view your new board in the level.</span></span> <span data-ttu-id="f2caf-219">按 **Esc** 即可返回編輯器。</span><span class="sxs-lookup"><span data-stu-id="f2caf-219">Press **Esc** to return to the editor.</span></span> 

<span data-ttu-id="f2caf-220">現在您將遵循相同的步驟來建立棋子，如同您建立棋盤一般：</span><span class="sxs-lookup"><span data-stu-id="f2caf-220">Now you'll follow the same steps to create a chess piece as you did with the board:</span></span>

1. <span data-ttu-id="f2caf-221">移至 [藍圖] 資料夾、按一下滑鼠右鍵並選取 [藍圖類別]，然後選擇 [動作項目]。</span><span class="sxs-lookup"><span data-stu-id="f2caf-221">Go to the **Blueprints** folder, right-click and select **Blueprint Class** and choose **Actor**.</span></span> <span data-ttu-id="f2caf-222">將動作項目命名為 **WhiteKing**。</span><span class="sxs-lookup"><span data-stu-id="f2caf-222">Name the actor **WhiteKing**.</span></span>

2. <span data-ttu-id="f2caf-223">按兩下 **WhiteKing** 以在藍圖編輯器中將其開啟、按一下 [新增元件] > [場景]，並將其命名為 **Root**。</span><span class="sxs-lookup"><span data-stu-id="f2caf-223">Double click **WhiteKing** to open it in the Blueprint Editor, click **Add Component > Scene** and name it **Root**.</span></span> 
    * <span data-ttu-id="f2caf-224">將 **Root** 拖放至 **DefaultSceneRoot**，以將其取代。</span><span class="sxs-lookup"><span data-stu-id="f2caf-224">Drag-and-drop **Root** onto **DefaultSceneRoot** to replace it.</span></span> 

3. <span data-ttu-id="f2caf-225">按一下 [新增元件] > [靜態網格]，並將其命名為 **SM_King**。</span><span class="sxs-lookup"><span data-stu-id="f2caf-225">Click **Add Component > Static Mesh** and name it **SM_King**.</span></span> 
    * <span data-ttu-id="f2caf-226">在 [詳細資料] 面板中，將 [靜態網格] 設定為 **Chess_King**，將 [材質] 設定為名為 **M_ChessWhite** 的新材質。</span><span class="sxs-lookup"><span data-stu-id="f2caf-226">Set **Static Mesh** to **Chess_King** and **Material** to a new Material called **M_ChessWhite** in the Details panel.</span></span> 

4. <span data-ttu-id="f2caf-227">在材質編輯器中開啟 **M_ChessWhite**，並將下列**紋理範例**節點連結至下列項目：</span><span class="sxs-lookup"><span data-stu-id="f2caf-227">Open **M_ChessWhite** in the Material editor and hook up the following **Texture Sample** nodes to the following:</span></span>
    * <span data-ttu-id="f2caf-228">將 [材質] 設定為 **ChessWhite_AO**，並將 **RGB** 連結至 [環境光遮蔽] 釘選。</span><span class="sxs-lookup"><span data-stu-id="f2caf-228">Set **Texture** to **ChessWhite_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="f2caf-229">將 [材質] 設定為 **ChessWhite_Metal**，並將 **RGB** 連結至 [金屬] 釘選。</span><span class="sxs-lookup"><span data-stu-id="f2caf-229">Set **Texture** to **ChessWhite_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="f2caf-230">將 [材質] 設定為 **ChessWhite_Normal**，並將 **RGB** 連結至 [一般] 釘選。</span><span class="sxs-lookup"><span data-stu-id="f2caf-230">Set **Texture** to **ChessWhite_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="f2caf-231">將 [材質] 設定為 **ChessWhite_Rough**，並將 **RGB** 連結至 [粗糙度] 釘選。</span><span class="sxs-lookup"><span data-stu-id="f2caf-231">Set **Texture** to **ChessWhite_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="f2caf-232">按一下 **[儲存]** 。</span><span class="sxs-lookup"><span data-stu-id="f2caf-232">Click **Save**.</span></span> 

<span data-ttu-id="f2caf-233">在繼續之前，您的 **M_ChessKing** 材質應該看起來像是下圖。</span><span class="sxs-lookup"><span data-stu-id="f2caf-233">Your **M_ChessKing** material should look like the following image before continuing.</span></span>

![為國王棋建立材質](images/unreal-uxt/2-chesskingmat.PNG)

<span data-ttu-id="f2caf-235">您幾乎只需將新的棋子加入場景中就大功告成了：</span><span class="sxs-lookup"><span data-stu-id="f2caf-235">You're almost there, just need to add the new chess piece into the scene:</span></span> 

1. <span data-ttu-id="f2caf-236">開啟 **WhiteKing** 藍圖，然後將 [縮放] 變更為 **(0.05, 0.05, 0.05)** ，並將 [Z 旋轉] 設定為 **90**。</span><span class="sxs-lookup"><span data-stu-id="f2caf-236">Open the **WhiteKing** blueprint and change the **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span>
    * <span data-ttu-id="f2caf-237">編譯並儲存您的藍圖，然後回到主視窗。</span><span class="sxs-lookup"><span data-stu-id="f2caf-237">Compile and save your blueprint, then head back to the main window.</span></span> 

2.  <span data-ttu-id="f2caf-238">將 **WhiteKing** 拖曳到檢視區、切換至 [世界大綱] 面板，然後將 **WhiteKing** 拖曳至 [棋盤]，使其成為子物件。</span><span class="sxs-lookup"><span data-stu-id="f2caf-238">Drag **WhiteKing** into the viewport, switch to the **World Outliner** panel drag **WhiteKing** onto **Board** to make it a child object.</span></span>

![世界大綱](images/unreal-uxt/2-child.PNG)

3.  <span data-ttu-id="f2caf-240">在 [變形] 底下的 [詳細資料] 面板中，將 **WhiteKing** 的 [位置] 設定為 **X = -26**、**Y = 4** 和 **Z = 0**。</span><span class="sxs-lookup"><span data-stu-id="f2caf-240">In the **Details** panel under **Transform**, set **WhiteKing**'s **Location** to **X = -26**, **Y = 4**, and **Z = 0**.</span></span>

<span data-ttu-id="f2caf-241">收工了！</span><span class="sxs-lookup"><span data-stu-id="f2caf-241">That's a wrap!</span></span> <span data-ttu-id="f2caf-242">按一下 [播放] 查看您填入的作用中層級，然後在您準備好要結束時，按 **Esc**。</span><span class="sxs-lookup"><span data-stu-id="f2caf-242">Click **Play** to see your populated level in action, and press **Esc** when you're ready to exit.</span></span> <span data-ttu-id="f2caf-243">本教學課程涵蓋了許多建立簡單專案的基礎，但您的專案已準備好繼續進行系列的下一個部分：設定混合實境。</span><span class="sxs-lookup"><span data-stu-id="f2caf-243">This tutorial covered a lot of ground creating a simple project, but your project is ready to move on to the next part of the series: setting up for mixed reality.</span></span> 

[<span data-ttu-id="f2caf-244">下一節：3.設定您的專案以進行混合實境</span><span class="sxs-lookup"><span data-stu-id="f2caf-244">Next Section: 3. Set up your project for mixed reality</span></span>](unreal-uxt-ch3.md)