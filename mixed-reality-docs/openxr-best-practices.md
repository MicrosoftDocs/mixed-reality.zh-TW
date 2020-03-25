---
title: OpenXR 最佳作法
description: 瞭解 OpenXR 應用程式的視覺品質、穩定性和效能最佳做法。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR，Khronos，BasicXRApp，DirectX，原生，原生應用程式，自訂引擎，中介軟體，最佳做法，效能，品質，穩定性
ms.openlocfilehash: 01ce2ac0a69ffdf5dd1f00b92f37f54964f4c30c
ms.sourcegitcommit: 9de2cb11321e6517db69e8c93459a205900a2174
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163352"
---
# <a name="openxr-app-best-practices"></a>OpenXR 應用程式最佳做法

您可以在 BasicXrApp 的[OpenXRProgram .cpp](https://github.com/microsoft/OpenXR-SDK-VisualStudio/blob/master/samples/BasicXrApp/OpenXrProgram.cpp)檔案中查看下列最佳做法的範例。 開頭的 Run （）函式會從初始化到事件和轉譯迴圈，捕獲一般的 OpenXR 應用程式代碼流程。

## <a name="best-practices-for-visual-quality-and-stability"></a>視覺品質和穩定性的最佳做法

本節中的最佳作法說明如何在任何 OpenXR 應用程式中取得最佳的視覺品質和穩定性。

如需 HoloLens 2 特定的進一步效能建議，請參閱下面的[hololens 2 的最佳效能做法](#best-practices-for-performance-on-hololens-2)一節。

### <a name="gamma-correct-rendering"></a>Gamma-正確呈現

請務必小心，以確保您的轉譯管線是 gamma 正確的。 當轉譯為 swapchain 時，轉譯目標視圖格式應符合 swapchain 格式（例如，swapchain 格式和轉譯目標視圖的 DXGI_FORMAT_B8G8R8A8_UNORM_SRGB）。
例外狀況是如果應用程式的轉譯管線在著色器程式碼中執行手動的 sRGB 轉換，在這種情況下，應用程式應該要求 sRGB swapchain 格式，但針對轉譯目標視圖使用線性格式（例如，要求 DXGI_FORMAT_B8G8R8A8_UNORM_SRGB 做為swapchain 格式，但使用 DXGI_FORMAT_B8G8R8A8_UNORM 做為轉譯目標視圖），以避免將內容更正為雙 gamma。

### <a name="submit-depth-buffer-for-projection-layers"></a>提交預測層的深度緩衝區

提交框架以 `xrEndFrame`時，請一律使用 `XR_KHR_composition_layer_depth` 延伸模組，並連同投影層一起提交深度緩衝區。
這會藉由啟用 HoloLens 2 上的硬體深度 reprojection，來改善全像全息的穩定性。

### <a name="choose-a-reasonable-depth-range"></a>選擇合理的深度範圍

偏好較窄的深度範圍來界定虛擬內容的範圍，以協助在 HoloLens 上進行全息的穩定性。
例如，OpenXrProgram 的範例是使用0.1 到20的計量。
使用[反向-Z](https://developer.nvidia.com/content/depth-precision-visualized)可取得更統一的深度解析。
請注意，在 HoloLens 2 上，使用慣用的 `DXGI_FORMAT_D16_UNORM` 深度格式將有助於達到更佳的畫面播放速率和效能，雖然16位深度緩衝區比24位深度緩衝區提供的深度解析度較少。
因此，遵循這些最佳作法來充分利用深度解析，會變得更重要。

### <a name="prepare-for-different-environment-blend-modes"></a>為不同的環境 blend 模式做好準備

如果您的應用程式也會在完全封鎖世界的沉浸式耳機上執行，請務必使用 `xrEnumerateEnvironmentBlendModes` API 列舉支援的環境 blend 模式，並據以準備您的轉譯內容。
例如，對於具有 `XR_ENVIRONMENT_BLEND_MODE_ADDITIVE` 的系統（例如 HoloLens），應用程式應該使用透明的色彩，而針對具有 `XR_ENVIRONMENT_BLEND_MODE_OPAQUE`的系統，應用程式應該在背景轉譯一些不透明的色彩或部分虛擬空間。

### <a name="choose-unbounded-reference-space-as-applications-root-space"></a>選擇未系結的參考空間作為應用程式的根空間

應用程式通常會建立一些根全局座標空間，以將視圖、動作和全息合併連接在一起。
當支援擴充功能來建立[全球規模座標系統](coordinate-systems.md#building-a-world-scale-experience)時，請使用 `XR_REFERENCE_SPACE_TYPE_UNBOUNDED_MSFT`，讓您的應用程式避免在使用者從應用程式啟動的位置往上移動（例如5米）時，不希望的全息影像漂移。
如果未受限制的空間延伸模組不存在，請使用 `XR_REFERENCE_SPACE_TYPE_LOCAL` 做為回復。

### <a name="associate-hologram-with-spatial-anchor"></a>將全息影像與空間錨點建立關聯

使用未系結的參考空間時，您直接放在該參考空間中的全息影像，[可能會在使用者進入遙遠的房間時漂移，然後再回來](coordinate-systems.md#building-a-world-scale-experience)。
對於全息影像使用者，請使用 `xrCreateSpatialAnchorSpaceMSFT` 擴充功能來[建立空間錨點](spatial-anchors.md#best-practices)，並在其原點位置放置全息影像。
這會在一段時間後，讓該全息影像獨立穩定。

### <a name="support-mixed-reality-capture"></a>支援混合現實 capture

雖然 HoloLens 2 的主要顯示器會使用加總的環境混合，當使用者起始[混合現實捕捉](mixed-reality-capture-for-developers.md)時，應用程式的轉譯內容會與環境影片串流進行 Alpha 混合。
若要在混合現實 capture 影片中達到最佳的視覺品質，最好是在投影層的 `layerFlags`中設定 `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT`。

## <a name="best-practices-for-performance-on-hololens-2"></a>HoloLens 2 上效能的最佳做法

作為具有硬體 reprojection 支援的行動裝置，HoloLens 2 會有更嚴格的需求，以取得最佳效能。  有數種方式可透過 `xrEndFrame` 提交組合資料，而這會導致後續處理，因而影響效能。

### <a name="select-a-swapchain-format"></a>選取 swapchain 格式

請一律使用 `xrEnumerateSwapchainFormats`列舉支援的像素格式，並從應用程式支援的執行時間選擇第一個色彩和深度像素格式，因為這是執行時間慣用的最佳效能。 請注意，在 HoloLens 2 上，`DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` 和 `DXGI_FORMAT_D16_UNORM` 通常是達到更佳轉譯效能的第一種選擇。 在桌上型電腦上執行的 VR 耳機上可能會有不同的喜好設定，其中24位深度緩衝區會降低效能影響。
  
**效能警告：** 使用主要 swapchain 色彩格式以外的格式會導致執行時間後置處理，這會造成顯著的效能影響。

### <a name="render-with-recommended-rendering-parameters-and-frame-timing"></a>使用建議的呈現參數和畫面格時間進行轉譯

一律使用建議的視圖設定寬度/高度（`recommendedImageRectWidth` 和 `recommendedImageRectHeight` 從 `XrViewConfigurationView`）進行轉譯，並一律使用 `xrLocateViews` API 來查詢建議的視圖姿勢、fov 和其他轉譯參數，然後再呈現。
查詢姿勢和 views 時，請一律使用最新 `xrWaitFrame` 呼叫中的 `XrFrameEndInfo.predictedDisplayTime`。
這可讓 HoloLens 針對正在戴 HoloLens 的人員調整呈現和優化視覺品質。

### <a name="use-a-single-projection-layer"></a>使用單一投影圖層

HoloLens 2 的 GPU 電源有限，可讓應用程式轉譯內容和針對單一投影層優化的硬體組合器。
一律使用單一投影層可以協助應用程式的畫面播放速率、全息圖形穩定性和視覺品質。  
  
**效能警告：** 提交任何專案，但單一保護層會導致執行時間後置處理，這會造成顯著的效能影響。

### <a name="render-with-texture-array-and-vprt"></a>使用材質陣列和 VPRT 呈現

使用色彩 swapchain 的 `arraySize=2`，同時建立一個 `xrSwapchain` 以進行左右排列，另一種是深度。
將視覺呈現到配量0，並將適當的眼轉譯為配量1。
使用著色器搭配 VPRT 和實例繪製呼叫來進行 stereoscopic 轉譯，以將 GPU 負載降至最低。
這也可讓執行時間的優化在 HoloLens 2 上達到最佳效能。
使用材質陣列的替代方案（例如，每眼的雙重轉譯或個別的 swapchain）會導致執行時間後置處理，這會造成顯著的效能影響。

### <a name="avoid-quad-layers"></a>避免四層

不是以 `XrCompositionLayerQuad`的組合層來提交四層，而是直接將四個內容轉譯成投射 swapchain。

**效能警告：** 提供超出單一預測層的額外層級（例如四層），會導致執行時間後置處理，而產生顯著的效能影響。