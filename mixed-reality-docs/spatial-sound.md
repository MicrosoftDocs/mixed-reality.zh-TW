---
title: 空間音效
description: 在混合現實應用程式中使用空間音效，可以讓您 convincingly 將音效放在3D 空間中。
author: hak0n
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: 空間音效，環繞音效，3d 音訊，3d 音效，空間音訊
ms.openlocfilehash: 31ec8f88a060127daab9bf3afc970457ec7c90a3
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437400"
---
# <a name="spatial-sound"></a>空間音效

當物件不在我們的視線時，我們可以透過音效來觀察目前的狀況。 在 Windows Mixed Reality 中，音訊引擎會使用方向、距離和環境模擬來模擬3D 音效，以提供混合現實體驗的以聽覺方式元件。 在應用程式中使用空間音效，可以讓開發人員 convincingly 在使用者周圍，以3維空間（球體）來放置聲音。 這些聽起來好像是來自實際的實體物件，或是使用者周圍的混合現實全息。 由於[全息影像](hologram.md)是物件的光線，有時也是音效，因此音效元件可協助基礎的全像投影，使其更可信，並建立更有沉浸的體驗。

雖然全息影像只會以視覺化方式出現在使用者的眼睛指向何處，但您應用程式的音效可能來自所有方向;上方、下方、後面、到側邊等等。您可以使用這項功能，對可能目前不在使用者觀點中的物件繪製注意力。 使用者可以察覺從混合現實世界中的來源 mouseleave 的音效。 例如，當使用者接近物件，或物件接近其時，磁片區就會增加。 同樣地，當物件在使用者之間移動時，或相反的，空間音效會提供聲音直接來自物件的假像。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>特徵</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (第 1 代)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>空間音效</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️（含耳機）</td>
    </tr>
</table>

## <a name="simulating-the-perceived-location-and-distance-of-sounds"></a>模擬聲音的認知位置和距離

藉由分析音效如何達到我們的耳，我們的大腦會決定物件發出音效的距離和方向。 HRTF （或標頭相關的傳送函式）會藉由建立 spectral 回應的模型來模擬這項互動，以說明耳如何從空間的角度來接收音效。 空間音效引擎使用個人化的 Hrtf 來擴展混合現實體驗，並模擬來自各種方向和距離的聲音。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

左或右音訊（azimuth）提示源自于每個耳的音效抵達時間差異。 向上和向下提示來自外部耳圖形（pinnae）所產生的 spectral 變更。 藉由指定音訊的來源，系統可以模擬在不同時間到達我們的耳的音效體驗。 請注意，在 HoloLens 上，當 azimuth spatialization 是個人化時，提高許可權的模擬是以一組平均的 anthropometrics 為基礎。 因此，提高許可權精確度可能會比 azimuth 精確度更不精確。

音效的特性也會根據其存在的環境而變更。 比方說，cave 中的 shouting 會讓您的聲音從牆、地面和上限中退出，並建立 echo 效果。 空間音效的房間模型設定會重現這些反射，以將聲音放在特定的音訊環境中。 您可以使用這項設定來比對使用者在該空間中模擬音效的實際位置，以建立更多沉浸的音訊體驗。

## <a name="integrating-spatial-sound"></a>整合空間音效

因為混合現實的一般原則是要在使用者的實體世界或虛擬環境中接地[全息影像](hologram.md)，所以大部分來自全息的聲音都應該 hrtf。 在 HoloLens 上，有自然的 CPU 和記憶體預算考慮，但是您可以在該處使用10-12 空間音效，同時使用低於 ~ 12% 的 CPU （70約四個核心的其中一個）。 適用于空間音效語音的建議用法包括：
* 注視混合（反白顯示物件，特別是在外）。 當全息影像需要使用者注意時，請在該全息影像上播放音效（例如，有虛擬狗吠）。 這可協助使用者在未觀賞時尋找全息影像。
* 音訊 Haptics （適用于 touchless 互動的被動音訊）。 例如，當使用者的手或運動控制器進入並結束手勢畫面時，播放音效。 或在使用者選取全息影像時播放音效。
* 深度（使用者周圍的環境音效）。

也請務必注意，在混合標準身歷聲音效與空間音效時，可以有效地建立實際的環境，身歷聲音效應該相對無意義，以留出空間音效的細微部分，例如反射（距離提示），在雜訊的環境中可能很容易聽到。

Windows 的空間音效引擎僅支援播放的48k 取樣率。 大部分中介軟體（例如 Unity）都會自動將音效檔轉換成支援的格式，但當您直接使用 Windows 音訊 Api 時，請將內容格式與效果所支援的格式進行比對。

## <a name="see-also"></a>請參閱
* [MR 空間220](holograms-220.md)
* [Unity 中的空間音效](spatial-sound-in-unity.md)
* [DirectX 中的空間音效](spatial-sound-in-directx.md)
* [空間音效設計](spatial-sound-design.md)
