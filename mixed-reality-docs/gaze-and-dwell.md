---
title: 注視和停留
description: （眼睛/head）注視和停留輸入模型的一般總覽
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Mixed Reality，注視，停留，互動，設計，眼睛追蹤，head 追蹤
ms.openlocfilehash: d87406d0b2695cd86c40f27cb132af54ed525b25
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435361"
---
# <a name="gaze-and-dwell"></a>注視和停留

當手上拿著工具和組件時，手勢可以很繁瑣或不可能進行。 語音命令在某些內容中可能也不可靠，例如在過高的情況下。 注視和停留提供了一種熟悉且簡單的機制，可讓您在 HoloLens 上運作並無需實際操作。 此外，注視和停留是一個絕佳的回溯，與作業環境中的干擾干擾或無聲條件約束無關。
我們區分兩種看眼_和停留_的變化：[頭部眼和停留](gaze-and-dwell-head.md)，以及監看[式和停留](gaze-and-dwell-eyes.md)。

## <a name="scenarios"></a>案例

在某人的手中使用其他工作的情況下，注視並停留擅長，而語音不會因為環境或社交條件約束而處於100% 可靠或可供使用。 穿戴 HoloLens 的人員在修理汽車引擎時覆疊參考資訊就是個不錯的範例。 他們的雙手忙著拿起工具，或在靠向引擎室時支撐其身體。 車庫空間很吵雜，充斥著工具的碰撞和唧唧聲，讓語音命令變得難以使用。 注視和停留可讓使用 HoloLens 的人安心地流覽其參考資料，而不會中斷工作流程。 

## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>輸入模型</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>頭部注視並佇留</td>
        <td>✔️ 建議使用</td>
        <td>✔️ 建議使用</td>
        <td>✔️ 建議使用</td>
    </tr>
     <tr>
        <td>眼睛與停留</td>
        <td>❌ 無法使用</td>
        <td>✔️ 建議使用</td>
        <td>❌ 無法使用</td>
    </tr>
</table>


<br>

---
 
 ## <a name="see-also"></a>請參閱
* [目視互動](eye-gaze-interaction.md)
* [HoloLens 2 上的眼睛追蹤](eye-tracking.md)
* [注視和認可](gaze-and-commit.md)
* [直接操作](direct-manipulation.md)
* [實習手勢](gaze-and-commit.md#composite-gestures)
* [實際操作和認可](point-and-commit.md)
* [本能互動](interaction-fundamentals.md)
* [語音輸入](voice-input.md)
