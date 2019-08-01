---
title: 多使用者功能教學課程-3。 連接多個使用者
description: 完成此課程, 以瞭解如何在 HoloLens 2 應用程式中執行多使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: d3068a1ebbbc2b6db8b563be8bf8c6e488e9491a
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701934"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="06f3a-105">3.連接多個使用者</span><span class="sxs-lookup"><span data-stu-id="06f3a-105">3. Connecting multiple users</span></span>

<span data-ttu-id="06f3a-106">在這一課, 我們將瞭解如何在即時共用體驗中連接多個使用者。</span><span class="sxs-lookup"><span data-stu-id="06f3a-106">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="06f3a-107">在本課程結束時, 您將能夠在多個裝置上開啟應用程式, 並查看每個聯結人員的標記法, 以球體表示。</span><span class="sxs-lookup"><span data-stu-id="06f3a-107">By the end of this lesson, you'll be able to open the application on multiple devices, and see avatar, represented by a sphere, representations of each person that joins.</span></span> 

<span data-ttu-id="06f3a-108">目標</span><span class="sxs-lookup"><span data-stu-id="06f3a-108">Objectives:</span></span>

- <span data-ttu-id="06f3a-109">在您的應用程式中設定雙關語</span><span class="sxs-lookup"><span data-stu-id="06f3a-109">Configure PUN within your application</span></span>
- <span data-ttu-id="06f3a-110">設定播放者</span><span class="sxs-lookup"><span data-stu-id="06f3a-110">Configure players</span></span>
- <span data-ttu-id="06f3a-111">瞭解如何在共用體驗中連接多個使用者</span><span class="sxs-lookup"><span data-stu-id="06f3a-111">Learn how to connect multiple users in a shared experience</span></span>

## <a name="instructions"></a><span data-ttu-id="06f3a-112">指示</span><span class="sxs-lookup"><span data-stu-id="06f3a-112">Instructions</span></span>

1. <span data-ttu-id="06f3a-113">在 [資產-> 資源]-[專案] 面板的 [> Prefabs] 資料夾中, 將 NetworkLobby prefab 拖放到階層中, 如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="06f3a-113">In the Assets->Resources->Prefabs folder in the Project panel, drag and drop the NetworkLobby prefab in to the hierarchy as shown in the image below.</span></span>

![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="06f3a-115">當您展開 [NetworkLobby] 時, 您會看到名為 NetworkRoom 的子物件。</span><span class="sxs-lookup"><span data-stu-id="06f3a-115">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="06f3a-116">選取 NetworkRoom 後, 進入 [檢查] 面板, 然後按一下 [新增元件]。</span><span class="sxs-lookup"><span data-stu-id="06f3a-116">With NetworkRoom selected, go into the Inspector panel, and click Add Component.</span></span> <span data-ttu-id="06f3a-117">搜尋 PhotonView 並新增元件。</span><span class="sxs-lookup"><span data-stu-id="06f3a-117">Search for PhotonView and add the component.</span></span>

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="06f3a-119">在階層中建立新的空白遊戲物件。</span><span class="sxs-lookup"><span data-stu-id="06f3a-119">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="06f3a-120">在階層中按一下滑鼠右鍵, 然後從內容功能表中選取 [空白]。</span><span class="sxs-lookup"><span data-stu-id="06f3a-120">Right click in the hierarchy, and select Empty from the Context menu.</span></span> <span data-ttu-id="06f3a-121">請確定定位設定為 x = 0、y = 0、z = 0, 並將物件命名為 PhotonUser。</span><span class="sxs-lookup"><span data-stu-id="06f3a-121">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="06f3a-123">按一下 [新增元件], 然後輸入一般 Net Sync。選取 [一般 Net Sync] 類別。</span><span class="sxs-lookup"><span data-stu-id="06f3a-123">Click Add Component, and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="06f3a-124">當類別出現時, 按一下 [使用者] 核取方塊以開啟它。</span><span class="sxs-lookup"><span data-stu-id="06f3a-124">When the class appears, click on the User check box to turn it on.</span></span> 

![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="06f3a-126">再次按一下 [新增元件], 然後輸入 Photon View。</span><span class="sxs-lookup"><span data-stu-id="06f3a-126">Click on Add Component again, and type Photon View.</span></span> <span data-ttu-id="06f3a-127">選取出現在下拉式清單中的 [Photon] View 類別。</span><span class="sxs-lookup"><span data-stu-id="06f3a-127">Select the Photon View class that appears in the drop-down list.</span></span>

![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="06f3a-129">按一下 [一般 Net Sync] 類別的 [檔案] 圖示。</span><span class="sxs-lookup"><span data-stu-id="06f3a-129">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="06f3a-130">將它拖放到 [Photon] 視圖的 [觀察的元件] 欄位中。</span><span class="sxs-lookup"><span data-stu-id="06f3a-130">Drag and drop it in the Photon View's Observed Components field.</span></span> 

![module3chapter3updateStep6im .png](images/module3chapter3updateStep6im.png) 

7. <span data-ttu-id="06f3a-132">接下來, 我們會建立球體來代表加入共用體驗的每個人。</span><span class="sxs-lookup"><span data-stu-id="06f3a-132">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="06f3a-133">以滑鼠右鍵按一下您剛才建立的 PhotonUser 物件, 並 scrolldown 至 [3D 物件], 然後按一下 [球體]。</span><span class="sxs-lookup"><span data-stu-id="06f3a-133">Right click the PhotonUser object you just created, and scrolldown to "3D Object, and click Sphere.</span></span> <span data-ttu-id="06f3a-134">這會將球體遊戲物件建立為 PhotonUser 物件的子系。</span><span class="sxs-lookup"><span data-stu-id="06f3a-134">This will create a sphere game object as a child of the PhotonUser object.</span></span>

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="06f3a-136">將球體向下調整為 x = 0.06、y = 0.06、ad z = 0.06。</span><span class="sxs-lookup"><span data-stu-id="06f3a-136">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="06f3a-138">將 [PhotonUser 遊戲] 物件拖曳至 [專案] 面板中的 [Prefabs] 資料夾, 然後從場景中刪除它。</span><span class="sxs-lookup"><span data-stu-id="06f3a-138">Drag the PhotonUser game object into the Prefabs folder in the Project panel, and then delete it from the scene.</span></span> <span data-ttu-id="06f3a-139">我們現在建立了一個 prefab, 可在建立或具現化共用體驗中的新玩家時使用。</span><span class="sxs-lookup"><span data-stu-id="06f3a-139">We have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="06f3a-141">注意: 請確定遊戲物件已成功複製到 Prefabs 資料夾, 然後才將它從您的階層中刪除。</span><span class="sxs-lookup"><span data-stu-id="06f3a-141">Note: ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="06f3a-142">遵循步驟3中的指示, 在階層中建立新的物件, 並將其命名為 SharedPlayground。</span><span class="sxs-lookup"><span data-stu-id="06f3a-142">Create a new object in the hierarchy by following the instructions in Step 3, and name it SharedPlayground.</span></span> <span data-ttu-id="06f3a-143">接著, 按一下 [新增元件], 並搜尋 [一般網路系統管理員], 然後按一下以新增 [一般網路系統管理員] 元件。</span><span class="sxs-lookup"><span data-stu-id="06f3a-143">Then, click Add Component, and search for generic network manager, and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="06f3a-144">將物件的位置變更為 x = 0、y = 0、z = 0。</span><span class="sxs-lookup"><span data-stu-id="06f3a-144">Change the position of the object to x=0, y=0, and z =0.</span></span>

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="06f3a-146">恭喜！</span><span class="sxs-lookup"><span data-stu-id="06f3a-146">Congratulations</span></span>

<span data-ttu-id="06f3a-147">完成上述所有步驟之後, 建立程式也會完成, 請按下 [播放] 按鈕並連接您的 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="06f3a-147">Once all the steps above are complete, and the build process is also complete, press the play button and connect your HoloLens 2.</span></span> <span data-ttu-id="06f3a-148">當您移動 head 時, 您應該會看到一個球體四處移動。</span><span class="sxs-lookup"><span data-stu-id="06f3a-148">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="06f3a-149">這會針對加入 Unity 專案的任何使用者顯示!</span><span class="sxs-lookup"><span data-stu-id="06f3a-149">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="06f3a-150">[下一課：4.與多個使用者共用物件移動](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="06f3a-150">[Next Lesson: 4. Sharing object movements with multiple users](mrlearning-sharing(photon)-ch4.md)</span></span>

