---
title: 全像攝影遠端疑難排解和限制
description: HoloLens 2 上全像攝影遠端處理的疑難排解步驟。
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 10/28/2019
ms.topic: article
keywords: Windows Mixed Reality，全息影像，全像攝影遠端，遠端轉譯，網路轉譯，HoloLens，遠端全息影像，疑難排解，協助
ms.openlocfilehash: 7b438d9169c9306e0056655e561c04b62b1662cf
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434241"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="be093-104">全像攝影遠端疑難排解</span><span class="sxs-lookup"><span data-stu-id="be093-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="be093-105">本指導方針專屬於 HoloLens 2 上的全像攝影遠端處理。</span><span class="sxs-lookup"><span data-stu-id="be093-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="be093-106">找不到 Spectre 緩和的程式庫。</span><span class="sxs-lookup"><span data-stu-id="be093-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="be093-107">全像攝影遠端範例應用程式在發行設定中啟用了 Spectre 緩和措施（/Qspectre）。</span><span class="sxs-lookup"><span data-stu-id="be093-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="be093-108">如果您收到嚴重的連結器錯誤，指出無法開啟 ' vccorlib.h '，請確定您的 Visual Studio 工作負載包含 Spectre 緩和程式庫。</span><span class="sxs-lookup"><span data-stu-id="be093-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="be093-109">如需相關資訊，請參閱 https://aka.ms/Ofhn4c 。</span><span class="sxs-lookup"><span data-stu-id="be093-109">See https://aka.ms/Ofhn4c for more information.</span></span>

## <a name="limitations"></a><span data-ttu-id="be093-110">限制</span><span class="sxs-lookup"><span data-stu-id="be093-110">Limitations</span></span>

<span data-ttu-id="be093-111">使用 HoloLens 2 的全像的遠端處理時，目前**不**支援下列 api，除非另有指示，否則會引發 ```ERROR_NOT_SUPPORTED``` 錯誤：</span><span class="sxs-lookup"><span data-stu-id="be093-111">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="be093-112">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="be093-112">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="be093-113">HolographicCamera.ViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="be093-113">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
* [<span data-ttu-id="be093-114">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="be093-114">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="be093-115">HolographicCameraPose.OverrideViewport</span><span class="sxs-lookup"><span data-stu-id="be093-115">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="be093-116">HolographicCameraPose.OverrideViewTransform</span><span class="sxs-lookup"><span data-stu-id="be093-116">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [<span data-ttu-id="be093-117">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="be093-117">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="be093-118">不會失敗，但深度緩衝區將不會進行遠端處理。</span><span class="sxs-lookup"><span data-stu-id="be093-118">Does not fail but depth buffer will not be remoted.</span></span>
* [<span data-ttu-id="be093-119">HolographicDisplay.TryGetViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="be093-119">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
* [<span data-ttu-id="be093-120">HolographicSpace.CreateFramePresentationMonitor</span><span class="sxs-lookup"><span data-stu-id="be093-120">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)

[<span data-ttu-id="be093-121">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="be093-121">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="be093-122">Spatiallocation. AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="be093-122">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="be093-123">Spatiallocation. AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="be093-123">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="be093-124">Spatiallocation. AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="be093-124">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="be093-125">Spatiallocation. AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="be093-125">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="be093-126">Spatiallocation. AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="be093-126">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="be093-127">Spatiallocation. AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="be093-127">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="be093-128">SpatialStageFrameOfReference。目前</span><span class="sxs-lookup"><span data-stu-id="be093-128">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="be093-129">一律會傳回 ```nullptr```。</span><span class="sxs-lookup"><span data-stu-id="be093-129">Always returns ```nullptr```.</span></span>
* [<span data-ttu-id="be093-130">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="be093-130">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [<span data-ttu-id="be093-131">SpatialAnchor.RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="be093-131">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="be093-132">SpatialAnchorExporter.GetDefault</span><span class="sxs-lookup"><span data-stu-id="be093-132">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="be093-133">從版本[2.0.9](holographic-remoting-version-history.md#v2.0.9)開始支援。</span><span class="sxs-lookup"><span data-stu-id="be093-133">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="be093-134">在先前版本中，一律會傳回 ```nullptr```。</span><span class="sxs-lookup"><span data-stu-id="be093-134">On previous versions always returns ```nullptr```.</span></span> 
* [<span data-ttu-id="be093-135">SpatialAnchorExporter.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="be093-135">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="be093-136">從版本[2.0.9](holographic-remoting-version-history.md#v2.0.9)開始支援。</span><span class="sxs-lookup"><span data-stu-id="be093-136">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="be093-137">在先前的版本中，非同步作業一律以 ```SpatialPerceptionAccessStatus.DeniedBySystem```完成。</span><span class="sxs-lookup"><span data-stu-id="be093-137">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="be093-138">SpatialAnchorTransferManager.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="be093-138">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="be093-139">非同步作業一律會以 ```SpatialPerceptionAccessStatus.DeniedBySystem```完成。</span><span class="sxs-lookup"><span data-stu-id="be093-139">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="be093-140">SpatialAnchorTransferManager.TryExportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="be093-140">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="be093-141">非同步作業一律會以 ```false```完成。</span><span class="sxs-lookup"><span data-stu-id="be093-141">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="be093-142">SpatialAnchorTransferManager.TryImportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="be093-142">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="be093-143">非同步作業一律會以 ```nullptr```完成。</span><span class="sxs-lookup"><span data-stu-id="be093-143">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="be093-144">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="be093-144">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="be093-145">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="be093-145">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="be093-146">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="be093-146">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[<span data-ttu-id="be093-147">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="be093-147">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="be093-148">SpatialGraphInteropPreview.CreateLocatorForNode</span><span class="sxs-lookup"><span data-stu-id="be093-148">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="be093-149">SpatialGraphInteropPreview.TryCreateFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="be093-149">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)
* [<span data-ttu-id="be093-150">SpatialInteractionSource 控制器</span><span class="sxs-lookup"><span data-stu-id="be093-150">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)

## <a name="see-also"></a><span data-ttu-id="be093-151">請參閱</span><span class="sxs-lookup"><span data-stu-id="be093-151">See Also</span></span>
* [<span data-ttu-id="be093-152">全像遠端版本歷程記錄</span><span class="sxs-lookup"><span data-stu-id="be093-152">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="be093-153">撰寫全像的遠端主機應用程式</span><span class="sxs-lookup"><span data-stu-id="be093-153">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="be093-154">撰寫自訂的全像遠端播放播放機應用程式</span><span class="sxs-lookup"><span data-stu-id="be093-154">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="be093-155">全像攝影遠端軟體授權條款</span><span class="sxs-lookup"><span data-stu-id="be093-155">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="be093-156">Microsoft 隱私權聲明</span><span class="sxs-lookup"><span data-stu-id="be093-156">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
