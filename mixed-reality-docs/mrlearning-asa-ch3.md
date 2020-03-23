---
title: Azure Spatial Anchor 教學課程 - 3。 顯示 Azure Spatial Anchor 意見反應
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 11342bada65e963db6393d35c99e2c2fbffe8ff1
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031258"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a>3.顯示 Azure Spatial Anchor 意見反應

在本教學課程中，您將了解如何在使用 Azure Spatial Anchors (ASA) 時，為使用者提供有關錨點探索、事件和狀態的相關回饋。

## <a name="objectives"></a>目標

* 了解如何設定 UI 面板，以顯示目前 ASA 工作階段的相關重要資訊
* 了解並探索 ASA SDK 可供使用者使用的回饋元素

## <a name="set-up-asa-feedback-ui-panel"></a>設定 ASA 回饋 UI 面板

在 [階層] 視窗中，以滑鼠右鍵按一下 [指示]   > [TextContent]  物件，然後選取 [3D 物件]   > [文字 - TextMeshPro]  ，將 TextMeshPro 文字物件建立為 [指示] > [TextContent 物件] 的子系，並為其提供適當的名稱，例如 **Feedback**：

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> 若要更簡便地使用場景，請按一下物件左邊的眼睛圖示，將 ParentAnchor 物件的<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">場景可見度</a>設為關閉。 這會在場景視窗中隱藏物件，而不會變更其遊戲內的可見度。

在仍選取 **Feedback** 物件的情況下，在 [偵測器] 視窗中變更其位置和大小，使其整齊地放在指示文字底下，例如：

* 將矩形變形的 **Y 位置**變更為 -0.24
* 將矩形變形的**寬度**變更為 0.555
* 將矩形變形的**高度**變更為 0.1

然後選擇字型屬性，讓文字適當地放在文字區域中，例如：

* 將 Text Mesh Pro (指令碼) 的**字型樣式**變更為粗體
* 將 Text Mesh Pro (指令碼) 的**字型大小**變更為 0.17
* 將 Text Mesh Pro (指令碼) 的**對齊**變更為置中和中間

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

在仍選取 **Feedback** 物件的情況下，在 [偵測器] 視窗中，使用 [新增元件]  按鈕，將 **Anchor Feedback Script (指令碼)** 元件新增至 Feedback 物件：

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

將 **Feedback** 物件本身指派給 **Anchor Feedback Script (指令碼)** 元件的 [回饋文字]  欄位：

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a>恭喜！

在本教學課程中，您已了解如何建立 UI 面板，以顯示 Azure Spatial Anchor 驗的目前狀態，進而提供使用者即時回饋。
