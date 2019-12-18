---
title: 混合現實中的音訊
description: 混合現實中的音訊可以增加使用者對 UI 互動的信心，並 immerse 使用者體驗。
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: 空間音效，環繞音效，3d 音訊，3d 音效，空間音訊
ms.openlocfilehash: b939433daf80a95a11bc0e1ac2ffd75dfe0cf299
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181978"
---
# <a name="audio-in-mixed-reality"></a>混合現實中的音訊
音訊是混合現實中設計和生產力的重要部分。 音效可以：
* 增加手勢和語音互動的使用者信賴度。
* 引導使用者進行後續步驟。
* 有效率地結合虛擬物件與真實世界。

混合現實耳機的低延遲標頭追蹤（包括 HoloLens）支援高品質的 HRTF 型 spatialization。 您可以在應用程式中 spatialize 音訊，以執行下列動作：
* 請注意視覺元素。
* 協助使用者維護其真實世界周圍的認知。

聲場更深入地將全息影像連線到混合現實世界。 它會提供有關環境和物件狀態的提示。

請參閱[使用音訊的設計詳細範例](spatial-sound-design.md)。

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
        <td><strong>功能</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens （第一代）</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>Spatialization</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>Spatialization 硬體加速</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="use-of-sounds-in-mixed-reality"></a>在混合現實中使用音效
[在混合現實中使用](spatial-sound-design.md)音效，需要的方法與觸控和鍵盤和滑鼠應用程式不同。 關鍵的設計決策包括要 spatialize 哪些聲音，以及要 sonify 哪些互動。 這些決策會強烈影響使用者信賴度、生產力和學習曲線。

### <a name="case-studies"></a>案例研究
HoloTour 幾乎會讓使用者在世界各地旅遊和歷程記錄網站。 請參閱 HoloTour 案例研究的[音效設計](case-study-spatial-sound-design-for-holotour.md)。 用來捕捉主旨空間的特殊麥克風和轉譯設定。

RoboRaid 是 HoloLens 的高能源射擊。 RoboRaid 案例研究的[音效設計](case-study-using-spatial-sound-in-roboraid.md)描述了用來確保空間音訊最大效果的設計選擇。

## <a name="spatialization"></a>Spatialization
Spatialization 是空間音訊的方向元件。 若為7.1 的家庭劇院設定，spatialization 就像在 loudspeakers 之間移動一樣簡單。 但對於混合式現實中的耳機，請務必使用 HRTF 型技術，以取得精確度和舒適度。 Windows 提供以 HRTF 為基礎的 spatialization，而這種支援是 HoloLens 2 上的硬體加速。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a>我應該 spatialize 嗎？
Spatialization 可以改善混合現實應用程式中的許多音效。 Spatialization 會從接聽程式的標頭中取出聲音，並將其放在世界各地。 如需在應用程式中有效使用 spatialization 的建議，請參閱[空間音效設計](spatial-sound-design.md)。

### <a name="spatializer-personalization"></a>空間定位器個人化
Hrtf 會操控各個頻率範圍內的各種層級和階段差異。 它們是根據實體模型以及人類 head、torso 和耳（pinnae）的度量。 我們的大腦會回應這些差異，以提供音效中的預期方向。

每個人都有獨特的 ear 圖形、標題大小和耳位置。 因此，最佳的 Hrtf 會符合您的規定。 為了增加 spatialization 的精確度，HoloLens 會使用耳機顯示器的 pupilary 間距離（IPD）來調整您的前端大小 Hrtf。

### <a name="spatializer-platform-support"></a>空間定位器平臺支援
Windows 透過[ISPATIALAUDIOCLIENT API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)提供 spatialization，包括 hrtf。 此 API 會向應用程式公開 HoloLens 2 HRTF 硬體加速。

### <a name="spatializer-middleware-support"></a>空間定位器中介軟體支援
Windows ' Hrtf 的支援適用于下列協力廠商音訊引擎。
* [Unity 音訊引擎外掛程式](spatial-sound-in-unity.md)
* [Wwise 音訊引擎外掛程式](https://www.audiokinetic.com/products/plug-ins/msspatial/)

## <a name="acoustics"></a>運轉
空間音訊大約是方向。 其他維度則包括遮蔽、障礙物、回音、portalling 和來源模型。 這些維度*統稱為聲場。* 如果沒有聲場，hrtf 音效就不會察覺距離。

聲場的治療範圍從簡單到非常複雜。 您可以使用任何音訊引擎支援的簡單回音，將 hrtf 的聲音推送至接聽程式的環境。 聲場系統（例如[聲場專案](https://aka.ms/acoustics)）可提供更豐富且更吸引人的聲場處理。 聲場專案可以在音效上建立牆、門和其他場景幾何的效果模型。 在開發階段已知相關場景幾何的案例中，這是有效的選項。

## <a name="next-steps"></a>後續步驟
- [Unity 中的空間音效](spatial-sound-in-unity.md)
- [如何在混合現實應用程式中使用音效](spatial-sound-design.md)
