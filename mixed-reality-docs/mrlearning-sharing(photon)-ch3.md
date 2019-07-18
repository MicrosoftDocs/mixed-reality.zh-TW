---
title: HoloLens 2 的 MR 學習共用模組
description: 完成此課程, 以瞭解如何在 HoloLens 2 應用程式中執行多使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 92bea1f3130f67645c10e36fe40cd4bc6f8b9151
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293659"
---
# <a name="connecting-multiple-users"></a>連接多個使用者

在這一課, 我們將瞭解如何在即時共用體驗中連接多個使用者。 在本課程結束時, 您將能夠在多個裝置上開啟應用程式, 並查看每個聯結人員的標記法, 以球體表示。 

目標

- 在您的應用程式中設定雙關語
- 設定播放者
- 瞭解如何在共用體驗中連接多個使用者

### <a name="instructions"></a>指示

1. 在 [資產-> 資源]-[專案] 面板的 [> Prefabs] 資料夾中, 將 NetworkLobby prefab 拖放到階層中, 如下圖所示。

![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. 當您展開 [NetworkLobby] 時, 您會看到名為 NetworkRoom 的子物件。 選取 NetworkRoom 後, 進入 [檢查] 面板, 然後按一下 [新增元件]。 搜尋 PhotonView 並新增元件。

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. 在階層中建立新的空白遊戲物件。 在階層中按一下滑鼠右鍵, 然後從內容功能表中選取 [空白]。 請確定定位設定為 x = 0、y = 0、z = 0, 並將物件命名為 PhotonUser。

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. 按一下 [新增元件], 然後輸入一般 Net Sync。選取 [一般 Net Sync] 類別。 當類別出現時, 按一下 [使用者] 核取方塊以開啟它。 

![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. 再次按一下 [新增元件], 然後輸入 Photon View。 選取出現在下拉式清單中的 [Photon] View 類別。

![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. 按一下 [一般 Net Sync] 類別的 [檔案] 圖示。 將它拖放到 [Photon] 視圖的 [觀察的元件] 欄位中。 

![module3chapter3updateStep6im .png](images/module3chapter3updateStep6im.png) 

7. 接下來, 我們會建立球體來代表加入共用體驗的每個人。 以滑鼠右鍵按一下您剛才建立的 PhotonUser 物件, 並 scrolldown 至 [3D 物件], 然後按一下 [球體]。 這會將球體遊戲物件建立為 PhotonUser 物件的子系。

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. 將球體向下調整為 x = 0.06、y = 0.06、ad z = 0.06。

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. 將 [PhotonUser 遊戲] 物件拖曳至 [專案] 面板中的 [Prefabs] 資料夾, 然後從場景中刪除它。 我們現在建立了一個 prefab, 可在建立或具現化共用體驗中的新玩家時使用。

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> 注意: 請確定遊戲物件已成功複製到 Prefabs 資料夾, 然後才將它從您的階層中刪除。

10. 遵循步驟3中的指示, 在階層中建立新的物件, 並將其命名為 SharedPlayground。 接著, 按一下 [新增元件], 並搜尋 [一般網路系統管理員], 然後按一下以新增 [一般網路系統管理員] 元件。 將物件的位置變更為 x = 0、y = 0、z = 0。

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a>恭喜！

完成上述所有步驟之後, 建立程式也會完成, 請按下 [播放] 按鈕並連接您的 HoloLens 2。 當您移動 head 時, 您應該會看到一個球體四處移動。 這會針對加入 Unity 專案的任何使用者顯示!

[下一課：共用 (Photon) 第4課](mrlearning-sharing(photon)-ch4.md)

