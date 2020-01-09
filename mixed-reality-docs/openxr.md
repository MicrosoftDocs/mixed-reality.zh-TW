---
title: OpenXR
description: 使用可攜的 OpenXR API 標準組建引擎，並將其部署至 Windows Mixed Reality 和 HoloLens 2 耳機。
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR，Khronos，BasicXRApp，Mixed Reality OpenXR 開發人員入口網站，DirectX，原生，原生應用程式，自訂引擎，中介軟體
ms.openlocfilehash: 8140b9d3a9e1f4d2d7a25b77a48b39cb765cf6d9
ms.sourcegitcommit: 270ca09ec61e1153a83cf44942d7ba3783ef1805
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694132"
---
# <a name="openxr"></a>OpenXR

OpenXR 是一項開放的免費免權利 API 標準，來自<a href="https://www.khronos.org/" target="_blank">Khronos</a> ，可讓引擎以原生的許可權，從多個跨[混合現實](mixed-reality.md)範圍的廠商取得各種裝置。

您可以使用 OpenXR 在 HoloLens 2 或 Windows Mixed Reality 沉浸式耳機桌面上進行開發。  如果您沒有頭戴式裝置的存取權，您可以改用 HoloLens 2 模擬器或 Windows Mixed Reality 模擬器。

## <a name="why-openxr"></a>為什麼要 OpenXR？

有了 OpenXR，您就可以建立以全像是 HoloLens 2）為目標的引擎，將數位內容放在真實世界中，就像真正的一樣，還有沉浸式裝置（例如桌上型電腦的 Windows Mixed Reality 耳機），其會隱藏實體全球，並以數位體驗取代。  OpenXR 可讓您撰寫程式碼一次，然後在各種不同的硬體平臺上進行移植。

OpenXR API 會使用載入器，將您的應用程式直接連接到頭戴式裝置的原生平臺支援。  這可為使用者提供最大的效能和最小延遲，不論是使用 Windows Mixed Reality 耳機或任何其他耳機。

## <a name="what-is-openxr"></a>什麼是 OpenXR？

核心 OpenXR 1.0 API 提供的基本功能，可讓您建立一個引擎，讓它能夠以全像是 HoloLens 2 和沉浸式裝置（例如 Windows Mixed Reality 耳機）為目標的所有裝置：
* 系統 + 會話
* 參考空間（view、local、stage）
* 視圖設定（mono、身歷聲）
* Swapchains + 框架時間
* 組合圖層
* 輸入和 haptics
* 圖形 API + 平臺整合

若要深入瞭解 OpenXR API，請參閱 OpenXR 1.0<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">規格</a>、 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">API 參考</a>和<a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">快速參考指南</a>。  如需詳細資訊，請參閱<a href="https://www.khronos.org/openxr/" target="_blank">Khronos OpenXR 頁面</a>。

若要以 HoloLens 2 的完整功能集為目標，您也會使用跨廠商和廠商專屬的 OpenXR 延伸模組，以啟用 OpenXR 1.0 核心以外的其他功能，像是明確的手勢追蹤、眼睛追蹤、空間對應和空間錨點。  請參閱下面的[藍圖一](openxr.md#roadmap)節，以取得今年稍後所提供之延伸模組的詳細資訊。

請注意，OpenXR 本身不是混合的現實引擎。  相反地，OpenXR 可以讓 Unity 和 Unreal 之類的引擎撰寫可攜的程式碼一次，之後就可以存取使用者全像攝影或沉浸式裝置的原生平臺功能，而不論該平臺的哪個廠商。

## <a name="getting-started-with-openxr-for-hololens-2"></a>適用于 HoloLens 2 的 OpenXR 入門

若要開始開發 HoloLens 2 的 OpenXR 應用程式：

1. 設定 HoloLens 2 或遵循指示來[安裝 hololens 2 模擬器](using-the-hololens-emulator.md)。
1. 從裝置或模擬器內啟動 Store 應用程式，並確定已更新所有應用程式。  這可確保 HoloLens 上的 OpenXR 執行時間已更新為 OpenXR 1.0。  如果使用模擬器，您會想要參閱[模擬器輸入指示](using-the-hololens-emulator.md#basic-emulator-input)，以協助您在模擬器內使用 Store 應用程式。

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>開始使用 OpenXR for Windows Mixed Reality 耳機

若要開始開發沉浸式 Windows Mixed Reality 耳機的 OpenXR 應用程式：

1. 請確定您執行的是 Windows 10 5 月2019更新（1903），這是 Windows Mixed Reality 終端使用者執行 OpenXR 應用程式的最低需求。  如果您是在舊版的 Windows 10 上，您可以使用<a href="https://www.microsoft.com//software-download/windows10" target="_blank">Windows 10 更新</a>小幫手升級至2019版的更新。  如果您無法更新您的電腦，您也可以[使用 Windows 10 2018 年10月更新（1809）來開發 OpenXR 應用程式](openxr.md#developing-on-windows-10-october-2018-update)，不過您可能會遇到較低的效能或其他問題。
2. 設定 Windows Mixed Reality 耳機，或遵循指示[啟用 Windows Mixed reality](using-the-windows-mixed-reality-simulator.md)模擬器。  設定 Windows Mixed Reality 之後，混合現實入口網站會自動安裝 Windows Mixed Reality OpenXR 執行時間。  然後，Microsoft Store 會讓執行時間保持在最新狀態。
3. 從 [開始] 功能表啟動混合現實入口網站，然後按一下 [...]，讓 Windows Mixed Reality OpenXR 執行時間變成作用中功能表左下方選取 [設定 OpenXR]。<br>
![在混合現實入口網站中設定 OpenXR](images/mixed-reality-portal-set-up-openxr.png)

如果您需要讓 Windows Mixed Reality OpenXR 執行時間再次生效，請重複步驟3。

> [!NOTE]
> Windows Mixed Reality OpenXR 執行時間很快就會針對所有 Windows Mixed Reality 使用者自動設定。

## <a name="getting-the-mixed-reality-openxr-developer-portal"></a>取得 Mixed Reality OpenXR 開發人員入口網站

若要試用 Windows Mixed Reality OpenXR 執行時間，您可以安裝<a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">[Mixed Reality OpenXR 開發人員入口網站] 應用程式</a>。  此應用程式提供的示範場景會演練 OpenXR 的各種功能，以及提供作用中執行時間和目前耳機的重要資訊的 [系統狀態] 頁面。

![Mixed Reality OpenXR 開發人員入口網站應用程式](images/mixed-reality-openxr-developer-portal.png)

## <a name="building-a-sample-openxr-app"></a>建立範例 OpenXR 應用程式

<a href="https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>專案示範一個簡單的 OpenXR 範例，其中包含兩個 Visual Studio 專案檔，一個用於 Win32 桌面應用程式，另一個用於 UWP HoloLens 2 應用程式。  因為解決方案包含 HoloLens UWP 專案，所以您需要安裝在 Visual Studio 中的[通用 Windows 平臺開發工作負載](install-the-tools.md#installation-checklist)，才能完全開啟它。

請注意，雖然 Win32 和 UWP 專案檔因封裝和部署的差異而不同，但每個專案內的應用程式代碼都是100% 的相同！

建立 OpenXR 的 Win32 桌面之後。EXE，不論是 Windows Mixed Reality 耳機或任何其他耳機，您都可以在任何支援 OpenXR 的 desktop VR 平臺上搭配使用 VR 頭戴式裝置。

建立 OpenXR UWP 應用程式套件之後，您可以將[該套件部署](using-visual-studio.md)到 hololens 2 裝置或 Hololens 2 模擬器。

## <a name="openxr-app-best-practices-for-hololens-2"></a>適用于 HoloLens 2 的 OpenXR 應用程式最佳作法

您可以在 BasicXrApp 的[OpenXRProgram .cpp](https://github.com/microsoft/OpenXR-SDK-VisualStudio/blob/master/samples/BasicXrApp/OpenXrProgram.cpp)檔案中查看下列最佳做法的範例。 開頭的 Run （）函式會從初始化到事件和轉譯迴圈，捕獲一般的 OpenXR 應用程式代碼流程。

### <a name="select-a-swapchain-format"></a>選取 swapchain 格式

一律使用 `xrEnumerateSwapchainFormats`列舉支援的像素格式，並從應用程式支援的執行時間選擇第一個色彩和深度像素格式，因為這是執行時間慣用的。 請注意，在 HoloLens 2 上，`DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` 和 `DXGI_FORMAT_D16_UNORM` 通常是達到更佳轉譯效能的第一種選擇。 在桌上型電腦上執行的 VR 耳機上，此喜好設定可能會不同。  
  
**效能警告：** 使用主要 swapchain 色彩格式以外的格式會導致執行時間後置處理，這會造成顯著的效能影響。

### <a name="gamma-correct-rendering"></a>Gamma-正確呈現

雖然這適用于所有 OpenXR 執行時間，但必須特別小心，以確保轉譯管線是 gamma 正確的。 當轉譯為 swapchain 時，轉譯目標視圖格式應符合 swapchain 格式（例如，swapchain 格式和轉譯目標視圖的 DXGI_FORMAT_B8G8R8A8_UNORM_SRGB）。
例外狀況是如果應用程式的轉譯管線在著色器程式碼中執行手動的 sRGB 轉換，在這種情況下，應用程式應該要求 sRGB swapchain 格式，但針對轉譯目標視圖使用線性格式（例如，要求 DXGI_FORMAT_B8G8R8A8_UNORM_SRGB 做為swapchain 格式，但使用 DXGI_FORMAT_B8G8R8A8_UNORM 做為轉譯目標視圖），以避免將內容更正為雙 gamma。

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

### <a name="render-with-recommended-rendering-parameters-and-frame-timing"></a>使用建議的呈現參數和畫面格時間進行轉譯

一律使用建議的視圖設定寬度/高度（`recommendedImageRectWidth` 和 `recommendedImageRectHeight` 從 `XrViewConfigurationView`）進行轉譯，並一律使用 `xrLocateViews` API 來查詢建議的視圖姿勢、fov 和其他轉譯參數，然後再呈現。
查詢姿勢和 views 時，請一律使用最新 `xrWaitFrame` 呼叫中的 `XrFrameEndInfo.predictedDisplayTime`。
這可讓 HoloLens 針對正在戴 HoloLens 的人員調整呈現和優化視覺品質。

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

### <a name="avoid-quad-layers"></a>避免四層

不是以 `XrCompositionLayerQuad`的組合層來提交四層，而是直接將四個內容轉譯成投射 swapchain。

**效能警告：** 提供超出單一預測層的額外層級（例如四層），會導致執行時間後置處理，而產生顯著的效能影響。

## <a name="openxr-app-performance-on-hololens-2"></a>在 HoloLens 2 上 OpenXR 應用程式效能

在 HoloLens 2 上，有幾種方式可以透過 `xrEndFrame` 提交組合資料，而這會導致後續處理，因而影響效能。
若要避免效能 penalities，請使用下列特性[提交單一 `XrCompositionProjectionLayer`](#use-a-single-projection-layer) ：
* [使用材質陣列 swapchain](#render-with-texture-array-and-vprt)
* [使用主要色彩 swapchain 格式](#select-a-swapchain-format)
* [使用建議的視圖維度](#render-with-recommended-rendering-parameters-and-frame-timing)
* 請勿設定 `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` 旗標
* 將 `XrCompositionLayerDepthInfoKHR` `minDepth` 設定為 0.0 f，並將 `maxDepth` 為 1.0 f

其他考慮會產生較佳的效能：
* [使用16位深度格式](#choose-a-reasonable-depth-range)
* [進行實例繪製呼叫](#render-with-texture-array-and-vprt)

## <a name="roadmap"></a>藍圖

OpenXR 規格定義了擴充機制，可讓執行時間實施者公開超出<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Base OpenXR 1.0 規格</a>中所定義之[核心功能](openxr.md#what-is-openxr)的其他功能。

有三種 OpenXR 擴充功能：
* **廠商擴充功能（例如 MSFT）：** 啟用硬體或軟體功能中的每一廠商創新。  任何執行時間廠商隨時都可以引進和運送廠商延伸模組。
* **EXT 擴充功能：** 多家公司所定義和實行的跨廠商擴充功能。  有興趣的公司群組可以隨時引進 EXT 延伸模組。
* **KHR 延伸模組：** 正式 Khronos 延伸模組已核准為核心規格版本的一部分。  KHR 延伸模組是由與核心規格本身相同的授權所涵蓋。

一年年底，Windows Mixed Reality OpenXR 執行時間將支援一組 MSFT 和 EXT 延伸模組，將一組完整的 HoloLens 2 功能帶入 OpenXR 應用程式：
* [未系結的參考空間（全球規模的體驗）](coordinate-systems.md#building-a-world-scale-experience)
* [空間錨點 + 儲存體](spatial-anchors.md)
* [手形文字清晰度 + 手上網格](hands-and-tools.md)
* [眼睛目光](eye-tracking.md)
* [次要視圖設定（混合現實捕捉）](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)
* [場景理解](scene-understanding.md)
* 與 Windows SDK Api 交互操作

雖然其中一些延伸模組可能會以廠商專屬的 MSFT 延伸模組開頭，但 Microsoft 和其他 OpenXR 執行時間廠商會共同合作，為許多功能領域設計跨廠商的 EXT 或 KHR 延伸模組。  這可讓您針對這些功能所撰寫的程式碼在執行時間廠商之間具有可攜性，就像使用核心規格一樣。

## <a name="troubleshooting"></a>[疑難排解]

以下是 Windows Mixed Reality OpenXR 執行時間的一些疑難排解秘訣。  如果您有任何關於<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 規格</a>的其他問題，請造訪<a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR 論壇</a>或<a href="https://khr.io/slack" target="_blank">#openxr 頻道的時差</a>。

### <a name="developing-on-windows-10-october-2018-update"></a>在 Windows 10 2018 年10月更新上進行開發

如果您無法將[開發電腦升級至5月2019更新](https://www.microsoft.com//software-download/windows10)，您可以再依照下列步驟，設定 Windows 10 2018 年10月更新（1809）電腦以進行開發：

1. 請遵循上述步驟，在您的桌上型電腦上開始使用 OpenXR。
1. 若要將 Windows Mixed Reality OpenXR 執行時間設定為系統的 active OpenXR 執行時間，請安裝[Windows Mixed Reality OpenXR 開發人員相容性套件](https://aka.ms/openxr-compat)。

> [!NOTE]
> 雖然 Windows 10 2018 年10月更新（1809）可在開發 OpenXR 應用程式時使用，但 Windows 10 可能會 2019 Update （1903）是讓一般使用者使用 OpenXR 與 Windows Mixed Reality 的最低需求。  您在2018年10月更新上執行 OpenXR 應用程式時，可能會遇到較低的效能或其他問題。  強烈建議您將開發電腦升級至 Windows 10 5 月2019更新（1903）。

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>OpenXR 應用程式未啟動 Windows Mixed Reality

如果您的 OpenXR 應用程式在執行時未啟動 Windows Mixed Reality，則 Windows Mixed Reality OpenXR 執行時間可能不會設定為作用中的執行時間。  請務必遵循上述指示，以[開始使用適用于 Windows Mixed Reality 耳機的 OpenXR](#getting-started-with-openxr-for-windows-mixed-reality-headsets) ，讓執行時間變成作用中。

您也可以執行[Mixed Reality OpenXR 開發人員入口網站](#getting-the-mixed-reality-openxr-developer-portal)，以取得有關系統上的 Windows Mixed Reality OpenXR 執行時間狀態的其他疑難排解協助。

### <a name="mixed-reality-portal-not-showing-set-up-openxr-menu-item"></a>混合現實入口網站未顯示 [設定 OpenXR] 功能表項目

請確定您至少執行 Windows 10 2018 年10月更新（1809）。  如果您是在舊版的 Windows 10 上，您可以使用[Windows 10 更新](https://www.microsoft.com//software-download/windows10)小幫手升級至5月2019更新（1903）。

如果您有較舊版本的混合現實入口網站應用程式，則可能無法使用 [設定 OpenXR] 功能表項目。  檢查是否有[混合現實入口網站應用程式更新](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m)，以確保您擁有最新版本。

請注意，如果 Windows Mixed Reality OpenXR 執行時間已安裝且作用中，就不會顯示 [設定 OpenXR] 功能表項目。  您可以安裝[Mixed Reality OpenXR 開發人員入口網站](#getting-the-mixed-reality-openxr-developer-portal)，以判斷系統上 OpenXR 執行時間的目前狀態。

## <a name="see-also"></a>請參閱

* <a href="https://www.khronos.org/openxr/" target="_blank">OpenXR 的詳細資訊</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 規格</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">OpenXR 1.0 API 參考</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">OpenXR 1.0 快速參考指南</a>
