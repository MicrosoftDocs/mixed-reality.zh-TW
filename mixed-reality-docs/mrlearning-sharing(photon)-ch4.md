---
title: 多使用者功能教學課程-4。 與多個使用者共用物件移動
description: 完成此課程，以瞭解如何在 HoloLens 2 應用程式中執行多使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: f523aabd74b9267b3f7f5024d8af46110e43c32a
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334279"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="7f227-105">4. 與多個使用者共用物件移動</span><span class="sxs-lookup"><span data-stu-id="7f227-105">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="7f227-106">在本教學課程中，您將瞭解如何共用物件的移動，讓共用會話的所有參與者都可以共同作業及查看彼此的互動。</span><span class="sxs-lookup"><span data-stu-id="7f227-106">In this Tutorial, you'll learn how to share the movements of objects so that all participants of a shared session can collaborate and view each others' interactions.</span></span> <span data-ttu-id="7f227-107">這一課是以[基本模組教學](mrlearning-base.md)課程中建立的陰曆啟動器為基礎。</span><span class="sxs-lookup"><span data-stu-id="7f227-107">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

## <a name="objectives"></a><span data-ttu-id="7f227-108">目標</span><span class="sxs-lookup"><span data-stu-id="7f227-108">Objectives</span></span>

- <span data-ttu-id="7f227-109">帶入陰曆啟動器作為要共用的3D 模型</span><span class="sxs-lookup"><span data-stu-id="7f227-109">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="7f227-110">設定專案以共用3D 模型的移動</span><span class="sxs-lookup"><span data-stu-id="7f227-110">Configure your project to share the movements of the 3D model</span></span>
- <span data-ttu-id="7f227-111">瞭解如何建立基本的多使用者協同作業應用程式</span><span class="sxs-lookup"><span data-stu-id="7f227-111">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="instructions"></a><span data-ttu-id="7f227-112">指示</span><span class="sxs-lookup"><span data-stu-id="7f227-112">Instructions</span></span>

1. <span data-ttu-id="7f227-113">從上一課（Control + S）儲存場景。</span><span class="sxs-lookup"><span data-stu-id="7f227-113">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="7f227-114">您可以將它命名為 HLSharedProjectMainPart4，以便在需要時更容易找到。</span><span class="sxs-lookup"><span data-stu-id="7f227-114">You can name it HLSharedProjectMainPart4.unity so it's easier to find when you need it.</span></span>

2. <span data-ttu-id="7f227-115">從 [專案] 視窗的 [資產-> 腳本] 資料夾中，按兩下 [GenericNetSync]，在 Visual Studio 或您使用的程式碼編輯器中開啟它。</span><span class="sxs-lookup"><span data-stu-id="7f227-115">From the Project window, in the Assets->Scripts folder, double-click GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  

    ![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="7f227-117">在行34和38上，移除 "//" 以啟用您將在本課程中使用之資料表的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7f227-117">On Lines 34 and 38, remove "//" to activate the code for the table that you will use in this lesson.</span></span> <span data-ttu-id="7f227-118">接下來，儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="7f227-118">Next, save the file.</span></span>

    ![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="7f227-120">在 [專案] 視窗中，按兩下 [資產-> 腳本] 資料夾中的 PhotonRoom.cs 檔案，在 Visual Studio 中將它開啟。</span><span class="sxs-lookup"><span data-stu-id="7f227-120">In the Project window, double-click the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span>

    ![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="7f227-122">就像在步驟3中，我們需要移除 "//" 以啟動第25、26和106行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7f227-122">Just like in Step 3, we need to remove "//" to activate the code at Lines 25, 26, and 106.</span></span>

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png)

    ![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="7f227-125">在 [階層] 視圖中，選取 [NetworkRoom] 物件。</span><span class="sxs-lookup"><span data-stu-id="7f227-125">In the Hierarchy view, select the NetworkRoom object.</span></span>

    ![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. <span data-ttu-id="7f227-127">在 專案 視圖中，流覽至 資產-> 資源-> Prefabs。</span><span class="sxs-lookup"><span data-stu-id="7f227-127">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="7f227-128">首先，將資料表 prefab 拖放到 PhotonRoom 類別上的 Tableprefab 位置。</span><span class="sxs-lookup"><span data-stu-id="7f227-128">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="7f227-129">接下來，將 RocketLauncherCompleteVariantprefab 拖放到 PhotonRoom 類別上的模組 Prefab 位置。</span><span class="sxs-lookup"><span data-stu-id="7f227-129">Next, drag and drop the RocketLauncherCompleteVariantprefab to the Module Prefab slot on the PhotonRoom class.</span></span>

    ![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

    >[!NOTE]
    ><span data-ttu-id="7f227-131">如果您按一下其中一個 prefab 物件和版本，則偵測器會切換至該物件。</span><span class="sxs-lookup"><span data-stu-id="7f227-131">If you click one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="7f227-132">按一下、拖放，然後將每個物件釋放到適當的位置。</span><span class="sxs-lookup"><span data-stu-id="7f227-132">Click, drag, drop, and release each object to its appropriate slot.</span></span>

8. <span data-ttu-id="7f227-133">按一下 [MixedRealityPlayspace] 左邊的箭號，然後將子遊戲物件 MainCamera 向下移動到 SharedPlayground prefab。</span><span class="sxs-lookup"><span data-stu-id="7f227-133">Click the arrow to the left of MixedRealityPlayspace and move the child game object MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="7f227-134">接下來，選取 [prefab] 來刪除 prefab，MixedRealityPlayspace，然後在鍵盤上按一下 [刪除]）。</span><span class="sxs-lookup"><span data-stu-id="7f227-134">Next, delete the prefab, MixedRealityPlayspace by selecting the prefab and tap "delete" on your keyboard).</span></span>

    ![Module3hapter4step5im](images/module3chapter4step5im.PNG)

    >[!NOTE]
    ><span data-ttu-id="7f227-136">請確定主要相機和 SharedPlayground 位置都設定為0，0，0。</span><span class="sxs-lookup"><span data-stu-id="7f227-136">Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="7f227-137">選取 [SharedPlayground] 物件，並以滑鼠右鍵按一下滑鼠，選擇 [建立空的] 選項，將空白遊戲物件建立為 "SharedPlayground" 遊戲物件的子系。</span><span class="sxs-lookup"><span data-stu-id="7f227-137">Select "SharedPlayground" object and right click the mouse to choose "create empty" option to create an empty game object as a child of "SharedPlayground" game object.</span></span>

   ![Module3chapter4step6im](images/module3chapter4step6im.PNG)

10. <span data-ttu-id="7f227-139">在您的階層中選取新的物件後，請在 [偵測器] 面板中將物件的名稱變更為 TableAnchor。</span><span class="sxs-lookup"><span data-stu-id="7f227-139">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="7f227-140">此外，按一下 [新增元件]，並搜尋 TableAnchor 元件。</span><span class="sxs-lookup"><span data-stu-id="7f227-140">Also, click Add Component and search for the TableAnchor component.</span></span> <span data-ttu-id="7f227-141">選取它，並將它新增至物件。</span><span class="sxs-lookup"><span data-stu-id="7f227-141">Select it and add it to the object.</span></span>

    ![Module3Chapter4step7im](images/module3chapter4step7im.PNG)

11. <span data-ttu-id="7f227-143">從 [Prefabs] 資料夾的 [專案] 面板中，將資料表 prefab 拖曳至您剛才建立的 "TableAnchor" 子物件。</span><span class="sxs-lookup"><span data-stu-id="7f227-143">From the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object that you just created.</span></span>

    ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

12. <span data-ttu-id="7f227-145">在 DebugWindow 物件中，將 [寬度] 變更為 [50]，並將 [高度] 變更為20。</span><span class="sxs-lookup"><span data-stu-id="7f227-145">In the DebugWindow object, change the width to 50 and the height to 20.</span></span>

    ![Module3Chapter4step9im](images/module3chapter4step11im.PNG)

## <a name="congratulations"></a><span data-ttu-id="7f227-147">恭喜您</span><span class="sxs-lookup"><span data-stu-id="7f227-147">Congratulations</span></span>

<span data-ttu-id="7f227-148">完成後，請尋找以尋找陰曆課程模組。</span><span class="sxs-lookup"><span data-stu-id="7f227-148">Once this is complete, look around to find the lunar module.</span></span> <span data-ttu-id="7f227-149">在此之後，加入 Unity 專案的所有使用者都可以移動農曆啟動程式。</span><span class="sxs-lookup"><span data-stu-id="7f227-149">After this, all users that join your Unity project can move the lunar launcher around.</span></span>  <span data-ttu-id="7f227-150">所有的移動都會同步處理，讓每個使用者都可以看到彼此的互動。</span><span class="sxs-lookup"><span data-stu-id="7f227-150">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="7f227-151">這些概念可做為全功能、共用共同作業體驗的基本組建區塊。</span><span class="sxs-lookup"><span data-stu-id="7f227-151">These concepts serve as the fundamental building blocks for full-featured, shared collaboration experiences.</span></span>

<span data-ttu-id="7f227-152">雖然所有使用者都是以共用體驗的一部分進行連線，而且可以查看物件的相對移動，但應用程式仍無法精確地對齊虛擬人偶和物件，讓本機使用者無法看到彼此和物件位於實體世界。</span><span class="sxs-lookup"><span data-stu-id="7f227-152">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users were not able see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="7f227-153">為了錨定本機共用體驗，每個裝置都需要對實體環境有共同的瞭解。</span><span class="sxs-lookup"><span data-stu-id="7f227-153">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="7f227-154">在此課程模組中，我們將使用[Azure 空間錨點](<https://azure.microsoft.com//services/spatial-anchors/>)（ASA）來達成此目的，其將在下一課中實行。</span><span class="sxs-lookup"><span data-stu-id="7f227-154">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) which will be implemented in the next lesson.</span></span>

<span data-ttu-id="7f227-155">在繼續進行下一課之前，我們必須先完成 ASA 學習課程模組，其中涵蓋 ASA 基本概念、Azure 帳戶和資源建立，以及我們在將此整合到我們的共用體驗之前所需的其他基本建築物組塊。</span><span class="sxs-lookup"><span data-stu-id="7f227-155">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, as well as other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="7f227-156">[下一課： 5. 將 Azure 空間錨點整合到共用體驗中](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="7f227-156">[Next Lesson: 5. Integration Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch5.md)</span></span>
