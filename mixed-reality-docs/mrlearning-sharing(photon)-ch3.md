---
title: 學習模組共用 HoloLens 2 MR
description: 完成這個課程來了解如何實作 HoloLens 2 應用程式內的多使用者分享的經驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: f2e8cef618ea2fbee398ce19f1ba60b712b5fe3e
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327583"
---
# <a name="connecting-multiple-users"></a><span data-ttu-id="20da0-104">**連接多個使用者**</span><span class="sxs-lookup"><span data-stu-id="20da0-104">**Connecting Multiple Users**</span></span> 

<span data-ttu-id="20da0-105">在這一課中，我們將了解如何連接多個使用者，即時分享經驗的一部分。</span><span class="sxs-lookup"><span data-stu-id="20da0-105">In this lesson, we will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="20da0-106">本課程結束時，您都能夠開啟多個裝置上的應用程式，並查看的聯結 （頭像球體所表示）。 每個人的 「 虛擬人偶 」 表示法</span><span class="sxs-lookup"><span data-stu-id="20da0-106">By the end of this lesson, you will be able to open the application on multiple devices, and see "avatar" representations of each person that joins (avatars represented by a sphere.)</span></span> 

<span data-ttu-id="20da0-107">目標：</span><span class="sxs-lookup"><span data-stu-id="20da0-107">Objectives:</span></span>

- <span data-ttu-id="20da0-108">在您的應用程式內設定了絕佳</span><span class="sxs-lookup"><span data-stu-id="20da0-108">Configure PUN within your application</span></span>
- <span data-ttu-id="20da0-109">設定播放程式</span><span class="sxs-lookup"><span data-stu-id="20da0-109">Configure players</span></span>
- <span data-ttu-id="20da0-110">了解如何連接多個使用者分享經驗</span><span class="sxs-lookup"><span data-stu-id="20da0-110">Learn how to connect multiple users in a shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="20da0-111">指示</span><span class="sxs-lookup"><span data-stu-id="20da0-111">Instructions</span></span>

1. <span data-ttu-id="20da0-112">在資產中 > 資源 > Prefabs 資料夾的 [專案] 面板、 拖曳和卸除 「 NetworkLobby"prefab 在階層中，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="20da0-112">In the Assets>Resources>Prefabs folder of the project panel, drag and drop the "NetworkLobby" prefab in to the hierarchy, as shown in the image below.</span></span>


![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="20da0-114">當您展開 prefab"NetworkLobby 」 時，您應該會看到子物件呼叫 「 NetworkRoom。 」</span><span class="sxs-lookup"><span data-stu-id="20da0-114">When you expand the prefab "NetworkLobby," you should see a child object called "NetworkRoom."</span></span> <span data-ttu-id="20da0-115">有了它選取，進入 [偵測器] 面板，並按一下 [新增元件]。</span><span class="sxs-lookup"><span data-stu-id="20da0-115">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="20da0-116">搜尋 「 PhotonView"，並將元件加入。</span><span class="sxs-lookup"><span data-stu-id="20da0-116">Search for "PhotonView" and add the component.</span></span>

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="20da0-118">在階層中建立新的空白遊戲物件 （在階層中以滑鼠右鍵按一下並從內容功能表中選取 [清理]）。</span><span class="sxs-lookup"><span data-stu-id="20da0-118">Create a new empty game object in the hierarchy (right click in the hierarchy and select "Empty" from the context menu).</span></span> <span data-ttu-id="20da0-119">請確定位置設定為 x = 0，y = 0，z = 0，並命名物件，也就是 「 PhotonUser。 」</span><span class="sxs-lookup"><span data-stu-id="20da0-119">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="20da0-121">接下來，我們想要建立來代表每個聯結分享的經驗的人員所置放的球體。</span><span class="sxs-lookup"><span data-stu-id="20da0-121">Next, we want to create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="20da0-122">以滑鼠右鍵按一下您剛才建立的 「 PhotonUser"物件往下移到 「 3D 物件 」，按一下 "球紋。 」</span><span class="sxs-lookup"><span data-stu-id="20da0-122">Right click the "PhotonUser" object you just created, go down to "3D Object" and click "Sphere."</span></span> <span data-ttu-id="20da0-123">這會建立圓球的遊戲物件為 PhotonUser 物件的子系。</span><span class="sxs-lookup"><span data-stu-id="20da0-123">This will create a sphere game object as a child of the PhotonUser object.</span></span>

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

5. <span data-ttu-id="20da0-125">調整到 x 球體 = $0.06，y = $0.06，ad z = $0.06。</span><span class="sxs-lookup"><span data-stu-id="20da0-125">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

6. <span data-ttu-id="20da0-127">將"PhotonUser 」 遊戲物件拖曳至 [專案] 面板中的 「 prefabs"資料夾。</span><span class="sxs-lookup"><span data-stu-id="20da0-127">Drag the "PhotonUser" game object into the "prefabs" folder in the project panel.</span></span> <span data-ttu-id="20da0-128">然後，刪除從場景。</span><span class="sxs-lookup"><span data-stu-id="20da0-128">Then, delete it from the scene.</span></span> <span data-ttu-id="20da0-129">我們現在已建立時產生，或具現化新的播放程式分享經驗中，會使用 prefab。</span><span class="sxs-lookup"><span data-stu-id="20da0-129">We have now created a prefab that will be used when spawning or instantiating new players in a shared experience.</span></span>

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="20da0-131">注意： 請確定，遊戲物件已成功複製到 「 prefabs"資料夾中刪除從您的階層之前。</span><span class="sxs-lookup"><span data-stu-id="20da0-131">Note: ensure that the game object has successfully copied into the "prefabs" folder before deleting it from your hierarchy.</span></span>

7. <span data-ttu-id="20da0-132">（使用類似的步驟 3 的指示），階層中建立新的物件並將它命名為"SharedPlayground。 」</span><span class="sxs-lookup"><span data-stu-id="20da0-132">Create a new object in the hierarchy (using similar instructions to that of Step 3), and name it "SharedPlayground."</span></span> <span data-ttu-id="20da0-133">然後，按一下 [新增元件]，並搜尋 「 一般網路管理員 」，然後按一下以新增泛型網路管理員元件。</span><span class="sxs-lookup"><span data-stu-id="20da0-133">Then, click "Add Component" and search for "generic network manager" and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="20da0-134">將物件的位置變更為 x = 0，y = 0，且 z = 0。</span><span class="sxs-lookup"><span data-stu-id="20da0-134">Change the position of the object to x=0, y=0, and z =0.</span></span>

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="20da0-136">恭喜！</span><span class="sxs-lookup"><span data-stu-id="20da0-136">Congratulations</span></span>

<span data-ttu-id="20da0-137">一旦上述所有步驟都已完成，而在建置程序完成時，按下 [播放] 按鈕，並連接 HoloLens 2 時，您應該會看到球體四處移動，當您移動您 ！</span><span class="sxs-lookup"><span data-stu-id="20da0-137">Once all the steps above are complete, and the build process is complete, when you press the play button and connect your HoloLens 2, you should see a sphere moving around as you move your head!</span></span> <span data-ttu-id="20da0-138">這會顯示任何使用者加入您的 Unity 專案 ！</span><span class="sxs-lookup"><span data-stu-id="20da0-138">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="20da0-139">[下一課：第 4 課 Sharing(Photon)](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="20da0-139">[Next Lesson: Sharing(Photon) Lesson 4](mrlearning-sharing(photon)-ch4.md)</span></span>

