---
title: Azure 空間錨點教學課程-3。 顯示 Azure 空間錨點意見反應
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 45a71cada97dff4a2fb32f2eaf7700816f2e0d42
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2019
ms.locfileid: "68702032"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a>3.顯示 Azure 空間錨點意見反應

在這一課, 您將瞭解如何在使用 Azure 空間錨點時, 為使用者提供錨點探索、事件和狀態的意見反應。

## <a name="objectives"></a>目標

* 瞭解如何設定 UI 面板, 以顯示目前 ASA 會話的相關重要資訊

* 瞭解並探索 ASA SDK 可供使用者使用的意見反應元素

## <a name="instructions"></a>指示

### <a name="set-up-asa-feedback-ui-panel"></a>設定 ASA 意見反應 UI 面板

1. 在本課程中, 我們不會使用 [SaveAnchorToDisk] 和 [ShareAnchor] 按鈕, 因此請選取這兩個按鈕, 並取消核取 [偵測器] 面板中的核取方塊 (如下所示) 以隱藏這些按鈕。
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. 接下來, 建立指示面板。 一開始先以滑鼠右鍵按一下 [指示] 按鈕, 將滑鼠停留在 [3D 物件] 上, 然後選取 [textmeshpro-text]。

![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. 調整文字的尺規和位置, 使其符合場景中的指示。 此外, 請確定所有文字的對齊都會置中。 然後從文字編輯器中刪除範例文字, 如下圖所示。

![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. 將 TextMeshPro 物件的名稱變更為 "FeedbackPanel"。
   

![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. 在 [專案] 面板中, 選取 [資產] 並按一下滑鼠右鍵, 然後選取 [在 explorer 中顯示]。
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

現在, 按一下[這裡](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E)以下載接下來幾個步驟所需的檔案。

6. 一旦開啟 explorer, 請選取 [資產] 資料夾, 然後按一下 [ASAmodulesAssets] 資料夾, 再將錨點意見反應腳本和錨點模組腳本檔案複製到資料夾中。 

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> 注意: 如果您看到快顯視窗, 詢問您是否要覆寫舊的或保留舊的, 請務必選取 [覆寫]。

7. 現在返回 [資產] 資料夾。 然後, 移至 "AzureSpatialAnchorsPlugin" 資料夾、[範例] 資料夾, 最後是 [腳本] 資料夾, 然後將 Azure 空間錨點示範包裝函式複製到該資料夾。 

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. 既然檔案已上傳, 請確定已選取 [feedbackpanel] 文字, 並在 ASA_feedback 階層中按一下 [新增元件], 然後在出現後加以選取, 以新增錨點意見反應腳本。 

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. 將 "feedbackPanel" 文字物件從 ASA_Feedback 階層拖曳至腳本底下的空插槽, 如下圖所示。 

![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a>恭喜！

在本課程中, 我們已瞭解如何建立 UI 面板, 以顯示 Azure 空間錨點體驗的目前狀態, 以提供使用者即時意見反應。


