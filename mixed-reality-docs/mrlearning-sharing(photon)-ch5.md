---
title: 學習模組共用 HoloLens 2 MR
description: 完成這個課程來了解如何實作 HoloLens 2 應用程式內的多使用者分享的經驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 2a16d318c6d749bcbf6ed9db0d6cd2228a6ea06e
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465207"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a>Azure 空間的錨點和共用的經驗

在這一課中，我們了解如何將 Azure 空間的錨點 (ASA) 整合到我們分享經驗。 ASA 可讓多個位於相同位置的裝置有常見的參考，如果其實體的環境是錨點的虛擬體驗，使得所有參與者都看到相同的實體位置中的物件。

繼續進行這一課之前，我們必須完成 ASA 的學習模組，將討論 ASA 基本概念、 Azure 帳戶並建立資源和其他我們可以將 ASA 整合到我們分享經驗之前所需的基本建築物區塊。

目標：

- 將 ASA 整合到 multi-device 對齊的共用體驗
- 了解 ASA 本機的共用經驗的內容中的運作方式的基本概念

### <a name="instructions"></a>指示

1. 將專案儲存在上一課 （control + S），並命名"HLSharedProjectMainPart5.unity 」 以便更輕鬆地尋找當您再次需要它。

2. 選取 TableAnchor prefab 下方 MixedRealityPlayspace 父物件，並將它刪除。

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)



3.  在 專案檢視移至 資產-> 資源-> Prefabs，並將拖曳 TableAnchor prefab 物件上方的 SharedPlayground 讓子系。
4.  展開 MixedRealityPlayspace 父物件、 TableAnchor 物件，然後展開 [按鈕] 物件。 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. 現在在階層中，選取 ShareAzureAnchorButton，並移動您的注意 Inaspector 面板。 向下捲動，如下圖所示的下拉式選單，選取 AnchorModuleScript 並按一下 ShareAnchorNetework()。

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. 選取 GetAzureAnchorButton （請參閱步驟 4），並移動您回到 [偵測器] 面板的注意。 向下捲動，如下圖所示的下拉式選單和選取 AnchorModuleScript，並按一下 GetSharedAnchorNetwork()，然後儲存。

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a>恭喜！

在這一課，您了解如何整合 Azure 的強大新空間錨點來對齊共的裝置共用體驗中的內容 ！ 這一課也結束時，共用的模組。 我們了解如何設定新的 Photon 帳戶，請將 Photon 與自己使用這個雙關語整合到新的 Unity 應用程式中，設定虛擬人偶 」 和 「 共用的物件，以及最後對齊這些使用 ASA 的多個參與者。 

