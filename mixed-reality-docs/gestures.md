---
title: 手勢
description: 手勢允許使用者在混合實境中採取的動作。
author: rwinj
ms.author: cmeekhof
ms.date: 02/24/2019
ms.topic: article
keywords: 混合的實境，手勢互動、 設計
ms.openlocfilehash: afebefddfd620b4697b86616e8ecc930b271dca2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591131"
---
# <a name="gestures"></a>手勢

手勢允許混合實境中的使用者採取動作。 互動根據**視線**為目標並**筆勢**或**語音**已針對任何項目採取動作。 手勢不提供確切的位置中的空間，但置於 HoloLens 和立即與內容互動的簡易性可讓使用者取得運作而不進行任何其他附屬應用程式。

<br>

>[!VIDEO https://www.youtube.com/embed/kwn9Lh0E_vU]

## <a name="device-support"></a>裝置支援

<table>
<tr>
<th>功能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens （第 1 代）</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沈浸式耳機</a></th>
</tr><tr>
<td> 手勢</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
<tr>
<td> 相互連貫的指針</td><td></td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

> [!NOTE]
> HoloLens 2 的特定的詳細指引[即將推出](index.md#news-and-notes)。

## <a name="gaze-and-commit"></a>視線認可

若要採取的動作，請送筆勢使用[前端的視線](gaze.md)做為目標的機制。 組合**視線**並**空中點選**軌跡導致**視線認可**互動。 視線認可的替代方式是**點認可**，藉由已啟用[動作控制器](motion-controllers.md)。 HoloLens 執行的應用程式只需要支援視線認可，因為 HoloLens 不支援移動控制站。 HoloLens 和沈浸式耳機執行的應用程式應支援視線驅動和指向導向的互動，讓使用者選擇他們使用何種輸入裝置中。

## <a name="the-two-core-gestures-of-hololens"></a>這兩個核心的 HoloLens 的筆勢

HoloLens 目前可辨識兩個核心元件筆勢-**空中點選**並**Bloom**。 這些兩個核心互動都有空間開發人員可以存取的輸入資料的最低層級。 它們形成各種可能的使用者動作的基礎。

### <a name="air-tap"></a>空中點選

空中點選是與手持垂直，類似於按下滑鼠點選手勢，或選取。 這用於大部分的 HoloLens 體驗相當於 「 按一下 」 的 UI 元素之後對其具有[視線](gaze.md)。 它是通用的動作，您了解一次，，然後套用到您的所有應用程式。 若要執行選取的其他方式所按下的單一按鈕[HoloLens Clicker](hardware-accessories.md#hololens-clicker)或透過說話語音命令"Select"。

![就緒狀態，以便在 HoloLens 上的手勢](images/image9.png)<br>
*空中點選 HoloLens 上的狀態。*

空中點選是離散的動作。 選取範圍已完成或不是，動作是或不在體驗中取出。 可能是，雖然不建議使用而不需要某些特定的目的，若要從主要的元件 （例如點選手勢，以表示點一下以外） 的組合建立其他不連續的筆勢。

![在準備好位置，然後點選或按一下 移動手指](images/readyandpress.jpg)<br>
*如何執行空中點選：引發食指就緒的位置、 按下點選或選取您的手指和釋放然後備份。*

### <a name="bloom"></a>Bloom

Bloom 是 「 主要 」 手勢，並保留供，單獨。 它是用來返回至 [開始] 功能表的特殊系統動作。 它就相當於按下鍵盤或 Xbox 控制器上的 Xbox 按鈕上的 Windows 鍵。 使用者可以使用任一游標。

![HoloLens 上 bloom 筆勢](images/image10-640px.png)

若要執行 HoloLens 上的 bloom 筆勢，您的手鑑效，掌，使用隨手可得在一起。 然後開啟您的手。 請注意，您可以也一律回到開始說 「 嘿 Cortana，移至首頁 」。 應用程式無法回應特別首頁的動作，因為這些會由系統處理。

![Bloom 筆勢](images/bloom-giphy.gif)<br>
*如何執行 bloom 筆勢 HoloLens 上。*

## <a name="composite-gestures"></a>複合的筆勢

應用程式，可以識別多個個別的點選。 結合點選，按住並釋放與左手邊移動，您可以執行更複雜的複合筆勢。 低層級空間輸入資料 （從空中點選和 Bloom） 開發人員可以存取建置這些複合或高階的筆勢。

<table>
<tr>
<th> 複合的筆勢</th><th> 如何套用</th>
</tr><tr>
<td>空中點選</td><td>空中點選手勢 （以及下列其他筆勢） 只回應特定的點選。 若要偵測其他點選動作，例如功能表或掌握，您的應用程式必須直接使用兩個主要元件筆勢上一節中所述的較低層級互動。</td>
</tr><tr>
<td>Tap and hold</td><td><p>保留只維護空中點選向下指位置。 空中點選並按住的組合讓各種不同的更複雜&quot;按一下並拖曳&quot;互動結合 arm 挑出的物件，而非啟用它，例如移動或&quot;mousedown&quot;次要的互動，例如顯示操作功能表。</p><p>不過，為使用者設計這個筆勢很容易就能在任何擴充筆勢的過程中放寬他們手 postures 時，應注意。</p></td>
</tr><tr>
<td>操作</td><td><p>操作筆勢可以用來移動、 調整大小或旋轉雷射，當您想回應給使用者的 1:1 全像&#39;s 手動移動。 這類的 1 對 1 移動的用法之一是讓使用者繪製或繪製世界中。</p><p>操作筆勢的初始目標應該視線或指向所完成。 一旦在點選並按住物件的任何操作啟動，然後處理以手動方式移動，讓使用者看著，而這些操作。</p></td>
</tr><tr>
<td>巡覽</td><td><p>瀏覽筆勢的運作方式如同虛擬搖桿，而且可用來瀏覽 UI 的小工具，例如放射狀功能表。 您點選並按住啟動筆勢，然後移動 您的手在正規化 3D cube 中，以初始按下時。 設為 1，其中 0 表示的起始點，您可以從-1 值移動您的手沿著 X、 Y 或 Z 軸。</p><p>瀏覽可用來建置速度為基礎連續捲動或縮放筆勢，類似於按一下滑鼠中間按鈕，然後再移動滑鼠向上和向下捲動 2D 的 UI。</p><p>巡覽及 rails 指的是辨識特定座標軸內移動，直到該軸上達到特定臨界值。 這只時很有用，在多個軸中的移動已啟用應用程式中由開發人員，例如應用程式是設定為可辨識之間的瀏覽筆勢，X，Y 軸，但也指定如果 X 軸 rails 使用。 在此情況下系統將會在 X 軸的手移動，只要它們都保留在虛數 rails （輔助線） 在 X 軸，如果辨識手動移動，也會發生 Y 軸。</p><p>在 2D 應用程式，使用者可以捲動、 放大，或在應用程式內拖曳使用垂直巡覽筆勢。 這會插入虛擬的手指修飾，以模擬觸控筆勢相同類型的應用程式。 使用者可以選取其中一個這些動作上方應用程式，藉由選取按鈕，或說出的列上的工具之間切換會發生&#39;&lt;捲 /token&gt 拖曳/縮放&gt;工具&#39;。</p></td>
</tr>
</table>



### <a name="gesture-recognizers"></a>筆勢辨識器

使用筆勢辨識的其中一個優點是，您可以設定只針對目前的目標全像圖可接受的筆勢筆勢辨識器。 平台即可只去除混淆為了區分這些特定的支援的筆勢。 如此一來，只支援空中點選全像圖可以接受任何按下及放開之間的時間長度，在全像圖時，支援同時點選並按住可以點選，按住不放以完成後升級保留時間臨界值。

## <a name="hand-recognition"></a>手狀辨識

HoloLens 辨識手勢，藉由追蹤或兩個都看得到裝置的實際操作的位置。 HoloLens 會看到實際操作的其中一個**就緒狀態**（背面朝您與食指的手） 或**按下狀態**（背面手形朝您食指下）。 當其他會帶來在手，HoloLens 將會忽略它們。

針對每一個指針的 HoloLens 偵測，您可以存取它的位置 （不含方向） 和其已按下的狀態。 因為手形接近筆勢框架邊緣時，也會提供方向向量，您可以讓他們了解如何移動其手拿回 HoloLens 可以看到顯示給使用者。

## <a name="gesture-frame"></a>筆勢框架

手形 HoloLens 上的手勢，必須是"筆勢範圍內"，範圍中之筆勢感應數位相機中所見適當 （非常大約鼻子機身，來回大任之間）。 使用者需要辨識動作的成功和自己的緩和 （筆勢框架必須透過 HoloLens、 其檢視內，並保留其手臂 uncomfortably 以便進行互動，則有許多使用者會一開始假設） 的這個區域進行定型。 當使用 HoloLens Clicker，雙手不需要筆勢框架內。

在連續的筆勢的情況下特別的是，會有些風險的使用者移動板中間的筆勢 （例如移動某個全像攝影版的物件） 時中的筆勢框架外部，並會遺失其預期的結果。

有三個您應該考慮的事項：
* 使用者教育筆勢畫面格的存在和大約界限 （這教授 HoloLens 安裝期間）。
* 當其筆勢是接近/重大筆勢框架界限，應用程式內，不想要的結果會導致遺失的筆勢的程度，請通知使用者。 研究顯示的這類通知系統中，索引鍵的品質和 HoloLens 殼層提供這種類型的通知 （視覺效果，集中的資料指標，指出哪一個界限中跨越正在進行的方向） 的良好範例。
* 中斷筆勢框架界限的結果應該降到最低。 一般情況下，這表示應該停止的界限上，動作的結果，但不是會反轉。 例如，如果使用者移動一些全像攝影版的物件之間的空間，移動時，應該停止的筆勢框架遭到入侵，但**不**傳回給起始點。 使用者可能會遇到一些挫折然後，但可能更快速地了解界限，並不需要每次重新啟動其完整的預定的動作。

## <a name="see-also"></a>另請參閱
* [為目標的視線](gaze-targeting.md)
* [語音設計](voice-design.md)
* [MR 輸入 211:筆勢](holograms-211.md)
* [筆勢和 Unity 中的動作控制站](gestures-and-motion-controllers-in-unity.md)
* [視線、 手勢和在 DirectX 中的動作控制站](gaze,-gestures,-and-motion-controllers-in-directx.md)
* [動作控制站](motion-controllers.md)
