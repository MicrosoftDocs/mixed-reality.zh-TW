---
title: Azure Spatial Anchors 教學課程 - 4. 適用於 Android 和 iOS 的 Azure Spatial Anchors
description: 完成此教學課程以了解如何在混合實境應用程式中實作 Azure Spatial Anchors。
author: jessemcculloch
ms.author: jemccull
ms.date: 05/18/2020
ms.topic: article
keywords: 混合實境、unity、教學課程、課程、hololens、azure、空間錨點
ms.localizationpriority: high
ms.openlocfilehash: a35f73ae5aee493182f0f4990aa345d990c3f513
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83867620"
---
# <a name="4-azure-spatial-anchors-for-android-and-ios"></a>4.適用於 Android 和 iOS 的 Azure Spatial Anchors

在本教學課程中，您將了解如何使用 AR Foundation、ARCore XR 外掛程式和 ARKit XR 外掛程式，在 Android 和 iOS 裝置上建置專案。

## <a name="objectives"></a>目標

* 了解如何使用 Unity AR Foundation 和 ARCore XR 外掛程式，在 Android 裝置上建置專案。
* 了解如何使用 Unity AR Foundation 和 ARKit XR 外掛程式，在 iOS 裝置上建置專案。

[!NOTE] 若要完成本教學課程，請確定您已完成 Azure Spatial Anchors 教學課程 -> [開始使用 Azure Spatial Anchors](mrlearning-asa-ch1.md)。

## <a name="adding-inbuilt-unity-packages"></a>新增內建的 Unity 套件

在本節中，您將安裝支援 Android 和 iOS 裝置所需的 Unity 內建 AR Foundation、ARCore XR 外掛程式和 ARKit XR 外掛程式套件。

請確定您已安裝這些 Unity 套件的正確版本，如下所示：

* **AR Foundation 2.1.4**
* **ARCore XR 外掛程式 2.2.0 預覽版 2**
* **ARKit XR 外掛程式 2.1.1**

[!NOTE] 如果您正針對 Android 開發本專案，則不需要安裝 ARKit XR 外掛程式套件。 同樣地，如果您要針對 iOS 開發本專案，就不需要安裝 ARCore XR 外掛程式。

在 Unity 功能表中，選取 [視窗] >  **[套件管理員]** ：

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-1.png)

可能需要幾秒鐘的時間，清單中才會出現所有套件。 按一下 [進階] 選項，然後選取 [顯示預覽套件]，以顯示預覽套件。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-2.png)

在 [套件管理員] 視窗中，選取 [AR Foundation]，您會在此看到許多版本，請按一下 [更新至 2.1.4] 按鈕以選取版本 2.1.4 並更新套件：

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-3.png)

若要支援 Android 裝置，請遵循相同的程序來匯入 ARCore XR 外掛程式 2.2.0 預覽版 2。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-4.png)

若要支援 iOS 裝置，您應該從套件管理員匯入 **ARKit XR 外掛程式 2.1.1** Unity 套件。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-5.png)

## <a name="customize-mrtk-to-support-ar-foundation-camera"></a>自訂 MRTK 以支援 AR Foundation 相機

在 [階層] 視窗中選取 [MixedRealityToolKit]，然後在 [偵測器] 視窗中，按一下 [混合實境工具組] 中的 [複製] 按鈕，以自訂 MRTK 設定以支援 AR Foundation。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-1.png)

當您按一下 [複製] 按鈕時，會出現新的 [複製設定檔] 視窗，然後再按一下 [複製] 按鈕來複製 DefaultMixedRealityToolkitProfile。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-2.png)

同樣地，在 [偵測器] 視窗中複製相機設定檔，並將設定檔重新命名為 "UnityARConfigurationProfile"，然後按一下 [複製] 按鈕。 在 [偵測器] 視窗中，找出 MixedReality，並選取 [相機] 索引標籤，展開 [偵測器] 視窗中的相機設定提供者，然後按一下 [+ 新增相機設定提供者] > 展開 [新的資料提供者 1] > 選取類型 [無] > 選取 [Microsoft.MixedReality.Toolkit.Experimental.UnityAR] > 選取 [UnityARCameraSettings]。


![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-3.png)

在 [階層] 視窗中選取 MixedRealityToolKit 物件之後，在 [偵測器] 視窗中按一下 [新增元件] 按鈕，然後輸入 AR 參考點管理員並選取指令碼，即可附加支援的指令碼。

新增「AR 參考點管理員」指令碼會自動隨附在 [偵測器] 視窗中新增「AR 工作階段來源」。 新增支援的指令碼之後，[偵測器] 視窗外觀如下所示。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-4.png)

## <a name="build-application-to-android-device"></a>將應用程式建置到 Android 裝置

若要將此應用程式建置到 Android 裝置，請按一下視窗頂端的 [檔案]，然後選取 [建置設定]。 畫面上會出現新的視窗，選取 [Android]，然後按一下 [切換平台]。 切換平台需要幾分鐘的時間。 切換至 Android 平台之後，按一下 [新增開啟場景]，並確定您目前的場景是 [組建中的場景] 清單中唯一選取的場景。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-1.png)

關閉 [建置設定] 視窗。 在 Unity 功能表中，選取 [混合實境工具組]  >  [公用程式]  >  [設定 Unity 專案] ，然後按一下 [套用] 來設定 Android 平台的 Unity 專案。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-2.png)

在 Unity 功能表中，選取 [編輯]  >  [專案設定] 來開啟 [專案設定] 視窗。 在 [專案設定] 視窗中，選取 [玩家] 索引標籤，展開 [其他設定] 區段，選取 [Vulkan]，並按一下 "-" 符號將其移除。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-3.png)

關閉 [玩家設定] 視窗，然後再次開啟 [建置設定] 視窗。 接著，使用 USB 纜線將 Android 裝置連接到您的電腦，並在 [建置並執行] 下拉式清單中選取您的裝置，再按一下 [建置並執行]。 系統會要求您儲存 .apk 檔案，您可以選擇任何名稱。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-4.png)

> [!NOTE]
> 如果您在 Unity 主控台視窗中遇到與 Android SDK、NDK 和/或 JDK 模組相關的任何錯誤，則需要開啟 Unity Hub，並安裝適用於 Android 建置支援模組相關聯的 SDK、NDK 和 JDK 模組。

當建置程序完成時，應用程式應該會自動載入您的 Android 裝置。

## <a name="build-application-to-ios-device"></a>將應用程式建置到 iOS 裝置

若要將此應用程式建置到 iOS 裝置，請按一下視窗頂端的 [檔案]，然後選取 [組建設定]。 畫面上會出現新的視窗，選取 [iOS]，然後按一下 [切換平台]。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-1.png)

關閉 [建置設定] 視窗。 在 Unity 功能表中，選取 [混合實境工具組]  >  [公用程式]  >  [設定 Unity 專案] ，然後按一下 [套用] 來設定 iOS 平台的 Unity 專案。

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-2.png)

若要建置 iOS XCode 專案，請移至 [建置設定]，然後按一下 [建置]。

請遵循[本指南](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project)，以了解如何將此專案部署至您的 iOS 裝置。

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已了解如何針對 Android 和 iOS 裝置建置專案。 您也了解如何使用 AR Foundation、ARCore XR 外掛程式和 ARKit XR 外掛程式，讓您的專案適用於 Android 和 iOS 裝置。