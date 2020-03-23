---
title: 多使用者功能教學課程 - 4。 與多個使用者共用物件移動
description: 完成此課程以了解如何在 HoloLens 2 應用程式中實作使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: b0ddf0799fd94c29ce8f1221c55073cd77b63703
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031251"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4.與多個使用者共用物件移動

在本教學課程中，您將了解如何共用物件的移動，讓共用工作階段的所有參與者都可以共同作業及查看彼此的互動。 本課程以[基本模組教學課程](mrlearning-base.md)中所建立的登月小艇為基礎。

## <a name="objectives"></a>目標

- 帶入月球發射器以作為要共用的 3D 模型
- 設定專案來共用 3D 模型的移動
- 了解如何建立基本的多使用者共同作業應用程式

## <a name="instructions"></a>指示

1. 儲存上一課中的場景 (Control+S)。 您可以將其命名為 HLSharedProjectMainPart4，以便在需要時更容易找到。

2. 從 [專案] 視窗的 [資產] -> [指令碼] 資料夾中按兩下 [GenericNetSync]，從 Visual Studio 或您使用的程式碼編輯器中將其開啟。  

    ![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. 在第 34 和 38 行上移除 "//"，以針對您將在本課程中使用的資料表啟用程式碼。 接下來，儲存檔案。

    ![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. 在 [專案] 視窗中，按兩下 [資產] -> [指令碼] 資料夾中的 PhotonRoom.cs 檔案，在 Visual Studio 中將其開啟。

    ![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. 如同步驟 3，我們需要移除第 25、26 和 106 行上的 "//" 以啟動程式碼。

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png)

    ![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. 在 [階層] 視圖中，選取 NetworkRoom 物件。

    ![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. 在 [專案] 檢視中，瀏覽至 [資產] -> [資源] -> [Prefabs]。 首先，將資料表 Prefab 拖放到 PhotonRoom 類別上的 Tableprefab 位置。 接下來，將 RocketLauncherCompleteVariantprefab 拖放到 PhotonRoom 類別上的模組 Prefab 位置。

    ![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

    >[!NOTE]
    >如果您按一下其中一個 Prefab 物件和版本，偵測器就會切換至該物件。 按一下、拖放，然後將每個物件放到適當的位置。

8. 按一下 MixedRealityPlayspace 左邊的箭號，將子遊戲物件 MainCamera 向下移動到 SharedPlayground Prefab。 接下來，藉由選取 MixedRealityPlayspace Prefab 並在鍵盤上按一下 "delete" 來刪除該 Prefab。

    ![Module3hapter4step5im](images/module3chapter4step5im.PNG)

    >[!NOTE]
    >請確定主要相機和 SharedPlayground 位置都設定為 0,0,0。

9. 選取 SharedPlayground 物件，並按一下滑鼠右鍵來選擇 [建立空物件] 選項，將空白遊戲物件建立為 "SharedPlayground" 遊戲物件的子系。

   ![Module3chapter4step6im](images/module3chapter4step6im.PNG)

10. 在您的階層中選取新物件後，請在 [偵測器] 面板中將物件的名稱變更為 TableAnchor。 然後按一下 [新增元件]，並搜尋 TableAnchor 元件。 選取該元件並將其新增至物件。

    ![Module3Chapter4step7im](images/module3chapter4step7im.PNG)

11. 從 [專案] 面板的 [Prefabs] 資料夾中，將資料表 Prefab 拖曳至您剛才建立的 "TableAnchor" 子物件。

    ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

## <a name="congratulations"></a>恭喜！

完成後此課程後，請四處瀏覽以尋找登月小艇。 在此之後，加入 Unity 專案的所有使用者都可以四處移動月球發射器。  所有的移動都會進行同步，讓每個使用者都可以看到彼此的互動。 這些概念可為功能完整且共用的共同作業體驗提供基本構成要素。

雖然所有使用者都會連結為共用體驗的一部分，而且可以查看物件的相對移動，但應用程式仍無法精確地對齊虛擬人偶和物件，因此本機使用者無法看到實際世界中相同位置上的彼此和物件。 為了針對本機共用體驗建立錨點，每個裝置都需要對實體環境有共同的了解。 在此課程模組中，我們將使用 [Azure Spatial Anchors](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) 來達成此目的，這會在下一課中實作。

在繼續進行下一課之前，我們必須先完成 ASA 學習課程模組，其中涵蓋 ASA 基本概念、Azure 帳戶和資源建立，以及我們在將此整合到我們的共用體驗之前所需的其他基本構成要素。

[下一課：5.將 Azure Spatial Anchors 整合到共用體驗](mrlearning-sharing(photon)-ch5.md)
