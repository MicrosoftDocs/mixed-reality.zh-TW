---
title: 學習模組共用 HoloLens 2 MR
description: 完成這個課程來了解如何實作 HoloLens 2 應用程式內的多使用者分享的經驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 8940de029ef5c67c38f427a238f88fcab527d79d
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328077"
---
# <a name="setting-up-photon"></a>設定 Photon

在這一課中，我們將了解如何做好準備，以建立共用的體驗 Photon Unity 網路功能 （自己使用這個雙關語） 匯入 Unity 專案。 Photon 是數個網路功能選項 Mixed Reality 開發人員可用來建立共用的體驗。 我們將帶領您學習建立 Photon 帳戶、 匯入 Photon，並建立選用的本機伺服器

目標：

* 了解如何建立 Photon 帳戶

* 了解如何尋找並匯入 Photon Unity 網路

* 設定本機的 Photon server

  

### <a name="setting-up-photon"></a>設定 Photon

1. 設定好[Photon](https://dashboard.photonengine.com/en-US/Account/SignUp)帳戶。 按一下瀏覽至 Photon 註冊頁面[此連結](https://dashboard.photonengine.com/en-US/Account/SignUp)。 若要建立的帳戶註冊頁面上，遵循的指示。 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

2. 一旦您已註冊，請按一下 Sdk。 當您在該頁面上，按一下在 [伺服器]，並確定它說 「 自我裝載。 」 然後向下捲動，然後按一下 [伺服器] 下方的第二個影像所示。

   

   ![Module3Chapter1step2aim](images/module3chapter1step2aim.PNG)

   ![Module3Chapter1step2bim](images/module3chapter1step2bim.PNG)
   
   3. 這會造成文字方塊中，會加上標籤，顯示 「 讀我 」。 請繼續並讀取它。 一旦完成，請按一下 「 downloadSDK 」，若要下載它旁邊的連結。


![Module3Chapter1step3im](images/module3chapter1step3im.PNG)

4. 完成下載之後，按兩下 資料夾。  檔案總管開啟後揭露 SDK 資料夾，請將複製的 SDK 資料夾。
   
   - 下一步是進入 windows c： 磁碟機，並建立新資料夾，稱為 「 伺服器 」。
   
   ![Module3Chapter1step4aim](images/module3chapter1step4aim.PNG)
   
   - 現在開啟資料夾，並貼上您之前複製的 SDK 資料夾。
   
   ![Module3Chapter1step4bim](images/module3chapter1step4bim.PNG)
   
5. 完成之後，開啟 [SDK] 資料夾，並移至 「 部署 」 的再"bin_Win64 」，然後按兩下 「 photon 控制項 」。


![Module3Chapter1step5im](images/module3chapter1step5im.PNG)

> 注意:如果您有任何疑問的 IP 位址或任何其他類似的問題，您可以找到大部分的資訊，在工具列中 （如圖所示） 即可。
>
> ![Module3Chapter1noteim](images/module3chapter1noteim.PNG)

6. 現在，伺服器已設定，並起始，回到 Photon 網站，並確定您仍登入 （或重新登入，如果您不。）按一下設定檔圖示 （右上角的下面的影像中進行 boxed 處理），然後選取 「 您的應用程式。 」
   

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

7. 按一下 [建立新的應用程式] 按鈕，以建立應用程式識別碼。

   ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

   - 選取"Photon 了絕佳 」 從下拉式功能表中，在 「 photon 類型 」。 然後為它命名，在此範例中，我們將它命名為"HoloLensPhotonProject。 」 完成之後，按一下 [建立] 按鈕。

   ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

8. 完成後，返回您的應用程式頁面，您應該會看到類似下圖。 按一下 應用程式識別碼，並將它複製。 貼上是您可以輕鬆存取的地方。  
   

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

9. 建立新的 unity 專案並將它命名為"HLSharingProject。 」 如需有關如何建立新的 Unity 專案的指示，請參閱[基底模組中的 < 建立 Unity 專案 > 一節](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project)。 


10. 專案載入後，按一下 「 資產存放區 」 索引標籤，如下圖所示。 然後，在下圖中反白顯示搜尋方塊中輸入 「 自己 」 使用這個雙關語，然後從搜尋結果中選取 「 Photon 自己使用這個雙關語 2 免費 」 的資產。 

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)
    
    11. 下載並匯入此資產藉由按下 「 下載 」 及 「 匯入 」 按鈕。
    
    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

## <a name="congratulations"></a>恭喜！

您已成功建立 Photon 帳戶、 設定本機 Photon 伺服器，並自己使用這個雙關語匯入 Unity。 下一步是要設定專案，然後允許與其他使用者的連線，這樣多個使用者可以看到您的工作。 

[下一課：第 2 課 Sharing(Photon)](mrlearning-sharing(photon)-ch2.md)

