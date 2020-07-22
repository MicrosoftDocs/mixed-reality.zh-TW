---
title: Azure 雲端教學課程 - 1. 適用於 HoloLens 2 的 Azure 雲端服務
description: 完成此課程，以了解如何在 HoloLens 2 應用程式中執行各種 Azure 服務。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: azure, 混合實境, unity, 教學課程, hololens, hololens 2, azure blob 儲存體, azure 表格儲存體，azure spatial anchors, azure bot framework
ms.localizationpriority: high
ms.openlocfilehash: 649046f9416c880d6e69b544866fba60d3e43f4c
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304451"
---
# <a name="1-azure-cloud-services-for-hololens-2"></a>1.適用於 HoloLens 2 的 Azure 雲端服務

## <a name="overview"></a>概觀

歡迎參與這系列的教學課程，本系列課程內容著重於將 **Azure 雲端**服務帶入 **HoloLens 2** 應用程式中。 在此五部分的教學課程系列中，您將了解如何將數個 **Azure 雲端**服務整合至 **HoloLens 2** 的 **Unity** 專案中。 在每個連續章節中，您將新增新的 **Azure 雲端**服務以擴充應用程式功能和使用者體驗，同時了解每個 **Azure 雲端**服務的基本概念。

> [!NOTE]
> 本教學課程系列著重於 **HoloLens 2**，但由於 Unity 的跨平台性質，您的學習內容也適用於桌面和智慧型手機應用程式。

在第一個教學課程中，會[介紹適用於 HoloLens 2 的 Azure 雲端服務](mr-learning-azure-01.md)，一開始會先說明應用程式的目標，並簡單介紹每個 Azure 雲端服務，並設定 Unity 專案。

在第二個教學課程[整合 Azure 儲存體](mr-learning-azure-02.md)中，您會將 Azure 儲存體整合為示範應用程式的持續性解決方案，學習 Blob 儲存體和表格儲存體之間的差異、準備所需的專案資源、設定場景以及確認讀取、更新和刪除資料等作業。

繼續進行第三個教學課程，[整合 Azure 自訂視覺](mr-learning-azure-03.md)，您將使用 Azure 自訂視覺來定型和偵測 HoloLens 2 應用程式中的影像。 本章一開始會先設定您自己的 Azure 自訂視覺資源、準備場景元件，並從應用程式內部定型和偵測您自己的影像開始。

接下來，您會前進到第四個教學課程[整合 Azure Spatial Anchors](mr-learning-azure-04.md)，並探索 Azure Spatial Anchors 服務來儲存和尋找位置、了解核心概念、準備必要資源、設定場景，以及開始使用應用程式中的新功能。

在第五個教學課程[將 Azure Bot 服務與 LUIS 整合](mr-learning-azure-05.md)中，您可以為應用程式提供新的使用者互動方法，也就是自然語言！ 這項功能會透過搭配 Language Understanding (LUIS) 使用 Azure Bot Framework 來實現。 最後一章會教您 Azure Bot 服務的基本概念，並加速您使用 Bot Framework 編輯器作為零程式碼解決方案的程序。 建立 Bot 之後，您會將其整合到場景中，並執行 HoloLens 2 應用程式的最後階段。

## <a name="application-goals"></a>應用程式目標

在此教學課程系列中，您將建置一個 **HoloLens 2** 應用程式，以偵測影像中的物件並尋找其空間位置。 若要設定網域語言，您可以從現有的**追蹤物件**呼叫這類實體。
使用者可以建立**追蹤物件**，透過電腦視覺和 (或) 空間位置將其中一組或二組影像加以關聯。 所有資料都必須保存到雲端。 此外，應用程式的某些層面會選擇性地透過 Bot 以自然語言來控制。

### <a name="features"></a>功能

* 資料和影像的基本管理
* 影像訓練和偵測
* 儲存空間位置和操作方式指南
* 透過自然語言使用部分功能的 Bot 輔助程式

## <a name="azure-cloud-services"></a>Azure 雲端服務

若要解決應用程式所需的功能，您將使用這些 **Azure 雲端**服務：

### <a name="azure-storage"></a>Azure 儲存體

您會使用 [Azure 儲存體](https://azure.microsoft.com/services/storage/)作為持續性解決方案。 如可讓您將資料儲存在表格中，並上傳例如影像等的大型二進位檔案。

### <a name="azure-custom-vision"></a>Azure 自訂視覺

有了 [Azure 自訂視覺](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) ([Azure 認知服務](https://azure.microsoft.com/services/cognitive-services/)的一部分)，您可以建立一組影像與「追蹤物件」的關聯、將機器學習模型定型，並偵測「追蹤物件」。

### <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

若要儲存「追蹤物件」位置，並提供引導式指示以方便尋找，您可以使用 [Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/)。

### <a name="azure-bot-service"></a>Azure Bot Service

應用程式主要是由傳統的 UI 驅動，因此您可以使用 [Azure Bot 服務](https://azure.microsoft.com/services/bot-service/)新增一些特性，並作為新的互動方法。

## <a name="prerequisites"></a>必要條件

>[!TIP]
>如果您尚未完成[入門教學課程](mr-learning-base-01.md)系列，建議您先完成這些教學課程。

* 已[安裝正確工具](install-the-tools.md)的 Windows 10 電腦
* Windows 10 SDK 10.0.18362.0 或更新版本
* 基本的 C# 程式設計能力
* 已[針對開發而設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置
* 連線的網路攝影機 (如果想要從 Unity 編輯器進行測試)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，已安裝 Unity 2019.3.X，且已新增通用 Windows 平台組建支援模組

> [!CAUTION]
> 本教學課程系列的建議 Unity 版本是 Unity 2019.3.X。 這個版本能取代上述連結之必要條件中所述的任何 Unity 版本需求或建議。

## <a name="creating-and-preparing-the-unity-project"></a>建立和準備 Unity 專案

在本節中，您將建立新的 Unity 專案，並使該專案準備好進行 MRTK 開發。

為此，請先遵循[初始化您的專案和第一個應用程式](mr-learning-base-02.md) (但不包括[對您的裝置建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示)，其中包括下列步驟：

1. [建立 Unity 專案](mr-learning-base-02.md#creating-the-unity-project)，並為其提供適當的名稱，例如「Azure 雲端教學課程」
2. [切換建置平台](mr-learning-base-02.md#configuring-the-unity-project)
3. [匯入 TextMeshPro 基本資源](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [匯入混合實境工具組](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [設定 Unity 專案](mr-learning-base-02.md#configuring-the-unity-project)
6. [建立和設定場景](mr-learning-base-02.md#creating-and-configuring-the-scene)並為場景提供適當的名稱，例如 AzureCloudServices

然後遵循[變更空間感知顯示選項](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)的指示，將場景的 MRTK 組態設定檔變更為 **DefaultHoloLens2ConfigurationProfile**，並將空間感知網格的顯示選項變更為 [遮蔽]。

## <a name="installing-inbuilt-unity-packages"></a>安裝內建的 Unity 套件

在 Unity 功能表中，選取 視窗 >  **套件管理員** 以開啟 套件管理員 視窗，然後選取 AR 基本概念，並按一下 安裝 按鈕以安裝套件：

![mr-learning-azure](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> 您正在安裝 AR Foundation 套件，因為 Azure Spatial Anchors SDK 需要此套件，您將在下一節中匯入。

## <a name="importing-the-tutorial-assets"></a>匯入教學課程資產

下載並**依列出順序**來**匯入**下列 Unity 自訂套件：

* [適用於 Unity 的 Azure 儲存體](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/AzureStorageForUnity.unitypackage)
* [Azure Spatial Anchors](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage)
* [MRTK.Tutorials.AzureCloudServices](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/MRTK.Tutorials.AzureCloudServices.unitypackage)

> [!TIP]
> 如需有關如何匯入 Unity 自訂套件的提示，您可以參閱[匯入混合實境工具組](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) 的指示。

匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：

![mr-learning-azure](images/mr-learning-azure/tutorial1-section4-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a>建立和準備場景
<!-- TODO: Consider renaming to 'Preparing the scene' -->

在本節中，您將藉由新增一些教學課程 Prefab 來準備場景。

在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.AzureCloudServices] > [預製物件] > [管理員] 資料夾。 按住 CTRL 鍵時，按一下 [SceneController]、**RootMenu** 和 **DataManager**以選取三個預製物件：

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-1.png)

**SceneController (預製物件)** 包含兩個指令碼，也就是**SceneController (指令碼)** 和 **UnityDispatcher (指令碼)** 。 **SceneController** 指令碼元件包含數個 UX 函式，並可協助相片擷取功能，而 **UnityDispatcher** 是允許 Unity 主執行緒執行動作的協助程式類別。

**RootMenu (預製物件)** 是主要的 UI 預製物件，其中包含透過各種小型指令碼元件彼此連繫的所有 UI 視窗，並會控制應用程式的一般 UX 流程。

**DataManager (預製物件)** 負責與 Azure 儲存體溝通，我們會在下一個教學課程中進一步說明。

選取三個預製物件之後，將其拖曳到階層視窗中，即可新增至場景：

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-2.png)

若要將焦點放在場景中的物件上，您可以按兩下 **RootMenu** 物件，然後再次將場景稍微縮小：

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-3.png)

> [!TIP]
> 如果您發現場景中的大圖示 (例如大型邊框的 'T' 圖示) 會造成干擾，您可以藉由將 <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">Gizmo 切換</a>到關閉位置來將其隱藏。

## <a name="configuring-the-scene"></a>設定場景

在本節中，您會將 SceneManager、DataManager 和 RootMenu 連接在一起，讓適用於下列[整合 Azure 儲存體](mr-learning-azure-01.md)教學課程的工作場景準備就緒。

### <a name="connect-the-objects"></a>連接物件

在階層視窗中，選取 [DataManager] 物件：

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-1.png)

在偵測器視窗中，找出 **DataManager (指令碼)** 元件，接著您會在 **On Data Manager Ready ()** 事件的上看到空位。 現在，從階層視窗將 **SceneController** 物件拖曳到 **On Data Manager Ready ()** 事件中。

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-2.png)

您會注意到事件的下拉式功能表已變成作用中，請按一下下拉式功能表並瀏覽至 **SceneController**，然後在子功能表中選取 **Init ()** 選項：

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-3.png)

從階層視窗中，選取 **SceneController** 物件，您會在該處的偵測器中找到 **SceneController** (指令碼) 元件。

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-4.png)

您會看到有數個未填入的欄位等待您填入資訊。 將階層中的 **DataManager** 物件移至「資料管理員」欄位，並將階層中的 **RootMenu** GameObject 移至「主功能表」欄位。

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-5.png)

現在您的場景已準備就緒，可供未來的教學課程使用。 別忘了儲存到您的專案中。

## <a name="prepare-project-build-pipeline"></a>準備專案建置管線

雖然專案還必須填入內容，但您必須執行一些準備工作，讓專案準備好建置 **HoloLens 2**。

### <a name="1-add-additional-required-capabilities"></a>1.新增額外的必要功能

在 Unity 功能表中，選取 [編輯] >  [專案設定...] 來開啟 [專案設定] 視窗：

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-1.png)

在專案設定視窗中選取 [玩家]，然後選取 [發佈設定]：

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-2.png)

在 [發佈設定] 中，向下捲動至 [功能] 區段，然後再次確認您在教學課程開頭建立專案時所啟用的 **InternetClient**、**Microphone** 和 **SpatialPerception** 功能是否皆已啟用。 然後，啟用 **InternetClientServer**、**PrivateNetworkClientServer** 和 **Webcam** 功能：

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2.將應用程式部署至 HoloLens 2

您將在此教學課程系列中使用的所有功能並非都可以在 Unity 編輯器中執行，這表示您必須熟悉如何將應用程式部署至 HoloLens 2 裝置。

> [!TIP]
> 如需有關如何建立 Unity 專案並將其部署至 HoloLens 2 的提示，您可以參閱[入門教學課程 - 對您的裝置建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示。

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3.在 HoloLens 2 上執行應用程式，並遵循應用程式內的指示

> [!CAUTION]
> 所有 Azure 服務都會使用網際網路，因此請確定您的裝置已連線到網際網路。

當應用程式在您的裝置上執行時，請接受下列所要求功能的存取權：

* 麥克風
* 相機

這類服務需要像是「聊天機器人」和「自訂視覺」才能正常運作。

## <a name="congratulations"></a>恭喜！

在本教學課程中，我們介紹了教學課程系列，您也了解各項即將實作的功能，以及如何繫結 **Azure 雲端**，進而實現您的 *HoloLens 2* 應用程式。 您已將必要的元件新增至專案，並備妥此教學課程系列的場景。

在下一課中，您將使用 Azure 儲存體作為雲端式持續性解決方案，以儲存資料和影像。

[下一個教學課程：2.整合 Azure 儲存體](mr-learning-azure-02.md)
