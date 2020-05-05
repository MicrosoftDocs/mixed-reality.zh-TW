---
title: 多使用者功能教學課程 - 4。 與多個使用者共用物件移動
description: 完成此課程以了解如何在 HoloLens 2 應用程式中實作使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 41b62eb2d9f400d0af341c9fcce887c72af7a3aa
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610656"
---
# <a name="3-sharing-object-movements-with-multiple-users"></a>3.與多個使用者共用物件移動

在本教學課程中，您將了解如何共用物件的移動，讓共用體驗的所有參與者都可以共同作業及查看彼此的互動。

## <a name="objectives"></a>目標

* 設定專案來共用物件的移動
* 了解如何建立基本的多使用者共同作業應用程式

## <a name="preparing-the-scene"></a>準備場景

在本節中，您將藉由新增教學課程預製物件 (Prefab) 來準備場景。

在 [專案] 視窗中，瀏覽至 [資產]   > [MRTK.Tutorials.MultiUserCapabilities]   > [Prefabs]  資料夾，並將**TableAnchor** 預製物件 (Prefab) 拖曳到階層視窗中的 **SharedPlayground** 物件上方，以將其作為 SharedPlayground 物件的子系來新增至您的場景：

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a>設定 PUN 以具現化物件

在本節中，您會將專案設定為使用上一節中建立的 RocketLauncher_Complete_Variant 預製物件，並定義其將具現化的位置。

在 [專案] 視窗中，瀏覽至 [資產]   > [MRTK.Tutorials.MultiUserCapabilities]   > [Resources]  資料夾。

在 [階層] 視窗中，展開 **NetworkLobby** 物件，然後選取 **NetworkRoom** 子物件，接著在 [偵測器] 視窗中找出 **Photon Room (指令碼)** 元件，並依照下列方式進行設定：

* 在 [Photon 使用者預製物件]  欄位中，從 [Resources] 資料夾指派 **PhotonUser** 預製物件

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-1.png)

在仍選取 **NetworkRoom** 子物件的情況下，在 [階層] 視窗中，展開 **TableAnchor** 物件，然後在 [偵測器] 視窗中找出 **Photon Room (指令碼)** 元件，並依照下列方式進行設定：

* 在 [火箭發射器位置]  欄位中，從 [階層] 視窗指派 **Table** 子物件

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a>嘗試共用物件移動的體驗

如果您現在建立了 Unity 專案並將其部署至 HoloLens，然後回到 Unity，並在應用程式於 HoloLens 上執行時，按下 [開始遊戲] 按鈕進入遊戲模式，當您在 HoloLens 中移動物件時，您將會看到物件在 Unity 中移動：

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section3-step1-1.gif)

## <a name="congratulations"></a>恭喜！

您已成功設定專案來同步物件移動，而且使用者可以在其他使用者移動物件時，看到物件移動。 在下一個教學課程中，您將會實作讓共用體驗在實體世界中對齊的功能，而使用者會在實際的實體位置看到彼此，因此物件會出現在相同的實體位置，並為所有使用者旋轉。

[下一個教學課程：4.將 Azure Spatial Anchors 整合到共用體驗](mrlearning-sharing(photon)-ch4.md)
