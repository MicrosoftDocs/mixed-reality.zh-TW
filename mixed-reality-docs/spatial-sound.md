---
title: 混合現實中的音訊
description: 混合現實中的音訊可以增加使用者對 UI 互動的信心，並 immerse 使用者體驗。
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: 空間音效，環繞音效，3d 音訊，3d 音效，空間音訊
ms.openlocfilehash: 1930017903439aee3ac53b6c4be344fdc44c356f
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641110"
---
# <a name="audio-in-mixed-reality"></a>混合現實中的音訊
音訊是混合現實中設計和生產力的重要部分，而且可以：
* 提升使用者對筆勢和語音互動的信心
* 引導使用者進行後續步驟
* 有效率地結合虛擬物件與真實世界

混合現實耳機的低延遲標頭追蹤（包括 HoloLens）可讓您使用高品質的 HRTF 型 spatialization。 在您的應用程式中 Spatializing 音訊可以：
* 呼叫視覺元素的注意力
* 協助使用者維護其真實世界周圍的認知

新增聲場更深入地將全息連接到混合的世界，並且可以提供有關環境和物件狀態的提示。

如需使用音訊進行設計的詳細範例，請參閱[音效設計](spatial-sound-design.md)。

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

## <a name="using-sounds-in-mixed-reality"></a>在混合現實中使用音效
[使用混合現實中](spatial-sound-design.md)的音效，可能需要與觸控和鍵盤和滑鼠應用程式不同的方法。 關鍵的設計決策包括要 spatialize 哪些聲音，以及要 sonify 哪些互動。 這些決策可能會對使用者的信心、生產力和學習曲線造成很大的影響。

### <a name="case-studies"></a>案例研究
HoloTour 幾乎會讓使用者在世界各地旅遊和歷程記錄網站。 下列案例研究描述 HoloTour 的音效設計： HoloTour 的[音效設計](case-study-spatial-sound-design-for-holotour.md)。 用來捕捉主旨空間的特殊麥克風和轉譯設定。

RoboRaid 是 HoloLens 的高能源射擊。 下列案例研究描述的設計選擇，是為了確保已使用空間音訊來發揮最大效果： [RoboRaid 的音效設計](case-study-using-spatial-sound-in-roboraid.md)。

## <a name="spatialization"></a>Spatialization
Spatialization 是空間音訊的方向元件。 使用7.1 家用劇院設定時，spatialization 就像是在音量喇叭間移動一樣簡單。 但是，在混合式現實中，使用以 HRTF 為基礎的技術，是很重要的。 Windows 提供以 HRTF 為基礎的 spatialization，而這種支援是 HoloLens 2 上的硬體加速。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a>我應該 spatialize 嗎？
混合現實應用程式中的許多音效都受益于 spatialization，這會從接聽程式的頭部取得音效，並將其放在世界各地。 如需在應用程式中最有效使用 spatialization 的建議，請參閱[空間音效設計](spatial-sound-design.md)。

### <a name="spatializer-personalization"></a>空間定位器個人化
Hrtf 會操控各個頻率範圍內的各種層級和階段差異。 它們是根據實體模型以及人類 head、torso 和耳（pinnae）的度量。 我們的大腦會回應這些差異，以提供音效的方向。 

每個人都有獨特的 ear 圖形、標題大小和耳位置，因此最佳的 Hrtf 是符合您的選擇。 HoloLens 會使用您從頭戴式裝置顯示的 pupilary 距離（IPD）來增加 spatialization 的精確度，以調整您的前端大小 Hrtf。

### <a name="spatializer-platform-support"></a>空間定位器平臺支援
Windows 透過[ISPATIALAUDIOCLIENT API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)提供 spatialization，包括 hrtf。 此 API 會向應用程式公開 HoloLens 2 HRTF 硬體加速。

### <a name="spatializer-middleware-support"></a>空間定位器中介軟體支援
Windows ' Hrtf 的支援適用于一些協力廠商音訊引擎：
* [Unity 音訊引擎](spatial-sound-in-unity.md)外掛程式會呼叫 HRTF XAPO
* [Wwise 音訊引擎外掛程式](https://www.audiokinetic.com/products/plug-ins/msspatial/)會呼叫 ISpatialAudioClient API

## <a name="acoustics"></a>運轉
空間音訊可能會超過方向。 其他維度（包括遮蔽、障礙物、回音、portalling 和來源模型）統稱為「聲場」。 如果沒有聲場，hrtf 聽起來就沒有觀察距離。

聲場處理的範圍可以從簡單到非常複雜。 藉由使用任何音訊引擎所支援的簡單回音，您可以將 hrtf 推播到接聽程式周圍的環境中。 聲場系統（如[聲場專案](https://aka.ms/acoustics)）提供更豐富且更吸引人的聲場處理。 聲場專案可以在音效上建立牆、門和其他場景幾何的效果模型，這是在開發期間已知相關場景幾何的案例的有效選項。

