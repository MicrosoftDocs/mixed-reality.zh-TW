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
# <a name="holographic-remoting-version-history"></a><span data-ttu-id="991a3-104">全像遠端版本歷程記錄</span><span class="sxs-lookup"><span data-stu-id="991a3-104">Holographic Remoting Version History</span></span>

> [!IMPORTANT]
> <span data-ttu-id="991a3-105">本指導方針專屬於 HoloLens 2 上的全像攝影遠端處理。</span><span class="sxs-lookup"><span data-stu-id="991a3-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <span data-ttu-id="991a3-106">版本2.0.14 版（2019年10月26日）<a name="v2.0.14"></a></span><span class="sxs-lookup"><span data-stu-id="991a3-106">Version 2.0.14 (October 26, 2019) <a name="v2.0.14"></a></span></span>
* <span data-ttu-id="991a3-107">支援新的 PerceptionDevice Api （Windows 10 2019 年11月更新）。</span><span class="sxs-lookup"><span data-stu-id="991a3-107">Support for new PerceptionDevice APIs (Windows 10 November 2019 Update).</span></span>
* <span data-ttu-id="991a3-108">已修正導致 SpatialGestureRecognizer 無法觸發保存手勢事件的問題。</span><span class="sxs-lookup"><span data-stu-id="991a3-108">Fixed issue which prevent hold gesture events being triggered by SpatialGestureRecognizer.</span></span>
* <span data-ttu-id="991a3-109">已修正使用 SpatialSurfaceObserver. SetBoundingVolume 時的 theading 問題。</span><span class="sxs-lookup"><span data-stu-id="991a3-109">Fixed theading issue when using SpatialSurfaceObserver.SetBoundingVolume.</span></span>

## <span data-ttu-id="991a3-110">版本2.0.12 （2019年10月18日）<a name="v2.0.12"></a></span><span class="sxs-lookup"><span data-stu-id="991a3-110">Version 2.0.12 (October 18, 2019) <a name="v2.0.12"></a></span></span>
* <span data-ttu-id="991a3-111">已修正使用 NavigationRail （X/Y/Z）時的 SpatialGestureRecognizer 損毀。</span><span class="sxs-lookup"><span data-stu-id="991a3-111">Fixed crash in SpatialGestureRecognizer when using NavigationRail(X/Y/Z).</span></span>

## <span data-ttu-id="991a3-112">版本2.0.10 版（2019年10月10日）<a name="v2.0.10"></a></span><span class="sxs-lookup"><span data-stu-id="991a3-112">Version 2.0.10 (October 10, 2019) <a name="v2.0.10"></a></span></span>
* <span data-ttu-id="991a3-113">已修正使用 VR 控制器的觸發程式按鈕時的損毀。</span><span class="sxs-lookup"><span data-stu-id="991a3-113">Fixed crash when using trigger button of VR controllers.</span></span> <span data-ttu-id="991a3-114">全像攝影的遠端處理並不完全支援控制器，如果與 HoloLens 2 配對，只有 [觸發程式] 按鈕和 [Windows] 按鈕才有作用。</span><span class="sxs-lookup"><span data-stu-id="991a3-114">Holographic Remoting does not fully support controllers, only the trigger button and the Windows button are working if paired with HoloLens 2.</span></span>

## <span data-ttu-id="991a3-115">版本2.0.9 （2019年9月19日）<a name="v2.0.9"></a></span><span class="sxs-lookup"><span data-stu-id="991a3-115">Version 2.0.9 (September 19, 2019) <a name="v2.0.9"></a></span></span>
* <span data-ttu-id="991a3-116">已新增對[SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)的支援</span><span class="sxs-lookup"><span data-stu-id="991a3-116">Added support for [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span></span>
* <span data-ttu-id="991a3-117">已新增介面 ```IPlayerContext2``` （由 ```PlayerContext```執行），提供下列成員：</span><span class="sxs-lookup"><span data-stu-id="991a3-117">Added new interface ```IPlayerContext2``` (implemented by ```PlayerContext```) providing the following members:</span></span>
  - <span data-ttu-id="991a3-118">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)屬性。</span><span class="sxs-lookup"><span data-stu-id="991a3-118">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  property.</span></span>
* <span data-ttu-id="991a3-119">已將 ```Failed_RemoteFrameTooOld``` 值新增至 ```BlitResult```</span><span class="sxs-lookup"><span data-stu-id="991a3-119">Added ```Failed_RemoteFrameTooOld``` value to ```BlitResult```</span></span>
* <span data-ttu-id="991a3-120">穩定性和可靠性的改進</span><span class="sxs-lookup"><span data-stu-id="991a3-120">Stability and reliability improvements</span></span>

## <span data-ttu-id="991a3-121">版本2.0.8 （2019年8月20日）<a name="v2.0.8"></a></span><span class="sxs-lookup"><span data-stu-id="991a3-121">Version 2.0.8 (August 20, 2019) <a name="v2.0.8"></a></span></span>

* <span data-ttu-id="991a3-122">已修正使用[IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2)做為參數呼叫[HolographicCameraRenderingParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer)時的損毀。</span><span class="sxs-lookup"><span data-stu-id="991a3-122">Fixed crash when calling [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) with a [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as parameter.</span></span>
* <span data-ttu-id="991a3-123">穩定性和可靠性的改進</span><span class="sxs-lookup"><span data-stu-id="991a3-123">Stability and reliability improvements</span></span>

## <span data-ttu-id="991a3-124">版本2.0.7 （2019年7月26日）<a name="v2.0.7"></a></span><span class="sxs-lookup"><span data-stu-id="991a3-124">Version 2.0.7 (July 26, 2019) <a name="v2.0.7"></a></span></span>

* <span data-ttu-id="991a3-125">HoloLens 2 的第一個公開發行的全像攝影遠端功能。</span><span class="sxs-lookup"><span data-stu-id="991a3-125">First public release of Holographic Remoting for HoloLens 2.</span></span>

## <a name="see-also"></a><span data-ttu-id="991a3-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="991a3-126">See Also</span></span>
* [<span data-ttu-id="991a3-127">撰寫自訂的全像遠端播放播放機應用程式</span><span class="sxs-lookup"><span data-stu-id="991a3-127">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="991a3-128">撰寫全像的遠端主機應用程式</span><span class="sxs-lookup"><span data-stu-id="991a3-128">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="991a3-129">全像攝影遠端疑難排解和限制</span><span class="sxs-lookup"><span data-stu-id="991a3-129">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="991a3-130">全像攝影遠端軟體授權條款</span><span class="sxs-lookup"><span data-stu-id="991a3-130">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="991a3-131">Microsoft 隱私權聲明</span><span class="sxs-lookup"><span data-stu-id="991a3-131">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
