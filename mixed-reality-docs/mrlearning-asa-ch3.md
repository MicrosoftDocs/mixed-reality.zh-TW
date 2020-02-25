---
title: Azure 空間錨點教學課程-3。 顯示 Azure 空間錨點意見反應
description: 完成此課程以了解如何在混合實境應用程式中實作 Azure 臉部辨識。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合實境, unity, 教學課程, hololens
ms.openlocfilehash: 3d762950ea8e211fd5a8e4cf8af717674d3fe7e1
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553924"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a>3. 顯示 Azure 空間錨點的意見反應

在本教學課程中，您將瞭解如何在使用 Azure 空間錨點（ASA）時，為使用者提供錨點探索、事件和狀態的相關意見反應。

## <a name="objectives"></a>目標

* 瞭解如何設定 UI 面板，以顯示目前 ASA 會話的相關重要資訊
* 瞭解並探索 ASA SDK 可供使用者使用的意見反應元素

## <a name="set-up-asa-feedback-ui-panel"></a>設定 ASA 意見反應 UI 面板

在 [階層] 視窗中，以滑鼠右鍵按一下 > **TextContent**物件的**指示**，然後選取 [ **3d 物件** > **TextMeshPro** ]，以建立 TextMeshPro 文字物件做為指示 > TextContent 物件的子系，並為其提供適當的名稱，例如**意見**反應：

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> 若要讓您更輕鬆地使用場景，請按一下物件左側的眼睛圖示，將 ParentAnchor 物件的<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">場景可見度</a>設定為 [關閉]。 這會隱藏場景視窗中的物件，而不會變更其遊戲內可見度。

在仍選取 [**意見**反應] 物件的情況下，在 [偵測器] 視窗中變更其位置和大小，使其整齊地放在指令文字底下，例如：

* 將矩形轉換**Pos Y**變更為-0.24
* 將 [矩形轉換**寬度**] 變更為0.555
* 將矩形轉換**高度**變更為0。1

然後選擇 [字型屬性]，讓文字適當地放在文字區域中，例如：

* 將文本網格 Pro （腳本）**字型樣式**變更為粗體
* 將文本網格 Pro （腳本）**字型大小**變更為0.17
* 將文本網格 Pro （腳本）**對齊**變更為置中和中間

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

在仍選取 [**意見**反應] 物件的情況下，在 [偵測器] 視窗中，使用 [**加入元件**] 按鈕，將**錨點回饋腳本（腳本）** 元件新增至意見物件：

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

將**意見**物件本身指派給**錨點意見反應腳本（腳本）** 元件的**意見反應文字**欄位：

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a>恭喜

在本教學課程中，您已瞭解如何建立 UI 面板，以顯示 Azure 空間錨點體驗的目前狀態，以提供使用者即時意見反應。
