---
title: 多使用者功能教學課程 - 1。 設定 Photon Unity 網路
description: 完成此課程以了解如何在 HoloLens 2 應用程式中實作使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 2f5b55fe9c54e9e2c08177266c04a97d2302230e
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610752"
---
# <a name="1-setting-up-photon-unity-networking"></a>1.設定 Photon Unity 網路

## <a name="overview"></a>概觀

在本教學課程中，您將了解如何使用 Photon Unity 網路 (PUN) 來準備建立共用體驗。 Photon 是可讓混合實境開發人員用來建立共用體驗的眾多網路功能選項之一。 您將了解如何建立 Photon PUN 應用程式、將 Photon PUN 資產匯入到您的 Unity 專案，以及將您的 Unity 專案連線到 Photon PUN 應用程式。

## <a name="objectives"></a>目標

* 了解如何建立 Photon PUN 應用程式
* 了解如何尋找和匯入 Photon PUN 資產
* 了解如何將您的 Unity 專案連線至 Photon PUN 應用程式

## <a name="prerequisites"></a>必要條件

>[!TIP]
>如果您尚未完成[入門教學課程](mrlearning-base.md)及 [Azure Spatial Anchors 教學課程](mrlearning-asa-ch1.md)的教學課程系列，建議您先完成這些教學課程。

* 已[安裝正確工具](install-the-tools.md)的 Windows 10 電腦
* Windows 10 SDK 10.0.18362.0 或更新版本
* 基本的 C# 程式設計能力
* 已[針對開發而設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，已安裝 Unity 2019.2，且已新增通用 Windows 平台組建支援模組
* 完成[建立空間錨點資源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)區段，其位於[教學課程：建立使用 Azure Spatial Anchors 的 Unity HoloLens 應用程式](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)

> [!IMPORTANT]
> 本教學課程系列的建議 Unity 版本是 Unity 2019.2. X。 這個版本能取代上述連結之必要條件中所述的任何 Unity 版本需求或建議。

## <a name="creating-and-preparing-the-unity-project"></a>建立和準備 Unity 專案

在本節中，您將建立新的 Unity 專案，並使該專案準備好進行 MRTK 開發。

為此，請先遵循[初始化您的專案和第一個應用程式](mrlearning-base-ch1.md) (但不包括[對您的裝置建置應用程式](mrlearning-base-ch1.md#build-your-application-to-your-device)的指示)，其中包括下列步驟：

1. [建立新的 Unity 專案](mrlearning-base-ch1.md#create-new-unity-project)，並為其提供適當的名稱，例如「MRTK 教學課程」 

2. [設定適用於 Windows Mixed Reality 的 Unity 專案](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [匯入 TextMesh Pro 基本資源](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [匯入混合實境工具組](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [設定用於混合實境工具組的 Unity 專案](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. [將 Mixed Reality 工具組新增至 Unity 場景](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)並為場景提供適當的名稱，例如 *MultiUserCapabilities*

然後遵循[如何設定混合實境工具組設定檔 (變更空間感知顯示選項)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) 的指示，將場景的 MRTK 組態設定檔變更為 **DefaultHoloLens2ConfigurationProfile**，並將空間感知網格的顯示選項變更為 [遮蔽]  。

> [!CAUTION]
> 如上方連結：[設定用於混合實境工具組的 Unity 專案](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)中所述的指示，強烈建議您不要為 Unity 啟用 MSBuild。

## <a name="configuring-the-capabilities"></a>設定功能

在 Unity 功能表中，選取 [編輯]   > [專案設定...]  來開啟 [玩家設定] 視窗，然後找出 [玩家]   >  [發佈設定]  區段：

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-1.png)

在 [發佈設定]  中，向下捲動至 [功能]  區段，然後再次確認您在教學課程開頭建立專案時所啟用的 **InternetClient**、**Microphone** 和 **SpatialPerception** 功能是否皆已啟用。 然後，啟用 **InternetClientServer**、**PrivateNetworkClientServer**和 **RemovableStorage** 功能：

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-2.png)

## <a name="adding-inbuilt-unity-packages"></a>新增內建的 Unity 套件
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

在本節中，您將安裝 Unity 的內建 AR Foundation 套件，因為您在下一節匯入 Azure Spatial Anchors SDK 時會需要此套件。

在 Unity 功能表中，選取 [視窗]   >  **[套件管理員]** ：

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-1.png)

> [!NOTE]
> 可能需要幾秒鐘的時間，AR Foundation 套件才會出現在清單中。

在 [套件管理員] 視窗中選取 [AR Foundation]  ，然後按一下 [安裝]  按鈕來安裝套件：

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>匯入教學課程資產

下載並**依列出順序**來**匯入**下列 Unity 自訂套件：

* [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (2.1.1 版)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage)

> [!TIP]
> 如需有關如何匯入 Unity 自訂套件的提示，您可以參閱[匯入混合實境工具組](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) 的指示。

匯入教學課程資產之後，您的專案視窗看起來應該會像這樣：

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section4-step1-1.png)

> [!NOTE]
> 匯入 MultiUserCapabilities 教學課程資產套件之後，您會在主控台視窗中看到數個 [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) 錯誤，其指出缺少類型或命名空間。 這是預期的情況，將在下一節匯入 Photon 資產時解決。

## <a name="importing-the-photon-assets"></a>匯入 Photon 資產

在本節中，您將從 Unity 的資產存放區匯入 Photon Unity 網路 (PUN) 資產。

在 Unity 功能表中，選取 [視窗]   > [資產存放區]  來開啟 [資產存放區] 視窗，然後從 Exit Games 搜尋並選取 [PUN 2 - 免費]  ，並按一下 [下載]  按鈕，將資產套件下載到您的 Unity 帳戶：

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-1.png)

下載完成時，請按一下 [匯入]  按鈕來開啟 [匯入 Unity 套件] 視窗：

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-2.png)

在 [匯入 Unity 套件] 視窗中，按一下 [全部]  按鈕以確保選取所有資產，然後按一下 [匯入]  按鈕來匯入資產：

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-3.png)

Unity 完成匯入程序之後，Pun 精靈視窗會隨即出現並載入 PUN 設定功能表，您現在可以忽略或關閉此視窗：

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-4.png)

## <a name="setting-up-photon"></a>設定 Photon

在本節中，您將建立 Photon 帳戶 (如果您還沒有帳戶的話)，並建立新的 PUN 應用程式。

瀏覽至 Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">儀表板</a> 並登入 (如果您已經有想要使用的帳戶)，否則請按一下 [建立帳戶]  連結，並依照指示註冊新帳戶：

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-1.png)

登入之後，按一下 [建立新的應用程式]  按鈕：

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-2.png)

在 [建立新的應用程式] 頁面上，輸入下列值：

* 針對 [Photon 類型]，請選取 [Photon PUN]
* 針對 [名稱]，請輸入適當的名稱，例如 MRTK Tutorials 
* 針對 [描述]，您可以選擇性地輸入適當描述
* 針對 [URL]，請將欄位保留空白

按一下 [建立]  按鈕以建立新端點：

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-3.png)

當 Photon 完成建立程序後，新的 PUN 應用程式將會出現在儀表板上：

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a>將 Unity 專案連線至 PUN 應用程式

在本節中，您會將 Unity 專案連線到您在上一節中建立的 PUN 應用程式。

在 Photon 儀表板上，按一下 [應用程式識別碼]  欄位以顯示應用程式識別碼，然後將其複製到您的剪貼簿：

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-1.png)

在 Unity 功能表中，選取 [視窗]   > [Photon Unity 網路]   > [PUN 精靈]  以開啟 PUN 精靈視窗，然後按一下 [設定專案]  按鈕以開啟 [PUN 設定] 功能表，並依照下列方式進行設定：

* 在 [AppId 或電子郵件]  欄位中，貼上您在上一個步驟中複製的 PUN 應用程式識別碼

然後按一下 [設定專案]  按鈕來套用應用程式識別碼：

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-2.png)

當 Unity 完成 PUN 設定程序後，[PUN 設定] 功能表就會顯示訊息「完成！」  訊息 並自動選取 [專案] 視窗中的 **PhotonServerSettings** 資產，讓其屬性顯示在 [偵測器] 視窗中：

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-3.png)

## <a name="congratulations"></a>恭喜！

您已成功建立 Photon PUN 應用程式，並將其連線到您的 Unity 專案。 下一個步驟是允許與其他使用者連線，讓多個使用者可以看到彼此。

[下一個教學課程：2.連線多個使用者](mrlearning-sharing(photon)-ch2.md)
