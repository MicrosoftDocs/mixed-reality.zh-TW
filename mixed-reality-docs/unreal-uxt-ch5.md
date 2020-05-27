---
title: 5. 新增按鈕並重設棋子位置
description: 教學課程的第 5 部分，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置簡單的國際象棋應用程式
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件
ms.openlocfilehash: 77fe2b59db970a2ac4b531d69efec6794478f7d5
ms.sourcegitcommit: 09d9fa153cd9072f60e33a5f83ced8167496fcd7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/18/2020
ms.locfileid: "83519990"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a>5.新增按鈕並重設棋子位置

本節將繼續示範混合實境工具組 UX 工具外掛程式的功能，並建置國際象棋應用程式的特性。 您將建立新的函式，並了解如何將您層級中的動作項目參考放到藍圖中。

## <a name="objectives"></a>目標

* 在您的專案中新增一個按鈕
* 建立新的 “Reset Location” 函式，此函式會將棋子送回其原始位置
* 連結按鈕，以在按下按鈕時觸發新建立的函式

## <a name="create-a-function-to-reset-location"></a>建立用來重設位置的函式

1.  開啟 **WhiteKing**。 在 [我的藍圖] 面板中，按一下 [函式] 區段旁的 [+] 按鈕，以建立新的函式。 將此函式命名為 “Reset Location”。 

2.  在新建立的 **Reset Location** 藍圖中，拖曳執行連接點並將其放在藍圖方格中的任一位置，以呼叫 **SetActorRelativeTransform** 節點。 此函式會為動作項目設定與其父系相對的變形 (位置、旋轉和縮放)。 我們會使用此函式來重設棋盤上的國王位置，即使棋盤已從其原始位置移動也一樣。 建立**製造變形**節點，其位置為 X = -26、Y = 4、Z = 0，然後將其連接至新的相對變形輸入。 

![重設位置函式](images/unreal-uxt/5-function.PNG)

3.  編譯並儲存 **WhiteKing**。 返回主視窗。 

## <a name="add-a-button"></a>新增按鈕

1.  在您的 **Blueprints** 資料夾中，建立子類別為 SimpleButton 的新藍圖。 SimpleButton 是 3D 按鈕藍圖動作項目，會作為 UX 工具外掛程式的一部分提供。 將此按鈕命名為 "ResetButton"，然後按兩下以開啟藍圖。 

![從 SimpleButton 中為新藍圖建立子類別](images/unreal-uxt/5-subclass.PNG)

2.  在 [元件] 面板中，按一下 [PressableButton (繼承)]。 在 [詳細資料] 面板中，捲動畫面直到您看見 [事件] 區段。 按一下 [On Button Pressed (按下按鈕時)] 旁邊的綠色加號按鈕 - 這會將 [On Button Pressed] 事件新增至 Event Graph，並在按下按鈕時呼叫該事件。 從這裡開始，我們將要呼叫 WhiteKing 的 Reset Location 函式。 若要這樣做，我們必須先取得層級中 WhiteKing 動作項目的參考。 

3.  在 [我的藍圖] 面板中，尋找 [變數] 區段，然後按一下 [+] 按鈕以加入新的變數。 將此變數命名為 "WhiteKing"。 在 [詳細資料] 面板中，選取 [變數類型] 旁的下拉式清單，並搜尋 "WhiteKing"，然後選取 [物件參考]。 最後，勾選 [可編輯執行個體] 旁的方塊。 這可讓您從主要層級設定變數。 

![建立變數](images/unreal-uxt/5-var.PNG)

4.  將 WhiteKing 變數從 [我的藍圖] > [變數] 拖曳到重設按鈕事件圖形。 選擇 [取得 WhiteKing]。 

5.  拖放 WhiteKing 輸出連接，以放置新的節點。 選取 **Reset Location** 函式。 最後，將輸出執行連接點從 [On Button Pressed] 拖曳至 [Reset Location] 上的輸入執行連接點。 **編譯**並**儲存** ResetButton 藍圖，然後回到主視窗。 

![從 On Button Pressed 呼叫 Reset Location 函式](images/unreal-uxt/5-callresetloc.PNG)

6.  將 **ResetButton** 拖曳到檢視區，並將其位置設定為 X = 50、Y = -25、Z = 10。 在 [預設值] 底下，將 WhiteKing 變數的值設定為 **WhiteKing**。

![設定變數](images/unreal-uxt/5-buttonlevel.PNG)

您現在有一個混合實境應用程式，其中包含可抓取的棋子和棋盤，還有一個功能完整的按鈕，會在按下時重設棋子的位置。 您可以在 [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) 上找到此時完成的應用程式。 您可以隨意進行超越本教學課程範圍的內容並設定其餘的棋子，讓整個棋盤都可在使用者按下按鈕時重設。

![檢視區中的最終場景](images/unreal-uxt/5-endscene.PNG)

[下一節：6.封裝並部署至裝置或模擬器](unreal-uxt-ch6.md)
