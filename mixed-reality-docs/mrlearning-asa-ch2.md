---
title: MR 學習 ASA 模組上 HoloLens 2 Azure 空間的錨點
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 4dc36aec4d885fa75ea490446c2d682264049725
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326743"
---
# <a name="persistence-and-sharing-of-azure-spatial-anchors"></a><span data-ttu-id="c1dcf-104">持續性和共用 Azure 空間的錨點</span><span class="sxs-lookup"><span data-stu-id="c1dcf-104">Persistence and Sharing of Azure Spatial Anchors</span></span>

<span data-ttu-id="c1dcf-105">在這一課中，我們將了解如何將我們的錨點資訊儲存到 HoloLens 2 的磁碟，在多個應用程式工作階段之間保存我們 Azure 空間的錨點。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-105">In this lesson, we will learn how to persist our Azure Spatial Anchors across multiple app sessions by saving our anchor information to the HoloLens 2's disk.</span></span> <span data-ttu-id="c1dcf-106">我們也將了解如何共用此錨點的資訊到 multi-device 錨點的對齊方式的其他裝置。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-106">We will also learn how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="c1dcf-107">目標</span><span class="sxs-lookup"><span data-stu-id="c1dcf-107">Objectives</span></span>

* <span data-ttu-id="c1dcf-108">了解如何儲存和擷取 Azure 空間的錨點資訊從 HoloLens 2 本機磁碟，但應用程式工作階段之間的持續性</span><span class="sxs-lookup"><span data-stu-id="c1dcf-108">Learn how to save and retrieve Azure Spatial Anchor information from the HoloLens 2 local disk, for persistence between app sessions</span></span>

* <span data-ttu-id="c1dcf-109">了解如何在 Azure 空間的錨點之間共用資訊在多重裝置的案例中的使用者</span><span class="sxs-lookup"><span data-stu-id="c1dcf-109">Learn how to share Azure Spatial Anchor information between users in a multi-device scenario</span></span>

  

## <a name="instructions"></a><span data-ttu-id="c1dcf-110">指示</span><span class="sxs-lookup"><span data-stu-id="c1dcf-110">Instructions</span></span>

### <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a><span data-ttu-id="c1dcf-111">保存 Azure 應用程式工作階段-儲存到磁碟的錨點識別碼之間的錨點</span><span class="sxs-lookup"><span data-stu-id="c1dcf-111">Persist Azure Anchors Between App Sessions - Save Anchor ID to Disk</span></span>

1. <span data-ttu-id="c1dcf-112">搜尋並新增 「 SaveAnchorToDisk"prefab 至場景。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-112">Search for and add the "SaveAnchorToDisk" prefab to your scene.</span></span> <span data-ttu-id="c1dcf-113">這些包括兩個按鈕、 一個按鈕，將任何可用的 Azure 錨點識別碼儲存至 HoloLens 2 磁碟，另一個用於從磁碟擷取任何識別碼。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-113">These include two buttons, one button for saving any available Azure Anchor IDs to the HoloLens 2 disk, and another for retrieving any IDs from the disk.</span></span>

   ![module2chapter2step1im](images/module2chapter2step1im.PNG)

2. <span data-ttu-id="c1dcf-115">設定每個按鈕，依照下列指示</span><span class="sxs-lookup"><span data-stu-id="c1dcf-115">Configure Each button according to the instructions below</span></span>
   - <span data-ttu-id="c1dcf-116">名為"SaveToDisk 」 按鈕，建立新的事件，在 「 按下按鈕 」 事件觸發程序，以及 「 按一下 」 事件觸發程序。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-116">For the Button named "SaveToDisk", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="c1dcf-117">ParentAnchor 物件拖曳至空白的欄位，並將指派 SaveAzureAnchorIDToDisk() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-117">Drag the ParentAnchor object into the empty field, and assign the SaveAzureAnchorIDToDisk() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>
   
     > <span data-ttu-id="c1dcf-118">注意： 部分按鈕可能會出現重疊的場景中的其他按鈕。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-118">Note: some of the buttons may appear overlapping the other buttons in the scene.</span></span> <span data-ttu-id="c1dcf-119">您可以自由調整按鈕的定位項目。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-119">Feel free to adjust the button's positioning.</span></span>
   

  ![module2chapter2step2aim](images/module2chapter2step2aim.PNG)

![module2chapter2step2aim](images/module2chapter2step2bim.PNG)

![module2chapter2step2aim](images/module2chapter2step2cim.PNG)

   - <span data-ttu-id="c1dcf-123">名為"GetFromDisk 」 按鈕，建立新的事件，在 「 按下按鈕 」 事件觸發程序，以及 「 按一下 」 事件觸發程序。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-123">For the Button named "GetFromDisk", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="c1dcf-124">ParentAnchor 物件拖曳至空白的欄位，並將指派 LoadAzureAnchorIDsFromDisk() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-124">Drag the ParentAnchor object into the empty field, and assign the LoadAzureAnchorIDsFromDisk() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

3. <span data-ttu-id="c1dcf-125">若要建置到您的裝置更新的應用程式第 1 課中遵循的指示。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-125">Follow the instructions from Lesson 1 to build the updated application to your device.</span></span> <span data-ttu-id="c1dcf-126">之後按下 「 建立 Azure 錨點 」 按鈕，如同在先前的課程中，您可能現在儲存 Azure 錨點識別碼磁碟藉由按下儲存至磁碟 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-126">After pressing the "Create Azure Anchor" button, as you did in the previous lesson, you may now save the Azure Anchor ID to disk by pressing the save to disk button.</span></span>

4. <span data-ttu-id="c1dcf-127">重新啟動應用程式、 啟動 Azure 工作階段、 按 「 負載錨點識別碼 」 按鈕，然後按 」 找出 Azure 錨點 」 按鈕，以找出我們儲存至磁碟的識別碼相關聯的錨點。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-127">Restart the application, start the Azure Session, Press the "Load Anchor ID" button, and then press the "Locate Azure Anchor" button to locate the anchor associated with the ID we saved to the disk.</span></span> <span data-ttu-id="c1dcf-128">在整個場景現在應該貼齊位置，位置在您的錨點先前儲存 ！</span><span class="sxs-lookup"><span data-stu-id="c1dcf-128">The entire scene should now snap into position, at the location you saved the anchor previously!</span></span>

### <a name="share-azure-anchors-between-multiple-devices"></a><span data-ttu-id="c1dcf-129">多個裝置之間共用 Azure 錨點</span><span class="sxs-lookup"><span data-stu-id="c1dcf-129">Share Azure Anchors between multiple devices</span></span>

<span data-ttu-id="c1dcf-130">在本節中，我們將了解如何共用在多個裝置之間的 Azure 錨點識別碼。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-130">In this section, we'll learn how to share the Azure Anchor ID between multiple devices.</span></span> <span data-ttu-id="c1dcf-131">這可讓多個裝置，若要查詢 Azure 相同的錨點識別碼，讓我們的錨定全像投影和場景在空間上對齊。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-131">This will allow multiple devices to query Azure for the same anchor ID, allowing our anchored holograms and scenes to be spatially aligned.</span></span> <span data-ttu-id="c1dcf-132">空間 （出現在多個裝置之間的相同實體位置相同全像投影） 的對齊方式為 HoloLens 2 中的金鑰至本機共用的體驗。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-132">Spatial alignment (seeing the same holograms in the same physical location between multiple devices) is key to local shared experiences in the HoloLens 2.</span></span> <span data-ttu-id="c1dcf-133">有許多方法來傳輸資訊之間的裝置，包括方法的相關 azure 識別碼中所述 Azure 空間的錨點共用體驗教學課程 (TODO： 加入連結。)此範例會使用簡單的 web 服務上傳和下載裝置之間的錨點識別碼。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-133">There are many ways to transfer information regarding azure IDs between devices, including methods outlined in the Azure Spatial Anchors shared experiences tutorials (TODO: add link.) This example uses a simple web service to upload and download Anchor IDs between devices.</span></span>

1. <span data-ttu-id="c1dcf-134">新增到您的階層 」 ShareAnchor"prefab。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-134">Add the "ShareAnchor" prefab into your hierarchy.</span></span> <span data-ttu-id="c1dcf-135">此 prefab 將兩個新按鈕加入至場景;另一個用於上傳錨點識別碼資訊和下載的另一個錨點識別碼資訊。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-135">This prefab adds two new buttons to your scene; one for uploading anchor ID information and another for downloading anchor ID information.</span></span> 

   ![module2chapter2step5im](images/module2chapter2step5im.PNG)

2. <span data-ttu-id="c1dcf-137">設定每個按鈕，依照下列指示</span><span class="sxs-lookup"><span data-stu-id="c1dcf-137">Configure Each button according to the instructions below</span></span>

   - <span data-ttu-id="c1dcf-138">名為"SendSharedAnchor 」 按鈕，建立新的事件，在 「 按下按鈕 」 事件觸發程序，以及 「 按一下 」 事件觸發程序。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-138">For the Button named "SendSharedAnchor", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="c1dcf-139">ParentAnchor 物件拖曳至空白的欄位，並將指派 ShareAnchor() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-139">Drag the ParentAnchor object into the empty field, and assign the ShareAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

     ![module2chapter2step6aim](images/module2chapter2step6aim.PNG)

     ![module2chapter2step6bim](images/module2chapter2step6bim.PNG)

     

   - <span data-ttu-id="c1dcf-142">名為"GetSharedAnchor 」 按鈕，建立新的事件，在 「 按下按鈕 」 事件觸發程序，以及 「 按一下 」 事件觸發程序。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-142">For the Button named "GetSharedAnchor", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="c1dcf-143">ParentAnchor 物件拖曳至空白的欄位，並將指派 GetSharedAzureAnchor() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-143">Drag the ParentAnchor object into the empty field, and assign the GetSharedAzureAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

3. <span data-ttu-id="c1dcf-144">請依照下列指示[第 1 課](mrlearning-base-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-144">Follow the instructions from [Lesson 1](mrlearning-base-ch1.md).</span></span> <span data-ttu-id="c1dcf-145">若要建置到您的裝置更新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-145">to build the updated application to your device.</span></span> <span data-ttu-id="c1dcf-146">之後按下 「 建立 Azure 錨點 」 按鈕，如同在先前的課程中，您可能現在共用 Azure 錨點識別碼，與其他裝置按共用到其他的裝置。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-146">After pressing the "Create Azure Anchor" button, as you did in the previous lesson, you may now share the Azure Anchor ID to other devices by pressing the Share To Other Device button.</span></span>

   > <span data-ttu-id="c1dcf-147">注意:選取父錨點和向下父錨點指令碼捲動。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-147">Note: Select the parent anchor and scroll down to the parent anchor script.</span></span> <span data-ttu-id="c1dcf-148">確定您 「 公用共用釘選 是唯一的如此當您共用它，您就會知道它是您所共用。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-148">Ensure that your "public sharing pin" is unique, so that when you share it, you know it is yours that you are sharing.</span></span> <span data-ttu-id="c1dcf-149">可能有數千個使用者共用他們的 Azure 錨點，以讓執行此動作可讓您確保您的共用正確的 Azure 錨點。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-149">There could be thousands of users sharing their Azure Anchors, so doing this will allow you to ensure you are sharing the correct Azure Anchors.</span></span>

4. <span data-ttu-id="c1dcf-150">如果您有另一個 HoloLens 2 裝置時，啟動應用程式，然後再啟動 Azure 工作階段。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-150">If you have another HoloLens 2 device, start the application and then start the Azure Session.</span></span> <span data-ttu-id="c1dcf-151">按 取得共用錨點識別碼 按鈕，然後按 」 找出 Azure 錨點 」 按鈕，以找出我們儲存至磁碟的識別碼相關聯的錨點。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-151">Press the "Get Shared Anchor ID" button, and then press the "Locate Azure Anchor" button to locate the anchor associated with the ID we saved to the disk.</span></span> <span data-ttu-id="c1dcf-152">在整個場景現在應該放置到指定位置，在何處放置在其他的 HoloLens 2 裝置 ！</span><span class="sxs-lookup"><span data-stu-id="c1dcf-152">The entire scene should now snap into position, at the where it was placed on the other HoloLens 2 device!</span></span> <span data-ttu-id="c1dcf-153">如果您只有一個 HoloLens 2，您可能仍可測試功能藉由重新啟動應用程式時，啟動 Azure 工作階段中，然後按 取得共用錨點識別碼 按鈕按鈕，再按 」 找出 Azure 錨點 」 按鈕，以找出相關聯的錨點我們儲存至磁碟的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-153">If you only have one HoloLens 2, you may still test functionality by restarting the application, starting the Azure Session, and then Press the "Get Shared Anchor ID" button button, and then press the "Locate Azure Anchor" button to locate the anchor associated with the ID we saved to the disk.</span></span> <span data-ttu-id="c1dcf-154">在整個場景現在應該貼齊位置，位置在您的錨點先前儲存 ！</span><span class="sxs-lookup"><span data-stu-id="c1dcf-154">The entire scene should now snap into position, at the location you saved the anchor previously!</span></span>

## <a name="congratulations"></a><span data-ttu-id="c1dcf-155">恭喜！</span><span class="sxs-lookup"><span data-stu-id="c1dcf-155">Congratulations</span></span>
<span data-ttu-id="c1dcf-156">在這一課，您了解如何將 Azure 空間的錨點識別碼儲存至本機磁碟的 HoloLens 2 應用程式重新啟動應用程式工作階段之間保存 Azure 空間的錨點的內容。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-156">In this Lesson you learned how to persist Azure Spatial Anchors between app sessions and app restarts by saving the Azure Spatial Anchor ID to the local disk of the HoloLens 2.</span></span> <span data-ttu-id="c1dcf-157">您也學到如何針對基本的多使用者、 靜態全像共用經驗的多個裝置之間共用 Azure 空間的錨點 ！</span><span class="sxs-lookup"><span data-stu-id="c1dcf-157">You also learned how to share Azure Spatial Anchors between multiple devices for a basic multi-user, static hologram shared experience!</span></span>

<span data-ttu-id="c1dcf-158">我們將了解如何實作 Azure 空間的錨點期間最後一課中的共用的模組完全互動式的本機共用體驗的一部分。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-158">We will learn how to implement Azure Spatial Anchors as part of a fully interactive local shared experience during the final lesson of the Sharing Module.</span></span> <span data-ttu-id="c1dcf-159">本機的共用經驗可能包括功能，例如每位使用者已同步處理的 3D 物件的位置、 旋轉和縮放比例 識別項，以及共用應用程式狀態。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-159">A local sharing experience may include functionality such as synchronized 3D object position, rotation, and scale, identifiers for each user, and shared application states.</span></span> <span data-ttu-id="c1dcf-160">Azure 空間的錨點可提供常見的錨點，可讓所有使用者會看到相同的實體位置中的虛擬物件中的每個參與者，進而強化這些共用的案例。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-160">Azure Spatial Anchors enhances these shared scenarios by providing each participant with a common anchor which allows all users to see virtual objects in the same physical location.</span></span> <span data-ttu-id="c1dcf-161">這是一組裝置平台，包括 HoloLens、 Android 和 iOS 裝置，則為 true。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-161">This is true across a range of device platforms, including HoloLens, Android, and iOS devices.</span></span> <span data-ttu-id="c1dcf-162">若要了解如何開發分享的經驗，請完成共用模組中的所有課程。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-162">To learn how to develop a shared experience, please complete all lessons in the Sharing module.</span></span>

<span data-ttu-id="c1dcf-163">在下一課中，我們將學習如何為使用者提供即時回饋。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-163">In the next Lesson, we will learn how to provide users with real-time feedback.</span></span> <span data-ttu-id="c1dcf-164">此意見反應將錨點建立、 環境了解，品質和 Azure 的工作階段的狀態相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-164">This feedback will include information about Anchor creation, the quality of environment understanding, and the state of the Azure session.</span></span> <span data-ttu-id="c1dcf-165">沒有意見反應，使用者可能不知道是否為錨點已成功上的傳至 Azure，是否環境的品質就足以應付錨點建立或目前的狀態。</span><span class="sxs-lookup"><span data-stu-id="c1dcf-165">Without feedback, users may not know whether an anchor has successfully been upload to Azure, whether the quality of the environment is sufficient for anchor creation, or the current state.</span></span>

[<span data-ttu-id="c1dcf-166">下一課：ASA 第 3 課</span><span class="sxs-lookup"><span data-stu-id="c1dcf-166">Next Lesson: ASA Lesson 3</span></span>](mrlearning-asa-ch3.md)

