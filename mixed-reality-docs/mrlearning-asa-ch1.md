---
title: Azure 空間錨點教學課程-1。 開始使用 Azure 空間錨點
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: e62d3626ec6f2dbf8b66378212afab7db2f56422
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334456"
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

## <a name="prerequisites"></a>先決條件

>[!TIP]
>如果您尚未完成[快速入門教學](mrlearning-base.md)課程系列，建議您先完成這些教學課程。

* [已安裝正確工具](install-the-tools.md)的 WINDOWS 10 電腦
* Windows 10 SDK 10.0.18362.0 或更新版本
* 一些基本C#的程式設計能力
* [為開發設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置
* 完成[快速入門：建立使用 Azure 空間錨點的 Unity HoloLens 應用程式](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)教學課程中的[建立空間錨點資源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)一節。

>[!IMPORTANT]
>本教學課程系列需要<a href="https://unity3d.com/get-unity/download/archive" target="_blank">unity 2019.1</a> ，而建議的版本是 unity 2019.1.14。 這會取代上述所連結之必要條件中所述的任何 Unity 版本需求或建議。

## <a name="creating-the-unity-project"></a>建立 Unity 專案

在本節中，您將建立新的 Unity 專案，並針對 Windows Mixed Reality 進行設定。

1. 建立 Unity 專案，並為其提供適當的名稱，例如_Azure 空間錨點教學_課程。

2. 設定適用于 Windows Mixed Reality 的 Unity 專案。

    >[!TIP]
    >如需有關如何建立 Unity 專案並針對 Windows Mixed Reality 進行設定的提醒，您可以參閱[初始化專案和第一個應用程式](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1)教學課程中的[建立新的 Unity 專案](mrlearning-base-ch1.md#create-new-unity-project)和設定適用于[windows mixed reality 的 unity 專案](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)一節，這是使用者入門[教學](mrlearning-base.md)課程系列的一部分。

## <a name="adding-inbuilt-unity-packages"></a>新增內建 Unity 套件

在本節中，您將會新增要在專案中使用的工具組和 Sdk 所需的內建 Unity 資產和套件。

1. 匯入 TMP 基本資源。

    >[!NOTE]
    >我們正在新增此封裝，因為它是混合現實工具組的必要項。

    在 Unity 功能表中，選取 [Window > **TextMeshPro** > 匯**入 TMP 基本資源** **]** 。

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-1.1.png)

    在 [匯入 Unity 封裝] 快顯視窗中，先確定已選取所有資產，方法是按一下 [**全部**] 按鈕，然後按一下 [匯**入**] 按鈕來匯入資產。

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-1.2.png)

2. 安裝 AR Foundation。

    >[!NOTE]
    >我們會新增此封裝，因為 Azure 空間錨點 SDK 需要此套件。

    在 Unity 功能表中，選取 [Window > **封裝管理員** **]** 。

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-2.1.png)

    在 [套件管理員] 視窗中，選取 [ **AR Foundation** ]，然後按一下 [**安裝**] 按鈕來安裝封裝。

    >[!IMPORTANT]
    >這可能需要幾秒鐘的時間，AR Foundation 封裝才會出現在清單中。

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-2.2.png)

## <a name="importing-the-tutorial-assets"></a>匯入教學課程資產

在本節中，您將下載並匯入所有教學課程資產。

1. 下載資產。

    * [AzureSpatialAnchors. unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) （版本2.0.0）
    * [MixedReality. 2.1.0. unitypackage。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)
    * [MRTK.HoloLens2 GettingStarted. 2.1.0.1. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage)
    * [MRTK.HoloLens2 AzureSpatialAnchors. 2.1.0.1. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage)

2. 匯入資產。

    在 Unity 功能表中，選取 **資產** > 匯**入套件** > **自訂封裝**...。

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.1.png)

    在 [匯入套件 ...]快顯視窗中，選取 [ **AzureSpatialAnchors] unitypackage** ，然後按一下 [**開啟**] 按鈕。

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.2.png)

    在 [匯入 Unity 封裝] 快顯視窗中，先確定已選取所有資產，方法是按一下 [**全部**] 按鈕，然後按一下 [匯**入**] 按鈕來匯入資產。

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.3.png)

    重複這些步驟來匯入其餘的資產套件。 完成後，您的 Unity 專案的 [**資產**] 資料夾應該會包含這些子資料夾。

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.4.png)

## <a name="creating-and-preparing-the-scene"></a>建立和準備場景

在本節中，您將藉由新增混合現實工具組和一些教學課程 prefabs 來建立和準備場景。

1. 建立新場景。

    在 Unity 功能表中 **，選取 [** 檔案] > [**新場景**]。

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.1.png)

    在 Unity 功能表中 **，選取** 檔案 > **另存**新檔 ...。

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.2.png)

    在 [儲存場景] 快顯視窗中，流覽至專案的 [**幕後**] 資料夾，為您的場景提供適當的名稱（例如_ASATutorialScene_），然後按一下 [**儲存**] 按鈕來儲存場景。

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.3.png)

    >[!TIP]
    >只要此場景位於專案的 [資產] 資料夾內，您就可以將它儲存在您喜歡的任何地方。 不過，若要讓您的專案組織，通常建議將它儲存在專案的 [場景] 資料夾中。

2. 新增混合現實工具組。

    在 Unity 功能表中，選取 **混合現實工具**組， > **新增至場景並設定 ...** 。

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.1.png)

    在 [選取 MixedRealityToolkitConfigurationProfile] 快顯視窗中，按一下**DefaultHoloLens2ConfigurationProfile** ，將其設定為場景的 MRTK 設定檔。

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.2.png)

    在 Unity 功能表中 **，選取** 檔案 > **儲存** 以儲存場景。

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.3.png)

    >[!TIP]
    >當您進行本教學課程時，您可以使用鍵盤快速鍵 CTRL + S （macOS 上的 command + S）來快速儲存場景。

3. 新增教學課程 prefabs。

    在 [專案] 面板中，流覽至 [**資產**] [ > **MRTK]。教學課程. AzureSpatialAnchors** > **Prefabs**資料夾。 按住 CTRL 鍵（macOS 上的命令）時，按一下 [ **ButtonParent**]、[ **DebugWindow**] 和 [ **ParentAnchor** ] 以選取三個 prefabs。

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.1.png)

    在選取了三個 prefabs 的情況下，將它們拖曳到 [階層] 面板中，以將它們新增至場景。

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.2.png)

    若要將焦點放在場景中的物件上，您可以按兩下 [ParentAnchor] 物件，然後再稍微縮小一次。

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.3.png)

    >[!TIP]
    >比方說，如果您在場景中找到大圖示，例如，大框的 ' t ' 圖示會有干擾，您可以將<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">Gizmos 切換</a>到 off 位置來隱藏它們。

## <a name="configuring-the-buttons-to-operate-the-scene"></a>設定按鈕以操作場景

在本節中，您將在場景中新增 prefabs 和腳本，以建立一系列的按鈕，以示範本機錨點和 Azure 空間錨點在應用程式中的行為。

1. 設定 Pressable 按鈕 Hololens 透鏡2（腳本）元件。

    在 [階層] 面板中，展開 [ **ButtonParent** ] 物件，並選取名為**StartAzureSession**的第一個子物件。

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.1.png)

    在 [偵測器] 面板中，向下**Pressable 按鈕 Hololens 透鏡2（腳本）** 元件，然後按一下 [ **+** ] 圖示，將新的事件接聽程式新增至**按下的按鈕（）** 事件。

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.2.png)

    在 [階層] 面板中仍選取 StartAzureSession 物件時，按一下-並將**ParentAnchor**物件從 [階層] 面板拖曳至您剛才加入之事件接聽程式的 [空的**無（物件）** ] 欄位中，讓 ParentAnchor 物件在此按鈕中聆聽已按下按鈕的事件。

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.3.png)

    按一下相同事件接聽程式的 [**無**函式] 下拉式清單，然後選取 [ **AnchorModuleScript** > **StartAzureSession （）** ]，將 StartAzureSession （）函數設定為從這個按鈕引發按鈕按下的事件時所觸發的動作。

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.4.png)

2. 設定可互動（腳本）元件。

    在 [階層] 面板中仍然選取 StartAzureSession 物件時，請在 [偵測器] 面板中，向下流覽至 [**可互動（腳本）** ] 元件，然後針對**OnClick （）** 事件重複上述步驟1中的相同進程。

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-2.1.png)

3. 設定其餘按鈕

    針對其餘的每個按鈕，完成上述步驟1和2中所述的程式，將函式指派給按下的按鈕（）和 OnClick （）事件，如下所示：

    * 針對**StopAzureSession**物件，指派**StopAzureSession （）** 函數。
    * 針對**CreateAnchor**物件，指派**CreateAzureAnchor （）** 函式，然後將**ParentAnchor**再次拖曳到空白的**None （遊戲物件）** 欄位中。
    * 針對 [**開始尋找錨點**物件]，指派**FindAzureAnchor （）** 函數。
    * 針對 [**刪除 Azure 錨點**] 物件，指派**DeleteAzureAnchor （）** 函數。
    * 針對 [**刪除本機錨點**] 物件，指派**RemoveLocalAnchor （）** 函式，然後再次將**ParentAnchor**拖曳至 [空的**無（遊戲物件）** ] 欄位。

4. 將場景連線至 Azure 資源

    在 [階層] 面板中，選取 [ **ParentAnchor** ] 物件，然後在 [偵測器] 面板中，向下流覽至 [**空間錨點管理員（腳本）** ] 元件。

    然後，在 [**認證**] 區段中，將您的空間錨點帳戶識別碼和金鑰貼入對應的 [**空間錨點帳戶識別碼**] 和 [**空間錨點帳戶金鑰**] 欄位。

    >[!NOTE]
    >您已在本教學[課程的必要條件](mrlearning-asa-ch1.md#prerequisites)中建立空間錨點帳戶識別碼和金鑰。

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-4.1.png)

    >[!CAUTION]
    >請確定您已儲存場景。

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>嘗試 Azure 空間錨點的基本行為

您的場景已設定為示範 Azure 空間錨點的基本概念，現在可以部署應用程式，以便體驗 Azure 空間錨點搶先它。

1. 新增額外的必要功能。

    在 Unity 功能表中，選取 **編輯** > **專案設定 ...**  以開啟 播放 設定面板。

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.1.png)

    在 [Player 設定] 面板中，依序選取 [ **player** ] 和 [**發佈設定**]。

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.2.png)

    在 [**發行設定**] 中，向下流覽至 [**功能**] 區段，然後再次檢查您在教學課程開頭建立專案時所啟用的**SpatialPerception**（已啟用）。 然後，啟用**InternetClient**、 **InternetClientServer**、 **PrivateNetworkClientServer**、 **RemovableStorage**、**網路**攝影機和**麥克風**等功能。

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.3.png)

2. 將應用程式部署至 HoloLens 2。

    >[!TIP]
    >如需有關如何建立 Unity 專案並將其部署至 HoloLens 2 的提醒，您可以參閱[初始化專案和第一個應用程式](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1)教學課程的「將[應用程式建立到您的裝置](mrlearning-base-ch1.md#build-your-application-to-your-device)」區段，這是使用者入門[教學](mrlearning-base.md)課程系列的一部分。

3. 執行應用程式，並遵循應用程式內的指示。

    >[!CAUTION]
    >Azure 空間錨點會使用網際網路來儲存和載入錨定資料，因此請確定您的裝置已連線到網際網路。

    當應用程式在您的裝置上執行時，請遵循**Azure 空間錨點模組指示**面板上顯示的螢幕指示。

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-3.1.png)

## <a name="anchoring-an-experience"></a>錨定體驗

在前面幾節中，您已瞭解 Azure 空間錨點的基本概念。 我們使用 cube 來呈現父遊戲物件，並使用連結的錨點將其視覺化。 在本節中，您將瞭解如何藉由將它放在 ParentAnchor 物件的子系，來錨定整個體驗。

1. 新增 Rocket 啟動器體驗。

    在 專案 面板中，流覽至 **資產**  > **MRTK。GettingStarted** > **Prefabs**  資料夾，然後選取**Rocket Launcher_Complete** prefab。

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-1.1.png)

    在仍選取 [Rocket Launcher_Complete prefab] 的情況下，將其拖曳至 [階層] 面板中的 [ **ParentAnchor** ] 物件上方，使其成為 ParentAnchor 物件的子系。

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-1.2.png)

2. 重新置放 Rocket 啟動器體驗。

    移動模組**Rocket Launcher_Complete**物件，讓**ParentAnchor** （cube）仍然公開。

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-2.1.png)

    在應用程式中，使用者現在可以藉由移動 cube 來重新放置整個 Rocket 啟動器的使用體驗。

    >[!TIP]
    >有各種不同的使用者體驗流程可進行重新置放的體驗，包括使用重新置放的物件（例如本教學課程中使用的 cube）、使用按鈕來切換環繞體驗的周框方塊、使用位置和旋轉gizmos，還有更多。

## <a name="congratulations"></a>恭喜您

在本教學課程中，您已瞭解 Azure 空間錨點的基本概念。 這一課提供了數個按鈕，可讓您探索啟動和停止 Azure 會話，以及在單一裝置上建立、上傳和下載 azure 錨點所需的各種步驟。

在下一課中，您將瞭解如何將 Azure 錨點識別碼儲存至 HoloLens 2 進行抓取，即使在重新開機應用程式之後，以及如何在多個裝置之間傳輸錨點識別碼以達成空間對齊。

[下一課： 2. 儲存、正在抓取和共用 Azure 空間錨點](mrlearning-asa-ch2.md)
