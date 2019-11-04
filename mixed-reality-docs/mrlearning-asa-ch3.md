---
title: Azure 空間錨點教學課程-3。 顯示 Azure 空間錨點意見反應
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 77d639a88d8b4c71dc5fbe1c78565c4c3f91d36c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438421"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="f1847-105">3. 顯示 Azure 空間錨點的意見反應</span><span class="sxs-lookup"><span data-stu-id="f1847-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="f1847-106">在這一課，您將瞭解如何在使用 Azure 空間錨點時，為使用者提供錨點探索、事件和狀態的意見反應。</span><span class="sxs-lookup"><span data-stu-id="f1847-106">In this lesson, you'll learn how to provide users with feedback about anchor discovery, events and status when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="f1847-107">目標</span><span class="sxs-lookup"><span data-stu-id="f1847-107">Objectives</span></span>

* <span data-ttu-id="f1847-108">瞭解如何設定 UI 面板，以顯示目前 ASA 會話的相關重要資訊</span><span class="sxs-lookup"><span data-stu-id="f1847-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="f1847-109">瞭解並探索 ASA SDK 可供使用者使用的意見反應元素</span><span class="sxs-lookup"><span data-stu-id="f1847-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="instructions"></a><span data-ttu-id="f1847-110">指示</span><span class="sxs-lookup"><span data-stu-id="f1847-110">Instructions</span></span>

### <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="f1847-111">設定 ASA 意見反應 UI 面板</span><span class="sxs-lookup"><span data-stu-id="f1847-111">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="f1847-112">在本課程中，我們不會使用 [SaveAnchorToDisk] 和 [ShareAnchor] 按鈕，因此，請選取這兩個按鈕，並取消核取 [偵測器] 面板中的核取方塊（如下所示）以隱藏這些按鈕。</span><span class="sxs-lookup"><span data-stu-id="f1847-112">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons, so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="f1847-114">建立指示面板。</span><span class="sxs-lookup"><span data-stu-id="f1847-114">Create the instruction panel.</span></span> <span data-ttu-id="f1847-115">首先，以滑鼠右鍵按一下 [指示] 按鈕，將滑鼠停留在 [3D 物件] 上，然後選取 [textmeshpro-text]。</span><span class="sxs-lookup"><span data-stu-id="f1847-115">Start by right-clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. <span data-ttu-id="f1847-117">調整文字的縮放和定位，使其符合場景中的指示。</span><span class="sxs-lookup"><span data-stu-id="f1847-117">Adjust the scale and positioning of the text, so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="f1847-118">此外，請確定所有文字的對齊都會置中。</span><span class="sxs-lookup"><span data-stu-id="f1847-118">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="f1847-119">然後從文字編輯器中刪除範例文字，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="f1847-119">Then delete the sample text from the text editor, as shown in in the image below.</span></span>

![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="f1847-121">將 TextMeshPro 物件的名稱變更為 "FeedbackPanel"。</span><span class="sxs-lookup"><span data-stu-id="f1847-121">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>
   

![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. <span data-ttu-id="f1847-123">在 [專案] 面板中，選取 [資產] 並按一下滑鼠右鍵，然後選取 [在 explorer 中顯示]。</span><span class="sxs-lookup"><span data-stu-id="f1847-123">In the project panel, select "assets" and right click, then select "show in explorer."</span></span>
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

<span data-ttu-id="f1847-125">按一下[這裡](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E)以下載接下來幾個步驟所需的檔案。</span><span class="sxs-lookup"><span data-stu-id="f1847-125">Click [here](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) to download the files needed in the next few steps.</span></span>

6. <span data-ttu-id="f1847-126">一旦開啟 Explorer，請選取 [資產] 資料夾，然後按一下 [ASAmodulesAssets] 資料夾，並將錨點回饋腳本和錨點模組腳本檔案複製到資料夾中。</span><span class="sxs-lookup"><span data-stu-id="f1847-126">Once Explorer opens, select the Assets folder, then the "ASAmodulesAssets" folder and copy the anchor feedback script and the anchor module script files into the folder.</span></span> 

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> <span data-ttu-id="f1847-128">注意：如果您看到快顯視窗，詢問您是否要覆寫舊的或保留舊的訊息，請選取 [覆寫]。</span><span class="sxs-lookup"><span data-stu-id="f1847-128">note: if you get a pop-up message asking if you to overwrite the old or keep the old, select overwrite.</span></span>

7. <span data-ttu-id="f1847-129">返回 [資產] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f1847-129">Return to the Assets folder.</span></span> <span data-ttu-id="f1847-130">然後，移至 "AzureSpatialAnchorsPlugin" 資料夾，後面接著 [範例] 資料夾，最後是 [腳本] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f1847-130">Then, go into the "AzureSpatialAnchorsPlugin" folder, followed by the Examples folder and finally the Scripts folder.</span></span> <span data-ttu-id="f1847-131">然後將 Azure 空間錨點示範包裝函式複製到該資料夾。</span><span class="sxs-lookup"><span data-stu-id="f1847-131">Then copy the Azure Spatial Anchors demo wrapper into that folder.</span></span> 

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. <span data-ttu-id="f1847-133">既然檔案已上傳，請確定已在 ASA_feedback 階層中選取 "feedbackpanel" 文字，按一下 [新增元件]，然後在出現後選取 [錨點意見反應] 腳本，藉以新增它。</span><span class="sxs-lookup"><span data-stu-id="f1847-133">Now that the files are uploaded, ensure that the "feedbackpanel" text is selected in the ASA_feedback hierarchy, click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span> 

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. <span data-ttu-id="f1847-135">將 "feedbackPanel" 文字物件從 ASA_Feedback 階層拖曳至腳本底下的空插槽中，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="f1847-135">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span> 

![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a><span data-ttu-id="f1847-137">恭喜！</span><span class="sxs-lookup"><span data-stu-id="f1847-137">Congratulations</span></span>

<span data-ttu-id="f1847-138">在本課程中，我們已瞭解如何建立 UI 面板，以顯示 Azure 空間錨點體驗的目前狀態，以提供使用者即時意見反應。</span><span class="sxs-lookup"><span data-stu-id="f1847-138">In this lesson, we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>


