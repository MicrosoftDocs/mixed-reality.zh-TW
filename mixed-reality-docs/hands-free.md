---
title: 不需要用手
description: 最佳化您的應用程式，針對免持聽筒
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: 混合實境，免持聽筒，視線，視線目標，就會有互動，設計
ms.openlocfilehash: 23b1def15c4ad900265fab2a2c8757cf96706fbc
ms.sourcegitcommit: 5b4292ef786447549c0199003e041ca48bb454cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402336"
---
# <a name="hands-free"></a>不需要用手



## <a name="scenarios"></a>案例

中所述[互動模型概觀](interaction-fundamentals.md)、 一次您已識別的使用者和其目標、 自問一樣來完成其工作，他們可能會面臨哪些環境或環境的挑戰。 比方說，許多使用者需要使用其實際操作完成其真實世界的目標，並將很難與實際操作和控制站的基礎介面互動。 

某些特定情況下可能是： 
* 正在引導您完成一項工作，指針是忙碌中
* 您手裡忙碌時，參考資料
* 手狀疲勞
* 無法追蹤的手套
* 執行項目


## <a name="hands-free-modalities"></a>免持聽筒型態

### <a name="voice-commandingvoice-designmd"></a>[語音命令](voice-design.md)

使用您的語音命令和控制介面可以不只允許使用者操作 handsfree，但也略過多個步驟。 此樣式的使用方式的範圍可以從允許使用者只讀取任何按鈕名稱大聲來啟動它，如所示，請參閱-it-say-it，來與代理程式可以為您完成的工作人員交談。



### <a name="head-gaze-and-dwellgaze-and-dwellmd"></a>[頭部目光和停駐](gaze-and-dwell.md)

在某些免持聽筒的情況下，使用您的聲音不是理想或甚至可以。 大聲工廠環境、 隱私權或社交規範都可以條件約束。 標頭視線 + 探討模型可讓使用者使用其前端的向量來點，而延遲，以瀏覽應用程式或談論按鈕會啟動它之後一段時間 （通常大約 1 秒左右）。 


## <a name="transitioning-in-and-out-of-hands-free"></a>轉換流入和流出免持聽筒

針對這些案例中，釋放與命令和導覽全像投影互動雙手範圍可以從正在操作的應用程式端對端到便利性，使用者在任何時候，可以轉換和出的是絕對需求。 

如果應用程式的需求是，它將一律會使用免持聽筒，無論是使用詳述、 語音命令或單一語音命令，"select"，則請務必在您的 UI 中進行適當的 accomodations。 

如果您的目標使用者必須能夠從手切換至免持聽筒自行斟酌，則務必考量這些原則：

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>假設使用者已在他們想要切換到的模式
比方說，如果您的使用者是在工廠，觀賞視訊她 Hololens 上的參考，並決定挑選扳手，若要開始使用，她很可能想要開始在 handsfree 不必寫下按下按鈕扳手。 她應該要能夠叫用語音命令的語音工作階段，會探討已顯示的 UI，以開始詳述，或說出單字"select"。

使用者應該能夠： 
* 切換至 handsfree handsfree 時
* 切換到您手裡使用的實際操作
* 切換至使用控制器的控制站 

### <a name="create-redundant-ways-to-switch-modes"></a>建立備援的方式，若要切換模式
關於存取的第一個準則時，第二個是有關可用性。 不只應該有單一的方式來轉換流入和流出一種模式。 

某些範例可能是： 
* 若要開始的語音互動的按鈕
* 要轉換的語音命令，使用視線 + 詳述

### <a name="add-a-dash-of-drama"></a>加入劇本一層樓
模式參數是什麼大不了的事--很重要，這些轉換發生時，它們是個明確、 更大的參數，讓使用者知道發生了什麼事。 


## <a name="usability-checklist"></a>可用性檢查清單

**使用者可以做的所有項目和免持聽筒，端對端的任何作業？**
* 每個 interactible 必須能夠存取免持聽筒
* 確定所有自訂筆勢的詳細資訊，例如調整大小、 放置、 swipes、 點選等的取代項目。
* 請確定使用者隨時都有信心控制 UI 的目前狀態、 位置、 詳細資訊
    * 取得 UI 的方式
    * 定址超出欄位的視角 (FOV) 的 UI
    * 我看到多少，其中時

**互動的機制所教授和進行與右提供？**

使用者可以了解...
* ...它們會在何種模式？
* ...它們可以做什麼在這個模式？
* ...目前的狀態為何？
* ...如何可以轉換出嗎？
    
**UI 最適合用於免持聽筒嗎？**   

* Ex. 詳述提供不是內建於一般的 2D 模式
* Ex. 語音目標是透過反白顯示的物件更趨完美
* Ex. 語音互動會透過已開啟的原文字幕更趨完美


## <a name="see-also"></a>另請參閱
* [頭部目光和行動](gaze-and-commit.md)
* [手部直接操作](direct-manipulation.md)
* [手部指向和行動](point-and-commit.md)
