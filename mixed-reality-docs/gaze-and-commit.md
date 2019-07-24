---
title: 頭部注視並認可
description: 頭部注視並認可輸入模型的概觀
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Mixed Reality, 注視, 注視定向, 互動, 設計
ms.openlocfilehash: aeca5ceacf5ae350aa06cb58cc68162f885f6d78
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387676"
---
# <a name="head-gaze-and-commit"></a>頭部注視並認可
「前端注視」和「認可」是一種輸入模型, 其中牽涉到以您的頭向後 (head 方向) 方向為物件的目標, 然後使用次要輸入進行動作, 例如手勢碰點或語音命令選取。 它會被視為具有間接操作的輸入模型, 這表示它最適合用來與超越 arm 的內容互動。

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
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
    </tr>
     <tr>
        <td>頭部注視並認可</td>
        <td>✔️ 建議使用</td>
        <td>✔️ 建議使用 (第三個選擇 - <a href="interaction-fundamentals.md">查看其他選項</a>)</td>
        <td>➕ 替代選項</td>
    </tr>
</table>

## <a name="head-gaze"></a>頭部注視
混合實境頭戴式裝置使用使用者頭部的位置和方向來判斷其頭部方向向量。 您可以將此視為直接從使用者的雙眼之間向前直指的雷射。 這是相當粗略的使用者觀看位置概算。 您的應用程式可以將此光線與虛擬或真實世界的物件相交, 並在該位置繪製游標, 讓使用者知道它們目前的目標為何。

除了眼睛外, 某些混合現實耳機 (如 HoloLens 2) 包含可產生眼睛向量的監看式追蹤系統。 這會對使用者觀看的位置提供精細的測量。 您可以使用眼睛來建立注視和認可互動。 但是, 這是一組非常不同的設計條件約束, 會在[眼睛眼文章](eye-tracking.md)中另行討論。

## <a name="commit"></a>認可
以物件或 UI 元素為目標之後, 使用者可以使用次要輸入進行互動或按一下。 這也稱為模型的認可步驟。 支援的認可方法如下：

- 空中碰手勢
- 說出語音命令、選取或其中一個目標語音命令
- 在[HoloLens Clicker](hardware-accessories.md#hololens-clicker)上按一個按鈕
- 按下 Xbox 遊戲台上的 [A] 按鈕
- 按 Xbox 調適型控制器上的 [A] 按鈕

### <a name="head-gaze-and-air-tap-gesture"></a>頭部注視和空中點選手勢
空中點選是手部直立的點選手勢。 若要執行點一下, 請將您的索引指向準備好的位置, 然後將您的 thumb 縮小, 然後將索引手指的備份提升至發行。 在 HoloLens (第1代) 上, 空中碰是最常見的次要輸入。

![將手指放在就緒位置，然後點選或按一下移動](images/readyandpress.jpg)<br>

您也可以在 HoloLens 2 上使用空中按鍵功能。 它已從原始版本中放寬。 幾乎所有類型的 pinches 現在都可支援, 只要手是直立的, 而且仍然保留。 這可讓使用者更容易了解和執行手勢。 這個新的空中點會透過相同的 API 取代舊的, 因此現有的應用程式會在重新編譯 HoloLens 2 之後自動擁有新的行為。

### <a name="head-gaze-and-select-voice-command"></a>頭部注視和 "Select" 語音命令
語音命令是混合現實中的其中一種主要互動方法。 它提供了一種非常強大的無人參與機制來控制系統。 語音互動模型有不同的類型：

- 執行 click actuation 或 commit 做為次要輸入的一般命令選取。
- 像關閉或變得更大的物件命令會將動作執行並認可為次要輸入。
- 「移至開始」之類的全域 commnads 不需要目標。
- 對話使用者介面或 Cortana 等實體具有 AI 自然語言功能。
- 自訂命令

若要尋找更多詳細資料以及可用命令的 comprenhesive 清單, 以及如何使用它們, 請參閱我們的[語音命令](voice-design.md)指引。


### <a name="head-gaze-and-hololens-clicker"></a>頭部注視和 HoloLens Clicker
HoloLens Clicker 是專為 HoloLens 建立的第一個週邊裝置。 它隨附在 HoloLens (第1代) 開發版本中。 HoloLens Clicker 可讓使用者按一下最少的手運動, 並認可為次要輸入。 HoloLens Clicker 會使用藍牙低功耗 (BTLE) 連接到 HoloLens (第1代) 或 HoloLens 2。

![HoloLens Clicker](images/hololens-clicker-500px.jpg)<br>
*HoloLens Clicker*

您可以在[這裡](hardware-accessories.md#pairing-bluetooth-accessories)找到裝置配對的詳細資訊和指示。




### <a name="head-gaze-and-xbox-wireless-controller"></a>頭部注視和 Xbox 無線控制器
Xbox 無線控制器會使用 [A] 按鈕, 以次要輸入的形式執行按一下 actuation。 裝置會對應至一組預設動作，協助您導覽和控制系統。 如果您想要自訂控制器, 請使用 Xbox Accesories 應用程式來設定您的 Xbox 無線控制器。

![Xbox 無線控制器](images/xboxcontroller.jpg)<br>
*Xbox 無線控制器*

[將 Xbox 控制器與您的電腦配對](hardware-accessories.md#pairing-bluetooth-accessories)


### <a name="head-gaze-and-xbox-adaptive-controller"></a>頭部注視和 Xbox Adaptive Controller
Xbox 調調適型控制器是主要為了滿足行動裝置的需求, 而這是一種整合式集線器, 可協助讓混合現實更容易存取。

Xbox 調適型控制器會使用 [A] 按鈕, 以次要輸入的形式執行按一下 actuation。 裝置會對應至一組預設的動作, 以協助流覽和控制系統。 如果您想要自訂控制器, 請使用 Xbox Accesories 應用程式來設定 Xbox 調適型控制器。

![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)<br>
*Xbox Adaptive Controller*

連接外部裝置 (例如交換器、按鈕、掛接和搖桿), 以建立唯一的自訂控制器體驗。 按鈕、操縱杆和觸發程式輸入都是由透過 3.5 mm 插座和 USB 埠連線的輔助裝置所控制。

![Xbox Adaptive Controller 連接埠](images/xbox-adaptive-controller-ports.jpg)<br>
*Xbox Adaptive Controller 連接埠*

[裝置配對指示](hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/en-US/xbox-one/accessories/controllers/xbox-adaptive-controller>在 Xbox 網站上可取得更多資訊</a>


## <a name="design-guidelines"></a>設計指導方針
> [!NOTE]
> [即將推出](index.md)注視設計專屬的詳細指引。

## <a name="head-gaze-targeting"></a>頭部注視定向
無論輸入形式為何，當使用者能夠瞄準他們想要進行互動的元素時，所有互動就已建立。 在 Windows Mixed Reality 中，這通常會使用使用者的注視進行。
為了讓使用者能夠順利使用經驗, 系統對於使用者的意圖和使用者的實際意圖的瞭解, 必須盡可能地對齊。 系統儘可能正確解譯使用者的預定動作，所以滿意度提升且效能改善。


## <a name="target-sizing-and-feedback"></a>目標大小調整和回饋
注視向量已重複顯示, 可用於適當的目標, 但通常最適合用於總目標--取得較大的目標。 最小的目標大小為1到1.5 度, 在大多數情況下允許成功的使用者動作, 不過, 3 度的目標通常允許更快的速度。 請注意，使用者定向的大小實際上是 2D 區域 (即使是 3D 元素)，無論哪個投影面向他們都應該是可作為目標的區域。 提供某個元素為「作用中」的一些顯著提示 (使用者以其為目標) 非常有用。 這可能包括如可見的「暫留」效果、音訊反白顯示或點擊, 或清除游標與專案的對齊。

![距離 2 公尺的最佳目標大小](images/gazetargeting-size-1000px.jpg)<br>
*2 個計量表距離的最佳目標大小*

![醒目提示注視目標物件的範例](images/gazetargeting-highlighting-640px.jpg)<br>
*醒目提示注視目標物件的範例*

## <a name="target-placement"></a>目標位置
使用者通常無法在其視野中找到位置非常高或非常低的 UI 元素, 著重于其主要焦點附近的區域, 這大約是眼睛。 將大部分的目標放在眼部水平周圍的合理頻帶會有所幫助。 假設使用者傾向於隨時將焦點放在相對較小的視覺區域 (視覺的注意視錐大約是 10 度)，將概念上相關的 UI 元素聚集在一起，可以在使用者目光掃過區域時運用逐一項目的注意鏈結行為。 在設計 UI 時，請記住 HoloLens 與沉浸式頭戴裝置之間的視野可能有很大的變化。

![方便在 Galaxy Explorer 中進行注視定向的分組 UI 元素範例](images/gazetargeting-grouping-1000px.jpg)<br>
*方便在 Galaxy Explorer 中進行注視定向的分組 UI 元素範例*

## <a name="improving-targeting-behaviors"></a>改善定向行為
如果使用者意圖是以某個專案為目標 (或接近), 則在互動時接受接近遺漏的嘗試, 可能會很有説明, 如同其目標正確。 以下是幾個成功的方法, 可以併入混合現實體驗中:

### <a name="head-gaze-stabilization-gravity-wells"></a>頭部注視穩定 (「重力穴」)
這應該會在大部分或全時間開啟。 這項技術會移除使用者可能因外觀和說話行為而進行移動的自然頭和頸部起伏快速變換。

### <a name="closest-link-algorithms"></a>最接近的連結演算法
這些最適合用於具有疏鬆互動式內容的區域。 如果您可以判斷使用者嘗試與之互動的機率很高, 則可以假設某種程度的意圖來補充其目標功能。

### <a name="backdating-and-postdating-actions"></a>Backdating 和 postdating 動作
這項機制對於要求速度的工作很實用。 當使用者透過一系列的目標和啟用調動快速移動時, 假設有一些意圖, 並允許遺漏的步驟, 以使用者在點在點前後的焦點 (50 毫秒之前/之後) 來採取目標rly 測試)。

### <a name="smoothing"></a>平滑處理
這種機制對於路徑移動很有用, 因為自然的頭移動特性, 減少輕微的抖動和 wobble。 平滑處理路徑動作時, 會以移動的大小和距離來平滑, 而不是一段時間。

### <a name="magnetism"></a>磁性
這項機制可以視為較通用的最接近連結演算法版本--將游標向目標繪製, 或只是以明顯的方式增加 hitboxes (不論是否可見), 因為使用者可能會藉由使用某些互動式版面配置知識更好方法使用者意圖。 這對於小型目標特別有效果。

### <a name="focus-stickiness"></a>焦點黏著度
在決定要將焦點放在哪些鄰近的互動式元素時, [焦點] 會向目前焦點的元素提供偏差。 這有助於減少不穩定的焦點切換行為, 而在兩個專案之間的點浮動時, 會發生自然雜訊。


## <a name="composite-gestures"></a>複合手勢

### <a name="air-tap"></a>空中點選
[空中] 手勢 (以及下面的其他手勢) 只會對特定點碰做出回應。 您的應用程式必須直接使用上述兩個主要元件手勢一節中所述的較低層級互動, 以偵測其他功能表或抓住。

### <a name="tap-and-hold"></a>Tap and hold
按住只是維持空中點選的手指朝下位置。 結合 [按下] 和 [按住], 可讓您在結合 arm 動作 (例如, 挑選物件, 而不是啟動它或 mousedown 次要互動, 例如顯示操作功能表) 時, 使用各種較複雜的「按一下並拖曳」互動。
不過，針對這個手勢進行設計時應格外小心，因為使用者很容易在任何延伸手勢的過程中放鬆其手勢。

### <a name="manipulation"></a>操作
當您想要讓全像投影對使用者的移動進行1:1 回應時, 可以使用操作手勢來移動、調整大小或旋轉全息形狀。 這類 1:1 移動的用途之一是要讓使用者可以實際繪圖。
操作手勢的初始定向應經由注視或指向來完成。 當點一下和按住開始時, 物件的任何操作都是由手動移動處理, 讓使用者在操作時能夠四處尋找。

### <a name="navigation"></a>巡覽
瀏覽手勢的運作方式如同虛擬搖桿，可用來瀏覽 UI 小工具，例如放射狀功能表。 您可點選並按住來啟動手勢，然後在標準化 3D Cube (在初次按壓時置中) 中移動您的手。 您可以將您的手沿著 X、 Y 或 Z 軸從值 -1 移到 1 (而 0 表示起點)。
瀏覽可用來建置以速度為基礎的連續捲動或縮放手勢，類似於藉由按一下滑鼠中間按鈕，然後上下移動滑鼠來捲動 2D UI。

與 rails 的導覽指的是在特定軸中辨識移動的能力, 直到達到該軸上的特定臨界值為止。 這僅適用于開發人員在應用程式中啟用多個軸的移動時, 例如, 如果應用程式設定為在 X、Y 軸上辨識導覽手勢, 但也使用 rails 指定 X 軸。 在此情況下, 如果 Y 軸上也發生手移動, 系統將會辨識 X 軸上的手上移動, 前提是它們會保留在 X 軸上的虛數滑軌 (guide) 中。

在 2D 應用程式內，使用者可以使用垂直瀏覽手勢在應用程式內捲動、縮放或拖曳。 這會在應用程式中插入虛擬手指觸控，以模擬同類型的觸控手勢。 使用者可以藉由選取按鈕或說「< Scroll/拖曳/縮放 > 工具」, 在應用程式上方的工具之間切換, 藉以選取要執行的動作。

[複合手勢的詳細資訊](gestures.md#composite-gestures)

## <a name="gesture-recognizers"></a>手勢辨識器

使用手勢辨識的其中一個優點是, 您可以只針對目前目標的全息影像可以接受的手勢設定手勢辨識器。 平臺只會視需要去除混淆, 以區別那些特定支援的手勢。 如此一來, 只支援「點按」的全像投影可以接受按下和放開之間的任何時間長度, 而支援兩個點按和按住的全像投影則可以在按住時間臨界值之後, 將點擊次數提升至保留。

## <a name="hand-recognition"></a>手部辨識
HoloLens 可藉由追蹤裝置可見的任一手或雙手位置來辨識手勢。 當手部處於就緒狀態 (手背朝向您且食指朝上) 或按下狀態 (手背朝向您且食指朝下) 時，HoloLens 就會看見手部。 當手上有其他人時, HoloLens 會忽略 themz。
對於 HoloLens 偵測到的每一手勢, 您都可以存取其位置, 而不需要方向和其按下狀態。 當手部接近手勢框架邊緣時，您也會取得方向向量，而您可對使用者顯示該向量，讓他們知道如何移動其手部以回到 HoloLens 可看見手部的位置。

## <a name="gesture-frame"></a>手勢框架
對於 HoloLens 上的手勢, 手必須位於手勢框架內, 筆勢檢測攝影機可以適當地查看, 從鼻子到 waist, 以及在肩膀之間。 使用者必須在此辨識區域上訓練, 以進行動作的成功並讓自己的緩和。 許多使用者一開始會假設筆勢框架必須透過 HoloLens 在其觀看範圍內, 並將其 uncomfortably 以進行互動。 使用 HoloLens Clicker 時, 不需要將手放在筆勢框架中。

特別是在連續手勢的情況下, 使用者在移動全像投影物件時, 會有一些風險會將其手移至手勢框架外, 例如, 並失去其預期的結果。

您應該考量下列三個事項：

- 筆勢框架的存在和大致界限的使用者教育。 這會在 HoloLens 設定期間進行講授。

- 當使用者的手勢接近或中斷應用程式內的手勢框架邊界時, 會通知他們, 而失去的手勢會導致不想要的結果。 研究已顯示這類通知系統的重要品質。 HoloLens shell 會在中央游標上提供這種類型通知的良好範例--視覺效果, 指出發生邊界相交的方向。

- 您應該將突破手勢框架界限的後果最小化。 一般來說, 這表示手勢的結果應該在界限停止, 而不是反轉。 例如, 如果使用者在房間內移動一些全像攝影物件, 則在軌跡框架遭到入侵時, 移動應該會停止, 而不會傳回至起點。 使用者可能會遇到一些挫折, 但可能會更快速地瞭解界限, 而不必每次都重新開機其完整的預期動作。


## <a name="see-also"></a>另請參閱
* [手部直接操作](direct-manipulation.md)
* [手部指向和行動](point-and-commit.md)
* [本能互動](interaction-fundamentals.md)
* [頭部目光和停駐](gaze-and-dwell.md)
* [語音命令](voice-design.md)





