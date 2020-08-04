---
title: Azure 雲端教學課程 - 4. 整合 Azure Spatial Anchors
description: 完成此課程以了解如何在 HoloLens 2 應用程式中實作 Azure Spatial Anchors。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, hololens 2, Azure spatial anchors
ms.localizationpriority: high
ms.openlocfilehash: 468ba0d8e9fca85dc266b662f402f5c956dc94bb
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376440"
---
# <a name="4-integrating-azure-spatial-anchors"></a>4.整合 Azure Spatial Anchors

在本教學課程中，您將了解如何使用 **Azure Spatial Anchors**。 您會將**追蹤物件**儲存為 Azure Spatial Anchor。 然後，您會查詢並向使用者顯示指向該位置的指示箭頭。

## <a name="objectives"></a>目標

* 了解 Azure Spatial Anchors 的基本概念。
* 了解如何設定場景，以在此專案中使用 Azure Spatial Anchors。
* 了解如何整合儲存和查詢位置。

## <a name="understanding-azure-spatial-anchors"></a>了解 Azure Spatial Anchors

 **Azure Spatial Anchors** 是 Azure 雲端服務系列中的一部分，可用來儲存錨點位置。 您可以根據雲端的「錨點識別碼」來擷取已儲存的錨點位置。 此錨點位置可以由多平台裝置共用及存取，例如 HoloLens、iOS 和 Android 裝置。

深入了解 [Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/overview)。

## <a name="preparing-azure-spatial-anchors"></a>準備 Azure Spatial Anchors

開始之前，您必須在 Azure 入口網站中建立空間錨點資源。
了解如何建立[空間錨點資源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource)。

## <a name="preparing-the-scene"></a>準備場景

在本節中，您將了解如何設定場景，並進行必要的變更。

在 [專案] 視窗中，瀏覽至 [資產] > [MRTKMRTK.Tutorials.AzureCloudServices] > [Prefabs] > [Manager]

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step1-1.png)

從 [Manager] 資料夾，將 Prefab **Anchor Manager** 拖放到場景階層中。

選取階層中的 **Anchor Manager** GameObject，然後在 [偵測器] 區段中，您會看到 **Spatial Anchor Manager** (指令碼)。 尋找 [帳戶識別碼] 和 [金鑰] 欄位，然後新增您在先前階段的必要條件中所建立的認證。

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step2-1.png)

現在，在場景階層中尋找**Scene Controller** 物件，然後加以選取。 您會看到 **Scene Controller** 偵測器。

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step3-1.png)

您會發現 **Scene Controller** 中的 **Anchor Manager** 欄位是空的，請將 **Anchor Manager** 從場景中的階層拖放到該欄位，然後儲存場景。

## <a name="build-and-deploy-the-app-to-your-hololens-2"></a>建置應用程式，並將其部署至 HoloLens 2

Azure Spatial Anchors 無法在 Unity 中執行，因此若要測試 Azure Spatial Anchors 功能，您必須將專案部署至您的裝置。

> [!TIP]
> 如需有關如何建立 Unity 專案並將其部署至 HoloLens 2 的提醒，您可以參閱[對您的 HoloLens 2 建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示。

## <a name="run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>在 HoloLens 2 上執行應用程式，並遵循應用程式內的指示

### <a name="create-an-anchor-to-store-a-location"></a>建立錨點以儲存位置

在本節中，您將了解如何儲存物件位置。

執行應用程式，然後在體驗的主功能表中，按一下 [設定物件]。

提供您想要儲存的物件**名稱**，然後按一下 [設定物件] 以繼續。 若要新增有關物件的詳細資訊，請選取**影像**，並描述物件。

若要儲存位置，請按一下 [儲存位置]

您會看到**錨點指標**，您可以在想要儲存的位置上移動和放置該指標。 之後，您會看到確認快顯視窗。 如果您想要確認並儲存位置，請按一下 [是]；否則，您可以按一下 [否]，然後再次選取位置來變更位置。

當您按一下 [是] 來確認位置之後，位置和錨點識別碼將會儲存在 Azure 雲端儲存體中。 儲存之後，您會在錨點中看到具有物件名稱的**物件標記**。

現在已成功儲存物件位置。

### <a name="query-for-finding-an-anchor-location"></a>尋找錨點位置的查詢

成功儲存錨點位置之後，您現在可以在主功能表中選取 [搜尋物件] 來尋找錨點位置。

按一下 [搜尋物件] 之後，新視窗會隨即出現，您應該在其中提供要搜尋的物件名稱。

輸入物件的名稱，然後按一下 [搜尋物件]。 如果先前已儲存物件，而且可在資料庫中找到，您將會取得物件卡片，其中包含您稍早所儲存物件的所有詳細資料。

現在您可以按一下 [顯示位置] 來尋找物件。 按一下 [顯示位置] 之後，系統就會從雲端儲存體中查詢物件位址。

成功擷取位置之後，**箭頭**就會將您導向物件的位置。 遵循箭頭標記，直到您找到物件的位置。

您找到物件後，物件名稱就會出現在頂端，而箭頭將會消失，此時您可以按一下 [物件標記] 來查看物件的詳細資料。

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已了解 Azure Spatial Anchors 可以如何儲存和擷取 Hololense 2 上的物件位置。

在最後一個教學課程中，您將了解如何使用 **Azure Bot Service**，將自然語言新增為我們應用程式的新互動方法。

[下一個教學課程：5.整合 Azure Bot Service 與 LUIS](mr-learning-azure-05.md)
