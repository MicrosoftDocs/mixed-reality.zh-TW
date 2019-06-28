---
title: 學習模組共用 HoloLens 2 MR
description: 完成這個課程來了解如何實作 HoloLens 2 應用程式內的多使用者分享的經驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: d5bed61f5ffc1d3b4efed96f47c3568fbf3a2948
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416009"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a><span data-ttu-id="7a890-104">同步處理共用物件的移動</span><span class="sxs-lookup"><span data-stu-id="7a890-104">Synchronizing the Movements of Shared Objects</span></span>

<span data-ttu-id="7a890-105">在這一課中，我們將了解如何共用物件的移動，以便在共用的工作階段的所有參與者都可以一起共同作業，並檢視其他人互動。</span><span class="sxs-lookup"><span data-stu-id="7a890-105">In this lesson, we will learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="7a890-106">這一課為建置基礎所建置的一部分陰曆啟動器[基底模組的教學課程](mrlearning-base.md)。</span><span class="sxs-lookup"><span data-stu-id="7a890-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="7a890-107">目標：</span><span class="sxs-lookup"><span data-stu-id="7a890-107">Objectives:</span></span>

- <span data-ttu-id="7a890-108">將 3D 模型到共用陰曆啟動器</span><span class="sxs-lookup"><span data-stu-id="7a890-108">Bring in the Lunar Launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="7a890-109">將專案設定為共用的 3D 模型的移動。</span><span class="sxs-lookup"><span data-stu-id="7a890-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="7a890-110">了解如何建置基本的多使用者共同作業應用程式</span><span class="sxs-lookup"><span data-stu-id="7a890-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="7a890-111">指示</span><span class="sxs-lookup"><span data-stu-id="7a890-111">Instructions</span></span>

1. <span data-ttu-id="7a890-112">在上一課 （control + S） 中儲存的場景。</span><span class="sxs-lookup"><span data-stu-id="7a890-112">Save the scene from the previous lesson (control+S).</span></span> <span data-ttu-id="7a890-113">您可能會為它命名"HLSharedProjectMainPart4.unity 」 讓您可更輕鬆地尋找當您再次需要它。</span><span class="sxs-lookup"><span data-stu-id="7a890-113">You may name it "HLSharedProjectMainPart4.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="7a890-114">在 [專案] 視窗中，在資產中 > Scripts 資料夾中，按兩下 GenericNetSync 在 Visual Studio，或用過程式碼會使用的編輯器中開啟它。</span><span class="sxs-lookup"><span data-stu-id="7a890-114">In the Project window, in the Assets > Scripts folder, double click on GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  ![](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="7a890-115">同行 34 和 38，移除"/ / 」 啟用程式碼，我們將在這一課使用的資料表。</span><span class="sxs-lookup"><span data-stu-id="7a890-115">On lines 34 and 38, remove the "//" to activate the code for the Table that we will use in this lesson.</span></span>  <span data-ttu-id="7a890-116">然後儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="7a890-116">Then Save the file.</span></span> ![](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="7a890-117">在 專案 視窗中，按兩下 在資產中 PhotonRoom.cs 歸檔 > 若要再次開啟 Visual Studio 中的 指令碼 資料夾。</span><span class="sxs-lookup"><span data-stu-id="7a890-117">In the project window, double click on the PhotonRoom.cs file in the Assets > Scripts folder to again open it in Visual Studio.</span></span> ![](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="7a890-118">就像在步驟的 3 中我們需要移除"/ /"啟用位於第 25、 26 和 106 行程式碼。![](images/module3chapter4updatestep5a.png)</span><span class="sxs-lookup"><span data-stu-id="7a890-118">Just like in step 3 we need to remove the "//" to activate the code at lines 25, 26, and 106.![](images/module3chapter4updatestep5a.png)</span></span> ![](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="7a890-119">在階層檢視中，選取 NetworkRoom 物件。![](images/module3chapter4updatestep6.png)</span><span class="sxs-lookup"><span data-stu-id="7a890-119">In the Hierarchy view, select the NetworkRoom object.![](images/module3chapter4updatestep6.png)</span></span>

7. <span data-ttu-id="7a890-120">在 專案 檢視中，瀏覽至 資產 > 資源 > Prefabs。</span><span class="sxs-lookup"><span data-stu-id="7a890-120">In the project view, navigate to Assets > Resources > Prefabs.</span></span> <span data-ttu-id="7a890-121">首先，拖放資料表 prefab PhotonRoom 類別上的 「 Tableprefab"插槽。</span><span class="sxs-lookup"><span data-stu-id="7a890-121">First, drag and drop the Table prefab to the "Tableprefab" slot on the PhotonRoom class.</span></span> <span data-ttu-id="7a890-122">接下來將拖放 LunarModule prefab PhotonRoom 類別上的 「 模組 Prefab"插槽。</span><span class="sxs-lookup"><span data-stu-id="7a890-122">Next drag and drop the LunarModule prefab to the "Module Prefab" slot on the PhotonRoom class.</span></span> ![](images/module3chapter4updatestep7.png)

   <span data-ttu-id="7a890-123">注意:如果您按一下其中一個 prefab 物件和版本，偵測器會切換至該物件。</span><span class="sxs-lookup"><span data-stu-id="7a890-123">Note: If you click on one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="7a890-124">按一下、 拖放並釋放每個物件至其適當的位置。</span><span class="sxs-lookup"><span data-stu-id="7a890-124">Click, drag, drop and release each object to its appropriate slot.</span></span>



8. <span data-ttu-id="7a890-125">現在，按一下 「 MixedRealityPlayspace 」 左邊的箭號，然後向下移動子遊戲物件、 「 MainCamera"到"SharedPlayground"prefab。</span><span class="sxs-lookup"><span data-stu-id="7a890-125">Now, click the arrow to the left of "MixedRealityPlayspace" and move the child game object, "MainCamera" down into the "SharedPlayground" prefab.</span></span> <span data-ttu-id="7a890-126">然後，刪除 prefab"MixedRealityPlayspace"（若要刪除選取的 prefab，點選您鍵盤上的 [刪除]）。</span><span class="sxs-lookup"><span data-stu-id="7a890-126">Then, delete the prefab "MixedRealityPlayspace" (to delete, select the prefab and tap "delete" on your keyboard).</span></span>

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

<span data-ttu-id="7a890-128">注意：請確定將 Main Camera 與 SharedPlayground 的位置會設定成 0,0,0。</span><span class="sxs-lookup"><span data-stu-id="7a890-128">note:  Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="7a890-129">建立新的遊戲物件設定為子物件 」 SharedPlayground"父物件 （用於建立新的物件，父物件，以滑鼠右鍵按一下並選取 [建立空白]）。</span><span class="sxs-lookup"><span data-stu-id="7a890-129">Create a new game object set as a child object to the "SharedPlayground" parent object (to create a new object, right click on the parent object, and select "create  empty").</span></span> 

10. <span data-ttu-id="7a890-130">在您階層中選取新的物件，將物件的名稱變更為"TableAnchor 」，在 [偵測器] 面板。</span><span class="sxs-lookup"><span data-stu-id="7a890-130">With the new object selected in your hierarchy, change the name of the object to "TableAnchor" in the inspector panel.</span></span> <span data-ttu-id="7a890-131">此外，按一下 [新增元件]，並搜尋"TableAnchor 」 元件。</span><span class="sxs-lookup"><span data-stu-id="7a890-131">Also, click "add component" and search for the "TableAnchor" component.</span></span> <span data-ttu-id="7a890-132">選取它，並將它新增至物件。</span><span class="sxs-lookup"><span data-stu-id="7a890-132">Select it and add it to the object.</span></span> 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> <span data-ttu-id="7a890-134">注意： 設定定位為 x = 1，y = 0.55 和 z = 2。</span><span class="sxs-lookup"><span data-stu-id="7a890-134">note: set the positioning to x=1, y=-0.55, and z=2.</span></span> <span data-ttu-id="7a890-135">此外，設定 旋轉角度 y = 90。</span><span class="sxs-lookup"><span data-stu-id="7a890-135">Also, set the rotation to y=90.</span></span> 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. <span data-ttu-id="7a890-137">現在在 [專案] 面板中，在 「 prefabs"資料夾中，拖曳至 「 資料表 」 prefab 您剛才建立的 「 TableAnchor"子物件。</span><span class="sxs-lookup"><span data-stu-id="7a890-137">Now in the project panel, in the "prefabs" folder, drag the "table" prefab into the "TableAnchor" child object you just created.</span></span>

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. <span data-ttu-id="7a890-139">最後，如果在 「 DebugWindow 」 物件中，您可以變更寬度為 80 及高度設為 10。</span><span class="sxs-lookup"><span data-stu-id="7a890-139">Finally, in the "DebugWindow" object, change the width to 80 and the height to 10.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a><span data-ttu-id="7a890-141">恭喜！</span><span class="sxs-lookup"><span data-stu-id="7a890-141">Congratulations</span></span>

<span data-ttu-id="7a890-142">這項操作完成，加入您的 Unity 專案的所有使用者可四處都移動陰曆的啟動器。</span><span class="sxs-lookup"><span data-stu-id="7a890-142">Once this is complete, all users that join your Unity project can move the Lunar Launcher around.</span></span> <span data-ttu-id="7a890-143">所有的移動會同步處理，讓每位使用者可以看到其他人互動。</span><span class="sxs-lookup"><span data-stu-id="7a890-143">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="7a890-144">這些概念做為基本建置組塊的完整共用的共同作業體驗。</span><span class="sxs-lookup"><span data-stu-id="7a890-144">These concepts serve as the foundational building blocks for full-featured shared collaboration experiences.</span></span> 

<span data-ttu-id="7a890-145">雖然所有的使用者連接共用體驗的一部分，而且可以看到的物件相對的移動，應用程式是仍然無法正確對齊虛擬人偶和物件，以便在實體內的相同位置的物件與彼此，請參閱 < 本機使用者世界。</span><span class="sxs-lookup"><span data-stu-id="7a890-145">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="7a890-146">若要錨定在本機的共用的體驗，每個裝置會需要的實體環境的共識。</span><span class="sxs-lookup"><span data-stu-id="7a890-146">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="7a890-147">在這個模組中，我們將會達到此目的使用[Azure 空間的錨點](<https://azure.microsoft.com/en-us/services/spatial-anchors/>)(ASA)，這將在下一課中實作。</span><span class="sxs-lookup"><span data-stu-id="7a890-147">In this module, we will achieve this using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), which will be implemented in the next lesson.</span></span>

<span data-ttu-id="7a890-148">下一課之前，我們必須完成 ASA 的學習模組，將會討論 ASA 基本概念，Azure 帳戶和資源建立，而其他基本的建築物區塊需要之前我們將這整合到我們分享經驗。</span><span class="sxs-lookup"><span data-stu-id="7a890-148">Before proceeding to the next lesson, we will need to complete the ASA Learning Module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="7a890-149">[下一課：第 5 課 Sharing(Photon)](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="7a890-149">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>

