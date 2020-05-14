---
title: 5. 新增按鈕並重設棋子位置
description: 教學課程的第 5 部分，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置簡單的國際象棋應用程式
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件
ms.openlocfilehash: df5ea22e7097fdd3b788ec298bc1cd78c315b585
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840397"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a><span data-ttu-id="a0b57-104">5.新增按鈕並重設棋子位置</span><span class="sxs-lookup"><span data-stu-id="a0b57-104">5. Adding a button & resetting piece locations</span></span>

<span data-ttu-id="a0b57-105">本節將繼續示範混合實境工具組 UX 工具外掛程式的功能，並建置國際象棋應用程式的特性。</span><span class="sxs-lookup"><span data-stu-id="a0b57-105">This section continues demonstrating the capabilities of the Mixed Reality Toolkit UX Tools plugin and building out the features of your chess app.</span></span> <span data-ttu-id="a0b57-106">您將建立新的函式，並了解如何將您層級中的動作項目參考放到藍圖中。</span><span class="sxs-lookup"><span data-stu-id="a0b57-106">You’ll create a new function and learn how to get references to Actors from your Level into a Blueprint.</span></span>

## <a name="objectives"></a><span data-ttu-id="a0b57-107">目標</span><span class="sxs-lookup"><span data-stu-id="a0b57-107">Objectives</span></span>

* <span data-ttu-id="a0b57-108">在您的專案中新增一個按鈕</span><span class="sxs-lookup"><span data-stu-id="a0b57-108">Add a button to your project</span></span>
* <span data-ttu-id="a0b57-109">建立新的 “Reset Location” 函式，此函式會將棋子送回其原始位置</span><span class="sxs-lookup"><span data-stu-id="a0b57-109">Create a new “Reset Location” function that sends a piece back to its original location</span></span>
* <span data-ttu-id="a0b57-110">連結按鈕，以在按下按鈕時觸發新建立的函式</span><span class="sxs-lookup"><span data-stu-id="a0b57-110">Hook the button up to trigger the newly created function when pressed</span></span>

## <a name="create-a-function-to-reset-location"></a><span data-ttu-id="a0b57-111">建立用來重設位置的函式</span><span class="sxs-lookup"><span data-stu-id="a0b57-111">Create a function to reset location</span></span>

1.  <span data-ttu-id="a0b57-112">開啟 **WhiteKing**。</span><span class="sxs-lookup"><span data-stu-id="a0b57-112">Open **WhiteKing**.</span></span> <span data-ttu-id="a0b57-113">在 [我的藍圖]  面板中，按一下 [函式]  區段旁的 [+] 按鈕，以建立新的函式。</span><span class="sxs-lookup"><span data-stu-id="a0b57-113">In the **My Blueprint** panel, click the “+” button next to the **Functions** section to create a new function.</span></span> <span data-ttu-id="a0b57-114">將此函式命名為 “Reset Location”。</span><span class="sxs-lookup"><span data-stu-id="a0b57-114">Name this function “Reset Location”.</span></span> 

2.  <span data-ttu-id="a0b57-115">在新建立的 **Reset Location** 藍圖中，拖曳執行連接點並將其放在藍圖方格中的任一位置，以呼叫 **SetActorRelativeTransform** 節點。</span><span class="sxs-lookup"><span data-stu-id="a0b57-115">In your newly created **Reset Location** Blueprint, drag the execution pin and release anywhere on the Blueprint grid to call a **SetActorRelativeTransform** node.</span></span> <span data-ttu-id="a0b57-116">此函式會為動作項目設定與其父系相對的變形 (位置、旋轉和縮放)。</span><span class="sxs-lookup"><span data-stu-id="a0b57-116">This function sets the transform (location, rotation, and scale) of an actor relative to its parent.</span></span> <span data-ttu-id="a0b57-117">我們會使用此函式來重設棋盤上的國王位置，即使棋盤已從其原始位置移動也一樣。</span><span class="sxs-lookup"><span data-stu-id="a0b57-117">We’ll use this function to reset the king’s position on the board, even if the board has been moved from its original position.</span></span> <span data-ttu-id="a0b57-118">建立**製造變形**節點，其位置為 X = -26、Y = 4、Z = 0，然後將其連接至新的相對變形輸入。</span><span class="sxs-lookup"><span data-stu-id="a0b57-118">Create a **Make Transform** node with Location X = -26, Y = 4, Z = 0, and connect it to the New Relative Transform input.</span></span> 

![重設位置函式](images/unreal-uxt/5-function.PNG)

3.  <span data-ttu-id="a0b57-120">編譯並儲存 **WhiteKing**。</span><span class="sxs-lookup"><span data-stu-id="a0b57-120">Compile and Save **WhiteKing**.</span></span> <span data-ttu-id="a0b57-121">返回主視窗。</span><span class="sxs-lookup"><span data-stu-id="a0b57-121">Return to the Main window.</span></span> 

## <a name="add-a-button"></a><span data-ttu-id="a0b57-122">新增按鈕</span><span class="sxs-lookup"><span data-stu-id="a0b57-122">Add a button</span></span>

1.  <span data-ttu-id="a0b57-123">在您的 **Blueprints** 資料夾中，建立子類別為 SimpleButton 的新藍圖。</span><span class="sxs-lookup"><span data-stu-id="a0b57-123">In your **Blueprints** folder, create a new Blueprint that subclasses SimpleButton.</span></span> <span data-ttu-id="a0b57-124">SimpleButton 是 3D 按鈕藍圖動作項目，會作為 UX 工具外掛程式的一部分提供。</span><span class="sxs-lookup"><span data-stu-id="a0b57-124">SimpleButton is a 3D button Blueprint Actor that is provided as part of the UX Tools plugin.</span></span> <span data-ttu-id="a0b57-125">將此按鈕命名為 "ResetButton"，然後按兩下以開啟藍圖。</span><span class="sxs-lookup"><span data-stu-id="a0b57-125">Name this button “ResetButton” and double click to open the Blueprint.</span></span> 

![從 SimpleButton 中為新藍圖建立子類別](images/unreal-uxt/5-subclass.PNG)

2.  <span data-ttu-id="a0b57-127">在 [元件]  面板中，按一下 [PressableButton (繼承)]  。</span><span class="sxs-lookup"><span data-stu-id="a0b57-127">In the **Components** panel, click on **PressableButton (Inherited)**.</span></span> <span data-ttu-id="a0b57-128">在 [詳細資料] 面板中，捲動畫面直到您看見 [事件]  區段。</span><span class="sxs-lookup"><span data-stu-id="a0b57-128">In the Details panel, scroll until you see the **Events** section.</span></span> <span data-ttu-id="a0b57-129">按一下 [On Button Pressed (按下按鈕時)]  旁邊的綠色加號按鈕 - 這會將 [On Button Pressed]  事件新增至 Event Graph，並在按下按鈕時呼叫該事件。</span><span class="sxs-lookup"><span data-stu-id="a0b57-129">Click the green plus button next to **On Button Pressed**- this will add an **On Button Pressed** event to the Event Graph, which will be called when the button is pressed.</span></span> <span data-ttu-id="a0b57-130">從這裡開始，我們將要呼叫 WhiteKing 的 Reset Location 函式。</span><span class="sxs-lookup"><span data-stu-id="a0b57-130">From here, we’ll want to call our WhiteKing’s Reset Location function.</span></span> <span data-ttu-id="a0b57-131">若要這樣做，我們必須先取得層級中 WhiteKing 動作項目的參考。</span><span class="sxs-lookup"><span data-stu-id="a0b57-131">To do this, we’ll first need to get a reference to the WhiteKing Actor in our Level.</span></span> 

3.  <span data-ttu-id="a0b57-132">在 [我的藍圖]  面板中，尋找 [變數]  區段，然後按一下 [+]  按鈕以加入新的變數。</span><span class="sxs-lookup"><span data-stu-id="a0b57-132">In the **My Blueprint** panel, find the **Variables** section and click the **+** button to add a new variable.</span></span> <span data-ttu-id="a0b57-133">將此變數命名為 "WhiteKing"。</span><span class="sxs-lookup"><span data-stu-id="a0b57-133">Name this variable “WhiteKing”.</span></span> <span data-ttu-id="a0b57-134">在 [詳細資料] 面板中，選取 [變數類型]  旁的下拉式清單，並搜尋 "WhiteKing"，然後選取 [物件參考]  。</span><span class="sxs-lookup"><span data-stu-id="a0b57-134">In the Details panel, select the dropdown next to **Variable Type**, search for “WhiteKing”, and select the **Object Reference**.</span></span> <span data-ttu-id="a0b57-135">最後，勾選 [可編輯執行個體]  旁的方塊。</span><span class="sxs-lookup"><span data-stu-id="a0b57-135">Finally, check the box next to **Instance Editable**.</span></span> <span data-ttu-id="a0b57-136">這可讓您從主要層級設定變數。</span><span class="sxs-lookup"><span data-stu-id="a0b57-136">This will allow the variable to be set from the Main Level.</span></span> 

![建立變數](images/unreal-uxt/5-var.PNG)

4.  <span data-ttu-id="a0b57-138">將 WhiteKing 變數從 [我的藍圖] > [變數]  拖曳到 Simple Button Event Graph。</span><span class="sxs-lookup"><span data-stu-id="a0b57-138">Drag the WhiteKing variable from **My Blueprint > Variables** onto the Simple Button Event Graph.</span></span> <span data-ttu-id="a0b57-139">選擇 [取得 WhiteKing]  。</span><span class="sxs-lookup"><span data-stu-id="a0b57-139">Choose **Get WhiteKing**.</span></span> 

5.  <span data-ttu-id="a0b57-140">拖放 WhiteKing 輸出連接，以放置新的節點。</span><span class="sxs-lookup"><span data-stu-id="a0b57-140">Drag the WhiteKing output pin and release to place a new node.</span></span> <span data-ttu-id="a0b57-141">選取 **Reset Location** 函式。</span><span class="sxs-lookup"><span data-stu-id="a0b57-141">Select the **Reset Location** function.</span></span> <span data-ttu-id="a0b57-142">最後，將輸出執行連接點從 [On Button Pressed]  拖曳至 [Reset Location]  上的輸入執行連接點。</span><span class="sxs-lookup"><span data-stu-id="a0b57-142">Finally, drag the outgoing execution pin from **On Button Pressed** to the incoming execution pin on **Reset Location**.</span></span> <span data-ttu-id="a0b57-143">**編譯**並**儲存** ResetButton 藍圖，然後回到主視窗。</span><span class="sxs-lookup"><span data-stu-id="a0b57-143">**Compile** and **Save** the ResetButton Blueprint, then return to the Main window.</span></span> 

![從 On Button Pressed 呼叫 Reset Location 函式](images/unreal-uxt/5-callresetloc.PNG)

6.  <span data-ttu-id="a0b57-145">將 **SimpleButton** 拖曳到檢視區，並將其位置設定為 X = 50、Y = -25、Z = 10。</span><span class="sxs-lookup"><span data-stu-id="a0b57-145">Drag **SimpleButton** into the viewport and set its location to X = 50, Y = -25, Z = 10.</span></span> <span data-ttu-id="a0b57-146">在 [預設值]  底下，將 WhiteKing 變數的值設定為 **WhiteKing**。</span><span class="sxs-lookup"><span data-stu-id="a0b57-146">Under **Default**, set the value of the WhiteKing variable to **WhiteKing**.</span></span>

![設定變數](images/unreal-uxt/5-buttonlevel.PNG)

<span data-ttu-id="a0b57-148">您現在有一個混合實境應用程式，其中包含可抓取的棋子和棋盤，還有一個功能完整的按鈕，會在按下時重設棋子的位置。</span><span class="sxs-lookup"><span data-stu-id="a0b57-148">You now have a mixed reality app with a grabbable chess piece and board, as well as a fully functioning button that will reset the piece’s location when pressed.</span></span> <span data-ttu-id="a0b57-149">您可以在 [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) 上找到此時完成的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0b57-149">The completed app up to this point can be found on [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp).</span></span> <span data-ttu-id="a0b57-150">您可以隨意進行超越本教學課程範圍的內容並設定其餘的棋子，讓整個棋盤都可在使用者按下按鈕時重設。</span><span class="sxs-lookup"><span data-stu-id="a0b57-150">Feel free to go beyond this tutorial and set up the remainder of the chess pieces, so that the entire board is reset when the user presses the button.</span></span>

![檢視區中的最終場景](images/unreal-uxt/5-endscene.PNG)

[<span data-ttu-id="a0b57-152">下一節：6.封裝並部署至裝置或模擬器</span><span class="sxs-lookup"><span data-stu-id="a0b57-152">Next Section: 6. Packaging & deploying to device or emulator</span></span>](unreal-uxt-ch6.md)