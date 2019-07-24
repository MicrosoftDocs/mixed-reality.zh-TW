---
title: 瞭解混合現實的效能
description: 優化 Windows Mixed Reality 應用程式效能的 Advanced 主題和詳細資料
author: Troy-Ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: Windows Mixed Reality, 混合現實, 虛擬實境, VR, MR, 效能, 優化, CPU, GPU
ms.openlocfilehash: ce59f9023c21dc7c981a2bb97d9fbd0c57622dbf
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548833"
---
# <a name="understanding-performance-for-mixed-reality"></a>瞭解混合現實的效能

本文介紹合理化混合現實應用程式效能的重要性。  如果您的應用程式未以最佳畫面播放速率執行, 則使用者體驗可能會大幅降低。 全像投影會出現不穩定的情況, 而且環境的頭追蹤會不正確, 導致使用者的體驗不佳。 事實上, 必須將效能視為混合現實開發的第一類功能, 而不是穩定的迴圈結束工作。

如需審查, 以下列出每個目標平臺的高效能的畫面播放速率值。

| 平台 | 目標畫面播放速率 |
|----------|-------------------|
| [HoloLens](hololens-hardware-details.md) | 60 FPS |
| [Windows Mixed Reality Ultra 電腦](immersive-headset-hardware-details.md) | 90 FPS |
| [Windows Mixed Reality 電腦](immersive-headset-hardware-details.md) | 60 FPS |

以下架構提供最佳做法的一般大綱, 以及達到目標畫面播放速率的稍微瞭解。 若要深入瞭解詳細資料, 請考慮閱讀[Unity 的效能建議一文](performance-recommendations-for-unity.md)。 特別是, 這篇相關文章將討論如何測量 Unity Windows Mixed Reality 應用程式中的幀速度, 以及在 Unity 環境中採取的步驟來改善效能。

## <a name="understanding-performance-bottlenecks"></a>瞭解效能瓶頸

如果您的應用程式具有表現不佳的畫面播放速率, 第一個步驟是分析並瞭解您的應用程式需要大量計算的位置。 有兩個主要處理器負責呈現場景的工作: CPU 和 GPU。 這兩個元件都會處理混合現實應用程式的不同作業和階段。 有三個可能發生瓶頸的關鍵位置。 

1. **應用程式執行緒-CPU** -此執行緒負責您的應用程式邏輯。 這包括處理輸入、動畫、物理和其他應用程式邏輯/狀態
2. **將執行緒 CPU 轉譯為 gpu** -此執行緒負責將您的繪製呼叫提交至 gpu。 當您的應用程式想要轉譯物件 (例如 cube 或模型) 時, 此執行緒會將要求傳送至 GPU, 其具有針對轉譯而優化的架構, 以執行這些作業。
3. **GPU**- 
   此處理器最常處理應用程式的圖形管線, 以將3d 資料 (模型、材質等等) 轉換成圖元, 最後產生2d 影像以提交至裝置的螢幕。

![框架的存留期](images/lifetime-of-a-frame.png)

一般來說, HoloLens 應用程式會受到 GPU 限制。 不過, 這並不會在每個應用程式中都成立, 因此建議使用以下的工具 & 技術, 為您的特定應用程式提供最真實的做法。

## <a name="how-to-analyze-your-application"></a>如何分析您的應用程式

有許多工具可讓您身為開發人員, 以瞭解混合現實應用程式的效能設定檔。 這些可讓您以具有瓶頸的目標, 以及它們本身股潮流以進行偵錯工具的方式來進行。

這是熱門且功能強大的工具清單, 可取得應用程式的深入剖析資訊。
- [Intel 圖形效能分析器](https://software.intel.com/gpa)
- [Visual Studio 圖形偵錯工具](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)
- [Unity 框架偵錯工具](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a>如何在任何環境中進行分析

有一個簡單的測試可以快速判斷您的應用程式中是否有可能的 GPU 界限或 CPU 限制。 如果您降低轉譯目標輸出的解析度, 則會有較少的圖元來計算, 因此 GPU 需要執行以轉譯影像的工作量較少。 視口調整 (動態解析度調整) 是將影像轉譯成較小的轉譯目標, 然後您的輸出裝置可以顯示的做法。 裝置會從較小的圖元集合中取樣, 以顯示您的最終影像。

在減少轉譯解析度之後, 如果:
1) 應用程式的畫面播放速率**會增加**, 因此您可能會**限制 GPU**
1) 應用程式的畫面播放速率**未**變更, 您可能會受到**CPU 限制**

>[!NOTE]
>Unity 讓您能夠輕鬆地修改您的應用程式，透過在執行階段的轉譯目標解析度 *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 屬性。 裝置上顯示的最終映射具有固定的解析度。 平臺會取樣較低的解析度輸出, 以建立更高解析度的影像, 以便在顯示器上呈現。 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>如何改善您的應用程式

### <a name="cpu-performance-recommendations"></a>CPU 效能建議

一般來說, CPU 上混合現實應用程式中的大部分工作都牽涉到執行場景的「模擬」, 並處理大量的獨特應用程式邏輯。 因此, 下欄區域通常會以優化為目標。

- 動畫
- 簡化物理
- 記憶體配置
- 複雜演算法 (亦即 反向運動, 路徑尋找)

### <a name="gpu-performance-recommendations"></a>GPU 效能建議

#### <a name="understanding-bandwidth-vs-fill-rate"></a>瞭解頻寬與填滿率
在 GPU 上轉譯框架時, 應用程式通常會受到記憶體頻寬或填滿率的限制。

- **記憶體頻寬**是 GPU 可以從記憶體執行的讀取和寫入速率
    - 若要找出頻寬限制, 請降低材質品質, 並檢查是否已改善畫面播放速率。
    - 在 Unity 中, 您可以在 [**編輯** > **專案設定** >  **[品質] 設定](https://docs.unity3d.com/Manual/class-QualitySettings.html)** 中變更**材質品質**來完成這項作業。
- [**填滿速率**] 是指 GPU 每秒可繪製的轉譯圖元輸送量。
    - 若要識別填滿率限制, 請減少顯示器解析度, 並檢查是否已改善畫面播放速率。 
    - 在 Unity 中，這可以透過 *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 屬性

記憶體頻寬通常牽涉到下列其中一項的優化
1) 減少材質解析度
2) 利用較少的紋理 (也就是 法線、反射等等)

[填滿速率] 主要著重于減少需要針對最終呈現圖元計算的作業數目。 這種情況的範例通常會減少
1) 要呈現/處理的物件數目
2) 每個著色器的作業數目
3) 最後結果的 GPU 階段數 (幾何著色器、後置處理效果等)
4) 要呈現的圖元數 (亦即 顯示器解析度)

#### <a name="reduce-poly-count"></a>減少 poly 計數
較高的多邊形計數會導致 GPU 的更多作業, 並減少場景中的多邊形數目, 以減少呈現該幾何的時間量。 還有其他因素會加上陰影, 但可能仍然很昂貴, 但多邊形計數是基底計量, 用來判斷要呈現場景的代價。

#### <a name="limit-overdraw"></a>限制過度繪製

當轉譯多個物件但未輸出到螢幕上, 但另一個通常較近的 occluding 物件隱藏時, 就會發生高過度繪製。 想像一下有多個房間和幾何背後的牆。 所有的幾何都會處理以進行轉譯, 但只有不透明的牆在 occludes 所有其他內容的觀點時, 才需要轉譯。 這會導致目前的觀點不需要浪費作業。

#### <a name="shaders"></a>著色器

著色器是在 GPU 上執行的小型程式, 通常會判斷轉譯中的兩個重要步驟:
1) 哪一個物件的頂點應該繪製在畫面上, 以及它們在螢幕空間中的位置 (亦即 頂點著色器)
    - 端點著色器通常會針對每個 GameObject 的每個頂點執行
2) 這些圖元的色彩 (亦即 圖元著色器)
    - 圖元著色器會針對呈現的裝置材質, 每圖元執行一次

著色器通常會執行許多轉換和光源計算。 雖然複雜的光源模型、陰影和其他作業可以產生絕佳的結果, 但也會提供價格。 減少在著色器中計算的作業數目, 可以大幅減少每個畫面的 GPU 所需的整體工作。

##### <a name="shader-coding-recommendations"></a>著色器編碼建議

- 盡可能使用雙線性篩選
- 重新排列運算式以使用 MAD 內建函式, 以便同時執行乘法和 add
- 在 CPU 上盡可能 Precalculate, 並以常數的形式傳遞至材質
- **偏好將作業從圖元著色器移至頂點著色器**
    - 一般來說, 頂點的 # < < 的圖元數 (亦即 720p = = 921600 圖元、1080p = = 2073600 圖元等等)

#### <a name="remove-gpu-stages"></a>移除 GPU 階段
後續處理效果可能非常昂貴, 而且通常會抑制應用程式的填滿率。 這也包含消除鋸齒的技術, 例如 MSAA。 在 HoloLens 上, 建議您完全避免這些技術。 此外, 您應該盡可能避免其他的著色器階段, 例如幾何、輪廓和計算著色器。

## <a name="memory-recommendations"></a>記憶體建議
記憶體配置過多 & 解除配置作業可能會對您的全像攝影應用程式造成不良的影響, 因而導致效能不一致、凍結的框架和其他有害行為。 在 Unity 中開發時, 請務必瞭解記憶體考慮, 因為記憶體管理是由垃圾收集行程所控制。

#### <a name="object-pooling"></a>物件共用

物件共用是一種常用的技術, 可降低連續配置 & 取消設定物件的成本。 這是藉由配置相同物件的大型集區, 並重複使用此集區中的非作用中、可用的實例來完成, 而不是在一段時間內不斷產生和終結物件。 物件集區非常適合在應用程式期間有變數存留期的重複使用元件。

## <a name="see-also"></a>另請參閱
- [對 Unity 的效能建議](performance-recommendations-for-unity.md)
- [Unity 的建議設定](recommended-settings-for-unity.md)
