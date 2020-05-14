---
title: 4. 使場景成為互動式場景
description: 教學課程的第 4 部分，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置簡單的國際象棋應用程式
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件
ms.openlocfilehash: 17f7ab1c1126c47e5ac6388d125d45cf3f2c2d87
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851543"
---
# <a name="3-making-your-scene-interactive"></a><span data-ttu-id="14ae8-104">3.使場景成為互動式場景</span><span class="sxs-lookup"><span data-stu-id="14ae8-104">3. Making your scene interactive</span></span>

<span data-ttu-id="14ae8-105">本節將為您介紹開放原始碼混合實境工具組 UX 工具外掛程式，其提供一組工具讓您輕鬆地使場景成為互動式場景。</span><span class="sxs-lookup"><span data-stu-id="14ae8-105">This section introduces you to the open source Mixed Reality Toolkit UX Tools plugin, which provides a set of tools to easily make your scene interactive.</span></span> <span data-ttu-id="14ae8-106">在本節結束時，您的國際象棋將會回應使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="14ae8-106">By the end of this section, your chess pieces will respond to user input.</span></span> 

## <a name="objectives"></a><span data-ttu-id="14ae8-107">目標</span><span class="sxs-lookup"><span data-stu-id="14ae8-107">Objectives</span></span>

* <span data-ttu-id="14ae8-108">在您的專案中包含混合實境工具組 UX 工具外掛程式</span><span class="sxs-lookup"><span data-stu-id="14ae8-108">Include the Mixed Reality Toolkit UX Tools plugin in your project</span></span>
* <span data-ttu-id="14ae8-109">將手部互動動作項目新增至您的指尖</span><span class="sxs-lookup"><span data-stu-id="14ae8-109">Add Hand Interaction Actors to your fingertips</span></span>
* <span data-ttu-id="14ae8-110">建立操作工具，並將其附加到您的國際象棋棋盤和棋子</span><span class="sxs-lookup"><span data-stu-id="14ae8-110">Create and attach Manipulators to your chess board and pieces</span></span> 
* <span data-ttu-id="14ae8-111">使用輸入模擬來驗證您的專案</span><span class="sxs-lookup"><span data-stu-id="14ae8-111">Use input simulation to validate your project</span></span>

## <a name="download-the-mixed-reality-toolkit-ux-tools-plugin"></a><span data-ttu-id="14ae8-112">下載混合實境工具組 UX 工具外掛程式</span><span class="sxs-lookup"><span data-stu-id="14ae8-112">Download the Mixed Reality Toolkit UX Tools plugin</span></span>

1.  <span data-ttu-id="14ae8-113">從 [UX 工具 GitHub 存放庫](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases)複製或下載並解壓縮最新版本的 MRTK UX 工具外掛程式</span><span class="sxs-lookup"><span data-stu-id="14ae8-113">Clone or download and unzip the latest release of the MRTK UX Tools plugin from the [UX Tools GitHub repository](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases)</span></span>

2.  <span data-ttu-id="14ae8-114">在您的國際象棋專案根資料夾中，建立名為「外掛程式」的新資料夾。</span><span class="sxs-lookup"><span data-stu-id="14ae8-114">In your chess project root folder, create a new folder called “Plugins”.</span></span> <span data-ttu-id="14ae8-115">將解壓縮的 UXTools 外掛程式複製到此資料夾中。</span><span class="sxs-lookup"><span data-stu-id="14ae8-115">Copy your unzipped UXTools plugin into this folder.</span></span> <span data-ttu-id="14ae8-116">重新啟動 Unreal 編輯器。</span><span class="sxs-lookup"><span data-stu-id="14ae8-116">Restart the Unreal editor.</span></span> 

![建立專案外掛程式資料夾](images/unreal-uxt/4-plugins.PNG)

3.  <span data-ttu-id="14ae8-118">重新啟動之後，如果您在來源面板中看不到 UXTools 外掛程式內容，您可能需要按一下 [檢視選項] > [顯示外掛程式內容]  。</span><span class="sxs-lookup"><span data-stu-id="14ae8-118">After restarting, if you don’t see UXTools plugin content in your sources panel, you may need to click on **View Options > Show Plugin Content**.</span></span> <span data-ttu-id="14ae8-119">您會看到 UXTools 外掛程式提供具有指標、輸入模擬和簡單按鈕的內容資料夾，以及 C++ 類別資料夾 (具有以函式分隔的子資料夾)。</span><span class="sxs-lookup"><span data-stu-id="14ae8-119">You’ll see that the UXTools plugin provides a Content folder with Pointers, Input Simulation, and a Simple Button, as well as a C++ Classes folder with subfolders separated by function.</span></span>  

![顯示外掛程式內容](images/unreal-uxt/4-showplugincontent.PNG)

## <a name="spawn-hand-interaction-actors"></a><span data-ttu-id="14ae8-121">繁衍手部互動動作項目</span><span class="sxs-lookup"><span data-stu-id="14ae8-121">Spawn Hand Interaction Actors</span></span>

1.  <span data-ttu-id="14ae8-122">讓我們從 MRPawn 繁衍手部互動動作項目開始，如此一來 1) 我們可以使用游標視覺化 MRPawn，在食指指尖上顯示「兵」，2) 我們可以透過「兵」提供以關節連接的手部輸入事件 (因此直接操作動作項目)，以及 3) 我們可以透過從手掌延伸的手部光線提供遠處互動輸入事件。</span><span class="sxs-lookup"><span data-stu-id="14ae8-122">Let’s start by spawning Hand Interaction Actors from our MRPawn so that 1) we can visualize MRPawn with a cursor on the tips of the Pawn’s index fingers, 2) we can provide articulated hand input events (and thus, directly manipulate actors) through the Pawn, and 3) we can provide far interaction input events through hand rays extending from our palms.</span></span> <span data-ttu-id="14ae8-123">開啟 **MRPawn** 藍圖，然後瀏覽至**事件圖形**。</span><span class="sxs-lookup"><span data-stu-id="14ae8-123">Open the **MRPawn** Blueprint and navigate to the **Event Graph**.</span></span> 

2.  <span data-ttu-id="14ae8-124">從 Event BeginPlay 拖曳執行釘選，放開以放置新的節點。</span><span class="sxs-lookup"><span data-stu-id="14ae8-124">Drag the execution pin from Event BeginPlay and release to place a new node.</span></span> <span data-ttu-id="14ae8-125">選取 [從類別繁衍動作項目]  節點。</span><span class="sxs-lookup"><span data-stu-id="14ae8-125">Select the **Spawn Actor from Class** node.</span></span> <span data-ttu-id="14ae8-126">按一下 [類別]  釘選旁的下拉式清單，然後搜尋 **Uxt 手部互動動作項目**。</span><span class="sxs-lookup"><span data-stu-id="14ae8-126">Click the dropdown next to the **Class** pin and search for **Uxt Hand Interaction Actor**.</span></span> <span data-ttu-id="14ae8-127">從 SpawnActor Uxt 手部互動節點拖曳執行釘選、放開，然後搜尋 Uxt 手部互動動作項目類別中包含的**設定手部**功能。</span><span class="sxs-lookup"><span data-stu-id="14ae8-127">Drag the execution pin from the SpawnActor Uxt Hand Interaction node, release, and search for the **Set Hand** function contained in the Uxt Hand Interaction Actor class.</span></span> <span data-ttu-id="14ae8-128">將 SpawnActor 節點的傳回值連線至 [設定手部] 節點的目標釘選，以將手部互動動作項目的手部設為**左手**。</span><span class="sxs-lookup"><span data-stu-id="14ae8-128">Connect the SpawnActor node’s Return Value to the Target pin of the Set Hand node to set the hand of the Hand Interaction Actor to **Left**.</span></span> <span data-ttu-id="14ae8-129">繁衍第二個 **Uxt 手部互動動作項目**，這一次將手部設定為**右手**，如此一來，當事件開始時，Uxt 手部互動動作項目就會在各個手上繁衍。</span><span class="sxs-lookup"><span data-stu-id="14ae8-129">Spawn a second **Uxt Hand Interaction Actor**, this time setting the hand to **Right**, so that when the event begins, a Uxt Hand Interaction Actor will be spawned on each hand.</span></span> 

![繁衍 UXT 手部互動動作項目](images/unreal-uxt/4-spawnactor.PNG)

3.  <span data-ttu-id="14ae8-131">接下來，我們需要提供我們的 Uxt 手部互動動作項目，以及要繁衍的初始轉換和擁有者。</span><span class="sxs-lookup"><span data-stu-id="14ae8-131">Next, we need to provide our Uxt Hand Interaction Actors with an initial transform at which to spawn, and an owner.</span></span> <span data-ttu-id="14ae8-132">從其中一個**繁衍轉換**釘選拖曳釘選，然後放開以放置新的節點。</span><span class="sxs-lookup"><span data-stu-id="14ae8-132">Drag the pin off one of the **Spawn Transform** pins and release to place a new node.</span></span> <span data-ttu-id="14ae8-133">搜尋**製作轉換**節點。</span><span class="sxs-lookup"><span data-stu-id="14ae8-133">Search for the **Make Transform** node.</span></span> <span data-ttu-id="14ae8-134">初始轉換其實並不重要，因為手部互動動作項目會在其可見 (已在 UX 工具外掛程式中為我們撰寫的程式碼) 時立即跳到我們的手上，否則將會消失。</span><span class="sxs-lookup"><span data-stu-id="14ae8-134">The initial transform really doesn’t matter since the Hand Interaction Actors will jump to our hands as soon as they are visible (code that’s already written for us in the UX Tools plugin), otherwise, they’ll disappear.</span></span> <span data-ttu-id="14ae8-135">不過，SpawnActor 功能需要轉換作為輸入，以避免編譯器錯誤，因此我們保留「製作轉換」節點中原來的預設值。</span><span class="sxs-lookup"><span data-stu-id="14ae8-135">However, the SpawnActor function requires a Transform as input to avoid a compiler error, so we’ll just leave the default values in Make Transform as is.</span></span> <span data-ttu-id="14ae8-136">同時將「製作轉換」的**傳回值**拖曳至另一隻手的互動動作項目繁衍轉換。</span><span class="sxs-lookup"><span data-stu-id="14ae8-136">Drag Make Transform’s **Return Value** to the other hand’s Interaction Actor Spawn Transform as well.</span></span> 

4.  <span data-ttu-id="14ae8-137">按一下兩個 SpawnActor 節點底端的**向下鍵**，以顯示**擁有者**釘選。</span><span class="sxs-lookup"><span data-stu-id="14ae8-137">Click the **down arrow** at the bottom of both SpawnActor nodes to reveal the **Owner** pin.</span></span> <span data-ttu-id="14ae8-138">從其中一個**擁有者**釘選拖曳釘選，然後放開以放置新的節點。</span><span class="sxs-lookup"><span data-stu-id="14ae8-138">Drag the pin off one of the **Owner** pins and release to place a new node.</span></span> <span data-ttu-id="14ae8-139">搜尋「本身」，然後選取**取得本身的參考**變數。</span><span class="sxs-lookup"><span data-stu-id="14ae8-139">Search for “self” and select the **Get a reference to self** variable.</span></span> <span data-ttu-id="14ae8-140">同時在「本身」物件參考節點與另一個手部互動動作項目的擁有者釘選之間建立連結。</span><span class="sxs-lookup"><span data-stu-id="14ae8-140">Create a link between the Self object reference node and the other Hand Interaction Actor’s Owner pin as well.</span></span> <span data-ttu-id="14ae8-141">您可以隨意拖曳節點，讓您的藍圖更容易讀取。</span><span class="sxs-lookup"><span data-stu-id="14ae8-141">Feel free to drag around nodes to make your Blueprint more readable.</span></span> <span data-ttu-id="14ae8-142">**編譯**、**儲存**，然後返回主視窗。</span><span class="sxs-lookup"><span data-stu-id="14ae8-142">**Compile**, **save**, and return to the Main window.</span></span> 

![完成 UXT 手部互動動作項目設定](images/unreal-uxt/4-fingerptrs.PNG)

<span data-ttu-id="14ae8-144">如需有關 MRTK UX 工具外掛程式中所提供手部互動動作項目的詳細資訊，請參閱官方[文件](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/HandInteraction.html)。</span><span class="sxs-lookup"><span data-stu-id="14ae8-144">For more information about the Hand Interaction Actor provided in the MRTK UX Tools plugin, check out the official [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/HandInteraction.html).</span></span>

## <a name="attach-manipulators"></a><span data-ttu-id="14ae8-145">附加操作工具</span><span class="sxs-lookup"><span data-stu-id="14ae8-145">Attach Manipulators</span></span>

1.  <span data-ttu-id="14ae8-146">接下來，我們會將操作工具附加到我們的國際象棋棋盤和國王動作項目。</span><span class="sxs-lookup"><span data-stu-id="14ae8-146">Next, we’ll attach Manipulators to our chess board and king Actors.</span></span> <span data-ttu-id="14ae8-147">操作工具是一個元件，其回應以關節連接的手部輸入，而且可以抓取、旋轉和轉譯；藉由將操作工具的轉換套用至動作項目，可以直接操控動作項目。</span><span class="sxs-lookup"><span data-stu-id="14ae8-147">A Manipulator is a component that responds to articulated hand input and can be grabbed, rotated, and translated; by applying the Manipulator’s transform to that of an Actor, Actors can be directly manipulated.</span></span> 

2.  <span data-ttu-id="14ae8-148">開啟您的棋盤藍圖。</span><span class="sxs-lookup"><span data-stu-id="14ae8-148">Open your Board Blueprint.</span></span> <span data-ttu-id="14ae8-149">在 [元件]  面板中，按一下 [新增元件]  ，並搜尋 **Uxt 一般操作工具**。</span><span class="sxs-lookup"><span data-stu-id="14ae8-149">In the **Components** panel, click **Add Component** and search for **Uxt Generic Manipulator**.</span></span> <span data-ttu-id="14ae8-150">在 [詳細資料] 面板中，您會找到標題為 [一般操作工具]  的區段，您可以在其中設定要啟用單手或雙手操作、旋轉模式和平滑處理。</span><span class="sxs-lookup"><span data-stu-id="14ae8-150">In the Details panel, you’ll find a section titled **Generic Manipulator** where you can set whether you want to enable one-handed or two-handed manipulation, the rotation mode, and smoothing.</span></span> <span data-ttu-id="14ae8-151">請隨意選取您想要的任何模式，然後 [編譯]  及 [儲存]  棋盤。</span><span class="sxs-lookup"><span data-stu-id="14ae8-151">Feel free to select whichever modes you wish, then **Compile** and **Save** Board.</span></span> 

![新增一般操作工具](images/unreal-uxt/4-addmanip.PNG)

![設定模式](images/unreal-uxt/4-setrotmode.PNG)

3.  <span data-ttu-id="14ae8-154">針對 WhiteKing 動作項目重複上述步驟。</span><span class="sxs-lookup"><span data-stu-id="14ae8-154">Repeat the steps above for the WhiteKing Actor.</span></span>

<span data-ttu-id="14ae8-155">如需有關 MRTK UX 工具外掛程式中所提供操作工具元件的詳細資訊，請參閱官方[文件](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/Manipulator.html)。</span><span class="sxs-lookup"><span data-stu-id="14ae8-155">For more information about the Manipulator Components provided in the MRTK UX Tools plugin, visit the official [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/Manipulator.html).</span></span>

## <a name="test-out-your-scene-with-simulated-hands"></a><span data-ttu-id="14ae8-156">使用模擬的手測試您的場景</span><span class="sxs-lookup"><span data-stu-id="14ae8-156">Test out your scene with simulated hands</span></span>

1.  <span data-ttu-id="14ae8-157">在主視窗中，按下 [播放]  。</span><span class="sxs-lookup"><span data-stu-id="14ae8-157">In the Main window, press **Play**.</span></span> <span data-ttu-id="14ae8-158">您應該會看到由 MRTK UX 工具外掛程式提供的兩個網狀手部，並且具有從每一個手掌延伸的手部光線！</span><span class="sxs-lookup"><span data-stu-id="14ae8-158">You should see two mesh hands provided by the MRTK UX Tools plugin, with hand rays extending from each hand’s palm!</span></span> 

![檢視區中的模擬手部](images/unreal-uxt/4-handsim.PNG)

2.  <span data-ttu-id="14ae8-160">若要控制**右手**，請按住**左 Alt** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="14ae8-160">To control the **right hand**, hold down the **left Alt** button.</span></span> <span data-ttu-id="14ae8-161">移動滑鼠來移動手部。</span><span class="sxs-lookup"><span data-stu-id="14ae8-161">Move your mouse to move the hand.</span></span> <span data-ttu-id="14ae8-162">使用您的**滑鼠滾輪**捲動，將手部**向前**或**向後**移動。</span><span class="sxs-lookup"><span data-stu-id="14ae8-162">Scroll with your **mouse wheel** to move the hand **forwards** or **backwards**.</span></span> <span data-ttu-id="14ae8-163">按一下滑鼠左鍵以**捏合**，按一下滑鼠中間按鈕以**撥開**。</span><span class="sxs-lookup"><span data-stu-id="14ae8-163">Click your left mouse to **pinch**, click the middle mouse button to **poke**.</span></span>

3.  <span data-ttu-id="14ae8-164">若要控制**左手**，請按住**左 Shift** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="14ae8-164">To control the **left hand**, hold down the **left Shift** button.</span></span> <span data-ttu-id="14ae8-165">用來移動左手的控制項與右手的控制項相同。</span><span class="sxs-lookup"><span data-stu-id="14ae8-165">The controls for moving the left hand are the same as those for the right hand.</span></span> 

4.  <span data-ttu-id="14ae8-166">現在請試著使用模擬的手來拾起、移動和放置白棋國王。</span><span class="sxs-lookup"><span data-stu-id="14ae8-166">Now try using the simulated hands to pick up, move, and set down the white chess king.</span></span> <span data-ttu-id="14ae8-167">您也可以操控棋盤！</span><span class="sxs-lookup"><span data-stu-id="14ae8-167">You can also manipulate the board!</span></span> <span data-ttu-id="14ae8-168">具有遠近互動的實驗 - 請注意，當您的手夠靠近可以直接抓取棋盤和國王時，手部光線會消失，並且以索引提示上的手指游標取代。</span><span class="sxs-lookup"><span data-stu-id="14ae8-168">Experiment with both near and far interaction- notice that when your hands get close enough to grab the board and king directly, the hand ray disappears and is replaced with a finger cursor on the index tip.</span></span> 

<span data-ttu-id="14ae8-169">如需有關 MRTK UX 工具外掛程式中所提供模擬手部功能的詳細資訊，請參閱官方[文件](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/InputSimulation.html)。</span><span class="sxs-lookup"><span data-stu-id="14ae8-169">For more information about the simulated hands feature provided by the MRTK UX Tools plugin, visit the official [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/InputSimulation.html).</span></span>

[<span data-ttu-id="14ae8-170">下一節：5.新增按鈕並重設部分位置</span><span class="sxs-lookup"><span data-stu-id="14ae8-170">Next Section: 5. Adding a button & resetting piece locations</span></span>](unreal-uxt-ch5.md)