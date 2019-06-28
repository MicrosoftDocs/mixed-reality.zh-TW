---
title: 學習模組共用 HoloLens 2 MR
description: 完成這個課程來了解如何實作 HoloLens 2 應用程式內的多使用者分享的經驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 33f265c6333f12f7ec73ecb0c1e5730b168d4bde
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415909"
---
# <a name="connecting-multiple-users"></a>**連接多個使用者** 

在這一課中，我們將了解如何連接多個使用者，即時分享經驗的一部分。 本課程結束時，您都能夠開啟多個裝置上的應用程式，並查看的聯結 （頭像球體所表示）。 每個人的 「 虛擬人偶 」 表示法 

目標：

- 在您的應用程式內設定了絕佳
- 設定播放程式
- 了解如何連接多個使用者分享經驗

### <a name="instructions"></a>指示

1. 在資產中 > 資源 > Prefabs 資料夾的 [專案] 面板、 拖曳和卸除 「 NetworkLobby"prefab 在階層中，如下圖所示。


   ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. 當您展開 prefab"NetworkLobby 」 時，您應該會看到子物件呼叫 「 NetworkRoom。 」 有了它選取，進入 [偵測器] 面板，並按一下 [新增元件]。 搜尋 「 PhotonView"，並將元件加入。

   ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. 在階層中建立新的空白遊戲物件 （在階層中以滑鼠右鍵按一下並從內容功能表中選取 [清理]）。 請確定位置設定為 x = 0，y = 0，z = 0，並命名物件，也就是 「 PhotonUser。 」

   ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. 按一下 新增元件 按鈕，輸入 「 一般的淨同步 」 並選取 一般的淨同步處理類別。 一旦此類別會顯示，按一下 [使用者] 核取方塊，將它開啟。 

   ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. 再次按一下 [新增元件] 然後輸入 「 Photon 檢視 」 並選取 Photon 檢視類別出現在下拉式清單中。

   ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. 現在，為一般的淨同步處理類別中的檔案圖示上按一下然後拖曳它 Photon 檢視的 [觀察到的元件] 欄位。 ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png) 

7. 接下來，我們想要建立來代表每個聯結分享的經驗的人員所置放的球體。 以滑鼠右鍵按一下您剛才建立的 「 PhotonUser"物件往下移到 「 3D 物件 」，按一下 "球紋。 」 這會建立圓球的遊戲物件為 PhotonUser 物件的子系。

   ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. 調整到 x 球體 = $0.06，y = $0.06，ad z = $0.06。

   ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. 將"PhotonUser 」 遊戲物件拖曳至 [專案] 面板中的 「 prefabs"資料夾。 然後，刪除從場景。 我們現在已建立時產生，或具現化新的播放程式分享經驗中，會使用 prefab。

   ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> 注意： 請確定，遊戲物件已成功複製到 「 prefabs"資料夾中刪除從您的階層之前。

10. （使用類似的步驟 3 的指示），階層中建立新的物件並將它命名為"SharedPlayground。 」 然後，按一下 [新增元件]，並搜尋 「 一般網路管理員 」，然後按一下以新增泛型網路管理員元件。 將物件的位置變更為 x = 0，y = 0，且 z = 0。

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a>恭喜！

一旦上述所有步驟都已完成，而在建置程序完成時，按下 [播放] 按鈕，並連接 HoloLens 2 時，您應該會看到球體四處移動，當您移動您 ！ 這會顯示任何使用者加入您的 Unity 專案 ！

[下一課：第 4 課 Sharing(Photon)](mrlearning-sharing(photon)-ch4.md)

