---
title: Azure Spatial Anchor 教學課程 - 2。 儲存、擷取和共用 Azure Spatial Anchors
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 36f25229469e848a3f0612a5971cc8e9381262f5
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "80362006"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a><span data-ttu-id="46594-105">2.儲存、擷取和共用 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="46594-105">2. Saving, retrieving, and sharing Azure Spatial Anchors</span></span>

<span data-ttu-id="46594-106">在本教學課程中，您將了解如何藉由將錨點識別碼儲存至 HoloLens 2 的儲存體，讓 Azure 空間錨點可儲存在多個應用程式工作階段上。</span><span class="sxs-lookup"><span data-stu-id="46594-106">In this tutorial, you will learn how to save Azure Spatial Anchors across multiple app sessions by saving the anchor ID to the HoloLens 2's storage.</span></span> <span data-ttu-id="46594-107">您也將了解如何將此錨點識別碼與其他裝置共用，以對齊多個裝置的錨點。</span><span class="sxs-lookup"><span data-stu-id="46594-107">You will also learn how to share this anchor ID to other devices for a multi-device anchor alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="46594-108">目標</span><span class="sxs-lookup"><span data-stu-id="46594-108">Objectives</span></span>

* <span data-ttu-id="46594-109">了解如何以 HoloLens 2 本機磁碟作為來源或目標來儲存和擷取 Azure Spatial Anchor 識別碼，好讓識別碼可持續存在應用程式工作階段之間</span><span class="sxs-lookup"><span data-stu-id="46594-109">Learn how to save and retrieve Azure Spatial Anchor IDs to and from the HoloLens 2 local disk, for persistence between app sessions</span></span>
* <span data-ttu-id="46594-110">了解如何讓多裝置案例中的使用者共用 Azure Spatial Anchor 識別碼</span><span class="sxs-lookup"><span data-stu-id="46594-110">Learn how to share Azure Spatial Anchor IDs between users in a multi-device scenario</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="46594-111">準備場景</span><span class="sxs-lookup"><span data-stu-id="46594-111">Preparing the scene</span></span>

<span data-ttu-id="46594-112">在 [專案] 視窗中，瀏覽至 [資產]   > [MRTK.Tutorials.AzureSpatialAnchors]   > [Prefabs]  資料夾。</span><span class="sxs-lookup"><span data-stu-id="46594-112">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="46594-113">按住 CTRL 鍵並按一下 [ButtonParent_SaveAnchorId]  和 [ButtonParent_ShareAnchorId]  以選取這兩個 Prefab，然後將其拖曳到 [階層] 視窗中來新增至場景中：</span><span class="sxs-lookup"><span data-stu-id="46594-113">While holding down the CTRL button, click on **ButtonParent_SaveAnchorId** and **ButtonParent_ShareAnchorId** to select the two prefabs, then drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial2-section1-step1-1.png)

## <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a><span data-ttu-id="46594-115">在應用程式工作階段之間保存 Azure 錨點 - 將錨點識別碼儲存至磁碟</span><span class="sxs-lookup"><span data-stu-id="46594-115">Persist Azure Anchors between app sessions - Save anchor ID to disk</span></span>
<!-- TODO: Consider renaming to 'Persist Azure Anchors between app sessions' -->

<span data-ttu-id="46594-116">在本節中，您將了解如何以 HoloLens 2 本機磁碟作為來源或目標，以儲存和擷取 Azure 錨點識別碼。</span><span class="sxs-lookup"><span data-stu-id="46594-116">In this section, you will learn how to save and retrieve the Azure Anchor ID to and from the HoloLens 2 local disk.</span></span> <span data-ttu-id="46594-117">這可讓您在不同應用程式工作階段之間查詢 Azure 是否有相同的錨點識別碼，以便將具有錨點的全像投影放置在與先前應用程式工作階段相同的位置。</span><span class="sxs-lookup"><span data-stu-id="46594-117">This will allow you to query Azure for the same anchor ID between different app sessions, allowing the anchored holograms to be position at the same location as in the previous app session.</span></span>

<span data-ttu-id="46594-118">在 [階層] 視窗中，展開包含兩個按鈕的 **ButtonParent_SaveAnchorId**，一個按鈕用於將 Azure 錨點識別碼儲存至 HoloLens 2 儲存體，另一個用來從磁碟擷取已儲存的識別碼：</span><span class="sxs-lookup"><span data-stu-id="46594-118">In the Hierarchy window, expand the **ButtonParent_SaveAnchorId** object which contains two buttons, one button for saving the Azure Anchor ID to the HoloLens 2 storage and another for retrieving the saved ID from the disk:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial2-section2-step1-1.png)

<span data-ttu-id="46594-120">請遵循上一個教學課程中的[設定按鈕以操作場景](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene)指示來執行相同步驟，將 **Pressable Button Holo Lens 2 (指令碼)** 元件和 **Interactable (指令碼)** 元件設定在兩個按鈕上：</span><span class="sxs-lookup"><span data-stu-id="46594-120">Follow the same steps as in the [configuring the buttons to operate the scene](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) instructions from the previous tutorial to configure the **Pressable Button Holo Lens 2 (Script)** component and the **Interactable (Script)** component on each of the two buttons:</span></span>

* <span data-ttu-id="46594-121">針對 **SaveAzureAnchorIdToDisk** 物件，請指派 AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** 函式。</span><span class="sxs-lookup"><span data-stu-id="46594-121">For the **SaveAzureAnchorIdToDisk** object, assign the AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** function.</span></span>
* <span data-ttu-id="46594-122">針對 **GetAzureAnchorIdFromDisk** 物件，請指派 AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** 函式。</span><span class="sxs-lookup"><span data-stu-id="46594-122">For the **GetAzureAnchorIdFromDisk** object, assign the AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** function.</span></span>

<span data-ttu-id="46594-123">如果您將已更新的應用程式建立到 HoloLens，您現在可以藉由儲存 Azure 錨點識別碼，在應用程式工作階段之間保存 Azure Spatial Anchors。</span><span class="sxs-lookup"><span data-stu-id="46594-123">If you build the updated application to your HoloLens, you can now persist Azure Spatial Anchors between app sessions by saving the Azure Anchor ID.</span></span> <span data-ttu-id="46594-124">若要進行測試，您可以依照下列步驟執行：</span><span class="sxs-lookup"><span data-stu-id="46594-124">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="46594-125">將火箭發射器體驗移至想要的位置。</span><span class="sxs-lookup"><span data-stu-id="46594-125">Move the Rocket Launcher experience to desired location.</span></span>
2. <span data-ttu-id="46594-126">啟動 Azure 工作階段。</span><span class="sxs-lookup"><span data-stu-id="46594-126">Start Azure Session.</span></span>
3. <span data-ttu-id="46594-127">建立 Azure 錨點 (在火箭發射器體驗的位置上建立錨點)。</span><span class="sxs-lookup"><span data-stu-id="46594-127">Create Azure Anchor (creates anchors at the location of the Rocket Launcher experience).</span></span>
4. <span data-ttu-id="46594-128">將 Azure 錨點識別碼儲存至磁碟。</span><span class="sxs-lookup"><span data-stu-id="46594-128">Save Azure Anchor ID to Disk.</span></span>
5. <span data-ttu-id="46594-129">重新啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="46594-129">Restart the application.</span></span>
6. <span data-ttu-id="46594-130">從磁碟取得 Azure 錨點 (載入您剛儲存的錨點識別碼)。</span><span class="sxs-lookup"><span data-stu-id="46594-130">Get Azure Anchor from Disk (loads the anchor ID you just saved).</span></span>
7. <span data-ttu-id="46594-131">啟動 Azure 工作階段。</span><span class="sxs-lookup"><span data-stu-id="46594-131">Start Azure Session.</span></span>
8. <span data-ttu-id="46594-132">尋找 Azure 錨點 (將火箭發射器體驗置於步驟 3 的位置)。</span><span class="sxs-lookup"><span data-stu-id="46594-132">Find Azure Anchor (positions the Rocket Launcher experience at the location from step 3).</span></span>

> [!NOTE]
> <span data-ttu-id="46594-133">若要完全重新啟動應用程式，在結束沉浸式應用程式檢視之後，您必須先關閉混合實境首頁中的應用程式視窗，然後再從 [開始] 功能表重新啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="46594-133">To fully restart the application, after exiting the immersive app view, the app window in the mixed reality home needs to be closed before relaunching the application from the Start menu.</span></span> <span data-ttu-id="46594-134">如需其他詳細資料，您可以參閱[在 HoloLens 上使用應用程式](https://docs.microsoft.com/hololens/holographic-home#using-apps-on-hololens)一文。</span><span class="sxs-lookup"><span data-stu-id="46594-134">For additional details, you can refer to the [Using apps on HoloLens](https://docs.microsoft.com/hololens/holographic-home#using-apps-on-hololens) documentation.</span></span>

## <a name="share-azure-anchors-between-multiple-devices"></a><span data-ttu-id="46594-135">在多個裝置之間共用 Azure 錨點</span><span class="sxs-lookup"><span data-stu-id="46594-135">Share Azure Anchors between multiple devices</span></span>

<span data-ttu-id="46594-136">在本節中，您將了解如何在多個裝置之間共用 Azure 錨點識別碼。</span><span class="sxs-lookup"><span data-stu-id="46594-136">In this section, you will learn how to share the Azure Anchor ID between multiple devices.</span></span> <span data-ttu-id="46594-137">這可讓多個裝置查詢 Azure 是否有相同的錨點識別碼，以便具有錨點的全像投影能夠進行空間對齊。</span><span class="sxs-lookup"><span data-stu-id="46594-137">This will allow multiple devices to query Azure for the same anchor ID, allowing the anchored holograms to be spatially aligned.</span></span> <span data-ttu-id="46594-138">空間對齊 (亦即，在多個裝置之間看到相同實體位置中的相同全像投影) 是 HoloLens 2 本機共用體驗的關鍵。</span><span class="sxs-lookup"><span data-stu-id="46594-138">Spatial alignment, i.e. seeing the same holograms in the same physical location between multiple devices, is key to local shared experiences in the HoloLens 2.</span></span>

<span data-ttu-id="46594-139">在裝置之間傳輸 Azure 錨點識別碼的方式有很多種，包括[多使用者功能教學課程](mrlearning-sharing(photon)-ch1.md)系列中所述的方法。</span><span class="sxs-lookup"><span data-stu-id="46594-139">There are many ways to transfer Azure Anchor IDs between devices, including methods outlined in the the [Multi-user capabilities tutorials](mrlearning-sharing(photon)-ch1.md) series.</span></span> <span data-ttu-id="46594-140">在此範例中，您將使用簡單的 Web 服務，在裝置之間上傳和下載錨點識別碼。</span><span class="sxs-lookup"><span data-stu-id="46594-140">In this example, you will use a simple web service to upload and download anchor IDs between devices.</span></span>

<span data-ttu-id="46594-141">在 [階層] 視窗中，展開包含兩個按鈕的 **ButtonParent_ShareAnchorId** 物件；一個按鈕用來將 Azure 錨點識別碼上傳至 Web 伺服器，另一個則用於從 Web 伺服器下載識別碼：</span><span class="sxs-lookup"><span data-stu-id="46594-141">In the Hierarchy window, expand the **ButtonParent_ShareAnchorId** object which contains two buttons; one button for uploading the Azure Anchor ID to the web server, and another for downloading the ID from the web server:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial2-section3-step1-1.png)

<span data-ttu-id="46594-143">請遵循上一個教學課程中的[設定按鈕以操作場景](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene)指示來執行相同步驟，將 **Pressable Button Holo Lens 2 (指令碼)** 元件和 **Interactable (指令碼)** 元件設定在兩個按鈕上：</span><span class="sxs-lookup"><span data-stu-id="46594-143">Follow the same steps as in the [configuring the buttons to operate the scene](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) instructions from the previous tutorial to configure the **Pressable Button Holo Lens 2 (Script)** component and the **Interactable (Script)** component on each of the two buttons:</span></span>

* <span data-ttu-id="46594-144">針對 **ShareAzureAnchorIdToNetwork** 物件，請指派 AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** 函式。</span><span class="sxs-lookup"><span data-stu-id="46594-144">For the **ShareAzureAnchorIdToNetwork** object, assign the AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** function.</span></span>
* <span data-ttu-id="46594-145">針對 **GetAzureAnchorIdFromNetwork** 物件，請指派 AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** 函式。</span><span class="sxs-lookup"><span data-stu-id="46594-145">For the **GetAzureAnchorIdFromNetwork** object, assign the AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** function.</span></span>

<span data-ttu-id="46594-146">如果您將已更新的應用程式建立至兩部 HoloLens 裝置，您現在可以藉由共用 Azure 錨點識別碼，在裝置之間進行空間對齊。</span><span class="sxs-lookup"><span data-stu-id="46594-146">If you build the updated application to two HoloLens devices, you can now achieve spatial alignment between them by sharing the Azure Anchor ID.</span></span> <span data-ttu-id="46594-147">若要進行測試，您可以依照下列步驟執行：</span><span class="sxs-lookup"><span data-stu-id="46594-147">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="46594-148">在 HoloLens 裝置 1 上：將火箭發射器體驗移至想要的位置。</span><span class="sxs-lookup"><span data-stu-id="46594-148">On HoloLens device 1: Move the Rocket Launcher experience to desired location.</span></span>
2. <span data-ttu-id="46594-149">在 HoloLens 裝置 1 上：啟動 Azure 工作階段。</span><span class="sxs-lookup"><span data-stu-id="46594-149">On HoloLens device 1: Start Azure Session.</span></span>
3. <span data-ttu-id="46594-150">在 HoloLens 裝置 1 上：建立 Azure 錨點 (在火箭發射器體驗的位置上建立錨點)。</span><span class="sxs-lookup"><span data-stu-id="46594-150">On HoloLens device 1: Create Azure Anchor (creates anchors at the location of the Rocket Launcher experience).</span></span>
4. <span data-ttu-id="46594-151">在 HoloLens 裝置 1 上：將 Azure 錨點識別碼共用至網路。</span><span class="sxs-lookup"><span data-stu-id="46594-151">On HoloLens device 1: Share Azure Anchor ID to Network.</span></span>
5. <span data-ttu-id="46594-152">在 HoloLens 裝置 2 上：啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="46594-152">On HoloLens device 2: Start the application.</span></span>
6. <span data-ttu-id="46594-153">在 HoloLens 裝置 2 上：從網路取得共用錨點識別碼 (提取剛從 HoloLens 裝置 1 共用的錨點識別碼)。</span><span class="sxs-lookup"><span data-stu-id="46594-153">On HoloLens device 2: Get Shared Anchor ID from Network (fetches the anchor ID just shared from HoloLens device 1).</span></span>
7. <span data-ttu-id="46594-154">在 HoloLens 裝置 2 上：啟動 Azure 工作階段。</span><span class="sxs-lookup"><span data-stu-id="46594-154">On HoloLens device 2: Start Azure Session.</span></span>
8. <span data-ttu-id="46594-155">在 HoloLens 裝置 2 上：尋找 Azure 錨點 (將火箭發射器體驗置於步驟 3 的位置)。</span><span class="sxs-lookup"><span data-stu-id="46594-155">On HoloLens device 2: Find Azure Anchor (positions the Rocket Launcher experience at the location from step 3).</span></span>

> [!TIP]
> <span data-ttu-id="46594-156">如果您只有一個 HoloLens，您仍然可以藉由重新啟動應用程式來測試此功能，而不用使用第二個 HoloLens 裝置。</span><span class="sxs-lookup"><span data-stu-id="46594-156">If you only have one HoloLens, you can still test the functionality by restarting the application instead of using a second HoloLens device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="46594-157">恭喜！</span><span class="sxs-lookup"><span data-stu-id="46594-157">Congratulations</span></span>

<span data-ttu-id="46594-158">在本教學課程中，您已了解如何藉由將 Azure Spatial Anchor 識別碼儲存至 HoloLens 上的本機碟，在應用程式工作階段與應用程式重新啟動之間保存 Azure Spatial Anchors。</span><span class="sxs-lookup"><span data-stu-id="46594-158">In this tutorial you learned how to persist Azure Spatial Anchors between application sessions and application restarts by saving the Azure Spatial Anchor ID to the local disk on HoloLens.</span></span> <span data-ttu-id="46594-159">您也已了解如何在多個裝置之間共用 Azure Spatial Anchors，以進行基本的多使用者靜態全像投影共用體驗。</span><span class="sxs-lookup"><span data-stu-id="46594-159">You also learned how to share Azure Spatial Anchors between multiple devices for a basic multi-user, static hologram shared experience.</span></span>

<span data-ttu-id="46594-160">在下一個教學課程中，您將了解如何為使用者提供即時回饋。</span><span class="sxs-lookup"><span data-stu-id="46594-160">In the next tutorial you will learn how to provide users with real-time feedback.</span></span> <span data-ttu-id="46594-161">此回饋將包含有關錨點建立、環境理解品質和 Azure 工作階段狀態的資訊。</span><span class="sxs-lookup"><span data-stu-id="46594-161">This feedback will include information about Anchor creation, the quality of environment understanding, and the state of the Azure session.</span></span> <span data-ttu-id="46594-162">如果沒有任何回饋，使用者可能不知道錨點是否已成功上傳至 Azure、環境的品質是否足以建立錨點或目前狀態為何。</span><span class="sxs-lookup"><span data-stu-id="46594-162">Without feedback, users may not know whether an anchor has successfully been uploaded to Azure, whether the quality of the environment is sufficient for anchor creation, or the current state.</span></span>

[<span data-ttu-id="46594-163">下一課：3.顯示 Azure Spatial Anchor 意見反應</span><span class="sxs-lookup"><span data-stu-id="46594-163">Next Lesson: 3. Displaying Azure Spatial Anchor feedback</span></span>](mrlearning-asa-ch3.md)
