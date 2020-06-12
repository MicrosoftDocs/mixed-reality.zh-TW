---
title: 4. 使場景成為互動式場景
description: 教學課程系列的第 4 部分 (共有 6 部分)，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置簡單的國際象棋應用程式
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件
ms.openlocfilehash: a9de5755ab86c96322a8d50fecd7ba2cdea866d3
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330215"
---
# <a name="4-making-your-scene-interactive"></a><span data-ttu-id="b8086-104">4.使場景成為互動式場景</span><span class="sxs-lookup"><span data-stu-id="b8086-104">4. Making your scene interactive</span></span>

## <a name="overview"></a><span data-ttu-id="b8086-105">概觀</span><span class="sxs-lookup"><span data-stu-id="b8086-105">Overview</span></span>

<span data-ttu-id="b8086-106">在上一個教學課程中，您已新增 ARSession、Pawn 和遊戲模式，來完成適用於國際象棋應用程式的混合實境設定。</span><span class="sxs-lookup"><span data-stu-id="b8086-106">In the previous tutorial you added an ARSession, Pawn, and Game Mode to complete the mixed reality setup for the chess app.</span></span> <span data-ttu-id="b8086-107">本節著重於使用開放原始碼[混合實境工具組 UX 工具](https://github.com/microsoft/MixedReality-UXTools-Unreal)外掛程式，其提供讓場景成為互動式場景的工具。</span><span class="sxs-lookup"><span data-stu-id="b8086-107">This section focuses on using the open source [Mixed Reality Toolkit UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal) plugin, which provides tools to make the scene interactive.</span></span> <span data-ttu-id="b8086-108">本節結束時，您將能夠以使用者輸入來移動棋子。</span><span class="sxs-lookup"><span data-stu-id="b8086-108">By the end of this section you'll be able to move the chess pieces with user input.</span></span> 

## <a name="objectives"></a><span data-ttu-id="b8086-109">目標</span><span class="sxs-lookup"><span data-stu-id="b8086-109">Objectives</span></span>

* <span data-ttu-id="b8086-110">下載混合實境工具組 UX 工具外掛程式</span><span class="sxs-lookup"><span data-stu-id="b8086-110">Downloading the Mixed Reality Toolkit UX Tools plugin</span></span> 
* <span data-ttu-id="b8086-111">將手部互動動作項目新增至您的指尖</span><span class="sxs-lookup"><span data-stu-id="b8086-111">Adding Hand Interaction Actors to your fingertips</span></span>
* <span data-ttu-id="b8086-112">建立操作工具並將其新增到場景中的物件</span><span class="sxs-lookup"><span data-stu-id="b8086-112">Creating and adding Manipulators to objects in the scene</span></span>
* <span data-ttu-id="b8086-113">使用輸入模擬來驗證專案</span><span class="sxs-lookup"><span data-stu-id="b8086-113">Using input simulation to validate the project</span></span>

## <a name="downloading-the-mrtk-ux-tools-plugin"></a><span data-ttu-id="b8086-114">下載 MRTK UX 工具外掛程式</span><span class="sxs-lookup"><span data-stu-id="b8086-114">Downloading the MRTK UX Tools plugin</span></span>
<span data-ttu-id="b8086-115">開始處理使用者輸入之前，您必須先將外掛程式新增至專案。</span><span class="sxs-lookup"><span data-stu-id="b8086-115">Before you start working with user input, you'll need to add the plugin to the project.</span></span>

1.  <span data-ttu-id="b8086-116">從 [GitHub 存放庫](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases)複製或下載最新的 MRTK UX 工具外掛程式，並將該檔案解壓縮。</span><span class="sxs-lookup"><span data-stu-id="b8086-116">Clone or download the latest MRTK UX Tools plugin from the [GitHub repository](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases) and unzip the file.</span></span>

2.  <span data-ttu-id="b8086-117">在專案的根資料夾中，建立名為 **Plugins** 的新資料夾。</span><span class="sxs-lookup"><span data-stu-id="b8086-117">Create a new folder called **Plugins** in the root folder of the project.</span></span> <span data-ttu-id="b8086-118">將解壓縮的 UXTools 外掛程式複製到這個資料夾中，然後重新啟動 Unreal 編輯器。</span><span class="sxs-lookup"><span data-stu-id="b8086-118">Copy the unzipped UXTools plugin into this folder and restart the Unreal editor.</span></span> 

![建立專案外掛程式資料夾](images/unreal-uxt/4-plugins.PNG)

3.  <span data-ttu-id="b8086-120">UXTools 外掛程式具有子資料夾為 **Pointers**、**Input Simulation** 和 **Simple Button** 的 Content 資料夾，以及由函式區隔的 C++ Classes 資料夾。</span><span class="sxs-lookup"><span data-stu-id="b8086-120">The UXTools plugin has a Content folder with subfolders for **Pointers**, **Input Simulation**, and **Simple Button**, as well as a C++ Classes folder separated by function.</span></span>  

> [!NOTE]
> <span data-ttu-id="b8086-121">如果您在 [內容瀏覽器] 中沒有看到 [UXTools 內容] 區段，請按一下 [檢視選項] > [顯示外掛程式內容]。</span><span class="sxs-lookup"><span data-stu-id="b8086-121">If you don’t see the **UXTools Content** section in the **Content Browser**, click **View Options > Show Plugin Content**.</span></span> 

![顯示外掛程式內容](images/unreal-uxt/4-showplugincontent.PNG)

<span data-ttu-id="b8086-123">一旦安全地安裝了外掛程式，您就可以開始使用程式所提供的工具，從手部互動動作項目開始。</span><span class="sxs-lookup"><span data-stu-id="b8086-123">With the plugin safely installed, you're ready to start using the tools it has to offer, starting with hand interaction actors.</span></span>

## <a name="spawning-hand-interaction-actors"></a><span data-ttu-id="b8086-124">繁衍手部互動動作項目</span><span class="sxs-lookup"><span data-stu-id="b8086-124">Spawning Hand Interaction Actors</span></span>
<span data-ttu-id="b8086-125">與 UX 元素的手動互動是搭配手動互動動作項目來執行，此動作項目會建立及驅動指標和視覺效果，以進行遠近距離互動。</span><span class="sxs-lookup"><span data-stu-id="b8086-125">Hand interaction with UX elements is performed with Hand Interaction Actors, which create and drive the pointers and visuals for near and far interactions.</span></span>
- <span data-ttu-id="b8086-126">*近距離互動*是藉由在食指與拇指之間捏合元素或用指尖點戳來執行的。</span><span class="sxs-lookup"><span data-stu-id="b8086-126">*Near interactions* are performed by pinching elements between index finger and thumb or by poking them with a fingertip.</span></span> 
- <span data-ttu-id="b8086-127">*遠距離互動*是將虛擬手發出的光線指向某個元素，並同時按下食指和拇指來執行的。</span><span class="sxs-lookup"><span data-stu-id="b8086-127">*Far interactions* are performed by pointing a ray from the virtual hand at an element and pressing index and thumb together.</span></span>

<span data-ttu-id="b8086-128">在我們的案例中，將手部互動動作項目新增至 **MRPawn** 將會：</span><span class="sxs-lookup"><span data-stu-id="b8086-128">In our case, adding a Hand Interaction Actor to **MRPawn** will:</span></span>
- <span data-ttu-id="b8086-129">新增游標至 Pawn 食指的指尖。</span><span class="sxs-lookup"><span data-stu-id="b8086-129">Add a cursor to the tips of the Pawn’s index fingers.</span></span>
- <span data-ttu-id="b8086-130">提供以關節連接的手部輸入事件，可透過 Pawn 操作。</span><span class="sxs-lookup"><span data-stu-id="b8086-130">Provide articulated hand input events that can be manipulated through the Pawn.</span></span>
- <span data-ttu-id="b8086-131">允許透過從虛擬手掌延伸的手部光線，進行遠距離互動輸入事件。</span><span class="sxs-lookup"><span data-stu-id="b8086-131">Allow far interaction input events through hand rays extending from the palms of the virtual hands.</span></span>

<span data-ttu-id="b8086-132">為了將這些概念說清楚，鼓勵您先仔細閱讀有關手部互動的[文件](https://github.com/microsoft/MixedReality-UXTools-Unreal/blob/public/0.8.x/Docs/HandInteraction.md)，再繼續進行。</span><span class="sxs-lookup"><span data-stu-id="b8086-132">In order to drive these concepts home, you're encouraged to read through the [documentation](https://github.com/microsoft/MixedReality-UXTools-Unreal/blob/public/0.8.x/Docs/HandInteraction.md) on hand interactions before continuing.</span></span> 

<span data-ttu-id="b8086-133">一旦準備好，就開啟 **MRPawn** 藍圖，然後移至 [事件圖形]。</span><span class="sxs-lookup"><span data-stu-id="b8086-133">Once you're ready, open the **MRPawn** Blueprint and go to the **Event Graph**.</span></span> 

1. <span data-ttu-id="b8086-134">從 **Event BeginPlay** 拖曳並放開執行釘選，以放置新的節點。</span><span class="sxs-lookup"><span data-stu-id="b8086-134">Drag and release the execution pin from **Event BeginPlay** to place a new node.</span></span> 
    * <span data-ttu-id="b8086-135">選取 [從類別繁衍動作項目]、按一下 [類別] 釘選旁的下拉式清單，然後搜尋 [Uxt 手部互動動作項目]。</span><span class="sxs-lookup"><span data-stu-id="b8086-135">Select **Spawn Actor from Class**, click the dropdown next to the **Class** pin and search for **Uxt Hand Interaction Actor**.</span></span> 

2. <span data-ttu-id="b8086-136">從 [SpawnActor Uxt 手部互動] 節點拖曳並放開執行釘選，然後搜尋 [Uxt 手部互動動作項目] 類別中的 [設定手部] 功能。</span><span class="sxs-lookup"><span data-stu-id="b8086-136">Drag and release the execution pin from the **SpawnActor Uxt Hand Interaction** node and search for the **Set Hand** function in the **Uxt Hand Interaction Actor** class.</span></span> 
    * <span data-ttu-id="b8086-137">將 **SpawnActor** 節點的 [傳回值] 連線至 [設定手部] 節點的 [目標] 釘選。</span><span class="sxs-lookup"><span data-stu-id="b8086-137">Connect the **SpawnActor** node’s **Return Value** to the **Target** pin of the **Set Hand** node.</span></span> <span data-ttu-id="b8086-138">這會將手部互動動作項目的手部設定為 [左手]。</span><span class="sxs-lookup"><span data-stu-id="b8086-138">This sets the hand of the Hand Interaction Actor to **Left**.</span></span> 

3. <span data-ttu-id="b8086-139">繁衍第二個 [Uxt 手部互動動作項目]，這次會將手部設定為 [右手]。</span><span class="sxs-lookup"><span data-stu-id="b8086-139">Spawn a second **Uxt Hand Interaction Actor**, this time setting the hand to **Right**.</span></span> <span data-ttu-id="b8086-140">當事件開始時，會在每個手部上繁衍 Uxt 手部互動動作項目。</span><span class="sxs-lookup"><span data-stu-id="b8086-140">When the event begins, a Uxt Hand Interaction Actor will be spawned on each hand.</span></span> 

<span data-ttu-id="b8086-141">您的 [事件圖形] 應該符合下列螢幕擷取畫面：</span><span class="sxs-lookup"><span data-stu-id="b8086-141">Your **Event Graph** should match the following screenshot:</span></span>

![繁衍 UXT 手部互動動作項目](images/unreal-uxt/4-spawnactor.PNG)

<span data-ttu-id="b8086-143">這兩個 Uxt 手部互動動作項目都需要擁有者和初始轉換位置。</span><span class="sxs-lookup"><span data-stu-id="b8086-143">Both Uxt Hand Interaction Actors need owners and initial transform locations.</span></span> <span data-ttu-id="b8086-144">初始轉換並不重要，因為手動互動動作項目會在其可見時立即跳到虛擬手部 (此行為包含在 UX 工具外掛程式中)。</span><span class="sxs-lookup"><span data-stu-id="b8086-144">The initial transform  doesn’t matter since the Hand Interaction Actors will jump to the virtual hands as soon as they're visible (this behavior is included in the UX Tools plugin).</span></span> <span data-ttu-id="b8086-145">不過，`SpawnActor` 函式需要轉換輸入來避免編譯器錯誤，因此您將使用預設值。</span><span class="sxs-lookup"><span data-stu-id="b8086-145">However, the `SpawnActor` function requires a Transform input to avoid a compiler error, so you'll use the default values.</span></span> 

1. <span data-ttu-id="b8086-146">從其中一個 [繁衍轉換] 釘選拖曳並放開釘選，以放置新的節點。</span><span class="sxs-lookup"><span data-stu-id="b8086-146">Drag and release the pin off one of the **Spawn Transform** pins to place a new node.</span></span> 
    * <span data-ttu-id="b8086-147">搜尋 [進行轉換] 節點，然後將 [傳回值] 拖曳至另一手的 [繁衍轉換]，讓兩個 **SpawnActor** 節點連線。</span><span class="sxs-lookup"><span data-stu-id="b8086-147">Search for the **Make Transform** node, then drag the **Return Value** to the other hand’s **Spawn Transform** so that both **SpawnActor** nodes are connected.</span></span> 

3.  <span data-ttu-id="b8086-148">按一下兩個 **SpawnActor** 節點底端的**向下箭頭**，以顯示 [擁有者] 釘選。</span><span class="sxs-lookup"><span data-stu-id="b8086-148">Click the **down arrow** at the bottom of both **SpawnActor** nodes to reveal the **Owner** pin.</span></span>    
    * <span data-ttu-id="b8086-149">從其中一個**擁有者**釘選拖曳釘選，然後放開以放置新的節點。</span><span class="sxs-lookup"><span data-stu-id="b8086-149">Drag the pin off one of the **Owner** pins and release to place a new node.</span></span> 
    * <span data-ttu-id="b8086-150">搜尋 [本身] 並選取 [取得本身的參考] 變數，然後在 [本身] 物件參考節點與其他手部互動動作項目的 [擁有者] 釘選之間建立連結。</span><span class="sxs-lookup"><span data-stu-id="b8086-150">Search for **self** and select the **Get a reference to self** variable, then create a link between the **Self** object reference node and the other Hand Interaction Actor’s **Owner** pin.</span></span> 
    * <span data-ttu-id="b8086-151">**編譯**、**儲存**，然後返回主視窗。</span><span class="sxs-lookup"><span data-stu-id="b8086-151">**Compile**, **save**, and return to the Main window.</span></span> 

<span data-ttu-id="b8086-152">確定連線符合下列螢幕擷取畫面，但是您可以隨意拖曳節點，讓您的藍圖更容易閱讀</span><span class="sxs-lookup"><span data-stu-id="b8086-152">Make sure the connections match the following screenshot, but feel free to drag around nodes to make your Blueprint more readable</span></span>

![完成 UXT 手部互動動作項目設定](images/unreal-uxt/4-fingerptrs.PNG) 

<span data-ttu-id="b8086-154">若要深入了解 MRTK UX 工具外掛程式中所提供的手部互動動作項目，請參閱[文件](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/HandInteraction.html)。</span><span class="sxs-lookup"><span data-stu-id="b8086-154">You can find more information about the Hand Interaction Actor provided in the MRTK UX Tools plugin in the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/HandInteraction.html).</span></span>

<span data-ttu-id="b8086-155">現在，專案中的虛擬手部有一種方式可以選取物件，但仍然無法進行操作。</span><span class="sxs-lookup"><span data-stu-id="b8086-155">Now the virtual hands in the project have a way of selecting objects, but they still can't manipulate them.</span></span> <span data-ttu-id="b8086-156">測試應用程式前的最後一項工作是將操作工具元件新增至場景中的動作項目。</span><span class="sxs-lookup"><span data-stu-id="b8086-156">Your last task before testing the app is to add Manipulator components to the actors in the scene.</span></span>

## <a name="attaching-manipulators"></a><span data-ttu-id="b8086-157">附加操作工具</span><span class="sxs-lookup"><span data-stu-id="b8086-157">Attaching Manipulators</span></span>

<span data-ttu-id="b8086-158">操作工具是一種元件，可回應以關節連接的手部輸入，而且可以抓取、旋轉和轉譯。</span><span class="sxs-lookup"><span data-stu-id="b8086-158">A Manipulator is a component that responds to articulated hand input and can be grabbed, rotated, and translated.</span></span> <span data-ttu-id="b8086-159">將操作工具的轉換套用至動作項目轉換可允許直接動作項目操作。</span><span class="sxs-lookup"><span data-stu-id="b8086-159">Applying the Manipulator’s transform to an Actors transform allows direct Actor manipulation.</span></span> 

1. <span data-ttu-id="b8086-160">開啟 [棋盤] 藍圖、按一下 [新增元件]，然後在 [元件] 面板中搜尋 [Uxt 一般操作工具]。</span><span class="sxs-lookup"><span data-stu-id="b8086-160">Open the **Board** blueprint, click **Add Component** and search for **Uxt Generic Manipulator** in the **Components** panel.</span></span>

![新增一般操作工具](images/unreal-uxt/4-addmanip.PNG)

2. <span data-ttu-id="b8086-162">展開 [詳細資料] 面板中的 [一般操作工具] 區段。</span><span class="sxs-lookup"><span data-stu-id="b8086-162">Expand the **Generic Manipulator** section in the **Details** panel.</span></span> <span data-ttu-id="b8086-163">您可以從這裡設定單手或雙手操作、旋轉模式和其他等等。</span><span class="sxs-lookup"><span data-stu-id="b8086-163">You can set one-handed or two-handed manipulation, rotation mode, and smoothing from here.</span></span> <span data-ttu-id="b8086-164">請隨意選取您想要的任何模式，然後 [編譯] 及 [儲存] 棋盤。</span><span class="sxs-lookup"><span data-stu-id="b8086-164">Feel free to select whichever modes you wish, then **Compile** and **Save** Board.</span></span> 

![設定模式](images/unreal-uxt/4-setrotmode.PNG)

3. <span data-ttu-id="b8086-166">針對 **WhiteKing** 動作項目重複上述步驟。</span><span class="sxs-lookup"><span data-stu-id="b8086-166">Repeat the steps above for the **WhiteKing** Actor.</span></span>

<span data-ttu-id="b8086-167">若要深入了解 MRTK UX 工具外掛程式中所提供的操作工具元件，請參閱[文件](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/Manipulator.html)。</span><span class="sxs-lookup"><span data-stu-id="b8086-167">You can find more information about the Manipulator Components provided in the MRTK UX Tools plugin in the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/Manipulator.html).</span></span>

## <a name="testing-the-scene"></a><span data-ttu-id="b8086-168">測試場景</span><span class="sxs-lookup"><span data-stu-id="b8086-168">Testing the scene</span></span>
<span data-ttu-id="b8086-169">好消息！</span><span class="sxs-lookup"><span data-stu-id="b8086-169">Good news everyone!</span></span> <span data-ttu-id="b8086-170">您已經準備好使用新的虛擬手部和使用者輸入來測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="b8086-170">You're ready to test out the app with its new virtual hands and user input.</span></span> <span data-ttu-id="b8086-171">按下主視窗中的 [播放]，您會看到由 MRTK UX 工具外掛程式提供的兩個網狀手部，並且具有從每一個手掌延伸的手部光線。</span><span class="sxs-lookup"><span data-stu-id="b8086-171">Press **Play** in the Main Window and you'll see two mesh hands provided by the MRTK UX Tools plugin with hand rays extending from each hand’s palm.</span></span> <span data-ttu-id="b8086-172">您可以控制手部及其互動，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b8086-172">You can control the hands and their interactions as follows:</span></span>
- <span data-ttu-id="b8086-173">按住**左 Alt** 鍵，以控制**左手**，按住**左 Shift** 鍵，以控制**右手**。</span><span class="sxs-lookup"><span data-stu-id="b8086-173">Hold down the **left Alt** key to control the **left hand** and the **left Shift** key to control the **right hand**.</span></span> 
- <span data-ttu-id="b8086-174">移動您的滑鼠來移動手部，並使用您的**滑鼠滾輪**來捲動，將手部**向前**或**向後**移動。</span><span class="sxs-lookup"><span data-stu-id="b8086-174">Move your mouse to move the hand and scroll with your **mouse wheel** to move the hand **forwards** or **backwards**.</span></span> 
- <span data-ttu-id="b8086-175">按一下滑鼠左鍵以**捏合**，按一下滑鼠中間按鈕以**撥開**。</span><span class="sxs-lookup"><span data-stu-id="b8086-175">Click the left mouse button to **pinch**, click the middle mouse button to **poke**.</span></span> 

![檢視區中的模擬手部](images/unreal-uxt/4-handsim.PNG)

<span data-ttu-id="b8086-177">試著使用模擬的手部來拾起、移動和放置白棋國王，並操作棋盤！</span><span class="sxs-lookup"><span data-stu-id="b8086-177">Try using the simulated hands to pick up, move, and set down the white chess king and manipulate the board!</span></span> <span data-ttu-id="b8086-178">實驗遠近距離互動 - 請注意，當您的手夠靠近可以直接抓取棋盤和國王時，手部光線會消失，並取代為食指指尖上的手指游標。</span><span class="sxs-lookup"><span data-stu-id="b8086-178">Experiment with both near and far interaction - notice that when your hands get close enough to grab the board and king directly, the hand ray disappears and is replaced with a finger cursor at the tip of the index finger.</span></span> 

<span data-ttu-id="b8086-179">若要深入了解 MRTK UX 工具外掛程式中所提供的模擬手部功能，請參閱[文件](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/InputSimulation.html)。</span><span class="sxs-lookup"><span data-stu-id="b8086-179">You can find more information about the simulated hands feature provided by the MRTK UX Tools plugin in the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/InputSimulation.html).</span></span>

<span data-ttu-id="b8086-180">既然您的虛擬手部可以與物件互動，您就可以繼續進行下一個教學課程，並新增使用者介面和事件。</span><span class="sxs-lookup"><span data-stu-id="b8086-180">Now that your virtual hands can interact with objects, you're ready to move on to the next tutorial and add user interfaces and events.</span></span>

[<span data-ttu-id="b8086-181">下一節：5.新增按鈕並重設棋子位置</span><span class="sxs-lookup"><span data-stu-id="b8086-181">Next Section: 5. Adding a button & resetting piece locations</span></span>](unreal-uxt-ch5.md)
