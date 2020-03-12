---
title: 全像攝影遠端疑難排解和限制
description: HoloLens 2 上全像攝影遠端處理的疑難排解步驟。
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: Windows Mixed Reality，全息影像，全像攝影遠端，遠端轉譯，網路轉譯，HoloLens，遠端全息影像，疑難排解，協助
ms.openlocfilehash: 79258832d29741c56a1e7e89baeb7d728c806dd1
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2020
ms.locfileid: "79092365"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="2cf06-104">全像攝影遠端疑難排解</span><span class="sxs-lookup"><span data-stu-id="2cf06-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2cf06-105">本指導方針專屬於 HoloLens 2 上的全像攝影遠端處理。</span><span class="sxs-lookup"><span data-stu-id="2cf06-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="2cf06-106">找不到 Spectre 緩和的程式庫。</span><span class="sxs-lookup"><span data-stu-id="2cf06-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="2cf06-107">全像攝影遠端範例應用程式在發行設定中啟用了 Spectre 緩和措施（/Qspectre）。</span><span class="sxs-lookup"><span data-stu-id="2cf06-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="2cf06-108">如果您收到嚴重的連結器錯誤，指出無法開啟 ' vccorlib.h '，請確定您的 Visual Studio 工作負載包含 Spectre 緩和程式庫。</span><span class="sxs-lookup"><span data-stu-id="2cf06-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="2cf06-109">如需相關資訊，請參閱 https://aka.ms/Ofhn4c。</span><span class="sxs-lookup"><span data-stu-id="2cf06-109">See https://aka.ms/Ofhn4c for more information.</span></span>

## <a name="limitations"></a><span data-ttu-id="2cf06-110">限制</span><span class="sxs-lookup"><span data-stu-id="2cf06-110">Limitations</span></span>

<span data-ttu-id="2cf06-111">使用 HoloLens 2 的全像的遠端處理時，目前**不**支援下列 api，除非另有指示，否則會引發 ```ERROR_NOT_SUPPORTED``` 錯誤：</span><span class="sxs-lookup"><span data-stu-id="2cf06-111">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="2cf06-112">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="2cf06-112">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="2cf06-113">HolographicCamera.ViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="2cf06-113">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - <span data-ttu-id="2cf06-114">從版本[2.0.18 版](holographic-remoting-version-history.md#v2.0.18)開始支援</span><span class="sxs-lookup"><span data-stu-id="2cf06-114">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="2cf06-115">在先前版本中，一律會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="2cf06-115">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="2cf06-116">HolographicViewConfiguration.RequestRenderTargetSize</span><span class="sxs-lookup"><span data-stu-id="2cf06-116">HolographicViewConfiguration.RequestRenderTargetSize</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - <span data-ttu-id="2cf06-117">不會失敗，但轉譯目標大小不會變更。</span><span class="sxs-lookup"><span data-stu-id="2cf06-117">Does not fail, but the render target size will not be changed.</span></span>
* [<span data-ttu-id="2cf06-118">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="2cf06-118">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="2cf06-119">HolographicCameraPose.OverrideViewport</span><span class="sxs-lookup"><span data-stu-id="2cf06-119">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="2cf06-120">HolographicCameraPose.OverrideViewTransform</span><span class="sxs-lookup"><span data-stu-id="2cf06-120">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [<span data-ttu-id="2cf06-121">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="2cf06-121">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="2cf06-122">不會失敗，但深度緩衝區將不會進行遠端處理。</span><span class="sxs-lookup"><span data-stu-id="2cf06-122">Does not fail but depth buffer will not be remoted.</span></span>
  - <span data-ttu-id="2cf06-123">從版本[2.1.0](holographic-remoting-version-history.md#v2.1.0)開始支援</span><span class="sxs-lookup"><span data-stu-id="2cf06-123">Supported starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0)</span></span>
* [<span data-ttu-id="2cf06-124">HolographicDisplay.TryGetViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="2cf06-124">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - <span data-ttu-id="2cf06-125">查詢 HolographicViewConfigurationKind。 PhotoVideoCamera 一律會傳回 ```nullptr```。</span><span class="sxs-lookup"><span data-stu-id="2cf06-125">Querying HolographicViewConfigurationKind.PhotoVideoCamera will always return a ```nullptr```.</span></span>
  - <span data-ttu-id="2cf06-126">從版本[2.0.18 版](holographic-remoting-version-history.md#v2.0.18)開始支援</span><span class="sxs-lookup"><span data-stu-id="2cf06-126">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="2cf06-127">在先前版本中，一律會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="2cf06-127">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="2cf06-128">HolographicSpace.CreateFramePresentationMonitor</span><span class="sxs-lookup"><span data-stu-id="2cf06-128">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [<span data-ttu-id="2cf06-129">HolographicDisplay.GetDefault</span><span class="sxs-lookup"><span data-stu-id="2cf06-129">HolographicDisplay.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - <span data-ttu-id="2cf06-130">如果在建立連接之前呼叫，將會報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="2cf06-130">Will report an error if called before a connection was established.</span></span>


[<span data-ttu-id="2cf06-131">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="2cf06-131">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="2cf06-132">Spatiallocation. AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="2cf06-132">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="2cf06-133">Spatiallocation. AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="2cf06-133">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="2cf06-134">Spatiallocation. AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="2cf06-134">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="2cf06-135">Spatiallocation. AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="2cf06-135">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="2cf06-136">Spatiallocation. AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="2cf06-136">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="2cf06-137">Spatiallocation. AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="2cf06-137">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="2cf06-138">SpatialStageFrameOfReference。目前</span><span class="sxs-lookup"><span data-stu-id="2cf06-138">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="2cf06-139">一律會傳回 ```nullptr```。</span><span class="sxs-lookup"><span data-stu-id="2cf06-139">Always returns ```nullptr```.</span></span>
* [<span data-ttu-id="2cf06-140">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="2cf06-140">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [<span data-ttu-id="2cf06-141">SpatialAnchor.RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="2cf06-141">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="2cf06-142">SpatialAnchorExporter.GetDefault</span><span class="sxs-lookup"><span data-stu-id="2cf06-142">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="2cf06-143">從版本[2.0.9](holographic-remoting-version-history.md#v2.0.9)開始支援。</span><span class="sxs-lookup"><span data-stu-id="2cf06-143">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="2cf06-144">在先前版本中，一律會傳回 ```nullptr```。</span><span class="sxs-lookup"><span data-stu-id="2cf06-144">On previous versions always returns ```nullptr```.</span></span> 
* [<span data-ttu-id="2cf06-145">SpatialAnchorExporter.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="2cf06-145">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="2cf06-146">從版本[2.0.9](holographic-remoting-version-history.md#v2.0.9)開始支援。</span><span class="sxs-lookup"><span data-stu-id="2cf06-146">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="2cf06-147">在先前的版本中，非同步作業一律以 ```SpatialPerceptionAccessStatus.DeniedBySystem```完成。</span><span class="sxs-lookup"><span data-stu-id="2cf06-147">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="2cf06-148">SpatialAnchorTransferManager.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="2cf06-148">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="2cf06-149">非同步作業一律會以 ```SpatialPerceptionAccessStatus.DeniedBySystem```完成。</span><span class="sxs-lookup"><span data-stu-id="2cf06-149">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="2cf06-150">SpatialAnchorTransferManager.TryExportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="2cf06-150">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="2cf06-151">非同步作業一律會以 ```false```完成。</span><span class="sxs-lookup"><span data-stu-id="2cf06-151">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="2cf06-152">SpatialAnchorTransferManager.TryImportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="2cf06-152">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="2cf06-153">非同步作業一律會以 ```nullptr```完成。</span><span class="sxs-lookup"><span data-stu-id="2cf06-153">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="2cf06-154">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="2cf06-154">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="2cf06-155">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="2cf06-155">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="2cf06-156">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="2cf06-156">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[<span data-ttu-id="2cf06-157">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="2cf06-157">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="2cf06-158">SpatialGraphInteropPreview.CreateLocatorForNode</span><span class="sxs-lookup"><span data-stu-id="2cf06-158">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="2cf06-159">SpatialGraphInteropPreview.TryCreateFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="2cf06-159">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)
* [<span data-ttu-id="2cf06-160">SpatialInteractionSource 控制器</span><span class="sxs-lookup"><span data-stu-id="2cf06-160">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)

## <a name="see-also"></a><span data-ttu-id="2cf06-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2cf06-161">See Also</span></span>
* [<span data-ttu-id="2cf06-162">全像遠端版本歷程記錄</span><span class="sxs-lookup"><span data-stu-id="2cf06-162">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="2cf06-163">撰寫全像攝影遠端應用程式</span><span class="sxs-lookup"><span data-stu-id="2cf06-163">Writing a Holographic Remoting remote app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="2cf06-164">撰寫自訂的全像遠端播放播放機應用程式</span><span class="sxs-lookup"><span data-stu-id="2cf06-164">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="2cf06-165">全像攝影遠端軟體授權條款</span><span class="sxs-lookup"><span data-stu-id="2cf06-165">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="2cf06-166">Microsoft 隱私權聲明</span><span class="sxs-lookup"><span data-stu-id="2cf06-166">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
