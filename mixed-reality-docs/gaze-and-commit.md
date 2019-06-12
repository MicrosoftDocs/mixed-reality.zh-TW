---
title: 頭部注視並認可
description: 頭部注視並認可輸入模型的概觀
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 注視, 注視定向, 互動, 設計
ms.openlocfilehash: d9eae3c0cfceba7c2c31425941dfce865f3aa609
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66692309"
---
# <a name="head-gaze-and-commit"></a>頭部注視並認可
「頭部注視並認可」是一種輸入模型，其涉及以頭部向前指的方向 (頭部方向) 瞄準物件，然後以次要輸入 (例如空中點選手勢或語音命令 "Select") 產生作用。 我們將其視為間接操作的「遠距」輸入模型，這表示它最適合用於伸手可及範圍內的內容互動。

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
混合實境頭戴式裝置使用使用者頭部的位置和方向來判斷其頭部方向向量。 您可以將此視為直接從使用者的雙眼之間向前直指的雷射。 這是相當粗略的使用者觀看位置概算。 您的應用程式可以讓此射線與虛擬或實際物件相交並在該位置繪製游標，讓使用者知道他們目前所定向的目標。

除了頭部注視以外，有些混合實境頭戴式裝置 (例如 HoloLens 2) 包含可產生眼部注視向量的眼動追蹤系統。 這會對使用者觀看的位置提供精細的測量。 使用眼部注視可以建立注視並認可互動，但這伴隨著一組非常不同的設計限制，其將會分別涵蓋於[眼動追蹤文章](eye-tracking.md)中。

## <a name="commit"></a>認可
瞄準物件或 UI 元素之後，使用者可以使用次要輸入進行互動或「按一下」。 這也稱為模型的認可步驟。 支援的認可方法如下：

- 空中點選手勢
- 說出語音命令 "Select"，或其中一個目標式語音命令
- 按下 [HoloLens Clicker](hardware-accessories.md#hololens-clicker) 上的單一按鈕
- 按下 Xbox Gamepad 上的 'A' 按鈕
- 按下 Xbox Adaptive Controller 上的 'A' 按鈕

### <a name="head-gaze-and-air-tap-gesture"></a>頭部注視和空中點選手勢
空中點選是手部直立的點選手勢。 若要執行空中點選，舉起食指朝向就緒位置，然後搭配拇指捏合並提起食指放開。 在 HoloLens 1 上，空中點選是最常見的次要輸入。

![將手指放在就緒位置，然後點選或按一下移動](images/readyandpress.jpg)<br>

空中點選也適用於 HoloLens 2，它已從原始版本放寬。 現在支援幾乎所有類型的捏合動作，只要手部直立並保持靜止。 這可讓使用者更容易了解和執行手勢。  這項新的空中點選透過相同的 API 取代舊的空中點選，所以現有應用程式會在針對 HoloLens 2 重新編譯之後自動取得新行為。

### <a name="head-gaze-and-select-voice-command"></a>頭部注視和 "Select" 語音命令
語音命令是 Mixed Reality 上其中一種主要互動方法。 它提供非常強大的「免持式」機制來控制系統。 語音互動模型有不同的類型：

- 一般命令 "Select"，可允許執行 [按一下] 行動或作為次要輸入認可。
- 「關閉」或「放大」等物件命令，可允許執行並作為次要輸入認可至動作。
- 「立即開始」等不需要目標的全域命令。
- 具有 AI 自然語言功能的交談使用者介面或實體 (例如 Cortana)。
- 自訂命令

若要尋找更多詳細資料和可用命令完整清單以及其使用方式，請查看我們的[語音命令](voice-design.md)指引。


### <a name="head-gaze-and-hololens-clicker"></a>頭部注視和 HoloLens Clicker
HoloLens Clicker 是專為 HoloLens 建置的第一個周邊裝置且隨附於 HoloLens 1 Development Edition。 HoloLens Clicker 可讓使用者以最少手動動作按一下，並認可為次要輸入。 HoloLens Clicker 會使用藍牙低能源 (BTLE) 連線到 HoloLens 1 或 2。

![HoloLens Clicker](images/hololens-clicker-500px.jpg)<br>
*HoloLens Clicker*

您可以在[這裡](hardware-accessories.md#pairing-bluetooth-accessories)找到裝置配對的詳細資訊和指示。




### <a name="head-gaze-and-xbox-wireless-controller"></a>頭部注視和 Xbox 無線控制器
Xbox 無線控制器允許使用 A 按鈕來執行 [按一下] 行動作為次要輸入。 裝置會對應至一組預設動作，協助您導覽和控制系統。 如果您想要自訂控制器，請使用 Xbox Accesories 應用程式來設定 Xbox 無線控制器。

![Xbox 無線控制器](images/xboxcontroller.jpg)<br>
*Xbox 無線控制器*

[將 Xbox 控制器與您的電腦配對](hardware-accessories.md#pairing-bluetooth-accessories)


### <a name="head-gaze-and-xbox-adaptive-controller"></a>頭部注視和 Xbox Adaptive Controller
Xbox Adaptive Controller 是裝置的統一中樞，有助於更方便存取 Mixed Reality，其主要設計訴求是要透過有限的行動性來符合玩家的需求。

Xbox Adaptive Controller 允許使用 A 按鈕來執行 [按一下] 行動作為次要輸入。 裝置會對應至一組預設動作，協助您導覽和控制系統。 如果您想要自訂控制器，請使用 Xbox Accesories 應用程式來設定 Xbox Adaptive Controller。

![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)<br>
*Xbox Adaptive Controller*

連接外部裝置 (例如開關、按鈕、底座和搖桿)，建立您專屬的自訂控制站體驗。 按鈕、搖桿和觸發器輸入都是使用透過 3.5mm 插口與 USB 連接埠連線的輔助裝置控制。

![Xbox Adaptive Controller 連接埠](images/xbox-adaptive-controller-ports.jpg)<br>
*Xbox Adaptive Controller 連接埠*

[裝置配對指示](hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/en-US/xbox-one/accessories/controllers/xbox-adaptive-controller>在 Xbox 網站上可取得更多資訊</a>


## <a name="design-guidelines"></a>設計指導方針
> [!NOTE]
> [即將推出](index.md)注視設計專屬的詳細指引。

## <a name="head-gaze-targeting"></a>頭部注視定向
無論輸入形式為何，當使用者能夠瞄準他們想要進行互動的元素時，所有互動就已建立。 在 Windows Mixed Reality 中，這通常會使用使用者的注視進行。
若要讓使用者能夠順利體驗，系統導出的使用者意圖理解，以及使用者的實際意圖都必須儘可能相吻合。 系統儘可能正確解譯使用者的預定動作，所以滿意度提升且效能改善。


## <a name="target-sizing-and-feedback"></a>目標大小調整和回饋
雖已重複表示注視向量可用於細微定向，但通常最適合用於粗略定向 (取得較大的目標)。 在大部分情況下，1 到 1.5 度的最小目標大小應可達成成功的使用者動作，但是 3 度的目標通常可讓速度提升。 請注意，使用者定向的大小實際上是 2D 區域 (即使是 3D 元素)，無論哪個投影面向他們都應該是可作為目標的區域。 提供元素為「作用中」(使用者以其為目標) 的一些明顯線索非常有用 - 這可能包括視覺「暫留」效果、音訊醒目提示或點按，或游標與元素的清楚比對等處理。

![2 個計量表距離的最佳目標大小](images/gazetargeting-size-1000px.jpg)<br>
*2 個計量表距離的最佳目標大小*

![醒目提示注視目標物件的範例](images/gazetargeting-highlighting-640px.jpg)<br>
*醒目提示注視目標物件的範例*

## <a name="target-placement"></a>目標位置
使用者通常找不到其視野中位於很高或很低的 UI 元素，而將其大部分的注意力放在其主要焦點的四周 (通常大約在眼部水平高度)。 將大部分的目標放在眼部水平周圍的合理頻帶會有所幫助。 假設使用者傾向於隨時將焦點放在相對較小的視覺區域 (視覺的注意視錐大約是 10 度)，將概念上相關的 UI 元素聚集在一起，可以在使用者目光掃過區域時運用逐一項目的注意鏈結行為。 在設計 UI 時，請記住 HoloLens 與沉浸式頭戴裝置之間的視野可能有很大的變化。

![方便在 Galaxy Explorer 中進行注視定向的分組 UI 元素範例](images/gazetargeting-grouping-1000px.jpg)<br>
*方便在 Galaxy Explorer 中進行注視定向的分組 UI 元素範例*

## <a name="improving-targeting-behaviors"></a>改善定向行為
如果可以判定使用者瞄準某物的意圖 (或極為近似)，則接受互動時的「近似差錯」嘗試 (彷彿已正確瞄準) 很有幫助。 有少數幾個成功方法可以納入混合實境體驗：

### <a name="head-gaze-stabilization-gravity-wells"></a>頭部注視穩定 (「重力穴」)
在大部分/所有的時間，應該開啟此功能。 這項技術會消除使用者可能會有的頭部/頸部緊張情形。 以及由於觀看/說話行為而造成的移動。

### <a name="closest-link-algorithms"></a>最接近的連結演算法
這些最適合用於具有疏鬆互動式內容的區域。 如果您非常可能判定使用者嘗試進行互動的項目，則只要假定某些層級的意圖，即可補充其定向能力。

### <a name="backdatingpostdating-actions"></a>回溯記日/事後記日動作
這項機制對於要求速度的工作很實用。 當使用者快速掃過一系列的定向/啟用調動時，假定某個意圖並允許錯過的步驟在使用者於點選稍前或稍後聚焦的目標上起作用 (在早期測試中於前/後 50 毫秒生效)。

### <a name="smoothing"></a>平滑處理
這項機制可用於路徑移動，減少自然頭部移動特性所造成的些許抖動/搖晃。 平滑處理路徑移動時，請依照移動的大小/距離 (而非隨著時間) 進行平滑處理

### <a name="magnetism"></a>磁性
這項機制可以視為更普遍的「最接近連結」演算法版本 - 繪製指向目標的游標，或只要在使用者接近適當目標時增加命中框 (不論是否看得見)，使用互動式版面配置的一些知識更完善處理使用者意圖。 這對於小型目標特別有效果。

### <a name="focus-stickiness"></a>焦點黏著度
在判斷要聚焦在哪些附近互動式元素時，提供目前焦點所在元素的偏差。 這有助於在浮動於兩個具有自然雜訊的元素間中點時，減少不穩定的焦點切換行為。


## <a name="composite-gestures"></a>複合手勢
應用程式不只可以辨識個別的點選動作。 結合點選、按住和放開與手部移動，即可執行更複雜的複合手勢。 這些複合或高階手勢是以開發人員可以存取的低階空間輸入資料 (來自空中點選和綻開) 為建置基礎。

### <a name="air-tap"></a>空中點選
空中點選手勢 (以及下列其他手勢) 只會回應特定點選動作。 若要偵測其他點選動作 (例如功能表或抓握)，您的應用程式必須直接使用上面兩個主要元件手勢一節中所述的較低層級互動。

### <a name="tap-and-hold"></a>Tap and hold
按住只是維持空中點選的手指朝下位置。 空中點選和按住的組合若搭配手臂移動 (例如拿起物件)，即可進行各種更複雜的「點擊並拖曳」互動，而不需加以啟動或以「滑鼠點擊」次要互動 (例如顯示快顯功能表)。
不過，針對這個手勢進行設計時應格外小心，因為使用者很容易在任何延伸手勢的過程中放鬆其手勢。

### <a name="manipulation"></a>操作
當您希望全像投影可 1:1 回應使用者的手部移動時，操作手勢可用來移動、調整大小或旋轉全像投影。 這類 1:1 移動的用途之一是要讓使用者可以實際繪圖。
操作手勢的初始定向應經由注視或指向來完成。 一旦啟動點選並按住，任何物件操作都由手部移動接著處理，讓使用者在操作時有空四周環顧。

### <a name="navigation"></a>瀏覽
瀏覽手勢的運作方式如同虛擬搖桿，可用來瀏覽 UI 小工具，例如放射狀功能表。 您可點選並按住來啟動手勢，然後在標準化 3D Cube (在初次按壓時置中) 中移動您的手。 您可以將您的手沿著 X、 Y 或 Z 軸從值 -1 移到 1 (而 0 表示起點)。
瀏覽可用來建置以速度為基礎的連續捲動或縮放手勢，類似於藉由按一下滑鼠中間按鈕，然後上下移動滑鼠來捲動 2D UI。

利用滑軌瀏覽就是指在達到特定座標軸上特定閾值前，辨識該座標軸內移動的功能。 只有當開發人員在應用程式中啟用多個座標軸移動時，這項功能才有用，例如將應用程式設定為可辨識遍及 X、Y 軸的瀏覽手勢，但也包含採用滑軌的指定 X 軸。 在此情況下，如果手部移動也會發生於 Y 軸，只要這些移動留在 X 軸上的虛構滑軌 (輔助線) 內，系統就會辨識遍及 X 軸的手部移動。

在 2D 應用程式內，使用者可以使用垂直瀏覽手勢在應用程式內捲動、縮放或拖曳。 這會在應用程式中插入虛擬手指觸控，以模擬同類型的觸控手勢。 在應用程式上方工具列中的工具之間切換 (藉由選取按鈕或說出「<捲動/拖曳/縮放> 工具」)，使用者即可選取發生哪個動作。

[複合手勢的詳細資訊](gestures.md#composite-gestures)

## <a name="gesture-recognizers"></a>手勢辨識器

使用手勢辨識的其中一個優勢，就是您可以只針對目前定向的全像投影可接受的手勢，設定手勢辨識器。 此平台只會為了區分這些特定支援的手勢而進行必要的去除混淆。 如此一來，只支援空中點選的全像投影可以接受在按下與放開之間的任何時間長度，而同時支援點選和按住的全像投影可以在按住時間閾值後將點選提升為按住。

## <a name="hand-recognition"></a>手部辨識
HoloLens 可藉由追蹤裝置可見的任一手或雙手位置來辨識手勢。 當手部處於就緒狀態 (手背朝向您且食指朝上) 或按下狀態 (手背朝向您且食指朝下) 時，HoloLens 就會看見手部。 當手部為其他姿勢時，HoloLens 就會忽略手部。
對於 HoloLens 偵測到的每隻手，您可以存取其位置 (不含方向) 及其按下狀態。 當手部接近手勢框架邊緣時，您也會取得方向向量，而您可對使用者顯示該向量，讓他們知道如何移動其手部以回到 HoloLens 可看見手部的位置。

## <a name="gesture-frame"></a>手勢框架
對於 HoloLens 上的手勢，手部必須在「手勢框架」內，也就是手勢感應攝影機可適度看見的範圍 (約略是從鼻子到腰部的範圍，且介於雙肩之間) 中。 使用者必須同時針對動作成功與其本身的舒適度，接受這個辨識範圍的訓練 (許多使用者一開始都假定手勢框架必定在其 HoloLens 視野內，且為了進行互動而不自在地高舉其手臂)。 使用 HoloLens Clicker 時，您的手不需要在手勢框架內。

尤其在連續手勢的情況下，在手勢過程 (例如在移動某個全像攝影物件時) 中將手部移出手勢框架的使用者會有些風險，並且會失去其預期的結果。

您應該考量下列三個事項：

- 教育使用者有關手勢框架的存在性和大約界限 (這在 HoloLens 設定期間教導)。

- 當手勢接近/突破應用程式內的手勢框架界限時，通知使用者，因為遺失手勢會導致不想要的結果。 研究已顯示這類通知系統的主要品質，而 HoloLens 殼層提供這類型通知的良好範例 (視覺化，位於中央游標，指出發生越界的方向)。

- 您應該將突破手勢框架界限的後果最小化。 一般而言，這表示手勢的結果應止於界限，但不會反轉。 例如，如果使用者正在房間內移動某個全像攝影物件，則當手勢框架被突破時，就應該停止移動，但不會回到起點。 使用者可能遭遇一些挫敗，但可以更快了解界限，而不必每次重新開始其完整的預定動作。


## <a name="see-also"></a>請參閱
* [手部直接操作](direct-manipulation.md)
* [手部指向和行動](point-and-commit.md)
* [本能互動](interaction-fundamentals.md)
* [頭部目光和停駐](gaze-and-dwell.md)
* [語音命令](voice-design.md)





