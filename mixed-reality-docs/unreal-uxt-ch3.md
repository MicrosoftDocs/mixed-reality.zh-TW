---
title: 3. 設定您的專案以進行混合實境
description: 教學課程的第 3 部分，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置簡單的國際象棋應用程式
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件
ms.openlocfilehash: b5b5e2de787279602341e60f2bfa29aa05ea9b31
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840617"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a><span data-ttu-id="8f081-104">3.設定您的專案以進行混合實境</span><span class="sxs-lookup"><span data-stu-id="8f081-104">3. Setting up your project for mixed reality</span></span>

<span data-ttu-id="8f081-105">本節將逐步引導您完成設定應用程式以進行混合現實開發的程序。</span><span class="sxs-lookup"><span data-stu-id="8f081-105">This section walks you through the process of configuring your app for mixed reality development.</span></span> 

## <a name="objectives"></a><span data-ttu-id="8f081-106">目標</span><span class="sxs-lookup"><span data-stu-id="8f081-106">Objectives</span></span>

* <span data-ttu-id="8f081-107">了解如何使用 ARSessionConfig、Pawn 和 GameMode 來設定混合實境專案</span><span class="sxs-lookup"><span data-stu-id="8f081-107">Understand how to set up a mixed reality project with ARSessionConfig, Pawn, and GameMode</span></span>

## <a name="configure-the-session"></a><span data-ttu-id="8f081-108">設定工作階段</span><span class="sxs-lookup"><span data-stu-id="8f081-108">Configure the Session</span></span>

1. <span data-ttu-id="8f081-109">在內容瀏覽器中，往回瀏覽到 [內容]  資料夾。</span><span class="sxs-lookup"><span data-stu-id="8f081-109">In the Content Browser, navigate back to the **Content** folder.</span></span> <span data-ttu-id="8f081-110">按一下 [新增] > [其他] > [資料資產]  。</span><span class="sxs-lookup"><span data-stu-id="8f081-110">Click **Add New > Miscellaneous > Data Asset**.</span></span> 

2. <span data-ttu-id="8f081-111">挑選 **ARSessionConfig** 作為類別，然後按一下 [選取]  。</span><span class="sxs-lookup"><span data-stu-id="8f081-111">Pick **ARSessionConfig** as the class and click **Select**.</span></span> <span data-ttu-id="8f081-112">將資產命名為 "ARSessionConfig"。</span><span class="sxs-lookup"><span data-stu-id="8f081-112">Name the asset “ARSessionConfig”.</span></span>

![建立資料資產](images/unreal-uxt/3-createasset.PNG)

3. <span data-ttu-id="8f081-114">按兩下 [ARSessionConfig] 以將其開啟。</span><span class="sxs-lookup"><span data-stu-id="8f081-114">Double click ARSessionConfig to open it.</span></span> <span data-ttu-id="8f081-115">ARSessionConfig 資料資產包含一些實用的 AR 設定，包括空間對應和遮蔽。</span><span class="sxs-lookup"><span data-stu-id="8f081-115">An ARSessionConfig data asset contains a number of useful AR settings including spatial mapping and occlusion.</span></span> <span data-ttu-id="8f081-116">如需有關 ARSessionConfig 的詳細資訊，請參閱有關 [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) 的 Unreal 引擎文件。</span><span class="sxs-lookup"><span data-stu-id="8f081-116">For more details on ARSessionConfig, take a look at Unreal Engine’s documentation on [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html).</span></span> <span data-ttu-id="8f081-117">針對我們的國際象棋應用程式，我們不需要修改任何設定，只要按 [儲存]  並返回主視窗即可。</span><span class="sxs-lookup"><span data-stu-id="8f081-117">For our chess app, we won’t need to modify any settings, so just hit **Save** and return to the Main window.</span></span> 

![AR 工作階段設定](images/unreal-uxt/3-arsessionconfig.PNG)

4. <span data-ttu-id="8f081-119">在檢視區上方的工具列上，按一下 [藍圖] > [開啟層級藍圖]  。</span><span class="sxs-lookup"><span data-stu-id="8f081-119">On the toolbar above the viewport, click **Blueprints > Open Level Blueprint**.</span></span> <span data-ttu-id="8f081-120">層級藍圖是特殊的藍圖，可作為整個層級的全域事件圖表。</span><span class="sxs-lookup"><span data-stu-id="8f081-120">The Level Blueprint is a special Blueprint that acts as a level-wide global event graph.</span></span> <span data-ttu-id="8f081-121">我們即將在此啟動 AR 工作階段，讓 AR 工作階段設定在層級開始時就加以套用。</span><span class="sxs-lookup"><span data-stu-id="8f081-121">We’re going to start an AR session here, so that our AR session configuration is applied at the start of the level.</span></span>  

5. <span data-ttu-id="8f081-122">拖曳 **Event BeginPlay** 的執行節點並放開。</span><span class="sxs-lookup"><span data-stu-id="8f081-122">Drag the execution node off **Event BeginPlay** and release.</span></span> <span data-ttu-id="8f081-123">搜尋 [啟動 AR 工作階段]  節點。</span><span class="sxs-lookup"><span data-stu-id="8f081-123">Search for the **Start AR Session** node.</span></span> <span data-ttu-id="8f081-124">按一下 [工作階段]  ，然後選取您新建立的 **ARSessionConfig** 資產。</span><span class="sxs-lookup"><span data-stu-id="8f081-124">Click on **Session Config** and select your newly created **ARSessionConfig** asset.</span></span> <span data-ttu-id="8f081-125">點擊 [編譯]  和 [儲存]  。</span><span class="sxs-lookup"><span data-stu-id="8f081-125">Hit **Compile**, then **Save**.</span></span> <span data-ttu-id="8f081-126">返回主視窗。</span><span class="sxs-lookup"><span data-stu-id="8f081-126">Return to the Main window.</span></span>

![啟動 AR 工作階段](images/unreal-uxt/3-startarsession.PNG)

## <a name="create-a-pawn"></a><span data-ttu-id="8f081-128">建立 Pawn</span><span class="sxs-lookup"><span data-stu-id="8f081-128">Create a Pawn</span></span>

1.  <span data-ttu-id="8f081-129">在 [內容] 資料夾中，建立繼承自 **DefaultPawn** 的新藍圖。</span><span class="sxs-lookup"><span data-stu-id="8f081-129">In the Content folder, create a new Blueprint that inherits from **DefaultPawn**.</span></span> <span data-ttu-id="8f081-130">在 Unreal 中，Pawn 代表遊戲中的使用者，或在此案例中是 HoloLens 2 體驗。</span><span class="sxs-lookup"><span data-stu-id="8f081-130">In Unreal, a Pawn represents the user in the game, or in this case, the HoloLens 2 experience.</span></span> <span data-ttu-id="8f081-131">將新的 Pawn 重新命名為 "MRPawn"，然後按兩下 MRPawn 來將其開啟。</span><span class="sxs-lookup"><span data-stu-id="8f081-131">Rename your new Pawn “MRPawn” and double click on MRPawn to open it.</span></span> 

![建立繼承自 DefaultPawn 的新 Pawn](images/unreal-uxt/3-defaultpawn.PNG)

2.  <span data-ttu-id="8f081-133">根據預設，Pawn 具有網格元件和衝突元件，因為在大部分的 Unreal 專案中，由使用者控制的 Pawn 是會與其他元件衝突的穩固物件。</span><span class="sxs-lookup"><span data-stu-id="8f081-133">By default, the Pawn has a mesh component and a collision component, since in most Unreal projects, Pawns controlled by the user are solid objects that collides with other components.</span></span> <span data-ttu-id="8f081-134">在這種情況下，由於使用者是 Pawn，所以我們想要能夠通過全像投影，而不會產生衝突。</span><span class="sxs-lookup"><span data-stu-id="8f081-134">In this situation, since the user is the Pawn, we want to be able to pass through holograms without generating collisions.</span></span> <span data-ttu-id="8f081-135">在 [元件] 面板中，選取 [CollisionComponent]  。</span><span class="sxs-lookup"><span data-stu-id="8f081-135">In the Components panel, select the **CollisionComponent**.</span></span> <span data-ttu-id="8f081-136">在 [詳細資料] 面板中，向下捲動至 [衝突] 區段，然後按一下 [衝突預設] 旁的下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="8f081-136">In the Details panel, scroll down to the Collision section and click the dropdown next to Collision Presets.</span></span> <span data-ttu-id="8f081-137">將此設定從 Pawn 變更為 **NoCollision**。</span><span class="sxs-lookup"><span data-stu-id="8f081-137">Change this from Pawn to **NoCollision**.</span></span> <span data-ttu-id="8f081-138">針對 **MeshComponent** 執行相同的動作。</span><span class="sxs-lookup"><span data-stu-id="8f081-138">Do the same for the **MeshComponent**.</span></span> <span data-ttu-id="8f081-139">**編譯**並**儲存**藍圖。</span><span class="sxs-lookup"><span data-stu-id="8f081-139">**Compile**, then **Save** the Blueprint.</span></span> <span data-ttu-id="8f081-140">返回主視窗。</span><span class="sxs-lookup"><span data-stu-id="8f081-140">Return to the Main window.</span></span> 

![調整 Pawn 的衝突預設值](images/unreal-uxt/3-nocollision.PNG)

## <a name="create-a-game-mode"></a><span data-ttu-id="8f081-142">建立遊戲模式</span><span class="sxs-lookup"><span data-stu-id="8f081-142">Create a Game Mode</span></span>

1.  <span data-ttu-id="8f081-143">在內容瀏覽器的 [內容] 資料夾中，建立具有父系**遊戲模式基底**的新藍圖。</span><span class="sxs-lookup"><span data-stu-id="8f081-143">In the Content folder in the Content Browser, create a new Blueprint with the parent **Game Mode Base**.</span></span> <span data-ttu-id="8f081-144">將其命名為 MRGameMode，然後按兩下來開啟。</span><span class="sxs-lookup"><span data-stu-id="8f081-144">Name it MRGameMode and double click to open.</span></span> <span data-ttu-id="8f081-145">在 Unreal 中，遊戲模式會決定遊戲或體驗的一些設定，包括要使用的預設 Pawn。</span><span class="sxs-lookup"><span data-stu-id="8f081-145">In Unreal, the Game Mode determines a number of settings for the game or experience, including the default pawn to use.</span></span> 

![內容瀏覽器中的 MRGameMode](images/unreal-uxt/3-gamemode.PNG)

2.  <span data-ttu-id="8f081-147">在 [詳細資料] 面板中，找出 [類別] 區段。</span><span class="sxs-lookup"><span data-stu-id="8f081-147">In the Details panel, locate the Classes section.</span></span> <span data-ttu-id="8f081-148">將預設的 Pawn 類別從 DefaultPawn 變更為您剛才建立的 **MRPawn**。</span><span class="sxs-lookup"><span data-stu-id="8f081-148">Change the Default Pawn Class from DefaultPawn to the **MRPawn** you just created.</span></span> <span data-ttu-id="8f081-149">點擊 [編譯]  和 [儲存]  。</span><span class="sxs-lookup"><span data-stu-id="8f081-149">Hit **Compile**, then **Save**.</span></span> <span data-ttu-id="8f081-150">返回主視窗。</span><span class="sxs-lookup"><span data-stu-id="8f081-150">Return to the Main window.</span></span> 

![設定預設的 Pawn 類別](images/unreal-uxt/3-setpawn.PNG)

3.  <span data-ttu-id="8f081-152">設定專案的最後一個步驟是告訴 Unreal 預設為 MRGameMode。</span><span class="sxs-lookup"><span data-stu-id="8f081-152">The last step in setting up your project is to tell Unreal to default to MRGameMode.</span></span> <span data-ttu-id="8f081-153">移至 [編輯] > [專案設定] > [地圖與模式] (在專案中)  區段。</span><span class="sxs-lookup"><span data-stu-id="8f081-153">Go to **Edit > Projects Settings > Maps & Modes** (in the Projects) section.</span></span> <span data-ttu-id="8f081-154">在 [預設模式] 區段中，按一下下拉式清單，然後選擇 [MRGameMode]  。</span><span class="sxs-lookup"><span data-stu-id="8f081-154">In the Default Modes section, click the dropdown and choose **MRGameMode**.</span></span> <span data-ttu-id="8f081-155">在下方的 [預設地圖] 區段中，將 [EditorStartupMap]  和 [GameDefaultMap]  變更為 [主要]  。</span><span class="sxs-lookup"><span data-stu-id="8f081-155">In the Default Maps section right below, change both the **EditorStartupMap** and the **GameDefaultMap** to **Main**.</span></span> <span data-ttu-id="8f081-156">如此一來，當您關閉編輯器並重新開啟時，系統會預設為選取主要地圖。</span><span class="sxs-lookup"><span data-stu-id="8f081-156">This way when you close the editor and reopen it, the Main map will be selected by default.</span></span> <span data-ttu-id="8f081-157">同樣地，當您開始遊戲時，主要地圖會是啟動的層級。</span><span class="sxs-lookup"><span data-stu-id="8f081-157">Similarly, when you play the game, the Main map will be the level that is started.</span></span> 

![專案設定 - 地圖與模式](images/unreal-uxt/3-mapsandmodes.PNG)

[<span data-ttu-id="8f081-159">下一節：4.使場景成為互動式場景</span><span class="sxs-lookup"><span data-stu-id="8f081-159">Next Section: 4. Making your scene interactive</span></span>](unreal-uxt-ch4.md)