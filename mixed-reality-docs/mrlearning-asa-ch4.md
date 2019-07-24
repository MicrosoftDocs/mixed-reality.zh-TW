---
title: MR Learning ASA 模組 Azure 空間錨點 on HoloLens 2
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
# <a name="photon-correct-me-if-im-wrong"></a>Photon (如果發生錯誤, 請更正)

在這一課, 

目標

* 瞭解如何 _____________________________________________

* 瞭解如何 _________________________________________________

  

## <a name="instructions"></a>指示

### <a name="setting-up-photon"></a>設定 Photon

1. 設定[Photon](https://dashboard.photonengine.com/en-US/Account/SignUp)帳戶。 這麼做是由輸入您的電子郵件, 以及進行一些驗證步驟所組成。
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. 註冊之後, 請按一下 [Sdk]。 一旦您在該頁面上, 請按一下 [伺服器], 並確定它顯示「自我裝載」。 然後向下滾動並按一下 [伺服器], 如下圖中的第二個影像所示。

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. 這會使文字方塊出現標記為「大聲朗讀」。 請繼續閱讀。 完成後, 按一下 [downloadSDK] 旁邊的連結以下載。


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. 完成下載後, 請按兩下資料夾。  當您的檔案瀏覽器開啟並顯示 SDK 資料夾之後, 請複製 [SDK] 資料夾。
   
   - 您的下一個步驟是進入 windows C: 磁片磁碟機, 並建立名為 ' server ' 的新資料夾。
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - 現在開啟資料夾, 並貼上您稍早複製的 SDK 資料夾。
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. 完成之後, 請開啟 SDK 資料夾並移至 [部署], 然後按一下 [bin_Win64], 再按兩下 [photon 控制項]。


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> 注意:如果您有任何有關 IP 位址或任何其他類似問題的問題, 您可以在工具列中找到大部分的資訊 (如下圖所示)。
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. 現在已設定並起始伺服器, 請回到 Photon 網站, 然後按一下設定檔圖示 (下圖中的方塊), 再選取 [您的應用程式]。
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. 按一下 [建立新的應用程式] 按鈕, 以建立應用程式識別碼。

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - 從 [Photon 類型] 底下的下拉式功能表中選取 [Photon 執行]。 然後為它命名 (您會記住的東西)。 在此範例中, 我們將它命名為 "HoloLensPhotonProject"。 完成後, 按一下 [建立]。

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. 完成後, 請返回您的應用程式頁面, 您應該會看到類似下圖的內容。 按一下 [應用程式識別碼] 並加以複製。 貼入您可以輕鬆存取的位置。  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. 建立新的 unity 專案。 開啟 Unity 中樞, 然後按一下 [新增]。 將它命名為 "HLSharingProject"。 然後按一下 [建立]。 

   > 下視電腦的速度而定, 最多可能需要2分鐘的時間才能載入。

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> 注意: 藉由變更 [位置] 選項, 選擇在電腦中儲存專案的位置。 將它儲存到您將記得且容易存取的位置。

10. 專案載入後, 按一下 [資產] 存放區。 然後, 在下圖所示的搜尋方塊中, 輸入 "雙關語", 然後選取 [Photon 雙關語-2 FREE] 資產。 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. 下載並匯入!
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a>**設定 Unity 專案** 

11. 按一下這裡, 下載在 Unity 中設定 Photon 所需的新資產[。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)

12. 在 Unity 中, 按一下 [資產] 功能表並選取 [匯入資產], 然後按一下 [自訂資產]。

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. 從步驟1所提供的連結中, 選取您剛才下載的 Unity 套件。 一旦 [匯入] 按鈕出現在 Unity 中, 請按一下它。

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> 注意: 您將套件下載到的任何位置都將是您找到它的地方。 上圖不會說明您會在何處找到封裝。

14. 建立新的場景 (這可以使用 control/command + N 來完成, 或按一下 [檔案], 然後選取 [新增場景])。 將場景儲存為 "HLSharedProjectMain"。

> 注意: 您可能會收到類似下圖的快顯視窗。 現在, 只要按一下 [否] 即可。
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. 在 [混合式現實工具組] 底下, 按一下 [新增至場景並設定]。

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. 完成之後, 就會出現新的設定檔案, 讓您選擇自訂設定檔。 按一下 [複製並自訂]。

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. 向下並取消選取 [啟用診斷系統]。 這可讓您更輕鬆地設定此專案。

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. 開啟 [組建設定] (ctrl + shift + B)。 請注意, 程式目前是在「電腦、Mac 和 Linux 獨立」平臺下設定。 針對此專案, 請將平臺設定為「通用 windows 平臺」。 選取它, 然後按一下 [切換平臺]。

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. 完成後, 請按一下顯示「新增開啟場景」的方塊。 現在, 請移至 [偵測器] 面板, 並確定已核取 [支援的虛擬實境] 右邊的核取方塊 (如下圖所示)。 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> 下同時也請確定已核取 [場景/HLSharedProjectMain] 旁的核取方塊。

20. 在 [偵測器] 面板中的 [發行設定] 底下, 向下滾動到 [功能], 並確定只會標示下列核取方塊:

- 網際網路用戶端
- 網際網路用戶端伺服器
- 私人網路用戶端伺服器
- 相機/網路攝影機
- 麥克風

21. 就像步驟12一樣, 下一個步驟是匯入另一個名為 "第2課" 的自訂套件, 您可以在這裡下載 [這裡]。[第2課. unitypackage link 這裡]匯入該套件。

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. 現在, 在 [專案] 面板中, 移至 "prefabs" 資料夾, 因為在接下來的幾個步驟中, 您將會在場景中執行幾個 prefabs。 在 "prefabs" 資料夾中, 按一下 prefab, 將 "DebugWindow" 拖曳至階層中。 完成後, 儲存專案 (依序按一下 [檔案]、[儲存] 或 [控制 + S])

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> 下您可能會注意到當您按一下 prefab 時, 快顯視窗會詢問您有關 TMP Essentials 的資訊。 如有需要, 請按一下 [匯入 TMP Essentials]。
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a>**連接多個使用者**

23. 就像步驟 22, 在 [專案] 面板的 [prefabs] 資料夾中, 下一個步驟是將 "NetworkLobby" prefab 拖放到階層中。 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. 當您開啟父 prefab "NetworkLobby" 時, 您應該會看到子 prefab "NetworkRoom"。 選取此選項後, 進入 [檢查] 面板, 然後按一下 [新增元件]。 搜尋 "PhotonView" 並新增元件。

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. 在階層中建立新的空白遊戲物件 (以滑鼠右鍵按一下階層中, 然後選取 [空的])。 請確定定位設定為 x = 0、y = 0、z = 0, 並將物件命名為 "PhotonUser"。

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a>恭喜！



