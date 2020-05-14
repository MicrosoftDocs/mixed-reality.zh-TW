---
title: 2. 初始化您的專案和第一個應用程式
description: 教學課程的第 2 部分，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置簡單的國際象棋應用程式
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件
ms.openlocfilehash: fc85f011ff3b186f3b4b5449b4f8ec49f0b6418f
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851572"
---
# <a name="2-initializing-your-project-and-first-application"></a>2.初始化您的專案和第一個應用程式

本節將引導您開始為 HoloLens 2 建立新的 Unreal 應用程式。 

## <a name="objectives"></a>目標

* 設定 Unreal 以用於 HoloLens 開發
* 匯入資產並設定場景

## <a name="create-a-new-unreal-project"></a>建立新的 Unreal 專案

1. 啟動 Unreal Engine

2. 在 [新增專案類別]  底下選取 [遊戲]  ，然後按 [下一步]。 選取**空白**範本，然後按 [下一步]。 

![選取空白範本](images/unreal-uxt/2-template.PNG)

3. 在 [專案設定] 中，選擇 [C++]、[可縮放 3D 或 2D]、[行動裝置/平板電腦]  及 [無起始內容]  。 選取要儲存專案的位置，然後按一下 [建立專案]  。 這會在 Visual Studio 專案和 Unreal 編輯器中開啟您的 C++ 檔案。 

![初始專案設定](images/unreal-uxt/2-project-settings.PNG)

4. 移至左上角的 [編輯] > [外掛程式]  。 在 [擴增實境] 底下，核取 **HoloLens** 外掛程式的啟用方塊。 向下捲動至 [虛擬實境] 區段，核取 **Microsoft Windows Mixed Reality** 外掛程式的啟用方塊。 這兩個外掛程式都是進行 HoloLens 2 開發的必要項目。 重新啟動您的編輯器。 

![外掛程式](images/unreal-uxt/2-plugins.PNG)

5. 移至左上角的 [檔案] > [新增層級]  。 選取 [空白層級]  。 檢視區中的預設場景現在應該是空白的。

6. 從左側 [模式] 面板的 [基本] 索引標籤中，拖曳並放置 [PlayerStart]。在右邊的 [詳細資料] 面板中，將 [位置] 設定為 X = 0、Y = 0、Z = 0，以便讓使用者位在應用程式啟動時的原始位置開始作業。

![具有 PlayerStart 的檢視區](images/unreal-uxt/2-playerstart.PNG)

7. 將 [立方體]  從 [模式] 面板的 [基本] 索引標籤拖曳至檢視區。 在 [詳細資料] 面板中，將 [位置] 設定為 X = 50、Y = 0、Z = 0，以在開始時將立方體設定為距離播放器 50 公分的位置。 由於預設的立方體相當大，請將立方體的縮放變更為 (0.2, 0.2, 0.2)。 

8. 除非您將光線新增至場景，否則無法看到立方體。 切換至 [模式] 面板上的 [光線]  索引標籤，然後將 [定向光線]  拖曳到場景中的 PlayerStart 上方。

![已新增光線的檢視區](images/unreal-uxt/2-light.PNG)

9.  按下工具列上的 [播放]  按鈕，即可在您的檢視區中查看您的立方體！ 按 **Esc** 即可停止該層級。 

![檢視區中的立方體](images/unreal-uxt/2-cube.PNG)

10. 接著來儲存您的層級。 從左上角按一下 [檔案] > [儲存目前項目]  。 將您的層級命名為 "Main"，然後按一下 [儲存]  。 

## <a name="set-up-a-chess-scene"></a>設定國際象棋場景

1. 在內容瀏覽器中，按一下 [新增] 底下的圖示來顯示來源面板。 然後按一下 [新增] > [新增資料夾]  ，並將資料夾命名為 "ChessAssets"。 按兩下此資料夾以在其中進行瀏覽。 我們將在其中匯入國際象棋的 3D 資產。

![顯示或隱藏來源面板](images/unreal-uxt/2-showhidesources.PNG)

2. 從 [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) 下載資產的 zip 檔案。 此檔案包含適用於棋盤和一套國際象棋的 3D 模型。 將此檔案解壓縮。

3. 在內容瀏覽器的頂端，按一下 [匯入]  。 瀏覽至您剛才解壓縮的資料夾，然後選取其中所有項目。 此資料夾包含 FBX 檔案，也就是棋盤和棋子的 3D 物件網格，以及 TGA 檔案，將用來為棋盤和棋子建立材質的紋理貼圖。 按一下 [開啟]  。 

4. FBX 匯入選項視窗會隨即出現。 在 [材質]  區段中，將 [材質匯入方法]  變更為 [不要建立材質]  。 然後，按一下 [全部匯入]  。

![匯入 FBX 選項](images/unreal-uxt/2-nocreatemat.PNG)

5. 回到 [內容] 資料夾，建立名為 **Blueprints** 的新資料夾。 我們將在此儲存所有藍圖，這些藍圖是特殊資產，可提供以節點為基礎的介面來建立新的動作項目類型和指令碼層級事件。 

6. 按兩下 **Blueprints** 資料夾以在其中進行瀏覽，然後在內容瀏覽器中按一下滑鼠右鍵，並選取 [藍圖類別]  。 按一下 [動作項目]  ，並將新藍圖命名為 “Board” (棋盤)。 按兩下 [Board] 來將其開啟。 

![選取您藍圖的父類別](images/unreal-uxt/2-bpparent.PNG)

![新的棋盤藍圖](images/unreal-uxt/2-bpboard.PNG)

7. 在藍圖編輯器中，瀏覽至 [元件] 面板，然後按一下 [新增元件] > [場景]  。 將新建立的場景命名為 “Root”，然後按一下 Root 並將其拖曳到 DefaultSceneRoot 上方。 這會取代預設場景的根項目，並清除檢視區中的球體。 

![取代根項目](images/unreal-uxt/2-root.PNG)

8. 再次按一下 [新增元件]  ，這次請選擇 [靜態網格]  。 將新的靜態網格命名為 “SM_Board”。 

![新增靜態網格](images/unreal-uxt/2-sm-board.PNG)

9. 在 [詳細資料]  面板中，找出 [靜態網格]  區段，然後按一下下拉式清單。 選取 [ChessBoard]  。 

![檢視區中的棋盤網格](images/unreal-uxt/2-sm-board-view.PNG)

10. 繼續在 [詳細資料]  面板中，找出 [材質]  區段，然後按一下下拉式清單。 在 [建立新資產]  中，選取 [材質]  。 將此資產命名 **M_ChessBoard**，並將其儲存在 **ChessAssets** 資料夾中。 

![建立新的材質](images/unreal-uxt/2-newmat.PNG)

11. 按兩下 M_ChessBoard 下拉式清單旁的方塊，開啟您新建立的 M_ChessBoard 材質。 在材質編輯器中，以滑鼠右鍵按一下，然後搜尋**紋理範例**節點。 在 [材質呈現紋理基底]  區段底下的 [詳細資料]  面板中，按一下下拉式清單，然後選取 [ChessBoard_Albedo]  。 最後，將 **RGB** 輸出連接拖曳到 **M_ChessBoard** 的「基本色彩」輸出連接。 

![設定基本色彩](images/unreal-uxt/2-boardalbedomat.PNG)

12. 再執行四次同樣的動作，將 **ChessBoard_AO** 紋理範例連結至**環境光遮蔽**連接點、將 **ChessBoard_Metal** 材質範例連接至**金屬**連接點，將 **ChessBoard_Normal** 紋理範例連接至**法線**連接點，以及將 **ChessBoard_Rough** 材質範例連接到**粗糙度**。 按一下 **[儲存]** 。 

![連結其餘紋理](images/unreal-uxt/2-boardmat.PNG)

13. 返回您的 **Board** 藍圖。 您應該會看到您剛建立的材質已套用至藍圖。 為了確保棋盤的大小和位置適合放在場景中，請將棋盤的**縮放**變更為 (0.05, 0.05, 0.05) ，並將**旋轉**變更為 Z = 90。 在頂端的工具列中，按一下 [編譯]  ，然後**儲存**。 返回您的主視窗。 

![已套用材質的棋盤](images/unreal-uxt/2-chessboard.PNG)

14. 現在我們要刪除立方體，並將其取代為新建立的棋盤動作項目。 在 [世界大綱 (World Outliner)]  中，以滑鼠右鍵按一下您的立方體 > [編輯] > [刪除]  。 將 [棋盤] 從內容瀏覽器拖曳至檢視區。 將棋盤的位置設定為 X = 80、Y = 0、Z = -20。 

15. 按一下 [播放]  按鈕，以在您的層級中查看新的棋盤。 按 **Esc** 即可返回編輯器。 

16. 現在，我們將使用建立棋盤的相同步驟來建立棋子，這次我們要選取棋子的網格和材質：

    a) 瀏覽至內容瀏覽器中的 Blueprints 資料夾，並為動作項目類型建立新的藍圖類別。 將此動作項目命名為 "WhiteKing"。

    b) 按兩下 [WhiteKing] 來將其開啟。 新增名為 “Root” 的新場景元件，並使用其來取代 DefaultSceneRoot。 

    c) 新增名為 "SM_King" 的新靜態網格元件。 在 [詳細資料] 面板中，將 [靜態網格]  設定為 **Chess_King**，將 [材質]  設定為名為 **M_ChessWhite** 的新材質。 

    d) 開啟新的 **M_ChessWhite** 材質，並將相關紋理連結到其對應的材質輸入。 

    ![為國王棋建立材質](images/unreal-uxt/2-chesskingmat.PNG)

    e) 回到您的 **WhiteKing** 藍圖，將**縮放**變更為 (0.05, 0.05, 0.05)，並將**旋轉**設定為 Z = 90。

    f) 編譯並儲存您的藍圖，然後往回瀏覽到主視窗。 

17. 將 WhiteKing 拖曳至您的檢視區。 在 [世界大綱]  中，將 WhiteKing 拖曳至棋盤，讓 WhiteKing 現在成為棋盤的子系。 

![世界大綱](images/unreal-uxt/2-child.PNG)

18. 在 [變形]  底下的 [詳細資料]  面板中，將 WhiteKing 的 [位置]  設定為 X = -26、Y = 4、Z = 0

19. 按一下 [播放]  以查看您的層級。 按 **Esc** 即可結束。 

[下一節：3.設定您的專案以進行混合實境](unreal-uxt-ch3.md)