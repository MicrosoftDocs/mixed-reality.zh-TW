---
title: 多使用者功能教學課程 - 2。 設定 Photon Unity 網路
description: 完成此課程以了解如何在 HoloLens 2 應用程式中實作使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: e5817338dbed944232664a86f8b0625bc9d3e1e7
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304767"
---
# <a name="2-setting-up-photon-unity-networking"></a>2.設定 Photon Unity 網路

## <a name="overview"></a>概觀

在本教學課程中，您將使用 Photon Unity 網路 (PUN) 來準備建立共用體驗。 您將了解如何建立 Photon PUN 應用程式、將 PUN 資產匯入到您的 Unity 專案，以及將您的 Unity 專案連線到 PUN 應用程式。

## <a name="objectives"></a>目標

* 了解如何建立 PUN 應用程式
* 了解如何尋找和匯入PUN 資產
* 了解如何將您的 Unity 專案連線至 PUN 應用程式

## <a name="creating-and-preparing-the-unity-project"></a>建立和準備 Unity 專案

在本節中，您將建立新的 Unity 專案，並使該專案準備好進行 MRTK 開發。

為此，請先遵循[初始化您的專案和部署第一個應用程式](mr-learning-base-02.md) (但不包括[對您的裝置建置應用程式](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的指示)，其中包括下列步驟：

1. [建立 Unity 專案](mr-learning-base-02.md#creating-the-unity-project)，並為其提供適當的名稱，例如「MRTK 教學課程」
1. [切換建置平台](mr-learning-base-02.md#configuring-the-unity-project)
1. [匯入 TextMeshPro 基本資源](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
1. [匯入混合實境工具組](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
1. [設定 Unity 專案](mr-learning-base-02.md#configuring-the-unity-project)
1. [建立和設定場景](mr-learning-base-02.md#creating-and-configuring-the-scene)並為場景提供適當的名稱，例如 MultiUserCapabilities

然後遵循[變更空間感知顯示選項](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)的指示，以執行下列動作：

1. 將 **MRTK 設定檔**變更為 **DefaultHoloLens2ConfigurationProfile**
1. 將**空間感知網格顯示選項**變更為**遮蔽**。

## <a name="enabling-additional-capabilities"></a>啟用其他功能

在 Unity 功能表中，選取 [編輯] > [專案設定...] 來開啟 [玩家設定] 視窗，然後找出 [玩家] >  [發佈設定] 區段：

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section2-step1-1.png)

在 [發佈設定] 中，向下捲動至 [功能] 區段，然後再次確認您在上述[設定 Unity 專案](mr-learning-base-02.md#configuring-the-unity-project)所啟用的 **InternetClient**、**Microphone**、**SpatialPerception** 和 **GazeInput** 功能是否皆已啟用。

然後啟用下列其他功能：

* **InternetClientServer** 功能
* **PrivateNetworkClientServer** 功能

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section2-step1-2.png)

## <a name="installing-inbuilt-unity-packages"></a>安裝內建的 Unity 套件

在 Unity 功能表中，選取 視窗 >  **套件管理員** 以開啟 套件管理員 視窗，然後選取 AR 基本概念，並按一下 安裝 按鈕以安裝套件：

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section3-step1-1.png)

> [!NOTE]
> 您正在安裝 AR Foundation 套件，因為 Azure Spatial Anchors SDK 需要此套件，您將在下一節中匯入。

## <a name="importing-the-tutorial-assets"></a>匯入教學課程資產

下載並**依列出順序**來**匯入**下列 Unity 自訂套件：

* [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (2.2.1 版)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage)

匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section4-step1-1.png)

> [!TIP]
> 如需有關如何匯入 Unity 自訂套件的提示，您可以參閱[匯入混合實境工具組 ](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) 的指示。

> [!NOTE]
> 匯入 MultiUserCapabilities 教學課程資產套件之後，您會在主控台視窗中看到數個 [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) 錯誤，其指出缺少類型或命名空間。 這是預期的情況，將在下一節匯入 PUN 資產時解決。

## <a name="importing-the-pun-assets"></a>匯入 PUN 資產

在 Unity 功能表中，選取 [視窗] > [資產存放區] 來開啟 [資產存放區] 視窗，然後從 Exit Games 搜尋並選取 [PUN 2 - 免費]，按一下 [下載] 按鈕，將資產套件下載到您的 Unity 帳戶：

下載完成時，請按一下 [匯入] 按鈕來開啟 [匯入 Unity 套件] 視窗：

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-1.png)

在 [匯入 Unity 套件] 視窗中，按一下 [全部] 按鈕以確保選取所有資產，然後按一下 [匯入] 按鈕來匯入資產：

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-2.png)

Unity 完成匯入程序之後，Pun 精靈視窗會隨即出現並載入 PUN 設定功能表，您現在可以忽略或關閉此視窗：

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-3.png)

## <a name="creating-the-pun-application"></a>建立 PUN 應用程式

在本節中，您將建立 Photon 帳戶 (如果您還沒有帳戶的話)，並建立新的 PUN 應用程式。

瀏覽至 Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">儀表板</a> 並登入 (如果您已經有想要使用的帳戶)，否則請按一下 [建立帳戶] 連結，並依照指示註冊新帳戶：

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-1.png)

登入之後，按一下 [建立新的應用程式] 按鈕：

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-2.png)

在 [建立新的應用程式] 頁面上，輸入下列值：

* 針對 Photon 類型，請選取 [PUN]
* 針對 [名稱]，請輸入適當的名稱，例如 MRTK Tutorials
* 針對 [描述]，您可以選擇性地輸入適當描述
* 針對 [URL]，請將欄位保留空白

接著按一下 [建立] 按鈕以建立新應用程式：

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-3.png)

當 Photon 完成建立程序後，新的 PUN 應用程式將會出現在儀表板上：

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a>將 Unity 專案連線至 PUN 應用程式

在本節中，您會將 Unity 專案連線到您在上一節中建立的 PUN 應用程式。

在 Photon 儀表板上，按一下 [應用程式識別碼] 欄位以顯示應用程式識別碼，然後將其複製到您的剪貼簿：

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-1.png)

在 Unity 功能表中，選取 [視窗] > [Photon Unity 網路] > [PUN 精靈] 以開啟 PUN 精靈視窗，然後按一下 [設定專案] 按鈕以開啟 [PUN 設定] 功能表，並依照下列方式進行設定：

* 在 [AppId 或電子郵件] 欄位中，貼上您在上一個步驟中複製的 PUN 應用程式識別碼

然後按一下 [設定專案] 按鈕來套用應用程式識別碼：

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-2.png)

當 Unity 完成 PUN 設定程序後，[PUN 設定] 功能表就會顯示訊息「完成！」訊息 並自動選取 [專案] 視窗中的 **PhotonServerSettings** 資產，讓其屬性顯示在 [偵測器] 視窗中：

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-3.png)

## <a name="congratulations"></a>恭喜！

您已成功建立 PUN 應用程式，並將其連線到您的 Unity 專案。 下一個步驟是允許與其他使用者連線，讓多個使用者可以看到彼此。

[下一個教學課程：3.連線多個使用者](mr-learning-sharing-03.md)
