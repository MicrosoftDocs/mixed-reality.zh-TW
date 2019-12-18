---
title: 全像遠端版本歷程記錄
description: HoloLens 2 上全像攝影遠端處理的版本歷程記錄。
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens、遠端、全像攝影遠端
ms.openlocfilehash: f051dbf24cab550470a312933ffb99e1ba595257
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181958"
---
# <a name="holographic-remoting-version-history"></a><span data-ttu-id="f8548-104">全像遠端版本歷程記錄</span><span class="sxs-lookup"><span data-stu-id="f8548-104">Holographic Remoting Version History</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f8548-105">本指導方針專屬於 HoloLens 2 上的全像攝影遠端處理。</span><span class="sxs-lookup"><span data-stu-id="f8548-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <span data-ttu-id="f8548-106">版本2.0.18.0 （2019年12月17日）<a name="v2.0.18"></a></span><span class="sxs-lookup"><span data-stu-id="f8548-106">Version 2.0.18.0 (December 17, 2019) <a name="v2.0.18"></a></span></span>
* <span data-ttu-id="f8548-107">已新增對 HolographicViewConfiguration 的支援： https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration</span><span class="sxs-lookup"><span data-stu-id="f8548-107">Added support for HolographicViewConfiguration: https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration</span></span>
* <span data-ttu-id="f8548-108">已修正導致當機的各種錯誤。</span><span class="sxs-lookup"><span data-stu-id="f8548-108">Fixed various bugs that lead to crashes.</span></span>
* <span data-ttu-id="f8548-109">已修正 HolographicCamera 要接受並顯示為 HoloraphicFrame 中新增的相機所需的 HolographicSpace CameraAdded 回呼的 bug。</span><span class="sxs-lookup"><span data-stu-id="f8548-109">Fixed bug where a HolographicSpace.CameraAdded callback was required for a HolographicCamera to get accepted and show up as added camera in the HoloraphicFrame.</span></span>

## <span data-ttu-id="f8548-110">版本2.0.16 （2019年11月11日）<a name="2.0.16"></a></span><span class="sxs-lookup"><span data-stu-id="f8548-110">Version 2.0.16 (November 11, 2019) <a name="2.0.16"></a></span></span>
* <span data-ttu-id="f8548-111">已修正 QR 代碼追蹤中的鎖死。</span><span class="sxs-lookup"><span data-stu-id="f8548-111">Fixed deadlock in QR code tracking.</span></span>
* <span data-ttu-id="f8548-112">已修正 unhandeled 例外狀況，因為在主執行緒中封鎖等候。</span><span class="sxs-lookup"><span data-stu-id="f8548-112">Fixed unhandeled exception due to blocking wait in main thread.</span></span>

## <span data-ttu-id="f8548-113">版本2.0.14 版（2019年10月26日）<a name="v2.0.14"></a></span><span class="sxs-lookup"><span data-stu-id="f8548-113">Version 2.0.14 (October 26, 2019) <a name="v2.0.14"></a></span></span>
* <span data-ttu-id="f8548-114">支援新的 PerceptionDevice Api （Windows 10 2019 年11月更新）。</span><span class="sxs-lookup"><span data-stu-id="f8548-114">Support for new PerceptionDevice APIs (Windows 10 November 2019 Update).</span></span>
* <span data-ttu-id="f8548-115">已修正導致 SpatialGestureRecognizer 無法觸發保存手勢事件的問題。</span><span class="sxs-lookup"><span data-stu-id="f8548-115">Fixed issue which prevent hold gesture events being triggered by SpatialGestureRecognizer.</span></span>
* <span data-ttu-id="f8548-116">已修正使用 SpatialSurfaceObserver. SetBoundingVolume 時的執行緒問題。</span><span class="sxs-lookup"><span data-stu-id="f8548-116">Fixed threading issue when using SpatialSurfaceObserver.SetBoundingVolume.</span></span>

## <span data-ttu-id="f8548-117">版本2.0.12 （2019年10月18日）<a name="v2.0.12"></a></span><span class="sxs-lookup"><span data-stu-id="f8548-117">Version 2.0.12 (October 18, 2019) <a name="v2.0.12"></a></span></span>
* <span data-ttu-id="f8548-118">已修正使用 NavigationRail （X/Y/Z）時的 SpatialGestureRecognizer 損毀。</span><span class="sxs-lookup"><span data-stu-id="f8548-118">Fixed crash in SpatialGestureRecognizer when using NavigationRail(X/Y/Z).</span></span>

## <span data-ttu-id="f8548-119">版本2.0.10 版（2019年10月10日）<a name="v2.0.10"></a></span><span class="sxs-lookup"><span data-stu-id="f8548-119">Version 2.0.10 (October 10, 2019) <a name="v2.0.10"></a></span></span>
* <span data-ttu-id="f8548-120">已修正使用 VR 控制器的觸發程式按鈕時的損毀。</span><span class="sxs-lookup"><span data-stu-id="f8548-120">Fixed crash when using trigger button of VR controllers.</span></span> <span data-ttu-id="f8548-121">全像攝影的遠端處理並不完全支援控制器，如果與 HoloLens 2 配對，只有 [觸發程式] 按鈕和 [Windows] 按鈕才有作用。</span><span class="sxs-lookup"><span data-stu-id="f8548-121">Holographic Remoting does not fully support controllers, only the trigger button and the Windows button are working if paired with HoloLens 2.</span></span>

## <span data-ttu-id="f8548-122">版本2.0.9 （2019年9月19日）<a name="v2.0.9"></a></span><span class="sxs-lookup"><span data-stu-id="f8548-122">Version 2.0.9 (September 19, 2019) <a name="v2.0.9"></a></span></span>
* <span data-ttu-id="f8548-123">已新增對[SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)的支援</span><span class="sxs-lookup"><span data-stu-id="f8548-123">Added support for [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span></span>
* <span data-ttu-id="f8548-124">已新增介面 ```IPlayerContext2``` （由 ```PlayerContext```執行），提供下列成員：</span><span class="sxs-lookup"><span data-stu-id="f8548-124">Added new interface ```IPlayerContext2``` (implemented by ```PlayerContext```) providing the following members:</span></span>
  - <span data-ttu-id="f8548-125">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)屬性。</span><span class="sxs-lookup"><span data-stu-id="f8548-125">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  property.</span></span>
* <span data-ttu-id="f8548-126">已將 ```Failed_RemoteFrameTooOld``` 值新增至 ```BlitResult```</span><span class="sxs-lookup"><span data-stu-id="f8548-126">Added ```Failed_RemoteFrameTooOld``` value to ```BlitResult```</span></span>
* <span data-ttu-id="f8548-127">穩定性和可靠性的改進</span><span class="sxs-lookup"><span data-stu-id="f8548-127">Stability and reliability improvements</span></span>

## <span data-ttu-id="f8548-128">版本2.0.8 （2019年8月20日）<a name="v2.0.8"></a></span><span class="sxs-lookup"><span data-stu-id="f8548-128">Version 2.0.8 (August 20, 2019) <a name="v2.0.8"></a></span></span>

* <span data-ttu-id="f8548-129">已修正使用[IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2)做為參數呼叫[HolographicCameraRenderingParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer)時的損毀。</span><span class="sxs-lookup"><span data-stu-id="f8548-129">Fixed crash when calling [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) with a [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as parameter.</span></span>
* <span data-ttu-id="f8548-130">穩定性和可靠性的改進</span><span class="sxs-lookup"><span data-stu-id="f8548-130">Stability and reliability improvements</span></span>

## <span data-ttu-id="f8548-131">版本2.0.7 （2019年7月26日）<a name="v2.0.7"></a></span><span class="sxs-lookup"><span data-stu-id="f8548-131">Version 2.0.7 (July 26, 2019) <a name="v2.0.7"></a></span></span>

* <span data-ttu-id="f8548-132">HoloLens 2 的第一個公開發行的全像攝影遠端功能。</span><span class="sxs-lookup"><span data-stu-id="f8548-132">First public release of Holographic Remoting for HoloLens 2.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8548-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="f8548-133">See Also</span></span>
* [<span data-ttu-id="f8548-134">撰寫自訂的全像遠端播放播放機應用程式</span><span class="sxs-lookup"><span data-stu-id="f8548-134">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="f8548-135">撰寫全像的遠端主機應用程式</span><span class="sxs-lookup"><span data-stu-id="f8548-135">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="f8548-136">全像攝影遠端疑難排解和限制</span><span class="sxs-lookup"><span data-stu-id="f8548-136">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="f8548-137">全像攝影遠端軟體授權條款</span><span class="sxs-lookup"><span data-stu-id="f8548-137">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="f8548-138">Microsoft 隱私權聲明</span><span class="sxs-lookup"><span data-stu-id="f8548-138">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
