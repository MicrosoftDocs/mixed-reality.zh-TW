---
title: Azure 空間錨點教學課程-2。 儲存、抓取和共用 Azure 空間錨點
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 7b19233a9634e2568200476c9483464bbf9dd3c8
ms.sourcegitcommit: a580166a19294f835b8e09c780f663f228dd5de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77250729"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2. 儲存、抓取和共用 Azure 空間錨點

在本教學課程中，您將瞭解如何藉由將錨點識別碼儲存至 HoloLens 2 的儲存體，來將 Azure 空間錨點儲存在多個應用程式會話。 您也將瞭解如何將此錨點識別碼與其他裝置共用，以進行多重裝置錨點對齊。

## <a name="objectives"></a>目標

* 瞭解如何在應用程式會話之間持續儲存和取出 HoloLens 2 本機磁片的 Azure 空間錨點識別碼
* 瞭解如何在多裝置案例中，共用使用者之間的 Azure 空間錨點識別碼

## <a name="preparing-the-scene"></a>準備場景

在 [專案] 視窗中，流覽至 [**資產**] [ > **MRTK]。教學課程. AzureSpatialAnchors** > **Prefabs**資料夾。 按住 CTRL 鍵時，按一下  **ButtonParent_SaveAnchorId**並**ButtonParent_ShareAnchorId**以選取兩個 prefabs，然後將它們拖曳到 階層 視窗，將它們加入場景中：

![mrlearning-asa](images/mrlearning-asa/tutorial2-section1-step1-1.png)

## <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>在應用程式會話之間保存 Azure 錨點-將錨點識別碼儲存至磁片
<!-- TODO: Consider renaming to 'Persist Azure Anchors between app sessions' -->

在本節中，您將瞭解如何在 HoloLens 2 本機磁片中儲存和取出 Azure 錨點識別碼。 這可讓您在不同的應用程式會話之間查詢 Azure 是否有相同的錨點識別碼，以便將錨定的全息影像放置在與先前應用程式會話相同的位置。

在 [階層] 視窗中，展開包含兩個按鈕的 [ **ButtonParent_SaveAnchorId** ] 物件，一個按鈕用於將 Azure 錨點識別碼儲存至 HoloLens 2 儲存體，另一個用於從磁片抓取已儲存的識別碼：

![mrlearning-asa](images/mrlearning-asa/tutorial2-section2-step1-1.png)

遵循從上一個教學課程設定[按鈕以操作場景](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene)指示中的相同步驟，在兩個按鈕上設定**Pressable 按鈕 hololens 透鏡2（腳本）** 元件和**可互動（腳本）** 元件：

* 針對**SaveAzureAnchorIdToDisk**物件，指派 AnchorModuleScript > **SaveAzureAnchorIdToDisk （）** 函數。
* 針對**GetAzureAnchorIdFromDisk**物件，指派 AnchorModuleScript > **GetAzureAnchorIdFromDisk （）** 函數。

如果您將已更新的應用程式建立到 HoloLens，您現在可以藉由儲存 Azure 錨點識別碼，在應用程式會話之間保存 Azure 空間錨點。 若要測試它，您可以依照下列步驟執行：

1. 將 Rocket 啟動器體驗移至所需的位置。
2. 啟動 Azure 會話。
3. 建立 Azure 錨點（在 Rocket 啟動器體驗的位置建立錨點）。
4. 將 Azure 錨點識別碼儲存至磁片。
5. 重新開機應用程式。
6. 從磁片取得 Azure 錨點（載入您剛儲存的錨點識別碼）。
7. 啟動 Azure 會話。
8. 尋找 Azure 錨點（將 Rocket 啟動器體驗置於步驟3的位置）。

## <a name="share-azure-anchors-between-multiple-devices"></a>在多個裝置之間共用 Azure 錨點

在本節中，您將瞭解如何在多個裝置之間共用 Azure 錨點識別碼。 這可讓多個裝置查詢 Azure 是否有相同的錨點識別碼，讓錨定的全息圖形能夠進行空間對齊。 空間對齊（亦即，在多個裝置之間的相同實體位置中看到相同的全息影像）是 HoloLens 2 中本機共用體驗的關鍵。

有許多方式可以在裝置之間傳輸 Azure 錨點識別碼，包括[多使用者功能教學](mrlearning-sharing(photon)-ch1.md)課程系列中所述的方法。 在此範例中，您將使用簡單的 web 服務，在裝置之間上傳和下載錨點識別碼。

在 [階層] 視窗中，展開包含兩個按鈕的**ButtonParent_ShareAnchorId**物件;一個按鈕，用來將 Azure 錨點識別碼上傳至 web 伺服器，另一個則用於從 web 伺服器下載識別碼：

![mrlearning-asa](images/mrlearning-asa/tutorial2-section3-step1-1.png)

遵循從上一個教學課程設定[按鈕以操作場景](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene)指示中的相同步驟，在兩個按鈕上設定**Pressable 按鈕 hololens 透鏡2（腳本）** 元件和**可互動（腳本）** 元件：

* 針對**ShareAzureAnchorIdToNetwork**物件，指派 AnchorModuleScript > **ShareAzureAnchorIdToNetwork （）** 函數。
* 針對**GetAzureAnchorIdFromNetwork**物件，指派 AnchorModuleScript > **GetAzureAnchorIdFromNetwork （）** 函數。

如果您將已更新的應用程式建立至兩部 HoloLens 裝置，您現在可以藉由共用 Azure 錨點識別碼，達到其之間的空間對齊方式。 若要測試它，您可以依照下列步驟執行：

1. 在 HoloLens 裝置1上：將 Rocket 啟動器體驗移到想要的位置。
2. 在 HoloLens 裝置1上：啟動 Azure 會話。
3. 在 HoloLens 裝置1上：建立 Azure 錨點（在 Rocket 啟動器體驗的位置建立錨點）。
4. 在 HoloLens 裝置1上：共用 Azure 錨點識別碼到網路。
5. 在 HoloLens 裝置2上：重新開機應用程式。
6. 在 HoloLens 裝置2上：從網路取得共用錨點識別碼（提取剛從 HoloLens 裝置共用的錨點識別碼）。
7. 在 HoloLens 裝置2上：啟動 Azure 會話。
8. 在 HoloLens 裝置2上：尋找 Azure 錨點（將 Rocket 啟動器體驗置於步驟3的位置）。

> [!TIP]
> 如果您只有一個 HoloLens，您仍然可以藉由重新開機應用程式，而不是使用第二個 HoloLens 裝置來測試功能。

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已瞭解如何藉由將 Azure 空間錨點識別碼儲存至 HoloLens 上的本機磁片，在應用程式會話與應用程式重新開機之間保存 Azure 空間錨點。 您也已瞭解如何在多個裝置之間共用 Azure 空間錨點，以進行基本的多使用者、靜態全息影像共用體驗。

在下一個教學課程中，您將學習如何提供使用者即時意見反應。 此意見反應將包含有關錨點建立、環境理解品質和 Azure 會話狀態的資訊。 如果沒有任何意見反應，使用者可能不知道錨點是否已成功上傳至 Azure、環境的品質是否足以進行錨點建立，或目前的狀態。

[下一課： 3. 顯示 Azure 空間錨點意見反應](mrlearning-asa-ch3.md)
