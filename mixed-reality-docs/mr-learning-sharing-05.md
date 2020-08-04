---
title: 多使用者功能教學課程 - 5。 將 Azure Spatial Anchors 整合到共用體驗
description: 完成此課程以了解如何在 HoloLens 2 應用程式中實作使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: fc8e20a9ddaa595db0a3d59975e7c785d01c0a6d
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376580"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="c2618-105">5.將 Azure Spatial Anchors 整合到共用體驗</span><span class="sxs-lookup"><span data-stu-id="c2618-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="c2618-106">在此教學課程中，您將了解如何將 Azure Spatial Anchors (ASA) 整合到共用體驗中。</span><span class="sxs-lookup"><span data-stu-id="c2618-106">In this tutorial, you will learn how to integrate Azure Spatial Anchors (ASA) into the shared experience.</span></span> <span data-ttu-id="c2618-107">ASA 可讓多部裝置共同參照實體世界，讓使用者可以看到實際實體位置中的彼此，並看到相同位置中的共用體驗。</span><span class="sxs-lookup"><span data-stu-id="c2618-107">ASA allows multiple devices to have a common reference to the physical world so that the users see each other in their actual physical location and see the shared experience in the same place.</span></span>

## <a name="objectives"></a><span data-ttu-id="c2618-108">目標</span><span class="sxs-lookup"><span data-stu-id="c2618-108">Objectives</span></span>

* <span data-ttu-id="c2618-109">將 ASA 整合到多個裝置一致的共用體驗</span><span class="sxs-lookup"><span data-stu-id="c2618-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
* <span data-ttu-id="c2618-110">了解 ASA 如何在本機共用體驗內容中運作的基本概念</span><span class="sxs-lookup"><span data-stu-id="c2618-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="c2618-111">準備場景</span><span class="sxs-lookup"><span data-stu-id="c2618-111">Preparing the scene</span></span>

<span data-ttu-id="c2618-112">在 [階層] 視窗中，展開 **SharedPlayground** 物件，然後展開 **TableAnchor** 物件以公開其子物件：</span><span class="sxs-lookup"><span data-stu-id="c2618-112">In the Hierarchy window, expand the **SharedPlayground** object, then expand the **TableAnchor** object to expose its child objects:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section1-step1-1.png)

<span data-ttu-id="c2618-114">在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.MultiUserCapabilities] > [預製物件] 資料夾，並將**按鈕**預製物件拖曳到 **TableAnchor** 子物件上方，以將其作為 TableAnchor 物件的子系來新增至您的場景：</span><span class="sxs-lookup"><span data-stu-id="c2618-114">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **Buttons** prefab onto the **TableAnchor** child object to add it to your scene as a child of the TableAnchor object:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="c2618-116">設定按鈕以操作場景</span><span class="sxs-lookup"><span data-stu-id="c2618-116">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="c2618-117">在本節中，您將設定一系列的按鈕事件，以示範如何使用 Azure Spatial Anchors 來達到共用體驗中的空間對齊。</span><span class="sxs-lookup"><span data-stu-id="c2618-117">In this section, you will configure a series of button events demonstrating the fundamentals of how Azure Spatial Anchors can be used to achieve spatial alignment in a shared experience.</span></span>

<span data-ttu-id="c2618-118">在 [階層] 視窗中，展開 **Button** 物件，然後選取名為 **StartAzureSession** 的第一個子按鈕物件：</span><span class="sxs-lookup"><span data-stu-id="c2618-118">In the Hierarchy window, expand the **Button** object and select the first child button object named **StartAzureSession**:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-1.png)

<span data-ttu-id="c2618-120">在 [偵測器] 視窗中，找出 **Interactable (指令碼)** 元件，並設定 **OnClick ()** 事件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c2618-120">In the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="c2618-121">針對**無 (物件)** 欄位，請指派 **TableAnchor** 物件</span><span class="sxs-lookup"><span data-stu-id="c2618-121">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="c2618-122">從**無函式**下拉式清單中，選取 **AnchorModuleScript** > **StartAzureSession ()** 函式</span><span class="sxs-lookup"><span data-stu-id="c2618-122">From the **No Function** dropdown, select the **AnchorModuleScript** > **StartAzureSession ()** function</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-2.png)

<span data-ttu-id="c2618-124">在 [階層] 視窗中，選取名為 **CreateAzureAnchor** 的第二個子按鈕物件，然後在 [偵測器] 視窗中，找出 **Interactable (指令碼)** 元件，並設定 **OnClick ()** 事件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c2618-124">In the Hierarchy window, select the second child button object named **CreateAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="c2618-125">針對**無 (物件)** 欄位，請指派 **TableAnchor** 物件</span><span class="sxs-lookup"><span data-stu-id="c2618-125">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="c2618-126">從**無函式**下拉式清單中，選取 **AnchorModuleScript** > **CreateAzureAnchor ()** 函式</span><span class="sxs-lookup"><span data-stu-id="c2618-126">From the **No Function** dropdown, select the **AnchorModuleScript** > **CreateAzureAnchor ()** function</span></span>
* <span data-ttu-id="c2618-127">針對所顯示的 [無 (遊戲物件)] 欄位，請指派 **TableAnchor** 物件</span><span class="sxs-lookup"><span data-stu-id="c2618-127">To the new **None (Game Object)** field that appears, assign the **TableAnchor** object</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-3.png)

<span data-ttu-id="c2618-129">在 [階層] 視窗中，選取名為 **ShareAzureAnchor** 的第三個子按鈕物件，然後在 [偵測器] 視窗中，找出 **Interactable (指令碼)** 元件，並設定 **OnClick ()** 事件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c2618-129">In the Hierarchy window, select the third child button object named **ShareAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="c2618-130">針對**無 (物件)** 欄位，請指派 **TableAnchor** 物件</span><span class="sxs-lookup"><span data-stu-id="c2618-130">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="c2618-131">從**無函式** 下拉式清單中，選取 **AnchorModuleScript** > **CreateAzureAnchor ()** 函式</span><span class="sxs-lookup"><span data-stu-id="c2618-131">From the **No Function** dropdown, select the **SharingModuleScript** > **ShareAzureAnchor ()** function</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-4.png)

<span data-ttu-id="c2618-133">在 [階層] 視窗中，選取名為 **GetAzureAnchor** 的第四個子按鈕物件，然後在 [偵測器] 視窗中，找出 **Interactable (指令碼)** 元件，並設定 **OnClick ()** 事件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c2618-133">In the Hierarchy window, select the fourth child button object named **GetAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="c2618-134">針對**無 (物件)** 欄位，請指派 **TableAnchor** 物件</span><span class="sxs-lookup"><span data-stu-id="c2618-134">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="c2618-135">從**無函式** 下拉式清單中，選取 **SharingModuleScript** > **GetAzureAnchor ()** 函式</span><span class="sxs-lookup"><span data-stu-id="c2618-135">From the **No Function** dropdown, select the **SharingModuleScript** > **GetAzureAnchor ()** function</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="c2618-137">將場景連線至 Azure 資源</span><span class="sxs-lookup"><span data-stu-id="c2618-137">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="c2618-138">在 [階層] 視窗中，展開 **SharedPlayground** 物件，然後選取 **TableAnchor** 物件。</span><span class="sxs-lookup"><span data-stu-id="c2618-138">In the Hierarchy window, expand the **SharedPlayground** object and select the **TableAnchor** object.</span></span>

<span data-ttu-id="c2618-139">在 [偵測器] 視窗中，找出 **Spatial Anchor Manager (指令碼)** 元件，並使用 Azure Spatial Anchors 帳戶中的認證來設定 [認證] 區段，該帳戶會在本教學課程系列的[必要條件](mr-learning-sharing-01.md#prerequisites)中建立：</span><span class="sxs-lookup"><span data-stu-id="c2618-139">In the Inspector window, locate the **Spatial Anchor Manager (Script)** component and configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-sharing-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="c2618-140">在 [Spatial Anchors Account 識別碼] 欄位中，貼上 Azure Spatial Anchors 帳戶中的**帳戶識別碼**</span><span class="sxs-lookup"><span data-stu-id="c2618-140">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="c2618-141">在 [Spatial Anchors 帳戶金鑰] 欄位中，貼上 Azure Spatial Anchors 帳戶中的主要或次要**存取金鑰**</span><span class="sxs-lookup"><span data-stu-id="c2618-141">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="c2618-143">除了在場景中設定 Spatial Anchors 帳戶識別碼和金鑰，您可以針對整個專案設定；如果您有多個場景使用 ASA，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="c2618-143">Instead of setting the Spatial Anchors Account ID and Key in the scene, you can set it for your entire project, this can be advantageous if you have multiple scenes using ASA.</span></span> <span data-ttu-id="c2618-144">若要這麼做，請在 [專案] 視窗中，瀏覽至 [資產] > [AzureSpatialAnchors.SDK] > [資源] > **SpatialAnchorConfig** 資產，然後在 [偵測器] 視窗中設定這些值。</span><span class="sxs-lookup"><span data-stu-id="c2618-144">To do this, in the Project window, navigate to the Assets > AzureSpatialAnchors.SDK > Resources > **SpatialAnchorConfig** asset, then set the values in the Inspector window.</span></span>

<span data-ttu-id="c2618-145">在 [階層] 視窗中，選取 **TableAnchor** 物件，然後在 [偵測器] 視窗中尋找 **Anchor Module (指令碼)** 元件並設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c2618-145">In the Hierarchy window, select the **TableAnchor** object, then in the Inspector window, locate the **Anchor Module (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="c2618-146">在**公用共用 Pin 碼**欄位中變更幾個數字，讓 Pin 碼變成專案的專用碼</span><span class="sxs-lookup"><span data-stu-id="c2618-146">In the **Public Sharing Pin** field, change a few digits, so the pin becomes unique to your project</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-2.png)

<span data-ttu-id="c2618-148">在仍選取 **TableAnchor** 物件的情況下，在 [偵測器] 視窗中，確定**已啟用**所有指令碼元件：</span><span class="sxs-lookup"><span data-stu-id="c2618-148">With the **TableAnchor** object still selected, in the Inspector window, make sure all the script components are **enabled**:</span></span>

* <span data-ttu-id="c2618-149">勾選 **Spatial Anchor Manager (指令碼)** 元件旁的核取方塊來將其啟用</span><span class="sxs-lookup"><span data-stu-id="c2618-149">Check the checkbox next to the **Spatial Anchor Manager (Script)** components to enable it</span></span>
* <span data-ttu-id="c2618-150">勾選 **Anchor Module Script (指令碼)** 元件旁的核取方塊來將其啟用</span><span class="sxs-lookup"><span data-stu-id="c2618-150">Check the checkbox next to the **Anchor Module Script (Script)** components to enable it</span></span>
* <span data-ttu-id="c2618-151">勾選 **Sharing Module Script (指令碼)** 元件旁的核取方塊來將其啟用</span><span class="sxs-lookup"><span data-stu-id="c2618-151">Check the checkbox next to the **Sharing Module Script (Script)** components to enable it</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-3.png)

## <a name="trying-the-experience-with-spatial-alignment"></a><span data-ttu-id="c2618-153">試用空間對齊的體驗</span><span class="sxs-lookup"><span data-stu-id="c2618-153">Trying the experience with spatial alignment</span></span>

> [!NOTE]
> <span data-ttu-id="c2618-154">Azure Spatial Anchors 無法在 Unity 中執行。</span><span class="sxs-lookup"><span data-stu-id="c2618-154">Azure Spatial Anchors can not run in Unity.</span></span> <span data-ttu-id="c2618-155">因此，若要測試 Azure Spatial Anchors 功能，您必須將專案部署到至少兩個裝置。</span><span class="sxs-lookup"><span data-stu-id="c2618-155">Consequently, to test the Azure Spatial Anchors functionality, you need to deploy the project to a minimum of two devices.</span></span>

<span data-ttu-id="c2618-156">如果您現在建立 Unity 專案，並將其部署到裝置，您就可以藉由共用 Azure Anchor 識別碼，在裝置之間進行空間對齊。</span><span class="sxs-lookup"><span data-stu-id="c2618-156">If you now build and deploy the Unity project to two devices, you can achieve spatial alignment between the devices by sharing the Azure Anchor ID.</span></span> <span data-ttu-id="c2618-157">若要進行測試，您可以依照下列步驟執行：</span><span class="sxs-lookup"><span data-stu-id="c2618-157">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="c2618-158">裝置 1 上：**啟動應用程式** (Rover Explorer 已具現化並放在桌面上)</span><span class="sxs-lookup"><span data-stu-id="c2618-158">On device 1: **Start the app** (the Rover Explorer is instantiated and placed on the table)</span></span>
2. <span data-ttu-id="c2618-159">在裝置 2 上：**啟動應用程式** (兩位使用者都會看到具有 Rover Explorer 的桌面，但桌面不會出現在相同的位置，而且使用者虛擬人偶不會出現在使用者的所在位置)</span><span class="sxs-lookup"><span data-stu-id="c2618-159">On device 2: **Start the app** (both users see the table with the Rover Explorer, but the table does not appear in the same place, and the user avatars do not appear where the users are)</span></span>
3. <span data-ttu-id="c2618-160">裝置 1 上：按下 [啟動 Azure 工作階段] 按鈕</span><span class="sxs-lookup"><span data-stu-id="c2618-160">On device 1: Press the **Start Azure Session** button</span></span>
4. <span data-ttu-id="c2618-161">裝置 1 上：按下 [建立 Azure 錨點] 按鈕 (在 TableAnchor 物件的位置上建立錨點，並將錨點資訊儲存在 Azure 資源中)。</span><span class="sxs-lookup"><span data-stu-id="c2618-161">On device 1: Press the **Create Azure Anchor** button (creates anchor at the location of the TableAnchor object and stores the anchor information in the Azure resource).</span></span>
5. <span data-ttu-id="c2618-162">裝置 1 上：按下 [共用 Azure 錨點] 按鈕 (即時與其他使用者共用錨點識別碼)</span><span class="sxs-lookup"><span data-stu-id="c2618-162">On device 1: Press the **Share Azure Anchor** button (shares the anchor ID with other users in real-time)</span></span>
6. <span data-ttu-id="c2618-163">在裝置 2 上：按下 [啟動 Azure 工作階段] 按鈕</span><span class="sxs-lookup"><span data-stu-id="c2618-163">On device 2: Press the **Start Azure Session** button</span></span>
7. <span data-ttu-id="c2618-164">在裝置 2 上：按下 [取得 Azure Anchor] 按鈕 (連線至 Azure 資源以抓取共用錨點識別碼的錨點資訊，然後將 TableAnchor 物件移至使用裝置 1 建立錨點的位置)</span><span class="sxs-lookup"><span data-stu-id="c2618-164">On device 2: Press the **Get Azure Anchor** button (connects to the Azure resource to retrieve the anchor information for the shared anchor ID, then moves the TableAnchor object to the location where the anchor was created with the device 1)</span></span>

> [!TIP]
> <span data-ttu-id="c2618-165">如果您沒有兩個 HoloLens 裝置的存取權，可以遵循[建置行動裝置的 Azure Spatial Anchors](mr-learning-asa-05.md) 將專案部署到行動裝置。</span><span class="sxs-lookup"><span data-stu-id="c2618-165">If you don't have access to two HoloLens devices, you may follow the [Building Azure Spatial Anchors for mobile devices](mr-learning-asa-05.md) to deploy the project to your mobile device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="c2618-166">恭喜！</span><span class="sxs-lookup"><span data-stu-id="c2618-166">Congratulations</span></span>

<span data-ttu-id="c2618-167">在本教學課程中，您已了解如何整合 Azure 的強大 Spatial Anchors，在共用體驗中對齊裝置。</span><span class="sxs-lookup"><span data-stu-id="c2618-167">In this tutorial, you learned how to integrate Azure's powerful Spatial Anchors to align devices in a shared experience.</span></span>

<span data-ttu-id="c2618-168">此課程也是這一系列教學課程的總結，您已在此系列中了解如何設定 Photon 帳戶、建立 PUN 應用程式、將 PUN 整合到 Unity 應用程式、設定使用者虛擬人偶和共用物件，最後使用 Azure Spatial Anchors 來調整多個參與者。</span><span class="sxs-lookup"><span data-stu-id="c2618-168">This also concludes this tutorial series where you learned how to set up a Photon account, create a PUN app, integrate PUN into the Unity project, configure user avatars and shared objects, and finally align multiple participants using Azure Spatial Anchors.</span></span>
