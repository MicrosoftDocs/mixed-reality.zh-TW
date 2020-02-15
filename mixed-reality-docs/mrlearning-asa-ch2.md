---
title: Azure 空間錨點教學課程-2。 儲存、抓取和共用 Azure 空間錨點
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 7b19233a9634e2568200476c9483464bbf9dd3c8
ms.sourcegitcommit: a580166a19294f835b8e09c780f663f228dd5de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77250729"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a><span data-ttu-id="727d6-105">2. 儲存、抓取和共用 Azure 空間錨點</span><span class="sxs-lookup"><span data-stu-id="727d6-105">2. Saving, retrieving, and sharing Azure Spatial Anchors</span></span>

<span data-ttu-id="727d6-106">在本教學課程中，您將瞭解如何藉由將錨點識別碼儲存至 HoloLens 2 的儲存體，來將 Azure 空間錨點儲存在多個應用程式會話。</span><span class="sxs-lookup"><span data-stu-id="727d6-106">In this tutorial, you will learn how to save Azure Spatial Anchors across multiple app sessions by saving the anchor ID to the HoloLens 2's storage.</span></span> <span data-ttu-id="727d6-107">您也將瞭解如何將此錨點識別碼與其他裝置共用，以進行多重裝置錨點對齊。</span><span class="sxs-lookup"><span data-stu-id="727d6-107">You will also learn how to share this anchor ID to other devices for a multi-device anchor alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="727d6-108">目標</span><span class="sxs-lookup"><span data-stu-id="727d6-108">Objectives</span></span>

* <span data-ttu-id="727d6-109">瞭解如何在應用程式會話之間持續儲存和取出 HoloLens 2 本機磁片的 Azure 空間錨點識別碼</span><span class="sxs-lookup"><span data-stu-id="727d6-109">Learn how to save and retrieve Azure Spatial Anchor IDs to and from the HoloLens 2 local disk, for persistence between app sessions</span></span>
* <span data-ttu-id="727d6-110">瞭解如何在多裝置案例中，共用使用者之間的 Azure 空間錨點識別碼</span><span class="sxs-lookup"><span data-stu-id="727d6-110">Learn how to share Azure Spatial Anchor IDs between users in a multi-device scenario</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="727d6-111">準備場景</span><span class="sxs-lookup"><span data-stu-id="727d6-111">Preparing the scene</span></span>

<span data-ttu-id="727d6-112">在 [專案] 視窗中，流覽至 [**資產**] [ > **MRTK]。教學課程. AzureSpatialAnchors** > **Prefabs**資料夾。</span><span class="sxs-lookup"><span data-stu-id="727d6-112">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="727d6-113">按住 CTRL 鍵時，按一下  **ButtonParent_SaveAnchorId**並**ButtonParent_ShareAnchorId**以選取兩個 prefabs，然後將它們拖曳到 階層 視窗，將它們加入場景中：</span><span class="sxs-lookup"><span data-stu-id="727d6-113">While holding down the CTRL button, click on **ButtonParent_SaveAnchorId** and **ButtonParent_ShareAnchorId** to select the two prefabs, then drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial2-section1-step1-1.png)

## <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a><span data-ttu-id="727d6-115">在應用程式會話之間保存 Azure 錨點-將錨點識別碼儲存至磁片</span><span class="sxs-lookup"><span data-stu-id="727d6-115">Persist Azure Anchors between app sessions - Save anchor ID to disk</span></span>
<!-- TODO: Consider renaming to 'Persist Azure Anchors between app sessions' -->

<span data-ttu-id="727d6-116">在本節中，您將瞭解如何在 HoloLens 2 本機磁片中儲存和取出 Azure 錨點識別碼。</span><span class="sxs-lookup"><span data-stu-id="727d6-116">In this section, you will learn how to save and retrieve the Azure Anchor ID to and from the HoloLens 2 local disk.</span></span> <span data-ttu-id="727d6-117">這可讓您在不同的應用程式會話之間查詢 Azure 是否有相同的錨點識別碼，以便將錨定的全息影像放置在與先前應用程式會話相同的位置。</span><span class="sxs-lookup"><span data-stu-id="727d6-117">This will allow you to query Azure for the same anchor ID between different app sessions, allowing the anchored holograms to be position at the same location as in the previous app session.</span></span>

<span data-ttu-id="727d6-118">在 [階層] 視窗中，展開包含兩個按鈕的 [ **ButtonParent_SaveAnchorId** ] 物件，一個按鈕用於將 Azure 錨點識別碼儲存至 HoloLens 2 儲存體，另一個用於從磁片抓取已儲存的識別碼：</span><span class="sxs-lookup"><span data-stu-id="727d6-118">In the Hierarchy window, expand the **ButtonParent_SaveAnchorId** object which contains two buttons, one button for saving the Azure Anchor ID to the HoloLens 2 storage and another for retrieving the saved ID from the disk:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial2-section2-step1-1.png)

<span data-ttu-id="727d6-120">遵循從上一個教學課程設定[按鈕以操作場景](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene)指示中的相同步驟，在兩個按鈕上設定**Pressable 按鈕 hololens 透鏡2（腳本）** 元件和**可互動（腳本）** 元件：</span><span class="sxs-lookup"><span data-stu-id="727d6-120">Follow the same steps as in the [configuring the buttons to operate the scene](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) instructions from the previous tutorial to configure the **Pressable Button Holo Lens 2 (Script)** component and the **Interactable (Script)** component on each of the two buttons:</span></span>

* <span data-ttu-id="727d6-121">針對**SaveAzureAnchorIdToDisk**物件，指派 AnchorModuleScript > **SaveAzureAnchorIdToDisk （）** 函數。</span><span class="sxs-lookup"><span data-stu-id="727d6-121">For the **SaveAzureAnchorIdToDisk** object, assign the AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** function.</span></span>
* <span data-ttu-id="727d6-122">針對**GetAzureAnchorIdFromDisk**物件，指派 AnchorModuleScript > **GetAzureAnchorIdFromDisk （）** 函數。</span><span class="sxs-lookup"><span data-stu-id="727d6-122">For the **GetAzureAnchorIdFromDisk** object, assign the AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** function.</span></span>

<span data-ttu-id="727d6-123">如果您將已更新的應用程式建立到 HoloLens，您現在可以藉由儲存 Azure 錨點識別碼，在應用程式會話之間保存 Azure 空間錨點。</span><span class="sxs-lookup"><span data-stu-id="727d6-123">If you build the updated application to your HoloLens, you can now persist Azure Spatial Anchors between app sessions by saving the Azure Anchor ID.</span></span> <span data-ttu-id="727d6-124">若要測試它，您可以依照下列步驟執行：</span><span class="sxs-lookup"><span data-stu-id="727d6-124">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="727d6-125">將 Rocket 啟動器體驗移至所需的位置。</span><span class="sxs-lookup"><span data-stu-id="727d6-125">Move the Rocket Launcher experience to desired location.</span></span>
2. <span data-ttu-id="727d6-126">啟動 Azure 會話。</span><span class="sxs-lookup"><span data-stu-id="727d6-126">Start Azure Session.</span></span>
3. <span data-ttu-id="727d6-127">建立 Azure 錨點（在 Rocket 啟動器體驗的位置建立錨點）。</span><span class="sxs-lookup"><span data-stu-id="727d6-127">Create Azure Anchor (creates anchors at the location of the Rocket Launcher experience).</span></span>
4. <span data-ttu-id="727d6-128">將 Azure 錨點識別碼儲存至磁片。</span><span class="sxs-lookup"><span data-stu-id="727d6-128">Save Azure Anchor ID to Disk.</span></span>
5. <span data-ttu-id="727d6-129">重新開機應用程式。</span><span class="sxs-lookup"><span data-stu-id="727d6-129">Restart the application.</span></span>
6. <span data-ttu-id="727d6-130">從磁片取得 Azure 錨點（載入您剛儲存的錨點識別碼）。</span><span class="sxs-lookup"><span data-stu-id="727d6-130">Get Azure Anchor from Disk (loads the anchor ID you just saved).</span></span>
7. <span data-ttu-id="727d6-131">啟動 Azure 會話。</span><span class="sxs-lookup"><span data-stu-id="727d6-131">Start Azure Session.</span></span>
8. <span data-ttu-id="727d6-132">尋找 Azure 錨點（將 Rocket 啟動器體驗置於步驟3的位置）。</span><span class="sxs-lookup"><span data-stu-id="727d6-132">Find Azure Anchor (positions the Rocket Launcher experience at the location from step 3).</span></span>

## <a name="share-azure-anchors-between-multiple-devices"></a><span data-ttu-id="727d6-133">在多個裝置之間共用 Azure 錨點</span><span class="sxs-lookup"><span data-stu-id="727d6-133">Share Azure Anchors between multiple devices</span></span>

<span data-ttu-id="727d6-134">在本節中，您將瞭解如何在多個裝置之間共用 Azure 錨點識別碼。</span><span class="sxs-lookup"><span data-stu-id="727d6-134">In this section, you will learn how to share the Azure Anchor ID between multiple devices.</span></span> <span data-ttu-id="727d6-135">這可讓多個裝置查詢 Azure 是否有相同的錨點識別碼，讓錨定的全息圖形能夠進行空間對齊。</span><span class="sxs-lookup"><span data-stu-id="727d6-135">This will allow multiple devices to query Azure for the same anchor ID, allowing the anchored holograms to be spatially aligned.</span></span> <span data-ttu-id="727d6-136">空間對齊（亦即，在多個裝置之間的相同實體位置中看到相同的全息影像）是 HoloLens 2 中本機共用體驗的關鍵。</span><span class="sxs-lookup"><span data-stu-id="727d6-136">Spatial alignment, i.e. seeing the same holograms in the same physical location between multiple devices, is key to local shared experiences in the HoloLens 2.</span></span>

<span data-ttu-id="727d6-137">有許多方式可以在裝置之間傳輸 Azure 錨點識別碼，包括[多使用者功能教學](mrlearning-sharing(photon)-ch1.md)課程系列中所述的方法。</span><span class="sxs-lookup"><span data-stu-id="727d6-137">There are many ways to transfer Azure Anchor IDs between devices, including methods outlined in the the [Multi-user capabilities tutorials](mrlearning-sharing(photon)-ch1.md) series.</span></span> <span data-ttu-id="727d6-138">在此範例中，您將使用簡單的 web 服務，在裝置之間上傳和下載錨點識別碼。</span><span class="sxs-lookup"><span data-stu-id="727d6-138">In this example, you will use a simple web service to upload and download anchor IDs between devices.</span></span>

<span data-ttu-id="727d6-139">在 [階層] 視窗中，展開包含兩個按鈕的**ButtonParent_ShareAnchorId**物件;一個按鈕，用來將 Azure 錨點識別碼上傳至 web 伺服器，另一個則用於從 web 伺服器下載識別碼：</span><span class="sxs-lookup"><span data-stu-id="727d6-139">In the Hierarchy window, expand the **ButtonParent_ShareAnchorId** object which contains two buttons; one button for uploading the Azure Anchor ID to the web server, and another for downloading the ID from the web server:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial2-section3-step1-1.png)

<span data-ttu-id="727d6-141">遵循從上一個教學課程設定[按鈕以操作場景](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene)指示中的相同步驟，在兩個按鈕上設定**Pressable 按鈕 hololens 透鏡2（腳本）** 元件和**可互動（腳本）** 元件：</span><span class="sxs-lookup"><span data-stu-id="727d6-141">Follow the same steps as in the [configuring the buttons to operate the scene](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) instructions from the previous tutorial to configure the **Pressable Button Holo Lens 2 (Script)** component and the **Interactable (Script)** component on each of the two buttons:</span></span>

* <span data-ttu-id="727d6-142">針對**ShareAzureAnchorIdToNetwork**物件，指派 AnchorModuleScript > **ShareAzureAnchorIdToNetwork （）** 函數。</span><span class="sxs-lookup"><span data-stu-id="727d6-142">For the **ShareAzureAnchorIdToNetwork** object, assign the AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** function.</span></span>
* <span data-ttu-id="727d6-143">針對**GetAzureAnchorIdFromNetwork**物件，指派 AnchorModuleScript > **GetAzureAnchorIdFromNetwork （）** 函數。</span><span class="sxs-lookup"><span data-stu-id="727d6-143">For the **GetAzureAnchorIdFromNetwork** object, assign the AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** function.</span></span>

<span data-ttu-id="727d6-144">如果您將已更新的應用程式建立至兩部 HoloLens 裝置，您現在可以藉由共用 Azure 錨點識別碼，達到其之間的空間對齊方式。</span><span class="sxs-lookup"><span data-stu-id="727d6-144">If you build the updated application to two HoloLens devices, you can now achieve spatial alignment between them by sharing the Azure Anchor ID.</span></span> <span data-ttu-id="727d6-145">若要測試它，您可以依照下列步驟執行：</span><span class="sxs-lookup"><span data-stu-id="727d6-145">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="727d6-146">在 HoloLens 裝置1上：將 Rocket 啟動器體驗移到想要的位置。</span><span class="sxs-lookup"><span data-stu-id="727d6-146">On HoloLens device 1: Move the Rocket Launcher experience to desired location.</span></span>
2. <span data-ttu-id="727d6-147">在 HoloLens 裝置1上：啟動 Azure 會話。</span><span class="sxs-lookup"><span data-stu-id="727d6-147">On HoloLens device 1: Start Azure Session.</span></span>
3. <span data-ttu-id="727d6-148">在 HoloLens 裝置1上：建立 Azure 錨點（在 Rocket 啟動器體驗的位置建立錨點）。</span><span class="sxs-lookup"><span data-stu-id="727d6-148">On HoloLens device 1: Create Azure Anchor (creates anchors at the location of the Rocket Launcher experience).</span></span>
4. <span data-ttu-id="727d6-149">在 HoloLens 裝置1上：共用 Azure 錨點識別碼到網路。</span><span class="sxs-lookup"><span data-stu-id="727d6-149">On HoloLens device 1: Share Azure Anchor ID to Network.</span></span>
5. <span data-ttu-id="727d6-150">在 HoloLens 裝置2上：重新開機應用程式。</span><span class="sxs-lookup"><span data-stu-id="727d6-150">On HoloLens device 2: Restart the application.</span></span>
6. <span data-ttu-id="727d6-151">在 HoloLens 裝置2上：從網路取得共用錨點識別碼（提取剛從 HoloLens 裝置共用的錨點識別碼）。</span><span class="sxs-lookup"><span data-stu-id="727d6-151">On HoloLens device 2: Get Shared Anchor ID from Network (fetches the anchor ID just shared from HoloLens device 1).</span></span>
7. <span data-ttu-id="727d6-152">在 HoloLens 裝置2上：啟動 Azure 會話。</span><span class="sxs-lookup"><span data-stu-id="727d6-152">On HoloLens device 2: Start Azure Session.</span></span>
8. <span data-ttu-id="727d6-153">在 HoloLens 裝置2上：尋找 Azure 錨點（將 Rocket 啟動器體驗置於步驟3的位置）。</span><span class="sxs-lookup"><span data-stu-id="727d6-153">On HoloLens device 2: Find Azure Anchor (positions the Rocket Launcher experience at the location from step 3).</span></span>

> [!TIP]
> <span data-ttu-id="727d6-154">如果您只有一個 HoloLens，您仍然可以藉由重新開機應用程式，而不是使用第二個 HoloLens 裝置來測試功能。</span><span class="sxs-lookup"><span data-stu-id="727d6-154">If you only have one HoloLens, you can still test the functionality by restarting the application instead of using a second HoloLens device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="727d6-155">恭喜！</span><span class="sxs-lookup"><span data-stu-id="727d6-155">Congratulations</span></span>

<span data-ttu-id="727d6-156">在本教學課程中，您已瞭解如何藉由將 Azure 空間錨點識別碼儲存至 HoloLens 上的本機磁片，在應用程式會話與應用程式重新開機之間保存 Azure 空間錨點。</span><span class="sxs-lookup"><span data-stu-id="727d6-156">In this tutorial you learned how to persist Azure Spatial Anchors between application sessions and application restarts by saving the Azure Spatial Anchor ID to the local disk on HoloLens.</span></span> <span data-ttu-id="727d6-157">您也已瞭解如何在多個裝置之間共用 Azure 空間錨點，以進行基本的多使用者、靜態全息影像共用體驗。</span><span class="sxs-lookup"><span data-stu-id="727d6-157">You also learned how to share Azure Spatial Anchors between multiple devices for a basic multi-user, static hologram shared experience.</span></span>

<span data-ttu-id="727d6-158">在下一個教學課程中，您將學習如何提供使用者即時意見反應。</span><span class="sxs-lookup"><span data-stu-id="727d6-158">In the next tutorial you will learn how to provide users with real-time feedback.</span></span> <span data-ttu-id="727d6-159">此意見反應將包含有關錨點建立、環境理解品質和 Azure 會話狀態的資訊。</span><span class="sxs-lookup"><span data-stu-id="727d6-159">This feedback will include information about Anchor creation, the quality of environment understanding, and the state of the Azure session.</span></span> <span data-ttu-id="727d6-160">如果沒有任何意見反應，使用者可能不知道錨點是否已成功上傳至 Azure、環境的品質是否足以進行錨點建立，或目前的狀態。</span><span class="sxs-lookup"><span data-stu-id="727d6-160">Without feedback, users may not know whether an anchor has successfully been uploaded to Azure, whether the quality of the environment is sufficient for anchor creation, or the current state.</span></span>

[<span data-ttu-id="727d6-161">下一課： 3. 顯示 Azure 空間錨點意見反應</span><span class="sxs-lookup"><span data-stu-id="727d6-161">Next Lesson: 3. Displaying Azure Spatial Anchor feedback</span></span>](mrlearning-asa-ch3.md)
