---
title: 多使用者功能教學課程 - 5。 將 Azure Spatial Anchors 整合到共用體驗
description: 完成此課程以了解如何在 HoloLens 2 應用程式中實作使用者共用體驗。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7fb8cd03b2f3739037dee38786493bfd9012f6ce
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031679"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a>5.將 Azure Spatial Anchors 整合到共用體驗

在這一課中，您將了解如何將 Azure Spatial Anchors (ASA) 整合到我們的共用體驗中。 如果實體環境已用於對虛擬經驗建立錨點，則 ASA 可允許多個共置裝置擁有共同的參考，讓所有參與者可看到相同實體位置中的物件。

## <a name="objectives"></a>目標

* 將 ASA 整合到多個裝置一致的共用體驗。
* 了解 ASA 如何在本機共用體驗內容中運作的基本概念。

## <a name="instructions"></a>指示

1. 選取 MixedRealityPlayspace 父物件底下的 TableAnchor Prefab，然後將其刪除。

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. 在 [專案] 檢視中移至 [資產] -> [資源]-> [Prefabs]，然後將 TableAnchor Prefab 拖曳至 SharedPlayground 物件上方，使其成為子系。

3. 展開 MixedRealityPlayspace 父物件：TableAnchor 物件，並同時展開 [按鈕] 物件。

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. 現在，在階層中選取 [ShareAzureAnchorButton]，並將您的注意力移至 [偵測器] 面板。 向下捲動到下圖所示的下拉式功能表並選取 [AnchorModuleScript]，然後按一下 [ShareAnchorNetwork()]。

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. 選取 [GetAzureAnchorButton] \(請參閱步驟4)，並將您的注意力移回 [偵測器] 面板。 向下捲動到下圖所示的下拉式功能表並選取 [AnchorModuleScript]，然後按一下 [GetSharedAnchorNetwork()] 並儲存。

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. 重複步驟 4，將 StartAzureSession () 函式連結至 StartAzureSessionButton。

7. 重複步驟 4，將 CreateAzureAnchor () 函式連結至 CreateAzureAnchorButton，並確認 TableAnchor 物件已指派給函式的 'Game Object' 參數欄位。

8. 遵循[將場景連線至 Azure 資源](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource)的指示，以新增您的 Azure Spatial Anchors 服務認證。

9. 若要測試共用模組，請按一下 [啟動 Azure ASA 工作階段] 按鈕來啟動 Azure Spatial Anchors 工作階段，然後按一下 [建立 Azure 錨點] 按鈕來建立 Azure 錨點。 等候 Azure 錨點建立。 建立 Azure 錨點之後，請按一下 [共用 Azure 錨點] 按鈕，從 HoloLens 共用建立的 Azure 錨點。

10. 若要在另一部 HoloLens 中接收共用的 Azure 錨點，請按一下 [啟動 Azure ASA 工作階段] 以啟動並進入目前的 ASA 工作階段

11. 按一下 [取得 Azure 錨點] 按鈕，以從其他 HoloLens 取得共用的 Azure 錨點。

## <a name="congratulations"></a>恭喜！

在這一課，您已了解如何整合 Azure 的強大新 Spatial Anchors，使共置的裝置在共用體驗中達到一致！ 共用課程模組也在此結束。 我們已了解如何設定新的 Photon 帳戶、將 Photon 和 PUN 整合到新的 Unity 應用程式、設定虛擬人偶和共用物件，最後使用 ASA 來調整多個參與者。
