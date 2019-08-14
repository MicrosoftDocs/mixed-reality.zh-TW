---
title: Azure 空間錨點教學課程-2。 儲存、抓取和共用 Azure 空間錨點
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 70f84c1ec03919a15bed486ffa51fb57db39deec
ms.sourcegitcommit: 599bbdd861ce6ff11b6cfb345a0a995f8b7bf85b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68977975"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2.儲存、抓取和共用 Azure 空間錨點

在本教學課程中, 我們將瞭解如何藉由將錨點資訊儲存至 HoloLens 2 的磁片, 將我們的 Azure 空間錨點儲存在多個應用程式會話。 我們也將瞭解如何將此錨點資訊與其他裝置共用, 以進行多重裝置錨定的對齊。

## <a name="objectives"></a>目標

* 瞭解如何從 HoloLens 2 本機磁片儲存和取出 Azure 空間錨點資訊, 以在應用程式會話之間持續保留

* 瞭解如何在多裝置案例中, 于使用者之間共用 Azure 空間錨點資訊

## <a name="instructions"></a>指示

### <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>在應用程式會話之間保存 Azure 錨點-將錨點識別碼儲存至磁片

1. 搜尋 SaveAnchorToDisk prefab 並將其新增至您的場景。 其中包含兩個按鈕, 一個按鈕用來將任何可用的 Azure 錨點識別碼儲存至 HoloLens 2 磁片, 另一個則用於從磁片中抓取任何識別碼。

![module2chapter2step1im](images/module2chapter2step1im.PNG)

2. 根據下列指示設定每個按鈕

   - 針對名為 SaveToDisk 的按鈕, 在 [已按下的事件觸發程式] 和 [On Click] 事件觸發程式底下, 建立新的事件。 將 ParentAnchor 物件拖曳至空白欄位, 然後從 ParentAnchor 物件的 ASAmoduleScript 元件指派 SaveAzureAnchorIDToDisk () 方法。
   
     > 注意: 有些按鈕可能會與場景中的其他按鈕重迭。 請隨意調整按鈕的定位。

![module2chapter2step2aim](images/module2chapter2step2aim.PNG)

![module2chapter2step2aim](images/module2chapter2step2bim.PNG)

![module2chapter2step2aim](images/module2chapter2step2cim.PNG)


   - 針對名為 GetFromDisk 的按鈕, 在 [已按下的事件觸發程式] 和 [On Click] 事件觸發程式底下, 建立新的事件。 將 ParentAnchor 物件拖曳至空白欄位, 然後從 ParentAnchor 物件的 ASAmoduleScript 元件指派 LoadAzureAnchorIDsFromDisk () 方法。

3. 依照教學課程1中的指示, 將更新的應用程式建立至您的裝置。 依照您在上一課所做的操作, 按下 [建立 Azure 錨點] 按鈕之後, 您現在可以按 [儲存至磁片] 按鈕, 將 Azure 錨點識別碼儲存至磁片。

4. 重新開機應用程式, 啟動 Azure 會話, 按 [載入錨點識別碼], 然後按 [尋找 Azure 錨點], 找出與我們儲存到磁片的識別碼相關聯的錨點。 整個場景現在應該會在您先前儲存錨點的位置貼齊位置!

### <a name="share-azure-anchors-between-multiple-devices"></a>在多個裝置之間共用 Azure 錨點

在本節中, 我們將瞭解如何在多個裝置之間共用 Azure 錨點識別碼。 這可讓多個裝置查詢 Azure 是否有相同的錨點識別碼, 讓我們的錨定的全息影像和場景能夠以空間對齊。 空間對齊 (在多個裝置之間的相同實體位置中看到相同的全息影像) 是 HoloLens 2 中本機共用體驗的關鍵。 有許多方式可以傳輸裝置之間有關 azure 識別碼的資訊, 包括 Azure 空間錨點共用體驗教學課程[教學](mrlearning-sharing(photon)-ch1.md)課程中所述的方法。 這個範例會使用簡單的 web 服務, 在裝置之間上傳和下載錨點識別碼。

1. 將 ShareAnchor prefab 新增至您的階層。 此 prefab 會將兩個新按鈕新增至您的場景;一個用來上傳錨點識別碼資訊, 另一個用於下載錨點識別碼資訊。 

![module2chapter2step5im](images/module2chapter2step5im.PNG)

2. 根據下列指示設定每個按鈕

   - 針對名為 SendSharedAnchor 的按鈕, 在 [已按下的事件觸發程式] 和 [On Click] 事件觸發程式底下建立新事件。 將 ParentAnchor 物件拖曳至空白欄位, 然後從 ParentAnchor 物件的 ASAmoduleScript 元件指派 ShareAnchor () 方法。

![module2chapter2step6aim](images/module2chapter2step6aim.PNG)

![module2chapter2step6bim](images/module2chapter2step6bim.PNG)

   - 針對名為 GetSharedAnchor 的按鈕, 在 [已按下的事件觸發程式] 和 [On Click] 事件觸發程式底下建立新事件。 將 ParentAnchor 物件拖曳至空白欄位, 然後從 ParentAnchor 物件的 ASAmoduleScript 元件指派 GetSharedAzureAnchor () 方法。

3. 依照[教學課程 1](mrlearning-base-ch1.md)中的指示進行。 將更新的應用程式建立至您的裝置。 依照您在上一課所做的操作, 按下 [建立 Azure 錨點] 按鈕之後, 您現在可以按 [與其他裝置共用] 按鈕, 將 Azure 錨點識別碼與其他裝置共用。

   > 注意:選取父錨點, 並向下卷到父錨點腳本。 請確定您的公用共用 pin 是唯一的, 因此當您共用時, 您知道它是您共用的。 可能有數千名使用者共用其 Azure 錨點, 因此這麼做可讓您確保您共用的是正確的 Azure 錨點。

4. 如果您有另一部 HoloLens 2 裝置, 請啟動應用程式, 然後啟動 Azure 會話。 按 [取得共用錨點識別碼] 按鈕, 然後按 [尋找 Azure 錨點] 按鈕, 以找出與我們儲存到磁片的識別碼相關聯的錨點。 整個場景現在應該會貼齊位置, 其位於另一部 HoloLens 2 裝置上! 如果您只有一個 HoloLens 2, 您仍然可以藉由重新開機應用程式、啟動 Azure 會話, 然後按 [取得共用的錨點識別碼] 按鈕按鈕來測試功能, 然後按 [尋找 Azure 錨點] 按鈕, 找出與下列相關聯的錨點:儲存到磁片的識別碼。 整個場景現在應該會在您先前儲存錨點的位置貼齊位置!

## <a name="congratulations"></a>恭喜！
在這一課, 您已瞭解如何藉由將 Azure 空間錨點識別碼儲存到 HoloLens 2 上的本機磁片, 在應用程式會話和應用程式重新開機之間保存 Azure 空間錨點。 您也已瞭解如何在多個裝置之間共用 Azure 空間錨點, 以進行基本的多使用者、靜態全息影像共用體驗。

我們會瞭解如何在共用模組的最後一課, 將 Azure 空間錨點實作為完全互動的本機共用體驗的一部分。 本機共用體驗可能包括同步處理的3D 物件位置、旋轉和縮放、每個使用者的識別碼, 以及共用的應用程式狀態等功能。 Azure 空間錨點藉由提供每個參與者一個通用錨點, 讓所有使用者都能看到相同實體位置中的虛擬物件, 藉此增強這些共用案例。 這適用于各種裝置平臺, 包括 HoloLens、Android 和 iOS 裝置。 若要瞭解如何開發共用體驗, 請完成共用模組中的所有課程。

在下一課中, 我們將學習如何提供使用者即時意見反應。 此意見反應將包含有關錨點建立、環境理解品質和 Azure 會話狀態的資訊。 如果沒有任何意見反應, 使用者可能不知道錨點是否已成功上傳至 Azure、環境的品質是否足以進行錨點建立, 或目前的狀態。

[下一課：3.顯示 Azure Spatial Anchor 意見反應](mrlearning-asa-ch3.md)

