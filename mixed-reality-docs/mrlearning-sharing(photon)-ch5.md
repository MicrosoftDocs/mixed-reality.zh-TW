---
title: 學習模組共用 HoloLens 2 MR
description: 完成這個課程來了解如何實作 HoloLens 2 應用程式內的多使用者分享的經驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 9f4a0c0cc37ab097a60c44891d56fa65f6032418
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326997"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a>Azure 空間的錨點和共用的經驗

在這一課中，我們將了解如何將 Azure 空間的錨點 (ASA) 整合到我們分享經驗。 ASA 允許多個位於相同位置的裝置，其以虛擬的錨點的實體環境體驗，所有參與者都看到相同的實體位置中的物件有共識。

繼續進行這一課之前，我們必須完成 ASA 的學習模組，將討論 ASA 基本概念、 Azure 帳戶並建立資源和其他我們可以將 ASA 整合到我們分享經驗之前所需的基本建築物區塊。

目標：

- 將 ASA 整合到 multi-device 對齊的共用體驗
- 了解 ASA 本機的共用經驗的內容中的運作方式的基本概念

### <a name="instructions"></a>指示

1. 將專案儲存在上一課 （control + S），並命名"HLSharedProjectMainPart5.unity 」 以便更輕鬆地尋找當您再次需要它。

2. 選取 TableAnchor prefab 底下 「 MixedRealityPlayspace"的父物件，並將它刪除。

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3. 如同某些先前的課程中，匯入新的自訂封裝，您可以取得[這裡。](placeholderlink)

![Module3Chapter5step3im](images/module3chapter5step3im.PNG)

4. 它匯入之後，從 [專案] 面板中的 「 prefabs"資料夾抓取 （從上一個步驟中匯入 unity 封裝） 的新更新的資料表錨點和拖放到父物件 「 MixedRealityPlayspace。 」

![Module3hapter5step4im](images/module3chapter5step4im.PNG)

5. 展開 「 MixedRealityPlayspace"的父物件，則 「 TableAnchor 」 物件，然後展開的 「 按鈕 」 物件。 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

6. 現在在階層中，選取 「 ShareAzureAnchorButton"並移動您注意到 [偵測器] 面板。 向下捲動，如下圖所示的下拉式功能表並選取 「 AnchorModuleScript 」 並按一下 「 ShareAnchorNetework()。 」

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

7. 如同步驟 6 中，選取 「 GetAzureAnchorButton"並移動您回到 [偵測器] 面板的注意。 向下捲動，如下圖所示的下拉式功能表並選取 「 AnchorModuleScript 」 並按一下 「 GetSharedAnchorNetwork()。 」 然後儲存。

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a>恭喜！

在這一課，您了解如何整合 Azure 的強大新空間錨點來對齊共的裝置共用體驗中的內容 ！ 這一課也結束時，共用的模組。 我們了解如何設定新的 Photon 帳戶，請將 Photon 與自己使用這個雙關語整合到新的 Unity 應用程式中，設定虛擬人偶 」 和 「 共用的物件，以及最後對齊這些使用 ASA 的多個參與者。 

