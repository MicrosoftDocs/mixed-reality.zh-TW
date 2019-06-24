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
# <a name="displaying-azure-spatial-anchor-feedback"></a>顯示 Azure 空間的錨點的意見反應

在這一課，您將了解如何使用 Azure 空間的錨點時使用者提供意見反應錨點探索、 事件和狀態。

目標：

* 了解如何設定 UI 面板，其中顯示目前的 ASA 工作階段的相關重要資訊

* 了解和探索 ASA SDK 會提供給使用者的意見反應項目

  

## <a name="instructions"></a>指示

### <a name="set-up-asa-feedback-ui-panel"></a>設定 ASA 意見反應 UI 面板

1. 在這一課中，我們不會使用 「 SaveAnchorToDisk"和"ShareAnchor 」 按鈕因此選取這兩個按鈕，並取消核取 [偵測器] 面板中的核取方塊 （如下所示） 以隱藏這些按鈕。
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. 接下來，建立指示面板。 以滑鼠右鍵按一下"instructions"按鈕啟動，請停留在 「 3D 物件 」 並選取 「 textmeshpro-文字 」。

   

   ![module2chapter3step2im](images/module2chapter3step2im.PNG)

   3. 調整規模和位置的文字，使其符合場景中的指示。 此外，請確定會置中的所有文字的對齊方式。 然後，在下圖中所示，請從文字編輯器中，刪除的範例文字。


![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. 將 TextMeshPro 物件的名稱變更為 「 FeedbackPanel。 」
   
   ![module2chapter3step4im](images/module2chapter3step4im.PNG)
   
5. 在 [專案] 面板中，選取 「 資產 」，並按一下滑鼠右鍵，然後選取 [顯示總管] 中。
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

現在，按一下 [此處](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E)下載檔案所需在接下來的幾個步驟。

6. 檔案總管開啟後，請選取 [assets] 資料夾中，則 「 ASAmodulesAssets"資料夾中，與錨點回饋指令碼和錨點模組指令碼檔案複製到資料夾。 
   

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> 注意： 如果您會收到快顯視窗，詢問您是否想要覆寫舊，或保留舊請確定您選取 覆寫。

7. 現在回到 [Assets] 資料夾。 然後，進入 「 AzureSpatialAnchorsPlugin"資料夾中，範例 資料夾，然後最後指令碼 資料夾中，並將 Azure 空間的錨點示範包裝函式複製到該資料夾。 
   

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. 現在，將檔案上傳時，確認 「 feedbackpanel"文字已選取，ASA_feedback 階層中按一下 [新增元件] 並新增錨點回饋指令碼，藉由搜尋它，並選取它，它出現時。 
   
   

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. 拖曳至 「 feedbackPanel"文字物件從 ASA_Feedback 階層指令碼下方的空插槽如下圖所示。 
   

![module2chapter3step9im](images/module2chapter3step9im.PNG)

   

## <a name="congratulations"></a>恭喜！

在這一課，我們學到如何建立顯示 Azure 空間的錨點體驗的使用者提供即時回饋的目前狀態的 UI 面板的內容。


