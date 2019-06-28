---
title: 學習模組共用 HoloLens 2 MR
description: 完成這個課程來了解如何實作 HoloLens 2 應用程式內的多使用者分享的經驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 941bdc64ed614d5ce71f58f05585d0dfc86c3bb7
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415929"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a><span data-ttu-id="3218f-104">Azure 空間的錨點和共用的經驗</span><span class="sxs-lookup"><span data-stu-id="3218f-104">Azure Spatial Anchors and Shared Experiences</span></span>

<span data-ttu-id="3218f-105">在這一課中，我們將了解如何將 Azure 空間的錨點 (ASA) 整合到我們分享經驗。</span><span class="sxs-lookup"><span data-stu-id="3218f-105">In this lesson, we will learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="3218f-106">ASA 允許多個位於相同位置的裝置，其以虛擬的錨點的實體環境體驗，所有參與者都看到相同的實體位置中的物件有共識。</span><span class="sxs-lookup"><span data-stu-id="3218f-106">ASA allows multiple co-located devices to have a common understanding if their physical environment in order to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="3218f-107">繼續進行這一課之前，我們必須完成 ASA 的學習模組，將討論 ASA 基本概念、 Azure 帳戶並建立資源和其他我們可以將 ASA 整合到我們分享經驗之前所需的基本建築物區塊。</span><span class="sxs-lookup"><span data-stu-id="3218f-107">Before proceeding with this lesson, we will need to complete the ASA Learning Module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="3218f-108">目標：</span><span class="sxs-lookup"><span data-stu-id="3218f-108">Objectives:</span></span>

- <span data-ttu-id="3218f-109">將 ASA 整合到 multi-device 對齊的共用體驗</span><span class="sxs-lookup"><span data-stu-id="3218f-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
- <span data-ttu-id="3218f-110">了解 ASA 本機的共用經驗的內容中的運作方式的基本概念</span><span class="sxs-lookup"><span data-stu-id="3218f-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="3218f-111">指示</span><span class="sxs-lookup"><span data-stu-id="3218f-111">Instructions</span></span>

1. <span data-ttu-id="3218f-112">將專案儲存在上一課 （control + S），並命名"HLSharedProjectMainPart5.unity 」 以便更輕鬆地尋找當您再次需要它。</span><span class="sxs-lookup"><span data-stu-id="3218f-112">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="3218f-113">選取 TableAnchor prefab 底下 「 MixedRealityPlayspace"的父物件，並將它刪除。</span><span class="sxs-lookup"><span data-stu-id="3218f-113">Select the TableAnchor prefab underneath  the "MixedRealityPlayspace" parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)



3.  <span data-ttu-id="3218f-115">在 專案檢視中，移至資產 > 資源 > Prefabs 和拖曳 TableAnchor prefab 物件上方的 SharedPlayground 讓子系。</span><span class="sxs-lookup"><span data-stu-id="3218f-115">In the Project view go to Assets > Resources > Prefabs and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>
4.  <span data-ttu-id="3218f-116">展開 「 MixedRealityPlayspace"的父物件，則 「 TableAnchor 」 物件，然後展開的 「 按鈕 」 物件。</span><span class="sxs-lookup"><span data-stu-id="3218f-116">Expand the "MixedRealityPlayspace" parent object, then the "TableAnchor" object, and expand the "buttons" object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="3218f-118">現在在階層中，選取 「 ShareAzureAnchorButton"並移動您注意到 [偵測器] 面板。</span><span class="sxs-lookup"><span data-stu-id="3218f-118">Now in the hierarchy, select the "ShareAzureAnchorButton" and move your attention to the inspector panel.</span></span> <span data-ttu-id="3218f-119">向下捲動，如下圖所示的下拉式功能表並選取 「 AnchorModuleScript 」 並按一下 「 ShareAnchorNetework()。 」</span><span class="sxs-lookup"><span data-stu-id="3218f-119">Scroll down to the dropdown menu shown in the image below, and select "AnchorModuleScript" and click on "ShareAnchorNetework()."</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="3218f-121">如同步驟 4 中，選取 「 GetAzureAnchorButton"並移動您回到 [偵測器] 面板的注意。</span><span class="sxs-lookup"><span data-stu-id="3218f-121">Much like step 4, select the "GetAzureAnchorButton" and move your attention back to the inspector panel.</span></span> <span data-ttu-id="3218f-122">向下捲動，如下圖所示的下拉式功能表並選取 「 AnchorModuleScript 」 並按一下 「 GetSharedAnchorNetwork()。 」</span><span class="sxs-lookup"><span data-stu-id="3218f-122">Scroll down to the dropdown menu shown in the image below, and select "AnchorModuleScript" and click on "GetSharedAnchorNetwork()."</span></span> <span data-ttu-id="3218f-123">然後儲存。</span><span class="sxs-lookup"><span data-stu-id="3218f-123">Then save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a><span data-ttu-id="3218f-125">恭喜！</span><span class="sxs-lookup"><span data-stu-id="3218f-125">Congratulations</span></span>

<span data-ttu-id="3218f-126">在這一課，您了解如何整合 Azure 的強大新空間錨點來對齊共的裝置共用體驗中的內容 ！</span><span class="sxs-lookup"><span data-stu-id="3218f-126">In this Lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="3218f-127">這一課也結束時，共用的模組。</span><span class="sxs-lookup"><span data-stu-id="3218f-127">This lesson also concludes the Sharing Module.</span></span> <span data-ttu-id="3218f-128">我們了解如何設定新的 Photon 帳戶，請將 Photon 與自己使用這個雙關語整合到新的 Unity 應用程式中，設定虛擬人偶 」 和 「 共用的物件，以及最後對齊這些使用 ASA 的多個參與者。</span><span class="sxs-lookup"><span data-stu-id="3218f-128">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configuring avatars and shared objects, and finally aligning multiple participants using ASA.</span></span> 

