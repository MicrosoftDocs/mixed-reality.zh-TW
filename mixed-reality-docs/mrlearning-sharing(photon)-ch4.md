---
title: 多使用者功能教學課程 - 4。 與多個使用者共用物件移動
description: 完成此課程以了解如何在 HoloLens 2 應用程式中實作使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: b0ddf0799fd94c29ce8f1221c55073cd77b63703
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031251"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="8d8f9-105">4.與多個使用者共用物件移動</span><span class="sxs-lookup"><span data-stu-id="8d8f9-105">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="8d8f9-106">在本教學課程中，您將了解如何共用物件的移動，讓共用工作階段的所有參與者都可以共同作業及查看彼此的互動。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-106">In this Tutorial, you'll learn how to share the movements of objects so that all participants of a shared session can collaborate and view each others' interactions.</span></span> <span data-ttu-id="8d8f9-107">本課程以[基本模組教學課程](mrlearning-base.md)中所建立的登月小艇為基礎。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-107">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

## <a name="objectives"></a><span data-ttu-id="8d8f9-108">目標</span><span class="sxs-lookup"><span data-stu-id="8d8f9-108">Objectives</span></span>

- <span data-ttu-id="8d8f9-109">帶入月球發射器以作為要共用的 3D 模型</span><span class="sxs-lookup"><span data-stu-id="8d8f9-109">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="8d8f9-110">設定專案來共用 3D 模型的移動</span><span class="sxs-lookup"><span data-stu-id="8d8f9-110">Configure your project to share the movements of the 3D model</span></span>
- <span data-ttu-id="8d8f9-111">了解如何建立基本的多使用者共同作業應用程式</span><span class="sxs-lookup"><span data-stu-id="8d8f9-111">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="instructions"></a><span data-ttu-id="8d8f9-112">指示</span><span class="sxs-lookup"><span data-stu-id="8d8f9-112">Instructions</span></span>

1. <span data-ttu-id="8d8f9-113">儲存上一課中的場景 (Control+S)。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-113">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="8d8f9-114">您可以將其命名為 HLSharedProjectMainPart4，以便在需要時更容易找到。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-114">You can name it HLSharedProjectMainPart4.unity so it's easier to find when you need it.</span></span>

2. <span data-ttu-id="8d8f9-115">從 [專案] 視窗的 [資產] -> [指令碼] 資料夾中按兩下 [GenericNetSync]，從 Visual Studio 或您使用的程式碼編輯器中將其開啟。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-115">From the Project window, in the Assets->Scripts folder, double-click GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  

    ![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="8d8f9-117">在第 34 和 38 行上移除 "//"，以針對您將在本課程中使用的資料表啟用程式碼。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-117">On Lines 34 and 38, remove "//" to activate the code for the table that you will use in this lesson.</span></span> <span data-ttu-id="8d8f9-118">接下來，儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-118">Next, save the file.</span></span>

    ![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="8d8f9-120">在 [專案] 視窗中，按兩下 [資產] -> [指令碼] 資料夾中的 PhotonRoom.cs 檔案，在 Visual Studio 中將其開啟。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-120">In the Project window, double-click the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span>

    ![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="8d8f9-122">如同步驟 3，我們需要移除第 25、26 和 106 行上的 "//" 以啟動程式碼。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-122">Just like in Step 3, we need to remove "//" to activate the code at Lines 25, 26, and 106.</span></span>

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png)

    ![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="8d8f9-125">在 [階層] 視圖中，選取 NetworkRoom 物件。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-125">In the Hierarchy view, select the NetworkRoom object.</span></span>

    ![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. <span data-ttu-id="8d8f9-127">在 [專案] 檢視中，瀏覽至 [資產] -> [資源] -> [Prefabs]。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-127">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="8d8f9-128">首先，將資料表 Prefab 拖放到 PhotonRoom 類別上的 Tableprefab 位置。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-128">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="8d8f9-129">接下來，將 RocketLauncherCompleteVariantprefab 拖放到 PhotonRoom 類別上的模組 Prefab 位置。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-129">Next, drag and drop the RocketLauncherCompleteVariantprefab to the Module Prefab slot on the PhotonRoom class.</span></span>

    ![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

    >[!NOTE]
    ><span data-ttu-id="8d8f9-131">如果您按一下其中一個 Prefab 物件和版本，偵測器就會切換至該物件。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-131">If you click one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="8d8f9-132">按一下、拖放，然後將每個物件放到適當的位置。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-132">Click, drag, drop, and release each object to its appropriate slot.</span></span>

8. <span data-ttu-id="8d8f9-133">按一下 MixedRealityPlayspace 左邊的箭號，將子遊戲物件 MainCamera 向下移動到 SharedPlayground Prefab。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-133">Click the arrow to the left of MixedRealityPlayspace and move the child game object MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="8d8f9-134">接下來，藉由選取 MixedRealityPlayspace Prefab 並在鍵盤上按一下 "delete" 來刪除該 Prefab。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-134">Next, delete the prefab, MixedRealityPlayspace by selecting the prefab and tap "delete" on your keyboard).</span></span>

    ![Module3hapter4step5im](images/module3chapter4step5im.PNG)

    >[!NOTE]
    ><span data-ttu-id="8d8f9-136">請確定主要相機和 SharedPlayground 位置都設定為 0,0,0。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-136">Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="8d8f9-137">選取 SharedPlayground 物件，並按一下滑鼠右鍵來選擇 [建立空物件] 選項，將空白遊戲物件建立為 "SharedPlayground" 遊戲物件的子系。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-137">Select "SharedPlayground" object and right click the mouse to choose "create empty" option to create an empty game object as a child of "SharedPlayground" game object.</span></span>

   ![Module3chapter4step6im](images/module3chapter4step6im.PNG)

10. <span data-ttu-id="8d8f9-139">在您的階層中選取新物件後，請在 [偵測器] 面板中將物件的名稱變更為 TableAnchor。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-139">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="8d8f9-140">然後按一下 [新增元件]，並搜尋 TableAnchor 元件。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-140">Also, click Add Component and search for the TableAnchor component.</span></span> <span data-ttu-id="8d8f9-141">選取該元件並將其新增至物件。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-141">Select it and add it to the object.</span></span>

    ![Module3Chapter4step7im](images/module3chapter4step7im.PNG)

11. <span data-ttu-id="8d8f9-143">從 [專案] 面板的 [Prefabs] 資料夾中，將資料表 Prefab 拖曳至您剛才建立的 "TableAnchor" 子物件。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-143">From the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object that you just created.</span></span>

    ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

## <a name="congratulations"></a><span data-ttu-id="8d8f9-145">恭喜！</span><span class="sxs-lookup"><span data-stu-id="8d8f9-145">Congratulations</span></span>

<span data-ttu-id="8d8f9-146">完成後此課程後，請四處瀏覽以尋找登月小艇。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-146">Once this is complete, look around to find the lunar module.</span></span> <span data-ttu-id="8d8f9-147">在此之後，加入 Unity 專案的所有使用者都可以四處移動月球發射器。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-147">After this, all users that join your Unity project can move the lunar launcher around.</span></span>  <span data-ttu-id="8d8f9-148">所有的移動都會進行同步，讓每個使用者都可以看到彼此的互動。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-148">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="8d8f9-149">這些概念可為功能完整且共用的共同作業體驗提供基本構成要素。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-149">These concepts serve as the fundamental building blocks for full-featured, shared collaboration experiences.</span></span>

<span data-ttu-id="8d8f9-150">雖然所有使用者都會連結為共用體驗的一部分，而且可以查看物件的相對移動，但應用程式仍無法精確地對齊虛擬人偶和物件，因此本機使用者無法看到實際世界中相同位置上的彼此和物件。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-150">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users were not able see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="8d8f9-151">為了針對本機共用體驗建立錨點，每個裝置都需要對實體環境有共同的了解。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-151">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="8d8f9-152">在此課程模組中，我們將使用 [Azure Spatial Anchors](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) 來達成此目的，這會在下一課中實作。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-152">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) which will be implemented in the next lesson.</span></span>

<span data-ttu-id="8d8f9-153">在繼續進行下一課之前，我們必須先完成 ASA 學習課程模組，其中涵蓋 ASA 基本概念、Azure 帳戶和資源建立，以及我們在將此整合到我們的共用體驗之前所需的其他基本構成要素。</span><span class="sxs-lookup"><span data-stu-id="8d8f9-153">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, as well as other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="8d8f9-154">[下一課：5.將 Azure Spatial Anchors 整合到共用體驗](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="8d8f9-154">[Next Lesson: 5. Integration Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch5.md)</span></span>
