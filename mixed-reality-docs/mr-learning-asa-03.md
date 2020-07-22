---
title: Azure Spatial Anchor 教學課程 - 3。 儲存、擷取和共用 Azure Spatial Anchors
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure Spatial Anchors。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 25676404a71daf41b6a5c7587fa9bed95ab813f6
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304430"
---
# <a name="3-saving-retrieving-and-sharing-azure-spatial-anchors"></a><span data-ttu-id="c5d3a-105">3.儲存、擷取和共用 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="c5d3a-105">3. Saving, retrieving, and sharing Azure Spatial Anchors</span></span>

<span data-ttu-id="c5d3a-106">在本教學課程中，您將了解如何藉由將錨點識別碼儲存至 HoloLens 2 的儲存體，讓 Azure 空間錨點可儲存在多個應用程式工作階段上。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-106">In this tutorial, you will learn how to save Azure Spatial Anchors across multiple app sessions by saving the anchor ID to the HoloLens 2's storage.</span></span> <span data-ttu-id="c5d3a-107">您也將了解如何將此錨點識別碼與其他裝置共用，以對齊多個裝置的錨點。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-107">You will also learn how to share this anchor ID to other devices for a multi-device anchor alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="c5d3a-108">目標</span><span class="sxs-lookup"><span data-stu-id="c5d3a-108">Objectives</span></span>

* <span data-ttu-id="c5d3a-109">了解如何跨多個應用程式工作階段來達到空間對齊。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-109">Learn how to achieve spatial alignment across multiple app sessions.</span></span>
* <span data-ttu-id="c5d3a-110">了解如何達到多個裝置之間的空間對齊。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-110">Learn how to achieve spatial alignment between multiple devices.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="c5d3a-111">準備場景</span><span class="sxs-lookup"><span data-stu-id="c5d3a-111">Preparing the scene</span></span>

<span data-ttu-id="c5d3a-112">在 [階層] 視窗中，展開 **ButtonParent** 物件。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-112">In the Hierarchy window, expand the **ButtonParent** object.</span></span> <span data-ttu-id="c5d3a-113">選取 **last four child button** 物件。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-113">Select the **last four child button** objects.</span></span> <span data-ttu-id="c5d3a-114">在 [偵測器] 視窗中，**核取**名稱欄位旁的核取方塊，讓所有物件變成作用中。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-114">In the Inspector window, **check** the checkbox next to the name field to make all the objects active.</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-03-section1-step1-1.png)

<span data-ttu-id="c5d3a-116">在 [階層] 視窗中，選取 **ButtonParent** 物件。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-116">In the Hierarchy window, select the **ButtonParent** objects.</span></span> <span data-ttu-id="c5d3a-117">然後在 [偵測器] 視窗中，找出 **GridObjectCollection** 元件，然後按一下 [更新集合] 按鈕，以更新所有 **ButtonParent** 物件的子物件位置。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-117">Then in the Inspector window, locate the **GridObjectCollection** component and click the **Update Collection** button to update the position of all the **ButtonParent** object's child objects.</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-03-section1-step1-2.png)

## <a name="persisting-azure-spatial-anchors-between-app-sessions"></a><span data-ttu-id="c5d3a-119">在應用程式工作階段之間保存 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="c5d3a-119">Persisting Azure Spatial Anchors between app sessions</span></span>

<span data-ttu-id="c5d3a-120">在本節中，您將了解如何以 HoloLens 本機磁碟作為來源或目標，以儲存和擷取 Azure 錨點識別碼。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-120">In this section, you will learn how to save and retrieve the Azure Anchor ID to and from the HoloLens' local disk.</span></span> <span data-ttu-id="c5d3a-121">這可讓您在不同的應用程式工作階段之間查詢 Azure 是否有相同的錨點識別碼。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-121">This will allow you to query Azure for the same anchor ID between different app sessions.</span></span> <span data-ttu-id="c5d3a-122">這可讓錨定的全像投影放置在與先前應用程式工作階段相同的位置。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-122">It will enable the anchored holograms to be positioned at the same location as in the previous app session.</span></span>

<span data-ttu-id="c5d3a-123">在 [階層] 視窗中，展開 **ButtonParent** 物件，並找出名為 **SaveAzureAnchorIdToDisk** 和 **GetAzureAnchorIdFromDisk** 的兩個按鈕：</span><span class="sxs-lookup"><span data-stu-id="c5d3a-123">In the Hierarchy window, expand the **ButtonParent** object and locate the two buttons named **SaveAzureAnchorIdToDisk** and **GetAzureAnchorIdFromDisk**:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-03-section2-step1-1.png)

<span data-ttu-id="c5d3a-125">請遵循上一個教學課程中的[設定按鈕以操作場景](mr-learning-asa-02.md#configuring-the-buttons-to-operate-the-scene)指示來執行相同步驟，在兩個按鈕上設定 **Interactable (指令碼)** 元件：</span><span class="sxs-lookup"><span data-stu-id="c5d3a-125">Follow the same steps as in the [configuring the buttons to operate the scene](mr-learning-asa-02.md#configuring-the-buttons-to-operate-the-scene) instructions from the previous tutorial to configure the **Interactable (Script)** component on each of the two buttons:</span></span>

* <span data-ttu-id="c5d3a-126">針對 **SaveAzureAnchorIdToDisk** 按鈕物件，請指派 AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** 函式。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-126">For the **SaveAzureAnchorIdToDisk** button object, assign the AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** function.</span></span>
* <span data-ttu-id="c5d3a-127">針對 **GetAzureAnchorIdFromDisk** 按鈕物件，請指派 AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** 函式。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-127">For the **GetAzureAnchorIdFromDisk** button object, assign the AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** function.</span></span>

<span data-ttu-id="c5d3a-128">如果您將已更新的應用程式建立到 HoloLens，您現在可以藉由儲存 Azure 錨點識別碼，在應用程式工作階段之間保存 Azure Spatial Anchors。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-128">If you build the updated app to your HoloLens, you can now persist Azure Spatial Anchors between app sessions by saving the Azure Anchor ID.</span></span> <span data-ttu-id="c5d3a-129">若要進行測試，您可以依照下列步驟執行：</span><span class="sxs-lookup"><span data-stu-id="c5d3a-129">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="c5d3a-130">將 Rover Explorer 移至所需的位置</span><span class="sxs-lookup"><span data-stu-id="c5d3a-130">Move the Rover Explorer to the desired location</span></span>
2. <span data-ttu-id="c5d3a-131">啟動 Azure 工作階段</span><span class="sxs-lookup"><span data-stu-id="c5d3a-131">Start Azure Session</span></span>
3. <span data-ttu-id="c5d3a-132">建立 Azure 錨點 (在 Rover Explorer 的位置上建立錨點)。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-132">Create Azure Anchor (creates anchors at the location of the Rover Explorer)</span></span>
4. <span data-ttu-id="c5d3a-133">將 Azure 錨點識別碼儲存至磁碟</span><span class="sxs-lookup"><span data-stu-id="c5d3a-133">Save Azure Anchor ID to Disk</span></span>
5. <span data-ttu-id="c5d3a-134">重新啟動應用程式</span><span class="sxs-lookup"><span data-stu-id="c5d3a-134">Restart the app</span></span>
6. <span data-ttu-id="c5d3a-135">從磁碟取得 Azure 錨點 (載入您剛儲存的錨點識別碼)</span><span class="sxs-lookup"><span data-stu-id="c5d3a-135">Get Azure Anchor from Disk (loads the anchor ID you just saved)</span></span>
7. <span data-ttu-id="c5d3a-136">啟動 Azure 工作階段</span><span class="sxs-lookup"><span data-stu-id="c5d3a-136">Start Azure Session</span></span>
8. <span data-ttu-id="c5d3a-137">尋找 Azure 錨點 (將 Rover Explorer 置於步驟 3 的位置)</span><span class="sxs-lookup"><span data-stu-id="c5d3a-137">Find Azure Anchor (positions the Rover Explorer at the location from step 3)</span></span>

> [!NOTE]
> <span data-ttu-id="c5d3a-138">若要完全重新啟動應用程式，在結束沉浸式應用程式檢視之後，您必須先關閉混合實境首頁中的應用程式視窗，然後再從 [開始] 功能表重新啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-138">To fully restart the app, after exiting the immersive app view, the app window in the mixed reality home needs to be closed before relaunching it from the Start menu.</span></span> <span data-ttu-id="c5d3a-139">如需其他詳細資料，您可以參閱[在 HoloLens 上使用應用程式](https://docs.microsoft.com/hololens/holographic-home#using-apps-on-hololens)一文。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-139">For additional details, you can refer to the [Using apps on HoloLens](https://docs.microsoft.com/hololens/holographic-home#using-apps-on-hololens) documentation.</span></span>

## <a name="sharing-azure-spatial-anchors-between-devices"></a><span data-ttu-id="c5d3a-140">在裝置之間共用 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="c5d3a-140">Sharing Azure Spatial Anchors between devices</span></span>

<span data-ttu-id="c5d3a-141">在本節中，您將了解如何在多個裝置之間共用 Azure 錨點識別碼。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-141">In this section, you will learn how to share the Azure Anchor ID between multiple devices.</span></span> <span data-ttu-id="c5d3a-142">這可讓多個裝置查詢 Azure 是否有相同的錨點識別碼，以便具有錨點的全像投影能夠進行空間對齊。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-142">This will allow multiple devices to query Azure for the same anchor ID, allowing the anchored holograms to be spatially aligned.</span></span> <span data-ttu-id="c5d3a-143">空間對齊 (亦即，在多個裝置之間看到相同實體位置中的相同全像投影) 是 HoloLens 2 本機共用體驗的關鍵。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-143">Spatial alignment, i.e., seeing the same holograms in the same physical location between multiple devices, is key to local shared experiences in the HoloLens 2.</span></span>

<span data-ttu-id="c5d3a-144">在裝置之間傳輸 Azure 錨點識別碼的方式有很多種，包括[多使用者功能教學課程](mr-learning-sharing-02.md)系列中所述的方法。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-144">There are many ways to transfer Azure Anchor IDs between devices, including methods outlined in the [Multi-user capabilities tutorials](mr-learning-sharing-02.md) series.</span></span> <span data-ttu-id="c5d3a-145">在此範例中，您將使用簡單的 Web 服務，在裝置之間上傳和下載錨點識別碼。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-145">In this example, you will use a simple web service to upload and download anchor IDs between devices.</span></span>

<span data-ttu-id="c5d3a-146">在 [階層] 視窗中，展開 **ButtonParent** 物件。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-146">In the Hierarchy window, expand the **ButtonParent** object.</span></span>   <span data-ttu-id="c5d3a-147">找出名為 **ShareAzureAnchorIdToNetwork** 和 **GetAzureAnchorIdFromNetwork** 的兩個按鈕：</span><span class="sxs-lookup"><span data-stu-id="c5d3a-147">Locate the two buttons named **ShareAzureAnchorIdToNetwork** and **GetAzureAnchorIdFromNetwork**:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-03-section3-step1-1.png)

<span data-ttu-id="c5d3a-149">請遵循上一個教學課程中的[設定按鈕以操作場景](mr-learning-asa-02.md#configuring-the-buttons-to-operate-the-scene)指示來執行相同步驟，在兩個按鈕上設定 **Interactable (指令碼)** 元件：</span><span class="sxs-lookup"><span data-stu-id="c5d3a-149">Follow the same steps as in the [configuring the buttons to operate the scene](mr-learning-asa-02.md#configuring-the-buttons-to-operate-the-scene) instructions from the previous tutorial to configure the **Interactable (Script)** component on each of the two buttons:</span></span>

* <span data-ttu-id="c5d3a-150">針對 **ShareAzureAnchorIdToNetwork** 物件，請指派 AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** 函式。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-150">For the **ShareAzureAnchorIdToNetwork** object, assign the AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** function.</span></span>
* <span data-ttu-id="c5d3a-151">針對 **GetAzureAnchorIdFromNetwork** 物件，請指派 AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** 函式。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-151">For the **GetAzureAnchorIdFromNetwork** object, assign the AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** function.</span></span>

<span data-ttu-id="c5d3a-152">如果您將已更新的應用程式建立在兩部 HoloLens 裝置中，您現在可以藉由共用 Azure 錨點識別碼來進行空間對齊。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-152">If you build the updated app to two HoloLens devices, you can now achieve spatial alignment by sharing the Azure Anchor ID.</span></span> <span data-ttu-id="c5d3a-153">若要進行測試，您可以依照下列步驟執行：</span><span class="sxs-lookup"><span data-stu-id="c5d3a-153">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="c5d3a-154">在 HoloLens 裝置 1 上：將 Rover Explorer 移至所需的位置。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-154">On HoloLens device 1: Move the Rover Explorer to the desired location.</span></span>
2. <span data-ttu-id="c5d3a-155">在 HoloLens 裝置 1 上：啟動 Azure 工作階段。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-155">On HoloLens device 1: Start Azure Session.</span></span>
3. <span data-ttu-id="c5d3a-156">在 HoloLens 裝置 1 上：建立 Azure 錨點 (在 Rover Explorer 體驗的位置上建立錨點)。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-156">On HoloLens device 1: Create Azure Anchor (creates anchors at the location of the Rover Explorer).</span></span>
4. <span data-ttu-id="c5d3a-157">在 HoloLens 裝置 1 上：將 Azure 錨點識別碼共用至網路。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-157">On HoloLens device 1: Share Azure Anchor ID to Network.</span></span>
5. <span data-ttu-id="c5d3a-158">在 HoloLens 裝置 2 上：啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-158">On HoloLens device 2: Start the app.</span></span>
6. <span data-ttu-id="c5d3a-159">在 HoloLens 裝置 2 上：從網路取得共用錨點識別碼 (提取剛從 HoloLens 裝置 1 共用的錨點識別碼)。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-159">On HoloLens device 2: Get Shared Anchor ID from Network (fetches the anchor ID just shared from HoloLens device 1).</span></span>
7. <span data-ttu-id="c5d3a-160">在 HoloLens 裝置 2 上：啟動 Azure 工作階段。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-160">On HoloLens device 2: Start Azure Session.</span></span>
8. <span data-ttu-id="c5d3a-161">在 HoloLens 裝置 2 上：尋找 Azure 錨點 (將 Rover Explorer 置於步驟 3 的位置)。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-161">On HoloLens device 2: Find Azure Anchor (positions the Rover Explorer at the location from step 3).</span></span>

> [!TIP]
> <span data-ttu-id="c5d3a-162">如果您只有一個 HoloLens，您仍然可以藉由重新啟動應用程式來測試此功能，而不用使用第二個 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-162">If you only have one HoloLens, you can still test the functionality by restarting the app instead of using a second HoloLens device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="c5d3a-163">恭喜！</span><span class="sxs-lookup"><span data-stu-id="c5d3a-163">Congratulations</span></span>

<span data-ttu-id="c5d3a-164">在本教學課程中，您已了解如何藉由將 Azure Spatial Anchor 識別碼儲存至 HoloLens 上的本機碟，在應用程式工作階段與應用程式重新啟動之間保存 Azure Spatial Anchors。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-164">In this tutorial, you learned how to persist Azure Spatial Anchors between app sessions and app restarts by saving the Azure Spatial Anchor ID to the local disk on HoloLens.</span></span> <span data-ttu-id="c5d3a-165">您也已了解如何在多個裝置之間共用 Azure Spatial Anchors，以進行基本的多使用者靜態全像投影共用體驗。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-165">You also learned how to share Azure Spatial Anchors between multiple devices for a basic multi-user, static hologram shared experience.</span></span>

<span data-ttu-id="c5d3a-166">在下一個教學課程中，您將了解如何為使用者提供即時回饋。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-166">In the next tutorial, you will learn how to provide users with real-time feedback.</span></span> <span data-ttu-id="c5d3a-167">此回饋將包含有關錨點建立、環境理解品質和 Azure 工作階段狀態的資訊。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-167">This feedback will include information about Anchor creation, the quality of environment understanding, and the Azure session's state.</span></span> <span data-ttu-id="c5d3a-168">如果沒有任何回饋，使用者可能不知道錨點是否已成功上傳至 Azure、環境的品質是否足以建立錨點或目前狀態為何。</span><span class="sxs-lookup"><span data-stu-id="c5d3a-168">Without feedback, users may not know whether an anchor has successfully been uploaded to Azure, whether the quality of the environment is sufficient for anchor creation, or the current state.</span></span>

[<span data-ttu-id="c5d3a-169">下一個教學課程：4.顯示 Azure Spatial Anchor 意見反應</span><span class="sxs-lookup"><span data-stu-id="c5d3a-169">Next Tutorial: 4. Displaying Azure Spatial Anchor feedback</span></span>](mr-learning-asa-04.md)
