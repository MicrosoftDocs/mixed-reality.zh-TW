---
title: MR 學習 ASA 模組上 HoloLens 2 Azure 空間的錨點
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: f8a52660fe05b6ed4508321ed246b8e299b75bca
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523339"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2.儲存、 擷取和共用 Azure 空間的錨點

在本教學課程中，我們將了解如何跨多個應用程式工作階段儲存我們 Azure 空間的錨點，我們的錨點資訊儲存到 HoloLens 2 的磁碟。 我們也將了解如何共用此錨點的資訊到 multi-device 錨點的對齊方式的其他裝置。

## <a name="objectives"></a>目標

* 了解如何儲存和擷取 Azure 空間的錨點資訊從 HoloLens 2 本機磁碟，但應用程式工作階段之間的持續性

* 了解如何在 Azure 空間的錨點之間共用資訊在多重裝置的案例中的使用者

  

## <a name="instructions"></a>指示

### <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>保存 Azure 應用程式工作階段-儲存到磁碟的錨點識別碼之間的錨點

1. 搜尋並新增至場景的 SaveAnchorToDisk prefab。 這些包括兩個按鈕、 一個按鈕，將任何可用的 Azure 錨點識別碼儲存至 HoloLens 2 磁碟，另一個用於從磁碟擷取任何識別碼。

   ![module2chapter2step1im](images/module2chapter2step1im.PNG)

2. 設定每個按鈕，依照下列指示
   - 名為 SaveToDisk 按鈕，建立新的事件，在按下按鈕事件觸發程序，以及在按一下 事件觸發程序。 ParentAnchor 物件拖曳至空白的欄位，並將指派 SaveAzureAnchorIDToDisk() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。
   
     > 注意： 部分按鈕可能會出現重疊的場景中的其他按鈕。 您可以自由調整按鈕的定位項目。
   

  ![module2chapter2step2aim](images/module2chapter2step2aim.PNG)

![module2chapter2step2aim](images/module2chapter2step2bim.PNG)

![module2chapter2step2aim](images/module2chapter2step2cim.PNG)

   - 名為 GetFromDisk 按鈕，建立新的事件，在按下按鈕事件觸發程序，以及在按一下 事件觸發程序。 ParentAnchor 物件拖曳至空白的欄位，並將指派 LoadAzureAnchorIDsFromDisk() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。

3. 請遵循 Tutoiral 1，以建置到您的裝置更新的應用程式的指示。 之後按下 建立 Azure 錨點 按鈕，如同在先前的課程中，您可能現在儲存 Azure 錨點識別碼磁碟藉由按下儲存至磁碟 按鈕。

4. 重新啟動應用程式中啟動 Azure 工作階段，請按負載錨點識別碼，然後按找出 Azure 錨點來尋找我們儲存至磁碟的識別碼相關聯的錨點。 在整個場景現在應該貼齊位置，位置在您的錨點先前儲存 ！

### <a name="share-azure-anchors-between-multiple-devices"></a>多個裝置之間共用 Azure 錨點

在本節中，我們將了解如何共用在多個裝置之間的 Azure 錨點識別碼。 這可讓多個裝置，若要查詢 Azure 相同的錨點識別碼，讓我們的錨定全像投影和場景在空間上對齊。 空間 （出現在多個裝置之間的相同實體位置相同全像投影） 的對齊方式為 HoloLens 2 中的金鑰至本機共用的體驗。 有許多方法來傳輸資訊之間的裝置，包括方法的相關 azure 識別碼中所述 Azure 空間的錨點共用體驗教學課程 (TODO： 加入連結。)此範例會使用簡單的 web 服務上傳和下載裝置之間的錨點識別碼。

1. 新增到您的階層 ShareAnchor prefab。 此 prefab 將兩個新按鈕加入至場景;另一個用於上傳錨點識別碼資訊和下載的另一個錨點識別碼資訊。 

   ![module2chapter2step5im](images/module2chapter2step5im.PNG)

2. 設定每個按鈕，依照下列指示

   - 名為 SendSharedAnchor，按鈕建立新的事件，在按下按鈕事件觸發程序，以及在按一下 事件觸發程序。 ParentAnchor 物件拖曳至空白的欄位，並將指派 ShareAnchor() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。

     ![module2chapter2step6aim](images/module2chapter2step6aim.PNG)

     ![module2chapter2step6bim](images/module2chapter2step6bim.PNG)

     

   - 名為 GetSharedAnchor，按鈕建立新的事件，在按下按鈕事件觸發程序，以及在按一下 事件觸發程序。 ParentAnchor 物件拖曳至空白的欄位，並將指派 GetSharedAzureAnchor() 方法從 ParentAnchor 物件之 ASAmoduleScript 元件。

3. 請依照下列指示[教學課程 1](mrlearning-base-ch1.md)。 若要建置到您的裝置更新的應用程式。 之後按下 [建立 Azure 錨點] 按鈕，如同在先前的課程中，您可能現在共用 Azure 錨點識別碼，與其他裝置按共用到其他的裝置。

   > 注意:選取父錨點和向下父錨點指令碼捲動。 請確定您公開共用的 pin 碼是唯一的，如此當您共用它，您就會知道它是您所共用。 可能有數千個使用者共用其 Azure 的錨點，以讓執行此動作可讓您確保您共用的正確 Azure 錨點。

4. 如果您有另一個 HoloLens 2 裝置時，啟動應用程式，然後再啟動 Azure 工作階段。 按下 取得共用的錨點識別碼 按鈕，然後按 找出 Azure 錨點 按鈕，以找出我們儲存至磁碟的識別碼相關聯的錨點。 在整個場景現在應該放置到指定位置，在何處放置在其他的 HoloLens 2 裝置 ！ 如果您只需要一個 HoloLens 2，您可能仍測試功能藉由重新啟動應用程式，啟動 Azure 工作階段，然後按 [[取得共用錨點識別碼] 按鈕] 按鈕，然後按 [找出 Azure 錨點] 按鈕，以找出錨點相關聯我們儲存至磁碟的識別碼。 在整個場景現在應該貼齊位置，位置在您的錨點先前儲存 ！

## <a name="congratulations"></a>恭喜！
在這一課，您了解如何將 Azure 空間的錨點識別碼儲存至本機磁碟中上 HoloLens 2, 應用程式工作階段與應用程式重新啟動之間保存 Azure 空間的錨點的內容。 您也學到如何針對基本的多使用者、 靜態全像共用經驗的多個裝置之間共用 Azure 空間的錨點。

我們了解如何實作 Azure 空間的錨點期間最後一課中的共用的模組完全互動式的本機共用體驗的一部分。 本機的共用經驗可能包括功能，例如每位使用者已同步處理的 3D 物件的位置、 旋轉和縮放比例 識別項，以及共用應用程式狀態。 Azure 空間的錨點可提供常見的錨點，可讓所有使用者會看到相同的實體位置中的虛擬物件中的每個參與者，進而強化這些共用的案例。 這是一組裝置平台，包括 HoloLens、 Android 和 iOS 裝置，則為 true。 若要了解如何開發分享的經驗，完成共用模組中的所有課程。

在下一課中，我們將學習如何為使用者提供即時回饋。 此意見反應將錨點建立、 環境了解，品質和 Azure 的工作階段的狀態相關資訊。 沒有意見反應，使用者可能不知道是否為錨點已成功上的傳至 Azure，是否環境的品質就足以應付錨點建立或目前的狀態。

[下一課：ASA 教學課程 3](mrlearning-asa-ch3.md)

