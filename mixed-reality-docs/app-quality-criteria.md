---
title: 應用程式品質準則
description: 本檔說明影響混合現實應用程式品質的最大因素。
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: 應用程式品質準則，混合現實，混合現實應用程式
ms.openlocfilehash: f98111ebe9aacc30778e86501be41e6ac5f6d165
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437045"
---
# <a name="app-quality-criteria"></a>應用程式品質準則

本檔說明影響混合現實應用程式品質的最大因素。 針對每個因素，會提供下列資訊
* 總覽–「品質因素」和「重要性」的簡短描述。
* 裝置影響-受影響的 Windows 混合現實裝置類型。
* 品質準則–如何評估品質因素。
* 如何測量–測量（或體驗）問題的方法。
* 建議事項–提供更佳使用者體驗的方法摘要。
* 資源-相關的開發人員和設計資源，有助於建立更佳的應用程式體驗。

## <a name="frame-rate"></a>畫面播放速率

畫面播放速率是全息和使用者緩和的第一要件。 低於建議目標的畫面播放速率可能會使全息影像顯得抖動、對體驗的 believability 造成負面影響，並可能造成眼睛疲勞。 您在 Windows Mixed Reality 沉浸式耳機上體驗的目標畫面播放速率會是60Hz 或90Hz，視您想要支援的 Windows Mixed Reality 相容電腦而定。 若是 HoloLens，目標畫面播放速率為60Hz。

### <a name="device-impact"></a>裝置影響

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

|  效果  |  遇到 |  無法 |
--- | --- | ---
| 應用程式一致符合目標裝置的每秒畫面格數（FPS）目標： HoloLens 上的 60fps;Ultra 電腦上的 90fps;和60fps 在主流電腦上。 | 應用程式的斷斷續續畫面不會阻礙核心體驗;或 FPS 一致地低於所需的目標，但不會妨礙應用程式體驗。 | 應用程式平均每十秒或更短的畫面播放速率下降。 |

### <a name="how-to-measure"></a>如何測量

* [Windows 裝置入口網站](using-the-windows-device-portal.md#system-performance)會在 [系統效能] 下提供即時畫面播放速率圖表。
* 若是開發的偵錯工具，請在應用程式中新增 [畫面播放速率] 診斷計數器。 請參閱範例計數器的資源。
* 當應用程式正在執行時，畫面播放速率下降可能會在裝置上經歷，方法是將您的 head 從側邊移至一邊。 如果全像投影顯示非預期的抖動移動，則低畫面播放速率或穩定性平面可能是原因。

### <a name="recommendations"></a>建議事項

* 在開發工作開始時新增畫面播放速率計數器。
* 會評估產生下降畫面播放速率的變更，並適當地解決為效能錯誤。

### <a name="resources"></a>資源

#### <a name="documentation"></a>文件

* [瞭解混合現實的效能](understanding-performance-for-mixed-reality.md)
* [全息的穩定性和畫面播放速率](hologram-stability.md#frame-rate)
* [資產效能預算](asset-creation-process.md)
* [對 Unity 的效能建議](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a>工具和教學課程

* [MRToolkit，FPS 計數器顯示](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [MRToolkit、著色器](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a>外部參考

* [Unity，將行動應用程式優化](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a>全息影像穩定性

穩定的全息影像會提高應用程式的可用性和 believability，並為使用者建立更舒適的觀看體驗。 全像投影穩定性的品質是良好應用程式開發的結果，以及裝置瞭解（追蹤）其環境的能力。 雖然畫面播放速率是穩定性的第一個要件，但其他因素可能會影響穩定性，包括：

* 使用穩定平面
* 距離空間錨點
* 修訂

### <a name="device-impact"></a>裝置影響

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

|  效果  |  遇到 |  無法 |
--- | --- | ---
|  全息影像一致地顯示穩定。 | 次要內容表現出非預期的移動;或非預期的移動不會妨礙整體應用程式體驗。 | 框架中的主要內容展現了非預期的移動。 |

### <a name="how-to-measure"></a>如何測量

在戴上裝置並觀看體驗時：

* 將您的 head 從側邊移到一邊，如果全息影像顯示非預期的移動，則不正確的畫面播放速率，或穩定性平面與焦點平面的不適當對齊可能是原因。
* 四處移動全息影像和環境，尋找像是 [泳道] 和 [jumpiness] 的行為。 這種動作可能是因為裝置未追蹤環境，或與空間錨點的距離所造成。
* 如果框架中有大型或多個全息影像，請觀察各種深度的全息影像行為，同時將您的頭部位置從側邊移至一邊，如果 shakiness 出現，這可能是穩定平面所造成。

### <a name="recomendations"></a>建議

* 在開發工作開始時新增 [畫面播放速率] 計數器。
* 使用穩定平面。
* 一律在其錨點的3個計量中轉譯錨定的全息影像。
* 請確定您的環境已設定適當的追蹤。
* 設計您的體驗，以避免框架內各種焦點深度層級的全息影像。

### <a name="resources"></a>資源

#### <a name="documentation"></a>文件

* [全息的穩定性和畫面播放速率](hologram-stability.md#frame-rate)
* [使用穩定平面的案例研究](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [瞭解混合現實的效能](understanding-performance-for-mixed-reality.md)
* [對 Unity 的效能建議](performance-recommendations-for-unity.md)
* [空間錨點](spatial-anchors.md)
* [處理追蹤錯誤](coordinate-systems.md#handling-tracking-errors)
* [固定的參考框架](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a>工具和教學課程

* [MR 配套套件，Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a>實際表面上的全息影像位置

具有實體物件的全息影像不一致（如果要放在彼此之間的關聯性），可以清楚指出全息和真實世界的非聯合。 放置的精確度應該相對於案例的需求;例如，一般介面位置可以使用空間對應，但更精確的放置需要使用標記和校正。

### <a name="device-impact"></a>裝置影響

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

|  效果  |  遇到 |  無法 |
--- | --- | ---
| 全像投影對齊表面，通常是以釐米到英寸的範圍。 如果需要更多的精確度，應用程式應該為所需的應用程式規格中的共同作業提供有效率的方式。 | NA | 全息影像會與實體目標物件顯示不對齊，方法是中斷表面平面，或顯示為遠離表面。 如果需要精確度，則全息影像應符合案例的近接規格。 | 

### <a name="how-to-measure"></a>如何測量

* 放在空間地圖上的全息影像應該不會明顯地浮動在表面上方或下方。
* 需要精確放置的全息影像應具有某種形式的標記和校正系統，以精確因應案例的需求。

### <a name="recommendations"></a>建議事項

* 當不需要有效位數時，空間對應適用于將物件放在介面上。
* 為了達到最佳精確度，請使用標記或海報來設定全息和 Xbox 控制器（或某種手動對齊機制），以進行最後的校正。
* 請考慮將多大的全息影像分解成邏輯部分，並將每個部分對齊介面。
* 不當設定的 interpupilary 距離（IPD）也會影響全息影像對齊。 請一律將 HoloLens 設定為使用者的 IPD。

### <a name="resources"></a>資源

#### <a name="documentation"></a>文件

* [空間對應位置](spatial-mapping.md#placement)
* [房間掃描程式](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [空間錨點最佳做法](spatial-anchors.md#best-practices)
* [處理追蹤錯誤](coordinate-systems.md#handling-tracking-errors)
* [Unity 中的空間對應](spatial-mapping-in-unity.md)
* [Vuforia 開發總覽](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a>工具和教學課程

* [MR 空間230：空間對應](holograms-230.md)
* [MR 工具組，空間對應程式庫](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [MR 配套套件，海報校正範例](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [MR 配套套件，Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a>外部參考

* [Lowes 案例研究，精確度對齊](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a>觀賞舒適的區域

應用程式開發人員可以在各種深度放置內容和全息影像，以控制使用者的眼睛。 戴 HoloLens 的使用者一律會容納到 2.0 m，以維護清楚的影像，因為 HoloLens 顯示器的固定距離使用者遠接近 2.0 m。 不當的內容深度可能會導致視覺 discomfort 或疲勞。

### <a name="device-impact"></a>裝置影響

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
<td> 效果 </td><td><ul>
<li>將內容放在2m。</li><li>當您無法避免在2m 時放置全息影像，而且無法避免聚合與住宿之間的衝突時，全像投影位置的最佳區域會介於 1.25 m 到5m 之間。</li><li>在每個案例中，設計人員都應該結構內容，以鼓勵使用者離開 1 + m （例如調整內容大小和預設位置參數）。</li><li>除非案例特別不需要，否則裁剪平面應該使用從1百萬開始的 fadeout 來執行。</li><li>如果需要更深入觀察 motionless 的全像投影，則內容不應該比50cm 更接近。</li>
</ul></td>
</tr><tr>
<td> 遇到</td><td> 內容位於觀看和動作指引內，但不適當地使用或不使用裁剪平面。</td>
</tr><tr>
<td> 無法 </td><td> 內容的顯示太接近（通常是 &lt;1.25 m，或 &lt;50cm，針對需要更深入觀察的靜止全息影像）。</td>
</tr>
</table>

### <a name="how-to-measure"></a>如何測量

* 內容通常應該2m 在外，但不能接近1.25 或高於5m。
* 除了少數例外狀況之外，HoloLens 裁剪轉譯距離應該設定為. 85CM，fadeout 的內容是從1m 開始。 處理內容，並記下裁剪平面效果。
* 固定的內容應該不會接近50cm 的距離。

### <a name="recommendations"></a>建議事項

* 設計內容以取得2m 的最佳觀賞距離。
* 使用從1m 開始的 fadeout 內容，將裁剪轉譯距離設定為85cm。
* 對於需要進一步觀賞的靜止全息影像，裁剪平面應該不會接近30cm，而 fadeout 應從裁剪平面開始至少10cm。

### <a name="resources"></a>資源

* [呈現距離](hologram-stability.md#hologram-render-distances)
* [Unity 中的焦點](focus-point-in-unity.md)
* [使用 scale 進行實驗](scale.md#experimenting-with-scale)
* [文字、建議的字型大小](typography.md#recommended-font-size)

## <a name="depth-switching"></a>深度切換

無論觀賞的緩和問題區域為何，使用者需要經常或快速地在接近和遠的焦點物件之間切換（包括全息影像和真實世界內容），可能會導致 oculomotor 疲勞和一般 discomfort。

### <a name="device-impact"></a>裝置影響

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

|  效果  |  遇到 |  無法 |
--- | --- | ---
|  限制或自然深度切換，這不會造成使用者 unnaturally 將。 | 自然深度切換：這是核心並設計成應用程式體驗，或是因非預期的真實世界內容而造成的「突然深度」切換。 | 一致的深度切換，或不是必要或不是應用程式體驗核心的深入深度切換。 | 

### <a name="how-to-measure"></a>如何測量

* 如果應用程式需要使用者一致且/或突然變更深度焦點，則會有深度切換問題。

### <a name="recommendations"></a>建議事項

* 將主要內容保持在一致的焦點平面上，並確保穩定平面符合焦點平面。 這可減輕 oculomotor 的疲勞和非預期的全息影像移動。

### <a name="resources"></a>資源

* [呈現距離](hologram-stability.md#hologram-render-distances)
* [Unity 中的焦點](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a>使用空間音效

在 Windows Mixed Reality 中，音訊引擎提供混合現實體驗的以聽覺方式元件，方法是使用方向、距離和環境模擬來模擬3D 音效。 在應用程式中使用空間音效，可以讓開發人員 convincingly 在使用者周圍，以3維空間（球體）來放置聲音。 這些聽起來好像是來自實際的實體物件，或是使用者周圍的混合現實全息。 空間音效是強大的工具，可在混合現實應用程式中進行深度、協助工具及 UX 設計。

### <a name="device-impact"></a>裝置影響

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

|  效果  |  遇到 |  無法 |
--- | --- | ---
|  音效會以邏輯方式 hrtf，而 UX 會適當地使用音效來協助物件探索和使用者意見反應。 音效是自然且與物件相關，並會在案例中正規化。 | 空間音訊會適當地用於 believability，但缺少以協助使用者提供意見反應和發現。 | 音效不會如預期般 hrtf，也不會有聲音可協助使用者在 UX 中。 或在案例的設計中未考慮或使用空間音訊。 | 

### <a name="how-to-measure"></a>如何測量

* 一般情況下，相關的音效應該從目標的全息影像發出（例如，從全像攝影狗的吠聲）。
* 在整個 UX 中都應該使用音效提示，以協助使用者對全像攝影框架以外的動作提供意見反應或認知。

### <a name="recommendations"></a>建議事項

* 使用空間音訊來協助物件探索和使用者介面。
* 真實音效的效果優於合成或非自然音效。
* 大部分的音效都應該 hrtf。
* 避免隱藏的發射器。
* 避免空間遮罩。
* 標準化所有聲音。

### <a name="resources"></a>資源

#### <a name="documentation"></a>文件

* [空間音效](spatial-sound.md)
* [空間音效設計](spatial-sound-design.md)
* [Unity 中的空間音效](spatial-sound-in-unity.md)
* [案例研究，HoloTour 的空間音效](case-study-spatial-sound-design-for-holotour.md)
* [案例研究，使用 RoboRaid 中的空間音效](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a>工具和教學課程

* [MR 空間220：空間音效](holograms-220.md)
* [MRToolkit，空間音訊](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a>專注于全像攝影框架（FOV）界限

設計良好的使用者體驗，可以建立和維護虛擬環境的實用內容，以延伸使用者。 緩和 FOV 界限的效果牽涉到內容規模和內容的精心設計，使用空間音訊、指引系統和使用者的位置。 如果正確，使用者會覺得 FOV 界限不會受到影響，同時具備舒適的應用程式體驗。

### <a name="device-impact"></a>裝置影響

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

|  效果  |  遇到 |  無法 |
--- | --- | ---
|  使用者絕對不會失去內容，而且也很樂意進行觀看。 內容協助是針對大型物件所提供。 探索和流覽指引是針對框架外的物件所提供。 在一般情況下，動態影像的動作設計和縮放比例適用于熟悉的觀賞體驗。 | 使用者絕對不會失去內容，但是在有限的情況下可能需要額外的頸部動作。 在有限的情況下，調整會導致全息影像中斷垂直或水準框架，而導致一些頸部動作來觀看全息影像。 | 使用者可能會遺失內容和（或）一致的頸部動作，以查看全息影像。 大型的全像攝影物件沒有任何內容指引、在沒有發現性指引的框架外移動物件很容易遺失，或高度的全像投影需要週期性頸部動作來觀看。 | 

### <a name="how-to-measure"></a>如何測量

* （大型）全息的內容會因為在界限裁剪而遺失或無法瞭解。
* 因為缺乏注意的總監，或是快速移出全像攝影框架的內容，所以很難找到全息型的位置。
* 案例需要定期和重複的頭運動，才能完全看到全像疲勞的全息影像。

### <a name="recommendations"></a>建議事項

* 以符合 FOV 的小型物件開始體驗，然後以視覺提示轉換成較大的版本。
* 使用空間音訊和注意總監，協助使用者尋找 FOV 外的內容。
* 盡可能避免以垂直方式裁剪 FOV 的全息影像。
* 提供使用者應用程式內的指引，以取得最佳的流覽位置。

### <a name="resources"></a>資源

#### <a name="documentation"></a>文件

* [全像攝影框架](holographic-frame.md)
* [案例研究，HoloStudio UI 和互動設計學習](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [物件和環境的規模](scale.md)
* [游標，視覺提示](cursors.md#visual-cues)

#### <a name="external-references"></a>外部參考

* [FOV 的許多 ado](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a>使用者位置的內容反應

全息影像應該以「實際」物件的相同方式來回應使用者位置。 值得注意的設計考慮是 UI 元素，不一定會假設使用者的位置是固定的，而且會隨著使用者的動作而調整。 設計可正確適應使用者位置的應用程式，將會建立更可信的體驗，並讓您更容易使用。

### <a name="device-impact"></a>裝置影響

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
<td> 效果 </td><td> 內容和 UI 會適應使用者位置，讓使用者自然地與預期使用者移動範圍內的內容互動。</td>
</tr><tr>
<td> 遇到 </td><td> UI 會配合使用者位置，但可能會妨礙需要使用者調整其位置的重要內容的觀點。</td>
</tr><tr>
<td> 無法 </td><td><ol>
<li>UI 元素會在移動期間遺失或鎖定，導致使用者 unnaturally 返回（或尋找）控制項。</li><li>UI 元素會限制主要內容的顯示。</li><li>UI 移動不會針對觀看距離和動力而優化，特別是以<a href="billboarding-and-tag-along.md">標記為沿著</a>的 UI 元素。</li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a>如何測量

* 所有的測量都應該在案例的合理範圍內完成。 雖然使用者移動會有所不同，但不會嘗試透過極端的使用者移動來誘騙應用程式。
* 針對 UI 元素，不論使用者移動為何，都應該可以使用相關的控制項。 例如，如果使用者正在觀看3D 地圖並使用 zoom 進行流覽，則無論位置為何，縮放控制項都應該隨時可供使用者使用。

### <a name="recommendations"></a>建議事項

* 使用者是相機，並控制移動。 讓它們成為磁片磁碟機。
* 請考慮 billboarding 的文字和功能表系統，如果使用者想要四處移動，則會以世界鎖定或遮蔽的方式呈現。
* 針對需要追蹤使用者的內容使用標記，同時仍允許使用者查看其前面的內容。

### <a name="resources"></a>資源

#### <a name="documentation"></a>文件

* [互動設計](hologram.md)
* [色彩、光線和材質](color,-light-and-materials.md)
* [佈告板和常駐標籤](billboarding-and-tag-along.md)
* [本能互動](interaction-fundamentals.md)
* [自我移動和使用者 locomotion](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a>工具和教學課程

* [MR 輸入210：注視](holograms-210.md)

## <a name="input-interaction-clarity"></a>輸入互動清楚

輸入互動清楚是應用程式可用性的關鍵，並包含互動方法的輸入一致性、是多麼平易近人、可搜尋性。 使用者應該能夠在不重新的情況下，使用全平臺的通用互動。 如果應用程式具有自訂輸入，則應該清楚地溝通並示範。

### <a name="device-impact"></a>裝置影響

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

|  效果  |  遇到 |  無法 |
--- | --- | ---
|  輸入互動方法與 Windows Mixed Reality 一致提供的[指引](interaction-fundamentals.md)。 任何自訂輸入都不應該與標準輸入（而是使用標準互動）重複，而且必須清楚地傳達並向使用者示範。 | 與 [最佳] 類似，但自訂輸入與標準輸入方法是多餘的。 使用者仍可透過應用程式體驗達成目標和進度。 | 不易瞭解輸入法或按鈕對應。 輸入會經過大量自訂，不支援標準輸入、無指示，或可能導致疲勞和緩和問題。 | 

### <a name="how-to-measure"></a>如何測量

* 應用程式會使用一致的[標準輸入方法。](interaction-fundamentals.md)
* 如果應用程式有領域輸入，則會透過下列方式清楚地進行通訊：
* 首次執行體驗
* 簡介畫面
* 工具提示
* 手動教練
* 說明區段
* 聲音結束

### <a name="recommendations"></a>建議事項

* 盡可能使用標準輸入方法。
* 提供非標準輸入法的示範、教學課程和工具提示。
* 在整個應用程式中使用一致的互動模型。

### <a name="resources"></a>資源

#### <a name="documentation"></a>文件

* [本能互動](interaction-fundamentals.md)
* [可互動物件](interactable-object.md)
* [頭部目光和停駐](gaze-and-dwell.md)
* [游標](cursors.md)
* [舒適和注視](comfort.md#gaze-direction)
* [語音輸入](voice-input.md)
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

* [案例研究：對更個人運算的追求](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [轉換研究： HoloStudio UI 和互動設計學習](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [範例應用程式：元素的定期資料表](periodic-table-of-the-elements.md)
* [範例應用程式：農曆模組](lunar-module.md)
* [MR 輸入210：注視](holograms-210.md)
* [MR 輸入211：手勢](holograms-211.md)
* [MR 輸入212：語音](holograms-212.md)

## <a name="interactable-objects"></a>可互動物件

一個按鈕很長的比喻，是用來觸發2D 抽象世界中的事件。 在三維混合現實世界中，我們不再需要局限于此抽象概念。 任何專案都可以是觸發事件的可互動物件。 可互動物件可以從資料表上的咖啡杯，呈現為以空中浮動的球形文字。 不論表單為何，使用者都應該透過視覺和音訊提示清楚地辨識可互動物件。

### <a name="device-impact"></a>裝置影響

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

|  效果  |  遇到 |  無法 |
--- | --- | ---
|  不論何種形式，可互動物件都可以透過三個狀態的視覺和音訊提示來辨識： [閒置]、[目標] 和 [已選取]。 「瞭解這一點」在整個經驗中都是清楚且一致的使用方式。 系統會縮放並散佈物件，以允許錯誤的目標。 | 使用者可以透過音訊或視覺效果的意見反應，將物件辨識為可互動，並可將物件設為目標並啟動。 | 若未提供視覺或音訊提示，使用者就無法辨識可互動物件。 互動因物件縮放或物件之間的距離而容易出錯。 | 

### <a name="how-to-measure"></a>如何測量

* 可互動物件可辨識為 ' 可互動 ';包括按鈕、功能表和應用程式特定內容。 根據經驗法則，在以可互動物件為目標時，應該會有視覺和音訊提示。

### <a name="recommendations"></a>建議事項

* 使用視覺效果和音訊意見反應進行互動。
* 應針對每個輸入狀態（[閒置]、[目標]、[已選取]）區分視覺效果意見反應
* 可互動物件應調整並放置於錯誤的目標上。
* 群組的可互動物件（例如功能表列或清單）應具有適當的目標間距。
* 支援語音命令的按鈕和功能表應該提供命令關鍵字的文字標籤（「請參閱它」）

### <a name="resources"></a>資源

#### <a name="documentation"></a>文件

* [可互動的物件](interactable-object.md)
* [Unity 中的文字](text-in-unity.md)
* [週框方塊和應用程式列](app-bar-and-bounding-box.md)
* [語音輸入](voice-input.md)

#### <a name="tools-and-tutorials"></a>工具和教學課程

* [混合現實工具組-UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a>房間掃描

需要空間對應資料的應用程式會依賴裝置，在使用者探索其在使用中裝置的環境時，于一段時間內自動收集此資料。 此資料的完整性和品質取決於數個因素，包括使用者已完成的探索量、流覽後經過的時間，以及設備（例如傢俱和門）在掃描區域之後是否已移動。 許多應用程式會在體驗開始時分析空間對應資料，以判斷使用者是否應該執行額外的步驟來改善空間對應的完整性和品質。 如果需要使用者掃描環境，請在掃描體驗期間提供清楚的指引。

### <a name="device-impact"></a>裝置影響

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

|  效果  |  遇到 |  無法 |
--- | --- | ---
|  空間網格的視覺效果會告訴使用者掃描正在進行中。 使用者清楚知道要執行的動作，以及掃描開始和停止的時間。 | 提供空間網格的視覺效果，但使用者可能無法清楚瞭解該怎麼做，而且不會提供任何進度資訊。 | 沒有網格的視覺效果。 沒有提供指引資訊給使用者關於要查看的位置，或掃描開始/停止的時間。 |

### <a name="how-to-measure"></a>如何測量

* 在進行必要的房間掃描時，會提供視覺和音訊指引，指出要查看的位置，以及開始和停止掃描的時機。

### <a name="recommendations"></a>建議事項

* 指出使用者鄰近範圍中的總數量必須是體驗的一部分。
* 當掃描開始並停止（例如進度指示器）時進行通訊。
* 在掃描期間使用網格的視覺效果。
* 提供視覺和音訊提示，以鼓勵使用者在房間周圍尋找並移動。
* 通知使用者要在哪裡改善資料。 在許多情況下，最好告訴使用者需要執行的動作（例如，查看 [傢俱] 的上限），以便取得所需的掃描品質。

### <a name="resources"></a>資源

#### <a name="documentation"></a>文件

* [空間位置掃描視覺效果](room-scan-visualization.md)
* [案例研究：擴充 HoloLens 的空間對應功能](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [案例研究： HoloTour 的空間音效設計](case-study-spatial-sound-design-for-holotour.md)
* [案例研究：在片段中建立沉浸式體驗](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a>工具和教學課程

* [混合現實工具組-UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a>方向指標

在混合現實應用程式中，內容可能會在 pixels occluded 的欄位之外，或由真實世界的物件所組成。 設計良好的應用程式可讓使用者更輕鬆地尋找不可見的內容。 方向指標會向使用者通知重要內容，並提供相對於使用者位置的內容指引。 非可見內容的指引可以採用音效發射器、方向箭號或直接視覺提示的形式。

### <a name="device-impact"></a>裝置影響

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

|  效果  |  遇到 |  無法 |
--- | --- | ---
|  視覺效果和音訊提示會直接引導使用者前往視圖欄位以外的相關內容。 | 箭號或某個指標，會以內容的一般方向來指向使用者。 | 相關內容不在視野的範圍內，也不會提供不佳的位置指引給使用者。 | 

### <a name="how-to-measure"></a>如何測量

* [使用者] 欄位以外的相關內容可透過視覺效果和/或音訊提示來進行探索。

### <a name="recommendations"></a>建議事項

* 當相關內容超出使用者的視圖欄位時，請使用方向指標和音訊提示來引導使用者進行內容。 在許多情況下，直接視覺輔助線優先于方向箭號。
* 方向指標不應內建至游標處。

### <a name="resources"></a>資源

* [全像攝影框架](holographic-frame.md)

## <a name="data-loading"></a>資料載入

進度控制項為使用者提供回饋，告知正在進行長時間執行的操作。 這可能表示當進度指示器可見時，使用者無法與應用程式互動，也可以指出等候時間可能是多久。

### <a name="device-impact"></a>裝置影響

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

|  效果  |  遇到 |  無法 |
--- | --- | ---
|  以進度列或環形形式呈現的動畫視覺指標，顯示任何資料載入或處理期間的進度。 視覺指標會提供等待時間長度的指引。 | 使用者會收到資料載入正在進行中的通知，但不會指出等候的時間長度。 | 工作所花費的時間超過5秒的資料載入或處理指示器。 |

### <a name="how-to-measure"></a>如何測量

* 在資料載入期間，確認不會有超過5秒的空白狀態。

### <a name="recommendations"></a>建議事項

* 當使用者可能會感覺到此應用程式停止或損毀時，請提供資料載入 animator，以顯示任何情況下的進度。 合理的經驗法則是任何可能需要5秒以上的「載入」活動。

### <a name="resources"></a>資源

* [顯示進度](progress.md)
