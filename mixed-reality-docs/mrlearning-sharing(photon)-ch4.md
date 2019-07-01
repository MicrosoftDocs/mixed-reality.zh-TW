---
title: 學習模組共用 HoloLens 2 MR
description: 完成這個課程來了解如何實作 HoloLens 2 應用程式內的多使用者分享的經驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: b729de818dfa21df8fbce782a24a611a365ac795
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465229"
---
# <a name="synchronizing-shared-object-movements"></a><span data-ttu-id="14e3f-104">同步處理共用的物件移動</span><span class="sxs-lookup"><span data-stu-id="14e3f-104">Synchronizing shared object movements</span></span>

<span data-ttu-id="14e3f-105">在這一課中，我們了解如何共用物件的移動，以便在共用的工作階段的所有參與者都可以一起共同作業，並檢視其他人互動。</span><span class="sxs-lookup"><span data-stu-id="14e3f-105">In this lesson, we learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="14e3f-106">這一課為建置基礎所建置的一部分陰曆啟動器[基底模組的教學課程](mrlearning-base.md)。</span><span class="sxs-lookup"><span data-stu-id="14e3f-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="14e3f-107">目標：</span><span class="sxs-lookup"><span data-stu-id="14e3f-107">Objectives:</span></span>

- <span data-ttu-id="14e3f-108">將 3D 模型到共用陰曆啟動器</span><span class="sxs-lookup"><span data-stu-id="14e3f-108">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="14e3f-109">將專案設定為共用的 3D 模型的移動。</span><span class="sxs-lookup"><span data-stu-id="14e3f-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="14e3f-110">了解如何建置基本的多使用者共同作業應用程式</span><span class="sxs-lookup"><span data-stu-id="14e3f-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="14e3f-111">指示</span><span class="sxs-lookup"><span data-stu-id="14e3f-111">Instructions</span></span>


1. <span data-ttu-id="14e3f-112">在上一課 (Control + S) 中儲存的場景。</span><span class="sxs-lookup"><span data-stu-id="14e3f-112">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="14e3f-113">您可以為它命名 HLSharedProjectMainPart4.unity 以便更輕鬆地尋找當您需要它。</span><span class="sxs-lookup"><span data-stu-id="14e3f-113">You can name it HLSharedProjectMainPart4.unity so that it's easier to find when you need it.</span></span>

2. <span data-ttu-id="14e3f-114">從 專案 視窗中，在資產-> 指令碼 資料夾，按兩下 GenericNetSync 在 Visual Studio，或用過程式碼會使用的編輯器中開啟它。</span><span class="sxs-lookup"><span data-stu-id="14e3f-114">From the Project window, in the Assets->Scripts folder, double click on GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  ![](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="14e3f-115">在行 34 和 38，移除 / / 若要啟動的程式碼，我們將在這一課使用的資料表。</span><span class="sxs-lookup"><span data-stu-id="14e3f-115">On Lines 34 and 38, remove the // to activate the code for the table that we will use in this lesson.</span></span> <span data-ttu-id="14e3f-116">接下來，將檔案儲存。</span><span class="sxs-lookup"><span data-stu-id="14e3f-116">next, Save the file.</span></span> ![](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="14e3f-117">在 專案 視窗中，按兩下 PhotonRoom.cs 檔案，在 資產-> 在 Visual Studio 中開啟的 指令碼 資料夾。</span><span class="sxs-lookup"><span data-stu-id="14e3f-117">In the Project window, double click on the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span> ![](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="14e3f-118">就像在步驟 3 中，我們需要移除 / / 啟用在 25、 26 及 106 的幾行程式碼。![](images/module3chapter4updatestep5a.png)</span><span class="sxs-lookup"><span data-stu-id="14e3f-118">Just like in Step 3, we need to remove the // to activate the code at Lines 25, 26, and 106.![](images/module3chapter4updatestep5a.png)</span></span> ![](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="14e3f-119">在階層檢視中，選取 NetworkRoom 物件。![](images/module3chapter4updatestep6.png)</span><span class="sxs-lookup"><span data-stu-id="14e3f-119">In the Hierarchy view, select the NetworkRoom object.![](images/module3chapter4updatestep6.png)</span></span>

7. <span data-ttu-id="14e3f-120">在 [專案] 檢視中，瀏覽至資產]-> [資源]-> [Prefabs。</span><span class="sxs-lookup"><span data-stu-id="14e3f-120">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="14e3f-121">首先，拖放資料表 prefab PhotonRoom 類別上的 Tableprefab 插槽。</span><span class="sxs-lookup"><span data-stu-id="14e3f-121">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="14e3f-122">接下來將拖放 LunarModule prefab PhotonRoom 類別上的模組 Prefab 插槽。</span><span class="sxs-lookup"><span data-stu-id="14e3f-122">Next drag and drop the LunarModule prefab to the Module Prefab slot on the PhotonRoom class.</span></span> ![](images/module3chapter4updatestep7.png)

   <span data-ttu-id="14e3f-123">注意:如果您按一下其中一個 prefab 物件和版本，偵測器會切換至該物件。</span><span class="sxs-lookup"><span data-stu-id="14e3f-123">Note: If you click on one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="14e3f-124">按一下、 拖放，並釋放每個物件至其適當的位置。</span><span class="sxs-lookup"><span data-stu-id="14e3f-124">Click, drag, drop, and release each object to its appropriate slot.</span></span>



8. <span data-ttu-id="14e3f-125">按一下 MixedRealityPlayspace，左邊的箭號，向下移動子遊戲物件、 MainCamera SharedPlayground prefab 到。</span><span class="sxs-lookup"><span data-stu-id="14e3f-125">Click the arrow to the left of MixedRealityPlayspace, and move the child game object, MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="14e3f-126">接下來，刪除 prefab，MixedRealityPlayspace，若要刪除選取的 prefab，在鍵盤上點選 [刪除]）。</span><span class="sxs-lookup"><span data-stu-id="14e3f-126">Next, delete the prefab, MixedRealityPlayspace, to delete, select the prefab, and tap "delete" on your keyboard).</span></span>
<span data-ttu-id="14e3f-127">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span><span class="sxs-lookup"><span data-stu-id="14e3f-127">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span></span>

<span data-ttu-id="14e3f-128">注意:請確定將 Main Camera 與 SharedPlayground 的位置會設定成 0,0,0。</span><span class="sxs-lookup"><span data-stu-id="14e3f-128">Note:  Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="14e3f-129">建立新的遊戲物件來建立新的物件設定為子物件 SharedPlayground 父物件。</span><span class="sxs-lookup"><span data-stu-id="14e3f-129">Create a new game object set as a child object to the SharedPlayground parent object to create a new object.</span></span> <span data-ttu-id="14e3f-130">父物件，以滑鼠右鍵按一下，然後選取 建立空白。</span><span class="sxs-lookup"><span data-stu-id="14e3f-130">Right click on the parent object, and select Create Empty.</span></span> 

10. <span data-ttu-id="14e3f-131">在您階層中選取新的物件，將物件的名稱變更為 TableAnchor，在 [偵測器] 面板。</span><span class="sxs-lookup"><span data-stu-id="14e3f-131">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="14e3f-132">此外，按一下 新增元件，並搜尋 TableAnchor 元件。</span><span class="sxs-lookup"><span data-stu-id="14e3f-132">Also, click Add Component, and search for the TableAnchor component.</span></span> <span data-ttu-id="14e3f-133">選取它，並將它新增至物件。</span><span class="sxs-lookup"><span data-stu-id="14e3f-133">Select it and add it to the object.</span></span> 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> <span data-ttu-id="14e3f-135">注意:設定定位為 x = 1，y = 0.55 和 z = 2。</span><span class="sxs-lookup"><span data-stu-id="14e3f-135">Note: Set the positioning to x=1, y=-0.55, and z=2.</span></span> <span data-ttu-id="14e3f-136">此外，設定 旋轉角度 y = 90。</span><span class="sxs-lookup"><span data-stu-id="14e3f-136">Also, set the rotation to y=90.</span></span> 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. <span data-ttu-id="14e3f-138">現在從 Prefabs 資料夾中的 [專案] 面板，請將資料表 prefab 拖曳到您剛才建立的 「 TableAnchor"子物件。</span><span class="sxs-lookup"><span data-stu-id="14e3f-138">Now from the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object you just created.</span></span>

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. <span data-ttu-id="14e3f-140">最後，如果在 DebugWindow 物件中，您可以變更其寬度為 80 及高度設為 10。</span><span class="sxs-lookup"><span data-stu-id="14e3f-140">Finally, in the DebugWindow object, change the width to 80 and the height to 10.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a><span data-ttu-id="14e3f-142">恭喜！</span><span class="sxs-lookup"><span data-stu-id="14e3f-142">Congratulations</span></span>


<span data-ttu-id="14e3f-143">這項操作完成，加入您的 Unity 專案的所有使用者可四處都移動陰曆的啟動器。</span><span class="sxs-lookup"><span data-stu-id="14e3f-143">Once this is complete, all users that join your Unity project can move the lunar launcher around.</span></span> <span data-ttu-id="14e3f-144">所有的移動會同步處理，讓每位使用者可以看到其他人互動。</span><span class="sxs-lookup"><span data-stu-id="14e3f-144">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="14e3f-145">這些概念做為基本建置組塊的完整功能、 共用的共同作業體驗。</span><span class="sxs-lookup"><span data-stu-id="14e3f-145">These concepts serve as the foundational building blocks for full-featured, shared collaboration experiences.</span></span> 

<span data-ttu-id="14e3f-146">雖然所有的使用者連接共用，一部分，而且可以看到的物件相對的移動，應用程式是經驗的仍然無法正確對齊虛擬人偶和物件，以便在實體內的相同位置的物件與彼此，請參閱 < 本機使用者世界。</span><span class="sxs-lookup"><span data-stu-id="14e3f-146">Although all users are connected as part of a shared experience, and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="14e3f-147">若要錨定在本機的共用的體驗，每個裝置會需要的實體環境的共識。</span><span class="sxs-lookup"><span data-stu-id="14e3f-147">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="14e3f-148">在這個模組中，我們將會達到此目的使用[Azure 空間的錨點](<https://azure.microsoft.com/en-us/services/spatial-anchors/>)(ASA)，將在下一課中實作。</span><span class="sxs-lookup"><span data-stu-id="14e3f-148">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) that will be implemented in the next lesson.</span></span>

<span data-ttu-id="14e3f-149">下一課之前，我們必須完成 ASA 學習模組，它涵蓋了 ASA 基本的 Azure 帳戶和資源建立，而其他基本的建築物區塊需要之前我們將這整合到我們分享經驗。</span><span class="sxs-lookup"><span data-stu-id="14e3f-149">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="14e3f-150">[下一課：第 5 課 Sharing(Photon)](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="14e3f-150">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>

