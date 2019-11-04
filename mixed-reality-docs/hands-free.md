---
title: 不需要用手
description: 將您的應用程式優化以進行無人參與
author: liamartinez
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Mixed Reality，無人參與，注視，注視目標，互動，設計
ms.openlocfilehash: b2405f5dca19838271363f53ca377c4f90ca1b36
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435080"
---
# <a name="hands-free"></a>不需要用手

## <a name="scenarios"></a>案例

如[互動模型總覽](interaction-fundamentals.md)中所述，一旦識別出您的使用者及其目標之後，請自問他們在完成工作時可能面臨的環境或狀況挑戰。 例如，許多使用者需要使用他們的手來完成其真實世界的目標，而且他們將難以與以實際操作和控制器為基礎的介面互動。 

某些特定案例包括： 
* 透過工作進行引導，而使用者的手忙碌中
* 當使用者的手忙碌時參考素材
* 手形疲勞
* 無法追蹤的手套
* 親自攜帶東西
* 執行大型手勢的社交 awkwardness
* 緊密空格


## <a name="hands-free-modalities"></a>無人參與形式

### <a name="voice-inputvoice-inputmd"></a>[語音輸入](voice-input.md)

使用您的語音來命令和控制介面提供便利的方式來操作無人參與，並視需要使用快捷方式來彈性略過多個步驟。 使用語音輸入時，使用者可以直接讀取任何按鈕的名稱來啟用它（「_見它，說它」）_ ，然後與可為您完成工作的數位代理程式對話。


### <a name="gaze-and-dwellgaze-and-dwellmd"></a>[目光和停駐](gaze-and-dwell.md)

在某些實際操作的情況下，使用您的語音並不是理想或甚至不可能。 較高的處理站環境、隱私權或社交規範都可以是條件約束。 [監看式] 和 [停留] 模型可讓使用者導覽應用程式，而不需要任何額外的輸入，並將其放在其眼或前端中：使用者只要在目標上保留撥雲見日（及其頭部或眼睛）並 lingers，即可啟動它。 若要深入瞭解您的眼睛 + 停留的個別設計考慮，請查看[眼中的](gaze-and-dwell-eyes.md)[監看式] 和 [列印頭] [+](gaze-and-dwell-head.md)[停留]。


## <a name="transitioning-in-and-out-of-hands-free"></a>在手上自由轉換

在這些情況下，您可以將您的手與全像位置互動以進行命令和導覽，其範圍必須是對應用程式進行端對端作業的絕對需求，以方便使用者在任何時間進行轉換。階段. 

如果應用程式的需求是一律會使用無人參與，不論是使用 [停留]、[自訂語音命令] 或 [單一語音] 命令，請按一下 [選取]，然後務必在您的 UI 中做出適當的便利。 

如果您的目標使用者必須自行決定是否要從手中自由切換，則請務必考慮下列原則。

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>假設使用者已處於想要切換的模式
比方說，如果使用者在工廠中，觀賞 HoloLens 上的影片參照，並決定要開始使用扳手，她很可能會開始自由操作，而不需要放下扳手來按下按鈕。 她應該能夠使用語音命令叫用語音會話，停留在已經可見的 UI 上，以開始停留，或說出「select」這個字。

使用者應具備下列功能： 
* 在免實習的情況下切換到無人參與
* 改用手
* 使用控制器切換到控制器 

### <a name="create-redundant-ways-to-switch-modes"></a>建立切換模式的重複方式
第一個原則是關於 access，第二個是關於可用性。 不應該只有一種方法可以在模式之間進行轉換。 

部分範例如下： 
* 開始語音互動的按鈕
* 用來轉換至的語音命令，使用頭部注視和停留

### <a name="add-a-dash-of-drama"></a>新增戲劇的虛線
模式切換是一項很重要的事，那就是當這些轉換發生時，它們是明確的，甚至是很大的切換，讓使用者知道發生了什麼事。 


## <a name="usability-checklist"></a>可用性檢查清單

**使用者是否可以執行所有內容，以及是否有任何免費的端對端功能？**
* 每個可互動都應該是可存取的無人參與
* 請確定所有自訂手勢都有取代，例如調整大小、放置、撥動、點擊等。
* 確保使用者隨時都能自信地控制 UI 目前狀態、放置和詳細資訊
    * 以現成的方式取得 UI
    * 定址不在 view 欄位的 UI （FOV）
    * 我看到的內容有多少，其中

**如何使用正確的 affordances 來教授和加強互動的機制？**

使用者瞭解 。
* ...它們的所在模式為何？
* ...在此模式中，他們可以做什麼？
* ...目前的狀態為何？
* ...他們可以如何轉移？
    
**UI 是否已針對無人參與優化？**   

* 範例：停留 affordances 不是內建的一般2D 模式
* 範例：語音目標較適合使用物件反白顯示
* 範例：語音互動較適合需要開啟的字幕


## <a name="see-also"></a>請參閱
* [HoloLens 2 上的眼睛追蹤](eye-tracking.md)
* [注視和認可](gaze-and-commit.md)
* [目光和停駐](gaze-and-dwell.md)
* [直接操作](direct-manipulation.md)
* [實習手勢](gaze-and-commit.md#composite-gestures)
* [實際操作和認可](point-and-commit.md)
* [本能互動](interaction-fundamentals.md)
* [語音輸入](voice-input.md)
