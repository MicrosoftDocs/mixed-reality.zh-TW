---
title: 多使用者功能教學課程 - 5。 將 Azure Spatial Anchors 整合到共用體驗
description: 完成此課程以了解如何在 HoloLens 2 應用程式中實作使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7fb8cd03b2f3739037dee38786493bfd9012f6ce
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031679"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="1f85f-105">5.將 Azure Spatial Anchors 整合到共用體驗</span><span class="sxs-lookup"><span data-stu-id="1f85f-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="1f85f-106">在這一課中，您將了解如何將 Azure Spatial Anchors (ASA) 整合到我們的共用體驗中。</span><span class="sxs-lookup"><span data-stu-id="1f85f-106">In this lesson, you'll learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="1f85f-107">如果實體環境已用於對虛擬經驗建立錨點，則 ASA 可允許多個共置裝置擁有共同的參考，讓所有參與者可看到相同實體位置中的物件。</span><span class="sxs-lookup"><span data-stu-id="1f85f-107">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

## <a name="objectives"></a><span data-ttu-id="1f85f-108">目標</span><span class="sxs-lookup"><span data-stu-id="1f85f-108">Objectives</span></span>

* <span data-ttu-id="1f85f-109">將 ASA 整合到多個裝置一致的共用體驗。</span><span class="sxs-lookup"><span data-stu-id="1f85f-109">Integrate ASA into a shared experience for multi-device alignment.</span></span>
* <span data-ttu-id="1f85f-110">了解 ASA 如何在本機共用體驗內容中運作的基本概念。</span><span class="sxs-lookup"><span data-stu-id="1f85f-110">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

## <a name="instructions"></a><span data-ttu-id="1f85f-111">指示</span><span class="sxs-lookup"><span data-stu-id="1f85f-111">Instructions</span></span>

1. <span data-ttu-id="1f85f-112">選取 MixedRealityPlayspace 父物件底下的 TableAnchor Prefab，然後將其刪除。</span><span class="sxs-lookup"><span data-stu-id="1f85f-112">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. <span data-ttu-id="1f85f-114">在 [專案] 檢視中移至 [資產] -> [資源]-> [Prefabs]，然後將 TableAnchor Prefab 拖曳至 SharedPlayground 物件上方，使其成為子系。</span><span class="sxs-lookup"><span data-stu-id="1f85f-114">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>

3. <span data-ttu-id="1f85f-115">展開 MixedRealityPlayspace 父物件：TableAnchor 物件，並同時展開 [按鈕] 物件。</span><span class="sxs-lookup"><span data-stu-id="1f85f-115">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span>

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="1f85f-117">現在，在階層中選取 [ShareAzureAnchorButton]，並將您的注意力移至 [偵測器] 面板。</span><span class="sxs-lookup"><span data-stu-id="1f85f-117">Now in the hierarchy, select ShareAzureAnchorButton and move your attention to the Inspector panel.</span></span> <span data-ttu-id="1f85f-118">向下捲動到下圖所示的下拉式功能表並選取 [AnchorModuleScript]，然後按一下 [ShareAnchorNetwork()]。</span><span class="sxs-lookup"><span data-stu-id="1f85f-118">Scroll down to the drop-down menu shown in the image below, select AnchorModuleScript and click ShareAnchorNetwork().</span></span>

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="1f85f-120">選取 [GetAzureAnchorButton] \(請參閱步驟4)，並將您的注意力移回 [偵測器] 面板。</span><span class="sxs-lookup"><span data-stu-id="1f85f-120">Select GetAzureAnchorButton (see Step 4) and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="1f85f-121">向下捲動到下圖所示的下拉式功能表並選取 [AnchorModuleScript]，然後按一下 [GetSharedAnchorNetwork()] 並儲存。</span><span class="sxs-lookup"><span data-stu-id="1f85f-121">Scroll down to the drop-down menu displayed in the image below, select AnchorModuleScript, click GetSharedAnchorNetwork(), and save.</span></span>

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="1f85f-123">重複步驟 4，將 StartAzureSession () 函式連結至 StartAzureSessionButton。</span><span class="sxs-lookup"><span data-stu-id="1f85f-123">Repeat step 4 to hook up the StartAzureSession () function to the StartAzureSessionButton.</span></span>

7. <span data-ttu-id="1f85f-124">重複步驟 4，將 CreateAzureAnchor () 函式連結至 CreateAzureAnchorButton，並確認 TableAnchor 物件已指派給函式的 'Game Object' 參數欄位。</span><span class="sxs-lookup"><span data-stu-id="1f85f-124">Repeat step 4 to hook up the CreateAzureAnchor () function to the CreateAzureAnchorButton and verify that the TableAnchor object is assigned to the function's parameter 'Game Object' field.</span></span>

8. <span data-ttu-id="1f85f-125">遵循[將場景連線至 Azure 資源](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource)的指示，以新增您的 Azure Spatial Anchors 服務認證。</span><span class="sxs-lookup"><span data-stu-id="1f85f-125">Follow the [Connect the scene to the Azure resource](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) instructions to add your Azure Spatial Anchors service credentials.</span></span>

9. <span data-ttu-id="1f85f-126">若要測試共用模組，請按一下 [啟動 Azure ASA 工作階段] 按鈕來啟動 Azure Spatial Anchors 工作階段，然後按一下 [建立 Azure 錨點] 按鈕來建立 Azure 錨點。</span><span class="sxs-lookup"><span data-stu-id="1f85f-126">To test the sharing module, click the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button.</span></span> <span data-ttu-id="1f85f-127">等候 Azure 錨點建立。</span><span class="sxs-lookup"><span data-stu-id="1f85f-127">Wait for the azure anchor to get created.</span></span> <span data-ttu-id="1f85f-128">建立 Azure 錨點之後，請按一下 [共用 Azure 錨點] 按鈕，從 HoloLens 共用建立的 Azure 錨點。</span><span class="sxs-lookup"><span data-stu-id="1f85f-128">Once the azure anchor is created, click the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

10. <span data-ttu-id="1f85f-129">若要在另一部 HoloLens 中接收共用的 Azure 錨點，請按一下 [啟動 Azure ASA 工作階段] 以啟動並進入目前的 ASA 工作階段</span><span class="sxs-lookup"><span data-stu-id="1f85f-129">To receive the shared azure anchor in another HoloLens, click the "Start Azure ASA Session" to start and get in to the current ASA session</span></span>

11. <span data-ttu-id="1f85f-130">按一下 [取得 Azure 錨點] 按鈕，以從其他 HoloLens 取得共用的 Azure 錨點。</span><span class="sxs-lookup"><span data-stu-id="1f85f-130">Click the "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

## <a name="congratulations"></a><span data-ttu-id="1f85f-131">恭喜！</span><span class="sxs-lookup"><span data-stu-id="1f85f-131">Congratulations</span></span>

<span data-ttu-id="1f85f-132">在這一課，您已了解如何整合 Azure 的強大新 Spatial Anchors，使共置的裝置在共用體驗中達到一致！</span><span class="sxs-lookup"><span data-stu-id="1f85f-132">In this lesson, you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="1f85f-133">共用課程模組也在此結束。</span><span class="sxs-lookup"><span data-stu-id="1f85f-133">This also concludes the Sharing Module.</span></span> <span data-ttu-id="1f85f-134">我們已了解如何設定新的 Photon 帳戶、將 Photon 和 PUN 整合到新的 Unity 應用程式、設定虛擬人偶和共用物件，最後使用 ASA 來調整多個參與者。</span><span class="sxs-lookup"><span data-stu-id="1f85f-134">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configure avatars and shared objects, and finally align multiple participants using ASA.</span></span>
