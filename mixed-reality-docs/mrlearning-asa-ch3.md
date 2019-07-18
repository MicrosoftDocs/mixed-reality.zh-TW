---
title: MR Learning ASA 模組 Azure 空間錨點 on HoloLens 2
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: c6e902710eebe205b9e944b1bf95a9ddd3bd9044
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293811"
---
# <a name="displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="b0d31-104">顯示 Azure 空間錨點意見反應</span><span class="sxs-lookup"><span data-stu-id="b0d31-104">Displaying Azure Spatial Anchor Feedback</span></span>

<span data-ttu-id="b0d31-105">在這一課, 您將瞭解如何在使用 Azure 空間錨點時, 為使用者提供錨點探索、事件和狀態的意見反應。</span><span class="sxs-lookup"><span data-stu-id="b0d31-105">In this lesson, you'll learn about how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors.</span></span>

<span data-ttu-id="b0d31-106">目標</span><span class="sxs-lookup"><span data-stu-id="b0d31-106">Objectives:</span></span>

* <span data-ttu-id="b0d31-107">瞭解如何設定 UI 面板, 以顯示目前 ASA 會話的相關重要資訊</span><span class="sxs-lookup"><span data-stu-id="b0d31-107">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="b0d31-108">瞭解並探索 ASA SDK 可供使用者使用的意見反應元素</span><span class="sxs-lookup"><span data-stu-id="b0d31-108">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="instructions"></a><span data-ttu-id="b0d31-109">指示</span><span class="sxs-lookup"><span data-stu-id="b0d31-109">Instructions</span></span>

### <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="b0d31-110">設定 ASA 意見反應 UI 面板</span><span class="sxs-lookup"><span data-stu-id="b0d31-110">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="b0d31-111">在本課程中, 我們不會使用 [SaveAnchorToDisk] 和 [ShareAnchor] 按鈕, 因此請選取這兩個按鈕, 並取消核取 [偵測器] 面板中的核取方塊 (如下所示) 以隱藏這些按鈕。</span><span class="sxs-lookup"><span data-stu-id="b0d31-111">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="b0d31-113">接下來, 建立指示面板。</span><span class="sxs-lookup"><span data-stu-id="b0d31-113">Next, create the instruction panel.</span></span> <span data-ttu-id="b0d31-114">一開始先以滑鼠右鍵按一下 [指示] 按鈕, 將滑鼠停留在 [3D 物件] 上, 然後選取 [textmeshpro-text]。</span><span class="sxs-lookup"><span data-stu-id="b0d31-114">Start by right clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. <span data-ttu-id="b0d31-116">調整文字的尺規和位置, 使其符合場景中的指示。</span><span class="sxs-lookup"><span data-stu-id="b0d31-116">Adjust the scale and the positioning of the text so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="b0d31-117">此外, 請確定所有文字的對齊都會置中。</span><span class="sxs-lookup"><span data-stu-id="b0d31-117">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="b0d31-118">然後從文字編輯器中刪除範例文字, 如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="b0d31-118">Then delete the sample text from the text editor, as shown in in the image below.</span></span>

![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="b0d31-120">將 TextMeshPro 物件的名稱變更為 "FeedbackPanel"。</span><span class="sxs-lookup"><span data-stu-id="b0d31-120">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>
   

![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. <span data-ttu-id="b0d31-122">在 [專案] 面板中, 選取 [資產] 並按一下滑鼠右鍵, 然後選取 [在 explorer 中顯示]。</span><span class="sxs-lookup"><span data-stu-id="b0d31-122">In the project panel, select "assets" and right click, then select "show in explorer."</span></span>
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

<span data-ttu-id="b0d31-124">現在, 按一下[這裡](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E)以下載接下來幾個步驟所需的檔案。</span><span class="sxs-lookup"><span data-stu-id="b0d31-124">Now, click [here](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) to download the files needed in the next few steps.</span></span>

6. <span data-ttu-id="b0d31-125">一旦開啟 explorer, 請選取 [資產] 資料夾, 然後按一下 [ASAmodulesAssets] 資料夾, 再將錨點意見反應腳本和錨點模組腳本檔案複製到資料夾中。</span><span class="sxs-lookup"><span data-stu-id="b0d31-125">Once explorer opens, select the assets folder, then the "ASAmodulesAssets" folder, and copy the anchor feedback script and the anchor module script files into the folder.</span></span> 

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> <span data-ttu-id="b0d31-127">注意: 如果您看到快顯視窗, 詢問您是否要覆寫舊的或保留舊的, 請務必選取 [覆寫]。</span><span class="sxs-lookup"><span data-stu-id="b0d31-127">note: if you get a pop-up asking you if you would like to overwrite the old or keep the old make sure you select overwrite.</span></span>

7. <span data-ttu-id="b0d31-128">現在返回 [資產] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="b0d31-128">Now return to the Assets folder.</span></span> <span data-ttu-id="b0d31-129">然後, 移至 "AzureSpatialAnchorsPlugin" 資料夾、[範例] 資料夾, 最後是 [腳本] 資料夾, 然後將 Azure 空間錨點示範包裝函式複製到該資料夾。</span><span class="sxs-lookup"><span data-stu-id="b0d31-129">Then, go into the "AzureSpatialAnchorsPlugin" folder, then the examples folder, and finally the scripts folder, and copy the Azure Spatial Anchors demo wrapper into that folder.</span></span> 

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. <span data-ttu-id="b0d31-131">既然檔案已上傳, 請確定已選取 [feedbackpanel] 文字, 並在 ASA_feedback 階層中按一下 [新增元件], 然後在出現後加以選取, 以新增錨點意見反應腳本。</span><span class="sxs-lookup"><span data-stu-id="b0d31-131">Now that the files are uploaded, ensure that the "feedbackpanel" text is selected, in the ASA_feedback hierarchy and click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span> 

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. <span data-ttu-id="b0d31-133">將 "feedbackPanel" 文字物件從 ASA_Feedback 階層拖曳至腳本底下的空插槽, 如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="b0d31-133">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span> 

![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a><span data-ttu-id="b0d31-135">恭喜！</span><span class="sxs-lookup"><span data-stu-id="b0d31-135">Congratulations</span></span>

<span data-ttu-id="b0d31-136">在本課程中, 我們已瞭解如何建立 UI 面板, 以顯示 Azure 空間錨點體驗的目前狀態, 以提供使用者即時意見反應。</span><span class="sxs-lookup"><span data-stu-id="b0d31-136">In this lesson we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing user with real-time feedback.</span></span>


