---
title: 注視
description: 注視是第一種形式的輸入, 是混合現實中的主要目標形式。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Mixed reality, 注視, 互動, 設計
ms.openlocfilehash: 7e65d26d3e9edabbd01d35a887ffc8622a3c6337
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414374"
---
# <a name="gaze"></a>注視

**注視**是第一種形式的輸入, 是混合現實中的主要目標形式。 注視會告訴您使用者在世界中的所在位置, 並可讓您判斷其意圖。 在真實世界中, 您通常會查看想要與之互動的物件。 這與注視相同。

混合現實耳機會使用您使用者的前端位置和方向來判斷其 head 的注視向量。 您可以直接從使用者的眼睛, 將此向量視為鐳射指標。 當使用者查看房間時, 您的應用程式可以與此光線相交, 這兩者都有自己的全息影像和[空間對應](spatial-mapping.md)網格, 以判斷您的使用者可能會查看的虛擬或真實世界物件。

在 HoloLens 2 上, 互動的目標可能是使用者的前端、眼睛眼, 或接近或遠的手間互動。
在 HoloLens (第1代) 上, 互動通常會從使用者的前端衍生其目標, 而不是嘗試直接在手中呈現或互動。 互動開始之後, 手的相對運動可能會用來控制[手勢](gestures.md), 如同[操作或導覽](gestures.md#composite-gestures)手勢。 有了沉浸式耳機, 您就可以使用頭部注視或可支援指標的[運動控制器](motion-controllers.md)作為目標。

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>頭部注視</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>眼睛</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

> [!NOTE]
> [即將推出](index.md#news-and-notes)更多 HoloLens 2 特定指引。


## <a name="uses-of-gaze"></a>注視的使用

身為混合現實的開發人員, 您可以使用 head 或眼睛來進行許多動作:
* 您的應用程式可以與場景中的全息影像相交, 以判斷使用者的注意位置。
* 您的應用程式可以根據使用者的注視來鎖定手勢和控制器按下, 讓使用者選取、啟動、抓取、滾動, 或以其他方式與其全息影像互動。
* 您的應用程式可以讓使用者將全息影像放在真實世界的表面上, 並將其注視光線與空間對應網格相交。
* 您的應用程式可以知道使用者何時看*不*到重要物件的方向, 這可能會導致您的應用程式提供視覺和音訊提示來轉向該物件。

## <a name="cursor"></a>資料指標

對於列印頭, 大部分的應用程式都應該使用[游標](cursors.md)(或其他聽覺/視覺指示), 讓使用者能夠信賴他們要與之互動的物件。 您通常會將此游標置於世界中, 其前端光線會先與物件相交, 這可能是全息影像或真實世界表面。

![顯示注視的視覺化游標範例](images/cursor.jpg)<br>
*顯示注視的視覺化游標範例*

就眼睛而言, 我們通常建議*不要*顯示游標, 因為這可能會很快就會變得令人困擾, 而且不會讓使用者雜亂。 相反地, 反白顯示視覺效果目標, 或使用非常不好的眼游標, 讓您安心瞭解使用者的互動方式。 如需詳細資訊, 請查看我們在 HoloLens 2 上[以眼睛為基礎之輸入的設計指引](eye-tracking.md)。

## <a name="giving-action-to-the-users-gaze"></a>對使用者的注視提供動作

一旦使用者使用其注視來鎖定全息影像或真實世界物件, 下一步就是對該物件採取動作。 使用者採取動作的主要方式是透過[手勢](gestures.md)、[動作控制器](motion-controllers.md)和[語音](voice-input.md)。

## <a name="see-also"></a>另請參閱
* [MR Input 210：頭部注視](holograms-210.md)
* [DirectX 中的頭部和眼睛目光](gaze-in-directx.md)
* [Unity 中的頭注視](gaze-in-unity.md)
* [HoloLens 2 上的眼睛](eye-tracking.md)
* [Unity 使用混合現實工具組的眼睛](https://aka.ms/mrtk-eyes)
