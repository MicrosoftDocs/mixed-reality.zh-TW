---
title: 3. 設定您的專案以進行混合實境
description: 教學課程系列的第 3 部分 (共有 6 部分)，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置簡單的國際象棋應用程式
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件
ms.openlocfilehash: 105e817e54f7de12afdcab9fde1dfce0c38ff4a7
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376380"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a><span data-ttu-id="f2383-104">3.設定您的專案以進行混合實境</span><span class="sxs-lookup"><span data-stu-id="f2383-104">3. Setting up your project for mixed reality</span></span>

## <a name="overview"></a><span data-ttu-id="f2383-105">概觀</span><span class="sxs-lookup"><span data-stu-id="f2383-105">Overview</span></span>

<span data-ttu-id="f2383-106">在上一個教學課程中，您已花費時間設定國際象棋應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="f2383-106">In the previous tutorial, you spent time setting up the chess app project.</span></span> <span data-ttu-id="f2383-107">本節將逐步引導您設定應用程式以進行混合實境開發，這表示新增 AR 工作階段。</span><span class="sxs-lookup"><span data-stu-id="f2383-107">This section is going to walk you through setting up the app for mixed reality development, which means adding an AR session.</span></span> <span data-ttu-id="f2383-108">您將會針對此工作使用 ARSessionConfig 資料資產，其中有很多有用的 AR 設定，例如空間對應和遮蔽。</span><span class="sxs-lookup"><span data-stu-id="f2383-108">You'll be using an ARSessionConfig data asset for this task, which has a lot of useful AR settings like spatial mapping and occlusion.</span></span> <span data-ttu-id="f2383-109">如果您想要深入了解，Unreal Engine 文件有更多關於 [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) 資產和 [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) 類別的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="f2383-109">If you want to dive deeper, the Unreal Engine documentation has more details on the [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) asset and the [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) class.</span></span>

## <a name="objectives"></a><span data-ttu-id="f2383-110">目標</span><span class="sxs-lookup"><span data-stu-id="f2383-110">Objectives</span></span>
* <span data-ttu-id="f2383-111">使用 Unreal Engine 的 AR 設定</span><span class="sxs-lookup"><span data-stu-id="f2383-111">Working with Unreal Engine's AR settings</span></span> 
* <span data-ttu-id="f2383-112">使用 ARSessionConfig 資料資產</span><span class="sxs-lookup"><span data-stu-id="f2383-112">Using an ARSessionConfig data asset</span></span>
* <span data-ttu-id="f2383-113">設定 Pawn 和遊戲模式</span><span class="sxs-lookup"><span data-stu-id="f2383-113">Setting up a Pawn and game mode</span></span>

## <a name="adding-the-session-asset"></a><span data-ttu-id="f2383-114">新增工作階段資產</span><span class="sxs-lookup"><span data-stu-id="f2383-114">Adding the session asset</span></span>
<span data-ttu-id="f2383-115">Unreal 中的 AR 工作階段本身不會發生。</span><span class="sxs-lookup"><span data-stu-id="f2383-115">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="f2383-116">若要使用工作階段，您需有 ARSessionConfig 資料資產來使用，這是您的下一項工作：</span><span class="sxs-lookup"><span data-stu-id="f2383-116">To use a session you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="f2383-117">在 [內容瀏覽器] 中，按一下 [新增] > [其他] > [資料資產]。</span><span class="sxs-lookup"><span data-stu-id="f2383-117">Click **Add New > Miscellaneous > Data Asset** in the **Content Browser**.</span></span> <span data-ttu-id="f2383-118">確定您是在根**內容**資料夾層級。</span><span class="sxs-lookup"><span data-stu-id="f2383-118">Make sure you're at the root **Content** folder level.</span></span> 
    * <span data-ttu-id="f2383-119">選取 **ARSessionConfig**按一下 [選取]，然後將資產命名為 **ARSessionConfig**。</span><span class="sxs-lookup"><span data-stu-id="f2383-119">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**.</span></span>

![建立資料資產](images/unreal-uxt/3-createasset.PNG)

3. <span data-ttu-id="f2383-121">按兩下 **ARSessionConfig** 將其開啟、保留所有預設設定，然後點擊 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="f2383-121">Double-click **ARSessionConfig** to open it, leave all default settings and hit **Save**.</span></span> <span data-ttu-id="f2383-122">返回主視窗。</span><span class="sxs-lookup"><span data-stu-id="f2383-122">Return to the Main window.</span></span> 

![AR 工作階段設定](images/unreal-uxt/3-arsessionconfig.PNG)

<span data-ttu-id="f2383-124">完成後，您的下一個步驟是確保 AR 工作階段會在層級載入時啟動，並在層級結束時停止。</span><span class="sxs-lookup"><span data-stu-id="f2383-124">With that done, your next step is to make sure that the AR session starts when the level loads and stops when the level ends.</span></span> <span data-ttu-id="f2383-125">幸好，Unreal 具有特殊種類的藍圖，稱為**層級藍圖**，可作為整個層級的全域事件圖形。</span><span class="sxs-lookup"><span data-stu-id="f2383-125">Luckily, Unreal has a special kind of blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="f2383-126">在**層級藍圖**中連線 ARSessionConfig 資產，保證 AR 工作階段會在遊戲開始玩時立即啟動。</span><span class="sxs-lookup"><span data-stu-id="f2383-126">Connecting the ARSessionConfig asset in the **Level Blueprint** guarantees the AR session will fire right when the game starts playing.</span></span>

1. <span data-ttu-id="f2383-127">從編輯器工具列中按一下 [藍圖] > [開啟層級藍圖]：</span><span class="sxs-lookup"><span data-stu-id="f2383-127">Click **Blueprints > Open Level Blueprint** from the editor toolbar:</span></span> 

![開啟層級藍圖](images/unreal-uxt/3-level-blueprint.PNG)

5. <span data-ttu-id="f2383-129">拖曳 **Event BeginPlay** 的執行節點 (向左箭號圖示) 並放開。</span><span class="sxs-lookup"><span data-stu-id="f2383-129">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release.</span></span> <span data-ttu-id="f2383-130">搜尋 [啟動 AR 工作階段] 節點，然後按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="f2383-130">Search for the **Start AR Session** node and hit enter.</span></span>  
    * <span data-ttu-id="f2383-131">按一下 [工作階段組態] 底下的 [選取資產] 下拉式清單，然後選擇 **ARSessionConfig** 資產。</span><span class="sxs-lookup"><span data-stu-id="f2383-131">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset.</span></span> 

![啟動 AR 工作階段](images/unreal-uxt/3-start-ar-session.PNG)

6. <span data-ttu-id="f2383-133">以滑鼠右鍵按一下 EventGraph 中的任一處，並建立新的 [事件 EndPlay] 節點。</span><span class="sxs-lookup"><span data-stu-id="f2383-133">Right-click anywhere in the EventGraph and create a new **Event EndPlay** node.</span></span> <span data-ttu-id="f2383-134">拖放執行連接點。</span><span class="sxs-lookup"><span data-stu-id="f2383-134">Drag the execution pin and release.</span></span> <span data-ttu-id="f2383-135">搜尋 [停止 AR 工作階段] 節點，然後按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="f2383-135">Search for a **Stop AR Session** node and hit enter.</span></span> <span data-ttu-id="f2383-136">如果 AR 工作階段在層級結束時並未停止，若您在串流至頭戴式裝置時重新啟動應用程式，某些功能可能會停止運作。</span><span class="sxs-lookup"><span data-stu-id="f2383-136">If the AR session isn't stopped when the level ends, certain features may stop working if you restart your app while streaming to a headset.</span></span> 
    * <span data-ttu-id="f2383-137">依序點擊 [編譯]、[儲存]，然後返回主視窗。</span><span class="sxs-lookup"><span data-stu-id="f2383-137">Hit **Compile**, then **Save** and return to the Main window.</span></span>

![停止 AR 工作階段](images/unreal-uxt/3-stoparsession.PNG)

## <a name="create-a-pawn"></a><span data-ttu-id="f2383-139">建立 Pawn</span><span class="sxs-lookup"><span data-stu-id="f2383-139">Create a Pawn</span></span>
<span data-ttu-id="f2383-140">此時，專案仍然需要玩家物件。</span><span class="sxs-lookup"><span data-stu-id="f2383-140">At this point, the project still needs a player object.</span></span> <span data-ttu-id="f2383-141">在 Unreal 中，**Pawn** 代表遊戲中的使用者，或在此案例中，其將是 HoloLens 2 體驗。</span><span class="sxs-lookup"><span data-stu-id="f2383-141">In Unreal, a **Pawn** represents the user in the game, but in this case it's going to be the HoloLens 2 experience.</span></span>

1. <span data-ttu-id="f2383-142">在 [內容] 資料夾中按一下 [新增] > [藍圖類別]，然後展開底端的 [所有類別] 區段。</span><span class="sxs-lookup"><span data-stu-id="f2383-142">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span> 
    * <span data-ttu-id="f2383-143">搜尋 **DefaultPawn**，按一下 [選取]，將其命名為 **MRPawn**，然後按兩下要開啟的資產。</span><span class="sxs-lookup"><span data-stu-id="f2383-143">Search for **DefaultPawn**, click **Select**, name it **MRPawn**, and double-click the asset to open.</span></span> 

![建立繼承自 DefaultPawn 的新 Pawn](images/unreal-uxt/3-defaultpawn.PNG)

> [!NOTE]
> <span data-ttu-id="f2383-145">根據預設，Pawn 具有網格和碰撞元件。</span><span class="sxs-lookup"><span data-stu-id="f2383-145">By default, Pawns have mesh and collision components.</span></span> <span data-ttu-id="f2383-146">在大部分的 Unreal 專案中，Pawn 是可與其他元件碰撞的固體物件。</span><span class="sxs-lookup"><span data-stu-id="f2383-146">In most Unreal projects, Pawns are solid objects that can collide with other components.</span></span> <span data-ttu-id="f2383-147">由於 Pawn 和使用者在混合實境中是相同的，因此您希望能夠在不發生任何碰撞的情況下通過全像投影。</span><span class="sxs-lookup"><span data-stu-id="f2383-147">Since the Pawn and user are the same in mixed reality, you want to be able to pass through holograms without any collisions.</span></span> 

2. <span data-ttu-id="f2383-148">從 [元件] 面板中選取 **CollisionComponent**，然後向下捲動至 [詳細資料] 面板的 [碰撞] 區段。</span><span class="sxs-lookup"><span data-stu-id="f2383-148">Select **CollisionComponent** from the **Components** panel and scroll down to the **Collision** section of the **Details** panel.</span></span> 
    * <span data-ttu-id="f2383-149">按一下 [碰撞預設] 下拉式清單，然後將值變更為 **NoCollision**。</span><span class="sxs-lookup"><span data-stu-id="f2383-149">Click the **Collision Presets** dropdown and change the value to **NoCollision**.</span></span> 
    * <span data-ttu-id="f2383-150">針對 **MeshComponent** 執行相同的動作。</span><span class="sxs-lookup"><span data-stu-id="f2383-150">Do the same for the **MeshComponent**</span></span>

![調整 Pawn 的衝突預設值](images/unreal-uxt/3-nocollision.PNG)

3. <span data-ttu-id="f2383-152">從 [元件] 面板中按一下 [新增元件] > [相機]，並將其命名為 **Camera**。</span><span class="sxs-lookup"><span data-stu-id="f2383-152">Click **Add Component > Camera** from the **Components** panel and name it **Camera**.</span></span> <span data-ttu-id="f2383-153">這可讓播放器相機隨著 HoloLens 2 裝置一起移動。</span><span class="sxs-lookup"><span data-stu-id="f2383-153">This allows the player camera to move with the HoloLens 2 device.</span></span>

4. <span data-ttu-id="f2383-154">**編譯**和**儲存**藍圖。</span><span class="sxs-lookup"><span data-stu-id="f2383-154">**Compile** and **Save** the Blueprint.</span></span>

<span data-ttu-id="f2383-155">您在這裡的工作完成後，回到主視窗。</span><span class="sxs-lookup"><span data-stu-id="f2383-155">With your work here done, return to the Main Window.</span></span>

## <a name="create-a-game-mode"></a><span data-ttu-id="f2383-156">建立遊戲模式</span><span class="sxs-lookup"><span data-stu-id="f2383-156">Create a Game Mode</span></span>
<span data-ttu-id="f2383-157">混合實境設定的最後一塊拼圖是遊戲模式。</span><span class="sxs-lookup"><span data-stu-id="f2383-157">The last puzzle piece of the mixed reality setup is the Game Mode.</span></span> <span data-ttu-id="f2383-158">遊戲模式會決定遊戲或體驗的一些設定，包括要使用的預設 Pawn。</span><span class="sxs-lookup"><span data-stu-id="f2383-158">The Game Mode determines a number of settings for the game or experience, including the default pawn to use.</span></span>

1.  <span data-ttu-id="f2383-159">在 [內容] 資料夾中按一下 [新增] > [藍圖類別]，然後展開底端的 [所有類別] 區段。</span><span class="sxs-lookup"><span data-stu-id="f2383-159">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span> 
    * <span data-ttu-id="f2383-160">搜尋 [遊戲模式基底]、將其命名為 **MRGameMode**，然後按兩下來開啟。</span><span class="sxs-lookup"><span data-stu-id="f2383-160">Search for **Game Mode Base**, name it **MRGameMode** and double-click to open.</span></span> 

![內容瀏覽器中的 MRGameMode](images/unreal-uxt/3-gamemode.PNG)

2.  <span data-ttu-id="f2383-162">移至 [詳細資料] 面板中的 [類別] 區段，然後將 [預設 Pawn 類別] 變更為 **MRPawn**。</span><span class="sxs-lookup"><span data-stu-id="f2383-162">Go to the **Classes** section in the **Details** panel and change the **Default Pawn Class** to **MRPawn**.</span></span> 
    * <span data-ttu-id="f2383-163">依序點擊 [編譯]、[儲存]，然後返回主視窗。</span><span class="sxs-lookup"><span data-stu-id="f2383-163">Hit **Compile**, then **Save** and return to the Main window.</span></span> 

![設定預設的 Pawn 類別](images/unreal-uxt/3-setpawn.PNG)

3.  <span data-ttu-id="f2383-165">選取 [編輯] > [專案設定]，然後按一下左側清單中的 [地圖與模式]。</span><span class="sxs-lookup"><span data-stu-id="f2383-165">Select **Edit > Projects Settings** and click **Maps & Modes** in the left-hand list.</span></span> 
    * <span data-ttu-id="f2383-166">展開 [預設模式]，然後將 [預設遊戲模式] 變更為 **MRGameMode**。</span><span class="sxs-lookup"><span data-stu-id="f2383-166">Expand **Default Modes** and change **Default Game Mode** to **MRGameMode**.</span></span> 
    * <span data-ttu-id="f2383-167">展開 [預設地圖]，然後同時將 **EditorStartupMap** 和 **GameDefaultMap** 變更為 **Main**。</span><span class="sxs-lookup"><span data-stu-id="f2383-167">Expand **Default Maps** and change both **EditorStartupMap** and **GameDefaultMap** to **Main**.</span></span> <span data-ttu-id="f2383-168">如此一來，當您關閉編輯器並重新開啟時，系統會預設為選取主要地圖。</span><span class="sxs-lookup"><span data-stu-id="f2383-168">This way when you close and reopen the editor, or play the game, the Main map will be selected by default.</span></span>

![專案設定 - 地圖與模式](images/unreal-uxt/3-mapsandmodes.PNG)

<span data-ttu-id="f2383-170">在混合實境的專案完全設定好之後，您就可以繼續進行下一個教學課程，並開始將使用者輸入新增到場景。</span><span class="sxs-lookup"><span data-stu-id="f2383-170">With the project fully setup for mixed reality, you're ready to move on to the next tutorial and start adding user input to the scene.</span></span> 

[<span data-ttu-id="f2383-171">下一節：4.使場景成為互動式場景</span><span class="sxs-lookup"><span data-stu-id="f2383-171">Next Section: 4. Making your scene interactive</span></span>](unreal-uxt-ch4.md)