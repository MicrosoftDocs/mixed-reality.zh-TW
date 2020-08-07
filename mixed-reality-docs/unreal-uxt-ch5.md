---
title: 5. 新增按鈕並重設棋子位置
description: 教學課程系列的第 5 部分 (共有 6 部分)，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置簡單的國際象棋應用程式
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件
ms.openlocfilehash: e81da5a4550f258b629443df9b2b655d81108c21
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376360"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a>5.新增按鈕並重設棋子位置


## <a name="overview"></a>概觀

在上一個教學課程中，您已將手動互動動作項目新增至 Pawn，並將操作工具元件新增至國際象棋盤，使其都能夠互動。 在本節中，您將建置國際象棋應用程式的功能，來繼續使用混合實境工具組 UX 工具外掛程式。 這包括建立新的函式，以及了解如何在藍圖中取得動作項目的參考。 本節結束時，您將可以在裝置或模擬器上封裝和部署混合實境應用程式。

## <a name="objectives"></a>目標

* 新增互動式按鈕
* 建立函式來重設棋子的位置
* 連結按鈕以在按下按鈕時觸發函式

## <a name="creating-a-reset-function"></a>建立重設函式
您的第一項工作是建立函式藍圖，將棋子重設為其在場景中的原始位置。 

1.  開啟 **WhiteKing**、按一下 [ My 藍圖] 中 [函式] 區段旁的 **+** 圖示，並將其命名為 [Reset Location]。 

2.  從藍圖格線上的 [Reset Location] 拖曳並放開執行，以建立 **SetActorRelativeTransform** 節點。 
    * 此函式會為動作項目設定與其父系相對的變形 (位置、旋轉和縮放)。 您會使用此函式來重設棋盤上的國王位置，即使棋盤已從其原始位置移動也一樣。 
    
3. 在事件圖形內部按一下滑鼠右鍵，選取 [進行轉換]，並將其 [位置] 變更為 **X =-26**、**Y = 4**、**Z = 0**。
    * 將其 [傳回值] 連線到 **SetActorRelativeTransform** 中的 [新增相對轉換] 釘選。 

![重設位置函式](images/unreal-uxt/5-function.PNG)

**編譯**並**儲存**專案，然後回到主視窗。 


## <a name="adding-a-button"></a>新增按鈕
既然已正確設定函式，您的下一項工作就是建立按鈕，讓該函式在被觸碰時啟動。 

1.  按一下 [新增] > [藍圖類別]、展開 [所有類別] 區段，然後搜尋 **SimpleButton**。 
    * 將其命名為 **ResetButton**，然後按兩下以開啟藍圖

> [!NOTE]
> **SimpleButton** 是 3D 按鈕藍圖動作項目，屬於 UX 工具外掛程式。 . 

![從 SimpleButton 中為新藍圖建立子類別](images/unreal-uxt/5-subclass.PNG)

2. 從 [元件] 面板中按一下 **可點按的按鈕 (繼承)** ，然後將 [詳細資料] 面板向下捲動至 [事件] 區段。 
    * 按一下 [On Button Pressed] 旁邊的綠色 **+** 按鈕，將事件新增至事件圖形，如此在按下按鈕時便會呼叫該事件。 
    
從這裡開始，您會想要呼叫 **WhiteKing** 的 **Reset Location** 函式，該函式需要參考層級中的 **WhiteKing** 動作項目。 

1.  在 [我的藍圖] 面板中，瀏覽至 [變數] 區段、按一下 **+** 按鈕，並將變數命名為 **WhiteKing**。 
    * 在 [詳細資料] 面板中，選取 [變數類型] 旁的下拉式清單，搜尋 **WhiteKing**，然後選取 [物件參考]。 
    * 勾選 [可編輯執行個體] 旁的方塊。 這可讓您從主要層級設定變數。 

![建立變數](images/unreal-uxt/5-var.PNG)

2.  將 WhiteKing 變數從 [我的藍圖] > [變數] 拖曳到重設按鈕事件圖形，然後選擇 [取得 WhiteKing]。 

## <a name="firing-the-function"></a>啟動函式
剩下的工作就是在按下按鈕時，正式啟動重設函式。

1.  拖放 WhiteKing 輸出連接，以放置新的節點。 選取 **Reset Location** 函式。 最後，將輸出執行連接點從 [On Button Pressed] 拖曳至 [Reset Location] 上的輸入執行連接點。 **編譯**並**儲存** ResetButton 藍圖，然後回到主視窗。 

![從 On Button Pressed 呼叫 Reset Location 函式](images/unreal-uxt/5-callresetloc.PNG)

2.  將 **ResetButton** 拖曳到檢視區，並將其位置設定為 **X = 50**、**Y = -25** 和 **Z = 10**。 在 [預設值] 底下，將 **WhiteKing** 變數的值設定為 **WhiteKing**。

![設定變數](images/unreal-uxt/5-buttonlevel.PNG)

執行應用程式、將棋子移至新位置，然後按下大型粉紅色按鈕，以查看作用中的重設邏輯！

您現在有一個混合實境應用程式，其中包含可與其互動的棋子和棋盤，還有一個功能完整的按鈕，可重設棋子的位置。 到目前為止，您可在 [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) 存放庫中找到完成的應用程式。 您可以隨意進行超越本教學課程範圍的內容並設定其餘的棋子，讓整個棋盤都可在您按下按鈕時重設。

![檢視區中的最終場景](images/unreal-uxt/5-endscene.PNG)

您已準備好繼續進行本教學課程的最後一節，在這裡您將了解如何正確封裝應用程式，並將其部署至裝置或模擬器。

[下一節：6.封裝並部署至裝置或模擬器](unreal-uxt-ch6.md)
