---
title: 使用 WebXR 搭配 Windows Mixed Reality
description: 在 Windows Mixed Reality 中使用和開發 WebXR 的總覽
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR，WinMR，WebAR，WebVR，WindowsMixedReality，HoloLens，windows mixed reality，web vr，web xr，web mr，web ar，360，360 video，360影片，360相片，360相片，360內容，沉浸式 web，immersiveweb，IW
ms.openlocfilehash: 01e6cd44e9879cd7fd9b11e178134eaf364cc53c
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278439"
---
# <a name="webxr-overview"></a><span data-ttu-id="a4c6e-104">WebXR 總覽</span><span class="sxs-lookup"><span data-stu-id="a4c6e-104">WebXR Overview</span></span>

## <a name="what-is-webxr"></a><span data-ttu-id="a4c6e-105">什麼是 WebXR</span><span class="sxs-lookup"><span data-stu-id="a4c6e-105">What is WebXR</span></span>

<span data-ttu-id="a4c6e-106">**WebXR 裝置 API**是用來存取**虛擬實境（VR）** 和增強的**現實（AR）** 裝置，**包括感應器**和**網路**上的前端**裝載顯示器**。</span><span class="sxs-lookup"><span data-stu-id="a4c6e-106">The **WebXR device API** is for accessing **virtual reality (VR)** and **augmented reality (AR)** devices, including **sensors** and **head-mounted displays** on the **Web**.</span></span> <span data-ttu-id="a4c6e-107">WebXR 裝置 API 目前可在 Microsoft Edge 和 Chrome 79 版和更新版本上取得，並支援 WebXR 作為預設值。</span><span class="sxs-lookup"><span data-stu-id="a4c6e-107">WebXR device API is currently available on Microsoft Edge and Chrome version 79 and later versions supports WebXR as a default.</span></span> <span data-ttu-id="a4c6e-108">您可以在[caniuse.com](https://caniuse.com/#search=webxr)檢查 WebXR 的最新瀏覽器支援狀態。</span><span class="sxs-lookup"><span data-stu-id="a4c6e-108">You can check the latest browser support status for WebXR at [caniuse.com](https://caniuse.com/#search=webxr).</span></span>

<span data-ttu-id="a4c6e-109">在[新功能](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide)一節中深入瞭解[Windows Mixed Reality 和新的 Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)。</span><span class="sxs-lookup"><span data-stu-id="a4c6e-109">Learn more about the [Windows Mixed Reality and the new Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)in [What's new](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide) section.</span></span>

## <a name="viewing-webxr"></a><span data-ttu-id="a4c6e-110">觀看 WebXR</span><span class="sxs-lookup"><span data-stu-id="a4c6e-110">Viewing WebXR</span></span>

<span data-ttu-id="a4c6e-111">若要測試您的瀏覽器是否支援 WebXR，您可以在瀏覽器中流覽至[WebXR 範例](https://immersive-web.github.io/webxr-samples/)。</span><span class="sxs-lookup"><span data-stu-id="a4c6e-111">To test if your browser supports WebXR, you can navigate to [WebXR Samples](https://immersive-web.github.io/webxr-samples/) in your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="a4c6e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4c6e-112">See Also</span></span>

* [<span data-ttu-id="a4c6e-113">WebXR 裝置 API 規格</span><span class="sxs-lookup"><span data-stu-id="a4c6e-113">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="a4c6e-114">WebXR 裝置 API 檔</span><span class="sxs-lookup"><span data-stu-id="a4c6e-114">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="a4c6e-115">Immersiveweb dev</span><span class="sxs-lookup"><span data-stu-id="a4c6e-115">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="a4c6e-116">WebXR 範例</span><span class="sxs-lookup"><span data-stu-id="a4c6e-116">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="a4c6e-117">Windows Mixed Reality 和新的 Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="a4c6e-117">Windows Mixed Reality and the new Microsoft Edge</span></span>](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [<span data-ttu-id="a4c6e-118">沉浸式 Web W3C Github</span><span class="sxs-lookup"><span data-stu-id="a4c6e-118">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="a4c6e-119">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="a4c6e-119">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="a4c6e-120">[遊戲台 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx)和[遊戲台擴充](https://w3c.github.io/gamepad/extensions.html)功能</span><span class="sxs-lookup"><span data-stu-id="a4c6e-120">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="a4c6e-121">處理 WebGL 中遺失的內容</span><span class="sxs-lookup"><span data-stu-id="a4c6e-121">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="a4c6e-122">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="a4c6e-122">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="a4c6e-123">glTF</span><span class="sxs-lookup"><span data-stu-id="a4c6e-123">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="a4c6e-124">使用 Babylon.js 建立 WebXR 體驗</span><span class="sxs-lookup"><span data-stu-id="a4c6e-124">Using Babylon.js to create WebXR experiences</span></span>](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [<span data-ttu-id="a4c6e-125">沉浸式 web 社區群組</span><span class="sxs-lookup"><span data-stu-id="a4c6e-125">Immersive web community group</span></span>](https://www.w3.org/community/immersive-web/)
