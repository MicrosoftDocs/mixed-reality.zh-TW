---
title: 多使用者功能教學課程-4。 與多個使用者共用物件移動
description: 完成此課程, 以瞭解如何在 HoloLens 2 應用程式中執行多使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 2e676d319ba7221cf9549b200b3d748f26025aa7
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701909"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4.與多個使用者共用物件移動

在本教學課程中, 我們將瞭解如何共用物件的移動, 讓共用會話的所有參與者都可以共同合作, 並查看彼此的互動。 這一課是以[基本模組教學](mrlearning-base.md)課程中建立的陰曆啟動器為基礎。

目標

- 帶入陰曆啟動器作為要共用的3D 模型
- 將您的專案設定為共用3D 模型的移動。
- 瞭解如何建立基本的多使用者協同作業應用程式

## <a name="instructions"></a>指示


1. 從上一課 (Control + S) 儲存場景。 您可以將它命名為 HLSharedProjectMainPart4, 以便在需要時更容易找到。

2. 從 [專案] 視窗的 [資產-> 腳本] 資料夾中, 按兩下 [GenericNetSync], 在 Visual Studio 或您使用的程式碼編輯器中開啟它。  

![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. 在行34和38上, 移除//以啟動我們將在此課程中使用之資料表的程式碼。 接下來, 儲存檔案。 

![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. 在 [專案] 視窗中, 按兩下 [資產-> 腳本] 資料夾中的 PhotonRoom.cs 檔案, 在 Visual Studio 中將它開啟。 

![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. 就像在步驟3中, 我們需要移除//以在第25、26和106行啟用程式碼。

![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png) 

![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. 在 [階層] 視圖中, 選取 [NetworkRoom] 物件。

![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. 在 專案 視圖中, 流覽至 資產-> 資源-> Prefabs。 首先, 將資料表 prefab 拖放到 PhotonRoom 類別上的 Tableprefab 位置。 接下來, 將 RocketLauncherCompleteVariantprefab 拖放到 PhotonRoom 類別上的模組 Prefab 位置。

![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

   注意:如果您按一下其中一個 prefab 物件和 [釋放], 則偵測器會切換至該物件。 按一下、拖放, 然後將每個物件釋放到適當的位置。

8. 按一下 [MixedRealityPlayspace] 左邊的箭號, 然後將 [子遊戲] 物件向下 MainCamera 至 [SharedPlayground] prefab。 接下來, 刪除 prefab、MixedRealityPlayspace、刪除、選取 prefab, 然後在您的鍵盤上點一下 [刪除]。
![Module3hapter4step5im](images/module3chapter4step5im.PNG)

>注意:請確定主要相機和 SharedPlayground 位置都設定為 0, 0, 0。
>

9. 建立新的遊戲物件集, 做為 SharedPlayground 父物件的子物件, 以建立新的物件。 以滑鼠右鍵按一下父物件, 然後選取 [建立空的]。 

10. 在您的階層中選取新的物件後, 請在 [偵測器] 面板中將物件的名稱變更為 TableAnchor。 此外, 按一下 [新增元件], 然後搜尋 TableAnchor 元件。 選取它, 並將它新增至物件。 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

11. 現在, 從 [Prefabs] 資料夾的 [專案] 面板中, 將資料表 prefab 拖曳至您剛才建立的 "TableAnchor" 子物件。

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

12. 最後, 在 DebugWindow 物件中, 將 [寬度] 變更為 50, 並將 [高度] 變更為20。

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)

## <a name="congratulations"></a>恭喜！


完成後, 加入 Unity 專案的所有使用者都可以移動陰曆啟動器。 所有的移動都會同步處理, 讓每個使用者都可以看到彼此的互動。 這些概念可做為全功能、共用共同作業體驗的基本組建區塊。 

雖然所有使用者都是以共用體驗的一部分進行連線, 而且可以查看物件的相對移動, 但應用程式仍無法精確地對齊虛擬人偶和物件, 讓本機使用者可以在實體中的相同位置看到彼此和物件成為. 為了錨定本機共用體驗, 每個裝置都需要對實體環境有共同的瞭解。 在此課程模組中, 我們將使用將在下一課中實行的[Azure 空間錨點](<https://azure.microsoft.com/en-us/services/spatial-anchors/>)(ASA) 來達到此目的。

在繼續進行下一課之前, 我們必須先完成 ASA 學習課程模組, 其中涵蓋 ASA 基本概念、Azure 帳戶和資源建立, 以及其他所需的基本建築物組塊, 才可將其整合到我們的共用體驗。

[下一課：5.將 Azure Spatial Anchors 整合到共用體驗](mrlearning-sharing(photon)-ch5.md)

