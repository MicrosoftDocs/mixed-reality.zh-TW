---
title: Head 視線與認可
description: Head 視線和 commit 輸入模型的概觀
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合實境，視線、 視線目標，就會有互動，設計
ms.openlocfilehash: 95f2cef8c10ce3d0d2a218953613fef6f0a00362
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730814"
---
# <a name="head-gaze-and-commit"></a>Head 視線與認可
Head 視線和認可為牽涉到目標物件的向前指您前端 （head-方向）、 方向與輸入的模型，然後處理它與次要輸入例如空中點選手筆勢或語音命令"Select"。 它會被視為 「 目前 」 輸入的模型與間接的操作，這表示它最適合用於互動超過手臂觸達的內容。

## <a name="device-support"></a>裝置支援

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>輸入的模型</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沈浸式耳機</strong></a></td>
    </tr>
     <tr>
        <td>Head 視線與認可</td>
        <td>建議的 ✔️</td>
        <td>✔️ 建議 (第三個選擇-<a href="interaction-fundamentals.md">查看其他選項</a>)</td>
        <td>➕ 替代選項</td>
    </tr>
</table>

## <a name="head-gaze"></a>Head 視線
混合的實境耳機使用位置和方向的使用者的標頭來判斷其前端方向的向量。 您可以將此視為直接在使用者的眼睛之間直接繼續點從雷射。 這是很粗略的使用者正在尋找其中的近似值。 您的應用程式可以交集此光線，具有虛擬或實際物件，並在該位置，以讓使用者知道什麼它們的目前目標繪製資料指標。

除了前端的視線，例如 HoloLens 2 一些混合的實境耳機會包含追蹤產生眼睛視線向量的系統。 這會提供精細的測量的使用者注視的位置。 可建置視線並認可使用眼睛視線互動，但這是隨附一組非常不同的設計上的限制，將會分別在涵蓋這[追蹤文章的眼睛](eye-tracking.md)。

## <a name="commit"></a>認可
目標物件或 UI 項目之後, 使用者就可以互動或者 「 按一下 」 使用之次要輸入。 這就是模型的認可步驟。 支援下列的 commit 方法：

- 空中點選手勢
- 將語音命令 「 Select 」，或其中一個目標的語音命令
- 按下的單一按鈕[HoloLens Clicker](hardware-accessories.md#hololens-clicker)
- 按下 'A' 上的 Xbox 遊戲台
- 按下 'A' 上的 Xbox 調適性控制器

### <a name="head-gaze-and-air-tap-gesture"></a>Head 視線和空中點選手勢
空中點選是點選手勢與垂直手持。 若要執行空中點選、 引發食指為準備的位置，則捏合以拇指和食指引發備份，以釋放。 HoloLens 1 空中點選是最常見的第二個輸入。

![在準備好位置，然後點選或按一下 移動手指](images/readyandpress.jpg)<br>

空中點選也會提供在 HoloLens 2，它具有與原始版本已經放寬。 現在支援幾乎所有類型的 pinches，只要手形椅背與股仍然是。 這可讓您了解，並執行動作的使用者更容易。  讓現有的應用程式將會自動取得新的行為，在重新編譯 HoloLens 2 之後，這個新的空中點選會取代舊的憑證，透過相同的 API。

### <a name="head-gaze-and-select-voice-command"></a>Head 視線和 「 選取 」 語音命令
語音命令是其中一種主要的互動方法，在混合實境上。 它提供非常強大的 「 實際操作免費 」 機制，來控制系統。 有的語音互動模型的 diferent 類型：

- [選取]，一般的命令，可讓執行 [按一下] 時閉路或做為第二個輸入的認可。
- 物件命令，例如 「 關閉 」 或 「 放大 」，可讓執行並認可至做為次要輸入動作。
- 全域 commnads，例如 移至 開始 並不需要為目標。
- 交談的使用者介面或實體，例如 Cortana 具有 AI 自然語言功能。
- 自訂 commnads

若要尋找更多詳細資料和可用的命令以及如何使用 comprenhesive 清單，請查看我們[語音設計](voice-design.md)指引。


### <a name="head-gaze-and-hololens-clicker"></a>Head 視線和 HoloLens Clicker
HoloLens Clicker 是專為 HoloLens 建置第一個周邊裝置，並隨附 HoloLens 1 Development Edition。 HoloLens Clicker 可讓使用者按一下 以最少的手動動作，並認可為次要輸入。 HoloLens clicker 會連接到 HoloLens 1 或 2 使用藍牙低能源 (BTLE)。

![](images/hololens-clicker-500px.jpg)<br>
HoloLens Clicker

您可以找到詳細資訊和指示，來配對裝置[這裡](hardware-accessories.md#pairing-bluetooth-accessories)




### <a name="head-gaze-and-xbox-wireless-controller"></a>Head 視線和 Xbox 無線控制器
Xbox 無線控制器可讓執行 [按一下] 時閉路做為次要輸入使用的按鈕。 裝置會對應至一組預設的動作，協助您瀏覽和控制系統。 如果您想要自訂控制器，請設定您的 Xbox 無線控制站使用 Xbox Accesories 應用程式。

![](images/xboxcontroller.jpg)<br>
Xbox 無線控制器

[配對您的 PC 與 Xbox 控制器](hardware-accessories.md#pairing-bluetooth-accessories)


### <a name="head-gaze-and-xbox-adaptive-controller"></a>Head 視線和 Xbox 的自適性控制器
主要設計用來透過有限的行動性需求的玩家，Xbox 調適性控制器是可協助您更方便使用混合實境聯合的中樞的裝置。

Xbox 調適性控制器可讓執行 [按一下] 時閉路做為次要輸入使用的按鈕。 裝置會對應至一組預設的動作，協助您瀏覽和控制系統。 如果您想要自訂控制器，請設定 Xbox 調適性控制器使用 Xbox Accesories 應用程式。

![](images/xbox-adaptive-controller-devices.jpg)<br>
Xbox 調適性控制器

連線外部的裝置，例如參數、 按鈕、 掛接，以及建立唯一是您的自訂控制站體驗搖桿。 按鈕、 搖桿和觸發程序的輸入被控制與輔助透過 3.5 公釐端子與 USB 連接埠連線的裝置。

![](images/xbox-adaptive-controller-ports.jpg)<br>
Xbox 調適性控制器的連接埠

[指示裝置配對](hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/en-US/xbox-one/accessories/controllers/xbox-adaptive-controller>更多可用的資訊 Xbox 網站上</a>


# <a name="head-gaze-design-guidelines"></a>Head 視線設計指導方針
> [!NOTE]
> 特定視線設計的詳細指引[即將推出](index.md)。

## <a name="head-gaze-targeting"></a>Head 視線目標
使用者能夠針對他們想要進行互動，無論輸入強制回應性的項目所建立的所有互動。 在 Windows Mixed Reality，這通常是使用使用者的視線。
若要啟用的使用者，才能順利運作的體驗，系統的導出了解使用者的意圖，以及使用者的實際的意圖，必須為儘可能密集地對齊。 程度系統解譯使用者的預定的動作正確，增加滿意度和效能改善。


## <a name="target-sizing-and-feedback"></a>目標大小和意見反應
視線向量可能會重複用來順利的目標，但通常最適合 gross 目標 （取得較大目標）。 1 到 1.5 度的最小目標大小應該在大部分情況下，允許成功的使用者動作，但目標 3 度通常可讓較快的速度。 請注意，使用者目標實際上是 3D 元素--即使 2D 區域的大小任何投影面向它們應該將目標設為區域。 提供一些主要的項目是 「 作用中 」 （該使用者以其為目標） 的提示會非常有用-這可能包括經過處理，例如顯示 「 暫留 」 效果、 音效反白顯示或需按幾下，或清除元素的資料指標的對齊方式。

![2 個計量表距離的最佳目標大小](images/gazetargeting-size-1000px.jpg)<br>
*2 個計量表距離的最佳目標大小*

![舉例來說，反白顯示的視線目標的物件](images/gazetargeting-highlighting-640px.jpg)<br>
*舉例來說，反白顯示的視線目標的物件*

## <a name="target-placement"></a>目標位置
使用者將通常無法找到位於很高或極低的 UI 項目中的視角，將焦點放在周圍 （通常大約是眼睛層級） 及其主要焦點區域注意大多。 將大部分的目標放在一些合理的頻外，周圍視覺層級可以幫助。 指定使用者傾向專注於相對較小視覺效果區域 （願景 attentional 圓錐圖是大約 10 度），隨時分組的 UI 項目程度它們在概念上相關可以利用注意鏈結的行為項目到項目以使用者身分將其視線通過區域。 在設計 UI 時，請記住視野 HoloLens 和沈浸式耳機之間的潛在大變異。

![舉例而言，更輕鬆的視線 Galaxy 檔案總管中的目標群組的 UI 項目](images/gazetargeting-grouping-1000px.jpg)<br>
*舉例而言，更輕鬆的視線 Galaxy 檔案總管中的目標群組的 UI 項目*

## <a name="improving-targeting-behaviors"></a>改善目標的行為
如果使用者意圖為目標的項目可以決定 （或接近近似），它可以接受"near miss"會嘗試在互動，如同它們已正確目標很有幫助。 有少數幾個成功的方法，可以將其納入混合的實境體驗：

### <a name="head-gaze-stabilization-gravity-wells"></a>Head 視線穩定 (「 重力 wells")
這應該開啟大部分/所有的時間。 這項技術會移除使用者可能有自然的前端/頸部做法。 也因為尋找/談到的行為而移動。

### <a name="closest-link-algorithms"></a>最接近的連結演算法
這些最適合疏鬆的互動式內容區域中。 如果有較高的機率，您可以決定使用者已嘗試進行互動，您可以只假設某些層級的意圖來補充其目標的能力。

### <a name="backdatingpostdating-actions"></a>Backdating/postdating 動作
這項機制可用於需要速度的工作。 當使用者透過一系列的目標/啟用調動的速度移動時，它可用假設某些意圖，並允許遺失的步驟，可以根據使用者具有焦點稍微之前或之後 （50 毫秒前/後是有效的點選稍微目標及早測試）。

### <a name="smoothing"></a>平滑處理
這項機制可用於路徑移動，減少些許抖動/搖晃因為自然磁頭移動特性。 當透過 smooth 大小/距離的移動，而不是經過一段時間的路徑動作平滑處理

### <a name="magnetism"></a>磁場
這項機制可以視為 「 最接近連結 」 演算法-繪製為目標，向資料指標，或 （不論明顯與否），只需增加 hitboxes 的較通用版本使用者達到可能的目標，使用互動式的版面配置，以一些知識使用者意圖更好的方法。 這可以是特別強大，小型的目標。

### <a name="focus-stickiness"></a>焦點黏著度
當判斷哪些焦點提供給互動項目附近，會提供目前焦點的項目偏差。 這有助於減少不穩定的焦點時具有自然雜訊的兩個項目之間的中間點在浮動切換行為。


## <a name="composite-gestures"></a>複合的筆勢
應用程式，可以識別多個個別的點選。 結合點選，按住並釋放與左手邊移動，您可以執行更複雜的複合筆勢。 低層級空間輸入資料 （從空中點選和 Bloom） 開發人員可以存取建置這些複合或高階的筆勢。

### <a name="air-tap"></a>空中點選
空中點選手勢 （以及下列其他筆勢） 只回應特定的點選。 若要偵測其他點選動作，例如功能表或掌握，您的應用程式必須直接使用兩個主要元件筆勢上一節中所述的較低層級互動。

### <a name="tap-and-hold"></a>Tap and hold
保留只維護空中點選向下指位置。 空中點選並按住的組合可讓各種不同的更複雜 「 按一下並拖曳 」 互動結合例如挑出物件，而非在啟用 arm 移動時或 「 mousedown 」 次要互動，例如顯示操作功能表。
不過，為使用者設計這個筆勢很容易就能在任何擴充筆勢的過程中放寬他們手 postures 時，應注意。

### <a name="manipulation"></a>操作
操作筆勢可以用來移動、 調整大小或旋轉雷射，當您想要以回應使用者的手移動到的 1 對 1 全像中。 這類的 1 對 1 移動的用法之一是讓使用者繪製或繪製世界中。
操作筆勢的初始目標應該視線或指向所完成。 一旦在點選並按住物件的任何操作啟動，然後處理以手動方式移動，讓使用者看著，而這些操作。

### <a name="navigation"></a>巡覽
瀏覽筆勢的運作方式如同虛擬搖桿，而且可用來瀏覽 UI 的小工具，例如放射狀功能表。 您點選並按住啟動筆勢，然後移動 您的手在正規化 3D cube 中，以初始按下時。 設為 1，其中 0 表示的起始點，您可以從-1 值移動您的手沿著 X、 Y 或 Z 軸。
瀏覽可用來建置速度為基礎連續捲動或縮放筆勢，類似於按一下滑鼠中間按鈕，然後再移動滑鼠向上和向下捲動 2D 的 UI。

巡覽及 rails 指的是辨識特定座標軸內移動，直到該軸上達到特定臨界值。 這只時很有用，在多個軸中的移動已啟用應用程式中由開發人員，例如應用程式是設定為可辨識之間的瀏覽筆勢，X，Y 軸，但也指定如果 X 軸 rails 使用。 在此情況下系統將會在 X 軸的手移動，只要它們都保留在虛數 rails （輔助線） 在 X 軸，如果辨識手動移動，也會發生 Y 軸。

在 2D 應用程式，使用者可以捲動、 放大，或在應用程式內拖曳使用垂直巡覽筆勢。 這會插入虛擬的手指修飾，以模擬觸控筆勢相同類型的應用程式。 使用者可以選取其中一個這些動作進行應用程式，藉由選取按鈕，或說出 '< 捲 /token&gt 拖曳/縮放 > Tool' 上方的列上的工具之間切換。

[深入了解複合的筆勢](gestures.md#composite-gestures)

## <a name="gesture-recognizers"></a>筆勢辨識器

使用筆勢辨識的其中一個優點是，您可以設定只針對目前的目標全像圖可接受的筆勢筆勢辨識器。 平台即可只去除混淆為了區分這些特定的支援的筆勢。 如此一來，只支援空中點選全像圖可以接受任何按下及放開之間的時間長度，在全像圖時，支援同時點選並按住可以點選，按住不放以完成後升級保留時間臨界值。

## <a name="hand-recognition"></a>手狀辨識
HoloLens 辨識手勢，藉由追蹤或兩個都看得到裝置的實際操作的位置。 HoloLens 為 [就緒] 狀態 （背面朝您與食指的手） 或 （背面朝您食指下手掌形狀） 的已按下的狀態時，會看到實際操作。 當其他會帶來在手，HoloLens 將會忽略它們。
針對每一個指針的 HoloLens 偵測，您可以存取它的位置 （不含方向） 和其已按下的狀態。 因為手形接近筆勢框架邊緣時，也會提供方向向量，您可以讓他們了解如何移動其手拿回 HoloLens 可以看到顯示給使用者。

## <a name="gesture-frame"></a>筆勢框架
手形 HoloLens 上的手勢，必須是"筆勢範圍內"，範圍中之筆勢感應數位相機中所見適當 （非常大約鼻子機身，來回大任之間）。 使用者需要辨識動作的成功和自己的緩和 （筆勢框架必須透過 HoloLens、 其檢視內，並保留其手臂 uncomfortably 以便進行互動，則有許多使用者會一開始假設） 的這個區域進行定型。 當使用 HoloLens Clicker，雙手不需要筆勢框架內。

在連續的筆勢的情況下特別的是，會有些風險的使用者移動板中間的筆勢 （例如移動某個全像攝影版的物件） 時中的筆勢框架外部，並會遺失其預期的結果。

有三個您應該考慮的事項：

- 使用者教育筆勢畫面格的存在和大約界限 （這教授 HoloLens 安裝期間）。

- 當其筆勢是接近/重大筆勢框架界限，應用程式內，不想要的結果會導致遺失的筆勢的程度，請通知使用者。 研究顯示的這類通知系統中，索引鍵的品質和 HoloLens 殼層提供這種類型的通知 （視覺效果，集中的資料指標，指出哪一個界限中跨越正在進行的方向） 的良好範例。

- 中斷筆勢框架界限的結果應該降到最低。 一般情況下，這表示應該停止的界限上，動作的結果，但不是會反轉。 例如，如果使用者移動一些全像攝影版的物件之間的空間，移動時，應該停止筆勢框架遭到入侵，但不是會傳回給起始點。 使用者可能會遇到一些挫折然後，但可能更快速地了解界限，並不需要每次重新啟動其完整的預定的動作。


## <a name="see-also"></a>另請參閱
* [直接操作](direct-manipulation.md)
* [指向和行動](point-and-commit.md)
* [互動基本概念](interaction-fundamentals.md)
* [目光和停駐](gaze-targeting.md)
* [目光和語音](voice-design.md)





