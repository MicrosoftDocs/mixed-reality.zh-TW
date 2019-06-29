---
title: 學習模組共用 HoloLens 2 MR
description: 完成這個課程來了解如何實作 HoloLens 2 應用程式內的多使用者分享的經驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 2a16d318c6d749bcbf6ed9db0d6cd2228a6ea06e
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465207"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a><span data-ttu-id="ed1a0-104">Azure 空間的錨點和共用的經驗</span><span class="sxs-lookup"><span data-stu-id="ed1a0-104">Azure Spatial Anchors and shared experiences</span></span>

<span data-ttu-id="ed1a0-105">在這一課中，我們了解如何將 Azure 空間的錨點 (ASA) 整合到我們分享經驗。</span><span class="sxs-lookup"><span data-stu-id="ed1a0-105">In this lesson, we learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="ed1a0-106">ASA 可讓多個位於相同位置的裝置有常見的參考，如果其實體的環境是錨點的虛擬體驗，使得所有參與者都看到相同的實體位置中的物件。</span><span class="sxs-lookup"><span data-stu-id="ed1a0-106">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="ed1a0-107">繼續進行這一課之前，我們必須完成 ASA 的學習模組，將討論 ASA 基本概念、 Azure 帳戶並建立資源和其他我們可以將 ASA 整合到我們分享經驗之前所需的基本建築物區塊。</span><span class="sxs-lookup"><span data-stu-id="ed1a0-107">Before proceeding with this lesson, we'll need to complete the ASA learning module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="ed1a0-108">目標：</span><span class="sxs-lookup"><span data-stu-id="ed1a0-108">Objectives:</span></span>

- <span data-ttu-id="ed1a0-109">將 ASA 整合到 multi-device 對齊的共用體驗</span><span class="sxs-lookup"><span data-stu-id="ed1a0-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
- <span data-ttu-id="ed1a0-110">了解 ASA 本機的共用經驗的內容中的運作方式的基本概念</span><span class="sxs-lookup"><span data-stu-id="ed1a0-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="ed1a0-111">指示</span><span class="sxs-lookup"><span data-stu-id="ed1a0-111">Instructions</span></span>

1. <span data-ttu-id="ed1a0-112">將專案儲存在上一課 （control + S），並命名"HLSharedProjectMainPart5.unity 」 以便更輕鬆地尋找當您再次需要它。</span><span class="sxs-lookup"><span data-stu-id="ed1a0-112">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="ed1a0-113">選取 TableAnchor prefab 下方 MixedRealityPlayspace 父物件，並將它刪除。</span><span class="sxs-lookup"><span data-stu-id="ed1a0-113">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)



3.  <span data-ttu-id="ed1a0-115">在 專案檢視移至 資產-> 資源-> Prefabs，並將拖曳 TableAnchor prefab 物件上方的 SharedPlayground 讓子系。</span><span class="sxs-lookup"><span data-stu-id="ed1a0-115">In the Project view go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>
4.  <span data-ttu-id="ed1a0-116">展開 MixedRealityPlayspace 父物件、 TableAnchor 物件，然後展開 [按鈕] 物件。</span><span class="sxs-lookup"><span data-stu-id="ed1a0-116">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="ed1a0-118">現在在階層中，選取 ShareAzureAnchorButton，並移動您的注意 Inaspector 面板。</span><span class="sxs-lookup"><span data-stu-id="ed1a0-118">Now in the hierarchy, select ShareAzureAnchorButton, and move your attention to the Inaspector panel.</span></span> <span data-ttu-id="ed1a0-119">向下捲動，如下圖所示的下拉式選單，選取 AnchorModuleScript 並按一下 ShareAnchorNetework()。</span><span class="sxs-lookup"><span data-stu-id="ed1a0-119">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript and click ShareAnchorNetework().</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="ed1a0-121">選取 GetAzureAnchorButton （請參閱步驟 4），並移動您回到 [偵測器] 面板的注意。</span><span class="sxs-lookup"><span data-stu-id="ed1a0-121">Select GetAzureAnchorButton (see Step 4), and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="ed1a0-122">向下捲動，如下圖所示的下拉式選單和選取 AnchorModuleScript，並按一下 GetSharedAnchorNetwork()，然後儲存。</span><span class="sxs-lookup"><span data-stu-id="ed1a0-122">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript, and click GetSharedAnchorNetwork(), and save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a><span data-ttu-id="ed1a0-124">恭喜！</span><span class="sxs-lookup"><span data-stu-id="ed1a0-124">Congratulations</span></span>

<span data-ttu-id="ed1a0-125">在這一課，您了解如何整合 Azure 的強大新空間錨點來對齊共的裝置共用體驗中的內容 ！</span><span class="sxs-lookup"><span data-stu-id="ed1a0-125">In this Lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="ed1a0-126">這一課也結束時，共用的模組。</span><span class="sxs-lookup"><span data-stu-id="ed1a0-126">This lesson also concludes the Sharing Module.</span></span> <span data-ttu-id="ed1a0-127">我們了解如何設定新的 Photon 帳戶，請將 Photon 與自己使用這個雙關語整合到新的 Unity 應用程式中，設定虛擬人偶 」 和 「 共用的物件，以及最後對齊這些使用 ASA 的多個參與者。</span><span class="sxs-lookup"><span data-stu-id="ed1a0-127">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configuring avatars and shared objects, and finally aligning multiple participants using ASA.</span></span> 

