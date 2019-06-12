---
title: 什麼是全像投影？
description: HoloLens 可讓您檢視並與其互動三維全像投影，物件所做的光線和音效，會出現在您的世界。
author: beaufolsom
ms.author: befolsom
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、 HoloLens、 全像投影、 設計、 互動
ms.openlocfilehash: 714b08db23aa641252291aebe89fa3059c209a6f
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829777"
---
# <a name="what-is-a-hologram"></a>什麼是全像投影？

HoloLens 可讓您建立**全像投影**、 物件所做的光線和音效，會出現在世界各地，就如同它們是真正的物件。 全像投影回應您[視線](gaze.md)，[筆勢](gestures.md)並[語音命令](voice-input.md)，並可進行互動[真實世界介面](spatial-mapping.md)看待您。 使用全像投影，您可以建立屬於您的世界的數位物件。

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
        <td><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沈浸式耳機</strong></a></td>
    </tr>
     <tr>
        <td>全像投影</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="a-hologram-is-made-of-light-and-sound"></a>雷射組成光線和音效

全像投影的 HoloLens[呈現](rendering.md)會出現在全像攝影版的畫面格，直接呈現使用者的眼睛。 全像投影會加入您的世界裡，這表示您看到從顯示的光線和從周圍環境光中的光線。 HoloLens 不移除 light 眼睛，讓全像投影無法轉譯色彩黑色。 相反地，黑色的內容會顯示為透明。

全像投影可以有許多不同的外觀和行為。 一些實際並選取 實線，而其他人 cartoonish 和把。 全像投影可以反白顯示功能的光線，並且可以在您的應用程式使用者介面中的項目。

![地板上逐一查看的 dog 全像攝影版](images/fang3-640px.jpg)

也可以將全像投影[音效](spatial-sound.md)，這會顯示為來自在周圍環境中的特定位置。 在 HoloLens，聽起來是來自兩個位於正上方 되 어，而不涵蓋它們的主講人。 類似於顯示器，主講人是加總，而不會封鎖您的環境的聲音引進新的音效。

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>全像可以放置在全球或配合您的標記

當您有想讓雷射的特定位置時，您可以[放置](coordinate-systems.md)其中精確地世界中。 逐步解決該全像圖時，它會顯示相對於您的世界穩定。 如果您使用[空間的錨點](coordinate-systems.md#spatial-anchors)釘選穩固地以全球該物件，系統可以甚至記住離開的地方它時您後續返回頁面。

![坐在資料表上的全像攝影版建置 maquette](images/image5-640px.png)

某些全像投影請改為遵循使用者。 這些 tag-along 全像投影會將本身相對於使用者，無論他們逐步解說的位置。 您甚至可以選擇來與您全像一段時間，並再將它放在塗鴉牆上一旦您取得另一個房間內。

**最佳作法**
* 某些情況下可能會要求全像投影，維持輕鬆探索或可見的體驗。 有兩種高層級的方法，以這種定位。 暫且把他們 **「 顯示鎖定 」** 並 **「 主體鎖定 」** 。
   * 顯示鎖定的內容是依位置來建立 「 鎖定 」 裝置螢幕。 弔詭的多種原因所造成，包括 「 clingyness 」，讓許多使用者受挫非自然掌控，且想要"shake 它。 」 一般情況下，許多設計工具中發現最好避免顯示鎖定的內容。
   * 主體鎖定方法是更 forgivable。 主體鎖定時，雷射行動網卡的使用者主體或視線向量，但位於使用者周圍的 3d 空間中。 許多體驗已採用其中全像 「 遵循 」 使用者視線，可讓使用者旋轉其主體，並移動空間，而不會遺失全像本文鎖定的行為。 併入延遲有助於感覺更自然的全像移動。 比方說，一些核心 Windows 全像攝影版作業系統的 UI 會在接下來溫和，類似彈性的延遲時間的使用者的視線，當使用者開啟腦袋內文-鎖定使用變化。
* 在置入全像舒適的檢視距離通常約 1-2 俖籇標頭。
* 提供必須持續在全像攝影版的框架內，或請考慮當使用者變更他們的觀點來看，以動畫顯示您的內容，顯示的某一端的項目數量漂移。

**全像投影置於 「 最佳 」 區域-1.25 m 和 5 分鐘之間**

兩個計量是最適合的並體驗將會降低您從一個計量的取得越快。 越重要比一個計量表距離，定期移動防禦全像投影是更有可能是比 「 定態全像投影有問題。 建議您依正常程序裁剪或淡出您的內容，當它取得太接近來為未 jar 使用者到未預期的體驗。

![對於將使用者從全像投影的最佳距離。](images/distanceguiderendering-640px.png)

## <a name="a-hologram-interacts-with-you-and-your-world"></a>您和您的世界互動全像

全像投影不只需光線和音效;它們也是世界的您中作用中的部份。 在全像和您用手，筆勢的視線雷射可以開始依照您。 以全像圖中，所發出的語音命令，它可以回覆。

![納入實際 motorcycle 主體上的全像攝影版 motorcycle 設計](images/image8-640px.png)

全像投影可讓個人在其他地方不可行的互動。 由於 HoloLens 知道其所在的世界中，全像攝影版的字元可以查看您直接眼睛逐步房間周圍。

雷射也可以與周圍環境互動。 例如，您可以放置全像攝影版的彈跳球，上述資料表。 然後，再[空中點選](gestures.md#air-tap)，觀看球彈，並讓音效，當它叫用的資料表。

真實世界物件也可以阻擋全像投影。 例如，透過門後，請在牆上、 您使其看不可能會逐步引導全像攝影版的字元。

**整合全像投影和真實世界的秘訣**
* 對齊重力規則可讓全像投影，與相關的工作變得更容易且更可信。 例如：將全像攝影版的 dog 放在地上 & 花瓶資料表上的，而不是讓它們在空間中浮動。
* 許多設計工具中發現，甚至更 believably 可以藉由建立全像正坐在介面上的 「 負值陰影 」 整合全像投影。 他們這麼做，藉由建立周圍全像地面上的虛光暈，並再減去 「 影子 」 從光暈。 軟光暈整合在現實世界中光線和陰影 grounds 全像在環境中。

## <a name="a-hologram-is-whatever-you-dream-up"></a>雷射是您一起完成的任何內容

身為全像攝影版的開發人員，您必須能夠中斷您的創意出 2D 螢幕並進入您的世界。 項目有哪些*您*建置？

![在客廳中全像攝影版的虛數世界](images/designoverview.jpg)

## <a name="see-also"></a>另請參閱
* [空間音效](spatial-sound.md)
* [色彩、光線和材質](color,-light-and-materials.md)
