---
title: Azure Spatial Anchors 教學課程 - 5。 適用於 Android 和 iOS 的 Azure Spatial Anchors
description: 完成此課程，以了解如何將包含混合實境工具組和 Azure Spatial Anchors 的 Unity 專案部署至 Android 和 iOS。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens, android, ios
ms.localizationpriority: high
ms.openlocfilehash: e95b659eed3bfb406dcc41d5b3ad6e5e18c764a5
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304442"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a>5.適用於 Android 和 iOS 的 Azure Spatial Anchors

在本教學課程中，您將了解如何使用 AR Foundation、ARCore XR 外掛程式和 ARKit XR 外掛程式，在 Android 和 iOS 裝置上建置專案。

## <a name="objectives"></a>目標

* 了解如何使用 Unity 的 AR Foundation 和 ARCore XR 外掛程式，在 Android 裝置上建置專案
* 了解如何使用 Unity 的 AR Foundation 和 ARKit XR 外掛程式，在 iOS 裝置上建置專案

## <a name="installing-inbuilt-unity-packages"></a>安裝內建的 Unity 套件

在本節中，您將升級及安裝下列內建套件：

* AR Foundation 3.1.3
* 舊版 Input Helpers 2.1.4
* 適用於 Android 的 ARCore XR 外掛程式 3.1.3 支援
* 適用於 iOS 的 ARKit XR 外掛程式 3.1.3 支援

> [!CAUTION]
> 並非所有版本都與 MRTK 相容，而且只有特定版本能夠一起使用，因此請務必安裝上列確切版本。

在 Unity 功能表中，選取 [視窗] > [套件管理員] 以開啟 [套件管理員] 視窗，然後選取 [AR Foundation] > [3.1.3]，並按一下 [更新為 3.1.3] 按鈕以更新套件：

![mr-learning-asa](images/mr-learning-asa/asa-05-section1-step1-1.png)

若有需要，遵循相同程序來匯入其餘套件。

> [!NOTE]
> 如果您正針對 Android 開發本專案，則不需要安裝 ARKit XR 外掛程式套件。 同樣地，如果您要針對 iOS 開發本專案，就不需要安裝 ARCore XR 外掛程式。

## <a name="configure-mrtk-for-ar-foundation-camera"></a>針對 AR Foundation 相機設定 MRTK

在本節中，您將了解如何設定 MRTK 以部署至行動裝置。

在 [階層] 視窗中，選取 [MixedRealityToolkit] 物件。 然後在 [偵測器] 視窗中，選取 [相機] 索引標籤、複製相機設定檔，並為其提供適當的名稱，例如，**AzureSpatialAnchors_ARCameraProfile**：

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> 如需有關如何複製 MRTK 設定檔的提示，您可以參閱[設定混合實境工具組設定檔](mr-learning-base-03.md)的指示。

在仍選取 [相機] 索引標籤的 [偵測器] 視窗中展開 [相機設定提供者]，然後按一下 [+ 新增相機設定提供者] 按鈕，再展開新增的 [新資料提供者 1]：

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-2.png)

使用 [類型] 下拉式清單，將類型變更為 [Microsoft.MixedReality.Toolkit.Experimental.UnityAR] > [UnityARCameraSettings]：

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-3.png)

在仍然選取 **MixedRealityToolkit** 物件的 [階層] 視窗中，使用 [新增元件] 按鈕來新增下列元件：

* AR Anchor Manager (指令碼)
* DisableDiagnosticsSystem (指令碼)

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-4.png)

> [!NOTE]
> AR Session Origin (指令碼) 元件會在您新增 AR Reference Point Manager (指令碼) 元件時自動加入，因為這是 AR Reference Point Manager (指令碼) 元件的必要項目。

## <a name="building-your-application-to-your-android-device"></a>在您的 Android 裝置上建置應用程式

在本節中，您將了解如何設定您的專案，以在 Android 裝置中建置及部署該專案。

在 Unity 功能表中，選取 [檔案] > [建置設定...] 來開啟 [建置設定] 視窗，然後將平台切換為 Android：

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> 如需有關如何切換建置平台的提示，可參閱[切換建置平台](mr-learning-base-02.md#switching-the-build-platform)的指示。

關閉 [建置設定] 視窗。

在 Unity 功能表中，選取 [混合實境工具組] > [公用程式] > [設定 Unity 專案] 來開啟 [MRTK 專案設定程式] 視窗，並確定已選取所有選項，然後按一下 [套用] 按鈕來套用設定：

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-2.png)

在 Unity 功能表中，選取 [編輯] > [專案設定...] 來開啟 [玩家設定] 視窗，然後找出 [玩家] >  [其他設定] 區段，選取 [Vulkan]，然後按一下 **"-"** 來將其移除：

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-3.png)

關閉 [玩家設定] 視窗，然後再次開啟 [建置設定] 視窗。

在 [建置設定] 視窗中，按一下 [新增開啟的場景] 按鈕，將您目前的場景加入至 [建置中的場景] 清單。 然後，使用 USB 纜線，將您的 Android 裝置連接到您的電腦，並從 [執行裝置] 下拉式清單中將其選取：

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> 如果您的裝置未出現在 [執行裝置] 下拉式清單中，您可能需要按下下拉式清單旁的 [重新整理] 按鈕。

在 [建置設定] 視窗中，按一下 [建置並執行] 按鈕，以開啟 [建置 Android] 視窗。

選擇適當的位置來儲存您的建置，例如 _D:\MixedRealityLearning\Builds_，然後為 apk 提供適當的名稱，例如 _MRTKTutorials-AzureSpatialAnchors_，然後按一下 [儲存] 按鈕來啟動建置程序：

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
如果您在 Unity 主控台視窗中遇到與 Android SDK、NDK 或 JDK 模組相關的任何錯誤，則需要開啟 Unity Hub，並安裝相關聯的 Android 建置支援模組。

當建置程序完成時，應用程式應該會自動載入您的 Android 裝置。

## <a name="building-your-application-to-your-ios-device"></a>在您的 iOS 裝置上建置應用程式

在本節中，您將了解如何設定您的專案，以在 iOS 裝置中建置及部署該專案。

在 Unity 功能表中，選取 [檔案] > [建置設定...] 來開啟 [建置設定] 視窗，然後將平台切換為 iOS：

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> 如需有關如何切換建置平台的提示，可參閱[切換建置平台](mr-learning-base-02.md#switching-the-build-platform)的指示。

關閉 [建置設定] 視窗。

在 Unity 功能表中，選取 [混合實境工具組] > [公用程式] > [設定 Unity 專案] 來開啟 [MRTK 專案設定程式] 視窗，並確定已選取所有選項，然後按一下 [套用] 按鈕來套用設定：

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-2.png)

在 Unity 功能表中，選取 [編輯] > [專案設定...] 來開啟 [玩家設定] 視窗，然後找出 [玩家] >  [其他設定] 區段，取消核取 [Strip Engine Code] 核取方塊來將其停用：

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-3.png)

關閉 [玩家設定] 視窗，然後再次開啟 [建置設定] 視窗。

在 [建置設定] 視窗中，按一下 [新增開啟的場景] 按鈕，將您目前的場景加入至 [建置中的場景] 清單：

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-4.png)

在 [建置設定] 視窗中，按一下 [建置] 按鈕，以開啟 [建置 iOS] 視窗。

選擇適當的位置來儲存您的 Xcode 專案，例如 _D:\MixedRealityLearning\Builds_，建立新的資料夾並指定適當的名稱，例如 _MRTKTutorials-AzureSpatialAnchors_，然後按一下 [選取資料夾] 按鈕來開始建置程序：

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-5.png)

當建置程序完成時，請遵循[ Xcode 專案](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project)的指示，以了解如何將 Xcode 專案部署至您的 iOS 裝置。

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已了解如何使用 AR Foundation、ARCore XR 外掛程式和 ARKit XR 外掛程式，在 Android 和 iOS 裝置上建置專案。
