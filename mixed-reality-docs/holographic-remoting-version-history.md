---
title: 全像遠端版本歷程記錄
description: HoloLens 2 上全像攝影遠端處理的版本歷程記錄。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens、遠端、全像攝影遠端
ms.openlocfilehash: 5ba3aaa8874dea4418114b331d3d99fc977e982c
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278196"
---
# <a name="holographic-remoting-version-history"></a>全像遠端版本歷程記錄

> [!IMPORTANT]
> 本指導方針專屬於 HoloLens 2 上的全像攝影遠端處理。

## <a name="version-210-march-11-2020"></a>版本2.1.0 （2020年3月11日）<a name="v2.1.0"></a>
* 已將網路傳輸切換為使用[RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) via UDP。 安全連線立即使用[SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) 。 請注意，全像之前發行的「全像攝影[」遠端處理](holographic-remoting-player.md)版本仍然相容。 若要從新的網路傳輸中獲益，全像攝影的遠端播放程式和遠端應用程式有問題，必須使用版本2.1.0。
* 已新增對[HolographicCameraRenderingParameters 的支援。 CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)。 

## <a name="version-2020-february-2-2020"></a>版本2.0.20 版（2020年2月2日）<a name="v2.0.20"></a>
* 已修正導致當機的各種錯誤。

## <a name="version-2018-december-17-2019"></a>版本2.0.18 版（2019年12月17日）<a name="v2.0.18"></a>
* 已新增對[HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration)的支援
* 已修正導致當機的各種錯誤。
* 已修正 HolographicCamera 要接受並顯示為 HoloraphicFrame 中新增的相機所需的 HolographicSpace CameraAdded 回呼的 bug。

## <a name="version-2016-november-11-2019"></a>版本2.0.16 （2019年11月11日）<a name="2.0.16"></a>
* 已修正 QR 代碼追蹤中的鎖死。
* 已修正 unhandeled 例外狀況，因為在主執行緒中封鎖等候。

## <a name="version-2014-october-26-2019"></a>版本2.0.14 版（2019年10月26日）<a name="v2.0.14"></a>
* 支援新的 PerceptionDevice Api （Windows 10 2019 年11月更新）。
* 已修正導致 SpatialGestureRecognizer 無法觸發保存手勢事件的問題。
* 已修正使用 SpatialSurfaceObserver. SetBoundingVolume 時的執行緒問題。

## <a name="version-2012-october-18-2019"></a>版本2.0.12 （2019年10月18日）<a name="v2.0.12"></a>
* 已修正使用 NavigationRail （X/Y/Z）時的 SpatialGestureRecognizer 損毀。

## <a name="version-2010-october-10-2019"></a>版本2.0.10 版（2019年10月10日）<a name="v2.0.10"></a>
* 已修正使用 VR 控制器的觸發程式按鈕時的損毀。 全像攝影的遠端處理並不完全支援控制器，如果與 HoloLens 2 配對，只有 [觸發程式] 按鈕和 [Windows] 按鈕才有作用。

## <a name="version-209-september-19-2019"></a>版本2.0.9 （2019年9月19日）<a name="v2.0.9"></a>
* 已新增對[SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)的支援
* 已新增介面 ```IPlayerContext2``` （由 ```PlayerContext```執行），提供下列成員：
  - [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)屬性。
* 已將 ```Failed_RemoteFrameTooOld``` 值新增至 ```BlitResult```
* 穩定性和可靠性的改進

## <a name="version-208-august-20-2019"></a>版本2.0.8 （2019年8月20日）<a name="v2.0.8"></a>

* 已修正使用[IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2)做為參數呼叫[HolographicCameraRenderingParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer)時的損毀。
* 穩定性和可靠性的改進

## <a name="version-207-july-26-2019"></a>版本2.0.7 （2019年7月26日）<a name="v2.0.7"></a>

* HoloLens 2 的第一個公開發行的全像攝影遠端功能。

## <a name="see-also"></a>另請參閱
* [撰寫自訂的全像遠端播放播放機應用程式](holographic-remoting-create-player.md)
* [撰寫全像的遠端主機應用程式](holographic-remoting-create-host.md)
* [全像攝影遠端疑難排解和限制](holographic-remoting-troubleshooting.md)
* [全像攝影遠端軟體授權條款](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隱私權聲明](https://go.microsoft.com/fwlink/?LinkId=521839)
