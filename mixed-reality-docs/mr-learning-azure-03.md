---
title: Azure 雲端教學課程 - 3。 整合 Azure 自訂視覺
description: 完成此課程，以了解如何在 HoloLens 2 應用程式中執行 Azure 自訂視覺。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, hololens 2, azure 自訂視覺, azure 認知服務
ms.localizationpriority: high
ms.openlocfilehash: 0fc3793315dd05f91a6193b68343205f53a3092a
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376460"
---
# <a name="3-integrating-azure-custom-vision"></a>3.整合 Azure 自訂視覺

您將在本教學課程中了解如何使用 **Azure 自訂視覺**。您將上傳一組相片，將其與「追蹤物件」產生關聯，然後上傳至**自訂視覺**服務並開始訓練程序。 接著，您將使用該服務從網路攝影機摘要中捕捉相片，以偵測「追蹤物件」。

## <a name="objectives"></a>目標

* 了解 Azure 自訂視覺的基本概念
* 了解如何設定場景，以在此專案中使用自訂視覺
* 了解如何整合上傳、訓練和偵測影像

## <a name="understanding-azure-custom-vision"></a>了解 Azure 自訂視覺

**Azure 自訂視覺**是**認知服務**系列中的一部分，可用來訓練影像分類器。 影像分類器是一種 AI 服務，會使用訓練的模型來套用相符的標記。 我們的應用程式會使用此分類功能來偵測「追蹤物件」。

深入了解 [Azure 自訂視覺](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)。

## <a name="preparing-azure-custom-vision"></a>準備 Azure 自訂視覺

開始之前，您必須建立自訂視覺專案，而最快的方式是使用入口網站。

在＜上傳和標記影像＞區段之前，請遵循此[快速入門教學課程](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images)來設定帳戶和專案。

> [!WARNING]
> 若要訓練模型，您必須至少有 2 個標記，且每個標記應有 5 個影像。 若要使用此應用程式，您應至少建立一個包含 5 個影像的標記，如此之後的訓練程序才不會失敗。

## <a name="preparing-the-scene"></a>準備場景

在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.AzureCloudServices] > [Prefabs] > [Manager] 資料夾。

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-1.png)

從該處，將 Prefab **ObjectDetectionManager** 拖曳到場景階層中。

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-2.png)

在 [階層] 視窗中，找出 **ObjectDetectionManager** 物件並加以選取。
**ObjectDetectionManager** Prefab 包含 **ObjectDetectionManager (指令碼)** 元件，而且您可以從 [偵測器] 視窗看到其相依於數個設定。

## <a name="retrieving-azure-api-resource-credentials"></a>擷取 Azure API 資源認證

您可以從 Azure 入口網站和自訂視覺入口網站取得 **ObjectDetectionManager (指令碼)** 設定的必要認證。

### <a name="azure-portal"></a>Azure 入口網站

尋找並找出您在本教學課程＜準備場景＞一節中建立且類型為**認知服務**的自訂視覺資源。 按一下 [金鑰和端點] 以擷取必要的認證。

### <a name="custom-vision-dashboard"></a>自訂視覺儀表板

在[自訂視覺](https://www.customvision.ai/projects)儀表板中，開啟您在本教學課程中建立的專案，然後按一下頁面右上角的齒輪圖示，以開啟設定頁面。 您會在右側的＜資源＞區段中找到所需的認證。

現在，正確設定 **ObjectDetectionManager (指令碼)** 之後，請在場景階層中尋找 **的 SceneController** 物件，然後加以選取。

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-3.png)

您會在 **SceneController** 元件中看到 [物件偵測管理員] 欄位是空的，請將 **ObjectDetectionManager** 從階層拖曳至該欄位並儲存場景。

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-4.png)

## <a name="take-and-upload-images"></a>拍攝影像並上傳

執行場景並按一下 [設定物件]，然後輸入您在[上一課](mr-learning-azure-02.md)中建立的其中一個**追蹤物件名稱**。 現在，按一下**物件卡片**底部的 [電腦視覺] 按鈕。

新的視窗會隨即開啟，而您必須在其中拍攝六張相片來訓練模型，以進行影像辨識。 當您看到想要追蹤的物件時，請按一下 [相機] 按鈕並執行 AirTap，請執行此動作六次。

> [!TIP]
> 若要改善模型訓練，請嘗試拍攝角度和光源條件各不相同的影像。

當您有足夠的影像之後，請按一下 [訓練] 按鈕，在雲端中啟動模型訓練程序。 啟動訓練將會上傳所有影像並開始訓練，這可能需要一分鐘或更長的時間。 功能表內的訊息會指出目前進度，當其指示已完成時，您就可以停止應用程式

> [!TIP]
> **ObjectDetectionManager (指令碼)** 會直接將拍攝的影像上傳至自訂視覺服務。 另一種方式是使用自訂視覺 API 接受影像的 URL，作為練習，您可以修改 **ObjectDetectionManager (指令碼)** ，改為將影像上傳至 Blob 儲存體。

## <a name="detect-objects"></a>偵測物件

您現在可以將訓練的模型放到測試中、執行應用程式，然後從 [主功能表] 中按一下 [搜尋物件]，接著輸入有問題的**追蹤物件**名稱。 **物件卡片**會隨即出現，然後請按一下 [自訂視覺] 按鈕。 在這裡，**ObjectDetectionManager** 會開始在背景中取得相機中的拍攝影像，並在功能表上顯示進度。 將相機指向您用來訓練模型的物件，您將在不久後看到其已偵測到該物件。

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已了解如何使用 Azure 自訂視覺來訓練影像，並使用分類服務來偵測符合相關**追蹤物件**的影像。

在下一個教學課程中，您將了解如何使用 Azure Spatial Anchors，將「追蹤物件」與實體世界中的位置連結，以及如何顯示箭號來引導使用者回到追蹤物件的連結位置。

[下一個教學課程：4.整合 Azure Spatial Anchors](mr-learning-azure-04.md)
