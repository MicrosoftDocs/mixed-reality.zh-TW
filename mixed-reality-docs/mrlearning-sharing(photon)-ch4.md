---
title: 學習模組共用 HoloLens 2 MR
description: 完成這個課程來了解如何實作 HoloLens 2 應用程式內的多使用者分享的經驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: d5bed61f5ffc1d3b4efed96f47c3568fbf3a2948
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416009"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a>同步處理共用物件的移動

在這一課中，我們將了解如何共用物件的移動，以便在共用的工作階段的所有參與者都可以一起共同作業，並檢視其他人互動。 這一課為建置基礎所建置的一部分陰曆啟動器[基底模組的教學課程](mrlearning-base.md)。

目標：

- 將 3D 模型到共用陰曆啟動器
- 將專案設定為共用的 3D 模型的移動。
- 了解如何建置基本的多使用者共同作業應用程式

### <a name="instructions"></a>指示

1. 在上一課 （control + S） 中儲存的場景。 您可能會為它命名"HLSharedProjectMainPart4.unity 」 讓您可更輕鬆地尋找當您再次需要它。

2. 在 [專案] 視窗中，在資產中 > Scripts 資料夾中，按兩下 GenericNetSync 在 Visual Studio，或用過程式碼會使用的編輯器中開啟它。  ![](images/module3chapter4updatestep2.png)

3. 同行 34 和 38，移除"/ / 」 啟用程式碼，我們將在這一課使用的資料表。  然後儲存檔案。 ![](images/module3chapter4updatestep3.png)

4. 在 專案 視窗中，按兩下 在資產中 PhotonRoom.cs 歸檔 > 若要再次開啟 Visual Studio 中的 指令碼 資料夾。 ![](images/module3chapter4updatestep4.png)

5. 就像在步驟的 3 中我們需要移除"/ /"啟用位於第 25、 26 和 106 行程式碼。![](images/module3chapter4updatestep5a.png) ![](images/module3chapter4updatestep5b.png)

6. 在階層檢視中，選取 NetworkRoom 物件。![](images/module3chapter4updatestep6.png)

7. 在 專案 檢視中，瀏覽至 資產 > 資源 > Prefabs。 首先，拖放資料表 prefab PhotonRoom 類別上的 「 Tableprefab"插槽。 接下來將拖放 LunarModule prefab PhotonRoom 類別上的 「 模組 Prefab"插槽。 ![](images/module3chapter4updatestep7.png)

   注意:如果您按一下其中一個 prefab 物件和版本，偵測器會切換至該物件。 按一下、 拖放並釋放每個物件至其適當的位置。



8. 現在，按一下 「 MixedRealityPlayspace 」 左邊的箭號，然後向下移動子遊戲物件、 「 MainCamera"到"SharedPlayground"prefab。 然後，刪除 prefab"MixedRealityPlayspace"（若要刪除選取的 prefab，點選您鍵盤上的 [刪除]）。

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

注意：請確定將 Main Camera 與 SharedPlayground 的位置會設定成 0,0,0。

9. 建立新的遊戲物件設定為子物件 」 SharedPlayground"父物件 （用於建立新的物件，父物件，以滑鼠右鍵按一下並選取 [建立空白]）。 

10. 在您階層中選取新的物件，將物件的名稱變更為"TableAnchor 」，在 [偵測器] 面板。 此外，按一下 [新增元件]，並搜尋"TableAnchor 」 元件。 選取它，並將它新增至物件。 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> 注意： 設定定位為 x = 1，y = 0.55 和 z = 2。 此外，設定 旋轉角度 y = 90。 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. 現在在 [專案] 面板中，在 「 prefabs"資料夾中，拖曳至 「 資料表 」 prefab 您剛才建立的 「 TableAnchor"子物件。

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. 最後，如果在 「 DebugWindow 」 物件中，您可以變更寬度為 80 及高度設為 10。

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a>恭喜！

這項操作完成，加入您的 Unity 專案的所有使用者可四處都移動陰曆的啟動器。 所有的移動會同步處理，讓每位使用者可以看到其他人互動。 這些概念做為基本建置組塊的完整共用的共同作業體驗。 

雖然所有的使用者連接共用體驗的一部分，而且可以看到的物件相對的移動，應用程式是仍然無法正確對齊虛擬人偶和物件，以便在實體內的相同位置的物件與彼此，請參閱 < 本機使用者世界。 若要錨定在本機的共用的體驗，每個裝置會需要的實體環境的共識。 在這個模組中，我們將會達到此目的使用[Azure 空間的錨點](<https://azure.microsoft.com/en-us/services/spatial-anchors/>)(ASA)，這將在下一課中實作。

下一課之前，我們必須完成 ASA 的學習模組，將會討論 ASA 基本概念，Azure 帳戶和資源建立，而其他基本的建築物區塊需要之前我們將這整合到我們分享經驗。

[下一課：第 5 課 Sharing(Photon)](mrlearning-sharing(photon)-ch5.md)

