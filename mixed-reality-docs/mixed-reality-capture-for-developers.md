---
title: 開發人員的混合現實 capture
description: 開發人員混合現實的最佳作法。
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc、相片、影片、capture、攝影機
ms.openlocfilehash: d1675d2d6c74c6d15ca245a66719e00f2a7c2111
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694367"
---
# <a name="mixed-reality-capture-for-developers"></a>開發人員的混合現實 capture

> [注意!]如需 HoloLens 2 新 MRC 功能的指引, 請參閱下列[PV 攝影機](#render-from-the-pv-camera-opt-in)的轉譯。

由於使用者可以隨時採取[混合現實 capture](mixed-reality-capture.md) (MRC) 相片或影片, 因此在開發應用程式時, 您應該記住幾件事。 這包括 MRC 視覺品質的最佳做法, 並在 MRCs 時回應系統變更。

開發人員也可以順暢地將混合現實的 capture 和插入整合到其應用程式中。

HoloLens (第一代) 上的 MRC 支援最多720p 的影片和相片, 而 HoloLens 2 上的 MRC 則支援最高1080p 和最多4K 解析度的影像。

## <a name="the-importance-of-quality-mrc"></a>品質 MRC 的重要性

混合現實已捕捉的相片和影片可能是使用者在您的應用程式中的第一次曝光。 在您的 Microsoft Store 頁面上, 還是在社交網路上共用 MRCs 的其他使用者上, 是否為混合現實螢幕擷取畫面。 您可以使用 MRC 來示範您的應用程式、教育使用者、鼓勵使用者分享其混合世界互動, 以及進行使用者研究和問題解決。

## <a name="how-mrc-impacts-your-app"></a>MRC 如何影響您的應用程式

### <a name="enabling-mrc-in-your-app"></a>在您的應用程式中啟用 MRC

根據預設, 應用程式不需要執行任何動作, 即可讓使用者進行混合的事實捕捉。

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a>針對您應用程式中的 MRC 啟用改良的對齊

根據預設, 混合現實 capture 會將適當的全像攝影輸出與相片/影片 (PV) 攝影機結合。 這兩個來源會使用目前執行的沉浸式應用程式所設定的焦點點進行結合。

這表示焦點平面外的全息影像也不會對齊 (因為 PV 攝影機和右邊顯示之間的實體距離)。

#### <a name="set-the-focus-point"></a>設定焦點點

沉浸式應用程式 (在 HoloLens 上) 應該設定其穩定平面所在的[焦點點](focus-point-in-unity.md)。 這可確保耳機和混合現實 capture 中的最佳對齊方式。

如果未設定焦點, 穩定平面會預設為兩個計量。

#### <a name="render-from-the-pv-camera-opt-in"></a>從 PV 攝影機轉譯 (加入宣告)

HoloLens 2 增加了當混合現實捕捉正在執行時, 沉浸式應用程式**從 PV 攝影機**轉譯的功能。 為了確保應用程式能夠正確支援額外的轉譯, 應用程式必須加入宣告這項功能。

從 PV 攝影機轉譯可提供下列對預設 MRC 體驗的改良功能:
* 您的實體環境和手上的全像投影對齊 (用於近距離互動) 應會隨時精確, 而不是在焦點點以外的距離 (如您在預設的 MRC 中看到)。
* 耳機中的適當眼睛不會受到危害, 因為它不會用來呈現 MRC 輸出的全息影像。

有三個步驟可讓您從 PV 攝影機進行轉譯:
1. 啟用 PhotoVideoCamera HolographicViewConfiguration
2. 處理其他 HolographicCamera 轉譯
3. 確認您的著色器和程式碼從這個額外的 HolographicCamera 正確呈現

##### <a name="enable-the-photovideocamera-holographicviewconfiguration"></a>啟用 PhotoVideoCamera HolographicViewConfiguration

若要加入宣告, 應用程式只會啟用 PhotoVideoCamera 的[HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration):
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfiguration.PhotoVideoCamera);
if (view != null)
{
   view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a>處理 DirectX 中的其他 HolographicCamera 轉譯

當應用程式選擇從 PV 攝影機轉譯時, 混合現實 capture 就會開始:
1. HolographicSpace 的 CameraAdded 事件將會引發。 如果應用程式目前無法處理相機, 此事件可能會延遲。
2. 一旦事件完成 (而且沒有任何未完成的延期), HolographicCamera 就會出現在下一個 HolographicFrame 的 [AddedCameras] 清單中。

當混合現實 capture 停止時 (或如果應用程式在混合現實 capture 執行時停用 view 設定): HolographicCamera 會出現在下一個 HolographicFrame 的 RemovedCameras 清單中, 而 HolographicSpace 的 CameraRemoved 事件將會從中.

已將[ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)屬性新增至 HolographicCamera, 以協助識別相機所屬的設定。

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a>處理 Unity 中的其他 HolographicCamera 轉譯

>[!NOTE]
> 從 PV 攝影機轉譯的 Unity 支援正在開發中, 尚無法使用。 當支援從 PV 攝影機轉譯的 Unity 組建可供使用時, 將會更新這份檔。

##### <a name="verify-shaders-and-code-support-additional-cameras"></a>驗證著色器和程式碼支援其他相機

執行混合的現實捕捉, 並檢查是否有不尋常的對齊、遺失的內容或效能問題。 適當地更新著色器和程式碼。

如果有某些場景無法支援轉譯為其他相機, 您可以在 PhotoVideoCamera 的 HolographicViewConfiguration 期間停用它。

### <a name="disabling-mrc-in-your-app"></a>在您的應用程式中停用 MRC

#### <a name="2d-app"></a>2D 應用程式

2D 應用程式可以選擇在執行混合現實 capture 時, 將其視覺內容遮蔽:
* 以[DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present)旗標呈現
* 使用[DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag)旗標來建立應用程式的交換鏈
* 使用 Windows 10 5 月2019更新, 設定 ApplicationView 的[IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)

#### <a name="immersive-app"></a>沉浸式應用程式

沉浸式應用程式可以選擇從混合現實 capture 中排除其視覺內容, 方法如下:
* 將 HolographicCameraRenderingParameter 的[IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled)設定為停用其相關聯框架的混合現實 capture
* 將 HolographicCamera 的[IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled)設定為停用其相關聯的全像攝影攝影機的混合現實 capture

#### <a name="password-keyboard"></a>密碼鍵盤

有了 Windows 10 的2019更新, 當顯示密碼或 pin 鍵盤時, 視覺內容會自動從混合現實 capture 中排除。

### <a name="knowing-when-mrc-is-active"></a>瞭解 MRC 何時處於作用中

應用程式可以使用[AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture)類別來知道何時執行系統混合現實 capture (針對音訊或影片)。

>[!NOTE]
>如果裝置上無法使用混合現實捕捉, AppCapture 的[GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) API 可能會傳回 null。 也請務必在應用程式暫停時, 取消註冊 CapturingChanged 事件, 否則 MRC 可能會進入封鎖狀態。

### <a name="best-practices-hololens-specific"></a>最佳做法 (HoloLens 特定)

MRC 預期不需要開發人員執行其他工作, 但有幾件事要注意, 以提供應用程式的最佳混合現實捕捉體驗。

**MRC 使用全息圖形的 Alpha 色板與[相機](locatable-camera.md)影像混合**

最重要的步驟是確定您的應用程式已清除為透明黑色, 而不是清除為不透明的黑色。 在 Unity 中, 這是根據 MixedRealityToolkit 的預設值, 但如果您是在非 Unity 中進行開發, 您可能需要變更一行。

如果您的應用程式未清除為透明黑色, 以下是您可能會在 MRC 中看到的一些成品:

**失敗的範例**:內容周圍的黑色邊緣 (無法清除為透明黑色)

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

**失敗的範例**:全像投影的整個背景場景會呈現黑色。 將背景 Alpha 值設定為1會導致黑色背景

![將背景 Alpha 值設定為1會導致黑色背景](images/clearopaqueblack-300px.png)

**預期的結果**:全息影像與真實世界有適當的混合 (如果清除為透明黑色, 則預期會產生結果)

![清除透明黑色時的預期結果](images/cleartransparentblack-300px.png)

**解決方案**：
* 將顯示為不透明黑色的任何內容變更為具有 Alpha 值0。
* 確定應用程式已清除為透明的黑色。
* Unity 預設為使用 MixedRealityToolkit 自動清除, 但如果它是非 Unity 應用程式, 您應該修改與 ID3D11DeiceCoNtext:: ClearRenderTargetView () 搭配使用的色彩。 您想要確保清除透明的黑色 (0, 0, 0, 0), 而不是不透明的黑色 (0, 0, 0, 1)。

如有需要, 您現在可以微調資產的 Alpha 值, 但通常不需要這麼做。 在大部分的情況下, MRCs 看起來都很好用。 MRC 會假設已乘以 Alpha。 Alpha 值只會影響 MRC 捕捉。

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a>在 HoloLens 上啟用 MRC 時的預期事項

以下適用于 HoloLens (第一代) 和 HoloLens 2, 除非另有注明:

* 系統會將應用程式節流以30Hz 轉譯。 這會建立一些可供 MRC 執行的空間, 因此應用程式不需要保留持續的預算保留, 而且也會符合30fps 的 MRC 影片記錄的畫面播放速率
* 在錄製/串流處理 MRC 時, 裝置上的全息影像內容可能會顯示為「閃爍」: 文字可能會變得更難以閱讀, 而全息全像投影邊緣可能會更 jaggy (在**HoloLens 2**上選擇第三張攝影機轉譯可避免這種危害)
* 如果應用程式已啟用「MRC 相片」和「影片」, 將會遵循該應用程式的[焦點](focus-point-in-unity.md), 這有助於確保全息影像的位置正確。 針對影片, 焦點會平滑, 因此如果焦點深度改變, 則全息影像可能會變得緩慢。 從焦點點不同深度的全息影像可能會顯示在現實世界中的位移 (請參閱下列範例, 其中的焦點是設定為2個計量, 但全息全像是位於1個計量)。

![以2計的全息影像會完全向世界註冊。 近距離或遠處的全息影像可能會有些許時差。](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a>從您的應用程式內整合 MRC 功能

您的混合現實應用程式可以從應用程式內起始 MRC 相片或影片捕捉, 而所捕捉到的內容則會提供給您的應用程式使用, 而不會儲存至裝置的「相機變換」。 您可以建立自訂的「MRC 錄製器」, 或利用內建的「相機捕捉」 UI。 

### <a name="mrc-with-built-in-camera-ui"></a>具有內建攝影機 UI 的 MRC

開發人員可以使用 *[相機擷取 UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* 取得的使用者擷取混合的實境相片或視訊，只要短短幾行程式碼。

此 API 會啟動內建的 MRC 攝影機 UI, 讓使用者可以在其中拍攝相片或影片, 並將產生的 capture 傳回給您的應用程式。  如果您想要建立自己的相機 UI, 或需要較低層級的 capture 串流存取, 您可以建立自訂的混合現實「捕捉錄製器」。

### <a name="creating-a-custom-mrc-recorder"></a>建立自訂的「MRC 錄製器」

雖然使用者一律可以使用系統 MRC 捕捉服務觸發相片或影片, 但應用程式可能會想要建立自訂相機應用程式, 但在相機串流中包含全息影像, 就像 MRC 一樣。 這可讓應用程式代表使用者啟動捕捉、建立自訂錄製 UI, 或自訂 MRC 設定來命名一些範例。

**HoloStudio 使用 MRC 效果新增自訂的 MRC 相機**

![HoloStudio 使用 MRC 效果新增自訂的 MRC 相機](images/cameraiconholostudio-300px.jpg)

Unity 應用程式應該會看到屬性的[Locatable_camera_in_Unity](locatable-camera-in-unity.md) , 以啟用全息影像。

其他應用程式可以使用[Windows Media Capture api](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture)控制相機並新增 MRC 影片和音訊效果, 以在靜止和影片中包含虛擬的全息影像和應用程式音訊, 來執行這項操作。

應用程式有兩個選項可新增效果:
* 舊版 API:[MediaCapture. AddEffectAsync ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)
* 新的 Microsoft 建議 API (會傳回物件, 讓您能夠操作動態屬性):[MediaCapture. AddVideoEffectAsync ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync)  /  [MediaCapture AddAudioEffectAsync ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) , 它會要求應用程式建立自己的[IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition)執行, 以及[IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition)。 如需範例使用方式, 請參閱 MRC 效果範例。

>[!NOTE]
> Visual Studio 將無法辨識 MixedRealityCapture 命名空間, 但字串仍然有效。

MRC 影片效果 (**Windows. MixedRealityCapture. MixedRealityCaptureVideoEffect**)

|  屬性名稱  |  Type  |  Default Value  |  描述 | 
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))  |  1 (VideoRecord)  |  描述此效果用於哪一個捕捉串流。 音訊無法使用。 | 
|  HologramCompositionEnabled  |  boolean  |  TRUE  |  用來啟用或停用影片捕捉中的全息影像的旗標。 | 
|  RecordingIndicatorEnabled  |  boolean  |  TRUE  |  用來啟用或停用在全息影像捕捉期間錄製指示器的旗標。 | 
|  VideoStabilizationEnabled  |  boolean  |  FALSE  |  用來啟用或停用 HoloLens 追蹤程式所支援之視頻穩定的旗標。 | 
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  設定用於視頻穩定的歷程記錄畫面格數目。 從電源和效能的角度來看, 0 為 0-延遲, 幾乎是「免費」。 15是建議的最高品質 (以延遲和記憶體15個畫面的成本為代價)。 | 
|  GlobalOpacityCoefficient  |  FLOAT  |  0.9 (HoloLens) 1.0 (沉浸式耳機)  |  設定從 0.0 (完全透明) 到 1.0 (完全不透明) 範圍內的全息影像全域不透明度係數。 | 
|  BlankOnProtectedContent  |  boolean  |  FALSE  |  當有 2d UWP 應用程式顯示受保護的內容時, 啟用或停用的旗標會傳回空白框架。 如果此旗標為 false, 而 2d UWP 應用程式顯示受保護的內容, 則 2d UWP 應用程式將會被耳機和混合現實捕捉中的受保護內容材質取代。 |
|  ShowHiddenMesh  |  boolean  |  FALSE  |  用來啟用或停用顯示全像攝影機的隱藏區網格和鄰近內容的旗標。 |
| OutputSize | Size | 0、0 | 在裁剪影片穩定之後, 設定所需的輸出大小。 如果指定0或不正確輸出大小, 則會選擇預設的裁剪大小。 |
| PreferredHologramPerspective | UINT32 | 1 (PhotoVideoCamera) | 列舉, 用來指出應該捕捉的全像攝影視圖設定。 設定 0 (顯示) 表示不會要求應用程式從相片/攝影機呈現 |

MRC 音訊效果 (**Windows MixedRealityCapture. MixedRealityCaptureAudioEffect**)

<table>
<tr>
<th>屬性名稱</th>
<th>Type</th>
<th>Default Value</th>
<th>描述</th>
</tr>
<tr>
<td>MixerMode</td>
<td>UINT32</td>
<td>2</td>
<td>
<ul>
<li>0僅限 Mic 音訊</li>
<li>sha-1僅限系統音訊</li>
<li>2Mic 和系統音訊</li>
</ul>
</td>
</tr>
</table>

### <a name="simultaneous-mrc-limitations"></a>同時 MRC 限制

同時存取 MRC 的多個應用程式有某些限制。

#### <a name="photovideo-camera-access"></a>相片/攝影機存取

相片/攝影機僅限於可以同時存取它的進程數目。 當處理常式正在錄製影片或拍攝相片時, 任何其他程式將無法取得相片/攝影機。 (這同時適用于混合現實捕捉和標準相片/影片捕捉)

使用 HoloLens 2, 應用程式可以使用 MediaCaptureInitializationSettings 的[SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode)內容來指出, 如果他們不需要對相片/攝影機進行獨佔控制, 他們想要執行 SharedReadOnly。 這麼做表示, 捕捉的解析度和畫面播放速率會限制為其他應用程式已設定相機提供的功能。

##### <a name="built-in-mrc-photovideo-camera-access"></a>內建的 MRC 相片/攝影機存取

Windows 10 內建的 MRC 功能 (透過 Cortana、[開始] 功能表、硬體快捷方式、Miracast、Windows 裝置入口網站):
* 預設會以 ExclusiveControl 執行

不過, 已將支援新增至每個子系統, 以共用模式運作:
* 如果應用程式要求相片/攝影機的 ExclusiveControl 存取權, 內建的 MRC 會自動停止使用相片/攝影機, 讓應用程式的要求成功
* 如果在應用程式有 ExclusiveControl 時啟動內建的 MRC, 內建的 MRC 會在 SharedReadOnly 模式中執行

此共用模式功能有一些限制:
* 透過 Cortana、硬體快捷方式或 [開始] 功能表的相片:需要 Windows 10 2018 年4月更新 (或更新版本)
* 透過 Cortana、硬體快捷方式或 [開始] 功能表的影片:需要 Windows 10 2018 年4月更新 (或更新版本)
* 透過 Miracast 的串流處理 MRC:需要 Windows 10 2018 年10月更新 (或更新版本)
* 透過 Windows 裝置入口網站或透過 HoloLens 隨附應用程式來串流處理 MRC:需要 HoloLens 2

>[!NOTE]
> 當另一個應用程式正在使用相片/攝影機時, 內建 MRC 相機 UI 的解析度和畫面播放速率可能會從其正常值中縮減。

#### <a name="mrc-access"></a>MRC 存取

在 Windows 10 四月份2018更新中, 有多個應用程式存取 MRC 串流不再受限制 (不過, 相片/攝影機的存取仍然有限制)。

在 Windows 10 4 月2018更新之前, 應用程式的自訂 MRC 錄製器與系統 MRC (從 Windows 裝置入口網站捕捉相片、捕獲影片或串流) 互斥。

## <a name="see-also"></a>另請參閱
* [混合實境擷取](mixed-reality-capture.md)
* [觀眾檢視](spectator-view.md)
