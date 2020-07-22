---
title: Azure Spatial Anchors 教學課程 - 4. 顯示 Azure Spatial Anchors 意見反應
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure Spatial Anchors。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: d221a7e64bda7a6dabf76b60c7bff7c6333666ef
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304435"
---
# <a name="4-displaying-feedback-from-azure-spatial-anchors"></a>4.顯示 Azure Spatial Anchors 的意見反應

在本教學課程中，您將了解如何為使用者提供使用 Azure Spatial Anchors (ASA) 的相關錨點探索、事件和狀態的相關回饋。

## <a name="objectives"></a>目標

* 了解如何設定 UI 面板，以顯示目前 ASA 工作階段的相關重要資訊
* 了解並探索 ASA SDK 可供使用者使用的回饋元素

## <a name="setting-up-asa-feedback-panel"></a>設定 ASA 意見反應面板

在階層視窗中，以滑鼠右鍵按一下 [指示] >  [TextContent] 物件。 選取 [3D 物件] >  [文字 - TextMeshPro]，將 TextMeshPro 文字物件建立為指示 > TextContent 物件的子系：

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-1.png)

> [!TIP]
> 若要更簡便地使用場景，請按一下物件左邊的眼睛圖示，將 ParentAnchor 物件的<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">場景可見度</a>設為關閉。 這會在場景視窗中隱藏物件，而不會變更其遊戲內的可見度。

將新建立的文字 (TMP) 物件**意見反應**重新命名，接著在 [偵測器] 視窗中變更其位置和大小，使其整齊地放在指示文字底下，例如：

* 將矩形變形元件的 **Y 位置**變更為 -0.24。
* 將矩形變形元件的**寬度**變更為 0.555。
* 將矩形變形元件的**高度**變更為 0.1。

然後選擇字型屬性，讓文字適當地放在文字區域中，例如：

* 將 TextMeshPro - 文字元件的**字型樣式**變更為粗體。
* 將 TextMeshPro - 文字元件的**字型大小**變更為 0.17。
* 將 TextMeshPro 文字元件的**對齊**變更為置中和中間。

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-2.png)

在階層視窗中再次選取 [意見反應] 物件，然後在偵測器視窗中使用 [新增元件] 按鈕來新增**錨點意見反應指令碼 (指令碼)** 元件，並進行以下設定：

* 將 **Feedback** 物件本身指派給 **Anchor Feedback Script (指令碼)** 元件的 [回饋文字] 欄位。

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-3.png)

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已了解如何建立 UI 面板。 該面板會顯示 Azure Spatial Anchors 體驗的目前狀態，以提供即時的使用者意見反應。

[下一個教學課程：5.適用於 Android 和 iOS 的 Azure Spatial Anchors](mr-learning-asa-05.md)
