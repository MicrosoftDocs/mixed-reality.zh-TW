---
title: Azure 空間錨點教學課程-3。 顯示 Azure 空間錨點意見反應
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 9f57cb9874aade2d6b19d0c061fd83eb04b9ef11
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2019
ms.locfileid: "73914385"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="a51cd-105">3. 顯示 Azure 空間錨點的意見反應</span><span class="sxs-lookup"><span data-stu-id="a51cd-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="a51cd-106">在這一課，您將瞭解如何在使用 Azure 空間錨點時，為使用者提供錨點探索、事件和狀態的意見反應。</span><span class="sxs-lookup"><span data-stu-id="a51cd-106">In this lesson, you'll learn how to provide users with feedback about anchor discovery, events and status when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="a51cd-107">目標</span><span class="sxs-lookup"><span data-stu-id="a51cd-107">Objectives</span></span>

* <span data-ttu-id="a51cd-108">瞭解如何設定 UI 面板，以顯示目前 ASA 會話的相關重要資訊</span><span class="sxs-lookup"><span data-stu-id="a51cd-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>

* <span data-ttu-id="a51cd-109">瞭解並探索 ASA SDK 可供使用者使用的意見反應元素</span><span class="sxs-lookup"><span data-stu-id="a51cd-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="instructions"></a><span data-ttu-id="a51cd-110">指示</span><span class="sxs-lookup"><span data-stu-id="a51cd-110">Instructions</span></span>

### <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="a51cd-111">設定 ASA 意見反應 UI 面板</span><span class="sxs-lookup"><span data-stu-id="a51cd-111">Set Up ASA Feedback UI Panel</span></span>

1. <span data-ttu-id="a51cd-112">在本課程中，我們不會使用 [SaveAnchorToDisk] 和 [ShareAnchor] 按鈕，因此，請選取這兩個按鈕，並取消核取 [偵測器] 面板中的核取方塊（如下所示）以隱藏這些按鈕。</span><span class="sxs-lookup"><span data-stu-id="a51cd-112">In this lesson, we are not using the "SaveAnchorToDisk" and "ShareAnchor" buttons, so select both buttons and uncheck the checkbox in the inspector panel (as shown below) to hide these buttons.</span></span>
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. <span data-ttu-id="a51cd-114">建立指示面板。</span><span class="sxs-lookup"><span data-stu-id="a51cd-114">Create the instruction panel.</span></span> <span data-ttu-id="a51cd-115">首先，以滑鼠右鍵按一下 [指示] 按鈕，將滑鼠停留在 [3D 物件] 上，然後選取 [textmeshpro-text]。</span><span class="sxs-lookup"><span data-stu-id="a51cd-115">Start by right-clicking the "instructions" button, hover over "3D Object" and select "textmeshpro-text."</span></span>

![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. <span data-ttu-id="a51cd-117">調整文字的縮放和定位，使其符合場景中的指示。</span><span class="sxs-lookup"><span data-stu-id="a51cd-117">Adjust the scale and positioning of the text, so that it matches with the instructions in your scene.</span></span> <span data-ttu-id="a51cd-118">此外，請確定所有文字的對齊都會置中。</span><span class="sxs-lookup"><span data-stu-id="a51cd-118">Also, ensure the alignment for all of the text is centered.</span></span> <span data-ttu-id="a51cd-119">然後從文字編輯器中刪除範例文字，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="a51cd-119">Then delete the sample text from the text editor, as shown in in the image below.</span></span>

![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. <span data-ttu-id="a51cd-121">將 TextMeshPro 物件的名稱變更為 "FeedbackPanel"。</span><span class="sxs-lookup"><span data-stu-id="a51cd-121">Change the name of the TextMeshPro object to "FeedbackPanel."</span></span>
   

![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. <span data-ttu-id="a51cd-123">請確定已在 ASA_feedback 階層中選取 "feedbackpanel" 文字，按一下 [新增元件]，並藉由搜尋並在其出現後加以選取，來新增錨點意見反應腳本。</span><span class="sxs-lookup"><span data-stu-id="a51cd-123">Ensure that the "feedbackpanel" text is selected in the ASA_feedback hierarchy, click "add component" and add the anchor feedback script by searching for it and selecting it once it appears.</span></span> 

![module2chapter3step8im](images/module2chapter3step8im.PNG)

6. <span data-ttu-id="a51cd-125">將 "feedbackPanel" 文字物件從 ASA_Feedback 階層拖曳至腳本底下的空插槽中，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="a51cd-125">Drag the "feedbackPanel" text object from the ASA_Feedback hierarchy into the empty slot beneath the script as seen in the picture below.</span></span> 

![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a><span data-ttu-id="a51cd-127">恭喜！</span><span class="sxs-lookup"><span data-stu-id="a51cd-127">Congratulations</span></span>

<span data-ttu-id="a51cd-128">在本課程中，我們已瞭解如何建立 UI 面板，以顯示 Azure 空間錨點體驗的目前狀態，以提供使用者即時意見反應。</span><span class="sxs-lookup"><span data-stu-id="a51cd-128">In this lesson, we learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>


