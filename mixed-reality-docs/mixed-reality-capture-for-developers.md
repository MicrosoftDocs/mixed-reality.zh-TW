---
title: 混合實境擷取適用於開發人員
description: 適用於開發人員，擷取的混合實境的最佳作法。
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc、 相片、 視訊、 擷取、 相機
ms.openlocfilehash: c2d98baf16b2ea724247224aabadc1e2ca533ec1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591595"
---
# <a name="mixed-reality-capture-for-developers"></a>混合實境擷取適用於開發人員

> [!NOTE]
> HoloLens 2 的特定的詳細指引[即將推出](index.md#news-and-notes)。 

請參閱[應用程式中的啟用 MRC](#enabling-mrc-in-your-app)以下新的 MRC 功能有關的 HoloLens 2 指導方針。

因為使用者無法接管[混合實境擷取](mixed-reality-capture.md)(MRC) 相片或視訊在任何時間，有幾件事開發您的應用程式時，您應該謹記在心。 這包括 MRC 視覺品質和正在回應系統的變更，正在擷取 MRCs 時的最佳作法。

開發人員可以也會順暢地整合混合的實境擷取和插入自己的應用程式。

MRC HoloLens （第一代） 上的支援視訊和相片最多 720p，雖然 MRC HoloLens 2 上的啟動支援高達 1080p 和相片的影片，4k 解析度。

## <a name="the-importance-of-quality-mrc"></a>品質 MRC 的重要性

混合的實境擷取相片和影片可能是使用者會有您的應用程式的第一次。 是否為您的 Microsoft Store 頁面上，或從共用 MRCs 社交網路上其他使用者的混合的實境螢幕擷取畫面。 您可以使用 MRC 來示範您的應用程式，所以請教導使用者，鼓勵使用者共用其混合的環境的互動，以及根據使用者研究和解決問題。

## <a name="how-mrc-impacts-your-app"></a>MRC 會如何影響您的應用程式

### <a name="enabling-mrc-in-your-app"></a>應用程式中啟用 MRC

根據預設，應用程式並沒有採取任何動作，讓使用者可以採取混合的實境擷取。 不過，因為 HoloLens 2 的設計會增加相片/影片 (PV) 相機與顯示之間的距離，我們將會引進新的選項，來產生第 3 個相機轉譯對齊 PV 相機**HoloLens 2**。 

選擇單元到第 3 個攝影機呈現 HoloLens 2 供應項目上下列增強功能對預設 MRC 經驗：
* 全像您實體環境和實際操作 （適用於幾近互動） 的對齊方式應該是精確完全距離，而不是有的位移距離以外[專注點](focus-point-in-unity.md)您可能會看到預設 MRC 中。
* 耳機在右邊的眼睛將不會遭到入侵，因為它不會用來呈現全像投影 MRC 輸出。

### <a name="disabling-mrc-in-your-app"></a>在您的應用程式中停用 MRC

當 2D 應用程式時，使用[DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://msdn.microsoft.com/library/windows/desktop/bb509554(v=vs.85).aspx)或是[DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://msdn.microsoft.com/library/windows/desktop/bb173076(v=vs.85).aspx)應用程式的視覺化內容將會顯示具有正確設定交換鏈結的受保護的內容，混合的實境擷取正在執行時，會自動隱藏。

### <a name="knowing-when-mrc-is-active"></a>了解當 MRC 在作用中

[AppCapture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.aspx)類別可用的應用程式中了解混合實境擷取的系統 （例如音訊或視訊） 的執行時。

>[!NOTE]
>AppCapture [GetForCurrentView](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.getforcurrentview.aspx) API 可以傳回 null，如果混合實境擷取無法在裝置上使用。 務必也要取消註冊您的應用程式已暫止的 CapturingChanged 事件，否則 MRC 可以進入封鎖狀態。

### <a name="best-practices-hololens-specific"></a>最佳作法 （特定的 HoloLens）

MRC 應該可以運作而不需要額外的工作，從開發人員，但有幾件事要注意的以提供最適合混合的實境擷取經驗，您的應用程式。

**MRC 使用全像圖的 alpha 色頻來與混合[相機](locatable-camera.md)圖像**

最重要的步驟是確定您的應用程式會藉由清除設為透明的黑色，而不是不透明的黑色的清除。 在 Unity 中，這是藉由使用 MixedRealityToolkit 的預設值，但如果您正在開發非 Unity 中，您可能需要進行變更的一行。

以下是一些您可能會看到在 MRC 如果您的應用程式不會清除為透明的黑色的成品：

**範例失敗**:（無法清除以透明的黑色） 內容周圍邊緣的黑色

<table>
<tr>
<td>
<img src="images/chessboardblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
<td>
<img src="images/fieldblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
</tr>
</table>

**範例失敗**:整個背景場景的全像圖會顯示為黑色。 黑色背景中設定背景 alpha 值的 1 個結果

![黑色背景中設定背景 alpha 值的 1 個結果](images/clearopaqueblack-300px.png)

**預期的結果**:全像投影出現正確混合使用真實世界 （如果設為透明黑色清除預期結果）

![預期的結果，如果設為透明黑色清除](images/cleartransparentblack-300px.png)

**解決方案**：
* 變更為不透明的黑色出現有 alpha 值為 0 的任何內容。
* 請確定應用程式會清除為透明的黑色。
* 清除 自動清除 MixedRealityToolkit，但如果它是您應該修改與 ID3D11DeiceContext::ClearRenderTargetView() 搭配使用的色彩的非 Unity 應用程式使用的 unity 預設值。 您想要確保您清除設為透明的黑色 (0,0,0,0)，而不是不透明的黑色 (0,0,0,1)。

如果您想要但通常不需要您現在可以微調您的資產的 alpha 值。 大部分的情況下，MRCs 看起來良好現成的。 MRC 假設預乘的 alpha。 Alpha 值只會影響 MRC 擷取。

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a>MRC HoloLens 上啟用時的行為

下列適用於 （第一代） 的 HoloLens 和 HoloLens 2，除非另有說明：

* 系統將會節流處理至 30 赫茲轉譯應用程式。 這會建立執行，因此應用程式不需要保留固定的預算保留 MRC 一些成長空間，並也會比對的 30fps MRC 影片記錄畫面播放速率
* 全像圖內容眼裡出正確的裝置時可能會出現以"火花"錄製/串流 MRC： 文字可能會變得更難以讀取和全像邊緣可能會出現更多鋸齒 (選擇單元到第 3 個攝影機上呈現**HoloLens 2**避免此入侵）
* MRC 相片和視訊，則會採用應用程式的[專注點](focus-point-in-unity.md)如果應用程式已啟用它，這將有助於確保全像投影會精確地放置。 影片，焦點是經過平滑處理讓全像投影似乎緩慢漂移原位如果鶗懘深度發生重大變更。 在不同的深度，焦點從全像投影中可能會顯示位移真實世界 （請參閱以下範例焦點設在 2 個計量，但闀位於 1 公尺）。

![2 個計量在全像投影會完全註冊到世界。 全像投影在關閉或遠的距離可能有些微的位移。](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a>將從您的應用程式內的 MRC 功能整合

您的混合的實境應用程式可以起始 MRC 相片或視訊擷取在 app 中，和擷取的內容開放給您的應用程式而不儲存至裝置的 「 數位相機向前復原。 」 您可以建立自訂的 MRC 錄製器，或利用內建相機擷取 UI。 

### <a name="mrc-with-built-in-camera-ui"></a>使用內建相機 UI MRC

開發人員可以使用 *[相機擷取 UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* 取得的使用者擷取混合的實境相片或視訊，只要短短幾行程式碼。

此 API 會啟動內建 MRC 相機 UI，使用者可以拍攝相片或視訊，並傳回結果擷取到您的應用程式。  如果您想要建立您自己的相機 UI，或需要較低層級存取擷取資料流，您可以建立自訂的混合實境擷取錄製器。

### <a name="creating-a-custom-mrc-recorder"></a>建立自訂的 MRC 錄製器

使用者一律可以觸發相片或視訊使用系統 MRC 擷取服務，而應用程式可能想要建置自訂的相機應用程式，但如同 MRC 相機資料流中包含全像投影中。 這可讓應用程式開始執行代表使用者擷取、 建置自訂的錄製作業的 UI，或自訂 MRC 設定舉幾個例子。

**HoloStudio 新增自訂 MRC 相機使用 MRC 效果**

![HoloStudio 新增自訂 MRC 相機使用 MRC 效果](images/cameraiconholostudio-300px.jpg)

Unity 應用程式應該會看到[Locatable_camera_in_Unity](locatable-camera-in-unity.md)来啟用全像投影的屬性。

其他應用程式可以使用來執行這[Windows 媒體擷取 Api](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx)控制相機，並新增 MRC 視訊和音訊效果中仍然可和影片包含虛擬全像投影和應用程式音訊。

應用程式具有要新增效果的兩個選項：
* 較舊的 API:[Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://msdn.microsoft.com/library/windows/apps/br211961.aspx)
* 新的 Microsoft 建議 API （傳回的物件，因此您能夠管理動態屬性）：[Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addvideoeffectasync.aspx) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addaudioeffectasync.aspx) ，您需要應用程式建立其自己實作[IVideoEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.ivideoeffectdefinition.aspx)並[IAudioEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.iaudioeffectdefinition.aspx)。 請參閱範例使用方式的 MRC 作用範例。

（請注意，Visual Studio 中，不會辨識這些命名空間，但字串仍然有效）

MRC 視訊效果 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)

|  屬性名稱  |  類型  |  預設值  |  描述 | 
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([MediaStreamType](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediastreamtype.aspx))  |  1 (VideoRecord)  |  描述對使用此效果的擷取資料流。 不使用音訊。 | 
|  HologramCompositionEnabled  |  布林值  |  TRUE  |  若要啟用或停用全像投影影片擷取畫面中的旗標。 | 
|  RecordingIndicatorEnabled  |  布林值  |  TRUE  |  若要啟用或停用在全像擷取的畫面上的記錄指標的旗標。 | 
|  VideoStabilizationEnabled  |  布林值  |  FALSE  |  若要啟用或停用由 HoloLens 追蹤器的視訊穩定功能旗標。 | 
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  設定歷程記錄的框架數目用於視訊穩定功能。 0 是 0 延遲和幾乎 「 免費 」 能力和效能的觀點。 建議 （但要付出的延遲和記憶體的 15 框架） 的最高品質的 15。 | 
|  GlobalOpacityCoefficient  |  FLOAT  |  0.9 (HoloLens) 1.0 （沈浸式耳機）  |  設定全域的不透明度係數的全像範圍中從 0.0 （完全透明） 到 1.0 （完全不透明）。 | 
|  BlankOnProtectedContent  |  布林值  |  FALSE  |  若要啟用或停用 如果沒有 2d 的 UWP 應用程式顯示受保護的內容，傳回空框架的旗標。 如果這個旗標設定為 false 且 2d UWP 應用程式會顯示受保護的內容、 2d 的 UWP 應用程式將會取代受保護的內容材質中這兩個耳機及混合的實境擷取畫面中。 |
|  ShowHiddenMesh  |  布林值  |  FALSE  |  若要啟用或停用顯示全像攝影版相機的隱藏的區域網格和相鄰內容的旗標。 |

MRC 音訊效果 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)

<table>
<tr>
<th>屬性名稱</th>
<th>類型</th>
<th>預設值</th>
<th>描述</th>
</tr>
<tr>
<td>MixerMode</td>
<td>UINT32</td>
<td>2</td>
<td>
<ul>
<li>0 :僅限 mic 音訊</li>
<li>1 :僅限系統音訊</li>
<li>2 :Mic 和系統音訊</li>
</ul>
</td>
</tr>
</table>

### <a name="simultaneous-mrc-limitations"></a>同時 MRC 限制

有多個應用程式在同一時間存取 MRC 周圍的某些限制。

#### <a name="photovideo-camera-access"></a>相片/影片相機存取

相片或視訊攝影機僅限於在同一時間可以存取它的處理序數目。 處理序正在錄製影片，或利用任何其他處理序的相片將會失敗取得相片/影片相機。 （這適用於混合實境擷取和標準的相片/影片擷取）

使用 Windows 10 April 2018 Update，這項限制不適用於如果內建的 MRC 相機 UI 用來讓照相或拍攝影片之後應用程式已開始使用相片/影片相機。 當發生這種情況的內建的 MRC 相機 UI 畫面播放速率與解析度可能會降低其一般的值。

使用 Windows 10 年 10 月 2018 Update，這項限制不適用於透過 Miracast 串流 MRC。

#### <a name="mrc-access"></a>MRC 存取

使用 Windows 10 April 2018 Update，不再有多個應用程式存取 （不過，存取相片/影片相機仍有限制） MRC 資料流周圍的限制。

先前的 windows 10 April 2018 Update，應用程式的自訂 MRC 錄製器已與系統 MRC （擷取相片、 擷取影片或來自 Windows Device Portal） 互斥。

## <a name="see-also"></a>另請參閱
* [混合的實境擷取](mixed-reality-capture.md)
* [Spectator 檢視](spectator-view.md)
