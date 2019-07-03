---
title: 學習模組共用 HoloLens 2 MR
description: 完成這個課程來了解如何實作 HoloLens 2 應用程式內的多使用者分享的經驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 44cc41b10ed79d3085ec601ec9cf21af47b0fea5
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523301"
---
# <a name="connecting-multiple-users"></a>連接多個使用者

在這一課中，我們了解如何連接多個使用者，即時分享經驗的一部分。 本課程結束時，您可以開啟多個裝置上的應用程式，並查看 顯示圖片，由球體，聯結每個人的表示法。 

目標：

- 在您的應用程式內設定了絕佳
- 設定播放程式
- 了解如何連接多個使用者分享經驗

### <a name="instructions"></a>指示

1. 在 [資產]-> [資源]-> [專案] 面板中的 Prefabs 資料夾、 拖曳和卸除在 NetworkLobby prefab 至階層，如下圖所示。


   ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. 當您展開 NetworkLobby 時，您會看到呼叫 NetworkRoom 子物件。 選取的 NetworkRoom，進入 偵測器 面板中，然後按一下 新增元件。 搜尋 PhotonView 並新增此元件。

   ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. 建立新的空白遊戲物件階層架構中。 在階層中，以滑鼠右鍵按一下，並從操作功能表中選取 空白。 請確定位置設定為 x = 0，y = 0，z = 0，並命名物件，PhotonUser。

   ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. 按一下 新增元件，並輸入一般的淨同步處理。選取 一般的淨同步處理類別。 類別的出現時，按一下 [使用者] 核取方塊，將它開啟。 

   ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. 同樣地，按一下新增元件，然後鍵入 Photon 檢視。 選取 Photon 檢視類別出現在下拉式清單中。

   ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. 按一下 [檔案] 圖示，一般的淨同步處理類別。 將拖放 Photon 檢視的觀察到的元件 欄位中。 ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png) 

7. 接下來，我們會建立置放的球體來代表每個聯結分享的經驗的人員。 以滑鼠右鍵按一下您剛才建立的 PhotonUser 物件及要 scrolldown"3D 物件，然後按一下 球紋。 這會建立圓球的遊戲物件為 PhotonUser 物件的子系。

   ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. 調整到 x 球體 = $0.06，y = $0.06，ad z = $0.06。

   ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. PhotonUser 遊戲物件拖曳至 [專案] 面板中，在 Prefabs 資料夾，然後刪除它從場景。 我們現在已建立時產生，或具現化新的播放程式分享經驗中可以使用 prefab。

   ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> 注意： 確定遊戲物件已成功複製到 Prefabs 資料夾之前從階層中刪除。

10. 建立新的物件階層架構中，依照步驟 3 中的指示，並將它命名為 SharedPlayground。 然後，按一下 [新增元件，和一般網路管理員] 中，搜尋，然後按一下要新增 「 一般網路管理員元件。 將物件的位置變更為 x = 0，y = 0，且 z = 0。

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a>恭喜！

上述所有步驟都都完成時，並在建置程序也已完成之後, 按下 [播放] 按鈕，並連接 HoloLens 2。 您應該會看到四處移動，當您移動您的球體。 這會顯示任何使用者加入您的 Unity 專案 ！

[下一課：第 4 課 Sharing(Photon)](mrlearning-sharing(photon)-ch4.md)

