---
title: 目光和行動
description: 「注視和認可」輸入模型的一般總覽-使用眼睛或 head 輸入。
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Mixed Reality，注視，注視目標，互動，設計，眼睛追蹤，head 追蹤
ms.openlocfilehash: c44c1a75e831869a3ed4d12bb6c9e87c478daf56
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83866888"
---
# <a name="gaze-and-commit"></a>目光和行動

_注視和認可_是一種基本的輸入模型，與我們使用滑鼠進行互動的方式密切相關： _Point & 按一下_。
在此頁面上，我們引進兩種類型的注視輸入（head 和眼睛）和不同類型的認可動作。 
_注視和認可_會被視為具有間接操作的輸入模型。
這表示它最適合用來與不在手中的全像攝影內容互動。

混合現實耳機可以使用使用者頭部的位置和方向來判斷其前端方向向量。 您可以將此視為直接從使用者的雙眼之間向前直指的雷射。 這是相當粗略的使用者觀看位置概算。 您的應用程式可以將此光線與虛擬或真實世界的物件相交，並在該位置繪製游標，讓使用者知道它們目前的目標為何。

除了眼睛外，某些混合現實耳機（如 HoloLens 2）包含了產生眼睛向量的監看式追蹤系統。 這會對使用者觀看的位置提供精細的測量。 在這兩種情況下，注視代表使用者意圖的重要信號。 系統能夠解讀和預測使用者的期望動作，使用者滿意度增加並提升效能。

以下幾個範例會說明如何讓混合現實開發人員受益于 head 或眼睛：
* 您的應用程式可以與場景中的全息影像相交，以判斷使用者注意的位置（更精確的眼睛）。
* 您的應用程式可以根據使用者的注視來進行通道手勢和控制器按下動作，讓使用者順暢地選取、啟動、抓取、滾動，或以其他方式與其全息影像互動。
* 您的應用程式可讓使用者在真實世界的表面上放置全息影像，方法是將其注視光線與空間對應網格相交。
* 您的應用程式可以知道使用者何時看*不*到重要物件的方向，這可能會導致您的應用程式提供視覺和音訊提示來轉向該物件。

<br>


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
        <td>頭部注視並認可</td>
        <td>✔️ 建議使用</td>
        <td>✔️ 建議使用 (第三個選擇 - <a href="interaction-fundamentals.md">查看其他選項</a>)</td>
        <td>➕ 替代選項</td>
    </tr>
         <tr>
        <td>眼部注視並認可</td>
        <td>❌無法使用</td>
        <td>✔️ 建議使用 (第三個選擇 - <a href="interaction-fundamentals.md">查看其他選項</a>)</td>
        <td>❌無法使用</td>
    </tr>
</table>


## <a name="gaze"></a>注視

### <a name="eye--or-head-gaze"></a>眼睛或列印頭？
當您遇到問題時，應該考慮幾個考慮，不論您是否應該使用「眼睛與認可」或「列印頭和認可」輸入模型。 如果您是針對沉浸式耳機或 HoloLens （第1代）進行開發，則選擇很簡單： Head 注視和認可。 如果您是針對 HoloLens 2 進行開發，則選擇會變得有點困難，這就是了解每一項的優點和挑戰的重要性。
我們在下表中編譯了一些廣泛的 pro 和 con，以對比「前端與眼睛」目標。 這不是完整的，因此我們建議您在這裡瞭解混合現實中的眼睛目標：
* [Hololens 上的眼睛追蹤 2](eye-tracking.md)：在 hololens 2 上引進新眼追蹤功能的一般簡介，包括一些開發人員指引。 
* [眼睛互動](eye-gaze-interaction.md)：規劃使用眼睛追蹤做為輸入時的設計考慮和建議。

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><strong>眼睛目標</strong></td>
        <td><strong>頭部注視定向</strong></td>
    </tr>
    <tr>
        <td>地!</td>
        <td>一點</td>
    </tr>
    <tr>
        <td>低度（幾乎所有的主體移動都是必要的）</td>
        <td>可能是 fatiguing 的 discomfort （例如，頸部壓力）</td>
    </tr>
    <tr>
        <td>不需要資料指標，但建議使用細微的意見反應</td>
        <td>需要顯示資料指標</td>
    </tr>
    <tr>
        <td>不會順暢地移動–例如，不適合繪製</td>
        <td>更具控制和明確</td>
    </tr>
    <tr>
        <td>非常小的目標很困難（例如，小按鈕或 weblinks）</td>
        <td>可靠! 絕佳的回復！</td>
    </tr>
    <tr>
        <td>...</td>
        <td>...</td>
    </tr>
</table>

不論您使用的是注視或監看式輸入模型，都隨附不同的設計條件約束集合，這些限制將會分別涵蓋在[眼睛和認可](gaze-and-commit-eyes.md)和[認可](gaze-and-commit-head.md)文章中。

<br>

---

### <a name="cursor"></a>資料指標

:::row:::
    :::column:::
        對於列印頭，大部分的應用程式都應該使用[游標](cursors.md)（或其他聽覺/視覺指示），讓使用者能夠信賴他們要與之互動的物件。 您通常會將此游標置於世界中，其前端光線會先與物件相交，這可能是全息影像或真實世界表面。<br>
        <br>
        就眼睛而言，我們通常建議*不要*顯示游標，因為這可能會很快就會變得令人困擾，而且不會讓使用者雜亂。 相反地，反白顯示視覺效果目標，或使用非常不好的眼游標，讓您安心瞭解使用者的互動方式。 如需詳細資訊，請查看我們在 HoloLens 2 上[以眼睛為基礎之輸入的設計指引](eye-tracking.md)。
    :::column-end:::
        :::column:::
       ![顯示注視的視覺化游標範例](images/cursor.jpg)<br>
       *影像：顯示注視的視覺化游標範例*
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a>Commit
_在談到某個_目標的不同方式之後，讓我們更進一步討論_注視和認可_的_認可_部分。
以物件或 UI 元素為目標之後，使用者可以使用次要輸入進行互動或按一下。 這就是所謂的輸入模型認可步驟。 

支援的認可方法如下：
- 點按手勢（也就是在您的前方舉手，並結合您的食指和拇指）
- 說「 _select_ 」或其中一個目標語音命令
- 在[HoloLens Clicker](https://docs.microsoft.com/hololens/hololens1-clicker)上按一個按鈕
- 按下 Xbox 遊戲台上的 [A] 按鈕
- 按 Xbox 調適型控制器上的 [A] 按鈕

### <a name="gaze-and-air-tap-gesture"></a>注視和碰點手勢
空中點選是手部直立的點選手勢。 若要執行點一下，請將您的索引指向準備好的位置，然後將您的 thumb 縮小，然後將索引手指的備份提升至發行。 在 HoloLens （第1代）上，空中碰是最常見的次要輸入。


:::row:::
    :::column:::
       ![觸達就緒位置](images/readyandpress-ready.jpg)<br>
       **觸達就緒位置**<br>
    :::column-end:::
    :::column:::
       ![按下手指以點按或按一下](images/readyandpress-press.jpg)<br>
        **按下手指以點按或按一下**<br>
    :::column-end:::
:::row-end:::


您也可以在 HoloLens 2 上使用空中按鍵功能。 它已從原始版本中放寬。 幾乎所有類型的 pinches 現在都可支援，只要手是直立的，而且仍然保留。 這可讓使用者更容易了解和執行手勢。 這個新的空中點會透過相同的 API 取代舊的，因此現有的應用程式會在重新編譯 HoloLens 2 之後自動擁有新的行為。

<br>

---

### <a name="gaze-and-select-voice-command"></a>注視和「選取」語音命令
語音命令是混合現實中的其中一種主要互動方法。 它提供了一種非常強大的無人參與機制來控制系統。 語音互動模型有不同的類型：

- 執行 click actuation 或 commit 做為次要輸入的泛型 "Select" 命令。
- 物件命令（例如「關閉」或「使它變大」）會執行並認可動作做為次要輸入。
- 全域命令（例如「移至開始」）不需要目標。
- 對話使用者介面或 Cortana 等實體具有 AI 自然語言功能。
- 自訂語音命令

若要瞭解更多詳細資料以及可用語音命令的完整清單，以及如何使用它們，請參閱我們的[語音命令](voice-design.md)指引。

<br>

---


### <a name="gaze-and-hololens-clicker"></a>注視和 HoloLens Clicker

:::row:::
    :::column:::
        HoloLens Clicker 是專為 HoloLens 建立的第一個週邊裝置。 它隨附在 HoloLens （第1代）開發版本中。 HoloLens Clicker 可讓使用者按一下最少的手運動，並認可為次要輸入。 HoloLens Clicker 會使用藍牙低功耗（BTLE）連接到 HoloLens （第1代）或 HoloLens 2。<br>
        <br>
        [配對裝置的詳細資訊和指示](hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *映射： HoloLens Clicker*
    :::column-end:::
        :::column:::
       ![HoloLens Clicker](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a>注視和 Xbox 無線控制器

:::row:::
    :::column:::
        Xbox 無線控制器會使用 [A] 按鈕，以次要輸入的形式執行按一下 actuation。 裝置會對應至一組預設的動作，以協助流覽和控制系統。 如果您想要自訂控制器，請使用 Xbox 配件應用程式來設定您的 Xbox 無線控制器。<br>
        <br>
        [如何將 Xbox 控制器與您的電腦配對](hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *映射： Xbox 無線控制器*
    :::column-end:::
        :::column:::
       ![Xbox 無線控制器](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a>注視和 Xbox 適應性控制器
Xbox 調調適型控制器是主要為了滿足行動裝置的需求，而這是一種整合式集線器，可協助讓混合現實更容易存取。

Xbox 調適型控制器會使用 [A] 按鈕，以次要輸入的形式執行按一下 actuation。 裝置會對應至一組預設的動作，以協助流覽和控制系統。 如果您想要自訂控制器，請使用 Xbox 配件應用程式來設定 Xbox 調適型控制器。

![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)<br>
*Xbox Adaptive Controller*

連接外部裝置（例如交換器、按鈕、掛接和搖桿），以建立唯一的自訂控制器體驗。 按鈕、操縱杆和觸發程式輸入都是由透過 3.5 mm 插座和 USB 埠連線的輔助裝置所控制。

![Xbox Adaptive Controller 連接埠](images/xbox-adaptive-controller-ports.jpg)<br>
*Xbox Adaptive Controller 連接埠*

[裝置配對指示](hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>在 Xbox 網站上可取得更多資訊</a>

<br>

---

## <a name="composite-gestures"></a>複合手勢

### <a name="air-tap"></a>空中點選
[空中] 手勢（以及下面的其他手勢）只會對特定點碰做出回應。 您的應用程式必須直接使用上述兩個主要元件手勢一節中所述的較低層級互動，以偵測其他功能表或抓住。

### <a name="tap-and-hold"></a>點一下並按住
按住只是維持空中點選的手指朝下位置。 結合 [按下] 和 [按住]，可讓您在結合 arm 動作（例如，挑選物件，而不是啟動它或 mousedown 次要互動，例如顯示操作功能表）時，使用各種較複雜的「按一下並拖曳」互動。
不過，針對這個手勢進行設計時應格外小心，因為使用者很容易在任何延伸手勢的過程中放鬆其手勢。

### <a name="manipulation"></a>操作
當您想要讓全像投影對使用者的移動進行1:1 回應時，可以使用操作手勢來移動、調整大小或旋轉全息形狀。 這類 1:1 移動的用途之一是要讓使用者可以實際繪圖。
操作手勢的初始定向應經由注視或指向來完成。 當點一下和按住開始時，物件的任何操作都是由手動移動處理，讓使用者在操作時能夠四處尋找。

### <a name="navigation"></a>瀏覽
瀏覽手勢的運作方式如同虛擬搖桿，可用來瀏覽 UI 小工具，例如放射狀功能表。 您可點選並按住來啟動手勢，然後在標準化 3D Cube (在初次按壓時置中) 中移動您的手。 您可以將您的手沿著 X、 Y 或 Z 軸從值 -1 移到 1 (而 0 表示起點)。
瀏覽可用來建置以速度為基礎的連續捲動或縮放手勢，類似於藉由按一下滑鼠中間按鈕，然後上下移動滑鼠來捲動 2D UI。

與 rails 的導覽指的是在特定軸中辨識移動的能力，直到達到該軸上的特定臨界值為止。 這僅適用于開發人員在應用程式中啟用多個軸的移動時，例如，如果應用程式設定為在 X、Y 軸上辨識導覽手勢，但也使用 rails 指定 X 軸。 在此情況下，如果 Y 軸上也發生手移動，系統將會辨識 X 軸上的手上移動，前提是它們會保留在 X 軸上的虛數滑軌（guide）中。

在 2D 應用程式內，使用者可以使用垂直瀏覽手勢在應用程式內捲動、縮放或拖曳。 這會在應用程式中插入虛擬手指觸控，以模擬同類型的觸控手勢。 使用者可以藉由選取按鈕或說「<Scroll/拖曳/縮放> 工具」，在應用程式上方的工具之間切換，藉以選取要執行的動作。

[複合手勢的詳細資訊](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a>手勢辨識器

使用手勢辨識的其中一個優點是，您可以只針對目前目標的全息影像可以接受的手勢設定手勢辨識器。 平臺只會視需要去除混淆，以區別那些特定支援的手勢。 如此一來，只支援「點按」的全像投影可以接受按下和放開之間的任何時間長度，而支援兩個點按和按住的全像投影則可以在按住時間臨界值之後，將點擊次數提升至保留。

## <a name="hand-recognition"></a>手部辨識
HoloLens 可藉由追蹤裝置可見的任一手或雙手位置來辨識手勢。 當手部處於就緒狀態 (手背朝向您且食指朝上) 或按下狀態 (手背朝向您且食指朝下) 時，HoloLens 就會看見手部。 當手上有其他人時，HoloLens 會忽略它們。
對於 HoloLens 偵測到的每一手勢，您都可以存取其位置，而不需要方向和其按下狀態。 當手部接近手勢框架邊緣時，您也會取得方向向量，而您可對使用者顯示該向量，讓他們知道如何移動其手部以回到 HoloLens 可看見手部的位置。

## <a name="gesture-frame"></a>手勢框架
對於 HoloLens 上的手勢，手必須位於手勢框架內，筆勢檢測攝影機可以適當地查看，從鼻子到 waist，以及在肩膀之間。 使用者必須在此辨識區域上訓練，以進行動作的成功並讓自己的緩和。 許多使用者一開始會假設筆勢框架必須透過 HoloLens 在其觀看範圍內，並將其 uncomfortably 以進行互動。 使用 HoloLens Clicker 時，不需要將手放在筆勢框架中。

特別是在連續手勢的情況下，使用者在移動全像投影物件時，會有一些風險會將其手移至手勢框架外，例如，並失去其預期的結果。

您應該考量下列三個事項：

- 筆勢框架的存在和大致界限的使用者教育。 這會在 HoloLens 設定期間進行講授。

- 當使用者的手勢接近或中斷應用程式內的手勢框架邊界時，會通知他們，而失去的手勢會導致不想要的結果。 研究已顯示這類通知系統的重要品質。 HoloLens shell 會在中央游標上提供這種類型通知的良好範例--視覺效果，指出發生邊界相交的方向。

- 您應該將突破手勢框架界限的後果最小化。 一般來說，這表示手勢的結果應該在界限停止，而不是反轉。 例如，如果使用者在房間內移動一些全像攝影物件，則在軌跡框架遭到入侵時，移動應該會停止，而不會傳回至起點。 使用者可能會遇到一些挫折，但可能會更快速地瞭解界限，而不必每次都重新開機其完整的預期動作。



## <a name="see-also"></a>另請參閱
* [眼動式互動](eye-gaze-interaction.md)
* [HoloLens 2 的眼球追蹤](eye-tracking.md)
* [目光和停駐](gaze-and-dwell.md)
* [手 - 直接操作](direct-manipulation.md)
* [手 - 手勢](gaze-and-commit.md#composite-gestures)
* [手 - 指向和行動](point-and-commit.md)
* [本能互動](interaction-fundamentals.md)
* [語音輸入](voice-input.md)

