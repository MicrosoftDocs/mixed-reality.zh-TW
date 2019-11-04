---
title: 全像遠端版本歷程記錄
description: HoloLens 2 上全像攝影遠端處理的版本歷程記錄。
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens、遠端、全像攝影遠端
ms.openlocfilehash: 75e7c276560b4efbbdcbf2ea7579ed5ad7aadb4d
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439229"
---
# <a name="holographic-remoting-version-history"></a>全像遠端版本歷程記錄

> [!IMPORTANT]
> 本指導方針專屬於 HoloLens 2 上的全像攝影遠端處理。

## 版本2.0.14 版（2019年10月26日）<a name="v2.0.14"></a>
* 支援新的 PerceptionDevice Api （Windows 10 2019 年11月更新）。
* 已修正導致 SpatialGestureRecognizer 無法觸發保存手勢事件的問題。
* 已修正使用 SpatialSurfaceObserver. SetBoundingVolume 時的 theading 問題。

## 版本2.0.12 （2019年10月18日）<a name="v2.0.12"></a>
* 已修正使用 NavigationRail （X/Y/Z）時的 SpatialGestureRecognizer 損毀。

## 版本2.0.10 版（2019年10月10日）<a name="v2.0.10"></a>
* 已修正使用 VR 控制器的觸發程式按鈕時的損毀。 全像攝影的遠端處理並不完全支援控制器，如果與 HoloLens 2 配對，只有 [觸發程式] 按鈕和 [Windows] 按鈕才有作用。

## 版本2.0.9 （2019年9月19日）<a name="v2.0.9"></a>
* 已新增對[SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)的支援
* 已新增介面 ```IPlayerContext2``` （由 ```PlayerContext```執行），提供下列成員：
  - [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)屬性。
* 已將 ```Failed_RemoteFrameTooOld``` 值新增至 ```BlitResult```
* 穩定性和可靠性的改進

## 版本2.0.8 （2019年8月20日）<a name="v2.0.8"></a>

* 已修正使用[IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2)做為參數呼叫[HolographicCameraRenderingParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer)時的損毀。
* 穩定性和可靠性的改進

## 版本2.0.7 （2019年7月26日）<a name="v2.0.7"></a>

* HoloLens 2 的第一個公開發行的全像攝影遠端功能。

## <a name="see-also"></a>請參閱
* [撰寫自訂的全像遠端播放播放機應用程式](holographic-remoting-create-player.md)
* [撰寫全像的遠端主機應用程式](holographic-remoting-create-host.md)
* [全像攝影遠端疑難排解和限制](holographic-remoting-troubleshooting.md)
* [全像攝影遠端軟體授權條款](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隱私權聲明](https://go.microsoft.com/fwlink/?LinkId=521839)
