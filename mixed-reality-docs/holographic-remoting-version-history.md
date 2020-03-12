---
title: 全像遠端版本歷程記錄
description: HoloLens 2 上全像攝影遠端處理的版本歷程記錄。
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens、遠端、全像攝影遠端
ms.openlocfilehash: 62f54dbcf5327cdd5f13622704684a2cb0606d7d
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2020
ms.locfileid: "79092316"
---
# <a name="holographic-remoting-version-history"></a><span data-ttu-id="b4cc0-104">全像遠端版本歷程記錄</span><span class="sxs-lookup"><span data-stu-id="b4cc0-104">Holographic Remoting Version History</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b4cc0-105">本指導方針專屬於 HoloLens 2 上的全像攝影遠端處理。</span><span class="sxs-lookup"><span data-stu-id="b4cc0-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <span data-ttu-id="b4cc0-106">版本2.1.0 （2020年3月11日）<a name="v2.1.0"></a></span><span class="sxs-lookup"><span data-stu-id="b4cc0-106">Version 2.1.0 (March 11, 2020) <a name="v2.1.0"></a></span></span>
* <span data-ttu-id="b4cc0-107">已將網路傳輸切換為使用[RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) via UDP。</span><span class="sxs-lookup"><span data-stu-id="b4cc0-107">Switched network transport to use [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) via UDP.</span></span> <span data-ttu-id="b4cc0-108">安全連線立即使用[SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) 。</span><span class="sxs-lookup"><span data-stu-id="b4cc0-108">Secure connections use [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) now.</span></span> <span data-ttu-id="b4cc0-109">請注意，全像之前發行的「全像攝影[」遠端處理](holographic-remoting-player.md)版本仍然相容。</span><span class="sxs-lookup"><span data-stu-id="b4cc0-109">Note, the [Holographic Remoting Player](holographic-remoting-player.md) is still compatible with all previously release Holographic Remoting versions.</span></span> <span data-ttu-id="b4cc0-110">若要從新的網路傳輸中獲益，全像攝影的遠端播放程式和遠端應用程式有問題，必須使用版本2.1.0。</span><span class="sxs-lookup"><span data-stu-id="b4cc0-110">To benefit from the new network transport both, the Holographic Remoting Player and the remote app in question, have to use version 2.1.0.</span></span>
* <span data-ttu-id="b4cc0-111">已新增對[HolographicCameraRenderingParameters 的支援。 CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)。</span><span class="sxs-lookup"><span data-stu-id="b4cc0-111">Added support for [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span> 

## <span data-ttu-id="b4cc0-112">版本2.0.20 版（2020年2月2日）<a name="v2.0.20"></a></span><span class="sxs-lookup"><span data-stu-id="b4cc0-112">Version 2.0.20 (February 2, 2020) <a name="v2.0.20"></a></span></span>
* <span data-ttu-id="b4cc0-113">已修正導致當機的各種錯誤。</span><span class="sxs-lookup"><span data-stu-id="b4cc0-113">Fixed various bugs that lead to crashes.</span></span>

## <span data-ttu-id="b4cc0-114">版本2.0.18 版（2019年12月17日）<a name="v2.0.18"></a></span><span class="sxs-lookup"><span data-stu-id="b4cc0-114">Version 2.0.18 (December 17, 2019) <a name="v2.0.18"></a></span></span>
* <span data-ttu-id="b4cc0-115">已新增對[HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration)的支援</span><span class="sxs-lookup"><span data-stu-id="b4cc0-115">Added support for [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration)</span></span>
* <span data-ttu-id="b4cc0-116">已修正導致當機的各種錯誤。</span><span class="sxs-lookup"><span data-stu-id="b4cc0-116">Fixed various bugs that lead to crashes.</span></span>
* <span data-ttu-id="b4cc0-117">已修正 HolographicCamera 要接受並顯示為 HoloraphicFrame 中新增的相機所需的 HolographicSpace CameraAdded 回呼的 bug。</span><span class="sxs-lookup"><span data-stu-id="b4cc0-117">Fixed bug where a HolographicSpace.CameraAdded callback was required for a HolographicCamera to get accepted and show up as added camera in the HoloraphicFrame.</span></span>

## <span data-ttu-id="b4cc0-118">版本2.0.16 （2019年11月11日）<a name="2.0.16"></a></span><span class="sxs-lookup"><span data-stu-id="b4cc0-118">Version 2.0.16 (November 11, 2019) <a name="2.0.16"></a></span></span>
* <span data-ttu-id="b4cc0-119">已修正 QR 代碼追蹤中的鎖死。</span><span class="sxs-lookup"><span data-stu-id="b4cc0-119">Fixed deadlock in QR code tracking.</span></span>
* <span data-ttu-id="b4cc0-120">已修正 unhandeled 例外狀況，因為在主執行緒中封鎖等候。</span><span class="sxs-lookup"><span data-stu-id="b4cc0-120">Fixed unhandeled exception due to blocking wait in main thread.</span></span>

## <span data-ttu-id="b4cc0-121">版本2.0.14 版（2019年10月26日）<a name="v2.0.14"></a></span><span class="sxs-lookup"><span data-stu-id="b4cc0-121">Version 2.0.14 (October 26, 2019) <a name="v2.0.14"></a></span></span>
* <span data-ttu-id="b4cc0-122">支援新的 PerceptionDevice Api （Windows 10 2019 年11月更新）。</span><span class="sxs-lookup"><span data-stu-id="b4cc0-122">Support for new PerceptionDevice APIs (Windows 10 November 2019 Update).</span></span>
* <span data-ttu-id="b4cc0-123">已修正導致 SpatialGestureRecognizer 無法觸發保存手勢事件的問題。</span><span class="sxs-lookup"><span data-stu-id="b4cc0-123">Fixed issue which prevent hold gesture events being triggered by SpatialGestureRecognizer.</span></span>
* <span data-ttu-id="b4cc0-124">已修正使用 SpatialSurfaceObserver. SetBoundingVolume 時的執行緒問題。</span><span class="sxs-lookup"><span data-stu-id="b4cc0-124">Fixed threading issue when using SpatialSurfaceObserver.SetBoundingVolume.</span></span>

## <span data-ttu-id="b4cc0-125">版本2.0.12 （2019年10月18日）<a name="v2.0.12"></a></span><span class="sxs-lookup"><span data-stu-id="b4cc0-125">Version 2.0.12 (October 18, 2019) <a name="v2.0.12"></a></span></span>
* <span data-ttu-id="b4cc0-126">已修正使用 NavigationRail （X/Y/Z）時的 SpatialGestureRecognizer 損毀。</span><span class="sxs-lookup"><span data-stu-id="b4cc0-126">Fixed crash in SpatialGestureRecognizer when using NavigationRail(X/Y/Z).</span></span>

## <span data-ttu-id="b4cc0-127">版本2.0.10 版（2019年10月10日）<a name="v2.0.10"></a></span><span class="sxs-lookup"><span data-stu-id="b4cc0-127">Version 2.0.10 (October 10, 2019) <a name="v2.0.10"></a></span></span>
* <span data-ttu-id="b4cc0-128">已修正使用 VR 控制器的觸發程式按鈕時的損毀。</span><span class="sxs-lookup"><span data-stu-id="b4cc0-128">Fixed crash when using trigger button of VR controllers.</span></span> <span data-ttu-id="b4cc0-129">全像攝影的遠端處理並不完全支援控制器，如果與 HoloLens 2 配對，只有 [觸發程式] 按鈕和 [Windows] 按鈕才有作用。</span><span class="sxs-lookup"><span data-stu-id="b4cc0-129">Holographic Remoting does not fully support controllers, only the trigger button and the Windows button are working if paired with HoloLens 2.</span></span>

## <span data-ttu-id="b4cc0-130">版本2.0.9 （2019年9月19日）<a name="v2.0.9"></a></span><span class="sxs-lookup"><span data-stu-id="b4cc0-130">Version 2.0.9 (September 19, 2019) <a name="v2.0.9"></a></span></span>
* <span data-ttu-id="b4cc0-131">已新增對[SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)的支援</span><span class="sxs-lookup"><span data-stu-id="b4cc0-131">Added support for [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span></span>
* <span data-ttu-id="b4cc0-132">已新增介面 ```IPlayerContext2``` （由 ```PlayerContext```執行），提供下列成員：</span><span class="sxs-lookup"><span data-stu-id="b4cc0-132">Added new interface ```IPlayerContext2``` (implemented by ```PlayerContext```) providing the following members:</span></span>
  - <span data-ttu-id="b4cc0-133">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)屬性。</span><span class="sxs-lookup"><span data-stu-id="b4cc0-133">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  property.</span></span>
* <span data-ttu-id="b4cc0-134">已將 ```Failed_RemoteFrameTooOld``` 值新增至 ```BlitResult```</span><span class="sxs-lookup"><span data-stu-id="b4cc0-134">Added ```Failed_RemoteFrameTooOld``` value to ```BlitResult```</span></span>
* <span data-ttu-id="b4cc0-135">穩定性和可靠性的改進</span><span class="sxs-lookup"><span data-stu-id="b4cc0-135">Stability and reliability improvements</span></span>

## <span data-ttu-id="b4cc0-136">版本2.0.8 （2019年8月20日）<a name="v2.0.8"></a></span><span class="sxs-lookup"><span data-stu-id="b4cc0-136">Version 2.0.8 (August 20, 2019) <a name="v2.0.8"></a></span></span>

* <span data-ttu-id="b4cc0-137">已修正使用[IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2)做為參數呼叫[HolographicCameraRenderingParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer)時的損毀。</span><span class="sxs-lookup"><span data-stu-id="b4cc0-137">Fixed crash when calling [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) with a [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as parameter.</span></span>
* <span data-ttu-id="b4cc0-138">穩定性和可靠性的改進</span><span class="sxs-lookup"><span data-stu-id="b4cc0-138">Stability and reliability improvements</span></span>

## <span data-ttu-id="b4cc0-139">版本2.0.7 （2019年7月26日）<a name="v2.0.7"></a></span><span class="sxs-lookup"><span data-stu-id="b4cc0-139">Version 2.0.7 (July 26, 2019) <a name="v2.0.7"></a></span></span>

* <span data-ttu-id="b4cc0-140">HoloLens 2 的第一個公開發行的全像攝影遠端功能。</span><span class="sxs-lookup"><span data-stu-id="b4cc0-140">First public release of Holographic Remoting for HoloLens 2.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4cc0-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4cc0-141">See Also</span></span>
* [<span data-ttu-id="b4cc0-142">撰寫自訂的全像遠端播放播放機應用程式</span><span class="sxs-lookup"><span data-stu-id="b4cc0-142">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="b4cc0-143">撰寫全像的遠端主機應用程式</span><span class="sxs-lookup"><span data-stu-id="b4cc0-143">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="b4cc0-144">全像攝影遠端疑難排解和限制</span><span class="sxs-lookup"><span data-stu-id="b4cc0-144">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="b4cc0-145">全像攝影遠端軟體授權條款</span><span class="sxs-lookup"><span data-stu-id="b4cc0-145">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="b4cc0-146">Microsoft 隱私權聲明</span><span class="sxs-lookup"><span data-stu-id="b4cc0-146">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
