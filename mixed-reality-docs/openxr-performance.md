---
title: OpenXR 效能
description: 將 OpenXR 應用程式的 GPU 效能進行 Debug。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR，Khronos，BasicXRApp，DirectX，原生，原生應用程式，自訂引擎，中介軟體，效能，優化，GPU 偵錯工具，RenderDoc，PIX
ms.openlocfilehash: 717dc2d534773bd28f5ad2d5c3720bf4177a1480
ms.sourcegitcommit: 9de2cb11321e6517db69e8c93459a205900a2174
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163342"
---
# <a name="openxr-performance"></a>OpenXR 效能

在 HoloLens 2 上，有幾種方式可以透過 `xrEndFrame` 提交組合資料，而這會導致後續處理，因而影響效能。
若要避免效能 penalities，請使用下列特性[提交單一 `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) ：
* [使用材質陣列 swapchain](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [使用主要色彩 swapchain 格式](openxr-best-practices.md#select-a-swapchain-format)
* [使用建議的視圖維度](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* 請勿設定 `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` 旗標
* 將 `XrCompositionLayerDepthInfoKHR` `minDepth` 設定為 0.0 f，並將 `maxDepth` 為 1.0 f

其他考慮會產生較佳的效能：
* [使用16位深度格式](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [進行實例繪製呼叫](openxr-best-practices.md#render-with-texture-array-and-vprt)
