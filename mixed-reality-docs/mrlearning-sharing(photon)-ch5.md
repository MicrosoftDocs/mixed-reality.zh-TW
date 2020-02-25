---
title: 多使用者功能教學課程-5。 將 Azure 空間錨點整合到共用體驗中
description: 完成此課程，以瞭解如何在 HoloLens 2 應用程式中執行多使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: c1b64b9d32409d61284f21ca216417ece4767d1b
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553806"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a>5. 將 Azure 空間錨點整合到共用體驗中

在這一課，您將瞭解如何將 Azure 空間錨點（ASA）整合到我們的共用體驗中。 如果實體環境是錨定虛擬經驗，讓所有參與者在相同的實體位置中看到物件，則 ASA 允許多個共置的裝置擁有共同的參考。

## <a name="objectives"></a>目標

* 將 ASA 整合到多裝置對齊的共用體驗。
* 瞭解 ASA 如何在本機共用體驗的內容中運作的基本概念。

## <a name="instructions"></a>指示

1. 選取 MixedRealityPlayspace 父物件底下的 [TableAnchor] prefab，然後將它刪除。

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. 在 專案 視圖中，移至 資產-> 資源-> Prefabs，然後將 TableAnchor prefab 拖曳至 SharedPlayground 物件上方，使其成為子系。

3. 展開 MixedRealityPlayspace 父物件 TableAnchor 物件，並同時展開 [按鈕] 物件。

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. 現在，在階層中選取 [ShareAzureAnchorButton]，並將您的注意力移至 [偵測器] 面板。 向下卷到下圖所示的下拉式功能表，選取 [AnchorModuleScript]，然後按一下 [ShareAnchorNetwork （）]。

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. 選取 [GetAzureAnchorButton] （請參閱步驟4），並將您的注意力移回 [偵測器] 面板。 向下卷到下圖中顯示的下拉式功能表，選取 [AnchorModuleScript]，按一下 [GetSharedAnchorNetwork （）]，然後 [儲存]。

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. 重複步驟4，將 StartAzureSession （）函式連結至 StartAzureSessionButton。

7. 重複步驟4，將 CreateAzureAnchor （）函式連結至 CreateAzureAnchorButton，並確認 TableAnchor 物件已指派給函式的參數 ' 遊戲物件 ' 欄位。

8. 遵循將[場景連線至 azure 資源](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource)指示，以新增您的 Azure 空間錨點服務認證。

9. 若要測試共用模組，請按一下 [啟動 Azure ASA 會話] 按鈕，這會啟動 azure 空間錨點會話，然後按一下 [建立 Azure 錨點] 按鈕來建立 azure 錨點。 等候 azure 錨點建立。 建立 azure 錨點之後，請按一下 [共用 Azure 錨點] 按鈕，從 HoloLens 共用建立的 azure 錨點。

10. 若要在另一部 HoloLens 中接收共用的 azure 錨點，請按一下 [啟動 Azure ASA 會話] 以啟動並進入目前的 ASA 會話

11. 按一下 [取得 Azure 錨點] 按鈕，以從其他 HoloLens 取得共用的 Azure 錨點。

## <a name="congratulations"></a>恭喜

在這一課，您已瞭解如何整合 Azure 的強大新空間錨點，以將共置的裝置對齊共用體驗！ 這也會結束共用模組。 我們已瞭解如何設定新的 Photon 帳戶、將 Photon 和雙關語整合到新的 Unity 應用程式、設定虛擬人偶和共用物件，最後使用 ASA 來對齊多個參與者。
