---
title: 混合實境擷取適用於開發人員
description: 適用於開發人員，擷取的混合實境的最佳作法。
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc、 相片、 視訊、 擷取、 相機
ms.openlocfilehash: d1675d2d6c74c6d15ca245a66719e00f2a7c2111
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694367"
---
# <a name="mixed-reality-capture-for-developers"></a>混合實境擷取適用於開發人員

> [注意 ！]請參閱[PV 相機中呈現](#render-from-the-pv-camera-opt-in)以下新的 MRC 功能有關的 HoloLens 2 指導方針。

因為使用者無法接管[混合實境擷取](mixed-reality-capture.md)(MRC) 相片或視訊在任何時間，有幾件事開發您的應用程式時，您應該謹記在心。 這包括 MRC 視覺品質和正在回應系統的變更，正在擷取 MRCs 時的最佳作法。

開發人員可以也會順暢地整合混合的實境擷取和插入自己的應用程式。

MRC HoloLens （第一代） 上的支援視訊和相片最多 720p，雖然 MRC HoloLens 2 上的啟動支援高達 1080p 和相片的影片，4k 解析度。

## <a name="the-importance-of-quality-mrc"></a>品質 MRC 的重要性

混合的實境擷取相片和影片可能是使用者會有您的應用程式的第一次。 是否為您的 Microsoft Store 頁面上，或從共用 MRCs 社交網路上其他使用者的混合的實境螢幕擷取畫面。 您可以使用 MRC 來示範您的應用程式，所以請教導使用者，鼓勵使用者共用其混合的環境的互動，以及根據使用者研究和解決問題。

## <a name="how-mrc-impacts-your-app"></a>MRC 會如何影響您的應用程式

### <a name="enabling-mrc-in-your-app"></a>應用程式中啟用 MRC

根據預設，應用程式並沒有採取任何動作，讓使用者可以採取混合的實境擷取。

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a>啟用 MRC 應用程式中的改善的調整

根據預設，混合的實境擷取會結合相片/影片 (PV) 相機右邊的眼睛全像攝影版的輸出。 這些兩個來源會結合使用由目前執行的沈浸式應用程式設定的焦點。

這表示全像投影焦點平面之外，不會對齊也 （因為 PV 觀景窗之間的正確顯示實際的距離）。

#### <a name="set-the-focus-point"></a>設定焦點

（在 HoloLens) 的沈浸式應用程式應該設定[專注點](focus-point-in-unity.md)使用者想要其穩定平面的位置。 這可確保最佳的對齊方式，在這兩個耳機和混合的實境擷取。

如果未設定婧鎏鶗懘，穩定平面將會預設為兩個計量。

#### <a name="render-from-the-pv-camera-opt-in"></a>呈現從 PV 相機 （選用功能）

HoloLens 2 加入沈浸式應用程式的能力**PV 相機中呈現**混合的實境擷取正在執行時。 若要確保正確的應用程式支援的其他轉譯，則應用程式必須 opt-in 以這項功能。

轉譯 PV 相機的供應項目從以下的改良，對預設 MRC 經驗：
* 全像您實體環境和實際操作 （適用於幾近互動） 的對齊方式應該是正確的完全距離，而不需要在焦點點以外的距離的位移，您可能會看到預設 MRC。
* 耳機在右邊的眼睛將不會遭到入侵，因為它不會用來呈現全像投影 MRC 輸出。

有三個步驟，若要啟用轉譯從 PV 相機：
1. 啟用 PhotoVideoCamera HolographicViewConfiguration
2. 處理其他 HolographicCamera 轉譯
3. 請確認您的著色器和程式碼正確呈現此額外 HolographicCamera 從

##### <a name="enable-the-photovideocamera-holographicviewconfiguration"></a>啟用 PhotoVideoCamera HolographicViewConfiguration

若要選擇加入應用程式只是讓 PhotoVideoCamera [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration):
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfiguration.PhotoVideoCamera);
if (view != null)
{
   view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a>處理其他 HolographicCamera 呈現在 DirectX

當應用程式已選擇加入要呈現從 PV 相機及混合的實境擷取功能開始：
1. HolographicSpace 的 CameraAdded 事件就會引發。 如果應用程式無法處理觀景窗在這個階段，就會延期此事件。
2. 當事件完成 （而且有任何未完成延期時） HolographicCamera 會出現在下一步 的 HolographicFrame AddedCameras 清單中。

當混合的實境擷取停駐點 （或應用程式在混合的實境擷取正在執行時，會停用檢視設定）： HolographicCamera 會出現在下一步 的 HolographicFrame RemovedCameras 清單和 HolographicSpace CameraRemoved 事件將引發。

A [ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) HolographicCamera 以協助找出相機所屬的設定已加入屬性。

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a>處理其他 HolographicCamera 呈現在 Unity 中

>[!NOTE]
> 要呈現 PV 相機中的 unity 支援正在開發，尚無法使用。 PV 相機中的轉譯支援 Unity 組建可用時，將會更新這份文件。

##### <a name="verify-shaders-and-code-support-additional-cameras"></a>確認著色器和程式碼支援其他觀景窗

執行混合的實境擷取和檢查有不尋常的對齊方式、 遺失的內容或效能問題。 更新著色器和適當的程式碼。

某些無法支援額外的攝影機呈現的場景時，您可以在這些期間停用 PhotoVideoCamera HolographicViewConfiguration。

### <a name="disabling-mrc-in-your-app"></a>在您的應用程式中停用 MRC

#### <a name="2d-app"></a>2D 應用程式

2D 應用程式可以選擇隱藏執行混合的實境擷取時其視覺化內容：
* 看見[DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present)旗標
* 建立具有應用程式的交換鏈結[DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag)旗標
* Windows 10 可能 2019年更新，請設定 ApplicationView 的[IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)

#### <a name="immersive-app"></a>沈浸式應用程式

沈浸式應用程式可以選擇排除，藉以混合的實境擷取其視覺化內容：
* 設定的 HolographicCameraRenderingParameter [IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled)停用混合的實境擷取其相關聯的框架
* 設定的 HolographicCamera [IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled)停用其相關聯的全像攝影版相機的混合的實境擷取

#### <a name="password-keyboard"></a>密碼鍵盤

Windows 10 可能 2019年的更新，可以看到密碼或 pin 碼的鍵盤時，混合的實境擷取自動排除視覺內容。

### <a name="knowing-when-mrc-is-active"></a>了解當 MRC 在作用中

[AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture)類別可用的應用程式中了解混合實境擷取的系統 （例如音訊或視訊） 的執行時。

>[!NOTE]
>AppCapture [GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) API 可以傳回 null，如果混合實境擷取無法在裝置上使用。 務必也要取消註冊您的應用程式已暫止的 CapturingChanged 事件，否則 MRC 可以進入封鎖狀態。

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

其他應用程式可以使用來執行這[Windows 媒體擷取 Api](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture)控制相機，並新增 MRC 視訊和音訊效果中仍然可和影片包含虛擬全像投影和應用程式音訊。

應用程式具有要新增效果的兩個選項：
* 較舊的 API:[Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)
* 新的 Microsoft 建議 API （傳回的物件，因此您能夠管理動態屬性）：[Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) ，您需要應用程式建立其自己實作[IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition)並[IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition)。 請參閱範例使用方式的 MRC 作用範例。

>[!NOTE]
> Visual Studio 中，不會辨識 Windows.Media.MixedRealityCapture 命名空間，但字串仍然有效。

MRC 視訊效果 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)

|  屬性名稱  |  type  |  Default Value  |  描述 | 
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))  |  1 (VideoRecord)  |  描述對使用此效果的擷取資料流。 不使用音訊。 | 
|  HologramCompositionEnabled  |  boolean  |  TRUE  |  若要啟用或停用全像投影影片擷取畫面中的旗標。 | 
|  RecordingIndicatorEnabled  |  boolean  |  TRUE  |  若要啟用或停用在全像擷取的畫面上的記錄指標的旗標。 | 
|  VideoStabilizationEnabled  |  boolean  |  FALSE  |  若要啟用或停用由 HoloLens 追蹤器的視訊穩定功能旗標。 | 
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  設定歷程記錄的框架數目用於視訊穩定功能。 0 是 0 延遲和幾乎 「 免費 」 能力和效能的觀點。 建議 （但要付出的延遲和記憶體的 15 框架） 的最高品質的 15。 | 
|  GlobalOpacityCoefficient  |  FLOAT  |  0.9 (HoloLens) 1.0 （沈浸式耳機）  |  設定全域的不透明度係數的全像範圍中從 0.0 （完全透明） 到 1.0 （完全不透明）。 | 
|  BlankOnProtectedContent  |  boolean  |  FALSE  |  若要啟用或停用 如果沒有 2d 的 UWP 應用程式顯示受保護的內容，傳回空框架的旗標。 如果這個旗標設定為 false 且 2d UWP 應用程式會顯示受保護的內容、 2d 的 UWP 應用程式將會取代受保護的內容材質中這兩個耳機及混合的實境擷取畫面中。 |
|  ShowHiddenMesh  |  boolean  |  FALSE  |  若要啟用或停用顯示全像攝影版相機的隱藏的區域網格和相鄰內容的旗標。 |
| OutputSize | Size | 0, 0 | 在剪輯的視訊穩定後，設定想要的輸出大小。 如果指定了 0 或無效的輸出大小，則會選擇預設裁剪大小。 |
| PreferredHologramPerspective | UINT32 | 1 (PhotoVideoCamera) | 列舉用來指出應該擷取哪種全像攝影版的相機檢視設定。 設定 0 （顯示器） 表示應用程式不會呈現從相片或視訊攝影機要求 |

MRC 音訊效果 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)

<table>
<tr>
<th>屬性名稱</th>
<th>type</th>
<th>Default Value</th>
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

HoloLens 2 應用程式可以使用的 MediaCaptureInitializationSettings [SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode)屬性，指出他們想要執行 SharedReadOnly，如果它們不需要將相片/攝影機的專有控制權。 擷取的畫面播放速率與解析度，這樣做表示會受限於其他應用程式已設定的項目提供的相機。

##### <a name="built-in-mrc-photovideo-camera-access"></a>內建 MRC 相片/影片相機存取

內建於 Windows 10 （透過 Cortana、 [開始] 功能表、 硬體快速鍵 Miracast、 Windows Device Portal） MRC 功能：
* 預設會使用 ExclusiveControl 執行

不過，支援已新增至每個子系統，在共用模式中運作：
* 如果應用程式要求 ExclusiveControl 存取相片/攝影機，內建 MRC 將會自動停止使用相片/攝影機，因此應用程式的要求將會成功
* 如果內建 MRC 已啟動時，應用程式必須 ExclusiveControl，內建 MRC 將以 SharedReadOnly 模式執行

此共用的模式功能具有某些限制：
* 相片透過 Cortana、 硬體的捷徑或 [開始] 功能表：需要 Windows 10 April 2018 Update （或更新版本）
* 透過 Cortana、 硬體的捷徑或 [開始] 功能表的影片：需要 Windows 10 April 2018 Update （或更新版本）
* 資料流透過 Miracast MRC:需要 Windows 10 年 10 月 2018年更新 （或更新版本）
* 透過 Windows Device Portal，或透過 HoloLens 小幫手應用程式的資料流 MRC:需要 HoloLens 2

>[!NOTE]
> 內建的 MRC 相機 UI 畫面播放速率與解析度可能會降低其一般的值從另一個應用程式使用相片/攝影機時。

#### <a name="mrc-access"></a>MRC 存取

使用 Windows 10 April 2018 Update，不再有多個應用程式存取 （不過，存取相片/影片相機仍有限制） MRC 資料流周圍的限制。

先前的 windows 10 April 2018 Update，應用程式的自訂 MRC 錄製器已與系統 MRC （擷取相片、 擷取影片或來自 Windows Device Portal） 互斥。

## <a name="see-also"></a>另請參閱
* [混合實境擷取](mixed-reality-capture.md)
* [觀眾檢視](spectator-view.md)
