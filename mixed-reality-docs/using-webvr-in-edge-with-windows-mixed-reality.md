---
title: 在 Microsoft Edge 中搭配 Windows Mixed Reality 使用 WebVR
description: 在 Windows Mixed Reality 中使用和開發 WebVR 的總覽
author: YashMaster
ms.author: yabahman
ms.date: 03/21/2018
ms.topic: article
keywords: WebVR，WebXR，WinMR，WebAR，web vr，web xr，web mr，web ar，360，360 video，360影片，360相片，360相片，360內容，沉浸式 web，immersiveweb，IW
ms.openlocfilehash: 87805d2c40e9e63cdf3e432189b9deb7d575a380
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437210"
---
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a><span data-ttu-id="2e332-104">在 Microsoft Edge 中搭配 Windows Mixed Reality 使用 WebVR</span><span class="sxs-lookup"><span data-stu-id="2e332-104">Using WebVR in Microsoft Edge with Windows Mixed Reality</span></span>

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="2e332-105">建立 Windows Mixed reality 沉浸式耳機的 WebVR 內容</span><span class="sxs-lookup"><span data-stu-id="2e332-105">Creating WebVR content for Windows Mixed reality immersive headsets</span></span>

<span data-ttu-id="2e332-106">從 Windows 10 秋季建立者更新開始，Microsoft Edge 中提供了 WebVR 1.1。</span><span class="sxs-lookup"><span data-stu-id="2e332-106">WebVR 1.1 is available in Microsoft Edge beginning with the Windows 10 Fall Creators Update.</span></span> <span data-ttu-id="2e332-107">開發人員現在可以使用此 API 在網路上建立沉浸式的 VR 體驗。</span><span class="sxs-lookup"><span data-stu-id="2e332-107">Developers can now use this API to create immersive VR experiences on the web.</span></span>

<span data-ttu-id="2e332-108">WebVR API 提供 HMD 姿勢資料給頁面，可用來將身歷聲 WebGL 場景呈現回 HMD。</span><span class="sxs-lookup"><span data-stu-id="2e332-108">The WebVR API provides HMD pose data to the page which can be used to render a stereo WebGL scene back to the HMD.</span></span> <span data-ttu-id="2e332-109">如需 API 支援的詳細資料，請至[Microsoft Edge 平臺狀態頁面](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/)。</span><span class="sxs-lookup"><span data-stu-id="2e332-109">Details on API support is available on the [Microsoft Edge Platform Status page](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/).</span></span> <span data-ttu-id="2e332-110">WebVR API 介面區會在 Microsoft Edge 中的任何時間存在。</span><span class="sxs-lookup"><span data-stu-id="2e332-110">The WebVR API surface area is present at all times within Microsoft Edge.</span></span> <span data-ttu-id="2e332-111">不過，如果耳機已插入或模擬器已開啟，則呼叫 getVRDisplays （）只會傳回耳機。</span><span class="sxs-lookup"><span data-stu-id="2e332-111">However, a call to getVRDisplays() will only return a headset if either a headset is plugged in or the simulator has been turned on.</span></span>

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="2e332-112">在 Windows Mixed Reality 沉浸式耳機中觀看 WebVR 內容</span><span class="sxs-lookup"><span data-stu-id="2e332-112">Viewing WebVR content in Windows Mixed Reality immersive headsets</span></span>

<span data-ttu-id="2e332-113">如需如何存取您的沉浸式耳機中 WebVR 內容的指示，請參閱《[愛好者指南》](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr)。</span><span class="sxs-lookup"><span data-stu-id="2e332-113">Instructions for accessing WebVR content in your immersive headset can be found in the [Enthusiast's Guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="2e332-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="2e332-114">See Also</span></span>
* [<span data-ttu-id="2e332-115">WebVR 資訊</span><span class="sxs-lookup"><span data-stu-id="2e332-115">WebVR information</span></span>](https://webvr.info)
* [<span data-ttu-id="2e332-116">WebVR 規格</span><span class="sxs-lookup"><span data-stu-id="2e332-116">WebVR specification</span></span>](https://w3c.github.io/webvr/)
* <span data-ttu-id="2e332-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="2e332-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span></span>
* <span data-ttu-id="2e332-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="2e332-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="2e332-119">[遊戲台 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx)和[遊戲台擴充](https://w3c.github.io/gamepad/extensions.html)功能</span><span class="sxs-lookup"><span data-stu-id="2e332-119">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="2e332-120">處理 WebGL 中遺失的內容</span><span class="sxs-lookup"><span data-stu-id="2e332-120">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="2e332-121">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="2e332-121">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="2e332-122">glTF</span><span class="sxs-lookup"><span data-stu-id="2e332-122">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="2e332-123">使用 Babylon.js 來啟用 WebVR</span><span class="sxs-lookup"><span data-stu-id="2e332-123">Using Babylon.js to enable WebVR</span></span>](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)

