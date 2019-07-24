---
title: 在 Microsoft Edge 中搭配 Windows Mixed Reality 使用 WebVR
description: 在 Windows Mixed Reality 中使用和開發 WebVR 的總覽
author: YashMaster
ms.author: yabahman
ms.date: 03/21/2018
ms.topic: article
keywords: WebVR, WebXR, WinMR, WebAR, web vr, web xr, web mr, web ar, 360, 360 video, 360 影片, 360 相片, 360 相片, 360 內容, 沉浸式 web, immersiveweb, IW
ms.openlocfilehash: fab17f4dcecc34d8f1ca4836dce6de90522899cd
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548769"
---
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a>在 Microsoft Edge 中搭配 Windows Mixed Reality 使用 WebVR

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a>建立 Windows Mixed reality 沉浸式耳機的 WebVR 內容

從 Windows 10 秋季建立者更新開始, Microsoft Edge 中提供了 WebVR 1.1。 開發人員現在可以使用此 API 在網路上建立沉浸式的 VR 體驗。

WebVR API 提供 HMD 姿勢資料給頁面, 可用來將身歷聲 WebGL 場景呈現回 HMD。 如需 API 支援的詳細資料, 請至[Microsoft Edge 平臺狀態頁面](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/)。 WebVR API 介面區會在 Microsoft Edge 中的任何時間存在。 不過, 如果耳機已插入或模擬器已開啟, 則呼叫 getVRDisplays () 只會傳回耳機。

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a>在 Windows Mixed Reality 沉浸式耳機中觀看 WebVR 內容

如需如何存取您的沉浸式耳機中 WebVR 內容的指示, 請參閱《[愛好者指南》](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr)。

## <a name="see-also"></a>另請參閱
* [WebVR 資訊](http://webvr.info)
* [WebVR 規格](https://w3c.github.io/webvr/)
* [WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)
* [WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)
* [遊戲台 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx)和[遊戲台擴充](https://w3c.github.io/gamepad/extensions.html)功能
* [處理 WebGL 中遺失的內容](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock](http://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [使用 Babylon.js 來啟用 WebVR](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)

