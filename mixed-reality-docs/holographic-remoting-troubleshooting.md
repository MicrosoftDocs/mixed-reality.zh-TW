---
title: 全像攝影遠端疑難排解和限制
description: HoloLens 2 上全像攝影遠端處理的疑難排解步驟。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: Windows Mixed Reality，全息影像，全像攝影遠端，遠端轉譯，網路轉譯，HoloLens，遠端全息影像，疑難排解，協助
ms.openlocfilehash: fc379eb4ad849fb5b236b82719711b37fead8a68
ms.sourcegitcommit: 48456c607a2d0dcf035a77e8ba67615396b0a211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81484308"
---
# <a name="holographic-remoting-troubleshooting"></a>全像攝影遠端疑難排解

> [!IMPORTANT]
> 本指導方針專屬於 HoloLens 2 上的全像攝影遠端處理。

## <a name="spectre-mitigated-libraries-not-found"></a>找不到 Spectre 緩和的程式庫。

全像攝影遠端範例應用程式在發行設定中啟用了 Spectre 緩和措施（/Qspectre）。

如果您收到嚴重的連結器錯誤，指出無法開啟 ' vccorlib.h '，請確定您的 Visual Studio 工作負載包含 Spectre 緩和程式庫。 如需相關資訊，請參閱 https://aka.ms/Ofhn4c。

## <a name="limitations"></a>限制

使用 HoloLens 2 的全像的遠端處理時，目前**不**支援下列 api，除非另有指示，否則會引發 ```ERROR_NOT_SUPPORTED``` 錯誤：

[Windows.Graphics.Holographic](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [HolographicCamera.ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - 從版本[2.0.18 版](holographic-remoting-version-history.md#v2.0.18)開始支援
  - 在先前版本中，一律會引發錯誤。
* [HolographicCamera.IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [HolographicViewConfiguration.RequestRenderTargetSize](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - 不會失敗，但轉譯目標大小不會變更。
* [HolographicCameraPose.OverrideProjectionTransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [HolographicCameraPose.OverrideViewport](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [HolographicCameraPose.OverrideViewTransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - 不會失敗，但深度緩衝區將不會進行遠端處理。
  - 從版本[2.1.0](holographic-remoting-version-history.md#v2.1.0)開始支援
* [HolographicDisplay.TryGetViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - 查詢 HolographicViewConfigurationKind。 PhotoVideoCamera 一律會傳回 ```nullptr```。
  - 從版本[2.0.18 版](holographic-remoting-version-history.md#v2.0.18)開始支援
  - 在先前版本中，一律會引發錯誤。
* [HolographicSpace.CreateFramePresentationMonitor](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [HolographicDisplay.GetDefault](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - 如果在建立連接之前呼叫，將會報告錯誤。


[Windows.Perception.Spatial](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [Spatiallocation. AbsoluteAngularAcceleration](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [Spatiallocation. AbsoluteAngularAccelerationAxisAngle](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [Spatiallocation. AbsoluteAngularVelocity](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [Spatiallocation. AbsoluteAngularVelocityAxisAngle](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [Spatiallocation. AbsoluteLinearAcceleration](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [Spatiallocation. AbsoluteLinearVelocity](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [SpatialStageFrameOfReference。目前](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - 一律會傳回 ```nullptr```。
* [SpatialStageFrameOfReference.RequestNewStageAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [SpatialAnchor.RemovedByUser](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [SpatialAnchorExporter.GetDefault](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - 從版本[2.0.9](holographic-remoting-version-history.md#v2.0.9)開始支援。 
  - 在先前版本中，一律會傳回 ```nullptr```。 
* [SpatialAnchorExporter.RequestAccessAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - 從版本[2.0.9](holographic-remoting-version-history.md#v2.0.9)開始支援。 
  - 在先前的版本中，非同步作業一律以 ```SpatialPerceptionAccessStatus.DeniedBySystem```完成。
* [SpatialAnchorTransferManager.RequestAccessAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - 非同步作業一律會以 ```SpatialPerceptionAccessStatus.DeniedBySystem```完成。
* [SpatialAnchorTransferManager.TryExportAnchorsAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - 非同步作業一律會以 ```false```完成。
* [SpatialAnchorTransferManager.TryImportAnchorsAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - 非同步作業一律會以 ```nullptr```完成。

[Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [SpatialInteractionSource.TryCreateHandMeshObserver](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [SpatialInteractionSource.TryCreateHandMeshObserverAsync](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [SpatialInteractionSource 控制器](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)

[Windows.Perception.Spatial.Preview](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [SpatialGraphInteropPreview.CreateLocatorForNode](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [SpatialGraphInteropPreview.TryCreateFrameOfReference](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a>另請參閱
* [全像遠端版本歷程記錄](holographic-remoting-version-history.md)
* [撰寫全像攝影遠端應用程式](holographic-remoting-create-host.md)
* [撰寫自訂的全像遠端播放播放機應用程式](holographic-remoting-create-player.md)
* [全像攝影遠端軟體授權條款](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隱私權聲明](https://go.microsoft.com/fwlink/?LinkId=521839)
