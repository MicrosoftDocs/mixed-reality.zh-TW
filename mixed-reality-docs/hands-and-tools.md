---
title: 實習和運動控制器
description: 實習與運動控制器互動的總覽
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: Mixed Reality, 實習, 運動控制器, 互動, 設計
ms.openlocfilehash: b6efb0a9651cad8eee9b80bb130aa1a85b9a9941
ms.sourcegitcommit: 76a7aa6e64e114b63ace058dd6d6d662b3c9f09e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2019
ms.locfileid: "68507863"
---
# <a name="hands-and-motion-controllers"></a>實習和運動控制器
## <a name="scenarios"></a>案例
如果您在閱讀[設計指導方針](interaction-fundamentals.md)之後選擇採用此互動模型, 就表示您正在開發的應用程式需要使用者使用兩個手來與全像攝影世界互動。 您的應用程式即將達到在虛擬與實體之間移除 boundry 的目標。

某些特定案例可能是:
* 提供資訊工作者 2D vitual 畫面和 Ui 以顯示和控制內容
* 在 factory 元件行中提供第一行工作者教學課程和指南
* 開發專業工具來協助及教育醫療專業人員  
* 使用3D 虛擬物件裝飾真實世界或建立第二個世界 
* 使用真實世界作為背景來建立位置服務和遊戲

## <a name="hands-and-motion-controllers-modalities"></a>實習和運動控制器形式
### <a name="direct-manipulation-with-handsdirect-manipulationmd"></a>[手部直接操作](direct-manipulation.md)
這是運用手的功能, 可供使用者直接碰觸和操作全息影像。 藉由 leaveraging 每日生活經驗, 並提供適當的視覺 affordances, 使用者就能夠使用相同的方式來操作真實世界的物件, 以與虛擬化進行互動。   

### <a name="point-and-commit-with-handspoint-and-commitmd"></a>[手部指向和行動](point-and-commit.md)
這種方式可讓使用者在某個距離內與全息影像互動。 它可讓使用者充分利用周圍的環境。 使用者可以將全息影像放在任何位置, 而且仍然可以從任何距離進行存取。 控制和操作2D 和3D 全像投影的心理模型和手勢, 與直接操作的程式高度同步。

### <a name="motion-controllersmotion-controllersmd"></a>[運動控制器](motion-controllers.md)
「動作控制器」是一種工具, 藉由在大量距離之間提供精確的互動, 同時使用一或兩個手來擴充使用者的實體功能。 這些硬體配件提供許多常用互動的快捷方式, 並提供 surefooted、觸覺各種動作的意見反應。 目前, 動作控制器僅適用于 Windows Mixed Reality (WMR) 案例。 

![實習與運動控制器形式的比較](images/Hands-and-controllers-720px.jpg)<br>

*實習與運動控制器形式的比較*

## <a name="see-also"></a>另請參閱
* [頭部目光和行動](gaze-and-commit.md)
* [頭部目光和停駐](gaze-and-dwell.md)
* [手部直接操作](direct-manipulation.md)
* [手部指向和行動](point-and-commit.md)
* [免持式](hands-free.md)
