---
title: 應用程式的品質準則
description: 本文件說明最上層的因素影響混合的實境應用程式的品質。
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: 應用程式品質準則，混合實境，混合實境應用程式
ms.openlocfilehash: 8e635585c0981d81bf71fb5577232af28f2a0fdd
ms.sourcegitcommit: 150d258a23130026c8792da383a3993657841fb4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024491"
---
# <a name="app-quality-criteria"></a>應用程式的品質準則

本文件說明最上層的因素影響混合的實境應用程式的品質。 針對每個因素提供下列資訊
* 概觀 ─ 品質係數和重要性的簡短描述。
* 裝置影響-哪一種視窗混合實境裝置會受到影響。
* 品質準則 – 如何評估品質係數。
* 如何測量 – 量值 （或體驗） 問題的方法。
* 建議 – 摘要的方法來提供較佳的使用者體驗。
* 資源-相關的開發人員和設計資源，適合用來建立更優質的應用程式體驗。

## <a name="frame-rate"></a>畫面播放速率

畫面播放速率是全像穩定性和使用者緩和的第一要件。 畫面播放速率低於建議的目標可能會導致出現抖動，造成負面影響的經驗 believability，而可能造成眼睛疲勞全像投影。 60 赫茲或您想要支援根據哪一個 Windows Mixed Reality 相容電腦的 90 Hz，將會針對您的體驗，在 Windows Mixed Reality 沈浸式耳機目標畫面播放速率。 HoloLens 目標畫面播放速率是 60 赫茲。

### <a name="device-impact"></a>裝置的影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質準則

|  最佳  |  符合 |  失敗 |
--- | --- | ---
| 應用程式一致的方式符合每個目標裝置的第二個 (FPS) 目標畫面格：HoloLens; 上的 60 fps在 超級電腦; 90 fps並在主要電腦上的 60 fps。 | 應用程式有間歇性的框架會卸除不妨礙的核心體驗;或 FPS 一致低於所需目標，但不會妨礙應用程式體驗。 | 應用程式發生平均每隔 10 秒或更少的畫面播放速率會下降。 |

### <a name="how-to-measure"></a>如何測量

* 透過提供即時的畫面格速率圖形所[Windows Device Portal](using-the-windows-device-portal.md#system-performance) [系統效能] 底下。
* 進行偵錯開發，將應用程式中的畫面播放速率診斷計時器。 請參閱範例計數器的資源。
* 藉由左右移動您執行應用程式時，可以在裝置發生畫面格速率會卸除。 如果全像圖顯示非預期的抖動移動，然後低畫面播放速率或穩定性平面是可能的原因。

### <a name="recommendations"></a>建議

* 開發工作的開頭加入畫面格速率計數器。
* 應該評估並適當地解析為效能錯誤會造成畫面播放速率下降的變更。

### <a name="resources"></a>資源

#### <a name="documentation"></a>文件

* [了解效能 for Mixed Reality](understanding-performance-for-mixed-reality.md)
* [全像穩定性和畫面播放速率](hologram-stability.md#frame-rate)
* [資產的效能預算](asset-creation-process.md)
* [對 Unity 的效能建議](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a>工具和教學課程

* [MRToolkit，FPS 計數器顯示](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [MRToolkit，著色器](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a>外部參考

* [Unity，最佳化行動應用程式](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a>全像穩定性

穩定全像投影會增加的可用性和 believability 應用程式，並建立更舒適的檢視經驗的使用者。 全像穩定性的品質是良好的應用程式開發，以及裝置的能力，以了解 （追蹤） 的結果，其環境。 穩定性的第一要件畫面播放速率時，其他因素可能會影響穩定性包括：

* 穩定平面的使用
* 空間的錨點的距離
* 追蹤

### <a name="device-impact"></a>裝置的影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質準則

|  最佳  |  符合 |  失敗 |
--- | --- | ---
|  以一致的方式，全像投影會出現穩定狀態。 | 次要內容表現出非預期的移動方式;或非預期的移動不會影響整體應用程式體驗。 | 在框架中的主要內容表現出非預期的移動。 |

### <a name="how-to-measure"></a>如何測量

頭戴裝置和檢視體驗時：

* 移動您並排，如果全像投影顯示非預期的移動然後低畫面播放速率，或不正確的對齊方式主要平面穩定性平面的是可能的原因。
* 移動全像投影和環境中，找出 jumpiness 泳道等的行為。 這種類型的動作可能被造成裝置不追蹤環境或距離的空間的錨點。
* 如果是大型或多個全像投影會在框架中，觀察在各種深度的全像行為，而您前端的位置從左右移動，如果 shakiness 出現這可能是因穩定平面。

### <a name="recomendations"></a>建議

* 開發工作的開頭加入的畫面播放速率計時器。
* 使用穩定平面。
* 一定會轉譯錨定全像投影中的其錨點 3 公尺。
* 請確定您的環境設定適當的追蹤。
* 設計您的體驗，以避免全像投影的範圍內的各個主要的深度層級。

### <a name="resources"></a>資源

#### <a name="documentation"></a>文件

* [全像穩定性和畫面播放速率](hologram-stability.md#frame-rate)
* [案例研究，使用穩定平面](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [了解效能 for Mixed Reality](understanding-performance-for-mixed-reality.md)
* [對 Unity 的效能建議](performance-recommendations-for-unity.md)
* [空間錨點](spatial-anchors.md)
* [處理追蹤錯誤](coordinate-systems.md#handling-tracking-errors)
* [靜態參考座標系](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a>工具和教學課程

* [MR 附屬套件，Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a>在實際的介面上的全像投影位置

Misalignments 的全像投影的實體物件 （如果要置於彼此） 是清楚的非等位的全像投影和真實世界。 位置的精確度應該是相對的案例需求比方說，一般的表面放置可用空間的對應，但更精確的位置將會需要某些使用標記和校正。

### <a name="device-impact"></a>裝置的影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質準則

|  最佳  |  符合 |  失敗 |
--- | --- | ---
| 全像投影對齊英吋為單位的範圍通常以公分為單位的介面。 如果需要更精確，應用程式應該提供有效率的方法中所需的應用程式規格的共同作業。 | NA | 全像投影重大介面平面或似乎 float 遠離介面會出現與實體的目標物件未對齊。 如果需要精確度，全像投影應該符合案例的鄰近性規格。 | 

### <a name="how-to-measure"></a>如何測量

* 空間對應的全像投影不應該出現大幅浮動的上方或下方的介面。
* 全像投影需要精確的位置應該有某種形式的標記，並在校正的精確度的案例需求的系統。

### <a name="recommendations"></a>建議

* 空間對應可用於將物件放在介面上，有效位數不需要時。
* 最佳的有效位數，如使用標記或海報來設定全像投影和 Xbox 控制器 （或一些手動的對齊方式機制） 的最終的校正。
* 請考慮分成邏輯的組件中的超大型全像投影大小以及對齊這些介面的每個組件。
* 未正確設定 interpupilary 的距離 (IPD) 也可以影響全像對齊。 一律先設定使用者的 IPD 的 HoloLens。

### <a name="resources"></a>資源

#### <a name="documentation"></a>文件

* [空間的對應位置](spatial-mapping.md#placement)
* [掃描處理程序的房間](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [空間的錨點的最佳作法](spatial-anchors.md#best-practices)
* [處理追蹤錯誤](coordinate-systems.md#handling-tracking-errors)
* [Unity 中的空間對應](spatial-mapping-in-unity.md)
* [Vuforia 開發概觀](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a>工具和教學課程

* [MR Spatial 230：空間對應](holograms-230.md)
* [MR 工具組，空間的對應程式庫](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [MR 附屬套件，海報校正範例](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [MR 附屬套件，Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a>外部參考

* [Lowes 案例研究，有效位數的對齊方式](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a>緩和的檢視區域

應用程式開發人員控制使用者的眼睛將內容和全像投影放在不同的深度交集的位置。 穿著 HoloLens 的使用者會永遠足以容納要保持清晰的影像 HoloLens 顯示因為固定的光學距離約 2.0 m 遠離使用者的 2.0 萬個。 不適當內容的深度可能會導致 visual discomfort 或疲勞。

### <a name="device-impact"></a>裝置的影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質準則

<table>
<tr>
<td> 最佳 </td><td><ul>
<li>將內容放在 2 分鐘。</li><li>全像投影不能放在 2 分鐘，而且無法避免的聚合和住宿之間的衝突，全像放置的最佳區域時 1.25 m 和 5 分鐘之間。</li><li>在每個案例中，設計工具應該在建構內容，以鼓勵使用者互動 1 + m 消失 （例如調整內容大小和位置參數的預設值）。</li><li>除非特別不需要的案例，裁剪平面應該與 fadeout 開始 1m 的實作。</li><li>在需要仔細觀察蒼穹全像所在的情況下，內容不應該超過 50 cm 接近。</li>
</ul></td>
</tr><tr>
<td> 符合</td><td> 內容是中的檢視和動作的指導方針，但不當使用或不使用裁剪平面。</td>
</tr><tr>
<td> 失敗 </td><td> 太靠近呈現內容 (通常&lt;1.25 m 或&lt;50 cm 的 「 定態全像投影需要仔細觀察。)</td>
</tr>
</table>

### <a name="how-to-measure"></a>如何測量

* 內容通常都是 2m 淘汰過，但無法進一步比 1.25 或進一步超過 5 分鐘。
* 少數的例外狀況，HoloLens 裁剪轉譯距離應該設定為.85CM fadeout 的起價 1m 的內容使用。 方法內容，並注意裁剪平面的效果。
* 不應該接近放下 50 cm 比靜態內容。

### <a name="recommendations"></a>建議

* 設計最佳的檢視之間距離的 2m 的內容。
* 設 85 cm 使用的內容開頭 1m fadeout 裁剪轉譯距離。
* 「 定態全像投影需要更接近檢視，應該不超過 30 cm 接近裁剪平面以及 fadeout 應該開始至少 10 個 cm 遠離裁剪平面。

### <a name="resources"></a>資源

* [轉譯距離](hologram-stability.md#hologram-render-distances)
* [Unity 中的焦點](focus-point-in-unity.md)
* [小數位數的實驗](scale.md#experimenting-with-scale)
* [文字，建議使用的字型大小](typography.md#recommended-font-size)

## <a name="depth-switching"></a>深度切換

檢視區域的緩和問題，不論要求之間切換時，經常或快速使用者接近，而且最主要的物件 （包括全像投影和實際內容） 可能會導致 oculomotor 疲勞症和一般 discomfort。

### <a name="device-impact"></a>裝置的影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質準則

|  最佳  |  符合 |  失敗 |
--- | --- | ---
|  有限或自然深度切換，並不會造成使用者出奇聚焦。 | 突然深度參數這是核心，而且設計到應用程式體驗或突然深度參數所造成未預期的實際內容。 | 一致的深度交換器或突然深度切換，就不需要或應用程式體驗的核心。 | 

### <a name="how-to-measure"></a>如何測量

* 如果應用程式需要使用者以一致的方式和/或突然變更深度焦點，則切換問題的深度。

### <a name="recommendations"></a>建議

* 保持一致的主要平面中的主要內容，以確保穩定平面符合主要的平面。 這將有助於解決 oculomotor 疲勞症和非預期的全像移動。

### <a name="resources"></a>資源

* [轉譯距離](hologram-stability.md#hologram-render-distances)
* [Unity 中的焦點](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a>使用的空間的音效

在 Windows Mixed Reality，音訊引擎會提供混合的實境體驗聽覺元件，藉由模擬 3D 音效使用方向、 距離和環境的模擬。 在 應用程式中使用空間的聲音各地使用者允許開發人員 convincingly 置於 3 維空間 （球形） 中的音效。 這些聽起來再看起來將如同就像是來自真正的實體物件或使用者的周圍環境中混合的實境全像投影。 空間的聲音是訓練活動，協助工具，在混合的實境應用程式的 UX 設計的強大工具。

### <a name="device-impact"></a>裝置的影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質準則

|  最佳  |  符合 |  失敗 |
--- | --- | ---
|  以邏輯方式 spatialized 音效，和 UX 適當地使用音效來協助物件探索和使用者意見反應。 音效的案例是自然並與物件相關的正規化。 | 空間的音訊會適當地用於 believability 缺少做為以協助使用者意見反應與探索性的方法。 | 如預期般運作，不 spatialized 音效和/或缺乏可協助使用者在 UX 中的音效 或不被視為或案例的設計使用空間的音訊。 | 

### <a name="how-to-measure"></a>如何測量

* 一般情況下，相關的音效應該發出從目標全像投影 (例如。，全像攝影版的 dog 樹皮聲音。)
* 音效提示應該用於整個 UX 協助使用者意見反應或感知的全像攝影版的框架外的動作。

### <a name="recommendations"></a>建議

* 物件探索和使用者介面協助使用空間的音訊。
* 實際的聲音優於合成或非自然音效運作。
* 應該 spatialized 大部分的音效。
* 避免不可見的 fixit 發出器。
* 避免空間的遮罩。
* 正規化聽起來。

### <a name="resources"></a>資源

#### <a name="documentation"></a>文件

* [空間音效](spatial-sound.md)
* [空間音效設計](spatial-sound-design.md)
* [Unity 中的空間音效](spatial-sound-in-unity.md)
* [案例研究，如 HoloTour 聲音的空間](case-study-spatial-sound-design-for-holotour.md)
* [案例研究，RoboRaid 中使用空間的音效](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a>工具和教學課程

* [MR Spatial 220：空間音效](holograms-220.md)
* [MRToolkit，空間音訊](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a>焦點放在全像攝影版的框架 (FOV) 界限

設計良好的使用者體驗，可以建立和維護擴充大約是使用者在虛擬環境的有用的內容。 緩和 FOV 界限的效果牽涉到仔細考量的設計內容的小數位數和內容，請使用空間的音訊、 指引系統和使用者的位置。 如果，使用者會覺得小於受損根據 FOV 界限時有舒適的應用程式體驗。

### <a name="device-impact"></a>裝置的影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質準則

|  最佳  |  符合 |  失敗 |
--- | --- | ---
|  使用者永遠不會遺失內容，而且知道如何檢視。 大型物件提供內容協助。 外框以外的物件提供可測知性和檢視的指引。 一般情況下，動態設計和小數位數全像投影適合舒適的檢視體驗。 | 使用者永遠不會遺失內容，但在少數的情況下，可能需要額外的頸部影片。 在少數的情況下擴展可能會中斷可能導致某些頸部動作，若要檢視全像投影的垂直或水平框架是全像投影。 | 使用者可能會遺失內容及/或一致的頸部動作，才能檢視全像投影。 沒有內容的指引將物件移容易會遺失任何可搜尋性指引，或高全像投影框架外部，全像攝影版的大型物件，需要一般的頸部運動，讓檢視。 | 

### <a name="how-to-measure"></a>如何測量

* 內容 （大） 的全像遺失或不了解由於未經裁剪界限上。
* 全像投影的位置很難找到因為缺乏注意主管或快速斷斷續續全像攝影版的畫面格的內容。
* 案例需要一般和重複向上和向下完整查看導致頸部疲勞雷射前端的動作。

### <a name="recommendations"></a>建議

* 開始體驗與小型物件符合 FOV，然後轉換至較大版本的視覺提示。
* 若要協助使用者尋找內容超出 FOV 使用空間的音訊，並注意董事會。
* 儘可能，避免，垂直裁剪 FOV 全像投影。
* 為使用者提供最佳的檢視位置的應用程式指引。

### <a name="resources"></a>資源

#### <a name="documentation"></a>文件

* [全像攝影框架](holographic-frame.md)
* [案例研究、 HoloStudio UI 和互動的設計做法](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [小數位數的物件和環境](scale.md)
* [資料指標的視覺提示](cursors.md#visual-cues)

#### <a name="external-references"></a>外部參考

* [關於 FOV 多 ado](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a>內容回應至使用者的位置

全像投影應該回應大致上的 「 真實 」 物件的相同方式的使用者位置。 是值得注意的設計考量的重點是一定不能假設使用者的位置的 UI 項目為靜態，並且配合使用者的動作。 設計正確配合使用者位置的應用程式建立更可信的體驗，並讓它更容易使用。

### <a name="device-impact"></a>裝置的影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質準則

<table>
<tr>
<td> 最佳 </td><td> 內容和 UI 調整至使用者的位置，讓使用者自然互動與預期的使用者移動的範圍內的內容。</td>
</tr><tr>
<td> 符合 </td><td> UI 調整到使用者的位置，但可能會妨礙要求使用者調整其位置的索引鍵內容的檢視。</td>
</tr><tr>
<td> 失敗 </td><td><ol>
<li>UI 項目遺失或鎖定期間移動而造成使用者出奇返回 （或尋找） 控制項。</li><li>主要內容的檢視限制的 UI 項目。</li><li>UI 移動不適合檢視趨勢電子報，尤其是與距離<a href="billboarding-and-tag-along.md">tag-along</a> UI 項目。</li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a>如何測量

* 所有度量均應完成的案例在合理範圍內。 當使用者移動而異時，請勿嘗試誘騙具有極高的使用者移動的應用程式。
* UI 項目，相關的控制項應該是可以使用無論使用者移動。 比方說，如果使用者是檢視，並與 zoom 的 3D 對應四處跑，縮放控制項應該不論位置為何，使用者可以輕易地使用。

### <a name="recommendations"></a>建議

* 使用者是數位相機，它們控制移動。 讓這些磁碟機。
* 考慮告示板文字，否則會世界鎖定或遮蔽如果使用者的施展空間系統四處移動。
* 您可以使用 tag-along 必須遵循使用者，同時仍然允許使用者查看最前面的內容。

### <a name="resources"></a>資源

#### <a name="documentation"></a>文件

* [互動設計](hologram.md)
* [色彩、 光線及材料](color,-light-and-materials.md)
* [佈告板和常駐標籤](billboarding-and-tag-along.md)
* [本能互動](interaction-fundamentals.md)
* [自我動作和使用者 locomotion](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a>工具和教學課程

* [MR Input 210：目光](holograms-210.md)

## <a name="input-interaction-clarity"></a>輸入的互動清晰度

輸入的互動清楚很重要的應用程式的可用性，以及包含輸入的一致性、 易學、 可搜尋性互動的方法。 使用者應該能夠使用不含 relearning 的全平台的常見的互動方式。 如果應用程式有自訂的輸入，它應該能夠清楚地溝通和證明。

### <a name="device-impact"></a>裝置的影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質準則

|  最佳  |  符合 |  失敗 |
--- | --- | ---
|  輸入的互動方法都必須配合提供的 Windows Mixed Reality[指引](interaction-fundamentals.md)。 任何自訂的輸入不應該重複使用標準輸入 （而不是使用標準互動），必須能夠清楚地溝通和證明給使用者。 | 類似於最好的方式，但自訂的輸入是多餘的標準輸入的方法。 使用者仍可達到的目標和透過應用程式體驗的進度。 | 了解輸入的方法或按鈕對應很難。 輸入大量自訂，不支援標準的輸入，而不需指示，或可能會造成疲勞症和緩和問題。 | 

### <a name="how-to-measure"></a>如何測量

* 應用程式中使用一致[標準輸入方法。](interaction-fundamentals.md)
* 如果應用程式而代理商輸入，是將它透過清楚地溝通：
* 首次執行經驗
* 簡介畫面
* 工具提示
* 手狀 coach
* 說明區段
* 旁白

### <a name="recommendations"></a>建議

* 使用盡可能的標準輸入的方法。
* 非標準的輸入方法提供示範、 教學課程和工具提示。
* 使用整個應用程式一致的互動模型。

### <a name="resources"></a>資源

#### <a name="documentation"></a>文件

* [本能互動](interaction-fundamentals.md)
* [可互動的物件](interactable-object.md)
* [頭部目光和停駐](gaze-and-dwell.md)
* [游標](cursors.md)
* [舒適度與視線](comfort.md#gaze-direction)
* [筆勢](gestures.md)
* [語音輸入](voice-input.md)
* [語音命令](voice-design.md)
* [運動控制器](motion-controllers.md)
* [Unity 的輸入移植指南](input-porting-guide-for-unity.md)
* [Unity 中的鍵盤輸入](keyboard-input-in-unity.md)
* [Unity 中的目光](gaze-in-unity.md)
* [Unity 中的筆勢和運動控制器](gestures-and-motion-controllers-in-unity.md)
* [Unity 中的語音輸入](voice-input-in-unity.md)
* [DirectX 中的鍵盤、滑鼠及控制器輸入](keyboard,-mouse,-and-controller-input-in-directx.md)
* [DirectX 中的頭部和眼睛目光](gaze-in-directx.md)
* [DirectX 中的手部和運動控制器](hands-and-motion-controllers-in-directx.md)
* [DirectX 中的語音輸入](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a>工具和教學課程

* [案例研究：為達成更多個人運算](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [Cast 研究：HoloStudio UI 和互動的設計做法](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [範例應用程式：定期的資料表的項目](periodic-table-of-the-elements.md)
* [範例應用程式：農曆模組](lunar-module.md)
* [MR Input 210：目光](holograms-210.md)
* [MR Input 211：筆勢](holograms-211.md)
* [MR Input 212：語音](holograms-212.md)

## <a name="interactable-objects"></a>可互動的物件

按鈕長久以來所用的觸發事件 2D 抽象全球隱喻。 在三維的混合的現實世界中，我們沒有不再侷限於這個抽象層再的世界。 任何項目可以是可互動的物件，都會觸發事件。 可互動的物件可以表示為任何項目從咖啡杯資料表在空中浮在球形文字說明。 表單中，不論可互動的物件應該清楚地識別使用者已透過視覺與音訊提示。

### <a name="device-impact"></a>裝置的影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質準則

|  最佳  |  符合 |  失敗 |
--- | --- | ---
|  表單中，不論可互動的物件都可透過視覺與音訊提示辨識三種狀態： 閒置，設為目標，並選取。 「 請查看它說它的項目 」 會清楚且一致地使用整個體驗。 物件會調整，並散發到允許免費為目標的錯誤。 | 使用者可以辨識為可透過音訊或視覺效果的意見反應，互動的物件和目標即可啟動物件。 | 沒有 visual 或音訊提示，使用者無法辨識的可互動的物件。 互動是因為物件小數位數或物件之間的距離而容易發生錯誤。 | 

### <a name="how-to-measure"></a>如何測量

* 可互動的物件會被視為 '互動';包括按鈕、 功能表和應用程式特定的內容。 根據經驗法則應該有視覺與音訊提示以互動的物件為目標時。

### <a name="recommendations"></a>建議

* 使用互動視覺與音訊的意見反應。
* 視覺化回饋應該加以區別，針對每個輸入狀態 （閒置、 目標、 選取）
* 可互動的物件應該調整，而且置於錯誤的可用目標。
* 群組可互動的物件 （例如功能表列或清單中） 應該針對適當的間距。
* 按鈕和功能表支援語音命令，應該為命令關鍵字提供文字的標籤 （"看到它，它說出"）

### <a name="resources"></a>資源

#### <a name="documentation"></a>文件

* [可互動的物件](interactable-object.md)
* [Unity 中的文字](text-in-unity.md)
* [週框方塊和應用程式列](app-bar-and-bounding-box.md)
* [語音命令](voice-design.md)

#### <a name="tools-and-tutorials"></a>工具和教學課程

* [混合的實境工具組-UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a>掃描的房間

需要空間的對應資料的應用程式依賴自動收集一段時間的這項資料的裝置，並以使用者的工作階段之間探索其環境與作用中裝置。 完整性和品質的這項資料取決於許多因素，包括使用者已完成探勘數量、 瀏覽過多少時間，以及是否物件，例如 furniture 和機門已因為裝置掃描區域。 許多應用程式會分析空間的對應資料的使用經驗判斷使用者是否應該執行其他步驟，以改善的完整性和品質空間對應的開頭。 如果使用者所掃描的環境，清除掃描體驗期間，應該提供指引。

### <a name="device-impact"></a>裝置的影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質準則

|  最佳  |  符合 |  失敗 |
--- | --- | ---
|  空間網狀結構的視覺效果會告訴使用者掃描正在進行中。 使用者清楚知道該如何和何時掃描啟動和停止。 | 提供空間網狀結構的視覺效果，但使用者可能不清楚知道要如何，會提供任何進度資訊。 | 網狀結構的任何視覺效果。 提供給使用者有關何處尋找或當掃描啟動/停止任何指引資訊。 |

### <a name="how-to-measure"></a>如何測量

* 在所需的空間掃描時，會指出哪裡可找到此項目，以及何時開始和停止掃描提供視覺與音訊的指引。

### <a name="recommendations"></a>建議

* 表示在使用者附近的總磁碟區中有多少必須能夠體驗的一部分。
* 當掃瞄啟動且例如進度列指示器會停止時，便會進行通訊。
* 使用在掃描期間之網狀結構的視覺效果。
* 提供視覺與音訊提示，可鼓勵使用者尋找並聊天室四處移動。
* 通知使用者前往改善資料的位置。 在許多情況下，可能是最理想的做法，告訴使用者他們需要執行 （例如查看最高限度，查看 furniture 後面），以取得必要的掃描品質。

### <a name="resources"></a>資源

#### <a name="documentation"></a>文件

* [空間位置掃描視覺效果](room-scan-visualization.md)
* [案例研究：展開 HoloLens 空間的對應的功能](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [案例研究：空間設計完善的 HoloTour](case-study-spatial-sound-design-for-holotour.md)
* [案例研究：在片段中建立沉浸式體驗](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a>工具和教學課程

* [混合的實境工具組-UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a>方向性指標

在混合的實境應用程式中，內容可能位於檢視欄位之外，或阻擋真實世界的物件。 設計良好的應用程式會方便使用者尋找不可見的內容。 方向性指標警示使用者重要的內容，並提供指引，以相對於使用者的位置內容。 不可見內容的指導方針可以達到這種音效的 fixit 發出器、 方向性箭號或直接的視覺提示。

### <a name="device-impact"></a>裝置的影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質準則

|  最佳  |  符合 |  失敗 |
--- | --- | ---
|  視覺與音訊提示直接引導使用者檢視欄位以外的相關內容。 | 箭號或某些指標，指向使用者內容的一般方向。 | 相關內容之外視野，並不佳，或沒有位置指引提供給使用者。 | 

### <a name="how-to-measure"></a>如何測量

* 外部使用者的檢視相關的內容是透過視覺化及 （或） 音訊提示可探索。

### <a name="recommendations"></a>建議

* 外部使用者的視野相關內容時，使用方向性指標和音訊提示來引導使用者的內容。 在許多情況下，直接的視覺輔助線是偏好透過方向性箭號。
* 方向性指標應該不會內建資料指標。

### <a name="resources"></a>資源

* [全像攝影框架](holographic-frame.md)

## <a name="data-loading"></a>載入資料

進度控制項為使用者提供回饋，告知正在進行長時間執行的操作。 它可以表示進度列指示器是可見的也可以指定等候時間可能長時，無法與應用程式互動使用者。

### <a name="device-impact"></a>裝置的影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式頭戴裝置</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質準則

|  最佳  |  符合 |  失敗 |
--- | --- | ---
|  在進度列或在任何資料載入或處理期間顯示進度環表單中的視覺指標以動畫顯示。 視覺指示器多少時間等候可能是提供指引。 | 載入資料進行中，但不會表示的時間等候可能是，會通知使用者。 | 沒有資料載入或處理程序耗時超過 5 秒的工作的指標。 |

### <a name="how-to-measure"></a>如何測量

* 在資料載入期間確認沒有空白狀態的時間超過 5 秒。

### <a name="recommendations"></a>建議

* 提供進度顯示在任何情況下，當使用者可能會感覺此應用程式已停止，或當機資料載入動畫。 合理的經驗法則是任何 '載入' 的活動，花費時間超過 5 秒。

### <a name="resources"></a>資源

* [顯示進度](progress.md)
