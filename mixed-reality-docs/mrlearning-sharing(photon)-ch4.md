---
title: 多使用者功能教學課程 - 5。 將 Azure Spatial Anchors 整合到共用體驗
description: 完成此課程以了解如何在 HoloLens 2 應用程式中實作使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: c27ed7327cfe0a61f2b63e309348bdea1a535ea1
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604969"
---
# <a name="4-integrating-azure-spatial-anchors-into-a-shared-experience"></a>4.將 Azure Spatial Anchors 整合到共用體驗

在此教學課程中，您將了解如何將 Azure Spatial Anchors (ASA) 整合到共用體驗中。 ASA 可讓多部裝置共同參照實體世界，讓使用者可以看到實際實體位置中的彼此，並看到相同位置中的共用體驗。

## <a name="objectives"></a>目標

* 將 ASA 整合到多個裝置一致的共用體驗
* 了解 ASA 如何在本機共用體驗內容中運作的基本概念

## <a name="preparing-the-scene"></a>準備場景

在 [階層] 視窗中，展開 **SharedPlayground** 物件，然後展開 **TableAnchor** 物件以公開其子物件：

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section1-step1-1.png)

在 [專案] 視窗中，瀏覽至 [資產]   > [MRTK.Tutorials.MultiUserCapabilities]   > [Prefabs]  資料夾，並將**按鈕**預製物件 (Prefab) 拖曳到階層視窗中的 **TableAnchor** 子物件上方，以將其作為 TableAnchor 物件的子系來新增至您的場景：

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a>設定按鈕以操作場景

在本節中，您將設定一系列的按鈕事件，以示範如何使用 Azure Spatial Anchors 來達到共用體驗中的空間對齊。

在 [階層] 視窗中，展開 **Button** 物件，然後選取名為 **StartAzureSession** 的第一個子按鈕物件：

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-1.png)

在 [偵測器] 視窗中，找出 **Interactable (指令碼)** 元件，並設定 **OnClick ()** 事件，如下所示：

* 針對 [無 (物件)]  欄位，請指派 **TableAnchor** 物件
* 從 [無函式]  下拉式清單中，選取 **AnchorModuleScript** > **StartAzureSession ()** 函式

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-2.png)

在 [階層] 視窗中，選取名為 **CreateAzureAnchor** 的第二個子按鈕物件，然後在 [偵測器] 視窗中，找出 **Interactable (指令碼)** 元件，並設定 **OnClick ()** 事件，如下所示：

* 針對 [無 (物件)]  欄位，請指派 **TableAnchor** 物件
* 從 [無函式]  下拉式清單中，選取 **AnchorModuleScript** > **CreateAzureAnchor ()** 函式
* 針對所顯示的 [無 (遊戲物件)]  欄位，請指派 **TableAnchor** 物件

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-3.png)

在 [階層] 視窗中，選取名為 **ShareAzureAnchor** 的第三個子按鈕物件，然後在 [偵測器] 視窗中，找出 **Interactable (指令碼)** 元件，並設定 **OnClick ()** 事件，如下所示：

* 針對 [無 (物件)]  欄位，請指派 **TableAnchor** 物件
* 從 [無函式]  下拉式清單中，選取 **AnchorModuleScript** > **CreateAzureAnchor ()** 函式

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-4.png)

在 [階層] 視窗中，選取名為 **GetAzureAnchor** 的第四個子按鈕物件，然後在 [偵測器] 視窗中，找出 **Interactable (指令碼)** 元件，並設定 **OnClick ()** 事件，如下所示：

* 針對 [無 (物件)]  欄位，請指派 **TableAnchor** 物件
* 從 [無函式]  下拉式清單中，選取 **SharingModuleScript** > **GetAzureAnchor ()** 函式

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a>將場景連線至 Azure 資源

在 [階層] 視窗中，展開 **SharedPlayground** 物件，然後選取 **TableAnchor** 物件。 然後在 [偵測器] 視窗中，找出 **Spatial Anchor Manager (指令碼)** 元件，並使用 Azure Spatial Anchors 帳戶中的認證來設定 [認證]  區段，該帳戶會在本教學課程系列的[必要條件](mrlearning-sharing(photon)-ch1.md#prerequisites)中建立：

* 在 [Spatial Anchors Account 識別碼]  欄位中，貼上 Azure Spatial Anchors 帳戶中的**帳戶識別碼**
* 在 [Spatial Anchors 帳戶金鑰]  欄位中，貼上 Azure Spatial Anchors 帳戶中的主要或次要**存取金鑰**

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section3-step1-1.png)

在仍選取 **TableAnchor** 物件的情況下，在 [偵測器] 視窗中，確定已啟用所有指令碼元件：

* 勾選 **Spatial Anchor Manager (指令碼)** 元件旁的核取方塊來將其啟用
* 勾選 **Anchor Module Script (指令碼)** 元件旁的核取方塊來將其啟用
* 勾選 **Sharing Module Script (指令碼)** 元件旁的核取方塊來將其啟用

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section3-step1-2.png)

## <a name="trying-the-experience-with-spatial-alignment"></a>試用空間對齊的體驗

> [!NOTE]
> Azure Spatial Anchors 無法在 Unity 中執行。 因此，若要測試 Azure Spatial Anchors 功能，您必須將專案部署到至少兩個 HoloLens 裝置。

如果您現在建立 Unity 專案，並將其部署到 HoloLens 裝置，您就可以藉由共用 Azure 錨點識別碼，在裝置之間進行空間對齊。 若要進行測試，您可以依照下列步驟執行：

1. 在 HoloLens 裝置 1 上：**啟動應用程式** (火箭發射器已具現化並放在桌面上)
2. 在 HoloLens 裝置 2 上：**啟動應用程式** (兩位使用者都會看到具有火箭發射器的桌面，但桌面不會出現在相同的位置，而且使用者虛擬人偶不會出現在使用者的所在位置)
3. 在 HoloLens 裝置 1 上：按下 [啟動 Azure 工作階段]  按鈕
4. 在 HoloLens 裝置 1 上：按下 [建立 Azure 錨點]  按鈕 (在 TableAnchor 物件的位置上建立錨點，並將錨點資訊儲存在 Azure 資源中)。
5. 在 HoloLens 裝置 1 上：按下 [共用 Azure 錨點]  按鈕 (即時與其他使用者共用錨點識別碼)
6. 在 HoloLens 裝置 2 上：按下 [啟動 Azure 工作階段]  按鈕
7. 在 HoloLens 裝置 2 上：按下 [取得 Azure 錨點]  按鈕 (連線至 Azure 資源以抓取共用錨點識別碼的錨點資訊，然後將 TableAnchor 物件移至使用 HoloLens 裝置 1 建立錨點的位置)

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已了解如何整合 Azure 的強大 Spatial Anchors，在共用體驗中對齊裝置。 此課程也是這一系列教學課程的總結，您已在此系列中了解如何設定新的 Photon 帳戶及應用程式、將 Photon 和 PUN 整合到新的 Unity 應用程式、設定虛擬人偶和共用物件，最後使用 ASA 來調整多個參與者。
