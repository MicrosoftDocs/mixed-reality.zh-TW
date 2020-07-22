---
title: OpenXR
description: 使用可攜的 OpenXR API 標準組建引擎，並將其部署至 Windows Mixed Reality 和 HoloLens 2 耳機。
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、DirectX、原生、原生應用程式、自訂引擎、中介軟體
ms.openlocfilehash: 170ce0b55990158940692db25b925a1e79d7cf39
ms.sourcegitcommit: 3c32f45fd941767d408cccc5a76f1ff1cec763da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86879156"
---
# <a name="openxr"></a>OpenXR

<img align="right" src="images/openxr.png" alt="OpenXR logo">

OpenXR 是一項開放的免費免權利 API 標準，來自<a href="https://www.khronos.org/" target="_blank">Khronos</a> ，可讓引擎以原生的許可權，從多個跨[混合現實](mixed-reality.md)範圍的廠商取得各種裝置。

您可以使用 OpenXR 在 HoloLens 2 或 Windows Mixed Reality 沉浸式耳機桌面上進行開發。  如果您沒有頭戴式裝置的存取權，您可以改用 HoloLens 2 模擬器或 Windows Mixed Reality 模擬器。

## <a name="why-openxr"></a>為什麼要 OpenXR？

有了 OpenXR，您就可以建立以全像是 HoloLens 2）為目標的引擎，將數位內容放在真實世界中，就像真正的一樣，還有沉浸式裝置（例如適用于桌上型電腦的 Windows Mixed Reality 耳機），其會隱藏實體世界並以數位體驗取代。  OpenXR 可讓您撰寫程式碼一次，然後在各種不同的硬體平臺上進行移植。

OpenXR API 會使用載入器，將您的應用程式直接連接到頭戴式裝置的原生平臺支援。  這可為使用者提供最大的效能和最小延遲，不論是使用 Windows Mixed Reality 耳機或任何其他耳機。

## <a name="what-is-openxr"></a>什麼是 OpenXR？

OpenXR API 提供核心姿勢預測、框架時間和空間輸入功能，您將需要建立一個引擎，讓它能夠以像是 HoloLens 2 和沉浸式裝置（例如 Windows Mixed Reality 耳機）為目標的全像攝影裝置。

若要深入瞭解 OpenXR API，請參閱 OpenXR 1.0<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">規格</a>、 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">API 參考</a>和<a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">快速參考指南</a>。  如需詳細資訊，請參閱<a href="https://www.khronos.org/openxr/" target="_blank">Khronos OpenXR 頁面</a>。

若要以 HoloLens 2 的完整功能集為目標，您也會使用跨廠商和廠商專屬的 OpenXR 延伸模組，以啟用 OpenXR 1.0 核心以外的其他功能，像是明確的手勢追蹤、眼睛追蹤、空間對應和空間錨點。  請參閱下面的「[藍圖」一節](#roadmap)，以取得今年稍後所提供之延伸模組的詳細資訊。

請注意，OpenXR 本身不是混合的現實引擎。  相反地，OpenXR 可以讓 Unity 和 Unreal 之類的引擎撰寫可攜的程式碼一次，之後就可以存取使用者全像攝影或沉浸式裝置的原生平臺功能，而不論該平臺的哪個廠商。

## <a name="roadmap"></a>藍圖

OpenXR 規格定義了擴充機制，可讓執行時間實施者公開超出<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Base OpenXR 1.0 規格</a>中所定義之[核心功能](#what-is-openxr)的其他功能。

有三種 OpenXR 擴充功能：
* **廠商延伸模組（例如 `MSFT` ）：** 啟用硬體或軟體功能中的每一廠商創新。  任何執行時間廠商隨時都可以引進和運送廠商延伸模組。
  * **實驗性廠商擴充功能（例如 `MSFT_preview` ）：** 預覽實驗廠商延伸模組，以收集意見反應。  `MSFT_preview`延伸模組僅適用于開發人員裝置，並會在真正的延伸模組隨附時移除。  若要進行實驗，您可以[在開發人員裝置上啟用預覽擴充](openxr-getting-started.md#using-preview-extensions)功能。
* **跨廠商 `EXT` 擴充功能：** 多家公司所定義和實行的跨廠商擴充功能。  有興趣的公司群組可以隨時引進 EXT 延伸模組。
* **官方 `KHR` 延伸模組：** 正式 Khronos 延伸模組已核准為核心規格版本的一部分。  KHR 延伸模組是由與核心規格本身相同的授權所涵蓋。

從2020年7月起，Windows Mixed Reality OpenXR 執行時間支援一組和延伸模組，可將一 `MSFT` `EXT` 組完整的 HoloLens 2 功能帶入 OpenXR 應用程式：

| 功能區域 | 延伸模組可用性 |
|--------------|------------------------|
| 系統 + 會話 | **OpenXR 1.0 核心規格：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#instance" target="_blank">XrInstance</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#system" target="_blank">XrSystemId</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#session" target="_blank">XrSession</a></code> |
| [參考空間（view、local、stage）](coordinate-systems.md) | **OpenXR 1.0 核心規格：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#spaces" target="_blank">XrSpace</a></code> |
| 視圖設定（mono、身歷聲） | **OpenXR 1.0 核心規格：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#view_configurations" target="_blank">XrView...</a></code> |
| [Swapchains](rendering.md)  + [畫面格時間](understanding-performance-for-mixed-reality.md) | **OpenXR 1.0 核心規格：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#rendering" target="_blank">XrSwapchain...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-synchronization" target="_blank">xrWaitFrame</a></code> |
| 組合圖層<br />（投影，四） | **OpenXR 1.0 核心規格：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#compositing" target="_blank">XrCompositionLayer...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-submission" target="_blank">xrEndFrame</a></code> |
| [輸入和 haptics](interaction-fundamentals.md) | **OpenXR 1.0 核心規格：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#input" target="_blank">XrAction...</a></code> |
| Direct3D 11 整合 | **正式 `KHR` 發行延伸模組：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D11_enable" target="_blank">XR_KHR_D3D11_enable</a></code> |
| Direct3D 12 整合 | **正式 `KHR` 發行延伸模組：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D12_enable" target="_blank">XR_KHR_D3D12_enable</a></code> |
| [未系結的參考空間 <br /> （全球規模的體驗）](coordinate-systems.md#building-a-world-scale-experience) | **`MSFT`發行的延伸模組：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_unbounded_reference_space" target="_blank">XR_MSFT_unbounded_reference_space</a></code> |
| [空間錨點](spatial-anchors.md) | **`MSFT`發行的延伸模組：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_anchor">XR_MSFT_spatial_anchor</a></code> |
| [手互動 <br /> （抓握/瞄準姿勢、空中碰、抓住）](hands-and-tools.md)<p>*僅限 HoloLens 2*</p> | **`MSFT`發行的延伸模組：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_interaction">XR_MSFT_hand_interaction</a></code> |
| [手形文字清晰度 + 手上網格](hands-and-tools.md)<p>*僅限 HoloLens 2*</p> | <p>**`EXT`執行時間102中發行的延伸模組：**<code><br /><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hand_tracking">XR_EXT_hand_tracking</a></code></p>**`MSFT`執行時間102中發行的延伸模組：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_tracking_mesh">XR_MSFT_hand_tracking_mesh</a></code> |
| [眼睛目光](eye-tracking.md)<p>*僅限 HoloLens 2*</p> | **`EXT`發行的延伸模組：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_eye_gaze_interaction" target="_blank">XR_EXT_eye_gaze_interaction</a></code> |
| 與其他 HoloLens Sdk 交互操作<br />（例如[QR](qr-code-tracking.md)）<p>*僅限 HoloLens 2*</p> | **`MSFT`執行時間102中發行的延伸模組：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code> |
| [混合現實 Capture <br /> （PV 攝影機的第三個轉譯）](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)<p>*僅限 HoloLens 2*</p> | **`MSFT`執行時間102中發行的擴充功能：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_secondary_view_configuration">XR_MSFT_secondary_view_configuration</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_first_person_observer">XR_MSFT_first_person_observer</a></code> |
| 使用 UWP CoreWindow API 的 Interop<br />（例如鍵盤/滑鼠） | **`MSFT_preview`[預覽執行時間 102](openxr-getting-started.md#using-preview-extensions)中的延伸模組：**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_holographic_window_attachment_preview">XR_MSFT_holographic_window_attachment_preview</a></code><p>** `MSFT` 預覽執行時間中的延伸**模組：2020年8月 *（已規劃）*</p>
| [運動控制器呈現模型](motion-controllers.md#rendering-the-motion-controller-model) | **`MSFT_preview`[預覽運行](openxr-getting-started.md#using-preview-extensions)時間中的延伸模組：**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_controller_model_preview">XR_MSFT_controller_model_preview</a></code><p>** `MSFT` 預覽執行時間中的延伸**模組：2020年9月 *（已規劃）*</p> |
| [場景理解（平面、網格）](scene-understanding.md)<p>*僅限 HoloLens 2*</p> | <p>**在[preview 執行時間 102](openxr-getting-started.md#using-preview-extensions)中：**<br />搭配 <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code> [場景理解 SDK](scene-understanding-sdk.md)使用</p><p>** `MSFT_preview` 未來預覽執行時間中的延伸**模組 *（已規劃）*</p> |
| 其他跨廠商擴充功能 | <p>**發行的官方 `KHR` 延伸模組：**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_depth" target="_blank">XR_KHR_composition_layer_depth</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_visibility_mask" target="_blank">XR_KHR_visibility_mask</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_win32_convert_performance_counter_time" target="_blank">XR_KHR_win32_convert_performance_counter_time</a></code><p>**`EXT`發行的延伸模組：**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_win32_appcontainer_compatible" target="_blank">XR_EXT_win32_appcontainer_compatible</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_debug_utils" target="_blank">XR_EXT_debug_utils</a></code> |

雖然其中一些延伸模組可能會以廠商專屬的 `MSFT` 擴充功能作為開頭，但 Microsoft 和其他 OpenXR 執行時間廠商會共同合作， `EXT` 為 `KHR` 這些功能領域設計跨廠商或延伸模組。  這可讓您針對這些功能所撰寫的程式碼在執行時間廠商之間具有可攜性，就像使用核心規格一樣。

## <a name="get-started-with-openxr"></a>開始使用 OpenXR

您可以使用 OpenXR 在 HoloLens 2 或 Windows Mixed Reality 沉浸式耳機桌面上進行開發。  如果您沒有頭戴式裝置的存取權，您可以改用 HoloLens 2 模擬器或 Windows Mixed Reality 模擬器。

若要開始開發 HoloLens 2 或沉浸式 Windows Mixed Reality 耳機的 OpenXR 應用程式，請參閱[如何開始使用 OpenXR 開發](openxr-getting-started.md)。

## <a name="see-also"></a>請參閱

* <a href="https://www.khronos.org/openxr/" target="_blank">OpenXR 的詳細資訊</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 規格</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">OpenXR 1.0 API 參考</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">OpenXR 1.0 快速參考指南</a>
