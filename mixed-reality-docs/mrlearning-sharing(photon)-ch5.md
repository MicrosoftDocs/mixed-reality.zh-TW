---
title: 多使用者功能教學課程-5。 將 Azure 空間錨點整合到共用體驗中
description: 完成此課程，以瞭解如何在 HoloLens 2 應用程式中執行多使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: c1b64b9d32409d61284f21ca216417ece4767d1b
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553806"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="9a66a-105">5. 將 Azure 空間錨點整合到共用體驗中</span><span class="sxs-lookup"><span data-stu-id="9a66a-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="9a66a-106">在這一課，您將瞭解如何將 Azure 空間錨點（ASA）整合到我們的共用體驗中。</span><span class="sxs-lookup"><span data-stu-id="9a66a-106">In this lesson, you'll learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="9a66a-107">如果實體環境是錨定虛擬經驗，讓所有參與者在相同的實體位置中看到物件，則 ASA 允許多個共置的裝置擁有共同的參考。</span><span class="sxs-lookup"><span data-stu-id="9a66a-107">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

## <a name="objectives"></a><span data-ttu-id="9a66a-108">目標</span><span class="sxs-lookup"><span data-stu-id="9a66a-108">Objectives</span></span>

* <span data-ttu-id="9a66a-109">將 ASA 整合到多裝置對齊的共用體驗。</span><span class="sxs-lookup"><span data-stu-id="9a66a-109">Integrate ASA into a shared experience for multi-device alignment.</span></span>
* <span data-ttu-id="9a66a-110">瞭解 ASA 如何在本機共用體驗的內容中運作的基本概念。</span><span class="sxs-lookup"><span data-stu-id="9a66a-110">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

## <a name="instructions"></a><span data-ttu-id="9a66a-111">指示</span><span class="sxs-lookup"><span data-stu-id="9a66a-111">Instructions</span></span>

1. <span data-ttu-id="9a66a-112">選取 MixedRealityPlayspace 父物件底下的 [TableAnchor] prefab，然後將它刪除。</span><span class="sxs-lookup"><span data-stu-id="9a66a-112">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. <span data-ttu-id="9a66a-114">在 專案 視圖中，移至 資產-> 資源-> Prefabs，然後將 TableAnchor prefab 拖曳至 SharedPlayground 物件上方，使其成為子系。</span><span class="sxs-lookup"><span data-stu-id="9a66a-114">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>

3. <span data-ttu-id="9a66a-115">展開 MixedRealityPlayspace 父物件 TableAnchor 物件，並同時展開 [按鈕] 物件。</span><span class="sxs-lookup"><span data-stu-id="9a66a-115">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span>

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="9a66a-117">現在，在階層中選取 [ShareAzureAnchorButton]，並將您的注意力移至 [偵測器] 面板。</span><span class="sxs-lookup"><span data-stu-id="9a66a-117">Now in the hierarchy, select ShareAzureAnchorButton and move your attention to the Inspector panel.</span></span> <span data-ttu-id="9a66a-118">向下卷到下圖所示的下拉式功能表，選取 [AnchorModuleScript]，然後按一下 [ShareAnchorNetwork （）]。</span><span class="sxs-lookup"><span data-stu-id="9a66a-118">Scroll down to the drop-down menu shown in the image below, select AnchorModuleScript and click ShareAnchorNetwork().</span></span>

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="9a66a-120">選取 [GetAzureAnchorButton] （請參閱步驟4），並將您的注意力移回 [偵測器] 面板。</span><span class="sxs-lookup"><span data-stu-id="9a66a-120">Select GetAzureAnchorButton (see Step 4) and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="9a66a-121">向下卷到下圖中顯示的下拉式功能表，選取 [AnchorModuleScript]，按一下 [GetSharedAnchorNetwork （）]，然後 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="9a66a-121">Scroll down to the drop-down menu displayed in the image below, select AnchorModuleScript, click GetSharedAnchorNetwork(), and save.</span></span>

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="9a66a-123">重複步驟4，將 StartAzureSession （）函式連結至 StartAzureSessionButton。</span><span class="sxs-lookup"><span data-stu-id="9a66a-123">Repeat step 4 to hook up the StartAzureSession () function to the StartAzureSessionButton.</span></span>

7. <span data-ttu-id="9a66a-124">重複步驟4，將 CreateAzureAnchor （）函式連結至 CreateAzureAnchorButton，並確認 TableAnchor 物件已指派給函式的參數 ' 遊戲物件 ' 欄位。</span><span class="sxs-lookup"><span data-stu-id="9a66a-124">Repeat step 4 to hook up the CreateAzureAnchor () function to the CreateAzureAnchorButton and verify that the TableAnchor object is assigned to the function's parameter 'Game Object' field.</span></span>

8. <span data-ttu-id="9a66a-125">遵循將[場景連線至 azure 資源](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource)指示，以新增您的 Azure 空間錨點服務認證。</span><span class="sxs-lookup"><span data-stu-id="9a66a-125">Follow the [Connect the scene to the Azure resource](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) instructions to add your Azure Spatial Anchors service credentials.</span></span>

9. <span data-ttu-id="9a66a-126">若要測試共用模組，請按一下 [啟動 Azure ASA 會話] 按鈕，這會啟動 azure 空間錨點會話，然後按一下 [建立 Azure 錨點] 按鈕來建立 azure 錨點。</span><span class="sxs-lookup"><span data-stu-id="9a66a-126">To test the sharing module, click the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button.</span></span> <span data-ttu-id="9a66a-127">等候 azure 錨點建立。</span><span class="sxs-lookup"><span data-stu-id="9a66a-127">Wait for the azure anchor to get created.</span></span> <span data-ttu-id="9a66a-128">建立 azure 錨點之後，請按一下 [共用 Azure 錨點] 按鈕，從 HoloLens 共用建立的 azure 錨點。</span><span class="sxs-lookup"><span data-stu-id="9a66a-128">Once the azure anchor is created, click the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

10. <span data-ttu-id="9a66a-129">若要在另一部 HoloLens 中接收共用的 azure 錨點，請按一下 [啟動 Azure ASA 會話] 以啟動並進入目前的 ASA 會話</span><span class="sxs-lookup"><span data-stu-id="9a66a-129">To receive the shared azure anchor in another HoloLens, click the "Start Azure ASA Session" to start and get in to the current ASA session</span></span>

11. <span data-ttu-id="9a66a-130">按一下 [取得 Azure 錨點] 按鈕，以從其他 HoloLens 取得共用的 Azure 錨點。</span><span class="sxs-lookup"><span data-stu-id="9a66a-130">Click the "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

## <a name="congratulations"></a><span data-ttu-id="9a66a-131">恭喜</span><span class="sxs-lookup"><span data-stu-id="9a66a-131">Congratulations</span></span>

<span data-ttu-id="9a66a-132">在這一課，您已瞭解如何整合 Azure 的強大新空間錨點，以將共置的裝置對齊共用體驗！</span><span class="sxs-lookup"><span data-stu-id="9a66a-132">In this lesson, you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="9a66a-133">這也會結束共用模組。</span><span class="sxs-lookup"><span data-stu-id="9a66a-133">This also concludes the Sharing Module.</span></span> <span data-ttu-id="9a66a-134">我們已瞭解如何設定新的 Photon 帳戶、將 Photon 和雙關語整合到新的 Unity 應用程式、設定虛擬人偶和共用物件，最後使用 ASA 來對齊多個參與者。</span><span class="sxs-lookup"><span data-stu-id="9a66a-134">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configure avatars and shared objects, and finally align multiple participants using ASA.</span></span>
