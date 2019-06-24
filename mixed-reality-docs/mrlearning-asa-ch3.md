---
title: MR 學習 ASA 模組上 HoloLens 2 Azure 空間的錨點
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 4aabb4a35efebdd893cbb248365e534abd60f684
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327341"
---
# <a name="displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="b40e7-104">顯示 Azure 空間的錨點的意見反應</span><span class="sxs-lookup"><span data-stu-id="b40e7-104">Displaying Azure Spatial Anchor Feedback</span></span>

<span data-ttu-id="b40e7-105">在這一課，您將了解如何使用 Azure 空間的錨點時使用者提供意見反應錨點探索、 事件和狀態。</span><span class="sxs-lookup"><span data-stu-id="b40e7-105">In this lesson, you'll learn about how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors.</span></span>

<span data-ttu-id="b40e7-106">目標：</span><span class="sxs-lookup"><span data-stu-id="b40e7-106">Objectives:</span></span>

* <span data-ttu-id="b40e7-107">了解如何設定 UI 面板，其中顯示目前的 ASA 工作階段的相關重要資訊</span><span class="sxs-lookup"><span data-stu-id="b40e7-107">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="b40e7-108">了解和探索 ASA SDK 會提供給使用者的意見反應項目</span><span class="sxs-lookup"><span data-stu-id="b40e7-108">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

  

## <a name="instructions"></a><span data-ttu-id="b40e7-109">指示</span><span class="sxs-lookup"><span data-stu-id="b40e7-109">Instructions</span></span>

### <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="b40e7-110">設定 ASA 意見反應 UI 面板</span><span class="sxs-lookup"><span data-stu-id="b40e7-110">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="b40e7-111">在這一課中，我們不會使用 「 SaveAnchorToDisk"和"ShareAnchor 」 按鈕因此選取這兩個按鈕，並取消核取 [偵測器] 面板中的核取方塊 （如下所示） 以隱藏這些按鈕。</span><span class="sxs-lookup"><span data-stu-id="b40e7-111">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="b40e7-113">接下來，建立指示面板。</span><span class="sxs-lookup"><span data-stu-id="b40e7-113">Next, create the instruction panel.</span></span> <span data-ttu-id="b40e7-114">以滑鼠右鍵按一下"instructions"按鈕啟動，請停留在 「 3D 物件 」 並選取 「 textmeshpro-文字 」。</span><span class="sxs-lookup"><span data-stu-id="b40e7-114">Start by right clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

   

   ![module2chapter3step2im](images/module2chapter3step2im.PNG)

   3. <span data-ttu-id="b40e7-116">調整規模和位置的文字，使其符合場景中的指示。</span><span class="sxs-lookup"><span data-stu-id="b40e7-116">Adjust the scale and the positioning of the text so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="b40e7-117">此外，請確定會置中的所有文字的對齊方式。</span><span class="sxs-lookup"><span data-stu-id="b40e7-117">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="b40e7-118">然後，在下圖中所示，請從文字編輯器中，刪除的範例文字。</span><span class="sxs-lookup"><span data-stu-id="b40e7-118">Then delete the sample text from the text editor, as shown in in the image below.</span></span>


![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="b40e7-120">將 TextMeshPro 物件的名稱變更為 「 FeedbackPanel。 」</span><span class="sxs-lookup"><span data-stu-id="b40e7-120">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>
   
   ![module2chapter3step4im](images/module2chapter3step4im.PNG)
   
5. <span data-ttu-id="b40e7-122">在 [專案] 面板中，選取 「 資產 」，並按一下滑鼠右鍵，然後選取 [顯示總管] 中。</span><span class="sxs-lookup"><span data-stu-id="b40e7-122">In the project panel, select "assets" and right click, then select "show in explorer."</span></span>
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

<span data-ttu-id="b40e7-124">現在，按一下 [此處](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E)下載檔案所需在接下來的幾個步驟。</span><span class="sxs-lookup"><span data-stu-id="b40e7-124">Now, click [here](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) to download the files needed in the next few steps.</span></span>

6. <span data-ttu-id="b40e7-125">檔案總管開啟後，請選取 [assets] 資料夾中，則 「 ASAmodulesAssets"資料夾中，與錨點回饋指令碼和錨點模組指令碼檔案複製到資料夾。</span><span class="sxs-lookup"><span data-stu-id="b40e7-125">Once explorer opens, select the assets folder, then the "ASAmodulesAssets" folder, and copy the anchor feedback script and the anchor module script files into the folder.</span></span> 
   

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> <span data-ttu-id="b40e7-127">注意： 如果您會收到快顯視窗，詢問您是否想要覆寫舊，或保留舊請確定您選取 覆寫。</span><span class="sxs-lookup"><span data-stu-id="b40e7-127">note: if you get a pop-up asking you if you would like to overwrite the old or keep the old make sure you select overwrite.</span></span>

7. <span data-ttu-id="b40e7-128">現在回到 [Assets] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="b40e7-128">Now return to the Assets folder.</span></span> <span data-ttu-id="b40e7-129">然後，進入 「 AzureSpatialAnchorsPlugin"資料夾中，範例 資料夾，然後最後指令碼 資料夾中，並將 Azure 空間的錨點示範包裝函式複製到該資料夾。</span><span class="sxs-lookup"><span data-stu-id="b40e7-129">Then, go into the "AzureSpatialAnchorsPlugin" folder, then the examples folder, and finally the scripts folder, and copy the Azure Spatial Anchors demo wrapper into that folder.</span></span> 
   

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. <span data-ttu-id="b40e7-131">現在，將檔案上傳時，確認 「 feedbackpanel"文字已選取，ASA_feedback 階層中按一下 [新增元件] 並新增錨點回饋指令碼，藉由搜尋它，並選取它，它出現時。</span><span class="sxs-lookup"><span data-stu-id="b40e7-131">Now that the files are uploaded, ensure that the "feedbackpanel" text is selected, in the ASA_feedback hierarchy and click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span> 
   
   

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. <span data-ttu-id="b40e7-133">拖曳至 「 feedbackPanel"文字物件從 ASA_Feedback 階層指令碼下方的空插槽如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="b40e7-133">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span> 
   

![module2chapter3step9im](images/module2chapter3step9im.PNG)

   

## <a name="congratulations"></a><span data-ttu-id="b40e7-135">恭喜！</span><span class="sxs-lookup"><span data-stu-id="b40e7-135">Congratulations</span></span>

<span data-ttu-id="b40e7-136">在這一課，我們學到如何建立顯示 Azure 空間的錨點體驗的使用者提供即時回饋的目前狀態的 UI 面板的內容。</span><span class="sxs-lookup"><span data-stu-id="b40e7-136">In this lesson we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing user with real-time feedback.</span></span>


