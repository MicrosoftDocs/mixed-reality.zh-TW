---
title: 全像攝影遠端疑難排解和限制
description: HoloLens 2 上全像攝影遠端處理的疑難排解步驟。
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 08/01/2019
ms.topic: article
keywords: Windows Mixed Reality, 全息影像, 全像攝影遠端, 遠端轉譯, 網路轉譯, HoloLens, 遠端全息影像, 疑難排解, 協助
ms.openlocfilehash: 86b6979dbfc9b514b3af13ebdcc3d3ece17e6335
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718142"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="c47ea-104">全像攝影遠端疑難排解</span><span class="sxs-lookup"><span data-stu-id="c47ea-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c47ea-105">本指導方針專屬於 HoloLens 2 上的全像攝影遠端處理。</span><span class="sxs-lookup"><span data-stu-id="c47ea-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="c47ea-106">找不到 Spectre 緩和的程式庫。</span><span class="sxs-lookup"><span data-stu-id="c47ea-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="c47ea-107">全像攝影遠端範例應用程式在發行設定中啟用了 Spectre 緩和措施 (/Qspectre)。</span><span class="sxs-lookup"><span data-stu-id="c47ea-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="c47ea-108">如果您收到嚴重的連結器錯誤, 指出無法開啟 ' vccorlib.h ', 請確定您的 Visual Studio 工作負載包含 Spectre 緩和程式庫。</span><span class="sxs-lookup"><span data-stu-id="c47ea-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="c47ea-109">如需相關資訊，請參閱 https://aka.ms/Ofhn4c 。</span><span class="sxs-lookup"><span data-stu-id="c47ea-109">See https://aka.ms/Ofhn4c for more information.</span></span>

# <a name="limitations"></a><span data-ttu-id="c47ea-110">限制</span><span class="sxs-lookup"><span data-stu-id="c47ea-110">Limitations</span></span>

<span data-ttu-id="c47ea-111">使用 HoloLens 2 的全像的遠端處理時, 目前**不**支援下列 api, 除非```ERROR_NOT_SUPPORTED```另有指示, 否則會引發錯誤:</span><span class="sxs-lookup"><span data-stu-id="c47ea-111">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="c47ea-112">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="c47ea-112">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="c47ea-113">HolographicCamera.ViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="c47ea-113">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
* [<span data-ttu-id="c47ea-114">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="c47ea-114">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="c47ea-115">HolographicCameraPose.OverrideViewport</span><span class="sxs-lookup"><span data-stu-id="c47ea-115">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="c47ea-116">HolographicCameraPose.OverrideViewTransform</span><span class="sxs-lookup"><span data-stu-id="c47ea-116">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* <span data-ttu-id="c47ea-117">[HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) -不會失敗, 但深度緩衝區將不會進行遠端處理。</span><span class="sxs-lookup"><span data-stu-id="c47ea-117">[HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) - Does not fail but depth buffer will not be remoted.</span></span>
* [<span data-ttu-id="c47ea-118">HolographicDisplay.TryGetViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="c47ea-118">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
* [<span data-ttu-id="c47ea-119">HolographicSpace.CreateFramePresentationMonitor</span><span class="sxs-lookup"><span data-stu-id="c47ea-119">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)

[<span data-ttu-id="c47ea-120">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="c47ea-120">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="c47ea-121">Spatiallocation. AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="c47ea-121">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="c47ea-122">Spatiallocation. AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="c47ea-122">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="c47ea-123">Spatiallocation. AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="c47ea-123">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="c47ea-124">Spatiallocation. AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="c47ea-124">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="c47ea-125">Spatiallocation. AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="c47ea-125">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/is-is/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="c47ea-126">Spatiallocation. AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="c47ea-126">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* <span data-ttu-id="c47ea-127">[SpatialStageFrameOfReference。目前](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)-一律```nullptr```會傳回。</span><span class="sxs-lookup"><span data-stu-id="c47ea-127">[SpatialStageFrameOfReference.Current](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialstageframeofreference.current) - Always returns ```nullptr```.</span></span>
* [<span data-ttu-id="c47ea-128">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="c47ea-128">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [<span data-ttu-id="c47ea-129">SpatialAnchor.RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="c47ea-129">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* <span data-ttu-id="c47ea-130">[SpatialAnchorExporter. GetDefault](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
) - ```nullptr```一律會傳回。</span><span class="sxs-lookup"><span data-stu-id="c47ea-130">[SpatialAnchorExporter.GetDefault](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
) - Always returns ```nullptr```.</span></span>
* <span data-ttu-id="c47ea-131">[SpatialAnchorExporter。 RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
) -非同步作業一律使用```SpatialPerceptionAccessStatus.DeniedBySystem```完成。</span><span class="sxs-lookup"><span data-stu-id="c47ea-131">[SpatialAnchorExporter.RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
) - Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* <span data-ttu-id="c47ea-132">[SpatialAnchorTransferManager。 RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync) -非同步作業一律使用```SpatialPerceptionAccessStatus.DeniedBySystem```完成。</span><span class="sxs-lookup"><span data-stu-id="c47ea-132">[SpatialAnchorTransferManager.RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync) - Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* <span data-ttu-id="c47ea-133">[SpatialAnchorTransferManager。 TryExportAnchorsAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_) -非同步作業一律使用```false```完成。</span><span class="sxs-lookup"><span data-stu-id="c47ea-133">[SpatialAnchorTransferManager.TryExportAnchorsAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_) - Async operation always completes with ```false```.</span></span>
* <span data-ttu-id="c47ea-134">[SpatialAnchorTransferManager。 TryImportAnchorsAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
) -非同步作業一律使用```nullptr```完成。</span><span class="sxs-lookup"><span data-stu-id="c47ea-134">[SpatialAnchorTransferManager.TryImportAnchorsAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
) - Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="c47ea-135">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="c47ea-135">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="c47ea-136">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="c47ea-136">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="c47ea-137">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="c47ea-137">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[<span data-ttu-id="c47ea-138">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="c47ea-138">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="c47ea-139">SpatialGraphInteropPreview.CreateLocatorForNode</span><span class="sxs-lookup"><span data-stu-id="c47ea-139">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="c47ea-140">SpatialGraphInteropPreview.TryCreateFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="c47ea-140">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a><span data-ttu-id="c47ea-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c47ea-141">See Also</span></span>
* [<span data-ttu-id="c47ea-142">撰寫全像的遠端主機應用程式</span><span class="sxs-lookup"><span data-stu-id="c47ea-142">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="c47ea-143">撰寫自訂的全像遠端播放播放機應用程式</span><span class="sxs-lookup"><span data-stu-id="c47ea-143">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="c47ea-144">全像攝影遠端軟體授權條款</span><span class="sxs-lookup"><span data-stu-id="c47ea-144">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="c47ea-145">Microsoft 隱私權聲明</span><span class="sxs-lookup"><span data-stu-id="c47ea-145">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)