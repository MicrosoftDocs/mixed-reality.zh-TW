---
title: 4. 使場景成為互動式場景
description: 教學課程的第 4 部分，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置簡單的國際象棋應用程式
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件
ms.openlocfilehash: 17f7ab1c1126c47e5ac6388d125d45cf3f2c2d87
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851543"
---
# <a name="3-making-your-scene-interactive"></a>3.使場景成為互動式場景

本節將為您介紹開放原始碼混合實境工具組 UX 工具外掛程式，其提供一組工具讓您輕鬆地使場景成為互動式場景。 在本節結束時，您的國際象棋將會回應使用者輸入。 

## <a name="objectives"></a>目標

* 在您的專案中包含混合實境工具組 UX 工具外掛程式
* 將手部互動動作項目新增至您的指尖
* 建立操作工具，並將其附加到您的國際象棋棋盤和棋子 
* 使用輸入模擬來驗證您的專案

## <a name="download-the-mixed-reality-toolkit-ux-tools-plugin"></a>下載混合實境工具組 UX 工具外掛程式

1.  從 [UX 工具 GitHub 存放庫](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases)複製或下載並解壓縮最新版本的 MRTK UX 工具外掛程式

2.  在您的國際象棋專案根資料夾中，建立名為「外掛程式」的新資料夾。 將解壓縮的 UXTools 外掛程式複製到此資料夾中。 重新啟動 Unreal 編輯器。 

![建立專案外掛程式資料夾](images/unreal-uxt/4-plugins.PNG)

3.  重新啟動之後，如果您在來源面板中看不到 UXTools 外掛程式內容，您可能需要按一下 [檢視選項] > [顯示外掛程式內容]  。 您會看到 UXTools 外掛程式提供具有指標、輸入模擬和簡單按鈕的內容資料夾，以及 C++ 類別資料夾 (具有以函式分隔的子資料夾)。  

![顯示外掛程式內容](images/unreal-uxt/4-showplugincontent.PNG)

## <a name="spawn-hand-interaction-actors"></a>繁衍手部互動動作項目

1.  讓我們從 MRPawn 繁衍手部互動動作項目開始，如此一來 1) 我們可以使用游標視覺化 MRPawn，在食指指尖上顯示「兵」，2) 我們可以透過「兵」提供以關節連接的手部輸入事件 (因此直接操作動作項目)，以及 3) 我們可以透過從手掌延伸的手部光線提供遠處互動輸入事件。 開啟 **MRPawn** 藍圖，然後瀏覽至**事件圖形**。 

2.  從 Event BeginPlay 拖曳執行釘選，放開以放置新的節點。 選取 [從類別繁衍動作項目]  節點。 按一下 [類別]  釘選旁的下拉式清單，然後搜尋 **Uxt 手部互動動作項目**。 從 SpawnActor Uxt 手部互動節點拖曳執行釘選、放開，然後搜尋 Uxt 手部互動動作項目類別中包含的**設定手部**功能。 將 SpawnActor 節點的傳回值連線至 [設定手部] 節點的目標釘選，以將手部互動動作項目的手部設為**左手**。 繁衍第二個 **Uxt 手部互動動作項目**，這一次將手部設定為**右手**，如此一來，當事件開始時，Uxt 手部互動動作項目就會在各個手上繁衍。 

![繁衍 UXT 手部互動動作項目](images/unreal-uxt/4-spawnactor.PNG)

3.  接下來，我們需要提供我們的 Uxt 手部互動動作項目，以及要繁衍的初始轉換和擁有者。 從其中一個**繁衍轉換**釘選拖曳釘選，然後放開以放置新的節點。 搜尋**製作轉換**節點。 初始轉換其實並不重要，因為手部互動動作項目會在其可見 (已在 UX 工具外掛程式中為我們撰寫的程式碼) 時立即跳到我們的手上，否則將會消失。 不過，SpawnActor 功能需要轉換作為輸入，以避免編譯器錯誤，因此我們保留「製作轉換」節點中原來的預設值。 同時將「製作轉換」的**傳回值**拖曳至另一隻手的互動動作項目繁衍轉換。 

4.  按一下兩個 SpawnActor 節點底端的**向下鍵**，以顯示**擁有者**釘選。 從其中一個**擁有者**釘選拖曳釘選，然後放開以放置新的節點。 搜尋「本身」，然後選取**取得本身的參考**變數。 同時在「本身」物件參考節點與另一個手部互動動作項目的擁有者釘選之間建立連結。 您可以隨意拖曳節點，讓您的藍圖更容易讀取。 **編譯**、**儲存**，然後返回主視窗。 

![完成 UXT 手部互動動作項目設定](images/unreal-uxt/4-fingerptrs.PNG)

如需有關 MRTK UX 工具外掛程式中所提供手部互動動作項目的詳細資訊，請參閱官方[文件](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/HandInteraction.html)。

## <a name="attach-manipulators"></a>附加操作工具

1.  接下來，我們會將操作工具附加到我們的國際象棋棋盤和國王動作項目。 操作工具是一個元件，其回應以關節連接的手部輸入，而且可以抓取、旋轉和轉譯；藉由將操作工具的轉換套用至動作項目，可以直接操控動作項目。 

2.  開啟您的棋盤藍圖。 在 [元件]  面板中，按一下 [新增元件]  ，並搜尋 **Uxt 一般操作工具**。 在 [詳細資料] 面板中，您會找到標題為 [一般操作工具]  的區段，您可以在其中設定要啟用單手或雙手操作、旋轉模式和平滑處理。 請隨意選取您想要的任何模式，然後 [編譯]  及 [儲存]  棋盤。 

![新增一般操作工具](images/unreal-uxt/4-addmanip.PNG)

![設定模式](images/unreal-uxt/4-setrotmode.PNG)

3.  針對 WhiteKing 動作項目重複上述步驟。

如需有關 MRTK UX 工具外掛程式中所提供操作工具元件的詳細資訊，請參閱官方[文件](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/Manipulator.html)。

## <a name="test-out-your-scene-with-simulated-hands"></a>使用模擬的手測試您的場景

1.  在主視窗中，按下 [播放]  。 您應該會看到由 MRTK UX 工具外掛程式提供的兩個網狀手部，並且具有從每一個手掌延伸的手部光線！ 

![檢視區中的模擬手部](images/unreal-uxt/4-handsim.PNG)

2.  若要控制**右手**，請按住**左 Alt** 按鈕。 移動滑鼠來移動手部。 使用您的**滑鼠滾輪**捲動，將手部**向前**或**向後**移動。 按一下滑鼠左鍵以**捏合**，按一下滑鼠中間按鈕以**撥開**。

3.  若要控制**左手**，請按住**左 Shift** 按鈕。 用來移動左手的控制項與右手的控制項相同。 

4.  現在請試著使用模擬的手來拾起、移動和放置白棋國王。 您也可以操控棋盤！ 具有遠近互動的實驗 - 請注意，當您的手夠靠近可以直接抓取棋盤和國王時，手部光線會消失，並且以索引提示上的手指游標取代。 

如需有關 MRTK UX 工具外掛程式中所提供模擬手部功能的詳細資訊，請參閱官方[文件](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/InputSimulation.html)。

[下一節：5.新增按鈕並重設部分位置](unreal-uxt-ch5.md)