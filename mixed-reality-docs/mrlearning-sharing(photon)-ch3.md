---
title: 多使用者功能教學課程 - 3。 連線多個使用者
description: 完成此課程以了解如何在 HoloLens 2 應用程式中實作使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: cbe0d8d2db6c34ba262fe9c946b68366ed3dbb93
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031224"
---
# <a name="3-connecting-multiple-users"></a>3.連線多個使用者

在這一課中，我們將了解如何在即時共用體驗中連線多個使用者。 在本課程結束時，您將能夠在多個裝置上開啟應用程式，並看到每個加入人員的虛擬人偶 (以球體呈現)。

## <a name="objectives"></a>目標

* 在您的應用程式中設定 PUN
* 設定玩家
* 了解如何在共用體驗中連線多個使用者

## <a name="instructions"></a>指示

1. 在 [專案] 面板的 [資產] -> [資源] -> [Prefabs] 資料夾中，將 NetworkLobby Prefab 拖放到階層中，如下圖所示。

    ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. 當您展開 [NetworkLobby] 時，您會看到名為 NetworkRoom 的子物件。 選取 NetworkRoom 後，進入 [偵測器] 面板，然後按一下 [新增元件]。 搜尋 PhotonView 並新增元件。

    ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. 在階層中建立新的空白遊戲物件。 以滑鼠右鍵按一下階層，然後從內容功能表中選取 [空白]。 請確定定位已設定為 x = 0、y = 0、z = 0，並將物件命名為 PhotonUser。

    ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. 按一下 [新增元件]，然後輸入 Generic Net Sync。選取 [Generic Net Sync] 類別。 當該類別出現時，按一下 [使用者] 核取方塊以將其開啟。

    ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. 再次按一下 [新增元件]，然後輸入 Photon View。 選取出現在下拉式清單中的 [Photon View] 類別。

    ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. 按一下 [Generic Net Sync] 類別的 [檔案] 圖示。 將其拖放到 Photon View 的 [觀察的元件] 欄位中。

    ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png)

7. 接下來，我們會建立球體來代表加入共用體驗的每個人。 在您剛才建立的 PhotonUser 物件上按一下滑鼠右鍵，並向下捲動至 [3D 物件]，然後按一下 [球體]。 這會將球體遊戲物件建立為 PhotonUser 物件的子系。

    ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. 將球體縮小為 x = 0.06、y = 0.06 及 z = 0.06。

    ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. 將 PhotonUser 遊戲物件拖曳至 [專案] 面板中的 [Prefabs] 資料夾，然後從場景中將其刪除。 您現在已建立可在共用體驗中產生或具現化新玩家時使用的 Prefab。

    ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

    >[!NOTE]
    >請先確定遊戲物件已成功複製到 Prefabs 資料夾，再將其從您的階層中刪除。

10. 遵循步驟 3 的指示，在階層中建立新的物件，並將其命名為 SharedPlayground。 然後，按一下 [新增元件]，並搜尋 Generic network manager。  再次按一下該項目以新增 Generic Network Manager 元件。 將物件的位置變更為 x = 0、y = 0、z = 0。

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)

## <a name="congratulations"></a>恭喜！

完成上述所有步驟且組建程序也完成之後，請按下 [開始遊戲] 按鈕並連結您的 HoloLens 2。 當您移動頭部時，您應該會看到一個球體四處移動。 這會向加入 Unity 專案的任何使用者顯示！

[下一課：4.與多個使用者共用物件移動](mrlearning-sharing(photon)-ch4.md)
