---
title: HoloLens 2 的 MR 學習共用模組
description: 完成此課程, 以瞭解如何在 HoloLens 2 應用程式中執行多使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 529a888dfa00180ca908fbc7f4c62f9a9086c661
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460323"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="cd675-104">4.與多個使用者共用物件移動</span><span class="sxs-lookup"><span data-stu-id="cd675-104">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="cd675-105">在本教學課程中, 我們將瞭解如何共用物件的移動, 讓共用會話的所有參與者都可以共同合作, 並查看彼此的互動。</span><span class="sxs-lookup"><span data-stu-id="cd675-105">In this Tutorial, we learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="cd675-106">這一課是以[基本模組教學](mrlearning-base.md)課程中建立的陰曆啟動器為基礎。</span><span class="sxs-lookup"><span data-stu-id="cd675-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="cd675-107">目標</span><span class="sxs-lookup"><span data-stu-id="cd675-107">Objectives:</span></span>

- <span data-ttu-id="cd675-108">帶入陰曆啟動器作為要共用的3D 模型</span><span class="sxs-lookup"><span data-stu-id="cd675-108">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="cd675-109">將您的專案設定為共用3D 模型的移動。</span><span class="sxs-lookup"><span data-stu-id="cd675-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="cd675-110">瞭解如何建立基本的多使用者協同作業應用程式</span><span class="sxs-lookup"><span data-stu-id="cd675-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="cd675-111">指示</span><span class="sxs-lookup"><span data-stu-id="cd675-111">Instructions</span></span>


1. <span data-ttu-id="cd675-112">從上一課 (Control + S) 儲存場景。</span><span class="sxs-lookup"><span data-stu-id="cd675-112">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="cd675-113">您可以將它命名為 HLSharedProjectMainPart4, 以便在需要時更容易找到。</span><span class="sxs-lookup"><span data-stu-id="cd675-113">You can name it, HLSharedProjectMainPart4.unity, so that it's easier to find when you need it.</span></span>

2. <span data-ttu-id="cd675-114">從 [專案] 視窗的 [資產-> 腳本] 資料夾中, 按兩下 [GenericNetSync], 在 Visual Studio 或您使用的程式碼編輯器中開啟它。</span><span class="sxs-lookup"><span data-stu-id="cd675-114">From the Project window, in the Assets->Scripts folder, double click on GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  

![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="cd675-116">在行34和38上, 移除//以啟動我們將在此課程中使用之資料表的程式碼。</span><span class="sxs-lookup"><span data-stu-id="cd675-116">On Lines 34 and 38, remove the // to activate the code for the table that we will use in this lesson.</span></span> <span data-ttu-id="cd675-117">接下來, 儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="cd675-117">next, Save the file.</span></span> 

![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="cd675-119">在 [專案] 視窗中, 按兩下 [資產-> 腳本] 資料夾中的 PhotonRoom.cs 檔案, 在 Visual Studio 中將它開啟。</span><span class="sxs-lookup"><span data-stu-id="cd675-119">In the Project window, double click on the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span> 

![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="cd675-121">就像在步驟3中, 我們需要移除//以在第25、26和106行啟用程式碼。</span><span class="sxs-lookup"><span data-stu-id="cd675-121">Just like in Step 3, we need to remove the // to activate the code at Lines 25, 26, and 106.</span></span>

![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png) 

![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="cd675-124">在 [階層] 視圖中, 選取 [NetworkRoom] 物件。</span><span class="sxs-lookup"><span data-stu-id="cd675-124">In the Hierarchy view, select the NetworkRoom object.</span></span>

![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. <span data-ttu-id="cd675-126">在 專案 視圖中, 流覽至 資產-> 資源-> Prefabs。</span><span class="sxs-lookup"><span data-stu-id="cd675-126">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="cd675-127">首先, 將資料表 prefab 拖放到 PhotonRoom 類別上的 Tableprefab 位置。</span><span class="sxs-lookup"><span data-stu-id="cd675-127">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="cd675-128">接下來, 將 RocketLauncherCompleteVariantprefab 拖放到 PhotonRoom 類別上的模組 Prefab 位置。</span><span class="sxs-lookup"><span data-stu-id="cd675-128">Next drag and drop the RocketLauncherCompleteVariantprefab to the Module Prefab slot on the PhotonRoom class.</span></span>

![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

   <span data-ttu-id="cd675-130">注意:如果您按一下其中一個 prefab 物件和 [釋放], 則偵測器會切換至該物件。</span><span class="sxs-lookup"><span data-stu-id="cd675-130">Note: If you click on one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="cd675-131">按一下、拖放, 然後將每個物件釋放到適當的位置。</span><span class="sxs-lookup"><span data-stu-id="cd675-131">Click, drag, drop, and release each object to its appropriate slot.</span></span>

8. <span data-ttu-id="cd675-132">按一下 [MixedRealityPlayspace] 左邊的箭號, 然後將 [子遊戲] 物件向下 MainCamera 至 [SharedPlayground] prefab。</span><span class="sxs-lookup"><span data-stu-id="cd675-132">Click the arrow to the left of MixedRealityPlayspace, and move the child game object, MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="cd675-133">接下來, 刪除 prefab、MixedRealityPlayspace、刪除、選取 prefab, 然後在您的鍵盤上點一下 [刪除]。</span><span class="sxs-lookup"><span data-stu-id="cd675-133">Next, delete the prefab, MixedRealityPlayspace, to delete, select the prefab, and tap "delete" on your keyboard).</span></span>
<span data-ttu-id="cd675-134">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span><span class="sxs-lookup"><span data-stu-id="cd675-134">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span></span>

><span data-ttu-id="cd675-135">注意:請確定主要相機和 SharedPlayground 位置都設定為 0, 0, 0。</span><span class="sxs-lookup"><span data-stu-id="cd675-135">Note:  Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>
>

9. <span data-ttu-id="cd675-136">建立新的遊戲物件集, 做為 SharedPlayground 父物件的子物件, 以建立新的物件。</span><span class="sxs-lookup"><span data-stu-id="cd675-136">Create a new game object set as a child object to the SharedPlayground parent object to create a new object.</span></span> <span data-ttu-id="cd675-137">以滑鼠右鍵按一下父物件, 然後選取 [建立空的]。</span><span class="sxs-lookup"><span data-stu-id="cd675-137">Right click on the parent object, and select Create Empty.</span></span> 

10. <span data-ttu-id="cd675-138">在您的階層中選取新的物件後, 請在 [偵測器] 面板中將物件的名稱變更為 TableAnchor。</span><span class="sxs-lookup"><span data-stu-id="cd675-138">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="cd675-139">此外, 按一下 [新增元件], 然後搜尋 TableAnchor 元件。</span><span class="sxs-lookup"><span data-stu-id="cd675-139">Also, click Add Component, and search for the TableAnchor component.</span></span> <span data-ttu-id="cd675-140">選取它, 並將它新增至物件。</span><span class="sxs-lookup"><span data-stu-id="cd675-140">Select it and add it to the object.</span></span> 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

11. <span data-ttu-id="cd675-142">現在, 從 [Prefabs] 資料夾的 [專案] 面板中, 將資料表 prefab 拖曳至您剛才建立的 "TableAnchor" 子物件。</span><span class="sxs-lookup"><span data-stu-id="cd675-142">Now from the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object you just created.</span></span>

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

12. <span data-ttu-id="cd675-144">最後, 在 DebugWindow 物件中, 將 [寬度] 變更為 50, 並將 [高度] 變更為20。</span><span class="sxs-lookup"><span data-stu-id="cd675-144">Finally, in the DebugWindow object, change the width to 50 and the height to 20.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)

## <a name="congratulations"></a><span data-ttu-id="cd675-146">恭喜！</span><span class="sxs-lookup"><span data-stu-id="cd675-146">Congratulations</span></span>


<span data-ttu-id="cd675-147">完成後, 加入 Unity 專案的所有使用者都可以移動陰曆啟動器。</span><span class="sxs-lookup"><span data-stu-id="cd675-147">Once this is complete, all users that join your Unity project can move the lunar launcher around.</span></span> <span data-ttu-id="cd675-148">所有的移動都會同步處理, 讓每個使用者都可以看到彼此的互動。</span><span class="sxs-lookup"><span data-stu-id="cd675-148">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="cd675-149">這些概念可做為全功能、共用共同作業體驗的基本組建區塊。</span><span class="sxs-lookup"><span data-stu-id="cd675-149">These concepts serve as the fundamental building blocks for full-featured, shared collaboration experiences.</span></span> 

<span data-ttu-id="cd675-150">雖然所有使用者都是以共用體驗的一部分進行連線, 而且可以查看物件的相對移動, 但應用程式仍無法精確地對齊虛擬人偶和物件, 讓本機使用者可以在實體中的相同位置看到彼此和物件成為.</span><span class="sxs-lookup"><span data-stu-id="cd675-150">Although all users are connected as part of a shared experience, and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="cd675-151">為了錨定本機共用體驗, 每個裝置都需要對實體環境有共同的瞭解。</span><span class="sxs-lookup"><span data-stu-id="cd675-151">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="cd675-152">在此課程模組中, 我們將使用將在下一課中實行的[Azure 空間錨點](<https://azure.microsoft.com/en-us/services/spatial-anchors/>)(ASA) 來達到此目的。</span><span class="sxs-lookup"><span data-stu-id="cd675-152">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) that will be implemented in the next lesson.</span></span>

<span data-ttu-id="cd675-153">在繼續進行下一課之前, 我們必須先完成 ASA 學習課程模組, 其中涵蓋 ASA 基本概念、Azure 帳戶和資源建立, 以及其他所需的基本建築物組塊, 才可將其整合到我們的共用體驗。</span><span class="sxs-lookup"><span data-stu-id="cd675-153">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="cd675-154">[下一課：共用 (Photon) 第5課](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="cd675-154">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>

