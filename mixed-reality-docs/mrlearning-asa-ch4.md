---
title: MR 學習 ASA 模組上 HoloLens 2 Azure 空間的錨點
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: b29f27284c352d27fb1d4d4de701a1ebc2a7cd1c
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326821"
---
# <a name="photon-correct-me-if-im-wrong"></a>Photon （更正我如果我是錯誤）

在這一課中， 

目標：

* 了解如何 ___

* 了解如何 ___

  

## <a name="instructions"></a>指示

### <a name="setting-up-photon"></a>設定 Photon

1. 設定好[Photon](https://dashboard.photonengine.com/en-US/Account/SignUp)帳戶。 執行此動作將會包含輸入您的電子郵件，並透過一些驗證步驟。
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. 一旦您已註冊，請按一下 Sdk。 當您在該頁面上，按一下在 [伺服器]，並確定它說 「 自我裝載。 」 然後向下捲動，然後按一下 [伺服器] 下方的第二個影像所示。

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. 這會造成文字方塊中，會加上標籤，顯示 「 讀我 」。 請繼續並讀取它。 一旦完成，請按一下 「 downloadSDK 」，若要下載它旁邊的連結。


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. 完成下載之後，按兩下 資料夾。  檔案總管開啟後揭露 SDK 資料夾，請將複製的 SDK 資料夾。
   
   - 下一步是進入 windows c： 磁碟機，並建立新資料夾，稱為 「 伺服器 」。
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - 現在開啟資料夾，並貼上您之前複製的 SDK 資料夾。
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. 完成之後，開啟 [SDK] 資料夾，並移至 「 部署 」 的再"bin_Win64 」，然後按兩下 「 photon 控制項 」。


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> 注意:如果您有任何疑問的 IP 位址或任何其他類似的問題，您可以找到大部分的資訊，在工具列中 （如圖所示） 即可。
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. 現在，伺服器已設定，並起始，返回 Photon 網站 （在下圖中進行 boxed 處理） 的設定檔圖示上按一下，並選取 「 您的應用程式。 」
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. 按一下 [建立新的應用程式] 按鈕，以建立應用程式識別碼。

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - 從 「 photon 類型 」。 下的下拉式功能表中選取 Photon 執行 然後為它的名稱 （項目就會記住）。 在此範例中，我們將它命名為"HoloLensPhotonProject。 」 完成後，按一下 [建立]。

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. 完成後，返回您的應用程式頁面，您應該會看到類似下圖。 按一下 應用程式識別碼，並將它複製。 貼上是您可以輕鬆存取的地方。  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. 建立新的 unity 專案。 開啟 Unity 中樞，然後按一下 「 new 」。 它命名為"HLSharingProject。 」 然後按一下 [建立]。 

   > 注意：這可能需要 2 分鐘的時間載入，根據您的電腦速度。

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> 注意： 挑選一個位置來儲存您的專案中您的電腦，藉由變更 「 位置 」 選項。 請將它儲存到您將會記住，並能輕鬆存取的位置。

10. 專案載入後，按一下 「 資產存放區 」。 然後，在搜尋方塊中顯示在下圖中，輸入 「 自己 」 使用這個雙關語，然後選取 「 Photon 自己使用這個雙關語 2 免費 」 的資產。 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. 下載並匯入 ！
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a>**設定 Unity 專案** 

11. 下載新設定 Photon Unity 中，依序按一下所需的資產[這裡。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)

12. 在 Unity 中，按一下 資產 功能表並選取 「 匯入資產 」 然後按一下 「 自訂資產。 」

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. 選取您從步驟 1 中所提供的連結下載 Unity 套件。 一旦匯入 按鈕會出現在 Unity 中，按一下它。

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> 注意： 下載套件的任一處，將會在您找到。 上圖未顯示您將在其中找到封裝。

14. 建立新的場景 (這可以是使用控制項 / 命令 + N，或按一下 [檔案]，然後選取 「 新的場景。")。 將場景儲存為"HLSharedProjectMain。 」

> 注意： 您可能會收到看起來類似下面的影像的快顯視窗。 現在，只要按一下 [否。]
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. 在 「 混合實境工具組 」 中，按一下 "新增至場景，並設定 」。

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. 完成後完成時，新的組態檔會出現，讓您選擇以自訂設定檔。 按一下 複製和自訂 」。

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. 向下捲動，並取消核取 [啟用診斷系統]。 這會讓您更輕鬆地設定此專案。

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. 開啟 組建設定 （控制 + shift + B）。 請注意，此程式目前設定下的 「 個人電腦、 Mac 和 Linux 的獨立 」 平台。 此專案中，將 平台為 「 通用 windows 平台。 」 選取它，然後按一下 「 交換器平台。 」

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. 完成後，按一下 加入 開啟的場景。 方塊 現在請移至 [偵測器] 面板，並確定核取方塊右邊的 「 支援的虛擬實境"（如下圖所示） 會檢查。 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> 注意：也請確定 「 場景/HLSharedProjectMain 」 旁的核取方塊也會核取。

20. 底下的 「 發佈設定 」 偵測器 面板中捲動到 「 功能 」，並確定下列核取方塊會標示：

- 網際網路用戶端
- 網際網路用戶端伺服器
- 私人網路用戶端伺服器
- camera/webcam
- 麥克風

21. 如同步驟 12 中下, 一個步驟是匯入另一個稱為 「 第 2 課 」 可以在 [這裡]。 下載的自訂套件[lesson2.unitypackage 連結置於此處]匯入該套件。

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. 現在，在 [專案] 面板中，移至 「 prefabs"資料夾，因為在接下來的步驟中您會實作少數 prefabs 場景。 在 「 prefabs"資料夾中，按一下並拖曳 prefab，"DebugWindow 」 到階層。 完成之後，儲存專案 (按一下檔案，然後儲存檔案，或 control + S)

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> 注意：您可能會注意到快顯視窗會顯示當您按一下 prefab，詢問您關於 TMP Essentials。 將需要，請按一下 [匯入 TMP Essentials]。
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a>**連接多個使用者**

23. 如步驟 22，在 [專案] 面板中，「 prefabs"資料夾中的下一個步驟是拖放 「 NetworkLobby"prefab 至階層。 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. 當您開啟父 prefab，而"NetworkLobby 」，您應該會看到子系 prefab，「 NetworkRoom。 」 有了它選取，進入 [偵測器] 面板，並按一下 [新增元件]。 搜尋 「 PhotonView"，並將元件加入。

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. 階層 （以滑鼠右鍵按一下 階層 和 選取 「 空白 」） 中建立新的空白遊戲物件。 請確定位置設定為 x = 0，y = 0，z = 0，並命名物件，也就是 「 PhotonUser。 」

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a>恭喜！



