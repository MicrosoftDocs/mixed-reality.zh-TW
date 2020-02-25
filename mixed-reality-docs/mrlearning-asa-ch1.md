---
title: Azure 空間錨點教學課程-1。 開始使用 Azure 空間錨點
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 0163b61bfbf8bd583532092581d94f63e1c2a624
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77554634"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. 開始使用 Azure 空間錨點

## <a name="overview"></a>概觀

歡迎使用第二系列的 HoloLens 2 教學課程。 在這三部分的教學課程系列中，您將瞭解 Azure 空間錨點的基本概念。

在第一個教學課程中，[開始使用 Azure 空間錨點](mrlearning-asa-ch1.md)，您將探索啟動和停止 azure 會話，以及在單一裝置上建立、上傳和下載 azure 錨點所需的各種步驟。

在第二個教學課程中，[儲存、抓取和共用 Azure 空間錨點](mrlearning-asa-ch2.md)，您將瞭解如何藉由將錨點資訊儲存至 HoloLens 2 的儲存體，來將 Azure 空間錨點儲存到多個應用程式會話，以及如何將此錨點資訊與其他裝置共用，以進行多重裝置錨定的對齊。

在第三個教學課程中，[顯示 Azure 空間錨點意見](mrlearning-asa-ch3.md)反應，您將瞭解如何在使用 Azure 空間錨點時，為使用者提供錨點事件和狀態的相關意見反應。

## <a name="objectives"></a>目標

* 瞭解使用 HoloLens 2 的 Azure 空間錨點進行開發的基本概念
* 建立、上傳及下載空間錨點

## <a name="prerequisites"></a>必要條件

>[!TIP]
>如果您尚未完成[快速入門教學](mrlearning-base.md)課程系列，建議您先完成這些教學課程。

* 已[安裝正確工具](install-the-tools.md)的 Windows 10 電腦
* Windows 10 SDK 10.0.18362.0 或更新版本
* 基本的 C# 程式設計能力
* 已[針對開發而設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，已安裝 Unity 2019.2，且已新增通用 Windows 平台組建支援模組
* 完成[快速入門：建立使用 Azure 空間錨點的 Unity HoloLens 應用程式](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)教學課程中的[建立空間錨點資源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)一節。

> [!IMPORTANT]
> 本教學課程系列的建議 Unity 版本是 Unity 2019.2. X。 這個版本能取代上述連結之必要條件中所述的任何 Unity 版本需求或建議。

## <a name="creating-the-unity-project"></a>建立 Unity 專案
<!-- TODO: Consider renaming to 'Creating and preparing the Unity scene and project'-->

在本節中，您將建立新的 Unity 專案，並準備好進行 MRTK 開發。

為此，請先遵循[初始化您的專案和第一個應用程式](mrlearning-base-ch1.md)，但不包括將[您的應用程式建立至您的裝置](mrlearning-base-ch1.md#build-your-application-to-your-device)指示，其中包括下列步驟：

1. [建立新的 Unity 專案](mrlearning-base-ch1.md#create-new-unity-project)，並為其提供適當的名稱，例如*MRTK 教學*課程。

2. [設定適用于 Windows Mixed Reality 的 Unity 專案](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [匯入 TextMesh Pro 基本資源](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [匯入 Mixed Reality 工具組](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [設定混合現實工具組的 Unity 專案](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. [將 Mixed Reality 工具組新增至 Unity 場景](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)，並為場景提供適當的名稱，例如*AzureSpatialAnchors*

然後遵循[如何設定混合現實工具組設定檔（變更空間感知顯示選項）](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)指示，將場景的 MRTK 設定檔變更為**DefaultHoloLens2ConfigurationProfile** ，並將空間感知網格的顯示選項變更為**遮蔽**。

> [!CAUTION]
> 如上述連結的[混合現實工具組指示設定 Unity 專案](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)中所述，強烈建議不要啟用適用于 Unity 的 MSBuild。

## <a name="adding-inbuilt-unity-packages"></a>新增內建 Unity 套件
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

在本節中，您將安裝 Unity 的內建 AR Foundation 套件，因為您將在下一節中匯入 Azure 空間錨點 SDK 所需。

在 Unity 功能表中，選取 [Window > **封裝管理員** **]** ：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> 這可能需要幾秒鐘的時間，AR Foundation 封裝才會出現在清單中。

在 [套件管理員] 視窗中，選取 [ **AR Foundation** ]，然後按一下 [**安裝**] 按鈕來安裝套件：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>匯入教學課程資產

依照**列出的順序**下載並匯**入**下列 Unity 自訂套件：

* [AzureSpatialAnchors. unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) （2.1.1 版）
* [MRTK.HoloLens2 GettingStarted. 2.3.0.2. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
* [MRTK.HoloLens2 AzureSpatialAnchors. 最新 2.3.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)

> [!TIP]
> 如需有關如何匯入 Unity 自訂套件的提醒，您可以參閱匯[入混合現實工具](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)組指示。

匯入教學課程資產之後，您的 [專案] 視窗看起來應該如下所示：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a>建立和準備場景
<!-- TODO: Consider renaming to 'Preparing the scene' -->

在本節中，您將藉由新增一些教學課程 prefabs 來準備場景。

在 [專案] 視窗中，流覽至 [**資產**] [ > **MRTK]。教學課程. AzureSpatialAnchors** > **Prefabs**資料夾。 按住 CTRL 鍵時，按一下 [ **ButtonParent**]、[ **DebugWindow**]、[**指示**] 和 [ **ParentAnchor** ] 以選取四個 prefabs：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

在選取四個 prefabs 的情況下，將它們拖曳到 [階層] 視窗中，以將它們新增至場景：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

若要將焦點放在場景中的物件上，您可以按兩下 [ParentAnchor] 物件，然後再稍微縮小一次：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> 比方說，如果您在場景中找到大圖示，例如，大框的 ' t ' 圖示會有干擾，您可以將<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">Gizmos 切換</a>到 off 位置來隱藏它們。

## <a name="configuring-the-buttons-to-operate-the-scene"></a>設定按鈕以操作場景

在本節中，您將在場景中新增腳本，以建立一系列的按鈕事件，以示範本機錨點和 Azure 空間錨點在應用程式中的行為。

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a>1. 設定 Pressable 按鈕 Hololens 透鏡2（腳本）元件

在 [階層] 視窗中，展開 [ **ButtonParent** ] 物件，並選取名為**StartAzureSession**的第一個子物件：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

在 [偵測器] 視窗中，找出 [ **Pressable] 按鈕 Hololens 透鏡2（腳本）** 元件，然後按一下 [ **+** ] 圖示，將新的事件接聽程式新增至**按下的按鈕（）** 事件：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

在 [階層] 視窗中仍然選取 StartAzureSession 物件時，按一下並將**ParentAnchor**物件從 [階層] 視窗拖曳至您剛才加入之事件接聽程式的 [空的**無（物件）** ] 欄位中，讓 ParentAnchor 物件可以從這個按鈕接聽按鈕已按下的事件：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

按一下同一個事件接聽程式的 [**無**函式] 下拉式清單，然後選取 [ **AnchorModuleScript** > **StartAzureSession （）** ]，將 StartAzureSession （）函數設定為從這個按鈕引發按鈕按下的事件時所觸發的動作：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a>2. 設定可互動（腳本）元件

在 [階層] 視窗中，仍然選取 StartAzureSession 物件，在 [偵測器] 視窗中，找出 [**可互動（腳本）** ] 元件，並針對**OnClick （）** 事件重複上述步驟1中的相同進程：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a>3. 設定其餘按鈕

針對其餘的每個按鈕，完成上述步驟1和2中所述的程式，將函式指派給**按下按鈕的（）** 和**OnClick （）** 事件：

* 針對**StopAzureSession**物件，指派 AnchorModuleScript > **StopAzureSession （）** 函數。
* 針對**CreateAzureAnchor**物件，指派 AnchorModuleScript > **CreateAzureAnchor （）** 函數，
  * 然後再次將**ParentAnchor**拖曳至 [空的**無（遊戲物件）** ] 欄位。
* 針對**RemoveLocalAnchor**物件，指派 AnchorModuleScript > **RemoveLocalAnchor （）** 函數，
  * 然後再次將**ParentAnchor**拖曳至 [空的**無（遊戲物件）** ] 欄位。
* 針對**FindAzureAnchor**物件，指派 AnchorModuleScript > **FindAzureAnchor （）** 函數。
* 針對**DeleteAzureAnchor**物件，指派 AnchorModuleScript > **DeleteAzureAnchor （）** 函數。

### <a name="4-connect-the-scene-to-the-azure-resource"></a>4. 將場景連線至 Azure 資源

在 [階層] 視窗中，選取 [ **ParentAnchor** ] 物件，然後在 [偵測器] 視窗中，向下流覽至 [**空間錨點管理員（腳本）** ] 元件。

然後，在 [**認證**] 區段中，將您在本教學[課程必要條件](mrlearning-asa-ch1.md#prerequisites)中建立的空間錨點帳戶識別碼和金鑰貼到對應的 [**空間錨點帳戶識別碼**] 和 [**空間錨點帳戶金鑰**] 欄位中：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>嘗試 Azure 空間錨點的基本行為

您的場景已設定為示範 Azure 空間錨點的基本概念，現在可以部署應用程式，以便體驗 Azure 空間錨點搶先它。

### <a name="1-add-additional-required-capabilities"></a>1. 新增額外的必要功能

在 Unity 功能表中，選取 **編輯** > **專案設定 ...**  以開啟 Player 設定 視窗：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

在 [Player 設定] 視窗中，依序選取 [ **player** ] 和 [**發佈設定**]：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

在 [**發行設定**] 中，向下流覽至 [**功能**] 區段，然後再次檢查您在教學課程開頭建立專案時所啟用的**InternetClient**、**麥克風**和**SpatialPerception**功能是否已啟用。 然後，啟用**InternetClientServer**、 **PrivateNetworkClientServer**、 **RemovableStorage**和**網路**攝影機功能：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2. 將應用程式部署至 HoloLens 2

Azure 空間錨點無法在 Unity 中執行，因此若要測試 Azure 空間錨點功能，您必須將專案部署至您的裝置。

> [!TIP]
> 如需有關如何建立 Unity 專案並將其部署至 HoloLens 2 的提醒，您可以參閱將[您的應用程式建立至您的裝置](mrlearning-base-ch1.md#build-your-application-to-your-device)指示。

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3. 在 HoloLens 2 上執行應用程式，並遵循應用程式內的指示

> [!CAUTION]
> Azure 空間錨點會使用網際網路來儲存和載入錨定資料，因此請確定您的裝置已連線到網際網路。

當應用程式在您的裝置上執行時，請遵循 Azure 空間錨點教學課程指示面板上顯示的螢幕指示：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a>錨定體驗

在前面幾節中，您已瞭解 Azure 空間錨點的基本概念。 我們使用 cube 來呈現父遊戲物件，並使用連結的錨點將其視覺化。 在本節中，您將瞭解如何藉由將它放在 ParentAnchor 物件的子系，來錨定整個體驗。

### <a name="1-add-the-rocket-launcher-experience"></a>1. 新增 Rocket 啟動器體驗

在 [專案] 視窗中，流覽至 [**資產**] > **MRTK。教學課程. GettingStarted** > **Prefabs** > **RocketLauncher**資料夾，然後選取**RocketLauncher_Complete** prefab：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

在仍選取 [RocketLauncher_Complete prefab] 的情況下，將其拖曳至 [階層] 視窗中的 [ **ParentAnchor** ] 物件上方，使其成為 ParentAnchor 物件的子系：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a>2. 重新置放 Rocket 啟動器體驗

將**RocketLauncher_Complete**物件定位、旋轉和縮放至適當的縮放和方向，同時確保**ParentAnchor**物件仍會公開，例如：

* 轉換**位置**X = 0、Y = 0、Z = 3.75
* 轉換**旋轉**X = 0、Y = 90、Z = 0
* 轉換**小數值**X = 10，Y = 10，Z = 10

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

在應用程式中，使用者現在可以藉由移動 cube 來重新放置整個 Rocket 啟動器的使用體驗。

> [!TIP]
> 有各種不同的使用者體驗流程可進行重新置放的體驗，包括使用重新置放的物件（例如本教學課程中使用的 cube）、使用按鈕來切換環繞體驗的周框方塊、使用位置和旋轉gizmos，還有更多。

## <a name="congratulations"></a>恭喜

在本教學課程中，您已瞭解 Azure 空間錨點的基本概念。 本教學課程提供您幾個按鈕，可讓您探索啟動和停止 Azure 空間錨點會話，以及在單一裝置上建立、上傳和下載 Azure 空間錨點所需的各種步驟。

在下一課中，您將瞭解如何將 Azure 錨點識別碼儲存至 HoloLens 2 進行抓取，即使在重新開機應用程式之後，以及如何在多個裝置之間傳輸錨點識別碼以達成空間對齊。

[下一課： 2. 儲存、正在抓取和共用 Azure 空間錨點](mrlearning-asa-ch2.md)
