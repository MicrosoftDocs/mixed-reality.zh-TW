---
title: HoloLens 2 的 MR 學習共用模組
description: 完成此課程, 以瞭解如何在 HoloLens 2 應用程式中執行多使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 1ae880208e79e2e045bd5e7298db260b7f0b2232
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293631"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a><span data-ttu-id="0e8ac-104">Azure 空間錨點和共用體驗</span><span class="sxs-lookup"><span data-stu-id="0e8ac-104">Azure Spatial Anchors and shared experiences</span></span>

<span data-ttu-id="0e8ac-105">在本課程中, 我們將瞭解如何將 Azure 空間錨點 (ASA) 整合到我們的共用體驗中。</span><span class="sxs-lookup"><span data-stu-id="0e8ac-105">In this lesson, we learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="0e8ac-106">如果實體環境是錨定虛擬經驗, 讓所有參與者在相同的實體位置中看到物件, 則 ASA 允許多個共置的裝置擁有共同的參考。</span><span class="sxs-lookup"><span data-stu-id="0e8ac-106">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="0e8ac-107">繼續進行本課程之前, 我們必須先完成 ASA 學習課程模組, 其中將涵蓋 ASA 基本概念、Azure 帳戶和資源建立, 以及在我們將 ASA 整合到我們的共用體驗之前所需的其他基本建築物組塊。</span><span class="sxs-lookup"><span data-stu-id="0e8ac-107">Before proceeding with this lesson, we'll need to complete the ASA learning module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="0e8ac-108">目標</span><span class="sxs-lookup"><span data-stu-id="0e8ac-108">Objectives:</span></span>

- <span data-ttu-id="0e8ac-109">將 ASA 整合到多裝置對齊的共用體驗。</span><span class="sxs-lookup"><span data-stu-id="0e8ac-109">Integrate ASA into a shared experience for multi-device alignment.</span></span>
- <span data-ttu-id="0e8ac-110">瞭解 ASA 如何在本機共用體驗的內容中運作的基本概念。</span><span class="sxs-lookup"><span data-stu-id="0e8ac-110">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

### <a name="instructions"></a><span data-ttu-id="0e8ac-111">指示</span><span class="sxs-lookup"><span data-stu-id="0e8ac-111">Instructions</span></span>

1. <span data-ttu-id="0e8ac-112">儲存上一課 (control + S) 中的專案, 並將它命名為 "HLSharedProjectMainPart5", 以便在您再次需要時更容易找到。</span><span class="sxs-lookup"><span data-stu-id="0e8ac-112">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="0e8ac-113">選取 MixedRealityPlayspace 父物件底下的 [TableAnchor] prefab, 然後將它刪除。</span><span class="sxs-lookup"><span data-stu-id="0e8ac-113">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3.  <span data-ttu-id="0e8ac-115">在 專案 視圖中, 移至 資產-> 資源-> Prefabs, 然後將 TableAnchor prefab 拖曳至 SharedPlayground 物件上方, 使其成為子系。</span><span class="sxs-lookup"><span data-stu-id="0e8ac-115">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>
4.  <span data-ttu-id="0e8ac-116">展開 MixedRealityPlayspace 父物件 TableAnchor 物件, 並同時展開 [按鈕] 物件。</span><span class="sxs-lookup"><span data-stu-id="0e8ac-116">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="0e8ac-118">現在, 在階層中選取 [ShareAzureAnchorButton], 並將您的注意力移至 [Inaspector] 面板。</span><span class="sxs-lookup"><span data-stu-id="0e8ac-118">Now in the hierarchy, select ShareAzureAnchorButton, and move your attention to the Inaspector panel.</span></span> <span data-ttu-id="0e8ac-119">向下流覽至下圖所示的下拉式功能表, 然後選取 [AnchorModuleScript], 再按一下 [ShareAnchorNetework ()]。</span><span class="sxs-lookup"><span data-stu-id="0e8ac-119">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript and click ShareAnchorNetework().</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="0e8ac-121">選取 [GetAzureAnchorButton] (請參閱步驟 4), 並將您的注意力移回 [檢查] 面板。</span><span class="sxs-lookup"><span data-stu-id="0e8ac-121">Select GetAzureAnchorButton (see Step 4), and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="0e8ac-122">向下流覽至下圖所示的下拉式功能表, 然後選取 [AnchorModuleScript], 再按一下 [GetSharedAnchorNetwork ()], 然後按一下 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="0e8ac-122">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript, and click GetSharedAnchorNetwork(), and save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="0e8ac-124">若要測試共用模組, 請按一下 [啟動 Azure ASA 會話] 按鈕, 以啟動 azure 空間錨點會話, 然後按一下 [建立 Azure 錨點] 按鈕以建立 azure 錨點, 並等待一段時間讓 azure 錨點建立。</span><span class="sxs-lookup"><span data-stu-id="0e8ac-124">To test the sharing module, click on the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button and wait for sometime for the azure anchor to get created.</span></span> <span data-ttu-id="0e8ac-125">建立 azure 錨點之後, 請按一下 [共用 Azure 錨點] 按鈕, 從 HoloLens 共用建立的 azure 錨點。</span><span class="sxs-lookup"><span data-stu-id="0e8ac-125">Once the azure anchor is created then click on the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

7. <span data-ttu-id="0e8ac-126">若要在另一部 HoloLens 中接收共用的 azure 錨點, 請按一下 [啟動 Azure ASA 會話] 來啟動並進入目前的 ASA 會話, 然後按一下 [取得 Azure 錨點] 按鈕, 從其他 HoloLens 取得共用的 azure 錨點。</span><span class="sxs-lookup"><span data-stu-id="0e8ac-126">To recieve the shared azure anchor in another HoloLens, click on the "Start Azure ASA Session" to start and get in to the current ASA session and click on "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

   > <span data-ttu-id="0e8ac-127">注意:個別按鈕上對應動作的所有詳細資料都會顯示在 [調試] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="0e8ac-127">Note: All details of the corresponding actions on the individual buttons will be displayed in the debug window.</span></span>

## <a name="congratulations"></a><span data-ttu-id="0e8ac-128">恭喜！</span><span class="sxs-lookup"><span data-stu-id="0e8ac-128">Congratulations</span></span>

<span data-ttu-id="0e8ac-129">在這一課, 您已瞭解如何整合 Azure 強大的新空間錨點, 以將共置的裝置對齊共用體驗!</span><span class="sxs-lookup"><span data-stu-id="0e8ac-129">In this Lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="0e8ac-130">本課程也會結束共用模組。</span><span class="sxs-lookup"><span data-stu-id="0e8ac-130">This lesson also concludes the Sharing Module.</span></span> <span data-ttu-id="0e8ac-131">我們已瞭解如何設定新的 Photon 帳戶、將 Photon 和雙關語整合到新的 Unity 應用程式、設定虛擬人偶和共用物件, 最後使用 ASA 來對齊多個參與者。</span><span class="sxs-lookup"><span data-stu-id="0e8ac-131">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configuring avatars and shared objects, and finally aligning multiple participants using ASA.</span></span> 

