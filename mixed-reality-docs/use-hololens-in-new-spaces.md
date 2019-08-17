---
title: 使用新空間中的 HoloLens
description: HoloLens 學習了一段時間後的空間外觀。 使用者可以透過空間以特定方式移動 HoloLens 來加速此程式。
author: dorreneb
ms.author: dobrown
ms.date: 08/16/2019
ms.topic: article
keywords: Windows Mixed Reality, 設計, 空間對應, HoloLens, 表面重建, 網格, 頭追蹤, 對應
ms.openlocfilehash: a6a83dfc2c883723e4cd79c0dc46a9cd78f1f604
ms.sourcegitcommit: 60f73ca23023c17c1da833c83d2a02f4dcc4d17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566017"
---
# <a name="use-hololens-in-new-spaces"></a>使用新空間中的 HoloLens

HoloLens*對應*或學習的相關資訊, 也就是使用者在空間前後移動的環境。 經過一段時間後, HoloLens 會為環境中所有已觀察到的部分建立*空間對應*。 在觀察到環境中的變更時, HoloLens 會更新對應。 此掃描會在應用程式啟動時自動儲存。

只要裝置已開啟且使用者已登入, HoloLens 就會建立並更新對應。 如果您按住或磨損裝置, 並將相機指向某個空間, 則裝置會嘗試對應該區域。 雖然 HoloLens 會在一段時間內自然地學習空間, 但是有一些秘訣和訣竅可讓您更快且更有效率地對應空間。 

如果您的 HoloLens 無法對應您的空間或無法校正, 您可以進入有限的模式。 在 [受限] 模式中, 您無法將全息影像放在您的環境中。

## <a name="tips-and-tricks-for-mapping-spaces"></a>對應空間的秘訣和訣竅

### <a name="make-sure-the-space-is-set-up-for-mixed-reality"></a>請確定已設定混合現實的空間

環境中的功能可能會使 HoloLens 難以解讀空間。 輕量、空間中的材質、物件的版面配置等等, 全都會影響 HoloLens 如何對應區域。

在[hololens 的環境考慮](environment-considerations-for-hololens.md)中, 可以找到設定 hololens 和其他混合現實裝置空間的秘訣。

### <a name="understand-the-scenarios-for-the-area"></a>瞭解區域的案例

請務必花最多時間來使用 HoloLens, 讓對應更相關且完整。 

例如, 如果 HoloLens 的使用者案例牽涉到從點 A 移到第 B 點, 請將該路徑逐一移到三次, 並在您移動時查看所有方向。 

### <a name="walk-slowly-around-the-space"></a>以緩慢的速度四處流覽空間

如果您在此區域中的速度過快, 可能是 HoloLens 錯過了對應區域。 沿著空間的速度變慢, 每隔5-8 英尺就能在您的周圍進行討論。

順暢的移動也可協助 HoloLens 對應更 effeciently。

### <a name="look-in-all-directions"></a>查詢所有方向

當您對應空間時, 會提供 HoloLens 更多資料, 其中的點彼此相對。 

例如, 如果您找不到, 則 HoloLens 可能無法得知房間內的上限為何。 

當您對應空間時, 別忘了在地面上向下查看。

### <a name="cover-key-areas-multiple-times"></a>涵蓋重要區域多次

在某個區域中多次移動, 將有助於挑選您在第一個逐步解說中可能錯過的功能。 嘗試遍歷區域二到三次, 以建立理想的對應。

可能的話, 在重複這些移動時, 請花點時間在某個方向的區域中進行, 然後再來回進行, 然後回頭流覽您的方式。

### <a name="take-your-time-mapping-the-area"></a>讓您的時間與區域對應

HoloLens 可能需要15到20分鐘的時間, 才能完全對應並自行調整為其周圍的環境。 如果您想要經常使用 HoloLens, 讓該時間預先對應空間可能會導致稍後發生問題。 

## <a name="possible-errors-in-the-spatial-map"></a>空間對應中可能發生的錯誤

空間對應資料中的錯誤屬於下列三種類別的其中一種:

* *漏洞*:空間對應資料中遺漏了真實世界的表面。
* *Hallucinations*:表面存在於不存在於真實世界中的空間對應資料。
* *Wormholes*:HoloLens 「失去」空間對應的一部分, 因為它是在地圖的不同部分, 而不是實際的。
* *偏差*:空間對應資料中的表面會 imperfectly 對齊實際的表面, 不論是推送或拉出。

您可以藉由[刪除您的全息影像](environment-considerations-for-hololens.md)並重新對應空間, 來減輕其中許多錯誤。