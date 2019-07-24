---
title: 不需要用手
description: 將您的應用程式優化以進行無人參與
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Mixed Reality, 無人參與, 注視, 注視目標, 互動, 設計
ms.openlocfilehash: 7942192f644a7133335f089cfaaccfaebdd9292e
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414387"
---
# <a name="hands-free"></a>不需要用手



## <a name="scenarios"></a>案例

如[互動模型總覽](interaction-fundamentals.md)中所述, 一旦您識別出使用者及其目標之後, 請自問他們在完成工作時可能面臨的環境或狀況挑戰。 例如, 許多使用者需要使用他們的手來完成其真實世界的目標, 而且將難以與以實際操作和控制器為基礎的介面互動。 

某些特定案例可能是: 
* 透過工作進行引導, 而手中的人忙
* 在您的手中參考材質
* 手形疲勞
* 無法追蹤的手套
* 攜帶東西


## <a name="hands-free-modalities"></a>無人參與形式

### <a name="voice-commandingvoice-designmd"></a>[語音命令](voice-design.md)

使用您的語音來命令並控制介面, 不只允許使用者操作 handsfree, 還會略過多個步驟。 此種樣式的使用範圍可讓使用者直接讀取任何按鈕的名稱來啟用它, 就像 it 一樣, 可以與可為您完成工作的代理程式交談。



### <a name="head-gaze-and-dwellgaze-and-dwellmd"></a>[頭部目光和停駐](gaze-and-dwell.md)

在某些實際操作的情況下, 使用您的語音並不是理想或甚至不可能。 較高的處理站環境、隱私權或社交規範都可以是條件約束。 前端的 [注視 + 停留] 模型可讓使用者使用其 head 向量來導覽應用程式, 而 [延遲] 或 [俗套] 按鈕會在一段時間後啟動, 通常大約1秒左右。 


## <a name="transitioning-in-and-out-of-hands-free"></a>在手上自由轉換

在這些情況下, 您可以將您的手與全像位置互動以進行命令和導覽, 其範圍必須是對應用程式進行端對端作業的絕對需求, 以方便使用者在任何時間進行轉換。階段. 

如果應用程式的需求是一律會使用無人參與, 不論是使用 [停留]、[語音命令] 或 [單一語音] 命令, 請按一下 [選取], 然後務必在您的 UI 中進行適當的 accomodations。 

如果您的目標使用者必須自行決定是否要從手中自由切換, 則請務必考慮下列原則。

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>假設使用者已處於想要切換的模式
比方說, 如果使用者在工廠中, 觀賞 Hololens 上的影片參照, 並決定要開始使用扳手, 她很可能會開始在 handsfree 中工作, 而不需要減少扳手以按下按鈕。 她應該能夠使用語音命令叫用語音會話, 停留在已經可見的 UI 上, 以開始停留, 或說出「select」這個字。

使用者應具備下列功能: 
* 在免實習的情況下切換到無人參與
* 改用手
* 使用控制器切換到控制器 

### <a name="create-redundant-ways-to-switch-modes"></a>建立切換模式的重複方式
第一個原則是關於 access, 第二個是關於可用性。 不應該只有一種方法可以在模式之間進行轉換。 

部分範例如下: 
* 開始語音互動的按鈕
* 用來轉換至使用注視 + 停留的語音命令

### <a name="add-a-dash-of-drama"></a>新增戲劇的虛線
模式切換是一項很重要的事, 那就是當這些轉換發生時, 它們是明確而驚人的切換, 讓使用者知道發生了什麼事。 


## <a name="usability-checklist"></a>可用性檢查清單

**使用者是否可以執行所有內容, 以及是否有任何免費的端對端功能？**
* 每個 interactible 都應該是可存取的無人參與
* 請確定所有自訂手勢都有取代, 例如調整大小、放置、撥動、點擊等。
* 確保使用者隨時都能自信地控制 UI 目前狀態、放置和詳細資訊
    * 以現成的方式取得 UI
    * 定址不在 view 欄位的 UI (FOV)
    * 我看到的內容有多少, 其中

**如何使用正確的 affordances 來教授和加強互動的機制？**

使用者瞭解 。
* ...它們的所在模式為何？
* ...在此模式中, 他們可以做什麼？
* ...目前的狀態為何？
* ...他們可以如何轉移？
    
**UI 是否已針對無人參與優化？**   

* 範例：停留 affordances 不是內建的一般2D 模式
* 範例：語音目標較適合使用物件反白顯示
* 範例：語音互動較適合需要開啟的字幕


## <a name="see-also"></a>另請參閱
* [頭部目光和行動](gaze-and-commit.md)
* [手部直接操作](direct-manipulation.md)
* [手部指向和行動](point-and-commit.md)
