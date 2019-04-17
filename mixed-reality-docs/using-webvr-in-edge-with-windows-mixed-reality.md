---
title: 在 Microsoft Edge 中使用 Windows Mixed Reality WebVR
description: 使用與中 Windows Mixed Reality WebVR 開發概觀
author: YashMaster
ms.author: yabahman
ms.date: 03/21/2018
ms.topic: article
keywords: WebVR、 WebXR、 WinMR、 WebAR，web vr、 web xr、 web mr、 web ar，360 360 影片、 360 影片、 360 的相片、 360 的相片、 360 內容、 沈浸式 web、 immersiveweb，IW
ms.openlocfilehash: fab17f4dcecc34d8f1ca4836dce6de90522899cd
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596939"
---
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a><span data-ttu-id="b5c14-104">在 Microsoft Edge 中使用 Windows Mixed Reality WebVR</span><span class="sxs-lookup"><span data-stu-id="b5c14-104">Using WebVR in Microsoft Edge with Windows Mixed Reality</span></span>

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="b5c14-105">建立 Windows Mixed reality WebVR 內容沈浸式耳機</span><span class="sxs-lookup"><span data-stu-id="b5c14-105">Creating WebVR content for Windows Mixed reality immersive headsets</span></span>

<span data-ttu-id="b5c14-106">提供 Windows 10 Fall Creators Update 的 Microsoft Edge 開頭 WebVR 1.1。</span><span class="sxs-lookup"><span data-stu-id="b5c14-106">WebVR 1.1 is available in Microsoft Edge beginning with the Windows 10 Fall Creators Update.</span></span> <span data-ttu-id="b5c14-107">開發人員現在可以使用此 API，在網站上建立沉浸式 VR 體驗。</span><span class="sxs-lookup"><span data-stu-id="b5c14-107">Developers can now use this API to create immersive VR experiences on the web.</span></span>

<span data-ttu-id="b5c14-108">WebVR API 提供頁面可用來呈現立體音響 WebGL 場景回到 HMD HMD 姿勢資料。</span><span class="sxs-lookup"><span data-stu-id="b5c14-108">The WebVR API provides HMD pose data to the page which can be used to render a stereo WebGL scene back to the HMD.</span></span> <span data-ttu-id="b5c14-109">API 支援的詳細資訊位於[Microsoft Edge 平台狀態 頁面](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/)。</span><span class="sxs-lookup"><span data-stu-id="b5c14-109">Details on API support is available on the [Microsoft Edge Platform Status page](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/).</span></span> <span data-ttu-id="b5c14-110">在 Microsoft Edge 中所有時間有 WebVR API 介面區。</span><span class="sxs-lookup"><span data-stu-id="b5c14-110">The WebVR API surface area is present at all times within Microsoft Edge.</span></span> <span data-ttu-id="b5c14-111">不過，getVRDisplays() 呼叫只會傳回耳機，如果已插入耳機或模擬器已開啟。</span><span class="sxs-lookup"><span data-stu-id="b5c14-111">However, a call to getVRDisplays() will only return a headset if either a headset is plugged in or the simulator has been turned on.</span></span>

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="b5c14-112">在 Windows Mixed Reality 沈浸式耳機中檢視 WebVR 內容</span><span class="sxs-lookup"><span data-stu-id="b5c14-112">Viewing WebVR content in Windows Mixed Reality immersive headsets</span></span>

<span data-ttu-id="b5c14-113">存取沈浸式耳機 WebVR 內容的指示可在[人十分熱心的指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr)。</span><span class="sxs-lookup"><span data-stu-id="b5c14-113">Instructions for accessing WebVR content in your immersive headset can be found in the [Enthusiast's Guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="b5c14-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5c14-114">See Also</span></span>
* [<span data-ttu-id="b5c14-115">WebVR 資訊</span><span class="sxs-lookup"><span data-stu-id="b5c14-115">WebVR information</span></span>](http://webvr.info)
* [<span data-ttu-id="b5c14-116">WebVR 規格</span><span class="sxs-lookup"><span data-stu-id="b5c14-116">WebVR specification</span></span>](https://w3c.github.io/webvr/)
* <span data-ttu-id="b5c14-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="b5c14-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span></span>
* <span data-ttu-id="b5c14-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="b5c14-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="b5c14-119">[遊樂器 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx)和[遊戲台延伸模組](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="b5c14-119">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="b5c14-120">遺失 WebGL 中的內容的處理</span><span class="sxs-lookup"><span data-stu-id="b5c14-120">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="b5c14-121">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="b5c14-121">Pointerlock</span></span>](http://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="b5c14-122">glTF</span><span class="sxs-lookup"><span data-stu-id="b5c14-122">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="b5c14-123">若要啟用 WebVR 使用 Babylon.js</span><span class="sxs-lookup"><span data-stu-id="b5c14-123">Using Babylon.js to enable WebVR</span></span>](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)

