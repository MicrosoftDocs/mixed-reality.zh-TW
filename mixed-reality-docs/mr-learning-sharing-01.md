---
title: 多使用者功能教學課程 - 1。 簡介
description: 完成此課程以了解如何在 HoloLens 2 應用程式中實作使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: ebdef9818aace28b32e91384cd9d3278da2733b4
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376340"
---
# <a name="1-introduction"></a>1.簡介

## <a name="overview"></a>概觀

歡迎使用多使用者功能教學課程！ 透過本教學課程系列，您將了解使用 <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity 網路</a> (PUN) 建置多使用者體驗的基本概念。 PUN 是可讓混合實境開發人員用來建立共用體驗的眾多網路功能選項之一。

本系列的教學課程：

* [設定 Photon Unity 網路](mr-learning-sharing-02.md)
* [連線多個使用者](mr-learning-sharing-03.md)
* [與多個使用者共用物件移動](mr-learning-sharing-04.md)
* [將 Azure Spatial Anchors 整合到共用體驗](mr-learning-sharing-05.md)

## <a name="objectives"></a>目標

* 了解如何建立 PUN 應用程式以及將您的 Unity 專案連線至 PUN 應用程式
* 了解如何在共用體驗中連線多個使用者
* 了解如何與其他使用者共用物件移動
* 了解如何達到多個裝置之間的空間對齊

## <a name="prerequisites"></a>必要條件

* 已[安裝正確工具](install-the-tools.md)的 Windows 10 電腦
* Windows 10 SDK 10.0.18362.0 或更新版本
* 已[針對開發而設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，已安裝 Unity 2019.3.15，且已新增通用 Windows 平台組建支援模組
* 完成[建立空間錨點資源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)區段，其位於[教學課程：建立使用 Azure Spatial Anchors 的 Unity HoloLens 應用程式](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)
* 完成[使用者入門教學課程](mr-learning-base-01.md)系列或一些基本的 Unity 和 MRTK 體驗
* 完成 [Azure 空間錨點教學課程](mr-learning-asa-01.md)系列，或建立 Azure 空間錨點帳戶的體驗
* 如果想要部署至 Android 及 HoloLens
  * 已啟用<a href="https://developer.android.com/studio/debug/dev-options" target="_blank">開發人員</a>和具有 <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore 功能</a>的 Android 裝置，可透過 USB 連接至您的 Windows 或 macOS 電腦
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，已安裝 Unity 2019.3.15，且已新增 Android 組建支援模組
* 如果想要部署至 iOS 及 HoloLens
  * 已安裝最新版 <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> 和 <a href="https://cocoapods.org" target="_blank">CocoaPods</a> 的 macOS 電腦
  * <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit 相容</a>的 iOS 裝置可透過 USB 連接至您的 macOS 電腦
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，已安裝 Unity 2019.3.15，且已新增 iOS 組建支援模組

> [!CAUTION]
> 本教學課程系列的建議混合實境工具組版本是 MRTK 2.4.0。

> [!CAUTION]
> 本教學課程系列的建議 Unity 版本是 Unity 2019.3.15。 這個版本能取代上述連結必要條件中所述的任何 Unity 版本需求。

[下一個教學課程：2.設定 Photon Unity 網路](mr-learning-sharing-02.md)
