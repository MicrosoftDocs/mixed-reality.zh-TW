---
title: 注視
description: 視線是第一種形式的輸入，而且是主要表單的目標在混合實境中。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 混合的實境、 視線、 互動，設計
ms.openlocfilehash: 738ba9063a5d00f3bbedce989d93076d56ad1a44
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629093"
---
# <a name="gaze"></a>注視

**視線**是第一種形式的輸入，而且為混合實境中目標的主要表單。 視線會告訴您使用者尋找世界中的位置，並讓您判斷其意圖。 在真實世界中，您將通常探討您想要與互動的物件。 這是相同的視線。

混合的實境耳機使用位置和您的使用者標頭的方向，以判斷其前端的視線向量。 您可以想像這個向量的雷射指標直接繼續從直接在使用者的眼睛之間。 使用者看起來房間周圍，因為您的應用程式有交集使用它自己全像投影和與此光線[空間對應](spatial-mapping.md)網狀結構來判斷您的使用者可能會看到什麼虛擬或實際物件。

HoloLens 2 上的互動可以使用者的前端視線的目標或透過附近或到目前為止送互動。  HoloLens 上 （第 1 代），互動應該通常衍生其目標從使用者的前端的視線，而不是嘗試轉譯，或直接互動的游標位置。 一旦啟動互動，相對的左手邊的動作可能會用來控制[筆勢](gestures.md)，如同[操作或瀏覽](gestures.md#composite-gestures)筆勢。 使用沈浸式耳機，您可以針對使用任一視線或指向-能夠[動作控制器](motion-controllers.md)。

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>功能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens （第 1 代）</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td> Head 視線</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr><tr>
<td> 眼睛視線</td><td></td><td style="text-align: center;">✔️</td><td></td>
</tr>
</table>

> [!NOTE]
> HoloLens 2 的特定的詳細指引[即將推出](index.md#news-and-notes)。


## <a name="uses-of-gaze"></a>視線的用途

混合的實境開發人員，您可以執行許多與視線：
* 您的應用程式有交集視線全像投影場景中使用以判斷使用者的注意力所在。
* 您的應用程式筆勢和根據使用者的視線，讓使用者選取、 啟動、 擷取、 捲動，或否則互動及其全像投影的控制器動作目標。
* 您的應用程式可以讓使用者加全像投影在真實世界表面上交集空間對應網狀結構其視線無限遠的光線。
* 您的應用程式可以知道使用者何時*不*尋找重要的物件，可能會導致您的應用程式，提供視覺與音訊提示，可針對該物件所開啟的方向。

## <a name="cursor"></a>資料指標

大部分的應用程式應使用[游標](cursors.md)（或其他聽覺/visual 指示） 給使用者的信心，在他們要進行互動。 您通常會放在其視線光線第一次互動的物件，可能是雷射或實際介面世界的這個資料指標。

![若要顯示視線範例視覺化資料指標](images/cursor.jpg)<br>
*若要顯示視線範例視覺化資料指標*

## <a name="giving-action-to-the-users-gaze"></a>讓使用者的視線動作

一旦使用者已針對全像或使用其視線的真實物件，其下一個步驟是該物件上採取動作。 讓使用者以採取動作的主要方式是透過[筆勢](gestures.md)，[動作控制站](motion-controllers.md)並[語音](voice-input.md)。

## <a name="see-also"></a>另請參閱
* [MR Input 210：目光](holograms-210.md)
* [DirectX 中的前端和眼睛視線](gaze-in-directx.md)
* [Unity 中的目光](gaze-in-unity.md)
