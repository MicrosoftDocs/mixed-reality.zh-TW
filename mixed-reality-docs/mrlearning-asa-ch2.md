---
title: Azure Spatial Anchor 教學課程 - 2。 儲存、擷取和共用 Azure Spatial Anchors
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 36f25229469e848a3f0612a5971cc8e9381262f5
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "80362006"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2.儲存、擷取和共用 Azure Spatial Anchors

在本教學課程中，您將了解如何藉由將錨點識別碼儲存至 HoloLens 2 的儲存體，讓 Azure 空間錨點可儲存在多個應用程式工作階段上。 您也將了解如何將此錨點識別碼與其他裝置共用，以對齊多個裝置的錨點。

## <a name="objectives"></a>目標

* 了解如何以 HoloLens 2 本機磁碟作為來源或目標來儲存和擷取 Azure Spatial Anchor 識別碼，好讓識別碼可持續存在應用程式工作階段之間
* 了解如何讓多裝置案例中的使用者共用 Azure Spatial Anchor 識別碼

## <a name="preparing-the-scene"></a>準備場景

在 [專案] 視窗中，瀏覽至 [資產]   > [MRTK.Tutorials.AzureSpatialAnchors]   > [Prefabs]  資料夾。 按住 CTRL 鍵並按一下 [ButtonParent_SaveAnchorId]  和 [ButtonParent_ShareAnchorId]  以選取這兩個 Prefab，然後將其拖曳到 [階層] 視窗中來新增至場景中：

![mrlearning-asa](images/mrlearning-asa/tutorial2-section1-step1-1.png)

## <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>在應用程式工作階段之間保存 Azure 錨點 - 將錨點識別碼儲存至磁碟
<!-- TODO: Consider renaming to 'Persist Azure Anchors between app sessions' -->

在本節中，您將了解如何以 HoloLens 2 本機磁碟作為來源或目標，以儲存和擷取 Azure 錨點識別碼。 這可讓您在不同應用程式工作階段之間查詢 Azure 是否有相同的錨點識別碼，以便將具有錨點的全像投影放置在與先前應用程式工作階段相同的位置。

在 [階層] 視窗中，展開包含兩個按鈕的 **ButtonParent_SaveAnchorId**，一個按鈕用於將 Azure 錨點識別碼儲存至 HoloLens 2 儲存體，另一個用來從磁碟擷取已儲存的識別碼：

![mrlearning-asa](images/mrlearning-asa/tutorial2-section2-step1-1.png)

請遵循上一個教學課程中的[設定按鈕以操作場景](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene)指示來執行相同步驟，將 **Pressable Button Holo Lens 2 (指令碼)** 元件和 **Interactable (指令碼)** 元件設定在兩個按鈕上：

* 針對 **SaveAzureAnchorIdToDisk** 物件，請指派 AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** 函式。
* 針對 **GetAzureAnchorIdFromDisk** 物件，請指派 AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** 函式。

如果您將已更新的應用程式建立到 HoloLens，您現在可以藉由儲存 Azure 錨點識別碼，在應用程式工作階段之間保存 Azure Spatial Anchors。 若要進行測試，您可以依照下列步驟執行：

1. 將火箭發射器體驗移至想要的位置。
2. 啟動 Azure 工作階段。
3. 建立 Azure 錨點 (在火箭發射器體驗的位置上建立錨點)。
4. 將 Azure 錨點識別碼儲存至磁碟。
5. 重新啟動應用程式。
6. 從磁碟取得 Azure 錨點 (載入您剛儲存的錨點識別碼)。
7. 啟動 Azure 工作階段。
8. 尋找 Azure 錨點 (將火箭發射器體驗置於步驟 3 的位置)。

> [!NOTE]
> 若要完全重新啟動應用程式，在結束沉浸式應用程式檢視之後，您必須先關閉混合實境首頁中的應用程式視窗，然後再從 [開始] 功能表重新啟動應用程式。 如需其他詳細資料，您可以參閱[在 HoloLens 上使用應用程式](https://docs.microsoft.com/hololens/holographic-home#using-apps-on-hololens)一文。

## <a name="share-azure-anchors-between-multiple-devices"></a>在多個裝置之間共用 Azure 錨點

在本節中，您將了解如何在多個裝置之間共用 Azure 錨點識別碼。 這可讓多個裝置查詢 Azure 是否有相同的錨點識別碼，以便具有錨點的全像投影能夠進行空間對齊。 空間對齊 (亦即，在多個裝置之間看到相同實體位置中的相同全像投影) 是 HoloLens 2 本機共用體驗的關鍵。

在裝置之間傳輸 Azure 錨點識別碼的方式有很多種，包括[多使用者功能教學課程](mrlearning-sharing(photon)-ch1.md)系列中所述的方法。 在此範例中，您將使用簡單的 Web 服務，在裝置之間上傳和下載錨點識別碼。

在 [階層] 視窗中，展開包含兩個按鈕的 **ButtonParent_ShareAnchorId** 物件；一個按鈕用來將 Azure 錨點識別碼上傳至 Web 伺服器，另一個則用於從 Web 伺服器下載識別碼：

![mrlearning-asa](images/mrlearning-asa/tutorial2-section3-step1-1.png)

請遵循上一個教學課程中的[設定按鈕以操作場景](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene)指示來執行相同步驟，將 **Pressable Button Holo Lens 2 (指令碼)** 元件和 **Interactable (指令碼)** 元件設定在兩個按鈕上：

* 針對 **ShareAzureAnchorIdToNetwork** 物件，請指派 AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** 函式。
* 針對 **GetAzureAnchorIdFromNetwork** 物件，請指派 AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** 函式。

如果您將已更新的應用程式建立至兩部 HoloLens 裝置，您現在可以藉由共用 Azure 錨點識別碼，在裝置之間進行空間對齊。 若要進行測試，您可以依照下列步驟執行：

1. 在 HoloLens 裝置 1 上：將火箭發射器體驗移至想要的位置。
2. 在 HoloLens 裝置 1 上：啟動 Azure 工作階段。
3. 在 HoloLens 裝置 1 上：建立 Azure 錨點 (在火箭發射器體驗的位置上建立錨點)。
4. 在 HoloLens 裝置 1 上：將 Azure 錨點識別碼共用至網路。
5. 在 HoloLens 裝置 2 上：啟動應用程式。
6. 在 HoloLens 裝置 2 上：從網路取得共用錨點識別碼 (提取剛從 HoloLens 裝置 1 共用的錨點識別碼)。
7. 在 HoloLens 裝置 2 上：啟動 Azure 工作階段。
8. 在 HoloLens 裝置 2 上：尋找 Azure 錨點 (將火箭發射器體驗置於步驟 3 的位置)。

> [!TIP]
> 如果您只有一個 HoloLens，您仍然可以藉由重新啟動應用程式來測試此功能，而不用使用第二個 HoloLens 裝置。

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已了解如何藉由將 Azure Spatial Anchor 識別碼儲存至 HoloLens 上的本機碟，在應用程式工作階段與應用程式重新啟動之間保存 Azure Spatial Anchors。 您也已了解如何在多個裝置之間共用 Azure Spatial Anchors，以進行基本的多使用者靜態全像投影共用體驗。

在下一個教學課程中，您將了解如何為使用者提供即時回饋。 此回饋將包含有關錨點建立、環境理解品質和 Azure 工作階段狀態的資訊。 如果沒有任何回饋，使用者可能不知道錨點是否已成功上傳至 Azure、環境的品質是否足以建立錨點或目前狀態為何。

[下一課：3.顯示 Azure Spatial Anchor 意見反應](mrlearning-asa-ch3.md)
