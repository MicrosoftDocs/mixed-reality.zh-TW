---
title: 瞭解混合現實的效能
description: 優化 Windows Mixed Reality 應用程式效能的 Advanced 主題和詳細資料
author: troy-ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: Windows Mixed Reality，混合現實，虛擬實境，VR，MR，效能，優化，CPU，GPU
ms.openlocfilehash: 54e1eec5445fe655a0b498be5c18f08efe2270f0
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277476"
---
# <a name="understanding-performance-for-mixed-reality"></a>瞭解混合現實的效能

本文介紹如何瞭解混合現實應用程式的效能重要性。  如果您的應用程式未以最佳畫面播放速率執行，則使用者體驗可能會大幅降低。 全像投影會出現不穩定的情況，而環境的頭追蹤則不正確，導致使用者的體驗不佳。 效能必須視為混合現實開發的第一類功能，而不是波蘭文工作。

以下列出每個目標平臺的高效能速率值。

| 平台 | 目標畫面播放速率 |
|----------|-------------------|
| [HoloLens](hololens-hardware-details.md) | 60 FPS |
| [Windows Mixed Reality Ultra 電腦](immersive-headset-hardware-details.md) | 90 FPS |
| [Windows Mixed Reality 電腦](immersive-headset-hardware-details.md) | 60 FPS |

以下架構概述達到目標畫面播放速率的最佳做法。 如果在 Unity 中進行開發，請考慮閱讀[unity 的效能建議一文](performance-recommendations-for-unity.md)，以取得在 Unity 環境中測量和改善畫面播放速率的秘訣。

## <a name="understanding-performance-bottlenecks"></a>瞭解效能瓶頸

如果您的應用程式具有表現不佳的畫面播放速率，第一個步驟是分析並瞭解您的應用程式需要大量計算的位置。 有兩個主要處理器負責呈現場景的工作： CPU 和 GPU。 每個都處理您混合現實應用程式的不同層面。 有三個主要位置可能發生瓶頸： 

1. **應用程式執行緒-CPU** -此執行緒負責您的應用程式邏輯。 這包括處理輸入、動畫、物理和其他應用程式邏輯。
2. **將執行緒 CPU 轉譯為 gpu** -此執行緒負責將您的繪製呼叫提交至 gpu。 當您的應用程式想要呈現物件（例如 cube 或模型）時，此執行緒會將要求傳送至 GPU 以執行這些作業。
3. **GPU** -此處理器最常處理應用程式的圖形管線，以將3d 資料（模型、紋理等）轉換成圖元。 最後，它會產生2D 影像以提交至裝置的螢幕。

![框架的存留期](images/lifetime-of-a-frame.png)

通常，HoloLens 應用程式會受到 GPU 的限制，但不一定是固定的。 使用下列工具和技術來瞭解您的特定應用程式瓶頸的位置。

## <a name="how-to-analyze-your-application"></a>如何分析您的應用程式

有許多工具可讓您瞭解混合現實應用程式的效能設定檔。 這些可讓您找出發生瓶頸的位置和原因，讓您可以解決問題。

以下是取得應用程式深入分析資訊的一些常見工具：
- [Intel 圖形效能分析器](https://software.intel.com/gpa)
- [Visual Studio 圖形偵錯工具](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)
- [Unity 框架偵錯工具](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a>如何在任何環境中進行分析

判斷您的應用程式中是否已系結 GPU 或 CPU 系結的一種方式，是降低轉譯目標輸出的解析度。 藉由減少要計算的圖元數，這將可減少您的 GPU 負載。 裝置會轉譯成較小的材質，然後向上取樣以顯示您的最終影像。

在減少轉譯解析度之後，如果：
1) 應用程式的畫面播放速率**會增加**，因此您可能會受到**GPU 的限制**
1) 應用程式的畫面播放速率**未**變更，您可能會受到**CPU 限制**

>[!NOTE]
>Unity 可讓您透過 *[XRSettings renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 屬性，在執行時間輕鬆修改應用程式的呈現目標解析度。 裝置上顯示的最終映射具有固定的解析度。 平臺會取樣較低的解析度輸出，以建立更高解析度的影像，以便在顯示器上呈現。 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>如何改善您的應用程式

### <a name="cpu-performance-recommendations"></a>CPU 效能建議

一般來說，CPU 上混合現實應用程式中的大部分工作都牽涉到執行場景的「模擬」，以及處理您的應用程式邏輯。 下欄區域通常會以優化為目標：

- 動畫
- 物理
- 記憶體配置
- 複雜演算法（亦即 反向運動，路徑尋找）

### <a name="gpu-performance-recommendations"></a>GPU 效能建議

#### <a name="understanding-bandwidth-vs-fill-rate"></a>瞭解頻寬與填滿率
在 GPU 上轉譯框架時，應用程式通常會受到記憶體頻寬或填滿率的限制。

- **記憶體頻寬**是 GPU 可以從記憶體執行的讀取和寫入速率
    - 若要找出頻寬限制，請降低材質品質，並檢查幀的是否已改善。
    - 在 Unity 中，這可以藉由變更 **編輯**] > **專案設定** >  **[品質設定](https://docs.unity3d.com/Manual/class-QualitySettings.html)** ] 中的**材質品質**來完成。
- [**填滿速率**] 是指 GPU 每秒可繪製的圖元。
    - 若要識別填滿率限制，請減少顯示器解析度，並檢查是否已改善畫面播放速率。 
    - 在 Unity 中，這可以透過 *[XRSettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 屬性來完成。

記憶體頻寬通常牽涉到下列其中一項的優化：
1) 減少材質解析度
2) 使用較少的材質（法線、反射等等）

[填滿速率] 著重于減少需要針對最終呈現圖元計算的作業數目。 這包括減少：
1) 要呈現/處理的物件數目
2) 每個著色器的作業數目
3) 最後結果的 GPU 階段數（幾何著色器、後置處理效果等）
4) 要呈現的圖元數（顯示解析度）

#### <a name="reduce-polygon-count"></a>減少多邊形計數

較高的多邊形計數會產生更多 GPU 的作業;減少場景中的[多邊形數目](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)會減少轉譯時間。 有一些其他因素會使幾何變得昂貴，但多邊形計數是最簡單的計量，用以判斷要呈現場景的成本。

#### <a name="limit-overdraw"></a>限制過度繪製

當有多個物件呈現，但因為 occluding 物件隱藏而未顯示在螢幕上時，就會發生高過度繪製。 想像一下，看一下有物件背後的牆。 所有的幾何都會處理以進行轉譯，但只需要轉譯不透明的牆。 這會導致不必要的作業。

#### <a name="shaders"></a>著色器

著色器是在 GPU 上執行的小型程式，會在轉譯時執行兩個重要步驟：
1) 判斷應該繪製哪些頂點，以及它們在螢幕空間中的位置（頂點著色器）
    - 頂點著色器通常會針對每個網格執行每個頂點。
2) 判斷每個圖元的色彩（圖元著色器）
    - 圖元著色器會針對幾何轉譯成材質的每個圖元執行。

著色器通常會執行許多轉換和光源計算。 雖然複雜的光源模型、陰影和其他作業可以產生絕佳的結果，但也會提供價格。 減少著色器中計算的作業數目，可以大幅減少每個畫面格所需的 GPU 工作量。

##### <a name="shader-coding-recommendations"></a>著色器編碼建議

- 盡可能使用雙線性篩選
- 重新排列運算式以使用 MAD 內建函式，以便同時執行乘法和 add
- 在 CPU 上盡可能 Precalculate，並以常數的形式傳遞至材質
- **偏好將作業從圖元著色器移至頂點著色器**
    - 通常，頂點數目遠小於圖元數（720p 為921600圖元、1080p 為2073600圖元等等）。

#### <a name="remove-gpu-stages"></a>移除 GPU 階段

後續處理效果可能非常昂貴，而且會增加應用程式的填滿率。 這包括消除鋸齒的技術，例如 MSAA。 在 HoloLens 上，建議您完全避免這些技術，以及額外的著色器階段，例如幾何、輪廓和計算著色器。

## <a name="memory-recommendations"></a>記憶體建議

過多的記憶體配置和解除配置作業，可能會導致效能不一致、凍結的框架和其他不利的行為。 在 Unity 中開發時，請務必瞭解記憶體考慮，因為記憶體管理是由垃圾收集行程所控制。

#### <a name="object-pooling"></a>物件集區

物件共用是降低連續配置和物件取消配置成本的常用技術。 這是藉由配置相同物件的大型集區，並重複使用此集區中非使用中的可用實例來完成，而不是在一段時間內不斷產生和終結物件。 物件集區非常適合在應用程式期間有變數存留期的重複使用元件。

## <a name="see-also"></a>另請參閱
- [對 Unity 的效能建議](performance-recommendations-for-unity.md)
- [Unity 的建議設定](recommended-settings-for-unity.md)
- [優化3D 模型](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [轉換和優化即時3D 模型的最佳做法](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/best-practices)

