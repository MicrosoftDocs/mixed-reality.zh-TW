---
title: Azure 空間錨點教學課程-2。 儲存、抓取和共用 Azure 空間錨點
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: a24d15f0c0fff045c01f6070027b7defa87c2416
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2019
ms.locfileid: "73914466"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a><span data-ttu-id="f89aa-105">2. 儲存、抓取和共用 Azure 空間錨點</span><span class="sxs-lookup"><span data-stu-id="f89aa-105">2. Saving, retrieving, and sharing Azure Spatial Anchors</span></span>

<span data-ttu-id="f89aa-106">在本教學課程中，我們將瞭解如何藉由將錨點資訊儲存至 HoloLens 2 的儲存體，將我們的 Azure 空間錨點儲存在多個應用程式會話。</span><span class="sxs-lookup"><span data-stu-id="f89aa-106">In this tutorial, we will learn how to save our Azure Spatial Anchors across multiple app sessions by saving our anchor information to the HoloLens 2's storage.</span></span> <span data-ttu-id="f89aa-107">我們也將瞭解如何將此錨點資訊與其他裝置共用，以進行多重裝置錨定的對齊。</span><span class="sxs-lookup"><span data-stu-id="f89aa-107">We will also learn how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="f89aa-108">目標</span><span class="sxs-lookup"><span data-stu-id="f89aa-108">Objectives</span></span>

* <span data-ttu-id="f89aa-109">瞭解如何從 HoloLens 2 本機磁片儲存和取出 Azure 空間錨點資訊，以在應用程式會話之間持續保留</span><span class="sxs-lookup"><span data-stu-id="f89aa-109">Learn how to save and retrieve Azure Spatial Anchor information from the HoloLens 2 local disk, for persistence between app sessions</span></span>

* <span data-ttu-id="f89aa-110">瞭解如何在多裝置案例中，于使用者之間共用 Azure 空間錨點資訊</span><span class="sxs-lookup"><span data-stu-id="f89aa-110">Learn how to share Azure Spatial Anchor information between users in a multi-device scenario</span></span>

## <a name="instructions"></a><span data-ttu-id="f89aa-111">指示</span><span class="sxs-lookup"><span data-stu-id="f89aa-111">Instructions</span></span>

### <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a><span data-ttu-id="f89aa-112">在應用程式會話之間保存 Azure 錨點-將錨點識別碼儲存至磁片</span><span class="sxs-lookup"><span data-stu-id="f89aa-112">Persist Azure anchors between app sessions - Save anchor ID to Disk</span></span>

1. <span data-ttu-id="f89aa-113">搜尋 SaveAnchorToDisk prefab 並將其新增至您的場景。</span><span class="sxs-lookup"><span data-stu-id="f89aa-113">Search for and add the SaveAnchorToDisk prefab to your scene.</span></span> <span data-ttu-id="f89aa-114">其中包含兩個按鈕，一個按鈕用來將任何可用的 Azure 錨點識別碼儲存至 HoloLens 2 儲存體，另一個則用於從磁片中抓取任何識別碼。</span><span class="sxs-lookup"><span data-stu-id="f89aa-114">These include two buttons, one button for saving any available Azure Anchor IDs to the HoloLens 2 storage, and another for retrieving any IDs from the disk.</span></span>

![module2chapter2step1im](images/module2chapter2step1im.PNG)

2. <span data-ttu-id="f89aa-116">根據下列指示設定每個按鈕</span><span class="sxs-lookup"><span data-stu-id="f89aa-116">Configure Each button according to the instructions below</span></span>

   - <span data-ttu-id="f89aa-117">針對名為 SaveToDisk 的按鈕，在 [已按下的事件觸發程式] 和 [On Click] 事件觸發程式底下，建立新的事件。</span><span class="sxs-lookup"><span data-stu-id="f89aa-117">For the Button named SaveToDisk, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="f89aa-118">將 ParentAnchor 物件拖曳至空白欄位，然後從 ParentAnchor 物件的 ASAmoduleScript 元件指派 SaveAzureAnchorIDToDisk （）方法。</span><span class="sxs-lookup"><span data-stu-id="f89aa-118">Drag the ParentAnchor object into the empty field, and assign the SaveAzureAnchorIDToDisk() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>
   
     > <span data-ttu-id="f89aa-119">注意：有些按鈕可能會與場景中的其他按鈕重迭。</span><span class="sxs-lookup"><span data-stu-id="f89aa-119">Note: some of the buttons may appear overlapping the other buttons in the scene.</span></span> <span data-ttu-id="f89aa-120">請隨意調整按鈕的定位。</span><span class="sxs-lookup"><span data-stu-id="f89aa-120">Feel free to adjust the button's positioning.</span></span>

![module2chapter2step2aim](images/module2chapter2step2aim.PNG)

![module2chapter2step2aim](images/module2chapter2step2bim.PNG)

![module2chapter2step2aim](images/module2chapter2step2cim.PNG)


   - <span data-ttu-id="f89aa-124">針對名為 GetFromDisk 的按鈕，在 [已按下的事件觸發程式] 和 [On Click] 事件觸發程式底下，建立新的事件。</span><span class="sxs-lookup"><span data-stu-id="f89aa-124">For the Button named GetFromDisk, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="f89aa-125">將 ParentAnchor 物件拖曳至空白欄位，然後從 ParentAnchor 物件的 ASAmoduleScript 元件指派 LoadAzureAnchorIDsFromDisk （）方法。</span><span class="sxs-lookup"><span data-stu-id="f89aa-125">Drag the ParentAnchor object into the empty field, and assign the LoadAzureAnchorIDsFromDisk() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

3. <span data-ttu-id="f89aa-126">依照教學課程1中的指示，將更新的應用程式建立至您的裝置。</span><span class="sxs-lookup"><span data-stu-id="f89aa-126">Follow the instructions from Tutorial 1 to build the updated application to your device.</span></span> <span data-ttu-id="f89aa-127">依照您在上一課所做的操作，按下 [建立 Azure 錨點] 按鈕之後，您現在可以按 [儲存至磁片] 按鈕，將 Azure 錨點識別碼儲存至磁片。</span><span class="sxs-lookup"><span data-stu-id="f89aa-127">After pressing the Create Azure Anchor button, as you did in the previous lesson, you may now save the Azure Anchor ID to disk by pressing the save to disk button.</span></span>

4. <span data-ttu-id="f89aa-128">重新開機應用程式，啟動 Azure 會話，按 [載入錨點識別碼]，然後按 [尋找 Azure 錨點]，找出與我們儲存到磁片的識別碼相關聯的錨點。</span><span class="sxs-lookup"><span data-stu-id="f89aa-128">Restart the application, start the Azure Session, Press Load Anchor ID, and then press Locate Azure Anchor to locate the anchor associated with the ID we saved to the disk.</span></span> <span data-ttu-id="f89aa-129">整個場景現在應該會在您先前儲存錨點的位置貼齊位置！</span><span class="sxs-lookup"><span data-stu-id="f89aa-129">The entire scene should now snap into position, at the location you saved the anchor previously!</span></span>

### <a name="share-azure-anchors-between-multiple-devices"></a><span data-ttu-id="f89aa-130">在多個裝置之間共用 Azure 錨點</span><span class="sxs-lookup"><span data-stu-id="f89aa-130">Share Azure Anchors between multiple devices</span></span>

<span data-ttu-id="f89aa-131">在本節中，我們將瞭解如何在多個裝置之間共用 Azure 錨點識別碼。</span><span class="sxs-lookup"><span data-stu-id="f89aa-131">In this section, we'll learn how to share the Azure Anchor ID between multiple devices.</span></span> <span data-ttu-id="f89aa-132">這可讓多個裝置查詢 Azure 是否有相同的錨點識別碼，讓我們的錨定的全息影像和場景能夠以空間對齊。</span><span class="sxs-lookup"><span data-stu-id="f89aa-132">This will allow multiple devices to query Azure for the same anchor ID, allowing our anchored holograms and scenes to be spatially aligned.</span></span> <span data-ttu-id="f89aa-133">空間對齊（在多個裝置之間的相同實體位置中看到相同的全息影像）是 HoloLens 2 中本機共用體驗的關鍵。</span><span class="sxs-lookup"><span data-stu-id="f89aa-133">Spatial alignment (seeing the same holograms in the same physical location between multiple devices) is key to local shared experiences in the HoloLens 2.</span></span> <span data-ttu-id="f89aa-134">有許多方式可以傳輸裝置之間有關 azure 識別碼的資訊，包括 Azure 空間錨點共用體驗教學課程[教學](mrlearning-sharing(photon)-ch1.md)課程中所述的方法。</span><span class="sxs-lookup"><span data-stu-id="f89aa-134">There are many ways to transfer information regarding azure IDs between devices, including methods outlined in the Azure Spatial Anchors shared experiences tutorials [Tutorials](mrlearning-sharing(photon)-ch1.md).</span></span> <span data-ttu-id="f89aa-135">這個範例會使用簡單的 web 服務，在裝置之間上傳和下載錨點識別碼。</span><span class="sxs-lookup"><span data-stu-id="f89aa-135">This example uses a simple web service to upload and download Anchor IDs between devices.</span></span>

1. <span data-ttu-id="f89aa-136">將 ShareAnchor prefab 新增至您的階層。</span><span class="sxs-lookup"><span data-stu-id="f89aa-136">Add the ShareAnchor prefab into your hierarchy.</span></span> <span data-ttu-id="f89aa-137">此 prefab 會將兩個新按鈕新增至您的場景，一個用於上傳錨點識別碼資訊，另一個用於下載錨點識別碼資訊。</span><span class="sxs-lookup"><span data-stu-id="f89aa-137">This prefab adds two new buttons to your scene, one for uploading anchor ID information and another for downloading anchor ID information.</span></span> 

![module2chapter2step5im](images/module2chapter2step5im.PNG)

2. <span data-ttu-id="f89aa-139">根據下列指示設定每個按鈕</span><span class="sxs-lookup"><span data-stu-id="f89aa-139">Configure Each button according to the instructions below</span></span>

   - <span data-ttu-id="f89aa-140">針對名為 SendSharedAnchor 的按鈕，在 [已按下的事件觸發程式] 和 [On Click] 事件觸發程式底下建立新事件。</span><span class="sxs-lookup"><span data-stu-id="f89aa-140">For the Button named, SendSharedAnchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="f89aa-141">將 ParentAnchor 物件拖曳至空白欄位，然後從 ParentAnchor 物件的 ASAmoduleScript 元件指派 ShareAnchor （）方法。</span><span class="sxs-lookup"><span data-stu-id="f89aa-141">Drag the ParentAnchor object into the empty field, and assign the ShareAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

![module2chapter2step6aim](images/module2chapter2step6aim.PNG)

![module2chapter2step6bim](images/module2chapter2step6bim.PNG)

   - <span data-ttu-id="f89aa-144">針對名為 GetSharedAnchor 的按鈕，在 [已按下的事件觸發程式] 和 [On Click] 事件觸發程式底下建立新事件。</span><span class="sxs-lookup"><span data-stu-id="f89aa-144">For the Button named, GetSharedAnchor, create a new event under the Button Pressed event trigger as well as the On Click event trigger.</span></span> <span data-ttu-id="f89aa-145">將 ParentAnchor 物件拖曳至空白欄位，然後從 ParentAnchor 物件的 ASAmoduleScript 元件指派 GetSharedAzureAnchor （）方法。</span><span class="sxs-lookup"><span data-stu-id="f89aa-145">Drag the ParentAnchor object into the empty field, and assign the GetSharedAzureAnchor() method from the ParentAnchor object's ASAmoduleScript component.</span></span>

3. <span data-ttu-id="f89aa-146">依照[教學課程 1](mrlearning-base-ch1.md)中的指示進行。</span><span class="sxs-lookup"><span data-stu-id="f89aa-146">Follow the instructions from [Tutorial 1](mrlearning-base-ch1.md).</span></span> <span data-ttu-id="f89aa-147">將更新的應用程式建立至您的裝置。</span><span class="sxs-lookup"><span data-stu-id="f89aa-147">to build the updated application to your device.</span></span> <span data-ttu-id="f89aa-148">依照您在上一課所做的操作，按下 [建立 Azure 錨點] 按鈕之後，您現在可以按 [與其他裝置共用] 按鈕，將 Azure 錨點識別碼與其他裝置共用。</span><span class="sxs-lookup"><span data-stu-id="f89aa-148">After pressing the Create Azure Anchor button, as you did in the previous lesson, you may now share the Azure Anchor ID to other devices by pressing the Share To Other Device button.</span></span>

   > <span data-ttu-id="f89aa-149">注意：選取父錨點，並向下卷到父錨點腳本。</span><span class="sxs-lookup"><span data-stu-id="f89aa-149">Note: Select the parent anchor and scroll down to the parent anchor script.</span></span> <span data-ttu-id="f89aa-150">請確定您的公用共用 pin 是唯一的（您可以將 pin 碼變更為其他號碼），以便在共用時，知道您是共用的。</span><span class="sxs-lookup"><span data-stu-id="f89aa-150">Ensure that your public sharing pin is unique (You can change the pin to some other number), so that when you share it, you know it is yours that you are sharing.</span></span> <span data-ttu-id="f89aa-151">可能有數千名使用者共用其 Azure 錨點，因此這麼做可讓您確保您共用的是正確的 Azure 錨點。</span><span class="sxs-lookup"><span data-stu-id="f89aa-151">There could be thousands of users sharing their Azure anchors, so doing this will allow you to ensure you are sharing the correct Azure anchors.</span></span>
   > 

![module2chapter2step7bim](images/module2chapter2step7bim.PNG)

4. <span data-ttu-id="f89aa-153">如果您有另一部 HoloLens 2 裝置，請啟動應用程式，然後啟動 Azure 會話。</span><span class="sxs-lookup"><span data-stu-id="f89aa-153">If you have another HoloLens 2 device, start the application and then start the Azure Session.</span></span> <span data-ttu-id="f89aa-154">按 [取得共用錨點識別碼] 按鈕，然後按下 [尋找 Azure 錨點] 按鈕，以找出與我們使用 web 服務共用之識別碼相關聯的錨點。</span><span class="sxs-lookup"><span data-stu-id="f89aa-154">Press the Get Shared Anchor ID button, and then press the Locate Azure Anchor button to locate the anchor associated with the ID we shared using the web service.</span></span> <span data-ttu-id="f89aa-155">整個場景現在應該貼齊位置，也就是放置在另一個 HoloLens 2 裝置上的地方！</span><span class="sxs-lookup"><span data-stu-id="f89aa-155">The entire scene should now snap into position, at where it was placed on the other HoloLens 2 device!</span></span> <span data-ttu-id="f89aa-156">如果您只有一個 HoloLens 2，您仍然可以藉由重新開機應用程式、啟動 Azure 會話，然後按 [取得共用的錨點識別碼] 按鈕來測試功能，然後按 [尋找 Azure 錨點] 按鈕，找出與識別碼相關聯的錨點儲存至磁片。</span><span class="sxs-lookup"><span data-stu-id="f89aa-156">If you only have one HoloLens 2, you may still test functionality by restarting the application, starting the Azure Session, and then press the "Get Shared Anchor ID" button, and then press the "Locate Azure Anchor button" to locate the anchor associated with the ID we saved to the disk.</span></span> <span data-ttu-id="f89aa-157">整個場景現在應該會在您先前儲存錨點的位置貼齊位置！</span><span class="sxs-lookup"><span data-stu-id="f89aa-157">The entire scene should now snap into position, at the location you saved the anchor previously!</span></span>

## <a name="congratulations"></a><span data-ttu-id="f89aa-158">恭喜！</span><span class="sxs-lookup"><span data-stu-id="f89aa-158">Congratulations</span></span>
<span data-ttu-id="f89aa-159">在這一課，您已瞭解如何藉由將 Azure 空間錨點識別碼儲存到 HoloLens 2 上的本機磁片，在應用程式會話和應用程式重新開機之間保存 Azure 空間錨點。</span><span class="sxs-lookup"><span data-stu-id="f89aa-159">In this Lesson you learned how to persist Azure Spatial Anchors between application sessions and application restarts by saving the Azure Spatial Anchor ID to the local disk on HoloLens 2.</span></span> <span data-ttu-id="f89aa-160">您也已瞭解如何在多個裝置之間共用 Azure 空間錨點，以進行基本的多使用者、靜態全息影像共用體驗。</span><span class="sxs-lookup"><span data-stu-id="f89aa-160">You also learned how to share Azure Spatial Anchors between multiple devices for a basic multi-user, static hologram shared experience.</span></span>

<span data-ttu-id="f89aa-161">我們會瞭解如何在共用模組的最後一課，將 Azure 空間錨點實作為完全互動的本機共用體驗的一部分。</span><span class="sxs-lookup"><span data-stu-id="f89aa-161">We learn how to implement Azure Spatial Anchors as part of a fully interactive local shared experience during the final lesson of the Sharing Module.</span></span> <span data-ttu-id="f89aa-162">本機共用體驗可能包括同步處理的3D 物件位置、旋轉和縮放、每個使用者的識別碼，以及共用的應用程式狀態等功能。</span><span class="sxs-lookup"><span data-stu-id="f89aa-162">A local sharing experience may include functionality such as synchronized 3D object position, rotation, and scale, identifiers for each user, and shared application states.</span></span> <span data-ttu-id="f89aa-163">Azure 空間錨點藉由提供每個參與者一個通用錨點，讓所有使用者都能看到相同實體位置中的虛擬物件，藉此增強這些共用案例。</span><span class="sxs-lookup"><span data-stu-id="f89aa-163">Azure Spatial Anchors enhances these shared scenarios by providing each participant with a common anchor that lets all users see virtual objects in the same physical location.</span></span> <span data-ttu-id="f89aa-164">這適用于各種裝置平臺，包括 HoloLens、Android 和 iOS 裝置。</span><span class="sxs-lookup"><span data-stu-id="f89aa-164">This is true across a range of device platforms, including HoloLens, Android, and iOS devices.</span></span> <span data-ttu-id="f89aa-165">若要瞭解如何開發共用體驗，請完成共用模組中的所有課程。</span><span class="sxs-lookup"><span data-stu-id="f89aa-165">To learn how to develop a shared experience, complete all lessons in the Sharing module.</span></span>

<span data-ttu-id="f89aa-166">在下一課中，我們將學習如何提供使用者即時意見反應。</span><span class="sxs-lookup"><span data-stu-id="f89aa-166">In the next Lesson, we will learn how to provide users with real-time feedback.</span></span> <span data-ttu-id="f89aa-167">此意見反應將包含有關錨點建立、環境理解品質和 Azure 會話狀態的資訊。</span><span class="sxs-lookup"><span data-stu-id="f89aa-167">This feedback will include information about Anchor creation, the quality of environment understanding, and the state of the Azure session.</span></span> <span data-ttu-id="f89aa-168">如果沒有任何意見反應，使用者可能不知道錨點是否已成功上傳至 Azure、環境的品質是否足以進行錨點建立，或目前的狀態。</span><span class="sxs-lookup"><span data-stu-id="f89aa-168">Without feedback, users may not know whether an anchor has successfully been upload to Azure, whether the quality of the environment is sufficient for anchor creation, or the current state.</span></span>

[<span data-ttu-id="f89aa-169">下一課： 3. 顯示 Azure 空間錨點意見反應</span><span class="sxs-lookup"><span data-stu-id="f89aa-169">Next Lesson: 3. Displaying Azure Spatial Anchor feedback</span></span>](mrlearning-asa-ch3.md)

