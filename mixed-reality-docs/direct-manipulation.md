---
title: 直接操作
description: 直接操作輸入模型的概觀
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
keywords: 混合實境、 視線、 視線目標，就會有互動，設計
ms.openlocfilehash: d855955d44c1cf074849992e5dd7b36b54675fdd
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2019
ms.locfileid: "64581328"
---
# <a name="direct-manipulation"></a>直接操作
直接操作是需要動到全像投影雙手直接輸入的模型。 直接操作的目標是物件的行為就如同真實世界中。 可以啟動按鈕，只要按下這些物件可以藉由抓取，撿起，2D 內容的行為類似虛擬觸控螢幕。  因為這個緣故，直接操作很容易讓使用者了解，並很好玩的太。  它會被視為 「 附近 」 輸入的模型，這表示它最適合用於互動手臂內到達的內容。

若要了解輕鬆直接操作的重要組成成分是，它是功能可見性為基礎。 沒有符號的筆勢，以教導使用者。 應該會可以接觸到或抓取的視覺元素架構的所有互動。

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
        <td>直接操作 （靠近手動互動）</td>
        <td>不支援的 ❌</td>
        <td>建議的 ✔️</td>
        <td>➕ 另一個選項，但<a href="point-and-commit.md">點和認可 （遠端互動）</a>建議</td>
    </tr>
</table>

直接操作是 HoloLens 2，利用新的相互連貫的手動追蹤系統上的主要輸入的模型。 輸入的模型也會提供在透過移動控制站，使用擬真耳機，但不是建議主要表示的物件操作之外的互動。  無法使用 HoloLens 第 1 版上直接 manipluation。

## <a name="collidable-fingertip"></a>Collidable 寫寫看
HoloLens 2 上使用者的實際手被辨識和解譯為左邊和右邊的架構模型。 若要實作觸碰全像投影直接與實際操作的概念，在理想情況下，5 colliders 可以連接到每一個手動架構模型的 5 個手。 不過，實際上，tactile 的意見反應的不足，10 collidable 握有一間功能造成許多非預期且無法預期的衝突與全像投影。 因此，我們建議僅將 collider 放入每個索引的手指。 2 手指按到 5 的手指按下點選 collidable 握有一間功能仍然可做為涉及其他手指，例如 1 手指 press，1 指的各種不同的觸控筆勢的作用中觸控點的索引。

![Collidable 寫寫看映像](images/Collidable-Fingertip-720px.jpg)<br>

### <a name="sphere-collider"></a>球紋 collider
而不是使用隨機的一般形狀，我們建議使用球體 collider，並以視覺化方式呈現它為幾近目標提供更好的提示。 球體的直徑應符合食指，以提高觸控的正確性的粗細。 它很容易就能藉由呼叫手形 API 擷取手指粗細的變數。

<br>

### <a name="fingertip-cursor"></a>用手指對資料指標
除了呈現 collidable 球體上索引寫寫看，我們會建立進階解決方案，用手指對資料指標，以達到更接近目標設定體驗以互動方式。 它是附加在索引寫寫看甜甜圈圖形資料指標。 根據鄰近性，以動態方式回應為目標的方向和大小，如下所示：
* 當食指移到全像圖時，資料指標一律會平行至全像圖介面，而逐漸隨之縮減其大小。 
* 手指觸控式介面，如資料指標會壓縮成一個點，並發出觸控事件。

<br> 使用互動式的意見反應，使用者可達到目標的工作，例如觸發的 web 內容的超連結或按下按鈕附近的有效位數很高。 <br>

![寫寫看游標影像](images/Fingertip-Cursor-720px.jpg)<br>

## <a name="bounding-box-with-proximity-shader"></a>週框方塊與鄰近著色器
全像圖本身也需要將視覺與音訊來補償缺少 tactile 的意見反應的意見反應。 為此，我們會產生的週框方塊與鄰近著色器的概念。 週框方塊是最小的體積型區域封入 3D 物件。 週框方塊有互動式轉譯機制稱為 「 鄰近著色器。 鄰近著色器的行為，如下所示：

* 食指時在範圍內，會用手指對精選轉型之介面的週框方塊。 
* 當寫寫看表面接近，焦點就會據以總是。 
* 只要用手指對觸控式介面，整個週框方塊變更色彩，或產生以反映觸控狀態的視覺效果。 
* 同時，就可以啟動的聲音效果來增強 visual 觸控意見反應。

![使用鄰近著色器映像的週框方塊](images/Bounding-Box-With-Proximity-Shader-720px.jpg)<br>

## <a name="pressable-button"></a>Pressable 按鈕
使用 collidable 用手指對使用者現在已準備好使用非常基本全像攝影版 UI 元件，pressable 按鈕互動。 Pressable 按鈕是針對直接手指按量身打造的全像攝影版按鈕。 同樣地，因為缺乏 tactile 的意見反應，pressable 按鈕提供一些機制，以處理 tactile 的意見反應相關問題。 
* 第一種機制週框方塊與鄰近著色器，前述的段落中已解決。 它可以提供更好的方法，並讓使用者的鄰近性概念連絡人與按鈕。 
* 第二個是 depression。 寫寫看連絡 按鈕之後，它會建立按下的意義。 機制是按鈕緊密移動與深度軸寫寫看。 按鈕可以盡速以達到指定的深度 （在按下） 或離開 （在發行版本） 的深度，通過之後觸發。 
* 音效，應該將增強的意見反應，觸發按鈕時。 

![Pressable 按鈕影像](images/Pressable-Button-720px.jpg)<br>

## <a name="2d-slate-interaction"></a>2D 平板電腦的互動
2D slate 是全像攝影版的容器，裝載 2D 應用程式的內容，例如網頁瀏覽器。 透過直接操作 2D 靜態圖像與互動的設計概念是運用使用實體的觸控式螢幕進行互動的心智模型。<br> <br>
進行互動的平板電腦的連絡人：<br> 
* 使用者會使用索引的手指來按下超連結或按鈕。 
* 使用者捲動平板電腦的內容使用食指的增加和減少。 
* 使用者會使用兩個索引的手指來放大 in 和 out 根據相對的移動，指的平板電腦的內容。 
![2D slate 映像](images/2D-Slate-Interaction-720px.jpg)<br>

<br>操作 2D slate 本身：<br>
* 使用者可以接近其邊角和邊緣，以顯示最接近的操作提供的指針。 
* 藉由抓取操作提供，使用者可以執行透過角 affordnaces 統一縮放，並自動重排透過邊緣提供。 
* 抓取頂端的 2D slate holobar 可以使用者移動整個 slate。<br><br>

![平板電腦操作的映像](images/Manipulate-2d-slate-720px.jpg)


## <a name="3d-object-manipulation"></a>3D 物件操作
在 HoloLens 2 中，使用者可以使用其實際操作來直接操作 3D hologramphic 物件套用至每個 3D 物件的週框方塊。 週框方塊會提供更好的深度認知，透過其鄰近著色器。 週框方塊中，有兩個 3D 物件操作的設計方法：      
### <a name="affordance-based-manipulation"></a>功能可見性基礎操作：
這是使用者管理透過週框方塊以及操作提供，其周圍的 3D 物件的方式。 只要使用者的手很接近 3D 物件，會顯示週框方塊 」 和 「 最接近的功能可見性。 使用者可以抓取移動整個物件，也就是 edge 提供，若要旋轉的週框方塊和 coner 提供一致的方式調整。<br>

![3D 物件操作的映像](images/3D-Object-Manipulation-720px.jpg)<br>

### <a name="non-affordance-based-manipulation"></a>非功能可見性基礎操作：
在此 mechanisom，沒有功能可見性會附加至週框方塊。 使用者可以只顯示週框方塊，然後直接與它互動。 週框方塊以一隻手拿起，轉譯和旋轉的物件關聯到影片以及左手邊的方向。 時物件會抓取具有兩個實際操作中，使用者可以轉譯、 縮放和旋轉根據相對的兩個實際操作的動作。<br><br> 

<br><br>
進行操作，您需要有效位數，我們建議您 afforance 基礎操作提供高層級的資料粒度。 對於具有彈性的操作，非功能可見性操作會很好的選擇，並提供使用者立即和 playful 體驗。


## <a name="instinctual-gestures"></a>Instinctual 筆勢
不同於 HoloLens （第 1 代），一些預先定義的教育使用者筆勢，例如 Bloom 和空中點選，HoloLens 2 中，我們不要求使用者記住任何符號的筆勢。 使用者需要全像投影和內容互動的所有筆勢都是 instinctual。 完成 instinctual 筆勢的方式是引導使用者來執行透過 UI 提供的設計的筆勢。 比方說，如果我們鼓勵使用者先抓取的物件或使用兩個手指縮小的控點時，該物件或控制項控點應該很小。 如果我們想要使用者能夠執行五個手指抓取，表示物件或控制項控點應該相當大。 類似於按鈕，小按鈕會限制使用者一根手指，以按龐大的按鈕會鼓勵使用者使用其手掌按它時。
![](images/Instinctual-Gestures-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a>指針與 6 DoF 控制器之間的對稱式設計
您可能已經注意到，現在有我們可繪製手中 VR AR 和移動控制站之間的互動 parallels。 這兩個輸入可用來直接操作各自的環境中觸發程序。 HoloLens 2 抓取，然後拖曳手在關閉距離適用於使用許多相同的方式，為擷取按鈕會在影片中的控制站 WMR。 這可讓使用者使用兩個平台之間的互動熟悉度，並會派上用場應該您決定要將應用程式從兩個不同的連接埠。

## <a name="optimizing-with-eye-tracking"></a>追蹤與最佳化
如果它運作正常，但可能也很快就會令人沮喪，如果您不能再移動手任何位置，而不會不小心觸發雷射，直接操作可以感覺神奇。
追蹤可能有助於更好用來識別使用者的目的什麼。 

* **當**:減少錯誤地觸發操作回應。 追蹤可讓您進一步了解哪些使用者目前可供使用。 例如，假設您正在閱讀透過全像攝影版 （指示） 的文字時達到超過擷取您的實際工作的工具。
如此一來，您不小心會跨您還沒有之前 （甚至是外部使用者的檢視欄位的可能） 即使發現一些互動式全像攝影版按鈕移動手。
長話短說：如果使用者尚未看過全像一段時間，但它偵測觸控或掌握事件，它可能是使用者不實際想要進行互動，全像。 

* **哪一個**:除了定址，則為 false 的正面啟用，另一個範例中會包含進一步識別哪一個擷取或逛為精確的交集點可能無法清除從您的觀點來看特別是當數個全像投影位於接近每個全像投影其他。 雖然 HoloLens 2 上的眼睛追蹤有特定限制如何準確地它可以判斷眼睛視線，這仍然是非常有幫助附近因為深度差異的互動與輸入的手動互動時。 這表示，它有時很難判斷您的手後面或前面雷射精確地抓取，例如操作小工具。

 * **如何**:使用哪些使用者正在查看快速擲回的筆勢的相關資訊。 抓取雷射，並大致上其投到桌子朝向您的目的端。 雖然這有時可能會正常運作，快速地執行手勢可能會導致高度不正確的目的地。
這是追蹤可以幫助要借助交回擲回向量，以您想要的位置。

## <a name="see-also"></a>另請參閱
* [視線與認可](gaze-and-commit.md)
* [點和認可](point-and-commit.md)
* [互動基本概念](interaction-fundamentals.md)

