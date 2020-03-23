---
title: 多使用者功能教學課程 - 1。 設定 Photon Unity 網路
description: 完成此課程以了解如何在 HoloLens 2 應用程式中實作使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 94068ff706e0e56ca8ec0f23beaed3a34159b777
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031335"
---
# <a name="1-setting-up-photon-unity-networking"></a>1.設定 Photon Unity 網路

## <a name="overview"></a>概觀

在本教學課程中，您將了解如何藉由將 Photon Unity 網路 (PUN) 匯入 Unity 專案，來準備建立共用體驗。 Photon 是可讓混合實境開發人員用來建立共用體驗的眾多網路功能選項之一。 您將了解如何建立 Photon 帳戶、匯入 Photon，以及建立選用的本機伺服器

## <a name="objectives"></a>目標

* 了解如何建立 Photon 帳戶
* 了解如何尋找和匯入 Photon Unity 網路功能
* 設定本機 Photon 伺服器

## <a name="prerequisites"></a>必要條件

>[!TIP]
>如果您尚未完成[入門教學課程](mrlearning-base.md)及 [Azure Spatial Anchors 入門教學課程](mrlearning-asa-ch1.md)的教學課程系列，建議您先完成這些教學課程。

* 已[安裝正確工具](install-the-tools.md)的 Windows 10 電腦
* Windows 10 SDK 10.0.18362.0 或更新版本
* 基本的 C# 程式設計能力
* 已[針對開發而設定](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 裝置

>[!IMPORTANT]
> 本教學課程系列的建議 Unity 版本是 Unity 2019.2. X。 這個版本能取代上述連結之必要條件中所述的任何 Unity 版本需求或建議。

## <a name="setting-up-photon"></a>設定 Photon

1. 設定 [Photon](https://dashboard.photonengine.com//Account/SignUp) 帳戶。 按一下[此連結](https://dashboard.photonengine.com//Account/SignUp)來瀏覽至 Photon 註冊頁面。 遵循註冊頁面上的指示來建立帳戶。

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. 按一下 [建立新的應用程式] 按鈕，以建立應用程式識別碼。

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. 從 [Photon 類型] 底下的下拉式功能表中，選取 [Photon PUN]。 然後為其命名。 在此範例中，我們將其命名為 HoloLensPhotonProject。 完成後，按一下 [建立] 按鈕。

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. 返回您的應用程式頁面，您應該會看到類似下圖的畫面。 按一下應用程式識別碼並加以複製。 將其貼入您可以輕鬆存取的位置。  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. 建立新的 Unity 專案，並將其命名為 HLSharingProject。 如需如何建立新 Unity 專案的指示，請參閱[基礎課程模組的＜建立 Unity 專案＞一節](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)。 

6. 專案載入後，按一下 [資產存放區] 索引標籤，如下圖所示。 然後，在下圖中醒目顯示的搜尋方塊中輸入 PUN，然後從搜尋結果中選取 [Photon PUN 2 - 免費] 資產。

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. 按下 [下載] 和 [匯入] 按鈕來下載並匯入此資產。

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. 一旦 Photon 完成匯入程序後，Pun 精靈會隨即出現。 取出步驟 4 中取得的應用程式識別碼 (應該位於您的剪貼簿中)，將其貼到 [AppID] 方塊中，然後按下 [安裝專案] 按鈕。

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. 成功新增 AppID 之後，請在 [資產] 中瀏覽至 [Photon] -> [PhotonUnityNetworking] -> [資源] -> [PhotonServerSettings]。 選取 [使用名稱伺服器] 選項，並將固定區域設定為 [美國] 或您的 Photon 服務區域。

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>恭喜！

您已成功建立 Photon 帳戶、設定本機 Photon 伺服器，並將 PUN 匯入 Unity。 下一個步驟是設定專案，並允許與其他使用者進行連線，讓多個使用者可以看到您的工作。

[下一個教學課程：2.準備 Unity 以進行開發](mrlearning-sharing(photon)-ch2.md)
