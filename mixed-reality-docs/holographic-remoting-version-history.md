---
title: 全像遠端版本歷程記錄
description: HoloLens 2 上全像攝影遠端處理的版本歷程記錄。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens、遠端、全像攝影遠端
ms.openlocfilehash: 1f4d463ab734cbb627f251486b0058fbf295d2ed
ms.sourcegitcommit: b392847529961ac36bbff154ce0830f8b2dbd766
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86300516"
---
# <a name="holographic-remoting-version-history"></a>全像遠端版本歷程記錄

> [!IMPORTANT]
> 本指導方針專屬於 HoloLens 2 上的全像攝影遠端處理。

## <a name="version-222-july-10-2020"></a>版本 2.2.2 (2020 年7月10日) <a name="v2.2.2"></a>
* 已修正[HolographicCamera. LeftViewportParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.leftviewportparameters?view=winrt-19041#Windows_Graphics_Holographic_HolographicCamera_LeftViewportParameters)和[HolographicCamera](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.rightviewportparameters?view=winrt-19041#Windows_Graphics_Holographic_HolographicCamera_RightViewportParameters)的問題。從 Windows Mixed Reality 耳機進行串流處理時，不會傳回任何隱藏的區域網格頂點。
* 已修正網路連線不佳時可能發生的損毀。

## <a name="version-221-july-6-2020"></a>版本 2.2.1 (2020 年7月6日) <a name="v2.2.1"></a>
> [!IMPORTANT]
> 具有版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)的[Windows 應用程式認證套件](https://developer.microsoft.com/windows/downloads/app-certification-kit/)驗證將會失敗。 如果您是在版本[2.2.0](holographic-remoting-version-history.md#v2.2.0) ，而且想要將應用程式提交至 Microsoft store，請至少更新為版本2.2.1。
* 已修正[Windows 應用程式認證套件](https://developer.microsoft.com/windows/downloads/app-certification-kit/)合規性問題。

## <a name="version-220-july-1-2020"></a>2020年7月1日 (版本 2.2.0) <a name="v2.2.0"></a>
* 全像攝影遠端播放播放機現在可以安裝在執行[Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)的電腦上，讓它可以串流到沉浸式耳機。
* 透過 SpatialInteractionSource，您現在可以透過「全像」遠端處理來支援[動態](motion-controllers.md)控制站，並可透過[SpatialInteractionSource.Controller](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)取得控制器特定的資料。
* 現在支援[SpatialStageFrameOfReference](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference) ，而且可以透過[SpatialStageFrameOfReference](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)來抓取目前的階段。 此外，您也可以透過 SpatialStageFrameOfReference 來要求新的階段[。 RequestNewStageAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)。
* 在舊版中，「全像攝影」遠端播放程式會在玩家端完整處理預測。 從版本2.2.0 開始，全像攝影遠端處理具有時間同步，而預測則是由遠端應用程式來完成。 在艱難的網路情況下，使用者應該也會獲得改良的全息影像穩定性。

## <a name="version-213-may-25-2020"></a>版本 2.1.3 (5 月25日，2020) <a name="v2.1.3"></a>
* 已變更[HolographicSpace CameraAdded](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.cameraadded?view=winrt-18362)事件的行為。 在先前的版本中，當透過[HolographicSpace](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createnextframe?view=winrt-18362#Windows_Graphics_Holographic_HolographicSpace_CreateNextFrame)建立下一個畫面格時，**不**保證新增的[HolographicCamera](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera?view=winrt-18362)也具有有效的[HolographicCameraPose](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose?view=winrt-18362) 。 從版本 2.1.3 [HolographicSpace](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.cameraadded?view=winrt-18362)開始，會與來自全像遠端播放程式的姿勢資料同步處理，而使用者可以預期在新增相機時，在下一個畫面上，該攝影機也會有有效的[HolographicCameraPose](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose?view=winrt-18362)可用。
* 已將**停用**的新增至 DepthBufferStreamResolution，可用來透過 RemoteContext.ConfigureDepthVideoStream 停用深度緩衝區串流。 請注意，如果使用[HolographicCameraRenderingParameters，CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer?view=winrt-18362#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)將會失敗，並*E_ILLEGAL_METHOD_CALL*。
* 全像攝影遠端播放程式的啟動畫面已重新設計，現在不會封鎖使用者的觀看。
* 穩定性改進和 bug 修正。

## <a name="version-212-april-5-2020"></a>版本 2.1.2 (2020 年4月5日) <a name="v2.1.2"></a>
* 已修正最新的全像攝影遠端播放程式與使用小於2.1.0 版本之遠端應用程式之間的音訊回溯相容性問題。
* 已修正未預期地關閉全像攝影遠端播放播放機的空間錨點問題。 此問題也會影響自訂播放機。

## <a name="version-211-march-20-2020"></a>2020年3月20日 (2.1.1 版) <a name="v2.1.1"></a>
* 已修正使用 AMD Gpu 時，遠端應用程式的影片編碼問題。
* 全像攝影遠端播放播放機效能改進。

## <a name="version-210-march-11-2020"></a>2020年3月11日 (版本 2.1.0) <a name="v2.1.0"></a>
* 已將網路傳輸切換為使用[RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) via UDP。 安全連線立即使用[SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) 。 請注意，全像之前發行的「全像攝影[」遠端處理](holographic-remoting-player.md)版本仍然相容。 若要從新的網路傳輸中獲益，全像攝影的遠端播放程式和遠端應用程式有問題，必須使用版本2.1.0。
* 已新增對[HolographicCameraRenderingParameters 的支援。 CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)。 

## <a name="version-2020-february-2-2020"></a>2020年2月2日 (版本2.0.20 版) <a name="v2.0.20"></a>
* 已修正導致當機的各種錯誤。

## <a name="version-2018-december-17-2019"></a>2019年12月17日 (版本2.0.18 版) <a name="v2.0.18"></a>
* 已新增對[HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration)的支援
* 已修正導致當機的各種錯誤。
* 已修正 HolographicCamera 要接受並顯示為 HolographicFrame 中新增的相機所需的 HolographicSpace CameraAdded 回呼的 bug。

## <a name="version-2016-november-11-2019"></a>2019年11月11日 (版本 2.0.16) <a name="2.0.16"></a>
* 已修正 QR 代碼追蹤中的鎖死。
* 已修正 unhandeled 例外狀況，因為在主執行緒中封鎖等候。

## <a name="version-2014-october-26-2019"></a>2019年10月 26 (版本2.0.14 版) <a name="v2.0.14"></a>
* 支援新的 PerceptionDevice Api (Windows 10 2019 年11月更新) 。
* 已修正導致 SpatialGestureRecognizer 無法觸發保存手勢事件的問題。
* 已修正使用 SpatialSurfaceObserver. SetBoundingVolume 時的執行緒問題。

## <a name="version-2012-october-18-2019"></a>2019年10月18日 (版本 2.0.12) <a name="v2.0.12"></a>
* 已修正使用 NavigationRail (X/Y/Z) 時的 SpatialGestureRecognizer 損毀。

## <a name="version-2010-october-10-2019"></a>2019年10月10日 (版本2.0.10 版) <a name="v2.0.10"></a>
* 已修正使用 VR 控制器的觸發程式按鈕時的損毀。 全像攝影的遠端處理並不完全支援控制器，如果與 HoloLens 2 配對，只有 [觸發程式] 按鈕和 [Windows] 按鈕才有作用。

## <a name="version-209-september-19-2019"></a>2019年9月19日 (版本 2.0.9) <a name="v2.0.9"></a>
* 已新增對[SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)的支援
* 已加入新介面 ```IPlayerContext2``` (由 ```PlayerContext```) 提供下列成員來執行：
  - [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)屬性。
* 已 ```Failed_RemoteFrameTooOld``` 將值新增至```BlitResult```
* 穩定性和可靠性的改進

## <a name="version-208-august-20-2019"></a>2019年8月20日 (版本 2.0.8) <a name="v2.0.8"></a>

* 已修正使用[IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2)做為參數呼叫[HolographicCameraRenderingParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer)時的損毀。
* 穩定性和可靠性的改進

## <a name="version-207-july-26-2019"></a>2019年7月26日 (版本 2.0.7) <a name="v2.0.7"></a>

* HoloLens 2 的第一個公開發行的全像攝影遠端功能。

## <a name="see-also"></a>另請參閱
* [撰寫自訂全像攝影遠端播放應用程式](holographic-remoting-create-player.md)
* [撰寫全像的遠端主機應用程式](holographic-remoting-create-host.md)
* [全像攝影遠端疑難排解和限制](holographic-remoting-troubleshooting.md)
* [全像攝影遠端軟體授權條款](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隱私權聲明](https://go.microsoft.com/fwlink/?LinkId=521839)
