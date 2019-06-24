---
title: 學習模組共用 HoloLens 2 MR
description: 完成這個課程來了解如何實作 HoloLens 2 應用程式內的多使用者分享的經驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: a67eaef45582054b62198a563f0ee01724fd60db
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326999"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a><span data-ttu-id="b3e15-104">同步處理共用物件的移動</span><span class="sxs-lookup"><span data-stu-id="b3e15-104">Synchronizing the Movements of Shared Objects</span></span>

<span data-ttu-id="b3e15-105">在這一課中，我們將了解如何共用物件的移動，以便在共用的工作階段的所有參與者都可以一起共同作業，並檢視其他人互動。</span><span class="sxs-lookup"><span data-stu-id="b3e15-105">In this lesson, we will learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="b3e15-106">這一課為建置基礎所建置的一部分陰曆啟動器[基底模組的教學課程](mrlearning-base.md)。</span><span class="sxs-lookup"><span data-stu-id="b3e15-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="b3e15-107">目標：</span><span class="sxs-lookup"><span data-stu-id="b3e15-107">Objectives:</span></span>

- <span data-ttu-id="b3e15-108">作為要共用的 3D 模型匯入已完成的陰曆啟動器</span><span class="sxs-lookup"><span data-stu-id="b3e15-108">Import the completed Lunar Launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="b3e15-109">將專案設定為共用的 3D 模型的移動。</span><span class="sxs-lookup"><span data-stu-id="b3e15-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="b3e15-110">了解如何建置基本的多使用者共同作業應用程式</span><span class="sxs-lookup"><span data-stu-id="b3e15-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="b3e15-111">指示</span><span class="sxs-lookup"><span data-stu-id="b3e15-111">Instructions</span></span>

1. <span data-ttu-id="b3e15-112">在上一課 （control + S） 中儲存的場景。</span><span class="sxs-lookup"><span data-stu-id="b3e15-112">Save the scene from the previous lesson (control+S).</span></span> <span data-ttu-id="b3e15-113">您可能會為它命名"HLSharedProjectMainPart4.unity 」 讓您可更輕鬆地尋找當您再次需要它。</span><span class="sxs-lookup"><span data-stu-id="b3e15-113">You may name it "HLSharedProjectMainPart4.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="b3e15-114">刪除"NetworkLobby 」 物件 （方法是選取它，然後按下 delete 鍵）。</span><span class="sxs-lookup"><span data-stu-id="b3e15-114">Delete the "NetworkLobby" object (by selecting it and pressing delete).</span></span> <span data-ttu-id="b3e15-115">此外，進入 「 prefabs"資料夾，從第 2 課，並從該處也刪除 「 NetworkLobby"prefab。</span><span class="sxs-lookup"><span data-stu-id="b3e15-115">Also, go into the "prefabs" folder from lesson 2 and delete the "NetworkLobby" prefab from there as well.</span></span>

![Module3Chapter4tep2im](images/module3chapter4step2im.PNG)

3. <span data-ttu-id="b3e15-117">匯入新的自訂封裝 （例如從第 2 課步驟 2），並匯入[LunarModule.unitypackage](linkforModule1 lesson with the lunar module)而[NetworkLobbyReplacement.unitypackage。](linkforNetworklobbyreplacement package here)</span><span class="sxs-lookup"><span data-stu-id="b3e15-117">Import a new custom package (like step 2 from the lesson 2) and import the [LunarModule.unitypackage](linkforModule1 lesson with the lunar module) and the [NetworkLobbyReplacement.unitypackage.](linkforNetworklobbyreplacement package here)</span></span>

![Module3Chapter4step3im](images/module3chapter4step3im.PNG)

4. <span data-ttu-id="b3e15-119">現在，在 「 prefabs"資料夾中，拖曳至新的 「 NetworkLobby"prefab 階層。</span><span class="sxs-lookup"><span data-stu-id="b3e15-119">Now, in the "prefabs" folder, drag the new "NetworkLobby" prefab into the hierarchy .</span></span> 

![Module3hapter4step4im](images/module3chapter4step4im.PNG)

> <span data-ttu-id="b3e15-121">注意： 我們在先前步驟中匯入的兩個封裝更新 「 NetworkLobby"prefab。</span><span class="sxs-lookup"><span data-stu-id="b3e15-121">note: the two packages we imported in the previous steps updated the "NetworkLobby" prefab.</span></span> <span data-ttu-id="b3e15-122">它可讓您打字的 ！</span><span class="sxs-lookup"><span data-stu-id="b3e15-122">It saves you from a lot of typing!</span></span>

5. <span data-ttu-id="b3e15-123">現在，按一下 「 MixedRealityPlayspace 」 左邊的箭號，然後向下移動子遊戲物件、 「 MainCamera"到"SharedPlayground"prefab。</span><span class="sxs-lookup"><span data-stu-id="b3e15-123">Now, click the arrow to the left of "MixedRealityPlayspace" and move the child game object, "MainCamera" down into the "SharedPlayground" prefab.</span></span> <span data-ttu-id="b3e15-124">然後，刪除 prefab"MixedRealityPlayspace"（若要刪除選取的 prefab，點選您鍵盤上的 [刪除]）。</span><span class="sxs-lookup"><span data-stu-id="b3e15-124">Then, delete the prefab "MixedRealityPlayspace" (to delete, select the prefab and tap "delete" on your keyboard).</span></span>

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

6. <span data-ttu-id="b3e15-126">建立新的遊戲物件設定為子物件 」 SharedPlayground"父物件 （用於建立新的物件，父物件，以滑鼠右鍵按一下並選取 [建立空白]）。</span><span class="sxs-lookup"><span data-stu-id="b3e15-126">Create a new game object set as a child object to the "SharedPlayground" parent object (to create a new object, right click on the parent object, and select "create  empty").</span></span>
7. <span data-ttu-id="b3e15-127">在您階層中選取新的物件，將物件的名稱變更為"TableAnchor 」，在 [偵測器] 面板。</span><span class="sxs-lookup"><span data-stu-id="b3e15-127">With the new object selected in your hierarchy, change the name of the object to "TableAnchor" in the inspector panel.</span></span> <span data-ttu-id="b3e15-128">此外，按一下 [新增元件]，並搜尋"TableAnchor 」 元件。</span><span class="sxs-lookup"><span data-stu-id="b3e15-128">Also, click "add component" and search for the "TableAnchor" component.</span></span> <span data-ttu-id="b3e15-129">選取它，並將它新增至物件。</span><span class="sxs-lookup"><span data-stu-id="b3e15-129">Select it and add it to the object.</span></span>

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> <span data-ttu-id="b3e15-131">注意： 設定定位為 x = 1，y = 0.55 和 z = 2。</span><span class="sxs-lookup"><span data-stu-id="b3e15-131">note: set the positioning to x=1, y=-0.55, and z=2.</span></span> <span data-ttu-id="b3e15-132">此外，設定 旋轉角度 y = 90。</span><span class="sxs-lookup"><span data-stu-id="b3e15-132">Also, set the rotation to y=90.</span></span> 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

8. <span data-ttu-id="b3e15-134">現在在 [專案] 面板中，在 「 prefabs"資料夾中，拖曳至 「 資料表 」 prefab 您剛才建立的 「 TableAnchor"子物件。</span><span class="sxs-lookup"><span data-stu-id="b3e15-134">Now in the project panel, in the "prefabs" folder, drag the "table" prefab into the "TableAnchor" child object you just created.</span></span>

   ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

9. <span data-ttu-id="b3e15-136">選取 「 NetworkRoom"，"NetworkLobby 」 底下的子物件，在階層中，並按一下偵測器 面板和搜尋"PhotonView 」 中的 新增元件，新增指令碼，以 「*NetworkRoom*」 物件。</span><span class="sxs-lookup"><span data-stu-id="b3e15-136">Select "NetworkRoom," a child object under "NetworkLobby" in the hierachy, and click "add component" in the inspector panel and search for "PhotonView" and add the script to the "*NetworkRoom*" object.</span></span>

![Module3Chapter4step9im](images/module3chapter4step9im.PNG)

11. <span data-ttu-id="b3e15-138">最後，如果在 「 DebugWindow 」 物件中，您可以變更寬度為 80 及高度設為 10。</span><span class="sxs-lookup"><span data-stu-id="b3e15-138">Finally, in the "DebugWindow" object, change the width to 80 and the height to 10.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a><span data-ttu-id="b3e15-140">恭喜！</span><span class="sxs-lookup"><span data-stu-id="b3e15-140">Congratulations</span></span>

<span data-ttu-id="b3e15-141">這項操作完成，加入您的 Unity 專案的所有使用者可四處都移動陰曆的啟動器。</span><span class="sxs-lookup"><span data-stu-id="b3e15-141">Once this is complete, all users that join your Unity project can move the Lunar Launcher around.</span></span> <span data-ttu-id="b3e15-142">所有的移動會同步處理，讓每位使用者可以看到其他人互動。</span><span class="sxs-lookup"><span data-stu-id="b3e15-142">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="b3e15-143">這些概念做為基本建置組塊的完整共用的共同作業體驗。</span><span class="sxs-lookup"><span data-stu-id="b3e15-143">These concepts serve as the foundational building blocks for full-featured shared collaboration experiences.</span></span> 

<span data-ttu-id="b3e15-144">雖然所有的使用者連接共用體驗的一部分，而且可以看到的物件相對的移動，應用程式是仍然無法正確對齊虛擬人偶和物件，以便在實體內的相同位置的物件與彼此，請參閱 < 本機使用者世界。</span><span class="sxs-lookup"><span data-stu-id="b3e15-144">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="b3e15-145">若要錨定在本機的共用的體驗，每個裝置會需要的實體環境的共識。</span><span class="sxs-lookup"><span data-stu-id="b3e15-145">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="b3e15-146">在這個模組中，我們將會達到此目的使用[Azure 空間的錨點](<https://azure.microsoft.com/en-us/services/spatial-anchors/>)(ASA)，這將在下一課中實作。</span><span class="sxs-lookup"><span data-stu-id="b3e15-146">In this module, we will achieve this using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), which will be implemented in the next lesson.</span></span>

<span data-ttu-id="b3e15-147">下一課之前，我們必須完成 ASA 的學習模組，將會討論 ASA 基本概念，Azure 帳戶和資源建立，而其他基本的建築物區塊需要之前我們將這整合到我們分享經驗。</span><span class="sxs-lookup"><span data-stu-id="b3e15-147">Before proceeding to the next lesson, we will need to complete the ASA Learning Module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="b3e15-148">[下一課：第 5 課 Sharing(Photon)](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="b3e15-148">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>

