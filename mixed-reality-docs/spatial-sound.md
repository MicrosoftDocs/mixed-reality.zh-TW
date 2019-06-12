---
title: 空間音效
description: 在混合的實境應用程式中使用空間的聲音，可讓您 convincingly 放置在 3D 空間中的音效。
author: hak0n
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: 空間的音效、 環繞音效、 3d 的音訊、 3d 的音效、 空間音訊
ms.openlocfilehash: a30a484c4e47593556fbd1786158262551e11d22
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829925"
---
# <a name="spatial-sound"></a>空間音效

當物件不在我們的視野時，我們能夠察覺發生什麼情況我們週遭的方式之一是透過音效。 在 Windows Mixed Reality，音訊引擎會提供混合實境體驗聽覺元件，藉由模擬 3D 方向、 距離和環境模擬使用的音效。 在 應用程式中使用空間的聲音各地使用者允許開發人員 convincingly 置於 3 維空間 （球形） 中的音效。 這些聽起來再看起來將如同就像是來自真正的實體物件或使用者的周圍環境中混合的實境全像投影。 假設[全像投影](hologram.md)會進行的光線的物件，並幫助的有時音效、 音效元件地面全像投影使其更可信，並建立更多人沉迷的體驗。

雖然全像投影只可以出現視覺上使用者的視線所指向的位置，您的應用程式的聲音可能來自所有方向;上方下, 面，一邊，等等。您可以使用這項功能，以強調目前可能不存在的使用者檢視中的物件。 使用者能夠察覺聲音，動畫從混合現實世界中的來源。 比方說，當使用者即將來臨的物件或物件取得較近時，會增加磁碟區。 同樣地，當物件移動周圍的使用者，或反之亦然，空間的聲音會讓聽起來來自直接從物件的假象。

<br>

>[!VIDEO https://www.youtube.com/embed/PTPvx7mDon4]

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
        <td><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沈浸式耳機</strong></a></td>
    </tr>
     <tr>
        <td>空間音效</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ （使用耳機）</td>
    </tr>
</table>

## <a name="simulating-the-perceived-location-and-distance-of-sounds"></a>模擬的認知的位置和距離的音效

藉由分析如何音效達到這兩個耳朵，我們的大腦決定距離和物件發出聲音的方向。 模型化幽靈回應特性 이 어 空間中的點從所接收的聲音 HRTF （或標頭相關傳輸函式） 時，模擬這種互動。 空間的音訊引擎會使用個人化的 HRTFs 拓展混合的實境體驗，並模擬來自不同的方向和距離的音效。

<br>

>[!VIDEO https://www.youtube.com/embed/aB3TDjYklmo]

向左或右音訊 (azimuth) 提示源自音效抵達每個 이 어 時間差異。 向上和向下提示源自幽靈 outer 이 어 圖形 (pinnae) 所產生的變更。 指定在音訊來源，系統可以模擬耳朵來在不同時間抵達的音效的體驗。 請注意，在 HoloLens，azimuth 往個人化，而提高權限模擬基礎 anthropometrics 平均組。 因此，提高精確度，可能比 azimuth 精確度較不精確。

音效的特性也會變更根據它們的環境。 比方說，喊叫的洞裡會導致您的聲音，彈開牆壁、 現場和上限，建立迴音效果。 空間的聲音的空間模型設定重現這些反射放置在特定的音訊環境中的音效。 您可以使用此設定，以符合使用者的實際位置為該空間中的音效模擬來建立更多人沉迷的音訊體驗。

## <a name="integrating-spatial-sound"></a>整合空間的音效

由於混合實境的一般原則是要地面[全像投影](hologram.md)應該在使用者的真實世界或虛擬環境，spatialized 從全像投影的大部分音效。 HoloLens，在有自然 CPU 和記憶體的預算考量，但您可以使用 10-12 空間音效語音那里同時使用小於 ~ 12%的 CPU （其中四個核心的 ~ 70%)。 建議的使用的空間音效語音包括：
* 視線 （反白顯示的物件，特別是當超出檢視） 的混合。 當雷射需要使用者的注意力時，則在該全像圖上播放音效 （例如具有虛擬 dog 樹皮）。 這可協助使用者尋找全像圖不在檢視中時。
* 音訊 Haptics （反應式音訊 touchless 互動）。 比方說，當使用者的手或移動控制站進入和離開筆勢框架時，才能播放的音效。 或當使用者選取雷射播放的音效。
* 深度 （環境的相關使用者的聲音）。

務必也請注意，雖然混用空間的音效標準立體聲音聽起來可能很有效地建立實際環境，是立體聲的音效應該要保留的空間的音效，例如反射 （細微層面的空間相對較無訊息距離提示），可能很難聽到吵雜的環境中。

Windows 的空間音效引擎只支援播放 48 的 k 取樣率。 大部分中的介軟體，例如 Unity，將會自動將音效檔轉換成支援的格式，但直接使用 Windows 音訊 Api 時請比對來影響所支援之格式內容的格式。

## <a name="see-also"></a>另請參閱
* [MR Spatial 220](holograms-220.md)
* [Unity 中的空間音效](spatial-sound-in-unity.md)
* [DirectX 中的空間音效](spatial-sound-in-directx.md)
* [空間音效設計](spatial-sound-design.md)
