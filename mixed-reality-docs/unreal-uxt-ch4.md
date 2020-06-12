---
title: 4. 使場景成為互動式場景
description: 教學課程系列的第 4 部分 (共有 6 部分)，使用 Unreal Engine 4 和混合實境工具組 UX 工具外掛程式來建置簡單的國際象棋應用程式
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合實境, 教學課程, 開始使用, mrtk, uxt, UX 工具, 文件
ms.openlocfilehash: a9de5755ab86c96322a8d50fecd7ba2cdea866d3
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330215"
---
# <a name="4-making-your-scene-interactive"></a>4.使場景成為互動式場景

## <a name="overview"></a>概觀

在上一個教學課程中，您已新增 ARSession、Pawn 和遊戲模式，來完成適用於國際象棋應用程式的混合實境設定。 本節著重於使用開放原始碼[混合實境工具組 UX 工具](https://github.com/microsoft/MixedReality-UXTools-Unreal)外掛程式，其提供讓場景成為互動式場景的工具。 本節結束時，您將能夠以使用者輸入來移動棋子。 

## <a name="objectives"></a>目標

* 下載混合實境工具組 UX 工具外掛程式 
* 將手部互動動作項目新增至您的指尖
* 建立操作工具並將其新增到場景中的物件
* 使用輸入模擬來驗證專案

## <a name="downloading-the-mrtk-ux-tools-plugin"></a>下載 MRTK UX 工具外掛程式
開始處理使用者輸入之前，您必須先將外掛程式新增至專案。

1.  從 [GitHub 存放庫](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases)複製或下載最新的 MRTK UX 工具外掛程式，並將該檔案解壓縮。

2.  在專案的根資料夾中，建立名為 **Plugins** 的新資料夾。 將解壓縮的 UXTools 外掛程式複製到這個資料夾中，然後重新啟動 Unreal 編輯器。 

![建立專案外掛程式資料夾](images/unreal-uxt/4-plugins.PNG)

3.  UXTools 外掛程式具有子資料夾為 **Pointers**、**Input Simulation** 和 **Simple Button** 的 Content 資料夾，以及由函式區隔的 C++ Classes 資料夾。  

> [!NOTE]
> 如果您在 [內容瀏覽器] 中沒有看到 [UXTools 內容] 區段，請按一下 [檢視選項] > [顯示外掛程式內容]。 

![顯示外掛程式內容](images/unreal-uxt/4-showplugincontent.PNG)

一旦安全地安裝了外掛程式，您就可以開始使用程式所提供的工具，從手部互動動作項目開始。

## <a name="spawning-hand-interaction-actors"></a>繁衍手部互動動作項目
與 UX 元素的手動互動是搭配手動互動動作項目來執行，此動作項目會建立及驅動指標和視覺效果，以進行遠近距離互動。
- *近距離互動*是藉由在食指與拇指之間捏合元素或用指尖點戳來執行的。 
- *遠距離互動*是將虛擬手發出的光線指向某個元素，並同時按下食指和拇指來執行的。

在我們的案例中，將手部互動動作項目新增至 **MRPawn** 將會：
- 新增游標至 Pawn 食指的指尖。
- 提供以關節連接的手部輸入事件，可透過 Pawn 操作。
- 允許透過從虛擬手掌延伸的手部光線，進行遠距離互動輸入事件。

為了將這些概念說清楚，鼓勵您先仔細閱讀有關手部互動的[文件](https://github.com/microsoft/MixedReality-UXTools-Unreal/blob/public/0.8.x/Docs/HandInteraction.md)，再繼續進行。 

一旦準備好，就開啟 **MRPawn** 藍圖，然後移至 [事件圖形]。 

1. 從 **Event BeginPlay** 拖曳並放開執行釘選，以放置新的節點。 
    * 選取 [從類別繁衍動作項目]、按一下 [類別] 釘選旁的下拉式清單，然後搜尋 [Uxt 手部互動動作項目]。 

2. 從 [SpawnActor Uxt 手部互動] 節點拖曳並放開執行釘選，然後搜尋 [Uxt 手部互動動作項目] 類別中的 [設定手部] 功能。 
    * 將 **SpawnActor** 節點的 [傳回值] 連線至 [設定手部] 節點的 [目標] 釘選。 這會將手部互動動作項目的手部設定為 [左手]。 

3. 繁衍第二個 [Uxt 手部互動動作項目]，這次會將手部設定為 [右手]。 當事件開始時，會在每個手部上繁衍 Uxt 手部互動動作項目。 

您的 [事件圖形] 應該符合下列螢幕擷取畫面：

![繁衍 UXT 手部互動動作項目](images/unreal-uxt/4-spawnactor.PNG)

這兩個 Uxt 手部互動動作項目都需要擁有者和初始轉換位置。 初始轉換並不重要，因為手動互動動作項目會在其可見時立即跳到虛擬手部 (此行為包含在 UX 工具外掛程式中)。 不過，`SpawnActor` 函式需要轉換輸入來避免編譯器錯誤，因此您將使用預設值。 

1. 從其中一個 [繁衍轉換] 釘選拖曳並放開釘選，以放置新的節點。 
    * 搜尋 [進行轉換] 節點，然後將 [傳回值] 拖曳至另一手的 [繁衍轉換]，讓兩個 **SpawnActor** 節點連線。 

3.  按一下兩個 **SpawnActor** 節點底端的**向下箭頭**，以顯示 [擁有者] 釘選。    
    * 從其中一個**擁有者**釘選拖曳釘選，然後放開以放置新的節點。 
    * 搜尋 [本身] 並選取 [取得本身的參考] 變數，然後在 [本身] 物件參考節點與其他手部互動動作項目的 [擁有者] 釘選之間建立連結。 
    * **編譯**、**儲存**，然後返回主視窗。 

確定連線符合下列螢幕擷取畫面，但是您可以隨意拖曳節點，讓您的藍圖更容易閱讀

![完成 UXT 手部互動動作項目設定](images/unreal-uxt/4-fingerptrs.PNG) 

若要深入了解 MRTK UX 工具外掛程式中所提供的手部互動動作項目，請參閱[文件](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/HandInteraction.html)。

現在，專案中的虛擬手部有一種方式可以選取物件，但仍然無法進行操作。 測試應用程式前的最後一項工作是將操作工具元件新增至場景中的動作項目。

## <a name="attaching-manipulators"></a>附加操作工具

操作工具是一種元件，可回應以關節連接的手部輸入，而且可以抓取、旋轉和轉譯。 將操作工具的轉換套用至動作項目轉換可允許直接動作項目操作。 

1. 開啟 [棋盤] 藍圖、按一下 [新增元件]，然後在 [元件] 面板中搜尋 [Uxt 一般操作工具]。

![新增一般操作工具](images/unreal-uxt/4-addmanip.PNG)

2. 展開 [詳細資料] 面板中的 [一般操作工具] 區段。 您可以從這裡設定單手或雙手操作、旋轉模式和其他等等。 請隨意選取您想要的任何模式，然後 [編譯] 及 [儲存] 棋盤。 

![設定模式](images/unreal-uxt/4-setrotmode.PNG)

3. 針對 **WhiteKing** 動作項目重複上述步驟。

若要深入了解 MRTK UX 工具外掛程式中所提供的操作工具元件，請參閱[文件](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/Manipulator.html)。

## <a name="testing-the-scene"></a>測試場景
好消息！ 您已經準備好使用新的虛擬手部和使用者輸入來測試應用程式。 按下主視窗中的 [播放]，您會看到由 MRTK UX 工具外掛程式提供的兩個網狀手部，並且具有從每一個手掌延伸的手部光線。 您可以控制手部及其互動，如下所示：
- 按住**左 Alt** 鍵，以控制**左手**，按住**左 Shift** 鍵，以控制**右手**。 
- 移動您的滑鼠來移動手部，並使用您的**滑鼠滾輪**來捲動，將手部**向前**或**向後**移動。 
- 按一下滑鼠左鍵以**捏合**，按一下滑鼠中間按鈕以**撥開**。 

![檢視區中的模擬手部](images/unreal-uxt/4-handsim.PNG)

試著使用模擬的手部來拾起、移動和放置白棋國王，並操作棋盤！ 實驗遠近距離互動 - 請注意，當您的手夠靠近可以直接抓取棋盤和國王時，手部光線會消失，並取代為食指指尖上的手指游標。 

若要深入了解 MRTK UX 工具外掛程式中所提供的模擬手部功能，請參閱[文件](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/InputSimulation.html)。

既然您的虛擬手部可以與物件互動，您就可以繼續進行下一個教學課程，並新增使用者介面和事件。

[下一節：5.新增按鈕並重設棋子位置](unreal-uxt-ch5.md)
