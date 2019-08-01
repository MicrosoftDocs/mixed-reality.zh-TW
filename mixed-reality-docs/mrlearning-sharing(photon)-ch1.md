---
title: 多使用者功能教學課程-1。 設定 Photon Unity 網路功能
description: 完成此課程, 以瞭解如何在 HoloLens 2 應用程式中執行多使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: acb6966ace81180e95e6a0fe447d350572f7c0dd
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701964"
---
#  <a name="1-setting-up-photon-unity-networking"></a>1.設定 Photon Unity 網路功能

在本教學課程中, 我們將瞭解如何藉由將 Photon Unity 網路 (雙關語) 匯入 Unity 專案, 來準備建立共用體驗。 Photon 是可讓混合現實開發人員建立共用體驗的幾個網路功能選項之一。 我們將學習如何建立 Photon 帳戶、匯入 Photon, 以及建立選用的本機伺服器

## <a name="objectives"></a>目標

* 瞭解如何建立 Photon 帳戶

* 瞭解如何尋找和匯入 Photon Unity 網路功能

* 設定本機 Photon 伺服器

  

## <a name="setting-up-photon"></a>設定 Photon

1. 設定[Photon](https://dashboard.photonengine.com/en-US/Account/SignUp)帳戶。 按一下[此連結](https://dashboard.photonengine.com/en-US/Account/SignUp), 流覽至 Photon 註冊頁面。 遵循註冊頁面上的指示來建立帳戶。 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. 按一下 [建立新的應用程式] 按鈕, 以建立應用程式識別碼。

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. 從 [Photon 類型] 底下的下拉式功能表中, 選取 [Photon 雙關語]。 然後為它命名。 在此範例中, 我們將它命名為 HoloLensPhotonProject。 完成後, 按一下 [建立] 按鈕。

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. 完成後, 請返回您的應用程式頁面, 您應該會看到類似下圖的內容。 按一下 [應用程式識別碼] 並加以複製。 將它貼入您可以輕鬆存取的位置。  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. 建立新的 unity 專案, 並將其命名為 HLSharingProject。 如需如何建立新 Unity 專案的指示, 請參閱[基底模組的「建立 Unity 專案」一節](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)。 

6. 專案載入後, 按一下 [資產] [存放區] 索引標籤, 如下圖所示。 然後, 在下圖中反白顯示的搜尋方塊中, 輸入雙關語, 然後從搜尋結果中選取 Photon 雙關語2免費的資產。 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. 按下 [下載] 和 [匯入] 按鈕, 下載並匯入此資產。

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. 一旦 Photon 完成匯入程式, 就會出現雙關語 Wizard。 從步驟4取出 [應用程式識別碼] (應該位於您的剪貼簿中), 並將它貼入 [AppID] 方塊中, 然後按下 [安裝專案] 按鈕。 
![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. 成功新增 AppID 之後, 請流覽至 Photon-> PhotonUnityNetworking-> Resources-> PhotonServerSettings 在 [資產] 中。 選取 [使用名稱伺服器] 選項, 並將 [固定區域] 設定為 [US] 或您的 photon 服務區域。

![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>恭喜！

您已成功建立 Photon 帳戶、設定本機 Photon 伺服器, 並將雙關語匯入 Unity。 下一個步驟是設定專案, 然後允許與其他使用者進行連線, 讓多個使用者可以看到您的工作。 

[下一個教學課程:2.準備 Unity 以進行開發](mrlearning-sharing(photon)-ch2.md)

