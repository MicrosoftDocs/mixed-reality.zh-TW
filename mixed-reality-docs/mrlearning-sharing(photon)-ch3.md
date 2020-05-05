---
title: 多使用者功能教學課程 - 4。 與多個使用者共用物件移動
description: 完成此課程以了解如何在 HoloLens 2 應用程式中實作使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 41b62eb2d9f400d0af341c9fcce887c72af7a3aa
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610656"
---
# <a name="3-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="56ff5-105">3.與多個使用者共用物件移動</span><span class="sxs-lookup"><span data-stu-id="56ff5-105">3. Sharing object movements with multiple users</span></span>

<span data-ttu-id="56ff5-106">在本教學課程中，您將了解如何共用物件的移動，讓共用體驗的所有參與者都可以共同作業及查看彼此的互動。</span><span class="sxs-lookup"><span data-stu-id="56ff5-106">In this tutorial, you will learn how to share the movements of objects so that all participants of a shared experience can collaborate and view each others' interactions.</span></span>

## <a name="objectives"></a><span data-ttu-id="56ff5-107">目標</span><span class="sxs-lookup"><span data-stu-id="56ff5-107">Objectives</span></span>

* <span data-ttu-id="56ff5-108">設定專案來共用物件的移動</span><span class="sxs-lookup"><span data-stu-id="56ff5-108">Configure your project to share the movements of objects</span></span>
* <span data-ttu-id="56ff5-109">了解如何建立基本的多使用者共同作業應用程式</span><span class="sxs-lookup"><span data-stu-id="56ff5-109">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="56ff5-110">準備場景</span><span class="sxs-lookup"><span data-stu-id="56ff5-110">Preparing the scene</span></span>

<span data-ttu-id="56ff5-111">在本節中，您將藉由新增教學課程預製物件 (Prefab) 來準備場景。</span><span class="sxs-lookup"><span data-stu-id="56ff5-111">In this section, you will prepare the scene by adding the tutorial prefab.</span></span>

<span data-ttu-id="56ff5-112">在 [專案] 視窗中，瀏覽至 [資產]   > [MRTK.Tutorials.MultiUserCapabilities]   > [Prefabs]  資料夾，並將**TableAnchor** 預製物件 (Prefab) 拖曳到階層視窗中的 **SharedPlayground** 物件上方，以將其作為 SharedPlayground 物件的子系來新增至您的場景：</span><span class="sxs-lookup"><span data-stu-id="56ff5-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **TableAnchor** prefab on top of the **SharedPlayground** object in the Hierarchy window to add it to your scene as a child of the SharedPlayground object:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a><span data-ttu-id="56ff5-114">設定 PUN 以具現化物件</span><span class="sxs-lookup"><span data-stu-id="56ff5-114">Configuring PUN to instantiate the objects</span></span>

<span data-ttu-id="56ff5-115">在本節中，您會將專案設定為使用上一節中建立的 RocketLauncher_Complete_Variant 預製物件，並定義其將具現化的位置。</span><span class="sxs-lookup"><span data-stu-id="56ff5-115">In this section, you will configure the project to use the RocketLauncher_Complete_Variant prefab you created in the previous section and define where it will be instantiated.</span></span>

<span data-ttu-id="56ff5-116">在 [專案] 視窗中，瀏覽至 [資產]   > [MRTK.Tutorials.MultiUserCapabilities]   > [Resources]  資料夾。</span><span class="sxs-lookup"><span data-stu-id="56ff5-116">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="56ff5-117">在 [階層] 視窗中，展開 **NetworkLobby** 物件，然後選取 **NetworkRoom** 子物件，接著在 [偵測器] 視窗中找出 **Photon Room (指令碼)** 元件，並依照下列方式進行設定：</span><span class="sxs-lookup"><span data-stu-id="56ff5-117">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="56ff5-118">在 [Photon 使用者預製物件]  欄位中，從 [Resources] 資料夾指派 **PhotonUser** 預製物件</span><span class="sxs-lookup"><span data-stu-id="56ff5-118">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-1.png)

<span data-ttu-id="56ff5-120">在仍選取 **NetworkRoom** 子物件的情況下，在 [階層] 視窗中，展開 **TableAnchor** 物件，然後在 [偵測器] 視窗中找出 **Photon Room (指令碼)** 元件，並依照下列方式進行設定：</span><span class="sxs-lookup"><span data-stu-id="56ff5-120">With the **NetworkRoom** child object still selected, in the Hierarchy window, expand the **TableAnchor** object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="56ff5-121">在 [火箭發射器位置]  欄位中，從 [階層] 視窗指派 **Table** 子物件</span><span class="sxs-lookup"><span data-stu-id="56ff5-121">To the **Rocket Launcher Location** field, assign the **Table** child object from the Hierarchy window</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a><span data-ttu-id="56ff5-123">嘗試共用物件移動的體驗</span><span class="sxs-lookup"><span data-stu-id="56ff5-123">Trying the experience with shared object movement</span></span>

<span data-ttu-id="56ff5-124">如果您現在建立了 Unity 專案並將其部署至 HoloLens，然後回到 Unity，並在應用程式於 HoloLens 上執行時，按下 [開始遊戲] 按鈕進入遊戲模式，當您在 HoloLens 中移動物件時，您將會看到物件在 Unity 中移動：</span><span class="sxs-lookup"><span data-stu-id="56ff5-124">If you now build and deploy the Unity project to your HoloLens, and then, back in Unity, press the Play button to enter Game mode while the application is running on your HoloLens, you will see the object move in Unity when you move the object in HoloLens:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section3-step1-1.gif)

## <a name="congratulations"></a><span data-ttu-id="56ff5-126">恭喜！</span><span class="sxs-lookup"><span data-stu-id="56ff5-126">Congratulations</span></span>

<span data-ttu-id="56ff5-127">您已成功設定專案來同步物件移動，而且使用者可以在其他使用者移動物件時，看到物件移動。</span><span class="sxs-lookup"><span data-stu-id="56ff5-127">You have successfully configured your project so object movements are synchronized and users can see the objects move when other users move the objects.</span></span> <span data-ttu-id="56ff5-128">在下一個教學課程中，您將會實作讓共用體驗在實體世界中對齊的功能，而使用者會在實際的實體位置看到彼此，因此物件會出現在相同的實體位置，並為所有使用者旋轉。</span><span class="sxs-lookup"><span data-stu-id="56ff5-128">In the next tutorial, you will implement functionality so the shared experience is aligned in the physical world and the users see each other in their actual physical location and so the objects appear in the same physical position and rotation for all users.</span></span>

<span data-ttu-id="56ff5-129">[下一個教學課程：4.將 Azure Spatial Anchors 整合到共用體驗](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="56ff5-129">[Next tutorial: 4. Integrating Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch4.md)</span></span>
