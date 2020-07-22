---
title: Azure Spatial Anchor 教學課程 - 2。 開始使用 Azure Spatial Anchors
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure Spatial Anchors。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: a24b6b03ce75a57db49b3d0c875d123ea87c8162
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304534"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a>2.開始使用 Azure Spatial Anchors

## <a name="overview"></a>概觀

在此教學課程中，您將探索啟動和停止 Azure Spatial Anchors 工作階段，以及在單一裝置上建立、上傳和下載 Azure Spatial Anchors 所需的各種步驟。

## <a name="objectives"></a>目標

* 了解 HoloLens 2 的 Azure Spatial Anchors 開發基本概念
* 了解如何建立空間錨點，並從 Azure 提取這些錨點

## <a name="creating-and-preparing-the-unity-project"></a>建立和準備 Unity 專案

在本節中，您將建立新的 Unity 專案，並使該專案準備好進行 MRTK 開發。

為此，請先遵循[初始化您的專案和部署第一個應用程式](mr-learning-base-02.md) (但不包括[對您的裝置建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示)，其中包括下列步驟：

1. [建立 Unity 專案](mr-learning-base-02.md#creating-the-unity-project)，並為其提供適當的名稱，例如「MRTK 教學課程」
1. [切換建置平台](mr-learning-base-02.md#configuring-the-unity-project)
1. [匯入 TextMeshPro 基本資源](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
1. [匯入混合實境工具組](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
1. [設定 Unity 專案](mr-learning-base-02.md#configuring-the-unity-project)
1. [建立和設定場景](mr-learning-base-02.md#creating-and-configuring-the-scene)並為場景提供適當的名稱，例如 AzureSpatialAnchors

然後遵循[變更空間感知顯示選項](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)的指示，以執行下列動作：

1. 將 **MRTK 設定檔**變更為 **DefaultHoloLens2ConfigurationProfile**
1. 將**空間感知網格顯示選項**變更為**遮蔽**。

## <a name="installing-inbuilt-unity-packages"></a>安裝內建的 Unity 套件

在 Unity 功能表中，選取 [視窗] >  **[套件管理員]** 以開啟 [套件管理員] 視窗，然後選取 [AR 基本概念]，並按一下 [安裝] 按鈕以安裝套件：

![mr-learning-asa](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> 您正在安裝 AR Foundation 套件，因為 Azure Spatial Anchors SDK 需要此套件，您將在下一節中匯入。

## <a name="importing-the-tutorial-assets"></a>匯入教學課程資產

下載並**依列出順序**來**匯入**下列 Unity 自訂套件：

* [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (2.2.1 版)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)

匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：

![mr-learning-asa](images/mr-learning-asa/asa-02-section3-step1-1.png)

> [!TIP]
> 如需有關如何匯入 Unity 自訂套件的提示，您可以參閱[匯入混合實境工具組](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) 的指示。

## <a name="preparing-the-scene"></a>準備場景

在本節中，您將藉由新增一些教學課程 Prefab 來準備場景。

在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.AzureSpatialAnchors] > [Prefabs] 資料夾，然後按一下下列 Prefab 並將其拖曳至 [階層] 視窗中，將其新增到您的場景中：

* **ButtonParent** Prefab
* **DebugWindow** Prefab
* **Instructions** Prefab
* **ParentAnchor** Prefab

![mr-learning-asa](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> 如果您發現場景中的大圖示 (例如大型邊框的 'T' 圖示) 會造成干擾，您可以藉由將 <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">Gizmo 切換</a>到關閉位置來將其隱藏，如上圖所示。

## <a name="configuring-the-buttons-to-operate-the-scene"></a>設定按鈕以操作場景

在本節中，您將在場景中新增指令碼來建立一系列的按鈕事件，以示範本機錨點和 Azure Spatial Anchors 在應用程式中的行為基礎。

在 [階層] 視窗中，展開 **ButtonParent** 物件，並選取名為 **StartAzureSession** 的第一個子物件，然後在 [偵測器] 視窗中，設定 **Button Config Helper (指令碼)** 元件的 **On Click ()** 事件，如下所示：

* 將 **ParentAnchor** 物件指派給 [無 (物件)] 欄位
* 從 [沒有函式] 下拉式清單中，選取 [AnchorModuleScript] > [StartAzureSession ()]，以將此函式設定為觸發事件時所要執行的動作

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-1.png)

在 [階層] 視窗中，選取名為 **StopAzureSession** 的下一個按鈕，然後在 [偵測器] 視窗中，設定 **Button Config Helper (指令碼)** 元件的 **On Click ()** 事件，如下所示：

* 將 **ParentAnchor** 物件指派給 [無 (物件)] 欄位
* 從 [沒有函式] 下拉式清單中，選取 [AnchorModuleScript] > [StopAzureSession ()]，以將此函式設定為觸發事件時所要執行的動作

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-2.png)

在 [階層] 視窗中，選取名為 **CreateAzureAnchor** 的下一個按鈕，然後在 [偵測器] 視窗中，設定 **Button Config Helper (指令碼)** 元件的 **On Click ()** 事件，如下所示：

* 將 **ParentAnchor** 物件指派給 [無 (物件)] 欄位
* 從 [沒有函式] 下拉式清單中，選取 [AnchorModuleScript] > [CreateAzureAnchor ()]，以將此函式設定為觸發事件時所要執行的動作
* 將 **ParentAnchor** 物件指派給空的 [無 (遊戲物件)] 欄位，使其成為 CreateAzureAnchor () 函式的引數

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-3.png)

在 [階層] 視窗中，選取名為 **RemoveLocalAnchor** 的下一個按鈕，然後在 [偵測器] 視窗中，設定 **Button Config Helper (指令碼)** 元件的 **On Click ()** 事件，如下所示：

* 將 **ParentAnchor** 物件指派給 [無 (物件)] 欄位
* 從 [沒有函式] 下拉式清單中，選取 [AnchorModuleScript] > [RemoveLocalAnchor ()]，以將此函式設定為觸發事件時所要執行的動作
* 將 **ParentAnchor** 物件指派給空的 [無 (遊戲物件)] 欄位，使其成為 RemoveLocalAnchor () 函式的引數

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-4.png)

在 [階層] 視窗中，選取名為 **FindAzureAnchor** 的下一個按鈕，然後在 [偵測器] 視窗中，設定 **Button Config Helper (指令碼)** 元件的 **On Click ()** 事件，如下所示：

* 將 **ParentAnchor** 物件指派給 [無 (物件)] 欄位
* 從 [沒有函式] 下拉式清單中，選取 [AnchorModuleScript] > [FindAzureAnchor ()]，以將此函式設定為觸發事件時所要執行的動作

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-5.png)

在 [階層] 視窗中，選取名為 **DeleteAzureAnchor** 的下一個按鈕，然後在 [偵測器] 視窗中，設定 **Button Config Helper (指令碼)** 元件的 **On Click ()** 事件，如下所示：

* 將 **ParentAnchor** 物件指派給 [無 (物件)] 欄位
* 從 [沒有函式] 下拉式清單中，選取 [AnchorModuleScript] > [DeleteAzureAnchor ()]，以將此函式設定為觸發事件時所要執行的動作

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a>將場景連線至 Azure 資源

在 [階層] 視窗中，選取 **ParentAnchor** 物件，然後在 [偵測器] 視窗中尋找 **Spatial Anchor Manager (指令碼)** 元件。 使用 Azure Spatial Anchors 帳戶中的認證來設定 [認證] 區段，該帳戶會在本教學課程系列的[必要條件](mr-learning-asa-01.md#prerequisites)中建立：

* 在 [Spatial Anchors Account 識別碼] 欄位中，貼上 Azure Spatial Anchors 帳戶中的**帳戶識別碼**
* 在 [Spatial Anchors 帳戶金鑰] 欄位中，貼上 Azure Spatial Anchors 帳戶中的主要或次要**存取金鑰**

![mr-learning-asa](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>嘗試 Azure Spatial Anchors 的基本行為

Azure Spatial Anchors 無法在 Unity 中執行，因此若要測試 Azure Spatial Anchors 功能，您必須在裝置中建置專案並部署應用程式。

> [!TIP]
> 如需有關如何建立 Unity 專案並將其部署至 HoloLens 2 的提醒，您可以參閱[對您的 HoloLens 2 建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示。

當應用程式在您的裝置上執行時，請遵循 Azure Spatial Anchor 教學課程指示面板上顯示的螢幕指示：

1. 將立方體移至不同的位置
1. 啟動 Azure 工作階段
1. 建立 Azure 錨點 (在立方體的位置上建立錨點)。
1. 停止 Azure 工作階段
1. 移除區域錨點 (允許使用者移動立方體)
1. 將立方體移至其他地方
1. 啟動 Azure 工作階段
1. 尋找 Azure 錨點 (將立方體置於步驟 3 的位置)
1. 刪除 Azure 錨點
1. 停止 Azure 工作階段

![mr-learning-asa](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> Azure Spatial Anchors 會使用網際網路來儲存和載入錨點資料，因此請確定您的裝置已連線到網際網路。

## <a name="anchoring-an-experience"></a>錨點體驗

在前面幾節中，您已了解 Azure Spatial Anchors 的基本概念。 我們使用了立方體和連結的錨點來呈現及視覺化父遊戲物件。 在本節中，您將了解如何藉由將整個體驗放在 ParentAnchor 物件的子系，來為其建立錨點。

在 [階層] 視窗中，選取 **ParentAnchor** 物件，然後在 [偵測器] 視窗中設定**變形**元件，如下所示：

* 將 [X 軸縮放] 變更為 1.1
* 將 [Z 軸縮放] 變更為 1.1

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-1.png)

在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.GettingStarted] > [Prefabs] > [Rover] 資料夾，然後按一下 **RoverExplorer_Complete** Prefab，並將其拖曳至 [階層] 視窗中來新增到您的場景中：

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-2.png)

在 [階層] 視窗中，繼續選取新增的 RoverModule_Complete 物件，並將其拖曳至 **ParentAnchor** 物件，使其成為 ParentAnchor 物件的子系：

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-3.png)

如果您現在重建專案，並將應用程式部署到您的裝置，您現在就可以藉由移動已調整大小的立方體來重新放置整個 Rover Explorer 體驗。

> [!TIP]
> 有各種不同的使用者體驗流程可用於重新置放體驗，包括使用重新置放物件 (例如本教學課程中使用的立方體)、使用按鈕來切換環繞體驗的周框方塊、使用位置和旋轉 gizmo 等等。

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已了解 Azure Spatial Anchors 的基本概念。 本教學課程提供了您幾個按鈕，讓您探索啟動和停止 Azure Spatial Anchors 工作階段所需的各種步驟。 此外，也可以在單一裝置上建立、上傳和下載 Azure Spatial Anchors。

在下一個教學課程中，您將了解如何將 Azure 錨點識別碼儲存至 HoloLens 2 以便擷取 (即使在重新啟動應用程式之後)，以及如何在多個裝置之間傳輸錨點識別碼以達到空間對齊。

[下一個教學課程：3.儲存、擷取和共用 Azure Spatial Anchors](mr-learning-asa-03.md)
