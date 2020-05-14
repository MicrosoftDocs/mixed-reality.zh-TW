---
title: 2. 初始化您的專案和第一個應用程式
description: 教學課程的第 2 部分，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置簡單的國際象棋應用程式
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件
ms.openlocfilehash: fc85f011ff3b186f3b4b5449b4f8ec49f0b6418f
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851572"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="f4751-104">2.初始化您的專案和第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="f4751-104">2. Initializing your project and first application</span></span>

<span data-ttu-id="f4751-105">本節將引導您開始為 HoloLens 2 建立新的 Unreal 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f4751-105">This section gets you started with creating a new Unreal application for HoloLens 2.</span></span> 

## <a name="objectives"></a><span data-ttu-id="f4751-106">目標</span><span class="sxs-lookup"><span data-stu-id="f4751-106">Objectives</span></span>

* <span data-ttu-id="f4751-107">設定 Unreal 以用於 HoloLens 開發</span><span class="sxs-lookup"><span data-stu-id="f4751-107">Configure Unreal for HoloLens development</span></span>
* <span data-ttu-id="f4751-108">匯入資產並設定場景</span><span class="sxs-lookup"><span data-stu-id="f4751-108">Import assets and set up the scene</span></span>

## <a name="create-a-new-unreal-project"></a><span data-ttu-id="f4751-109">建立新的 Unreal 專案</span><span class="sxs-lookup"><span data-stu-id="f4751-109">Create a new Unreal project</span></span>

1. <span data-ttu-id="f4751-110">啟動 Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="f4751-110">Launch Unreal Engine</span></span>

2. <span data-ttu-id="f4751-111">在 [新增專案類別]  底下選取 [遊戲]  ，然後按 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="f4751-111">Under **New Project Categories**, select **Games** and click Next.</span></span> <span data-ttu-id="f4751-112">選取**空白**範本，然後按 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="f4751-112">Select a **Blank** Template and click Next.</span></span> 

![選取空白範本](images/unreal-uxt/2-template.PNG)

3. <span data-ttu-id="f4751-114">在 [專案設定] 中，選擇 [C++]、[可縮放 3D 或 2D]、[行動裝置/平板電腦]  及 [無起始內容]  。</span><span class="sxs-lookup"><span data-stu-id="f4751-114">In Project Settings, choose **C++, Scalable 3D or 2D, Mobile / Tablet**, and **No Starter Content**.</span></span> <span data-ttu-id="f4751-115">選取要儲存專案的位置，然後按一下 [建立專案]  。</span><span class="sxs-lookup"><span data-stu-id="f4751-115">Select a location for your project to be saved and click **Create Project**.</span></span> <span data-ttu-id="f4751-116">這會在 Visual Studio 專案和 Unreal 編輯器中開啟您的 C++ 檔案。</span><span class="sxs-lookup"><span data-stu-id="f4751-116">This will open up your C++ files in a Visual Studio project and the Unreal editor.</span></span> 

![初始專案設定](images/unreal-uxt/2-project-settings.PNG)

4. <span data-ttu-id="f4751-118">移至左上角的 [編輯] > [外掛程式]  。</span><span class="sxs-lookup"><span data-stu-id="f4751-118">In the top left-hand corner, go to **Edit > Plugins**.</span></span> <span data-ttu-id="f4751-119">在 [擴增實境] 底下，核取 **HoloLens** 外掛程式的啟用方塊。</span><span class="sxs-lookup"><span data-stu-id="f4751-119">Under Augmented Reality, check the box to enable the **HoloLens** plugin.</span></span> <span data-ttu-id="f4751-120">向下捲動至 [虛擬實境] 區段，核取 **Microsoft Windows Mixed Reality** 外掛程式的啟用方塊。</span><span class="sxs-lookup"><span data-stu-id="f4751-120">Scroll down to the Virtual Reality section and check the box to enable the **Microsoft Windows Mixed Reality** plugin.</span></span> <span data-ttu-id="f4751-121">這兩個外掛程式都是進行 HoloLens 2 開發的必要項目。</span><span class="sxs-lookup"><span data-stu-id="f4751-121">Both plugins are required for HoloLens 2 development.</span></span> <span data-ttu-id="f4751-122">重新啟動您的編輯器。</span><span class="sxs-lookup"><span data-stu-id="f4751-122">Restart your editor.</span></span> 

![外掛程式](images/unreal-uxt/2-plugins.PNG)

5. <span data-ttu-id="f4751-124">移至左上角的 [檔案] > [新增層級]  。</span><span class="sxs-lookup"><span data-stu-id="f4751-124">In the top left-hand corner, go to **File > New Level**.</span></span> <span data-ttu-id="f4751-125">選取 [空白層級]  。</span><span class="sxs-lookup"><span data-stu-id="f4751-125">Select **Empty Level**.</span></span> <span data-ttu-id="f4751-126">檢視區中的預設場景現在應該是空白的。</span><span class="sxs-lookup"><span data-stu-id="f4751-126">The default scene in the viewport should now be empty.</span></span>

6. <span data-ttu-id="f4751-127">從左側 [模式] 面板的 [基本] 索引標籤中，拖曳並放置 [PlayerStart]。在右邊的 [詳細資料] 面板中，將 [位置] 設定為 X = 0、Y = 0、Z = 0，以便讓使用者位在應用程式啟動時的原始位置開始作業。</span><span class="sxs-lookup"><span data-stu-id="f4751-127">Drag PlayerStart and drop PlayerStart from the Modes panel on the left, located in the Basic tab. In the Details panel on the right, set the location to X = 0, Y = 0, Z = 0 in order to have the user start at the origin when the app stars.</span></span>

![具有 PlayerStart 的檢視區](images/unreal-uxt/2-playerstart.PNG)

7. <span data-ttu-id="f4751-129">將 [立方體]  從 [模式] 面板的 [基本] 索引標籤拖曳至檢視區。</span><span class="sxs-lookup"><span data-stu-id="f4751-129">Drag a **Cube** from the Basic tab of the Modes panel into the viewport.</span></span> <span data-ttu-id="f4751-130">在 [詳細資料] 面板中，將 [位置] 設定為 X = 50、Y = 0、Z = 0，以在開始時將立方體設定為距離播放器 50 公分的位置。</span><span class="sxs-lookup"><span data-stu-id="f4751-130">In the Details panel, set the location to X = 50, Y = 0, Z = 0 to set the cube to 50 cm away from the player at start time.</span></span> <span data-ttu-id="f4751-131">由於預設的立方體相當大，請將立方體的縮放變更為 (0.2, 0.2, 0.2)。</span><span class="sxs-lookup"><span data-stu-id="f4751-131">Since the default cube is quite large, change the Scale of the cube to (0.2, 0.2, 0.2).</span></span> 

8. <span data-ttu-id="f4751-132">除非您將光線新增至場景，否則無法看到立方體。</span><span class="sxs-lookup"><span data-stu-id="f4751-132">You won’t be able to see the cube unless you add a light to your scene.</span></span> <span data-ttu-id="f4751-133">切換至 [模式] 面板上的 [光線]  索引標籤，然後將 [定向光線]  拖曳到場景中的 PlayerStart 上方。</span><span class="sxs-lookup"><span data-stu-id="f4751-133">Switch to the **Lights** tab on the Modes panel and drag a **Directional Light** into the scene, above the PlayerStart.</span></span>

![已新增光線的檢視區](images/unreal-uxt/2-light.PNG)

9.  <span data-ttu-id="f4751-135">按下工具列上的 [播放]  按鈕，即可在您的檢視區中查看您的立方體！</span><span class="sxs-lookup"><span data-stu-id="f4751-135">Press the **Play** button on the toolbar to see your cube in the viewport!</span></span> <span data-ttu-id="f4751-136">按 **Esc** 即可停止該層級。</span><span class="sxs-lookup"><span data-stu-id="f4751-136">Press **Esc** to stop the level.</span></span> 

![檢視區中的立方體](images/unreal-uxt/2-cube.PNG)

10. <span data-ttu-id="f4751-138">接著來儲存您的層級。</span><span class="sxs-lookup"><span data-stu-id="f4751-138">Let’s save your level.</span></span> <span data-ttu-id="f4751-139">從左上角按一下 [檔案] > [儲存目前項目]  。</span><span class="sxs-lookup"><span data-stu-id="f4751-139">In the top left corner, click on **File > Save Current**.</span></span> <span data-ttu-id="f4751-140">將您的層級命名為 "Main"，然後按一下 [儲存]  。</span><span class="sxs-lookup"><span data-stu-id="f4751-140">Name your level "Main" and click **Save**.</span></span> 

## <a name="set-up-a-chess-scene"></a><span data-ttu-id="f4751-141">設定國際象棋場景</span><span class="sxs-lookup"><span data-stu-id="f4751-141">Set up a chess scene</span></span>

1. <span data-ttu-id="f4751-142">在內容瀏覽器中，按一下 [新增] 底下的圖示來顯示來源面板。</span><span class="sxs-lookup"><span data-stu-id="f4751-142">In your Content Browser, click icon under Add New to show the sources panel.</span></span> <span data-ttu-id="f4751-143">然後按一下 [新增] > [新增資料夾]  ，並將資料夾命名為 "ChessAssets"。</span><span class="sxs-lookup"><span data-stu-id="f4751-143">Then click on **Add New > New Folder** and name the folder “ChessAssets”.</span></span> <span data-ttu-id="f4751-144">按兩下此資料夾以在其中進行瀏覽。</span><span class="sxs-lookup"><span data-stu-id="f4751-144">Double-click this folder to navigate in.</span></span> <span data-ttu-id="f4751-145">我們將在其中匯入國際象棋的 3D 資產。</span><span class="sxs-lookup"><span data-stu-id="f4751-145">This is where we’ll import the 3D assets for our chess set.</span></span>

![顯示或隱藏來源面板](images/unreal-uxt/2-showhidesources.PNG)

2. <span data-ttu-id="f4751-147">從 [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) 下載資產的 zip 檔案。</span><span class="sxs-lookup"><span data-stu-id="f4751-147">Download the zip file of assets from [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z).</span></span> <span data-ttu-id="f4751-148">此檔案包含適用於棋盤和一套國際象棋的 3D 模型。</span><span class="sxs-lookup"><span data-stu-id="f4751-148">This file contains the 3D models for a chess board and chess set.</span></span> <span data-ttu-id="f4751-149">將此檔案解壓縮。</span><span class="sxs-lookup"><span data-stu-id="f4751-149">Unzip this file.</span></span>

3. <span data-ttu-id="f4751-150">在內容瀏覽器的頂端，按一下 [匯入]  。</span><span class="sxs-lookup"><span data-stu-id="f4751-150">At the top of the Content Browser, click on **Import**.</span></span> <span data-ttu-id="f4751-151">瀏覽至您剛才解壓縮的資料夾，然後選取其中所有項目。</span><span class="sxs-lookup"><span data-stu-id="f4751-151">Navigate to the folder that you just unzipped and select all the items within.</span></span> <span data-ttu-id="f4751-152">此資料夾包含 FBX 檔案，也就是棋盤和棋子的 3D 物件網格，以及 TGA 檔案，將用來為棋盤和棋子建立材質的紋理貼圖。</span><span class="sxs-lookup"><span data-stu-id="f4751-152">This folder contains FBX files which are the 3D object meshes for our chess board and pieces, as well as TGA files which are the texture maps we’ll use to create materials for our board and pieces.</span></span> <span data-ttu-id="f4751-153">按一下 [開啟]  。</span><span class="sxs-lookup"><span data-stu-id="f4751-153">Click **Open**.</span></span> 

4. <span data-ttu-id="f4751-154">FBX 匯入選項視窗會隨即出現。</span><span class="sxs-lookup"><span data-stu-id="f4751-154">An FBX Import Options window will pop up.</span></span> <span data-ttu-id="f4751-155">在 [材質]  區段中，將 [材質匯入方法]  變更為 [不要建立材質]  。</span><span class="sxs-lookup"><span data-stu-id="f4751-155">In the **Material** section, change the **Material Import Method** to **Do Not Create Material**.</span></span> <span data-ttu-id="f4751-156">然後，按一下 [全部匯入]  。</span><span class="sxs-lookup"><span data-stu-id="f4751-156">Then, click **Import All**.</span></span>

![匯入 FBX 選項](images/unreal-uxt/2-nocreatemat.PNG)

5. <span data-ttu-id="f4751-158">回到 [內容] 資料夾，建立名為 **Blueprints** 的新資料夾。</span><span class="sxs-lookup"><span data-stu-id="f4751-158">Back in your Content folder, create a new folder called **Blueprints**.</span></span> <span data-ttu-id="f4751-159">我們將在此儲存所有藍圖，這些藍圖是特殊資產，可提供以節點為基礎的介面來建立新的動作項目類型和指令碼層級事件。</span><span class="sxs-lookup"><span data-stu-id="f4751-159">This is where we will store all our blueprints, which are special assets that provide a node-based interface to create new types of Actors and script level events.</span></span> 

6. <span data-ttu-id="f4751-160">按兩下 **Blueprints** 資料夾以在其中進行瀏覽，然後在內容瀏覽器中按一下滑鼠右鍵，並選取 [藍圖類別]  。</span><span class="sxs-lookup"><span data-stu-id="f4751-160">Double click the **Blueprints** folder to navigate inside, then right click in your Content Browser and select **Blueprint Class**.</span></span> <span data-ttu-id="f4751-161">按一下 [動作項目]  ，並將新藍圖命名為 “Board” (棋盤)。</span><span class="sxs-lookup"><span data-stu-id="f4751-161">Click on **Actor** and name the new blueprint “Board”.</span></span> <span data-ttu-id="f4751-162">按兩下 [Board] 來將其開啟。</span><span class="sxs-lookup"><span data-stu-id="f4751-162">Double click Board to open it.</span></span> 

![選取您藍圖的父類別](images/unreal-uxt/2-bpparent.PNG)

![新的棋盤藍圖](images/unreal-uxt/2-bpboard.PNG)

7. <span data-ttu-id="f4751-165">在藍圖編輯器中，瀏覽至 [元件] 面板，然後按一下 [新增元件] > [場景]  。</span><span class="sxs-lookup"><span data-stu-id="f4751-165">In the Blueprint editor, navigate to the Components panel and click **Add Component > Scene**.</span></span> <span data-ttu-id="f4751-166">將新建立的場景命名為 “Root”，然後按一下 Root 並將其拖曳到 DefaultSceneRoot 上方。</span><span class="sxs-lookup"><span data-stu-id="f4751-166">Name the newly created scene “Root”, and then click and drag Root over the DefaultSceneRoot.</span></span> <span data-ttu-id="f4751-167">這會取代預設場景的根項目，並清除檢視區中的球體。</span><span class="sxs-lookup"><span data-stu-id="f4751-167">This will replace the default scene root and get rid of the sphere in the viewport.</span></span> 

![取代根項目](images/unreal-uxt/2-root.PNG)

8. <span data-ttu-id="f4751-169">再次按一下 [新增元件]  ，這次請選擇 [靜態網格]  。</span><span class="sxs-lookup"><span data-stu-id="f4751-169">Click **Add Component** again, and this time choose **Static Mesh**.</span></span> <span data-ttu-id="f4751-170">將新的靜態網格命名為 “SM_Board”。</span><span class="sxs-lookup"><span data-stu-id="f4751-170">Name the new static mesh “SM_Board”.</span></span> 

![新增靜態網格](images/unreal-uxt/2-sm-board.PNG)

9. <span data-ttu-id="f4751-172">在 [詳細資料]  面板中，找出 [靜態網格]  區段，然後按一下下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="f4751-172">In the **Details** panel, locate the **Static Mesh** section and click the dropdown.</span></span> <span data-ttu-id="f4751-173">選取 [ChessBoard]  。</span><span class="sxs-lookup"><span data-stu-id="f4751-173">Select **ChessBoard**.</span></span> 

![檢視區中的棋盤網格](images/unreal-uxt/2-sm-board-view.PNG)

10. <span data-ttu-id="f4751-175">繼續在 [詳細資料]  面板中，找出 [材質]  區段，然後按一下下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="f4751-175">Still in the **Details** panel, locate the **Materials** section and click the dropdown.</span></span> <span data-ttu-id="f4751-176">在 [建立新資產]  中，選取 [材質]  。</span><span class="sxs-lookup"><span data-stu-id="f4751-176">Under **Create New Asset**, select **Material**.</span></span> <span data-ttu-id="f4751-177">將此資產命名 **M_ChessBoard**，並將其儲存在 **ChessAssets** 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="f4751-177">Name this asset **M_ChessBoard** and save it in the **ChessAssets** folder.</span></span> 

![建立新的材質](images/unreal-uxt/2-newmat.PNG)

11. <span data-ttu-id="f4751-179">按兩下 M_ChessBoard 下拉式清單旁的方塊，開啟您新建立的 M_ChessBoard 材質。</span><span class="sxs-lookup"><span data-stu-id="f4751-179">Double click the square next to M_ChessBoard dropdown to open your newly created M_ChessBoard material.</span></span> <span data-ttu-id="f4751-180">在材質編輯器中，以滑鼠右鍵按一下，然後搜尋**紋理範例**節點。</span><span class="sxs-lookup"><span data-stu-id="f4751-180">In the Material Editor, right click and search for the **Texture Sample** node.</span></span> <span data-ttu-id="f4751-181">在 [材質呈現紋理基底]  區段底下的 [詳細資料]  面板中，按一下下拉式清單，然後選取 [ChessBoard_Albedo]  。</span><span class="sxs-lookup"><span data-stu-id="f4751-181">In the **Details** panel under the **Material Expression Texture Base** section, click the dropdown and select **ChessBoard_Albedo**.</span></span> <span data-ttu-id="f4751-182">最後，將 **RGB** 輸出連接拖曳到 **M_ChessBoard** 的「基本色彩」輸出連接。</span><span class="sxs-lookup"><span data-stu-id="f4751-182">Finally, drag the **RGB** output pin to the Base Color pin of **M_ChessBoard**.</span></span> 

![設定基本色彩](images/unreal-uxt/2-boardalbedomat.PNG)

12. <span data-ttu-id="f4751-184">再執行四次同樣的動作，將 **ChessBoard_AO** 紋理範例連結至**環境光遮蔽**連接點、將 **ChessBoard_Metal** 材質範例連接至**金屬**連接點，將 **ChessBoard_Normal** 紋理範例連接至**法線**連接點，以及將 **ChessBoard_Rough** 材質範例連接到**粗糙度**。</span><span class="sxs-lookup"><span data-stu-id="f4751-184">Do the same four more times, linking the **ChessBoard_AO** Texture Sample to the **Ambient Occlusion** pin, the **ChessBoard_Metal** Texture Sample to the **Metallic** pin, the **ChessBoard_Normal** Texture Sample to the **Normal** pin, and the **ChessBoard_Rough** Texture Sample to the **Roughness** pin.</span></span> <span data-ttu-id="f4751-185">按一下 **[儲存]** 。</span><span class="sxs-lookup"><span data-stu-id="f4751-185">Click **Save**.</span></span> 

![連結其餘紋理](images/unreal-uxt/2-boardmat.PNG)

13. <span data-ttu-id="f4751-187">返回您的 **Board** 藍圖。</span><span class="sxs-lookup"><span data-stu-id="f4751-187">Return to your **Board** Blueprint.</span></span> <span data-ttu-id="f4751-188">您應該會看到您剛建立的材質已套用至藍圖。</span><span class="sxs-lookup"><span data-stu-id="f4751-188">You should see that the material you just created has been applied to your Blueprint.</span></span> <span data-ttu-id="f4751-189">為了確保棋盤的大小和位置適合放在場景中，請將棋盤的**縮放**變更為 (0.05, 0.05, 0.05) ，並將**旋轉**變更為 Z = 90。</span><span class="sxs-lookup"><span data-stu-id="f4751-189">To ensure the board is at a reasonable size and position once we place it in our scene, change the **Scale** of the board to (0.05, 0.05, 0.05) and the **Rotation** to Z = 90.</span></span> <span data-ttu-id="f4751-190">在頂端的工具列中，按一下 [編譯]  ，然後**儲存**。</span><span class="sxs-lookup"><span data-stu-id="f4751-190">In the toolbar at the top, click **Compile**, then **Save**.</span></span> <span data-ttu-id="f4751-191">返回您的主視窗。</span><span class="sxs-lookup"><span data-stu-id="f4751-191">Return to your Main window.</span></span> 

![已套用材質的棋盤](images/unreal-uxt/2-chessboard.PNG)

14. <span data-ttu-id="f4751-193">現在我們要刪除立方體，並將其取代為新建立的棋盤動作項目。</span><span class="sxs-lookup"><span data-stu-id="f4751-193">Let’s now delete the cube and replace it with your newly created Board actor.</span></span> <span data-ttu-id="f4751-194">在 [世界大綱 (World Outliner)]  中，以滑鼠右鍵按一下您的立方體 > [編輯] > [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="f4751-194">In the **World Outliner**, right click your **Cube > Edit > Delete**.</span></span> <span data-ttu-id="f4751-195">將 [棋盤] 從內容瀏覽器拖曳至檢視區。</span><span class="sxs-lookup"><span data-stu-id="f4751-195">Drag Board from your Content Browser into the viewport.</span></span> <span data-ttu-id="f4751-196">將棋盤的位置設定為 X = 80、Y = 0、Z = -20。</span><span class="sxs-lookup"><span data-stu-id="f4751-196">Set the location of the board to X = 80, Y = 0, Z = -20.</span></span> 

15. <span data-ttu-id="f4751-197">按一下 [播放]  按鈕，以在您的層級中查看新的棋盤。</span><span class="sxs-lookup"><span data-stu-id="f4751-197">Click the **Play** button to view your new board in your level.</span></span> <span data-ttu-id="f4751-198">按 **Esc** 即可返回編輯器。</span><span class="sxs-lookup"><span data-stu-id="f4751-198">Press **Esc** to return to the editor.</span></span> 

16. <span data-ttu-id="f4751-199">現在，我們將使用建立棋盤的相同步驟來建立棋子，這次我們要選取棋子的網格和材質：</span><span class="sxs-lookup"><span data-stu-id="f4751-199">Now we’ll follow the same steps to create a chess piece as we did with the board, this time selecting the mesh and material for the chess piece:</span></span>

    <span data-ttu-id="f4751-200">a) 瀏覽至內容瀏覽器中的 Blueprints 資料夾，並為動作項目類型建立新的藍圖類別。</span><span class="sxs-lookup"><span data-stu-id="f4751-200">a) Navigate to the Blueprints folder in the Content Browser and create a new Blueprint class of type Actor.</span></span> <span data-ttu-id="f4751-201">將此動作項目命名為 "WhiteKing"。</span><span class="sxs-lookup"><span data-stu-id="f4751-201">Name this actor “WhiteKing”.</span></span>

    <span data-ttu-id="f4751-202">b) 按兩下 [WhiteKing] 來將其開啟。</span><span class="sxs-lookup"><span data-stu-id="f4751-202">b) Double click WhiteKing to open it.</span></span> <span data-ttu-id="f4751-203">新增名為 “Root” 的新場景元件，並使用其來取代 DefaultSceneRoot。</span><span class="sxs-lookup"><span data-stu-id="f4751-203">Add a new Scene component named “Root” and use it to replace DefaultSceneRoot.</span></span> 

    <span data-ttu-id="f4751-204">c) 新增名為 "SM_King" 的新靜態網格元件。</span><span class="sxs-lookup"><span data-stu-id="f4751-204">c) Add a new Static Mesh component named “SM_King”.</span></span> <span data-ttu-id="f4751-205">在 [詳細資料] 面板中，將 [靜態網格]  設定為 **Chess_King**，將 [材質]  設定為名為 **M_ChessWhite** 的新材質。</span><span class="sxs-lookup"><span data-stu-id="f4751-205">In the Details panel, set the **Static Mesh** to **Chess_King** and the **Material** to a new Material called **M_ChessWhite**.</span></span> 

    <span data-ttu-id="f4751-206">d) 開啟新的 **M_ChessWhite** 材質，並將相關紋理連結到其對應的材質輸入。</span><span class="sxs-lookup"><span data-stu-id="f4751-206">d) Open the new **M_ChessWhite** Material and hook up the relevant textures to their corresponding material inputs.</span></span> 

    ![為國王棋建立材質](images/unreal-uxt/2-chesskingmat.PNG)

    <span data-ttu-id="f4751-208">e) 回到您的 **WhiteKing** 藍圖，將**縮放**變更為 (0.05, 0.05, 0.05)，並將**旋轉**設定為 Z = 90。</span><span class="sxs-lookup"><span data-stu-id="f4751-208">e) Back in your **WhiteKing** Blueprint, change the **Scale** to (0.05, 0.05, 0.05) and **Rotation** to Z = 90.</span></span>

    <span data-ttu-id="f4751-209">f) 編譯並儲存您的藍圖，然後往回瀏覽到主視窗。</span><span class="sxs-lookup"><span data-stu-id="f4751-209">f) Compile and save your blueprint, then navigate back to your main window.</span></span> 

17. <span data-ttu-id="f4751-210">將 WhiteKing 拖曳至您的檢視區。</span><span class="sxs-lookup"><span data-stu-id="f4751-210">Drag WhiteKing into your viewport.</span></span> <span data-ttu-id="f4751-211">在 [世界大綱]  中，將 WhiteKing 拖曳至棋盤，讓 WhiteKing 現在成為棋盤的子系。</span><span class="sxs-lookup"><span data-stu-id="f4751-211">In the **World Outliner**, drag WhiteKing onto Board so that WhiteKing is now a child of Board.</span></span> 

![世界大綱](images/unreal-uxt/2-child.PNG)

18. <span data-ttu-id="f4751-213">在 [變形]  底下的 [詳細資料]  面板中，將 WhiteKing 的 [位置]  設定為 X = -26、Y = 4、Z = 0</span><span class="sxs-lookup"><span data-stu-id="f4751-213">In the **Details** panel under **Transform**, set the **Location** of WhiteKing to X = -26, Y = 4, Z = 0</span></span>

19. <span data-ttu-id="f4751-214">按一下 [播放]  以查看您的層級。</span><span class="sxs-lookup"><span data-stu-id="f4751-214">Click **Play** to see your level.</span></span> <span data-ttu-id="f4751-215">按 **Esc** 即可結束。</span><span class="sxs-lookup"><span data-stu-id="f4751-215">Press **Esc** to exit.</span></span> 

[<span data-ttu-id="f4751-216">下一節：3.設定您的專案以進行混合實境</span><span class="sxs-lookup"><span data-stu-id="f4751-216">Next Section: 3. Set up your project for mixed reality</span></span>](unreal-uxt-ch3.md)