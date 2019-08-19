---
title: 什麼是全像投影？
description: HoloLens 可讓您觀賞3d 的全息影像, 並與世界各地出現的光線和音效物件進行互動。
author: beaufolsom
ms.author: befolsom
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, 全息影像, 設計, 互動
ms.openlocfilehash: 714b08db23aa641252291aebe89fa3059c209a6f
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829777"
---
# <a name="what-is-a-hologram"></a>什麼是全像投影？

HoloLens 可讓您建立在世界各地顯示的**全息影像**、光線和音效的物件, 就像是真正的物件一樣。 全息影像會回應您的[注視](gaze.md)、[手勢](gestures.md)和[語音命令](voice-input.md), 並可與您的[真實世界表面](spatial-mapping.md)互動。 透過全息影像, 您可以建立屬於您世界的數位物件。

<br>

>[!VIDEO https://www.youtube.com/embed/MVXH5V8MVQo]

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
        <td>全息</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="a-hologram-is-made-of-light-and-sound"></a>全像投影是由光線和音效所組成

HoloLens[呈現](rendering.md)的全息影像會直接出現在使用者眼睛前方的全像攝影畫面中。 全像投影將光線新增至您的世界, 這表示您可以從顯示器和周圍查看光線。 HoloLens 並不會從眼睛中去除光線, 因此無法以黑色呈現全息影像。 而是以透明的方式顯示黑色內容。

全息影像可以有許多不同的外觀和行為。 有些是逼真且穩固的, 有些則是編排卡通和 ethereal。 全息影像可以反白顯示您的環境中的功能, 而且可以是應用程式使用者介面中的元素。

![全像地面的全像攝影狗](images/fang3-640px.jpg)

全像投影也可以製作[音效](spatial-sound.md), 這看起來就像您的環境中的特定位置。 在 HoloLens 上, 音效來自于位於您的耳的兩個喇叭, 而不會加以涵蓋。 與顯示器類似, 喇叭是加總的, 引進新的音效, 而不會封鎖環境中的音效。

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>您可以將全息全像位置放在世界或標籤中

當您有想要的全像投影的特定位置時, 可以將它精確[放](coordinate-systems.md)在世界上。 當您流覽該全像投影時, 其外觀會相對於您周圍的世界。 如果您使用[空間錨點](coordinate-systems.md#spatial-anchors), 將該物件牢固地釘選到世界, 那麼當您稍後返回時, 系統可能會記住您剩下的地方。

![Maquette 坐在桌上的全像大樓](images/image5-640px.png)

某些全息影像會改為遵循使用者。 這些加上標籤的全息影像位置本身相對於使用者, 無論他們在哪裡進行。 您甚至可以選擇帶您一段時間, 然後將它放在牆上, 一旦到達另一個房間。

**最佳作法**
* 在某些案例中, 您可能會需要在整個過程中, 讓全息影像保持容易探索或可見。 這種定位的高階方法有兩種。 讓我們將它們稱為「**顯示鎖定**」和「**主體鎖定**」。
   * 顯示鎖定的內容會 positionally 「鎖定」到裝置顯示。 這麼做的原因很多, 包括非自然的「clingyness」, 讓許多使用者感到挫折並想要「搖動」。 一般而言, 許多設計人員都發現它更適合用來避免顯示鎖定的內容。
   * 主體鎖定的方法遠 forgivable。 內文鎖定是指將全息行動網卡至使用者的主體或注視向量, 但位於使用者周圍的3d 空間中。 許多經驗都採用了內文鎖定行為, 其中的全息顯示「跟隨」使用者注視, 這讓使用者可以旋轉其內文, 並在空間中移動而不會遺失全息影像。 結合延遲可協助全息影像的移動更加自然。 例如, Windows 全像攝影作業系統的某些核心 UI, 會使用不同的內文鎖定, 並在使用者輪流時, 在使用者的注視之後, 使用一種非常類似彈性的延遲。
* 將全息影像放在舒適的觀賞距離, 通常是從 head 開始的大約1-2 計量。
* 針對必須持續在全像全像攝影框架中的專案提供漂移, 或考慮在使用者變更其觀點時, 將內容以動畫顯示到畫面的一邊。

**將全息影像放在最佳區域, 介於 1.25 m 和5m 之間**

兩個計量是最理想的, 而且體驗會降低您從一個計量取得的距離。 距離接近一計量的位置, 定期移動的全息影像較可能會有問題, 而不是固定的全息影像。 當內容太近關閉時, 請考慮適當地裁剪或淡出內容, 以免使用者進入非預期的體驗。

![從使用者處放置全息影像的最佳距離。](images/distanceguiderendering-640px.png)

## <a name="a-hologram-interacts-with-you-and-your-world"></a>全息與您和您的世界互動

全像投影不只是亮和音效;它們也是您世界中的活躍部分。 以您的手眼看一下全像投影和手勢, 而全息的形狀可以開始追蹤。 將語音命令提供給全息影像, 它可以回復。

![全像現實生活 motorcycle 的 motorcycle 設計](images/image8-640px.png)

全像投影可以讓個人互動不可能發生在其他地方。 因為 HoloLens 知道它在世界中的位置, 所以在您離開房間時, 全像攝影的字元可以直接在眼睛中找到。

全息影像也可以與您的環境互動。 例如, 您可以將全像跳動的球放在資料表上方。 然後, 使用 [點一下], 監看球彈, 並在[觸](gestures.md#air-tap)達資料表時發出音效。

影像也可以由真實世界的物件 pixels occluded。 例如, 全像攝影字元可能會逐步解說門, 而不是您所看到的背景。

**整合全息和真實世界的秘訣**
* 對應到 gravitational 規則可讓您更輕鬆地將全息與可信相關聯。 示例將全像攝影狗放在基礎上, & 花瓶在資料表上, 而不是將它們浮動在空間中。
* 許多設計人員發現, 他們甚至可以在全息桌上的表面上建立「負陰影」, 藉此 believably 整合全息影像。 其做法是在全像投影的基礎上建立軟性發光, 然後從發光中減去「陰影」。 軟性發光與真實世界的光線整合, 而陰影遮蔽了環境中的全息型。

## <a name="a-hologram-is-whatever-you-dream-up"></a>全像您的夢想

身為全像攝影的開發人員, 您可以將您的創意細分成2D 畫面, 並在世界各地。 *您*會建立什麼？

![生活空間中的全像虛構世界](images/designoverview.jpg)

## <a name="see-also"></a>另請參閱
* [空間音效](spatial-sound.md)
* [色彩、光線和材質](color,-light-and-materials.md)
