---
title: 學習模組共用 HoloLens 2 MR
description: 完成這個課程來了解如何實作 HoloLens 2 應用程式內的多使用者分享的經驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 44cc41b10ed79d3085ec601ec9cf21af47b0fea5
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523301"
---
# <a name="connecting-multiple-users"></a><span data-ttu-id="08128-104">連接多個使用者</span><span class="sxs-lookup"><span data-stu-id="08128-104">Connecting multiple users</span></span>

<span data-ttu-id="08128-105">在這一課中，我們了解如何連接多個使用者，即時分享經驗的一部分。</span><span class="sxs-lookup"><span data-stu-id="08128-105">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="08128-106">本課程結束時，您可以開啟多個裝置上的應用程式，並查看 顯示圖片，由球體，聯結每個人的表示法。</span><span class="sxs-lookup"><span data-stu-id="08128-106">By the end of this lesson, you'll be able to open the application on multiple devices, and see avatar, represented by a sphere, representations of each person that joins.</span></span> 

<span data-ttu-id="08128-107">目標：</span><span class="sxs-lookup"><span data-stu-id="08128-107">Objectives:</span></span>

- <span data-ttu-id="08128-108">在您的應用程式內設定了絕佳</span><span class="sxs-lookup"><span data-stu-id="08128-108">Configure PUN within your application</span></span>
- <span data-ttu-id="08128-109">設定播放程式</span><span class="sxs-lookup"><span data-stu-id="08128-109">Configure players</span></span>
- <span data-ttu-id="08128-110">了解如何連接多個使用者分享經驗</span><span class="sxs-lookup"><span data-stu-id="08128-110">Learn how to connect multiple users in a shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="08128-111">指示</span><span class="sxs-lookup"><span data-stu-id="08128-111">Instructions</span></span>

1. <span data-ttu-id="08128-112">在 [資產]-> [資源]-> [專案] 面板中的 Prefabs 資料夾、 拖曳和卸除在 NetworkLobby prefab 至階層，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="08128-112">In the Assets->Resources->Prefabs folder in the Project panel, drag and drop the NetworkLobby prefab in to the hierarchy as shown in the image below.</span></span>


   ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="08128-114">當您展開 NetworkLobby 時，您會看到呼叫 NetworkRoom 子物件。</span><span class="sxs-lookup"><span data-stu-id="08128-114">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="08128-115">選取的 NetworkRoom，進入 偵測器 面板中，然後按一下 新增元件。</span><span class="sxs-lookup"><span data-stu-id="08128-115">With NetworkRoom selected, go into the Inspector panel, and click Add Component.</span></span> <span data-ttu-id="08128-116">搜尋 PhotonView 並新增此元件。</span><span class="sxs-lookup"><span data-stu-id="08128-116">Search for PhotonView and add the component.</span></span>

   ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="08128-118">建立新的空白遊戲物件階層架構中。</span><span class="sxs-lookup"><span data-stu-id="08128-118">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="08128-119">在階層中，以滑鼠右鍵按一下，並從操作功能表中選取 空白。</span><span class="sxs-lookup"><span data-stu-id="08128-119">Right click in the hierarchy, and select Empty from the Context menu.</span></span> <span data-ttu-id="08128-120">請確定位置設定為 x = 0，y = 0，z = 0，並命名物件，PhotonUser。</span><span class="sxs-lookup"><span data-stu-id="08128-120">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

   ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="08128-122">按一下 新增元件，並輸入一般的淨同步處理。選取 一般的淨同步處理類別。</span><span class="sxs-lookup"><span data-stu-id="08128-122">Click Add Component, and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="08128-123">類別的出現時，按一下 [使用者] 核取方塊，將它開啟。</span><span class="sxs-lookup"><span data-stu-id="08128-123">When the class appears, click on the User check box to turn it on.</span></span> 

   ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="08128-125">同樣地，按一下新增元件，然後鍵入 Photon 檢視。</span><span class="sxs-lookup"><span data-stu-id="08128-125">Click on Add Component again, and type Photon View.</span></span> <span data-ttu-id="08128-126">選取 Photon 檢視類別出現在下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="08128-126">Select the Photon View class that appears in the drop-down list.</span></span>

   ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="08128-128">按一下 [檔案] 圖示，一般的淨同步處理類別。</span><span class="sxs-lookup"><span data-stu-id="08128-128">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="08128-129">將拖放 Photon 檢視的觀察到的元件 欄位中。</span><span class="sxs-lookup"><span data-stu-id="08128-129">Drag and drop it in the Photon View's Observed Components field.</span></span> ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png) 

7. <span data-ttu-id="08128-131">接下來，我們會建立置放的球體來代表每個聯結分享的經驗的人員。</span><span class="sxs-lookup"><span data-stu-id="08128-131">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="08128-132">以滑鼠右鍵按一下您剛才建立的 PhotonUser 物件及要 scrolldown"3D 物件，然後按一下 球紋。</span><span class="sxs-lookup"><span data-stu-id="08128-132">Right click the PhotonUser object you just created, and scrolldown to "3D Object, and click Sphere.</span></span> <span data-ttu-id="08128-133">這會建立圓球的遊戲物件為 PhotonUser 物件的子系。</span><span class="sxs-lookup"><span data-stu-id="08128-133">This will create a sphere game object as a child of the PhotonUser object.</span></span>

   ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="08128-135">調整到 x 球體 = $0.06，y = $0.06，ad z = $0.06。</span><span class="sxs-lookup"><span data-stu-id="08128-135">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

   ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="08128-137">PhotonUser 遊戲物件拖曳至 [專案] 面板中，在 Prefabs 資料夾，然後刪除它從場景。</span><span class="sxs-lookup"><span data-stu-id="08128-137">Drag the PhotonUser game object into the Prefabs folder in the Project panel, and then delete it from the scene.</span></span> <span data-ttu-id="08128-138">我們現在已建立時產生，或具現化新的播放程式分享經驗中可以使用 prefab。</span><span class="sxs-lookup"><span data-stu-id="08128-138">We have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

   ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="08128-140">注意： 確定遊戲物件已成功複製到 Prefabs 資料夾之前從階層中刪除。</span><span class="sxs-lookup"><span data-stu-id="08128-140">Note: ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="08128-141">建立新的物件階層架構中，依照步驟 3 中的指示，並將它命名為 SharedPlayground。</span><span class="sxs-lookup"><span data-stu-id="08128-141">Create a new object in the hierarchy by following the instructions in Step 3, and name it SharedPlayground.</span></span> <span data-ttu-id="08128-142">然後，按一下 [新增元件，和一般網路管理員] 中，搜尋，然後按一下要新增 「 一般網路管理員元件。</span><span class="sxs-lookup"><span data-stu-id="08128-142">Then, click Add Component, and search for generic network manager, and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="08128-143">將物件的位置變更為 x = 0，y = 0，且 z = 0。</span><span class="sxs-lookup"><span data-stu-id="08128-143">Change the position of the object to x=0, y=0, and z =0.</span></span>

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="08128-145">恭喜！</span><span class="sxs-lookup"><span data-stu-id="08128-145">Congratulations</span></span>

<span data-ttu-id="08128-146">上述所有步驟都都完成時，並在建置程序也已完成之後, 按下 [播放] 按鈕，並連接 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="08128-146">Once all the steps above are complete, and the build process is also complete, press the play button and connect your HoloLens 2.</span></span> <span data-ttu-id="08128-147">您應該會看到四處移動，當您移動您的球體。</span><span class="sxs-lookup"><span data-stu-id="08128-147">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="08128-148">這會顯示任何使用者加入您的 Unity 專案 ！</span><span class="sxs-lookup"><span data-stu-id="08128-148">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="08128-149">[下一課：第 4 課 Sharing(Photon)](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="08128-149">[Next Lesson: Sharing(Photon) Lesson 4](mrlearning-sharing(photon)-ch4.md)</span></span>

