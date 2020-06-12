---
title: 3. 設定您的專案以進行混合實境
description: 教學課程系列的第 3 部分 (共有 6 部分)，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置簡單的國際象棋應用程式
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件
ms.openlocfilehash: d22c3d8c9048f53171298642768877d7bcdcb972
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330281"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a><span data-ttu-id="6c7f1-104">3.設定您的專案以進行混合實境</span><span class="sxs-lookup"><span data-stu-id="6c7f1-104">3. Setting up your project for mixed reality</span></span>

## <a name="overview"></a><span data-ttu-id="6c7f1-105">概觀</span><span class="sxs-lookup"><span data-stu-id="6c7f1-105">Overview</span></span>

<span data-ttu-id="6c7f1-106">在上一個教學課程中，您已花費時間設定國際象棋應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-106">In the previous tutorial, you spent time setting up the chess app project.</span></span> <span data-ttu-id="6c7f1-107">本節將逐步引導您設定應用程式以進行混合實境開發，這表示新增 AR 工作階段。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-107">This section is going to walk you through setting up the app for mixed reality development, which means adding an AR session.</span></span> <span data-ttu-id="6c7f1-108">您將會針對此工作使用 ARSessionConfig 資料資產，其中有很多有用的 AR 設定，例如空間對應和遮蔽。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-108">You'll be using an ARSessionConfig data asset for this task, which has a lot of useful AR settings like spatial mapping and occlusion.</span></span> <span data-ttu-id="6c7f1-109">如果您想要深入了解，Unreal Engine 文件有更多關於 [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) 資產和 [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) 類別的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-109">If you want to dive deeper, the Unreal Engine documentation has more details on the [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) asset and the [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) class.</span></span>

## <a name="objectives"></a><span data-ttu-id="6c7f1-110">目標</span><span class="sxs-lookup"><span data-stu-id="6c7f1-110">Objectives</span></span>
* <span data-ttu-id="6c7f1-111">使用 Unreal Engine 的 AR 設定</span><span class="sxs-lookup"><span data-stu-id="6c7f1-111">Working with Unreal Engine's AR settings</span></span> 
* <span data-ttu-id="6c7f1-112">使用 ARSessionConfig 資料資產</span><span class="sxs-lookup"><span data-stu-id="6c7f1-112">Using an ARSessionConfig data asset</span></span>
* <span data-ttu-id="6c7f1-113">設定 Pawn 和遊戲模式</span><span class="sxs-lookup"><span data-stu-id="6c7f1-113">Setting up a Pawn and game mode</span></span>

## <a name="adding-the-session-asset"></a><span data-ttu-id="6c7f1-114">新增工作階段資產</span><span class="sxs-lookup"><span data-stu-id="6c7f1-114">Adding the session asset</span></span>
<span data-ttu-id="6c7f1-115">Unreal 中的 AR 工作階段本身不會發生。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-115">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="6c7f1-116">若要使用工作階段，您需有 ARSessionConfig 資料資產來使用，這是您的下一項工作：</span><span class="sxs-lookup"><span data-stu-id="6c7f1-116">To use a session you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="6c7f1-117">在 [內容瀏覽器] 中，按一下 [新增] > [其他] > [資料資產]。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-117">Click **Add New > Miscellaneous > Data Asset** in the **Content Browser**.</span></span> <span data-ttu-id="6c7f1-118">確定您是在根**內容**資料夾層級。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-118">Make sure you're at the root **Content** folder level.</span></span> 
    * <span data-ttu-id="6c7f1-119">選取 **ARSessionConfig**按一下 [選取]，然後將資產命名為 **ARSessionConfig**。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-119">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**.</span></span>

![建立資料資產](images/unreal-uxt/3-createasset.PNG)

3. <span data-ttu-id="6c7f1-121">按兩下 **ARSessionConfig** 將其開啟、保留所有預設設定，然後點擊 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-121">Double-click **ARSessionConfig** to open it, leave all default settings and hit **Save**.</span></span> <span data-ttu-id="6c7f1-122">返回主視窗。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-122">Return to the Main window.</span></span> 

![AR 工作階段設定](images/unreal-uxt/3-arsessionconfig.PNG)

<span data-ttu-id="6c7f1-124">完成後，您的下一個步驟是確保 AR 工作階段會在層級載入時啟動。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-124">With that done, your next step is to make sure that the AR session starts when the level loads.</span></span> <span data-ttu-id="6c7f1-125">幸好，Unreal 具有特殊種類的藍圖，稱為**層級藍圖**，可作為整個層級的全域事件圖形。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-125">Luckily, Unreal has a special kind of blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="6c7f1-126">在**層級藍圖**中連線 ARSessionConfig 資產，保證 AR 工作階段會在遊戲開始玩時立即啟動。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-126">Connecting the ARSessionConfig asset in the **Level Blueprint** guarantees the AR session will fire right when the game starts playing.</span></span>

1. <span data-ttu-id="6c7f1-127">從編輯器工具列中按一下 [藍圖] > [開啟層級藍圖]：</span><span class="sxs-lookup"><span data-stu-id="6c7f1-127">Click **Blueprints > Open Level Blueprint** from the editor toolbar:</span></span> 

![開啟層級藍圖](images/unreal-uxt/3-level-blueprint.PNG)

5. <span data-ttu-id="6c7f1-129">拖曳 **Event BeginPlay** 的執行節點 (向左箭號圖示) 並放開。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-129">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release.</span></span> <span data-ttu-id="6c7f1-130">搜尋 [啟動 AR 工作階段] 並點擊 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-130">Search for the **Start AR Session** and hit enter.</span></span>  
    * <span data-ttu-id="6c7f1-131">按一下 [工作階段組態] 底下的 [選取資產] 下拉式清單，然後選擇 **ARSessionConfig** 資產。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-131">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset.</span></span> 
    * <span data-ttu-id="6c7f1-132">依序點擊 [編譯]、[儲存]，然後返回主視窗。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-132">Hit **Compile**, then **Save** and return to the Main window.</span></span>

![啟動 AR 工作階段](images/unreal-uxt/3-start-ar-session.PNG)

## <a name="create-a-pawn"></a><span data-ttu-id="6c7f1-134">建立 Pawn</span><span class="sxs-lookup"><span data-stu-id="6c7f1-134">Create a Pawn</span></span>
<span data-ttu-id="6c7f1-135">此時，專案仍然需要玩家物件。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-135">At this point, the project still needs a player object.</span></span> <span data-ttu-id="6c7f1-136">在 Unreal 中，**Pawn** 代表遊戲中的使用者，或在此案例中，其將是 HoloLens 2 體驗。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-136">In Unreal, a **Pawn** represents the user in the game, but in this case it's going to be the HoloLens 2 experience.</span></span>

1. <span data-ttu-id="6c7f1-137">在 [內容] 資料夾中按一下 [新增] > [藍圖類別]，然後展開底端的 [所有類別] 區段。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-137">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span> 
    * <span data-ttu-id="6c7f1-138">搜尋 **DefaultPawn**按一下 [選取]，然後按兩下要開啟的資產。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-138">Search for **DefaultPawn**, click **Select** and double-click the asset to open.</span></span> 

![建立繼承自 DefaultPawn 的新 Pawn](images/unreal-uxt/3-defaultpawn.PNG)

> [!NOTE]
> <span data-ttu-id="6c7f1-140">根據預設，Pawn 具有網格和碰撞元件。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-140">By default, Pawns have mesh and collision components.</span></span> <span data-ttu-id="6c7f1-141">在大部分的 Unreal 專案中，Pawn 是可與其他元件碰撞的固體物件。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-141">In most Unreal projects, Pawns are solid objects that can collide with other components.</span></span> <span data-ttu-id="6c7f1-142">由於 Pawn 和使用者在混合實境中是相同的，因此您希望能夠在不發生任何碰撞的情況下通過全像投影。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-142">Since the Pawn and user are the same in mixed reality, you want to be able to pass through holograms without any collisions.</span></span> 

2. <span data-ttu-id="6c7f1-143">從 [元件] 面板中選取 **CollisionComponent**，然後向下捲動至 [詳細資料] 面板的 [碰撞] 區段。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-143">Select **CollisionComponent** from the **Components** panel and scroll down to the **Collision** section of the **Details** panel.</span></span> 
    * <span data-ttu-id="6c7f1-144">按一下 [碰撞預設] 下拉式清單，然後將值變更為 **NoCollision**。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-144">Click the **Collision Presets** dropdown and change the value to **NoCollision**.</span></span> 
    * <span data-ttu-id="6c7f1-145">對於 **MeshComponent** 執行相同的動作，然後**編譯**並**儲存**藍圖。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-145">Do the same for the **MeshComponent**, then **Compile** and **Save** the Blueprint.</span></span> 

![調整 Pawn 的衝突預設值](images/unreal-uxt/3-nocollision.PNG)

<span data-ttu-id="6c7f1-147">您在這裡的工作完成後，回到主視窗。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-147">With your work here done, return to the Main Window.</span></span>

## <a name="create-a-game-mode"></a><span data-ttu-id="6c7f1-148">建立遊戲模式</span><span class="sxs-lookup"><span data-stu-id="6c7f1-148">Create a Game Mode</span></span>
<span data-ttu-id="6c7f1-149">混合實境設定的最後一塊拼圖是遊戲模式。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-149">The last puzzle piece of the mixed reality setup is the Game Mode.</span></span> <span data-ttu-id="6c7f1-150">遊戲模式會決定遊戲或體驗的一些設定，包括要使用的預設 Pawn。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-150">The Game Mode determines a number of settings for the game or experience, including the default pawn to use.</span></span>

1.  <span data-ttu-id="6c7f1-151">在 [內容] 資料夾中按一下 [新增] > [藍圖類別]，然後展開底端的 [所有類別] 區段。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-151">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span> 
    * <span data-ttu-id="6c7f1-152">搜尋 [遊戲模式基底]、將其命名為 **MRGameMode**，然後按兩下來開啟。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-152">Search for **Game Mode Base**, name it **MRGameMode** and double-click to open.</span></span> 

![內容瀏覽器中的 MRGameMode](images/unreal-uxt/3-gamemode.PNG)

2.  <span data-ttu-id="6c7f1-154">移至 [詳細資料] 面板中的 [類別] 區段，然後將 [預設 Pawn 類別] 變更為 **MRPawn**。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-154">Go to the **Classes** section in the **Details** panel and change the **Default Pawn Class** to **MRPawn**.</span></span> 
    * <span data-ttu-id="6c7f1-155">依序點擊 [編譯]、[儲存]，然後返回主視窗。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-155">Hit **Compile**, then **Save** and return to the Main window.</span></span> 

![設定預設的 Pawn 類別](images/unreal-uxt/3-setpawn.PNG)

3.  <span data-ttu-id="6c7f1-157">選取 [編輯] > [專案設定]，然後按一下左側清單中的 [地圖與模式]。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-157">Select **Edit > Projects Settings** and click **Maps & Modes** in the left-hand list.</span></span> 
    * <span data-ttu-id="6c7f1-158">展開 [預設模式]，然後將 [預設遊戲模式] 變更為 **MRGameMode**。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-158">Expand **Default Modes** and change **Default Game Mode** to **MRGameMode**.</span></span> 
    * <span data-ttu-id="6c7f1-159">展開 [預設地圖]，然後同時將 **EditorStartupMap** 和 **GameDefaultMap** 變更為 **Main**。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-159">Expand **Default Maps** and change both **EditorStartupMap** and **GameDefaultMap** to **Main**.</span></span> <span data-ttu-id="6c7f1-160">如此一來，當您關閉編輯器並重新開啟時，系統會預設為選取主要地圖。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-160">This way when you close and reopen the editor, or play the game, the Main map will be selected by default.</span></span>

![專案設定 - 地圖與模式](images/unreal-uxt/3-mapsandmodes.PNG)

<span data-ttu-id="6c7f1-162">在混合實境的專案完全設定好之後，您就可以繼續進行下一個教學課程，並開始將使用者輸入新增到場景。</span><span class="sxs-lookup"><span data-stu-id="6c7f1-162">With the project fully setup for mixed reality, you're ready to move on to the next tutorial and start adding user input to the scene.</span></span> 

[<span data-ttu-id="6c7f1-163">下一節：4.使場景成為互動式場景</span><span class="sxs-lookup"><span data-stu-id="6c7f1-163">Next Section: 4. Making your scene interactive</span></span>](unreal-uxt-ch4.md)