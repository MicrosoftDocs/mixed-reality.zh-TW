---
title: Azure Spatial Anchor 教學課程 - 1。 開始使用 Azure Spatial Anchors
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 2a171d601d094375a56734e8d7890c9d3e17c887
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83866908"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1.開始使用 Azure Spatial Anchors

## <a name="overview"></a>概觀

歡迎使用第二個系列的 HoloLens 2 教學課程。 在此四個部分的教學課程系列中，您將了解 Azure Spatial Anchors 的基本概念。

在第一個教學課程：[開始使用 Azure Spatial Anchors](mrlearning-asa-ch1.md) 中，您將探索啟動和停止 Azure 工作階段，以及在單一裝置上建立、上傳和下載 Azure 錨點所需的各種步驟。

在第二個教學課程：[儲存、擷取和共用 Azure Spatial Anchors](mrlearning-asa-ch2.md) 中，您將了解如何藉由將錨點資訊儲存至 HoloLens 2 的儲存體，來將 Azure Spatial Anchors 儲存到多個應用程式工作階段，以及如何將此錨點資訊與其他裝置共用，使多個裝置的錨點一致。

在第三個教學課程：[顯示 Azure Spatial Anchor 回饋](mrlearning-asa-ch3.md)中，您將了解如何在使用 Azure Spatial Anchors 時，向使用者提供錨點事件和狀態的意見反應。

在第四個教學課程中，[適用於 Android 和 iOS 的 Azure Spatial Anchors](mrlearning-asa-ch4.md)，您將了解如何建置專案並將其部署至 Android 和 iOS 裝置。

## <a name="objectives"></a>目標

* 了解 HoloLens 2 的 Azure Spatial Anchors 開發基本概念
* 建立、上傳及下載空間錨點

## <a name="prerequisites"></a>必要條件

>[!TIP]
>如果您尚未完成[入門教學課程](mrlearning-base.md)系列，建議您先完成這些教學課程。

* 已[安裝正確工具](install-the-tools.md)的 Windows 10 電腦
* Windows 10 SDK 10.0.18362.0 或更新版本
* 基本的 C# 程式設計能力
* 已[針對開發而設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，已安裝 Unity 2019.2，且已新增通用 Windows 平台組建支援模組
* 完成[建立空間錨點資源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)區段，其位於[教學課程：建立使用 Azure Spatial Anchors 的 Unity HoloLens 應用程式](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)。
* 如果想要部署至 Android
    * 已啟用<a href="https://developer.android.com/studio/debug/dev-options" target="_blank">開發人員</a>和具有 <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore 功能</a>的 Android 裝置，可透過 USB 連接至您的 Windows 或 macOS 電腦
    * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，已安裝 Unity 2019.2.X，且已新增 Android 組建支援模組
* 如果想要部署至 iOS
    * 已安裝最新版 <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> 和 <a href="https://cocoapods.org" target="_blank">CocoaPods</a> 的 macOS 電腦
    * <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit 相容</a>的 iOS 裝置可透過 USB 連接至您的 macOS 電腦
    * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，已安裝 Unity 2019.2.X，且已新增 iOS 組建支援模組

> [!IMPORTANT]
> 本教學課程系列的建議 Unity 版本是 Unity 2019.2. X。 這個版本能取代上述連結之必要條件中所述的任何 Unity 版本需求或建議。

## <a name="creating-the-unity-project"></a>建立 Unity 專案
<!-- TODO: Consider renaming to 'Creating and preparing the Unity project'-->

在本節中，您將建立新的 Unity 專案，並使該專案準備好進行 MRTK 開發。

為此，請先遵循[初始化您的專案和第一個應用程式](mrlearning-base-ch1.md) (但不包括[對您的裝置建置應用程式](mrlearning-base-ch1.md#build-your-application-to-your-device)的指示)，其中包括下列步驟：

1. [建立新的 Unity 專案](mrlearning-base-ch1.md#create-new-unity-project)，並為其提供適當的名稱，例如「MRTK 教學課程」

2. [設定適用於 Windows Mixed Reality 的 Unity 專案](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [匯入 TextMesh Pro 基本資源](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [匯入混合實境工具組](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [設定用於混合實境工具組的 Unity 專案](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. [將 Mixed Reality 工具組新增至 Unity 場景](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)並為場景提供適當的名稱，例如 AzureSpatialAnchors

然後遵循[如何設定混合實境工具組設定檔 (變更空間感知顯示選項)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) 的指示，將場景的 MRTK 組態設定檔變更為 **DefaultHoloLens2ConfigurationProfile**，並將空間感知網格的顯示選項變更為 [遮蔽]。

> [!CAUTION]
> 如上方連結：[設定用於混合實境工具組的 Unity 專案](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)中所述的指示，強烈建議您不要為 Unity 啟用 MSBuild。

## <a name="adding-inbuilt-unity-packages"></a>新增內建的 Unity 套件
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

在本節中，您將安裝 Unity 的內建 AR Foundation 套件，因為您在下一節匯入 Azure Spatial Anchors SDK 時會需要此套件。

在 Unity 功能表中，選取 [視窗] >  **[套件管理員]** ：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> 可能需要幾秒鐘的時間，AR Foundation 套件才會出現在清單中。

在 [套件管理員] 視窗中選取 [AR Foundation]，然後按一下 [安裝] 按鈕來安裝套件：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>匯入教學課程資產

下載並**依列出順序**來**匯入**下列 Unity 自訂套件：

* [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (2.1.1 版)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)

> [!TIP]
> 如需有關如何匯入 Unity 自訂套件的提示，您可以參閱[匯入混合實境工具組](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) 的指示。

匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a>建立和準備場景
<!-- TODO: Consider renaming to 'Preparing the scene' -->

在本節中，您將藉由新增一些教學課程 Prefab 來準備場景。

在 [專案] 視窗中，瀏覽至 [資產] > [MRTK.Tutorials.AzureSpatialAnchors] > [Prefab] 資料夾。 按住 CTRL 鍵並按一下 [ButtonParent]、[DebugWindow]、[Instructions] 和 [ParentAnchor] 以選取四個 Prefab：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

選取四個 Prefab 之後，將其拖曳到 [階層] 視窗中，即可新增至場景：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

若要將焦點放在場景中的物件上，您可以按兩下 ParentAnchor 物件，然後再次將場景稍微縮小：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> 如果您發現場景中的大圖示 (例如大型邊框的 'T' 圖示) 會造成干擾，您可以藉由將 <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">Gizmo 切換</a>到關閉位置來將其隱藏。

## <a name="configuring-the-buttons-to-operate-the-scene"></a>設定按鈕以操作場景

在本節中，您將在場景中新增指令碼來建立一系列的按鈕事件，以示範本機錨點和 Azure Spatial Anchors 在應用程式中的行為基礎。

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a>1.設定 Pressable Button Holo Lens 2 (指令碼) 元件

在 [階層] 視窗中，展開 **ButtonParent** 物件，然後選取名為 **StartAzureSession**的第一個子物件：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

在 [偵測器] 視窗中，找出 **Pressable Button Holo Lens 2 (指令碼)** 元件，然後按一下 [+] 圖示，將新的事件接聽程式新增至 **Button Pressed ()** 事件：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

在 [階層] 視窗中仍選取 StartAzureSession 物件的情況下，按一下 **ParentAnchor** 物件並將其從 [階層] 視窗拖曳至您剛才所新增事件接聽程式的空白 [無 (物件)] 欄位，讓 ParentAnchor 物件可以從此按鈕接聽按下按鈕的事件：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

按一下相同事件接聽程式的 [無函式] 下拉式清單，然後選取 [AnchorModuleScript] > [StartAzureSession ()]，將 StartAzureSession () 函式設定為從此按鈕引發「按下按鈕」事件時所觸發的動作：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a>2.設定 Interactable (指令碼) 元件

在 [階層] 視窗中仍然選取 StartAzureSession 物件的情況下，在 [偵測器] 視窗中找出 **Interactable (指令碼)** 元件，並針對 **OnClick ()** 事件重複上述步驟 1 中的相同程序：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a>3.設定其餘按鈕

針對其餘的每個按鈕，完成上述步驟 1 和 2 中所述的程序，將函式指派給 **Button Pressed ()** 和 **OnClick ()** 事件：

* 針對 **StopAzureSession** 物件，請指派 AnchorModuleScript > **StopAzureSession ()** 函式。
* 針對 **CreateAzureAnchor** 物件，請指派 AnchorModuleScript > **CreateAzureAnchor ()** 函式，
  * 然後將 **ParentAnchor** 再次拖曳到空白的 [無 (遊戲)] 欄位中。
* 針對 **RemoveLocalAnchor** 物件，請指派 AnchorModuleScript > **RemoveLocalAnchor ()** 函式，
  * 然後將 **ParentAnchor** 再次拖曳到空白的 [無 (遊戲)] 欄位中。
* 針對 **FindAzureAnchor** 物件，請指派 AnchorModuleScript > **FindAzureAnchor ()** 函式。
* 針對 **DeleteAzureAnchor** 物件，請指派 AnchorModuleScript > **DeleteAzureAnchor ()** 函式。

### <a name="4-connect-the-scene-to-the-azure-resource"></a>4.將場景連線至 Azure 資源

在 [階層] 視窗中，選取 **ParentAnchor** 物件，然後在 [偵測器] 視窗中，向下瀏覽至 **Spatial Anchor Manager (指令碼)** 元件。

然後，在 [認證] 區段中，將您在本教學課程[必要條件](mrlearning-asa-ch1.md#prerequisites)中所建立的 Spatial Anchors 帳戶識別碼和金鑰，貼入對應的 [Spatial Anchors 帳戶識別碼] 和 [Spatial Anchors 帳戶金鑰] 欄位：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>嘗試 Azure Spatial Anchors 的基本行為

現在，您的場景已設定為示範 Azure Spatial Anchors 的基本概念，您可以開始部署應用程式來搶先體驗 firsthand。

### <a name="1-add-additional-required-capabilities"></a>1.新增額外的必要功能

在 Unity 功能表中，選取 [編輯] > [專案設定...] 來開啟 [玩家設定] 視窗：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

在 [玩家設定] 視窗中選取 [玩家]，然後選取 [發佈設定]：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

在 [發佈設定] 中，向下捲動至 [功能] 區段，然後再次確認您在教學課程開頭建立專案時所啟用的 **InternetClient**、**Microphone** 和 **SpatialPerception** 功能是否皆已啟用。 然後，啟用 **InternetClientServer**、**PrivateNetworkClientServer**、**RemovableStorage**和 **Webcam** 功能：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2.將應用程式部署至 HoloLens 2

Azure Spatial Anchors 無法在 Unity 中執行，因此若要測試 Azure Spatial Anchors 功能，您必須將專案部署至您的裝置。

> [!TIP]
> 如需有關如何建立 Unity 專案並將其部署至 HoloLens 2 的提示，您可以參閱[對您的裝置建置應用程式](mrlearning-base-ch1.md#build-your-application-to-your-device)的指示。

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3.在 HoloLens 2 上執行應用程式，並遵循應用程式內的指示

> [!CAUTION]
> Azure Spatial Anchors 會使用網際網路來儲存和載入錨點資料，因此請確定您的裝置已連線到網際網路。

當應用程式在您的裝置上執行時，請遵循 Azure Spatial Anchor 教學課程指示面板上顯示的螢幕指示：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a>錨點體驗

在前面幾節中，您已了解 Azure Spatial Anchors 的基本概念。 我們使用了立方體和連結的錨點來呈現及視覺化父遊戲物件。 在本節中，您將了解如何藉由將整個體驗放在 ParentAnchor 物件的子系，來為其建立錨點。

### <a name="1-add-the-rocket-launcher-experience"></a>1.新增火箭發射器的體驗

在 [專案] 視窗中，流覽至 [資產] > [MRTK.Tutorials.GettingStarted] > [Prefabs] > [RocketLauncher] 資料夾，並選取 **RocketLauncher_Complete** Prefab：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

在仍選取 RocketLauncher_Complete Prefab 的情況下，將其拖曳至 [階層] 視窗中 **ParentAnchor** 物件的上方，使其成為 ParentAnchor 物件的子系：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a>2.重新放置火箭發射器的體驗

將 **RocketLauncher_Complete** 物件的位置、旋轉和規模調整為適當的規模和方向，同時確保 **ParentAnchor** 物件仍為公開狀態，例如：

* 變形**位置** X = 0、Y = 0、Z = 3.75
* 變形**旋轉** X = 0、Y = 90、Z = 0
* 變形**縮放** X = 10、Y = 10、Z = 10

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

在應用程式中，使用者現在可以藉由移動立方體來重新放置整個火箭發射器的體驗。

> [!TIP]
> 有各種不同的使用者體驗流程可用於重新置放體驗，包括使用重新置放物件 (例如本教學課程中使用的立方體)、使用按鈕來切換環繞體驗的周框方塊、使用位置和旋轉 gizmo 等等。

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已了解 Azure Spatial Anchors 的基本概念。 本教學課程提供了您幾個按鈕，讓您探索啟動和停止 Azure Spatial Anchors 工作階段，以及在單一裝置上建立、上傳和下載 Azure Spatial Anchors 所需的各種步驟。

在下一個課程中，您將了解如何將 Azure 錨點識別碼儲存至 HoloLens 2 以便擷取 (即使在重新啟動應用程式之後)，以及如何在多個裝置之間傳輸錨點識別碼以達到空間對齊。

[下一課：2.儲存、擷取和共用 Azure Spatial Anchors](mrlearning-asa-ch2.md)
