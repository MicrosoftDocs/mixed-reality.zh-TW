---
title: 學習模組共用 HoloLens 2 MR
description: 完成這個課程來了解如何實作 HoloLens 2 應用程式內的多使用者分享的經驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: a67eaef45582054b62198a563f0ee01724fd60db
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326999"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a>同步處理共用物件的移動

在這一課中，我們將了解如何共用物件的移動，以便在共用的工作階段的所有參與者都可以一起共同作業，並檢視其他人互動。 這一課為建置基礎所建置的一部分陰曆啟動器[基底模組的教學課程](mrlearning-base.md)。

目標：

- 作為要共用的 3D 模型匯入已完成的陰曆啟動器
- 將專案設定為共用的 3D 模型的移動。
- 了解如何建置基本的多使用者共同作業應用程式

### <a name="instructions"></a>指示

1. 在上一課 （control + S） 中儲存的場景。 您可能會為它命名"HLSharedProjectMainPart4.unity 」 讓您可更輕鬆地尋找當您再次需要它。

2. 刪除"NetworkLobby 」 物件 （方法是選取它，然後按下 delete 鍵）。 此外，進入 「 prefabs"資料夾，從第 2 課，並從該處也刪除 「 NetworkLobby"prefab。

![Module3Chapter4tep2im](images/module3chapter4step2im.PNG)

3. 匯入新的自訂封裝 （例如從第 2 課步驟 2），並匯入[LunarModule.unitypackage](linkforModule1 lesson with the lunar module)而[NetworkLobbyReplacement.unitypackage。](linkforNetworklobbyreplacement package here)

![Module3Chapter4step3im](images/module3chapter4step3im.PNG)

4. 現在，在 「 prefabs"資料夾中，拖曳至新的 「 NetworkLobby"prefab 階層。 

![Module3hapter4step4im](images/module3chapter4step4im.PNG)

> 注意： 我們在先前步驟中匯入的兩個封裝更新 「 NetworkLobby"prefab。 它可讓您打字的 ！

5. 現在，按一下 「 MixedRealityPlayspace 」 左邊的箭號，然後向下移動子遊戲物件、 「 MainCamera"到"SharedPlayground"prefab。 然後，刪除 prefab"MixedRealityPlayspace"（若要刪除選取的 prefab，點選您鍵盤上的 [刪除]）。

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

6. 建立新的遊戲物件設定為子物件 」 SharedPlayground"父物件 （用於建立新的物件，父物件，以滑鼠右鍵按一下並選取 [建立空白]）。
7. 在您階層中選取新的物件，將物件的名稱變更為"TableAnchor 」，在 [偵測器] 面板。 此外，按一下 [新增元件]，並搜尋"TableAnchor 」 元件。 選取它，並將它新增至物件。

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> 注意： 設定定位為 x = 1，y = 0.55 和 z = 2。 此外，設定 旋轉角度 y = 90。 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

8. 現在在 [專案] 面板中，在 「 prefabs"資料夾中，拖曳至 「 資料表 」 prefab 您剛才建立的 「 TableAnchor"子物件。

   ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

9. 選取 「 NetworkRoom"，"NetworkLobby 」 底下的子物件，在階層中，並按一下偵測器 面板和搜尋"PhotonView 」 中的 新增元件，新增指令碼，以 「*NetworkRoom*」 物件。

![Module3Chapter4step9im](images/module3chapter4step9im.PNG)

11. 最後，如果在 「 DebugWindow 」 物件中，您可以變更寬度為 80 及高度設為 10。

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a>恭喜！

這項操作完成，加入您的 Unity 專案的所有使用者可四處都移動陰曆的啟動器。 所有的移動會同步處理，讓每位使用者可以看到其他人互動。 這些概念做為基本建置組塊的完整共用的共同作業體驗。 

雖然所有的使用者連接共用體驗的一部分，而且可以看到的物件相對的移動，應用程式是仍然無法正確對齊虛擬人偶和物件，以便在實體內的相同位置的物件與彼此，請參閱 < 本機使用者世界。 若要錨定在本機的共用的體驗，每個裝置會需要的實體環境的共識。 在這個模組中，我們將會達到此目的使用[Azure 空間的錨點](<https://azure.microsoft.com/en-us/services/spatial-anchors/>)(ASA)，這將在下一課中實作。

下一課之前，我們必須完成 ASA 的學習模組，將會討論 ASA 基本概念，Azure 帳戶和資源建立，而其他基本的建築物區塊需要之前我們將這整合到我們分享經驗。

[下一課：第 5 課 Sharing(Photon)](mrlearning-sharing(photon)-ch5.md)

