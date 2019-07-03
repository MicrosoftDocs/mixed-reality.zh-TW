---
title: 學習模組共用 HoloLens 2 MR
description: 完成這個課程來了解如何實作 HoloLens 2 應用程式內的多使用者分享的經驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 80cefb36ec1944ec6f537aafcbf4b63f7f812d26
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523295"
---
#  <a name="setting-up-photon-unity-networking"></a>設定 Photon Unity 網路

在本教學課程中，我們了解如何做好準備，以建立共用的體驗 Photon Unity 網路功能 （自己使用這個雙關語） 匯入 Unity 專案。 Photon 是數個網路功能選項 Mixed Reality 開發人員可用來建立共用的體驗。 我們將帶領您學習建立 Photon 帳戶、 匯入 Photon，並建立選用的本機伺服器

目標：

* 了解如何建立 Photon 帳戶

* 了解如何尋找並匯入 Photon Unity 網路

* 設定本機的 Photon server

  

### <a name="setting-up-photon"></a>設定 Photon

1. 設定好[Photon](https://dashboard.photonengine.com/en-US/Account/SignUp)帳戶。 按一下瀏覽至 Photon 註冊頁面[此連結](https://dashboard.photonengine.com/en-US/Account/SignUp)。 若要建立的帳戶註冊頁面上，遵循的指示。 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. 依序按一下 [建立新的應用程式] 按鈕建立的應用程式識別碼。

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. 從 Photon 類型下的下拉式功能表中選取 Photon 自己使用這個雙關語。 然後為它的名稱。 在此範例中，我們命名為它 HoloLensPhotonProject。 完成之後，按一下 [建立] 按鈕。

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. 完成後，返回您的應用程式頁面，您應該會看到類似下圖。 按一下應用程式識別碼，並將它複製。 貼上是您可以輕鬆存取的地方。  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. 建立新的 unity 專案並將它命名為 HLSharingProject。 如需有關如何建立新的 Unity 專案的指示，請參閱[基底模組中的 < 建立 Unity 專案 > 一節](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)。 

6. 專案載入後，按一下 [資產存放區] 索引標籤中，如下圖所示。 然後，在下圖中反白顯示搜尋方塊中輸入自己使用這個雙關語，並選取 Photon 自己使用這個雙關語 2-例如 FRE"資產，從搜尋結果。 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. 下載並匯入此資產藉由按下 [下載和匯入] 按鈕。

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. 匯入程序完成後 Photon，自己使用這個雙關語精靈 隨即出現。 需要應用程式識別碼 （這應該是您的剪貼簿中） 從步驟 4 中，並將它貼到 AppID 方塊中，然後按 安裝專案按鈕。 
![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. 已成功新增 AppID 之後, 瀏覽至 Photon PhotonUnityNetworking]-> []-> [資源]-> [PhotonServerSettings 在資產中的。 選取 [使用名稱伺服器] 選項中，並設定我們的固定的區域或 yourPphoton 服務區域。

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>恭喜！

您已成功建立 Photon 帳戶、 設定本機 Photon 伺服器，並自己使用這個雙關語匯入 Unity。 下一步是要設定專案，然後允許與其他使用者的連線，這樣多個使用者可以看到您的工作。 

[下一個教學課程：準備 Unity 進行開發](mrlearning-sharing(photon)-ch2.md)

