---
title: Azure 空間錨點教學課程-3。 顯示 Azure 空間錨點意見反應
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 19529cbfebd74938395545c329097d42b5af9ff9
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334400"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a>3. 顯示 Azure 空間錨點的意見反應

在這一課，您將瞭解如何在使用 Azure 空間錨點時，為使用者提供錨點探索、事件和狀態的意見反應。

## <a name="objectives"></a>目標

* 瞭解如何設定 UI 面板，以顯示目前 ASA 會話的相關重要資訊

* 瞭解並探索 ASA SDK 可供使用者使用的意見反應元素

## <a name="set-up-asa-feedback-ui-panel"></a>設定 ASA 意見反應 UI 面板

1. 在本課程中，我們不會使用 [SaveAnchorToDisk] 和 [ShareAnchor] 按鈕，因此，請選取這兩個按鈕，並取消核取 [偵測器] 面板中的核取方塊（如下所示）以隱藏這些按鈕。

    ![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. 建立指示面板。 首先，以滑鼠右鍵按一下 [指示] 按鈕，將滑鼠停留在 [3D 物件] 上，然後選取 [textmeshpro-text]。

    ![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. 調整文字的縮放和定位，使其符合場景中的指示。 此外，請確定所有文字的對齊都會置中。 然後從文字編輯器中刪除範例文字，如下圖所示。

    ![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. 將 TextMeshPro 物件的名稱變更為 "FeedbackPanel"。

    ![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. 請確定已在 ASA_feedback 階層中選取 "feedbackpanel" 文字，按一下 [新增元件]，並藉由搜尋並在其出現後加以選取，來新增錨點意見反應腳本。

    ![module2chapter3step8im](images/module2chapter3step8im.PNG)

6. 將 "feedbackPanel" 文字物件從 ASA_Feedback 階層拖曳至腳本底下的空插槽中，如下圖所示。

    ![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a>恭喜您

在本課程中，我們已瞭解如何建立 UI 面板，以顯示 Azure 空間錨點體驗的目前狀態，以提供使用者即時意見反應。
